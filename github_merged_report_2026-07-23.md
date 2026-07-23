# GitHub Stars 合并报告 - 2026-07-23

**合并日期**: 2026-07-24
**监控日期**: 2026-07-23
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


**报告日期**: 2026-07-24
**监控日期**: 2026-07-23
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2105
- **最后更新**: 2026-07-23T13:44:09Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-07-24
**监控日期**: 2026-07-23
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2521
- **最后更新**: 2026-07-23T15:15:02Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Musisoul, STwangyingrui

## AI分析总结

根据提供的仓库背景和提交记录，以下是昨日更新的分析总结：

## 1. 主要更新类型
- **Bug修复**（提交 `d21f9b7`）
- **功能新增**（提交 `adf85f2`）

## 2. 关键变更点及其与项目整体方向的关系
- **Bug修复（#1285）**：修复了在新的 Ulysses 序列并行路径中，`max_seqlen_q/kv` 等 dense 元数据未正确传播的问题。这导致某些注意力后端（如 FlashAttention）在序列并行重构后失效。
  - **方向关联**：LightX2V 作为轻量视频生成推理框架，需要支持高效的序列并行机制（如 Ulysses）以处理长视频/长序列。该修复确保了并行策略的完整性和正确性，是维持框架稳定性的关键步骤。
- **功能新增（#1283）**：支持 **Libero-Plus** 的 `fastwam` 训练模式。
  - **方向关联**：Libero-Plus 可能是项目支持的新数据集或任务规范（例如用于视频动作规划或生成）。`fastwam` 可能是一种快速Warmup或训练策略。该提交扩展了训练能力，符合项目从推理向训练场景拓展的趋势。

## 3. 对项目的影响和潜在意义
- **Bug修复**：直接影响使用 Ulysses 序列并行的用户，修复后所有依赖 `max_seqlen_q/kv` 的注意力后端（如 FlashAttention、xformers 等）将正常工作，避免推理/训练崩溃。提升了框架在长序列场景下的**鲁棒性**和**兼容性**。
- **功能新增**：为训练任务增加了新的数据/策略支持，可能加速特定任务（如视频生成中的动作规划）的训练流程，吸引更多研究或应用用户。降低了在 Libero-Plus 上进行实验的门槛。

## 4. 值得关注的技术点
- **序列并行中的元数据传播**：Ulysses 路径中 `dense max_seqlen_q/kv` 的正确传递是稀疏/稠密注意力后端正确工作的前提。该修复揭示了序列并行重构中可能遗漏的关键通信步骤，对同行开发者有参考价值。
- **FastWarm / FastWAM 策略**：如果 `fastwam` 是一种新的训练加速技术（如自适应学习率调度或梯度累积优化），则值得后续关注其实现细节和效果。

## 5. 基于README背景的整体发展影响
- LightX2V 定位为“轻量视频生成推理框架”，但仓库近期开始强化训练支持（如 #1283），表明项目正从纯推理向**推理-训练一体化**演进。这有助于构建完整的视频生成开发生态。
- 序列并行修复保持了对**长视频/高分辨率**场景的适配能力，这是视频生成落地的关键技术挑战之一。项目持续打磨底层通信机制，为未来支持更大规模模型和更长时间视频打下基础。

> 总结：昨日更新以**稳定性修复**和**训练能力扩展**为主，体现了项目在保持高性能推理核心的同时，积极向训练场景渗透，并注重解决并行架构中的隐蔽问题。建议后续关注 Libero-Plus fastwam 的具体效果以及是否存在更多并行策略优化。

## 详细提交记录

### [d21f9b7](https://github.com/ModelTC/LightX2V/commit/d21f9b7ef0159abfac1478b225a4d98ad390e301)

- **作者**: STwangyingrui
- **时间**: 2026-07-23T15:13:05Z
- **提交信息**: FIX ulysses seqlen metadata (#1285)

Fix missing dense max_seqlen_q/kv propagation in the new Ulysses path,
which caused some attention backends to fail after the sequence-parallel
refactor.

### [adf85f2](https://github.com/ModelTC/LightX2V/commit/adf85f2822524992140fc24f705387629819078d)

- **作者**: Musisoul
- **时间**: 2026-07-23T09:21:14Z
- **提交信息**: [Train] Support libero-plus fastwam training (#1283)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-07-24
**监控日期**: 2026-07-23
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2179
- **最后更新**: 2026-07-23T10:16:57Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-07-24
**监控日期**: 2026-07-23
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 6014
- **最后更新**: 2026-07-23T22:10:21Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 4
- **主要提交者**: Yan Wang, Hiki, Jimmy Zhou

## AI分析总结

根据提供的提交记录和项目背景（FlashInfer 是一个面向推理的高性能 GPU 内核库），以下是昨日更新的要点总结：

### 1. 主要更新类型
- **Bug 修复**：2 个（profiler workspace 尺寸计算遗漏、FIFO 发送竞态）
- **性能优化**：1 个（SM103 架构 NVFP4 GEMM epilogue 优化）
- **测试稳定性改进**：1 个（避免 bf16 舍入导致的测试误判）

### 2. 关键变更点及其与项目整体方向的关系
- **修复 NVFP4 autotuner 崩溃**（#4080）：处理 CUTLASS NVFP4 fused-MoE 在 B300 上自调优时的 workspace 尺寸分支缺失。**关系**：确保最新量化方案（NVFP4×NVFP4）在自动化调优工具中正确运行，支持更广泛的量化推理场景。
- **修复 MoE all-to-all 通信竞态**（#4092）：在 `sendFinalize` 前加入 `__syncthreads()`，避免其他线程未写完 payload 时线程 0 就发布 FIFO 头部。**关系**：提升分布式 MoE 推理时数据传输的可靠性，直接解决 issue #3723 中的间歇性零 scale 错误。
- **mm_fp4 测试精度提升**（#4105）：cosine 相似度计算改为 fp32，避免 bf16 舍入悬崖导致误判。**关系**：提高测试的可靠性，减少 CI 随机失败，为量化推理功能的长期维护提供稳定质量门禁。
- **SM103 NVFP4 epilogue 性能优化**（#4063）：在 SM103 架构上使用 256 位全局存储和 `mul.f32x2` 配对乘法，几何平均提速 11%~16%。**关系**：直接改进最新 NVIDIA 架构（SM103）上 NVFP4 GEMM 的推理执行速度，保持 FlashInfer 在高性能推理领域的

## 详细提交记录

### [2475121](https://github.com/flashinfer-ai/flashinfer/commit/2475121f1987396d5c030e68ada892510b61b830)

- **作者**: Jimmy Zhou
- **时间**: 2026-07-23T22:09:36Z
- **提交信息**: fix: Add missing nvfp4 sizing branch in getProfilerWorkspaces (#4080)

<!-- .github/pull_request_template.md -->

## 📌 Description

The FlashInfer perf-CI on B300 crashes when autotuning the CUTLASS NVFP4
fused-MoE with Assertion failed:
`quant_1 && … && quant_6 at cutlass_fused_moe_kernels.cuh:5034.` The
failure is confined to the autotuner's tactic-profiler
(GemmProfilerBackend), which fabricates its own scratch scale-factor
buffers quant_1..6 to time GEMM candidates in isolation — the real MoE
forward builds its quant params from the caller's actual tensors and is
unaffected.

[PR3738](https://github.com/flashinfer-ai/flashinfer/pull/3738)
refactored the profiler's FP4 workspace-sizing, replacing the broad
`is_fp4_w_quant` branch (which covered every FP4-weight case) with two
narrower branches, `is_native_wfp4afp8_family` and
`is_sm90_wfp4afp8_family`, both of which require FP8 activation (`mDType
== kFP8`). Plain NVFP4×NVFP4 has FP4/INT64 activation, so it matched
neither branch, leaving all six quant_* buffers sized 0 → null pointers
→ the assertion.

The fix restores NVFP4 coverage by adding an `is_nvfp4_quant` predicate
(`mSM>=100 && mDType∈{kFP4,kINT64} && mWType∈{kFP4,kINT64}`) and adding
an additional sizing branch, whose buffer sizes are byte-for-byte
identical to the removed `is_fp4_w_quant` block.

Verified on a B300: the previously-crashing repro now completes
autotuning (gemm1/gemm2 21/21 each) and benchmarks cleanly.



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
* Improved profiler workspace sizing for NVFP4 (FP4 quantization)
workloads by applying the correct FP4/NVFP4-specific scaling layout.
* Ensured these updated sizing rules take precedence only for the
intended FP4 + INT64 quantization configuration, preventing unintended
overrides in other quantization families.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [e4c7fce](https://github.com/flashinfer-ai/flashinfer/commit/e4c7fcec10dfc3e349d334707b4f8fd5693332e4)

- **作者**: Hiki
- **时间**: 2026-07-23T21:40:03Z
- **提交信息**: fix(comm): sync all sender threads before publishing the final FIFO step to fix the intermittent race issue (#4092)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

The sender CTA cooperatively writes expert IDs, routing scales, and
optional expert statistics into a FIFO packet. Thread 0 then publishes
the FIFO head with a system-scope release store, allowing the receiver
to consume the packet after a matching system-scope acquire load.

However, `PacketPipeline::sendFinalize()` did not sync the threads
within CTA before publishing the final partial step. Thread 0 could
therefore publish the head while other threads were still writing the
payload, allowing the receiver to observe an incomplete packet. This
manifested intermittently as a valid expert ID paired with a stale zero
scale.

This PR adds a `__syncthreads()` at the start of
`PacketPipeline::sendFinalize()` so every packet writer reaches the
barrier before thread 0 publishes the final step.

Note that, no explicit `__threadfence_system()` is needed. The existing
`st.release.sys`/`ld.acquire.sys` pair provides system-scope
release/acquire semantics.

## 🔍 Related Issues

<!-- Link any related issues here -->

Fixes #3723.

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

Validated on NVIDIA GB10 (DGX Spark):

```bash
python -m pytest -x -q \
  --count=1000 \
  --repeat-scope=function \
  -k "test_moe_alltoall_prepare and 4000" \
  tests/comm/test_trtllm_alltoall.py
```

Results:
  - Before:
<img width="1819" height="757" alt="image"
src="https://github.com/user-attachments/assets/d5f8d768-7eb6-4056-a61e-a4d6754c2e69"
/>

  - After:
<img width="1822" height="689" alt="image"
src="https://github.com/user-attachments/assets/7d4a13dd-5588-4669-a1d9-d4cef70023b1"
/>

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved synchronization during packet processing to ensure all packet
writes complete before transmission is finalized.
  * Increased reliability of data transfers under concurrent workloads.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: Haobin Guo <haobing@nvidia.com>

### [3653d01](https://github.com/flashinfer-ai/flashinfer/commit/3653d011d01e4b0c5f2e1b072f392f31935cc077)

- **作者**: BARRET
- **时间**: 2026-07-23T21:23:24Z
- **提交信息**: test: compute mm_fp4 cosine similarity in fp32 to avoid bf16 rounding cliff (#4105)

<!-- .github/pull_request_template.md -->

## 📌 Description

compute mm_fp4 cosine similarity in fp32 to avoid bf16 rounding cliff.

Example:

```python
import torch
t = torch.tensor(0.9702, dtype=torch.bfloat16)  # true value passes the threshold
print(t.item(), t > 0.97)   # 0.96875 False  <- spurious failure
f = torch.tensor(0.9702, dtype=torch.float32)    # metric computed in fp32 (the fix)
print(f.item(), f > 0.97)           # 0.9702 True   <- correct verdict
```

## 🔍 Related Issues

Contributes to #3824. Complements #3829, which fixes the other half of
the flake (unseeded inputs); the two changes touch different lines and
do not conflict.

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
* Improved numerical consistency in tensor similarity checks by ensuring
values are compared using floating-point precision.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [0f5bb82](https://github.com/flashinfer-ai/flashinfer/commit/0f5bb82457f3c79c1747c951eecab9f658cea351)

- **作者**: Yan Wang
- **时间**: 2026-07-23T13:48:03Z
- **提交信息**: perf(sm103): optimize NVFP4 epilogue stores and scaling (#4063)

## 📌 Description

This PR optimizes the native SM103 (`CTA_K=768`) CUTLASS NVFP4 GEMM
epilogue:

- Keeps the source/C alignment at 128 bits and raises the D/output
alignment to 256 bits, enabling 256-bit global stores in the native
SM103 no-smem epilogue.
- Adds a local CUTLASS fusion callback that evaluates `alpha *
accumulator` in pairs with `mul.f32x2` on device architectures `>=
SM100`, with a scalar host/older-architecture fallback.
- Preserves the stock linear-combination callback structure and
shared-storage layout. The generic K128/K256/TMA-store paths are
unchanged.

The primary gain comes from Store256. The paired multiply is a smaller,
shape-dependent improvement and is included here because it preserves
bitwise output in the tested path.

### Local B300 / SM103 performance

Geometric-mean speedup over the current epilogue across the 14
production M/K/N shapes used in our evaluation:

| Protocol | Store256 only | Store256 + `mul.f32x2` |
|---|---:|---:|
| Independently autotuned | 1.115× | 1.120× |
| Same native K768 tactic | 1.157× | 1.161× |

### Code-generation check

For the final merged library (`63` tactics):

- `FMUL2`: 5,184
- direct `STG.256`: 648
- direct `STG.128`: 0
- existing `UTMASTG`: 324 (unchanged generic path)

## 🔍 Related Issues

N/A

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] Ran all repository pre-commit hooks applicable to the two touched
files with `pre-commit run --files ...`; all passed.
- [ ] A full-tree `pre-commit run --all-files` was not run because this
change touches only two C++ headers.

## 🧪 Tests

- [x] JIT-compiled the complete SM103 NVFP4 module on B300; all 63
tactics load successfully.
- [x] Compared the final merged native K768 kernel against the current
baseline for M=512, K=1536, N=256, tactic 57 (`128x256x768`, cluster
`2x2x1`). Complete BF16 outputs are bitwise equal for `alpha = 1.0`,
`0.73125`, and `-0.34375`.
- [x] The preceding 14-shape fixed-native evaluation completed 42
bitwise-equal comparisons (14 shapes × 3 repetitions).

## Reviewer Notes

The implementation is deliberately local to the SM103 epilogue header
instead of enabling CUTLASS-wide architecture feature macros. This keeps
the change scoped to FlashInfer's native SM103 NVFP4 path and preserves
the incumbent callback ABI/layout.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added SM103-specific FP4 GEMM epilogue fusion to accelerate fused
output computation.
* Updated the SM103 FP4 GEMM configuration to use a dedicated epilogue
alignment setting.
* **Tests**
* Added an SM103-only correctness test for the public `mm_fp4` API on
CUDA (compute capability 10.3), including 32-byte output buffer
alignment checks and accuracy validation against an FP32 reference
across output dtypes and `alpha_factor` values.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yan Wang <yanwa@umb-b300-dp-141.ipp4a1.colossus.nvidia.com>
Co-authored-by: Yan Wang <yanwa@umb-b300-020.ipp2a1.colossus.nvidia.com>
Co-authored-by: Yan Wang <yanwa@umb-b300-022.ipp2a1.colossus.nvidia.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-07-24
**监控日期**: 2026-07-23
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3877
- **最后更新**: 2026-07-23T21:23:50Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Yogya Mehrotra, William Lin

## AI分析总结

好的，以下是针对 FastVideo 仓库昨日提交记录的分析总结：

---

### 1. 主要更新类型
- **Bug修复**（#1574）：修复非 Linux 系统上的依赖安装失败问题
- **CI/测试配置优化**（#1616）：延长完整训练套件的超时时间

---

### 2. 关键变更点及其与项目整体方向的关系
- **跨平台兼容性改进** (#1574)：  
  在非 Linux 系统（如 macOS、Windows）上，自动跳过 `fastvideo-kernel` 和 `flashinfer-python` 这两个 CUDA-only 依赖的安装。  
  **关系**：项目此前可能默认依赖 Linux + CUDA 环境，此补丁拓宽了开发与试用场景，与 README 中强调的“Quick Start”和社区参与（Slack、Discussions）目标一致，降低非 Linux 用户的入门门槛。

- **CI 稳定性提升** (#1616)：  
  将完整训练套件的 CI 超时时间延长，避免因偶然超时导致流水线失败。  
  **关系**：项目处于活跃开发期（每周开发会议），完善的 CI 保障可以加速功能迭代与回归测试，支撑项目长期发展。

---

### 3. 对项目的影响和潜在意义
- **影响**：  
  - 非 Linux 用户（特别是 macOS 开发者）现在能成功安装项目基础依赖，参与开发或本地测试。  
  - CI 管道更健壮，减少假阴性失败，提高开发效率。
- **潜在意义**：  
  - 吸引更多非 GPU 环境下的贡献者（如文档、代码审查、非 CUDA 功能开发）。  
  - 为未来支持 Windows/Linux 混合开发环境铺路，符合开源项目扩大社区参与的趋势。

---

### 4. 值得关注的技术点
- **依赖条件判断**：提交中使用了平台检测逻辑，仅当系统为 Linux 时才添加 CUDA 相关依赖。这是一种常见的跨平台兼容做法，可借鉴到类似项目。
- **CUDA-only 依赖隔离**：`fastvideo-kernel` 和 `flashinfer-python` 可能是针对 NVIDIA GPU 加速的自定义 kernel 或推理优化库，说明项目核心能力依赖 CUDA，但开发者正在努力让非核心功能脱离此限制。

---

### 5. 基于项目背景的发展影响
- **发展方向**：项目定位为视频生成/处理框架（从 README 中 Inferences、Training 等术语判断），追求易用性和快速上手。  
  - 此次修复直接响应了用户在非 Linux 环境下遇到的阻塞问题，提升了项目的跨平台可用性，符合“Quick Start”和社区讨论（#982 表示开发周会）中收集的用户反馈。  
  - CI 超时调整则体现了项目对代码质量与自动化测试的重视，为后续引入更多训练/推理功能打下稳定基础。  
- **总结**：这两次提交虽小，但体现了项目在“保持 CUDA 高性能优势的同时，积极降低外部贡献门槛”的健康演进。

--- 

如果需要更详细的代码分析或相关文件解读，请提供更多上下文。

## 详细提交记录

### [8d89f30](https://github.com/hao-ai-lab/FastVideo/commit/8d89f30d3fe6d6e9e6123114786ceb3e6508d4e8)

- **作者**: Yogya Mehrotra
- **时间**: 2026-07-23T21:23:45Z
- **提交信息**: [bugfix] Skip CUDA-only fastvideo-kernel/flashinfer-python deps on non-Linux (#1574)

Co-authored-by: Claude Sonnet 5 <noreply@anthropic.com>

### [1054635](https://github.com/hao-ai-lab/FastVideo/commit/10546353dabf5aff4d779e8bf47041920f705c32)

- **作者**: William Lin
- **时间**: 2026-07-23T20:00:00Z
- **提交信息**: [ci]: extend Full Suite training lane timeouts (#1616)

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-07-24
**监控日期**: 2026-07-23
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34135
- **最后更新**: 2026-07-23T18:32:39Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Cedric Perauer, Wang, Yi

## AI分析总结

根据您提供的提交记录，并结合 Hugging Face Diffusers 库的常见定位（一个支持多种扩散模型和流水线的开源库），以下是昨日更新的要点总结：

---

### 1. 主要更新类型
- **功能新增**：引入 **Krea2 模块化流水线**（Modular Pipeline）支持，包括配套文档、自动文档生成和测试用例。
- **Bug 修复**：修复 **Wan 视频流水线** 和 **Motif 视频流水线** 的快速测试失败，涉及数值精度、内存卸载覆盖和预期切片值更新。

---

### 2. 关键变更点及其与项目方向的关系
- **Krea2 模块化流水线**  
  - 新增 `modular_pipelines/krea2/` 目录，包含分阶段模块（如 `before_denoise.py`、`modular_blocks_krea2.py`）和自动生成的文档。  
  - **方向关联**：模块化设计是 Diffusers 近年来推动的核心架构演变，旨在让用户更灵活地组合流水线组件，降低定制新流水线的门槛。Krea2 的加入进一步扩充了模块化生态。

- **Wan & Motif 视频流水线测试修复**  
  - 调整 `test_motif_video.py` 中 fp16 保存/加载的容差；修改 `transformer_wan.py` 中 RoPE 模块保持 fp32 精度；更新 `memory.py` 中组卸载覆盖逻辑；更新 `test_wan_image_to_video.py` 中的预期切片值。  
  - **方向关联**：视频生成是 Diffusers 近期重点领域（如支持 Wan、Motif 等模型），测试修复增强了 CI 稳定性，保障视频流水线在不同混合精度和内存策略下的可靠性。

---

### 3. 对项目的影响和潜在意义
- **Krea2 模块化**  
  - **影响**：丰富了 Diffusers 对特定任务（可能为图像/视频到视频生成）的官方支持，为用户提供了开箱即用的新流水线。  
  - **意义**：模块化架构的成熟应用可以加速社区贡献，降低第三方添加新流水线的代码复杂度，促进生态扩展。

- **测试修复**  
  - **影响**：消除当前版本中的已知 CI 失败，提升开发者和用户对视频流水线稳定性的信心。  
  - **意义**：作为持续集成的一部分，这些修复确保了未来对 Wan/Motif 的改动不会破坏现有功能，维护了代码库健康度。

---

### 4. 值得关注的技术点
- **模块化流水线的实现模式**：`modular_blocks_krea2.py` 与 `before_denoise.py` 等分阶段模块的设计，体现了组件化、可插拔的设计思想。  
- **fp16 精度处理**：在 Wan 流水线中强制 RoPE 模块保持 fp32，避免了混合精度训练/推理场景下的数值漂移，这是一个常见的精度稳定技巧。  
- **自动文档生成**：使用 `modular autodoc` 脚本自动生成 API 文档，减少手动维护工作量。  
- **内存卸载策略**：更新 `memory.py` 中的组卸载覆盖逻辑，处理可选组件（如 `transformer_2`）为 `None` 的情况，避免运行时错误。

---

### 5. 结合项目背景，这些提交如何影响项目发展
- **README 上下文**：虽然 README 仅包含 Apache License，但 Diffusers 项目文档始终强调其目标是 **“提供最先进的扩散模型流水线，易于使用且可扩展”**。  
- **发展影响**：  
  - Krea2 模块化支持直接响应社区对灵活、可组合流水线的需求，符合

## 详细提交记录

### [623213d](https://github.com/huggingface/diffusers/commit/623213d29f8323f4003ffc7d0eadf260ab5aec9d)

- **作者**: Cedric Perauer
- **时间**: 2026-07-23T17:27:48Z
- **提交信息**: Krea2 Modular Pipeline Support, Documentation, Test Cases (#14083)

* towards krea2 modular

* add test cases

* self-review fixes: test model id to hf internal, guider change

* remove pnd

* modular autodoc

* modular autodoc

* Update src/diffusers/modular_pipelines/krea2/modular_blocks_krea2.py

Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

* Update src/diffusers/modular_pipelines/krea2/before_denoise.py

Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

* Update docs/source/en/api/pipelines/krea2.md

Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

* input params, dim multiple of scale factor * patch

* docs for krea2 turbo modular

* docs fix

* Update tests/modular_pipelines/krea2/test_modular_pipeline_krea2.py

Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

* Update src/diffusers/modular_pipelines/krea2/before_denoise.py

Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

* modular blocks krea2 turbo fix

* Update docs/source/en/api/pipelines/krea2.md

Co-authored-by: YiYi Xu <yixu310@gmail.com>

* Update src/diffusers/modular_pipelines/krea2/before_denoise.py

Co-authored-by: YiYi Xu <yixu310@gmail.com>

* fix default height/width and inference time steps

* Apply suggestions from code review

Co-authored-by: YiYi Xu <yixu310@gmail.com>

* Regenerate stale krea2 auto docstrings

Co-Authored-By: Claude Fable 5 <noreply@anthropic.com>

---------

Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>
Co-authored-by: YiYi Xu <yixu310@gmail.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [af95be6](https://github.com/huggingface/diffusers/commit/af95be6bef717a4e11f2be272774a47bd4d4245d)

- **作者**: Wang, Yi
- **时间**: 2026-07-23T11:06:48Z
- **提交信息**: Fix Wan and Motif video pipeline fast test failures (#14269)

* Fix Wan and Motif video pipeline fast test failures

Description

This PR fixes several failing fast tests for Motif Video and Wan pipelines.

Changes

Updated test_motif_video.py to use a Motif-specific fp16 save/load tolerance.
T5Gemma2Encoder rebuilds non-persistent RoPE buffers after save/load, which introduces small fp16 numerical drift. The test now keeps coverage while allowing this expected drift.

Updated transformer_wan.py to keep Wan RoPE modules in fp32 during mixed precision handling.
This avoids fp16 precision drift in Wan save/load paths.

Updated memory.py group offloading coverage to include transformer_2 and skip None optional components.
This fixes Wan 2.2 memory/offloading tests where optional secondary transformers may be absent.

Updated stale expected slices in test_wan_image_to_video.py for:

TestWanImageToVideoPipeline::test_inference
TestWanFLFToVideoPipeline::test_inference

Signed-off-by: Wang, Yi A <yi.a.wang@intel.com>

* revert change in test_wan_image_to_video.py

Signed-off-by: Wang, Yi A <yi.a.wang@intel.com>

---------

Signed-off-by: Wang, Yi A <yi.a.wang@intel.com>
Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-07-24
**监控日期**: 2026-07-23
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 426
- **最后更新**: 2026-07-21T12:34:22Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-07-24
**监控日期**: 2026-07-23
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12749
- **最后更新**: 2026-07-23T16:16:13Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-07-24
**监控日期**: 2026-07-23
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 30674
- **最后更新**: 2026-07-23T21:55:42Z

## 提交统计

- **昨日提交总数**: 22
- **提交者数量**: 15
- **主要提交者**: Baizhou Zhang, Qiaolin Yu, Xiaoyu Zhang

## AI分析总结

好的，以下是对仓库 `sgl-project/sglang` 昨日提交记录的要点分析，结合项目背景（高性能 LLM 推理与服务框架）进行总结。

---

### 1. 主要更新类型
- **Bug 修复**：最多，涉及 Mamba 池、TRTLLM 后端、Mamba state corruption、nvfp4 量化、Mamba 命名空间、dist_init 检查、FPM 队列等。
- **功能新增**：`return_token_ids` API 支持、初始化 Rust Server 项目、DeepSeek V4 Megamoe 支持、MLX 配置处理。
- **性能优化**：Mamba 池 +1 padding slot 预留、DeepSeek V4 CP decode 优化、Spec decoding 调度优化（grammar overlap、decode retraction ordering）。
- **重构/基础设施**：创建 Rust workspace、Kernel 归并（sweep）、跳过不必要的测试。
- **文档更新**：Ascend 快速入门。
- **其他**：CI 修复、临时跳过特定测试。

---

### 2. 关键变更点及其与项目整体方向的关系
| 变更内容 | 与项目方向的关系 |
|----------|------------------|
| **`return_token_ids` API 支持** | 扩展了 completions/chat completions 接口的实用性，满足更细粒度的 token 级别输出需求，符合“易用性”目标。 |
| **初始化 Rust Server 项目** | 引入 Rust 高性能基础设施，为后期极致性能优化（如零拷贝、低延迟调度）铺路，符合“高性能”核心定位。 |
| **DeepSeek V4 Megamoe 支持 & CP decode 优化** | 强化对最新大模型架构（MegaMoE、Context Parallel）的支持，体现项目紧随前沿模型趋势。 |
| **Mamba 相关多个修复与优化** | 提升项目对新型状态空间模型（Mamba）的稳定性与内存效率，扩大支持的模型生态。 |
| **nvfp4 online scale 修复** | 修复最新 FP4 量化方案（nvfp4），推动低比特量化在推理中的实际可用性。 |
| **Spec decoding 调度优化** | 改善推测解码下的调度策略（grammar

## 详细提交记录

### [59ef3b1](https://github.com/sgl-project/sglang/commit/59ef3b15cc86eb64c48cd5e687a95dbefb872a29)

- **作者**: Liangsheng Yin
- **时间**: 2026-07-23T21:55:35Z
- **提交信息**: [Fix] Reserve the mamba pool's +1 padding slot in the memory budget solve (#32184)

### [3d0c6bf](https://github.com/sgl-project/sglang/commit/3d0c6bf57fd1a6ab9b4f1d8e26c71259a5206d2b)

- **作者**: Baizhou Zhang
- **时间**: 2026-07-23T21:55:18Z
- **提交信息**: [Fix] Fix trtllm_mla backend + fp8 kv cache without rope (#32181)

### [a0728ea](https://github.com/sgl-project/sglang/commit/a0728ea5026c782b00f13aa91a67d990b1ae649a)

- **作者**: Qiaolin Yu
- **时间**: 2026-07-23T21:52:30Z
- **提交信息**: [spec decoding] fix inkling multi layer mtp draft extend cuda graph (#32254)

### [ed26a11](https://github.com/sgl-project/sglang/commit/ed26a111b240f567c40b5294b1f7964d793f3091)

- **作者**: Baizhou Zhang
- **时间**: 2026-07-23T21:51:43Z
- **提交信息**: Revert "docker: install dynamo nightly in the dev image for rapid iteration/testing" (#32257)

### [20eb37a](https://github.com/sgl-project/sglang/commit/20eb37a2a10fb899e66b4837010eb10acba41e5c)

- **作者**: Rain Jiang
- **时间**: 2026-07-23T21:47:15Z
- **提交信息**: init sglang rust server project (#32256)

### [71fe41b](https://github.com/sgl-project/sglang/commit/71fe41b6b3c7f55f928468d6a38333ec2838fb77)

- **作者**: Siyuan Chen
- **时间**: 2026-07-23T21:46:32Z
- **提交信息**: [DSV4] Support megamoe for CP (#29569)

### [378aea1](https://github.com/sgl-project/sglang/commit/378aea138550853f27bed74f586008df269fffe2)

- **作者**: Qiaolin Yu
- **时间**: 2026-07-23T21:42:37Z
- **提交信息**: Fix nvfp4 online scale with pcg (#32246)

### [410ab4f](https://github.com/sgl-project/sglang/commit/410ab4fde5791ed7007c9b21a88e75d691e41f9d)

- **作者**: Jimmy Shong
- **时间**: 2026-07-23T21:41:52Z
- **提交信息**: Add return_token_ids support to completions and chat completions APIs (#30917)

### [ebe3ab2](https://github.com/sgl-project/sglang/commit/ebe3ab29e4853c26208e9b5d22997e4beda0f803)

- **作者**: Yongfei Xu
- **时间**: 2026-07-23T21:06:25Z
- **提交信息**: [DeepSeek V4] CP decode opt: slice repeat attention weights to local TP partition (#27657)

### [845f6ad](https://github.com/sgl-project/sglang/commit/845f6ad954cdf5bb29966e048a48eb4bf890f00e)

- **作者**: Calvin Chen
- **时间**: 2026-07-23T21:01:35Z
- **提交信息**: [MLX] Handle configs without quant_method in Humming (#31460)

Signed-off-by: calvin chen <120380290qq.com>
Co-authored-by: calvin chen <120380290qq.com>

### [a2ddf92](https://github.com/sgl-project/sglang/commit/a2ddf92e616c6b47f8a166aece71d3c0bc5976af)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-07-23T20:15:50Z
- **提交信息**: [CI] Fix Mamba ServerArgs namespace (#32211)

### [1f9d778](https://github.com/sgl-project/sglang/commit/1f9d778d1bcdef8ef9f53eb37a8ca0bd77759e55)

- **作者**: Sam Shleifer
- **时间**: 2026-07-23T19:40:41Z
- **提交信息**: Skip dist_init/nccl port prechecks when the dist init method is overridden (#31410)

### [7fe82dd](https://github.com/sgl-project/sglang/commit/7fe82dd02e17615fb8679479c9c48ffeb5efc1aa)

- **作者**: Rain Jiang
- **时间**: 2026-07-23T19:02:41Z
- **提交信息**: create rust workspace (#32014)

### [d0b9689](https://github.com/sgl-project/sglang/commit/d0b9689805232d8ab37789121cbc3b766b5c723e)

- **作者**: Hongkuan Zhou
- **时间**: 2026-07-23T16:30:27Z
- **提交信息**: [Fix] Include disagg prefill waiting queue in FPM (#32122)

Signed-off-by: hongkuanz <hongkuanz@nvidia.com>

### [b98a577](https://github.com/sgl-project/sglang/commit/b98a577fbef036c3bab5a9ee1fd01edc2af8386c)

- **作者**: Jinyan Yi
- **时间**: 2026-07-23T12:25:20Z
- **提交信息**: Doc/update ascend quickstart (#32205)

### [70ac0c4](https://github.com/sgl-project/sglang/commit/70ac0c4b0e8e832945c245d9fb0696f368e4aa19)

- **作者**: Jialin Ouyang
- **时间**: 2026-07-23T10:48:31Z
- **提交信息**: [UnifiedRadixCache][mamba] Fix mamba state corruption and slot leak when load_back aborts (#30986)

Co-authored-by: hzh0425 <hzh0425@apache.org>

### [c18919f](https://github.com/sgl-project/sglang/commit/c18919f8f37bb9cf4e98042aed11683debbe46b4)

- **作者**: YAMY
- **时间**: 2026-07-23T09:58:36Z
- **提交信息**: [Mamba] Add a per-path cap for cached states (#31230)

### [20f6a41](https://github.com/sgl-project/sglang/commit/20f6a416e740c18d8b40d8cadb479acdb6d6bfca)

- **作者**: Baizhou Zhang
- **时间**: 2026-07-23T09:54:58Z
- **提交信息**: [Tiny] Skip sm120 deepgemm test temporarily (#32193)

### [62aa85d](https://github.com/sgl-project/sglang/commit/62aa85d9aa2fabd339ee06077e09d3ce1ac4e608)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-07-23T09:07:16Z
- **提交信息**: [Kernel] Sweep missed dedicated kernels into kernels.ops (moe/quant siblings + dspark) (RFC #29630) (#32160)

Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>

### [f35411e](https://github.com/sgl-project/sglang/commit/f35411ee8149e815f76fd7d69b825c5b4df48a0b)

- **作者**: Liangsheng Yin
- **时间**: 2026-07-23T08:47:27Z
- **提交信息**: [Spec] Enable grammar overlap scheduling for STANDALONE speculative decoding (#32110)

### [5387e23](https://github.com/sgl-project/sglang/commit/5387e23ecd7dde4c383ae857983686e6a73bddf3)

- **作者**: Baizhou Zhang
- **时间**: 2026-07-23T08:13:14Z
- **提交信息**: [Tiny]Correct runner for testing deepgemm (#32174)

### [9b853e6](https://github.com/sgl-project/sglang/commit/9b853e6832e71a3058212df02a025232a453e146)

- **作者**: Liangsheng Yin
- **时间**: 2026-07-23T07:42:56Z
- **提交信息**: [Scheduler] Enable decode retraction ordering under speculative decoding (#32023)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-07-24
**监控日期**: 2026-07-23
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1235
- **最后更新**: 2026-07-23T04:23:29Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-07-24
**监控日期**: 2026-07-23
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 86991
- **最后更新**: 2026-07-23T22:12:55Z

## 提交统计

- **昨日提交总数**: 25
- **提交者数量**: 19
- **主要提交者**: Nicolò Lucchesi, Michael Goin, Andrey Talman

## AI分析总结

分析生成失败

## 详细提交记录

### [2659467](https://github.com/vllm-project/vllm/commit/26594674975cf68b4b33b329b9a9ad2d508bb243)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-07-23T21:49:53Z
- **提交信息**: [CI][PD] Add hybrid SSM P_TP>D_TP accuracy sweep entry (#49593)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [a49d37c](https://github.com/vllm-project/vllm/commit/a49d37c6b902036385fcfd87c9ed40320ac06490)

- **作者**: Andreas Karatzas
- **时间**: 2026-07-23T19:02:54Z
- **提交信息**: [CI] Disable reasoning in Responses smoke test (#49511)

Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>

### [4501a6d](https://github.com/vllm-project/vllm/commit/4501a6d56b2c45dd9d2af816bef631da50374828)

- **作者**: music-dino
- **时间**: 2026-07-23T19:01:36Z
- **提交信息**: [ROCm][CI] Language Models tests tiny-mixtral with aiter fix (#49551)

Signed-off-by: Dino Music <Dino.Music@amd.com>

### [e18f003](https://github.com/vllm-project/vllm/commit/e18f0037a5d54dc2ead5896af896305f2bf57496)

- **作者**: Michael Goin
- **时间**: 2026-07-23T18:30:50Z
- **提交信息**: [Bugfix][KV cache] Support sparse-MLA targets with SWA drafts (#48776)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [b354734](https://github.com/vllm-project/vllm/commit/b354734d17e04c66076f73511f14acde52dd81e3)

- **作者**: Wentao Ye
- **时间**: 2026-07-23T18:27:38Z
- **提交信息**: [Bug] Fix batch invariance rms norm comparison (#49603)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [b91a40e](https://github.com/vllm-project/vllm/commit/b91a40e7297919e0baf57bab185b9d73076aa121)

- **作者**: Chang Guo
- **时间**: 2026-07-23T18:26:03Z
- **提交信息**: [Bugfix] Restore structured output logger initialization (#49626)

Signed-off-by: Change72 <changg@nvidia.com>
Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>

### [75ccdf3](https://github.com/vllm-project/vllm/commit/75ccdf31458070501a7ca01eb1ac11728a0933fd)

- **作者**: Andrey Talman
- **时间**: 2026-07-23T18:09:36Z
- **提交信息**: [Core] Update PyTorch to 2.13.0, torchvision to 0.28.0, triton to 3.7.1 (#48155)

Signed-off-by: Andrey Talman <atalman@users.noreply.github.com>
Co-authored-by: Andrey Talman <atalman@users.noreply.github.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [c6fe94b](https://github.com/vllm-project/vllm/commit/c6fe94b4d5b418fa213af0e5884eddd304333dcd)

- **作者**: Andrey Talman
- **时间**: 2026-07-23T18:08:45Z
- **提交信息**: [CI] Bump PyTorch Compilation Unit Tests timeout to 150 min (#49606)

### [46f01a5](https://github.com/vllm-project/vllm/commit/46f01a50acd6862806ed67b88176c96c2b161142)

- **作者**: Nick Hill
- **时间**: 2026-07-23T17:26:02Z
- **提交信息**: [CI][Bugfix] Fix test isolation in block_int8/ptpc_fp8 MoE kernel tests (#49609)

Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [f00efc5](https://github.com/vllm-project/vllm/commit/f00efc52652046aac18dc37865adfa8f21fbdb10)

- **作者**: Andreas Karatzas
- **时间**: 2026-07-23T17:16:19Z
- **提交信息**: [CI] Isolate cudagraph tests in child processes (#49510)

Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>

### [b0cb1da](https://github.com/vllm-project/vllm/commit/b0cb1da1bde62a738baba33f1fbb1fcf906d29bc)

- **作者**: Wentao Ye
- **时间**: 2026-07-23T17:08:08Z
- **提交信息**: [DSv4 Perf] Skip topk and router when not needed, 3.4% E2E TTFT improvement for Decode case (#49486)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [0e36e3b](https://github.com/vllm-project/vllm/commit/0e36e3bbd1a55c5ac3602304031e7d7e86bf0ca0)

- **作者**: Andreas Karatzas
- **时间**: 2026-07-23T16:54:26Z
- **提交信息**: [CI] Use explicit devices in quantization tests (#49512)

Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>

### [494845e](https://github.com/vllm-project/vllm/commit/494845e79f8ae40f356902ba8ac181bf545603b5)

- **作者**: vllm-agent
- **时间**: 2026-07-23T16:51:33Z
- **提交信息**: Revert "[MRV2] Always build attn metadata at capture time" (#49364) (#49451)

Co-authored-by: vllm-agent CI bot <ci-bot@vllm-agent.local>

### [0416dab](https://github.com/vllm-project/vllm/commit/0416dab275d51327b331a1c6baaec754a68d7764)

- **作者**: yue.yu
- **时间**: 2026-07-23T16:14:15Z
- **提交信息**: [Bugfix][Structured Output][Spec Decode] Advance grammar across reasoning boundary (#44993)

Signed-off-by: Allen.Yu <yuyue0225sc@163.com>

### [c8db00b](https://github.com/vllm-project/vllm/commit/c8db00b16cc188b46b7b9517a5836a0da4aa8c3e)

- **作者**: vllmellm
- **时间**: 2026-07-23T13:59:48Z
- **提交信息**: Fix GPTQ quantized Qwen3.5 MTP weight loading with spec decode (#48816)

Signed-off-by: vllmellm <vllm.ellm@embeddedllm.com>
Co-authored-by: TJian <tunjian.tan@embeddedllm.com>
Co-authored-by: noobHappylife <64898326+noobHappylife@users.noreply.github.com>

### [80c7683](https://github.com/vllm-project/vllm/commit/80c7683923795e9c2e8929fb8b766aecb0a63447)

- **作者**: Guan-Ming Chiu
- **时间**: 2026-07-23T13:58:50Z
- **提交信息**: [Perf] Defer MM embeds loading off the event loop (#49477)

Signed-off-by: Guan-Ming (Wesley) Chiu <105915352+guan404ming@users.noreply.github.com>

### [638d6e9](https://github.com/vllm-project/vllm/commit/638d6e97575c49f7e0aa128ae1e775892c92bb1c)

- **作者**: Nikhil Kulkarni
- **时间**: 2026-07-23T12:25:14Z
- **提交信息**: [Bugfix][CI/Build] Fix Plamo2 HF runner crash on transformers v5 (_tied_weights_keys list→dict) (#44239)

Signed-off-by: Nikhil Kulkarni <nikhilkulkarni1755@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [1ad84fe](https://github.com/vllm-project/vllm/commit/1ad84fea866bc478942efa8550036ffa52a51283)

- **作者**: Junpu Yu
- **时间**: 2026-07-23T10:14:06Z
- **提交信息**: [Bugfix][Spec Decode] Select earliest-completing stop string in check_stop_strings (#49391)

Signed-off-by: Junpu Yu <davidyu@nvidia.com>

### [12213c6](https://github.com/vllm-project/vllm/commit/12213c67951b71cd6d750cc059a87a53641e8730)

- **作者**: zhrrr
- **时间**: 2026-07-23T10:13:49Z
- **提交信息**: [Bugfix] handle grammar compilation failures to avoid engine crash (#47312)

Signed-off-by: zhuhaoran <zhuhaoran.zhr@alibaba-inc.com>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>

### [10c7547](https://github.com/vllm-project/vllm/commit/10c75477b07c2f1a361f54b7357af1019bba5fd8)

- **作者**: chaeminlim-mb
- **时间**: 2026-07-23T10:13:29Z
- **提交信息**: [Bugfix][Core] shm_broadcast: bound idle reader waits and release read slots (#45224)

Signed-off-by: Chaemin Lim <chaemin.lim@mangoboost.io>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Edwin Lim <edwin.lim@mangoboost.io>
Co-authored-by: Jaeyoun Kim <jaeyoun.kim@mangoboost.io>
Co-authored-by: Nick Hill <nickhill123@gmail.com>

### [ac36a7a](https://github.com/vllm-project/vllm/commit/ac36a7a1e7eb8f03f9ec2b6bf643f1002b205794)

- **作者**: Michael Goin
- **时间**: 2026-07-23T10:13:13Z
- **提交信息**: [MRV2][Spec Decode] Avoid rejection sampler OOM by chunking (#48630)

Signed-off-by: mgoin <mgoin64@gmail.com>
Signed-off-by: Michael Goin <mgoin64@gmail.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>

### [521aa80](https://github.com/vllm-project/vllm/commit/521aa80f719bb11bf973d2d51873ca966afe373d)

- **作者**: Nick Hill
- **时间**: 2026-07-23T10:12:46Z
- **提交信息**: [Core] Simplify KVBlockZeroer index tensor handling (#48399)

Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [a76df87](https://github.com/vllm-project/vllm/commit/a76df87db89bb87213f60cff817d5789796ee158)

- **作者**: Dao007forever
- **时间**: 2026-07-23T10:12:28Z
- **提交信息**: [MooncakeStore] Re-derive full external hits on stored boundaries (#49481)

Signed-off-by: Dao Le <Dao007forever@gmail.com>
Signed-off-by: Yifan Qiao <yifanqiao@inferact.ai>
Co-authored-by: Yifan Qiao <yifanqiao@inferact.ai>
Co-authored-by: Claude <noreply@anthropic.com>

### [a4904ba](https://github.com/vllm-project/vllm/commit/a4904ba9032af87610965ba7c90267bf7b21b425)

- **作者**: Summer Yang
- **时间**: 2026-07-23T10:12:00Z
- **提交信息**: [Perf][KVConnector][Mooncake] Vectorize prepare_value on the KV load path (#48531)

Signed-off-by: girasoley <girasoley@inferact.ai>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: girasoley <girasoley@inferact.ai>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [f83de6d](https://github.com/vllm-project/vllm/commit/f83de6d44c2473656f95357900d53f1b7401d21c)

- **作者**: Rehan Khan
- **时间**: 2026-07-23T07:17:24Z
- **提交信息**: [CPU][Docs] Update docs and dockerfile for s390x (#49523)

Signed-off-by: Rehan Khan <Rehan.Khan7@ibm.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-07-24
**监控日期**: 2026-07-23
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 5663
- **最后更新**: 2026-07-23T17:17:08Z

## 提交统计

- **昨日提交总数**: 7
- **提交者数量**: 5
- **主要提交者**: Joshna-Medisetty, psv666, Sy03

## AI分析总结

以下是针对 `vllm-omni` 仓库昨日提交记录的分析总结，结合了项目背景（**易用、快速、低成本的全模态模型服务**）：

---

### 1. 主要更新类型
- **功能新增**：全双工实时运行时支持 + MiniCPM-o 4.5 演示（#3907）
- **模型适配**：MiniCPM-o 4.5 TTS 模型加载路径优化（#5301）
- **Bug 修复**：XPU 平台内存释放异常与推测步数崩溃修复（#5330）；Docker 缓存导致的 CLI 导入问题（#5341）
- **重构**：服务基准测试 CLI 拆分（#5206）；指标相关辅助函数集中化（#5168）
- **CI 稳定性**：将 Krea-2 扩展移至慢速测试，跳过失败的 README 代码片段（#5347）

---

### 2. 关键变更点及与项目方向的关系
| 变更点 | 与项目方向的关系 |
|--------|------------------|
| **全双工实时运行时**（Full-Duplex realtime runtime） | 直接支撑“模态服务”的**实时交互能力**，使模型能够同时收发音频/视频流，贴合“易用、快速、低成本”中**快速**（低延迟）的核心诉求。 |
| **MiniCPM-o 4.5 演示集成**（含 TTS 路径修复） | 增加对**多模态模型**（特别是端到端语音/视觉模型）的支持，丰富了项目支持的模型生态，使用户能直接体验多模态推理。 |
| **XPU 平台 Bug 修复** | 保证在 **Intel XPU（国产/加速器）** 上的稳定性，**扩展硬件兼容性**，降低多模态服务在不同硬件上的部署门槛。 |
| **指标系统集中化**（metrics/） | 提升服务**可观测性**，便于监控多模态模型在多种硬件上的性能指标，符合“低成本”中**运维友好**的需求。 |
| **CLI 拆分与 CI 优化** | 改善开发体验（重构）与测试可靠性（CI），间接降低社区贡献门槛，推动项目快速迭代。 |

---

### 3. 对项目的影响和潜在意义
- **实时多模态交互成为可能**：全双工运行时是本次最重要的新增能力，意味着 `vllm-omni` 可以从纯“请求-响应”模式升级为**双工流式对话**，如实时语音对话、视频理解等场景。这直接提升了项目在**对话式AI、音视频助手**等应用中的价值。
- **MiniCPM-o 4.5 的落地示范**：该模型是多模态领域的新秀，集成后能吸引更多关注多模态的开发者与用户，促进社区和生态扩展。
- **基础设施成熟

## 详细提交记录

### [0fe5d73](https://github.com/vllm-project/vllm-omni/commit/0fe5d73a6365893c981398de576e8d20f22f9c19)

- **作者**: Joshna-Medisetty
- **时间**: 2026-07-23T17:17:00Z
- **提交信息**: [Bugfix][XPU] Fix free-memory abort and num_speculative_steps crash on XPU (#5330)

Signed-off-by: Joshna Medisetty <joshna.medisetty@intel.com>
Co-authored-by: Chendi.Xue <chendi.xue@intel.com>

### [4c23a31](https://github.com/vllm-project/vllm-omni/commit/4c23a3164b98fecf63d2d28b87bc4ffad8853bdf)

- **作者**: ZacheryAU
- **时间**: 2026-07-23T16:00:32Z
- **提交信息**: [Refactor] Split vllm_omni/entrypoints/cli/benchmark/serve.py (#5206)

### [7789597](https://github.com/vllm-project/vllm-omni/commit/778959797c5c454f58606dd4b25ff7947d6fd863)

- **作者**: ZacheryAU
- **时间**: 2026-07-23T15:55:05Z
- **提交信息**: [Refactor] Centralize metrics related helpers to metrics/ (#5168)

### [e9a06d5](https://github.com/vllm-project/vllm-omni/commit/e9a06d5bdc5dae249ca0a1c1ce195bc0a974ce76)

- **作者**: wangyu
- **时间**: 2026-07-23T14:15:52Z
- **提交信息**: [CI/Bugfix] Fix empty vllm_omni stub breaking stage CLI imports after Docker cache (#5338) (#5341)

Signed-off-by: wangyu <410167048@qq.com>

### [f72b381](https://github.com/vllm-project/vllm-omni/commit/f72b38184b8ea0a9b9eb7253173634a1a82751ed)

- **作者**: wangyu
- **时间**: 2026-07-23T13:47:58Z
- **提交信息**: [CI] move Krea-2 expansion to slow and skip failing README snippets (#5347)

Signed-off-by: wangyu <410167048@qq.com>

### [05b794f](https://github.com/vllm-project/vllm-omni/commit/05b794f29b02096eba17801d7e2d99911640085e)

- **作者**: Sy03
- **时间**: 2026-07-23T08:45:18Z
- **提交信息**: [Full Duplex] Feat: Support Full-Duplex realtime runtime & add MiniCPM-o 4.5 demo (#3907)

Signed-off-by: Sy03 <1370724210@qq.com>
Signed-off-by: lishunyang12 <lishunyang03@gmail.com>
Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: lishunyang12 <lishunyang03@gmail.com>
Co-authored-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: StormMelody <22371184@zju.edu.cn>
Co-authored-by: Gao Han <hgaoaf@connect.ust.hk>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [b55120c](https://github.com/vllm-project/vllm-omni/commit/b55120c93b868e8f8c4c34c8e26cb68c2c638340)

- **作者**: psv666
- **时间**: 2026-07-23T08:05:54Z
- **提交信息**: [Model][MiniCPM-o 4.5] Resolve Hugging Face model ID to local cache path in TTS (#5301)

Signed-off-by: psv666 <2693925048@qq.com>

---
