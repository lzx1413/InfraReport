# GitHub Stars 合并报告 - 2026-03-24

**合并日期**: 2026-03-25
**监控日期**: 2026-03-24
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


**报告日期**: 2026-03-25
**监控日期**: 2026-03-24
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 1758
- **最后更新**: 2026-03-24T12:55:58Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 2
- **主要提交者**: Bin Jia, Lu Di

## AI分析总结

根据提供的提交记录和README摘要，以下是对VeOmni项目昨日更新的分析总结：

### 1. 主要更新类型
- **Bug修复**：修复了端到端并行测试中任务名称打印时括号被错误解析的问题。
- **代码维护与工具优化**：新增了导入工具函数，并更新了微信相关的PNG图片。

### 2. 关键变更点及其与项目整体方向的关系
- **CI/CD流程改进**（提交 `f41061e`）：通过使用 `rich.Text` 避免括号被误解析，提升了测试输出的可读性和稳定性。这与VeOmni作为大规模多模态模型训练框架对**可靠性和自动化测试**的高要求一致。
- **代码结构优化**（提交 `4d98436`）：添加导入工具，可能用于简化模块导入或管理依赖，体现了项目在**代码可维护性和开发者体验**上的持续投入。
- **文档/资源更新**（提交 `9954624`）：更新微信PNG图片，可能涉及项目文档、示例或社区沟通材料的维护，支持项目的**社区生态和用户体验**。

### 3. 对项目的影响和潜在意义
- **提升开发与测试效率**：CI修复减少了测试中的潜在干扰，有助于更快发现和定位问题。
- **增强代码可维护性**：新的导入工具可能为后续功能扩展或模块重构提供便利。
- **维护项目形象与沟通渠道**：更新微信图片可能意味着项目在积极维护社区互动或文档资源，促进用户参与。

### 4. 值得关注的技术点
- **`rich.Text` 的应用**：展示了项目在控制台输出处理中注重格式与兼容性，可能对复杂测试环境的日志输出有借鉴意义。
- **导入工具的设计**：可能涉及动态导入、路径管理或依赖注入，反映了大型项目中模块化管理的常见实践。

### 5. 基于项目背景的提交影响分析
VeOmni的核心目标是**为任意模态模型训练提供模型中心的分布式方案库**。昨日的更新虽未直接涉及核心训练算法或分布式逻辑，但通过：
- **强化基础设施**：修复测试工具、优化代码结构，为大规模、多模态实验的**稳定性和可扩展性**打下基础。
- **维护项目生态**：更新资源文件，支持项目文档与社区建设，有助于吸引更多用户和贡献者，促进框架的**采用与迭代**。

这些看似细微的维护性工作，正是确保一个旨在“规模化”（Scaling）的复杂框架能够**长期可靠运行和持续演进**的重要支撑。

## 详细提交记录

### [f41061e](https://github.com/ByteDance-Seed/VeOmni/commit/f41061e5370cf744accbb5fa9de59d8909b577d7)

- **作者**: Lu Di
- **时间**: 2026-03-24T12:55:54Z
- **提交信息**: [ci] fix: use rich.Text to avoid bracket markup parsing in printing task names in e2e parallel tests (#605)

### [4d98436](https://github.com/ByteDance-Seed/VeOmni/commit/4d98436953b11cf69d9c0228c173a970f026bf7c)

- **作者**: Bin Jia
- **时间**: 2026-03-24T11:51:53Z
- **提交信息**: [misc] chore: add import utils (#604)

### [9954624](https://github.com/ByteDance-Seed/VeOmni/commit/995462414cf0f018339c4b4f502974812ff3f554)

- **作者**: Bin Jia
- **时间**: 2026-03-24T08:37:08Z
- **提交信息**: [misc] chore: update_wechat_png (#601)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-03-25
**监控日期**: 2026-03-24
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Light Image Video Generation Inference Framework
- **语言**: Python
- **星标数**: 2097
- **最后更新**: 2026-03-24T14:02:06Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Shiqiao Gu (谷石桥)

## AI分析总结

根据提供的提交记录和README摘要，以下是针对仓库 'ModelTC/LightX2V' 昨日更新的分析总结：

### 1. 主要更新类型
*   **功能新增**：添加了一个名为 `lingbot` 的新组件或功能。

### 2. 关键变更点及其与项目整体方向的关系
*   **新增 `lingbot`**：这是本次提交的核心变更。根据项目名称 **LightX2V**（轻量级视频生成推理框架）和README中强调的“Light Video Generation Inference Framework”定位，`lingbot` 很可能是一个新的、轻量化的视频生成模型、工具或集成模块。
*   **与项目方向的关系**：此变更直接服务于项目的核心目标——构建一个**轻量、高效的视频生成推理框架**。添加新的模型或组件旨在**丰富框架的能力或生态**，使其能够支持更多样化的视频生成任务或提供更便捷的开发/部署工具，从而增强项目的实用性和吸引力。

### 3. 对项目的影响和潜在意义
*   **扩展功能边界**：为框架引入了新的视频生成能力或工作流，可能覆盖了之前未支持的特定场景或需求。
*   **提升开发者体验**：如果 `lingbot` 是一个工具或集成，它可能会简化视频生成应用的开发、测试或部署流程。
*   **吸引社区关注**：持续的功能更新表明项目活跃，有助于吸引更多开发者和用户参与，构建更丰富的社区生态。

### 4. 值得关注的技术点
*   **`lingbot` 的具体定义**：提交信息较为简洁，未明确说明 `lingbot` 是**一个新的轻量视频生成模型**、一个**与特定大语言模型（LLM）或聊天机器人集成的工具**，还是一个**辅助性的命令行或Web界面工具**。其具体技术实现和定位是后续关注的重点。
*   **集成方式**：需要关注 `lingbot` 是如何与现有 LightX2V 框架的核心推理引擎、模型库或API进行集成的，是作为插件、独立模块还是核心扩展。
*   **性能与轻量化**：作为“Light”框架的一部分，`lingbot` 组件本身是否保持了轻量、高效的特点，其对推理速度、资源消耗的影响值得评估。

### 5. 基于项目背景的提交影响分析
LightX2V 项目旨在成为一个专注于**推理部署**的轻量级视频生成框架，区别于训练框架。昨日的提交（添加 `lingbot`）可以理解为：
*   **强化核心定位**：通过引入新的组件，持续丰富其作为“推理框架”的工具箱，使开发者能利用该框架更灵活、便捷地构建和部署视频生成应用。
*   **探索应用场景**：这可能是在探索视频生成与自然语言交互、特定垂直领域应用或简化工作流的新结合点，旨在扩大框架的实际应用范围。
*   **生态建设步骤**：这是项目迭代和生态建设中的一步，通过不断添加功能来完善框架，逐步实现其成为高效、易用视频生成推理解决方案的长期目标。

**总结**：本次更新是一次**功能扩展**，通过添加 `lingbot` 来增强 LightX2V 框架的能力。虽然具体细节不明，但它符合项目向轻量、高效、功能丰富的视频生成推理平台发展的方向，旨在提升框架的实用性和竞争力。

## 详细提交记录

### [54a193e](https://github.com/ModelTC/LightX2V/commit/54a193eda530660b186817ca3432f970b03da9ea)

- **作者**: Shiqiao Gu (谷石桥)
- **时间**: 2026-03-24T07:02:18Z
- **提交信息**: add lingbot (#959)

Co-authored-by: gushiqiao <975033167>

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-03-25
**监控日期**: 2026-03-24
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 1978
- **最后更新**: 2026-03-23T03:43:39Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-03-25
**监控日期**: 2026-03-24
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5212
- **最后更新**: 2026-03-24T19:36:24Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 3
- **主要提交者**: Albert Cheng, nv-yunzheq, Li Min

## AI分析总结

根据提供的提交记录和README摘要（FlashInfer是一个专注于推理的高性能GPU内核项目），以下是昨日更新的分析总结：

### 1. 主要更新类型
- **Bug修复**：修复了`int32`整数溢出问题，解决了大规模专家并行（EP）配置下的错误。
- **功能新增**：为SM100f GPU架构添加了Mixture of Experts（MoE）工具的前期编译（AOT）支持。
- **依赖更新**：将`nvidia-cutlass-dsl`依赖版本从`>=4.3.4`升级到`>=4.4.2`，并优化了CI配置。

### 2. 关键变更点及其与项目整体方向的关系
- **整数溢出修复**：针对大规模MoE模型（如DeepSeek-R1）在EP32+配置下部署时出现的“Unsupported hidden state scale shape”错误，通过将计算中的`int`提升为`int64_t`来避免溢出。这直接关系到项目**支持大规模、高性能推理**的核心目标，确保了框架在极端规模下的稳定性和可靠性。
- **MoE AOT工具添加**：为SM100f架构（如H100 GPU）引入MoE相关的CUTLASS DSL工具到AOT包中。这**增强了项目对前沿硬件和复杂模型架构（MoE）的优化支持**，符合其提供尖端GPU内核的定位。
- **CUTLASS DSL版本升级**：更新依赖至较新版本，并设置CI环境立即使用新版本。这**保持了项目依赖的现代性和兼容性**，有助于利用库的最新优化和修复。

### 3. 对项目的影响和潜在意义
- **稳定性提升**：修复了可能影响大规模生产部署的关键Bug，特别是对于像DeepSeek-R1这样的大模型，**提升了项目在超大规模推理场景下的可用性和信誉**。
- **功能扩展**：新增的MoE AOT支持**扩展了项目的应用场景**，使其能更好地服务于当前流行的MoE模型架构。
- **维护性增强**：依赖更新和CI优化**确保了开发流程的顺畅和代码库的健康**。

### 4. 值得关注的技术点
- **大规模计算的整数溢出**：这是一个在超大规模（数十亿参数、高并行度）AI推理中容易被忽视但至关重要的问题。修复方案（使用`int64_t`）是处理此类问题的标准做法。
- **专家并行（EP）与MoE**：提交内容密集涉及MoE和EP，这是当前大模型推理的前沿和复杂领域，表明FlashInfer正在深入优化这些高性能场景。
- **AOT（Ahead-of-Time）编译**：将特定工具加入AOT包，有助于**提升内核的启动性能和部署便利性**，是高性能推理库的常见优化手段。
- **与vLLM的深度集成**：从Bug描述中可以看出，此问题是在vLLM框架中暴露的，说明FlashInfer作为底层内核被vLLM等主流推理框架所使用，其稳定性直接影响上层生态。

### 5. 基于项目背景的提交影响分析
FlashInfer的目标是提供“高性能GPU推理内核”。昨日的更新完美契合了这一方向：
- **强化核心优势**：通过修复大规模EP部署的Bug，**巩固了其在高性能、大规模推理场景下的核心竞争力**。一个能稳定处理EP32配置的底层内核库，是其技术先进性的有力证明。
- **紧跟技术趋势**：积极添加对MoE模型和SM100f（H100）硬件的AOT支持，表明项目**紧密跟随AI模型和硬件的最新发展**，确保其内核始终处于优化前沿。
- **支撑上层生态**：作为vLLM等框架的底层依赖，这些修复和增强**直接提升了整个AI推理栈的稳定性和能力**，增强了FlashInfer在生态系统中的关键价值。

**总结**：昨日的更新是一次聚焦于**稳定性加固**和**功能前沿扩展**的迭代。它解决了大规模部署中的一个关键瓶颈，并为进一步优化先进的MoE模型铺平了道路，整体上使FlashInfer更稳健、更强大，更符合其作为高性能推理基础设施工厂的定位。

## 详细提交记录

### [6d34eba](https://github.com/flashinfer-ai/flashinfer/commit/6d34ebad8734e1e1fbb8e046a9cd33d3c9239772)

- **作者**: nv-yunzheq
- **时间**: 2026-03-24T14:31:44Z
- **提交信息**: fix: add cute dsl moe utils to AOT (#2872)

<!-- .github/pull_request_template.md -->

## 📌 Description

Add cute dsl moe utils to AOT package

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
* Added Mixture of Experts utilities support for SM100f GPU architecture
in ahead-of-time compilation.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [23bf17b](https://github.com/flashinfer-ai/flashinfer/commit/23bf17b6dd0f18de1130438cbc3b775c0bebac5f)

- **作者**: Li Min
- **时间**: 2026-03-24T13:24:45Z
- **提交信息**: feat: bump nvidia-cutlass-dsl to >=4.4.2 (#2833)

Update requirements.txt to require >=4.4.2 and add CI override via
setup_python.env so tests use the new version immediately without
waiting for Docker image rebuild.

<!-- .github/pull_request_template.md -->

## 📌 Description

 ## Summary
- Update `requirements.txt` to require `nvidia-cutlass-dsl>=4.4.2` (was
`>=4.3.4`)
- Add `CUTLASS_DSL_VERSION` override support in
`scripts/setup_test_env.sh`
- Set `CUTLASS_DSL_VERSION=4.4.2` in `ci/setup_python.env` so CI tests
use the new version immediately without waiting for Docker image
  rebuild

  ## Test plan
- [x] CI tests pass with nvidia-cutlass-dsl 4.4.2 installed via
setup_python.env override
- [x] After Docker images are rebuilt, remove `CUTLASS_DSL_VERSION` from
`ci/setup_python.env`

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

* **Chores**
  * Updated nvidia-cutlass-dsl dependency requirement to version 4.4.2
* Added CUTLASS_DSL_VERSION environment variable for CI configuration
override
* Enhanced test environment setup with CUDA-aware package selection
logic
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>
Co-authored-by: Yunzhe Qiu <yunzheq@nvidia.com>

### [76790d8](https://github.com/flashinfer-ai/flashinfer/commit/76790d894b136f9eb7f8262e3b33dba92d3d8768)

- **作者**: Albert Cheng
- **时间**: 2026-03-24T13:20:18Z
- **提交信息**: fix: int32 overflow in `trtllm_fp4_block_scale_moe` causing "Unsupported hidden state scale shape" for EP32+ configs (#2853)

## 📌 Description

Fix `int32` overflow in `trtllm_fp4_block_scale_moe` that causes a
misleading `NotImplementedError: Unsupported hidden state scale shape`
when deploying large Expert Parallel configurations (e.g., EP32 with
`DeepSeek-R1 NVFP4`).


**Step 1, NVFP4 activation quantization (per EP rank)**

Each of the 32 EP ranks quantizes its local activations via
`vllm.ops.scaled_fp4_quant` with `is_sf_swizzled_layout=False`. From
[nvfp4_quant_entry.cu](https://github.com/vllm-project/vllm/blob/a5e9d511defe2d2dc2dd270674fc197542fc0169/csrc/quantization/fp4/nvfp4_quant_entry.cu):
```cpp
output_sf = torch::empty(
    {m, n / CVT_FP4_SF_VEC_SIZE},
    torch::TensorOptions().device(device).dtype(torch::kUInt8));
```
For m=10240 (`max_num_batched_tokens`), n=7168 (`hidden_size`):

`hidden_states`: `[10240, 3584]` `uint8` (FP4 packed, 2 values per byte)
`hidden_states_scale`: `[10240, 448]` `uint8` → viewed as
`float8_e4m3fn`
No padding is applied in the non-swizzled layout. Scale numel = `10240 ×
448 = 4,587,520`.

**Step 2, EP allgather via dispatch()**

`MoEPrepareAndFinalizeNaiveDPEPModular.prepare()` in
[naive_dp_ep.py](https://github.com/vllm-project/vllm/blob/a5e9d511defe2d2dc2dd270674fc197542fc0169/vllm/model_executor/layers/fused_moe/prepare_finalize/naive_dp_ep.py)
calls `get_ep_group().dispatch()`, which allgathers both `hidden_states`
and `hidden_states_scale` (passed as `extra_tensors`) across all 32 EP
ranks:

`hidden_states`: `32 × [10240, 3584]` → [`327680, 3584]`
`hidden_states_scale`: `32 × [10240, 448]` → `[327680, 448]`

**Step 3, Scale reshape in vLLM wrapper**

In
[trtllm_nvfp4_moe.py](https://github.com/vllm-project/vllm/blob/a5e9d511defe2d2dc2dd270674fc197542fc0169/vllm/model_executor/layers/fused_moe/experts/trtllm_nvfp4_moe.py),
the scale is reshaped before passing to flashInfer:
```
hidden_states_scale=a1q_scale.view(torch.float8_e4m3fn).reshape(
    *hidden_states.shape[:-1], -1)  # → [327680, 448]
```
At this point `hidden_states_scale.numel()` = 327680 × 448 =
146,800,640.

**Step 4, int32 overflow in FlashInfer C++ kernel**

In `csrc/trtllm_fused_moe_kernel_launcher.cu`, the scale vector size is
computed as:
```cpp
int const num_tokens = hidden_states.size(0);   // int (32-bit) = 327680
int hidden_size = hidden_states.size(1);          // int (32-bit) = 3584
if (hidden_states.dtype() == dl_uint8) hidden_size *= 2;  // hidden_size = 7168
hidden_states_scale_vec_size =
    (num_tokens * hidden_size) / hidden_states_scale.value().numel();
//   ^^^^^^^^^^^^^^^^^^^^^^^^
//   int * int = int → OVERFLOW before promotion to int64 for division
```

the overflow:
`327680 × 7168 = 2,348,810,240`
`INT_MAX` = 2,147,483,647
2,348,810,240 > `INT_MAX`, signed int32 overflow (undefined behavior in
C++, wraps to -1,946,157,056 on two's complement architectures)

vec_size = -1,946,157,056 / 146,800,640 = -13
-13 ≠ 16 and -13 ≠ 32 will throws "Unsupported hidden state scale shape"

Step 5, why not and works

Overflow threshold for DeepSeek-R1 (hidden_size=7168):
Max safe tokens: INT_MAX / 7168 = 299,593
EP32 per-rank limit: 299,593 / 32 ≈ 9,362
Any max_num_batched_tokens > 9362 with EP32 will trigger the overflow

We confirmed the overflow boundary on an 8-node GB200 cluster (32 GPUs,
EP32, DP32) with --all2all-backend `allgather_reducescatter`:

| max_num_batched_tokens | Total tokens (×32) | M × 7168 | vs INT_MAX |
Result |
| :--- | :--- | :--- | :--- | :--- |
| 9360 | 299,520 | 2,146,560,000 | < 2,147,483,647 | ✅ Success |
| 9370 | 299,840 | 2,148,853,760 | > 2,147,483,647 | ❌ **Crash** |
| 8192 (Workaround) | 262,144 | 1,879,048,192 | < 2,147,483,647 | ✅
Success |
| 10240 (Original) | 327,680 | 2,348,810,240 | > 2,147,483,647 | ❌
**Crash** |


**Reproduction**
vLLM serve with EP32:
```
vllm serve nvidia/DeepSeek-R1-NVFP4 \
    --tensor-parallel-size 1 \
    --data-parallel-size 32 \
    --enable-expert-parallel \
    --all2all-backend allgather_reducescatter \
    --max-num-batched-tokens 10240 \
    --kv-cache-dtype fp8 \
    --trust-remote-code
```
Crashes during engine initialization with:
`NotImplementedError: Unsupported hidden state scale shape.` (Also found
this issue in
https://github.com/vllm-project/vllm/pull/36022#issuecomment-4062909013)



Promote the multiplication operands to int64_t before division to
prevent overflow:
`hidden_states_scale_vec_size`: Cast num_tokens to int64_t so the
multiplication chain executes in 64-bit.
`weight_scale_vec_size`: Apply the same pattern with local_num_experts
cast to int64_t, and declare the variable as int64_t for consistency.

Cast the multiplication operands to int64_t before the division:
```cpp
// In csrc/trtllm_fused_moe_kernel_launcher.cu
// Before (overflow-prone):
int const num_tokens = hidden_states.size(0);
int hidden_size = hidden_states.size(1);
if (hidden_states.dtype() == dl_uint8) hidden_size *= 2;
hidden_states_scale_vec_size =
    (num_tokens * hidden_size) / hidden_states_scale.value().numel();

// After (safe):
int const num_tokens = hidden_states.size(0);
int hidden_size = hidden_states.size(1);
if (hidden_states.dtype() == dl_uint8) hidden_size *= 2;
    hidden_states_scale_vec_size = (static_cast<int64_t>(num_tokens) * hidden_size) / hidden_states_scale.value().numel();
  }
```

The same pattern should also be applied to weight_scale_vec_size for
safety:
```cpp
int64_t weight_scale_vec_size =
    (static_cast<int64_t>(local_num_experts) * intermediate_size
     * intermediate_size_factor * hidden_size) /
    gemm1_weights_scale.numel();
```

**Impact**
Zero performance impact: these are CPU-side setup computations executed
once before GPU kernel launch.
Zero API change: No function signatures are modified.
Unblocks: EP32+ deployments for large-hidden-size models (DeepSeek-R1,
etc.) with max_num_batched_tokens above the int32 threshold.

**Environment**
Model: DeepSeek-R1-0528-FP4 (NVFP4, hidden_size=7168)
Hardware: 8× GB200 nodes (32 GPUs), disaggregated prefill-decode
Configuration: DP=32, EP=32, TP=1, PP=1
vLLM: v0.17.2rc1 (bundled FlashInfer)


## 🔍 Related Issues


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
* Fixed integer overflow in internal size calculations that could cause
crashes or incorrect behavior with very large models or batch sizes,
improving stability and reliability for large-scale inference.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Albert Cheng (Engrg-Hardware 1) <albecheng@login-lyris01.lyris.clusters.nvidia.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-03-25
**监控日期**: 2026-03-24
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3299
- **最后更新**: 2026-03-24T22:10:10Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Kaiqin Kong

## AI分析总结

根据提供的仓库信息和提交记录，以下是针对昨日更新的分析总结：

### 1. 主要更新类型
- **重构/代码优化**：本次提交（`74db6e1`）归类为 `[misc]`，主要涉及对验证（validation）和预处理（preprocess）流程中“action loading”机制的更新，属于代码内部逻辑的优化与重构。

### 2. 关键变更点及其与项目整体方向的关系
- **关键变更**：优化了验证和预处理阶段中“action loading”（可能指模型推理动作或数据加载动作）的实现方式。
- **与项目方向的关系**：FastVideo 项目专注于高效视频处理与AI推理（参考README中的“Quick Start”和“Documentation”链接）。本次更新直接针对核心流程（验证和预处理）进行改进，符合项目提升**处理效率、稳定性和代码可维护性**的整体方向。

### 3. 对项目的影响和潜在意义
- **积极影响**：
    - 可能提升了验证和预处理阶段的代码清晰度或执行可靠性。
    - 为后续功能扩展或性能优化打下更好的代码基础。
- **潜在意义**：这类底层重构通常旨在减少潜在错误、统一接口或提升流程的可配置性，有助于长期项目的稳健迭代。

### 4. 值得关注的技术点
- **“action loading”机制**：具体实现细节未在提交信息中明确，但可能涉及**动态加载不同的处理动作或模型**，这是构建灵活视频处理管道的关键设计。
- **提交关联的PR #1143**：建议查看该Pull Request的详细讨论，以了解更具体的技术动机和修改细节。

### 5. 基于项目背景的提交影响分析
- FastVideo 项目定位为高效的视频AI处理工具库（从README强调的文档、快速开始和社区会议可知）。本次更新虽未直接增加用户可见功能，但通过**优化内部核心流程**，间接支持了项目的核心目标：
    - **提升开发体验**：更清晰的代码结构便于团队协作和后续开发（与“Weekly Dev Meeting”的社区活跃导向一致）。
    - **保障处理管线稳定性**：验证和预处理是视频AI流程的基础环节，其优化有助于提高整个系统输出的可靠性。
    - **渐进式技术债管理**：持续重构是保持项目长期健康发展的常见实践。

**总结**：本次更新是一次针对核心流程的底层代码优化，虽不涉及用户端新特性，但通过提升代码质量间接强化了项目的**效率、可维护性和长期发展基础**，符合FastVideo作为高效视频AI工具库的定位。

## 详细提交记录

### [74db6e1](https://github.com/hao-ai-lab/FastVideo/commit/74db6e18d184ce9e06add5f8471bbe24e738b333)

- **作者**: Kaiqin Kong
- **时间**: 2026-03-24T22:10:03Z
- **提交信息**: [misc] update action loading in validation and preprocess (#1143)

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-03-25
**监控日期**: 2026-03-24
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 33143
- **最后更新**: 2026-03-24T21:14:19Z

## 提交统计

- **昨日提交总数**: 7
- **提交者数量**: 6
- **主要提交者**: YangKai0616, Dhruv Nair, Cheung Ka Wai

## AI分析总结

根据提供的 `huggingface/diffusers` 仓库提交记录和README背景（一个专注于扩散模型的Python库，用于图像、音频生成等任务），以下是昨日更新的要点总结：

### 1. 主要更新类型
- **Bug修复**：占主导，涉及注意力掩码、导入错误、测试失败等问题（提交1、4、5、6）。
- **重构/代码优化**：改进数据结构以提升代码健壮性（提交2）。
- **性能优化**：稳定低精度计算下的归一化操作（提交7）。
- **CI/CD更新**：更新持续集成流程以适配最新工具版本（提交3）。

### 2. 关键变更点及其与项目整体方向的关系
- **图像模型与注意力机制修复**（提交1、6）：针对`ZImageTransformer2D`和`QwenImage`的注意力掩码问题进行修复，确保模型在序列长度不等或特定架构下正确运行。这直接支持项目核心目标——提供可靠、高效的扩散模型组件。
- **适配器与LoRA相关改进**（提交2、5）：通过使用`defaultdict`优化适配器缩放函数映射，并修复LoRA测试，增强了模型微调（如LoRA）的稳定性和可维护性。这符合项目对模块化、可扩展模型适配的支持。
- **低精度计算稳定性**（提交7）：在自定义自动编码器中稳定RMS归一化的低精度（如fp8/fp4）计算，提升模型在资源受限环境或高性能场景下的鲁棒性。这与项目优化推理效率的方向一致。
- **依赖管理与测试**（提交3、4）：更新CI中的管道获取逻辑，并修复未受保护的`torchvision`导入，确保库与最新Hub版本兼容并避免运行时错误。这维护了项目的生态集成和用户体验。

### 3. 对项目的影响和潜在意义
- **提升模型可靠性**：修复注意力掩码和导入错误，防止潜在崩溃或错误输出，增强用户信任。
- **加速开发迭代**：CI更新和测试修复确保自动化流程顺畅，减少开发中断。
- **扩展应用场景**：低精度优化使模型更易部署在边缘设备或大规模服务中，拓宽使用范围。
- **社区协作体现**：多个提交由社区贡献者协同完成，反映项目活跃的开放协作生态。

### 4. 值得关注的技术点
- **注意力掩码的动态处理**（提交1）：仅在序列长度不等时构建掩码，优化计算效率。
- **defaultdict在配置映射中的应用**（提交2）：简化代码逻辑，避免键缺失错误。
- **低精度RMS归一化的数值稳定性**（提交7）：涉及混合精度训练中的常见挑战，对扩散模型的质量至关重要。
- **QwenImage特定修复**（提交6）：针对新兴模型架构的快速响应，显示项目对前沿技术的跟进。

### 5. 基于项目背景的提交影响分析
Diffusers库旨在成为扩散模型的**标准化、高性能工具箱**。昨日的更新整体强化了这一方向：
- **功能完善性**：通过修复多个模型组件（如图像Transformer、自动编码器），确保库覆盖的模型家族（如Stable Diffusion、Qwen）运行更稳定，支持更复杂的生成任务。
- **开发者体验**：重构和CI更新降低了贡献门槛和维护成本，鼓励社区参与，符合开源项目的发展需求。
- **生产就绪性**：低精度优化和依赖管理改进提升了库在工业场景中的适用性，助力扩散模型从研究到应用的过渡。

这些提交虽以修复和优化为主，未引入重大新功能，但**巩固了项目基础**，为后续大规模模型集成和性能突破铺平道路，体现了项目在快速迭代中保持代码质量的成熟度。

## 详细提交记录

### [da6718f](https://github.com/huggingface/diffusers/commit/da6718f08032580a943f278a052364471302d89a)

- **作者**: Beinsezii
- **时间**: 2026-03-24T16:06:50Z
- **提交信息**: ZImageTransformer2D: Only build attention mask if seqlens are not equal (#12955)

### [832676d](https://github.com/huggingface/diffusers/commit/832676d35ec102b107453e63957ae851479eac1a)

- **作者**: Alexey Kirillov
- **时间**: 2026-03-24T12:19:50Z
- **提交信息**: Use defaultdict for _SET_ADAPTER_SCALE_FN_MAPPING (#13320)

refactor: use defaultdict for _SET_ADAPTER_SCALE_FN_MAPPING

Co-authored-by: Alexkkir <alexkkir@gmail.coom>
Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

### [7bbd96d](https://github.com/huggingface/diffusers/commit/7bbd96da5da2af3f49e4a0c5d461db6e15d47e10)

- **作者**: Dhruv Nair
- **时间**: 2026-03-24T11:12:32Z
- **提交信息**: [CI] Update fetching pipelines for latest HF Hub Version (#13322)

update

### [62777fa](https://github.com/huggingface/diffusers/commit/62777fa819aa14164199c410f9bae46d9830c2e1)

- **作者**: Dhruv Nair
- **时间**: 2026-03-24T10:30:24Z
- **提交信息**: Fix unguarded `torchvision` import in Cosmos (#13321)

update

### [f1fd515](https://github.com/huggingface/diffusers/commit/f1fd5152579aae2fb293a389016a6026fed41b53)

- **作者**: Sayak Paul
- **时间**: 2026-03-24T10:18:03Z
- **提交信息**: [tests] fix lora logging tests for models. (#13318)

* fix lora logging tests for models.

* make style

### [afdda57](https://github.com/huggingface/diffusers/commit/afdda57f61f77eb67165db22bd56963cb905e648)

- **作者**: Cheung Ka Wai
- **时间**: 2026-03-24T09:12:50Z
- **提交信息**: Fix the attention mask in ulysses SP for QwenImage (#13278)

* fix mask in SP

* change the modification to qwen specific

* drop xfail since qwen-image mask is fixed

---------

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

### [5fc2bd2](https://github.com/huggingface/diffusers/commit/5fc2bd2c8f556fdcce0593613dbba90212e9e7e5)

- **作者**: YangKai0616
- **时间**: 2026-03-24T09:00:05Z
- **提交信息**: Stabilize low-precision custom autoencoder RMS normalization (#13316)

* Stabilize low-precision custom autoencoder RMS normalization

* Add fp8/4

* Apply style fixes

---------

Co-authored-by: github-actions[bot] <github-actions[bot]@users.noreply.github.com>
Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-03-25
**监控日期**: 2026-03-24
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 387
- **最后更新**: 2026-03-24T05:55:47Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-03-25
**监控日期**: 2026-03-24
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12086
- **最后更新**: 2026-03-24T21:41:40Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Zhongjie Duan, lzws

## AI分析总结

根据提供的README摘要和提交记录，以下是针对 `modelscope/DiffSynth-Studio` 仓库昨日更新的分析总结：

### 1. 主要更新类型
- **功能新增**：新增了 `FireRed-Image-Edit-1.1` 模型示例，并更新了 `flux.2-dev` 的编辑示例。
- **版本发布**：将项目版本更新至 `2.0.7`，属于常规迭代发布。

### 2. 关键变更点及其与项目整体方向的关系
- **新增模型示例**：`FireRed-Image-Edit-1.1` 的加入扩展了图像编辑功能，与项目作为“Diffusion-based Video Synthesis Studio”（基于扩散模型的视频合成工作室）的定位一致，旨在提供多样化的生成与编辑工具。
- **更新 `flux.2-dev` 示例**：强化了 `flux` 系列模型（可能指一种先进的扩散模型架构）的编辑能力，体现了项目持续集成最新AI模型技术以提升视频/图像合成质量的方向。
- **版本号迭代**：从 `2.0.6` 升至 `2.0.7`，表明项目处于活跃开发阶段，定期集成新功能和修复。

### 3. 对项目的影响和潜在意义
- **功能丰富化**：为用户提供了更多图像编辑选项，可能提升创作灵活性和输出效果。
- **技术栈更新**：保持与前沿模型（如 `flux.2-dev`）的同步，有助于维持项目竞争力。
- **开发者体验**：版本更新可能包含底层优化或依赖调整，提升稳定性和兼容性。

### 4. 值得关注的技术点
- **`flux.2-dev` 模型的应用**：可能涉及最新的扩散模型优化技术（如更高效的采样或编辑控制），值得关注其性能提升细节。
- **`FireRed-Image-Edit-1.1` 的特性**：可能专注于特定风格的图像编辑（如色彩增强、细节修复），扩展了项目的实用场景。

### 5. 基于项目背景的提交影响分析
- **README 背景**：项目定位为开源视频合成工作室，集成多种扩散模型（如 Stable Diffusion、FLUX 等）支持视频生成、编辑和控制。昨日更新直接服务于这一目标：
  - **增强编辑能力**：新增示例强化了图像编辑模块，与项目“Studio”特性（提供全流程创作工具）高度契合。
  - **技术生态维护**：持续集成新模型示例，有助于吸引社区关注和贡献，推动项目作为AI创作平台的发展。
  - **用户价值提升**：更多示例降低了用户使用门槛，促进项目在视频合成领域的应用普及。

**总结**：昨日更新以功能新增为主，通过扩展模型示例和版本迭代，进一步巩固了项目作为前沿AI视频合成工具的地位，同时提升了用户体验和技术前瞻性。

## 详细提交记录

### [166e6d2](https://github.com/modelscope/DiffSynth-Studio/commit/166e6d2d38764209f66a74dd0fe468226536ad0f)

- **作者**: Zhongjie Duan
- **时间**: 2026-03-24T09:37:54Z
- **提交信息**: update version to 2.0.7 (#1370)

### [5e7e3db](https://github.com/modelscope/DiffSynth-Studio/commit/5e7e3db0afd873940edb2f530ec09a8260467c2b)

- **作者**: lzws
- **时间**: 2026-03-24T09:32:45Z
- **提交信息**: update flux.2-dev editing examples (#1369)

* add FireRed-Image-Edit-1.1

* flux.2-dev-edit

* flux.2-dev-edit

* flux.2-dev-edit

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-03-25
**监控日期**: 2026-03-24
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 24968
- **最后更新**: 2026-03-24T22:01:21Z

## 提交统计

- **昨日提交总数**: 14
- **提交者数量**: 13
- **主要提交者**: Elizaveta Martirosian, Zhang Yiyang (SII), Lianmin Zheng

## AI分析总结

根据提供的提交记录和README摘要（SGLang是一个专注于高效LLM推理和服务的项目），以下是昨日更新的分析总结：

### 1. 主要更新类型
昨日提交以**功能新增、性能优化和Bug修复**为主，同时包含**CI/CD流程改进**和**文档维护**。
*   **功能新增 (4项)**：主要为新硬件支持（AMD MI325, NPU）和新模型支持（MoE LoRA, Hunyuan3D, Minimax2.5量化）。
*   **性能优化 (2项)**：针对GPT MoE路由和AMD GPU的稀疏计算进行了优化。
*   **Bug修复 (3项)**：修复了AMD兼容性、扩散模型输出正确性和评估脚本的问题。
*   **CI/CD与测试 (4项)**：新增测试套件、调整CI策略、添加链接检查、修改定时任务。
*   **文档/维护 (2项)**：更新代码所有者文件和文档链接检查。

### 2. 关键变更点及其与项目方向的关系
| 关键变更点 | 与项目方向的关系 |
| :--- | :--- |
| **支持MoE模型的LoRA微调与张量并行** (`a32e0d5`) | **核心能力扩展**。SGLang旨在高效服务LLM，此提交直接增强了其对复杂、高性能模型（MoE）的微调和服务能力，是项目向支持更先进模型架构迈进的关键一步。 |
| **为AMD MI325等GPU新增测试与优化** (`6cb1c2d`, `855d15a`) | **硬件生态拓展**。通过增加对AMD最新硬件的官方测试支持和性能优化（稀疏计算），表明项目正积极拥抱多元化的硬件生态，以提升其在不同部署环境下的适用性和性能。 |
| **集成FlashInfer优化GPT MoE路由** (`bbe25b2`) | **性能核心优化**。利用高性能内核（FlashInfer）优化MoE模型的关键路径（路由计算），直接服务于项目的核心目标——**提升LLM推理效率**。 |
| **新增对Hunyuan3D等扩散模型的支持与修复** (`9f4d8ac`, `eefb504`) | **模态与模型扩展**。虽然README强调LLM，但项目实际已扩展至多模态（如图像生成的扩散模型）。这些提交巩固了其在**AIGC全栈推理**领域的能力。 |
| **NPU支持与模型量化适配** (`1b4933d`) | **部署优化与硬件扩展**。适配特定硬件的量化层，体现了项目对**模型压缩**和**边缘/专用芯片部署**场景的重视，与高效推理的目标高度一致。 |

### 3. 对项目的影响和潜在意义
*   **提升竞争力**：对MoE、最新AMD GPU、NPU和多种扩散模型的深度支持，使SGLang在**多硬件、多模型的高效推理框架**竞争中保持前沿地位。
*   **拓宽应用场景**：从纯文本LLM服务扩展到文生图、3D生成等多模态任务，潜在用户群和应用场景得到显著拓宽。
*   **增强稳定性与开发者体验**：持续的CI/CD改进、Bug修复和文档维护，有助于提升框架的稳定性和对社区开发者、贡献者的友好度。

### 4. 值得关注的技术点
1.  **MoE + LoRA + TP的协同** (`a32e0d5`)：在混合专家模型上实现参数高效微调并与张量并行结合，是部署大规模可定制化MoE模型的重要技术路径。
2.  **硬件特定优化** (`bbe25b2`, `855d15a`)：针对SM90+（NVIDIA）和AMD MI300系列GPU的定制化内核优化，展示了框架层与底层计算库深度结合以榨取硬件性能的趋势。
3.  **多模态推理统一**：提交中同时涉及LLM（GPT MoE）、视觉语言模型（FLUX.1）和扩散模型（Hunyuan3D），表明SGLang正试图构建一个**统一的后端推理引擎**来服务不同类型的生成式AI模型。

### 5. 基于项目背景的提交影响分析
SGLang的目标是成为“LLM操作系统的运行时”。昨日的提交集体指向这一目标的深化：
*   **“高效”**：通过FlashInfer集成和AMD稀疏优化直接体现。
*   **“服务”**：通过扩展支持的模型（MoE, Hunyuan3D）和硬件（AMD, NPU），使操作系统能在更多“设备”（硬件）上运行更多“应用程序”（模型）。
*   **“生态系统”**：完善的CI/CD、测试套件和文档检查，是维护一个健康开源项目生态系统的基础，能吸引更多开发者（如提交中活跃的AMD、NPU贡献者）和用户。
*   **超越LLM**：虽然README以LLM为焦点，但实际开发已涵盖扩散模型，暗示项目愿景可能是一个更通用的**生成式AI推理与服务运行时**，LLM是其当前最重要但非唯一的组成部分。

**总结**：昨日的更新是一次集中的**能力强化与生态扩展**。它不仅在核心的LLM推理性能（MoE优化）和部署广度（新硬件）上发力，还巩固了其在多模态推理领域的能力，并通过工程实践保障了项目质量，整体上推动SGLang朝着更强大、更稳定、更通用的AI推理运行时演进。

## 详细提交记录

### [bbe25b2](https://github.com/sgl-project/sglang/commit/bbe25b24126d456965577c159557f97036556e9f)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-03-24T22:00:18Z
- **提交信息**: Use FlashInfer tinygemm for GPT-OSS MoE router on SM90+ (#20755)

Co-authored-by: elvischenv <219235043+elvischenv@users.noreply.github.com>

### [31c35f1](https://github.com/sgl-project/sglang/commit/31c35f1c2233ca58896227687c448c0e6f0c7b2d)

- **作者**: Liangsheng Yin
- **时间**: 2026-03-24T21:07:25Z
- **提交信息**: [CI] Skip multimodal CI for doc-only changes (#21334)

### [6cb1c2d](https://github.com/sgl-project/sglang/commit/6cb1c2d53da32650aea68f290e3cbc0024964f54)

- **作者**: Michael
- **时间**: 2026-03-24T21:04:49Z
- **提交信息**: [AMD] Add 4-GPU test suite for MI325 runners (#20294)

### [c4db64c](https://github.com/sgl-project/sglang/commit/c4db64c16bba9cb549d510735a064272c87779fa)

- **作者**: Jiaxin(Jackson) Deng
- **时间**: 2026-03-24T20:48:26Z
- **提交信息**: Add Lychee Doc Links Check to Local and CI (#19742)

Co-authored-by: Zijie Xia <zijie_xia@icloud.com>
Co-authored-by: Zijie Xia <zijiexia@users.noreply.github.com>
Co-authored-by: zijiexia <37504505+zijiexia@users.noreply.github.com>

### [a32e0d5](https://github.com/sgl-project/sglang/commit/a32e0d57e7f04db5fa9a728b4e4ef1a2e537fe00)

- **作者**: Jonah Bernard
- **时间**: 2026-03-24T20:14:14Z
- **提交信息**: [LoRA][III] Add LoRA support for MoE layers and enable TP (#14105)

Co-authored-by: Yusheng Su <yushengsu.thu@gmail.com>
Co-authored-by: Baizhou Zhang <sobereddiezhang@gmail.com>

### [a3ed2e4](https://github.com/sgl-project/sglang/commit/a3ed2e4d2974ff643eeaec2101925c41b604932d)

- **作者**: Zhang Yiyang (SII)
- **时间**: 2026-03-24T18:28:16Z
- **提交信息**: [diffusion][CI] Add CI for MOVA model inference (#20430)

Co-authored-by: Luo <139519292+0-693@users.noreply.github.com>
Co-authored-by: Mick <mickjagger19@icloud.com>

### [71f5ae3](https://github.com/sgl-project/sglang/commit/71f5ae3f9acd52fd47430d2a5e7e44d0a5feb540)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-03-24T17:41:44Z
- **提交信息**: [AMD] Fix AMD Nightly Test - Transformers 5.3.0 incompatibility and gemma2-27b kv issue (#21193)

Co-authored-by: bingxche <Bingxu.Chen@amd.com>

### [9f4d8ac](https://github.com/sgl-project/sglang/commit/9f4d8ac99f81f77097f365d3ebfa8f6c5e326d57)

- **作者**: Elizaveta Martirosian
- **时间**: 2026-03-24T13:18:49Z
- **提交信息**: [Diffusion][NPU] Add support for Hunyuan3D (#20352)

Co-authored-by: Elizaveta Martirosian <elizaveta.martirosian@gmail.com>

### [1b4933d](https://github.com/sgl-project/sglang/commit/1b4933d45d9384feede20e4cf4fc6c5df2c7e04e)

- **作者**: shadowxz109
- **时间**: 2026-03-24T12:57:18Z
- **提交信息**: [NPU][ModelSlim] adapt w2 quant layer for Minimax2.5 (#20905)

### [eefb504](https://github.com/sgl-project/sglang/commit/eefb504f843a1fb856a77ad399b4c34e49eeb4f0)

- **作者**: Aleksi Vesanto
- **时间**: 2026-03-24T12:17:33Z
- **提交信息**: [diffusion] model: Fix FLUX.1 output correctness (#21041)

Co-authored-by: Mick <mickjagger19@icloud.com>

### [4fbb311](https://github.com/sgl-project/sglang/commit/4fbb311234f75e54834400458a809b0a383831cd)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-03-24T09:25:11Z
- **提交信息**: [Fix][Eval] Keep `--dataset-path` scoped to `longbench_v2` (#21156)

### [8d7453d](https://github.com/sgl-project/sglang/commit/8d7453d8fb887d0e4e6e368b2a603a45242981b7)

- **作者**: Ke Bao
- **时间**: 2026-03-24T09:15:25Z
- **提交信息**: Update CODEOWNERS (#21298)

### [855d15a](https://github.com/sgl-project/sglang/commit/855d15adf6571e90b07bb851bbab512def1d3413)

- **作者**: Thomas Wang
- **时间**: 2026-03-24T09:01:39Z
- **提交信息**: [AMD] Tilelang sparse fwd for dsv32 mi355/mi300 (#19945)

### [3dfaa47](https://github.com/sgl-project/sglang/commit/3dfaa47d5e1141235c37a9f26bf9bc3646551ac0)

- **作者**: Lianmin Zheng
- **时间**: 2026-03-24T07:04:23Z
- **提交信息**: Change cron schedule to run every 6 hours (#21285)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-03-25
**监控日期**: 2026-03-24
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with hybrid cache acceleration and massive parallelism for DiTs.
- **语言**: Python
- **星标数**: 1107
- **最后更新**: 2026-03-24T12:32:45Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

根据仓库README摘要（PyTorch原生推理引擎，专注于DiTs的混合缓存加速和大规模并行）及提交记录，以下是昨日更新的分析总结：

### 1. 主要更新类型
- **功能新增**：支持区域量化（regional quantization）。
- **性能优化**：优化量化统计摘要（quant stats summary）。
- **内核集成**：将自定义通信内核（包括FP8）注册为Torch操作（ops）。
- **文档/样式更新**：调整文档高亮颜色。

### 2. 关键变更点及其与项目整体方向的关系
- **区域量化支持**：允许对模型不同区域应用差异化量化策略，**直接增强量化灵活性**，与项目“混合缓存加速”方向一致，可提升推理效率与精度平衡。
- **内核注册为Torch操作**：将底层通信内核（包括FP8支持）深度集成到PyTorch框架中，**强化了“PyTorch原生”特性**，有利于提升跨平台兼容性和执行效率。
- **量化统计摘要优化**：简化或加速量化过程中的统计信息计算，**支持大规模并行处理**，减少预处理开销。

### 3. 对项目的影响和潜在意义
- **提升量化适应性**：区域量化使模型能针对不同结构（如注意力层与MLP层）采用不同量化参数，可能**提高压缩后模型的精度保持能力**。
- **增强系统集成度**：内核注册为Torch操作可降低部署复杂度，**改善用户体验和性能可移植性**。
- **加速开发迭代**：优化量化统计摘要有助于**更快地实验和调优量化配置**。

### 4. 值得关注的技术点
- **FP8通信内核**：低精度（FP8）通信支持对**大规模分布式推理**至关重要，可减少数据传输开销。
- **区域量化实现**：可能引入了分层或分模块的量化策略，**需关注其对缓存机制的影响**（如不同精度区域的缓存管理）。
- **Torch操作注册**：表明项目正将自定义C++/CUDA内核更紧密地融入PyTorch生态，**有利于长期维护和社区采用**。

### 5. 基于项目背景的提交影响分析
- **README强调“混合缓存加速”和“大规模并行”**：  
  - 区域量化与缓存机制协同，可能通过**差异化精度缓存**提升缓存效率。  
  - 内核注册为Torch操作**强化了并行计算基础**，使通信更高效，支持更大规模分布式推理。  
  - 量化统计优化**加速了预处理阶段**，有助于快速适配不同DiT模型结构。  
- **整体发展影响**：这些更新共同推动项目向**更灵活、高效、易集成的生产级推理引擎**演进，特别有利于复杂DiT模型（如视频生成、大分辨率图像生成）的部署优化。

---

**总结**：昨日更新聚焦于**量化增强**（区域量化、统计优化）和**系统集成深化**（内核注册），强化了项目的核心优势——通过精细化精度管理和底层优化，提升DiT推理的速度与可扩展性。

## 详细提交记录

### [477d08a](https://github.com/vipshop/cache-dit/commit/477d08ad5f8e444f1046568e825c8aa4e9e80113)

- **作者**: DefTruth
- **时间**: 2026-03-24T12:32:40Z
- **提交信息**: kernel: register comm kernels as torch ops (#905)

* register fp8 comm kernels as torch ops

* register custom kernels as torch ops

* register custom kernels as torch ops

* register custom kernels as torch ops

* register custom kernels as torch ops

* register custom kernels as torch ops

* register custom kernels as torch ops

* register custom kernels as torch ops

* register custom kernels as torch ops

* register custom kernels as torch ops

* register custom kernels as torch ops

* register custom kernels as torch ops

### [7000195](https://github.com/vipshop/cache-dit/commit/7000195fb618880b3d717eab6d9b0cd4e19b1f09)

- **作者**: DefTruth
- **时间**: 2026-03-24T08:22:28Z
- **提交信息**: chore: optimize quant stats summary (#904)

* chore: change docs highlight color

* chore: optimize quant stats summary

* chore: optimize quant stats summary

* chore: optimize quant stats summary

* chore: optimize quant stats summary

* chore: optimize quant stats summary

* chore: optimize quant stats summary

* chore: optimize quant stats summary

* chore: optimize quant stats summary

### [594542c](https://github.com/vipshop/cache-dit/commit/594542c602335202a426f7300e63d132c45af5b6)

- **作者**: DefTruth
- **时间**: 2026-03-24T07:40:27Z
- **提交信息**: chore: change docs highlight color (#903)

### [05305e8](https://github.com/vipshop/cache-dit/commit/05305e8842d2a0b63212eb7c7de2bf324aa340d3)

- **作者**: DefTruth
- **时间**: 2026-03-24T07:28:20Z
- **提交信息**: feat: support regional quantization (#902)

* feat: support regional quantize

* feat: support regional quantize

* feat: support regional quantize

* feat: support regional quantize

* feat: support regional quantize

* feat: support regional quantize

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-03-25
**监控日期**: 2026-03-24
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 74187
- **最后更新**: 2026-03-24T22:28:17Z

## 提交统计

- **昨日提交总数**: 24
- **提交者数量**: 21
- **主要提交者**: amey asgaonkar, Woosuk Kwon, Javier De Jesus

## AI分析总结

根据提供的 `vllm-project/vllm` 仓库提交记录和项目背景（一个专注于“易用、快速、廉价”的大语言模型服务框架），以下是昨日更新的要点总结：

### 1. 主要更新类型
昨日提交以 **Bug修复** 和 **功能增强/优化** 为主，辅以**文档更新**、**新模型支持**和**代码质量维护**。
*   **Bug修复 (9项)**：涉及核心调度、KV缓存、模型加载、编译、CPU支持、结构化输出等多个关键模块。
*   **功能新增与优化 (8项)**：包括调度策略、注意力机制、推理优化、硬件支持、类型检查等。
*   **文档更新 (2项)**：修复文档中的错误链接和构建问题。
*   **模型支持 (1项)**：新增对 Granite 4.0 1B 语音模型的支持。
*   **代码维护与重构 (3项)**：包括类型检查、逻辑简化、弃用通知等。
*   **基础设施 (1项)**：增加对 Ubuntu 24.04 的 Docker 构建支持。

### 2. 关键变更点及其与项目整体方向的关系
| 关键变更点 | 与项目方向（易用、快速、廉价）的关系 |
| :--- | :--- |
| **微批次优化 (DBO) 支持通用模型** (`#37926`) | **性能 (快速)**：扩展了动态批处理优化技术的适用范围，有望提升更多模型的吞吐量和资源利用率。 |
| **调度策略增强** (`#37307`, `#20859`) | **性能与成本 (快速、廉价)**：新增基于完整输入序列长度的调度选项，有助于优化内存和计算资源分配；限制“思考令牌”可防止资源浪费，控制成本。 |
| **核心Bug修复** (Mamba状态、KV缓存、模型加载等) | **稳定性与可靠性 (易用)**：修复影响服务稳定性和正确性的底层问题，是保证生产环境可靠性的基础。 |
| **FlexAttention 支持自定义掩码** (`#37692`) | **灵活性与性能 (易用、快速)**：为高级用户提供更灵活的注意力机制定制能力，可能解锁新的优化或研究用例。 |
| **多硬件支持扩展** (XPU信息收集、CPU修复) | **可及性与成本 (廉价、易用)**：加强对Intel XPU和CPU的支持，使用户能在更广泛的硬件上部署，降低使用门槛和成本。 |
| **新增 Granite 4.0 1B 语音模型支持** (`#38019`) | **生态与易用性 (易用)**：持续扩展支持的模型库，使用户能更方便地服务最新模型，丰富应用场景。 |

### 3. 对项目的影响和潜在意义
*   **提升生产环境稳定性**：大量核心Bug修复直接增强了系统的鲁棒性，减少了服务中断或输出错误的风险。
*   **扩展性能优化边界**：微批次优化、新调度策略、注意力机制定制等更新，为在不同负载和模型下实现更高性能提供了更多工具和选项。
*   **降低部署与使用门槛**：对Ubuntu 24.04、Intel XPU的更好支持，以及文档修复，使得在不同环境和硬件上安装、配置vLLM更加顺畅。
*   **维护代码健康度**：通过Mypy类型检查和逻辑简化，提高了代码的可维护性和长期演进的可靠性。
*   **明确功能演进路径**：弃用“池化多任务支持”等功能，有助于简化代码库，引导用户使用更优的替代方案。

### 4. 值得关注的技术点
1.  **动态批处理优化 (DBO)**：此次使其适用于“通用模型”，表明该技术已趋于成熟，正成为提升推理效率的核心手段之一。
2.  **调度算法的多样化**：新增“基于完整输入序列长度(ISL)调度”和“硬限制思考令牌”，显示项目在精细化资源管理和控制方面持续深入。
3.  **对Mamba等状态空间模型(SSM)的支持**：修复Mamba状态损坏问题，印证了vLLM对超越Transformer架构的新兴模型的支持投入。
4.  **硬件抽象层的完善**：针对Intel XPU和CPU的修复与增强，体现了其向“全硬件栈”高效推理引擎发展的野心。
5.  **编译流程的改进**：多个提交涉及编译标志和日志，说明项目重视构建体验和自定义编译的稳定性。

### 5. 基于项目背景的提交影响分析
vLLM的目标是成为**面向所有人的LLM服务解决方案**。昨日的更新集体指向这一目标的多个维度：

*   **“易用”方面**：通过修复模型加载（HF Token传递）、文档错误、CPU警告信息、编译问题等，**改善了用户体验和部署流程**。支持更多硬件和操作系统也扩大了“所有人”的覆盖范围。
*   **“快速”方面**：微批次优化(DBO)的扩展、新的调度策略、FlexAttention的增强，都是**直接针对推理性能的挖潜**，致力于在各种场景下实现更低的延迟和更高的吞吐。
*   **“廉价”方面**：调度优化（如限制思考令牌）和更广泛的硬件支持（XPU/CPU），有助于用户**更高效地利用现有计算资源**，从而降低单位推理成本。

**总结**：昨日的更新是一次典型的**稳健迭代**。它没有引入颠覆性特性，而是通过**夯实基础（修复Bug）、扩展边界（支持新硬件/模型）和优化核心（调度与性能）**，全方位地巩固和推进v

## 详细提交记录

### [b73b5b0](https://github.com/vllm-project/vllm/commit/b73b5b06290c0d1439b09db71eef15fe59bc1fbb)

- **作者**: Junhao
- **时间**: 2026-03-24T21:40:08Z
- **提交信息**: Make microbatch optimization (DBO) work with general models (#37926)

Signed-off-by: Junhao Li <junhao@ubicloud.com>

### [0f0e038](https://github.com/vllm-project/vllm/commit/0f0e03890ed7edd41eb0b5e2de21447b3f70586c)

- **作者**: Michael Goin
- **时间**: 2026-03-24T21:13:08Z
- **提交信息**: [UX] Add flashinfer-cubin as CUDA default dep (#37233)

Signed-off-by: mgoin <mgoin64@gmail.com>

### [4b53740](https://github.com/vllm-project/vllm/commit/4b53740d7f3c2216be7a737d585bff37f4975d2e)

- **作者**: Woosuk Kwon
- **时间**: 2026-03-24T21:03:24Z
- **提交信息**: [MRV2] Fix for DS v3.2 (#38030)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>

### [4e824d1](https://github.com/vllm-project/vllm/commit/4e824d1c835d9b57db621297e8d9119bfc32fb2e)

- **作者**: Nick Hill
- **时间**: 2026-03-24T20:57:17Z
- **提交信息**: [Model Runner V2][Minor] Simplify PP logic (#38031)

Signed-off-by: Nick Hill <nickhill123@gmail.com>

### [0c1809c](https://github.com/vllm-project/vllm/commit/0c1809c8065f51646c9ca6ce7911831a763a5d18)

- **作者**: amey asgaonkar
- **时间**: 2026-03-24T20:34:44Z
- **提交信息**: Add Ubuntu 24.04 support for Docker builds (#35386)

Signed-off-by: aasgaonkar <aasgaonkar@nvidia.com>

### [8c47fdf](https://github.com/vllm-project/vllm/commit/8c47fdfdb17c7bab93c70722b7adf71d87deddb9)

- **作者**: liangel-02
- **时间**: 2026-03-24T20:03:24Z
- **提交信息**: [FlexAttention] allow custom mask mod (#37692)

Signed-off-by: Angel Li <liangel@meta.com>

### [54b0578](https://github.com/vllm-project/vllm/commit/54b0578adacd0413b18c0f59948dabc7533a6524)

- **作者**: Javier De Jesus
- **时间**: 2026-03-24T19:22:05Z
- **提交信息**: [Bugfix] Pass hf_token through config loading paths for gated model support (#37920)

Signed-off-by: javierdejesusda <javier.dejesusj9@gmail.com>

### [89f572d](https://github.com/vllm-project/vllm/commit/89f572dbc0bf18efaaec52b95119bf4c01330dfe)

- **作者**: Richard Zou
- **时间**: 2026-03-24T19:08:26Z
- **提交信息**: [BugFix] fix VLLM_USE_STANDALONE_COMPILE=0 (#38015)

Signed-off-by: Richard Zou <zou3519@gmail.com>

### [71a4a2f](https://github.com/vllm-project/vllm/commit/71a4a2fbd043260a0e693e909fc7d00ec23c9a5f)

- **作者**: Richard Zou
- **时间**: 2026-03-24T18:58:18Z
- **提交信息**: [BugFix] Fix order of compile logging (#38012)

Signed-off-by: Richard Zou <zou3519@gmail.com>

### [935c46d](https://github.com/vllm-project/vllm/commit/935c46dd9bad76b11c4f7392ed8140109093e7ca)

- **作者**: Nick Cao
- **时间**: 2026-03-24T18:23:41Z
- **提交信息**: [Model] Add Granite 4.0 1B speech to supported models (#38019)

Signed-off-by: Nick Cao <ncao@redhat.com>

### [057fc94](https://github.com/vllm-project/vllm/commit/057fc94cbdcfbb484d4aac5f244aee1eefe17f0e)

- **作者**: Willy Hardy
- **时间**: 2026-03-24T17:44:17Z
- **提交信息**: [Bugfix] Fix structured output crash on CPU due to pin_memory=True (#37706)

Signed-off-by: Willy Hardy <whardy@redhat.com>
Signed-off-by: Will Hardy <whardy@redhat.com>
Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>

### [b58c5f2](https://github.com/vllm-project/vllm/commit/b58c5f28aa687de58e0d314eb1d43a3e26359689)

- **作者**: Vineeta Tiwari
- **时间**: 2026-03-24T17:35:14Z
- **提交信息**: docs: fix broken offline inference paths in documentation (#37998)

Signed-off-by: Vineeta Tiwari <vineeta.tiwari2@ibm.com>
Signed-off-by: Vineeta Tiwari <vineetatiwari2000@gmail.com>
Co-authored-by: Vineeta Tiwari <vineeta.tiwari2@ibm.com>
Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>

### [c07e2ca](https://github.com/vllm-project/vllm/commit/c07e2ca6e0ace42aaeae96b5ce6b8525e592e2ae)

- **作者**: Ming Yang
- **时间**: 2026-03-24T17:29:59Z
- **提交信息**: Fix Mamba state corruption from referencing stale block table entries (#37728) (#37728) (#37728)

### [4df5fa7](https://github.com/vllm-project/vllm/commit/4df5fa74396bef3995a6192573f75d58a2976ebc)

- **作者**: Dhruv Singal
- **时间**: 2026-03-24T17:29:50Z
- **提交信息**: [Bugfix] Force continuous usage stats when CLI override is enabled (#37923)

Signed-off-by: Your Name <you@example.com>
Co-authored-by: Your Name <you@example.com>
Co-authored-by: OpenCode <noreply@openai.com>

### [a5416bc](https://github.com/vllm-project/vllm/commit/a5416bc52e5d516008388c833a8d6270e92a894c)

- **作者**: sihao_li
- **时间**: 2026-03-24T17:29:17Z
- **提交信息**: [XPU] Support Intel XPU hardware information collection in usage stats (#37964)

Signed-off-by: sihao.li <sihao.li@intel.com>

### [b3601da](https://github.com/vllm-project/vllm/commit/b3601da6e7feb2b2b522f38a8b0d95e590262b63)

- **作者**: Harry Mellor
- **时间**: 2026-03-24T17:14:01Z
- **提交信息**: [Mypy] Fix mypy for `vllm/model_executor` (except `vllm/model_executor/layers`) (#37904)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [dc78c2c](https://github.com/vllm-project/vllm/commit/dc78c2c933ac8903d7e34bff7b5161eae70595fc)

- **作者**: Dan Blanaru
- **时间**: 2026-03-24T17:01:12Z
- **提交信息**: [Core] add option to schedule requests based on full ISL (#37307)

Signed-off-by: Dan Blanaru <48605845+DanBlanaru@users.noreply.github.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [4731884](https://github.com/vllm-project/vllm/commit/4731884796d43bd8493769dbfb0e199a2a542092)

- **作者**: Sungjae Lee
- **时间**: 2026-03-24T16:53:07Z
- **提交信息**: [Feature] limit thinking tokens (hard limit) (#20859)

Signed-off-by: Sungjae Lee <33976427+llsj14@users.noreply.github.com>
Signed-off-by: Sungjae Lee <sung-jae.lee@navercorp.com>
Signed-off-by: Chauncey <chaunceyjiang@gmail.com>
Co-authored-by: Chauncey <chaunceyjiang@gmail.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [8de5261](https://github.com/vllm-project/vllm/commit/8de5261e69af81aaf7f68d420b69199653cd1882)

- **作者**: Harry Mellor
- **时间**: 2026-03-24T16:01:41Z
- **提交信息**: Update new contributor message (#37999)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [1b6cb92](https://github.com/vllm-project/vllm/commit/1b6cb920e6ebcac57154e6154578c39d4892a16c)

- **作者**: wang.yuqi
- **时间**: 2026-03-24T14:07:47Z
- **提交信息**: [Deprecate] Deprecate pooling multi task support. (#37956)

Signed-off-by: wang.yuqi <yuqi.wang@daocloud.io>
Signed-off-by: wang.yuqi <noooop@126.com>
Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>
Co-authored-by: Cyrus Leung <cyrus.tl.leung@gmail.com>

### [352b90c](https://github.com/vllm-project/vllm/commit/352b90c4a4f2af1d75cdc09fecf30a47a4ca39fb)

- **作者**: Li, Jiang
- **时间**: 2026-03-24T14:00:20Z
- **提交信息**: [Bugfix] Add replacement of _compute_slot_mapping_kernel on CPU (#37987)

Signed-off-by: jiang1.li <jiang1.li@intel.com>

### [1c0aabd](https://github.com/vllm-project/vllm/commit/1c0aabdeb0cf77019a1f89b5bed5b8eebdd5c211)

- **作者**: Sage
- **时间**: 2026-03-24T12:36:18Z
- **提交信息**: [Bugfix] Suppress spurious CPU KV cache warning in `launch render` (#37911)

Signed-off-by: Sage Ahrac <sagiahrak@gmail.com>

### [14acf42](https://github.com/vllm-project/vllm/commit/14acf429ac08b6d538ca6feb3e06b6d13895804d)

- **作者**: Ilya Markov
- **时间**: 2026-03-24T11:50:44Z
- **提交信息**: [EPLB] Remove main waits in case of slow EPLB (#36271)

Signed-off-by: ilmarkov <markovilya197@gmail.com>

### [ce57fd5](https://github.com/vllm-project/vllm/commit/ce57fd555703e2b24352fd582dbb2b687d7ba7c5)

- **作者**: Harry Mellor
- **时间**: 2026-03-24T10:20:49Z
- **提交信息**: [Docs] Fix build (#37991)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-03-25
**监控日期**: 2026-03-24
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 3740
- **最后更新**: 2026-03-24T22:14:48Z

## 提交统计

- **昨日提交总数**: 16
- **提交者数量**: 12
- **主要提交者**: Canlin Guo, Yueqian Lin, SYLAR

## AI分析总结

根据提供的README摘要和提交记录，以下是vllm-omni项目昨日更新的分析总结：

### 1. 主要更新类型
- **Bug修复**：4项（音频处理、内存泄漏、TTFP延迟、CI稳定性）
- **功能新增**：3项（语音批处理端点、标量类型支持、图像编辑API参数）
- **性能优化**：2项（统一量化框架、自定义音频分块大小）
- **CI/CD改进**：4项（测试流程优化、性能基准测试、GPU资源调整）
- **文档更新**：1项（修复文档错误）
- **代码重构**：1项（统一Torch Profiler）
- **测试增强**：2项（端到端测试、扩散模型功能测试）

### 2. 关键变更点与项目方向关系
| 变更点 | 与项目方向的关系 |
|--------|----------------|
| **统一量化框架 (#1764)** | 直接支持"cheap"目标，通过量化降低推理成本 |
| **语音批处理入口 (#1701)** | 增强"fast"特性，提升语音模型服务吞吐量 |
| **Qwen3 TTS长音频修复 (#2104)** | 完善"omni-modality"中的语音模态支持 |
| **内存泄漏修复 (#2028)** | 提升系统稳定性，确保长时间服务可靠性 |
| **自定义音频分块大小 (#1964)** | 优化多模态音频模型性能，提升处理效率 |

### 3. 对项目的影响和潜在意义
- **性能提升**：统一量化框架为后续模型优化提供基础设施
- **稳定性增强**：内存泄漏修复和CI稳定性改进提升生产环境可靠性
- **功能扩展**：语音批处理和图像编辑API增强使服务更全面
- **开发者体验**：文档修复和测试覆盖提升项目易用性
- **多模态完善**：音频、图像、语音各模态均有针对性改进

### 4. 值得关注的技术点
1. **统一量化框架**：可能引入新的量化策略，支持更多硬件和模型
2. **Torch Profiler统一**：为性能分析和优化提供标准化工具
3. **自定义chunk_size**：针对MIMO音频模型的优化，反映对特定架构的深度支持
4. **标量类型支持**：扩展AdditionalInformationEntry功能，增强数据传递能力
5. **分层扩散模型测试**：显示对复杂多模态模型的测试方法论

### 5. 基于项目背景的提交影响分析
vllm-omni定位为"Easy, fast, and cheap omni-modality model serving"，昨日提交从三个维度推进这一目标：

- **Easy方面**：
  - 文档修复提升用户体验
  - API参数扩展（图像编辑的layers/resolution）提供更细粒度控制
  - 端到端测试确保功能稳定性

- **Fast方面**：
  - 语音批处理显著提升吞吐量
  - TTFP延迟优化改善响应速度
  - 性能CI监控确保速度指标

- **Cheap方面**：
  - 统一量化框架直接降低计算成本
  - 内存泄漏修复减少资源浪费
  - GPU资源优化提高硬件利用率

- **Omni-modality方面**：
  - 覆盖语音（TTS、音频处理）、视觉（图像编辑）、多模态（Qwen-Image）全栈改进
  - 各模态均有性能优化和bug修复
  - 测试覆盖扩展到复杂扩散模型

**整体趋势**：项目正从基础功能建设转向深度优化和性能提升阶段，同时加强多模态能力的完整性和稳定性。

## 详细提交记录

### [44770f9](https://github.com/vllm-project/vllm-omni/commit/44770f9f200b7121530c8a578968c738acd75dc7)

- **作者**: Sy03
- **时间**: 2026-03-24T20:02:52Z
- **提交信息**: [Fix] Qwen3 TTS audio handling for long ref_audio (#2104)

Signed-off-by: Sy03 <1370724210@qq.com>
Signed-off-by: Sy0307 <1370724210@qq.com>

### [69652a2](https://github.com/vllm-project/vllm-omni/commit/69652a298392fe20a37c4c289e39d3296cbb6337)

- **作者**: Du Bin
- **时间**: 2026-03-24T14:52:31Z
- **提交信息**: [Bugfix] Fix memory leak: missing chunk_transfer_adapter.cleanup() in OmniARScheduler (#2028)

Signed-off-by: dubin555 <dubin555@gmail.com>
Signed-off-by: OSS Scout <scout@oss-scout.local>

### [e7e05a5](https://github.com/vllm-project/vllm-omni/commit/e7e05a55cf09772378cc24b0df3127a4294d97ba)

- **作者**: dsinghvi
- **时间**: 2026-03-24T14:52:01Z
- **提交信息**: [Feature] Speech batch entrypoint (#1701)

Signed-off-by: dsinghvi <divyanshsinghvi@gmail.com>
Signed-off-by: Divyansh Singhvi <divyanshsinghvi@gmail.com>

### [7f11204](https://github.com/vllm-project/vllm-omni/commit/7f112041da3be807eac6ffd08c8ff72a04232a75)

- **作者**: Yueqian Lin
- **时间**: 2026-03-24T14:47:09Z
- **提交信息**: [Bugfix] Fix high TTFP for Base task in Gradio TTS demo (#2116)

Signed-off-by: linyueqian <linyueqian@outlook.com>

### [7bcd43f](https://github.com/vllm-project/vllm-omni/commit/7bcd43f456c37f3ce3dcdec8fd474a0de2eaa06f)

- **作者**: Canlin Guo
- **时间**: 2026-03-24T14:39:23Z
- **提交信息**: [Docs][skip ci] Fix omni and tts docs (#2130)

Signed-off-by: gcanlin <canlinguosdu@gmail.com>

### [47ba887](https://github.com/vllm-project/vllm-omni/commit/47ba887b93d62446b4c9ab9709eecbe63071e356)

- **作者**: Nick Cao
- **时间**: 2026-03-24T14:29:38Z
- **提交信息**: [Feat] Support scalar types in AdditionalInformationEntry (#2105)

Signed-off-by: Nick Cao <ncao@redhat.com>

### [c7c1c3b](https://github.com/vllm-project/vllm-omni/commit/c7c1c3b04a0718d00f410c8cdaa717c8e73493d5)

- **作者**: Didan Deng
- **时间**: 2026-03-24T11:25:57Z
- **提交信息**: [Fix CI] Reduce num gpus to prevent ci failure (#2131)

Signed-off-by: Didan Deng <33117903+wtomin@users.noreply.github.com>

### [6b93459](https://github.com/vllm-project/vllm-omni/commit/6b9345982620f4ed88459fd6b2f166a1345d98fb)

- **作者**: SYLAR
- **时间**: 2026-03-24T10:56:55Z
- **提交信息**: [Core] Unified quantization framework (#1764)

### [2a63031](https://github.com/vllm-project/vllm-omni/commit/2a630313ce031852798ff601ac99376d861fd8c5)

- **作者**: Alicia
- **时间**: 2026-03-24T09:58:24Z
- **提交信息**: [CI] Trigger nightly diffusion benchmark collects and html generates. (#1995)

Signed-off-by: Alicia <115451386+congw729@users.noreply.github.com>

### [8619321](https://github.com/vllm-project/vllm-omni/commit/8619321b908321fdad9b03aaa9c1b27294c262c3)

- **作者**: Baoyuan Qi
- **时间**: 2026-03-24T09:14:50Z
- **提交信息**: [Enhancement] Custom chunk_size for mimo-audio model (#1964)

Signed-off-by: 齐保元 <qibaoyuan@xiaomi.com>

### [f8777d8](https://github.com/vllm-project/vllm-omni/commit/f8777d85bc69adf924eae0f308a8a159079f1496)

- **作者**: Alicia
- **时间**: 2026-03-24T08:58:22Z
- **提交信息**: [CI] Add conditions for L3 (tests after merging) and L4 (tests for nightly). (#1514)

Signed-off-by: Alicia <115451386+congw729@users.noreply.github.com>

### [c392257](https://github.com/vllm-project/vllm-omni/commit/c39225724df39ea0bdf7c3ec21295a70d18c1092)

- **作者**: Didan Deng
- **时间**: 2026-03-24T08:52:48Z
- **提交信息**: [Perf] Qwen-Image Nightly Performance CI Improvement (#2111)

Signed-off-by: Didan Deng <33117903+wtomin@users.noreply.github.com>

### [5c14757](https://github.com/vllm-project/vllm-omni/commit/5c14757ef0f157fa828b810273f066e13213dc36)

- **作者**: knlnguyen1802
- **时间**: 2026-03-24T07:49:11Z
- **提交信息**: [CI] [RL]: Add e2e test for custom pipeline  (#2005)

Signed-off-by: knlnguyen1802 <knlnguyen1802@gmail.com>
Signed-off-by: Samit <285365963@qq.com>
Co-authored-by: Samit <285365963@qq.com>
Co-authored-by: SYLAR <125541396+lishunyang12@users.noreply.github.com>

### [fb9f20a](https://github.com/vllm-project/vllm-omni/commit/fb9f20a9210cd6f6aa9b111e70e51ed1ce19b721)

- **作者**: Canlin Guo
- **时间**: 2026-03-24T07:47:41Z
- **提交信息**: [API] Add layers and resolution parameters to /v1/images/edits endpoint (#2053)

Signed-off-by: gcanlin <canlinguosdu@gmail.com>

### [7217557](https://github.com/vllm-project/vllm-omni/commit/7217557950320d825b5c158ea6a2469166e02a4b)

- **作者**: Canlin Guo
- **时间**: 2026-03-24T07:25:52Z
- **提交信息**: [Refactor] Unify torch profiler for omni and diffusion models (#2099)

Signed-off-by: gcanlin <canlinguosdu@gmail.com>
Signed-off-by: Samit <285365963@qq.com>
Co-authored-by: Samit <285365963@qq.com>
Co-authored-by: lishunyang lishunyang12@163.com

### [93f1878](https://github.com/vllm-project/vllm-omni/commit/93f1878229f7edcc051b49c9ed4df3baa63668eb)

- **作者**: John Liu BUAA
- **时间**: 2026-03-24T07:20:35Z
- **提交信息**: [Test] L4 complete diffusion feature test for Qwen-Image-Layered models (#2085)

Signed-off-by: John Liu BUAA <liukecheng97@gmail.com>

---
