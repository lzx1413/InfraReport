# GitHub Stars 合并报告 - 2026-04-14

**合并日期**: 2026-04-15
**监控日期**: 2026-04-14
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


**报告日期**: 2026-04-15
**监控日期**: 2026-04-14
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 1825
- **最后更新**: 2026-04-14T13:50:05Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Bin Jia

## AI分析总结

根据提供的提交记录和README摘要，以下是对昨日更新的分析总结：

### 1. 主要更新类型
- **Bug修复**：修复了持续集成（CI）流程中的端口选择错误。

### 2. 关键变更点及其与项目整体方向的关系
- **变更点**：修复CI测试中端口选择的错误（`#646`）。
- **与项目方向的关系**：VeOmni 作为一个专注于“模型中心化分布式配方库”的大规模多模态训练框架，其稳定性和可靠性至关重要。CI/CD管道的健康运行是保证代码质量、加速迭代和支撑大规模分布式实验的基础。此次修复直接服务于项目 **“规模化”（Scaling）** 和 **“可靠性”** 的核心目标。

### 3. 对项目的影响和潜在意义
- **直接影响**：确保了自动化测试流程的稳定运行，避免了因CI失败导致的开发阻塞或错误代码合并。
- **潜在意义**：维护了项目基础设施的健壮性，这对于一个旨在简化并优化大规模多模态模型训练（涉及复杂分布式配置）的项目来说，是长期高效协作和高质量交付的基本保障。

### 4. 值得关注的技术点
- **CI/CD配置**：提交涉及CI环境的网络端口管理，暗示项目可能拥有复杂的多服务测试环境或分布式测试场景，这与项目处理分布式训练的特性相符。
- **问题追踪**：通过PR编号（`#646`）关联修复，显示了项目具有规范的开发流程和问题追踪机制。

### 5. 基于项目背景的提交影响分析
- VeOmni 的目标是提供一套 **“配方”（Recipe）** 来简化任何模态模型的**大规模分布式训练**。这背后需要极其稳定和自动化的工程体系作为支撑。
- 此次 **CI修复** 虽不直接增加新功能或优化算法性能，但它是 **“磨刀不误砍柴工”** 的关键维护工作。它确保了：
    - **开发效率**：团队能持续、快速地进行集成测试，加速新配方和功能的开发。
    - **项目可信度**：稳定的CI是项目成熟度和工程严谨性的体现，有助于吸引开源贡献者和用户。
    - **规模化基础**：为未来更复杂的多模态、分布式训练场景的自动化测试铺平道路，是项目实现其“规模化”愿景的底层工程保障。

**总结**：这是一次针对项目**基础设施的维护性修复**，虽看似微小，但对于VeOmni这类致力于解决大规模、复杂训练工程问题的项目而言，是维持其健康发展、确保长期“规模化”目标得以实现的重要基石。

## 详细提交记录

### [984bb0b](https://github.com/ByteDance-Seed/VeOmni/commit/984bb0b4f70885693149de444a36a1f7833e2020)

- **作者**: Bin Jia
- **时间**: 2026-04-14T07:58:54Z
- **提交信息**: [ci] fix: fix ci port select error (#646)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-04-15
**监控日期**: 2026-04-14
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Light Image Video Generation Inference Framework
- **语言**: Python
- **星标数**: 2172
- **最后更新**: 2026-04-14T19:19:04Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 2
- **主要提交者**: Yang Yong (雍洋), Shankun Wang (王善昆)

## AI分析总结

根据您提供的仓库 `ModelTC/LightX2V` 的 README 摘要和昨日提交记录，以下是对更新的分析总结：

### 1. 主要更新类型
- **功能新增**：添加了虚拟模型（dummy model）功能。
- **模型/依赖更新**：更新了 Zoe 和 Qwen-Image 相关的组件或配置。
- **文档更新**：更新了项目 README 文档。

### 2. 关键变更点及其与项目整体方向的关系
- **`[6db002f] [feat] Add dummy model feature (#1009)`**：
    - **关键变更**：引入了“虚拟模型”功能。这通常用于在真实模型不可用或资源受限时，提供一个轻量级的模拟接口，用于测试、演示或开发流程验证。
    - **与项目方向关系**：`LightX2V` 定位为 **轻量级视频生成推理框架**。此功能直接服务于其“轻量”和“易用”的核心目标。它降低了开发者和研究者的入门和测试门槛，允许他们在不部署完整、重型模型的情况下，快速搭建和验证推理流水线、API接口或前端应用，这与框架追求高效、灵活的理念高度一致。

- **`[09f01d3] update zoe qwen-image (#1012)`**：
    - **关键变更**：对 `Zoe`（可能指深度估计模型 ZoeDepth）和 `Qwen-Image`（通义千问的多模态视觉模型）进行了更新。这可能是版本升级、Bug修复、性能优化或适配性改进。
    - **与项目方向关系**：作为视频生成框架，其能力依赖于底层视觉和多模态模型的性能与稳定性。更新主流组件（如深度估计、图像理解模型）是**保持技术先进性和兼容性**的关键。这表明项目在积极集成和维护最新的AI模型成果，以确保框架能够提供最先进、最可靠的视频生成能力。

- **`[c36e465] update readme (#1010)`**：
    - **关键变更**：更新了项目最主要的说明文档。
    - **与项目方向关系**：良好的文档是开源项目成功和推广的基石。及时更新 README 反映了项目维护的活跃度，有助于**改善用户体验、吸引贡献者、清晰传达项目最新状态和能力**，这对于一个旨在推广使用的框架至关重要。

### 3. 对项目的影响和潜在意义
- **提升开发体验与可测试性**：虚拟模型功能显著改善了框架的开发、调试和演示体验，使快速原型设计成为可能。
- **维持技术竞争力**：更新核心模型组件确保了框架底层技术的时效性和鲁棒性，避免因依赖过时而影响生成效果。
- **增强项目可访问性与专业性**：更新文档直接提升了用户和潜在合作者对项目的认知效率与信任度。
- **潜在意义**：这些更新共同强化了 `LightX2V` 作为一个 **“现代化、开发者友好、易于上手且技术前沿”** 的轻量级推理框架的定位，为其在快速发展的视频生成领域吸引更广泛的用户和贡献者奠定了基础。

### 4. 值得关注的技术点
- **“Dummy Model”的实现机制**：它是如何模拟真实模型的输入/输出行为的？是否支持可配置的延迟和输出格式？这体现了框架在**抽象化和可测试性设计**上的考量。
- **Zoe 和 Qwen-Image 的集成方式**：更新是否涉及模型接口、预处理/后处理逻辑或性能优化？这反映了框架在**多模型组件管理和集成**方面的设计水平。
- **README 更新的具体内容**：是否增加了新功能的使用说明、性能基准数据或新的应用案例？这直接反映了项目重点的演进和宣传方向。

### 5. 基于项目背景的提交影响分析
`LightX2V` 的目标是成为一个高效的视频生成推理框架。昨日的提交从三个层面推动了这一发展：
1.  **基础设施层（虚拟模型）**：通过添加虚拟模型，**降低了框架的使用和评估成本**，使更多开发者能无负担地探索和集成 `LightX2V`，这有利于生态构建。
2.  **核心能力层（模型更新）**：通过更新关键模型，**直接提升了框架所能提供的视频生成任务的上限和质量**，确保了其技术核心不落伍。
3.  **生态与传播层（文档更新）**：通过维护文档，**优化了项目的对外形象和沟通效率**，是项目从“可用”走向“易用”和“流行”的重要一步。

**总结**：昨日的更新是一次 **“体验优化、能力维护、生态建设”** 三位一体的迭代。它没有引入颠覆性的新功能，而是扎实地打磨了框架的**可用性、稳健性和可接近性**，这正是 `LightX2V` 这类旨在服务广大开发者的基础设施类项目健康发展的典型标志。

## 详细提交记录

### [09f01d3](https://github.com/ModelTC/LightX2V/commit/09f01d3f6e9b31a09aa09bdec43d5f4d16dfbe41)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-04-14T19:18:59Z
- **提交信息**: update zoe qwen-image (#1012)

### [6db002f](https://github.com/ModelTC/LightX2V/commit/6db002f2755036b02bd0900bf9b41958bbfb4137)

- **作者**: Shankun Wang (王善昆)
- **时间**: 2026-04-14T09:06:48Z
- **提交信息**: [feat] Add dummy model feature (#1009)

### [c36e465](https://github.com/ModelTC/LightX2V/commit/c36e465a47ff3ccd63b46a762058a8928d4c565d)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-04-14T08:50:36Z
- **提交信息**: update readme (#1010)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-04-15
**监控日期**: 2026-04-14
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2019
- **最后更新**: 2026-04-14T19:09:46Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-04-15
**监控日期**: 2026-04-14
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5395
- **最后更新**: 2026-04-14T21:28:52Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 4
- **主要提交者**: Brian K. Ryu, Alex Yang, aniskumar-nv

## AI分析总结

根据FlashInfer仓库的README摘要（专注于“高性能GPU推理内核”）和昨日提交记录，以下是分析总结：

### 1. 主要更新类型
- **Bug修复**：修复了SM120（Blackwell）上FP8 MoE内核的共享内存占用问题，以及编译回归问题。
- **功能新增**：为MoE内核添加了路由重放支持，并新增了针对SM120的FP4 GEMM后端“b12x”。
- **性能优化**：通过“b12x”后端显著提升了SM120上FP4矩阵乘法的性能（尤其在小M形状上）。
- **文档更新**：新增了环境变量`MAX_JOBS`的文档，并提供了vLLM路由重放集成指南。
- **版本发布**：版本号升级至0.6.8，包含多项API变更和功能增强。

### 2. 关键变更点及其与项目整体方向的关系
| 变更点 | 与项目方向的关系 |
|--------|----------------|
| **SM120 FP8 MoE修复** (`bf9b1da`) | 确保在新一代Blackwell GPU上MoE推理的稳定性和性能，**维持跨GPU架构的高性能兼容性**。 |
| **MoE路由重放** (`5056474`) | 支持RL训练工作流（如vLLM），**扩展了MoE在训练-推理一体化场景的应用**，增强了与主流推理引擎的集成。 |
| **SM120 FP4 GEMM后端“b12x”** (`8c93f92`) | 针对Blackwell架构优化FP4计算，**提升了低精度推理在最新硬件上的性能**（平均1.2倍加速）。 |
| **编译环境变量文档** (`c60699d`) | 帮助用户管理大规模内核编译时的内存使用，**改善了开发者体验和部署稳定性**。 |
| **版本升级至0.6.8** (`8063bc5`) | 整合了多项API改进（如`kv_cache_sf`参数重命名），**标志着项目进入更成熟阶段**，为生产环境提供更稳定的接口。 |

### 3. 对项目的影响和潜在意义
- **硬件覆盖扩展**：强化了对NVIDIA Blackwell（SM120）的支持，确保项目在最新硬件上保持竞争力。
- **生态集成深化**：路由重放功能直接服务于vLLM等流行推理引擎，**增强了FlashInfer在MoE推理生态中的核心地位**。
- **性能基准提升**：“b12x”后端为FP4推理设定了新的性能标杆，尤其在解码场景（小M）中优势明显。
- **开发者友好性**：文档和API的改进降低了使用门槛，有利于社区采纳和贡献。

### 4. 值得关注的技术点
- **MoE路由重放的CUDA图兼容性**：通过内核级写入（而非Python回调）解决`torch.compile` + CUDA图的兼容问题，**体现了对生产级部署需求的深度理解**。
- **共享内存占用预过滤**：在autotuning前剔除零占用的tile配置，**避免了运行时错误并提升了调优效率**。
- **CuTe DSL移植**：“b12x”后端基于CuTe DSL实现，**展示了项目对现代CUDA编程范式的采纳**。
- **编译资源管理**：明确`MAX_JOBS`与`FLASHINFER_NVCC_THREADS`的相互作用，**解决了大规模内核编译时的OOM风险**。

### 5. 基于项目背景的提交影响分析
FlashInfer的核心目标是提供**高性能、跨平台的GPU推理内核**。昨日的提交集体推动了这一目标：
- **性能维度**：“b12x”后端和MoE修复直接提升了在Blackwell上的计算效率，**巩固了其在低精度推理和MoE场景的性能领先地位**。
- **可扩展性维度**：路由重放支持了更复杂的训练-推理流水线，**拓宽了应用场景**，使项目不仅限于纯推理。
- **稳健性维度**：Bug修复和文档更新**增强了项目的生产就绪性**，降低了用户在不同硬件和配置下的故障风险。
- **社区与生态维度**：与vLLM的集成指南和清晰的API变更（v0.6.8）**促进了生态协作和用户迁移**，有助于项目成为GPU推理堆栈的标准组件。

**总结**：昨日的更新体现了FlashInfer在**支持最新硬件、优化关键路径性能、深化生态集成、提升开发者体验**四个方向的同步推进，整体上强化了其作为高性能GPU推理内核库的定位和竞争力。

## 详细提交记录

### [bf9b1da](https://github.com/flashinfer-ai/flashinfer/commit/bf9b1dac855005ffaa57b48ae54cba30642bf213)

- **作者**: aniskumar-nv
- **时间**: 2026-04-14T21:28:46Z
- **提交信息**: fix: fused_moe: pre-filter SM89 tactics with zero occupancy on SM120 Blackwell (fix review feedback on #2764) (#3032)

## Summary

Supersedes #2764 (by @dryu-nv). This PR carries the original fix forward
and addresses all review feedback raised by CodeRabbit and Gemini Code
Assist.

Closes #3031.

### Original fix (#2764)
On SM120 (Blackwell), pure FP8 MoE falls back to `cutlass::arch::Sm89`
kernels. Some SM89 tile configs exceed Blackwell's shared memory,
causing the autotuner to hit a shared memory assertion and skip those
tactics, degrading MoE throughput. The fix adds an occupancy pre-filter
in `MoERunner.get_valid_tactics()` so zero-occupancy tactics are dropped
before autotuning begins.

### Changes in this PR (on top of #2764)


**`csrc/fused_moe/cutlass_backend/flashinfer_cutlass_fused_moe_binding.cu`**
- Add `std::lock_guard<std::mutex> lock(mMutex)` inside the
`get_tactic_occupancy` lambda to protect access to `mAllProfiles` and
`mKernelRunner` from concurrent `setTactic()`/`runMoe()` calls (thread
safety issue flagged by CodeRabbit)

**`flashinfer/fused_moe/core.py`**
- Capture exception `e` and emit `logger.warning(...)` in the
`get_occ(t)` failure path so FFI/C++ errors are no longer silently
swallowed (logging issue flagged by Gemini)
- Return `[-1]` sentinel when `all_tactics` is empty (zero-tactic
stage), preventing `get_valid_tactics()` from returning an empty list
and violating its contract (edge case flagged by CodeRabbit)

## Test plan

- [ ] Run FP8 MoE autotuner on SM120 Blackwell (RTX PRO 6000 / GB10) —
confirm no `GPU lacks shared memory` warnings
- [ ] Verify no regression on SM90 (H100) FP8 MoE autotuner
- [ ] Confirm dense NVFP4 models unaffected

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Exposed an occupancy query so callers can determine whether a kernel
tactic is supported on the device before execution.

* **Refactor**
* Tactic selection now pre-validates candidates using occupancy results,
preserves safe fallbacks when queries are missing or fail, logs warnings
for query errors, and avoids returning an empty candidate list.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Donghan Ryu <dryu@nvidia.com>

### [5056474](https://github.com/flashinfer-ai/flashinfer/commit/5056474e16f31f014056a1b2f7c856472052cba3)

- **作者**: TomerBN-Nvidia
- **时间**: 2026-04-14T21:02:26Z
- **提交信息**: feat: Add routing_replay_out support to MoE kernels and Python API (#3024)

## 📌 Description

Add an optional `routing_replay_out` parameter to all MoE kernel entry
points. When provided (int16 tensor of shape `[N, top_k]`), the routing
kernel writes selected expert IDs per token during MoE routing — inside
the same fused kernel that computes the MoE output. When `None`
(default), zero overhead.

This enables **routing replay** for RL training workflows: an inference
engine (e.g., vLLM) captures which experts were selected for each token
and returns the data alongside the model output, so the training
pipeline can replay the same routing decisions.

The previous Python callback approach in vLLM's router breaks under
`torch.compile` + CUDA graphs (callback is traced once, tensor reference
baked at trace time). This kernel-level approach works correctly with
pre-allocated buffers and CUDA graph replay.

### Changes

**C++ kernel changes:**
- `trtllm_fused_moe_kernel_launcher.cu`: Add `routing_replay_out` field
to `FusedMoeLauncher` base class. Add validation + passthrough in all
entry points (`trtllm_fp8_block_scale_moe`, `trtllm_bf16_moe`,
`trtllm_fp8_per_tensor_scale_moe`, `trtllm_fp4_block_scale_moe`,
`trtllm_mxint4_block_scale_moe`).
- `trtllm_fused_moe_runner.cu`: Add `int16_t* routing_replay_out` to
`Runner::run()`. Pass through to routing data struct for all routing
method paths (DeepSeek, Llama4, Custom/Renormalize, MiniMax2).
- `noAuxTcKernels.cu`: Add `routing_replay_out` to standalone DSV3 fused
routing kernel and `NoAuxTc` entry point.
- Routing kernel writes in `trtllm_fused_moe_routing_deepseek.cu`,
`trtllm_fused_moe_routing_custom.cu`,
`trtllm_fused_moe_routing_llama4.cu`, and `noAuxTcKernels.cu`.

**Python API changes:**
- `core.py`: Add `routing_replay_out` parameter to
`trtllm_fp8_block_scale_moe()`, `trtllm_bf16_moe()`,
`trtllm_bf16_routed_moe()`, internal op functions, fake functions, and
autotuner/launcher kwargs threading.
- `fused_routing_dsv3.py`: Add `routing_replay_out` to
`fused_topk_deepseek()` with int16 dtype validation and relaxed dim0
check (`>=` instead of `==`).

**`routing_replay_out` spec:**
- **dtype**: `torch.int16`
- **shape**: `(num_tokens_or_larger, top_k)` — buffer may be larger than
`num_tokens` for CUDA graph pre-allocation
- **layout**: row-major. `replay[t, k]` = k-th ranked expert ID for
token `t`
- **when None**: zero overhead, kernel skips the write entirely
- **dim0 validation**: `>=` (not `==`) — the kernel determines write
extent from `routing_logits.shape[0]`

## 🔍 Related Issues

vLLM's `--enable-return-routed-experts` for RL training pipelines. The
previous Python callback approach breaks under `torch.compile` + CUDA
graphs.

## 🚀 Pull Request Checklist

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

**New tests:**
- `test_dsv3_fused_routing.py::test_routing_replay_out` — Verifies
replay matches `topk_indices` and `None` has no side effects
-
`test_trtllm_gen_routed_fused_moe.py::test_fp8_block_scale_moe_routing_replay`
— Verifies replay has zero effect on MoE output, IDs are valid, each
token has `top_k` unique experts

**Test plan:**
- [ ] `pytest
tests/model_optimizations/test_dsv3_fused_routing.py::test_routing_replay_out
-v`
- [ ] `pytest
tests/moe/test_trtllm_gen_routed_fused_moe.py::test_fp8_block_scale_moe_routing_replay
-v`
- [ ] Verify zero overhead when `routing_replay_out=None` (benchmark
with and without)
- [ ] Validated end-to-end with vLLM on Super MXFP8 (2 nodes, TP=4,
DP=2) — non-zero routing data at 256 concurrency

## Reviewer Notes

- The dim0 validation uses `>=` instead of `==` intentionally — this
allows CUDA graph pre-allocation of oversized buffers. The kernel
determines write extent from `routing_logits.shape[0]`.
- Also includes `docs/vllm_routing_replay_integration.md` as an
integration guide for vLLM consumers.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added optional `routing_replay_out` parameter to TensorRT-LLM MoE
operations, enabling recording of selected expert indices during routing
for each token.

* **Documentation**
  * Added guide for integrating routing replay with vLLM's MoE workflow.

* **Tests**
* Added validation tests for routing replay functionality across
DeepSeek V3 and FP8 block-scale MoE kernels.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Tomer Natan <tbarnatan@oci-hsg-cs-001-login-02.cm.cluster>
Co-authored-by: Alex Yang <aleyang@nvidia.com>
Co-authored-by: Claude Opus 4.6 (1M context) <noreply@anthropic.com>

### [dfcafb1](https://github.com/flashinfer-ai/flashinfer/commit/dfcafb1219e6aa25a65d80b0f3150a5d67eaf1c6)

- **作者**: Alex Yang
- **时间**: 2026-04-14T20:41:27Z
- **提交信息**: fix: std option for comm device side compilation regression (#3056)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

## 🔍 Related Issues

https://github.com/flashinfer-ai/flashinfer/pull/2772

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

* **Refactor**
* Updated internal CUDA device code for improved compatibility and
consistency in quantization and memory computation kernels used in
AllReduce fusion operations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [c60699d](https://github.com/flashinfer-ai/flashinfer/commit/c60699d3f12f4436cbf9de339c3393107b705e7e)

- **作者**: Alex Yang
- **时间**: 2026-04-14T19:01:38Z
- **提交信息**: docs: document MAX_JOBS env var and its interaction with FLASHINFER_N… (#3060)

…VCC_THREADS

Add MAX_JOBS to the Quick Reference table and Environment Variables
section. Document that total compilation memory pressure is MAX_JOBS ×
FLASHINFER_NVCC_THREADS, and both should be capped for modules with many
kernel variants (e.g. GDN prefill: 64 .cu files) to avoid OOM on
memory-constrained CI machines.

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

* **Documentation**
* Added new `MAX_JOBS` environment variable to control parallel job
execution during compilation, enabling build performance optimization.
* Clarified existing configuration parameter behavior and added guidance
on how compilation memory requirements scale with configuration
settings.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Larry Wu <larwu@nvidia.com>
Co-authored-by: Claude Opus 4.6 (1M context) <noreply@anthropic.com>

### [8c93f92](https://github.com/flashinfer-ai/flashinfer/commit/8c93f924f148cce491982089913e6f3ffb7f8cc8)

- **作者**: Brian K. Ryu
- **时间**: 2026-04-14T17:00:55Z
- **提交信息**: feat: Add backend="b12x" for mm_fp4 on SM120 (#3051)

<!-- .github/pull_request_template.md -->

## 📌 Description

### Summary
- Add a new `backend="b12x"` option for `mm_fp4` targeting SM120 GPUs.
Supports nvfp4 only.
- Port the `b12x` block-scaled NVFP4 dense GEMM kernel using CuTe DSL.
Ported from the [b12x
library](https://github.com/lukealonso/b12x/tree/master)
- On SM120, `backend="auto"` now prefers "b12x" over "cutlass" and
"cudnn" for NVFP4
- SM121 (Spark) is not yet supported pending a `nvidia-cutlass-dsl==4.5`
wheel release.

### Changes
| File | Change |
|---|---|
| `flashinfer/gemm/kernels/dense_blockscaled_gemm_sm120.py` | New SM120
kernel with `wrapper()` method for FlashInfer's TVM-FFI compile
interface |
| `flashinfer/cute_dsl/utils.py` | Add `sm120_make_smem_layout_sfa/sfb`
with 64-aligned tile support |
| `flashinfer/gemm/gemm_base.py` | New `_b12x_gemm_fp4_requirement`,
`_b12x_gemm_fp4_runner` (separate cache and runner class),
`_select_default_sm120_mma_tiler` heuristic, SM120 auto-selection in
heuristic |
| `flashinfer/gemm/__init__.py` | Export
`Sm120BlockScaledDenseGemmKernel` |
| `tests/gemm/test_mm_fp4.py` | Add `"b12x"` to backend parametrize with
SM120-only skip |
| `benchmarks/routines/gemm.py` | Add `"b12x"` to CLI choices and
autotune-supported backends, remove redundant backend guard in
`run_backend` |

### Performance numbers on RTX 5090 (SM120)
Geomean speedup vs CUTLASS:
- cuDNN: **1.02x**
- b12x: **1.20x**

`b12x` performance is particularly strong on small-M (decode) shapes
where the underfill tiles (64x64, 64x128) kick in — many of those show
1.3-1.6x speedup. The larger shapes are roughly at parity

<details>
<summary>Click to view performance comparisons on between
backends</summary>

| M | N | K | cuDNN (us) | CUTLASS (us) | b12x (us) | best |
|---:|---:|---:|---:|---:|---:|---|
| 1 | 512 | 7168 | 18.448 | 24.240 | 13.680 | **b12x** |
| 4 | 512 | 7168 | 18.976 | 24.400 | 13.983 | **b12x** |
| 16 | 512 | 7168 | 19.152 | 24.304 | 14.303 | **b12x** |
| 64 | 512 | 7168 | 19.088 | 24.352 | 15.360 | **b12x** |
| 256 | 512 | 7168 | 21.728 | 24.575 | 25.392 | cuDNN |
| 1024 | 512 | 7168 | 23.519 | 25.232 | 26.592 | cuDNN |
| 1 | 896 | 1024 | 7.056 | 6.512 | 4.720 | **b12x** |
| 4 | 896 | 1024 | 7.232 | 6.608 | 4.976 | **b12x** |
| 16 | 896 | 1024 | 7.232 | 6.544 | 4.944 | **b12x** |
| 64 | 896 | 1024 | 7.152 | 6.432 | 4.993 | **b12x** |
| 256 | 896 | 1024 | 7.360 | 6.640 | 6.656 | CUTLASS |
| 1024 | 896 | 1024 | 7.664 | 6.736 | 6.928 | CUTLASS |
| 1 | 896 | 5120 | 20.192 | 18.144 | 11.200 | **b12x** |
| 8 | 896 | 5120 | 18.624 | 18.208 | 11.424 | **b12x** |
| 64 | 896 | 5120 | 19.008 | 18.224 | 12.560 | **b12x** |
| 512 | 896 | 5120 | 20.192 | 18.864 | 20.032 | CUTLASS |
| 1 | 1024 | 7168 | 18.895 | 24.256 | 14.880 | **b12x** |
| 4 | 1024 | 7168 | 19.231 | 24.592 | 15.744 | **b12x** |
| 16 | 1024 | 7168 | 19.488 | 24.671 | 16.432 | **b12x** |
| 256 | 1024 | 7168 | 23.103 | 24.720 | 25.824 | cuDNN |
| 1024 | 1024 | 7168 | 28.928 | 26.160 | 28.816 | CUTLASS |
| 1 | 1280 | 8192 | 18.287 | 27.872 | 18.191 | **b12x** |
| 8 | 1280 | 8192 | 18.688 | 27.856 | 19.296 | cuDNN |
| 64 | 1280 | 8192 | 18.528 | 27.920 | 19.936 | cuDNN |
| 512 | 1280 | 8192 | 21.328 | 29.040 | 31.599 | cuDNN |
| 1 | 1792 | 5120 | 17.600 | 18.864 | 14.592 | **b12x** |
| 8 | 1792 | 5120 | 17.488 | 18.912 | 14.272 | **b12x** |
| 64 | 1792 | 5120 | 20.063 | 18.832 | 14.976 | **b12x** |
| 512 | 1792 | 5120 | 23.536 | 19.904 | 22.080 | CUTLASS |
| 1 | 2560 | 8192 | 20.304 | 29.328 | 25.520 | cuDNN |
| 8 | 2560 | 8192 | 22.288 | 29.151 | 26.064 | cuDNN |
| 64 | 2560 | 8192 | 19.472 | 29.184 | 26.272 | cuDNN |
| 512 | 2560 | 8192 | 34.128 | 30.752 | 33.871 | CUTLASS |
| 1 | 3584 | 5120 | 21.456 | 22.128 | 19.504 | **b12x** |
| 8 | 3584 | 5120 | 21.071 | 22.111 | 19.520 | **b12x** |
| 64 | 3584 | 5120 | 20.800 | 22.463 | 20.128 | **b12x** |
| 512 | 3584 | 5120 | 26.079 | 24.608 | 24.736 | CUTLASS |
| 1 | 4608 | 7168 | 29.040 | 32.512 | 28.016 | **b12x** |
| 4 | 4608 | 7168 | 28.816 | 32.560 | 28.192 | **b12x** |
| 16 | 4608 | 7168 | 32.399 | 32.992 | 28.559 | **b12x** |
| 64 | 4608 | 7168 | 24.688 | 32.479 | 28.496 | cuDNN |
| 256 | 4608 | 7168 | 35.776 | 34.255 | 35.888 | CUTLASS |
| 1024 | 4608 | 7168 | 68.367 | 71.200 | 67.919 | **b12x** |
| 1 | 5120 | 640 | 7.632 | 6.768 | 5.456 | **b12x** |
| 8 | 5120 | 640 | 7.648 | 6.624 | 5.200 | **b12x** |
| 64 | 5120 | 640 | 7.808 | 6.752 | 5.296 | **b12x** |
| 512 | 5120 | 640 | 8.928 | 8.288 | 7.504 | **b12x** |
| 1 | 5120 | 1024 | 8.240 | 7.728 | 6.272 | **b12x** |
| 8 | 5120 | 1024 | 8.079 | 7.680 | 6.176 | **b12x** |
| 64 | 5120 | 1024 | 8.160 | 7.536 | 5.952 | **b12x** |
| 512 | 5120 | 1024 | 9.136 | 10.368 | 8.784 | **b12x** |
| 1 | 5120 | 1280 | 9.968 | 9.088 | 7.456 | **b12x** |
| 8 | 5120 | 1280 | 9.680 | 9.328 | 7.504 | **b12x** |
| 64 | 5120 | 1280 | 9.775 | 9.008 | 7.280 | **b12x** |
| 512 | 5120 | 1280 | 10.848 | 11.776 | 10.128 | **b12x** |
| 1 | 5120 | 2048 | 12.816 | 12.512 | 10.032 | **b12x** |
| 8 | 5120 | 2048 | 12.640 | 12.160 | 9.888 | **b12x** |
| 64 | 5120 | 2048 | 12.816 | 11.536 | 9.872 | **b12x** |
| 512 | 5120 | 2048 | 13.872 | 14.624 | 13.232 | **b12x** |
| 1 | 5120 | 2560 | 15.024 | 14.384 | 11.760 | **b12x** |
| 8 | 5120 | 2560 | 14.816 | 14.336 | 11.968 | **b12x** |
| 64 | 5120 | 2560 | 14.944 | 13.872 | 11.584 | **b12x** |
| 512 | 5120 | 2560 | 16.400 | 16.592 | 15.887 | **b12x** |
| 1 | 5120 | 4096 | 20.608 | 19.040 | 15.584 | **b12x** |
| 8 | 5120 | 4096 | 20.527 | 18.800 | 15.984 | **b12x** |
| 64 | 5120 | 4096 | 20.784 | 19.280 | 17.168 | **b12x** |
| 512 | 5120 | 4096 | 23.696 | 23.967 | 23.376 | **b12x** |
| 1 | 5120 | 5120 | 24.303 | 23.856 | 19.823 | **b12x** |
| 8 | 5120 | 5120 | 22.415 | 23.663 | 19.840 | **b12x** |
| 64 | 5120 | 5120 | 25.568 | 23.552 | 20.560 | **b12x** |
| 512 | 5120 | 5120 | 29.328 | 30.016 | 29.152 | **b12x** |
| 1 | 5120 | 8192 | 35.887 | 33.903 | 27.616 | **b12x** |
| 8 | 5120 | 8192 | 31.424 | 34.336 | 29.200 | **b12x** |
| 64 | 5120 | 8192 | 36.224 | 34.591 | 31.696 | **b12x** |
| 512 | 5120 | 8192 | 42.111 | 43.791 | 41.440 | **b12x** |
| 1 | 5120 | 16384 | 59.119 | 58.911 | 49.968 | **b12x** |
| 8 | 5120 | 16384 | 59.103 | 58.959 | 50.175 | **b12x** |
| 64 | 5120 | 16384 | 51.456 | 58.864 | 51.407 | **b12x** |
| 512 | 5120 | 16384 | 81.375 | 84.191 | 81.871 | cuDNN |
| 1 | 7168 | 256 | 5.424 | 4.976 | 3.968 | **b12x** |
| 4 | 7168 | 256 | 5.728 | 5.168 | 3.935 | **b12x** |
| 16 | 7168 | 256 | 5.456 | 4.992 | 4.096 | **b12x** |
| 64 | 7168 | 256 | 5.855 | 5.184 | 4.240 | **b12x** |
| 256 | 7168 | 256 | 5.856 | 5.488 | 5.040 | **b12x** |
| 1024 | 7168 | 256 | 9.696 | 12.912 | 10.048 | cuDNN |
| 1 | 7168 | 512 | 7.072 | 7.008 | 5.184 | **b12x** |
| 4 | 7168 | 512 | 7.120 | 6.864 | 5.408 | **b12x** |
| 16 | 7168 | 512 | 6.976 | 6.720 | 5.120 | **b12x** |
| 64 | 7168 | 512 | 7.071 | 6.559 | 5.456 | **b12x** |
| 256 | 7168 | 512 | 7.296 | 7.104 | 6.576 | **b12x** |
| 1024 | 7168 | 512 | 15.280 | 18.000 | 14.752 | **b12x** |
| 4 | 7168 | 2304 | 15.168 | 14.800 | 11.551 | **b12x** |
| 16 | 7168 | 2304 | 14.848 | 14.479 | 11.232 | **b12x** |
| 64 | 7168 | 2304 | 14.528 | 13.712 | 11.423 | **b12x** |
| 256 | 7168 | 2304 | 15.136 | 15.840 | 14.320 | **b12x** |
| 1 | 7168 | 4608 | 25.552 | 25.792 | 19.264 | **b12x** |
| 4 | 7168 | 4608 | 25.200 | 25.184 | 18.560 | **b12x** |
| 16 | 7168 | 4608 | 27.648 | 24.320 | 19.120 | **b12x** |
| 64 | 7168 | 4608 | 25.952 | 24.383 | 22.544 | **b12x** |
| 256 | 7168 | 4608 | 27.984 | 27.328 | 26.480 | **b12x** |
| 1024 | 7168 | 4608 | 70.480 | 72.335 | 69.743 | **b12x** |
| 1 | 7168 | 5120 | 28.063 | 27.552 | 19.552 | **b12x** |
| 8 | 7168 | 5120 | 26.048 | 26.287 | 20.192 | **b12x** |
| 64 | 7168 | 5120 | 27.824 | 25.215 | 23.312 | **b12x** |
| 512 | 7168 | 5120 | 47.567 | 48.175 | 47.648 | cuDNN |
| 1 | 8192 | 1024 | 10.352 | 9.775 | 7.376 | **b12x** |
| 8 | 8192 | 1024 | 10.367 | 9.456 | 7.696 | **b12x** |
| 64 | 8192 | 1024 | 9.568 | 9.233 | 7.712 | **b12x** |
| 512 | 8192 | 1024 | 14.016 | 15.264 | 13.776 | **b12x** |
| 1 | 8192 | 2048 | 14.832 | 14.688 | 10.640 | **b12x** |
| 8 | 8192 | 2048 | 14.591 | 14.080 | 10.560 | **b12x** |
| 64 | 8192 | 2048 | 14.128 | 13.104 | 11.936 | **b12x** |
| 512 | 8192 | 2048 | 22.272 | 23.280 | 22.080 | **b12x** |
| 1 | 8192 | 3584 | 21.087 | 21.872 | 15.727 | **b12x** |
| 8 | 8192 | 3584 | 22.272 | 21.264 | 15.808 | **b12x** |
| 64 | 8192 | 3584 | 20.448 | 19.200 | 18.336 | **b12x** |
| 512 | 8192 | 3584 | 35.423 | 35.023 | 35.344 | CUTLASS |
| 1 | 8192 | 4096 | 22.880 | 23.872 | 16.416 | **b12x** |
| 8 | 8192 | 4096 | 25.312 | 23.663 | 18.352 | **b12x** |
| 64 | 8192 | 4096 | 22.176 | 21.184 | 20.624 | **b12x** |
| 512 | 8192 | 4096 | 39.392 | 38.928 | 39.552 | CUTLASS |
| 1 | 8192 | 7168 | 37.663 | 38.783 | 26.863 | **b12x** |
| 8 | 8192 | 7168 | 37.888 | 37.296 | 27.663 | **b12x** |
| 64 | 8192 | 7168 | 37.584 | 34.224 | 32.416 | **b12x** |
| 512 | 8192 | 7168 | 67.824 | 70.751 | 67.759 | **b12x** |
| 1 | 8192 | 8192 | 40.288 | 42.784 | 29.472 | **b12x** |
| 8 | 8192 | 8192 | 39.487 | 42.191 | 31.904 | **b12x** |
| 64 | 8192 | 8192 | 38.159 | 35.663 | 39.263 | CUTLASS |
| 512 | 8192 | 8192 | 76.895 | 80.655 | 77.391 | cuDNN |
| 1 | 8192 | 14336 | 69.615 | 70.624 | 52.720 | **b12x** |
| 8 | 8192 | 14336 | 69.647 | 70.175 | 53.615 | **b12x** |
| 64 | 8192 | 14336 | 61.919 | 67.904 | 58.223 | **b12x** |
| 512 | 8192 | 14336 | 124.814 | 128.014 | 124.735 | **b12x** |
| 1 | 8192 | 28672 | 134.031 | 135.231 | 100.127 | **b12x** |
| 8 | 8192 | 28672 | 133.935 | 131.982 | 102.047 | **b12x** |
| 64 | 8192 | 28672 | 108.863 | 127.887 | 122.463 | cuDNN |
| 512 | 8192 | 28672 | 233.486 | 243.533 | 232.621 | **b12x** |
| 1 | 9216 | 7168 | 41.200 | 45.840 | 29.296 | **b12x** |
| 4 | 9216 | 7168 | 41.232 | 46.031 | 29.584 | **b12x** |
| 16 | 9216 | 7168 | 39.008 | 42.911 | 32.912 | **b12x** |
| 64 | 9216 | 7168 | 37.999 | 35.135 | 33.151 | **b12x** |
| 256 | 9216 | 7168 | 42.655 | 39.839 | 41.536 | CUTLASS |
| 1024 | 9216 | 7168 | 125.534 | 128.511 | 125.279 | **b12x** |
| 1 | 10240 | 8192 | 47.807 | 50.847 | 35.328 | **b12x** |
| 8 | 10240 | 8192 | 47.535 | 51.615 | 35.887 | **b12x** |
| 64 | 10240 | 8192 | 38.944 | 38.336 | 44.496 | CUTLASS |
| 512 | 10240 | 8192 | 84.383 | 86.399 | 83.343 | **b12x** |



</details>

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

## 🔍 Related Issues

#3013 
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

* **New Features**
* Added "b12x" FP4 backend with SM120-optimized execution and a new
SM120 block-scaled dense GEMM kernel.
* Registered SM120 kernel for CuTe-DSL-enabled builds and added
SM120-specific shared-memory layouts.

* **Enhancements**
* Improved SM120 tiling/auto-selection heuristics for small-M and
low-occupancy scenarios.

* **Tests**
* Extended FP4 tests to include "b12x" with SM120-specific preconditions
and skip logic.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 4.6 (1M context) <noreply@anthropic.com>

### [8063bc5](https://github.com/flashinfer-ai/flashinfer/commit/8063bc5feb5a5fab2c6bfc5e496ac4b286c8f450)

- **作者**: Alex Yang
- **时间**: 2026-04-14T16:25:41Z
- **提交信息**: bump version to 0.6.8 (#3042)

## Description

Bump version to 0.6.8 for release.

## Related Issues (Gated-by PRs)


https://github.com/flashinfer-ai/flashinfer/issues?q=is%3Aopen+label%3Av0.6.8

## Reviewer Notes

**API changes review**

API changes since v0.6.7.post3

```diff
$ git diff v0.6.7.post3..main -- "*.py" | grep -B5 -A20 "@flashinfer_api"
-            Union[torch.Tensor, Tuple[torch.Tensor, torch.Tensor]]
-        ] = None,
+        kv_cache_sf: Optional[Tuple[torch.Tensor, torch.Tensor]] = None,
     ) -> Tuple[torch.Tensor, torch.Tensor]: ...
 
     @flashinfer_api
@@ -1227,9 +1232,7 @@ class BatchDecodeWithPagedKVCacheWrapper:
         sinks: Optional[torch.Tensor] = None,
         q_len_per_req: Optional[int] = 1,
         skip_softmax_threshold_scale_factor: Optional[float] = None,
-        kv_block_scales: Optional[
-            Union[torch.Tensor, Tuple[torch.Tensor, torch.Tensor]]
-        ] = None,
+        kv_cache_sf: Optional[Tuple[torch.Tensor, torch.Tensor]] = None,
     ) -> Union[torch.Tensor, Tuple[torch.Tensor, torch.Tensor]]:
         r"""Compute batch decode attention between query and paged kv cache.
 
@@ -1288,14 +1291,22 @@ class BatchDecodeWithPagedKVCacheWrapper:
             enable_pdl = device_support_pdl(q.device)
         k_cache, v_cache = _unpack_paged_kv_cache(paged_kv_cache, self._kv_layout)
 
-        # Unpack kv_block_scales
+        if (
+            k_cache.dtype == torch.uint8 or v_cache.dtype == torch.uint8
+        ) and kv_cache_sf is None:
+            raise ValueError("kv_cache_sf must be provided for NVFP4 KV cache.")
--
 
     return SimpleNamespace(gdn_prefill=gdn_prefill)
 
 
-def chunk_gated_delta_rule_hopper(
+@flashinfer_api
+def chunk_gated_delta_rule(
     q: torch.Tensor,
     k: torch.Tensor,
     v: torch.Tensor,
@@ -104,6 +106,9 @@ def chunk_gated_delta_rule_hopper(
     use_qk_l2norm_in_kernel: bool = False,
     output: Optional[torch.Tensor] = None,
     output_state: Optional[torch.Tensor] = None,
+    state_checkpoints: Optional[torch.Tensor] = None,
+    checkpoint_cu_starts: Optional[torch.Tensor] = None,
+    checkpoint_every_n_tokens: int = 0,
 ) -> Union[torch.Tensor, Tuple[torch.Tensor, torch.Tensor]]:
     r"""Chunked Gated Delta Rule (GDN) attention for prefill.
 
@@ -111,12 +116,82 @@ def chunk_gated_delta_rule_hopper(
     training and inference. Supports both GQA (grouped query attention) and GVA
     (grouped value attention) configurations.
 
+    Args:
+        q (torch.Tensor):
--
-
-@backend_requirement(
-    {},
-    common_check=_check_gdn_prefill,
-)
-@flashinfer_api
-def chunk_gated_delta_rule(
-    q: torch.Tensor,
-    k: torch.Tensor,
-    v: torch.Tensor,
-    g: Optional[torch.Tensor] = None,
-    beta: Optional[torch.Tensor] = None,
-    scale: Optional[float] = None,
-    initial_state: Optional[torch.Tensor] = None,
-    output_final_state: bool = False,
-    cu_seqlens: Optional[torch.Tensor] = None,
-    use_qk_l2norm_in_kernel: bool = False,
-    output: Optional[torch.Tensor] = None,
-    output_state: Optional[torch.Tensor] = None,
-) -> Union[torch.Tensor, Tuple[torch.Tensor, torch.Tensor]]:
-    r"""Chunked Gated Delta Rule (GDN) attention for prefill.
-
-    Args:
-        q (torch.Tensor):
-            Queries of shape ``[total_seq_len, num_q_heads, head_size]``.
-            Must be contiguous and on CUDA.
--
+
+@backend_requirement(
+    {},
+    common_check=_check_group_gemm_nvfp4_nt_groupwise_problem_size,
+)
+@flashinfer_api
+def group_gemm_nvfp4_nt_groupwise(
+    a: torch.Tensor,  # (cum_m, k)
+    b: torch.Tensor,  # (batch_size, n, k // 2)
+    a_scale: torch.Tensor,  # (cum_m_padded, k // 16)
+    b_scale: torch.Tensor,  # (batch_size, n_padded, k // 16)
+    m_indptr: torch.Tensor,  # (batch_size + 1, )
+    alpha: Optional[torch.Tensor] = None,  # (batch_size, )
+    tile_m: int = 128,
+    tile_n: int = 128,
+    tile_k: int = 128,
+    out: Optional[torch.Tensor] = None,  # (cum_m, n)
+    out_dtype: Optional[torch.dtype] = None,
+) -> torch.Tensor:
+    r"""Perform group GEMM with NVFP4 data types using groupwise scaling. Currently only implemented on NVIDIA
+    Blackwell Geforce, and DGX Spark architectures.
+
+    Parameters
+    ----------
+    a: torch.Tensor
+        Row-major input tensor, shape ``(cum_m, k // 2)``, data type is ``torch.uint8`` (packed NVFP4).
--
+        "Unsupported output dtype for fused_rmsnorm_silu: "
+        f"{dtype}. Supported dtypes: bfloat16, float8_e4m3fn, float4_e2m1fn_x2"
+    )
+
+
+@flashinfer_api
+def fused_rmsnorm_silu(
+    input: torch.Tensor,
+    weight: torch.Tensor,
+    eps: float = 1e-6,
+    out: Optional[torch.Tensor] = None,
+    block_scale: Optional[torch.Tensor] = None,
+) -> Union[torch.Tensor, tuple]:
+    r"""Fused RMSNorm + SiLU activation.
+
+    ``out[i] = SiLU(RMSNorm(input[i], weight, eps))``
+
+    where ``SiLU(x) = x / (1 + exp(-x))``
+
+    Optimized for SM100 (B200) for WAN VAE decoder problem sizes.
+    Other shapes and architectures (SM80+) use conservative fallback heuristics.
+
+    Parameters
+    ----------
+    input: torch.Tensor
+        Input tensor, shape ``(num_tokens, hidden_size)``, dtype ``bfloat16``.
--
+            f"(sf_vec_size=16, sf_use_ue8m0=False) for NVFP4, "
+            f"(sf_vec_size=32, sf_use_ue8m0=True) for MXFP4."
+        )
+
+
 @flashinfer_api
 def block_scale_interleave(unswizzled_sf: torch.Tensor) -> torch.Tensor:
     """Swizzle block scale tensor for FP4 format.
@@ -833,55 +931,95 @@ def nvfp4_quantize(
     do_shuffle=False,
     sf_vec_size=16,
     enable_pdl=None,
+    backend: str = "cuda",
 ):
     """
     Quantize input tensor to NVFP4 format.
 
     Parameters:
-        a (torch.Tensor): Input tensor of shape [M, K] with dtype fp16/bf16.
+        a (torch.Tensor): Input tensor of shape [M, K] with dtype fp16/bf16/float8_e4m3fn.
         a_global_sf (torch.Tensor): Global scale factor of shape [1] with dtype float32.
         sfLayout (SfLayout, optional): Scale factor layout. Defaults to SfLayout.layout_128x4.
         do_shuffle (bool, optional): Whether to shuffle the scale factors. Defaults to False. Only TRTLLM backend needs to shuffle the tensor B scale factors.
         sf_vec_size (int, optional): Scale factor vector size. Defaults to 16.
         enable_pdl (Optional[bool], optional): Whether to enable PDL (Programmatic Dependent Launch).
             If None, automatically detects based on device capability. Defaults to None.
--
 
-    return kv_cache_fp4, kv_block_scales, k_gs_ret, v_gs_ret
+    return kv_cache_fp4, kv_cache_sf, k_gs_ret, v_gs_ret
 
 
 @flashinfer_api
diff --git a/flashinfer/quantization/kernels/__init__.py b/flashinfer/quantization/kernels/__init__.py
index 7e99b74a..0f30455b 100644
--- a/flashinfer/quantization/kernels/__init__.py
+++ b/flashinfer/quantization/kernels/__init__.py
@@ -27,6 +27,7 @@ SM100+ (Blackwell) GPUs and the nvidia-cutlass-dsl package.
 """
 
 from .mxfp4_quantize import (
+    MXFP4QuantizeLinearKernel,
     MXFP4QuantizeSwizzledKernel,
     mxfp4_quantize_cute_dsl,
 )
@@ -35,11 +36,18 @@ from .mxfp8_quantize import (
     MXFP8QuantizeSwizzledKernel,
     mxfp8_quantize_cute_dsl,
 )
+from .nvfp4_quantize import (
+    NVFP4QuantizeSwizzledKernel,
+    nvfp4_quantize_cute_dsl,
+)
--
+        )
+
+        return compiled_kernel, swizzled_obj.rows_per_block
 
 
 @flashinfer_api
 def mxfp4_quantize_cute_dsl(
     input: torch.Tensor,
+    sf_layout: int = SF_LAYOUT_128x4,
     enable_pdl: bool | None = None,
 ) -> Tuple[torch.Tensor, torch.Tensor]:
     """
     Quantize input tensor to MXFP4 format using CuTe-DSL kernel.
 
-    This is a GPU implementation matching FlashInfer's mxfp4_quantize() behavior:
-    - Global scale computed as (448 * 6) / max(|input|)
-    - UE8M0 scale factors
-    - E2M1 output format (4-bit, 2 values per byte)
-    - Swizzled (128x4) scale factor layout
+    This is a GPU implementation with dual-path optimization:
+    - LINEAR layout: flat SF-block based iteration with adaptive 1T/4T per SF
+      block dispatch — uses 4T/SF on low-SM GPUs (<=80 SMs) for coalesced
+      memory access, and 1T/SF on high-SM GPUs where enough SMs generate
+      sufficient outstanding memory requests
+    - SWIZZLED layout: row-based iteration with padding fast path (optimized)
 
--
+    )
+
+    return compiled_kernel, kernel_obj.rows_per_block
+
+
+@flashinfer_api
+def nvfp4_quantize_cute_dsl(
+    input: torch.Tensor,
+    global_scale: torch.Tensor,
+    sf_layout: int = SF_LAYOUT_128x4,
+    enable_pdl: bool | None = None,
+) -> Tuple[torch.Tensor, torch.Tensor]:
+    """
+    Quantize input tensor to NVFP4 format using CuTe-DSL kernel.
+
+    This is a GPU implementation matching FlashInfer's nvfp4_quantize() behavior:
+    - E4M3 scale factors (FP8)
+    - E2M1 output format (4-bit, 2 values per byte)
+    - Supports 128x4, 8x4, and linear scale factor layouts
+    - sf_vec_size=16
+
+    The kernel is compiled once per (K, dtype, sf_layout, pdl) combination and
+    handles varying M (batch size) at runtime without recompilation.
+
+    Args:
+        input: Input tensor of shape [M, K] with dtype fp16/bf16/float8_e4m3fn
```

prefill.py `BatchPrefillWithPagedKVCacheWrapper.run()` and
`trtllm_batch_context_with_kv_cache()` overload stubs fall outside the
grep window above:

```diff
$ git diff v0.6.7.post3..main -- 'flashinfer/prefill.py' | grep -B5 -A10 'kv_block_scales|kv_cache_sf'
         if backend == "cudnn":
@@ -2098,9 +2104,7 @@ class BatchPrefillWithPagedKVCacheWrapper:
         enable_pdl: Optional[bool] = None,
         window_left: Optional[int] = None,
         sinks: Optional[torch.Tensor] = None,
-        kv_block_scales: Optional[
-            Union[torch.Tensor, Tuple[torch.Tensor, torch.Tensor]]
-        ] = None,
+        kv_cache_sf: Optional[Tuple[torch.Tensor, torch.Tensor]] = None,
         skip_softmax_threshold_scale_factor: Optional[float] = None,
     ) -> torch.Tensor: ...
 
@@ -2118,9 +2122,7 @@ class BatchPrefillWithPagedKVCacheWrapper:
         enable_pdl: Optional[bool] = None,
         window_left: Optional[int] = None,
         sinks: Optional[torch.Tensor] = None,
-        kv_block_scales: Optional[
-            Union[torch.Tensor, Tuple[torch.Tensor, torch.Tensor]]
-        ] = None,
+        kv_cache_sf: Optional[Tuple[torch.Tensor, torch.Tensor]] = None,
         skip_softmax_threshold_scale_factor: Optional[float] = None,
     ) -> Tuple[torch.Tensor, torch.Tensor]: ...
 
@@ -2139,9 +2141,7 @@ class BatchPrefillWithPagedKVCacheWrapper:
         enable_pdl: Optional[bool] = None,
         window_left: Optional[int] = None,
         sinks: Optional[torch.Tensor] = None,
-        kv_block_scales: Optional[
-            Union[torch.Tensor, Tuple[torch.Tensor, torch.Tensor]]
-        ] = None,
+        kv_cache_sf: Optional[Tuple[torch.Tensor, torch.Tensor]] = None,
         skip_softmax_threshold_scale_factor: Optional[float] = None,
     ) -> Union[torch.Tensor, Tuple[torch.Tensor, torch.Tensor]]:
         r"""Compute batch prefill/append attention between query and paged kv-cache.
@@ -2181,6 +2181,21 @@ class BatchPrefillWithPagedKVCacheWrapper:
         enable_pdl : bool
             Whether to enable Programmatic Dependent Launch (PDL). See https://docs.nvidia.com/cuda/cuda-c-programming-guide/#programmatic-dependent-launch-and-synchronization
             Only supported for >= sm90, and currently only for FA2 and CUDA core decode.
+        kv_cache_sf : Optional[Tuple[torch.Tensor, torch.Tensor]]
+            Per-block scale factors for NVFP4 KV cache, as a tuple of ``(k_scales, v_scales)``.
+            Scale tensors must follow the same :attr:`kv_layout` as the KV cache:
+
+            * **HND**: ``[num_pages, num_kv_heads, page_size, head_dim // 16]``
+            * **NHD**: ``[num_pages, page_size, num_kv_heads, head_dim // 16]``
+
+            Both tensors have dtype ``torch.float8_e4m3fn``. ``k_scales`` uses a linear
+            (row-major) layout, while ``v_scales`` must use TRT-LLM's 4-token interleaved
+            layout within each ``[page_size, head_dim // 16]`` tile. Use
+            :func:`flashinfer.fp4_quantization.nvfp4_quantize_paged_kv_cache` to produce
--
         Union[torch.Tensor, Tuple[torch.Tensor, torch.Tensor]]
@@ -2212,14 +2227,22 @@ class BatchPrefillWithPagedKVCacheWrapper:
                     f"where total_tokens = qo_indptr[-1]."
                 )
 
-        # Unpack kv_block_scales
+        if (
+            k_cache.dtype == torch.uint8 or v_cache.dtype == torch.uint8
+        ) and kv_cache_sf is None:
+            raise ValueError("kv_cache_sf must be provided for NVFP4 KV cache.")
         key_block_scales = None
         value_block_scales = None
-        if kv_block_scales is not None:
-            if isinstance(kv_block_scales, tuple):
-                key_block_scales, value_block_scales = kv_block_scales
-            else:
-                key_block_scales, value_block_scales = kv_block_scales.unbind(dim=1)
+        if kv_cache_sf is not None:
+            if (
+                not isinstance(kv_cache_sf, (tuple, list))
+                or len(kv_cache_sf) != 2
+                or not all(torch.is_tensor(x) for x in kv_cache_sf)
+            ):
+                raise TypeError(
+                    "kv_cache_sf must be a tuple/list of two tensors: (k_scales, v_scales)."
+                )
+            key_block_scales, value_block_scales = kv_cache_sf
 
         o_dtype = self._cached_o_data_type
         if out is not None and out.dtype != o_dtype:
@@ -2265,7 +2288,7 @@ class BatchPrefillWithPagedKVCacheWrapper:
 
         # For NVFP4 KV (uint8 packed), v_cache last dim is head_dim//2;
         # use q's head_dim for output instead
-        out_head_dim = q.shape[-1] if kv_block_scales is not None else v_cache.shape[-1]
+        out_head_dim = q.shape[-1] if kv_cache_sf is not None else v_cache.shape[-1]
         if out is None:
             # Use cached output data type if available (for FP8 attention with FP16 output)
             out_dtype = getattr(self, "_cached_o_data_type", None) or q.dtype
@@ -2355,7 +2378,19 @@ class BatchPrefillWithPagedKVCacheWrapper:
                 enable_pdl,
             ]
             if self._jit_module is not None:
-                run_args.extend(list(args))
+                run_args.extend(
+                    prepare_jit_additional_args(
--
     attention_sinks: Optional[torch.Tensor] = None,
@@ -3731,9 +3781,7 @@ def trtllm_batch_context_with_kv_cache(
     kv_layout: str = "HND",
     enable_pdl: Optional[bool] = None,
     sinks: Optional[List[torch.Tensor]] = None,
-    kv_block_scales: Optional[
-        Union[torch.Tensor, Tuple[torch.Tensor, torch.Tensor]]
-    ] = None,
+    kv_cache_sf: Optional[Tuple[torch.Tensor, torch.Tensor]] = None,
     skip_softmax_threshold_scale_factor: Optional[float] = None,
     uses_shared_paged_kv_idx: bool = True,
 ) -> Union[torch.Tensor, FP4Tensor]:
@@ -3800,11 +3848,21 @@ def trtllm_batch_context_with_kv_cache(
         data copy overhead. Use ``HND`` for better performance.
     sinks : Optional[List[torch.Tensor]] = None
         additional value per head in the denominator of the softmax.
-    kv_block_scales : Optional[Union[torch.Tensor, Tuple[torch.Tensor, torch.Tensor]]] = None
-        Per-block scale factors for NVFP4 KV cache. Either a tuple of (k_scales, v_scales) or
-        a single tensor with shape ``[num_pages, 2, ...]`` that will be unbound along dim=1.
-        Each scale tensor has shape ``[num_pages, num_kv_heads, page_size, head_dim // 16]``
-        in HND layout, with dtype ``torch.float8_e4m3fn``.
+    kv_cache_sf : Optional[Tuple[torch.Tensor, torch.Tensor]] = None
+        Per-block scale factors for NVFP4 KV cache, as a tuple of ``(k_scales, v_scales)``.
+        Scale tensors must follow the same :attr:`kv_layout` as the KV cache:
+
+        * **HND**: ``[num_pages, num_kv_heads, page_size, head_dim // 16]``
+        * **NHD**: ``[num_pages, page_size, num_kv_heads, head_dim // 16]``
+
+        Both tensors have dtype ``torch.float8_e4m3fn``. ``k_scales`` uses a linear
+        (row-major) layout, while ``v_scales`` must use TRT-LLM's 4-token interleaved
+        layout within each ``[page_size, head_dim // 16]`` tile. Use
+        :func:`flashinfer.fp4_quantization.nvfp4_quantize_paged_kv_cache` to produce
--
 
@@ -3845,20 +3903,22 @@ def trtllm_batch_context_with_kv_cache(
             # it doesn't change underlying storage
             k_cache, v_cache = kv_cache.unbind(dim=1)
 
-    # Unpack kv_block_scales
+    if (
+        k_cache.dtype == torch.uint8 or v_cache.dtype == torch.uint8
+    ) and kv_cache_sf is None:
+        raise ValueError("kv_cache_sf must be provided for NVFP4 KV cache.")
     key_block_scales = None
     value_block_scales = None
-    if kv_block_scales is not None:
-        if isinstance(kv_block_scales, tuple):
-            key_block_scales, value_block_scales = kv_block_scales
-        else:
-            if kv_block_scales.shape[1] == 1:
-                key_block_scales, value_block_scales = kv_block_scales, kv_block_scales
-            else:
-                assert kv_block_scales.shape[1] == 2, (
-                    "When kv_block_scales is a single tensor, the second dimension must be 1 or 2"
-                )
-                key_block_scales, value_block_scales = kv_block_scales.unbind(dim=1)
+    if kv_cache_sf is not None:
+        if (
+            not isinstance(kv_cache_sf, (tuple, list))
+            or len(kv_cache_sf) != 2
+            or not all(torch.is_tensor(x) for x in kv_cache_sf)
+        ):
+            raise TypeError(
+                "kv_cache_sf must be a tuple/list of two tensors: (k_scales, v_scales)."
+            )
+        key_block_scales, value_block_scales = kv_cache_sf
 
     # Convert NHD layout to HND if necessary
     if kv_layout == "NHD":
```

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-04-15
**监控日期**: 2026-04-14
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3379
- **最后更新**: 2026-04-14T22:20:53Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: William Lin

## AI分析总结

根据提供的仓库信息与提交记录，结合README摘要中提到的项目名称 **FastVideo**（专注于视频处理与AI推理的高效工具），以下是昨日更新的分析总结：

---

### 1. **主要更新类型**
- **功能新增**：本次提交明确标记为 `[feat]`，属于功能增强类更新。

### 2. **关键变更点及其与项目整体方向的关系**
- **变更点**：扩展了命令行接口（CLI）的支持，这是“改进API”系列更新的第三部分（`[3/n]`）。
- **与项目方向的关系**：FastVideo 旨在提供高效的视频处理与AI推理工具。增强CLI支持直接符合其**提升用户体验和易用性**的目标，让用户能更灵活地通过命令行调用功能，降低使用门槛，并支持自动化集成。

### 3. **对项目的影响和潜在意义**
- **积极影响**：
  - **提升可用性**：CLI的扩展使工具更适合脚本化、批量处理或集成到其他工作流中。
  - **扩大用户群**：吸引更多开发者、研究人员或需要自动化视频处理的用户。
- **潜在意义**：为后续可能推出的**API标准化、云服务集成或第三方插件**奠定基础。

### 4. **值得关注的技术点**
- **API与CLI的协同设计**：如何保持API与CLI在功能上的一致性，同时确保CLI的简洁性。
- **向后兼容性**：在扩展CLI时是否会影响现有命令行参数或行为。
- **错误处理与提示**：CLI通常需要更友好的错误信息和帮助文档。

### 5. **基于项目背景的提交影响分析**
- README中强调“Quick Start”和“Documentation”，表明项目重视**快速上手和易用性**。本次提交通过扩展CLI支持，**直接强化了快速启动和命令行操作的体验**，与项目目标高度一致。
- 作为“Improve API”系列的一部分，这显示项目正**系统性地优化接口层**，可能为未来更复杂的视频处理管道或模型部署做准备。
- 结合项目可能涉及的AI推理场景，CLI的增强有助于**促进批量推理、实验迭代和生产力提升**，推动项目向更专业、可集成的方向发展。

---

**总结**：昨日更新是FastVideo项目在提升用户体验和工具易用性方向上的重要一步，通过扩展CLI支持来强化命令行操作能力，符合其高效视频处理工具的定位，并为未来的集成与自动化应用铺平道路。

## 详细提交记录

### [88a5a93](https://github.com/hao-ai-lab/FastVideo/commit/88a5a933abfc28d1094ad19ec4688c48af0ec77d)

- **作者**: William Lin
- **时间**: 2026-04-14T22:20:47Z
- **提交信息**: [feat] [3/n] Improve API: extend support to cli (#1226)

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-04-15
**监控日期**: 2026-04-14
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 33328
- **最后更新**: 2026-04-14T21:37:33Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 3
- **主要提交者**: Alexey Zolotenkov, YiYi Xu, Sayak Paul

## AI分析总结

根据提供的提交记录和README摘要，以下是对 `huggingface/diffusers` 仓库昨日更新的分析总结：

### 1. 主要更新类型
- **文档更新**：新增模块化文档（提交1）。
- **Bug修复**：修复Qwen Image DreamBooth训练中的批次排序问题（提交4）。
- **测试优化**：修复已弃用注意力处理器测试（提交3），并标记CLIP相关测试为预期失败（提交2）。

### 2. 关键变更点及其与项目整体方向的关系
- **模块化文档新增**：为“agent”功能添加文档，符合项目作为**扩散模型库**的定位，旨在提升易用性和开发者体验。
- **DreamBooth修复**：针对Qwen Image模型的训练批次问题修复，强化了项目对**定制化图像生成**（如DreamBooth微调）的支持。
- **测试稳定性提升**：通过修复和标记测试，确保代码可靠性，体现项目对**持续集成和代码质量**的重视。

### 3. 对项目的影响和潜在意义
- **开发者体验提升**：模块化文档帮助用户更好地理解和使用agent功能，降低入门门槛。
- **训练稳定性增强**：修复DreamBooth批次排序问题可避免训练错误，提升模型微调效果。
- **测试效率优化**：减少因测试失败导致的开发干扰，加速迭代进程。

### 4. 值得关注的技术点
- **Qwen Image DreamBooth训练**：涉及多模态模型（图像+文本）的微调技术，是扩散模型应用的前沿方向。
- **注意力处理器测试**：反映项目内部API的演进，需关注旧版本兼容性策略。
- **CLIP相关测试标记**：可能暗示CLIP模型集成存在临时性问题，需后续跟进修复。

### 5. 基于项目背景的提交影响分析
- **项目背景**：Diffusers是一个专注于**扩散模型**（如Stable Diffusion）的库，支持训练、推理和定制化生成。
- **发展影响**：
  - 文档和测试更新**巩固项目基础**，提升长期维护性。
  - DreamBooth修复**强化实用场景支持**，吸引更多用户进行个性化模型训练。
  - 整体更新体现项目在**快速迭代中兼顾稳定性**，平衡新功能开发与代码健康度。

---
**总结**：昨日更新以**文档完善、Bug修复和测试优化**为主，虽无重大功能新增，但通过提升代码健壮性和用户体验，支持项目作为扩散模型核心库的持续发展。

## 详细提交记录

### [e9c092d](https://github.com/huggingface/diffusers/commit/e9c092d88626b167b13b15c5a64c8fbf06634f54)

- **作者**: YiYi Xu
- **时间**: 2026-04-14T17:43:26Z
- **提交信息**: [agent] add modular doc (#13410)

* merge

* update based on feedback

---------

Co-authored-by: yiyi@huggingface.co <yiyi@ip-26-0-160-103.ec2.internal>

### [f65f135](https://github.com/huggingface/diffusers/commit/f65f135f649790eb3786d927a2f9457c46d6705a)

- **作者**: Sayak Paul
- **时间**: 2026-04-14T17:03:25Z
- **提交信息**: [tests] xfail clip related issues. (#13454)

xfail clip related issues./

### [273b445](https://github.com/huggingface/diffusers/commit/273b445426f05297381fc4b3bfaf9af6a33cacb0)

- **作者**: Sayak Paul
- **时间**: 2026-04-14T16:35:39Z
- **提交信息**: [tests] fix deprecated attention processor testing. (#13469)

fix deprecated attention processor testing.

### [526498d](https://github.com/huggingface/diffusers/commit/526498d219dac01a3dc6261b0ba9d3a929e83867)

- **作者**: Alexey Zolotenkov
- **时间**: 2026-04-14T12:30:37Z
- **提交信息**: Fix Qwen Image DreamBooth prior-preservation batch ordering (#13441)

Fix Qwen Image DreamBooth prior-preservation batching

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-04-15
**监控日期**: 2026-04-14
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 394
- **最后更新**: 2026-04-14T03:27:26Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-04-15
**监控日期**: 2026-04-14
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12230
- **最后更新**: 2026-04-14T17:33:48Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Zhongjie Duan

## AI分析总结

根据提供的提交记录和README摘要，以下是针对昨日更新的分析总结：

---

### 1. **主要更新类型**
- **版本发布**：本次提交（`45d973e`）是一个版本更新，将项目升级至 **v2.0.8**。这通常属于**功能迭代或Bug修复**的常规发布，可能包含多项内部改进。

### 2. **关键变更点及其与项目整体方向的关系**
- **版本号提升**：从 `2.0.x` 升级到 `2.0.8`，表明项目处于**稳定迭代阶段**，专注于增量优化和问题修复。
- **与项目方向的关系**：  
  - 根据README，DiffSynth-Studio 是一个基于扩散模型的合成工具（如Logo动画所示），旨在提供高效的生成能力。  
  - 此次更新可能进一步**增强稳定性、兼容性或功能完整性**，符合项目作为开源生成工具持续优化的目标。

### 3. **对项目的影响和潜在意义**
- **用户体验提升**：版本更新通常修复已知问题，提升工具可靠性，对用户的实际使用体验有积极影响。
- **开发者生态维护**：定期版本发布有助于保持社区活跃度，吸引开发者持续关注和贡献。
- **潜在意义**：若更新包含对最新深度学习框架或硬件的适配，可能拓展项目的应用场景。

### 4. **值得关注的技术点**
- 由于提交信息较简洁（仅版本号），未透露具体技术细节。但可推测可能涉及：
  - **扩散模型推理优化**（如速度、内存效率提升）。
  - **依赖库更新**（如PyTorch、Diffusers版本适配）。
  - **API或配置调整**，以支持更丰富的生成任务。

### 5. **基于项目背景的提交影响分析**
- README强调项目是一个**集成化生成工具**（支持Logo动画等视觉内容合成）。此次更新：
  - **强化工具链成熟度**：版本迭代反映项目正在向生产就绪（production-ready）方向推进。
  - **响应社区需求**：可能修复了用户反馈的问题，提升工具在实际创作中的实用性。
  - **技术栈对齐**：可能适配了最新的扩散模型研究进展，保持技术前沿性。

---

### 总结建议
- 本次提交虽未提供详细变更日志，但作为**常规版本迭代**，它标志着项目在**稳定性和功能完善性**上的持续投入。  
- 对于用户：建议关注后续发布的详细更新说明，以了解具体优化内容。  
- 对于开发者：可观察版本间的代码差异（如合并的PR #1394），进一步分析技术演进路径。

## 详细提交记录

### [45d973e](https://github.com/modelscope/DiffSynth-Studio/commit/45d973e87dc730bb4b92958a2b67aacc4c1faf0b)

- **作者**: Zhongjie Duan
- **时间**: 2026-04-14T08:58:17Z
- **提交信息**: update to version 2.0.8 (#1394)

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-04-15
**监控日期**: 2026-04-14
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 25811
- **最后更新**: 2026-04-14T23:25:48Z

## 提交统计

- **昨日提交总数**: 26
- **提交者数量**: 22
- **主要提交者**: Jincong Chen, jianzhao-xu, Alexis MacAskill

## AI分析总结

根据提供的提交记录和README摘要（SGLang是一个专注于高效语言模型推理的项目），以下是昨日更新的分析总结：

### 1. 主要更新类型
- **Bug修复**：修复了Docker回归错误、流式会话计数、推测解码、NPU参数等多个关键问题。
- **性能优化**：优化了流缓冲区拼接、EPLB调度、PCG路径、注意力计算等核心组件的性能。
- **功能新增/增强**：新增了`runai-model-streamer` Docker支持、扩散模型对Ltx 2.3两阶段TI2V和FLUX.1-dev量化支持、统一基数缓存测试增强。
- **文档更新**：大量更新了NPU相关文档（最佳实践、参数说明、模型名称修正）、卸载文档、工具调用解析器格式。
- **基础设施/CI**：更新了CI权限、Dockerfile、缓存策略。
- **硬件支持扩展**：持续深化对NPU（华为昇腾）、AMD ROCm、特定存储后端（Mooncake）的支持。

### 2. 关键变更点及其与项目方向的关系
- **核心推理性能**（#22606, #21232, #21734, #17706）：通过优化字符串拼接（O(n²) -> O(1)）、EPLB、FP8模型路径和注意力计算，直接强化了SGLang作为**高效推理引擎**的核心竞争力。
- **多硬件后端支持**（#22804, #22808, #22796, #22722, #22626）：针对NPU、AMD、特定缓存后端的大量提交，体现了项目向**异构计算平台扩展**的战略方向，旨在成为硬件无关的通用推理框架。
- **流式与解码可靠性**（#22755, #22753, #21723）：修复流式会话计数和推测解码中的bug，提升了**流式输出**的稳定性和准确性，这是服务化场景的关键需求。
- **模型范围扩展**（#22667, #22672）：在扩散模型（视频生成、FLUX）和Kimi模型上的支持更新，表明项目正从纯文本LLM向**多模态模型推理**领域拓展。
- **测试与可维护性**（#22815, #22812）：增强基准测试和重构单元测试，提升了**代码质量与性能评估**的严谨性。

### 3. 对项目的影响和潜在意义
- **用户体验**：修复关键Bug（如Docker错误、解码错误）直接提升了框架的稳定性和部署体验。
- **性能基准**：多项性能优化可能带来显著的吞吐量提升和延迟降低，尤其在流式和高并发场景下。
- **生态扩展**：加强对NPU等硬件的支持，有助于吸引更广泛的硬件厂商和用户群体，构建更开放的生态。
- **技术债务**：重构测试和修复底层问题，有助于长期项目的健康维护。

### 4. 值得关注的技术点
- **推测解码与文法约束**（#21723）：将文法（grammar）集成到推测解码（EAGLE）的完成机制中，是**约束解码**与**加速技术**结合的前沿实践。
- **统一基数缓存**（#22815, #22812）：对KV Cache管理的持续优化和测试，这是影响LLM推理内存和效率的核心组件。
- **FP8模型优化**（#21734）：针对低精度（FP8）模型的专用优化路径，是追求极致推理效率的重要方向。
- **O(n²)到O(1)的流缓冲区优化**（#22606）：一个经典的数据结构优化，对处理长文本流输出有显著性能收益。

### 5. 基于项目背景的提交影响分析
SGLang的目标是成为“语言模型的高效推理引擎”。昨日的提交**全面强化了这一核心定位**：
1.  **强化核心引擎**：通过多项性能优化和Bug修复，使推理核心更**快、更稳**。
2.  **拓宽适用场景**：通过支持更多硬件（NPU、AMD）和更多模型类型（扩散模型、Kimi），提升了框架的**通用性和适用性**，使其不局限于特定芯片或文本模型。
3.  **完善开发生态**：通过更新文档、增强测试、改进CI，降低了用户和开发者的使用与贡献门槛，促进了**社区和生态的健康发展**。
4.  **探索前沿方向**：在推测解码、低精度计算、多模态支持等方面的提交，表明项目在保持工程稳健的同时，也在积极**探索和集成前沿推理技术**。

**总结**：昨日的更新是一次典型的“夯实基础、扩展边界”的迭代。既通过修复和优化巩固了核心推理引擎的可靠性与性能，又通过硬件适配、模型支持和新功能探索，积极推动项目向更广泛、更高效的通用模型服务化平台演进。

## 详细提交记录

### [e15401e](https://github.com/sgl-project/sglang/commit/e15401ee0eb4054fa374e5a453ad70ff4eca7fa8)

- **作者**: Alexis MacAskill
- **时间**: 2026-04-14T23:25:41Z
- **提交信息**: Add runai-model-streamer into Python packages installed in Dockerfile and fix NotADirectoryError Docker regression (#22537)

### [222eda1](https://github.com/sgl-project/sglang/commit/222eda1598be6fb9c6dcaa1adb8d9b5f70364a38)

- **作者**: Lianmin Zheng
- **时间**: 2026-04-14T22:22:10Z
- **提交信息**: [Misc] Use cache_once for is_arch_support_pdl in sgl-kernel (#22725)

### [e835605](https://github.com/sgl-project/sglang/commit/e83560562b8a740d95382e021987b392d4c6135a)

- **作者**: Jimmy Shong
- **时间**: 2026-04-14T22:13:31Z
- **提交信息**: Update CI Permissions (#22826)

### [8092431](https://github.com/sgl-project/sglang/commit/80924313166544714b4912ab572a3ff5b6fb20eb)

- **作者**: Alex Nails
- **时间**: 2026-04-14T21:48:44Z
- **提交信息**: [serving] replace O(n²) stream_buffer string concat with integer offset (#22606)

Co-authored-by: Claude Opus 4.6 (1M context) <noreply@anthropic.com>
Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>

### [36891ab](https://github.com/sgl-project/sglang/commit/36891ab5142ab7f4b8def65ee94793ba6fee6ac9)

- **作者**: Liangsheng Yin
- **时间**: 2026-04-14T20:26:03Z
- **提交信息**: Rename _alive_streaming_session_count; use _is_streaming helper (#22755)

### [0cb7295](https://github.com/sgl-project/sglang/commit/0cb7295698f01e948ab757dbdf73ece49ffbf548)

- **作者**: Liangsheng Yin
- **时间**: 2026-04-14T20:11:06Z
- **提交信息**: Fix streaming session busy-check double-counting via active_pool_idxs (#22753)

### [b4616dc](https://github.com/sgl-project/sglang/commit/b4616dcbf54305fab69a0537ba481b7aa05a1418)

- **作者**: mingyue300
- **时间**: 2026-04-14T19:43:50Z
- **提交信息**: [BugFix] Fix EAGLE speculative decoding missing grammar-based finish … (#21723)

### [d2f479e](https://github.com/sgl-project/sglang/commit/d2f479e544663d320988648d346054a16d598641)

- **作者**: Mick
- **时间**: 2026-04-14T16:02:05Z
- **提交信息**: [diffusion] chore: auto-enable best parallel setting if unspecified (#22763)

Co-authored-by: Claude Opus 4.6 (1M context) <noreply@anthropic.com>

### [3c0a6c6](https://github.com/sgl-project/sglang/commit/3c0a6c6987562a8fcd5c01b18e3b080faf3e32ca)

- **作者**: Ke Bao
- **时间**: 2026-04-14T15:58:05Z
- **提交信息**: Add page_size and SWA coverage to unified radix cache bench test (#22815)

### [070c6a2](https://github.com/sgl-project/sglang/commit/070c6a248919c305d62d116bf35a9a880e1f7064)

- **作者**: Bi Xue
- **时间**: 2026-04-14T14:52:17Z
- **提交信息**: [sgl] perf optimization for eplb (#21232)

### [9f9e023](https://github.com/sgl-project/sglang/commit/9f9e0231bb78111dda2c9213a5aca6ec011af9cb)

- **作者**: Ke Bao
- **时间**: 2026-04-14T14:34:33Z
- **提交信息**: Refactor unified radix cache UT into parameterized test suite (#22812)

### [c5e9508](https://github.com/sgl-project/sglang/commit/c5e95080d21bd2619348f2662ad86cda99663fb0)

- **作者**: Mick
- **时间**: 2026-04-14T14:10:08Z
- **提交信息**: [diffusion] model: support Ltx 2.3 two stage ti2v (#22667)

### [680bd4b](https://github.com/sgl-project/sglang/commit/680bd4b429388cebe9f8f735353471587f035a34)

- **作者**: chx96642264
- **时间**: 2026-04-14T13:34:07Z
- **提交信息**: [NPU] Modify the parameter name and optional values, and add the parameter restrictions. Modify some parameters supported type. (#22804)

### [1588856](https://github.com/sgl-project/sglang/commit/1588856e9b7c275e25db67aeba9118f5c8d434a6)

- **作者**: McZyWu
- **时间**: 2026-04-14T13:21:37Z
- **提交信息**: [NPU] qwen3next low latency best practice docs. (#22808)

Co-authored-by: root <root@localhost.localdomain>

### [ddc7daa](https://github.com/sgl-project/sglang/commit/ddc7daaf89a0d5e4b19f2b9eb8bb6fa7e43f1c40)

- **作者**: amote-i
- **时间**: 2026-04-14T13:10:28Z
- **提交信息**: [NPU] [DOC] Update NPU docs to match latest code (#22796)

### [454228e](https://github.com/sgl-project/sglang/commit/454228e071aa906fe3cbf56deb40e52986bce08a)

- **作者**: lawtherWu
- **时间**: 2026-04-14T12:51:06Z
- **提交信息**: hicache storage backend mooncake support ascend hixl (#20016)

### [074c2a4](https://github.com/sgl-project/sglang/commit/074c2a476ddf52ffc9b55bc5fe9b3327b0886540)

- **作者**: loading66
- **时间**: 2026-04-14T12:15:22Z
- **提交信息**: fix:[NPU]correct the full name of then Kimi model (#22799)

### [68dfffa](https://github.com/sgl-project/sglang/commit/68dfffaaa3bd809f96cd8769c309daa9b4c7117c)

- **作者**: jianzhao-xu
- **时间**: 2026-04-14T12:03:29Z
- **提交信息**: Offloading docs update (#22795)

Co-authored-by: Jianzhao Xu <xujianchao@huawei.com>

### [88253c3](https://github.com/sgl-project/sglang/commit/88253c39b0e066e60fd390e08fcfe93e646452d6)

- **作者**: xdtbynd
- **时间**: 2026-04-14T11:21:31Z
- **提交信息**: [Docs] Fix formatting of tool-call-parser options (#22793)

### [368cdfb](https://github.com/sgl-project/sglang/commit/368cdfbe2f29a22b0f71e21023984c63db085777)

- **作者**: amote-i
- **时间**: 2026-04-14T11:21:15Z
- **提交信息**: [NPU] [DOC] Fix outdated descriptions in the NPU documentation (#22707)

### [6da3aba](https://github.com/sgl-project/sglang/commit/6da3aba6a5d62f9b9b976553c46b5d45b88b3b13)

- **作者**: Jia Guo
- **时间**: 2026-04-14T09:51:27Z
- **提交信息**: perf: optimize PCG inductor path for FP8 models (#21734)

Co-authored-by: Claude Opus 4.6 (1M context) <noreply@anthropic.com>

### [3cb3f7c](https://github.com/sgl-project/sglang/commit/3cb3f7c01814c90f3f4aacde83f6f2cfcd20ed35)

- **作者**: xutizhou
- **时间**: 2026-04-14T09:33:27Z
- **提交信息**: fix: EPLB dispatch OOB when shared experts fusion enabled under DeepEP (#22525)

### [6760c79](https://github.com/sgl-project/sglang/commit/6760c790bd5401b6793adc6761a04b8872caebf7)

- **作者**: Jincong Chen
- **时间**: 2026-04-14T08:08:23Z
- **提交信息**: [bugfix] avoid attention padding tokens computation in pcg (#17706)

### [eab045b](https://github.com/sgl-project/sglang/commit/eab045b2b74eac9b32b20534e52c0eda582a754a)

- **作者**: Michael
- **时间**: 2026-04-14T07:30:11Z
- **提交信息**: [AMD] Add MiniMax-M2.7 accuracy and performance nightly tests (#22722)

Co-authored-by: HaiShaw <hixiao@gmail.com>

### [d7ecab5](https://github.com/sgl-project/sglang/commit/d7ecab51134d5640b298bed735c7494ade40c142)

- **作者**: xiaobochen-amd
- **时间**: 2026-04-14T07:25:09Z
- **提交信息**: [ROCm]fix(aiter): cast fp8 prefill output back to model dtype (#22626)

Co-authored-by: kk <43161300+kkHuang-amd@users.noreply.github.com>

### [f97c608](https://github.com/sgl-project/sglang/commit/f97c608caa371e62ae8fe4847619f4b336a3ee69)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-04-14T07:00:59Z
- **提交信息**: [diffusion] quant: add FLUX.1-dev modelopt nvfp4 support (#22672)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-04-15
**监控日期**: 2026-04-14
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native Inference Engine with Cache Acceleration, Parallelism and Quantization for DiTs.
- **语言**: Python
- **星标数**: 1138
- **最后更新**: 2026-04-14T15:41:45Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

根据仓库README摘要（一个专注于为Diffusion Transformers提供缓存、并行化和量化的PyTorch原生推理引擎）以及提供的提交记录，以下是昨日更新的要点总结：

### 1. 主要更新类型
*   **功能新增**：新增了对`svdq-dq few shot`和基于`cute-dsl`的`svdquant w4a4`的支持。
*   **文档更新**：更新了与`svdq-dq few shot`功能相关的文档。

### 2. 关键变更点及其与项目整体方向的关系
*   **支持svdq-dq few shot**：这是一种新的量化技术或模式（推测为“SVDQ-DeQuantization Few Shot”），旨在通过少量样本优化量化过程，提升模型精度或效率。这直接服务于项目的核心方向之一——**模型量化**，旨在降低推理时的计算和存储开销。
*   **支持cute-dsl based svdquant w4a4**：引入了基于特定领域语言（DSL，推测为`cute-dsl`）实现的SVD量化方法，支持权重和激活均为4位（W4A4）的极低比特量化。这同样是项目**量化**方向上的重要深化，探索更极致的模型压缩与加速。
*   **更新相关文档**：为新功能提供使用说明，确保项目的**易用性和可维护性**。

### 3. 对项目的影响和潜在意义
*   **扩展量化技术栈**：为使用者提供了更多、更先进的量化选项（特别是极低比特W4A4量化），增强了引擎在模型压缩和加速方面的能力。
*   **提升量化精度与灵活性**：`few shot`支持可能意味着量化过程可以更好地适应特定数据分布，有望在保持高压缩率的同时减少精度损失。
*   **技术探索与集成**：集成`cute-dsl`表明项目在积极吸收和整合业界先进的编译或优化工具链，可能为未来更复杂的优化策略铺平道路。

### 4. 值得关注的技术点
*   **SVDQ-DQ Few Shot**：关注其如何利用少量样本优化量化参数，以及相比标准量化在精度/速度上的具体提升。
*   **Cute-DSL**：这是一个值得关注的外部工具或内部DSL。需要了解它在定义和执行量化计算图优化方面的作用，以及它如何与PyTorch原生生态集成。
*   **W4A4量化**：这是当前模型量化的前沿方向之一，实现稳定可用的W4A4量化具有较高的技术挑战性和实用价值。

### 5. 基于项目背景的提交影响分析
Cache-DIT项目的核心目标是构建一个高效、轻量的Diffusion Transformer推理引擎。昨日的提交**紧密围绕“量化”这一核心支柱展开**：
*   **强化核心优势**：通过新增`svdq-dq few shot`和基于DSL的`svdquant w4a4`，项目在模型压缩和加速这一关键赛道上增加了新的、更先进的“武器”，**直接提升了引擎的竞争力和实用性**。
*   **探索性能边界**：W4A4量化的支持意味着项目在探索推理速度和内存占用的极限，这与README中强调的“高效”目标高度一致。
*   **完善开发者体验**：及时更新文档确保了新功能的可发现性和易用性，有助于社区采纳和反馈，促进项目生态发展。

**总结**：昨日的更新是Cache-DIT项目在量化技术方向上的一次**实质性推进**，不仅增加了新的功能特性，也通过集成新工具（cute-dsl）和更新文档，持续巩固其作为专注于Diffusion Transformer高效推理的PyTorch原生引擎的定位。

## 详细提交记录

### [125571a](https://github.com/vipshop/cache-dit/commit/125571af2d82bba6532509aa2a3943215fd32a11)

- **作者**: DefTruth
- **时间**: 2026-04-14T13:54:15Z
- **提交信息**: chore: update svdq-dq few shot docs (#980)

### [9a34f02](https://github.com/vipshop/cache-dit/commit/9a34f025ca43814fc84f19d26239a7fa6d8c62e2)

- **作者**: DefTruth
- **时间**: 2026-04-14T13:45:53Z
- **提交信息**: feat: support svdq-dq few shot (#979)

* feat: support svdq-dq few shot

* feat: support svdq-dq few shot

* feat: support svdq-dq few shot

* feat: support svdq-dq few shot

* feat: support svdq-dq few shot

### [a52693f](https://github.com/vipshop/cache-dit/commit/a52693f375f7be51c735dae90def13a3a5d8ebf2)

- **作者**: DefTruth
- **时间**: 2026-04-14T08:29:34Z
- **提交信息**: [1/N] feat: support cute-dsl based svdquant w4a4 (#978)

* [1/N] feat: support cute-dsl based svdquant w4a4

* [1/N] feat: support cute-dsl based svdquant w4a4

* [1/N] feat: support cute-dsl based svdquant w4a4

* [1/N] feat: support cute-dsl based svdquant w4a4

* [1/N] feat: support cute-dsl based svdquant w4a4

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-04-15
**监控日期**: 2026-04-14
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 76602
- **最后更新**: 2026-04-14T23:04:03Z

## 提交统计

- **昨日提交总数**: 33
- **提交者数量**: 31
- **主要提交者**: wang.yuqi, Shanshan Shen, Albert Cheng

## AI分析总结

根据vLLM仓库的提交记录和README摘要（项目定位为“为所有人提供简单、快速、廉价的LLM服务”），以下是昨日更新的分析总结：

### 1. 主要更新类型
- **Bug修复**：占主导地位（约15项），涉及GPU兼容性、内核、缓存、量化、模型加载等多个核心模块。
- **性能优化与功能增强**：包括推理加速、内存优化、新模型/硬件支持。
- **重构与代码整理**：主要围绕MoE（混合专家）架构和内核代码。
- **CI/测试与工具改进**：涉及测试修复、编译优化和基准测试工具。

### 2. 关键变更点及其与项目方向的关系
| 关键变更点 | 与项目方向（简单、快速、廉价）的关系 |
| :--- | :--- |
| **GPU硬件兼容性修复**（SM121/DGX Spark、ROCm、XPU） | 扩大硬件支持范围，使服务能在更多平台上“廉价”运行。 |
| **MoE架构的多项优化与重构**（#35549, #39007, #39107等） | 提升MoE模型推理效率，对服务“快速”和扩展性至关重要。 |
| **内核与量化支持增强**（NVFP4、FP8 KV缓存、TRT-LLM集成） | 通过优化内存和计算，直接提升推理速度并降低成本。 |
| **多模态与视觉模型支持**（Qwen3-VL视频、Ernie-4.5 VL） | 拓展服务范围，支持更复杂的“LLM服务”场景。 |
| **前端与预处理优化**（异步处理、推理解析器） | 改善用户体验和系统响应速度，体现“简单”和“快速”。 |
| **KV缓存与内存管理优化**（KV卸载、缓存修复） | 核心性能优化，直接影响吞吐量和成本。 |

### 3. 对项目的影响和潜在意义
- **稳定性与可靠性提升**：大量Bug修复增强了生产环境稳定性。
- **性能与效率进步**：内核优化、MoE重构和内存管理改进直接提升吞吐量、降低延迟与成本。
- **生态扩展**：对更多硬件（AMD ROCm、Intel XPU）、模型架构（MoE、Mamba、多模态）和量化方案的支持，扩大了用户基础和适用场景。
- **开发者体验**：编译缓存、导入错误处理等改进使项目更易于使用和贡献。

### 4. 值得关注的技术点
- **FlashInfer与定制内核**：针对特定硬件（如DGX Spark）和模型（Mamba）的深度优化。
- **混合推理与推测解码**：`[Hybrid]`提交显示对复杂推理场景的持续优化。
- **统一内存布局与KV卸载**：面向大模型推理的内存瓶颈进行系统性优化。
- **PluggableLayer的推进**：模块化设计，提高代码可维护性和可扩展性。

### 5. 基于项目背景的提交影响分析
vLLM的目标是成为**高效、普适的LLM服务引擎**。昨日的提交集体推动了这一目标：
- **“快速”与“廉价”**：通过内核优化、MoE重构、量化支持和内存管理，持续压榨硬件性能，降低单位推理成本。
- **“简单”与“为所有人”**：通过修复各类兼容性问题（硬件、模型格式）、增强多模态支持、优化前端处理，降低了用户的使用门槛和适配成本。
- **项目成熟度**：提交中大量针对边缘案例的Bug修复和细致的性能优化，表明项目正在从“实现核心功能”向“追求工业级稳定与效率”深度演进。
- **战略方向**：对MoE、多模态、多种硬件和后端（如TRT-LLM）的重点投入，显示出项目正积极拥抱行业趋势，构建一个全面且高性能的推理生态系统。

**总结**：昨日更新是一次以**修复和优化**为主的常规推进，全面巩固了vLLM在**性能、兼容性和稳定性**方面的基础，并持续拓展其支持的**模型前沿和硬件生态**，与项目成为主流LLM服务核心引擎的愿景高度一致。

## 详细提交记录

### [65b9808](https://github.com/vllm-project/vllm/commit/65b9808960d7f25a018c525d2aca3dba7c411cfb)

- **作者**: Michael Goin
- **时间**: 2026-04-14T23:03:57Z
- **提交信息**: [Bugfix] Disable FlashInfer CUTLASS MoE on SM121 (DGX Spark) (#39825)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [507df79](https://github.com/vllm-project/vllm/commit/507df79a29ac8733ea03c624d215ccfffad7bbe9)

- **作者**: Francesco Fusco
- **时间**: 2026-04-14T22:19:09Z
- **提交信息**: [Hybrid] Simplify accepted token counting in spec decode for hybrid models (#38372)

### [1696c86](https://github.com/vllm-project/vllm/commit/1696c864b90afb9cec925312d0cf12c396517007)

- **作者**: Zhewen Li
- **时间**: 2026-04-14T21:13:58Z
- **提交信息**: [Bugfix][Mooncake] Fix thread-local CUDA context for NVLink transfers in _send_blocks (#39548)

Signed-off-by: Zhewen Li <zhewenli@inferact.ai>
Co-authored-by: Zhewen Li <zhewenli@inferact.ai>

### [2ad1029](https://github.com/vllm-project/vllm/commit/2ad10292339c045db0cb3998a76240a459cc83a7)

- **作者**: Wentao Ye
- **时间**: 2026-04-14T21:08:17Z
- **提交信息**: [Bug] Fix batch invariance nvfp4 support (#39820)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [b2f749d](https://github.com/vllm-project/vllm/commit/b2f749dc97d59e3eb808499e88a29663f2143aa1)

- **作者**: maobaolong
- **时间**: 2026-04-14T20:51:27Z
- **提交信息**: fix(lmcache): correct store for cached requests while enable prefix cache (#39719)

Signed-off-by: baoloongmao <baoloongmao@tencent.com>

### [70ed015](https://github.com/vllm-project/vllm/commit/70ed01550c2a47d1888450935f30b8cf2f55d6bd)

- **作者**: rishitdholakia13
- **时间**: 2026-04-14T20:29:06Z
- **提交信息**: [Reasoning][Frontend] Add model config to adjust_request in reasoning parser (#37848)

Signed-off-by: rishitdholakia13 <rishit+github@cohere.com>
Signed-off-by: rishitdholakia13 <123388671+rishitdholakia13@users.noreply.github.com>
Signed-off-by: Aaron Pham <contact@aarnphm.xyz>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Aaron Pham <contact@aarnphm.xyz>

### [19ec9a0](https://github.com/vllm-project/vllm/commit/19ec9a0a6276d5af449b3011dac2944e8af37ee0)

- **作者**: bnellnm
- **时间**: 2026-04-14T20:11:20Z
- **提交信息**: [MoE Refactor] Refactor ZeroExpertFusedMoE into new framework (#35549)

Signed-off-by: Bill Nell <bnell@redhat.com>

### [1a9353b](https://github.com/vllm-project/vllm/commit/1a9353bb02e69de4631de6f7c0424aae5aa32f1a)

- **作者**: Jackmin801
- **时间**: 2026-04-14T19:27:39Z
- **提交信息**: [MoE] Move GPT OSS Triton kernel experts into fused_moe/experts/ (#39007)

Signed-off-by: Robert Shaw <robertgshaw2@gmail.com>
Signed-off-by: Jackmin801 <ongjackm@gmail.com>
Co-authored-by: Robert Shaw <robertgshaw2@gmail.com>

### [ecf5ff7](https://github.com/vllm-project/vllm/commit/ecf5ff7ce3ac2a8db51654712cbcea3540faaef8)

- **作者**: roikoren755
- **时间**: 2026-04-14T19:10:58Z
- **提交信息**: [Mamba] Flashinfer selective_state_update (#36162)

Signed-off-by: Roi Koren <roik@nvidia.com>

### [3067931](https://github.com/vllm-project/vllm/commit/30679319e83a78f6fd405130e562043c1e7f5e7e)

- **作者**: zhanqiuhu
- **时间**: 2026-04-14T18:59:15Z
- **提交信息**: [CI][KVConnector][Metrics] Update multi KV connector edge case according to prefill stats changes (#39808)

Signed-off-by: Zhanqiu Hu <zhu@redhat.com>

### [240f263](https://github.com/vllm-project/vllm/commit/240f2636ca4954941dd314ba961023100f804307)

- **作者**: danielafrimi
- **时间**: 2026-04-14T18:49:56Z
- **提交信息**: [Kernel] Support TRTLLM GEN NVFP4 MoE for non-512-aligned hidden dims via weight padding (#39510)

Signed-off-by: root <root@lyris0017.lyris.clusters.nvidia.com>
Signed-off-by: Daniel Afrimi <dafrimi@nvidia.com>
Co-authored-by: root <root@lyris0017.lyris.clusters.nvidia.com>

### [dc8df11](https://github.com/vllm-project/vllm/commit/dc8df110bc8a5c80dbb8f1fef02e98deb8aa2b09)

- **作者**: Albert Cheng
- **时间**: 2026-04-14T18:43:05Z
- **提交信息**: add warning when FP8 KV cache misses prefill query quantization (#39752)

Signed-off-by: Michael Goin <mgoin64@gmail.com>
Co-authored-by: Albert Cheng (Engrg-Hardware 1) <albecheng@login-lyris02.lyris.clusters.nvidia.com>
Co-authored-by: Michael Goin <mgoin64@gmail.com>
Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>

### [be0c855](https://github.com/vllm-project/vllm/commit/be0c855ebd6ed4a8bface6c7df6d99150fdb5d90)

- **作者**: omerpaz95
- **时间**: 2026-04-14T18:33:33Z
- **提交信息**: [KV Offload] Unified memory layout for offloading workers (#37206)

Signed-off-by: omerpaz95 <omerpaz95@gmail.com>
Co-authored-by: Or Ozeri <oro@il.ibm.com>

### [e64b39e](https://github.com/vllm-project/vllm/commit/e64b39ea7114d7294db1da9766f5f9a88ef4ed25)

- **作者**: Andrew Barnes
- **时间**: 2026-04-14T17:36:26Z
- **提交信息**: [ROCm] Align AiterFlashAttentionImpl attn_type check with backend (#39119)

Signed-off-by: Bortlesboat <bortstheboat@gmail.com>

### [2faad08](https://github.com/vllm-project/vllm/commit/2faad08362ff50f254de27cb3c54272b9f3af4b8)

- **作者**: Alessandro Sangiorgi
- **时间**: 2026-04-14T17:17:54Z
- **提交信息**: [compile] Nest inductor cache under AOT compile dir (#39718)

Signed-off-by: Alessandro Sangiorgi <asangior@redhat.com>

### [23f3760](https://github.com/vllm-project/vllm/commit/23f3760217614807b1c1b08e593a54a824e42479)

- **作者**: Rohan Potdar
- **时间**: 2026-04-14T17:10:04Z
- **提交信息**: [Bugfix][ROCm]: Allow `gpt_oss_mxfp4` quantization method on rocm (#39754)

Signed-off-by: Rohan138 <rohanpotdar138@gmail.com>

### [906a8c1](https://github.com/vllm-project/vllm/commit/906a8c15d0beded2cca8b357877266c631340f74)

- **作者**: Mark McLoughlin
- **时间**: 2026-04-14T16:53:57Z
- **提交信息**: [Core][Metrics] Remove unused `SchedulerStats.encoder_cache_usage` (#39693)

Signed-off-by: Mark McLoughlin <markmc@redhat.com>

### [4f4f8ea](https://github.com/vllm-project/vllm/commit/4f4f8eaa78fb861dcb0b141951f7496b47ea679e)

- **作者**: Micah Williamson
- **时间**: 2026-04-14T16:14:31Z
- **提交信息**: [ROCm][CI] Fix condition for `test_per_token_group_quant_fp8_packed` (#39730)

Signed-off-by: Micah Williamson <micah.williamson@amd.com>

### [b6890a1](https://github.com/vllm-project/vllm/commit/b6890a120a70ffbf2e932b4f49e1e2416e3881f2)

- **作者**: Netanel Haber
- **时间**: 2026-04-14T15:11:46Z
- **提交信息**: Bugfix: `use_existing_torch.py`: Glob recursive subdirs in requirements (fixes #39024) (#39793)

Signed-off-by: Netanel Haber <58652339+netanel-haber@users.noreply.github.com>

### [c08f3b2](https://github.com/vllm-project/vllm/commit/c08f3b2a62fd8ddcb644ae91697a7981f2db4097)

- **作者**: Lucas Kabela
- **时间**: 2026-04-14T14:52:49Z
- **提交信息**: Measure encoder compile time seperate from llm backbone (#39240)

Signed-off-by: Lucas Kabela <lucaskabela@meta.com>

### [f02b326](https://github.com/vllm-project/vllm/commit/f02b3269e7e0ebfdc62f39db2169d88074512d6d)

- **作者**: Hexiang Wang
- **时间**: 2026-04-14T13:55:00Z
- **提交信息**: [PluggableLayer][3/N] Apply PluggableLayer to moe-related layers. (#33556)

Signed-off-by: whx-sjtu <2952154980@qq.com>

### [e1e318a](https://github.com/vllm-project/vllm/commit/e1e318af010b4f92d39324d03231cfd409766bf9)

- **作者**: bnellnm
- **时间**: 2026-04-14T13:48:05Z
- **提交信息**: [MoE Refactor] Remove MoE DP chunking (#39107)

Signed-off-by: Bill Nell <bnell@redhat.com>
Co-authored-by: Robert Shaw <114415538+robertgshaw2-redhat@users.noreply.github.com>

### [f7e62e3](https://github.com/vllm-project/vllm/commit/f7e62e3d6618f64430262bf776079d0d89f20501)

- **作者**: bhargav-patel-29
- **时间**: 2026-04-14T12:13:36Z
- **提交信息**: [Bugfix] Fix mismatch between global and local attention heads in tensor-parallel mode for param2moe model (#39707)

Signed-off-by: bhargav-patel-29 <bhargav.patel@tihiitb.org>
Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>

### [18b1c77](https://github.com/vllm-project/vllm/commit/18b1c77211d8f6fe800bcfb89524d2b598708032)

- **作者**: Yiyang "Ian" Liu
- **时间**: 2026-04-14T11:09:06Z
- **提交信息**: fix: handle ImportError in load_audio (#39473)

Signed-off-by: Yiyang Liu <37043548+ianliuy@users.noreply.github.com>
Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>

### [1e4748c](https://github.com/vllm-project/vllm/commit/1e4748c66a156af3ea7b72a9dbe3fb686c8750eb)

- **作者**: Matthias Gehre
- **时间**: 2026-04-14T11:00:40Z
- **提交信息**: [Bugfix] Fix `vllm bench serve` to count multimodal tokens in "total input tokens" (#38654)

Signed-off-by: Matthias Gehre <matthias.gehre@amd.com>

### [6f786f2](https://github.com/vllm-project/vllm/commit/6f786f2c506cb07f4566771fdc62e640e2c4a176)

- **作者**: Thomas
- **时间**: 2026-04-14T10:11:18Z
- **提交信息**: [Bugfix][Model] Fix Devstral Small 2 HF format weight loading (#39293)

Signed-off-by: thomasmaindron <thomasmaindron@users.noreply.github.com>
Co-authored-by: thomasmaindron <thomasmaindron@users.noreply.github.com>
Co-authored-by: Claude Opus 4.6 (1M context) <noreply@anthropic.com>

### [4eee77b](https://github.com/vllm-project/vllm/commit/4eee77b877d9ecf493967433707eb44caf5c7558)

- **作者**: fxmarty-amd
- **时间**: 2026-04-14T09:35:28Z
- **提交信息**: [fix][MOE] Fix MOE experts `intermediate_size` dimension not being narrowed before weight loading (#39688)

Signed-off-by: Felix Marty <Felix.Marty@amd.com>

### [a1993b9](https://github.com/vllm-project/vllm/commit/a1993b96fd95ad19cc4b8a1554219ff115939edf)

- **作者**: xiangdong
- **时间**: 2026-04-14T09:27:38Z
- **提交信息**: [XPU][CI] Remove Arc in label-xpu (#39776)

Signed-off-by: zengxian <xiangdong.zeng@intel.com>

### [893b2af](https://github.com/vllm-project/vllm/commit/893b2affff548bf0f54978ca2ba4545c5b4d5fbe)

- **作者**: Julien Debache
- **时间**: 2026-04-14T09:20:03Z
- **提交信息**: feat: add TxtSlicesDataset to allow sampling slices from txt file for benchmarking (#30156)

Signed-off-by: jdebache <jdebache@nvidia.com>

### [8011885](https://github.com/vllm-project/vllm/commit/80118853f42a728805e6a861ffb50f3b876a9939)

- **作者**: Shanshan Shen
- **时间**: 2026-04-14T08:49:32Z
- **提交信息**: [MM][Perf][CG] Support ViT full CUDA graph for Qwen3-VL video inference (#38061)

Signed-off-by: shen-shanshan <467638484@qq.com>
Signed-off-by: Shanshan Shen <87969357+shen-shanshan@users.noreply.github.com>
Co-authored-by: Roger Wang <hey@rogerw.io>

### [c0ecaed](https://github.com/vllm-project/vllm/commit/c0ecaed95030815c49699995bf6461209ccd6a0f)

- **作者**: wang.yuqi
- **时间**: 2026-04-14T08:29:25Z
- **提交信息**: [Frontend] Offload blocking preprocessing & postprocessing ops to thread pool for pooling entrypoints. (#39763)

Signed-off-by: wang.yuqi <yuqi.wang@daocloud.io>
Signed-off-by: wang.yuqi <noooop@126.com>
Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>

### [0008729](https://github.com/vllm-project/vllm/commit/0008729abfbd380d29e0a67a882c8f01220acd73)

- **作者**: lalit10
- **时间**: 2026-04-14T08:11:52Z
- **提交信息**: [Model] Use mm_features for Ernie-4.5 VL M-RoPE (#39753)

Signed-off-by: Lalit Laxminarayan Bangad <lalitbangad@gmail.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>

### [d3af8c1](https://github.com/vllm-project/vllm/commit/d3af8c18317c0dc008d42e4367fbb9045cfb7bf6)

- **作者**: Mark McLoughlin
- **时间**: 2026-04-14T08:00:45Z
- **提交信息**: [Core][Metrics][BugFix] Replace num_cached_tokens/num_external_computed_tokens with PrefillStats (#37460)

Related to `Counters can only be incremented by non-negative amounts`
error with the `vllm:prompt_tokens_by_source_total` metric.

Signed-off-by: Mark McLoughlin <markmc@redhat.com>
Co-authored-by: Or Ozeri <or@ozery.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-04-15
**监控日期**: 2026-04-14
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 4290
- **最后更新**: 2026-04-14T22:05:33Z

## 提交统计

- **昨日提交总数**: 12
- **提交者数量**: 10
- **主要提交者**: amy-why-3459, wangyu, Hongsheng Liu

## AI分析总结

根据提供的README摘要和提交记录，以下是vllm-omni项目昨日更新的分析总结：

### 1. 主要更新类型
- **Bug修复**：占主导地位（7项），涉及模型推理、API接口、量化配置和测试稳定性。
- **测试与CI/CD**：包括测试用例新增、CI配置清理和测试阈值调整（4项）。
- **功能增强**：1项（Omni Transfer Engine Connector支持多发送者）。
- **文档更新**：1项（修复文档命令）。
- **其他**：1项（添加技能描述，内容不明）。

### 2. 关键变更点及其与项目方向的关系
| 关键变更点 | 与项目方向的关系 |
| :--- | :--- |
| **修复HunyuanImage3模型mrope参数问题** | 确保多模态模型（图像处理）的推理稳定性，符合“omni-modality”服务目标。 |
| **修复Qwen omni模型音频API接口** | 明确接口边界，避免误用，提升API服务的健壮性和用户体验。 |
| **修复预量化检查点的FP8配置问题** | 保护视觉/音频编码器不被错误量化，确保模型精度和推理质量。 |
| **新增长视频/音频测试用例** | 加强对长序列多模态输入的支持和验证，是项目处理复杂场景的关键。 |
| **Omni传输引擎支持1对N发送者** | 增强分布式推理和并行处理能力（如Bagel的TP/CFG），直接服务于“fast”和可扩展的部署目标。 |

### 3. 对项目的影响和潜在意义
- **稳定性提升**：集中修复多个关键Bug，直接提高生产环境服务的可靠性和用户体验。
- **测试覆盖度增强**：新增长内容测试和修复CI问题，有助于在复杂场景下提前发现隐患，保障“cheap”且稳定的服务。
- **架构扩展性**：传输引擎的增强为未来更复杂的多模态、大规模并行推理场景奠定了基础。
- **开发者体验**：清理临时CI配置、修复文档，改善了项目的维护性和上手体验。

### 4. 值得关注的技术点
- **多模态模型特定问题**：针对`HunyuanImage3`、`Qwen omni`等具体模型的修复，反映了支持多样化前沿模型时的工程挑战。
- **量化配置的精细化管理**：区分对待模型主干和编码器的量化，体现了对模型精度与推理效率的平衡考量。
- **并行推理架构**：“1-receiver-to-N-senders”模式是优化分布式多模态推理吞吐量和延迟的关键设计。
- **长序列多媒体处理**：专门为长视频和长音频添加测试，表明项目正积极应对实际应用中的长上下文挑战。

### 5. 基于项目背景的提交影响分析
项目目标是提供**简单、快速、经济的全模态模型服务**。昨日的提交整体上是一次以**巩固和优化**为主的迭代：
- **巩固“Easy”与“Fast”**：通过修复Bug和增强测试，减少了用户和服务运维的潜在故障，使服务更稳定（Easy），并行引擎的优化则直接支持了更快的推理（Fast）。
- **夯实“omni-modality”基础**：修复涉及图像、音频、视频等多种模态的处理问题，并扩展测试覆盖范围，正是在强化其全模态服务能力的核心根基。
- **为“cheap”和规模化铺路**：CI/CD的优化和架构扩展性的提升，有助于降低长期运维成本，并支持更高效的资源利用，这与经济高效的服务目标相一致。

**总结**：本次更新虽无重大功能发布，但通过一系列扎实的Bug修复、测试增强和底层架构优化，显著提升了vllm-omni作为生产级全模态服务框架的**成熟度、稳定性和可扩展性**，是项目向稳定可靠目标迈进的关键一步。

## 详细提交记录

### [bc4a659](https://github.com/vllm-project/vllm-omni/commit/bc4a659f03f7d28892fa1a52a1cceaa55ddac0ba)

- **作者**: Yiyang "Ian" Liu
- **时间**: 2026-04-14T14:41:28Z
- **提交信息**: [Bugfix] Make mrope kwargs optional in HunyuanImage3 get_mrope_input_positions (#2654)

Signed-off-by: Yiyang Liu <yiyangliu@microsoft.com>
Co-authored-by: SYLAR <125541396+lishunyang12@users.noreply.github.com>

### [f03ab38](https://github.com/vllm-project/vllm-omni/commit/f03ab38783cb6ed5f110540966aae54fec06828d)

- **作者**: amy-why-3459
- **时间**: 2026-04-14T14:26:55Z
- **提交信息**: [BugFix] Fix NoneType' object has no attribute 'detach' (#2797)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [53a9cf4](https://github.com/vllm-project/vllm-omni/commit/53a9cf49a6a2ee8dbacb7985458390ffb804ddbe)

- **作者**: Yiyang "Ian" Liu
- **时间**: 2026-04-14T13:52:32Z
- **提交信息**: fix: do not apply FP8 quant config to vision/audio encoders for pre-quantized checkpoints (#2702)

Signed-off-by: Yiyang Liu <37043548+ianliuy@users.noreply.github.com>
Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>

### [4fb078a](https://github.com/vllm-project/vllm-omni/commit/4fb078a03166fc749e889a1934b6a59b483d5e18)

- **作者**: Bvicii
- **时间**: 2026-04-14T12:53:06Z
- **提交信息**: [Bugfix] Reject /v1/audio/speech for Qwen omni models (#2763)

Signed-off-by: Bvicii <yizhanhuang2002@gmail.com>

### [cf1fcd5](https://github.com/vllm-project/vllm-omni/commit/cf1fcd5acf9ec0c7d74daf550a922f6fd3d716ca)

- **作者**: Alex Brooks
- **时间**: 2026-04-14T12:49:57Z
- **提交信息**: [CI/BugFix] Fix Flaky Test for Qwen Omni Perf (#2754)

Signed-off-by: Alex Brooks <albrooks@redhat.com>

### [5ce0a43](https://github.com/vllm-project/vllm-omni/commit/5ce0a434920590e090d7080f9f67e03c4c300d82)

- **作者**: wangyu
- **时间**: 2026-04-14T12:48:04Z
- **提交信息**: [CI][Bugfix] Update thresholds for accuracy tests (#2725)

Signed-off-by: wangyu <410167048@qq.com>

### [bcd5f16](https://github.com/vllm-project/vllm-omni/commit/bcd5f16321df6bbc6f997a3906d16a23c8bb489e)

- **作者**: n1ptune
- **时间**: 2026-04-14T12:41:23Z
- **提交信息**: [Misc] clean Temporary CI Configs (#2784)

Signed-off-by: neptune <neptune@hust.edu.cn>
Co-authored-by: neptune <neptune@hust.edu.cn>

### [f87674a](https://github.com/vllm-project/vllm-omni/commit/f87674aa447b24fb305f3eafcab1e51b30e0d9a6)

- **作者**: Hongsheng Liu
- **时间**: 2026-04-14T12:26:27Z
- **提交信息**: [skip ci]add skills (#2710)

Signed-off-by: hsliuustc0106 <liuhongsheng4@huawei.com>

### [159d655](https://github.com/vllm-project/vllm-omni/commit/159d6558ea55ef59b3c57cf512e8114b62cd881e)

- **作者**: amy-why-3459
- **时间**: 2026-04-14T11:36:02Z
- **提交信息**: [Tests][Qwen3-Omni]Add test cases for long videos and long audios. (#2598)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [3229bae](https://github.com/vllm-project/vllm-omni/commit/3229bae331cb7ad37a71bb19853dae62fff9b4ec)

- **作者**: rongfu.leng
- **时间**: 2026-04-14T10:33:31Z
- **提交信息**: [skip ci] fix docs, gdown remove --id param (#2787)

Signed-off-by: rongfu.leng <lenronfu@gmail.com>

### [6d01a8b](https://github.com/vllm-project/vllm-omni/commit/6d01a8b506a2a28a7aedc1ffd5c989a407b0bd70)

- **作者**: NATURE
- **时间**: 2026-04-14T08:06:37Z
- **提交信息**: [Omni Connector] Omni Transfer Engine Connector: Enable 1-receiver-to-N-senders to support Bagel TP/CFG parallel (#2731)

Signed-off-by: natureofnature <wzliu@connect.hku.hk>

### [17acd05](https://github.com/vllm-project/vllm-omni/commit/17acd0589a26a84bd30733496d9ffedee7f8cb67)

- **作者**: Zhang Jian
- **时间**: 2026-04-14T07:05:12Z
- **提交信息**: [Test] Add Stable Audio offline e2e TeaCache Test (#2377)

Signed-off-by: Zhang <jianmusings@gmail.com>
Signed-off-by: Zhang Jian <jianmusings@gmail.com>
Co-authored-by: Claude Opus 4.6 (1M context) <noreply@anthropic.com>

---
