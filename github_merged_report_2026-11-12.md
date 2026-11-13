# GitHub Stars 合并报告 - 2026-11-12

**合并日期**: 2026-11-13
**监控日期**: 2026-11-12
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


**报告日期**: 2026-11-13
**监控日期**: 2026-11-12
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2292
- **最后更新**: 2026-11-13T01:55:27Z

## 提交统计

- **昨日提交总数**: 5
- **提交者数量**: 4
- **主要提交者**: Coach257, Obser, Zeren Chen

## AI分析总结

## 1. 主要更新类型

本批次提交以**性能优化**和**架构重构**为主导，兼有**功能新增**与**生态兼容**扩展，其中包含一条明确标注 `BREAKING` 的破坏性变更。整体类型分布为：性能优化 2 项（grouped-GEMM 遍历、MFU 估计）、重构 2 项（checkpoint 加载器、QAT 算子组织）、功能新增 2 项（Bagel HF 布局、MFU 工具）。

## 2. 关键变更点及其与项目整体方向的关系

项目目标是打造"以模型为中心的分布式训练配方库"，支撑任意模态模型的规模化训练，这批提交与该方向高度一致：

- **算子层提速**：N-fast 紧凑分组 GEMM 遍历重构，直接服务于多模态训练中密集的矩阵乘负载，属于配方库底层性能基座的持续打磨。
- **生态打通**：SeedOmni 支持 Bagel 的 HuggingFace checkpoint 布局，降低了与主流模型生态的互操作成本，契合"任意模态/任意模型"的通用性定位。
- **体系简化**：删除预切分 checkpoint 恢复加载器，是一次主动的"减法"，旨在统一并简化 checkpoint 生命周期管理，减少配方分发中的历史包袱。
- **量化训练规范化**：将单一的 `qat_implementation` 开关重构为按模型家族划分的 QAT 算子行，使量化感知训练从"全局开关"演进为"按需配方"，呼应 Model-Centric 配方理念。
- **效率可观测**：新增 MiniMax-H3 的 MFU（模型算力利用率）估计，为大规模训练提供量化评估手段。

## 3. 对项目的影响和潜在意义

- **破坏性变更需迁移**：移除 pre-split checkpoint 恢复加载器会中断依赖旧加载路径的下游训练流程，迫使用户迁移到统一入口，短期增加迁移成本，长期换来更可维护的 checkpoint 体系。
- **性能收益可量化**：GEMM 遍历优化与 MFU 估计形成"优化—度量"闭环，使配方效果更易验证。
- **生态位扩展**：HF checkpoint 兼容让 VeOmni 更易被外部模型团队采用，扩大配方库的适用面。
- **QAT 可组合性提升**：按家族组织算子行，意味着未来新增模型只需追加一行配方，而非侵入式改动。

## 4. 值得关注的技术点

- **N-fast grouped-GEMM 遍历**：对分组 GEMM 内存访问模式的紧凑化重排，是多模态混合形状算子调度的典型优化手法。
- **Checkpoint 布局标准化**：从"预切分"到"标准布局"的取舍，体现了分布式训练中分片粒度与加载通用性的权衡。
- **QAT 的配方化表达**：将量化策略参数化为表格化算子行，是配置驱动训练系统的典型设计。
- **MFU 估计作为一等公民**：把性能指标内置进仓库，而非依赖外部脚本，表明项目正走向工程化的性能基线管理。
- **AI 辅助协作痕迹**：多条提交带有 Cursor 协作署名，反映仓库已引入智能体参与开发流程。

## 5. 基于项目背景对发展的影响

结合 README 中"Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo"的定位，这批提交共同推动项目从"能训练"向"高效、规范、可组合地训练"演进：底层算子与 MFU 度量强化了**规模化性能**，HF 布局与 QAT 配方行强化了**通用性与可组合性**，而破坏性简化则强化了**体系一致性**。三者合力降低了新模型、新模态接入配方库的边际成本，使 VeOmni 作为分布式训练配方中心的长期可维护性和生态吸引力进一步增强。

## 详细提交记录

### [a891630](https://github.com/ByteDance-Seed/VeOmni/commit/a891630cb00bc30ff09202928821d614e0d8d818)

- **作者**: LeoCristallo
- **时间**: 2026-11-12T11:34:11Z
- **提交信息**: [ops, perf] refactor: use N-fast compact grouped-GEMM traversal (#1459)

### [cb4558f](https://github.com/ByteDance-Seed/VeOmni/commit/cb4558f421a62f38ab24adb88fb4dcc741d45c8e)

- **作者**: Zeren Chen
- **时间**: 2026-11-12T08:58:21Z
- **提交信息**: [omni, model, ckpt, docs] feat: support Bagel HF checkpoint layout in SeedOmni (#1456)

Co-authored-by: Cursor <cursoragent@cursor.com>

### [e8978f5](https://github.com/ByteDance-Seed/VeOmni/commit/e8978f59f97b076f9950dc7943c92b987e164868)

- **作者**: Coach257
- **时间**: 2026-11-12T08:21:06Z
- **提交信息**: [BREAKING][ckpt, docs] refactor: drop the pre-split checkpoint resume loader (#1437)

### [f71831a](https://github.com/ByteDance-Seed/VeOmni/commit/f71831aa25364ded354636289c5164424133ba64)

- **作者**: Coach257
- **时间**: 2026-11-12T08:13:37Z
- **提交信息**: [model, ops] refactor: replace qat_implementation with per-family QAT op rows (#1414)

Co-authored-by: Cursor <cursoragent@cursor.com>

### [d6fdd53](https://github.com/ByteDance-Seed/VeOmni/commit/d6fdd53f6c4d1df984cf94556247114b3306d0f2)

- **作者**: Obser
- **时间**: 2026-11-12T07:18:45Z
- **提交信息**: [perf] feat: add MFU estimation for MiniMax-H3 (#1425)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-11-13
**监控日期**: 2026-11-12
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 3003
- **最后更新**: 2026-11-12T11:45:53Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 3
- **主要提交者**: Bilang ZHANG, Yang Yong (雍洋), Musisoul

## AI分析总结

## LightX2V 昨日提交分析（共6条）

### 1. 主要更新类型
- **性能优化**（占主导）：动态编译热身修复、RMSNorm融合恢复、AdaLN缓存机制改进
- **功能集成**：LightX2V与ComfyUI的统一集成
- **重构**：AdaLN缓存设置简化、因果示例与配置整理
- **Bug修复**：动态编译的热身（warmup）问题

### 2. 关键变更点与项目方向的关系
- **ComfyUI统一集成（#1689）** 是本轮最大功能更新，标志着LightX2V从独立推理框架向**生态扩展**迈出关键一步，使用户能在ComfyUI工作流中直接调用LightX2V的轻量化推理能力，与README定位的"轻量视频生成推理框架"高度契合。
- **h3模型系列的集中优化**（#1697-#1701）表明团队正围绕MiniMax H3等模型进行深度性能调优，包括AdaLN缓存机制的更新与简化，这直接服务于框架核心的**推理效率提升**目标。
- **编译优化（#1698, #1700）**：恢复RMSNorm算子融合与默认编译行为，修复动态编译热身问题，体现对**编译加速链路**稳定性的重视。

### 3. 对项目的影响和潜在意义
- **降低使用门槛**：ComfyUI集成使非开发者用户也能便捷使用LightX2V，有望扩大用户群体和社区贡献。
- **性能收益显著**：RMSNorm融合与AdaLN缓存优化直接减少推理延迟和显存占用，强化"轻量"这一核心卖点。
- **稳定性提升**：热身修复和配置整理减少了边缘情况下的运行异常，提升生产环境可靠性。

### 4. 值得关注的技术点
- **AdaLN缓存机制**的持续演进（更新→简化）：这是Transformer视频生成模型中自适应层归一化的缓存策略，直接影响多帧生成的一致性和速度，其简化可能意味着发现了更优雅的实现方式。
- **动态编译热身问题**：反映了PyTorch 2.x动态编译（torch.compile）在视频推理场景下的典型坑点，修复经验对同类项目有参考价值。
- **算子融合策略**：RMSNorm融合的恢复说明团队在精度与速度间做了权衡验证，最终确认融合方案可行。

### 5. 对项目发展的整体影响
这批提交体现了LightX2V在两个维度的同步推进：**纵向深化**（对h3等模型的推理性能持续压榨，包括编译、缓存、融合多层面优化）和**横向扩展**（通过ComfyUI集成触达更广泛的AI创作社区）。前者巩固了框架在视频生成推理领域的技术壁垒，后者则为项目的生态繁荣奠定了基础。README中强调的"轻量"理念通过这些性能优化得到了实质性的落地支撑，而ComfyUI集成则让这一轻量优势能被更多创作者实际体验到，形成了"性能增强→生态扩展→用户增长"的良性循环，对项目长期发展具有积极而深远的意义。

## 详细提交记录

### [3aebc7f](https://github.com/ModelTC/LightX2V/commit/3aebc7f885f84e2f3c4276617caf669f4e858326)

- **作者**: Bilang ZHANG
- **时间**: 2026-11-12T10:45:48Z
- **提交信息**: chore(h3): tidy causal examples and configs (#1701)

Co-authored-by: zhangbilang <2045966653@qq.com>

### [542448f](https://github.com/ModelTC/LightX2V/commit/542448fb6e95e423bfa8c6c91d36b7538b18547d)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-11-12T09:07:17Z
- **提交信息**: Fix warmup for dynamic compile (#1700)

### [5c5a8c8](https://github.com/ModelTC/LightX2V/commit/5c5a8c8e98ebf8a6e3cfac746cb2fdfd8d03ff4f)

- **作者**: Bilang ZHANG
- **时间**: 2026-11-12T07:03:19Z
- **提交信息**: refactor(h3): simplify AdaLN cache setup (#1699)

### [0a0085b](https://github.com/ModelTC/LightX2V/commit/0a0085b13c629811a6a24b215cc72fec8a614fab)

- **作者**: Musisoul
- **时间**: 2026-11-12T06:28:42Z
- **提交信息**: Unified Integration of LightX2V with ComfyUI (#1689)

### [911de05](https://github.com/ModelTC/LightX2V/commit/911de057dec31f55a298cdc2aa42694e5b20b9e9)

- **作者**: Bilang ZHANG
- **时间**: 2026-11-12T06:18:16Z
- **提交信息**: `perf(h3): restore RMSNorm fusion and default compile behavior` (#1698)

### [d5e8d53](https://github.com/ModelTC/LightX2V/commit/d5e8d5399988f5f5599337be64ef9b7d3c81cf8f)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-11-12T05:34:01Z
- **提交信息**: update adaln cache for minimax h3 video and image (#1697)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-11-13
**监控日期**: 2026-11-12
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2334
- **最后更新**: 2026-11-12T16:30:26Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-11-13
**监控日期**: 2026-11-12
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6915
- **最后更新**: 2026-11-13T02:31:38Z

## 提交统计

- **昨日提交总数**: 36
- **提交者数量**: 17
- **主要提交者**: Yechan Kim, feih-nv, Ka-Hyun Nam

## AI分析总结

# FlashInfer 昨日 36 个提交合并分析总结

## 一、主要更新类型

昨日提交以 **Bug 修复** 为最大类别，辅以**性能优化**、**功能新增**与**发布生态加固**，重心集中在 Blackwell/Rubin 架构（SM100/SM103/SM107）上的 MoE、注意力与量化内核。其中最突出的是围绕 PDL（Programmatic Dependent Launch）的高优先级正确性修复。

## 二、关键变更

**PDL 数据竞争修复**：DeepSeek-V3 融合路由内核（#9341）原使用裸 `asm volatile("griddepcontrol.wait;")` 等待生产者网格，缺少 `"memory"` clobber，编译器可将全局加载调度到等待指令之前，导致 PDL 默认开启时读到上一内核未写完的数据。修复改用带 clobber 的 `cudaGridDependencySynchronize()`，并以 `cudaTriggerProgrammaticLaunchCompletion()` 对称替换 `launch_dependents`。同类问题也修复于 `cake_muse_spark_norm_backend` 的 gated residual RMSNorm mode 0/1 路径（#9359），竞争发生在等待之后才读取分支条件，覆盖 M ≤ 128 的三种架构路径，并附 GB300/B200/R200 多架构、CUDA graph + PDL 多启动模式的性能对照表。

**性能优化**：Blackwell MSA 稀疏 prefill 仅访问选中 KV 块，长前缀提速 5–10 倍；Gated Residual RMSNorm 经 PDL 路由重切获 6.7%–16.5% 加速；StepFun MoE 改用常驻网格调度，小 token 场景提速约 5.7%；MegaMoE FP8 引入自动调优替代硬编码配置。

**正确性修复**：修复 `fused_topk_deepseek` sigmoid 数值问题（logits ≤ -18 时路由全零，#9393）、KDA prefill NaN 跨序列污染、MXFP8 E8M0 scale 为零时的置零、MegaMoE TMEM lane 越界，以及 MoE 的 PDL 时序竞态、零 token 启动失败、共享内存脏槽位等隐蔽错误（部分移植自 TensorRT-LLM）。

**功能新增与生态**：新增批量不变 BF16 MegaMoE EP 内核，workspace 过滤使临时内存峰值从 530MB 降至 12MB；新增 DeepSeek-V4 NVFP4 稀疏 MLA prefill 与 FP8 per-(token,head) KV 量化写侧算子；SM100 D256 paged GQA 纳入 auto 后端，SM120 获专属 mega_gate 后端；恢复 BGMV 旧 API 为带弃用警告的别名；修复轮子打包缺失 `build.json` 与 `csrc/` 的问题；支持 Windows 原生构建；恢复 autotuner 缓存键一致性以消除 vLLM 侧绕过方案。

## 三、项目影响

正确性修复消除了静默错误与延迟暴露的 CUDA 故障，显著增强生产可靠性；内存与吞吐优化直接改善大规模推理成本；低精度路径（NVFP4、MXFP8、FP8 KV）的完善对齐业界低比特化趋势；API 弃用策略与打包修复维护了 vLLM、SGLang、TensorRT-LLM 等下游生态稳定。项目在积极采纳 PDL 压低延迟的同时，正在建立严格的内存正确性审查，防止"默认开启的优化反而引入数据竞争"。整体呈现从"追求性能"向"跑得快、跑得对、易维护"的成熟化演进，巩固了其作为推理框架核心算子依赖的地位。

## 四、技术关注点

- **PDL 与内存语义**：内嵌汇编缺少 `"memory"` clobber 会让编译器自由重排内存访问与同步；`griddepcontrol.launch_dependents` 非内存屏障，需先 `__syncthreads()` + `__threadfence()`，且首个线程触发即全局生效；wait 与 launch_dependents 需成对升级为 CUDA 内置 API 以保持语义对称。
- **系统性排查**：`norm.cuh`、`sampling.cuh`、`pos_enc.cuh`、`trtllm/fmha/lse.cuh` 等仍存在相同的裸 `griddepcontrol.wait` 模式，同类问题横跨 Norm、采样、位置编码等模块，需系统性清理而非逐个打补丁。
- **TMEM 生命周期**：`tcgen05.dealloc` 不清理数据，需用命名 barrier 显式排序以消除对 CTA 占用率的隐式依赖。
- **数值精度与验证**：tanh 形式 sigmoid 在 FP32 下的截断边界分析；算术指纹 + Lean 模型验证内核算术契约；对照表区分"同内核"与"变内核"行的严谨性能回归验证流程。

## 五、整体影响

这些工作系统性推进了 FlashInfer 在 MoE、稀疏注意力、量化算子矩阵上的能力版图，尤其巩固了对 DeepSeek-V3/V4、StepFun MoE 等前沿模型工作负载的支持深度，为下一代大模型推理基础设施奠定了基础。

## 详细提交记录

### [60bd3e6](https://github.com/flashinfer-ai/flashinfer/commit/60bd3e6e0cbb4c1363dd0122627678f62ecc04a0)

- **作者**: Yanqin Zhai
- **时间**: 2026-11-12T23:45:47Z
- **提交信息**: Add batch-invariant BF16 MegaMoE for Blackwell and Rubin (#9417)

<!-- .github/pull_request_template.md -->

## 📌 Description

Add opt-in batch-invariant BF16 MegaMoE EP on SM100, SM103 and SM107
while reusing the existing kernel implementation.

- Pin the ordered K16 accumulation, SwiGLU and slot-ordered
finalization. Validate explicit knobs, autotune candidates and cached
plans against the same arithmetic contract; admit up to 72
tile/scheduler/carrier plans after shape and shared-memory filtering.
- Expose architecture-specific arithmetic fingerprints and a Lean model
of the ordered trace. Early and late routing-weight placement remain
separate numerical classes.
- Fix single-CTA atomic-counter publication to use a warp shuffle and
the existing CTA consumer pipeline; reserve the DSMEM asynchronous-store
protocol for multi-CTA clusters.
- Apply selected geometry before workspace admission, normalize
equivalent FP32 clamps, and stream fingerprint hashing with local
interning. Existing v1 receipts remain unchanged; the measured
large-shape temporary-memory peak drops from about 530 MB to 12 MB.

## 🔍 Related Issues

Part of #9009 (batch-invariant kernel tracking).

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
Reason: Targeted tests cover the changed backend, policy and arithmetic
specification; full-scope CI is not requested.

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust):
`tests/moe_ep/test_bf16_megamoe_batch_invariant.py
tests/moe_ep/test_bf16_megamoe_spec.py
tests/batch_invariant/test_megamoe_lean.py`

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

Validation on revision `1db237313`:

- CPU policy/configuration/fingerprint tests: 280 passed, with CUDA
devices hidden.
- Lean conformance and axioms checks: 5 passed.
- SM100 native `sm_100a` GPU regression (`--full`): 109 passed, 2
expected skips requiring multi-rank torchrun (90 sequential cases plus
19 parallel cases; disjoint shards).
- Compute Sanitizer memcheck: 10 scheduler regressions passed, 0 errors,
including one-CTA atomic paths, static/two-CTA controls and CUDA Graph
replay.
- Changed-file pre-commit hooks passed. All 90 golden v1 fingerprints
are preserved.

The public CI matrix has no SM100/SM103/SM107 lane, so its H100-only GPU
skips are expected and do not establish hardware coverage. Internal
Blackwell CI should run the scoped targets above, preferably on a CUDA
13 lane. SM103, SM107 and multi-rank EP were not rerun in this
review-fix revision.

The guarantee assumes fixed input values, weights, ordered routes,
architecture and software stack. The Lean proofs cover the modeled
arithmetic trace and batch transformations; device synchronization and
compiler lowering require GPU validation. SM107 requires native
`sm_107a` compilation, oversized shared-memory launcher support and
Rubin-aware NCCL (previously validated with NCCL 2.32.6).

Developed and reviewed with assistance from Codex.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added optional batch-invariant BF16 MegaMoE execution on supported
SM100, SM103, and SM107 hardware, with validated tile and scheduling
choices.
* For supported configurations, fixed inputs and routing produce
bitwise-consistent outputs across batch-size changes.
* Added arithmetic fingerprints to identify compatible configurations
and distinguish tuning records.
* Added validation for eligible batch-invariant candidates in automatic
configuration and selection.
* **Documentation**
* Expanded guidance on supported configurations, hardware requirements,
tuning, and the scope and limitations of batch-invariant output
guarantees.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [6a80e9d](https://github.com/flashinfer-ai/flashinfer/commit/6a80e9d76e0e0dab2f6bbdc589cab7f1155bd784)

- **作者**: Zihao Ye
- **时间**: 2026-11-12T22:57:28Z
- **提交信息**: perf(cake_stepfun_moe): resident-grid routed FC1 / FC2 programs for the StepFun fused MoE (sm_100a, sm_103a) (#7203)

The Cake StepFun SwiGLU fused MoE
(`flashinfer.experimental.cake_stepfun_moe`) has five precision
variants: bf16, per-tensor fp8, mxfp8, nvfp4, and per-token nvfp4 (nvfp4
with bf16 FC1 output and a per-token scale). This PR runs the bf16 FC1
programs of tiles 8/16/32, every bf16 FC2 program, the fp8 FC2 programs
of tiles 8/16/32/128/256 and the mxfp8 FC2 programs of tiles 8/16/32 on
a resident grid instead of one CTA per output tile. For tiles 8/16/32,
one resident CTA per SM claims tiles from a work counter that the kernel
re-arms itself; the larger tiles (bf16 FC2 64/128/256 and fp8 FC2
128/256) run as one resident two-CTA cluster per SM pair. The baseline
is the previous Cake version on FlashInfer main (commit 1bdba8725). The
largest gains are at 8 tokens, up to 1.0578x (mxfp8) on GB300 and
1.0493x on B200. At 512 tokens and above the results are close to
parity; the largest GB300 slowdown is fp8 at 1024 tokens (0.9948x).

The nvfp4 and per-token nvfp4 variants and the rest of the package
(other tiles, routing, requantization, finalize) are regenerated from
the current kernel sources and keep their previous launch; the family
ships on sm_100a and sm_103a.

**NVIDIA GB300, sm_103a, CUDA 13.4.** Whole forward captured as one CUDA
graph (H 4096, I 1536, 64 experts, top-8, SwiGLU limit 7, uniform
routing, warm L2); latencies are medians over 6 interleaved processes
per side, speedup is their ratio, and [min, max] is the per-process
speedup range.

| precision | tokens | previous Cake (µs) | this PR (µs) | speedup
[per-process min, max] |
|---|---:|---:|---:|---:|
| bf16 | 8 | 211.35 | 209.63 | 1.0082x [1.0080, 1.0085] |
| bf16 | 64 | 349.99 | 349.39 | 1.0017x [1.0012, 1.0019] |
| bf16 | 512 | 377.89 | 376.97 | 1.0025x [1.0018, 1.0074] |
| bf16 | 1024 | 408.87 | 406.50 | 1.0058x [0.9938, 1.0083] |
| bf16 | 2048 | 585.13 | 586.39 | 0.9978x [0.9970, 1.0035] |
| fp8 | 8 | 114.70 | 110.15 | 1.0413x [1.0386, 1.0428] |
| fp8 | 64 | 188.09 | 188.06 | 1.0001x [0.9996, 1.0006] |
| fp8 | 512 | 208.76 | 209.11 | 0.9983x [0.9967, 1.0001] |
| fp8 | 1024 | 230.30 | 231.50 | 0.9948x [0.9919, 0.9983] |
| fp8 | 2048 | 331.48 | 332.48 | 0.9970x [0.9933, 1.0089] |
| mxfp8 | 8 | 119.12 | 112.61 | 1.0578x [1.0567, 1.0587] |
| mxfp8 | 64 | 197.65 | 191.92 | 1.0299x [1.0293, 1.0304] |
| mxfp8 | 512 | 220.14 | 220.31 | 0.9992x [0.9988, 0.9995] |
| mxfp8 | 1024 | 248.11 | 247.31 | 1.0032x [0.9988, 1.0107] |
| mxfp8 | 2048 | 363.32 | 362.87 | 1.0012x [0.9882, 1.0042] |
| nvfp4 | 8 | 71.38 | 71.48 | 0.9985x [0.9976, 0.9996] |
| nvfp4 | 64 | 112.90 | 112.57 | 1.0030x [1.0026, 1.0034] |
| nvfp4 | 512 | 135.38 | 135.32 | 1.0005x [1.0000, 1.0013] |
| nvfp4 | 1024 | 169.17 | 167.82 | 1.0080x [1.0074, 1.0084] |
| nvfp4 | 2048 | 229.84 | 229.16 | 1.0030x [1.0021, 1.0039] |
| nvfp4 (per-token) | 8 | 77.34 | 77.46 | 0.9985x [0.9966, 0.9998] |
| nvfp4 (per-token) | 64 | 119.04 | 119.25 | 0.9982x [0.9968, 0.9991] |
| nvfp4 (per-token) | 512 | 145.78 | 145.72 | 1.0004x [0.9999, 1.0007] |
| nvfp4 (per-token) | 1024 | 201.24 | 200.29 | 1.0047x [1.0043, 1.0054]
|
| nvfp4 (per-token) | 2048 | 271.81 | 272.08 | 0.9990x [0.9984, 0.9995]
|

**NVIDIA B200, sm_100a, CUDA 13.4.** Same measurement with 9 interleaved
processes per side. Rows at 512 tokens and above are noise-dominated:
the GPU hits its power cap there (SM clock 1.03-1.97 GHz), and an A/A
run of the previous version against itself varies 0.89-1.09 per process,
about as wide as the A/B range (0.86-1.11).

| precision | tokens | previous Cake (µs) | this PR (µs) | speedup
[per-process min, max] |
|---|---:|---:|---:|---:|
| bf16 | 8 | 215.24 | 213.99 | 1.0058x [1.0042, 1.0060] |
| bf16 | 64 | 363.83 | 362.25 | 1.0044x [1.0021, 1.0093] |
| bf16 | 512 | 432.86 | 428.84 | 1.0094x [0.9589, 1.0710] |
| bf16 | 1024 | 510.27 | 506.21 | 1.0080x [0.9516, 1.0413] |
| bf16 | 2048 | 755.02 | 759.41 | 0.9942x [0.9664, 1.0585] |
| fp8 | 8 | 116.76 | 112.71 | 1.0359x [1.0355, 1.0363] |
| fp8 | 64 | 193.08 | 192.70 | 1.0020x [0.9968, 1.0030] |
| fp8 | 512 | 226.80 | 219.24 | 1.0345x [0.9782, 1.0645] |
| fp8 | 1024 | 285.60 | 284.78 | 1.0029x [0.8789, 1.0839] |
| fp8 | 2048 | 424.13 | 425.87 | 0.9959x [0.9182, 1.0127] |
| mxfp8 | 8 | 121.46 | 115.75 | 1.0493x [1.0468, 1.0504] |
| mxfp8 | 64 | 202.01 | 196.11 | 1.0301x [1.0229, 1.0309] |
| mxfp8 | 512 | 233.60 | 238.89 | 0.9779x [0.9690, 1.0041] |
| mxfp8 | 1024 | 301.20 | 310.70 | 0.9694x [0.8553, 1.1084] |
| mxfp8 | 2048 | 472.33 | 467.86 | 1.0096x [0.9456, 1.0580] |
| nvfp4 | 8 | 73.75 | 73.74 | 1.0002x [0.9991, 1.0012] |
| nvfp4 | 64 | 118.07 | 117.90 | 1.0014x [1.0002, 1.0024] |
| nvfp4 | 512 | 143.50 | 142.48 | 1.0071x [1.0007, 1.0146] |
| nvfp4 | 1024 | 181.90 | 182.80 | 0.9951x [0.9392, 1.0441] |
| nvfp4 | 2048 | 279.29 | 278.12 | 1.0042x [0.9612, 1.0621] |
| nvfp4 (per-token) | 8 | 79.90 | 79.66 | 1.0030x [1.0024, 1.0036] |
| nvfp4 (per-token) | 64 | 124.45 | 123.98 | 1.0038x [1.0027, 1.0061] |
| nvfp4 (per-token) | 512 | 154.62 | 153.69 | 1.0061x [0.9966, 1.0116] |
| nvfp4 (per-token) | 1024 | 215.08 | 209.08 | 1.0287x [0.9761, 1.0682]
|
| nvfp4 (per-token) | 2048 | 322.60 | 324.10 | 0.9954x [0.9872, 1.0189]
|


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added resident-grid scheduling for eligible MoE programs, alongside
existing tile-based scheduling.
* **Bug Fixes**
* Improved validation of input limits and tensor descriptors, with
clearer errors for invalid dimensions and arithmetic overflow.
  * Preserved work-counter state safely across CUDA graph replays.
* **Documentation**
  * Clarified grid sizing and work-counter requirements.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [b2ba832](https://github.com/flashinfer-ai/flashinfer/commit/b2ba83286a96c8b54ab80844768be37b41c57fb9)

- **作者**: Zihao Ye
- **时间**: 2026-11-12T22:56:44Z
- **提交信息**: fix(cake_mega_moe): address each warp's own TMEM lane quarter in the BF16 rank-major FC1/FC2 epilogues (#6890)

**Issue.** The SM100 BF16 rank-major MegaMoE source bundle
(`flashinfer/moe_ep/kernel_src/blackwell_bf16_rank_major/src/flashinfer_blackwell_moe_ep_layer_sm100.cu`)
runs the epilogues of `kernel_rank_major_exact_fc1_swiglu_v1` and
`kernel_trtllm_moe_bmm_tile_n64_fc2_bf16` on warps 0-3, and each warp
loads its accumulator rows with two `tcgen05.ld.16x256b`. A `tcgen05.ld`
from warp *w* of a warpgroup may access only TMEM lanes 32·(w mod 4) …
32·(w mod 4)+31, the lane being bits 31:16 of the address (PTX ISA,
tcgen05 memory-access restrictions). Both loads addressed lane 0 and
lane 16 from every warp, so warps 1-3 issued out-of-quarter accesses.
GB300 serves such an access from the warp's own quarter, so results were
correct, but the code relied on behaviour PTX leaves undefined.

**Change.** The four loads add the warp's lane base, `(tid & 96) << 16`;
`manifest.json` carries the new `source_sha256`. The other kernels of
the bundle are unchanged (with nvcc 13.4.92, 14 of the 16 kernels have
SASS identical to main's on each of sm_100a and sm_107a; the two changed
kernels differ only in the lane-base arithmetic, alignment NOPs and a
few equivalent register moves).

**Tests** (after merging current main). On 8× B200 (CUDA 13.4), `bash
tests/moe_ep/run_tests.sh bf16-rank-major`: 52 passed on each of the 8
ranks. `tests/cpu/moe_ep/test_bf16_rank_major_cuda_backend_cpu.py` and
`test_bf16_rank_major_cuda_session_cpu.py`: 88 passed. Outputs equal
main bit for bit for T = 1/8/32/64/128 rows per rank, in eager forward
with both routings and in CUDA-graph replay with one routing (120
rank-case digests, 840 comparisons over four 8-rank runs per side).
Whole-forward CUDA-graph time, this branch / main: 0.999–1.000. An
eight-GPU R200 run has not been done.

**Timing** (earlier measurement) of the same epilogue change in the
standalone FC1/FC2 kernels of this layer (NVIDIA GB300, sm_103a, CUDA
13.3; median over 3 ABBA rounds in one process, fresh inputs, cold L2;
"cooled" adds an idle delay before every call):

| kernel | before (ms) | after (ms) | change | change, cooled |
|---|---|---|---|---|
| FC1 gather + SwiGLU (two shapes) | 0.2805 | 0.2805 | −0.01% / +0.01% |
−0.02% / +0.02% |
| FC2 tile-N 64 (six shapes) | 0.177–0.204 | 0.177–0.204 | +0.02% …
+0.05% | −0.03% … +0.09% |



<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Updated memory access patterns in affected Blackwell BF16
Mixture-of-Experts operations. This changes how tensor data is accessed
during select processing steps, while leaving other reported behavior
unchanged. The adjustment applies to two operations in the processing
flow; no changes to user-facing controls or capabilities were reported.
Users should see the updated behavior when running workloads that use
these operations.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [ca4b857](https://github.com/flashinfer-ai/flashinfer/commit/ca4b8578cccd8d4de6f63acbaadf8cc89b0fcbc8)

- **作者**: Zihao Ye
- **时间**: 2026-11-12T22:56:20Z
- **提交信息**: fix(cake_dsv4): FP8 route refuses widths over 1152; faster bodies for low-head and SGLang decode rows (#9049)

The Cake DeepSeek-V4 sparse MLA route (`backend="cake"`) runs FP8 rows
on five FP8 bodies (the persistent body in its uniform- and lane-gather
programs, the M64 body, the low-head prefill producer, the one-partition
producer and the H64 cluster body), plus the shape-locked source-exact
programs. This PR changes the route for these rows:

- FP8 rows of 8, 16 and 32 heads with `max_q_len < 257` and 385-1152
sparse slots raised before this PR. They now run the M64 body. On
SM100/SM103, 32-head rows instead run the persistent body while its two
CTAs per token fit one wave.
- 8-head prefill rows (`max_q_len >= 257`) move from the low-head
prefill producer to the M64 body.
- 8/16/32-head decode rows past one wave move to the M64 body on
SM100/SM103: SWA-only rows (from the low-head prefill producer, as SM107
already did) and compressed rows of at most 384 slots (from the
one-partition producer). SM107 runs the latter on the M64 body at every
token count.
- On SM103, 64-head decode rows of 257-383 slots and at most 12 tokens
move from the H64 cluster body to the persistent body, and 128-head
SWA-only decode launches with at most 2 query rows per request keep the
uniform-gather program at every row count.
- Every FP8 row wider than 1152 slots now raises one `ValueError` from
the route.

GB300 (sm_103a, 152 SMs), CUDA 13.4, cold L2, cooled median µs. The
decode rows of the last four tables are one-token requests, as SGLang
passes them (batch = tokens, `max_q_len` 1).

8 heads, two ragged requests (T/3 + 2T/3): low-head prefill producer →
M64 body.

| tokens | width 128 | width 640 (page 64) | width 640 (page 2) | width
1152 (page 2) |
|---|---|---|---|---|
| 512 | 31.65 → 11.44 (2.77x) | 88.14 → 40.74 (2.16x) | 88.10 → 40.88
(2.16x) | 145.93 → 70.05 (2.08x) |
| 2048 | 119.12 → 29.07 (4.10x) | 338.80 → 133.90 (2.53x) | 338.75 →
133.82 (2.53x) | 561.84 → 234.46 (2.40x) |
| 8192 | 465.47 → 100.16 (4.65x) | 1344.32 → 500.74 (2.68x) | 1344.08 →
500.50 (2.69x) | 2240.03 → 909.49 (2.46x) |

8, 16 and 32 heads, 640 and 1152 slots: decode rows that raised before
this PR. The baseline is the low-head prefill producer, the other Cake
body that runs them.

| heads | width | batch x q_len | baseline | this PR | speedup |
|---|---|---|---|---|---|
| 8 | 640 | 1 x 1 | 13.25 | 13.65 (M64) | 0.97x |
| 8 | 640 | 16 x 1 | 13.28 | 13.28 (M64) | 1.00x |
| 8 | 640 | 64 x 1 | 14.43 | 14.29 (M64) | 1.01x |
| 8 | 640 | 128 x 1 | 27.04 | 15.60 (M64) | 1.73x |
| 8 | 640 | 256 x 1 | 51.26 | 25.09 (M64) | 2.04x |
| 8 | 640 | 16 x 4 | 13.66 | 13.62 (M64) | 1.00x |
| 8 | 640 | 64 x 4 | 50.50 | 23.55 (M64) | 2.14x |
| 8 | 1152 | 1 x 1 | 21.06 | 19.90 (M64) | 1.06x |
| 8 | 1152 | 64 x 1 | 22.62 | 20.93 (M64) | 1.08x |
| 8 | 1152 | 256 x 1 | 84.16 | 39.81 (M64) | 2.11x |
| 16 | 640 | 1 x 1 | 12.99 | 13.28 (M64) | 0.98x |
| 16 | 640 | 64 x 1 | 14.32 | 14.24 (M64) | 1.01x |
| 16 | 640 | 128 x 1 | 26.72 | 15.78 (M64) | 1.69x |
| 16 | 640 | 256 x 1 | 51.36 | 25.25 (M64) | 2.03x |
| 16 | 640 | 64 x 4 | 50.54 | 23.46 (M64) | 2.15x |
| 16 | 1152 | 1 x 1 | 21.15 | 20.16 (M64) | 1.05x |
| 16 | 1152 | 64 x 1 | 22.69 | 21.10 (M64) | 1.08x |
| 16 | 1152 | 128 x 1 | 43.26 | 22.78 (M64) | 1.90x |
| 16 | 1152 | 256 x 1 | 84.40 | 39.98 (M64) | 2.11x |
| 16 | 1152 | 64 x 4 | 83.52 | 37.68 (M64) | 2.22x |
| 32 | 640 | 1 x 1 | 13.02 | 10.21 (persistent) | 1.28x |
| 32 | 640 | 16 x 1 | 13.44 | 10.29 (persistent) | 1.31x |
| 32 | 640 | 64 x 1 | 14.46 | 11.65 (persistent) | 1.24x |
| 32 | 640 | 128 x 1 | 26.98 | 15.84 (M64) | 1.70x |
| 32 | 640 | 256 x 1 | 51.84 | 25.63 (M64) | 2.02x |
| 32 | 640 | 16 x 4 | 13.80 | 11.20 (persistent) | 1.23x |
| 32 | 640 | 64 x 4 | 51.01 | 23.73 (M64) | 2.15x |
| 32 | 1152 | 1 x 1 | 21.31 | 13.14 (persistent) | 1.62x |
| 32 | 1152 | 16 x 1 | 21.76 | 13.36 (persistent) | 1.63x |
| 32 | 1152 | 64 x 1 | 22.72 | 15.09 (persistent) | 1.51x |
| 32 | 1152 | 128 x 1 | 43.46 | 22.74 (M64) | 1.91x |
| 32 | 1152 | 256 x 1 | 84.96 | 40.51 (M64) | 2.10x |
| 32 | 1152 | 16 x 4 | 22.19 | 14.66 (persistent) | 1.51x |
| 32 | 1152 | 64 x 4 | 84.11 | 38.16 (M64) | 2.20x |

8, 16 and 32 heads, SWA only (width 128), past one wave: low-head
prefill producer → M64 body.

| heads | tokens | before | after | speedup |
|---|---|---|---|---|
| 8 | 77 | 10.80 | 7.28 | 1.48x |
| 8 | 88 | 11.30 | 7.49 | 1.51x |
| 8 | 104 | 11.50 | 7.86 | 1.46x |
| 8 | 128 | 11.71 | 8.05 | 1.45x |
| 8 | 256 | 21.20 | 10.70 | 1.98x |
| 16 | 77 | 10.69 | 7.33 | 1.46x |
| 16 | 88 | 11.14 | 7.49 | 1.49x |
| 16 | 104 | 11.47 | 7.73 | 1.48x |
| 16 | 128 | 11.74 | 8.05 | 1.46x |
| 16 | 256 | 21.23 | 10.69 | 1.99x |
| 32 | 77 | 10.74 | 7.49 | 1.43x |
| 32 | 88 | 11.30 | 7.58 | 1.49x |
| 32 | 104 | 11.57 | 7.87 | 1.47x |
| 32 | 128 | 11.82 | 8.08 | 1.46x |
| 32 | 256 | 21.49 | 10.90 | 1.97x |

8, 16 and 32 heads, compressed cache, widths up to 384, past one wave:
one-partition producer → M64 body.

| heads | width (live) | tokens | before | after | speedup |
|---|---|---|---|---|---|
| 8 | 192 (192) | 128 | 17.39 | 9.57 | 1.82x |
| 8 | 192 (192) | 256 | 30.37 | 13.87 | 2.19x |
| 8 | 256 (256) | 128 | 15.26 | 9.22 | 1.66x |
| 8 | 256 (256) | 256 | 29.04 | 13.78 | 2.11x |
| 8 | 320 (256) | 128 | 19.01 | 9.31 | 2.04x |
| 8 | 320 (256) | 256 | 33.62 | 13.97 | 2.41x |
| 8 | 320 (320) | 128 | 19.94 | 11.62 | 1.72x |
| 8 | 320 (320) | 256 | 35.38 | 17.90 | 1.98x |
| 8 | 384 (384) | 128 | 17.62 | 11.79 | 1.49x |
| 8 | 384 (384) | 256 | 33.55 | 17.63 | 1.90x |
| 16 | 192 (192) | 128 | 17.50 | 9.57 | 1.83x |
| 16 | 192 (192) | 256 | 30.54 | 14.06 | 2.17x |
| 16 | 256 (256) | 128 | 15.23 | 9.22 | 1.65x |
| 16 | 256 (256) | 256 | 29.14 | 13.87 | 2.10x |
| 16 | 320 (256) | 128 | 19.01 | 9.36 | 2.03x |
| 16 | 320 (256) | 256 | 33.71 | 14.00 | 2.41x |
| 16 | 320 (320) | 128 | 20.26 | 11.62 | 1.74x |
| 16 | 320 (320) | 256 | 35.57 | 17.84 | 1.99x |
| 16 | 384 (384) | 128 | 17.68 | 11.79 | 1.50x |
| 16 | 384 (384) | 256 | 33.74 | 17.79 | 1.90x |
| 32 | 192 (192) | 128 | 17.89 | 9.74 | 1.84x |
| 32 | 192 (192) | 256 | 31.38 | 14.59 | 2.15x |
| 32 | 256 (256) | 128 | 15.65 | 9.33 | 1.68x |
| 32 | 256 (256) | 256 | 29.82 | 14.28 | 2.09x |
| 32 | 320 (256) | 128 | 19.34 | 9.38 | 2.06x |
| 32 | 320 (256) | 256 | 34.38 | 14.21 | 2.42x |
| 32 | 320 (320) | 128 | 20.46 | 11.81 | 1.73x |
| 32 | 320 (320) | 256 | 36.45 | 18.00 | 2.03x |
| 32 | 384 (384) | 128 | 18.02 | 11.86 | 1.52x |
| 32 | 384 (384) | 256 | 34.50 | 18.26 | 1.89x |

64 heads, widths 257-383, up to 12 tokens: H64 cluster body → persistent
body.

| width (live) | tokens | before | after | speedup |
|---|---|---|---|---|
| 320 (256) | 1 | 9.12 | 7.62 | 1.20x |
| 320 (256) | 4 | 8.90 | 7.52 | 1.18x |
| 320 (256) | 8 | 9.25 | 7.52 | 1.23x |
| 320 (256) | 12 | 9.31 | 7.58 | 1.23x |
| 320 (320) | 1 | 9.57 | 8.70 | 1.10x |
| 320 (320) | 4 | 9.38 | 8.35 | 1.12x |
| 320 (320) | 8 | 9.60 | 8.22 | 1.17x |
| 320 (320) | 12 | 9.73 | 8.37 | 1.16x |
| 260 (260) | 1 | 10.08 | 8.42 | 1.20x |
| 260 (260) | 4 | 9.73 | 8.48 | 1.15x |
| 260 (260) | 8 | 9.54 | 8.42 | 1.13x |
| 260 (260) | 12 | 9.74 | 8.48 | 1.15x |
| 288 (288) | 1 | 10.10 | 8.99 | 1.12x |
| 288 (288) | 4 | 9.79 | 8.53 | 1.15x |
| 288 (288) | 8 | 9.57 | 8.64 | 1.11x |
| 288 (288) | 12 | 9.84 | 8.64 | 1.14x |
| 352 (352) | 1 | 9.89 | 9.17 | 1.08x |
| 352 (352) | 4 | 9.57 | 8.53 | 1.12x |
| 352 (352) | 8 | 9.95 | 8.64 | 1.15x |
| 352 (352) | 12 | 10.02 | 8.77 | 1.14x |
| 380 (380) | 1 | 10.19 | 9.04 | 1.13x |
| 380 (380) | 4 | 9.78 | 8.46 | 1.16x |
| 380 (380) | 8 | 9.65 | 8.54 | 1.13x |
| 380 (380) | 12 | 9.95 | 8.72 | 1.14x |

128 heads, SWA only: lane-gather persistent program (its PDL-free twin
from 384 rows) → uniform-gather program.

| tokens | before | after | speedup |
|---|---|---|---|
| 128 | 11.58 | 11.17 | 1.037x |
| 192 | 14.40 | 14.37 | 1.002x |
| 256 | 17.26 | 16.91 | 1.021x |
| 320 | 20.27 | 19.81 | 1.023x |
| 383 | 22.38 | 21.47 | 1.042x |
| 384 | 22.66 | 21.70 | 1.044x |
| 512 | 27.09 | 26.91 | 1.007x |
| 640 | 32.30 | 31.60 | 1.022x |
| 768 | 36.75 | 36.22 | 1.015x |
| 1024 | 46.46 | 45.98 | 1.010x |
| 1536 | 65.57 | 64.96 | 1.009x |
| 2048 | 84.75 | 84.18 | 1.007x |

Cake also ships BF16 and NVFP4 KV routes for this operator, on sm_100a
and sm_103a; the FP8 route also ships on sm_107a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Expanded support for FP8 sliding-window and compressed-cache workloads
across decode, MTP, and prefill.
* Added support for more low-head decode and prefill shapes on supported
hardware, including additional SM103 cases.
* **Bug Fixes**
* Inputs exceeding the 1,152-slot FP8 sparse-width limit are now
rejected before launch.
* Improved handling of low-head decode and prefill inputs across
supported hardware.
* Invalid C128 top-k widths are rejected before launch without modifying
output.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [b86beb0](https://github.com/flashinfer-ai/flashinfer/commit/b86beb000b03f73855463a02a09939e89d3c15ca)

- **作者**: Zihao Ye
- **时间**: 2026-11-12T22:55:36Z
- **提交信息**: feat(cake_dsv4): NVFP4 sparse-MLA prefill for SM100/SM103 on a packed NVFP4 query (#6851)

## feat(cake_dsv4): NVFP4 sparse-MLA prefill for SM100/SM103 on a packed
NVFP4 query

This PR adds Cake NVFP4 prefill bodies to
`trtllm_batch_decode_sparse_mla_dsv4(..., backend="cake",
kv_cache_format="nvfp4")`: query-block bodies for 16/32 heads, per-token
builds for up to 64 heads, and a two-CTA body for 128 heads.

The prefill call takes the query already packed to the NVFP4 cache row
format, uint8 `[..., heads, 384]`. This mirrors the FP8 route, which
takes an E4M3 query. `flashinfer.mla.cake_dsv4_nvfp4_pack_query` packs a
BF16 query. A BF16 query still runs the decode family below 128 rows.

**Routing**

| heads | rows | build |
|---|---|---|
| 16 | SWA layer, T ≤ #SMs / ≤ 1024 / above | per-token
`tmem_v`+`early_gather` / query-block `breaks` / query-block |
| 32 | SWA layer, T ≤ #SMs / 8·blocks > 11·#SMs and T ≤ 512 / else |
per-token `tmem_v`+`early_gather` / query-block `late_claim` /
query-block |
| ≤ 32 | C4 / C128 layers | per-token `tmem_v` (`+early_gather` when T ≤
#SMs) |
| 33–64 | T ≤ #SMs / SWA / C4, C128 | per-token `early_gather` /
`q_prefetch` / `o_boxes` |
| 128 | ≤ 256 selected keys / more | two-CTA persistent / two-CTA
`v_unit_pairs` (sm_103a; sm_100a keeps persistent) |

**DSv4 attention time per forward**

GB300, CUDA graph, cooled. The NVFP4 call takes the pre-packed query;
the FP8 call takes an E4M3 query. Times are summed over the model's
layers.
- DSv4-Flash: 43 layers, 3 SWA + 20 C4 (128 + 512) + 20 C128.
- DSv4-Pro: 61 layers, assumed 1 SWA + 29 C4 (128 + 1024) + 31 C128 from
the `compress_ratios` pattern.
- Tables are in SGLang order. The FP8 baseline is the best Cake FP8
kernel for each layer.

| model, deployment | T | context | NVFP4 ms | Cake FP8 ms | NVFP4 / FP8
|
|---|---|---|---|---|---|
| Flash, DP attention (64 heads) | 2048 | 16K | 4.47 | 3.91 | 1.145 |
| Flash, DP attention (64 heads) | 2048 | 64K | 5.89 | 5.35 | 1.100 |
| Flash, DP attention (64 heads) | 2048 | 256K | 11.53 | no FP8 kernel |
NVFP4 only |
| Flash, DP attention (64 heads) | 8192 | 16K | 16.71 | 14.53 | 1.150 |
| Flash, DP attention (64 heads) | 8192 | 64K | 22.02 | 20.02 | 1.100 |
| Flash, DP attention (64 heads) | 8192 | 256K | 43.75 | no FP8 kernel |
NVFP4 only |
| Flash, TP4 (16 heads) | 2048 | 16K | 4.17 | 3.75 | 1.114 |
| Flash, TP4 (16 heads) | 2048 | 64K | 5.56 | 5.09 | 1.091 |
| Flash, TP4 (16 heads) | 2048 | 256K | 11.21 | no FP8 kernel | NVFP4
only |
| Flash, TP4 (16 heads) | 8192 | 16K | 15.88 | 14.09 | 1.128 |
| Flash, TP4 (16 heads) | 8192 | 64K | 20.80 | 19.16 | 1.085 |
| Flash, TP4 (16 heads) | 8192 | 256K | 42.70 | no FP8 kernel | NVFP4
only |
| Flash, TP8 (8 heads) | 2048 | 16K | 4.19 | 3.74 | 1.119 |
| Flash, TP8 (8 heads) | 2048 | 64K | 5.57 | 5.08 | 1.096 |
| Flash, TP8 (8 heads) | 2048 | 256K | 11.22 | no FP8 kernel | NVFP4
only |
| Flash, TP8 (8 heads) | 8192 | 16K | 16.04 | 14.05 | 1.141 |
| Flash, TP8 (8 heads) | 8192 | 64K | 20.88 | 19.11 | 1.092 |
| Flash, TP8 (8 heads) | 8192 | 256K | 42.72 | no FP8 kernel | NVFP4
only |
| Pro, TP1 (128 heads) | 2048 | 16K | 13.77 | 11.50 | 1.198 |
| Pro, TP1 (128 heads) | 2048 | 64K | 17.02 | 14.14 | 1.203 |
| Pro, TP1 (128 heads) | 2048 | 256K | 30.07 | no FP8 kernel | NVFP4
only |
| Pro, TP1 (128 heads) | 8192 | 16K | 53.42 | 43.69 | 1.223 |
| Pro, TP1 (128 heads) | 8192 | 64K | 65.72 | 53.79 | 1.222 |
| Pro, TP1 (128 heads) | 8192 | 256K | 117.91 | no FP8 kernel | NVFP4
only |

**Per layer** (µs; FP8 is the best Cake FP8 kernel):

| heads | layer | T | NVFP4 | Cake FP8 | NVFP4 / FP8 |
|---|---|---|---|---|---|
| 8 | swa | 2048 | 42.5 | 29.1 | 1.46 |
| 8 | swa | 8192 | 148.9 | 99.9 | 1.49 |
| 8 | c4flash | 2048 | 136.0 | 123.6 | 1.10 |
| 8 | c4flash | 8192 | 508.8 | 463.6 | 1.10 |
| 8 | c128-16k | 2048 | 67.0 | 59.1 | 1.13 |
| 8 | c128-16k | 8192 | 270.6 | 224.1 | 1.21 |
| 8 | c128-64k | 2048 | 135.9 | 126.1 | 1.08 |
| 8 | c128-64k | 8192 | 512.8 | 477.1 | 1.07 |
| 8 | c128-256k | 2048 | 418.7 | – | NVFP4 only |
| 8 | c128-256k | 8192 | 1604.8 | – | NVFP4 only |
| 16 | swa | 2048 | 20.8 | 29.5 | 0.70 |
| 16 | swa | 8192 | 58.2 | 101.1 | 0.58 |
| 16 | c4flash | 2048 | 137.3 | 123.7 | 1.11 |
| 16 | c4flash | 8192 | 514.0 | 464.0 | 1.11 |
| 16 | c128-16k | 2048 | 68.3 | 59.3 | 1.15 |
| 16 | c128-16k | 8192 | 271.5 | 225.2 | 1.21 |
| 16 | c128-64k | 2048 | 137.4 | 126.4 | 1.09 |
| 16 | c128-64k | 8192 | 517.2 | 479.0 | 1.08 |
| 16 | c128-256k | 2048 | 420.2 | – | NVFP4 only |
| 16 | c128-256k | 8192 | 1612.0 | – | NVFP4 only |
| 32 | swa | 2048 | 30.4 | 31.2 | 0.97 |
| 32 | swa | 8192 | 100.6 | 107.0 | 0.94 |
| 32 | c4flash | 2048 | 140.8 | 125.2 | 1.12 |
| 32 | c4flash | 8192 | 525.0 | 468.4 | 1.12 |
| 32 | c128-64k | 2048 | 139.9 | 128.7 | 1.09 |
| 32 | c128-64k | 8192 | 526.7 | 484.0 | 1.09 |
| 64 | swa | 2048 | 48.6 | 38.5 | 1.26 |
| 64 | swa | 8192 | 171.0 | 133.1 | 1.28 |
| 64 | c4flash | 2048 | 143.1 | 128.5 | 1.11 |
| 64 | c4flash | 8192 | 533.3 | 476.2 | 1.12 |
| 64 | c4pro | 2048 | 237.6 | 216.7 | 1.10 |
| 64 | c4pro | 8192 | 897.6 | 814.5 | 1.10 |
| 64 | c128-16k | 2048 | 73.3 | 61.1 | 1.20 |
| 64 | c128-16k | 8192 | 276.4 | 230.4 | 1.20 |
| 64 | c128-64k | 2048 | 144.1 | 133.5 | 1.08 |
| 64 | c128-64k | 8192 | 542.2 | 504.8 | 1.07 |
| 64 | c128-256k | 2048 | 426.3 | – | NVFP4 only |
| 64 | c128-256k | 8192 | 1628.5 | – | NVFP4 only |
| 128 | swa | 2048 | 75.6 | 71.1 | 1.06 |
| 128 | swa | 8192 | 279.5 | 260.2 | 1.07 |
| 128 | c4pro | 2048 | 354.6 | 289.1 | 1.23 |
| 128 | c4pro | 8192 | 1379.6 | 1100.5 | 1.25 |
| 128 | c128-16k | 2048 | 110.0 | 98.2 | 1.12 |
| 128 | c128-16k | 8192 | 423.8 | 371.6 | 1.14 |
| 128 | c128-64k | 2048 | 214.7 | 183.4 | 1.17 |
| 128 | c128-64k | 8192 | 820.5 | 697.2 | 1.18 |
| 128 | c128-256k | 2048 | 635.7 | – | NVFP4 only |
| 128 | c128-256k | 8192 | 2504.0 | – | NVFP4 only |

**Known gaps**
- NVFP4 wins on 16/32-head SWA layers and on every 256K C128 layer,
where FP8 has no kernel (width > 1152).
- C4/C128 layers at 64 and 128 heads are 1.07–1.25× FP8: they are bound
by the per-tile NVFP4 → E4M3 V transform, which FP8 does not need.
- 8-head SWA is 1.5× the best FP8 kernel, though 0.35× FlashInfer's
8-head FP8 route.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added NVFP4 sparse-attention prefill support for packed `uint8`
queries on supported SM100 and SM103 hardware.
  * Added a helper to pack BF16 queries into the NVFP4 format.
* BF16 queries continue to use decode for smaller metadata batches;
larger BF16 batches are rejected. Prefill outputs include attention
results and base-2 LSE.
* Added prefill workspace support and architecture-specific kernel
variants.
* **Documentation**
* Clarified query format requirements, prefill routing, test commands,
and NVFP4 test tolerances.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [976e7da](https://github.com/flashinfer-ai/flashinfer/commit/976e7daad5fff4756531b6d9daa615d10918728f)

- **作者**: eigen
- **时间**: 2026-11-12T22:55:18Z
- **提交信息**: perf(cake_msa): blackwell_msa BF16-Q E4M3-KV sparse prefill visits only the selected KV blocks (#9394)

FlashInfer's Blackwell MSA union prefill kernel (`prefill_union`) comes
in several variants:

- **Unfolded, by Q/KV data type:** BF16/BF16, FP16/FP16 and BF16/E4M3 on
both flat and paged KV layouts, and E4M3/E4M3 on paged only.
- **GQA-folded:** gqa16 and gqa8 forms (BF16 only).
- **Paged gqa16 BF16 causal:** two variants, causal_large and
causal_mask64.

This PR delivers the BF16-Q / E4M3-KV unfolded variant, flat and paged.
The baseline is the previous Cake version of this program on FlashInfer
main. Against it, the new version is:

- 10.100x-10.285x faster for a q=8 chunk on a 131072-token prefix
- 5.295x-5.376x faster for a q=8 chunk on a 65536-token prefix
- 1.178x-1.226x faster for q=512/2048 on a 65536-token prefix
- 1.078x-1.118x faster for q=8192/16384 with or without a prefix

The family's other Cake variants are decode (decode_m16, FP8
single-query decode and the uniform-FP8 decode tiers), K-major
persistent prefill (kmaj_p, kmaj_p_fused), long BF16 reverse prefill and
top-k select; like this one, they ship on sm_100a and sm_103a.

**GB300 (sm_103a), CUDA 13.4.** Latency of one public
`flashinfer.msa_ops.msa_sparse_attention` call in ms, measured with
CUPTI, cold L2, no CUDA graph; median of 3 round medians, 15 samples per
round. Main = FlashInfer main `1bdba8725`. Shapes: batch 1, causal,
query length q, prefix p (KV length = p + q), 16 query heads / 1 KV
head, top-k 16, block 128, head dim 128.

| Shape | Flat main | Flat this PR | Flat speedup | Paged main | Paged
this PR | Paged speedup |
|---|---|---|---|---|---|---|
| q=8, p=0 | 0.0568 | 0.0575 | 0.989x | 0.1044 | 0.0906 | 1.153x |
| q=8192, p=0 | 0.6853 | 0.6201 | 1.105x | 0.6834 | 0.6205 | 1.101x |
| q=16384, p=0 | 2.2162 | 2.0526 | 1.080x | 2.2124 | 2.0517 | 1.078x |
| q=8, p=65536 | 2.4003 | 0.4465 | 5.376x | 2.3954 | 0.4457 | 5.374x |
| q=8192, p=65536 | 9.1416 | 8.3541 | 1.094x | 9.1303 | 8.3421 | 1.094x
|
| q=16384, p=65536 | 16.9874 | 15.7450 | 1.079x | 16.9656 | 15.7249 |
1.079x |
| q=8, p=131072 | 4.7872 | 0.4669 | 10.252x | 4.7841 | 0.4652 | 10.285x
|
| q=512, p=65536 | 2.3753 | 1.9835 | 1.198x | 2.3760 | 1.9814 | 1.199x |
| q=2048, p=65536 | 2.3882 | 2.0265 | 1.178x | 2.3865 | 2.0227 | 1.180x
|

The q=8 / prefix 0 rows are dominated by host time (round spread
main/this PR: flat 90%/2%, paged 134%/69%).

**B200 (sm_100a), CUDA 13.4.** Same method and shapes as above.

| Shape | Flat main | Flat this PR | Flat speedup | Paged main | Paged
this PR | Paged speedup |
|---|---|---|---|---|---|---|
| q=8, p=0 | 0.0154 | 0.0185 | 0.832x | 0.0242 | 0.0218 | 1.109x |
| q=8192, p=0 | 0.7434 | 0.6789 | 1.095x | 0.7434 | 0.6769 | 1.098x |
| q=16384, p=0 | 2.4105 | 2.2067 | 1.092x | 2.4115 | 2.2046 | 1.094x |
| q=8, p=65536 | 2.4402 | 0.4608 | 5.295x | 2.4340 | 0.4588 | 5.305x |
| q=8192, p=65536 | 9.7475 | 8.7225 | 1.118x | 9.7260 | 8.7122 | 1.116x
|
| q=16384, p=65536 | 18.3635 | 16.6431 | 1.103x | 18.3337 | 16.6339 |
1.102x |
| q=8, p=131072 | 4.8711 | 0.4823 | 10.100x | 4.8589 | 0.4802 | 10.119x
|
| q=512, p=65536 | 2.5222 | 2.0572 | 1.226x | 2.5140 | 2.0542 | 1.224x |
| q=2048, p=65536 | 2.5457 | 2.0992 | 1.213x | 2.5365 | 2.0961 | 1.210x
|

The q=8 / prefix 0 rows are dominated by host time (round spread
main/this PR: flat 16%/54%, paged 78%/23%).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Updated Blackwell MSA prefill support for flat and paged workloads
using bfloat16 queries and float8 keys.
* For eligible workloads, processing can now focus on selected KV
blocks, with full-block traversal retained as a fallback.
* **Bug Fixes**
* Invalid inputs and CUDA or driver failures now produce reported errors
rather than proceeding with unsupported settings.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [ab3e738](https://github.com/flashinfer-ai/flashinfer/commit/ab3e738bd44c870b312d7369cf9847c5a14995b8)

- **作者**: eigen
- **时间**: 2026-11-12T22:54:59Z
- **提交信息**: fix(cake_kda): keep non-finite V of one packed sequence out of the others in KDA prefill (#9407)

Cake KDA chunked prefill (`backend="cake"`) on packed variable-length
sequences (`cu_seqlens`) has several bodies. This PR fixes three of
them: the small-BH M128 owner body (BF16 state, FP32 state pool, or no
initial state), the BF16 BT16 chain used by `recurrent_kda`, and the
TF32 BT16 chain behind the prepared TF32 API. On a sequence's tail
chunk, these bodies TMA-load the V tile across the whole chunk. The rows
past the sequence end hold the next sequence's tokens, and the only
thing cancelling them was a multiplication by zero. As a result, a NaN
or inf V in one packed sequence reached the output and final state of
the previous sequence (Fixes #8443). The fix clears those V rows on the
tail chunk only, and full chunks run their original code. The small-BH
body peels the last chunk out of its loop, and the chains clear V in a
block that only the tail chunk enters. This is a correctness fix, not a
speed-up. Against the same Cake kernels on FlashInfer main (1bdba8725)
on GB300 (sm_103a), the geomean kernel time over 14 shapes is 1.004x
faster. The largest slowdown is 0.9% (small-BH with an FP32 state pool),
and the BT16 chain rows are 1.1-2.2% faster. On B200 (sm_100a) the fix
costs 1.5% (geomean 1.0148x kernel time over the same 14 shapes):
1.6-2.4% on the small-BH body, 1.3-1.5% on the TF32 chain and 0.6-1.0%
on the BF16 chain, including shapes without a tail chunk.

The other Cake KDA variants (persistent, fused M128/M64, V-tile and TF32
fused routes) already zero-fill past the sequence end, and the family
ships on sm_100a and sm_103a.

**NVIDIA GB300, sm_103a (152 SMs), CUDA 13.4.** Per-launch CUDA kernel
time in µs, median over 5 rotating rounds (spread = (max - min) / median
over rounds); BF16 q/k/v, head dim 128; same GPU for main and this PR.

| body | API | packed sequence lengths | heads | initial state | main µs
(spread) | this PR µs (spread) | this PR / main |
|---|---|---|---:|---|---:|---:|---:|
| small-BH | `recurrent_kda` | 4100, 2049 | 4 | BF16 | 167.8 (0.05%) |
168.0 (0.05%) | 1.0010 |
| small-BH | `recurrent_kda` | 4100, 2049 | 4 | FP32 pool | 169.1
(0.06%) | 170.6 (0.08%) | 1.0091 |
| small-BH | `recurrent_kda` | 4100, 2049 | 2 | none | 171.2 (0.09%) |
170.6 (0.03%) | 0.9962 |
| small-BH | `recurrent_kda` | 8193 | 1 | BF16 | 321.1 (0.06%) | 320.0
(0.07%) | 0.9965 |
| small-BH | `recurrent_kda` | 4096, 2048 (no tail chunk) | 4 | BF16 |
166.7 (0.04%) | 166.7 (0.07%) | 0.9997 |
| small-BH | `recurrent_kda` | 4096, 2048 (no tail chunk) | 4 | FP32
pool | 167.6 (0.05%) | 169.2 (0.06%) | 1.0091 |
| small-BH | `recurrent_kda` | 8192 (no tail chunk) | 1 | BF16 | 320.2
(0.08%) | 319.1 (0.03%) | 0.9968 |
| BF16 BT16 chain | `recurrent_kda` | 4100, 4097, 5000, 4099 | 8 | BF16
| 204.1 (0.24%) | 201.3 (0.16%) | 0.9862 |
| BF16 BT16 chain | `recurrent_kda` | 4100, 4097, 5000, 4099 | 8 | FP32
pool | 203.0 (0.14%) | 198.6 (0.28%) | 0.9784 |
| BF16 BT16 chain | `recurrent_kda` | 4100, 2049 | 8 | none | 146.6
(0.05%) | 144.8 (0.05%) | 0.9882 |
| BF16 BT16 chain | `recurrent_kda` | 4100, 4200 | 16 | BF16 | 183.1
(0.22%) | 181.0 (0.22%) | 0.9889 |
| TF32 BT16 chain | `prepare_tf32_kda_prefill` | 4100, 2049 | 8 | FP32
pool | 149.9 (0.09%) | 149.7 (0.05%) | 0.9983 |
| TF32 BT16 chain | `prepare_tf32_kda_prefill` | 4100, 2049 | 1 | FP32
pool | 128.1 (0.05%) | 127.7 (0.07%) | 0.9975 |
| TF32 BT16 chain | `prepare_tf32_kda_prefill` | 300, 517, 1023, 77 | 12
| FP32 pool | 50.3 (0.23%) | 50.3 (0.15%) | 0.9995 |

Geomean this PR / main over the 14 rows: 0.9960 (1.004x faster); max
1.0091, min 0.9784.

**NVIDIA B200, sm_100a (148 SMs), CUDA 13.4.** Per-launch CUDA kernel
time in µs, median over 5 rotating rounds (spread = (max - min) / median
over rounds); BF16 q/k/v, head dim 128; same GPU for main and this PR.

| body | API | packed sequence lengths | heads | initial state | main µs
(spread) | this PR µs (spread) | this PR / main |
|---|---|---|---:|---|---:|---:|---:|
| small-BH | `recurrent_kda` | 4100, 2049 | 4 | BF16 | 177.7 (0.12%) |
180.5 (0.12%) | 1.0156 |
| small-BH | `recurrent_kda` | 4100, 2049 | 4 | FP32 pool | 181.5
(0.04%) | 185.8 (0.05%) | 1.0235 |
| small-BH | `recurrent_kda` | 4100, 2049 | 2 | none | 182.2 (0.04%) |
185.3 (0.05%) | 1.0169 |
| small-BH | `recurrent_kda` | 8193 | 1 | BF16 | 341.8 (0.06%) | 348.8
(0.09%) | 1.0206 |
| small-BH | `recurrent_kda` | 4096, 2048 (no tail chunk) | 4 | BF16 |
175.9 (0.05%) | 178.7 (0.02%) | 1.0157 |
| small-BH | `recurrent_kda` | 4096, 2048 (no tail chunk) | 4 | FP32
pool | 179.9 (0.08%) | 184.1 (0.13%) | 1.0231 |
| small-BH | `recurrent_kda` | 8192 (no tail chunk) | 1 | BF16 | 340.9
(0.10%) | 347.6 (0.07%) | 1.0198 |
| BF16 BT16 chain | `recurrent_kda` | 4100, 4097, 5000, 4099 | 8 | BF16
| 210.2 (0.12%) | 212.3 (0.25%) | 1.0099 |
| BF16 BT16 chain | `recurrent_kda` | 4100, 4097, 5000, 4099 | 8 | FP32
pool | 209.4 (0.17%) | 211.0 (0.27%) | 1.0076 |
| BF16 BT16 chain | `recurrent_kda` | 4100, 2049 | 8 | none | 149.4
(0.07%) | 150.4 (0.04%) | 1.0063 |
| BF16 BT16 chain | `recurrent_kda` | 4100, 4200 | 16 | BF16 | 186.8
(0.07%) | 188.1 (0.32%) | 1.0067 |
| TF32 BT16 chain | `prepare_tf32_kda_prefill` | 4100, 2049 | 8 | FP32
pool | 160.6 (0.11%) | 163.0 (0.10%) | 1.0150 |
| TF32 BT16 chain | `prepare_tf32_kda_prefill` | 4100, 2049 | 1 | FP32
pool | 136.3 (0.05%) | 138.1 (0.05%) | 1.0136 |
| TF32 BT16 chain | `prepare_tf32_kda_prefill` | 300, 517, 1023, 77 | 12
| FP32 pool | 53.5 (0.21%) | 54.2 (0.18%) | 1.0130 |

Geomean this PR / main over the 14 rows: 1.0148 (1.5% slower); max
1.0235, min 1.0063.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Corrected handling of incomplete final chunks in KDA prefill,
preventing values beyond the sequence length from affecting outputs and
final states across supported schedules and data formats.
* **Tests**
* Added coverage for sequence isolation and final-state accuracy across
KDA prefill schedules, including SM103 V-tile routes and TF32 chains.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [ee59cd5](https://github.com/flashinfer-ai/flashinfer/commit/ee59cd5d981960acdd0b7fe1be1f7237f2aa6a10)

- **作者**: eigen
- **时间**: 2026-11-12T22:54:36Z
- **提交信息**: fix(cake_grouped_mxfp8_quantize): keep nonzero blocks whose E8M0 scale byte is 0 (#9416)

The Cake grouped MXFP8 quantize kernel (`mxfp8_grouped_quantize(...,
backend="cake")`) has 16 variants. They are 8 program forms (ROW2D,
BULK, TILED, TILED_WIDE, TILED_K2048, TILED_K4096, HEAD2048, HEAD4096)
times 2 input dtypes (BF16, F16). This PR regenerates all 16 and fixes
#5996. Before this fix, a nonzero BF16 block with amax at most 448 x
2^-127 got scale byte 0 and decoded to zeros. Scale byte 0 now uses the
reciprocal 2^127, so these blocks keep their values. F16 outputs are
unchanged. This is a correctness fix at speed parity. The baseline is
the previous Cake version of the kernel on FlashInfer main (1bdba8725).
On GB300 (sm_103a), the geomean over 24 rows (12 shapes x 2 dtypes) is
1.002x (time ratio 0.9982). The largest slowdown is 0.32% (F16
TILED_K2048, 11.51 -> 11.55 µs), and the largest speed-up is 1.35% (F16
TILED_K4096). On B200 (sm_100a), the geomean is 1.003x (time ratio
0.9974), and the largest slowdown is 0.07% (F16 TILED_K4096, 31.28 ->
31.31 µs).

The kernel has no other Cake variants, and the family ships on sm_100a
and sm_103a.

**NVIDIA GB300, sm_103a (152 SMs), CUDA 13.4.** Time per call in µs: a
CUDA graph of 200 back-to-back `mxfp8_grouped_quantize(x, mask,
backend="cake")` calls with a full mask and `randn * 16` input, median
of 5 alternating rounds; main and this PR on the same GPU.

| input | program | B x M x K | main µs | this PR µs | this PR / main |
|---|---|---|---:|---:|---:|
| BF16 | BULK | 2 x 256 x 4096 | 2.03 | 2.02 | 0.9958 |
| BF16 | BULK | 3 x 200 x 160 | 1.64 | 1.64 | 0.9958 |
| BF16 | ROW2D | 2 x 257 x 4096 | 2.02 | 2.01 | 0.9966 |
| BF16 | ROW2D | 4 x 1024 x 2048 | 4.05 | 4.02 | 0.9929 |
| BF16 | HEAD2048 | 8 x 512 x 2048 | 4.08 | 4.08 | 0.9996 |
| BF16 | HEAD4096 | 64 x 128 x 4096 | 12.52 | 12.51 | 0.9988 |
| BF16 | TILED | 32 x 1024 x 256 | 3.52 | 3.51 | 0.9975 |
| BF16 | TILED | 32 x 1024 x 8192 | 115.05 | 115.07 | 1.0002 |
| BF16 | TILED_K2048 | 16 x 1024 x 2048 | 11.54 | 11.55 | 1.0008 |
| BF16 | TILED_K4096 | 16 x 1024 x 4096 | 30.52 | 30.50 | 0.9997 |
| BF16 | TILED_WIDE | 16 x 1024 x 7168 | 51.23 | 51.23 | 1.0001 |
| BF16 | TILED_WIDE | 32 x 1024 x 7168 | 100.16 | 100.18 | 1.0002 |
| F16 | BULK | 2 x 256 x 4096 | 2.02 | 2.02 | 1.0017 |
| F16 | BULK | 3 x 200 x 160 | 1.64 | 1.64 | 0.9987 |
| F16 | ROW2D | 2 x 257 x 4096 | 2.01 | 2.00 | 0.9982 |
| F16 | ROW2D | 4 x 1024 x 2048 | 3.98 | 3.98 | 0.9988 |
| F16 | HEAD2048 | 8 x 512 x 2048 | 4.03 | 4.02 | 0.9990 |
| F16 | HEAD4096 | 64 x 128 x 4096 | 12.53 | 12.52 | 0.9989 |
| F16 | TILED | 32 x 1024 x 256 | 3.53 | 3.53 | 0.9982 |
| F16 | TILED | 32 x 1024 x 8192 | 115.18 | 115.05 | 0.9989 |
| F16 | TILED_K2048 | 16 x 1024 x 2048 | 11.51 | 11.55 | 1.0032 |
| F16 | TILED_K4096 | 16 x 1024 x 4096 | 30.64 | 30.23 | 0.9865 |
| F16 | TILED_WIDE | 16 x 1024 x 7168 | 51.38 | 51.22 | 0.9968 |
| F16 | TILED_WIDE | 32 x 1024 x 7168 | 100.25 | 100.15 | 0.9992 |

Geomean this PR / main over the 24 rows: 0.9982 (1.002x); max 1.0032,
min 0.9865.

**NVIDIA B200, sm_100a (148 SMs), CUDA 13.4.** Time per call in µs: a
CUDA graph of 200 back-to-back `mxfp8_grouped_quantize(x, mask,
backend="cake")` calls with a full mask and `randn * 16` input, median
of 5 alternating rounds; main and this PR on the same GPU.

| input | program | B x M x K | main µs | this PR µs | this PR / main |
|---|---|---|---:|---:|---:|
| BF16 | BULK | 2 x 256 x 4096 | 2.08 | 2.07 | 0.9970 |
| BF16 | BULK | 3 x 200 x 160 | 1.70 | 1.69 | 0.9950 |
| BF16 | ROW2D | 2 x 257 x 4096 | 2.14 | 2.13 | 0.9960 |
| BF16 | ROW2D | 4 x 1024 x 2048 | 4.21 | 4.19 | 0.9949 |
| BF16 | HEAD2048 | 8 x 512 x 2048 | 4.30 | 4.29 | 0.9965 |
| BF16 | HEAD4096 | 64 x 128 x 4096 | 13.97 | 13.95 | 0.9990 |
| BF16 | TILED | 32 x 1024 x 256 | 3.72 | 3.71 | 0.9971 |
| BF16 | TILED | 32 x 1024 x 8192 | 118.41 | 118.43 | 1.0002 |
| BF16 | TILED_K2048 | 16 x 1024 x 2048 | 12.80 | 12.68 | 0.9924 |
| BF16 | TILED_K4096 | 16 x 1024 x 4096 | 31.32 | 31.31 | 0.9996 |
| BF16 | TILED_WIDE | 16 x 1024 x 7168 | 52.78 | 52.79 | 1.0000 |
| BF16 | TILED_WIDE | 32 x 1024 x 7168 | 103.12 | 103.20 | 1.0006 |
| F16 | BULK | 2 x 256 x 4096 | 2.09 | 2.08 | 0.9941 |
| F16 | BULK | 3 x 200 x 160 | 1.71 | 1.69 | 0.9910 |
| F16 | ROW2D | 2 x 257 x 4096 | 2.13 | 2.12 | 0.9953 |
| F16 | ROW2D | 4 x 1024 x 2048 | 4.15 | 4.15 | 0.9991 |
| F16 | HEAD2048 | 8 x 512 x 2048 | 4.22 | 4.21 | 0.9979 |
| F16 | HEAD4096 | 64 x 128 x 4096 | 13.98 | 13.97 | 0.9993 |
| F16 | TILED | 32 x 1024 x 256 | 3.73 | 3.72 | 0.9974 |
| F16 | TILED | 32 x 1024 x 8192 | 118.36 | 118.38 | 1.0000 |
| F16 | TILED_K2048 | 16 x 1024 x 2048 | 12.94 | 12.89 | 0.9947 |
| F16 | TILED_K4096 | 16 x 1024 x 4096 | 31.28 | 31.31 | 1.0007 |
| F16 | TILED_WIDE | 16 x 1024 x 7168 | 52.69 | 52.69 | 1.0000 |
| F16 | TILED_WIDE | 32 x 1024 x 7168 | 102.72 | 102.78 | 1.0006 |

Geomean this PR / main over the 24 rows: 0.9974 (1.003x); max 1.0007,
min 0.9910.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Updated Cake grouped MXFP8 quantization for blocks with a zero scale
byte: nonzero values in these blocks are quantized using a reciprocal of
\(2^{127}\), rather than being forced to signed zero.
* **Documentation**
* Clarified how zero-scale blocks can differ across Cake, cuTile, and
CUDA backends, and documented the relevant bfloat16 maximum-value
threshold.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [e4ad8d4](https://github.com/flashinfer-ai/flashinfer/commit/e4ad8d4a19a0fc557c2931448dfd97682805f8ef)

- **作者**: eigen
- **时间**: 2026-11-12T22:53:36Z
- **提交信息**: fix(fused_topk_deepseek): exp-form sigmoid in the default and Cake routing kernels (#9393)

`fused_topk_deepseek` (DeepSeek-V3 grouped top-k routing) has two
backends. `backend="default"` runs the noAuxTc kernel. `backend="cake"`
has two variants for sm_100a/sm_103a, the grouped kernel (group
warp-select / group tile) and the single-group kernel, plus the SM 10.7
multi-token and single-group kernels. All of them take bfloat16 or
float32 scores. Both backends computed the routing sigmoid as
`0.5*tanh(0.5x)+0.5`, which rounds to exactly 0 in FP32 for logits at or
below about -18. A token whose logits were all that negative therefore
got all-zero routing weights (Fixes #7928). This PR changes noAuxTc to
`1/(1+expf(-x))`, the change proposed in #5557 (credit
@iaroslav-reflection), and every Cake variant to
`approx_rcp(1+__expf(-x))`. Under `-use_fast_math` both forms compile to
the same `ex2.approx.ftz` + `rcp.approx.ftz` sequence. Compared with the
previous Cake kernels on main, the new Cake kernels are at parity:
latency is within about 3% on every measured row, with a this PR / main
latency ratio of 0.994-1.027 across the three GPUs. The default
backend's speed is unchanged; per-row differences are within about 2% in
either direction. After the fix, the Cake backend's geomean speedup over
the default backend is 1.07x on B200, 1.37x on GB300 and 1.29x on VR200.

The Cake backend of this kernel ships on sm_100a, sm_103a and sm_107a,
and this PR changes all of its variants, so no Cake variant still uses
the tanh form.

Median microseconds per call, CUDA graph of 32 calls, 4 alternating
sessions, same GPU for main and this PR.

**B200 (sm_100a, 148 SM, CUDA 13.4)**

| E | n_group/topk_group | topk | T | scores | default main (us) |
default this PR (us) | Cake main (us) | Cake this PR (us) | Cake this PR
/ main (latency) | default / Cake (this PR) |
|---|---|---|---|---|---|---|---|---|---|---|
| 128 | 1/1 | 1 | 1 | bfloat16 | 1.923 | 1.923 | 1.629 | 1.667 | 1.023 |
1.15x |
| 128 | 1/1 | 1 | 1 | float32 | 1.923 | 1.923 | 1.476 | 1.476 | 1.000 |
1.30x |
| 128 | 1/1 | 1 | 4096 | bfloat16 | 5.187 | 5.190 | 5.337 | 5.378 |
1.008 | 0.97x |
| 128 | 1/1 | 1 | 4096 | float32 | 5.146 | 5.186 | 5.319 | 5.320 | 1.000
| 0.97x |
| 256 | 8/4 | 8 | 1 | bfloat16 | 2.499 | 2.499 | 2.336 | 2.327 | 0.996 |
1.07x |
| 256 | 8/4 | 8 | 1 | float32 | 2.435 | 2.436 | 2.115 | 2.115 | 1.000 |
1.15x |
| 256 | 8/4 | 8 | 8 | bfloat16 | 2.435 | 2.435 | 2.307 | 2.307 | 1.000 |
1.06x |
| 256 | 8/4 | 8 | 8 | float32 | 2.438 | 2.438 | 2.310 | 2.310 | 1.000 |
1.06x |
| 256 | 8/4 | 8 | 32 | bfloat16 | 2.499 | 2.499 | 2.371 | 2.371 | 1.000
| 1.05x |
| 256 | 8/4 | 8 | 32 | float32 | 2.467 | 2.439 | 2.371 | 2.371 | 1.000 |
1.03x |
| 256 | 8/4 | 8 | 128 | bfloat16 | 2.499 | 2.502 | 2.435 | 2.435 | 1.000
| 1.03x |
| 256 | 8/4 | 8 | 128 | float32 | 2.509 | 2.531 | 2.435 | 2.435 | 1.000
| 1.04x |
| 256 | 8/4 | 8 | 512 | bfloat16 | 2.736 | 2.755 | 2.565 | 2.602 | 1.014
| 1.06x |
| 256 | 8/4 | 8 | 512 | float32 | 2.755 | 2.755 | 2.568 | 2.627 | 1.023
| 1.05x |
| 256 | 8/4 | 8 | 849 | bfloat16 | 3.254 | 3.233 | 3.014 | 3.019 | 1.002
| 1.07x |
| 256 | 8/4 | 8 | 849 | float32 | 3.330 | 3.277 | 2.969 | 3.010 | 1.014
| 1.09x |
| 256 | 8/4 | 8 | 1024 | bfloat16 | 3.458 | 3.459 | 3.206 | 3.265 |
1.018 | 1.06x |
| 256 | 8/4 | 8 | 1024 | float32 | 3.458 | 3.458 | 3.169 | 3.203 | 1.011
| 1.08x |
| 256 | 8/4 | 8 | 3393 | bfloat16 | 6.593 | 6.592 | 6.211 | 6.214 |
1.000 | 1.06x |
| 256 | 8/4 | 8 | 3393 | float32 | 6.592 | 6.602 | 6.208 | 6.208 | 1.000
| 1.06x |
| 256 | 8/4 | 8 | 4096 | bfloat16 | 7.543 | 7.502 | 7.069 | 7.080 |
1.002 | 1.06x |
| 256 | 8/4 | 8 | 4096 | float32 | 7.494 | 7.555 | 7.040 | 7.040 | 1.000
| 1.07x |
| 256 | 8/4 | 8 | 4241 | bfloat16 | 7.753 | 7.755 | 7.238 | 7.241 |
1.000 | 1.07x |
| 256 | 8/4 | 8 | 4241 | float32 | 7.750 | 7.811 | 7.237 | 7.236 | 1.000
| 1.08x |
| 256 | 8/4 | 8 | 16384 | bfloat16 | 23.288 | 23.285 | 21.818 | 21.844 |
1.001 | 1.07x |
| 256 | 8/4 | 8 | 16384 | float32 | 23.181 | 23.352 | 21.748 | 21.753 |
1.000 | 1.07x |
| 384 | 1/1 | 8 | 1 | bfloat16 | n/a | n/a | n/a | n/a | - | - |
| 384 | 1/1 | 8 | 1 | float32 | n/a | n/a | n/a | n/a | - | - |
| 384 | 1/1 | 8 | 128 | bfloat16 | n/a | n/a | n/a | n/a | - | - |
| 384 | 1/1 | 8 | 128 | float32 | n/a | n/a | n/a | n/a | - | - |
| 384 | 1/1 | 8 | 4096 | bfloat16 | n/a | n/a | n/a | n/a | - | - |
| 384 | 1/1 | 8 | 4096 | float32 | n/a | n/a | n/a | n/a | - | - |

**GB300 (sm_103a, 152 SM, CUDA 13.4)**

| E | n_group/topk_group | topk | T | scores | default main (us) |
default this PR (us) | Cake main (us) | Cake this PR (us) | Cake this PR
/ main (latency) | default / Cake (this PR) |
|---|---|---|---|---|---|---|---|---|---|---|
| 128 | 1/1 | 1 | 1 | bfloat16 | 2.243 | 2.243 | 1.475 | 1.475 | 1.000 |
1.52x |
| 128 | 1/1 | 1 | 1 | float32 | 2.306 | 2.307 | 1.539 | 1.539 | 1.000 |
1.50x |
| 128 | 1/1 | 1 | 4096 | bfloat16 | 8.643 | 8.642 | 5.187 | 5.186 |
1.000 | 1.67x |
| 128 | 1/1 | 1 | 4096 | float32 | 8.960 | 9.013 | 5.187 | 5.187 | 1.000
| 1.74x |
| 256 | 8/4 | 8 | 1 | bfloat16 | 2.691 | 2.691 | 2.179 | 2.179 | 1.000 |
1.23x |
| 256 | 8/4 | 8 | 1 | float32 | 2.752 | 2.752 | 1.792 | 1.793 | 1.001 |
1.53x |
| 256 | 8/4 | 8 | 8 | bfloat16 | 2.755 | 2.755 | 1.995 | 2.048 | 1.027 |
1.35x |
| 256 | 8/4 | 8 | 8 | float32 | 2.755 | 2.755 | 2.179 | 2.179 | 1.000 |
1.26x |
| 256 | 8/4 | 8 | 32 | bfloat16 | 2.819 | 2.819 | 2.243 | 2.243 | 1.000
| 1.26x |
| 256 | 8/4 | 8 | 32 | float32 | 2.819 | 2.819 | 2.243 | 2.243 | 1.000 |
1.26x |
| 256 | 8/4 | 8 | 128 | bfloat16 | 2.883 | 2.883 | 2.307 | 2.341 | 1.015
| 1.23x |
| 256 | 8/4 | 8 | 128 | float32 | 2.883 | 2.883 | 2.307 | 2.307 | 1.000
| 1.25x |
| 256 | 8/4 | 8 | 512 | bfloat16 | 3.267 | 3.267 | 2.499 | 2.499 | 1.000
| 1.31x |
| 256 | 8/4 | 8 | 512 | float32 | 3.267 | 3.267 | 2.499 | 2.499 | 1.000
| 1.31x |
| 256 | 8/4 | 8 | 849 | bfloat16 | 3.840 | 3.842 | 2.883 | 2.910 | 1.009
| 1.32x |
| 256 | 8/4 | 8 | 849 | float32 | 3.944 | 3.907 | 2.945 | 2.947 | 1.001
| 1.33x |
| 256 | 8/4 | 8 | 1024 | bfloat16 | 4.160 | 4.160 | 3.075 | 3.127 |
1.017 | 1.33x |
| 256 | 8/4 | 8 | 1024 | float32 | 4.226 | 4.227 | 3.108 | 3.139 | 1.010
| 1.35x |
| 256 | 8/4 | 8 | 3393 | bfloat16 | 7.938 | 7.938 | 5.823 | 5.825 |
1.000 | 1.36x |
| 256 | 8/4 | 8 | 3393 | float32 | 8.123 | 8.124 | 5.769 | 5.766 | 0.999
| 1.41x |
| 256 | 8/4 | 8 | 4096 | bfloat16 | 8.965 | 8.966 | 6.596 | 6.597 |
1.000 | 1.36x |
| 256 | 8/4 | 8 | 4096 | float32 | 9.216 | 9.216 | 6.594 | 6.594 | 1.000
| 1.40x |
| 256 | 8/4 | 8 | 4241 | bfloat16 | 9.159 | 9.156 | 6.786 | 6.789 |
1.000 | 1.35x |
| 256 | 8/4 | 8 | 4241 | float32 | 9.369 | 9.395 | 6.725 | 6.726 | 1.000
| 1.40x |
| 256 | 8/4 | 8 | 16384 | bfloat16 | 27.664 | 27.664 | 20.293 | 20.320 |
1.001 | 1.36x |
| 256 | 8/4 | 8 | 16384 | float32 | 28.658 | 28.661 | 20.218 | 20.218 |
1.000 | 1.42x |
| 384 | 1/1 | 8 | 1 | bfloat16 | n/a | n/a | n/a | n/a | - | - |
| 384 | 1/1 | 8 | 1 | float32 | n/a | n/a | n/a | n/a | - | - |
| 384 | 1/1 | 8 | 128 | bfloat16 | n/a | n/a | n/a | n/a | - | - |
| 384 | 1/1 | 8 | 128 | float32 | n/a | n/a | n/a | n/a | - | - |
| 384 | 1/1 | 8 | 4096 | bfloat16 | n/a | n/a | n/a | n/a | - | - |
| 384 | 1/1 | 8 | 4096 | float32 | n/a | n/a | n/a | n/a | - | - |

**VR200 (sm_107a, 212 SM, CUDA 13.5)**

| E | n_group/topk_group | topk | T | scores | default main (us) |
default this PR (us) | Cake main (us) | Cake this PR (us) | Cake this PR
/ main (latency) | default / Cake (this PR) |
|---|---|---|---|---|---|---|---|---|---|---|
| 128 | 1/1 | 1 | 1 | bfloat16 | 1.577 | 1.575 | 1.226 | 1.219 | 0.994 |
1.29x |
| 128 | 1/1 | 1 | 1 | float32 | 1.529 | 1.536 | 1.048 | 1.053 | 1.005 |
1.46x |
| 128 | 1/1 | 1 | 4096 | bfloat16 | 4.438 | 4.442 | 4.545 | 4.552 |
1.002 | 0.98x |
| 128 | 1/1 | 1 | 4096 | float32 | 4.463 | 4.437 | 4.511 | 4.520 | 1.002
| 0.98x |
| 256 | 8/4 | 8 | 1 | bfloat16 | 1.833 | 1.833 | 1.681 | 1.682 | 1.001 |
1.09x |
| 256 | 8/4 | 8 | 1 | float32 | 2.019 | 2.023 | 1.675 | 1.675 | 1.000 |
1.21x |
| 256 | 8/4 | 8 | 8 | bfloat16 | 2.284 | 2.289 | 2.121 | 2.123 | 1.001 |
1.08x |
| 256 | 8/4 | 8 | 8 | float32 | 2.273 | 2.275 | 2.140 | 2.144 | 1.002 |
1.06x |
| 256 | 8/4 | 8 | 32 | bfloat16 | 2.262 | 2.269 | 2.141 | 2.150 | 1.004
| 1.06x |
| 256 | 8/4 | 8 | 32 | float32 | 2.315 | 2.318 | 2.169 | 2.175 | 1.003 |
1.07x |
| 256 | 8/4 | 8 | 128 | bfloat16 | 2.310 | 2.311 | 2.181 | 2.181 | 1.000
| 1.06x |
| 256 | 8/4 | 8 | 128 | float32 | 2.400 | 2.409 | 2.204 | 2.204 | 1.000
| 1.09x |
| 256 | 8/4 | 8 | 512 | bfloat16 | 2.590 | 2.577 | 2.329 | 2.329 | 1.000
| 1.11x |
| 256 | 8/4 | 8 | 512 | float32 | 2.488 | 2.513 | 2.343 | 2.343 | 1.000
| 1.07x |
| 256 | 8/4 | 8 | 849 | bfloat16 | 2.647 | 2.653 | 2.317 | 2.320 | 1.001
| 1.14x |
| 256 | 8/4 | 8 | 849 | float32 | 2.579 | 2.602 | 2.363 | 2.364 | 1.000
| 1.10x |
| 256 | 8/4 | 8 | 1024 | bfloat16 | 3.018 | 3.031 | 2.401 | 2.397 |
0.998 | 1.26x |
| 256 | 8/4 | 8 | 1024 | float32 | 2.882 | 2.911 | 2.416 | 2.415 | 1.000
| 1.21x |
| 256 | 8/4 | 8 | 3393 | bfloat16 | 5.530 | 5.551 | 3.276 | 3.300 |
1.007 | 1.68x |
| 256 | 8/4 | 8 | 3393 | float32 | 5.512 | 5.553 | 3.284 | 3.292 | 1.002
| 1.69x |
| 256 | 8/4 | 8 | 4096 | bfloat16 | 6.362 | 6.400 | 3.572 | 3.614 |
1.012 | 1.77x |
| 256 | 8/4 | 8 | 4096 | float32 | 6.355 | 6.414 | 3.546 | 3.608 | 1.017
| 1.78x |
| 256 | 8/4 | 8 | 4241 | bfloat16 | 6.505 | 6.529 | 3.733 | 3.782 |
1.013 | 1.73x |
| 256 | 8/4 | 8 | 4241 | float32 | 6.404 | 6.457 | 3.747 | 3.792 | 1.012
| 1.70x |
| 256 | 8/4 | 8 | 16384 | bfloat16 | 18.747 | 18.903 | 9.604 | 9.631 |
1.003 | 1.96x |
| 256 | 8/4 | 8 | 16384 | float32 | 18.540 | 18.693 | 9.521 | 9.600 |
1.008 | 1.95x |
| 384 | 1/1 | 8 | 1 | bfloat16 | n/a | n/a | n/a | n/a | - | - |
| 384 | 1/1 | 8 | 1 | float32 | n/a | n/a | n/a | n/a | - | - |
| 384 | 1/1 | 8 | 128 | bfloat16 | n/a | n/a | n/a | n/a | - | - |
| 384 | 1/1 | 8 | 128 | float32 | n/a | n/a | n/a | n/a | - | - |
| 384 | 1/1 | 8 | 4096 | bfloat16 | n/a | n/a | n/a | n/a | - | - |
| 384 | 1/1 | 8 | 4096 | float32 | n/a | n/a | n/a | n/a | - | - |

n/a: E=384 with one group is not supported by the Cake backend; not
measured.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved sigmoid score calculations used by mixture-of-experts
routing, including for negative logits.
* Updated single-token and multi-token routing paths to use consistent
score calculations, helping preserve expert selection and weights across
backends.

* **Tests**
* Added coverage for negative-logit routing and comparisons between
routing backends across supported data types.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [8b2cdfa](https://github.com/flashinfer-ai/flashinfer/commit/8b2cdfa89d8c5e6af0526c420a503a7e1ddbd886)

- **作者**: eigen
- **时间**: 2026-11-12T22:53:25Z
- **提交信息**: fix(bgmv_moe): restore BGMVMoEBlackwellPlan and backend="blackwell" as deprecated aliases (#9388)

This restores `BGMVMoEBlackwellPlan` (importable from
`flashinfer.fused_moe` and `flashinfer.fused_moe.bgmv_moe`) and
`prepare_bgmv_moe(backend="blackwell")` as deprecated aliases of the
Cake plan and backend, each emitting a `DeprecationWarning`. #6745
removed the class name and #5989 made `backend="blackwell"` raise, so
code written for 0.7.0/0.7.1 broke without a deprecation period. Fixes
#6520.

`fallback` now defaults to `None`, which resolves to `True` for
`backend="cake"` (current behaviour unchanged) and to `False` for
`"blackwell"`, so unsupported inputs raise `ValueError` as they did in
0.7.1 instead of silently returning a `BGMVMoEPortablePlan`. An explicit
`fallback` is honoured for both names.

The change is host-only. The new alias, warning and error-path tests and
the full `tests/moe/test_cake_bgmv_moe.py` pass on H100, B200 and GB300
(89 passed, 0 skipped on each).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Updates**
* The `blackwell` backend name and plan class remain available as
deprecated aliases for their `cake` equivalents and emit a deprecation
warning.
* Unsupported inputs with the `blackwell` alias raise an error by
default; pass `fallback=True` to enable fallback. The `cake` backend
continues to use portable fallback by default.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [cf87b9b](https://github.com/flashinfer-ai/flashinfer/commit/cf87b9bdc457a9fcf59781a9da7650c5d817bd36)

- **作者**: Akaash Parthasarathy
- **时间**: 2026-11-12T22:32:23Z
- **提交信息**: test: fix RMSNorm cache warmup and split EP CUDA guard (#9412)

<!-- .github/pull_request_template.md -->

## 📌 Description

Warm the RMSNorm row-count variants before checking module-cache reuse.
Skip the split EP selection test on CUDA 12, where its EP runtime is
unsupported.

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
reviewers may adjust): `tests/norm/test_cake_rmsnorm_det_train.py
tests/moe_ep/test_ep_selection_split.py`

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

* **Tests**
* Updated GPU test coverage to skip execution on CUDA versions below 13,
where the required runtime wheels are unavailable.
* Expanded normalization cache checks to verify that revisiting
previously tested token counts does not trigger additional module loads.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [646988d](https://github.com/flashinfer-ai/flashinfer/commit/646988d28750c4616895677a11e2aad54f7adfdf)

- **作者**: Ka-Hyun Nam
- **时间**: 2026-11-12T22:04:30Z
- **提交信息**: bump version to 0.7.5 (#9418)

### [1689208](https://github.com/flashinfer-ai/flashinfer/commit/168920874c95f1bc9888bdd015d13e056fa3a341)

- **作者**: Ka-Hyun Nam
- **时间**: 2026-11-12T21:48:11Z
- **提交信息**: test(gdn): bound state_dtype prefill output and state errors below the signal (#8405)

<!-- .github/pull_request_template.md -->

## 📌 Description

`tests/gdn/test_prefill_delta_rule.py::test_prefill_kernel_state_dtype`
compared the chunked prefill output and final recurrent state against
`blockwise_delta_rule` with `atol_o = 1e-1` and `atol_kv = 1e-1`, while
the outputs themselves peak at about 0.015-0.047 and the states never
exceed about 0.10 in magnitude. Any output or state inside the
reference's own range passed, including an all-zero state, so the test
could not catch a wrong (or NaN-adjacent) kernel; that is the second
half of #4704 (the ~0.25 relative L2 the reporter saw on 0.6.18 still
passed).

Output check: `atol_o` 1e-1 -> 5e-3 (with the existing `rtol_o = 5e-2`)
plus an output relative-L2 bound of 2e-2. Measured error on SM100 at
current main is max |delta| <= 5e-4 and relative L2 of 0.0037-0.0071
across bf16/fp16/fp8 states, so the new bounds sit roughly 3-10x above
the observed error and well below the signal.

State check: measured on B200 over the test's 96 `state_dtype` cases for
seeds 0, 1 and 2 (288 cases, no NaN), the state relative L2 is at most
0.0043 for bf16 and fp16 states and 0.037 / 0.025 for fp8 e4m3 / e5m2,
and the largest elementwise error is one fp8 ulp (0.0156 at a magnitude
of 0.078), a rounding disagreement in the final cast that the test has
to allow. The new bounds are `atol_kv = 2e-3` for 16-bit states (about
4x the worst measured error) and `2.5e-2` for fp8 states (one ulp up to
magnitude 0.25 at `rtol_kv = 5e-2`, about 2x the worst measured need),
plus a state relative-L2 bound of `2e-2` (16-bit) / `1e-1` (fp8)
mirroring the output bound.

The non-determinism half of #4704 (cross-process NaN) was not
reproducible on current main: six runs of this selector in fresh
processes with a cold JIT cache on SM100 all passed, and the per-process
recompile (#4912), the stream-scoped WY workspace (#4476) and the TMEM
load/release fence (#5335) that could have caused it have all landed
since 0.6.18. The reporter is asked to retest on >= 0.7.x; these
tightened bounds are the regression guard that would make any recurrence
visible instead of passing silently.

## 🔍 Related Issues

Fixes #4704

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
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/gdn/test_prefill_delta_rule.py`

`SEED={0,1,2} pytest tests/gdn/test_prefill_delta_rule.py -k
state_dtype` with a fresh JIT cache: 96 passed for each seed on B200
(CUDA 13.0) at the combined head. The output bound alone also passed
96/96 on H100 (SM90) and L40S (SM89).

## 🔬 Experimental Track

<!-- Only for PRs submitted under the experimental policy
(CONTRIBUTING.md → "Experimental APIs and Backends").
     Leave this section untouched for normal PRs. -->

## Reviewer Notes

The bounds were measured on SM100 (B200); the same test also runs the
SM8x, SM90 and SM12x prefill kernels, so the H100 and RTX PRO 6000 CI
lanes are the check that the 16-bit tolerances hold there too. If a
per-dtype `atol_kv` is not wanted, a single value would have to be
`2.5e-2`, about 50x the 16-bit error, which is why the split is kept.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [236a027](https://github.com/flashinfer-ai/flashinfer/commit/236a0278bb542bcd715a5936cd849260533aab0f)

- **作者**: Yang Xu
- **时间**: 2026-11-12T21:25:05Z
- **提交信息**: fix(attention): reject ignored sinks in standard FA paged adapters (#9410)

<!-- .github/pull_request_template.md -->

## 📌 Description

Passing `sinks` to the standard FA2/FA3 paged adapter currently launches
a kernel that does not consume the tensor, silently computing attention
without the sink contribution. Reject this unsupported argument before
launch, including tensor-core decode paths that share this adapter. TRT
sink forwarding and ordinary no-sink calls are unchanged; custom sink
JIT variants keep their existing positional interface.

Adds CPU regressions against the actual Python adapter with only native
launch/build plumbing mocked. Both rejection tests fail on the parent,
while the five supported/no-sink/no-CUDA controls pass; all seven pass
with the fix. Implemented with Codex assistance.

## 🔍 Related Issues

Found during paged attention integration validation; no existing
tracking issue.

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
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Local validation: 34 focused CPU tests passed, including the seven new
adapter tests and existing independent-query-length contracts.
Changed-file pre-commit hooks passed. GPU execution was not needed for
this argument-rejection check; the existing GPU sink-variant tests are
requested in targeted CI.

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/cpu/attention/test_paged_sinks_contract.py
tests/cpu/attention/test_paged_query_lengths_contract.py
tests/attention/test_attention_sink.py`

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

Scope is the standard FA2/FA3 paged adapter. This does not add sink
support, change kernels, or claim to fix every other wrapper that
accepts a `sinks` keyword. The CUDA-core decode and custom-JIT keyword
paths need a separate audit. Hooks were run only on changed files; the
full repository suite has not been run.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Paged prefill now clearly rejects `sinks` when using the standard FA2
or FA3 backend, instead of passing an unsupported configuration to the
backend.
* Calls without `sinks` continue to work with FA2, FA3, and TRT-LLM Gen.

* **Documentation**
* Updated backend notes to clarify sink support for paged adapters,
including custom sink JIT module requirements and tensor-core decode
routing.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [036a447](https://github.com/flashinfer-ai/flashinfer/commit/036a447c5ae88d84a199a28de7eb1ba426254d00)

- **作者**: eigen
- **时间**: 2026-11-12T21:14:26Z
- **提交信息**: fix(jit): embed cubins as COFF objects on Windows (#9415)

<!-- .github/pull_request_template.md -->

## 📌 Description

On native Windows (arm64, MSVC host toolchain), the `embed_cubin` ninja
rule in `flashinfer/jit/cpp_ext.py` runs `python -m
tvm_ffi.utils.embed_cubin`. That tool uses GNU `ld -r -b binary`,
`objcopy` and `ld -r`, and MSVC has none of them. The embed step fails
with `[WinError 2] The system cannot find the file specified`, followed
by `ninja: build stopped`. This was reported on a Windows 11 arm64
workstation with a GB300. Even after the alphamoe `small` rename
(#9303), `tests/moe/test_alphamoe_fused_router.py` still fails 120 of
129 cases at this step.

With this PR, the `embed_cubin` rule on Windows runs a new script,
`flashinfer/jit/embed_cubin_coff.py`. It uses only the standard library
and is invoked by file path, so it does not import the flashinfer
package. For each cubin, it writes a separate COFF object that has:

- one `.rdata` section (initialized data, read-only, 64-byte aligned)
holding the cubin bytes
- `__tvm_ffi__cubin_<name>` at offset 0 and
`__tvm_ffi__cubin_<name>_end` at offset len(cubin). These are the two
`extern "C"` symbols that `TVM_FFI_EMBED_CUBIN` declares.
- machine type ARM64 (0xAA64) or AMD64 (0x8664), chosen from
`platform.machine()`

Each object goes into the link inputs next to the host objects. It is
not merged into the first host object with `ld -r`. On Windows, build
lines escape the drive colon, spaces and `$` (`_ninja_windows_path`).
The rule quotes `$in`/`$out`, the Python executable and the script path.
Linux is unchanged: the ld/objcopy rule and the chained
`embedded_<i>_<obj>` objects are emitted exactly as before.

The script writes an object file instead of generating a C/C++ source
with a byte array because the `_end` symbol has to sit exactly at the
end of the bytes.
`flashinfer/moe_ep/kernel_src/sm120/cake_mxfp4_megamoe/src/cake_sm120_megamoe_cubins.cu`
computes the image size as `end - begin`. C++ does not guarantee that
two separately defined arrays are adjacent, but one COFF section with
two symbols does. This approach also avoids a compiler pass over large
byte arrays.

This fix covers the modules that use FlashInfer's `embedded_cubins` /
`embedded_cubin_factory` path: alphamoe_fused_router, cake_vsa,
flash_kda and the SM120 cake MXFP4 MegaMoE cubins. It does not cover
modules that call `tvm_ffi.cpp.load_inline(embed_cubin=...)`: cake_gdn,
cake_fmha_request_ordered, the KDA PTX static runtime and
cake_ssd_combined. For those, tvm-ffi raises `NotImplementedError("CUBIN
embedding is not yet supported on Windows")`, and fixing that needs a
change in tvm-ffi.

## 🔍 Related Issues

Part of the native Windows arm64 support work (#8431).
Follows #9303 (alphamoe `small` rename).

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
      Reason: 

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/cpu/infra/test_jit_cpp_ext.py
tests/moe/test_alphamoe_fused_router.py`

## Reviewer Notes

- On Windows, this change only helps together with #8431's
cl.exe/link.exe rules. Both PRs add the same `import platform` /
`is_windows = platform.system() == "Windows"` lines.
- A 3-way merge with #8431 has one small conflict, in the embedded-cubin
loop: #8431 wraps `resolved_cubin`/`embedded_obj` in its own
`ninja_path()` helper. Once both land, `ninja_path` can replace
`_ninja_windows_path`.
- After that merge, the new simulated-Windows ninja test may need
#8431's Windows-only include overlays stubbed, because the test sets
`is_windows=True` on Linux.
- New tests in `tests/cpu/infra/test_jit_cpp_ext.py` (all `cpu_only`):
- An independent reader parses the COFF object for arm64 and x64 and
checks the machine type, section flags (0x40700040), bytes and both
symbol offsets.
- The simulated-Windows ninja output has the COFF rule, one build line
per cubin and the object on the link line, with no tvm_ffi embed.
- The Linux ninja output still uses `tvm_ffi.utils.embed_cubin` with the
chained object.
  - `_ninja_windows_path` escapes paths correctly.
- Validation on a Linux aarch64 CPU node (Python 3.12.13, torch
2.15.0+cu132): `pytest tests/cpu/infra/test_jit_cpp_ext.py` gave 37
passed, 1 failed. The one failure,
`test_customize_batch_prefill_nvfp4_large_head_uses_prefill_flags`,
fails the same way on unmodified main in that environment and is
unrelated: the source tree is not installed, so `flashinfer/data/csrc`
is missing. `pre-commit run` passes on the changed files.
- Link check with an MSVC-compatible linker, for arm64 and x64:
- Setup: LLVM `lld-link` (from the `ziglang` package) linked the
script's objects into a DLL, together with a Windows object that
references the symbols. That object was built with `zig cc -target
aarch64-windows-msvc` / `x86_64-windows-msvc`. The DLL contained two
cubins: 300,001 bytes and 81 bytes, one with a long symbol name.
- Result: reading the DLL export table with `pefile` shows that for
every cubin, RVA(_end) − RVA(start) equals the cubin length, the bytes
at the start symbol match the cubin, and the start is 64-byte aligned.
- Not yet validated: a build and run with MSVC `link.exe` on native
Windows arm64 with a GB300 (needs #8431 on top). Could the reporter or
the #8431 author run `python -m pytest -q
tests/moe/test_alphamoe_fused_router.py` on that setup?


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Windows users can now build FlashInfer components that include GPU
cubins, with support for both ARM64 and x64 systems.
* **Bug Fixes**
* Improved handling of Windows build paths to help prevent path-related
build failures. Linux cubin embedding behavior remains unchanged.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [2f9d7fb](https://github.com/flashinfer-ai/flashinfer/commit/2f9d7fb2e14efac3a2afce2f2623d74a6d021654)

- **作者**: ranx2026
- **时间**: 2026-11-12T21:14:21Z
- **提交信息**: fix: rename the alphamoe router local small, a Windows SDK macro (#9303)

<!-- .github/pull_request_template.md -->

## 📌 Description

`csrc/alphamoe_fused_router.cu` declares a local kernel handle named
`small` in the SM100 and SM103 kernel tables. The Windows SDK header
`rpcndr.h` defines `small` as `char`, so every JIT build of the alphamoe
fused router module fails on native Windows with `invalid combination of
type specifiers` (the line expands to `static auto char = ...`);
`tests/moe/test_alphamoe_fused_router.py` loses 72 of 81 cases.

The four uses are renamed to `small_kernel`; no behavior change.
Verified on a Windows 11 arm64 workstation with a Blackwell GPU: the
compile error is gone; Linux unchanged.

Fixing the compile error makes a second failure visible in the same
module build on native Windows: the cubin-embedding step
(`tvm_ffi.utils.embed_cubin` runs GNU `ld` and `objcopy`, which Windows
does not have). That failure is tracked separately and is not addressed
here.

## 🔍 Related Issues

Part of the native Windows arm64 support work (#8431).

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
      Reason: 

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/moe/test_alphamoe_fused_router.py`

## 🔬 Experimental Track
## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Refactor**
* Renamed an internal kernel variable; runtime behavior and kernel
selection remain unchanged.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [d4a76c4](https://github.com/flashinfer-ai/flashinfer/commit/d4a76c440c117455a64db9a5abf281fb6d2660cc)

- **作者**: Bastian Hagedorn
- **时间**: 2026-11-12T21:14:06Z
- **提交信息**: fix(attn_scores): order the MQA logits kernels' TMEM dealloc after every math warp's tcgen05.ld (#8855)

## 📌 Description

`flashinfer/attn_scores/kernels/fp8_paged_mqa_logits.py` and
`fp4_paged_mqa_logits.py` free their accumulator TMEM without ordering
the other math warps' reads before the free.

Math warps 0-7 (two warp groups) read the UMMA accumulators with
`tcgen05.ld`. Math warp 0 is the allocator and, at the end of the
kernel, runs `tmem.relinquish_alloc_permit()` and `tmem.free(...)`, i.e.
`tcgen05.dealloc` from warp 0 alone (`cutlass.utils.TmemAllocator.free`
has no CTA barrier for a 1-CTA kernel). Nothing orders the last
`tcgen05.ld` of warps 1-7 before that dealloc: each warp's
`fence_view_async_tmem_load` (`tcgen05.wait::ld`) covers only its own
loads, the UMMA pipelines' `consumer_release` arrivals are waited on by
the UMMA warp and not by math warp 0, and each pipeline's consumer group
is one warp group, so warp group 0 learns nothing about warp group 1.
There is no barrier between the last load of warps 1-7 and the free. The
CuTe DSL's own `examples/blackwell/dense_gemm.py` does
`cute.arch.barrier()` right before `dealloc_tmem`.

`tcgen05.dealloc` does not clear TMEM, so the stale loads return the
right data unless something re-allocates the columns in between. With
the shipped launch (384 threads x 168 registers, >128 KB smem) one CTA
fits per SM and nothing else can take the freed columns before the CTA
exits, so the output is correct today; the ordering is still wrong and
breaks with any change in occupancy or any in-CTA reuse.

**Change**: one named barrier over all 256 math threads (id 2 in the fp8
kernel; id 3 in the fp4 kernel, where id 2 is `sfb_sync_barrier`),
reached after `fence_view_async_tmem_load` and before
`relinquish_alloc_permit` / `free`.

**Evidence**: the fp8 kernel is the FlashInfer copy of SGLang's
`cutedsl_fp8_paged_mqa_logits.py`, whose tail is identical line for
line. That kernel was run on a B200 (CUDA 13.0): with warps 4-7 held
back by a `nanosleep` before their `tcgen05.ld`, `globaltimer` probes
show warp group 1 issuing its loads after warp 0's `tcgen05.dealloc` in
148/148 CTAs (stall of 10 us or 100 us). The output stays correct
because nothing re-allocates the columns. When warp 0 re-allocates the
same columns right after its dealloc and writes a marker (what any other
allocator on the SM would do), 20/20 launches are wrong, 4736 elements
each (148 CTAs x the 32 kv positions warp 4 reads from lanes 0-31, all
in warp group 1's kv block); with the barrier, 0/20 at every stall
length. The fp4 kernel has the same tail and gets the same change; it
was compile-checked, not run.

## 🔍 Related Issues

SGLang original of the fp8 kernel: sgl-project/sglang#48728. Same class
of TMEM-release ordering as #6786 / #7443 / #8787 (there the allocator
was the MMA warp and the fix a phase-0 wait; here the allocator is a
math warp and the fix a barrier over the readers).

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues. (ruff 0.12.8 check + format and codespell
on the changed files; mypy not run.)

## 🧪 Tests

- [ ] Tests have been added or updated as needed. (No new test: the race
needs an injected stall plus a re-allocation of the freed columns to
become observable.)
- [ ] All tests are passing (`unittest`, etc.). (Not yet run on CI.)
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).

Suggested CI test targets: `tests/attn_scores/test_attn_scores.py
tests/attn_scores/test_attn_scores_adversarial.py`

## Reviewer Notes

Both kernels compile with the change (pre-LLVM dump identical apart from
the added barrier). The fence before the barrier is each thread's
`tcgen05.wait::ld`; the barrier then orders the last loads of warps 1-7
before warp 0's dealloc. A stricter variant would add
`tcgen05.fence::before_thread_sync` / `after_thread_sync` around the
barrier; `cute.arch` has no stable helper for those, and the DSL's own
kernels use the fence-plus-barrier form.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved synchronization during attention-score processing to ensure
asynchronous loads complete before temporary memory is released.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [0df46f4](https://github.com/flashinfer-ai/flashinfer/commit/0df46f4a66154ecc302fcd84ad7d8c9c23fbf7c4)

- **作者**: Ruoqian Guo
- **时间**: 2026-11-12T21:13:44Z
- **提交信息**: feat(mega_gate): experimental SM120 CuTe DSL backend for prepare_mega_gate (#8479)

<!-- .github/pull_request_template.md -->

## 📌 Description

An SM120 backend (RTX PRO Blackwell, compute capability 12.0) for the
experimental `prepare_mega_gate` API, written in CuTe DSL. It has the
semantics of DeepGEMM's `bf16_mega_gate`: the BF16 routing GEMM,
sqrt-softplus scoring, biased top-k, unbiased weight normalization and
logical-to-physical expert mapping run in one kernel.
`flashinfer/mega_gate.py` dispatches compute capability 12.x to it;
SM10x keeps the exported DeepGEMM programs. Target shapes are the
DeepSeek-V4-Flash (K=4096, 256 experts) and DeepSeek-V4.1-Flash (K=5120,
384 experts) routers, top-6.

Design (details in `flashinfer/experimental/sm12x_mega_gate/README.md`):
- Swap-AB `mma.sync` (128 experts per CTA as the A operand, tokens as
B), TMA + mbarrier pipeline with `ldmatrix`.
- Persistent worker groups of `L = ceil(E/128) * split_k` CTAs. FP32
split-K partials go to scratch, and a per-block score barrier with
self-rearming counters keeps it CUDA-graph safe.
- Gate warps rank block b while the MMA warps run block b+1. For decode,
a cooperative gate ranks up to 3 tokens per CTA. For prefill,
96/128-token blocks use 4x2 MMA warps.
- Programmatic dependent launch is supported.
- Schedule: a cost model fitted on the 110-SM RTX PRO 5000. For
K=4096/E=256 the model misranks the near-tied one-wave schedules, so
that shape uses a measured split table (`MEASURED_SPLITS`).

The SM10x programs are exported for K=5120, E=384 and top-6. Beyond
them, this backend also accepts other hidden sizes (multiples of 64), up
to 1024 experts (a multiple of 4), top-k up to 32 slots and no bias.
Token masks, image bias and shared-as-routed slots are supported as on
SM10x. It also supports two more inputs:
- **Fixed routing (`fix_routing_mask`)**, for hash-routed layers, as
DeepGEMM defines it. Flagged tokens take the logical experts already in
their `unmapped_topk_idx` row and are weighted from their unbiased
scores. They skip the top-k rounds; with the cooperative gate (on 110
SMs up to 256 tokens with 384 experts, 288 with 256) their flag and
experts are also loaded before the score wait. A call with every token
fixed takes about as long as a ranked one; the differences are within
run-to-run variation (`bench_mega_gate_sm12x.py --fixed-routing`).
- **An SM cap (`num_sms`)**, SM12x only: a new keyword-only argument
whose default (`None`) keeps existing calls unchanged. It leaves SMs to
kernels that run at the same time, for example communication overlapped
with the gate. Uncapped, calls of up to 256 tokens use 30–96 CTAs (5120
× 384) or 32–96 (4096 × 256). Capped at 64 SMs they take up to 1.1 µs
longer for 4096 × 256 (1–240 tokens) and up to 1.9 µs for 5120 × 384
(140 tokens; 1 token is unchanged), from single runs of
`bench_mega_gate_sm12x.py --cupti --no-baseline --num-sms 64` against
the same command without `--num-sms`.

Not implemented yet: `force_random`, which raises `NotImplementedError`.
SM121 is not enabled. Tuning was done only on the 110-SM RTX PRO 5000.

**Performance.** RTX PRO 5000 Blackwell (110 SMs). CUPTI timing, cold
L2, PDL off, top-6. Times in µs.

`benchmarks/bench_mega_gate_sm12x.py`: the fused call with physical map
and logical output. Baselines are a cuBLAS BF16→FP32 GEMM alone, and
that GEMM followed by b12x's Triton `route_topk`, timed together in one
CUDA graph. L2 is flushed before each replay, preserving the GEMM logits
between stages. Values below are medians of three independent process
runs.

```bash
python benchmarks/bench_mega_gate_sm12x.py --cupti --tokens 1 128 1024 4096 16384
python benchmarks/bench_mega_gate_sm12x.py --cupti --hidden 4096 --num-experts 256 --tokens 1 240 960 8192
```

| K × E | Tokens | Mega gate | cuBLAS GEMM alone | cuBLAS + Triton top-k
| Speedup vs cuBLAS + Triton |
|---|---|---|---|---|---|
| 5120 × 384 | 1 | 7.74 | 9.47 | 13.57 | 1.75× |
| 5120 × 384 | 128 | 9.92 | 9.63 | 13.92 | 1.40× |
| 5120 × 384 | 1024 | 28.22 | 37.47 | 49.12 | 1.74× |
| 5120 × 384 | 4096 | 91.17 | 101.06 | 136.51 | 1.50× |
| 5120 × 384 | 16384 | 317.76 | 338.11 | 471.04 | 1.48× |
| 4096 × 256 | 1 | 5.95 | 7.20 | 10.56 | 1.77× |
| 4096 × 256 | 240 | 9.76 | 11.20 | 14.88 | 1.52× |
| 4096 × 256 | 960 | 18.21 | 24.38 | 30.72 | 1.69× |
| 4096 × 256 | 8192 | 116.00 | 129.28 | 163.97 | 1.41× |

Against SGLang's router on the same GPU. This uses upstream SGLang (main
11d6878): a cuBLAS BF16→FP32 GEMM (`torch.mm(...,
out_dtype=torch.float32)`) followed by its Triton `moe_fused_gate`, with
both stages timed together in one CUDA graph and L2 flushed before each
replay. Values below are medians of three independent process runs. For
up to 16 tokens SGLang uses its own `tiny_gemm`, which could not be
loaded standalone, so cuBLAS stands in for it there. The numbers come
from a standalone script that loads SGLang's kernel modules; it is not
part of this PR. Both selected identical expert sets in every case we
measured.

| Shape | Tokens per call | Mega gate | SGLang router | Speedup vs
SGLang |
|---|---|---|---|---|
| 4096 × 256 | 6–240 | 6.2–9.6 | 10.1–14.1 | 1.38–1.86× |
| 5120 × 384 | 7–140 | 7.8–10.6 | 12.7–15.0 | 1.34–1.86× |
| 4096 × 256 | 1024–8192 | 18.2–114.2 | 28.3–143.1 | 1.15–1.58× |
| 5120 × 384 | 1024–8192 | 27.1–167.4 | 43.7–209.9 | 1.18–1.61× |

At decode sizes the kernel is close to the time it takes to read the
router weight from DRAM. For 5120 × 384 at 1 token, a standalone kernel
that only reads the 3.93 MB weight with 16-byte loads over all SMs takes
5.50 µs (CUPTI, cold L2; an empty kernel takes 1.22 µs), of the 7.7 µs
total. The rest is the top-k and the synchronization tail.

## 🔍 Related Issues

Tracking issue: #8897

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
reviewers may adjust): `tests/experimental/test_mega_gate_sm12x.py
tests/experimental/test_mega_gate_generated.py`

`tests/experimental/test_mega_gate_sm12x.py` checks the outputs against
an FP64 reference. It covers both router shapes over decode and prefill
token counts, other K/E/top-k, masks, image bias, physical mapping,
shared slots, deterministic mode (against the reference and batch
invariance across token counts), bitwise repeatability, CUDA graph
replay (including the first invocation in fresh processes, both cold
compilation and disk-cache reload), output-buffer overlap rejection,
invalid split-K overrides, uint32 hash wraparound, routing-rank order,
top-k through 32, fixed routing, the SM cap, NaN scores, input
validation and the CPU-only schedule invariants. The PDL test puts the
gate behind a producer that triggers its dependents before it writes the
tokens; with the gate's `griddepcontrol.wait` removed, that test fails.
All 213 tests pass on an RTX PRO 5000 Blackwell; the GPU tests skip off
SM120. The SM120 CI runners (170 and 188 SMs) pick other schedules than
the 110-SM board; with schedule selection forced to their picks, all 204
GPU tests pass for each SM count on the RTX PRO 5000.
`tests/experimental/test_mega_gate_generated.py` covers the SM10x branch
of the shared entry point, which this PR also touches.

## 🔬 Experimental Track

<!-- Only for PRs submitted under the experimental policy
(CONTRIBUTING.md → "Experimental APIs and Backends").
     Leave this section untouched for normal PRs. -->

- [x] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.
Tracking issue: #8897
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

```experimental-tests
tests/experimental/test_mega_gate_sm12x.py
tests/experimental/test_mega_gate_generated.py
```

## Reviewer Notes

The most useful review targets:
- **Synchronization in `kernel.py`:** the per-block score barrier and
its counter rearm, and the proxy fence between `ldmatrix` reads and TMA
refills of a stage.
- **Schedule selection in `heuristics.py`:** the cost model and the
measured split table.
- **The core entry point:** compute-capability dispatch in
`flashinfer/mega_gate.py`. It gains `num_sms` (keyword-only, default
`None`) and rejects a non-`None` value on SM10x.

Things to know:
- **Co-residency.** Each worker group spins until all of its CTAs
arrive, and there is no cooperative launch. The call hangs under an SM
budget smaller than one group (up to 30 or 32 CTAs at decode sizes, e.g.
a green context or an MPS partition), or next to a kernel that holds SMs
while it waits for the gate. The DeepGEMM programs have the same
requirement. The public docstring and the README say so. PDL is not a
risk: the next kernel launches only once every CTA has triggered or
exited.
- **Workspace.** The poll waits for exactly L arrivals. A
`score_barriers` buffer that was never zeroed, an aborted launch, or two
plans running concurrently on shared `scratch`/`score_barriers` would
hang. Workspace shapes depend on the chosen schedule, as on SM10x.
- **Deviations from DeepGEMM.**
- Where DeepGEMM traps, this backend clamps: replica counts and
fixed-routing expert ids.
- NaN scores rank last; a slot with no finite candidate gets the clamped
expert with weight 0, with or without a bias (tested).
- The score barrier rearms itself instead of using `%gridid` tags (a
CUDA graph kernel node keeps one grid id across replays).
- Accepted shapes: K a multiple of 64; E at most 1024 and a multiple of
4.
- **Limitations.**
- Compute capability 12.1 dispatches here and raises `RuntimeError`
until it is validated.
- `MEASURED_SPLITS` is keyed on the effective SM count, so a 188-SM
board capped to `num_sms=110` would take the RTX PRO 5000 table. Boards
with other SM counts (the SM120 CI runners have 170 and 188) take the
cost model.
- **PDL** is on by default. The dependents trigger fires before the
outputs are stored, so consumers must wait (`griddepcontrol.wait`).
- **Host cost.** TMA descriptors are encoded on the host on every
`run()`; CUDA graphs amortize it.
- **Proxy fence.** It is an empirical fix for an observed SM120 hazard,
one fence per stage.
- `_config` on `MegaGateSm12xPlan` is a private, test-only override.
- `examples/experimental/mega_gate.py` now also runs on SM120.
- DeepGEMM attribution: the package ships DeepGEMM's MIT notice
(`DEEPGEMM_NOTICE.txt`), as `deepgemm_mega_gate` does.
- `plan.route` reports `num_worker_groups` and `kernel`, where the SM10x
plan reports `num_workers`, `template` and `program`.
- Test cost: the 213-test file ran in 73 s on the RTX PRO 5000, with
some compiled specializations already cached. CuTe DSL emits deprecation
warnings for `cutlass.utils.LayoutEnum` and `SmemAllocator`, as for the
surrounding kernels.
- AI assistance (Claude Code and Codex) was used to implement, test and
review this change.

The runnable example is `benchmarks/bench_mega_gate_sm12x.py`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added an experimental fused mega-gate backend for supported SM120
GPUs, with routing, scoring, masking, shared experts, physical expert
mapping, and fixed-routing options.
* Added an optional SM count setting when preparing a mega-gate plan on
supported hardware.
* Added a benchmark comparing fused performance with an unfused
baseline.

* **Documentation**
* Added usage, hardware support, workspace, scheduling, and benchmarking
guidance, including limitations and requirements.

* **Tests**
* Added coverage for routing behavior, supported options, scheduling,
repeatability, and invalid inputs.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Codex <noreply@openai.com>

### [a63f775](https://github.com/flashinfer-ai/flashinfer/commit/a63f775b5c150704dd66e4fad9aac4dd2acf8e83)

- **作者**: Zhaowei Gu
- **时间**: 2026-11-12T19:09:37Z
- **提交信息**: fix(cake): ship build.json and csrc for the Muse Spark norm and TP MoE finalize backends (#9392)

<!-- .github/pull_request_template.md -->

## 📌 Description

As reported in #9387, the 0.7.3 and 0.7.4 wheels ship
`flashinfer/cake_muse_spark_norm_backend/` without its `build.json` and
`csrc/`, so when `backend="auto"` picks the Cake kernels the call fails
with `RuntimeError: .../build.json is missing`. `include-package-data`
is false, and that package has no `[tool.setuptools.package-data]`
entry. `flashinfer.cake_tp_moe_finalize_rmsnorm_backend` (the Cake route
of `tp_moe_finalize_rmsnorm`) has the same gap.

This adds both entries, matching the other top-level Cake backends, and
removes the xfail from the two existing
`test_package_data_lists_the_package` tests. They check that the entry
covers `build.json` and every source the manifest lists, which is the
check the issue asks for, done on `pyproject.toml` instead of a built
wheel. On a CPU-only machine they fail against main's `pyproject.toml`
and pass with this change. A wheel built from this branch has both
`build.json` files and every source they list, which adds 403 files and
about 1.5 MB to the wheel.

`experimental/cake_fp8_attention` and
`experimental/kimi_k3_vision_tower` have no entry either. I left them
out: they're experimental, the PyPI wheel drops experimental `csrc/`
anyway, and the `cake_fp8_attention` README says its wheels leave these
files out on purpose.

## 🔍 Related Issues

Fixes #9387

Related: #8440 adds a way to fetch the experimental kernel sources that
release wheels leave out. These two backends aren't experimental, so
like the other top-level Cake backends they should ship their
`build.json` and `csrc/` in the wheel, which is what this adds.

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

`pre-commit run --files` on the three changed files passes; I did not
run `--all-files`.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/norm/test_cake_muse_spark_norm_api.py
tests/comm/test_cake_tp_moe_finalize_rmsnorm_api.py`

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

Implemented and validated with Claude assistance.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Installed packages now include the build and source files required by
two additional backends, improving their availability in packaged
distributions.
* **Tests**
* Package-content checks for both backends now report failures directly
instead of marking them as expected.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: Zhaowei Gu <83746079+zw-g@users.noreply.github.com>

### [568ebcd](https://github.com/flashinfer-ai/flashinfer/commit/568ebcd255f490ecab164c9c26bf2245c89ef420)

- **作者**: Ji Sung Han
- **时间**: 2026-11-12T18:29:38Z
- **提交信息**: fix(autotuner): keep the op's own bucket mapper under autotune(tuning_buckets=...) (#8545)

<!-- .github/pull_request_template.md -->

## 📌 Description

Inside `autotune(tuning_buckets=...)`, tuning stored results under keys
built from
the bucket list (`make_bucket_mapper`), while lookups outside the
context use the
op's own `map_to_tuning_buckets`. When the largest bucket is off the
op's grid, the
keys differ. Example: vLLM tunes with `max_num_batched_tokens=21504`;
tuning stores
`21504`, but lookups for M in 16385..21504 ask for `32768`. Since #7626
this miss
is caught by the top-bucket fallback. This PR removes the miss itself.

**Change.** Keep the op's own mapper inside the override. The bucket
list still
decides which sizes are profiled, so tuning and lookups build the same
key by
construction (the profile tuned at 21504 is stored under 32768). This
also covers
#5450.

**Behavior change** (inside `autotune(tuning_buckets=...)` only; lookups
outside
the context are unchanged):

- The op's own mapper, not the list, maps a runtime size to its bucket.
- A size whose op bucket no listed size maps to uses the default tactic
inside
  the context. It used to be clamped or rounded to a listed bucket.
- Listed sizes that the op maps to the same bucket share one tuned
entry, profiled
  at the size equal to that bucket, or the largest of them if none is.
- `round_up` has no effect together with `tuning_buckets`.

The `autotune()` docstring and the #7626 fallback description (docstring
and
`docs/autotuning.rst`) are updated to match.

## 🔍 Related Issues

- #5450 (floor mapping under the override; #5449 is a near-duplicate).
- #7626 (merged): lookup fallback above the tuned range. It still covers
runtime
sizes above the tuned range; the off-grid top bucket no longer needs it.
- #5685 overlaps in the `round_up` docstring and tests. Whichever lands
second
  rebases.
- vllm-project/vllm#63159: vLLM-side workaround for the same mismatch,
not needed
  with this PR.

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

- [x] Tests have been added or updated as needed
(`tests/autotuner/test_autotuner_core.py`):
- New `test_tuning_buckets_off_grid_top_bucket_matches_inference_key`
checks the
stored keys: fails on main (`{8, 16, 24}`), passes here (`{8, 16, 32}`).
- New `test_tuning_buckets_profile_one_size_per_op_bucket` checks which
listed
sizes are profiled when several map to one op bucket: `{8, 12}` here;
the
    previous revision profiled the smallest (`{1, 10}`).
  - `test_autotune_context_both_overrides` and
`test_choose_one_with_custom_buckets_selects_best_tactic` assert that
the op's
    mapper decides.
- #7626's
`test_choose_one_above_overridden_top_bucket_uses_largest_tuned_profile`:
same tactics; the fallback is now logged once (for 32768) instead of
twice,
    because 8192 is a direct hit.
- [x] All tests are passing (`unittest`, etc.). On SM107, this branch on
main (b9455a23):
`tests/autotuner/` 421 passed; `tests/gemm/test_mm_bf16.py` 43 passed.
- [x] End to end on SM107 with `CuteDslFusedMoE` (E=128, top-k 8, hidden
4096,
      intermediate 1536) and `bf16_gemm`: tune M=21504 under
`autotune(tuning_buckets=(1024, 4096, 16384, 21504), round_up=True)`,
then run
with no autotune context. For M=21504, 20000, 16448 and 16385, main
serves the
tactic tuned at 21504 through the #7626 fallback; this PR serves the
same tactic
by a direct hit. Keys and lookups for the other sizes are unchanged. MoE
output
at M=16448 against the float reference: PASS, relative L2 error 0.2032
on both.
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/autotuner/ tests/gemm/test_mm_bf16.py`

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

- #7626 already fixes the symptom, so this PR cleans up the key itself.
Is dropping
  the list-defined mapping inside the context acceptable?
- Not run: a vLLM server end to end. The run above is at the FlashInfer
level.
- The one-line change was suggested by Mingyuan Ma (co-author).
- AI assistance (Claude, via Claude Code) was used to write parts of
this change and the tests. I reviewed every change and ran all of the
validation above on SM107.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Behavior Updates**
* Custom tuning buckets follow the operation’s existing lookup rules.
Listed sizes that map to the same operation bucket share one tuned
entry, profiled at the bucket value when listed or otherwise at the
largest matching listed size.
* When `tuning_buckets` is supplied, `round_up` is ignored. Runtime
sizes above the tuned range use the highest applicable tuned entry;
sizes below or between tuned buckets use the fallback tactic and count
as replay-coverage misses.
* **Documentation**
* Clarified custom-bucket profiling and lookup behavior, including
handling of above-range runtime sizes.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Ji sung Han <jisungh@nvidia.com>
Co-authored-by: Mingyuan Ma <111467530+Victor49152@users.noreply.github.com>

### [88702be](https://github.com/flashinfer-ai/flashinfer/commit/88702becdb6ce148ce2d9257b5da9ea266c5a69d)

- **作者**: Akaash Parthasarathy
- **时间**: 2026-11-12T18:16:36Z
- **提交信息**: feat(moe_ep): order and deduplicate Rubin tuning candidates (#9402)

<!-- .github/pull_request_template.md -->

## 📌 Description

The Rubin tuning grids currently follow their construction order, so a
small `--max-candidates` budget can miss useful tile and scheduling
choices. Use one order per variant across datatypes. Inference retains
all 32 choices and GenPhase retains all 8 or 11, depending on datatype.
Optional reduction choices stay adjacent, and full search remains the
default.

Remove duplicate knob dictionaries before measurement and before the CLI
applies its per-variant limit. JSON lists and Python tuples count as the
same choice; supplied order and the first occurrence are preserved.

## 🔍 Related Issues

Follow-up to #8575.

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
      Reason: targeted MoE EP tests cover the change.

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust):
`tests/moe_ep/test_sm107_block_scaled_contracts.py
tests/moe_ep/test_sm107_runtime_options.py
tests/moe_ep/test_sm107_tuning.py
tests/moe_ep/test_sm107_tuning_protocol.py
tests/moe_ep/test_sm107_variant_selection.py`

332 host tests passed with four existing CUDA-only skips. All-files
pre-commit passed. The same ordered grids were qualified in 25 inference
and 30 GenPhase GPU cases across five formats at EP2/EP4.

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

Prefixes remain workload-dependent; a one-candidate budget is not a
universal choice. Existing compatible tuning records remain usable.

Developed with Codex.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Autotuning now evaluates unique candidate configurations in the
supplied order, preserving custom ordering and avoiding repeated trials.
* Candidate limits select the first requested number of unique options
for each eligible variant; shorter candidate lists are used in full.
* **Documentation**
* Added details on default candidate counts and search order for
inference and GenPhase tuning.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [f776a15](https://github.com/flashinfer-ai/flashinfer/commit/f776a15b281a19fc809224f4fbae3274cb4ea1ef)

- **作者**: Brian K. Ryu
- **时间**: 2026-11-12T17:45:43Z
- **提交信息**: benchmarks: `--backends batch_invariant` in `flashinfer_benchmark.py` for the batch-invariant GEMM, quantization and sampling (#9368)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

**Benchmark changes only. No library code changes**

`--backends batch_invariant` runs a routine's operator with
`batch_invariant=True` (and `backend="auto"`): the batch-invariant
kernels of `flashinfer.batch_invariant` (#9009), listed next to the
routine's other backends so one run compares them on the same inputs
with the same method (CUPTI kernel time, cold L2, CUDA graph).

Covered: 
* GEMM: `mm_bf16`, `bmm_fp8`, `gemm_fp8_nt_groupwise`, `mm_mxfp8`,
`mm_fp4` (NVFP4 and MXFP4, with `--use_128x4_sf_layout`)
* Quantization: `mxfp8_quantize`, `mxfp4_quantize`, `nvfp4_quantize`, 
* Sampling:`softmax`, `log_softmax` and `log_probs`. 

Misc:
* **Refcheck.** `--refcheck` keeps each routine's check against the
torch reference and adds, for this backend, a bitwise batch-invariance
check (`check_batch_invariance` in `flashinfer_benchmark_utils.py`)
* **Small fixes on the way.** The softmax refcheck tolerance widens by a
few ulps for 16-bit outputs (both backends return the input dtype) and
the softmax bytes count the output at its actual dtype (the formula
assumed fp32); `gemm_fp8_nt_groupwise` returned `None` instead of its
(empty) result list when every backend was filtered. `nvfp4_quantize`'s
cross-backend bitwise refcheck prints a hint to set
`FLASHINFER_DISABLE_FP4_QUANT_FAST_MATH=1` so `cuda` / `cute-dsl` take
the exact path the batch-invariant kernel computes (on the smoke run's
random inputs they agreed bit for bit even with fast math on).

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
* Added a `batch_invariant` benchmark backend for selected GEMM,
quantization, and softmax operations on supported GPU architectures.
* Added benchmarks for `log_softmax` and `log_probs`; these routines use
the batch-invariant backend.
* Added optional bitwise checks that compare results across full
batches, sub-batches, individual rows, and row permutations.
* **Documentation**
* Updated benchmark guidance with backend support, architecture
availability, command-line options, and sample configurations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [bbeef7b](https://github.com/flashinfer-ai/flashinfer/commit/bbeef7b8e04b617477c3db46c749d37250925583)

- **作者**: IriKa
- **时间**: 2026-11-12T17:18:53Z
- **提交信息**: Add FP8 per-(token, head) slot-mapping paged KV quantize (#6863)

<!-- .github/pull_request_template.md -->

## 📌 Description

Add
`flashinfer.fp8_token_head_quantize_append_paged_kv_cache_with_slot_mapping`,
the native CUDA write-side counterpart to the FA2 per-(token, head) FP8
KV scale read path.

```python
flashinfer.fp8_token_head_quantize_append_paged_kv_cache_with_slot_mapping(
    append_key, append_value, slot_mapping,
    paged_kv_cache=(k_slot, v_slot),  # uint8 inline slots
    kv_cache_sf=(k_sf, v_sf),        # float32 views into the same slots
    kv_layout="NHD", kv_data_type="e4m3",
)
```

The operator accepts FP16/BF16 inputs, E4M3/E5M2 targets, NHD/HND
layouts, int32/int64 slot mappings, and head dimensions 64, 128, 256,
and 512. Each CUDA block handles one (token, head), computes `max(amax /
fp8_max, 1e-12)` on device, and writes the quantized bytes and FP32
scale in place. Negative and out-of-range slots are ignored; extra
padded input rows are not written. The write path supports CUDA graph
capture and replay.

Each K/V slot occupies `head_dim + 16` bytes: `[head_dim FP8 bytes |
4-byte FP32 scale | 12-byte padding]`. The padding preserves the 16-byte
alignment required by the FA2 reader. The caller supplies scale views
sliced from this storage; the existing reader interface is unchanged.

Trace export covers both layouts and both FP8 formats. Exported
initialization binds the definition's resolved Const axes, so standalone
replay needs only Var axes; E5M2 has distinct definitions and retains
its target format. Four generated JSON examples and standalone CPU/CUDA
replay tests cover these combinations.

Also adds API documentation and
`benchmarks/bench_fp8_token_head_quantize_append.py`, with a startup
dequantization check (cosine and relative L2 error) and cold-L2 timing
sweeps. Performance timings are not part of the validation reported
below.

## 🔍 Related Issues

Companion to #5272 (FA2 per-(token, head) FP8 KV scale read path).

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

Validation: `pre-commit run --files` passed for all eight files in
commit `7ae3af192`, including mypy, Ruff, and formatting hooks. The
all-files checkbox above remains unchecked because that broader command
was not run.

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
reviewers may adjust): `tests/attention/test_page.py
tests/attention/test_fp8_token_head_scale.py
tests/trace/test_fp8_token_head_append_trace.py
tests/trace/test_fi_trace_template_consistency.py
tests/trace/test_template_registry.py`

### Validation

The final code was tested on both GPUs, selected by UUID and confirmed
using `torch.cuda.get_device_name(0)` and compute capability:

| Device | FP8 writer | Write/read round trip | Trace replay | Combined
|
| --- | --- | --- | --- | --- |
| NVIDIA A100-PCIE-40GB (SM80) | 79 passed | 16 passed | 25 passed |
**120 passed** |
| NVIDIA GeForce RTX 2080 Ti (SM75) | 47 passed, 32 skipped | 8 passed,
8 skipped | 25 passed | **80 passed, 40 skipped** |

All 40 SM75 skips are BF16 cases: the operator/read path requires native
input dtype support, so BF16 combinations require SM80 or newer. The
FP16 round-trip cases executed successfully.

Command run for each GPU (`CUDA_VISIBLE_DEVICES` set to that GPU's
UUID):

```bash
export FLASHINFER_CUDA_ARCH_LIST="7.5 8.0"
python -m pytest \
  tests/attention/test_page.py \
  tests/attention/test_fp8_token_head_scale.py::test_fp8_pth_write_read_roundtrip_paged \
  tests/trace/test_fp8_token_head_append_trace.py \
  -k 'fp8_pth or fp8_token_head_append_trace' -q --tb=short
```

Coverage includes independent scale/FP8 reference checks, ignored slots,
untouched padding, page size 1, invalid inputs, CUDA graph replay,
layout/format dispatch and aliases, non-default Const shapes, shared
storage, and standalone initialization from generated JSON.

CPU template consistency and registry checks: **1198 passed, 2
skipped**:

```bash
CUDA_VISIBLE_DEVICES="" FLASHINFER_CUDA_ARCH_LIST="7.5 8.0" python -m pytest \
  tests/trace/test_fi_trace_template_consistency.py \
  tests/trace/test_template_registry.py -q
```

The full repository suite was not run. A broader `tests/trace/` run on
SM75 was stopped after POD/batch-attention cooperative-launch failures
in configurations exceeding that device's shared-memory budget; those
paths are outside this FP8 writer change. The all-tests checkbox remains
unchecked to distinguish the targeted results above from a full-suite
pass.

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

- Public API, CUDA binding/AOT exposure, inline data/scale layout, and
standalone trace replay are included. vLLM integration remains a
separate follow-up.
- Normal contribution track; this PR does not add experimental APIs or
backends.
- AI assistance was used for development and validation.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added FP8 per-token, per-head quantization and append support for
paged KV caches using slot mapping.
* Supports FP16/BF16 inputs, E4M3/E5M2 formats, NHD/HND layouts, and
32-bit/64-bit slot mappings.
  * Added tracing support for the new cache operation.

* **Documentation**
  * Added the operation to the public API documentation.

* **Tests**
* Added coverage for accuracy, validation, edge cases, and CUDA graph
usage.

* **Benchmarks**
* Added configurable performance benchmarking across supported
configurations.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: IriKa Qiu <qiujie.jq@gmail.com>
Co-authored-by: Claude Code <noreply@anthropic.com>

### [8dfc61b](https://github.com/flashinfer-ai/flashinfer/commit/8dfc61baf5e3342f9f7ffbf037eb6d25a4e5ceb3)

- **作者**: lazypool
- **时间**: 2026-11-12T17:18:37Z
- **提交信息**: fix(prefill): validate FA2 prefill head dimensions (#4312)

## Summary

FA2 prefill JIT-compiles a kernel per `(head_dim_qk, head_dim_vo)`
without validating it. Compilation succeeds for dimensions the kernels
cannot handle, so invalid shapes either produce silently wrong results /
out-of-bounds reads or fail late with a compile-time `static_assert`.
This PR adds `_check_head_dim` in `flashinfer/utils.py` so the Python
layer rejects those dimensions before any module build or kernel launch.

## What is rejected

Non-positive dimensions are rejected for every backend. The FA2-specific
rules apply only when the resolved backend is `fa2`; other backends
return after the positivity check. `_check_head_dim` raises `ValueError`
when:

- `head_dim_qk` or `head_dim_vo` is non-positive;
- either dimension is not a multiple of 64;
- `head_dim_vo > 256` and is not a multiple of 256 (`KernelTraits` caps
the output tile at 256 dims and `static_assert`s that it divides
`head_dim_vo`).

## Call sites

`_check_head_dim` runs after the backend is resolved and before the JIT
module build:

- `single_prefill_with_kv_cache`
- `BatchPrefillWithPagedKVCacheWrapper.workspace_size()` and `.plan()`
- `BatchPrefillWithRaggedKVCacheWrapper.plan()`

`workspace_size()` also passes `head_dim_qk`/`head_dim_vo` to
`determine_attention_backend()` and re-checks after `"auto"` resolves,
so workspace sizing and `plan()` select the same module. The batch
`plan()` paths check before `get_batch_prefill_module()`, so
`head_dim_vo=320/384/448` raises a clear `ValueError` instead of a
compile-time `static_assert`.

## Issues fixed

- #4299: FA2 head dims that are not multiples of 64 can read out of
bounds (`head_dim=96`) or return silently wrong results (`head_dim=72`).
- `head_dim_vo` 320/384/448: previously failed the `NUM_MMA_D_VO` tiling
`static_assert` at JIT build time; now rejected up front.

## Tests

- Added `tests/attention/test_prefill_head_dim_validation.py`: rejected
and accepted shapes across single, paged, and ragged prefill.

## Notes

- No public API change; `_check_head_dim` follows the existing
`_check_*` helpers.
- One-byte KV (FP8 / packed NVFP4) shapes are **not** rejected here.
Their wrong-output and out-of-bounds failures come from the FA2 one-byte
K/V load and swizzle path (`produce_kv` copies a row in 128-byte chunks,
and the `k128B` layout assumes 8-cell rows), which is a kernel defect,
not an input-contract rule. It is tracked separately: #5085 addresses
the FP8 case, and NVFP4 still needs a kernel fix. Encoding the current
limitation in the Python check would reject shapes that become correct
once the kernel is fixed.
- `flashinfer/decode.py` has the same latent non-multiple-of-64 issue;
left as a follow-up.

---------

Signed-off-by: lazypool <lazypool@proton.me>
Co-authored-by: WEI CHENG CHIU <waynehacking8@gmail.com>
Co-authored-by: Brian K. Ryu <43616432+bkryu@users.noreply.github.com>

### [656eaee](https://github.com/flashinfer-ai/flashinfer/commit/656eaee454f48479d6f07740670eb3e64a7eb98c)

- **作者**: Haobin Guo
- **时间**: 2026-11-12T14:10:25Z
- **提交信息**: fix(moe): check build before the pack contract in BatchInvariantMoeRunner (#9391)

<!-- .github/pull_request_template.md -->

## 📌 Description

`BatchInvariantMoeRunner.pack_inputs` (added in #9283) ran
`_validate_pack_contract(act)` before `_require_built()`. On a runner
that was never built, it then dereferenced `act` first. With the `None`
pack used by the lifecycle test, that raised `AttributeError` instead of
the `RuntimeError: ...build() must be called before execution.` that
every runner must raise. This broke the lifecycle test on `main`:

```
FAILED tests/moe/test_unified_moe_cutlass.py::test_registered_runner_execution_requires_build[pack_inputs-args0-BatchInvariantMoeRunner]
  flashinfer/fused_moe/runners.py:791: AttributeError: 'NoneType' object has no attribute 'routing_input_mode'
```

The test fails for any PR whose targeted CI includes `tests/moe/`, for
example the H100 run on #9260.

This PR swaps the two calls so `pack_inputs` checks the build state
first, then validates the pack. That is the order every other runner
already uses (cuDNN Frost, Frost low-latency, the warp-decode runners in
`runners.py`, and others). It changes no behavior for a built runner:
the same pack-contract errors are raised, and only the order relative to
the build guard differs.

## 🔍 Related Issues

- Regression from #9283
- Seen in the targeted H100 CI on #9260

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

(Ran `pre-commit run --files
flashinfer/fused_moe/batch_invariant/runner.py`: all hooks pass.)

## 🧪 Tests

- [x] Tests have been added or updated as needed. (The existing
`test_registered_runner_execution_requires_build` already covers this;
no new test is needed.)
- [x] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).

Suggested CI test targets: `tests/moe/test_unified_moe_cutlass.py
tests/moe/test_unified_moe_pack_contract.py
tests/moe/test_unified_moe_batch_invariant.py`

Local validation (SM100):

| Test | `main` | This PR |
| --- | --- | --- |
|
`test_unified_moe_cutlass.py::test_registered_runner_execution_requires_build`
| 1 failed (`BatchInvariantMoeRunner`) | 132 passed |
| `test_unified_moe_cutlass.py`, `test_unified_moe_pack_contract.py`,
`test_unified_moe_batch_invariant.py` | — | 634 passed, 55 skipped |

## Reviewer Notes

One-line reorder. AI-assisted (Claude Code): it diagnosed the CI failure
and drafted the change; the author reviewed it.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Input packing now checks that the runner has been built before
validating the activation pack. When the runner is not built, callers
encounter the build-state check first.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [1bdba87](https://github.com/flashinfer-ai/flashinfer/commit/1bdba872568a87391f64ffb91910e52aeff9479d)

- **作者**: Yang Xu
- **时间**: 2026-11-12T08:19:31Z
- **提交信息**: feat(attention): admit measured SM100 D256 paged GQA (#9386)

<!-- .github/pull_request_template.md -->

## 📌 Description

Extend SM100 BF16 paged-prefill `backend="auto"` to measured D256
grouped-query prefixes using the existing cuDNN graph interface. The new
native packed-GQA/split-KV support can serve this width; automatic
admission currently remains D128-only.

The additional domain is HND/page16, batch 1–4, query length 64–1024, KV
length 2048–32768, 8–64 query heads and GQA groups 2/4/8/16. Every
request needs KV >= 4*Q and must stay in the declared Q<=128 or Q>128
class. Work is computed from paired actual lengths, Hq*sum(Qi*KVi), with
a floor of 16 Mi for D256.

Admission uses only already available CPU metadata, including
independent query masks when supplied. It requires cuDNN 9.24+, FE
1.33+, and matching native packed-split and physical-origin flags for
the width. Existing feature and CUDA Graph retention guards remain in
force. D128 admission is preserved. Backend and FROST use one public
graph contract; this change does not force an engine.

## 🔍 Related Issues

Builds on cuDNN 9.24 enablement #9351, query-length fallback #9371, and
D128 expansion #9382. Requires the FE D256 packed-split and
physical-origin support in NVIDIA/cudnn-frontend#2471,
NVIDIA/cudnn-frontend#2481, NVIDIA/cudnn-frontend#2488 and
NVIDIA/cudnn-frontend#2489.

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
reviewers may adjust): `tests/cpu/attention
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

Validation of commit `5e1cef2680655311a34c8e4fe3f3687a70ca45c0` (base
`4cdf2f56f834a4bcbae3874e783eff338e927722`):

- **336 focused CPU tests** passed with CUDA uninitialized, plus **324
independent-oracle / no-readback checks**. The D128 predicate body is
AST-identical to main. Changed-file hooks, including mypy/Ruff, and `git
diff --check` pass.
- B200 (148 SM), source Frontend 1.33.0 at merged
NVIDIA/cudnn-frontend#2489 with matching native, actual cuDNN
**9.24.0.43**, Torch 2.14.1+cu130, CuTeDSL CUDA 13.4 compiler. Imported
source, native binary and every loaded cuDNN library were verified. This
is **source-build qualification**, not a released FE 1.33 wheel claim;
latest published FE is 1.32.3.
- **108/108 final-source cases passed**: 41 D256 admissions, 13 D256
fallback controls and 54 D64 fallback controls. Coverage includes
sampled FP64 O/LSE, all-row provider comparisons, eager and captured
changed-input execution, output rebinding, nondefault streams, actual
route assertions and stable graph-build counts.
- **10/10 public GPU tests passed**: two new D256 retained-capture
O/O+LSE cases, six existing runtime-scale cases and two
device-length/readback controls. The new cases cover strided Q,
independent query masks, physical token origins and changed lengths/page
mappings/values under the retained graph, with full valid-row FP64
references.
- **41 newly admitted cases:** geometric-mean speedup **2.74x
whole-graph replay / 2.68x drained eager wall**; across all108 cases
**1.47x / 1.45x**. No changed route is >5% slower in both AB and BA
orders in either metric. Five blocks of20 calls per arm/order;
plan/JIT/reference work is outside timing. The slowest admitted
two-order ratio is 0.647x for graph replay and 0.664x for drained eager.

Representative warm whole-graph medians (mean of the two order medians):

| B | Q per request | KV per request | Hq/Hkv | Parent auto / FA2 (us) |
New auto / cuDNN (us) |
|---:|---:|---:|---:|---:|---:|
| 1 | 96 | 8193 | 32/4 | 92.34 | 39.00 |
| 1 | 129 | 32767 | 16/8 | 288.92 | 114.67 |
| 2 | 96 | 8193 | 32/4 | 169.82 | 59.49 |
| 2 | 129 | 32767 | 16/8 | 614.61 | 222.20 |

The original 108-input D64/D256 candidate was frozen before its first
complete qualification. It passed numerics but failed performance on one
mixed-length D64 case; that combined candidate remains rejected. This PR
extracts the **complete unchanged D256 domain** and keeps all D64
native. The final-source run reuses those108 inputs and is not a fresh
unseen holdout. No threshold was fitted to remove the failed D64 cell.
On the earlier independent45-case D256 development survey, the unchanged
rule admits41 cases (previously0).

All newly admitted cases use the existing public cuDNN graph contract;
no provider or knobs are forced. Some default plans use packed split and
others do not. Public H100 CI may skip the new SM100/FE1.33 tests; the
B200 source-build evidence above is distinct from public CI coverage.
The rule does not establish default vLLM/SGLang reach, other
architectures/page sizes, or serving/TTFT gains.

A single representative shape can also be compared with the existing
benchmark CLI (on the same FE/native/runtime):

```bash
python benchmarks/flashinfer_benchmark.py \
  --routine BatchPrefillWithPagedKVCacheWrapper --backends fa2 auto \
  --batch_size 1 --s_qo 96 --s_kv 8193 --page_size 16 \
  --num_qo_heads 32 --num_kv_heads 4 --head_dim_qk 256 --head_dim_vo 256 \
  --q_dtype bfloat16 --kv_dtype bfloat16 --causal --refcheck --use_cuda_events
```

The fixed qualification harness measures five blocks of 20 calls in both
AB/BA orders, validates the actual provider, and records graph replay
and drained eager wall separately. CLI defaults are not the
qualification protocol.

Implemented and validated with Codex assistance.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Eligible paged GQA workloads with 256-dimensional heads can now be
automatically routed to the cuDNN backend when the required hardware,
software, and workload conditions are met.
* Workloads that do not meet the admission requirements continue to use
the native backend. Existing 128-dimensional routing remains unchanged,
and 64-dimensional workloads remain on the native path.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [ae90965](https://github.com/flashinfer-ai/flashinfer/commit/ae909654207091f2b1811bc8d0721bd5fcb77c90)

- **作者**: eigen
- **时间**: 2026-11-12T08:07:11Z
- **提交信息**: perf(cake_muse_spark_norm): re-cut the gated residual RMSNorm PDL routes at 1-128 rows (#9385)

Gated residual RMSNorm (`flashinfer.norm.gated_residual_rmsnorm`) has
four Cake variants: mode 0 (no weight) and mode 1 (weight), each with a
plain route and a PDL route. This PR changes only the two PDL routes
(`enable_pdl=True`, the default) for 1 to 128 rows on sm_100a, sm_103a
and sm_107a. It reassigns those rows among programs the Cake package
already ships, with no kernel change. Every other route, and every row
above 128, runs the same program as before.

The baseline is the previous Cake package on FlashInfer main. Over every
M from 1 to 128, not only the rows in the tables:

- **sm_103a:** 70 rows change program and none are slower. Mode 0
geomean is 1.067 (max 1.300) and mode 1 geomean is 1.159.
- **sm_100a:** 23 rows change program and none are slower. Mode 0
geomean is 1.165 (max 1.314) and mode 1 geomean is 1.108.
- **sm_107a:** 185 rows change program. Mode 0 geomean is 1.126 (min
1.023) and mode 1 geomean is 1.077. One row is slower: mode 1 at M = 66,
at 0.9913.

The package's other Cake variants are not changed by this PR. They are
gated residual next-RMSNorm (alpha tensor + post weight, alpha scalar +
post weight, alpha scalar without post weight) and RMSNorm + sigmoid
gate (plain and PDL routes), for nine variants in total, all shipping on
sm_100a, sm_103a and sm_107a.

All tables use hidden size 8192, latency in microseconds, and speedup =
previous / this PR. "=" means both sides run the same program on that
row. "gap" means the route has no Cake program for that row, so the call
runs the CuTe DSL kernel.

**NVIDIA GB300, sm_103a, 152 SMs, CUDA 13.4**

| M | mode 0 previous (us) | mode 0 this PR (us) | mode 0 speedup | mode
1 previous (us) | mode 1 this PR (us) | mode 1 speedup |
|---:|---:|---:|---:|---:|---:|---:|
| 1 | 1.095 | 1.095 | 0.9999 = | 1.347 | 1.346 | 1.0001 = |
| 2 | 1.218 | 1.218 | 0.9998 = | 1.412 | 1.412 | 0.9998 = |
| 4 | 1.220 | 1.220 | 0.9998 = | 1.450 | 1.454 | 0.9974 = |
| 8 | 1.282 | 1.282 | 1.0002 = | 1.475 | 1.475 | 1.0000 = |
| 16 | 1.337 | 1.337 | 1.0002 = | 1.539 | 1.539 | 1.0000 = |
| 17 | 1.411 | 1.283 | 1.0996 | 1.667 | 1.539 | 1.0832 |
| 19 | 1.411 | 1.347 | 1.0475 | 1.667 | 1.667 | 1.0002 = |
| 24 | 1.411 | 1.411 | 1.0000 = | 1.667 | 1.667 | 1.0000 = |
| 32 | 1.475 | 1.475 | 1.0000 = | 1.731 | 1.731 | 1.0000 = |
| 40 | 1.792 | 1.731 | 1.0351 | 1.987 | 1.987 | 1.0000 = |
| 48 | 1.859 | 1.795 | 1.0357 | 2.115 | 2.115 | 1.0000 = |
| 56 | 1.859 | 1.859 | 1.0000 | 2.115 | 2.115 | 1.0000 = |
| 64 | 1.920 | 1.920 | 1.0000 = | 2.142 | 2.133 | 1.0045 = |
| 65 | 2.179 | 1.920 | 1.1350 | 2.624 | 2.176 | 1.2059 |
| 66 | 2.499 | 1.923 | 1.2995 | 2.608 | 2.179 | 1.1969 |
| 72 | 2.179 | 1.923 | 1.1331 | 2.579 | 2.179 | 1.1835 |
| 80 | 2.243 | 2.075 | 1.0812 | 2.374 | 2.373 | 1.0007 = |
| 96 | 2.421 | 2.422 | 0.9993 = | 2.437 | 2.440 | 0.9987 = |
| 112 | 2.411 | 2.413 | 0.9992 = | 2.435 | 2.435 | 1.0000 = |
| 128 | 2.374 | 2.373 | 1.0005 = | 2.435 | 2.437 | 0.9994 = |
| 256 | 3.234 | 3.234 | 1.0000 = | 3.349 | 3.351 | 0.9993 = |
| 1024 | 11.398 | 11.406 | 0.9993 = | 11.561 | 11.562 | 0.9999 = |
| 2048 | gap | gap | - | 24.555 | 24.554 | 1.0001 = |
| 4096 | 49.098 | 49.086 | 1.0002 = | 48.811 | 48.822 | 0.9998 = |
| 8192 | 95.179 | 95.168 | 1.0001 = | 95.131 | 95.131 | 1.0000 = |
| 16384 | 188.104 | 188.107 | 1.0000 = | 187.712 | 187.706 | 1.0000 = |

**NVIDIA B200, sm_100a, 148 SMs, CUDA 13.4**

| M | mode 0 previous (us) | mode 0 this PR (us) | mode 0 speedup | mode
1 previous (us) | mode 1 this PR (us) | mode 1 speedup |
|---:|---:|---:|---:|---:|---:|---:|
| 1 | 1.220 | 1.220 | 1.0000 = | 1.444 | 1.445 | 0.9989 = |
| 2 | 1.284 | 1.284 | 1.0000 = | 1.502 | 1.508 | 0.9966 = |
| 4 | 1.348 | 1.348 | 1.0000 = | 1.476 | 1.476 | 1.0000 = |
| 8 | 1.348 | 1.349 | 0.9989 = | 1.477 | 1.478 | 0.9993 = |
| 16 | 1.412 | 1.412 | 1.0000 = | 1.603 | 1.603 | 1.0000 = |
| 17 | 1.476 | 1.412 | 1.0453 | 1.674 | 1.554 | 1.0772 |
| 19 | 1.476 | 1.476 | 1.0001 = | 1.710 | 1.711 | 0.9999 = |
| 24 | 1.476 | 1.476 | 0.9999 = | 1.678 | 1.680 | 0.9988 = |
| 32 | 1.539 | 1.539 | 1.0000 = | 1.754 | 1.749 | 1.0026 = |
| 40 | 1.926 | 1.926 | 1.0000 = | 2.189 | 2.179 | 1.0044 |
| 48 | 1.946 | 1.946 | 1.0000 = | 2.243 | 2.243 | 1.0000 = |
| 56 | 1.986 | 1.987 | 0.9992 = | 2.243 | 2.243 | 1.0000 = |
| 64 | 1.987 | 1.987 | 1.0000 = | 2.246 | 2.246 | 1.0000 = |
| 65 | 2.307 | 1.987 | 1.1610 | 2.691 | 2.246 | 1.1980 |
| 66 | 2.611 | 1.987 | 1.3140 | 2.691 | 2.246 | 1.1980 |
| 72 | 2.307 | 2.307 | 1.0000 = | 2.691 | 2.691 | 1.0000 = |
| 80 | 2.310 | 2.310 | 1.0000 = | 2.483 | 2.483 | 1.0000 = |
| 96 | 2.523 | 2.525 | 0.9994 = | 2.479 | 2.480 | 0.9994 = |
| 112 | 2.563 | 2.565 | 0.9994 = | 2.565 | 2.563 | 1.0006 = |
| 128 | 2.499 | 2.499 | 1.0000 = | 2.563 | 2.563 | 1.0000 = |
| 256 | 3.291 | 3.292 | 0.9997 = | 3.439 | 3.440 | 0.9998 = |
| 1024 | gap | gap | - | 14.305 | 14.306 | 0.9999 = |
| 2048 | gap | gap | - | 27.378 | 27.373 | 1.0002 = |
| 4096 | 51.322 | 51.277 | 1.0009 = | 52.954 | 52.869 | 1.0016 = |
| 8192 | 100.990 | 100.958 | 1.0003 = | 104.602 | 104.570 | 1.0003 = |
| 16384 | 202.933 | 202.902 | 1.0002 = | 208.486 | 208.273 | 1.0010 = |

**NVIDIA R200 (VR200 board), sm_107a, 212 SMs, CUDA 13.5.** One row is
slower: mode 1 at M = 66 (0.9913).

| M | mode 0 previous (us) | mode 0 this PR (us) | mode 0 speedup | mode
1 previous (us) | mode 1 this PR (us) | mode 1 speedup |
|---:|---:|---:|---:|---:|---:|---:|
| 1 | 1.130 | 1.130 | 0.9998 = | 1.306 | 1.306 | 1.0000 = |
| 2 | 1.152 | 1.152 | 0.9998 = | 1.373 | 1.373 | 1.0005 = |
| 4 | 1.211 | 1.211 | 0.9998 = | 1.411 | 1.413 | 0.9986 = |
| 8 | 1.216 | 1.215 | 1.0009 = | 1.486 | 1.487 | 0.9991 = |
| 16 | 1.243 | 1.243 | 1.0001 = | 1.552 | 1.533 | 1.0129 |
| 17 | 1.369 | 1.253 | 1.0924 | 1.544 | 1.545 | 0.9999 = |
| 19 | 1.371 | 1.269 | 1.0811 | 1.540 | 1.540 | 1.0005 = |
| 24 | 1.364 | 1.270 | 1.0735 | 1.564 | 1.563 | 1.0002 = |
| 32 | 1.364 | 1.364 | 1.0000 = | 1.688 | 1.687 | 1.0003 = |
| 40 | 1.483 | 1.404 | 1.0558 | 2.070 | 1.748 | 1.1843 |
| 48 | 1.526 | 1.526 | 0.9994 = | 2.083 | 2.040 | 1.0211 |
| 56 | 1.689 | 1.689 | 0.9998 = | 2.103 | 2.066 | 1.0177 |
| 64 | 1.688 | 1.688 | 1.0000 = | 2.108 | 2.053 | 1.0269 |
| 65 | 2.117 | 1.742 | 1.2151 | 2.121 | 2.064 | 1.0273 |
| 66 | 2.057 | 1.684 | 1.2217 | 2.110 | 2.128 | 0.9913 |
| 72 | 2.092 | 1.718 | 1.2182 | 2.119 | 2.075 | 1.0213 |
| 80 | 2.135 | 1.807 | 1.1812 | 2.141 | 2.092 | 1.0234 |
| 96 | 2.122 | 1.920 | 1.1048 | 2.196 | 1.980 | 1.1086 |
| 112 | 2.179 | 1.881 | 1.1583 | 2.203 | 1.998 | 1.1023 |
| 128 | 2.166 | 1.909 | 1.1345 | 2.227 | 2.058 | 1.0822 |
| 256 | gap | gap | - | 3.012 | 3.014 | 0.9993 = |
| 1024 | 8.652 | 8.652 | 1.0000 = | 8.765 | 8.763 | 1.0002 = |
| 2048 | 17.927 | 17.929 | 0.9999 = | 17.722 | 17.731 | 0.9995 = |
| 4096 | 34.599 | 34.596 | 1.0001 = | 34.296 | 34.292 | 1.0001 = |
| 8192 | 64.281 | 64.288 | 0.9999 = | 71.303 | 71.296 | 1.0001 = |
| 16384 | 127.456 | 127.456 | 1.0000 = | 138.661 | 138.819 | 0.9989 = |


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Improvements**
* Updated gated residual RMS normalization kernel selection across
SM100, SM103, and SM107 GPUs for a revised range of input row counts.
* Added an updated SM107 implementation, including support for CUDA 13.4
and revised routing for larger inputs.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [4cdf2f5](https://github.com/flashinfer-ai/flashinfer/commit/4cdf2f56f834a4bcbae3874e783eff338e927722)

- **作者**: Yang Xu
- **时间**: 2026-11-12T06:28:18Z
- **提交信息**: refactor(attention): drop obsolete cuDNN Frontend compatibility paths (#9376)

<!-- .github/pull_request_template.md -->

## 📌 Description

FlashInfer already requires `nvidia-cudnn-frontend>=1.32.0`, but
attention still parsed older FE versions, probed the 1.31 replay-hint
signature, and carried the 1.30 short-cache fallback. Remove those
unreachable compatibility paths and their obsolete plumbing. Supported
frontends always receive the replay hint for captured decode plans; the
old always-skipped short-cache test now checks automatic cuDNN routing
and O/LSE numerics at both table widths.

Keep backend version/bug guards, native binding feature checks,
missing-runtime fallback, split controls, and the current
automatic-selection envelope. This does not change the dependency floor
or add D64/D256 paged admission.

## 🔍 Related Issues

Related to #9351 (cuDNN 9.24 enablement); independent of #9371
(query-length fallback validation).

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

Changed-file `pre-commit run --files` passed, including mypy and Ruff;
the entire repository was not reformatted. `git diff --check` passed.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: targeted attention tests cover the changed wrappers and runtime
guards.

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/attention/test_cudnn_decode.py
tests/attention/test_cudnn_prepared_graph.py
tests/cpu/attention/test_cudnn_prepared_contract.py
tests/cpu/utils/test_cudnn_decode_auto_rule.py`

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

Validation uses the released minimum FE 1.32.0 and actual loaded cuDNN
9.24.0.43, with import paths and shared-library hashes checked. CPU: 236
tests pass. An independent old/new comparison found identical decisions
across 64,857 decode inputs and 672 prefill backend/native/runtime
combinations without initializing CUDA.

B200: **18/18 focused GPU tests pass** with FE 1.32.0 / cuDNN 9.24.0.43.
Coverage includes short caller tables, replay-hint plan keys/capture,
eager versus captured auto routing, per-plan reevaluation,
missing-runtime fallback, batch-invariant split controls, and retained
paged capture with changed lengths/data and O/LSE. Actual CI is
requested separately for the final head.

Review focus: preserve backend/FROST parity and distinguish guaranteed
FE APIs from runtime/native capabilities. Historical measured selector
thresholds remain unchanged. This is a compatibility cleanup, not a
performance or serving-speedup claim. AI assistance: authored and
validated with OpenAI Codex.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* cuDNN decode routing now relies on runtime availability and CUDA
capability checks rather than frontend version thresholds. CUDA graph
replay hints are passed when graph-compatible.
* **Documentation**
* Clarified backend capability requirements for attention features and
graph support.
* **Tests**
* Updated coverage for runtime availability, backend selection, and CUDA
graph behavior.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [1ad5ab7](https://github.com/flashinfer-ai/flashinfer/commit/1ad5ab7850f8bc0cf904ebcc9912a476a6dd5ba2)

- **作者**: Yang Xu
- **时间**: 2026-11-12T06:08:13Z
- **提交信息**: feat(attention): widen measured SM100 D128 paged auto domains (#9382)

<!-- .github/pull_request_template.md -->

## 📌 Description

Extend SM100 BF16 D128 paged-prefill `backend="auto"` to additional
measured long-query, larger-batch and full-prefill shapes. For example,
B6/Q256/KV4096 now selects cuDNN instead of FA2. Existing admissions are
preserved, including short prefixes and the original 8 Mi paired-work
floor.

Additional admission uses only CPU metadata already available to
`plan()` and requires at least 16 Mi query-key pairs across heads. Full
prefill requires per-request Q=KV and maximum Q1024–16384. Other
prefixes require every Q>128, maximum Q8192, and maximum KV2048–32768.
HND/page16, BF16, D128, existing head ratios, feature restrictions, and
the qualified runtime guard remain in force. Independent Q overrides and
device-only metadata retain the original rule.

This changes plan-time admission through the existing cuDNN graph
contract; it does not force an engine or add a device-to-host copy.
Tests cover old admissions, work/shape boundaries, runtime/architecture
rejection, and actual auto routing with non-unit runtime scales.

## 🔍 Related Issues

Builds on cuDNN 9.24 enablement #9351 and the query-length contract fix
#9371.

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
reviewers may adjust): `tests/cpu/attention
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

Validation of commit `d3d77ba1ccf9ba1bdf4b599332dd0759f893c6c3`:

- 192 focused CPU tests passed; 13,998 comparisons establish that the
production predicate matches the separately frozen additive candidate.
No existing admission is withdrawn.
- Changed-file pre-commit hooks passed, including mypy/Ruff; `git diff
--check` passed. The entire repository was not reformatted.
- B200 (148 SM), released Frontend 1.32.0, actual cuDNN 9.24.0.43, Torch
2.14.1+cu130, CuTeDSL CUDA 13.4 compiler: all **113 independent held-out
shapes** passed sampled FP64 O/LSE references, all-row provider
comparisons, eager/captured changed-input replay, output rebinding,
nondefault streams, route assertions and stable graph-build counts.
Source/native/loaded-library identity was verified.
- All **8 public GPU regressions** passed: six actual-auto runtime-scale
cases and two device-length/readback controls. Existing tolerances were
unchanged.
- **49 newly admitted cases:** geometric-mean speedup **2.35x** for
whole-graph replay and **2.31x** for drained eager wall time. Across all
113 cases, the corresponding speedups are **1.45x / 1.44x**. No changed
route was >5% slower in both AB and BA orders in either metric. Five
blocks of 20 calls per arm/order; medians retained.
- On a separate 415-shape development set, admission grows from **191 to
326** (46.0% to 78.6%), with **zero withdrawals**. This is dataset
coverage, not a workload-weighted serving claim.

Representative warm whole-graph medians (mean of the two order medians):

| B | Q | KV | Hq/Hkv | Parent auto / FA2 (us) | New auto / cuDNN (us) |
|---:|---:|---:|---:|---:|---:|
| 1 | 1536 | 16383 | 32/4 | 1336.74 | 401.23 |
| 6 | 384 | 8190 | 64/4 | 1719.80 | 775.58 |
| 6 | 1536 | 1536 | 8/8 | 141.61 | 60.16 |
| 2 | 16384 | 16384 | 24/3 | 9186.41 | 3276.98 |

The qualification used explicit `seq_lens` / page tables and per-request
CPU lengths with deterministically permuted physical pages. Public
regression tests also cover ordinary `plan()` metadata inference.
`use_cuda_graph` provider-retention rules are unchanged.

The original broad proposal was rejected on performance; its withdrawals
and short-Q regressions are not part of this additive expansion.
Performance qualification uses new shapes sealed before execution. Warm
CUDA Graph replay and drained eager wall time are separate metrics;
plan/JIT is outside timing. No serving/TTFT speedup is claimed.

Implemented and validated with Codex assistance.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Automatic backend selection now supports a broader range of paged BF16
attention workloads on compatible SM100 hardware, including larger
batches and longer prefill sequences. Existing supported workloads
remain eligible, subject to request-length, layout, and runtime
requirements.
* **Documentation**
* Updated backend guidance to describe the expanded workload support and
its eligibility limits.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [072c706](https://github.com/flashinfer-ai/flashinfer/commit/072c706e4233597e8ec7365112195bc422b1f05e)

- **作者**: Yang Xu
- **时间**: 2026-11-12T04:41:51Z
- **提交信息**: fix(attention): reject unsupported independent query lengths in paged fallback (#9371)

<!-- .github/pull_request_template.md -->

## 📌 Description

Paged prefill accepts `seq_lens_q` independently of the physical query
offsets, but non-cuDNN providers derive their query lengths from
`qo_indptr`. When auto falls back to FA2, this can silently change
causal alignment. For example, physical Q128 with actual Q1 and KV8192
can return 0.015869 instead of the expected 2.0 for a zero-Q/K,
tail-valued-V control.

Resolve the prospective backend before committing plan state, then
reject an independent Q mask that the selected provider cannot
represent. A redundant CPU mask equal to the query-offset differences
remains accepted. Device masks are not copied back to prove equality.
The error identifies the unsupported contract and the available
alternatives. The existing provider admission rules are unchanged.

Regression coverage checks explicit and auto fallback, CPU/device
metadata, existing FA2 captures, and both eager and retained CUDA Graph
execution after a rejected replan. It also verifies that rejected plans
leave metadata, schedules, and accepted plan objects untouched.

## 🔍 Related Issues

Found while qualifying cuDNN 9.24 paged auto admission following #9351.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

Changed-file hooks passed as directed by `AGENTS.md`; the whole-tree
command above was not run.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: Targeted paged planning and retained-capture coverage is
sufficient; no shared build or global dispatch infrastructure changes.

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust):
`tests/attention/test_paged_query_lengths_contract.py
tests/attention/test_batch_prefill.py
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

Validation on production head `24669c6d1bcd`:

- 143 targeted local CPU tests passed; CUDA remained uninitialized. The
18 new rejection checks fail on the previous implementation.
- 8 GPU regressions passed on B200 with released Frontend 1.32.0 and
cuDNN 9.24.0.43, with source/native/library identity verified.
- Actual [CI run
43119601068](https://github.com/flashinfer-ai/flashinfer/actions/runs/43119601068)
passed: CPU 9,214 passed / 20 skipped; H100 184 passed / 118 skipped;
six AOT builds and three provider-spec lint jobs passed. The eight new
GPU cases were SM100-gated in that run.
- Review follow-up broadens the explicit FA2 cases to other BF16-capable
GPUs while preserving the SM100 gate for cuDNN auto. Production code is
unchanged; the expanded H100 coverage awaits the new-head targeted CI
request.



<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Invalid paged query-length inputs are now rejected during planning,
before they can alter an existing plan.
* Non-cuDNN backends now accept query lengths only when they match the
lengths implied by the query offsets.
* Rejected replanning preserves the previously accepted plan and its
results, including during captured execution.
* **Documentation**
  * Clarified the query-length requirements for paged attention.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [286c22a](https://github.com/flashinfer-ai/flashinfer/commit/286c22a6ab6e4471d8e405ec80deefb56ddbc7aa)

- **作者**: Ruoqian Guo
- **时间**: 2026-11-12T02:37:54Z
- **提交信息**: perf(moe_ep): faster SM90 FP8 pull MegaMoE autotuning (batched/rotated dispatch pull, blockwise N72/N80 tiles) (#9209)

<!-- .github/pull_request_template.md -->

## 📌 Description

This PR brings the dispatch and epilogue improvements of #7961 (SM90
pull-style CuTe-DSL MegaMoE, packed FP4) to the FP8 kernels (per-tensor
and blockwise), mainly through autotuning.

**What changes for FP8.**

- **Batched and rotated dispatch pull as tactic fields.** The kernel's
`TokenComm` already supports keeping several rows in flight per active
dispatch warp in the idle slots of the 4-slot pull buffer
(`dispatch_pull_batch`), and rotating the rows a warp takes on each pass
(`dispatch_pull_rotate`); FP8 always used 1/False. They are now FP8
config, backend and tactic fields. A batch above 1 needs
`compact_pull_buffer=False`, `epi_warps` token-back, no `dedup_dispatch`
/ `grouped_token_back`, and batch x `active_dispatch_warps` <= 4;
rotation needs `epi_warps` token-back. One check
(`tuner.validate_dispatch_pull`) serves FP8 and packed FP4.
- **Autotune candidates.** From 1024 tokens per rank (one active
dispatch warp, no dispatch dedup), every `epi_warps` candidate also gets
three pull variants: rotation, a batch of 3, and both; ping-pong
candidates get the rotation only, since batching never measured faster
on them (38 -> 81 candidates). The heuristic table is unchanged: on
H7168/E384/EP4 the 4-slot buffer costs 21 KiB of AB-stage SMEM and
batching is 0.5-6.6% slower, so it is a tuning choice, not a default.
- **Blockwise N72/N80 swap-AB tiles (M256).** One task holds an expert's
65-80 rows where N64 needs a second, nearly empty tile, and blockwise
N128 spills. The activation-SF pool is padded to a multiple of the tile.
Blockwise autotune candidates add these tiles (40 / 89 candidates).
- **Shared swap-AB epilogue code.** With `epi_warps` token-back, the two
epilogue warpgroups of an M256 non-ping-pong FP8 kernel now run one
FC1/FC2 code copy, as packed FP4 does. Blockwise N64 keeps one copy per
half: it runs near the register limit and the shared copy measured
2.5-4% slower there. Per-tensor M256N64 runs 0.988-0.996x on the EP2
shape.
- **Compile key.** `compact_pull_buffer`, `generate_c` and the two pull
fields are now part of the FP8 compile key. The missing fields were not
reachable before (every config change clears the compiled kernel), but
the key now matches its stated contract.

**Behavior changes.**

- `Sm90_Fp8_Fp8_Bf16_PullCutedsl_MegaMoeConfig` and the shim entry
points take `dispatch_pull_batch` / `dispatch_pull_rotate` (default
`None` = follow the tactic). An explicit value wins over a cached or
table tactic; an explicit batch above 1 uses the 4-slot buffer. When the
caller's own layout (dispatch-side token-back, `dedup_dispatch`, more
dispatch warps) rules out a tactic's batch or rotation, the rest of the
tactic applies with the serial pull.
- The FP8 backend rejects `knobs="auto"` with an explicit
`dispatch_pull_batch` or `dispatch_pull_rotate`, including `1` and
`False`. Leave both `None` to tune; `knobs=None` and knob dicts preserve
explicit pull precedence. Online autotuning controls
`compact_pull_buffer` through its tactics and does not preserve the
caller's bool.
- Blockwise swap-AB N72/N80 requires `generate_c=False`. Config
validation rejects `generate_c=True` before kernel construction because
its 128-row expert padding does not align the activation-SF TMA bases to
N72/N80.
- The FP8 frontend's `apply_knobs` resets pull fields a knob dict omits
to the defaults (compact buffer, serial, unrotated), including for `{}`,
so an autotune candidate never inherits the previous candidate's pull
settings. `apply_knobs(None)` leaves the current config unchanged.
- Existing FP8 knob-cache entries stay valid; re-tune to pick up the new
candidates. From 1024 tokens per rank a bucket has about twice as many
candidates to time.
- The SM90 mega bench accepts the fields in `--fp8-knobs-json` and as
`--dispatch-pull-batch` / `--[no-]dispatch-pull-rotate`.

**Performance.** H200 SXM, SM clocks locked at 1830 MHz, the benchmark's
block-permutation routing. Each tree was tuned into its own cache
(`python -m flashinfer.moe_ep.tune --dtype sm90_fp8_e4m3
--fp8-scale-mode <mode> --gate-up-clamp 10`), which
`benchmarks/moe_ep/backends/mega/kernel/sm90/bench_moe_ep_sm90_mega.py`
then read with `knobs=None` (10 warmup and 50 timed iterations in 3
rounds, 600 µs padding, per-rank median, maximum over ranks). Every
bucket ran its cached winner (checked from the recorded tactic). The
trees ran in alternating fresh processes (main, PR, PR, main, main, PR).
Ratios are medians of the three paired PR/main ratios (range in
brackets), µs values are medians over processes. "main" is the #7961
head, whose SM90 pull and FP8 files match current main. The EP4
per-tensor 1024 row comes from a separate run of that bucket, re-tuned
after ping-pong candidates lost their batch variants.

**H7168/I3072/E384/top-6, EP4, FP8 per-tensor, tuned on both sides**

| Tokens/rank | main µs | PR µs | PR/main | Tactic, main → PR |
|---:|---:|---:|---:|---|
| 8 | 685.5 | 686.1 | 1.001 [0.996–1.007] | pp M128N8: same |
| 16 | 1025.5 | 1025.7 | 1.000 [1.000–1.001] | pp M128N8: same |
| 32 | 1290.3 | 1289.9 | 1.000 [0.999–1.000] | pp M128N8: same |
| 64 | 1427.8 | 1427.5 | 1.000 [0.999–1.000] | pp M128N8: same |
| 128 | 1488.9 | 1489.2 | 1.000 [1.000–1.000] | pp M128N16: same |
| 256 | 1508.8 | 1509.5 | 1.001 [1.000–1.001] | pp M128N16: same |
| 512 | 1569.0 | 1569.2 | 1.000 [1.000–1.000] | pp M128N32: same |
| 1024 | 1686.5 | 1673.8 | 0.992 [0.990–0.994] | pp M128N128: pp
M128N128 → pp M128N64, rotation |
| 2048 | 2130.8 | 2136.1 | 1.002 [0.999–1.005] | pp M128N128: same |
| 4096 | 3476.8 | 3486.5 | 1.002 [0.997–1.010] | pp M128N128: same |
| 8192 | 6432.9 | 6374.8 | 0.994 [0.986–0.997] | pp M128N128: same |
| 16384 | 12394.0 | 12424.5 | 1.002 [0.998–1.002] | pp M128N128: same |
| 32768 | 24863.9 | 24905.3 | 1.001 [1.001–1.004] | pp M128N128: same |

**H7168/I3072/E384/top-6, EP4, FP8 blockwise, tuned on both sides**

| Tokens/rank | main µs | PR µs | PR/main | Tactic, main → PR |
|---:|---:|---:|---:|---|
| 8 | 692.8 | 693.7 | 1.002 [1.000–1.002] | pp M128N8: same |
| 16 | 1049.8 | 1035.6 | 0.986 [0.986–0.987] | pp M128N16: pp M128N16 →
pp M128N8 |
| 32 | 1299.2 | 1299.5 | 1.000 [1.000–1.000] | pp M128N8: same |
| 64 | 1458.5 | 1458.8 | 1.000 [1.000–1.000] | pp M128N16: same |
| 128 | 1502.8 | 1502.5 | 1.000 [1.000–1.000] | pp M128N16: same |
| 256 | 1525.5 | 1526.4 | 1.000 [1.000–1.001] | pp M128N16: same |
| 512 | 1733.0 | 1732.2 | 1.000 [0.999–1.000] | M64N256: same |
| 1024 | 1719.5 | 1719.3 | 1.000 [1.000–1.000] | M64N256: same |
| 2048 | 2533.9 | 2533.3 | 1.000 [0.988–1.005] | M64N256: rotation |
| 4096 | 4548.2 | 4547.9 | 0.995 [0.993–1.002] | M64N256: rotation |
| 8192 | 8616.2 | 8515.7 | 0.989 [0.987–0.991] | M64N256: reuse → epi
token-back |
| 16384 | 16512.9 | 16426.9 | 0.995 [0.994–0.995] | M64N256: scheduler |
| 32768 | 32450.6 | 32485.4 | 1.001 [0.998–1.004] | M64N256: rotation |

**H2560/I640/E512/top-10, EP2, FP8 per-tensor, tuned on both sides**

| Tokens/rank | main µs | PR µs | PR/main | Tactic, main → PR |
|---:|---:|---:|---:|---|
| 1024 | 453.6 | 440.9 | 0.973 [0.971–0.975] | M64N256: scheduler, batch
3 |
| 2048 | 711.8 | 649.2 | 0.912 [0.911–0.915] | M64N256: batch 3 |
| 4096 | 1225.2 | 1091.1 | 0.890 [0.890–0.891] | M64N256: batch 3 |
| 8192 | 2248.2 | 1951.2 | 0.868 [0.868–0.870] | M64N256: batch 3 |
| 16384 | 4263.7 | 3696.9 | 0.867 [0.867–0.868] | pp M128N128: pp
M128N128 → M64N256, batch 3 |

**H2560/I640/E512/top-10, EP2, FP8 blockwise, tuned on both sides**

| Tokens/rank | main µs | PR µs | PR/main | Tactic, main → PR |
|---:|---:|---:|---:|---|
| 1024 | 468.3 | 454.4 | 0.970 [0.970–0.972] | M64N256: scheduler, batch
3 |
| 2048 | 742.8 | 662.3 | 0.892 [0.892–0.893] | M64N256: scheduler, batch
3 + rotation |
| 4096 | 1255.7 | 1127.8 | 0.898 [0.897–0.900] | M64N256: scheduler,
batch 3 |
| 8192 | 2295.9 | 1981.5 | 0.863 [0.863–0.864] | M64N256: batch 3 |
| 16384 | 4422.5 | 3788.8 | 0.857 [0.856–0.857] | M64N256: batch 3 |

Untuned (heuristic) paths: 0.999-1.001 on the EP2 shape; on the EP4
shape 0.996-1.001 up to 512 tokens per rank and 0.995-1.011 at 2048 /
8192, where the clocks hit the power cap (A/A spread up to 2%) and the
cubins are unchanged. Outputs are byte-identical to the base at every
point.

## 🔍 Related Issues

Follow-up to #7961: the kernel-side pull batch/rotation and the shared
epilogue code come from it.

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
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust):
`tests/moe_ep/test_moe_ep_sm90_pull_fp8_mega_multirank.py
tests/moe_ep/test_sm90_pull_fp8_tuner.py
tests/moe_ep/test_moe_ep_sm90_pull_mxfp4_mega_multirank.py`

Existing tests include parameter rows for batched/rotated pulls
(including dispatch dedup and two dispatch warps, with checks that
settings reach the kernel) and blockwise N72/N80 tiles, plus assertions
for tuner validity and candidates, configuration resolution and
validation. Host checks, the FP8 tuner suite, FP8/MXFP4 multirank tests
and `pre-commit run --all-files` passed on 4x H100 80GB. FP8 cubins with
the new fields at their defaults are byte-identical to the base; the
shared epilogue copy changes only M256 non-ping-pong `epi_warps` cubins
(not blockwise N64), with byte-identical outputs.

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

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added configurable dispatch-pull batching and rotation for FP8
workloads, with tactic-resolved defaults when settings are omitted.
* Added blockwise swap-AB tile sizes N=72 and N=80 for supported
configurations. Autotuning can consider these tiles and eligible
dispatch-pull variants.
* **Bug Fixes**
* Added validation for incompatible pull settings, token-back options,
and tile configurations.
* **Documentation**
* Expanded tuning guidance with configuration constraints, defaults, and
autotuning candidates.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [c2f2071](https://github.com/flashinfer-ai/flashinfer/commit/c2f207129becf6638ccbc413fb2b58e586a5deec)

- **作者**: feih-nv
- **时间**: 2026-11-12T01:46:43Z
- **提交信息**: fix(moe): make zero tokens a no-op in the DSv3 routing launcher and check the launch (#9345)

<!-- .github/pull_request_template.md -->

## 📌 Description

Port of TensorRT-LLM
[16df7eaf2](https://github.com/NVIDIA/TensorRT-LLM/commit/16df7eaf251ab981021f355a0f7608b9248e945c)
(NVIDIA/TensorRT-LLM#19727; only its `noAuxTcKernels.cu` hunk, the rest
of that commit is a DeepSeek-V4.1 feature) and
[c98b9765d](https://github.com/NVIDIA/TensorRT-LLM/commit/c98b9765d85f277d58589d740e75bbc33a022bf0)
(NVIDIA/TensorRT-LLM#19988, which folds in NVIDIA/TensorRT-LLM#19840:
"skip zero-row launches in fp4_quantize, mxfp8_quantize, noaux_tc_op"
with tests that failed on their main) to the DeepSeek-V3 fused routing
launcher (`invokeNoAuxTc`, `csrc/fused_moe/noAuxTcKernels.cu`).

- **Bug.** `fused_topk_deepseek` with zero tokens set `gridDim = 0`.
`cudaLaunchKernelEx` rejects that with `cudaErrorInvalidValue`; the
return value was not checked, so the call returned normally and the
error surfaced on the next unrelated CUDA call (`AcceleratorError: CUDA
error: invalid argument` from, say, `torch.ones(4).sum()`), on every
path and with or without `routing_replay_out`.
- **Fix.** Return before the launch when `num_tokens == 0`; otherwise
check the launch with `TLLM_CUDA_CHECK`, as upstream does (it throws
with the CUDA error string). No change for non-empty inputs.
- **Test.** `test_zero_tokens_launch_nothing`: grouped, 256-expert and
128-expert single-group configurations, with and without a replay
buffer; asserts the output shapes and that the following CUDA call is
clean. 6 of 6 cases failed before the fix.

## 🔍 Related Issues

NVIDIA/TensorRT-LLM#19727, NVIDIA/TensorRT-LLM#19988

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
- [x] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust):
`tests/model_optimizations/test_dsv3_fused_routing.py`

Run on B200 (SM100) in the CUDA 13.0 CI container at this branch's head:

```
pytest tests/model_optimizations/test_dsv3_fused_routing.py \
  -k "zero_tokens_launch_nothing or (backend_correctness and default) or routing_replay_out_extended"
84 passed, 30 skipped
```

`test_zero_tokens_launch_nothing` on the pre-fix kernel: 6 failed.

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

The Cake backend already rejects zero tokens in its contract; this is
the default backend only.

The new test sits with the other input-contract test
(`test_dsv3_fused_routing_rejects_strided_views`). #9344 adds its test
elsewhere in the same file; whichever merges second gets rebased.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Zero-token routing operations now complete without launching
unnecessary GPU work across grouped and single-group configurations.
Empty outputs retain their expected shapes, and subsequent GPU
operations can proceed normally.
* GPU kernel launch failures are now checked and reported before stream
error synchronization, while successful launches continue through the
existing error checks.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [05e7652](https://github.com/flashinfer-ai/flashinfer/commit/05e76524d0106ae88ffb18ecc44a49c5ed1a29be)

- **作者**: Yechan Kim
- **时间**: 2026-11-12T01:45:41Z
- **提交信息**: fix(trtllm-gen moe): publish routing outputs before the PDL trigger (#8610)

<!-- .github/pull_request_template.md -->

## 📌 Description

With PDL on (the default), `trtllm_fp8_block_scale_routed_moe` sometimes
returns wrong rows on SM100. In a back-to-back repro (#8607) we saw up
to 3% wrong calls at 2560 to 8192 tokens when the workspace is filled
with 0xFF before each call, and about 1 in 10,000 calls without the
fill. With this PR we see 0 wrong calls in 584,000 calls. The cost is
+0.2% to +0.5% per MoE call from 32 to 4096 tokens, and +0.5 to +0.6 µs
(+1.2% to +2.5%) at 1 and 8 tokens. The 1- and 8-token cost comes only
from the second, optional commit. The `enable_pdl=False` workaround
costs +0.6% to +7.9%.

**Why it breaks.** The routing kernels call
`cudaTriggerProgrammaticLaunchCompletion()` after their global writes.
The comment in `routingPermutation` says why: "Triggering before the
permutation writes causes the consumer to read stale data → NaN". But
the trigger takes effect for the whole CTA as soon as the first thread
of the CTA runs it (PTX ISA, `griddepcontrol.launch_dependents`:
"Repeated invocations of this instruction by threads in the current CTA
will have no additional side effects past that of the first
invocation"). So a thread that finishes its part of the permutation loop
early lets the next kernel start while other threads of the same CTA
still write the routing outputs. The kernels after routing then read
some stale values. The trigger is also not a memory fence. The PTX ISA
says a GPU-scope release fence before `launch_dependents` in the
triggering thread is what makes the writes visible at the start of the
dependent grid.

**What changed.** Two commits. They can be reviewed and taken
separately.

1. `fix(moe): trigger PDL in trtllm-gen routing only after all CTA
writes`. This is the fix.
- New `triggerDependentLaunchAfterWrites()` in `RoutingKernel.cuh`:
`__syncthreads()`, then `__threadfence()`, then the trigger. The barrier
makes sure no thread triggers before every thread of the CTA has written
its part. The fence makes those writes visible at GPU scope before the
trigger.
- Used at the three routing trigger points that come after the routing
writes: `routingPermutation` (cluster kernels),
`routingIndicesOffsetsKernel` and `routingIndicesCoopKernel`.
- The small-batch `routingIndicesBlockKernel` and
`routingIndicesDynBlockKernel` (up to 16 tokens) trigger at their start
on purpose. They are not changed here (see Reviewer Notes).
   - New test `tests/moe/test_trtllm_gen_moe_pdl_ordering.py`.
2. `fix(moe): wait on the primary grid before finalize reads routing
outputs`. This is optional hardening. It does not fix the bug alone.
- `finalizeKernelVecLoad` and `finalizeKernelSmallBatch` read
`expandedIdxToPermutedIdx` and the expert weights before
`cudaGridDependencySynchronize()`. The comment says routing has finished
before the GEMMs could start. Under PDL that is not guaranteed: for
example, `activationDeepSeekKernel` triggers at its first instruction,
before it waits. The wait now comes first.
- Without commit 1, this commit does not remove the wrong rows (694 and
642 of 32000 calls are still wrong). It costs about +0.5 to +0.6 µs per
call at 1 and 8 tokens and about +0.2 µs from 32 tokens on. We are happy
to drop it if you prefer to keep the early reads; commit 1 alone fixes
the repro.

The public API and the `enable_pdl` default do not change.

**Tests.** One GB200, upstream main `c0d987da` as the base for the
"before" numbers (main `53350021`, the base of this branch, has the same
trtllm-gen MoE sources). DeepSeek-V3-style block-FP8 MoE: 256 experts,
top-8, hidden 7168, intermediate 128 per GPU, random weights.
Back-to-back calls on one stream, each compared bit for bit with the
same call with `enable_pdl=False`. "Poisoned" means the caller-owned
`workspace_buffer` is filled with 0xFF before every call, so a too-early
read returns garbage. This does not change any result when the ordering
is right.

| Run (PDL on) | main | this PR |
|---|---|---|
| repro, poisoned, seed 0 (16 calls x 2000 waves) | 1003 / 32000 wrong |
0 / 32000 |
| repro, poisoned, seed 7 | 831 / 32000 | 0 / 32000 |
| repro, plain scratch, seeds 0 and 7 (16 x 6000 each) | 8 / 96000 (seed
0) | 0 / 192000 |
| 1 to 2048 tokens, poisoned (this PR: 10 sizes x 4 layers x 2000 waves)
| 0 / 156000 (earlier runs: 8 sizes, 3000 waves) | 0 / 80000 |
| second script with more options, plain scratch, seed 0 (this PR: 16
calls x 12000 waves) | 31 / 288000 (earlier runs of 6000 and 12000
waves) | 0 / 192000 |
| second script, poisoned (16 calls x 3000 waves) | 817 / 48000 (earlier
run) | 0 / 48000 |
| CUDA graph replay, poisoned | 0 | 0 / 8000 |
| new test (4800 calls per run) | fails in 6 of 6 runs (60 to 104 wrong)
| passes in 3 of 3 runs |

Total with this PR: 0 wrong calls in 584,000 back-to-back calls with PDL
on. With PDL off, every run on both sides was bit-exact.

A second, independent rerun on fresh JIT builds (main `53350021` vs this
branch, seeds 0, 7 and 21): main had 2035 / 96000 wrong calls with the
0xFF fill and 4 / 192000 with plain calls; this PR had 0 / 96000 and 0 /
192000 (commit 1 alone: 0 / 64000). The new test failed 2 of 2 runs on
main (67 and 83 wrong) and passed 2 of 2 runs on this branch.

Commit 1 alone: 0 / 32000 for seeds 0 and 7. What else we tried, same
poisoned repro (wrong calls for seed 0 / seed 7): barrier only before
the trigger 0 / 0; per-thread fence only, no barrier, 289 / 444;
finalize change only 694 / 642; GEMM2 launched without PDL only 735 /
624.

We also ran on this branch: `tests/moe/test_trtllm_gen_routing.py`,
`tests/moe/test_trtllm_gen_routed_fused_moe.py -k fp8` and
`tests/moe/test_trtllm_gen_moe_workspace.py -k fp8_block_scale` (all
passed: 690 passed and 24 skipped; 267 passed; 17 passed). We did not
run the whole test suite.

**Performance.** Same shapes, 8 layers back to back captured in one CUDA
graph, µs per MoE call, mean of 4 runs (2 for commit 1 only), each the
median of 5 rounds. One GB200, nothing else on the node.

| Tokens | main, PDL on | commit 1 only | this PR | this PR vs main |
main, PDL off (workaround) |
|---|---|---|---|---|---|
| 1 | 25.28 | 25.27 | 25.91 | +0.64 µs (+2.5%) | 27.05 (+7.0%) |
| 8 | 38.35 | 38.34 | 38.81 | +0.46 µs (+1.2%) | 41.38 (+7.9%) |
| 32 | 102.43 | 102.44 | 102.61 | +0.17 µs (+0.2%) | 104.14 (+1.7%) |
| 128 | 144.65 | 145.19 | 145.37 | +0.72 µs (+0.5%) | 146.39 (+1.2%) |
| 512 | 268.24 | 269.28 | 269.51 | +1.27 µs (+0.5%) | 270.76 (+0.9%) |
| 1024 | 304.73 | 305.29 | 305.48 | +0.76 µs (+0.2%) | 307.13 (+0.8%) |
| 2048 | 345.95 | 346.59 | 346.78 | +0.83 µs (+0.2%) | 348.49 (+0.7%) |
| 4096 | 451.90 | 452.88 | 453.10 | +1.19 µs (+0.3%) | 454.65 (+0.6%) |

Commit 1 costs nothing up to 32 tokens and about 0.5 to 1 µs from 128
tokens on. Commit 2 costs about 0.5 to 0.6 µs at 1 and 8 tokens and
about 0.2 µs from 32 tokens on.

## 🔍 Related Issues

Fixes #8607

Related: #3835 (finalize and PDL), #6449 (block routing trigger), #7598
(RFC: which inputs a PDL launch may read before the wait), #8495 (open
PR that changes the same routing and finalize code).

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
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/moe/test_trtllm_gen_moe_pdl_ordering.py
tests/moe/test_trtllm_gen_routing.py
tests/moe/test_trtllm_gen_routed_fused_moe.py
tests/moe/test_trtllm_gen_fused_moe.py
tests/moe/test_trtllm_gen_moe_workspace.py`

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

- The new test depends on timing and on where buffers land in memory. On
main it failed in every run we tried (about 1.5% of calls). The extra `*
1.0` temporary in `_rand_fp8` is there on purpose: without it, the same
test hit the bug far less often (1 of 4800 calls, or 0). The test can
only fail when the ordering is wrong; it never fails on a correct build.
It takes about 5 s plus about 3 GB of weights.
- Small batches are not changed. `routingIndicesBlockKernel` and
`routingIndicesDynBlockKernel` trigger at their start, and their comment
says "the batched GEMMs guard every routing-dependent load with a grid
dependency". That is not true for all cubins: the DeepSeek-FP8 GEMM2
cubins (`bmm_Bfloat16_E4m3E4m3_..._dsFp8_..._dynB`) are built with
`mGridWaitForPrimaryRouting = false`, and their SASS loads
`numNonExitingCtas`, `ctaIdxXyToBatchIdx` and `ctaIdxXyToMnLimit` before
the first `ACQBULK`. We did not see wrong results at 1 to 2048 tokens (0
of 80000 poisoned calls with this PR, and none on main before), and
launching GEMM2 without PDL did not remove the wrong rows at 2560 to
8192 tokens, so we left these kernels alone. It may still be worth a
look.
- #8495 adds `finalizeKernelWarpPerToken`, which also reads the permuted
indices and weights before the PDL wait, and it changes the same routing
files. Whichever lands second will need a small rebase.
- We did not find which load reads the routing outputs too early. By the
PTX ISA, a load after `griddepcontrol.wait` sees all writes of the
finished primary grid, so it must be a load that comes before a wait
(the comment in `routingPermutation` says the consumer does this). We
only know that, in our runs, the barrier before the trigger removes the
wrong rows and a per-thread fence alone does not.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved the reliability of routed mixture-of-experts results on
supported GPUs, particularly across repeated, back-to-back calls.
* Fixed cases where routing information could be read before it was
ready, helping ensure outputs are correct and consistent.
* Added coverage for repeated calls across several input sizes to verify
that results remain stable.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Yechan Kim <161688079+yechank-nvidia@users.noreply.github.com>

### [9623673](https://github.com/flashinfer-ai/flashinfer/commit/96236732c8d7cfb06ab0b470097eea5c8ebf0abf)

- **作者**: feih-nv
- **时间**: 2026-11-12T01:44:08Z
- **提交信息**: fix(moe): initialise the DSv3 routing kernel's unused intermediate top-k slots (#9344)

<!-- .github/pull_request_template.md -->

## 📌 Description

Port of the bugfix part of TensorRT-LLM
[dff77efa2](https://github.com/NVIDIA/TensorRT-LLM/commit/dff77efa2ac827503386066a5a013fba3ce23819)
(NVIDIA/TensorRT-LLM#9792) to the DeepSeek-V3 fused routing kernel
(`fused_topk_deepseek`, `csrc/fused_moe/noAuxTcKernels.cu`). The
commit's Nemotron 512-expert / top-22 feature is not ported. Upstream's
PR is a feature PR and does not call this out as a bug; the sentinel
fill is part of its diff, and the bug it closes is established here by
the regression test below rather than by an upstream report.

- **Bug.** With one group and more than 128 experts the kernel runs
several expert warps. Each writes `topk` of its `MaxNumTopExperts` (8)
intermediate shared-memory slots; warp 0 then reduces all slots of every
warp. The unwritten slots hold whatever the previous kernel left in
shared memory. `tests/model_optimizations/test_dsv3_fused_routing.py`
already noted this ("their output depends on stale shared memory and is
not a usable reference") and dropped the 256/384-expert single-group
configurations from the backend comparison instead of fixing the kernel.
- **Effect.** The stale slots hold whatever the previous kernel left
(expert 0 and garbage ids such as 4, 122, 127 were observed). Whenever
the token's true best `sigmoid(score) + bias` is negative (negative
correction biases are ordinary), a stale slot wins and the kernel
returns its expert with weight 1.0. The new test reproduces it
deterministically: before the fix 2048 of 2048 tokens take a stale slot
for both 256 and 384 experts, fp32 and bf16.
- **Fix.** Lanes `topk .. MaxNumTopExperts - 1` of each expert warp
write `-inf` / `MaxNumExperts - 1` into their slots, as upstream does.
`NumInterTopKPerThread` counted `NumExpertWarps` twice and
over-allocated the per-lane registers; corrected as upstream did (no
behavioral change, the extra entries were filled with the sentinel).
- **Tests.** `test_single_group_topk_ignores_stale_intermediate_slots`
(256 or 384 experts, one group, negative bias, the answer never expert
0; the stale content itself is not under the test's control).
`single256` / `single384` return to `_ROUTING_CONFIGS`, so the
Cake-vs-default comparison covers the single-group path above 128
experts again.

## 🔍 Related Issues

NVIDIA/TensorRT-LLM#9792

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
- [x] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust):
`tests/model_optimizations/test_dsv3_fused_routing.py`

Run on B200 (SM100) in the CUDA 13.0 CI container at this branch's head:

```
pytest tests/model_optimizations/test_dsv3_fused_routing.py \
  -k "stale_intermediate_slots or (backend_correctness and default) or ground_truth \
      or (cake_backend_matches_default and (single256 or single384) and not 65536) \
      or routing_replay_out_extended or (fused_routing_op and 256-1 and 1-1-1)"
269 passed, 96 skipped
```

The new test on the pre-fix kernel: 4 failed (2048 of 2048 tokens took
expert 0, for 256 and 384 experts, fp32 and bf16).

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

- Not in this PR: FlashInfer's wrapper and launcher both require
`topk_group * n_group >= topk`, which for a single group means `topk <=
1`, so a 384-expert / top-8 single-group model (Kimi K2) cannot use
`fused_topk_deepseek` at all. Upstream has no such limit for the
single-group path. Keeping it unchanged in this PR.

### [60794ce](https://github.com/flashinfer-ai/flashinfer/commit/60794ce3b2e077b8d78382cc5406ea577e0c29bc)

- **作者**: feih-nv
- **时间**: 2026-11-12T01:41:59Z
- **提交信息**: fix(moe): give the DSv3 routing kernel's PDL wait a memory clobber (#9341)

<!-- .github/pull_request_template.md -->

## 📌 Description

Port of TensorRT-LLM
[1c4dacb19](https://github.com/NVIDIA/TensorRT-LLM/commit/1c4dacb19a52b1b68079bea1960c8160d149cca3)
(NVIDIA/TensorRT-LLM#9799) to the DeepSeek-V3 fused routing kernel
(`fused_topk_deepseek`, `csrc/fused_moe/noAuxTcKernels.cu`).

- The kernel waited on the producer grid with a bare `asm
volatile("griddepcontrol.wait;")`. Without a `"memory"` clobber the
compiler is free to schedule the `scores` / `routingBias` global loads
above the wait, so under `launch_with_pdl=True` (the default) the kernel
can read its inputs before the previous kernel has finished writing
them.
- `cudaGridDependencySynchronize()` is the same instruction with the
clobber (`asm volatile("griddepcontrol.wait;" ::: "memory")`);
`cudaTriggerProgrammaticLaunchCompletion()` replaces the matching
`launch_dependents` asm for symmetry, as upstream did. No behavior
change when PDL is off.
- `csrc/dsv3_router_gemm.cu` (FlashInfer's copy of the other file
upstream touched) has no PDL asm, so nothing to port there. The same
bare `griddepcontrol.wait` pattern exists in other FlashInfer kernels
(`norm.cuh`, `sampling.cuh`, `pos_enc.cuh`, `trtllm/fmha/lse.cuh`,
`nv_internal/.../quantization.cuh`); those are outside this port and
left for a separate change.

## 🔍 Related Issues

NVIDIA/TensorRT-LLM#9799

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
reviewers may adjust):
`tests/model_optimizations/test_dsv3_fused_routing.py`

No new test: the hazard is a compiler scheduling freedom, not a
deterministic input. The existing `test_dsv3_fused_routing.py` runs the
kernel with `launch_with_pdl=True`; see Reviewer Notes for the SASS
check.

Run on B200 (SM100) in the CUDA 13.0 CI container at this branch's head:

```
pytest tests/model_optimizations/test_dsv3_fused_routing.py \
  -k "(backend_correctness and default) or routing_replay_out_extended or (fused_routing_op and 256-8 and 8-4 and float32-float32) or ground_truth"
79 passed, 30 skipped (invalid group combinations)
```

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

Calibration of the claim: I compared the SASS of all 27
`deepseek_v3_topk_kernel` instantiations before and after (`cuobjdump
-sass` of the JIT module built by nvcc 13.0 for `sm_100a`). In both,
`ACQBULK` (the `griddepcontrol.wait`) sits at offset `0x30` and the
first `LDG` at `0x140` / `0x1a0`, with no global load ahead of the wait.
So on this toolchain the reordering upstream guarded against does not
actually occur; the change removes the compiler's permission to do it
(the missing clobber) rather than a reordering observed here, and is
otherwise a no-op in the generated code.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Refactor**
* Updated internal GPU execution coordination on supported CUDA
architectures. No user-facing behavior changes or public interface
changes are noted.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [0f2d52c](https://github.com/flashinfer-ai/flashinfer/commit/0f2d52c2652054e3d3fae5d0e1cb20b6d916e309)

- **作者**: eigen
- **时间**: 2026-11-12T01:30:14Z
- **提交信息**: fix(cake_muse_spark_norm): gated residual RMSNorm PDL programs read branch after the grid dependency wait (#9359)

The Cake package `flashinfer/cake_muse_spark_norm_backend` has nine
variants across three kernels: gated residual RMSNorm (mode 0 and mode
1, each with a plain and a PDL route), gated residual next-RMSNorm
(alpha tensor + post weight, alpha scalar + post weight, alpha scalar
without post weight), and RMSNorm + sigmoid gate (plain and PDL routes).
This PR changes the mode 0 and mode 1 PDL routes of gated residual
RMSNorm at M <= 128 on all three architectures. Fixes #9343. The
baseline is the previous Cake package on FlashInfer main. This is a
correctness fix, so the changed rows are slower or unchanged. Speedup on
the changed rows (M <= 128) is 0.8949 to 1.0002 on GB300, 0.8576 to
1.0002 on B200, and 0.8537 to 0.9864 on R200.

No other Cake variant in the package changes, and the package ships on
sm_100a, sm_103a and sm_107a.

**Table 1.** Gated residual RMSNorm, mode 0 PDL route, NVIDIA GB300
(sm_103a, 152 SMs), CUDA 13.4, driver 580.159.03. CUDA graph + PDL, 32
launches per graph, 20 replays, per-launch average, median over 4
interleaved sessions. Speedup = previous / this PR (below 1 = this PR
slower).

| M (rows) | previous us | this PR us | speedup |
|---|---|---|---|
| 1 | 1.090 | 1.218 | 0.8949 |
| 2 | 1.090 | 1.218 | 0.8949 |
| 4 | 1.157 | 1.218 | 0.9501 |
| 8 | 1.218 | 1.282 | 0.9501 |
| 16 | 1.282 | 1.286 | 0.9973 |
| 32 | 1.411 | 1.475 | 0.9566 |
| 64 | 1.795 | 1.880 | 0.9546 |
| 128 | 2.115 | 2.307 | 0.9168 |
| 256 | 3.205 | 3.205 | 1.0000 (same kernel) |
| 1024 | 11.472 | 11.474 | 0.9999 (same kernel) |
| 2048 | gap (CuTe DSL kernel) | gap (CuTe DSL kernel) | gap (CuTe DSL
kernel) |
| 4096 | 48.995 | 48.987 | 1.0002 (same kernel) |
| 8192 | 95.299 | 95.294 | 1.0001 (same kernel) |
| 16384 | 188.232 | 188.240 | 1.0000 (same kernel) |

**Table 2.** Gated residual RMSNorm, mode 1 PDL route, NVIDIA GB300
(sm_103a, 152 SMs), CUDA 13.4, driver 580.159.03. CUDA graph + PDL, 32
launches per graph, 20 replays, per-launch average, median over 4
interleaved sessions. Speedup = previous / this PR (below 1 = this PR
slower).

| M (rows) | previous us | this PR us | speedup |
|---|---|---|---|
| 1 | 1.470 | 1.474 | 0.9967 |
| 2 | 1.475 | 1.474 | 1.0001 |
| 4 | 1.474 | 1.474 | 0.9999 |
| 8 | 1.475 | 1.481 | 0.9961 |
| 16 | 1.603 | 1.602 | 1.0002 |
| 32 | 1.603 | 1.667 | 0.9612 |
| 64 | 2.051 | 2.115 | 0.9697 |
| 128 | 2.222 | 2.371 | 0.9372 |
| 256 | 3.203 | 3.204 | 0.9999 (same kernel) |
| 1024 | 11.724 | 11.727 | 0.9997 (same kernel) |
| 2048 | 24.499 | 24.501 | 0.9999 (same kernel) |
| 4096 | 49.038 | 49.037 | 1.0000 (same kernel) |
| 8192 | 95.131 | 95.133 | 1.0000 (same kernel) |
| 16384 | 187.816 | 187.818 | 1.0000 (same kernel) |

**Table 3.** Gated residual RMSNorm, mode 0 PDL route, NVIDIA B200
(sm_100a, 148 SMs), CUDA 13.4, driver 580.82.07. CUDA graph + PDL, 32
launches per graph, 20 replays, per-launch average, median over 4
interleaved sessions. Speedup = previous / this PR (below 1 = this PR
slower).

| M (rows) | previous us | this PR us | speedup |
|---|---|---|---|
| 1 | 1.156 | 1.348 | 0.8576 |
| 2 | 1.157 | 1.348 | 0.8585 |
| 4 | 1.223 | 1.348 | 0.9072 |
| 8 | 1.285 | 1.352 | 0.9502 |
| 16 | 1.348 | 1.412 | 0.9547 |
| 32 | 1.421 | 1.480 | 0.9600 |
| 64 | 1.863 | 1.987 | 0.9373 |
| 128 | 2.307 | 2.499 | 0.9232 |
| 256 | 3.271 | 3.269 | 1.0006 (same kernel) |
| 1024 | gap (CuTe DSL kernel) | gap (CuTe DSL kernel) | gap (CuTe DSL
kernel) |
| 2048 | gap (CuTe DSL kernel) | gap (CuTe DSL kernel) | gap (CuTe DSL
kernel) |
| 4096 | 51.685 | 51.654 | 1.0006 (same kernel) |
| 8192 | 99.908 | 100.290 | 0.9962 (same kernel) |
| 16384 | 201.869 | 201.744 | 1.0006 (same kernel) |

**Table 4.** Gated residual RMSNorm, mode 1 PDL route, NVIDIA B200
(sm_100a, 148 SMs), CUDA 13.4, driver 580.82.07. CUDA graph + PDL, 32
launches per graph, 20 replays, per-launch average, median over 4
interleaved sessions. Speedup = previous / this PR (below 1 = this PR
slower).

| M (rows) | previous us | this PR us | speedup |
|---|---|---|---|
| 1 | 1.570 | 1.604 | 0.9790 |
| 2 | 1.540 | 1.539 | 1.0002 |
| 4 | 1.539 | 1.541 | 0.9988 |
| 8 | 1.540 | 1.548 | 0.9948 |
| 16 | 1.604 | 1.604 | 1.0000 |
| 32 | 1.677 | 1.732 | 0.9685 |
| 64 | 2.243 | 2.246 | 0.9986 |
| 128 | 2.348 | 2.583 | 0.9090 |
| 256 | 3.343 | 3.342 | 1.0004 (same kernel) |
| 1024 | 14.010 | 14.007 | 1.0002 (same kernel) |
| 2048 | 27.055 | 27.061 | 0.9998 (same kernel) |
| 4096 | 52.384 | 52.418 | 0.9994 (same kernel) |
| 8192 | 103.877 | 104.166 | 0.9972 (same kernel) |
| 16384 | 207.264 | 207.248 | 1.0001 (same kernel) |

**Table 5.** Gated residual RMSNorm, mode 0 PDL route, NVIDIA R200
(VR200 board; sm_107a, 212 SMs), CUDA 13.5, driver 620.43. CUDA graph +
PDL, 32 launches per graph, 20 replays, per-launch average, median over
4 interleaved sessions. Speedup = previous / this PR (below 1 = this PR
slower).

| M (rows) | previous us | this PR us | speedup |
|---|---|---|---|
| 1 | 1.054 | 1.139 | 0.9261 |
| 2 | 1.003 | 1.175 | 0.8537 |
| 4 | 1.151 | 1.204 | 0.9564 |
| 8 | 1.176 | 1.237 | 0.9514 |
| 16 | 1.220 | 1.237 | 0.9864 |
| 32 | 1.339 | 1.387 | 0.9656 |
| 64 | 1.678 | 1.729 | 0.9702 |
| 128 | 1.986 | 2.274 | 0.8734 |
| 256 | gap (CuTe DSL kernel) | gap (CuTe DSL kernel) | gap (CuTe DSL
kernel) |
| 1024 | 8.727 | 8.729 | 0.9998 (same kernel) |
| 2048 | 17.968 | 17.966 | 1.0001 (same kernel) |
| 4096 | 34.289 | 34.286 | 1.0001 (same kernel) |
| 8192 | 64.756 | 64.739 | 1.0003 (same kernel) |
| 16384 | 127.878 | 127.838 | 1.0003 (same kernel) |

**Table 6.** Gated residual RMSNorm, mode 1 PDL route, NVIDIA R200
(VR200 board; sm_107a, 212 SMs), CUDA 13.5, driver 620.43. CUDA graph +
PDL, 32 launches per graph, 20 replays, per-launch average, median over
4 interleaved sessions. Speedup = previous / this PR (below 1 = this PR
slower).

| M (rows) | previous us | this PR us | speedup |
|---|---|---|---|
| 1 | 1.245 | 1.318 | 0.9445 |
| 2 | 1.358 | 1.412 | 0.9617 |
| 4 | 1.408 | 1.450 | 0.9710 |
| 8 | 1.458 | 1.510 | 0.9656 |
| 16 | 1.540 | 1.599 | 0.9633 |
| 32 | 1.613 | 1.702 | 0.9481 |
| 64 | 1.974 | 2.225 | 0.8869 |
| 128 | 2.069 | 2.390 | 0.8657 |
| 256 | 3.260 | 3.260 | 1.0002 (same kernel) |
| 1024 | 8.787 | 8.787 | 1.0000 (same kernel) |
| 2048 | 18.066 | 18.071 | 0.9997 (same kernel) |
| 4096 | 34.425 | 34.414 | 1.0003 (same kernel) |
| 8192 | 71.150 | 71.114 | 1.0005 (same kernel) |
| 16384 | 137.620 | 137.435 | 1.0013 (same kernel) |


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Refactor**
* Updated the internal execution order of normalization operations
across supported GPU architectures. No changes to the available features
or user-facing behavior are noted.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-11-13
**监控日期**: 2026-11-12
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4813
- **最后更新**: 2026-11-13T01:12:37Z

## 提交统计

- **昨日提交总数**: 5
- **提交者数量**: 5
- **主要提交者**: cuteNBD, Yixing Wang, CloudGPU

## AI分析总结

# FastVideo 昨日提交分析（5条，批次 1/1）

## 1. 主要更新类型
以**Bug修复为主（3/5）**，辅以**性能优化（1条）**和**文档修复（1条）**，无新功能引入，整体属于稳定性与健壮性打磨。

## 2. 关键变更点及与项目方向的关系
- **正确性修复**：保留被掩码路径下的 FlashAttention mask 与 scale，确保变长/掩码视频序列场景下注意力计算数值正确，直接关系视频生成质量。
- **显存优化**：负提示词文本编码完成后立即释放编码器，降低推理峰值显存占用，契合 FastVideo 面向高效推理的定位。
- **跨平台与服务健壮性**：修复 Apple Silicon（MPS）多进程 worker 的交接问题以及 Studio 命名镜像下载，增强 macOS 端与推理服务（Studio）的可用性。
- **国产硬件适配**：PyHcclCommunicator 改用 NPU 当前流（current streams），修复昇腾 NPU 上 HCCL 通信的同步问题，体现项目对多后端（CUDA/MPS/NPU）异构硬件的持续支持。
- **文档维护**：修复按版本区分的模型集合链接，保障用户在 Quick Start 与文档站能找到对应版本的模型资源。

## 3. 对项目的影响和潜在意义
- 修复注意力掩码与 NPU 通信两类底层缺陷，可减少特定配置下的生成错误与分布式训练/推理崩溃，提升在生产环境的可信度。
- 及时释放文本编码器使低显存设备（消费级 GPU、Mac）能以更大批次或更高分辨率运行，扩大用户覆盖面。
- 文档与 Studio 下载问题的修复降低新用户上手摩擦，配合 README 中的 Quick Start、Cookbook 与周会机制，巩固活跃社区的贡献闭环。

## 4. 值得关注的技术点
- **FlashAttention 掩码语义**：被屏蔽位置的 mask 与 scale 若被丢弃，会导致 softmax 归一化范围出错——这类修复需配合单元测试防回归。
- **文本编码器生命周期管理**：在保留/复用与及时释放之间权衡，需注意多轮生成（如批量不同提示词）时的重复加载开销。
- **MPS 多进程同步**：PyTorch MPS 后端的进程间 handoff 与 CUDA 语义差异，是跨平台推理常见坑点。
- **HCCL 流语义**：通信操作绑定正确计算流可避免异步流水线中的竞态，对昇腾集群上的大模型并行尤为重要。
- **AI 辅助协作痕迹**：提交中出现 Cursor Agent 等共同署名，反映项目已引入 AI 代理参与开发流程。

## 5. 结合 README 背景对项目发展的影响
README 显示 FastVideo 是一个配备完整文档站、Cookbook、Quick Start、周会与 Slack 社区的成熟视频生成框架。昨日这批提交未推进新模型或新功能，而是集中修复多硬件后端（NPU/MPS/FlashAttention）、推理内存效率与文档链接，表明项目当前处于**兼容性与生产就绪度打磨阶段**。这类"低曝光、高价值"的修复能显著降低用户在异构硬件与资源受限环境中的踩坑率，与项目强调的易用性和广泛部署目标一致，也为后续功能迭代奠定稳定基线。多贡献者与 AI 代理协作的模式也印证了社区驱动的可持续发展路径，整体上这些提交将巩固 FastVideo 作为高性能、跨平台视频生成基础设施的项目定位。

## 详细提交记录

### [ec9145a](https://github.com/hao-ai-lab/FastVideo/commit/ec9145ab3d86b2255b6fa3bbbb2845859c72cafd)

- **作者**: cuteNBD
- **时间**: 2026-11-12T19:03:33Z
- **提交信息**: [bugfix] Preserve masked FlashAttention mask and scale (#2080)

Co-authored-by: cuteNBD <206630735+bingdongni@users.noreply.github.com>

### [a4a5ceb](https://github.com/hao-ai-lab/FastVideo/commit/a4a5cebd00ac442a4af847b47dd83b6928286118)

- **作者**: Wenbo Ji　嵇文博
- **时间**: 2026-11-12T19:02:52Z
- **提交信息**: [perf] Free the negative-prompt text encoder right after encoding (#2058)

Co-authored-by: fv-superagent <352344047+fv-superagent@users.noreply.github.com>

### [ce24fca](https://github.com/hao-ai-lab/FastVideo/commit/ce24fca7f7285c8d223f6e0333b63bc57acd4477)

- **作者**: Yixing Wang
- **时间**: 2026-11-12T18:55:50Z
- **提交信息**: [bugfix] Fix MPS worker handoff and named Studio image downloads (#1847)

Co-authored-by: leo <269992774+leo2ultimate@users.noreply.github.com>
Co-authored-by: Aryan Kumar <156166681+aryan5v@users.noreply.github.com>

### [9795373](https://github.com/hao-ai-lab/FastVideo/commit/979537354c2b559f413882dcc6ba9bdb8ea2e1d3)

- **作者**: Xingjian Guo
- **时间**: 2026-11-12T18:44:35Z
- **提交信息**: [bugfix] Use NPU current streams in PyHcclCommunicator (#2053)

Co-authored-by: Xingjian Guo <222823329+Gxj230958@users.noreply.github.com>

### [794b873](https://github.com/hao-ai-lab/FastVideo/commit/794b8737fee65bd10ce36dd5b7ae617783a30e3d)

- **作者**: CloudGPU
- **时间**: 2026-11-12T09:44:57Z
- **提交信息**: [docs] Repair the version-specific model collection links (#2091)

Signed-off-by: mrhy7176 <129925370+mrhy7176@users.noreply.github.com>
Co-authored-by: Cursor Agent <cursoragent@cursor.com>
Co-authored-by: Aryan Kumar <156166681+aryan5v@users.noreply.github.com>

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-11-13
**监控日期**: 2026-11-12
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34915
- **最后更新**: 2026-11-13T00:47:20Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 2
- **主要提交者**: Steven Liu, Sayak Paul

## AI分析总结

## 分析总结：huggingface/diffusers 昨日提交

### 1. 主要更新类型

- **文档更新**（占比最高）：6 条中有 4 条（#14867、#15241、#15234、#15235）纯粹是文档层面的改进
- **测试增强**：1 条（#15140）为模型加载行为添加专项测试
- **版本发布后处理**：1 条（#15243）处理 0.42.0 版本发布后的收尾工作

### 2. 关键变更点及与项目方向的关系

- **深度文档优化（#14867）**：这是一次大规模文档重构，涉及概览、标题层级、编译（compile）、缓存（cache）、注意力（attention）等多个主题。发布前经过大量评审反馈迭代（多次"feedback"和"fix"），体现了团队对**用户体验和开发者可读性的高度重视**，这与 diffusers 作为开源库需要广泛社区采纳的方向一致。
- **文档架构整理（#15241、#15234、#15253）**：将流水线（pipelines）文档归类到合适章节、提取共享文件、将绝对链接改为相对链接——这些操作表明项目正在**系统性地治理文档结构**，降低新贡献者的上手门槛。
- **模型加载测试（#15140）**：针对 `_keys_to_ignore_on_load_unexpected` 属性添加测试。这是模型加载时忽略多余权重键的机制，添加测试**加固了模型兼容性回归防线**，防止上游模型结构变化导致加载失败。
- **版本后处理（#15243）**：0.42.0 发布后的清理工作，包括移除 ONNX 相关内容，暗示项目正在**调整推理后端策略**（可能将 ONNX 导出迁移至独立仓库或已被更好的替代方案取代）。

### 3. 对项目的影响和潜在意义

- 文档的系统性优化将**降低用户理解和使用门槛**，有助于扩大 diffusers 的开发者社区和采用率。
- 移除 ONNX 内容可能是有意的**功能瘦身策略**，让核心库更聚焦于 PyTorch 原生推理路径，避免维护过多导出后端。
- 测试补强提升了**模型加载链路的可靠性**，对于 diffusers 这样需要对接数百个 HuggingFace Hub 模型的库至关重要。

### 4. 值得关注的技术点

- **编译（compile）与缓存（cache）文档**的引入，表明 diffusers 生态正在拥抱 PyTorch 2.x 的 `torch.compile` 加速路径，这是一个重要的性能方向信号。
- **注意力机制（attention）文档的深度重写**，反映注意力相关模块（如 xFormers、sdp_attention 等）已成为用户最关心的核心话题之一。
- `_keys_to_ignore_on_load_unexpected` 测试带有描述性注释，体现了项目对**测试可维护性**的重视。

### 5. 基于README背景对项目发展的评估

diffusers 是 HuggingFace 团队的开源生成模型库，采用 Apache 2.0 许可证，目标是提供通用的扩散模型工具链。昨日的提交虽无重大功能新增，但集中体现了项目正处于 **0.42.0 发布后的稳定期**：优先巩固文档质量、补齐测试覆盖、清理发布遗留问题。这种"文档+测试"并行推进的节奏，说明团队在快速迭代功能之余**同步投入基础设施建设**，为后续更复杂的功能（如编译加速、新注意力机制支持）打下坚实的文档和质量基础。ONNX 内容的移除则提示需关注其推理后端战略是否正在收敛。整体而言，这一批提交对项目发展的直接功能影响有限，但对**社区体验、代码质量和长期可维护性**具有积极的累积效应。

## 详细提交记录

### [843f174](https://github.com/huggingface/diffusers/commit/843f1743e259e510f22065c0cb917d417b98d9f5)

- **作者**: Steven Liu
- **时间**: 2026-11-12T17:19:23Z
- **提交信息**: [docs] Optimize and scale pt. 1 (#14867)

* overview

* better titles

* compile

* cache

* attention

* feedback - titles

* feedback - attention

* feedback - soften absolutes

* feedback - cache integration, update table

* fix

* feedback - rename file

* fix

* fix

### [04f2159](https://github.com/huggingface/diffusers/commit/04f215933ec6610ebc7989f7285eaec06b669fa0)

- **作者**: Sayak Paul
- **时间**: 2026-11-12T17:17:03Z
- **提交信息**: [docs] move pipelines to appropriate sections. (#15241)

move pipelines to appropriate sections.

### [2e3fb9d](https://github.com/huggingface/diffusers/commit/2e3fb9db48418383bfabdb2c4c0d241ee50cfc79)

- **作者**: Steven Liu
- **时间**: 2026-11-12T17:03:50Z
- **提交信息**: [docs] Shared files (#15234)

* shared files

* feedback - note

### [2cf719d](https://github.com/huggingface/diffusers/commit/2cf719d21753c2b265fd5d6229d30d771219ace9)

- **作者**: Steven Liu
- **时间**: 2026-11-12T16:47:52Z
- **提交信息**: [docs] Use relative links (#15235)

* absolute to relative

* feedback - revert https links

### [396d7a4](https://github.com/huggingface/diffusers/commit/396d7a4696bff6b0bc2baa7d9e41965b8383f017)

- **作者**: Sayak Paul
- **时间**: 2026-11-12T08:24:57Z
- **提交信息**: tests: add a test for _keys_to_ignore_on_load_unexpected. (#15140)

* tests: add a test for _keys_to_ignore_on_load_unexpected.

* add descriptive comments.

### [f9316b0](https://github.com/huggingface/diffusers/commit/f9316b0d4d69555c5e3f625585262e79cd299d34)

- **作者**: Sayak Paul
- **时间**: 2026-11-12T04:39:29Z
- **提交信息**: post release 0.42.0. (#15243)

* post release 0.42.0.

* up

* up

* remove onnx

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-11-13
**监控日期**: 2026-11-12
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


**报告日期**: 2026-11-13
**监控日期**: 2026-11-12
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13363
- **最后更新**: 2026-11-12T13:17:08Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Hong Zhang

## AI分析总结

## 提交分析：[2863804] support comfy-h3image-prune (#1825)

### 1. 主要更新类型
**功能新增**：为项目添加了对 "comfy-h3image-prune" 的支持，属于模型/工作流集成类的功能扩展。

### 2. 关键变更点及与项目整体方向的关系
- 提交名称中的 **"comfy"** 指向 ComfyUI 生态，表明该提交将某种图像生成能力接入 ComfyUI 工作流体系。
- **"h3image"** 推测为一款图像生成模型或工作流代号，**"prune"** 意为剪枝/压缩版本，暗示提供的是轻量化、优化后的模型变体。
- 该项目作为扩散模型合成工作室，其核心方向是整合与提供多样化的扩散模型、加速与压缩方案。该提交正契合这一方向——通过引入经过剪枝的模型版本来降低使用门槛与计算成本，同时扩展对 ComfyUI 节点生态的支持，是"多模型支持 + 易用性增强"路线的具体体现。

### 3. 对项目的影响和潜在意义
- **扩展生态覆盖**：使 DiffSynth-Studio 用户可在 ComfyUI 中直接使用剪枝版 h3image 模型，提升跨工具链的兼容性。
- **降低部署成本**：剪枝模型通常显存占用更低、推理更快，有利于在消费级硬件上运行，扩大用户群体。
- **积累轻量化资产**：为项目建立"原版 + 剪枝版"并行支持的模式，未来可复用至其他模型。

### 4. 值得关注的技术点
- 剪枝策略：权重量化、结构化剪枝还是层裁剪，具体方式需查看代码变更。
- 剪枝后模型在图像质量与推理速度上的权衡（是否附带评测数据）。
- ComfyUI 集成方式：是注册自定义节点、导入工作流 JSON，还是提供模型加载适配器，这决定了集成深度与可维护性。
- PR 编号 (#1825) 显示该仓库社区贡献活跃，评审流程较为规范。

### 5. 基于README背景对项目发展的整体影响
README显示 DiffSynth-Studio 是 ModelScope 旗下、在 PyPI 发布的扩散模型合成工具包，旨在提供统一、便捷的扩散模型使用体验。此次提交延续了"广纳模型、优化性能、拥抱社区"的主线：一方面通过 ComfyUI 集成拥抱更广泛的用户社区，另一方面通过剪枝优化响应"高效推理"的行业趋势。这类持续的模型与生态集成提交，将稳步提升项目在扩散模型工具链中的影响力和实用价值，巩固其作为一站式扩散合成平台的定位。

## 详细提交记录

### [2863804](https://github.com/modelscope/DiffSynth-Studio/commit/28638042df62d206486a8bcff3ef22973c84e414)

- **作者**: Hong Zhang
- **时间**: 2026-11-12T12:16:58Z
- **提交信息**: support comfy-h3image-prune (#1825)

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-11-13
**监控日期**: 2026-11-12
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 38800
- **最后更新**: 2026-11-13T02:26:32Z

## 提交统计

- **昨日提交总数**: 89
- **提交者数量**: 54
- **主要提交者**: xiaofei-zheng, Mick, Liangsheng Yin

## AI分析总结

# SGLang 昨日提交总结（共 89 条提交）

## 一、主要更新类型

- **性能优化占比最高（约 30+ 条）**：集中在 diffusion 模型 kernel 融合（VAE QK norm、RMSNorm epilogue、head-128 均方归约）、投机解码单 kernel 化（Gumbel-max 采样、SiLU 与 NVFP4 量化融合）、DSA/稀疏注意力、MoE 与 AMD 后端。
- **功能新增（约 20 余条）**：dflash 投机解码、hicache/hisparse、磁盘专家分层、Mooncake linker 布局、NPU/寒武纪 XPU 支持、sgl-router 可配置项、JIT 调试。
- **Bug 修复（约 20 余条）**：涉及 scheduler、mamba 缓存、disaggregation、Anthropic/OpenAI 兼容层、AMD 权重加载、数值对齐与错误报告。
- **CI/文档/测试（约 15 条）**：NPU 精度套件与 CPU 覆盖、B200 专属 CI、fa3 abi3 发布流程、cookbook 配方。

## 二、关键变更与项目方向

- **Diffusion/多模态成为主战场**：SANA-Video、MiniMax-H3、Runway、Pika H3、Cosmos 3、Qwen3 文本编码器等扩散模型获得 Breakable CUDA Graph、条件缓存 O(1) 淘汰、ring attention 复用等深度优化，与 README“LLM 与多模态快速推理”定位高度一致。
- **投机解码与 PD 分离架构融合**：dflash 滑窗 MLA draft KV 环形缓存经 Mooncake 传输、dcp 断裂 prefill 前缀复用、top-k 分片与 smem/寄存器分级合并、Kimi-K3.1 DSA/MTP 支持，表明项目在推进“PD 分离 + 投机解码”的生产级组合。
- **量化与低精度路线扩张**：NVFP4、MXFP8（ModelOpt KDA）、block-FP8 MTP 草稿专家量化持续演进，向更低比特、更高吞吐推进。
- **多硬件生态拓展**：AMD（gfx950 fp8 KV、AITER MoE 修复、MI300X–MI355X cookbook、ROCm diffusion）、华为 NPU（AIV 传输、采样功能）、寒武纪 XPU、B200 CI，多后端战略持续投入。
- **工程化与网关收敛**：sgl-router 补齐 PD 能力以替代 sgl-model-gateway、请求体上限可配置、API key 覆盖与 WebSocket 路由、OpenAI 风格上下文长度报错、profiler 校验与 fa3 发布工作流，反映项目向企业级发行体靠拢。

## 三、对项目的影响

kernel 融合与量化提升小 batch 和投机解码场景的延迟，增强性能榜单竞争力；diffusion 缓存优化与显存分层（磁盘专家、prefix 重放）直接提升高并发文生图/视频吞吐，降低超大 MoE 部署门槛；hicache prefetch、mamba COW 清理、release_memory_occupation 时序修复增强长上下文稳定性。需注意一条 Mamba GDS 淘汰策略加入后随即被回滚（#49430 → #50118），相关用户应谨慎依赖。大量厂商工程师与 Claude 协作提交显示该仓库已是活跃上游，架构决策将影响下游生态。

## 四、值得关注的技术点

- GreedyDual-Size 缓存淘汰（已回滚）与 diffusion 条件缓存 O(1) 淘汰体现缓存管理在多模态推理中的重要性。
- Breakable CUDA Graph、PDL kernel（kimi-k3 1024 线程路由）是较新的 GPU 编程范式应用。
- FlashInfer 0.7.4 升级与 Prims-TS 稀疏 MLA 后端可能改变稀疏注意力性能基线。
- 词表分块 final-token 采样、Mooncake 直连 L3 布局、`layernorm_sp` 小 extend 复制路径等是带宽换算力与并行细粒度调优的典型。

## 五、总结

基于 README 定位，本批提交沿三条主线推进：一是把 diffusion 推理推向高性能生产就绪，二是以“PD 分离 + 投机解码 + 稀疏 MLA”组合巩固长上下文 LLM 竞争力，三是借 CI、发布流程与多硬件覆盖提升工程成熟度。SGLang 正从单一 LLM serving 平台演进为覆盖全硬件栈、全模态、全规模的综合性推理底座，其在速度、广度、容量三维度的同步投入将进一步巩固其在生产环境中的采用。

## 详细提交记录

### [7e31007](https://github.com/sgl-project/sglang/commit/7e31007a86d4cfe29c3e86ee93aaad51e7ff950e)

- **作者**: yz-wqf
- **时间**: 2026-11-12T23:44:36Z
- **提交信息**: [Perf] diffusion: Make conditioning cache eviction O(1) and raise its entry limit to 4096 (#49576)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [11a5f34](https://github.com/sgl-project/sglang/commit/11a5f34c7cbcc5dd536bbed85ca057ccf1dbd460)

- **作者**: forrestl
- **时间**: 2026-11-12T23:44:11Z
- **提交信息**: [Fix] minimax-h3: preserve per-layer AdaLN parameters with Cache-DiT (#49826)

### [bf8ca99](https://github.com/sgl-project/sglang/commit/bf8ca99bdc5473e6f33fa8835a3a5826bc313b1e)

- **作者**: Baizhou Zhang
- **时间**: 2026-11-12T22:24:16Z
- **提交信息**: [CI] fa3: Build the sgl-fa3 wheel with Python 3.10 for cp310-abi3 (#50193)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [c8ea707](https://github.com/sgl-project/sglang/commit/c8ea70797157cafab46b3807f850d1c5c061a8d1)

- **作者**: Long Jin
- **时间**: 2026-11-12T21:16:31Z
- **提交信息**: [Doc] tool-parser: Clarify streamed argument completion (#49927)

Co-authored-by: GoldArowana <27399349+GoldArowana@users.noreply.github.com>
Co-authored-by: Zijie Xia <zijie.xia@radixark.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [b6f7e75](https://github.com/sgl-project/sglang/commit/b6f7e752045e18ef15331cfa95ee1b63d647c9dd)

- **作者**: Zhiqiang Xie
- **时间**: 2026-11-12T21:10:43Z
- **提交信息**: [Fix] hicache: resolve prefetch trailing-window keys before the storage read (#50056)

### [bf8e5de](https://github.com/sgl-project/sglang/commit/bf8e5de1ed41eba8cc6a93f2bf42a3c2aaac8b22)

- **作者**: zijiexia
- **时间**: 2026-11-12T21:02:24Z
- **提交信息**: [Doc] cookbook: Add Inkling-2-Small deployment recipes (#50185)

Co-authored-by: Chunan Zeng <zcnrex@gmail.com>
Co-authored-by: Qinghan Chen <70640928+Bob-Chen222@users.noreply.github.com>
Co-authored-by: Yuhao Yang <47235274+yhyang201@users.noreply.github.com>
Co-authored-by: ispobock <ispobaoke@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [bd4c1af](https://github.com/sgl-project/sglang/commit/bd4c1afc37b3919869ec88a1987649fa5ad0f870)

- **作者**: Kangyan-Zhou
- **时间**: 2026-11-12T19:22:07Z
- **提交信息**: [Feat] sgl-router: Make the request-body cap configurable via SGLANG_ROUTER_MAX_BODY_BYTES (#50161)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [86c33ef](https://github.com/sgl-project/sglang/commit/86c33efa814038508e76d44abde65602ae121199)

- **作者**: Mick
- **时间**: 2026-11-12T19:17:47Z
- **提交信息**: [Perf] [ROCM] diffusion: Ring attention on aiter, and reuse the ring's K/V buffers (#49078)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [87702b4](https://github.com/sgl-project/sglang/commit/87702b4f67de90ad616652f17840ff124fcd9105)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-12T19:09:20Z
- **提交信息**: [Fix] sgl-router: Close the PD gaps that block replacing sgl-model-gateway in CI (#50052)

### [2f2f186](https://github.com/sgl-project/sglang/commit/2f2f186e6fb0dd21981c44663e3ecdc7a110460e)

- **作者**: Baizhou Zhang
- **时间**: 2026-11-12T18:22:17Z
- **提交信息**: [CI] fa3: Add the sgl-fa3 release workflow (#49972)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [b70ee8b](https://github.com/sgl-project/sglang/commit/b70ee8ba3fb4b2fb644a7c6c8f5b2565fb34c766)

- **作者**: Shuwen Wang
- **时间**: 2026-11-12T17:07:12Z
- **提交信息**: [Fix] entrypoints: Apply API keys in tokenizer workers and on WebSocket routes (#49894)

### [8385d83](https://github.com/sgl-project/sglang/commit/8385d83d4a43c76c52fa4c59f054d8c82fe8763e)

- **作者**: DarkSharpness
- **时间**: 2026-11-12T17:05:56Z
- **提交信息**: [Feat] JIT: Add SGLANG_JIT_ENABLE_LINEINFO for profiler source views (#50144)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [721ef92](https://github.com/sgl-project/sglang/commit/721ef92c4c764bb3c2307378bf13609fc7be7e72)

- **作者**: WenhaoZhang
- **时间**: 2026-11-12T15:17:56Z
- **提交信息**: [CI] diffusion: run MiniMax-H3-Image T2I and edit in the B200 suite (#49706)

### [d193c34](https://github.com/sgl-project/sglang/commit/d193c34ae4b138aae4b8c0479ff395b0138a0156)

- **作者**: WenhaoZhang
- **时间**: 2026-11-12T14:45:55Z
- **提交信息**: [Fix] diffusion: Keep ComfyUI patches in the plugin and refresh H3 compatibility (#45730)

### [fd42781](https://github.com/sgl-project/sglang/commit/fd42781a2af84f4205a9381740ff5b6ae89bdf77)

- **作者**: Artur
- **时间**: 2026-11-12T14:30:36Z
- **提交信息**: [Feat] diffusion: runway praxis 1 support (#49872)

Co-authored-by: Mick <mickjagger19@icloud.com>
Co-authored-by: Po-Han Huang <pohanh@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [7b790e1](https://github.com/sgl-project/sglang/commit/7b790e1c5f3f2601c3d9c549ad24eaf7ee0d5938)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-11-12T13:42:08Z
- **提交信息**: Revert "[Feat] mem_cache: Evict Mamba states by GreedyDual-Size (--radix-eviction-policy gds)" (#50118)

### [353ab94](https://github.com/sgl-project/sglang/commit/353ab94207c0273a067a4c5c0ba0664bb04c110d)

- **作者**: Shuwen Wang
- **时间**: 2026-11-12T13:35:34Z
- **提交信息**: [Doc] cookbook: Pin GLM-5.3-Flash high-throughput recipes to mamba ratio 0.9 (#50041)

### [3fdd191](https://github.com/sgl-project/sglang/commit/3fdd191fba615325e36eeb63beee92c659c3e387)

- **作者**: 渺如星辰
- **时间**: 2026-11-12T13:35:09Z
- **提交信息**: [Fix] benchmark: Accept --dtype int4_w4a16 in tuning_fused_moe_triton_sep.py (#49890)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [30593f9](https://github.com/sgl-project/sglang/commit/30593f940be2fa9d2b4468606007930374f71e36)

- **作者**: Asaf Gardin
- **时间**: 2026-11-12T13:34:46Z
- **提交信息**: [Fix] scheduler: Answer release_memory_occupation only after every pipeline stage released (#49798)

### [800f9b3](https://github.com/sgl-project/sglang/commit/800f9b30515cc331822cfaa1dfdeab57e63678ee)

- **作者**: Alexandr
- **时间**: 2026-11-12T13:24:46Z
- **提交信息**: [Refactor] RoPE: Support RotaryEmbedding class usage for DiT models (#44753)

Co-authored-by: ronnie_zheng <zl19940307@163.com>

### [61a0d0c](https://github.com/sgl-project/sglang/commit/61a0d0c580cb48afdd63ffdf4dd7928bbdc1cbfc)

- **作者**: shun8686
- **时间**: 2026-11-12T13:05:39Z
- **提交信息**: [CI] NPU: Scope CPU coverage to NPU unit tests (#50115)

### [fa17931](https://github.com/sgl-project/sglang/commit/fa179312e94c764f8637724ea2a364d302888906)

- **作者**: shun8686
- **时间**: 2026-11-12T12:30:02Z
- **提交信息**: [CI] NPU: Add base-a CPU coverage collection (#50108)

### [1ac7275](https://github.com/sgl-project/sglang/commit/1ac727550b7f0cd9b38f83b7f4140093c32cca80)

- **作者**: xiaofei-zheng
- **时间**: 2026-11-12T12:06:58Z
- **提交信息**: [Perf] [AMD] dsa: Default the DSA KV cache to fp8_e4m3 on gfx950 (#48996)

### [f2d0031](https://github.com/sgl-project/sglang/commit/f2d00315c432a4a4c1bf657941968835602ce84d)

- **作者**: sherdavincl9
- **时间**: 2026-11-12T11:50:30Z
- **提交信息**: [Feat] [NPU] hicache: Support AIV transfers for MLA and DeepSeek V4 (#48031)

### [1cf14eb](https://github.com/sgl-project/sglang/commit/1cf14eb1c1cb1fa66c1ee7253c54564b5cd35855)

- **作者**: vOv
- **时间**: 2026-11-12T11:49:46Z
- **提交信息**: [Feat] diffusion/sana-video2: Support breakable CUDA graphs (#41501)

Signed-off-by: cr-gao <gaochenrui@sjtu.edu.cn>
Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [96eb498](https://github.com/sgl-project/sglang/commit/96eb498eaa309be4e59fad028ed02d2384da6b9c)

- **作者**: Chen Cheng
- **时间**: 2026-11-12T11:49:15Z
- **提交信息**: [Feat] mem_cache: Evict Mamba states by GreedyDual-Size (--radix-eviction-policy gds) (#49430)

### [caae131](https://github.com/sgl-project/sglang/commit/caae1311f9a0d994a99d764928809323d9cc9526)

- **作者**: Asaf Gardin
- **时间**: 2026-11-12T11:48:45Z
- **提交信息**: [Feat] pp: Relay routed experts through pipeline-parallel stages (#48412)

### [47cb652](https://github.com/sgl-project/sglang/commit/47cb6521fafe0f647bd4d992b58164604fcbc4b1)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-11-12T11:30:07Z
- **提交信息**: [Perf] [NVIDIA] diffusion/nomas: Fuse VAE QK normalization and MRoPE epilogue (#49354)

Co-authored-by: Claude <noreply@anthropic.com>

### [1fa728d](https://github.com/sgl-project/sglang/commit/1fa728d7550cafdc081f20f4c1e66b3cddd14f4b)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-11-12T11:29:44Z
- **提交信息**: [Perf] diffusion/ming: Fuse lossless RMSNorm scale and residual epilogues (#49456)

### [cd47c12](https://github.com/sgl-project/sglang/commit/cd47c1228f4e0aa2fb7971a1ecfe597f20e5e932)

- **作者**: Han-Yin Chang
- **时间**: 2026-11-12T11:29:19Z
- **提交信息**: [Perf] diffusion: Replay the Qwen3 text encoder from breakable CUDA graphs (#49808)

Signed-off-by: Han-Yin Chang <nick20350@gmail.com>

### [1947690](https://github.com/sgl-project/sglang/commit/194769085b14c7ac147dbb1fd10a589f264cd490)

- **作者**: Han-Yin Chang
- **时间**: 2026-11-12T11:28:58Z
- **提交信息**: [Fix] diffusion/zimage: Align request sizes to the 16-pixel patch grid (#49714)

Signed-off-by: Han-Yin Chang <nick20350@gmail.com>

### [3df70c3](https://github.com/sgl-project/sglang/commit/3df70c309ba3007735a5f91945a03f0bcb5e1833)

- **作者**: Po-Han Huang (NVIDIA)
- **时间**: 2026-11-12T11:25:19Z
- **提交信息**: [Doc] cookbook: Refresh SemiAnalysis AgentX launches to InferenceX main f4c7f821 (#50081)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [c9d2ecb](https://github.com/sgl-project/sglang/commit/c9d2ecbfef0c4e375bee639830a58572d32c8f07)

- **作者**: pllimax
- **时间**: 2026-11-12T11:12:35Z
- **提交信息**: [Test] [NPU] qwen3.6-27b: enable expandable_segments for 1080p perf case (#49544)

### [fcb92bf](https://github.com/sgl-project/sglang/commit/fcb92bfda34785d7801a618cd27aa75684cf0993)

- **作者**: Shangming Cai
- **时间**: 2026-11-12T11:06:42Z
- **提交信息**: [Fix] disaggregation: Bound unsharded PD prefill prompts at bootstrap (#49669)

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [353cd07](https://github.com/sgl-project/sglang/commit/353cd07596b68f63ee188a786f4db17154b89a0f)

- **作者**: Yuhao Yang
- **时间**: 2026-11-12T10:20:54Z
- **提交信息**: [Fix] dflash: Gather candidate top-k over the target lm_head's own shard group (#47267)

Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: hnyls2002 <lsyincs@gmail.com>

### [406b727](https://github.com/sgl-project/sglang/commit/406b7275bb1c5ee338e2afee16cb1d578f306831)

- **作者**: Yuhao Yang
- **时间**: 2026-11-12T10:10:18Z
- **提交信息**: [Feat] dflash: Send the draft KV ring over PD disaggregation (Mooncake) (#49665)

Co-authored-by: kpham-sgl <khoa.pham@radixark.ai>
Co-authored-by: Yuwei An <ayw.sirius19@gmail.com>
Co-authored-by: Shuwen Wang <47200617+alphabetc1@users.noreply.github.com>
Co-authored-by: Baizhou Zhang <sobereddiezhang@gmail.com>
Co-authored-by: hnyls2002 <lsyincs@gmail.com>
Co-authored-by: Liangsheng Yin <hnyls2002@gmail.com>

### [36027fd](https://github.com/sgl-project/sglang/commit/36027fd1529eb2c11800c16f821549d401f8cf59)

- **作者**: Shuwen Wang
- **时间**: 2026-11-12T10:07:00Z
- **提交信息**: [Perf] model_overrides: Default GLM-5.3-Flash to an agentic Mamba pool split (#50018)

### [a8ff994](https://github.com/sgl-project/sglang/commit/a8ff99485354a12de61be8150b7ccd24b4de5eec)

- **作者**: Rohith Rachala
- **时间**: 2026-11-12T09:18:37Z
- **提交信息**: [Perf] layernorm_sp: Add --layernorm-sp-min-tokens to run small extend passes replicated (#48947)

Co-authored-by: Rohan Varma <rohanv@nvidia.com>
Co-authored-by: Shu Wang <shuw@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Po-Han Huang <pohanh@nvidia.com>

### [7bf5067](https://github.com/sgl-project/sglang/commit/7bf5067e9ee2d1e38df9cc1c7c258d9dd898ba29)

- **作者**: shun8686
- **时间**: 2026-11-12T09:15:50Z
- **提交信息**: [CI] NPU: upgrade lb-actions/precision-test from v1.0.9 to v1.0.11 (#50055)

### [cabb43a](https://github.com/sgl-project/sglang/commit/cabb43afd5ecc9de2c95458397eea68f34fa61a9)

- **作者**: Khoa Pham
- **时间**: 2026-11-12T08:58:35Z
- **提交信息**: [Fix] mamba: Clear a stale COW source when an unadmitted request is matched again (#50009)

Co-authored-by: Yuhao Yang <47235274+yhyang201@users.noreply.github.com>
Co-authored-by: Shuwen Wang <47200617+alphabetc1@users.noreply.github.com>

### [56005a5](https://github.com/sgl-project/sglang/commit/56005a53a50038c9e2aee9ae81530478f0c8945d)

- **作者**: Shuwen Wang
- **时间**: 2026-11-12T08:57:55Z
- **提交信息**: [Feat] hisparse: Support Kimi-K3.1 DSA layers on PD decode with DFLASH (#50005)

### [c7f3e2b](https://github.com/sgl-project/sglang/commit/c7f3e2bdfd348d396f17f776f067f5765fa2bc52)

- **作者**: Po-Han Huang (NVIDIA)
- **时间**: 2026-11-12T08:18:00Z
- **提交信息**: [Perf] dsa: Add an opt-in FlashInfer Prims-TS sparse MLA backend (#48602)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [12b727d](https://github.com/sgl-project/sglang/commit/12b727d3efd731e1ee91128644fffcb87557476e)

- **作者**: Yihao Wang
- **时间**: 2026-11-12T08:03:07Z
- **提交信息**: [Doc] diffusion: Fix feature guides that disagree with the code (#49675)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [0bf026b](https://github.com/sgl-project/sglang/commit/0bf026b1b586ea53d02c1d37e7d04c14c5c03271)

- **作者**: Ta
- **时间**: 2026-11-12T07:54:53Z
- **提交信息**: [Doc] README: update the readme logo (#49983)

Co-authored-by: Mingyi Lu <wisclmy0611@gmail.com>

### [bad3dd5](https://github.com/sgl-project/sglang/commit/bad3dd51002438423c16915e61c652ef3fbf18ec)

- **作者**: Chunan Zeng
- **时间**: 2026-11-12T07:36:43Z
- **提交信息**: [Perf] kimi-k3: Build the fused routing metadata in a separate 1024-thread PDL kernel (#49923)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [725b98b](https://github.com/sgl-project/sglang/commit/725b98b114f3af937636e4e709f1898b9fcb0ad0)

- **作者**: Shunkangz
- **时间**: 2026-11-12T07:03:15Z
- **提交信息**: [Feat] Comm: Add gated allgather in kv cache sharding (#45947)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [9f6d998](https://github.com/sgl-project/sglang/commit/9f6d9981b8a5538372c29c988794f08d761a695b)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-11-12T06:36:07Z
- **提交信息**: [Perf] diffusion: Enable verified eager LN fusion for SANA-Video (#47253)

### [3ba983d](https://github.com/sgl-project/sglang/commit/3ba983d7d8d764a053af46b9827e27fb8618304a)

- **作者**: Jan Schalkamp
- **时间**: 2026-11-12T06:34:33Z
- **提交信息**: [Chore] codeowners: paged-experts (#49867)

### [e548314](https://github.com/sgl-project/sglang/commit/e54831471af2b6ff96380f5bf4ce8e16a1297f61)

- **作者**: zijie
- **时间**: 2026-11-12T06:12:07Z
- **提交信息**: [Perf] [AMD] muse-spark: Prefill and decode optimization (#49704)

Co-authored-by: Zijie Chen <300606707+zijiecode@users.noreply.github.com>
Co-authored-by: HAI <hixiao@gmail.com>

### [f92ff40](https://github.com/sgl-project/sglang/commit/f92ff40b135d192bbc0f77daf58402027e636b80)

- **作者**: Mick
- **时间**: 2026-11-12T05:52:10Z
- **提交信息**: [Perf] diffusion/h3: Calibrate quality=high with a per-step cache schedule (#49762)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>

### [977e769](https://github.com/sgl-project/sglang/commit/977e769b486d31a6076f6f26cf94531ced977e0d)

- **作者**: zijie
- **时间**: 2026-11-12T05:39:33Z
- **提交信息**: [Fix] [AMD] scheduler: Keep Muse Spark's scheduler GPU work on the forward stream under monokernel (#47491)

Co-authored-by: Zijie Chen <300606707+zijiecode@users.noreply.github.com>

### [993199e](https://github.com/sgl-project/sglang/commit/993199e9fcb9e333ffb045b2c6ccdcc944e43e26)

- **作者**: Will Badr
- **时间**: 2026-11-12T04:56:42Z
- **提交信息**: [Fix] [AMD] moe: Keep is_shuffled on AITER-shuffled unquantized MoE weights (#48219)

### [853f27f](https://github.com/sgl-project/sglang/commit/853f27f998067d513c900f40a2818515987c9d24)

- **作者**: kangwangamd
- **时间**: 2026-11-12T04:52:56Z
- **提交信息**: [Fix] [AMD] ct-fp8-moe: Mark the pre-shuffled CT FP8 MoE weights is_shuffled (#47870)

Co-authored-by: YC Yen-Ching Tseng <yctseng@amd.com>

### [4464374](https://github.com/sgl-project/sglang/commit/44643740722a1a633f65f058a03c90ee106822b8)

- **作者**: Jeongho Shin
- **时间**: 2026-11-12T04:16:45Z
- **提交信息**: [Feat] hisparse: reject unvalidated speculative algorithms by name (#48846)

Co-authored-by: mlleo <mlleo@users.noreply.github.com>
Co-authored-by: Shuwen Wang <47200617+alphabetc1@users.noreply.github.com>
Co-authored-by: alphabetc1 <alphabetc1@users.noreply.github.com>

### [a158a1d](https://github.com/sgl-project/sglang/commit/a158a1d286010a0e8ef407666de535e8cf9bcc21)

- **作者**: Jeongho Shin
- **时间**: 2026-11-12T04:16:18Z
- **提交信息**: [Fix] hisparse: disambiguate __ffsll for HIP's dual overloads (#48840)

Co-authored-by: mlleo <mlleo@users.noreply.github.com>

### [809133c](https://github.com/sgl-project/sglang/commit/809133c31d9ebb247ccbd046af4a69e6be1ed9bb)

- **作者**: Shuwen Wang
- **时间**: 2026-11-12T04:15:49Z
- **提交信息**: [Fix] anthropic: Accept thinking enabled without budget_tokens (#47093)

Co-authored-by: Xinyuan Tong <xinyuantong.cs@gmail.com>
Co-authored-by: Xinyuan Tong <115166877+JustinTong0323@users.noreply.github.com>

### [a081aaa](https://github.com/sgl-project/sglang/commit/a081aaa257fddb22d8b9fcc506fe84d80c86b7fa)

- **作者**: Po-Han Huang (NVIDIA)
- **时间**: 2026-11-12T03:39:20Z
- **提交信息**: [Chore] deps: Bump FlashInfer to 0.7.4 (#49771)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Baizhou Zhang <sobereddiezhang@gmail.com>

### [6a72cc2](https://github.com/sgl-project/sglang/commit/6a72cc2918b5300d20a5a5ea9989e651509e3e25)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-11-12T03:36:06Z
- **提交信息**: [Perf] [NVIDIA] diffusion/joy: Reuse FP32 residual gate for large image updates on SM103 (#49391)

### [57a0019](https://github.com/sgl-project/sglang/commit/57a001996680ef9650a588b393976526d425201a)

- **作者**: Lee Nau
- **时间**: 2026-11-12T03:34:17Z
- **提交信息**: [CI] profiling: Check stage-profiler sync against the kernel's measured time (#49908)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [175ab80](https://github.com/sgl-project/sglang/commit/175ab80201868643048cf02f593323872460c91f)

- **作者**: Khoa Pham
- **时间**: 2026-11-12T03:24:49Z
- **提交信息**: [Perf] dsa: Native-head FlashMLA and a precomputed schedule for DCP decode (#49980)

Co-authored-by: Xiaoyu Zhang <35585791+BBuf@users.noreply.github.com>
Co-authored-by: Yuhao Yang <47235274+yhyang201@users.noreply.github.com>

### [4457a1c](https://github.com/sgl-project/sglang/commit/4457a1c47fc9c5c78b00fc666d219f59cd7d8376)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-11-12T03:20:53Z
- **提交信息**: [Perf] [NVIDIA] diffusion/nomas: Fuse exact head-128 mean-square reduction (#49308)

### [1edbe8f](https://github.com/sgl-project/sglang/commit/1edbe8f6f5b1a2a54b8959ffe6e04839ac37842d)

- **作者**: Po-Han Huang (NVIDIA)
- **时间**: 2026-11-12T03:12:23Z
- **提交信息**: [Test] mem_cache: Set sparse_prefill_small_heads on the page-sharded DSA test backend (#49987)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [cb79602](https://github.com/sgl-project/sglang/commit/cb79602a7ef1272f40bbb349e6c9ee0b72f06e77)

- **作者**: Yuhao Yang
- **时间**: 2026-11-12T03:09:14Z
- **提交信息**: [Perf] dflash: Keep a sliding-window MLA draft's KV in a per-request ring (#49664)

Co-authored-by: kpham-sgl <khoa.pham@radixark.ai>
Co-authored-by: Yuwei An <ayw.sirius19@gmail.com>
Co-authored-by: Shuwen Wang <47200617+alphabetc1@users.noreply.github.com>
Co-authored-by: Baizhou Zhang <sobereddiezhang@gmail.com>
Co-authored-by: hnyls2002 <lsyincs@gmail.com>

### [7966020](https://github.com/sgl-project/sglang/commit/7966020bc933075ec4a76c335617bb46bbf7d60d)

- **作者**: Aki Yang
- **时间**: 2026-11-12T03:01:17Z
- **提交信息**: [Fix] [NPU] dsv4: transfer A3 C4 state using peer-local rows (#47934)

Co-authored-by: AkiYangDev <331522356+AkiYangDev@users.noreply.github.com>

### [2d7874b](https://github.com/sgl-project/sglang/commit/2d7874b42f461c852e8126baf8b75dba5e1c05fa)

- **作者**: ishandhanani
- **时间**: 2026-11-12T02:58:27Z
- **提交信息**: [Feat] linker: Describe the direct linker's Mooncake objects in the L3 layout (#49434)

Signed-off-by: Ishan Dhanani <ishandhanani@gmail.com>

### [74cb973](https://github.com/sgl-project/sglang/commit/74cb973d78dfa4af85a90d2841891fec27e78db2)

- **作者**: Khoa Pham
- **时间**: 2026-11-12T02:46:52Z
- **提交信息**: [Perf] dcp: Replay prefix hits under breakable prefill graphs (#49943)

### [84ee24c](https://github.com/sgl-project/sglang/commit/84ee24c97dac5b93af09c403d320c76a2de356bc)

- **作者**: Khoa Pham
- **时间**: 2026-11-12T02:44:15Z
- **提交信息**: [Perf] dsa: bf16 MQA logits for the prefill indexer (#49102)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [88a44c1](https://github.com/sgl-project/sglang/commit/88a44c1adb333412db119647c3da72079f8db5ff)

- **作者**: Jan Schalkamp
- **时间**: 2026-11-12T02:27:32Z
- **提交信息**: [Feat] paged-experts: a disk tier for experts that do not fit host memory (#49195)

### [f98e961](https://github.com/sgl-project/sglang/commit/f98e9611bc07f9a32580a63f6d839ae66bbf1d0a)

- **作者**: Kevin Mi
- **时间**: 2026-11-12T02:22:42Z
- **提交信息**: [Fix] diffusion: Align Pika H3 Flex inference numerics (#47468)

### [884eece](https://github.com/sgl-project/sglang/commit/884eeced9fd703ca6f2b2792c307cf301524aa2c)

- **作者**: Rabinovich
- **时间**: 2026-11-12T02:22:03Z
- **提交信息**: [Fix] diffusion: Fix Cosmos 3 ignoring number of output per request for image and video requests (#49268)

### [0f512db](https://github.com/sgl-project/sglang/commit/0f512dbfc5a8f0474719abe8116e10b6d4cd440c)

- **作者**: andyluo7
- **时间**: 2026-11-12T02:21:41Z
- **提交信息**: [Feat] [AMD] diffusion: Run MiniMax-H3-Image on ROCm and add MI300X/MI325X/MI350X/MI355X cookbook recipes (#49707)

Signed-off-by: andyluo7 <andy.luo@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Mick <mickjagger19@icloud.com>

### [c487801](https://github.com/sgl-project/sglang/commit/c4878019d3af275d0087c828bb375208bb7ddf88)

- **作者**: ZY Y
- **时间**: 2026-11-12T02:12:56Z
- **提交信息**: [CI] [NPU] accuracy: Add 8-NPU suite for MiniMax-M2.5 W8A8 4p GPQA (#49793)

### [46dc697](https://github.com/sgl-project/sglang/commit/46dc69747c72d1e0fce9a208df7ccad151e29b89)

- **作者**: Xia Weiwen
- **时间**: 2026-11-12T02:06:45Z
- **提交信息**: [Feat] [XPU] GDN: support speculative decoding (#44017)

Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>

### [f211f41](https://github.com/sgl-project/sglang/commit/f211f4103de210fc0558fa704ba3df583d2717fd)

- **作者**: SeaAsters
- **时间**: 2026-11-12T01:52:37Z
- **提交信息**: [Feat] [NPU] sampling: Add sampling-mask support for Ascend (#43517)

### [91fd917](https://github.com/sgl-project/sglang/commit/91fd917a66c0005e45cc0c02bfcef72fa303d420)

- **作者**: akhilg-nv
- **时间**: 2026-11-12T01:47:14Z
- **提交信息**: [Perf] dflash: Fuse the simulated-acceptance overwrite into one kernel (#47765)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Po-Han Huang <pohanh@nvidia.com>

### [e15d36b](https://github.com/sgl-project/sglang/commit/e15d36b9b2cae312a378f08197ee7497f6e09d9b)

- **作者**: esarafian
- **时间**: 2026-11-12T01:45:34Z
- **提交信息**: [Fix] scheduler: use OpenAI's context-length wording when a prompt exceeds the KV pool (#48228)

Signed-off-by: Elad Sarafian <esarafian@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Po-Han Huang <pohanh@nvidia.com>

### [6299ec2](https://github.com/sgl-project/sglang/commit/6299ec2608e365a7e397ed7eae56165a18b37b56)

- **作者**: esarafian
- **时间**: 2026-11-12T01:42:56Z
- **提交信息**: [Perf] qsa: drop the per-layer RoPE cache length check in the indexer (#48271)

Signed-off-by: Elad Sarafian <esarafian@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Po-Han Huang <pohanh@nvidia.com>

### [3769d88](https://github.com/sgl-project/sglang/commit/3769d88f51380fda97159b8004d10a9a67ef566a)

- **作者**: esarafian
- **时间**: 2026-11-12T01:42:17Z
- **提交信息**: [Fix] mem_cache: report the CUDA error when host registration fails (#48272)

Signed-off-by: Elad Sarafian <esarafian@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Po-Han Huang <pohanh@nvidia.com>

### [46aa131](https://github.com/sgl-project/sglang/commit/46aa131b7b8b3a15f13a1fc202a2efdc145619a0)

- **作者**: esarafian
- **时间**: 2026-11-12T01:41:39Z
- **提交信息**: [Feat] modelopt: Quantize block-FP8 MTP draft experts to NVFP4 for MIXED_PRECISION checkpoints (#48295)

Signed-off-by: Elad Sarafian <esarafian@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Po-Han Huang <pohanh@nvidia.com>

### [d46d9ad](https://github.com/sgl-project/sglang/commit/d46d9adff79c1a0a75bf620489955913609b3b42)

- **作者**: esarafian
- **时间**: 2026-11-12T01:39:08Z
- **提交信息**: [Perf] speculative: Fuse the draft proposal's Gumbel-max sample into one pass (#48367)

Signed-off-by: Elad Sarafian <esarafian@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Po-Han Huang <pohanh@nvidia.com>

### [93dbe65](https://github.com/sgl-project/sglang/commit/93dbe651f0b96c9a957aeb286652ee907e05fcff)

- **作者**: Rohith Rachala
- **时间**: 2026-11-12T01:36:24Z
- **提交信息**: [Perf] reject_sampling: Vocabulary-tiled final-token pass at small batch (#48949)

Co-authored-by: Rohan Varma <rohanv@nvidia.com>
Co-authored-by: Shu Wang <shuw@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Po-Han Huang <pohanh@nvidia.com>

### [ed03760](https://github.com/sgl-project/sglang/commit/ed037608a6843bd4b269ca0652540dbbc78c26a0)

- **作者**: anmolgupt
- **时间**: 2026-11-12T01:35:22Z
- **提交信息**: [Perf] [NVIDIA] nvfp4: Fuse SiLU-and-mul with the next linear layer's NVFP4 activation quant (#48263)

Signed-off-by: Anmol Gupta <14880251+anmolgupt@users.noreply.github.com>
Co-authored-by: Po-Han Huang <pohanh@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [81f75cb](https://github.com/sgl-project/sglang/commit/81f75cb3fbdf3b4a073c8e94b1b28d1005941e71)

- **作者**: Schwinn Saereesitthipitak
- **时间**: 2026-11-12T01:34:09Z
- **提交信息**: [Fix] [NVIDIA] moe: Stop DeepGEMM's MLOPart helper once MegaMoE creates its buffer (#49601)

Co-authored-by: Po-Han Huang <pohanh@nvidia.com>

### [83b9012](https://github.com/sgl-project/sglang/commit/83b90121b3471296ab334aef9d9381d6a4d401e2)

- **作者**: Michael
- **时间**: 2026-11-12T01:31:55Z
- **提交信息**: [Fix] [AMD] kimi-k3: Skip the CuTe DSL TGV tactic registration on ROCm (#49929)

### [254d397](https://github.com/sgl-project/sglang/commit/254d3971eed477dab8baad30fd3460e505ea0f66)

- **作者**: Po-Han Huang (NVIDIA)
- **时间**: 2026-11-12T01:12:56Z
- **提交信息**: [Test] mem_cache: Use a 16-slot GDN spec ring in the row-state reset test (#49948)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [e46744d](https://github.com/sgl-project/sglang/commit/e46744dd4ca6605fad667d125af8779e594e02b0)

- **作者**: Chunan Zeng
- **时间**: 2026-11-12T00:58:45Z
- **提交信息**: [CI] deepgemm: pin apache-tvm-ffi for the release test jobs (#49967)

Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>

### [7352f1a](https://github.com/sgl-project/sglang/commit/7352f1aa85896a452c798640e0d4bdfb56cef893)

- **作者**: elvischenv
- **时间**: 2026-11-12T00:54:45Z
- **提交信息**: [Feat] kimi_k3: Support ModelOpt MXFP8 KDA for Kimi-K3.1-Pro (#49851)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [087e57c](https://github.com/sgl-project/sglang/commit/087e57c4e3da6490c50fbc7635dd52ad6de4f71a)

- **作者**: Yanbin Jiang
- **时间**: 2026-11-12T00:41:22Z
- **提交信息**: [Fix] [NVIDIA] unquant: restore eager low-M BF16 performance (#49931)

### [2c597c9](https://github.com/sgl-project/sglang/commit/2c597c922512521276194996bb4f7b46c369b091)

- **作者**: Chunan Zeng
- **时间**: 2026-11-12T00:14:10Z
- **提交信息**: [Perf] dsa: Stage the DCP top-k merge push in smem and fall back in registers for up to two ranks (#49922)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-11-13
**监控日期**: 2026-11-12
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for 100+ DiTs.
- **语言**: Python
- **星标数**: 1303
- **最后更新**: 2026-11-12T16:03:39Z

## 提交统计

- **昨日提交总数**: 20
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

## 1. 主要更新类型

以**性能优化**和**功能新增**为主，辅以少量重构与文档更新：新增 FlashInfer SVDQuant 运行时、MiniMax-H3-Image 模型支持、原生 FP8 后端；优化 Ulysses 通信与 FLUX 系列融合算子；重构算子开关配置。

## 2. 关键变更点及与项目方向的关系

- **量化线**：新增可选的 FlashInfer SVDQuant 运行时与原生 FP8 量化/GEMM 后端（含 warp-specialized GEMM、torch.compile 激活量化融合、QW8A8Linear 重命名），直接对应 README 中的 Quantization 能力。
- **并行线**：Ulysses FP8 通信优化——16 字节对齐填充、FP8 O permute 与量化融合、BF16 按最后一维计算填充、Ring 接收缓冲复用与 NUMA 诊断，强化 Parallelism 主题。
- **模型线**：MiniMax-H3-Image 支持（Pattern_3 适配器、CP/TP/VAE tile 规划器、`--prompt-enhancer`），以及 FLUX.2/3-Klein 的内存受限算子融合（LayerNorm+调制、门控残差、QK-Norm+RoPE 单趟化）。
- **配置重构**：用三态 `CACHE_DIT_FUSED_OPS` 统一各模型分散的融合开关，降低维护成本。

## 3. 对项目的影响和潜在意义

AdaLN 表按 `temb` 字节精确记忆化后，1024² bf16 从 6.67s 降至 3.71s 且位级一致，证明此前 CP 落后源于主机侧逐 step 拷贝而非上下文并行本身，使 CP2 追平 TP2 的 3.08s；FLUX.3 eager 提速 17%、FLUX.2 eager 提速 14%，而 compile 路径几乎无收益，明确了融合算子的适用边界。这些改动整体提升了引擎在多模型、多并行策略下的吞吐一致性与部署灵活性。

## 4. 值得关注的技术点

- AdaLN 缓存"网格外 timestep 永不复用其他表"的正确性设计，兼顾位级精确与缓存命中。
- 融合算子 eager 分支直接回退为上游表达式，前置条件失败时降级为相同数值而非报错。
- bf16 乘加先舍入再 FMA，保住约 23% 元素的一次舍入精度。
- 在 torch.compile 中分派算子导致图碎裂（39 个图、-1.9%），故融合路径仅用于 eager 与 `--cache`；编译期改写字面表达式。
- FP8 保持最小分块填充以避免额外字节传输，BF16 则追求零开销对齐的差异化策略。
- SVDQ 小 M 生产者采用 CuTe 融合与 K128 异步 split-K 的针对性调度。

## 5. 对项目发展的影响

这批提交沿 README 定义的 Cache、Parallelism、Quantization、CPU Offload 四大主线同步推进：新增 MiniMax-H3-Image 与 SVDQuant 后端拓宽了模型与量化覆盖面；通信与算子级优化兑现了性能承诺；统一开关重构则为后续算子族扩展奠定了可维护的基础设施。整体上，项目正从"功能可用"走向"跨模型、跨并行策略的位级精确高效推理"，并在文档中如实标注收益边界，体现了工程上的严谨性。这些改进共同巩固了 cache-dit 作为 DiT 原生 PyTorch 推理引擎的性能与生态竞争力。

## 详细提交记录

### [0733822](https://github.com/vipshop/cache-dit/commit/073382234c2a6d5627ef8f4d445aa41ba0bb7462)

- **作者**: DefTruth
- **时间**: 2026-11-12T15:03:31Z
- **提交信息**: feat(svdq): add an opt-in FlashInfer SVDQuant runtimet (#1308)

feat(svdq): add an opt-in FlashInfer SVDQuant runtime

### [99cade9](https://github.com/vipshop/cache-dit/commit/99cade9ee27411c696280a6ac4959e1d40c95da7)

- **作者**: DefTruth
- **时间**: 2026-11-12T12:55:19Z
- **提交信息**: Merge pull request #1306 from vipshop/dev

feat(model): support MiniMax-H3-Image with exact AdaLN plan memoization

### [34f86a3](https://github.com/vipshop/cache-dit/commit/34f86a396f8abf935b0cd310a17f8c6c9b7c2d88)

- **作者**: DefTruth
- **时间**: 2026-11-12T12:51:58Z
- **提交信息**: docs: split the MiniMax-H3-Image matrix row into T2I and Edit

### [d933e1d](https://github.com/vipshop/cache-dit/commit/d933e1da0d0caee5f90d97d19f247ff77c608296)

- **作者**: DefTruth
- **时间**: 2026-11-12T12:45:17Z
- **提交信息**: feat(model): support MiniMax-H3-Image with exact AdaLN plan memoization

MiniMax-H3-Image is MiniMax-H3's image partition as a Modular Pipeline: one packed
sequence of text / reference / generated rows through 50 blocks, guidance distilled into
the weights and PDD-distilled onto a fixed 6-step grid with one output head per step.

Model support:
- `MiniMaxH3Image` block adapter (Pattern_3 over `transformer_blocks`), registered before
  `MiniMaxH3` because the adapter registry matches the first class-name prefix;
- CP planner that gathers at `pdd_proj_out.*` (six per-step heads, `(B,S,96)` fp32 instead
  of `(B,S,5376)` bf16) and shards the packed sequence at the first block;
- TP planner reusing the video block plan (same attention, SwiGLU FFN and AdaLN table);
- tile-parallel VAE planner over the model's own `_split_tiles` grid, bit-exact;
- `minimax_h3_image` / `minimax_h3_image_edit` CLI examples and the docs matrix rows.

`--adaln-online` memoizes the AdaLN modulation tables: they are a pure function of a
handful of timestep embeddings, so they are built once (600 plans), keyed on the exact
`temb` bytes, and the 24.2 GiB of projections are parked on the host. A timestep outside
the announced grid is recomputed, never answered from another table. 1024^2 bf16 goes
from 6.67 s to 3.71 s and stays bit-exact; with it CP2 reaches the same 3.08 s as TP2,
which shows the earlier 1.10x was the per-step host copy, not context parallelism.

`--prompt-enhancer` optionally runs MiniMax-H3-Image-PE (the blocks repository) before
the DiT and takes its aspect-ratio advice; off by default because it changes the encoded
prompt and dominates the latency.

Also: cpu tests for the adapter order, the CP plan, the tiny TP/CP/TP2xCP2 parity
(four GPUs), the AdaLN plan cache and the prompt-expansion helpers.

### [d33bda7](https://github.com/vipshop/cache-dit/commit/d33bda761e9996f958dc4adbebdc2b04eb8a2e0d)

- **作者**: DefTruth
- **时间**: 2026-11-12T08:25:06Z
- **提交信息**: Merge pull request #1304 from vipshop/opt/pcie-comm

perf(distributed): optimize Ulysses FP8 communication and alignment

### [472cadf](https://github.com/vipshop/cache-dit/commit/472cadf9b5e4e7ac51606eff305ed4239509a49b)

- **作者**: DefTruth
- **时间**: 2026-11-12T08:07:00Z
- **提交信息**: docs(skill): record Ulysses and Ring communication status

### [ad7a290](https://github.com/vipshop/cache-dit/commit/ad7a290dfae1f76cec30765849c560a44f7d61db)

- **作者**: DefTruth
- **时间**: 2026-11-12T07:32:21Z
- **提交信息**: perf(distributed): use row-aligned BF16 padding

Compute BF16 alignment padding from the last dimension alone so the common aligned case adds no list traversal or chunk-based search. FP8 keeps chunk-minimal padding to avoid sending extra bytes.

### [79ddf57](https://github.com/vipshop/cache-dit/commit/79ddf57c32b9fbceaa27f8aac3a569e3579674f0)

- **作者**: DefTruth
- **时间**: 2026-11-12T07:23:41Z
- **提交信息**: perf(distributed): align Ulysses communication buffers

Add per-chunk 16-byte alignment padding for FP8 and BF16 Ulysses all-to-all paths, fuse the FP8 O permute with quantize/dequantize, and make K FP8 an explicit opt-in. Reorganize the communication kernels under csrc/kernels/ulysses with ulysses_fp8_* operator names, add read-only NUMA topology diagnostics, and reuse Ring K/V receive buffers.

### [45bfb8a](https://github.com/vipshop/cache-dit/commit/45bfb8a4869841d2bb33f968731ee8657d3a1820)

- **作者**: DefTruth
- **时间**: 2026-11-12T07:54:40Z
- **提交信息**: feat(fp8): add native FP8 quantize/GEMM backend and kernels (#1302)

feat(fp8): add native FP8 quantize/GEMM backend and kernels

### [f2ab340](https://github.com/vipshop/cache-dit/commit/f2ab3402d689512435362a85162909cc13aa106e)

- **作者**: DefTruth
- **时间**: 2026-11-12T07:38:22Z
- **提交信息**: docs(fp8): record quantize+gemm convergence target

### [693413c](https://github.com/vipshop/cache-dit/commit/693413c7e7622953ed160bce1202e032309a8b0e)

- **作者**: DefTruth
- **时间**: 2026-11-12T07:35:43Z
- **提交信息**: docs(fp8): record converged optimization priorities

### [98ab728](https://github.com/vipshop/cache-dit/commit/98ab7282d142d41b060cae12d0e24b73e74ad734)

- **作者**: DefTruth
- **时间**: 2026-11-12T07:20:51Z
- **提交信息**: refactor(fp8): rename runtime linear to QW8A8Linear

### [72d7495](https://github.com/vipshop/cache-dit/commit/72d74959b5246f187b7ee83ba69e120f46e73cda)

- **作者**: DefTruth
- **时间**: 2026-11-12T07:19:53Z
- **提交信息**: perf(fp8): fuse activation quantize through torch.compile

### [ceb786a](https://github.com/vipshop/cache-dit/commit/ceb786a5c1fc31cf3c32ef23c768ae1375738f1b)

- **作者**: DefTruth
- **时间**: 2026-11-12T06:07:00Z
- **提交信息**: fix(fp8): guard WS register-reconfig assert for clangd

### [b6a1512](https://github.com/vipshop/cache-dit/commit/b6a1512757c089942a7c4d41b0ab2f7bd61f2d0f)

- **作者**: DefTruth
- **时间**: 2026-11-12T05:58:54Z
- **提交信息**: feat(fp8): add warp-specialized GEMM and split row/tensor kernels

### [0dfb17e](https://github.com/vipshop/cache-dit/commit/0dfb17e6b7f445bfe76c2973db9b2e197457f348)

- **作者**: DefTruth
- **时间**: 2026-11-12T05:23:40Z
- **提交信息**: feat(quantization): add native FP8 backend and kernels

### [adefbff](https://github.com/vipshop/cache-dit/commit/adefbff83f05d1240111707da61466da28fcf847)

- **作者**: DefTruth
- **时间**: 2026-11-12T04:01:18Z
- **提交信息**: refactor(pipelines): control every fused-op family with CACHE_DIT_FUSED_OPS (#1301)

Replaces CACHE_DIT_{FLUX2_KLEIN,FLUX3_KLEIN,QWEN_IMAGE21,BOOGU}_FUSED_OPS and the per-model companions (_OPS allow-list, FLUX.2 _ROPE_CACHE / _JOIN) with one tri-state variable parsed in models/pipelines/env.py: unset keeps a family off until its install point (install_fused_modules() for the transformer subclasses, BooguImageTransformer2DModel.__init__ for the vendored model) turns it on, 1 forces it on, 0 forces it off. Per-operator selection is the ACTIVE_OPS constant.

The docs state plainly that the operators are at parity with torch.compile and only win against the eager arm, so the switch ships as an optional optimisation.

### [53beebd](https://github.com/vipshop/cache-dit/commit/53beebd34dd3f1c02d7445d058e271d1dc32956c)

- **作者**: DefTruth
- **时间**: 2026-11-12T02:25:01Z
- **提交信息**: perf(flux3-klein): fuse memory-bound block operators for FLUX.3-Klein (#1299)

* perf(models): add fused operators for the FLUX.3 Klein transformer

Second-pass optimisation of the diffusers FLUX.3 transformer, following the
_QwenImage21 shape: a thin subclass plus fused CUDA operators on the block and
attention seams, no vendored code and no pipeline subclass (FLUX.3 is a
ModularPipeline, so `flux3_fused` swaps the transformer class in its
post_init_hook, before enable_cache / compile / offload).

Operators (models family, shared _C_ops extension):
* flux3_klein_qk_norm_rope - per-head fp32 RMSNorm + interleaved RoPE in one
  pass. ncu: 28.0us at 83.5% of DRAM peak, against inductor's 75.2us at 71.8%
  (its only elementwise kernel in the compiled step with headroom).
* flux3_klein_gated_residual(+_split) - branch sum folded into the gated
  residual, removing one (B,S,D) write and read per block.
* flux3_klein_ln_modulate(+_cat) - LayerNorm + (1+scale)*x + shift, with the
  joint block writing the concatenated buffer directly.

Numerics: fp32 inside, bf16 stores. The branch sum of the gated residual keeps
its own rounding because upstream materialises `attn_output + ff_output`
(transformer_flux3.py:284) and stock+compile keeps it as a separate kernel.

Compiled graphs get the literal expression instead of the operators: dispatching
inside torch.compile fragmented the step into 39 graphs and cost 1.9%, so the
fused path is for the eager and `--cache` configurations, where it is worth
-17%. A lazy `import_module` in the hot path was a second graph break and is
gone - the torch.ops handles are resolved once, outside any traced region.

Measured on an RTX PRO 5000 (1024x1024, 16 steps, CUDA events, warmup then
median of a single transformer forward): eager 290.5 -> 241.1 ms (-17.0%),
compile 236.3 -> 236.6 ms with one graph on both sides. CLI end to end:
4.83 -> 4.03 s, `--cache` 3.78 -> 3.17 s, `--compile` 3.95 -> 3.94 s.

* fix(models): align the FLUX.3 fused fallback with the kernels and give the tests CI coverage

Code review follow-ups:

* The gated-residual fallback now implements the same chain as the kernel (branch sum
  rounded once, fp32 mul/add, one store): upstream materialises `attn_output + ff_output`
  (transformer_flux3.py:284) and stock+compile keeps it as its own kernel, so a fallback that
  used the three-rounding eager expression would let a failed precondition change the values.
  `_compiled_gated_residual(_split)` is the single definition and the test oracle.
* The Python preconditions are now a subset of the C++ checks: bf16 only (the kernels are
  written for it), `D % 1024 == 0` and `D <= 8192` for the LayerNorm rows, and explicit rank
  checks. Anything the C++ side would raise on is refused in Python, so a "supported" tensor
  falls back instead of throwing.
* Tests split by what can run in CI. `tests/api/test_flux3_klein_fused_pipeline.py` is
  CPU-only and never imports `_C_ops`: it runs the block forwards against the stock blocks
  bit-exactly on the fallback path, compares the forward signatures, pins that the fused pass
  only rebinds instance attributes (`_repeated_blocks` matches class names), resolves the
  adapter and both parallelism planners, and covers the switches and the dispatch counters.
  `tests/kernels/test_flux3_klein_model_ops.py` keeps the GPU-only operator parity.

94 tests pass, 8 of them CPU-only.

* docs(models): replace the stale FLUX.3 operator numbers with the measured ones

The docstring on `_ops_from_env` still quoted the pre-review measurements, where two of the
three operators silently fell back and the compiled arm appeared 1.15% faster. On the final
code the compiled arm is at parity by design (the operators are bypassed while tracing), and
the eager arm is 289.6 -> 241.3 ms. Quote those instead, plus the per-operator eager split and
a pointer to why the compiled graph gets the literal expression.

* refactor(models): hand compiled graphs the stock FLUX.3 code instead of a transcription

The compiled path returned cache-dit's own transcription of each seam, which drifts from the
stock graph for no speed in return. The block forwards and the attention processor now call the
stock class forward / the stock processor whenever `torch.compiler.is_compiling()`, and the
`_EAGER_BYPASS` table is gone. The eager fallbacks also call the stock helpers
(`apply_rotary_emb`) rather than re-deriving the rotation, so `CACHE_DIT_FLUX3_KLEIN_OPS=0` is
the configuration that has to reproduce stock bit for bit.

No measurable cost: the compiled arm stays at parity (236.4 vs 236.4 ms, unique_graphs=1 on
both sides) and the eager arm keeps 289.6 -> 241.3 ms.

* fix(models): keep the stock attention processor whenever the FLUX.3 kernel cannot run

The fused processor now defers to `Flux3AttnProcessor` not only while tracing but also when
`qk_norm_rope` is disabled, so a configuration without the kernel runs the stock code instead of
a transcription of it. Same rule as the block forwards: replacing stock only pays off when the
kernel is actually used.

* docs(models): state the compiled-arm comparison against its run-to-run floor

The compiled arm is not reproducible: two stock `--compile` runs differ by 34.79 dB, so a
fused-vs-stock figure of 33.48 dB is inside the noise and means "indistinguishable", not "bit
identical". Say that where the parity claim lives, so nobody reads the number as a controlled
comparison. The eager arm is bit-reproducible, which is where the amplification curve is
measured.

---------

Co-authored-by: DefTruth <DefTruth@users.noreply.github.com>

### [db2eba3](https://github.com/vipshop/cache-dit/commit/db2eba3a253501cbf5fdb7693f48d825fd195de6)

- **作者**: DefTruth
- **时间**: 2026-11-12T02:22:44Z
- **提交信息**: perf(flux2-klein): fuse memory-bound block operators for FLUX.2-Klein (#1298)

* perf(flux2-klein): fuse the memory-bound block operators

Add `_Flux2KleinPipeline` / `_Flux2KleinTransformer2DModel`, a second-pass
optimisation of the diffusers FLUX.2-Klein model, plus five CUDA operators in
the shared `_C_ops` extension:

- `ln_modulate`: LayerNorm(no affine) + `(1 + scale) * x + shift` in one pass,
  with the modulation folded into `[R, D]` rows instead of a `(B, S, D)`
  broadcast.
- `residual_ln_modulate`: the block's gated residual and the normalisation that
  follows it, in one pass, so the residual stream is read once instead of three
  times (the eager chain reads it for the add, then twice inside the norm).
- `qk_norm_rope` (+ `_join`): `torch.nn.RMSNorm` (fp32, one rounding after the
  affine) and GPT-J interleaved RoPE, one read and one write. The joined
  variant writes the text and image streams straight into one buffer, so the
  double block's three `torch.cat` calls stop materialising a second copy.
  Inductor's fused kernel for this chain measured a 12:1 load-to-store sector
  ratio (NCU: 21.45M vs 1.77M sectors); holding the row in registers removes
  that pass.
- `gated_residual` / `silu_mul`: implemented and measured, but inductor already
  fuses those chains at the DRAM ceiling, so they stay out of the default
  allow-list.

The eager branch of every operator is the upstream expression itself
(`F.rms_norm` + `apply_rotary_emb`, or the same sequence of bf16 tensor ops),
so a failed precondition degrades to identical values instead of an error.
The bf16 multiply-add pairs round the product first: `__hadd2(a, __hmul2(b, c))`
contracts into a bf16x2 FMA and drops a rounding on ~23% of the elements.

Measured on an RTX PRO 5000 (1024x1024, 4 steps, guidance 1.0, bf16, CUDA
events, text encoder and VAE excluded): eager 228.79 -> 196.44 ms/step
(-14.1%); `compile_repeated_blocks()` 190.15 -> 189.55 ms/step (-0.3%).
Accuracy fused+compile vs stock+compile: 46.75 dB / 0.9970 mean and 45.74 dB /
0.9968 min, against compile's own drift of 46.70 dB / 0.9971.

* fix(flux2-klein): invoke the norm module in the eager fallback

Under module-layerwise CPU offload a norm weight still lives on the CPU until
accelerate's pre-forward hook moves it, so reading norm.weight directly raised
"weight is on cpu" instead of falling back cleanly. The fallback now calls the
module when one is available, which also keeps the fallback identical to the
stock path by construction.

Measured after the fix, 1024x1024 / 4 steps: layerwise offload 43.32 dB and
TP2 46.05 dB against the single-GPU image.

* perf(flux2-klein): gate the joined q/k buffer behind a switch, correct the delta

`qk_norm_rope_join` writes the text and image streams into one buffer so the double
block's concatenation never runs. Against two calls plus `cat` it measures neutral:
-0.41 ms/step with one build order, +0.11 ms with the other, and in both cases the
pipeline built *second* in the process ran 0.3-0.5 ms faster, so that comparison was
measuring the process rather than the copy. It now sits behind
`CACHE_DIT_FLUX2_KLEIN_JOIN` and is off by default: one path to reason about, not two.

This also corrects the compile-arm number in 58b2ea7c. Re-measured with the build
order controlled and with one pipeline per process:

  four independent runs, alternating  stock 190.07 / 190.12   fused 190.08 / 189.94
  stock -> fused build order         -0.48% / -0.47% / -0.22%
  fused -> stock build order         +0.005% / -0.021%

The earlier -0.3% was inflated by whichever arm was built second. The real compile-arm
effect is 0.0 to -0.2%, i.e. flat, which is what the NCU data predicted: inductor
already runs these chains at 89-90.5% of DRAM (the SwiGLU + cat kernel moves exactly
the minimum traffic at 1.38 TB/s), so there is no bandwidth left for a hand-written
kernel to recover. The eager arm is unaffected and still wins 228.72 -> 198.99 ms/step
(-13.0%).

* fix(flux2-klein): fall back to the stock processors under async Ulysses

`async_ulysses/flux2.py` wraps `Flux2AttnProcessor.__call__` and
`Flux2ParallelSelfAttnProcessor.__call__` **on the class**, so a fused subclass quietly
overrode the async path: nothing failed, the all-to-all overlap simply disappeared.

Both orders are covered now:

- `install_attention_patch()` probes `AsyncUlyssesRegistry.get_original_method()` first and
  skips the install with a warning when the async wrapper is already on the stock classes;
- the FLUX.2 CP planner runs `AsyncUlyssesRegistry.apply()` and, if a fused processor is
  installed, restores the stock ones with a warning. That is the order the CLI actually
  takes: `from_pretrained` installs, `enable_parallel` applies async.

Verified end to end with `--parallel-type ulysses --ulysses-async` on two cards: the warning
appears, no traceback, 0.78 s for 4 steps, image written. New test
`test_install_is_skipped_under_async_ulysses` covers the detection and the skip.

* fix(flux2-klein): align the Python preconditions with the kernels, add API tests

Review follow-up. The Python gates were wider than the C++ `TORCH_CHECK`s, which turns a clean
fallback into an exception:

- `_fusable_tensor` / `_fusable_qk` now require bf16 exactly (they accepted fp16, and an fp16
  pipeline would have hit `TORCH_CHECK` instead of the eager branch); the old fp16 test passed a
  `[1, 32, 1, 3072]` tensor, so it failed on `head_dim != 128` and asserted nothing;
- `apply_qk_norm_rope` checks `cos.dim() == 2`;
- `apply_ln_modulate` / `apply_residual_ln_modulate` check `R in {1, B}` via `_rows_match`
  (`1 in (1, B)` also admitted `B = 1, R = 2`) and that `shift`/`gate` match `one_plus`.

The extension gate is resolved once at import (`EXTENSION_AVAILABLE`) instead of per block per
step: calling the loader inside `_enabled` produced two extra dynamo graphs on the block-level
compile (measured).

Contract fixes on the CUDA side: `out.is_contiguous()` for `gated_residual` / `silu_mul`,
`gate_up.stride(1) >= packed` against overlapping views, and the tautological `out_tokens`
argument of the single-stream `qk_norm_rope` is now a stated condition. Two docstrings claimed
bit-exactness that the measured 2.8e-6 rel-L2 contradicts; they now describe the rounding
schedule plus the one-ulp reduction-tree difference.

Tests: the module-level `skipif` is gone, so the switch parsing, the processor swap, the async
probe and the precondition fallbacks run on CPU (11 pass with no GPU, `cpu-tests.yml` can pick
them up). New `tests/api/test_flux2_klein_fused_pipeline.py` pins the adapter and CP/TP planner
registrations, the forward-pattern signature, the untouched block class names and a bit-exact
comparison of the fused double block against the stock diffusers block. `ln_modulate` gained a
shifted-activation case: at offsets up to 50 sigma the raw-square variance stays within 4.7e-6
rel-L2 of ATen's Welford.

Re-measured after the changes: interleaved A/B/A -0.03% (190.31 vs 190.25 ms/step), quality
unchanged (fused+compile 46.75 / 45.74 dB, 0.9970 / 0.9968), `unique_graphs` back to 2.

* chore: restore the cutlass submodule pointer

A 'git add -A csrc' in ddacf5a1 staged the gitlink for csrc/third_party/cutlass (the directory
is a copy of the main worktree's checkout, so its recorded commit drifted). Restore it so the
branch diff carries no submodule change.

---------

Co-authored-by: klein2 <klein2@local>

### [03e4fa7](https://github.com/vipshop/cache-dit/commit/03e4fa723134c5cebd406ef6080db9885deb6860)

- **作者**: DefTruth
- **时间**: 2026-11-12T01:50:09Z
- **提交信息**: perf(svdq): optimize small-M CuTe producers (#1297)

Use fused for small-M rank64 producers and K128 async split-K for small-M rank128 producers.

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-11-13
**监控日期**: 2026-11-12
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 96845
- **最后更新**: 2026-11-13T02:44:04Z

## 提交统计

- **昨日提交总数**: 94
- **提交者数量**: 69
- **主要提交者**: Uros Markovic, zhangyiming, Mikko Tukiainen

## AI分析总结

# vLLM 昨日提交分析（共 94 条）

## 1. 主要更新类型分布

- **Bug 修复占比最高**：约 30 条，覆盖 KV Offload、多模态、CUDA graph、MoE、前端等核心路径。
- **性能优化**：约 27 条，集中在 GLM 5.3、MoE、HiSparse、ROCm RDNA/GFX、AITER 算子融合等方向。
- **功能新增**：约 16 条，包括 KV Offload 触发器、可扩展 KV 缓存导出、Mamba2 投机解码、Tensorized 模型加载，以及 Kimi K3.1 Pro、GLM-5.3-Flash、MiniMax-M3 等新模型支持。
- **CI/工程化与重构**：测试自动分片、NIXL PD 测试 pytest 化、依赖升级（FlashInfer 0.7.4、FlashMLA、triton_kernels、xgrammar 0.2.9/0.5），以及移除死代码模型、TeleChat2/3 下线、移除 RunLLM 组件等清理工作。

## 2. 关键变更点与项目方向

- **KV Offload / KV Connector 密集迭代**：新增 store 触发器、Mooncake 预占修复、部分尾部卸载、ARC 驱逐策略；可扩展 KV 缓存支持 EXPORTS_FD 导出以对接 LMCache 多进程，warmup 块在 CUDA graph 捕获前释放，FlashInfer 自动调优峰值与缓存估算解耦。这直接服务于"廉价服务"目标，通过分层内存与缓存共享降低 GPU 显存压力。
- **投机解码持续演进**：PP 下草稿模型单 stage、FlashInfer CUDA graph 保留、Mamba2 ReplaySSM 落地 Triton 后端、GLM MTP 行裁剪（4.2% 吞吐提升），延续对低延迟生成的投入。
- **GLM 5.3 性能专项**：延迟特化默认开启带来 27% 端到端吞吐提升，叠加 MTP 行跳过，合计 E2E 提升超 30%，是本日最亮眼的单项收益。
- **多硬件并进**：AMD ROCm 约占三分之一提交，新增 mxfp4_mla 与 FP8 KV 缓存（DeepSeek-V4 稀疏 MLA）、AITER 算子融合（W_UK 吸收、滑窗解码、topk gating、MLA 头数对齐原生 tile）、K2 FFN 调优；另有 Intel XPU CI 恢复、NVIDIA SM90 优化。
- **MoE 内核强化**：FlashInfer mega mHC 融合、DeepGEMM BF16 MegaMoE、MXFP4 专家在 SM90 运行、routed-scale 枚举重构，响应大规模 MoE 推理需求。
- **Rust 前端成熟化**：多模态与 LoRA 的 engine-free renderer、引擎永久故障退出处理、MiniMax-M3 流式工具调用参数、Lark 文法组合、并行截断时 tokenizer 池化修复，标志其走向生产可用。

## 3. 对项目的影响

CUDA graph 池清理与重建修复了长运行服务的显存碎片问题；Elastic EP、EPLB、DeepGEMM 等修复保障大规模并行部署可靠性；字节码钩子清理、块 scale 广播等修复提升多进程与跨平台稳定性。KV 缓存导出为 disaggregated serving 与缓存共享生态铺路，前端流式路径开销削减直接改善长连接吞吐。多后端并进降低厂商锁定风险，配合 Kimi K3、Muse Spark MegaMoE 等 Recipe，强化其大模型生产级推理平台定位。

## 4. 值得关注的技术点

- **BF16 ReLU2 与 NVFP4 量化融合内核**：激活与量化一步完成，且 NVFP4 手动激活融合已扩展至更多 linear 后端，量化融合走向通用化。
- **硬件感知优化手法**：AITER MLA 头数对齐原生 tile 的 padding 调整、RDNA MXFP4 适配、LLVM 回归规避。
- **AI 协作开发**：多数提交含 Claude、Codex、Cursor 等 AI 共同署名，vLLM 已深度拥抱人机协作开发模式。

## 5. 总体意义

本日提交呈现三条清晰主线：通过 KV 分层卸载与连接器完善持续压低成本，通过投机解码、模型特化与量化融合持续拉升吞吐与延迟表现，通过多硬件适配、CI 加固与 Rust 前端成熟夯实工程底座。整体呈现"广度扩后端、深度抠性能、稳态修边角"的成熟期特征，推动 vLLM 从推理引擎向稳定、高效、多平台的 LLM 服务基础设施演进，正从功能快速扩张转向生产级硬化与生态互通。

## 详细提交记录

### [f48bfde](https://github.com/vllm-project/vllm/commit/f48bfde4dde385b8dde7df481be7c8c84dff23f5)

- **作者**: Nick Hill
- **时间**: 2026-11-12T23:32:24Z
- **提交信息**: [Bugfix] Clear cuBLAS workspaces at in-process shutdown to free the graph pool (#67279)

Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [3bc1d31](https://github.com/vllm-project/vllm/commit/3bc1d31306e9a10fce59846f888fe106f274bc8c)

- **作者**: Amir Friedman
- **时间**: 2026-11-12T23:13:46Z
- **提交信息**: [KV Offload] Add a store trigger and isolated store trigger handlers (#64286)

Signed-off-by: Amir Friedman <Amir.Friedman1@ibm.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Or Ozeri <oro@il.ibm.com>

### [508e578](https://github.com/vllm-project/vllm/commit/508e5784b18a0addf1d607bb7eeaf6792f24c142)

- **作者**: Matthew Bonanni
- **时间**: 2026-11-12T23:11:48Z
- **提交信息**: [Perf][HiSparse] Batch the coordinator's per-page residency bookkeeping (#65607)

Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Lucas Wilkinson <lwilkins@redhat.com>

### [b704146](https://github.com/vllm-project/vllm/commit/b70414673330f969f07bd6d0f214fd536e6a7dd1)

- **作者**: Josh Schell
- **时间**: 2026-11-12T22:20:49Z
- **提交信息**: [Bugfix][Elastic EP] Recreate stat loggers before starting new engines (#67068)

Signed-off-by: josh schell <josh.schell@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Micah Williamson <micah.williamson@amd.com>
Co-authored-by: Wei Zhao <51183510+wzhao18@users.noreply.github.com>

### [145cc64](https://github.com/vllm-project/vllm/commit/145cc6428b65db1c4b26ce8d28c7dec444563561)

- **作者**: Thang Nguyen
- **时间**: 2026-11-12T21:44:51Z
- **提交信息**: [CI] Enroll 7 more jobs in automatic sharding (#66830)

Signed-off-by: Thang Nguyen <thangnguyenvn647@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [1273ccc](https://github.com/vllm-project/vllm/commit/1273ccc1df92730e1464c046f9f3cceab28a7fc7)

- **作者**: Thang Nguyen
- **时间**: 2026-11-12T21:43:53Z
- **提交信息**: [CI] Run the NIXL PD tests as pytest and enroll every Disaggregated step (#66910)

Signed-off-by: Thang Nguyen <thangnguyenvn647@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [6363872](https://github.com/vllm-project/vllm/commit/6363872519d46fa1767a8d38c5fe6f08a83061b2)

- **作者**: Woosuk Kwon
- **时间**: 2026-11-12T21:41:34Z
- **提交信息**: [Recipe] Use the inkling-2-small image for Inkling 2 Small (#67322)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [663dacc](https://github.com/vllm-project/vllm/commit/663daccfb9e1f39f9f9f93034bf87bc709d91c06)

- **作者**: Yifei Wang
- **时间**: 2026-11-12T21:40:32Z
- **提交信息**: [Spec Decode][PP] Run draft models as a single pipeline stage (#66063)

Signed-off-by: Yifei Wang <yifei.w@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [c907905](https://github.com/vllm-project/vllm/commit/c907905a87e233ef68b77927c83aaeca1de7946a)

- **作者**: Seyfal Sultanov
- **时间**: 2026-11-12T21:39:00Z
- **提交信息**: [Bugfix][Spec Decode] Keep FlashInfer CUDA graphs for drafters with their own head count (#62964)

Signed-off-by: Yufeng He <40085740+he-yufeng@users.noreply.github.com>
Signed-off-by: Seyfal Sultanov <seyfal.s@outlook.com>
Co-authored-by: Yufeng He <40085740+he-yufeng@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [df8c029](https://github.com/vllm-project/vllm/commit/df8c0296af83ac9807a473fbb01e614a643964c0)

- **作者**: Matthew Bonanni
- **时间**: 2026-11-12T21:37:37Z
- **提交信息**: [HiSparse] GLM-5.3-Flash support (#61243)

Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Signed-off-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Lucas Wilkinson <LucasWilkinson@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [ee2a078](https://github.com/vllm-project/vllm/commit/ee2a0783d117f556caaff47a29080a73cb253433)

- **作者**: Matthew Bonanni
- **时间**: 2026-11-12T21:27:33Z
- **提交信息**: [Dependency] Upgrade FlashInfer to 0.7.4 (#67042)

Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [b9fdd3f](https://github.com/vllm-project/vllm/commit/b9fdd3f7536c96cb874e45c524a023d921abbbe2)

- **作者**: Woosuk Kwon
- **时间**: 2026-11-12T21:26:32Z
- **提交信息**: [Recipe] Add Inkling 2 Small Recipe (#67319)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [e2421d2](https://github.com/vllm-project/vllm/commit/e2421d2ac5fb82c1659e04288762eeddad099ecc)

- **作者**: Uros Markovic
- **时间**: 2026-11-12T20:27:10Z
- **提交信息**: [ROCm][RDNA][Perf] Bump triton_kernels to ROCm 3.8.x with the RDNA MXFP4 configs (#64331)

Signed-off-by: Uros Markovic <umarkovi@amd.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Rohan Potdar <rohan.potdar@amd.com>

### [dc405af](https://github.com/vllm-project/vllm/commit/dc405afdea3a13203b16645fe2422f20d9afae23)

- **作者**: Uros Markovic
- **时间**: 2026-11-12T20:26:29Z
- **提交信息**: [ROCm][RDNA][Perf][MoE] Use w2 scatter + topk sum for the tk 3.8 OAI MoE combine on RDNA (#64055)

Signed-off-by: Uros Markovic <umarkovi@amd.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [1c4f8c4](https://github.com/vllm-project/vllm/commit/1c4f8c41a3f276d5beba5b83796b5fae50622d35)

- **作者**: Jakub Zakrzewski
- **时间**: 2026-11-12T20:08:05Z
- **提交信息**: [Quantization][Fusion] Extend manual activation fusion to more NVFP4 linear backends (#65149)

Signed-off-by: Jakub Zakrzewski <jzakrzewski@nvidia.com>
Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [0e633c4](https://github.com/vllm-project/vllm/commit/0e633c4a867680a1e92deb0dc92d1d39aaaf06a7)

- **作者**: francesco-bertolotti
- **时间**: 2026-11-12T20:01:03Z
- **提交信息**: build with param.dtype when one is not specified (#67212)

Signed-off-by: Francesco Bertolotti <francesco.bertolotti@domyn.com>
Signed-off-by: francesco-bertolotti <francesco.bertolotti@igenius.ai>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [c74cab9](https://github.com/vllm-project/vllm/commit/c74cab9b33659e92de9ca9c35eb949c78ebbe64c)

- **作者**: Chaitanya Sri Krishna Lolla
- **时间**: 2026-11-12T19:04:53Z
- **提交信息**: [ROCm][DI-CI] Enable Kimi K3 in AMD DI CI pipeline for nightly runs (#67056)

Signed-off-by: lcskrishna <lollachaitanya@gmail.com>
Co-authored-by: Shanshan Shen <467638484@qq.com>

### [701c2ec](https://github.com/vllm-project/vllm/commit/701c2ec95613701430b9b6473d12d1304c37c7e7)

- **作者**: Chauncey
- **时间**: 2026-11-12T18:58:49Z
- **提交信息**: [Bugfix] Reset the global CUDA graph pool on engine shutdown (#67201)

Signed-off-by: chaunceyjiang <chaunceyjiang@gmail.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [df5d803](https://github.com/vllm-project/vllm/commit/df5d80339b5fbca645e991444970b75fa330cd35)

- **作者**: Hosang Yoon
- **时间**: 2026-11-12T18:01:36Z
- **提交信息**: [ROCm] Unify ViT FlashAttention backend selection (#50449)

Signed-off-by: Hosang Yoon <hosang.yoon@amd.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: Rohan Potdar <rohanpotdar138@gmail.com>
Co-authored-by: Rohan Potdar <rohan.potdar@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [77eca0d](https://github.com/vllm-project/vllm/commit/77eca0dc06a94f5c7e4600d5d10935d2a07f9b52)

- **作者**: Robert Esclapez
- **时间**: 2026-11-12T18:00:45Z
- **提交信息**: [ROCm][RDNA] ROCM_RDNA_ATTN: work around an LLVM VGPR regression that spills decode kernels on gfx11 (#67226)

Signed-off-by: Robert Esclapez Garcia <robert.garcia@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [7115dd1](https://github.com/vllm-project/vllm/commit/7115dd1ea6d3486e21abd29cf371971714488e91)

- **作者**: fxmarty-amd
- **时间**: 2026-11-12T18:00:04Z
- **提交信息**: [CI][Quantization] Skip ModelOpt INT8_PB_WO routing test on ROCm (#67263)

Signed-off-by: Felix Marty <Felix.Marty@amd.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [e5dc65c](https://github.com/vllm-project/vllm/commit/e5dc65c1c4a398b718341c397ee4f1413baffcb4)

- **作者**: Jiangyun Zhu
- **时间**: 2026-11-12T17:40:14Z
- **提交信息**: [Model] Kimi K3.1 Pro (split 5/6: ROCm DCP, P/D, indexer top-k) (#65685)

Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>
Signed-off-by: Mi Sun Park <misunp@nvidia.com>
Signed-off-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: Roger Wang <hey@rogerw.io>
Co-authored-by: wangzhengtao <wangzhengtao@msh.team>
Co-authored-by: wanglinian <wanglinian@stu.pku.edu.cn>
Co-authored-by: Kimi <kimi@moonshot.cn>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Bowen Wang <abmfy@icloud.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: qizixi <22851944+zixi-qi@users.noreply.github.com>
Co-authored-by: Thien Tran <gau.nernst@yahoo.com.sg>
Co-authored-by: Jiahan Chang (Cyrus) <173873397+jiahanc@users.noreply.github.com>
Co-authored-by: Perkz Zheng <67892460+PerkzZheng@users.noreply.github.com>
Co-authored-by: Wei Zhao <51183510+wzhao18@users.noreply.github.com>
Co-authored-by: Wei Zhao <weizha@nvidia.com>
Co-authored-by: Yifan Qiao <yifanqiao@inferact.ai>
Co-authored-by: Jared Wen <jaredwen@inferact.ai>
Co-authored-by: billishyahao <bill.he@amd.com>
Co-authored-by: Yichao Zhu <Yichao.Zhu@amd.com>
Co-authored-by: hyukjlee <hyukjlee@amd.com>
Co-authored-by: seungrokj <seungrok.jung@amd.com>
Co-authored-by: Hexiang Wang <56632993+whx-sjtu@users.noreply.github.com>
Co-authored-by: seungrokj <144636725+seungrokj@users.noreply.github.com>
Co-authored-by: inferact-agent-v[bot] <326714608+inferact-agent-v[bot]@users.noreply.github.com>
Co-authored-by: v <v@inferact.ai>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Hongxia Yang <hongxia.yang@amd.com>
Co-authored-by: Hongxia Yang <62075498+hongxiayang@users.noreply.github.com>
Co-authored-by: Jiayi Yan <1195343015@qq.com>
Co-authored-by: 1195343015 <1195343015@users.noreply.github.com>
Co-authored-by: mispa-ms <81828223+mispa-ms@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>

### [def41bb](https://github.com/vllm-project/vllm/commit/def41bb0afe6d50c111b15391986408ad332d1a9)

- **作者**: Pratham Shirbhate
- **时间**: 2026-11-12T17:21:47Z
- **提交信息**: [Bugfix] granite_20b_fc: render conversations that carry a system message (#66348)

Signed-off-by: Pratham Shirbhate <prathamshirbhate1909@gmail.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [a793351](https://github.com/vllm-project/vllm/commit/a7933519764efd3b51782ebd7df4362c527e4a4c)

- **作者**: Harry Mellor
- **时间**: 2026-11-12T17:12:05Z
- **提交信息**: [Model Loader] Load tensorized vLLM models into the other model implementation (#67205)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [778f0fe](https://github.com/vllm-project/vllm/commit/778f0fe600242a17229611011d51cf7c7ca63661)

- **作者**: Wentao Ye
- **时间**: 2026-11-12T16:45:40Z
- **提交信息**: [GLM 5.3 Perf] Skip unused MTP post-attention rows, 4.2% E2E throughput improvement (#67104)

Signed-off-by: yewentao256 <zhyanwentao@126.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [9573fb5](https://github.com/vllm-project/vllm/commit/9573fb500efc4d8ffaab329a70be23d6c7e7311f)

- **作者**: Jee Jee Li
- **时间**: 2026-11-12T16:44:54Z
- **提交信息**: [Recipe] Enable Muse Spark MegaMoE and B300 specialized decode (#67269)

Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>

### [02981a8](https://github.com/vllm-project/vllm/commit/02981a8f53fe9dabaa6de052bbd6821c5c3eb331)

- **作者**: Wentao Ye
- **时间**: 2026-11-12T16:44:28Z
- **提交信息**: [GLM5.3 Perf] Enable `latency_specialized` by default, 27.0% E2E Throughput improvement (#67099)

Signed-off-by: yewentao256 <zhyanwentao@126.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [fb631f9](https://github.com/vllm-project/vllm/commit/fb631f9b5f2396ee3730802a442224391aaba7cb)

- **作者**: Oxana Korzh
- **时间**: 2026-11-12T16:31:53Z
- **提交信息**: [ROCm][Perf][DSv4.1] Shard the sparse-indexer decode rows across TP (#66047)

Signed-off-by: Oxana Korzh <okorzh@amd.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [b8ff067](https://github.com/vllm-project/vllm/commit/b8ff067c46ff02f8b6543f20a0e14e073e5d3513)

- **作者**: zhangyiming
- **时间**: 2026-11-12T16:31:34Z
- **提交信息**: [Quantization][OOT] Fix OnlineQuantizationConfig overriding the registered OOT online quantization config (#64056)

Signed-off-by: menogrey <1299267905@qq.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [c674476](https://github.com/vllm-project/vllm/commit/c674476e2d47629859901eca43ae8555d21648b0)

- **作者**: Wentao Ye
- **时间**: 2026-11-12T16:16:17Z
- **提交信息**: [Refactor] Remove dead code models (#67085)

Signed-off-by: yewentao256 <zhyanwentao@126.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [9263161](https://github.com/vllm-project/vllm/commit/9263161af292eee3dbd84ea803f75198587606af)

- **作者**: Simon Mo
- **时间**: 2026-11-12T16:15:32Z
- **提交信息**: [Docs] Remove RunLLM widget (#67092)

Co-authored-by: vllm-agent <claw@inferact.ai>

### [3f1ebac](https://github.com/vllm-project/vllm/commit/3f1ebac297fb8791a8fa8ee55e635e7fa93ddaec)

- **作者**: Dakai An
- **时间**: 2026-11-12T16:04:47Z
- **提交信息**: [KV Connector] Mooncake Store: keep a request re-admitted in the step that reports its preemption (#66384)

Signed-off-by: Dakai An <dakaian108@gmail.com>

### [e509ffb](https://github.com/vllm-project/vllm/commit/e509ffb94361c36cbecf02801225089253fc0d49)

- **作者**: Andreas Karatzas
- **时间**: 2026-11-12T15:47:44Z
- **提交信息**: [Kernel][Mamba] Support Mamba2 ReplaySSM speculative decoding on the Triton backend (#66318)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [f0787a9](https://github.com/vllm-project/vllm/commit/f0787a9ab838d1df96300c517bf109ef140b4598)

- **作者**: Dakai An
- **时间**: 2026-11-12T14:36:20Z
- **提交信息**: [KV Connector][Spec Decode] Support lookahead block hashes in remaining KV connectors (#65448)

Signed-off-by: Dakai An <dakaian108@gmail.com>

### [0317258](https://github.com/vllm-project/vllm/commit/031725855711e4160d9920ef5074f451c3bb4e91)

- **作者**: Ao Tang
- **时间**: 2026-11-12T14:25:25Z
- **提交信息**: [Bugfix][Model Runner V2] Embed randomized dummy input ids for inputs_embeds models (#64530)

Signed-off-by: Ao Tang <aot@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Wei Zhao <51183510+wzhao18@users.noreply.github.com>

### [02ed6dc](https://github.com/vllm-project/vllm/commit/02ed6dc75a0bcf4a0d9ff2824f223e0fb7031420)

- **作者**: nien-hui
- **时间**: 2026-11-12T14:16:56Z
- **提交信息**: [Bugfix] Honor X-Vllm-Priority in scale-out generate. (#67008)

Signed-off-by: paul <paulqwer.cs13@nycu.edu.tw>
Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>

### [3f96f6b](https://github.com/vllm-project/vllm/commit/3f96f6b923a0f1e5671b026a8ab75465c49838fb)

- **作者**: Chauncey
- **时间**: 2026-11-12T13:48:46Z
- **提交信息**: [Build] Bump FlashMLA to enable SM90 small-head ETAP sparse prefill (#67175)

Signed-off-by: chaunceyjiang <chaunceyjiang@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [fa211f2](https://github.com/vllm-project/vllm/commit/fa211f2de248ae79e22cee83712a0d12ee7ffc43)

- **作者**: Bowen Wang
- **时间**: 2026-11-12T13:26:57Z
- **提交信息**: [Bugfix][EPLB] Start the async rearrangement interval after the last layer commits (#64485)

Signed-off-by: Bowen Wang <bowen@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [d0c2036](https://github.com/vllm-project/vllm/commit/d0c2036061e3d00a2c333093362b6e8cc2a24d34)

- **作者**: Chauncey
- **时间**: 2026-11-12T13:18:07Z
- **提交信息**: [Bugfix][MoE] Skip DeepGEMM localizer cleanup on SM90 (#67225)

Signed-off-by: chaunceyjiang <chaunceyjiang@gmail.com>

### [b4b0b96](https://github.com/vllm-project/vllm/commit/b4b0b96fffb62bf4f86287c91c3e2c4d2503895f)

- **作者**: Yu-Chi (Maggie) Pai
- **时间**: 2026-11-12T12:48:07Z
- **提交信息**: [Bugfix][Multimodal] Skip the encoder CUDA graph for precomputed embeddings (#65535)

Signed-off-by: Baiiiiiiiiii <2002paipai@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>

### [8a36f08](https://github.com/vllm-project/vllm/commit/8a36f080e2a28a91137d86ef503eab6e37d0a9d4)

- **作者**: yutwu
- **时间**: 2026-11-12T12:01:29Z
- **提交信息**: [Bugfix][KV Offload] Enable partial-tail offload for hybrid models under DCP (#58619)

Signed-off-by: Yuting Wu (DLAlgo) <yutwu@nvidia.com>
Co-authored-by: Devin <158243242+devin-ai-integration[bot]@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Or Ozeri <oro@il.ibm.com>

### [19812fa](https://github.com/vllm-project/vllm/commit/19812fa0be0ae219004e25c25ed10126a07a8bb5)

- **作者**: Chinmay Shrivastava
- **时间**: 2026-11-12T11:58:43Z
- **提交信息**: [Bugfix][KV Offload] Evict a running request’s ARC chunks tail first (#67098)

Signed-off-by: JonSnow1807 <JonSnow1807@users.noreply.github.com>
Co-authored-by: JonSnow1807 <JonSnow1807@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [8291578](https://github.com/vllm-project/vllm/commit/82915781df4a163de021d3f2fc329a10c0215b42)

- **作者**: waizuichougou
- **时间**: 2026-11-12T11:56:18Z
- **提交信息**: [Bugfix][KV Offload] Clear partial-tail pending state on a required group miss (#67152)

Signed-off-by: waizuichougou <2082431897@qq.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [b6f417f](https://github.com/vllm-project/vllm/commit/b6f417fcd1c291b0cbb013579e7c697ace4e4e0a)

- **作者**: Subhash Polisetti
- **时间**: 2026-11-12T11:32:30Z
- **提交信息**: [Bugfix][Multimodal] Pass only the video count to get_num_frames_with_most_features (#66608)

Signed-off-by: subhash polisetti <subhashr161347@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>

### [49d6074](https://github.com/vllm-project/vllm/commit/49d6074354983f5278ba7202ce913f9b305d71eb)

- **作者**: Reid
- **时间**: 2026-11-12T11:32:03Z
- **提交信息**: [Bugfix][Rust Frontend] Exit on permanent engine failure (#66773)

Signed-off-by: reidliu41 <reid201711@gmail.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [ddb0cb8](https://github.com/vllm-project/vllm/commit/ddb0cb8cb83591ffd743fe5ad56147ca7c3d4b86)

- **作者**: yousef-cohere
- **时间**: 2026-11-12T11:27:19Z
- **提交信息**: [Bugfix][Frontend] Render tool-result media in the Inkling renderer (#66891)

Signed-off-by: yousef.sadr <yousef.sadr@cohere.com>
Co-authored-by: North Code <noreply@cohere.com>

### [3b43d2b](https://github.com/vllm-project/vllm/commit/3b43d2b01c2fb667101746e1acd33b6a3c9d0863)

- **作者**: Uros Markovic
- **时间**: 2026-11-12T11:13:31Z
- **提交信息**: [Bugfix][ROCm] Restore MoE weight padding dropped by #46009 (#61872)

Signed-off-by: Uros Markovic <umarkovi@amd.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Douglas Lehr <91553416+dllehr-amd@users.noreply.github.com>

### [9a77b42](https://github.com/vllm-project/vllm/commit/9a77b4201bc4551f7e23ce59758dcbe6410c9e10)

- **作者**: Itay Etelis
- **时间**: 2026-11-12T10:59:06Z
- **提交信息**: Share DeepSeek V4.1 CPU KV across TP ranks (#65373)

Signed-off-by: Itay Etelis <92247226+Etelis@users.noreply.github.com>

### [f55b08e](https://github.com/vllm-project/vllm/commit/f55b08ec0f904ddeec748ea24c1e029cab992292)

- **作者**: Himanshu Jaju
- **时间**: 2026-11-12T10:54:37Z
- **提交信息**: [Bugfix][KV Connector] Skip Mooncake saves after failed existence checks (#67080)

Signed-off-by: Himanshu Jaju <hj@mistral.ai>

### [5916cef](https://github.com/vllm-project/vllm/commit/5916cef98eed2152b232ed4712ac468402be849b)

- **作者**: Guoxiang Zu
- **时间**: 2026-11-12T10:22:34Z
- **提交信息**: [Bugfix][P/D] Proxies: return text/event-stream for streaming requests (#67150)

Signed-off-by: GuoxiangZu <zuguoxiang@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [1c675c6](https://github.com/vllm-project/vllm/commit/1c675c68687ddfdb823f0c8662358c380f3f2ca9)

- **作者**: Lantao Jin
- **时间**: 2026-11-12T10:11:24Z
- **提交信息**: [Bugfix][Frontend] Report the matching request type's error from SageMaker /invocations (#66777)

Signed-off-by: Lantao Jin <ltjin@amazon.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [2011b8f](https://github.com/vllm-project/vllm/commit/2011b8f0fd783dadc2d71359487b2b5d67a82744)

- **作者**: Dao007forever
- **时间**: 2026-11-12T09:30:41Z
- **提交信息**: [Rust Frontend] Multimodal and LoRA in the engine-free renderer (#65993)

Signed-off-by: Dao Le <Dao007forever@gmail.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [94febce](https://github.com/vllm-project/vllm/commit/94febce7563ae2d67a062dc0f8ab408cd817f66c)

- **作者**: Yiliu Dong
- **时间**: 2026-11-12T09:07:34Z
- **提交信息**: [Perf][MoE] Enable SM90 block-FP8 MegaMoE via FlashInfer MoE-EP (#62603)

Signed-off-by: Yiliu Dong <91178480+qianlihuang@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [0a77dea](https://github.com/vllm-project/vllm/commit/0a77deacd3035b723994d15dc7a65f4ad6859a70)

- **作者**: Mikko Tukiainen
- **时间**: 2026-11-12T09:02:59Z
- **提交信息**: [ROCm][Perf][Muse Spark] Add gfx942 FP8 W8A8 fused-MoE configs for E=32,N=4096 (#63727)

Signed-off-by: Mikko Tukiainen <Mikko.Tukiainen@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [613fa94](https://github.com/vllm-project/vllm/commit/613fa94e3d185b6bdc9057d5ff8fdc37c63fc294)

- **作者**: Fanli Lin
- **时间**: 2026-11-12T08:41:35Z
- **提交信息**: [XPU][CI] Re-enable `test_reset_prefix_cache_e2e` and `test_scheduler_e2e` on XPU (#62656)

Signed-off-by: Lin, Fanli <fanli.lin@intel.com>
Signed-off-by: Fanli Lin <fanli.lin@intel.com>
Signed-off-by: Fanli Lin <fanli@gnr17409.jf.intel.com>

### [9e6815a](https://github.com/vllm-project/vllm/commit/9e6815acab1a6acb188931510271b1bce4688c75)

- **作者**: Itay Etelis
- **时间**: 2026-11-12T08:27:58Z
- **提交信息**: [Perf][KV Offload] Split the shared Tiering region and skip the scheduler pre-fault (#66391)

Signed-off-by: Itay Etelis <92247226+Etelis@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [d969092](https://github.com/vllm-project/vllm/commit/d9690929be4167eaafe964f274f992bcc6ffe03a)

- **作者**: Harry Mellor
- **时间**: 2026-11-12T08:20:50Z
- **提交信息**: [Model] Remove TeleChat2 and TeleChat3 (#67035)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [c6573ee](https://github.com/vllm-project/vllm/commit/c6573eed5e56fd39b01d610db04616ed9b221851)

- **作者**: Juntian Liu
- **时间**: 2026-11-12T07:53:06Z
- **提交信息**: [Recipe] MiniMax-M3.1-Flash: sync the GB300 Dynamo AgentX presets to InferenceX #4998 (#67184)

Signed-off-by: Juntian Liu <Juntianl777@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [efe1230](https://github.com/vllm-project/vllm/commit/efe12305f064b9c5301231d66eb42b7c0db5895f)

- **作者**: Stefano Castagnetta
- **时间**: 2026-11-12T07:32:03Z
- **提交信息**: [Misc] Use the b12x package shipped with flashinfer-python (#64765)

Signed-off-by: Stefano Castagnetta <scastagnetta@nvidia.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [6d3eba0](https://github.com/vllm-project/vllm/commit/6d3eba0272acac182d2b95d5374b619f1efd6ce5)

- **作者**: viktorkou
- **时间**: 2026-11-12T07:04:25Z
- **提交信息**: [Bugfix] Use max_split_size_mb:21 so freed 1-10 MiB tensors are reused (#66561)

Signed-off-by: Viktor Koukouliev <vkoukouliev@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [7a8f1f9](https://github.com/vllm-project/vllm/commit/7a8f1f9e7cf779afac354d3d8c14fcc185627cea)

- **作者**: Avinash Paul
- **时间**: 2026-11-12T06:43:45Z
- **提交信息**: [ROCm][Disagg][CI] Set token budgets for the MiniMax-M3 wide-EP cells (#66646)

Signed-off-by: avpaul <avpaul@amd.com>
Co-authored-by: avpaul <avpaul@amd.com>
Co-authored-by: Shanshan Shen <467638484@qq.com>

### [3b95523](https://github.com/vllm-project/vllm/commit/3b95523ed904cf02a26b872f4a900ef17e6be8ad)

- **作者**: Nick Hill
- **时间**: 2026-11-12T06:18:21Z
- **提交信息**: [Doc][Tests] Stop setting `gpu_memory_utilization` in most extensible KV cache cases (#67071)

Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [be47189](https://github.com/vllm-project/vllm/commit/be47189f37f6162991366ff6b91539f6e9d1f432)

- **作者**: Bugen Zhao
- **时间**: 2026-11-12T05:59:56Z
- **提交信息**: [Rust Frontend] Bump xgrammar-structural-tag to 0.5 and compose Lark answers (#66692)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [4fee061](https://github.com/vllm-project/vllm/commit/4fee061e3e42b5e23f8a6bd5e18e3efdc3626c87)

- **作者**: Bugen Zhao
- **时间**: 2026-11-12T05:59:56Z
- **提交信息**: [Frontend] Bump xgrammar to 0.2.9 and compose Lark answers as Lark (#66691)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [cfe069c](https://github.com/vllm-project/vllm/commit/cfe069c9e229dea2ae71acaa1b76f50a2fa98982)

- **作者**: Haishuo.Kong
- **时间**: 2026-11-12T05:39:14Z
- **提交信息**: [Bugfix][Frontend] Pool HF fast tokenizers in BaseRenderer so concurrent truncation stays per request (#65932)

Signed-off-by: Haishuo.Kong <haiskong@amd.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [dac5106](https://github.com/vllm-project/vllm/commit/dac51063cc1295a2a8426998c4c372b19c42a0f9)

- **作者**: amd-dlimpus
- **时间**: 2026-11-12T04:46:22Z
- **提交信息**: [ROCm][Attention] Add an mxfp4_mla KV cache for rope-free sparse MLA (read/write path) (#60321)

Signed-off-by: Limpus, David <dlimpus@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Simon Danielsson <70206058+simondanielsson@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Claude Sonnet 5.5 <noreply@anthropic.com>
Co-authored-by: Douglas Lehr <91553416+dllehr-amd@users.noreply.github.com>

### [54ba569](https://github.com/vllm-project/vllm/commit/54ba56981e54489255bf95eaa6e108fc1c9f9069)

- **作者**: David Teather
- **时间**: 2026-11-12T04:39:58Z
- **提交信息**: [Perf][Frontend] Trim per-chunk and per-request work in the completions stream (#66325)

Signed-off-by: davidteather <34144122+davidteather@users.noreply.github.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [ee548e7](https://github.com/vllm-project/vllm/commit/ee548e7f6036e7fc8ff0090b0daecdbfe42d43d1)

- **作者**: Nick Hill
- **时间**: 2026-11-12T04:37:24Z
- **提交信息**: [Bugfix] Remove compiled models' bytecode hooks at in-process shutdown (#67081)

Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [b5dcc87](https://github.com/vllm-project/vllm/commit/b5dcc877257d644d63ecc01de4ac191e68b7abe7)

- **作者**: Ryan Rock
- **时间**: 2026-11-12T04:33:55Z
- **提交信息**: [ROCm][Bugfix] Route biased softmax/sigmoid top-k to AITER topk_gating (#67107)

Signed-off-by: Ryan Rock <ryan.rock@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [2a14a5e](https://github.com/vllm-project/vllm/commit/2a14a5e4778213d538e3cc1875fea432636f32e0)

- **作者**: Subhash Polisetti
- **时间**: 2026-11-12T04:22:57Z
- **提交信息**: [Bugfix][Multimodal] Cache multi-page Unlimited-OCR-2 requests in the processor cache (#66638)

Signed-off-by: subhash polisetti <subhashr161347@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>

### [3de0b48](https://github.com/vllm-project/vllm/commit/3de0b48c85133be800f572a4e17c1f48e5c00c47)

- **作者**: Ayaan Nadamal
- **时间**: 2026-11-12T04:21:50Z
- **提交信息**: [Perf][mHC] use FlashInfer mega mHC for MHCFusedPostPreOp (GLM-5.3-Fl… (#65521)

Signed-off-by: Ayaan Nadamal <anadamal@nvidia.com>

### [6201c7d](https://github.com/vllm-project/vllm/commit/6201c7d3cd690f7f75494e48b3be1ff1f19ac03b)

- **作者**: Yihua Cheng
- **时间**: 2026-11-12T04:06:58Z
- **提交信息**: [KVConnector] Allocate the extensible KV cache exportable for EXPORTS_FD (LMCache MP) (#66674)

Signed-off-by: ApostaC <yihua@tensormesh.ai>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [8527d75](https://github.com/vllm-project/vllm/commit/8527d757d2184da0ed8f6c78532524fa6d23cc24)

- **作者**: Bugen Zhao
- **时间**: 2026-11-12T04:01:03Z
- **提交信息**: [Rust Frontend] Stream MiniMax M3 tool-call arguments (#66531)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [9a4decd](https://github.com/vllm-project/vllm/commit/9a4decde960a8dabcc0a6dba5cdedb9a7a5dcdef)

- **作者**: Bugen Zhao
- **时间**: 2026-11-12T04:01:02Z
- **提交信息**: [Rust Frontend] Match MiniMax M3 markers by token identity (#66767)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [c9c3648](https://github.com/vllm-project/vllm/commit/c9c36486c3f7c767c25bb37f087e38d101edf1ef)

- **作者**: Ning Liu
- **时间**: 2026-11-12T03:50:00Z
- **提交信息**: [MoE] Replace routed-scale bool flags with a RoutedScaleMode enum (#66859)

Signed-off-by: Ning Liu <3339723+nliu365@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [5237388](https://github.com/vllm-project/vllm/commit/52373885168d70886d0a047477a33f65f06b5dc0)

- **作者**: Ziyang Ma
- **时间**: 2026-11-12T03:38:12Z
- **提交信息**: [XPU][UT] Increase the prompt length in the late chunking test to allow prefix cache hits on XPU (#66978)

Signed-off-by: RyanMa29 <ziyang.ma@intel.com>

### [a547de8](https://github.com/vllm-project/vllm/commit/a547de8a8176c46bbfaf1c37e16de4c5180bbc43)

- **作者**: Oxana Korzh
- **时间**: 2026-11-12T03:23:51Z
- **提交信息**: [ROCm][MLA][DCP] Pad the AITER MLA decode head count to a native tile (#54899)

Signed-off-by: Oxana Korzh <okorzh@amd.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [20ad1db](https://github.com/vllm-project/vllm/commit/20ad1db3fe900ce07c2ee2ccdac077ed9826530b)

- **作者**: Canlin Guo
- **时间**: 2026-11-12T03:11:34Z
- **提交信息**: [Perf][GLM-5.3] DeepGEMM BF16 MegaMoE for unquantized checkpoints (#67040)

Signed-off-by: Canlin <canlinguosdu@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [0854d2f](https://github.com/vllm-project/vllm/commit/0854d2f280ef11a404ae56b4fe708f0462bca20d)

- **作者**: Mehmet Cagri
- **时间**: 2026-11-12T03:05:59Z
- **提交信息**: [ROCm][DSv4/4.1] Enable Tensor scale FP8 KV Cache for Sparse MLA (#66036)

Signed-off-by: Mehmet Cagri Kaymak <mehmet.kaymak@amd.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Fangzhou Ai <31551580+Fangzhou-Ai@users.noreply.github.com>

### [11ddd58](https://github.com/vllm-project/vllm/commit/11ddd587ebdcb3d3c4ed502e6c76d5da9768bba3)

- **作者**: Oxana Korzh
- **时间**: 2026-11-12T02:52:22Z
- **提交信息**: [ROCm][Perf] AITER FA: trim the sliding-window decode table with fewer ops (#63392)

Signed-off-by: Oxana Korzh <okorzh@amd.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [d838863](https://github.com/vllm-project/vllm/commit/d838863e2ba961c6617a1f36c78f52cfbf0fcfc4)

- **作者**: Fanli Lin
- **时间**: 2026-11-12T02:49:40Z
- **提交信息**: [Bugfix][XPU] Remove CUDA-only dependencies from Unlimited-OCR-2 DASH attention (#66495)

Signed-off-by: Lin, Fanli <fanli.lin@intel.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [8f0a381](https://github.com/vllm-project/vllm/commit/8f0a381fdca1a115837e6360d386a806f336381d)

- **作者**: Oxana Korzh
- **时间**: 2026-11-12T02:30:35Z
- **提交信息**: [ROCm][Perf][DSv4.1] Mono: tuned K2 FFN seam at TP4 / TP8 (#64883)

Signed-off-by: Oxana Korzh <okorzh@amd.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Douglas Lehr <91553416+dllehr-amd@users.noreply.github.com>

### [318fca3](https://github.com/vllm-project/vllm/commit/318fca3fddcd6950eeb739737eaafb0973e5f34a)

- **作者**: Jan Bernlöhr
- **时间**: 2026-11-12T02:19:27Z
- **提交信息**: [Bugfix] Exclude FlashInfer autotune peak from KV cache sizing (#66197)

Signed-off-by: Jan Bernloehr <jbernloehr@nvidia.com>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [d0eca76](https://github.com/vllm-project/vllm/commit/d0eca76eb41526910ca3317143ecda26985a1dc9)

- **作者**: rmhaskar
- **时间**: 2026-11-12T02:16:01Z
- **提交信息**: [Attention][MiniMax-M3] Add FlashInfer MSA backend for SM90 and SM120/SM121 (#66018)

Signed-off-by: Rajas Mhaskar <rmhaskar@nvidia.com>
Co-authored-by: Yicheng Jin <yichengj@nvidia.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [06dbdda](https://github.com/vllm-project/vllm/commit/06dbdda4b2b950a0b6083770b6417aa8e9f9ad16)

- **作者**: Yan Ma
- **时间**: 2026-11-12T02:06:03Z
- **提交信息**: [XPU] support adaptive verification for deepseek-v4 (#62309)

Signed-off-by: Yan Ma <yan.ma@intel.com>

### [bfc1e38](https://github.com/vllm-project/vllm/commit/bfc1e381135b8cc522ce7597e8da912010243355)

- **作者**: Samuel Nordmann
- **时间**: 2026-11-12T02:05:31Z
- **提交信息**: [Kernel] Fuse native BF16 ReLU2 with NVFP4 quantization (#59384)

Signed-off-by: samnordmann <snordmann@nvidia.com>
Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [d6cf068](https://github.com/vllm-project/vllm/commit/d6cf0684aca86b70351a14d581a1c37b74e21d04)

- **作者**: Divakar Verma
- **时间**: 2026-11-12T02:01:16Z
- **提交信息**: [CI][ROCm] Move the AMD monokernel steps into a Monokernels test area (#67073)

Signed-off-by: Divakar Verma <divakar.verma@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [da7520f](https://github.com/vllm-project/vllm/commit/da7520f7fa731f18c046908c652624647f476d32)

- **作者**: aoshen02
- **时间**: 2026-11-12T01:42:32Z
- **提交信息**: [Frontend][Multimodal] Accept features together with content_parts in /generate (#57796)

Signed-off-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [92a7c21](https://github.com/vllm-project/vllm/commit/92a7c216c0bc4d9613d3d18ce4e1b6beeebf951b)

- **作者**: xiangdong
- **时间**: 2026-11-12T01:29:05Z
- **提交信息**: [XPU][CI]Update working_dir from /workspace/vllm to /vllm-workspace/ (#66973)

Signed-off-by: zengxian <xiangdong.zeng@intel.com>

### [3319c62](https://github.com/vllm-project/vllm/commit/3319c629a148c8f7ce088445911d9db4119af134)

- **作者**: Hoang Nguyen
- **时间**: 2026-11-12T00:55:50Z
- **提交信息**: [Bugfix] Extensible KV cache: release warmup's blocks before CUDA graph capture (#66523)

Signed-off-by: Hoang Nguyen Tien <hoang.nguyentien.2601@gmail.com>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Bo Pang <80964159+Pb314314@users.noreply.github.com>

### [6713d05](https://github.com/vllm-project/vllm/commit/6713d05d6cfcec529394f7bb32ce5ec9a09e7d85)

- **作者**: Jan Bernlöhr
- **时间**: 2026-11-12T00:53:58Z
- **提交信息**: [Bugfix] Broadcast scalar block scales in Triton fused MoE (#66274)

Signed-off-by: Jan Bernloehr <jbernloehr@nvidia.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Wei Zhao <51183510+wzhao18@users.noreply.github.com>

### [63980fb](https://github.com/vllm-project/vllm/commit/63980fbf1ead0215e2bfaf89da7399895725003a)

- **作者**: Nick Hill
- **时间**: 2026-11-12T00:43:20Z
- **提交信息**: [Misc] Warn when gpu_memory_utilization withholds memory from the extensible KV cache (#66704)

Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [1d09f2b](https://github.com/vllm-project/vllm/commit/1d09f2bfdb44a4999831e3a2301c713ccfd878d7)

- **作者**: lucas-santos-amd
- **时间**: 2026-11-12T00:30:56Z
- **提交信息**: [ROCm][Perf][MLA] Fuse the decode W_UK absorb, q concat + fp8 quant and head pad via AITER (#64560)

Signed-off-by: Lucas Santos <Lucas.Santos@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Douglas Lehr <91553416+dllehr-amd@users.noreply.github.com>

### [127dd02](https://github.com/vllm-project/vllm/commit/127dd027d71afe6d349059245c887bb1c80bee1d)

- **作者**: simon-veitner-redhat
- **时间**: 2026-11-12T00:28:04Z
- **提交信息**: [Kernel][Perf] Run DeepGEMM Mega MoE on SM90 with MXFP4 experts (#64061)

Signed-off-by: Simon Veitner <sveitner@redhat.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-11-13
**监控日期**: 2026-11-12
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7724
- **最后更新**: 2026-11-13T01:42:04Z

## 提交统计

- **昨日提交总数**: 27
- **提交者数量**: 19
- **主要提交者**: wangyu, y-null, wuli666

## AI分析总结

# vllm-omni 昨日提交分析（第1/1批，共27条）

## 1. 主要更新类型分布

- **Bug修复**：约14条（占比最高），涉及 tokenizer、张量序列化、音频采样、GLM-Image 网格位置、LoRA 参数路由、视频捕获复用等
- **CI/构建**：约7条，集中在 ROCm/NIGHTLY 任务稳定化、任务合并与分级（nightly→weekly→blocking）
- **性能优化**：MiniCPM-o 4.5 的 NPU K/V cache 拆分与整图解码、MXFP4 MoE 原生启用、VAE 图解码
- **文档/配方**：RTX 4090 MiniMax-H3-Image 部署配方、性能上限（perf-ceiling）技能文档
- **新功能/配方**：Sophon-Realtime-32B 全双工语音到语音配方

## 2. 关键变更点与项目方向的关系

- **多模态/全双工音频是核心主线**：MiMo-Audio 种子采样恢复、MiniCPM-o 双工边界保持、Voxtral MRV2 后处理修复、Qwen3-Omni 双工精度+性能 CI 合并——直接服务于"omni-modality model serving"的项目定位。
- **异构硬件生态扩张**：NPU（华为昇腾）、ROCm（AMD）、MUSA（摩尔线程）并行推进，与 README 中"easy, fast, cheap"的目标一致，通过多后端降低部署门槛。
- **权重量共享机制成熟化**：#9850 运行时 rank 配对协调 + #10251 具体并行测试 + #10221 单 OmniServer 复用，显示多进程/多模型权重复用架构正在系统化。
- **LoRA 服务链路梳理**：StagePool 类型化客户端、LLM stage 类型化 owner、StagePool add_lora 路由，属于核心架构的类型安全重构。

## 3. 对项目的影响与潜在意义

- **稳定性优先**：大量 bugfix + CI 稳定化（OOM gate、HunyuanImage/Ming 启动）表明项目正从功能铺开转向生产可用性打磨。
- **社区规模活跃**：27条提交涉及约20位独立作者，华为、AMD、Intel、Mthreads、社区个人贡献者多元参与，生态健康。
- **量化落地**：MXFP4 MoE 原生启用（Intel 贡献）将显著降低 MoE 模型推理成本，契合"cheap"承诺。
- **部署可达性**：单卡 4090 配方 + Sophon 实时全双工配方，把高端多模态能力下放到消费级/边缘硬件。

## 4. 值得关注的技术点

- **连续张量序列化修复**（last stride≠1）：这是底层分布式通信的正确性问题，影响面广，值得回归测试。
- **GLM-Image 请求网格位置修复**（#9570）：图像扩散模型坐标系统的精度问题，关系生成质量。
- **CFG companion 注册顺序**（#7104）：Classifier-Free Guidance 的调度次序，直接影响扩散采样正确性。
- **diffusion attention 跨平台分发**（#10071）：树外平台支持，体现架构的可扩展性设计。

## 5. 对项目发展的整体影响

结合 README "Easy, fast, and cheap omni-modality model serving for everyone" 的定位，这批提交呈现清晰的三阶段推进：**架构类型化重构**（LoRA、权共享）夯实底层，**多后端+量化+单卡配方**降低成本门槛，**CI 分级（nightly→blocking）与全双工 bugfix** 保障质量。项目正从"能跑多模态"迈向"生产级全双工多模态服务"，核心竞争力在于同时覆盖语音、图像、视频的 omni 推理栈以及 NPU/ROCm/MUSA 的异构硬件适配能力，这在 vLLM 生态中形成了差异化定位。后续需关注权共享与 LoRA 重构是否引入行为变化，以及 ROCm/NIGHTLY 转正后的回归表现。

## 详细提交记录

### [b7bbfbd](https://github.com/vllm-project/vllm-omni/commit/b7bbfbdb4f2b3c070d9632043ea6cd2b1c601270)

- **作者**: Sylvan Liu
- **时间**: 2026-11-12T14:00:53Z
- **提交信息**: [Bugfix] Remove placeholder tokenizer: gpt2 from skip_tokenizer_init deploy configs (#10145)

Signed-off-by: Sylvan Liu <Sylvan.Liu@amd.com>
Signed-off-by: Liu, Sylvan <Sylvan.Liu@amd.com>

### [d3a88f1](https://github.com/vllm-project/vllm-omni/commit/d3a88f18d1a7b4c6fd56787858269043945f514e)

- **作者**: wuli666
- **时间**: 2026-11-12T13:58:49Z
- **提交信息**: [Bugfix] Serialize contiguous tensors whose last stride is not 1 (#10117)

Signed-off-by: wuli666 <421774554@qq.com>

### [7b3c84a](https://github.com/vllm-project/vllm-omni/commit/7b3c84a5e7b979f3265d218d6778d9f448c44843)

- **作者**: Dong1017
- **时间**: 2026-11-12T13:10:56Z
- **提交信息**: [Bugfix] Fix GLM-Image positions for requested grids (#9570)

Signed-off-by: GUOGUO <xwdong1998@163.com>

### [f65fe5a](https://github.com/vllm-project/vllm-omni/commit/f65fe5ab9e852bb50fc1f34c2a1f2664fd390806)

- **作者**: amy-why-3459
- **时间**: 2026-11-12T12:59:26Z
- **提交信息**: [Bugfix][MiMo-Audio] Restore seeded sampling in eager and CUDA graphs (#10241)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [7c586b5](https://github.com/vllm-project/vllm-omni/commit/7c586b5cbe019194b8d52f845139b3ff2c39ca18)

- **作者**: wangyu
- **时间**: 2026-11-12T10:57:28Z
- **提交信息**: [CI/Build] Keep MiniCPM-o 4.5 async_chunk cases adjacent to share one OmniServer (#10221)

Signed-off-by: wangyu <53896905+yenuo26@users.noreply.github.com>
Co-authored-by: wangyu <yenuo26@users.noreply.github.com>

### [163ee81](https://github.com/vllm-project/vllm-omni/commit/163ee8192a34c6c3c2a53f0113765a791ca7092c)

- **作者**: y-null
- **时间**: 2026-11-12T09:58:57Z
- **提交信息**: [Model][NPU] MiniCPM-o 4.5: split estimator K/V cache, fused codec-tail sampling and a whole-decode graph on stage 0 (#10016)

Signed-off-by: y-null <213026468+y-null@users.noreply.github.com>
Signed-off-by: y-null <y_null@qq.com>
Signed-off-by: y-null <y-null@users.noreply.github.com>
Co-authored-by: y-null <213026468+y-null@users.noreply.github.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>
Co-authored-by: y-null <y-null@users.noreply.github.com>

### [d112af2](https://github.com/vllm-project/vllm-omni/commit/d112af22e4e21af3976e6f83c342d77898a96e0f)

- **作者**: wangqiankun13
- **时间**: 2026-11-12T09:39:29Z
- **提交信息**: [Bugfix][CI] Give the weight-sharing worker test a concrete parallel … (#10251)

Signed-off-by: wangqiankun13 <wangqiankun13@huawei.com>

### [2a113f1](https://github.com/vllm-project/vllm-omni/commit/2a113f10645b23af3b0c3461900b2f69024a1664)

- **作者**: Yi Liu
- **时间**: 2026-11-12T09:36:09Z
- **提交信息**: [Quant] Enable native MXFP4 MoE (#9749)

Signed-off-by: yiliu30 <yi4.liu@intel.com>

### [7979211](https://github.com/vllm-project/vllm-omni/commit/7979211eab1379cc40f2165924b9bc634f8b1cf7)

- **作者**: lm10-arg
- **时间**: 2026-11-12T09:23:07Z
- **提交信息**: [Bugfix] Feed Voxtral MRV2 postprocess outputs (#10244)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Signed-off-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>

### [1b51ce9](https://github.com/vllm-project/vllm-omni/commit/1b51ce9c48fbf7de9f5bccc1309b775423c18bdc)

- **作者**: yiminghub2024
- **时间**: 2026-11-12T08:33:20Z
- **提交信息**: [Doc] Add single RTX 4090 MiniMax-H3-Image recipe (#10245)

Signed-off-by: yiminghub2024 <202503791+yiminghub2024@users.noreply.github.com>
Co-authored-by: yiminghub2024 <202503791+yiminghub2024@users.noreply.github.com>

### [fbafe69](https://github.com/vllm-project/vllm-omni/commit/fbafe698d158bebb8bee31bb549ea709c6c1ad08)

- **作者**: amy-why-3459
- **时间**: 2026-11-12T08:18:31Z
- **提交信息**: [Bugfix] Preserve MiniCPM-o duplex boundaries and sampled turn endings (#10066)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [ee44b9a](https://github.com/vllm-project/vllm-omni/commit/ee44b9afcaee0a9def12f54f31b1e3145264d583)

- **作者**: MinhaoLi0318
- **时间**: 2026-11-12T08:04:47Z
- **提交信息**: [Bugfix] Give LLM stages typed owners for vLLM LoRA engine args (#8574)

Signed-off-by: MinhaoLi0318 <lminhao039@gmail.com>
Signed-off-by: dengyunyang <584797741@qq.com>
Co-authored-by: dengyunyang <584797741@qq.com>

### [f22adf6](https://github.com/vllm-project/vllm-omni/commit/f22adf6112ebf311e38107296f5dcc690350580d)

- **作者**: Honghan Zhu
- **时间**: 2026-11-12T06:45:36Z
- **提交信息**: [Core] Add runtime coordination for rank-paired weight sharing (#9850)

Signed-off-by: zhuhh97 <zhuhonghan@huawei.com>
Signed-off-by: wangqiankun <wangqiankun13@huawei.com>
Co-authored-by: wangqiankun <wangqiankun13@huawei.com>
Co-authored-by: dengyunyang <584797741@qq.com>

### [e7c72b8](https://github.com/vllm-project/vllm-omni/commit/e7c72b87a761ab7786bfb3a4f4af1531d604bf8e)

- **作者**: amy-why-3459
- **时间**: 2026-11-12T06:36:09Z
- **提交信息**: [Doc] Add omni-perf-ceiling skill for serving performance ceilings (#10001)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [f57fe20](https://github.com/vllm-project/vllm-omni/commit/f57fe200dfa6bc7a793e05aa74b8dee165f2cd28)

- **作者**: JSs-u
- **时间**: 2026-11-12T06:11:39Z
- **提交信息**: [Bugfix][Core] Route StagePool add_lora through the typed client helper (#9466)

Signed-off-by: JSs-u <1564582868@qq.com>
Co-authored-by: dengyunyang <584797741@qq.com>

### [04e03a4](https://github.com/vllm-project/vllm-omni/commit/04e03a4cf8c562bf247118ffdaf0b49781d63b2c)

- **作者**: lm10-arg
- **时间**: 2026-11-12T05:41:35Z
- **提交信息**: [CI/Build][ROCm] Stabilize OOM sidecar saturation gate (#10218)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>

### [fecbdf4](https://github.com/vllm-project/vllm-omni/commit/fecbdf43023fb8f6d682e9fb71c928c1cc219aa9)

- **作者**: lm10-arg
- **时间**: 2026-11-12T05:40:19Z
- **提交信息**: [CI/Build][ROCm] Stabilize HunyuanImage weekly startup (#10208)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>

### [b6d3f8e](https://github.com/vllm-project/vllm-omni/commit/b6d3f8e72e51dd0fff0a8ef9f7cfb448b85ac6cc)

- **作者**: Diao Shengjia
- **时间**: 2026-11-12T04:34:00Z
- **提交信息**: [Bugfix][Diffusion] Dispatch diffusion attention on out-of-tree platforms (#10071)

Signed-off-by: GoDiao <diaoshengjia@gmail.com>

### [fe0557d](https://github.com/vllm-project/vllm-omni/commit/fe0557dc2566fcbe79ca704a5fb890e0a5d52d5b)

- **作者**: R0CKSTAR
- **时间**: 2026-11-12T03:25:25Z
- **提交信息**: [MUSA] MiniMax-H3-Image: enable the VAE graph decode on cuda-alike devices (#10139)

Signed-off-by: Xiaodong Ye <xiaodong.ye@mthreads.com>

### [6241280](https://github.com/vllm-project/vllm-omni/commit/6241280a7434b3904eae32a8c67d4400c6fc0036)

- **作者**: hac17
- **时间**: 2026-11-12T03:13:41Z
- **提交信息**: [CI/Build][ROCm] Promote seven NIGHTLY documentation and accuracy jobs (#10211)

Signed-off-by: hac17 <29197483+hacZ17@users.noreply.github.com>
Co-authored-by: hac17 <29197483+hacZ17@users.noreply.github.com>

### [0c6328e](https://github.com/vllm-project/vllm-omni/commit/0c6328ed4f5512cb1bf48d5bcba1f7634e47cbe7)

- **作者**: 梧桐雨
- **时间**: 2026-11-12T02:57:34Z
- **提交信息**: [Bugfix] Register CFG companions before parent dispatch (#7104)

Signed-off-by: wutongyuonce <147830929+wutongyuonce@users.noreply.github.com>
Signed-off-by: dengyunyang <584797741@qq.com>
Co-authored-by: dengyunyang <584797741@qq.com>

### [db48f8e](https://github.com/vllm-project/vllm-omni/commit/db48f8eea885cfe1521df8062bf052460b3b09b8)

- **作者**: psv666
- **时间**: 2026-11-12T02:51:18Z
- **提交信息**: [Bugfix] Reuse OpenCV captures on vLLM 0.33.0 (#10057)

Signed-off-by: psv666 <2693925048@qq.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [fee6134](https://github.com/vllm-project/vllm-omni/commit/fee61345cf35fdd243d4e2b6b6014caceede6f0c)

- **作者**: wangyu
- **时间**: 2026-11-12T02:25:20Z
- **提交信息**: [CI/Build] Move Qwen-Image and Drama 3 to weekly and map Ascend910 to A3 (#10068)

Signed-off-by: wangyu <410167048@qq.com>

### [cb559bf](https://github.com/vllm-project/vllm-omni/commit/cb559bffc8814daf69878c79f5f5b8eaff1a35b2)

- **作者**: hac17
- **时间**: 2026-11-12T02:20:53Z
- **提交信息**: [CI/Build][ROCm] Promote tiny diffusion READY coverage to blocking (#10210)

Signed-off-by: hac17 <29197483+hacZ17@users.noreply.github.com>
Co-authored-by: hac17 <29197483+hacZ17@users.noreply.github.com>

### [69cc94b](https://github.com/vllm-project/vllm-omni/commit/69cc94bb366d07a61c35db2b1aa11c70666bd4fa)

- **作者**: lm10-arg
- **时间**: 2026-11-12T02:17:49Z
- **提交信息**: [CI/Build][ROCm] Stabilize Ming weekly stage startup (#10206)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>

### [3949ecd](https://github.com/vllm-project/vllm-omni/commit/3949ecde469a09faf359335ec2157ca6c3705d8c)

- **作者**: psv666
- **时间**: 2026-11-12T02:09:59Z
- **提交信息**: [CI/Build] Combine Qwen3-Omni duplex C8 accuracy and performance (#9623)

Signed-off-by: psv666 <2693925048@qq.com>
Co-authored-by: wangyu <53896905+yenuo26@users.noreply.github.com>

### [80f1ae5](https://github.com/vllm-project/vllm-omni/commit/80f1ae5fb6a5e85ad58235cd10eb7a05d2082118)

- **作者**: BKtensor
- **时间**: 2026-11-12T01:33:09Z
- **提交信息**: [Recipe] Add Sophon-Realtime-32B-Tag (full-duplex speech-to-speech) (#10052)

Signed-off-by: Jie Jin <jiejin@adventists.ai>
Co-authored-by: Jie Jin <jiejin@adventists.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

---
