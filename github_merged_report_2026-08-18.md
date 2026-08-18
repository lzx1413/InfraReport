# GitHub Stars 合并报告 - 2026-08-18

**合并日期**: 2026-08-19
**监控日期**: 2026-08-18
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


**报告日期**: 2026-08-19
**监控日期**: 2026-08-18
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2158
- **最后更新**: 2026-08-18T13:08:51Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Wenzhe_Wang

## AI分析总结

### 1. 主要更新类型
- **Bug修复**：本次提交为数据模块的确定性修复，属于缺陷修正范畴。

### 2. 关键变更点及其与项目整体方向的关系
- **变更点**：修复了数据映射循环（mapping cycles）的非确定性行为，确保其生成过程可复现。
- **与项目方向的关系**：VeOmni 的核心目标是“以模型为中心的分布式训练配方库”，支持任意模态模型训练。数据映射是训练流水线中连接原始数据与模型输入的关键环节，其确定性直接影响训练结果的可复现性，与项目强调的“规模化”和“可靠性”目标高度一致。

### 3. 对项目的影响和潜在意义
- **提升可复现性**：确定性映射使相同配置下的训练实验可精确复现，这对学术研究和工业调优至关重要。
- **增强调试效率**：消除随机性后，开发者能更快速定位问题（如数据相关错误），减少因数据顺序波动导致的干扰。
- **支撑规模化扩展**：在分布式场景下，确定性映射有助于多节点间数据切分的一致性，避免因随机性引发的负载不均或结果偏差，为更大规模训练奠定基础。

### 4. 值得关注的技术点
- **确定性算法设计**：修复可能涉及固定随机种子、排序策略或哈希映射，确保跨进程、跨机器的一致行为。
- **循环结构处理**：映射循环可能指数据增强或预处理中的迭代过程，修复需保证循环次数和顺序的确定性，避免依赖系统时间或非稳定状态。
- **测试覆盖**：此类修复通常伴随回归测试，验证不同环境下的输出一致性，值得关注其测试用例设计。

### 5. 基于项目背景，这些提交如何影响项目发展
- **强化信任基础**：作为面向研究社区的开源项目，可复现性是建立用户信任的基石。此修复直接回应了“配方库”场景下用户对结果一致性的核心诉求，有助于吸引更多开发者采用。
- **推动规模化落地**：确定性映射是分布式训练中数据并行策略的前提，此修复为VeOmni在更大规模集群上的稳定运行扫清障碍，加速其“任意模态模型”训练能力的实际部署。
- **完善工程成熟度**：从“功能实现”转向“质量打磨”，表明项目正从原型阶段迈向生产级工具，为后续高级特性（如自动调优、故障恢复）奠定工程基础。

**总结**：本次提交虽小，但精准解决了训练流水线中的关键可靠性问题，与VeOmni“规模化、可复现、多模态”的定位紧密契合，是项目走向成熟的重要一步。

## 详细提交记录

### [c465a63](https://github.com/ByteDance-Seed/VeOmni/commit/c465a6302122d4326c3c94c0b80d5b8dd995bacc)

- **作者**: Wenzhe_Wang
- **时间**: 2026-08-18T08:11:18Z
- **提交信息**: [data] fix: make mapping cycles deterministic (#1045)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-08-19
**监控日期**: 2026-08-18
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2688
- **最后更新**: 2026-08-18T22:03:46Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Watebear, Xin Qiu

## AI分析总结

## 提交分析总结

### 1. 主要更新类型
- **功能新增**：为XPU平台新增RMSNorm算子后端
- **重构与扩展**：重构MoE（混合专家）模块，新增Ascend和Metax硬件后端，并引入权重绑定的融合MoE后端

### 2. 关键变更点与项目方向的关系
- **RMSNorm XPU后端**：为Intel XPU硬件提供RMSNorm支持，覆盖FP32/FP16/BF16精度，支持最大8192隐藏维度（需32整除）。用户可通过配置`"rms_norm_type": "intel_xpu"`按模型选择后端。这直接扩展了LightX2V在Intel硬件生态的适配能力。
- **MoE后端重构**：将权重绑定的融合MoE实现注册为可插拔后端，并新增Ascend（华为）和Metax（沐曦）两个国产加速器后端。这与项目“轻量级视频生成推理框架”的定位一致——通过多硬件适配降低推理成本、提升部署灵活性。

### 3. 对项目的影响与潜在意义
- **硬件覆盖扩大**：从原有GPU生态扩展至Intel XPU、华为Ascend、Metax等国产/专用加速器，显著提升框架在异构计算环境中的可用性，符合国产化替代趋势。
- **推理性能优化潜力**：权重绑定融合MoE可减少显存占用和通信开销，对视频生成这类大模型推理场景尤为关键；RMSNorm的硬件专用实现可提升归一化层计算效率。
- **生态友好性增强**：通过配置化后端选择，用户无需修改模型代码即可适配不同硬件，降低了部署门槛。

### 4. 值得关注的技术点
- **权重绑定融合MoE**：该技术将专家权重共享与算子融合结合，是MoE模型推理优化的前沿方向，可显著降低参数规模和内存带宽压力。
- **RMSNorm的XPU实现约束**：要求隐藏维度≤8192且可被32整除，反映了硬件对向量化对齐的依赖，也提示了未来需处理非对齐场景。
- **后端注册机制**：通过注册表模式管理多后端，体现了框架的模块化设计，便于持续集成新硬件。

### 5. 对项目发展的影响
LightX2V作为轻量级视频生成推理框架，其核心竞争力在于“轻量”与“多硬件适配”。本次提交：
- **强化了“轻量”属性**：通过融合算子与专用后端优化，在保持推理质量的同时降低资源消耗，契合视频生成模型对高吞吐、低延迟的诉求。
- **加速了“多硬件”战略**：覆盖Intel、华为、沐曦等主流国产/专用芯片，使框架能服务于更广泛的政企与边缘场景，增强项目在AI基础设施领域的竞争力。
- **奠定了后续扩展基础**：后端注册机制和配置化选择模式，为未来接入更多硬件（如寒武纪、燧原）和更多算子（如Attention、RoPE）提供了清晰架构范式。

总体而言，这两项提交是LightX2V在硬件适配和推理优化上的重要里程碑，既巩固了其技术领先性，也拓宽了商业与生态合作空间。

## 详细提交记录

### [b9cd165](https://github.com/ModelTC/LightX2V/commit/b9cd165ef6bb0554ff65edc872b3768f8bc613b0)

- **作者**: Watebear
- **时间**: 2026-08-18T08:28:40Z
- **提交信息**: refactor(moe/ascend/metax): add registered weight-bound fused MoE backends and add ascend,metax backends (#1383)

Co-authored-by: Super User <root@dev-metax-0.dev-metax.3b1febd2-0246-40a8-a771-04544a47aa0d.svc.cluster.local>

### [e4ac7ef](https://github.com/ModelTC/LightX2V/commit/e4ac7ef0122b79ea75b4af429a34f40456b741d4)

- **作者**: Xin Qiu
- **时间**: 2026-08-18T07:16:08Z
- **提交信息**: feat(xpu): add RMSNorm intel_xpu backend  (#1393)

## Summary

  - Implements RMSNorm for contiguous FP32, FP16, and BF16 XPU tensors.
  - Supports hidden sizes up to 8192 that are divisible by 32.
## Usage
  Select the backend with per model:
```
  {
    "rms_norm_type": "intel_xpu"
  }
```
or
```
  {
    "rms_norm_type": "intel_xpu"
  }
```

## Testing:
E2E test for Minimax H3

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-08-19
**监控日期**: 2026-08-18
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2198
- **最后更新**: 2026-08-17T14:04:01Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-08-19
**监控日期**: 2026-08-18
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 6187
- **最后更新**: 2026-08-18T20:59:23Z

## 提交统计

- **昨日提交总数**: 9
- **提交者数量**: 8
- **主要提交者**: EdalatiAli, Yunxiao Ning, Ziang Li

## AI分析总结

# FlashInfer 昨日提交综合分析

## 一、主要更新类型

昨日共9个提交，涵盖**功能新增**（3项）、**Bug修复**（3项）、**性能优化**（1项）、**重构**（1项）、**测试/打包修复**（1项）。

## 二、关键变更点

1. **MoE配置重构**（#4385）：将`do_finalize`从`ExecutionConfig`拆分为独立的`MoEFinalizeConfig`，新增`use_fused_finalize`字段，体现MoE架构关注点分离的设计理念。

2. **MegaMoE零拷贝输出**（#4341）：新增`return_workspace_view`参数，允许调用方直接使用工作区输出视图，减少大规模逐层输出物化开销，是对SGLang集成的直接优化。

3. **CUDA版本守卫修复**（#4377）：将共享内存相关枚举的守卫从CUDA 13.3提升至13.4，修复trtllm-gen JIT构建在CUDA 13.3上的编译失败。

4. **W4A16 SiTU性能优化**（#4540）：将FP32倒数预先计算并折叠，用乘法替代逐元素除法，是此前优化的延续。

5. **XQA支持head_dim 512**（#4570）：突破原有`head_dim > 256`限制，支持Gemma风格GQA解码，并修复V页推进的潜在bug，是对SM12x架构XQA默认后端的重大能力扩展。

6. **TopKSigmoid路由方法**（#4404）：新增`RoutingMethodType::TopKSigmoid`，先选TopK再应用sigmoid，解决饱和logits下的平局问题，无需内核改动即可生效。

7. **SM90内核越界读取修复**（#4525）：修复attention sinks数组在`headGrpSize % 8 != 0`时的越界全局读取，compute-sanitizer验证零错误。

8. **NIXL子模块版本恢复**：将`3rdparty/nixl`从v1.1.0恢复至v1.3.1，修复PR #3759无意中回退子模块指针导致的构建失败；同时将nixl-cu13 wheel安装约束从`>=1.3.1`改为`==1.3.1`并增加版本偏差警告，确保设备端内核与运行时库严格匹配。

9. **测试打包修复**（#4580）：修复SM90 push FP8 MoE测试在夜间包测试隔离环境中的源码路径依赖问题。

## 三、项目影响与意义

- **MoE推理栈持续演进**：配置拆分、零拷贝输出、TopKSigmoid和SiTU优化共同构建了更高效灵活的MoE推理路径，直接服务SGLang、vLLM等大规模部署场景。
- **硬件适配广度扩展**：head_dim 512支持和CUDA版本守卫修复扩大了支持的模型形态和工具链范围，特别是针对SM12x新硬件。
- **多GPU推理能力保障**：NIXL-EP修复确保大规模模型（如DeepSeek-V3/V4）多卡推理路径持续可用，版本锁定消除了“构建通过但运行时崩溃”的隐性风险。
- **正确性与稳定性提升**：越界读取修复和测试打包修复增强了代码健壮性和可维护性。

## 四、值得关注的技术点

- **JIT-only设计**（#4570）：head_dim > 256仅走JIT路径，不进AOT预构建，保护flashinfer-jit-cache二进制体积。
- **策略分发机制**（#4404）：通过`PolicyTraits`和`SigmoidPostprocess`策略组合实现新路由方法，展示架构扩展性。
- **零拷贝视图能力门控**（#4341）：通过`supports_output_view`能力属性表达后端支持，保持API向后兼容。
- **子模块指针漂移问题**：PR #3759仅修改代码却意外回退子模块指针，暴露Git子模块管理脆弱性，此提交通过显式恢复和版本锁定提供防御性措施。

## 五、项目发展方向

FlashInfer正沿**MoE推理优化**和**硬件适配广度**双线推进，同时强化工程严谨性。MoE相关变更共同构建更高效的推理栈，XQA扩展和CUDA兼容修复扩大服务范围，NIXL版本管理则传递“可依赖、可复现”的信号。整体上，项目朝着更广泛的模型支持、更高效的推理路径、更健壮的工程实践方向稳步发展，为后续新功能开发（如FP8量化AllReduce）奠定稳定基础。

## 详细提交记录

### [7aa0cd3](https://github.com/flashinfer-ai/flashinfer/commit/7aa0cd3b64f84c50c18ee958e24f708afb2103c1)

- **作者**: Alex Yang
- **时间**: 2026-08-18T20:57:34Z
- **提交信息**: refactor(moe): split finalize knobs out of ExecutionConfig into MoEFinalizeConfig (#4385)

## 📌 Description

Closes #4325.

`ExecutionConfig` mixed two unrelated concerns: runtime execution knobs
(`enable_pdl`, `tune_max_num_tokens`) and how the finalize/combine step
behaves. Finalize is an architectural concern in its own right — how
per-expert partials are reduced back into one row per token — so it gets
its own config, exactly as `RoutingConfig` is separated.

**Why now:** this is deliberately early. The unified MoE API is still
new and not yet widely adopted, so the config surface can still be
corrected cheaply. Doing the split now means it is *not* a breaking
change in practice — the in-tree call sites are updated in this PR and
there is nothing else to migrate. Left until adoption grows, the same
cleanup would be a genuine break with a deprecation cycle attached.

### New `MoEFinalizeConfig`

| field | notes |
|---|---|
| `do_finalize: bool = True` | moved off `ExecutionConfig` |
| `use_fused_finalize: Optional[bool] = None` | **newly reachable** from
the unified API; `None` → backend default |

`use_fused_finalize` already existed in the low-level `core.py` /
`cute_dsl` entry points but was not exposed through the unified config
surface at all — it was pinned to the `True` default. It is now plumbed
into `CuteDslNvfp4Runner`, the one backend that honors it; an explicit
value is only forwarded when set, so the backend default is preserved
otherwise.

`MoEConfig` gains a `finalize` field, **appended last** so existing
positional construction is unaffected.

## 🔁 Call-site change

`ExecutionConfig` no longer accepts `do_finalize`:

```python
# before
MoEConfig(..., execution=ExecutionConfig(do_finalize=False))
# after
MoEConfig(..., finalize=MoEFinalizeConfig(do_finalize=False))
```

Every in-tree caller is migrated here, so nothing downstream needs
touching today. No deprecation shim: the issue asks to *simplify*
`ExecutionConfig`, a forwarding field would defeat that, and there is no
adoption base that would need the bridge. Say the word and I will add
one.

## 🔍 Related Issues

- Closes #4325

## 🧪 Tests

- `eval(repr(cfg))` round-trip coverage added for `MoEFinalizeConfig`
(default + custom), matching the existing per-config pattern in
`tests/moe/test_unified_moe.py`.
- Updated the four unified-API call sites that passed `do_finalize`
(`test_unified_moe.py`, `test_unified_moe_b12x.py`,
`test_constraints.py`).
- All 10 `config.execution.do_finalize` consumers in `flashinfer/`
repointed to `config.finalize.do_finalize`, including the user-facing
MoE-EP error string.
- `pre-commit` (mypy / ruff check / ruff format) passes on all changed
files.

**Not run:** the MoE test suites themselves — authored on a machine
without a GPU or a torch install. Config semantics (repr round-trip,
defaults, hashability, `do_finalize` removal from `ExecutionConfig`)
were verified by exercising the dataclasses standalone. CI is the real
gate here.

## Reviewer Notes

- Low-level `do_finalize=` kernel arguments in
`trtllm_gen_fused_moe_utils.py`, the autotuner tests, etc. are untouched
— this only moves the *config-surface* knob.
- Doc table in `docs/design_docs/flashinfer_moe_api.md` updated to
match.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
  * Added a dedicated MoE finalization configuration.
  * Added controls for enabling finalization and fused finalization.
  * Exposed finalization settings through the public MoE API.
* Updated MoE execution paths to consistently apply finalization
preferences.

* **Documentation**
* Clarified the separation between execution and finalization controls
in the MoE API.

* **Tests**
* Expanded coverage for finalization configuration, output handling, and
validation scenarios.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [7015afd](https://github.com/flashinfer-ai/flashinfer/commit/7015afdc033ef58be3e254ee68d5b112187a63d0)

- **作者**: Yunxiao Ning
- **时间**: 2026-08-18T20:43:45Z
- **提交信息**: [MoE] Expose zero-copy MegaMoE workspace output view (#4341)

## Summary

This draft exposes a backward-compatible zero-copy output path for the
FlashInfer MegaMoE layer.

The new `return_workspace_view=False` argument preserves the existing
owned
output behavior by default. When enabled and supported by the selected
MegaMoE backend, `forward` returns the layer's workspace output view
instead
of copying the result into a new tensor. Capability gating keeps
unsupported
backends on the existing path. Backend support is expressed as the
`supports_output_view` capability property on the kernel contract.

The patch also keeps the workspace-view contract explicit across the
NVFP4 and
MXFP8 CuTeDSL MegaMoE backends and updates the relevant CUDA-graph and
multi-rank tests.

## Before and after

```text
Before (default behavior):

  MoEEpTensors
       |
       v
  MegaMoE forward(...)
       |
       v
  workspace output --copy--> caller-owned output tensor

After (opt-in view):

  MoEEpTensors
       |
       v
  MegaMoE forward(..., return_workspace_view=True)
       |
       v
  workspace output view ------> caller uses workspace-backed tensor
```

The default remains the copied, caller-owned output. The new path makes
the
workspace view available only when the backend advertises the
capability.

## Motivation

The SGLang MegaMoE integration currently needs the computed output to
remain
in the FlashInfer workspace. Returning that view removes a large
per-layer
output materialization while retaining the old API behavior for callers
that
need an owned tensor.

## Validation

- `tests/moe_ep/test_mega_cuda_graph.py`: 8 passed.
- The targeted output-view test passes: 1 passed, 7 deselected.
- Four-GPU NVFP4 multi-rank output-view coverage passes with
  `NVSHMEM_DISABLE_CUDA_VMM=1`.
- The corresponding SGLang adapter test passes 3 cases when paired with
this
  API.

The upstream `moe_ep_benchmark` harness was also run from the
`vllm_repro_8_gpu_v2` branch with the FlashInfer MegaMoE section on four
GPUs
(`GPUS=4`, `DEVS=0,1,2,3`). This is a GB200 smoke/regression run, not an
8-GPU reference result:

| backend | tokens/rank | hidden/intermediate | experts/top-k | p50
latency | throughput |
| --- | ---: | ---: | ---: | ---: | ---: |
| NVFP4 CuTeDSL | 32 | 7168 / 2048 | 256 / 8 | 358.4 us | 357174.7 |
| MXFP8 CuTeDSL | 32 | 7168 / 2048 | 256 / 8 | 619.9 us | 206472.9 |

The harness reported accuracy-loss fields of 23.201 percent for NVFP4
and
6.371 percent for MXFP8 against its BF16 dense reference. These are
retained
as harness output and are not used as a model accuracy claim here.

This is the FlashInfer side of the paired SGLang integration. The SGLang
draft depends on this API and is posted separately.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added an option to return workspace-backed output views, reducing
unnecessary output copying when supported.
* Added capability detection so unsupported configurations provide a
clear error while preserving existing default behavior.
  * Enabled output views for supported FP8 and FP4 workflows.

* **Tests**
* Added coverage for output-view shapes, workspace aliasing,
repeatability, zero-token inputs, and multi-size execution.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [92ef090](https://github.com/flashinfer-ai/flashinfer/commit/92ef090ed4f8c95688397e9ebdf46606d6118c30)

- **作者**: Jiaxuan Bai
- **时间**: 2026-08-18T20:40:52Z
- **提交信息**: fix: guard oversized shared memory driver enums with CUDA >= 13.4 (#4377)

https://github.com/flashinfer-ai/flashinfer/issues/4375

CU_FUNC_ATTRIBUTE_SHARED_MEMORY_MODE,
CU_SHARED_MEMORY_MODE_ALLOW_OVERSIZED_SHARED_MEMORY and
CU_DEVICE_ATTRIBUTE_MAX_OVERSIZED_SHARED_MEMORY_PER_BLOCK were
introduced in CUDA 13.4; CUDA 13.3 only ships the launch-attribute half
of the shared-memory-mode API (CU_LAUNCH_ATTRIBUTE_SHARED_MEMORY_MODE,
CUsharedMemoryMode values 0-2). The `#if CUDA_VERSION >= 13030` guards
added in #4122 / relanded in #4280 therefore break the trtllm-gen
fmha_gen JIT build on CUDA 13.3 (the current released toolkit) with
  fmhaKernels.cuh(136/157/169): error: identifier ... is undefined
on any GPU arch, e.g. via trtllm_batch_decode_with_kv_cache_mla on
SM100.

Bump the three guards to `#if CUDA_VERSION >= 13040`. No CUDA 13.3
fallback is needed: the 13.3 driver does not support the oversized mode,
so falling through to the existing MAX_DYNAMIC_SHARED_SIZE_BYTES path is
correct.

References:
- CUDA 13.3 Driver API (symbols absent):
https://docs.nvidia.com/cuda/archive/13.3.0/cuda-driver-api/group__CUDA__TYPES.html
- CUDA 13.4 developer preview Driver API (symbols present):
https://docs.nvidia.com/cuda/developer-preview/13.4/pdf/CUDA_Driver_API.pdf

Verified with CUDA 13.3 (nvcc V13.3.73) on SM100:
tests/attention/test_trtllm_gen_mla.py::test_trtllm_batch_decode_mla
(trtllm-gen backend) fails to build before, passes after.

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

* **Bug Fixes**
* Updated CUDA compatibility checks for oversized shared-memory support.
* Ensured related functionality is available only with CUDA 13.4 or
newer, improving compatibility with supported CUDA environments.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: Jimmy Zhou <79552142+jimmyzho@users.noreply.github.com>

### [7319c44](https://github.com/flashinfer-ai/flashinfer/commit/7319c448b7a62fb8deb3de2c878794194cb23558)

- **作者**: Ziang Li
- **时间**: 2026-08-18T20:37:43Z
- **提交信息**: perf(moe): fold W4A16 SiTU reciprocals (#4540)

<!-- .github/pull_request_template.md -->

## 📌 Description

@humansand

This is a focused follow-up to #4394 and #4506 for the CuTe DSL W4A16
SiTU path.

- Preserve `situ_beta` as a Python scalar so the existing shared
`situ_f32` helper folds its FP32 reciprocal while tracing.
- Precompute the optional up-branch reciprocal with `f32_reciprocal`,
then replace both per-element divisions with multiplies.
- Reuse the existing gate-only and gate-plus-up SiTU accuracy cases,
which already exercise both reciprocal paths changed here.
- Leave GeGLU, ordinary SwiGLU, ReLU2, GEMM2, routing, and finalize
behavior unchanged.

The reciprocal is derived from the FP32-rounded beta, matching the value
used by the kernel's multiply-back step. Reciprocal multiplication is
tolerance-equivalent to division, but is not guaranteed to be
bitwise-identical.

## 🔍 Related Issues

- #4394
- #4506

## ⏱️ Performance

### Environment and workload

- Image: `nvcr.io/nvidia/pytorch:26.05-py3` (`linux/amd64` digest
`sha256:ca73b4795f0d3ae27e9cd81b1b1f1b7fc6c0a129f7d51a359d2326e95af48a3d`)
- Devbox: `c1`, host `B200-147`, 8 x NVIDIA B200; measurements pinned to
GPU 0 at a 1000 W power limit
- Driver: `580.126.09`
- Python: `3.12.3`
- PyTorch: `2.12.0a0+5aff3928d8.nv26.05`
- PyTorch CUDA / system nvcc: `13.2` / `13.2` (`cuda_13.2.r13.2`,
compiler `37668154_0`)
- FlashInfer: `0.6.18`
- `nvidia-cutlass-dsl`: `4.7.0`
- `cupti-python`: `13.3.1`
- Baseline: `f4043ef18c92f38e0c70da76ca40b26d36318eed` (the #4394 merge
on `main`)
- Candidate kernel: `093fd3d7d24fa01afa16445cae230e477335f3fc`
- Workload: pre-routed W4A16 fused MoE, BF16 activations, NVFP4 weights,
`E=896`, `topK=16`, `H=3584`, `I=3072`, `situ_beta=4.0`,
`situ_linear_beta=25.0`

This is a Kimi-K3-shaped W4A16 derivative. It does not claim to use
Kimi-K3's native MXFP4 weight format.

### Method

- One fresh process per adjacent `A1 baseline -> B candidate -> A2
baseline` arm on the same GPU and node.
- A1 generated a single autotune cache; B and A2 loaded it cache-only.
The selected tactic was then passed explicitly to every timed call, and
exact A1/B/A2 tactic equality was validated for every shape.
- Full weight construction and quantization, compilation, and autotuning
were outside the timed region.
- CUDA-event timing used `use_cuda_graph=False`, `cold_l2_cache=True`,
10 warmups, 50 measured samples per repeat, and 3 repeats per arm.
- Every measured shape reported finite output.
- Derived baseline latency is the median of the six A1+A2 repeat
medians. Candidate latency is the median of the three B repeat medians.
`speedup = baseline / candidate`, so values above `1.0x` are faster.

Selected tactics for both GEMMs were identical across A1/B/A2:

| Tokens | Tactic per GEMM |
|---:|:---|
| 1, 8, 64, 512 | `((256, 16, 256), (2, 1), true)` |
| 2048 | `((256, 64, 256), (2, 1), true)` |
| 4096 | `((128, 128, 256), (2, 1), true)` |
| 8192 | `((256, 192, 256), (2, 1), true)` |

### Raw CUDA-event repeat medians

All values are milliseconds.

| Tokens | A1 r1 | A1 r2 | A1 r3 | B r1 | B r2 | B r3 | A2 r1 | A2 r2 |
A2 r3 |
|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 1 | 0.109600 | 0.109760 | 0.110400 | 0.107648 | 0.108432 | 0.108384 |
0.108448 | 0.108544 | 0.108560 |
| 8 | 0.611312 | 0.611328 | 0.611328 | 0.607264 | 0.607264 | 0.607232 |
0.610848 | 0.611360 | 0.610416 |
| 64 | 4.231168 | 4.325312 | 4.294672 | 4.063312 | 4.272128 | 4.251680 |
4.149184 | 4.296640 | 4.292672 |
| 512 | 4.392864 | 4.448288 | 4.446208 | 4.432448 | 4.429984 | 4.433216
| 4.437952 | 4.442624 | 4.438000 |
| 2048 | 5.702688 | 5.713840 | 5.715040 | 5.338224 | 5.483472 | 5.453744
| 5.466608 | 5.663840 | 5.660288 |
| 4096 | 7.799760 | 7.794224 | 7.797776 | 6.896560 | 7.029232 | 7.144368
| 7.370256 | 7.487568 | 7.549360 |
| 8192 | 11.601920 | 11.608000 | 11.610096 | 10.840064 | 10.907632 |
10.906624 | 11.527200 | 11.636208 | 11.628608 |

### Derived CUDA-event results

| Tokens | Baseline median (ms) | Candidate median (ms) | Speedup |
|---:|---:|---:|---:|
| 1 | 0.109080 | 0.108384 | 1.0064x |
| 8 | 0.611320 | 0.607264 | 1.0067x |
| 64 | 4.293672 | 4.251680 | 1.0099x |
| 512 | 4.440312 | 4.432448 | 1.0018x |
| 2048 | 5.683264 | 5.453744 | 1.0421x |
| 4096 | 7.671792 | 7.029232 | 1.0914x |
| 8192 | 11.609048 | 10.906624 | 1.0644x |

The 1-512-token changes are at or below 1% and are treated as noise. The
measurable result is `1.0421x-1.0914x` at 2048-8192 tokens. At 4096
tokens the two event-timed baseline arms drifted (`~7.798 ms` A1 versus
`~7.488 ms` A2), but the candidate stayed below both arms; the separate
CUPTI timing-backend spot-check below corroborates the direction.

### CUPTI 4096-token spot-check

This used the same fixed tactic and cold-L2 path in fresh A1/B/A2
processes, with 10 warmups and 50 samples per arm. CUPTI mode permits
one repeat per process.

| Arm | Revision | Median (ms) |
|:---|:---|---:|
| A1 baseline | `f4043ef18c92f38e0c70da76ca40b26d36318eed` | 7.234587 |
| B candidate | `093fd3d7d24fa01afa16445cae230e477335f3fc` | 6.889771 |
| A2 baseline | `f4043ef18c92f38e0c70da76ca40b26d36318eed` | 7.367835 |
| Bracketing baseline | median of A1 and A2 | 7.301211 |

The CUPTI spot-check shows a `1.0597x` speedup (`7.301211 / 6.889771`),
corresponding to 5.64% lower latency.

### Reproduction commands

The benchmark harness is retained locally and in branch commit
`ae6f92f5`, but is intentionally absent from the PR's final tree. The
run used the same script before a formatting-only `ruff format` pass. To
recover that equivalent harness from branch history, then verify that A1
starts without an existing tactic cache:

```bash
git show ae6f92f5:benchmarks/bench_w4a16_situ.py \
  > /hai-workspace/w4a16-situ-tools/bench_w4a16_situ.py
mkdir -p /hai-workspace/w4a16-situ-results
test ! -e /hai-workspace/w4a16-situ-results/tactics.json
```

The following are the exact CUDA-event arm commands:

```bash
cd /hai-workspace/flashinfer-baseline
CUDA_VISIBLE_DEVICES=0 FLASHINFER_DISABLE_VERSION_CHECK=1 \
FLASHINFER_WORKSPACE_BASE=/hai-workspace/cache-baseline \
PYTHONPATH=/hai-workspace/flashinfer-baseline \
python3 /hai-workspace/w4a16-situ-tools/bench_w4a16_situ.py \
  --arm A1-baseline \
  --revision f4043ef18c92f38e0c70da76ca40b26d36318eed \
  --tokens 1,8,64,512,2048,4096,8192 \
  --warmup 10 --iters 50 --repeats 3 --timing event \
  --autotune-cache /hai-workspace/w4a16-situ-results/tactics.json \
  --json-out /hai-workspace/w4a16-situ-results/A1-baseline.json

cd /hai-workspace/flashinfer-candidate
CUDA_VISIBLE_DEVICES=0 FLASHINFER_DISABLE_VERSION_CHECK=1 \
FLASHINFER_WORKSPACE_BASE=/hai-workspace/cache-tests-candidate \
PYTHONPATH=/hai-workspace/flashinfer-candidate \
python3 /hai-workspace/w4a16-situ-tools/bench_w4a16_situ.py \
  --arm B-candidate \
  --revision 093fd3d7d24fa01afa16445cae230e477335f3fc \
  --tokens 1,8,64,512,2048,4096,8192 \
  --warmup 10 --iters 50 --repeats 3 --timing event \
  --autotune-cache /hai-workspace/w4a16-situ-results/tactics.json \
  --json-out /hai-workspace/w4a16-situ-results/B-candidate.json

cd /hai-workspace/flashinfer-baseline
CUDA_VISIBLE_DEVICES=0 FLASHINFER_DISABLE_VERSION_CHECK=1 \
FLASHINFER_WORKSPACE_BASE=/hai-workspace/cache-baseline \
PYTHONPATH=/hai-workspace/flashinfer-baseline \
python3 /hai-workspace/w4a16-situ-tools/bench_w4a16_situ.py \
  --arm A2-baseline \
  --revision f4043ef18c92f38e0c70da76ca40b26d36318eed \
  --tokens 1,8,64,512,2048,4096,8192 \
  --warmup 10 --iters 50 --repeats 3 --timing event \
  --autotune-cache /hai-workspace/w4a16-situ-results/tactics.json \
  --json-out /hai-workspace/w4a16-situ-results/A2-baseline.json
```

The CUPTI commands changed only the arm/output labels and timing
arguments:

```bash
cd /hai-workspace/flashinfer-baseline
CUDA_VISIBLE_DEVICES=0 FLASHINFER_DISABLE_VERSION_CHECK=1 \
FLASHINFER_WORKSPACE_BASE=/hai-workspace/cache-baseline \
PYTHONPATH=/hai-workspace/flashinfer-baseline \
python3 /hai-workspace/w4a16-situ-tools/bench_w4a16_situ.py \
  --arm A1-cupti \
  --revision f4043ef18c92f38e0c70da76ca40b26d36318eed \
  --tokens 4096 --warmup 10 --iters 50 --repeats 1 --timing cupti \
  --autotune-cache /hai-workspace/w4a16-situ-results/tactics.json \
  --json-out /hai-workspace/w4a16-situ-results/cupti-4096/A1.json

cd /hai-workspace/flashinfer-candidate
CUDA_VISIBLE_DEVICES=0 FLASHINFER_DISABLE_VERSION_CHECK=1 \
FLASHINFER_WORKSPACE_BASE=/hai-workspace/cache-tests-candidate \
PYTHONPATH=/hai-workspace/flashinfer-candidate \
python3 /hai-workspace/w4a16-situ-tools/bench_w4a16_situ.py \
  --arm B-cupti \
  --revision 093fd3d7d24fa01afa16445cae230e477335f3fc \
  --tokens 4096 --warmup 10 --iters 50 --repeats 1 --timing cupti \
  --autotune-cache /hai-workspace/w4a16-situ-results/tactics.json \
  --json-out /hai-workspace/w4a16-situ-results/cupti-4096/B.json

cd /hai-workspace/flashinfer-baseline
CUDA_VISIBLE_DEVICES=0 FLASHINFER_DISABLE_VERSION_CHECK=1 \
FLASHINFER_WORKSPACE_BASE=/hai-workspace/cache-baseline \
PYTHONPATH=/hai-workspace/flashinfer-baseline \
python3 /hai-workspace/w4a16-situ-tools/bench_w4a16_situ.py \
  --arm A2-cupti \
  --revision f4043ef18c92f38e0c70da76ca40b26d36318eed \
  --tokens 4096 --warmup 10 --iters 50 --repeats 1 --timing cupti \
  --autotune-cache /hai-workspace/w4a16-situ-results/tactics.json \
  --json-out /hai-workspace/w4a16-situ-results/cupti-4096/A2.json
```

Raw JSON artifact checksums:

```text
4fd5c520996a529dde48f7a9f2ddef757efbb2f51f297dc68478ed89b0418268  A1-baseline.json
1447f556b1293e0a9472af9c066b7b9228a5a3bf2cfe3eea5e37e166e5e5d8d9  B-candidate.json
3be3b8066ffe2662f89ad274ff06aecab2e89c02e083c4f69a4aabc441bdccc8  A2-baseline.json
89c7416855d513228d8f4e93bf8d6d4cb87f72fa0e91674ee52213835e187e0e  tactics.json
1c8ca8e5f792a13b7bb1d6303ca089f6f2ffc7c322d5d3d580387b814a4c91ae  cupti-4096/A1.json
6baeda5a3294fb23ce73fb837d08dcee7356067bd1b21ec44faee19571187522  cupti-4096/B.json
039afa49d9db2787182d096b5a818541ce26fd11ba0d1ad079dce8411acae979  cupti-4096/A2.json
```

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
- [ ] All tests are passing (`unittest`, etc.).

Full-suite validation was not run. Targeted validation used PR head
`adcf4b123caaeda1fe589a722462c8beb75d7176` on one NVIDIA B300 SXM6 AC
(SM103, driver `590.48.01`) per process:

- CUDA 12.9: `flashinfer/flashinfer-ci-cu129:20260811-e673f7f`, Python
3.12.13, PyTorch 2.13.0+cu129, CuTe DSL 4.7.0
- CUDA 13.0: `flashinfer/flashinfer-ci-cu130:20260811-e673f7f`, Python
3.12.13, PyTorch 2.13.0+cu130, CuTe DSL 4.7.0

The same targeted commands were run in both images from
`/hai-workspace/flashinfer-pr4540`; `<stack>` was `cu129` or `cu130`:

```bash
CUDA_VISIBLE_DEVICES=0 FLASHINFER_DISABLE_VERSION_CHECK=1 \
FLASHINFER_WORKSPACE_BASE=/hai-workspace/cache-pr4540-<stack> \
python -m pytest -vv -s \
  tests/moe/test_cute_dsl_fused_moe.py::TestCuteDslFusedMoeFunctional::test_situ_accuracy \
  --tb=long

CUDA_VISIBLE_DEVICES=0 FLASHINFER_DISABLE_VERSION_CHECK=1 \
FLASHINFER_WORKSPACE_BASE=/hai-workspace/cache-pr4540-<stack> \
python -m pytest -vv -s \
  tests/moe/test_cute_dsl_fused_moe.py::TestCuteDslMoEWrapper::test_wrapper_with_autotune \
  -k "w4a16 and situ" --tb=long
```

```text
CUDA 12.9 functional SiTU matrix:
6 passed, 337 warnings in 648.05s (0:10:48)

CUDA 12.9 W4A16 SiTU wrapper/autotune:
1 passed, 7 deselected, 1219 warnings in 52.98s

CUDA 13.0 functional SiTU matrix:
6 passed, 337 warnings in 1020.78s (0:17:00)

CUDA 13.0 W4A16 SiTU wrapper/autotune:
1 passed, 7 deselected, 1219 warnings in 51.78s
```

No test-file change remains in the final diff. Existing coverage is
sufficient for both W4A16 paths changed here:

- `(1.75, None)` exercises the gate-only `situ_f32` path and its
trace-time reciprocal.
- `(0.8, 1.5)` exercises the gate path plus the optional up-branch
reciprocal and both multiplication sites.
- `test_wrapper_with_autotune[situ-w4a16]` covers wrapper propagation,
autotuning, and compiled execution.

The warnings were CuTe DSL deprecation warnings; none of these runs
reported a test failure.

Local source checks:

```bash
pre-commit run --all-files
pre-commit run --files \
  flashinfer/fused_moe/cute_dsl/blackwell/moe_w4a16_kernel.py \
  tests/moe/test_cute_dsl_fused_moe.py
python3 -m compileall -q \
  flashinfer/fused_moe/cute_dsl/blackwell/moe_w4a16_kernel.py \
  tests/moe/test_cute_dsl_fused_moe.py
git diff --check upstream/main...HEAD
```

```text
pre-commit run --all-files: all applicable hooks passed
Applicable hooks passed:
  check-added-large-files, check-case-conflict, check-merge-conflict,
  end-of-file-fixer, mixed-line-ending, trailing-whitespace, remove-tabs,
  remove-crlf, mypy, ruff-check, ruff-format
Skipped (no applicable files): check-symlinks, clang-format
compileall: exit 0
git diff --check: exit 0
```

## Reviewer Notes

Please focus on the trace-time scalar handling and the FP32 reciprocal
contract. This follows the same mechanism as #4506, but changes only the
W4A16 caller that #4394 introduced.

Limitations and untested scope:

- The performance workload is Kimi-K3-shaped W4A16 (BF16 activations and
NVFP4 weights), not Kimi-K3's native MXFP4 weight format.
- Measurements cover the pre-routed fused-MoE operator on one B200;
routing and end-to-end model performance are out of scope.
- Event-timing changes at or below 1% are treated as noise; no
small-shape speedup is claimed.
- Only the targeted SiTU accuracy and wrapper/autotune tests were run,
not the full repository test suite.
- By routing W4A16 through the shared `f32_reciprocal` helper, this
follow-up inherits its limitation for positive Python betas that round
to FP32 zero. No validation change is included here, and the production
`4.0` / `25.0` betas are unaffected.

### [fafab47](https://github.com/flashinfer-ai/flashinfer/commit/fafab47273e97208208833c94449c0cfbf91deb6)

- **作者**: Brian K. Ryu
- **时间**: 2026-08-18T20:04:56Z
- **提交信息**: feat(xqa): support non-MLA head_dim 512 (Gemma-style GQA decode) on SM12x (#4570)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

XQA currently rejects `head_dim > 256`, blocking Gemma-style GQA decode
(head_dim 512) — notably on SM120/121 where XQA is the default choice
for decode backend. Existing kernel path for head dim <= 256 should be
identical as before
  
Also included:
- Fix for a latent (previously unreachable) V page-advance bug when
`cacheVTileSeqStride % tokensPerPage != 0`: `exactDiv` yielded a zero
page step under NDEBUG. Required for fp16 KV at 512 on SM12x (16-token V
tiles with 32-token pages).
- `copyPartialHeadsAsync` generalized to head parts wider than one
warp-load (equivalent indexing for all existing configs).
- **JIT-only by design**: >256 stays out of the AOT prebuild to protect
flashinfer-jit-cache binary size.



### Performance
In general, 
* No regressions observed on head_dim=256.
* head_dim=512 performance is comparable to `fa2` backend

RTX PRO 6000 (SM120), decode q_len=1, 4 KV heads, group 4, page 32:
  
| Config | XQA (this PR) | FA2 tensor-core decode (only prior option) |
|---|---|---|
| fp16 KV, b64, seq 4096 | 1505 µs | 1417 µs |
| **fp8 KV, b64, seq 4096** | **741 µs** | n/a (FA2 has no fp8 KV at
512) |
| fp8 KV, b256, seq 1024 | 755 µs | n/a (fp16 FA2: 1411 µs) |


## 🔍 Related Issues

<!-- Link any related issues here -->

#4546

Note: smem was not really a blocker; it just needed a slight kernel
redesign.

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
  * Added support for attention head dimensions up to 512 elements.
  * Improved grouped value loading and processing for larger heads.
  * Enabled large-head batch decoding in supported configurations.

* **Bug Fixes**
* Improved handling of split heads, partial data, page transitions, and
output reduction.
* Updated kernel selection to use compatible execution paths for larger
dimensions.

* **Tests**
* Expanded batch-decoding coverage with multiple 512-element
head-dimension scenarios.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [efbd232](https://github.com/flashinfer-ai/flashinfer/commit/efbd2329402e34afeecf6079766b50c7d9122ac6)

- **作者**: EdalatiAli
- **时间**: 2026-08-18T19:02:48Z
- **提交信息**: feat(moe): add TopKSigmoid routing method (TopK -> Sigmoid) (#4404)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

Adds `RoutingMethodType::TopKSigmoid` (= 9): expert selection ranks the
raw routing logits, then sigmoid is applied to only the top-K survivors.
The existing `Sigmoid` (= 8) does the reverse — sigmoid, then TopK.
Sigmoid is monotonic, so the two orders agree on nearly all inputs. They
diverge once logits saturate: past roughly |17|, fp32 sigmoid returns
exactly 1.0 and ranking the squashed scores degenerates into a tie-break
by expert index, while TopKSigmoid still orders experts by raw
magnitude. No kernel changes are needed. It is a new
`SigmoidPostprocess` policy paired with the existing `NoOpPreprocess`,
plus a `PolicyTraits` tier entry for <=128 and <=256 experts, so all
existing routing kernels pick it up via the generic policy dispatch.
`Unspecified` moves from 9 to 10 so it remains the numerically largest
member.


## 🔍 Related Issues

<!-- Link any related issues here -->
None.

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

- `test_topk_sigmoid_selects_on_raw_logits`: saturating logits where the
two selection orders must disagree, swept across all six routing kernel
paths (static block, dyn block, cluster, block-per-token split,
block-per-token large batch, histogram scores) and both `enable_pdl`
settings.
- `test_topk_sigmoid_weights_are_unnormalized`: pins the weights to
`sigmoid(raw)` with no renormalization.
- `TopKSigmoid` configs added to `test_sigmoid_routing` (128 experts,
full backend matrix, `num_tokens` 8/768/3072) and
`test_routing_dtype_flexibility` (128 and 256 experts, bf16 and fp32
logits).
- Host reference `routing_reference_topk_sigmoid`, plus `TopKSigmoid` in
the `test_unified_moe_fuzz` routing-method pool.

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added Top-K Sigmoid routing, selecting experts by raw logits and
applying sigmoid weighting to selected experts.
* Added support across supported MoE execution paths and routing
configurations.
  * Added serialization and documentation for the new routing method.

* **Bug Fixes**
  * Extended routing validation to support Sigmoid-based methods.

* **Tests**
* Added coverage for Top-K Sigmoid behavior, kernel variants, data
types, fuzz testing, and compatibility scenarios.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [065795e](https://github.com/flashinfer-ai/flashinfer/commit/065795ea4179ee078c366092cfe8f86549971d72)

- **作者**: Brian K. Ryu
- **时间**: 2026-08-18T18:03:29Z
- **提交信息**: fix(xqa): out-of-bounds read of attention sinks in SM90 kernel epilogue (#4525)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->


Fixes an out-of-bounds global read reported by compute-sanitizer
initcheck on `tests/attention/test_xqa_batch_decode.py`, H100. (does not
impact other archs)

**Issue:** In `loadGmemColWiseVecWithDup` (`csrc/xqa/mha_sm90.cu`), the
bounds clamp is applied to a pair-group index but `bound` is an element
index (`headGrpSize - 1`), and the clamped index is then scaled by
`GmmaAccCoreMat::cols`. The attention-sinks array holds only
`headGrpSize` floats while `ShmQWiseVec` is padded to
`roundUp(headGrpSize, 8)`, so whenever `headGrpSize % 8 != 0` and sinks
are enabled, padding lanes read up to 12 bytes past the end of the sinks
tensor. Results are unaffected in practice (the stray values only feed
padding lanes that are masked at write-out), but the read targets
unrelated memory.
  
**Fix:** clamp per element — `gmemVec[mha::min(baseOffset + j, bound)]`
— so padding lanes duplicate the last valid element, matching the
multi-block combine path's existing convention.
  
**Compute-sanitizer results** (H100, `head_group_ratio=5`, fp8 KV, sinks
enabled; memcheck +
`PYTORCH_NO_CUDA_MEMORY_CACHING=1` reproduces the report
deterministically):
- Before: 64× `Invalid __global__ read of size 4 bytes` at
`kernel_mha+0x2d30` ("5 bytes after the nearest allocation of size 40
bytes" = the sinks tensor) — same kernel/offset as the original
initcheck record.
- After: `ERROR SUMMARY: 0 errors` (memcheck and initcheck). Affected
test subsets pass unchanged (`head_group_ratio` 5 and 6 configs).

**No performance regression:** the change is two branchless integer
clamps in the once-per-CTA epilogue, executed only when sinks are
enabled. A/B on the affected config (H100, batch 128, 4K KV): 77.1 µs
before vs 76.9 µs after — identical within noise.


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
* Fixed an issue where padded lanes could read beyond valid vector data
during certain operations.
* Improved handling of final duplicated elements when vector widths do
not align with the accumulator width.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [4581d63](https://github.com/flashinfer-ai/flashinfer/commit/4581d6385994bd300ff36ba8c0c15ce93281a149)

- **作者**: Cindy Zhang
- **时间**: 2026-08-18T14:45:01Z
- **提交信息**: Fix/missing source tree files for two more moe_ep test files (#4580)

<!-- .github/pull_request_template.md -->

Fix SM90 push FP8 MoE tests so they work in nightly package-test
isolation.

The contract tests previously assumed a full source checkout existed
next to tests/ and read private kernel sources via paths derived from
Path(__file__).parents[2]. Nightly package tests intentionally copy only
tests/ and pytest.ini into /tmp/flashinfer-nightly-tests.*, so those
source-tree paths do not exist there.

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

## 🔍 Related Issues

https://github.com/flashinfer-ai/flashinfer/issues/4515

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

- [ ] python -m pytest
tests/moe_ep/test_sm90_push_fp8_orchestrator.py::test_abort_cuda_contract_is_wired_through_waits_and_traps
- [ ] python -m pytest
tests/moe_ep/test_sm90_push_fp8_packaging.py::test_sm90_push_backend_imports_kernel_package_through_public_boundaries
- [ ] python -m pytest
tests/moe_ep/test_sm90_push_fp8_packaging.py::test_sm90_push_package_data_contains_cuda_sources
## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Tests**
* Improved test compatibility across source checkouts and packaged
installations.
* Added fallback handling for locating packaged source files when
checkout files are unavailable.
  * Added graceful skipping when project metadata is not present.
* Improved validation of backend imports and package contents across
installation environments.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [27a5a29](https://github.com/flashinfer-ai/flashinfer/commit/27a5a2945a2af3a4aaa0d1f659c6933d411bdfed)

- **作者**: Md Saidul Hoque Anik
- **时间**: 2026-08-18T07:16:21Z
- **提交信息**: fix(build): restore the nixl v1.3.1 submodule pin accidentally rolled back in #3759 (#4530)

## 📌 Description

PR #3759 (FP8 quantized two-shot AllReduce) unintentionally rolled the
`3rdparty/nixl` gitlink back from v1.3.1 (`b20f4d0a`, pinned by #4075)
to v1.1.0 (`05e4243f`) — that PR touches only `flashinfer/comm/`
quantized-allreduce code and never mentions nixl, so this looks like a
stale submodule pointer that slipped into the commit. cc @kailashbuki to
confirm.

Main's NIXL-EP build tooling has targeted v1.3.1 since #4075 (which set
this pin and refreshed the EP patches), while the gitlink now points at
v1.1.0 again, so every `BUILD_NIXL_EP=1` install is broken at TOT (both
verified against clean v1.1.0 / v1.3.1 checkouts):
- `3rdparty_patches/nixl/0002-ep-only-build.patch` no longer applies to
the v1.1.0 tree (`error: patch failed: meson_options.txt:49`).
- `build_backend.py` passes `-Dnixl_cuda_arch_list`, a meson option that
doesn't exist in v1.1.0 (added in NIXL v1.2.0, ai-dynamo/nixl#1639), so
`meson setup` would fail even if the patch applied.

## 🔧 Changes

- **`3rdparty/nixl`**: gitlink restored to v1.3.1 (`b20f4d0a`).
- **`build_backend.py`**: the nixl-cu13 wheel is now installed `==1.3.1`
via `_NIXL_WHEEL_VERSION` (bump together with the gitlink) instead of
`>=1.3.1`. A 1.4.x wheel over the v1.3.1 device kernels builds and
imports fine, then dies at the first dispatch with device asserts
(`nixlPut != NIXL_IN_PROG` → `cudaErrorIllegalAddress`); the hook now
also warns when an already-installed wheel skews from the pin.

## ✅ Validation

Pipecleaned on 8x B200 with this pin: `BUILD_NIXL_EP=1` build from a
clean checkout, NIXL-EP transport smoke + low-latency dispatch sweep
across DeepSeek-V3/V4, Kimi-K2, and Qwen3.5-397B shapes — all passing.
Patch applicability re-verified against pristine v1.1.0 and v1.3.1
trees.

## 🧪 Test coverage

No new tests; this restores the pin the existing NIXL-EP path (merged in
#4075) was built and tested against. Existing multi-GPU EP tests cover
the transport.

AI-assisted (Claude Code).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Standardized NIXL installation and wheel handling on the exact version
1.3.1.
* Added clearer warnings and corrective installation guidance when a
different NIXL version is detected.
* Updated missing-wheel and runtime installation messages to reference
`nixl-cu13==1.3.1`.
* Updated the bundled NIXL integration to align with the supported
release and improve compatibility.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-08-19
**监控日期**: 2026-08-18
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3949
- **最后更新**: 2026-08-18T22:08:08Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Aryan Kumar

## AI分析总结

### 提交分析总结

**1. 主要更新类型**  
功能新增：为 Apple Silicon 设备引入 MLX 运行时，支持 INT8 量化的 Wan2.1 和 Wan2.2 模型推理。

**2. 关键变更点与项目方向**  
- 新增 MLX 后端，使 FastVideo 能在 Apple Silicon（如 M 系列芯片）上原生运行视频生成模型，无需依赖 CUDA/GPU。  
- 支持 INT8 量化，降低显存和内存占用，提升推理效率。  
- 与项目“快速、高效视频生成”的核心目标一致，扩展了硬件兼容性，覆盖 Mac 用户群体。

**3. 对项目的影响和潜在意义**  
- 显著扩大用户基础：此前依赖 NVIDIA GPU，现可覆盖 Apple 生态开发者与研究者。  
- 降低入门门槛：Mac 用户无需高性能 GPU 即可体验 Wan2.1/2.2 推理，利于社区推广和反馈收集。  
- 为后续多后端支持（如 AMD、Intel）奠定架构基础，增强项目可移植性。

**4. 值得关注的技术点**  
- MLX 是 Apple 专为统一内存架构设计的机器学习框架，其优化策略（如内存带宽利用）与 CUDA 不同，需针对性调优。  
- INT8 量化在保证生成质量的同时，需处理精度损失问题，可能涉及混合精度或量化感知训练。  
- 代码中可能包含条件编译或运行时检测逻辑，以自动选择 MLX 或 CUDA 后端，体现模块化设计。

**5. 对项目发展的影响**  
- 结合 README 中“快速上手”和“文档”导向，此提交直接响应了跨平台需求，使 FastVideo 从单一 GPU 工具转向多平台通用框架。  
- 有助于吸引 Apple 生态贡献者，促进社区多样性，并可能推动后续对更多模型（如 Wan2.2 变体）的适配。  
- 为未来边缘设备部署（如 MacBook 本地推理）铺路，符合生成式 AI 轻量化趋势。  

**总结**：该提交是 FastVideo 迈向跨平台的重要一步，通过 MLX 支持填补了 Apple Silicon 空白，兼具技术前瞻性和生态扩展价值。

## 详细提交记录

### [8537dcd](https://github.com/hao-ai-lab/FastVideo/commit/8537dcd6ded64052327c4c8e2d7acdfa903c845e)

- **作者**: Aryan Kumar
- **时间**: 2026-08-18T22:08:00Z
- **提交信息**: [feat]: Apple Silicon MLX runtime — INT8 Wan2.1 and Wan2.2 inference (#1638)

Co-authored-by: Aryan Kumar <aryan5v@users.noreply.github.com>

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-08-19
**监控日期**: 2026-08-18
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34340
- **最后更新**: 2026-08-18T22:10:43Z

## 提交统计

- **昨日提交总数**: 8
- **提交者数量**: 5
- **主要提交者**: Sayak Paul, YiYi Xu, apolinário

## AI分析总结

# 提交分析总结

## 1. 主要更新类型

本次提交涵盖**性能优化**（Krea 2注意力机制改进）、**Bug修复**（DiffusionGemma批处理停止、量化加载问题）、**测试重构**（量化测试与SD Pipeline测试）、**功能新增**（MiniMax-H3 LoRA支持）、**文档更新**（Kandinsky文档修正）及**项目状态调整**（Modular Diffusers去实验化）。

## 2. 关键变更点与项目方向

- **Krea 2注意力优化**：用`repeat_interleave`替代`enable_gqa`，解决掩码与头数不匹配导致的性能回退，使模型兼容更多后端（cuDNN、flash、FA3等），与项目“多后端支持”目标一致。
- **量化测试重构**：修复torchao和bitsandbytes的序列化问题，将测试迁移至mixin体系，实现“一次编写、全模型运行”，强化了项目对量化方案的系统性验证。
- **Modular Diffusers转正**：移除实验警告，标志该架构进入稳定阶段，是项目模块化战略的重要里程碑。

## 3. 项目影响与潜在意义

Krea 2优化将单次注意力调用内存从9.02GiB降至0.16GiB（速度提升6.5倍），显著降低高分辨率生成门槛。量化测试重构提升了多模型覆盖率和可靠性，为生产环境部署提供保障。Modular Diffusers去实验化增强了用户信心，推动生态采用。

## 4. 值得关注的技术点

- **Krea 2的权衡**：`repeat_interleave`与`enable_gqa`在计算等价但后端兼容性不同，文档提供了选择指引。
- **torchao根级张量处理**：过滤无模块前缀的扁平化张量，避免反序列化崩溃。
- **bnb跨分片SCB延迟合并**：解决8-bit权重与统计信息分片分离的加载问题。
- **DiffusionGemma批处理停止**：修复多批次自适应停止逻辑，提升推理效率。

## 5. 对项目发展的影响

这些提交体现了diffusers“**性能优先、测试完备、架构稳定**”的发展路径。性能优化持续降低硬件门槛，测试重构保障多方案（bnb、torchao、gguf）的可靠性，Modular Diffusers转正则标志着项目从快速迭代转向生态成熟期。整体上，项目正朝着更高效、更稳定、更易扩展的方向演进，为社区贡献者提供了更清晰的技术基座。

## 详细提交记录

### [11a82a1](https://github.com/huggingface/diffusers/commit/11a82a15fe473ed974ff35111dd629b05fb1b3ed)

- **作者**: YiYi Xu
- **时间**: 2026-08-18T20:15:09Z
- **提交信息**: replace enable_gpa with repeat_interleave for krea2 (#14523)

* Krea 2: repeat key/value heads instead of `enable_gqa`

Krea 2 always attends with a text padding mask, and no fused SDPA kernel takes
a mask together with mismatched query/key head counts — flash rejects the mask,
the memory-efficient kernel rejects the mismatch. Attention therefore fell back
to the math backend, which materializes the full
[batch_size, num_heads, seq_len, seq_len] score matrix with no error or warning.

Repeating the key/value heads in the processor computes the same thing and keeps
the memory-efficient kernel eligible: at 1024x1024 (48/12 heads, 4608 tokens) one
attention call goes from 9.02 GiB / 26.7 ms to 0.16 GiB / 4.1 ms.

It also unpins the model from the native backend, since cuDNN, flash, FA3, sage
and the hub kernels all raise on `enable_gqa`.

Fixes #14518

Co-Authored-By: Claude Opus 5 <noreply@anthropic.com>

* docs: how to choose between `enable_gqa` and repeating key/value heads

Co-Authored-By: Claude Opus 5 <noreply@anthropic.com>

* docs: recommend a choice rather than just reporting one

Co-Authored-By: Claude Opus 5 <noreply@anthropic.com>

* docs: add enable_gqa reference model, reword performance note

Co-Authored-By: Claude Fable 5 <noreply@anthropic.com>

---------

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [425b113](https://github.com/huggingface/diffusers/commit/425b113c211c42ec26ff646cbdbaa7d83adb46b5)

- **作者**: Sayak Paul
- **时间**: 2026-08-18T18:53:32Z
- **提交信息**: [tests] refactor pipeline-level quantization tests (#14435)

* fix(torchao): route root-level tensors around safetensors reconstruction

Models with parameters at the root of the module tree (e.g. Wan's
`scale_shift_table`) crashed torchao's `unflatten_tensor_state_dict`
when loading serialized checkpoints, since flattened tensor names are
assumed to carry a module prefix. Filter such tensors and their
metadata entries out of the reconstruction and merge them back
unchanged.

Co-Authored-By: Claude Fable 5 <noreply@anthropic.com>

* fix(bnb): defer 8-bit weights split from their SCB stats across shards

Sharded serialization can place an 8-bit weight and its `SCB`
statistics in different shard files, in which case the shard-by-shard
loader failed with "Missing quantization component `SCB`". Hold the
incomplete half of the pair back until its counterpart arrives with a
later shard, mirroring the torchao pending mechanism, and disable
parallel shard loading for prequantized 8-bit checkpoints.

Co-Authored-By: Claude Fable 5 <noreply@anthropic.com>

* [tests] extend model-level quantization tester mixins

Migrate remaining model-level coverage from tests/quantization into the
tester mixins so it runs for every wired model:

- base: buffer-placement assertions in the device-map test, and an
  opt-in sharded-serialization test enabled by setting
  `sharded_serialization_config`
- bnb: serialization across all configs (sharded included), dtype
  assignment and adapter training for 8-bit, device moves preserving
  the memory footprint, corrupted-state-dict loading error, and a fixed
  modules-to-not-convert test (BitsAndBytesConfig only exposes
  llm_int8_skip_modules; the old test passed an unsupported kwarg and
  only survived by being skipped)
- torchao: custom device maps with cpu/disk offload, generalized from
  the Flux-specific test
- gguf: the diffusers-format single-file loading path, wired into the
  Flux model tests

Co-Authored-By: Claude Fable 5 <noreply@anthropic.com>

* [tests] fix model-level quantization test wiring

- SD3.5: the quantized testers reused the random-init dummy inputs
  (4 latent channels, fp32) while the tiny Hub checkpoint has
  in_channels=8 and the quantizers load the model in half precision;
  give them matching inputs and relax the 4-bit memory expectation for
  the tiny checkpoint.
- QwenImage / Flux2: the quantized testers had no Hub checkpoint wired
  at all, so every test errored; point them at
  hf-internal-testing/tiny-qwenimage-pipe and tiny-flux2 with matching
  inputs.
- NucleusMoE: no tiny checkpoint exists on the Hub yet; comment the
  testers out like the LTX ones.

Co-Authored-By: Claude Fable 5 <noreply@anthropic.com>

* [tests] split tests/quantization into pipeline-level and backend-level tiers

Pipeline-level quantization tests (pipeline quality slices, cpu offload,
LoRA loading, compile, PipelineQuantizationConfig) move to
tests/pipelines/testing_utils/quantization.py, marked per backend so the
nightly CI can select them with `pytest -m`. tests/quantization keeps
only backend-level tests that fit neither tier: config validation,
utility warnings, and GGUF CUDA kernel correctness. Tests already
covered by the model-level mixins are dropped.

Co-Authored-By: Claude Fable 5 <noreply@anthropic.com>

* [ci] select nightly quantization tests by marker across test tiers

Each backend job now runs `pytest -m <marker>` over tests/models,
tests/quantization, and tests/pipelines/testing_utils/quantization.py,
giving the model-level mixin tests a nightly home with the backend
dependencies installed. The torchao job additionally installs mslk.

Co-Authored-By: Claude Fable 5 <noreply@anthropic.com>

---------

Co-authored-by: sayak@huggingface.co <sayak@ip-10-53-90-45.ec2.internal>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [a14d630](https://github.com/huggingface/diffusers/commit/a14d630211853ab5a5a8fec65d590f067e096170)

- **作者**: Sayak Paul
- **时间**: 2026-08-18T17:58:22Z
- **提交信息**: [tests] refactor stable diffusion pipeline tests (#14339)

* refactor stable diffusion pipeline tests

* consolidate on nightly

* define sets explicitly.

* up

### [a0b3a07](https://github.com/huggingface/diffusers/commit/a0b3a073d632a0e2157537304350c8639c358632)

- **作者**: apolinário
- **时间**: 2026-08-18T17:13:25Z
- **提交信息**: Support DiffSynth-Studio MiniMax-H3 LoRAs (#14484)

* Support DiffSynth-Studio MiniMax-H3 LoRAs

* Note the DiffSynth fp32 factors in the LoRA docstring

### [59c4744](https://github.com/huggingface/diffusers/commit/59c47446f2f9e9e8e45f23d2e2dde2bb475d97b7)

- **作者**: iridescentWen
- **时间**: 2026-08-18T15:55:22Z
- **提交信息**: docs: fix typos in Kandinsky 5.0 video docs (#14345)

- `qualty` -> `quality`
- `infered` -> `inferred` (x3)
- `bakend` -> `backend` (x3, in the trailing `# <--- Set attention
  bakend to Flex` comments; the actual `set_attention_backend` calls
  were already spelled correctly)
- `wothout` -> `without`

Prose and comments only, no code or behavior changes.

### [d6bfaa7](https://github.com/huggingface/diffusers/commit/d6bfaa71b858f32bdc54ab9868e0385c093f1122)

- **作者**: Kashif Rasul
- **时间**: 2026-08-18T09:12:21Z
- **提交信息**: Fix batched DiffusionGemma adaptive stopping (#14386)

* Fix DiffusionGemma stopping

* Test batched stopping

* Style DiffusionGemma docs

* Address DiffusionGemma review

* Update DiffusionGemma review

---------

Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

### [356c2fc](https://github.com/huggingface/diffusers/commit/356c2fc7e5efd40e314ac4a7036b512e47bb6690)

- **作者**: Sayak Paul
- **时间**: 2026-08-18T08:06:23Z
- **提交信息**: [tests] skip parallelism tests for some models. (#14505)

* skip parallelism tests for some models.

* clarify comment

* skip others too.

### [a00d536](https://github.com/huggingface/diffusers/commit/a00d536450c6cb83824366f4b4d22426cba9165c)

- **作者**: YiYi Xu
- **时间**: 2026-08-18T07:28:43Z
- **提交信息**: Drop the experimental warning from Modular Diffusers (#14525)

Modular Diffusers is no longer experimental: remove the import-time warning
and the docstring warnings from ModularPipeline, the block base classes, and
every model's modular pipeline, and drop it from the docs overview.

ComponentsManager and the Mellon integration are still moving, so they keep
a warning — added one to the ComponentsManager docs page and to
mellon_node_utils, which had none.

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-08-19
**监控日期**: 2026-08-18
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 431
- **最后更新**: 2026-08-11T01:47:46Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-08-19
**监控日期**: 2026-08-18
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12962
- **最后更新**: 2026-08-18T15:01:25Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Yuze-e20

## AI分析总结

### 1. 主要更新类型
**功能新增**：本次提交为 DiffSynth-Studio 引入了对 FLUX.1 系列模型（FLUX Fill、FLUX Redux、Insert Anything）的推理支持，属于新模型能力扩展。

### 2. 关键变更点及与项目整体方向的关系
- **新增三种 FLUX 模型推理**：支持 FLUX Fill（图像填充/修复）、FLUX Redux（图像变体生成）和 Insert Anything（任意内容插入）任务。
- **代码整合与优化**：在原始 PR（由 huan-yin 等作者贡献）基础上进行了进一步改进，提升了代码质量和功能完整性。
- **与项目方向的关系**：DiffSynth-Studio 定位为多模态内容生成与编辑工具，FLUX 系列模型是当前业界领先的图像生成/编辑模型，本次更新直接扩展了项目在图像编辑与生成领域的覆盖范围，符合项目“多模型集成、一站式创作”的核心理念。

### 3. 对项目的影响和潜在意义
- **增强模型生态**：使项目支持更多主流生成模型，提升对用户多样化需求的响应能力。
- **提升竞争力**：FLUX 系列在图像编辑（如局部重绘、内容插入）方面表现优异，可吸引更多专业用户和创作者。
- **为后续扩展铺路**：新增的推理框架可复用于未来其他 FLUX 变体或类似架构模型，降低后续集成成本。

### 4. 值得关注的技术点
- **多任务统一推理**：在一个框架内同时支持 Fill、Redux、Insert 三类任务，可能涉及条件输入（如掩码、参考图）的灵活处理。
- **代码协作与优化**：提交中明确提到“进一步改进原始 PR”，说明团队重视代码质量与可维护性，可能涉及性能优化、接口统一或错误处理增强。
- **模型兼容性设计**：需确保不同 FLUX 变体的输入输出格式与现有 DiffSynth 管线无缝衔接，体现架构的扩展性设计。

### 5. 基于项目背景的总结
DiffSynth-Studio 作为一款面向创意工作者的多模态生成工具，持续集成最新模型是其保持活力的关键。本次 FLUX.1 系列支持直接响应了图像编辑领域的热门需求（如局部修改、内容插入），显著提升了项目的实用性和吸引力。从发展角度看，这不仅是功能堆叠，更强化了项目作为“统一生成平台”的定位，有望吸引更多社区贡献者参与模型适配，形成良性生态循环。未来若结合项目已有的视频、音频能力，FLUX 的加入可能催生跨模态创作新场景，进一步巩固其在生成式 AI 工具链中的地位。

## 详细提交记录

### [0361581](https://github.com/modelscope/DiffSynth-Studio/commit/03615819a6209a198c7e4020988a18ba64e05fb0)

- **作者**: Yuze-e20
- **时间**: 2026-08-18T07:05:36Z
- **提交信息**: Support FLUX.1 Fill Redux InsertAnything (#1611)

* support the inference of FLUX Fill, FLUX Redux, Insert Anything

* feat/fix: further improve the origin pr authored by huan-yin

---------

Co-authored-by: Li Xiangyue <2792578061@qq.com>
Co-authored-by: Li Xiangyue <113219380+huan-yin@users.noreply.github.com>
Co-authored-by: yjy415 <2471352175@qq.com>

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-08-19
**监控日期**: 2026-08-18
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 32057
- **最后更新**: 2026-08-18T22:07:41Z

## 提交统计

- **昨日提交总数**: 31
- **提交者数量**: 26
- **主要提交者**: Khoa Pham, WenhaoZhang, Xiaoyu Zhang

## AI分析总结

# SGLang 昨日提交分析报告

## 一、主要更新类型

本次共31个提交，涵盖**性能优化**（约40%）、**Bug修复**（约25%）、**功能新增**（约20%）、**重构与CI改进**（约15%）。无纯文档更新。

## 二、关键变更点与项目方向

**1. 投机解码与KV缓存优化（核心方向）**
- 多个提交围绕EAGLE/DFLASH的页对齐解码分配、SWA evict floor断言、DSv4 draft-extend SWA写位置提升，以及MHC post-pre fusion默认开启。这些直接服务于SGLang高性能推理引擎的核心目标——通过投机解码和KV缓存管理降低推理延迟。

**2. MoE路由与量化支持（硬件适配）**
- Laguna配置驱动MoE路由评分、AMD平台block-fp8 QKV融合、NPU平台mxfp4-w4a4量化支持，以及NVFP4 Marlin测试扩展至SM120。体现项目在多硬件（AMD/NPU/消费级GPU）上的广泛适配战略。

**3. 调度器与负载管理**
- 限制prefill-delayer队列目标、按缓存命中率折扣排队prefill负载、PD解码端延迟KV释放。这些优化提升系统在高并发下的吞吐稳定性。

**4. Diffusion模型支持扩展**
- 解耦编码器并行与DiT并行布局、INT8 Linear+可插拔注意力后端、支持Cosmos3 RL、算子按域重组。显示项目正从纯LLM推理向多模态生成扩展。

**5. 推理质量与工具链**
- 修复Kimi-K3工具调用丢失问题、保留输出logprobs、Rust服务器延迟元数据、详细执行步骤注解。提升生产环境的可观测性和输出质量。

## 三、项目影响与潜在意义

- **性能层面**：页对齐和缓存优化可显著降低PD分离场景下的显存碎片和延迟，对长序列推理尤为关键。
- **生态层面**：多硬件量化支持和Diffusion扩展将吸引更广泛的用户群体，巩固SGLang作为通用推理框架的定位。
- **稳定性层面**：CI fast-fail跳过和NPU测试目录重组，提升开发迭代效率，降低回归风险。

## 四、值得关注的技术点

1. **页对齐DFLASH解码KV预留**：解决投机解码中KV缓存分配不对齐导致的性能损耗。
2. **NIXL混合缓存键分组修复**：涉及混合缓存一致性，对多级缓存架构的正确性至关重要。
3. **自定义all-reduce v2拓扑选择**：根据拓扑能力自动选择通信算法，优化多节点扩展。
4. **DSv4 draft-extend SWA写位置提升**：减少跨设备内存访问，提升投机解码吞吐。

## 五、对项目发展的影响

结合README中SGLang定位为**高性能、高吞吐的LLM推理框架**，这些提交呈现三条清晰路径：**一是持续深挖投机解码和KV缓存管理以保持性能领先**；**二是通过多硬件（AMD/NPU/消费级GPU）和多模态（Diffusion）支持扩大适用场景**；**三是通过调度器优化和可观测性增强提升生产环境可靠性**。特别是DeepSeek-V4相关优化和MHC fusion默认开启，表明项目正积极适配最新模型架构，维持技术前沿地位。整体而言，本次提交体现了SGLang在性能、兼容性和工程成熟度上的均衡推进。

## 详细提交记录

### [b814a7e](https://github.com/sgl-project/sglang/commit/b814a7e812fb9367d994af307085bd30de329f96)

- **作者**: Baizhou Zhang
- **时间**: 2026-08-18T22:07:33Z
- **提交信息**: [CI] Skip fast-fail for scheduled stages (#35392)

### [87a0949](https://github.com/sgl-project/sglang/commit/87a09494fa3fbd685bd7c88d6a2dbdd3135de602)

- **作者**: Liangsheng Yin
- **时间**: 2026-08-18T21:39:41Z
- **提交信息**: [Refactor] Share the page-aligned decode alloc lens between EAGLE and DFLASH (#35382)

### [7b5410c](https://github.com/sgl-project/sglang/commit/7b5410c999be60489c71636443ea036596fe1432)

- **作者**: Joe Rowell
- **时间**: 2026-08-18T20:42:36Z
- **提交信息**: Laguna: config-driven MoE router scoring (#35362)

### [79dfef3](https://github.com/sgl-project/sglang/commit/79dfef390bf38334df9801eb45376a4cd0401510)

- **作者**: Liangsheng Yin
- **时间**: 2026-08-18T20:36:04Z
- **提交信息**: [Spec] Page-align the DFLASH decode KV reservation (#35265)

### [aa82229](https://github.com/sgl-project/sglang/commit/aa8222917343b0a2bb702b23cb2651057b0a4191)

- **作者**: Liangsheng Yin
- **时间**: 2026-08-18T20:32:16Z
- **提交信息**: [Fix] Assert the page-aligned SWA evict floor at PD decode prealloc (#35286)

### [9557045](https://github.com/sgl-project/sglang/commit/955704544c60e920672aa434cefa2ce78c0ceb4c)

- **作者**: Yuwei An
- **时间**: 2026-08-18T20:07:19Z
- **提交信息**: [Fix] Skip padded state slots in the chunked GDN kernel (#33431)

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [307a90f](https://github.com/sgl-project/sglang/commit/307a90f6d3c73ad4cbf3d90e817bc23617580475)

- **作者**: Khoa Pham
- **时间**: 2026-08-18T19:42:56Z
- **提交信息**: Stop losing Kimi-K3 tool calls to reasoning, constraint conflicts, and truncation (#34881)

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: Xinyuan Tong <xinyuantong.cs@gmail.com>
Co-authored-by: Xinyuan Tong <115166877+JustinTong0323@users.noreply.github.com>

### [8bb106c](https://github.com/sgl-project/sglang/commit/8bb106cee94c1ccb5625cdb78ef0ee3e0cad3918)

- **作者**: Wei Yang
- **时间**: 2026-08-18T18:55:51Z
- **提交信息**: Fix NIXL cleaner grouping for hybrid cache keys (#35130)

Co-authored-by: Wei Yang <yawei@microsoft.com>

### [526af15](https://github.com/sgl-project/sglang/commit/526af158452c7b9323a14b7fa5016aeb51b49efd)

- **作者**: Hanming Lu
- **时间**: 2026-08-18T18:27:21Z
- **提交信息**: [Metrics] Discount queued prefill load by recent cache hits when waiting-queue matching is off (#35248)

### [7dcaf11](https://github.com/sgl-project/sglang/commit/7dcaf119875eaa2e14e479c039c367c69959f21b)

- **作者**: Xingyu Liu
- **时间**: 2026-08-18T17:30:10Z
- **提交信息**: [Fix] Select custom all-reduce v2 by topology capability (#35061)

Co-authored-by: xingyuliu <xingyuliu@fb.com>

### [480033d](https://github.com/sgl-project/sglang/commit/480033def052471e0f31f84ec1623fae061fe80a)

- **作者**: Ke Bao
- **时间**: 2026-08-18T17:20:17Z
- **提交信息**: Refactor kv cache event mixin into a recorder (#35164)

### [83d7d45](https://github.com/sgl-project/sglang/commit/83d7d453306977dd3aad4402c921c8a6b66d9a9d)

- **作者**: jain-ria
- **时间**: 2026-08-18T17:07:13Z
- **提交信息**: fix: preserve output logprobs without input logprobs (#34627)

Signed-off-by: jain-ria <riajain@NVIDIA.com>

### [3f26feb](https://github.com/sgl-project/sglang/commit/3f26febaff04bac4cfefd60bdc9097bc26a96cb8)

- **作者**: Mick
- **时间**: 2026-08-18T16:16:09Z
- **提交信息**: [diffusion] fix: decouple encoder parallelism from the dit parallel layout (#34713)

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [9485c08](https://github.com/sgl-project/sglang/commit/9485c083bbc8d48636a84fc41441a12bdaa93573)

- **作者**: LinyuanLi
- **时间**: 2026-08-18T16:06:05Z
- **提交信息**: [NPU] Add mxfp4-w4a4 MOE Quantization Support for NPU (#30319)

### [97dedd1](https://github.com/sgl-project/sglang/commit/97dedd1ce9b161c476e0a91106857f210b5bfa41)

- **作者**: Shangming Cai
- **时间**: 2026-08-18T15:56:33Z
- **提交信息**: [PD] Deferred decode-side KV release for aborts mid-transfer (#35049)

Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [c60952d](https://github.com/sgl-project/sglang/commit/c60952d9330091b0db5b11b2cdbc00fd3063a935)

- **作者**: hhhh1252023
- **时间**: 2026-08-18T15:48:48Z
- **提交信息**: Exclude multimodal-gen NPU jobs from fast-fail cascade (#35238)

### [499e90a](https://github.com/sgl-project/sglang/commit/499e90a12569a16a422ca937a2f5218467516ff6)

- **作者**: pllimax
- **时间**: 2026-08-18T15:46:00Z
- **提交信息**: [NPU CI] Reorganize test output/log directory structure with workflow context (#33685)

### [63d783b](https://github.com/sgl-project/sglang/commit/63d783bbe0955237ec41f9ddabf7235ddf04673c)

- **作者**: WenhaoZhang
- **时间**: 2026-08-18T13:44:39Z
- **提交信息**: [diffusion] optimization: INT8 Linear + pluggable DiT attention backends for MiniMax-H3 on consumer-level GPUs (#34581)

### [0065fbf](https://github.com/sgl-project/sglang/commit/0065fbfae1d22626203c158b9e8c0e8f7126c4cd)

- **作者**: paulzhang-tm
- **时间**: 2026-08-18T13:40:13Z
- **提交信息**: [Scheduler] Cap prefill-delayer queue target by admission capacity (#35191)

### [94eef83](https://github.com/sgl-project/sglang/commit/94eef833fe40460230cd6856e2602e038c8305e0)

- **作者**: Andy Ye
- **时间**: 2026-08-18T12:42:27Z
- **提交信息**: [diffusion] rl: support cosmos3 (#34197)

### [ae6945e](https://github.com/sgl-project/sglang/commit/ae6945e112334bd3599400f933fa0cad60f60515)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-08-18T12:37:43Z
- **提交信息**: [kernels] Reorganize ops/diffusion by operator domain behind a lazy facade (#35114)

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [7605529](https://github.com/sgl-project/sglang/commit/7605529bdf98ded2815e48c7054b1bc4533256c9)

- **作者**: HeYao
- **时间**: 2026-08-18T11:41:25Z
- **提交信息**: Add deepseek_v4_flash_w8a8_8p_in32k_out1k_50ms (#35162)

Co-authored-by: HeYao <heyao@example.com>

### [f7101b0](https://github.com/sgl-project/sglang/commit/f7101b0ae626d6d8700f8f5fa444e9cbe69351ad)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-08-18T10:01:01Z
- **提交信息**: [AMD] MiniMax-M3 : Fuse QKV+index proj for block-fp8 (#32099)

### [24d6256](https://github.com/sgl-project/sglang/commit/24d625698d44c78f6e8ab8b7c19f96f45bbaa90a)

- **作者**: karverma-amd
- **时间**: 2026-08-18T09:32:57Z
- **提交信息**: [AMD] feat(moe): fold padded-topk_ids fill into fused shared-experts append+remap (#31370)

### [70ee6b1](https://github.com/sgl-project/sglang/commit/70ee6b1714dbed9079630d24e1ea531ec2fa9315)

- **作者**: Lianmin Zheng
- **时间**: 2026-08-18T09:08:07Z
- **提交信息**: [Rust Server] Add e2e latency metadata and fix Sarashina import (#35125)

### [880ab72](https://github.com/sgl-project/sglang/commit/880ab72f34ead8f39544c7c7e08edbd443964a1f)

- **作者**: vijay-kodamalla
- **时间**: 2026-08-18T08:24:00Z
- **提交信息**: test: extend NVFP4 Marlin tests to SM120 (#34327)

### [fc0b95e](https://github.com/sgl-project/sglang/commit/fc0b95e7badd94198925722445b93f063905a71c)

- **作者**: mohbasit
- **时间**: 2026-08-18T08:09:07Z
- **提交信息**: Profiling Enhancements [2/3]: detailed execution step annotations (#24911)

### [667389c](https://github.com/sgl-project/sglang/commit/667389c50f2a2bb62af55df4b3585bb0642f3aff)

- **作者**: Emil Bogomolov
- **时间**: 2026-08-18T08:05:05Z
- **提交信息**: [diffusion] chore: filter transformer safetensors by index.json to drop duplicate shard variants (#35107)

Co-authored-by: Emil Bogomolov <zetyquickly@googlemail.com>

### [0111b29](https://github.com/sgl-project/sglang/commit/0111b290312aa224962397db86c04fe112539fb2)

- **作者**: Liangsheng Yin
- **时间**: 2026-08-18T07:13:28Z
- **提交信息**: [Perf] Hoist DSv4 draft-extend SWA write locs; unify SWA graph buffer naming (#34890)

### [a779a2a](https://github.com/sgl-project/sglang/commit/a779a2a2a54a9fa728836e12796254c1589baa21)

- **作者**: Lianmin Zheng
- **时间**: 2026-08-18T07:11:12Z
- **提交信息**: [Chore] Move version tag helper to release scripts (#35196)

### [5b60b7c](https://github.com/sgl-project/sglang/commit/5b60b7c6511fc8e26ce4bfd20daa92de6a894c17)

- **作者**: Baizhou Zhang
- **时间**: 2026-08-18T07:03:37Z
- **提交信息**: [DSV4] Turn on mhc post pre fusion by default (#35214)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-08-19
**监控日期**: 2026-08-18
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1250
- **最后更新**: 2026-08-17T12:17:39Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-08-19
**监控日期**: 2026-08-18
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 89375
- **最后更新**: 2026-08-18T22:16:39Z

## 提交统计

- **昨日提交总数**: 29
- **提交者数量**: 28
- **主要提交者**: Alexander Lee, Taneem Ibrahim, Jikui Xie

## AI分析总结

## 提交分析总结

### 1. 主要更新类型
本批次提交涵盖**Bug修复**（约10项）、**性能优化**（约6项）、**CI/测试改进**（约5项）、**功能增强**（约4项）及**代码重构**（约3项），整体以稳定性和效率提升为核心。

### 2. 关键变更点与项目方向
- **ROCm/AMD支持强化**：多个提交针对AMD GPU（MI325X等）优化，包括启用fused KDA decode、修复int4/int8量化错误、门控Torch FP8 scaled-MM架构支持，并新增AMD CI拉取请求命令，体现对多硬件生态的持续投入。
- **DeepSeek模型专项优化**：为DSV3.2添加PCP支持、加固fused kernel grids，并修复GLM-5.2的MLA注意力问题，显示对前沿模型架构的快速适配能力。
- **Rust前端与数据并行改进**：简化数据并行大小所有权、等待所有工具调用完成、添加路由专家提示偏移，提升分布式推理的健壮性和可扩展性。
- **量化与MoE标准化**：移除死代码分支、抽象fused shared expert优化选择，推动量化路径的统一和可维护性。

### 3. 项目影响与潜在意义
- **稳定性提升**：修复结构化输出中XGrammar token批次终止、数据并行唤醒假设、PaliGemma图像嵌入缩放等关键Bug，降低生产环境风险。
- **性能优化**：注意力测试加速、非对齐AITER MLA头填充、fused kernel网格加固等，直接提升推理吞吐和延迟表现。
- **生态扩展**：Flashinfer升级至0.6.17、huggingface-hub升级至1.28.0，保持与上游依赖同步，支持新硬件特性。

### 4. 值得关注的技术点
- **MLA注意力优化**：针对GLM-5.2禁用Dense MHA，避免错误路径，体现对新型注意力机制的精细调优。
- **量化后端标准化**：用linear_backend/moe_backend替代强制FP8 Marlin测试变量，简化配置并增强灵活性。
- **多模态视频解码器重组**：重构视频解码后端，为未来多模态模型扩展奠定基础。
- **错误码规范化**：/detokenize接口对客户端错误返回4xx，改善API语义一致性。

### 5. 对项目发展的影响
vLLM定位为“人人可用的快速、便宜LLM服务”，本批次提交通过**强化AMD ROCm支持**扩大硬件覆盖，通过**DeepSeek等前沿模型优化**保持技术领先，通过**Rust前端和分布式改进**提升大规模部署可靠性，通过**CI标准化**保障代码质量。整体上，项目正从“功能齐全”向“多硬件高效稳定”演进，同时保持对最新模型架构的快速响应能力，巩固其作为高性能LLM推理引擎的行业地位。

## 详细提交记录

### [203926c](https://github.com/vllm-project/vllm/commit/203926c4778698f11904beec88f6a91b94b7122d)

- **作者**: Andreas Karatzas
- **时间**: 2026-08-18T22:16:25Z
- **提交信息**: [ROCm][CI] Add AMD CI Pull-Request Commands (#52822)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [5f7a20b](https://github.com/vllm-project/vllm/commit/5f7a20b3162ef88d531ada03aa1174643bb97c11)

- **作者**: Summer Yang
- **时间**: 2026-08-18T21:59:08Z
- **提交信息**: [nv] add pcp support in dsv3.2 (#52046)

Signed-off-by: Summer Yang <girasoleyang@gmail.com>

### [d3fafe0](https://github.com/vllm-project/vllm/commit/d3fafe0c27f9666a06675858738aaeab949da0f5)

- **作者**: xuebwang-amd
- **时间**: 2026-08-18T21:42:45Z
- **提交信息**: [Quantization] Remove the dead ocp_mx_scheme branch from moe_kernel_quantize_input (#52603)

Signed-off-by: xuebwang-amd <xuebwang@amd.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [6066bb3](https://github.com/vllm-project/vllm/commit/6066bb3d502107d27383a64b306d36148421d4b9)

- **作者**: stefankoncarevic
- **时间**: 2026-08-18T21:40:30Z
- **提交信息**: [ROCM][CI] Attention test speedup (#52763)

Signed-off-by: Stefan Koncarevic <stefan.koncarevic@amd.com>

### [5d8a4cf](https://github.com/vllm-project/vllm/commit/5d8a4cf9761ec890ae9f11502fe0f4a13e9981a5)

- **作者**: yinfengLiu
- **时间**: 2026-08-18T21:37:10Z
- **提交信息**: [ROCm] Pad non-aligned AITER MLA heads (#51647)

Signed-off-by: Liuyinfeng01 <yinfeliu@amd.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [12f64b3](https://github.com/vllm-project/vllm/commit/12f64b39d29282437e35be9aa5db432fb2a1a6e6)

- **作者**: Flora Feng
- **时间**: 2026-08-18T21:21:43Z
- **提交信息**: [Bugfix][Structured Output] Stop XGrammar token batches at termination (#52805)

Signed-off-by: sfeng33 <4florafeng@gmail.com>

### [7ddb507](https://github.com/vllm-project/vllm/commit/7ddb50788ddf0846518feff972028534e39bcb86)

- **作者**: aoshen02
- **时间**: 2026-08-18T20:49:35Z
- **提交信息**: [Bugfix][DP] Don't assume the engines started when forwarding a wake (#51481)

Signed-off-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [6a391a9](https://github.com/vllm-project/vllm/commit/6a391a931a92250aa45aa711aaa3f099f5a8d05f)

- **作者**: Biswa Panda
- **时间**: 2026-08-18T20:04:28Z
- **提交信息**: [Rust Frontend][RL] add routed expert prompt offset (#52703)

Signed-off-by: Biswa Panda <biswa.panda@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [8d6b183](https://github.com/vllm-project/vllm/commit/8d6b18329a303c3d4a8f1a7b515cd69a4ef64800)

- **作者**: Kevin H. Luu
- **时间**: 2026-08-18T19:50:32Z
- **提交信息**: [CI] Standardize test job labels by device (#52659)

Signed-off-by: Kevin Luu <51931015+khluu@users.noreply.github.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [9842d70](https://github.com/vllm-project/vllm/commit/9842d701450214d4b78cd9aefb8eee0c616bce33)

- **作者**: Sage Moore
- **时间**: 2026-08-18T19:00:04Z
- **提交信息**: [DBO][CI] Increase the coverage of prefill DBO in test_dbo.py (#48628)

Signed-off-by: Sage Moore <sage@neuralmagic.com>

### [6948a43](https://github.com/vllm-project/vllm/commit/6948a43fbbf427e69ca0d325cd7ab1daee8d131b)

- **作者**: Michał Ganczarenko
- **时间**: 2026-08-18T18:43:51Z
- **提交信息**: [Bugfix] Detect all attention-spelling variants in ModelConfig.is_hybrid (#52161)

Signed-off-by: Michal Ganczarenko <michal.ganczarenko@intel.com>
Signed-off-by: Michał Ganczarenko <michal.ganczarenko@intel.com>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>

### [90984dd](https://github.com/vllm-project/vllm/commit/90984ddbed27a09409506d6d6c0eea87f54b04b5)

- **作者**: Andreas Karatzas
- **时间**: 2026-08-18T18:35:44Z
- **提交信息**: [CI] Upgrade huggingface-hub to 1.28.0 (#52797)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [d75136c](https://github.com/vllm-project/vllm/commit/d75136c030cc62973dc470d1981199be8de47d62)

- **作者**: Connor Carpenter
- **时间**: 2026-08-18T18:23:34Z
- **提交信息**: [Rust Frontend] Wait for all utility calls to finish (#52671)

Signed-off-by: Connor Carpenter <connorc@nvidia.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>

### [01e56ca](https://github.com/vllm-project/vllm/commit/01e56caaf2b2d6f62be5fd78e0a7733fc9c9ed5f)

- **作者**: Woosuk Kwon
- **时间**: 2026-08-18T18:20:48Z
- **提交信息**: [Bugfix][MLA] Do not use Dense MHA for GLM-5.2 (#52512)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [ad5e71b](https://github.com/vllm-project/vllm/commit/ad5e71b276f6a8d9642560205736bee800464937)

- **作者**: Matvei Pashkovskii
- **时间**: 2026-08-18T18:01:00Z
- **提交信息**: [ROCm][Perf] Enable fused KDA decode on gfx942 (MI325X) (#52293)

Signed-off-by: Matvei Pashkovskii <mpashkov@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [ddbf826](https://github.com/vllm-project/vllm/commit/ddbf826bee965ace7d2a68599fb45a69e79745d2)

- **作者**: Strahinja Stamenkovic
- **时间**: 2026-08-18T17:54:51Z
- **提交信息**: [ROCm] Gate Torch FP8 scaled-MM on architecture support (#51021)

Signed-off-by: sstamenk <strahinja.stamenkovic@amd.com>
Signed-off-by: Strahinja Stamenkovic <strahinja.stamenkovic@amd.com>
Signed-off-by: Strahinja Stamenkovic <sstamenk@amd.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [bca7bea](https://github.com/vllm-project/vllm/commit/bca7bea2405127bd5291bb6fffa679bdcd8f6dd9)

- **作者**: Misha Goin
- **时间**: 2026-08-18T16:58:04Z
- **提交信息**: Remove VLLM_TEST_FORCE_FP8_MARLIN to replace with linear_backend/moe_backend (#52182)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [88b2bff](https://github.com/vllm-project/vllm/commit/88b2bff2c63d0f28396451f1199d09ee0f3e2d88)

- **作者**: fxmarty-amd
- **时间**: 2026-08-18T16:56:56Z
- **提交信息**: [MOE] Standardize and abstract fused shared expert optimization selection (#51695)

Signed-off-by: Felix Marty <Felix.Marty@amd.com>

### [f9f066d](https://github.com/vllm-project/vllm/commit/f9f066d195ca079c7403d9d9447c6b1d740c348c)

- **作者**: Jikui Xie
- **时间**: 2026-08-18T16:00:55Z
- **提交信息**: [Bugfix][PaliGemma] Remove stale image embedding scaling (#52692)

Signed-off-by: jikuixie <jikuixie@gmail.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [241ff8c](https://github.com/vllm-project/vllm/commit/241ff8c443175ae3e5e2b42b866e4c9275bd7744)

- **作者**: karthik
- **时间**: 2026-08-18T15:53:49Z
- **提交信息**: [Model] Enable LoRA support for tower and connector in LlavaNextForConditionalGeneration (#49788)

Signed-off-by: gangula-karthik <gkarthik923@gmail.com>

### [3bb9c18](https://github.com/vllm-project/vllm/commit/3bb9c18f0c845170679498f6aa39c6a92f2f68cb)

- **作者**: Isotr0py
- **时间**: 2026-08-18T15:06:18Z
- **提交信息**: [Multimodal] Reorganize video decoder backends (#49155)

Signed-off-by: Isotr0py <Isotr0py@outlook.com>

### [689be2b](https://github.com/vllm-project/vllm/commit/689be2bcd37a3a862d1330c2aa91727406e64085)

- **作者**: Wei Zhao
- **时间**: 2026-08-18T15:04:36Z
- **提交信息**: Upgrade Flashinfer version to 0.6.17 (#52681)

Signed-off-by: wzhao18 <wzhao18.sz@gmail.com>

### [d29dc3a](https://github.com/vllm-project/vllm/commit/d29dc3ab87840aef42129b30825176295ea73b07)

- **作者**: Alexander Lee
- **时间**: 2026-08-18T12:41:26Z
- **提交信息**: [Bugfix][Gemma4] Align parser enable_thinking default with template (#52430)

Signed-off-by: lxy-alexander <lxy_alexander@outlook.com>
Co-authored-by: Chauncey <chaunceyjiang@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [be3f614](https://github.com/vllm-project/vllm/commit/be3f614ff158ccecc99546958bf5e4893f8e0581)

- **作者**: Taneem Ibrahim
- **时间**: 2026-08-18T12:28:00Z
- **提交信息**: [CI] Register CPU CI "VLLM_CPU_CI_ENV" environment variable (#52633)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [41f179b](https://github.com/vllm-project/vllm/commit/41f179b57aa8ab6f634f508128ce1f1efadd0eb1)

- **作者**: Bugen Zhao
- **时间**: 2026-08-18T09:06:05Z
- **提交信息**: [Rust Frontend] Simplify data-parallel size ownership (#52575)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>

### [eab1cff](https://github.com/vllm-project/vllm/commit/eab1cff5b0ca87ec415c3ca555f060933d0a6b72)

- **作者**: yimdev
- **时间**: 2026-08-18T08:43:12Z
- **提交信息**: Harden DeepSeek V3.2 fused kernel grids (#52381)

Signed-off-by: yimdev <5779256+yimdev@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [e8ad285](https://github.com/vllm-project/vllm/commit/e8ad2855e7f5d40665250eb468bfd567e3a4b3c1)

- **作者**: qli88
- **时间**: 2026-08-18T08:31:51Z
- **提交信息**: [Bugfix][ROCm] Fix a few int4/int8 quantization errors (#52112)

Signed-off-by: Qiang Li <qiang.li2@amd.com>

### [5c9ff53](https://github.com/vllm-project/vllm/commit/5c9ff5366b039a69b344773bdfead8466ed9a097)

- **作者**: Yufeng He
- **时间**: 2026-08-18T08:22:13Z
- **提交信息**: [Bugfix] Accept logprobs=-1 in the Completion API (#46175)

Signed-off-by: Yufeng He <40085740+he-yufeng@users.noreply.github.com>

### [b01728b](https://github.com/vllm-project/vllm/commit/b01728b0880ca419bb41199523535457f4ab0010)

- **作者**: Rajath Pai
- **时间**: 2026-08-18T07:07:15Z
- **提交信息**: [Bugfix] Return 4xx for client-caused errors in /detokenize (#52622)

Signed-off-by: rajathpi <rajathpai2000@gmail.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-08-19
**监控日期**: 2026-08-18
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 6155
- **最后更新**: 2026-08-18T22:22:17Z

## 提交统计

- **昨日提交总数**: 10
- **提交者数量**: 9
- **主要提交者**: Alex Brooks, Weiming Liao, Wang  fuyin

## AI分析总结

## 提交分析总结

### 1. 主要更新类型

本批次提交以 **Bug修复** 为主（6项），同时包含 **核心功能增强**（2项）、**配置重构**（1项）和 **测试优化**（1项），无纯文档更新。

### 2. 关键变更点与项目方向的关系

- **多模态推理能力扩展**：新增DLO AllGather在线FP8支持，提升大规模多模态模型分布式推理效率；为Diffusion模型引入原生KV缓存初始化和Scheduler管理的块分配机制，强化图像生成场景的内存管理。
- **硬件适配与稳定性**：修复NPU上Wan2.2-S2V的RoPE实现、XPU上SDXL文本编码器设备分配、ROCm循环导入问题，体现项目对多硬件平台（NPU/XPU/ROCm）的持续适配承诺。
- **配置系统统一**：复用vLLM标准配置于VllmOmniConfig，减少重复定义，推动配置体系向vLLM生态对齐。
- **测试可靠性**：修复Qwen3-omni OOM问题并移除不稳定的voxcpm2测试用例，提升CI稳定性。

### 3. 对项目的影响与潜在意义

- **性能与可扩展性**：FP8+DLO AllGather和Diffusion KV缓存优化直接提升推理吞吐与显存效率，支撑更大规模部署。
- **生态兼容性**：配置复用和硬件修复降低了用户从vLLM迁移的门槛，扩大潜在用户群。
- **开发效率**：修复pi0运行时导入和ROCm循环依赖，减少维护负担，加速后续迭代。

### 4. 值得关注的技术点

- **DLO AllGather与FP8结合**：分布式通信与低精度量化协同，是高性能推理的关键路径。
- **Scheduler管理的块分配**：将KV缓存管理从模型内部解耦至调度器，是架构层面的重要演进。
- **复杂索引替换为index_select**：在NPU上避免complex64高级索引的性能陷阱，体现硬件感知的代码优化思路。

### 5. 对项目发展的影响

vllm-omni定位为“人人可用的多模态模型服务”，本批次提交通过**修复多硬件Bug**、**增强推理性能**和**统一配置体系**，直接支撑其“易用、快速、低成本”的核心目标。特别是Diffusion和TTS相关修复，巩固了其在语音和图像生成领域的覆盖能力；而配置复用和测试清理则提升了项目的工程成熟度，为吸引更广泛社区贡献奠定基础。整体上，这些变更推动项目向**生产级多模态推理引擎**稳步迈进。

## 详细提交记录

### [07ceb33](https://github.com/vllm-project/vllm-omni/commit/07ceb3324a52061d6fb0cd4293b573783d287896)

- **作者**: Doug Smith
- **时间**: 2026-08-18T22:22:11Z
- **提交信息**: [BugFix][TTS] Move user input from INFO to DEBUG in TTS/audio log lines (#6329)

### [b4b907e](https://github.com/vllm-project/vllm-omni/commit/b4b907e7b60086c6428145f8dbab687314971dea)

- **作者**: Alex Brooks
- **时间**: 2026-08-18T16:43:05Z
- **提交信息**: [Bugfix | Model] Fix SenseNova & Use Well-defined Model Configs (#5877)

Signed-off-by: Alex Brooks <albrooks@redhat.com>

### [f208f90](https://github.com/vllm-project/vllm-omni/commit/f208f907bc351dbb863e353ab5d996707bd4c339)

- **作者**: Weiming Liao
- **时间**: 2026-08-18T16:06:29Z
- **提交信息**: [BugFix][NPU] Wan2.2-S2V RoPE: replace complex64 advanced indexing with index_select (#6320)

Signed-off-by: Weiming Liao <liaowm5@gmail.com>

### [284e05c](https://github.com/vllm-project/vllm-omni/commit/284e05c88b7b46be9fae6d822bf22075840cbfbb)

- **作者**: Hongsheng Liu
- **时间**: 2026-08-18T15:48:07Z
- **提交信息**: [Core] Support online FP8 with DLO AllGather (#6279)

Signed-off-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [c3de04e](https://github.com/vllm-project/vllm-omni/commit/c3de04e12777708cfb994958c614fc8708cf5225)

- **作者**: Hongsheng Liu
- **时间**: 2026-08-18T15:42:03Z
- **提交信息**: [Bugfix] Avoid eager pi0 runtime import in pipeline registry (#6322)

Signed-off-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [4cd6678](https://github.com/vllm-project/vllm-omni/commit/4cd667875f983819414ca6a19cf612b58e6c138e)

- **作者**: Joshna-Medisetty
- **时间**: 2026-08-18T14:03:31Z
- **提交信息**: [XPU][SDXL] Fix text encoder input device under CPU offload (#6125)

Signed-off-by: Joshna Medisetty <joshna.medisetty@intel.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Nick Cao <ncao@redhat.com>

### [e1c5f59](https://github.com/vllm-project/vllm-omni/commit/e1c5f59aab091b5aed864808d118903ceb77d6ac)

- **作者**: Wang  fuyin
- **时间**: 2026-08-18T13:27:58Z
- **提交信息**: [Config] Reuse vLLM configs in VllmOmniConfig (#6050)

Signed-off-by: Acerak01-fy <wfy2003324@163.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [02069a5](https://github.com/vllm-project/vllm-omni/commit/02069a5bbf95b4f88de1c1e1e9c0da7564e697ad)

- **作者**: TJian
- **时间**: 2026-08-18T09:45:05Z
- **提交信息**: [ROCm] [CI] Fix circular import for rocm due to patch (#6287)

Signed-off-by: tjtanaa <tunjian.tan@embeddedllm.com>

### [cd9ae66](https://github.com/vllm-project/vllm-omni/commit/cd9ae66b3a67b47e13092abcfe648b4ada86042e)

- **作者**: zhumingjue138
- **时间**: 2026-08-18T09:36:08Z
- **提交信息**: [Bugfix][Test] fix Qwen3-omni OOM reliability and drop voxcpm2 stability/reliability test cases (#6299)

Signed-off-by: zhumingjue <zhumingjue@huawei.com>

### [0a1846a](https://github.com/vllm-project/vllm-omni/commit/0a1846aa458283a13c1a7b5a96ab585937f9726c)

- **作者**: Yukim1
- **时间**: 2026-08-18T07:00:24Z
- **提交信息**: [Diffusion] Add native KV cache initialization and Scheduler-managed block allocation (#6094)

Signed-off-by: zwhzzz0821 <zwhzzz0821@users.noreply.github.com>
Co-authored-by: zwhzzz0821 <zwhzzz0821@users.noreply.github.com>

---
