# GitHub Stars 合并报告 - 2026-05-06

**合并日期**: 2026-05-07
**监控日期**: 2026-05-06
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


**报告日期**: 2026-05-07
**监控日期**: 2026-05-06
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 1896
- **最后更新**: 2026-05-07T12:37:47Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 3
- **主要提交者**: Ting, Lu Di, Bin Jia

## AI分析总结

好的，作为专业的代码分析助手，以下是对仓库 `ByteDance-Seed/VeOmni` 昨日提交记录的分析总结。

### 1. 主要更新类型

- **Bug修复** (2项): 修复了FSDP2钩子问题和FLOPs计数错误。
- **功能新增/重构** (1项): 引入了GPU最优算子默认配置，并增加了严格的NPU验证（Breaking Change）。

### 2. 关键变更点及其与项目整体方向的关系

- **修复FSDP2预向后钩子 (commit 1):** 修复了在 `qwen3_5_moe` 等MoE模型中，`log-prob` 输出时FSDP2的预向后钩子被错误清除的问题。
    - **与项目方向的关系:** VeOmni的核心是“以模型为中心的分布式配方库”，旨在高效扩展任意模态模型训练。FSDP2是PyTorch中用于大规模模型分片训练的关键技术。修复此钩子问题，直接保障了MoE这类复杂架构模型在分布式训练下的正确性和稳定性，是项目核心能力的巩固。

- **修复FLOPs计数 (commit 2):** 修正了浮点运算次数（FLOPs）的计算错误。
    - **与项目方向的关系:** 准确的FLOPs计数是衡量模型训练效率、进行性能分析和资源规划的基础。修复此问题，确保了VeOmni提供的性能指标是可信的，有助于用户和开发者精确评估不同“配方”的效率，符合项目“优化训练”的宗旨。

- **GPU最优算子默认配置 + 严格NPU验证 (commit 3):** 这是一个**破坏性变更**。它将GPU上性能最优的算子设为默认配置，并增加了对NPU（神经网络处理器）的严格验证逻辑。
    - **与项目方向的关系:** 这是项目发展的一个关键里程碑。
        1.  **性能优化:** “GPU最优算子默认”直接体现了项目“Scaling Any Modality Model Training”的目标，通过默认启用最高效的算子，为用户提供开箱即用的高性能体验。
        2.  **硬件兼容性:** “严格NPU验证”表明VeOmni正在积极扩展其硬件支持范围，从GPU向NPU等更多样化的硬件平台迈进。这符合“Any Modality”背后隐含的“Any Hardware”趋势，增强了项目的通用性和未来适应性。

### 3. 对项目的影响和潜在意义

- **提升稳定性与可靠性:** 修复FSDP2和FLOPs计数Bug，直接提升了VeOmni作为训练框架的稳定性和数据可靠性，降低了用户在使用复杂模型（如MoE）时的出错风险。
- **降低用户使用门槛:** GPU最优算子默认化，意味着用户无需手动调优即可获得较好的训练性能，降低了使用门槛，让用户能更专注于模型本身。
- **拓展应用场景:** 严格的NPU验证为VeOmni支持非GPU硬件铺平了道路。这使其能够服务于更广泛的硬件生态（如国产芯片），对项目的长期发展和社区建设具有重大战略意义。
- **引入迁移成本:** 作为Breaking Change，现有用户可能需要调整其配置或代码以适应新的默认值和NPU验证逻辑。项目方需要提供清晰的迁移指南。

### 4. 值得关注的技术点

- **FSDP2与MoE模型的交互:** 修复FSDP2钩子问题，揭示了在混合专家（MoE）模型中使用FSDP2进行分布式训练时的一个潜在陷阱。这对于其他使用类似技术栈的开发者具有参考价值。
- **算子默认配置策略:** “GPU-optimal ops defaults”的实现方式值得关注。它是如何定义和选择“最优”算子的？是基于硬件自动检测，还是通过基准测试？这体现了项目的性能优化哲学。
- **NPU验证机制:** 严格的NPU验证逻辑是如何实现的？是简单的API兼容性检查，还是包含了性能或精度测试？这反映了项目对多硬件支持的严谨程度。

### 5. 基于项目背景，这些提交如何影响项目发展

根据README，VeOmni致力于“Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo”。

- **巩固核心能力:** 修复FSDP2和FLOPs的Bug，是在夯实“Distributed Recipe Zoo”的基础。一个稳定、准确的配方库是用户信任的基石。
- **加速性能迭代:** GPU最优算子默认化，是“Scaling”和“Optimizing”的直接体现。它让VeOmni在性能上更具竞争力，能吸引更多追求效率的用户。
- **开启硬件多元化新篇章:** 严格的NPU验证是项目从“GPU-only”向“Any Hardware”迈出的关键一步。这极大地扩展了VeOmni的潜在用户群和应用场景，尤其是在国产算力生态日益重要的背景下，这一举措具有前瞻性。这使得VeOmni不仅仅是一个GPU训练框架，而是一个面向未来多种计算架构的通用训练平台。

## 详细提交记录

### [58759e7](https://github.com/ByteDance-Seed/VeOmni/commit/58759e78015ad429507079aa443215e3c515364f)

- **作者**: Lu Di
- **时间**: 2026-05-06T21:09:36Z
- **提交信息**: [model] fix: preserve FSDP2 pre-backward hooks for log-prob outputs in qwen3_5_moe and other models (#731)

Co-authored-by: 鐘天楽 <zhluosuu@outlook.com>

### [6af26f7](https://github.com/ByteDance-Seed/VeOmni/commit/6af26f7c8b665bd5c50faa90a27c885fbcf772e3)

- **作者**: Bin Jia
- **时间**: 2026-05-06T19:33:08Z
- **提交信息**: [model] fix: fix flops count (#730)

### [29fc8e6](https://github.com/ByteDance-Seed/VeOmni/commit/29fc8e663979856420b5f03e912a69a7ffcea750)

- **作者**: Ting
- **时间**: 2026-05-06T07:42:16Z
- **提交信息**: [BREAKING][ops, model] feat: GPU-optimal ops defaults + strict NPU validation (#716)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-05-07
**监控日期**: 2026-05-06
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Light Image Video Generation Inference Framework
- **语言**: Python
- **星标数**: 2241
- **最后更新**: 2026-05-07T02:55:59Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Shankun Wang (王善昆)

## AI分析总结

好的，这是对仓库 `ModelTC/LightX2V` 昨日提交记录的分析总结。

### 1. 主要更新类型
- **Bug修复 (BugFix)**

### 2. 关键变更点及其与项目整体方向的关系
- **变更点**: 修复了 `cpu_offload` 功能中存在的同步缺失问题。
- **与项目方向的关系**: `LightX2V` 是一个**轻量级视频生成推理框架**。`cpu_offload` 是一种关键的内存优化技术，它允许将模型权重或中间激活值从GPU显存卸载到CPU内存，从而在有限的GPU资源下运行更大的模型或更长的视频生成任务。修复此处的同步问题，直接保障了该核心功能的稳定性和正确性，是项目实现“轻量”和“高效”目标的基础。

### 3. 对项目的影响和潜在意义
- **直接影响**: 解决了在使用 `cpu_offload` 时可能出现的**数据竞争或状态不一致**问题，避免了因此导致的**推理结果错误或程序崩溃**。
- **潜在意义**: 提升了框架在**低显存环境下的可靠性**。这对于希望使用消费级显卡（如RTX 3090/4090）运行视频生成模型的用户至关重要，能显著改善用户体验，并扩大项目的用户基础。

### 4. 值得关注的技术点
- **同步机制**: 在GPU异步执行（如CUDA streams）和CPU-GPU数据传输（`cpu_offload`）的场景下，确保操作顺序和内存可见性是关键。本次修复专门针对“同步缺失”问题，表明开发者对GPU编程中的**异步与同步模型**有深入理解。
- **社区贡献**: 修复方案源自社区贡献者 `HanFa` 的PR（#1051），项目维护者在此基础上进行了调整和合并。这体现了项目**开放的社区协作模式**，能够快速吸收外部优秀修复，提升代码质量。

### 5. 基于项目背景，这些提交如何影响项目发展
- **巩固核心优势**: `LightX2V` 的核心卖点是“轻量”和“高效”。`cpu_offload` 是实现这一目标的关键技术。修复其Bug，相当于**加固了项目的核心支柱**，确保其“轻量”特性不是以牺牲稳定性为代价。
- **提升成熟度**: 从“功能可用”到“功能稳定可靠”是项目走向成熟的关键一步。修复此类底层同步问题，是项目从原型阶段迈向**生产级应用**的重要标志。
- **增强用户信心**: 一个稳定、不出错的推理框架更容易获得开发者和研究者的信任，从而吸引更多用户使用、反馈和贡献，形成**正向循环**，加速项目发展。

## 详细提交记录

### [c177fd8](https://github.com/ModelTC/LightX2V/commit/c177fd82db34ae52f844c113578ee75693adcbf4)

- **作者**: Shankun Wang (王善昆)
- **时间**: 2026-05-06T07:36:07Z
- **提交信息**: [BugFix]: Fix missing synchronization issue in cpu_offload (#1053)

The fix is adapted from HanFa's contribution:
https://github.com/ModelTC/LightX2V/pull/1051

Adjustments were made to ensure proper synchronization behavior.

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-05-07
**监控日期**: 2026-05-06
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2065
- **最后更新**: 2026-05-07T11:38:33Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-05-07
**监控日期**: 2026-05-06
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5570
- **最后更新**: 2026-05-07T13:24:22Z

## 提交统计

- **昨日提交总数**: 12
- **提交者数量**: 10
- **主要提交者**: Lee Nau, Wei Zhao, yanqinz2

## AI分析总结

好的，这是对 `flashinfer-ai/flashinfer` 仓库昨日提交记录的分析总结。

### 1. 主要更新类型

- **Bug修复 (Bug Fixes)**: 这是本次更新的核心，修复了多个关键性问题。
- **功能新增 (New Features)**: 增加了新的算子、路由策略和融合操作。
- **性能优化 (Performance Optimization)**: 通过减少冗余操作和优化算法来提升性能。
- **版本发布 (Version Release)**: 发布了 v0.6.11 版本。
- **重构 (Refactor)**: 改进了构建系统和代码结构。

### 2. 关键变更点及其与项目整体方向的关系

- **`[f080fd3]` 修复构建系统**: 改进了 JIT 缓存构建脚本，使其在子模块已存在时跳过 `git submodule update`。这解决了在 Docker 等受限环境中构建失败的问题，提升了项目的**可移植性和构建鲁棒性**。
- **`[e6ac7cc]` 修复 MoE 自动调优器**: 将 MoE (Mixture-of-Experts) 自动调优器的桶配置从硬编码上限 (`8192`) 改为动态适应运行时输入。这直接修复了 DeepSeek-V3 等模型在长序列预填充时性能减半的问题，是**对大型模型推理性能的关键优化**。
- **`[cb44e7d]` 版本发布**: 将项目版本提升至 v0.6.11，标志着上述修复和新功能的正式发布。
- **`[d885b71]` 修复 MLA 内核整数溢出**: 修复了 MLA (Multi-head Latent Attention) 解码/预填充内核中的 32 位整数溢出问题。当处理大型 KV 缓存时，此问题会导致读取错误的页面，产生全零输出。这是**对长上下文推理正确性的关键修复**。
- **`[89af11c]` 增强 CuTe DSL FMHA 预填充**: 为 CuTe DSL 实现的 FMHA (Flash Multi-Head Attention) 预填充内核增加了 `attention_sink` 和 PDL (Programmatic Dependent Launch) 支持，并移除了前端填充要求。这**扩展了注意力算子的功能集**，使其能支持更复杂的注意力模式（如流式应用中的注意力下沉），并利用 PDL 提升性能。基准测试显示性能相比 TRT-LLM 原生实现有 1.0x-1.17x 的提升。
- **`[417e59f]` 新增 Sigmoid 路由函数**: 为 MoE 层增加了 `Sigmoid` 路由策略，该策略在 TopK 选择前应用 Sigmoid 函数且不进行重归一化。这**丰富了 MoE 路由的选项**，满足特定模型架构的需求。
- **`[979644f]` 优化 MoE 排序内核**: 移除了 `moe_sort` 包装器中冗余的 Python 端缓冲区初始化（如 `fill_(-1)`, `zero_()`），因为底层 CUDA 内核会自行写入所有条目。这**减少了不必要的 GPU 内核启动**，提升了 MoE 路由的性能。
- **`[55a9eea]` 修复 CUBIN 下载重试**: 将 CUBIN 文件下载的重试策略从确定性指数退避改为全抖动（full jitter）退避，以**缓解并发 CI 运行器导致的 CDN 节流问题**（如 403 错误）。
- **`[2bb1f85]` 修复融合 MoE 自动调优正确性**: 过滤掉会导致错误结果的 `clusterDimZ >= 1` 的 tactic，并添加了穷举测试。这**确保了融合 MoE 自动调优结果的正确性**。
- **`[435826a]` 新增 Allreduce + Norm + FP8 量化融合**: 实现了 Allreduce、LayerNorm 和 Per-token Group FP8 量化的融合内核。这**减少了显存带宽消耗和内核启动开销**，是面向 DeepGemm 等需要 FP8 激活的模型的关键优化，已在 vLLM 中集成测试。
- **`[5345bf5]` 新增 Grouped MM 算子**: 增加了 `grouped_mm_bf16`, `grouped_mm_fp8` 等分组矩阵乘法算子，并提供了 cuDNN 后端实现。这**扩展了 FlashInfer 的算子库**，为 MoE 层提供了更灵活、高性能的矩阵乘法选择。
- **`[ae3e530]` 修复多实例随机种子冲突**: 修复了在同一台机器上运行多个 vLLM 实例时，因使用相同随机种子导致 IPC 套接字文件路径冲突的问题。这**提升了项目在多进程部署场景下的稳定性**。

### 3. 对项目的影响和潜在意义

- **提升大型模型推理的可靠性和性能**: 修复 MLA 整数溢出和 MoE 自动调优器问题，直接提升了 DeepSeek-V3 等前沿模型在长上下文场景下的**正确性和性能**。
- **扩展对最新模型架构的支持**: 新增的 Sigmoid 路由、Attention Sink 和 FP8 量化融合等功能，使 FlashInfer 能更好地支持**新兴的 MoE 和长上下文模型**。
- **增强项目的健壮性和易用性**: 修复构建系统、下载重试和多实例冲突等问题，降低了用户在不同环境下的使用门槛，提升了**项目的生产就绪度**。
-

## 详细提交记录

### [f080fd3](https://github.com/flashinfer-ai/flashinfer/commit/f080fd3e3768a001d9a8a8acb19d3902082bded5)

- **作者**: Ka-Hyun Nam
- **时间**: 2026-05-06T23:14:21Z
- **提交信息**: Fix: skip git submodule update when submodules are already populated (#3248)

<!-- .github/pull_request_template.md -->

## 📌 Description

The unconditional git submodule update in jit-cache build_backend.py
fails in Docker environments where .git is a submodule-style gitfile
pointing to a parent repo not in the Docker context.

Check if submodule directories are already populated before attempting
git submodule update. Only raise an error if git fails AND the required
submodule contents are actually missing.

Fixes #3241

## 🔍 Related Issues

[<!-- Link any related issues here
-->](https://github.com/flashinfer-ai/flashinfer/issues/3241)

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

* **Bug Fixes**
* Improved error handling in submodule initialization with enhanced
diagnostics and clearer error messages to help troubleshoot build
failures and missing dependencies.

* **Chores**
* Optimized build backend to conditionally initialize submodules only
when necessary, reducing build time and eliminating redundant operations
for faster builds.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Cursor <cursoragent@cursor.com>

### [e6ac7cc](https://github.com/flashinfer-ai/flashinfer/commit/e6ac7cc25eb8b5f138b39bd58700639d3d888e51)

- **作者**: Lee Nau
- **时间**: 2026-05-06T22:09:47Z
- **提交信息**: fix(cute_dsl/moe): make autotuner bucket configuration adapt to runtime input (#3216)

<!-- .github/pull_request_template.md -->

## 📌 Description

The autotuner's `DynamicTensorSpec` in
`flashinfer/fused_moe/cute_dsl/tuner.py` declared `gen_tuning_buckets`
as the pre-computed tuple `get_hybrid_num_tokens_buckets(8192)` and
`map_to_tuning_buckets` as `lambda x: map_to_hybrid_bucket(x,8192)`. The
hardcoded 8192 cap silently clamped any runtime workload larger than
that to the 8192-bucket's cached tactic — at DeepSeek-V3 prefill
(N=16384) fi profiled at half the per-expert workload and used a tactic
optimized for the wrong shape.

This PR replaces the pre-computed tuple with the bare callable form
(`get_hybrid_num_tokens_buckets`) and switches the mapper to the
uncapped variant `map_to_hybrid_bucket_uncapped` (added alongside the
hybrid-bucket scheme for exactly this case). The autotuner now invokes
them with the actual input dim at autotune time, matching TRT-LLM's
pattern at `cute_dsl_custom_ops.py:2390-2391` and flashinfer's own
pattern at `gemm/gemm_base.py:_FP8_GEMM_SM100_TUNING_CONFIG`.

## 🔍 Related Issues

https://github.com/flashinfer-ai/flashinfer/pull/3171
https://github.com/flashinfer-ai/flashinfer/pull/3198
https://github.com/flashinfer-ai/flashinfer/pull/3115

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

* **Bug Fixes**
* MoE autotuner now uses uncapped dynamic hybrid bucket mapping instead
of a fixed-bounded set, improving adaptation to varying input token
sizes.

* **Tests**
* Added offline tests validating autotuner bucket configuration: dynamic
bucket generation, responsiveness to input size, monotonic mapping
behavior, large-input scaling, and alignment with expected power-of-2
bucket values.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 4.7 (1M context) <noreply@anthropic.com>

### [cb44e7d](https://github.com/flashinfer-ai/flashinfer/commit/cb44e7df429cee12330e799ca91e510b9eae04f6)

- **作者**: Alex Yang
- **时间**: 2026-05-06T18:26:45Z
- **提交信息**: bump version to 0.6.11 (#3245)

## Description

Bump version to 0.6.11 for release.

## Related Issues (Gated-by PRs)


https://github.com/flashinfer-ai/flashinfer/issues?q=is%3Aopen+label%3Av0.6.11

## Reviewer Notes

**API changes review**

API changes since v0.6.10

```diff
$ git diff v0.6.10..main -- "*.py" | grep -B5 -A20 "@flashinfer_api"
+# the returned tensor, any caller-side ``view`` / ``slice`` / ``clone`` that
+# drops the original tensor would silently free the workspace under the kernel.
+_workspace_keepalive: Dict[int, MnnvlMemory] = {}
+
+
 @flashinfer_api
 def decode_cp_a2a_workspace_size(cp_size: int) -> int:
     """Return the workspace size **in bytes** per rank for the given CP group size.
@@ -119,33 +133,24 @@ def decode_cp_a2a_workspace_size(cp_size: int) -> int:
 
 
 @flashinfer_api
-def decode_cp_a2a_allocate_workspace(
-    cp_size: int,
-    cp_rank: int,
+def decode_cp_a2a_allocate_mnnvl_workspace(
+    mapping: Mapping,
     *,
-    mapping: Optional[Mapping] = None,
     mnnvl_config: Optional[MnnvlConfig] = None,
 ) -> torch.Tensor:
-    """Allocate a workspace tensor of shape ``[cp_size, ws_elems_per_rank]``.
+    """Allocate an MNNVL-backed workspace of shape ``[cp_size, ws_elems_per_rank]``.
+
+    The DCP A2A kernel requires a single unified VA spanning all CP ranks
+    (see module docstring), so workspace allocation must go through MNNVL
+    fabric memory. This function is the only supported allocator.
 
     After allocation, call :func:`decode_cp_a2a_init_workspace` followed by a
     cross-rank barrier before the first :func:`decode_cp_a2a_alltoall` call.
 
-    Two allocation modes:
--
+        list(workspace.stride()),
+    )
+    return workspace
 
 
 @flashinfer_api
@@ -197,7 +198,7 @@ def decode_cp_a2a_init_workspace(
 
     Args:
         workspace: ``[cp_size, ws_elems_per_rank]`` int64 tensor from
-            :func:`decode_cp_a2a_allocate_workspace`.
+            :func:`decode_cp_a2a_allocate_mnnvl_workspace`.
         cp_rank: This rank's position in the CP group.
         cp_size: Context-parallel group size.
     """
@@ -229,7 +230,7 @@ def decode_cp_a2a_alltoall(
         softmax_stats: ``[..., cp_size, S]`` — float32, ``S >= 2`` and even.
             Batch dimensions must match ``partial_o``.
         workspace: ``[cp_size, ws_elems_per_rank]`` int64 tensor from
-            :func:`decode_cp_a2a_allocate_workspace`, already initialized.
+            :func:`decode_cp_a2a_allocate_mnnvl_workspace`, already initialized.
         cp_rank: This rank's position in the CP group.
         cp_size: Context-parallel group size.
         enable_pdl: Enable Programmatic Dependent Launch (SM90+).
@@ -249,7 +250,7 @@ def decode_cp_a2a_alltoall(
 
--
+            )
+    return True
+
+
+@backend_requirement({}, common_check=_check_grouped_mm_bf16)
+@flashinfer_api
+def grouped_mm_bf16(
+    a: torch.Tensor,
+    b: torch.Tensor,
+    m_indptr: torch.Tensor,
+    out: Optional[torch.Tensor] = None,
+    out_dtype: torch.dtype = torch.bfloat16,
+    backend: str = "cudnn",
+    tactic: int = -1,
+) -> torch.Tensor:
+    r"""Grouped matrix multiplication with BF16/FP16 data types (cuDNN MOE backend).
+
+    Performs a grouped GEMM across experts, as used in Mixture-of-Experts layers.
+    Mirrors :func:`flashinfer.mm_bf16` but for expert-partitioned inputs.
+
+    .. math::
+
+        \text{out}[\text{start}:\text{end}] = a[\text{start}:\text{end}] \times b[e]^T
+        \quad \text{for each expert } e
+
+    where ``start, end = m_indptr[e], m_indptr[e+1]``.
--
+            )
+    return True
+
+
+@backend_requirement({}, common_check=_check_grouped_mm_fp8)
+@flashinfer_api
+def grouped_mm_fp8(
+    a: torch.Tensor,
+    b: torch.Tensor,
+    m_indptr: torch.Tensor,
+    alpha: Optional[torch.Tensor] = None,
+    out: Optional[torch.Tensor] = None,
+    out_dtype: torch.dtype = torch.bfloat16,
+    backend: str = "cudnn",
+    tactic: int = -1,
+) -> torch.Tensor:
+    r"""Grouped matrix multiplication with FP8 data types (cuDNN MOE backend).
+
+    Performs a grouped GEMM across experts, as used in Mixture-of-Experts layers.
+    Mirrors :func:`flashinfer.mm_fp8` but for expert-partitioned inputs.
+
+    .. math::
+
+        \text{out}[\text{start}:\text{end}] = a[\text{start}:\text{end}] \times b[e]^T
+        \quad \text{for each expert } e
+
--
+            )
+    return True
+
+
+@backend_requirement({}, common_check=_check_grouped_mm_mxfp8)
+@flashinfer_api
+def grouped_mm_mxfp8(
+    a: torch.Tensor,
+    b: torch.Tensor,
+    a_descale: torch.Tensor,
+    b_descale: torch.Tensor,
+    m_indptr: torch.Tensor,
+    out: Optional[torch.Tensor] = None,
+    out_dtype: torch.dtype = torch.bfloat16,
+    backend: str = "cudnn",
+    tactic: int = -1,
+) -> torch.Tensor:
+    r"""Grouped matrix multiplication with MXFP8 data types (cuDNN MOE backend).
+
+    Performs a grouped GEMM across experts, as used in Mixture-of-Experts layers.
+    Mirrors :func:`flashinfer.mm_mxfp8` but for expert-partitioned inputs.
+
+    .. math::
+
+        \text{out}[\text{start}:\text{end}] = a[\text{start}:\text{end}] \times b[e]^T
+        \quad \text{for each expert } e
--
+
+    return True
+
+
+@backend_requirement({}, common_check=_check_grouped_mm_fp4)
+@flashinfer_api
+def grouped_mm_fp4(
+    a: torch.Tensor,
+    b: torch.Tensor,
+    a_descale: torch.Tensor,
+    b_descale: torch.Tensor,
+    m_indptr: torch.Tensor,
+    alpha: Optional[torch.Tensor] = None,
+    out: Optional[torch.Tensor] = None,
+    out_dtype: torch.dtype = torch.bfloat16,
+    block_size: int = 16,
+    backend: str = "cudnn",
+    tactic: int = -1,
+) -> torch.Tensor:
+    r"""Grouped matrix multiplication with FP4 data types (cuDNN MOE backend).
+
+    Performs a grouped GEMM across experts, as used in Mixture-of-Experts layers.
+    Mirrors :func:`flashinfer.mm_fp4` but for expert-partitioned inputs.
+
+    .. math::
+
--
+
+def _dit_ln_empty_f32(device: torch.device) -> torch.Tensor:
+    return torch.empty(0, dtype=torch.float32, device=device)
+
+
+@flashinfer_api
+def fused_dit_gate_residual_layernorm_gamma_beta(
+    input: torch.Tensor,
+    residual: torch.Tensor,
+    gate: torch.Tensor,
+    gamma: torch.Tensor,
+    beta: torch.Tensor,
+    *,
+    gate_bias: Optional[torch.Tensor] = None,
+    epsilon: float = 1e-6,
+    use_nvfp4: bool = False,
+    use_mxfp8: bool = False,
+    global_scaling_factor: Optional[torch.Tensor] = None,
+    input_global_scaling_factor: Optional[torch.Tensor] = None,
+    residual_out: Optional[torch.Tensor] = None,
+    norm_out: Optional[torch.Tensor] = None,
+    sf_out: Optional[torch.Tensor] = None,
+) -> Tuple[torch.Tensor, torch.Tensor]:
+    r"""Fused gate + residual + LayerNorm(gamma, beta) for DIT self-attention.
+
+    Computes in a single kernel:
--
+    )
+
+    return residual_out, norm_out
+
+
+@flashinfer_api
+def fused_dit_gate_residual_layernorm_scale_shift(
+    input: torch.Tensor,
+    residual: torch.Tensor,
+    gate: torch.Tensor,
+    scale: torch.Tensor,
+    shift: torch.Tensor,
+    *,
+    gate_bias: Optional[torch.Tensor] = None,
+    scale_bias: Optional[torch.Tensor] = None,
+    shift_bias: Optional[torch.Tensor] = None,
+    epsilon: float = 1e-6,
+    use_nvfp4: bool = False,
+    use_mxfp8: bool = False,
+    global_scaling_factor: Optional[torch.Tensor] = None,
+    input_global_scaling_factor: Optional[torch.Tensor] = None,
+    residual_out: Optional[torch.Tensor] = None,
+    norm_out: Optional[torch.Tensor] = None,
+    sf_out: Optional[torch.Tensor] = None,
+) -> Tuple[torch.Tensor, torch.Tensor]:
+    r"""Fused gate + residual + LayerNorm + scale/shift for DIT self-attention.
--
+    )
+
+    return residual_out, norm_out
+
+
+@flashinfer_api
+def fused_dit_residual_layernorm_scale_shift(
+    input: torch.Tensor,
+    scale: torch.Tensor,
+    shift: torch.Tensor,
+    *,
+    residual: Optional[torch.Tensor] = None,
+    scale_bias: Optional[torch.Tensor] = None,
+    shift_bias: Optional[torch.Tensor] = None,
+    epsilon: float = 1e-6,
+    use_nvfp4: bool = False,
+    use_mxfp8: bool = False,
+    global_scaling_factor: Optional[torch.Tensor] = None,
+    input_global_scaling_factor: Optional[torch.Tensor] = None,
+    residual_out: Optional[torch.Tensor] = None,
+    norm_out: Optional[torch.Tensor] = None,
+    sf_out: Optional[torch.Tensor] = None,
+) -> Tuple[torch.Tensor, torch.Tensor]:
+    r"""Fused residual + LayerNorm + scale/shift for DIT self-attention.
+
+    Computes in a single kernel:
```


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Chores**
  * Version bumped to 0.6.11

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: aleozlx <aleozlx@users.noreply.github.com>

### [d885b71](https://github.com/flashinfer-ai/flashinfer/commit/d885b71f334d6086c6a9ff94c5e798cdbcdfac66)

- **作者**: Qi Zhang (qizh)
- **时间**: 2026-05-06T16:46:24Z
- **提交信息**: fix(mla): widen page index to int64_t to avoid 32-bit overflow (#3136)

<!-- .github/pull_request_template.md -->

## 📌 Description
In the MLA decode/prefill KV load path, `indices[q] * ckv_stride_page`
was computed in 32-bit because `IdType` is `int32_t` and `*_stride_page`
is `uint32_t`; the product wraps modulo 2^32 before any widening to
`int64_t` (Hopper) or pointer arithmetic (FA2). For large page pools
(e.g. page_idx ~1M with page_size=32, kv_lora_rank=512, stride=16384)
the true product exceeds 2^32 and the kernel reads the wrong page,
producing all-zero outputs. Cast the selected page index to `int64_t` at
all three sites (mla.cuh NUM_MMA_KV==1 and !=1 branches, and
mla_hopper.cuh prefetch_offset) so the multiply executes in 64-bit.

## 🔍 Related Issues

https://github.com/flashinfer-ai/flashinfer/issues/3130

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [ ] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [ ] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Fixed integer overflow in page-index arithmetic that could select the
wrong memory page for very large attention KV caches, improving
reliability and correctness for large-context workloads.

* **Tests**
* Added a regression test that reproduces the page-index overflow case
and verifies correct outputs for large KV cache scenarios, with gating
to ensure it runs only when sufficient GPU support and memory are
available.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 4.7 (1M context) <noreply@anthropic.com>

### [89af11c](https://github.com/flashinfer-ai/flashinfer/commit/89af11c5cb7770b7f22988131444114d93f5e6f4)

- **作者**: Li Min
- **时间**: 2026-05-06T16:44:06Z
- **提交信息**: cute-dsl fmha prefill (cubin integration): remove front-padding, add attention_sink, and pdl support (#3181)

Update cute-dsl fmha prefill (cubin integration) by removing
front-pading, and add support for attention_sink and pdl.

Runtime API changes (flashinfer/attention/cute_dsl/fmha.py):
- Drop front-padding requirement and remove the docstring section about
it.
- Reshape q/k/v/o tensors from 4D (B, S, H, D) to 5D matching kernel
docstring: q/o: (1, total, H_k, H_q//H_k, D); k/v: (1, total, H_k, 1, D)
- LSE reshaped to 4D (1, total_q, H_k, H_q//H_k).
- TVM-FFI: pass torch.Tensors directly (not data_ptr()); drop trailing
q_tensor env-stream-detection arg (removed in new DKG).
- Add attention_sinks parameter and enable_sink to variant lookup; pass
sink tensor through to kernel.
- CuTe native ABI path updated to 5D from_dlpack with leading_dim=4.

flashinfer/prefill.py:
- Remove warnings about cute-dsl not supporting PDL/sinks; pass
attention_sinks through to cute_dsl_fmha_ragged_prefill.
- Drop front-padding caveat from trtllm_ragged_attention_deepseek
docstring.

Benchmark / test cleanup:
- benchmarks/routines/attention.py: remove front_pad_q/front_pad_kv
allocation and slicing for q/k/v and output.
- tests/attention/test_trtllm_gen_attention.py: drop the `if backend ==
"cute-dsl"` front-padding branches in test_trtllm_gen_prefill (bf16) and
test_trtllm_gen_prefill_fp8.
- Add enable_sink parametrize to test_trtllm_gen_prefill, with
sink_attention_unified reference for sink case. Currently parametrized
to [False] only with TODO, pending DKG kernel sink semantics fix (kernel
adds raw sink to row_sum without exp/max-shift, mismatching trtllm-gen
logit-style sink).

Verified: 432/432 non-sink cute-dsl tests pass; perf 1.07-1.13x vs
trtllm-native on FP8 h192 (no regression vs prior cute-dsl baseline).

**UT cwd：**

`python -m pytest
tests/attention/test_trtllm_gen_attention.py::test_trtllm_gen_prefill -k
"cute-dsl"`


**benchmark results:**

**Cubin commit:** `801e770219613fbf088bc074c414732b26cc550d`
**Date:** 2026-04-28
**Backends:** `cute-dsl` vs `trtllm-native`
**Config:** causal, num_qo_heads=128, num_kv_heads=128, head_dim_vo=128
**Timing:** CUPTI + CUDA Graph, num_iters=30, dry_run_iters=5
**Cubin source:** public artifactory (downloaded fresh, checksums
verified)

---

 **head_dim_qk = 192 (FP8 e4m3 only — BF16 unsupported at D=192**)

| Shape (B, S_qo, S_kv) | cute-dsl (ms / TFLOPS) | trtllm-native (ms /
TFLOPS) | Speedup |
|---|---|---|---|
| 1, 8192, 8192   | 1.515 / 1814 | 1.628 / 1688 | 1.07× |
| 1, 8192, 32768  | 8.582 / 2242 | 9.546 / 2016 | 1.11× |
| 1, 8192, 65536  | 18.022 / 2288 | 20.025 / 2059 | 1.11× |
| 4, 512, 81920   | 6.585 / 2081 | 7.454 / 1838 | 1.13× |
| 4, 1024, 81920  | 12.481 / 2189 | 14.051 / 1944 | 1.13× |

**Result:** cute-dsl wins all 5 shapes (1.07×–1.13×).

---

**head_dim_qk = 128**

**FP8 e4m3**

| Shape (B, S_qo, S_kv) | cute-dsl (ms / TFLOPS) | trtllm-native (ms /
TFLOPS) | Speedup |
|---|---|---|---|
| 1, 8192, 8192   | 1.452 / 1515 | 1.568 / 1403 | 1.08× |
| 1, 8192, 32768  | 7.745 / 1988 | 9.058 / 1699 | 1.17× |
| 1, 8192, 65536  | 16.209 / 2035 | 18.665 / 1767 | 1.15× |
| 4, 512, 81920   | 5.846 / 1875 | 6.504 / 1685 | 1.11× |
| 4, 1024, 81920  | 11.176 / 1955 | 12.486 / 1750 | 1.12× |

**Result:** cute-dsl wins all 5 shapes (1.08×–1.17×).

**BF16**

| Shape (B, S_qo, S_kv) | cute-dsl (ms / TFLOPS) | trtllm-native (ms /
TFLOPS) | Speedup |
|---|---|---|---|
| 1, 8192, 8192   | 1.702 / 1292 | 1.778 / 1237 | 1.04× |
| 1, 8192, 32768  | 10.192 / 1510 | 11.117 / 1385 | 1.09× |
| 1, 8192, 65536  | 21.898 / 1506 | 23.266 / 1418 | 1.06× |
| 4, 512, 81920   | 8.721 / 1257 | 8.706 / 1259 | 1.00× |
| 4, 1024, 81920  | 16.114 / 1356 | 16.278 / 1342 | 1.01× |

**Result:** cute-dsl wins on batch=1 shapes (1.04×–1.09×); parity on
batch=4.


<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

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

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Optional attention-sink and PDL support for ragged attention prefill
and kernel selection; APIs now accept sink/PDL options.

* **Bug Fixes**
* Removed misleading warnings about sinks and fixed conditional
LSE/output comparisons for ragged flows.

* **Chores**
* Reduced memory usage by eliminating front-padding; tensors and outputs
allocate exact ragged sizes.

* **Tests**
* Expanded coverage for sink/PDL modes and simplified FP8 and output
verification logic.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 4.7 (1M context) <noreply@anthropic.com>

### [417e59f](https://github.com/flashinfer-ai/flashinfer/commit/417e59ff337c02da4bde17240b77ebecf52d7a85)

- **作者**: EdalatiAli
- **时间**: 2026-05-06T14:08:41Z
- **提交信息**: Support Sigmoid (sigmoid+topk) routing function (#2869)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

Depends on #2803 .

This PR adds `RoutingMethodType.Sigmoid` to support a routing function
that applies sigmoid before topk (without renormalization) to be used by
MoE layers that use this routing function.

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

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
  * Added a Sigmoid routing strategy for Mixture-of-Experts.

* **Behavior Change**
  * Increased allowed top_k from 10 to 32 for applicable routing modes.

* **Documentation**
* Updated docs to include Sigmoid and SigmoidRenorm routing
descriptions.

* **Tests**
* Added tests validating Sigmoid routing across implementations and
configurations.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: EdalatiAli <aliedalati@cohere.com>

### [979644f](https://github.com/flashinfer-ai/flashinfer/commit/979644f19a19cc12aa5ed3fad3b5002ab460c2c5)

- **作者**: Lee Nau
- **时间**: 2026-05-06T12:54:41Z
- **提交信息**: cute_dsl/moe: drop redundant Python-side moe_sort buffer init (#3226)

<!-- .github/pull_request_template.md -->

## 📌 Description

Aligns flashinfer's `moe_sort` wrapper with the trt-llm thop allocation
pattern (`torch::empty(...)` with no Python-side init).

Removed from the preallocated-buffer (CUDA-graph) path:

- `expanded_idx_to_permuted_idx.fill_(-1)` (and the stale "kernel
expects this" comment)
- `permuted_idx_to_expanded_idx.zero_()`
- `total_num_padded_tokens_tensor.zero_()`
- `num_non_exiting_tiles.zero_()`

Aligned the else-branch allocations (functional-API path with no
preallocated buffer) from `torch.full((..., -1), ...)` and
`torch.zeros(...)` to `torch.empty(...)`. The `expert_counts` buffer
(used for >1024-token routing) was changed from `torch.zeros` to
`torch.empty` since the vendored kernel zeros it internally via
`launchInitExpertCounts` before reading.

The routing kernel `runPostTopKPipeline` (in
`csrc/fused_moe/trtllm_backend/trtllm_fused_moe_routing_common.cu` on
the fi side) writes every entry of all four output buffers itself —
including writing `-1` to masked slots of
`expanded_idx_to_permuted_idx` at EP > 1, and writing valid permuted
indices to all unmasked slots. The Python-side init was redundant
defensive programming; trt-llm's thop has been running this pattern in
production with `torch::empty(...)` and no Python init.

4 fewer Python-launched FillFunctor kernels per `moe_sort` call when
buffers are preallocated by `CuteDslMoEWrapper`.

## 🔍 Related Issues

https://github.com/flashinfer-ai/flashinfer/pull/2811
https://github.com/flashinfer-ai/flashinfer/pull/2803

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

* **Tests**
* Added a CUDA-graph regression test to ensure MoE routing buffers are
fully overwritten and outputs are numerically stable (no NaNs/Infs)
across multiple configurations.

* **Improvements**
* Optimized MoE routing memory allocation to reduce unnecessary
initialization and improve performance.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 4.7 (1M context) <noreply@anthropic.com>

### [55a9eea](https://github.com/flashinfer-ai/flashinfer/commit/55a9eea3517704d7958bc12a863722c696f7e22d)

- **作者**: Paul Luh
- **时间**: 2026-05-06T11:22:39Z
- **提交信息**: fix: add jitter to cubin download backoff (#3169)

The retry loop in download_file used a fully deterministic exponential
backoff (5s, 10s, 20s). Combined with 4 parallel download threads
sharing one session and many concurrent CI runners, this produces
lockstep retries that hammer the same CDN edge — a plausible contributor
to the intermittent 403s reported in #3164.

Switch to full jitter (uniform[0, base*2^(attempt-1)]) to spread retries
across the window and break the thundering-herd pattern.

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

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

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Improved download retry logic to use jittered exponential backoff for
more resilient recovery from transient failures.
* Clarified retry termination so reported attempt counts match actual
behavior.
* Randomized retry delays are now logged to aid troubleshooting and
visibility.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 4.7 (1M context) <noreply@anthropic.com>
Co-authored-by: Alex Yang <aleyang@nvidia.com>

### [2bb1f85](https://github.com/flashinfer-ai/flashinfer/commit/2bb1f857f0467f47b7ed5c0fc2e104a710ae89fa)

- **作者**: Wei Zhao
- **时间**: 2026-05-06T10:11:01Z
- **提交信息**: fix: fused MoE autotuning correctness issues by filtering clusterDimZ (#3227)

## 📌 Description
There has been correctness issues observed using fused MoE autotuning.
Investigating shows tactics using `clusterDimZ >= 1` produces incorrect
outputs. See https://github.com/flashinfer-ai/flashinfer/issues/3197

This PR changes the following:
- only allow tactics with `clusterDimZ == 1`
- add test that enumerates all tactics in fp8 and fp4 fused MoE and
validate the correctness
- fix the topk_ids initialization for autotuning for EP

Before the fix, `tests/moe/test_trtllm_gen_moe_autotune_tactics.py`
fails.
```
=========================== short test summary info ============================
FAILED tests/moe/test_trtllm_gen_moe_autotune_tactics.py::test_trtllm_fp4_routed_moe_all_tactics_correctness[4-128-3072-4096-128-NvFP4xNvFP4]
FAILED tests/moe/test_trtllm_gen_moe_autotune_tactics.py::test_trtllm_fp4_routed_moe_all_tactics_correctness[4-128-3072-4096-128-MxFP4xMxFP8]
FAILED tests/moe/test_trtllm_gen_moe_autotune_tactics.py::test_trtllm_fp8_routed_moe_all_tactics_correctness[4-128-3072-4096-128-MxFp8]
=================== 3 failed, 2 passed in 131.69s (0:02:11) ====================
```

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

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Autotuning now aligns routing IDs with the full expert index space and
skips unsupported kernel configurations during tuning to prevent
incorrect tactic selection and runtime mismatches.

* **Tests**
* Added exhaustive per-tactic correctness tests for routed
Mixture-of-Experts kernels across FP4 and FP8 quantization modes; tests
validate numerical fidelity, determinism, and autotuner cache behavior.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [435826a](https://github.com/flashinfer-ai/flashinfer/commit/435826ab05a3332209d138004a693dbc1003d6b8)

- **作者**: Wei Zhao
- **时间**: 2026-05-06T09:58:50Z
- **提交信息**: Support Allreduce + Norm + Per-token Group Fp8 Quant Fusion (#3059)

<!-- .github/pull_request_template.md -->

## 📌 Description
This PR adds support for allreduce + Norm + Per-token Group Fp8 Quant
Fusion, which quantizes activation for DeepGemm gemm
(`per_token_group_quant_fp8_packed_for_deepgemm` in vllm)
<img width="1021" height="240" alt="Screenshot 2026-04-13 at 9 44 49 PM"
src="https://github.com/user-attachments/assets/496d831f-7131-4cff-8ae2-0e91e259db33"
/>

With fusion:
<img width="790" height="144" alt="Screenshot 2026-04-13 at 9 45 56 PM"
src="https://github.com/user-attachments/assets/d4f0149b-e87d-460c-81f8-74c0d6ffea1c"
/>

Tested Integration in vllm:
https://github.com/vllm-project/vllm/pull/39758

From testing, the values of `quant_out` and `norm_out` from the fused
kernel match exactly as applying
`per_token_group_quant_fp8_packed_for_deepgemm` on the `norm_out` of the
fused kernel.

E2E eval:
```
vllm serve MiniMaxAI/MiniMax-M2.5 --trust-remote-code --tensor-parallel-size 2

|Tasks|Version|     Filter     |n-shot|  Metric   |   |Value |   |Stderr|
|-----|------:|----------------|-----:|-----------|---|-----:|---|-----:|
|gsm8k|      3|flexible-extract|     5|exact_match|↑  |0.9257|±  |0.0072|
|     |       |strict-match    |     5|exact_match|↑  |0.9227|±  |0.0074|
```

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

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added two fused all-reduce + residual + RMSNorm modes with
per-token-group FP8 packed-scale quantization.
* Added optional control parameter block_quant_group_size to specify
group sizes; runtime validation enforces allowed sizes and packed-scale
shape/stride/dtype and alignment constraints.
* Outputs now include TMA-aligned packed scale storage with explicit
padding semantics.

* **Tests**
* New distributed GPU correctness tests verifying packed-scale layout,
padding behavior, and FP8 quantized outputs.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 4.6 (1M context) <noreply@anthropic.com>
Co-authored-by: root <root@bia0038.bia.clusters.nvidia.com>

### [5345bf5](https://github.com/flashinfer-ai/flashinfer/commit/5345bf5ef891bc91d12e6311b22fb7c971aae1a2)

- **作者**: yanqinz2
- **时间**: 2026-05-06T09:57:55Z
- **提交信息**: add_grouped_mm_operation_directory (#3052)

<!-- .github/pull_request_template.md -->

## 📌 Description

Add a new grouped_mm operation class and apis with cudnn backend
implementation and tests
grouped_mm_bf16, grouped_mm_fp8, grouped_mm_mxfp8, grouped_mm_fp4

## 🔍 Related Issues

<!-- Link any related issues here -->

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

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added MoE-friendly grouped matrix-multiplication operators (BF16, FP8,
MXFP8, FP4) with flexible output dtypes, optional scaling, and
block-scale support; cuDNN-backed execution and compatibility gating.

* **Tests**
* Added comprehensive CUDA/cuDNN-gated test suites covering correctness,
quantization/block-scale paths, error handling, output-buffer reuse, and
cached-graph determinism.

* **Chores**
* Updated CI labeling and CODEOWNERS to include grouped-mm areas and
top-level package exports.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yanqin Zhai <yanqinz@nvidia.com>

### [ae3e530](https://github.com/flashinfer-ai/flashinfer/commit/ae3e5306ffcaf5546dc40305ce96c6a75d6dc572)

- **作者**: huxiaolong
- **时间**: 2026-05-06T09:56:03Z
- **提交信息**: Fix multi-instances using same random seed (#3102)

<!-- .github/pull_request_template.md -->

## 📌 Description

When running two vLLM instances on the same machine at the same time,
one instance will print the following error.
```
allreduce_rms_fusion.py:779] Failed to initialize FlashInfer All Reduce workspace: [Errno 98] Address already in use. AllReduce fusion pass will be disabled.
```

The reason for this is that both instances create the same random seed,
so the `IpcSocket` uses the same socket file path.



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

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Refactor**
* Improved inter-process communication initialization with enhanced
random operation ID generation.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-05-07
**监控日期**: 2026-05-06
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3453
- **最后更新**: 2026-05-07T09:00:05Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-05-07
**监控日期**: 2026-05-06
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 33570
- **最后更新**: 2026-05-07T12:13:32Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 4
- **主要提交者**: Dhruv Nair, Akshan Krithick, hf-security-analysis[bot]

## AI分析总结

好的，根据您提供的 `huggingface/diffusers` 仓库的README摘要和昨日提交记录，以下是分析总结：

### 1. 主要更新类型

*   **Bug修复与代码审查跟进**：提交 `84006ed` 主要针对 `ernie-image` 功能的代码审查意见进行修复和改进。
*   **安全修复**：提交 `9dad53e` 修复了CI/CD工作流中的一个安全漏洞。
*   **性能优化**：提交 `dc55124` 优化了DreamBooth训练脚本中数据加载的性能，特别是缓存对齐问题。
*   **CI/CD质量改进**：提交 `e16719a` 对PR大小标签器进行了质量改进。

### 2. 关键变更点及其与项目整体方向的关系

*   **`ernie-image` 功能完善**：`84006ed` 修复了 `ernie-image` pipeline中的多个问题，包括：
    *   使用更具体的模型类型（`Mistral3Model` / `Ministral3ForCausalLM`）。
    *   修复了 `bn_mean`/`bn_std` 的数据类型转换问题。
    *   统一了 `VaeImageProcessor.postprocess` 的使用。
    *   **关系**：这直接关系到 `diffusers` 项目支持更多样化、更复杂的图像生成模型（如ERNIE-ViLG系列）的目标，确保新功能的稳定性和代码质量。
*   **安全加固**：`9dad53e` 修复了 `pr_labeler.yml` 工作流中的漏洞。
    *   **关系**：这体现了项目对基础设施安全的重视，确保开源协作流程的安全性，是项目长期健康发展的基础。
*   **DreamBooth训练优化**：`dc55124` 修复了 `BucketBatchSampler` 的缓存对齐问题，并优化了批次打乱逻辑。
    *   **关系**：DreamBooth是 `diffusers` 的核心功能之一，用于个性化图像生成。此优化直接提升了用户在使用DreamBooth进行微调时的训练效率和稳定性，符合项目“让扩散模型更易用”的宗旨。
*   **CI流程改进**：`e16719a` 改进了PR大小标签器，这是一个开发者体验（DevEx）改进。
    *   **关系**：这有助于维护者更高效地管理PR，提升项目协作效率，是项目持续集成流程优化的体现。

### 3. 对项目的影响和潜在意义

*   **提升新功能可靠性**：`ernie-image` 的修复意味着该功能更接近稳定发布，为后续用户使用更先进的文生图模型铺平了道路。
*   **增强社区信任**：及时修复CI/CD安全漏洞，保护了贡献者和维护者的安全，增强了社区对项目的信任。
*   **改善核心用户体验**：DreamBooth的性能优化直接让大量使用该功能的用户受益，减少训练时间，提高资源利用率。
*   **提升开发效率**：CI流程的改进虽然对最终用户透明，但能显著提升内部开发和社区贡献的效率。

### 4. 值得关注的技术点

*   **类型安全与精度**：`84006ed` 中明确使用具体模型类型（而非通用类型）以及将 `bn_mean`/`bn_std` 强制转换为 `latents` 的数据类型，体现了对数值精度和类型安全的重视，这在模型推理中至关重要。
*   **数据加载优化**：`dc55124` 中的 `BucketBatchSampler` 缓存对齐和打乱优化，是典型的深度学习训练性能优化技巧，对于处理变长数据（如图片）的批处理非常关键。
*   **安全最佳实践**：`9dad53e` 提醒我们，即使是自动化工作流脚本（如YAML）也可能存在安全风险，需要定期审查和修复。

### 5. 基于项目背景，这些提交如何影响项目发展

根据README，`diffusers` 的目标是成为最先进扩散模型的首选库，提供模块化、易用的工具。

*   **`ernie-image` 修复**：直接支持了更先进的模型架构，丰富了 `diffusers` 的模型生态，使其保持技术前沿性。
*   **DreamBooth优化**：强化了项目在“个性化/微调”这一核心应用场景上的竞争力，让用户能更高效地创造定制化内容，符合“易用”和“实用”的目标。
*   **安全与CI改进**：这些“幕后”工作虽然不直接增加功能，但确保了项目能够稳定、安全地发展，为引入更多复杂功能（如README中提到的各种pipeline和调度器）提供了坚实的基础。

**总结**：昨日的更新是一次典型的“巩固与优化”型提交。在持续引入新模型（如 `ernie-image`）的同时，项目团队也投入精力修复核心功能（DreamBooth）的性能问题，并加固基础设施安全。这体现了 `diffusers` 项目在追求功能丰富性的同时，也高度重视稳定性、安全性和用户体验的平衡发展。

## 详细提交记录

### [84006ed](https://github.com/huggingface/diffusers/commit/84006ed923371ceff0cf48f5d786d83c3e17dc2e)

- **作者**: Akshan Krithick
- **时间**: 2026-05-06T19:05:13Z
- **提交信息**: Address ernie-image review findings #13577 (#13663)

* Address ernie-image review findings #13577

* Use concrete Mistral3Model / Ministral3ForCausalLM types

* Cast bn_mean/bn_std to latents dtype + add TODO for hub eps

* Use VaeImageProcessor.postprocess in standard and modular ernie

* Revert "Use concrete Mistral3Model / Ministral3ForCausalLM types"

This reverts commit 2b297bf4b54deccb6cd5b82e881f29bca18259d7.

---------

Co-authored-by: YiYi Xu <yixu310@gmail.com>

### [9dad53e](https://github.com/huggingface/diffusers/commit/9dad53e0362e0e48fc481484e77772d80299b76b)

- **作者**: hf-security-analysis[bot]
- **时间**: 2026-05-06T18:08:55Z
- **提交信息**: chore: update pr_labeler.yml (#13685)

fix(security): remediate workflow vulnerability in .github/workflows/pr_labeler.yml

Co-authored-by: hf-security-analysis[bot] <265538906+hf-security-analysis[bot]@users.noreply.github.com>

### [dc55124](https://github.com/huggingface/diffusers/commit/dc55124e0405374632db55a5037d901a932a5ac4)

- **作者**: Alexey Zolotenkov
- **时间**: 2026-05-06T14:12:01Z
- **提交信息**: Fix BucketBatchSampler cache alignment in DreamBooth scripts (#13353)

* Fix bucket sampler cache alignment in DreamBooth scripts

* Shuffle precomputed DreamBooth bucket batches once

* Scope stable bucket ordering to cached DreamBooth batches

* Format DreamBooth bucket sampler updates

* Address bucket sampler cache variable naming review

---------

Co-authored-by: Linoy Tsaban <57615435+linoytsaban@users.noreply.github.com>
Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

### [e16719a](https://github.com/huggingface/diffusers/commit/e16719abb2f50528798dc1f2d872a69e183ae998)

- **作者**: Dhruv Nair
- **时间**: 2026-05-06T12:02:01Z
- **提交信息**: [CI] QOL improvement for PR size labeler (#13554)

* update

* update

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-05-07
**监控日期**: 2026-05-06
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 401
- **最后更新**: 2026-05-01T17:57:49Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-05-07
**监控日期**: 2026-05-06
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12373
- **最后更新**: 2026-05-07T12:29:14Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 2
- **主要提交者**: Hong Zhang, Zhongjie Duan

## AI分析总结

好的，这是对昨日 `modelscope/DiffSynth-Studio` 仓库提交记录的分析总结：

### 昨日更新要点总结

1.  **主要更新类型**
    *   **文档更新**：更新了文档目录。
    *   **功能更新**：更新了推理 WebUI。
    *   **Bug修复**：修复了在 DeepSpeed 环境下的 FFT 数据类型兼容性问题。

2.  **关键变更点及其与项目整体方向的关系**
    *   **文档目录更新 (`#1429`)**：优化了项目文档结构，使其更清晰易读。这直接服务于项目的**易用性**和**开发者友好性**，有助于降低新用户的入门门槛。
    *   **推理 WebUI 更新 (`#1428`)**：改进了用户交互界面，可能涉及新功能、性能优化或用户体验提升。这与项目“提供便捷的推理工具”的目标一致，旨在让用户更方便地使用模型进行创作。
    *   **DeepSpeed FFT 兼容性修复 (`#1427`)**：修复了在使用 DeepSpeed 分布式训练/推理框架时，快速傅里叶变换（FFT）操作可能出现的类型错误。这直接提升了项目在**大规模、高性能计算场景下的稳定性和兼容性**，是项目走向工程化、规模化应用的重要一步。

3.  **对项目的影响和潜在意义**
    *   **提升用户体验**：文档和 WebUI 的更新直接改善了用户的使用体验，无论是开发者还是普通用户都能从中受益。
    *   **增强系统稳定性**：DeepSpeed 兼容性修复解决了特定环境下的潜在崩溃问题，这对于需要高性能计算的专业用户至关重要，能确保他们在复杂配置下稳定运行。
    *   **巩固技术基础**：修复底层框架兼容性问题，表明项目团队在积极解决技术债务，为后续更复杂的功能开发打下坚实基础。

4.  **值得关注的技术点**
    *   **DeepSpeed 集成**：项目正在积极适配 DeepSpeed，这是一个用于大规模模型训练的优化框架。这表明 `DiffSynth-Studio` 可能正朝着支持更大模型、更高分辨率或更复杂视频生成任务的方向发展。
    *   **FFT 数据类型问题**：这是一个典型的深度学习框架兼容性问题，尤其是在混合精度训练（如 FP16/BF16）中容易出现。修复此问题体现了项目对细节和稳定性的重视。

5.  **基于项目背景，这些提交如何影响项目发展**
    *   **README 定位**：项目旨在提供一个“DiffSynth”的集成环境，强调易用性和功能。
    *   **发展影响**：
        *   **文档更新**和**WebUI 更新**直接呼应了项目“易用”的定位，通过降低使用门槛来吸引更多用户，扩大社区影响力。
        *   **DeepSpeed 兼容性修复**则体现了项目在追求“强大”功能的同时，也在夯实“稳定”的基础。这有助于项目从实验性工具向更可靠的生产级解决方案演进，吸引对性能和稳定性有高要求的专业用户（如视频创作者、AI 研究员）。
        *   总的来说，昨日的更新是典型的“内外兼修”：对外优化用户体验，对内增强系统健壮性，共同推动项目向更成熟、更专业的方向发展。

## 详细提交记录

### [b19337f](https://github.com/modelscope/DiffSynth-Studio/commit/b19337fc1bd5560138cb268ac5f9420e36b318fa)

- **作者**: Zhongjie Duan
- **时间**: 2026-05-06T08:07:04Z
- **提交信息**: update docs catalog (#1429)

### [be4490c](https://github.com/modelscope/DiffSynth-Studio/commit/be4490c3ca4ad1a77610b18a38886df426e885ea)

- **作者**: Zhongjie Duan
- **时间**: 2026-05-06T07:58:01Z
- **提交信息**: update inference webui (#1428)

### [dea7faa](https://github.com/modelscope/DiffSynth-Studio/commit/dea7faaea510b88abe2b636ef029e398cb21f181)

- **作者**: Hong Zhang
- **时间**: 2026-05-06T07:14:21Z
- **提交信息**: fix fft dtype compatibility in deepspeed (#1427)

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-05-07
**监控日期**: 2026-05-06
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 27181
- **最后更新**: 2026-05-07T14:35:40Z

## 提交统计

- **昨日提交总数**: 32
- **提交者数量**: 11
- **主要提交者**: cctry, Xiaoyu Zhang, gh1595

## AI分析总结

好的，作为专业的代码分析助手，以下是对仓库 `sgl-project/sglang` 昨日提交记录的分析总结。

### 1. 主要更新类型

- **Bug修复 (Bug Fixes):** 数量最多，涉及多个核心模块。
- **功能新增 (New Features):** 包括新的工具、测试框架和功能支持。
- **性能优化 (Performance Optimization):** 针对特定模型和操作进行了优化。
- **重构 (Refactoring):** 对内部模块进行解耦和清理。
- **测试与CI (Testing & CI):** 增加了新的测试用例，调整了CI配置。
- **文档更新 (Documentation):** 修正了环境配置说明。

### 2. 关键变更点及其与项目整体方向的关系

- **`[Codex] Optimize Z-Image packed QKV`**: 针对Codex模型（可能是多模态模型）的QKV（查询、键、值）打包操作进行了优化。这直接提升了模型推理时的计算效率，符合项目追求高性能推理的目标。
- **`[LoRA] Fix qkv_proj LoRA buffer sizing`**: 修复了在使用张量并行（TP）且头数配置特殊时，LoRA适配器的缓冲区大小计算错误。这确保了LoRA微调功能在复杂部署场景下的正确性，增强了项目的灵活性和兼容性。
- **`[PD] Prevent update_status to Failed from cleared entries` & `[PD] Fix missing update_status call in abort()`**: 修复了PD（推测解码/并行解码）模块中状态管理的两个关键Bug。这直接关系到模型推理的稳定性和正确性，是提升项目可靠性的重要步骤。
- **`[CP] Register KV cache allgather buffer with symmetric memory`**: 为上下文并行（CP）中的KV缓存全收集操作注册了对称内存。这可能是为了优化跨GPU通信效率，是项目在分布式推理方向上的持续优化。
- **`Support swa HiCache for unified radix cache`**: 为统一的基数缓存（Radix Cache）增加了对滑动窗口注意力（SWA）HiCache的支持。基数缓存是SGLang的核心特性之一，用于高效管理KV缓存，此更新扩展了其适用范围，使其能更好地服务于长上下文和流式应用。
- **`Refactor: decouple segment tracking from comm registration`**: 对通信模块进行了重构，将段跟踪与通信注册解耦。这提高了代码的可维护性和模块化程度，为未来更复杂的通信模式打下基础。
- **`Improve metrics, observability, and PD deploy tooling`**: 增强了指标、可观测性和PD部署工具。这有助于开发者更好地监控系统状态、定位问题，并简化部署流程，对项目的运维友好性有显著提升。
- **`Support getting checksums in weight checker` 及相关提交**: 为权重检查器增加了校验和功能，并进行了重构和测试。权重检查器是确保模型加载正确性的关键组件，此更新增强了其健壮性和可调试性。
- **`[Codex] Diffusion handle non-contiguous CFG communication`**: 修复了Codex模型中扩散（Diffusion）模块在处理非连续内存时的通信问题。这再次体现了对多模态模型（特别是扩散模型）的支持和优化。
- **`dumper grafter` 系列提交**: 引入了一个名为“dumper grafter”的新工具/框架，支持跨系统张量移植、日志记录、数据转换等功能。这看起来是一个强大的调试和诊断工具，用于捕获、分析和重放张量数据，对复杂问题的排查非常有价值。

### 3. 对项目的影响和潜在意义

- **稳定性与可靠性显著提升**: 大量针对PD、LoRA、权重检查器等核心模块的Bug修复，直接提升了SGLang在生产环境中的稳定性和可靠性。
- **多模态模型支持深化**: 对Codex模型的多次优化和修复，表明项目正在积极扩展对多模态模型（如视觉-语言模型、扩散模型）的支持，并解决其特有的性能与正确性问题。
- **分布式推理能力增强**: 对CP、PD等分布式推理模块的优化和修复，以及通信模块的重构，巩固了SGLang在高效分布式推理方面的领先地位。
- **可观测性与可调试性增强**: 新的指标、日志和“dumper grafter”工具，为开发者提供了更强大的手段来监控、诊断和优化系统，降低了开发和运维门槛。
- **核心特性持续演进**: 对基数缓存（Radix Cache）的扩展，使其能支持更复杂的注意力模式（如SWA），这有助于SGLang在长上下文和流式应用场景中保持优势。

### 4. 值得关注的技术点

- **`dumper grafter` 工具**: 这是一个非常值得关注的新工具。它似乎提供了一种“张量级”的调试能力，可以记录、转换和重放不同系统间的张量数据，对于排查分布式训练/推理中的非确定性Bug或通信问题可能非常有效。
- **`Symmetric memory` 在CP中的应用**: 为KV缓存全收集注册对称内存，这可能是一种针对特定硬件（如NVIDIA GPU）的内存优化技巧，用于减少跨设备通信的开销。
- **`HiCache` 与 `Radix Cache` 的结合**: 将滑动窗口注意力（SWA）的缓存机制（HiCache）集成到统一的基数缓存中，这是一个巧妙的设计，展示了如何将不同的缓存策略统一管理，以支持更广泛的模型架构。
- **`Weight Checker` 的增强**: 引入校验和功能，使得模型权重的完整性验证更加可靠，这对于确保模型加载的正确性至关重要。

###

## 详细提交记录

### [a9a8b20](https://github.com/sgl-project/sglang/commit/a9a8b20a90df3c8b64f7308abde7d3d1fa1a5d12)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-05-06T23:51:22Z
- **提交信息**: [codex] Optimize Z-Image packed QKV (#24117)

### [9e1336d](https://github.com/sgl-project/sglang/commit/9e1336d406f9a6873a3bd4345a7294ee728901b6)

- **作者**: Baizhou Zhang
- **时间**: 2026-05-06T22:42:54Z
- **提交信息**: [Misc] Fix breaking weight checker test (#24553)

### [ece7e95](https://github.com/sgl-project/sglang/commit/ece7e95b659940ee266b49c3b94482a6b7b9c4c6)

- **作者**: gh1595
- **时间**: 2026-05-06T21:51:30Z
- **提交信息**: [LoRA] Fix qkv_proj LoRA buffer sizing when tp_size > num_key_value_heads (#24420)

Co-authored-by: Yanbin Jiang <jybsuper@gmail.com>

### [e72246c](https://github.com/sgl-project/sglang/commit/e72246c6e64526669b23eed5228fb5bb42e313f5)

- **作者**: Alison Shao
- **时间**: 2026-05-06T21:35:43Z
- **提交信息**: ci: bump test_mimo_models.py est_time 330 → 610 (#24551)

### [bc70488](https://github.com/sgl-project/sglang/commit/bc704886956c906619d63e609bb0cbb465d05520)

- **作者**: jsheng_Linkedin
- **时间**: 2026-05-06T21:28:39Z
- **提交信息**: [CI] Temporarily disable marco/mcdse-2b-v1 in test_embedding_models (#24279)

Co-authored-by: Claude Opus 4.7 (1M context) <noreply@anthropic.com>

### [b859f7f](https://github.com/sgl-project/sglang/commit/b859f7ffbaf01955b44dded4ecb5a3da9cddd426)

- **作者**: Lianmin Zheng
- **时间**: 2026-05-06T18:27:35Z
- **提交信息**: Improve metrics, observability, and PD deploy tooling (#24521)

### [d86f291](https://github.com/sgl-project/sglang/commit/d86f2916ccbf1ffa248dc3e102842411466ac94b)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-05-06T16:05:43Z
- **提交信息**: Fix diffusion fallback guards and validation (#23335)

### [32d9998](https://github.com/sgl-project/sglang/commit/32d9998b9d4e640419a640452a910b0c4c03aaf0)

- **作者**: Shangming Cai
- **时间**: 2026-05-06T15:32:04Z
- **提交信息**: [PD] Prevent update_status to Failed from cleared entries (#24539)

Signed-off-by: Shangming Cai <csmthu@gmail.com>

### [bfc1aea](https://github.com/sgl-project/sglang/commit/bfc1aeae13932bffd9e3ce905391b692eec3e9cd)

- **作者**: sky
- **时间**: 2026-05-06T15:24:36Z
- **提交信息**: [CP] Register KV cache allgather buffer with symmetric memory (#24040)

Signed-off-by: wangfakang <fakangwang@gmail.com>

### [c4c5541](https://github.com/sgl-project/sglang/commit/c4c5541618dd5931a77b0e16890a22e234562122)

- **作者**: fzyzcjy
- **时间**: 2026-05-06T14:59:28Z
- **提交信息**: Support getting checksums in weight checker (#24537)

### [ae5ae84](https://github.com/sgl-project/sglang/commit/ae5ae840f63fd4797764def5c0888599fbcb6032)

- **作者**: fzyzcjy
- **时间**: 2026-05-06T14:52:07Z
- **提交信息**: Refactor buffer patterns in weight checker (#24538)

### [800deaa](https://github.com/sgl-project/sglang/commit/800deaaefab76c03716e5c4c3f24c5c00f5c063f)

- **作者**: fzyzcjy
- **时间**: 2026-05-06T14:48:48Z
- **提交信息**: Add unit and end-to-end tests for weight checker (#24536)

### [eb5f0fb](https://github.com/sgl-project/sglang/commit/eb5f0fbeef5b90aa522abf0103f6e0eaf00c29d9)

- **作者**: Ke Bao
- **时间**: 2026-05-06T14:19:25Z
- **提交信息**: Support swa HiCache for unified radix cache (#23391)

Co-authored-by: hzh0425 <hzh0425@apache.org>

### [491051c](https://github.com/sgl-project/sglang/commit/491051c622e251cb74a110f5a7684340b8280f7f)

- **作者**: fzyzcjy
- **时间**: 2026-05-06T13:21:12Z
- **提交信息**: Cherry pick weight_checker `_weight_fp32` buffer skip from #22663 (#24534)

Co-authored-by: JD <jaedon.guo@gmail.com>

### [0d40931](https://github.com/sgl-project/sglang/commit/0d40931b08ca29e42507b25ee587e1d21d2b0f9e)

- **作者**: fzyzcjy
- **时间**: 2026-05-06T13:14:01Z
- **提交信息**: Cherry pick weight_checker non-persistent buffer pattern list from #21278 (#24533)

Co-authored-by: JD <jaedon.guo@gmail.com>

### [864f963](https://github.com/sgl-project/sglang/commit/864f9633f251a5d345a925c06b744743a63ca258)

- **作者**: fzyzcjy
- **时间**: 2026-05-06T13:13:17Z
- **提交信息**: Cherry pick weight_checker fp8 dequant fix and non-persistent buffer skip from #21494 (#24532)

Co-authored-by: Yueming Yuan <yym022502@gmail.com>

### [d4d4b04](https://github.com/sgl-project/sglang/commit/d4d4b04d66207f1695c687860640f9f18821e04e)

- **作者**: Lianmin Zheng
- **时间**: 2026-05-06T12:30:11Z
- **提交信息**: [PD] Fix missing update_status call in abort() across all KV backends (#24522)

### [163bf1b](https://github.com/sgl-project/sglang/commit/163bf1ba7143fe612124598f485b670fdd5bf1c1)

- **作者**: cctry
- **时间**: 2026-05-06T10:44:48Z
- **提交信息**: [PD] Fix KV transfer metrics (#24416)

Co-authored-by: Lianmin Zheng <lianminzheng@gmail.com>
Co-authored-by: Shangming Cai <csmthu@gmail.com>

### [11b0e51](https://github.com/sgl-project/sglang/commit/11b0e510aad5732eda17444deab681ba13d2c890)

- **作者**: fzyzcjy
- **时间**: 2026-05-06T10:26:41Z
- **提交信息**: Fix lint (#24520)

### [7ec18f7](https://github.com/sgl-project/sglang/commit/7ec18f7e4e5c015a03267597d12c84397869c121)

- **作者**: Baizhou Zhang
- **时间**: 2026-05-06T09:37:23Z
- **提交信息**: [Doc] Fix instruction on Cuda 13 environments (#24516)

### [b67df7c](https://github.com/sgl-project/sglang/commit/b67df7cd1b1ae043f6a6685d515917cf78d5380a)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-05-06T09:27:14Z
- **提交信息**: [Codex] Diffusion handle non-contiguous CFG communication (#24332)

Co-authored-by: BBuf Codex <bbuf-codex@users.noreply.github.com>

### [c8bc235](https://github.com/sgl-project/sglang/commit/c8bc23522fe2534b0648f9ce36b7837b38a68f55)

- **作者**: sky
- **时间**: 2026-05-06T09:07:58Z
- **提交信息**: Refactor: decouple segment tracking from comm registration (#21392)

Signed-off-by: wangfakang <fakangwang@gmail.com>

### [a858fda](https://github.com/sgl-project/sglang/commit/a858fda708d45be60f12a072f21c67ffa75cd701)

- **作者**: fzyzcjy
- **时间**: 2026-05-06T09:00:13Z
- **提交信息**: Add e2e test with log snapshot in dumper grafter (#24513)

### [8527db0](https://github.com/sgl-project/sglang/commit/8527db0a91fcd8b909c61c9dee4a1a7872ea1cd3)

- **作者**: fzyzcjy
- **时间**: 2026-05-06T08:58:08Z
- **提交信息**: Enhance diff and tensor-info logging in dumper grafter (#24512)

### [75943cf](https://github.com/sgl-project/sglang/commit/75943cfbcf79dff54688ad57032bdceb70e9c0c2)

- **作者**: fzyzcjy
- **时间**: 2026-05-06T08:57:44Z
- **提交信息**: Support per-call extras and dataclass transform input in dumper grafter (#24511)

### [833279e](https://github.com/sgl-project/sglang/commit/833279eb2ea0b2a5d8adaa14225297a91ada5210)

- **作者**: fzyzcjy
- **时间**: 2026-05-06T08:57:20Z
- **提交信息**: Support multi-rank exchange via all_gather_object in dumper grafter (#24510)

### [ebd64f5](https://github.com/sgl-project/sglang/commit/ebd64f5d40e20a77b35ca6fae9feaf1096737d91)

- **作者**: fzyzcjy
- **时间**: 2026-05-06T08:56:52Z
- **提交信息**: Support user-supplied recv-side transform in dumper grafter (#24509)

### [9a65f0a](https://github.com/sgl-project/sglang/commit/9a65f0ac2687d3067a206307f7298ce53716139f)

- **作者**: fzyzcjy
- **时间**: 2026-05-06T08:56:24Z
- **提交信息**: Support t2b direction and overlap protection in dumper grafter (#24508)

### [58487e6](https://github.com/sgl-project/sglang/commit/58487e68e546d8938530e73939147a8f7a1fb1e0)

- **作者**: fzyzcjy
- **时间**: 2026-05-06T08:55:40Z
- **提交信息**: Support cross-system tensor grafting in dumper (#24507)

### [61104d7](https://github.com/sgl-project/sglang/commit/61104d7d0a7041bbb749578b10e165b86d4b1084)

- **作者**: fzyzcjy
- **时间**: 2026-05-06T08:54:20Z
- **提交信息**: Add prefixed _log helper in dumper (#24506)

### [2317222](https://github.com/sgl-project/sglang/commit/23172224b92a74e6f6392f85d1677da65ed3e9d5)

- **作者**: fzyzcjy
- **时间**: 2026-05-06T08:53:56Z
- **提交信息**: chore: Gitignore Claude scheduled_tasks.lock (#24505)

### [094b90b](https://github.com/sgl-project/sglang/commit/094b90b1ece466253359e22861ba6c031938099f)

- **作者**: Alison Shao
- **时间**: 2026-05-06T08:02:31Z
- **提交信息**: ci: drop 1-gpu-h100-h200 shared label (#24495)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-05-07
**监控日期**: 2026-05-06
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization for Diffusion Transformers.
- **语言**: Python
- **星标数**: 1164
- **最后更新**: 2026-05-07T03:49:05Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-05-07
**监控日期**: 2026-05-06
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 79273
- **最后更新**: 2026-05-07T14:28:17Z

## 提交统计

- **昨日提交总数**: 28
- **提交者数量**: 28
- **主要提交者**: Nicolò Lucchesi, Micah Williamson, Yongye Zhu

## AI分析总结

好的，作为专业的代码分析助手，以下是对 vllm-project/vllm 仓库昨日提交记录的分析总结。

### 1. 主要更新类型

- **Bug修复 (Bugfix):** 占比最高，共10项，覆盖了模型推理、流水线并行、API兼容性、测试框架等多个方面。
- **功能新增 (Feat):** 2项，包括对Intel DNNL库的AVX2 W8A8 Int8量化支持，以及为Gemma4模型添加的多令牌预测（MTP）投机解码支持。
- **文档更新 (Docs):** 2项，涉及缓存目录安全指南和模型支持列表更新。
- **重构 (Refactor):** 1项，对NIXL（一个可能的网络通信库）的传输设计进行了重构。
- **CI/测试 (CI/Test):** 3项，包括启用新模型解析测试、修复测试框架问题、调整测试路径。
- **平台适配 (Platform):** 5项，主要针对ROCm (AMD GPU)、CPU (RISC-V)、XPU (Intel)等非NVIDIA平台进行修复和功能增强。

### 2. 关键变更点及其与项目整体方向的关系

- **模型支持扩展与修复:**
    - **DeepSeekV3/V4 & Qwen3:** 修复了DeepSeek模型对`string='true|false'`属性的解析问题，以及Qwen3的流式输出内容路由问题。这体现了项目对最新、最流行开源模型的快速跟进和兼容性保障。
    - **Gemma4:** 新增了MTP投机解码支持，并修复了多模态编码器的token预算问题。这表明vLLM正积极支持Google的最新模型及其高级特性。
    - **ModernBERT & Gemma4:** 更新了文档，将ModernBERT加入评分模型列表，并启用了Gemma4的解析测试。这确保了新模型能被正确识别和使用。

- **性能与效率优化:**
    - **投机解码 (Speculative Decode):** 为Gemma4添加MTP支持，直接提升了推理吞吐量，符合项目“fast”和“cheap”的核心目标。
    - **量化支持:** 新增了Intel CPU上的FP8 W8A16线性层支持和DNNL库的AVX2 W8A8 Int8支持。这显著扩展了vLLM在CPU平台上的部署能力和性能，降低了硬件门槛。
    - **流水线并行 (PP) 修复:** 修复了PP模式下因token丢失导致的精度下降问题，这对于大规模分布式部署至关重要，保证了模型在扩展时的准确性。

- **平台兼容性与稳定性:**
    - **ROCm (AMD):** 移除了一个旧的NCCL阻塞等待环境变量（因ROCm 7.2已修复），修复了MoE权重更新后张量地址重用问题，以及Qwen3.5在TP=2时的参数错误。这些修复显著提升了vLLM在AMD GPU上的稳定性和性能。
    - **CPU (RISC-V):** 增强了OpenMP线程绑定逻辑，提升了在RISC-V架构上的运行稳定性。
    - **XPU (Intel):** 禁用了不支持的CUDA图内存估算功能，避免在Intel XPU上出现错误。

- **基础设施与可靠性:**
    - **KV Offload:** 修复了in-flight块在`lookup()`时返回None的问题，这对于实现长上下文推理的显存卸载功能至关重要。
    - **测试框架:** 修复了`spawn_new_process_for_each_test`静默吞掉测试失败的问题，提高了CI/CD的质量门禁可靠性。
    - **NIXL重构:** 对底层网络传输库进行重构，旨在为未来的分布式通信提供更清晰、更高效的设计。

### 3. 对项目的影响和潜在意义

- **提升模型生态的广度和深度:** 对DeepSeek、Qwen、Gemma等热门模型的持续修复和特性支持，巩固了vLLM作为首选LLM推理引擎的地位。
- **降低部署成本，扩展硬件选择:** 对CPU (Intel, RISC-V) 和 AMD GPU的持续优化，使得用户可以在更多样化、可能更经济的硬件上部署LLM，真正实现“cheap”的目标。
- **增强大规模部署的可靠性:** 修复PP模式精度问题和改进测试框架，直接提升了vLLM在生产环境中进行大规模、高可靠性部署的信心。
- **为未来特性铺路:** NIXL重构和KV Offload的修复，为未来更高效的分布式推理和超长上下文支持打下了基础。

### 4. 值得关注的技术点

- **Gemma4 MTP投机解码:** 这是对Google最新投机解码技术的原生支持，值得关注其性能提升效果。
- **CPU上的FP8 W8A16和Int8 W8A8:** 这表明vLLM正在将先进的量化技术从GPU扩展到CPU，对边缘计算和低成本部署意义重大。
- **ROCm生态的成熟:** 多个针对ROCm的修复表明，vLLM对AMD GPU的支持正在快速成熟，不再是“二等公民”。
- **NIXL重构:** 这是一个底层架构变更，虽然对用户透明，但对项目未来的分布式能力有深远影响。

### 5. 基于项目背景的分析：这些提交如何影响项目发展

vLLM的目标是“**Easy, fast, and cheap LLM serving for everyone**”。

- **Easy (易用):** 文档更新（缓存安全、模型列表）和API兼容性修复（OpenAI工具调用、DeepSeek属性解析）直接降低了用户的使用门槛和出错概率。


## 详细提交记录

### [5a0a8fc](https://github.com/vllm-project/vllm/commit/5a0a8fc1ea7542394ff315138bd5677b7b53bca1)

- **作者**: Russell Bryant
- **时间**: 2026-05-06T23:54:29Z
- **提交信息**: [Docs] add cache directory security guidance (#38920)

Signed-off-by: Russell Bryant <rbryant@redhat.com>

### [7a576e2](https://github.com/vllm-project/vllm/commit/7a576e2c724e135236c0dc005dce114c7e4d911e)

- **作者**: Micah Williamson
- **时间**: 2026-05-06T23:37:11Z
- **提交信息**: [ROCm][CI] Remove `TORCH_NCCL_BLOCKING_WAIT=1` After Bugfix In ROCm 7.2 (#41840)

Signed-off-by: Micah Williamson <micah.williamson@amd.com>

### [80d5e7d](https://github.com/vllm-project/vllm/commit/80d5e7d103ee181f66389d0e2580841e2a2f1db5)

- **作者**: Yongye Zhu
- **时间**: 2026-05-06T23:17:48Z
- **提交信息**: [Bugfix] Fix condition to clear persistent topk so that it can be captured regardless (#41665)

Signed-off-by: Yongye Zhu <zyy1102000@gmail.com>

### [9558286](https://github.com/vllm-project/vllm/commit/95582868efd4db0b120e3640bbc61dcfce20d59f)

- **作者**: Chauncey
- **时间**: 2026-05-06T21:48:01Z
- **提交信息**: [Bugfix] DeepSeekV32/v4: respect string='true|false' attribute andunwrap arguments/input wrapper (#41801)

Signed-off-by: chaunceyjiang <chaunceyjiang@gmail.com>
Co-authored-by: QwertyJack <7554089+QwertyJack@users.noreply.github.com>

### [50acdc5](https://github.com/vllm-project/vllm/commit/50acdc5b5cc00f10408d8f98b21fc97efc615173)

- **作者**: xy3
- **时间**: 2026-05-06T21:22:01Z
- **提交信息**: Fix Qwen3 streaming content routing (#40820)

Signed-off-by: xy3 <120182408@qq.com>
Signed-off-by: sfeng33 <4florafeng@gmail.com>
Co-authored-by: sfeng33 <4florafeng@gmail.com>

### [deb737e](https://github.com/vllm-project/vllm/commit/deb737e323b3c2bf7986b2225ba76e32b4b097f2)

- **作者**: JackyLiu
- **时间**: 2026-05-06T21:17:56Z
- **提交信息**: [Doc] Add ModernBertForSequenceClassification to scoring.md cross-en… (#41832)

Signed-off-by: JLiu4Coding <lzwgre@126.com>

### [f3f8efa](https://github.com/vllm-project/vllm/commit/f3f8efa73a49ec87d6a22fe268d0abde503497d7)

- **作者**: Flora Feng
- **时间**: 2026-05-06T20:25:34Z
- **提交信息**: [CI] Enable gemma4 parser test on CI (#41857)

Signed-off-by: sfeng33 <4florafeng@gmail.com>

### [ca3e62d](https://github.com/vllm-project/vllm/commit/ca3e62d3363d3f8f5470b351ebfc48fa1826e687)

- **作者**: Johnny Yang
- **时间**: 2026-05-06T18:41:37Z
- **提交信息**: Upgrade tpu-inference to v0.19.0 (#41844)

Signed-off-by: Johnny Yang <johnnyyang@google.com>

### [38e1667](https://github.com/vllm-project/vllm/commit/38e16678ba7ec8417ce87f7010a03d203ee64b2b)

- **作者**: Benjamin Chislett
- **时间**: 2026-05-06T18:17:02Z
- **提交信息**: [Bugfix] Align block table for TRTLLM MLA edge-case (#39324)

Signed-off-by: Benjamin Chislett <bchislett@nvidia.com>

### [27702f6](https://github.com/vllm-project/vllm/commit/27702f6d0879312c011e0180ffd48cbc034380d2)

- **作者**: Jing Wang
- **时间**: 2026-05-06T18:07:32Z
- **提交信息**: [Bugfix] Fix token loss in PP mode which causes degraded accuracy (#41133)

Signed-off-by: Jing Wang <jingwang96@qq.com>
Co-authored-by: Copilot <175728472+Copilot@users.noreply.github.com>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [22a3cbe](https://github.com/vllm-project/vllm/commit/22a3cbe1520bc8a3b19ace0abe497c514b3129ea)

- **作者**: Divakar Verma
- **时间**: 2026-05-06T16:11:36Z
- **提交信息**: [ROCm] aiter_unified_attn fp8 q scale refactor (#38296)

Signed-off-by: Divakar Verma <divakar.verma@amd.com>

### [d5b31c9](https://github.com/vllm-project/vllm/commit/d5b31c954d511ecdb486e84c71d52d2a5c28ade4)

- **作者**: Viktor Pus
- **时间**: 2026-05-06T16:10:17Z
- **提交信息**: [Bugfix] Account for truncate_prompt_tokens when computing max_tokens (#41800)

Signed-off-by: Viktor Pus <viktorpus@tenstorrent.com>

### [ee38750](https://github.com/vllm-project/vllm/commit/ee38750a7565ee7158ddc78ff5abd12e9c0d3733)

- **作者**: David Zheng
- **时间**: 2026-05-06T15:17:15Z
- **提交信息**: [Bugfix] Fix spawn_new_process_for_each_test silently swallowing test failures (#41423)

Signed-off-by: dqzhengAP <dqzheng1996@gmail.com>

### [27e0057](https://github.com/vllm-project/vllm/commit/27e0057aeda6bc443069c20fdf2f3cc95ed892f3)

- **作者**: Luciano Martins
- **时间**: 2026-05-06T14:39:29Z
- **提交信息**: [Spec Decode] Add Gemma4 MTP speculative decoding support (#41745)

Signed-off-by: Luciano Martins <lucianommartins@users.noreply.github.com>
Co-authored-by: Luciano Martins <lucianommartins@users.noreply.github.com>

### [f39bcf1](https://github.com/vllm-project/vllm/commit/f39bcf1e30693f2e620e3a2ec732c5f7192408fb)

- **作者**: Ronen Schaffer
- **时间**: 2026-05-06T14:31:21Z
- **提交信息**: [KV Offload] Return None from lookup() for in-flight blocks (#41795)

Signed-off-by: Ronen Schaffer <ronen.schaffer@ibm.com>

### [6467213](https://github.com/vllm-project/vllm/commit/6467213a9f118fcf5ebf65d5e1ee8d64d2e101e4)

- **作者**: jack
- **时间**: 2026-05-06T14:16:03Z
- **提交信息**: fix(openai): tolerate empty content in forced tool choice (#40148)

Signed-off-by: QwertyJack <7554089+QwertyJack@users.noreply.github.com>
Signed-off-by: chaunceyjiang <chaunceyjiang@gmail.com>
Co-authored-by: QwertyJack <7554089+QwertyJack@users.noreply.github.com>
Co-authored-by: chaunceyjiang <chaunceyjiang@gmail.com>

### [df8e63f](https://github.com/vllm-project/vllm/commit/df8e63f4edabc06e51c10fe479fc9b95c303542f)

- **作者**: zhanqiuhu
- **时间**: 2026-05-06T13:16:25Z
- **提交信息**: nixl refactor: new transfer design (#40731)

Signed-off-by: ZhanqiuHu <zhu@redhat.com>
Signed-off-by: NickLucche <nlucches@redhat.com>
Co-authored-by: NickLucche <nlucches@redhat.com>

### [242afc6](https://github.com/vllm-project/vllm/commit/242afc6bf40d6d088b7b97eda1dd7f00ddcdfa21)

- **作者**: SeongJun Lee
- **时间**: 2026-05-06T12:54:42Z
- **提交信息**: [MM][Gemma4] Respect max_soft_tokens in encoder budget (#41799)

Signed-off-by: lesj0610 <lesj0610@users.noreply.github.com>
Co-authored-by: lesj0610 <lesj0610@users.noreply.github.com>
Co-authored-by: gemini-code-assist <gemini-code-assist@google.com>

### [5d0fd87](https://github.com/vllm-project/vllm/commit/5d0fd87038b123a11dd9c85a05ce2d258e27ce7b)

- **作者**: lyd1992
- **时间**: 2026-05-06T11:38:08Z
- **提交信息**: [CPU][RISC-V] Auto-bind OMP threads and harden nobind path (#40569)

Signed-off-by: liuyudong <liuyudong@iscas.ac.cn>

### [d8deb5b](https://github.com/vllm-project/vllm/commit/d8deb5b7ade403ae36feda6f71898a61ac0bda6e)

- **作者**: Harry Mellor
- **时间**: 2026-05-06T11:13:12Z
- **提交信息**: Fix some legacy checkpoints with deprecated `rope_type` values (#41734)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [2e777d2](https://github.com/vllm-project/vllm/commit/2e777d21a82c232ee8bc315c13400cd9d9afd489)

- **作者**: Yuankai Chen
- **时间**: 2026-05-06T10:32:26Z
- **提交信息**: [Bugfix][Rocm]Aiter MoE re-uses existing tensor addresses after weight update. (#40390)

Signed-off-by: Yuankai Chen <yuankach@amd.com>
Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>

### [e43a791](https://github.com/vllm-project/vllm/commit/e43a7912847ef335337476138e5e863850a4ae0a)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-05-06T09:41:24Z
- **提交信息**: [Bugfix][CI] Fix Disaggregated test area path (#41794)

Signed-off-by: NickLucche <nlucches@redhat.com>

### [66d1cc0](https://github.com/vllm-project/vllm/commit/66d1cc0c77628e36df8e5e245c116e6aac3045fb)

- **作者**: Zhaodong Bing
- **时间**: 2026-05-06T08:38:32Z
- **提交信息**: fix(rocm): remove workaround causing invalid argument on Qwen3.5 with TP=2 (#40686)

Co-authored-by: Test User <test@example.com>
Co-authored-by: TJian <tunjian.tan@embeddedllm.com>

### [1c58876](https://github.com/vllm-project/vllm/commit/1c58876618dc7275520297cbbd1244a64f551952)

- **作者**: Chaojun Zhang
- **时间**: 2026-05-06T08:38:18Z
- **提交信息**: [XPU] Disable CUDA graph memory estimate on XPU platform (#41344)

Signed-off-by: chaojun-zhang <chaojun.zhang@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [51c1ee9](https://github.com/vllm-project/vllm/commit/51c1ee9b7c8acbba4899a8ebffd390685d171946)

- **作者**: wang.yuqi
- **时间**: 2026-05-06T08:20:38Z
- **提交信息**: [Examples] Resettle Disaggregated examples. (#40759)

Signed-off-by: wang.yuqi <yuqi.wang@daocloud.io>
Signed-off-by: wang.yuqi <noooop@126.com>
Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>

### [213f10b](https://github.com/vllm-project/vllm/commit/213f10bfdd43422d2936a8f5e218000050572678)

- **作者**: Lucas Kabela
- **时间**: 2026-05-06T08:11:37Z
- **提交信息**: [Bugfix] Fix codegen for unqualified names (#40726)

Signed-off-by: Lucas Kabela <lucaskabela@meta.com>

### [e87e09a](https://github.com/vllm-project/vllm/commit/e87e09a50a41db3ddd1cc0403e8d1ebe0b0f522c)

- **作者**: Tianmu Li
- **时间**: 2026-05-06T07:28:02Z
- **提交信息**: [Feat] dnnl build for AVX2 W8A8 Int8 (#41318)

Signed-off-by: Li, Tianmu <tianmu.li@intel.com>
Co-authored-by: Li, Jiang <jiang1.li@intel.com>

### [809b98e](https://github.com/vllm-project/vllm/commit/809b98e5b71482e52ee0ecbf140084aae49f3652)

- **作者**: Yuwen Zhou
- **时间**: 2026-05-06T07:05:27Z
- **提交信息**: [CPU] Add FP8 W8A16 linear support (#41186)

Signed-off-by: yuwenzho <yuwen.zhou@intel.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-05-07
**监控日期**: 2026-05-06
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 4617
- **最后更新**: 2026-05-07T14:28:25Z

## 提交统计

- **昨日提交总数**: 16
- **提交者数量**: 14
- **主要提交者**: dengyunyang, Vensen, Juan Pablo Zuluaga

## AI分析总结

好的，这是对 `vllm-project/vllm-omni` 仓库昨日提交记录的分析总结。

### 1. 主要更新类型

- **功能新增 (Feature)**: 4项
- **Bug修复 (BugFix)**: 7项
- **重构 (Refactor)**: 1项
- **文档更新 (Docs)**: 1项
- **CI/构建 (CI/Build)**: 2项

### 2. 关键变更点及其与项目整体方向的关系

项目目标：**为所有人提供简单、快速、便宜的Omni模态模型服务**。

- **功能新增 - 核心模型与能力扩展**:
    - **HunyuanImage-3.0 图像编辑 (IT2I) 支持** (commit `576afb6`): 直接扩展了项目支持的模态和任务类型，从文本到图像生成扩展到图像编辑，增强了“Omni”能力。
    - **Qwen3-Omni Code2Wav 解码器 CUDA Graph 支持** (commit `19f8f42`): 针对特定模型（Qwen3-Omni）的音频生成部分进行性能优化，体现了项目对前沿多模态模型的快速跟进和深度优化。
    - **多阶段部署支持** (commit `1e5f288`): 这是一个重要的架构级功能，允许将复杂的Omni模型（如语音、视频生成）拆分为多个阶段进行部署和推理，提升了服务的灵活性和可扩展性，是实现“便宜”和“快速”服务的关键基础设施。
    - **Z-Image 文本编码器 FP8 在线量化** (commit `0a8204c`): 通过量化技术降低模型内存占用和计算成本，直接服务于“便宜”和“快速”的目标。

- **Bug修复 - 稳定性和准确性提升**:
    - **修复单字回答精度问题** (commit `b25ea13`): 直接提升模型输出质量，对用户体验至关重要。
    - **修复 CLI 中 tokenizer 参数传递** (commit `56ca5d9`): 确保用户通过命令行配置的 tokenizer 能正确应用到所有模型阶段，修复了配置一致性问题。
    - **修复离线路径下语音克隆字段读取** (commit `687a44e`): 修复了特定功能（语音克隆）在特定使用场景（离线）下的可用性问题。
    - **修复 CLI Logo 在管道输出时 ANSI 颜色丢失** (commit `b8bd758`): 提升命令行工具的用户体验。
    - **修复默认扩散阶段配置生成器丢弃运行时参数** (commit `1e8dc84`): 修复了与多阶段部署相关的配置错误，确保运行时参数正确传递。
    - **修复有问题的 Pipeline 在注册时导致迭代失败** (commit `6f784cb`): 提升了系统的健壮性，避免单个Pipeline问题影响整个服务。
    - **HunyuanImage-3.0 精度修复** (commit `369a47d`): 对新功能的快速跟进修复，保证其质量。

- **重构与CI**:
    - **移除遗留的 CLI 参数助手并调整测试** (commit `81ab2f9`): 清理代码库，为未来的配置系统重构铺路。
    - **更新 XPU Dockerfile 以适配 PyTorch 2.11** (commit `2856ff7`): 保持对 Intel XPU 硬件的支持，扩展项目硬件生态。
    - **修复 Qwen 图像性能退化问题** (commit `28558cc`): 确保在最新依赖（vllm 0.20, CUDA 13.0）下模型性能不下降。
    - **CI 测试中增加 max_tokens** (commit `282e0b6`): 提升测试覆盖率，确保长文本生成场景的稳定性。

- **文档更新**:
    - **添加 LTX-2-T2V 和 LTX-2-I2V 使用指南** (commit `e969d2e`): 为新的视频生成模型提供文档，降低用户使用门槛，符合“Easy”的目标。

### 3. 对项目的影响和潜在意义

- **核心能力显著增强**: 新增的图像编辑、多阶段部署等功能，使项目从一个“多模态模型服务”向一个更全面的“Omni模态模型服务平台”迈进。
- **稳定性和成熟度提升**: 大量的Bug修复，特别是针对精度、配置传递和系统健壮性的修复，表明项目正在从快速迭代期进入稳定期，这对于生产环境部署至关重要。
- **性能与成本优化**: FP8量化和CUDA Graph支持等优化，直接降低了推理成本和延迟，使“快速”和“便宜”的承诺更具说服力。
- **生态扩展**: 对XPU的支持和文档更新，表明项目正在积极吸引更广泛的用户和硬件平台。

### 4. 值得关注的技术点

- **多阶段部署架构**: 这是本次更新中最具影响力的技术点。它暗示了项目内部可能采用了一种流水线式的模型执行框架，能够灵活编排不同模态的模型组件（如视觉编码器、LLM、音频解码器）。这为未来支持更复杂的、多步骤的Omni任务（如视频理解与生成）奠定了基础。
- **FP8 在线量化**: 针对特定模块（文本编码器）进行量化，而非全模型量化，这是一种更精细、更高效的优化策略，平衡了精度和性能。
- **CUDA Graph 在非LLM模块的应用**: 将CUDA Graph优化应用于Code2Wav解码器，

## 详细提交记录

### [2856ff7](https://github.com/vllm-project/vllm-omni/commit/2856ff7aeac763e88b095a47d9af503901c50035)

- **作者**: Chendi.Xue
- **时间**: 2026-05-06T22:45:30Z
- **提交信息**: [XPU][DOCKER] update dockerfile.xpu after main repo updating to pt2.11 (#3393)

Signed-off-by: Chendi Xue <chendi.xue@intel.com>

### [56ca5d9](https://github.com/vllm-project/vllm-omni/commit/56ca5d9a8f8779336f6dcdd6f73b0ad020eb77fd)

- **作者**: Chen-Yo Sun
- **时间**: 2026-05-06T22:43:01Z
- **提交信息**: [BugFix] Forward CLI --tokenizer to per-stage engine configs (#3120)

Signed-off-by: Chen-Yo Sun <chenyo.sun@mistral.ai>

### [81ab2f9](https://github.com/vllm-project/vllm-omni/commit/81ab2f98da21817638dbf14c0b0b46e2ad6354b1)

- **作者**: Haco
- **时间**: 2026-05-06T22:32:01Z
- **提交信息**: [Config Refactor] Remove legacy Omni CLI arg helper and align tests with nullified parser defaults (#3144)

Signed-off-by: xiaohajiayou <923390377@qq.com>

### [b25ea13](https://github.com/vllm-project/vllm-omni/commit/b25ea13cb04c7a56b944da110bceb07a5c2bd6f7)

- **作者**: amy-why-3459
- **时间**: 2026-05-06T22:21:00Z
- **提交信息**: [BugFix] Fixed a precision issue with one-word answers. (#3385)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>
Signed-off-by: Hongsheng Liu <liuhongsheng4@huawei.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>
Co-authored-by: Canlin Guo <961750412@qq.com>

### [687a44e](https://github.com/vllm-project/vllm-omni/commit/687a44e5c83cedf16882b188ce0b042197fe69c8)

- **作者**: Yueqian Lin
- **时间**: 2026-05-06T22:17:57Z
- **提交信息**: [Bugfix][OmniVoice] Read voice-cloning fields from OmniTextPrompt in offline path (#3392)

Signed-off-by: Yueqian Lin <linyueqian@outlook.com>

### [19f8f42](https://github.com/vllm-project/vllm-omni/commit/19f8f428223fa8acbeabeed9d89609d623374689)

- **作者**: Juan Pablo Zuluaga
- **时间**: 2026-05-06T22:16:03Z
- **提交信息**: [Feat][Qwen3-Omni] Add CUDA graph support for Code2Wav decoder (#2376)

Signed-off-by: JuanPZuluaga <juanz9312@gmail.com>
Co-authored-by: Yueqian Lin <70319226+linyueqian@users.noreply.github.com>

### [0a8204c](https://github.com/vllm-project/vllm-omni/commit/0a8204cb81bf8608b21fcc3a4199e5bde6b1136c)

- **作者**: Isotr0py
- **时间**: 2026-05-06T16:37:36Z
- **提交信息**: [Quantization] Redo Z-Image text encoder FP8 online quantization (#3279)

Signed-off-by: Isotr0py <mozf@mail2.sysu.edu.cn>
Signed-off-by: Isotr0py <2037008807@qq.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>
Co-authored-by: SYLAR <125541396+lishunyang12@users.noreply.github.com>

### [b8bd758](https://github.com/vllm-project/vllm-omni/commit/b8bd75837ebf716854e40997995928128b6cf0db)

- **作者**: Lidang Jiang
- **时间**: 2026-05-06T15:43:19Z
- **提交信息**: [Bugfix] Fix missing ANSI colors in CLI logo when output is piped (#1636)

Signed-off-by: Lidang-Jiang <lidangjiang@gmail.com>

### [576afb6](https://github.com/vllm-project/vllm-omni/commit/576afb6f53c3e817c1895a3790bacef2470c0fa9)

- **作者**: skf
- **时间**: 2026-05-06T14:37:39Z
- **提交信息**: [Feature] HunyuanImage-3.0 IT2I (image editing) support (#3107)

Signed-off-by: TaffyOfficial <2324465096@qq.com>
Signed-off-by: zuiho <2324465096@qq.com>
Signed-off-by: skf1999 <13234016272@163.com>
Co-authored-by: TaffyOfficial <2324465096@qq.com>
Co-authored-by: dengyunyang <584797741@qq.com>
Co-authored-by: John Liu BUAA <liukecheng97@gmail.com>

### [1e8dc84](https://github.com/vllm-project/vllm-omni/commit/1e8dc841503146bcb2b5af01b36d1eca94dd8e24)

- **作者**: Haco
- **时间**: 2026-05-06T14:21:29Z
- **提交信息**: [Bugfix] Fix default diffusion stage config generator drops runtime engine args (#2559)

Signed-off-by: xiaohajiayou <923390377@qq.com>
Co-authored-by: reidliu41 <reidliu41@users.noreply.github.com>

### [28558cc](https://github.com/vllm-project/vllm-omni/commit/28558cc37471da8258c95aa515363a4a05fce601)

- **作者**: Zeyu Huang | 黃澤宇
- **时间**: 2026-05-06T13:11:35Z
- **提交信息**: [bugfix][CI] Fix qwen image performance degradation w/ vllm 0.20 & CUDA 13.0 (#3352)

Signed-off-by: Huang, Zeyu <11222265+fhfuih@users.noreply.github.com>

### [282e0b6](https://github.com/vllm-project/vllm-omni/commit/282e0b664231275d9a17f56880c99e084028a435)

- **作者**: amy-why-3459
- **时间**: 2026-05-06T12:42:56Z
- **提交信息**: [BugFix][CI] Change max_tokens from 150 to 2048 (#3376)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>
Co-authored-by: Gao Han <hgaoaf@connect.ust.hk>

### [1e5f288](https://github.com/vllm-project/vllm-omni/commit/1e5f288a915494f8ffd9783a4886bbfe9929e65e)

- **作者**: Zheng Wengang
- **时间**: 2026-05-06T11:33:18Z
- **提交信息**: [FEAT] support multi-stage deployment (#2396)

Signed-off-by: ZhengWG <zwg0606@gmail.com>
Signed-off-by: Zheng Wengang <zwg0606@gmail.com>
Signed-off-by: Peiqi Yin <60515999+yinpeiqi@users.noreply.github.com>
Signed-off-by: yinpe <11810305@mail.sustech.edu.cn>
Signed-off-by: yinpeiqi <yinpeiqi809@gmail.com>
Co-authored-by: Peiqi Yin <60515999+yinpeiqi@users.noreply.github.com>
Co-authored-by: yinpe <11810305@mail.sustech.edu.cn>
Co-authored-by: yinpeiqi <yinpeiqi809@gmail.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>
Co-authored-by: Gao Han <hgaoaf@connect.ust.hk>
Co-authored-by: Chenguang Zheng <645327136@qq.com>

### [e969d2e](https://github.com/vllm-project/vllm-omni/commit/e969d2e99f464044b50a59ea618ad9a8edcbfb9f)

- **作者**: fywc
- **时间**: 2026-05-06T10:11:22Z
- **提交信息**: [Docs] Add LTX-2-T2V and LTX-2-I2V recipes (#3294)

Signed-off-by: hanzheli <hanzheli@kuaishou.com>
Signed-off-by: fywc <hanzheli@kuaishou.com>

### [6f784cb](https://github.com/vllm-project/vllm-omni/commit/6f784cbc50b2ef1489a73b7c89016f5d95c18d7c)

- **作者**: Vensen
- **时间**: 2026-05-06T08:35:41Z
- **提交信息**: [Bugfix]: skip faulty pipelines during registry iteration (#2999)

Signed-off-by: vensen <vensenmu@gmail.com>
Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: Gao Han <hgaoaf@connect.ust.hk>
Co-authored-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: Yueqian Lin <70319226+linyueqian@users.noreply.github.com>

### [369a47d](https://github.com/vllm-project/vllm-omni/commit/369a47d5a1874e2a5050c830d5a18398b52446b7)

- **作者**: dengyunyang
- **时间**: 2026-05-06T07:31:11Z
- **提交信息**: [Hunyuanimage-3.0] Accuracy fix (#3373)

Signed-off-by: dengyunyang <584797741@qq.com>

---
