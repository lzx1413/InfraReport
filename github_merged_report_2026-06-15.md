# GitHub Stars 合并报告 - 2026-06-15

**合并日期**: 2026-06-16
**监控日期**: 2026-06-15
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


**报告日期**: 2026-06-16
**监控日期**: 2026-06-15
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2016
- **最后更新**: 2026-06-15T22:42:25Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: 鐘天楽

## AI分析总结

好的，根据您提供的仓库README摘要和提交记录，以下是昨日更新的分析总结：

### 昨日更新要点分析

1.  **主要更新类型**
    *   **功能新增/依赖管理**：本次提交属于功能新增（feat）类别，具体是锁定了一个关键的第三方依赖库（FlashAttention 4）的特定版本。

2.  **关键变更点及其与项目整体方向的关系**
    *   **变更点**：将FlashAttention 4 (FA4) 的版本固定为 `4.0.0b16`。
    *   **与项目方向的关系**：VeOmni 项目的核心目标是“**扩展任意模态模型的训练**”（Scaling Any Modality Model Training）。FlashAttention 是一种广泛用于加速Transformer模型（包括文本、图像、视频等多模态模型）训练和推理的高效注意力机制实现。锁定其版本是为了确保项目依赖环境的**稳定性和可复现性**，避免因上游库的意外更新（如API变更、性能回归或bug）导致VeOmni的训练流程出错或性能波动。这是支撑项目大规模、稳定训练的基础设施保障。

3.  **对项目的影响和潜在意义**
    *   **直接影响**：确保所有使用VeOmni框架的用户和开发者都使用完全一致的FlashAttention版本，从而消除因环境差异导致的“在我机器上能跑”问题。
    *   **潜在意义**：
        *   **可靠性提升**：为VeOmni的分布式训练配方（Recipe Zoo）提供了一个更可靠的底层依赖，尤其是在处理长序列或大规模多模态数据时，FA4的性能至关重要。
        *   **可复现性**：这是科学研究和工程实践中的关键一步，锁定的版本使得论文中的实验结果可以被精确复现。
        *   **为未来升级做准备**：通过明确锁定一个经过充分测试的beta版本，项目团队可以在内部充分验证其稳定性后，再计划性地升级到FA4的正式版或更新版本。

4.  **值得关注的技术点**
    *   **FlashAttention 4 (FA4)**：这是当前最先进的注意力机制加速库之一。锁定其版本表明VeOmni项目紧跟前沿技术，并依赖其来优化多模态模型的训练效率。
    *   **版本锁定策略**：`pip install flash-attn==4.0.0b16` 这种精确到补丁版本的锁定方式，体现了项目对依赖管理的严谨态度，这对于一个旨在成为“分布式训练配方中心”的项目尤为重要。

5.  **基于项目背景，这些提交如何影响项目发展**
    *   结合README中“**Scaling Any Modality Model Training**”的目标，本次提交虽然看似微小，但实际上是**夯实项目地基**的关键一步。它确保了支撑多模态模型训练的核心加速组件（FA4）是稳定可控的。
    *   这有助于VeOmni项目吸引更多用户和贡献者，因为他们可以信赖一个环境一致、结果可复现的平台。稳定的底层依赖是项目从“可用”走向“可靠”和“易用”的必经之路，为未来集成更多复杂模型和训练策略扫清了环境障碍。

## 详细提交记录

### [f3f6be9](https://github.com/ByteDance-Seed/VeOmni/commit/f3f6be9fe3b0794a90de211567265b46c59c0269)

- **作者**: 鐘天楽
- **时间**: 2026-06-15T08:18:06Z
- **提交信息**: [misc] feat: pin FA4 4.0.0b16 (#837)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-06-16
**监控日期**: 2026-06-15
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2406
- **最后更新**: 2026-06-15T20:20:01Z

## 提交统计

- **昨日提交总数**: 5
- **提交者数量**: 4
- **主要提交者**: Shiqiao Gu (谷石桥), Musisoul, XHPlus

## AI分析总结

好的，这是对仓库 `ModelTC/LightX2V` 昨日提交记录的分析总结。

### 1. 主要更新类型

- **功能新增**:
    - 支持通过 `entry_points` 发现外部（out-of-tree）芯片后端插件（#1126）。
    - 新增 `PPU` 平台支持（#1149）。
- **功能增强**:
    - 支持 `Qwen` 模型的 `DMD-LoRA` 训练（#1076）。
    - 支持 `WanT2V` 模型的 `LoRA` 训练（#1148）。
- **Bug修复**:
    - 修复了 `metax` 平台的问题，并更新了 `PPU` 平台（#1150）。

### 2. 关键变更点及其与项目整体方向的关系

- **插件化后端架构 (PR #1126)**: 这是本次更新中最具战略意义的变更。它引入了一套标准的插件机制，允许第三方芯片厂商或开发者无需修改 `LightX2V` 核心代码，就能以独立的 `pip` 包形式集成自己的硬件后端。这与项目“轻量级视频生成推理框架”的定位高度契合，旨在降低新硬件适配的门槛，从而扩大生态。
- **新增PPU平台支持 (PR #1149, #1150)**: 直接为 `PPU-ZW810E` 芯片添加了平台支持，并修复了 `metax` 平台的问题。这体现了项目积极扩展硬件生态，覆盖更多国产芯片（如PPU、Metax）的意图。
- **扩展训练能力 (PR #1076, #1148)**: 为 `Qwen` 和 `WanT2V` 模型添加了 `LoRA` 训练支持。这表明项目不仅关注推理，也在增强其训练能力，特别是支持主流的、高效的微调方法（LoRA），使其成为一个更完整的视频生成模型开发工具。

### 3. 对项目的影响和潜在意义

- **降低社区贡献门槛**: 插件化架构是项目走向成熟和社区化的重要一步。它允许硬件厂商和开发者独立维护和分发自己的后端，无需等待上游合并，极大地加速了新硬件的适配和迭代。
- **增强硬件生态竞争力**: 通过支持PPU等新兴国产芯片，并修复Metax的问题，项目展现了其作为国产AI基础设施的潜力，能够服务于更广泛的国产硬件生态。
- **提升模型开发效率**: 支持 `Qwen` 和 `WanT2V` 的 `LoRA` 训练，为研究人员和开发者提供了更便捷、高效的模型微调手段，有助于推动视频生成领域的应用创新。

### 4. 值得关注的技术点

- **`entry_points` 插件机制**: 这是从 `vLLM` 借鉴的成熟设计模式。它利用Python标准库 `importlib.metadata` 实现，无需引入额外依赖，设计精巧且安全。其关键挑战在于 `set_ai_device()` 函数中扫描插件的时机，必须早于核心注册表的“快照”操作，该PR通过将扫描放在 `init_ai_device()` 和 `registry_factory` 导入之前，巧妙地解决了这个问题。
- **`LoRA` 训练支持**: 对于视频生成模型，`LoRA` 是一种高效的微调方法。支持 `DMD-LoRA`（可能是一种针对扩散模型的变体）和标准 `LoRA`，表明项目在训练功能上紧跟前沿技术。
- **`PPU` 平台**: 这是一个新的硬件后端，其具体实现和性能值得关注，代表了项目对特定领域芯片的支持。

### 5. 基于项目背景，这些提交如何影响项目发展

`LightX2V` 的目标是成为一个“轻量视频生成推理框架”。昨日提交的核心贡献在于：

1.  **从“单一框架”向“开放生态”演进**: 插件化架构是决定性的转折点。它使 `LightX2V` 从一个需要开发者手动适配硬件的框架，转变为一个可以动态发现和加载第三方后端的开放平台。这直接呼应了README中“轻量”和“推理”的定位，通过解耦硬件适配，让框架本身保持轻量和专注。
2.  **巩固“国产芯片友好”的定位**: 通过支持PPU和修复Metax，项目明确地将自己定位为支持国产硬件的解决方案。这在中国AI芯片生态快速发展的背景下，具有重要的战略意义。
3.  **拓展“训练+推理”全链路能力**: 增加对 `Qwen` 和 `WanT2V` 的 `LoRA` 训练支持，使项目不仅仅是一个推理引擎，也开始具备模型微调的能力。这有助于形成一个“训练-微调-部署”的闭环，提升项目的实用价值。

**总结**: 昨日的更新标志着 `LightX2V` 从一个功能性的推理框架，向一个具备强大生态扩展能力和完整模型开发链路的平台迈出了关键一步。插件化架构是其发展的核心驱动力。

## 详细提交记录

### [b07dcbd](https://github.com/ModelTC/LightX2V/commit/b07dcbd8aa928d4f56ab6b9079013ac326c0c8b7)

- **作者**: XHPlus
- **时间**: 2026-06-15T20:12:32Z
- **提交信息**: feat(platform): discover out-of-tree backends via entry points (#1126)

## Motivation

Adding a chip backend to `lightx2v_platform` currently requires editing
in-tree files (`base/__init__.py` to import the `Device` class,
`ops/__init__.py` to add an `elif PLATFORM == ...` branch). That means
every backend must be upstreamed or the user must patch the repo to use
it.

This PR adds an out-of-tree (OOT) plugin seam so a chip backend can be
shipped as a separate pip-installable package and registered at runtime
— the same mechanism vLLM uses for hardware backends via
`vllm.platform_plugins`.

## What changed

`set_ai_device()` now scans the `lightx2v.platform_plugins` entry-point
group and invokes each registered callable before initialising the
device.

A plugin package declares:

```toml
[project.entry-points."lightx2v.platform_plugins"]
my_backend = "my_backend_pkg:register"
```

```python
def register():
    from . import device          # @PLATFORM_DEVICE_REGISTER("my_backend")
    from .ops import register_ops
    register_ops()
```

Then `pip install my-backend-package && PLATFORM=my_backend python
lightx2v/infer.py ...` — no edits to this repo.

## Why the scan sits inside `set_ai_device()`

`lightx2v/utils/registry_factory.py` builds the framework-facing
registries by **copying** the platform staging registries at import
time:

```python
ATTN_WEIGHT_REGISTER.merge(PLATFORM_ATTN_WEIGHT_REGISTER)
MM_WEIGHT_REGISTER.merge(PLATFORM_MM_WEIGHT_REGISTER)
...
```

`merge()` is a one-shot snapshot, not a live view. So a plugin's
registrations are only picked up if they run **before** that import. The
scan is placed:

- **before** `init_ai_device()` — so a plugin-provided device (e.g. its
`PLATFORM` key) is visible to the lookup;
- **before** `from lightx2v_platform.ops import *` — i.e. before
`registry_factory` snapshots the `PLATFORM_*` op tables.

## Safety

- **No behaviour change without plugins** — `entry_points(group=...)`
returns empty; the loop is a no-op. In-tree platforms are untouched.
- **Failure isolation** — a plugin whose `register()` raises is logged
and skipped; it cannot crash `set_ai_device()`.
- **No new dependency** — `importlib.metadata` is stdlib (3.8+); the
`TypeError` branch handles the pre-3.10 dict-like return.

## First consumer

`lightx2v-plugin-FL` (https://github.com/ModelTC/lightx2v-plugin-FL)
uses this hook to expose a `flagos` meta-platform: a single
`PLATFORM=flagos` backend that covers many domestic chips at once by
delegating compute to FlagGems and collective communication to FlagCX,
instead of one hand-written kernel set per chip.

## Test plan

- [x] No-plugin regression: `set_ai_device()` for in-tree platforms
(`cuda`, `ascend_npu`, ...) behaves identically.
- [x] `set_ai_device.py` compiles; scan is a no-op when no entry points
are registered.
- [ ] Plugin discovery (reviewer-runnable): install a stub package
exposing a `lightx2v.platform_plugins` entry point; assert its device
key reaches `PLATFORM_DEVICE_REGISTER` and its op keys reach
`lightx2v.utils.registry_factory` after `import lightx2v`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>
Co-authored-by: Yang Yong (雍洋) <yongyang1030@163.com>

### [8fe8db9](https://github.com/ModelTC/LightX2V/commit/8fe8db9b9d6160244b45332252ab2918f317c68f)

- **作者**: Musisoul
- **时间**: 2026-06-15T19:59:22Z
- **提交信息**: [Train] Support qwen dmd-lora training (#1076)

Co-authored-by: helloyongyang <yongyang1030@163.com>

### [524de26](https://github.com/ModelTC/LightX2V/commit/524de2630e49145e90d6fb3bf626797a9cd00757)

- **作者**: Shiqiao Gu (谷石桥)
- **时间**: 2026-06-15T13:04:06Z
- **提交信息**: support want2v lora train (#1148)

Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>

### [45fecfb](https://github.com/ModelTC/LightX2V/commit/45fecfbb700451b6bb723305c1c4276a577498fa)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-06-15T07:56:51Z
- **提交信息**: fix metax & update ppu (#1150)

### [4a30fca](https://github.com/ModelTC/LightX2V/commit/4a30fca688362c225530b819c41578fb6060b517)

- **作者**: XHPlus
- **时间**: 2026-06-15T07:29:28Z
- **提交信息**: [feat] add PPU platform for PPU-ZW810E (#1149)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-06-16
**监控日期**: 2026-06-15
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2133
- **最后更新**: 2026-06-15T04:04:49Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-06-16
**监控日期**: 2026-06-15
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5797
- **最后更新**: 2026-06-15T21:40:49Z

## 提交统计

- **昨日提交总数**: 5
- **提交者数量**: 4
- **主要提交者**: Brian K. Ryu, Gabriel Wu, Ka-Hyun Nam

## AI分析总结

好的，这是对 `flashinfer-ai/flashinfer` 仓库昨日提交记录的分析总结。

### 1. 主要更新类型

- **功能新增 (Feature)**: 2项
- **Bug修复 (Bug Fix)**: 2项
- **测试改进 (Test Improvement)**: 1项

### 2. 关键变更点及其与项目整体方向的关系

项目 `flashinfer-ai/flashinfer` 的目标是提供**高性能的 GPU 推理内核**。这些提交都紧密围绕这一核心目标，通过修复关键 Bug 和扩展对新硬件架构（Blackwell SM120/121）的支持来强化项目。

- **功能新增：支持 Gemma 4 模型的 `head_dim=512` 注意力机制** (提交 `5b30074`)
    - **变更点**: 为 Blackwell 架构（SM120/121）的 `BatchDecodeWithPagedKVCacheWrapper` 和 `BatchPrefillWithPagedKVCacheWrapper` 等核心 API 添加了 `head_dim=512` 的支持。
    - **与项目方向的关系**: 直接响应了最新一代大模型（如 Gemma 4）对更大注意力头维度的需求，确保 FlashInfer 能持续为前沿模型提供高性能推理支持，巩固其在 GPU 推理内核领域的领先地位。

- **功能新增：为 Blackwell 架构添加稀疏 MLA (Multi-head Latent Attention) 内核** (提交 `f954694`)
    - **变更点**: 为 SM120/SM121 架构添加了稀疏 MLA 的 Decode 和 Prefill 内核，支持 DSv4 和 DSv3.2/GLM-5.1 等主流稀疏注意力方案。
    - **与项目方向的关系**: 这是对项目“高性能”和“推理”方向的重大扩展。稀疏 MLA 是当前提升长上下文推理效率的关键技术，将其移植到最新的 Blackwell 硬件上，使 FlashInfer 能服务于对内存和计算效率有极致要求的推理场景。

- **Bug修复：修复 `grouped_gemm_nt_masked` 中的内存布局校验问题** (提交 `38feb62`)
    - **变更点**: 显式校验 `grouped_gemm_nt_masked` 操作的张量内存布局，防止因布局错误导致的 NaN 值污染。
    - **与项目方向的关系**: 修复了可能导致模型推理结果完全错误（NaN）的严重 Bug，提升了项目的**稳定性和可靠性**，这对于生产环境下的推理至关重要。

- **Bug修复：修复 `SamplingFromLogitsKernel` 中的共享内存竞态和越界 Token ID 问题** (提交 `78d0a06`)
    - **变更点**: 修复了采样内核中因共享内存重用未同步导致的竞态条件，以及可能返回越界 Token ID 的问题。
    - **与项目方向的关系**: 采样是推理流程的最后一步，其正确性直接影响模型输出。此修复消除了一个难以复现的、可能导致生成非法 Token 的 Bug，显著提升了推理结果的**正确性和鲁棒性**。

- **测试改进：对齐 CuTe DSL Decode 测试的输出缩放逻辑** (提交 `a81e6b4`)
    - **变更点**: 修改了 CuTe DSL Decode 的测试代码，使其在 BF16 转换前应用输出缩放，以匹配实际内核的行为。
    - **与项目方向的关系**: 这是一个纯测试改进，旨在消除因浮点数舍入路径不同导致的测试不稳定（Flaky Test），提高了测试套件的**准确性和可信度**，为后续开发提供了更可靠的回归保障。

### 3. 对项目的影响和潜在意义

- **巩固对最新硬件的支持**: 对 Blackwell SM120/121 架构的密集支持（`head_dim=512` 和稀疏 MLA）是本次更新的最大亮点。这标志着 FlashInfer 已准备好为 NVIDIA 最新一代数据中心和消费级 GPU 提供高性能推理能力，对吸引和留住使用最新硬件的用户至关重要。
- **提升生产环境的稳定性**: 修复了 `grouped_gemm` 和 `sampling` 中的两个关键 Bug，直接提升了库在复杂、大规模推理任务中的稳定性和结果正确性，降低了用户在生产环境中遇到“静默错误”（Silent Data Corruption）的风险。
- **扩展对前沿模型架构的支持**: 稀疏 MLA 内核的加入，使 FlashInfer 能够高效支持 DeepSeek-V3/V4 和 GLM-5 等采用稀疏注意力机制的最新模型，保持了项目在技术前沿的竞争力。

### 4. 值得关注的技术点

- **Blackwell 架构适配**: 提交 `5b30074` 和 `f954694` 都涉及对 SM120/121 架构的适配。这包括利用新的硬件特性（如 TMA - Tensor Memory Accelerator）和调整内核调度策略（如 warp-specialization, split-K）来达到最佳性能。
- **稀疏 MLA 的实现**: 提交 `f954694` 详细描述了稀疏 MLA 的实现，包括对“双缓存”（dual cache）的支持，以及如何处理不同版本的稀疏格式（DSv4 vs DSv3.2）。这是一个复杂的系统工程，涉及 JIT 编译、AutoTuner 和新的 CUDA 内核。
- **CUB 库的正确使用**: 提交 `78d0a06` 的 Bug 修复提醒我们，在使用 CUB 等并行原语库时，必须严格遵守其关于线程同步（`__syncthreads()`）的契约，否则在高并发场景下极易引入难以调试的竞

## 详细提交记录

### [38feb62](https://github.com/flashinfer-ai/flashinfer/commit/38feb62b789c70bc0fcc7a7149c1ebe0e49158d7)

- **作者**: Ka-Hyun Nam
- **时间**: 2026-06-15T21:40:44Z
- **提交信息**: [fix] explicitly validate grouped_gemm_nt_masked layout contract to prevent NaN contamination (#3574)

<!-- .github/pull_request_template.md -->

## 📌 Description

See comment here for description of root cause + rationale for PR
change/solution:
https://github.com/flashinfer-ai/flashinfer/issues/3103#issuecomment-4675817973
. Ended up at this issue from debugging this other 2nd issue:
https://github.com/flashinfer-ai/flashinfer/issues/3057#issuecomment-4675866789

## 🔍 Related Issues

[<!-- Link any related issues here
-->](https://github.com/flashinfer-ai/flashinfer/issues/3103)

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
* Prevented silent data corruption in grouped GEMM by enforcing expected
tensor memory-layout for expert/batch dimensions; invalid layouts now
raise an error.

* **Tests**
* Added a regression test that verifies the output-layout validation and
correct expert-dimension ordering (accepts compliant layouts, rejects
non-compliant ones).
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [5b30074](https://github.com/flashinfer-ai/flashinfer/commit/5b3007412da37d6d9e273865234cb47b19ce608c)

- **作者**: Brian K. Ryu
- **时间**: 2026-06-15T18:59:41Z
- **提交信息**: feat(attention): head_dim=512 support for attention prefill & decode for Gemma 4 on SM120/121 (#3576)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

PR adds **head_dim = 512** support to
the`BatchDecodeWithPagedKVCacheWrapper`,
`BatchPrefillWithPagedKVCacheWrapper` and
`BatchPrefillWithRaggedKVCacheWrapper` `backend='fa2'` path for
SM120/121. Head dim 512 is required for Gemma4's global (non-sliding
window) attention layers

Supports
- Prefill and decode
- Q=bfloat16 and KV=bfloat16 or fp8_e4m3 cache targeting Gemma-style
global attention.

Aimed for Blackwell SM12x e.g. RTX PRO 6000 and DGX Spark

### Performance:
Measured on **RTX PRO 6000 (SM120)** and **DGX Spark / GB10 (SM121)**.
Config: batch=1, 32 QO / 8 KV heads (GQA-4), page_size=16, BF16 query +
FP8-e4m3 KV, `s_kv`=8192, causal.

Prefill performance is likely has more headroom. Decode performance is
satisfactory.
  
#### Prefill — `s_qo`=8192 (compute-bound)

  | head_dim | RTX PRO 6000 (TFLOP/s) | DGX Spark (TFLOP/s) |
  |:--------:|:----------------------:|:-------------------:|
  | 128      | 280.8                  | 66.2                |
  | 256      | 213.3                  | 45.7                |
  | 512      | 156.7                  | 34.6                |
  
#### Speculative decode — `s_qo`=8 (KV-bandwidth-bound)    
  
  | head_dim | RTX PRO 6000 (TB/s) | DGX Spark (GB/s) |
  |:--------:|:-------------------:|:----------------:|
  | 128      | 0.43                | 111              |     
  | 256      | 0.55                | 149              |
  | 512      | 0.71                | 180              |
  
#### Decode — `q`=1 (KV-bandwidth-bound)             
  
  | head_dim | RTX PRO 6000 (TB/s) | DGX Spark (GB/s) |
  |:--------:|:-------------------:|:----------------:|
  | 128      | 0.48                | 117              |     
  | 256      | 0.65                | 149              |
  | 512      | 0.79                | 183              |
  
Decode numbers are the native `fa2` decode kernel; the tensor-core
decode path (`fa2_tc`, which rides the prefill kernel) is within ~3%
across all head dims.


## 🔍 Related Issues

<!-- Link any related issues here -->
- #3297

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
* Added explicit support for head-dimension 512 in attention paths;
introduced a new tile-size option and tightened when the holistic
(persistent) kernel is allowed (now limited to head dims ≤256), with
guidance to use paged/ragged or tensor-core decode for larger dims.

* **Bug Fixes**
* FP8 backend filtering now depends on the query dtype only; KV-cache
dtype no longer causes backend skipping.

* **Tests**
* Expanded test coverage to include head-dimension 512 across decode,
FP8 prefill, and sliding-window scenarios.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [78d0a06](https://github.com/flashinfer-ai/flashinfer/commit/78d0a06b7e3a52172f2df030d9f0ed7819391c45)

- **作者**: Ka-Hyun Nam
- **时间**: 2026-06-15T18:19:47Z
- **提交信息**: fix(sampling): fix shared-memory race and out-of-range token id in SamplingFromLogitsKernel (#3624)

<!-- .github/pull_request_template.md -->

## 📌 Description

**Summary**
SamplingFromLogitsKernel reused the CUB BlockReduce shared temp storage
across reduction-loop iterations without a __syncthreads() barrier,
violating CUB's contract. For large vocab (e.g. vocab_size=32000) the
loop runs multiple iterations, so concurrent read/write of the shared
reduction state races and can corrupt the reduced argmax. Combined with
padding lanes (token_idx >= d) keeping their out-of-range index, this
let the kernel occasionally return a token id >= vocab_size, breaking
the invariant 0 <= sample < vocab_size and causing the flaky
test_int64_indices_sampling failure.

**Changes**
Add __syncthreads() after each BlockReduce so the shared temp storage is
safe to reuse next iteration (the actual data race).
Give padding lanes a valid fallback index (0) so the returned token id
is always in [0, d) even under any reduction anomaly.

**Validation**
Verified with compute-sanitizer --tool racecheck: the original kernel
reports hundreds of Write/Read hazards in SamplingFromLogitsKernel; the
fixed kernel reports 0 hazards. sampling_from_logits output stays within
range across repeated runs.

## 🔍 Related Issues

https://github.com/flashinfer-ai/flashinfer/issues/3470

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

* **Refactor**
* Improved internal sampling kernel robustness and thread
synchronization for more reliable concurrent sampling operations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [a81e6b4](https://github.com/flashinfer-ai/flashinfer/commit/a81e6b478f565247477920ac7de049e128bb9c94)

- **作者**: Mingyang Wang
- **时间**: 2026-06-15T17:45:57Z
- **提交信息**: test: match test output scaling with cutedsl kernel (scale before bf16 cast) (#3596)

## 📌 Description

This PR updates the CuTe DSL decode scale tests so they verify the fused
output-scale semantics directly. The paged decode reference now accepts
`o_scale` and applies it while the reference output is still float32,
before the final bf16 cast.

That matches the CuTe DSL kernel path, where `v_scale` is passed through
as `o_scale` and applied before output conversion/store. The previous
test compared against multiplying an already bf16-rounded output, which
created a narrow B300 flake from mismatched rounding paths.

## 🔍 Related Issues

Closes #3505

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [ ] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

Pre-commit note: changed-file pre-commit was attempted with
`PRE_COMMIT_HOME=.cache/pre-commit uv run pre-commit run --files
tests/attention/test_cute_dsl_decode.py`, but hook setup required
network access to fetch third-party hook environments, so this remains
unchecked.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

Validation run:

- `uv run python -m py_compile tests/attention/test_cute_dsl_decode.py`
- `git diff --check`
- `python3 -m pytest
tests/attention/test_cute_dsl_decode.py::test_batch_decode_wrapper_cute_dsl_v_scale
-q`
- `python3 -m pytest
tests/attention/test_cute_dsl_decode.py::test_cute_dsl_decode_paged_wrapper_o_scale
-q`
- `python3 -m pytest tests/attention/test_cute_dsl_decode.py -q`

## Reviewer Notes

Test-only change. No CuTe DSL kernels, public decode API, or unrelated
tolerances were changed. Validation used a Blackwell SM100/B200-class
surface; exact repeated B300 CI proof remains the follow-up trigger if
CI shows another mismatch.

### [f954694](https://github.com/flashinfer-ai/flashinfer/commit/f954694781093138ade24034cc7bd3944c9a94eb)

- **作者**: Gabriel Wu
- **时间**: 2026-06-15T15:55:57Z
- **提交信息**: feat(attention): add SM120 sparse MLA kernels (#3395)

## Summary

Sparse-MLA paged attention for SM120a / SM121a, covering both the DSv4
family
(`d_qk=512`) and the DSv3.2 / GLM-5.1 family (`d_qk=576`). Adds decode
(warp-spec, split-K) and prefill (TMA + warp-spec) kernels in the SM120
sparse
MLA JIT/AOT module, with dispatch through the existing MLA Python APIs.

## Surfaces

The user-facing surface is limited to extending existing MLA entry
points with
SM120/SM121 sparse backend coverage. SM120-specific dispatchers,
runners, and
direct kernel wrappers remain internal implementation details; users
should
continue to call the public `flashinfer.mla` APIs below. The public APIs
keep
their existing decode-oriented names, while the SM120 sparse backend
internally
selects decode or prefill kernels from the flattened token count.

### Public Python APIs

- `flashinfer.mla.trtllm_batch_decode_sparse_mla_dsv4(...)`
  - Extends the DSv4 sparse-MLA decode entry point to SM120/SM121.
  - SM100/SM103 continue to route through the TRTLLM-GEN path.
- SM120/SM121 route through the new packed sparse backend. The SM120
path
accepts BF16 query tensors, a packed uint8 SWA KV cache with 584 bytes
per
token, optional attention sinks, and an optional second packed KV cache
via
    `extra_sparse_indices` / `extra_sparse_topk_lens`.
  - `swa_topk_lens` describes the active SWA segment. When the optional
compressed segment is present, `extra_sparse_topk_lens` describes its
active
    length. Both sparse segments share one online-softmax denominator.

- `flashinfer.mla.trtllm_batch_decode_with_kv_cache_mla(...)`
- Extends the existing MLA decode API with an SM120/SM121 sparse backend
for
DSv3.2 / GLM-style packed sparse MLA (`d_qk=576`, 656 bytes per token).
- With `backend="auto"` on SM120/SM121 and `sparse_mla_top_k > 0`, the
call
selects the sparse backend. `backend="sparse"` selects it explicitly.
  - `kv_scale_format` controls the packed-cache scale convention:
`"auto"` / `"pow2_fp32"` for DSv3.2-style power-of-two FP32 scales, and
    `"arbitrary_fp32"` for GLM-style arbitrary FP32 scales.

### Internal / JIT Implementation Details

-
`flashinfer.mla._sparse_mla_sm120._sparse_mla_sm120_paged_attention(...)`
is
an internal dispatcher that shares validation and buffer handling
between
  decode and prefill shapes. It is registered as the custom op
  `flashinfer::sparse_mla_sm120_paged_attention`.
- `_SparseMLAPagedAttentionRunner` is an internal helper used by tests,
benchmarks, and the public API implementation to own LSE and decode
scratch
  buffers.
- `flashinfer.mla._sparse_mla_sm120.sparse_mla_sm120_decode_dsv4(...)`
and the
DSv3.2 decode wrapper are internal direct kernel wrappers around the JIT
  module and AutoTuner `chunks_per_block` tactic cache.
- `flashinfer.jit.mla.gen_sparse_mla_sm120_module()` wires the new SM120
sparse
  MLA CUDA sources into the JIT/AOT build.

## Performance

RTX PRO 6000 Blackwell Server Edition (SM120a). KV pool sized > L2
(>=600 MB)
so analytical numbers reflect DRAM-bound production. `attn_TFLOPs = 2 *
T *
num_heads * topk * (d_qk + d_v) / latency`.

**DSv4 prefill, single cache** (584 B/slot footer, FP8 paged):

| NH | topk | T | latency us | KV GB/s | TFLOPs |
|---:|---:|---:|---:|---:|---:|
|  16 |  128 |  256 |    53.2 | 359 |  20.2 |
|  64 |  128 |  256 |   108.5 | 176 |  39.6 |
|  64 | 2048 |  256 |   608.3 | 503 | 113.0 |
| 128 | 2048 |  256 |  1171.5 | 261 | 117.3 |
|  64 | 2048 | 1024 |  2096.1 | 584 | 131.1 |
| 128 | 2048 | 1024 |  4110.4 | 298 | 133.8 |

**DSv4 prefill, dual cache** (main SWA cache `topk=128` plus secondary
C4A /
C128A cache, 584 B/slot footer, FP8 paged):

| NH | main topk | extra topk | T | extra PBS | latency us | KV GB/s |
TFLOPs |
|---:|---:|---:|---:|---:|---:|---:|---:|
|  64 | 128 |  512 | 256 | 64 |   239.6 | 399 |  89.6 |
| 128 | 128 |  512 | 512 | 64 |   804.8 | 238 | 106.7 |
| 128 | 128 |  512 | 512 |  2 |   806.9 | 237 | 106.5 |
| 128 | 128 |  768 | 512 |  2 |  1045.5 | 256 | 115.0 |
| 128 | 128 | 1536 | 512 |  2 |  1699.6 | 293 | 131.4 |
| 128 | 128 | 1664 | 512 |  2 |  1813.5 | 296 | 132.6 |

**DSv4 decode** (T=1):

| NH | topk | latency us |
|---:|---:|---:|
|  16 |  128 | 22.4 |
|  64 |  128 | 22.5 |
|  64 |  512 | 22.6 |
| 128 |  512 | 22.6 |
| 128 | 1024 | 24.6 |

**DSv3.2 / GLM-5.1** (656 B/slot inline, FP8 paged, `topk = 2048`):

| NH | T | latency us | KV GB/s | TFLOPs |
|---:|---:|---:|---:|---:|
|  16 |   1 |  22.7 |   59 |   3.2 |
|  16 |  64 | 137.9 |  624 |  33.1 |
|  16 | 256 | 352.3 |  976 |  51.8 |
|  64 |  16 | 111.5 |  193 |  40.9 |
|  64 | 256 | 454.7 |  756 | 160.6 |
| 128 |  16 | 163.9 |  131 |  55.7 |
| 128 | 256 | 811.0 |  424 | 180.1 |

## Testing

```bash
pytest tests/attention/test_sparse_mla_sm120.py
```

122 tests covering decode + prefill, single + dual cache, attention
sink, top-k
length masking, and full DSv4 / DSv3.2 / GLM-5.1 shape coverage. Tests
`compute-sanitizer --tool racecheck` clean on representative shapes.

End-to-end validated by serving **GLM-5.1** and **DSv4-Flash** through
these
kernels.

---------

Signed-off-by: Zihua Wu <13583761+lucifer1004@users.noreply.github.com>
Co-authored-by: leavelet <45084815+leavelet@users.noreply.github.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-06-16
**监控日期**: 2026-06-15
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3712
- **最后更新**: 2026-06-15T14:06:52Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-06-16
**监控日期**: 2026-06-15
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 33861
- **最后更新**: 2026-06-15T20:54:49Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 3
- **主要提交者**: liwd190019, Sayak Paul, YiYi Xu

## AI分析总结

好的，作为专业的代码分析助手，我将结合 `huggingface/diffusers` 项目的背景，对您提供的提交记录进行分析和总结。

---

### 昨日更新要点分析 (`huggingface/diffusers`)

**项目背景参考**：`diffusers` 是一个用于生成图像、音频等的扩散模型库，强调模块化、易用性和社区贡献。其文档和哲学（PHILOSOPHY.md）是指导项目发展方向和社区协作的核心文件。

#### 1. 主要更新类型

本次更新主要由**文档维护**和**Bug修复**构成，没有新增功能或重大性能优化。

-   **文档更新**：提交 `4757c7c` 和 `93d3296` 均属于此类别。
-   **Bug修复**：提交 `d1f8e55` 属于此类别。

#### 2. 关键变更点及其与项目整体方向的关系

-   **文档统一与国际化 (提交 `4757c7c` & `93d3296`)**：
    -   **变更点**：
        1.  将根目录的 `PHILOSOPHY.md` 文件替换为指向 `docs/source/en/conceptual/philosophy.md` 的符号链接（symlink），确保“单一事实来源”。
        2.  修复了因符号链接导致的 GitHub 页面显示问题，将 PR 模板、贡献指南等中的链接从指向 GitHub 原始文件（`blob/main/...`）改为指向渲染后的文档网站。
        3.  添加了中文教程翻译。
    -   **与项目方向的关系**：这与 `diffusers` 项目强调的**社区驱动**和**易用性**高度一致。通过统一文档源、优化链接体验和提供多语言翻译，降低了全球开发者的贡献门槛和使用门槛，符合 Hugging Face 生态系统的国际化战略。

-   **测试修复 (提交 `d1f8e55`)**：
    -   **变更点**：修复了 `consistency decoder`（一致性解码器）相关的测试。
    -   **与项目方向的关系**：`diffusers` 作为生产级库，**代码质量和稳定性**至关重要。修复测试是维护项目健康度的基础工作，确保核心组件（如一致性模型）的可靠性，为后续功能迭代提供保障。

#### 3. 对项目的影响和潜在意义

-   **提升文档维护效率**：将 `PHILOSOPHY.md` 改为符号链接，避免了文档内容重复和不同步的问题，未来更新只需修改一处，降低了维护成本。
-   **改善开发者体验**：修复文档链接，确保贡献者和用户能直接跳转到可读的网页，而不是 GitHub 上的路径占位符，提升了导航体验。
-   **扩大社区影响力**：添加中文教程翻译，直接服务了庞大的中文开发者社区，有助于吸引更多非英语母语的贡献者和用户，促进项目生态繁荣。
-   **增强项目稳定性**：修复一致性解码器的测试，确保了该特定模型功能的正确性，避免了潜在的回归问题。

#### 4. 值得关注的技术点

-   **符号链接（Symlink）策略**：这是一个巧妙且高效的文档管理技巧。在大型项目中，使用符号链接将根目录的说明性文件（如 `README.md`, `CONTRIBUTING.md`, `PHILOSOPHY.md`）指向文档目录下的详细版本，可以避免内容膨胀和同步问题，同时保持根目录的整洁。
-   **链接策略的调整**：从 `blob/main/...` 改为渲染后的文档链接，是一个重要的细节。这反映了项目对“最终用户体验”的重视，即用户应该看到格式良好的文档页面，而不是原始的 Markdown 文件。

#### 5. 基于项目背景，这些提交如何影响项目发展

-   **巩固了项目治理基础**：`diffusers` 项目发展迅速，其哲学和贡献指南是社区协作的基石。本次更新通过技术手段（符号链接）和内容优化（修复链接），确保了这些基石文件的**权威性、一致性和可访问性**。这为项目在更大规模上的有序发展奠定了基础。
-   **加速了全球化进程**：中文教程的加入是项目国际化的重要一步。这表明项目团队正积极地将 `diffusers` 打造为一个真正的全球性工具，而不仅仅是英语世界的项目。这有助于吸引顶尖人才和更广泛的用户群体。
-   **维护了技术信誉**：及时修复测试（即使是小范围的）体现了项目对质量的高要求。对于像 `diffusers` 这样被广泛依赖的库，任何微小的不稳定都可能影响大量下游应用。这种对细节的关注是项目长期健康发展的关键。

**总结**：昨日的更新看似“琐碎”，实则是 `huggingface/diffusers` 项目在**规模化发展**和**全球化扩张**阶段进行的一次重要的“基础设施”维护。它通过优化文档管理和修复测试，提升了项目的可维护性、开发者体验和稳定性，为未来的功能创新和社区增长扫清了障碍。

## 详细提交记录

### [4757c7c](https://github.com/huggingface/diffusers/commit/4757c7c465157ce843294424a5dd9fcd24f52cb2)

- **作者**: YiYi Xu
- **时间**: 2026-06-15T17:39:24Z
- **提交信息**: Make root PHILOSOPHY.md a symlink to the docs philosophy page (#13954)

* Make root PHILOSOPHY.md a symlink to the docs philosophy page

The root PHILOSOPHY.md had drifted into a stale duplicate of
docs/source/en/conceptual/philosophy.md (which was rewritten in #13808 to
cover the single-file model policy and Modular Diffusers). Replace it with a
symlink to the docs file, mirroring CONTRIBUTING.md -> contribution.md, so
there's a single source of truth.

A symlink renders as a path stub (not content) on GitHub, so repoint the
links that pointed at blob/main/PHILOSOPHY.md to the rendered docs site:
the PR template and the English contribution guide.

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

* Point contributor-guide links at the rendered docs site

CONTRIBUTING.md is a symlink, so blob/main/CONTRIBUTING.md renders as a path
stub on GitHub rather than the guide. Repoint the PR template and README
links to the rendered docs page, matching the philosophy/AI-agents links.

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

* Repoint remaining symlink-stub doc links to the rendered docs site

The stale-bot comment and the ko/zh contribution guides still linked to
blob/main/{CONTRIBUTING,PHILOSOPHY}.md, which render as path stubs because
those root files are symlinks. Point them at the rendered docs pages
(localized /ko/ and /zh/ for the translations).

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

---------

Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>

### [93d3296](https://github.com/huggingface/diffusers/commit/93d3296b54d5f28b4b15e3c954662b92584e15c2)

- **作者**: liwd190019
- **时间**: 2026-06-15T15:43:44Z
- **提交信息**: Add tutorial translations in Chinese (#13932)

Add Chinese tutorial translations

### [d1f8e55](https://github.com/huggingface/diffusers/commit/d1f8e55c3b6e3ac42d6303a8805ded1c2a4bdd0e)

- **作者**: Sayak Paul
- **时间**: 2026-06-15T09:08:52Z
- **提交信息**: [tests] fix consistency decoder tests (#13905)

* fix consistency decoder tests

* address feedback

* feedback

* up

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-06-16
**监控日期**: 2026-06-15
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 415
- **最后更新**: 2026-06-15T15:06:16Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-06-16
**监控日期**: 2026-06-15
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12582
- **最后更新**: 2026-06-15T21:13:05Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-06-16
**监控日期**: 2026-06-15
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 29049
- **最后更新**: 2026-06-15T23:14:15Z

## 提交统计

- **昨日提交总数**: 33
- **提交者数量**: 29
- **主要提交者**: zijiexia, littleyellowbicycle, cctry

## AI分析总结

好的，根据您提供的仓库 `sgl-project/sglang` 的README摘要和昨日提交记录，以下是我的分析总结：

### 1. 主要更新类型

- **Bug修复 (Bugfix):** 数量最多，覆盖了多个模块和硬件平台。
- **性能优化 (Performance Optimization):** 针对特定模型、硬件和场景进行了优化。
- **文档更新 (Documentation):** 主要集中在NPU（Ascend）相关的文档完善和修正。
- **功能新增 (Feature):** 新增了使用示例和CI自动化功能。
- **重构 (Refactoring):** 对部分代码和数据结构进行了整理和优化。
- **CI/DevOps:** 改进了持续集成流程和代码所有者配置。

### 2. 关键变更点及其与项目整体方向的关系

- **多硬件平台支持 (Multi-Hardware Support):**
    - **AMD:** 大量提交涉及AMD GPU，包括重构稀疏MLA解码内核、更新AITER库、优化CI镜像等。这表明项目正在积极强化对AMD硬件的支持和性能。
    - **NPU (Ascend):** 多个提交专注于修复NPU的bug、更新文档和添加测试用例。这显示项目正在努力扩展对新兴NPU硬件的支持，并提升其稳定性和可用性。
- **模型与推理优化 (Model & Inference Optimization):**
    - **DeepSeek V4 (DSV4):** 优化了MHC prenorm内核的预热，并重构了稀疏MLA解码内核，直接针对特定高性能模型进行深度优化。
    - **Qwen3.5:** 修复了CUDA双流重叠的性能回归问题，确保了对新模型的高效支持。
    - **MTP (Multi-Token Prediction) / EAGLE:** 修复了多模态模型在使用EAGLE v2投机解码时的崩溃问题，并更新了相关文档，体现了对先进推理加速技术的持续投入。
    - **Diffusion模型:** 优化了因果卷积3D VAE的填充，表明项目不仅限于LLM，也在扩展对扩散模型的支持。
- **系统稳定性与可靠性 (System Stability & Reliability):**
    - **CI改进:** 增加了在服务器启动时回收泄露的 `/dev/shm` 段的逻辑，这是一个重要的系统级稳定性修复，防止因内存泄漏导致服务中断。
    - **Bug修复:** 修复了多个可能导致NaN嵌入、性能回退或崩溃的bug，提升了项目的整体健壮性。

### 3. 对项目的影响和潜在意义

- **提升多硬件生态成熟度:** 对AMD和NPU的持续投入，将显著扩大SGLang的用户基础，使其不局限于NVIDIA GPU，成为一个更通用的推理框架。
- **增强对前沿模型的支持:** 针对DeepSeek V4、Qwen3.5、Minimax-M3等最新模型的优化和修复，确保了SGLang能快速适配并高效运行业界最先进的模型，保持其技术领先性。
- **提高生产环境可靠性:** 修复系统级内存泄漏、投机解码崩溃等问题，直接提升了SGLang在生产环境中的稳定性和可用性，对用户至关重要。
- **降低使用门槛:** 大量的文档更新和示例代码（如OrcaRouter使用示例）有助于新用户快速上手，并帮助现有用户更好地利用高级功能。

### 4. 值得关注的技术点

- **投机解码 (Speculative Decoding) 的深度优化:** 对EAGLE v2和MTP的修复和优化表明，SGLang在投机解码这一关键加速技术上投入了大量精力，这是提升LLM推理吞吐量的核心手段。
- **针对特定硬件的内核级优化:** 如 `[AMD] refactor sparse MLA decode kernel` 和 `[dsv4] Prewarm MHC prenorm kernel`，这些是深入到GPU底层计算内核的优化，能带来显著的性能提升。
- **系统级稳定性修复:** `[CI] Reclaim leaked /dev/shm segments` 是一个典型的运维痛点解决方案，体现了项目对生产环境细节的关注。
- **多模态模型支持:** 修复多模态模型在投机解码下的bug，表明项目正在积极扩展其多模态能力，这是当前AI应用的主流趋势。

### 5. 基于项目背景，这些提交如何影响项目发展

根据README，SGLang是一个专注于**高性能LLM推理**的框架，其核心目标是**速度**和**灵活性**。

- **强化“速度”优势:** 大量的性能优化（DSV4、Qwen3.5、Diffusion模型、投机解码）直接服务于“速度”这一核心目标，确保SGLang在推理性能上保持领先。
- **扩展“灵活性”边界:** 对AMD、NPU等非NVIDIA硬件的支持，以及对Diffusion模型、多模态模型的支持，极大地扩展了SGLang的“灵活性”，使其能服务于更广泛的硬件和模型生态。
- **提升“生产就绪”程度:** 系统级稳定性修复、CI改进、文档完善，这些工作虽然不直接提升性能，但极大地提升了SGLang作为生产级工具的可靠性和易用性，这是从实验性项目走向成熟产品的关键一步。
- **紧跟社区与前沿:** 对DeepSeek V4、Qwen3.5、Minimax-M3等最新模型和技术的快速跟进，表明SGLang社区非常活跃，能够迅速响应并集成AI领域的最新进展，这对于保持项目生命力至关重要。

**总结来说，昨日的更新体现了SGLang项目在“保持性能领先”的同时，正全力向“多硬件、多模型、生产级”的方向发展，旨在成为一个更通用、更可靠、更

## 详细提交记录

### [cad43d3](https://github.com/sgl-project/sglang/commit/cad43d3212c8c227073a5edf4cb10e1f123e02bd)

- **作者**: Kangyan-Zhou
- **时间**: 2026-06-15T23:14:08Z
- **提交信息**: [CI] Reclaim leaked /dev/shm segments on server startup (#28089)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [7221be2](https://github.com/sgl-project/sglang/commit/7221be2cec428ea7e2f452b6878aa603ba312c9b)

- **作者**: zijiexia
- **时间**: 2026-06-15T22:53:01Z
- **提交信息**: feat(cookbook): MTP --max-running-requests callout + skill sync (#28340)

Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [4c0457f](https://github.com/sgl-project/sglang/commit/4c0457f44081152090a61924de9b94e13663c95a)

- **作者**: Baizhou Zhang
- **时间**: 2026-06-15T21:42:01Z
- **提交信息**: [misc] Update codeowner (#28342)

### [3a0dd69](https://github.com/sgl-project/sglang/commit/3a0dd69f8e7e187292332ba5fbbad96c25c6817b)

- **作者**: Yi Zhong
- **时间**: 2026-06-15T21:39:10Z
- **提交信息**: Minor refactorings to the LFM2.5 cookbook for accuracy (#28072)

### [30d8ee8](https://github.com/sgl-project/sglang/commit/30d8ee87b01611f492d9a8cdcb1f55e37e56858f)

- **作者**: jinhaosong-source
- **时间**: 2026-06-15T21:15:26Z
- **提交信息**: Add OrcaRouter usage example (#28004)

### [4ed698a](https://github.com/sgl-project/sglang/commit/4ed698a491122859f86775bfd3ab6b90da587b9b)

- **作者**: Jia Guo
- **时间**: 2026-06-15T20:46:22Z
- **提交信息**: fix(fa3): no NaN embeddings with fa_skip_kv_cache under piecewise CUDA graph (#27343)

### [f870bf1](https://github.com/sgl-project/sglang/commit/f870bf1ed0d7c95775ee5908d616e3692197563d)

- **作者**: YAMY
- **时间**: 2026-06-15T20:26:26Z
- **提交信息**: [dsv4] Prewarm MHC prenorm kernel at startup (#27986)

### [7e629a2](https://github.com/sgl-project/sglang/commit/7e629a2f8cc5f491ca5e25aab8cc69c8dcf1875e)

- **作者**: Lianmin Zheng
- **时间**: 2026-06-15T20:07:50Z
- **提交信息**: Allow overriding tokenizer path in benchmark harness (#28280)

Co-authored-by: Ian O'Connell <ianoc@meta.com>

### [33719cf](https://github.com/sgl-project/sglang/commit/33719cfb317b1dd7fb86289e77d04f2ea63f0926)

- **作者**: cctry
- **时间**: 2026-06-15T18:01:55Z
- **提交信息**: [PD] Optimize SWA allocation (#28085)

Co-authored-by: cctry <cctry@fb.com>
Co-authored-by: Lianmin Zheng <lianminzheng@gmail.com>

### [19e8586](https://github.com/sgl-project/sglang/commit/19e85868f616b885755cb567246517fc30502dc2)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-06-15T14:50:16Z
- **提交信息**: [AMD] Point AITER scout at amd/aiter-ci (#28313)

Co-authored-by: bingxche <bingxche@amd.com>

### [378e66d](https://github.com/sgl-project/sglang/commit/378e66d2488bf9078580ce8fe679f59fbd332901)

- **作者**: Shangming Cai
- **时间**: 2026-06-15T14:36:05Z
- **提交信息**: [PD] Remove outdated backend whitelist for decode radix cache (#28238)

Signed-off-by: Shangming Cai <csmthu@gmail.com>

### [20f4272](https://github.com/sgl-project/sglang/commit/20f4272109083ca607c8106aa0c8896a0fe4756f)

- **作者**: Trevor Morris
- **时间**: 2026-06-15T13:45:09Z
- **提交信息**: fix: Fix DSR1 perf regression due to unnecessarily falling back to triton gemm (#28073)

### [d5899b9](https://github.com/sgl-project/sglang/commit/d5899b95c4d54db58d5412b9ce0cc487b212d9a0)

- **作者**: YAMY
- **时间**: 2026-06-15T13:44:21Z
- **提交信息**: fix(qwen3.5): keep CUDA dual-stream overlap (regressed by #25885) (#27868)

### [09e9c4f](https://github.com/sgl-project/sglang/commit/09e9c4fde3b4326c4a66fbb014d9c7a6b8995b30)

- **作者**: littleyellowbicycle
- **时间**: 2026-06-15T13:31:39Z
- **提交信息**: 【bugfix】The NPU's forward_dsa_prepare_npu also needs special handling for is_nextn (#28118)

### [e985422](https://github.com/sgl-project/sglang/commit/e985422b2b0e4fa5a21f119a31a195029789c24e)

- **作者**: Kurkur
- **时间**: 2026-06-15T13:30:45Z
- **提交信息**: [Fix][MTP][MM] Fix EAGLE v2 chunked-prefill next-token chain crash on multimodal models due to placeholder tokens (#27863)

### [81166f3](https://github.com/sgl-project/sglang/commit/81166f382d60c88daf45b0e974137df2fec7325a)

- **作者**: qinsir5522
- **时间**: 2026-06-15T13:12:18Z
- **提交信息**: Fix inaccuracies and add NPU constraints in ascend_npu_profiling.mdx. (#28283)

### [f8d1d39](https://github.com/sgl-project/sglang/commit/f8d1d397b6e2f38a38de406156c9baa9186d69fe)

- **作者**: jianzhao-xu
- **时间**: 2026-06-15T13:11:55Z
- **提交信息**: [NPU] fix ascend_docs (#28279)

### [8bdb007](https://github.com/sgl-project/sglang/commit/8bdb007e588e6f83f0162f7b462bf87a7ed35541)

- **作者**: McZyWu
- **时间**: 2026-06-15T12:28:18Z
- **提交信息**: [NPU] Docs op performance optimize (#28277)

### [818808d](https://github.com/sgl-project/sglang/commit/818808d15272ec6918034b6b467846fa0b51f519)

- **作者**: Mick
- **时间**: 2026-06-15T12:18:08Z
- **提交信息**: [diffusion] optimize: optimize causal conv3d vae padding (#28204)

### [f768344](https://github.com/sgl-project/sglang/commit/f768344b1a01ffd2cb8ab4f5904945e2ea11896c)

- **作者**: loading66
- **时间**: 2026-06-15T12:06:05Z
- **提交信息**: [DOCS][NPU]Supplementary Notes (#28295)

### [7bd1a9d](https://github.com/sgl-project/sglang/commit/7bd1a9d1638d5c21abf625f0e5ab5cfb77dff29d)

- **作者**: longxin9715
- **时间**: 2026-06-15T12:02:50Z
- **提交信息**:  Update documentation for Ascend NPU Guide (#28284)

### [edd5eff](https://github.com/sgl-project/sglang/commit/edd5eff5198136d8de2bbd52298d7415f64dff56)

- **作者**: amote-i
- **时间**: 2026-06-15T11:58:33Z
- **提交信息**: [NPU] [DOC] fix issues in ascend_npu_support_new_models (#28296)

### [3df6e2f](https://github.com/sgl-project/sglang/commit/3df6e2f9681a5f926d3b73286d19de9fa76b44a2)

- **作者**: iridiumine
- **时间**: 2026-06-15T11:57:49Z
- **提交信息**: [NPU] Add MiMo-V2-Flash manual testcases (#28223)

### [eb349ef](https://github.com/sgl-project/sglang/commit/eb349efb14606d78c29bafd2cfe91764e3d65fed)

- **作者**: Yuang Chen
- **时间**: 2026-06-15T11:47:52Z
- **提交信息**: [EPD][BugFix] Fix encode_with_global_cache_mooncake (#28031)

Co-authored-by: 晟海 <huangtingwei.htw@antgroup.com>
Co-authored-by: Michael Qiu <qiudayu.qdy@antgroup.com>

### [c4ec39a](https://github.com/sgl-project/sglang/commit/c4ec39a785c5ef543bd61a32a5bc284a2d1abc75)

- **作者**: amd-danli103
- **时间**: 2026-06-15T10:26:59Z
- **提交信息**: [AMD] refactor sparse MLA decode kernel for Deepseek V4 triton backend (#28265)

Co-authored-by: Raiden-Makoto <Raiden-Makoto@users.noreply.github.com>
Co-authored-by: yichiche@amd.com <jacky.cheng>

### [da12f36](https://github.com/sgl-project/sglang/commit/da12f36629a1774bfab156f17ce87faa93a4e1e7)

- **作者**: Thomas Wang
- **时间**: 2026-06-15T09:59:01Z
- **提交信息**: [AMD] Refactor unified_kv attention metadata to data class and fuse c4/128 out_loc (#28275)

### [3b419f6](https://github.com/sgl-project/sglang/commit/3b419f66da7f64a62d65f7d3ac362eafa65020fa)

- **作者**: Lianmin Zheng
- **时间**: 2026-06-15T09:58:14Z
- **提交信息**: [JIT] Track angle-bracket includes in source hash (#28273)

Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>

### [2a33724](https://github.com/sgl-project/sglang/commit/2a33724c9b22e403893b68399042eb149473f6c5)

- **作者**: Zhonghua Deng
- **时间**: 2026-06-15T09:47:47Z
- **提交信息**: [perf] Reuse a pooled HTTP session for multimodal URL downloads (#28056)

Signed-off-by: Abatom <abzhonghua@gmail.com>

### [bf186cf](https://github.com/sgl-project/sglang/commit/bf186cf8fc05b687c9f00e47f283760d2996b244)

- **作者**: McZyWu
- **时间**: 2026-06-15T09:24:10Z
- **提交信息**: bugfix revise interface get cpu copy for npu mem pool to align with gpu (#27802)

### [1180b70](https://github.com/sgl-project/sglang/commit/1180b7044080ae220d17cfe4f24bd3c4018f978b)

- **作者**: monkeyLoveding
- **时间**: 2026-06-15T09:20:19Z
- **提交信息**: triton-ascend update (#27624)

### [9864059](https://github.com/sgl-project/sglang/commit/9864059e2b26f4c6601abe6989156fa71465bacb)

- **作者**: Bingxu Chen
- **时间**: 2026-06-15T09:04:34Z
- **提交信息**: [AMD] Update AITER commit (#28249)

### [19c7855](https://github.com/sgl-project/sglang/commit/19c78552dc8a29da1b9a9627755ec5925da11838)

- **作者**: Bingxu Chen
- **时间**: 2026-06-15T08:08:48Z
- **提交信息**: [AMD] Restrict CI image fallback to versioned tags (#28263)

Co-authored-by: Cursor <cursoragent@cursor.com>

### [33f9983](https://github.com/sgl-project/sglang/commit/33f99831f8723098296c3028890db46c9c1a3082)

- **作者**: Xinyuan Tong
- **时间**: 2026-06-15T07:15:38Z
- **提交信息**: docs(minimax-m3): refresh B200 benchmarks (tp8, piecewise) + add GPQA (#28207)

Co-authored-by: zijiexia <37504505+zijiexia@users.noreply.github.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-06-16
**监控日期**: 2026-06-15
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1202
- **最后更新**: 2026-06-15T12:08:48Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

好的，根据您提供的仓库README摘要和提交记录，以下是昨日更新的要点分析：

### 1. 主要更新类型
- **文档更新 (Documentation Update)**

### 2. 关键变更点及其与项目整体方向的关系
- **变更点**：修复了DMD（可能指“Diffusion Model Distillation”或类似技术）相关的文档（`chore: fix dmd docs`）。
- **与项目方向的关系**：`cache-dit` 是一个专注于DiT（Diffusion Transformers）推理加速的引擎，其核心功能包括缓存、并行化、量化和CPU卸载。DMD作为一种模型蒸馏或加速技术，与项目“提升DiT推理效率”的核心目标高度相关。修复其文档有助于用户正确理解和使用该功能，从而更好地利用`cache-dit`进行加速。

### 3. 对项目的影响和潜在意义
- **直接影响**：提高了项目文档的准确性和可用性，减少了用户因文档错误而产生的困惑。
- **潜在意义**：清晰的文档是开源项目吸引和留住用户的关键。这次修复表明项目团队重视用户体验，并持续维护项目质量，有助于提升项目的专业形象和社区信任度。

### 4. 值得关注的技术点
- **DMD技术**：虽然本次提交只是文档修复，但它暗示了`cache-dit`可能集成了DMD（扩散模型蒸馏）这类高级加速技术。这值得关注，因为它可能代表了项目在模型压缩和推理加速方面的前沿探索，与量化、缓存等技术形成互补。

### 5. 基于项目背景，这些提交如何影响项目发展
- **巩固核心功能**：通过完善DMD相关文档，项目团队确保了用户能正确使用这一关键加速特性，从而让`cache-dit`的“缓存、并行化、量化、CPU卸载”等核心能力与DMD技术更好地协同工作，强化了其作为“PyTorch原生DiT推理引擎”的定位。
- **提升用户采纳率**：高质量的文档降低了使用门槛，有助于吸引更多开发者尝试和采用`cache-dit`，从而推动项目在DiT推理加速领域的普及和发展。

## 详细提交记录

### [eb0ec99](https://github.com/vipshop/cache-dit/commit/eb0ec99f2492c31c3c8798f15ea72d10fddd0d47)

- **作者**: DefTruth
- **时间**: 2026-06-15T12:08:39Z
- **提交信息**: chore: fix dmd docs (#1060)

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-06-16
**监控日期**: 2026-06-15
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 82968
- **最后更新**: 2026-06-15T23:12:14Z

## 提交统计

- **昨日提交总数**: 24
- **提交者数量**: 22
- **主要提交者**: Jee Jee Li, Flora Feng, yzong-rh

## AI分析总结

好的，这是对 vllm-project/vllm 仓库昨日提交记录的分析总结。

### 1. 主要更新类型

- **Bug修复 (Bugfix):** 占比最高，涉及多个核心模块。
- **功能新增 (Feature):** 包括新模型支持、新功能实现。
- **性能优化 (Performance):** 针对特定场景的吞吐量提升。
- **重构 (Refactor):** 代码清理和架构统一。
- **文档更新 (Docs):** 安装指南和在线服务文档。
- **安全增强 (Security):** 文件上传大小限制。
- **硬件支持 (Hardware):** 针对 AMD、Intel XPU 的修复和适配。

### 2. 关键变更点及其与项目整体方向的关系

- **新模型支持 (MiniMax M3, MiMo v2.x 修复):** 持续扩展支持的模型生态，符合项目“为所有人提供LLM服务”的目标。
- **NIXL EP (Expert Parallelism) 增强:** 优化了NVIDIA GPU上的专家并行推理，包括数据类型处理和索引查询，直接提升模型推理效率。
- **性能优化 (DSv4 Prefill Chunking):** 通过优化预填充阶段的块规划，实现了4.0%的端到端吞吐量提升，直接兑现了“快速、便宜”的承诺。
- **KV Cache 管理修复:** 修复了异步调度下的块释放问题、跨组前缀缓存命中问题，以及实现了KV卸载的缓存重置功能。这些是保障长序列推理和内存效率的关键。
- **前端/API 重构与修复:** 统一了推理/工具解析器，修复了 `parallel_tool_calls` 的行为，并清理了聊天补全的代码。这提升了API的稳定性和一致性，是项目成熟化的标志。
- **安全增强:** 在音频上传时增加大小限制，防止恶意文件导致内存耗尽，增强了服务的安全性。
- **硬件适配 (AMD, Intel XPU):** 修复了AMD上的量化层跳过逻辑，跳过了Intel XPU上不支持的测试，体现了项目对多硬件平台的支持承诺。

### 3. 对项目的影响和潜在意义

- **稳定性和可靠性提升:** 大量的Bug修复（尤其是KV Cache和调度相关）直接提升了生产环境下的稳定性，减少了因内存管理或并发问题导致的错误。
- **性能提升:** DSv4的优化和NIXL EP的改进，将直接转化为用户可感知的更低延迟和更高吞吐量，增强了项目的竞争力。
- **开发者体验改善:** 代码重构和文档更新降低了新贡献者的参与门槛，并使API行为更可预测。
- **安全加固:** 文件上传限制是重要的安全实践，对于提供公共服务的部署至关重要。
- **生态扩展:** 支持MiniMax M3等新模型，吸引了更广泛的用户群体。

### 4. 值得关注的技术点

- **NIXL EP 与 NVFP4:** 提交 `ab8b0fe` 跳过了NVFP4（一种4位浮点格式）的后接收量化，这表明项目正在积极探索和优化低精度计算路径，以在保证精度的同时最大化性能。
- **异步调度 + PD KV Consumer 的块释放:** 提交 `d467a2a` 修复了一个复杂的并发问题，确保在异步调度和前缀缓存（PD）场景下，内存块不会在仍有请求使用时被提前释放。这是对vLLM核心调度器健壮性的重要增强。
- **DSv4 Prefill Chunking 优化:** 提交 `e18fe93` 通过算法优化提升了4%的吞吐量，说明在推理的预填充阶段仍有显著的优化空间，是持续性能改进的体现。
- **Triton KV Cache 架构检查:** 提交 `fa63bb9` 移除了冗余的断言，并强制要求FP8 KV Cache需要sm89（Ada Lovelace架构）及以上支持，这有助于在支持的硬件上获得最佳性能，并避免在不支持的硬件上出现难以调试的错误。

### 5. 基于项目背景的综合分析

vLLM 的核心目标是提供“**简单、快速、便宜的LLM服务**”。昨日的提交记录清晰地围绕这一目标展开：

- **“快速”和“便宜”**：通过性能优化（DSv4 Prefill）、专家并行优化（NIXL EP）和低精度计算支持（NVFP4），直接提升了推理速度和降低了计算成本。
- **“简单”**：通过修复API行为（`parallel_tool_calls`）、重构前端代码（统一Parser）、更新文档，降低了用户的使用和部署复杂度。
- **“为所有人”**：通过支持新模型（MiniMax M3）、修复多硬件平台问题（AMD, Intel XPU），扩大了项目的适用范围。

总的来说，昨日的更新是一次典型的、高质量的维护和增强迭代。它**在巩固项目稳定性和安全性的基础上，持续进行性能优化和生态扩展**，这对于一个旨在成为生产级LLM服务引擎的项目至关重要。这些提交表明vLLM正在从一个快速发展的项目，向一个更加成熟、稳定、可靠的平台迈进。

## 详细提交记录

### [16e9117](https://github.com/vllm-project/vllm/commit/16e91176cf77bf0f40ae48da22365a5e21b517af)

- **作者**: Itay Alroy
- **时间**: 2026-06-15T22:50:18Z
- **提交信息**: [EP] Query NIXL EP top-k index dtype (#45298)

Signed-off-by: Itay Alroy <ialroy@nvidia.com>

### [ab8b0fe](https://github.com/vllm-project/vllm/commit/ab8b0fe338d02df87b0844ead99b0a0f2cfb638c)

- **作者**: Itay Alroy
- **时间**: 2026-06-15T22:42:05Z
- **提交信息**: nixl_ep: Skip post-receive quantization for NVFP4 (#45606)

Signed-off-by: Itay Alroy <ialroy@nvidia.com>

### [d467a2a](https://github.com/vllm-project/vllm/commit/d467a2a7f2f088dd360c7bef2f3cf5c59a1ffde8)

- **作者**: llx
- **时间**: 2026-06-15T21:36:09Z
- **提交信息**: [Bugfix] Defer block freeing until in-flight steps finish under async scheduling + PD KV consumer (#45357)

Signed-off-by: llx-08 <2596671364@qq.com>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Jiangyun Zhu <riverclouds.zhu@qq.com>

### [76a373e](https://github.com/vllm-project/vllm/commit/76a373eff47a35f828636774b63ba0315e8f15d0)

- **作者**: Ben Browning
- **时间**: 2026-06-15T21:34:07Z
- **提交信息**: [Frontend] Replace legacy Gemma4 parsers with engine-based implementation (#45588)

Signed-off-by: Ben Browning <bbrownin@redhat.com>
Co-authored-by: Flora Feng <4florafeng@gmail.com>

### [25ee659](https://github.com/vllm-project/vllm/commit/25ee659db01f42747e87e784c139c0686f2cada6)

- **作者**: Zang Peiyu
- **时间**: 2026-06-15T21:14:10Z
- **提交信息**: Fix parallel_tool_calls: null treated as false instead of default true (#44955)

Signed-off-by: factnn <166481866+factnn@users.noreply.github.com>

### [eacff17](https://github.com/vllm-project/vllm/commit/eacff17c8d574daea685387216b6bb23959ab2b1)

- **作者**: Jee Jee Li
- **时间**: 2026-06-15T20:17:23Z
- **提交信息**: [Model Runner V2][Bugfix] Fix MRV2 LoRA warmup (#35536)

Signed-off-by: Jee Jee Li <pandaleefree@gmail.com>
Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>
Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Woosuk Kwon <woosuk@inferact.ai>

### [cd9078f](https://github.com/vllm-project/vllm/commit/cd9078fe59111b02459320108bae8f72b1ddf569)

- **作者**: Flora Feng
- **时间**: 2026-06-15T19:55:31Z
- **提交信息**: [Frontend] Skip structural tags for auto tool_choice without strict mode (#45600)

Signed-off-by: sfeng33 <4florafeng@gmail.com>

### [e18fe93](https://github.com/vllm-project/vllm/commit/e18fe932ca61fbdcf9575989c75fefa8ff8d701b)

- **作者**: Wentao Ye
- **时间**: 2026-06-15T19:50:21Z
- **提交信息**: [Perf] Optimize DSv4 prefill chunk planning, 4.0% E2E Throughput Improvement (#45061)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [51ec5cf](https://github.com/vllm-project/vllm/commit/51ec5cf08f4e3e6f55f51edfbbc29c645f1c4dcd)

- **作者**: yzong-rh
- **时间**: 2026-06-15T18:45:19Z
- **提交信息**: [Bugfix] Chat Completions Harmony Refactor Clean up (#45464)

Signed-off-by: Yifan Zong <yzong@redhat.com>
Co-authored-by: Ben Browning <bbrownin@redhat.com>

### [7e612a0](https://github.com/vllm-project/vllm/commit/7e612a0f06ad9e31b4609726266fea3cfb0883fe)

- **作者**: Ronen Schaffer
- **时间**: 2026-06-15T18:42:53Z
- **提交信息**: [KV Offloading] Implement `reset_cache` for `TieringOffloadingManager` (#44541)

Signed-off-by: Ronen Schaffer <ronen.schaffer@ibm.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [0a1c503](https://github.com/vllm-project/vllm/commit/0a1c5034f5e4fe736db672010cda33d9d850f87e)

- **作者**: youkaichao
- **时间**: 2026-06-15T17:01:25Z
- **提交信息**: [Model] Add MiniMax M3 support (#45381)

Signed-off-by: youkaichao <youkaichao@gmail.com>
Signed-off-by: Isotr0py <mozf@mail2.sysu.edu.cn>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Signed-off-by: Jee Jee Li <pandaleefree@gmail.com>
Signed-off-by: functionstackx <47992694+functionstackx@users.noreply.github.com>
Signed-off-by: Yongye Zhu <zyy1102000@gmail.com>
Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: Isotr0py <mozf@mail2.sysu.edu.cn>
Co-authored-by: Thien Tran <gau.nernst@yahoo.com.sg>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Jee Jee Li <pandaleefree@gmail.com>
Co-authored-by: Roger Wang <hey@rogerw.io>
Co-authored-by: functionstackx <47992694+functionstackx@users.noreply.github.com>
Co-authored-by: Yongye Zhu <zyy1102000@gmail.com>
Co-authored-by: Jee Jee Li <jeejeelee@inferact.ai>

### [a3195fa](https://github.com/vllm-project/vllm/commit/a3195fab7b1227e75403fef83891e961e69228a6)

- **作者**: RoyWang
- **时间**: 2026-06-15T16:37:52Z
- **提交信息**: [AMD][Bugfix][Quantization] Honor fused-name match in is_layer_skipped (#43981)

### [0d80979](https://github.com/vllm-project/vllm/commit/0d80979644e0237b6ef02ce0601dc0bd654e357b)

- **作者**: Flora Feng
- **时间**: 2026-06-15T15:16:45Z
- **提交信息**: [Chore] Consolidate reasoning/tool parser attributes into unified Parser in chat serving (#45548)

Signed-off-by: sfeng33 <4florafeng@gmail.com>

### [588db18](https://github.com/vllm-project/vllm/commit/588db1836245bb40589d45b3e87048a53a13cfe5)

- **作者**: Saddss
- **时间**: 2026-06-15T14:39:59Z
- **提交信息**: [Bugfix] Two-phase KV allocation for cross-group prefix cache hits (supersedes #33775) (#44409)

Signed-off-by: Saddss <2872669061@qq.com>

### [fa63bb9](https://github.com/vllm-project/vllm/commit/fa63bb9db6f48108077fb5497081f7189092d163)

- **作者**: Mike G
- **时间**: 2026-06-15T13:49:57Z
- **提交信息**: Remove redundant Triton KV cache dtype asserts and enforce architectural support (fp8 >= sm89) (#43914)

Signed-off-by: Mike G <180722391+mikekg@users.noreply.github.com>
Co-authored-by: Michael Gschwind <mgschwind@nvidia.com>

### [5ed15f4](https://github.com/vllm-project/vllm/commit/5ed15f42b93d4ea7b40f4dfc2dd7f12a44c99d75)

- **作者**: Xin He
- **时间**: 2026-06-15T13:04:54Z
- **提交信息**: Fix the E8M0 scale computation in the MXFP4 (W4A4) MOE CUTLASS kernel (#43557)

Signed-off-by: Xin He <xin3.he@intel.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [b997071](https://github.com/vllm-project/vllm/commit/b997071ec493765abbed990c65843ed05e4708a8)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-06-15T10:25:24Z
- **提交信息**: (security) Enforce audio upload size limit before full file materialization (#45510)

Signed-off-by: jperezde <jperezde@redhat.com>

### [6c5872e](https://github.com/vllm-project/vllm/commit/6c5872efc5fca7a53f5f3aa589e8cb7896d98618)

- **作者**: Martin Kukla
- **时间**: 2026-06-15T09:31:57Z
- **提交信息**: [Bugfix] Unset HF's default max_new_tokens for DiffusionGemma (#45417)

Signed-off-by: Martin Kukla <martin.kukla@cantab.net>

### [1d88c4d](https://github.com/vllm-project/vllm/commit/1d88c4daddb267173f69901dfbcbb20b21046fa4)

- **作者**: wang.yuqi
- **时间**: 2026-06-15T09:23:36Z
- **提交信息**: [Docs] Update the online serving docs. (#45676)

Signed-off-by: wang.yuqi <yuqi.wang@daocloud.io>

### [25c53d1](https://github.com/vllm-project/vllm/commit/25c53d129302d354272e0a433fdac129be049e72)

- **作者**: vllmellm
- **时间**: 2026-06-15T09:22:55Z
- **提交信息**: [ROCm][Doc] Add installation notes about python version requirement (#45671)

Signed-off-by: vllmellm <vllm.ellm@embeddedllm.com>

### [9872921](https://github.com/vllm-project/vllm/commit/9872921c5f5e733a4f46943562c0a31c9ff69493)

- **作者**: Yejing Lai
- **时间**: 2026-06-15T08:46:30Z
- **提交信息**: [XPU] skip UT test_with_ngram_gpu_spec_decoding (#44423)

Signed-off-by: Lai, Yejing <yejing.lai@intel.com>

### [c17e2f7](https://github.com/vllm-project/vllm/commit/c17e2f7c84d28dfcf5e8cfcc3c5c10bd3caad8b5)

- **作者**: Reid
- **时间**: 2026-06-15T08:05:10Z
- **提交信息**: [Bugfix][Rust Frontend] Make metrics respect --served-model-name (#45465)

Signed-off-by: reidliu41 <reid201711@gmail.com>

### [40eac9a](https://github.com/vllm-project/vllm/commit/40eac9a9d92bba51ad49ca777a5517ee212ea394)

- **作者**: FAUST
- **时间**: 2026-06-15T07:50:48Z
- **提交信息**: [Rust Frontend] Support `parallel_tool_calls = false` (#44760)

Signed-off-by: zhoujinyu <2319109590@qq.com>

### [b5adb02](https://github.com/vllm-project/vllm/commit/b5adb027ad03c29b46181752ba3b1cb84eff1dd4)

- **作者**: Giancarlo Delfin
- **时间**: 2026-06-15T07:13:34Z
- **提交信息**: [Models] Fix MiMo v2.x QKV TP sharding + FP4 support (#45200)

Signed-off-by: Giancarlo Delfin <gdelfin@inferact.ai>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-06-16
**监控日期**: 2026-06-15
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 5150
- **最后更新**: 2026-06-15T21:31:23Z

## 提交统计

- **昨日提交总数**: 9
- **提交者数量**: 9
- **主要提交者**: wangyu, Chendi.Xue, dengyunyang

## AI分析总结

好的，根据您提供的仓库README摘要和提交记录，以下是对昨日更新的分析总结：

### 1. 主要更新类型

*   **Bug修复**：修复了测试标记错误、张量并行注意力问题、音频克隆逻辑。
*   **性能优化**：移除了同步逻辑，引入了分组步进批处理。
*   **新功能**：支持了新的策略服务器（DROID）用于Cosmos3 OpenPI。
*   **重构**：提取了扩散输出格式化的边界。
*   **CI/构建**：优化了CI流程，跳过特定标记变更的测试。
*   **文档/社区**：更新了微信二维码。

### 2. 关键变更点及其与项目整体方向的关系

*   **`[Perf][HunyuanImage] remove sync logic`**：移除了HunyuanImage模型中的同步逻辑。这直接服务于项目“快速”和“便宜”的目标，通过减少不必要的等待来提升推理吞吐量。
*   **`[Feature] Add HunyuanImage3 DiT grouped step batching`**：为HunyuanImage3模型引入了分组步进批处理。这是对扩散模型（DiT）推理的深度优化，旨在提高GPU利用率和处理效率，是项目“快速”和“便宜”目标的核心技术实现。
*   **`[Bugfix] Fix LTX-2.3 tensor-parallel gated attention`**：修复了LTX-2.3模型在张量并行下的门控注意力问题。张量并行是支持大规模模型和长序列的关键技术，此修复确保了项目在扩展性（“for everyone”）上的稳定性。
*   **`[Bugfix] Qwen3-TTS: trim reference audio in no_async_chunk voice clone`**：修复了Qwen3-TTS在非异步分块模式下的语音克隆问题。这直接提升了多模态（语音）服务的质量和可靠性，符合项目“omni-modality”的定位。
*   **`Support DROID policy server for Cosmos3 OpenPI`**：增加了对Cosmos3 OpenPI的DROID策略服务器支持。这扩展了项目支持的模型生态，特别是针对世界模型或策略学习领域，体现了“omni-modality”的广度。

### 3. 对项目的影响和潜在意义

*   **性能提升**：HunyuanImage相关的两项优化（移除同步、分组步进批处理）将显著提升图像生成模型的推理速度和吞吐量，降低服务成本。
*   **稳定性增强**：对LTX-2.3和Qwen3-TTS的Bug修复，提升了多模态模型在复杂部署场景（如张量并行、特定推理模式）下的可靠性，增强了用户体验。
*   **生态扩展**：支持DROID策略服务器，使vllm-omni能够服务于更前沿的AI应用（如具身智能、世界模型），拓宽了项目的应用边界。
*   **开发效率**：CI流程的优化和重构工作，有助于保持代码库的健康度，降低开发者的维护成本，加速未来功能迭代。

### 4. 值得关注的技术点

*   **扩散模型推理优化**：`HunyuanImage3 DiT grouped step batching` 是一个值得深入的技术点。它可能涉及将扩散步长分组，并在单个批次内并行处理，以平衡计算负载和延迟，这是当前图像/视频生成模型服务化的前沿优化方向。
*   **张量并行下的注意力机制**：`Fix LTX-2.3 tensor-parallel gated attention` 的修复，揭示了在多GPU环境下实现复杂注意力（如门控注意力）的潜在挑战，对理解分布式推理的细节很有帮助。
*   **音频处理的边界情况**：`trim reference audio in no_async_chunk voice clone` 的修复，表明在处理流式或非流式音频克隆时，对参考音频的预处理（如裁剪）至关重要，这关系到语音克隆的质量和一致性。

### 5. 基于项目背景，这些提交如何影响项目发展

*   **强化核心优势**：针对HunyuanImage的性能优化，直接强化了vllm-omni在“快速”和“便宜”这两个核心卖点上的竞争力，使其在图像生成服务领域更具吸引力。
*   **巩固多模态能力**：对Qwen3-TTS和LTX-2.3的修复，确保了项目在语音和视频模态上的服务质量，巩固了其作为“omni-modality”服务框架的定位。
*   **拓展应用场景**：支持DROID策略服务器，标志着vllm-omni开始涉足更复杂的AI推理场景（如策略网络），这不仅是模型支持的扩展，更是项目从“模型服务”向“AI能力服务”演进的重要一步。
*   **提升开发者体验**：CI优化和代码重构，表明项目在追求功能丰富的同时，也注重内部工程质量和开发效率，这有助于吸引更多贡献者，形成健康的开源生态。

## 详细提交记录

### [c58a02c](https://github.com/vllm-project/vllm-omni/commit/c58a02c8736040d7eeddae480010e3686e122f66)

- **作者**: Chendi.Xue
- **时间**: 2026-06-15T21:31:04Z
- **提交信息**: [XPU][CI] Fix ERROR ...test_glm_image_sp.py - Failed: 'sp' not found in markers  (#4451)

Signed-off-by: Chendi Xue <chendi.xue@intel.com>

### [a86c333](https://github.com/vllm-project/vllm-omni/commit/a86c333c7ea17ad503d3105ce92e71a95eb9a018)

- **作者**: dengyunyang
- **时间**: 2026-06-15T21:28:51Z
- **提交信息**: [Perf][HunyuanImage] remove sync logic (#4401)

Signed-off-by: dengyunyang <584797741@qq.com>

### [aff0af9](https://github.com/vllm-project/vllm-omni/commit/aff0af97546f5350493304c9d7a4f112782d3e2d)

- **作者**: Hongsheng Liu
- **时间**: 2026-06-15T14:50:50Z
- **提交信息**: [Refactor] Extract diffusion output formatting boundary (#4407)

Signed-off-by: hsliuustc0106 <liuhongsheng4@huawei.com>

### [b1a4b08](https://github.com/vllm-project/vllm-omni/commit/b1a4b08a7ed4aef6eca5db5d5920d00d967c308e)

- **作者**: wangyu
- **时间**: 2026-06-15T14:21:13Z
- **提交信息**: [CI/Build] Skip L2/L3 CI for pytest skip-mark changes (#4422)

Signed-off-by: wangyu <410167048@qq.com>

### [e2e7917](https://github.com/vllm-project/vllm-omni/commit/e2e79177db29f55a5e6e94493b518f5fb5d28a69)

- **作者**: Yuzhu Dong
- **时间**: 2026-06-15T13:22:59Z
- **提交信息**: Support DROID policy server for Cosmos3 OpenPI (#4282)

Signed-off-by: yuzhud <yuzhudong@gmail.com>

### [ae93732](https://github.com/vllm-project/vllm-omni/commit/ae937320ff33f54535cfecf43be6c4a2e65c5cce)

- **作者**: TaffyOfficial
- **时间**: 2026-06-15T12:36:41Z
- **提交信息**: [Feature] Add HunyuanImage3 DiT grouped step batching (#4041)

Signed-off-by: TaffyOfficial <2324465096@qq.com>
Signed-off-by: zuiho <2324465096@qq.com>
Co-authored-by: TaffyOfficial <2324465096@qq.com>
Co-authored-by: Gao Han <hgaoaf@connect.ust.hk>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [11829cc](https://github.com/vllm-project/vllm-omni/commit/11829ccd75e67167254249d149d3ab01c86ff25a)

- **作者**: Mu GuanLin
- **时间**: 2026-06-15T11:40:06Z
- **提交信息**: [Bugfix] Fix LTX-2.3 tensor-parallel gated attention (#4439)

Signed-off-by: mglyn <1203789601@qq.com>

### [a693ae6](https://github.com/vllm-project/vllm-omni/commit/a693ae67f6eec6df1d443581857a9c016850a0a2)

- **作者**: Yueqian Lin
- **时间**: 2026-06-15T10:00:03Z
- **提交信息**: [Bugfix] Qwen3-TTS: trim reference audio in no_async_chunk voice clone (#4429)

Signed-off-by: Yueqian Lin <linyueqian@outlook.com>

### [3c62c53](https://github.com/vllm-project/vllm-omni/commit/3c62c53f5954babe58e2f7ae328827adf920b18c)

- **作者**: WeiQing Chen
- **时间**: 2026-06-15T07:52:22Z
- **提交信息**: Update WeChat QR code (#4431)

Signed-off-by: David Chen <530634352@qq.com>

---
