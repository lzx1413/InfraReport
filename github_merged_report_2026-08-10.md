# GitHub Stars 合并报告 - 2026-08-10

**合并日期**: 2026-08-11
**监控日期**: 2026-08-10
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


**报告日期**: 2026-08-11
**监控日期**: 2026-08-10
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2137
- **最后更新**: 2026-08-10T08:35:30Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-08-11
**监控日期**: 2026-08-10
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2623
- **最后更新**: 2026-08-10T13:15:44Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 2
- **主要提交者**: Shiqiao Gu (谷石桥), Watebear

## AI分析总结

### 主要更新类型
- **功能新增**：本次提交全部为新增功能支持，无Bug修复、性能优化或文档更新。

### 关键变更点及与项目方向的关系
1. **为minimax-h3-t2av添加mthreads脚本与配置**：新增针对该模型的线程调度脚本和配置文件，属于工程化支持，便于用户在不同硬件环境下部署。
2. **minimax-h3新增LoRA推理与DMD训练支持**：LoRA（低秩适配）推理可大幅降低微调成本，DMD（扩散模型蒸馏）训练则提升训练效率，两者均指向“轻量高效”的核心目标。
3. **为seedvr2添加序列并行（SP）支持**：序列并行是长视频生成的关键优化技术，可突破单卡显存限制，提升长序列处理能力。

### 对项目的影响和潜在意义
- **扩展模型生态**：新增对minimax-h3和seedvr2的支持，使框架覆盖更多主流视频生成模型，增强通用性。
- **降低使用门槛**：LoRA推理支持让用户无需完整微调即可适配特定场景，DMD训练加速则缩短模型迭代周期，两者共同提升易用性。
- **提升可扩展性**：序列并行支持为处理更长视频序列铺路，是应对高分辨率、长时长生成需求的基础能力。

### 值得关注的技术点
- **LoRA推理**：在保持生成质量的同时显著减少显存占用和计算量，是轻量化部署的关键路径。
- **DMD训练**：通过蒸馏技术压缩模型训练成本，与项目“Light”（轻量）定位高度契合。
- **序列并行**：涉及跨设备通信和负载均衡，是分布式推理的核心难点，其实现质量直接影响长视频生成的稳定性。

### 对项目发展的影响
LightX2V定位为“轻量视频生成推理框架”，本次提交从三个维度强化该定位：
- **模型适配广度**：新增两个模型的支持，扩大框架适用范围，吸引更多用户。
- **资源效率深度**：LoRA与DMD从推理和训练两端降低资源消耗，强化“轻量”标签。
- **技术前瞻性**：序列并行支持为未来处理更长、更复杂视频生成任务奠定基础，保持技术领先性。

整体来看，这些提交是框架在“轻量”与“高效”双轨上的稳步推进，既满足当前用户对低成本部署的需求，也为后续功能扩展预留了技术空间。

## 详细提交记录

### [60631ff](https://github.com/ModelTC/LightX2V/commit/60631ff15310d645128226a98f138245bd59eba0)

- **作者**: Watebear
- **时间**: 2026-08-10T09:48:43Z
- **提交信息**: mthreads: add scripts/configs for minimax-h3-t2av (#1356)

### [e02a77d](https://github.com/ModelTC/LightX2V/commit/e02a77daab5f5c88a1ab965a714d9fec9fb0909c)

- **作者**: Shiqiao Gu (谷石桥)
- **时间**: 2026-08-10T09:02:09Z
- **提交信息**: feat(minimax-h3): add LoRA inference and DMD training support (#1352)

### [a901718](https://github.com/ModelTC/LightX2V/commit/a901718607392f1f4b8439b943d4a93d66954618)

- **作者**: Shiqiao Gu (谷石桥)
- **时间**: 2026-08-10T07:42:04Z
- **提交信息**: support sp for seedvr2 (#1345)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-08-11
**监控日期**: 2026-08-10
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2192
- **最后更新**: 2026-08-09T04:09:22Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-08-11
**监控日期**: 2026-08-10
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 6139
- **最后更新**: 2026-08-10T22:33:37Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Po-Han Huang (NVIDIA), Yong Wu

## AI分析总结

## 提交分析总结

### 主要更新类型
本次两笔提交分别属于**流程优化**和**Bug修复**，无新增功能或性能优化。

### 关键变更点与项目方向
1. **CI触发机制调整**：要求所有PR（含维护者）必须显式触发CI，通过评论命令或添加`run-ci`标签启动。这强化了流程管控，与项目作为高性能GPU内核库对代码质量的高要求一致。
2. **BF16 MoE内核修复**：为Blackwell架构的TRTLLM-Gen路径填充中间缓冲区至128 KiB，解决小批量解码时TMA地址生成导致的非法内存访问。这是对核心推理内核的可靠性修复。

### 项目影响与意义
- CI变更提升流程透明度，减少资源浪费，但可能增加维护者操作成本。
- MoE修复直接消除B200x8上的崩溃问题，提升Blackwell平台稳定性，对生产环境部署至关重要。

### 值得关注的技术点
- **TMA `BASE_128KB` 地址生成机制**：理解GPU硬件寻址约束对内核开发的重要性。
- **`maybeGetMinTokenCount` 复用**：统一不同精度启动器的内存分配策略，体现代码复用价值。
- **独立计算GEMM1/GEMM2行数**：适应不同隐藏维度，增强内核通用性。

### 对项目发展的影响
这两笔提交分别从**工程效率**和**硬件适配**两个维度巩固了FlashInfer作为高性能推理库的竞争力。CI流程规范化有助于吸引外部贡献者，而Blackwell平台的稳定性修复则确保项目能紧跟最新GPU架构，维持技术领先地位。整体上，提交体现了项目在追求性能的同时，对代码质量和跨平台可靠性的持续投入。

## 详细提交记录

### [a01a52e](https://github.com/flashinfer-ai/flashinfer/commit/a01a52eb5510e8e750ebdadd0fd7d3ded2997cfb)

- **作者**: Yong Wu
- **时间**: 2026-08-10T22:33:28Z
- **提交信息**: require explicit ci triggering for all pull requests (#4383)

<!-- .github/pull_request_template.md -->

Public CI no longer starts on its own for any pull request, including
PRs from maintainers. To start CI, comment `@flashinfer-bot run` or add
the `run-ci` label. Applying the label is what starts a run, not the
label being present, so you'll need to trigger again after pushing new
commits.

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

* **New Features**
* Public CI can be manually started by applying the `run-ci` label or
issuing the documented CI command.
* CI authorization is consistently enforced for pull requests, including
drafts.

* **Bug Fixes**
* Reapplying the `run-ci` label reliably triggers CI for the current
commit.
* CI results and rerun instructions are preserved and updated
appropriately.
  * Workflow cancellation failures are now reported clearly.

* **Documentation**
* Clarified that CI must be restarted after new commits and applies only
to the current commit.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [2fb785c](https://github.com/flashinfer-ai/flashinfer/commit/2fb785c192ba78ede492a34c59c471e45284b0eb)

- **作者**: Po-Han Huang (NVIDIA)
- **时间**: 2026-08-10T15:31:52Z
- **提交信息**: fix(moe): pad BF16 TRTLLM-Gen intermediates to 128 KiB (#4319)

[by Codex]

## Summary

- pad the BF16 TRTLLM-Gen MoE GEMM1 and GEMM2 intermediate allocations
to at least 128 KiB
- reuse `Routing::maybeGetMinTokenCount`, matching the existing FP8/MXFP
launchers
- calculate the GEMM1 and GEMM2 row counts independently because their
hidden dimensions can differ

## Why

On Blackwell, the TRTLLM-Gen BMM2 kernel can use TMA `BASE_128KB`
address generation based on the logical tensor-map shape. With a small
eager decode batch, the BF16 launcher currently allocates only the
logical 16/32-KiB intermediate. That leaves less than 128 KiB mapped
after the activation base and can produce an illegal memory access in
`UTMALDG.4D`.

The quantized launchers already call `maybeGetMinTokenCount` for both
intermediates. Applying the same allocation policy to the BF16 launcher
gives the TMA transaction the required backing without changing the
logical token count passed to routing or GEMM.

## Validation

- `pre-commit run --all-files`
- B200x8 patched-JIT compile/load preflight
- six consecutive Miles/SGLang rollout runs with the original reproducer
setting:
  - pinned image and model revision
  - FlashInfer TRTLLM backend, TP8
  - four train/rollout steps per run
  - 256 one-token post-update health probes per step boundary
- no descriptor-bit override, TMA-OOB disablement, extra
allocation-padding knob, or synchronization workaround

Result: six consecutive valid passes on B200x8. Every run exited
normally, completed all four steps, passed the diagnostic evidence gate,
and had zero IMA/sanitizer/segfault matches.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Improved BF16 Mixture-of-Experts processing by ensuring intermediate
buffers have sufficient capacity for required token mappings.
* Increased reliability for GEMM-based operations across varying tensor
dimensions while preserving expected output shapes and device placement.
* Helps prevent capacity-related processing failures in workloads with
larger or uneven token distributions.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: Po-Han Huang <pohanh@nvidia.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-08-11
**监控日期**: 2026-08-10
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3936
- **最后更新**: 2026-08-10T10:03:26Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-08-11
**监控日期**: 2026-08-10
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34277
- **最后更新**: 2026-08-10T17:54:34Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 3
- **主要提交者**: Jingya HUANG, Sayak Paul, apolinário

## AI分析总结

## 提交分析总结

### 1. 主要更新类型
本批次提交包含**Bug修复**（LoRA缩放问题）、**功能增强**（设备推断逻辑优化）和**测试基础设施改进**（导入保护）三类变更，无新增功能或文档更新。

### 2. 关键变更点与项目方向的关系
- **混合秩LoRA缩放修复**：修正了无alpha键的混合秩LoRA未按预期缩放的问题，直接关系到diffusers核心的LoRA适配器功能正确性，与项目“提供可靠微调工具”的目标一致。
- **设备推断逻辑重构**：重新定义`DiffusionPipeline.device`的推导方式，支持分设备（split-device）管线场景，移除所有CPU检查，使设备属性更准确反映实际运行环境，契合项目对多硬件部署的支持方向。
- **测试导入保护**：将peft导入置于`is_peft_available()`守卫后，解决Hub staging测试任务因未安装peft而收集失败的问题，属于测试基础设施的健壮性改进。

### 3. 对项目的影响和潜在意义
- LoRA修复直接影响使用混合秩LoRA的用户，确保模型加载后行为符合预期，避免静默错误，提升生态可信度。
- 设备推断改进使跨设备（如GPU+CPU混合）管线能正确报告设备信息，为后续依赖该属性的功能（如自动混合精度、设备调度）奠定基础。
- 测试修复降低了CI误报率，减少开发者排查无关失败的时间成本，提升协作效率。

### 4. 值得关注的技术点
- **LoRA缩放逻辑**：混合秩LoRA无alpha键时的默认缩放策略调整，涉及权重合并时的数值稳定性，值得关注其与有alpha键路径的一致性。
- **设备推导策略**：从“检查所有设备”改为更智能的推导方式，可能基于管线中活跃张量的设备或主执行设备，需关注边缘情况（如空管线、全CPU管线）。
- **测试收集优化**：通过条件导入避免模块级依赖，是大型库管理可选依赖的标准实践，可推广至其他可选后端。

### 5. 对项目发展的影响
结合README背景，diffusers作为HuggingFace生态的扩散模型核心库，本批次提交体现了三个发展方向：**可靠性**（修复LoRA缩放）、**灵活性**（支持复杂部署拓扑）和**工程效率**（优化测试流程）。这些改进虽不引入新功能，但巩固了项目作为生产级工具的基础，为后续更复杂的模型并行、混合精度训练等高级特性铺路，同时降低社区贡献门槛，符合其“让扩散模型民主化”的使命。

## 详细提交记录

### [90c0ffd](https://github.com/huggingface/diffusers/commit/90c0ffdc045902a3667d473d2fbfc03e8716dba9)

- **作者**: apolinário
- **时间**: 2026-08-10T16:27:11Z
- **提交信息**: 🚨 Give mixed-rank LoRAs without alpha keys their intended scale (#14409)

Give mixed-rank LoRAs without alpha keys their intended scale

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

### [1ca0943](https://github.com/huggingface/diffusers/commit/1ca0943e5912e90933cb49383281c7953976a938)

- **作者**: Jingya HUANG
- **时间**: 2026-08-10T12:32:06Z
- **提交信息**: [core] `DiffusionPipeline.device` deduction for split-device pipelines (#14383)

* feat:redefine device deduction

* test: unit test

* review: remove all cpu check

### [f6e1c4d](https://github.com/huggingface/diffusers/commit/f6e1c4d1e7a6aebaeeaaa0880a82ad036517909e)

- **作者**: Sayak Paul
- **时间**: 2026-08-10T08:40:24Z
- **提交信息**: [tests] guard peft imports in test_lora_loader_utils (#14434)

The Hub staging-tests job runs `pytest -m "is_staging_test" tests`, which
imports every test module at collection time, but that job doesn't install
peft. The top-level `from peft import ...` added in #14385 therefore breaks
collection with exit code 2 on every PR.

Guard the imports behind `is_peft_available()` (as `tests/lora/utils.py`
already does) and mark the one test that needs them with
`require_peft_backend`.

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-08-11
**监控日期**: 2026-08-10
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 430
- **最后更新**: 2026-08-05T05:40:44Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-08-11
**监控日期**: 2026-08-10
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12908
- **最后更新**: 2026-08-10T16:46:52Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 1
- **主要提交者**: Zhongjie Duan

## AI分析总结

# DiffSynth-Studio 提交分析

## 主要更新类型

本次提交记录包含两类变更：**Bug修复**（修复拼写错误）和**版本更新**（发布2.1.1版本）。整体属于维护性更新，无新增功能或架构调整。

## 关键变更点

1. **修复拼写错误**（#1580）：对代码或文档中的拼写问题进行修正，属于代码质量维护。
2. **版本号更新至2.1.1**（#1578）：正式发布新版本，通常伴随bug修复或小幅优化。

## 对项目的影响与潜在意义

- **版本发布**表明项目处于活跃迭代周期，2.1.1作为补丁版本，旨在修复已知问题并提升稳定性，对用户而言是低风险升级。
- **拼写修复**虽不改变功能，但有助于提升代码可读性和可维护性，减少后续开发中的理解成本。

## 值得关注的技术点

本次提交未涉及算法、性能或架构层面的技术变更，技术含量较低。版本号从2.1.0升至2.1.1，符合语义化版本规范，暗示为向后兼容的bug修复版本。

## 对项目发展的影响

DiffSynth-Studio是一个面向视频/图像合成与编辑的开源工具，基于README可知其核心价值在于提供高效的扩散模型合成能力。本次提交虽不引入新功能，但持续的小步维护和版本迭代有助于：
- **增强用户信任**：及时发布修复版本，体现项目维护活跃度。
- **夯实基础**：拼写修复和版本管理为后续功能开发提供更干净的代码基础。
- **生态建设**：稳定的版本发布节奏有助于吸引更多开发者贡献和用户采用。

总体而言，这是一次常规的维护性更新，对项目长期发展起到稳固基础的作用，但短期内不会带来显著的功能或性能变化。

## 详细提交记录

### [b8e3811](https://github.com/modelscope/DiffSynth-Studio/commit/b8e3811e5c4abd83a44b99b2bcff7ccabdb26a71)

- **作者**: Zhongjie Duan
- **时间**: 2026-08-10T12:07:25Z
- **提交信息**: fix typo (#1580)

### [7c26ccb](https://github.com/modelscope/DiffSynth-Studio/commit/7c26ccbea618b79d84d65d9b1f01db811158691d)

- **作者**: Zhongjie Duan
- **时间**: 2026-08-10T12:01:41Z
- **提交信息**: update version to 2.1.1 (#1578)

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-08-11
**监控日期**: 2026-08-10
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 31633
- **最后更新**: 2026-08-10T22:36:39Z

## 提交统计

- **昨日提交总数**: 35
- **提交者数量**: 22
- **主要提交者**: Qiaolin Yu, siyu, Thomas Wang

## AI分析总结

# SGLang 昨日提交分析报告

## 一、主要更新类型

本次提交涵盖**Bug修复**（约10项）、**性能优化**（约5项）、**新功能支持**（约6项）、**文档/教程更新**（约5项）、**CI/CD改进**（约4项）及**代码重构**（约3项），整体呈现多维度并行推进态势。

## 二、关键变更点与项目方向

**1. AMD/ROCm平台深度优化**（提交1、3、5、24、34）
- 修复AITER reduce-scatter在CUDA-graph捕获下的崩溃问题
- 优化hisparse的DSv4值拷贝（128位非临时拷贝）
- 恢复K3 MLA verify kernel路径
- 这些工作强化了SGLang作为**多硬件平台推理框架**的定位，与README中强调的广泛硬件支持目标一致

**2. 推测解码（Speculative Decoding）体系完善**（提交6、8、10、30、32）
- 新增Inkling DSPARK支持及thinking budget
- 修复DSPARK下两个NaN根因（页分配清零、CuTe int32槽位步长回绕）
- 为DFLASH草稿KV池引入注意力几何预算机制
- 推测解码是提升推理吞吐的关键技术，SGLang在此持续投入，巩固其**高性能推理引擎**的核心竞争力

**3. 扩散模型（Diffusion）功能增强**（提交11、12、13、14、16、17、26）
- 修复H3 rank-local FSDP QKV加载问题
- 支持--served-model-name参数
- Z-Image单GPU BCG输出与eager模式bit-exact对齐
- 优化权重加载性能
- 表明SGLang正积极扩展**多模态生成**能力边界

**4. 多模态缓存解耦**（提交21）
- 将多模态全局缓存与Mooncake解耦，提升架构灵活性和可移植性

**5. 统一Radix Cache支持Mamba分支**（提交29）
- HiCache支持Mamba架构分支，扩展了缓存系统对**状态空间模型**的适配能力

## 三、项目影响与潜在意义

- **稳定性提升**：多项崩溃修复（CUDA-graph捕获、replay崩溃）直接提升生产环境可靠性
- **性能增益**：128位非临时拷贝、缓存复用优化等可显著降低内存带宽瓶颈
- **生态扩展**：新增多个模型Cookbook（Intern-S2-Mobius、Ling-3.0-tiny、Muse Glimmer），降低新模型接入门槛
- **CI/CD强化**：Docker镜像双架构构建、保留torch编译缓存等改进加速开发迭代

## 四、值得关注的技术点

1. **bit-exact对齐**：Z-Image输出与eager模式完全一致，对调试和可复现性至关重要
2. **NaN根因修复**：涉及页分配清零和CuTe整数溢出，属于底层内存管理的精细问题
3. **异步tracing导出**（提交35）：支持异步导出追踪数据，减少对推理路径的性能干扰
4. **cuda-tile版本固定**：解决Python 3.10 x86_64安装阻塞，体现对**安装体验**的重视

## 五、对项目发展的影响

结合README背景，SGLang定位为**高性能、多硬件、多模态的大模型推理框架**。昨日提交清晰呈现三条发展主线：**一是深化AMD/ROCm适配**，扩大硬件覆盖；**二是完善推测解码和缓存机制**，强化性能优势；**三是扩展扩散模型和状态空间模型支持**，拓宽应用场景。同时，CI改进和文档完善表明项目在**工程化成熟度**上持续投入。整体来看，这些提交体现了SGLang在保持性能领先的同时，正稳步向**全栈、全硬件、全模型类型**的通用推理平台演进。

## 详细提交记录

### [2c72323](https://github.com/sgl-project/sglang/commit/2c72323d90e157866e7560baf4dc28efa44aa158)

- **作者**: Zhiyao Jiang
- **时间**: 2026-08-10T22:36:15Z
- **提交信息**: [AMD] Fix AITER custom reduce-scatter CUDA-graph capture crash under torch_memory_saver (#34203)

### [c80a38e](https://github.com/sgl-project/sglang/commit/c80a38edcd2c7077c909a5ed925c9241e754c067)

- **作者**: Liangsheng Yin
- **时间**: 2026-08-10T22:09:47Z
- **提交信息**: [Fix] Pin `cuda-tile` to 1.6.0rc5 to unblock Python 3.10 x86_64 installs (#34321)

### [ca0f8a0](https://github.com/sgl-project/sglang/commit/ca0f8a0f4ced5fc107f27a3be386d12bc7850711)

- **作者**: AMD-yanfeiwang
- **时间**: 2026-08-10T21:30:15Z
- **提交信息**: perf(hisparse): fuse the DSv4 value and scale swap-in copy on ROCm (#33484)

### [166c6f7](https://github.com/sgl-project/sglang/commit/166c6f71811087d427feed48c685356965810707)

- **作者**: QIN2DIM
- **时间**: 2026-08-10T20:31:18Z
- **提交信息**: [Kernel] cutedsl_bf16_gemm: trailing cluster barrier for 2-CTA TGV kernel exit (#32907) (#32954)

### [1a8e487](https://github.com/sgl-project/sglang/commit/1a8e4876b6ddccc5f2712efdca7f87fdc5514c7b)

- **作者**: AMD-yanfeiwang
- **时间**: 2026-08-10T20:27:15Z
- **提交信息**: perf(hisparse): 128-bit non-temporal swap-in copy on ROCm (#33085)

### [733c05c](https://github.com/sgl-project/sglang/commit/733c05c887da9aad4b2e6c46292588ba5110a8e0)

- **作者**: Qiaolin Yu
- **时间**: 2026-08-10T20:21:35Z
- **提交信息**: [spec decoding] support inkling dspark (#31847)

### [e54c153](https://github.com/sgl-project/sglang/commit/e54c153ba637582f41169b5679b68531071d4324)

- **作者**: Xinyuan Tong
- **时间**: 2026-08-10T20:13:35Z
- **提交信息**: Add Intern-S2-Mobius cookbook (#33820)

Co-authored-by: Justin Tong <justintong0323@outlook.com>
Co-authored-by: Zijie Xia <zijie.xia@radixark.ai>

### [a2161ce](https://github.com/sgl-project/sglang/commit/a2161ce682af59158c79bfd76f9f20a7238742fc)

- **作者**: Lifan Shen
- **时间**: 2026-08-10T18:01:08Z
- **提交信息**: Support thinking budget for Inkling (#33146)

Co-authored-by: Xinyuan Tong <115166877+JustinTong0323@users.noreply.github.com>

### [955aab8](https://github.com/sgl-project/sglang/commit/955aab8db1032e37be15320c25659bc891b2e38e)

- **作者**: Tan Trinh
- **时间**: 2026-08-10T17:45:40Z
- **提交信息**: [DCP] Reuse partial output in natural-log LSE merge (#34213)

### [7738062](https://github.com/sgl-project/sglang/commit/7738062294e2701149aad4860d3d0edadf1630b2)

- **作者**: Cheng Wan
- **时间**: 2026-08-10T17:35:06Z
- **提交信息**: [unified memory] Support DSPARK speculative decoding + fix two NaN root causes (page hand-out zeroing, CuTe int32 slot-stride wrap) (#33974)

### [ec9babe](https://github.com/sgl-project/sglang/commit/ec9babe36cc172cb5d7f3882547718e99ddb2e0c)

- **作者**: Mick
- **时间**: 2026-08-10T15:59:00Z
- **提交信息**: [diffusion] fix: fix h3 rank-local fsdp qkv loading (#34294)

### [d07ac32](https://github.com/sgl-project/sglang/commit/d07ac32d056e19e6e28366a6e20c2085ad149e70)

- **作者**: TobyMint
- **时间**: 2026-08-10T14:27:09Z
- **提交信息**: [diffusion] feat: support --served-model-name in sglang serve (#34228)

Co-authored-by: TobyMint <tobymint@users.noreply.github.com>
Co-authored-by: Mick <mickjagger19@icloud.com>

### [f5f0c3e](https://github.com/sgl-project/sglang/commit/f5f0c3ee7a3bab17897e057e3a03af7198b4c64c)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-08-10T14:18:32Z
- **提交信息**: [diffusion] Z-Image single-GPU BCG: fix the replay crash and make output bit-exact vs eager (#34183) (#34210)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [fd30365](https://github.com/sgl-project/sglang/commit/fd3036523a1af7ba0775bc785d8063f4d7ee5094)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-08-10T14:14:09Z
- **提交信息**: [diffusion] Clean up shared bitexact gates, helpers, and stale naming (#34180)

Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [77c90e7](https://github.com/sgl-project/sglang/commit/77c90e7e54938f9835c8d27563183f1ca2def4a6)

- **作者**: Xinyuan Tong
- **时间**: 2026-08-10T13:25:17Z
- **提交信息**: Cookbook: add Ling-3.0-tiny (#34283)

### [3e2a267](https://github.com/sgl-project/sglang/commit/3e2a26708ba9e3a7463761269426631c75a95cff)

- **作者**: Mick
- **时间**: 2026-08-10T12:08:45Z
- **提交信息**: [diffusion] chore: expose architecture config at the dit runtime boundary (#34248)

### [8ba9385](https://github.com/sgl-project/sglang/commit/8ba9385097322875f1a1c22e5f88356ebed2ec2a)

- **作者**: Mick
- **时间**: 2026-08-10T12:07:48Z
- **提交信息**: [diffusion] chore: optimize model weight loading (#34064)

### [4eaaeda](https://github.com/sgl-project/sglang/commit/4eaaeda00416309a1db19c39bc9ec8684991bb47)

- **作者**: Liangsheng Yin
- **时间**: 2026-08-10T11:49:22Z
- **提交信息**: [CI] Build patched Docker images for both amd64 and arm64 (#34276)

### [01a2ef9](https://github.com/sgl-project/sglang/commit/01a2ef95b8fbd5f645c613732ea4135bf7364077)

- **作者**: 黄孝君
- **时间**: 2026-08-10T11:40:52Z
- **提交信息**: [NPU] Modified kernel tag version to 8.10 (#34254)

### [d95e824](https://github.com/sgl-project/sglang/commit/d95e824a4976aabc852bb42e85a1fcbd0041a191)

- **作者**: Brayden Zhong
- **时间**: 2026-08-10T11:39:55Z
- **提交信息**: Muse Glimmer Cookbook: install from the PR branch (#34281)

Co-authored-by: Brayden Zhong <brayden.zhong@radixark.ai>

### [14ffd44](https://github.com/sgl-project/sglang/commit/14ffd447a4bc431c67e33e1743e076e0f53780c8)

- **作者**: siyu
- **时间**: 2026-08-10T11:23:19Z
- **提交信息**: [FEAT] Decouple multimodal global cache from Mooncake (#30392)

Co-authored-by: Yuang Chen <cya539102@antgroup.com>
Co-authored-by: Yuang Chen <1131578721@qq.com>

### [d96b153](https://github.com/sgl-project/sglang/commit/d96b1533eac26cb488c8aaf493e4078bda68dd86)

- **作者**: Brayden Zhong
- **时间**: 2026-08-10T10:49:02Z
- **提交信息**: Muse Glimmer Cookbook: install from the PR branch (#34278)

Co-authored-by: Brayden Zhong <brayden.zhong@radixark.ai>

### [443b62d](https://github.com/sgl-project/sglang/commit/443b62db57a964cf7261210721070be2da654fd5)

- **作者**: Mick
- **时间**: 2026-08-10T10:47:19Z
- **提交信息**: fix(vlm): stream-order cuda-ipc feature pool lifecycle and streamline multimodal transport module (#33949)

### [0977b22](https://github.com/sgl-project/sglang/commit/0977b22431cf7a735eced1f6f092b5c64019dc92)

- **作者**: Thomas Wang
- **时间**: 2026-08-10T10:31:53Z
- **提交信息**: [AMD] Restore K3 MLA verify kernel path blocked by can_handle() guard (#34261)

### [a6c34df](https://github.com/sgl-project/sglang/commit/a6c34df0442b6060e781273d10acbf105cb93a51)

- **作者**: Brayden Zhong
- **时间**: 2026-08-10T10:21:13Z
- **提交信息**: Muse Glimmer Cookbook (#34271)

Co-authored-by: Brayden Zhong <brayden.zhong@radixark.ai>
Co-authored-by: Jimmy Shong <jimmysh341@gmail.com>
Co-authored-by: Zijie Xia <zijie.xia@radixark.ai>

### [955569a](https://github.com/sgl-project/sglang/commit/955569a2dc993174a27c6e8bfea70e2e212afad1)

- **作者**: Mick
- **时间**: 2026-08-10T10:16:20Z
- **提交信息**: [diffusion] feat: expose cosmos3 policies through the Action API (#34243)

### [c971d7a](https://github.com/sgl-project/sglang/commit/c971d7ac9c9c8d677e7feba3b73a2c4b428d0b86)

- **作者**: YAMY
- **时间**: 2026-08-10T09:53:32Z
- **提交信息**: Refactor staging registration metadata fields (#33910)

Co-authored-by: Shangming Cai <csmthu@gmail.com>

### [0b6189d](https://github.com/sgl-project/sglang/commit/0b6189d0e8cc9635769e98d77d16891c9ee77cf9)

- **作者**: Liangsheng Yin
- **时间**: 2026-08-10T09:48:03Z
- **提交信息**: [CI] Add output_tag input to the Patch Docker Image workflow (#34253)

### [3c533ac](https://github.com/sgl-project/sglang/commit/3c533acec6cdb0b0e44ab0f26411e499225fef02)

- **作者**: Jincong Chen
- **时间**: 2026-08-10T09:16:42Z
- **提交信息**: [Hicache][2/2]Support Mamba branching in Unified Radix Cache with HiCache (#33639)

### [430f38e](https://github.com/sgl-project/sglang/commit/430f38ea2530453c0940b94da8251adf2d0ea047)

- **作者**: Ke Bao
- **时间**: 2026-08-10T09:12:51Z
- **提交信息**: Update dspark draft path in Inkling small cookbook (#34250)

### [a76a167](https://github.com/sgl-project/sglang/commit/a76a167812e8fcc8d665581208fd84ed20c90a09)

- **作者**: ybyang
- **时间**: 2026-08-10T08:58:13Z
- **提交信息**: Fix/hisparse host backed max request length (#28753)

Co-authored-by: huangtingwei <141888744+huangtingwei9988@users.noreply.github.com>
Co-authored-by: Zhangheng <hzh0425@apache.org>

### [b51bf9e](https://github.com/sgl-project/sglang/commit/b51bf9ec9e5ccce8ab05e7d4ce555b1fb51df3db)

- **作者**: Liangsheng Yin
- **时间**: 2026-08-10T08:28:49Z
- **提交信息**: [Spec] Budget the DFLASH draft KV pool from its own attention geometry (#34234)

Co-authored-by: Brayden Zhong <b8zhong@uwaterloo.ca>

### [3bb72bc](https://github.com/sgl-project/sglang/commit/3bb72bc72a22173023160f7391fc90490f68063a)

- **作者**: Liangsheng Yin
- **时间**: 2026-08-10T08:21:20Z
- **提交信息**: [CI] Keep the torch compilation cache instead of wiping it on install (#34231)

### [f2a4c4c](https://github.com/sgl-project/sglang/commit/f2a4c4c847786df76a11382e9eb3bdde6f223a10)

- **作者**: Michael
- **时间**: 2026-08-10T08:09:00Z
- **提交信息**: [AMD] [CI] Enable 3 nested unit tests needing harness stub fixes (#31843)

Co-authored-by: HAI <hixiao@gmail.com>

### [fb3d141](https://github.com/sgl-project/sglang/commit/fb3d1419fd0be8e56d357e8fe63fef2e0ba4be59)

- **作者**: Feng Su
- **时间**: 2026-08-10T07:23:05Z
- **提交信息**: [tracing] sglang tracing v2: support exporting tracing data asynchronously (#30023)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-08-11
**监控日期**: 2026-08-10
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1245
- **最后更新**: 2026-08-09T23:02:23Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-08-11
**监控日期**: 2026-08-10
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 88700
- **最后更新**: 2026-08-10T22:36:50Z

## 提交统计

- **昨日提交总数**: 38
- **提交者数量**: 33
- **主要提交者**: Giancarlo Delfin, Almog Tavor, Summer Yang

## AI分析总结

# vLLM 昨日提交分析报告

## 一、主要更新类型

本次共38个提交，涵盖Bug修复（约12个）、性能优化（4个）、硬件适配（ROCm/XPU/AMD，约8个）、CI/构建改进（约7个）、新功能支持（Kimi-K3 DCP、gRPC路由等）、文档与安全修复。

## 二、关键变更点与项目方向

1. **模型支持扩展**：Kimi-K3 DCP支持、DeepSeek V4优化、Qwen3.5 MTP修复、Gemma 4适配，体现vLLM持续跟进最新模型生态。
2. **推理性能优化**：MTP共享topk索引缓冲、Triton采样器8-warp优化、DeepSeek V4 eager CUDA graph区域收窄、3D-grid state-copy内核平铺，直接提升吞吐与延迟表现。
3. **硬件生态覆盖**：大量ROCm/XPU提交（AITER MLA后端、TCP store、内核版本升级），强化AMD和Intel平台支持，符合“easy, fast, cheap for everyone”的普惠目标。
4. **架构演进**：Rust前端gRPC数据并行路由、protobuf schema发布至Buf、KV Connector规范化CPU布局，推动服务化与多机扩展能力。

## 三、项目影响与意义

- **稳定性提升**：修复MTP初始化、窗口注意力、音频解码DoS漏洞等关键问题，增强生产环境可靠性。
- **生态兼容性**：升级huggingface-hub、CUTLASS DSL，适配Transformers新版本，降低用户集成成本。
- **开发效率**：CI新增/ci cancel命令、缓存测试依赖、稳定DP supervisor测试，加速迭代节奏。

## 四、值得关注的技术点

- **MTP共享缓冲**：跨draft步骤复用topk索引，减少显存分配开销。
- **3D-grid Triton平铺**：优化state-copy内核的并行效率。
- **安全修复**：音频解码时长校验防DoS，体现安全意识。
- **YAML配置布尔标志修复**：确保`--no-{key}`正确传递，提升配置灵活性。

## 五、对项目发展的影响

vLLM正从“高性能推理引擎”向“全栈LLM服务平台”演进：一方面通过硬件适配和性能优化巩固技术壁垒，另一方面通过gRPC架构、KV offload标准化和部署指南（Crusoe）拓展企业级应用场景。大量AI辅助编码（Codex、Claude、Cursor）参与提交，反映开源项目正加速采用AI工具提升开发效率。整体来看，项目在保持性能领先的同时，正系统性强化多硬件、多模型、多部署形态的兼容性，朝着“人人可用的LLM服务”目标稳步前进。

## 详细提交记录

### [3e174bb](https://github.com/vllm-project/vllm/commit/3e174bb73c70b677dd339c59c39d7460abc5d02d)

- **作者**: Giancarlo Delfin
- **时间**: 2026-08-10T22:46:13Z
- **提交信息**: [Model Runner V2][MTP] Share topk index buffer between draft steps (#47352)

Signed-off-by: Giancarlo Delfin <gdelfin@inferact.ai>
Co-authored-by: Woosuk Kwon <woosuk@inferact.ai>

### [c3cac8c](https://github.com/vllm-project/vllm/commit/c3cac8c63d917759a38e94dfa933e71196de40bb)

- **作者**: Almog Tavor
- **时间**: 2026-08-10T22:36:42Z
- **提交信息**: [Bugfix][MiMo] Apply vision attention sinks in the window attention path (#49815)

Signed-off-by: almogtavor <almogtavor@gmail.com>

### [98a4144](https://github.com/vllm-project/vllm/commit/98a4144a4197c2b96e4df7bfd9c386d4fbdb1f4f)

- **作者**: Tristan Rice
- **时间**: 2026-08-10T22:14:53Z
- **提交信息**: [Bugfix] Preserve non-logitproc entry points in tests (#51097)

Signed-off-by: Tristan Rice <rice@fn.lc>

### [fa722b9](https://github.com/vllm-project/vllm/commit/fa722b9f0188179a66728f2f882e9d5bc92c9b0c)

- **作者**: Connor Carpenter
- **时间**: 2026-08-10T22:05:24Z
- **提交信息**: [Rust Frontend][gRPC] Add explicit data-parallel rank routing (#51178)

Signed-off-by: Connor Carpenter <connorc@nvidia.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [3c6b2e9](https://github.com/vllm-project/vllm/commit/3c6b2e9c08447a7f839c6aa201d2683ab52d267e)

- **作者**: Kevin H. Luu
- **时间**: 2026-08-10T21:55:26Z
- **提交信息**: [CI] Add /ci cancel command (#51732)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [635dd6a](https://github.com/vllm-project/vllm/commit/635dd6aae656f3b47d174461f34d3de799f2dc94)

- **作者**: Connor Carpenter
- **时间**: 2026-08-10T20:34:39Z
- **提交信息**: [Build][gRPC] Publish protobuf schemas to Buf (#51276)

Signed-off-by: Connor Carpenter <connorc@nvidia.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [63ac04a](https://github.com/vllm-project/vllm/commit/63ac04a61e6272b746d82e180e7f6276b3ee1ede)

- **作者**: Summer Yang
- **时间**: 2026-08-10T19:54:26Z
- **提交信息**: [Kimi-K3] DCP support (#50484)

Signed-off-by: girasoley <girasoley@inferact.ai>
Signed-off-by: Summer Yang <girasoleyang@gmail.com>
Signed-off-by: 云挚 <ningyunxiao.nyx@antgroup.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: 云挚 <ningyunxiao.nyx@antgroup.com>
Co-authored-by: foraxe <73625538+foraxe@users.noreply.github.com>
Co-authored-by: Woosuk Kwon <woosuk@inferact.ai>

### [3f142bd](https://github.com/vllm-project/vllm/commit/3f142bd85e962a795c6c484f0249f9c92aed37b2)

- **作者**: Flora Feng
- **时间**: 2026-08-10T19:30:30Z
- **提交信息**: [Bugfix] Align deepseek v4 parser thinking default with tokenizer (#51296)

Signed-off-by: sfeng33 <4florafeng@gmail.com>

### [d40c3e3](https://github.com/vllm-project/vllm/commit/d40c3e3c00ab904928ab51c9c62b7f514c39647d)

- **作者**: xijiaat
- **时间**: 2026-08-10T19:12:19Z
- **提交信息**: Fix DSpark warmup without sparse index buffer (#50693)

Signed-off-by: xijiade.aihemaiti <3146335281@qq.com>
Signed-off-by: xijiaat <52128022+xijiaat@users.noreply.github.com>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [1482d2e](https://github.com/vllm-project/vllm/commit/1482d2e015cc71e6ce0d3d92249cb78f4738f2e7)

- **作者**: Chaitanya Sri Krishna Lolla
- **时间**: 2026-08-10T18:39:26Z
- **提交信息**: [ROCm][DistInf] Enable vLLM DI CI with buildkite/slurm (#47030)

Signed-off-by: lcskrishna <lollachaitanya@gmail.com>
Co-authored-by: Sheral Kumar <shekumar@amd.com>
Co-authored-by: avininjamay8 <Avinash.Paul@amd.com>
Co-authored-by: tej <37236721+itej89@users.noreply.github.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [05f0a80](https://github.com/vllm-project/vllm/commit/05f0a80016a4a12c5f4e241e92e233acd1c2c0b0)

- **作者**: Flora Feng
- **时间**: 2026-08-10T18:29:20Z
- **提交信息**: [Bugfix][Structured Output] Mask request stop tokens in xgrammar until grammar terminates (#49227)

Signed-off-by: sfeng33 <4florafeng@gmail.com>

### [405bc86](https://github.com/vllm-project/vllm/commit/405bc86768d1267f05dd2d4139048eb30a84b6cb)

- **作者**: kiroxu
- **时间**: 2026-08-10T17:55:35Z
- **提交信息**: [Perf] Launch the top-k/top-p Triton sampler kernel with 8 warps (#51507)

Signed-off-by: BabyDrangoner <148877251+BabyDrangoner@users.noreply.github.com>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [79c865b](https://github.com/vllm-project/vllm/commit/79c865b838e34f7a98a936771284773819d79c8f)

- **作者**: Woosuk Kwon
- **时间**: 2026-08-10T17:52:10Z
- **提交信息**: [Perf] Narrow DeepSeek V4 eager CUDA graph region (#51430)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [21c667a](https://github.com/vllm-project/vllm/commit/21c667aa64d4023320fb608b81a343e7f9a47250)

- **作者**: Michael Goin
- **时间**: 2026-08-10T17:34:59Z
- **提交信息**: [Docker] Cache test dependencies before vLLM install (#51184)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [355a338](https://github.com/vllm-project/vllm/commit/355a338b8f54befed4ab23a9f09aff301de26b4f)

- **作者**: wangxiyuan
- **时间**: 2026-08-10T17:33:10Z
- **提交信息**: [BugFix][SpecDecode] Fix dspark parallel_drafting_token_id init bug (#51602)

Signed-off-by: wangxiyuan <wangxiyuan1007@gmail.com>
Co-authored-by: Benjamin Chislett <bchislett@nvidia.com>

### [3a749ce](https://github.com/vllm-project/vllm/commit/3a749ce81600f67e609eeb4a9b2b8da52dac16f2)

- **作者**: Michael Goin
- **时间**: 2026-08-10T16:38:53Z
- **提交信息**: [Build] Skip precompiled wheel fetch during metadata hooks (#51424)

Signed-off-by: mgoin <mgoin64@gmail.com>

### [0e2d780](https://github.com/vllm-project/vllm/commit/0e2d78028c473bb04fc74bf945eb32da29239b0c)

- **作者**: Lyu, Xudong
- **时间**: 2026-08-10T16:05:20Z
- **提交信息**: [Bugfix][Kimi-K3] Give the AMD packed KDA decode kernel the state-index stride (#51682)

Signed-off-by: Lyu, Xudong <xudong.lyu@amd.com>

### [640a090](https://github.com/vllm-project/vllm/commit/640a09086d1b3c129c4e21f85acbf551eb17b4d1)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-08-10T15:49:17Z
- **提交信息**: Fix DoS via sample-rate forgery bypassing audio decode duration guard (#49948)

Signed-off-by: jperezde <jperezde@redhat.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [37fbf52](https://github.com/vllm-project/vllm/commit/37fbf5208413486e5553c1b287af64f6af6afdcf)

- **作者**: fanxingran
- **时间**: 2026-08-10T15:42:10Z
- **提交信息**: [ROCm][MLA] [K3] Fix fp8 KV cache decode on the AITER MLA backend (#51011)

Signed-off-by: fanxingran <xingran.fan@amd.com>

### [8fea1d3](https://github.com/vllm-project/vllm/commit/8fea1d306fdfe9b7f47a8f45114b2bb23e8c0d9b)

- **作者**: Elvir Crnčević
- **时间**: 2026-08-10T15:28:57Z
- **提交信息**: Fix uniform_random routing simulation to sample without replacement (#43680)

Signed-off-by: Elvir Crncevic <elvircrn@gmail.com>
Signed-off-by: Elvir Crnčević <elvircrn@gmail.com>
Signed-off-by: Tyler Michael Smith <tlrmchlsmth@gmail.com>
Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>
Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>
Co-authored-by: Tyler Michael Smith <tlrmchlsmth@gmail.com>

### [fac808b](https://github.com/vllm-project/vllm/commit/fac808b36f502d0d992509a187dca94c68b0360a)

- **作者**: Francesco Fusco
- **时间**: 2026-08-10T15:02:49Z
- **提交信息**: [Perf][Hybrid] 3D-grid tiling of the state-copy Triton kernels (#49436)

Signed-off-by: Francesco Fusco <ffu@zurich.ibm.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [bd65360](https://github.com/vllm-project/vllm/commit/bd6536071cec4dcd8cf91c0e2aa04aec83fc1c37)

- **作者**: liuzhenwei
- **时间**: 2026-08-10T13:57:45Z
- **提交信息**: [XPU][Test] Pin block size in test_multi_connector (#51213)

Signed-off-by: zhenwei-intel <zhenwei.liu@intel.com>

### [ec21f61](https://github.com/vllm-project/vllm/commit/ec21f61d82cfe74723bf51e94beb1a6665fb736e)

- **作者**: pmanczak
- **时间**: 2026-08-10T13:57:02Z
- **提交信息**: [Misc] Enable test_fused_moe_wn16 on XPU (#51672)

Signed-off-by: pmanczak <pawel.manczak@intel.com>

### [ea3115e](https://github.com/vllm-project/vllm/commit/ea3115e30b1288e3e3ecafd3943695d3f06d1eac)

- **作者**: Taneem Ibrahim
- **时间**: 2026-08-10T13:13:52Z
- **提交信息**: [CI] Stabilize DP supervisor lifecycle tests (#51557)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>

### [789c4f9](https://github.com/vllm-project/vllm/commit/789c4f905eb3f5b73a4de98182fd6eb32c55e15f)

- **作者**: Lucas Wilkinson
- **时间**: 2026-08-10T13:06:08Z
- **提交信息**: [CI] Bump CUTLASS DSL to 4.6.2 (#51566)

### [cf8f3a3](https://github.com/vllm-project/vllm/commit/cf8f3a3bb23ef99d956f3763bc7b6b85cacb125b)

- **作者**: Harry Mellor
- **时间**: 2026-08-10T12:57:12Z
- **提交信息**: [2/N] Harden Transformers modelling backend multi-modal path (#51657)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [436be94](https://github.com/vllm-project/vllm/commit/436be94e135fd07fc94e4c165a1b6870af72bf31)

- **作者**: vllmellm
- **时间**: 2026-08-10T11:07:14Z
- **提交信息**: [ROCm][Bugfix] Use TCP store when AITER custom all-reduce is enabled (#51635)

Signed-off-by: vllmellm <vllm.ellm@embeddedllm.com>
Signed-off-by: tjtanaa <tunjian.tan@embeddedllm.com>
Co-authored-by: tjtanaa <tunjian.tan@embeddedllm.com>

### [3dafaef](https://github.com/vllm-project/vllm/commit/3dafaef02735de08f16298bac42fe18dd930d2ee)

- **作者**: Raj Vijay Firke
- **时间**: 2026-08-10T11:05:15Z
- **提交信息**: [Bugfix][Core] Emit --no-{key} for false BooleanOptionalAction flags in YAML config (#51573)

Signed-off-by: Raj Firke <79653531+rajfirke@users.noreply.github.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [900d09f](https://github.com/vllm-project/vllm/commit/900d09f91a1fe164c0df175c334060cad68ce245)

- **作者**: efschu
- **时间**: 2026-08-10T11:04:53Z
- **提交信息**: [Bugfix][Model] Fix Qwen3.5 MTP for text-only checkpoints (#50734)

Signed-off-by: efschu <51944948+efschu@users.noreply.github.com>

### [3a79957](https://github.com/vllm-project/vllm/commit/3a79957b62ade336010cc052e322d0005eb091a2)

- **作者**: Emmanuel Acheampong
- **时间**: 2026-08-10T10:31:34Z
- **提交信息**: [Doc] Add Crusoe Managed Inference deployment guide (#49353)

Signed-off-by: Emmanuel Acheampong <achampion.emma@gmail.com>

### [51562de](https://github.com/vllm-project/vllm/commit/51562de5ab16bacd821d7130187b6bebdd293f93)

- **作者**: xiangdong
- **时间**: 2026-08-10T09:32:16Z
- **提交信息**: [CI][XPU] Add VLLM_DISABLE_COMPILE_CACHE=1 for other random failed cases in Intel GPU CI (#51604)

Signed-off-by: zengxian <xiangdong.zeng@intel.com>

### [243c63b](https://github.com/vllm-project/vllm/commit/243c63baf5239f961305e25160c1bf6d34096df4)

- **作者**: Jiangyun Zhu
- **时间**: 2026-08-10T08:37:17Z
- **提交信息**: [V1][Scheduler] Apply Mamba alignment before encoder caps (#51603)

Signed-off-by: Jiangyun Zhu <riverclouds.zhu@qq.com>
Co-authored-by: Akshat Anand <40275336+cipheraxat@users.noreply.github.com>
Co-authored-by: Codex <codex@openai.com>

### [d89ba64](https://github.com/vllm-project/vllm/commit/d89ba6481bd0cbe99e1c83ed169131682b366dbd)

- **作者**: Kunshang Ji
- **时间**: 2026-08-10T08:09:23Z
- **提交信息**: [XPU] bump up xpu kernel to v0.1.12.3 (#50441)

Signed-off-by: Kunshang Ji <kunshang.ji@intel.com>

### [74c94b9](https://github.com/vllm-project/vllm/commit/74c94b9f29ff946647870299e7dbc8d41b206060)

- **作者**: Andreas Karatzas
- **时间**: 2026-08-10T07:59:15Z
- **提交信息**: [CI] Upgrade huggingface-hub to 1.27.0 (#51422)

Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [70b84f0](https://github.com/vllm-project/vllm/commit/70b84f0bcbb6d0a35b74b1035673a1c934089dbb)

- **作者**: Harry Mellor
- **时间**: 2026-08-10T07:48:26Z
- **提交信息**: Fix Gemma 4 for upcoming Transformers version (#49797)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [81840a1](https://github.com/vllm-project/vllm/commit/81840a172f2886f4c59dafd9dce9917bb789280c)

- **作者**: Itay Etelis
- **时间**: 2026-08-10T07:44:54Z
- **提交信息**: [KV Connector] Canonical CPU layout for parallelism-agnostic KV offload (#48414)

Signed-off-by: Itay Etelis <itay.etelis@ibm.com>
Co-authored-by: Itay Etelis <itay.etelis@ibm.com>

### [31cd109](https://github.com/vllm-project/vllm/commit/31cd109f18f1ff49cef8dfd25329e7c49d0f2310)

- **作者**: Andreas Karatzas
- **时间**: 2026-08-10T07:35:13Z
- **提交信息**: [ROCm][CI] Extend ROCm AITER MHA (FA) coverage (#40958)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Signed-off-by: Micah Williamson <micah.williamson@amd.com>
Co-authored-by: Micah Williamson <micah.williamson@amd.com>

### [7303c66](https://github.com/vllm-project/vllm/commit/7303c66f68ea87573cf29d9a678748a73c8e8c6d)

- **作者**: Zetian Li - ikun
- **时间**: 2026-08-10T07:10:06Z
- **提交信息**: [Bugfix] Fix lfm2 tool parser dropping calls with brackets or newline… (#48171)

Signed-off-by: Zetian Li <804561096@qq.com>
Co-authored-by: Claude (Anthropic) <noreply@anthropic.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-08-11
**监控日期**: 2026-08-10
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 6022
- **最后更新**: 2026-08-10T21:50:21Z

## 提交统计

- **昨日提交总数**: 12
- **提交者数量**: 8
- **主要提交者**: R0CKSTAR, ooooooye, Zeyu Huang | 黃澤宇

## AI分析总结

# vLLM-Omni 昨日提交分析报告

## 一、主要更新类型

本次提交涵盖**Bug修复**（3项）、**性能优化**（2项）、**文档更新**（4项）、**代码重构**（1项）、**基准测试更新**（1项）及**仓库维护**（1项），整体以稳定性和体验优化为主。

## 二、关键变更点

1. **Rainfusion视频支持全面化**：修复了此前仅支持特定形状视频的限制，使该模型能够处理任意形状的视频输入，显著提升模型适用性。
2. **TTS Ratchet容错改进**：修复了分支计数下降时系统崩溃的问题，增强了TTS推理链路的健壮性。
3. **TeaCache FakeBackend恢复**：修复了`supports_packed_mask_free`属性缺失问题，确保Diffusion模型缓存机制正常工作。
4. **MiniMax-H3性能优化**：在NPU上启用packed varlen attention，消除二次方掩码物化开销；同时在MUSA平台恢复动态RoPE融合，实现跨硬件平台性能提升。
5. **调度器准入等待策略重构**：对请求调度器的准入等待策略进行核心重构，为后续调度优化奠定架构基础。

## 三、项目影响与意义

- **多模态能力增强**：Rainfusion的视频形状支持扩展了项目“omni-modality”的核心定位，使更多视频输入场景成为可能。
- **跨平台性能提升**：MiniMax-H3在NPU和MUSA上的优化体现了项目对多样化硬件生态的重视，有助于降低推理成本。
- **稳定性提升**：TTS和TeaCache的Bug修复减少了生产环境中的潜在故障点，提升用户体验。
- **文档与导航优化**：多项文档改进（如修复链接、保留量化URL、共享任务导航）降低了用户上手门槛，提升项目可发现性。

## 四、值得关注的技术点

- **packed varlen attention**在NPU上的应用是消除掩码物化开销的关键技术，对长序列Diffusion推理有显著加速效果。
- **调度器准入等待策略重构**可能影响后续请求排队和资源分配逻辑，是架构层面的重要调整。
- **CODEOWNERS对齐设计文档**表明项目正在规范化维护流程，提升协作效率。

## 五、对项目发展的影响

vLLM-Omni定位为“人人可用的多模态模型服务”，本次提交通过修复关键Bug、优化跨硬件性能、完善文档体系，稳步推进了这一目标。特别是MiniMax-H3在NPU和MUSA上的性能优化，直接响应了“fast and cheap”的核心理念，降低了多模态推理的硬件门槛。调度器重构则为未来更复杂的多模态工作负载做好了架构准备。整体来看，项目正从功能完善阶段向性能优化和生态建设阶段过渡，发展态势健康。

## 详细提交记录

### [c27623c](https://github.com/vllm-project/vllm-omni/commit/c27623c29c62365424d4633e2d45f01d9eebf039)

- **作者**: fan2956
- **时间**: 2026-08-10T21:10:50Z
- **提交信息**: [Bugfix] rainfusion support all shape video (#6000)

Signed-off-by: Fan <fan@FandeMacBook-Air.local>
Co-authored-by: Fan <fan@FandeMacBook-Air.local>

### [f8fa86f](https://github.com/vllm-project/vllm-omni/commit/f8fa86fb1fbd6a09e79b59404af9fc568d08bf08)

- **作者**: Yueqian Lin
- **时间**: 2026-08-10T21:08:31Z
- **提交信息**: [BugFix] Don't fail the TTS ratchet when the branch count goes down (#6008)

Signed-off-by: Yueqian Lin <linyueqian@outlook.com>

### [422d8fd](https://github.com/vllm-project/vllm-omni/commit/422d8fd8f9313176802b792e41a30fcd286d6408)

- **作者**: ooooooye
- **时间**: 2026-08-10T14:20:37Z
- **提交信息**: [Bugfix][Diffusion] Restore supports_packed_mask_free on teacache FakeBackend (#5997)

Signed-off-by: brandneway <gyuan4892@gmail.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [62e239b](https://github.com/vllm-project/vllm-omni/commit/62e239bf1e7e53240873ada6c18a4ac11ada8828)

- **作者**: Hongsheng Liu
- **时间**: 2026-08-10T13:55:01Z
- **提交信息**: [Docs] Fix broken attention backend link (#5998)

Signed-off-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [740f45a](https://github.com/vllm-project/vllm-omni/commit/740f45abcd2e6754d1cdded01ee9901d595ccac5)

- **作者**: ooooooye
- **时间**: 2026-08-10T11:47:03Z
- **提交信息**: [Perf][Diffusion] MiniMax-H3: opt into packed varlen attention on NPU to eliminate quadratic mask materialization (#5891)

Signed-off-by: brandneway <gyuan4892@gmail.com>

### [5e4b9f8](https://github.com/vllm-project/vllm-omni/commit/5e4b9f8c6e503080f16595c578139d37759de1bb)

- **作者**: Hongsheng Liu
- **时间**: 2026-08-10T11:25:03Z
- **提交信息**: [Misc] Align CODEOWNERS with module/feature design docs (#5958)

Signed-off-by: hsliu_ustc <hsliu_ustc@noreply.gitcode.com>
Signed-off-by: Hongsheng Liu <liuhongsheng4@huawei.com>
Co-authored-by: hsliu_ustc <hsliu_ustc@noreply.gitcode.com>
Co-authored-by: Copilot Autofix powered by AI <175728472+Copilot@users.noreply.github.com>

### [ae81104](https://github.com/vllm-project/vllm-omni/commit/ae811043e9a3245f68e457903df77c49799b11fd)

- **作者**: Hongsheng Liu
- **时间**: 2026-08-10T11:13:52Z
- **提交信息**: docs: keep shared task examples in navigation (#5987)

Signed-off-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [636d44e](https://github.com/vllm-project/vllm-omni/commit/636d44e27266f794f1a440867e78f25c20cf3185)

- **作者**: R0CKSTAR
- **时间**: 2026-08-10T09:24:46Z
- **提交信息**: [Perf][MUSA] Restore MiniMax-H3 dynamic RoPE fusion (#5881)

Signed-off-by: Xiaodong Ye <xiaodong.ye@mthreads.com>

### [8e44e78](https://github.com/vllm-project/vllm-omni/commit/8e44e78038766b44832d6f9fd7000909517cd1cd)

- **作者**: yiminghub2024
- **时间**: 2026-08-10T07:51:15Z
- **提交信息**: Add Ref2VA measurements to the MiniMax-H3 DGX Spark (GB10) recipe (#5972)

Signed-off-by: yiminghub2024 <482890@qq.com>

### [b98b7c8](https://github.com/vllm-project/vllm-omni/commit/b98b7c852969f737b944120e4aaa0447b644d4e2)

- **作者**: Hongsheng Liu
- **时间**: 2026-08-10T07:45:50Z
- **提交信息**: [Docs] Preserve generated quantization URLs and link recipes in supported models (#5969)

Signed-off-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [1ee2fff](https://github.com/vllm-project/vllm-omni/commit/1ee2fff532113c05d26f5fd51cb72dd3b9799eed)

- **作者**: bjf-frz
- **时间**: 2026-08-10T07:24:59Z
- **提交信息**: Update Wan2.2 I2V performance baselines (#5977)

Signed-off-by: bjf-frz <frz123db@gmail.com>
Co-authored-by: Alicia <115451386+congw729@users.noreply.github.com>

### [33dd9a5](https://github.com/vllm-project/vllm-omni/commit/33dd9a5a3e03fdae300957ce9ccffe710d8e8c86)

- **作者**: Zeyu Huang | 黃澤宇
- **时间**: 2026-08-10T07:06:27Z
- **提交信息**: [Core][Refactor][Diffusion] refactor request scheduler's admission wait policy (#5843)

Signed-off-by: Huang, Zeyu <11222265+fhfuih@users.noreply.github.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

---
