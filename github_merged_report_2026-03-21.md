# GitHub Stars 合并报告 - 2026-03-21

**合并日期**: 2026-03-22
**监控日期**: 2026-03-21
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


**报告日期**: 2026-03-22
**监控日期**: 2026-03-21
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 1746
- **最后更新**: 2026-03-21T15:09:30Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-03-22
**监控日期**: 2026-03-21
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Light Image Video Generation Inference Framework
- **语言**: Python
- **星标数**: 2085
- **最后更新**: 2026-03-21T21:17:17Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-03-22
**监控日期**: 2026-03-21
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 1976
- **最后更新**: 2026-03-21T13:21:54Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-03-22
**监控日期**: 2026-03-21
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5192
- **最后更新**: 2026-03-21T14:15:05Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Alex Yang, Ka-Hyun Nam

## AI分析总结

根据提供的提交记录和README摘要（FlashInfer是一个专注于推理的高性能GPU内核项目），以下是昨日更新的分析总结：

### 1. 主要更新类型
- **CI/CD优化**：调整了GitHub Actions工作流，以更高效地利用测试资源。
- **Bug修复**：解决了特定CUDA版本下GPU内核编译和执行的兼容性问题。

### 2. 关键变更点及其与项目整体方向的关系
- **跳过草稿PR的测试**：在CI/CD流程中，为标记为“草稿”的Pull Request自动跳过测试。这**优化了开发流程和资源分配**，让团队能更专注于准备就绪的代码，符合项目作为高性能内核库对**效率和快速迭代**的追求。
- **修复SM 12.x架构的CUDA标志**：针对NVIDIA Spark架构（SM 12.x），修复了在CUDA 12.9环境下编译目标错误（从`120a`修正为`sm120a`）的问题。这**确保了内核在最新GPU硬件和驱动环境下的正确编译与执行**，直接关系到项目核心目标——**提供广泛兼容且可靠的高性能推理内核**。

### 3. 对项目的影响和潜在意义
- **提升开发效率**：减少不必要的CI运行，加快开发反馈循环。
- **增强代码健壮性与兼容性**：修复了可能导致运行时错误（`no kernel image is available for execution on the device`）的隐患，提升了库在新硬件平台（如基于Blackwell架构的GPU）上的稳定性和用户体验。
- **维护项目声誉**：避免用户因环境兼容性问题导致推理失败，有助于维护其作为高性能、生产级推理库的声誉。

### 4. 值得关注的技术点
- **CI/CD策略精细化**：体现了对持续集成资源的成本与效率考量。
- **GPU架构与CUDA版本的深度适配**：揭示了为不同NVIDIA架构（如Spark/Thor）和CUDA工具链版本进行微调的必要性，这是高性能计算库开发中的关键且复杂环节。
- **编译目标标志**：`sm120a`与`120a`的区别，以及`f`后缀（针对CUDA 13+）的引入，反映了NVIDIA工具链的细微变化和对未来硬件的准备。

### 5. 基于项目背景的提交影响分析
FlashInfer旨在为LLM等模型推理提供**底层GPU内核加速**。昨日的更新虽非直接新增功能或优化性能，但至关重要：
- **保障交付质量**：Bug修复直接确保了内核在目标硬件上的可用性，这是任何性能优化的基础。没有正确的执行，高性能无从谈起。
- **优化协作流程**：CI/CD的改进使核心开发者能更流畅地集成贡献，这对于一个开源高性能项目保持开发活力、快速响应问题至关重要。
- **适应硬件生态演进**：针对SM 12.x（新一代GPU架构）的修复，表明项目正积极跟进硬件发展，确保其内核能持续发挥新一代GPU的计算潜力，这与其保持技术领先性的目标一致。

**总结**：昨日更新是典型的**维护性增强**，侧重于**开发体验优化**和**底层兼容性加固**。它们虽不直接提升内核速度，但通过确保代码的正确性和开发流程的顺畅性，为项目长期稳定发展、高效迭代以及在新硬件平台上的竞争力提供了坚实保障。

## 详细提交记录

### [1ddef01](https://github.com/flashinfer-ai/flashinfer/commit/1ddef01bf248302c48ddb424c058db6586425623)

- **作者**: Alex Yang
- **时间**: 2026-03-21T10:41:53Z
- **提交信息**: skip per-pr for draft PRs (#2831)

<!-- .github/pull_request_template.md -->

## 📌 Description

Saves testing capacity not running per-pr testing on draft PRs

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

* **Chores**
* Updated CI/CD workflow to better handle draft pull requests. Tests are
now automatically skipped for draft PRs and execute when marked as ready
for review.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [e2f821b](https://github.com/flashinfer-ai/flashinfer/commit/e2f821b8c5f20eacbc343f03f9db25a6b8af2216)

- **作者**: Ka-Hyun Nam
- **时间**: 2026-03-21T09:51:55Z
- **提交信息**: fix: arch 12.1 -> "sm120a" flag for Spark, CUDA 12.9 (#2839)

<!-- .github/pull_request_template.md -->

## 📌 Description

Bug found in nightly [Spark, 12.9] matrix
https://gitlab-master.nvidia.com/dl/flashinfer/flashinfer-ci/-/jobs/285092631,
where Spark compiles to "120a" (see "/tmp/.cache/flashinfer/0.6.6/120a/"
path in log below).
```
E   RuntimeError: Check failed: (status == cudaSuccess) is false: SingleDecodeWithKVCache kernel launch failed, error: no kernel image is available for execution on the device
/tmp/.cache/flashinfer/0.6.6/120a/generated/single_decode_with_kv_cache_dtype_q_f16_dtype_kv_f16_dtype_o_f16_head_dim_qk_128_head_dim_vo_128_posenc_2_use_swa_False_use_logits_cap_False/single_decode.cu:100: RuntimeError: Check failed: (status == cudaSuccess) is false: SingleDecodeWithKVCache kernel launch failed, error: no kernel image is available for execution on the device
```

Root cause was https://github.com/flashinfer-ai/flashinfer/pull/2725 ,
where we added logic for compiling both Spark and Thor to 120f, but on
the condition that cuda version is 13 or higher. Lower (12.9) defaults
to 'a' suffix, 120a.

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

* **Bug Fixes**
* Strengthened CUDA validation for SM 12.x GPUs: now requires CUDA 12.9
or newer and emits a clear error if unmet, replacing the previous silent
fallback behavior.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-03-22
**监控日期**: 2026-03-21
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3254
- **最后更新**: 2026-03-21T19:03:59Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-03-22
**监控日期**: 2026-03-21
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 33117
- **最后更新**: 2026-03-21T21:39:18Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-03-22
**监控日期**: 2026-03-21
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 387
- **最后更新**: 2026-03-20T07:34:22Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-03-22
**监控日期**: 2026-03-21
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12050
- **最后更新**: 2026-03-21T22:32:48Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-03-22
**监控日期**: 2026-03-21
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 24848
- **最后更新**: 2026-03-21T23:11:44Z

## 提交统计

- **昨日提交总数**: 11
- **提交者数量**: 7
- **主要提交者**: Liangsheng Yin, Mick, Baizhou Zhang

## AI分析总结

根据提供的提交记录和README摘要（项目为SGLang，一个LLM推理框架），以下是昨日更新的分析总结：

---

### 1. **主要更新类型**
- **CI/CD与测试优化**（7项）：涉及测试流程调度、测试用例简化、移除不稳定测试、修复测试问题等。
- **Bug修复**（3项）：修复模型推理中的逻辑错误和内存引用问题。
- **功能扩展**（1项）：为Dbrx模型添加NPU支持。

### 2. **关键变更点及其与项目整体方向的关系**
- **CI/CD流程强化**（如#21082、#21087、#21090）：频繁调整PR测试的定时任务，表明团队在**提升开发效率和自动化测试可靠性**，这与SGLang作为高性能推理框架需要快速迭代、保证稳定性的目标一致。
- **测试稳定性提升**（如#20983、#21088、#21081）：简化测试、移除不稳定用例，直接服务于**提高代码质量和持续集成效率**，减少开发干扰。
- **核心功能修复**：
  - **流式logprobs修复**（#21030）：解决了共享可变列表引用导致的损坏问题，**直接影响推理输出的正确性**，对用户体验和调试至关重要。
  - **Qwen3.5模型并行修复**（#21070）：确保大规模模型在分布式环境下正确运行，**支持更高效的分布式推理**，符合项目对多GPU/集群部署的优化方向。
- **硬件支持扩展**（#17121）：为Dbrx模型添加NPU支持，**扩大框架的硬件兼容性和部署场景**，增强其在不同加速器上的竞争力。

### 3. **对项目的影响和潜在意义**
- **短期**：提升开发流程的稳定性和响应速度，减少因测试问题导致的阻塞。
- **长期**：
  - 通过修复核心推理Bug（如logprobs）和模型支持问题，**增强框架的鲁棒性和准确性**，提升用户信任度。
  - NPU支持扩展了生态边界，**吸引更多硬件厂商和边缘计算场景用户**。
  - 持续的CI/CD优化为项目高速迭代打下基础，**支持更频繁的功能发布和更快的bug修复周期**。

### 4. **值得关注的技术点**
- **流式logprobs的引用问题修复**（#21030）：涉及Python可变对象的共享引用，这类问题在异步/流式推理中容易引发隐蔽Bug，修复体现了对**内存安全和并发安全**的重视。
- **Qwen3.5的流水线并行层分割修复**（#21070）：涉及**分布式模型切分策略**，对支持千亿参数模型的高效推理有重要意义。
- **NPU支持集成**（#17121）：表明项目在**异构计算支持**上投入，可能涉及定制内核或运行时适配，技术门槛较高。

### 5. **基于项目背景的提交影响分析**
SGLang旨在提供**高性能、低延迟的LLM推理服务**，并支持复杂提示词和流式输出。昨日的提交整体围绕以下方向推动项目发展：
- **强化工程基础**：通过CI/CD和测试优化，确保项目在快速迭代中保持稳定，**支撑大规模生产部署的可靠性需求**。
- **提升核心推理质量**：修复logprobs和模型并行问题，直接**改善推理准确性和分布式性能**，与项目“高性能推理”的核心目标紧密对齐。
- **扩展生态兼容性**：添加NPU支持，**降低用户部署门槛并拓宽应用场景**，符合开源框架通过硬件适配扩大影响力的常见策略。

---

**总结**：昨日更新以**工程优化和核心Bug修复为主**，体现了项目在快速发展期对**稳定性、性能和质量**的持续投入，同时通过硬件支持扩展生态，整体推动SGLang向更成熟、更通用的LLM推理框架演进。

## 详细提交记录

### [6dfa8a4](https://github.com/sgl-project/sglang/commit/6dfa8a40bc6a18512677b4cc60a42bf76fadea68)

- **作者**: Mick
- **时间**: 2026-03-21T12:18:23Z
- **提交信息**: [diffusion] CI: make auxiliary coverage explicit and simplify testcases (#20983)

### [a0862f0](https://github.com/sgl-project/sglang/commit/a0862f00c246c1595e7ea334bd06aafc96751447)

- **作者**: KnightLTC
- **时间**: 2026-03-21T09:10:35Z
- **提交信息**: dbrx instruct npu support (#17121)

Co-authored-by: McZyWu <zhuoyun.wu.23@ucl.ac.uk>

### [ff921a2](https://github.com/sgl-project/sglang/commit/ff921a2ed3bfe80b611937e70fadb2948e771bee)

- **作者**: Liangsheng Yin
- **时间**: 2026-03-21T08:03:45Z
- **提交信息**: Update cron schedule for PR test workflow (#21090)

### [852e112](https://github.com/sgl-project/sglang/commit/852e112ebf0054b317e9f02aec97fcf533259cac)

- **作者**: Alison Shao
- **时间**: 2026-03-21T08:02:51Z
- **提交信息**: [Qwen3.5] Fix broken pipeline parallelism layer splitting (#21070)

Co-authored-by: Alison Shao <alison.shao@Mac.attlocal.net>

### [9ca68a5](https://github.com/sgl-project/sglang/commit/9ca68a59040606b5ec253df3b7aee1b474135bd1)

- **作者**: Baizhou Zhang
- **时间**: 2026-03-21T07:52:40Z
- **提交信息**: Remove flaky test for test_lora_update.py (#21088)

### [9b98d55](https://github.com/sgl-project/sglang/commit/9b98d55ba47a31011fdafa594a3282a82acc6d1a)

- **作者**: Lianmin Zheng
- **时间**: 2026-03-21T07:36:05Z
- **提交信息**: Change PR test schedule time to 7:50 AM UTC (#21087)

### [f2c9d56](https://github.com/sgl-project/sglang/commit/f2c9d5696f01d77db9e4f11cc4254fce05c9776c)

- **作者**: Lianmin Zheng
- **时间**: 2026-03-21T07:24:53Z
- **提交信息**: Change daily cron job time in pr-test.yml (#21084)

### [3f883eb](https://github.com/sgl-project/sglang/commit/3f883ebf2e11fd1c56224bc9111deea1b8860a50)

- **作者**: Qiaolin Yu
- **时间**: 2026-03-21T07:22:38Z
- **提交信息**: Fix test_qwen35_models (#21081)

### [dba6fb3](https://github.com/sgl-project/sglang/commit/dba6fb3d308d19e8068380fe34ce3292cd7a67ce)

- **作者**: Lianmin Zheng
- **时间**: 2026-03-21T07:18:48Z
- **提交信息**: Fix streaming logprobs corruption caused by shared mutable list reference (#21030)

### [d089db0](https://github.com/sgl-project/sglang/commit/d089db05631afa1afd43a1dc558dae9d80db9c51)

- **作者**: Lianmin Zheng
- **时间**: 2026-03-21T07:15:48Z
- **提交信息**: ci: add daily PR Test schedule at 12:18am PDT (#21083)

### [182dd20](https://github.com/sgl-project/sglang/commit/182dd20d57ba968d502f9d25a5181570c86e66f6)

- **作者**: Lianmin Zheng
- **时间**: 2026-03-21T07:08:47Z
- **提交信息**: ci: bypass maintenance gate for PR Test on main (#21082)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-03-22
**监控日期**: 2026-03-21
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with hybrid cache acceleration and massive parallelism for DiTs.
- **语言**: Python
- **星标数**: 1102
- **最后更新**: 2026-03-20T17:42:25Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-03-22
**监控日期**: 2026-03-21
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 73876
- **最后更新**: 2026-03-21T23:15:22Z

## 提交统计

- **昨日提交总数**: 10
- **提交者数量**: 6
- **主要提交者**: Francesco Fusco, Chaitanya Sri Krishna Lolla, Robert Shaw

## AI分析总结

根据提供的 `vllm-project/vllm` 仓库的提交记录和项目背景（专注于“易用、快速、经济的LLM服务”），以下是昨日更新的要点总结：

### 1. 主要更新类型
- **性能优化**：针对特定硬件（NVIDIA B300/GB300, AMD GPU）的通信和计算优化。
- **功能新增**：为多模态数据处理添加了新的IPC传输机制。
- **代码重构**：合并和清理量化相关代码，解决循环依赖问题。
- **功能弃用与移除**：移除已弃用的量化方法。
- **硬件支持扩展**：增强对AMD ROCm平台的支持和测试。
- **Bug修复/代码改进**：优化Mamba模型的内存组获取逻辑。

### 2. 关键变更点及其与项目整体方向的关系
| 关键变更点 | 与项目方向的关系 |
| :--- | :--- |
| **为SM 10.3（B300/GB300）启用并优化All-Reduce融合** | 直接服务于“**快速**”和“**经济**”的目标。通过优化最新NVIDIA GPU上的集体通信，减少延迟、提高吞吐量，从而提升服务效率和资源利用率。 |
| **新增多模态数据的张量IPC传输机制** | 服务于“**易用**”和功能扩展。随着LLM向多模态发展，此功能为高效处理图像、音频等数据提供了底层支持，是项目适应前沿应用需求的重要一步。 |
| **合并AWQ量化文件，移除PTPC FP8** | 服务于“**易用**”和代码维护。简化代码结构，消除循环依赖，提升开发者体验；移除旧量化方法，推动用户使用更成熟、高效的方案，保持代码库的整洁和先进。 |
| **扩展AMD ROCm支持（DeepEP后端，更新CI测试）** | 服务于“**为所有人**”和“**经济**”的目标。降低对特定硬件的依赖，为用户提供更多硬件选择，有助于降低部署成本并扩大用户基础。 |
| **优化Mamba模型的内存组调用逻辑** | 服务于“**快速**”和稳定性。通过减少重复调用优化性能，并可能避免潜在错误，提升特定模型架构的推理效率。 |
| **移动FlashInfer MoE专家内核代码** | 属于代码组织优化，为未来MoE（混合专家）模型的功能开发和性能优化做准备，符合支持前沿模型架构的方向。 |

### 3. 对项目的影响和潜在意义
- **性能提升**：针对B300/GB300的优化直接提升了在最新旗舰硬件上的推理性能，巩固了vLLM在高性能场景下的竞争力。
- **功能前瞻性**：多模态IPC和MoE代码整理表明项目正在积极布局，以支持超越纯文本的下一代AI应用和更复杂的模型架构。
- **生态扩展**：加强对AMD ROCm平台的支持，有助于构建更开放、多元的硬件生态系统，吸引更广泛的用户和贡献者。
- **代码健康度**：通过重构和移除废弃代码，提高了代码库的可维护性和长期演进的可持续性。

### 4. 值得关注的技术点
- **All-Reduce Fusion调优**：针对特定计算能力（SM 10.3）的深度优化，体现了对硬件特性极致利用的工程能力。
- **跨进程张量IPC**：这是构建高效多模态服务管道的底层基石，技术实现涉及进程间通信与内存管理，对复杂工作负载的性能至关重要。
- **量化代码重构**：将`awq.py`和`awq_marlin.py`合并的模式（类似之前的GPTQ），展示了项目在整合不同优化实现、提供统一接口方面的设计思路。
- **硬件后端集成**：将DeepEP作为AMD GPU的All2All后端，是跨平台支持的关键一步，涉及不同硬件SDK的集成。

### 5. 基于项目背景的提交影响分析
这些提交共同推动vLLM朝着其“**为所有人提供易用、快速、经济的LLM服务**”的愿景发展：
- **快速与经济**：针对B300/GB300和AMD GPU的优化，直接降低了最新硬件的推理延迟和成本。量化代码的整理则维护了模型压缩这条“经济性”核心路径的代码质量。
- **易用与普及**：多模态支持为开发者处理更复杂的输入提供了便利。对AMD平台的持续投入降低了使用门槛，使“为所有人”的承诺更加落地。
- **面向未来**：对MoE和多模态的底层支持表明项目并非仅优化现有文本模型，而是在为即将到来的、更复杂的AI服务需求搭建基础设施。

**总结**：昨日的更新是一次典型的“夯实基础、前瞻布局”的迭代。既通过深度硬件优化和代码重构来**巩固其在高性能推理领域的现有优势**，又通过添加多模态支持和扩展硬件兼容性来**积极拓展其能力边界和用户范围**，确保项目在快速发展的LLM服务生态中保持领先和适应性。

## 详细提交记录

### [6b2fa3a](https://github.com/vllm-project/vllm/commit/6b2fa3a76204a8e1f64db1bc1962f384bd11c005)

- **作者**: Robert Shaw
- **时间**: 2026-03-21T23:15:16Z
- **提交信息**: [MoE] Move FlashInfer CuteDSL experts into fused_moe/experts/ (#37759)

Signed-off-by: Robert Shaw <robertgshaw2@gmail.com>

### [eeee5b2](https://github.com/vllm-project/vllm/commit/eeee5b262d9a730794ecfc82cb3d55ff030ca3e1)

- **作者**: Robert Shaw
- **时间**: 2026-03-21T22:10:16Z
- **提交信息**: [Quantization][Deprecation] Remove PTPC FP8 (#32700)

Signed-off-by: Robert Shaw <robshaw@redhat.com>
Co-authored-by: Robert Shaw <robshaw@redhat.com>

### [5ad0446](https://github.com/vllm-project/vllm/commit/5ad0446572dcec6bc5af2519ea4a8a54b315f37c)

- **作者**: Robert Shaw
- **时间**: 2026-03-21T21:20:41Z
- **提交信息**: Revert "Consolidate AWQ quantization into single awq_marlin.py file" (#37768)

### [8cc700d](https://github.com/vllm-project/vllm/commit/8cc700dd6a0d44c3b6983c0305af790b703f6b48)

- **作者**: Robert Shaw
- **时间**: 2026-03-21T21:09:17Z
- **提交信息**: Consolidate AWQ quantization into single awq_marlin.py file

Merge awq.py and awq_marlin.py into a single file, eliminating the
circular import between them. awq.py becomes a backward-compat shim.
Follows the same structure as gptq_marlin.py.

Co-authored-by: Claude

Signed-off-by: Robert Shaw <robertgshaw2@gmail.com>

### [80b7088](https://github.com/vllm-project/vllm/commit/80b70884ebd6b5a297d4b87e05651ea2d7c9d116)

- **作者**: Brandon Pelfrey
- **时间**: 2026-03-21T20:10:20Z
- **提交信息**: Add tensor IPC transfer mechanism for multimodal data (#32104)

Signed-off-by: Brandon Pelfrey <bpelfrey@nvidia.com>
Signed-off-by: Brandon Pelfrey <brandonpelfrey@gmail.com>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>

### [61e381d](https://github.com/vllm-project/vllm/commit/61e381dcf01f25cc8a006ecf0ba9c31dde662b42)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-03-21T19:43:47Z
- **提交信息**: [Perf] Add SM 10.3 (B300/GB300) all-reduce communicator tuning (#37756)

Signed-off-by: Mohammad Miadh Angkad <176301910+mmangkad@users.noreply.github.com>

### [88f1b37](https://github.com/vllm-project/vllm/commit/88f1b374f53e1d079dda26966dfd4422cf84a978)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-03-21T19:40:37Z
- **提交信息**: [Core] Enable allreduce fusion by default for SM 10.3 (B300/GB300) (#37755)

Signed-off-by: Mohammad Miadh Angkad <176301910+mmangkad@users.noreply.github.com>

### [298e510](https://github.com/vllm-project/vllm/commit/298e5108482e52fed40de315011c30e08342c979)

- **作者**: Francesco Fusco
- **时间**: 2026-03-21T09:29:43Z
- **提交信息**: [Hybrid] calling get_mamba_groups() once at MambaCopyBuffers.create() (#37318)

Signed-off-by: Francesco Fusco <ffu@zurich.ibm.com>

### [3982bc2](https://github.com/vllm-project/vllm/commit/3982bc2cd0bd9d633060b22e9ff683d8316a0f82)

- **作者**: Chaitanya Sri Krishna Lolla
- **时间**: 2026-03-21T07:32:31Z
- **提交信息**: [ROCm] Enable DeepEP ROCm as all2allbackend for AMD GPUs.  (#34692)

Signed-off-by: Tej Kiran <vpolamre@amd.com>
Co-authored-by: Tej Kiran <vpolamre@amd.com>

### [02eec7e](https://github.com/vllm-project/vllm/commit/02eec7ecbefdb0d32e76e3c95a7426758369e5b2)

- **作者**: Andreas Karatzas
- **时间**: 2026-03-21T07:27:12Z
- **提交信息**: [ROCm][CI] Update GSM8K eval config to use fp8-and-mixed models list (MI355) (#37721)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-03-22
**监控日期**: 2026-03-21
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 3498
- **最后更新**: 2026-03-21T23:35:58Z

## 提交统计

- **昨日提交总数**: 7
- **提交者数量**: 6
- **主要提交者**: SYLAR, 汪志鹏, Zeyu Huang | 黃澤宇

## AI分析总结

根据提供的README摘要和提交记录，以下是vllm-omni项目昨日更新的分析总结：

### 1. 主要更新类型
- **功能新增**：新增HunyuanVideo-1.5模型支持（T2V和I2V）。
- **Bug修复**：修复Fish Speech、CosyVoice3在线服务、Qwen3TTS和扩散模型的问题。
- **依赖升级/重构**：将项目基础升级至vllm v0.18.0，并移除冗余补丁。
- **文档更新**：更新文档和Dockerfile以适配vllm v0.18.0。

### 2. 关键变更点及其与项目整体方向的关系
- **升级至vllm v0.18.0**：这是核心变更，表明项目紧跟底层vLLM引擎的更新，确保性能、稳定性和新特性的同步。
- **新增HunyuanVideo-1.5支持**：扩展了多模态能力（文本到视频、图像到视频），直接强化了项目的“omni-modality”（全模态）定位。
- **修复多个模型服务Bug**：针对语音合成（Fish Speech、CosyVoice3、Qwen3TTS）和扩散模型的修复，提升了特定模态服务的可靠性和用户体验。
- **移除mm_prefix_lm补丁**：因vllm v0.18.0已原生支持，简化了代码库，减少了维护负担。

### 3. 对项目的影响和潜在意义
- **正向影响**：
    - **兼容性与现代化**：升级到vllm v0.18.0使项目保持在技术前沿，可能带来性能提升和新功能。
    - **功能扩展**：新增视频生成模型支持，丰富了项目处理模态的范围。
    - **稳定性提升**：多个Bug修复提高了语音和图像生成服务的健壮性。
- **潜在风险**：重大版本升级（vllm v0.18.0）可能引入新的兼容性问题，需要充分测试。

### 4. 值得关注的技术点
- **vllm v0.18.0集成**：需关注此次升级是否引入了新的API、优化或对现有功能的影响。
- **HunyuanVideo-1.5集成**：这是新的视频生成模型，其实现方式可能涉及复杂的多模态推理流水线。
- **在线服务Bug修复**：如`is_comprehension`字段、模型检测和CudaGraph池的修复，涉及服务端逻辑和GPU资源管理。

### 5. 基于项目背景的提交影响分析
项目目标是提供**简单、快速、经济的全模态模型服务**。昨日的提交紧密围绕这一目标：
- **强化“全模态”能力**：通过新增视频生成模型支持和修复多个语音模型，项目在“视觉”和“听觉”模态的支持上更加完善和稳定。
- **提升“简单”与“快速”**：升级至vllm新版本和修复Bug，旨在提升服务稳定性和性能（可能更快）。移除冗余补丁使项目结构更简洁。
- **确保“服务”可靠性**：针对在线服务（`/chat/completion`接口、模型检测）的修复直接提升了终端用户和开发者的使用体验。

**总结**：昨日更新是一次以**底层引擎升级为核心**，**同步扩展模态支持**并**夯实服务基础**的综合性推进，有力支撑了项目作为全模态服务框架的定位和发展。

## 详细提交记录

### [1bd1d9d](https://github.com/vllm-project/vllm-omni/commit/1bd1d9d618996e841781ee9e67bab1f371bc6344)

- **作者**: 汪志鹏
- **时间**: 2026-03-21T14:32:00Z
- **提交信息**: Remove mm_prefix_lm patch because vllm==0.18.0 already support (#2062)

Signed-off-by: princepride <wangzhipeng628@gmail.com>

### [15f9d60](https://github.com/vllm-project/vllm-omni/commit/15f9d60dd422f395537eeb5252bd1ee7b9ff9c72)

- **作者**: Yueqian Lin
- **时间**: 2026-03-21T14:18:10Z
- **提交信息**: [Bugfix] Fix Fish Speech and CosyVoice3 online serving - missing is_comprehension and broken model detection (#2058)

Signed-off-by: linyueqian <linyueqian@outlook.com>

### [6838533](https://github.com/vllm-project/vllm-omni/commit/6838533998f1d8ef4d006e5429995118d9ba9e64)

- **作者**: SYLAR
- **时间**: 2026-03-21T13:26:39Z
- **提交信息**: [Model] Add HunyuanVideo-1.5 T2V and I2V support (#1516)

Signed-off-by: lishunyang <lishunyang12@163.com>
Signed-off-by: 汪志鹏 <wangzhipeng628@gmail.com>
Co-authored-by: 汪志鹏 <wangzhipeng628@gmail.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [d6e338f](https://github.com/vllm-project/vllm-omni/commit/d6e338f9d61be586d6c084dc369d183375768b86)

- **作者**: Zhou Taichang
- **时间**: 2026-03-21T13:21:33Z
- **提交信息**: [Doc] Update docs and dockerfiles for rebase of vllm v0.18.0 (#2038)

Signed-off-by: tzhouam <tzhouam@connect.ust.hk>
Signed-off-by: Gao Han <hgaoaf@connect.ust.hk>
Co-authored-by: Gao Han <hgaoaf@connect.ust.hk>

### [a90a769](https://github.com/vllm-project/vllm-omni/commit/a90a7690b80bae675286b2644e83f70f3566012d)

- **作者**: Zhou Taichang
- **时间**: 2026-03-21T12:37:38Z
- **提交信息**: [Rebase] Rebase to vllm v0.18.0 (#2037)

Signed-off-by: tzhouam <tzhouam@connect.ust.hk>
Signed-off-by: Zhou Taichang <tzhouam@connect.ust.hk>
Signed-off-by: gcanlin <canlinguosdu@gmail.com>
Co-authored-by: gcanlin <canlinguosdu@gmail.com>

### [8e12007](https://github.com/vllm-project/vllm-omni/commit/8e12007ac1680d169e68e2601d855f2c7eabb363)

- **作者**: Juan Pablo Zuluaga
- **时间**: 2026-03-21T11:11:34Z
- **提交信息**: [BugFix][Qwen3TTS] CodePredictor CudaGraph Pool (#2059)

Signed-off-by: JuanPZuluaga <juanz9312@gmal.com>
Co-authored-by: JuanPZuluaga <juanz9312@gmal.com>

### [da21e99](https://github.com/vllm-project/vllm-omni/commit/da21e991cc7443ffc0193d6d6d1102db60ae1af7)

- **作者**: Zeyu Huang | 黃澤宇
- **时间**: 2026-03-21T07:53:04Z
- **提交信息**: [bugfix] /chat/completion doesn't read extra_body for diffusion model (#2042)

Signed-off-by: Huang, Zeyu <11222265+fhfuih@users.noreply.github.com>
Signed-off-by: Samit <285365963@qq.com>
Co-authored-by: Samit <285365963@qq.com>

---
