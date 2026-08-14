# GitHub Stars 合并报告 - 2026-08-14

**合并日期**: 2026-08-15
**监控日期**: 2026-08-14
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


**报告日期**: 2026-08-15
**监控日期**: 2026-08-14
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2151
- **最后更新**: 2026-08-14T14:46:17Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Bin Jia, Ting

## AI分析总结

### 主要更新类型
本次提交以**工程化与工具链优化**为主，包含CI流程增强（CodeRabbit代码审查集成）和依赖管理调整（uv版本上限放宽），无功能新增或Bug修复。

### 关键变更点及与项目方向的关系
1. **CodeRabbit审查配置**：引入AI驱动的自动化代码审查工具，强化了VeOmni作为“模型中心分布式训练配方库”的协作开发规范。这与项目强调的“可扩展、可复现”理念一致，通过自动化质量门禁保障多模态训练配方（如不同模态组合、并行策略）的代码可靠性。
2. **uv版本上限放宽**：将uv（Python包管理器）的允许版本从<0.12扩展至<0.13，提升了对新工具链的兼容性。这直接服务于项目“分布式训练配方”的快速迭代需求——训练脚本常需依赖最新依赖解析特性，放宽限制可减少环境搭建摩擦。

### 对项目的影响和潜在意义
- **开发效率**：CodeRabbit可自动发现PR中的逻辑缺陷或风格问题，减少人工审查负担，尤其对涉及多文件、多模态配置的复杂提交（如新增训练配方）意义重大。
- **生态兼容性**：uv版本上限放宽降低了开发者因工具版本不匹配导致的安装失败概率，有助于吸引更多社区贡献者复现或扩展训练配方，符合项目“Recipe Zoo”（配方动物园）的开放定位。

### 值得关注的技术点
- **AI审查的上下文感知**：CodeRabbit配置需结合项目特定的训练脚本结构（如并行策略配置、数据加载逻辑）进行规则定制，否则可能产生误报。
- **依赖管理策略**：uv版本上限的“放宽”而非“固定”，体现了项目对快速演进工具链的包容性，但需警惕未来大版本更新可能引入的破坏性变更。

### 对项目发展的影响
VeOmni的核心目标是降低多模态模型训练门槛，而本次提交虽未直接触及训练逻辑，却通过**提升协作效率和工具链稳定性**间接加速了配方库的扩展。CodeRabbit的引入尤其重要——随着配方数量增长，自动化审查将成为维持代码质量、防止“配方冲突”（如不同模态组合的配置错误）的关键基础设施。整体上，这些提交属于“地基加固”型工作，为后续大规模功能迭代（如新模态支持、分布式策略优化）铺平了道路。

## 详细提交记录

### [3d9b967](https://github.com/ByteDance-Seed/VeOmni/commit/3d9b967b29c7ba9c28b67d17d6a275a50dd63ba9)

- **作者**: Bin Jia
- **时间**: 2026-08-14T12:03:41Z
- **提交信息**: [ci] feat: add CodeRabbit review configuration (#1049)

Co-authored-by: Cursor <cursoragent@cursor.com>

### [ccfdf77](https://github.com/ByteDance-Seed/VeOmni/commit/ccfdf778bbfe2236d64c80212302dab63d7ee7a7)

- **作者**: Ting
- **时间**: 2026-08-14T07:38:51Z
- **提交信息**: [misc] chore: widen the uv required-version ceiling to <0.13 (#1047)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-08-15
**监控日期**: 2026-08-14
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2669
- **最后更新**: 2026-08-14T16:44:14Z

## 提交统计

- **昨日提交总数**: 8
- **提交者数量**: 4
- **主要提交者**: Yang Yong (雍洋), helloyongyang, Watebear

## AI分析总结

### 主要更新类型
- **性能优化**：核心方向，包括VAE推理优化、FP8算子融合、SageAttention后端适配。
- **Bug修复**：修复SageAttention在特定硬件（sm120）上的后端问题。
- **配置更新**：更新MUSA（摩尔线程）配置、通用配置及分布式环境初始化。
- **功能增强**：新增VAE块编译、编译兼容的SGL FP8 scaled MM、可配置的SageAttention支持。

### 关键变更点与项目方向
- **MiniMax-H3 VAE推理优化**：通过块编译、FP8 QKV投影融合和SageAttention支持，显著提升视频生成中VAE编解码效率，直接服务于“轻量级视频生成推理”的核心目标。
- **SageAttention修复与配置化**：修复sm120后端问题，并使其支持可配置，增强对不同GPU架构（如Ada Lovelace）的兼容性，扩大硬件适用范围。
- **MUSA配置与分布式环境初始化**：完善对国产GPU（摩尔线程）的支持，并初始化分布式推理环境，为多卡扩展和国产化部署铺路。

### 项目影响与潜在意义
- **推理速度提升**：VAE优化和FP8融合可显著降低延迟，提升视频生成吞吐量，符合“Light”定位。
- **硬件适配扩展**：修复和配置更新使框架能更好支持新GPU架构（sm120）和国产MUSA平台，增强生态兼容性。
- **部署灵活性增强**：分布式环境初始化和可配置后端，便于用户根据硬件资源灵活调整推理方案。

### 值得关注的技术点
- **FP8 scaled MM与QKV融合**：在编译兼容前提下实现FP8量化矩阵乘法，并融合QKV投影，减少内存访问和算子调用开销。
- **VAE块编译**：将VAE网络按块编译，可能结合算子融合或图优化，提升整体执行效率。
- **SageAttention可配置化**：允许用户根据硬件选择不同后端，平衡精度与速度。

### 对项目发展的影响
这些提交紧密围绕“轻量级、高性能、多硬件适配”的路线。通过优化核心VAE模块、修复特定硬件问题、完善国产GPU支持，项目在保持易用性的同时，提升了实际部署的效率和广度。特别是对MiniMax-H3的针对性优化，表明项目正积极适配主流视频生成模型，增强竞争力。分布式环境初始化则为未来大规模推理和云服务部署奠定基础，推动项目向生产级框架演进。

## 详细提交记录

### [205d5c8](https://github.com/ModelTC/LightX2V/commit/205d5c872d01557935dc87d67156f4f94069ea65)

- **作者**: helloyongyang
- **时间**: 2026-08-14T16:43:48Z
- **提交信息**: fix sage

### [c5f8c14](https://github.com/ModelTC/LightX2V/commit/c5f8c14d912cf4b574ba84838fc6a9706588e70c)

- **作者**: helloyongyang
- **时间**: 2026-08-14T16:36:32Z
- **提交信息**: update musa config

### [971d848](https://github.com/ModelTC/LightX2V/commit/971d84850d5a73ddab12e820ce0e82032e6a93c5)

- **作者**: STwangyingrui
- **时间**: 2026-08-14T16:27:09Z
- **提交信息**: fix sageattn backend for sm120 (#1384)

### [d3f3dee](https://github.com/ModelTC/LightX2V/commit/d3f3dee9a3a78d0af3be49c7b2b31f321a32b5ea)

- **作者**: helloyongyang
- **时间**: 2026-08-14T14:49:22Z
- **提交信息**: update config

### [98d928a](https://github.com/ModelTC/LightX2V/commit/98d928a25b888495b758c3d5a0bab0d01041289d)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-08-14T14:19:03Z
- **提交信息**: update warmup (#1382)

### [1903ed9](https://github.com/ModelTC/LightX2V/commit/1903ed95c65888a4539fe46fa098d712366f6b74)

- **作者**: STwangyingrui
- **时间**: 2026-08-14T09:15:33Z
- **提交信息**: Optimize MiniMax-H3 VAE inference (#1381)

Add VAE block compilation, compile-compatible SGL FP8 scaled MM, fused
FP8 QKV projections, and configurable SageAttention support.

### [6cf40b7](https://github.com/ModelTC/LightX2V/commit/6cf40b793a4a512ad3005f9eed36108269113c42)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-08-14T08:09:51Z
- **提交信息**: update (#1380)

### [f11423b](https://github.com/ModelTC/LightX2V/commit/f11423ba5612c29133146fe8cfb5804602b1bcdd)

- **作者**: Watebear
- **时间**: 2026-08-14T07:00:42Z
- **提交信息**: musa: init dist env (#1376)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-08-15
**监控日期**: 2026-08-14
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2197
- **最后更新**: 2026-08-13T10:13:52Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-08-15
**监控日期**: 2026-08-14
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 6160
- **最后更新**: 2026-08-14T22:12:18Z

## 提交统计

- **昨日提交总数**: 11
- **提交者数量**: 10
- **主要提交者**: Yong Wu, Md Saidul Hoque Anik, Jonathan Dierksen

## AI分析总结

# FlashInfer 昨日提交综合分析

## 一、主要更新类型

昨日共11个提交，涵盖**功能新增**（5个）、**性能优化**（1个）、**Bug修复**（1个）、**CI/基础设施改进**（3个）和**代码重构**（1个），整体以功能扩展和工程基建为主。

## 二、关键变更点与项目方向的关系

**核心功能扩展**集中在四个方向：

1. **MLA（多头潜在注意力）支持增强**：新增FP8 KV NoPE MLA在SM90上的支持，允许`head_dim_kpe=0`的零宽度位置键嵌入场景，并引入可选的逐token、逐组`ckv_scale_arr`反量化张量。这直接服务于下游SGLang等推理框架对MLA架构的需求。

2. **MoE（混合专家）体系重构与扩展**：对`flashinfer.moe_ep`的mega-kernel层进行taxonomy/provenance重构，按架构、数据类型和kernel风格重新组织目录结构，并纳入SM90 push-style FP8后端。同时为TRTLLM fused MoE新增unpacked预计算路由支持，兼容标准`(topk_ids, topk_weights)`元组输入。

3. **硬件适配扩展**：为SM107（Blackwell Ultra）启用CUTLASS NVFP4 SVDQuant GEMM编译目标；为BlockSparseAttentionWrapper新增`vsa_sm120_blk64`后端，支持SM120/SM121硬件上的fp16/bf16精度、GQA、block_mask和BSR格式输入，同时将原有后端重命名为`sm100_blk128`和`sm100_blk64`并保留向后兼容别名。

4. **代码清晰化改进**：在`trtllm_ragged_attention_launcher`中显式设置`mMultiCtasKvMode = false`，与paged context路径保持一致，虽是no-op操作但提升了代码可读性。

**性能优化**方面，将SiTU激活函数中的`x / beta`除法替换为`x * (1/beta)`乘法——由于SiTU的beta值（如Kimi-K3的25.0）在FP32下不精确，直接折叠除法不合法，改为在trace时计算倒数再相乘。优化后SiTU性能从与SwiGLU差距巨大（最高60%+）缩小到1-6%以内。

**Bug修复**针对trtllm-gen在长序列多token批量解码时的归约索引错误，修复后解决了vLLM中Gemma 4 31B在投机解码场景下约94%请求输出损坏、吞吐量从6.05降至0.41 req/s的严重问题。

**CI改进**包括：扩展`@flashinfer-bot run`权限至可打标签的协作者、上传H100单元测试JUnit报告（失败时也保留30天）、升级sccache至v0.17.0并保留统计信息以便分析JIT缓存命中率。

## 三、项目影响与潜在意义

- **MLA FP8支持**填补了SM90上FP8 KV与零KPE组合的空白，对DeepSeek等使用MLA架构的模型在Hopper平台上的推理效率有直接提升。
- **MoE重构**建立了清晰的命名规范（如`sm100_fp8_fp4_bf16_deepgemm`），使kernel选择一目了然，为后续新后端接入奠定结构基础。
- **SiTU优化**使Kimi-K3等使用SiTU激活的模型在MoE场景下性能逼近SwiGLU，扩大了FlashInfer的高性能覆盖范围。
- **trtllm-gen修复**解决了多请求批处理下的正确性问题，对生产环境的稳定性和吞吐量恢复意义重大。
- **VSA后端扩展**通过抽取`_vsa_common_checks()`和`_vsa_run_core()`公共辅助函数，消除后端间重复验证和NHD↔BSHD reshape逻辑，降低维护成本；新增测试覆盖精度、GQA、非对称序列长度、LSE、可变块数和per-head mask等场景。

## 四、值得关注的技术点

1. **FP8反量化灵活性**：`ckv_scale_arr`采用物理paged-cache布局`[num_pages, page_size, head_dim_ckv/128]`，与SGLang集成对齐，体现框架间协同设计。
2. **数值精度意识**：SiTU优化中明确指出`1/beta`非精确时不能直接折叠除法，需从FP32 beta推导倒数以保持一致性，展示了对浮点语义的严谨态度。
3. **后端命名规范化**：从模糊的`vsa_blackwell`改为明确的`vsa_sm100_blk128`，体现对硬件架构差异的精确区分；新命名规则区分deep_gemm的`fp8/fp4`与cutedsl的`mx/nvfp4`块缩放格式，输出dtype统一为bf16。
4. **依赖隔离策略**：清理`cute_dsl/sparse/__init__.py`的急切导入，改用运行时直接子模块导入，避免跨后端导入时的依赖冲突。
5. **CI可观测性**：sccache统计通过EXIT hook收集，失败构建也保留证据；JUnit报告在测试失败时仍上传，体现对CI可诊断性的重视。

## 五、对项目发展的影响

FlashInfer作为高性能GPU推理kernel库，本批提交呈现三个发展趋势：**架构覆盖扩展**（SM90 MLA FP8、SM107 SVDQuant、SM120 VSA）、**框架集成深化**（SGLang的MLA布局、vLLM的TRTLLM路由格式、CuTe-DSL版本同步）、**工程成熟度提升**（CI权限治理、缓存统计、测试报告留存、模块化重构与依赖隔离）。特别是MoE重构和SiTU优化表明项目正从"可用"向"极致性能"迈进，而CI改进和代码架构优化则保障了社区协作效率与多后端并行维护的清晰结构——这些共同巩固了FlashInfer作为推理加速基础设施的地位，并为其吸引更广泛的硬件平台用户奠定基础。

## 详细提交记录

### [38ebb15](https://github.com/flashinfer-ai/flashinfer/commit/38ebb1511488e53b6ae55d86bcc07094541faad7)

- **作者**: Xinyuan Tong
- **时间**: 2026-08-14T22:11:15Z
- **提交信息**: feat: support FP8 KV NoPE MLA on SM90 (#4373)

## Description

Allow `BatchMLAPagedAttentionWrapper` to run with `head_dim_kpe=0`,
including FP8 KV caches on SM90.

When the positional-key-embedding dimension is zero, the KPE MMA loop is
empty. The FA2 and FA3 paths initialize the QK accumulator from
compressed KV instead. For FP8 KV, both native backends repack to BF16
and can consume an optional contiguous FP32 scale tensor with one scale
per physical KV token and 128 CKV channels.

This change:

- supports zero-width KPE in FA2 and FA3;
- supports FP8 E4M3 KV with BF16 queries on SM90 for `head_dim_ckv=512`
and `head_dim_kpe` in `{0, 64}`;
- adds optional `ckv_scale_arr` with shape `ckv_cache.shape[:-1] + (4,)`
for per-token, per-group CKV dequantization;
- preserves existing per-tensor `ckv_scale` / `kpe_scale` behavior;
- validates backend, device, dtype, dimensions, scale shape, dtype,
device, and contiguity;
- adds paged-MLA correctness coverage with a non-identity page table for
FA2 and FA3.

## Related Issues

None.

## Pull Request Checklist

- [x] Pre-commit hooks pass on the changed files.
- [x] Tests have been added or updated as needed.
- [x] GPU tests pass.

## Tests

NVIDIA H200, CUDA 12.8, PyTorch 2.11.0+cu128:

- `test_batch_mla_without_kpe`: FA2 and FA3 passed.
- `test_batch_mla_fp8_nope_group_scales_matches_bf16_reference`: FA2 and
FA3 passed.
- `test_fp8_kv_scales_are_keyword_only` and
`test_fp8_kv_requires_scales`: passed.
- Representative existing KPE=64 per-tensor FP8 and row-aliasing
regressions: passed.

## Reviewer Notes

- `ckv_scale_arr` follows the physical paged-cache layout used by the
downstream SGLang integration: `[num_pages, page_size, head_dim_ckv /
128]`.
- Existing BF16/FP16 and FP8 per-tensor scale behavior is unchanged.
- The latest external attention CI failures before this update were not
stable across reruns: HCA failures were classified as pre-existing,
while the new failures alternated between GB200 multi-node NCCL setup
and RTX Pro 6000 `cudaErrorUnknown` failures.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added FP8 batched paged attention with optional per-token/per-channel
CKV scaling.
  * Added support for FA2 and FA3 FP8 execution.
* Expanded supported configurations to include zero- or 64-dimensional
key positional encoding.

* **Bug Fixes**
* Fixed attention computation without key positional encoding
dimensions.
* Added validation for incompatible scale inputs, shapes, layouts, and
configurations.

* **Tests**
  * Added coverage for grouped CKV scaling and trace inputs.
  * Added BF16 reference comparisons across supported implementations.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Lee Nau <lnau@nvidia.com>

### [956c537](https://github.com/flashinfer-ai/flashinfer/commit/956c537c6b5aaeeaab183297ca230549df313c99)

- **作者**: Yong Wu
- **时间**: 2026-08-14T21:51:17Z
- **提交信息**: ci: grant @flashinfer-bot access to collaborators who can apply labels (#4510)

<!-- .github/pull_request_template.md -->

Prior to the patch: `@flashinfer-bot run` only worked for members of the
`ci-users` team. Collaborators who can apply the `run-ci` label by hand
got a :confused: reaction instead, even though both paths trigger the
exact same CI.

The fix is to also grant collaborators who have permission to apply
label the permission to use `@flashinfer-bot run`


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
* Expanded CI authorization to include users with repository triage,
write, maintain, or admin permissions, as well as users who can apply
labels.
* Added automatic cleanup for empty CI runs that obscure testing for the
same commit.
  * Draft pull requests can now be started manually.

* **Bug Fixes**
  * Prevented unrelated label events from cancelling active test runs.
* Improved handling and reporting for earlier active, unsuccessful, or
unavailable CI runs.

* **Documentation**
* Clarified CI trigger permissions, label behavior, command access, and
authorization messages.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [a6dfe70](https://github.com/flashinfer-ai/flashinfer/commit/a6dfe70b7598bb696a402114d9d4c2f6937400c8)

- **作者**: Vincent
- **时间**: 2026-08-14T21:13:34Z
- **提交信息**: gemm: enable CUTLASS NVFP4 SVDQuant on SM107 (#4509)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

Fixes tests/gemm/test_nvfp4_svdquant_gemm.py failures on SM 107 by
extending the support surface of CUTLASS NVFP4 SVDQuant. No kernel
changes are made. We are just adding the SM100f (and SM107 when
supported) compilation targets.

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
* Added support for SVDQuant GEMM operations on compute capability 107
hardware.
  * Enabled NVFP4 SVDQuant GEMM compilation for SM107 devices.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Vincent Tombari <Vinnie6167@users.noreply.github.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [d1fff56](https://github.com/flashinfer-ai/flashinfer/commit/d1fff568eadf0acc06659f1800c9dee62a7e104d)

- **作者**: Md Saidul Hoque Anik
- **时间**: 2026-08-14T20:58:44Z
- **提交信息**: refactor(moe_ep): taxonomy/provenance restructure; incorporate SM90 push-style FP8 backend; sync CuTe-DSL 4.7 quant-staging fix (#4449)

## Summary

Three things: a layout/naming refactor of `flashinfer.moe_ep`'s
mega-kernel layer, the incorporation of the SM90 push-style FP8 backend
(#4069, since merged upstream) as the first new backend added in the
restructured shape, and one vendored-kernel sync that fixes the fused
activation-quant staging crash on CuTe-DSL 4.7 — un-blocking 4.7.x and
lifting the temporary `==4.6.1` pin. The branch is merged up to
upstream/main (2febce55, past the v0.6.17 line and the #4069 squash).
The refactor organizes the layer around two orthogonal views:

1. **Taxonomy (user view)** — backends move to
`backends/mega/kernel/sm<arch>/<act_dtype>_<weight_dtype>_<out_dtype>_<kernel_style>/`,
and registry `kernel_name` strings plus config classes carry the same
fully-qualified names. One glance at a name now tells you the
architecture, the activation/weight/output dtypes, and the kernel style:

   | old kernel_name | new kernel_name | new config class |
   |---|---|---|
| `deep_gemm_mega` | `sm100_fp8_fp4_bf16_deepgemm` |
`Sm100_Fp8_Fp4_Bf16_Deepgemm_MegaMoeConfig` |
| `nvfp4_cutedsl` | `sm100_nvfp4_nvfp4_bf16_cutedsl` |
`Sm100_Nvfp4_Nvfp4_Bf16_Cutedsl_MegaMoeConfig` |
| `mxfp8_cutedsl` | `sm100_mxfp8_mxfp8_bf16_cutedsl` |
`Sm100_Mxfp8_Mxfp8_Bf16_Cutedsl_MegaMoeConfig` |
| `sm90_pull_fp8` | `sm90_fp8_fp8_bf16_pull_cutedsl` |
`Sm90_Fp8_Fp8_Bf16_PullCutedsl_MegaMoeConfig` |
| `sm90_push_fp8` (new, from #4069) | `sm90_fp8_fp8_bf16_push_cuda` |
`Sm90_Fp8_Fp8_Bf16_PushCuda_MegaMoeConfig` |

Naming conventions: deep_gemm dtypes are plain `fp8`/`fp4`, matching
upstream `deep_gemm.fp8_fp4_mega_moe`; the mx/nv prefixes are reserved
for the cutedsl kernels' block-scaled formats. Output dtype is always
bf16 — nvfp4's `combine_dtype` is comm-wire compression, not an output
format.

2. **Provenance (kernel-dev view)** — vendored kernel sources in
`kernel_src/` are keyed by upstream repo snapshot, not by architecture:
`kernel_src/sm100/cutedsl_megamoe` moves to `kernel_src/cutedsl_megamoe`
(the mother repo ships kernels for multiple arches, so an smXX level
misrepresents it). Each drop mirrors the vendor repo layout — `src/`
byte-for-byte upstream, all adaptation in `shim/` — and gains a
`VENDOR.md` recording upstream repo/commit/sync state and pending local
diffs. A new `kernel_src/README.md` states the contract explicitly: **no
edits to `src/` of any kind — including docstrings, comments, and lint
fixes**; tool warnings against vendored files (docstring-coverage gates,
review bots) are handled by excluding the path, never by editing the
file. The sm90 fork trees
(`kernel_src/sm90/pull_style_cutedsl_megakernel` from #4113,
`kernel_src/sm90/push_style_megamoe` from #4069) intentionally stay
separate snapshots — one kernel_src dir = one upstream commit — and fold
into the mother drop if/when upstream merges them.

**Why:** verbatim snapshots must stay diffable against one upstream
commit, and splitting vendored trees per-dtype or per-arch breaks
re-sync; meanwhile users navigate by architecture and dtype, not by
which vendor repo a kernel came from. Putting each concern where its
audience looks resolves the tension. The layout rule is documented in
`docs/design_docs/moe_ep_architecture.md`, and it is what makes new
backend families routine — demonstrated in this very PR by the SM90
push-style incorporation below, and next by the follow-up backend-family
PRs (SM100 BF16 #4386, SM120 MXFP8).

## Directories affected

All changes live under `flashinfer/moe_ep/` plus its tests and docs:

-
`backends/mega/kernel/sm100/{fp8_fp4_bf16_deepgemm,nvfp4_nvfp4_bf16_cutedsl,mxfp8_mxfp8_bf16_cutedsl}/`
and
`backends/mega/kernel/sm90/{fp8_fp8_bf16_pull_cutedsl,fp8_fp8_bf16_push_cuda}/`
— taxonomy backend wrappers (moved/renamed; push_cuda is new).
- `kernel_src/cutedsl_megamoe/` (moved from
`kernel_src/sm100/cutedsl_megamoe/`),
`kernel_src/sm90/pull_style_cutedsl_megakernel/`,
`kernel_src/sm90/push_style_megamoe/` (new) — provenance-keyed vendored
drops, each with `VENDOR.md`; new `kernel_src/README.md` states the
no-edits contract.
- `backends/mega/kernel/tuning.py` + per-backend `tuner.py` files —
tuning machinery moved out of `tune.py` (now a CLI shim).
- `core/kernel/registry.py`, `moe_ep/__init__.py` — deprecated-alias
resolution and re-exports.
- `tests/moe_ep/`, `docs/design_docs/moe_ep_{architecture,runbook}.md`,
`pyproject.toml`/`.pre-commit-config.yaml` excludes, `run_tests.sh` (new
2-GPU `sm90_push` target).

## Test results

- **Full `run_tests.sh` matrix — all 12 targets green** on 4xH100 (job
2389821, 2026-08-13), including the new `sm90_push` Hopper target and
the fault-tolerance suites after the deadlock fixes.
- **B200** (jobs 2388315/2388326): registry/alias smoke, deprecated
aliases, unit x3 green — 396 passed / 72 skipped (push
cpu/packaging/contract tests run; Hopper-marked kernel tests skip).
- **Unit target re-validated green** after the second upstream merge
(job 2389880) and again after the round-2 CodeRabbit fixes (job
2389916), same 396/72 counts, B200.
- **8x B200** (jobs 2384640/2384641/2384650): quant-staging sync matrix
fully green on both dsl 4.6.1 and 4.7.0 (details in the vendored-sync
section below).
- **GB200 + B200**: mxfp8/nvfp4 multirank oracle suites with the
per-cell tolerance band.
- Microbenchmark re-run: no regressions vs pre-restructure reference
numbers (deep_gemm parity; cutedsl kernels at or above their previous
points).
- `pre-commit run -a` fully green at the branch head (e9f791a0).

## SM90 push-style FP8 backend (incorporates #4069)

Ports flashinfer-ai/flashinfer#4069 (head 301f8ce3; since merged to main
as f9b13ef1 — re-diffed, byte-identical, no post-review deltas) onto the
taxonomy/provenance layout, serving as the first proof of the "one
taxonomy backend dir + one provenance-keyed kernel drop" recipe:

- **`kernel_src/sm90/push_style_megamoe/`** — verbatim byte-for-byte
drop from the PR head (`src/{a2a,fp8_gemm}` CUDA sources, `shim/`,
ACKNOWLEDGEMENT.md) plus a `VENDOR.md` provenance record.
- **`backends/mega/kernel/sm90/fp8_fp8_bf16_push_cuda/`** — the five
wrapper files relocated from upstream's flat `kernel/sm90_push_fp8/`,
config renamed to `Sm90_Fp8_Fp8_Bf16_PushCuda_MegaMoeConfig`, registered
with `deprecated_aliases=("sm90_push_fp8",)`.
- **Core deltas carried from the PR:** `mega_layer.py` allocates the
output before `stage_inputs`; pyproject package-data ships the drop's
`.cu`/`.cuh` for non-editable installs; the `isolated_deep_gemm_cache`
conftest fixture; the mega-layer allocation-order regression test.
- **Tests:** the nine sm90_push_fp8 test files (names kept to minimize
re-sync friction) rewritten to the taxonomy. Deviation from upstream:
`run_tests.sh` exposes `sm90_push` as its own 2-GPU Hopper target
instead of folding it into multirank — on non-Hopper nodes the
arch-marked files collect 0 tests and torchrun turns pytest exit 5 into
a failure.

## CuTe-DSL 4.7 quant-staging fix (vendored sync)

The `CUDA_ERROR_MISALIGNED_ADDRESS` crash on cutlass-dsl 4.7.0 — which
presented as a deep_gemm mega multirank failure — was root-caused to the
**fused bf16→quantized activation staging** (`DataPreprocess` in the
vendored cutedsl_megamoe tree), which every mega staging path shares,
deep_gemm's included. The kernel team's fix is synced in as a
single-file partial re-sync per the vendoring policy:

- `kernel_src/cutedsl_megamoe/src/src/inputs_process.py` +
`src/common/host_utils.py` taken **verbatim** from upstream
`bangyus/cutedsl_megamoe @ 50117315d`, recorded in `VENDOR.md` under
pending-diffs (resolves at the next full re-sync). The mxfp8 quant
kernel is reworked so each lane owns one contiguous 16-byte fp8 store
(adjacent lanes reduce the 32-element block amax via
`shuffle_sync_bfly`, even lane writes the E8M0 scale), and `__init__`
gains a hidden-size row-alignment guard.
- Also fixes a stale pre-commit exclude left by the directory move
(`kernel_src/sm100/cutedsl_megamoe` → `kernel_src/cutedsl_megamoe`) so
hooks stop reformatting the verbatim `src/` tree.

Validated on 8x B200 (jobs 2384640/2384641/2384650), full matrix green
on **both** DSL versions:

| section | dsl 4.6.1 | dsl 4.7.0 |
|---|---|---|
| drop's own harness (`python -m src.inputs_process`: bit-exact scales +
SNR vs reference, nvfp4 offline/online + mxfp8) | 3/3 | 3/3 |
| `test_fused_quant_stage.py` | 11/11 | 11/11 |
| mega multirank x4 ranks (deep_gemm + nvfp4 + mxfp8) | 20/rank |
20/rank |
| single-rank kernel-vs-reference oracles | 6/6 | 6/6 |

The deep_gemm multirank suite previously crashed deterministically on
4.7.0; it now passes there. On the strength of this, the runbook's
temporary `==4.6.1` pin is lifted (see the DSL guidance bullet below).

## Also in this PR

- **Per-backend tuners.** `flashinfer/moe_ep/tune.py` becomes a pure CLI
shim (surface unchanged: `python -m flashinfer.moe_ep.tune`);
dtype-specific tuning moves into the backends
(`sm100/{nvfp4,mxfp8}.../tuner.py`), shared sweep machinery (dist
lifecycle, skewed restage, schedule grid, timed sweep tail) into
`backends/mega/kernel/tuning.py`.
- **CUTLASS DSL guidance updated (pin lifted).** The test-container
recipe briefly carried a hard `nvidia-cutlass-dsl==4.6.1` pin because
4.7.0 crashed the mega multirank path; with the crash root-caused and
fixed above, the runbook now allows `-U` installs again. 4.6.1 remains
the perf-validated reference (pin it when producing numbers meant to
compare against the TUNING.md tables); 4.7.0 is correctness-validated.
The library's supported floor remains 4.5.2 (the MR!27 WAR already in
main).
- **Per-cell bf16 term-magnitude tolerance band** for the mxfp8
multirank oracle compares — a principled per-cell bound derived from the
bf16 accumulation term magnitudes, replacing the global rtol that
produced rare single-cell false failures. Validated on GB200 and B200.
- **One-direction import layering rules** codified in the architecture
doc, with all `cutedsl_megamoe` access routed through the drop's
`__init__` rather than deep-path imports.

## Merge with upstream/main and follow-up fixes

The branch is merged up to upstream/main in two steps. First to aaf97df4
(95 commits, incl. the v0.6.17 release line): conflict resolution keeps
the restructure spellings everywhere; upstream's one real kernel advance
in the moved tree — the 4fbac49f singleton-expert TMA-modes fix (#4296)
— is ported onto the renamed paths and recorded in `VENDOR.md`. Notable
upstream picks now in-tree: `BootstrapConfig.device` (#4348) and the
E_local=1 nvfp4 oracle regression test.

Second merge to 2febce55 (13 commits), resolving the conflicts created
when #4069 itself squash-merged upstream (f9b13ef1) with the same moe_ep
files in the pre-restructure flat layout. Every conflict resolves to the
taxonomy spellings (upstream's side is the flat spelling of content this
branch already carries); upstream's flat
`backends/mega/kernel/sm90_push_fp8/` wrapper and its re-folding of
`sm90_push` into the multirank target are dropped in favor of this
branch's layout. The vendored push drop was re-diffed against the merged
SHA: byte-for-byte identical, no post-review deltas (recorded in
`VENDOR.md`).

Post-merge hardening found and fixed by full-suite runs:

- **Merge fallout:** auto-merged regions had re-introduced
pre-restructure `kernel_src.sm100.cutedsl_megamoe` spellings in 12
files, silently skipping entire GPU test files via `importorskip`;
restored, and upstream's re-added flat `sm90_pull_fp8/` wrapper removed.
- **FT test deadlocks (4xH100):** the fault-tolerance multirank test's
evicted victim ran a collective `destroy()` against the survivors'
barrier sequence, deadlocking until the NCCL watchdog — the victim tail
now mirrors the survivors' barrier→destroy→barrier shape. The FT smoke's
survivors now keep forwarding past the kill window so they actually
observe the fault, and `run_tests.sh` judges the smoke by counting
`SMOKE_RESULT` markers (torchrun interleaves lines).
- **Unit-suite crasher isolation:** the long-known in-suite-only
interpreter abort (heap corruption accumulating over the ~200-test
single-process run, firing during a plain module import or in CPython
teardown) is worked around by running the trigger test in its own pytest
process and exiting the unit invocations via `os._exit(pytest_rc)`;
rationale in the runbook, root cause tracked (needs ASAN). All tests
pass — this is process-teardown hygiene, not a kernel bug.

**CodeRabbit review responses.** Two rounds of actionable findings are
fixed in-branch (640b75fb, 57926a98) — highlights from round 2: the push
packaging test's import-boundary gate was building the pre-taxonomy flat
backend path and passing vacuously (fixed, now validates all 5 wrapper
files); the test baseline's weight cache gains weakref eviction;
`cutedsl_megamoe/shim/__main__.py` added so the documented `python -m
...shim` commands resolve; the cutedsl_megamoe `VENDOR.md` provenance
TODOs are filled. Findings inside verbatim-vendored `kernel_src/**/src/`
trees are deliberately not patched locally — they route upstream per the
vendoring policy in `kernel_src/README.md`.

**Lint.** `pre-commit run -a` is fully green (clang-format, mypy, ruff
check/format, whitespace hooks). The final e9f791a0 is a pure
ruff-format pass over 13 moe_ep files — line wraps where the longer
taxonomy class names pushed calls past the limit. The vendored `src/`
trees are untouched by hooks (the exclude set holds).

## Backward compatibility

External callers keep working unchanged — both the old config-class
names and the old kernel_name strings remain as deprecated aliases:

- **Config classes**: `DeepGemmMegaMoeConfig`,
`Nvfp4CutedslMegaMoeConfig`, `Mxfp8CutedslMegaMoeConfig`,
`Sm90PullFp8MegaMoeConfig`, and `Sm90PushFp8MegaMoeConfig` are plain
aliases of the new `Sm<arch>_..._MegaMoeConfig` classes, defined (with a
removal note) in `flashinfer/moe_ep/__init__.py` right below the
taxonomy imports, and still exported via `__all__`.
- **Registry kernel_name strings**: `deep_gemm_mega`, `nvfp4_cutedsl`,
`mxfp8_cutedsl`, `sm90_pull_fp8`, and `sm90_push_fp8` resolve to the
taxonomy backends through the `deprecated_aliases=` parameter of each
backend's `@register_mega_kernel(...)` decoration; the resolution
machinery lives in `flashinfer/moe_ep/core/kernel/registry.py`. Using
one emits a `DeprecationWarning`, and aliases are excluded from the
available-kernels listing.
- Both alias families WILL BE REMOVED in a future release (noted at both
locations above).

## Testing

- Directory moves and renames are behavior-preserving by construction;
registry tests exercise both the taxonomy names and the deprecated
aliases (alias use warns; the kernel listing shows taxonomy names only).
- Full `run_tests.sh` matrix (all 12 targets) green on 4xH100 (job
2389821); B200 unit/registry/alias validation (jobs 2388315/2388326) —
see Test results above.
- The quant-staging sync validated on both dsl 4.6.1 and 4.7.0 (matrix
above); mxfp8/nvfp4 multirank oracle suites validated on GB200 and B200.
- The standalone MoE-EP microbenchmark was re-run against this branch
with no regressions vs the pre-restructure reference numbers (deep_gemm
parity; cutedsl kernels at or above their previous points).

## Relation to other PRs

Re-layering on top of #4113 (SM90 pull-style FP8 backend, merged) and
incorporating #4069 (SM90 push-style FP8 backend, merged upstream
2026-08-12; the vendored drop was re-diffed against the merged SHA
f9b13ef1 and is byte-identical). This is the base branch for the
upcoming backend-family PRs — SM100 BF16 (#4386) and SM120 MXFP8 — each
of which adds one taxonomy backend directory plus one provenance-keyed
kernel drop in the shape this restructure establishes. Both follow-up
branches are already rebased onto this branch's head (unit target green
on each), so they apply as exactly their backend-specific commits once
this merges.

---------

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: coderabbitai[bot] <136622811+coderabbitai[bot]@users.noreply.github.com>
Co-authored-by: Md Anik <mhoqueanik@cw-dfw-cs-001-login-01.cm.cluster>
Co-authored-by: Md Saidul Hoque Anik <mhoqueanik@login-preos01.a51.clusters.nvidia.com>

### [9df0de2](https://github.com/flashinfer-ai/flashinfer/commit/9df0de2ffc12519f2907c6dd528d194a6bcd8e1e)

- **作者**: Julien Debache
- **时间**: 2026-08-14T20:54:17Z
- **提交信息**: feat: unpacked FP8 per-tensor scaling support for TRTLLM fused MoE (#4478)

## 📌 Description

This PR adds unpacked precomputed routing support to
`trtllm_fp8_per_tensor_scale_routed_moe` while preserving the existing
packed
routing format.

Previously, the Python wrapper assumed `topk_ids` was always a packed
tensor.
Passing the standard `(topk_ids, topk_weights)` tuple therefore failed
before
reaching FlashInfer because the wrapper tried to access `dtype` on the
tuple.

The changes:

- Accept either the existing packed `int32` tensor or separate `int32`
expert
  IDs and BF16/FP32 routing weights.
- Propagate the routing input mode and separate routing weights through
the
  Python custom op and C++ launcher.
- Borrow unpacked routing tensors directly and select the correct
routing-weight
  dtype instead of constructing the packed representation.
- Reuse the common fused-MoE execution path for packed, unpacked, and
  logits-based routing.
- Preserve packed-format behavior, including the launcher-owned BF16
routing
  weight buffer.
- Convert unpacked FP32 weights to a launcher-owned BF16 token-scale
buffer only
for Llama4 routing, where the available per-tensor FP8 GEMM cubins
require
BF16 routing scales on the GEMM1 input. The original FP32 routing
weights are
  retained for the normal routing/finalization contract.
- Enable unpacked routing in the unified per-tensor FP8 runner and
configure its
  autotuning path consistently for Llama4 per-token scaling.

## 🔍 Related Issues

Supports merging https://github.com/vllm-project/vllm/pull/46872.

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

Validation performed:

- Packed and unpacked-FP32 public per-tensor FP8 routed-MoE parity
tests.
- Unified runner coverage for logits, packed, and unpacked routing.
- Llama4 unpacked-FP32 correctness test.
- Llama4 unpacked-FP32 CUDA graph capture and replay test.

## Reviewer Notes

Please focus on the Llama4-specific conversion. Unpacked FP32 routing
weights
are consumed directly by the normal per-tensor FP8 routing/finalization
path.
Llama4 additionally uses those weights as GEMM1 token scales, while the
currently shipped scale-only E4M3 GEMM cubins expect BF16 token scales.
The
conversion is therefore limited to that combination and does not add
overhead
to ordinary unpacked routing.

The packed API remains supported and follows its existing
internal-buffer path.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added support for unpacked precomputed routing with separate expert
IDs and weights in FP8 routed MoE operations.
* Expanded Llama4 routing support with per-token scaling and FP32
routing-weight conversion.
  * Added validation for routing formats and expert-index types.

* **Bug Fixes**
  * Improved handling and reuse of caller-provided routing weights.

* **Tests**
* Expanded coverage for packed and unpacked routing, CUDA graph replay,
and Llama4 scenarios.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: jdebache <jdebache@nvidia.com>

### [3f5acea](https://github.com/flashinfer-ai/flashinfer/commit/3f5acea9cf8a738724f7a07b4d8b1ae4a4fa25e5)

- **作者**: sychen52
- **时间**: 2026-08-14T20:39:52Z
- **提交信息**: perf(moe): fold the SiTU beta reciprocal in the CuTe DSL MoE epilogue (#4506)

`x / beta` in the SiTU gate and up branches lowers to a per-element
`div.rn.f32`: folding it to `x * (1/beta)` is only legal when `1/beta`
is
exact, which the SiTU betas (e.g. Kimi-K3's 25.0) are not.  Compute the
reciprocal at trace time and multiply instead.

`f32_reciprocal` derives it from the fp32 beta the kernel multiplies
back in,
so `x * inv_beta` stays consistent with `x / beta_f32`; taking the
reciprocal
of the unrounded Python float can differ by 1 ulp when beta is not
fp32-exact.

Kimi-K3 MoE (E=896, topK=16, hidden=3584, intermediate=3072) on one B200
at
1000 W, NVFP4, pre-routed, autotuned, microseconds, best of 3 repeats of
50 timed iters:

| tokens | 1 | 8 | 64 | 512 | 2048 | 4096 | 8192 |
|---|---|---|---|---|---|---|---|
| SiTU before | 123 | 673 | 3167 | 4744 | 4779 | 4845 | 7826 |
| SiTU after | 77 | 363 | 1734 | 2702 | 2914 | 3011 | 4992 |
| SwiGLU | 75 | 360 | 1724 | 2677 | 2761 | 2998 | 4361 |

SiTU now lands within 1-6% of SwiGLU on the same kernel through 4096
tokens.

`pytest tests/moe/test_cute_dsl_fused_moe.py -k situ` is unchanged (7
passed,
2 failed; both failures pre-exist on main)
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

- [ ] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

## Summary by CodeRabbit

* **Performance**
* Improved SiTU activation calculations by replacing repeated division
with precomputed reciprocal multiplication.
* Optimized both vectorized and scalar calculation paths while
preserving existing behavior.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [4757ebc](https://github.com/flashinfer-ai/flashinfer/commit/4757ebcf9784172c0c0e55f36fbcd22026d5cebd)

- **作者**: Jonathan Dierksen
- **时间**: 2026-08-14T20:24:39Z
- **提交信息**: ci: upload GitHub unit-test JUnit reports (#4488)

## Summary

- upload the H100 unit-test JUnit XML even when the test step fails
- retain reports for 30 days for later analysis
- warn when an early failure prevents XML generation

The A10G and T4 jobs still run legacy scripts that do not generate JUnit
XML, so this only uploads reports from the H100 sharded runner.

## Validation

- pre-commit hooks passed
- git diff --check
- parsed .github/workflows/pr-test.yml with PyYAML

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Tests**
* Test results from H100 matrix runs are now uploaded as downloadable
JUnit XML artifacts, including for failed or cancelled runs.
* Test artifacts are retained for 30 days, with warnings shown when
result files are unavailable.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [4fa40ae](https://github.com/flashinfer-ai/flashinfer/commit/4fa40aeea3b8c2c408da5fe5139bed43fb482c6f)

- **作者**: Jhao-Ting Chen
- **时间**: 2026-08-14T18:06:46Z
- **提交信息**: fix: correct trtllm-gen reduction indexing for FMHA decode at long q_len (#4382)

## 📌 Description

Fix two trtllm-gen reduction indexing errors in multi-token batch
decode:

- Index Q/O by the packed request offset.
- Derive causal KV extent from the CTA's last valid query token.

Thanks to @Dymasik for discovering the bug and providing the original
patch.

### Observed vLLM failure

With Gemma 4 31B, MTP `num_speculative_tokens=5` (`q_len_per_req=6`), a
~26k-token context, and batch size greater than one, requests after the
first receive corrupted attention output. This produces incorrect logits
at the first speculative verification step; affected generations repeat
one token, never emit EOS, and run to `max_tokens`. At batch size 4,
about 94% of requests were affected and throughput dropped from 6.05 to
0.41 req/s. Batch size 1 remains correct.

### Standalone Python reproduction

This requires one SM100/SM103 GPU and no model weights. Identical
queries and KV caches are used for every request, then compared with a
PyTorch reference. The failure begins at `q_len_per_req >= 5`;
`q_len_per_req=4` is included as a passing control.

```python
import torch
from flashinfer.decode import trtllm_batch_decode_with_kv_cache

DEV, DTYPE = "cuda", torch.bfloat16
HEAD_DIM, NUM_QO, NUM_KV, PAGE = 512, 8, 1, 16


def build(num_reqs, q_len, seq_len):
    torch.manual_seed(1234)
    pages = (seq_len + PAGE - 1) // PAGE
    kv_one = (
        torch.randn(
            pages, 2, NUM_KV, PAGE, HEAD_DIM, dtype=DTYPE, device=DEV
        )
        / 4
    )
    kv_cache = kv_one.repeat(num_reqs, 1, 1, 1, 1).contiguous()
    block_tables = (
        torch.arange(num_reqs * pages, dtype=torch.int32, device=DEV)
        .view(num_reqs, pages)
        .contiguous()
    )
    seq_lens = torch.full(
        (num_reqs,), seq_len, dtype=torch.int32, device=DEV
    )
    q_one = (
        torch.randn(q_len, NUM_QO, HEAD_DIM, dtype=DTYPE, device=DEV) / 4
    )
    query = q_one.repeat(num_reqs, 1, 1).contiguous()
    return query, kv_cache, block_tables, seq_lens


def reference(num_reqs, q_len, seq_len):
    query, kv_cache, block_tables, _ = build(num_reqs, q_len, seq_len)
    group = NUM_QO // NUM_KV
    pos = torch.arange(seq_len, device=DEV)
    qpos = seq_len - q_len + torch.arange(q_len, device=DEV)
    mask = pos[None, :] > qpos[:, None]
    out = torch.empty(
        num_reqs,
        q_len,
        NUM_QO,
        HEAD_DIM,
        dtype=torch.float32,
        device=DEV,
    )
    for r in range(num_reqs):
        g = kv_cache[block_tables[r].long()].float()
        k = g[:, 0].permute(1, 0, 2, 3).reshape(NUM_KV, -1, HEAD_DIM)[
            :, :seq_len
        ]
        v = g[:, 1].permute(1, 0, 2, 3).reshape(NUM_KV, -1, HEAD_DIM)[
            :, :seq_len
        ]
        k = k.repeat_interleave(group, 0)
        v = v.repeat_interleave(group, 0)
        q = query[r * q_len : (r + 1) * q_len].float().transpose(0, 1)
        scores = torch.bmm(q, k.transpose(1, 2)) * HEAD_DIM**-0.5
        scores = scores.masked_fill(mask[None], float("-inf"))
        out[r] = torch.bmm(torch.softmax(scores, -1), v).transpose(0, 1)
    return out


def kernel(num_reqs, q_len, seq_len, workspace):
    query, kv_cache, block_tables, seq_lens = build(
        num_reqs, q_len, seq_len
    )
    return trtllm_batch_decode_with_kv_cache(
        query=query,
        kv_cache=kv_cache,
        workspace_buffer=workspace,
        block_tables=block_tables,
        seq_lens=seq_lens,
        max_seq_len=seq_len,
        bmm1_scale=HEAD_DIM**-0.5,
        bmm2_scale=1.0,
        window_left=-1,
        kv_layout="HND",
        backend="trtllm-gen",
        q_len_per_req=q_len,
    ).view(num_reqs, q_len, NUM_QO, HEAD_DIM).float()


print(
    f"{'seq_len':>8} {'q_len':>6} {'batch':>6} {'call':>5}  "
    "max abs error per request"
)
for seq_len, q_len, batch in [
    (26121, 6, 4),
    (26121, 5, 4),
    (26121, 4, 4),
]:
    ref = reference(batch, q_len, seq_len)
    # vLLM reuses one global workspace across layers and steps.
    workspace = torch.zeros(
        256 * 1024 * 1024, dtype=torch.int8, device=DEV
    )
    for call in range(2):
        got = kernel(batch, q_len, seq_len, workspace)
        errors = [
            (got[r] - ref[r]).abs().max().item() for r in range(batch)
        ]
        formatted = ", ".join(
            "nan" if value != value else f"{value:.4f}"
            for value in errors
        )
        print(
            f"{seq_len:>8} {q_len:>6} {batch:>6} {call:>5}  "
            f"{formatted}"
        )
```

On the unpatched build, request 0 stays correct while requests 1-3 fail
for `q_len_per_req=5` and 6, with errors ranging from ~5e-3 to NaN.
`q_len_per_req=4` stays correct. With this patch, all three
configurations match the reference (maximum error <= 1e-4).

### Unit-test coverage

`test_trtllm_batch_decode_reduction_indexing` uses `q_len_per_req=6` and
covers both fixes in one SM100/SM103 test:

- `packed_qo_offset`: four 4096-token requests with identical Q/K/V
detect the padded per-request Q/O offset. Reverting only the first fix
causes 24.1% mismatched elements and NaNs.
- `causal_kv_extent`: variable sequence lengths `[2052, 8192]`, zero
Q/K, and 128-token-tile-coded V deterministically expose a missing
reduction contribution. Reverting only the second fix causes 8.3%
mismatched elements with maximum absolute error 0.03125.

The test passes when both fixes are present.

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

## Reviewer Notes

Validated on B300: the targeted regression test passes with both fixes
and fails independently when either fix is reverted. Ruff format/check
also pass.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Improved attention reduction indexing for variable-length and packed
sequences.
* Corrected causal key/value length adjustments to use the final token
processed by each block.

* **Tests**
* Added regression coverage for batch decode reduction indexing on
supported hardware.
* Validates packed offsets and causal tile handling against a reference
implementation.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Jhao-Ting Chen <jhaotingc@nvidia.com>

### [23382fd](https://github.com/flashinfer-ai/flashinfer/commit/23382fd6ddcefad7449e7a6d9bb2d8c5d86d094b)

- **作者**: Jonathan Dierksen
- **时间**: 2026-08-14T15:28:35Z
- **提交信息**: ci: upgrade sccache and retain stats (#4505)

## Summary

- pin the JIT-cache build helper to [sccache
v0.17.0](https://github.com/mozilla/sccache/releases/tag/v0.17.0) for
both x86_64 and aarch64 builds
- collect text, JSON, and advanced JSON stats from an EXIT hook so
failed builds retain evidence without changing their exit status
- add a dedicated `Display sccache stats` workflow step to each nightly,
release, and PR AOT matrix job that enables sccache
- retain safe cache/build metadata, including cache mode, key prefix,
source SHA, CUDA architecture list, container tag, and pulled image
digest
- upload the stats and metadata with `if: always()` for later comparison

## Motivation

The nightly JIT-cache jobs are reporting unexpectedly low hit rates. The
existing `::group::sccache stats` markers were valid and GitHub rendered
them as a foldable section, but that section was buried near the end of
a roughly 294,000-line container-build step. A separate workflow step
makes the final stats immediately visible in the job step list, while
machine-readable artifacts make runs easy to compare later.

The v0.17 client-side execution mode remains disabled because it is
opt-in; this keeps the version upgrade separate from an execution-mode
change. Full sccache debug logging is intentionally not enabled to avoid
runtime, artifact-size, and credential-exposure risk.

## Artifact contents

- `sccache-stats.txt`
- `sccache-stats.json`
- `sccache-advanced-stats.json`
- `sccache-metadata.txt`
- `job-metadata.txt`

Artifacts are retained for 14 days and are uploaded on both success and
failure.

## Validation

- verified official v0.17.0 Linux musl archives and checksum assets for
x86_64 and aarch64
- exercised setup, metadata, text/JSON/advanced stats, secret exclusion,
and EXIT collection with a mocked sccache lifecycle
- confirmed the stats-only path does not set `SCCACHE_LOG` or
`SCCACHE_ERROR_LOG` and does not create a debug-log artifact
- `bash -n` on all changed shell scripts
- YAML parsing on all changed workflows
- actionlint v1.7.12, filtering only the repository baseline shellcheck
and custom self-hosted runner-label diagnostics
- repository pre-commit hooks on all changed files
- `git diff --check`

A real CUDA JIT-cache build was not run locally; the workflow matrix
will provide that behavioral validation.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added build diagnostics capturing cache statistics and build
environment metadata.
* Build and test artifacts now include diagnostic reports retained for
14 days.

* **Bug Fixes**
  * Diagnostic collection now runs even when builds fail or exit early.
  * Collection failures no longer change the original build result.
  * Added warnings when cache statistics are unavailable.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [750dbfd](https://github.com/flashinfer-ai/flashinfer/commit/750dbfd54267384b36c6cfd85ee1e01ce5c30ddd)

- **作者**: hsr1234563
- **时间**: 2026-08-14T09:49:15Z
- **提交信息**:  integrate SM120 VSA (Video Sparse Attention) block-sparse backend (#4259)

- Add vsa_sm120_blk64 backend to BlockSparseAttentionWrapper
(SM120/SM121)
  supporting fp16/bf16, GQA, block_mask and BSR indptr/indices inputs
- Rename blk128/ → sm100_blk128/ and blk64/ → sm100_blk64/ for clarity;
  rename backend strings vsa_blackwell → vsa_sm100_blk128 and
  vsa_blackwell_blk64 → vsa_sm100_blk64 with backward-compat aliases
- Extract _vsa_common_checks() and _vsa_run_core() helpers to eliminate
  duplicate validation and NHD↔BSHD reshape logic across backends
- Move shared to_cute_tensor() to bsa_utils/cute_tensor_utils.py so
SM120
  can import it without pulling in SM100's quack dependency
- Clear cute_dsl/sparse/__init__.py eager imports; use direct submodule
  imports in run() to avoid cross-backend dependency at import time
- Add tests/attention/test_vsa_block_sparse_sm120.py covering accuracy,
  GQA, asymmetric seqlen, LSE, variable block counts, per-head mask

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

* **New Features**
* Added SM100 and SM120 block-sparse attention backends for supported
NVIDIA architectures.
* Added variable KV block counts, variable block sizes, GQA/MQA, block
masks, and optional log-sum-exp outputs.
* Added optimized fused forward paths for 64- and 128-token sparse
blocks.
* **Bug Fixes**
* Improved architecture, input, and configuration validation with
clearer errors.
  * Updated CUDA compatibility handling.
* **Refactor**
* Standardized sparse attention backend names while retaining legacy
aliases.
  * Improved backend dispatch and compilation support.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: root <root@smc521ge-0036.ipp2a2.colossus.nvidia.com>
Co-authored-by: Claude Sonnet 4.6 (1M context) <noreply@anthropic.com>
Co-authored-by: root <root@smc521ge-0038.ipp2a2.colossus.nvidia.com>
Co-authored-by: root <root@smc521ge-0039.ipp2a2.colossus.nvidia.com>
Co-authored-by: root <root@umbriel-b200-017.ipp4a1.colossus.nvidia.com>

### [555492e](https://github.com/flashinfer-ai/flashinfer/commit/555492e2bc6e6dabdba1b46eeceb6d52be479cf1)

- **作者**: namgyu-youn
- **时间**: 2026-08-14T07:42:02Z
- **提交信息**: chore: explicitly set mMultiCtasKvMode in ragged attention launcher (#3469)

<!-- .github/pull_request_template.md -->

## 📌 Description

Explicitly set `mMultiCtasKvMode = false` in
`trtllm_ragged_attention_launcher` for clarity, matching the paged
context path. Confirmed this is a no-op: `TllmGenSelectKernelParams`
already forces `Disabled` for `Context`-type kernels regardless of this
field, and the struct is zero-initialized by default anyway.

## 🔍 Related Issues

Closes #2409

## 🚀 Pull Request Checklist

- [x] `pre-commit install`
- [x] `pre-commit run --all-files`

## 🧪 Tests

- [x] `pytest tests/attention/` with `is_causal=False` ragged attention
cases


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

## Summary by CodeRabbit

* **Bug Fixes**
* Improved parameter handling for ragged attention during context
processing.
* Enhanced inference stability by ensuring attention execution uses a
compatible key-value processing mode.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-08-15
**监控日期**: 2026-08-14
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3942
- **最后更新**: 2026-08-14T22:19:00Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-08-15
**监控日期**: 2026-08-14
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34314
- **最后更新**: 2026-08-14T14:56:30Z

## 提交统计

- **昨日提交总数**: 9
- **提交者数量**: 5
- **主要提交者**: apolinário, Sayak Paul, dependabot[bot]

## AI分析总结

# 提交分析总结

## 主要更新类型

本批次提交以**Bug修复**和**测试改进**为主，辅以**依赖更新**和**功能增强**。

## 关键变更点

1. **测试稳定性修复**：修复Qwen测试在CI中的内存溢出问题，以及T5模型测试改用`eval()`模式确保结果确定性。这反映了项目对测试可靠性的持续投入。

2. **LoRA测试警告修复**：修复因PEFT重构导致的意外键警告逻辑失效问题，通过移除adapter名称检查并精确化`lora_`匹配模式，确保与PEFT新旧版本兼容。

3. **MiniMax-H3 LoRA加载支持**：这是本批次最实质的功能增强，新增对MiniMax-H3模型的LoRA适配器加载能力，覆盖多种第三方LoRA布局格式，并处理了alpha缩放因子的元数据读取逻辑。

4. **ROCm FlashAttention优化**：改用Hub内核替代直接依赖`aiter`包，简化依赖管理并提升ROCm平台兼容性。

5. **依赖更新**：flux-control示例的transformers依赖从4.47.0升级至5.5.0。

6. **测试拆分**：将模块化pipeline测试拆分，提升测试组织性和可维护性。

## 对项目的影响和意义

- **生态兼容性增强**：MiniMax-H3 LoRA支持扩展了模型生态，吸引更多第三方适配器创作者；PEFT兼容性修复确保与上游库同步演进。
- **平台覆盖扩大**：ROCm FlashAttention优化降低AMD GPU用户使用门槛。
- **工程质量提升**：测试稳定性和拆分改进减少CI噪音，提升开发效率。

## 值得关注的技术点

- **LoRA alpha元数据读取**：从文件`__metadata__`读取训练时的alpha值，解决无标量文件导致的强度错误问题，这是对LoRA加载逻辑的精细化处理。
- **PEFT重构适配**：针对上游重构导致的键匹配逻辑变化，采用更精确的`.lora_`匹配策略。
- **Hub内核替代**：通过Hub分发内核减少直接依赖，是依赖管理的最佳实践。

## 对项目发展的影响

这些提交体现了diffusers作为**多模态生成模型统一框架**的定位：一方面通过LoRA支持扩展模型适配能力，强化其作为社区生态枢纽的角色；另一方面通过测试和依赖管理优化，维持大规模项目在快速迭代中的稳定性。对ROCm的支持则反映了项目对多元化硬件生态的重视，有助于扩大用户基础。整体上，这些变更巩固了diffusers在生成式AI工具链中的核心地位。

## 详细提交记录

### [90b4e34](https://github.com/huggingface/diffusers/commit/90b4e34e79a86ec5e7f2437634fe95ecd2108796)

- **作者**: Sayak Paul
- **时间**: 2026-08-14T12:25:33Z
- **提交信息**: tests: fix qwen tests from getting oom'd in our CI. (#14474)

### [69a0d5a](https://github.com/huggingface/diffusers/commit/69a0d5a52b43f257ae73a3015761425f2bf53f4d)

- **作者**: Sayak Paul
- **时间**: 2026-08-14T12:25:26Z
- **提交信息**: [tests] use eval() on t5 for deterministic results. (#14472)

* use eval() on t5 for deterministic results.

* fix wan

### [ea129f3](https://github.com/huggingface/diffusers/commit/ea129f30ed6d7af2911ded1261df8f4717a76974)

- **作者**: Benjamin Bossan
- **时间**: 2026-08-14T12:25:21Z
- **提交信息**: FIX LoRA tests warning about unexpected keys (#14476)

Resolves https://github.com/huggingface/peft/issues/3548.

The issue appeared after merging
https://github.com/huggingface/peft/pull/3490 in PEFT. As part of a
side effect of that refactor, the adapter name is not part of the
state dict keys in the reported mismatches. The warning logic did,
however, check for the adapter name, resulting in the warning not
being emitted.

The fix simply drops the adapter name from the check for unexpected
keys. This should be safe, because we only load one adapter at a time,
so unexpected keys should not report on other adapters anyway.

While working on this function, I also changed the "lora_" in k check
to ".lora_" in k. This should be strictly more precise, but it's not
related to the fix. I also added some type annotations for good
measure.

The tests now pass with both PEFT from source and the latest PEFT
release (i.e. before the refactor merge).

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

### [4dea855](https://github.com/huggingface/diffusers/commit/4dea8550916738aa8c96f206ba3ed7709830840a)

- **作者**: dependabot[bot]
- **时间**: 2026-08-14T10:25:41Z
- **提交信息**: Bump transformers from 4.47.0 to 5.5.0 in /examples/flux-control (#14179)

Bumps [transformers](https://github.com/huggingface/transformers) from 4.47.0 to 5.5.0.
- [Release notes](https://github.com/huggingface/transformers/releases)
- [Commits](https://github.com/huggingface/transformers/compare/v4.47.0...v5.5.0)

---
updated-dependencies:
- dependency-name: transformers
  dependency-version: 5.5.0
  dependency-type: direct:production
...

Signed-off-by: dependabot[bot] <support@github.com>
Co-authored-by: dependabot[bot] <49699333+dependabot[bot]@users.noreply.github.com>

### [4c963d9](https://github.com/huggingface/diffusers/commit/4c963d9b81eca698382c881e3930a62d4fbefb1a)

- **作者**: Sayak Paul
- **时间**: 2026-08-14T10:14:57Z
- **提交信息**: Revert "svd failures."

This reverts commit 875cccb3f5b03910962e10a629a705606c8d0f60.

### [875cccb](https://github.com/huggingface/diffusers/commit/875cccb3f5b03910962e10a629a705606c8d0f60)

- **作者**: Sayak Paul
- **时间**: 2026-08-14T10:14:26Z
- **提交信息**: svd failures.

### [102c249](https://github.com/huggingface/diffusers/commit/102c24934fe1705e6caaadb03789b0f2542fd8a9)

- **作者**: Sayak Paul
- **时间**: 2026-08-14T09:54:01Z
- **提交信息**: split up tests in modular pipelines (#14444)

* notes from .ai

* ltx2

* cover the remaining tests

* fixes

### [8222302](https://github.com/huggingface/diffusers/commit/8222302f0340744fdc71e85362d76f7b8ccd8ae6)

- **作者**: BADAOUI Abdennacer
- **时间**: 2026-08-14T08:39:23Z
- **提交信息**: [FA2] Use `kernels-community/aiter-flash-attn-ck` Hub kernel for ROCm FlashAttention (drop `aiter` dependency) (#14436)

Use  Hub kernel

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

### [8c3dcd6](https://github.com/huggingface/diffusers/commit/8c3dcd6da10668bff6c0d51fc00e010c7b0b2ed7)

- **作者**: apolinário
- **时间**: 2026-08-14T07:50:12Z
- **提交信息**: Add LoRA loading support for MiniMax-H3 (#14408)

* Add LoRA support for MiniMax-H3

* Address review: Copied-from loader, LoRA badge, docstring caveats, drop generic scale test

* Move the MiniMax-H3 LoRA tests to tests/lora

* Support the remaining published MiniMax-H3 LoRA layouts

Three more published H3 LoRAs did not load. Two were key-layout gaps and the
third was the reason neither was noticed: a layout that reaches no module at
all used to return without an exception.

- musubi-tuner writes one flattened `lora_unet_` name per module. It is
  un-flattened against the H3 module vocabulary, since `qkv_proj`,
  `token_refiner`, `final_layer` and the output heads carry underscores that
  are not path separators, and then goes through the existing kohya path.
- one producer publishes its own converter's output: diffusers module names
  with peft's `.default.` infix left in and no component prefix. The infix is
  dropped and the prefix added.
- a state dict that filters to nothing in both partitions now warns instead of
  loading as a silent no-op, in the wording `load_lora_adapter` uses for the same
  situation.

A fourth loaded, but at the wrong strength. One producer ships no `.alpha` scalars
and records the alpha it trained with in the file's own `__metadata__` instead,
under `alpha`. Its 8-step turbo LoRA pairs that entry's 8 with rank 128, an
effective scale of 0.0625, so synthesizing `alpha == rank` applied the adapter 16x
too strong. That entry is now read as the uniform network alpha. Per-module scalars
still win when a file carries both, since the converter has already folded them into
the weights, and a non-numeric value is warned about and ignored. `__metadata__` only
exists on a file, so `_fetch_state_dict` hands it back on request.

* Simplify the MiniMax-H3 LoRA comments

* Trim the MiniMax-H3 LoRA tests to loading and effectiveness

* Reference the alpha convention in the MiniMax-H3 LoRA docstring

* Drop a redundant format comment

* Test only diffusers-written state dicts

* Rely on get_peft_kwargs for alpha-less files

* Drop the peft version guards after the main cleanup

---------

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-08-15
**监控日期**: 2026-08-14
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


**报告日期**: 2026-08-15
**监控日期**: 2026-08-14
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12938
- **最后更新**: 2026-08-14T13:17:48Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 2
- **主要提交者**: Zhongjie Duan, wentao tao

## AI分析总结

### 主要更新类型  
本次提交包含**文档更新**、**Bug修复**和**示例更新**三类，无重大功能新增或架构重构。

### 关键变更点及与项目方向的关系  
1. **文档澄清（#1591）**：明确Diffutoon示例的版本要求，降低用户因版本不匹配导致的配置错误，提升项目易用性。  
2. **MPS内存问题修复（#1599）**：针对Apple Silicon（MPS后端）的内存泄漏或溢出问题，保障Mac用户的使用体验，扩大跨平台兼容性。  
3. **Minimax-H3示例更新（#1598）**：同步最新模型接口或参数，确保示例与当前代码库一致，维持教程的时效性。

### 对项目的影响和潜在意义  
- **稳定性提升**：MPS修复直接解决特定硬件环境下的崩溃风险，增强用户信任。  
- **生态完善**：示例更新和文档澄清降低了新用户的上手门槛，促进社区采用。  
- **维护健康度**：及时响应issue（#1591/#1598/#1599），体现项目活跃维护状态，吸引更多贡献者。

### 值得关注的技术点  
- **MPS内存管理**：修复可能涉及PyTorch MPS后端的显存分配策略或张量生命周期优化，对依赖Apple硬件的创意工具类项目尤为关键。  
- **示例版本锁定**：文档中明确版本号，暗示项目对依赖版本敏感，未来可能引入自动化版本校验机制。

### 对项目发展的影响  
DiffSynth-Studio定位为**多模态创意生成工具**（如视频、图像风格化），其核心价值在于“易用+跨平台”。本次提交虽小，但通过修复Mac端稳定性、更新前沿模型（Minimax-H3）示例，直接强化了“开箱即用”的承诺，并紧跟生成式AI模型迭代趋势。这有助于巩固其在Trendshift榜单中的热度，吸引更多非专业用户和研究者，为后续功能扩展（如更多模型集成）奠定用户基础。整体上，这些提交是项目在成熟期“精雕细琢”的体现，而非扩张性开发。

## 详细提交记录

### [6343ded](https://github.com/modelscope/DiffSynth-Studio/commit/6343deda06b3e09efc9b1ce23c135c35a341d143)

- **作者**: wentao tao
- **时间**: 2026-08-14T08:06:44Z
- **提交信息**: docs: clarify Diffutoon example version (#1591)

### [971f54f](https://github.com/modelscope/DiffSynth-Studio/commit/971f54feab9015bea8c3ba8facc1dc9f17acbb67)

- **作者**: Zhongjie Duan
- **时间**: 2026-08-14T07:47:47Z
- **提交信息**: fix mps memory issue (#1599)

### [1978fcf](https://github.com/modelscope/DiffSynth-Studio/commit/1978fcfe6c51395516cc49cd098257caf39a6129)

- **作者**: Zhongjie Duan
- **时间**: 2026-08-14T07:41:54Z
- **提交信息**: update minimax-h3 examples (#1598)

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-08-15
**监控日期**: 2026-08-14
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 31815
- **最后更新**: 2026-08-14T22:22:36Z

## 提交统计

- **昨日提交总数**: 28
- **提交者数量**: 23
- **主要提交者**: Ke Bao, zijiexia, chilltongx

## AI分析总结

# SGLang 昨日提交分析报告

## 一、主要更新类型

本次提交涵盖多种类型：**Bug修复**（约10项）、**性能优化**（约6项）、**文档更新**（约5项）、**功能新增**（约4项）、**架构重构**（约3项）。

## 二、关键变更点与项目方向

1. **推理模型压缩技术**：新增Reasoning-Aware Compression (RAC)剪枝方案，针对推理模型（如DeepSeek-R1类）的思维链特性优化压缩策略，与SGLang服务推理模型的定位高度契合。

2. **TorchAO集成移除**：彻底移除`--torchao-config`配置，简化依赖链。这是架构精简决策，可能因维护成本或生态整合考虑，需关注后续量化方案的替代路径。

3. **MoE架构深度优化**：包括H200 Triton配置、swiglu MoE上投影融合、MiniMax-M3共享/路由专家重叠执行，持续强化MoE推理效率，符合SGLang高性能推理的核心目标。

4. **新模型支持**：新增Qwen3.8-27B/GLM-5.2/MiniMax-H3等模型的部署文档与基准测试，保持对前沿模型快速适配的节奏。

5. **扩散模型修复**：多项针对Helios去噪、cache-DiT BCG警告的修复，表明SGLang正扩展至扩散模型推理领域。

## 三、对项目的影响与意义

- **性能提升**：FlashInfer fused top-k、EPD批量拷贝、WAR事件发布等优化，直接降低推理延迟，增强竞争力。
- **稳定性增强**：修复MTP启动、Mamba检查点、权重加载等问题，提升生产环境可靠性。
- **生态扩展**：新增Ascend NPU部署教程，拓展硬件生态；RAC压缩方案吸引推理模型用户。

## 四、值得关注的技术点

- **FlashInfer fused top-k**：针对PAGED rows的融合内核，是KV缓存管理的关键优化。
- **SWA状态检查点保留**：滑动窗口注意力在最后状态检查点保留，对长上下文场景重要。
- **DeepEP-class后端支持**：Qwen3.5/3.8系列对EPLB（专家并行负载均衡）的适配，体现对大规模MoE部署的重视。
- **MHC post+pre路径默认开启**：SM12x架构的默认路径变更，影响后续性能基准。

## 五、对项目发展的影响

从README可知，SGLang定位为高性能LLM推理框架，强调**低延迟、高吞吐、多硬件支持**。本次提交体现了三个发展方向：

1. **推理模型优化**：RAC压缩和Qwen3.8系列支持，瞄准推理模型（如o1类）市场，这是当前AI领域最热方向。
2. **硬件多元化**：AMD gfx950、Ascend NPU、H200等适配，扩大部署场景，降低对单一GPU厂商依赖。
3. **架构精简与融合**：移除TorchAO、融合MoE内核，表明项目在成熟期更注重代码质量和执行效率，而非功能堆砌。

整体来看，SGLang正从“通用推理框架”向“推理模型+多硬件+极致性能”的垂直深度方向演进，本次提交是这一战略的稳步推进。

## 详细提交记录

### [a9654ea](https://github.com/sgl-project/sglang/commit/a9654eacc12cb27abfb39f586d386b11ccd102bf)

- **作者**: Ziang Li
- **时间**: 2026-08-14T22:22:18Z
- **提交信息**: fix(dsa): use FlashInfer fused top-k for packed PAGED rows (#33006)

### [bfb224f](https://github.com/sgl-project/sglang/commit/bfb224ff01d4f2d6108633dff39ad37284e8f29d)

- **作者**: Zhipeng Wang
- **时间**: 2026-08-14T22:13:45Z
- **提交信息**: Add Reasoning-Aware Compression (RAC) pruning recipe for reasoning models (#32414)

Co-authored-by: Ryan Lucas <ryanluc@mit.edu>
Co-authored-by: Kayhan Behdin <kbehdin@linkedin.com>
Co-authored-by: Zhipeng Wang <zwanga@wustl.edu>

### [03c1d58](https://github.com/sgl-project/sglang/commit/03c1d58112642964fe237cd56962c320407adb6d)

- **作者**: Vedant V Jhaveri
- **时间**: 2026-08-14T21:37:58Z
- **提交信息**: perf: add H200 Triton MoE configs for E256 N512 (#34150)

Co-authored-by: Vedant Jhaveri <vjhaveri@linkedin.com>
Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>

### [22dde1d](https://github.com/sgl-project/sglang/commit/22dde1dd5b56d648251c115498fd4e1815a6264a)

- **作者**: Han-Yin Chang
- **时间**: 2026-08-14T20:56:55Z
- **提交信息**: [Docs] Fill GLM-5.2 H200 FP8 speed cells (low-latency, balanced); fix MTP notation (#31554)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [b676793](https://github.com/sgl-project/sglang/commit/b676793e5ef375c0787253c17e359c33e97dd99f)

- **作者**: sglang-bot
- **时间**: 2026-08-14T20:55:52Z
- **提交信息**: docs: sync LMSYS SGLang blog cards (#32982)

Co-authored-by: sglang-bot <sglang-bot@users.noreply.github.com>

### [42e8718](https://github.com/sgl-project/sglang/commit/42e8718d3da7516def7b62ed46d8cf64bc5e5bb9)

- **作者**: Sidhartha Reddy Potu
- **时间**: 2026-08-14T20:43:48Z
- **提交信息**: fix(muse-glimmer): parse required/named tool calls natively (#34781)

Co-authored-by: Xinyuan Tong <xinyuantong.cs@gmail.com>

### [d7207be](https://github.com/sgl-project/sglang/commit/d7207be156749024cbade6527bf0b87896f58967)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-08-14T20:18:53Z
- **提交信息**: Fix startup weight load after TorchAO removal (#34869)

### [1af761a](https://github.com/sgl-project/sglang/commit/1af761a09a5a0821a10157858069666ada803263)

- **作者**: Jackey Hua
- **时间**: 2026-08-14T19:51:21Z
- **提交信息**: [SM12x] Default the fused MHC post+pre path on (#34019)

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [41cd5a7](https://github.com/sgl-project/sglang/commit/41cd5a718942f97bc45b0b5d7fca82992e8ae529)

- **作者**: DarkraiHL
- **时间**: 2026-08-14T17:55:41Z
- **提交信息**: [Fix] Fix Qwen3.5 MTP startup with HiCache (#34560)

Co-authored-by: hjzhang <76768149+1e4ves@users.noreply.github.com>
Co-authored-by: YAMY <74099316+YAMY1234@users.noreply.github.com>

### [d8399af](https://github.com/sgl-project/sglang/commit/d8399af70cf6aa5b216f3d6aa869d3d83bd50645)

- **作者**: Xun Sun
- **时间**: 2026-08-14T17:27:39Z
- **提交信息**: fix(qwen3): support DeepEP-class backends and early EPLB state (#34810)

### [7562e74](https://github.com/sgl-project/sglang/commit/7562e741e26a4818ee78f1e63140240ec59147c0)

- **作者**: Ke Bao
- **时间**: 2026-08-14T17:12:38Z
- **提交信息**: Retain SWA down to the last state checkpoint (#34729)

### [c20acee](https://github.com/sgl-project/sglang/commit/c20aceeb88d65cd4815551d8e2a75f7a1988ed72)

- **作者**: Ke Bao
- **时间**: 2026-08-14T16:34:00Z
- **提交信息**: Fix mamba checkpoint depth under dcp (#34808)

### [70e291b](https://github.com/sgl-project/sglang/commit/70e291b70f5a2833291fff517a00b2f3ff559463)

- **作者**: zijiexia
- **时间**: 2026-08-14T15:42:50Z
- **提交信息**: [Docs] Add GB300 cells and benchmarks for Qwen3.8-27B (#34863)

Co-authored-by: Xinyuan Tong <xinyuantong.cs@gmail.com>
Co-authored-by: yhyang201 <yhyang201@gmail.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [29c6be1](https://github.com/sgl-project/sglang/commit/29c6be15a4ef08c0ecc239b313a706334c471e1e)

- **作者**: zijiexia
- **时间**: 2026-08-14T15:23:39Z
- **提交信息**: [Docs] Add Qwen3.8-27B cookbook page (#34860)

Co-authored-by: BBuf <1182563586@qq.com>
Co-authored-by: yhyang201 <yhyang201@gmail.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [9c9a327](https://github.com/sgl-project/sglang/commit/9c9a3273be7f8657ae15d24ec0df8d2b1d1dc9f5)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-08-14T15:21:54Z
- **提交信息**: [diffusion] Fix Helios denoising profiler stepping (#34826)

### [5f2a6d6](https://github.com/sgl-project/sglang/commit/5f2a6d6422bfda700b8d134bf8b1c5fe4a40e1a2)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-08-14T15:20:29Z
- **提交信息**: [diffusion] Fix symbolic replicated-mode counting under torch.compile (#34824)

### [b95a746](https://github.com/sgl-project/sglang/commit/b95a74694842b0540c4682d94add777a5c2feeda)

- **作者**: Yuan Luo
- **时间**: 2026-08-14T14:11:34Z
- **提交信息**: [MoE] Fuse swiglu moe up gemm epilogue (#32944)

Co-authored-by: luoyuan.luo <luoyuan.luo@antgroup.com>

### [9d2f158](https://github.com/sgl-project/sglang/commit/9d2f1584fa3ce8a03908f4808447d2706544cf5e)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-08-14T14:07:50Z
- **提交信息**: Fix MiniMax-H3 Cache-DiT BCG warning (#34848)

### [c939307](https://github.com/sgl-project/sglang/commit/c939307e8aaa0ebb07929cf0d947d12dc4e8ed1e)

- **作者**: Roger Young
- **时间**: 2026-08-14T14:01:48Z
- **提交信息**: [MiniMax-M3] Overlap shared and routed experts (#34542)

Co-authored-by: xuebi <xuebi@minimaxi.com>
Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

### [1a178f7](https://github.com/sgl-project/sglang/commit/1a178f7c7c21ce35d2250a78a60e05e3d973adca)

- **作者**: Yuang Chen
- **时间**: 2026-08-14T14:01:12Z
- **提交信息**: [EPD] Batch embedding cache host-device range copies (#31574)

Co-authored-by: 晟海 <huangtingwei.htw@antgroup.com>
Co-authored-by: liusy58 <liusy58@linux.alibaba.com>
Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

### [5e65dd0](https://github.com/sgl-project/sglang/commit/5e65dd01a7d414204398fd38ec1b91e9f68e1c40)

- **作者**: Brayden Zhong
- **时间**: 2026-08-14T13:49:11Z
- **提交信息**: Remove the torchao integration (--torchao-config) (#34304)

Co-authored-by: Brayden Zhong <brayden@radixark.ai>

### [fe0c18e](https://github.com/sgl-project/sglang/commit/fe0c18effd2169d6314dc3749e5aa9e857d4ea5d)

- **作者**: amote-i
- **时间**: 2026-08-14T12:02:04Z
- **提交信息**: [NPU] [DOC] Add Qwen3.8-Max deployment tutorial on Ascend NPUs (#34836)

### [18107e3](https://github.com/sgl-project/sglang/commit/18107e38d266a98f59a8e3c766f8ddaf9b723ded)

- **作者**: Ke Bao
- **时间**: 2026-08-14T09:13:21Z
- **提交信息**: Skip oow slot freeing under eagle (#34823)

### [4d94f1d](https://github.com/sgl-project/sglang/commit/4d94f1d31054dc471fedf296655cfa6f5c21414f)

- **作者**: chilltongx
- **时间**: 2026-08-14T08:45:36Z
- **提交信息**: [diffusion] fix: warn when bcg disables cache-dit (#34242)

Co-authored-by: chilltongx <284668524+chilltongx@users.noreply.github.com>

### [f2c84de](https://github.com/sgl-project/sglang/commit/f2c84de022a166a5c2388a96b6e9d4183f06170d)

- **作者**: Liangsheng Yin
- **时间**: 2026-08-14T07:46:52Z
- **提交信息**: [Perf] Publish the WAR read-done event at DSPARK verify (#34816)

### [a86edcd](https://github.com/sgl-project/sglang/commit/a86edcdc0a69679b4927b4dcefbc64dd682bf0dd)

- **作者**: triple-mu
- **时间**: 2026-08-14T07:33:51Z
- **提交信息**: [diffusion] feat: rebuild minimax-h3 adaln outputs on demand (#34650)

Co-authored-by: Mick <mickjagger19@icloud.com>

### [2622e01](https://github.com/sgl-project/sglang/commit/2622e013ebc1ec5959ace9693a1ca51b929b42cc)

- **作者**: gilfordting
- **时间**: 2026-08-14T07:17:42Z
- **提交信息**: [Fix] has_hf_quant_config crashes on local dirs without the config (#34774)

Co-authored-by: harmya <harmya@modal.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [65d6210](https://github.com/sgl-project/sglang/commit/65d62109dd15e3eeb577e5b37ae45d2db75e6eef)

- **作者**: kk
- **时间**: 2026-08-14T07:05:42Z
- **提交信息**: [AMD] Fix Triton 3.7 gfx950 extend-attention spills (#34741)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-08-15
**监控日期**: 2026-08-14
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1246
- **最后更新**: 2026-08-14T13:15:32Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

### 1. 主要更新类型
- **功能新增**：为Ascend NPU硬件平台新增性能分析（Profiling）支持。

### 2. 关键变更点及其与项目整体方向的关系
- 通过`torch_npu.profiler`为NPU设备接入性能分析能力，替代原先仅支持CUDA的单一路径。
- NPU路径从`export_chrome_trace`（单JSON文件）切换为`tensorboard_trace_handler` + `experimental_config`，生成完整的Ascend Profiler输出目录（含`kernel_details.csv`、`step_trace_time.csv`、`trace_view.json`等文件），并保留所有生成文件（`data_simplification=False`）。
- 新增环境变量`CACHE_DIT_NPU_PROFILER_LEVEL`控制profiler级别（默认Level0），并清洗`worker_name`以符合`[A-Za-z0-9_-]`字符集，同时自动定位生成的`*_ascend_pt`目录并通过`trace_path`暴露。
- CUDA路径保持不变。

### 3. 对项目的影响和潜在意义
- **扩展硬件生态**：项目定位为PyTorch原生推理引擎，支持NPU意味着可覆盖华为昇腾等国产硬件场景，提升在国产化AI基础设施中的适用性。
- **增强可观测性**：完整的性能分析输出（含算子统计、时间线、内核详情）有助于开发者定位NPU上的性能瓶颈，优化推理延迟和吞吐。
- **降低使用门槛**：通过环境变量配置profiler级别，用户无需修改代码即可调整分析粒度，提升易用性。

### 4. 值得关注的技术点
- **Profiler输出完整性**：选择`tensorboard_trace_handler`而非`export_chrome_trace`，是为了获取更全面的Ascend原生分析数据（如`op_summary.csv`、`operator_details.csv`），而非仅Chrome Trace格式。
- **路径与命名规范化**：清洗`worker_name`字符集和自动定位输出目录，体现了对多进程/分布式场景下文件冲突和路径管理的细致考虑。
- **向后兼容**：CUDA路径未改动，确保现有用户不受影响，体现了增量式演进策略。

### 5. 对项目发展的影响
- 结合README中“Cache, Parallelism, Quantization and CPU Offload”的核心特性，NPU profiling支持进一步强化了项目作为**跨硬件高性能推理引擎**的定位，有助于吸引更多使用昇腾等国产芯片的开发者。
- 该功能为后续针对NPU的优化（如算子融合、内存复用）提供了数据基础，可能推动项目在国产硬件上的性能调优和生态建设，与当前AI基础设施国产化的趋势相契合。
- 同时，通过完善的可观测性，项目在工程成熟度上更进一步，为生产环境部署提供了更可靠的诊断工具。

## 详细提交记录

### [b904e00](https://github.com/vipshop/cache-dit/commit/b904e00ae65d09f349a1328294bc3e6761a1b467)

- **作者**: DefTruth
- **时间**: 2026-08-14T10:38:08Z
- **提交信息**: feat(profiler): support Ascend NPU profiling via torch_npu.profiler (#1096)

* feat(profiler): support Ascend NPU profiling via torch_npu.profiler (#1093)

* feat(profiler): support Ascend NPU profiling via torch_npu.profiler

* feat(profiler): export full CANN output directory on NPU

Switch the NPU path from export_chrome_trace (single json) to
on_trace_ready=tensorboard_trace_handler + experimental_config, so the
full Ascend profiling output directory is produced: ASCEND_PROFILER_OUTPUT
(kernel_details.csv, step_trace_time.csv, trace_view.json, op_summary.csv,
op_statistic.csv, operator_details.csv, .db) plus PROF_XXX, FRAMEWORK and
logs. data_simplification=False keeps every generated file.

- profiler_level configurable via CACHE_DIT_NPU_PROFILER_LEVEL (Level0 default)
- sanitize worker_name to the allowed [A-Za-z0-9_-] charset
- locate the produced *_ascend_pt dir and expose it via trace_path
- CUDA path unchanged

---------

Co-authored-by: changetheway <guotaoyuan1@h-partners.com>

* update boogu-image

* Update boogu_image.py

* Refactor import paths for boogu modules

---------

Co-authored-by: ooooooye <53851298+brandneway@users.noreply.github.com>
Co-authored-by: changetheway <guotaoyuan1@h-partners.com>

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-08-15
**监控日期**: 2026-08-14
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 89062
- **最后更新**: 2026-08-14T22:19:05Z

## 提交统计

- **昨日提交总数**: 27
- **提交者数量**: 22
- **主要提交者**: Kevin H. Luu, Isotr0py, ccaadaro

## AI分析总结

# vLLM 昨日提交分析总结

## 1. 主要更新类型

- **CI/CD 优化**（约7项）：多个测试任务分片（Humming H100、MoE B200、多模态扩展生成、池化模型、量化任务），提升CI效率
- **Bug修复**（约5项）：flashinfer导入保护、Helm资源引用、Cosmos3-Edge处理器兼容性、XPU测试修复
- **性能优化**（约4项）：多模态编码器减少GPU-CPU同步、Cohere二进制嵌入向量化、CPU端MXFP4块缩放指令优化、DeepEP v2 MoE worker种子设置
- **功能新增**（约3项）：Rust前端gRPC强化学习生命周期控制、Kimi K3 DFlash辅助状态、KV-Cache布局重构
- **重构与清理**（约3项）：移除`override_attention_dtype`、入口异常处理器整合、ROCm SiTU支持简化
- **文档更新**（1项）：模型支持信息更新
- **硬件适配**（约4项）：ROCm稀疏索引、XPU内核升级、XPU流水线并行优化、DSA SM90解码路径

## 2. 关键变更点与项目方向关系

- **CI分片优化**直接响应vLLM“易用、快速、廉价”目标，通过缩短测试时间加速迭代
- **KV-Cache布局重构（5/N）** 是长期架构演进，后端发布KV打包方式，为更灵活的缓存管理铺路
- **强化学习生命周期控制**扩展vLLM从纯推理向训练/RL生态延伸
- **多模态编码器优化**强化vLLM在多模态领域的竞争力
- **硬件适配（ROCm/XPU）** 体现跨平台战略，扩大硬件覆盖范围

## 3. 项目影响与潜在意义

- **CI效率提升**：量化任务分片至4并行（≤30分钟目标），显著缩短反馈周期，加速开发迭代
- **稳定性增强**：flashinfer导入保护防止引擎启动崩溃，Helm资源引用修复提升部署可靠性
- **性能提升**：多模态编码器减少同步、Cohere位打包向量化、CPU MXFP4指令优化，直接改善推理延迟和吞吐
- **架构演进**：KV-Cache重构为未来优化奠定基础，RL控制为强化学习场景提供支持

## 4. 值得关注的技术点

- **DeepEP v2 MoE worker种子设置**：确保分布式MoE训练/推理的确定性，对可复现性至关重要
- **Kimi K3 DFlash辅助状态**：投机解码中利用预归一化AttnRes混合，提升解码效率
- **MRV2多模态编码器CUDA图**：为模型运行器v2启用编码器CUDA图，减少内核启动开销
- **XPU流水线并行重叠**：异步调度PP采样token广播与计算重叠，优化XPU上的PP效率

## 5. 对项目发展的影响

vLLM作为“人人可用的快速廉价LLM服务”框架，本批提交体现了三个战略方向：**一是持续优化性能与效率**，通过减少同步、向量化、指令优化等手段降低推理成本；**二是扩展硬件与场景覆盖**，强化ROCm/XPU支持，并引入RL生命周期控制，向训练/RL领域延伸；**三是夯实工程基础**，通过CI分片、异常处理整合、依赖清理等提升项目可维护性和稳定性。KV-Cache重构系列表明项目正进行深层次架构优化，为未来更复杂的缓存策略和更高性能铺路。整体上，这些提交展现了vLLM在保持快速迭代的同时，正系统性地向多硬件、多场景、高性能方向演进。

## 详细提交记录

### [bb4b448](https://github.com/vllm-project/vllm/commit/bb4b448f9896cf3f5607bd5ed4b35b29cd866a6b)

- **作者**: Kevin H. Luu
- **时间**: 2026-08-14T22:12:02Z
- **提交信息**: [CI] Shard Humming H100 eval (#52326)

Signed-off-by: Kevin Luu <51931015+khluu@users.noreply.github.com>

### [81e81da](https://github.com/vllm-project/vllm/commit/81e81dac1f3654564c3c48000edce1cdbe248ab9)

- **作者**: Kevin H. Luu
- **时间**: 2026-08-14T22:11:55Z
- **提交信息**: [CI] Shard MoE refactor B200 eval (#52327)

Signed-off-by: Kevin Luu <51931015+khluu@users.noreply.github.com>

### [694db07](https://github.com/vllm-project/vllm/commit/694db075f8af1ccb026720782bc0e2400a3f5c61)

- **作者**: Kevin H. Luu
- **时间**: 2026-08-14T22:11:48Z
- **提交信息**: [CI] Shard multimodal extended generation 2 (#52323)

Signed-off-by: Kevin Luu <51931015+khluu@users.noreply.github.com>

### [549cef0](https://github.com/vllm-project/vllm/commit/549cef0b0b2c8924d302686c613cb4c39fc24dcd)

- **作者**: Kevin H. Luu
- **时间**: 2026-08-14T22:11:41Z
- **提交信息**: [CI] Shard extended pooling model tests (#52322)

Signed-off-by: Kevin Luu <51931015+khluu@users.noreply.github.com>
Signed-off-by: khluu <khluu000@gmail.com>

### [d87ef45](https://github.com/vllm-project/vllm/commit/d87ef456abe54565cef476637df5e585bfddfb37)

- **作者**: Kevin H. Luu
- **时间**: 2026-08-14T22:11:32Z
- **提交信息**: [CI] Shard Quantization job into 4 parallel shards (≤30 min target) (#52328)

### [925ea7e](https://github.com/vllm-project/vllm/commit/925ea7e60f727bbb3fe3fcdb1c02b01a5bfb2749)

- **作者**: Guanxin Li
- **时间**: 2026-08-14T20:01:24Z
- **提交信息**: [CI][Test] Seed the DeepEP v2 MoE workers, not just the parent (#50589)

Signed-off-by: Guanxin Li <guanxinl@nvidia.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [c794754](https://github.com/vllm-project/vllm/commit/c794754062d49a8fdb63ab3c5215b488b865030c)

- **作者**: sroberts-amd
- **时间**: 2026-08-14T18:38:04Z
- **提交信息**: [ROCm]Remove special-case SiTU support model-specific gating (#50597)

Signed-off-by: Stacy Roberts <sroberts@amd.com>
Signed-off-by: Stacy Roberts <robers23@utexas.edu>
Co-authored-by: Stacy Roberts <robers23@utexas.edu>

### [f473870](https://github.com/vllm-project/vllm/commit/f473870ecf7a5a83958dbc116468663224f45b05)

- **作者**: Connor Carpenter
- **时间**: 2026-08-14T18:32:39Z
- **提交信息**: [Rust Frontend][gRPC] Add RL lifecycle control (#51316)

Signed-off-by: Connor Carpenter <connorc@nvidia.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>

### [3e3ceb1](https://github.com/vllm-project/vllm/commit/3e3ceb1961d44252ff4a4f8e22364186d70c54f7)

- **作者**: Nick Hill
- **时间**: 2026-08-14T17:40:14Z
- **提交信息**: [Perf] Avoid more GPU<->CPU syncs in multimodal encoders (#52369)

Signed-off-by: Nick Hill <nickhill123@gmail.com>

### [9b0ab5d](https://github.com/vllm-project/vllm/commit/9b0ab5dd53583ee25066b8d937e8bd3235daa6e2)

- **作者**: James E T Smith
- **时间**: 2026-08-14T17:38:14Z
- **提交信息**: [ROCm][AMD] Enable preshuffled sparse indexing for 16-token blocks (#51216)

Signed-off-by: jamesETsmith <james.smith9113@gmail.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [83ded8d](https://github.com/vllm-project/vllm/commit/83ded8d839f60d97f5b020b598001cd9081150f6)

- **作者**: stefankoncarevic
- **时间**: 2026-08-14T17:08:41Z
- **提交信息**: [Test][LoRA] Speed up the LoRA test job (#52331)

Signed-off-by: Stefan Koncarevic <stefan.koncarevic@amd.com>

### [e078a22](https://github.com/vllm-project/vllm/commit/e078a2238a1e4b53d49a7cc15e09716ed61abf3b)

- **作者**: shanjiaz
- **时间**: 2026-08-14T16:27:24Z
- **提交信息**: [Bugfix] Widen flashinfer.comm import guard so a failed import doesn't abort engine startup (#52241)

Signed-off-by: shanjiaz <zsjwpianpian@gmail.com>

### [03a8d0b](https://github.com/vllm-project/vllm/commit/03a8d0b1ede68efc20b8bbfc14ee4681a62f8d75)

- **作者**: Rahul Chalamala
- **时间**: 2026-08-14T16:03:42Z
- **提交信息**: [Model][Spec Decode] Tap the pre-norm AttnRes mixture as the Kimi K3 DFlash aux state (#50487)

Signed-off-by: Rahul Chalamala <22563365+rchalamala@users.noreply.github.com>
Co-authored-by: Janelle Cai <janelle.cai@modal.com>

### [cdc4824](https://github.com/vllm-project/vllm/commit/cdc4824a21eaa986d4d1fee90a7e6465c9f706e6)

- **作者**: wangxiyuan
- **时间**: 2026-08-14T15:15:43Z
- **提交信息**: [Misc] Remove `override_attention_dtype` (#48684)

Signed-off-by: wangxiyuan <wangxiyuan1007@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [1f7427b](https://github.com/vllm-project/vllm/commit/1f7427bc0ad31fdad1b0933c77ea5acae15da2e0)

- **作者**: Qiming Zhang
- **时间**: 2026-08-14T13:49:47Z
- **提交信息**: [UT][XPU] fix b12x UT (#52265)

Signed-off-by: mayuyuace <qiming1.zhang@intel.com>
Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>
Co-authored-by: Andreas Karatzas <Andreas.Karatzas@amd.com>

### [57bd0ed](https://github.com/vllm-project/vllm/commit/57bd0ed441095b5c546707cabe25d3fa08b7f161)

- **作者**: Lucas Wilkinson
- **时间**: 2026-08-14T13:47:55Z
- **提交信息**: [5/N][KV-Cache Layout Refactor] Backend-published KV packing via customize_spec (#51704)

Signed-off-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [63a9a50](https://github.com/vllm-project/vllm/commit/63a9a5010a6d1539c52957646ef9d6bbcf7a4deb)

- **作者**: Zhuobin Huang
- **时间**: 2026-08-14T10:09:51Z
- **提交信息**: [Attention][DSA] Take the native decode path for MTP=3 on SM90 (#52164)

Signed-off-by: zobinHuang <zobin1999@gmail.com>
Co-authored-by: nodeeeeee <zhangkai.nodeee@gmail.com>

### [aa31003](https://github.com/vllm-project/vllm/commit/aa3100357322995b201d5348c5490596a7bd70a9)

- **作者**: iwannagotobed
- **时间**: 2026-08-14T09:47:42Z
- **提交信息**: [Bugfix][Helm] Fix chart resource references (#51664)

Signed-off-by: iwannagotobed <us990704@yonsei.ac.kr>
Co-authored-by: Chauncey <chaunceyjiang@gmail.com>

### [69e0e58](https://github.com/vllm-project/vllm/commit/69e0e58da107a9d0aa48a50094d6f16a0984a090)

- **作者**: Jee Jee Li
- **时间**: 2026-08-14T09:47:30Z
- **提交信息**: [Doc] Update model support information (#52289)

Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>

### [20405bf](https://github.com/vllm-project/vllm/commit/20405bfb15546bb988f425a3c95fef9ac59104c7)

- **作者**: bastefaniak
- **时间**: 2026-08-14T09:46:46Z
- **提交信息**: [Bugfix] Fix Cosmos3-Edge processor after transformers 5.15 release (#51989)

Signed-off-by: Bartosz Stefaniak <bstefaniak@nvidia.com>

### [66728fe](https://github.com/vllm-project/vllm/commit/66728feb1fbe0c6d32dcce2d4ce6e827712118c8)

- **作者**: Isotr0py
- **时间**: 2026-08-14T09:33:21Z
- **提交信息**: [MRV2][Multimodal] Enable encoder cuda graph for model runner v2 (#49852)

Signed-off-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [b8165e5](https://github.com/vllm-project/vllm/commit/b8165e5e58ee25a9f5183e692b6259d37c3873ad)

- **作者**: wang.yuqi
- **时间**: 2026-08-14T09:27:24Z
- **提交信息**: [Frontend] Consolidate entrypoint exception handler (#52261)

Signed-off-by: wang.yuqi <yuqi.wang@daocloud.io>

### [103c419](https://github.com/vllm-project/vllm/commit/103c419f048474d757c752524abb1e155dd01b9a)

- **作者**: Fangchen Li
- **时间**: 2026-08-14T09:15:59Z
- **提交信息**: [Perf][Frontend] Vectorize Cohere binary embedding bit-packing (#52277)

Signed-off-by: Fangchen Li <fangchen.li@outlook.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [624999a](https://github.com/vllm-project/vllm/commit/624999aae5315b3d1d9a36b3bab1629f39456de9)

- **作者**: Kunshang Ji
- **时间**: 2026-08-14T09:01:37Z
- **提交信息**: [XPU]bump up vllm_xpu_kernels to 0.1.13.2 (#52138)

Signed-off-by: Kunshang Ji <jikunshang95@gmail.com>
Signed-off-by: Kunshang Ji <kunshang.ji@intel.com>

### [3c8676a](https://github.com/vllm-project/vllm/commit/3c8676aebbd54ccf5d666b9c493d28badd3f970f)

- **作者**: YiSheng5
- **时间**: 2026-08-14T09:00:23Z
- **提交信息**: [PP][XPU]Overlap async-scheduling PP sampled-token broadcast with compute (#51650)

Signed-off-by: yisheng <yi.sheng@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [d4c24e6](https://github.com/vllm-project/vllm/commit/d4c24e6f5d1864bc81ad0769097e00b9042178ca)

- **作者**: Lucas Wilkinson
- **时间**: 2026-08-14T08:23:51Z
- **提交信息**: [CI] Increase extended generation test timeout (#52252)

### [bda4c3e](https://github.com/vllm-project/vllm/commit/bda4c3e8eefe5442897f07f9c0c2d1cae833ca2f)

- **作者**: ccaadaro
- **时间**: 2026-08-14T08:19:21Z
- **提交信息**: [CPU] Fold the MXFP4 block scale in 2 instructions instead of 4 (#51583)

Signed-off-by: ccaadaro <ccanadar@unex.es>
Co-authored-by: Li, Jiang <jiang1.li@intel.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-08-15
**监控日期**: 2026-08-14
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 6114
- **最后更新**: 2026-08-14T20:57:39Z

## 提交统计

- **昨日提交总数**: 9
- **提交者数量**: 7
- **主要提交者**: Shenglei Fu, R0CKSTAR, baonudesifeizhai

## AI分析总结

## 提交分析总结

### 1. 主要更新类型

本次提交批次涵盖**Bug修复**（4项）、**性能优化**（3项）、**CI/测试基础设施改进**（2项）和**功能修复**（1项），无新增功能或文档更新。

### 2. 关键变更点与项目方向的关系

- **XPU/MUSA/ROCm等异构硬件适配**：修复XPU测试收集崩溃、MUSA平台Qwen图像模型的RoPE别名问题、将ROCm CI迁移至MI300X，体现项目对多硬件平台（Intel、摩尔线程、AMD）的持续支持承诺。
- **NPU性能优化**：融合MiniMax H3和Qwen3-VL的SwiGLU与RoPE算子，针对NPU架构进行内核级优化，符合“快速”服务目标。
- **API Server模型同步修复**：解决模型标签与模型同步问题及标志规范化，提升服务端稳定性。
- **HSDP与FP8线性方法兼容性修复**：确保新量化方法在分布式训练/推理场景下正常工作。
- **CI代码覆盖率收集**：按模型和入口模式细分覆盖率，强化测试体系。

### 3. 对项目的影响和潜在意义

- **硬件生态扩展**：XPU/MUSA/ROCm修复与CI迁移，降低新硬件接入门槛，扩大用户基础。
- **推理性能提升**：NPU算子融合直接减少内核启动开销和内存访问，对长序列推理场景收益显著。
- **服务可靠性增强**：API同步修复和HSDP兼容性修复，减少生产环境中的隐性故障。
- **测试质量提升**：细粒度覆盖率收集有助于发现测试盲区，提升回归防护能力。

### 4. 值得关注的技术点

- **NPU算子融合策略**：SwiGLU和RoPE的融合方式（如是否利用NPU的向量单元特性）值得关注，可能成为其他硬件平台的优化参考。
- **RoPE别名守卫简化**：MUSA平台避免复杂别名判断，可能涉及对不同RoPE实现的统一抽象。
- **HSDP与FP8兼容性**：涉及分布式通信与量化格式的交互，修复方案可能影响后续量化方法的分布式支持设计。
- **CI迁移至MI300X**：反映ROCm生态对CDNA3架构的成熟支持，以及项目对最新AMD硬件的适配策略。

### 5. 对项目发展的影响

vLLM-Omni定位为“人人可用的全模态模型服务”，本次提交从三个维度推动该目标：

- **广度**：持续扩展XPU、MUSA、ROCm、NPU等异构硬件支持，践行“人人可用”的硬件包容性理念。
- **速度**：NPU算子融合和FP8兼容性优化，直接提升推理吞吐和延迟表现，强化“快速”承诺。
- **成本**：CI基础设施改进和测试覆盖增强，降低维护成本并提高开发效率，间接降低用户使用成本。

整体来看，本次提交以**基础设施稳健性**和**异构硬件性能**为核心，为全模态模型在多硬件环境下的规模化部署奠定更坚实的基础。

## 详细提交记录

### [4b6d6d5](https://github.com/vllm-project/vllm-omni/commit/4b6d6d5cf79506d2a6ea697da11f1b2bdceccda8)

- **作者**: Joshna-Medisetty
- **时间**: 2026-08-14T20:23:41Z
- **提交信息**: [Bugfix][XPU][Tests]Scope XPU pytest to explicit paths to fix collection crash (#6175)

Signed-off-by: Joshna Medisetty <joshna.medisetty@intel.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Chendi.Xue <chendi.xue@intel.com>

### [f7a5146](https://github.com/vllm-project/vllm-omni/commit/f7a5146093bc4d16b5607901a8a2509d785777db)

- **作者**: Alex Brooks
- **时间**: 2026-08-14T19:13:00Z
- **提交信息**: [Feat/Bugfix] Fix API Server model tag <-> model sync & flag normalization (#3805)

Signed-off-by: Alex Brooks <albrooks@redhat.com>

### [8ecd1f6](https://github.com/vllm-project/vllm-omni/commit/8ecd1f6d5cc91aab8a475a861213720b336e2f65)

- **作者**: Wenjia Li
- **时间**: 2026-08-14T11:47:17Z
- **提交信息**: [Perf][NPU] Fuse MiniMax H3 Qwen3-VL SwiGLU (#6167)

Signed-off-by: Wenjia Li <wjialish@gmail.com>

### [ffd11c1](https://github.com/vllm-project/vllm-omni/commit/ffd11c181e5fa4e558ba2570f326fb41371c0421)

- **作者**: Wenjia Li
- **时间**: 2026-08-14T09:49:26Z
- **提交信息**: [Perf][NPU] Fuse MiniMax H3 Qwen3-VL RoPE (#6061)

Signed-off-by: Wenjia Li <wjialish@gmail.com>

### [728640f](https://github.com/vllm-project/vllm-omni/commit/728640f4d9bb7c1b68d646e2a4c59ce1ce45de9c)

- **作者**: R0CKSTAR
- **时间**: 2026-08-14T07:51:23Z
- **提交信息**: [Bugfix][MUSA][Qwen Image] Avoid complex RoPE alias guards (#6110)

Signed-off-by: Xiaodong Ye <xiaodong.ye@mthreads.com>

### [022d7a7](https://github.com/vllm-project/vllm-omni/commit/022d7a7695ffc3ce7329c38656e388cc11aecb8d)

- **作者**: R0CKSTAR
- **时间**: 2026-08-14T07:49:26Z
- **提交信息**: [Perf][Diffusion] Avoid redundant MiniMax-H3 reference video scans (#6064)

Signed-off-by: Xiaodong Ye <xiaodong.ye@mthreads.com>

### [b300f66](https://github.com/vllm-project/vllm-omni/commit/b300f666568e6b83a1e8893a3e13fa71afa88aa5)

- **作者**: baonudesifeizhai
- **时间**: 2026-08-14T07:45:55Z
- **提交信息**: [Bugfix] Fix HSDP compatibility with the new online FP8 linear method (#5677)

Signed-off-by: roG0d <baonudesifeizhai@gmail.com>

### [bc73546](https://github.com/vllm-project/vllm-omni/commit/bc73546c065844136b16e3a8e799cc0bd36bc2ca)

- **作者**: TJian
- **时间**: 2026-08-14T07:38:47Z
- **提交信息**: [ROCm] [CI] Migrate CI to mi300x for v0.27.x (#5886)

Signed-off-by: tjtanaa <tunjian.tan@embeddedllm.com>
Signed-off-by: TJian <tunjian.tan@embeddedllm.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [2b08419](https://github.com/vllm-project/vllm-omni/commit/2b08419d8be88f3f78852e42bb70a0bd46b289ae)

- **作者**: Shenglei Fu
- **时间**: 2026-08-14T07:36:56Z
- **提交信息**: [CI] Per-model, per-entry-mode code coverage collection (#5593)

Signed-off-by: Shenglei Fu <sfu@confluent.io>
Signed-off-by: Shenglei Fu <117230642+ShengleiFu@users.noreply.github.com>
Co-authored-by: Claude Sonnet 5 <noreply@anthropic.com>
Co-authored-by: Alicia <115451386+congw729@users.noreply.github.com>
Co-authored-by: wangyu <53896905+yenuo26@users.noreply.github.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

---
