# GitHub Stars 合并报告 - 2026-04-03

**合并日期**: 2026-04-04
**监控日期**: 2026-04-03
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


**报告日期**: 2026-04-04
**监控日期**: 2026-04-03
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 1793
- **最后更新**: 2026-04-03T11:15:44Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-04-04
**监控日期**: 2026-04-03
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Light Image Video Generation Inference Framework
- **语言**: Python
- **星标数**: 2134
- **最后更新**: 2026-04-03T17:37:32Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: PengGao

## AI分析总结

根据提供的提交记录和README摘要，以下是针对昨日更新的分析总结：

### 1. 主要更新类型
- **重构与优化**：本次提交（`fix(rs2v_infer)`）主要是一次**重构**和**性能优化**。它通过模块化音频和视频片段处理逻辑，提升了代码的可维护性和执行效率。

### 2. 关键变更点及其与项目整体方向的关系
- **模块化处理**：将音频和视频片段处理逻辑进行模块化重构。
- **性能优化**：优化了处理流程，可能减少了资源消耗或提高了处理速度。
- **关系**：这与项目 **LightX2V** 作为“轻量级视频生成推理框架”的核心目标高度一致。项目强调“⚡️ Light”（轻量、快速），因此优化推理流程、提升效率是直接服务于项目“高效、轻量”的整体方向。

### 3. 对项目的影响和潜在意义
- **积极影响**：
    - **可维护性提升**：模块化使代码结构更清晰，便于后续功能扩展和团队协作。
    - **推理性能增强**：优化可能直接带来更快的视频生成速度或更低的硬件资源需求，改善用户体验。
    - **稳定性基础**：重构往往伴随着潜在Bug的修复，能提高系统稳定性。
- **潜在意义**：为未来集成更复杂的音频-视频处理功能或支持更多模型变体奠定了更健壮的代码基础。

### 4. 值得关注的技术点
- **音频与视频处理的解耦与模块化**：如何设计接口将音视频处理流程分离，是实现高效、灵活推理框架的关键技术点。
- **优化策略**：具体优化了哪些环节（如I/O、内存管理、计算图）未在日志中明说，但这是提升“轻量”框架性能的核心。

### 5. 基于项目背景的提交影响分析
- **README背景**：LightX2V定位为**轻量级视频生成推理框架**，注重**高效部署和快速推理**。
- **影响分析**：
    1. **强化核心优势**：此次优化直接作用于推理管线（`rs2v_infer`），通过提升处理效率，进一步巩固了其“轻量、快速”的框架特性。
    2. **提升开发者体验**：模块化代码更易于理解和二次开发，有助于吸引社区贡献，促进项目生态发展。
    3. **面向实际应用**：性能优化意味着在同等硬件条件下能实现更快的生成速度或处理更长的视频，增强了框架在生产环境中的实用性和竞争力。

**总结**：这是一次紧扣项目核心目标（轻量、高效）的实质性代码改进，虽未增加新功能，但通过重构和优化夯实了基础，对项目的长期健康发展和技术竞争力有积极影响。

## 详细提交记录

### [7216292](https://github.com/ModelTC/LightX2V/commit/7216292de236447480d936e2dcaa7084dab48147)

- **作者**: PengGao
- **时间**: 2026-04-03T09:54:53Z
- **提交信息**: fix(rs2v_infer): modularize and optimize audio and video segment processing (#987)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-04-04
**监控日期**: 2026-04-03
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 1996
- **最后更新**: 2026-04-03T17:47:03Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-04-04
**监控日期**: 2026-04-03
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5268
- **最后更新**: 2026-04-03T23:00:32Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 4
- **主要提交者**: Brian K. Ryu, Zihao Ye, Jonathan Dierksen

## AI分析总结

根据FlashInfer仓库的README摘要（这是一个专注于**高性能GPU推理内核**的项目）以及昨日的提交记录，以下是分析总结：

### 1. 主要更新类型
昨日提交主要为 **Bug修复** 和 **测试优化**。
- **Bug修复 (2项)**：修复了可能导致死锁的优化和重复下载问题。
- **测试优化 (2项)**：针对特定硬件/软件环境（SM12x、Blackwell GPU、CUDA 12.9）调整了测试策略，以提高测试套件的稳定性和可靠性。

### 2. 关键变更点及其与项目整体方向的关系
| 提交 | 关键变更点 | 与项目方向的关系 |
| :--- | :--- | :--- |
| **5758837** | **回退一项在Blackwell Ultra GPU上的FMHA优化**，因该优化导致了死锁。 | 项目核心是提供**稳定、高性能的推理内核**。此修复直接确保了核心功能（注意力机制）在最新硬件上的**可靠性**，这是高性能库的基石。 |
| **e0f3729** | **优化构建/启动流程**，避免在已安装`flashinfer-cubin`时重复下载BMM头文件。 | 提升**开发者/用户体验**和部署效率。减少不必要的网络请求和构建时间，使库更易于集成和使用，符合开源高性能库的易用性目标。 |
| **582bd7b** | **在SM12x GPU上跳过不支持的`mm_mxfp8`测试配置**。 | 确保测试套件能**准确反映不同硬件后端的支持情况**。这有助于维护清晰的兼容性矩阵，避免因测试错误而误导用户或开发者。 |
| **fc5441a** | **将Blackwell GPU + CUDA 12.9上cuDNN FP8预填充测试标记为预期失败**。 | **主动管理已知的第三方依赖问题**。这避免了因上游（cuDNN）未修复的bug导致CI失败，维护了测试的“绿色”状态和开发流程的顺畅。 |

### 3. 对项目的影响和潜在意义
- **稳定性提升**：修复死锁和优化资源下载，直接提升了库在**生产环境中的稳定性和部署效率**。
- **兼容性管理更清晰**：测试的调整使项目对**新一代GPU硬件（Blackwell, SM12x）的兼容性支持**更加明确和稳健，降低了用户在不同平台上的使用门槛和困惑。
- **开发者体验优化**：减少重复下载和妥善处理已知测试失败，使得**CI/CD流程更可靠**，内部开发和外部贡献体验更顺畅。

### 4. 值得关注的技术点
- **硬件特定优化与陷阱**：提交`5758837`揭示了对**Blackwell Ultra架构**进行极致性能优化时可能引入的并发问题（死锁），体现了在硬件前沿探索的复杂性。
- **混合精度支持与生态兼容**：提交`582bd7b`和`fc5441a`涉及**MXFP8和FP8**这两种用于推理的重要低精度格式，以及它们与CUTLASS、cuDNN等不同计算后端的交互，反映了项目在**高效利用新硬件算力**的同时，需要处理复杂的软件生态兼容性问题。
- **构建与分发优化**：提交`e0f3729`展示了对**Python wheel包 (`flashinfer-cubin`)** 安装流程的精细优化，通过统一资源获取和利用符号链接，提升了库的封装水平和用户体验。

### 5. 基于项目背景的提交影响分析
FlashInfer的目标是提供**行业领先的高性能GPU推理内核**。昨日的提交虽未直接增加新功能或大幅提升性能，但至关重要：
- **巩固基础**：通过修复关键bug和优化资源管理，**强化了项目的可靠性和专业性**，这是高性能底层库赢得信任的关键。
- **拥抱新硬件**：多项提交围绕**Blackwell和SM12x**等NVIDIA最新GPU架构进行调整，表明项目正积极**适配前沿硬件**，确保其内核在未来平台上继续保持性能领先地位。
- **完善开发生态**：通过精细化测试管理和构建优化，项目在追求极致性能的同时，也在**构建一个健壮、友好的开发者生态**，这有助于吸引更多贡献者和用户，形成良性循环。

**总结**：昨日更新是一次以**稳定性和兼容性**为核心的“夯实基础”行动。在快速迭代的高性能计算领域，FlashInfer通过这些提交确保了其在最新硬件平台上的核心功能稳定可靠，并优化了开发和部署体验，为其长期发展和技术领先地位奠定了更坚实的基础。

## 详细提交记录

### [5758837](https://github.com/flashinfer-ai/flashinfer/commit/5758837a8594c15aaae14e4e638fa4e634632c53)

- **作者**: Perkz Zheng
- **时间**: 2026-04-03T23:00:26Z
- **提交信息**: fix: [Fmha] revert blackwell ultra optimization that causes deadlocks. (#2956)

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

## Release Notes

* **Chores**
* Updated TRTLLM GEN FMHA artifact references and associated checksums
used for download and verification.

* **Refactor**
* Improved kernel tile-shape handling for paged K/V cache and refined
scaling-factor tensor layout to optimize TMA transfers and memory access
patterns.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [582bd7b](https://github.com/flashinfer-ai/flashinfer/commit/582bd7b7c1e8271f0d1dd09bf3161a58be23450a)

- **作者**: Brian K. Ryu
- **时间**: 2026-04-03T22:41:15Z
- **提交信息**: test: skip unsupported mm_mxfp8 configurations on SM12x (#2974)

<!-- .github/pull_request_template.md -->

## 📌 Description

- On SM12x GPUs, only the CUTLASS backend is available for `mm_mxfp8`,
and it requires 1D swizzled scales (`SfLayout.layout_128x4`). The
`trtllm` and `cute-dsl` backends do not support SM12x at all.
- The backend requirement checks in `gemm_base.py` already enforce this
correctly, but several test cases in `test_mm_mxfp8.py` were not
skipping these unsupported configurations, causing them to hit
`BackendSupportedError` / `ValueError` instead of being gracefully
skipped.
- Add SM12x skip guards to `_run_mm_mxfp8`,
`test_mm_mxfp8_find_minimum_cosine_similarity`, and
`test_mm_mxfp8_scale_contiguity_requirement` so that non-swizzled scale
layout tests are skipped on SM12x.

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

## 🔍 Related Issues

#2902

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

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

## Tests

* Improved test reliability by adding runtime CUDA compute capability
detection for SM12x GPUs, with conditional skips for non-swizzled scale
layouts across multiple test cases.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [fc5441a](https://github.com/flashinfer-ai/flashinfer/commit/fc5441a5ab9dc659f1543ddeeb7cabeec2023bb6)

- **作者**: Jonathan Dierksen
- **时间**: 2026-04-03T20:34:59Z
- **提交信息**: test: xfail cuDNN FP8 prefill on Blackwell with CUDA <= 12.9 (#2963)

Known cuDNN bug causes test_cudnn_prefill_fp8 to fail on Blackwell
(SM100) systems with CUDA 12.9. Mark as expected failure until the cuDNN
fix is available.

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

- [ ] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Tests**
* Marked a specific hardware/compute-capability scenario in the test
suite as an expected failure, causing the test to exit early on affected
systems and improving overall test stability.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 4.6 (1M context) <noreply@anthropic.com>

### [e0f3729](https://github.com/flashinfer-ai/flashinfer/commit/e0f3729b4b5ff6f564989a7f74e39c94a015ed8a)

- **作者**: Zihao Ye
- **时间**: 2026-04-03T12:24:57Z
- **提交信息**: fix: avoid re-downloading BMM export headers when flashinfer-cubin is installed (#2903)

## Summary
- `download_trtllm_headers()` stored BMM export headers at a custom path
(`CUBIN_DIR/flashinfer/trtllm/batched_gemm/trtllmGen_bmm_export/`), but
`download_artifacts()` (used when building the flashinfer-cubin wheel)
stores them at the canonical artifact hash path. The separate
`get_file()` function only checked the destination path, so it never
found the pre-packaged files and always re-downloaded ~17 header files
from the network on every startup (×2 for each TP worker).
- Remove `download_trtllm_headers()`, `get_file()`, and rename
`get_cubin()` → `get_artifact()`. Two unified primitives remain:
- **`get_artifact(name, sha256)`** — fetches any artifact (cubins,
headers, checksums, metainfo) into the canonical path, reusing
flashinfer-cubin files when available
- **`ensure_symlink(link, target)`** — maps C++ include paths to the
artifact directory
- Callers (fused_moe, moe_utils) use these two primitives directly. A
`get_cubin = get_artifact` alias is kept for backward compatibility.

## Related issue
- vllm-project/vllm#38110

## Test plan
- [x] 7 unit tests covering `get_artifact()` local cache (cubins,
checksums.txt, metainfo headers, sha256 mismatch) and the BMM header
symlink pattern (no download, stale dir replacement, idempotent)
- [ ] Verify on a gpt-oss-20b-sm100-fi-mxfp4-mxfp8-trtllm run with
flashinfer-cubin installed that "Fetching file from" log messages no
longer appear

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Claude Opus 4.6 (1M context) <noreply@anthropic.com>
Co-authored-by: Alex Yang <aleyang@nvidia.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-04-04
**监控日期**: 2026-04-03
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3342
- **最后更新**: 2026-04-03T12:43:25Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-04-04
**监控日期**: 2026-04-03
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 33253
- **最后更新**: 2026-04-03T22:45:39Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 2
- **主要提交者**: Sayak Paul, sippycoder

## AI分析总结

根据提供的提交记录和项目背景（Diffusers库是一个用于扩散模型的Python库），以下是昨日更新的分析总结：

---

### 1. **主要更新类型**
- **文档更新**：提交1和2主要更新了性能分析（profiling）指南的README，增加了详细的使用示例和工作流程说明。
- **功能新增**：提交3新增了**NucleusMoE-Image模型**及相关组件（如文本KV缓存、SwiGLUExperts等），属于重要的模型扩展。

---

### 2. **关键变更点及其与项目整体方向的关系**
- **性能分析工具完善**：通过提交1和2，强化了库的**性能优化工具链**，帮助用户分析和优化扩散模型推理流程（如CUDA图、`torch.compile`集成）。这与项目“高效、可扩展的扩散模型库”的目标一致。
- **新模型集成**：提交3引入了**NucleusMoE-Image**（一种基于混合专家MoE的图像生成模型），并配套实现了**文本KV缓存机制**和**SwiGLUExperts**优化。这体现了项目持续集成前沿模型架构、提升生成效率的方向。

---

### 3. **对项目的影响和潜在意义**
- **提升开发者体验**：详尽的性能分析文档降低了用户优化模型的门槛，可能吸引更多开发者进行性能调优。
- **扩展模型生态**：NucleusMoE-Image的加入丰富了Diffusers支持的模型类型，特别是MoE架构可能为高参数规模模型提供更高效的推理路径。
- **技术债务管理**：提交3中重构了文本KV缓存的管理方式（改为由`StateManager`统一管理），提高了代码可维护性。

---

### 4. **值得关注的技术点**
- **CUDA图与`torch.compile`集成**：性能分析指南中强调了这些PyTorch新特性，可用于减少内核启动开销，提升推理速度。
- **文本KV缓存机制**：通过缓存注意力层的键值对，避免重复计算，显著加速文本条件生成（尤其适用于多步生成或长文本）。
- **SwiGLUExperts融合**：在MoE模型中采用SwiGLU激活函数，可能提升模型表达能力并降低计算开销。

---

### 5. **基于项目背景的提交影响分析**
- **强化工具链完整性**：Diffusers不仅提供模型实现，还致力于成为端到端的扩散模型解决方案。性能分析工具的完善直接支持了用户从实验到部署的完整流程。
- **拥抱前沿架构**：集成MoE模型符合社区对高效大模型的需求，有助于Diffusers在文本到图像生成领域保持竞争力。
- **优化实践导向**：通过文档和示例强调性能优化（如缓存、编译），引导用户在生产环境中高效使用库，符合开源项目降低应用门槛的长期目标。

---

**总结**：昨日更新以**文档完善**和**新模型集成**为主，既提升了工具链的实用性，又扩展了模型覆盖范围。这些变更紧密围绕Diffusers的核心目标——提供**高效、易用、前沿**的扩散模型库，进一步巩固了其在生成式AI生态中的工具链地位。

## 详细提交记录

### [fbe8a75](https://github.com/huggingface/diffusers/commit/fbe8a75ad59fe5c0eec7f3691d2eb0ed890a0c90)

- **作者**: Sayak Paul
- **时间**: 2026-04-03T16:54:27Z
- **提交信息**: Update README.md of the profiling guide (#13400)

Update README.md

### [b114620](https://github.com/huggingface/diffusers/commit/b114620d85027a6a18dda4ae2d51078e6fe7954a)

- **作者**: Sayak Paul
- **时间**: 2026-04-03T14:13:01Z
- **提交信息**: Add examples on how to profile a pipeline (#13356)

* add a profiling worflow.

* fix

* fix

* more clarification

* add points.

* up

* cache hooks

* improve readme.

* propagate deletion.

* up

* up

* wan fixes.

* more

* up

* add more traces.

* up

* better title

* cuda graphs.

* up

* Apply suggestions from code review

Co-authored-by: Steven Liu <59462357+stevhliu@users.noreply.github.com>

* add torch.compile link.

* approach -> How the tooling works

* table

* unavoidable gaps.

* make important

* note on regional compilation

* Apply suggestions from code review

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

* make regional compilation note clearer.

* Apply suggestions from code review

Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

* clarify scheduler related changes.

* Apply suggestions from code review

Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

* Update examples/profiling/README.md

Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

* up

* formatting

* benchmarking runtime

* up

* up

* up

* up

* Update examples/profiling/README.md

Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

---------

Co-authored-by: Steven Liu <59462357+stevhliu@users.noreply.github.com>
Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

### [447e571](https://github.com/huggingface/diffusers/commit/447e571ada565992ea150ad01ac9e335b26b33d1)

- **作者**: sippycoder
- **时间**: 2026-04-03T09:01:13Z
- **提交信息**: NucleusMoE-Image (#13317)

* adding NucleusMoE-Image model

* update system prompt

* Add text kv caching

* Class/function name changes

* add missing imports

* add RoPE credits

* Update src/diffusers/models/transformers/transformer_nucleusmoe_image.py

Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

* Update src/diffusers/models/transformers/transformer_nucleusmoe_image.py

Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

* Update src/diffusers/models/transformers/transformer_nucleusmoe_image.py

Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

* Update src/diffusers/models/transformers/transformer_nucleusmoe_image.py

Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

* update defaults

* Update src/diffusers/pipelines/nucleusmoe_image/pipeline_nucleusmoe_image.py

Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

* review updates

* fix the tests

* clean up

* update apply_text_kv_cache

* SwiGLUExperts addition

* fuse SwiGLUExperts up and gate proj

* Update src/diffusers/hooks/text_kv_cache.py

Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

* Update src/diffusers/hooks/text_kv_cache.py

Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

* Update src/diffusers/hooks/text_kv_cache.py

Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

* Update src/diffusers/hooks/text_kv_cache.py

Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

* Update src/diffusers/models/transformers/transformer_nucleusmoe_image.py

Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

* Update src/diffusers/models/transformers/transformer_nucleusmoe_image.py

Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

* _SharedCacheKey -> TextKVCacheState

* Apply style fixes

* Run python utils/check_copies.py --fix_and_overwrite
python utils/check_dummies.py --fix_and_overwrite

* Apply style fixes

* run `make fix-copies`

* fix import

* refactor text KV cache to be managed by StateManager

---------

Co-authored-by: Murali Nandan Nagarapu <nmn@withnucleus.ai>
Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>
Co-authored-by: github-actions[bot] <github-actions[bot]@users.noreply.github.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-04-04
**监控日期**: 2026-04-03
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 388
- **最后更新**: 2026-04-03T21:47:41Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-04-04
**监控日期**: 2026-04-03
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12165
- **最后更新**: 2026-04-03T22:20:59Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-04-04
**监控日期**: 2026-04-03
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 25393
- **最后更新**: 2026-04-03T23:16:13Z

## 提交统计

- **昨日提交总数**: 31
- **提交者数量**: 25
- **主要提交者**: Ke Bao, Lianmin Zheng, monkeyLoveding

## AI分析总结

根据提供的提交记录和README摘要（SGLang是一个用于大语言模型推理的框架），以下是昨日更新的分析总结：

### 1. 主要更新类型
- **Bug修复**：占主导，涉及生成控制、注意力机制、端口绑定、缓存清理等多个核心模块。
- **功能新增/调整**：包括评分API、JIT内核激活、AMD/NPU硬件支持优化、扩散模型修复等。
- **性能优化**：针对特定硬件（AMD、NPU）的kernel优化和缓存策略。
- **CI/CD与测试**：持续集成流程改进、测试套件验证、环境超时调整。
- **代码质量与重构**：代码清理、依赖管理、注释修复。
- **版本管理**：内核版本升级至0.4.1。
- **临时措施**：因稳定性问题**回退了三项功能**（JIT激活、NVFP4回退、温度+softmax融合），并跳过了特定GPU上的TRTLLM注意力。

### 2. 关键变更点及其与项目方向的关系
| 关键变更点 | 与项目方向的关系 |
| :--- | :--- |
| **多项回退与跳过**：因稳定性/性能问题临时撤销或规避新功能。 | 体现了项目在**快速迭代中优先保证系统稳定性**，符合生产级推理框架对可靠性的高要求。 |
| **多硬件支持深化**：针对AMD（MI300/MI355）、NPU、特定CPU阶段的优化与CI支持。 | 强化了SGLang作为**跨硬件推理框架**的定位，致力于扩大其部署生态。 |
| **核心引擎与API增强**：实现`EngineScoreMixin`、修复`pause_generation`逻辑。 | 提升了框架的**功能完备性**（如评分）和**控制精细度**（生成流程控制），增强开发者体验。 |
| **内核与后端优化**：FlashAttention懒加载、MoE模型图捕获修复、CUDA图重放问题修复。 | 持续优化**推理性能与正确性**，这是推理框架的核心竞争力。 |

### 3. 对项目的影响和潜在意义
- **稳定性优先**：大量修复和回退表明团队正在处理高速开发中引入的复杂问题，旨在为下一个稳定版本打下基础。
- **生态扩展**：对AMD、NPU的持续投入表明项目正积极拥抱多元算力，降低用户部署门槛，提升市场竞争力。
- **内部质量提升**：CI流程的完善和代码清理有助于提升长期维护效率和代码健康度。
- **用户影响**：普通用户可能暂时无法使用部分新特性（因回退），但能获得更稳定的体验。AMD/NPU用户将直接受益于性能提升。

### 4. 值得关注的技术点
- **JIT内核激活**（#21766被回退#22078，后又重新提交#22044？需核实）：这项功能旨在通过即时编译提升性能，其反复调整值得关注。
- **AMD FP8 KV缓存与注意力**：利用FP8精度和TileLang后端，是追求极致推理性能的前沿尝试。
- **HiSparse后端限制**：明确其仅适用于DSA模型，体现了对不同稀疏化策略的精细化支持。
- **多模态处理重构**：用`MultimodalProcessorOutput`替换字典，可能意味着多模态API正朝着更结构化、类型安全的方向发展。

### 5. 基于项目背景的更新影响分析
SGLang的目标是提供“用于LLM推理的协程式编程框架和运行时系统”。昨日的更新紧密围绕这一目标：
- **强化运行时可靠性**：大量内核、后端和引擎层的Bug修复直接提升了**运行时系统**的健壮性，这是框架可用性的基石。
- **拓展与优化后端**：对TRT-LLM、FlashAttention、AMD、NPU等后端的修复和优化，丰富了**运行时系统**的硬件支持与性能表现。
- **完善开发者工具链**：CI/CD改进、测试验证、版本发布提示等，提升了框架本身的开发效率和交付质量。
- **探索新特性边界**：对JIT、评分API、稀疏化等的尝试，即使有回退，也显示了项目在**编程模型和功能**上的积极探索，以保持技术领先性。

**总结**：昨日更新是一次以**稳定性修复和生态夯实**为主的密集提交。在积极向多硬件平台拓展并尝试性能突破的同时，团队展现出对生产环境稳定性的高度审慎。这符合一个成熟推理框架在快速发展期的典型特征：在创新与稳定之间寻找平衡，为更广泛、更可靠的部署做准备。

## 详细提交记录

### [9593d43](https://github.com/sgl-project/sglang/commit/9593d434c4054b584133cbc386b86cb19754fa08)

- **作者**: Lawrence Wu
- **时间**: 2026-04-03T23:16:06Z
- **提交信息**: fix: pause_generation should not populate running_batch on prefill nodes (#20273)

### [5118295](https://github.com/sgl-project/sglang/commit/5118295f7b0ba7234118ade474f8a1495dd6e4d3)

- **作者**: Liangsheng Yin
- **时间**: 2026-04-03T22:56:54Z
- **提交信息**: [CI] Support CPU stage and auto-batch same-stage files in `/rerun-test` (#22081)

### [90e8680](https://github.com/sgl-project/sglang/commit/90e86800f47667debcdd8b16fd82a50dfa7da991)

- **作者**: Sundara Raman Ramachandran
- **时间**: 2026-04-03T22:17:42Z
- **提交信息**: [Score API] Implement EngineScoreMixin for scoring functionality and refactor Tok… (#21342)

### [ac1e437](https://github.com/sgl-project/sglang/commit/ac1e437f6a6348e08fa48583eee008204305b9bf)

- **作者**: Baizhou Zhang
- **时间**: 2026-04-03T22:04:15Z
- **提交信息**: Revert "[Feature] JIT activation and update skills (by codex)" (#22078)

### [8cb337c](https://github.com/sgl-project/sglang/commit/8cb337c8ea48357bb1a404e99b93813089ed64ba)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-04-03T21:19:13Z
- **提交信息**: [Bugfix] Temporarily skip TRTLLM attention on (G)B300 (SM103) to avoid high-concurrency hang (#21906)

Co-authored-by: Baizhou Zhang <sobereddiezhang@gmail.com>

### [1d7a53d](https://github.com/sgl-project/sglang/commit/1d7a53dd0373cf7ffa09040266e606e563594ea8)

- **作者**: Yz Xiao
- **时间**: 2026-04-03T21:17:59Z
- **提交信息**: [Fix] XGrammarGrammarBackend reset to clear inherited cache (#22054)

### [84118ac](https://github.com/sgl-project/sglang/commit/84118acf50b3a4c74e85e9ff9033792552de1a76)

- **作者**: sglang-bot
- **时间**: 2026-04-03T20:58:35Z
- **提交信息**: chore: bump sglang-kernel version to 0.4.1 (#22009)

Co-authored-by: sglang-bot <sglang-bot@users.noreply.github.com>

### [eb407b8](https://github.com/sgl-project/sglang/commit/eb407b80f3775e79703bafd08a3dd62d2a5c46ec)

- **作者**: Lianmin Zheng
- **时间**: 2026-04-03T20:49:00Z
- **提交信息**: [Kernel] Make FA3/FA4 imports lazy in FlashAttentionBackend (#22028)

### [6aafe75](https://github.com/sgl-project/sglang/commit/6aafe756b9698b662ac76fc6db7a7da81a646e5c)

- **作者**: Brayden Zhong
- **时间**: 2026-04-03T20:12:30Z
- **提交信息**: Revert "[Feature] NVFP4 Marlin fallback for non-Blackwell GPUs (SM75+… (#22047)

### [0c9dc09](https://github.com/sgl-project/sglang/commit/0c9dc098e73f5cffb3b0f6a1238848d01a625c49)

- **作者**: Shiyan Deng
- **时间**: 2026-04-03T19:39:39Z
- **提交信息**: Fix DP attention worker port binding for IPv6 support (#21917)

Signed-off-by: Shiyan Deng <dsy842974287@meta.com>

### [ed3435e](https://github.com/sgl-project/sglang/commit/ed3435e37fb65159ccc895ce3a4b70711dc8af4a)

- **作者**: Zhangheng
- **时间**: 2026-04-03T18:23:56Z
- **提交信息**: [HiSparse]: Optimize server args checking-HiSparse is temporarily only available for DSA models. (#22065)

### [151f727](https://github.com/sgl-project/sglang/commit/151f727163f3a5fae0a7593f4a8eb6ab4a660db6)

- **作者**: Mick
- **时间**: 2026-04-03T16:43:11Z
- **提交信息**: [diffusion] fix: fix gated repo failing the generate cmd (#22040)

Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>
Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>

### [896ea75](https://github.com/sgl-project/sglang/commit/896ea7582074ae8e4956d1def54970e1241c37e0)

- **作者**: Ke Bao
- **时间**: 2026-04-03T15:51:37Z
- **提交信息**: Remove reverted test (#22058)

### [47f4fd2](https://github.com/sgl-project/sglang/commit/47f4fd275ac078bd9f6915681b36ba7ab40ce613)

- **作者**: Ke Bao
- **时间**: 2026-04-03T15:47:17Z
- **提交信息**: [CI] Fix test suite names and add suite validation (#21937)

### [44e5d35](https://github.com/sgl-project/sglang/commit/44e5d357037cdd45ec86078ab9b7775936081d53)

- **作者**: DarkSharpness
- **时间**: 2026-04-03T15:28:54Z
- **提交信息**: [Feature][JIT Kernel] JIT activation and update skills (by codex) (#21766)

Co-authored-by: weiminc <tnwilly@gmail.com>

### [030fb1c](https://github.com/sgl-project/sglang/commit/030fb1c4b10088f849d06fcd689c91cb62146338)

- **作者**: Mick
- **时间**: 2026-04-03T15:26:37Z
- **提交信息**: refactor: replace mm_inputs dict with MultimodalProcessorOutput (#21738)

### [9f409d0](https://github.com/sgl-project/sglang/commit/9f409d0749b5dca0224a5d747d25d42f7f5387dd)

- **作者**: Ke Bao
- **时间**: 2026-04-03T14:38:07Z
- **提交信息**: [CI] Adjust CI server launch timeout (#22045)

### [ee9d922](https://github.com/sgl-project/sglang/commit/ee9d922f5a795d4c94b2ec0f9143551bc9541021)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-04-03T13:32:08Z
- **提交信息**: Revert "[Kernel] Fuse temperature + softmax in sampling for decode speedup" (#22046)

### [97adf8a](https://github.com/sgl-project/sglang/commit/97adf8a2909dc642ddf58e98cdd607aa5e76046c)

- **作者**: Baizhou Zhang
- **时间**: 2026-04-03T10:31:44Z
- **提交信息**: [misc] Add hint for kernel release trigger (#22036)

### [98ac401](https://github.com/sgl-project/sglang/commit/98ac40192bcc025e9c07403bfb6b7a239517cd5f)

- **作者**: Baizhou Zhang
- **时间**: 2026-04-03T10:23:03Z
- **提交信息**: [Workflow] Fix kernel release build failures for aarch64 and wheel renaming (#22018)

Co-authored-by: Claude Opus 4.6 (1M context) <noreply@anthropic.com>

### [838f815](https://github.com/sgl-project/sglang/commit/838f815e9fce04be2763c84e6429fe1419f48ae3)

- **作者**: Mick
- **时间**: 2026-04-03T09:39:29Z
- **提交信息**: [diffusion] CI: temporarily disable accuracy ci (#22031)

### [56ac9c9](https://github.com/sgl-project/sglang/commit/56ac9c9932be44558803d60325a6a175dc6fe04d)

- **作者**: Kangyan-Zhou
- **时间**: 2026-04-03T09:33:16Z
- **提交信息**: [Fix] Add _MOE_TP to graph_capture for MoE models with ep>1 (#21907)

Co-authored-by: Claude Opus 4.6 (1M context) <noreply@anthropic.com>
Co-authored-by: Baizhou Zhang <sobereddiezhang@gmail.com>

### [ac593fe](https://github.com/sgl-project/sglang/commit/ac593fed901263911bb9cf7564d9e09949ed0345)

- **作者**: Duyi-Wang
- **时间**: 2026-04-03T08:54:28Z
- **提交信息**: [AMD][Dockerfile] Support build-arg AITER_COMMIT for rocm.Dockerfile (#21949)

### [cd75d54](https://github.com/sgl-project/sglang/commit/cd75d54fc573e757630dfbbeaa7f639def30d379)

- **作者**: Khoa Pham
- **时间**: 2026-04-03T08:45:13Z
- **提交信息**: [Bugfix] Fix CUDA graph replay issues in trtllm_mla draft_extend (#21987)

Co-authored-by: Claude Opus 4.6 (1M context) <noreply@anthropic.com>

### [4f84ce5](https://github.com/sgl-project/sglang/commit/4f84ce58076278ddd57cb01e302bc9bed12e3eb7)

- **作者**: shuwenn
- **时间**: 2026-04-03T08:32:18Z
- **提交信息**: [CI] ci: add test_http_server_auth.py to CI (#21866)

### [658a281](https://github.com/sgl-project/sglang/commit/658a2813d8e567fa724098bb0aa2177db07bc38e)

- **作者**: monkeyLoveding
- **时间**: 2026-04-03T08:22:11Z
- **提交信息**: [NPU] Update CI Dependency (#21578)

### [d07d0a1](https://github.com/sgl-project/sglang/commit/d07d0a15ceb87046b9d64a3a608c17560413d6d5)

- **作者**: Michael
- **时间**: 2026-04-03T08:01:03Z
- **提交信息**: [AMD] Add MiniMax-M2.5 nightly perf benchmarks for MI30x and MI35x (#21524)

### [7431db7](https://github.com/sgl-project/sglang/commit/7431db7392fe5b4a5beb8c296a6dcba2b4bb9ba0)

- **作者**: Thomas Wang
- **时间**: 2026-04-03T07:58:23Z
- **提交信息**: [AMD] Enable FP8 KV cache and FP8 attention kernel for NSA on MI300/MI355 with TileLang backend (#21511)

### [ad0516d](https://github.com/sgl-project/sglang/commit/ad0516d9c1f8235edf594f14b76106dcc8b7e469)

- **作者**: Kelon
- **时间**: 2026-04-03T07:44:07Z
- **提交信息**: [NPU] optimize glm4.7 (#19246)

### [d82097a](https://github.com/sgl-project/sglang/commit/d82097a0df0640ea28587fb9762b9dc43bf07be3)

- **作者**: Shangming Cai
- **时间**: 2026-04-03T07:13:44Z
- **提交信息**: [PD] Tiny register info field cleanup for mooncake backend (#22016)

### [24f52e6](https://github.com/sgl-project/sglang/commit/24f52e66d37edc447bca9d6cfcc29cd9b43ea116)

- **作者**: Ricardo-M-L
- **时间**: 2026-04-03T07:05:39Z
- **提交信息**: fix: remove duplicate words in comments (#22007)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-04-04
**监控日期**: 2026-04-03
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with hybrid cache acceleration and massive parallelism for DiTs.
- **语言**: Python
- **星标数**: 1120
- **最后更新**: 2026-04-03T15:13:14Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

根据提供的README摘要和提交记录，以下是针对仓库 `vipshop/cache-dit` 昨日更新的分析总结：

### 1. 主要更新类型
- **功能新增**：新增对 `svdquant w4a4`（4位权重和4位激活量化）的初步支持，包括内核实现和相关技术。
- **测试优化**：为测试引入 `fast_svd` 模式，并优化测试数据（使用GPU数据）以加速测试执行。

### 2. 关键变更点及其与项目整体方向的关系
- **svdquant w4a4支持**：这是低精度量化技术的重要扩展，旨在减少模型内存占用和计算开销，与项目“混合缓存加速”的核心目标高度一致，有助于提升推理效率。
- **测试模式优化**：通过 `fast_svd` 模式和GPU数据加速测试，反映了项目对开发效率和测试可靠性的重视，确保新功能（如量化）的快速迭代和验证。

### 3. 对项目的影响和潜在意义
- **性能提升潜力**：`w4a4` 量化可显著降低模型部署的资源需求，适用于边缘设备或高并发场景，增强项目的实用性。
- **测试效率提高**：更快的测试周期有助于加速功能开发和回归测试，降低维护成本。
- **技术生态扩展**：量化支持丰富了项目的功能矩阵，可能吸引更多关注高效推理的用户和贡献者。

### 4. 值得关注的技术点
- **低精度量化（w4a4）**：这是当前模型压缩的前沿方向，需关注其精度损失与加速效果的平衡。
- **GPU数据测试优化**：体现了对硬件加速测试的重视，可能涉及CUDA或特定GPU内核的集成。
- **SVD（奇异值分解）量化**：结合SVD的量化方法可能提供更高效的参数压缩，值得深入研究其实现细节。

### 5. 基于项目背景的提交影响分析
- **项目背景**：Cache-DiT 是一个专注于DiT（Diffusion Transformers）推理的PyTorch原生引擎，强调混合缓存加速和大规模并行。其目标是高效部署生成式AI模型。
- **发展影响**：
  - **功能强化**：`svdquant w4a4` 支持直接推进了项目的“加速”使命，通过量化技术减少计算负载，可能提升吞吐量。
  - **开发者体验**：测试优化降低了贡献门槛，鼓励社区参与，符合开源项目的协作需求。
  - **竞争力提升**：量化功能的加入使项目在高效推理领域更具竞争力，尤其适用于资源受限环境。

**总结**：昨日更新聚焦于量化功能扩展和测试效率提升，这两者都紧密围绕项目的核心目标——通过技术创新优化DiT推理性能。这些变更不仅增强了项目的功能深度，也改善了开发流程，为后续高性能特性（如混合缓存集成）的落地奠定了基础。

## 详细提交记录

### [48f6ffa](https://github.com/vipshop/cache-dit/commit/48f6ffa4cadf8ba3941e5f6a5e1f08f737b967fb)

- **作者**: DefTruth
- **时间**: 2026-04-03T12:33:36Z
- **提交信息**: pytest: fast_svd mode for testing (#955)

* test: ignore builtin DeprecationWarning

* pytest: ignore builtin DeprecationWarning

* pytest: ignore builtin DeprecationWarning

* pytest: ignore builtin DeprecationWarning

* use gpu data for fast test

* use gpu data for fast test

* use gpu data for fast test

* use gpu data for fast test

* use gpu data for fast test

* use gpu data for fast test

* use gpu data for fast test

* use gpu data for fast test

* use gpu data for fast test

* use gpu data for fast test

* use gpu data for fast test

* use gpu data for fast test

### [a62c5f5](https://github.com/vipshop/cache-dit/commit/a62c5f5bbd27e17f271b3c1426a3971ed7f0a052)

- **作者**: DefTruth
- **时间**: 2026-04-03T07:32:34Z
- **提交信息**: [1/N] feat: support svdquant w4a4 - kernels & skills (#954)

* [1/N] feat: support svdquant w4a4 - kernels

* [1/N] feat: support svdquant w4a4 - kernels

* [1/N] feat: support svdquant w4a4 - kernels

* [1/N] feat: support svdquant w4a4 - kernels

* [1/N] feat: support svdquant w4a4 - kernels & skills

* [1/N] feat: support svdquant w4a4 - kernels & skills

* [1/N] feat: support svdquant w4a4 - kernels & skills

* [1/N] feat: support svdquant w4a4 - kernels & skills

* [1/N] feat: support svdquant w4a4 - kernels & skills

* [1/N] feat: support svdquant w4a4 - kernels & skills

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-04-04
**监控日期**: 2026-04-03
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 75179
- **最后更新**: 2026-04-03T23:01:28Z

## 提交统计

- **昨日提交总数**: 23
- **提交者数量**: 21
- **主要提交者**: Nick Hill, Xiaoshuang Wang, Yusuf Mohammad

## AI分析总结

根据提供的提交记录和README摘要（vLLM项目致力于“为所有人提供简单、快速、经济的LLM服务”），以下是昨日更新的要点总结：

### 1. 主要更新类型
- **Bug修复**：占主导地位，涉及多个硬件平台（AMD ROCm、NVIDIA、Intel XPU）和功能模块（AWQ量化、MoE路由、日志概率、KV缓存等）。
- **CI/CD与测试优化**：包括修复CI构建、调整测试策略（移除软失败、跳过特定GPU测试、移除多节点测试）。
- **功能增强与扩展**：
    - 新增**在线量化前端**，简化模型量化流程。
    - 为**vLLM IR**添加对“开箱即用”平台的支持，提升可移植性。
    - 为**Intel Triton后端**添加`round_int8`支持。
    - 为**SM120架构**的CUTLASS FP8 GEMM添加`swapAB`支持。
    - 为**前端API**添加流式生成支持。
- **性能优化**：消除GPU->CPU同步以提升预填充阶段性能。

### 2. 关键变更点及其与项目整体方向的关系
| 关键变更点 | 与项目方向的关系 |
| :--- | :--- |
| **多硬件平台支持（ROCm/XPU/Intel）**：修复和优化针对AMD、Intel GPU的代码与CI。 | 直接支撑“为所有人”的目标，通过扩大硬件兼容性降低使用门槛和成本。 |
| **模型与量化优化**：修复AWQ模型批处理一致性问题、重新启用TRT-LLM MoE专家路由、修复MTP下的日志概率。 | 确保**推理正确性**和**模型支持广度**，这是“可靠服务”的基础。 |
| **新前端功能**：新增在线量化前端、流式生成API支持。 | 提升**开发者体验**和**易用性**，让功能更“简单”易用。 |
| **性能优化**：消除GPU->CPU同步、优化内核。 | 直接贡献于“快速”和“经济”的目标，通过减少开销提升吞吐、降低延迟。 |
| **测试与CI精简**：移除不稳定测试、修复CI输出。 | 提升**开发效率**和**代码质量**，确保项目稳定迭代。 |

### 3. 对项目的影响和潜在意义
- **稳定性与可靠性提升**：大量跨平台的Bug修复增强了vLLM在不同部署环境下的稳定性和可靠性。
- **硬件生态扩展**：对AMD ROCm和Intel XPU的持续投入，降低了用户对特定硬件（如NVIDIA）的依赖，符合“廉价”和“广泛可及”的愿景。
- **开发者体验改善**：新的前端功能（在线量化、流式API）降低了使用高级特性的技术门槛。
- **性能基线提高**：针对关键路径（如GDN中的预填充）的优化，有助于提升整体服务性能。
- **维护成本控制**：清理和简化测试套件，有助于长期维护。

### 4. 值得关注的技术点
- **vLLM IR的扩展性**：`import_ir_kernels()`的引入意味着项目正致力于解耦核心与平台特定内核，提升向新硬件平台移植的灵活性。
- **在线量化前端**：这可能意味着vLLM正在将量化等模型优化技术更深度地集成到服务流水线中，实现“开箱即用”的模型优化。
- **MoE模型支持深化**：针对TRT-LLM MoE的修复表明对复杂模型架构的支持在不断成熟。
- **零拷贝或异步优化**：`Eliminate GPU->CPU sync in prepare_chunk_indices` 是典型的减少同步、提升GPU利用率的优化手段。
- **多后端统一**：为Intel Triton后端添加`round_int8`支持，体现了对不同后端算子一致性的努力。

### 5. 基于项目背景的提交影响分析
vLLM的核心目标是**降低高性能LLM服务的工程复杂性和成本**。昨日的提交集体体现了对这一目标的推进：
- **扩大可及性（Cheap & for everyone）**：通过修复AMD ROCm和Intel XPU的问题，项目正积极拥抱更广泛的硬件生态，这直接降低了用户的硬件采购和运营成本。
- **提升易用性与可靠性（Easy & fast）**：
    - **在线量化**和**流式API**等功能新增，让用户无需深入底层细节即可使用高级特性，提升了易用性。
    - **大量的Bug修复**覆盖了从模型加载（AWQ）、推理逻辑（MTP logprobs）到系统调度（KV缓存）等多个层面，这直接提升了服务的正确性和稳定性，是“可靠服务”的基石。
    - **性能优化**直接贡献于“fast”的目标，通过减少不必要的同步和优化内核来提升速度。
- **夯实工程基础**：对CI/CD的修复和测试策略的调整，确保了在快速迭代和多硬件支持背景下，代码质量与集成效率得以维持，这是项目能够健康、持续发展的关键。

**总结**：昨日的更新是一次以**稳定性修复和多平台支持**为核心的常规迭代，同时辅以**提升易用性的新功能**和**关键路径的性能优化**。这完全符合vLLM作为一个成熟、追求广泛适用的生产级服务项目的演进路径，旨在不断巩固基础、扩展边界、优化体验。

## 详细提交记录

### [4b506ff](https://github.com/vllm-project/vllm/commit/4b506ff90a52e92269de24406bc6d932111ba903)

- **作者**: Andreas Karatzas
- **时间**: 2026-04-03T23:01:20Z
- **提交信息**: [ROCm][CI] Minor missing import patch (#38951)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [5875bb2](https://github.com/vllm-project/vllm/commit/5875bb2e9cc3797fe5f42d74c5853576849e4625)

- **作者**: Andreas Karatzas
- **时间**: 2026-04-03T22:58:57Z
- **提交信息**: [ROCm][CI] Added back missing common deps (#38937)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [f0d3ad9](https://github.com/vllm-project/vllm/commit/f0d3ad9f3e080b51322fde6c20ea4889099819aa)

- **作者**: Kevin H. Luu
- **时间**: 2026-04-03T20:42:33Z
- **提交信息**: [ci] Remove soft fail for AMD image build job (#38941)

Signed-off-by: Kevin H. Luu <khluu000@gmail.com>

### [121ea5a](https://github.com/vllm-project/vllm/commit/121ea5a21f0d16e63e98883e17489927adea0728)

- **作者**: Divin Honnappa
- **时间**: 2026-04-03T20:11:08Z
- **提交信息**: Removed GPU state confirmation and cleanup steps. (#38238)

Signed-off-by: Divin Honnappa <divin.honnappa@amd.com>

### [ab79863](https://github.com/vllm-project/vllm/commit/ab79863e6c4f4df652328af6901be2ee208dacec)

- **作者**: Jeffrey Wang
- **时间**: 2026-04-03T20:00:08Z
- **提交信息**: Remove MQ multi-node tests (#38934)

Signed-off-by: Jeffrey Wang <jeffreywang@anyscale.com>

### [5f1de2b](https://github.com/vllm-project/vllm/commit/5f1de2b14b1daece3eb2a1768563e7f84bf1aa99)

- **作者**: Nick Hill
- **时间**: 2026-04-03T19:08:08Z
- **提交信息**: [Model Runner V2] Add config validation for not-yet-supported features (#38758)

Signed-off-by: Nick Hill <nickhill123@gmail.com>

### [a5a623d](https://github.com/vllm-project/vllm/commit/a5a623d9616337ed53e8fa0e1376e2d17b505e38)

- **作者**: yzong-rh
- **时间**: 2026-04-03T17:48:17Z
- **提交信息**: [Bugfix] Re-enable Renormalize routing for TRT-LLM MoE experts (#38859)

Signed-off-by: Yifan Zong <yzong@redhat.com>

### [f8c3af2](https://github.com/vllm-project/vllm/commit/f8c3af2d85a18823d70f359408f7ca72a1c5b9ac)

- **作者**: Xiaoshuang Wang
- **时间**: 2026-04-03T17:25:19Z
- **提交信息**: [vLLM IR] add `import_ir_kernels()` to support OOT platforms (#38807)

Signed-off-by: Icey <1790571317@qq.com>

### [50cd567](https://github.com/vllm-project/vllm/commit/50cd5674b39c69e60fefd0ec1d61652d693e6a06)

- **作者**: danisereb
- **时间**: 2026-04-03T16:24:37Z
- **提交信息**: Fix invalid logprobs with MTP enabled and sync scheduling (#38711)

Signed-off-by: Daniel Serebrenik <daserebrenik@nvidia.com>

### [7b1a742](https://github.com/vllm-project/vllm/commit/7b1a7423bea1705bd51d838e34bef99e8a01cbbd)

- **作者**: Vasiliy Kuznetsov
- **时间**: 2026-04-03T15:58:39Z
- **提交信息**: [Frontend] new online quantization frontend (#38138)

Signed-off-by: Vasiliy Kuznetsov <vasiliy@meta.com>

### [97f92c6](https://github.com/vllm-project/vllm/commit/97f92c6b4741e99ac278f326cabef4f7884d0e49)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-04-03T15:40:16Z
- **提交信息**: [KVConnector] Skip `register_kv_caches` on profiling (#38558)

Signed-off-by: NickLucche <nlucches@redhat.com>

### [46f02e0](https://github.com/vllm-project/vllm/commit/46f02e00f2d99944ecd24000bcc8be2a9504eafe)

- **作者**: Yusuf Mohammad
- **时间**: 2026-04-03T14:54:15Z
- **提交信息**: [Bugfix] Fix AWQ models batch invariance issues (#38670)

Signed-off-by: yusuf <yusuf@deeplearningmachine.mynet>
Signed-off-by: <>
Co-authored-by: yusuf <yusuf@deeplearningmachine.mynet>

### [6b48722](https://github.com/vllm-project/vllm/commit/6b4872240f72bce225f1f3106d1669245345e958)

- **作者**: Qiming Zhang
- **时间**: 2026-04-03T14:10:02Z
- **提交信息**: [XPU] bump up xpu-kernel v0.1.5, transpose moe weights (#38342)

Signed-off-by: mayuyuace <qiming1.zhang@intel.com>
Signed-off-by: Qiming Zhang <qiming1.zhang@intel.com>
Signed-off-by: Kunshang Ji <kunshang.ji@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [580090d](https://github.com/vllm-project/vllm/commit/580090db6bcbb95ca9413ccf2d4d6726e6e69799)

- **作者**: Necofish
- **时间**: 2026-04-03T13:49:59Z
- **提交信息**: [Kernel] Add swapAB support for SM120 CUTLASS blockwise FP8 GEMM  (#38325)

### [cb10b7e](https://github.com/vllm-project/vllm/commit/cb10b7e80b138f876079c2cd697df29f0965b885)

- **作者**: Artem Perevedentsev
- **时间**: 2026-04-03T13:38:02Z
- **提交信息**: [GDN] Eliminate GPU->CPU sync in prepare_chunk_indices during prefill (#38361)

Signed-off-by: Artem Perevedentsev <aperevedents@nvidia.com>
Signed-off-by: Vadim Gimpelson <156319763+vadiklyutiy@users.noreply.github.com>

### [bf8b022](https://github.com/vllm-project/vllm/commit/bf8b022e60abd3008cc9309d837ef2727e6c0acd)

- **作者**: Mieszko Dziadowiec
- **时间**: 2026-04-03T12:47:35Z
- **提交信息**: [Intel][Triton] Support `round_int8` for Intel backend (#38825)

Signed-off-by: Mieszko Dziadowiec <mdziadowiec@habana.ai>
Signed-off-by: Lucas Wilkinson <lwilkins@redhat.com>
Signed-off-by: Stefano Castagnetta <scastagnetta@nvidia.com>
Co-authored-by: Lucas Wilkinson <LucasWilkinson@users.noreply.github.com>
Co-authored-by: Stefano Castagnetta <scastagnetta@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [40ee64c](https://github.com/vllm-project/vllm/commit/40ee64c00ec2b46bb0f093e19e4aa5dc5160a3e5)

- **作者**: xiangdong
- **时间**: 2026-04-03T12:44:52Z
- **提交信息**: [XPU][CI] Skip test_topp_only and test_topk_and_topp cases on Intel GPU in CI (#38904)

Signed-off-by: zengxian <xiangdong.zeng@intel.com>

### [1b117cb](https://github.com/vllm-project/vllm/commit/1b117cb0ac51b84dd7aed364e6e802dea5147ca6)

- **作者**: wufann
- **时间**: 2026-04-03T10:54:00Z
- **提交信息**: [ROCm] Fix aiter persistent mode mla with q/o nhead<16 for kimi-k2.5 tp8 (#38615)

Signed-off-by: wufann <36477220+wufann@users.noreply.github.com>
Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>

### [abebd93](https://github.com/vllm-project/vllm/commit/abebd9323d7cf8abefd07f976be3be356d873075)

- **作者**: Anton Ivanov
- **时间**: 2026-04-03T10:42:43Z
- **提交信息**: [CPU] Replace OMP initialization (#36487)

Signed-off-by: Anton Ivanov <anton.ivanov@cambridgegreys.com>

### [25f2b55](https://github.com/vllm-project/vllm/commit/25f2b5531977293c780edabd211e826b9e644bff)

- **作者**: Hyeonki Hong
- **时间**: 2026-04-03T10:20:32Z
- **提交信息**: [Frontend] feat: add streaming support for token generation endpoint (#37171)

Signed-off-by: Hyeonki Hong <hyeonki.hong@moreh.io>

### [cb4ff07](https://github.com/vllm-project/vllm/commit/cb4ff07f8b1747f77673222456dd3f3968aead9c)

- **作者**: xiangdong
- **时间**: 2026-04-03T09:50:41Z
- **提交信息**: [XPU][CI] Skip test_topk_only cases on Intel GPU in CI (#38899)

Signed-off-by: zengxian <xiangdong.zeng@intel.com>

### [a7d79fa](https://github.com/vllm-project/vllm/commit/a7d79fa1331912d533cc0adbf31552ea761104a5)

- **作者**: Gregory Shtrasberg
- **时间**: 2026-04-03T09:24:26Z
- **提交信息**: [ROCm][CI/Build] Fix the pytest hook to properly print out the summary (#38585)

Signed-off-by: Gregory Shtrasberg <Gregory.Shtrasberg@amd.com>

### [fa9e680](https://github.com/vllm-project/vllm/commit/fa9e68022d29c5396dfbb96d13587b6bc1bdb933)

- **作者**: Netanel Haber
- **时间**: 2026-04-03T07:22:06Z
- **提交信息**: Fix Nano Nemotron VL regressions (#38655)

Signed-off-by: Netanel Haber <58652339+netanel-haber@users.noreply.github.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-04-04
**监控日期**: 2026-04-03
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 4156
- **最后更新**: 2026-04-03T23:19:56Z

## 提交统计

- **昨日提交总数**: 7
- **提交者数量**: 7
- **主要提交者**: Juan Pablo Zuluaga, Yueqian Lin, Alex Brooks

## AI分析总结

根据提供的README摘要和提交记录，以下是vllm-omni项目昨日更新的分析总结：

### 1. 主要更新类型
- **功能新增**：新增两阶段TTS服务支持（OmniVoice）、为LTX-2蒸馏模型添加两阶段推理。
- **重构**：重构Qwen3TTS的语音缓存管理器、重构StageDiffusionClient和StageEngineCoreClient。
- **Bug修复**：修复Flux2开发引导问题。
- **性能优化**：跳过Wan2.2交叉注意力Ulysses SP以提升性能。
- **代码质量/清理**：替换裸`print()`为日志记录器，使用特定异常类型。

### 2. 关键变更点及其与项目方向的关系
- **TTS（文本转语音）增强**：两项提交（#2108, #2463）专注于优化和扩展TTS功能，特别是**语音缓存管理**和**两阶段服务架构**。这与项目“**全模态（omni-modality）**”服务的目标高度一致，旨在提升语音模态的处理效率和灵活性。
- **多阶段推理支持**：不仅TTS，图像模型（LTX-2）也引入了两阶段推理（#2260）。这表明项目在**复杂模型服务优化**上的统一架构思路，通过分解推理步骤来平衡延迟、成本或质量。
- **性能与稳定性**：跳过特定计算步骤（#2459）和修复引导错误（#2433）直接服务于项目的“**快速（fast）**”和“**稳定**”核心承诺。
- **代码健壮性**：日志和异常处理的规范化（#2228）是大型开源项目走向成熟、便于维护和协作的常见举措。

### 3. 对项目的影响和潜在意义
- **用户体验提升**：TTS服务的重构和增强有望为用户提供**更快速、更可靠的语音生成体验**。
- **架构扩展性**：两阶段服务/推理模式的推广为未来集成更复杂的多模态模型（如视频生成、音频理解）提供了**可复用的架构范式**。
- **性能与成本优化**：性能调优提交直接降低计算开销，有助于实现“**廉价（cheap）**”服务的目标。
- **协作与维护**：代码清理和重构提高了代码库的可读性和可维护性，有利于吸引更多贡献者。

### 4. 值得关注的技术点
- **语音缓存管理器重构**：可能涉及缓存策略、内存管理或分布式缓存的优化，对高并发TTS服务至关重要。
- **两阶段（Two-Stage）服务/推理**：这是一个重要的服务设计模式，通常将计算密集型任务（如模型推理）与轻量级任务（如后处理、调度）解耦，以优化资源利用和响应时间。
- **Wan2.2交叉注意力Ulysses SP的跳过**：这是一个非常具体的性能优化，可能针对某个特定模型或硬件（如Intel？从签名看有Intel贡献者）的瓶颈操作进行了规避。

### 5. 基于项目背景的提交影响分析
vllm-omni旨在成为“**面向所有人的简易、快速、廉价的全模态模型服务**”平台。昨日的更新集中体现了这一愿景的推进：
- **全模态扩展**：更新强烈偏向于**TTS（语音模态）**，表明项目正在积极强化除文本、图像外（vLLM传统强项）的模态支持，向真正的“全模态”迈进。
- **“简易、快速、廉价”的实践**：
    - **快速与廉价**：通过缓存重构、计算步骤跳过和两阶段推理优化，直接提升效率、降低延迟与成本。
    - **简易**：代码重构和健壮性提升使项目更易于开发者理解和贡献，间接提升了最终用户获得稳定服务的简易性。
- **社区与生态建设**：多达十余位贡献者的签名和合作作者列表显示了**活跃的社区协作**，这对于一个旨在服务“所有人”的开源项目至关重要。

**总结**：昨日的更新是vllm-omni项目一次**聚焦于TTS功能强化、性能优化和代码质量提升**的迭代。它紧密围绕项目“全模态、高效、易用”的核心目标，通过架构优化和细节打磨，推动平台在多模态AI服务领域变得更加成熟和强大。

## 详细提交记录

### [f50c5a4](https://github.com/vllm-project/vllm-omni/commit/f50c5a413ff37b0314ce24a09a26b3d02e696a67)

- **作者**: Juan Pablo Zuluaga
- **时间**: 2026-04-03T20:51:58Z
- **提交信息**: [Qwen3TTS] [TTS] [Feat] Refactor voice cache manager (#2108)

Signed-off-by: JuanPZuluaga <juanz9312@gmal.com>
Signed-off-by: yiliu30 <yi4.liu@intel.com>
Signed-off-by: gcanlin <canlinguosdu@gmail.com>
Signed-off-by: Binh Tang <tangbinhna@gmail.com>
Signed-off-by: Binh Tang <binht@netflix.com>
Signed-off-by: Didan Deng <33117903+wtomin@users.noreply.github.com>
Signed-off-by: Rein Yang <ruiruyang2@gmail.com>
Signed-off-by: CHEN <116010019@link.cuhk.edu.cn>
Signed-off-by: vraiti <vraiti@redhat.com>
Signed-off-by: Songrui625 <songrui625@gmail.com>
Signed-off-by: Lidang Jiang <lidangjiang@gmail.com>
Signed-off-by: Lidang-Jiang <lidangjiang@gmail.com>
Signed-off-by: Alex Brooks <albrooks@redhat.com>
Co-authored-by: JuanPZuluaga <juanz9312@gmal.com>
Co-authored-by: Yi Liu <yi4.liu@intel.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>
Co-authored-by: Canlin Guo <canlinguosdu@gmail.com>
Co-authored-by: Binh Tang <tangbinhna@gmail.com>
Co-authored-by: Binh Tang <binht@netflix.com>
Co-authored-by: Didan Deng <33117903+wtomin@users.noreply.github.com>
Co-authored-by: rein yang <73573651+R2-Y@users.noreply.github.com>
Co-authored-by: zhumingjue138 <zhumingjue@huawei.com>
Co-authored-by: ChenWenjing <54166744+Shirley125@users.noreply.github.com>
Co-authored-by: vraiti <vraiti@redhat.com>
Co-authored-by: 汪志鹏 <wangzhipeng628@gmail.com>
Co-authored-by: Sy03 <1370724210@qq.com>
Co-authored-by: chickeyton <ngton2014@gmail.com>
Co-authored-by: Jerry Song <46962917+Songrui625@users.noreply.github.com>
Co-authored-by: Lidang Jiang <119769478+Lidang-Jiang@users.noreply.github.com>
Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>
Co-authored-by: Alex Brooks <albrooks@redhat.com>
Co-authored-by: linyueqian <linyueqian@outlook.com>
Co-authored-by: Yueqian Lin <70319226+linyueqian@users.noreply.github.com>

### [0e83ebe](https://github.com/vllm-project/vllm-omni/commit/0e83ebe1d47cdc605637db5f4ef5c8765626f0a5)

- **作者**: Yueqian Lin
- **时间**: 2026-04-03T20:41:20Z
- **提交信息**: [OmniVoice] Add two-stage TTS serving support (#2463)

Signed-off-by: linyueqian <linyueqian@outlook.com>

### [10db95f](https://github.com/vllm-project/vllm-omni/commit/10db95f9a9e9f718db289fce2bd769a9888a497f)

- **作者**: Alex Brooks
- **时间**: 2026-04-03T16:05:19Z
- **提交信息**: [Bugfix] Fix Flux2 Dev Guidance (#2433)

Signed-off-by: Alex Brooks <albrooks@redhat.com>

### [515d15e](https://github.com/vllm-project/vllm-omni/commit/515d15ef87141198f22db1a2f9494452d0348efe)

- **作者**: Lidang Jiang
- **时间**: 2026-04-03T15:59:07Z
- **提交信息**: [Cleanup] Replace bare print() with logger and use specific exception types (#2228)

Signed-off-by: Lidang Jiang <lidangjiang@gmail.com>
Signed-off-by: Lidang-Jiang <lidangjiang@gmail.com>
Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>

### [cd71567](https://github.com/vllm-project/vllm-omni/commit/cd71567b0686968d378486c38844e1fa5fc92998)

- **作者**: Jerry Song
- **时间**: 2026-04-03T15:17:49Z
- **提交信息**: [Model] Add two stages inference for model LTX-2 distilled. (#2260)

Signed-off-by: Songrui625 <songrui625@gmail.com>

### [6dc61c9](https://github.com/vllm-project/vllm-omni/commit/6dc61c9a20a49e86aaf48ad4a03e7c8cb6b29e34)

- **作者**: Canlin Guo
- **时间**: 2026-04-03T08:23:36Z
- **提交信息**: [Perf] Skip Wan2.2 cross attn Ulysses SP (#2459)

Signed-off-by: gcanlin <canlinguosdu@gmail.com>

### [563f73b](https://github.com/vllm-project/vllm-omni/commit/563f73b78a1be00f483f1d940bb5bf6276550984)

- **作者**: chickeyton
- **时间**: 2026-04-03T08:05:19Z
- **提交信息**: Refactor StageDiffusionClient and StageEngineCoreClient (#2006)

---
