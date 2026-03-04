# GitHub Stars 合并报告 - 2026-02-27

**合并日期**: 2026-02-28
**监控日期**: 2026-02-27
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
11. [vllm-project/vllm-omni](#vllm-project-vllm-omni)
12. [vllm-project/vllm](#vllm-project-vllm)

---

<a id="ByteDance-Seed-VeOmni"></a>


**报告日期**: 2026-02-28
**监控日期**: 2026-02-27
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 1670
- **最后更新**: 2026-02-27T11:53:07Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交



---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-02-28
**监控日期**: 2026-02-27
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Light Image Video Generation Inference Framework
- **语言**: Python
- **星标数**: 1995
- **最后更新**: 2026-02-27T16:07:26Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 3
- **主要提交者**: Chengtao Lv, Shiqiao Gu (谷石桥), ziyanxzy

## AI分析总结

根据提供的提交记录和README摘要，以下是对昨日更新的分析总结：

### 1. 主要更新类型
*   **功能新增**：为项目添加了对**Intel XPU（GPU）的原生支持**，这是本次更新的核心。
*   **Bug修复**：修复了CI（持续集成）流程和某些bug，确保代码质量和稳定性。
*   **性能优化**：通过支持**NVFP4（NVIDIA FP4量化）** 来优化模型在NVIDIA平台上的推理效率。

### 2. 关键变更点及其与项目整体方向的关系
*   **平台扩展**：新增 `intel_xpu_native_support`，使LightX2V从主要支持NVIDIA GPU扩展到也支持Intel集成/独立GPU。这与项目作为“**轻量级视频生成推理框架**”的目标高度一致，旨在**降低用户使用门槛、扩大硬件兼容性**。
*   **性能与效率**：
    *   `support nvfp4 for ar models`：通过支持更低的精度（FP4）来减少模型内存占用、提升推理速度，直接服务于项目的“**Light**”（轻量、高效）核心目标。
    *   Intel支持中强调利用 `torch_sdpa` 内核实现“原生级性能”，表明在扩展平台的同时并未牺牲性能。
*   **稳定性与质量**：`fix ci and bug` 的提交确保了新增功能和现有代码的可靠性，是项目健康迭代的基础。

### 3. 对项目的影响和潜在意义
*   **扩大用户基础**：吸引拥有Intel显卡（特别是笔记本集成显卡）的用户和开发者，显著提升了项目的潜在受众和实用性。
*   **强化“轻量”定位**：NVFP4支持进一步强化了框架在资源受限环境下高效运行的特性。
*   **生态建设**：通过支持更多硬件平台，LightX2V向成为更通用、更开放的视频生成推理生态迈出了一步。
*   **降低体验门槛**：为更多用户提供了在本地设备（无需高端NVIDIA GPU）上体验视频生成的可能性。

### 4. 值得关注的技术点
*   **Intel XPU集成**：展示了如何通过PyTorch的XPU后端 (`torch.xpu`) 和特定内核 (`torch_sdpa`) 将扩散模型推理任务适配到Intel硬件。
*   **量化支持**：`nvfp4` 的引入表明项目正在积极集成模型量化技术，这是边缘部署和降低推理成本的关键技术。
*   **平台抽象**：提交中通过 `PLATFORM=intel_xpu` 环境变量和独立的配置文件 (`configs/platforms/intel_xpu/`) 来管理不同平台，体现了良好的架构设计，便于未来支持更多硬件。

### 5. 基于项目背景的提交影响分析
LightX2V的目标是成为一个**高效、易用、跨平台的轻量级视频生成推理框架**。昨日的更新完美地推动了这一发展：
1.  **从“高效”看**：NVFP4支持直接提升了在NVIDIA硬件上的推理效率；Intel支持通过优化内核实现了在iGPU上的可用性能。
2.  **从“易用”和“跨平台”看**：新增Intel支持是质的飞跃。它打破了硬件壁垒，提供了清晰的安装、环境设置和示例代码，大幅提升了框架的易用性和可及性。
3.  **整体发展**：这些提交表明项目正沿着两条主线快速发展：一是**纵向深入**（通过量化等技术优化现有平台性能），二是**横向拓展**（支持新的硬件平台）。这使LightX2V不仅是一个技术演示，更朝着成为**生产级、可广泛部署的视频生成基础工具**的方向演进。

**总结**：昨日的更新是一次重要的版本迭代，核心是**新增对Intel GPU的官方支持**，并辅以性能优化和稳定性修复。这极大地拓展了框架的适用场景，巩固了其作为轻量级、跨平台视频生成解决方案的定位，对项目的用户增长和生态构建具有积极的战略意义。

## 详细提交记录

### [3a2bf8f](https://github.com/ModelTC/LightX2V/commit/3a2bf8f4017ba620b7914a6de54740c62c8498de)

- **作者**: Chengtao Lv
- **时间**: 2026-02-27T12:43:49Z
- **提交信息**: support nvfp4 for ar models (#907)

### [16ecaaa](https://github.com/ModelTC/LightX2V/commit/16ecaaab7859fdb522871297798ab946fe8565c8)

- **作者**: Shiqiao Gu (谷石桥)
- **时间**: 2026-02-27T10:58:53Z
- **提交信息**:  fix ci and bug (#905)

Co-authored-by: gushiqiao <975033167>

### [3e2edc1](https://github.com/ModelTC/LightX2V/commit/3e2edc1012c73937eee7f7ab90e62f0e7a976f7d)

- **作者**: ziyanxzy
- **时间**: 2026-02-27T10:35:19Z
- **提交信息**: intel_xpu_native_support (#903)

# Intel Support for LightX2V

## Summary
This PR adds Intel support for LightX2V, enabling video generation and
image generation on Intel GPUs.

## End-to-End Performance
On PTL integrated GPUs (iGPUs), we have achieved native-level
performance leveraging the torch_sdpa kernel.
| Models            | Configuration                  | Time    |
|-------------------|--------------------------------|---------|
| Wan2.1-T2V-1.3B   | 33 frames, 480×848, 20 steps   | 197.80s |
| Z-image-turbo     | 16:9 ratio, 9steps             | 57s     |

## Usage

### Environment Setup
Set the platform environment variable for Intel iGPUs (Windows):
```bash
set PLATFORM=intel_xpu
```
### Wan Models (Text-to-Video)

```python
"""
Wan2.1 text-to-video generation example.
This example demonstrates how to use LightX2V with Wan2.1 model for T2V generation.
"""

from lightx2v import LightX2VPipeline

# Initialize pipeline for Wan2.1 T2V task
pipe = LightX2VPipeline(
    model_path=r"xxx\models\Wan2.1-T2V-1.3B",
    model_cls="wan2.1",
    task="t2v",
)
pipe.create_generator(
    config_json="../../configs/platforms/intel_xpu/wan_t2v_1_3.json"
)

# Create generator with specified parameters
pipe.create_generator(
    attn_mode="torch_sdpa",
    infer_steps=50,
    height=480,  # Can be set to 720 for higher resolution
    width=832,  # Can be set to 1280 for higher resolution
    num_frames=33,
    guidance_scale=5.0,
    sample_shift=5.0,
)

seed = 42
prompt = "a cat"
negative_prompt = "镜头晃动，色调艳丽，过曝，静态，细节模糊不清，字幕，风格，作品，画作，画面，静止，整体发灰，最差质量，低质量，JPEG压缩残留，丑陋的，残缺的，多余的手指，画得不好的手部，画得不好的脸部，畸形的，毁容的，形态畸形的肢体，手指融合，静止不动的画面，杂乱的背景，三条腿，背景人很多，倒着走"
save_result_path = "./output.mp4"

pipe.generate(
    seed=seed,
    prompt=prompt,
    negative_prompt=negative_prompt,
    save_result_path=save_result_path,
)
```

### Z-image-turbo Models (Text-to-Image)
  ```python
"""
Z-Image image-to-image generation example.
This example demonstrates how to use LightX2V with Z-Image-Turbo model
for T2I generation.
"""

from lightx2v import LightX2VPipeline

# Initialize pipeline for Z-Image-edit T2I task
pipe = LightX2VPipeline(
    model_path=r"xxxx\models\Z-Image-Turbo",
    model_cls="z_image",
    task="t2i",
)

# Alternative: create generator from config JSON file
pipe.create_generator(
config_json="../../configs/platforms/intel_xpu/z_image_turbo_t2i.json"
)

# Create generator manually with specified parameters
pipe.create_generator(
    attn_mode="torch_sdpa",
    aspect_ratio="16:9",
    infer_steps=9,
    guidance_scale=1,
)

# Generation parameters
seed = 42
prompt = 'A coffee shop entrance features a chalkboard sign reading
"Qwen Coffee 😊 $2 per cup," with a neon light beside it displaying
"通义千问". Next to it hangs a poster showing a beautiful Chinese woman, and
beneath the poster is written
"π≈3.1415926-53589793-23846264-33832795-02384197". Ultra HD, 4K,
cinematic composition, Ultra HD, 4K, cinematic composition.'
negative_prompt = ""
save_result_path = "./output.png"

# Generate video
pipe.generate(
    seed=seed,
    prompt=prompt,
    negative_prompt=negative_prompt,
    save_result_path=save_result_path,
)
```

## Installation
Prerequisites
For intel platform, install dependencies with the following commands:
```bash
pip install --no-cache-dir -r requirements_win.txt
pip install --no-cache-dir torch==2.9.1+xpu torchvision torchaudio
--index-url https://download.pytorch.org/whl/xpu
pip install --no-cache-dir -e .
```
## Platform Detection
Verify Intel XPU availability with the following code:
```python
import torch
torch.xpu.is_available()

---------

Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>



---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-02-28
**监控日期**: 2026-02-27
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 1925
- **最后更新**: 2026-02-27T06:05:30Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交



---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-02-28
**监控日期**: 2026-02-27
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5050
- **最后更新**: 2026-02-27T16:23:59Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交



---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-02-28
**监控日期**: 2026-02-27
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3111
- **最后更新**: 2026-02-27T20:47:37Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Peiyuan Zhang

## AI分析总结

根据提供的仓库 `hao-ai-lab/FastVideo` 的提交记录和 README 摘要，以下是昨日更新的分析总结：

### 1. **主要更新类型**
- **重构/代码清理**：提交 `e1eda47` 移除了“时间帧调整”（temporal frame adjustment）功能或相关代码。

### 2. **关键变更点及其与项目整体方向的关系**
- **移除时间帧调整逻辑**：这一变更可能涉及视频处理流程中与帧率、时序对齐或插值相关的代码。结合 README 中提到的“FastVideo”项目（推测为高效视频处理或生成框架），移除该功能可能意味着：
  - **简化核心流程**：项目可能正聚焦于更核心的视频生成/处理算法，去除非必要的或实验性的调整模块。
  - **优化架构**：该调整可能与其他功能重叠或已被更优方案替代，有助于减少代码复杂性和维护成本。

### 3. **对项目的影响和潜在意义**
- **正向影响**：
  - **代码精简**：可能提升代码可读性和可维护性，减少潜在错误。
  - **性能提升**：若该模块是性能瓶颈，移除后可能提高处理效率。
- **潜在风险**：
  - **功能缺失**：如果该调整是某些用例的必要功能，可能影响部分用户的工作流程，需通过文档或替代方案说明。

### 4. **值得关注的技术点**
- **时间帧处理的重要性**：在视频生成/编辑中，时间一致性是关键挑战。移除该模块可能意味着项目采用了更端到端的方法，或依赖外部工具处理时序问题。
- **提交的孤立性**：单次提交仅涉及移除操作，未提及替代实现，可能后续会有相关更新（如集成新模块）。

### 5. **基于项目背景的提交影响分析**
- README 暗示项目定位为**高效视频处理工具**（如快速推理、易用性）。此次更新符合以下方向：
  - **聚焦核心功能**：通过剔除冗余代码，强化主要视频处理链路，提升用户体验和性能。
  - **敏捷迭代**：反映项目处于积极维护阶段，可能正为后续功能（如模型优化、新特性）铺路。
- **发展影响**：短期可能简化开发流程；长期需确保移除的功能不影响项目竞争力（如与其他视频工具相比的完整性）。

---
**总结**：本次更新是一次**代码重构**，旨在精简架构，可能帮助项目更专注于高效视频处理的核心目标。建议关注后续是否引入更优的时间处理方案，或更新文档说明变更对用户的影响。

## 详细提交记录

### [e1eda47](https://github.com/hao-ai-lab/FastVideo/commit/e1eda47589b40ebe66695425f1285182c3f7935f)

- **作者**: Peiyuan Zhang
- **时间**: 2026-02-27T20:47:16Z
- **提交信息**: remove temporal frame adjustment



---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-02-28
**监控日期**: 2026-02-27
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 32890
- **最后更新**: 2026-02-27T20:50:43Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 3
- **主要提交者**: YiYi Xu, Christopher, Jerry Song

## AI分析总结

### 1. 主要更新类型
- **文档更新**：更新了 `auto_pipeline_blocks` 的文档，并添加至 API 文档。
- **Bug 修复**：
  - 修复了 Kohya LoRA 权重加载问题（针对 Flux.1-dev 模型的文本编码器 LoRA）。
  - 修复了 LTX-2 图像到视频两阶段生成中的形状不匹配错误。
- **测试增强**：为 LTX-2 修复添加了单元测试。

### 2. 关键变更点及其与项目整体方向的关系
- **文档完善**：`auto_pipeline_blocks` 文档更新，符合 Diffusers 作为**模块化、易用**的扩散模型库的定位，帮助用户更好地理解和使用自动化管道功能。
- **模型兼容性修复**：
  - Kohya LoRA 加载修复增强了与**第三方训练工具**的兼容性，支持更广泛的社区模型生态。
  - LTX-2 图像到视频生成修复确保了**多阶段生成流程**的稳定性，体现了对复杂生成任务的支持。
- **测试覆盖**：新增单元测试强化了代码可靠性，符合项目对**高质量、可维护代码**的追求。

### 3. 对项目的影响和潜在意义
- **用户体验提升**：文档更新降低了使用门槛；Bug 修复直接解决了用户在使用特定功能（LoRA 加载、LTX-2 视频生成）时可能遇到的错误。
- **生态扩展**：Kohya LoRA 修复促进了社区模型（尤其是经过微调的模型）的集成，增强了 Diffusers 的**互操作性**。
- **稳定性增强**：LTX-2 修复和测试添加减少了生成过程中的崩溃风险，提升了**生产环境可用性**。

### 4. 值得关注的技术点
- **LoRA 加载逻辑调整**：针对 `lora_te1_` 前缀的文本编码器 LoRA 进行特殊处理，反映了不同训练框架对 LoRA 命名的差异。
- **条件掩码动态创建**：在 LTX-2 修复中，根据 `latents` 形状动态生成 `conditioning_mask`，避免了硬编码形状依赖，提高了代码的适应性。
- **模块化文档结构化**：`auto_pipeline_blocks` 文档的细化，展示了如何通过组合不同模块构建定制化生成流程，体现了库的**灵活性设计**。

### 5. 基于项目背景的提交影响分析
Diffusers 旨在提供**先进、易用且模块化**的扩散模型工具库。这些提交共同推动了这一目标：
- **文档更新**直接服务于**易用性**，帮助用户更快上手高级功能。
- **Bug 修复**解决了实际使用中的痛点，提升了**可靠性**，特别是对于新兴模型（如 Flux、LTX-2）和社区工作流（如 Kohya LoRA）的支持，加强了项目的**前沿性和包容性**。
- **测试增强**确保了核心功能的稳定性，为持续迭代和**大规模应用**打下基础。

总体而言，这些更新虽以修复和优化为主，但显著提升了库的成熟度和用户体验，巩固了 Diffusers 作为**扩散模型标准工具库**的地位。

## 详细提交记录

### [680076f](https://github.com/huggingface/diffusers/commit/680076fcc00d466247a384e2337913ae9405f0c5)

- **作者**: YiYi Xu
- **时间**: 2026-02-27T20:50:35Z
- **提交信息**: [Modular] update the auto pipeline blocks doc (#13148)

* update

* Apply suggestion from @yiyixuxu

* Update docs/source/en/modular_diffusers/auto_pipeline_blocks.md

Co-authored-by: Steven Liu <59462357+stevhliu@users.noreply.github.com>

* Update docs/source/en/modular_diffusers/auto_pipeline_blocks.md

Co-authored-by: Steven Liu <59462357+stevhliu@users.noreply.github.com>

* Update docs/source/en/modular_diffusers/auto_pipeline_blocks.md

Co-authored-by: Steven Liu <59462357+stevhliu@users.noreply.github.com>

* Update docs/source/en/modular_diffusers/auto_pipeline_blocks.md

Co-authored-by: Steven Liu <59462357+stevhliu@users.noreply.github.com>

* add to api

---------

Co-authored-by: yiyi@huggingface.co <yiyi@ip-26-0-160-103.ec2.internal>
Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>
Co-authored-by: Steven Liu <59462357+stevhliu@users.noreply.github.com>
Co-authored-by: yiyi@huggingface.co <yiyi@ip-26-0-161-123.ec2.internal>

### [5910a1c](https://github.com/huggingface/diffusers/commit/5910a1cc6c48fe0e9a2038c0b36cb9a24663932b)

- **作者**: Christopher
- **时间**: 2026-02-27T10:13:41Z
- **提交信息**: Fixing Kohya loras loading: Flux.1-dev loras with TE ("lora_te1_" prefix) (#13188)

* fixing text encoder lora loading

* following Cursor's review

### [40e9645](https://github.com/huggingface/diffusers/commit/40e96454f122a8220342429507f5652fdafe57e6)

- **作者**: Jerry Song
- **时间**: 2026-02-27T08:55:01Z
- **提交信息**: Fix LTX-2 image-to-video generation failure in two stages generation (#13187)

* Fix LTX-2 image-to-video generation failure in two stages generation

In LTX-2's two-stage image-to-video generation task, specifically after
the upsampling step, a shape mismatch occurs between the `latents` and
the `conditioning_mask`, which causes an error in function
`_create_noised_state`.

Fix it by creating the `conditioning_mask` based on the shape of the
`latents`.

* Add unit test for LTX-2 i2v two stages inference with upsampler

* Downscaling the upsampler in LTX-2 image-to-video unit test

* Apply style fixes

---------

Co-authored-by: github-actions[bot] <github-actions[bot]@users.noreply.github.com>



---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-02-28
**监控日期**: 2026-02-27
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 374
- **最后更新**: 2026-02-26T02:11:05Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交



---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-02-28
**监控日期**: 2026-02-27
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 11861
- **最后更新**: 2026-02-27T15:39:19Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交



---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-02-28
**监控日期**: 2026-02-27
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 23824
- **最后更新**: 2026-02-27T22:00:47Z

## 提交统计

- **昨日提交总数**: 19
- **提交者数量**: 18
- **主要提交者**: yrk111222, Baizhou Zhang, wufann

## AI分析总结

根据提供的提交记录和README摘要（SGLang项目是一个专注于高效语言模型推理的框架），以下是昨日更新的分析总结：

### 1. 主要更新类型
- **Bug修复**：占比最高，涉及多个组件（如HiCache、EAGLE、Diffusion、AMD CI测试等）。
- **性能优化**：包括缓存策略优化、AMD后端优化、移除冗余操作等。
- **功能新增/增强**：支持新模型（如Qwen3-Next）、新增AMD测试、扩展Diffusion API兼容性。
- **重构**：对DeepSeek-V2等模型的代码结构进行改进。
- **CI/CD与基础设施**：更新CI测试命令、优化Dockerfile、改进PR协作流程。

### 2. 关键变更点及其与项目方向的关系
| 变更点 | 说明 | 与项目方向的关系 |
|--------|------|------------------|
| **AMD平台优化**（多项提交） | 启用CUDA图、优化NSA后端、修复CI测试、合并Dockerfile等。 | 强化对AMD硬件的支持，体现项目对**多硬件平台兼容性**的重视，符合高效推理的定位。 |
| **HiCache与缓存改进** | 重构I/O内核、修复内存池类型错误、新增保守估计策略。 | 直接提升**推理缓存效率**，是项目核心优化方向之一。 |
| **模型支持扩展** | 支持Qwen3-Next的融合RMSNorm、新增MiniMax-M2.5测试。 | 持续扩展**模型生态兼容性**，增强框架实用性。 |
| **Diffusion模块修复** | 修复MulAdd 4D路径索引问题、优化NPU性能、完善API默认参数。 | 提升**多模态生成功能**的稳定性和用户体验。 |
| **基础设施与测试** | 更新CI测试命令、允许PR作者自助重跑失败CI、修复路由构造参数。 | 提升**开发效率与代码质量**，支持项目快速迭代。 |

### 3. 对项目的影响和潜在意义
- **稳定性提升**：大量Bug修复（尤其是缓存、AMD后端、Diffusion模块）直接增强生产环境可靠性。
- **性能增益**：AMD后端优化、缓存改进、冗余操作移除，有望降低延迟、提高吞吐量。
- **生态扩展**：新增模型支持和硬件平台优化，吸引更广泛的用户和开发者。
- **协作效率**：CI流程改进和PR自助工具，加速团队协作和集成验证。

### 4. 值得关注的技术点
- **AMD NSA后端与CUDA图**：针对AMD硬件的深度优化，反映项目在异构计算领域的投入。
- **HiCache内核重构**：可能涉及低层次内存/IO优化，对高性能缓存机制有重要影响。
- **Diffusion模块的4D路径修复**：涉及底层计算内核，可能影响图像生成的正确性与性能。
- **保守缓存估计策略**：新增策略可能平衡内存使用与命中率，适用于动态负载场景。

### 5. 基于项目背景的提交影响分析
SGLang旨在提供**高效、可扩展的LLM推理服务**。昨日提交整体符合这一目标：
- **强化核心能力**：缓存优化和AMD后端改进直接提升推理效率与跨平台能力。
- **提升开发者体验**：CI/CD改进和模型支持降低使用门槛，促进社区贡献。
- **拓展应用场景**：Diffusion模块修复和完善增强了多模态生成支持，扩大项目适用范围。
- **体现成熟度**：高频率的Bug修复和基础设施优化表明项目处于快速迭代期，注重稳定性和可维护性。

**总结**：昨日更新以**Bug修复和性能优化**为主，重点提升AMD平台支持、缓存效率和Diffusion模块稳定性，同时扩展模型生态并改进开发流程。这些变更紧密围绕SGLang的**高效推理与多平台兼容**核心目标，有助于巩固其作为生产级LLM推理框架的竞争力。

## 详细提交记录

### [e6da514](https://github.com/sgl-project/sglang/commit/e6da514c2c016d2fb269c4b2bf16d105dc18df90)

- **作者**: yrk111222
- **时间**: 2026-02-27T22:00:41Z
- **提交信息**: CI: use 'sglang serve' in CI tests (#18597)

Co-authored-by: Mick <mickjagger19@icloud.com>
Co-authored-by: sglang-bot <sglangbot@gmail.com>

### [776709e](https://github.com/sgl-project/sglang/commit/776709efe89390599302a244f6ab1626f02ba9ff)

- **作者**: Baizhou Zhang
- **时间**: 2026-02-27T21:37:29Z
- **提交信息**: [3/n] deepseek_v2.py Refactor: Migrate MLA forward method in deepseek_v2.py (#19122)

### [7e46aaf](https://github.com/sgl-project/sglang/commit/7e46aafebb6dded04f6ba345a8e203049618704a)

- **作者**: wufann
- **时间**: 2026-02-27T21:18:32Z
- **提交信息**: [AMD] Enable cudagraph for aiter nsa backend and add aiter impl for nsa pr… (#18526)

### [36dc973](https://github.com/sgl-project/sglang/commit/36dc973cbfb9c35688cc2799a61591d80ce25d13)

- **作者**: huangtingwei
- **时间**: 2026-02-27T19:43:14Z
- **提交信息**: [HiCache] refactor page_first_direct io kernel (#18113)

Co-authored-by: hzh0425 <hzh0425@apache.org>

### [1b75d0d](https://github.com/sgl-project/sglang/commit/1b75d0d1a979a324a24daf6a10fd8491b579f1c9)

- **作者**: Shu Wang
- **时间**: 2026-02-27T19:35:45Z
- **提交信息**: Fix BatchMLAPagedAttentionWrapper query/qo_inptr mismatch for EAGLE (#15601)

### [6a1480c](https://github.com/sgl-project/sglang/commit/6a1480ce45aa06c1f712ba4f3169f835a799ec0c)

- **作者**: ishandhanani
- **时间**: 2026-02-27T18:59:32Z
- **提交信息**: Fix HiCacheNixl TypeError: mem_pool_host passed as file_path (#19517)

### [35ef38c](https://github.com/sgl-project/sglang/commit/35ef38c61b2de3ce905836f18cfffd80e56c0a00)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-02-27T18:30:00Z
- **提交信息**: Remove gpt-oss hybrid swa gate for trtllm_mha (#19079)

### [1b79934](https://github.com/sgl-project/sglang/commit/1b79934d347ff1799fe651ee08d1d7a8cff3001f)

- **作者**: Michael
- **时间**: 2026-02-27T18:18:15Z
- **提交信息**: [AMD] Fix AMD CI test of TestToolChoiceLfm2Moe (#19113)

Co-authored-by: michaelzhang-ai <michaelzhang-ai@users.noreply.github.com>
Co-authored-by: bingxche <Bingxu.Chen@amd.com>
Co-authored-by: yctseng0211 <yctseng@amd.com>

### [2c856c6](https://github.com/sgl-project/sglang/commit/2c856c6d2766e8b88f4e1ed2b29ceeb3dcbe790b)

- **作者**: Alison Shao
- **时间**: 2026-02-27T18:14:57Z
- **提交信息**: Allow PR authors to use /rerun-failed-ci on their own PRs (#19496)

Co-authored-by: Alison Shao <alisonshao@MacBook-Pro-D2W773R9CD.local>

### [fe4bc8e](https://github.com/sgl-project/sglang/commit/fe4bc8ebd5210817bcd1dcd80789e1158bbd5739)

- **作者**: R0CKSTAR
- **时间**: 2026-02-27T17:52:57Z
- **提交信息**: [diffusion] fix: MulAdd 4D path (shift indexing) (#18673)

Signed-off-by: Xiaodong Ye <xiaodong.ye@mthreads.com>

### [b1249ac](https://github.com/sgl-project/sglang/commit/b1249ac909297cb94e0b969d3abeb89229792038)

- **作者**: Makcum888e
- **时间**: 2026-02-27T15:23:02Z
- **提交信息**: [Diffusion] [NPU] [CI] fix CI performance (#19486)

### [d2885a9](https://github.com/sgl-project/sglang/commit/d2885a9094c3847769923322e51a85841a552662)

- **作者**: Yuan Luo
- **时间**: 2026-02-27T15:08:08Z
- **提交信息**: [Qwen3-Next] Support gdn fused_rms_norm_gated (#19434)

Co-authored-by: luoyuan.luo <luoyuan.luo@antgroup.com>

### [ca5f2e2](https://github.com/sgl-project/sglang/commit/ca5f2e2ed13c03e5e6f76b4c4e5428a45839268d)

- **作者**: joesun
- **时间**: 2026-02-27T11:47:38Z
- **提交信息**: [diffusion] fix: Support default response_format=url in /v1/images/generations to avoid 400 errors when response_format is omitted (#19360)

Co-authored-by: Makcum888e <79456407+Makcum888e@users.noreply.github.com>
Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>

### [98e433e](https://github.com/sgl-project/sglang/commit/98e433e305c54f1ccf7704049fa6cb60e5190939)

- **作者**: Duyi-Wang
- **时间**: 2026-02-27T10:40:01Z
- **提交信息**: [PD-Disagg][Fix] Remove 'test_external_dp_routing' from Rust Router constructor parameters. (#19492)

### [403195d](https://github.com/sgl-project/sglang/commit/403195d59de0db4fe37d0b730e9cf6c2a9d9749c)

- **作者**: Michael
- **时间**: 2026-02-27T10:39:33Z
- **提交信息**: [AMD] [MiniMax-M2.5 Day 0] Add MiniMax-M2.5 nightly accuracy test (#19443)

### [f69ca93](https://github.com/sgl-project/sglang/commit/f69ca93d496d96ce881a11b6992601cf0c18bd81)

- **作者**: AMD-yanfeiwang
- **时间**: 2026-02-27T10:15:55Z
- **提交信息**: [AMD] remove redundancy H2D op in aiter attention backend (#19416)

Co-authored-by: root <root@mia1-p01-g28.mia.tensorwave.lan>

### [07da4be](https://github.com/sgl-project/sglang/commit/07da4bed7b31cdb28f582bbfddd852373def51f1)

- **作者**: Yilong Zhao
- **时间**: 2026-02-27T10:14:46Z
- **提交信息**: [cache] add conservative estimation (#19482)

### [9496bbd](https://github.com/sgl-project/sglang/commit/9496bbd7b11c7ce7ac96b339c7a1fb23d0406545)

- **作者**: fxmarty-amd
- **时间**: 2026-02-27T09:43:34Z
- **提交信息**: [AMD] Use `tilelang` as default NSA attention backend dispatch on AMD Instinct (#18319)

### [9b2fbf7](https://github.com/sgl-project/sglang/commit/9b2fbf7e6ad4730c0f6abf49a307fa2fecc4952a)

- **作者**: Alan Kao
- **时间**: 2026-02-27T08:53:51Z
- **提交信息**: [AMD] Merge Dockerfiles for ROCm (#19203)

Co-authored-by: bingxche <Bingxu.Chen@amd.com>



---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-02-28
**监控日期**: 2026-02-27
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: 🤗 A PyTorch-native and Flexible Inference Engine with Hybrid Cache Acceleration and Parallelism for DiTs.
- **语言**: Python
- **星标数**: 1057
- **最后更新**: 2026-02-27T18:40:29Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交



---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-02-28
**监控日期**: 2026-02-27
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 2838
- **最后更新**: 2026-02-27T21:35:36Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 2
- **主要提交者**: Alicia, Zhou Taichang

## AI分析总结

根据提供的提交记录和README摘要（vLLM-Omni项目），以下是昨日更新的要点总结：

---

### 1. **主要更新类型**
- **文档更新**：所有提交均为文档或配置文件的调整，无代码功能变更。
- **CI/CD维护**：涉及持续集成配置的链接更新。

### 2. **关键变更点及其与项目整体方向的关系**
- **更新H100镜像链接**（#1538）：修正CI/CD中NVIDIA H100 GPU镜像的引用链接，确保自动化测试/构建环境能正确访问所需资源。
- **文档同步**（#1363）：同步文档内容，可能涉及格式修复、链接更新或版本对齐，保持文档与代码状态一致。
- **安装指南更新**（#1505）：针对vLLM 0.16.0版本调整安装说明，反映依赖版本或步骤变化。

**与项目方向的关系**：  
vLLM-Omni作为高效推理框架，强调多后端支持（如NVIDIA、AMD、AWS等）和易用性。这些更新维护了文档准确性和基础设施稳定性，符合项目追求**可靠性**和**开发者体验**的目标。

### 3. **对项目的影响和潜在意义**
- **正面影响**：
  - 提升文档质量，降低用户使用门槛。
  - 确保CI/CD环境可靠性，避免因资源链接失效导致构建失败。
  - 支持新版本vLLM适配，促进生态兼容性。
- **潜在风险**：无直接代码变更，不影响运行时性能或功能。

### 4. **值得关注的技术点**
- **CI/CD依赖管理**：H100镜像链接的更新反映项目对异构硬件（如NVIDIA最新GPU）的持续集成支持。
- **版本同步策略**：安装指南针对vLLM 0.16.0更新，提示项目可能依赖上游vLLM核心库的迭代，需保持版本协同。

### 5. **基于项目背景的提交影响分析**
- **项目背景**（从README推断）：vLLM-Omni是扩展vLLM的“全能”推理引擎，支持多硬件、多模型部署，注重高性能与易用性。
- **影响分析**：
  - **强化项目可维护性**：文档和CI的维护虽看似微小，但能减少用户困惑和开发中断，间接支持项目长期稳定发展。
  - **生态适配信号**：紧跟vLLM 0.16.0的安装说明更新，表明项目积极与上游生态保持同步，有利于吸引vLLM用户迁移。
  - **硬件兼容性维护**：H100镜像链接修正，强调对最新硬件的支持，符合项目“多后端”愿景。

---

**总结**：昨日更新主要为**维护性改进**，聚焦文档和基础设施的完善。虽无直接功能增强，但通过提升文档准确性和CI稳定性，支持了项目的**易用性**和**跨平台兼容性**目标，为后续功能迭代奠定基础。

## 详细提交记录

### [11f59f6](https://github.com/vllm-project/vllm-omni/commit/11f59f600d64fb34fd45fe481a242e0ef9aa5e6e)

- **作者**: Alicia
- **时间**: 2026-02-27T10:25:18Z
- **提交信息**: [CI][skip ci]Update H100 image link based on #1518 (#1538)

Signed-off-by: Alicia <115451386+congw729@users.noreply.github.com>

### [64f5ef6](https://github.com/vllm-project/vllm-omni/commit/64f5ef615c1d7f47cac8be95842b2da4bc38dfde)

- **作者**: Alicia
- **时间**: 2026-02-27T09:28:35Z
- **提交信息**: [Doc] [skip ci]Sync. (#1363)

Signed-off-by: Alicia <115451386+congw729@users.noreply.github.com>
Co-authored-by: Yueqian Lin <70319226+linyueqian@users.noreply.github.com>

### [bc13f7c](https://github.com/vllm-project/vllm-omni/commit/bc13f7cf38b697b32ba8cc422a66c0b1007ba968)

- **作者**: Zhou Taichang
- **时间**: 2026-02-27T08:06:30Z
- **提交信息**: [Doc] Update installation instructions for vllm 0.16.0 (#1505)

Signed-off-by: tzhouam <tzhouam@connect.ust.hk>



---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-02-28
**监控日期**: 2026-02-27
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 71414
- **最后更新**: 2026-02-27T22:01:58Z

## 提交统计

- **昨日提交总数**: 25
- **提交者数量**: 23
- **主要提交者**: Gregory Shtrasberg, Aaron Hao, Jakub Zakrzewski

## AI分析总结

根据提供的提交记录和vLLM项目背景（一个专注于高效推理和服务大规模语言模型的高吞吐量、低延迟LLM推理引擎），以下是昨日更新的要点总结：

### 1. 主要更新类型
- **功能新增**：4项（ROCm后端支持、RL权重同步API、新模型支持、音频编码器支持）
- **Bug修复**：10项（模型推理、内存/缓存、并行化、API端点等）
- **性能优化**：3项（内存传输、编译缓存、内核预热）
- **文档/维护**：3项（文档链接、代码所有权、代码清理）
- **重构/底层变更**：2项（内核调用表示、编译清理）
- **功能回退**：1项（撤销特定模型配置）

### 2. 关键变更点及其与项目方向的关系
| 关键变更点 | 与项目方向的关系 |
| :--- | :--- |
| **ROCm后端支持编码器模型** (`#35334`) | 扩展硬件支持（AMD ROCm），提升生态兼容性，符合多硬件支持战略 |
| **原生RL权重同步API** (`#34171`) | 强化分布式训练/推理集成能力，支持更复杂的RLHF等工作流 |
| **多模型Bug修复** (GPT-OSS, Transformers后端, 3D RoPE等) | 确保核心推理功能的正确性和稳定性，是维持高可靠性的基础 |
| **性能优化** (异步H2D传输、缓存修复、内核预热) | 直接服务于项目核心目标：**提升吞吐量和降低延迟** |
| **Flashinfer cuDNN后端用于Qwen3 VL** (`#34580`) | 集成高性能内核（Flashinfer），优化视觉语言模型推理效率 |

### 3. 对项目的影响和潜在意义
- **扩大硬件和模型覆盖**：通过支持ROCm和新增模型（如skt/A.X-K1），吸引更广泛的用户和部署场景。
- **提升系统健壮性**：大量Bug修复（特别是分布式、缓存、批处理相关）增强了生产环境下的稳定性。
- **优化推理性能**：内存传输和内核层面的优化直接提升端到端推理效率。
- **改善开发者体验**：文档修复、CODEOWNERS更新和预提交错误清理有助于社区协作。
- **功能整合与回退**：新增RL API和音频编码器支持丰富了功能栈，而回退GLM-OCR配置的提交则表明对代码质量的审慎管理。

### 4. 值得关注的技术点
- **统一后端架构**：`[ROCm] Enabling encoder... on ROCm and AITER unified backends` 体现了项目在抽象和统一不同硬件后端（如CUDA, ROCm）上的努力。
- **分布式通信优化**：`[RL][2/2] Native Weight Syncing API: IPC` 引入了进程间通信的原生权重同步，可能用于降低分布式推理的延迟。
- **编译与缓存机制**：多项提交涉及编译缓存、序列并行和cuDNN后端，显示项目在利用编译技术优化计算图执行。
- **复杂模型支持**：针对多模态（音频、视频交错、视觉语言）和特殊结构（如Mamba, MTP）的修复，说明vLLM正在深入适配前沿模型架构。

### 5. 基于项目背景的提交影响分析
vLLM的核心目标是实现**高效、可扩展的LLM服务**。昨日的提交整体上紧密围绕这一目标：
- **巩固核心推理能力**：绝大多数Bug修复和性能优化都直接作用于推理管线，确保其在不同模型、硬件和批处理场景下的**高效与正确**，这是项目立身之本。
- **拓展生态边界**：支持ROCm、新模型和音频编码器，降低了用户的使用门槛，扩大了vLLM的**适用场景和用户基数**，有助于其成为更通用的推理解决方案。
- **强化生产就绪性**：修复分布式训练检查点（DCP）、API端点验证、防止竞争条件等，提升了系统在**大规模、长时间运行**下的可靠性，这对企业级部署至关重要。
- **投资未来架构**：对Helion内核、编译层和统一后端的投入，是在为**更极致的性能和更灵活的硬件支持**打基础，保持技术领先性。

**总结**：昨日的更新是一次典型的“巩固与拓展”并行的迭代。在扎实修复底层问题、优化性能以**捍卫其高效推理的核心竞争力**的同时，积极拓展硬件支持、模型覆盖和高级功能（如RL集成），以**推动项目的生态增长和长期发展**。

## 详细提交记录

### [9fa6c68](https://github.com/vllm-project/vllm/commit/9fa6c68fa627c7ab041c48ac9987fb093719597f)

- **作者**: Gregory Shtrasberg
- **时间**: 2026-02-27T21:32:55Z
- **提交信息**: [ROCm] Enabling encoder and encoder-decoder on ROCm and AITER unified backends (#35334)

Signed-off-by: Gregory Shtrasberg <Gregory.Shtrasberg@amd.com>

### [2ce6f3c](https://github.com/vllm-project/vllm/commit/2ce6f3cf67934ebe199188c9a1f83ff1c2d8ba96)

- **作者**: Aaron Hao
- **时间**: 2026-02-27T20:45:21Z
- **提交信息**: [Feat][RL][2/2] Native Weight Syncing API: IPC (#34171)

Signed-off-by: hao-aaron <ahao@anyscale.com>
Signed-off-by: Aaron Hao <ahao@anyscale.com>
Signed-off-by: ahao-anyscale <ahao@anyscale.com>

### [1f3dbd9](https://github.com/vllm-project/vllm/commit/1f3dbd95fd13849e974f1f31ff36b3e91d7768bc)

- **作者**: Jakub Zakrzewski
- **时间**: 2026-02-27T20:41:24Z
- **提交信息**: [Bugfix][Model] Fix gpt-oss batch invariance (#35404)

Signed-off-by: Jakub Zakrzewski <jzakrzewski@nvidia.com>

### [1d532f9](https://github.com/vllm-project/vllm/commit/1d532f9d8fb205942035313293af701ee580a7e2)

- **作者**: Lucas Wilkinson
- **时间**: 2026-02-27T20:14:31Z
- **提交信息**: [DP] Only use DP padding when cudagraphs are actually used  (#34102)

Signed-off-by: Lucas Wilkinson <lwilkins@redhat.com>

### [234a65b](https://github.com/vllm-project/vllm/commit/234a65b781d9dc51d28aebb208096baa8fe0458e)

- **作者**: Lucas Kabela
- **时间**: 2026-02-27T19:51:36Z
- **提交信息**: [Bugfix] Add monkeypatch to prevent race condition from writing (#35420)

Signed-off-by: Lucas Kabela <lucaskabela@meta.com>

### [2decec9](https://github.com/vllm-project/vllm/commit/2decec9856033347f3129f1d1b2ec015e1ad88ea)

- **作者**: SteadfastAsArt
- **时间**: 2026-02-27T19:39:23Z
- **提交信息**: [Transformers backend] Ignore MTP weights when num_nextn_predict_layers=0 (#34888)

Signed-off-by: SteadfastAsArt <695488173@qq.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [29b3547](https://github.com/vllm-project/vllm/commit/29b35477b0661f527d2b951ff5125f5c58fce3fe)

- **作者**: Zhengxu Chen
- **时间**: 2026-02-27T19:34:16Z
- **提交信息**: [compile] Fix caching error over pytree slice node. (#35308)

Signed-off-by: zhxchen17 <zhxchen17@fb.com>

### [b1d9f53](https://github.com/vllm-project/vllm/commit/b1d9f5372d802513e9e009a5d572dd594a09e1dc)

- **作者**: Nick Hill
- **时间**: 2026-02-27T18:43:30Z
- **提交信息**: [Model Runner V2] Warmup kernels (#35172)

Signed-off-by: Nick Hill <nickhill123@gmail.com>

### [fd6de37](https://github.com/vllm-project/vllm/commit/fd6de37fcafe9540ed821256877127df75d74db8)

- **作者**: Raushan Turganbay
- **时间**: 2026-02-27T18:34:49Z
- **提交信息**: [BugFix] Fix 3D rope in transformers backend (#35097)

Signed-off-by: raushan <raushan@huggingface.co>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [c8aca0c](https://github.com/vllm-project/vllm/commit/c8aca0c9e1b35ee4a1683a01467e638b23076a37)

- **作者**: Netanel Haber
- **时间**: 2026-02-27T18:07:38Z
- **提交信息**: Support parakeet as audio encoder for nemotron-nano-vl (#35100)

Signed-off-by: Netanel Haber <58652339+netanel-haber@users.noreply.github.com>
Co-authored-by: Roger Wang <hey@rogerw.io>

### [b602e4f](https://github.com/vllm-project/vllm/commit/b602e4f299a596a14402e6a4ead5e51abb180c49)

- **作者**: Martin Hickey
- **时间**: 2026-02-27T17:51:09Z
- **提交信息**: [Doc] Fix link to Llama chat template for usability (#35525)

Signed-off-by: Martin Hickey <martin.hickey@ie.ibm.com>
Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>
Co-authored-by: Cyrus Leung <cyrus.tl.leung@gmail.com>

### [157722d](https://github.com/vllm-project/vllm/commit/157722da756daa6f967433903680745abc0c4861)

- **作者**: Huamin Li
- **时间**: 2026-02-27T17:50:37Z
- **提交信息**: [perf] Use pinned memory for async H2D transfer in do_mamba_copy_block (#35480)

Signed-off-by: Huamin Li <3ericli@gmail.com>

### [1d897ff](https://github.com/vllm-project/vllm/commit/1d897ff04f90c46041ed3966dea671a6ae532184)

- **作者**: Nick Hill
- **时间**: 2026-02-27T17:34:37Z
- **提交信息**: [Misc] Fill in some v1 CODEOWNERS gaps (#35524)

Signed-off-by: Nick Hill <nickhill123@gmail.com>

### [905d76b](https://github.com/vllm-project/vllm/commit/905d76b51dc3b98c4d0ee35317493f21f9e6b5d0)

- **作者**: fort726
- **时间**: 2026-02-27T17:26:02Z
- **提交信息**: [Model] Add huggingface skt/A.X-K1 model (#32407)

Signed-off-by: Sungwan(Alex) Kim <sw0726.kim@sktelecom.com>
Signed-off-by: fort726 <38447663+fort726@users.noreply.github.com>
Co-authored-by: Sungwan(Alex) Kim <sw0726.kim@sktelecom.com>
Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>
Co-authored-by: TJian <tunjian.tan@embeddedllm.com>

### [9098ce6](https://github.com/vllm-project/vllm/commit/9098ce690c802887fb36a8f3ee95bb18aacd2f76)

- **作者**: Yanan Cao
- **时间**: 2026-02-27T17:21:35Z
- **提交信息**: [Kernel] [Helion] [7/N] Use HOP to represent Helion Kernel call to enable fx tracing and pattern matching (#34390)

Signed-off-by: Yanan Cao <gmagogsfm@gmail.com>

### [876312f](https://github.com/vllm-project/vllm/commit/876312f0b59b24f95704a37c93675e36a018a140)

- **作者**: Nick Hill
- **时间**: 2026-02-27T15:54:24Z
- **提交信息**: [Core] Fix `gpu_worker.py` pre-commit errors (#35312)

Signed-off-by: Nick Hill <nickhill123@gmail.com>

### [5de98ab](https://github.com/vllm-project/vllm/commit/5de98abc122dd4049adf1234c9fc20b5cc83d6cb)

- **作者**: Boyuan Feng
- **时间**: 2026-02-27T15:53:47Z
- **提交信息**: Add @BoyuanFeng to CODEOWNERS (#35317)

Signed-off-by: Boyuan Feng <boyuan@meta.com>

### [9251ed5](https://github.com/vllm-project/vllm/commit/9251ed5c4fc6c954a5cdc5399d9d4f25ea5a8dd3)

- **作者**: Koushik Dutta
- **时间**: 2026-02-27T14:58:28Z
- **提交信息**: [Bugfix] Handle case when kimi ends reasoning with a tool call (#33646)

Signed-off-by: Koushik Dutta <koushd@gmail.com>
Co-authored-by: mondaylord <20212010046@fudan.edu.cn>
Co-authored-by: Chauncey <chaunceyjiang@gmail.com>
Co-authored-by: Roger Wang <hey@rogerw.io>

### [e824937](https://github.com/vllm-project/vllm/commit/e8249378e414d76387a027a6ffb5bde8b9aff765)

- **作者**: Yueqian Lin
- **时间**: 2026-02-27T14:48:25Z
- **提交信息**: [Bugfix] Fix check_interleaved_audio_video false positive for batched non-interleaved requests (#35487)

Signed-off-by: linyueqian <linyueqian@outlook.com>
Co-authored-by: Roger Wang <hey@rogerw.io>

### [6d4f9d3](https://github.com/vllm-project/vllm/commit/6d4f9d3ad5aa3750697edcf013ad080619ae25e9)

- **作者**: haosdent
- **时间**: 2026-02-27T14:27:06Z
- **提交信息**: [Bugfix] Fix DCP + FA3 crash due to missing num_splits in _forward_with_dcp (#35082)

Signed-off-by: haosdent <haosdent@gmail.com>

### [fbe3f01](https://github.com/vllm-project/vllm/commit/fbe3f0120a5e786a1459c982c72185311c78a276)

- **作者**: Harry Mellor
- **时间**: 2026-02-27T14:13:27Z
- **提交信息**: Revert "Add GlmOcrConfig for GLM-OCR model type recognition" (#35512)

### [66c1751](https://github.com/vllm-project/vllm/commit/66c1751d13b7b3c294418a88fbfbfe2ec49d5d3f)

- **作者**: Jason Li
- **时间**: 2026-02-27T13:36:37Z
- **提交信息**: [compile] Cleanup: Remove unnecessary +rms_norm forcing for sequence parallelism (#35410)

Signed-off-by: jasonlizhengjian <jasonlizhengjian@gmail.com>

### [6467b63](https://github.com/vllm-project/vllm/commit/6467b635b6acfd5b30dd31804c79ef70ad4bf834)

- **作者**: Tib
- **时间**: 2026-02-27T12:53:35Z
- **提交信息**: [Bugfix] Add missing activation attr to RMSNormGated (#35423)

Signed-off-by: tibG <naps@qubes.milou>
Co-authored-by: tibG <naps@qubes.milou>

### [9c3fe99](https://github.com/vllm-project/vllm/commit/9c3fe9936b929b5503d780bd4e8e3cd524de1c4e)

- **作者**: Max Hu
- **时间**: 2026-02-27T12:20:23Z
- **提交信息**: Flashinfer cuDNN backend for Qwen3 VL ViT attention (#34580)

Signed-off-by: Max Hu <maxhu@nvidia.com>
Signed-off-by: Max Hu <hyoung2991@gmail.com>
Co-authored-by: Max Hu <maxhu@nvidia.com>
Co-authored-by: Shang Wang <shangw@nvidia.com>

### [b66a746](https://github.com/vllm-project/vllm/commit/b66a74649e40022c6b1180b98fbb1b6e4b4af74a)

- **作者**: Umut Polat
- **时间**: 2026-02-27T08:01:06Z
- **提交信息**: [Bugfix] Replace assert with ValueError for response_format validation in completions endpoint (#35456)

Signed-off-by: umut-polat <52835619+umut-polat@users.noreply.github.com>



---

