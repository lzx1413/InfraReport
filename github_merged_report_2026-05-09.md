# GitHub Stars 合并报告 - 2026-05-09

**合并日期**: 2026-05-10
**监控日期**: 2026-05-09
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


**报告日期**: 2026-05-10
**监控日期**: 2026-05-09
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 1904
- **最后更新**: 2026-05-09T07:24:13Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-05-10
**监控日期**: 2026-05-09
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Light Image Video Generation Inference Framework
- **语言**: Python
- **星标数**: 2251
- **最后更新**: 2026-05-09T12:45:08Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-05-10
**监控日期**: 2026-05-09
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2067
- **最后更新**: 2026-05-09T15:58:18Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-05-10
**监控日期**: 2026-05-09
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5581
- **最后更新**: 2026-05-09T15:27:16Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Jonathan Dierksen

## AI分析总结

好的，这是对 `flashinfer-ai/flashinfer` 仓库昨日提交记录的分析总结。

### 1. 主要更新类型

*   **CI/构建系统优化**：本次提交主要围绕持续集成（CI）和构建流程进行优化，属于基础设施层面的改进。

### 2. 关键变更点及其与项目整体方向的关系

*   **变更点**：将支持 `sm110` (CUDA 11.0a) 架构的构建限制在 `aarch64` (ARM64) 平台上，并从 `x86_64` 平台的构建列表中移除。
*   **与项目方向的关系**：
    *   **目标平台精准化**：`sm110` 架构主要对应 NVIDIA 的 Jetson AGX Thor / T5000 等嵌入式或边缘计算平台，这些平台通常采用 ARM 架构。此变更确保了为特定硬件（ARM + 特定 GPU）生成的 FlashInfer 内核是精确且高效的，避免了在 x86_64 平台上为不存在的硬件进行不必要的编译。
    *   **提升构建效率**：减少 `x86_64` 平台的构建目标数量，可以缩短 CI 流水线的执行时间，加快开发和测试迭代速度。
    *   **维护项目专业性**：FlashInfer 的目标是提供高性能推理内核，支持多种硬件平台。此变更体现了团队对硬件兼容性和构建流程精细化管理的能力，确保项目能更好地服务于不同的部署场景（从数据中心到边缘设备）。

### 3. 对项目的影响和潜在意义

*   **直接影响**：
    *   **x86_64 用户**：在 x86_64 系统上使用 CUDA 13.0 构建 FlashInfer 时，将不再包含 `sm110` 的内核，这可能会略微减少安装包体积和编译时间。
    *   **aarch64 用户**：在 ARM 平台（如 Jetson）上，`sm110` 内核的构建和支持保持不变，确保了这些平台上的功能完整性。
*   **潜在意义**：
    *   **为未来架构做准备**：这种架构分离的做法，为未来可能出现的更多、更细分的硬件架构支持奠定了基础，使得项目可以更灵活地适配不同的硬件组合。
    *   **提升项目健壮性**：修复了 sccache 缓存系统的凭证处理逻辑，确保了在 CI 环境中缓存功能的稳定运行，这对于大型项目的持续集成至关重要。

### 4. 值得关注的技术点

*   **sccache 凭证处理优化**：提交中修复了 `sccache` 匿名 S3 缓存的设置问题。通过清除空的 AWS 凭证环境变量，再设置 `SCCACHE_S3_NO_CREDENTIALS=true`，确保了在无凭证环境下能正确切换到只读缓存模式。这是一个典型的 CI 环境配置优化技巧，值得其他项目借鉴。
*   **架构检测的健壮性**：测试部分提到验证了 CUDA 13 架构检测能标准化处理 `AARCH64`、`ARM64` 和 `X86_64` 等不同大小写的输入，这体现了代码的健壮性。

### 5. 基于项目背景的分析：这些提交如何影响项目发展

*   **强化“高性能推理”定位**：通过精准控制不同平台上的内核编译，FlashInfer 能够为特定硬件生成最优化的代码，避免“一刀切”带来的性能或兼容性问题。这直接支持了其“为推理提供高性能 GPU 内核”的核心目标。
*   **拓展生态支持**：明确区分 x86_64 和 aarch64 的构建，表明项目正在积极支持更广泛的硬件生态，特别是面向边缘计算和嵌入式场景的 ARM 平台（如 Jetson）。这有助于 FlashInfer 在 AI 推理的多样化部署场景中获得更广泛的应用。
*   **提升开发者体验**：优化 CI 流程（减少不必要的构建、修复缓存问题）能显著提升开发者的迭代效率，降低维护成本，使团队能更专注于核心算法和性能优化，从而推动项目更快发展。

## 详细提交记录

### [0a128d1](https://github.com/flashinfer-ai/flashinfer/commit/0a128d112af75de403769dd4e53edcfcc165afb9)

- **作者**: Jonathan Dierksen
- **时间**: 2026-05-09T15:27:11Z
- **提交信息**: ci(jit-cache): limit sm110 builds to aarch64 (#3275)

## Summary

- Removes `11.0a` / `sm110` from CUDA 13.0 x86_64 flashinfer-jit-cache
build arch lists.
- Keeps `11.0a` for CUDA 13.0 aarch64 builds, where Jetson AGX Thor /
T5000 targets live.
- Mirrors the same architecture split in the PR AOT build/import script.
- Fixes sccache anonymous S3 setup by clearing empty AWS credential
environment variables before setting `SCCACHE_S3_NO_CREDENTIALS=true`.

## Testing

- Parsed `release.yml`, `nightly-release.yml`, and `pr-test.yml` with
`yaml.safe_load`.
- Ran `bash -n scripts/task_test_jit_cache_package_build_import.sh`.
- Ran `bash -n scripts/jit_cache_build_common.sh
scripts/task_test_jit_cache_package_build_import.sh
scripts/build_flashinfer_jit_cache_whl.sh`.
- Mocked `setup_sccache` with empty AWS credential variables and
verified read-only anonymous mode unsets them before starting sccache.
- Mocked `setup_sccache` with non-empty AWS credentials and verified
read-write mode leaves `SCCACHE_S3_NO_CREDENTIALS` unset.
- Verified CUDA 13 architecture detection normalizes uppercase
`AARCH64`, `ARM64`, and `X86_64` inputs.
- Ran `git diff --check`.
- Verified generated CUDA 13 arch lists:
  - `x86_64`: `7.5 8.0 8.9 9.0a 10.0a 10.3a 12.0f`
  - `aarch64` / `arm64`: `7.5 8.0 8.9 9.0a 10.0a 10.3a 11.0a 12.0f`


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Chores**
* Adjusted CUDA architecture selection to choose ARM-specific CUDA
targets on aarch64 hosts, and a different list on non-ARM hosts, across
release and nightly build workflows and test scripts.
* Improved build-cache credential handling: read-write mode now requires
explicit AWS credentials; otherwise the workflow falls back to read-only
mode.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: dierksen <dierksen@dierksen-spark.localdomain>
Co-authored-by: Alex Yang <aleyang@nvidia.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-05-10
**监控日期**: 2026-05-09
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3460
- **最后更新**: 2026-05-09T20:06:58Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Aryan Kumar, William Lin

## AI分析总结

好的，根据您提供的仓库README摘要和提交记录，以下是昨日更新的要点分析：

### 1. 主要更新类型
- **功能新增 (feat)**: 新增了“LongCat”双向微调支持。
- **杂项/基础设施 (misc)**: 将“添加模型”技能栈导入到 `.agents/skills/` 目录下。

### 2. 关键变更点及其与项目整体方向的关系
- **`[feat]: add LongCat bidirectional finetuning support`**:
    - **变更点**: 为项目新增了名为“LongCat”的双向微调功能。
    - **与项目方向的关系**: FastVideo 是一个专注于视频生成的快速训练/微调框架。新增微调方法直接服务于项目的核心目标——提供更高效、更强大的视频模型定制能力。双向微调可能意味着模型在训练时能同时利用正向和反向的时序信息，这对于提升视频生成的质量和连贯性至关重要。

- **`[misc]: import add-model skill stack to .agents/skills/`**:
    - **变更点**: 将“添加模型”相关的技能栈代码整合到项目的智能体（agents）技能（skills）目录中。
    - **与项目方向的关系**: 这表明项目正在构建一个智能体（Agent）系统，用于自动化或辅助用户完成模型操作。将“添加模型”作为一项标准技能，是朝着“用户可以通过自然语言或简单指令与框架交互，完成复杂工作流”这一方向迈出的重要一步，提升了项目的易用性和自动化水平。

### 3. 对项目的影响和潜在意义
- **LongCat 双向微调**:
    - **影响**: 直接扩展了框架支持的微调算法库，为用户提供了新的、可能更优的训练选项。
    - **潜在意义**: 如果“LongCat”方法在长视频生成或时序一致性方面有显著优势，它将成为FastVideo区别于其他框架的核心竞争力之一，吸引更多需要高质量长视频生成能力的用户。

- **Agent 技能栈整合**:
    - **影响**: 标志着项目从“纯代码库”向“智能平台”的演进。代码结构更加模块化，为未来集成更多自动化功能（如自动调参、模型评估、部署等）奠定了基础。
    - **潜在意义**: 这降低了用户的使用门槛，尤其是对非专业开发者。未来用户可能只需通过对话式指令就能完成复杂的模型训练和部署任务，极大地提升了项目的可访问性和生态潜力。

### 4. 值得关注的技术点
- **双向微调 (Bidirectional Finetuning)**: 这是一种特定的训练策略，可能涉及修改模型架构或损失函数，以在训练过程中同时考虑过去和未来的帧信息。这对于解决视频生成中的“闪烁”或“不连贯”问题可能非常有效。
- **Agent 与 Skills 架构**: 项目采用了类似“智能体-技能”的架构模式。这是一种前沿的AI应用开发范式，将复杂任务分解为可组合的技能单元。`add-model` 技能的实现方式（例如，是否使用了函数调用、工具使用等）是值得关注的技术实现细节。

### 5. 基于项目背景，这些提交如何影响项目发展
- **强化核心能力**: `LongCat` 微调功能的加入，直接增强了FastVideo在**视频生成模型定制**这一核心赛道上的技术深度和竞争力，使其能更好地满足用户对特定风格、场景或长视频的生成需求。
- **推动智能化转型**: `Agent` 技能的整合，是FastVideo从“一个强大的训练工具”向“一个智能的创作平台”转型的关键一步。这与README中提到的“Weekly Dev Meeting”和社区建设目标一致，旨在通过降低使用门槛和提升自动化水平，吸引更广泛的用户群体，构建更活跃的开发者社区。
- **构建差异化优势**: 通过同时强化底层算法（微调）和上层交互（Agent），FastVideo正在构建一个从技术到体验的完整闭环。这种“硬核技术 + 智能易用”的组合，有助于其在众多视频生成框架中脱颖而出。

## 详细提交记录

### [e3a5c69](https://github.com/hao-ai-lab/FastVideo/commit/e3a5c6954f49bb48ab72455df5f2f03cdab913dd)

- **作者**: William Lin
- **时间**: 2026-05-09T20:06:54Z
- **提交信息**: [misc]: import add-model skill stack to .agents/skills/ (#1308)

Co-authored-by: Raghav <ragg04@gmail.com>

### [f633e30](https://github.com/hao-ai-lab/FastVideo/commit/f633e30ebb0efa61db3a537f10acb49e1d171949)

- **作者**: Aryan Kumar
- **时间**: 2026-05-09T19:20:43Z
- **提交信息**: [feat]: add LongCat bidirectional finetuning support (#1244)

Co-authored-by: Aryan Kumar <aryan5v@users.noreply.github.com>
Co-authored-by: alexzms <3036648523@qq.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-05-10
**监控日期**: 2026-05-09
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 33586
- **最后更新**: 2026-05-09T17:10:58Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-05-10
**监控日期**: 2026-05-09
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 402
- **最后更新**: 2026-05-09T07:54:38Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-05-10
**监控日期**: 2026-05-09
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12386
- **最后更新**: 2026-05-09T22:27:42Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-05-10
**监控日期**: 2026-05-09
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 27572
- **最后更新**: 2026-05-09T23:17:00Z

## 提交统计

- **昨日提交总数**: 17
- **提交者数量**: 12
- **主要提交者**: Baizhou Zhang, R0CKSTAR, Brayden Zhong

## AI分析总结

好的，这是对 `sgl-project/sglang` 仓库昨日提交记录的分析总结。

### 1. 主要更新类型

-   **Bug修复**：数量最多，涉及多个模块，包括Eagle3推测解码、CUDA图、NPU分析器、GLM模型等。
-   **功能新增/增强**：支持了新的模型架构（Gemma3/4 + Eagle3），并增强了DeepSeek V4分支的测试。
-   **性能优化**：修复了DeepSeek V3在特定后端（`moe-runner-backend=triton`）和架构（SM90）上的性能回退问题，并启用了PDL（Performance Dynamic Library）以优化特定内核。
-   **重构/清理**：清理了推测解码模块中无效的参数、返回值和操作。
-   **其他**：更新了`CODEOWNERS`文件，优化了Slash命令的用户体验，并回滚了一个有问题的NPU修复。

### 2. 关键变更点及其与项目整体方向的关系

-   **支持新模型架构 (Gemma3/4 + Eagle3)**：直接扩展了项目支持的模型范围，符合README中“快速、高效”服务大模型的宗旨，增强了项目的通用性和吸引力。
-   **修复DeepSeek V3/V4相关问题**：DeepSeek系列模型是当前社区热点，修复其性能回退和增强测试，直接提升了项目在主流模型上的稳定性和竞争力，与项目“提供高性能推理引擎”的核心目标高度一致。
-   **修复Eagle3推测解码 (Speculative Decoding) 的准确性**：Eagle3是先进的推测解码技术，修复其与FlashAttention3的交互问题（`fa3`）和混合滑动窗口注意力（`hybrid-SWA`）的精度问题，直接提升了推理加速技术的可靠性，是项目在“前沿技术”方向上的重要维护。
-   **启用PDL和Cute-DSL FP4内核**：这些是底层性能优化技术。PDL允许动态加载优化后的内核，Cute-DSL FP4则针对低精度计算进行优化。这表明项目持续在底层计算效率上进行投入，以追求更低的延迟和更高的吞吐量。
-   **修复GLM-5.1模型Bug**：支持GLM系列模型是项目多元化模型支持的一部分，修复其特定Bug（如`page_indice_batch_offset`、`draft worker`初始化）确保了该模型用户的体验。

### 3. 对项目的影响和潜在意义

-   **提升稳定性和准确性**：大量的Bug修复，特别是针对Eagle3和DeepSeek V3/V4的修复，将显著提升这些关键功能在生产环境下的稳定性和输出质量。
-   **增强模型生态兼容性**：支持Gemma3/4 + Eagle3，使项目能服务于更广泛的用户群体，巩固其作为通用推理框架的地位。
-   **巩固性能优势**：修复性能回退和启用新的底层优化（PDL, FP4），有助于维持和提升项目在推理速度上的领先地位，尤其是在NVIDIA最新架构（SM90）上。
-   **改善开发者体验**：清理无效代码、更新`CODEOWNERS`、优化Slash命令UX，这些工作虽然不直接面向最终用户，但能提升项目内部的可维护性和开发效率。

### 4. 值得关注的技术点

-   **Eagle3 + FlashAttention3 + CUDA Graph的协同修复**：提交 `[d5564c2]` 和 `[a309f1f]` 共同指向了Eagle3推测解码在结合FlashAttention3和CUDA Graph时遇到的复杂内存和精度问题。这揭示了在实现高性能推测解码时，需要精细处理注意力掩码、页表和缓存之间的交互。
-   **`moe-runner-backend=triton` 的性能回退修复**：提交 `[4b23f6b]` 专门修复了DeepSeek V3在使用Triton作为MoE运行后端时的性能问题。这表明项目对不同后端的性能调优非常细致，也暗示了Triton后端在特定场景下可能存在优化空间。
-   **PDL（Performance Dynamic Library）的启用**：提交 `[05d1ab5]` 为多个内核启用了PDL。这是一种将性能关键代码编译成动态库，在运行时按需加载的技术，有助于减少启动时间并实现更灵活的优化分发。
-   **`fa_skip_kv_cache` 的限制**：提交 `[fd63641]` 将`fa_skip_kv_cache`功能限制在非MLA（Multi-Head Latent Attention）后端。这暗示了MLA架构（如DeepSeek V2/V3使用）与FlashAttention的`skip_kv_cache`特性可能存在不兼容或性能问题，需要进行特殊处理。

### 5. 基于项目背景，这些提交如何影响项目发展

根据README，SGLang的目标是成为一个**快速、高效、功能丰富**的大模型推理和服务引擎。

-   **“快速”**：通过修复DeepSeek V3的性能回退、启用PDL和FP4 GEMM内核，项目在底层计算效率上持续精进，直接支撑了“快速”这一核心目标。
-   **“高效”**：支持Eagle3等推测解码技术本身就是一种“高效”的体现。修复其准确性Bug，确保了这种“高效”是可靠的。同时，清理无效代码也提升了项目自身的“高效”性。
-   **“功能丰富”**：支持Gemma3/4 + Eagle3、修复GLM-5.

## 详细提交记录

### [c95454b](https://github.com/sgl-project/sglang/commit/c95454b34176fbc0da5ad031d646e71340d8bb50)

- **作者**: Liangsheng Yin
- **时间**: 2026-05-09T22:53:31Z
- **提交信息**: speculative: drop dead params/returns/no-ops (#24865)

### [b735ca1](https://github.com/sgl-project/sglang/commit/b735ca178c9c60ed5f66a3c5428212a7b02a17c4)

- **作者**: R0CKSTAR
- **时间**: 2026-05-09T21:45:13Z
- **提交信息**: Update CODEOWNERS for /sgl-kernel/csrc/musa (#24746)

Signed-off-by: Xiaodong Ye <xiaodong.ye@mthreads.com>

### [12f42f2](https://github.com/sgl-project/sglang/commit/12f42f2e7e7520bef573230cadbdf6c10241aa61)

- **作者**: Charles Chen
- **时间**: 2026-05-09T20:34:56Z
- **提交信息**: Support Gemma3/4 + Eagle3 (#23976)

### [8087e07](https://github.com/sgl-project/sglang/commit/8087e07d52eede91414d7c1b9b323c98b1cf2dbf)

- **作者**: luchangli
- **时间**: 2026-05-09T15:52:22Z
- **提交信息**: [UnifiedRadixTree]: Align cache_empty_result with RadixTree (#24779)

Co-authored-by: Zhangheng <hzh0425@apache.org>

### [ef5e9f8](https://github.com/sgl-project/sglang/commit/ef5e9f8abab18609c42af4b1a1844ab21f76be0e)

- **作者**: Baizhou Zhang
- **时间**: 2026-05-09T11:15:37Z
- **提交信息**: [DSV4] Cherry pick missing commits from deepseek_v4 branch and enhance tests (#24793)

Co-authored-by: Xinyuan Tong <115166877+JustinTong0323@users.noreply.github.com>
Co-authored-by: yueming-yuan <yym022502@gmail.com>

### [4b23f6b](https://github.com/sgl-project/sglang/commit/4b23f6bdc50e45b8ae27c8e59bec3f62ea31bd9b)

- **作者**: Brayden Zhong
- **时间**: 2026-05-09T10:49:12Z
- **提交信息**: Fix performance regression on Deepseek V3 on `moe-runner-backend=triton` on SM90 (#24562)

Co-authored-by: b8zhong <b8zhong@users.noreply.github.com>

### [05d1ab5](https://github.com/sgl-project/sglang/commit/05d1ab51e87bc1a9e3f38065de1c646073ac23a1)

- **作者**: Brayden Zhong
- **时间**: 2026-05-09T10:42:56Z
- **提交信息**: Enable PDL for various kernels in DSV32/GLM5 (#23965)

Co-authored-by: b8zhong <b8zhong@users.noreply.github.com>

### [d5564c2](https://github.com/sgl-project/sglang/commit/d5564c2a962af23a0085cae5d08a75cf939bc3ba)

- **作者**: shuwenn
- **时间**: 2026-05-09T10:22:45Z
- **提交信息**: fix(fa3): translate page table to SWA loc in EAGLE3 topk>1 spec metadata (#24617)

### [a309f1f](https://github.com/sgl-project/sglang/commit/a309f1f8f4cb73dffa58010a1c37f569bb535b48)

- **作者**: JoyFuture
- **时间**: 2026-05-09T10:22:12Z
- **提交信息**: fix(cuda_graph): zero out_cache_loc_swa on pad and use int32 (hybrid-SWA accuracy fix) (#24743)

### [ba625d5](https://github.com/sgl-project/sglang/commit/ba625d529060264fdb176dae4b5ef8823e2cb9f9)

- **作者**: Liangsheng Yin
- **时间**: 2026-05-09T10:19:24Z
- **提交信息**: slash command rerun UX: emoji semantics + result writeback (#24802)

### [f4b7e73](https://github.com/sgl-project/sglang/commit/f4b7e7369978f54328b47c774e6ee59f0c9faed7)

- **作者**: Brayden Zhong
- **时间**: 2026-05-09T10:14:17Z
- **提交信息**: Enable trtllm-gen BF16 MoE for MTP (#24260)

Co-authored-by: b8zhong <b8zhong@users.noreply.github.com>

### [f1a9a45](https://github.com/sgl-project/sglang/commit/f1a9a455e0401587c2fde2477d0a55d0977c0308)

- **作者**: sglang-npu-bot
- **时间**: 2026-05-09T09:53:02Z
- **提交信息**: Revert "[NPU] fix profiler on npu" (#24815)

### [e2527df](https://github.com/sgl-project/sglang/commit/e2527df8b6a174ffba33b8857f2f7350d5ebbe20)

- **作者**: zhaozx-cn
- **时间**: 2026-05-09T09:48:24Z
- **提交信息**: [NPU] fix profiler on npu (#24685)

Signed-off-by: zhaozx-cn <zhaozx2116@163.com>

### [fd63641](https://github.com/sgl-project/sglang/commit/fd636410a20977e9253dba1114328d37b9b066ef)

- **作者**: Jia Guo
- **时间**: 2026-05-09T09:25:02Z
- **提交信息**: Restrict fa_skip_kv_cache to non-MLA backends (#24097)

### [8f33bee](https://github.com/sgl-project/sglang/commit/8f33bee31ba3d0f21f7c282b2438aef912f4428c)

- **作者**: Brayden Zhong
- **时间**: 2026-05-09T09:20:58Z
- **提交信息**: Reland Cute-DSL FP4 dense GEMM (#23590)

Co-authored-by: b8zhong <b8zhong@users.noreply.github.com>

### [d49fc09](https://github.com/sgl-project/sglang/commit/d49fc092cb424187ae4e0979125a73f64cb0be4c)

- **作者**: Yuxuan Zhang
- **时间**: 2026-05-09T07:43:45Z
- **提交信息**: [Bug Fix] GLM-5.1: drop constexpr on page_indice_batch_offset, skip offloader post_init on draft worker, support N=32 in copy_to_gpu_no_ce (#23550)

### [9d12f9e](https://github.com/sgl-project/sglang/commit/9d12f9e6fa87cb98ec72b6d675bd3ea7c3dc7005)

- **作者**: shuwenn
- **时间**: 2026-05-09T07:33:18Z
- **提交信息**: [HiCache] ci: lower est_time for test_hicache_spec_file_storage (#24713)

Co-authored-by: Claude Opus 4.7 (1M context) <noreply@anthropic.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-05-10
**监控日期**: 2026-05-09
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization for Diffusion Transformers.
- **语言**: Python
- **星标数**: 1166
- **最后更新**: 2026-05-09T15:00:28Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

好的，根据您提供的项目背景和提交记录，以下是昨日更新的要点分析：

### 昨日更新要点总结

1.  **主要更新类型**
    *   **功能新增 (Feature)**: 本次提交的核心是新增了一个功能模块。

2.  **关键变更点及其与项目整体方向的关系**
    *   **变更点**: 新增了对 `ray wrapper` 的支持（`feat: support ray wrapper`）。
    *   **与项目方向的关系**: `cache-dit` 是一个面向 Diffusion Transformers 的 PyTorch 原生推理引擎，其核心能力包括缓存、并行化和量化。引入 `ray` 支持，直接强化了项目的 **“并行化 (Parallelism)”** 能力。Ray 是一个流行的分布式计算框架，允许将计算任务扩展到多台机器或多个 GPU 上。这使 `cache-dit` 能够处理更大规模的推理请求，或加速单个大模型的推理过程。

3.  **对项目的影响和潜在意义**
    *   **提升可扩展性**: 使得 `cache-dit` 能够从单机推理无缝扩展到分布式集群，满足生产环境中高吞吐、低延迟的推理需求。
    *   **简化分布式部署**: 通过集成 Ray，用户无需手动管理复杂的分布式计算逻辑，可以更便捷地利用 Ray 提供的资源调度、任务分发和容错机制。
    *   **增强竞争力**: 在 AI 模型推理领域，支持分布式部署是衡量一个推理引擎成熟度和实用性的重要指标。此更新显著提升了 `cache-dit` 在工业级应用中的竞争力。

4.  **值得关注的技术点**
    *   **Ray Wrapper 的设计**: 虽然提交信息未提供具体实现细节，但值得关注的是这个 Wrapper 是如何设计的。它可能封装了模型加载、推理调用、结果收集等流程，并利用 Ray 的 Actor 或 Task 模型来实现并行。其设计的优劣将直接影响分布式推理的性能和易用性。
    *   **与现有并行策略的集成**: `cache-dit` 本身可能已有其他并行策略（如 Tensor Parallelism, Pipeline Parallelism）。Ray Wrapper 如何与这些策略协同工作，是技术实现上的一个关键点。

5.  **基于项目背景，这些提交如何影响项目发展**
    *   **从“引擎”迈向“平台”**: 结合 README 中“PyTorch-native Inference Engine”的定位，支持 Ray 意味着 `cache-dit` 不再仅仅是一个单机推理库，而是具备了成为分布式推理平台核心组件的能力。这为项目吸引需要大规模部署 Diffusion Transformer 模型的企业用户奠定了基础。
    *   **补齐关键拼图**: 对于一个强调“并行化”的引擎来说，支持 Ray 是补齐其分布式计算能力的关键一步。这使得 `cache-dit` 的功能描述（Cache, Parallelism, Quantization）更加完整和强大。
    *   **降低用户门槛**: 对于希望将 Diffusion Transformer 模型部署到生产环境的用户，Ray 是一个成熟且广泛使用的工具。原生支持 Ray 可以显著降低用户的学习成本和集成难度，从而加速 `cache-dit` 的采用。

## 详细提交记录

### [e08edc3](https://github.com/vipshop/cache-dit/commit/e08edc324522ebd91e4ce8248941c30fdb3eeb9d)

- **作者**: DefTruth
- **时间**: 2026-05-09T14:03:36Z
- **提交信息**: feat: support ray wrapper (#1003)

* feat: support ray wrapper

* feat: support ray wrapper

* feat: support ray wrapper

* feat: support ray wrapper

* feat: support ray wrapper

* feat: support ray wrapper

* feat: support ray wrapper

* feat: support ray wrapper

* feat: support ray wrapper

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-05-10
**监控日期**: 2026-05-09
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 79510
- **最后更新**: 2026-05-09T22:39:17Z

## 提交统计

- **昨日提交总数**: 11
- **提交者数量**: 10
- **主要提交者**: Jee Jee Li, Nicolò Lucchesi, Kermit

## AI分析总结

好的，这是对 vllm-project/vllm 仓库昨日提交记录的分析总结。

### 1. 主要更新类型

-   **Bug修复 (Bugfix):** 4项 (提交 5, 6, 7, 8)
-   **新功能/支持 (Feature/Support):** 3项 (提交 2, 3, 10)
-   **重构 (Refactor):** 2项 (提交 1, 4)
-   **性能优化 (Performance):** 1项 (提交 9)
-   **架构改进 (Architecture):** 1项 (提交 11)

### 2. 关键变更点及其与项目方向的关系

-   **量化支持 (Quantization):** 新增 `ModelOpt NVFP4 W4A16` 支持 (提交 2)。这直接响应了项目“**cheap**”和“**fast**”的目标，通过更激进的4-bit权重量化，在保证推理质量的同时，显著降低模型的内存占用和带宽需求，从而降低成本并可能提升速度。
-   **推测解码 (SpecDecoding):** 扩展了 MTP (Multi-Token Prediction) 支持到 MIMO 2.5 (提交 3)。这是对“**fast**”目标的直接贡献，通过更先进的推测解码技术，在不牺牲准确性的前提下，大幅提升LLM的推理吞吐量。
-   **模型支持 (Model Support):** 为 DeepSeekV2 模型使用 `AutoWeightsLoader` (提交 4)，并修复了 Gemma4 模型的 KeyError 问题 (提交 5)。这体现了项目致力于支持最新、最流行模型的承诺，确保用户能快速、稳定地部署这些模型。
-   **架构改进 (Architecture):** 为 LoRA 引入初始的 Expert Parallelism (EP) 支持 (提交 11)。LoRA 是微调和服务定制模型的关键技术，EP 支持允许将 LoRA 适配器的计算分散到多个 GPU 上，这对于服务大量、大型的 LoRA 适配器至关重要，直接提升了项目的可扩展性和服务能力。
-   **Bug修复与稳定性:** 修复了多个关键 Bug，包括：
    -   Gemma4 模型加载错误 (提交 5)
    -   DeepSeek V4 的 Disaggregated 前缀缓存 (PD) 功能问题 (提交 6)
    -   GDN (推测为某种自定义算子) 中 `torch.compile` 嵌套导致的 CUDA Graph 捕获失败 (提交 7)
    -   GDN 在 Hopper GPU 上的精度损失 (提交 8)
    这些修复显著提升了项目的稳定性和兼容性，是项目走向成熟和可靠的关键。
-   **性能优化:** 改进了 DeepSeek V4 的 fused Indexer Q quant kernel (提交 9)。这直接优化了特定模型（DeepSeek V4）的核心计算路径，体现了项目对高性能推理的持续追求。
-   **硬件支持:** 为 ROCm (AMD GPU) 升级了 `aiter` 库 (提交 10)。这体现了项目“**for everyone**”的目标，通过持续优化对非NVIDIA硬件的支持，扩大其用户基础和适用场景。

### 3. 对项目的影响和潜在意义

-   **提升竞争力:** 新增的 NVFP4 量化和 MTP 推测解码功能，使 vLLM 在推理速度和成本效益上更具竞争力，能吸引更多追求极致性能的用户。
-   **增强模型生态:** 对 DeepSeekV2、Gemma4 等前沿模型的支持和修复，巩固了 vLLM 作为主流 LLM 推理引擎的地位。
-   **提升稳定性和可靠性:** 大量的 Bug 修复，特别是针对 CUDA Graph 和特定 GPU 架构的修复，将显著提升 vLLM 在生产环境中的稳定性和可靠性，降低用户的使用门槛。
-   **拓展应用场景:** LoRA 的 EP 支持，为需要大规模、个性化模型服务的场景（如企业级聊天机器人、代码助手）提供了更强大的基础设施。

### 4. 值得关注的技术点

-   **NVFP4 W4A16 量化:** 这是一种混合精度量化方案，权重为4-bit，激活为16-bit。它比常见的 W8A16 或 W4A16 (权重4-bit，激活16-bit) 更进一步，在保持精度的同时，将内存占用和计算量降至新低。这是量化领域的前沿技术。
-   **MIMO 2.5 推测解码:** MIMO (Multi-Input Multi-Output) 是一种先进的推测解码架构。MIMO 2.5 可能是在效率和效果之间取得更好平衡的版本，值得关注其具体实现和性能表现。
-   **GDN (推测为 Gated Delta Network 或类似自定义算子) 的 Bug 修复:** 修复涉及 `torch.compile` 嵌套和 Hopper GPU 的 WGMMA 指令对齐问题。这表明 vLLM 在底层算子优化上投入了大量精力，并积极适配最新的 GPU 架构。
-   **LoRA 的 Expert Parallelism:** 这是将模型并行技术应用于 LoRA 适配器的一种创新方法，对于服务大量 LoRA 适配器具有重要参考价值。

### 5. 结合项目背景，这些提交如何影响项目发展

基于 README 中“**Easy, fast, and cheap LLM serving for everyone**”的愿景，昨日的更新从多个维度推动了项目发展：

-   **Fast (快):** 通过 MTP 推测解码 (提交 3)

## 详细提交记录

### [f80aa53](https://github.com/vllm-project/vllm/commit/f80aa53c9dc2273a19a6855092069db7e1306fff)

- **作者**: Wentao Ye
- **时间**: 2026-05-09T21:46:52Z
- **提交信息**: [Refactor] Nixl util using lazy init (#41392)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [7a2b596](https://github.com/vllm-project/vllm/commit/7a2b59698275f30d6168dbac1f2b3c5c3cd5fe94)

- **作者**: Juhi Mittal
- **时间**: 2026-05-09T21:15:50Z
- **提交信息**: [Quantization] Add ModelOpt NVFP4 W4A16 (4-bit weights, fp16/bf16 activations) support (#41769)

Signed-off-by: Juhi Mittal <juhim@nvidia.com>

### [2ee8c2a](https://github.com/vllm-project/vllm/commit/2ee8c2a56e41fbd00b4fb52f29464fb7fca48dba)

- **作者**: Jiangyun Zhu
- **时间**: 2026-05-09T18:22:59Z
- **提交信息**: [SpecDecoding] extend mtp support for mimo 2.5 (#41905)

Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>

### [cd74911](https://github.com/vllm-project/vllm/commit/cd74911d92841102c1cbbc8ed6d544518bf68223)

- **作者**: SoluMilken
- **时间**: 2026-05-09T17:55:25Z
- **提交信息**: [Model] use AutoWeightsLoader for DeepSeekV2 (#41706)

Signed-off-by: SoluMilken <ypiheyn.imm02g@g2.nctu.edu.tw>

### [25abddc](https://github.com/vllm-project/vllm/commit/25abddc1a5cb5dbe51d629aada9360579acb8acf)

- **作者**: SoluMilken
- **时间**: 2026-05-09T17:20:44Z
- **提交信息**: [BugFix] Fix Gemma4 'layers.0.moe.experts.0.down_proj_packed' KeyError issue (#40708)

Signed-off-by: SoluMilken <ypiheyn.imm02g@g2.nctu.edu.tw>

### [171d59a](https://github.com/vllm-project/vllm/commit/171d59ae8d1b8d6718ec3cd6558334ce8bbc0eb4)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-05-09T16:48:24Z
- **提交信息**: [Bugfix][PD] Fix DSv4 Disaggregated (#41957)

Signed-off-by: NickLucche <nlucches@redhat.com>
Co-authored-by: ZhanqiuHu <zhu@redhat.com>

### [3dda9ae](https://github.com/vllm-project/vllm/commit/3dda9aeb54cc15c9ecc6d1498a42ceb372d4472b)

- **作者**: Thomas Parnell
- **时间**: 2026-05-09T15:30:55Z
- **提交信息**: [Bugfix] Remove nested torch.compile in GDN rearrange_mixed_qkv causing CUDA graph capture failure (#42070)

Signed-off-by: Thomas Parnell <tpa@zurich.ibm.com>
Co-authored-by: Jiangyun Zhu <riverclouds.zhu@qq.com>

### [adb6d96](https://github.com/vllm-project/vllm/commit/adb6d96516cb0cd6d1dec985cb5e5cdc20ed418b)

- **作者**: Kermit
- **时间**: 2026-05-09T13:08:46Z
- **提交信息**: [Bugfix] Fix GDN KKT precision loss on Hopper GPUs by aligning tl.dot operand layout with WGMMA (#42076)

Signed-off-by: kermit <ckeming@outlook.com>

### [530d371](https://github.com/vllm-project/vllm/commit/530d37130278d38b07b089f936850537aa1ea5e6)

- **作者**: Thien Tran
- **时间**: 2026-05-09T08:20:32Z
- **提交信息**: [DSv4] Improved fused Indexer Q quant kernel (#41428)

### [34ab4f2](https://github.com/vllm-project/vllm/commit/34ab4f2565572a1525865a06d2ba19cc5fcb4f00)

- **作者**: Micah Williamson
- **时间**: 2026-05-09T08:13:45Z
- **提交信息**: [ROCm] Upgrade aiter to v0.1.13-rc5 (#42113)

Signed-off-by: Micah Williamson <micah.williamson@amd.com>

### [ecd0b60](https://github.com/vllm-project/vllm/commit/ecd0b60aad2f4e28dd00ababfc1402690d88cbed)

- **作者**: Jee Jee Li
- **时间**: 2026-05-09T07:31:23Z
- **提交信息**: [LoRA] Initial EP support for LoRA (#40867)

Signed-off-by: Jee Jee Li <pandaleefree@gmail.com>
Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-05-10
**监控日期**: 2026-05-09
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 4668
- **最后更新**: 2026-05-09T23:00:34Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 5
- **主要提交者**: wangyu, baonudesifeizhai, zhumingjue138

## AI分析总结

好的，这是对 `vllm-project/vllm-omni` 仓库昨日提交记录的分析总结。

### 昨日更新要点分析

#### 1. 主要更新类型

*   **CI/CD 优化与重构**：这是昨日更新的主体，占据了大部分提交。包括环境变量清理、测试分片、命令优化和合并策略调整。
*   **功能新增**：为扩散模型（Diffusion）检查点添加了 ModelOpt FP8 自动检测支持。
*   **测试修复**：恢复了针对 Voxtral TTS 模型的测试标记和测试夹具。

#### 2. 关键变更点及其与项目整体方向的关系

*   **CI 性能与稳定性提升**：
    *   **移除环境变量** (`26d481f`)：移除 `VLLM_TEST_CLEAN_GPU_MEMORY` 变量，避免不必要的 GPU 检测，从而加速测试执行。
    *   **测试分片** (`7748021`)：将夜间测试中耗时的 Diffusion X2I H100 测试用例进行分片，并集中管理分片定义，以平衡负载、缩短测试总时长。
    *   **避免重复测试** (`40a07e0`)：优化夜间测试命令，避免在 Omni 功能测试中重复执行相同的测试用例。
    *   **合并策略优化** (`0e81ef2`)：更新合并条件，在每周测试期间跳过 L3 合并，并更新相关文档。这有助于在特定测试窗口期保持代码库稳定。
*   **功能扩展**：
    *   **FP8 支持** (`c4a0990`)：为扩散模型检查点添加了 ModelOpt FP8 自动检测支持。这是 Phase 1 的实现，意味着项目正在扩展其量化支持能力，特别是针对多模态模型中的图像生成部分。
*   **测试修复**：
    *   **恢复 TTS 测试** (`ac69cbd`)：恢复了 Voxtral TTS 模型的测试标记和 `omni_runner_function` 测试夹具。这表明项目在修复或调整了某些问题后，重新启用了对特定语音合成模型的测试覆盖。

#### 3. 对项目的影响和潜在意义

*   **提升开发效率**：CI 优化（移除环境变量、测试分片、避免重复）将直接减少开发者和 CI 系统的等待时间，加快反馈循环，使团队能更快地迭代和发布新功能。
*   **增强模型支持**：为扩散模型添加 FP8 支持，是项目“easy, fast, and cheap”目标的具体体现。FP8 量化可以显著降低模型推理的显存占用和计算成本，使得在更经济的硬件上运行高质量图像生成模型成为可能，从而扩大项目的用户覆盖范围。
*   **保障代码质量**：恢复 TTS 测试表明项目对模型质量有持续的关注，确保在引入新功能或进行重构时，已有的多模态能力（如语音合成）不会退化。

#### 4. 值得关注的技术点

*   **FP8 自动检测**：`ModelOpt FP8 auto-detect` 是一个值得关注的技术点。它意味着项目可能集成了 NVIDIA 的 ModelOpt 工具包，能够自动识别并量化模型中的特定层，简化了用户使用 FP8 的流程。
*   **CI 分片策略**：`shard nightly Diffusion X2I H100 lanes` 和 `centralize shard definitions` 体现了大型项目中 CI 管理的成熟实践。通过将耗时的测试任务分片并行执行，可以有效利用计算资源，缩短测试总时间。
*   **环境变量管理**：移除 `VLLM_TEST_CLEAN_GPU_MEMORY` 以避免副作用，是一个典型的性能优化案例，提醒开发者注意环境变量可能带来的隐形成本。

#### 5. 基于项目背景，这些提交如何影响项目发展

根据 README，`vllm-omni` 的目标是提供 **“Easy, fast, and cheap omni-modality model serving”**。

*   **“Fast”**：CI 优化直接提升了开发速度，而 FP8 支持则通过降低计算开销来提升模型推理速度。
*   **“Cheap”**：FP8 支持是降低部署成本的关键技术。它允许在更少的 GPU 上运行模型，或者使用更便宜的 GPU，直接契合了“cheap”的目标。
*   **“Easy”**：FP8 的自动检测功能简化了用户的使用步骤，无需手动配置量化参数，符合“easy”的宗旨。同时，稳定的 CI 和测试覆盖确保了用户在使用时的体验是可靠和一致的。
*   **“Omni-modality”**：更新同时涉及了**图像生成**（Diffusion FP8）和**语音合成**（Voxtral TTS 测试修复），表明项目正在持续巩固和扩展其对多种模态（文本、图像、语音）的支持能力。

**总结**：昨日的更新是一次典型的“内功修炼”与“能力扩展”并重的迭代。一方面，通过大量 CI 优化，项目团队在提升自身开发效率和代码库稳定性上下了功夫；另一方面，通过引入 FP8 量化支持，项目在实现其“fast”和“cheap”的核心价值主张上迈出了坚实的一步，并继续巩固其多模态服务能力。

## 详细提交记录

### [26d481f](https://github.com/vllm-project/vllm-omni/commit/26d481fc847a584c3f385a9ddcce002af1bbd319)

- **作者**: wangyu
- **时间**: 2026-05-09T23:00:29Z
- **提交信息**: [CI] Remove VLLM_TEST_CLEAN_GPU_MEMORY to avoid environment variable pollution that causes unnecessary GPU detection, thereby slowing down test case execution. (#3446)

Signed-off-by: wangyu <410167048@qq.com>
Signed-off-by: [Your Name] <your.email@example.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [7748021](https://github.com/vllm-project/vllm-omni/commit/77480215f5c854b030364a3e352862228f98de1a)

- **作者**: wuhang
- **时间**: 2026-05-09T13:13:18Z
- **提交信息**: [CI][Nightly] Shard nightly Diffusion X2I H100 lanes and centralize shard definitions (#3455)

Signed-off-by: wuhang <wuhang6@huawei.com>

### [c4a0990](https://github.com/vllm-project/vllm-omni/commit/c4a099004411f0aa5d30ad05ed4e7fe6876e58e0)

- **作者**: baonudesifeizhai
- **时间**: 2026-05-09T08:55:05Z
- **提交信息**: （Phase 1）Add ModelOpt FP8 auto-detect support for diffusion checkpoints #2709 (#2913)

Signed-off-by: roG0d <rodgarcas98@gmail.com>
Signed-off-by: roG0d <baonudesifeizhai@gmail.com>
Signed-off-by: baonudesifeizhai <85092850+baonudesifeizhai@users.noreply.github.com>
Co-authored-by: roG0d <rodgarcas98@gmail.com>

### [40a07e0](https://github.com/vllm-project/vllm-omni/commit/40a07e0d809e3c2dc07de52ef977ca364a1dc2cb)

- **作者**: wangyu
- **时间**: 2026-05-09T08:17:57Z
- **提交信息**: [CI] Refine nightly pytest command in Omni · Function Test with H100 to avoid duplicate testing. (#3459)

Signed-off-by: wangyu <410167048@qq.com>

### [0e81ef2](https://github.com/vllm-project/vllm-omni/commit/0e81ef28707631fc6335bf083cf3df9966851403)

- **作者**: zhumingjue138
- **时间**: 2026-05-09T08:17:43Z
- **提交信息**: [CI] Update merge condition to skip L3 merges during weekly test and update doc (#3197)

Signed-off-by: zhumingjue <zhumingjue@huawei.com>

### [ac69cbd](https://github.com/vllm-project/vllm-omni/commit/ac69cbd27ecbf67e3a994c15c55d9ee65dacbd16)

- **作者**: Yueqian Lin
- **时间**: 2026-05-09T07:22:43Z
- **提交信息**: [Test] Restore tts mark and omni_runner_function fixture for Voxtral TTS (#3462)

Signed-off-by: Yueqian Lin <linyueqian@outlook.com>

---
