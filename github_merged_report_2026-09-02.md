# GitHub Stars 合并报告 - 2026-09-02

**合并日期**: 2026-09-03
**监控日期**: 2026-09-02
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


**报告日期**: 2026-09-03
**监控日期**: 2026-09-02
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2186
- **最后更新**: 2026-09-02T20:11:07Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 2
- **主要提交者**: Ting, Bin Jia

## AI分析总结

# VeOmni 昨日提交分析报告

## 一、主要更新类型

本次提交涵盖**功能新增**（DeepSeek-V4上下文并行支持）、**Bug修复**（AscendC算子导入问题）以及**工程自动化改进**（CI验证机制），属于混合型更新。

## 二、关键变更点与项目方向关联

1. **DeepSeek-V4上下文并行支持**：为模型训练框架新增对DeepSeek-V4的上下文并行（context-parallel）能力，覆盖attention、compressors和indexer三个核心模块。这与VeOmni“多模态模型训练”和“分布式配方库”的定位高度契合，直接扩展了框架对前沿大模型架构的支持范围。

2. **AscendC算子导入修复**：将fla_npu的导入改为惰性（lazy）加载，解决AscendC flash_gated_delta_rule的潜在初始化问题。这属于框架在多硬件后端（华为昇腾）适配过程中的稳定性优化。

3. **Agent文档路径验证**：在CI流程中新增对agent文档中仓库路径和技能引用的自动校验，属于工程质量和文档一致性的保障措施。

## 三、项目影响与潜在意义

- **模型支持广度提升**：DeepSeek-V4作为当前业界关注的高性能模型，其上下文并行支持使VeOmni能够服务更广泛的用户群体，增强框架在长序列训练场景的竞争力。
- **多硬件生态稳定性增强**：AscendC的修复表明项目正积极完善国产硬件适配，降低用户在不同加速器上的使用门槛。
- **自动化质量保障**：CI中引入文档路径验证，减少因文档错误导致的上手障碍，提升开发者体验。

## 四、值得关注的技术点

- **上下文并行实现**：DeepSeek-V4的attention、compressors和indexer三模块并行化是技术难点，涉及序列切分策略与通信模式设计，值得关注其与现有并行策略的协同方式。
- **惰性导入模式**：fla_npu的lazy import是规避硬件相关依赖在非目标环境下被提前加载的常见做法，体现了对多后端兼容性的细致考量。
- **AI辅助开发痕迹**：提交包含Cursor Agent的co-author标记，反映AI辅助编码已进入实际生产流程。

## 五、对项目发展的影响

结合README中VeOmni“以模型为中心的分布式配方库”定位，本次提交体现了三个发展方向：一是**紧跟前沿模型架构**，通过快速适配DeepSeek-V4保持配方的时效性；二是**强化多硬件适配能力**，为不同计算平台提供一致体验；三是**完善工程化基础设施**，通过CI自动化保障项目在快速迭代中的质量稳定性。整体上，这些变更巩固了VeOmni作为多模态训练基础设施的实用价值，有助于吸引更多研究者和工程师采用该框架进行大规模模型训练实验。

## 详细提交记录

### [573848a](https://github.com/ByteDance-Seed/VeOmni/commit/573848a00fcd7329c2411346c6f4a983e9f67e3f)

- **作者**: Ting
- **时间**: 2026-09-02T20:09:52Z
- **提交信息**: [ops] fix: make fla_npu import lazy in AscendC flash_gated_delta_rule (#1150)

### [f9b1930](https://github.com/ByteDance-Seed/VeOmni/commit/f9b19307538b77a5a013755095748400522311b1)

- **作者**: Bin Jia
- **时间**: 2026-09-02T14:16:28Z
- **提交信息**: [ci, agent] feat: verify repo paths and skill refs in agent docs (#1144)

### [d697023](https://github.com/ByteDance-Seed/VeOmni/commit/d697023c5ad4a4e925a374462da8a166cb686dd9)

- **作者**: Bin Jia
- **时间**: 2026-09-02T07:59:21Z
- **提交信息**: [model, dist, ci] feat: context-parallel DeepSeek-V4 attention, compressors and indexer (#1131)

Co-authored-by: Cursor <cursoragent@cursor.com>

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-09-03
**监控日期**: 2026-09-02
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2773
- **最后更新**: 2026-09-02T20:30:47Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: STwangyingrui

## AI分析总结

### 提交分析总结

**1. 主要更新类型**  
本次提交属于 **Bug修复** 与 **性能优化** 的混合类型，核心是修复注意力机制在特定硬件（SM120）上的后端选择逻辑，同时通过硬件调度优化推理性能。

**2. 关键变更点及与项目方向的关系**  
- **变更内容**：在注意力模块中，保留针对旧架构SM89的覆盖逻辑，但允许SM120通过SageAttention的硬件调度器自动选择后端，而非强制使用固定实现。  
- **与项目方向的关系**：LightX2V定位为**轻量级视频生成推理框架**，强调跨硬件适配与高效执行。该变更直接服务于“在不同GPU架构上自动选择最优计算路径”的目标，确保新硬件（如5090对应的SM120）能充分利用SageAttention的优化能力，与项目“轻量、高性能”的核心理念一致。

**3. 对项目的影响和潜在意义**  
- **影响**：修复了SM120上可能因后端选择不当导致的性能退化或兼容性问题，提升推理稳定性。  
- **潜在意义**：  
  - 增强框架对**最新硬件**的即插即用支持，降低用户在新设备上的部署门槛。  
  - 通过硬件调度器实现**自动化调优**，减少手动配置成本，符合“轻量”定位。  
  - 为后续支持更多架构（如未来GPU）奠定可扩展的调度基础。

**4. 值得关注的技术点**  
- **SageAttention硬件调度器**：利用其动态选择机制，替代硬编码后端，体现了对硬件差异化特性的精细适配。  
- **版本依赖管理**：提交明确要求更新后的SageAttention构建（如5090容器镜像），提示项目对依赖版本敏感，需同步更新环境以保证功能正确性。  
- **兼容性策略**：采用“旧架构保留覆盖，新架构走调度”的分层设计，平衡了稳定性与先进性。

**5. 对项目发展的影响**  
基于README背景，LightX2V致力于提供**高效、易用的视频生成推理方案**。本次提交通过优化注意力计算的后端适配，直接提升了框架在**高端消费级GPU（如5090）**上的实用价值，有助于吸引追求极致性能的用户群体。同时，这种“硬件感知”的调度模式，为项目未来扩展至更多异构平台（如边缘设备或云端加速器）提供了技术范式，强化了其作为**通用轻量推理框架**的竞争力。整体上，该提交是项目在“性能优化”与“生态兼容”双轨上的稳步推进，符合其技术路线图。

## 详细提交记录

### [2a60323](https://github.com/ModelTC/LightX2V/commit/2a603235e07ed281879ae90c5624abc05a14c35b)

- **作者**: STwangyingrui
- **时间**: 2026-09-02T10:56:51Z
- **提交信息**: fix(attention): use SageAttention dispatcher on SM120 (#1461)

Keep the legacy SM89 override, but let SM120 select its backend through
SageAttention hardware dispatch. This requires the updated SageAttention
build in the 5090 container image.

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-09-03
**监控日期**: 2026-09-02
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2229
- **最后更新**: 2026-09-02T12:47:24Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: 谢翊凡

## AI分析总结

### 提交分析总结

**1. 主要更新类型**  
本次提交属于 **Bug修复** 与 **兼容性适配**，核心是解决 transformers 库版本升级带来的 API 弃用问题。

**2. 关键变更点**  
- 将 `config.torch_dtype` 和 `torch_dtype` 关键字参数替换为 `dtype`，以适配 transformers >= 4.56 的新接口。  
- 通过 `try/except TypeError` 或 `packaging.version` 检测版本，实现新旧版本的回退兼容，确保在旧版 transformers 上仍能正常运行。  
- 变更涉及模型加载与配置传递环节，直接影响推理和训练时的数据类型设置。

**3. 对项目的影响与潜在意义**  
- **消除弃用警告**：避免因 transformers 4.56+ 移除旧参数而导致运行时错误，提升项目在最新依赖环境下的稳定性。  
- **前瞻性维护**：主动跟进上游库的 API 变化，减少未来升级 transformers 时的阻塞风险，降低社区用户的使用门槛。  
- **无功能变更**：属于纯技术债清理，不影响模型输出质量或现有功能逻辑。

**4. 值得关注的技术点**  
- 采用 **双保险策略**（异常捕获 + 版本判断）处理 API 差异，体现了对多版本兼容的细致考量。  
- 使用 `packaging.version` 进行语义化版本比较，比简单字符串比较更可靠，是处理依赖版本问题的良好实践。  
- 该模式可作为项目中其他依赖库升级时的参考模板。

**5. 对项目发展的影响**  
VideoX-Fun 作为面向视频生成（CogVideoX-Fun、Wan-Fun）的易用性工具，其核心价值在于“开箱即用”的体验。本次修复直接保障了用户在最新 transformers 环境下的流畅运行，避免了因依赖升级导致的“突然不可用”问题。这有助于维持项目的活跃维护形象，吸引更多开发者基于最新生态进行二次开发或集成，对项目的长期社区健康和生态兼容性具有积极意义。整体上是一次稳健的“地基加固”型更新。

## 详细提交记录

### [4373989](https://github.com/aigc-apps/VideoX-Fun/commit/43739895a18ae11fe66f45690d603aeb57ba360f)

- **作者**: 谢翊凡
- **时间**: 2026-09-02T08:47:39Z
- **提交信息**: fix: use dtype instead of deprecated torch_dtype (#514)

* fix: use dtype instead of deprecated torch_dtype for transformers >= 4.56

config.torch_dtype and the torch_dtype keyword argument were deprecated in transformers 4.56 (PR #39782). Use dtype when accepted and fall back to torch_dtype via try/except TypeError for older versions.

* fix: use dtype instead of deprecated torch_dtype for transformers >= 4.56

config.torch_dtype and the torch_dtype keyword argument were deprecated in transformers 4.56 (PR #39782). Pass dtype based on the installed transformers version (packaging.version), falling back to torch_dtype on older versions.

---------

Co-authored-by: 谢翊凡 <xyf5432@users.noreply.github.com>

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-09-03
**监控日期**: 2026-09-02
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 6321
- **最后更新**: 2026-09-02T23:16:39Z

## 提交统计

- **昨日提交总数**: 13
- **提交者数量**: 8
- **主要提交者**: Edwin Mascarenhas, Vincent, Md Saidul Hoque Anik

## AI分析总结

# FlashInfer 提交分析总结

## 主要更新类型

本次提交以**功能新增**为主，辅以**Bug修复**、**性能优化**、**配置更新**、**文档同步**及**依赖更新**，无纯文档或重构类提交。

## 关键变更点与项目方向

- **MoE后端全面扩展**：cuTile路径补齐Gated（SwiGLU/GeGLU/SiTU等）与非Gated（ReLU²/GELU等）全部十类激活函数，使统一后端与CUTLASS调度表完全对齐。SM90新增CuTe DSL实现的BF16/FP16融合MoE后端，采用连续分组执行模型（moe_sort→GEMM1→GEMM2），GEMM1融合token重排到A矩阵收集，GEMM2融合top-k合并到scatter操作，避免中间数据物化，填补Hopper非量化MoE空白。
- **多架构支持扩展**：SM107（Rubin）路径解除attention-ts的拒绝限制，trtllm-gen路径禁用PDL规避崩溃，并移除要求Rubin专用策略参数的过度守卫——因SM100策略在Rubin上可正常运行。Rubin MoE自动调优解除tile_size=256限制，该限制源于已修复的gemm1/gemm2布局不匹配问题。SM120 MXFP8 MegaMoE内核为RTX PRO 6000/GB10新增完整后端。
- **Router GEMM算子扩展**：新增Kimi-K2/K3及bf16输出共5个固定形状算子，覆盖SGLang全部支持组合，促成其删除自维护内核副本，强化生态整合。
- **稳定性与可靠性修复**：moe_ep通过Init/Update句柄拆分实现CUDA图捕获支持，修复图重放时的非法内存访问。GDN流作用域修复解决多流并发时的缓冲区竞争。bmm_fp8修正SM107上runner列表顺序，确保实验性cute-dsl runner置于末尾，恢复未调优调用的自动回退机制。
- **性能优化**：稀疏MLA启发式将半Q-tile策略限定于短查询，消除长查询重复KV加载，仅改host端选择逻辑，无需新cubin，成本极低。
- **工程维护**：重新生成MoE激活矩阵解决语义合并冲突导致的CI阻塞；TRTLLM-Gen cubin固定版本。

## 项目影响与意义

这些提交表明FlashInfer正从专注Hopper/Blackwell性能，转向**多架构覆盖**（SM90/100/107/120）与**生态兼容性**（对齐SGLang、vLLM需求）并重。通过统一MoE后端、补齐激活函数和算子形状，项目正成为推理框架可依赖的通用内核层。SM90 BF16后端扩大用户基础，Rubin支持确保对最新硬件的及时适配，修复自动回退和放宽策略限制降低了使用门槛与调优负担，符合“开箱即用高性能”定位。

## 值得关注的技术点

- **PDL条件禁用**：仅针对SM107 trtllm-gen路径，512 tokens时10.9%性能开销，4096 tokens时仅1.3%，体现精细化缺陷隔离。
- **CUDA图捕获句柄生命周期**：明确“Init在外、Update在内”的捕获规则。
- **连续分组执行模型**：跨三个算子启用PDL，配合静态grid和事件驱动的aux-stream memset重叠，精细优化延迟隐藏。
- **自动调优策略竞争**：形状启发式作为显式候选参与调优，确保结果不劣于默认策略。
- **架构兼容性认知更新**：SM100策略可在Rubin上运行（通过sm_100f家族目标），纠正此前错误归因的假设。

整体而言，这些提交强化了FlashInfer作为**生产级推理内核库**的成熟度——既有新功能扩展，也有对既有路径可靠性的认真打磨，同时通过自动化文档生成和CI检查维护项目可维护性。

## 详细提交记录

### [c536573](https://github.com/flashinfer-ai/flashinfer/commit/c5365737570a2a156d7cae0c4070fa3770ecc670)

- **作者**: Brian K. Ryu
- **时间**: 2026-09-02T23:16:33Z
- **提交信息**: feat(moe): expand cuTile fused MoE activation support (#4888)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

Expands the unified cuTile MoE backend to support the complete
activation set exposed by FlashInfer's other fused MoE backends:

- Gated: SwiGLU, SwiGLU-Step, GeGLU, GeGLU-Tanh, and SiTU
- Non-gated: ReLU², Identity, GELU, ReLU, and SiLU

**These activations covers all of the ten classes in
_CUTLASS_SEMANTIC_ACTIVATIONS and the complete CUTLASS dispatch table**

This PR adds typed scalar lowering for parameterized SwiGLU,
SwiGLU-Step, and SiTU; threads activation semantics through the BF16 and
NVFP4 W4A4 standalone and fused paths; and extends correctness coverage
across activations, fusion modes, precisions, and supported
architectures.

It also batches the PyTorch MoE reference computation to keep the
expanded CI coverage practical and extends the unified MoE benchmark and
reference check to all supported activations.


## 🔍 Related Issues

<!-- Link any related issues here -->

#4857

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

- **New Features**
- Expanded cuTile Unified MoE support to include gated and non-gated
activations such as SwiGLU, SwiGLU-Step, GeGLU, GeGLU-Tanh, SiTU, GELU,
ReLU, SiLU, ReLU², and Identity.
- Added configurable activation parameters, including scaling and
clamping, for BF16 and NVFP4 W4A4 workflows.
- Extended BF16 and NVFP4 execution paths to accept complete activation
configurations.

- **Documentation**
- Updated benchmark and API documentation to list all supported
activation functions.

- **Tests**
- Expanded coverage for activation variants, parameters, and BF16/NVFP4
execution paths.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [c5bec0c](https://github.com/flashinfer-ai/flashinfer/commit/c5bec0c59deed5f70a6d597ae764abd2cad06fa5)

- **作者**: Vincent
- **时间**: 2026-09-02T21:57:26Z
- **提交信息**: feat(prims_ts): accept SM107 (Rubin) in the attention-ts device gate (#4755)

<!-- .github/pull_request_template.md -->

## 📌 Description

`attention-ts` (the task-scheduled attention path under
`flashinfer/attention/prims_ts/`) rejects compute capability **10.7
(Rubin / SM107)** outright, in both the context and decode entry points:

```
NotImplementedError: attention-ts context requires an SM100a/B200 or SM103a/B300 GPU;
    device cuda:0 has compute capability (10, 7)
```

Because `_validate_device` runs early in `plan()`, this refusal
short-circuits **all** downstream validation. The most visible effect is
on the negative-path tests:
`test_attention_ts_context_plan_rejects_critical_public_contracts` feeds
deliberately-invalid inputs (bad dtype, bad `head_dim`, bad Q/KV head
ratio, bad packed offset, `window_left` without a causal mask) and
asserts each is rejected with its specific message. On Rubin those
assertions never see their expected error — they get the arch rejection
instead.

### Why the exclusion looks conservative rather than technical

Three signals, all pointing the same way:

1. **No stated rationale.** The tuple carries no explaining comment,
unlike the comparable `_TINYGEMM2_SM100_SUPPORTED_COMPUTE_CAPABILITIES`
in `gemm/routergemm.py`, which documents exactly why other 10.x parts
must use the reference kernel.
2. **No `native_only` declaration.** `is_cute_dsl_arch_supported(...,
native_only=True)` exists precisely to mark kernels that need
architecture-specific `tcgen05` instructions (the block-scaled MMA kinds
the DSL only accepts for `sm_100a`/`sm_103a`). Only two call sites use
it, and `prims_ts` is not one of them.
3. **Only family-portable `tcgen05` usage.** The kernels call
`tcgen05_alloc` / `tcgen05_dealloc` / `relinquish_alloc_permit` —
tensor-memory allocation primitives that are valid across the SM100
family, including 10.7.

### What this changes

- Adds `(10, 7)` to `_SUPPORTED_COMPUTE_CAPABILITIES` in `context.py`
and `decode.py`, and updates the diagnostic text to name SM107/Rubin.
- Gates the new capability on the installed CuTe DSL. Rubin runs these
kernels through the `sm_100f` family target, and a DSL older than 4.8
has no `sm_107a` member in `cutlass.base_dsl.arch.Arch`. Without the
gate, widening the tuple would swap one failure for a worse one —
`KeyError: 'sm_107a'` raised from deep inside kernel compilation.
`require_cute_dsl_arch` instead produces an actionable message naming
`CUTE_DSL_ARCH=sm_100f`. The import is deferred so the module keeps its
current import-time behaviour.
- Updates two test regexes that pinned the old wording. Both tests
monkeypatch the capability to `(9, 0)`, so they continue to exercise the
rejection path; only the message pattern changes.

No behaviour change on any non-107 device: every edit either adds 10.7
to a tuple or widens a message.

## 🔍 Related Issues

None filed publicly.

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

Measured on SM107 hardware,
`tests/attention/test_attention_ts_context.py`:

| | `..._plan_rejects_critical_public_contracts` |
|---|---|
| before | 3 failed, 2 passed |
| after | **5 passed** |

(Two of the five passed even with the gate closed, because their
validation happens to run *before* the device check — the ordering is
not uniform, which is why only three were affected.)

`pre-commit run` passes on all four changed files, including `mypy`,
`ruff check` and `ruff format`.

## Reviewer Notes

**This fixes the device gate, not attention-ts on Rubin — please read
before merging.**

`plan()` only validates inputs and builds scheduling metadata; it never
compiles a kernel, which is why the context-path contract tests go
green. The **decode** path is a different story:
`tests/attention/test_attention_ts_decode.py` is unchanged at **4 failed
/ 45 passed / 76 skipped both before and after** this change. Those four
fail earlier, at kernel construction, in the exhaustive deadlock/race
checker:

```
ValueError: Exhaustive checker found 1 aliasing race(s) after exploring 121713 states:
    Softmax0Task writes tmemSoftmaxLocal0 vs MmaTask prod tmemS0 (tmem[256:288])
```

That failure is **not Rubin-specific** — it reproduces on a real B200
(compute capability 10.0) and on SM107 with entirely unmodified code.
`exhaustive_deadlock_race_check` defaults to `True` and runs host-side
at kernel construction; it never queries the device. It also looks like
a known false-positive class: `fmha_decode/fmha_decode_kernel.py`
already carries a `TODO` noting that the checker "currently sees their
aggregate allocation and reports false races" for D256 configurations
with two physical S/stats/P stages, and the reported offset
`tmem[256:288]` points at D256.

So the honest trade-off for the decode path is that this replaces a
clear `NotImplementedError` with an opaque checker `ValueError`.
Reviewers may reasonably prefer to land this only once that checker
issue is resolved. The context path benefits either way.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added support for Rubin (SM107a) GPUs in attention context and decode
operations.
* Added compatibility checks requiring CuTe DSL 4.8 or newer for Rubin
devices.

* **Bug Fixes**
* Updated unsupported GPU error messages to accurately reflect supported
architectures.
  * Updated validation tests for the revised architecture guidance.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [c1fc1af](https://github.com/flashinfer-ai/flashinfer/commit/c1fc1afd79528a356df97283859447fd6d80dcd7)

- **作者**: Vincent
- **时间**: 2026-09-02T21:48:48Z
- **提交信息**: feat(gemm): add router GEMM ops for Kimi-K2 / Kimi-K3 and bf16 output (#4630)

## 📌 Description

Adds five fixed-shape router GEMM ops alongside the three that already
exist, in the same style:

| op | N | K | out dtype | model |
|---|---|---|---|---|
| `mm_M1_16_K7168_N256_bf16` | 256 | 7168 | bfloat16 | DeepSeek-V3, bf16
logits |
| `mm_M1_16_K7168_N384` | 384 | 7168 | float32 | Kimi-K2 (K2/K2.5/K2.6)
|
| `mm_M1_16_K7168_N384_bf16` | 384 | 7168 | bfloat16 | Kimi-K2, bf16
logits |
| `mm_M1_16_K7168_N896` | 896 | 7168 | float32 | Kimi-K3 |
| `mm_M1_16_K7168_N896_bf16` | 896 | 7168 | bfloat16 | Kimi-K3, bf16
logits |

`N=384` is the shape #2480 is about. SGLang's `MoEGate` falls back to
its own in-tree copy of this kernel whenever the expert count is not
256, and cannot delete that copy until flashinfer covers 384. Together
these five cover every (expert count, output dtype) combination SGLang's
kernel supports, so the capability gap closes completely rather than
partially.

`N` and `K` are template parameters on the existing
`generic_router_gemm_op`, so each op is a single instantiation. The
kernel, the launch path, and the 1–16 token unroller are untouched —
`csrc/dsv3_router_gemm.cu` is **+42/−0**.

The supported architecture list gains SM90. The kernel is plain FMA plus
warp shuffles and already guards PDL on `__CUDA_ARCH__ >= 900`; SGLang
dispatches its equivalent at SM90+, so matching that range is the other
half of letting it drop its copy. Verified on H100 (below). This is the
only edit to the three pre-existing ops: `[100, 103, 107]` → `[90, 100,
103, 107]`.

## 🔍 Related Issues

Closes #2480.

Per the discussion there this is a functional-parity task rather than a
performance one — nv-yunzheq: *"There is no performance issue. The
remaining task is just to extend the kernel with fp16 and 384 experts to
make it on par with SGLang, so they could remove the kernel from their
repo."* The SGLang-side change to adopt these and delete
`python/sglang/kernels/{jit/csrc/gemm/dsv3_router_gemm.cuh,ops/gemm/dsv3_router_gemm.py}`
will follow once a release carries them.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] `ruff-format` and `ruff-check` — clean on all changed Python
files.
- [x] `clang-format` (v19.1.1, `--dry-run -Werror`) — clean.
- [x] `mypy` (v1.17.1, repo `pyproject.toml` config) — `Success: no
issues found`.

Hooks were run individually at the pinned versions rather than via
`pre-commit run --all-files`, as the environment this was developed in
has no `pre-commit` install.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing.

`tests/model_optimizations/test_router_gemms.py` gains the five new ops
in the existing positive parametrization, per-op negative cases for
wrong expert count and wrong output dtype, and the new ops in the shared
`num_tokens`/stride negative arrays.

Run in the `flashinfer-ci-cu132` container (torch 2.13.0+cu132):

| GPU | SM | Result |
|---|---|---|
| B200 | 100 | **144 passed**, 0 failed |
| H100 | 90 | **144 passed**, 0 failed |

## Reviewer Notes

**SM90 is newly claimed.** The ops previously declared `[100, 103, 107]`
with a `TODO: other compute capabilities may be supported but are
untested`. The TODO is left in place, since 110/120/121 remain untested.
SM103 and SM107 stay claimed but **were not swept in this round** — the
kernel is architecture-agnostic, so they are expected to pass, but that
is an expectation rather than a measurement, and I would rather say so
than imply coverage I do not have. Happy to add B300/GR100 runs if
reviewers want them before merge.

**Scope.** Deliberately narrow: five ops, their tests, exports and doc
entries. Nothing pre-existing is restructured, and the benchmark is
untouched.

### [c7fcfe7](https://github.com/flashinfer-ai/flashinfer/commit/c7fcfe7309677cc04ff486822fd212dc010e5db9)

- **作者**: Anerudhan Gopal
- **时间**: 2026-09-02T21:47:53Z
- **提交信息**: feat(moe_ep): make the nccl_ep split path CUDA-graph capturable (#4795)

## 📌 Description

A `moe_ep` split-path `Handle` is created per forward today, which makes
the path impossible to capture into a CUDA graph. A graph records the
device pointers it sees at capture time, so a handle created *and
destroyed* inside the captured forward leaves the replay dereferencing
freed memory.

Measured on 4×B200 (dp=4, Qwen3-30B-A3B, driven through vLLM's
`flashinfer_ep_low_latency` backend):

| Configuration | Result |
|---|---|
| `--enforce-eager` | rc=0, ~616 tok/s per rank across 4 ranks |
| CUDA graphs enabled | capture completes (PIECEWISE 35/35, FULL 35/35),
then the **first replay** raises `CUDA error: an illegal memory access
was encountered` |

Silent at capture, crash at replay — invisible to any test that doesn't
actually run inference under graphs.

**NCCL-EP itself supports capture.** `contrib/nccl_ep/ep_test.cu` has a
`--use_cuda_graph` mode, and it is *not* gated on the algorithm, so LL
and HT are both captured there. Its recipe is a split:

> Non-graph mode tests CreateHandle (combined Init+Update). Graph mode
tests the Init+Update split, where **InitHandle stays outside the
capture** (host-side allocation only) **and UpdateHandle is recorded
inside** the captured region.
> — `ep_test.cu:478-481`

and `nccl_ep.h:422` states the rule directly:

> to avoid CUDA graph invalidation, all Handles must be created before
the beginning of the CUDA graph capture.

Two changes are needed, and **the second is the one that actually makes
capture work**.

### 1. `Handle.update()` — the missing per-step half

`moe_ep` only ever called the combined `ncclEpCreateHandle`, so the
Init/Update split could not be expressed through this API.

```python
# Before: one handle per forward -- uncapturable
for step in ...:
    handle = fleet.create_handle(HandleParams(topk_ids=topk_ids))   # Init + Update
    handle.dispatch(...); handle.combine(...); handle.complete()

# After: one durable handle, per-step rebind -- capturable
handle = fleet.create_handle(HandleParams(topk_ids=topk_buf))       # outside capture
for step in ...:
    handle.update(HandleParams(topk_ids=topk_buf))                  # inside capture
    handle.dispatch(...); handle.combine(...); handle.complete()
```

Optional capability with a raising default on the ABC, matching
`dispatch_send_only` / `dispatch_recv_only`, so `NixlEpHandle` and any
out-of-tree `Handle` are unaffected.

### 2. `NcclEpHandle._op_stream()` — issue transport work on the capture
stream

Every dispatch/combine/complete previously issued on `self._stream`, the
handle's **creation-time** stream (the `HandleAlgoKnobUserStream` value,
else the fleet's). That is correct for a per-forward handle, which is
created on the same stream it runs on. It is wrong for a persistent one:
it is created *before* the capture begins, so its stream is not the
stream being captured, and the transport work lands outside the graph
entirely — **the capture records nothing and the replay is a silent
no-op.**

`_op_stream()` returns the capture stream while capturing and
`self._stream` otherwise, so non-graph behaviour — including an explicit
`UserStream` — is byte-identical. Handle *creation* deliberately still
uses `self._stream`: `nccl_ep.h:422` requires it to happen outside any
capture.

This one is easy to miss because it fails silently rather than loudly;
`update()` alone is not sufficient.

## 🧪 Verification on 4×B200

`tests/moe_ep/test_moe_ep_cudagraph_multirank.py`, 4 ranks, **both
algorithms, all ranks passing**:

```
rank 0..3: low_latency     capture + replay OK across changed routing
rank 0..3: high_throughput capture + replay OK across changed routing
2 passed
```

The test asserts three properties in increasing order of what they would
catch:

1. capture completes;
2. replay does not fault and reproduces the eager result — the
regression above;
3. **the transport's reported routing changes when `topk_ids` is
rewritten in place between replays.** This is the one that matters: an
identity round trip is routing-invariant, so comparing outputs cannot
distinguish "`update()` replayed" from "`update()` skipped". The test
interrogates the transport (`expert_counts`, falling back to
`recv_topk_idx`) instead.

Assertions are algorithm-aware. **HT's identity round trip is
deliberately not asserted, because HT does not have that property:**
`_dispatch_ht` sizes its recv buffer to `max_tokens_per_rank * world`
and dispatch only writes the slots that actually received tokens, so an
identity pass-through hands `combine` the unwritten remainder. Real HT
consumers compute over the whole static buffer or trim to
`recv_total_counter`. Capture correctness is still fully covered for HT
(replay must match eager, routing must track across replays); only the
numerical check is weaker than LL's.

The test also completes all collective work and tears the fleet down
*before* asserting — a bare assert mid-test aborts one rank inside a
collective and strands the rest at the next barrier, turning a one-line
failure into a wedged multi-hour job.

## 🔍 Related Issues

Follow-up to #4183 (EP fault tolerance). Consumer:
vllm-project/vllm#47948.

**No caller in this repo uses `update()` yet** — consuming it is the
vLLM follow-up, which pins `flashinfer-python` and so needs a release
first.

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

`tests/moe_ep/nccl_ep/test_handle_mock.py` gains eight cases:

- rebinding **reuses the native handle** rather than creating a second
one — the property that makes capture safe, and the one that would
regress silently
- `top_k` changes are rejected
- growing past the creating token count is rejected; **shrinking is
allowed** (decode steps are smaller than the capture shape)
- the ABC default raises `NotImplementedError`
- `update()` is capturable — i.e. contains no host sync, the failure
mode that makes a prepare path uncapturable
- the caller's buffer is **bound, not copied** (a copy would make every
replay re-run stale routing)
- outside capture, ops stay on the knob stream (pins that `_op_stream()`
did not change non-graph behaviour)
- under capture, ops move to the capture stream

`FakeHandle` in `tests/moe_ep/nccl_ep/conftest.py` gains an `update()`
mirroring `ncclEpUpdateHandle`'s contract (rebinds routing, never
reallocates).

**72 passed** in the `nccl_ep` mock suite, locally and on the 4×B200
rig; `ruff check` / `ruff format` clean; `pre-commit` clean.

AI-assisted (Claude Code); every change reviewed and the failure
reproduced end-to-end by the submitter.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added support for updating existing communication handles with new
routing information without reallocating buffers.
  * Enables handle reuse across forward passes and CUDA graph replays.
* Ensures communication operations use the appropriate stream during
CUDA graph capture.

* **Bug Fixes**
* Added validation for unsupported updates, routing changes, token
limits, and low-latency hidden sizes.
* Prevents dispatch operations from exceeding per-rank capacity limits.

* **Tests**
* Expanded coverage for handle reuse, CUDA graph replay, capacity
limits, routing validation, and stream behavior.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Anerudhan Gopal <agopal@nvidia.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [f7d8be0](https://github.com/flashinfer-ai/flashinfer/commit/f7d8be0365f65138fe368a59874c98905790c57d)

- **作者**: Md Saidul Hoque Anik
- **时间**: 2026-09-02T21:47:41Z
- **提交信息**: feat(moe_ep): SM120 MXFP8 swap-AB CuTeDSL MegaMoE kernel (#4387)

# feat(moe_ep): SM120 MXFP8 swap-AB CuTeDSL MegaMoE kernel

## Summary

Adds an **SM120 (sm_120/sm_121) MXFP8 MegaMoE backend** to
`flashinfer.moe_ep` — the swap-AB CuTeDSL megakernel (fused dispatch +
grouped GEMM + combine) for the RTX PRO 6000 / GB10 (DGX Spark) class of
Blackwell parts. Registered as `sm120_mxfp8_mxfp8_bf16_cutedsl` behind
the standard `MegaKernelBackend` contract, on the same taxonomy layout
as the SM100/SM90 backends.

> **Status: functional correctness is validated; performance tuning and
benchmarking are ongoing.** The backend currently takes a knob dict only
(no autotune yet), and no performance numbers are quoted in this PR —
perf tables will follow once the tuning sweep lands.

## What's included

- **Vendored kernel drop**: `kernel_src/sm120/` — verbatim snapshot of
the four kernel packages (`common/`, `src/`, `moe_sm120_mxfp8_swapab/`,
`moe_mxfp8_glu/`) from the `sm120_swapab_wt` fork at `d19d30a` (branch
`run/sm120-mxfp8-perf`), including two uncommitted worktree edits
recorded in `VENDOR.md`. `src/` stays byte-for-byte upstream; all
adaptation lives in the shim.
- **Shim layer**: mirrors the sm90 fork-tree conventions — `_paths`
sibling-tree guard, per-tree `comm.py` (plus
`zero_local_counter_regions`; this drop's kernel does not tail-clean its
local counters), all-lazy `kernel_helpers`, and the SM120 MXFP8 frontend
with `combine_output` + topk-reduce second stage, per-expert epilogue
args, K-major weight views, and a mirrored-ABI-constant guard.
- **Backend**: `backends/mega/kernel/sm120/mxfp8_mxfp8_bf16_cutedsl/`
with `Sm120_Mxfp8_Mxfp8_Bf16_Cutedsl_MegaMoeConfig` (native
`token_back_mode` enum), K-major + interleave-8 weight preprocessing,
torch-composed staging (no fused DataPreprocess in this tree),
`validate_mega_arch_sm120` (exact sm_120/sm_121 family), and the sm120
runtime-requirements alias. Exported from `flashinfer.moe_ep`.
- **Rank-sharing bootstrap for single-GPU sm_12x boxes**: sm_12x cluster
nodes have one GPU, and the drop's own harness runs N ranks per GPU. The
FI runtime now folds `LOCAL_RANK` onto the physical GPUs (identity when
there are enough), and under `MEGA_SINGLE_GPU_GLOO=1` inits the process
group as gloo with a CPU-side NVSHMEM UID broadcast (NCCL cannot host
two ranks on one device).
- **Tests**: sm120 mxfp8 mega multirank suite mirroring the sm100 one
(layer-vs-shim parity across staged/prestaged/token-back profiles,
all-gather torch-oracle anchor, registry/preprocess checks), a shared
arch-free term-magnitude oracle-compare module, new `arch_sm120` pytest
marker (with `arch_blackwell` tightened to the sm_10x family so sm100
suites stop collecting on sm_11x/12x hosts), and a `mega_sm120` entry in
`run_tests.sh`.

## Upstream gaps found and guarded

Each was pinned by A/B against the drop's own runner and is recorded in
`VENDOR.md` as a pending-upstream item; the FI backend rejects the
broken configuration rather than silently running it:

| gap | disposition |
|---|---|
| `in_kernel_fc2_reduce` crashes with `cudaErrorIllegalAddress`
(verified RTX PRO 6000, 4 ranks / 1 GPU, DSL 4.6.1); absent from the
kernel team's own test scripts | rejected by the backend; ikr tests
skipped with documented reason; shim keeps the plumbing for a fixed drop
|
| `cluster_m > 1` fails `cute.compile` ("expects num_multicast to be 1
for non multicast G2S copies"); upstream scripts always use (1,1,1) |
config pinned to cluster (1,1,1) |
| `gate_up_clamp` is dead plumbing — `kernel_fc12` stores it but never
reads it; output bit-identical with/without (invisible to the drop's
±0.5-sparse test data) | backend rejects a set clamp; tests run
clampless |
| `world_size=1` (`MEGA_NO_DIST`) numerics silently wrong for
`mma_tiler` N=128 (5-20% of cells; reproduced upstream at their own
standard geometry); same tile bit-exact at world_size=4 | documented in
VENDOR.md; multirank is the validated path |

Two harness-level fixes that the correctness claims depend on: the
oracle's `all_gather` is CPU-staged under the rank-sharing gloo group
(gloo has no CUDA all_gather — the reference was previously built from
corrupted operands), and the shim's `_main` smoke device folds onto
physical GPUs.

## Usage

```python
from flashinfer.moe_ep import (
    BootstrapConfig, FleetParams, MegaConfig, MoEEpLayer, MoEEpTensors, MoEWeightPack,
    Sm120_Mxfp8_Mxfp8_Bf16_Cutedsl_MegaMoeConfig,
)

layer = MoEEpLayer(
    BootstrapConfig(world_size=world_size, rank=rank),
    FleetParams(num_experts=256, max_tokens_per_rank=tokens, token_hidden_size=7168),
    weights=MoEWeightPack(w13=w13_bf16, w2=w2_bf16),
    backend=MegaConfig(
        megakernel=Sm120_Mxfp8_Mxfp8_Bf16_Cutedsl_MegaMoeConfig(intermediate_size=2048, top_k=8),
    ),
)
out = layer.forward(MoEEpTensors(hidden_states=x_bf16, topk_ids=ids, topk_weights=w))
```

On a single-GPU sm_12x box, run multirank via the drop's env:
`MEGA_SINGLE_GPU_GLOO=1 torchrun --nproc_per_node=4 ...`.

## Constraints

- Exact sm_120 / sm_121 family only (`validate_mega_arch_sm120`).
- `in_kernel_fc2_reduce`, `cluster != (1,1,1)`, and `gate_up_clamp` are
rejected until the upstream drop fixes them (see table above).
- Validated against nvidia-cutlass-dsl 4.6.1.
- No autotuner yet — kernel knobs are passed as an explicit dict.

## Testing

- sm120 mxfp8 mega multirank suite green on RTX PRO 6000 (4 ranks / 1
GPU via the rank-sharing gloo bootstrap), DSL 4.6.1:
layer-vs-direct-shim parity across staged / prestaged / large-token
dispatch token-back profiles, plus the all-gather torch-oracle anchor
(the sm120 reference pins `gate_up_interleave=8` +
`apply_topk_in_fc1=True` itself).
- Registry, config-validation, and weight-preprocess checks.
- `run_tests.sh mega_sm120` (own torchrun process; kernel trees are
process-exclusive).

## Performance

**Ongoing.** Kernel-level tuning (tiler/knob sweeps) and the standalone
microbenchmark/e2e runs are in progress; numbers will be posted to this
PR (or a follow-up) once the tuning sweep completes. Nothing in this PR
should be read as a perf claim yet.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added SM120 MXFP8 MegaMoE support, including fused execution,
quantized inputs and weights, token communication, top-k reduction, and
single- or multi-rank operation.
* Added offline and collective autotuning for NVFP4 and MXFP8 workloads.
* Added architecture-specific backend configurations and runtime
validation for SM90, SM100, and SM120 hardware.

* **Improvements**
* Introduced clearer backend and kernel names while preserving
deprecated aliases for compatibility.
* Improved workspace cleanup, distributed initialization, CUDA graph
safeguards, and input validation.

* **Documentation**
* Expanded architecture, tuning, compatibility, testing, and
vendored-source guidance.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Md Anik <mhoqueanik@s4124-0010.ipp1a1.colossus.nvidia.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: Md Anik <mhoqueanik@ipp2-2176.ipp2u1.colossus.nvidia.com>
Co-authored-by: Anerudhan Gopal <agopal@nvidia.com>

### [cc6e879](https://github.com/flashinfer-ai/flashinfer/commit/cc6e8794c49bf66172627bdb9742fcb17d18b839)

- **作者**: Vincent
- **时间**: 2026-09-02T21:03:17Z
- **提交信息**: fix(moe): disable PDL in the trtllm-gen fused-MoE path on SM107 (Rubin) (#4806)

## 📌 Description

PDL in the trtllm-gen fused-MoE pipeline intermittently fails on SM107
(Rubin) with
`unspecified launch failure`, and occasionally hangs. The crash surfaces
at the
`routingIndicesClusterKernel` launch in
`trtllm_fused_moe_routing_custom.cu`.

A/B stress runs on SM107 hardware isolated the trigger. With PDL enabled
the
renormalize-routing tests crash across routing modes (split-topK on and
off), dtypes
(BF16 / MxFP4 / MxInt4) and autotune on/off — **4 crashes in ~21
full-file runs**. The
same loop with PDL fully disabled ran clean.

This clamps `enable_pdl` to off on SM107 at the six trtllm-gen MoE entry
points,
**including when the caller passes `enable_pdl=True` explicitly**: an
illegal memory
access is not something a caller should be able to opt into while the
underlying
launch-dependency chain is unaudited for Rubin timing.

### Scope is deliberately narrow

* **Only compute capability `(10, 7)`.** `device_support_pdl()` returns
`True` for every
`major >= 9`, so gating there instead would cost Hopper and Blackwell
for a
  Rubin-only defect.
* **Only the trtllm-gen path.** The three CUTLASS MoE sites are
untouched — that path
  has soaked with PDL enabled on Rubin for 9+ nights without a crash.

## 🧪 Performance impact

Measured on SM107, trtllm-gen `NvFP4xNvFP4` routed MoE (128 experts,
top-k 8,
hidden 2048, intermediate 768), autotuned:

| tokens | PDL on | PDL off | cost |
|--------|--------|---------|------|
| 8      | 0.027 ms | 0.028 ms | +3.7% |
| 64     | 0.046 ms | 0.048 ms | +4.3% |
| 512    | 0.055 ms | 0.061 ms | **+10.9%** |
| 4096   | 0.156 ms | 0.158 ms | +1.3% |

The cost is launch-overlap latency, so it is largest mid-range and
negligible at 4096
tokens where the kernels are long enough that overlap stops mattering.

**Caveat on the numbers:** single run per arm with CUDA-event timing
(CUPTI
unavailable), so the 1–4% points are within noise. The 512-token gap is
the one to
trust — it reproduces in both the autotuned (+10.9%) and untuned (+6.0%)
columns, so it
is not an autotuner artifact.

## 🔍 Related Issues

Mitigates the SM107 MoE routing illegal-memory-access reported against
the v0.6.18
release candidates. **This is a mitigation, not a root-cause fix** —
revert it once the
PDL launch-dependency chain is audited for Rubin timing.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks
- [x] `pre-commit` installed and hooks run (`ruff check`, `ruff format`
clean)

### 🧪 Tests
- [x] Verified on SM107 hardware; the A/B above was run on-device
- [ ] No new tests added — this changes a dispatch default, and the
existing MoE suite
      exercises both paths

AI-assisted (Claude Code).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Improved compatibility for fused Mixture-of-Experts operations on
Rubin GPUs.
* Automatically disables unsupported performance behavior for affected
MoE execution paths while preserving existing behavior elsewhere.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [61f9b29](https://github.com/flashinfer-ai/flashinfer/commit/61f9b29d2733883fd8ce05afbed35fcfcb8b1b46)

- **作者**: Lee Yong Jun
- **时间**: 2026-09-02T18:34:03Z
- **提交信息**: fix(gdn): stream-scope WY staging buffers and prefill launch workspace (#4476)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->
- `gdn_decode_bf16_wy_output_only.py`: the persistent short-T staging
buffers (`_STAGE`) were keyed by device/shape/dtype only. Two same-shape
calls on different streams shared one buffer set, so the second call's
staging `copy_()` could overwrite inputs the first call's kernel was
still reading. The stream is now part of the staging key; same-stream
reuse keeps the original zero-copy-tail behavior.
- `blackwell/gdn_prefill.py`: the growable launch workspace lived inside
the per-specialization compile-cache dict. The kernel writes TMA
tensormap descriptors into that workspace on every launch, so concurrent
calls on the same specialization could clobber each other's descriptors.
The workspace is now allocated per call, and the compile cache holds
only the compiled callable and `num_sm`, matching the lifecycle
separation described in #4214.

Reproduction of the WY race on unmodified main, measured on RTX 5090
(SM120): two streams, same shape (B=512, T=2, H=HK=16, HV=32),
interleaved without sync. Each result is compared against the
single-stream result of the same inputs.

| run | corrupted iterations | max abs err |
| --- | --- | --- |
| two streams | stream1 2/100, stream2 41/100 | 0.34 / 0.37 |
| single-stream control (same jitter) | 0/100 | 0.0 |

One observation from reproducing this: the race only materializes when
the enqueued GPU work outlasts the host launch gap (at B=64 the GPU
drained every op before the next enqueue and 200 iterations showed no
corruption), so the regression test deliberately uses a large batch.

New `tests/gdn/test_multistream_overlap.py`:

- Deterministic per-stream buffer-ownership checks for both WY staging
branches (full staged T=2, "ab" staging pair at T=4 with non-contiguous
a/b). These fail on the pre-fix code regardless of timing.
- The two-stream overlap stress above as a regression test.
- SM100 prefill: two-stream self-consistency plus a white-box check that
the compile-cache value holds only `compiled`/`num_sm`.

Existing `tests/gdn/test_decode_delta_rule.py -k wy_output_only`: 15
passed on SM120 before and after the change. I attempted the full
`test_decode_delta_rule.py` locally as well, but my dev box's network
filesystem kept stalling multi-hour runs, so I'd like to lean on GPU CI
for the full suite. The changed code paths are the WY module and the
SM100 prefill wrapper, and both are covered by the targeted runs above.

## 🔍 Related Issues

<!-- Link any related issues here -->
Part 3 of the plan in #4214 (GDN-H4): mutable execution state was stored
in process-global caches without stream ownership.
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
- I don't have SM100 hardware locally, so the prefill change is verified
only as import/skip-clean on SM120; I'd appreciate a GPU CI run (or a
check on H100/B200) for
`test_blackwell_prefill_workspace_not_in_compile_cache`.
- While auditing for other instances of the same pattern I noticed
`delta_rule_dsl/delta_rule_cp_sm120.py` (`_get_cp_workspace`) also
caches workspace tensors in a `functools.cache`. It's not listed under
GDN-H4 in #4214, so I left it out to keep the scope as planned. Happy to
address it here or in a follow-up if that seems reasonable.
- A destroyed stream leaves its staging entry in `_STAGE` (small,
bounded by the number of streams actually used for GDN decode). If
that's a concern I'm open to an explicit eviction hook or a capped pool
instead.
<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Improved reliability during concurrent operations across multiple CUDA
streams.
* Prevented shared temporary buffers from causing incorrect or corrupted
results.
  * Ensured each invocation uses isolated workspace memory.
* Improved safe reuse of temporary resources for short-sequence
workloads.

* **Tests**
* Added coverage for overlapping multi-stream execution and workload
correctness.
* Added validation for compilation-cache safety and numerical output
consistency.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Ka-Hyun Nam <knam@nvidia.com>

### [6f9a513](https://github.com/flashinfer-ai/flashinfer/commit/6f9a513ab9046319d765dd8c6c7085439a29afbf)

- **作者**: Edwin Mascarenhas
- **时间**: 2026-09-02T17:57:09Z
- **提交信息**: perf(sparse mla): Update sparse MLA half-Q-tile heuristic to apply to short queries only (#4752)

## 📌 Description

### Summary

This PR restricts the sparse-MLA half-Q-tile heuristic to short queries
(`mMaxSeqLenQ <= 16`). Short decode/MTP queries retain the existing Q8
choice,
while long-query DeepSeek-V4 prefill uses Q16.

The existing heuristic considers the number of KV-split CTAs and batch
size,
but not the amount of Q-axis parallelism. For the DeepSeek-V4 prefill
case on
B200:

- `numHeadsQPerKv = 16`, so the full and half Q tiles are Q16 and Q8.
- `maxNumCtasPerSeqKv = ceil(min(maxSeqLenKv, sparseMlaTopK) /
tileSizeKv)`.
- With `sparseMlaTopK = 2048` and `tileSizeKv = 128`,
  `maxNumCtasPerSeqKv = 16`.
- At batch 1 on a 148-SM B200, `1 * 16 <= 148 / 8`, so the current
condition
  selects Q8 even when `maxSeqLenQ = 16384`.

Q8 is useful for short batch-1 queries because it creates more
head-splitting
CTAs. A 16K query already supplies 16K-way Q-axis parallelism. In that
case Q8
changes the main-kernel grid from `(16384, 1, 1)` to `(16384, 2, 1)` and
makes
two CTAs load the same sparse KV set for the two eight-head groups. Q16
avoids
that duplicated KV traffic.

No new cubin is required: both Q8 and Q16 variants are already shipped.
The
change only narrows the host-side selector condition.

### vLLM DeepSeek-V4 prefill call site

vLLM invokes this generation-form FlashInfer API from its DeepSeek-V4
`_forward_prefill` path:
[`flashinfer_sparse.py:L781-L886`](https://github.com/vllm-project/vllm/blob/728d3ad09/vllm/models/deepseek_v4/nvidia/flashinfer_sparse.py#L781-L886).
Specifically, `_forward_prefill` calls
`flashinfer_trtllm_batch_decode_sparse_mla_dsv4(query=q_chunk, ...)`,
which is
why prefill reaches `selectSparseMlaGenerationKernel()`.

### Native FlashInfer B200 benchmark

This PR adds `trtllm_batch_decode_sparse_mla_dsv4` as a first-class
attention
routine in the repository's canonical
`benchmarks/flashinfer_benchmark.py`
driver. It uses the public FlashInfer API and the driver's existing
backend
filtering, common CLI flags, `bench_gpu_time`, cold-L2 handling, CSV
schema,
test-list execution, and generated reproduction commands. Correctness is
checked before timing against an independent sampled FP32 attention
oracle.

Native benchmark contract:

- 1x NVIDIA B200; PyTorch `2.13.0+cu130`; FlashInfer `0.6.16.post3`.
- Batch 1, 16 Q heads, head dim 512, FP8 E4M3 Q/KV, BF16 output.
- KV sequence length 16,384; 128 SWA + 1,920 compressed entries per
query
  (`sparseMlaTopK=2048`); HND cache layout; PDL disabled.
- Query lengths `1,8,16,17,32,256,4096,16384` cover both sides of the
guard
  and the target long-prefill case.
- Canonical `bench_gpu_time`: cold L2, 20 untimed warmups and 100
measured
iterations per case. `cupti-python` was absent in the application image,
so
  the driver used its documented CUDA-event fallback.
- Sampled FP32 reference checking ran before timing for every case. All
BF16
  outputs were finite and the maximum absolute error was `1.81e-4`.

From the FlashInfer repository root, the target 16K case can be
reproduced
with the canonical benchmark driver as follows:

```bash
python3 benchmarks/flashinfer_benchmark.py \
  --routine trtllm_batch_decode_sparse_mla_dsv4 \
  --backends trtllm-gen \
  --batch_size 1 \
  --s_qo 16384 \
  --s_kv 16384 \
  --num_qo_heads 16 \
  --num_kv_heads 1 \
  --head_dim_qk 512 \
  --head_dim_vo 512 \
  --page_size 256 \
  --swa_topk 128 \
  --compressed_kv_len 4096 \
  --compressed_page_size 64 \
  --compressed_topk 1920 \
  --kv_layout HND \
  --q_dtype fp8_e4m3 \
  --kv_dtype fp8_e4m3 \
  --out_dtype bfloat16 \
  --no_cuda_graph \
  --refcheck \
  --dry_run_iters 20 \
  --num_iters 100 \
  --generate_repro_command \
  --case_tag dsv4-q16384 \
  -vv
```

For the full boundary sweep, repeat the same command with
`--s_qo 1, 8, 16, 17, 32, 256, 4096, 16384` individually. Parent and PR
measurements must be run from their respective source checkouts with a
freshly
built `fmha_gen` host launcher; an installed AOT launcher can otherwise
hide
the selector change.

| Q length | Parent tile | PR tile | Parent (ms) | PR (ms) | Speedup |
|---:|:---:|:---:|---:|---:|---:|
| 1 | Q8 | Q8 | 0.027616 | 0.027616 | 1.000x |
| 8 | Q8 | Q8 | 0.027648 | 0.027584 | 1.002x |
| 16 | Q8 | Q8 | 0.029696 | 0.029680 | 1.001x |
| 17 | Q8 | Q16 | 0.029696 | 0.025568 | 1.162x |
| 32 | Q8 | Q16 | 0.037920 | 0.029696 | 1.277x |
| 256 | Q8 | Q16 | 0.134144 | 0.080736 | 1.662x |
| 4,096 | Q8 | Q16 | 1.565744 | 0.825200 | **1.897x** |
| 16,384 | Q8 | Q16 | 4.931104 | 2.614256 | **1.886x** |

The canonical-run logs show that the kernel name stays Q8 through `Q=16`
and
changes to Q16 at `Q=17`, exactly matching the new boundary. At the
target
`Q=16384`, the native API result is a 46.99% latency reduction. The
`Q<=16`
arms use the same Q8 selector path and agree within 0.23%.

### vLLM DeepSeek-V4 B200 benchmark

Hardware and software:

- 8x NVIDIA B200, TP=8
- DeepSeek-V4-Pro, FP8 KV cache, block size 256
- vLLM `0.1.dev19908+g728d3ad09`
- FlashInfer `0.6.16.post3`
- Image `vllm/vllm-openai:nightly-dev-x86_64-cu13.0.1-728d3ad`
(SHA-256
`9d812de47e34568de2a945635dd29cf2d6784fee62e3a602283d2665a9459cac`)
- `FLASHINFER_MLA_SPARSE_DSV4`, prefill-query quantization enabled, FP4
  indexer cache enabled, MTP=3
- Concurrency 16, ISL=16,384, OSL=1, seed 42,
  `max_num_batched_tokens=16384`, prefix caching disabled

The server used the DeepSeek-V4 configuration with the workload changes
above.
The relevant launch arguments were:

```bash
vllm serve /models/DeepSeek-V4-Pro \
  --served-model-name deepseek-ai/DeepSeek-V4-Pro \
  --trust-remote-code --tensor-parallel-size 8 \
  --kv-cache-dtype fp8 --block-size 256 --max-model-len 1048576 \
  --max-num-seqs 32 --max-num-batched-tokens 16384 \
  --attention-config '{"backend":"FLASHINFER_MLA_SPARSE_DSV4","use_prefill_query_quantization":true,"use_fp4_indexer_cache":true}' \
  --speculative-config '{"method":"mtp","num_speculative_tokens":3,"rejection_sample_method":"synthetic","synthetic_acceptance_length":2.49}' \
  --no-enable-flashinfer-autotune --no-enable-prefix-caching --enforce-eager
```

Each arm ran four unprofiled repeats of 16 requests. The first repeat
used 16
warmup requests; the server remained warm for the other repeats. The
client
command was:

```bash
python utils/bench_serving/benchmark_serving.py \
  --model deepseek-ai/DeepSeek-V4-Pro \
  --served-model-name deepseek-ai/DeepSeek-V4-Pro \
  --backend vllm --base-url http://127.0.0.1:8888 \
  --dataset-name random --random-input-len 16384 --random-output-len 1 \
  --random-range-ratio 1.0 --max-concurrency 16 --request-rate inf \
  --num-prompts 16 --ignore-eos --seed 42 --trust-remote-code \
  --tokenizer-mode deepseek_v4 --use-chat-template --dsv4
```

Q8 is the parent selector. Q16 is the same image and workload with only
this
query-length guard applied and the AOT host launcher rebuilt.

| Metric | Q8 (parent) | Q16 (this PR) | Change |
|---|---:|---:|---:|
| Four throughput repeats (tok/s) | 25,292.38; 25,286.59; 25,308.48;
25,294.95 | 27,892.23; 27,939.74; 27,923.39; 27,938.74 | -- |
| Mean total throughput | 25,295.60 tok/s | 27,923.53 tok/s |
**+10.39%** |
| Mean throughput per GPU | 3,161.95 tok/s | 3,490.44 tok/s |
**+10.39%** |
| Exact main sparse-MLA kernel | 142.38 ms/step | 75.89 ms/step |
**1.88x faster; -46.70%** |
| Overlap-accounted attention | 198.72 ms/step | 132.66 ms/step |
**-33.24%** |
| Iteration wall time | 648.73 ms/step | 589.02 ms/step | **-9.20%** |
| Main-kernel grid | `(16384, 2, 1)` | `(16384, 1, 1)` | **2x fewer
CTAs** |

The throughput coefficient of variation was 0.037% for Q8 and 0.079% for
Q16.
The wall-time ratio implies +10.14% throughput, consistent with the
independent
unprofiled +10.39% result.

A 64-step profile validated the selector on all eight ranks. Per rank,
all
`62 layers * 64 steps = 3968` main sparse-MLA calls used the Q16 kernel,
with
zero main-path Q8 calls. The two short MTP calls per step remained Q8
(`128` calls per rank), as intended.

The Q8 and Q16 throughput arms used different B200 nodes. The image,
framework,
model, and workload were identical; non-attention categories agreed
within
about 2.4%, and the exact main FMHA reduction (66.48 ms/step) accounts
for the
full raw-attention reduction (66.10 ms/step). A same-node rerun would
provide
the strictest hardware-controlled A/B.

## 🔍 Related Issues

N/A

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

Validation performed:

- `pre-commit run --all-files`: passed.
- Canonical `benchmarks/flashinfer_benchmark.py` public-API benchmark on
one
B200: 20 warmups + 100 measured iterations for each of eight Q lengths
and
  both selector variants; all sampled FP32 correctness checks passed.
  Long-prefill Q16 was 1.886x faster at `Q=16384` with cold L2.
- 4x unprofiled B200 throughput repeats per arm: passed, 16/16 requests
each.
- 64-step, eight-rank B200 selector profile: Q16 on all 3968 main-layer
calls
  per rank; short MTP remained Q8.

## Reviewer Notes

- This deliberately changes only the host-side tile selector. It does
not
  modify numerical code or cubin artifacts.
- The `<= 16` boundary matches the existing short-query/DSv3 min-latency
boundary in this runner and covers decode plus the configured MTP
length.
- The benchmarked package used an AOT host launcher, so the validation
rebuilt
that launcher after editing the header. Normal source/CI builds will
compile
  the updated selector into the launcher.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added benchmarking support for DeepSeek-V4 sparse MLA attention with
configurable sparse-window, compressed-cache, paging, and cache-length
settings.
* Added performance metrics, support-matrix coverage, documentation, and
sample configurations for supported hardware and the TensorRT-LLM
generation backend.
* **Bug Fixes**
  * Improved sparse MLA tile selection for long-query prefill workloads.
* **Tests**
* Added validation for availability, configuration, tensor layouts,
execution behavior, and reported metrics.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [b250399](https://github.com/flashinfer-ai/flashinfer/commit/b250399302acb2c4925b03416188c6678b762fbd)

- **作者**: Vincent
- **时间**: 2026-09-02T17:13:55Z
- **提交信息**: feat(moe): enable tile_size=256 for Rubin MoE autotuning (#4851)

## 📌 Description

`get_rubin_moe_valid_tactics` restricted the autotuner to
`tile_size=128`, citing illegal memory accesses at `tile_size=256` with
B-reuse and pointing at the equivalent restriction in
`get_blackwell_moe_valid_tactics`.

**That Blackwell restriction no longer exists.** It was the
gemm1(2CTA)/gemm2(1CTA) layout mismatch of #3067, fixed in #3171 by
parameterizing the gemm2 candidate list on `tile_size`.
`get_rubin_gemm2_valid_tactics` is already parameterized the same way,
so the Rubin path carries that fix too — the restriction was mirroring a
constraint that had since been lifted.

This iterates over `VALID_TILE_SIZES`, matching the Blackwell path.

The candidate lists are **unchanged**. The existing `mma_tiler_m ==
tile_size` and `cluster_shape_m * mma_tiler_m <= tile_size` constraints
already decide what is reachable at each tile size, and the 2CTA /
B-reuse entries were deliberately left in place for this — the note on
them read *"kept because they become reachable again once tile_size=256
is re-enabled."* Those notes, which described the entries as
unreachable, are corrected.

Net effect is a deletion: 16 insertions, 20 deletions, no new data
tables or special cases.

## 🔍 Related Issues

Follows #3067 / #3171, which fixed and then re-enabled the same
restriction on the Blackwell path.

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

Verified on an SM107 device by autotuning `cute_dsl_fused_moe_nvfp4`,
with the autotuner's per-tactic profiling traced at debug level:

- The tactic list grows from **4 to 8** entries, split `{128: 4, 256:
4}`.
- All 8 candidates profile on device and **none are skipped**, so every
newly reachable tactic compiles, launches and completes.
- A sweep of **10 shapes** — 1 to 4096 tokens, 8 to 128 experts, `top_k`
2 to 8, hidden/intermediate 1024 and 2048 — completes with **no illegal
memory access** (the process exits cleanly; an IMA is not catchable and
would abort it).
- Output matches the non-autotuned reference in every case, cosine
similarity **>= 0.999993**.

The routing-varying dimensions were chosen deliberately, since the
restriction described the IMAs as routing-dependent.

No new test file: `get_rubin_moe_valid_tactics` is only reachable on `cc
== (10, 7)` via `_get_arch_tactics()`, so a tile-256 assertion would
skip everywhere in CI today. The existing `TestTacticEnumeration`
invariants continue to pass.

## Reviewer Notes

**This is not a performance claim.** It removes a restriction that no
longer applies and lets the autotuner consider tactics it could not
previously reach; it asserts nothing about their speed. The autotuner
continues to select whichever candidate it measures as best.

An earlier revision of this PR added four tile-256 tactics as a
hand-written allowlist. That approach is dropped: those entries had
`cluster_shape_m * mma_tiler_m = 512 > tile_size = 256` and so were
**rejected by the generator's own validity rule** — they sat outside the
constraints the module asserts. Removing the stale gate reaches the
intended configurations through the existing rules instead.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added support for W4A8 quantization alongside W4A4 in the fused MoE
tuner.
* Added expanded Blackwell and Rubin tactic selection, including
256-sized tile options.
* Added validation and default tactic handling for W4A8 configurations.

* **Compatibility**
* Preserved access to the previous runner name with a deprecation
warning.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Vincent Tombari <Vinnie6167@users.noreply.github.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [feca244](https://github.com/flashinfer-ai/flashinfer/commit/feca244d81f2729605c3f0cd5aed0e33d9f06e3e)

- **作者**: Anerudhan Gopal
- **时间**: 2026-09-02T17:12:27Z
- **提交信息**: docs(moe): regenerate the Unified MoE activation matrix (unblocks CI on main) (#4903)

## 📌 Description


`tests/moe/test_unified_moe_activation_matrix.py::test_documented_activation_matrix_matches_runner_registry`
is failing on `main`, which blocks CI for **every open PR**:

```
AssertionError: docs/design_docs/flashinfer_moe_api.md is stale;
run: python scripts/generate_moe_activation_matrix.py --write
```

This is a **semantic merge conflict**, not a defect in any single PR.
#4805 added the generator, its check test, and a matrix block rendered
from `_BACKEND_RUNNERS` as it stood on that PR's base. Two changes
landed on `main` in between, and neither could have known to re-render
the block:

| Change | Effect on the matrix |
|---|---|
| #4793 (`f7d4b167`) | renamed `CuteDslRunner.backend_key`
`cute_dsl_nvfp4` → `cute_dsl` and added `QuantVariant.MXFP4` to its
supported variants |
| #4646 (`0cbace05`) | registered `CuTileBf16Runner` /
`CuTileNvfp4Runner` in `_BACKEND_RUNNERS` |

Each PR was green on its own base; the merged tree is what is stale.
Because the check compares the committed block against the live
registry, it has been red for everyone since #4805 merged.

## 🔍 Change

Only the generated block changes — this commit is the mechanical output
of the documented regeneration command:

```
python scripts/generate_moe_activation_matrix.py --write
```

- adds `cutile_bf16` (`BF16`) and `cutile_nvfp4` (`NVFP4`), both
`SwiGLU`, `ReLU2`
- replaces the two `cute_dsl_nvfp4` rows with three `cute_dsl` rows
(`MXFP4`, `NVFP4`, `W4A16`)

No source, test, or prose changes.

## 🧪 Testing

The authoritative check is
`test_documented_activation_matrix_matches_runner_registry`, which runs
in this PR's own CI.

## 🔗 Related

Surfaced while triaging CI on #4387, whose H100 job ran the full suite
with 221,273 passing and this as the sole failure.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Documentation**
* Updated the MoE activation matrix table to document MXFP4, NVFP4, and
W4A16 support across additional activation functions.
* Added documented BF16 and NVFP4 configuration entries for CuTile
implementations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [5b321fc](https://github.com/flashinfer-ai/flashinfer/commit/5b321fc4eb7aa249f36c13fd5ac3491914ed67b7)

- **作者**: Vincent
- **时间**: 2026-09-02T17:02:08Z
- **提交信息**: fix(gemm,moe): restore bmm_fp8 auto fallback and drop an over-strict SM107 tactic guard (#4853)

## 📌 Description

Port of #4645 to `main`. That PR was merged into `release-v0.6.18` only,
so both
defects are still present on `main` today — verified against `main`
before
opening: all eight lines this PR removes are still there.

Two Rubin (SM107) fixes, both originally measured on VR200.

### 1. Keep the experimental cute-dsl `bmm_fp8` runner last

`_heuristic_func_bmm_fp8` documents the intended ordering — *"preserve
order of
[cutlass, cublas, cudnn, cute-dsl] … cute-dsl is placed last as it's
still
experimental"* (still present on `main` at `gemm_base.py:7478-7479`) —
but
`fp8_gemm_sm100` built the runner list in the opposite order, appending
`cute-dsl_sm107` **first**.

The AutoTuner uses `runners[0]` as its no-profile fallback, so on SM107
every
**untuned** `backend="auto"` call went straight to the experimental CuTe
DSL
runner. For any shape the SM107 tactic space cannot serve (`m < 256` or
`n < 128`, since every `SM107_AUTOTUNE_CONFIGS` entry is 2-CTA with
`mma_tiler M=256`) `bmm_fp8` then raised

```
ValueError: No valid cute-dsl SM107 bmm_fp8 config for problem (...)
```

instead of falling back to cutlass/cublas/cudnn. Autotuned calls were
unaffected, since profiling walks the whole runner list.

### 2. Drop the "SM107 requires the Rubin tactic parameters" guard

Both MoE entry points rejected calls that supplied Blackwell-style
tactic
parameters (`mma_tiler_mn`) on an SM107 device. That guard assumed SM100
tactics
cannot run on Rubin — an assumption drawn from such calls failing with
`cudaErrorInvalidValue`. That failure has since been traced to the CuTe
DSL 4.8
cu12/cu13 runtime-selection bug, not to the tactics, so the premise no
longer
holds; the design comment in the finalize dispatcher says the SM100
kernel runs
on Rubin via the `sm_100f` family target.

The converse check (Rubin tactics on a non-Rubin device) is kept.

## 🧪 Tests

Validation below was performed on the `release-v0.6.18` version of this
change;
the diff ported here is identical.

**Fix 1 — A/B on VR200, same test path, one commit apart:**

| | passed | failed |
|---|---|---|
| `release-v0.6.18` | 1,750 | **9** |
| with this change | **1,759** | **0** |

The 9 were all `backend="auto"` cases in
`tests/gemm/test_unified_gemm_fuzz.py`
(`n=16`/`n=32` shapes plus `test_convention_conformance` at `m=128,
n=256`).

**Fix 2 — on GR100** with the cu13 runtime pinned and the guard absent,

`tests/moe/test_cute_dsl_mxfp8_mxfp4_grouped_gemm.py::TestMxfp8Mxfp4TwoStageMoe::test_gemm2_finalize_tile_n_variants`
passes **5/5**. With the guard, it contributes to 13 VR200 failures
across
`test_gemm2_finalize_tile_n_variants`,
`test_gemm1_quantize_then_gemm2_finalize`,
`test_wrapper_with_poisoned_moe_sort_buffers` and
`test_functional_and_wrapper_agree`.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit`.
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🔍 Related

* Original release-branch PR: #4645
* The `cudaErrorInvalidValue` failures referenced above are the CuTe DSL
4.8
cu12/cu13 support-runtime selection bug (`[cu13]` installs cu12 as well,
and
auto-discovery returns the cu12 DSO on `sm_107a`), worked around in CI
by
  pinning `CUTE_DSL_LIBS` to the cu13 runtime.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved FP8 grouped GEMM compatibility on SM107 devices when
Rubin-specific parameters are unavailable.
* Updated execution selection to prioritize established CUTLASS, cuBLAS,
and cuDNN paths before the SM107 specialized runner.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [c92227f](https://github.com/flashinfer-ai/flashinfer/commit/c92227fad382073503169fb53f1aee659462c327)

- **作者**: Hiki
- **时间**: 2026-09-02T14:32:29Z
- **提交信息**: feat(moe): add CuTe DSL SM90 BF16 MoE backend (#4878)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

Add a CuTe-DSL BF16/FP16 fused-MoE backend for SM90 (Hopper), exposed as
`cute_dsl_fused_moe_bf16` / `CuteDslBf16MoEWrapper`. It provides an
unquantized alternative to `cutlass_fused_moe` on Hopper using the
contiguous-grouped execution model: `moe_sort` (index maps only) → GEMM1
(cp.async gather + grouped WGMMA + fused SwiGLU epilogue) → GEMM2
(grouped WGMMA + fused router-scaled scatter-reduce finalize).

Design doc: `docs/design_docs/cute_dsl_moe_sm90.md`.

Highlights:
- Kernels (`flashinfer/fused_moe/cute_dsl/hopper/`): persistent
warp-specialized SM90 kernels. GEMM1 fuses the token permute into the A
gather (the permute is never materialized) and gates up/gate projections
in registers via a 32-column weight interleave. GEMM2 fuses the top-k
combine into a `cp.reduce.async.bulk` scatter (fused mode) or scatters
unscaled rows for a bitwise-reproducible fixed-order combine
(`use_fused_finalize=False`).
- CUDA-graph safe and PDL-enabled: static grids sized from `num_tokens`
only, device-side tile exit, no tensormap updates (expert index is the
TMA L-coordinate), event-based aux-stream memset overlap, PDL across the
three ops.
- Autotuning (`sm90_tuner.py`): a 6-field tactic (`tile_size,
gemm1_tile_n, gemm2_tile_n, gemm2_tile_k, gemm2_cluster_shape_mn,
gemm2_raster_along_m`) tuned through the FlashInfer AutoTuner with
balanced profiling inputs; the shape heuristic competes as an explicit
candidate, so tuned dispatch is never worse than the default. EP
sharding (`num_local_experts` / `local_expert_offset`) is supported.
- Benchmarks: `cute_dsl_bf16_moe` routine in
`benchmarks/flashinfer_benchmark.py` (+ `--autotune_cache` support for
tune-once/replay measurement).

Next steps:
- Extend the support surface, such as quantization, more activation
types, etc
- Optimize performance, especially for large intermediate_size.

## 🔍 Related Issues

<!-- Link any related issues here -->

[#3521](https://github.com/flashinfer-ai/flashinfer/issues/3521)

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

Added (all passing on H200, 78 tests):

- `tests/moe/test_cute_dsl_bf16_gather_grouped_gemm.py` — standalone
GEMM1 kernel tests (tile shapes, 2-warpgroup tiles, per-rank
geometries).
- `tests/moe/test_cute_dsl_bf16_grouped_gemm_finalize.py` — standalone
GEMM2 kernel tests: fused mode (bf16/fp16, tile-k 32/64, cluster (1,2),
M-major raster, poisoned padding rows, zero-scale routes) and
deterministic mode (expanded-order scatter).
- `tests/moe/test_cute_dsl_bf16_moe.py` — end-to-end: bf16/fp16 vs fp32
reference, tactic overrides, auto-selection, EP shards (including
all-routed-outside-shard), autotune profiling + cached-winner recall,
process-local compile reuse, deterministic-mode bitwise check, PDL
on/off equivalence, CUDA-graph capture/replay with fresh routing,
tiny/empty batches, fail-fast input validation.
- `tests/trace/…` — trace template + regenerated example JSON.

## Performance

### Kernel Performance

Measured on H200 against `cutlass_fused_moe` (`base` variant —
unquantized BF16) on identical tensors and routing. Setup:

- Each backend is autotuned once per suite with the winners stored to an
`--autotune_cache` file; all measured rounds replay the stored tactics
with autotune disabled, so between-round variance is execution-only.
- Each per-round value is the median of 50 CUPTI timings after 10 dry
runs, with a cold L2 before every timing. Each cell is the median of
three alternating backend-pair rounds (AB/BA/AB), reported only when the
between-round CV is at most 5% for both backends.
- Workloads: routed-expert geometries from the models' published
configs, TP in {1, 4}, unexpanded token counts T in {1, 256, 1024, 4096,
16384}.

Cells are the speedup over `cutlass_fused_moe` (values > 1 mean CuTe-DSL
is faster):

| model (h / I global / E / top_k) | tp -> I/rank | T=1 | 256 | 1024 |
4096 | 16384 |
|---|---|---|---|---|---|---|
| Qwen3-30B-A3B (2048/768/128/8) | 1 -> 768 | 1.38x | 1.02x | 1.02x |
1.27x | 1.31x |
| | 4 -> 192 | 1.82x | 1.24x | 1.34x | 1.75x | 1.90x |
| Qwen3-235B-A22B (4096/1536/128/8) | 1 -> 1536 | 1.10x | 1.00x | 0.88x
| 1.08x | 1.14x |
| | 4 -> 384 | 1.48x | 1.05x | 1.09x | 1.35x | 1.38x |
| Qwen3-Next-80B-A3B (2048/512/512/10) | 1 -> 512 | 1.70x | 0.98x |
1.03x | 1.17x | 1.48x |
| | 4 -> 128 | 2.30x | 1.17x | 1.26x | 1.73x | 1.82x |
| GLM-4.5-Air (4096/1408/128/8) | 1 -> 1408 | 1.14x | 1.01x | 0.89x |
1.04x | 1.13x |
| | 4 -> 352 | 1.48x | 1.09x | 1.07x | 1.11x | 1.11x |
| Kimi-K2 (7168/2048/384/8) | 1 -> 2048 | 1.08x | 1.00x | 1.03x | 1.02x
| 1.12x |
| | 4 -> 512 | 1.35x | 1.01x | 1.04x | 1.12x | 1.18x |
| DeepSeek-V3 (7168/2048/256/8) | 1 -> 2048 | 1.08x | 1.00x | 1.05x |
0.86x | 1.03x |
| | 4 -> 512 | 1.33x | 1.02x | 1.10x | 1.04x | 1.21x |
| Mixtral-8x7B (4096/14336/8/2) | 1 -> 14336 | 1.07x | 0.85x | 0.86x |
0.89x | 0.95x |
| | 4 -> 3584 | 1.18x | 0.90x | 1.07x | 1.07x | 1.05x |

All 70 cells pass the variance gate; their geo-mean speedup is
**1.16x**, and CuTe-DSL is faster in 59. The per-model geo-mean ranges
from **0.98x** (Mixtral-8x7B) to **1.41x** (Qwen3-Next-80B-A3B); the
advantage grows with TP (smaller per-rank I) and is largest at T=1
decode (up to 2.30x). Between-round CVs: CuTe-DSL median 0.12% / p95
2.45% / max 4.23%; baseline median 0.14% / p95 1.13% / max 4.09%.

### vLLM End-to-end performance

```
vllm bench throughput \
    --model Qwen/Qwen3-30B-A3B \
    --dataset-name random \
    --moe-backend triton/flashinfer_cutedsl \
    --num-warmups 128 -tp 1/2/4/8
```

| TP | Triton req/s | CuTe-DSL req/s | speedup |
|---|---:|---:|---:|
| 1 | 40.77 | 44.61 | **1.094x** |
| 2 | 64.62 | 69.56 | **1.076x** |
| 4 | 82.24 | 89.12 | **1.084x** |
| 8 | 88.05 | 95.52 | **1.085x** |

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->

- Shape constraints: `hidden % 64 == 0`, `2I % 64 == 0`, `I % 32 == 0`
  (design doc §1); violations fail fast with descriptive errors.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added experimental SM90/Hopper CuTe-DSL support for unquantized
BF16/FP16 fused MoE workloads.
* Exposed a fused MoE function and reusable wrapper with autotuning,
deterministic execution, CUDA Graph support, and expert-parallel
handling.
  * Added support for related benchmarking and trace workflows.

* **Documentation**
* Added design documentation covering the SM90 fused MoE implementation
and limitations.
  * Updated benchmarking guidance and MoE backend support details.

* **Tests**
* Added numerical and end-to-end coverage for fused operations,
execution modes, autotuning, and edge cases.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Haobin Guo <haobing@nvidia.com>

### [b2e36ef](https://github.com/flashinfer-ai/flashinfer/commit/b2e36efc06a320dc992368172d57b741d53753ce)

- **作者**: Bo Li
- **时间**: 2026-09-02T09:38:47Z
- **提交信息**: chore: update TRTLLM-Gen GEMM cubins (#4840)

## 📌 Description

Update the TRTLLM-Gen dense GEMM artifact pin to the newly published
multi-architecture package:

- artifact:
`7b1fc253cd6237950e76310873f4acf4d97a3904/gemm-b738138-25754e6/`
- manifest SHA-256:
`ca9d4f956f3fb63bff3066db88fa7ccf08b00f4b0b2751cc14ba72454fd01638`
- kernels: 186 cubins (`93 sm100f + 93 sm107a`)

This brings in the TRTLLM-Gen dense GEMM fixes from revision `b738138`
while retaining the existing GEMM config hash `25754e6`.

## 🔍 Related Issues

N/A

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] Commit-time pre-commit hooks passed.
- [ ] `pre-commit run --all-files` was not run for this pin-only change.

## 🧪 Tests

- [x] The public artifact and manifest URLs return HTTP 200.
- [x] The downloaded `checksums.txt` SHA-256 matches the new pin and
contains 201 entries.
- [ ] Full local test suite was not run.

## Reviewer Notes

The artifact was published from cubin-publishing main pipeline
`65421116`, job `418937481`; public publish job `418937489` completed
successfully.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
  * Updated the TensorRT-LLM generated GEMM artifact reference.
* Updated its verification checksum to ensure the correct artifact is
retrieved and validated.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: Bo Li <22713281+bobboli@users.noreply.github.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-09-03
**监控日期**: 2026-09-02
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4302
- **最后更新**: 2026-09-03T00:00:08Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Aryan Kumar

## AI分析总结

### 提交分析总结

**1. 主要更新类型**  
本次提交为**文档更新**，具体是向FastVideo的Cookbook文档中新增了关于“one-Spark FastH3”的运行时配置说明，并补充了设备数量（device-count）的配置行。

**2. 关键变更点与项目方向的关系**  
- 新增内容聚焦于**one-Spark FastH3**这一特定硬件/运行时环境下的使用指南，属于FastVideo多平台适配文档体系的一部分。  
- 项目README强调提供**快速上手（Quick Start）**和**Cookbook**等文档资源，本次提交直接丰富了Cookbook的实用场景覆盖，符合项目“降低用户使用门槛、扩展部署选项”的整体方向。

**3. 对项目的影响与潜在意义**  
- **提升易用性**：为使用one-Spark FastH3环境的用户提供了明确的配置参考，减少摸索成本。  
- **扩大硬件兼容性**：通过文档明确支持更多运行时，间接增强项目在不同算力平台上的可移植性，吸引更广泛的开发者社区。  
- **社区协作体现**：提交由外部贡献者（Aryan Kumar）共同完成，反映了项目开放协作的活跃度。

**4. 值得关注的技术点**  
- **设备数量（device-count）配置**：该参数在多卡或特定加速器环境下至关重要，文档明确列出该行，提示用户需根据实际硬件资源调整并行策略，避免资源浪费或分配错误。  
- **one-Spark FastH3**：可能是一种定制化或新兴的推理/训练加速方案，其与FastVideo的集成方式值得后续关注，或暗示项目对非主流硬件的适配趋势。

**5. 对项目发展的影响（结合README背景）**  
FastVideo定位为面向视频生成与处理的高效工具，其文档体系（含Cookbook）是吸引用户和开发者参与的关键入口。本次提交虽小，但通过补充特定硬件的配置指南，**完善了“从安装到部署”的闭环体验**，有助于在竞争激烈的视频生成领域巩固开发者生态。长期看，这类持续积累的文档优化将降低新用户的上手阻力，并可能吸引更多硬件厂商或社区成员贡献适配方案，推动项目向**多平台、多场景**的通用框架演进。整体而言，这是一次稳健且方向正确的增量更新。

## 详细提交记录

### [0bd19a9](https://github.com/hao-ai-lab/FastVideo/commit/0bd19a976b2e88ccd0d10b687b238bc1fa28c52a)

- **作者**: Aryan Kumar
- **时间**: 2026-09-02T17:05:59Z
- **提交信息**: [docs]: add one-Spark FastH3 cookbook runtime with a device-count row (#1811)

Co-authored-by: Aryan Kumar <aryan5v@users.noreply.github.com>

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-09-03
**监控日期**: 2026-09-02
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34430
- **最后更新**: 2026-09-02T23:15:48Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 3
- **主要提交者**: dg845, David Bertoin, Sayak Paul

## AI分析总结

# 提交分析总结

## 主要更新类型
本批提交以**性能优化**和**测试重构**为主，共4个提交，无新功能或文档更新。

## 关键变更点

1. **PRX注意力掩码优化**（2ff5e58）：避免在`PRXAttnProcessor2_0`中将注意力掩码从`[B,1,1,L_all]`预扩展为`[B,heads,L_img,L_all]`，改为传递未扩展掩码，由各后端自行广播。在PRX-1B训练规模下，扩展掩码每块占用1120 MiB，此改动显著降低显存峰值（8 GPU DDP场景从110.2降至75.2 GiB）并提升吞吐（446.1→427.5 ms/step）。

2. **Sana BF16测试修复**（e192749）：修复CI环境中Sana管线的BF16精度测试问题。

3. **组卸载测试拆分**（e9161bf）：将`GroupOffloadTesterMixin`中同时测试块级和叶级卸载的单一测试拆分为两个独立测试，并**将硬编码的8个组件卸载列表改为动态推导**——所有`nn.Module`组件默认卸载，除非配置明确排除。这修复了Ideogram4的`unconditional_transformer`和LTX2的`audio_vae`等组件因名称不在硬编码列表中而被静默遗漏的问题。

4. **SVD测试修复**（260a33d）：修复SVD管线的测试问题。

## 对项目的影响与潜在意义

- **显存优化**：PRX掩码改动对大规模训练意义重大，减少约35 GiB峰值显存意味着可在相同硬件上支持更大批次或更高分辨率，直接提升模型训练效率。
- **测试可靠性**：组卸载测试拆分使失败定位更精准，动态推导卸载组件消除了静默遗漏风险，为新增管线提供了更健壮的测试保障。
- **CI稳定性**：Sana和SVD测试修复减少CI误报，提升开发效率。

## 值得关注的技术点

- **后端掩码广播一致性**：提交验证了native/flex/xformers等后端均自行广播掩码，且未扩展掩码在输出和梯度上**位级一致**，fp32参考下相对误差保持6位有效数字不变——这是安全优化的关键证据。
- **测试设计模式**：从硬编码组件列表转向基于配置的推导逻辑，体现了测试代码随架构演进的自适应设计思路。

## 与项目整体方向的关系

diffusers作为多后端、多模型的扩散工具库，本批提交体现了两个核心方向：**大规模训练效率优化**（通过减少冗余内存操作）和**测试基础设施健壮性**（通过更细粒度和自适应的测试设计）。这些改进直接服务于库在专业级训练场景中的可用性，同时降低维护成本，与项目“提供灵活高效扩散模型工具”的定位一致。

## 详细提交记录

### [2ff5e58](https://github.com/huggingface/diffusers/commit/2ff5e5877f743b799cc389d7b60a054ce3b9ae50)

- **作者**: David Bertoin
- **时间**: 2026-09-02T23:15:32Z
- **提交信息**: Don't materialise the PRX attention mask (#14677)

`PRXAttnProcessor2_0` builds the joint [text | image] mask and then expands it
to the full `[B, heads, L_img, L_all]` before handing it to attention. Every
backend broadcasts a mask itself, so the expansion only costs bandwidth:

* `native` / `_native_*`: torch SDPA broadcasts `attn_mask` natively
* `flex`: `_native_flex_attention` does `attn_mask.expand(batch_size,
  num_heads, seq_len_q, seq_len_kv)` on a 4-D mask before building the block mask
* `xformers`: same, `attn_mask.expand(...)` for a 4-D mask
* `sage` / `aiter` / `_native_npu`: reject `attn_mask` outright

At PRX-1B's training shape (batch 32, 1024x1024, patch 32 -> 1024 image + 256
text tokens, 28 heads) the expanded mask is 1120 MiB per block, read once per
block per forward, for 16 blocks.

Passing the unexpanded `[B, 1, 1, L_all]` is bitwise identical -- verified with
`torch.equal` on both the block output and the full gradient vector, and against
an fp32 unfused-MATH reference the relative error is unchanged to 6 significant
figures.

Measured on an H200, PRX-1B, batch 32 @ 1024px, bf16 autocast, 5 warmup / 20
timed steps (fake tensors: no dataloader, no text encoder, no loss terms), with
`set_attention_backend("_native_cudnn")`:

    8 GPU DDP, compiled   446.1 -> 427.5 ms/step   peak 110.2 -> 75.2 GiB
    1 GPU, compiled       383.8 -> 373.8 ms/step   peak  65.6 -> 63.4 GiB
    1 GPU, eager          702.3 -> 649.4 ms/step   peak 132.7 -> 97.7 GiB

On the default `native` backend the same change is 809.1 -> 762.1 ms/step eager.

### [e192749](https://github.com/huggingface/diffusers/commit/e19274980c52d864f0a14971309eefe1fa72aa1d)

- **作者**: Sayak Paul
- **时间**: 2026-09-02T08:28:04Z
- **提交信息**: [tests] fix sana bf16 tests on ci. (#14688)

* fix sana bf16 tests on ci.

* Update tests/pipelines/sana/test_sana.py

Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

---------

Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

### [e9161bf](https://github.com/huggingface/diffusers/commit/e9161bfc7da8eb79fe8628881f3aeca4b3fb1b57)

- **作者**: dg845
- **时间**: 2026-09-02T07:57:20Z
- **提交信息**: [tests] Split Pipeline Group Offloading Block-Level and Leaf-Level Tests (#14635)

* tests: split block/leaf group offloading and derive the offloaded components

`GroupOffloadTesterMixin.test_group_offloading_inference` ran both offload
levels in one test body, so a pipeline that failed at one level had to skip
both. Split it into `test_group_offloading_inference_block_level` and
`test_group_offloading_inference_leaf_level`, sharing the helpers the test
body used to define inline, and compare against the class-scoped
`base_pipe_output` rather than rebuilding a baseline per level.

The set of components to offload was a hardcoded list of eight names, so a
pipeline with a component under any other name had it silently left on CPU
for the forward pass to trip over. Derive the set instead: every `nn.Module`
component is offloaded unless the config lists it in
`group_offloading_leaf_level_exclude_modules`, the new
`group_offloading_exclude_modules`, or `group_offloading_onload_component_names`.
A name in either exclusion list that matches no component on the pipeline
fails as the typo it is.

Ideogram4's `unconditional_transformer` was one of the silently dropped
components, which is why its group offload test was skipped; it now needs no
declaration at all, and `text_encoder` picks up block-level coverage it never
had. LTX2's skip goes the same way, with `audio_vae` declared alongside the
other VAEs the tests keep on the accelerator.

Co-Authored-By: Claude Opus 5 (1M context) <noreply@anthropic.com>

* style: fix `create_pipe` indentation in the group offload tester

The method body was indented one level too deep, which `ruff format` rewrites.

Co-Authored-By: Claude Opus 5 (1M context) <noreply@anthropic.com>

* tests: give group offloading one exclusion list per level

`group_offloading_onload_component_names` named an implementation detail —
components the tests keep resident — and justified itself with a mechanism
that cannot occur: lazy prefetch mis-tracing a tiled VAE decode needs
`use_stream=True`, which no test on this mixin sets, and most of the
pipelines it covers never enable tiling either.

What it actually encodes is a level-specific incapability, the mirror of
`group_offloading_leaf_level_exclude_modules`. Leaf-level offloading onloads
each leaf on its own `forward`, so it breaks on compute that reads a leaf's
`.weight` directly. Block-level onloads a group when the group's leader runs
its `forward`, so it breaks on compute that re-enters submodules without
going through that leader — which is what a VAE decode path does. Rename it
to `group_offloading_block_level_exclude_modules` and scope it to the level
it describes. `group_offloading_exclude_modules` is then redundant, since a
component that fails at both levels goes in both lists, and it never had a
user. `vqvae` leaves the default: no pipeline in the new harness has one.

Measured across the suite, offloading the `vae` at block level breaks 28 of
86 test classes, while all 86 offload it at leaf level with no failures --
coverage the component-scoped tests were skipping and the pipeline-level
test has always had. Sweep before and after: the same 9 pre-existing
failures, 782 -> 810 passing.

Co-Authored-By: Claude Opus 5 (1M context) <noreply@anthropic.com>

* Move group offloading changes to shared LTX-2 test mixins

* tests: cover the group offloading stream prefetch path

`use_stream=True` is the only way into `LazyPrefetchGroupOffloadingHook`,
which traces the group execution order on the first forward pass, wires each
group to its successor and flips `non_blocking` for the passes after. Nothing
in the pipeline suite reached that code, which is how a stale comment about
streams mis-tracing a tiled VAE decode survived unexamined for so long.

Add `test_group_offloading_inference_block_level_streaming` and
`..._leaf_level_streaming` alongside the synchronous pair, as separate methods
rather than a parametrized test so a pipeline can skip one level without
losing the other. Both route through `_run_group_offload_inference`, so they
compare against the same `base_pipe_output` and honour the same per-level
exclusion lists.

`apply_group_offloading` raises rather than degrading when there is nowhere to
put a stream, and `@require_torch_accelerator` still passes on MPS, so the two
tests also check for CUDA or XPU before running.

Guard against the flag quietly ceasing to have an effect: after enabling
offloading with `use_stream=True`, assert at least one group across the
pipeline actually carries a stream. The count is pipeline-wide because a
component with no `ModuleList`/`Sequential` children has nothing to prefetch
and legitimately streams nothing, and it asserts rather than skips because a
regression that drops `use_stream` would zero every count and a skip would
turn the whole streaming suite green by omission.

Sweep over `tests/pipelines -k group_offloading`: 31 failed, 1145 passed,
identical to the run without these tests. All 13 streaming failures have a
non-streaming twin that fails the same way, so the prefetch path adds no
failure of its own.

Co-Authored-By: Claude Opus 5 (1M context) <noreply@anthropic.com>

* tests: port the group offload overrides orphaned by the level split

Splitting `test_group_offloading_inference` into a block-level and a
leaf-level test removed the name six other test files override, so their
markers guarded a method the mixin no longer defines while the real tests ran
unprotected. The `xfail(strict=True)` ones hid it: `super()` raised
`AttributeError`, which counts as the expected failure, so they reported green
while testing nothing.

Rechecking each reason rather than renaming mechanically, three of the six
turned out to describe behaviour that no longer exists:

`LTX2DFRPipelineTesterConfig` subclasses `BasePipelineTesterConfig` rather
than `LTX2BaseTesterConfig`, so the family's `audio_vae` block-level exclusion
never reached it and its audio VAE was being offloaded. It needs the
declaration, not a skip, and its group offload tests now pass.

AudioLDM2 and Motif Video only fail at block level. `get_text_features()` and
the vision tower bypass the `forward` that block-level offloading gates the
group on, while leaf level onloads each leaf on its own `forward` and passes,
so the skip and the xfail are scoped to block level and the leaf-level tests
now run.

The Kandinsky prior xfails stay at both levels but their reason was describing
the hardcoded component list this branch removed. The actual cause is that the
pipeline calls `PriorTransformer.post_process_latents()` after the denoising
loop, reading `clip_mean` / `clip_std` that group offloading onloads only for
the duration of `forward`.

Also drop the class-count measurement from the block-level exclusion comment:
it was already stale one merge later. The mechanism it was evidence for —
`vae.decode()` never running `vae.forward()` — is the durable part.

Sweep over `tests/pipelines -k group_offloading`: 31 failed -> 13, all of them
failing identically on `main`, except `kolors`'s pipeline-level test, which
fails in isolation on `main` too and only passes there because of the test
order the split changed.

Co-Authored-By: Claude Opus 5 (1M context) <noreply@anthropic.com>

* Clarify the Ideogram 4 block-level group offloading module exclusion comment

* tests: parametrize `use_stream` instead of splitting the streaming tests

The streaming tests were separate methods so a pipeline could skip or xfail
them independently of their synchronous twins. Nothing has ever needed that:
across three full sweeps every streaming failure had a synchronous twin at the
same level and vice versa, and none of the sixteen downstream overrides marked
a streaming variant differently from its twin. The two *levels* do get scoped
apart — AudioLDM2 and Motif Video are block-level only — so those keep their
own methods.

Fold `use_stream` into a parameter on each level's test. Four mixin tests
become two and sixteen override methods become eight, with the same coverage:
a full sweep of the parametrized and the separate-method versions on the same
tree gives 15 failed, 1263 passed, 152 skipped, 22 xfailed, 1 xpassed on both,
with identical failure sets once `[stream]` and the `_streaming` suffix are
normalised.

Marks do not carry through a subclass override, so an override that forgets to
re-declare the parametrize collapses to one un-parametrized test that errors on
the missing argument — which an `xfail` then reports as green, the same failure
mode the orphaned overrides had. `_USE_STREAM` carries a note saying so, and the
six overrides re-declare it.

Co-Authored-By: Claude Opus 5 (1M context) <noreply@anthropic.com>

* tests: point the PNDM marker comment at the split group offload tests

`test_group_offloading_inference` no longer exists — it became one test per
offload level — so the comment listing which tests share the class-level xfail
named a test that is not there, and undercounted them by one.

Co-Authored-By: Claude Opus 5 (1M context) <noreply@anthropic.com>

* docs: record the group offload streaming parameter in the testing guide

The shared memory mixin now runs each offload level with and without
`use_stream`, which is the only path that reaches group offloading's lazy
prefetch. Say so next to the exclusion-list guidance, along with the reason it
is a parameter rather than a separate test, and the requirement that a subclass
overriding either test re-declare the `parametrize` — marks do not carry
through an override, and forgetting leaves a test that errors on the missing
argument and is reported as green by an `xfail`.

Co-Authored-By: Claude Opus 5 (1M context) <noreply@anthropic.com>

* tests: inline the single-caller group offload helpers

`_split_group_offload_components` and `_count_streamed_groups` each had one
caller, so per `code_style.md` they read better at the call site. The reasons
they existed survive as comments: that a component is offloaded unless the
level's list names it, and that several submodules share one `ModuleGroup` so
the stream count has to dedupe on group identity.

Co-Authored-By: Claude Opus 5 (1M context) <noreply@anthropic.com>

* docs: condense the group offload guidance to one bullet

The three group offload bullets in the testing guide had grown to explain
the hook mechanism at a level of detail that answers a reviewer's questions
rather than telling a test author what to write. Collapse them into one
bullet keeping the parts that change what a PR does: which remedy to reach
for, which exclusion list matches which hazard, that an unmatched name fails
as a typo, and that an override must re-declare the `use_stream` parametrize.

The worked examples below the bullet already carry the concrete diagnosis,
and the parametrize trap is explained in full at the code site.

Co-Authored-By: Claude Opus 5 (1M context) <noreply@anthropic.com>

* Explicitly declares group offloading leaf level excluded components for LTX-2

* Simplify comment regarding _USE_STREAM in GroupOffloadTesterMixin

---------

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

### [260a33d](https://github.com/huggingface/diffusers/commit/260a33d7973ea6440c7531f2cd317a96883e7e2d)

- **作者**: Sayak Paul
- **时间**: 2026-09-02T07:24:02Z
- **提交信息**: [tests] fix SVD tests (#14687)

* fix SVD tests

* make comment less confusing

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-09-03
**监控日期**: 2026-09-02
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 432
- **最后更新**: 2026-08-31T08:28:31Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-09-03
**监控日期**: 2026-09-02
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13039
- **最后更新**: 2026-09-02T11:08:24Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-09-03
**监控日期**: 2026-09-02
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 33522
- **最后更新**: 2026-09-03T00:16:31Z

## 提交统计

- **昨日提交总数**: 28
- **提交者数量**: 16
- **主要提交者**: YC Yen-Ching Tseng, paulzhang-tm, cctry

## AI分析总结

# SGLang 昨日提交分析报告

## 一、主要更新类型

本次提交涵盖**性能优化**（约40%）、**Bug修复**（约25%）、**功能新增**（约20%）、**CI/工程改进**（约15%）及少量**文档更新**。核心聚焦于注意力机制、推测解码和硬件适配三大方向。

## 二、关键变更点与项目方向

**1. SWA（Sliding Window Attention）统一化重构**（5ddca68、5a1275a、d9848b9、18d5ffb）
这是本批最核心的改动，将分散的SWA谓词收敛、统一读取流构建、按batch size动态规划读取表网格，并修复非owner节点的v2p表尺寸问题。这一系列重构显著简化了SWA的页表管理逻辑，与SGLang追求的高效分页注意力架构高度一致。

**2. 推测解码（EAGLE）体系完善**（3fa6b86、3c9cea8、19c30df）
发布多层EAGLE共享读取事件、裁剪draft-extend logits至选定行、支持DeepSeek-V4的DeepGEMM paged-MQA索引器与FP4 MoE。这些改动直接增强SGLang在推测解码场景下的吞吐能力，是其核心性能优势的重要支撑。

**3. 分页分配器优化**（c05f8ae、19c7679）
优化free-list释放流程，并实现`page_size == 1`时`free_swa`的无同步操作，减少内存管理开销。

**4. 硬件适配扩展**（f8cbf00、9c70d22、4bc3411）
支持AMD FP4 indexer、GLM-5.2 NVFP4 B200/B300、重新启用GB300任务，体现SGLang对多硬件平台（尤其AMD和最新NVIDIA架构）的持续投入。

**5. Diffusion模型支持**（f6aed6e、f586654、4b32948、fe3d4b9、9175590）
新增FastH3（4步VSA蒸馏MiniMax-H3）支持、cube稀疏注意力后端，并重构为按能力显式声明注意力后端。SGLang正从纯LLM推理引擎向多模态生成框架演进。

**6. 分布式与流水线并行修复**（718bd39、862a909、3a855b0）
修复DP注意力decode→extend前缀偏移、PP动态chunk profiling锁、disagg解码预分配轮询问题，提升分布式推理稳定性。

**7. CI与工程基建**（4bc3411、2d799c2、ebfd8c6、99b9109）
从PyPI安装评测依赖、git clone认证重试、ROCm 7.0定期测试，降低外部依赖风险并提升测试覆盖。

## 三、项目影响与潜在意义

- **SWA统一化**是架构级简化，将降低后续维护成本并提升长上下文场景的推理效率
- **EAGLE多层支持**与**DeepSeek-V4适配**表明SGLang正紧跟前沿模型架构，巩固其在高性能推理领域的领先地位
- **Diffusion能力扩展**使SGLang从纯文本生成走向多模态，拓宽应用边界
- **硬件适配**（AMD、GB300）增强跨平台竞争力

## 四、值得关注的技术点

- SWA页表按id空间而非物理页框尺寸分配，避免潜在越界
- CUDA graph去重签名基于kernel函数身份，防止错误复用
- 原生MoE对非连续top-k ID的处理修复
- 分页分配器tombstone scatter融合，减少内存碎片

## 五、对项目发展的影响

SGLang正沿三条主线演进：**架构精简**（SWA统一化）、**前沿模型快速适配**（DeepSeek-V4、GLM-5.2、MiniMax-H3）和**多模态扩展**（Diffusion）。大量提交由AI辅助生成（Claude参与），反映项目采用AI协作开发模式。整体来看，SGLang在保持LLM推理性能领先的同时，正积极构建覆盖更多模型类型和硬件平台的全方位推理基础设施，其工程化水平和高性能优化深度持续提升。

## 详细提交记录

### [5ddca68](https://github.com/sgl-project/sglang/commit/5ddca6819ebab6896b315967915161c1cb6b85e6)

- **作者**: Cheng Wan
- **时间**: 2026-09-02T23:56:18Z
- **提交信息**: Fix unified SWA: size a non-owner's v2p by the id space it must address (#37560)

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [5a1275a](https://github.com/sgl-project/sglang/commit/5a1275a5195104b824e6bd0df71678cfe25a2aa1)

- **作者**: Cheng Wan
- **时间**: 2026-09-02T23:55:46Z
- **提交信息**: Converge the two SWA predicates, and stop conditioning the capture sink on the pool (#37550)

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [d9848b9](https://github.com/sgl-project/sglang/commit/d9848b9ecdf7cab752eb1d1257de09f103c92582)

- **作者**: Cheng Wan
- **时间**: 2026-09-02T23:55:16Z
- **提交信息**: Build the unified read stream directly, without the page-table rectangle (#37512)

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [18d5ffb](https://github.com/sgl-project/sglang/commit/18d5ffb42a5e0fdf1e4af6fa12cb238bbe9b8c2a)

- **作者**: Cheng Wan
- **时间**: 2026-09-02T23:54:26Z
- **提交信息**: Size the unified read-table grid from bs, and fuse the allocator's tombstone scatters (#37511)

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [c05f8ae](https://github.com/sgl-project/sglang/commit/c05f8ae8302b0c5572707be0897e5e02d812f2cd)

- **作者**: wangwenmingaa
- **时间**: 2026-09-02T23:51:37Z
- **提交信息**: [PD] Optimize paged allocator free-list release (#37146)

Co-authored-by: wangwenming.41 <wangwenming.41@jd.com>
Co-authored-by: hnyls2002 <lsyincs@gmail.com>
Co-authored-by: Liangsheng Yin <hnyls2002@gmail.com>

### [4bc3411](https://github.com/sgl-project/sglang/commit/4bc34117f1d486c55f33170a62a1194704474b98)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-02T23:23:10Z
- **提交信息**: [CI] Install lmms-eval from PyPI, drop human-eval install, add clone token fallback (#37672)

### [a6da3a4](https://github.com/sgl-project/sglang/commit/a6da3a4922b46277dfab81c4378ada0e70368f55)

- **作者**: Alison Shao
- **时间**: 2026-09-02T23:15:40Z
- **提交信息**: [CI] Re-enable GB300 jobs (#37522)

### [718bd39](https://github.com/sgl-project/sglang/commit/718bd39fe08b42e0095daa571510e47c40c588d2)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-09-02T23:14:16Z
- **提交信息**: [Fix] DP attention: correct the decode->extend prefix off-by-one (#37505)

### [3fa6b86](https://github.com/sgl-project/sglang/commit/3fa6b865040d8008bc88b2666594da1892fbd272)

- **作者**: paulzhang-tm
- **时间**: 2026-09-02T22:57:50Z
- **提交信息**: [Spec] Publish the final multi-layer EAGLE shared-read event (#36752)

Co-authored-by: Qiaolin-Yu <liin1211@outlook.com>

### [19c30df](https://github.com/sgl-project/sglang/commit/19c30dff56204d3c259410ae8819c8309e3985f5)

- **作者**: eeecho
- **时间**: 2026-09-02T22:49:59Z
- **提交信息**: [SM120] DeepSeek-V4: DeepGEMM paged-MQA indexer +FP4 MoE+ page-split  (#29927)

Co-authored-by: Baizhou Zhang <sobereddiezhang@gmail.com>

### [982aa8a](https://github.com/sgl-project/sglang/commit/982aa8acfcfd0b6cb441f8d39d06c477ea4244f0)

- **作者**: YAMY
- **时间**: 2026-09-02T22:19:40Z
- **提交信息**: [Bugfix] Load Qwen3.5 MTP embedding under PP (#37471)

### [3c9cea8](https://github.com/sgl-project/sglang/commit/3c9cea8f100c69f39d528cca0a4e5658db9cd1c6)

- **作者**: YAMY
- **时间**: 2026-09-02T22:10:08Z
- **提交信息**: [EAGLE] Prune draft-extend logits to selected rows (#35546)

### [fe45af1](https://github.com/sgl-project/sglang/commit/fe45af1e6f04ac46d3a1a433cbb2049b12b023b9)

- **作者**: YAMY
- **时间**: 2026-09-02T22:07:49Z
- **提交信息**: perf(gdn): select ReplaySSM verify loop unrolling by shape (#36970)

### [9c70d22](https://github.com/sgl-project/sglang/commit/9c70d22721d3bb29541bb489f495a38aac4d612d)

- **作者**: Faradawn Yang
- **时间**: 2026-09-02T21:39:09Z
- **提交信息**: Update GLM-5.2 NVFP4 B200/B300 for AgentX HiCache (#35368)

### [3a855b0](https://github.com/sgl-project/sglang/commit/3a855b050aaa18edc45b44bd0d7c637e40a243c6)

- **作者**: cctry
- **时间**: 2026-09-02T21:26:40Z
- **提交信息**: fix(disagg): poll receivers during decode preallocation (#37483)

### [ad6e830](https://github.com/sgl-project/sglang/commit/ad6e8308582ab2dc7505e8e187c27996ab6ad1d1)

- **作者**: cctry
- **时间**: 2026-09-02T21:24:31Z
- **提交信息**: [Bugfix] Key CUDA graph dedup signatures on kernel function identity (#37657)

### [19c7679](https://github.com/sgl-project/sglang/commit/19c7679e9e9c6f36e0ede15c0900ab3c63fafdd5)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-02T21:18:22Z
- **提交信息**: [mem_cache] Make `free_swa` sync-free on `page_size == 1` (#36723)

### [acea430](https://github.com/sgl-project/sglang/commit/acea43079fa569d67172bf4754380bff2c8190be)

- **作者**: Joe
- **时间**: 2026-09-02T21:16:19Z
- **提交信息**: Fix native MoE handling of noncontiguous top-k IDs (#36407)

Co-authored-by: BBuf <1182563586@qq.com>

### [2d799c2](https://github.com/sgl-project/sglang/commit/2d799c28f450a2d83a5bedf2c07699cd32fb3c7a)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-02T20:21:26Z
- **提交信息**: [CI] Authenticate and retry git clones in install scripts (#37647)

### [f8cbf00](https://github.com/sgl-project/sglang/commit/f8cbf000f4a5bfd86d3fb7c1e2d6c8fb12339d0e)

- **作者**: Xinyi Song
- **时间**: 2026-09-02T16:45:08Z
- **提交信息**: [AMD] Enable FP4 indexer for Deepseek V4 (#37353)

Co-authored-by: 1am9trash <1am9trash@gmail.com>
Co-authored-by: AMD-yanfeiwang <256076023+AMD-yanfeiwang@users.noreply.github.com>
Co-authored-by: Thomas Wang <thomawan@amd.com>

### [f6aed6e](https://github.com/sgl-project/sglang/commit/f6aed6ec5322c8c1091bbbc8531cf3cd0c7e0f12)

- **作者**: Mick
- **时间**: 2026-09-02T15:42:54Z
- **提交信息**: [diffusion] doc: rewrite stale diffusion compatibility matrix (#36987)

### [f586654](https://github.com/sgl-project/sglang/commit/f5866545186f27a8a01c1a083e8c32809b5506f3)

- **作者**: Kevin Mi
- **时间**: 2026-09-02T13:39:54Z
- **提交信息**: [diffusion] feat: support FastH3 (4-step VSA-distilled MiniMax-H3) with a VSA-H3 attention backend (#37480)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [99b9109](https://github.com/sgl-project/sglang/commit/99b910955377375a1385122680e0daefcf706f79)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-09-02T09:51:16Z
- **提交信息**: [AMD] Run ROCm 7.0 shadow tests every two days- #37582 (#37586)

Co-authored-by: Chen <bingxche@amd.com>

### [862a909](https://github.com/sgl-project/sglang/commit/862a909a085f68f2e87a14e5bb7f8c930612c955)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-02T09:09:01Z
- **提交信息**: [Fix] Lock PP dynamic-chunk profiling requests before releasing through the tree cache (#37509)

### [ebfd8c6](https://github.com/sgl-project/sglang/commit/ebfd8c60e53e77d67fc79f171d230dd521d9ff73)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-02T08:45:25Z
- **提交信息**: [CI] Install sgl-eval from PyPI through the test extra (#37504)

### [fe3d4b9](https://github.com/sgl-project/sglang/commit/fe3d4b9bbbff744d056dda122ea9157c2932a2bd)

- **作者**: Shuwen Wang
- **时间**: 2026-09-02T07:58:31Z
- **提交信息**: fix: restore missing get_component_forced_attn_backend import in minimax_h3 (#37566)

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [4b32948](https://github.com/sgl-project/sglang/commit/4b329482e8a508ff741c6313a3d7dd6f6c99e322)

- **作者**: Mick
- **时间**: 2026-09-02T07:21:33Z
- **提交信息**: [diffusion] feat: support cube sparse attention for minimax h3 (#34893)

Co-authored-by: zhenaozhenfu <zhenaozhenfu@minimaxi.com>
Co-authored-by: Reynor <reynor@minimaxi.com>

### [9175590](https://github.com/sgl-project/sglang/commit/9175590aa06186379d9cda555d1a1a31eab889a7)

- **作者**: Mick
- **时间**: 2026-09-02T07:17:57Z
- **提交信息**: [diffusion] refactor: admit explicit attention backends by capability (#37441)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-09-03
**监控日期**: 2026-09-02
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1267
- **最后更新**: 2026-09-02T06:58:54Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-09-03
**监控日期**: 2026-09-02
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 90803
- **最后更新**: 2026-09-02T23:53:20Z

## 提交统计

- **昨日提交总数**: 48
- **提交者数量**: 33
- **主要提交者**: Hung Hoang (黄兴）, Huanxing, Simon Danielsson

## AI分析总结

# vLLM 仓库提交分析

## 主要更新类型

本批次48个提交涵盖：Bug修复（约15个）、CI优化（约12个）、性能优化（约6个）、新模型支持（2个）、功能新增（约5个）、文档与构建改进（约4个）。Bug修复和CI优化占据主导，体现项目在稳定性和工程效率上的持续投入。

## 关键变更点

**性能优化方面**，Rust前端合并解码块减少引擎更新开销；DeepSeek V3 GEMM内核针对内连续和行跨步张量实现12%-81%性能提升；XPU平台新增融合GemmaRMSNorm路径和批量不变内核注册。

**新模型支持**包括DeepSeek-V4-Flash-Vision-Exp多模态模型和GLM-OCR的MTP权重加载修复，延续vLLM快速适配前沿模型的策略。

**KV卸载与跨批次安全**是重点修复领域，涉及缓存哈希按模态隔离、异步查找结果过期处理、磁盘后端跨批次缓冲区竞争等问题，反映分布式推理场景下数据一致性的挑战。

**CI体系**大量优化包括AMD/ROCm测试超时延长、CPU任务分片、DockerHub清理规则修正、多节点检测修复等，显示项目对多硬件平台覆盖的重视。

## 项目影响与意义

vLLM作为“人人可用的快速廉价LLM服务”框架，本批次提交强化了多硬件适配（XPU、ROCm、Ascend NPU）、多模态模型支持和分布式推理稳定性。Rust前端的持续优化表明项目正推进高性能工程化路线。新增Triton内核编写技能暴露给Claude代理，体现AI辅助开发在项目中的应用。

## 值得关注的技术点

- Rust前端合并解码块策略，直接降低引擎更新频率
- FlashKDA版本升级修复Kimi-K3数值稳定性问题
- 在线量化配置支持用户模式定制，提升部署灵活性
- NIXL索引使用int32数组避免中间转换开销
- CUDA图分段不可用时的显式报错机制
- chat template回退机制纳入package_data，改善分发完整性

## 对项目发展的影响

本批次提交体现了vLLM在三个方向的持续演进：**性能极致优化**（Rust前端、GEMM内核调优）、**硬件生态扩展**（XPU、ROCm、NPU的持续适配）、**稳定性加固**（KV卸载、跨批次并发、CI可靠性）。多模态模型支持（DeepSeek-V4-Vision、Ernie4.5-VL）和AI代理辅助开发（Triton技能暴露）则展示了项目拥抱前沿技术趋势的姿态。整体来看，vLLM正从单一GPU推理框架向多硬件、多模态、企业级稳定的综合LLM服务平台演进。

## 详细提交记录

### [ad127d9](https://github.com/vllm-project/vllm/commit/ad127d9a0fb16c92de563e674e3737463e7f8688)

- **作者**: Bugen Zhao
- **时间**: 2026-09-02T22:44:23Z
- **提交信息**: [Perf][Rust Frontend] Coalesce decoded chunks per engine update (#55012)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>

### [443febe](https://github.com/vllm-project/vllm/commit/443febe723f62381cda46a9d4f989b8e74a8a857)

- **作者**: Woosuk Kwon
- **时间**: 2026-09-02T22:36:12Z
- **提交信息**: [Agents] Expose Triton kernel-writing skill to Claude (#55028)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [cf3263d](https://github.com/vllm-project/vllm/commit/cf3263d571dfa21e82787356b9506cbf80b68ad6)

- **作者**: Woosuk Kwon
- **时间**: 2026-09-02T22:29:16Z
- **提交信息**: [Agents] Add Triton kernel-writing skill (#55019)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [6c6376a](https://github.com/vllm-project/vllm/commit/6c6376a09e89acfbe62954246739f0dd52b892c7)

- **作者**: Kevin H. Luu
- **时间**: 2026-09-02T22:18:46Z
- **提交信息**: [CI] Remove deleted nvidia/Nemotron-3-Nano-Omni-30B-A3B-Reasoning-BF16 and its arch aliases (#55026)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Kimi Code <noreply@moonshot.cn>

### [a0d3e5c](https://github.com/vllm-project/vllm/commit/a0d3e5c16e96b62ec5c7f741952cfddc99534faf)

- **作者**: Huanxing
- **时间**: 2026-09-02T22:11:20Z
- **提交信息**: [XPU] Add fused GemmaRMSNorm path for eager execution (#53678)

Signed-off-by: Huanxing <huanxing.shen@intel.com>
Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [963054e](https://github.com/vllm-project/vllm/commit/963054ed580824e0f3901e3a53f7994349434d13)

- **作者**: Kevin H. Luu
- **时间**: 2026-09-02T22:09:18Z
- **提交信息**: [CI] Exclude nightly-dev tags from nightly DockerHub cleanup (#55023)

Signed-off-by: khluu <khluu000@gmail.com>

### [e3e1241](https://github.com/vllm-project/vllm/commit/e3e1241003473e33197e9b5d73e8f091fc75aad1)

- **作者**: Micah Williamson
- **时间**: 2026-09-02T21:11:46Z
- **提交信息**: [ROCm][CI] Extend Multimodal Processor Shard timeout on AMD CI (#55011)

Signed-off-by: Micah Williamson <micah.williamson@amd.com>

### [60857ba](https://github.com/vllm-project/vllm/commit/60857baa53a743913d4e919f12b5fd8d608ded86)

- **作者**: Reid
- **时间**: 2026-09-02T20:43:57Z
- **提交信息**: [Bugfix][Rust Frontend][Renderer] Align DeepSeek V4 historical developer message handling (#54854)

Signed-off-by: reidliu41 <reid201711@gmail.com>

### [a56654d](https://github.com/vllm-project/vllm/commit/a56654d6de060495ff2db3b1d9ff0b187084d1a9)

- **作者**: Wentao Ye
- **时间**: 2026-09-02T19:22:40Z
- **提交信息**: [K3 Perf] Enable DSV3 GEMM for inner-contiguous and row-strided tensors, 12%~81% kernel performance improvement (#54565)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [0e3ac49](https://github.com/vllm-project/vllm/commit/0e3ac4907d21e77cb4781338c49fef17bfea8f2b)

- **作者**: Sheral Kumar
- **时间**: 2026-09-02T18:53:07Z
- **提交信息**: [ROCm][CI] Fix false multi-node detection on native CI (#54989)

Signed-off-by: Sheral Kumar <shekumar@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [1945a94](https://github.com/vllm-project/vllm/commit/1945a9457563e28a32baa03dca620ed52bd18d10)

- **作者**: Luke Alonso
- **时间**: 2026-09-02T18:46:08Z
- **提交信息**: [Bugfix][Tests] Stabilize B12X linear kernel checks (#54996)

Signed-off-by: Luke Alonso <lalonso@gmail.com>

### [9b38e3a](https://github.com/vllm-project/vllm/commit/9b38e3ad53967856df6dd18dbaf91f8f5e3a5f32)

- **作者**: stefankoncarevic
- **时间**: 2026-09-02T18:31:36Z
- **提交信息**: [CI][MoE] Moe kernels test cleanup (#54954)

Signed-off-by: Stefan Koncarevic <stefan.koncarevic@amd.com>

### [3e9d364](https://github.com/vllm-project/vllm/commit/3e9d364ff727f002680d242ea76e8a0bbdc0163c)

- **作者**: stefankoncarevic
- **时间**: 2026-09-02T18:21:18Z
- **提交信息**: [CI/Build][ROCm] Guard the two CUDA-only tests in test_bf16_skinny_gemm (#54984)

Signed-off-by: Stefan Koncarevic <Stefan.Koncarevic@amd.com>

### [2691c6c](https://github.com/vllm-project/vllm/commit/2691c6cc535692d173986e93384c84970a0fe009)

- **作者**: stefankoncarevic
- **时间**: 2026-09-02T18:18:56Z
- **提交信息**: [Bugfix][CI] Set cudagraph_mode=FULL for the Ernie4.5-VL ViT cudagraph test (#54957)

Signed-off-by: Stefan Koncarevic <stefan.koncarevic@amd.com>

### [bf7a14d](https://github.com/vllm-project/vllm/commit/bf7a14d307bb495afc8c2587343bdc7d88c0f135)

- **作者**: Andreas Karatzas
- **时间**: 2026-09-02T18:14:32Z
- **提交信息**: [CI][ROCm] Add DSpark evals (#54852)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: mgoin <mgoin64@gmail.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [1356635](https://github.com/vllm-project/vllm/commit/1356635d837c4ef002ec98c1a0296e7ff60be3c1)

- **作者**: Isotr0py
- **时间**: 2026-09-02T18:09:09Z
- **提交信息**: [New model][Multimodal] Add DeepSeek-V4-Flash-Vision-Exp support (#54566)

Signed-off-by: Isotr0py <Isotr0py@outlook.com>

### [488e6fd](https://github.com/vllm-project/vllm/commit/488e6fd53cb29b4255364b69a4d298b1bbc26062)

- **作者**: fxmarty-amd
- **时间**: 2026-09-02T17:58:14Z
- **提交信息**: [CI] Revert flaky `test_quark_int8_w8a8_moe` (#54991)

Signed-off-by: Felix Marty <Felix.Marty@amd.com>

### [605c3dd](https://github.com/vllm-project/vllm/commit/605c3ddcbaaee06a2687a961ae7be51aec5dddc0)

- **作者**: Shengqi Chen
- **时间**: 2026-09-02T17:17:41Z
- **提交信息**: [BUILD] Bump cutlass to v4.7.1 (#54190)

Signed-off-by: Shengqi Chen <harry-chen@outlook.com>

### [d539de1](https://github.com/vllm-project/vllm/commit/d539de1c5d1a120ba3281d62c3bcb0e19a36348d)

- **作者**: Harry Mellor
- **时间**: 2026-09-02T16:56:07Z
- **提交信息**: [Docs] Add missing return annotations flagged by griffe (#54980)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [3b45d05](https://github.com/vllm-project/vllm/commit/3b45d053b4bbc61ce437f00891b52ce5ddde7c5a)

- **作者**: Hung Hoang (黄兴）
- **时间**: 2026-09-02T15:55:16Z
- **提交信息**: [Bugfix][Model] Fix CohereASR streaming audio-token estimate (unit + subsampling) (#53829)

Signed-off-by: hungh <hungh@nvidia.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>

### [41848ca](https://github.com/vllm-project/vllm/commit/41848caa63b131f931618055d3ece0b487ce8edb)

- **作者**: Ilia Yastrebov
- **时间**: 2026-09-02T14:30:16Z
- **提交信息**: [NIXL] Use int32 array for indices to avoid intermediate conversion (#51952)

Signed-off-by: Ilia Yastrebov <iyastrebov@nvidia.com>

### [c6bca6e](https://github.com/vllm-project/vllm/commit/c6bca6e58540817bd6f192ae615dfa108cec1152)

- **作者**: waizuichougou
- **时间**: 2026-09-02T14:20:26Z
- **提交信息**: [Bugfix][Multimodal] Scope cache hash kwargs by modality (#54918)

Signed-off-by: waizuichougou <2082431897@qq.com>

### [872084f](https://github.com/vllm-project/vllm/commit/872084fb773b4dedf9f72a08724451f72b115f89)

- **作者**: Misha Goin
- **时间**: 2026-09-02T14:18:38Z
- **提交信息**: [CI] Add Kimi-K3-pruned75-DSpark-TP4 gsm8k eval (#54817)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [ba6c60e](https://github.com/vllm-project/vllm/commit/ba6c60e98fd7ae91852ad81fa880d3f9153639c3)

- **作者**: drakosha
- **时间**: 2026-09-02T14:11:48Z
- **提交信息**: [Bugfix][KV Offload] Scale UniformTypeKVCacheSpecs groups by DCP (#50883)

Signed-off-by: Mikhail Kostryukov <mike@triptrack.net>
Co-authored-by: Claude <noreply@anthropic.com>

### [35faf95](https://github.com/vllm-project/vllm/commit/35faf957d65acdfc0b19f7cd4e4a2d50d7d73a1b)

- **作者**: AlexHuang
- **时间**: 2026-09-02T14:10:26Z
- **提交信息**: [Bugfix][KV Offload] Ignore stale async lookup results (#54872)

Signed-off-by: Alex <jihui.huang@daocloud.io>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [ffe3bb3](https://github.com/vllm-project/vllm/commit/ffe3bb3c723d9e5e5f5a0c8aeab1d857a4975b8b)

- **作者**: Tomasz Zielinski
- **时间**: 2026-09-02T13:31:38Z
- **提交信息**: [Hardware][XPU] Register matmul and linear batch-invariant kernels for XPU (#49209)

Signed-off-by: tzielinski-habana <tomasz.zielinski@intel.com>
Signed-off-by: Tomasz Zielinski <85164140+tzielinski-habana@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [7894394](https://github.com/vllm-project/vllm/commit/7894394b0759ba0f2d9c9cca249a6e49ecdd814f)

- **作者**: fxmarty-amd
- **时间**: 2026-09-02T12:55:15Z
- **提交信息**: [Online quantization] Add targeted online quantization configuration based on user patterns (#51285)

### [2a4e3cc](https://github.com/vllm-project/vllm/commit/2a4e3cc3dbddf4f44d69864209361f1e2a70c79a)

- **作者**: Cheng Rui
- **时间**: 2026-09-02T11:09:29Z
- **提交信息**: [Bugfix][KV Offload] Ensure tracker progress for oversized offers (#54759)

Signed-off-by: Cheng Rui <286040359@qq.com>
Co-authored-by: Codex <noreply@openai.com>

### [f81eb41](https://github.com/vllm-project/vllm/commit/f81eb4193431675918f37483d1541f6b1b96a69f)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-09-02T10:31:14Z
- **提交信息**: [Bugfix] `adjust_dcp_kv_cache_interleave_size` for NixlConnector only (#54803)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>
Co-authored-by: cjackal <44624812+cjackal@users.noreply.github.com>

### [3140531](https://github.com/vllm-project/vllm/commit/314053177332342e47bd046f134a69ea324b864c)

- **作者**: Tarun Kumar
- **时间**: 2026-09-02T09:44:06Z
- **提交信息**: Include chat template fallbacks in package_data (#53762)

Signed-off-by: Tarun Kumar <takumar@redhat.com>

### [76ba321](https://github.com/vllm-project/vllm/commit/76ba32160a501e5e8aadb5e1820c51c765714220)

- **作者**: Kevin H. Luu
- **时间**: 2026-09-02T09:16:05Z
- **提交信息**: [CI] Shard CPU jobs above the 24h P90 threshold (#54751)

Signed-off-by: Kevin Luu <51931015+khluu@users.noreply.github.com>

### [b205750](https://github.com/vllm-project/vllm/commit/b205750fe0ace51bdfda25a857386161471ef19b)

- **作者**: Simon Danielsson
- **时间**: 2026-09-02T08:59:23Z
- **提交信息**: [Bugfix][ROCm][Build] fix profiler hang due to queue interposition bug (#54171)

Signed-off-by: simondanielsson <simon.danielsson99@hotmail.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [1c26e57](https://github.com/vllm-project/vllm/commit/1c26e57d3c7b480bae4e67898784b6b976a4a515)

- **作者**: Isotr0py
- **时间**: 2026-09-02T08:52:24Z
- **提交信息**: [Bugfix] Raise for unavailable piecewise CUDA graphs (#54782)

Signed-off-by: Isotr0py <Isotr0py@outlook.com>

### [584e8f0](https://github.com/vllm-project/vllm/commit/584e8f0dda428c42c15da6e945f18eeb5356ae6d)

- **作者**: jackLei
- **时间**: 2026-09-02T08:38:36Z
- **提交信息**: [Model] Fix GLM-OCR MTP weight loading (#49869)

Signed-off-by: jackLei0901 <42642542+jackLei0901@users.noreply.github.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [87deddc](https://github.com/vllm-project/vllm/commit/87deddc7a4d673e8e17bfe774a886a55815c3bde)

- **作者**: Andreas Karatzas
- **时间**: 2026-09-02T08:29:38Z
- **提交信息**: [CI][Spec Decode] Add MTP placeholder-token regression coverage (#54893)

Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [c600500](https://github.com/vllm-project/vllm/commit/c6005000d326fe2726aed62553f5837d42c5e04c)

- **作者**: Andreas Karatzas
- **时间**: 2026-09-02T08:28:39Z
- **提交信息**: [CI][ROCm] Prefetch safetensors weights in AMD CI (#54898)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [e52407e](https://github.com/vllm-project/vllm/commit/e52407ef4ce8400bbbb6d0a34d26e0456ce72cb3)

- **作者**: Andreas Karatzas
- **时间**: 2026-09-02T08:27:05Z
- **提交信息**: [ROCm][CI] Add MTP and other spec-decode acceptance coverage (#53399)

Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>
Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [8052102](https://github.com/vllm-project/vllm/commit/8052102c2112e48f2c6ffe02ab0a3aa56632bd8f)

- **作者**: Fabian Joswig
- **时间**: 2026-09-02T08:18:41Z
- **提交信息**: [Bugfix] Fix cross-batch buffer race corrupting DiskBackend loads (#51667)

Signed-off-by: Fabian Joswig <fjosw@users.noreply.github.com>
Co-authored-by: Yifan Qiao <yifanqiao@inferact.ai>

### [01eeb79](https://github.com/vllm-project/vllm/commit/01eeb798b6c770284f7bb43e14fa6054fb98bb9d)

- **作者**: Andreas Karatzas
- **时间**: 2026-09-02T08:18:27Z
- **提交信息**: [CI][AMD] Preserve diagnostics for unwritable checkouts (#53437)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [f5711fa](https://github.com/vllm-project/vllm/commit/f5711fa138d06cfff6be8ccb8a4d98eafa8a3b50)

- **作者**: Kevin H. Luu
- **时间**: 2026-09-02T08:16:44Z
- **提交信息**: [CI] Shard LoRA TP distributed tests (#52350)

Signed-off-by: Kevin Luu <51931015+khluu@users.noreply.github.com>

### [b2558f8](https://github.com/vllm-project/vllm/commit/b2558f8da330a2fde6de44ea128d3c23c5cf8268)

- **作者**: Chauncey
- **时间**: 2026-09-02T08:15:35Z
- **提交信息**: [Bugfix] Fix launch render hanging on shutdown (#54913)

Signed-off-by: chaunceyjiang <chaunceyjiang@gmail.com>

### [c23e15b](https://github.com/vllm-project/vllm/commit/c23e15be9fc55d800ee7979ed7027163f5d468a5)

- **作者**: Zeyu Yang
- **时间**: 2026-09-02T08:14:00Z
- **提交信息**: [CI][Fix] Resolved the Ascend NPU test build image fail and add file dependencies (#50504)

Signed-off-by: yangzeyu <yangzeyu7@huawei.com>
Co-authored-by: Yikun Jiang <yikunkero@gmail.com>

### [878ec4b](https://github.com/vllm-project/vllm/commit/878ec4bfee4f9fc2f01ee0b616e57d3c81cf867a)

- **作者**: Kevin H. Luu
- **时间**: 2026-09-02T08:13:38Z
- **提交信息**: [CI] Shard entrypoints API-server tests (#52344)

Signed-off-by: Kevin Luu <51931015+khluu@users.noreply.github.com>

### [62588e0](https://github.com/vllm-project/vllm/commit/62588e0592ad5af8d3d4a536ace01afb44ebaed5)

- **作者**: stefankoncarevic
- **时间**: 2026-09-02T08:12:40Z
- **提交信息**: [CI] Batch the swap_blocks verification instead of copying block by block (#54558)

Signed-off-by: Stefan Koncarevic <stefan.koncarevic@amd.com>

### [1b4b2a1](https://github.com/vllm-project/vllm/commit/1b4b2a18b80c5e265b93ab6f83dde494eadfaa4a)

- **作者**: Kevin H. Luu
- **时间**: 2026-09-02T08:10:14Z
- **提交信息**: [CI] Shard H100 MoE refactor integration tests (#52352)

Signed-off-by: Kevin Luu <51931015+khluu@users.noreply.github.com>

### [df09c76](https://github.com/vllm-project/vllm/commit/df09c767355fd1313001fbf14ad363bba5bf0ffd)

- **作者**: Itay Etelis
- **时间**: 2026-09-02T07:43:26Z
- **提交信息**: [KV Connector][Offloading] Look through UniformTypeKVCacheSpecs in the canonical portability gate (#51690)

Signed-off-by: Itay Etelis <itay.etelis@ibm.com>
Co-authored-by: Itay Etelis <itay.etelis@ibm.com>
Co-authored-by: Or Ozeri <oro@il.ibm.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [798b557](https://github.com/vllm-project/vllm/commit/798b557e061b5b7554e2a26ef92f1ec88e9518e9)

- **作者**: Yusuke Oda
- **时间**: 2026-09-02T07:41:13Z
- **提交信息**: [Frontend] Add site-packages support for reasoning/tool parser plugins (#45241)

Signed-off-by: odashi <yusuke.oda@predicate.jp>
Co-authored-by: Chauncey <chaunceyjiang@gmail.com>

### [f4e6136](https://github.com/vllm-project/vllm/commit/f4e61361462882f82d91f60dfc4133807ef00822)

- **作者**: Thien Tran
- **时间**: 2026-09-02T07:16:29Z
- **提交信息**: [Kimi-K3] Bump FlashKDA to fix unstable inverse (#54859)

Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-09-03
**监控日期**: 2026-09-02
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 6593
- **最后更新**: 2026-09-02T23:27:18Z

## 提交统计

- **昨日提交总数**: 12
- **提交者数量**: 9
- **主要提交者**: GXIN, 汪志鹏, jingchengtian

## AI分析总结

# vLLM-Omni 提交分析

## 一、主要更新类型

本批次提交涵盖多种类型：Bug修复（5项）、功能新增（3项）、性能优化（1项）、CI基础设施改进（2项）、文档更新（1项）。整体以稳定性修复和模型能力扩展为主。

## 二、关键变更点与项目方向关系

**Bug修复类**集中在三个方向：一是修复vLLM serve错误响应的导入问题，保障基础服务稳定性；二是针对TTS/语音模型的并发构建隔离和任务类型校验，防止EngineCore分发前出现任务不匹配；三是修复Sana I2V视频管线的输出注册问题。

**功能新增类**围绕多模态模型支持展开：为SANA-Video 2B添加Cache-DiT和CPU offload支持，并新增TP和CFG并行能力，显著增强视频生成模型的部署灵活性；为MiniMax-H3补全VSA和Ulysses支持，完善序列并行策略。

**性能优化**聚焦OmniVoice的float16推理恢复和生成器热循环融合，直接提升语音模型的服务效率。

**CI改进**包括通过MIRROR_HW环境变量选择H100/B200硬件预设，以及将L4任务迁移至l4-k8s并按GPU数量拆分，优化测试资源配置。

## 三、对项目的影响与潜在意义

这批提交体现了项目“易用、快速、低成本的全模态模型服务”核心目标的落地。Bug修复直接提升服务稳定性，降低用户使用门槛；SANA-Video的并行和offload支持使大规模视频生成成为可能；MiniMax-H3的并行策略补全扩大了支持的模型范围。CI优化则保障了项目在多样化硬件上的持续集成效率。

## 四、值得关注的技术点

1. **Cache-DiT与CPU offload结合**：为视频生成模型提供更灵活的显存管理方案，对长视频生成场景意义重大
2. **StepAudio2 TRT构建隔离**：解决并发构建冲突，是TTS服务高并发场景的关键修复
3. **任务校验前置到EngineCore分发前**：避免无效计算资源浪费，体现架构设计的精细化
4. **Ascend NPU融合kernel应用**：针对特定硬件的优化表明项目对多硬件生态的重视

## 五、对项目发展的影响

从项目定位看，vLLM-Omni致力于成为全模态模型服务的一站式解决方案。本批次提交在三个维度推动这一目标：**广度上**扩展了视频生成（SANA-Video）、语音（OmniVoice、MOSS-TTS）和文本生成（MiniMax-H3）的模型覆盖；**深度上**通过并行策略、显存优化和硬件适配提升服务性能；**稳健性上**通过系统性Bug修复和CI改进夯实基础设施。特别是SANA-Video的多项增强和MiniMax-H3的并行支持，表明项目正从“能跑”向“高效跑”演进，为吸引更多生产环境用户奠定基础。Ascend NPU的适配也体现了项目对国产硬件生态的前瞻性布局。整体来看，这些提交使vLLM-Omni在“易用、快速、低成本”三个维度上均有所推进，符合其“人人可用的全模态模型服务”愿景。

## 详细提交记录

### [63ed0fd](https://github.com/vllm-project/vllm-omni/commit/63ed0fdef4e6e9bdd866ea418ad9cf65e498c67a)

- **作者**: maithilijoshi20
- **时间**: 2026-09-02T22:48:01Z
- **提交信息**: [Bugfix] Fix vLLM serve error response imports (#6707)

Signed-off-by: maithilijoshi20 <maithilijoshi2003@gmail.com>
Signed-off-by: maithilijoshi20 <97733343+maithilijoshi20@users.noreply.github.com>
Co-authored-by: maithilijoshi20 <maithilijoshi2003@gmail.com>

### [ca6b4e2](https://github.com/vllm-project/vllm-omni/commit/ca6b4e21127ff3f36530438a42948fe17117d412)

- **作者**: DanaerLee
- **时间**: 2026-09-02T19:54:55Z
- **提交信息**: [Perf][Bugfix][OmniVoice] Restore float16 serving, and fuse the generator hot loop (#6317)

Signed-off-by: MrlixiangWE <mrdanaer@gmail.com>

### [b9a88bf](https://github.com/vllm-project/vllm-omni/commit/b9a88bf51e2e7a175a6b559db1d442560551c581)

- **作者**: Jim Ban
- **时间**: 2026-09-02T19:53:02Z
- **提交信息**: [Bugfix][TTS] Isolate concurrent StepAudio2 TRT builds (#6957)

Signed-off-by: BANANASJIM <bananasjim1@gmail.com>

### [3ab582c](https://github.com/vllm-project/vllm-omni/commit/3ab582c99352113000d61e4522c18324a301793a)

- **作者**: GXIN
- **时间**: 2026-09-02T18:16:55Z
- **提交信息**: [Bugfix][Qwen3-TTS] Reject task mismatches before EngineCore dispatch (#6113)

Signed-off-by: XIN GAO <1037396230@qq.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [3b6ce98](https://github.com/vllm-project/vllm-omni/commit/3b6ce98421a4a32ad2c0a44e241a43f29f2ce5fa)

- **作者**: vOv
- **时间**: 2026-09-02T15:40:48Z
- **提交信息**: [Model] Add Cache-DiT and CPU offload support for SANA-Video 2B (#5882)

Signed-off-by: cr-gao <gaochenrui@sjtu.edu.cn>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>
Co-authored-by: Alicia <115451386+congw729@users.noreply.github.com>

### [95a9311](https://github.com/vllm-project/vllm-omni/commit/95a93116960e364cc759c49023a4c35284157235)

- **作者**: wangyu
- **时间**: 2026-09-02T15:39:49Z
- **提交信息**: [CI] Select mirror_hardwares presets via MIRROR_HW (H100/B200) (#5543)

Signed-off-by: wangyu <410167048@qq.com>
Signed-off-by: lishunyang12 <lishunyang12@163.com>
Signed-off-by: [Your Name] <your.email@example.com>
Signed-off-by: wangyu <53896905+yenuo26@users.noreply.github.com>
Signed-off-by: Bo Li <22713281+bobboli@users.noreply.github.com>
Co-authored-by: lishunyang12 <lishunyang12@163.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Bo Li <22713281+bobboli@users.noreply.github.com>

### [d5fd9eb](https://github.com/vllm-project/vllm-omni/commit/d5fd9eb6bbeb067582a42f7bd060996c7c6931c0)

- **作者**: wangyu
- **时间**: 2026-09-02T15:16:58Z
- **提交信息**: [Bugfix][Diffusion] Register Sana I2V pipeline as video output (#6953)

Signed-off-by: wangyu <410167048@qq.com>

### [5d20f6b](https://github.com/vllm-project/vllm-omni/commit/5d20f6b900dfcf22b42068e28a3cbbdb5b4707e7)

- **作者**: Bo Li
- **时间**: 2026-09-02T11:42:37Z
- **提交信息**: [Doc] Refine TRTLLM attention guidance (#6724)

Signed-off-by: Bo Li <22713281+bobboli@users.noreply.github.com>

### [c59b48b](https://github.com/vllm-project/vllm-omni/commit/c59b48b47e8359827b27f54cbdb18ba0da2836b4)

- **作者**: 汪志鹏
- **时间**: 2026-09-02T11:19:21Z
- **提交信息**: [Feature][MiniMax-H3] Complete VSA and Ulysses support (#6909)

Signed-off-by: princepride <wangzhipeng628@gmail.com>
Signed-off-by: 汪志鹏 <wangzhipeng628@gmail.com>

### [57c08d3](https://github.com/vllm-project/vllm-omni/commit/57c08d34c359cce233990fd138a8dc9f46973e34)

- **作者**: vOv
- **时间**: 2026-09-02T09:44:41Z
- **提交信息**: [Model] Add TP and CFG parallelism to SANA-Video 2B (#5861)

Signed-off-by: cr-gao <gaochenrui@sjtu.edu.cn>

### [b6e72f3](https://github.com/vllm-project/vllm-omni/commit/b6e72f3879f52cc7d75b989890a404758f87ebf6)

- **作者**: wangyu
- **时间**: 2026-09-02T09:09:59Z
- **提交信息**: [CI] Migrate L4 jobs to l4-k8s and split by GPU count (#6890)

Signed-off-by: wangyu <410167048@qq.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [67ef0b6](https://github.com/vllm-project/vllm-omni/commit/67ef0b64b94d2618aaa6c4090037c16175e0b92c)

- **作者**: jingchengtian
- **时间**: 2026-09-02T08:58:23Z
- **提交信息**: [Hardware][Ascend] Use npu_rotary_mul fused kernel for MOSS-TTS codec RoPE (#6908)

Signed-off-by: jingchengtian <tjc1995@126.com>

---
