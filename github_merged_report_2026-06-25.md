# GitHub Stars 合并报告 - 2026-06-25

**合并日期**: 2026-06-26
**监控日期**: 2026-06-25
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


**报告日期**: 2026-06-26
**监控日期**: 2026-06-25
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2046
- **最后更新**: 2026-06-25T22:54:55Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 3
- **主要提交者**: Albert Zhang, Zhichao Liu, Crystal-jiang

## AI分析总结

### 昨日更新要点总结

1. **主要更新类型**  
   - **功能新增**：添加数据管道 dry-run 脚本（`tasks/data_sim.py`）  
   - **测试增强**：为 LoRA 保存/加载添加 NPU 单元测试用例  
   - **Bug 修复**：修复 ops 默认配置自动解析为 NPU 不兼容的问题

2. **关键变更点与项目方向的关系**  
   - **数据管道 dry-run 脚本**：支持在不实际运行训练的前提下模拟数据流，便于调试多模态数据预处理与加载逻辑，提升开发效率。这与项目“多模态任意模态”的背景直接相关，确保数据管道的正确性。  
   - **LoRA 单元测试（NPU）**：LoRA 是高效微调多模态模型的关键技术；在 NPU 上验证其保存/加载能力，保障分布式微调场景下的稳定性，契合“模型中心配方”中的灵活微调需求。  
   - **默认配置 NPU 兼容修复**：自动解析操作默认值时强制对齐 NPU 硬件，避免因配置错误导致训练失败，体现了项目对多种硬件（特别是 NPU）的适配承诺。

3. **对项目的影响与潜在意义**  
   - **提升易用性**：dry-run 脚本简化了数据管道的调试流程，降低新手使用门槛。  
   - **增强可靠性**：LoRA 测试覆盖 NPU 环境，减少微调过程中的隐藏 bug。  
   - **强化硬件兼容**：默认配置自动适配 NPU，使得分布式训练配方在不同硬件上开箱即用，为后续扩展更多硬件类型（如 GPU、TPU）奠定基础。

4. **值得关注的技术点**  
   - `data_sim.py` 的实现方式：可能支持多模态数据混合模拟、分布式环境下的数据分片验证。  
   - LoRA 在 NPU 上的序列化/反序列化细节：需处理权重合并、适配器参数与基座模型的交互。  
   - 配置自动解析逻辑：如何根据硬件类型选择默认参数（如混合精度、通信后端），避免硬编码。

5. **结合项目背景的发展影响**  
   - **加速多模态模型迭代**：dry-run 帮助开发人员快速验证多模态数据流水线，配合项目“任意模态”目标，减少试错成本。  
   - **推动高效微调生态**：LoRA 测试完善了 NPU 上的微调支持，使得项目所倡导的“配方库”能覆盖更多微调策略。  
   - **夯实分布式训练基础**：配置兼容性修复属于底层基础设施优化，直接影响大规模训练作业的稳定性，为“模型中心分布式配方”提供更可靠的运行环境。

## 详细提交记录

### [7c38f42](https://github.com/ByteDance-Seed/VeOmni/commit/7c38f42504282987f0555b3c7210fb5b1226db6e)

- **作者**: Zhichao Liu
- **时间**: 2026-06-25T22:54:50Z
- **提交信息**: [data] feat: add data-pipeline dry-run script (tasks/data_sim.py) (#865)

Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [536ff4a](https://github.com/ByteDance-Seed/VeOmni/commit/536ff4aa9ef7ab7d11a0685630ff4283f867f20f)

- **作者**: Albert Zhang
- **时间**: 2026-06-25T10:49:03Z
- **提交信息**: [ci, lora] test: add LoRA save/load case to NPU unit tests (#851)

### [7b91cec](https://github.com/ByteDance-Seed/VeOmni/commit/7b91cec4c08d5cd944e3418a2ed48b40adb12a51)

- **作者**: Crystal-jiang
- **时间**: 2026-06-25T07:17:50Z
- **提交信息**: [config] fix: auto-resolve ops defaults to NPU-compatible (#863)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-06-26
**监控日期**: 2026-06-25
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2444
- **最后更新**: 2026-06-25T13:47:29Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 2
- **主要提交者**: Yang Yong (雍洋), Shiqiao Gu (谷石桥)

## AI分析总结

根据昨日提交记录，结合项目背景（LightX2V 是一个轻量级视频生成推理框架），总结如下：

---

### 1. 主要更新类型
- **功能新增**（3 个提交全部为新增功能，无 Bug 修复/性能优化/文档更新/重构）

### 2. 关键变更点及其与项目整体方向的关系
- **新增 `lightx2v_ros` 模块**（#1174）  
  引入 ROS（Robot Operating System）支持。这将使框架能够与机器人/自动驾驶等实时系统集成，增强在工业级场景下的部署能力。
- **支持 cosmos3-super I2V 模型**（#1184）  
  加入图生视频（Image-to-Video）模型推理能力，扩展了视频生成的任务类型。
- **支持 cosmos3-super T2I 模型**（#1183）  
  增加文本到图像（Text-to-Image）模型支持。虽然项目主打视频生成，但 T2I 可作为视频生成的中间步骤或辅助功能，丰富了框架的模型生态。

这些更新均围绕 **"轻量视频生成推理"** 的核心方向，一方面通过模型支持拓宽适用场景（从视频到图像、从文生视频到图生视频），另一方面通过 ROS 接口推动在机器人/自动化等实际系统中的应用。

### 3. 对项目的影响和潜在意义
- **扩大模型生态**：cosmos3-super 系列模型（T2I + I2V）的接入，使框架可服务更多用户（如图像生成、图生视频创作者）。
- **拓展应用领域**：ROS 支持使得 LightX2V 能从纯研究工具走向机器人仿真、自动驾驶模拟、工业视觉等场景，提升项目影响力。
- **降低集成门槛**：ROS 接口标准化，让已有 ROS 架构的系统能快速集成视频生成能力。

### 4. 值得关注的技术点
- **ROS 集成实现**：需关注如何封装推理调用（sync/async）、消息传递格式（例如图像/视频 topic）以及推理延迟对实时性的影响。
- **cosmos3-super 模型优化**：该模型可能为大型预训练模型，需关注其在 LightX2V 框架中的推理效率、显存占用及是否支持量化/蒸馏等轻量化策略。

### 5. 基于 README 背景的项目发展影响
- 项目定位为 **轻量视频生成推理框架**，原本可能仅支持有限模型和纯推理场景。  
- 通过添加 **ROS 接口**，项目开始向 **系统集成** 方向演进，从独立工具变为可嵌入外部系统的组件，符合业界对 AI 模型“落地”的需求。  
- 同时，**模型支持的扩展**（从单一任务到多任务）使框架更通用，能覆盖文生图、图生视频等多种生成需求，增强竞争力。  
- 整体来看，这些提交标志着项目正从一个学术原型向 **生产级视频生成基础设施** 迈进。

## 详细提交记录

### [c010071](https://github.com/ModelTC/LightX2V/commit/c01007172c38fe031ba8a44b58c923548e87da60)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-06-25T11:22:23Z
- **提交信息**: Add lightx2v_ros (#1174)

### [1566cd6](https://github.com/ModelTC/LightX2V/commit/1566cd6714dd6505ac409d729390aeab9b6991f5)

- **作者**: Shiqiao Gu (谷石桥)
- **时间**: 2026-06-25T11:13:05Z
- **提交信息**: Supports the cosmos3-super i2v model. (#1184)

### [78cf297](https://github.com/ModelTC/LightX2V/commit/78cf2979c7d179a75cd0aa74c84413f0b75289e8)

- **作者**: Shiqiao Gu (谷石桥)
- **时间**: 2026-06-25T09:15:21Z
- **提交信息**: Supports the cosmos3-super t2i model. (#1183)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-06-26
**监控日期**: 2026-06-25
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2147
- **最后更新**: 2026-06-24T14:17:49Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-06-26
**监控日期**: 2026-06-25
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5858
- **最后更新**: 2026-06-25T22:49:31Z

## 提交统计

- **昨日提交总数**: 7
- **提交者数量**: 7
- **主要提交者**: kangbintNV, alel, Lee Nau

## AI分析总结

根据您提供的 `flashinfer-ai/flashinfer` 仓库的 GitHub 提交记录，结合项目背景（高性能 GPU 推理内核库），昨日更新要点总结如下：

---

### 1. 主要更新类型

| 类型 | 提交数 | 说明 |
|------|--------|------|
| **功能新增** | 2 | cuTile 分组 MXFP8 量化 (#3657)、SM100 支持更多 state dtype (#3715) |
| **Bug 修复** | 1 | Mamba SSDCombined 对 SM120 报出清晰错误 (#3668) |
| **性能优化** | 1 | MoE finalize 性能改进（来自 TRTLLM）(#3564) |
| **文档更新** | 1 | 为 BF16×FP4 GEMM 补充 API 文档条目 (#3710) |
| **测试重构** | 1 | 拆分长耗时 MoE 测试文件以规避 CI 超时 (#3635) |
| **API 兼容性改进** | 1 | MLA decode 的 workspace 同时接受 `uint8` (#3599) |

---

### 2. 关键变更点及其与项目方向的关系

| 提交 | 变更摘要 | 与项目方向的关系 |
|------|----------|------------------|
| #3657 | `mxfp8_grouped_quantize`：Blackwell (SM100+) 上的分组 MXFP8 量化 | 扩展高精度推理支持，Mo

## 详细提交记录

### [dc83d0d](https://github.com/flashinfer-ai/flashinfer/commit/dc83d0d391e973109be924bbcf726441af754df4)

- **作者**: kangbintNV
- **时间**: 2026-06-25T22:49:26Z
- **提交信息**: docs(gemm): add missing .rst entries for mm_bf16_fp4 and prepare_bf16_fp4_weights (#3710)

## Summary

- and were introduced in #3597 (BF16×FP4 GEMM with cuDNN and CuTe-DSL
backends for SM120/121, W4A16 workloads)
- Both are decorated with but were absent from , causing API-coverage
alerts
- Adds a new **BF16×FP4 GEMM (W4A16)** section in listing both functions
under

## Changes

- : new section inserted after *FP4 GEMM* with  and 

## Test plan

- [ ] Verify  picks up both symbols without error
- [ ] Confirm API-coverage alert clears on next daily run

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Documentation**
* Added a new API documentation subsection for **BF16×FP4 GEMM
(W4A16)**, including generated reference pages for the weight
preparation and matrix multiplication operations.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: cindyz <cindyz@nvidia.com>
Co-authored-by: Claude Sonnet 4.6 <noreply@anthropic.com>
Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>

### [95cb947](https://github.com/flashinfer-ai/flashinfer/commit/95cb94741878c816742265515d20fdca01b5f923)

- **作者**: WEI CHENG CHIU
- **时间**: 2026-06-25T22:39:46Z
- **提交信息**: fix(mamba): reject SM120/SM121 in SSDCombined with a clear error (#3668)

## 📌 Description

`SSDCombined.__init__` only rejected `major < 10`, so
consumer/workstation Blackwell (SM120/SM121) passed the guard and
reached the SSD CuTe-DSL kernel, which uses tcgen05 MMA (`MmaF16BF16Op`)
— available only on datacenter Blackwell (SM100/SM103/SM110). On an RTX
PRO 6000 (SM120) this surfaces as a cryptic cute-dsl error at
construction:

```
cutlass.cute.nvgpu.common.OpError: expects arch to be one of
[sm_100a, sm_100f, sm_101a, sm_101f, sm_103a, sm_103f, sm_110a, sm_110f], but got sm_120a
   Error Code: MmaF16BF16Op error
   💡 Suggestions: Ensure env CUTE_DSL_ARCH matches your GPU architecture
```

The `CUTE_DSL_ARCH` hint is misleading — it's a hardware capability gap
(no tcgen05 on consumer Blackwell), not an env issue.

This tightens the guard to `major not in (10, 11)` (the op's own
supported arch set) and corrects the message to name the actual
supported range (SM100–SM110, tcgen05). **No SM120 SSD kernel exists, so
this is a clean-error change, not an enablement change.**

## 🔍 Related Issues

None — found while auditing SM120 dispatch on an RTX PRO 6000.

## 🧪 Tests

Verified on an RTX PRO 6000 Blackwell (SM120, CUDA 13.0) with
`SSDCombined(chunk_size=128, nheads=8, headdim=64, dstate=128,
ngroups=8)`:

- **Before:** `OpError: ... but got sm_120a (MmaF16BF16Op error)`
(cryptic, deep in cute-dsl).
- **After:** `ValueError: SSDCombined requires SM100-SM110 (tcgen05):
Blackwell datacenter GPUs (SM100/SM103/SM110). Got SM120.`

`tests/mamba/test_chunk_scan_combined.py` is `skipif not
is_sm100a_supported`, so SM100 behavior is unchanged. `pre-commit run
--files` passes (ruff check, ruff format, mypy, codespell).

## Reviewer Notes

Supported-arch set (majors 10, 11) is taken directly from the tcgen05
`MmaF16BF16Op` error's own arch list (`sm_100/101/103/110`). Happy to
add a negative-path unit test (mocking `get_compute_capability`) if
preferred.

> 🤖 AI-assisted: investigated and authored with Claude Code, validated
on SM120 hardware.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved GPU compatibility detection with more specific hardware
requirement checks and clearer error messaging for unsupported devices.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: WEI CHENG CHIU <waynehacking8@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [22ad420](https://github.com/flashinfer-ai/flashinfer/commit/22ad42062922b2f9c780eb8b013197f5b4df0fb7)

- **作者**: alel
- **时间**: 2026-06-25T22:38:11Z
- **提交信息**: perf(moe): Enhance CuteDSL NVF4 MOE Perf (#3564)

## 📌 Description

Cherry pick perf optimization changes from TRTLLM PR
https://github.com/NVIDIA/TensorRT-LLM/pull/15092.

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
* Improved grouped GEMM/MoE finalize behavior by refining epilogue
synchronization and accumulator consumption semantics, improving output
stability.
* Enhanced handling of padded/invalid rows and per-row scaling metadata
to reduce incorrect results in edge cases.

* **Performance**
* Improved finalize execution efficiency with dedicated metadata staging
and streamlined per-row scaling in the output pipeline.
* Updated kernel tactic validation to correctly respect the runtime
dtype of final scaling values.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Yuhan Li <51736452+liyuhannnnn@users.noreply.github.com>
Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [378457c](https://github.com/flashinfer-ai/flashinfer/commit/378457c76d2da418395e83bac11524f9ecd626a9)

- **作者**: feih-nv
- **时间**: 2026-06-25T20:35:05Z
- **提交信息**: tests: split test_trtllm_gen_fused_moe.py into shards (#3635)

## Summary

Split the long-running TRT-LLM Gen fused MoE test into smaller shards to
avoid the 2h per-file CI timeout.
Changes:
- Move shared helpers/fixtures into
`tests/moe/trtllm_gen_fused_moe_utils.py`.
- Split `test_renormalize_routing` by quant family (as it dominates
runtime):
  - `test_trtllm_gen_fused_moe_routing_renormalize_fp4.py`
  - `test_trtllm_gen_fused_moe_routing_renormalize_fp8.py`
  - `test_trtllm_gen_fused_moe_routing_renormalize_bf16.py`
- Move all the remaining tests into
`test_trtllm_gen_fused_moe_other.py`, preserving original order.

## Validation
Local timing data:
- `test_trtllm_gen_fused_moe_routing_renormalize_fp4.py`: **228 passed,
6684 skipped in 3075.27s (0:51:15)**
- `test_trtllm_gen_fused_moe_routing_renormalize_fp8.py`: **1020 passed,
5892 skipped in 3384.57s (0:56:24)**
- `test_trtllm_gen_fused_moe_routing_renormalize_bf16.py`: **150 passed,
4458 skipped in 4214.70s (1:10:14)**
- `test_trtllm_gen_fused_moe_other.py`: **450 passed, 6958 skipped, 1
warning in 3954.68s (1:05:54)**

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

### [bf534fc](https://github.com/flashinfer-ai/flashinfer/commit/bf534fcb7a50fd9f7388db3fccf31aea699ceb64)

- **作者**: Lee Nau
- **时间**: 2026-06-25T20:34:38Z
- **提交信息**: Accept uint8 workspaces in CUTE DSL MLA decode (#3599)

<!-- .github/pull_request_template.md -->

## 📌 Description

This updates CUTE DSL MLA decode to accept `torch.uint8` workspace
buffers in addition to the existing `torch.int8` buffers.

The workspace is byte storage; the CUTE kernel ABI still expects an
`int8` tensor, so `uint8` buffers are validated and reinterpreted as
`int8` with a zero-copy view before launch. This avoids breaking callers
that follow FlashInfer’s common `uint8` workspace convention.

### Changes

- Add shared `_as_cute_dsl_workspace_i8` helper for CUTE DSL workspace
validation and normalization.
- Apply it to both monolithic and modular CUTE DSL MLA decode paths.
- Preserve the internal `cutlass.Int8` kernel signature.
- Add explicit validation for dtype and contiguity.

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

* **Improvements**
* MLA decode now accepts workspace buffers in both int8 and uint8
formats for greater flexibility.
* User-provided workspace buffers are handled transparently (no manual
dtype coercion required).
* Enhanced validation checks with clearer error messages when provided
workspace capacity is insufficient.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [be55e2f](https://github.com/flashinfer-ai/flashinfer/commit/be55e2f555605028d9d2529314e438eaf890a656)

- **作者**: Philipp Hack
- **时间**: 2026-06-25T19:24:09Z
- **提交信息**: feat: cuTile Grouped MXFP8 Quantization (#3657)

## 📌 Description

Adds `mxfp8_grouped_quantize`, a masked grouped MXFP8 quantizer for the
MoE activation path. It quantizes a `[B, M, K]` batch to FP8 E4M3 with
UE8M0 block scales and emits the standard 128×4 swizzled scale-factor
layout consumed by a Blackwell masked grouped GEMM.

The cuTile kernel lives under `flashinfer/quantization/kernels/cutile/`,
matching the existing cuTile GEMM backends (#3426). Availability
detection is hoisted into a shared `flashinfer/cutile/` package
(`is_cuda_tile_available()`), and the CuTe-DSL quantization kernels in
`quantization/kernels/__init__.py` are now imported lazily so this path
does not pull in `nvidia-cutlass-dsl`.

Also adds an `mxfp8_grouped_quantize` `TraceTemplate` +
reference-correctness test, public exports, and a
`docs/api/quantization.rst` entry. Requires SM100+ (Blackwell).

## 🔍 Related Issues

N/A

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

Local (all passed): `pre-commit run --all-files`; `pytest
tests/utils/test_fp8_quantize.py -k grouped`; `pytest tests/trace/ -k
grouped` (SM100 + cuda.tile).

New coverage: exact per-group values + unswizzled scales; 128×4 GEMM
layout/stride contract; empty experts (`mask=0`); CUDA-graph
capture/replay; fake/meta op; dequantized round-trip reference test.

## Reviewer Notes

- The trace template intentionally has no `reference`: a plain-layout
reference is not comparable to the swizzled/permuted output, so
correctness is verified by a dequantized round-trip test rather than an
embedded oracle.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added grouped MXFP8 quantization via `mxfp8_grouped_quantize` exposed
at the package top level (SM100+ required; `K` must be divisible by 32).

* **Documentation**
* Extended quantization API docs with the new grouped quantization
function, backend notes, and input/shape constraints.

* **Tests**
* Added grouped MXFP8 quantization coverage, including reference
correctness, trace generation/fixtures, CUDA graph capture, empty-group
handling, concurrency, and output scale/layout validation.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [25dd814](https://github.com/flashinfer-ai/flashinfer/commit/25dd814e03791e370f96c3148242f0dc8de504ac)

- **作者**: Observer007
- **时间**: 2026-06-25T08:03:00Z
- **提交信息**: [GDN] sm100: support more state dtype (#3715)

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
* Expanded support for additional state tensor dtypes, including float8
formats on supported hardware.
* State checkpoint handling now accepts a wider range of dtypes on newer
GPU architectures.

* **Bug Fixes**
* Improved state loading and writing behavior for mixed dtype scenarios,
helping preserve correct results across precision formats.
* Updated validation messages to better reflect the supported dtype
options.

* **Documentation**
* Updated public guidance to match the newly supported state dtype
combinations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-06-26
**监控日期**: 2026-06-25
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3761
- **最后更新**: 2026-06-25T14:47:46Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: William Lin, Kevin Lin

## AI分析总结

根据您提供的提交记录和项目背景，昨日（假设为2025年某日）的更新属于**Bug修复**类别，无新增功能或性能优化。具体分析如下：

### 1. 主要更新类型
- **Bug修复**（2个PR： #1495, #1493）
- 无功能新增、性能优化、文档更新或重构。

### 2. 关键变更点及其与项目整体方向的关系
- **提交1 (`0356205`)**: 将 `fastvideo kernel` 版本回退至 `0.2.6`（PR #1495）。  
  - **关联背景**: FastVideo 项目依赖自定义 CUDA kernel（如 `fastvideo`）以加速视频模型的训练/推理。回退版本可能源于 `0.2.7` 或更高版本引入了稳定性或正确性问题（例如，与量化或注意力计算相关的 bug）。  
  - **项目方向**: 保持核心加速组件的稳定可靠，优先于版本迭代的功能性提升。

- **提交2 (`719a187`)**: 修正 `scaled_fp4_quant_trans_kernel` 中错误的 “V-行排列”（V-row permutation）。  
  - **关联背景**: 该 kernel 用于 4-bit 量化（FP4）的矩阵转置或变换，常见于低精度训练/推理（如量化加速）。错误的行排列会导致量化后矩阵运算结果错误，影响模型精度或生成质量。  
  - **项目方向**: 确保低精度加速的正确性，因为 FastVideo 可能依赖 FP4/FP8 等量化技术来降低显存占用、提升吞吐量。

### 3. 对项目的影响和潜在意义
- **直接效果**: 修复了两个潜在的 bug，避免了因 kernel 版本不兼容或量化逻辑错误导致的程序崩溃、显存异常或生成结果劣化。  
- **潜在意义**:  
  - 维护了用户在使用 FastVideo 进行大规模视频生成（如 CogVideo、CogVideoX 等模型）时的可靠性。  
  - 为后续加入更激进的性能优化（如更高版本的 kernel、新的量化方案）奠定了基础——必须先确保当前正确性。

### 4. 值得关注的技术点
- **快速回退策略**: 团队选择回退 kernel 版本而非修补新版本中的 bug，表明他们更注重短期稳定性，可能因为新版本改动较大或影响面广。  
- **量化 kernel 的正确性验证**: `scaled_fp4_quant_trans_kernel` 中的行排列错误提示开发者在手写 CUDA 核函数时，索引计算（permutation）是易错点，尤其是涉及多维张量转置时。  
- **与开源生态的依赖关系**: `fastvideo` kernel 版本管理可能涉及外部依赖（如 `flash-attention`、`triton` 等），回退到 `0.2.6` 可能意味着刻意与某个稳定版本的底层库对齐。

### 5. 基于 README 的项目背景，这些提交如何影响项目发展
- README 显示 FastVideo 致力于提供**快速**且**易用**的视频生成解决方案（支持快速推理、训练，并附有文档与社区讨论）。  
- 这两个 bugfix 直接提升了项目的**健壮性**和**用户信任度**：  
  - 回退 kernel 版本避免新版本中未修复的 bug 影响用户实验；  
  - 修复量化 kernel 确保 4-bit 推理/训练结果可靠（这是视频模型落地中降低显存的关键技术）。  
- **对发展路径的影响**: 短期而言，项目聚焦于“稳定当前可用的加速功能”，而非引入新特性。这符合开源项目初期“先稳定再优化”的常见策略，也为社区用户提供了明确信号：当前代码是经过验证的。后续的版本更新（如 kernel 升级）可能需要更充分的测试。

**总结**: 昨日更新是典型的“稳定化”提交——通过回退版本和修复量化 kernel 错误，消除了两个潜在的正确性或兼容性风险，保障了 FastVideo 作为视频加速工具的可靠性。对于用户的直接感受是：使用当前版本（基于 `0.2.6` kernel）进行低精度训练/推理将更稳定。

## 详细提交记录

### [0356205](https://github.com/hao-ai-lab/FastVideo/commit/0356205b84521223afc34b8423225d9888ab0a14)

- **作者**: William Lin
- **时间**: 2026-06-25T10:52:43Z
- **提交信息**: [bugfix] revert fastvideo kernel version to 0.2.6 (#1495)

### [719a187](https://github.com/hao-ai-lab/FastVideo/commit/719a1879bdc01f806a70cafb4c9ce5a5837bcbf8)

- **作者**: Kevin Lin
- **时间**: 2026-06-25T10:05:12Z
- **提交信息**: [bugfix] Remove incorrect V-row permutation in scaled_fp4_quant_trans_kernel (#1493)

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-06-26
**监控日期**: 2026-06-25
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 33933
- **最后更新**: 2026-06-25T20:08:22Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Hz_Zhang, Atharva Joshi

## AI分析总结

### 主要更新类型
- **Bug修复**：修复多GPU环境下VAE编码的跨设备错误（Cosmos 3模型）
- **功能新增**：为SkyReelsV2和ChronoEdit模型添加`from_single_file`支持（单文件加载）

### 关键变更点及其与项目整体方向的关系
1. **多GPU VAE修复**：在`device_map="balanced"`分片部署时，修复VAE`encode`过程中均值/逆标准差缓冲区被固定到错误设备的问题。  
   *与项目方向关联*：diffusers致力于支持大规模分布式训练/推理，此修复提升了多卡场景的稳定性，符合主流生产环境需求。

2. **单文件加载扩展**：SkyReelsV2和ChronoEdit（均基于Wan架构）复用`convert_wan_transformer_to_diffusers`函数，使社区导出的GGUF文件可直接加载。  
   *与项目方向关联*：促进开源生态兼容性，降低用户使用自定义/第三方模型的门槛，与diffusers长期“易于集成”的定位一致。

### 对项目的影响和潜在意义
- **稳定性提升**：多GPU VAE修复消除了偶发性的`RuntimeError`，让Cosmos 3等模型在分片场景下正常工作，降低用户排查成本。
- **生态扩展**：单文件支持让SkyReelsV2和ChronoEdit等新兴模型更容易被社区采用，有望吸引更多GPU-constrained用户（GGUF轻量格式）参与贡献。
- **维护效率**：复用已有的Wan转换代码，避免了冗余逻辑，保持核心函数库的简洁性。

### 值得关注的技术点
- **设备管理的精细控制**：修复中先计算`raw_mu`再固定缓冲区到其设备，体现了对`torch`张量设备赋值的正确用法，可作为跨设备操作的模板。
- **函数复用模式**：`convert_wan_transformer_to_diffusers`作为Wan系列模型的统一转换入口，体现出对“架构共享”场景的抽象能力，降低后续添加同类模型的工作量。
- **社区格式兼容**：`from_single_file`支持GGUF（一种轻量序列化格式），表明diffusers积极拥抱社区格式，而非仅限自家标准。

### 基于README背景的项目发展影响
- README虽仅展示许可证，但diffusers本质是一个**开放、模块化、生产就绪的扩散模型库**。这两项更新分别强化了其**生产可靠性**（多GPU修复）和**社区友好性**（单文件加载），属于典型的增量进步。
- 随着Cosmos、Wan等非Stable Diffusion系列模型涌现，diffusers通过及时修复和扩展支持，维持了“多模型统一框架”的核心竞争力，避免了碎片化。长期看，此类维护将巩固其作为扩散模型生态基石的定位。

## 详细提交记录

### [bd2c919](https://github.com/huggingface/diffusers/commit/bd2c91958881b777260eedb1c3d61d01c03e800f)

- **作者**: Atharva Joshi
- **时间**: 2026-06-25T19:03:58Z
- **提交信息**: multi-GPU VAE Fix for Cosmos 3 (#13924)

fix(cosmos3): pin VAE latent norm buffers to encode output device

Under sharded placement (device_map="balanced"), vae.encode() runs on the
VAE's own device while the mean/inv_std buffers were pinned to x.device,
causing a cross-device RuntimeError. Compute raw_mu first, then pin the
normalization buffers to its device so all tensors share one device.

Co-authored-by: Atharva Joshi <atjoshi@smc521ge-0036.ipp2a2.colossus.nvidia.com>
Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

### [577b28f](https://github.com/huggingface/diffusers/commit/577b28f8f5d30eabdd357d74944cd76568292faf)

- **作者**: Hz_Zhang
- **时间**: 2026-06-25T14:15:25Z
- **提交信息**: Add from_single_file support for SkyReelsV2 and ChronoEdit transformers (#13946)

SkyReels-V2 and ChronoEdit are both built on Wan, and their transformers have
the same keys as WanTransformer3DModel, so they reuse
convert_wan_transformer_to_diffusers (like WanVACE / WanAnimate). This lets the
community GGUF builds load directly.

Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-06-26
**监控日期**: 2026-06-25
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 418
- **最后更新**: 2026-06-25T11:30:41Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-06-26
**监控日期**: 2026-06-25
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12632
- **最后更新**: 2026-06-25T19:04:10Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: kelseyee

## AI分析总结

根据提供的提交记录和项目背景，总结如下：

### 1. 主要更新类型
- **文档更新/法律合规**：添加了 Krea2 的许可证文件。

### 2. 关键变更点及其与项目整体方向的关系
- 提交内容：`add krea2 liscense (#1511)`，在仓库中新增了与“Krea2”相关的许可证文件（可能是 `LICENSE` 或 `LICENSE-Krea2`）。
- 与项目方向的关系：DiffSynth-Studio 是一个面向视频/图像合成的开源工具，可能集成了或依赖了名为“Krea2”的第三方模型、代码库或资源。添加许可证是遵守开源协议、明确使用条款的必要步骤，确保项目合规性，同时便于用户了解衍生作品的法律限制。这符合项目作为开源社区主导软件时对知识产权管理的重视。

### 3. 对项目的影响和潜在意义
- **直接影响**：填补了之前可能缺失的许可证信息，避免潜在的法律风险。
- **潜在意义**：
  - 表明项目可能引入了“Krea2”作为新组件或优化了现有合成管线，尽管此次提交本身未涉及功能变更，但许可证添加暗示了底层依赖的调整。
  - 为后续使用者提供明确的授权指引，有助于项目吸引更多贡献者或商业采用。

### 4. 值得关注的技术点
- “Krea2”可能是某个特定的生成模型、图像增强算法或数据集。如果它被整合到 pipeline 中，后续版本可能会依赖该组件的特定能力（如更高效的视频风格迁移、超分辨率等）。
- 许可证类型（未在提交信息中显示）决定了该组件是开源、商业友好还是仅限研究使用，进而影响项目的分发策略。

### 5. 基于项目背景，提交对项目发展的影响
- DiffSynth-Studio 旨在提供易用的视频/图像合成工具（参考 README 中的 logo 和 Trendshift 排名），持续整合第三方高质量组件是提升其功能多样性和竞争力的关键。
- 添加“Krea2”许可证是引入新依赖的“准备步骤”，意味着开发者可能正在规划将 Krea2 的功能集成到主代码中（例如增强文本到视频合成、帧插值等），后续提交很可能会出现相关的功能合并或适配代码。
- 该提交本身虽小，但反映了项目管理者在快速迭代中仍注重法律合规，有助于维护项目健康度和社区信任。

## 详细提交记录

### [0db15b1](https://github.com/modelscope/DiffSynth-Studio/commit/0db15b19fa2be05d22211d6097478c873a4b2c56)

- **作者**: kelseyee
- **时间**: 2026-06-25T08:31:07Z
- **提交信息**: add krea2 liscense (#1511)

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-06-26
**监控日期**: 2026-06-25
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 29655
- **最后更新**: 2026-06-25T22:15:12Z

## 提交统计

- **昨日提交总数**: 23
- **提交者数量**: 16
- **主要提交者**: kk, Baizhou Zhang, weireweire

## AI分析总结

根据昨日提交记录和项目背景（sglang 是一个专注于大语言模型推理的高性能框架，支持多模态、MoE、推测解码等，并积极适配 AMD GPU 平台），分析如下：

### 1. 主要更新类型
- **新功能**：DeepSeek V2 DCP 支持、Qwen-Image NVFP4 支持、GLM5 MXFP4 支持、融合 QK 内核等。
- **性能优化**：早期缓存 KV 发送、跳过空批次、MoE 内核融合、推测解码重叠优化。
- **Bug 修复**：Ministral3 参数转发、CI 中断修复、AMD 测试超时修复。
- **文档更新**：修复扩散模型文档和 cookbook 链接漂移。
- **重构**：MoE 运行器集中化（FlashInfer CUTLASS）、代码风格清理。
- **测试与 CI**：新增 AMD 夜间 CI 测试（JIT 内核、chunked-prefill）、扩展 DeepSeek V4 Pro 和 Kimi K25 测试。

### 2. 关键变更点与项目方向关系
- **DeepSeek 系列模型深度支持**：实现 DCP 和 V4 优化，符合项目对热门模型（DeepSeek、Kimi、GLM）快速适配的方向。
- **AMD GPU 生态强化**：大量提交针对 AMD（MI350 系列），包括融合 Triton 内核、JIT 测试、MXFP4 支持，强化项目跨平台能力。
- **MoE 架构优化**：集中化 FlashInfer/CUTLASS 运行器、修复 fused shared-expert 缩放，提升 Mo

## 详细提交记录

### [ea8f4e9](https://github.com/sgl-project/sglang/commit/ea8f4e9f3fc8331de2471ae67f040ce82910436e)

- **作者**: Augusto Yao
- **时间**: 2026-06-25T22:15:04Z
- **提交信息**: [feature] implement dcp for deepseek_v2 (#14194)

### [e4696ed](https://github.com/sgl-project/sglang/commit/e4696ed62d6f7b4d2531e5fe0e406dfe4dd88163)

- **作者**: Liangsheng Yin
- **时间**: 2026-06-25T22:08:33Z
- **提交信息**: [test] Report token tps in fwd occupancy kit and force ignore_eos (#29332)

### [b7d3c30](https://github.com/sgl-project/sglang/commit/b7d3c3016d8cdc10087e65e6a5ea0ab6c697968f)

- **作者**: kk
- **时间**: 2026-06-25T20:45:18Z
- **提交信息**: [AMD] Feat/dsv4 aiter reduce scatter decode (#29103)

Co-authored-by: wunhuang <wunhuang@amd.com>

### [212c30d](https://github.com/sgl-project/sglang/commit/212c30d00899bf3f32c5de37ffa924318a67af25)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-06-25T20:40:33Z
- **提交信息**: [MoE Refactor] Centralize FlashInfer CUTLASS MoE runner (#28211)

### [dbe9e3b](https://github.com/sgl-project/sglang/commit/dbe9e3b7062df3120b3252c83fb6e3c48ac07c2c)

- **作者**: cctry
- **时间**: 2026-06-25T20:31:53Z
- **提交信息**: [PD] Early-send cached-prefix KV overlapping uncached prefill forward (#29316)

### [e6efe10](https://github.com/sgl-project/sglang/commit/e6efe10072f86cd9c1d9eb1b36f12eb800274b9a)

- **作者**: Michael
- **时间**: 2026-06-25T20:12:58Z
- **提交信息**: [AMD] Register 5 JIT kernel unit tests for AMD nightly CI (#29197)

### [118d6b2](https://github.com/sgl-project/sglang/commit/118d6b2e5ed30d9803728b845fb44e30b5289615)

- **作者**: Lianmin Zheng
- **时间**: 2026-06-25T19:51:15Z
- **提交信息**: [Cleanup] Style and type annotation improvements extracted from #28688 (#29224)

### [3344b73](https://github.com/sgl-project/sglang/commit/3344b73c80b317c60d2587d8ec963d0e197208ca)

- **作者**: Baizhou Zhang
- **时间**: 2026-06-25T19:13:52Z
- **提交信息**: Add DeepSeek V4 Pro GB300 nightly and expand Kimi K25 nightly test (#28103)

### [f9a3720](https://github.com/sgl-project/sglang/commit/f9a3720e2b182a85c98d558532d4c15b113de8e7)

- **作者**: weireweire
- **时间**: 2026-06-25T18:40:01Z
- **提交信息**: Skip empty non-idle output batches (#28504)

### [9495737](https://github.com/sgl-project/sglang/commit/9495737d828ce9ec353fa61e2b8e1ba547dc8bc4)

- **作者**: Brayden Zhong
- **时间**: 2026-06-25T17:35:34Z
- **提交信息**: Fix CI broken by #28450 (#29308)

Co-authored-by: Brayden Zhong <brayden@radixark.ai>

### [4d06d4c](https://github.com/sgl-project/sglang/commit/4d06d4c97f462145711bc9803e59670d6481406d)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-06-25T14:57:33Z
- **提交信息**: Sync Gemma4 hardware table with Blackwell recipes (#29266)

### [52c3203](https://github.com/sgl-project/sglang/commit/52c32035eb73ad2d9cdc2c77086a1ce366264558)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-06-25T14:56:09Z
- **提交信息**: [diffusion] Add Qwen-Image ModelOpt NVFP4 support (#28928)

Co-authored-by: jingyu-ml <jingyux@nvidia.com>
Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [890b38c](https://github.com/sgl-project/sglang/commit/890b38c2116a50967cb05932ac0a6bad158f8450)

- **作者**: Mick
- **时间**: 2026-06-25T13:13:00Z
- **提交信息**: [diffusion] doc: fix diffusion docs and cookbook drift (#29302)

### [bc15017](https://github.com/sgl-project/sglang/commit/bc150173b2717b41b8c8e31a627d4feae1a2b6d9)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-06-25T10:56:04Z
- **提交信息**: [AMD] Fix stage-b-test-1-gpu-small-amd-nondeterministic timeout after VLM model swap (#29234)

### [0075c8f](https://github.com/sgl-project/sglang/commit/0075c8f02b1eb8cef6843056e71c64519b278da1)

- **作者**: Raiden Makoto
- **时间**: 2026-06-25T10:54:48Z
- **提交信息**: [AMD] [GLM5] GLM-5.1 MXFP4 (MI355X) + enable EAGLE for gfx950 in cookbook (#29194)

Co-authored-by: Raiden-Makoto <Raiden-Makoto@users.noreply.github.com>

### [ddda4f9](https://github.com/sgl-project/sglang/commit/ddda4f90288b8a6140eff85074de02829d38566d)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-06-25T10:26:45Z
- **提交信息**: [Bugfix] Fix Ministral3 init argument forwarding (#29111)

### [e497668](https://github.com/sgl-project/sglang/commit/e4976683f4a79e8a462369a71a9acd56dbd83ba8)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-06-25T09:31:55Z
- **提交信息**: [Docs] Fix broken links in cookbook (#29261)

### [3d3a7ec](https://github.com/sgl-project/sglang/commit/3d3a7ec0315924804ccb278901d6f13fdd9b0943)

- **作者**: Rita Brugarolas
- **时间**: 2026-06-25T08:56:30Z
- **提交信息**:  [AMD] fix(moe): correct fused shared-expert scaling on aiter/DeepEP path (mori all-to-all) (#28237)

Signed-off-by: Rita Brugarolas Brufau <rita.brugarolasbrufau@amd.com>

### [ec12a28](https://github.com/sgl-project/sglang/commit/ec12a28a871c5dd8b456d330b2f187f54ea03efe)

- **作者**: Michael
- **时间**: 2026-06-25T08:51:30Z
- **提交信息**: [AMD] Register 7 JIT kernel unit tests for AMD nightly CI (#28967)

### [4ba8634](https://github.com/sgl-project/sglang/commit/4ba8634780d5d37ffd6aa0265ec5c32ac0a304ad)

- **作者**: Michael
- **时间**: 2026-06-25T08:50:08Z
- **提交信息**: [AMD] Register scripted-core chunked-prefill test for AMD extra-a CI (#29058)

### [de2d01c](https://github.com/sgl-project/sglang/commit/de2d01c8da49a522194f6acb8b839f9b452593cb)

- **作者**: Rita Brugarolas
- **时间**: 2026-06-25T08:22:57Z
- **提交信息**: [AMD] Fuse shared-expert append + DeepEP remap into one Triton kernel (#28450)

Signed-off-by: Rita Brugarolas Brufau <rita.brugarolasbrufau@amd.com>

### [4a82005](https://github.com/sgl-project/sglang/commit/4a8200565e1c659100fb3910bcd3be194e5506f2)

- **作者**: Yuhao Yang
- **时间**: 2026-06-25T07:58:54Z
- **提交信息**: Fused QK GemmaRMSNorm + RoPE + gate kernel for Qwen3.5 (#28320)

### [2812a3c](https://github.com/sgl-project/sglang/commit/2812a3c93a7060a40a3e7e5fc4acd2d3ec6fdca2)

- **作者**: Liangsheng Yin
- **时间**: 2026-06-25T07:44:38Z
- **提交信息**: [Spec] Unify spec/non-spec decode result handling and overlap relay-payload gating (#29225)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-06-26
**监控日期**: 2026-06-25
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1209
- **最后更新**: 2026-06-25T08:38:28Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

根据提交记录 `abe7c33` 和项目背景，总结昨日更新要点如下：

### 1. 主要更新类型
- **功能新增**（chore 类型，实质为配置扩展）：新增 `cache + dmd + svdq` 组合优化的 YAML 配置文件。

### 2. 关键变更点及其与项目方向的关系
- **变更点**：添加了多个新的 YAML 配置文件，用于定义推理引擎的优化策略组合（Cache 缓存、DMD、SVDQ）。
- **与项目方向关系**：项目定位是 DiT（Diffusion Transformers）的高效推理引擎，核心能力包括缓存、并行、量化、CPU 卸载等。此次新增的配置文件直接提供了将**缓存（Cache）** 与 **DMD**（可能为扩散模型蒸馏/动态多尺度解码）以及 **SVDQ**（可能为基于奇异值分解的量化/剪枝）三种技术联用的方案，进一步丰富了引擎支持的优化组合，符合项目提供“即插即用”优化配置的长期目标。

### 3. 对项目的影响和潜在意义
- **用户友好性提升**：预先定义好的优化组合配置降低使用者调参门槛，用户可快速尝试 SOTA 组合策略。
- **性能潜力**：Cache+DMD+SVDQ 可能同时利用缓存减少重复计算、蒸馏/DMD 提升速度、SVDQ 压缩模型，有望在推理吞吐、延迟和显存占用上取得更好平衡。
- **生态扩展**：为后续支持更多混合优化策略（如并行+量化+卸载等）提供了模板，推动项目成为更完备的 DiT 推理加速平台。

### 4. 值得关注的技术点
- **DMD 与 SVDQ 细节**：需要后续关注具体实现——DMD 可能指 Dynamic Multi-scale Decoding 或 Diffusion Model Distillation；SVDQ 大概率是 SVD-based Quantization（奇异值分解后量化），用于低秩近似压缩。这些技术的组合是当前 DiT 推理优化的前沿方向。
- **YAML 配置结构**：新配置文件的内容将揭示引擎如何统一调度不同优化模块（如是否自动启用 CPU 卸载、并行度设置等），值得查看具体参数项。

### 5. 结合项目背景的发展影响
- **对齐推理引擎核心目标**：项目 README 强调“PyTorch-native”和“高性能”，此次新增组合配置正是通过模块化方式实现更极致的加速，强化了项目在吞吐量和内存效率方面的竞争力。
- **吸引社区贡献**：配置文件的加入表明项目已进入**优化策略组合阶段**，可激励更多用户基于此提交自定义配置或实现新优化技术，促进项目从“单点优化”向“组合式自动化调优”演进。
- **潜在使用场景**：适用于对实时性要求高且显存受限的 DiT 推理场景（如文生图、视频生成等），缓存与模型压缩的组合尤其适合长序列生成任务。

## 详细提交记录

### [abe7c33](https://github.com/vipshop/cache-dit/commit/abe7c3383d79422bcaa70f5b4e91cbd6f6c3127e)

- **作者**: DefTruth
- **时间**: 2026-06-25T08:38:24Z
- **提交信息**: chore: add cache+dmd+svdq yaml configs (#1069)

* chore: add cache+dmd+svdq yaml configs

* chore: add cache+dmd+svdq yaml configs

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-06-26
**监控日期**: 2026-06-25
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 84319
- **最后更新**: 2026-06-25T23:07:19Z

## 提交统计

- **昨日提交总数**: 26
- **提交者数量**: 23
- **主要提交者**: Ranran, Flora Feng, Gabriel Wu

## AI分析总结

以下是对 vllm-project/vllm 昨日（2025-07-23）提交记录的要点分析，结合项目“Easy, fast, and cheap LLM serving”的背景进行解读。

---

### 1. 主要更新类型
- **性能优化**：约 1/3 的提交（3, 5, 6, 7, 13, 22, 23 等涉及 kernel 调优、移除冗余操作、稀疏注意力、量化方法）。
- **硬件/平台支持扩展**：AMD ROCm（1, 4, 8, 13, 14, 18, 22）、Intel CPU（20, 23, 25）、Intel XPU（21）、RISC-V（23）、NIXL（19）。
- **Bug 修复**：P/D 分离、NVFP4 兼容性、Cohere 计费、CI 测试修复等（5, 10, 11, 15, 26）。
- **CI/测试改进**：依赖构建、测试回归、ARM64 镜像、macOS 安全、ROCm 去重等（2, 9, 14, 16, 18, 20, 21）。
- **新功能/模型支持**：Mamba1 支持 NIXL（19）、CPU 上的流水线推测解码（25）、RISC-V W4A8 INT4 GEMM（23）。
- **重构/移除**：移除 Aquila 模型（24）、MoE kernel 重构（17）、向量化 reduction（3）。
- **工具链/前端**：Rust 前端超时配置（26）。

---

### 2. 关键变更点及其与项目整体方向的关系
| 变更点 | 与项目方向关联 |
|--------|----------------|
| **Vectorized fp32 moe_sum & 任意 topk**（#46643） | 直接提升 MoE 性能，降低推理延迟，契合“fast”目标。 |
| **Block-FP8 fused MoE 低 batch decode 调优**（#46642） | 针对低吞吐场景优化，提升小批量推理效率，降低“cheap”成本。 |
| **AMD ROCm 稀疏注意力优化**（#46546） | 扩展 AMD GPU 高效运行，降低对 NVIDIA 依赖，扩大硬件覆盖（“easy for everyone”）。 |
| **移除 Aquila 模型**（#46605） | 清理不再维护的模型，简化代码库，降低维护成本。 |
| **Mamba1 支持 NIXL P/D 分离**（#45019） | 增强状态空间模型支持，并利用 NIXL 实现预填充/解码分离（细粒度资源调度），提升整体吞吐。 |
| **CPU 上支持流水线推测解码**（#44029） | 突破 CPU 推理性能瓶颈，让低成本硬件也能加速推理（“cheap”）。 |
| **RISC-V W4A8 INT4 GEMM**（#45269） | 开辟新的边缘/嵌入式硬件支持，进一步拓展“everyone”范围。 |
| **Bug 修复（

## 详细提交记录

### [27da2a2](https://github.com/vllm-project/vllm/commit/27da2a2ac4776faa4265cba38ba86dd3a7119c4f)

- **作者**: Matt
- **时间**: 2026-06-25T22:08:04Z
- **提交信息**: [Hardware][AMD][CI] Use Triton-based AITER MHA for LM Eval Qwen-3.5 Models Tests (#46691)

Signed-off-by: Matthew Wong <Matthew.Wong2@amd.com>

### [a2e8ec3](https://github.com/vllm-project/vllm/commit/a2e8ec3d52ab4e163501c8c7bee8c03ca8359a7a)

- **作者**: Michael Goin
- **时间**: 2026-06-25T21:07:04Z
- **提交信息**: [CI] Depend GPQA Eval DGX Spark job on arm64 image build (#46736)

Signed-off-by: mgoin <mgoin64@gmail.com>

### [e8c24a7](https://github.com/vllm-project/vllm/commit/e8c24a769576fa318ca93fbd927128246a534325)

- **作者**: Michael Goin
- **时间**: 2026-06-25T21:02:28Z
- **提交信息**: [Kernel] Vectorized fp32 `moe_sum` reduction and support any topk (#46643)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [2a6f8f0](https://github.com/vllm-project/vllm/commit/2a6f8f0c05ab1dd0b11540157fb72b6888883aab)

- **作者**: Andreas Karatzas
- **时间**: 2026-06-25T20:24:09Z
- **提交信息**: [ROCm][CI] Fine-tuning queues and test names (#39238)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [c5e3c40](https://github.com/vllm-project/vllm/commit/c5e3c40877c2b6d0e16d534641b39fe6744979b7)

- **作者**: Robert Shaw
- **时间**: 2026-06-25T20:13:08Z
- **提交信息**: Fix P/D with DP Supervisor (#46628)

Signed-off-by: Robert Shaw <114415538+robertgshaw2-redhat@users.noreply.github.com>

### [8b4d93b](https://github.com/vllm-project/vllm/commit/8b4d93ba2b4e4e79062fd59a35a623e381dcf6b0)

- **作者**: Wentao Ye
- **时间**: 2026-06-25T20:09:00Z
- **提交信息**: [Perf] Remove redundant clone for GLM, Deepseek etc (#46651)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [e8e7b59](https://github.com/vllm-project/vllm/commit/e8e7b592d11d3ea5d5cdb78ee0f1ab4c5b440667)

- **作者**: Michael Goin
- **时间**: 2026-06-25T19:38:28Z
- **提交信息**: [Kernel][MoE] Tune block-FP8 fused MoE for low-batch decode (#46642)

Signed-off-by: mgoin <mgoin64@gmail.com>

### [e53a172](https://github.com/vllm-project/vllm/commit/e53a17232c3114ab276d7004edb195304ecdad57)

- **作者**: Rohan Potdar
- **时间**: 2026-06-25T18:53:26Z
- **提交信息**: [ROCm]: Bump aiter to 0.1.16.post2 (#46692)

Signed-off-by: Rohan138 <rohanpotdar138@gmail.com>

### [96eb8dd](https://github.com/vllm-project/vllm/commit/96eb8ddc41f9238f3aba51a190623203ff040b3f)

- **作者**: Flora Feng
- **时间**: 2026-06-25T17:11:41Z
- **提交信息**: [CI] Re-enable skipped glm and seedoss parser tests (#46671)

Signed-off-by: sfeng33 <4florafeng@gmail.com>

### [8fa36fb](https://github.com/vllm-project/vllm/commit/8fa36fbbebdf838953a904531c86fcd05896a4c8)

- **作者**: Gabriel Wu
- **时间**: 2026-06-25T16:12:00Z
- **提交信息**: [Bugfix] FLASHINFER_MLA_SPARSE_SM120 compatibility with GLM-5 NVFP4 (#46506)

### [e45b279](https://github.com/vllm-project/vllm/commit/e45b279928726951738427f48141739c1a4bcfe2)

- **作者**: Ranran
- **时间**: 2026-06-25T16:05:04Z
- **提交信息**: [Bugfix] Fix NVFP4+MTP crash: force unquantized mtp.fc for Qwen3Next (#46316)

Signed-off-by: Ranran Haoran Zhang <ranzhang@redhat.com>

### [d490b98](https://github.com/vllm-project/vllm/commit/d490b98162422922230c8b91757c58077e24682f)

- **作者**: Yiliu Dong
- **时间**: 2026-06-25T15:34:44Z
- **提交信息**: [Core] Avoid mixed length specdec batches via padding (#45237)

Signed-off-by: Yiliu Dong <91178480+qianlihuang@users.noreply.github.com>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Jade Zheng <zheng.shoujian@outlook.com>
Co-authored-by: Giancarlo Delfin <gdelfin@inferact.ai>
Co-authored-by: Zijing Liu <liuzijing2014@gmail.com>

### [1744adc](https://github.com/vllm-project/vllm/commit/1744adc256b81b8a7d2371a5e21f88174d60cc93)

- **作者**: haoyangli0109
- **时间**: 2026-06-25T15:14:15Z
- **提交信息**: [ROCM] [Communication] Add INT3 quantization method for quickreduce (#45666)

Signed-off-by: Haoyang Li <lihaoyang0109@gmail.com>

### [cdfa2fd](https://github.com/vllm-project/vllm/commit/cdfa2fd7e9eb26d911312989b6458d71f248608e)

- **作者**: Divakar Verma
- **时间**: 2026-06-25T14:58:17Z
- **提交信息**: [ROCm][CI] rm duplicate Distributed Torchrun ci test (#46729)

Signed-off-by: Divakar Verma <divakar.verma@amd.com>

### [6f3da46](https://github.com/vllm-project/vllm/commit/6f3da461d17e168539e99f925c0620db64eb011b)

- **作者**: Taneem Ibrahim
- **时间**: 2026-06-25T14:44:29Z
- **提交信息**: [Pooling] Fix Cohere embed billed image token accounting for mixed-content inputs (#46093)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [d3130d8](https://github.com/vllm-project/vllm/commit/d3130d878cb1ae9e0b943d78bcd3aa09cf59d5b8)

- **作者**: Russell Bryant
- **时间**: 2026-06-25T13:48:44Z
- **提交信息**: [CI] Pin GitHub Actions to commit hashes in macos-smoke-test.yml (#38290)

### [9bfd878](https://github.com/vllm-project/vllm/commit/9bfd878a48fb92e5e28267f07ad1b7d844ebf160)

- **作者**: Qiuyang Yue
- **时间**: 2026-06-25T13:34:03Z
- **提交信息**: [MoE] [MoE Refactor] Add moe kernel oracle abc 37753 (#43461)

Signed-off-by: Qiuyang Yue <yueqiuyang1389@gmail.com>
Signed-off-by: qyYue1389 <yueqiuyang1389@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [2365b7a](https://github.com/vllm-project/vllm/commit/2365b7a8e7c0f6c55eeb820fba43416f880d3a51)

- **作者**: Matt
- **时间**: 2026-06-25T13:25:09Z
- **提交信息**: [Hardware][AMD][CI] Mirror Basic Models (Others) and Weight Loading Multiple GPU test groups (#46668)

Signed-off-by: Matthew Wong <Matthew.Wong2@amd.com>

### [15be787](https://github.com/vllm-project/vllm/commit/15be78732bac03af62dc05d588e245271b72f10d)

- **作者**: Asaf Gardin
- **时间**: 2026-06-25T12:50:41Z
- **提交信息**: [NIXL][Mamba] Add Mamba1 support to NIXL P/D disaggregation (#45019)

Signed-off-by: Josephasafg <ajgard7@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [9222148](https://github.com/vllm-project/vllm/commit/92221485aaaa4088491db3f182dd65a390fc9ac5)

- **作者**: Li, Jiang
- **时间**: 2026-06-25T11:33:39Z
- **提交信息**: [CPU][CI/Build] Allow more CPU CI agents  (#46702)

Signed-off-by: jiang1.li <jiang1.li@intel.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [a6f41ab](https://github.com/vllm-project/vllm/commit/a6f41ab6789953c3dfb60ad0c52c7bdf55002d41)

- **作者**: xiangdong
- **时间**: 2026-06-25T08:58:26Z
- **提交信息**: [XPU][CI]Refine .buildkite/ci_config_intel.yaml for Intel GPU CI (#46674)

Signed-off-by: zengxian <xiangdong.zeng@intel.com>

### [c63cd49](https://github.com/vllm-project/vllm/commit/c63cd4906c2a67f18b3714786cc036c1ad97a64f)

- **作者**: Hongxia Yang
- **时间**: 2026-06-25T08:56:00Z
- **提交信息**: [ROCm][ [Perf] sparse attention optimization on minimax-m3  (#46546)

Signed-off-by: Hongxia Yang <hongxia.yang@amd.com>
Signed-off-by: tjtanaa <tunjian.tan@embeddedllm.com>
Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>
Co-authored-by: yueliu14 <yue.liu4@amd.com>
Co-authored-by: tjtanaa <tunjian.tan@embeddedllm.com>

### [638b1a9](https://github.com/vllm-project/vllm/commit/638b1a99ccd7b47f45f9a773456f77aeb66d4a1b)

- **作者**: wcy
- **时间**: 2026-06-25T08:18:10Z
- **提交信息**: [CPU][RISC-V] Add RVV path for W4A8 INT4 GEMM (#45269)

Signed-off-by: wcy <233313160abc@gmail.com>
Co-authored-by: lyd1992 <liuyudong@iscas.ac.cn>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [72adb20](https://github.com/vllm-project/vllm/commit/72adb20a6ac023fa6a6b2748fda673e582d2f74e)

- **作者**: Tiezhen WANG
- **时间**: 2026-06-25T08:08:26Z
- **提交信息**: [Model] Remove AquilaForCausalLM, AquilaModel (#46605)

Signed-off-by: Xianbao QIAN <xianbao.qian@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [2396d91](https://github.com/vllm-project/vllm/commit/2396d91e931295df877cdad5e2ac0de4e35dab9f)

- **作者**: guybd
- **时间**: 2026-06-25T07:32:48Z
- **提交信息**: [CPU][Spec Decode] Enable DFlash SD for CPU (#44029)

Signed-off-by: guybd <guy.boudoukh@intel.com>
Signed-off-by: Guy Boudoukh <guy.boudoukh@intel.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [9b215ae](https://github.com/vllm-project/vllm/commit/9b215ae60b523df34fd949598e657c2b26ea879a)

- **作者**: Kai
- **时间**: 2026-06-25T07:25:08Z
- **提交信息**: [Rust Frontend] Forward `VLLM_ENGINE_READY_TIMEOUT_S` via `--args-json` (#44610)

Signed-off-by: kai <kai@example.com>
Co-authored-by: 图灵 <tuling.wk@alibaba-inc.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-06-26
**监控日期**: 2026-06-25
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 5274
- **最后更新**: 2026-06-25T20:09:02Z

## 提交统计

- **昨日提交总数**: 7
- **提交者数量**: 7
- **主要提交者**: Weiming Liao, Gaël Glorian, bmengke

## AI分析总结

### 1. 主要更新类型

- **Bug修复**（2项）：Wan2.2模型在t2v/i2v中使用cache-dit与ulysses时的bug；NPU平台自定义算子注册问题。
- **新功能/模型支持**（3项）：新增Ming-omni-tts（MoE 16.8B-A3B + CFM CUDAGraph）和MOSS-TTS-local-v1.5两个TTS模型；LVSA（无需训练的块稀疏注意力）技术展示。
- **性能优化**（2项）：hunyuan-image预取KV（减少推理延迟）；LVSA本身即面向推理效率的注意力机制。
- **重构/工程改进**（1项）：引入结构化VllmOmniConfig配置类，改善可维护性。

### 2. 关键变更点与项目方向关系

| 变更 | 对应模态 | 与项目“全模态、快、便宜”目标的关系 |
|------|----------|-------------------------------------|
| Wan2.2 bug修复 | 视频（文本→视频、图像→视频） | 确保视频生成流程稳定，提升服务可靠性 |
| LVSA展示 | 通用（注意力） | 探索训练‑free稀疏注意力，降低计算成本、加速推理 |
| Ming-omni-tts + MOSS-TTS | 音频（语音合成） | 扩展语音模态支持，逼近“全模态”愿景 |
| hunyuan-image KV预取 | 图像 | 优化图像生成/理解流水线的KV缓存管理，提升吞吐 |
| NPU平台bug修复 | 硬件兼容 | 支持昇腾NPU，降低硬件门槛，使众筹/低成本部署可行 |
| 结构化配置类 | 工程基建 | 统一配置管理，提高易用性和扩展性（“Easy”） |

### 3. 对项目的影响和潜在意义

- **完善模态覆盖**：新增两个TTS模型（Ming-omni-tts、MOSS-TTS），使项目从视觉/语言进一步拓展到音频生成，更贴近“omni-modality”定位。
- **性能与成本**：LVSA若被采纳可显著减少注意力计算量；KV预取优化图像场景的内存与延迟；MoE模型（16.8B-A3B）兼顾容量与激活成本，符合“fast and cheap”。
- **稳定性提升**：修复Wan2.2和NPU平台的bug，减少线上服务故障风险。
- **工程健

## 详细提交记录

### [329c98f](https://github.com/vllm-project/vllm-omni/commit/329c98ff9d9da37b8fa38bc3ea8005cb8472406f)

- **作者**: bmengke
- **时间**: 2026-06-25T15:15:59Z
- **提交信息**: Wan2.2: Fix the bug of using cache-dit with ulysses in t2v and i2v (#3927)

Signed-off-by: Mengkejiergeli Ba <mengkejiergeli.ba@intel.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [36a5e9c](https://github.com/vllm-project/vllm-omni/commit/36a5e9cfd2e83d602fa83ca8d49b6534e37c604b)

- **作者**: Gaël Glorian
- **时间**: 2026-06-25T14:20:14Z
- **提交信息**: [skip ci][Misc] LVSA showcase (training-free block-sparse attention) (#4192)

Signed-off-by: Gael Glorian <gael.glorian@gmail.com>
Signed-off-by: Ioannis Lamprou <yiannis.lamprou@gmail.com>
Signed-off-by: Zhen Zhang <zhen.zhang.fr@huawei.com>
Co-authored-by: Ioannis Lamprou <yiannis.lamprou@gmail.com>
Co-authored-by: Zhen Zhang <zhen.zhang.fr@huawei.com>

### [0b04f2a](https://github.com/vllm-project/vllm-omni/commit/0b04f2a0d6163d9719b5a4fc6d3cae0797543fd3)

- **作者**: LHXuuu
- **时间**: 2026-06-25T14:11:35Z
- **提交信息**: [Model] Add Ming-omni-tts MoE 16.8B-A3B + CFM CUDAGraph (#4341)

Signed-off-by: LHXuuu <xulianhao.xlh@antgroup.com>
Signed-off-by: Yuanheng Zhao <jonathan.zhaoyh@gmail.com>
Signed-off-by: Hongsheng Liu <liuhongsheng4@huawei.com>
Co-authored-by: Yuanheng Zhao <jonathan.zhaoyh@gmail.com>
Co-authored-by: Yuanheng Zhao <54058983+yuanheng-zhao@users.noreply.github.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [5db89b4](https://github.com/vllm-project/vllm-omni/commit/5db89b41c427741e6c0d9b3f4b06775d2717245d)

- **作者**: Honghan Zhu
- **时间**: 2026-06-25T13:31:49Z
- **提交信息**: [Core] hunyuan-image prefetch kv (#4448)

Signed-off-by: z00806815 <zhuhonghan@huawei.com>
Signed-off-by: zhuhh97 <zhuhonghan@huawei.com>
Signed-off-by: dph97 <nenbaying@163.com>
Signed-off-by: zhh <zhh@users.noreply.github.com>
Co-authored-by: Claude Opus 4.7 <noreply@anthropic.com>
Co-authored-by: zhuhh97 <zhuhh97@users.noreply.github.com>

### [e500c00](https://github.com/vllm-project/vllm-omni/commit/e500c00545b80446d58c4ade4cbc831a26932042)

- **作者**: Weiming Liao
- **时间**: 2026-06-25T10:50:08Z
- **提交信息**: [Bugfix][NPU] Register vllm-ascend custom ops in NPUOmniPlatform.set_device (#4712)

Signed-off-by: Weiming Liao <liaowm5@gmail.com>

### [8ddcb36](https://github.com/vllm-project/vllm-omni/commit/8ddcb3621fa404a1cc39016c892b763902a8be74)

- **作者**: Wang  fuyin
- **时间**: 2026-06-25T09:48:20Z
- **提交信息**: [Config] Add structured VllmOmniConfig classes (#4425)

Signed-off-by: Acerak01-fy <wfy2003324@163.com>
Signed-off-by: zwhzzz0821 <2831474076@qq.com>
Signed-off-by: Wang  fuyin <wfy2003324@163.com>
Co-authored-by: zwhzzz0821 <2831474076@qq.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [2e6c83c](https://github.com/vllm-project/vllm-omni/commit/2e6c83c89c599ce4dd89fcde29626bc97b8b7ae4)

- **作者**: Canlin Guo
- **时间**: 2026-06-25T07:43:03Z
- **提交信息**: [Model] Support MOSS-TTS-local-v1.5 (#4664)

Signed-off-by: gcanlin <canlinguosdu@gmail.com>

---
