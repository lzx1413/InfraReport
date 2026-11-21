# GitHub Stars 合并报告 - 2026-11-20

**合并日期**: 2026-11-21
**监控日期**: 2026-11-20
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


**报告日期**: 2026-11-21
**监控日期**: 2026-11-20
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2299
- **最后更新**: 2026-11-20T15:30:44Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 4
- **主要提交者**: Coach257, Yusen Gao, yumingXiang

## AI分析总结

## VeOmni 昨日提交分析

### 1. 主要更新类型
本次提交以 **Bug修复** 为主（DPO训练中Float8与Muon优化器的精度问题），同时包含一项重要的 **BREAKING重构**（移除patchgen、统一HF建模），以及一项 **功能新增**（Cosmos3-Nano SFT支持SeedOmni）。整体属于"补丁维护 + 架构收敛 + 模型扩展"的组合。

### 2. 关键变更点及与项目方向的关系
- **[trainer] 禁用冻结DPO参考模型的Float8**：DPO训练时参考模型（reference model）被冻结但此前仍可能走Float8低精度路径，导致隐式精度损失或数值不一致。修复确保了RLHF/DPO管线的正确性，与项目"规模化任意模态训练"的目标一致——训练正确性是规模化前提。
- **[optim] Muon优化器排除路由/混合/门控矩阵**：Muon按二维矩阵形状分配更新策略，但transformer中的router、mixer、gate类矩阵结构特殊，套用Muon规则会破坏其语义。此修复保护了MoE类混合结构的稳定性，直接关系到多模态大模型中常见的MoE路由训练质量。
- **[omni, model, data, config, docs] 新增Cosmos3-Nano SFT on SeedOmni**：完整支持了NVIDIA Cosmos3-Nano在SeedOmni框架下的SFT训练，覆盖模型定义、数据、配置与文档四个层面，体现了"Model-Centric Distributed Recipe Zoo"的核心理念——为新模型提供成套训练配方。
- **[BREAKING] 移除patchgen，统一独立HF建模**：清理历史遗留的patchgen工具链，将模型实现收敛到统一的HuggingFace建模范式。作为破坏性变更，它降低了维护成本，提升了与HF生态的互操作性。

### 3. 对项目的影响和潜在意义
- 训练正确性修复（Float8、Muon）显著提升了DPO与MoE训练的可靠性，减少"隐性坏结果"。
- Cosmos3-Nano配方扩展印证了Recipe Zoo的可扩展性，向更多视觉生成/世界模型场景延伸。
- BREAKING重构虽增加迁移成本，但长期简化架构，为后续新模型接入铺路。

### 4. 值得关注的技术点
- **Float8与冻结模型的交互**：低精度训练中"冻结"不等于"可降精度"，参考模型需与策略模型保持数值对齐。
- **Muon对特殊矩阵的适用边界**：优化器形状启发式在非标准层（router/gate）上的失效模式值得社区借鉴。
- **HF统一建模路线**：与HuggingFace生态对齐是多模态框架降低采用门槛的关键策略。

### 5. 对项目发展的整体影响
结合README所述目标——"以模型为中心的分布式配方库扩展任意模态训练"——这批提交体现了项目从"快速堆功能"转向"质量收敛与架构治理"的阶段。修复提升了训练配方的可信度，Cosmos3-Nano扩展了模态覆盖面，而patchgen移除则为Recipe Zoo建立了更统一的建模基座。三者共同强化了项目作为可复现、可扩展多模态训练基础设施的定位，有助于吸引更多研究者与生产场景采用VeOmni。

## 详细提交记录

### [3660a32](https://github.com/ByteDance-Seed/VeOmni/commit/3660a3249d6796d1e7577b424198b059c5cbc69d)

- **作者**: Yusen Gao
- **时间**: 2026-11-20T09:25:25Z
- **提交信息**: [trainer] fix: disable Float8 on the frozen DPO reference (#1487)

### [0432d0e](https://github.com/ByteDance-Seed/VeOmni/commit/0432d0ebd123b888c3c027758ea59029f0c9a54e)

- **作者**: Coach257
- **时间**: 2026-11-20T08:34:14Z
- **提交信息**: [optim] fix: keep Muon off the 2D matrices that route, mix or gate (#1485)

Co-authored-by: Cursor <cursoragent@cursor.com>

### [2e5cd9d](https://github.com/ByteDance-Seed/VeOmni/commit/2e5cd9d86933b31c557934c9816a32b908ca5f94)

- **作者**: yumingXiang
- **时间**: 2026-11-20T07:21:58Z
- **提交信息**: [omni, model, data, config, docs] feat: add Cosmos3-Nano SFT on SeedOmni (#1463)

### [6695209](https://github.com/ByteDance-Seed/VeOmni/commit/6695209f57af09a8d369f4fecefc4ec1713c04d6)

- **作者**: Bin Jia
- **时间**: 2026-11-20T07:18:10Z
- **提交信息**: [BREAKING][model, ci, docs, agent, misc] refactor: remove patchgen and unify standalone HF modeling (#1464)

Co-authored-by: Cursor <cursoragent@cursor.com>

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-11-21
**监控日期**: 2026-11-20
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 3015
- **最后更新**: 2026-11-20T17:10:36Z

## 提交统计

- **昨日提交总数**: 5
- **提交者数量**: 2
- **主要提交者**: Bilang ZHANG, STwangyingrui

## AI分析总结

## LightX2V 仓库近期提交分析总结

### 1. 主要更新类型
- **功能新增**（2项）：RTX 4090D 全面适配、LongCat-Video-Avatar 1.6 支持
- **Bug修复**（1项）：HEIC/HEIF 参考图格式与纯音频 MP4 检测
- **性能优化**（2项）：RTX 5090 warmup 启用、MiniMax H3 图像生成加速

### 2. 关键变更点及与项目方向的关系
LightX2V 定位为**轻量级视频生成推理框架**，本轮提交核心围绕三个方向：

- **硬件适配广度**：#1747 一次性在 RTX 4090D 上打通 11 项图像/视频推理任务，覆盖 Qwen Image、Wan2.2、LTX2.3、SwiftVR、Animate/Animate2 等主流模型族；#1745 则为 RTX 5090 启用 warmup。这直接服务于项目"轻量推理"的定位——降低高端/消费级 GPU 的使用门槛。
- **模型生态扩展**：新增 LongCat-Video-Avatar 1.6 支持，延续了框架持续接入新视频生成模型的路线。
- **推理体验健壮性**：修复 HEIC/HEIF 参考图支持和纯音频 MP4 识别，改善了实际部署中输入格式兼容性的短板。

### 3. 对项目的影响和潜在意义
- RTX 4090D/5090 的深度优化使框架更贴近**国产及消费级显卡用户**（4090D 为中国市场特供版本），有助于扩大用户基数和部署场景。
- 多模型多任务的统一适配体现了框架的**通用推理底座**价值，减少用户在不同硬件上重复调优的成本。
- 输入格式修复虽小，但显著提升了**生产环境的可用性**，避免因格式不兼容导致的推理失败。

### 4. 值得关注的技术点
- **多模型×多硬件矩阵的系统性适配**（#1747）：一次性覆盖 11 个任务，说明框架已具备成熟的设备感知和算子优化流水线。
- **DiT conditioning 复用 + tiled VAE 加速**（#1743）：通过减少重复计算和分块处理显存峰值，在 MiniMax H3 图像任务上实现显著提速，是典型的推理级优化手法。
- **Warmup 策略**（#1745）：针对 RTX 5090 新架构的初始化优化，体现对新硬件特性的快速响应能力。

### 5. 对项目发展的整体影响
结合 README 可知，LightX2V 的核心目标是提供**轻量、高效的视频生成推理方案**。本轮提交在"轻量"（硬件门槛降低）和"高效"（性能优化与兼容性修复）两个维度同时推进：硬件适配让框架触达更多真实用户，模型扩展保持技术竞争力，输入兼容性修复则夯实工程质量。这些变更共同强化了项目作为**多模型、多硬件统一视频生成推理平台**的定位，为其在开源视频生成生态中建立差异化优势奠定了基础。

## 详细提交记录

### [c840dad](https://github.com/ModelTC/LightX2V/commit/c840dadef7ab911e3ce1406d39a000a66ad6d729)

- **作者**: STwangyingrui
- **时间**: 2026-11-20T14:51:34Z
- **提交信息**: feat: deploy and optimize multiple models and tasks on RTX 4090D (#1747)

This PR enables and optimizes RTX 4090D deployment for 11 image and
video inference tasks across Qwen Image, Wan2.2, LTX2.3, SwiftVR,
Animate, and Animate2.

### [af44ddf](https://github.com/ModelTC/LightX2V/commit/af44ddf872d7e5d687cfb7549506cdf9b843295b)

- **作者**: Bilang ZHANG
- **时间**: 2026-11-20T10:04:12Z
- **提交信息**: fix: support HEIC/HEIF reference images and detect audio-only MP4s (#1746)

### [f2a5617](https://github.com/ModelTC/LightX2V/commit/f2a56171bfe6555bd66a15d86e5c45c0d169add4)

- **作者**: Bilang ZHANG
- **时间**: 2026-11-20T04:20:36Z
- **提交信息**: perf: enable warmup for RTX 5090 (#1745)

### [0b23334](https://github.com/ModelTC/LightX2V/commit/0b23334e7cfbe6576f9779a8b66e62d0f633a2fd)

- **作者**: Bilang ZHANG
- **时间**: 2026-11-20T04:00:04Z
- **提交信息**: feat: support LongCat-Video-Avatar 1.6 (#1744)

### [6ef8487](https://github.com/ModelTC/LightX2V/commit/6ef8487c63dc9ee75b3f009ad965f0aa78f9ad58)

- **作者**: Bilang ZHANG
- **时间**: 2026-11-20T02:57:27Z
- **提交信息**: perf(minimax_h3_image): reuse DiT conditioning and accelerate tiled V… (#1743)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-11-21
**监控日期**: 2026-11-20
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2337
- **最后更新**: 2026-11-19T08:42:27Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-11-21
**监控日期**: 2026-11-20
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6979
- **最后更新**: 2026-11-21T02:24:49Z

## 提交统计

- **昨日提交总数**: 46
- **提交者数量**: 26
- **主要提交者**: Adrian, oiiai-oiiai, Bo Li

## AI分析总结

# FlashInfer 昨日提交综合分析

## 一、主要更新

昨日 46 个提交涵盖性能优化、功能新增、Bug 修复、构建维护与工程基建五类。性能方面包括 SM103 分页 FMHA 调度器调整、sm_107a Cake FP8 GEMM 调优、gathered-row GEMV、MLA decode 与 batch-invariant 采样/GEMM 开销削减；功能方面新增 tgv GEMM 的 tactic/FP32 输出、SM12x FP4 GEMV、NCCL EP 0.3 细粒度控制、非因果 batch-invariant 注意力、MoE routing tile 查询 API、Rubin MXFP8 MoE 局部域执行，以及 FP16 注意力路径与 GDN 训练无状态调用/状态导出；修复涉及 NVLink 内存屏障 clobber、PrimTS 空 KV 死锁、FA3 Hopper 静默数值错误、VC-Attention 越界读取、TGV 维度校验与 autotuner 缓存键问题；依赖方面 cuDNN Frontend 升至 1.33.0、DeepGEMM 改由 PyTorch 选择 C++ 标准，并新增 NVSkills CI 签名工作流。

## 二、关键变更

围绕三条主线展开。**新硬件适配与稳定化**：SM103 分页 FMHA 切换为 Static 调度器，以窄范围 workaround 消除 B300 死锁（位级一致、吞吐损失 <0.7%）；Cake FP8 GEMM 的 CTA 预留调优扩展到 212-SM 双 die SM107a，`expected_m >= 36` 时提速 1.03–1.12x 且输出位一致；FP16 Q/KV/output 复用 Blackwell paged-auto 路径，较此前 FA2 回退加速约 3.3–3.7x；同时为 SM12x 移植 FP4 GEMV 与局部域 MoE，利用 green context 并行 FC1/FC2。**训练推理一致与生态开放**：`chunk_gated_delta_rule` 在 `batch_invariant=True` 下支持无状态调用，逐位对齐推理前向，可选 `train_states` 单次 launch 写出 64 token 分块状态，布局兼容 cuDNN GDN 反向约定；开放 tgv tactic 与 FP32 输出以促 SGLang 弃用自带内核；新增 routing tile 查询接口，让调用方自建 metadata 实现跨流重叠，服务 vLLM/TRT-LLM 类引擎的算子融合。**确定性与健壮性**：补全非因果 batch-invariant 注意力满足 RL rollout；拒绝 K 非 8 倍数的 TGV/TinyGEMM 输入，杜绝静默错误；修复 FA3 barrier 计数脏读、PrimTS 持久化内核挂死与 PTX fence 缺 memory clobber 的重排隐患；收窄 CuTe-DSL 缓存键导入追踪规避 90 文件上限；回滚 autotuner 行为使 main 与 release 一致。

## 三、技术关注点

死锁定位采用 stream marker 加 `compute-sanitizer synccheck` 精确锁定 mbarrier 错误；持久化内核要求所有 warp 在 CTA barrier 一致到达，需复用统一谓词；`gemv_bf16_fp4_gather` 无 SMEM、无 tensor core，靠 half-warp 流式加载与 L2 共享实现加速；top-p 内核用 64 位定点精确 nucleus 解析配合 radix select；位级 batch-invariance 作为采样、KDA、GEMM 优化的硬约束；CTA reserve 按 SM 数差异化调优，体现对双 die 拓扑的精细感知；plan-time 准入与执行路径分离是低风险扩大覆盖面的典型手法；预处理器自带并 reseed 随机数生成器，不消耗调用方 CUDA generator；Cake MLA 将行计划移至设备端，以牺牲 host 缓存最优场景换取 decode 循环 1.15–3.95× 提速；SM107 共享内存测试由约 50s 降至 0.23s。

## 四、项目影响

稳定性修复消除了 B300 等生产环境的挂死与静默数值错误风险，VC-Attention 修复消除长视频场景崩溃；MoE 链路优化与 NCCL EP 0.3 直接提升 DeepSeek 系模型在 EP 场景的吞吐；autotuner 缓存键与黑名单修复避免调优盲区和非确定性策略复活；cuDNN FE 1.33.0 成为正式下限，形成版本-功能闭环。项目正从内核集合走向"推理—训练一致的高性能内核平台"：一手加深训练闭环纵深，一手拓宽工程协作工具链，在保持 API 与行为稳定的前提下加速对齐最新 NVIDIA 硬件及 vLLM、SGLang 生态，为下一次 release 收敛奠定了干净的 main 基线。

## 详细提交记录

### [ceb7af3](https://github.com/flashinfer-ai/flashinfer/commit/ceb7af388d41ae3532f27de3750375ef7efc29aa)

- **作者**: donguk.lim
- **时间**: 2026-11-20T23:39:01Z
- **提交信息**: fix(trtllm-gen): use static tile scheduler for SM103 paged context FMHA (#9702)

## 📌 Description

This PR uses `TileScheduler::Static` instead of
`TileScheduler::Persistent` for the **paged context** trtllm-gen FMHA
path on **SM103**. Other architectures, the ragged context path and the
generation path are unchanged.

### Why

On B300 (sm_103), `fmhaSm103aKernel_*PagedKv*PersistentContext` can
deadlock under serving load (#9700):

- **Hang signature:** GPU util 100 %, SM_ACTIVE ≈ 0.01, DRAM 0. It never
recovers and reports no Xid. The stuck call was confirmed with stream
markers to be inside `trtllm_batch_context_with_kv_cache`.
- **Sanitizer:** `compute-sanitizer --tool synccheck` reports `Barrier
error detected. Missing wait.` on the softmax-warpgroup mbarriers, and
only when one CTA processes more than one tile (grid > #SMs, CLC work
stealing).
  - single tile per CTA: 0 errors
  - static scheduler: 0 errors
  - The 0.7.0.post1 and current (0.7.4) cubins show the same pattern.

### Why Static is safe

- **Kernels exist:** every `Sm103a…PersistentContext` cubin in the
current cubin set has a matching `…StaticContext` cubin (1,074 / 1,074),
so kernel selection keeps working for all existing configurations.
- **Correctness:** outputs are bit-identical to Persistent on the cases
tested (single tile, multi-tile, and the shapes of real hangs).
- **Kernel time:** within ±3 % (median of 20 runs), except one tiny
single-tile case (0.103 → 0.131 ms).
- **Real prefill batches:** replaying 800 batches captured from serving
gives Static/Persistent total time 0.998.
- **End-to-end serving:** 8 × B300, 4 GPUs Persistent vs 4 GPUs Static,
~68 GPU-hours each.
  - Hangs: Persistent 2, Static 0.
  - Output throughput: within ±0.7 % at concurrency 240 / 280 / 320.

The change is deliberately narrow, so it can be reverted once the
persistent context kernel is fixed upstream.

## 🔍 Related Issues

- Fixes #9700 (workaround until the persistent context kernel is fixed)
- Possibly related: #4759 (SM103 ragged `…PersistentContext` that never
retires)

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

The changed file passes clang-format v19.1.1, the version the hook uses.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).

Suggested CI test targets:
`tests/attention/test_trtllm_gen_attention_prefill.py
tests/trace/test_trtllm_batch_context_reference_correctness.py
tests/attention/test_attention_sink_blackwell.py`

- **Verified locally:** the same one-line change on flashinfer
0.7.0.post1 and 0.7.4 (B300). That covered the bit-exactness, synccheck,
timing and serving results above, using the standalone reproducer from
#9700.
- **Not run:** the upstream test suite on this branch.

## Reviewer Notes

- **Scope:** only SM103 was measured. The SM100 persistent context
kernels likely share the same structure, but we have no SM100 data, so
they are left unchanged.
- **Option instead of a default:** if you would rather not change the
default, I can turn this into an opt-in instead (for example an env var
or a launcher argument).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Improvements**
* Paged-context attention on SM103 hardware now uses an
architecture-specific execution strategy; other architectures continue
using their existing strategy.
* Tiny-GQA generation continues to use its existing execution strategy
regardless of the paged-context scheduler choice.
  * No user-facing settings or workflows have changed.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [b498964](https://github.com/flashinfer-ai/flashinfer/commit/b4989647dde77c3d567af587a2377f33759fe5cc)

- **作者**: Yang Xu
- **时间**: 2026-11-20T23:28:40Z
- **提交信息**: refactor: remove obsolete cuDNN frontend version checks (#9795)

## Description

FlashInfer requires `nvidia-cudnn-frontend>=1.33.0`. Use that dependency
floor for frontend APIs in paged prefill, linear attention, QSA and FP4
GEMM. FP16 and BF16 now share the same paged placement predicates.
Runtime admission still checks the backend version, native binder
capabilities, DSL support and per-call layout/shape constraints. Linear
attention still handles an unsupported overwrite plan and checks
state-pool semantics.

## Related changes

Follows the FP16 paged auto placement in #9463. The expected-raise test
update is tracked in #9785.

## Validation

- CPU and dispatch contract suite with CUDA hidden, 471 passed and 28
skipped.
- Local SM100 with the released FE 1.33.0 wheel and cuDNN backend
9.24.0.43. Four paged full-prefill cases passed, covering FP16/BF16 at
D128 and D256, CUDA Graph replay with updated inputs and page mappings,
and fallback to FA2. GDN and KDA state-pool replay tests both passed.
- Checked the QSA lazy import and FP4 availability on backend 9.24,
including rejection of a simulated backend below 9.10.2.
- Repository pre-commit hooks passed on the changed files.

AI-assisted change.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* FP16 can now use automatic paged-attention placement under the same
matching-dtype rules as BF16.
* Full-prefill placement now supports additional head dimensions when
the required runtime capabilities are available.
* Relaxed cuDNN frontend-version restrictions for attention and
state-pool operations, allowing supported environments to use these
paths without those version checks.
* **Documentation**
* Updated paged-attention requirements to reflect runtime and
graph-declaration capabilities.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Yang Xu <yanxu@nvidia.com>

### [5b2f7de](https://github.com/flashinfer-ai/flashinfer/commit/5b2f7dea071dded817730fe684ab1c3db01ef95c)

- **作者**: Wookje Han
- **时间**: 2026-11-20T23:28:25Z
- **提交信息**: feat(gemm): mm_bf16(backend="tgv") takes a caller tactic and FP32 output (#9787)

## 📌 Description

1. SGLang ships its own copy of the `tgv_gemm_cute_ext` BF16 GEMM,
because it picks the tile per shape itself and needs FP32 output;
`mm_bf16(backend="tgv")` offers neither.
2. This PR adds the two missing inputs, so callers can use FlashInfer's
kernel and drop their copies.

### API
- `mm_bf16(..., backend="tgv", tactic=<id>)`: keyword-only. Runs that
tactic id of `_TGV_CUTE_EXT_TACTIC_CONFIGS` and skips the default and
the autotuner (also inside `autotune()`). Valid ids: `0 .. 28` on
SM100/SM103, `0 .. 46` on SM107. Other backends, `backend="auto"` and
`batch_invariant=True` reject it.
- `mm_bf16(..., out_dtype=torch.float32, backend="tgv")`: FP32 output
(explicit `backend="tgv"` only). The epilogue already casts to the
output tensor's element type, so the change is host side: the output
dtype is now part of the compile key and of the representative tensors.

```python
out = torch.empty(m, n, device="cuda", dtype=torch.float32)
flashinfer.mm_bf16(x, w.T, None, True, out=out, out_dtype=torch.float32, backend="tgv", tactic=18)
```

### Details
- `TgvGemmCuteExtKernel.__repr__` names the config, so profiles show
`TgvGemmCuteExtKernel_cta64x16x128_2cta1_pdl1_bias0_outbfloat16` instead
of `...TgvGemmCuteExtKernel_object_at_...`.
- FP32 output needs `backend="tgv"`; `backend="auto"` keeps its current
candidates for FP32 output.

## 🧪 Tests

`tests/gemm/test_mm_bf16.py`:
- `test_mm_bf16_tgv_tactic`: tactics 0, 1, 12, 15, 18, 24, 28 (+ 29, 39,
46 on SM107), with and without bias; the requested tactic runs under
`autotune(True)`, FP32 output matches an FP32 reference, and FP32 output
rounded to BF16 is bit-identical to the BF16 output.
- `test_mm_bf16_tgv_tactic_rejects`: tactic with another backend /
`"auto"` / `batch_invariant`, an out-of-range id, FP16 output.
- `test_tgv_cute_ext_kernel_name`: kernel name.
- New smoke case: `tgv` with FP32 output, bias and PDL.

Results:
- SM107: `test_mm_bf16.py` 123 passed; `test_tgv_gemm.py` +
`test_bmm_bf16.py` +
`tests/trace/test_tgv_gemm_sm100_reference_correctness.py` 310 passed,
161 skipped; `test_bf16_gemm_peer_store.py` 42 passed.
- SM103: `test_mm_bf16.py` 116 passed, 7 skipped (SM107-only tactics,
cuDNN FP16 output); the same three files 423 passed, 48 skipped;
`test_bf16_gemm_peer_store.py` 42 passed.
- Against SGLang's copy with the same tactic (275 cases: SGLang's
dense-GEMM shapes, every tactic 0-28, BF16 and FP32 output, with and
without bias): bit-identical on SM107 and SM103; kernel time
FlashInfer/SGLang geomean 1.001 (SM107) and 0.998 (SM103).
- pre-commit clean.

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

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/gemm/test_mm_bf16.py
tests/gemm/test_bmm_bf16.py tests/gemm/test_tgv_gemm.py
tests/gemm/test_bf16_gemm_peer_store.py`

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
* Added an option to select a TGV tactic directly when using the TGV
backend.
* TGV now supports FP32 output when explicitly selected; automatic
backend selection continues to support BF16 output.
  * Expanded GEMM support for FP32 output with bias and PDL enabled.

* **Validation**
* Unsupported combinations, including invalid tactics, FP16 output,
non-TGV backends, and batch-invariant mode, are rejected.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [e12c193](https://github.com/flashinfer-ai/flashinfer/commit/e12c19376a66d7247a674415439645b295379739)

- **作者**: Stefano Castagnetta
- **时间**: 2026-11-20T23:28:03Z
- **提交信息**: feat(gemm): gathered-row BF16 x NVFP4 GEMV with scatter epilogue for SM12x (#9780)

## 📌 Description

Adds `flashinfer.gemv_bf16_fp4_gather` (also
`flashinfer.gemm.gemv_bf16_fp4_gather`), a CuTe DSL kernel for
SM120/121:

```
out[m, out_col_offset + row_ids[m, j]] = alpha * (a[m] @ dequant(b[row_ids[m, j]]))
```

- `a`: `(M, K)` bf16. `b`: `(R, K/2)` packed E2M1 (low nibble = even
column). `b_descale`: `(R, K/16)` E4M3 block scales in the linear layout
(from `fp4_quantize(..., is_sf_swizzled_layout=False)`), so each picked
row's scales are one contiguous read instead of 4-byte pieces spread
across a 128x4 block. `alpha`: optional `(1,)` fp32.
- `row_ids`: `(M, J)` int32/int64. Negative ids are skipped. Columns of
`out` that no id names are left untouched.
- `out`: `(M, N)` bf16/fp16/fp32 with unit inner stride (a strided row
view works). fp32 accumulation, one rounding at the store.
- CUDA-graph safe: no allocation, no host sync.

Use case: sparse LM heads for speculative decoding on bandwidth-bound
GPUs. Each draft token computes exact logits only for a dense prefix of
the vocabulary (a regular GEMM) plus `J` rows picked by a cheap scorer
and `flashinfer.top_k`. This op computes the picked rows and writes them
straight into the full-vocabulary logits tensor, so no separate scatter
kernel is needed. The consumer is the sparse draft head proposed in
vllm-project/vllm#67220.

Kernel: no SMEM, no tensor cores. A half-warp streams one row at a time
with 16B non-coherent loads (`cvt.rn.f16x2.e2m1x2` /
`cvt.rn.f16x2.e4m3x2` decode, fp32 FMA). The token's activation slice
stays in registers. Tokens are the fastest grid axis, so CTAs resident
at the same time cover the same slot range of every token. When ids are
ascending (both `torch.topk(sorted=False)` and `flashinfer.top_k` return
them mostly ascending), rows shared between tokens are served from L2.
That is where the large-M speedup comes from.

Out of scope: the dense prefix GEMM and the scorer (existing GEMMs) and
top-k (existing `flashinfer.top_k`).

Not a duplicate: open and closed PRs and issues were searched for gather
GEMV, fp4 gather, sparse lm_head, draft vocab, and scatter logits. No
overlapping work was found.

### Performance

DGX Spark (GB10, SM121). R = 215552 candidate rows, J = 16384 picks per
token, ids from `torch.topk(sorted=False)`, independent per token. K =
2048 and K = 2560 are the hidden sizes of Qwen3.6-35B-A3B and
Qwen3.8-Flash-Next (vocabulary 248320 minus a 32768-row dense prefix).

Against the Triton gather GEMV plus scatter that the vLLM prototype uses
today (CUDA graphs, inputs rotated to avoid L2 reuse, same node):

| K | M | Triton gather + scatter (us) | this op, including `-inf` fill
and dense-prefix copy (us) | speedup |
|---|---|---|---|---|
| 2048 | 1 | 103.5 | 83.1 | 1.25x |
| 2048 | 4 | 363.4 | 322.1 | 1.13x |
| 2048 | 8 | 662.7 | 578.7 | 1.15x |
| 2048 | 32 | 2323.6 | 1209.3 | 1.92x |
| 2560 | 1 | 130.8 | 110.0 | 1.19x |
| 2560 | 4 | 450.2 | 419.0 | 1.07x |
| 2560 | 8 | 831.7 | 741.2 | 1.12x |
| 2560 | 32 | 2806.3 | 1529.1 | 1.84x |

At M = 1 the op reads rows at 217 GB/s, against 234 GB/s for a read-only
reduction on the same GPU. At M = 32 it reads the 228 MB of distinct
rows in 1.12 ms. In a vLLM MTP serve (k = 4), M equals the number of
running requests and the op runs 4 times per decode step.

<details><summary>Against an unfused PyTorch path, with error vs
fp32</summary>

Run with `benchmarks/bench_gemv_bf16_fp4_gather.py` (median, L2 flushed
per iteration). The baseline is the PyTorch path: `index_select` the
rows, dequantize them to bf16, `bmm`, then `scatter_`. GB/s counts the
`M x J` rows requested, so above the DRAM rate it reflects L2 hits on
rows shared between tokens.

| K | M | this op (us) | PyTorch (us) | speedup | GB/s | max rel err vs
fp32 |
|---|---|---|---|---|---|---|
| 2048 | 1 | 90.1 | 7614 | 84x | 209 | 2.1e-3 |
| 2048 | 4 | 317.5 | 30170 | 95x | 238 | 2.0e-3 |
| 2048 | 8 | 544.9 | 60784 | 112x | 277 | 3.1e-3 |
| 2048 | 32 | 1109.0 | 240751 | 217x | 545 | 2.6e-3 |
| 2560 | 1 | 112.7 | 9535 | 85x | 209 | 2.5e-3 |
| 2560 | 4 | 403.5 | 37721 | 93x | 234 | 2.5e-3 |
| 2560 | 8 | 696.4 | 75968 | 109x | 271 | 3.1e-3 |
| 2560 | 32 | 1397.7 | 305145 | 218x | 540 | 3.0e-3 |

With ids from `flashinfer.top_k` instead (`--ids-from flashinfer`),
times are within 3% of the table (for example 88.2 us at K = 2048, M =
1, and 1428.5 us at K = 2560, M = 32). The max rel error is bf16 output
rounding.

</details>

`flashinfer.top_k` on the bf16 scorer output (`[M, 215552]`, k = 16384)
is 1.7x to 2.3x faster than `torch.topk` at M = 1 to 32. Its ~76%
ascending ids keep the L2 reuse above (within 1 to 3% of fully ascending
ids), so no sort is needed between the two ops.

### Testing

```
pytest tests/gemm/test_gemv_bf16_fp4_gather.py tests/trace/test_gemv_bf16_fp4_gather_reference_correctness.py
pytest tests/trace/test_template_init.py tests/trace/test_template_registry.py tests/trace/test_fi_trace_template_consistency.py -k gemv_bf16_fp4_gather
python benchmarks/bench_gemv_bf16_fp4_gather.py
```

Results on GB10 (SM121, CUDA 13.0, torch 2.14, nvidia-cutlass-dsl
4.8.0):

- 70 passed (gemm tests plus the trace reference test).
- 4 passed, 3 skipped (template init and consistency tests; the skips
are the CPU-only init smoke checks, which this SM12x-only init does not
support).
- 4 passed (`tests/trace/test_template_registry.py`).
- pre-commit clean.

- `tests/gemm/test_gemv_bf16_fp4_gather.py`: torch reference (LUT
dequantize, fp32 matmul, scatter into `-inf`). Covers K in {2048, 2560,
1056, 2080} (the last two exercise the partial-chunk tail), M in {1, 4,
5, 32}, int32/int64 ids, bf16/fp32 out, nonzero `out_col_offset`,
negative and duplicate ids, `alpha=None`, a strided `out` view, rows
from `fp4_quantize(..., is_sf_swizzled_layout=False)`, CUDA graph
capture and replay, and argument validation. Skipped unless SM12x.
- Trace template `gemv_bf16_fp4_gather` with reference, init, and a
reference-correctness test.
- Docs: `docs/api/gemm.rst`.

AI assistance (Claude) was used to write this change. The submitter
reviewed it and ran the tests and benchmark above on GB10.

## 🔍 Related Issues

- vllm-project/vllm#67220 (sparse draft LM head, the consumer of this
op)

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

Suggested CI test targets: `tests/gemm/test_gemv_bf16_fp4_gather.py
tests/trace/test_gemv_bf16_fp4_gather_reference_correctness.py
tests/trace/test_template_init.py tests/trace/test_template_registry.py
tests/trace/test_fi_trace_template_consistency.py`

## 🔬 Experimental Track

- [ ] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.
Tracking issue: #

## Reviewer Notes

- The op is gated to SM120/121 because that is where the sparse head
pays off: on bandwidth-limited GPUs like GB10 the draft lm_head is a
large share of the draft step. On datacenter GPUs we measured no
end-to-end gain from the sparse head, so SM100/103 is left out until a
use case exists.
- This is the same math as `mm_bf16_fp4`, with indexed rows and indexed
output columns. If maintainers prefer, it can instead become a gather
mode of `mm_bf16_fp4` (optional `row_ids` and output column offset),
with this kernel as its gathered-GEMV tactic.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added gathered-row BF16 × NVFP4 GEMV for SM12x GPUs. Compute results
for selected rows and scatter them into specified output columns;
negative row IDs are skipped, and unselected columns remain unchanged.
* The operation is available through the top-level FlashInfer package
and can be used with optional scaling.
* **Documentation**
* Added API guidance covering input formats, output placement, and
sparse speculative-decoding use cases.
* **Benchmarks**
* Added a benchmark to compare kernel performance and accuracy with a
PyTorch reference.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Stefano Castagnetta <scastagnetta@nvidia.com>

### [aac74db](https://github.com/flashinfer-ai/flashinfer/commit/aac74db18a99fa2e5b45a70d9dc1915b5540e450)

- **作者**: eigen
- **时间**: 2026-11-20T23:27:38Z
- **提交信息**: perf(cake_batch_deepgemm_fp8): masked pair program for large expected_m on 212-SM sm_107a (#9773)

This PR adds a masked pair program to
`batch_deepgemm_fp8_nt_groupwise(backend="cake")` for masked grouped FP8
inputs with packed UE8M0 scales on sm_107a. The program runs two CTAs
per cluster (`cta_group::2`), uses 256-row passes per group and has two
tile widths, w256 and w512. It never writes rows at or past `masked_m`.
It is used only on 212-SM sm_107a devices, for (N, K) = (4096, 7168) and
(7168, 2048) with G = 32 or 64. Plain weights switch to it at expected_m
72 (w256) and 320 (w512), and homed weights switch at expected_m 160. On
those rows it is faster than previous Cake (FlashInfer main,
`backend="cake"`): 1.15-4.32x with memory at 3186 MHz and 1.21-4.25x at
4752 MHz. Against DeepGEMM (`backend="deepgemm"`, plain weights) it is
0.95-1.84x and 0.95-1.77x, so a few rows at expected_m 72-128 are still
slightly slower. Every other problem keeps its current program,
including 216-SM devices, other shapes and smaller expected_m. Those
rows measure 0.997-1.005x and 0.995-1.011x with identical outputs.

The family's other Cake variants are the sm_107a swap-AB serving
programs (used at small expected_m), their locality-domain twins for
weights homed with `localize_weights`, and the serving programs on
sm_100a and sm_103a.

**Table 1. NVIDIA VR200 (sm_107a, 212 SMs), CUDA 13.5 (NVRTC 13.5.37),
driver 620.43, memory at 3186 of 4752 MHz. CUPTI device time, CUDA graph
replay, cold L2. Times are medians over 6 alternating rounds. Ratios are
the per-round median (min-max). Speedup = baseline time / this PR time
(>1 = this PR faster). M = rows per group as allocated. "uneven em" rows
draw each group's count as int(em x U(0.7, 1.3)). This table has no
homed rows because the memory-clock guard leaves weights unhomed on this
board. "-" = not applicable.**

| G | N | K | expected_m | M | previous Cake us | this PR us | DeepGEMM
us | speedup vs previous Cake | speedup vs DeepGEMM |
|---|---|---|---|---|---|---|---|---|---|
| 32 | 4096 | 7168 | 1 | 128 | 81.2 | 81.2 | 91.9 | 1.000 (0.999-1.001)
| 1.132 (1.130-1.134) |
| 32 | 4096 | 7168 | 8 | 128 | 82.5 | 82.6 | 92.1 | 1.000 (0.998-1.003)
| 1.114 (1.113-1.116) |
| 32 | 4096 | 7168 | 32 | 128 | 82.8 | 82.8 | 92.0 | 1.000 (0.999-1.002)
| 1.112 (1.111-1.113) |
| 32 | 4096 | 7168 | 64 | 128 | 95.9 | 95.9 | 92.0 | 1.000 (0.997-1.002)
| 0.959 (0.957-0.961) |
| 32 | 4096 | 7168 | 72 | 128 | 113.8 | 89.9 | 92.0 | 1.267
(1.263-1.268) | 1.024 (1.022-1.025) |
| 32 | 4096 | 7168 | 96 | 128 | 114.3 | 90.5 | 92.0 | 1.262
(1.261-1.267) | 1.017 (1.014-1.019) |
| 32 | 4096 | 7168 | 128 | 128 | 138.1 | 91.4 | 92.0 | 1.511
(1.510-1.511) | 1.006 (1.004-1.008) |
| 32 | 4096 | 7168 | 160 | 256 | 167.9 | 95.9 | 127.7 | 1.750
(1.748-1.751) | 1.331 (1.330-1.333) |
| 32 | 4096 | 7168 | 192 | 256 | 191.7 | 97.2 | 127.8 | 1.972
(1.970-1.975) | 1.315 (1.311-1.316) |
| 32 | 4096 | 7168 | 256 | 256 | 252.7 | 99.3 | 127.7 | 2.545
(2.540-2.546) | 1.285 (1.283-1.287) |
| 32 | 4096 | 7168 | 320 | 384 | 313.4 | 113.5 | 172.7 | 2.762
(2.750-2.772) | 1.522 (1.516-1.528) |
| 32 | 4096 | 7168 | 512 | 512 | 491.8 | 133.4 | 212.3 | 3.689
(3.659-3.698) | 1.593 (1.579-1.597) |
| 32 | 4096 | 7168 | 1024 | 1024 | 967.5 | 235.4 | 383.7 | 4.109
(3.863-4.256) | 1.631 (1.533-1.687) |
| 32 | 4096 | 7168 | 4096 | 4096 | 3895.6 | 901.6 | 1683.6 | 4.321
(3.652-4.420) | 1.836 (1.592-1.984) |
| 32 | 4096 | 7168 | uneven 128 | 256 | 150.4 | 92.6 | 116.4 | 1.625
(1.623-1.626) | 1.257 (1.256-1.259) |
| 32 | 4096 | 7168 | uneven 512 | 768 | 492.3 | 161.6 | 243.6 | 3.045
(3.016-3.056) | 1.507 (1.492-1.513) |
| 32 | 4096 | 7168 | uneven 4096 | 5376 | 3990.6 | 956.6 | 1759.8 |
4.172 (3.443-4.255) | 1.838 (1.485-2.456) |
| 32 | 7168 | 2048 | 1 | 128 | 43.5 | 43.6 | 49.8 | 1.000 (0.999-1.002)
| 1.146 (1.141-1.153) |
| 32 | 7168 | 2048 | 8 | 128 | 42.8 | 42.6 | 50.0 | 1.005 (1.003-1.009)
| 1.172 (1.163-1.177) |
| 32 | 7168 | 2048 | 32 | 128 | 42.8 | 42.7 | 50.0 | 1.003 (0.996-1.007)
| 1.171 (1.165-1.180) |
| 32 | 7168 | 2048 | 64 | 128 | 48.9 | 48.8 | 49.8 | 1.000 (0.993-1.006)
| 1.017 (1.012-1.029) |
| 32 | 7168 | 2048 | 72 | 128 | 58.4 | 50.5 | 49.9 | 1.157 (1.153-1.165)
| 0.987 (0.977-0.995) |
| 32 | 7168 | 2048 | 96 | 128 | 58.7 | 51.0 | 49.8 | 1.151 (1.146-1.158)
| 0.977 (0.969-0.985) |
| 32 | 7168 | 2048 | 128 | 128 | 72.1 | 52.3 | 49.8 | 1.379
(1.376-1.384) | 0.953 (0.945-0.960) |
| 32 | 7168 | 2048 | 160 | 256 | 87.7 | 55.2 | 68.7 | 1.592
(1.587-1.596) | 1.245 (1.242-1.256) |
| 32 | 7168 | 2048 | 192 | 256 | 103.7 | 56.4 | 68.6 | 1.838
(1.830-1.849) | 1.216 (1.209-1.221) |
| 32 | 7168 | 2048 | 256 | 256 | 136.2 | 58.6 | 68.6 | 2.326
(2.322-2.328) | 1.171 (1.168-1.173) |
| 32 | 7168 | 2048 | 320 | 384 | 168.0 | 72.3 | 89.2 | 2.325
(2.312-2.331) | 1.235 (1.227-1.240) |
| 32 | 7168 | 2048 | 512 | 512 | 263.5 | 87.1 | 110.7 | 3.025
(3.019-3.032) | 1.270 (1.265-1.274) |
| 32 | 7168 | 2048 | 1024 | 1024 | 520.9 | 142.0 | 197.2 | 3.669
(3.635-3.693) | 1.389 (1.376-1.396) |
| 32 | 7168 | 2048 | 4096 | 4096 | 2073.1 | 499.7 | 713.5 | 4.149
(3.838-4.349) | 1.437 (1.290-1.730) |
| 32 | 7168 | 2048 | uneven 128 | 256 | 77.8 | 53.0 | 59.0 | 1.467
(1.458-1.472) | 1.113 (1.106-1.118) |
| 32 | 7168 | 2048 | uneven 512 | 768 | 265.8 | 92.7 | 124.3 | 2.873
(2.838-2.878) | 1.341 (1.327-1.348) |
| 32 | 7168 | 2048 | uneven 4096 | 5376 | 2119.6 | 519.0 | 730.5 | 4.089
(3.876-4.326) | 1.416 (1.336-1.601) |
| 64 | 4096 | 7168 | 1 | 128 | 157.9 | 157.8 | 178.5 | 1.001
(0.999-1.001) | 1.131 (1.130-1.132) |
| 64 | 4096 | 7168 | 8 | 128 | 158.7 | 158.6 | 178.6 | 1.000
(1.000-1.002) | 1.125 (1.125-1.127) |
| 64 | 4096 | 7168 | 32 | 128 | 159.1 | 158.8 | 178.6 | 1.001
(1.000-1.002) | 1.124 (1.122-1.126) |
| 64 | 4096 | 7168 | 64 | 128 | 190.1 | 189.8 | 178.5 | 1.001
(1.000-1.002) | 0.941 (0.936-0.942) |
| 64 | 4096 | 7168 | 72 | 128 | 225.4 | 174.1 | 178.5 | 1.294
(1.293-1.297) | 1.025 (1.024-1.027) |
| 64 | 4096 | 7168 | 96 | 128 | 225.9 | 175.6 | 178.4 | 1.286
(1.283-1.290) | 1.016 (1.015-1.017) |
| 64 | 4096 | 7168 | 128 | 128 | 271.3 | 177.4 | 178.4 | 1.529
(1.528-1.532) | 1.006 (1.005-1.007) |
| 64 | 4096 | 7168 | 160 | 256 | 330.5 | 186.1 | 240.3 | 1.777
(1.774-1.778) | 1.292 (1.290-1.294) |
| 64 | 4096 | 7168 | 192 | 256 | 383.5 | 188.1 | 240.3 | 2.038
(2.036-2.039) | 1.277 (1.276-1.279) |
| 64 | 4096 | 7168 | 256 | 256 | 504.6 | 192.6 | 240.5 | 2.620
(2.620-2.623) | 1.249 (1.246-1.250) |
| 64 | 4096 | 7168 | 320 | 384 | 621.9 | 219.6 | 330.9 | 2.831
(2.573-2.834) | 1.507 (1.369-1.508) |
| 64 | 4096 | 7168 | 512 | 512 | 974.9 | 267.7 | 417.2 | 3.646
(3.337-3.781) | 1.560 (1.427-1.619) |
| 64 | 4096 | 7168 | 1024 | 1024 | 1932.4 | 481.1 | 744.1 | 4.017
(3.915-4.267) | 1.551 (1.500-1.791) |
| 64 | 4096 | 7168 | 4096 | 4096 | 7784.1 | 2285.8 | 3526.3 | 3.405
(3.331-3.462) | 1.552 (1.509-1.618) |
| 64 | 4096 | 7168 | uneven 128 | 256 | 296.1 | 180.2 | 211.4 | 1.643
(1.642-1.645) | 1.173 (1.171-1.178) |
| 64 | 4096 | 7168 | uneven 512 | 768 | 1002.1 | 314.1 | 465.7 | 3.190
(3.162-3.340) | 1.486 (1.469-1.557) |
| 64 | 4096 | 7168 | uneven 4096 | 5376 | 7711.6 | 2354.1 | 3545.6 |
3.275 (3.244-3.570) | 1.512 (1.483-1.657) |
| 64 | 7168 | 2048 | 1 | 128 | 81.0 | 81.1 | 94.5 | 0.998 (0.997-1.001)
| 1.165 (1.162-1.166) |
| 64 | 7168 | 2048 | 8 | 128 | 81.7 | 81.6 | 94.3 | 1.001 (1.000-1.003)
| 1.156 (1.154-1.160) |
| 64 | 7168 | 2048 | 32 | 128 | 81.5 | 81.5 | 94.2 | 1.000 (0.997-1.003)
| 1.155 (1.151-1.157) |
| 64 | 7168 | 2048 | 64 | 128 | 93.6 | 93.8 | 94.4 | 0.997 (0.991-1.000)
| 1.006 (1.000-1.010) |
| 64 | 7168 | 2048 | 72 | 128 | 112.8 | 93.4 | 94.5 | 1.208
(1.206-1.209) | 1.011 (1.008-1.014) |
| 64 | 7168 | 2048 | 96 | 128 | 113.3 | 95.1 | 94.5 | 1.192
(1.190-1.195) | 0.993 (0.991-0.998) |
| 64 | 7168 | 2048 | 128 | 128 | 142.8 | 97.4 | 94.5 | 1.466
(1.465-1.469) | 0.970 (0.967-0.972) |
| 64 | 7168 | 2048 | 160 | 256 | 174.6 | 102.6 | 127.4 | 1.702
(1.697-1.705) | 1.242 (1.239-1.243) |
| 64 | 7168 | 2048 | 192 | 256 | 207.8 | 105.0 | 127.4 | 1.980
(1.967-1.983) | 1.214 (1.211-1.217) |
| 64 | 7168 | 2048 | 256 | 256 | 272.2 | 109.3 | 127.3 | 2.489
(2.488-2.497) | 1.165 (1.163-1.167) |
| 64 | 7168 | 2048 | 320 | 384 | 335.3 | 127.1 | 166.3 | 2.636
(2.622-2.654) | 1.309 (1.296-1.315) |
| 64 | 7168 | 2048 | 512 | 512 | 525.5 | 159.3 | 207.9 | 3.299
(3.291-3.310) | 1.305 (1.301-1.308) |
| 64 | 7168 | 2048 | 1024 | 1024 | 1047.6 | 271.0 | 380.6 | 3.866
(3.644-3.998) | 1.405 (1.324-1.451) |
| 64 | 7168 | 2048 | 4096 | 4096 | 4248.0 | 1084.6 | 1745.2 | 3.923
(3.613-4.218) | 1.611 (1.494-1.767) |
| 64 | 7168 | 2048 | uneven 128 | 256 | 155.4 | 98.3 | 110.6 | 1.582
(1.572-1.587) | 1.126 (1.122-1.131) |
| 64 | 7168 | 2048 | uneven 512 | 768 | 537.4 | 174.5 | 232.8 | 3.080
(3.069-3.084) | 1.334 (1.329-1.337) |
| 64 | 7168 | 2048 | uneven 4096 | 5376 | 4205.2 | 1096.4 | 1758.4 |
3.837 (3.664-4.231) | 1.586 (1.526-1.854) |

**Table 2. NVIDIA VR200 (sm_107a, 212 SMs), CUDA 13.5 (NVRTC 13.5.37),
driver 620.70.06, memory at 4752 of 4752 MHz. CUPTI device time, CUDA
graph replay, cold L2. Times are medians over 6 alternating rounds.
Ratios are the per-round median (min-max). Speedup = baseline time /
this PR time (>1 = this PR faster). M = rows per group as allocated.
"uneven em" rows draw each group's count as int(em x U(0.7, 1.3)).
"homed" rows use `localize_weights(b)` for both sides. "-" = not
applicable.**

| G | N | K | expected_m | M | previous Cake us | this PR us | DeepGEMM
us | speedup vs previous Cake | speedup vs DeepGEMM |
|---|---|---|---|---|---|---|---|---|---|
| 32 | 4096 | 7168 | 1 | 128 | 83.2 | 83.2 | 87.6 | 1.000 (1.000-1.001)
| 1.052 (1.052-1.054) |
| 32 | 4096 | 7168 | 8 | 128 | 79.2 | 79.1 | 87.7 | 1.001 (0.997-1.003)
| 1.108 (1.104-1.111) |
| 32 | 4096 | 7168 | 32 | 128 | 79.8 | 79.7 | 87.6 | 1.002 (0.998-1.003)
| 1.099 (1.099-1.102) |
| 32 | 4096 | 7168 | 64 | 128 | 85.6 | 85.6 | 87.6 | 1.000 (0.998-1.000)
| 1.024 (1.023-1.025) |
| 32 | 4096 | 7168 | 72 | 128 | 107.8 | 84.3 | 87.7 | 1.279
(1.276-1.281) | 1.040 (1.039-1.042) |
| 32 | 4096 | 7168 | 96 | 128 | 108.2 | 84.9 | 87.7 | 1.274
(1.272-1.275) | 1.032 (1.031-1.033) |
| 32 | 4096 | 7168 | 128 | 128 | 135.2 | 85.8 | 87.7 | 1.577
(1.569-1.583) | 1.022 (1.020-1.023) |
| 32 | 4096 | 7168 | 160 | 256 | 163.6 | 92.6 | 122.7 | 1.767
(1.764-1.776) | 1.326 (1.321-1.333) |
| 32 | 4096 | 7168 | 192 | 256 | 187.8 | 93.1 | 122.8 | 2.016
(2.011-2.026) | 1.319 (1.313-1.326) |
| 32 | 4096 | 7168 | 256 | 256 | 247.7 | 94.9 | 122.8 | 2.610
(2.603-2.625) | 1.294 (1.288-1.301) |
| 32 | 4096 | 7168 | 320 | 384 | 307.1 | 109.6 | 167.3 | 2.802
(2.693-2.827) | 1.526 (1.467-1.539) |
| 32 | 4096 | 7168 | 512 | 512 | 483.6 | 134.1 | 206.1 | 3.607
(3.590-3.663) | 1.538 (1.529-1.562) |
| 32 | 4096 | 7168 | 1024 | 1024 | 956.1 | 225.0 | 373.6 | 4.248
(4.227-4.279) | 1.661 (1.648-1.733) |
| 32 | 4096 | 7168 | 4096 | 4096 | 3826.9 | 987.3 | 1734.6 | 3.877
(3.519-4.262) | 1.768 (1.600-1.929) |
| 32 | 4096 | 7168 | uneven 128 | 256 | 146.4 | 88.1 | 111.2 | 1.661
(1.657-1.666) | 1.262 (1.259-1.263) |
| 32 | 4096 | 7168 | uneven 512 | 768 | 484.2 | 146.1 | 235.7 | 3.314
(3.285-3.331) | 1.613 (1.600-1.623) |
| 32 | 4096 | 7168 | uneven 4096 | 5376 | 3922.5 | 1029.5 | 1825.9 |
3.811 (3.458-4.028) | 1.754 (1.615-1.879) |
| 32 | 7168 | 2048 | 1 | 128 | 43.6 | 43.5 | 46.6 | 1.001 (1.000-1.006)
| 1.072 (1.065-1.078) |
| 32 | 7168 | 2048 | 8 | 128 | 41.8 | 41.4 | 46.6 | 1.008 (1.004-1.012)
| 1.125 (1.116-1.133) |
| 32 | 7168 | 2048 | 32 | 128 | 41.8 | 41.5 | 46.6 | 1.005 (1.003-1.008)
| 1.121 (1.115-1.127) |
| 32 | 7168 | 2048 | 64 | 128 | 44.4 | 44.3 | 46.2 | 1.004 (1.000-1.005)
| 1.042 (1.037-1.046) |
| 32 | 7168 | 2048 | 72 | 128 | 57.6 | 46.9 | 46.1 | 1.228 (1.222-1.245)
| 0.984 (0.978-0.990) |
| 32 | 7168 | 2048 | 96 | 128 | 57.8 | 47.7 | 46.2 | 1.214 (1.207-1.221)
| 0.968 (0.964-0.973) |
| 32 | 7168 | 2048 | 128 | 128 | 74.1 | 48.7 | 46.2 | 1.521
(1.519-1.529) | 0.949 (0.942-0.955) |
| 32 | 7168 | 2048 | 160 | 256 | 90.0 | 53.0 | 66.3 | 1.696
(1.685-1.706) | 1.250 (1.245-1.260) |
| 32 | 7168 | 2048 | 192 | 256 | 105.4 | 54.0 | 66.3 | 1.951
(1.940-1.961) | 1.228 (1.223-1.235) |
| 32 | 7168 | 2048 | 256 | 256 | 137.6 | 56.0 | 66.3 | 2.457
(2.442-2.469) | 1.183 (1.178-1.190) |
| 32 | 7168 | 2048 | 320 | 384 | 169.2 | 71.5 | 86.8 | 2.364
(2.347-2.380) | 1.214 (1.202-1.227) |
| 32 | 7168 | 2048 | 512 | 512 | 265.0 | 85.6 | 108.3 | 3.097
(3.087-3.128) | 1.265 (1.258-1.281) |
| 32 | 7168 | 2048 | 1024 | 1024 | 524.2 | 130.3 | 192.5 | 4.022
(3.953-4.051) | 1.477 (1.450-1.488) |
| 32 | 7168 | 2048 | 4096 | 4096 | 2070.9 | 504.9 | 794.3 | 4.099
(4.053-4.384) | 1.599 (1.532-1.724) |
| 32 | 7168 | 2048 | uneven 128 | 256 | 80.0 | 50.1 | 56.3 | 1.599
(1.596-1.601) | 1.124 (1.122-1.129) |
| 32 | 7168 | 2048 | uneven 512 | 768 | 267.7 | 92.7 | 120.9 | 2.887
(2.874-2.931) | 1.305 (1.298-1.323) |
| 32 | 7168 | 2048 | uneven 4096 | 5376 | 2123.4 | 525.0 | 822.3 | 4.045
(3.983-4.372) | 1.627 (1.532-1.743) |
| 64 | 4096 | 7168 | 1 | 128 | 165.0 | 164.8 | 170.3 | 1.001
(1.001-1.002) | 1.033 (1.032-1.034) |
| 64 | 4096 | 7168 | 8 | 128 | 153.5 | 153.5 | 170.4 | 1.000
(0.999-1.001) | 1.110 (1.108-1.112) |
| 64 | 4096 | 7168 | 32 | 128 | 155.0 | 154.7 | 170.3 | 1.001
(0.999-1.004) | 1.101 (1.098-1.103) |
| 64 | 4096 | 7168 | 64 | 128 | 167.5 | 167.5 | 170.3 | 1.000
(0.999-1.001) | 1.017 (1.016-1.018) |
| 64 | 4096 | 7168 | 72 | 128 | 209.4 | 164.2 | 170.2 | 1.275
(1.273-1.278) | 1.037 (1.036-1.038) |
| 64 | 4096 | 7168 | 96 | 128 | 210.7 | 165.4 | 170.4 | 1.274
(1.270-1.275) | 1.030 (1.028-1.032) |
| 64 | 4096 | 7168 | 128 | 128 | 266.7 | 166.9 | 170.3 | 1.598
(1.575-1.622) | 1.021 (1.019-1.022) |
| 64 | 4096 | 7168 | 160 | 256 | 320.2 | 178.3 | 229.2 | 1.795
(1.794-1.798) | 1.285 (1.282-1.288) |
| 64 | 4096 | 7168 | 192 | 256 | 373.7 | 179.8 | 229.2 | 2.079
(2.073-2.083) | 1.275 (1.271-1.279) |
| 64 | 4096 | 7168 | 256 | 256 | 492.7 | 182.9 | 229.0 | 2.694
(2.683-2.697) | 1.252 (1.247-1.255) |
| 64 | 4096 | 7168 | 320 | 384 | 607.5 | 219.5 | 319.2 | 2.767
(2.763-2.770) | 1.453 (1.452-1.456) |
| 64 | 4096 | 7168 | 512 | 512 | 958.0 | 269.4 | 404.6 | 3.559
(3.405-3.672) | 1.503 (1.437-1.556) |
| 64 | 4096 | 7168 | 1024 | 1024 | 1929.3 | 498.9 | 746.5 | 3.868
(3.726-4.124) | 1.535 (1.405-1.828) |
| 64 | 4096 | 7168 | 4096 | 4096 | 7670.9 | 2354.1 | 3580.2 | 3.259
(3.188-3.294) | 1.531 (1.465-1.564) |
| 64 | 4096 | 7168 | uneven 128 | 256 | 285.1 | 170.7 | 201.8 | 1.669
(1.668-1.673) | 1.182 (1.180-1.184) |
| 64 | 4096 | 7168 | uneven 512 | 768 | 986.6 | 296.8 | 451.2 | 3.326
(3.057-3.408) | 1.521 (1.400-1.571) |
| 64 | 4096 | 7168 | uneven 4096 | 5376 | 7609.9 | 2409.4 | 3566.0 |
3.158 (3.072-3.297) | 1.481 (1.431-1.541) |
| 64 | 4096 | 7168 | homed 64 | 128 | 160.2 | 160.2 | - | 1.000
(0.998-1.001) | - |
| 64 | 4096 | 7168 | homed 72 | 128 | 216.2 | 215.9 | - | 1.001
(1.001-1.002) | - |
| 64 | 4096 | 7168 | homed 96 | 128 | 217.3 | 217.1 | - | 1.001
(0.999-1.002) | - |
| 64 | 4096 | 7168 | homed 128 | 128 | 276.8 | 276.3 | - | 1.002
(1.001-1.002) | - |
| 64 | 4096 | 7168 | homed 160 | 256 | 339.0 | 253.8 | - | 1.335
(1.333-1.339) | - |
| 64 | 4096 | 7168 | homed 192 | 256 | 400.1 | 255.3 | - | 1.567
(1.565-1.568) | - |
| 64 | 4096 | 7168 | homed 256 | 256 | 522.9 | 258.4 | - | 2.025
(2.023-2.026) | - |
| 64 | 4096 | 7168 | homed 512 | 512 | 1007.8 | 340.4 | - | 2.961
(2.939-2.971) | - |
| 64 | 4096 | 7168 | homed 4096 | 4096 | 7909.1 | 2330.6 | - | 3.394
(3.248-3.416) | - |
| 64 | 7168 | 2048 | 1 | 128 | 83.3 | 83.7 | 88.0 | 0.995 (0.995-0.996)
| 1.051 (1.049-1.053) |
| 64 | 7168 | 2048 | 8 | 128 | 82.4 | 81.6 | 87.9 | 1.011 (1.007-1.013)
| 1.077 (1.076-1.082) |
| 64 | 7168 | 2048 | 32 | 128 | 81.4 | 81.6 | 88.1 | 0.998 (0.994-0.999)
| 1.079 (1.075-1.083) |
| 64 | 7168 | 2048 | 64 | 128 | 84.1 | 84.3 | 88.1 | 0.998 (0.996-1.001)
| 1.045 (1.042-1.049) |
| 64 | 7168 | 2048 | 72 | 128 | 108.3 | 86.2 | 88.1 | 1.257
(1.252-1.262) | 1.022 (1.018-1.026) |
| 64 | 7168 | 2048 | 96 | 128 | 109.8 | 87.7 | 88.0 | 1.252
(1.247-1.269) | 1.003 (1.002-1.007) |
| 64 | 7168 | 2048 | 128 | 128 | 144.9 | 89.9 | 88.2 | 1.613
(1.608-1.621) | 0.981 (0.980-0.985) |
| 64 | 7168 | 2048 | 160 | 256 | 175.1 | 96.2 | 121.9 | 1.819
(1.813-1.832) | 1.267 (1.260-1.274) |
| 64 | 7168 | 2048 | 192 | 256 | 207.8 | 98.3 | 121.8 | 2.111
(2.105-2.127) | 1.238 (1.231-1.248) |
| 64 | 7168 | 2048 | 256 | 256 | 272.3 | 102.8 | 121.6 | 2.650
(2.645-2.663) | 1.184 (1.178-1.191) |
| 64 | 7168 | 2048 | 320 | 384 | 335.6 | 125.4 | 160.3 | 2.676
(2.516-2.737) | 1.278 (1.203-1.307) |
| 64 | 7168 | 2048 | 512 | 512 | 528.7 | 156.0 | 201.7 | 3.386
(3.356-3.408) | 1.294 (1.280-1.300) |
| 64 | 7168 | 2048 | 1024 | 1024 | 1046.4 | 264.8 | 371.4 | 3.957
(3.787-4.150) | 1.405 (1.343-1.472) |
| 64 | 7168 | 2048 | 4096 | 4096 | 4232.1 | 1094.5 | 1785.4 | 3.865
(3.500-4.251) | 1.655 (1.476-1.785) |
| 64 | 7168 | 2048 | uneven 128 | 256 | 157.7 | 91.3 | 105.1 | 1.727
(1.720-1.731) | 1.150 (1.145-1.153) |
| 64 | 7168 | 2048 | uneven 512 | 768 | 540.5 | 168.8 | 225.3 | 3.197
(3.178-3.227) | 1.335 (1.324-1.346) |
| 64 | 7168 | 2048 | uneven 4096 | 5376 | 4178.2 | 1071.4 | 1802.2 |
3.899 (3.609-4.057) | 1.684 (1.544-1.818) |



<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added an automatically selected masked pair-serving route for
supported FP8 batched matrix multiplication workloads.
* The route handles partial row groups while preserving output rows
outside the valid range, and selects between 256- and 512-row tiles
based on workload size.
  * Added support for SM107a kernels and launch plans.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [86ab1c7](https://github.com/flashinfer-ai/flashinfer/commit/86ab1c74561d1ae7ef70ece38f2c34007848d030)

- **作者**: Akaash Parthasarathy
- **时间**: 2026-11-20T23:24:49Z
- **提交信息**: feat(moe_ep): add NCCL EP 0.3 controls and compatibility fixes (#9623)

<!-- .github/pull_request_template.md -->

## 📌 Description

Update SplitMoE's `nccl_ep` transport to `nccl-extensions>=0.2.0`, which
ships NCCL EP 0.3.0. These changes apply to SplitMoE with `nccl_ep`;
native MegaMoE's communication and kernels are unchanged.

Added controls and support:

- Group top-k and SM budgets: `num_topk`, `max_num_sms`, and independent
`dispatch_num_sms` / `combine_num_sms`.
- HT flow selection: `ht_flow="auto" | "push_pull" | "pull_push"`.
- HT metadata exchange: `meta_exchange_policy="auto" | "require_fused" |
"force_scan"`.
- HT eager receive sizing: `eager_recv=True` sizes FI's receive arrays
from the actual received-row count. It requires host synchronization,
cannot be captured, and can increase the provider's staging reservation.
- LL Rank-Major persistent receive windows: `dispatch_zero_copy=True`
registers receive storage for direct dispatch. Warmup is collective and
receive geometry must stay fixed.
- Quantized dispatch forwarding: `dispatch_quantization="forward"` sends
quantized values and scale rows separately through NCCL's FWD recipe.
The SplitMoE adapter passes received MXFP8 scales into expert compute.
- Experimental LL Rank-Major NVFP4 combine:
`combine_quantization="nvfp4"` compresses BF16 expert outputs for return
communication and produces BF16 token results. This is lossy
communication, independent of expert weight precision.
- LL hidden sizes 3072 and 3584, including automatic candidate
preflight, when the loaded EP library is 0.3 or newer.

The controls live in `FleetAlgoKnobNcclEpConfig`. Eager sizing and
receive windows default to `False`; dispatch/combine quantization
default to `"none"`. Unset tuning controls leave selection to the
provider. [The integration
note](https://github.com/akaashrp/flashinfer/blob/nccl-ep-03-integration/docs/design_docs/moe_ep_nccl_ep_03.md)
covers supported formats, layouts and lifetimes.

Compatibility and lifetime fixes:

- Use the C ABI for mask query/update and retain pinned mask inputs
until their asynchronous copies finish.
- Preserve captured receive allocations, check capture on the operation
stream, and give eager sizing per-handle counters and correctly
initialized receive arrays. Reject unsupported transport/scale
combinations at initialization.
- Validate topology replacements before teardown and reject use after
replacement failure until retry. Keep fault-tolerance settings fixed for
a Fleet, release FI-owned communicators/windows, and retain allocator
callbacks.
- Update dependency/container defaults, fix the nested-uv install
deadlock, and prefer the selected NCCL wheel over an older system
library.

## 🔍 Related Issues

None.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks on changed files with `pre-commit run --files
...`.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] Affected host tests pass. GPU validation is described below.

Host checks on the rebased source: **274 passed, 84 GPU-dependent cases
skipped**. Changed-file hooks pass. Both default EP container recipes
built in the earlier package qualification and reported Extensions 0.2.0
/ EP 0.3.0.

GPU qualification at `853aefb30` on four SM107 GPUs passed **53
regressions and seven complete-forward variants on every rank**, with no
skipped cases. Runtime code and multi-rank test bodies are unchanged by
the host-test consolidation. Coverage includes LL and both HT flows,
real MXFP4/MXFP8 expert compute, changed-input, route-ID and
routing-weight graph replay, eager sizing, empty receivers, windows,
communicator ownership and NVFP4 codec checks. Lossless cases use a 1%
same-format global-reference bound; NVFP4 uses a 2% explicit-scale
codec-reference bound. Cleanup passes. Replay checks assert receive
ownership, every scale block, current expert IDs, empty receivers and
actual mask readmission.

In an earlier synthetic BF16 operator case on four SM107 GPUs
(H2048/I1024/E16/top-k4, 64 tokens/rank, capacity 512), eager sizing
reduced receive payload/routing arrays from **8.09 to 1.01 MiB/rank**.
The uncaptured, host-completed forward with `pull_push` increased from
**295.01 to 418.11 us** in that single sweep. This measures FI's receive
arrays, not provider staging or total process memory.

A peer-loss probe completed ten forwards on each of three survivors in
eager and captured execution, checked against a reference that excludes
failed-rank contributions. Normal LL group destruction then blocked in
the provider's barrier across the original communicator. That barrier is
present in both EP 0.2 and EP 0.3. Full failure/restart recovery is not
qualified.

- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
      Reason: targeted MoE EP coverage is sufficient.

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/cpu/moe_ep/nccl_ep
tests/cpu/moe_ep/test_split_graph_state.py tests/moe_ep/nccl_ep
tests/moe_ep/test_ep_selection.py
tests/moe_ep/test_nccl_ep_release_multirank.py
tests/moe_ep/test_nccl_ep_dispatch_window_multirank.py
tests/moe_ep/test_nccl_ep_native_quantization_multirank.py
tests/moe_ep/test_split_fused_moe_kernel_vs_reference.py`

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

Deferred: HT Expert-Major and HT MXFP8 combine, HT window paths, AFD
roles, prepared-handle import, fused DeepSeek FP8 dispatch quantization,
an overflow-policy selector, and a grouped-expert caller API. CUDA 12,
other LL JIT sizes and opt-in CFT/NUCS remain unqualified. NVFP4 is
lossy; passing its codec reference does not establish model quality.

AI assistance: Codex.

### [6973c5a](https://github.com/flashinfer-ai/flashinfer/commit/6973c5ad2e55492e3fe26d8959c7426912848bdf)

- **作者**: Vincent
- **时间**: 2026-11-20T23:14:57Z
- **提交信息**: feat(batch_invariant): non-causal mode of the batch-invariant attention class (#9285)

## 📌 Description

This PR adds the non-causal mask mode to the batch-invariant attention
class of #8590, as a second class dimension next to the head dim:
`BatchPrefillWithPagedKVCacheWrapper` /
`BatchPrefillWithRaggedKVCacheWrapper` with `batch_invariant=True` now
accept `causal=False`, and `BatchDecodeWithPagedKVCacheWrapper` runs the
non-causal class for `q_len_per_req > 1` with `is_causal=False` (a
single query token per request sees every key either way and stays on
the causal class).

**Why.** RL rollouts and scoring passes also run non-causal attention
(encoder-style blocks, bidirectional prefix / multi-item scoring,
reward-model heads, speculative-decoding drafters); until now
`batch_invariant=True` refused `causal=False` outright. The non-causal
row has the same tiles, chunks, online softmax and chunk merge as the
causal one; only the visible set a token gets from the request metadata
differs (`[0, kv_len)` instead of `[0, p]`, or `[max(0, p -
window_left), p]` with a window), so it is the same dataflow with a
different term per token, i.e. a different class with its own
fingerprint, not a per-call input.

**What the flag guarantees.** Under either class a token's output bits
depend on its head, the input values and either its KV position and
window (causal) or its request's key count (non-causal) alone: R1
run-to-run determinism, R2 batch invariance (batch size, neighbours,
position in the batch, page table, SM count), R3 configuration agreement
(every ring depth, unit kind, softmax warpgroup count, fold placement,
launch grid and kernel body), R4 cross-path agreement (non-causal
prefill == multi-token non-causal decode for the same token; paged ==
ragged). The causal fingerprints are unchanged and the causal kernels
keep their names (the mode is a compile-time constant and the non-causal
bodies are separate objects, `*_nc`).

**Kernels.** No new body: the row body, the Swaps-AB decode body and the
split-KV fixup take the mode as a constexpr; under the non-causal mode
every row's visible range is the request's whole key range (the masking
of the causal row at the last position with no window), the planner
gives every row block the chunk and tile range of `kv_len`, and the
chunk fold recomputes each row's present chunks from `kv_len`. The mode
sits on top of the prefill and Rubin placements of #9301 and #9622: the
launch grid, the unit order, the pairing and the launch dependencies
work from each unit's tile and chunk counts, which the planner sets per
mode, so they needed no mode switch. The mode is a keyword-only argument
of every kernel, planner and engine signature that takes it, so a later
trailing flag cannot bind to it positionally.

**API changes a caller can see.**
* **Prefill `plan()` default.** The prefill wrappers' `plan()` defaults
to `causal=False`. That call used to raise under `batch_invariant=True`
and now runs the non-causal class; pass `causal=True` for the causal
class. The `batch_invariant` docstrings say so.
* **Receipts.** `fingerprint(<prefill wrapper>, head_dim=...,
causal=...)`: `causal` is now a required dimension for the two prefill
wrappers (omitted or `None` raises, naming the two classes), because
their `plan()` default is the non-causal class. For the decode wrapper
it stays optional and omitted / `None` is the causal class, as
`is_causal=None` is in its `plan()`. Non-causal receipts are
`attn-bf16-d<D>-nc-*`.
* **Workspace sizing.** `workspace_size()` under `batch_invariant=True`
sizes the plan of the mask mode `plan()` will run, so it takes the same
mode: the paged prefill wrapper forwards `causal`, and the decode
wrapper's `workspace_size()` gains `is_causal` (appended, default
`None`, same rule as `plan()`). Sizing raises the same typed
`BatchInvariantUnsupportedError` as `plan()` for inputs the class
refuses, instead of a planner assertion.
* **Chunked prefill.** Under the causal class a request cut into chunks
reproduces the one-shot bits. Under the non-causal class only query
chunks planned over the request's full key set do; a chunk run while the
KV is still growing is that chunk's view of the keys present at the
time.

**Lean.** `lean/BIKernels/Attention.lean` carries the mode: the dataflow
reads a row only through its visible range, so the causal term ignores
the key count and the non-causal term ignores the position (proved),
R1-R4 hold for both classes, prefill == multi-token decode is stated for
the non-causal one, and `output_depends_on_mode` separates the two
classes on a toy row; four non-causal toy cases (every head dim, partial
last tiles) join the generated cases.

**Generated Lean cases are split per kernel family.** The first commit
regroups the generated `Cases.lean` into
`BIKernels/Cases/<Family>[N].lean` modules with `Cases.lean` as an
umbrella that imports them; the content is the same, line for line. Each
case is one theorem holding a whole spec term as a literal, and with the
four new cases the single file went past the per-file size limit of the
internal mirror, so the mirror could not take the branch. The generator
cuts a family into numbered parts at declaration boundaries, removes
only stale files that carry the generated marker, and the added-file
size check of pre-commit exempts these modules.

**Supported:** everything of #8590 plus non-causal prefill (paged and
ragged; any `q_len` against at least one key per request) and non-causal
multi-token decode. **Refused** (typed `BatchInvariantUnsupportedError`,
nothing falls back): a `window_left >= 0` with `causal=False` (a
windowed non-causal row is a further class, left to a follow-up), a
request with query tokens and no key (a row without a visible key), and
a `forward()` whose `causal` disagrees with the planned class.

## 🔍 Related Issues

Follows #8590 (the batch-invariant attention class) and #8361 (the
mode); merged over #9301 and #9622 (the placements). Tracked in #9009.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

- [x] Tests have been added or updated as needed:
`tests/attention/test_batch_invariant_attention.py` (bitwise unless
noted): non-causal reference accuracy, paged and ragged, including
`q_len > kv_len`; paged == ragged; non-causal prefill == multi-token
non-causal decode and position independence; batch / permutation /
sub-batch invariance; configuration agreement over the whole space,
including the paired placements; query chunks over the full key set ==
one shot; multi-token decode on the Swaps-AB body (the plan is asserted
to take it); a multi-chunk request with more query tokens than keys
under split units with the fixup, in-kernel and automatic merges;
workspace sizing of both classes through the prefill and decode wrappers
(a buffer of exactly `workspace_size()` bytes keeps the split plan, a
smaller one falls back to fused units with the same bits) and its typed
errors; the fingerprint as a function of `(head_dim, causal)` with the
causal ones pinned unchanged, required for prefill and optional for
decode; the refusals; the single-token decode step as the causal class
whatever `is_causal` says. `tests/batch_invariant/test_lean.py` covers
the regenerated, split cases and the generator's cleanup of stale
generated modules.
- [x] All tests are passing:
`tests/attention/test_batch_invariant_attention.py` 161 / 161 on SM107
and 159 passed, 2 skipped on SM103 (B300);
`tests/batch_invariant/test_lean.py` 5 / 5 (`lake build`, conformance,
axioms: 0 sorry, 0 violations). SM100 is covered by CI.
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>

### [bc69e52](https://github.com/flashinfer-ai/flashinfer/commit/bc69e528ef216bb7b827e27704595d5decbc9b5b)

- **作者**: feih-nv
- **时间**: 2026-11-20T23:14:05Z
- **提交信息**: fix(comm): memory clobbers on the NVLink one-sided all-to-all fences (#9649)

## 📌 Description

The NVLink one-sided all-to-all kernels fence with inline PTX before
signalling peers (dispatch: `fence.release.sys`) and after observing
their flags (combine: `fence.acquire.sys`; `fence.acq_rel.sys` below
sm_90). The `asm volatile` statements had no `"memory"` clobber, so the
compiler was free to move the flag and payload accesses across the
fence. This adds the clobber to the four statements. Port of
NVIDIA/TensorRT-LLM#22388 (b3d78c5c8), by the kernel-sync controller's
triage.

## 🔍 Related Issues

NVIDIA/TensorRT-LLM#22388.

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

- [ ] Tests have been added or updated as needed. (None: see below.)
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/comm/test_cake_moe_alltoall.py
tests/comm/test_cake_moe_alltoall_multi_gpu.py
tests/comm/test_mnnvl_memory.py`

No test is added: a missing `"memory"` clobber is an
instruction-ordering hazard that a functional test cannot trigger
deterministically, and no behavior change is expected from today's
compilers. The multi-GPU all-to-all tests above are the regression
coverage; not run locally (single GPU).

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

Four one-token changes in
`csrc/nv_internal/tensorrt_llm/kernels/moe/communication/moeAlltoAllKernels.cu`;
same change as upstream.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved synchronization handling for multi-GPU communication
operations. No user-facing features or behavior changes are included.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [f922669](https://github.com/flashinfer-ai/flashinfer/commit/f92266907449b03c6ad8f6a0bc088f7ad00d63c5)

- **作者**: Jimmy Zhou
- **时间**: 2026-11-20T22:51:34Z
- **提交信息**: test(gdn): take the cuDNN GDN forward's checkpoint series by index (#9801)

## Problem


`tests/gdn/test_batch_invariant_gdn_stateless.py::test_train_states_are_the_series_the_cudnn_backward_takes`
fails on every GPU with cuDNN Frontend 1.33:

```
ValueError: too many values to unpack (expected 3)
```

The test calls cuDNN Frontend's own forward op,
`torch.ops.cudnn.gated_delta_net_fwd`, and unpacks its result into three
values. In Frontend 1.33 the op returns five: the output, the final
state, the checkpoint series, then two new outputs. This is the same
added-output change that #9765 handled in FlashInfer's library code. No
FlashInfer code calls this op, so only the test is affected.

## Fix

Take the third output (the checkpoint series) by index instead of
unpacking. Index 2 is the checkpoint series on both 1.32 and 1.33.

## Validation

The test needs a GPU and cuDNN Frontend with GDN backward support;
scoped CI below runs it.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Tests**
* Updated cuDNN forward comparison tests to support additional outputs
while preserving checkpoint shape and value checks.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: jimmzhou <jimmzhou@nvidia.com>

### [1ffd937](https://github.com/flashinfer-ai/flashinfer/commit/1ffd93754e179fa3ac5f37556ad529a3b7256a69)

- **作者**: Akaash Parthasarathy
- **时间**: 2026-11-20T22:51:16Z
- **提交信息**: refactor(moe_ep): organize kernel sources and refresh Blackwell/Hopper (#9740)

<!-- .github/pull_request_template.md -->

## 📌 Description

Separate MegaMoE kernel sources from FlashInfer adapters and refresh the
Blackwell and Hopper implementations.

- Group sources under
`moe_ep/kernels/{cutedsl_megamoe,kimi_k3,cake,flashinfer}/`. Mirror the
CuTe DSL provider's `sources/` and `pre_unification/` layout, with one
copy of the shared runtime in each tree.
- Move adapters to `moe_ep/shims/<sm>/<implementation>/`. Keep backend
registration under `backends/mega/kernel/<sm>/<dtype_backend>/` and
leave `csrc/` and `include/` unchanged.
- Refresh Blackwell standard and GenPhase, retaining N64,
batch-invariant arithmetic, supported finalization modes and initialized
scale padding. Preserve the existing Rubin integration and the retained
NVFP4 route's opt-in NVLS barrier from #9389.
- Reconcile Hopper at the canonical source paths, retaining hybrid FP4,
grouped/deduplicated return, batched pulls and SM90 reduction. Keep the
provider's 128-channel FC2 activation-scale default; FI explicitly
requests its existing 64-channel behavior.
- Keep a combined `VENDOR.md` and export manifest, with separate
SM90/SM100/SM107 `TUNING.md` files beside the adapters. SM120
split/swap-AB drops retain their own records under
`kernels/flashinfer/`.
- Fix migrated weight and reference helpers, finalizer setup, and
affected tests and examples.

```text
moe_ep/
├── kernels/
│   ├── cutedsl_megamoe/{sources,pre_unification}/
│   ├── cake/
│   ├── kimi_k3/
│   └── flashinfer/
├── shims/<sm>/<implementation>/
└── backends/mega/kernel/<sm>/<dtype_backend>/
```

**Import and selector changes:** Direct imports and module commands
using `kernel_src/` or `cute_dsl/megamoe/` must use the documented
replacement paths. SM100's unsuffixed NVFP4/MXFP8 selectors now use
`sources/`; the retained NVFP4 implementation uses `_legacy`. BF16/BF16
and BF16/MXFP8 keep their selectors. Remove `_next`, `nvfp4_cutedsl` and
`mxfp8_cutedsl`. Compatible former-next tuning records keep their
identities; removed legacy MXFP8 records do not apply to the
replacement.

Production tuning grids are unchanged. The Blackwell measurements and
methodology are in its tuning notes. GPU qualification compares both
revisions against independent references and exercises graph replay,
masked routes, finalization and batch-invariant paths on Blackwell,
Rubin and Hopper. These are kernel/adapter checks, not a new full-model
serving result.

## 🔍 Related Issues

Follows #9426 and preserves the batch-invariant integration from #9417
and #9454.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks on the changed files and fixed any reported
issues.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] Affected host tests and the selected Blackwell/Rubin/Hopper GPU
qualification pass.
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: target the MoE EP CPU and GPU suites for the moved
implementations.

Installed-wheel imports and repeated exports pass. The retained NVFP4
barrier passes four-GPU eager and CUDA-graph checks with NVLS enabled,
disabled and forced to fall back. GPU comparisons include matched timing
controls; Hopper is within 0.8% at fixed settings. One Rubin tuning run
selected a slower existing tactic; replaying the same settings on both
revisions differs by less than 0.22%. Existing SM120 failures reproduce
on the baseline.

Suggested CI targets: `tests/cpu/moe_ep tests/moe_ep`

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


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Expanded MegaMoE with inter-node communication, relay routing,
shared-expert execution, and additional scheduling and reduction
options.
* Standard SM100 NVFP4 and MXFP8 selectors no longer require the `_next`
suffix; GenPhase remains selectable.
* Added standard NVFP4 weight preprocessing and an instrumentation tag
for tuning-cache identity.
  * Added configurable FC2 activation scaling for Hopper FP8 workloads.
* **Changes**
* Removed the legacy SM100 MXFP8 backend and the short NVFP4/MXFP8
selector aliases.
* Updated MegaMoE package organization and migration, tuning, and
environment-variable documentation.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [3424a3a](https://github.com/flashinfer-ai/flashinfer/commit/3424a3a11c29ea7149258384126eaf34af92cb74)

- **作者**: Lee Nau
- **时间**: 2026-11-20T21:14:02Z
- **提交信息**: fix(autotuner): re-rank rank_tactics shortlists when the tactic pool changes (#9790)

<!-- .github/pull_request_template.md -->

## 📌 Description

#9289 added `TunableRunner.get_tactic_cache_key(inputs)` so that
`choose_one()` compares a runner's tactic pool again when the pool
changes under the same identity. It deliberately left `rank_tactics(k >
1)` alone. That path reuses a process-local shortlist when only the
measurement policy matches, so a runner whose pool grows from `[1, 3]`
to `[1, 3, 2]` keeps returning the old shortlist, and tactic 2 is never
ranked. Compound runners that rank each stage with `rank_tactics(k > 1)`
(the MoE stage searches in `fused_moe/runners.py`, cuDNN Frost tuning)
would never see the new tactics.

This PR closes that gap:

- `rank_tactics` reads the runner's signature **before enumeration**, as
`choose_one()` does, and stores it with each shortlist next to the
measurement policy.
- A shortlist is reused only when **both** the policy and the signature
match. Otherwise the stage is ranked again and the shortlist replaced.
- A pool that grows during preparation is ranked again on the next pass,
because the stored signature is the one read before enumeration.
- Runners returning `None` (all production runners today) keep the
existing reuse based on identity alone.
- **Capture:** a shortlist miss during an outer CUDA Graph capture
inside `autotune(True)` now fails before input synthesis, as
`choose_one()` already does. Previously it synthesized inputs into the
caller's graph, every tactic then failed its capture check, and the call
returned `[-1]`, so the caller silently got the fallback. This was
already true of any miss during capture. This PR adds signature changes
as a new cause of misses, so it's fixed here. A warm hit with an
unchanged signature is still returned during capture.
- The distributed path is unchanged in structure. The existing all-ranks
agreement on shortlist hits now also covers a rank whose signature
changed, so every rank re-ranks together.

Shortlists stay in memory for the process only; nothing is persisted, so
there is no cache-format change. The change in
`flashinfer/autotuner/autotuner.py` is about 15 lines of logic, plus
comments and the hook docstring; `docs/autotuning.rst` is updated to
match.

## 🔍 Related Issues

Follow-up to #9289, from the approving review there, which asked for
signature-aware `rank_tactics(k > 1)` shortlist reuse and one real
backend adopter before a compound backend relies on the contract. The
backend adopter is tracked separately in #9789.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

The hooks pass on the four changed files (`pre-commit run --files ...`);
the full repository was not run.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: the change is limited to the autotuner's shortlist cache;
targeted autotuner tests cover it.

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/cpu/autotuner tests/autotuner`

"All tests are passing" stays unchecked until upstream CI has run.

**New tests:**
- `test_rank_tactics_reranks_when_signature_changes[v1|managed]`: the
pool grows from `[1, 3]` to `[1, 3, 2]` under the same identity, so the
shortlist is ranked again (`[3, 1]` → `[2, 3]`). With an unchanged
signature, the shortlist is reused with no input synthesis, tactic
enumeration or profiling.
- `test_rank_tactics_signature_changed_by_preparation_reranks`: the pool
grows during preparation, and the next pass ranks it again.
- `test_rank_tactics_without_signature_keeps_shortlist`: a `None`
signature keeps today's reuse.
- `test_rank_tactics_shortlist_miss_fails_during_capture`: during
capture, an unchanged shortlist is returned, and a changed pool raises
without input synthesis or profiling.
-
`test_cache_hit_disagreement_reprofiles_together[2|4-ranked_partial_signature]`:
real local Gloo processes, where only rank 0's signature changed since
an identical shortlist was stored, and every rank re-ranks.
- The existing distributed cases that seed shortlists directly
(`ranked_*`, `rejected_shortlist_*`) now seed the `(policy, signature)`
identity, so they still test what they were written for instead of
missing for the wrong reason.

**Upstream CI:** public PR Test passed on `9529806e7`, before the
capture fix. To be rerun on the current head.

**Local CPU validation on the current head** (main at `d91cc6c70`).
macOS arm64, Python 3.12.12, PyTorch 2.14.1, pytest 9.2.0. The tests run
against the production autotuner modules through the same CPU import
harness as #9289, where native helpers are stubbed to raise if called:

- **206 passed:** `test_autotuner_tactic_coverage.py` (24 cases),
`test_autotuner_configs.py`, `test_tuning_protocol.py` and
`test_autotune_cache_v2.py`. The two
`test_pcie_lookup_without_tune_group_*` cases were deselected because
they import native JIT modules the harness cannot provide.
- **6 passed:** the coverage cases from
`tests/autotuner/test_autotuner_core.py`, run as a verbatim extract.
- **49 passed:** `test_autotuner_distributed.py`, deselecting the three
`test_preparation_memory_error_*` cases for the same native-import
reason.
- **Negative controls:**
- The three signature tests in `test_autotuner_tactic_coverage.py` fail
on `main` (`d91cc6c70`), and the `None` test passes there.
- The capture test fails on this PR's first head (`9529806e7`), before
the guard was added.
- On `main` the distributed case passes for an unrelated reason: `main`
stores the policy alone, so the new seed always misses. Its control is
therefore this branch with the signature forced to `None` in
`rank_tactics`, where both world sizes fail.
- `test_autotune_replay_coverage.py` and `test_autotune_audit.py` also
exercise `rank_tactics`, but import native modules at collection, so
they need CI.

No GPU, kernel, measurement-policy or performance change is claimed.

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

- **Where the capture guard sits.** It's inside the existing
input-preparation `try`, not directly after the hit check. A single
process still raises immediately. In distributed tuning the error goes
through the coordinated preparation-error path
(`_sync_oom_across_tune_group`), so every rank raises together instead
of one rank leaving the others waiting in a collective. This matches
`choose_one()`.
- **Where the signature is read.** It's read once, before enumeration,
inside the same planning block whose errors are coordinated across
ranks. So a raising hook behaves like any other planning error in
distributed tuning.
- **Stored shape.** The shortlist cache value's first element changes
from `policy` to `(policy, signature)`. The cache is in memory only, and
the only readers are `rank_tactics` itself and the retirement path,
which pops by key. Shortlists from older code can't exist in a new
process.
- **Winners from ranking.** As before, the winner a ranking publishes
under `choose_one`'s key carries no candidate-coverage record. A later
signature-bearing `choose_one()` therefore re-tunes it rather than
trusting it. That is unchanged and conservative.

AI-assisted: drafted and validated with Claude Code.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Autotuning can refresh ranked tactic shortlists when a runner’s
available tactics change, while reusing them when the tactic pool and
measurement settings remain unchanged.
* **Bug Fixes**
* Ranked tactic selection no longer starts profiling on a shortlist miss
during CUDA Graph capture; it reports an error instead.
* **Documentation**
* Updated the autotuning guide with details on tactic-pool signatures,
shortlist reuse, and CUDA Graph capture behavior.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [30c14db](https://github.com/flashinfer-ai/flashinfer/commit/30c14dbea213e8693756b6e5913317cdd8f53da2)

- **作者**: helen ngo
- **时间**: 2026-11-20T20:47:48Z
- **提交信息**: Add Nemotron tanh clamped sqrelu to TRTLLM path (#7496)

<!-- .github/pull_request_template.md -->

## 📌 Description

- Add BF16 and MXFP8 ClampedRelu2 support to the TRTLLM MoE backend.
- Fuse `(s * tanh(relu(x) / s))²` into the FC1 epilogue using per-expert
FP32 scales.

This is the TRTLLM equivalent of the PR for the CUTLASS path found here:
https://github.com/flashinfer-ai/flashinfer/pull/5696

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
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added ClampedRelu2 activation support for routed fused MoE with
matching BF16 or MXFP8 activation and weight formats.
* ClampedRelu2 requires a clamp limit and does not accept alpha or beta
parameters. It is unavailable with DeepSeek FP8 and staged MoE.
* **Documentation**
* Updated activation guidance to describe ClampedRelu2 support and its
parameter requirements.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Helen Ngo <helenn@nvidia.com>

### [ffa8487](https://github.com/flashinfer-ai/flashinfer/commit/ffa8487dbdc25431ea23e73b32ec43c50f9360ec)

- **作者**: moonlightleaf
- **时间**: 2026-11-20T20:22:19Z
- **提交信息**: fix(fa3): prevent silent numerical errors in Hopper FP16/BF16 prefill (#6160)

<!-- .github/pull_request_template.md -->

## 📌 Description

Fix a **silent numerical correctness bug** in Hopper FP16/BF16 prefill.
When one MMA warp group finishes writing shared O later than another,
the preceding `arrive` and subsequent `sync` on the same barrier can
count arrivals twice and let readers copy stale values to the output.

Remove the extra arrival and retain the existing full-consumer sync.
Single, ragged and paged prefill share this epilogue; the math, layouts
and public API remain unchanged. See the [PTX barrier
contract](https://docs.nvidia.com/cuda/parallel-thread-execution/index.html#parallel-synchronization-and-communication-instructions-bar-barrier).

## 🔍 Related Issues

Related: #2111 changed the epilogue to synchronize all MMA consumers
while retaining the preceding arrival. This patch removes that
now-redundant arrival; it does not restore a separate producer protocol.

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

H200 / CUDA 13.0: the same controlled late-writer regression exercises
the production STSM and shared-to-global copy path, retaining every
production barrier.

| Source | Result | Target head: 32768 BF16 values expected to be +2 |
|---|---|---|
| Clean base `ea8135c` | **FAIL** at the output assertion | 8192 stale
-1 values |
| This fix | **PASS** | All 32768 values correct |

Both kernels completed and all other-head guards remained correct. On
the base, the reader accessed shared O before the delayed writer entered
STSM; with the fix, all delayed writers completed before the read.

```bash
python -m pytest -q tests/attention/test_hopper_epilogue.py
```

Also passed: 72 normal API configurations (single/ragged/paged,
FP16/BF16, D64/128/256, causal/noncausal, with/without LSE), four
worker-cleanup checks, and full-file pre-commit. The 72 configurations
completed in disjoint 32+40 runs; the original cold-JIT timeout is
retained. The full cross-architecture suite was not run. Upstream GPU CI
is pending authorization.

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

The FP8 quantized epilogue uses a separate single blocking sync and is
unchanged. A maintainer with CI permission can trigger `@flashinfer-bot
run` for the pending upstream GPU tests.

## Summary by CodeRabbit

* **Bug Fixes**
* Improved the reliability of attention results on supported Hopper
GPUs, including cases where shared-memory writes complete at different
times.
* **Tests**
* Added regression coverage that checks output values and write ordering
on supported hardware.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [1cbcb24](https://github.com/flashinfer-ai/flashinfer/commit/1cbcb24d577513ed9f337d6df4fff449aa2fe23d)

- **作者**: Jimmy Zhou
- **时间**: 2026-11-20T20:16:27Z
- **提交信息**: test(attention): decline the cuDNN paged auto plan with a soft cap, not FP16 (#9785)

## 📌 Description


`tests/attention/test_paged_query_lengths_contract.py::test_rejected_query_mask_preserves_accepted_plan[*-auto]`
fails on B200 with `DID NOT RAISE` (12 cases) since CI moved to cuDNN
Frontend 1.33.

How the test works:
1. It makes an accepted BF16 plan that `backend="auto"` sends to cuDNN.
2. It re-plans with input that the cuDNN auto rule declines, so the plan
falls back to FA2.
3. It expects FA2 to reject the independent query lengths (`seq_lens_q`)
with a `ValueError`, and checks that the earlier plan and its captured
CUDA graph are unchanged.

Step 2 used an FP16 query as the declined input. #9463 admits FP16 on
Frontend 1.33 and later (`_cudnn_supports_paged_fp16_auto`). So on 1.33
the FP16 plan goes to cuDNN, cuDNN accepts `seq_lens_q`, and nothing
raises. The library behaves as intended; only the test's choice of
declined input is out of date.

The fix declines the plan with `logits_soft_cap=30.0` instead. The auto
rule never sends a soft-capped plan to cuDNN (`logits_soft_cap == 0` is
one of its conditions) on any frontend version. Everything else in the
declined plan matches the accepted one: same dtype and the same
auto-backend resolution. So the test checks the same thing as before:
the rejection happens before any state of the accepted plan changes,
with no host sync.

## 🔍 Related Issues

A follow-up to #9463 and #9371. It shows up together with #9672, which
moved CI to Frontend 1.33.

## 🧪 Tests

- pre-commit passes (ruff check and format).
- Not run locally: the `[auto]` cases need SM100 (this host has an
L40S), so scoped CI on B200 validates the change.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Tests**
* Updated contract test coverage for query data types and plan options.
* Adjusted the rejected-plan scenario while preserving checks for the
error message and accepted plan.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: jimmzhou <jimmzhou@nvidia.com>

### [addb8a8](https://github.com/flashinfer-ai/flashinfer/commit/addb8a87c2581aaf95fe358681fce7c9179e743f)

- **作者**: Brian K. Ryu
- **时间**: 2026-11-20T20:11:39Z
- **提交信息**: perf(batch_invariant): sampling host overhead, precompile pools and kernel variants (#9695)

<!-- .github/pull_request_template.md -->

## 📌 Description

Follow-up to #9619 on the batch-invariant sampling kernels (`softmax` /
`log_softmax` / `log_probs`, `sampling_from_probs` /
`sampling_from_logits`, the five truncated samplers and the kept-set
`log_probs`). No kernel output changes: every entry under
`batch_invariant=True` returns the same bits as before, the default
paths are untouched. Three things change.

**1. Reduced host overhead.** Host us per call (bf16, medians over N in
{32768, 152064} x M in {1, 64, 512}; the host time is flat in N and M):

| entry | before | after | the operator's default path at M = 1
(kernels) |
|---|---|---|---|
| `softmax` / `log_softmax` | 17.1 | 15.7 | 12.4 (2) |
| `log_probs` | 34.3 | 18.1 | 19.1 (3) |
| `sampling_from_probs` / `_from_logits` | 22.6 | 18.9 | 19-20 (2) |
| `top_k_sampling_from_probs` / `min_p_sampling_from_probs` | 28.3 /
29.1 | 22.4 / 22.1 | 32 / 20 (2) |
| `top_p_sampling_from_probs` | 36.1 | 22.4 | 22 (2) |
| `top_k_top_p_sampling_from_probs` / `_from_logits` | 37.1 / 38.6 |
22.8 / 22.7 | 49 / 58 (3-4) |
| `log_probs(..., top_k / top_p)` (the kept set) | 43.2 | 19.6 | -- |

**2. Compile time.** The suites' precompile pools were serial. The three
kernel modules gain a `precompile(...)` entry beside
`get_compiled_kernel(...)` (through `jit.precompile`, the unlocked
`compile_and_persist()` path meant for parallel precompilation; nothing
is loaded) and the suites' workers call it: 259 s.
`get_compiled_kernel`, the serving path, keeps the lock, so concurrent
processes missing the same kernel still compile it once. The per-kernel
cost (1-4 s: about half the Python trace of the kernel body, half the
MLIR / ptxas pipeline) is unchanged.

**3. Kernel variants.** The convenience flags were compile-time
dimensions -- 16 variants of every truncated-sampler kernel (temperature
form x index gather x kept log-probability x PDL) and of every draw
kernel, 4 of every lse kernel -- and became runtime arguments where the
registers allow, which in the end is PDL alone: the lse kernels 4 -> 2,
the draw kernels 16 -> 8, the truncated samplers' probability kernels 16
-> 2 and their logits kernels 16 -> 8 (per dtype / Kp bucket / config /
input kind / filter set). The other dimensions were folded, measured,
and put back, each for a register reason (below). A folded flag is one
select or one predicated store per row, so the dataflow and the bits of
every row are those of the specialised kernel it replaces; PDL is a
runtime launch argument with the `griddepcontrol` instructions always
emitted (inert without the attribute). Two details decided the shape:

* In the truncated samplers a runtime index gather costs registers: the
gathered source row entering the row loader as a loaded value drove the
256-thread kernels from 111 to 197 registers (one CTA per SM instead of
two); applying the row once to the input pointer cured that at some
picks but still cost 50-90 registers on the 256-thread cluster picks
(0.59-0.92x at bf16 top-k 128256 / 152064 x 16 and top-p 128256 x 48-128
in this PR's review), because the row base is per-thread data instead of
a block-uniform value. The folded temperature form and kept-set
log-probability chain, compiled into every logits kernel, cost that
entry 2-8 % everywhere, 0.6x at the 256-thread two-CTA picks of
32769-65536 x 80-144 rows (122 -> 140-150 registers) and 1.7-2.2x with
`return_logprob=True` on B200. All three stay compile-time variants:
every kernel is register-identical to the merge-base's at every pick
probed.
* The draw's register-resident 512-thread kernel (152064 x 4096) holds
128 of its 128 registers with the host scale as a constant-bank operand;
a per-row scale costs one live register and the log-probability chain
two, and the variants carrying them spill (they were already 1.27-1.33x
slower than the plain kernel at that cell). Folded in, the plain path
inherited the spill (1.34x); the same fold cost the plain lse kernels
2-12 % (the dummy temperature's load and division on the critical path
before the sweep). Those two folds are not in: lse and draw keep the
temperature form, the gather and the log-probability output as
compile-time variants.

The kernel names and compile keys drop the folded dimensions;
`get_compiled_kernel` of the three kernel modules still accepts the
former flag arguments positionally (ignored where folded); the suites'
spec builders canonicalise the folded dimensions, so a
pool compiles each kernel once; the IR pins follow the dataflow
(`lg2.approx` iff a log-probability is formed, the temperature's
`div.rn` iff the per-row form,
`griddepcontrol` in every kernel).
### Performance

Graph-replay device time, cold L2, Rubin NVL8 (SM107), A/B/A against the
committed kernels (a frozen copy of the pre-change tree before and after
the changed tree, each in its own process and kernel cache):

| kernels | cells | geomean | min | max |
|---|---|---|---|---|
| truncated samplers (all four flags runtime; top-k, top-k + top-p,
top-p, min-p at 32768 x 4096, 152064 x 64, 152064 x 4096) | 12 | 1.00 |
0.91 (top-p 152064 x 64) | 1.036 (min-p 152064 x 4096) |
| lse (PDL runtime; softmax, softmax + per-row T, log_softmax,
log_probs, log_probs + per-row T at four points) | 20 | 1.001 | 0.991 |
1.011 |
| draw (PDL runtime; probs, probs + gather, logits, logits + per-row T,
logits + log-probability at four points) | 20 | 0.999 | 0.991 | 1.005 |

The truncated samplers' 152064 x 4096 cells carry +1.6-3.6 % (top-k 1400
-> 1422, top-k + top-p 1759 -> 1789, min-p 1218 -> 1262 us); every other
cell is within ±2.5 %.
## 🔍 Related Issues

<!-- Link any related issues here -->

#9009 
#9619

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

## Release Notes

* **Performance Improvements**
* Reduced redundant sampling-kernel compilation across runtime launch
settings.
* Improved sampling efficiency by reusing compatible inputs and cached
parameters, including scalar filters used across CUDA streams.
* **New Features**
  * Added an option to precompile sampling kernels.
* **Bug Fixes**
  * Improved handling of invalid gathered indices during row sampling.
* Sampling launch behavior now responds to programmatic dependent-launch
settings at runtime.
  * Improved consistency when cached filters are reused across streams.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [d91cc6c](https://github.com/flashinfer-ai/flashinfer/commit/d91cc6c70d2dd9b9dd34059b5a49be2916396a72)

- **作者**: Lee Nau
- **时间**: 2026-11-20T19:16:48Z
- **提交信息**: Track opt-in tactic pools in autotuning cache coverage (#9289)

<!-- .github/pull_request_template.md -->

## 📌 Description

A runner can keep the same identity while its tactics grow from `[1]` to
`[1, 2]`. #9144 records which runners a cached comparison covered, but
not which tactics, so it reuses tactic 1 without ever comparing tactic
2.

This PR adds an optional `TunableRunner.get_tactic_cache_key(inputs)`
signature to #9144's tuning-coverage metadata. It applies to
single-runner comparisons too. When the signature changes, tuning reruns
the comparison. When it is unchanged, the cached winner is reused
without input synthesis, tactic enumeration or profiling.

- The signature is checked only during tuning. It is stored in the
existing JSON and managed-cache coverage records, with no new schema.
Frozensets inside it are written as `frozenset({...})` with sorted
items, so the stored text doesn't depend on the per-process hash seed
and never matches an equal tuple.
- Coverage keeps the signature read before tactic enumeration. If
preparation grows a runner's pool, the next tune compares it again
instead of recording it as covered.
- Calls outside tuning, including CUDA Graph capture, never query it;
they keep using the last valid winner until the next tune. A capture
inside `autotune(True)` does check it, and a changed signature then
fails there like any other tuning miss, since profiling can't start
during capture.
- Returning `None` (the default) keeps today's behavior.

**No native backend opts in yet.** This PR proposes the opt-in runner
contract and its cache behavior. It does not detect arbitrary tactic
changes automatically. No kernel, measurement-policy or
serving-performance change is claimed.

Changes (4 files): the hook and coverage keys in
`flashinfer/autotuner/autotuner.py`, a section in `docs/autotuning.rst`,
the new `tests/cpu/autotuner/test_autotuner_tactic_coverage.py`, and one
added case in `tests/cpu/autotuner/test_autotuner_distributed.py`.

## 🔍 Related Issues

Follow-up to #9144 (merged as dd4d0f465); related to #9029. #9144 covers
runner-set changes. This PR covers a runner-declared tactic-pool change,
which #9144 deliberately left out of scope.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

The hooks pass on the four changed files (`pre-commit run --files ...`);
the full repository was not run.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: the change is limited to the autotuner cache path; targeted
autotuner tests cover it.

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/cpu/autotuner tests/autotuner`

"All tests are passing" stays unchecked until upstream CI has run on
this head.

**Upstream CI:** public PR Test passed on `5322d7b35` and on
`2e235863d`, including Targeted Unittest (H100) and CPU Unittest. To be
rerun on the current head.

**Local CPU validation on the current head** (`84f659692`, main merged
at `25bc267eb`). macOS arm64, Python 3.12.12, PyTorch 2.14.1, pytest
9.2.0. The tests run against the production autotuner modules through a
CPU import harness, where native helpers are stubbed to raise if called:

- **202 passed, 2 failed:** `test_autotuner_tactic_coverage.py` (19 new
cases: 14 lifecycle/persistence, plus 5 regression tests for the review
fixes), `test_autotuner_configs.py`, `test_tuning_protocol.py` and
`test_autotune_cache_v2.py`. The 2 failures are the
`test_pcie_lookup_without_tune_group_*` cases, which import native JIT
modules (`JitSpec`) that the harness cannot provide. They were excluded
in earlier runs for the same reason.
- **6 passed:** the coverage cases from
`tests/autotuner/test_autotuner_core.py`, run as a verbatim extract,
since that file imports native modules at load. The extracted functions
match the current file exactly.
- **47 passed, 3 failed:** `test_autotuner_distributed.py` with real
local Gloo processes, including the added two-/four-rank case where only
one rank's signature invalidates its comparison. The 3 failures are
`test_preparation_memory_error_falls_back_on_every_rank[*]`, which fail
on the same native import; they were excluded before for the same
reason.
- **Negative controls:** all 14 new lifecycle cases fail on unmodified
`main` (`25bc267eb`) with the same harness. The review-fix regression
tests fail on the heads they fix: the pre-enumeration and canonical-text
tests on `5322d7b35`, and the frozenset-versus-tuple reload tests (v1
JSON and managed) on `2e235863d`.
- **24-case independent matrix: 24/24 passed**, with 0 coverage gaps.
Each JSON seed and reload runs in a separate OS process.
- The merge of `main` (`5322d7b35`) resolved conflicts in which both
sides added #9144's lines, keeping this branch's hunks. After it, `git
diff upstream/main` was exactly this PR's own commit (`a0d477f3d`).

**Native GPU qualification (November 9, on the pre-merge source
`a0d477f3d`):** one H100 NVL, driver 580.196.07, Python 3.12.15 /
PyTorch 2.14.1+cu130, JIT-compiled native cuBLASLt BF16 GEMM. Container:
pinned SGLang
`lmsysorg/sglang@sha256:c1f4d9fc6fcf50c2269adbc757ce7b1778883af04155edb888fa9eea3b6648c0`.
A standalone **test-only adapter** declares the signature and forwards
enumeration and execution to the real native runner; no production
backend is opted in.

- **6/6 scenarios passed:** v1 JSON, nested v2 with JSON, and managed
v2, each with eager and CUDA Graph profiling. Each scenario ran a cold
seed, a tactic expansion and a warm reuse in three separate OS
processes: 18 processes, 36 shape-phase cases, at `M={32,128}, N=512,
K=1024`.
- The native pool grows from `[0]` to `[0,1,2]` under the same runner
identity. Both new tactics are actually profiled (v2 also profiles
`-1`), using real profiler timings. Expanded winners survive persistence
and a fresh-process reload, including cases where a new tactic won.
- **264 numerical comparisons passed**, including 108 CUDA Graph
replays, against FP32 Torch matmul with TF32 disabled (`atol=rtol=0.02`;
max abs error `0.007551`). Inputs change in place and outputs are
poisoned with NaN before every replay.
- All six warm processes ran **zero tuner profiling, input synthesis or
tactic enumeration**; the test fails if a warm lookup reaches those
paths.
- **6/6 controls on the #9144 head fail as expected:** the expanded
native tactics are never profiled.

This GPU run predates the merge and the review fixes, and `main`'s
autotuner has since changed (#9374, #9144 itself, #9472). It has not
been repeated. It is a bounded correctness and cache qualification, not
a performance comparison, full-model serving test, dynamic-bucket test,
distributed GPU test, or MXFP8/Blackwell/Rubin qualification. Scripts,
cache records and logs are preserved with source hashes; GPU archive
SHA-256
`02e2d0d7560e3cd141522d53255e834951e5ab3da812a9bf816b7309cba5b70e`.

**Not done yet:** upstream CI on this head; a production native-runner
opt-in, with its own workload and hardware qualification, before this
counts as a deployed backend fix. No serving-speedup claim.

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

The main question for review is whether to land the opt-in contract
before any production runner uses it. Adding a first adopter in this PR
is also an option.

On the hook's design:

- **Cost and side effects.** Calling `get_valid_tactics()` on warm hits
can build plans or invoke nested tuning. So this hook must be cheap,
side-effect-free and unchanged by input synthesis, and it must return
hashable values that are stable across processes. Exposing an
already-known catalog revision is the intended use.
- **Exact equality.** Any signature change, including a shrinking pool,
refreshes the comparison. Frozensets are canonicalized when persisted;
other values need a `str()` that is stable across processes.
- **Why not `get_cache_key_extras()`.** Using it for a pool revision
would also change the serving cache key. This signature only qualifies
the cached comparison during tuning, and it tracks changes to
non-winning candidates too.
- **Compatibility.** Runners returning `None` keep their current
candidate keys and behavior.

Out of scope here:

- invalidation of `rank_tactics(k > 1)` shortlists;
- reordered v2 default participation;
- the distributed fallback gap after the tuning context exits, inherited
from #9144;
- ranks that share one managed entry but hold different signatures: the
last writer's coverage wins, so after a restart the group re-profiles.
This wastes tuning time but never reuses an unmeasured winner.

The signature does not replace cache-key properties that numerical
correctness depends on.

AI-assisted: drafted and validated with Claude Code.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Autotuning can detect changes to a runner’s available tactics and
refresh comparisons, while reusing cached results when the tactic pool
is unchanged.
* Runners without tactic signatures retain existing cache behavior.
Lookup-only serving and capture can continue using a valid cached
winner.
* Tactic signatures are saved with cache coverage information and can be
used across tuner modes and cache reloads.
* **Documentation**
* Added guidance on providing tactic-cache signatures and how they
affect cache reuse and retuning.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: losewayy <104015127+losewayy@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [f4939b6](https://github.com/flashinfer-ai/flashinfer/commit/f4939b643263a7b5616006a8260a21b401d7e79e)

- **作者**: Ka-Hyun Nam
- **时间**: 2026-11-20T19:13:43Z
- **提交信息**: feat(batch_invariant): stateless call of the KDA class `kda.bf16.c16` (a trainer's forward pass) (#9676)

Follow-up to #9294. Three commits on `main`: the stateless call, the
state series it hands to a backward, and review fixes to the latter
(argument checks, docs and tests; run on B200, the GB300 and Vera Rubin
NVL72 rows below are from the commit before it).

## What it adds

`flashinfer.recurrent_kda(..., batch_invariant=True)` without
`initial_state` is now a stateless call: whole sequences, every one from
the zero state, rows only. It is the form a training forward takes, and
its rows are bit for bit the rows inference returns for the same
sequence.

```python
out = torch.empty_like(v)          # once per layer, reused every step
flashinfer.recurrent_kda(
    q, k, v, g, beta, A_log=A_log, dt_bias=dt_bias, lower_bound=-5.0, cu_seqlens=cu, output=out,
    use_gate_in_kernel=True, use_qk_l2norm_in_kernel=True, beta_is_logit=True, batch_invariant=True,
)
```

No new keyword, function or module. The inputs are the class's fused
contract as it is: packed `[1, T, H, 128]` with `cu_seqlens` or `[B, T,
H, 128]`, bf16 `q` / `k` / `v` / raw gate, bf16 beta logits, fp32
`A_log` and `dt_bias`, the same head counts (a multiple of 8, or 1 to
10, or 12).

### State before every 16-token chunk, for a backward

`checkpoint_every_n_tokens=16` makes the stateless call also write
`state_checkpoints` and return `(rows, None, state_checkpoints)`. These
are the entry's existing checkpoint arguments, until now refused by the
class; they stay refused with a pool, and so does
`checkpoint_state_indices`.

- Row zero of a sequence is its zero initial state, the next rows the
states before tokens 16, 32, ...; a sequence of `n` tokens has `ceil(n /
16)` rows, sequences in call order.
- In fp32 a row is bit for bit the pool's slot after a pool prefill of
that many tokens. In bf16 (the default) it is that state rounded. The
rows of the call do not change.
- This is the layout the cuDNN frontend's KDA backward reads on its
`state_checkpoints` port (bf16, 16-token cadence). On B200 with frontend
1.31.0 that backward, given this series in place of its own forward's,
returns gradients within 1.3e-4 relative of the ones from its own
series. Its own forward is not this forward (rows up to 1.2e-4 apart),
so this is the way to take that gradient at the states of the
batch-invariant forward.
- With a caller's `state_checkpoints` buffer and `checkpoint_cu_starts`
the call still allocates nothing. One bf16 row is 32 KB per head: 2 KB
per head and token, so 197 KB per token at 96 heads.
- Not measured: the time the export adds.

## What it guarantees

- Stateless forward == inference prefill, bitwise, per sequence, for any
batch composition, order and number of sequences. Since the class
already makes chunked prefill and decode equal to prefill, the rows are
also the chunked-prefill and decode rows.
- Every row comes from one launch of the class's prefill kernel on its
pinned route over the whole sequences, built without a state input and
without a state output. The step kernel is not involved, the last rows
of a sequence off a multiple of 16 included.
- No state pool, nothing kept next to a pool, no state returned.
`ssm_state_indices` and `output_final_state=True` raise the class's
typed error without `initial_state`.
- With `output=`, int64 `cu_seqlens` and contiguous inputs a call
allocates nothing on the device once its sequence count (packed) or `[B,
T]` (fixed layout) has been seen: this route has no workspace and writes
the caller's buffer. A test asserts the peak allocation does not move
across a call.
- Inference is unchanged: none of the sources the class fingerprint
digests is touched and the existing class tests pass.

## What it does not do

- **No backward in FlashInfer. The rows carry no `grad_fn`**, also when
an input requires grad (inputs are read as plain values). A trainer's
backward is its own, for example its existing differentiable op wrapped
in an `autograd.Function` whose forward returns these rows; what that
gradient is, and whether it is batch-invariant, is not this PR's claim.
- Zero initial state and whole sequences only. A sequence that has to
continue later is a pool call. The call cannot be captured in a CUDA
graph (it raises).
- It is the same kernel source and route as the pool prefill but another
build of it (state arguments compiled out), so the equality with the
pool calls is measured, not structural. The tests below compare it
bitwise on SM100, SM103 and SM107.
- A packed call is preceded, as a pool prefill is, by the prefill
kernel's device-side ordering of the sequences. That step is sized for
serving batches and its time grows with the square of the sequence
count: with 4096 sequences in one call it costs more than the rows (last
rows of the table).
- The prefill kernel keeps its own metadata between calls (one int32 per
sequence for each sequence count seen; offsets and order per `[B, T]` in
the fixed layout). That cache lives in a file the fingerprint digests
and is left alone.
- More than 65535 sequences in one call is not checked by the entry.

## Behaviour change to look at

A `batch_invariant=True` call without `initial_state` used to raise. It
now runs when none of the other state arguments is passed, so a decode
step that drops its pool gets first-token rows instead of an error. A
caller that passes `ssm_state_indices` still gets the typed error. One
assertion of `tests/kda/test_batch_invariant_recurrent_kda.py` changes
with it ("a call without a pool raises" becomes "slots without a pool
raise").

Also: a non-finite `scale` is now a typed error for every call of the
class, and the call bumps the autograd version of `output` because the
kernel writes it directly (so one `output` buffer per layer).

## Tests

`tests/kda/test_batch_invariant_kda_stateless.py`, every comparison
bitwise: stateless rows against the pool prefill of each sequence alone
and of the packed batch (96, 12 and 8 heads; lengths 1 to 1000 including
15, 16, 17 and other lengths off a multiple of 16; steep and long
gates), against chunked prefill cut at multiples of 16, against a
prefill cut anywhere and continued by decode steps, against decode from
the first token, across batch subsets, orders and up to 300 sequences,
head counts 1, 3, 5, 9 and 10, fixed layout, repeats into a reused
buffer, inputs that require grad, strided and misaligned inputs, a
non-default scale and stream, no pool state created, a repeated call
allocating nothing, typed errors.

| Part | `test_batch_invariant_kda_stateless.py` |
`test_batch_invariant_recurrent_kda.py` + `test_kda_lean.py` |
`test_batch_invariant_gdn.py` + `test_gdn_lean.py` |
|---|---|---|---|
| GB300 (SM103), CUDA 13.0 | 85 passed | 137 passed, 1 skipped | 103
passed, 3 skipped |
| Vera Rubin NVL72 (SM107), CUDA 13.4 | 85 passed | 137 passed, 1
skipped | 103 passed, 3 skipped |
| B200 (SM100), CUDA 13.0 | 325 passed, 4 skipped (the five files in one
run) | | |

The seven checkpoint tests: every fp32 row against the pool's state
after a pool prefill of that many tokens (96, 12 and 8 heads), bf16
against fp32 rounded, rows unchanged, batch independence and the fixed
layout, a repeated call that allocates nothing and leaves further rows
alone, the refusals, and the cuDNN frontend's KDA backward fed with the
series (skipped where that frontend has no KDA backward; it ran on all
three parts).

Whole files with a fresh JIT cache. SM100 ran on a shared B200 only (no
timing from it).

## Performance

One KDA layer, head size 128, at 96 heads (Kimi K3) and at 12 heads (K3
at tensor-parallel 8). Wall clock of the whole call with a device
synchronize (median of 9) and CUPTI GPU time with a cold L2 cache.
Compared with FLA's `chunk_kda` forward (0.6.0; gate fused, `safe_gate`,
in-kernel l2-norm, beta sigmoid outside the op and inside the timed
call) and with this class's own prefill on a state pool. "Kept" is
memory that stays allocated between and after calls, inputs excluded;
"peak" adds the call's transients. A ratio above 1 means the stateless
call is faster.

| Part | Heads | Config (tokens) | Stateless fwd ms (wall / CUPTI) |
Pool prefill fwd ms (wall / CUPTI) | FLA chunk_kda fwd ms, grad on (wall
/ CUPTI) | FLA no_grad wall ms | FLA time / stateless time (wall) | Pool
time / stateless time (wall) | Kept KB/token: stateless / pool / FLA
grad on | Peak KB/token: stateless / pool / FLA |
|---|---|---|---|---|---|---|---|---|---|---|
| GB300 | 96 | 1x1024 (1024) | 0.31 / 0.25 | 0.61 / 0.59 | 1.13 / 1.37 |
1.12 | 3.6x | 1.94x | 24.0 / 35.0 / 97.1 | 24.0 / 59.0 / 289.1 |
| GB300 | 96 | 1x4096 (4096) | 0.44 / 0.38 | 0.67 / 0.68 | 1.59 / 1.70 |
1.61 | 3.6x | 1.52x | 24.0 / 26.7 / 97.1 | 24.0 / 50.7 / 289.1 |
| GB300 | 96 | 1x16384 (16384) | 1.10 / 1.04 | 1.40 / 1.43 | 4.54 / 4.62
| 4.54 | 4.1x | 1.27x | 24.0 / 24.7 / 97.1 | 24.0 / 48.7 / 289.1 |
| GB300 | 96 | 1x65536 (65536) | 3.78 / 3.73 | 4.42 / 4.45 | 17.39 /
17.49 | 17.37 | 4.6x | 1.17x | 24.0 / 24.2 / 97.1 | 24.0 / 48.2 / 289.1
|
| GB300 | 96 | 8x2048 (16384) | 0.88 / 0.83 | 1.23 / 1.26 | 4.38 / 4.46
| 4.37 | 5.0x | 1.39x | 24.0 / 29.5 / 97.1 | 24.0 / 53.5 / 289.1 |
| GB300 | 96 | 16 ragged, 24k (23970) | 1.07 / 1.03 | 2.28 / 2.42 | 6.23
/ 6.25 | 6.20 | 5.8x | 2.12x | 24.0 / 31.5 / 97.2 | 24.0 / 87.0 / 290.1
|
| GB300 | 96 | 64x512 (32768) | 1.53 / 1.47 | 2.30 / 2.34 | 8.29 / 8.34
| 8.27 | 5.4x | 1.51x | 24.0 / 45.9 / 97.1 | 24.0 / 69.9 / 289.1 |
| GB300 | 96 | 1024x64 (65536) | 5.28 / 5.30 | 11.44 / 11.51 | 17.00 /
17.15 | 16.97 | 3.2x | 2.17x | 24.0 / 199.6 / 97.1 | 24.0 / 223.6 /
289.1 |
| GB300 | 12 | 1x1024 (1024) | 0.25 / 0.20 | 0.46 / 0.51 | 1.05 / 1.25 |
1.07 | 4.2x | 1.86x | 3.0 / 4.4 / 12.6 | 3.0 / 7.4 / 36.6 |
| GB300 | 12 | 1x4096 (4096) | 0.43 / 0.38 | 0.58 / 0.61 | 1.11 / 1.30 |
1.07 | 2.6x | 1.33x | 3.0 / 3.3 / 12.1 | 3.0 / 6.3 / 36.1 |
| GB300 | 12 | 1x16384 (16384) | 1.09 / 1.04 | 1.31 / 1.32 | 1.67 / 1.79
| 1.65 | 1.5x | 1.20x | 3.0 / 3.1 / 12.1 | 3.0 / 6.1 / 36.1 |
| GB300 | 12 | 1x65536 (65536) | 3.78 / 3.71 | 4.00 / 4.04 | 4.69 / 4.78
| 4.66 | 1.2x | 1.06x | 3.0 / 3.0 / 12.1 | 3.0 / 6.0 / 36.1 |
| GB300 | 12 | 8x2048 (16384) | 0.32 / 0.27 | 0.56 / 0.52 | 1.26 / 1.41
| 1.24 | 3.9x | 1.75x | 3.0 / 3.7 / 12.1 | 3.0 / 6.7 / 36.1 |
| GB300 | 12 | 16 ragged, 24k (23970) | 0.37 / 0.32 | 1.01 / 1.22 | 1.47
/ 1.60 | 1.50 | 4.0x | 2.73x | 3.0 / 3.9 / 12.2 | 3.0 / 10.9 / 36.3 |
| GB300 | 12 | 64x512 (32768) | 0.41 / 0.35 | 0.74 / 0.78 | 1.84 / 1.88
| 1.75 | 4.4x | 1.78x | 3.0 / 5.7 / 12.1 | 3.0 / 8.7 / 36.1 |
| GB300 | 12 | 1024x64 (65536) | 1.18 / 1.14 | 2.93 / 2.90 | 3.10 / 3.18
| 3.06 | 2.6x | 2.48x | 3.0 / 24.9 / 12.1 | 3.0 / 27.9 / 36.1 |
| GB300 | 12 | 4096x16 (65536) | 5.98 / 5.93 | 12.09 / 12.16 | 6.82 /
6.95 | 6.78 | 1.1x | 2.02x | 3.0 / 90.8 / 12.1 | 3.0 / 93.8 / 54.1 |
| Vera Rubin NVL72 | 96 | 1x1024 (1024) | 0.14 / 0.11 | 0.25 / 0.24 |
0.50 / 0.52 | 0.48 | 3.5x | 1.73x | 24.0 / 35.0 / 97.1 | 24.0 / 59.0 /
289.1 |
| Vera Rubin NVL72 | 96 | 1x4096 (4096) | 0.28 / 0.25 | 0.40 / 0.39 |
0.91 / 0.91 | 0.90 | 3.3x | 1.42x | 24.0 / 26.7 / 97.1 | 24.0 / 50.7 /
289.1 |
| Vera Rubin NVL72 | 96 | 1x16384 (16384) | 0.81 / 0.78 | 0.98 / 0.98 |
2.79 / 2.80 | 2.78 | 3.4x | 1.21x | 24.0 / 24.7 / 97.1 | 24.0 / 48.7 /
289.1 |
| Vera Rubin NVL72 | 96 | 1x65536 (65536) | 2.94 / 2.91 | 3.32 / 3.32 |
10.81 / 10.88 | 10.80 | 3.7x | 1.13x | 24.0 / 24.2 / 97.1 | 24.0 / 48.2
/ 289.1 |
| Vera Rubin NVL72 | 96 | 8x2048 (16384) | 0.48 / 0.44 | 0.67 / 0.66 |
2.51 / 2.54 | 2.51 | 5.2x | 1.40x | 24.0 / 29.5 / 97.1 | 24.0 / 53.5 /
289.1 |
| Vera Rubin NVL72 | 96 | 16 ragged, 24k (23970) | 0.61 / 0.58 | 1.38 /
1.42 | 3.64 / 3.66 | 3.63 | 5.9x | 2.26x | 24.0 / 31.5 / 97.2 | 24.0 /
87.0 / 290.1 |
| Vera Rubin NVL72 | 96 | 64x512 (32768) | 0.87 / 0.84 | 1.31 / 1.30 |
4.85 / 4.88 | 4.85 | 5.6x | 1.50x | 24.0 / 45.9 / 97.1 | 24.0 / 69.9 /
289.1 |
| Vera Rubin NVL72 | 96 | 1024x64 (65536) | 3.14 / 3.15 | 6.69 / 6.71 |
10.02 / 10.12 | 10.01 | 3.2x | 2.13x | 24.0 / 199.6 / 97.1 | 24.0 /
223.6 / 289.1 |
| Vera Rubin NVL72 | 12 | 1x1024 (1024) | 0.15 / 0.12 | 0.25 / 0.24 |
0.51 / 0.51 | 0.48 | 3.4x | 1.66x | 3.0 / 4.4 / 12.6 | 3.0 / 7.4 / 36.6
|
| Vera Rubin NVL72 | 12 | 1x4096 (4096) | 0.28 / 0.25 | 0.38 / 0.38 |
0.57 / 0.59 | 0.55 | 2.0x | 1.37x | 3.0 / 3.3 / 12.1 | 3.0 / 6.3 / 36.1
|
| Vera Rubin NVL72 | 12 | 1x16384 (16384) | 0.81 / 0.78 | 0.93 / 0.92 |
1.17 / 1.19 | 1.16 | 1.4x | 1.15x | 3.0 / 3.1 / 12.1 | 3.0 / 6.1 / 36.1
|
| Vera Rubin NVL72 | 12 | 1x65536 (65536) | 2.94 / 2.91 | 3.12 / 3.11 |
3.82 / 3.83 | 3.81 | 1.3x | 1.06x | 3.0 / 3.0 / 12.1 | 3.0 / 6.0 / 36.1
|
| Vera Rubin NVL72 | 12 | 8x2048 (16384) | 0.19 / 0.16 | 0.30 / 0.30 |
0.70 / 0.71 | 0.69 | 3.6x | 1.56x | 3.0 / 3.7 / 12.1 | 3.0 / 6.7 / 36.1
|
| Vera Rubin NVL72 | 12 | 16 ragged, 24k (23970) | 0.24 / 0.20 | 0.57 /
0.61 | 0.98 / 1.01 | 0.97 | 4.1x | 2.40x | 3.0 / 3.9 / 12.2 | 3.0 / 10.9
/ 36.3 |
| Vera Rubin NVL72 | 12 | 64x512 (32768) | 0.22 / 0.18 | 0.40 / 0.39 |
1.14 / 1.15 | 1.12 | 5.2x | 1.82x | 3.0 / 5.7 / 12.1 | 3.0 / 8.7 / 36.1
|
| Vera Rubin NVL72 | 12 | 1024x64 (65536) | 0.78 / 0.75 | 1.89 / 1.91 |
2.08 / 2.10 | 2.07 | 2.7x | 2.42x | 3.0 / 24.9 / 12.1 | 3.0 / 27.9 /
36.1 |
| Vera Rubin NVL72 | 12 | 4096x16 (65536) | 4.68 / 4.69 | 8.74 / 8.77 |
4.09 / 4.15 | 4.09 | 0.9x | 1.87x | 3.0 / 90.8 / 12.1 | 3.0 / 93.8 /
54.1 |

- Against FLA at 96 heads: 3.2x to 5.8x faster on GB300, 3.2x to 5.9x on
Vera Rubin NVL72. At 12 heads: 1.2x to 4.4x and 1.3x to 5.2x, except
4096 sequences of 16 tokens (1.1x on GB300, 0.9x on Vera Rubin NVL72),
where the sequence-ordering step dominates.
- Against the class's pool prefill: 1.06x to 2.7x faster (no slot
read-back, no separate launch for the last rows, no copy into `output`).
- Memory: the stateless call keeps the output buffer only and its peak
equals that. The pool prefill keeps 117 KB per head and sequence slot on
top; FLA with grad on keeps 97 KB per token at 96 heads and peaks at 289
KB per token.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Batch-invariant KDA supports stateless sequence processing from zero
state, returning output rows without retaining final state or producing
gradients.
* Optionally return FP32 state checkpoints before each 16-token chunk.
Checkpoints are available only for stateless calls; they cannot be used
with a state pool or a different interval.
* Calls without a state pool can return output rows, but pool-dependent
options remain unsupported.
* **Documentation**
* Updated API and README guidance for stateless calls, checkpoints, and
state-pool limitations.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>

### [e219228](https://github.com/flashinfer-ai/flashinfer/commit/e2192284bf3d8c74a78f2a113b184540f8c056d3)

- **作者**: nv-yunzheq
- **时间**: 2026-11-20T19:04:34Z
- **提交信息**: perf(sampling): single-launch cluster top-p renorm for SM103 serving shapes (#9598)

<!-- .github/pull_request_template.md -->

## 📌 Description
On compute capability 10.3 (B300 / GB300), some
`top_p_renorm_probs(probs, top_p)` calls now run on a
thread-block-cluster kernel inside the existing API. A call qualifies
when all of these hold:

* `probs` are float32 rows, `top_p` is a per-row float32 tensor, and
`is_deterministic=False`;
* its `(batch_size, vocab_size)` is on the allowlist: 17 serving rows,
batch 4..68 over vocab 154880 / 248320.

Every other call keeps the AIR top-p kernels.

Why: the AIR path runs five kernels and applies with one 1024-thread CTA
per row. The small batches of speculative-decoding verify (a few to a
few dozen rows over a 150K–250K vocabulary) therefore occupy a handful
of SMs and read each row several times.

The new kernel:

* uses one cluster of 16 CTAs per row (8 for short rows) and streams
each row once;
* resolves the nucleus exactly with 64-bit fixed-point masses: a fast
path over the entries ≥ 2^-8, otherwise an exact 12/11/9-bit radix
select;
* writes every output element.

`top_p_renorm_probs` is the only entry point. The dispatch lives in the
private module `flashinfer/_top_p_renorm_specialized.py`, next to its
allowlist `top_p_renorm_probs_specialized_workloads.json`

### Scope, guard, kill switch, numerics

* **Guard order:**
  1. the kill switch;
  2. `is_deterministic`;
  3. a tensor `top_p`;
  4. dtypes;
  5. 2-D/1-D contiguous shapes;
  6. the allowlist;
  7. 16-byte alignment;
  8. CUDA device;
  9. compute capability exactly (10, 3).

The module is never built inside a CUDA-graph capture. A failed build or
launch falls back to the stock path.
* **Kill switch:** `FLASHINFER_SPECIALIZED_KERNEL_DISABLE=1`, read on
every call and documented in `docs/development/environment_variables.md`
(main moved the environment-variable table there from CLAUDE.md).
* **Diagnostics:**
* On SM103: a one-time dispatch line, a kill-switch line and per-reason
fallback lines, written to the `flashinfer.jit` logger and to stderr.
* On every other device: nothing on stderr; the lines go to the logger
at DEBUG.
  * Counters: `_top_p_renorm_probs_specialized_stats()`, private.
* **Numerics:** same semantics as the stock path.
* Keep p ≥ the threshold of the shortest descending prefix whose mass
reaches top_p; ties are kept.
  * A zero target keeps the row maximum.
* A row whose kept mass is ≤ 1e-8 is left unnormalised, like the AIR
apply pass. The kernel decides this on the exact kept mass: when its
64-bit fixed-point sum is within its rounding bound (V · 2^-57) of the
cutoff, it re-sums the kept entries in float64. A row that sums to about
1 never gets that close, so served rows pay one integer comparison.
* No fast math. 64-bit fixed-point accumulation. Deterministic outputs.

### performance
5x - 21x kernel-level performance improvement across targeted cases. 2%
ITL improvement on GB300, Qwen/Qwen3.5-397B-A17B-FP8, SGLang v0.5.20, 2
nodes

note: in allowed list, 54 × 154880 runs at about 0.8x of AIR when the
nucleus reaches below 2^-8. But it rarely happens with real data.

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

* **New Features**
* Added a specialized top-p renormalization path for supported workloads
on compute capability 10.3 with float32 inputs and nondeterministic
sampling. Calls that don’t meet its requirements continue to use the
existing AIR path.
* Setting `FLASHINFER_SPECIALIZED_KERNEL_DISABLE=1` keeps top-p
renormalization on the AIR path.
* **Documentation**
* Clarified that the disable setting applies to the specialized top-p
path.
* **Tests**
* Added coverage for dispatch conditions, fallback behavior, launch
planning, and numerical results.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [2866539](https://github.com/flashinfer-ai/flashinfer/commit/28665393925f29b10b74500a0615457041d84c53)

- **作者**: Wookje Han
- **时间**: 2026-11-20T19:02:01Z
- **提交信息**: feat(moe): routing tile query for routed FP4 MoE routing metadata (#9745)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->
1. The routed TRTLLM-Gen FP4 MoE runs two steps in sequence: routing
metadata, then the expert GEMMs.
2. A caller might want to build the metadata itself and pass it in
(`routing_metadata=`) for optimization such as overlap with another
stream or kernel fusion
3. The metadata is based on `tile_N`, so the caller needs the tile the
call will run. Today that means copying FlashInfer's tile heuristic, and
with autotuning the tile is only in the tuner's cache.

This PR adds `trtllm_fp4_block_scale_moe_routing_tile_n(...)`. It
returns the tile `trtllm_fp4_block_scale_routed_moe` runs with the same
arguments:
- the autotuned tactic's tile, if the tuner has one for this call;
- otherwise the tile an untuned launch runs: the first tile of the
launcher's fallback order whose default config is valid and loads (C++
`trtllm_fp4_moe_default_tile_n`), or `None` if no tile can run.

```python
tile_n = trtllm_fp4_block_scale_moe_routing_tile_n(topk_ids, hidden_states, ...)  # same args as the call
meta = trtllm_moe_allocate_routing_metadata_multi_tile(..., tile_ns=(tile_n,))
# populate meta.slots[0], then
trtllm_fp4_block_scale_routed_moe(..., routing_metadata=meta.slots[0])
```

### Details
- The query and the op build the runner and tuning config with one
helper, `_fp4_moe_runner_and_tuning_config`, and the query looks up with
`AutoTuner.choose_one`, so it hits the same cache key. Outside tuning,
`choose_one` is a lookup and never profiles.
- It takes the call's arguments that feed the cache key, under the same
names. Activations are read for shape and dtype only, so they may be
`meta` tensors (routing before quantization).
- Inside `autotune()` it returns the untuned tile: tune with the
ordinary call, build metadata outside tuning.
- The native lookup caches its runners per device and arch, as the
launcher does.

## 🧪 Tests

`tests/moe/test_trtllm_fp4_routed_moe_routing_metadata.py` (1 / 64 / 960
tokens, `do_finalize` on/off):
- untuned: the slot runs `[tile_n, -1]`, bitwise equal to the ordinary
call;
- tuned: the query (with `meta` activations) returns the tuned tile, and
the slot runs exactly the tuned `[tile_n, config]`, bitwise equal to the
ordinary tuned call;
- fallback: when the default tile cannot run, the query returns the next
tile in the fallback order (or `None`), and that slot matches the
ordinary call.

SM107: this file 109 passed; `test_trtllm_gen_routed_fused_moe.py` 373
passed, 2 skipped; `test_trtllm_gen_moe_autotune_tactics.py` 95 passed;
`test_trtllm_moe_valid_dims.py` 38 passed. pre-commit is clean.

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

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).
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
* Added a query for the tile used by routed FP4 MoE operations,
including those with precomputed routing metadata.
* The query reports the tuned tile when available; otherwise, it selects
a supported default fallback or returns no tile if none can run.
* Made the query available through the public fused MoE package
interface. It accounts for operation settings and device support when
reporting the selection.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [1c5e136](https://github.com/flashinfer-ai/flashinfer/commit/1c5e136f0bf92d0e6c05d0deffa87bddfdf3b84d)

- **作者**: eigen
- **时间**: 2026-11-20T18:39:45Z
- **提交信息**: perf(mla): Cake MLA decode in backend="auto" and a split-KV route (#9779)

### [863d666](https://github.com/flashinfer-ai/flashinfer/commit/863d666a5c76f8c717f20bafc585d22f5b92055d)

- **作者**: oiiai-oiiai
- **时间**: 2026-11-20T17:53:24Z
- **提交信息**: fix(autotuner): apply the tactics blocklist to cache-file entries (#8768)

## 📌 Description

The tactics blocklist (`FLASHINFER_TACTICS_BLOCKLIST`) is only applied
to the candidate tactics of a fresh profiling run. Entries loaded from
an autotune cache file (`load_configs` / `autotune(cache=...)`) are
never checked against it, so a cache tuned before a tactic was listed
keeps serving that tactic. A known-bad or non-deterministic tactic
therefore stays in use after it is blocklisted.

## 🔍 Changes

- `TacticsBlocklist.is_blocked(custom_op, runner_name, tactic)`:
single-entry check sharing `filter`'s key and tactic normalisation.
- `AutoTuner._drop_blocklisted_file_configs`: drops loaded entries whose
tactic is listed, remembers their keys so `save_configs` does not write
the on-disk entry back while its tactic is still blocklisted (a
permitted tactic re-tuned by another writer in the meantime survives),
and logs how many entries were dropped and why.
- `load_configs` drops listed entries on load; the file-config lookup
drops them on first use when the blocklist is loaded after the cache
file. A dropped entry is a cache miss: re-profiled without the listed
tactics inside a tuning context, default tactic (-1) otherwise. Replay
reports record the miss as `blocklisted_tactic`.
- No new flags or environment variables. The managed v2 store and
bundled legacy `.py` configs are not filtered by this PR (same class of
issue; can follow up if wanted).

## 🔍 Related Issues

Related to the tactic-selection work in #7207 (same autotuner area,
independent change).

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

Suggested CI test targets: `tests/autotuner/test_tactics_blocklist.py
tests/autotuner/test_autotuner_core.py
tests/autotuner/test_autotune_cache_v2.py`

`tests/autotuner/test_tactics_blocklist.py::TestBlocklistCacheFiles`
(CPU, fake profiling): blocklist loaded before the cache file, blocklist
loaded after the cache file, unlisted entries still hit, dropped entry
not revived by `save_configs`, a permitted winner written by another
writer survives a later `save_configs`, `is_blocked` unit test. All four
fail on main without the fix. Existing autotuner suites
(`test_tactics_blocklist.py`, `test_autotuner_core.py`,
`test_autotune_cache_v2.py`, replay coverage, cache scope) pass on CPU.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Cached configurations using blocked tactics are excluded whether the
blocklist is loaded before or after the cache.
* Lookups for excluded configurations are reported as cache misses, and
saving no longer restores blocked entries.
* Saving preserves a permitted replacement written by another process,
even if the original cache entry was blocked.
* Cache configurations with unhashable tactics remain usable, while
blocked tactics continue to be filtered.
  * Blocklist checks now handle unhashable tactics consistently.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [377335b](https://github.com/flashinfer-ai/flashinfer/commit/377335b87916a1d4a5d848cff376fd483648e6f9)

- **作者**: Jimmy Zhou
- **时间**: 2026-11-20T14:45:20Z
- **提交信息**: fix(cudnn): accept the fourth linear-attention output from cuDNN Frontend 1.33 (#9765)

## 📌 Description

cuDNN Frontend 1.33.0 adds a fourth output, `composed_initial_state`, at
the end of the outputs returned by the `gdn`, `gdn2`, `gdp` and `kda`
graph builders. It is `None` unless a preceding state update is passed,
which FlashInfer never passes. `_create_la_graph` unpacked exactly three
values, so every cuDNN linear-attention call (GDN/KDA prefill through
the cuDNN backend) failed with `ValueError: too many values to unpack
(expected 3)`. Since #9672, FlashInfer requires 1.33.0 or later, so
every install hits this.

The fix keeps only the first two outputs, `O` and `final_state`, which
are the only ones used. The frontend appends new outputs at the end of
the list, so this works on 1.32/1.33 and on future releases that add
more.

## 🔍 Related Issues

Follow-up to #9672.

## 🧪 Tests

New CPU contract test
`test_graph_builder_accepts_appended_frontend_outputs` in
`tests/cpu/kda/test_cudnn_linear_attention_contract.py`. It builds the
graph with a fake frontend graph for all four families, returning both 3
and 4 outputs, and checks that `O` and `final_state` are bound.

- With cuDNN Frontend 1.33.0, the real `graph.gdn(...)` returns a list
of 4: `[O, final_state, None, None]`.
- Before the fix, the four 4-output cases fail and the four 3-output
cases pass.
- After the fix, the whole file passes (21/21) with FE 1.33.0 and with
FE 1.31.0.
- pre-commit passes.

GPU numerics are unchanged. The kernels, attributes and bindings are the
same, and only the Python unpack changed.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved compatibility with linear-attention operations that return
additional backend results. The expected attention output and final
state are now preserved, preventing extra results from interfering with
their handling.
* **Tests**
* Added coverage for multiple linear-attention variants and backend
result formats, including cases with additional outputs.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: jimmzhou <jimmzhou@nvidia.com>

### [3042c3d](https://github.com/flashinfer-ai/flashinfer/commit/3042c3d070da47d655cd7d486a6c3823d086e5b8)

- **作者**: eigen
- **时间**: 2026-11-20T14:17:17Z
- **提交信息**: feat(cake_gdp): decode programs on SM107 (sm_107a) (#9774)

The Cake Gated DeltaProduct (GDP) kernel family has four decode routes,
`decode_nh1` to `decode_nh4`, for n = 1 to 4 Householder updates per
token. All routes use head sizes K = 128 and V = 64 and fused q/k L2
normalization. SM90 also has chunked varlen prefill programs. The state
pool is FP32, or FP16 stored with round to nearest even or stochastic
rounding (`rand_seed`, `philox_rounds`). FP16 calls that store per-token
snapshots can use two snapshot-noise programs with shared-memory Philox
noise.

This PR brings the decode programs to SM107 (R200 / VR200, `sm_107a`).
The 42 decode programs and the 2 snapshot-noise programs that ship on
`sm_100a` are built unchanged for `sm_107a` (44 libraries), with both
state pools. A call on SM107 selects the same program as on SM100,
except in one case. The runtime-token-count snapshot-noise program
serves stochastic snapshot calls from 16 Philox rounds on SM107 (from 10
on SM100 / SM103). Below 16 rounds, the plain program serves them.

No earlier Cake version runs on SM107, so the baselines are non-Cake.
They are the FlashInfer CuTe DSL GDP MTP decode kernels (FI CuTe DSL:
per row, the faster of PRs #6198 and #6250, the family's established
baseline), cuDNN frontend 1.32.3, and the per-row fastest non-Cake
implementation (those two and flash-linear-attention (fla) 0.6.0).
Speedup is baseline time / Cake time, so a value above 1 means Cake is
faster. Over the 96 shapes (H 80/24/20/10 x B 1/16/64/256 x T 2, 3, 5,
6, 7, 16), Cake is faster on 96 / 96 rows against each baseline. The
geomean speedup is 2.61x over FI CuTe DSL, 2.60x over cuDNN and 1.88x
over the per-row fastest non-Cake (min 1.06x at H 10, B 1, T 2; max
3.07x). The fastest non-Cake is FI CuTe DSL at small T, cuDNN at large
T, and fla on 9 rows with B 16. The FP16 state pool has no comparison
rows: FI CuTe DSL and cuDNN refuse an FP16 state, and fla has no
state-pool argument.

The FP32 and FP16 programs on `sm_100a` / `sm_103a` and the FP32
programs and chunked varlen prefill on `sm_90a` are unchanged, and the
family now ships on `sm_90a`, `sm_100a`, `sm_103a` and `sm_107a`.

Latency of one decode / MTP verification call on NVIDIA VR200 (R200,
`sm_107a`, 212 SMs), CUDA 13.5. FP32 state, 3 Householder steps, K =
128, V = 64; cold L2 (flushed before every call), median of 3 passes;
every implementation of a row ran on the same GPU. Ratio = baseline /
Cake (above 1: Cake is faster). FI CuTe DSL = the faster of the
FlashInfer CuTe DSL GDP MTP decode kernels of PRs #6198 and #6250 for
that row (nvidia-cutlass-dsl 4.8.1); cuDNN = cuDNN frontend 1.32.3;
fastest non-Cake = the fastest of those and flash-linear-attention 0.6.0
for that row. Cake kernels are built by nvcc 13.5.37; the FI CuTe DSL
and cuDNN kernels by nvidia-cutlass-dsl's bundled compiler (CUDA
13.4.59); fla's Triton 3.8.0 kernels by ptxas 13.5.37.

| H | B | T | Cake (us) | FI CuTe DSL (us) | ratio | cuDNN (us) | ratio
| fastest non-Cake (us) | ratio |
|---:|---:|---:|---:|---:|---:|---:|---:|---|---:|
| 80 | 1 | 2 | 4.99 | 8.10 | 1.62x | 19.84 | 3.97x | 8.10 (FI CuTe DSL)
| 1.62x |
| 80 | 1 | 3 | 5.34 | 11.07 | 2.07x | 19.55 | 3.66x | 11.07 (FI CuTe
DSL) | 2.07x |
| 80 | 1 | 5 | 6.30 | 18.34 | 2.91x | 19.78 | 3.14x | 18.34 (FI CuTe
DSL) | 2.91x |
| 80 | 1 | 6 | 6.91 | 21.86 | 3.16x | 20.00 | 2.89x | 20.00 (cuDNN) |
2.89x |
| 80 | 1 | 7 | 7.30 | 21.38 | 2.93x | 20.08 | 2.75x | 20.08 (cuDNN) |
2.75x |
| 80 | 1 | 16 | 11.87 | 60.51 | 5.10x | 19.94 | 1.68x | 19.94 (cuDNN) |
1.68x |
| 80 | 16 | 2 | 15.49 | 25.34 | 1.64x | 53.47 | 3.45x | 25.34 (FI CuTe
DSL) | 1.64x |
| 80 | 16 | 3 | 16.45 | 35.30 | 2.15x | 53.70 | 3.26x | 35.30 (FI CuTe
DSL) | 2.15x |
| 80 | 16 | 5 | 21.66 | 62.95 | 2.91x | 53.70 | 2.48x | 53.70 (cuDNN) |
2.48x |
| 80 | 16 | 6 | 24.86 | 91.62 | 3.68x | 53.09 | 2.14x | 53.09 (cuDNN) |
2.14x |
| 80 | 16 | 7 | 27.81 | 98.27 | 3.53x | 53.28 | 1.92x | 53.28 (cuDNN) |
1.92x |
| 80 | 16 | 16 | 49.09 | 253.73 | 5.17x | 53.60 | 1.09x | 53.60 (cuDNN)
| 1.09x |
| 80 | 64 | 2 | 40.70 | 83.78 | 2.06x | 162.02 | 3.98x | 83.78 (FI CuTe
DSL) | 2.06x |
| 80 | 64 | 3 | 44.45 | 124.03 | 2.79x | 161.99 | 3.64x | 124.03 (FI
CuTe DSL) | 2.79x |
| 80 | 64 | 5 | 61.57 | 209.70 | 3.41x | 163.11 | 2.65x | 163.11 (cuDNN)
| 2.65x |
| 80 | 64 | 6 | 71.39 | 317.77 | 4.45x | 164.35 | 2.30x | 164.35 (cuDNN)
| 2.30x |
| 80 | 64 | 7 | 81.12 | 341.54 | 4.21x | 165.28 | 2.04x | 165.28 (cuDNN)
| 2.04x |
| 80 | 64 | 16 | 154.88 | 799.82 | 5.16x | 174.88 | 1.13x | 174.88
(cuDNN) | 1.13x |
| 80 | 256 | 2 | 140.00 | 313.44 | 2.24x | 605.10 | 4.32x | 313.44 (FI
CuTe DSL) | 2.24x |
| 80 | 256 | 3 | 157.70 | 469.93 | 2.98x | 608.30 | 3.86x | 469.93 (FI
CuTe DSL) | 2.98x |
| 80 | 256 | 5 | 223.20 | 802.80 | 3.60x | 617.05 | 2.76x | 617.05
(cuDNN) | 2.76x |
| 80 | 256 | 6 | 259.46 | 1078.67 | 4.16x | 622.92 | 2.40x | 622.92
(cuDNN) | 2.40x |
| 80 | 256 | 7 | 295.62 | 1333.98 | 4.51x | 626.96 | 2.12x | 626.96
(cuDNN) | 2.12x |
| 80 | 256 | 16 | 579.69 | 3069.27 | 5.29x | 664.36 | 1.15x | 664.36
(cuDNN) | 1.15x |
| 24 | 1 | 2 | 4.61 | 5.57 | 1.21x | 20.42 | 4.43x | 5.57 (FI CuTe DSL)
| 1.21x |
| 24 | 1 | 3 | 5.02 | 6.72 | 1.34x | 20.32 | 4.04x | 6.72 (FI CuTe DSL)
| 1.34x |
| 24 | 1 | 5 | 5.95 | 7.42 | 1.25x | 19.55 | 3.29x | 7.42 (FI CuTe DSL)
| 1.25x |
| 24 | 1 | 6 | 6.50 | 8.99 | 1.38x | 19.62 | 3.02x | 8.99 (FI CuTe DSL)
| 1.38x |
| 24 | 1 | 7 | 6.98 | 8.90 | 1.28x | 19.87 | 2.85x | 8.90 (FI CuTe DSL)
| 1.28x |
| 24 | 1 | 16 | 11.42 | 25.86 | 2.26x | 19.87 | 1.74x | 19.87 (cuDNN) |
1.74x |
| 24 | 16 | 2 | 6.94 | 12.38 | 1.78x | 27.94 | 4.02x | 12.29 (fla) |
1.77x |
| 24 | 16 | 3 | 7.52 | 16.58 | 2.20x | 27.87 | 3.71x | 15.65 (fla) |
2.08x |
| 24 | 16 | 5 | 9.50 | 24.86 | 2.62x | 27.74 | 2.92x | 22.66 (fla) |
2.38x |
| 24 | 16 | 6 | 10.43 | 25.50 | 2.44x | 27.58 | 2.64x | 25.50 (FI CuTe
DSL) | 2.44x |
| 24 | 16 | 7 | 11.36 | 29.47 | 2.59x | 27.20 | 2.39x | 27.20 (cuDNN) |
2.39x |
| 24 | 16 | 16 | 18.82 | 74.91 | 3.98x | 28.74 | 1.53x | 28.74 (cuDNN) |
1.53x |
| 24 | 64 | 2 | 17.18 | 33.60 | 1.96x | 60.32 | 3.51x | 33.60 (FI CuTe
DSL) | 1.96x |
| 24 | 64 | 3 | 18.30 | 42.34 | 2.31x | 60.45 | 3.30x | 42.34 (FI CuTe
DSL) | 2.31x |
| 24 | 64 | 5 | 23.94 | 71.49 | 2.99x | 60.32 | 2.52x | 60.32 (cuDNN) |
2.52x |
| 24 | 64 | 6 | 27.49 | 108.13 | 3.93x | 59.97 | 2.18x | 59.97 (cuDNN) |
2.18x |
| 24 | 64 | 7 | 30.98 | 105.83 | 3.42x | 60.32 | 1.95x | 60.32 (cuDNN) |
1.95x |
| 24 | 64 | 16 | 55.01 | 305.73 | 5.56x | 60.80 | 1.11x | 60.80 (cuDNN)
| 1.11x |
| 24 | 256 | 2 | 47.62 | 99.75 | 2.09x | 189.47 | 3.98x | 99.75 (FI CuTe
DSL) | 2.09x |
| 24 | 256 | 3 | 51.94 | 147.49 | 2.84x | 191.04 | 3.68x | 147.49 (FI
CuTe DSL) | 2.84x |
| 24 | 256 | 5 | 71.97 | 248.58 | 3.45x | 191.11 | 2.66x | 191.11
(cuDNN) | 2.66x |
| 24 | 256 | 6 | 83.11 | 391.56 | 4.71x | 193.86 | 2.33x | 193.86
(cuDNN) | 2.33x |
| 24 | 256 | 7 | 94.18 | 413.32 | 4.39x | 195.04 | 2.07x | 195.04
(cuDNN) | 2.07x |
| 24 | 256 | 16 | 179.65 | 954.18 | 5.31x | 206.63 | 1.15x | 206.63
(cuDNN) | 1.15x |
| 20 | 1 | 2 | 4.61 | 5.54 | 1.20x | 19.01 | 4.12x | 5.54 (FI CuTe DSL)
| 1.20x |
| 20 | 1 | 3 | 5.02 | 6.59 | 1.31x | 19.10 | 3.80x | 6.59 (FI CuTe DSL)
| 1.31x |
| 20 | 1 | 5 | 5.92 | 7.30 | 1.23x | 19.14 | 3.23x | 7.30 (FI CuTe DSL)
| 1.23x |
| 20 | 1 | 6 | 6.43 | 8.93 | 1.39x | 19.07 | 2.97x | 8.93 (FI CuTe DSL)
| 1.39x |
| 20 | 1 | 7 | 7.01 | 8.70 | 1.24x | 19.07 | 2.72x | 8.70 (FI CuTe DSL)
| 1.24x |
| 20 | 1 | 16 | 11.39 | 25.47 | 2.24x | 19.14 | 1.68x | 19.14 (cuDNN) |
1.68x |
| 20 | 16 | 2 | 6.62 | 12.03 | 1.82x | 26.62 | 4.02x | 11.62 (fla) |
1.75x |
| 20 | 16 | 3 | 7.30 | 16.22 | 2.22x | 26.69 | 3.66x | 14.98 (fla) |
2.05x |
| 20 | 16 | 5 | 9.34 | 24.48 | 2.62x | 26.79 | 2.87x | 21.89 (fla) |
2.34x |
| 20 | 16 | 6 | 10.43 | 24.38 | 2.34x | 26.62 | 2.55x | 24.38 (FI CuTe
DSL) | 2.34x |
| 20 | 16 | 7 | 11.33 | 28.22 | 2.49x | 26.88 | 2.37x | 26.88 (cuDNN) |
2.37x |
| 20 | 16 | 16 | 19.23 | 74.94 | 3.90x | 27.17 | 1.41x | 27.17 (cuDNN) |
1.41x |
| 20 | 64 | 2 | 15.65 | 26.05 | 1.66x | 54.02 | 3.45x | 26.05 (FI CuTe
DSL) | 1.66x |
| 20 | 64 | 3 | 16.74 | 36.22 | 2.16x | 54.18 | 3.24x | 36.22 (FI CuTe
DSL) | 2.16x |
| 20 | 64 | 5 | 21.82 | 63.11 | 2.89x | 54.72 | 2.51x | 54.72 (cuDNN) |
2.51x |
| 20 | 64 | 6 | 24.83 | 91.49 | 3.68x | 54.91 | 2.21x | 54.91 (cuDNN) |
2.21x |
| 20 | 64 | 7 | 27.84 | 98.50 | 3.54x | 54.62 | 1.96x | 54.62 (cuDNN) |
1.96x |
| 20 | 64 | 16 | 49.06 | 252.61 | 5.15x | 54.88 | 1.12x | 54.88 (cuDNN)
| 1.12x |
| 20 | 256 | 2 | 41.02 | 83.81 | 2.04x | 162.82 | 3.97x | 83.81 (FI CuTe
DSL) | 2.04x |
| 20 | 256 | 3 | 44.80 | 124.29 | 2.77x | 163.14 | 3.64x | 124.29 (FI
CuTe DSL) | 2.77x |
| 20 | 256 | 5 | 61.66 | 209.48 | 3.40x | 163.52 | 2.65x | 163.52
(cuDNN) | 2.65x |
| 20 | 256 | 6 | 71.52 | 322.36 | 4.51x | 164.10 | 2.29x | 164.10
(cuDNN) | 2.29x |
| 20 | 256 | 7 | 81.22 | 339.05 | 4.17x | 165.63 | 2.04x | 165.63
(cuDNN) | 2.04x |
| 20 | 256 | 16 | 155.01 | 797.39 | 5.14x | 175.20 | 1.13x | 175.20
(cuDNN) | 1.13x |
| 10 | 1 | 2 | 4.61 | 4.90 | 1.06x | 18.78 | 4.08x | 4.90 (FI CuTe DSL)
| 1.06x |
| 10 | 1 | 3 | 4.96 | 5.98 | 1.21x | 18.82 | 3.79x | 5.98 (FI CuTe DSL)
| 1.21x |
| 10 | 1 | 5 | 5.89 | 6.66 | 1.13x | 18.75 | 3.18x | 6.66 (FI CuTe DSL)
| 1.13x |
| 10 | 1 | 6 | 6.34 | 8.03 | 1.27x | 18.66 | 2.94x | 8.03 (FI CuTe DSL)
| 1.27x |
| 10 | 1 | 7 | 6.88 | 7.97 | 1.16x | 18.91 | 2.75x | 7.97 (FI CuTe DSL)
| 1.16x |
| 10 | 1 | 16 | 11.36 | 24.29 | 2.14x | 19.10 | 1.68x | 19.10 (cuDNN) |
1.68x |
| 10 | 16 | 2 | 5.34 | 11.55 | 2.16x | 20.67 | 3.87x | 10.46 (fla) |
1.96x |
| 10 | 16 | 3 | 5.73 | 15.27 | 2.66x | 20.71 | 3.61x | 13.92 (fla) |
2.43x |
| 10 | 16 | 5 | 6.69 | 22.94 | 3.43x | 20.93 | 3.13x | 20.51 (fla) |
3.07x |
| 10 | 16 | 6 | 7.30 | 22.82 | 3.13x | 20.80 | 2.85x | 20.80 (cuDNN) |
2.85x |
| 10 | 16 | 7 | 7.84 | 26.27 | 3.35x | 20.80 | 2.65x | 20.80 (cuDNN) |
2.65x |
| 10 | 16 | 16 | 12.35 | 72.58 | 5.88x | 20.93 | 1.69x | 20.93 (cuDNN) |
1.69x |
| 10 | 64 | 2 | 9.34 | 14.30 | 1.53x | 37.76 | 4.04x | 14.30 (FI CuTe
DSL) | 1.53x |
| 10 | 64 | 3 | 10.75 | 19.30 | 1.79x | 37.98 | 3.53x | 19.30 (FI CuTe
DSL) | 1.79x |
| 10 | 64 | 5 | 14.05 | 28.99 | 2.06x | 37.44 | 2.67x | 28.99 (FI CuTe
DSL) | 2.06x |
| 10 | 64 | 6 | 15.97 | 33.86 | 2.12x | 37.70 | 2.36x | 33.86 (FI CuTe
DSL) | 2.12x |
| 10 | 64 | 7 | 18.02 | 39.55 | 2.20x | 37.82 | 2.10x | 37.82 (cuDNN) |
2.10x |
| 10 | 64 | 16 | 30.88 | 128.96 | 4.18x | 38.02 | 1.23x | 38.02 (cuDNN)
| 1.23x |
| 10 | 256 | 2 | 24.22 | 42.66 | 1.76x | 94.21 | 3.89x | 42.66 (FI CuTe
DSL) | 1.76x |
| 10 | 256 | 3 | 25.66 | 65.73 | 2.56x | 94.75 | 3.69x | 65.73 (FI CuTe
DSL) | 2.56x |
| 10 | 256 | 5 | 34.43 | 113.09 | 3.28x | 94.91 | 2.76x | 94.91 (cuDNN)
| 2.76x |
| 10 | 256 | 6 | 40.22 | 162.76 | 4.05x | 95.36 | 2.37x | 95.36 (cuDNN)
| 2.37x |
| 10 | 256 | 7 | 45.38 | 172.80 | 3.81x | 95.14 | 2.10x | 95.14 (cuDNN)
| 2.10x |
| 10 | 256 | 16 | 84.13 | 417.35 | 4.96x | 98.31 | 1.17x | 98.31 (cuDNN)
| 1.17x |


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added support for SM107 GPUs for GDP decode, including FP16 state
pools and snapshot-noise decoding.
* **Documentation**
* Updated architecture support and FP16 state-pool guidance to include
SM107.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery H <averyh@nvidia.com>

### [0479f95](https://github.com/flashinfer-ai/flashinfer/commit/0479f954cf47c7946a5fdd3312b477c0fd926c0c)

- **作者**: Cindy Zhang
- **时间**: 2026-11-20T13:48:52Z
- **提交信息**: fix(ci): prepare selected source for provider spec lint (#9753)

Reconstruct and verify the pinned base/head merge before initializing
submodules in the spec-lint job, matching the AOT test job. Extend
workflow regression tests to cover shallow checkouts, runs without
snapshots, selected submodule revisions, and tree mismatches.

AI-assisted implementation and review with OpenAI Codex.

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->
Ensure Provider Spec Lint checks the same selected source tree as the
AOT test job.

For bot-triggered runs with a pinned merge snapshot, setup outputs the
PR head together with the selected base and expected tree. The AOT job
reconstructs and verifies that merge, but the spec-lint job previously
checked out only the PR head. This could produce inconsistent results
when the selected base contains relevant changes absent from the PR
branch.

  This change:
- Reconstructs and verifies the selected merge before running spec lint.
  - Initializes submodules only after source verification.
- Extends regression tests to cover both jobs, shallow checkouts, runs
without snapshots, selected submodule revisions, and tree mismatches.


## 🔍 Related Issues

<!-- Link any related issues here -->
 Follow-up to #8718, addressing the CodeRabbit comment:

https://github.com/flashinfer-ai/flashinfer/pull/8718#discussion_r4483636243

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
reviewers may adjust): `tests/...`

Validation:
- `python3 tests/infra/test_sharding/test_bot_run_workflow.py -v` — 34
tests passed.
  - Changed-file pre-commit checks passed.
  - YAML parsing, Bash syntax checks, and `git diff --check` passed.
  - Confirmed existing AOT/GPU job definitions are unchanged.

  Suggested CI test target:
  `tests/infra/test_sharding/test_bot_run_workflow.py`


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
The spec-lint job follows the existing AOT source-preparation sequence.
Runs without snapshot metadata retain their checked-out source.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Chores**
* Improved pull request checks to validate the selected source snapshot
before initializing submodules, helping ensure checks run against the
intended code.
* Expanded automated coverage for test and specification-lint workflows,
including cases where repository history is shallow or a selected
snapshot is not provided.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [c7e4de0](https://github.com/flashinfer-ai/flashinfer/commit/c7e4de0b13ad677ec1b67447a0ac329a1109cb60)

- **作者**: eigen
- **时间**: 2026-11-20T12:43:23Z
- **提交信息**: fix(cake_batch_deepgemm_fp8): route no twin on a device whose memory runs below its full clock (#9757)

### [db23734](https://github.com/flashinfer-ai/flashinfer/commit/db2373490172a31dbbdc489ef82fe174e6d88f06)

- **作者**: eigen
- **时间**: 2026-11-20T09:23:41Z
- **提交信息**: perf(mla): build the Cake Blackwell MLA decode row plan on the device (#9718)

The Cake Blackwell MLA decode family (`backend="cake"` of
`trtllm_batch_decode_with_kv_cache_mla`) targets DeepSeek MLA dimensions
(qk_nope 128, kv_lora_rank 512, qk_rope 64, 128 heads, q_len 1-2, with
other shapes handled by tails). It has 19 generated programs: BF16 KV
with page size 32 and 64 (value-split programs with a quarter or half of
V per CTA, and CLC persistent programs including one-wave forms), FP8
E4M3 KV with page size 64, and BF16 / FP8 tail programs. In this PR, the
value-split, CLC and FP8 page-64 programs build their per-row plan on
the device. CLC programs keep a longest-first work order, which a new
order program now builds on the device. That program is one extra small
launch and runs only when `num_sms/2 < rows <= 1024`. The host no longer
reads `seq_lens` or caches a plan per input tensor. In its best case,
the previous Cake version on main (100465cbe) reuses a host-built plan
cached for the same tensors. Against that case this PR is not faster:
0.935x-1.006x, from 6.5% slower to 0.6% faster. When a serving engine
updates `seq_lens` in place before every call, as a decode loop does,
the previous version rebuilds its row plan on every call and this PR
does not. Per decode step, this PR is 1.149x-3.540x faster on B200 and
1.148x-3.950x faster on GB300.

Measured on B200 (Blackwell, sm_100a, 148 SMs) and GB300 (Blackwell,
sm_103a, 152 SMs) with CUDA 13.5 and torch 2.14.1+cu130: CUPTI kernel
span over CUDA-graph replay, L2 flushed before each replay, median of 9
(3 rounds x 3 repetitions).

| GPU | KV dtype | page size | batch | q_len | KV length | lengths |
previous Cake (us) | this PR (us) | speedup |
|---|---|---|---|---|---|---|---|---|---|
| B200 (sm_100a) | BF16 | 32 | 1 | 1 | 16384 | uniform | 131.86 | 133.50
| 0.988x |
| B200 (sm_100a) | BF16 | 32 | 128 | 1 | 1024 | varied | 32.48 | 33.86 |
0.959x |
| B200 (sm_100a) | BF16 | 32 | 128 | 1 | 4096 | uniform | 133.41 |
132.67 | 1.006x |
| B200 (sm_100a) | BF16 | 64 | 8 | 1 | 1024 | varied | 13.66 | 14.02 |
0.974x |
| B200 (sm_100a) | FP8 | 64 | 8 | 1 | 1024 | varied | 11.30 | 11.52 |
0.981x |
| B200 (sm_100a) | FP8 | 64 | 32 | 1 | 4096 | varied | 24.45 | 24.74 |
0.988x |
| B200 (sm_100a) | FP8 | 64 | 128 | 1 | 1024 | uniform | 55.87 | 55.58 |
1.005x |
| GB300 (sm_103a) | BF16 | 32 | 1 | 1 | 16384 | uniform | 111.78 |
113.63 | 0.984x |
| GB300 (sm_103a) | BF16 | 32 | 128 | 1 | 1024 | varied | 31.42 | 33.60
| 0.935x |
| GB300 (sm_103a) | BF16 | 32 | 128 | 1 | 4096 | uniform | 116.26 |
118.21 | 0.984x |
| GB300 (sm_103a) | BF16 | 64 | 8 | 1 | 1024 | varied | 11.87 | 12.22 |
0.971x |
| GB300 (sm_103a) | FP8 | 64 | 8 | 1 | 1024 | varied | 10.50 | 10.59 |
0.992x |
| GB300 (sm_103a) | FP8 | 64 | 32 | 1 | 4096 | varied | 23.68 | 23.84 |
0.993x |
| GB300 (sm_103a) | FP8 | 64 | 128 | 1 | 1024 | uniform | 52.16 | 52.64
| 0.991x |

Per decode step, measured on FlashInfer main dc00b0e51 (previous Cake)
and on the same base with this PR's kernels. GPUs: B200 (Blackwell,
sm_100a, 148 SMs) and GB300 (Blackwell, sm_103a, 152 SMs), with CUDA
13.5 JIT (nvcc 13.5) and torch 2.14.1+cu130. "Per step" means `seq_lens`
is updated in place before every call (same values, new tensor version),
as a decode loop does. Time is the CUPTI span of all kernels of one call
over CUDA-graph replay, with L2 flushed before every iteration. Each
value is the median over 6 rounds of per-round medians (3 repetitions
each). "Previous Cake, cached plan" is the same previous version with an
unchanged `seq_lens` (its best case), shown for reference. The
trtllm-gen and cute-dsl columns are the other backends of the same API
(`backend="trtllm-gen"` and tuned `backend="cute-dsl"`), measured the
same way. "Fastest other / this PR" = min(trtllm-gen, cute-dsl) / this
PR per step, and > 1 means this PR is faster. Cake is slower than the
fastest other backend on 8 of the 14 rows, as low as 0.130x at batch 1,
KV 16384 on B200.

| GPU | KV dtype | page size | batch | q_len | KV length | lengths |
previous Cake, cached plan (us) | previous Cake, per step (us) | this
PR, per step (us) | speedup per step | trtllm-gen (us) | cute-dsl (us) |
fastest other / this PR |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| B200 (sm_100a) | BF16 | 32 | 1 | 1 | 16384 | uniform | 132.19 | 168.27
| 135.68 | 1.240x | 46.72 | 17.62 | 0.130x |
| B200 (sm_100a) | BF16 | 32 | 128 | 1 | 1024 | varied | 32.08 | 72.16 |
35.76 | 2.018x | 42.27 | 42.18 | 1.179x |
| B200 (sm_100a) | BF16 | 32 | 128 | 1 | 4096 | uniform | 127.97 |
161.18 | 131.87 | 1.222x | 138.02 | 133.57 | 1.013x |
| B200 (sm_100a) | BF16 | 64 | 8 | 1 | 1024 | varied | 13.58 | 56.82 |
16.05 | 3.540x | 26.26 | 13.82 | 0.861x |
| B200 (sm_100a) | FP8 | 64 | 8 | 1 | 1024 | varied | 11.42 | 22.77 |
13.17 | 1.729x | 15.65 | 12.22 | 0.928x |
| B200 (sm_100a) | FP8 | 64 | 32 | 1 | 4096 | varied | 24.54 | 35.73 |
26.53 | 1.347x | 31.10 | 27.92 | 1.052x |
| B200 (sm_100a) | FP8 | 64 | 128 | 1 | 1024 | uniform | 55.73 | 66.21 |
57.60 | 1.149x | 30.11 | 31.15 | 0.523x |
| GB300 (sm_103a) | BF16 | 32 | 1 | 1 | 16384 | uniform | 112.18 |
144.03 | 118.29 | 1.218x | 43.54 | 16.72 | 0.141x |
| GB300 (sm_103a) | BF16 | 32 | 128 | 1 | 1024 | varied | 31.71 | 66.72
| 35.52 | 1.878x | 40.13 | 40.22 | 1.130x |
| GB300 (sm_103a) | BF16 | 32 | 128 | 1 | 4096 | uniform | 116.05 |
151.23 | 120.10 | 1.259x | 130.35 | 125.09 | 1.042x |
| GB300 (sm_103a) | BF16 | 64 | 8 | 1 | 1024 | varied | 11.81 | 54.93 |
13.90 | 3.950x | 24.54 | 13.50 | 0.971x |
| GB300 (sm_103a) | FP8 | 64 | 8 | 1 | 1024 | varied | 10.59 | 20.34 |
12.51 | 1.625x | 14.69 | 11.89 | 0.950x |
| GB300 (sm_103a) | FP8 | 64 | 32 | 1 | 4096 | varied | 23.55 | 33.15 |
25.14 | 1.319x | 30.69 | 25.37 | 1.009x |
| GB300 (sm_103a) | FP8 | 64 | 128 | 1 | 1024 | uniform | 52.32 | 62.69
| 54.59 | 1.148x | 27.41 | 28.13 | 0.502x |

The BF16 / FP8 tail programs now handle zero-length rows safely and have
a device guard for KV length > 4096, and the family ships for sm_100a
(B200) and sm_103a (GB300, with 148- and 152-SM programs).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added support for row-batched and ragged queries, sparse attention
inputs, and optional work reordering across Blackwell MLA workloads.
* Expanded FP8 attention support, including optional log-sum-exp output.
* **Bug Fixes**
* Padded or empty rows now produce zero outputs where applicable, and
page lookups are bounded.
* Improved handling of graph replay with changing sequence lengths and
page tables.
* Added coverage for dispatch selection, work ordering, cache behavior,
and edge cases involving long KV rows.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [d1c788a](https://github.com/flashinfer-ai/flashinfer/commit/d1c788a15d4cdbc4be4f1716a59c58a924083150)

- **作者**: Brian K. Ryu
- **时间**: 2026-11-20T09:12:35Z
- **提交信息**: perf(batch_invariant): fewer and cheaper GEMM compiles: runtime schedule arguments, kernel-source cache keys, engine-less export (#9727)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->
Follow-up to #9620 (host launch overhead) on the compile side of the
batch-invariant GEMM family: unit-test walls, framework start-up and
autotuning are dominated by CuTe-DSL compiles, and an edit anywhere in
the batch-invariant package wiped every compiled GEMM object. Four
changes, none to any kernel's arithmetic: outputs are bit-identical
before / after for every tactic of every class on both parts, and the
dispatcher, the autotuner's tactic tuple, the public API and the Lean
record are unchanged.

1. **Schedule parameters are runtime arguments.** Raster order, swizzle
size, the persistent grid size and (for the split-K classes) the chunk
count were compile-time constants, so each tactic of a tile / cluster
bucket was its own compiled object. They are now Int32 kernel arguments
(`blocks/scheduler.py`: FastDivmod tile decode with a one-divisor path
for the dispatcher's swizzle-1 picks, no padded clusters, the first tile
decoded before the barrier init completes), one object per bucket; the
split-K fixup stays one object per chunk count (its unrolled loop is
faster than a rolled one). The object names drop the `_rm|_rn`, `_sw<s>`
and `_g<n>` tokens; the launch handle keeps the record's values and the
API passes them with each launch.
2. **The JIT cache key is the kernel sources.** The import walk of
`flashinfer/batch_invariant/jit.py` followed every package `__init__` it
crossed, so a GEMM module's key held the sampling, GDN, KDA,
quantization and attention surfaces (42 files for the dense module, 31
outside the GEMM family): 20 of the 24 batch-invariant commits since
September invalidated every GEMM object of every cache. An import now
resolves to the file it names; `__init__` files on the way enter the key
unfollowed. No kernel source leaves any module's key (device-free test).
Every module's key changes once.
3. **Engine-less compile on the disk-cache path.** `JitSpecCuteDsl`
exported the compiled module to an object and reloaded it, after
building an execution engine, entry lookup and TVM-FFI link it never
used (a quarter of a GEMM compile). An optional `export_compile_fn`
compiles with the DSL's `no_jit_engine=True`; the engine path remains
for a failed export and for `FLASHINFER_CUTE_DSL_DISABLE_CACHE=1`. Other
CuTe-DSL kernels keep today's path until their closures opt in. Objects
are SHA-256-identical with and without the engine (17 / 17 production
objects, 1067 / 1067 across two measurement caches).
4. **Key-source hash once per process** instead of once per kernel built
or loaded. An edit to a key source is seen by the next process.

Also carried: `clear_kernel_cache()` for #9620's launch-handle cache,
registered with the rankings' clear hook (the review's
remaining note).

## 🔍 Related Issues

- #9620 (merged): host launch overhead; this is its compile-side
counterpart.
- #9327: parallel precompile of mm_fp4 / mm_mxfp8 tactics (independent;
fewer objects per bucket shrink what any pool compiles).

## 📊 Measurements

Rubin NVL4 (sm_107), fresh JIT cache per cold run, same GPU, main vs
this branch (compile and start-up: `tests/gemm` suites and Qwen3-8B
linears at M in {1, 8, 64, 512, 4096}).

| case | objects compiled | compile s | wall s | cache size MiB |
|---|---|---|---|---|
| mm_bf16 suite (cold) | 261 -> 126 | 112.5 -> 46.8 | 167 -> 89 | 18.2
-> 9.7 |
| mm_fp4 suite (cold) | 623 -> 279 | 257.7 -> 117.6 | 367 -> 211 | 51.2
-> 27.6 |
| 7B start-up bf16, untuned | 6 -> 6 | 2.0 -> 2.1 | 2.9 -> 2.9 | 0.4 ->
0.4 |
| 7B start-up bf16, autotune | 128 -> 38 | 50.5 -> 13.5 | 65.6 -> 25.4 |
9.4 -> 3.8 |
| 7B start-up NVFP4, untuned | 8 -> 8 | 3.9 -> 3.6 | 66.4 -> 57.0 (nvcc
quantizer) | 8.3 -> 8.4 |
| 7B start-up NVFP4, autotune | 119 -> 29 | 50.2 -> 11.0 | 61.2 -> 19.8
| 17.3 -> 11.2 |

Warm (every object cached): the per-kernel key hash is gone, so the warm
bf16 suite goes 49.6 -> 34.3 s, the warm fp4 suite 72.3 -> 41.6 s, a
tuned warm-up's re-tune 13.1 -> 9.0 s (bf16) and 9.2 -> 6.2 s (NVFP4).

Kernel time, static vs runtime schedule arguments (CUDA graphs, 200
executions per sample, 7 interleaved repeats, L2 flush at decode, a
second base process as the control arm; the study's cell set per class):

| class | cells | median % | range % | cells > +1 % | swizzled records
median % | control median / max abs % |
|---|---|---|---|---|---|---|
| bf16 | 45 | -0.80 | -47.1 .. +5.4 | 3 | -2.3 | -0.02 / 1.25 |
| fp8 per-tensor | 44 | -1.21 | -44.6 .. +20.8 | 5 | -4.6 | -0.18 / 1.44
|
| NVFP4 | 43 | -0.74 | -48.2 .. +1.5 | 1 | -4.2 | +0.10 / 1.78 |
| MXFP8 | 39 | -0.85 | -53.7 .. +5.3 | 2 | -9.4 | -0.03 / 1.62 |
| mixed MXFP4 x MXFP8 | 41 | -0.61 | -55.0 .. +1.9 | 1 | -9.2 | -0.25 /
1.97 |
| fp8 block-scale | 22 | -0.74 | -4.8 .. +0.7 | 0 | -3.2 | -0.10 / 1.13
|
| B200 bf16 | 35 | -0.72 | -6.5 .. +1.2 | 3 | -2.6 | +0.04 / 1.97 |
| B200 NVFP4 | 44 | -0.56 | -27.9 .. +1.1 | 1 | -3.8 | +0.01 / 1.09 |

The swizzled records are faster because the static scheduler padded the
fast axis to a multiple of the swizzle and ran the padded clusters (a
doubled wave on some shapes). Cells above +1 % with a quiet control: the
bf16 64x32-tile in-CTA fold object at C = 2 on (512, 16384) decode
cells, +4.4 .. +5.4 % (14.5 us, sixteen CTAs with one tile each; a
non-picked placement whose picked twin, the workspace split, is 1.7-5.5
% faster), bf16 1x512x16384 pick +3.0 % (control +0.9 %), fp8
64x512x16384 fold +2.3 %, fp8 512x256x32768 twin +2.4 %, MXFP8
512x256x32768 pick +1.0 %, B200 bf16 1x256x32768 fold +1.0 %; the other
rows above +1 % have control arms above 1.6 % or spreads above 7 % (the
bimodal 4096^2 / 512x8192 cells). Host time per public-API call (eager,
warm, Rubin): +0.07 .. +0.66 us against #9620's numbers (median +0.3 us;
the launch handle keeps the record's trailing arguments).


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

* **New Features**
* Batch-invariant GEMM kernels support runtime tile scheduling and
launch placement options, including swizzling and raster order.
* Split and batched GEMM workloads can reuse compiled kernels across
different launch configurations, with chunking handled at runtime.
* JIT compilation supports export-only compilation and source-aware
cache keys.
* **Bug Fixes**
* Improved relative-import handling when identifying source files for
JIT caching.
* Improved compiled-kernel reuse across launch placements and handling
of device-dependent launch arguments.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [b966a5b](https://github.com/flashinfer-ai/flashinfer/commit/b966a5b24c6c942247000abd335c9a3cff83db6a)

- **作者**: Yuxian Qiu
- **时间**: 2026-11-20T08:18:22Z
- **提交信息**: fix(prims-ts): keep persistent decode sink barriers in step on empty-KV requests (#9693)

<!-- .github/pull_request_template.md -->

## 📌 Description

With attention sinks, every task of a persistent PrimTS decode kernel
ends an active work tile at CTA barrier 12 (`thread_count=16*32`). This
keeps all tasks on the same logical tile until correction's sink tail
drains. Tasks with `skip_if=PackedDecodeWorkQueue.skip_work_tile_if`
skip a tile without arriving. A tile is skipped when its request has no
KV (`seqlens_kv[b] <= 0`) or its Q group starts past the request's live
Q tokens. The CLC scheduler task has no `skip_if`. It runs the ordinary
`DecodeGenTask._run_task_body_impl` path and made its own decision
there:

- uniform Q: it arrived on every tile;
- variable Q: it arrived when the Q group had live tokens, regardless of
KV length.

For a request with KV length ≤ 0 and live Q tokens, the scheduler warp
therefore arrived once more than the other task warps, and the kernel
hung. Requests with KV length ≤ 0 mark inactive slots, which
`test_attention_ts_decode_final_statistics` already exercises, but only
on a single-request grid that never selects the persistent scheduler.

The scheduler now arrives only when `skip_work_tile_if` is false for the
work-queue tile, the predicate that the `skip_if` tasks use. It
evaluates the tile before the runtime split-KV coordinate mapping, as
the work queue does.

This PR was prepared with AI assistance (Claude Code) and reviewed by
the author.

## 🔍 Related Issues

- Reported in review of #9647:
https://github.com/flashinfer-ai/flashinfer/pull/9647#discussion_r4614239071.
#9647 adds a CUTLASS DSL 4.9 path (`_end_work_tile`) with the same
decision; see Reviewer Notes.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

The hooks ran on both changed files and pass.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/attention/test_attention_ts_decode.py`

New test:
`test_attention_ts_decode_persistent_sinks_skip_inactive_requests`, with
uniform-Q and packed-Q parameters. It plans two requests per SM so the
planner selects the persistent scheduler (asserted). Each request has KV
length 257, 8 Q heads, 1 KV head, head dim 64, and page size 32, with
sinks and a causal mask. Request 1 has KV length 0 and request
`num_requests // 2` has −1. The test checks the live rows against a
reference and expects the inactive rows to remain untouched.

### Validation

B300 (SM103), NGC PyTorch 26.09 dev container, `nvidia-cutlass-dsl`
4.8.0, this branch on `PYTHONPATH`:

- New test: 2 passed (about 80 s cold, 5 s with a warm JIT cache).
- `test_attention_ts_decode.py -k "persistent or sink or packed_q or
final_statistics or clc or window_grouped"`: 56 passed, 1248 deselected
(including the 2 new cases).
- Without the source change (base `main` dc22dd5b3 plus the new test),
both cases hang, with the GPU at 100 % utilization until the process is
killed. The packed-Q case reached pytest-timeout after 420 s while
waiting in `offsets.tolist()`, the first host sync after the decode
launch. The uniform-Q case never reached pytest-timeout and was killed
at 480 s.

Separately, a standalone repro hangs `main` (a7d9e1865) on B300 with DSL
4.8.0 for both uniform Q = 3 and packed Q 3/5/7: 660 requests, the shape
above, request 1 at KV length 0. The same shape with all requests live
completes.

Not run: the full suite, and DSL 4.9 (`main` does not trace on 4.9
without #9647).

## Reviewer Notes

- #9647 replaces this override on CUTLASS DSL 4.9 with `_end_work_tile`,
which makes the same decision as the old code here. Whichever of the two
PRs merges second applies this predicate to the other path.
- In persistent sink configurations, the scheduler warp now reads the
request's KV length once per tile, and for variable Q the Q bounds that
it already read. I did not measure performance.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Persistent decode with attention sinks now handles inactive requests
correctly with both uniform and packed query configurations. Inactive
requests retain their existing output values, while active requests
continue to produce results consistent with sink-aware references.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: Yuxian Qiu <142763828+yuxianq@users.noreply.github.com>
Co-authored-by: qsang-nv <200703406+qsang-nv@users.noreply.github.com>

### [4433ef4](https://github.com/flashinfer-ai/flashinfer/commit/4433ef48d1eabaab82c7cdd33244aabedd810aa8)

- **作者**: Yuxian Qiu
- **时间**: 2026-11-20T08:17:26Z
- **提交信息**: refactor(prims-ts): hoist paged context helper imports (#9446)

<!-- .github/pull_request_template.md -->

## 📌 Description

Paged-context resource methods import their helpers inside JIT-traced
code, while `FmhaTs.__init__` preloads the helper module through
`importlib` to make those calls safe. This change resolves the helper
functions at module import time and removes the constructor preload.

The paged helpers now take `num_tokens_per_page` directly instead of
importing `FmhaConfig` from the resource module. That breaks the
circular dependency and allows ordinary module-level imports. Page-bound
arithmetic, resource scheduling, and public APIs are unchanged.

Current main already has the constructor preload. This is a structural
cleanup for review, not a claim that the normal main-branch entry point
fails. This change is now cherry-picked onto
`cute-dsl-precompile-api--prims-ts-upstream` as
`65dd30cc030043830ed46a3b688f891fd402270f`; the TRT-LLM consumer pin
uses it and drops the downstream helper-hoist patch.

## 🔍 Related Issues

- #6529 introduced the constructor preload.
- TensorRT-LLM carries a related helper-import hoist in its PrimTS
vendor patch.
- Related downstream integration: #9395 now includes this change as a
cherry-pick.

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

- Changed-file pre-commit checks passed; no full-repository hook run is
claimed.
- The helper, resource, and kernel modules import successfully with CUDA
devices hidden.
- **B200: main 2/2 and candidate 2/2 passed**, with zero
failures/errors/skips and clean outer exits. The same existing paged
packed-launch-bounds and FP8 D256 dynamic-causal cases exercise variable
sequence lengths, numerical references, and graph replay in fresh
processes/caches. Baseline: `ae58183fa8a21324c92a1bf2ad2ec658339cfed8`;
candidate: `bbbf232603adbdb3bd355667333ada2502b8be3b`. Both sides pass;
no failing-main or performance-improvement claim is made.
- No new test files, cases, or parameter matrix are added.

- [ ] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/attention/test_attention_ts_context.py`

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

AI-assisted implementation. Please review the dependency direction, the
scalar page-size substitution in both helper callers, and whether
replacing the existing preload workaround is worth upstreaming. Ready
for review. The consumer uses a cherry-pick; this PR has not been merged
upstream.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Refactor**
* Streamlined internal setup and configuration handling for paged
attention. No user-visible behavior or public interfaces changed.
* This maintenance update does not add or remove any user-facing
capabilities. No changes to workflows or available features are
expected. Users can continue using paged attention as before.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: Yuxian Qiu <142763828+yuxianq@users.noreply.github.com>
Co-authored-by: qsang-nv <200703406+qsang-nv@users.noreply.github.com>

### [3e28076](https://github.com/flashinfer-ai/flashinfer/commit/3e280769e0588113cd4984fde2d73016bfed93d1)

- **作者**: eigen
- **时间**: 2026-11-20T08:04:46Z
- **提交信息**: perf(cake_gdp): shared-memory noise programs for stochastic FP16 snapshot calls of n = 3 on SM100 and SM103 (#9763)

The Cake Gated DeltaProduct (GDP) kernel family has four decode routes,
`decode_nh1` to `decode_nh4`, for n = 1 to 4 Householder updates per
token. All routes use head sizes K = 128 and V = 64 and fused q/k L2
normalization. The state pool is FP32 on all three targets. On SM100 and
SM103 it can also be FP16, stored with round to nearest even (RNE) or
stochastic rounding (SR). SR uses the hardware `cvt.rs` instruction with
Philox-4x32 bits when `rand_seed` is given. `philox_rounds` takes 5 to
16 (default 10).

This PR adds snapshot-noise programs. They are shared-memory noise
variants of two FP16 `decode_nh3` programs, built for `sm_100a` and
`sm_103a` (4 new libraries). A snapshot call stores every token's state
(`ssm_state_indices` given). A snapshot-noise program stages the SR
noise of a snapshot call once in 16 KiB of shared memory. It stores the
same bits as the program it replaces. An SR snapshot call selects it in
two cases:

- in place of the 16-token `l8r4` program, at 5 or more rounds and more
than 2 CTAs per SM (batch x heads > 2 x SM count);
- in place of the runtime-token-count program (T 9 to 15), at 10 or more
rounds.

All other calls launch the same program as on main.

The baseline is the previous Cake version: the same call on FlashInfer
main, with the FP16 state pool as shipped. Speedup is main time / PR
time, so a value above 1 means this PR is faster. Figures are B200 /
GB300, geomean (min..max). At the default 10 rounds, the speedup over
all 64 snapshot shapes is 1.06x (1.00x..1.45x) / 1.06x (1.00x..1.46x).
On the 11 shapes per GPU that the snapshot-noise program serves, it is
about 1.43x..1.46x. At 16 rounds the snapshot speedup is 1.11x
(0.99x..1.83x) / 1.10x (0.99x..1.79x). At 5 rounds it is 1.02x
(0.99x..1.17x) / 1.03x (0.99x..1.18x). On the 12 snapshot shapes of the
runtime n = 3 program, it is 1.16x / 1.15x (1.02x..1.36x) at 10 rounds
and 1.35x / 1.34x (1.19x..1.62x) at 16 rounds. Final-state calls stay at
1.00x (0.99x..1.01x / 0.99x..1.02x). FP32 and RNE calls also stay at
1.00x.

Program selection is now cached (host values only), so each eager call
also spends less host time. The saving is 3.6 to 6.9 us per call on
B200, where main takes about 58 to 66 us per call. On GB300 it is 4.0 to
10.1 us, where main takes about 77 to 103 us.

The FP32 state pool on all three targets, the RNE and other FP16
programs, the other decode routes and the SM90 chunked varlen prefill
programs are unchanged, and the family ships on `sm_90a`, `sm_100a` and
`sm_103a`.

Per-shape median kernel times follow. Speedup is main time / PR time,
measured with CUPTI, a cold L2 and eager calls, with both sides on the
same GPU: B200 (`sm_100a`, 148 SMs) and GB300 (`sm_103a`, 152 SMs), CUDA
13.4.

Classes: P = FP32 state; RNE = FP16 state, round to nearest even; S5 /
S10 / S16 = FP16 state, stochastic rounding with 5 / 10 / 16 Philox
rounds.

### Geomean (min..max) of main / PR per set, GPU and class

| set | rows | B200 P | B200 RNE | B200 S5 | B200 S10 | B200 S16 | GB300
P | GB300 RNE | GB300 S5 | GB300 S10 | GB300 S16 |
|---|---|---|---|---|---|---|---|---|---|---|---|
| (1) snapshot | 64 | 1.00 (0.99..1.01) | 1.00 (0.98..1.02) | 1.02
(0.99..1.17) | 1.06 (1.00..1.45) | 1.11 (0.99..1.83) | 1.00 (1.00..1.01)
| 1.00 (0.99..1.01) | 1.03 (0.99..1.18) | 1.06 (1.00..1.46) | 1.10
(0.99..1.79) |
| (2) snapshot, runtime n = 3 | 12 | 1.00 (1.00..1.00) | 1.00
(1.00..1.00) | 1.00 (1.00..1.00) | 1.16 (1.02..1.36) | 1.35 (1.19..1.62)
| 1.00 (1.00..1.00) | 1.00 (1.00..1.00) | 1.00 (1.00..1.00) | 1.15
(1.02..1.36) | 1.34 (1.19..1.62) |
| (3) final state | 144 | 1.00 (0.99..1.01) | 1.00 (0.99..1.01) | 1.00
(0.99..1.01) | 1.00 (0.99..1.01) | 1.00 (0.99..1.01) | 1.00 (0.99..1.02)
| 1.00 (0.98..1.02) | 1.00 (0.99..1.01) | 1.00 (0.99..1.02) | 1.00
(0.99..1.02) |
| (4) l8r4 T = 16 cell | 6 | 1.00 (1.00..1.00) | 1.00 (1.00..1.00) |
1.15 (1.13..1.17) | 1.45 (1.44..1.45) | 1.80 (1.79..1.82) | 1.00
(1.00..1.00) | 1.00 (1.00..1.00) | 1.17 (1.14..1.19) | 1.44 (1.43..1.46)
| 1.78 (1.76..1.79) |
| (4) runtime n = 3 cell | 32 | 1.00 (1.00..1.00) | 1.00 (1.00..1.00) |
1.00 (1.00..1.00) | 1.20 (1.01..1.38) | 1.39 (1.17..1.65) | 1.00
(1.00..1.00) | 1.00 (1.00..1.00) | 1.00 (1.00..1.00) | 1.19 (1.01..1.38)
| 1.38 (1.17..1.65) |

### (1) Snapshot calls (`ssm_state_indices` given), S10, all 64 shapes

Rows served by a new shared-memory noise program: B200 11, GB300 11; the
other rows launch the same program on both sides.

| T | H | B | B200 main us | B200 PR us | B200 speedup | GB300 main us |
GB300 PR us | GB300 speedup |
|---|---|---|---|---|---|---|---|---|
| 2 | 80 | 1 | 5.904 | 5.92 | 1.00 | 5.744 | 5.744 | 1.00 |
| 2 | 80 | 16 | 22.04 | 22.064 | 1.00 | 20.289 | 20.288 | 1.00 |
| 2 | 80 | 64 | 73.184 | 73.168 | 1.00 | 65.504 | 65.488 | 1.00 |
| 2 | 80 | 256 | 272.937 | 272.832 | 1.00 | 248.496 | 248.512 | 1.00 |
| 2 | 24 | 1 | 5.888 | 5.888 | 1.00 | 5.696 | 5.68 | 1.00 |
| 2 | 24 | 16 | 9.632 | 9.632 | 1.00 | 9.176 | 9.088 | 1.01 |
| 2 | 24 | 64 | 25.728 | 25.648 | 1.00 | 23.456 | 23.424 | 1.00 |
| 2 | 24 | 256 | 86.576 | 86.512 | 1.00 | 78.176 | 78.192 | 1.00 |
| 2 | 20 | 1 | 5.824 | 5.84 | 1.00 | 5.584 | 5.568 | 1.00 |
| 2 | 20 | 16 | 9.488 | 9.488 | 1.00 | 8.864 | 8.864 | 1.00 |
| 2 | 20 | 64 | 22.016 | 22.032 | 1.00 | 20.352 | 20.32 | 1.00 |
| 2 | 20 | 256 | 73.104 | 73.056 | 1.00 | 65.8 | 65.824 | 1.00 |
| 2 | 10 | 1 | 6.032 | 6.032 | 1.00 | 5.344 | 5.328 | 1.00 |
| 2 | 10 | 16 | 7.36 | 7.344 | 1.00 | 6.96 | 6.96 | 1.00 |
| 2 | 10 | 64 | 14.024 | 14.08 | 1.00 | 13.096 | 13.056 | 1.00 |
| 2 | 10 | 256 | 39.536 | 39.504 | 1.00 | 34.992 | 34.976 | 1.00 |
| 4 | 80 | 1 | 7.232 | 7.264 | 1.00 | 6.768 | 6.72 | 1.01 |
| 4 | 80 | 16 | 31.856 | 31.888 | 1.00 | 29.04 | 29.056 | 1.00 |
| 4 | 80 | 64 | 110.144 | 110.032 | 1.00 | 98.624 | 98.639 | 1.00 |
| 4 | 80 | 256 | 413.408 | 413.137 | 1.00 | 376.905 | 377.104 | 1.00 |
| 4 | 24 | 1 | 7.184 | 7.152 | 1.00 | 6.56 | 6.56 | 1.00 |
| 4 | 24 | 16 | 13.184 | 13.224 | 1.00 | 12.256 | 12.288 | 1.00 |
| 4 | 24 | 64 | 37.84 | 37.792 | 1.00 | 34.184 | 34.224 | 1.00 |
| 4 | 24 | 256 | 130.144 | 130.128 | 1.00 | 117.872 | 117.808 | 1.00 |
| 4 | 20 | 1 | 7.36 | 7.328 | 1.00 | 6.608 | 6.592 | 1.00 |
| 4 | 20 | 16 | 13.04 | 13.04 | 1.00 | 12.0 | 12.0 | 1.00 |
| 4 | 20 | 64 | 31.92 | 31.904 | 1.00 | 29.0 | 28.992 | 1.00 |
| 4 | 20 | 256 | 110.224 | 110.192 | 1.00 | 98.8 | 98.736 | 1.00 |
| 4 | 10 | 1 | 7.056 | 7.04 | 1.00 | 6.944 | 6.96 | 1.00 |
| 4 | 10 | 16 | 9.952 | 9.937 | 1.00 | 9.136 | 9.136 | 1.00 |
| 4 | 10 | 64 | 19.536 | 19.52 | 1.00 | 17.752 | 17.68 | 1.00 |
| 4 | 10 | 256 | 58.736 | 58.752 | 1.00 | 51.632 | 51.664 | 1.00 |
| 8 | 80 | 1 | 10.128 | 10.136 | 1.00 | 9.728 | 9.744 | 1.00 |
| 8 | 80 | 16 | 55.28 | 55.272 | 1.00 | 51.088 | 51.08 | 1.00 |
| 8 | 80 | 64 | 197.152 | 197.04 | 1.00 | 179.52 | 179.488 | 1.00 |
| 8 | 80 | 256 | 752.317 | 751.909 | 1.00 | 694.568 | 694.48 | 1.00 |
| 8 | 24 | 1 | 9.985 | 9.984 | 1.00 | 9.552 | 9.568 | 1.00 |
| 8 | 24 | 16 | 21.488 | 21.48 | 1.00 | 20.032 | 20.032 | 1.00 |
| 8 | 24 | 64 | 66.32 | 66.288 | 1.00 | 60.64 | 60.632 | 1.00 |
| 8 | 24 | 256 | 233.999 | 233.944 | 1.00 | 214.384 | 214.433 | 1.00 |
| 8 | 20 | 1 | 9.872 | 9.856 | 1.00 | 9.504 | 9.504 | 1.00 |
| 8 | 20 | 16 | 21.232 | 21.224 | 1.00 | 19.728 | 19.744 | 1.00 |
| 8 | 20 | 64 | 55.608 | 55.584 | 1.00 | 50.944 | 50.928 | 1.00 |
| 8 | 20 | 256 | 197.056 | 196.976 | 1.00 | 179.52 | 179.552 | 1.00 |
| 8 | 10 | 1 | 9.952 | 9.936 | 1.00 | 9.68 | 9.664 | 1.00 |
| 8 | 10 | 16 | 15.776 | 15.728 | 1.00 | 14.656 | 14.632 | 1.00 |
| 8 | 10 | 64 | 33.208 | 33.248 | 1.00 | 30.592 | 30.688 | 1.00 |
| 8 | 10 | 256 | 104.368 | 104.32 | 1.00 | 92.688 | 92.648 | 1.00 |
| 16 | 80 | 1 | 17.312 | 17.28 | 1.00 | 16.528 | 16.528 | 1.00 |
| 16 | 80 | 16 | 153.04 | 106.776 | 1.43 | 140.184 | 97.504 | 1.44 |
| 16 | 80 | 64 | 556.24 | 386.944 | 1.44 | 504.992 | 351.808 | 1.44 |
| 16 | 80 | 256 | 2165.722 | 1497.036 | 1.45 | 1975.8 | 1374.976 | 1.44
|
| 16 | 24 | 1 | 16.928 | 16.912 | 1.00 | 16.32 | 16.32 | 1.00 |
| 16 | 24 | 16 | 56.416 | 39.0 | 1.45 | 51.424 | 35.904 | 1.43 |
| 16 | 24 | 64 | 182.664 | 127.343 | 1.43 | 168.752 | 117.344 | 1.44 |
| 16 | 24 | 256 | 665.28 | 462.24 | 1.44 | 605.52 | 421.736 | 1.44 |
| 16 | 20 | 1 | 16.848 | 16.832 | 1.00 | 16.24 | 16.224 | 1.00 |
| 16 | 20 | 16 | 55.984 | 38.72 | 1.45 | 51.024 | 35.52 | 1.44 |
| 16 | 20 | 64 | 152.768 | 106.592 | 1.43 | 140.168 | 97.592 | 1.44 |
| 16 | 20 | 256 | 556.216 | 387.2 | 1.44 | 504.976 | 351.856 | 1.44 |
| 16 | 10 | 1 | 16.824 | 16.832 | 1.00 | 16.256 | 16.288 | 1.00 |
| 16 | 10 | 16 | 27.44 | 27.44 | 1.00 | 25.744 | 25.744 | 1.00 |
| 16 | 10 | 64 | 89.872 | 62.048 | 1.45 | 82.224 | 56.504 | 1.46 |
| 16 | 10 | 256 | 292.728 | 203.664 | 1.44 | 256.984 | 179.696 | 1.43 |

### (2) Snapshot calls of the runtime n = 3 program, S10, all 12 shapes

Rows served by a new shared-memory noise program: B200 12, GB300 12; the
other rows launch the same program on both sides.

| T | H | B | B200 main us | B200 PR us | B200 speedup | GB300 main us |
GB300 PR us | GB300 speedup |
|---|---|---|---|---|---|---|---|---|
| 10 | 80 | 16 | 139.663 | 113.935 | 1.23 | 132.032 | 107.512 | 1.23 |
| 10 | 80 | 64 | 454.273 | 425.584 | 1.07 | 412.809 | 392.736 | 1.05 |
| 10 | 80 | 256 | 1701.833 | 1671.138 | 1.02 | 1579.648 | 1546.737 |
1.02 |
| 10 | 20 | 16 | 55.536 | 41.52 | 1.34 | 52.328 | 39.152 | 1.34 |
| 10 | 20 | 64 | 139.895 | 113.671 | 1.23 | 132.128 | 107.128 | 1.23 |
| 10 | 20 | 256 | 453.44 | 424.265 | 1.07 | 411.84 | 391.856 | 1.05 |
| 12 | 80 | 16 | 165.68 | 133.864 | 1.24 | 156.064 | 126.128 | 1.24 |
| 12 | 80 | 64 | 538.104 | 499.568 | 1.08 | 487.872 | 461.672 | 1.06 |
| 12 | 80 | 256 | 2017.392 | 1965.616 | 1.03 | 1875.44 | 1823.263 | 1.03
|
| 12 | 20 | 16 | 65.904 | 48.432 | 1.36 | 62.016 | 45.6 | 1.36 |
| 12 | 20 | 64 | 165.312 | 133.536 | 1.24 | 155.856 | 125.672 | 1.24 |
| 12 | 20 | 256 | 537.937 | 498.16 | 1.08 | 487.904 | 460.336 | 1.06 |

<details>
<summary>(3) Final-state calls (no snapshot), S10, all 144
shapes</summary>

Rows served by a new shared-memory noise program: B200 0, GB300 0; the
other rows launch the same program on both sides.

| T | H | B | B200 main us | B200 PR us | B200 speedup | GB300 main us |
GB300 PR us | GB300 speedup |
|---|---|---|---|---|---|---|---|---|
| 1 | 80 | 1 | 4.495 | 4.496 | 1.00 | 4.272 | 4.296 | 0.99 |
| 1 | 80 | 16 | 14.441 | 14.416 | 1.00 | 13.48 | 13.536 | 1.00 |
| 1 | 80 | 64 | 45.936 | 45.832 | 1.00 | 41.792 | 41.744 | 1.00 |
| 1 | 80 | 256 | 172.4 | 172.304 | 1.00 | 156.736 | 156.719 | 1.00 |
| 1 | 24 | 1 | 3.743 | 3.712 | 1.01 | 3.552 | 3.552 | 1.00 |
| 1 | 24 | 16 | 6.704 | 6.704 | 1.00 | 6.416 | 6.432 | 1.00 |
| 1 | 24 | 64 | 16.559 | 16.544 | 1.00 | 15.344 | 15.328 | 1.00 |
| 1 | 24 | 256 | 54.832 | 54.864 | 1.00 | 49.696 | 49.665 | 1.00 |
| 1 | 20 | 1 | 3.696 | 3.696 | 1.00 | 3.424 | 3.44 | 1.00 |
| 1 | 20 | 16 | 6.48 | 6.48 | 1.00 | 6.208 | 6.208 | 1.00 |
| 1 | 20 | 64 | 14.448 | 14.48 | 1.00 | 13.568 | 13.584 | 1.00 |
| 1 | 20 | 256 | 46.272 | 46.256 | 1.00 | 41.856 | 41.888 | 1.00 |
| 1 | 10 | 1 | 3.552 | 3.552 | 1.00 | 3.36 | 3.36 | 1.00 |
| 1 | 10 | 16 | 5.824 | 5.824 | 1.00 | 5.504 | 5.504 | 1.00 |
| 1 | 10 | 64 | 9.352 | 9.335 | 1.00 | 9.008 | 8.864 | 1.02 |
| 1 | 10 | 256 | 25.12 | 25.12 | 1.00 | 22.608 | 22.608 | 1.00 |
| 2 | 80 | 1 | 5.776 | 5.792 | 1.00 | 5.52 | 5.504 | 1.00 |
| 2 | 80 | 16 | 20.175 | 20.176 | 1.00 | 18.752 | 18.704 | 1.00 |
| 2 | 80 | 64 | 66.032 | 66.032 | 1.00 | 59.824 | 59.824 | 1.00 |
| 2 | 80 | 256 | 246.952 | 246.896 | 1.00 | 226.528 | 226.56 | 1.00 |
| 2 | 24 | 1 | 5.672 | 5.664 | 1.00 | 5.376 | 5.376 | 1.00 |
| 2 | 24 | 16 | 8.8 | 8.752 | 1.01 | 8.4 | 8.32 | 1.01 |
| 2 | 24 | 64 | 23.392 | 23.392 | 1.00 | 21.648 | 21.656 | 1.00 |
| 2 | 24 | 256 | 78.592 | 78.528 | 1.00 | 71.44 | 71.456 | 1.00 |
| 2 | 20 | 1 | 5.584 | 5.568 | 1.00 | 5.328 | 5.328 | 1.00 |
| 2 | 20 | 16 | 8.528 | 8.544 | 1.00 | 8.096 | 8.032 | 1.01 |
| 2 | 20 | 64 | 20.176 | 20.192 | 1.00 | 18.736 | 18.736 | 1.00 |
| 2 | 20 | 256 | 66.448 | 66.472 | 1.00 | 60.336 | 60.303 | 1.00 |
| 2 | 10 | 1 | 5.52 | 5.536 | 1.00 | 5.376 | 5.376 | 1.00 |
| 2 | 10 | 16 | 6.784 | 6.816 | 1.00 | 6.44 | 6.448 | 1.00 |
| 2 | 10 | 64 | 13.04 | 13.04 | 1.00 | 12.24 | 12.208 | 1.00 |
| 2 | 10 | 256 | 35.952 | 35.904 | 1.00 | 32.112 | 32.08 | 1.00 |
| 3 | 80 | 1 | 6.144 | 6.16 | 1.00 | 5.824 | 5.824 | 1.00 |
| 3 | 80 | 16 | 23.328 | 23.328 | 1.00 | 21.28 | 21.264 | 1.00 |
| 3 | 80 | 64 | 77.824 | 77.792 | 1.00 | 69.792 | 69.832 | 1.00 |
| 3 | 80 | 256 | 290.496 | 290.496 | 1.00 | 265.32 | 265.279 | 1.00 |
| 3 | 24 | 1 | 6.064 | 6.064 | 1.00 | 5.648 | 5.648 | 1.00 |
| 3 | 24 | 16 | 10.015 | 10.032 | 1.00 | 9.44 | 9.424 | 1.00 |
| 3 | 24 | 64 | 27.376 | 27.344 | 1.00 | 24.864 | 24.824 | 1.00 |
| 3 | 24 | 256 | 92.032 | 92.023 | 1.00 | 82.936 | 82.976 | 1.00 |
| 3 | 20 | 1 | 6.096 | 6.08 | 1.00 | 5.728 | 5.696 | 1.01 |
| 3 | 20 | 16 | 9.792 | 9.768 | 1.00 | 9.2 | 9.232 | 1.00 |
| 3 | 20 | 64 | 23.28 | 23.296 | 1.00 | 21.272 | 21.264 | 1.00 |
| 3 | 20 | 256 | 78.129 | 78.112 | 1.00 | 69.616 | 69.616 | 1.00 |
| 3 | 10 | 1 | 5.696 | 5.696 | 1.00 | 5.424 | 5.424 | 1.00 |
| 3 | 10 | 16 | 7.728 | 7.696 | 1.00 | 7.152 | 7.12 | 1.00 |
| 3 | 10 | 64 | 14.528 | 14.528 | 1.00 | 13.456 | 13.44 | 1.00 |
| 3 | 10 | 256 | 42.0 | 41.983 | 1.00 | 37.08 | 37.104 | 1.00 |
| 4 | 80 | 1 | 6.272 | 6.303 | 1.00 | 5.872 | 5.872 | 1.00 |
| 4 | 80 | 16 | 26.272 | 26.255 | 1.00 | 23.984 | 24.0 | 1.00 |
| 4 | 80 | 64 | 89.6 | 89.584 | 1.00 | 80.048 | 80.064 | 1.00 |
| 4 | 80 | 256 | 333.936 | 333.8 | 1.00 | 306.128 | 306.081 | 1.00 |
| 4 | 24 | 1 | 6.24 | 6.208 | 1.01 | 5.648 | 5.68 | 0.99 |
| 4 | 24 | 16 | 11.424 | 11.441 | 1.00 | 10.512 | 10.544 | 1.00 |
| 4 | 24 | 64 | 31.2 | 31.184 | 1.00 | 28.16 | 28.144 | 1.00 |
| 4 | 24 | 256 | 105.743 | 105.712 | 1.00 | 95.68 | 95.608 | 1.00 |
| 4 | 20 | 1 | 6.112 | 6.128 | 1.00 | 5.728 | 5.696 | 1.01 |
| 4 | 20 | 16 | 11.248 | 11.232 | 1.00 | 10.304 | 10.28 | 1.00 |
| 4 | 20 | 64 | 26.352 | 26.336 | 1.00 | 23.992 | 23.968 | 1.00 |
| 4 | 20 | 256 | 89.183 | 89.183 | 1.00 | 80.224 | 80.176 | 1.00 |
| 4 | 10 | 1 | 6.032 | 6.064 | 0.99 | 5.568 | 5.568 | 1.00 |
| 4 | 10 | 16 | 8.496 | 8.512 | 1.00 | 7.744 | 7.76 | 1.00 |
| 4 | 10 | 64 | 16.112 | 16.112 | 1.00 | 14.912 | 14.88 | 1.00 |
| 4 | 10 | 256 | 48.079 | 48.096 | 1.00 | 42.304 | 42.24 | 1.00 |
| 5 | 80 | 1 | 7.208 | 7.216 | 1.00 | 6.768 | 6.784 | 1.00 |
| 5 | 80 | 16 | 32.08 | 32.08 | 1.00 | 29.192 | 29.215 | 1.00 |
| 5 | 80 | 64 | 109.536 | 109.504 | 1.00 | 98.792 | 98.816 | 1.00 |
| 5 | 80 | 256 | 415.512 | 415.481 | 1.00 | 379.183 | 379.209 | 1.00 |
| 5 | 24 | 1 | 7.088 | 7.104 | 1.00 | 6.624 | 6.64 | 1.00 |
| 5 | 24 | 16 | 13.344 | 13.329 | 1.00 | 12.336 | 12.368 | 1.00 |
| 5 | 24 | 64 | 37.776 | 37.76 | 1.00 | 34.399 | 34.448 | 1.00 |
| 5 | 24 | 256 | 130.464 | 130.424 | 1.00 | 117.808 | 117.84 | 1.00 |
| 5 | 20 | 1 | 7.008 | 7.008 | 1.00 | 6.592 | 6.592 | 1.00 |
| 5 | 20 | 16 | 13.072 | 13.088 | 1.00 | 12.128 | 12.16 | 1.00 |
| 5 | 20 | 64 | 32.16 | 32.144 | 1.00 | 29.184 | 29.184 | 1.00 |
| 5 | 20 | 256 | 109.92 | 109.872 | 1.00 | 98.624 | 98.64 | 1.00 |
| 5 | 10 | 1 | 6.992 | 7.0 | 1.00 | 6.496 | 6.504 | 1.00 |
| 5 | 10 | 16 | 10.096 | 10.096 | 1.00 | 9.312 | 9.296 | 1.00 |
| 5 | 10 | 64 | 19.584 | 19.616 | 1.00 | 18.112 | 18.096 | 1.00 |
| 5 | 10 | 256 | 59.184 | 59.2 | 1.00 | 51.488 | 51.488 | 1.00 |
| 6 | 80 | 1 | 7.848 | 7.84 | 1.00 | 7.408 | 7.408 | 1.00 |
| 6 | 80 | 16 | 35.904 | 35.904 | 1.00 | 32.768 | 32.8 | 1.00 |
| 6 | 80 | 64 | 124.8 | 124.784 | 1.00 | 111.68 | 111.704 | 1.00 |
| 6 | 80 | 256 | 470.968 | 470.752 | 1.00 | 429.209 | 429.184 | 1.00 |
| 6 | 24 | 1 | 7.632 | 7.632 | 1.00 | 7.232 | 7.248 | 1.00 |
| 6 | 24 | 16 | 14.992 | 14.992 | 1.00 | 13.824 | 13.856 | 1.00 |
| 6 | 24 | 64 | 42.72 | 42.672 | 1.00 | 38.864 | 38.88 | 1.00 |
| 6 | 24 | 256 | 148.192 | 148.144 | 1.00 | 133.504 | 133.432 | 1.00 |
| 6 | 20 | 1 | 7.583 | 7.6 | 1.00 | 7.184 | 7.216 | 1.00 |
| 6 | 20 | 16 | 14.648 | 14.672 | 1.00 | 13.568 | 13.568 | 1.00 |
| 6 | 20 | 64 | 35.896 | 35.889 | 1.00 | 32.784 | 32.8 | 1.00 |
| 6 | 20 | 256 | 124.576 | 124.496 | 1.00 | 111.96 | 111.952 | 1.00 |
| 6 | 10 | 1 | 7.552 | 7.536 | 1.00 | 6.992 | 7.008 | 1.00 |
| 6 | 10 | 16 | 11.2 | 11.16 | 1.00 | 10.432 | 10.44 | 1.00 |
| 6 | 10 | 64 | 21.904 | 21.888 | 1.00 | 20.032 | 20.016 | 1.00 |
| 6 | 10 | 256 | 66.496 | 66.433 | 1.00 | 58.384 | 58.488 | 1.00 |
| 7 | 80 | 1 | 8.416 | 8.416 | 1.00 | 7.856 | 7.856 | 1.00 |
| 7 | 80 | 16 | 40.312 | 40.288 | 1.00 | 36.464 | 36.416 | 1.00 |
| 7 | 80 | 64 | 138.896 | 138.84 | 1.00 | 125.52 | 125.535 | 1.00 |
| 7 | 80 | 256 | 522.878 | 522.687 | 1.00 | 483.376 | 483.408 | 1.00 |
| 7 | 24 | 1 | 8.176 | 8.16 | 1.00 | 7.776 | 7.776 | 1.00 |
| 7 | 24 | 16 | 16.272 | 16.288 | 1.00 | 15.072 | 15.04 | 1.00 |
| 7 | 24 | 64 | 47.68 | 47.648 | 1.00 | 43.296 | 43.264 | 1.00 |
| 7 | 24 | 256 | 164.792 | 164.704 | 1.00 | 150.032 | 149.952 | 1.00 |
| 7 | 20 | 1 | 8.208 | 8.207 | 1.00 | 7.696 | 7.712 | 1.00 |
| 7 | 20 | 16 | 15.856 | 15.84 | 1.00 | 14.848 | 14.832 | 1.00 |
| 7 | 20 | 64 | 40.145 | 40.081 | 1.00 | 36.448 | 36.44 | 1.00 |
| 7 | 20 | 256 | 139.008 | 138.904 | 1.00 | 125.224 | 125.216 | 1.00 |
| 7 | 10 | 1 | 8.127 | 8.112 | 1.00 | 7.488 | 7.488 | 1.00 |
| 7 | 10 | 16 | 12.24 | 12.24 | 1.00 | 11.312 | 11.32 | 1.00 |
| 7 | 10 | 64 | 24.304 | 24.304 | 1.00 | 22.176 | 22.224 | 1.00 |
| 7 | 10 | 256 | 73.887 | 73.84 | 1.00 | 65.168 | 65.28 | 1.00 |
| 8 | 80 | 1 | 8.32 | 8.32 | 1.00 | 8.08 | 8.112 | 1.00 |
| 8 | 80 | 16 | 43.424 | 43.424 | 1.00 | 39.984 | 39.984 | 1.00 |
| 8 | 80 | 64 | 152.577 | 152.52 | 1.00 | 137.871 | 137.824 | 1.00 |
| 8 | 80 | 256 | 578.063 | 577.87 | 1.00 | 532.952 | 532.976 | 1.00 |
| 8 | 24 | 1 | 8.176 | 8.16 | 1.00 | 7.936 | 7.928 | 1.00 |
| 8 | 24 | 16 | 17.248 | 17.264 | 1.00 | 16.176 | 16.08 | 1.01 |
| 8 | 24 | 64 | 51.84 | 51.792 | 1.00 | 47.44 | 47.424 | 1.00 |
| 8 | 24 | 256 | 181.616 | 181.6 | 1.00 | 165.216 | 165.233 | 1.00 |
| 8 | 20 | 1 | 8.176 | 8.16 | 1.00 | 7.936 | 7.936 | 1.00 |
| 8 | 20 | 16 | 17.056 | 17.04 | 1.00 | 15.856 | 15.872 | 1.00 |
| 8 | 20 | 64 | 43.456 | 43.472 | 1.00 | 39.936 | 39.904 | 1.00 |
| 8 | 20 | 256 | 152.047 | 151.935 | 1.00 | 138.0 | 137.976 | 1.00 |
| 8 | 10 | 1 | 8.143 | 8.144 | 1.00 | 7.92 | 7.936 | 1.00 |
| 8 | 10 | 16 | 12.8 | 12.816 | 1.00 | 11.904 | 11.856 | 1.00 |
| 8 | 10 | 64 | 26.048 | 26.072 | 1.00 | 24.256 | 24.24 | 1.00 |
| 8 | 10 | 256 | 80.816 | 80.808 | 1.00 | 71.432 | 71.424 | 1.00 |
| 16 | 80 | 1 | 13.28 | 13.32 | 1.00 | 12.896 | 12.896 | 1.00 |
| 16 | 80 | 16 | 78.256 | 78.2 | 1.00 | 71.616 | 71.616 | 1.00 |
| 16 | 80 | 64 | 277.807 | 277.703 | 1.00 | 252.288 | 252.287 | 1.00 |
| 16 | 80 | 256 | 1073.216 | 1073.064 | 1.00 | 978.816 | 978.751 | 1.00
|
| 16 | 24 | 1 | 13.025 | 13.056 | 1.00 | 12.784 | 12.768 | 1.00 |
| 16 | 24 | 16 | 30.0 | 30.032 | 1.00 | 27.776 | 27.776 | 1.00 |
| 16 | 24 | 64 | 93.136 | 93.104 | 1.00 | 85.792 | 85.752 | 1.00 |
| 16 | 24 | 256 | 332.952 | 332.896 | 1.00 | 302.104 | 302.096 | 1.00 |
| 16 | 20 | 1 | 13.056 | 13.072 | 1.00 | 12.784 | 12.784 | 1.00 |
| 16 | 20 | 16 | 29.744 | 29.744 | 1.00 | 27.456 | 27.456 | 1.00 |
| 16 | 20 | 64 | 78.641 | 78.624 | 1.00 | 71.616 | 71.584 | 1.00 |
| 16 | 20 | 256 | 279.136 | 279.008 | 1.00 | 251.841 | 251.872 | 1.00 |
| 16 | 10 | 1 | 13.008 | 13.024 | 1.00 | 12.608 | 12.608 | 1.00 |
| 16 | 10 | 16 | 21.183 | 21.168 | 1.00 | 20.272 | 20.288 | 1.00 |
| 16 | 10 | 64 | 46.56 | 46.528 | 1.00 | 42.712 | 42.736 | 1.00 |
| 16 | 10 | 256 | 147.616 | 147.584 | 1.00 | 129.504 | 129.504 | 1.00 |

</details>

<details>
<summary>(4) Launch-class cells of the new programs (l8r4 T = 16 cell
and runtime n = 3 cell), S5 / S10 / S16</summary>

| T | H | B | class | B200 main us | B200 PR us | B200 speedup | GB300
main us | GB300 PR us | GB300 speedup |
|---|---|---|---|---|---|---|---|---|---|
| 16 | 80 | 4 | S5 | 44.128 | 37.984 | 1.16 | 41.352 | 35.088 | 1.18 |
| 16 | 80 | 4 | S10 | 55.84 | 38.568 | 1.45 | 51.152 | 35.544 | 1.44 |
| 16 | 80 | 4 | S16 | 70.712 | 39.44 | 1.79 | 63.912 | 36.336 | 1.76 |
| 16 | 80 | 8 | S5 | 71.12 | 60.992 | 1.17 | 65.92 | 55.648 | 1.18 |
| 16 | 80 | 8 | S10 | 89.768 | 61.952 | 1.45 | 82.4 | 56.528 | 1.46 |
| 16 | 80 | 8 | S16 | 113.136 | 63.296 | 1.79 | 102.992 | 57.728 | 1.78
|
| 16 | 80 | 32 | S5 | 227.912 | 200.457 | 1.14 | 203.263 | 177.224 |
1.15 |
| 16 | 80 | 32 | S10 | 292.472 | 203.232 | 1.44 | 256.928 | 179.608 |
1.43 |
| 16 | 80 | 32 | S16 | 373.504 | 207.2 | 1.80 | 325.392 | 183.224 | 1.78
|
| 16 | 80 | 128 | S5 | 848.302 | 748.574 | 1.13 | 785.312 | 686.032 |
1.14 |
| 16 | 80 | 128 | S10 | 1096.165 | 758.239 | 1.45 | 998.736 | 695.104 |
1.44 |
| 16 | 80 | 128 | S16 | 1409.028 | 772.806 | 1.82 | 1269.808 | 709.04 |
1.79 |
| 16 | 20 | 32 | S5 | 71.184 | 60.976 | 1.17 | 65.984 | 55.656 | 1.19 |
| 16 | 20 | 32 | S10 | 89.807 | 61.96 | 1.45 | 82.456 | 56.528 | 1.46 |
| 16 | 20 | 32 | S16 | 113.136 | 63.272 | 1.79 | 103.048 | 57.768 | 1.78
|
| 16 | 10 | 32 | S5 | 44.16 | 37.936 | 1.16 | 41.248 | 35.024 | 1.18 |
| 16 | 10 | 32 | S10 | 55.856 | 38.544 | 1.45 | 51.024 | 35.504 | 1.44 |
| 16 | 10 | 32 | S16 | 70.752 | 39.424 | 1.79 | 63.896 | 36.304 | 1.76 |
| 9 | 80 | 1 | S5 | 31.68 | 31.664 | 1.00 | 30.08 | 30.064 | 1.00 |
| 9 | 80 | 1 | S10 | 36.496 | 28.384 | 1.29 | 34.672 | 26.88 | 1.29 |
| 9 | 80 | 1 | S16 | 42.431 | 29.024 | 1.46 | 40.272 | 27.536 | 1.46 |
| 9 | 80 | 16 | S5 | 111.376 | 111.376 | 1.00 | 104.768 | 104.784 | 1.00
|
| 9 | 80 | 16 | S10 | 128.88 | 105.888 | 1.22 | 121.472 | 99.48 | 1.22 |
| 9 | 80 | 16 | S16 | 150.632 | 108.112 | 1.39 | 141.776 | 101.697 |
1.39 |
| 9 | 80 | 64 | S5 | 358.225 | 358.264 | 1.00 | 327.44 | 327.328 | 1.00
|
| 9 | 80 | 64 | S10 | 415.432 | 392.776 | 1.06 | 378.487 | 363.36 | 1.04
|
| 9 | 80 | 64 | S16 | 488.472 | 400.792 | 1.22 | 441.055 | 370.192 |
1.19 |
| 9 | 80 | 256 | S5 | 1360.52 | 1360.64 | 1.00 | 1261.912 | 1262.199 |
1.00 |
| 9 | 80 | 256 | S10 | 1560.473 | 1544.304 | 1.01 | 1449.352 | 1430.032
| 1.01 |
| 9 | 80 | 256 | S16 | 1839.705 | 1573.488 | 1.17 | 1705.728 | 1457.416
| 1.17 |
| 9 | 20 | 1 | S5 | 30.832 | 30.816 | 1.00 | 29.536 | 29.552 | 1.00 |
| 9 | 20 | 1 | S10 | 35.728 | 27.536 | 1.30 | 34.16 | 26.464 | 1.29 |
| 9 | 20 | 1 | S16 | 41.68 | 28.2 | 1.48 | 39.76 | 27.168 | 1.46 |
| 9 | 20 | 16 | S5 | 42.208 | 42.144 | 1.00 | 39.952 | 39.888 | 1.00 |
| 9 | 20 | 16 | S10 | 50.912 | 38.344 | 1.33 | 48.064 | 36.256 | 1.33 |
| 9 | 20 | 16 | S16 | 61.504 | 39.456 | 1.56 | 58.024 | 37.24 | 1.56 |
| 9 | 20 | 64 | S5 | 110.816 | 110.76 | 1.00 | 104.16 | 104.256 | 1.00 |
| 9 | 20 | 64 | S10 | 128.432 | 105.288 | 1.22 | 120.96 | 99.079 | 1.22
|
| 9 | 20 | 64 | S16 | 150.048 | 107.704 | 1.39 | 141.28 | 101.168 | 1.40
|
| 9 | 20 | 256 | S5 | 356.839 | 356.863 | 1.00 | 326.728 | 326.8 | 1.00
|
| 9 | 20 | 256 | S10 | 414.175 | 392.103 | 1.06 | 377.92 | 363.329 |
1.04 |
| 9 | 20 | 256 | S16 | 487.222 | 400.031 | 1.22 | 441.096 | 370.16 |
1.19 |
| 11 | 80 | 1 | S5 | 37.392 | 37.424 | 1.00 | 35.856 | 35.808 | 1.00 |
| 11 | 80 | 1 | S10 | 43.392 | 33.232 | 1.31 | 41.504 | 31.744 | 1.31 |
| 11 | 80 | 1 | S16 | 50.608 | 33.856 | 1.49 | 48.368 | 32.368 | 1.49 |
| 11 | 80 | 16 | S5 | 132.368 | 132.288 | 1.00 | 124.72 | 124.816 | 1.00
|
| 11 | 80 | 16 | S10 | 153.896 | 125.424 | 1.23 | 145.168 | 117.904 |
1.23 |
| 11 | 80 | 16 | S16 | 180.784 | 127.688 | 1.42 | 170.079 | 120.048 |
1.42 |
| 11 | 80 | 64 | S5 | 429.048 | 428.84 | 1.00 | 392.144 | 392.128 | 1.00
|
| 11 | 80 | 64 | S10 | 498.88 | 467.208 | 1.07 | 454.264 | 432.784 |
1.05 |
| 11 | 80 | 64 | S16 | 588.399 | 475.233 | 1.24 | 532.912 | 439.647 |
1.21 |
| 11 | 80 | 256 | S5 | 1630.184 | 1630.281 | 1.00 | 1514.303 | 1514.136
| 1.00 |
| 11 | 80 | 256 | S10 | 1875.408 | 1838.944 | 1.02 | 1744.128 | 1704.16
| 1.02 |
| 11 | 80 | 256 | S16 | 2217.064 | 1868.032 | 1.19 | 2061.287 | 1731.696
| 1.19 |
| 11 | 20 | 1 | S5 | 36.816 | 36.848 | 1.00 | 34.768 | 34.72 | 1.00 |
| 11 | 20 | 1 | S10 | 42.807 | 32.832 | 1.30 | 40.352 | 30.616 | 1.32 |
| 11 | 20 | 1 | S16 | 50.008 | 33.44 | 1.50 | 47.28 | 31.216 | 1.51 |
| 11 | 20 | 16 | S5 | 50.608 | 50.552 | 1.00 | 47.712 | 47.68 | 1.00 |
| 11 | 20 | 16 | S10 | 61.272 | 45.304 | 1.35 | 57.68 | 42.704 | 1.35 |
| 11 | 20 | 16 | S16 | 74.224 | 46.4 | 1.60 | 69.856 | 43.712 | 1.60 |
| 11 | 20 | 64 | S5 | 132.408 | 132.32 | 1.00 | 124.144 | 124.0 | 1.00 |
| 11 | 20 | 64 | S10 | 154.104 | 125.336 | 1.23 | 144.496 | 117.68 |
1.23 |
| 11 | 20 | 64 | S16 | 180.768 | 127.616 | 1.42 | 169.56 | 119.824 |
1.42 |
| 11 | 20 | 256 | S5 | 428.32 | 428.04 | 1.00 | 391.576 | 391.535 | 1.00
|
| 11 | 20 | 256 | S10 | 498.704 | 466.328 | 1.07 | 453.911 | 432.08 |
1.05 |
| 11 | 20 | 256 | S16 | 588.52 | 474.304 | 1.24 | 532.968 | 439.184 |
1.21 |
| 13 | 80 | 1 | S5 | 43.296 | 43.319 | 1.00 | 41.488 | 41.504 | 1.00 |
| 13 | 80 | 1 | S10 | 50.384 | 38.112 | 1.32 | 48.169 | 36.4 | 1.32 |
| 13 | 80 | 1 | S16 | 58.872 | 38.784 | 1.52 | 56.28 | 37.024 | 1.52 |
| 13 | 80 | 16 | S5 | 154.201 | 154.144 | 1.00 | 144.976 | 144.952 |
1.00 |
| 13 | 80 | 16 | S10 | 180.032 | 145.089 | 1.24 | 169.04 | 136.36 | 1.24
|
| 13 | 80 | 16 | S16 | 211.344 | 147.472 | 1.43 | 198.32 | 138.528 |
1.43 |
| 13 | 80 | 64 | S5 | 499.742 | 499.727 | 1.00 | 456.656 | 456.591 |
1.00 |
| 13 | 80 | 64 | S10 | 582.63 | 540.975 | 1.08 | 530.304 | 500.833 |
1.06 |
| 13 | 80 | 64 | S16 | 689.294 | 548.958 | 1.26 | 624.192 | 507.857 |
1.23 |
| 13 | 80 | 256 | S5 | 1903.786 | 1903.85 | 1.00 | 1763.36 | 1763.168 |
1.00 |
| 13 | 80 | 256 | S10 | 2193.971 | 2136.043 | 1.03 | 2035.649 | 1976.376
| 1.03 |
| 13 | 80 | 256 | S16 | 2603.099 | 2165.426 | 1.20 | 2411.16 | 2004.288
| 1.20 |
| 13 | 20 | 1 | S5 | 42.56 | 42.512 | 1.00 | 40.56 | 40.56 | 1.00 |
| 13 | 20 | 1 | S10 | 49.632 | 37.24 | 1.33 | 47.264 | 35.408 | 1.33 |
| 13 | 20 | 1 | S16 | 58.144 | 37.968 | 1.53 | 55.312 | 36.08 | 1.53 |
| 13 | 20 | 16 | S5 | 58.688 | 58.704 | 1.00 | 55.6 | 55.544 | 1.00 |
| 13 | 20 | 16 | S10 | 71.296 | 52.248 | 1.36 | 67.264 | 49.312 | 1.36 |
| 13 | 20 | 16 | S16 | 86.672 | 53.304 | 1.63 | 81.68 | 50.352 | 1.62 |
| 13 | 20 | 64 | S5 | 153.52 | 153.44 | 1.00 | 144.577 | 144.592 | 1.00
|
| 13 | 20 | 64 | S10 | 179.056 | 144.433 | 1.24 | 168.912 | 135.928 |
1.24 |
| 13 | 20 | 64 | S16 | 210.416 | 146.824 | 1.43 | 198.256 | 138.064 |
1.44 |
| 13 | 20 | 256 | S5 | 498.774 | 498.67 | 1.00 | 455.904 | 455.6 | 1.00
|
| 13 | 20 | 256 | S10 | 581.999 | 539.894 | 1.08 | 529.696 | 499.912 |
1.06 |
| 13 | 20 | 256 | S16 | 689.118 | 547.854 | 1.26 | 623.864 | 507.0 |
1.23 |
| 15 | 80 | 1 | S5 | 49.328 | 49.296 | 1.00 | 46.96 | 46.96 | 1.00 |
| 15 | 80 | 1 | S10 | 57.408 | 43.088 | 1.33 | 54.688 | 40.904 | 1.34 |
| 15 | 80 | 1 | S16 | 67.304 | 43.752 | 1.54 | 64.096 | 41.552 | 1.54 |
| 15 | 80 | 16 | S5 | 175.519 | 175.496 | 1.00 | 165.416 | 165.409 |
1.00 |
| 15 | 80 | 16 | S10 | 204.912 | 164.304 | 1.25 | 193.497 | 154.784 |
1.25 |
| 15 | 80 | 16 | S16 | 241.127 | 166.559 | 1.45 | 227.743 | 157.072 |
1.45 |
| 15 | 80 | 64 | S5 | 571.224 | 571.12 | 1.00 | 520.24 | 520.303 | 1.00
|
| 15 | 80 | 64 | S10 | 667.465 | 614.992 | 1.09 | 605.2 | 568.417 | 1.06
|
| 15 | 80 | 64 | S16 | 791.48 | 622.911 | 1.27 | 714.681 | 575.495 |
1.24 |
| 15 | 80 | 256 | S5 | 2175.545 | 2175.608 | 1.00 | 2014.288 | 2014.136
| 1.00 |
| 15 | 80 | 256 | S10 | 2510.848 | 2428.033 | 1.03 | 2328.752 | 2246.32
| 1.04 |
| 15 | 80 | 256 | S16 | 2990.729 | 2457.697 | 1.22 | 2768.168 | 2274.392
| 1.22 |
| 15 | 20 | 1 | S5 | 48.353 | 48.304 | 1.00 | 46.0 | 45.992 | 1.00 |
| 15 | 20 | 1 | S10 | 56.496 | 42.144 | 1.34 | 53.696 | 39.84 | 1.35 |
| 15 | 20 | 1 | S16 | 66.336 | 42.816 | 1.55 | 63.008 | 40.472 | 1.56 |
| 15 | 20 | 16 | S5 | 67.072 | 67.0 | 1.00 | 63.079 | 63.072 | 1.00 |
| 15 | 20 | 16 | S10 | 81.616 | 59.216 | 1.38 | 76.592 | 55.584 | 1.38 |
| 15 | 20 | 16 | S16 | 99.32 | 60.344 | 1.65 | 93.248 | 56.528 | 1.65 |
| 15 | 20 | 64 | S5 | 174.936 | 174.887 | 1.00 | 164.544 | 164.496 |
1.00 |
| 15 | 20 | 64 | S10 | 204.623 | 163.655 | 1.25 | 192.576 | 154.192 |
1.25 |
| 15 | 20 | 64 | S16 | 240.743 | 166.096 | 1.45 | 226.816 | 156.383 |
1.45 |
| 15 | 20 | 256 | S5 | 570.369 | 570.505 | 1.00 | 519.776 | 519.808 |
1.00 |
| 15 | 20 | 256 | S10 | 667.049 | 614.081 | 1.09 | 605.168 | 567.144 |
1.07 |
| 15 | 20 | 256 | S16 | 791.808 | 621.937 | 1.27 | 715.12 | 574.248 |
1.25 |

</details>


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added support for stochastic state rounding during FP16 decode,
including per-token state snapshots.
* Expanded GPU kernel support for additional architectures and CUDA
versions.
* **Bug Fixes**
* Improved decode dispatch to select programs based on rounding and
snapshot settings, with more reliable handling of runtime fallbacks.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery H <averyh@nvidia.com>

### [0cf9d70](https://github.com/flashinfer-ai/flashinfer/commit/0cf9d70d8db1dbc74dc34a4d69c33b60602414ac)

- **作者**: Yuxian Qiu
- **时间**: 2026-11-20T06:22:46Z
- **提交信息**: refactor(prims-ts): derive MLA CP bounds from global sequence lengths (#9641)

<!-- .github/pull_request_template.md -->

## 📌 Description

Follow up merged #5489 by replacing Prims-TS MLA decode's
`use_kv_bounds` / per-query `kv_bounds` interface with context-parallel
topology and global request lengths.

- `plan()` specializes `cp_world` and `cp_interleave_size`.
- `run()` receives `cp_rank` and graph-live global `seq_lens_kv`,
including the current query tokens. Planned `max_kv_len` and block
tables remain rank-local physical capacity.
- Both 1-CTA and 2-CTA kernels derive rank-local lengths and causal
prefixes directly. Packed queries use actual `qo_indptr` differences;
rank changes do not enter the compilation key.
- Preserve CP=1 behavior, empty/inactive-row contracts, split reduction
and LSE. The optional neutral writer uses a flattened grid without a
65,535-request grid-Y limit.
- Validate split-KV cluster size against the CUDA device’s launch limit
as well as occupancy. On B200 an occupancy query can report active
clusters for 17 CTAs, even though only 16 can launch. Over-limit
automatic splits use the separate reducer.
- Update validation, trace schemas/examples, documentation and the
existing focused regression file. Seven GPU cases remain; no large new
matrix is introduced.

The branch is based on upstream main. CP documentation updates are
confined to the PrimTS READMEs; `docs/development/backend_notes.md` is
unchanged. No new context-kernel or standard-attention changes are
introduced by this PR.

### Retained integration performance evidence

Same MLA implementation validated in the TRT-LLM integration, with full
FP8 KV cache, page size 128, 96 heads, latent/RoPE dimensions 512/64.
H-D1/H-D8: local batch 1/8, Q=8, CP8 rank 0, local history 512 (global
total 4104). D-D8/D-D16: local batch 8/16, Q=6, CP1, history 4096.

Values are **previous PrimTS → updated PrimTS microseconds**, using the
conservative order of balanced AB/BA runs and predefined confirmations.
These are retained integration-snapshot measurements, not a new GPU run
on this freshly main-based PR head.

| Scope | Case | Rubin SM107 | B200 SM100 | B300 SM103 |
|---|---|---|---|---|
| Raw generation | H-D1 | 14.240 → 13.752 | 20.480 → 20.480 | 20.448 →
18.432 |
| Raw generation | H-D8 | 18.000 → 17.936 | 16.368 → 16.384 | 16.352 →
16.368 |
| Raw generation | D-D8 | 26.656 → 26.624 | 36.832 → 36.864 | 34.784 →
34.816 |
| Raw generation | D-D16 | 30.552 → 30.584 | 65.504 → 65.536 | 65.792 →
66.261 |
| Attention backend | H-D1 | 17.680 → 17.536 | 24.576 → 24.608 | 24.448
→ 22.560 |
| Attention backend | H-D8 | 23.360 → 23.840 | 24.576 → 24.472 | 22.496
→ 22.496 |
| Attention backend | D-D8 | 30.464 → 30.472 | 40.960 → 40.944 | 38.896
→ 38.896 |
| Attention backend | D-D16 | 36.984 → 36.992 | 73.712 → 73.712 | 73.744
→ 73.752 |

50 warmups and 100 CUDA-event samples per process, CUDA graph replay,
2×L2 flush outside event intervals, clocks unlocked;
startup/JIT/reference work excluded. Backend timing includes
metadata/preprocessing/cache work, raw generation does not. TRT-LLM
still prepares compatibility bounds for other providers, so no
eliminated producer cost is claimed. Rubin H-D8 backend has a valid
+2.055% regression, narrowly above the predefined 2% cap; other Rubin
generation scopes and all Blackwell scopes pass. These are rank-local
component results, not CP communication, full-model throughput or TTFT.

The consumer also contains a separate native single-`is_lse` merge
cleanup and dispatch-policy update; those are not FlashInfer changes.

## 🔍 Related Issues

- Follow-up to merged #5489.
- Consumer integration:
https://github.com/NVIDIA/TensorRT-LLM/pull/19395
- Existing experimental PrimTS tracking context: #4829, #5059, #5082.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

> Changed-file pre-commit checks passed, including mypy and Ruff. The
existing checkout disables automatic hooks; hooks were run manually. A
full-repository hook run is not claimed.

## 🧪 Tests

- Cluster-limit regression: the existing device-local occupancy test
passed. Three B200 numerical checks covered the 17-CTA fallback on both
devices and a legal 16-CTA cluster; both previously failing TRT-LLM TP2
MTP tests passed.

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/attention/test_attention_ts_mla_cp.py
tests/attention/test_attention_ts_mla_decode.py
tests/trace/test_fi_trace_template_consistency.py`

Current-head local results:
- Focused CPU contract checks in `test_attention_ts_mla_decode.py`: **9
passed**.
- Trace consistency: **1,240 passed, 2 skipped**.
- CP GPU regression collection: **7 cases**, not executed again during
publication.
- Earlier matching-implementation GPU validation: seven CP kernel cases
plus strict two-GPU Helix/MTP replay on Rubin; retained TRT-LLM
focused/native/backend checks and paired generation measurements on
Rubin, B200 and B300. These historical results are not represented as a
fresh full-suite CI run.
- No FlashInfer CI bot command was issued; CI is left to the maintainer.

## 🔬 Experimental Track

<!-- Only for PRs submitted under the experimental policy
(CONTRIBUTING.md → "Experimental APIs and Backends").
     Leave this section untouched for normal PRs. -->

- [x] This PR updates existing **experimental** PrimTS APIs marked with
`@flashinfer_experimental_api`. Tracking context: #5489, #4829, #5059,
#5082; a separate graduation-tracking issue is not claimed.
- [ ] The tracking issue names an owner, the reason for the experimental
path, and a graduation plan with a target release.
- [ ] Core changes are limited to a thin entry point (signature, shared
validation, feature-gate check, backend selection, handoff).
- [ ] Tests live in `tests/experimental/` and were validated on the
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
tests/experimental/test_experimental_api.py
```

As in #5489, this scope covers shared experimental opt-in behavior, not
kernel correctness. Existing PrimTS implementation/tests remain under
`flashinfer/attention/prims_ts/` and `tests/attention/`; the targeted
attention tests above cover the kernels. Relocation/graduation is
outside this follow-up.

## Reviewer Notes

Please focus on global-to-local prefix arithmetic, packed-query
alignment, split-reduction empty rows and graph-live metadata. This was
developed and validated with Codex assistance. No NVIDIA-specific
notices were added to FlashInfer files.



<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added context-parallel support for paged MLA decode, with configurable
rank and interleave settings. Global KV lengths are mapped to rank-local
cache prefixes.
* Empty rows on ranks with no locally visible KV tokens now return zero
output and negative-infinity LSE by default; this behavior can be
disabled.
* **Bug Fixes**
* Improved handling of supported cluster sizes when selecting attention
launch configurations.
* **Documentation**
* Updated MLA decode guidance and trace examples for context-parallel
settings, local cache capacity, and empty-row behavior.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Yuxian Qiu <142763828+yuxianq@users.noreply.github.com>

### [7eae60f](https://github.com/flashinfer-ai/flashinfer/commit/7eae60fb4f9ee437df67ba9891f7b6691a12fee0)

- **作者**: Jupiter
- **时间**: 2026-11-20T05:04:11Z
- **提交信息**: feat(moe): MXFP8 locality-domain intermediate split + add on Rubin (#9541)

## 📌 Description

Adds a locality-domain execution mode to the MXFP8 x MXFP8 CuTe-DSL
fused MoE on Rubin (SM107), selected with
`localized_options={"fc2_split": "k"}`. Each locality domain holds half
of every expert's intermediate dimension, run FC1 and FC2 on its own
stream and adds its partial sum to the output, with no join between FC1
and FC2.

- **Weights**: each of the two domain shards holds half of every local
expert's FC1 rows (`[E, I/2, H]`) and the matching half of its FC2
reduction columns (`[E, H, I/2]`) in that domain's memory, with scale
factors sliced at 128-row atoms.
- **Execution**: routing runs once on the caller's stream. Each domain
then runs FC1 into a private intermediate buffer and FC2 over its K half
on its green-context stream, and both domains add their partial sums
into the token output with the fused atomic finalize. The only joins are
the fork after routing and the final join. If FC1 or FC2 throws an
exception on either locality domain, the caller's stream still waits for
both domains' streams before the exception is passed to the caller.
Gated activations are not supported in this mode.
- **Options**: `fc2_accumulator="float32"` (default) sums both domains
in an FP32 buffer and rounds once; `"output"` adds BF16 partial sums
straight into the output. `output_memset="overlap_fc1"` zeroes the
output on the main stream while FC1 runs; `"before_fork"` zeroes it
first. Optional per-domain `gemm1_out` / `gemm1_out_scale` buffers avoid
per-call allocation under CUDA graphs.
- **SM107 MXFP8 kernels**: the native Rubin gather kernel gathers NVFP4
scale factors only and has neither MXFP8 output nor ClampedRelu2, so
MXFP8 x MXFP8 on SM107 runs the SM100-family FC1 gather kernel and FC2
finalize kernel, with or without locality domains.
- **SM107 ClampedRelu2 clamp**: the SM100-family FC1 kernel gains a
compile-time option, `clamped_relu2_tanh_approx` (default `False`), that
computes the soft clamp `L * tanh(x / L)` with one `tanh.approx.f32` per
element. The FC1 wrapper enables it only for SM107 with MXFP8 x MXFP8
and ClampedRelu2, and the option is part of the FC1 compile-cache key.
With the option off, the kernel compiles the existing epilogue unchanged
(`cutlass.const_expr` branch), so SM100/SM103 behavior does not change.
- **SM107 MXFP8 API**: the SM107 rejections of `quant_mode="mxfp8"` and
of ClampedRelu2 with MXFP8 are lifted. The localized runner accepts
MXFP8, with the new options in its cache key.
- The existing W4A4 locality-domain path keeps `fc2_split="n"` and is
unchanged.

Consumer: Megatron-LM's `flashinfer_cutedsl` inference MoE backend uses
this mode for its locality-domain option.

## 🔍 Related Issues

NVIDIA/Megatron-LM#9260 (the consumer).

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
whitespace-separated — a starting point for `@flashinfer-bot run
<targets>` / `/bot run <targets>`, reviewers may adjust):
`tests/moe/test_cute_dsl_fused_moe.py
tests/moe/test_cute_dsl_mxfp8_moe.py
tests/moe/test_cute_dsl_moe_cache_key.py`

- New `test_localized_mxfp8_intermediate_split_matches_full_width`
(SM107 with CUDA locality domains) compares the localized K split
against the full-width MXFP8 kernel: both accumulators, both memset
placements, ReLU2 and ClampedRelu2, top-1 and top-8, eager and
CUDA-graph replay with caller-provided FC1 buffers.
- New `test_mxfp8_clamped_relu2_tanh_approx_only_on_sm107` checks, from
the arguments the FC1 kernel is built with, that the
`tanh.approx.f32` option is enabled for MXFP8 ClampedRelu2 on SM107 and
disabled for ReLU2 and on other GPUs.
- Rubin (SM107): the CuTe-DSL fused MoE suite
(`tests/moe/test_cute_dsl_fused_moe.py`, all valid tactics,
`test_cute_dsl_mxfp8_moe.py`, `test_cute_dsl_moe_cache_key.py`,
`test_routed_nvfp4.py`, the pre-FC2 reference) passes with no failures
(549 passed; the rest skip as hardware- or build-specific), including
the existing localized tests.
- Blackwell (GB300, SM103): the same suites pass with no failures (975
passed). Every test that exists on `main` has the same outcome as on
`main`; the new split tests skip and the new option test confirms the
option is off. The MXFP8 ClampedRelu2 fused MoE compiles the FC1 kernel
with the option off and runs in the same time as without this PR.
- End to end in Megatron-LM (MXFP8 hybrid MoE, EP4 decode with CUDA
graphs), greedy outputs agree with Megatron's stock grouped-GEMM MoE on
a 4-GPU Rubin node, with and without locality domains, and to the same
degree on a 4-GPU GB300 node.

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

- `blackwell/blockscaled_contiguous_gather_grouped_gemm_act_fusion.py`
gains one constructor option,
`clamped_relu2_tanh_approx`, default `False` and rejected without
ClampedRelu2. Both clamp sites keep the existing code in the `else`
branch of a compile-time `cutlass.const_expr`, so a kernel compiled with
the option off is the same as before. Only the FC1 wrapper sets it, and
only on SM107 for MXFP8 ClampedRelu2; it is in the compile-cache key, so
kernels compiled with and without it never share a cache entry.
- The split tests need SM107 with CUDA locality domains (CUDA 13.4) and
skip elsewhere, so CI without Rubin runs only the option test and the
unchanged full-width suite.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added localized MXFP8 support for mixture-of-experts workloads,
including K-split FC2 processing and configurable accumulation and
output-buffer handling.
* Added support for the ClampedRelu2 activation option on compatible
SM107 MXFP8 configurations.
* Localized runner configurations now accept MXFP8 and pass localized
execution options through to the operation.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: Chenshu Zhu <chenshuz@nvidia.com>

### [b5dd106](https://github.com/flashinfer-ai/flashinfer/commit/b5dd106aa1a9bce876c38ef7c77f8e6613ac94e0)

- **作者**: Bo Li
- **时间**: 2026-11-20T04:51:21Z
- **提交信息**: perf(moe_ep): finalize the split layer's experts into the combine input (#8498)

## 📌 Description

The expert-parallel split layer finalizes its fused MoE straight into
the communication's combine input region, and leaves alone the rows the
NVLink one-sided combine never reads.

- **Combine input in place.** `MoEEpSplitLayer` passed a
runner-allocated MoE output to `comm.combine()`, which the NVLink
one-sided fence combine then staged into the workspace's combine input
region with a prepare kernel: 84 us per layer for DeepSeek-V4.1-Flash at
4096 tokens per rank on 8 B300s. The split kernel context now carries
`get_combine_input_buffer()`, the fused MoE backend hands it to the
activation pack as its output, and `PrimsTsRunner` finalizes into it.
Runners that do not write in place keep allocating their own output.
- **Rows the combine never reads.** The finalize writes one row per
received row slot, and a zero row for every slot whose token has no
local expert. The NVLink one-sided combines never read those rows:
dispatch sends a token only to the ranks owning one of its valid expert
ids. The finalize kernel params get a runtime
`zeroRowsWithoutLocalExpert` flag (no new instantiations), true by
default and honored by every finalize variant; the staged finalize ops
take it as `zero_rows_without_local_expert`, `MoEActivationPack` carries
it for `PrimsTsRunner`, and
`MoEEpCommunication.combine_reads_only_local_expert_rows` tells the
split layer when to clear it. `NVLinkOneSidedAlltoAll` declares it; Cake
does not, since its dispatch also sends a token to the rank an invalid
pick maps to.

DeepSeek-V4.1-Flash on 8 B300s, perfect routing (a quarter of the
received rows have no local expert), fence protocol: finalize 20.1 ->
14.7 us and layer 1190.5 -> 1185.1 us at T = 4096; 7.3 -> 5.3 us and
357.1 -> 352.0 us at T = 1024.

## 🔍 Related Issues

Layer 4 of the stack
https://github.com/flashinfer-ai/flashinfer/stack/8499 (four PRs):
1. #8495 routing and finalize for precomputed top-k
2. #8496 Prims-TS weight cache policy per expert
3. #8497 Prims-TS MXFP4 x MXFP8 MoE GEMMs
4. #8498 **this PR**: split layer: finalize the experts into the combine
input

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

- `tests/moe_ep/test_moe_ep_communication_multirank.py`: 40 passed with
4 and with 8 ranks (38 on `main`; the two new cases are this PR's).
- `tests/moe_ep/test_nvlink_one_sided.py`: 62 passed, 1 skipped;
`test_nvlink_one_sided_lamport.py`: 70 passed, 3 skipped (4 ranks).
- moe_ep unit suite (`tests/moe_ep/run_tests.sh unit`): 1555 passed,
with the same 26 errors (`test_moe_ep_sm103_w4a16_cake_mega.py`, nvshmem
not installed in the test image) and 1 failure
(`test_mega_layer_validation.py`, a DeepGEMM assertion) as `main`.
- `tests/moe_ep/test_split_fused_moe_kernel_vs_reference.py` 14 passed;
`tests/moe/test_unified_moe.py` 434 passed;
`tests/moe/test_unified_moe_prims_ts.py` 39 passed, 1 xfailed;
`tests/prims_ts/test_moe_finalize_two_input.py` 40 passed (35 on
`main`); `tests/cpu/moe_ep` 520 and `tests/cpu/moe` 216 passed.
- `tests/experimental/test_cake_stepfun_moe.py` 299 passed;
`test_cake_stepfun_moe_api.py` 380 passed. On `main`, its
`test_full_path_finalize_matches_native_kernel` fails four times: the
test passes 11 arguments to `trtllm_moe_run_finalize`, which takes 12;
the second commit updates the call.
- Not run: the nccl_ep / nixl_ep multi-rank tests (not built in the test
image).

After the review fixes, rerun at the stack top 45cae150a: this PR adds
e82ea4d2a (a caller's output buffer must be on the activations' device
and 16-byte aligned; the multirank Lamport case skips on every rank
alike when the layer has no Lamport transport) and 45cae150a (the
partitioned-finalize option tests folded into one).
`tests/moe_ep/test_moe_ep_communication_multirank.py` 40 passed (4
ranks); moe_ep unit suite 1555 passed, with the same failure and errors
as `main`; `tests/moe/test_unified_moe.py` 434 passed;
`tests/moe/test_unified_moe_prims_ts.py` 39 passed, 1 xfailed;
`tests/moe_ep/test_split_fused_moe_kernel_vs_reference.py` 14 passed;
`tests/experimental/test_cake_stepfun_moe_api.py::test_full_path_finalize_matches_native_kernel`
4 passed.

Rebased onto #8497's review follow-up (d5be1d3db); the commits of this
PR are unchanged apart from the position of #8497's new test next to the
one this PR extends. At 244f295b2:
`tests/moe/test_unified_moe_prims_ts.py` 40 passed, 1 xfailed;
`tests/cpu/prims_ts` 368 passed.

Rebased onto main at 1bdba8725, with three changes for it. #8576 moved
the activation pack of `FusedMoeSplitKernelBackend` into
`_activation_pack`, which has no `dim0`/`dim1`, so the in-place output
check takes the row count from `expert_tensors` (d99334e3c). #8770
selects the NVLinkOneSided protocol with `sync_protocol` and names the
flag-free one sentinel, so
`test_split_layer_leaves_rows_the_combine_never_reads` runs
`sync_protocol` fence and sentinel, and the comment on
`combine_reads_only_local_expert_rows` names those two combines
(f5b312313, 1f38a9a24). #8610 moved the PDL wait of
`finalizeKernelVecLoad` and `finalizeKernelSmallBatch` before their
reads of the routing outputs, and #8495 and #8497 do the same for the
warp-per-token finalize kernels, so with `zeroRowsWithoutLocalExpert`
off, every finalize kernel returns for a token without a local expert
after the wait (f5b312313). At eac484dc8:
`tests/moe_ep/test_moe_ep_communication_multirank.py` 40 passed on 4 and
on 8 ranks; `test_nvlink_one_sided_sentinel.py` 68 passed, 3 skipped (4
ranks); `test_nvlink_one_sided.py` 62 passed, 1 skipped; moe_ep unit
suite 1795 passed, with the same failure and errors as main;
`test_split_fused_moe_kernel_vs_reference.py` 14 passed;
`tests/moe/test_unified_moe.py` 434 passed;
`test_unified_moe_prims_ts.py` 40 passed, 1 xfailed;
`tests/experimental/test_cake_stepfun_moe_api.py` 380 passed;
`test_cake_stepfun_moe.py` 299 passed; 22 of the 31 files of
`tests/prims_ts` pass except 6 cases of `test_batched_gemm_mx.py`, 6 of
`test_batched_gemm_fp4_fc1.py` and 4 of
`test_batched_gemm_c_row_stride.py`, which fail the same way on main
1bdba8725; `tests/cpu/{prims_ts,moe_ep,moe}` 369 / 615 / 217 passed.

Rebased onto main at 88077bda8. #7203 adds the `gemm2_output2` argument
(`None`) to the `trtllm_moe_run_finalize` call of
`test_full_path_finalize_matches_native_kernel` in
`tests/experimental/test_cake_stepfun_moe_api.py`, which this PR already
passed along with `zero_rows_without_local_expert`; the call is the same
as before (46deb17fe, was f5b312313). The other commits are unchanged.
Below this PR, #8495 adds b47c71dc4, which fixes the SM80 and SM89 build
of the routing kernels that failed the first CI run, and 952ef731f,
which launches no empty warp-per-token finalize slice. At 39aa95d58:
`tests/moe_ep/test_moe_ep_communication_multirank.py` 40 passed on 4 and
on 8 ranks; `test_nvlink_one_sided_sentinel.py` 68 passed, 3 skipped (4
ranks); `test_nvlink_one_sided.py` 62 passed, 1 skipped; moe_ep unit
suite 1905 passed, with the failure and errors of main 1bdba8725 and 5
failures of
`test_sm107_tuning.py::test_benchmark_reports_staging_and_capture_allocation`,
which fail the same way on main 88077bda8 (the test's arguments lack the
benchmark's `eager_completed_wall`);
`test_split_fused_moe_kernel_vs_reference.py` 14 passed;
`tests/moe/test_unified_moe.py` 434 passed;
`test_unified_moe_prims_ts.py` 40 passed, 1 xfailed;
`tests/experimental/test_cake_stepfun_moe_api.py` 380 passed;
`test_cake_stepfun_moe.py` 299 passed; 22 of the 31 files of
`tests/prims_ts` pass except the same 16 cases as before the rebase,
which fail the same way on main 1bdba8725;
`tests/cpu/{prims_ts,moe_ep,moe}` 369 / 858 / 217 passed.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Write finalized MoE outputs into a caller-provided buffer when it
meets the required shape, data type, device, contiguity, and alignment
requirements.
* On supported execution paths, choose whether rows for tokens without a
local expert are zeroed or left unchanged. Some communication paths can
leave rows that the combine step does not read unwritten.
* **Bug Fixes**
* Finalization applies the zero-row setting consistently across
supported execution paths, including multi-expert token handling.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Bo Li <22713281+bobboli@users.noreply.github.com>

### [38201b8](https://github.com/flashinfer-ai/flashinfer/commit/38201b8e2830c3ff463b12d95fb3aaa70646254a)

- **作者**: Bo Li
- **时间**: 2026-11-20T04:51:20Z
- **提交信息**: perf(prims_ts): faster MXFP4 x MXFP8 MoE GEMMs and tuning (#8497)

## 📌 Description

Faster Prims-TS MXFP4 x MXFP8 MoE GEMMs and tuning.

| Commit | Change |
|---|---|
| MXFP4 weights in 64-byte K blocks | `PrimsTsConfig.prepare_weights`
stores MXFP4 x MXFP8 weights BlockMajorK in 64-byte K blocks, `[experts,
K_bytes / 64, Mn, 64]`, so a pipeline stage reads contiguous 8 KB
regions instead of one short segment per weight row. Padded formats
always take 64-byte blocks, the box width of their tensor map format.
The runner infers the layout from the rank of the FP4 weights, so MajorK
views keep working. |
| deeper-pipelined tile-256 / 128 / 64 configs | More pipeline stages
for the MX FC1 (and tile-64 FC2) configs; the config version of cached
tactics is bumped since tactic indices change. |
| precompile a tuning pass | `PrimsTsRunner.precompile_tactics`
delegates to the inner runner; the MXFP4 x MXFP8 runner compiles each
distinct FC1 and FC2 GEMM once, and every rank starts at its
LOCAL_RANK-th share of the list, so ranks load from disk what another
one compiled. Tuning DeepSeek-V4.1-Flash experts for an EP8 batch of one
token per rank with no compiled GEMMs on disk: 420 s -> 80 s. |
| fused finalize in the FC2 epilogue | When tokens average at most one
local expert (as under expert parallelism), the FC2 epilogue stores
every token whose only local expert it computes straight into the MoE
output, scaled by its routing weight. `finalizeKernelMultiExpertTokens`
then only writes the zero rows of tokens without a local expert and
reduces the tokens with several. Selected by
`BatchedGemmConfig.fused_finalize_top_k`; the finalize kernels of the
trtllm-gen backend are unchanged. |

MoE compute stage, DeepSeek-V4.1-Flash experts (hidden 5120, 384
experts, top-6, inter 2304), EP8 on B300 (us), per change:

| T per rank | 64-byte K blocks | tile-256 FC1 (fresh tuning) | fused
finalize |
|---:|---|---|---|
| 64 | 159.9 -> 155.4 | | 148.8 -> 146.8 |
| 512 | 192.0 -> 187.9 | | 184.7 -> 175.5 |
| 1024 | 230.3 -> 229.6 | | 224.6 -> 204.5 |
| 2048 | 390.3 -> 387.5 | 386.2 -> 364.4 | 363.9 -> 329.6 |
| 4096 | 712.6 -> 709.1 | 706.7 -> 669.6 | 671.7 -> 603.3 |

DeepSeek-V4-Pro and Kimi-K3 expert shapes are in the commit messages.

### TODO

- [ ] Include the Prims-TS config-table version in the unified runner's
tuning-cache key, so that a persisted tuning cache of an earlier version
cannot select a changed tactic; the gap predates this PR
(https://github.com/flashinfer-ai/flashinfer/pull/8497#discussion_r4489343729).

## 🔍 Related Issues

Layer 3 of the stack
https://github.com/flashinfer-ai/flashinfer/stack/8499 (four PRs):
1. #8495 routing and finalize for precomputed top-k
2. #8496 Prims-TS weight cache policy per expert
3. #8497 **this PR**: Prims-TS MXFP4 x MXFP8 MoE GEMMs
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

Rebased over #7833, which set `num_load_b_warps` of the existing tile-64
MX FC1 rows to 0 (automatic: four load-B warps). The tile-64 rows this
PR adds keep one load-B warp, the configuration measured above.

After the review fixes, rerun at the stack top 45cae150a: this PR adds
295b2ff2f (the fused FC2 finalize predicates its stores on the hidden
size and computes their offsets in Int64; both finalize entry points
share the input checks; the routing-weight dtype is part of the FC2
compile-cache key; top-k mismatches and missing pointers of a fused
launch are rejected) and 50d866bce (trims the MX GEMM and tuning tests).
Checks outside the suite: two-CTA FC2 tactics at hidden size 384
differed from the unfused finalize in 11 to 32 of 300 rows before the
fix and match after it; 524,289 tokens at hidden size 4096 faulted
before and match after it. `tests/prims_ts/test_batched_gemm_mx.py` 55
passed, 1 skipped, with the same 6 failures as `main`;
`test_batched_gemm_c_row_stride.py` 20 passed, with the same 4 failures
as `main`; `test_moe_bf16_support.py` 70 passed;
`test_moe_finalize_two_input.py` 40 passed; `test_moe_nvfp4_support.py`
14 passed; `tests/moe/test_unified_moe_prims_ts.py` 39 passed, 1
xfailed; `tests/moe/test_prims_ts_fp8_block_scale_moe.py` 11 passed.

Review follow-up, 9ccbc439f and d5be1d3db: `apply_fused_finalize` logs
at debug level why an FC2 config keeps the unfused finalize, and
`test_mxfp4_mxfp8_fused_finalize_two_cta_fc2_past_hidden` pins a two-CTA
FC2 tactic at hidden size 384 and checks the fused finalize against the
unfused one bit for bit; with the bound of 295b2ff2f removed it fails.
At d5be1d3db: `tests/moe/test_unified_moe_prims_ts.py` 39 passed, 1
xfailed; `tests/cpu/prims_ts` 368 passed. At the stack top 244f295b2:
`tests/moe/test_unified_moe_prims_ts.py` 40 passed, 1 xfailed;
`tests/cpu/prims_ts` 368 passed.

Rebased onto main at 1bdba8725. The new
`trtllm_moe_run_finalize_multi_expert_tokens` precedes
`trtllm_moe_run_deepseek_fp8_activation` with the `sf_block_size`
argument #8666 added. `finalizeKernelMultiExpertTokens` now waits on the
PDL primary before it reads the routing outputs, as every finalize
kernel does with #8610 and #8495, so it also writes the zero rows of
tokens without a local expert after the wait (d078e20dd). On the EP8
shape above, its span grows by 0.3 to 0.8 us at T = 8..4096 per rank
(3.79 -> 4.27 us at T = 8, 16.10 -> 16.88 us at 4096); the
fused-finalize column above predates this. The other commits are
unchanged. At b5bb2a1c8: `tests/moe/test_unified_moe_prims_ts.py` 39
passed, 1 xfailed; `tests/prims_ts/test_batched_gemm_mx.py -k
"TestMxfp4BlockMajorK or deep_pipeline or evict_first_weights"` 12
passed; `test_moe_bf16_support.py` 73 passed;
`tests/moe/test_prims_ts_fp8_block_scale_moe.py` 12 passed;
`tests/cpu/prims_ts` 369 passed, 2 skipped. At the stack top (#8498,
eac484dc8): `tests/moe/test_unified_moe_prims_ts.py` 40 passed, 1
xfailed; 22 of the 31 files of `tests/prims_ts` pass except 6 cases of
`test_batched_gemm_mx.py`, 6 of `test_batched_gemm_fp4_fc1.py` and 4 of
`test_batched_gemm_c_row_stride.py`, which fail the same way on main
1bdba8725.

Rebased onto main at 88077bda8. 952ef731f in #8495 launches only the
warp-per-token finalize slices that hold steps; the grid now comes from
`warpPerTokenGrid` (18dd9f59a, was d078e20dd), which both warp-per-token
finalize kernels use, so `finalizeKernelMultiExpertTokens` launches no
empty slice either. The other commits are unchanged. At 6c155af45:
`tests/moe/test_unified_moe_prims_ts.py` 39 passed, 1 xfailed;
`tests/prims_ts/test_batched_gemm_mx.py -k "TestMxfp4BlockMajorK or
deep_pipeline or evict_first_weights"` 12 passed;
`test_moe_bf16_support.py` 73 passed;
`tests/moe/test_prims_ts_fp8_block_scale_moe.py` 12 passed;
`tests/cpu/prims_ts` 369 passed, 2 skipped. At the stack top (#8498,
39aa95d58): `tests/moe/test_unified_moe_prims_ts.py` 40 passed, 1
xfailed; 22 of the 31 files of `tests/prims_ts` pass except the same 16
cases as before the rebase (6 of `test_batched_gemm_mx.py`, 6 of
`test_batched_gemm_fp4_fc1.py`, 4 of
`test_batched_gemm_c_row_stride.py`), which fail the same way on main
1bdba8725.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* MXFP4×MXFP8 MoE workloads can combine finalization with the FC2
operation, including cases with zero, one, or multiple local experts.
* Prims-TS supports MXFP4×MXFP8 weights in BlockMajorK layout, with
automatic weight preparation.
* Expanded MXFP4×MXFP8 configurations support a broader range of
workloads.
* **Bug Fixes**
  * Tokens with no local experts now receive zeroed output rows.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Bo Li <22713281+bobboli@users.noreply.github.com>

### [5cd7ab0](https://github.com/flashinfer-ai/flashinfer/commit/5cd7ab08e2a7e4b607f011080f3601350ce95fdc)

- **作者**: eigen
- **时间**: 2026-11-20T04:00:42Z
- **提交信息**: feat(cake_gdn): opt-in Cake CP and "auto" backends for chunk_gated_delta_rule_paged (SM100/SM103/SM107) (#9704)

`chunk_gated_delta_rule_paged` gets an opt-in `backend="cake_gdn"`. It
adds the paged FP32-state-pool form of the Cake GDN context-parallel
(CP) prefill: four state-fixup forms (SIMT row-split, 2-CTA ring,
UTCMMA64, UTCMMA128) and four chunk-output forms (fp16 or bf16 inputs,
each full-block or ragged). The baseline is the default
`backend="flashinfer"` serial chunked kernel. Against it, the new
backend is up to 4.25× faster (Hq,Hv 2,4; N=1; T=16384) and 2.53× faster
with the same heads at N=4. The gain shrinks as N·Hv grows, and at N·Hv
≥ 64 the new backend is slower (0.42–0.44× at Hq,Hv 16,32, N=4), so it
is meant for small batch·heads and long sequences. `backend="auto"` is
also opt-in: it picks `cake_gdn` only when the caller passes
`aligned_prefixes=True` (the promise that every prefix is a multiple of
64) and the batch is inside the band measured below, and `flashinfer`
everywhere else. The band, with S = N·Hv and L the new tokens per
sequence: S ≤ 12 and L ≥ 2048 on every architecture; on `sm_100a` also S
≤ 24 and L ≥ 4096, or S ≤ 32 and L ≥ 6144; on `sm_103a` also S ≤ 32 and
L ≥ 4096; on `sm_107a` also S ≤ 32 and L ≥ 4096, or S ≤ 48 and L ≥ 6144.
Every measured row inside it is faster with `cake_gdn`. The default
stays `flashinfer`, so after this PR a row runs `cake_gdn` only when the
caller passes `backend="auto"` with `aligned_prefixes=True` (last
column) or `backend="cake_gdn"`.

The other Cake GDN prefill variants, the unpaged CP prefill (fp16/bf16,
with carried initial/final state and checkpoint outputs) and the
affine-split prefill, are already in FlashInfer, and the family ships on
`sm_100a`, `sm_103a` and `sm_107a`.

NVIDIA GB300 (Blackwell, `sm_103a`), CUDA 13.0 runtime (PyTorch
2.14.1+cu130). bf16 q/k/v, head dim 128, Hq = Hk < Hv, FP32 state pool,
page size 1024, N sequences of T new tokens each, checkpoints at every
page boundary, final state written in place. Each time is one call
captured in a CUDA graph, measured as CUPTI kernel time with cold L2
(median of 30 replays, then median over 3 alternating-order groups).
Times in µs. Regressions are in bold.

| Hq=Hk, Hv | N | T (new tokens / seq) | prefix | flashinfer (µs) |
cake_gdn (µs) | speedup | `auto` + `aligned_prefixes=True` picks
cake_gdn |
|---|---|---|---|---|---|---|---|
| 2, 4 | 1 | 2048 | 0 | 65.2 | 52.5 | 1.24× | yes |
| 2, 4 | 1 | 2048 | 4096 | 66.1 | 51.5 | 1.28× | yes |
| 2, 4 | 1 | 4096 | 0 | 121.3 | 59.8 | 2.03× | yes |
| 2, 4 | 1 | 4096 | 4096 | 122.7 | 60.2 | 2.04× | yes |
| 2, 4 | 1 | 8192 | 0 | 234.1 | 81.0 | 2.89× | yes |
| 2, 4 | 1 | 8192 | 4096 | 235.2 | 79.9 | 2.94× | yes |
| 2, 4 | 1 | 16384 | 0 | 459.1 | 108.4 | 4.24× | yes |
| 2, 4 | 1 | 16384 | 4096 | 460.7 | 108.3 | 4.25× | yes |
| 2, 4 | 2 | 2048 | 0 | 65.1 | 55.9 | 1.16× | yes |
| 2, 4 | 2 | 2048 | 4096 | 65.9 | 56.0 | 1.18× | yes |
| 2, 4 | 2 | 4096 | 0 | 121.2 | 66.7 | 1.82× | yes |
| 2, 4 | 2 | 4096 | 4096 | 122.4 | 65.5 | 1.87× | yes |
| 2, 4 | 2 | 8192 | 0 | 233.4 | 88.0 | 2.65× | yes |
| 2, 4 | 2 | 8192 | 4096 | 234.9 | 87.9 | 2.67× | yes |
| 2, 4 | 2 | 16384 | 0 | 458.9 | 120.8 | 3.80× | yes |
| 2, 4 | 2 | 16384 | 4096 | 459.9 | 120.8 | 3.81× | yes |
| 2, 4 | 4 | 2048 | 0 | 65.1 | 62.4 | 1.04× | no |
| 2, 4 | 4 | 2048 | 4096 | 66.3 | 63.7 | 1.04× | no |
| 2, 4 | 4 | 4096 | 0 | 121.4 | 79.7 | 1.52× | yes |
| 2, 4 | 4 | 4096 | 4096 | 122.5 | 80.8 | 1.52× | yes |
| 2, 4 | 4 | 8192 | 0 | 234.2 | 116.3 | 2.01× | yes |
| 2, 4 | 4 | 8192 | 4096 | 235.5 | 117.8 | 2.00× | yes |
| 2, 4 | 4 | 16384 | 0 | 459.5 | 181.7 | 2.53× | yes |
| 2, 4 | 4 | 16384 | 4096 | 460.8 | 182.7 | 2.52× | yes |
| 4, 8 | 1 | 2048 | 0 | 65.6 | 56.0 | 1.17× | yes |
| 4, 8 | 1 | 2048 | 4096 | 66.2 | 55.7 | 1.19× | yes |
| 4, 8 | 1 | 4096 | 0 | 121.7 | 66.4 | 1.83× | yes |
| 4, 8 | 1 | 4096 | 4096 | 122.9 | 66.8 | 1.84× | yes |
| 4, 8 | 1 | 8192 | 0 | 235.0 | 89.1 | 2.64× | yes |
| 4, 8 | 1 | 8192 | 4096 | 235.5 | 89.3 | 2.64× | yes |
| 4, 8 | 1 | 16384 | 0 | 460.0 | 121.2 | 3.80× | yes |
| 4, 8 | 1 | 16384 | 4096 | 461.3 | 121.8 | 3.79× | yes |
| 4, 8 | 2 | 2048 | 0 | 65.4 | 61.7 | 1.06× | no |
| 4, 8 | 2 | 2048 | 4096 | 66.5 | 63.7 | 1.04× | no |
| 4, 8 | 2 | 4096 | 0 | 121.9 | 81.2 | 1.50× | yes |
| 4, 8 | 2 | 4096 | 4096 | 123.0 | 82.0 | 1.50× | yes |
| 4, 8 | 2 | 8192 | 0 | 234.9 | 117.5 | 2.00× | yes |
| 4, 8 | 2 | 8192 | 4096 | 235.4 | 117.5 | 2.00× | yes |
| 4, 8 | 2 | 16384 | 0 | 459.1 | 180.8 | 2.54× | yes |
| 4, 8 | 2 | 16384 | 4096 | 460.3 | 182.2 | 2.53× | yes |
| 4, 8 | 4 | 2048 | 0 | 65.6 | 69.1 | **0.95×** | no |
| 4, 8 | 4 | 2048 | 4096 | 66.7 | 70.4 | **0.95×** | no |
| 4, 8 | 4 | 4096 | 0 | 122.6 | 103.0 | 1.19× | yes |
| 4, 8 | 4 | 4096 | 4096 | 123.4 | 104.5 | 1.18× | yes |
| 4, 8 | 4 | 8192 | 0 | 235.1 | 168.0 | 1.40× | yes |
| 4, 8 | 4 | 8192 | 4096 | 236.0 | 169.1 | 1.40× | yes |
| 4, 8 | 4 | 16384 | 0 | 460.5 | 299.1 | 1.54× | yes |
| 4, 8 | 4 | 16384 | 4096 | 461.7 | 300.5 | 1.54× | yes |
| 8, 16 | 1 | 2048 | 0 | 66.2 | 63.0 | 1.05× | no |
| 8, 16 | 1 | 2048 | 4096 | 66.7 | 63.8 | 1.05× | no |
| 8, 16 | 1 | 4096 | 0 | 122.4 | 80.7 | 1.52× | yes |
| 8, 16 | 1 | 4096 | 4096 | 123.0 | 82.2 | 1.50× | yes |
| 8, 16 | 1 | 8192 | 0 | 236.0 | 117.4 | 2.01× | yes |
| 8, 16 | 1 | 8192 | 4096 | 237.0 | 117.9 | 2.01× | yes |
| 8, 16 | 1 | 16384 | 0 | 462.3 | 175.3 | 2.64× | yes |
| 8, 16 | 1 | 16384 | 4096 | 462.9 | 176.4 | 2.62× | yes |
| 8, 16 | 2 | 2048 | 0 | 65.6 | 70.0 | **0.94×** | no |
| 8, 16 | 2 | 2048 | 4096 | 66.7 | 70.9 | **0.94×** | no |
| 8, 16 | 2 | 4096 | 0 | 122.7 | 104.0 | 1.18× | yes |
| 8, 16 | 2 | 4096 | 4096 | 123.5 | 104.5 | 1.18× | yes |
| 8, 16 | 2 | 8192 | 0 | 235.7 | 168.0 | 1.40× | yes |
| 8, 16 | 2 | 8192 | 4096 | 236.7 | 169.5 | 1.40× | yes |
| 8, 16 | 2 | 16384 | 0 | 462.1 | 312.2 | 1.48× | yes |
| 8, 16 | 2 | 16384 | 4096 | 463.7 | 314.9 | 1.47× | yes |
| 8, 16 | 4 | 2048 | 0 | 66.3 | 97.5 | **0.68×** | no |
| 8, 16 | 4 | 2048 | 4096 | 67.5 | 98.2 | **0.69×** | no |
| 8, 16 | 4 | 4096 | 0 | 123.3 | 162.2 | **0.76×** | no |
| 8, 16 | 4 | 4096 | 4096 | 124.6 | 163.1 | **0.76×** | no |
| 8, 16 | 4 | 8192 | 0 | 236.9 | 293.0 | **0.81×** | no |
| 8, 16 | 4 | 8192 | 4096 | 238.1 | 294.3 | **0.81×** | no |
| 8, 16 | 4 | 16384 | 0 | 464.4 | 553.9 | **0.84×** | no |
| 8, 16 | 4 | 16384 | 4096 | 465.5 | 554.9 | **0.84×** | no |
| 16, 32 | 1 | 2048 | 0 | 66.8 | 70.2 | **0.95×** | no |
| 16, 32 | 1 | 2048 | 4096 | 67.5 | 70.7 | **0.95×** | no |
| 16, 32 | 1 | 4096 | 0 | 124.5 | 104.3 | 1.19× | yes |
| 16, 32 | 1 | 4096 | 4096 | 125.3 | 106.1 | 1.18× | yes |
| 16, 32 | 1 | 8192 | 0 | 238.2 | 170.1 | 1.40× | yes |
| 16, 32 | 1 | 8192 | 4096 | 239.4 | 170.2 | 1.41× | yes |
| 16, 32 | 1 | 16384 | 0 | 466.2 | 302.5 | 1.54× | yes |
| 16, 32 | 1 | 16384 | 4096 | 467.3 | 303.8 | 1.54× | yes |
| 16, 32 | 2 | 2048 | 0 | 67.5 | 98.6 | **0.68×** | no |
| 16, 32 | 2 | 2048 | 4096 | 68.3 | 99.4 | **0.69×** | no |
| 16, 32 | 2 | 4096 | 0 | 124.9 | 164.4 | **0.76×** | no |
| 16, 32 | 2 | 4096 | 4096 | 125.7 | 164.1 | **0.77×** | no |
| 16, 32 | 2 | 8192 | 0 | 239.2 | 295.6 | **0.81×** | no |
| 16, 32 | 2 | 8192 | 4096 | 240.0 | 296.6 | **0.81×** | no |
| 16, 32 | 2 | 16384 | 0 | 467.9 | 558.2 | **0.84×** | no |
| 16, 32 | 2 | 16384 | 4096 | 468.8 | 558.7 | **0.84×** | no |
| 16, 32 | 4 | 2048 | 0 | 69.6 | 164.1 | **0.42×** | no |
| 16, 32 | 4 | 2048 | 4096 | 70.8 | 166.0 | **0.43×** | no |
| 16, 32 | 4 | 4096 | 0 | 128.4 | 295.8 | **0.43×** | no |
| 16, 32 | 4 | 4096 | 4096 | 129.9 | 297.9 | **0.44×** | no |
| 16, 32 | 4 | 8192 | 0 | 245.1 | 558.1 | **0.44×** | no |
| 16, 32 | 4 | 8192 | 4096 | 246.2 | 560.3 | **0.44×** | no |
| 16, 32 | 4 | 16384 | 0 | 477.1 | 1080.4 | **0.44×** | no |
| 16, 32 | 4 | 16384 | 4096 | 479.5 | 1082.3 | **0.44×** | no |

NVIDIA B200 (`sm_100a`), 148 SMs, same setup (bf16, prefix 0):

| Hq=Hk, Hv | N | T (new tokens / seq) | flashinfer (µs) | cake_gdn (µs)
| speedup | `auto` + `aligned_prefixes=True` picks cake_gdn |
|---|---|---|---|---|---|---|
| 2, 4 | 1 | 2048 | 69.4 | 55.1 | 1.26× | yes |
| 2, 4 | 1 | 4096 | 129.2 | 63.3 | 2.04× | yes |
| 2, 4 | 1 | 8192 | 249.0 | 84.8 | 2.94× | yes |
| 2, 4 | 1 | 16384 | 486.3 | 114.3 | 4.26× | yes |
| 2, 4 | 2 | 2048 | 68.7 | 58.7 | 1.17× | yes |
| 2, 4 | 2 | 4096 | 129.2 | 70.8 | 1.83× | yes |
| 2, 4 | 2 | 8192 | 248.0 | 94.2 | 2.63× | yes |
| 2, 4 | 2 | 16384 | 487.0 | 127.8 | 3.81× | yes |
| 2, 4 | 4 | 2048 | 69.2 | 66.0 | 1.05× | no |
| 2, 4 | 4 | 4096 | 129.3 | 85.6 | 1.51× | yes |
| 2, 4 | 4 | 8192 | 249.1 | 125.3 | 1.99× | yes |
| 2, 4 | 4 | 16384 | 486.5 | 163.5 | 2.98× | yes |
| 4, 8 | 1 | 2048 | 69.4 | 58.2 | 1.19× | yes |
| 4, 8 | 1 | 4096 | 129.7 | 69.3 | 1.87× | yes |
| 4, 8 | 1 | 8192 | 249.7 | 93.4 | 2.67× | yes |
| 4, 8 | 1 | 16384 | 491.0 | 128.8 | 3.81× | yes |
| 4, 8 | 2 | 2048 | 69.5 | 66.1 | 1.05× | no |
| 4, 8 | 2 | 4096 | 129.8 | 85.2 | 1.52× | yes |
| 4, 8 | 2 | 8192 | 250.3 | 125.9 | 1.99× | yes |
| 4, 8 | 2 | 16384 | 490.3 | 196.5 | 2.50× | yes |
| 4, 8 | 4 | 2048 | 70.7 | 74.1 | **0.95×** | no |
| 4, 8 | 4 | 4096 | 131.0 | 111.6 | 1.17× | no |
| 4, 8 | 4 | 8192 | 251.2 | 182.0 | 1.38× | yes |
| 4, 8 | 4 | 16384 | 490.0 | 228.2 | 2.15× | yes |
| 8, 16 | 1 | 2048 | 70.2 | 66.9 | 1.05× | no |
| 8, 16 | 1 | 4096 | 131.1 | 85.3 | 1.54× | yes |
| 8, 16 | 1 | 8192 | 252.0 | 125.6 | 2.01× | yes |
| 8, 16 | 1 | 16384 | 492.7 | 196.8 | 2.50× | yes |
| 8, 16 | 2 | 2048 | 70.8 | 73.6 | **0.96×** | no |
| 8, 16 | 2 | 4096 | 131.7 | 111.4 | 1.18× | no |
| 8, 16 | 2 | 8192 | 252.0 | 182.8 | 1.38× | yes |
| 8, 16 | 2 | 16384 | 493.6 | 321.8 | 1.53× | yes |
| 8, 16 | 4 | 2048 | 72.9 | 129.3 | **0.56×** | no |
| 8, 16 | 4 | 4096 | 134.1 | 199.7 | **0.67×** | no |
| 8, 16 | 4 | 8192 | 255.2 | 365.1 | **0.70×** | no |
| 8, 16 | 4 | 16384 | 496.1 | 696.8 | **0.71×** | no |
| 16, 32 | 1 | 2048 | 71.6 | 74.0 | **0.97×** | no |
| 16, 32 | 1 | 4096 | 133.2 | 112.6 | 1.18× | no |
| 16, 32 | 1 | 8192 | 254.8 | 183.3 | 1.39× | yes |
| 16, 32 | 1 | 16384 | 498.4 | 323.9 | 1.54× | yes |
| 16, 32 | 2 | 2048 | 73.5 | 105.6 | **0.70×** | no |
| 16, 32 | 2 | 4096 | 135.2 | 177.1 | **0.76×** | no |
| 16, 32 | 2 | 8192 | 257.3 | 317.2 | **0.81×** | no |
| 16, 32 | 2 | 16384 | 500.2 | 595.3 | **0.84×** | no |
| 16, 32 | 4 | 2048 | 80.5 | 178.5 | **0.45×** | no |
| 16, 32 | 4 | 4096 | 147.2 | 318.5 | **0.46×** | no |
| 16, 32 | 4 | 8192 | 276.3 | 595.7 | **0.46×** | no |
| 16, 32 | 4 | 16384 | 532.3 | 1150.4 | **0.46×** | no |

NVIDIA VR200 (`sm_107a`), 212 SMs, same setup (bf16, prefix 0):

| Hq=Hk, Hv | N | T (new tokens / seq) | flashinfer (µs) | cake_gdn (µs)
| speedup | `auto` + `aligned_prefixes=True` picks cake_gdn |
|---|---|---|---|---|---|---|
| 2, 4 | 1 | 2048 | 53.1 | 44.2 | 1.20× | yes |
| 2, 4 | 1 | 4096 | 97.7 | 51.2 | 1.91× | yes |
| 2, 4 | 1 | 8192 | 187.8 | 66.3 | 2.83× | yes |
| 2, 4 | 1 | 16384 | 367.9 | 89.4 | 4.11× | yes |
| 2, 4 | 2 | 2048 | 52.8 | 48.3 | 1.09× | yes |
| 2, 4 | 2 | 4096 | 97.4 | 56.7 | 1.72× | yes |
| 2, 4 | 2 | 8192 | 187.2 | 73.8 | 2.54× | yes |
| 2, 4 | 2 | 16384 | 366.9 | 97.4 | 3.77× | yes |
| 2, 4 | 4 | 2048 | 54.1 | 54.0 | 1.00× | no |
| 2, 4 | 4 | 4096 | 101.6 | 66.5 | 1.53× | yes |
| 2, 4 | 4 | 8192 | 196.2 | 89.7 | 2.19× | yes |
| 2, 4 | 4 | 16384 | 367.3 | 127.2 | 2.89× | yes |
| 4, 8 | 1 | 2048 | 52.9 | 46.2 | 1.15× | yes |
| 4, 8 | 1 | 4096 | 97.5 | 54.8 | 1.78× | yes |
| 4, 8 | 1 | 8192 | 186.8 | 73.3 | 2.55× | yes |
| 4, 8 | 1 | 16384 | 367.0 | 97.3 | 3.77× | yes |
| 4, 8 | 2 | 2048 | 53.9 | 53.8 | 1.00× | no |
| 4, 8 | 2 | 4096 | 100.5 | 66.1 | 1.52× | yes |
| 4, 8 | 2 | 8192 | 193.0 | 89.9 | 2.15× | yes |
| 4, 8 | 2 | 16384 | 378.8 | 127.4 | 2.97× | yes |
| 4, 8 | 4 | 2048 | 54.1 | 63.0 | **0.86×** | no |
| 4, 8 | 4 | 4096 | 101.0 | 86.9 | 1.16× | yes |
| 4, 8 | 4 | 8192 | 193.8 | 126.1 | 1.54× | yes |
| 4, 8 | 4 | 16384 | 367.0 | 156.4 | 2.35× | yes |
| 8, 16 | 1 | 2048 | 54.2 | 54.1 | 1.00× | no |
| 8, 16 | 1 | 4096 | 100.9 | 65.7 | 1.54× | yes |
| 8, 16 | 1 | 8192 | 194.2 | 89.8 | 2.16× | yes |
| 8, 16 | 1 | 16384 | 381.3 | 127.3 | 2.99× | yes |
| 8, 16 | 2 | 2048 | 54.8 | 62.9 | **0.87×** | no |
| 8, 16 | 2 | 4096 | 101.3 | 87.1 | 1.16× | yes |
| 8, 16 | 2 | 8192 | 194.9 | 127.0 | 1.53× | yes |
| 8, 16 | 2 | 16384 | 382.5 | 189.4 | 2.02× | yes |
| 8, 16 | 4 | 2048 | 54.3 | 87.9 | **0.62×** | no |
| 8, 16 | 4 | 4096 | 100.2 | 126.5 | **0.79×** | no |
| 8, 16 | 4 | 8192 | 192.8 | 202.0 | **0.95×** | no |
| 8, 16 | 4 | 16384 | 377.5 | 352.7 | 1.07× | no |
| 16, 32 | 1 | 2048 | 55.0 | 63.1 | **0.87×** | no |
| 16, 32 | 1 | 4096 | 102.0 | 87.4 | 1.17× | yes |
| 16, 32 | 1 | 8192 | 196.1 | 128.1 | 1.53× | yes |
| 16, 32 | 1 | 16384 | 384.2 | 191.6 | 2.01× | yes |
| 16, 32 | 2 | 2048 | 55.1 | 88.5 | **0.62×** | no |
| 16, 32 | 2 | 4096 | 101.3 | 128.4 | **0.79×** | no |
| 16, 32 | 2 | 8192 | 194.8 | 204.9 | **0.95×** | no |
| 16, 32 | 2 | 16384 | 380.2 | 336.6 | 1.13× | no |
| 16, 32 | 4 | 2048 | 67.8 | 137.8 | **0.49×** | no |
| 16, 32 | 4 | 4096 | 126.6 | 231.9 | **0.55×** | no |
| 16, 32 | 4 | 8192 | 244.5 | 420.1 | **0.58×** | no |
| 16, 32 | 4 | 16384 | 480.8 | 795.9 | **0.60×** | no |


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added a paged GDN prefill backend option, with FlashInfer remaining
the default.
* Added automatic backend selection based on device, data type, and
workload characteristics, with fallback to FlashInfer when the Cake
backend is unsupported.
* Added support for paged state updates and checkpoint handling,
including optional validation of slot and prefix inputs.
* **Documentation**
* Documented backend options, input constraints, alignment behavior, and
automatic selection.
  * Expanded the environment-variable reference for slot validation.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [c562253](https://github.com/flashinfer-ai/flashinfer/commit/c562253865bd551ba3110bae732a6676cf4e7c4f)

- **作者**: eigen
- **时间**: 2026-11-20T04:00:09Z
- **提交信息**: perf(cake_batch_deepgemm_fp8): full serving grid on 212-SM devices from expected_m 36 (#9687)

`cake_batch_deepgemm_fp8` is the masked FP8 NT groupwise grouped GEMM
with UE8M0 packed scales behind `backend="cake"`. Its packed-scale
serving route launches the whole serving program on `sm_count -
cta_reserve` CTAs. The reserve was tuned only for 148-SM devices, so
every other SM count used 24. This PR sets the reserve to 0 (full grid)
on 212-SM devices (dual-die SM107a) from expected_m 36, for both K
values. expected_m <= 32 and every other SM count are unchanged. Homed
weights (`localize_weights`) use the locality-domain twin, which already
runs a full grid and is unchanged. The `localize_weights` docstring now
says that for B=64 weights of (4096, 7168), plain weights take 0.95x the
time of homed weights at expected_m 64 and 512 and 0.97x at 4096, while
homed weights stay faster at 36 and below.

Against the previous Cake (FlashInfer main 03288fe1e, public
`backend="cake"`), plain-weight rows at expected_m >= 36 run
1.030-1.118x faster (table medians). expected_m <= 32 and all homed rows
are unchanged at 0.999-1.002x. Cake outputs are bit-identical between
main and this PR. Against the strongest non-Cake baseline
(`backend="deepgemm"` on plain B), DeepGEMM is still faster at
expected_m 512 and 4096, where the speedup vs DeepGEMM is 0.38-0.49.

The family's other Cake variants are the fp32-scale masked path and the
locality-domain serving twins for homed weights. The family ships on
sm_100a, sm_103a and sm_107a, and this change applies only to 212-SM
sm_107a devices.

NVIDIA VR200 (Rubin, sm_107a, 212 SMs), driver 620.70.06, CUDA/NVRTC
13.5.37, torch 2.14.1; median over 4 boards (3 even and 1 uneven die
split) of per-board medians of 8 alternating rounds, CUDA graph replay,
cold L2; ratio = baseline / this PR, median with min-max over boards in
parentheses.

**Plain weights**

| G | N | K | expected_m | M | B homed | previous Cake us | this PR us |
DeepGEMM us | speedup vs previous Cake | speedup vs DeepGEMM |
|---|---|---|---|---|---|---|---|---|---|---|
| 32 | 4096 | 7168 | 1 | 512 | no | 12.08 | 12.06 | 25.53 | 1.002
(1.000-1.003) | 2.116 (2.088-2.119) |
| 32 | 4096 | 7168 | 2 | 512 | no | 71.90 | 71.92 | 80.92 | 1.000
(0.997-1.002) | 1.124 (1.118-1.168) |
| 32 | 4096 | 7168 | 3 | 512 | no | 71.92 | 71.98 | 80.90 | 1.000
(0.998-1.000) | 1.124 (1.118-1.167) |
| 32 | 4096 | 7168 | 7 | 512 | no | 71.37 | 71.42 | 80.91 | 1.000
(0.999-1.000) | 1.133 (1.128-1.163) |
| 32 | 4096 | 7168 | 8 | 512 | no | 71.40 | 71.38 | 80.90 | 1.000
(0.999-1.001) | 1.133 (1.128-1.164) |
| 32 | 4096 | 7168 | 16 | 512 | no | 71.32 | 71.25 | 80.91 | 1.000
(1.000-1.001) | 1.132 (1.131-1.139) |
| 32 | 4096 | 7168 | 32 | 512 | no | 76.56 | 76.58 | 80.90 | 1.000
(1.000-1.000) | 1.057 (1.055-1.058) |
| 32 | 4096 | 7168 | 36 | 512 | no | 79.51 | 76.98 | 80.90 | 1.030
(1.029-1.037) | 1.051 (1.049-1.053) |
| 32 | 4096 | 7168 | 64 | 512 | no | 96.82 | 88.39 | 96.78 | 1.095
(1.090-1.096) | 1.098 (1.092-1.110) |
| 32 | 4096 | 7168 | 512 | 512 | no | 541.65 | 484.86 | 207.81 | 1.116
(1.109-1.118) | 0.429 (0.423-0.431) |
| 32 | 4096 | 7168 | 4096 | 4096 | no | 4249.41 | 3833.36 | 1740.86 |
1.109 (1.107-1.109) | 0.454 (0.442-0.460) |
| 32 | 7168 | 2048 | 1 | 512 | no | 8.09 | 8.10 | 14.61 | 1.000
(1.000-1.002) | 1.814 (1.765-1.829) |
| 32 | 7168 | 2048 | 2 | 512 | no | 38.25 | 38.26 | 43.93 | 1.000
(0.998-1.003) | 1.149 (1.132-1.157) |
| 32 | 7168 | 2048 | 3 | 512 | no | 38.10 | 38.08 | 44.05 | 1.000
(1.000-1.000) | 1.158 (1.139-1.166) |
| 32 | 7168 | 2048 | 7 | 512 | no | 38.08 | 38.07 | 44.00 | 1.000
(0.998-1.001) | 1.157 (1.137-1.165) |
| 32 | 7168 | 2048 | 8 | 512 | no | 38.08 | 38.06 | 43.94 | 1.000
(0.999-1.002) | 1.155 (1.140-1.164) |
| 32 | 7168 | 2048 | 16 | 512 | no | 38.42 | 38.45 | 43.99 | 0.999
(0.998-1.000) | 1.135 (1.108-1.154) |
| 32 | 7168 | 2048 | 32 | 512 | no | 39.08 | 39.08 | 43.88 | 1.000
(1.000-1.000) | 1.115 (1.102-1.136) |
| 32 | 7168 | 2048 | 36 | 512 | no | 42.60 | 41.03 | 43.97 | 1.038
(1.036-1.050) | 1.064 (1.054-1.078) |
| 32 | 7168 | 2048 | 64 | 512 | no | 50.59 | 47.48 | 48.01 | 1.066
(1.059-1.066) | 1.010 (0.993-1.015) |
| 32 | 7168 | 2048 | 512 | 512 | no | 287.69 | 265.51 | 108.61 | 1.084
(1.079-1.090) | 0.411 (0.402-0.415) |
| 32 | 7168 | 2048 | 4096 | 4096 | no | 2277.73 | 2080.04 | 793.16 |
1.098 (1.090-1.102) | 0.382 (0.375-0.401) |
| 64 | 4096 | 7168 | 1 | 512 | no | 18.64 | 18.65 | 31.16 | 1.000
(0.998-1.001) | 1.666 (1.644-1.677) |
| 64 | 4096 | 7168 | 2 | 512 | no | 143.81 | 143.87 | 160.55 | 1.000
(1.000-1.001) | 1.115 (1.109-1.161) |
| 64 | 4096 | 7168 | 3 | 512 | no | 143.78 | 143.87 | 160.52 | 1.000
(0.999-1.001) | 1.116 (1.108-1.163) |
| 64 | 4096 | 7168 | 7 | 512 | no | 140.54 | 140.45 | 160.47 | 1.001
(0.999-1.001) | 1.140 (1.134-1.174) |
| 64 | 4096 | 7168 | 8 | 512 | no | 140.52 | 140.53 | 160.49 | 1.000
(1.000-1.001) | 1.140 (1.134-1.174) |
| 64 | 4096 | 7168 | 16 | 512 | no | 141.43 | 141.33 | 160.48 | 1.000
(1.000-1.001) | 1.133 (1.120-1.137) |
| 64 | 4096 | 7168 | 32 | 512 | no | 143.82 | 143.80 | 160.50 | 1.000
(1.000-1.000) | 1.114 (1.101-1.122) |
| 64 | 4096 | 7168 | 36 | 512 | no | 152.83 | 147.72 | 159.48 | 1.034
(1.033-1.035) | 1.077 (1.071-1.084) |
| 64 | 4096 | 7168 | 64 | 512 | no | 188.70 | 176.53 | 158.80 | 1.069
(1.068-1.070) | 0.900 (0.897-0.908) |
| 64 | 4096 | 7168 | 512 | 512 | no | 1075.61 | 962.00 | 408.10 | 1.118
(1.101-1.118) | 0.424 (0.415-0.424) |
| 64 | 4096 | 7168 | 4096 | 4096 | no | 8522.21 | 7684.36 | 3719.52 |
1.108 (1.099-1.110) | 0.485 (0.459-0.488) |
| 64 | 7168 | 2048 | 1 | 512 | no | 12.80 | 12.82 | 21.93 | 0.999
(0.997-1.001) | 1.711 (1.666-1.757) |
| 64 | 7168 | 2048 | 2 | 512 | no | 74.48 | 74.50 | 82.78 | 1.000
(0.999-1.000) | 1.111 (1.107-1.172) |
| 64 | 7168 | 2048 | 3 | 512 | no | 74.10 | 74.20 | 82.74 | 1.000
(0.995-1.000) | 1.115 (1.106-1.155) |
| 64 | 7168 | 2048 | 7 | 512 | no | 74.15 | 74.11 | 82.77 | 1.000
(0.995-1.001) | 1.117 (1.108-1.155) |
| 64 | 7168 | 2048 | 8 | 512 | no | 74.11 | 74.12 | 82.90 | 0.999
(0.993-1.001) | 1.118 (1.108-1.164) |
| 64 | 7168 | 2048 | 16 | 512 | no | 72.88 | 72.82 | 82.91 | 1.000
(1.000-1.002) | 1.136 (1.123-1.146) |
| 64 | 7168 | 2048 | 32 | 512 | no | 74.10 | 74.07 | 82.90 | 1.000
(0.998-1.001) | 1.115 (1.098-1.128) |
| 64 | 7168 | 2048 | 36 | 512 | no | 80.70 | 78.13 | 82.66 | 1.034
(1.031-1.038) | 1.057 (1.055-1.059) |
| 64 | 7168 | 2048 | 64 | 512 | no | 97.95 | 93.07 | 82.27 | 1.053
(1.044-1.058) | 0.885 (0.881-0.895) |
| 64 | 7168 | 2048 | 512 | 512 | no | 577.52 | 529.72 | 203.15 | 1.091
(1.083-1.097) | 0.385 (0.379-0.386) |
| 64 | 7168 | 2048 | 4096 | 4096 | no | 4646.09 | 4225.14 | 1807.35 |
1.100 (1.094-1.102) | 0.426 (0.423-0.435) |

**Homed weights (`localize_weights`)**

| G | N | K | expected_m | M | B homed | previous Cake us | this PR us |
DeepGEMM us | speedup vs previous Cake | speedup vs DeepGEMM |
|---|---|---|---|---|---|---|---|---|---|---|
| 64 | 4096 | 7168 | 1 | 512 | yes | 16.96 | 17.01 | 31.16 | 0.999
(0.991-1.001) | 1.832 (1.824-1.841) |
| 64 | 4096 | 7168 | 2 | 512 | yes | 106.25 | 106.25 | 160.55 | 1.000
(1.000-1.000) | 1.515 (1.505-1.528) |
| 64 | 4096 | 7168 | 3 | 512 | yes | 106.27 | 106.31 | 160.52 | 1.000
(0.999-1.000) | 1.513 (1.503-1.529) |
| 64 | 4096 | 7168 | 7 | 512 | yes | 106.29 | 106.30 | 160.47 | 1.000
(1.000-1.000) | 1.512 (1.504-1.528) |
| 64 | 4096 | 7168 | 8 | 512 | yes | 106.28 | 106.28 | 160.49 | 1.000
(0.999-1.001) | 1.514 (1.503-1.528) |
| 64 | 4096 | 7168 | 16 | 512 | yes | 115.61 | 115.53 | 160.48 | 1.000
(0.995-1.001) | 1.391 (1.372-1.417) |
| 64 | 4096 | 7168 | 32 | 512 | yes | 128.32 | 128.23 | 160.50 | 1.000
(1.000-1.001) | 1.250 (1.242-1.300) |
| 64 | 4096 | 7168 | 36 | 512 | yes | 141.53 | 141.55 | 159.48 | 1.000
(0.999-1.000) | 1.122 (1.106-1.162) |
| 64 | 4096 | 7168 | 64 | 512 | yes | 184.57 | 184.33 | 158.80 | 1.000
(1.000-1.003) | 0.855 (0.852-0.893) |
| 64 | 4096 | 7168 | 512 | 512 | yes | 1011.33 | 1011.18 | 408.10 |
1.000 (1.000-1.000) | 0.403 (0.402-0.404) |
| 64 | 4096 | 7168 | 4096 | 4096 | yes | 7922.17 | 7922.54 | 3719.52 |
1.000 (1.000-1.000) | 0.470 (0.450-0.474) |


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* Serving workloads on 212-SM devices now use the full 212-CTA grid when
the expected batch size is 36 or greater, including for K=7168.
* Grid selection for smaller batch sizes remains unchanged, as do the
existing reserve settings for other supported device configurations.
* **Documentation**
* Added measured timing comparisons for weight placement on 212-SM
devices.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [82fab00](https://github.com/flashinfer-ai/flashinfer/commit/82fab003f58aed31d745e4ae5440e78f8ebd5574)

- **作者**: Anerudhan Gopal
- **时间**: 2026-11-20T03:44:51Z
- **提交信息**: build: require cuDNN Frontend 1.33.0 or later (#9672)

Raise the minimum cuDNN Frontend version to 1.33.0 in the Python package
and container build. Update the backend notes to match. [Upstream
release](https://github.com/NVIDIA/cudnn-frontend/releases/tag/v1.33.0)

Verified that the package requirement accepts 1.33.0 and excludes
1.32.3. The container script passed `bash -n`, and all applicable
pre-commit hooks passed.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Chores**
* Updated the minimum supported cuDNN Frontend version for project
requirements and container builds.
* **Documentation**
* Updated backend development notes to reflect the current minimum
version.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: Anerudhan Gopal <agopal@nvidia.com>

### [1c87bfa](https://github.com/flashinfer-ai/flashinfer/commit/1c87bfaf0530868be02be6605175635f5dd49b46)

- **作者**: Yang Xu
- **时间**: 2026-11-20T03:34:13Z
- **提交信息**: feat(attention): expand Blackwell paged auto for FP16 and full prefills (#9463)

<!-- .github/pull_request_template.md -->

## 📌 Description

Let matching FP16 Q/KV/output use the same qualified Blackwell
paged-auto regions as BF16, with stable cuDNN Frontend 1.33.0+, backend
9.24+, and the existing runtime/native capability guards. Previously
those FP16 requests fell back to FA2. This also includes the BF16
prerequisite changes from #9390 (SM103 D256 prefixes) and #9401
(D128/D256 full prefills), including D256 GQA groups 2/4/8/16.

The change is limited to plan-time admission. It preserves actual CPU
length/work checks, matching dtypes, layout/page/head-dimension bounds,
and the common backend/FROST graph API. It does not change the execution
path, kernels, engine ranking, or H100 admission. D64 and the
unqualified SM103 D128 short-prefix region remain on the native route.
Source comparison against current main confirms that existing wrapper
classes and cuDNN execution functions are unchanged.

FE 1.33.0 is now an official release. Its Blackwell paged full-square
and GQA-prefill placement predicates accept both BF16 and FP16; FE
1.32.3 restricted those predicates to BF16. This is why the FP16
admission keeps a stable-FE 1.33 floor even though the kernel family
supports both dtypes. The new-head validation below uses the unmodified
public wheel, rather than a development package with a 1.33 version
string.

Historical component evidence (each target: 448 FP16 inputs + 112 BF16
controls; B200/B300, 148 SMs, backend 9.24.0.43; FE source
`d0db79006acc809db44568e585a2084f5b9c5394`, FI baseline
`3ac41347fa222c604b3c73d1f28ad0d056f6f136`, candidate
`d6ff4146eb0d345abcd3a9a29ae299aea3bedb20`):

| GPU | Correctness | Newly admitted FP16 cases | New-route graph
speedup | New-route completed-eager speedup |
|---|---:|---:|---:|---:|
| B200 | 560/560 | 389 | 3.394x | 3.322x |
| B300 | 560/560 | 262 | 3.713x | 3.576x |

These are geometric component summaries, not traffic coverage,
current-wheel performance, or serving TTFT. Startup/JIT is excluded. No
new-route case lost more than 5% in both orders.

The original unchanged-route controls measured +0.042634% / +0.018407%
graph time and failed the study's strict `candidate/baseline <= 1`
threshold. Those measurements and original FAIL/HOLD verdicts are
retained; they are not relabeled as passes. The B300 within-instance
interval excludes one, so this is not a claim that all variation was
statistical noise. The release assessment separates those
unchanged-execution controls from the FP16 routing change: the change
affects plan-time admission only, while their warm execution and
selected plans were unchanged. It does not establish a causal FP16
regression. No favorable subset, retuned holdout, or repeated
performance run is substituted for the original study.

The landed `benchmarks/bench_cudnn_wrapper_host.py` records versions,
actual routes, selected plans, CPU enqueue, completed eager, and
poisoned graph replay with interleaved sampling. Example on eligible
SM100:

```bash
python benchmarks/bench_cudnn_wrapper_host.py --kind paged --dtype float16 --head-dim 128 --page-size 16 --layout HND --batch 1 --q 128 --kv 8192 --qo-heads 32 --kv-heads 4 --backends fa2 auto --expected-backend-version 92400 --expect-auto-backend cudnn --output prefix-fp16.json
python benchmarks/bench_cudnn_wrapper_host.py --kind paged --dtype float16 --head-dim 256 --page-size 64 --layout HND --batch 4 --q 1024 --kv 1024 --qo-heads 32 --kv-heads 4 --backends fa2 auto --expected-backend-version 92400 --expect-auto-backend cudnn --output full-fp16.json
```

## 🔍 Related Issues

Includes #9390 and #9401; their branches can be closed as superseded
after this union lands. Follows merged backend-9.24 enablement #9351.
The benchmark companion already landed through #9469/#9473 and is absent
from this diff.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

Changed-file hooks passed as required by `AGENTS.md`; whole-repository
hooks were not run.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.). Current-head local
results are listed below; actual targeted CI is still running.
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/cpu/attention/
tests/attention/test_cudnn_paged_full_prefill_auto.py
tests/attention/test_cudnn_paged_gqa_auto.py
tests/attention/test_cudnn_wrapper_regressions.py`

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

The measured unchanged-route graph-time deltas (+0.042634% on B200 and
+0.018407% on B300) are accepted for this release decision. The original
study verdicts stand. Normal review approval and successful current-head
CI are still required.

AI-assisted author closeout. Please review the complete union of
admission changes, especially dtype parity, full-prefill equality for
every request, capability floors, and retained captures after a native
fallback.

Current source: `dd9524fc66eb0681947da2eeca1ac5196508fff4`, including
main `6fd1320260a8224b8a0d69c8cca8235aed65b3b2`.

- 321 focused CPU admission/version/metadata tests: pass, zero skipped.
- 72 local SM100 GPU cases: pass, zero skipped. This is the complete
48-case full-prefill matrix, 8-case D256 GQA prefix matrix, and 16
changed D128 runtime-scale/device-length cases, covering BF16/FP16,
O/LSE, page sizes 16/64, retained CUDA Graph replay with changed
inputs/metadata, fallback after capture, and no added metadata readback.
- GPU setup: 68-SM SM100, unmodified official FE 1.33.0 wheel, actual
loaded backend 9.24.0.43, Torch 2.14.1+cu130, DSL 4.8.0;
`CUDNN_FRONTEND_ENABLE_FROST_ENGINES` unset. This run establishes
functionality, not B200/B300 performance.
- Changed-file pre-commit checks: pass. No kernel, wrapper execution, or
benchmark implementation was changed in this closeout.
- Exact-head H100 CI passed in [run
44660072399](https://github.com/flashinfer-ai/flashinfer/actions/runs/44660072399).
Its remaining CPU/AOT/lint jobs were cancelled by the ready-for-review
lifecycle event; a CPU-scoped replacement is requested below, without
repeating the successful H100 job.

The GPU logs retain nanobind shutdown reference-count diagnostics; both
pytest processes exited successfully. The historical study also retained
such shutdown diagnostics. They are not sanitizer or leak-free
qualification.

The old H100-only CI skipped all Blackwell-specific tests. That skip is
not GPU qualification; the explicit SM100 execution above supplies that
coverage. Public CI for this exact head must still finish and normal
approval is required before merge.



<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

- **New Features**
- Expanded automatic cuDNN selection for paged attention to support FP16
as well as BF16 on compatible systems.
- Added support for full-prefill workloads on Blackwell SM100 and SM103
GPUs, subject to supported layouts, sequence lengths, batch shapes, and
workload size.
- Existing FP16 routing remains available on earlier cuDNN versions;
unsupported configurations continue to use other eligible backends.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [879d2d8](https://github.com/flashinfer-ai/flashinfer/commit/879d2d841d5d02b75e4fdcbeca4158069c957ebf)

- **作者**: Artem Perevedentsev
- **时间**: 2026-11-20T03:09:19Z
- **提交信息**: fix(gemm): reject K not a multiple of 8 for the TGV and TinyGEMM bf16 backends (#9610)

For gemm BF16 kernels TGV and tinygemm K must be K % 8 == 0.
In case if TGV it returns wrong results if K is not multiple of 8.
If case of tinygemm if K is not multiple of 8 I get runtime error from
cuTensorMapEncodeTiled:
```
RuntimeError: Check failed: (res == CUDA_SUCCESS) is false: cuTensorMapEncodeTiled failed for weight_map
```

This PR rejects these kernels from autotuner in case K is not multiple
of 8.

Related PR https://github.com/flashinfer-ai/flashinfer/pull/8226

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* BF16 matrix and batched matrix multiplication using TGV or TinyGEMM
now reports an error when the reduction dimension is not divisible by 8.
* Automatic backend selection skips TGV and TinyGEMM for unsupported
dimensions, allowing it to choose a compatible backend instead.
* TGV GEMM now reports an error when the reduction dimension is not
divisible by 8 for supported data types.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Artem Perevedentsev <aperevedents@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [6fd1320](https://github.com/flashinfer-ai/flashinfer/commit/6fd1320260a8224b8a0d69c8cca8235aed65b3b2)

- **作者**: Ji Sung Han
- **时间**: 2026-11-20T01:14:11Z
- **提交信息**: Revert "fix(autotuner): serve lookups above the largest tuned bucket from it (#7626)" (#9534)

<!-- .github/pull_request_template.md -->

## 📌 Description

Reverts #7626 on `main`, as #9331 did on `release-v0.7.4` and
`release-v0.7.5`.

**Background.** vLLM tunes up to `max_num_batched_tokens`. With 21504,
which is off
the op's power-of-two grid, lookups for M in 16385..21504 asked for
bucket 32768,
which was never tuned, so those calls ran the default tactic. #7626
worked around
this in FlashInfer: any lookup above the largest tuned bucket reused
that bucket's
tactic, for every op and caller. That also changed callers that tune
small and run
large. SGLang tunes the MoE up to 256 tokens and prefills with 8k-16k
tokens, so it
ran the 256-token tile and became slower than with v0.7.3 (#9331).

Separately, review of the vLLM-side workaround (vllm-project/vllm#63159)
asked for
the fix in FlashInfer. That became #8545, now in main: the entry tuned
at 21504 is
stored under 32768, the key inference looks up.

**Purpose.** With #8545 in main, the reuse is no longer needed. This PR
removes it,
so lookups above the tuned range use the default heuristic again as in
v0.7.3, and
leaves #8545 as the fix for the vLLM case. Main then matches the release
branches,
and the next release branch will not bring #7626 back.

**Changes.** The same removal as #9331. One #8727 test case that
expected the
reuse now expects a miss, the same change as #9470 on `release-v0.7.5`.

## 🔍 Related Issues

- #7626 (reverted), #9331 and #9470 (release branches), #8545 (the fix
that
  replaces it), vllm-project/vllm#63159 (closed in favor of #8545).

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

Ran `pre-commit run --files` on the changed files: all hooks passed.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed: #7626's tests are
removed and
      one #8727 case now expects a miss.
- [x] All tests are passing (`unittest`, etc.). On SM107,
`tests/autotuner/
tests/cpu/autotuner/ tests/gemm/test_mm_bf16.py tests/cpu/gemm/`: 726
passed
on this branch, 734 on main (cd2d2c8e2), no failures. The difference is
the 8
      removed #7626 tests.
- [x] End to end on SM107 (`CuteDslFusedMoE` and `bf16_gemm`, tuned with
vLLM's
bucket list for `max_num_batched_tokens=21504`, then run without an
autotune
context): all 10 serving sizes up to 21504 hit a tuned entry directly,
none
falls back to `-1`. MoE output vs. float reference: PASS (relative L2
0.2032).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/autotuner/
tests/cpu/gemm/test_bf16_fp4_autotune_cache.py
tests/gemm/test_mm_bf16.py tests/gemm/test_mm_bf16_fp4.py`

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

- Tests that relied on the reuse: I ran 84 autotuner-related test files
on main
with a plugin that repeats each cache hit without the reuse. Apart from
#7626's
  own tests, only the #8727 case above changes outcome.
- AI assistance (Claude, via Claude Code) was used to write parts of
this change. I reviewed every change and ran all of the validation above
on SM107.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Behavior Changes**
* Requests above the largest tuned input profile no longer retry with
that profile’s settings; they follow the cache-miss fallback.
* Some runtime dimensions no longer reuse nearby tuned profiles. For
example, using a profile tuned for `m=2` at runtime with `m=4` now
results in a cache miss.
* **Documentation**
* Updated autotuning guidance to remove the previous description of
out-of-range lookup retries and related fallback behavior.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: Ji sung Han <jisungh@nvidia.com>

### [67b5329](https://github.com/flashinfer-ai/flashinfer/commit/67b5329067a258a7e0da3e211da7c31ff6c3b672)

- **作者**: Adrian
- **时间**: 2026-11-20T00:49:45Z
- **提交信息**: test: skip exhaustive search in SM107 memory accounting test (#9739)

<!-- .github/pull_request_template.md -->

## 📌 Description

The SM107 shared-memory accounting test can exceed its 180-second
timeout because the file-wide fixture enables exhaustive interleaving
search. Disable that search only for this allocation-size test while
retaining structural and capacity checks.

The targeted test previously took about 50 seconds locally and took 0.23
seconds after the change; GPU hardware is not used.

## 🔍 Related Issues

Found while investigating recent internal unit-test CI failures; no
tracking issue.

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

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

Local CPU validation with CuTe-DSL 4.8.0: the complete
schedule-validation test file passed (201 tests). Changed-file
pre-commit hooks passed.

```bash
python -m pytest -q tests/cpu/prims_ts/test_batched_gemm_schedule_validation.py
```

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust):
`tests/cpu/prims_ts/test_batched_gemm_schedule_validation.py`

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

Implemented and reviewed with assistance from OpenAI Codex. Local
validation is complete; GitHub CI has not been requested.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Tests**
* Updated the SM107 shared-memory capacity test setup; its capacity
assertions and expected outcomes are unchanged.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [9133d44](https://github.com/flashinfer-ai/flashinfer/commit/9133d44d5bba7ddd2e7de3de9ba189457d52555f)

- **作者**: Adrian
- **时间**: 2026-11-20T00:43:02Z
- **提交信息**: fix: let PyTorch select DeepGEMM's C++ standard (#9744)

<!-- .github/pull_request_template.md -->

## 📌 Description

The pinned DeepGEMM setup hard-codes C++17, which fails against newer
PyTorch headers requiring C++20. Patch DeepGEMM's `setup.py` before its
installer runs: remove the explicit standard and register the installed
PyTorch's `BuildExtension`.

PyTorch selects the appropriate standard for its headers. Preserve
DeepGEMM's other build commands and its non-Ninja compilation path.

## 🔍 Related Issues

No tracking issue; fixes an EP dependency-build failure observed during
unit tests.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

Changed-file hooks passed; a full-repository hook run was not performed.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

Built and installed the pinned DeepGEMM wheel, then imported the newly
built extension without GPU access:

| PyTorch | Standard selected by BuildExtension | Result |
| --- | --- | --- |
| 2.10.0+cu130 | C++17 | Wheel build and import passed |
| 2.15.0.dev20260923+cu134 | C++20 | Wheel build and import passed |

Also verified that the `sed` patch is idempotent and produces the same
setup source used for those builds. Bash syntax and changed-file
pre-commit checks passed. GPU numerical tests have not been run.

- [ ] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust):
`tests/moe_ep/test_deep_gemm_mega_kernel_vs_reference.py`

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

Implemented and validated with assistance from OpenAI Codex. This
changes dependency setup only; it does not raise FlashInfer's PyTorch
minimum or change DeepGEMM's runtime CUDA JIT standard.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Chores**
* Updated the DeepGEMM installation process to adjust build settings
before installation.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [88fb283](https://github.com/flashinfer-ai/flashinfer/commit/88fb283ce89eb20eb6a61096b9ae32651f0fd4f6)

- **作者**: Harrison Zhang
- **时间**: 2026-11-20T00:38:41Z
- **提交信息**: fix(prims-ts): fix VC-attention prepass: V gather, k-means initialization, restricted token grouping (#9549)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

Three fixes to the VC-Attention preparation, one commit each.

1. **Pre-pass V gather past the sequence.** `VcKvPass2` read each
permuted V row behind a predicate on the row being inside the sequence,
with the row offset computed in the register that also receives the
first row's permutation entry. Under load the generated code reused that
register for a row past the sequence, so the last tile of a sequence
whose length mod 128 lies in 1..31 read V at a misaligned address and
aborted (31 of 100 HunyuanVideo-1.5 prompts at 111,745-111,811 tokens).
Rows past the sequence now read the last token through its permutation
slot without a predicate; the later steps skip them as before.
compute-sanitizer memcheck at S = 1025, 1041 and 111,745 goes from 409
pass-2 errors to none on B300, with bit-identical tile-means outputs at
six lengths.
2. **k-means generator and cold start.** `vc_token_permutation` drew the
initial centroids from the caller's global CUDA generator, one draw per
batch element and head in turn, so a grouping depended on the elements
before it (1-3 % output change between batch 1 and batch 2 of the same
input) and consumed the caller's random numbers;
`VCAttentionPreprocessor` also warm-started step 0 from the previous
generation's centroids. The preprocessor now owns a generator reseeded
with `VC_KMEANS_SEED` at every cold start (the first call, or a step at
or before the last refresh, so a sampler that begins after step 0 starts
cold too), a cold start draws one set of initial rows shared by every
batch element and head, and only refreshes inside a generation
warm-start.
3. **Grouping restricted to a token range.** Every token of a joint
sequence was grouped, so text and audio keys landed among the video
clusters ahead of the video long tail of the rows that attend to them,
whose probabilities then rounded to zero against the row maximum
(HunyuanVideo-1.5 text rows at 4.7 % relative error, about 0.1 LPIPS
behind the paper). `vc_token_permutation` and
`VCAttentionPreprocessor.prepare` take `grouped_tokens=(start, stop)`,
the contiguous range to group; the other tokens follow it in input order
and the grouping cache is keyed by the range. `None` keeps the whole
sequence grouped.

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

The recipe matrix gains a one-token-tail row (S = 1025), and the
preprocessor schedule test checks the untouched caller generator, the
cold-start determinism, the batch invariance, a generation that begins
after step 0, the grouped range and a refresh with it. B300:
`tests/attention/test_attention_ts_vc.py` 31 passed.

- [X] Tests have been added or updated as needed.
- [X] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/attention/test_attention_ts_vc.py`

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
* Added the option to group only a selected range of tokens, while
keeping tokens outside that range in their original order.
* Token grouping now uses consistent initialization across generations
without changing the caller’s random-number state.
* New generations restart grouping from a consistent initial state,
while scheduled refreshes continue from the current grouping.
  * Grouping settings are respected when refreshing token groupings.
* **Bug Fixes**
* Improved handling of sequences where the final attention tile contains
only one valid token, preventing out-of-range rows from affecting
results.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [d808a84](https://github.com/flashinfer-ai/flashinfer/commit/d808a844baec13d35d51fccdf95985fe8b0d06d4)

- **作者**: Adrian
- **时间**: 2026-11-20T00:35:45Z
- **提交信息**: fix: narrow CuTe-DSL cache dependencies for named imports (#9738)

<!-- .github/pull_request_template.md -->

## 📌 Description

Strict CuTe-DSL cache-key analysis follows imports inside unused helper
functions, expanding the NVFP4 kernel closure beyond its 90-file limit.
Resolve named imports through the selected binding and module
initialization, while retaining full module content in the key and
conservative traversal when the module namespace escapes.

Move the GPU-free closure suite under `tests/cpu/infra/` and cover
`__dict__`/`__getattribute__` access so helper edits still invalidate
persistent caches.

## 🔍 Related Issues

Found while investigating recent internal unit-test CI failures; no
tracking issue.

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

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

Local CPU validation with CuTe-DSL 4.8.0: both cache-key suites passed
(66 tests). The NVFP4 closure is 40 files against the unchanged limit of
90. Changed-file pre-commit hooks, including mypy, passed.

```bash
python -m pytest -q tests/cpu/infra/test_cute_dsl_strict_key_closure.py tests/cpu/infra/test_jit_cache_key_and_build_log.py
```

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust):
`tests/cpu/infra/test_cute_dsl_strict_key_closure.py
tests/cpu/infra/test_jit_cache_key_and_build_log.py`

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

Implemented and reviewed with assistance from OpenAI Codex. Local
validation is complete; GitHub CI has not been requested.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* JIT build keys now reflect changes to dependencies used by named
imports, while avoiding changes caused by unrelated function
dependencies.
* Import-time dependencies remain tracked even when their imported
values are unused.
* Dynamic module access continues to account for dependencies across the
module.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [f629047](https://github.com/flashinfer-ai/flashinfer/commit/f6290475e8367d2a7e7a0a396f2935f3b3f7a8f7)

- **作者**: Ka-Hyun Nam
- **时间**: 2026-11-20T00:16:21Z
- **提交信息**: feat(batch_invariant): stateless call of the GDN class `gdn.bf16.c64` (a trainer's forward pass) with its boundary states (#9677)

Follow-up to #9405: six commits on `main` (the stateless call,
`train_states`, its row layout, then three commits of argument checks
from review).

## What it adds

`flashinfer.chunk_gated_delta_rule(..., batch_invariant=True)` without
`initial_state` is now a stateless call: packed whole sequences, every
one from the zero state, rows only. It is the form a training forward
takes, and its rows are bit for bit the rows inference returns for the
same sequence.

```python
out = torch.empty_like(v)          # once, reused every step
flashinfer.chunk_gated_delta_rule(
    q, k, v, g, beta, cu_seqlens=cu, cu_seqlens_cpu=offsets, output=out,
    use_qk_l2norm_in_kernel=True, gate_domain="log", batch_invariant=True,
)
```

The stateless call itself needs no new keyword. One optional keyword,
`train_states`, makes the same launch store the intermediates a backward
pass works from:

```python
from flashinfer.batch_invariant.gdn import training_state_rows, training_state_slots

states = torch.empty(training_state_slots(seq_lens), HV, 128, 128, device=v.device)   # fp32, once per layer
flashinfer.chunk_gated_delta_rule(
    q, k, v, g, beta, cu_seqlens=cu, cu_seqlens_cpu=offsets, output=out, train_states=states,
    use_qk_l2norm_in_kernel=True, gate_domain="log", batch_invariant=True,
)
rows = training_state_rows(seq_lens)   # rows[i][j]: the state chunk j of sequence i starts from (zero for j = 0)
```

## Intermediates for a backward pass

`train_states` receives the state every 64-token chunk of every sequence
starts from, written in the same launch by the kernel's existing
checkpoint outputs. The layout is the one cuDNN's GDN backward
(`cudnn::gated_delta_net_bwd`) takes as `state_checkpoints` with
`checkpoint_every_n_tokens=64`.

| What a chunked GDN backward works from | Where it comes from |
|---|---|
| `q`, `k`, `v`, `g`, `beta`, the output gradient | the trainer has them
|
| the state each chunk starts from | `train_states` |
| normalized `q` / `k`, cumulative gates, the solved triangular matrix,
corrected values | recomputed by the backward per chunk, from the
chunk's own 64 input rows and its starting state |
| the state after the last token | not consumed by a backward; not
stored |

- Layout: `(n - 1) // 64 + 1` rows per sequence of `n` tokens, sequences
in call order; a sequence's first row is the zero state its first chunk
starts from (the call writes the zeros), row `j` the state after its
first `64 * j` tokens. A state is `[HV, 128 (value), 128 (key)]`, one
per v head; FLA's `h` is the transpose.
- Checked against cuDNN's backward on SM100 (B100, cuDNN frontend
1.32.3, same `q`, `k`, `v`, `g`, `beta`, `cu_seqlens`, `scale`,
in-kernel l2-norm, log gates): it takes the fp32 buffer as it is. Its
gradients from this series differ from the ones it computes from its own
recomputed series by 0.03 % to 0.5 % in relative L2 norm (`dv` is
identical), and both sit at 0.5 % from an fp64 autograd of the token
recurrence, which is bf16 rounding of the rows. Three shapes: six ragged
sequences at 2 / 4 heads, three at 4 / 8, one of 4096 tokens at 16 / 48.
A frontend whose check requires the series in the input dtype takes
`states.to(torch.bfloat16)`; that path was run as well and gives the
same agreement.
- The state a chunk starts from is the one term a backward cannot
recompute from the chunk's own inputs; without it a backward first
re-runs the state scan over the sequence (FLA's backward and cuDNN's
default path do). cuDNN's backward takes nothing else from a forward, so
the kernel's per-chunk terms are not exported.
- Each stored state is bit for bit the state an inference prefill of the
same prefix leaves in its pool, whatever the other sequences of the
call; the output rows are the rows of the call without `train_states`.
cuDNN's own series is a bf16 rounding of its forward's states and is not
these bits; the gradient is the backward's, and this PR makes no bitwise
statement about it.
- Cost: 64 KiB per v head and chunk (48 KiB per token at 48 v heads for
long sequences, four times the output), index tensors for the layout
that are copied to the device once per distinct offsets (the last 16 are
kept), and the time in the table below.

## What it guarantees

- Stateless forward == inference prefill, bitwise, per sequence, for any
batch composition, order and number of sequences. Since the class
already makes chunked prefill and decode equal to prefill, the rows are
also the chunked-prefill and decode rows. The call is one launch of the
class's prefill kernel in which every sequence reads the zero state and
stores none.
- No state pool, nothing kept next to a pool, no state returned.
`state_indices`, `prefix_lens`, `output_state` and
`output_final_state=True` raise the class's typed error without
`initial_state`; so does `train_states` with `initial_state`, or a
buffer that is not 16-byte aligned.
- `output` and `train_states` may share no memory with an input, the
offsets, each other or one of the class's pools (a pool owns its storage
from its first slot to the storage's end): typed error before anything
is written. An `output` allocated under `inference_mode` is refused in a
call outside it, and the call bumps `output`'s autograd version.
- Given `cu_seqlens_cpu`, the call runs from those host offsets with or
without `train_states`, so device and host offsets cannot disagree in it
(only their lengths are compared); offsets that are not 1-D integers
raise the typed error.
- The rows are written into the caller's `output`; with a contiguous
int32 `cu_seqlens` on the device and no `cu_seqlens_cpu`, the call
without `train_states` adds no allocation of its own and keeps nothing
per call after it returns. With `cu_seqlens_cpu` the host offsets are
copied to the device once per distinct offsets and the last 16 copies
are kept (a few int32 per sequence). Per device and v-head count the
class keeps one 3.0 MiB tensor the kernel is pointed at, allocated at
the first stateless call, and an int32 index tensor.
- Inference is unchanged: none of the sources the class fingerprint
digests is touched, the fingerprint is the same before and after, and
the existing class tests pass as they are.

## What it does not do

- **No backward. The rows carry no `grad_fn`**, also when an input
requires grad (inputs are read as plain values). A trainer's backward is
its own, for example its existing differentiable op wrapped in an
`autograd.Function` whose forward returns these rows; what that gradient
is, and whether it is batch-invariant, is not this PR's claim.
- The prefill operator underneath still allocates its per-call
transients, as in every prefill of the class: the normalized `q` / `k`
(`2 * T * HQ * 256` bytes), the linear gates (`4 * T * HV` bytes) and a
small workspace. Removing them means an `out=` argument in
`gdn_kernels/qk_l2norm.py`, which the fingerprint digests, so it is left
for a change that renames the class anyway.
- Zero initial state and whole sequences only. A sequence that has to
continue later is a pool call. The call cannot be captured in a CUDA
graph (it raises).

## Behaviour change to look at

A `batch_invariant=True` call without `initial_state` used to raise. It
now runs when none of the other state arguments is passed, so a decode
step that drops its pool gets first-token rows instead of an error. A
caller that passes `state_indices` still gets the typed error. The
README lists this under what the caller owes the class.

Also: `output.requires_grad` is now a typed error on the pool path too
(it failed untyped before).

## Tests

`tests/gdn/test_batch_invariant_gdn_stateless.py`: stateless rows
against the pool prefill (batched and each sequence alone; 16 / 48, 4 /
8 and 16 / 16 heads; lengths 1 to 1000 including 63, 64, 65; weak and
strong decay), against chunked prefill plus decode, across batch subsets
and orders, more than 64 sequences, inputs that require grad, output
buffer and nothing kept, a NaN staying in its sequence, typed errors.
For `train_states`: every stored state against the pool state of an
inference prefill of the same prefix (bitwise), independence of the
batch, a chunk's rows following from its stored state under the fp64
recurrence, single-chunk sequences storing their zero state, host
offsets with an output buffer, rows beyond the stored ones untouched,
typed errors, and cuDNN's GDN backward run on the series against its own
recomputed series (skipped without the cuDNN frontend).

| Part | `tests/gdn/test_batch_invariant_gdn_stateless.py` |
`tests/gdn/test_batch_invariant_gdn.py` +
`tests/batch_invariant/test_gdn_lean.py` |
|---|---|---|
| GB300 (SM103), CUDA 13.0 | 101 passed | 103 passed, 3 skipped |
| Vera Rubin NVL72 (SM107), CUDA 13.4 | 101 passed | 103 passed, 3
skipped |
| B100 (SM100), CUDA 13.0 | 101 passed | 103 passed, 3 skipped |

Whole files with a fresh JIT cache (B100 on this head; GB300 and Vera
Rubin NVL72 on the commit before it, which differs in documentation
only), with cuDNN frontend 1.32.3 installed on all three parts (so the
cuDNN backward test ran). The class fingerprint is
`gdn-bf16-c64-6086f53017307e1b` before and after these commits. On the
commit before the layout change, a `train_states` buffer above 2^31
elements (2807 states at 48 v heads, 8.8 GB) was checked on B200 against
pool states at rows on both sides of the 2^31 element offset; that probe
was not repeated on this head.

## Performance

One layer at 16 q heads x 48 v heads, head size 128. Each cell is wall
clock of the whole call with a device synchronize (median of 9) / CUPTI
GPU time with a cold L2 cache. Compared with FLA's Triton
`chunk_gated_delta_rule` forward (0.6.0) and with this class's own
prefill on a state pool. "Kept" is memory that stays allocated between
and after calls, inputs excluded; with `train_states` it includes the
states buffer, and the 3.0 MiB per-device tensor of the stateless call
is not counted.

| Part | Config (tokens) | Stateless ms | Stateless + `train_states` ms
| Pool prefill ms | FLA Triton fwd ms, grad on | Stateless vs FLA (wall)
| With states vs FLA (wall) | Kept KB/token: stateless / with states /
pool / FLA grad on |
|---|---|---|---|---|---|---|---|---|
| Vera Rubin NVL72 | 1 x 1024 (1024) | 0.13 / 0.08 | 0.17 / 0.11 | 0.14
/ 0.12 | 0.38 / 0.40 | 3.0x | 2.3x | 12.0 / 60.0 / 19.5 / 42.6 |
| Vera Rubin NVL72 | 1 x 4096 (4096) | 0.20 / 0.15 | 0.29 / 0.23 | 0.21
/ 0.19 | 0.46 / 0.49 | 2.3x | 1.6x | 12.0 / 60.0 / 13.9 / 42.6 |
| Vera Rubin NVL72 | 1 x 16384 (16384) | 0.47 / 0.42 | 0.77 / 0.71 |
0.48 / 0.46 | 1.24 / 1.24 | 2.6x | 1.6x | 12.0 / 60.0 / 12.5 / 42.6 |
| Vera Rubin NVL72 | 1 x 65536 (65536) | 1.62 / 1.57 | 2.76 / 2.71 |
1.63 / 1.61 | 4.77 / 4.84 | 2.9x | 1.7x | 12.0 / 60.0 / 12.1 / 42.6 |
| Vera Rubin NVL72 | 8 x 2048 (16384) | 0.23 / 0.17 | 0.31 / 0.25 | 0.24
/ 0.22 | 1.01 / 1.02 | 4.4x | 3.3x | 12.0 / 60.0 / 15.8 / 42.6 |
| Vera Rubin NVL72 | 16 ragged (23970) | 0.37 / 0.32 | 0.54 / 0.47 |
0.50 / 0.48 | 1.47 / 1.48 | 3.9x | 2.7x | 12.0 / 60.9 / 17.9 / 42.6 |
| Vera Rubin NVL72 | 64 x 512 (32768) | 0.43 / 0.37 | 0.62 / 0.54 | 0.46
/ 0.43 | 1.95 / 1.97 | 4.5x | 3.1x | 12.0 / 60.0 / 27.0 / 42.6 |
| GB300 | 1 x 1024 (1024) | 0.28 / 0.19 | 0.35 / 0.22 | 0.33 / 0.31 |
0.89 / 1.05 | 3.2x | 2.6x | 12.0 / 60.0 / 19.5 / 42.6 |
| GB300 | 1 x 4096 (4096) | 0.37 / 0.27 | 0.47 / 0.37 | 0.38 / 0.36 |
0.93 / 1.08 | 2.5x | 2.0x | 12.0 / 60.0 / 13.9 / 42.6 |
| GB300 | 1 x 16384 (16384) | 0.70 / 0.61 | 1.05 / 0.94 | 0.71 / 0.69 |
1.71 / 1.78 | 2.4x | 1.6x | 12.0 / 60.0 / 12.5 / 42.6 |
| GB300 | 1 x 65536 (65536) | 2.13 / 2.03 | 3.43 / 3.30 | 2.15 / 2.11 |
6.52 / 6.54 | 3.1x | 1.9x | 12.0 / 60.0 / 12.1 / 42.6 |
| GB300 | 8 x 2048 (16384) | 0.42 / 0.34 | 0.59 / 0.48 | 0.46 / 0.44 |
1.59 / 1.65 | 3.7x | 2.7x | 12.0 / 60.0 / 15.8 / 42.6 |
| GB300 | 16 ragged (23970) | 0.57 / 0.49 | 0.83 / 0.72 | 0.80 / 0.82 |
2.21 / 2.18 | 3.8x | 2.6x | 12.0 / 60.9 / 17.9 / 42.6 |
| GB300 | 64 x 512 (32768) | 0.70 / 0.58 | 1.02 / 0.88 | 0.78 / 0.73 |
2.94 / 2.92 | 4.2x | 2.9x | 12.0 / 60.0 / 27.0 / 42.6 |

- All rows are on the commit before this head, which differs from it in
documentation only. The benchmark repeats its offsets, so the device
copy of the host offsets is reused; a call with offsets not among the
last 16 pays one small host-to-device copy (about 40 us per call on both
parts when measured without the reuse).
- Against 58862b8c (before the argument checks) on Vera Rubin NVL72: the
stateless call is 0 % to 11 % slower (0.013 ms at the smallest
configuration, the host-side refusals), the call with `train_states` 1 %
to 13 % faster (its index tensors are no longer copied per call).
- Against FLA's Triton forward (wall): 2.3x to 4.5x faster on Vera Rubin
NVL72, 2.4x to 4.2x on GB300. With `train_states`: 1.6x to 3.3x faster
on Vera Rubin NVL72, 1.6x to 2.9x on GB300. FLA under `no_grad` is
within 5 % of its time with grad on.
- Storing the state series makes the stateless call 30 % to 70 % longer
on Vera Rubin NVL72 and 23 % to 61 % on GB300 and keeps 48 to 49 KB per
token more (60 to 61 KB per token with the output, against 42.6 for FLA
with grad on).
- Against the class's pool prefill: the pool call takes 0 % to 34 %
longer on Vera Rubin NVL72 and 1 % to 39 % on GB300, and keeps 7.5 to
8.6 MiB per sequence (3.0 MiB of pool, the rest next to it). Why it is
longer was not measured.
- Memory: the stateless call keeps the output buffer (12 KB per token at
48 v heads); FLA with grad on keeps 42.6 KB per token, of which 24 are
the 16-to-48-head copies of `q` / `k` the benchmark makes for it inside
the timed call and 12 its output. Transients: 8 KB per token for the
stateless call, 84 KB per token on top of what it keeps for FLA's
forward.
- FLA ran as installed in the test image, where it reports that
`torch.compile` needs Python 3.11 and falls back to no compile
decoration; the effect on its time is not known.
- The stateless rows were bitwise the pool prefill's rows, and the rows
with `train_states` bitwise the rows without, in every configuration
above on both parts.
- CUPTI is within 0.08 ms of wall on Vera Rubin NVL72 and within 0.16 ms
on GB300. No SM100 timing here; SM100 has the test runs and the cuDNN
backward check only.

## Limits

- SM100 / SM103 / SM107 with CUDA 13, bf16 `q` / `k` / `v` of head size
128, fp32 log gates and `beta`, in-kernel l2-norm: the class's contract,
unchanged.
- cuDNN's backward was run with frontend 1.32.3 only.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

- **New Features**
- Added stateless batch-invariant GDN calls that process sequences from
a zero state without retaining state.
- Added an optional caller-provided buffer for recording states at
64-token boundaries, for use in training.
- Exposed helpers for calculating training-state buffer sizes and row
layouts.
- **Documentation**
- Expanded GDN guidance on stateless calls, state-buffer requirements,
and training-state layouts.
- **Tests**
- Added coverage for stateless execution, training-state buffers,
validation, and cuDNN integration.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>

### [4f24496](https://github.com/flashinfer-ai/flashinfer/commit/4f24496fc78299a6deb5157dd3a514c4430f2360)

- **作者**: Larry Wu
- **时间**: 2026-11-20T00:14:38Z
- **提交信息**: ci: add NVSkills CI request workflow for skills/ (#9698)

## 📌 Description

Adds `.github/workflows/request-nvskills-ci.yml`, the request-workflow
template from
[NVIDIA/skills](https://github.com/NVIDIA/skills/blob/main/.github/workflows/request-nvskills-ci.yml),
unchanged.

With it, a maintainer or admin can comment `/nvskills-ci` on a pull
request that changes `skills/`. NVSkills CI then validates and evaluates
the changed agent skills and pushes a signature commit (`BENCHMARK.md`,
`skill-card.md`, `skill.oms.sig`) to the PR branch. The public
[NVIDIA/skills](https://github.com/NVIDIA/skills) catalog only lists
skills that carry that signature.

- The reusable workflow
(`NVIDIA/skills/.github/workflows/team-request.yml@main`) only
dispatches for PRs that change `skills/` or `team-skills/`. All other
PRs are skipped.
- Until the `NVSKILLS_CI_DISPATCH_TOKEN` secret is configured, the job
skips.
- The `push` trigger only acts on the signing bot's `Attach NVSkills
validation signatures` commit. Other pushes skip the job.

This has to be on `main` before `/nvskills-ci` works, because
comment-triggered workflows run from the default branch. The skills move
that uses it follows in a separate PR.

## 🔍 Related Issues

None. The follow-up PR moves the skills to `skills/`.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

- [ ] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).

  Suggested CI test targets: none. The PR only adds a workflow file.

## Reviewer Notes

Before `/nvskills-ci` can run, these one-time setup steps are needed:
1. NVSkills CI maintainers add this repo to their onboarding list and
issue the dispatch token. This is requested.
2. A `flashinfer-ai` org owner installs the NVSkills CI GitHub App on
this repository only.
3. A repo admin adds the token as the `NVSKILLS_CI_DISPATCH_TOKEN`
Actions secret.
4. After the first run, add the `require-nvskills-ci` status check
(exact name from that run) as a required check on `main`. Otherwise a
skill edit can merge without a fresh signature.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Chores**
* Added an automated workflow for requesting NVSkills validation through
pull request activity, designated comments, and qualifying pushes. This
change affects project validation processes and does not add user-facing
application features.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-11-21
**监控日期**: 2026-11-20
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4831
- **最后更新**: 2026-11-20T02:13:27Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: FV SuperAgent

## AI分析总结

## 提交分析总结（hao-ai-lab/FastVideo，昨日第 1/1 批）

**1. 主要更新类型**
- 纯文档更新（docs），无代码逻辑变更。属于发布公告类提交。

**2. 关键变更点及与项目方向的关系**
- 在 README 顶部导航区新增 Dreamverse Harness 的链接，与已有的 Uniserve、Documentation、Cookbook 并列，形成完整的"核心工具 + 配套生态"入口矩阵。
- 正式宣布 Dreamverse Harness 发布，该仓库（dreamverse-harness）此前已在 README 中被引用，本次提交将其升格为一等公民级的对外入口。
- 这与 FastVideo 作为高性能视频生成/推理框架的定位一致：主仓库专注核心引擎，周边能力（harness 编排、uniserve 服务化）拆分为独立项目，通过文档互相引流。

**3. 对项目的影响和潜在意义**
- 降低新用户的上手门槛：顶部链接集中呈现全部生态资源，减少寻找成本。
- 标志着 FastVideo 生态从"单一库"向"工具集"演进，Dreamverse Harness 可能承担训练/评测/流水线编排的职责，补齐端到端工作流。
- 对外发布信号明确，有助于吸引社区贡献者和潜在合作者关注周边项目。

**4. 值得关注的技术点**
- 多仓库协作模式的清晰化：hao-ai-lab 组织下 FastVideo、Uniserve、Dreamverse Harness 分工明确，值得跟踪三者间的接口约定与版本兼容策略。
- README 作为单一事实来源的维护方式，Co-authored-by 显示有外部贡献者参与，反映社区协作流程。

**5. 对项目发展的影响**
- 结合 README 可知，FastVideo 正在构建完整的视频生成基础设施（文档 + Cookbook + Harness + Uniserve）。本次提交通过强化入口导航，把分散的生态组件串联起来，是生态整合期的典型文档动作。
- 此类提交虽不改变功能，但对项目"从工具到平台"的品牌建设和用户转化具有战略意义，后续应关注 Dreamverse Harness 的实际功能落地以及与 FastVideo 主仓库的集成深度，以判断生态协同是否真正形成闭环。

## 详细提交记录

### [5af9897](https://github.com/hao-ai-lab/FastVideo/commit/5af9897e75007f9c5745f3446c18a4852c9c04a8)

- **作者**: FV SuperAgent
- **时间**: 2026-11-20T04:31:07Z
- **提交信息**: [docs] Announce the Dreamverse Harness release and add top links (#2118)

Co-authored-by: Aryan Kumar <156166681+aryan5v@users.noreply.github.com>

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-11-21
**监控日期**: 2026-11-20
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34959
- **最后更新**: 2026-11-20T18:30:08Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 3
- **主要提交者**: yzhautouskay, Jingya HUANG, Sayak Paul

## AI分析总结

# HuggingFace Diffusers 昨日提交分析（共3条）

## 1. 主要更新类型
- **Bug修复**：修复分布式训练中默认随机数生成器（RNG）同步的问题（1条）
- **功能新增**：为Cosmos 3模型添加原生张量并行（Tensor Parallelism）支持（1条）
- **测试重构**：移除测试目录中的LoRA工具函数，清理测试代码（1条）

总体以**分布式训练稳定性**和**大模型并行推理**为主要方向。

## 2. 关键变更点及与项目方向的关系

- **RNG同步修复（#15141）**：修正了分布式环境下默认RNG仅在并行网格（parallel mesh）内同步而非全局同步的逻辑，使用broadcast而非all-gather优化通信。这直接关联diffusers对**多GPU/多节点训练与推理一致性**的支持，确保不同并行策略下采样结果可复现。
- **Cosmos 3张量并行（#15137）**：为新一代视频/图像生成模型Cosmos 3引入原生TP支持，复用`_get_tp_plan`机制和`_check_tp_supported`校验，提供条件式TP条目和使用文档。这体现了项目**快速适配最新大规模生成模型**的策略。
- **测试清理（#14965）**：移除tests/lora中的LoRA工具类，属于测试基础设施的去重复化，降低维护成本。

## 3. 对项目的影响和潜在意义

- RNG修复提升了**分布式训练的正确性与可复现性**，对科研用户和大规模部署场景至关重要。
- Cosmos 3原生TP支持使用户无需自定义并行代码即可在多设备上高效运行该模型，**降低了大模型使用门槛**，与diffusers"开源易用的生成模型库"定位高度一致。
- 测试重构虽影响面小，但有助于CI稳定性，减少未来LoRA相关测试的耦合。

## 4. 值得关注的技术点

- **仅在并行网格内同步RNG**而非全局同步的设计，避免了不必要的跨组通信开销，体现了对大规模训练通信效率的精细优化。
- TP实现采用**条件式条目和配置复用**（`_get_tp_plan`、`_check_tp_supported`），而非为每个模型编写定制逻辑，展示了良好的架构复用性。
- 测试中涵盖**submesh、from_pretrained加载、非并行基准对比**等多种场景，确保TP和RNG修复的健壮性。
- 提交中出现了AI辅助开发（Claude）的Co-author标记，反映了社区工作流的新趋势。

## 5. 对项目发展的整体影响

结合README可知，diffusers是Apache 2.0许可的开源扩散模型库。上述提交延续了项目**两条主线**：一是持续完善分布式/并行基础设施，支撑越来越大的生成模型；二是快速集成前沿模型（如Cosmos 3）并提供开箱即用的并行能力。这组变更共同强化了diffusers在**大规模生产环境中的可靠性**，对社区用户从原型验证走向多卡部署具有直接的实用价值。

## 详细提交记录

### [c215605](https://github.com/huggingface/diffusers/commit/c215605a189169236544c1c9828789bfca0891d1)

- **作者**: Jingya HUANG
- **时间**: 2026-11-20T14:53:46Z
- **提交信息**: fix: Fix default RNG synchronization for ditribution (#15141)

* fix: Fix default RNG synchronization for ditribution

* fix: use broadcast for just one rank instead of all gather all ranks

* removal: simplify the docstring

* test: seeds matching test

* test: improve, get into existed tests

* fix: sync default RNG only within the parallel mesh

* test: move parallel RNG sync checks into a standalone test

* review:  test RNG sync against non-parallel run and from_pretrained

* generalize the test case for sync rng for all supported models.

* Cover submesh and from_pretrained in Neuron/TPU RNG sync tests

* Handle list-valued main inputs in the parallel RNG sync tests

Co-Authored-By: Claude Fable 5.2 <noreply@anthropic.com>

---------

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>
Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>

### [e24786a](https://github.com/huggingface/diffusers/commit/e24786a5d347439a2847be74c4a61405426fbb42)

- **作者**: Sayak Paul
- **时间**: 2026-11-20T03:56:24Z
- **提交信息**: [tests] remove lora utils from tests/lora (#14965)

remove lora utils from tests/lora

### [5416331](https://github.com/huggingface/diffusers/commit/54163315d7fd0232959f82423be550e3fc94c80e)

- **作者**: yzhautouskay
- **时间**: 2026-11-20T03:42:01Z
- **提交信息**: [Cosmos3] Add native tensor parallelism (#15137)

* Add native tensor parallelism for Cosmos 3

* use _get_tp_plan for overrides.

* Refactor Cosmos 3 tensor parallel tests

* Simplify Cosmos 3 tensor parallelism documentation

* Fix docs

* Refactor tests to address review comments

* Bring back code snippet to the TP usage docs

* Refactor Cosmos 3 tensor parallel tests

* Use conditional TP entries for Cosmos3

* Remove custom Cosmos 3 BF16 TP test and simplify test workers

* Fix Cosmos 3 tensor parallelism guide link

* Remove Cosmos config checks override, reuse `_check_tp_supported`

* Remove TP head-divisibility test from shared model tests

---------

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>
Co-authored-by: YiYi Xu <yixu310@gmail.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-11-21
**监控日期**: 2026-11-20
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


**报告日期**: 2026-11-21
**监控日期**: 2026-11-20
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13423
- **最后更新**: 2026-11-21T00:43:01Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Zhongjie Duan

## AI分析总结

### 提交分析总结

#### 1. 主要更新类型
- **功能新增**：集成 ModelScope AIGC 推理服务，扩展项目功能范围。
- **文档更新**：同步更新相关文档，确保新功能的可理解性与可维护性。

#### 2. 关键变更点与项目整体方向的关系
- **新增推理服务**：符合 DiffSynth-Studio 作为扩散模型开发 Studio 的定位，从模型训练与实验工具向完整生产级解决方案演进。项目 README 强调其作为 AI 生成内容（AIGC）领域工具链的属性，推理服务的加入填补了“模型开发”到“模型部署/推理”之间的关键环节，与 ModelScope 生态的整合意图一致。
- **文档同步更新**：体现项目对用户体验与工程规范的重视，确保新功能可被社区快速上手，维护项目开源协作的透明性。

#### 3. 对项目的影响和潜在意义
- **提升实用性与部署能力**：推理服务为开发者提供了端到端能力，用户无需额外搭建推理管线即可直接调用，降低使用门槛。
- **增强生态整合**：作为 ModelScope 官方项目，此变更强化了与阿里云 ModelScope 平台的协同，可能吸引更多企业用户和研究者。
- **潜在影响**：可能推动项目在 AIGC 工业应用场景中的采用，为后续模型服务化、API 化奠定基础。

#### 4. 值得关注的技术点
- **服务架构设计**：需关注推理服务如何封装 DiffSynth 核心模型，是否支持多模型调度、并发处理及资源优化。
- **与 ModelScope 平台的交互机制**：例如服务是否依赖 ModelScope 的托管环境或模型仓库，以及认证、计费等云原生特性。
- **性能与扩展性**：推理服务在 GPU 资源利用、延迟控制方面的表现，尤其对扩散模型这类计算密集型任务至关重要。
- **API 设计**：接口是否简洁通用，能否灵活适配不同 DiffSynth 变体模型。

#### 5. 基于项目背景对项目发展的影响
DiffSynth-Studio 作为 ModelScope 生态下的扩散模型开发平台，其 README 展示了工具链完整性与社区活跃度。此次提交标志着项目从**离线实验工具**向**在线推理服务**的演进，使其更贴近 AIGC 生产需求。这不仅巩固了项目在扩散模型领域的工具地位，也可能为未来集成更多模型（如视频生成、多模态合成）提供服务化范本。长期看，此举有助于提升项目在开发者社区的采用率，加速 AIGC 技术在企业级场景的落地，并强化 ModelScope 作为一站式 AI 开发平台的竞争优势。

## 详细提交记录

### [d32f724](https://github.com/modelscope/DiffSynth-Studio/commit/d32f72424cd22bc0ea8100cc57559149b4eac933)

- **作者**: Zhongjie Duan
- **时间**: 2026-11-20T04:29:52Z
- **提交信息**: Release ModelScope AIGC Inference Services (#1843)

* add services

* update docs

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-11-21
**监控日期**: 2026-11-20
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 38890
- **最后更新**: 2026-11-21T01:53:29Z

## 提交统计

- **昨日提交总数**: 124
- **提交者数量**: 59
- **主要提交者**: Ziqi Fan, Aarne Talman, Kevin Mi

## AI分析总结

# sgl-project/sglang 昨日提交合并分析（共 124 条）

## 一、主要更新类型

功能新增与性能优化各占约三成，其中性能优化约 28 条、功能新增约 37 条，Bug 修复约 40 条，其余为 CI、测试、文档与重构。

## 二、关键变更与项目方向

**多模态与扩散模型全面提速**：围绕 H3、flux3、cosmos3、zimage、Hunyuan3D 等 diffusion 子系统，通过 CUDA graph 重放文本编码器、KV cache 优化、AMD aiter packed attention 压缩延迟；新增 Wan2.2-S2V-14B 语音转视频模型（Intel XPU 适配），并完善 FLUX.3 条件缓存与 VAE 配置文档，语音/视频生成覆盖面进一步扩大。

**rust-server 成为重要演进方向**：约 10 条提交涉及 Rust 服务端，包括多模态特征独立传输、逐 chunk BPE 解码、队列深度与拒绝数等指标导出、请求日志与崩溃转储优化、健康检查修复，显示高性能服务层正向 Rust 迁移。

**多硬件生态持续深化**：AMD（gfx950/gfx942、ROCm、AITER、UCX）、华为 NPU（Ascend A5、DSV4.1、kimi-k3.1、GLM DSA，内核升至 2026.11.0.post10）、Intel（GPTQ INT4）、XPU（W8A8 int8、功能整合）密集提交，非 CUDA 后端已进入主力维护期，降低对 NVIDIA 的单一依赖。

**PD 分离与调度健壮性**：KV 预取让渡、parked prefill 让出 KV、ignore_eos 流式准入、KV 校验和、hicache 请求级 KV 提示转发等修复，指向云端大规模分布式 serving 的生产稳定性。

**投机解码与内核底层优化**：DFLASH 请求惩罚修复、megakernel 拆分、FlashInfer CuTe DSL MoE prefill CUDA graph、EAGLE draft capture、DSA/MLA binding、top logprobs 批量化、DP attention 死锁修复，投机解码仍是性能主战场。

**模型生态扩展**：新增 Hunyuan-4-Flash 及专用内核（IndexPool、Engram、fused iHC），Gemma 4 视觉/工具调用修复，H4-Flash 融合 gate。

## 三、影响与技术关注点

这批提交体现"性能极限 + 生产稳定性"双轨推进：THP 开关、单次 memcpy、MegaMoE 局部输入、按节点 rank 拆分的检查点预取与多线程加载在途字节上限等小粒度优化持续压榨延迟吞吐；SynthID Text 水印与 Gumbel 水印统一接口、logprob 自定义候选集返回，拓展输出溯源与评测能力；kimi-k3 序列并行 LayerNorm 与多播通信优化长上下文 prefill；attention-TP 独立 PyNCCL 通信器保障大规模并行正确性；weight-update 融合跨 chunk 状态支持在线热更新；NVTX forward span 与 CI 延迟基线收紧提升可观测性与回归管控。

## 四、整体意义

SGLang 正沿三条主线发展：内核级性能（CUDA graph、megakernel、AMD TLX）、生产级调度与可靠性（PD 分离、流式会话、Rust-server）、模型与硬件广度（语音转视频、扩散模型、XPU/NPU）。这种深度与广度并进的节奏，巩固了其作为硬件无关、模态广泛的通用高性能推理平台的地位，为多模态生成与企业级分布式部署奠定基础。

## 详细提交记录

### [d2d70c6](https://github.com/sgl-project/sglang/commit/d2d70c6dd67594adc96934d0553027c1e9bb1def)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-20T23:57:50Z
- **提交信息**: [Fix] hunyuan_v4_flash: Read TP size and rank through get_parallel() and list its fusion gate (#51969)

### [94a698a](https://github.com/sgl-project/sglang/commit/94a698a791efc95993a093be0a84353474e8576c)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-20T23:55:45Z
- **提交信息**: [Doc] agents: Require kernel-organization before changing python/sglang/kernels (#51759)

### [44a3919](https://github.com/sgl-project/sglang/commit/44a391941aab5269a14b3726ce145c92bbe7d374)

- **作者**: Mick
- **时间**: 2026-11-20T23:52:07Z
- **提交信息**: [Fix] diffusion: Follow the Pika-H3-Flex reference pipeline in keyframe fitting, audio length and reference resizing (#51935)

Co-authored-by: niehen6174 <42087078+niehen6174@users.noreply.github.com>
Co-authored-by: Claude Mythos 5.2 <noreply@anthropic.com>
Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [eec0eec](https://github.com/sgl-project/sglang/commit/eec0eecfc7cf925b9842a03e9b795b8d99e0c47d)

- **作者**: Mick
- **时间**: 2026-11-20T23:50:45Z
- **提交信息**: [Perf] [AMD] diffusion: MiniMax-H3 packed attention on aiter's batch and MHA v4 kernels (#51933)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Mythos 5.2 <noreply@anthropic.com>

### [ed939d6](https://github.com/sgl-project/sglang/commit/ed939d6ac280a692ee088ff90f600d133c1ac5d2)

- **作者**: Akshat Anand
- **时间**: 2026-11-20T23:48:45Z
- **提交信息**: [Fix] dflash: Apply request penalties under DFLASH and DSPARK (#47020)

Co-authored-by: cipheraxat <cipheraxat@users.noreply.github.com>
Co-authored-by: hnyls2002 <lsyincs@gmail.com>

### [bb8699e](https://github.com/sgl-project/sglang/commit/bb8699efe1276a5e8227faf6f94e08a583c5d142)

- **作者**: metamergebot
- **时间**: 2026-11-20T23:33:37Z
- **提交信息**: [Feat] cp: Let zigzag CP keep a batch with a request shorter than 2 x cp_size (#51880)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: charlotte12l <charlotte12l@users.noreply.github.com>

### [bb06e81](https://github.com/sgl-project/sglang/commit/bb06e81637f44c683f28b69e352e3cbc53263643)

- **作者**: metamergebot
- **时间**: 2026-11-20T23:33:34Z
- **提交信息**: [Feat] logprob: Return an input candidate selector's weights with the prompt logprobs (#51909)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: hanming-lu <hanming-lu@users.noreply.github.com>

### [0f3159a](https://github.com/sgl-project/sglang/commit/0f3159a683fec1bd496043c84cfbf33e3b9f2858)

- **作者**: Ziang Li
- **时间**: 2026-11-20T23:25:19Z
- **提交信息**: [Feat] [NVIDIA] cuda-graph: Prefill CUDA graphs for FlashInfer CuTe DSL MoE and MegaMoE (#50684)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [4919cc8](https://github.com/sgl-project/sglang/commit/4919cc880058e16960c586793f7b0b33577c8dd3)

- **作者**: metamergebot
- **时间**: 2026-11-20T23:19:52Z
- **提交信息**: [Feat] rust-server: Let a processor publish multimodal features in its own transport (#51897)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: doanmh <doanmh@users.noreply.github.com>

### [b555418](https://github.com/sgl-project/sglang/commit/b5554189a8b110a548930f675878b26410f859f6)

- **作者**: metamergebot
- **时间**: 2026-11-20T23:19:37Z
- **提交信息**: [Feat] scheduler: Report where an ignore_eos request's first stop token would have ended it (#51165)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: sevenEng <sevenEng@users.noreply.github.com>

### [4e0535f](https://github.com/sgl-project/sglang/commit/4e0535f26957159629358066d27e36704eb07f18)

- **作者**: metamergebot
- **时间**: 2026-11-20T23:18:48Z
- **提交信息**: [Feat] cuda-graph: Let a model declare the dtype of the prefill input_embeds buffer (#51889)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: YavorGIvanov <YavorGIvanov@users.noreply.github.com>

### [e87de3d](https://github.com/sgl-project/sglang/commit/e87de3d0bb341a647ebbc29e3130a49c1d3437bc)

- **作者**: metamergebot
- **时间**: 2026-11-20T23:16:19Z
- **提交信息**: [Perf] rust-server: Decode each chunk's own bytes for byte-level BPE tokenizers (#51945)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: kingsmad <kingsmad@users.noreply.github.com>

### [215cf36](https://github.com/sgl-project/sglang/commit/215cf36020d3c3795fa6be85fec04bf84f37d663)

- **作者**: metamergebot
- **时间**: 2026-11-20T23:09:51Z
- **提交信息**: [Fix] disaggregation: A prefill request without a decode reservation yields its storage prefetch to a bootstrapped one (#51892)

Co-authored-by: metamergebot <metamergebot@users.noreply.github.com>
Co-authored-by: 842974287 <842974287@users.noreply.github.com>

### [7490430](https://github.com/sgl-project/sglang/commit/7490430dc10e6baf1231a35a9009f35eb3d43279)

- **作者**: metamergebot
- **时间**: 2026-11-20T23:09:28Z
- **提交信息**: [Fix] disaggregation: A parked optimistic prefill yields its KV when a bootstrapped request is blocked on KV (#51882)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: 842974287 <842974287@users.noreply.github.com>

### [6a6f4e5](https://github.com/sgl-project/sglang/commit/6a6f4e5da89bcb91d2eb79daed89e2d1752adab2)

- **作者**: metamergebot
- **时间**: 2026-11-20T23:07:50Z
- **提交信息**: [Refactor] rust-server: Remove the attention-DP generation relay (#51932)

Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [237cbfd](https://github.com/sgl-project/sglang/commit/237cbfd961e0617694f62b2bd6a0266b20ac09c1)

- **作者**: metamergebot
- **时间**: 2026-11-20T23:06:52Z
- **提交信息**: [Feat] logprob: Let a request choose its prompt logprob candidates in place of the top-k (#51899)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: Hanming Lu <69857889+hanming-lu@users.noreply.github.com>

### [c8d7acf](https://github.com/sgl-project/sglang/commit/c8d7acf234b40f021d973c75479d9ce0687ead6e)

- **作者**: metamergebot
- **时间**: 2026-11-20T23:05:11Z
- **提交信息**: [Perf] rust-server: Cut request-log and crash-dump copies and recorder lock holds (#51904)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [02e26ce](https://github.com/sgl-project/sglang/commit/02e26ce947811bc2271c5d8f6c07a26cd1493850)

- **作者**: metamergebot
- **时间**: 2026-11-20T23:04:34Z
- **提交信息**: [Fix] rust-server: Honor return_prompt_token_ids on /generate and return_token_ids on /v1/completions (#51895)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [2ab47f3](https://github.com/sgl-project/sglang/commit/2ab47f3c4f7066283de5aef3a489091076e8811c)

- **作者**: metamergebot
- **时间**: 2026-11-20T23:03:34Z
- **提交信息**: [Fix] http_server: Write a single /generate stream's finishing event and [DONE] together (#51891)

Co-authored-by: Fei Hu <fei-xx@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [aa69ea8](https://github.com/sgl-project/sglang/commit/aa69ea883476c7c3d445ff0a993df94c8ae2b4e8)

- **作者**: metamergebot
- **时间**: 2026-11-20T23:03:07Z
- **提交信息**: [Feat] rust-server: Export frontend queue depth, queue-full refusals and media fetch slot waits (#51881)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [a459223](https://github.com/sgl-project/sglang/commit/a45922399af0828e5d687e71cd27d77085e93713)

- **作者**: zijiexia
- **时间**: 2026-11-20T22:59:11Z
- **提交信息**: [Doc] cookbook: Use the rtx6000 hardware id for Inkling-2-Mini (#51953)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [9caefef](https://github.com/sgl-project/sglang/commit/9caefef24368277d4f249656daa42f7f61f1de32)

- **作者**: Tri Dao
- **时间**: 2026-11-20T22:28:28Z
- **提交信息**: [Fix] hicache: Keep device-only Mamba checkpoints through write-back eviction (#50841)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Shuwen Wang <47200617+alphabetc1@users.noreply.github.com>

### [44207b4](https://github.com/sgl-project/sglang/commit/44207b4204cadc900912ce4fb377174b7cf32ae6)

- **作者**: Mick
- **时间**: 2026-11-20T22:24:18Z
- **提交信息**: [CI] diffusion: Tighten H100 and B200 latency baselines (#51914)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [e7c382c](https://github.com/sgl-project/sglang/commit/e7c382c12978d7c3481ccfb35609f3c9e206bfea)

- **作者**: YAMY
- **时间**: 2026-11-20T22:20:52Z
- **提交信息**: [Fix] [NVIDIA] moe: keep the tuned autotune key for deferred-finalize FP4 TRT-LLM MoE calls (#50195)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [2195fbd](https://github.com/sgl-project/sglang/commit/2195fbd3c7c91aca466ffee58d194f0a15a34db8)

- **作者**: Qiaolin Yu
- **时间**: 2026-11-20T21:54:11Z
- **提交信息**: [Feat] models: Hunyuan-4-Flash text model (#51668)

Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

### [192b19b](https://github.com/sgl-project/sglang/commit/192b19bf51a06099dc6f15969b0f802954a4a537)

- **作者**: Mick
- **时间**: 2026-11-20T21:48:19Z
- **提交信息**: [Perf] diffusion: Replay the Qwen3 text encoder graph under tensor parallelism (#51908)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [e7caed8](https://github.com/sgl-project/sglang/commit/e7caed84e0bcfe85d7f42e57022695dc30f93bac)

- **作者**: Shangming Cai
- **时间**: 2026-11-20T21:33:54Z
- **提交信息**: [Test] sgl-router: Flush caches before the PD dp-aware spread test (#51686)

### [2ff46c5](https://github.com/sgl-project/sglang/commit/2ff46c5979d1ce1c053433c6bbcd13f1debeb878)

- **作者**: Puyan Lotfi
- **时间**: 2026-11-20T21:27:03Z
- **提交信息**: [Feat] [AMD] tlx: Add the vendored gfx950 TLX GEMM and Muse MoE kernels on stock Triton via uTLX (#50354)

Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: Xinyi Song <xinyisong0111@gmail.com>

### [84c9e76](https://github.com/sgl-project/sglang/commit/84c9e7677a947d368c0d3ffff5861c9c8c8d07b4)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-11-20T21:21:38Z
- **提交信息**: [Refactor] diffusion: Fix silent failures and prune dead code in multimodal_gen (4/4) (#50806)

Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>

### [6c7e1e9](https://github.com/sgl-project/sglang/commit/6c7e1e924cf98953810f494b2717f2f267a042ed)

- **作者**: Mick
- **时间**: 2026-11-20T21:17:03Z
- **提交信息**: [CI] diffusion: Put the real-checkpoint H3 TP check with manual tests (#51648)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [a034bb5](https://github.com/sgl-project/sglang/commit/a034bb57912e73eccf812ee77610e2dd6a8458e2)

- **作者**: Yuwei An
- **时间**: 2026-11-20T21:13:46Z
- **提交信息**: [Refactor] spec/dflash: Take the megakernel out of the DFLASH worker behind a guarded runtime binding (#51676)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [f389121](https://github.com/sgl-project/sglang/commit/f389121c03ce6d454f3e58382a384c9849f05054)

- **作者**: Qiaolin Yu
- **时间**: 2026-11-20T20:49:21Z
- **提交信息**: [Feat] kernels: Hy4-Flash IndexPool, Engram and fused iHC post-pre kernels (#51646)

Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

### [2eb62cf](https://github.com/sgl-project/sglang/commit/2eb62cf50ca752ff57823e00b94163c89244d0c5)

- **作者**: Jimmy Shong
- **时间**: 2026-11-20T20:23:47Z
- **提交信息**: [Doc] cookbook: Point the Inkling-2-Mini install at its pull request (#51930)

### [e3e0f2a](https://github.com/sgl-project/sglang/commit/e3e0f2a3f0fbaa931acf97eabdfe8b180c425f8e)

- **作者**: zijiexia
- **时间**: 2026-11-20T20:15:49Z
- **提交信息**: [Doc] cookbook: Add Inkling-2-Mini cookbook (#51927)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [20a378f](https://github.com/sgl-project/sglang/commit/20a378f7db1a7fe395c72a5f91c8dcf444cd7eec)

- **作者**: Ruilin Gao
- **时间**: 2026-11-20T20:06:09Z
- **提交信息**: [Fix] diffusion/zimage: Run n > 1 outputs one by one (#51464)

### [7e9028a](https://github.com/sgl-project/sglang/commit/7e9028a4d76173e111e57c9f09eaaf25684af480)

- **作者**: Pinjie Xu
- **时间**: 2026-11-20T19:59:53Z
- **提交信息**: [Perf] diffusion/cosmos3: optimize Sim-Bimanual kv cache management (#47889)

Signed-off-by: pinjie <pinjiex@nvidia.com>

### [3988258](https://github.com/sgl-project/sglang/commit/398825821a9efa2d6e9816dbcaa0ed92ea30f47b)

- **作者**: Mick
- **时间**: 2026-11-20T19:57:23Z
- **提交信息**: [CI] diffusion: Calibrate Hunyuan3D shape denoising on computable-e H100s (#51913)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [2c673ff](https://github.com/sgl-project/sglang/commit/2c673ff255fa7cbfbb2952a1ae18a341c9a039b6)

- **作者**: metamergebot
- **时间**: 2026-11-20T19:49:24Z
- **提交信息**: [Test] rust-server: Verify disconnect aborts an admitted unary prefill (#50819)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: frgossen <frgossen@users.noreply.github.com>

### [001ea2a](https://github.com/sgl-project/sglang/commit/001ea2afb6cad1e7443be6a58c089ec8465c5a94)

- **作者**: metamergebot
- **时间**: 2026-11-20T19:49:17Z
- **提交信息**: [Refactor] rust-server: Keep only the test-support helpers that need crate internals (#50897)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [9fc0e2a](https://github.com/sgl-project/sglang/commit/9fc0e2a6ba197f19f00165327adbb7c48cdf8281)

- **作者**: weireweire
- **时间**: 2026-11-20T18:53:25Z
- **提交信息**: [Perf] tokenizer_manager: Drop the prompt token list once a single request is dispatched (#50901)

Co-authored-by: weireweire <20922698+weireweire@users.noreply.github.com>
Co-authored-by: kpham-sgl <khoa.pham@radixark.ai>

### [27dce80](https://github.com/sgl-project/sglang/commit/27dce8023d8be7a838b9b6f333a6185029ce39f1)

- **作者**: ishandhanani
- **时间**: 2026-11-20T18:38:45Z
- **提交信息**: [Chore] ci: Grant AndyDai-nv CI permissions (#51258)

### [41f01f8](https://github.com/sgl-project/sglang/commit/41f01f8b524aa62f3425372ae7626b1de2513d60)

- **作者**: Mick
- **时间**: 2026-11-20T18:20:46Z
- **提交信息**: [Fix] [CI] diffusion: Repair cached subfolders and CI recovery (#50931)

### [f9fc07c](https://github.com/sgl-project/sglang/commit/f9fc07cc74daaf760f590af1e3959fc032c41f70)

- **作者**: Mick
- **时间**: 2026-11-20T18:19:42Z
- **提交信息**: [Perf] diffusion/flux3: Replay the text encoder's forward as a CUDA graph (#51562)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Mythos 5.2 <noreply@anthropic.com>

### [2b24897](https://github.com/sgl-project/sglang/commit/2b248971db8c8c349586c3757663be9cba5e366d)

- **作者**: Rohan Varma
- **时间**: 2026-11-20T17:41:54Z
- **提交信息**: [Feat] [NVIDIA] megakernels: DSA / MLA binding view, EAGLE draft capture checks, early draft embedding sharing (#46210)

Co-authored-by: Yangmin Li <yangminl@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Yuwei An <ayw.sirius19@gmail.com>
Co-authored-by: Po-Han Huang <pohanh@nvidia.com>
Co-authored-by: shuw <shuw@nvidia.com>
Co-authored-by: YAMY <74099316+YAMY1234@users.noreply.github.com>
Co-authored-by: Po-Han Huang (NVIDIA) <53919306+nvpohanh@users.noreply.github.com>

### [53b8e56](https://github.com/sgl-project/sglang/commit/53b8e56e4a065af5993ade615f0dc434947038e2)

- **作者**: Xueshen Liu
- **时间**: 2026-11-20T17:26:15Z
- **提交信息**: [Perf] Foundry: adding the adapter of foundry to enable fast CUDA graph save/load (#42254)

Signed-off-by: Xueshen Liu <liuxs@umich.edu>

### [4f56795](https://github.com/sgl-project/sglang/commit/4f56795ec5485b9bf1c72aea23dd153c3ee07e50)

- **作者**: Khoa Pham
- **时间**: 2026-11-20T17:24:34Z
- **提交信息**: [Fix] distributed: Give the attention-TP subgroup a PyNCCL communicator under attention DP (#51707)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [1761975](https://github.com/sgl-project/sglang/commit/176197551316f6b4998f31fbbb3b7d19daea584a)

- **作者**: metamergebot
- **时间**: 2026-11-20T17:11:39Z
- **提交信息**: [Fix] srt: Check IPv6 availability for default NCCL ports (#50817)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: luccafong <luccafong@users.noreply.github.com>

### [55d93f7](https://github.com/sgl-project/sglang/commit/55d93f72bd032b7480d6df78dfc12cf6a8f62108)

- **作者**: metamergebot
- **时间**: 2026-11-20T17:11:07Z
- **提交信息**: [Perf] rust-server: Derive a multimodal item's identity from one BLAKE3 digest of its feature (#50846)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [f9e1424](https://github.com/sgl-project/sglang/commit/f9e1424f14d6d0bc687f65d6300ee9235ca1381b)

- **作者**: metamergebot
- **时间**: 2026-11-20T17:10:45Z
- **提交信息**: [Feat] bench: Spread a one-batch benchmark batch over per-DP-rank listeners (#50864)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [f7ff1e0](https://github.com/sgl-project/sglang/commit/f7ff1e0a943596329508b9a91b2568aed2208ac3)

- **作者**: Shuwen Wang
- **时间**: 2026-11-20T16:15:57Z
- **提交信息**: [Fix] scheduler: Admit a chunked ignore-eos streaming-session turn after its prefix (#51257)

### [a4347f4](https://github.com/sgl-project/sglang/commit/a4347f43c2cec02f5b89ab1c787c56c3c55ed8fb)

- **作者**: Shuwen Wang
- **时间**: 2026-11-20T15:46:31Z
- **提交信息**: [Fix] simulator: Declare mock storage KV hints capability (#51849)

### [459b85f](https://github.com/sgl-project/sglang/commit/459b85fb6884b980a69c376ba2c4513ff9b0c71f)

- **作者**: Phạm Phú Lợi
- **时间**: 2026-11-20T14:24:23Z
- **提交信息**: [Fix] function_call: Use call order for Gemma4 streaming tool indices (#51592)

Co-authored-by: Po-Han Huang <pohanh@nvidia.com>

### [fa4e39b](https://github.com/sgl-project/sglang/commit/fa4e39b36b10c3fad2a0b7b0a14163f20405650d)

- **作者**: Phạm Phú Lợi
- **时间**: 2026-11-20T14:22:52Z
- **提交信息**: [Fix] function_call: Preserve text between and after Gemma 4 tool calls (#51616)

Co-authored-by: Po-Han Huang <pohanh@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [dc8f1c3](https://github.com/sgl-project/sglang/commit/dc8f1c35bdb960b78065c2c7795fe0148cc08984)

- **作者**: Shuwen Wang
- **时间**: 2026-11-20T13:50:52Z
- **提交信息**: [Fix] linker: Wait for external linker loads before breakable replays that capture KDA state reads (#50635)

### [1e93e43](https://github.com/sgl-project/sglang/commit/1e93e43f3935bd0c448a5361afef9690278b1ca5)

- **作者**: Kevin Mi
- **时间**: 2026-11-20T13:29:52Z
- **提交信息**: [Refactor] [AMD] kimi-k3: Keep Kimi-K3.1's gfx950 modules off the shared import paths (#51366)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [ea442ff](https://github.com/sgl-project/sglang/commit/ea442ff4ab19171212a9ecaa0e175d0f2dd2a595)

- **作者**: Phạm Phú Lợi
- **时间**: 2026-11-20T12:47:22Z
- **提交信息**: [Fix] gemma4: Keep valid vision patches when pooling is skipped (#51718)

Co-authored-by: Po-Han Huang <pohanh@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [8f060f8](https://github.com/sgl-project/sglang/commit/8f060f8337fd33f78ed1eaa4f286331f7712d96f)

- **作者**: Phạm Phú Lợi
- **时间**: 2026-11-20T12:40:57Z
- **提交信息**: [Fix] gemma4: Exclude padding and preserve range during vision pooling (#51615)

Co-authored-by: Po-Han Huang <pohanh@nvidia.com>

### [0c6d6eb](https://github.com/sgl-project/sglang/commit/0c6d6eb04e3b960b2069b30c5359bd6fc7443a19)

- **作者**: chenxb002
- **时间**: 2026-11-20T12:19:04Z
- **提交信息**: [Fix] mem_cache: Fix explicit HND initialization (#50116)

### [7d82bda](https://github.com/sgl-project/sglang/commit/7d82bda66c79f14eaf6fb4664425792558e78478)

- **作者**: Phạm Phú Lợi
- **时间**: 2026-11-20T12:03:38Z
- **提交信息**: [Test] scheduler: Test that the admission re-match records num_matched_prefix_tokens (#43095)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Zhiqiang Xie <zqx@meta.com>
Co-authored-by: Po-Han Huang (NVIDIA) <53919306+nvpohanh@users.noreply.github.com>

### [f5149f3](https://github.com/sgl-project/sglang/commit/f5149f367b8f0fd728bca44f4e77c8fc102ad803)

- **作者**: weireweire
- **时间**: 2026-11-20T11:05:40Z
- **提交信息**: [Fix] rust-server: Answer the PD decode heartbeat on /health without a generation probe (#51790)

Co-authored-by: weireweire <20922698+weireweire@users.noreply.github.com>

### [a0bd0c5](https://github.com/sgl-project/sglang/commit/a0bd0c56ad2d0cba425bc36d6a24598f14ec18e2)

- **作者**: esarafian
- **时间**: 2026-11-20T11:04:04Z
- **提交信息**: [Perf] speculative: batched top logprobs when every request asks the same k (#48208)

Signed-off-by: Elad Sarafian <esarafian@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Po-Han Huang <pohanh@nvidia.com>

### [ceb4ee8](https://github.com/sgl-project/sglang/commit/ceb4ee85c37d158b60d15f70b3d40d3717a09c0f)

- **作者**: esarafian
- **时间**: 2026-11-20T11:02:29Z
- **提交信息**: [Fix] http_server: skip the sglang launcher re-import in spawned uvicorn workers (#48247)

Signed-off-by: Elad Sarafian <esarafian@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Po-Han Huang <pohanh@nvidia.com>

### [4b6985c](https://github.com/sgl-project/sglang/commit/4b6985c614a70ebb4b21c720259909573884f2f2)

- **作者**: Anish Shanbhag
- **时间**: 2026-11-20T10:49:24Z
- **提交信息**: [Fix] model_loader: Split checkpoint prefetch among each node's own ranks (#51312)

Signed-off-by: Anish Shanbhag <52852612+anish-shanbhag@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Po-Han Huang <pohanh@nvidia.com>

### [eb49b87](https://github.com/sgl-project/sglang/commit/eb49b873a1665a43dae7ecb70b7b982a7001044f)

- **作者**: YAMY
- **时间**: 2026-11-20T10:47:59Z
- **提交信息**: [Fix] dsv41: Build MegaGate row masks inside the decoder replay-tail graph capture (#51479)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Po-Han Huang <pohanh@nvidia.com>

### [db420ed](https://github.com/sgl-project/sglang/commit/db420ed761c55d68e628f0aeb41af9b28948562e)

- **作者**: pllimax
- **时间**: 2026-11-20T10:44:25Z
- **提交信息**: [CI] npu: Lower the 3.5k/1.5k GPQA concurrency to fix pinned host OOM (#51765)

### [448efb1](https://github.com/sgl-project/sglang/commit/448efb13186f1ee8f3b0985900e25b1bee0cd508)

- **作者**: Ziqi Fan
- **时间**: 2026-11-20T10:34:55Z
- **提交信息**: [Feat] hicache: Forward request-scoped KV hints to storage backends (#51088)

Signed-off-by: Ziqi Fan <ziqif@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [ad96481](https://github.com/sgl-project/sglang/commit/ad96481482fe9d400195d12286f66a6359c56bb3)

- **作者**: Kevin Mi
- **时间**: 2026-11-20T10:24:30Z
- **提交信息**: [Fix] [AMD] kimi-k3: Drop the bundled TreeCore and its build-mode default (#51666)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [f5cc485](https://github.com/sgl-project/sglang/commit/f5cc4856acd653d5ba3a1aec60c1ad47cdea6765)

- **作者**: Michael
- **时间**: 2026-11-20T09:44:26Z
- **提交信息**: [CI] [AMD] schedule: Run the ROCm 7.2.0 and 7.2.4 lanes on weekends only (#49774)

### [4b02753](https://github.com/sgl-project/sglang/commit/4b02753381c948c42b7d8e0289bb72519f11e5f7)

- **作者**: Vedant V Jhaveri
- **时间**: 2026-11-20T09:29:18Z
- **提交信息**: [Feat] sampling: Add per-request SynthID Text watermarking (#45894)

Co-authored-by: Liangsheng Yin <hnyls2002@gmail.com>
Co-authored-by: hnyls2002 <lsyincs@gmail.com>

### [054c0d5](https://github.com/sgl-project/sglang/commit/054c0d556f30936af11eaa9b9fafad3aa8eeadb8)

- **作者**: Khoa Pham
- **时间**: 2026-11-20T09:28:52Z
- **提交信息**: [Perf] kimi-k3: Multicast collectives for LayerNorm sequence-parallel prefill (#51656)

### [d8eb518](https://github.com/sgl-project/sglang/commit/d8eb51846d74724efefcbbfbe98033372e54ee7a)

- **作者**: Trevor Morris
- **时间**: 2026-11-20T09:24:24Z
- **提交信息**: [Perf] scheduler: Add SGLANG_DISABLE_THP to turn off transparent huge pages (#51351)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: kpham-sgl <khoa.pham@radixark.ai>

### [242da74](https://github.com/sgl-project/sglang/commit/242da74ebf6a711d8f1946ba8437d9947fa2c1ad)

- **作者**: Trevor Morris
- **时间**: 2026-11-20T09:23:15Z
- **提交信息**: [Perf] disaggregation: Copy received aux data with one memcpy instead of a per-byte ctypes slice (#51343)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: kpham-sgl <khoa.pham@radixark.ai>

### [7894bdf](https://github.com/sgl-project/sglang/commit/7894bdf172df633b9770c06c07842eb92cb0c695)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-20T09:15:11Z
- **提交信息**: [Fix] weight-update: Keep fused-pair halves across chunked weight-update calls (#51661)

Co-authored-by: wzrd <floatlibai@gmail.com>
Co-authored-by: Elia Palme <elia.palme@cscs.ch>

### [28e5763](https://github.com/sgl-project/sglang/commit/28e576357488645398401d3badf44a24fc661cdf)

- **作者**: iridiumine
- **时间**: 2026-11-20T08:58:59Z
- **提交信息**: [Feat] [NPU] kimi-k3.1: Add model support and route DSA attention path on Ascend (#48420)

### [3b34d97](https://github.com/sgl-project/sglang/commit/3b34d97d9eca31f65b2a5cfeb5b7747cbc0cab54)

- **作者**: Aarne Talman
- **时间**: 2026-11-20T08:48:05Z
- **提交信息**: [Perf] [AMD] batch-invariant: Faster small-M launch for the segmented bf16 matmul on gfx950 (#49554)

Co-authored-by: Xinyi Song <xinyisong0111@gmail.com>

### [36d8221](https://github.com/sgl-project/sglang/commit/36d82211fe7374fd03ae3d91c20a8fddea5ad447)

- **作者**: Xinyuan Tong
- **时间**: 2026-11-20T08:38:40Z
- **提交信息**: [Fix] speculative: Read the current DP attention field in EAGLE draft (#51779)

### [561329a](https://github.com/sgl-project/sglang/commit/561329a0e6693a522369973b57453a664ff3bde1)

- **作者**: sherdavincl9
- **时间**: 2026-11-20T08:34:15Z
- **提交信息**: [Fix] muse-spark: Honor decrypted config in architecture probe (#49216)

### [6ccb37e](https://github.com/sgl-project/sglang/commit/6ccb37eb58b1d14b5997f3930425d910d3e0183a)

- **作者**: sherdavincl9
- **时间**: 2026-11-20T08:33:55Z
- **提交信息**: [Feat] [NPU] disaggregation: Support PD KV checksum (#41056)

### [f6726b4](https://github.com/sgl-project/sglang/commit/f6726b4caa0ea8215aa12acae3f00847cad4f97a)

- **作者**: Bingxu Chen
- **时间**: 2026-11-20T08:23:14Z
- **提交信息**: [Fix] [AMD] nixl: Bind AITER's HIP runtime before UCX hooks dlopen (#51525)

Co-authored-by: Claude <noreply@anthropic.com>

### [cc97c13](https://github.com/sgl-project/sglang/commit/cc97c13817e4544e23cfc8f1c7f6076c8b31fb07)

- **作者**: Mick
- **时间**: 2026-11-20T08:10:44Z
- **提交信息**: [Fix] diffusion: Keep FA4 for Blackwell sub-tile attention in the eager breaks of a graph replay (#51611)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Mythos 5.2 <noreply@anthropic.com>

### [0d81dbf](https://github.com/sgl-project/sglang/commit/0d81dbf3603506d9632f828d5116e7672cd1db31)

- **作者**: Mick
- **时间**: 2026-11-20T08:10:06Z
- **提交信息**: [Fix] diffusion: stop the worker profiler even if the HTTP profiler fails (#51598)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [28260f0](https://github.com/sgl-project/sglang/commit/28260f05fedba816b220a00e228d79a6907570d9)

- **作者**: Michael
- **时间**: 2026-11-20T08:09:26Z
- **提交信息**: [Fix] [AMD] unquant: Keep CPU inputs off the AITER GEMM path (#51079)

### [2a0869e](https://github.com/sgl-project/sglang/commit/2a0869ebcccc8b1a04198d0303fdabdc7bdceef5)

- **作者**: Lifan Shen
- **时间**: 2026-11-20T08:09:04Z
- **提交信息**: [Feat] logprob: Add token_ids_logprob_rows, token ids per scored input position (#51725)

Co-authored-by: hnyls2002 <lsyincs@gmail.com>

### [f694123](https://github.com/sgl-project/sglang/commit/f694123893483d728a4f93bb1c6a42d0dd9b9e9e)

- **作者**: Bingxu Chen
- **时间**: 2026-11-20T08:08:50Z
- **提交信息**: [Fix] [AMD] fp8-moe: Mark the AITER-shuffled per-tensor FP8 MoE weights is_shuffled (#51463)

Co-authored-by: Claude <noreply@anthropic.com>

### [d215bb3](https://github.com/sgl-project/sglang/commit/d215bb3b8c2007577e117777353c642744f0b90a)

- **作者**: Yuxingwang-intel
- **时间**: 2026-11-20T08:05:36Z
- **提交信息**: [Fix] [Intel] gemma4: Enable GPTQ INT4 inference on CPU (#47824)

Co-authored-by: Ma Mingfei <mingfei.ma@intel.com>

### [518dd30](https://github.com/sgl-project/sglang/commit/518dd30af21b946e053e04621fa8bf5d35d625c2)

- **作者**: Xinyuan Tong
- **时间**: 2026-11-20T07:48:30Z
- **提交信息**: [Doc] cookbook: Align Hy4 installation with the Docker guide (#51700)

### [0fff686](https://github.com/sgl-project/sglang/commit/0fff686ba40af8501d710ec77c808863b674858a)

- **作者**: yuhuang.89
- **时间**: 2026-11-20T07:47:16Z
- **提交信息**: [Fix] speculative: Prevent draft deadlock under DP attention when the DSA seed is missing (#41269)

Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [68c262b](https://github.com/sgl-project/sglang/commit/68c262b30617731b7e1761169aceb6b17feb918a)

- **作者**: qiaonan02
- **时间**: 2026-11-20T07:42:45Z
- **提交信息**: [Perf] [NVIDIA] fused_moe: Add H20-3e configs for GLM-5.3-Flash TP8/TP4 (#48314)

### [6e73258](https://github.com/sgl-project/sglang/commit/6e7325808610cc7c500fa8ae8bcfcb16aa941656)

- **作者**: Michael
- **时间**: 2026-11-20T07:39:49Z
- **提交信息**: [CI] [AMD] QSA: Fit MQA prefill kernels in gfx942 shared memory (#50886)

### [e183c41](https://github.com/sgl-project/sglang/commit/e183c415bdfc5995f6288b1651e1c320c6a74015)

- **作者**: Lee Nau
- **时间**: 2026-11-20T07:17:54Z
- **提交信息**: [CI] kernels: Widen the Marlin MoE GEMV-vs-GEMM bound to 1e-2 (#51624)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Po-Han Huang (NVIDIA) <53919306+nvpohanh@users.noreply.github.com>

### [789abb9](https://github.com/sgl-project/sglang/commit/789abb9be9d987e0b7fc950aa33f842f569168e5)

- **作者**: weireweire
- **时间**: 2026-11-20T07:08:30Z
- **提交信息**: [Perf] [NVIDIA] dspark: Stage draft DP-MoE token counts through persistent buffers (#47677)

Co-authored-by: weireweire <20922698+weireweire@users.noreply.github.com>
Co-authored-by: Po-Han Huang <pohanh@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [9866f0a](https://github.com/sgl-project/sglang/commit/9866f0a0c798ffb85da1122c09f8f135f66085d7)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-20T06:30:09Z
- **提交信息**: [Refactor] sampling: Add an algorithm-neutral watermark interface and move Gumbel behind it (#51719)

### [596c697](https://github.com/sgl-project/sglang/commit/596c697067870ac5f7b02e82ba3ff8a8dd55865a)

- **作者**: axx-ty911
- **时间**: 2026-11-20T06:23:49Z
- **提交信息**: [Doc] docs: Fix indentation, spelling and formatting issues (#50043)

### [843d27c](https://github.com/sgl-project/sglang/commit/843d27c9e297e0b921213889a78d6ec91abf41d1)

- **作者**: Kelon
- **时间**: 2026-11-20T06:12:31Z
- **提交信息**: [Feat] [NPU] DSV4.1: Support DeepSeek-V4.1 on Ascend A5 (#47660)

Co-authored-by: Aki Yang <kindradowers94500@outlook.com>

### [741d14c](https://github.com/sgl-project/sglang/commit/741d14cec1f8513576be7876d16552bdc8d86a16)

- **作者**: qiaonan02
- **时间**: 2026-11-20T06:04:16Z
- **提交信息**: [Fix] [NVIDIA] qwen3.5: Give text-only Qwen3.5 checkpoints the Qwen3 MoE family overrides (#49535)

Co-authored-by: Po-Han Huang <pohanh@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [b44ab81](https://github.com/sgl-project/sglang/commit/b44ab8128533f1321460fdeeb13b4a8216c7ecd9)

- **作者**: Shangming Cai
- **时间**: 2026-11-20T05:57:31Z
- **提交信息**: [CI] sgl-router: Restore the prebuilt Rust extensions before the e2e install (#51715)

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [99159c9](https://github.com/sgl-project/sglang/commit/99159c90503fe3a940ec519f9aae42d8632d8550)

- **作者**: Kangyan-Zhou
- **时间**: 2026-11-20T05:55:52Z
- **提交信息**: [Test] sgl-router: check DeepSeek image chats in processor_fixture_parity (#51711)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [9399f5f](https://github.com/sgl-project/sglang/commit/9399f5f4645eef43a5386b2074f2f80f77e982a3)

- **作者**: snadampal
- **时间**: 2026-11-20T05:26:06Z
- **提交信息**: [Feat] docker: Install AWS EFA in the main image; drop the EFA image variant (#48678)

Signed-off-by: Sunita Nadampalli <nadampal@amazon.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Erez Zarum <erezz@amazon.com>

### [d675c98](https://github.com/sgl-project/sglang/commit/d675c98bc76df951eec83196063cf2e546e0753d)

- **作者**: jobartlett
- **时间**: 2026-11-20T05:18:04Z
- **提交信息**: [Perf] inkling2: MegaMoE input for this rank's tokens only (#51595)

### [923a8b5](https://github.com/sgl-project/sglang/commit/923a8b5d1b373f6ad3fcc4278d8d25af08f00d24)

- **作者**: Rohit Kumar Singh
- **时间**: 2026-11-20T05:02:29Z
- **提交信息**: [Fix] [XPU] compressed-tensors: Support W8A8 int8 on XPU and quantize Whisper MLP linears. (#48353)

### [d96ae95](https://github.com/sgl-project/sglang/commit/d96ae9588b76c0e6e6a9b9187b716b6463e069b0)

- **作者**: Ma Mingfei
- **时间**: 2026-11-20T04:22:54Z
- **提交信息**: [Feat] [CPU] quantization: Add per-token FP8 quantization with AVX10.2 runtime dispatch (#51459)

### [b9e71d4](https://github.com/sgl-project/sglang/commit/b9e71d4c8bd2ff73574a0fb843bcfd8974e47a00)

- **作者**: zijiexia
- **时间**: 2026-11-20T04:03:24Z
- **提交信息**: [Perf] sampling: keep the fast top-p/top-k renorm under attention DP (#51363)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [98b6b7c](https://github.com/sgl-project/sglang/commit/98b6b7c646fe7932b44f7934496f7e17c5acd510)

- **作者**: Ke Bao
- **时间**: 2026-11-20T04:00:02Z
- **提交信息**: [Test] inkling2: Add a GB300 DSPARK e2e test (#51552)

### [c09ff83](https://github.com/sgl-project/sglang/commit/c09ff83ef4f2f085e6504e43180744bb4b371399)

- **作者**: Nader Al Awar
- **时间**: 2026-11-20T03:32:57Z
- **提交信息**: [Feat] profiler: Emit the forward step span as an NVTX range (#50140)

Co-authored-by: Po-Han Huang <pohanh@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [2e7bdf7](https://github.com/sgl-project/sglang/commit/2e7bdf77a2df45cab8fdede7d67930b07748c750)

- **作者**: esarafian
- **时间**: 2026-11-20T03:29:28Z
- **提交信息**: [Feat] model-loader: cap the bytes the multithreaded loader keeps in flight (#48227)

Signed-off-by: Elad Sarafian <esarafian@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Po-Han Huang <pohanh@nvidia.com>

### [a242c27](https://github.com/sgl-project/sglang/commit/a242c277e58d500beaaf5c631a1e5c84cc2b184f)

- **作者**: Shangming Cai
- **时间**: 2026-11-20T03:22:47Z
- **提交信息**: [Fix] sgl-router: Count a media tie-break once, at the worker level (#51671)

### [a3b7568](https://github.com/sgl-project/sglang/commit/a3b756844be58b8653902b366369b2d754c78d0f)

- **作者**: Xinyuan Tong
- **时间**: 2026-11-20T03:17:42Z
- **提交信息**: [Doc] cookbook: Add Hy4 (#51691)

### [41cd631](https://github.com/sgl-project/sglang/commit/41cd6318083bbc3973be49ee40f7237e60e6d47d)

- **作者**: Lee Nau
- **时间**: 2026-11-20T03:16:15Z
- **提交信息**: [CI] diffusion: Give h100-computable-d its own denoise references (#51594)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [401d0c7](https://github.com/sgl-project/sglang/commit/401d0c792902115eac9a2ae62e6e11ead80677f0)

- **作者**: Wayne Luo
- **时间**: 2026-11-20T03:11:33Z
- **提交信息**: [Refactor] [NPU] operators: Migrate sgl-kernel-npu calls to public operators entry points (#49995)

Co-authored-by: zejiluo <zejiluo7@gmail.com>
Co-authored-by: huangzhenyu <q_m_p@qq.com>
Co-authored-by: MatsueYu <hmzhu1999@gmail.com>
Co-authored-by: yuejiat0416 <yuejiat0416@163.com>
Co-authored-by: Wuhen <wh-duan@outlook.com>
Co-authored-by: Trae AI <trae@trae.ai>

### [f9c8371](https://github.com/sgl-project/sglang/commit/f9c83713e03b0bd1a76eed428866eef988ff5def)

- **作者**: Shuwen Wang
- **时间**: 2026-11-20T02:57:46Z
- **提交信息**: [Fix] linker: Read linker load-back from storage hits in the linker e2e tests (#51670)

### [23b2e67](https://github.com/sgl-project/sglang/commit/23b2e671c599331bb56a42da8b8119019a1a9f56)

- **作者**: Serge Panev
- **时间**: 2026-11-20T02:55:39Z
- **提交信息**: [Fix] hicache: Fail storage attach when the native hash extension cannot build (#50962)

Co-authored-by: Po-Han Huang <pohanh@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [35321ed](https://github.com/sgl-project/sglang/commit/35321ed0714bfd3c4a12669089fa28596d38664d)

- **作者**: Shri Rajamanikandan Vasudevan
- **时间**: 2026-11-20T02:54:38Z
- **提交信息**: [Fix] mem_cache: Set FP4 default in page-sharded DSA test mock (#51305)

Co-authored-by: Copilot App <223556219+Copilot@users.noreply.github.com>

### [f913bf9](https://github.com/sgl-project/sglang/commit/f913bf9aa1b6f9d428b3d521b72c42ed1d00292e)

- **作者**: pllimax
- **时间**: 2026-11-20T02:41:37Z
- **提交信息**: [CI] [NPU] workflow: Re-enable PR trigger and rerun only the failed nightly jobs (#51424)

### [307a616](https://github.com/sgl-project/sglang/commit/307a6164b207d4b5a2778d198f135a3d7c3ec286)

- **作者**: Shangming Cai
- **时间**: 2026-11-20T02:38:43Z
- **提交信息**: [Test] sgl-router: Run the e2e suite on 4-gpu-h100 with a PD dp-aware 2P+2D test (#51662)

### [ae69db4](https://github.com/sgl-project/sglang/commit/ae69db457eaa558e717335e8e3ae444cd800b8ba)

- **作者**: Shangming Cai
- **时间**: 2026-11-20T02:28:03Z
- **提交信息**: [Fix] sgl-router: match the engine's Responses summary events, argument coercion, and error type (#51637)

### [08f1009](https://github.com/sgl-project/sglang/commit/08f10090c76294a458c7b307e1ba97bd7ff1654e)

- **作者**: Rudy Mizrahi Celekli
- **时间**: 2026-11-20T01:46:55Z
- **提交信息**: [Feat] classify: Support independent multi-label probabilities (#51338)

Read the checkpoint's problem_type and apply elementwise sigmoid for multi-label classification while preserving softmax for other models. Document independent probabilities and top-scoring label compatibility.

### [6d35ff2](https://github.com/sgl-project/sglang/commit/6d35ff21d04b5bf845e99e71439cea1feef935e8)

- **作者**: Shangming Cai
- **时间**: 2026-11-20T01:33:28Z
- **提交信息**: [Feat] sgl-router: Route DeepSeek image chats by prefix cache (#48937)

### [cf9b03a](https://github.com/sgl-project/sglang/commit/cf9b03ab8265b9f7d06230379df67a3cfded8cb3)

- **作者**: Estrella-xx
- **时间**: 2026-11-20T01:30:06Z
- **提交信息**: [Feat] [NPU] mem-cache: support GLM DSA cache layer-split on Ascend (#48389)

### [a3d4b91](https://github.com/sgl-project/sglang/commit/a3d4b91d35d6aee80ad674450b72d92ed1090597)

- **作者**: Khoa Pham
- **时间**: 2026-11-20T01:27:15Z
- **提交信息**: [Feat] kimi-k3: Support --enable-layernorm-sp for sequence-parallel prefill (#51520)

Co-authored-by: Po-Han Huang <pohanh@nvidia.com>

### [9617d5f](https://github.com/sgl-project/sglang/commit/9617d5fa6af3b04b4fc46639ba54a20a3f829700)

- **作者**: Mick
- **时间**: 2026-11-20T01:06:31Z
- **提交信息**: [Doc] diffusion: Distinguish plain and pipelined Ulysses transports (#51649)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [3ee0803](https://github.com/sgl-project/sglang/commit/3ee08035aebe79431b80df0804aa4cf615d18b91)

- **作者**: Mick
- **时间**: 2026-11-20T01:06:10Z
- **提交信息**: [Doc] diffusion: Clarify FLUX.3 conditioning cache and VAE settings (#51652)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [9cca7c9](https://github.com/sgl-project/sglang/commit/9cca7c9fd2568b667adf64169b5a5b6b92357e8e)

- **作者**: Murthy L
- **时间**: 2026-11-20T00:55:38Z
- **提交信息**: [Feat] wan2.2-s2v: Add Wan2.2-S2V-14B speech-to-video with XPU support (port of #21609) (#43279)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Ma Mingfei <mingfei.ma@intel.com>

### [c532212](https://github.com/sgl-project/sglang/commit/c532212bbe6d4e0d7acef10296281c5e7569e689)

- **作者**: 黄孝君
- **时间**: 2026-11-20T00:49:56Z
- **提交信息**: [CI] [NPU] chore: Bump SGLang kernel NPU tag to 2026.11.0.post10 (#51536)

Co-authored-by: huangxiaojun15 <huangxiaojun15@users.noreply.github.com>

### [2510a8b](https://github.com/sgl-project/sglang/commit/2510a8b7bc2125454728738ee52f923c5d60a0d0)

- **作者**: Meng, Hengyu
- **时间**: 2026-11-20T00:44:11Z
- **提交信息**: [Feat] xpu: Consolidate simple XPU enablements (#50823)

Co-authored-by: Juan Muneton <102537701+jmunetong@users.noreply.github.com>
Co-authored-by: Yihao Wang <42559837+AgainstEntropy@users.noreply.github.com>
Co-authored-by: dayanandav <dayananda.vasantha.kumar@intel.com>
Co-authored-by: Cao E <e.cao@intel.com>
Co-authored-by: Han, Yan <yan.han@intel.com>
Co-authored-by: 源文雨 <41315874+fumiama@users.noreply.github.com>
Co-authored-by: Ranjan Debnath <ranjan.debnath@intel.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-11-21
**监控日期**: 2026-11-20
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1308
- **最后更新**: 2026-11-18T07:57:31Z

## 提交统计

- **昨日提交总数**: 7
- **提交者数量**: 2
- **主要提交者**: DefTruth, tridu33

## AI分析总结

## 提交记录分析：vipshop/cache-dit（昨日 7 个提交）

### 1. 主要更新类型
- **功能新增**：SVDQuant（SVDQ）Fused MLP / FP4 / FP8 W8A8 内核、门控激活变体、原生 MXFP4 量化后端、CLI 参数扩展
- **Bug修复与加固**：fused MLP 正确性加固（跳过 exact GELU 的静默误用、几何约束强制）
- **文档更新**：SVDQ fused MLP 覆盖路线图（P0/P1/P2 计划）
- **性能优化**：MXFP4 打包迁移至加速器设备，避免 CPU 慢速打包瓶颈

### 2. 关键变更点与项目方向的关系
- **量化矩阵补全**：新增原生 MXFP4（OCP E2M1 + E8M0）纯 PyTorch 后端，使非 Blackwell NVFP4 张量核心的加速器（如 PPU、NPU）也能获得 4-bit 量化能力，直接呼应 README 中"Quantization"与"CPU Offload"的定位。
- **SVDQ 内核融合深化**：从 FP4 扩展到 FP8 W8A8、支持 SiLU/tanh-GELU/GEGLU 等多种激活模式与 gate-first 排序，覆盖 FLUX.2/3 fused MLP 全链路，强化"Inference Engine"的高性能推理能力。
- **正确性与可观测性并重**：pass 层增加 guardrails/statistics，拒绝非标算子块，避免数值静默降级——对推理引擎的生产可信度至关重要。

### 3. 对项目的影响和潜在意义
- **硬件适用面扩大**：MXFP4 后端不依赖特定 CUDA 扩展（`is_supported` 不再要求 SVDQ ext），结合平台抽象（`current_platform`）覆盖 NPU/PPU，为国产及非 NVIDIA 硬件落地铺路。
- **实测收益显著**：FLUX.2-klein-9B 上 mxfp4 峰值显存 -34%（34.73→22.80 GiB），PSNR 20.3 dB；打包设备优化将 FLUX.1-dev 的 ~11 分钟打包时间大幅压缩，端到端可用性明显提升。
- **工程质量提升**：配套 CLI 快捷参数、roundtrip 测试、e2e 验证，形成"内核→配置→CLI→测试"闭环。

### 4. 值得关注的技术点
- **Triton `tl.dot_scaled(e2m1)` 快速 GEMM 已验证可编译**，当前为 fused-dequant 计算路径，后续有望进一步提速 MXFP4 推理。
- **E8M0 group-of-32 RCEIL scales** 严格遵循 OCP MX 规范，`mxfp4_block_size` 经 spec 校验，兼容性有保障。
- **exact GELU 不再静默回退到 tanh qout 内核**——这种"宁可拒绝不可错算"的设计对量化推理的数值保真度很关键。
- fused MLP pass 对 **TP、compile、CUDA Graph、PTQ roundtrip** 的多维度覆盖，说明项目已在复杂并行+编译场景做系统验证。

### 5. 结合 README 背景对项目发展的整体影响
cache-dit 定位为"带 Cache、并行、量化、CPU Offload 的 PyTorch 原生 DiT 推理引擎"。昨日提交集中发力**量化（Quantization）与内核融合**两条主线：MXFP4 补齐了低比特量化在通用加速器上的短板，SVDQ fused MLP 持续挖掘 NVFP4/FP8 的 GEMM 融合上限。二者共同指向 README 中的核心价值——在多样化硬件上实现更省显存、更快速的 DiT 推理。同时，路线图文档与多层级测试的引入，表明项目正从"功能堆叠"走向"体系化收敛"，为后续 Triton 快速 GEMM、更多激活模式的 P0/P1 路线图奠定了可扩展的架构基础，对推动 DiT 大模型在生产环境的低成本部署具有直接意义。

## 详细提交记录

### [fdf4270](https://github.com/vipshop/cache-dit/commit/fdf42708071d815d399b311c7e9d4c0c41b568dd)

- **作者**: DefTruth
- **时间**: 2026-11-20T13:55:10Z
- **提交信息**: feat(svdq): add fused SVDQuant-FP8 W8A8 kernels (#1384)

### [b311070](https://github.com/vipshop/cache-dit/commit/b31107040293b794e659e5c75d0dd8bcb254f643)

- **作者**: DefTruth
- **时间**: 2026-11-20T07:17:45Z
- **提交信息**: feat(svdq): support gated activation variants (#1381)

Add native/CuTe SiLU, tanh-GELU, and exact-GELU producer modes plus gate-first ordering; enable GEGLU and standalone FLUX.2/3 fused MLP passes with producer, chain, and e2e validation.

### [ea9d0f5](https://github.com/vipshop/cache-dit/commit/ea9d0f5b2352ab384e49f3308c55f06d2f3ffe43)

- **作者**: DefTruth
- **时间**: 2026-11-20T05:18:49Z
- **提交信息**: feat(svdq): expand fused MLP pass coverage (#1379)

Support standalone gated aliases and nested GELU chains, preserve w1/w3 operand direction, reject non-SiLU and non-standalone blocks, and cover native/CuTe numerics.

### [45a2aae](https://github.com/vipshop/cache-dit/commit/45a2aae4081466ae392ae96a6b04064bb63c1d91)

- **作者**: tridu33
- **时间**: 2026-11-20T04:45:36Z
- **提交信息**: feat(quantization): add native MXFP4 (OCP E2M1 + E8M0) support (#1367)

* feat(quantization): add native MXFP4 (OCP E2M1 + E8M0) support

Add cache-dit's own MXFP4 backend so MXFP4 works on accelerators without
Blackwell-class NVFP4 tensor cores and without relying on the platform's
BlockWise-1x32 torch._scaled_mm path (broken on some backends):

- new package cache_dit/quantization/mxfp4: pure-PyTorch E2M1 packing with
  E8M0 group-of-32 scales (RCEIL), MXFP4Linear, and quantize_mxfp4 entry that
  honors regional_quantize/repeated_blocks/exclude_layers
- QuantizeConfig: mxfp4/mxfp4_weight_only quant types resolve to the native
  CACHE_DIT backend, new mxfp4_block_size (32, spec-validated), is_mxfp4()
- QuantizeBackend.is_supported(CACHE_DIT) no longer requires the SVDQ CUDA ext
- dispatch: route mxfp4* to quantize_mxfp4
- CLI: --mxfp4 / --mxfp4-weight-only / --mxfp4-wo shortcuts + quantize-type choices
- tests/quantization/test_mxfp4.py: config/CLI, quant-dequant roundtrip,
  dispatch-level Linear replacement

Measured on FLUX.2-klein-9B (PPU, 50 steps, 1024^2, warmup 1 + repeat 1):
  bf16+compile 14.54s/34.73GiB, mxfp4+compile 15.79s/22.80GiB (peak -34%),
  PSNR vs bf16 20.3 dB.
v1 compute path is fused-dequant; a Triton tl.dot_scaled(e2m1) fast GEMM is
the planned follow-up (verified compilable on this backend).

* perf(mxfp4): pack weights on the accelerator when one is available

MXFP4 packing is pure element-wise math, yet it ran on whatever device the
module sat on. Quantization happens while the transformer is still CPU-resident,
so FLUX.1-dev spent ~11 min packing 494 layers before inference could start.

- QuantizeConfig.mxfp4_quantize_device ("auto"/"cpu"/"cuda", default "auto")
  plus --mxfp4-quantize-device: "auto" packs on the current accelerator when
  available (via cache_dit.platforms.current_platform, so NPU is covered too)
  and falls back to the weight device otherwise. Packed payload/scales are
  always copied back to the original device, so quantization never moves a
  module.
- Move first, cast second: the weight travels in its original dtype and the
  fp32 promotion happens on the packing device. Casting a CPU-resident
  4096x4096 weight before the copy cost ~45 ms per layer.
- Log the effective packing device; forward the mxfp4 fields through
  components_to_quantize.
- Tests: device resolution, config/CLI validation, component passthrough,
  accelerator-vs-CPU bit-identical packing, and a spy asserting the config
  field reaches the packing math (the previous assertion also held when the
  field was silently ignored).

FLUX.1-dev 1024^2, 28 steps, seed 0, RTX PRO 5000:
  init 649.0s -> 7.1s (91x), inference 37.04s -> 36.93s, peak 17.76 -> 17.75 GiB,
  PNG md5 unchanged. 80/80 real layers bit-identical across devices. Already
  GPU-resident model (22.17 GiB): 2.45s, +2.11 GiB peak.

* fix(mxfp4): address the PR #1367 review findings

- Tie-breaking: bucketize returns the lower code on an exact midpoint, so the
  even-rounding bump is idx + 1, not idx - 1. Values like 0.75/1.75/3.5 now land
  on 1.0/2.0/4.0 instead of one code below; both signs are covered by tests.
- Layer selection mirrors the native FP8 path: filter_fn is honored, exclusion
  wins over it, regional scoping follows _repeated_blocks, non-2D and DTensor
  weights are skipped with a reason, and a run that packs nothing raises instead
  of returning an unquantized module.
- observer=... is now attached (references captured before replacement, hooks
  installed after), and keep_refs_on_gpu follows the layer's own device (packed
  weights included) instead of a hardcoded cuda.
- MXFP4Linear._apply keeps the fp4/e8m0 payload verbatim across dtype casts and
  restores it if the transform raises, so .half()/.to(dtype) no longer crash.
- is_supported() now takes the quant type: MXFP4 checks the MX dtypes while
  native FP8/NVFP4/SVDQ keep the _C_ops gate; SVDQ FlashInfer/cute runtimes,
  which ship their own kernels, are no longer gated on the extension.
- Only mxfp4_weight_only remains a public type (activations are not quantized,
  unlike nvfp4); --mxfp4 stays as a CLI alias and the choices/docs follow.
- Divisibility relaxed to in_features % 32 == 0 (32/96/160 are legal MX shapes).
- Docs: MXFP4 weight-only section with requirements, the device switch and the
  measured matrix plus its compile/repeat floors; the package no longer claims
  a checkpoint path. Added bench/kernels/bench_mxfp4.py for the pack and forward
  numbers quoted by the docs.

FLUX.1-dev 1024^2 28 steps (fixed noise, RTX PRO 5000): eager 36.39s / compile
15.38s at 17.75 GiB vs bf16 16.99s / 14.88s at 33.82 GiB; PSNR 16.25 dB eager and
16.01 dB compiled against a 27.11 dB compile-vs-eager floor, repeat runs are
bit-identical. Packing 494 layers takes 7.1s instead of 649s.

---------

Co-authored-by: DefTruth <qiustudent_r@163.com>

### [d57710a](https://github.com/vipshop/cache-dit/commit/d57710aa9c5ae973203d06674838a4ddc3900628)

- **作者**: DefTruth
- **时间**: 2026-11-20T04:35:08Z
- **提交信息**: fix(svdq): harden fused MLP pass correctness (#1377)

Skip exact GELU instead of silently using the tanh qout kernel, enforce runtime-specific geometry, add pass guardrails/statistics, and cover native/CuTe, TP, compile, CUDA Graph, and PTQ roundtrips.

### [de4e366](https://github.com/vipshop/cache-dit/commit/de4e36669371a92a783e3d74a3faaf77fdafd2d7)

- **作者**: DefTruth
- **时间**: 2026-11-20T03:51:55Z
- **提交信息**: docs: add SVDQ fused MLP coverage roadmap (#1375)

Record the SVDQ NVFP4 fused MLP pattern inventory and P0/P1/P2 follow-up plan in the cache-dit custom-kernel skill.

### [159d141](https://github.com/vipshop/cache-dit/commit/159d14146bde6c5be3eebfbba06a929af4872328)

- **作者**: DefTruth
- **时间**: 2026-11-20T03:26:17Z
- **提交信息**: feat: add fused MLP support for native FP4 (#1373)

Add native NVFP4 GELU/SwiGLU fusion with Python and CLI integration, regression coverage, benchmarks, and FLUX validation.

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-11-21
**监控日期**: 2026-11-20
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 97290
- **最后更新**: 2026-11-21T03:12:42Z

## 提交统计

- **昨日提交总数**: 122
- **提交者数量**: 85
- **主要提交者**: Brandon Pelfrey, Bugen Zhao, Lantao Jin

## AI分析总结

# vLLM 昨日提交总结（122 条）

## 一、主要更新类型

昨日提交以 **Bug 修复占比最高**，涉及 ROCm、Kimi-K2.5、HiSparse、前端、内核等多个模块；其次是 **性能优化**（集中于 ROCm/AITER 内核融合与调度）、**Rust 前端完善**（约 14 条对齐修复）、**CI/测试稳定性** 改进，以及少量功能新增（Rust 前端、Responses API、Inkling/HY4/ShieldGemma 等模型）、安全加固与文档重构。

## 二、关键变更点与项目方向的关系

- **ROCm 生态持续深耕**：约 20 条提交围绕 gfx942/gfx950 的 AITER 内核、MoE 后端、注意力融合，加上 gfx1151 W4A16、gfx11 W4A8 MoE、GDN 融合等，体现 vLLM 跨平台目标，正缩小与 CUDA 后端差距。
- **模型支持扩展**：Inkling 2 Mini（1M 上下文单卡方案）、ShieldGemma 2、HY4 注册、DeepSeek-V3.2 NVFP4 修复、Kimi-K2.5 视频处理修复，持续扩充可服务模型版图。
- **上游集成策略**：Inkling、DeepseekV32、Falcon/RADIO 改用 HuggingFace Transformers 上游配置，减少重复维护。
- **Rust 前端补齐**：修复错误报告、chat 模板、prompt 校验、LoRA 卸载、工具 strict 模式等，目标是达到可替代旧 Python 服务的 API 兼容成熟度。
- **MoE 与量化主线**：Quark INT8 迁移到 MoE oracle、NVFP4→MXFP4 在线转换、E8M0 scale 保留、ModelOpt INT8 权重预处理，支撑低比特高效推理。
- **安全与健壮性**：限制批量对话数、校验 kv_transfer_params、Responses API 输入校验、拒绝 ICNS 解码、torchaudio 内核边界校验，提升多租户生产可靠性。
- **启动与缓存**：模型检查点预取到页缓存、VMM IPC 预加载、Fast Start 与权重缓存指纹修复，呼应低成本快速启动目标。

## 三、影响与潜在意义

- ROCm 密集投入使 AMD MI300 系列从"可用"走向"优化良好"，降低 CUDA 锁定。
- 安全修复批次为 vLLM 进入企业级部署扫清障碍。
- Intel XPU 测试扩展（Triton-only 的 ReplaySSM/SSU、Hybrid SSM + NixlConnector PD 分离前缀缓存 CI）巩固多硬件差异化竞争力，并验证前沿架构组合。
- CI 治理（镜像重试、测试隔离、B200 DeepEP 移 nightly、BMG 迁 k8s）改善贡献者体验，但也提示测试矩阵膨胀的维护负担。

## 四、值得关注的技术点

1. **细粒度内核融合**：k_out 反量化、FP8 查询量化折叠进 QK-norm+RoPE+KV-cache 融合路径（#67550）。
2. **批不变性**：SM89 int8 CUTLASS 修复、MIOpen split-K 规避、VLLM_BATCH_INVARIANT，满足确定性推理需求。
3. **投机解码优化**：FlashInfer XQA ragged draft mask 去除 GPU↔CPU 同步；EAGLE 块丢弃移除；Speculator 行为改为从 SpeculatorConfig 派生（#68798），配置驱动替代方法检查。
4. **长上下文基础设施**：KV connector/NIXL 兼容性哈希、Engram 池跨引擎拆分、DSv4.1 Engram 分池。
5. **架构简化**：移除 mamba_cache_mode、块尺寸统一、流水线 hidden states 保留、fx tracer 支持。
6. **RL 链路**：权重更新默认直载（VLLM_RELOAD_MODE=auto）。
7. **AI 辅助开发常态化**：大量提交带 Claude、Cursor、Codex 共同署名，社区已深度采用 AI 辅助工作流。

## 五、对项目发展的意义

这批提交显示 vLLM 正处于"横向扩展 + 纵向打磨"阶段：横向覆盖更多硬件（ROCm/XPU）、更多模型、更多 API 形态；纵向深化性能优化与生产级可靠性。对照"Easy, fast, and cheap"愿景，Rust 前端修复服务"Easy"，ROCm/XPU/量化优化服务"Fast and cheap"，CI 与安全投入保障工程可持续性。项目正从功能扩张转向成熟度提升与生态均衡，为以 Rust 前端为核心的服务架构奠定基础，并通过持续的测试与安全投入在企业级部署中建立可靠性口碑，巩固其作为开源 LLM 推理事实标准的地位。

## 详细提交记录

### [8f8aee6](https://github.com/vllm-project/vllm/commit/8f8aee61bd50c8b23ccf50d17b94413f3220782a)

- **作者**: Pham Binh
- **时间**: 2026-11-20T23:55:24Z
- **提交信息**: [Bugfix][ROCm] Apply the e4m3fnuz KV-scale factor for compressed-tensors (#66586)

Signed-off-by: Pham Binh <194774975+phambinhfin@users.noreply.github.com>
Co-authored-by: Pham Binh <194774975+phambinhfin@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [7bce843](https://github.com/vllm-project/vllm/commit/7bce843a08fd3119766cd73d346bce481ede2544)

- **作者**: akii96
- **时间**: 2026-11-20T23:47:22Z
- **提交信息**: [ROCm][MoE] Add AITER Triton MXFP8 MoE backend for gfx942 (#61214)

Signed-off-by: Aakif Nawaz <aakif.nawaz@amd.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [491e221](https://github.com/vllm-project/vllm/commit/491e221fb27b7d6d85d7a7c715c7fff4eb784738)

- **作者**: YAASHU DAVE
- **时间**: 2026-11-20T23:12:48Z
- **提交信息**: [Bugfix][ROCm] benchmark_moe: keep HIP_VISIBLE_DEVICES for Ray (#65935)

Signed-off-by: Yaashu Dave <daveyaashu2411@gmail.com>
Co-authored-by: Giuseppe Grossi <272274891+giuseppegrossi@users.noreply.github.com>

### [9740f70](https://github.com/vllm-project/vllm/commit/9740f70413d321c3ebbaeab1a376405662836d49)

- **作者**: Anish Shanbhag
- **时间**: 2026-11-20T22:52:33Z
- **提交信息**: [Bugfix][Model Loader] Prefetch the whole checkpoint into every node's page cache (#68351)

Signed-off-by: Anish Shanbhag <52852612+anish-shanbhag@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Artem Perevedentsev <aperevedents@nvidia.com>

### [c98006e](https://github.com/vllm-project/vllm/commit/c98006ee675c605dc99278c8898dc512ec69bb79)

- **作者**: Mikko Tukiainen
- **时间**: 2026-11-20T22:46:49Z
- **提交信息**: [ROCm][Perf][Muse Spark] Run the pooler and unpooler through the default ROCm GEMM dispatch on gfx942 and gfx950 (#63725)

Signed-off-by: Mikko Tukiainen <Mikko.Tukiainen@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [920e4f4](https://github.com/vllm-project/vllm/commit/920e4f4e5921c86feecedbd77ff05560b5426e80)

- **作者**: Mehdi Ghanimifard
- **时间**: 2026-11-20T22:35:14Z
- **提交信息**: [ROCm] Warm the AITER FA extend kernels from the attention backend (#68012)

Signed-off-by: Mehdi Ghanimifard <mehdi.ghanimifard@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [2742374](https://github.com/vllm-project/vllm/commit/2742374c18c4067742e9793f3fe677d628740f47)

- **作者**: Mikko Tukiainen
- **时间**: 2026-11-20T22:32:35Z
- **提交信息**: [ROCm][Bugfix] Keep non-float all-reduces off AITER custom all-reduce (#60839)

Signed-off-by: Mikko Tukiainen <Mikko.Tukiainen@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Simon Danielsson <70206058+simondanielsson@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [4d9cbc9](https://github.com/vllm-project/vllm/commit/4d9cbc9a8c9809999a5a5e2475507c3ef14f5295)

- **作者**: Dmitry Tokarev
- **时间**: 2026-11-20T22:19:04Z
- **提交信息**: [Doc] Make CUDA 13 the default in the GPU install guide (#67572)

Signed-off-by: Dmitry Tokarev <dtokarev@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [77a2c15](https://github.com/vllm-project/vllm/commit/77a2c1512c0d6287dbd6d3280f9168268f564b66)

- **作者**: Sheral Kumar
- **时间**: 2026-11-20T22:05:57Z
- **提交信息**: Revert "[ROCm][CI] Retarget `mi300_dpx` jobs to `mi300_1` queue temporarily" (#68987)

Signed-off-by: Sheral Kumar <shekumar@amd.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [252a38b](https://github.com/vllm-project/vllm/commit/252a38bc953f273b390912d91525280c8686d615)

- **作者**: Ahsan Saghir
- **时间**: 2026-11-20T21:58:53Z
- **提交信息**: [ROCm][CI] Don't run every AMD step on files only the CUDA build reads (#68528)

Signed-off-by: Ahsan Saghir <ahsaghir@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [b13eb01](https://github.com/vllm-project/vllm/commit/b13eb01d790a760254a66de52dcfc8253d3e13b1)

- **作者**: Woosuk Kwon
- **时间**: 2026-11-20T21:43:52Z
- **提交信息**: [Recipe] Inkling 2 Mini: serve the full 1M context on one GPU (#69039)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [77c887b](https://github.com/vllm-project/vllm/commit/77c887b4d68c49a8b15e0aee38cb45a5b4e8c0fc)

- **作者**: Mirza Halilčević
- **时间**: 2026-11-20T20:40:30Z
- **提交信息**: [ROCm][Bugfix] Avoid MIOpen's split-K conv solver in batch-invariant mode (#69025)

Signed-off-by: Mirza Halilcevic <mirza.halilcevic@amd.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [e82b7fc](https://github.com/vllm-project/vllm/commit/e82b7fca7e48ce4355795fee16affb0aacc72e2c)

- **作者**: alberto
- **时间**: 2026-11-20T20:36:35Z
- **提交信息**: [Rust Frontend] Support `additional_tools` input items in the Responses API (#69019)

Signed-off-by: Alberto Perdomo <aperdomo@redhat.com>
Co-authored-by: Flora Feng <4florafeng@gmail.com>

### [ab8b98e](https://github.com/vllm-project/vllm/commit/ab8b98eb1bde37d0e2b0ebdd6cfc56f57e541ab8)

- **作者**: simon-veitner-redhat
- **时间**: 2026-11-20T20:22:31Z
- **提交信息**: [Bugfix][Frontend] Read /v1/decisions predicates like /v1/systemone noul questions (#68917)

Signed-off-by: Simon Veitner <sveitner@redhat.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [d53154d](https://github.com/vllm-project/vllm/commit/d53154d9f354ebd4a4deb4fd81935db0e266c5fc)

- **作者**: Woosuk Kwon
- **时间**: 2026-11-20T20:19:09Z
- **提交信息**: [Recipe] Add Inkling 2 Mini (#69027)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [d7af009](https://github.com/vllm-project/vllm/commit/d7af009af1281df96b40726e51578907c6b2b5b0)

- **作者**: Brandon Pelfrey
- **时间**: 2026-11-20T20:13:11Z
- **提交信息**: [Build] Relax PyNvVideoCodec pin to >=2.2.4 to resolve CVEs (#68991)

Signed-off-by: Brandon Pelfrey <bpelfrey@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [1934f18](https://github.com/vllm-project/vllm/commit/1934f186eddbfde146dde745639241312fb92c8b)

- **作者**: Wentao Ye
- **时间**: 2026-11-20T20:09:09Z
- **提交信息**: [Refactor] Use `FULL` instead of `NONE` during MR V2 full-graph capture (#68006)

Signed-off-by: yewentao256 <zhyanwentao@126.com>
Signed-off-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: Lucas Wilkinson <LucasWilkinson@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [8f8f6c8](https://github.com/vllm-project/vllm/commit/8f8f6c8fc85de978555bf705ac21ec7580ded88f)

- **作者**: Harshal Janjani
- **时间**: 2026-11-20T20:06:22Z
- **提交信息**: feat: Add Omni support to the Transformers backend (#60648)

Signed-off-by: Harshal Janjani <harshaljanjani@gmail.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [56762eb](https://github.com/vllm-project/vllm/commit/56762eb614e864880deab363875c4b01a873678d)

- **作者**: Nick Hill
- **时间**: 2026-11-20T20:03:57Z
- **提交信息**: [Spec Decode] Derive speculator behavior from SpeculatorConfig instead of method checks (#68798)

Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [b492a09](https://github.com/vllm-project/vllm/commit/b492a09c10118f43bfaf5ff75f17fa10fe86e0a6)

- **作者**: Matthew Bonanni
- **时间**: 2026-11-20T19:20:48Z
- **提交信息**: [HiSparse] Store one copy of the offloaded indexer across TP ranks (#68785)

Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [0aa2bb1](https://github.com/vllm-project/vllm/commit/0aa2bb19496d9252c0dd7f8d1c0d073fc634d471)

- **作者**: Jack Hu
- **时间**: 2026-11-20T18:58:54Z
- **提交信息**: [ROCm][Model][Perf] Fold the k_out dequant and fp8 query quant into the QK-norm+RoPE+KV-cache fusion for ROCM_AITER_FA, ROCM_ATTN, and ROCM_AITER_UNIFIED_ATTN (#67550)

Signed-off-by: Jack Hu <Jack.Hu@amd.com>
Signed-off-by: Jack Hu <jack.hu@amd.com>
Co-authored-by: Simon Danielsson <70206058+simondanielsson@users.noreply.github.com>

### [c78f57f](https://github.com/vllm-project/vllm/commit/c78f57f74599cb3dc0a0bc2848d9b8b0dea3be6e)

- **作者**: Harry Mellor
- **时间**: 2026-11-20T18:33:35Z
- **提交信息**: [Model] Use upstream Transformers configs for Inkling (#68975)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [664dfcd](https://github.com/vllm-project/vllm/commit/664dfcd4f8a50cfa9960612187d14ebaff446ebf)

- **作者**: Andreas Karatzas
- **时间**: 2026-11-20T18:17:15Z
- **提交信息**: [ROCm][CI] Give apt a longer retry window in ROCm image builds (#68527)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Rohan Potdar <rohan.potdar@amd.com>

### [0e1d945](https://github.com/vllm-project/vllm/commit/0e1d945bac0d646b0d5ae0933d36c5583c6d9a36)

- **作者**: Tobias G.
- **时间**: 2026-11-20T18:08:37Z
- **提交信息**: [Bugfix][HiSparse] Emit the prefill staging plan without a dense prefill backend (#68967)

Signed-off-by: HansG89 <17526698+HansG89@users.noreply.github.com>

### [95d8de7](https://github.com/vllm-project/vllm/commit/95d8de77c24e5b6d1976ec8b9efd0a9a10de6a4b)

- **作者**: alberto
- **时间**: 2026-11-20T18:05:56Z
- **提交信息**: [Bugfix][Frontend] Hoist `additional_tools` input items into Responses tools (#68781)

Signed-off-by: Alberto Perdomo <aperdomo@redhat.com>
Co-authored-by: Robert Shaw <114415538+robertgshaw2-redhat@users.noreply.github.com>

### [673618e](https://github.com/vllm-project/vllm/commit/673618e0a439caec4d23b1ad89d4b77f57c21f6b)

- **作者**: Julien Denize
- **时间**: 2026-11-20T17:52:10Z
- **提交信息**: [Model] Voxtral: drop the unused model field from TranscriptionRequest (#68702)

Signed-off-by: juliendenize <40604584+juliendenize@users.noreply.github.com>

### [e2bab26](https://github.com/vllm-project/vllm/commit/e2bab26e51ad4b40c1fbb70f76ab8d7d4efa3b87)

- **作者**: Martin Hickey
- **时间**: 2026-11-20T17:15:07Z
- **提交信息**: [Bugfix] Reject stop strings when the generate server has no tokenizer (#68989)

Signed-off-by: Martin Hickey <martin.hickey@ie.ibm.com>

### [022759a](https://github.com/vllm-project/vllm/commit/022759ad1cac5ac2de1db4cf9be71aff2e848c8c)

- **作者**: Stefano Castagnetta
- **时间**: 2026-11-20T16:58:24Z
- **提交信息**: [Docs] Add stecasta to reviewers (#68981)

Signed-off-by: Stefano Castagnetta <scastagnetta@nvidia.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [3ba0879](https://github.com/vllm-project/vllm/commit/3ba087987fdc7d9ca3099d2ed6cf4bee582ea133)

- **作者**: Andreas Karatzas
- **时间**: 2026-11-20T16:50:38Z
- **提交信息**: [Bugfix][ROCm] Give EngineCore the cleanup grace window when shutdown has no budget (#68554)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [bb78939](https://github.com/vllm-project/vllm/commit/bb7893912e0f72e1c957e7a7caac957b0ed26d65)

- **作者**: Andreas Karatzas
- **时间**: 2026-11-20T16:48:18Z
- **提交信息**: [ROCm][CI] Retry ROCm image builds when a package mirror still fails after apt's retries (#68829)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [9c171c0](https://github.com/vllm-project/vllm/commit/9c171c0e6dbdf4829db137139ef566b1413c6b2d)

- **作者**: bogdan-petkovic
- **时间**: 2026-11-20T16:19:39Z
- **提交信息**: [ROCm][CI] Check the MLA W_UV kernel through a Triton launch hook (#68965)

Signed-off-by: bogdan-petkovic <bpetkovi@amd.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [311bf8a](https://github.com/vllm-project/vllm/commit/311bf8a38fa96356f8f30f402fab9e945739fdfd)

- **作者**: stefankoncarevic
- **时间**: 2026-11-20T16:17:21Z
- **提交信息**: [CI] Warm the Triton autotune cache in the MTP sharded-sampling test (#68986)

Signed-off-by: Stefan Koncarevic <Stefan.Koncarevic@amd.com>

### [339d0bd](https://github.com/vllm-project/vllm/commit/339d0bd69d520df75957b1f13efb42f717ee169c)

- **作者**: Matthias Gehre
- **时间**: 2026-11-20T16:16:43Z
- **提交信息**: [Bugfix] Support strided weights in sharded state saving (#61432)

Signed-off-by: Matthias Gehre <matthias.gehre@amd.com>
Co-authored-by: Douglas Lehr <91553416+dllehr-amd@users.noreply.github.com>

### [405a6ce](https://github.com/vllm-project/vllm/commit/405a6ce941cbdaf8dc8c7f4a64857b48c4694ac0)

- **作者**: sean
- **时间**: 2026-11-20T16:16:07Z
- **提交信息**: [Bugfix][Kimi-K2.5] Keep one vision_chunk UUID per item when rebuilding (#68738)

Signed-off-by: Sean Bangalore <bsudarshan@outlook.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [3da69ba](https://github.com/vllm-project/vllm/commit/3da69ba23fd5a042119dcae85399f7291e4c69f6)

- **作者**: sean
- **时间**: 2026-11-20T16:15:22Z
- **提交信息**: [Bugfix][Kimi-K2.5] Cast ViT time_weight to the pos-emb dtype for video chunks (#68737)

Signed-off-by: Sean Bangalore <bsudarshan@outlook.com>
Signed-off-by: sean <bsudarshan@outlook.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: cjackal <44624812+cjackal@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [1f41d0f](https://github.com/vllm-project/vllm/commit/1f41d0fb3145e0626c5e20d115df5adf7ee32906)

- **作者**: Andreas Karatzas
- **时间**: 2026-11-20T16:07:56Z
- **提交信息**: [ROCm][CI] Run test_preprocess_error_handling in its own AMD step (#68571)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [f79838e](https://github.com/vllm-project/vllm/commit/f79838e3636e845d5e0b2958394b74c857033c10)

- **作者**: maqiao.mq
- **时间**: 2026-11-20T16:00:10Z
- **提交信息**: [Frontend] Support cross-machine snapshot (step 1: portable attachments) (#61544)

Signed-off-by: Qiao Ma <mqaio@linux.alibaba.com>
Signed-off-by: Yunong He <ali_yuno@linux.alibaba.com>
Co-authored-by: Yunong He <ali_yuno@linux.alibaba.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [6875771](https://github.com/vllm-project/vllm/commit/68757716931c707bb2db59eb755a735ac9ca74fc)

- **作者**: Shashvat Singh
- **时间**: 2026-11-20T15:55:17Z
- **提交信息**: [Misc] Remove --disable-cascade-attn past its removal version (#68789)

Signed-off-by: sh4shv4t <shashvat.k.singh.16@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [3302deb](https://github.com/vllm-project/vllm/commit/3302deb9b589b86686255e3ea51654f0facd8b5b)

- **作者**: Mai Hoàng Đức
- **时间**: 2026-11-20T15:49:48Z
- **提交信息**: [Bugfix][Kernel] Fix int8 CUTLASS scaled_mm on SM89 with VLLM_BATCH_INVARIANT=1 (#67687)

Signed-off-by: Mazukiri <80498645+Mazukiri@users.noreply.github.com>
Signed-off-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [0d93fd5](https://github.com/vllm-project/vllm/commit/0d93fd5e17ee630a032050b9cb9366a1cd1bec35)

- **作者**: Tony Lin
- **时间**: 2026-11-20T14:56:21Z
- **提交信息**: [CI][XPU] Fix Engram peer group test capability (#68881)

Signed-off-by: Tony Lin <tony.lin@intel.com>

### [c334a49](https://github.com/vllm-project/vllm/commit/c334a4959a2d76ba4d4a7b12ee30ff0438989b83)

- **作者**: Harry Mellor
- **时间**: 2026-11-20T14:52:25Z
- **提交信息**: [Model] Use upstream DeepseekV32Config and fix DeepSeek-V3.2 NVFP4 loading (#68948)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [8e45c45](https://github.com/vllm-project/vllm/commit/8e45c458f619dbabff879c0f53c58fd9f296e983)

- **作者**: Cheng Jiang
- **时间**: 2026-11-20T14:09:09Z
- **提交信息**: [Bugfix] Fix hy-v4 mxfp4dfly, data-parallel and cudagraph_mm_encoder, reasoning_parser error (#68689)

Signed-off-by: thisjiang <thisjiang@qq.com>
Co-authored-by: Jee Jee Li <pandaleefree@gmail.com>

### [6c6e159](https://github.com/vllm-project/vllm/commit/6c6e159aa967b538385e3c501cc293c882a0606b)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-11-20T14:01:43Z
- **提交信息**: [Security] Bound the number of batch chat conversations (#68904)

Signed-off-by: Juan Pérez de Algaba <jperezde@redhat.com>
Co-authored-by: Codex <codex@openai.com>

### [6abe321](https://github.com/vllm-project/vllm/commit/6abe321bd8258565f7cd4081fabef6a74b671427)

- **作者**: alex7092
- **时间**: 2026-11-20T13:23:53Z
- **提交信息**: [Doc] Use the dash-separated CLI flag names in the docs (#65039)

Signed-off-by: 刘星 <liuxing35@huawei.com>
Co-authored-by: 刘星 <liuxing35@huawei.com>
Co-authored-by: opencode <noreply@opencode.ai>

### [6825e9c](https://github.com/vllm-project/vllm/commit/6825e9cae902f4dd26517b8e08293c50dbd1d06b)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-11-20T13:00:22Z
- **提交信息**: [Security] Validate kv_transfer_params role sub-dicts are dicts (#55182)

Signed-off-by: Juan Pérez de Algaba <jperezde@redhat.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [89c408f](https://github.com/vllm-project/vllm/commit/89c408f80400a758704f74802d71825cd50d712d)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-11-20T12:59:57Z
- **提交信息**: [Security] Stop Responses input validation after the first invalid item (#68907)

Signed-off-by: Juan Pérez de Algaba <jperezde@redhat.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [89d9b4d](https://github.com/vllm-project/vllm/commit/89d9b4d187efbe03a9a4fee72d668587a4629d18)

- **作者**: Luca Motz
- **时间**: 2026-11-20T12:51:24Z
- **提交信息**: [Bugfix][Rust Frontend] Skip the engine's LRU multimodal cache under vllm-rs (#68672)

Signed-off-by: Luca Motz <luca.motz@icloud.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [5cd63b6](https://github.com/vllm-project/vllm/commit/5cd63b656cee1671b23c1dcb9b88d89b4092eb40)

- **作者**: Isotr0py
- **时间**: 2026-11-20T12:43:40Z
- **提交信息**: [Multimodal] Deprecate `VLLM_OBJECT_STORAGE_SHM_BUFFER_NAME` env var (#68900)

Signed-off-by: Isotr0py <Isotr0py@outlook.com>

### [b38d1fe](https://github.com/vllm-project/vllm/commit/b38d1fe4d29ecf626cd162beef327511fd6f4784)

- **作者**: Jee Jee Li
- **时间**: 2026-11-20T12:36:32Z
- **提交信息**: [Model] Register public HY4 checkpoint and update supported models (#68875)

Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [e6109f0](https://github.com/vllm-project/vllm/commit/e6109f064ae7205a4164593817238180a4cbb59f)

- **作者**: Isotr0py
- **时间**: 2026-11-20T12:29:38Z
- **提交信息**: [Fast Start] Add VMM IPC backend support for preload daemon (#68210)

Signed-off-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [5a21c6c](https://github.com/vllm-project/vllm/commit/5a21c6c853bff525dbaa4cc06596e3c374599f85)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-11-20T12:06:16Z
- **提交信息**: [Bugfix][Security] Account for peak GPU usage in PyNvVideoCodec pool lease (#52605)

Signed-off-by: Juan Pérez de Algaba <jperezde@redhat.com>

### [b2bb55a](https://github.com/vllm-project/vllm/commit/b2bb55ab7ddf8506fb7e0db4b6d92f590e878a27)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-11-20T12:05:59Z
- **提交信息**: [Security] Bound torchaudio resample kernel size (#56842)

Signed-off-by: Juan Pérez de Algaba <jperezde@redhat.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [d07dc0d](https://github.com/vllm-project/vllm/commit/d07dc0dab966653c3c80efb5ea043bb7b7682ec3)

- **作者**: Cr
- **时间**: 2026-11-20T12:05:05Z
- **提交信息**: [Bugfix][Offload] Offload Transformers backend vision towers with --cpu-offload-gb (#68479)

Signed-off-by: Cr <60964294+Chr0mium24@users.noreply.github.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [6fe28b1](https://github.com/vllm-project/vllm/commit/6fe28b1edc6664054ff4da063046fbd13c8b928c)

- **作者**: Yarikama
- **时间**: 2026-11-20T11:50:05Z
- **提交信息**: [Bugfix][Multimodal] Qwen3-VL: accept integer per-video fps lists (#68832)

Signed-off-by: yarikama <amaki30226@gmail.com>

### [14da26e](https://github.com/vllm-project/vllm/commit/14da26e3e9d0a8dd042a62da17495ccd2a7d07b6)

- **作者**: Yarikama
- **时间**: 2026-11-20T11:46:36Z
- **提交信息**: [Bugfix][Multimodal] Normalize negative-stride video inputs (#68857)

Signed-off-by: yarikama <amaki30226@gmail.com>

### [4d92bb6](https://github.com/vllm-project/vllm/commit/4d92bb632424cc249358c350d55c2ed9980fb4c1)

- **作者**: Mikko Tukiainen
- **时间**: 2026-11-20T11:45:58Z
- **提交信息**: [ROCm][Perf][Qwen4Exp] Dispatch HC combine_and_mix to the AITER FlyDSL two-stage kernel on gfx942 and gfx950 (#59442)

Signed-off-by: Mikko Tukiainen <Mikko.Tukiainen@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Simon Danielsson <70206058+simondanielsson@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [88c12de](https://github.com/vllm-project/vllm/commit/88c12de0fec770bd5a49de7b2976937e32d2c72e)

- **作者**: Harry Mellor
- **时间**: 2026-11-20T11:42:29Z
- **提交信息**: [Model] Use upstream Falcon and RADIO configs at the Transformers 5.16 floor (#68793)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [2aa4752](https://github.com/vllm-project/vllm/commit/2aa47529f02bb34cf869c35c4345000fa2934c78)

- **作者**: Sean Murphy
- **时间**: 2026-11-20T11:24:15Z
- **提交信息**: [Bugfix] Map only encoded items in multimodal tower/connector LoRA (#68754)

Signed-off-by: Sean Murphy <89842589+chipsncheese-ie@users.noreply.github.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [0fda86a](https://github.com/vllm-project/vllm/commit/0fda86a35419c9c70dbfada224c838c10fbb62ad)

- **作者**: Sergio Morillas Carmona
- **时间**: 2026-11-20T10:27:38Z
- **提交信息**: [Model] Add native ShieldGemma 2 support for /classify (#68447)

Signed-off-by: Sergio Morillas Carmona <smorillas@arsys.es>

### [8e89ed9](https://github.com/vllm-project/vllm/commit/8e89ed9ff97240a609752d2e2be252edf7181502)

- **作者**: Jee Jee Li
- **时间**: 2026-11-20T10:24:55Z
- **提交信息**: [Rust Frontend] Stream Muse tool-call arguments (#68766)

Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [cd6964a](https://github.com/vllm-project/vllm/commit/cd6964a71766b7507c19d9a3993b370bdc681310)

- **作者**: Salt Sato
- **时间**: 2026-11-20T10:24:08Z
- **提交信息**: [Rust Frontend] Report engine errors on completion streams that request logprobs (#55399)

Signed-off-by: Feathbow <feathbow@gmail.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [1086e80](https://github.com/vllm-project/vllm/commit/1086e80310d0c18b6e867cb67f3e8dcc424891ce)

- **作者**: Bugen Zhao
- **时间**: 2026-11-20T10:23:22Z
- **提交信息**: [Rust Frontend] Prefer tokenizer.json over tekken.json (#68911)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [d32e716](https://github.com/vllm-project/vllm/commit/d32e716bc41bc986e3ed2a04f6f287cd3cf0d5a7)

- **作者**: Bugen Zhao
- **时间**: 2026-11-20T10:22:36Z
- **提交信息**: [Rust Frontend] Accept --enable-offline-docs, --aggregate-engine-logging and --uvicorn-log-level as no-ops (#68409)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [52ea1a4](https://github.com/vllm-project/vllm/commit/52ea1a47d537da9d452c2c1feed85cf1688865a3)

- **作者**: Bugen Zhao
- **时间**: 2026-11-20T10:21:49Z
- **提交信息**: [Rust Frontend] Treat an undefined value's length as 0 in chat templates (#68407)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [eafe086](https://github.com/vllm-project/vllm/commit/eafe086bd39c483b47aa92d6c076bb29b3162019)

- **作者**: Bugen Zhao
- **时间**: 2026-11-20T10:21:01Z
- **提交信息**: [Rust Frontend] List valid model aliases when a model is not found (#68913)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [e86274c](https://github.com/vllm-project/vllm/commit/e86274c629114eb957467fd1bef64dc5da5f38e8)

- **作者**: Bugen Zhao
- **时间**: 2026-11-20T10:18:46Z
- **提交信息**: [Rust Frontend] Unload a LoRA adapter an engine already evicted (#68910)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [55e6ac5](https://github.com/vllm-project/vllm/commit/55e6ac510016dda0177cdbf41cf5449ca86d1a75)

- **作者**: Johnson Shi
- **时间**: 2026-11-20T10:16:47Z
- **提交信息**: [Bugfix][Benchmark] Forward --seed to the spec_bench and speed_bench datasets (#68859)

Signed-off-by: Johnson Shi <13926417+johnsonshi@users.noreply.github.com>
Co-authored-by: Copilot App <223556219+Copilot@users.noreply.github.com>

### [932d2ea](https://github.com/vllm-project/vllm/commit/932d2ea04d8af4d09fff1eb46e4aa5f433e9fe85)

- **作者**: 최재영
- **时间**: 2026-11-20T10:15:57Z
- **提交信息**: [Bugfix][Rust Frontend] Keep response_format in chat /tokenize (#68143)

Signed-off-by: 최재영 <144660874+Jaeyeong-CHOI@users.noreply.github.com>
Co-authored-by: OpenAI Codex (GPT-6 Astra) <noreply@openai.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [e24f57c](https://github.com/vllm-project/vllm/commit/e24f57c5ccdb4c18efc2f6c70db8263f245cb589)

- **作者**: Bugen Zhao
- **时间**: 2026-11-20T10:15:09Z
- **提交信息**: [Rust Frontend] Reject a missing completions prompt with Python's message (#68406)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [09fa182](https://github.com/vllm-project/vllm/commit/09fa18222090aeff715133558a4b92ac3bfa4b93)

- **作者**: Edoardo Vacchi
- **时间**: 2026-11-20T10:11:05Z
- **提交信息**: [Rust Frontend] Add mistral reasoning parser (#48013)

Signed-off-by: Edoardo Vacchi <evacchi@users.noreply.github.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [adcb472](https://github.com/vllm-project/vllm/commit/adcb47222d4cc60f53077de4cc0d1ab4122f2c1f)

- **作者**: Marina Ma
- **时间**: 2026-11-20T10:08:23Z
- **提交信息**: [Bugfix][Rust Frontend] Check min_tokens against max_completion_tokens when both limits are set (#63967)

Signed-off-by: MarinaMackay <2428877264@qq.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [0cce1d7](https://github.com/vllm-project/vllm/commit/0cce1d7b68038faeac6ea0537140b5d47df4c826)

- **作者**: Yu-Chi (Maggie) Pai
- **时间**: 2026-11-20T10:07:21Z
- **提交信息**: [Bugfix][Rust Frontend] Accept strict tools without parameters (#68073)

Signed-off-by: Baiiiiiiiiii <2002paipai@gmail.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [9a4930a](https://github.com/vllm-project/vllm/commit/9a4930a797846e4d57af7f72df20d82acaeb9c10)

- **作者**: Jiangyun Zhu
- **时间**: 2026-11-20T09:35:43Z
- **提交信息**: [Core][Mamba] Remove mamba_cache_mode (#63830)

Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [feca149](https://github.com/vllm-project/vllm/commit/feca149032fcad40401b26c64854c26e53cf9d4d)

- **作者**: herotai214
- **时间**: 2026-11-20T09:23:13Z
- **提交信息**: [Core][EPD] Fail metadata-only items no EC or KV transfer covers (#66928)

Signed-off-by: herotai214 <herotai214@gmail.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [cc23ce1](https://github.com/vllm-project/vllm/commit/cc23ce153ec82cdda7046fb0d8369f8cd4dfba4f)

- **作者**: WMC
- **时间**: 2026-11-20T09:02:39Z
- **提交信息**: [ROCm][Perf] W4A16: serve 6-8 decode rows with the HIP skinny GEMM on gfx1151 (#65911)

Signed-off-by: weimin023 <tnwilly@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [5f47b64](https://github.com/vllm-project/vllm/commit/5f47b64f96245dd6ff236b2f7492aeb26bc78dfc)

- **作者**: Sahithi Chigurupati
- **时间**: 2026-11-20T08:54:44Z
- **提交信息**: [CI] Use a uv-managed Python in the Python 3.12 smoke test (#68887)

Signed-off-by: Sahithi Chigurupati <chigurupati.sahithi@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [92b9817](https://github.com/vllm-project/vllm/commit/92b9817e02aba90461e0e7ec4e8d0d2543f5ada3)

- **作者**: Hung Hoang (黄兴）
- **时间**: 2026-11-20T08:11:56Z
- **提交信息**: [Bugfix][Pooling] Let chunked embeddings truncate above max_model_len (#68852)

Signed-off-by: hungh <hungh@nvidia.com>
Co-authored-by: Cursor Agent <cursoragent@cursor.com>

### [d9d7e94](https://github.com/vllm-project/vllm/commit/d9d7e9434f2dfca94a424deedca44a36d673ce0a)

- **作者**: zsun6
- **时间**: 2026-11-20T07:53:34Z
- **提交信息**: [Perf][Startup] Move atomic_writer out of weight_utils so the model-info cache save stays light (#57311)

Signed-off-by: Zhongrui Sun <sunzhongrui66@gmail.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [f8ff213](https://github.com/vllm-project/vllm/commit/f8ff2135e5c9a1121e05c91820cfbdbe3d467427)

- **作者**: Taimys
- **时间**: 2026-11-20T07:41:48Z
- **提交信息**: [Refactor][MoE] Migrate Quark static INT8 to the MoE oracle (#58672)

Signed-off-by: fangyao fan <2281693949@qq.com>
Signed-off-by: Felix Marty <Felix.Marty@amd.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Felix Marty <Felix.Marty@amd.com>

### [97372a5](https://github.com/vllm-project/vllm/commit/97372a5f920930356cf65ad9fd219c978443763f)

- **作者**: Jared Wen
- **时间**: 2026-11-20T07:33:13Z
- **提交信息**: [CI] Skip HYV4Flash in PP equivalence below Hopper (#68883)

Signed-off-by: Jared Wen <jaredwen@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [f7a4370](https://github.com/vllm-project/vllm/commit/f7a4370530b73d81371d471285d1a1ffe006a11a)

- **作者**: Woosuk Kwon
- **时间**: 2026-11-20T07:18:18Z
- **提交信息**: [Recipe] Inkling 2 Small: serve from nightly and add Hopper (H200) (#68864)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [e71492c](https://github.com/vllm-project/vllm/commit/e71492c206a8c17810090f5c6c9730e4d4e8a9cd)

- **作者**: Jared Wen
- **时间**: 2026-11-20T07:17:22Z
- **提交信息**: [Perf][Mamba] Export ShortConv (LFM2/LFM3) prefill checkpoints (#68673)

Signed-off-by: Jared Wen <jaredwen@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [7fb48d1](https://github.com/vllm-project/vllm/commit/7fb48d1567305bb0b91cfbc4cdaf58776c03d778)

- **作者**: Dakai An
- **时间**: 2026-11-20T06:57:47Z
- **提交信息**: [Refactor][KV Cache] Remove EAGLE block dropping and default to lookahead hashes (#66234)

Signed-off-by: Dakai An <dakaian108@gmail.com>

### [aefea5c](https://github.com/vllm-project/vllm/commit/aefea5c8e00c47032cda6d0b75704f6cd0a7c66d)

- **作者**: Yifei Wang
- **时间**: 2026-11-20T06:42:40Z
- **提交信息**: [Core] Resolve the Mamba block size from the KV cache specs of all pipeline stages (#67994)

Signed-off-by: Yifei Wang <yifei.w@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: taking-lying-flat <234872336+taking-lying-flat@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [2852f91](https://github.com/vllm-project/vllm/commit/2852f91c8575eab7a1b51841c81e65aac2c18793)

- **作者**: Guancheng Fu
- **时间**: 2026-11-20T06:36:34Z
- **提交信息**: [Bugfix][Quantization] Load quantized Qwen3-Next MoE gate from INC/AutoRound checkpoints (#68120)

Signed-off-by: Guancheng Fu <guancheng.fu@intel.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [614f166](https://github.com/vllm-project/vllm/commit/614f166cf10b05662ccdb8aea26e14124d86fdd6)

- **作者**: Lantao Jin
- **时间**: 2026-11-20T06:35:11Z
- **提交信息**: [Model][LoRA] Serve native Transformers GTE rerankers and their LoRA adapters (#68622)

Signed-off-by: Lantao Jin <ltjin@amazon.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [45411b5](https://github.com/vllm-project/vllm/commit/45411b563c5fd303651ba85a8114e2c3f69a89f6)

- **作者**: Tony Lin
- **时间**: 2026-11-20T06:33:07Z
- **提交信息**: [CI] Use real hash initialization in KV handshake tests (#68815)

Signed-off-by: Lin Tony <tony.lin@intel.com>
Signed-off-by: Tony Lin <tony.lin@intel.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [8586ccb](https://github.com/vllm-project/vllm/commit/8586ccbcf58e69ecb69e370dd2fa69fb739f9b0c)

- **作者**: Hen in UI
- **时间**: 2026-11-20T05:47:42Z
- **提交信息**: [Bugfix] Apply --enable-force-include-usage to streaming generate (#67249)

Signed-off-by: paul <paulqwer.cs13@nycu.edu.tw>
Signed-off-by: nien-hui <paulqwer.cs13@nycu.edu.tw>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [23b5918](https://github.com/vllm-project/vllm/commit/23b5918d9d0152c3ba2d8445827124d22a733a13)

- **作者**: Aaron Hao
- **时间**: 2026-11-20T05:26:23Z
- **提交信息**: [Quantization] Keep E8M0 scale bytes when loading into uint8 params (#65256)

Signed-off-by: Aaron Hao <hao-aaron@users.noreply.github.com>
Co-authored-by: Aaron Hao <hao-aaron@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: aoshen02 <aoshen02@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [8aee7b5](https://github.com/vllm-project/vllm/commit/8aee7b57dedc8cbd975b09d5ae77fc453a19d569)

- **作者**: Chongmin Li
- **时间**: 2026-11-20T05:23:48Z
- **提交信息**: [Bugfix] Fingerprint skipped multimodal components in the weight cache key (#66396)

Signed-off-by: lichongmin <chongminli.cn@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>

### [fd2cf98](https://github.com/vllm-project/vllm/commit/fd2cf985b66f88c8d2d887d0faf023e4036f904d)

- **作者**: Hokwang Choi
- **时间**: 2026-11-20T05:23:41Z
- **提交信息**: [Bugfix][Pooling] Don't run chunked post-processing for /pooling (#67791)

Signed-off-by: Hokwang Choi <choi920330@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [aacae1c](https://github.com/vllm-project/vllm/commit/aacae1c20a83a3a0bd4770502f50adccae005f79)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-11-20T05:21:47Z
- **提交信息**: [Security] Reject ICNS image inputs before decoding (#68245)

Signed-off-by: Juan Pérez de Algaba <jperezde@redhat.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [9ed4a86](https://github.com/vllm-project/vllm/commit/9ed4a8668dc7c452b2acbf39fb645b99938ec15c)

- **作者**: Yan Ma
- **时间**: 2026-11-20T05:19:04Z
- **提交信息**: [XPU] quick fix for _compact_sampling_mask_xpu (#68624)

Signed-off-by: Yan Ma <yan.ma@intel.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [efffc2a](https://github.com/vllm-project/vllm/commit/efffc2a0bccb0d16f906fc0738835269fe3302e7)

- **作者**: LinG
- **时间**: 2026-11-20T05:10:09Z
- **提交信息**: [Perf][Qwen4Exp] QSA: sm_100 split-K launch configs for small batches (#68842)

Signed-off-by: LinG <notch5370@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [56adf39](https://github.com/vllm-project/vllm/commit/56adf393d564667eb85e9eecd1ad8524084afc04)

- **作者**: Jon Su
- **时间**: 2026-11-20T04:50:57Z
- **提交信息**: [Bugfix][Multimodal] Fix Qwen3-VL M-RoPE input positions after a pruned video (#68270)

Signed-off-by: Jon Su <jsu@gsitechnology.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [efb6ed2](https://github.com/vllm-project/vllm/commit/efb6ed2fe36ae358ed3b001e51221ef411484113)

- **作者**: Thang Nguyen
- **时间**: 2026-11-20T04:48:17Z
- **提交信息**: [CI] Move B200 DeepEP v2 MoE DP integration to nightly (#68840)

Signed-off-by: Thang Nguyen <thangnguyenvn647@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [8414448](https://github.com/vllm-project/vllm/commit/84144487904064821fe02fa738cb56bd72088004)

- **作者**: Yan Ma
- **时间**: 2026-11-20T04:42:42Z
- **提交信息**: [Feat][Quantization] Online linear NVFP4 to MXFP4 (#61620)

Signed-off-by: Yan Ma <yan.ma@intel.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [5020556](https://github.com/vllm-project/vllm/commit/5020556c32d24cd7429756fefe92cfb2d6c5e466)

- **作者**: Aaron Hao
- **时间**: 2026-11-20T04:26:32Z
- **提交信息**: [RL][Model Loader] Reload directly by default with weight updates (VLLM_RELOAD_MODE=auto) (#68041)

Signed-off-by: Aaron Hao <hao-aaron@users.noreply.github.com>
Signed-off-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: Aaron Hao <hao-aaron@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: aoshen02 <aoshen@inferact.ai>

### [e2881ce](https://github.com/vllm-project/vllm/commit/e2881cef2e031e1420c82fd6009c4ae8e925c6e5)

- **作者**: Juntian Liu
- **时间**: 2026-11-20T04:20:52Z
- **提交信息**: [Feature][DSv4.1] Engram pool: split Engram tables across engines over NVLink or RDMA (#67539)

Signed-off-by: Juntian Liu <Juntianl777@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: v <v@inferact.ai>

### [9b088c6](https://github.com/vllm-project/vllm/commit/9b088c6667cbb9cce3eaa5ad937548aad36e8e7e)

- **作者**: Oliver Yu
- **时间**: 2026-11-20T04:05:49Z
- **提交信息**: [ROCm][Perf][Qwen4Exp] Tile QSA indexer scoring and skip invisible columns (#62589)

Signed-off-by: Oliver Yu <tc3oliver@gmail.com>
Signed-off-by: tc3oliver <tc3oliver@gmail.com>
Signed-off-by: Oliver Yu <57586652+tc3oliver@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [fab14ef](https://github.com/vllm-project/vllm/commit/fab14ef3bde87cae47f3d07ac50fc00f4bb477d6)

- **作者**: xiangdong
- **时间**: 2026-11-20T03:50:26Z
- **提交信息**: [XPU][CI]Move BMG Engine (1 GPU) on k8s to avoid random hang (#68653)

Signed-off-by: zengxian <xiangdong.zeng@intel.com>

### [ba0112a](https://github.com/vllm-project/vllm/commit/ba0112a4af8b03cba4b4b5961134ec2355bdafc7)

- **作者**: Yiliu Dong
- **时间**: 2026-11-20T03:49:45Z
- **提交信息**: [Perf][MoE] Enable SM90 MXFP4 MegaMoE via FlashInfer MoE-EP (#64289)

Signed-off-by: Yiliu Dong <91178480+qianlihuang@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [0d787bf](https://github.com/vllm-project/vllm/commit/0d787bf97cf8ad8f40bb3a5eb0f4dea69beb9e9b)

- **作者**: Chongmin Li
- **时间**: 2026-11-20T03:44:00Z
- **提交信息**: [Bugfix][Fast Start] Keep the source daemon up when the compiled cache cannot be published (#68460)

Signed-off-by: lichongmin <chongminli.cn@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [596455c](https://github.com/vllm-project/vllm/commit/596455c7f16d14e761fbf8b61bf071b2e31c9aa5)

- **作者**: Kai Hoang
- **时间**: 2026-11-20T03:39:13Z
- **提交信息**: [Bugfix][Reasoning] Return unfinished K2 Horizon reasoning as reasoning (#60969)

Signed-off-by: hpdkhoa <hpdkhoa2311@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Chauncey <chaunceyjiang@gmail.com>

### [cf0a814](https://github.com/vllm-project/vllm/commit/cf0a814985c8107e905cde10ae43d8f7bc0c0675)

- **作者**: Xun Sun
- **时间**: 2026-11-20T03:35:52Z
- **提交信息**: [Fast Start] Support ModelOpt INT8 pre-processed weights (#68176)

Signed-off-by: Xun Sun <UNIDY2002@outlook.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [deac6e1](https://github.com/vllm-project/vllm/commit/deac6e19d4cd8421a4f22a252fbd4810ac07328b)

- **作者**: frida-andersson
- **时间**: 2026-11-20T03:30:49Z
- **提交信息**: [ROCm][DSv4.1][Perf] Fuse the gfx942 mHC seam in the V4.1 AMD model (#60153)

Signed-off-by: Frida Andersson <fanderss@amd.com>

### [700af46](https://github.com/vllm-project/vllm/commit/700af4612915fe008fe1e0d8c97de23c57e3a1ac)

- **作者**: Roy Wang
- **时间**: 2026-11-20T03:24:57Z
- **提交信息**: [Recipe] Add HY4 (#68844)

Signed-off-by: esmeetu <jasonailu87@gmail.com>
Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>

### [d1ad108](https://github.com/vllm-project/vllm/commit/d1ad1088bc63d5320689b06ba36fc5ae0564361f)

- **作者**: Sahithi Chigurupati
- **时间**: 2026-11-20T02:55:40Z
- **提交信息**: [Bugfix][Attention] Avoid GPU<->CPU sync in FlashInfer XQA ragged draft mask (#68782)

Signed-off-by: Sahithi Chigurupati <chigurupati.sahithi@gmail.com>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [898a7c6](https://github.com/vllm-project/vllm/commit/898a7c68c2d1e869ebde2ce25ffbfc1e253bf0b4)

- **作者**: Yifei Wang
- **时间**: 2026-11-20T02:34:22Z
- **提交信息**: [KV Connector][NIXL] Exclude indexer backends from the compatibility hash (#67680)

Signed-off-by: Yifei Wang <yifei.w@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [c3310a8](https://github.com/vllm-project/vllm/commit/c3310a88900a5e07b0380213d82a9e6057627d1e)

- **作者**: Ren Yuzhou
- **时间**: 2026-11-20T02:25:58Z
- **提交信息**: [Bugfix][MoRIIO] Preserve WRITE receive mappings after consumer abort (#59058)

Signed-off-by: Yuzhou Ren <ryzcqu@outlook.com>
Signed-off-by: Ren Yuzhou <54501155+yuzhouo7@users.noreply.github.com>
Co-authored-by: Codex <codex@openai.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Shanshan Shen <467638484@qq.com>

### [6f022f1](https://github.com/vllm-project/vllm/commit/6f022f1080b78e7f5f752bfae85a95cf819a402c)

- **作者**: xiao-vllm_amd
- **时间**: 2026-11-20T02:22:02Z
- **提交信息**: [ROCm][Kernel] Add W4A8 MoE decode kernel for RDNA3/RDNA3.5 (gfx11) (#62480)

Signed-off-by: Xiao Yu <xiao.yu.dc@outlook.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [1292401](https://github.com/vllm-project/vllm/commit/12924016eb8dbaae87d5163a1b7ec2614a44a797)

- **作者**: Nick Hill
- **时间**: 2026-11-20T02:09:54Z
- **提交信息**: [Bugfix][Scheduler] Free consumed encoder inputs at schedule time (simplifies #67385) (#68799)

Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Jonathan Buck <jonabuck@amazon.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [3d0cc35](https://github.com/vllm-project/vllm/commit/3d0cc3502b10fca55a8c0ab35d39fde3ba2b8f2a)

- **作者**: djramic
- **时间**: 2026-11-20T02:03:54Z
- **提交信息**: [Bugfix][ROCm] Fix a cross-wave race in the batched kpool decode update (#68749)

Signed-off-by: Djordje Ramic <djoramic@amd.com>

### [82c6b32](https://github.com/vllm-project/vllm/commit/82c6b325b49ce361f5a295eb7d932e1b439e187d)

- **作者**: Nick Hill
- **时间**: 2026-11-20T01:28:28Z
- **提交信息**: [Bugfix][NIXL] Don't invalidate a disconnected engine whose agents are gone (#68227)

Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [07e4d6b](https://github.com/vllm-project/vllm/commit/07e4d6b957f70075b132b7e0c05c649dcbd0d4b7)

- **作者**: Mirza Halilčević
- **时间**: 2026-11-20T00:56:59Z
- **提交信息**: [CI] Free torch.compile state between tests in compile pass tests (#68790)

Signed-off-by: Mirza Halilcevic <mirza.halilcevic@amd.com>

### [1c0b139](https://github.com/vllm-project/vllm/commit/1c0b139293a22cce96c41c9fb32cbf2c31d30e7a)

- **作者**: Aaravos
- **时间**: 2026-11-20T00:38:48Z
- **提交信息**: [Bugfix][Transformers] Preserve received hidden states on later pipeline stages (#67648)

Signed-off-by: tgghzyh <430211065@qq.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [34ca0b6](https://github.com/vllm-project/vllm/commit/34ca0b616cba103cec627c428259ddab50864f3a)

- **作者**: Harry Mellor
- **时间**: 2026-11-20T00:36:00Z
- **提交信息**: [Transformers backend] Trace decorated forwards and pin `cache` in the fx tracer (#68724)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [711c378](https://github.com/vllm-project/vllm/commit/711c378134451465934d022598568e1968b3120e)

- **作者**: Nils Matteson
- **时间**: 2026-11-20T00:33:55Z
- **提交信息**: [Bugfix] Don't re-append default custom ops on every `replace()` (#67166)

Signed-off-by: Nils Matteson <nils@inferact.ai>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [34c6538](https://github.com/vllm-project/vllm/commit/34c6538866768d9fdaafe6b208875af3bd95ddb2)

- **作者**: eky-amd
- **时间**: 2026-11-20T00:31:35Z
- **提交信息**: [ROCm][Perf] Fuse GDN decode (conv1d + delta rule + gated norm) into AITER's gluon kernel (Qwen3.8-27B) (#61428)

Signed-off-by: Ethan Ky <ethan.ky@amd.com>
Signed-off-by: eky-amd <ethan.ky@amd.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [1868d4c](https://github.com/vllm-project/vllm/commit/1868d4c56eae8b464c4634b9b70dbf02cd87df61)

- **作者**: Nick Hill
- **时间**: 2026-11-20T00:30:16Z
- **提交信息**: [Misc] Trim get_decode_stream_seed docstring (#68780)

Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [7a3650f](https://github.com/vllm-project/vllm/commit/7a3650fc6fca68db6273801e12f61c46c7765e26)

- **作者**: Fanli Lin
- **时间**: 2026-11-20T00:08:51Z
- **提交信息**: [XPU][Tests] Run Triton-only ReplaySSM/SSU tests on XPU (#68318)

Signed-off-by: Lin, Fanli <fanli.lin@intel.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [d8e6d28](https://github.com/vllm-project/vllm/commit/d8e6d2834fc32794a6489703a6d43f95cad31cc4)

- **作者**: Fanli Lin
- **时间**: 2026-11-20T00:05:38Z
- **提交信息**: [CI][XPU] Add Hybrid SSM NixlConnector PD prefix cache test to Intel CI (#68617)

Signed-off-by: root <root@gnr17409.jf.intel.com>
Co-authored-by: root <root@gnr17409.jf.intel.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-11-21
**监控日期**: 2026-11-20
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7876
- **最后更新**: 2026-11-21T02:12:44Z

## 提交统计

- **昨日提交总数**: 40
- **提交者数量**: 31
- **主要提交者**: Yukim1, y-null, Alexis Román

## AI分析总结

# vllm-omni 昨日提交分析（40条）

## 1. 主要更新类型分布
- **Bug修复为主**（约24条，60%）：音频截断、模型能力校验、参数覆盖、指标统计等
- **性能优化**（约5条）：CosyAttention3流式packed flow扩展、注意力掩码分类、CFM QKV融合等
- **功能新增/模型支持**（约5条）：Cosmos3-Nano-Transfer新模型、MiniMax-Music3/YuE2迁移至Model Runner V2
- **CI/构建与硬件适配**（约6条）：ROCm、NPU、XPU、HunyuanImage测试矩阵调整
- **重构/配置规范化**（约4条）：Pi运行时命名空间合并、TRT环境变量类型化、LoRA键归一化

## 2. 关键变更点与项目方向的关系
项目目标是"为所有人提供简单、快速、低成本的全模态模型服务"，本次提交紧密围绕这一主线：

- **Model Runner V2 推进**：MiniMax-Music3、YuE2、Higgs Audio v3 等模型陆续迁移到新一代Runner，表明核心推理架构升级正在进行中
- **多模态健壮性**：大量修复集中在音频生成边界场景（长度限制截断、上下文限界保留、first-packet延迟回归），直接提升TTS/音频服务的SLA
- **多硬件生态**：Ascend NPU算子融合、ROCm测试守卫、Intel XPU作业拆分，延续全平台覆盖承诺
- **服务治理**：按模型能力门控请求处理、serve标志优先级修复、Anthropic Messages 501响应，增强API层的正确性

## 3. 对项目的影响和潜在意义
- **稳定性提升**：密集的边界条件修复（截断、dtype保持、调度标志）降低生产环境故障率
- **性能收益**：FA2/FlashInfer扩展与注意力优化将显著降低CosyVoice3等流式模型的延迟
- **架构现代化**：Runner V2迁移减少技术债，为后续新模态模型铺路
- **生态兼容性**：LoRA布局校验、diffusion量化反量化等修复扩大了与第三方权重的兼容面

## 4. 值得关注的技术点
- **[Bugfix][Metrics] 排除diffusion调度器等待时间**：生成时间统计更真实，影响性能调优决策
- **FA4 Ring Attention编译修复**：长上下文注意力在NVIDIA新硬件上的可用性关键
- **NVFP4全精度diffusion层反量化**：量化模型在扩散任务中的质量权衡方案
- **Omni-DuplexEval judge帧分辨率限制**：全双工评测的成本与可重复性控制
- **Claude/Cursor等AI辅助工具的Co-authored-by记录**：反映AI辅助开发在本项目中已常态化

## 5. 基于README的项目发展影响
vllm-omni致力于让全模态服务"简单、快速、低成本"。昨日提交呈现**从功能扩张转向质量深耕**的趋势：Model Runner V2迁移保障"快速"，大量边界修复保障"简单可靠"，CI矩阵优化与硬件融合降低"成本"。测试矩阵精简（如doc tests限8个模型家族）和无效参数矩阵移至CPU测试，说明项目在控制CI成本的同时保持覆盖度。这种高频率、多贡献者的迭代节奏（含华为、NVIDIA、AMD、Intel等企业贡献者）表明项目已进入成熟社区驱动阶段，为1.0级别的生产就绪打下基础。

## 详细提交记录

### [31c8986](https://github.com/vllm-project/vllm-omni/commit/31c8986250d409db32006c51d4a1b3ce346a4d79)

- **作者**: amy-why-3459
- **时间**: 2026-11-20T22:14:08Z
- **提交信息**: [Bugfix] Preserve MiniMax Music 3 audio at the context limit (#10873)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [e037700](https://github.com/vllm-project/vllm-omni/commit/e037700200ae2d9e45a13b06f07bd7b0313e2440)

- **作者**: BruceLoveDecimal
- **时间**: 2026-11-20T21:42:31Z
- **提交信息**: [Perf][CosyVoice3] extend packed flow to FA2 and FlashInfer (#9081)

Signed-off-by: BruceLoveDecimal <liuqihao970610@gmail.com>
Signed-off-by: BruceLoveDecimal <39156883+BruceLoveDecimal@users.noreply.github.com>
Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Yueqian Lin <linyueqian@outlook.com>

### [a1a714c](https://github.com/vllm-project/vllm-omni/commit/a1a714c981c336720b53a6a054dd306953c37440)

- **作者**: Hikari
- **时间**: 2026-11-20T20:59:04Z
- **提交信息**: [Bugfix] Put the JoyAI delegate action before session instructions in the system prompt (#10847)

Signed-off-by: altale <extsuioku@gmail.com>

### [0795651](https://github.com/vllm-project/vllm-omni/commit/0795651e256244918edcb80da30d2763d2de99ca)

- **作者**: yezhi0312
- **时间**: 2026-11-20T19:54:22Z
- **提交信息**: [Hardware][Ascend] Fuse MiniCPM-o 4.5 CFM QKV normalization and KV writes (#10330)

Signed-off-by: yezhi0312 <liuyue199903@icloud.com>
Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: yezhi0312 <liuyue199903@icloud.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>
Co-authored-by: Yueqian Lin <linyueqian@outlook.com>

### [b1a42fd](https://github.com/vllm-project/vllm-omni/commit/b1a42fd21a70ee0b08362152e95d3a16a193f410)

- **作者**: lm10-arg
- **时间**: 2026-11-20T18:20:51Z
- **提交信息**: [CI/Build][ROCm] Take the AMD nightly count guards from collection (#10869)

Signed-off-by: andyluo7 <andy.luo@amd.com>
Co-authored-by: andyluo7 <andy.luo@amd.com>
Co-authored-by: Claude Code <noreply@anthropic.com>

### [d1374b3](https://github.com/vllm-project/vllm-omni/commit/d1374b3adfd575a8f5f2679a2d1abb87dd865014)

- **作者**: amy-why-3459
- **时间**: 2026-11-20T17:59:31Z
- **提交信息**: [Model] Run YuE2 on Model Runner V2 (#10792)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [3cb0191](https://github.com/vllm-project/vllm-omni/commit/3cb0191324ae69dd2e4a5033664a6c2e9485e2a7)

- **作者**: Weiming Liao
- **时间**: 2026-11-20T17:24:45Z
- **提交信息**: [Bugfix] Fix Qwen3-TTS first-packet P50 regression (#10851)

Signed-off-by: Weiming Liao <liaowm5@gmail.com>

### [99a9bf3](https://github.com/vllm-project/vllm-omni/commit/99a9bf38b731890c1cd0077fa16f78ed50682411)

- **作者**: searlion
- **时间**: 2026-11-20T14:58:07Z
- **提交信息**: [Bugfix][Cosmos3] Reject text-to-image requests that carry a reference image (#10653)

### [0d77b24](https://github.com/vllm-project/vllm-omni/commit/0d77b24d5b5dff334599f8fa1dd67895a5dcd85b)

- **作者**: amy-why-3459
- **时间**: 2026-11-20T14:33:41Z
- **提交信息**: [Bugfix] Fix Higgs Audio v3 MRV2 startup and first-batch audio (#10800)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [210fffb](https://github.com/vllm-project/vllm-omni/commit/210fffb189903c23450752aa32481a34998ad721)

- **作者**: wangyu
- **时间**: 2026-11-20T14:22:36Z
- **提交信息**: [CI/Build] Move invalid parameter matrices to CPU tests (#10719)

Signed-off-by: wangyu <410167048@qq.com>
Signed-off-by: [Your Name] <your.email@example.com>

### [5e0ecc0](https://github.com/vllm-project/vllm-omni/commit/5e0ecc0e185c543ab6b6af0698d689b9591cd1f2)

- **作者**: y-null
- **时间**: 2026-11-20T13:56:12Z
- **提交信息**: [Bugfix] Restore MiniCPM-o shutdown and crash cleanup coverage (#10738)

Signed-off-by: y_null <y_null@qq.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [b475b0c](https://github.com/vllm-project/vllm-omni/commit/b475b0c30283f9c22dcca3e873de97f28b847a03)

- **作者**: Gao Han
- **时间**: 2026-11-20T12:49:30Z
- **提交信息**: [Bugfix] Prevent stage-specific serve flags from overriding multiple stages (#10754)

Signed-off-by: Gao Han <hgaoaf@connect.ust.hk>

### [51d815b](https://github.com/vllm-project/vllm-omni/commit/51d815b105716a4d6f54a150d62357073c54013d)

- **作者**: Tianyao Wu
- **时间**: 2026-11-20T12:38:11Z
- **提交信息**: [Model] Run MiniMax-Music3 on Model Runner V2 (#9483)

Signed-off-by: Tianyao Wu <rayroy31@gmail.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [1feda9e](https://github.com/vllm-project/vllm-omni/commit/1feda9ef9324db359019b6625e6d45839e5ee45c)

- **作者**: Dong1017
- **时间**: 2026-11-20T12:29:01Z
- **提交信息**: [Bugfix] MiniMax-H3: validate the LightX2V Turbo 8-step v1.2 LoRA layout (#10805)

Signed-off-by: Dong1017 <55723162+Dong1017@users.noreply.github.com>
Co-authored-by: Samuel Cestola <samuel.cestola@h-partners.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: dengyunyang <584797741@qq.com>

### [0f7083c](https://github.com/vllm-project/vllm-omni/commit/0f7083c264750415cb54e7f18d9737dc7bdb917f)

- **作者**: Wang  fuyin
- **时间**: 2026-11-20T11:26:03Z
- **提交信息**: [Bugfix] Gate serving handlers on model capabilities (#10813)

Signed-off-by: Acerak01-fy <wfy2003324@163.com>
Co-authored-by: Clodagh Walsh <clodaghwalsh17@gmail.com>
Co-authored-by: dengyunyang <584797741@qq.com>

### [694f6ae](https://github.com/vllm-project/vllm-omni/commit/694f6aeadda6993d059aa9388a3718b9b3ac3480)

- **作者**: Armaan Amatya
- **时间**: 2026-11-20T11:14:07Z
- **提交信息**: [Bugfix] Bound Omni-DuplexEval judge frame resolution (#9038)

Signed-off-by: Armaan Amatya <armaanamatya2014@gmail.com>
Signed-off-by: Gao Han <hgaoaf@connect.ust.hk>
Co-authored-by: Gao Han <hgaoaf@connect.ust.hk>

### [c97819b](https://github.com/vllm-project/vllm-omni/commit/c97819b8b0c820fe48ef7f60d265457a9e701529)

- **作者**: amy-why-3459
- **时间**: 2026-11-20T10:28:35Z
- **提交信息**: [Bugfix] Return truncated Qwen3-TTS audio on length limits (#10795)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [dee0da7](https://github.com/vllm-project/vllm-omni/commit/dee0da70d548420436ffea43ab53b65ee142b3e5)

- **作者**: DarkMatter
- **时间**: 2026-11-20T09:58:25Z
- **提交信息**: [NPU] Bump mindiesd from 3.2.0 to 3.3.0 in NPU Dockerfiles (#10591)

Signed-off-by: DarkMatter9527 <1376576122@qq.com>
Co-authored-by: Weiming Liao <liaowm5@gmail.com>

### [751e50d](https://github.com/vllm-project/vllm-omni/commit/751e50d8e160f518a54607544a9836d45caba5e7)

- **作者**: wangbo23
- **时间**: 2026-11-20T09:41:13Z
- **提交信息**: fix(frontend): return 501 for Anthropic Messages on diffusion-only servers (#10694)

Signed-off-by: wang_bo <wangbo23@huawei.com>

### [985b14a](https://github.com/vllm-project/vllm-omni/commit/985b14a1d72dcc3372338c0333d204b2198ae705)

- **作者**: wangyu
- **时间**: 2026-11-20T08:29:41Z
- **提交信息**: [CI/Build] Align HunyuanImage performance and accuracy test matrix (#10408)

Signed-off-by: wangyu <410167048@qq.com>
Signed-off-by: [Your Name]
Signed-off-by: [Your Name] <your.email@example.com>
Co-authored-by: zzh <943967662@qq.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [da13f66](https://github.com/vllm-project/vllm-omni/commit/da13f66b834e07f9d4b05f1c6161a0c5d625bedf)

- **作者**: Dong1017
- **时间**: 2026-11-20T08:21:10Z
- **提交信息**: [Bugfix][Profiler] Build the wait/warmup/active schedule in the omni torch-profiler wrappers (#9891)

Signed-off-by: GUOGUO <xwdong1998@163.com>

### [379591b](https://github.com/vllm-project/vllm-omni/commit/379591bd4f83fba398a2f6124f04cc0beca25ab2)

- **作者**: NumberWan
- **时间**: 2026-11-20T07:58:52Z
- **提交信息**: [Bugfix] Normalize Qwen distill LoRA keys before fusion (#10722)

Signed-off-by: NumberWan <wantszkin2003@gmail.com>
Co-authored-by: Linze-Shi <linzeshi0@gmail.com>

### [77e6570](https://github.com/vllm-project/vllm-omni/commit/77e6570d60f7f031e3264a67821e0c5f17e1cbfa)

- **作者**: Rahul Steiger
- **时间**: 2026-11-20T06:36:14Z
- **提交信息**: [Bugfix] Fix FA4 Ring attention compilation (#8988)

Signed-off-by: Rahul Steiger <rsteiger@nvidia.com>
Signed-off-by: rsteiger <rsteiger@nsc-lhr-slurm-1-vscode-02.nvidia.com>
Co-authored-by: rsteiger <rsteiger@nsc-lhr-slurm-1-vscode-02.nvidia.com>

### [bbe6e7c](https://github.com/vllm-project/vllm-omni/commit/bbe6e7c851c162567498256da187fc04c9a18d2b)

- **作者**: wawa0125kirby
- **时间**: 2026-11-20T06:24:17Z
- **提交信息**: [Model][MiniMax-H3] Optional early-only video conditioning (keep_steps) for ref2va (#9762)

Signed-off-by: liliyongqi <wawawa0125@163.com>
Co-authored-by: wawa0125kirby <wawa0125kirby@users.noreply.github.com>
Co-authored-by: liliyongqi <wawawa0125@163.com>
Co-authored-by: Claude Code <noreply@anthropic.com>
Co-authored-by: dengyunyang <584797741@qq.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [0685d96](https://github.com/vllm-project/vllm-omni/commit/0685d96b03e6ca8564173473c48cf046488f90bf)

- **作者**: Abhinav Raichur
- **时间**: 2026-11-20T06:03:32Z
- **提交信息**: [Model][Pi] Consolidate runtimes under shared namespace (#8086)

Signed-off-by: avraichur96 <avraichur96@gmail.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [48f3ae7](https://github.com/vllm-project/vllm-omni/commit/48f3ae7d618d33ba1c621ef2c7570606f81ae5f0)

- **作者**: Sahil Joseph
- **时间**: 2026-11-20T05:23:03Z
- **提交信息**: [Misc][MiniCPM-o] Promote Token2Wav TRT env vars to typed stage keys (#10310)

Signed-off-by: warlord77 <sahiljoseph20@gmail.com>
Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: Yueqian Lin <linyueqian@outlook.com>

### [fac4d45](https://github.com/vllm-project/vllm-omni/commit/fac4d459b2e68cccd3c70ee0f163a9cc53667c81)

- **作者**: wangyu
- **时间**: 2026-11-20T04:59:24Z
- **提交信息**: [CI/Build] Limit GPU doc tests to eight model families (#10736)

Signed-off-by: wangyu <410167048@qq.com>
Signed-off-by: [Your Name] <your.email@example.com>
Co-authored-by: dengyunyang <584797741@qq.com>

### [62d353c](https://github.com/vllm-project/vllm-omni/commit/62d353c29ff14dba9f6e22d823b8def70f1e817b)

- **作者**: WEIXILIN
- **时间**: 2026-11-20T04:51:10Z
- **提交信息**: [Bugfix] Preserve Qwen3-Omni Code2Wav embedding dtype after mean (#8327)

Signed-off-by: Pinoeer-kingxi <13022943007@163.com>
Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: Yueqian Lin <linyueqian@outlook.com>

### [e26f36f](https://github.com/vllm-project/vllm-omni/commit/e26f36f1018785d44a519a54ee93f47652b6b600)

- **作者**: wenjun liu
- **时间**: 2026-11-20T04:27:10Z
- **提交信息**: [CI][Intel] Split the PR XPU step into dedicated 1-card and 2-card jobs (#10780)

Signed-off-by: wendyliu235 <wenjun.liu@intel.com>

### [e29e9b4](https://github.com/vllm-project/vllm-omni/commit/e29e9b468fd0c656e851f1d5f0524fb69b6089ad)

- **作者**: Yueqian Lin
- **时间**: 2026-11-20T03:56:52Z
- **提交信息**: [Bugfix] Pass num_logits to make_lora_inputs in the MRv2 runner (#10772)

Signed-off-by: Yueqian Lin <linyueqian@outlook.com>

### [f2f5c3a](https://github.com/vllm-project/vllm-omni/commit/f2f5c3affbfe044515caba0352d601f1136ce7e0)

- **作者**: Dong1017
- **时间**: 2026-11-20T03:53:26Z
- **提交信息**: [NPU] Log the torch_npu / CANN build identity at platform init (#9894)

Signed-off-by: GUOGUO <xwdong1998@163.com>

### [46cd3e6](https://github.com/vllm-project/vllm-omni/commit/46cd3e689f7ee75ab788bcb6214024652d011253)

- **作者**: Mateusz
- **时间**: 2026-11-20T03:50:01Z
- **提交信息**: [Bugfix] Honor request seed in Voxtral TTS (#6371)

Signed-off-by: Mateusz Kolodziejczyk <mateuszmrwkolodziejczyk@gmail.com>
Signed-off-by: Gao Han <hgaoaf@connect.ust.hk>
Co-authored-by: Mateusz Kolodziejczyk <mateuszmrwkolodziejczyk@gmail.com>
Co-authored-by: Gao Han <hgaoaf@connect.ust.hk>

### [735614b](https://github.com/vllm-project/vllm-omni/commit/735614ba60d63484b9bd6886cd9a01decb58aa49)

- **作者**: Yukim1
- **时间**: 2026-11-20T03:32:00Z
- **提交信息**: [Diffusion][Helios] Add resolution-specific VAE warmup at startup (#10734)

Signed-off-by: tyler lamar <2889896214@qq.com>
Signed-off-by: zwhzzz0821 <2831474076@qq.com>
Co-authored-by: tyler lamar <2889896214@qq.com>
Co-authored-by: dengyunyang <584797741@qq.com>

### [25d7d02](https://github.com/vllm-project/vllm-omni/commit/25d7d02336ab716556836daf99e40c9ba50275eb)

- **作者**: NumberWan
- **时间**: 2026-11-20T03:23:49Z
- **提交信息**: [Bugfix] Dequantize packed NVFP4 weights for full-precision diffusion layers (#10622)

Signed-off-by: NumberWan <wantszkin2003@gmail.com>
Co-authored-by: jbernloehr <jbernloehr@nvidia.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [1e77d5a](https://github.com/vllm-project/vllm-omni/commit/1e77d5abba32eabe201b8fed4a09dfcab520d692)

- **作者**: dongbo910220
- **时间**: 2026-11-20T02:54:10Z
- **提交信息**: [Bugfix] Keep inline VoxCPM2 references out of named voice caches (#10361)

Signed-off-by: dongbo910220 <1275604947@qq.com>
Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: Yueqian Lin <linyueqian@outlook.com>

### [8bf8318](https://github.com/vllm-project/vllm-omni/commit/8bf8318ce1dcfafb0b61d00f725d34359cd8893c)

- **作者**: MaciejBalaNV
- **时间**: 2026-11-20T02:42:05Z
- **提交信息**: [new model] Add Cosmos3-Nano-Transfer-Auto model (#6917)

Signed-off-by: Maciej Bala <mbala@nvidia.com>
Signed-off-by: MaciejBalaNV <mbala@nvidia.com>
Signed-off-by: Wojciech Rymer <wrymer@nvidia.com>
Signed-off-by: 汪志鹏 <wangzhipeng628@gmail.com>
Signed-off-by: princepride <wangzhipeng628@gmail.com>
Co-authored-by: Wojciech Rymer <wrymer@nvidia.com>
Co-authored-by: 汪志鹏 <wangzhipeng628@gmail.com>
Co-authored-by: Roger Wang <hey@rogerw.io>

### [d1812c8](https://github.com/vllm-project/vllm-omni/commit/d1812c82e61a57da5238bad49b03f764f4096331)

- **作者**: ZacheryAU
- **时间**: 2026-11-20T02:39:46Z
- **提交信息**: [Bugfix][Metrics] Exclude diffusion scheduler queue wait from stage generation time (#10610)

### [8098409](https://github.com/vllm-project/vllm-omni/commit/80984099cd1fc97b4bf024359b08564e15ae76cc)

- **作者**: searlion
- **时间**: 2026-11-20T02:32:41Z
- **提交信息**: [Bugfix][Cosmos3] Return every image for n > 1 text-to-image with guardrails on (#10652)

Signed-off-by: Lewis Won <lewis.won@gmail.com>

### [f5003af](https://github.com/vllm-project/vllm-omni/commit/f5003afa5311cd4474a111402fcbd40d03f9f581)

- **作者**: Alexis Román
- **时间**: 2026-11-20T02:25:50Z
- **提交信息**: fix(clients): honour the client handshake budget when opening a duplex session (#9084)

Signed-off-by: Jose Alexis Roman Martinez <alexis_romtz@hotmail.com>
Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: Yueqian Lin <linyueqian@outlook.com>

### [4662e59](https://github.com/vllm-project/vllm-omni/commit/4662e590dda1c443144593ea54faae7a00cb443d)

- **作者**: Yucheng Hu
- **时间**: 2026-11-20T02:03:34Z
- **提交信息**: [Perf][CosyVoice3] Classify the flow DiT attention mask once per forward on FLASH_ATTN (#9942)

Signed-off-by: Yucheng Hu <89879759+ychu824@users.noreply.github.com>
Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: Yueqian Lin <linyueqian@outlook.com>

---
