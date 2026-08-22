# GitHub Stars 合并报告 - 2026-08-22

**合并日期**: 2026-08-23
**监控日期**: 2026-08-22
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


**报告日期**: 2026-08-23
**监控日期**: 2026-08-22
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2167
- **最后更新**: 2026-08-21T09:07:38Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-08-23
**监控日期**: 2026-08-22
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2711
- **最后更新**: 2026-08-22T03:30:58Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-08-23
**监控日期**: 2026-08-22
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2199
- **最后更新**: 2026-08-20T21:19:51Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-08-23
**监控日期**: 2026-08-22
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 6211
- **最后更新**: 2026-08-22T20:25:01Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Alex Yang

## AI分析总结

# 提交分析：FlashInfer MoE 路由测试重构

## 1. 主要更新类型

本次提交属于**测试架构重构**，核心目标是解耦 MoE（Mixture of Experts）路由逻辑的测试与量化/布局/形状参数的组合测试，将原本庞大的测试矩阵拆分为独立、轻量的测试单元。

## 2. 关键变更点

- **新增独立路由算子**：将 `Routing::Runner` 从 `trtllm_fused_moe_runner.cu` 中拆分为独立编译单元，并通过 TVM-FFI 导出为 `trtllm_gen_routing`，提供轻量级 JIT 模块（仅含路由内核，不依赖 batched-GEMM 栈）。
- **新增 Python API**：`flashinfer.fused_moe.trtllm_gen_routing(...)`，支持 9 种路由方法，覆盖 top_k、专家数（最高 512 专家/top_k 22）、n_group/topk_group、bias 与 logits 数据类型、tile_tokens_dim、负载倾斜、边缘 token 数等维度。
- **测试矩阵分解**：将 `(路由方法) × (其他参数)` 的笛卡尔积拆分为 `(路由方法, 密集但廉价)` + `(少量路由方法) × (其他参数)` 两个独立测试集，大幅缩减测试规模（如 `test_deepseekv3_routing` 从约 7.9k 原始用例缩减）。
- **覆盖迁移而非删除**：路由正确性测试迁移至新测试文件，量化/布局/形状组合测试保留少量路由方法做冒烟验证。

## 3. 对项目的影响与意义

- **测试效率显著提升**：原 `renormalize` 分片测试耗时 123 分钟/1,398 个通过用例，拆分后大幅缩短 CI 时间，提升开发迭代速度。
- **关注点分离**：路由正确性与量化正确性在代码路径上完全正交（不共享内核代码），拆分测试符合软件工程最佳实践，便于定位失败原因。
- **API 扩展**：新增的 `trtllm_gen_routing` 独立算子为外部用户提供了更细粒度的 MoE 路由能力，无需加载完整 fused-MoE 栈即可使用。

## 4. 值得关注的技术点

- **从 logits 模式下的专家 ID 重建**：内核不直接输出 `topk_ids`，而是通过排列（permutation）和 `cta_idx_xy_to_batch_idx[slot // tile_tokens_dim]` 反推，这是对 Triton/FlashInfer 内核执行模型的深入理解。
- **JIT 模块轻量化设计**：仅编译路由内核，避免不必要的 GEMM 依赖，降低编译时间和二进制体积。
- **测试参数化策略**：将路由方法作为独立轴，与其他参数解耦，同时保留少量组合冒烟测试确保集成正确性。

## 5. 对项目发展的影响

FlashInfer 定位为**高性能 GPU 推理内核库**，MoE 是其核心场景之一。本次重构体现了项目在工程成熟度上的进步：

- **可维护性提升**：测试架构的合理化使后续新增路由方法或量化格式时，无需担心测试矩阵爆炸。
- **生态友好性增强**：独立路由 API 降低了外部集成门槛，可能吸引更多框架（如 vLLM、SGLang）采用 FlashInfer 的 MoE 路由能力。
- **性能优化空间**：路由与 GEMM 的解耦为未来针对路由内核单独优化（如负载均衡、专家并行）铺平了道路，符合项目"高性能"的核心目标。

总体而言，这是一次以测试重构为表象、以架构优化为实质的提交，对项目的长期可扩展性和社区采用均有积极意义。

## 详细提交记录

### [fb28d72](https://github.com/flashinfer-ai/flashinfer/commit/fb28d7242b3506a2348265962041acc1fb56cca4)

- **作者**: Alex Yang
- **时间**: 2026-08-22T11:34:52Z
- **提交信息**: feat(moe): standalone trtllm-gen routing op + decomposed tests/moe routing matrix (#4082)

## 📌 Description

`tests/moe` multiplies routing-method axes against the full quant ×
layout × shape matrix, which is the main driver of the suite's size
(e.g. `test_deepseekv3_routing` ~7.9k raw cases; the routed fused dense
grid carried a 6× routing multiplier; the renormalize shard trio
measured 123 min / 1,398 passing cases pre-split). Routing correctness
is orthogonal to quantization — they share no kernel code path — so this
PR decomposes `(routing methods) × (other params)` into `(routing
methods, dense but cheap) + (few routing methods) × (other params)`:

**New standalone routing op + test**
- Split the `Routing::Runner` dispatcher out of
`trtllm_fused_moe_runner.cu` into its own TU and expose it via a new
TVM-FFI export `trtllm_gen_routing` with a lightweight JIT module
(routing kernels only — no batched-GEMM stack).
- Python API `flashinfer.fused_moe.trtllm_gen_routing(...)`. Note: in
from-logits mode the kernels emit no expert ids (`mPtrTopKIds` is
input-only, `mPtrTopKPacked` is pipeline scratch); `topk_ids` is
reconstructed from the permutation via `cta_idx_xy_to_batch_idx[slot //
tile_tokens_dim]`.
- `tests/moe/test_trtllm_gen_routing.py`: all 9 routing methods ×
{top_k, num_experts (model shapes up to 512 experts / top_k 22),
n_group/topk_group, bias & logits dtypes, tile_tokens_dim, load skew,
edge token counts} against the existing `routing_reference_*` host
oracles, plus expert-parallel shard cases and grouped-argument rejection
tests.

**Fused-matrix reduction (coverage relocated, not deleted)**
- `test_trtllm_gen_routed_fused_moe.py`: dense grid pinned to
Renormalize/packed + an 18-case method × format × quant parity smoke
(routing here is host-precomputed, so the method axis only varied
reference math now tested directly).
- `test_trtllm_gen_fused_moe.py::test_deepseekv3_routing`: dropped
`kimi_k2`/`DSLite`/`GLM4_MoE` configs and orphaned intermediate sizes;
kept `DSv3`, `nemotron_3_super`, and both fused-shared-expert variants
(that fusion isn't covered standalone).
- Renormalize shard trio: `RENORMALIZE_ROUTING_CONFIGS` shrunk to the
Renormalize configs (the method GPT-OSS/Qwen3/Qwen3-Next/Mixtral use);
Default/SigmoidRenorm/MiniMax2 from-logits plumbing keeps smoke coverage
via `test_routing_dtype_flexibility`.

**Validation (B200, all green — zero failures)**

Collected counts re-measured against the current merge base `46fc99b9`
(main as of the 2026-08-21 merge). These are smaller than the numbers
first posted here, which were taken against the original `ce29c1a5`
baseline: main has since independently trimmed shape axes in the routed
file, so the two reductions compound.

| file | collected before → after | B200 result |
|---|---|---|
| `test_trtllm_gen_routed_fused_moe.py` | 466 → **364** (−22%) | 0
failures; hours-class → ~14 min incl. cold JIT |
| … of which the dense grid `test_trtllm_gen_routed_fused_moe` | 144 →
**24** (−83%) | |
| `test_trtllm_gen_fused_moe.py` | 8,173 → **4,141** (−49%) | deepseekv3
slice: 69 executed / 0 failed, ~22 min |
| renormalize shards (3 files) | 2,688 → **1,152** (−57%) | 201 executed
/ 0 failed, ~93 min total incl. cold JIT + autotune (pre-shrink: 1,398
executed / ~123 min) |
| **subtotal** | **11,327 → 5,657 (−50%)** | |
| `test_trtllm_gen_routing.py` (new) | — → 688 | **664 passed / 24
arch-skipped / 0 failed**, 3m44s on umb-b200-262 (sm100a) |

Rationale, design notes, and the full measurement table now live in
`docs/design_docs/moe_routing_test_decomposition.md` (promoted from the
temporary working doc; four in-code references updated).

## 🔍 Related Issues

Follow-up to the CI-budget sharding in #3635 (the shards kept the full
cross-product; this PR reduces it).

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

- All touched suites validated end-to-end on B200 (table above); the
routed SOLO file went from hours-class to ~14 min cold.
- **Build fix since the approval.** The 2026-08-21 main merge brought in
#4635, which split `trtllm_fused_moe_routing_custom.cu` into
`_custom_{block,cluster,cluster_large,entry}.cu`. The fused module's
source list was updated by the merge; `gen_trtllm_gen_routing_module()`
— added by this PR — was not, so every *AOT Build Import* job died with
`ninja: error: ... missing and no known rule to make it`. Fixed in
`451d855d` and verified by compiling the module for `sm_100a`.
- **Review findings addressed** (see the inline replies): EP-shard
coverage for the `topk_ids` reconstruction (`+ local_expert_offset` and
`-1` masking) — 36 new cases through both kernel families;
`n_group`/`topk_group` validation mirrored into the binding, since the
dispatcher only guards `top_k <= 22` and `topk_group <= 4`;
`TraceTemplate` + registry entry + `example.py` call + committed
`fi_trace_out` JSON; `docs/api/fused_moe.rst` entries clearing the two
`api_rst_missing` findings.
- Still deferred to follow-ups: `num_fused_shared_experts > 0` and
routing-replay coverage in the standalone test; possible further
thinning of from-logits grids once an fp8-per-tensor routed entry point
exists (it currently has no pre-routed counterpart).
- AI-assisted (see commit messages); happy to walk through any design
choice — the least obvious one is the `topk_ids` reconstruction,
documented in `flashinfer/fused_moe/trtllm_gen_routing.py`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added standalone TensorRT-LLM MoE routing for multiple routing
methods, expert grouping, scaling, normalization, shared experts, and
expert-parallel configurations.
* Exposed routing selections, permutation metadata, padding details, and
CTA information through the public fused MoE API.
* Added tracing support for standalone routing stages on supported GPUs.

* **Documentation**
  * Documented the routing API and test coverage strategy.

* **Tests**
* Added correctness, validation, parity, expert-sharding, trace, and
rendered-source coverage.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-08-23
**监控日期**: 2026-08-22
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4026
- **最后更新**: 2026-08-22T19:40:08Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: William Lin

## AI分析总结

### 提交分析总结

**1. 主要更新类型**  
本次提交为**性能优化**，针对DiT（Diffusion Transformer）推理过程引入可选的区域级全图编译（regional fullgraph compile）机制。

**2. 关键变更点与项目方向**  
- 新增`opt-in`（可选启用）的编译模式，允许用户对DiT推理的特定区域（如注意力模块或部分网络层）进行全图编译，而非整体模型编译。  
- 与FastVideo项目“加速视频生成全流程”的核心目标一致，通过减少编译开销和内存占用，提升推理效率，尤其适用于长视频或高分辨率生成场景。

**3. 项目影响与潜在意义**  
- **灵活性提升**：用户可根据硬件资源或任务需求，选择局部编译，避免全图编译带来的启动延迟或显存压力。  
- **性能优化空间**：区域级编译可针对性优化热点计算区域，可能显著降低推理延迟，同时保留非关键区域的动态灵活性。  
- **生态适配**：为后续支持更多模型架构（如混合专家模型）或边缘设备部署奠定基础。

**4. 值得关注的技术点**  
- **全图编译（fullgraph compile）**：利用`torch.compile`或类似框架，将区域计算图整体编译为高效内核，减少Python解释开销。  
- **区域选择策略**：需明确哪些区域适合编译（如静态形状的注意力层），避免因动态控制流导致编译失败。  
- **opt-in设计**：默认关闭，确保兼容性，同时为高级用户提供性能调优入口。

**5. 对项目发展的影响**  
FastVideo旨在提供高效、易用的视频生成工具链。此次优化直接强化了其推理性能优势，尤其在长视频生成或资源受限环境中，可提升用户体验。同时，该特性为后续引入更复杂的编译优化（如算子融合、内存规划）提供了实践基础，有助于项目在竞争激烈的视频生成框架中保持技术领先性。

## 详细提交记录

### [d3cff51](https://github.com/hao-ai-lab/FastVideo/commit/d3cff517cd5b3d824ec7590e78b28624244afbcc)

- **作者**: William Lin
- **时间**: 2026-08-22T19:14:39Z
- **提交信息**: [perf] Add opt-in regional fullgraph compile for DiT inference (#1741)

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-08-23
**监控日期**: 2026-08-22
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34353
- **最后更新**: 2026-08-22T21:19:46Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 1
- **主要提交者**: Sayak Paul

## AI分析总结

## 提交分析总结

### 1. 主要更新类型
本批次提交全部为**测试相关修复与重构**，无功能新增或文档更新。具体包括：修复CUDA显存溢出（OOM）、移除废弃测试基类、跳过特定测试、修复AOT编译失败。

### 2. 关键变更点
- **修复VidTok切片/平铺测试的显存溢出**：删除子类中错误的测试覆盖，继承mixin中正确实现（使用`torch.no_grad()`和`torch.allclose`），将峰值显存从10.9GiB降至1.7GiB。
- **清理测试架构**：移除旧的`AutoencoderTesterMixin`，统一使用新命名的测试基类，减少重复代码。
- **跳过Hunyuan框架组卸载测试**：避免在特定环境下运行不稳定或资源密集的测试。
- **修复AOT编译失败**：解决测试中因AOT（Ahead-of-Time）编译导致的兼容性问题。

### 3. 对项目的影响
- **提升测试稳定性**：显存优化直接解决了T4 GPU上因内存不足导致的连锁失败，使测试套件在资源受限环境（如CI）中更可靠。
- **降低维护成本**：删除重复测试代码和废弃基类，简化测试结构，便于后续扩展。
- **规避已知问题**：跳过Hunyuan相关测试和修复AOT编译，减少误报，聚焦核心功能验证。

### 4. 值得关注的技术点
- **显存优化技巧**：在测试中正确使用`torch.no_grad()`避免autograd图保留，是深度学习测试中常见的显存优化手段。
- **测试继承设计**：通过mixin提供默认实现，子类按需覆盖，避免复制粘贴导致的逻辑漂移（如`.all() == .all()`比较两个布尔值的错误写法）。
- **AOT编译兼容性**：反映项目对多种编译后端（如TorchInductor）的适配需求，是生产级库的重要考量。

### 5. 对项目发展的影响
Diffusers作为HuggingFace核心的扩散模型库，测试质量直接关系到其作为基础设施的可靠性。本批次提交虽不涉及新功能，但通过**加固测试基础设施**，为后续大规模模型（如VidTok视频模型）的稳定集成铺路。显存优化使测试能在更经济的GPU上运行，降低社区贡献门槛；测试架构清理则提升了代码可维护性，符合项目长期演进需求。整体上，这些改动体现了项目在**规模化、生产化**阶段的工程化投入，是成熟开源项目的典型特征。

## 详细提交记录

### [58eb52c](https://github.com/huggingface/diffusers/commit/58eb52c0803ea9af3abec60841c2a093bdf1f951)

- **作者**: Sayak Paul
- **时间**: 2026-08-22T19:04:28Z
- **提交信息**: tests: fix CUDA OOM in VidTok slicing/tiling tests (#14554)

TestAutoencoderVidTokSlicingTiling overrode test_enable_disable_tiling and
test_enable_disable_slicing with copies that ran their three forward passes
outside torch.no_grad(). The retained autograd graphs pushed each test to a
10.9 GiB peak on a 14.74 GiB T4, so with any memory left over from earlier
files in the same xdist worker the class OOM'd -- taking
test_forward_with_norm_groups down with it.

The mixin already implements both tests correctly (no_grad, plus torch.allclose
for the disable-comparison instead of the `.all() == .all()` idiom the copies
used, which compares two booleans and always passes). Drop the overrides and
inherit them.

Peak memory on a T4, measured per test:

  before   10937.3 MiB
  after     1666.5 MiB

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [4c52cb2](https://github.com/huggingface/diffusers/commit/4c52cb267ab60d239e3afccaa54ff7bcaa7f25fb)

- **作者**: Sayak Paul
- **时间**: 2026-08-22T16:57:36Z
- **提交信息**: [tests] remove autoencodertestermixin and rename new one. (#14555)

remove autoencodertestermixin and rename new one.

### [1b98ae1](https://github.com/huggingface/diffusers/commit/1b98ae1060b765f2efe22540f52691b8c00a83f1)

- **作者**: Sayak Paul
- **时间**: 2026-08-22T07:43:24Z
- **提交信息**: [tests] skip hunyuan framepack group offloading tests (#14551)

skip hunyuan framepack group offloading tests

### [ecfbf76](https://github.com/huggingface/diffusers/commit/ecfbf7662cfcfc1b8dd0f5db1a88ccfadc846fc1)

- **作者**: Sayak Paul
- **时间**: 2026-08-22T07:43:03Z
- **提交信息**: [tests] AOT compilation failure fixes (#14553)

compilation failure fixes

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-08-23
**监控日期**: 2026-08-22
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


**报告日期**: 2026-08-23
**监控日期**: 2026-08-22
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12976
- **最后更新**: 2026-08-22T10:08:01Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-08-23
**监控日期**: 2026-08-22
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 32265
- **最后更新**: 2026-08-22T21:22:58Z

## 提交统计

- **昨日提交总数**: 19
- **提交者数量**: 7
- **主要提交者**: Mohammad Miadh Angkad, Hồ Sỹ Thế, Shangming Cai

## AI分析总结

# SGLang 昨日提交分析报告

## 一、主要更新类型

本次提交涵盖**功能新增**（约7项）、**Bug修复**（约4项）、**性能优化**（约3项）、**重构**（约3项）和**文档更新**（1项），整体以功能扩展和优化为主。

## 二、关键变更点与项目方向

**Diffusion模型支持**是本次更新的核心主题（约8项提交），包括：新增minimax-h3节点、支持单文件组件权重覆盖、VAE解码器权重保持加载时的数据类型、量化原生编码器兼容、通过目录实现VAE映射门控、层间卸载策略优化、以及通过courier线程传输映射层。这些变更显著增强了SGLang在扩散模型领域的实用性和灵活性，与项目“高效推理框架”的定位高度契合。

**AMD平台优化**（2项）聚焦于DeepSeek-V4的aiter融合mHC前后置处理及NEXTN spec attention的GQA打包修复，体现了对AMD硬件生态的持续投入。

**KV传输重构**（3项）将辅助导入移出引导循环、将重复的`_handle_staging_req`提取为mixin、清理死代码，提升了代码可维护性。

**其他重要功能**包括：Weight Daemon抽象（支持权重管理服务化）、Pixtral多图像特征在CUDA IPC包装前拆分（修复VLM多图处理）、以及测试修复。

## 三、项目影响与潜在意义

- **Diffusion生态完善**：SGLang正从纯LLM推理引擎向多模态推理平台演进，本次大量diffusion相关提交表明该项目正积极抢占扩散模型推理市场。
- **硬件适配深化**：AMD和NPU的专项优化扩大了硬件覆盖范围，有助于吸引更多用户。
- **架构清晰化**：KV传输重构和Weight Daemon抽象为未来扩展奠定更稳固的架构基础。

## 四、值得关注的技术点

1. **aiter融合mHC前后置处理**：针对DeepSeek-V4的跨层边界调度，是面向新一代MoE架构的底层优化。
2. **courier线程传输映射层**：通过异步线程提升层映射传输效率，是性能优化的创新方案。
3. **VAE解码器dtype保持**：避免不必要的类型转换，减少显存占用和计算开销。
4. **Weight Daemon抽象**：将权重管理从推理进程中解耦，为分布式场景下的权重分发提供新思路。

## 五、对项目发展的影响

结合README中SGLang“高性能、易用的大模型推理框架”的定位，这些提交表明项目正沿着**多模态扩展**和**硬件适配深化**两条主线快速演进。Diffusion支持的持续增强将帮助SGLang在图像/视频生成推理领域建立竞争优势；AMD/NPU优化则扩大了潜在用户基础。同时，架构层面的重构和抽象（如Weight Daemon、KV传输mixin）为项目长期可维护性和功能扩展提供了坚实基础。整体来看，SGLang正从“LLM推理引擎”向“通用多模态推理平台”转型，这些提交是这一战略方向的具体落地。

## 详细提交记录

### [eec794b](https://github.com/sgl-project/sglang/commit/eec794bce0808ae26cc1dcb84a56b65d2df82af5)

- **作者**: Hồ Sỹ Thế
- **时间**: 2026-08-22T21:22:43Z
- **提交信息**: [AMD][Spec] Fix aiter GQA packing + split-KV routing in NEXTN spec attention (verify & draft_extend) (#30105)

### [cce0a12](https://github.com/sgl-project/sglang/commit/cce0a1244b5a3ee60411fb403f65f856a1d012f0)

- **作者**: Shangming Cai
- **时间**: 2026-08-22T17:24:58Z
- **提交信息**: refactor(disagg): hoist staging helper imports out of the bootstrap loops (#35980)

### [7d22b7a](https://github.com/sgl-project/sglang/commit/7d22b7a8750f53a04e41a5a5671f9a56ab6cd001)

- **作者**: Mick
- **时间**: 2026-08-22T15:48:40Z
- **提交信息**: [diffusion] docs: add tuning guide for h3 on consumer-level gpu (#35816)

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [b98d472](https://github.com/sgl-project/sglang/commit/b98d472158f707c11b39510fa8406253bbfd5008)

- **作者**: Артем Савкин
- **时间**: 2026-08-22T15:32:20Z
- **提交信息**: [NPU] [Diffusion] Fix critical Ascend NPU Diffusion regression/bugs & restore 2-NPU CI testcase (#34855)

Co-authored-by: Elizaveta Martirosian <elizabet3000@mail.ru>
Co-authored-by: Arseniy Mironov <98156294+Napkin-AI@users.noreply.github.com>
Co-authored-by: Alexandr <117110413+Allor-maker@users.noreply.github.com>
Co-authored-by: P_Alex_Tr <aleksandr.smyshlaev@yandex.ru>

### [0b064e3](https://github.com/sgl-project/sglang/commit/0b064e37397cf8fc7b0816574794e9fc9ac87df9)

- **作者**: Mick
- **时间**: 2026-08-22T15:11:49Z
- **提交信息**: [diffusion] comfyui: add a minimax-h3 node and a generic extra-fields passthrough (#35352)

### [453b98c](https://github.com/sgl-project/sglang/commit/453b98c490d7a7956903d2f3a603034d7cc0780e)

- **作者**: Mick
- **时间**: 2026-08-22T15:09:35Z
- **提交信息**: [diffusion] feat: support single-file component weight overrides (#35979)

### [46cb12a](https://github.com/sgl-project/sglang/commit/46cb12ab45d9c7f07fbb8fb07919ed55cbdbf6c5)

- **作者**: Mick
- **时间**: 2026-08-22T15:08:44Z
- **提交信息**: [diffusion] fix: fix hunyuan3d stale extension lock hangs (#35989)

### [d315eb7](https://github.com/sgl-project/sglang/commit/d315eb725044e435b146c85488b7c6d9222f7fec)

- **作者**: karverma-amd
- **时间**: 2026-08-22T14:34:57Z
- **提交信息**: [AMD] DeepSeek-V4: add aiter fused mHC post+pre with cross-layer boundary dispatch (#32577)

Co-authored-by: 1am9trash <1am9trash@gmail.com>
Co-authored-by: HAI <hixiao@gmail.com>

### [db570fe](https://github.com/sgl-project/sglang/commit/db570fe619ae15d8bd4ee04f146bc8234c52a20d)

- **作者**: Mick
- **时间**: 2026-08-22T13:36:46Z
- **提交信息**: [diffusion] chore: let the auto policy select h3's dit for layerwise offload (#35812)

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [61981e1](https://github.com/sgl-project/sglang/commit/61981e1fcd43c91cf8f70669fa43e91f774c5116)

- **作者**: Mick
- **时间**: 2026-08-22T13:31:06Z
- **提交信息**: [diffusion] optimization: keep vae decoder weights in their decode dtype from load (#35967)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [3c69a4c](https://github.com/sgl-project/sglang/commit/3c69a4c744525be0146629fc5933e3ddab609fb2)

- **作者**: Shangming Cai
- **时间**: 2026-08-22T11:23:46Z
- **提交信息**: fix(test): unbreak test_kv_transfer_replica_metric after #35950 (#35974)

### [a8c16b2](https://github.com/sgl-project/sglang/commit/a8c16b2e5575790f9d6c3db7e44ec1edf1ef71f1)

- **作者**: Mick
- **时间**: 2026-08-22T11:12:48Z
- **提交信息**: [diffusion] feature: use the directory for the vae mapping gate (#35946)

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [489e605](https://github.com/sgl-project/sglang/commit/489e605b352bdbba005814fa2ce7df83b953f17f)

- **作者**: Mick
- **时间**: 2026-08-22T10:51:01Z
- **提交信息**: [diffusion] feat: admit compatible quantized native encoders (#35962)

### [382343f](https://github.com/sgl-project/sglang/commit/382343f860c7df8dc43ecefd7902c940d81c99a9)

- **作者**: Mick
- **时间**: 2026-08-22T09:17:14Z
- **提交信息**: [diffusion] optimization: transfer mapped layers through a courier thread (#35882)

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [cb10ca1](https://github.com/sgl-project/sglang/commit/cb10ca16ddaa0d01781ea3d8291ffa34073f3872)

- **作者**: siyu
- **时间**: 2026-08-22T09:13:46Z
- **提交信息**: [FEAT] Weight Daemon abstraction (#33279)

Co-authored-by: liusy58 <liusy58@smail.nju.edu.cn>

### [5c03069](https://github.com/sgl-project/sglang/commit/5c03069d4bce87c97b257ad05f9d497729a47c4f)

- **作者**: Shangming Cai
- **时间**: 2026-08-22T07:45:18Z
- **提交信息**: refactor(disagg): drop dead placeholder overrides in Common KV sender/receiver (#35950)

### [15a4398](https://github.com/sgl-project/sglang/commit/15a439832054c1809a2bf59f7b94bf9dd71de282)

- **作者**: Shangming Cai
- **时间**: 2026-08-22T07:35:55Z
- **提交信息**: refactor(disagg): hoist duplicated _handle_staging_req into a mixin (#35948)

### [b391ef1](https://github.com/sgl-project/sglang/commit/b391ef171f1a2a23653a6ad0bb77d4d34ae3a95b)

- **作者**: Mick
- **时间**: 2026-08-22T07:33:53Z
- **提交信息**: [diffusion] feat: load serialized bnb4 components with transformers (#35945)

### [9035432](https://github.com/sgl-project/sglang/commit/90354326c74a8313d7f776a156f9c77b1d4ea5cc)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-08-22T07:17:55Z
- **提交信息**: [VLM] Split Pixtral multi-image features before the CUDA IPC wrap (#35463)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-08-23
**监控日期**: 2026-08-22
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1253
- **最后更新**: 2026-08-21T15:28:25Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-08-23
**监控日期**: 2026-08-22
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 89718
- **最后更新**: 2026-08-22T22:19:56Z

## 提交统计

- **昨日提交总数**: 11
- **提交者数量**: 7
- **主要提交者**: Jens, Taneem Ibrahim, Kevin H. Luu

## AI分析总结

## 提交分析总结

### 1. 主要更新类型
本批次提交涵盖**Bug修复**、**性能优化**、**功能增强**和**代码重构**四类。其中Bug修复3项（Rust pooling端点、LFM2投机解码、ROCm profiler），性能优化1项（Mamba前缀缓存），功能增强2项（稀疏检查点更新、输入吞吐量报告），重构与清理3项（多模态处理器简化、flag移除、mypy类型修复），另有1项CI构建镜像恢复。

### 2. 关键变更点与项目方向
- **稀疏检查点更新**（#50723）：支持通过原生权重加载器进行稀疏检查点更新，直接服务于RL训练场景，与vLLM“易用、快速、廉价”的LLM服务目标一致，降低大规模模型迭代成本。
- **Mamba前缀缓存优化**（#52789）：针对Mamba架构实现内部预填充检查点，TTFT提升9%~25%，显著改善首token延迟，强化vLLM在长序列场景下的性能优势。
- **投机解码修复**（#50272）：修复LFM2模型short_conv的投机解码问题，提升特定架构的推理正确性，扩大模型兼容性。
- **多模态处理器简化**（#53275/#53364/#53385）：持续重构多模态处理流程，移除冗余flag，简化HF处理器应用逻辑，体现项目对代码可维护性和架构清晰度的重视。

### 3. 项目影响与潜在意义
- **性能层面**：Mamba前缀缓存优化直接提升用户体验，9%~25%的TTFT改善对实时交互场景意义重大。
- **功能层面**：稀疏检查点更新为RL工作流提供更高效的模型迭代路径，吸引更多研究用户。
- **稳定性层面**：ROCm profiler修复和CUDA 13构建镜像恢复，保障了多硬件平台的开发与部署体验。
- **架构层面**：多模态代码重构和mypy类型修复，降低长期维护成本，为后续功能扩展奠定基础。

### 4. 值得关注的技术点
- **原生权重加载器**：稀疏检查点更新的实现方式值得关注，可能涉及新的权重序列化格式或加载策略。
- **Mamba前缀缓存机制**：内部预填充检查点的设计思路，对非Transformer架构的缓存优化具有参考价值。
- **LFM2投机解码修复**：涉及short_conv与投机解码的交互逻辑，对混合架构模型的推理优化有启示。
- **Rust pooling端点**：vLLM引入Rust组件的趋势值得留意，可能预示性能关键路径的Rust化方向。

### 5. 对项目发展的影响
结合README中“Easy, fast, and cheap LLM serving for everyone”的定位，本批次提交从三个维度推动项目发展：**性能**上通过Mamba优化和profiler修复巩固“fast”承诺；**易用性**上通过多模态重构和类型修复降低使用与开发门槛；**生态**上通过稀疏检查点和投机解码支持扩展模型覆盖范围。整体呈现“性能优化+架构治理”双轮驱动的发展态势，既追求即时性能收益，也注重长期代码健康度，符合一个成熟开源项目的演进节奏。

## 详细提交记录

### [a014e35](https://github.com/vllm-project/vllm/commit/a014e35f38c80fb0652387740193ad2147fed6a3)

- **作者**: Taneem Ibrahim
- **时间**: 2026-08-22T19:45:09Z
- **提交信息**: [Pooling] Fix Rust pooling endpoint for benchmark (#53352)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [811d12e](https://github.com/vllm-project/vllm/commit/811d12ee26fa119cf8faae44d80330becf1e7fe3)

- **作者**: Wentao Ye
- **时间**: 2026-08-22T19:41:27Z
- **提交信息**: [Mypy Fix] Mypy fix for "vllm/model_executor/models/[eE][fF]" (#53381)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [236f78c](https://github.com/vllm-project/vllm/commit/236f78cc5c39362f80c0c7df1ffe810466525f33)

- **作者**: Shuolei Wang
- **时间**: 2026-08-22T17:39:58Z
- **提交信息**: [Core][RL] Support sparse checkpoint updates through native weight loaders (#50723)

Signed-off-by: Shuolei Wang <shuoleiwang123@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [9eb9d9d](https://github.com/vllm-project/vllm/commit/9eb9d9d3953959695108600c8ed33d36bc6a1e5f)

- **作者**: Wentao Ye
- **时间**: 2026-08-22T17:32:40Z
- **提交信息**: [Perf] Support internal prefill checkpoints for Mamba prefix caching, 9%~25% TTFT improvement (#52789)

Signed-off-by: yewentao256 <zhyanwentao@126.com>
Signed-off-by: Ziming Huang <zelda.huanghuang@gmail.com>
Signed-off-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>
Co-authored-by: Ziming Huang <zelda.huanghuang@gmail.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [020829f](https://github.com/vllm-project/vllm/commit/020829f66baa231a3ed549c7f6b4a3171ef1c759)

- **作者**: Cyrus Leung
- **时间**: 2026-08-22T17:25:55Z
- **提交信息**: [MM] Remove renderer_applies_updates flag (#53385)

Signed-off-by: DarkLight1337 <tlleungac@connect.ust.hk>

### [610bfc5](https://github.com/vllm-project/vllm/commit/610bfc58e93c652fc8a075bc814ba1617f5fcf2b)

- **作者**: Rohan Potdar
- **时间**: 2026-08-22T17:16:25Z
- **提交信息**: [ROCm] Ship rocprofiler-sdk 1.3.2 in Dockerfile.rocm_base to fix torch.profiler traces (#53182)

Signed-off-by: Rohan138 <rohanpotdar138@gmail.com>

### [da329cc](https://github.com/vllm-project/vllm/commit/da329cc303a5233e17fa3d553ce0a3d6ceea87a8)

- **作者**: Jens
- **时间**: 2026-08-22T13:34:22Z
- **提交信息**: [Bugfix] Fix speculative decoding for short_conv (LFM2) models (#50272)

Signed-off-by: jens.luecke <jens.luecke@liquid.ai>
Co-authored-by: Tonoken3 <sakamakismile@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [704f12a](https://github.com/vllm-project/vllm/commit/704f12aa1ed66db6307659f2996fd905a73570d4)

- **作者**: Taneem Ibrahim
- **时间**: 2026-08-22T13:01:40Z
- **提交信息**: [Pooling] Report input throughput for batched requests (#53213)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [1070454](https://github.com/vllm-project/vllm/commit/10704541aaf72567fe9d6229b3e3d84d37f2ddba)

- **作者**: Kevin H. Luu
- **时间**: 2026-08-22T10:50:33Z
- **提交信息**: [CI][ARM64] Restore known-good CUDA 13 builder image (#53374)

Signed-off-by: Kevin Luu <51931015+khluu@users.noreply.github.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [040700a](https://github.com/vllm-project/vllm/commit/040700aaa6cae3ef54dad8ba75db1abfb79db449)

- **作者**: Cyrus Leung
- **时间**: 2026-08-22T10:27:59Z
- **提交信息**: [MM] Address comments on #53275 (#53364)

Signed-off-by: DarkLight1337 <tlleungac@connect.ust.hk>

### [0b19ebc](https://github.com/vllm-project/vllm/commit/0b19ebcacd0e9578460206035c4b3575361c19c4)

- **作者**: Cyrus Leung
- **时间**: 2026-08-22T08:49:37Z
- **提交信息**: [MM] Simplify _apply_hf_processor_main (#53275)

Signed-off-by: DarkLight1337 <tlleungac@connect.ust.hk>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-08-23
**监控日期**: 2026-08-22
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 6248
- **最后更新**: 2026-08-22T21:50:11Z

## 提交统计

- **昨日提交总数**: 8
- **提交者数量**: 7
- **主要提交者**: ivanusto, Zhou Taichang, Rahul Steiger

## AI分析总结

# vllm-omni 昨日提交分析

## 一、主要更新类型

本批8个提交以**Bug修复**为主（4个），同时包含**核心功能新增**（2个）、**架构优化**（1个）和**运行时优化**（1个），无文档更新或纯重构提交。

## 二、关键变更点与项目方向的关系

1. **Qwen3-Omni thinker MRoPE编译稳定性修复**：解决多模态模型中旋转位置编码的编译问题，直接提升Qwen3-Omni模型的推理稳定性，与项目"人人可用的多模态模型服务"目标高度一致。

2. **扩散执行失败后GPU内存释放**：修复扩散模型推理异常时的显存泄漏问题，保障长时间服务运行的资源安全，是生产环境稳定性的关键补丁。

3. **流水线采样约束保留**：确保多阶段生成流水线中采样参数不被丢失，对多模态生成质量的一致性至关重要。

4. **异步输出等待边界可配置化**：将等待时间从固定值改为可配置参数并提高默认值，增强系统在高负载场景下的鲁棒性。

5. **单GPU UniProc扩散执行器**：为单GPU环境新增扩散模型执行器，显著降低多模态推理的硬件门槛，直接呼应"为每个人提供"的项目理念。

6. **扩散worker原生分页KV后端**：为扩散模型引入类似LLM的KV缓存管理机制，提升长序列生成效率。

7. **DLO钩子移出区域编译**：修复编译优化与钩子机制的冲突，保证调试和扩展能力不被编译优化破坏。

8. **BF16主机权重运行时产物**：新增BF16精度的权重格式，在保持精度的同时降低显存占用。

## 三、对项目的影响与潜在意义

这批提交集中体现了vllm-omni从"可用"向"好用"过渡的关键阶段。Bug修复类提交（1、2、3、4、7）主要解决生产环境中的稳定性痛点，特别是显存泄漏和编译失败问题，这些是阻碍用户实际部署的主要障碍。功能新增类提交（5、6、8）则从硬件适配、内存管理和精度优化三个维度扩展了系统的适用场景。

## 四、值得关注的技术点

- **UniProc执行器**：单GPU支持扩散模型是重要突破，意味着个人开发者无需多卡集群即可体验多模态推理
- **分页KV后端**：将LLM领域的成熟优化技术迁移至扩散模型，体现了项目技术栈的深度融合
- **BF16主机权重**：在推理精度与资源消耗之间提供了新的平衡点

## 五、对项目发展的影响

结合README所述"Easy, fast, and cheap omni-modality model serving for everyone"的愿景，本批提交从三个维度推动项目前进：**易用性**上，单GPU支持和可配置等待时间降低了使用门槛；**速度**上，分页KV和编译优化提升了推理效率；**成本**上，BF16权重和显存释放机制减少了资源浪费。特别是UniProc执行器的引入，有望将vllm-omni的适用人群从企业级用户扩展到个人开发者，对项目生态的繁荣具有战略意义。整体来看，这批提交标志着项目正稳步走向成熟，为后续更广泛的多模态模型支持奠定了坚实基础。

## 详细提交记录

### [3ad64c6](https://github.com/vllm-project/vllm-omni/commit/3ad64c6a1236dfdeb26354f8e4be72a97a4c1a04)

- **作者**: Zhou Taichang
- **时间**: 2026-08-22T19:42:56Z
- **提交信息**: [Bugfix][Qwen3-Omni] Stabilize thinker MRoPE compilation (#6449)

Signed-off-by: tzhouam <tzhouam@connect.ust.hk>

### [855719e](https://github.com/vllm-project/vllm-omni/commit/855719e3318bcc96ed070a6d331a19532f47c7d0)

- **作者**: hurukawa
- **时间**: 2026-08-22T18:32:48Z
- **提交信息**: [Bugfix] Release GPU memory after diffusion execution failures (#6385)

Signed-off-by: nagisa <1434936049@qq.com>
Signed-off-by: nagisa-kun <1434936049@qq.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [bd4f9ac](https://github.com/vllm-project/vllm-omni/commit/bd4f9acfd30456cb8fa98af53d32f7adc34e03a0)

- **作者**: maithilijoshi20
- **时间**: 2026-08-22T14:57:09Z
- **提交信息**: [Bugfix] Preserve pipeline sampling constraints (#6182)

Signed-off-by: maithilijoshi20 <97733343+maithilijoshi20@users.noreply.github.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [f09bdcb](https://github.com/vllm-project/vllm-omni/commit/f09bdcbc7dc94827e76d4e9479674639be6ac442)

- **作者**: ivanusto
- **时间**: 2026-08-22T14:10:30Z
- **提交信息**: [Bugfix] Make the async-output wait bound configurable and default it higher (#6255)

Signed-off-by: ivanusto <ivanusto@gmail.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [b39f599](https://github.com/vllm-project/vllm-omni/commit/b39f599b09a9ec06cfef05213273de7ed6626b7f)

- **作者**: Rahul Steiger
- **时间**: 2026-08-22T13:58:21Z
- **提交信息**: [Core] Add UniProc diffusion executor for single-GPU (#6308)

Signed-off-by: Rahul Steiger <rsteiger@nvidia.com>
Signed-off-by: Rahul Steiger <rsteiger@aws-cmh-slurm-1-vscode-04.cm.cluster>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>
Co-authored-by: Rahul Steiger <rsteiger@aws-cmh-slurm-1-vscode-04.cm.cluster>

### [72ee535](https://github.com/vllm-project/vllm-omni/commit/72ee535fcde303a4802b9b2e9663fad23d6f7cdb)

- **作者**: Wang  fuyin
- **时间**: 2026-08-22T13:45:45Z
- **提交信息**: [Diffusion] Add native paged KV backend for diffusion workers (#6102)

Signed-off-by: Acerak01-fy <wfy2003324@163.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [c2daa47](https://github.com/vllm-project/vllm-omni/commit/c2daa471c330901e537b6a176dbbce014dbcb307)

- **作者**: Hongsheng Liu
- **时间**: 2026-08-22T13:44:03Z
- **提交信息**: fix: keep DLO hooks outside regional compilation (#6073)

Signed-off-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [493fc64](https://github.com/vllm-project/vllm-omni/commit/493fc6439755101c018e5950a4df39f188aaebdb)

- **作者**: Hongsheng Liu
- **时间**: 2026-08-22T13:37:20Z
- **提交信息**: [Diffusion] Add final-layout BF16 Host Weight Runtime artifacts (#6445)

Signed-off-by: Hongsheng Liu <liuhongsheng4@huawei.com>

---
