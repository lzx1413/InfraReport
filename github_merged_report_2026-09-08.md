# GitHub Stars 合并报告 - 2026-09-08

**合并日期**: 2026-09-09
**监控日期**: 2026-09-08
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


**报告日期**: 2026-09-09
**监控日期**: 2026-09-08
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2199
- **最后更新**: 2026-09-08T13:31:16Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Avaya Aggarwal, 0z5a

## AI分析总结

# VeOmni 仓库提交分析报告

## 一、主要更新类型

本次提交记录包含 **2 个 Bug 修复**，均属于分布式训练与模型并行场景下的正确性问题修复，无新增功能或文档更新。

## 二、关键变更点

1. **分布式梯度同步修复**（`[dist, parallel]`）：修复共享梯度（shared gather gradients）在分布式环境中的梯度保持问题，确保梯度在并行通信过程中不被错误覆盖或丢失。
2. **模型注意力正确性修复**（`[model, ci]`）：修复 Wan Ulysses 模型在 SP（Sequence Parallelism，序列并行）同步路径下的注意力计算正确性问题，涉及 CI（持续集成）验证流程。

## 三、对项目的影响与意义

这两个修复直接针对 **大规模多模态模型训练中的分布式一致性问题**。VeOmni 作为“以模型为中心的分布式训练配方库”，其核心价值在于为不同模态模型提供可扩展的训练方案。梯度同步错误和注意力计算偏差会直接影响模型收敛质量与训练稳定性，因此这两个修复对保障框架在真实大规模训练场景下的可靠性具有重要意义。

## 四、值得关注的技术点

- **共享梯度保持**：在分布式数据并行与模型并行混合场景下，共享参数的梯度聚合策略是训练正确性的关键细节，涉及通信原语的选择与梯度累积顺序。
- **SP 同步路径**：序列并行中跨设备注意力计算的同步机制，需确保中间状态在通信边界处正确对齐，否则会导致数值偏差。
- **CI 集成验证**：修复同时附带 CI 验证，表明项目重视回归测试与可复现性。

## 五、对项目发展的影响

基于 README 背景，VeOmni 的目标是构建覆盖任意模态的分布式训练“配方库”，其竞争力取决于 **训练正确性、可扩展性与易用性**。本次提交虽为小规模修复，但体现了项目在以下方向上的持续投入：

- **工程成熟度提升**：修复分布式训练中的隐蔽正确性问题，是框架从研究原型走向生产可用的必经之路。
- **多模态模型支持深化**：Wan Ulysses 相关修复表明项目正积极适配视频/多模态生成模型，与“任意模态”的定位一致。
- **质量保障体系建设**：CI 修复路径的引入，有助于建立自动化验证机制，降低后续扩展新模型时的回归风险。

总体而言，这两项修复属于“地基加固”型工作，虽不引入新特性，但对保障 VeOmni 在复杂分布式环境下的训练稳定性、吸引更多模型接入具有基础性价值，是项目向成熟分布式训练框架演进的重要一步。

## 详细提交记录

### [1f6674f](https://github.com/ByteDance-Seed/VeOmni/commit/1f6674f0a2556702f4db6ac5a51e0fb02c20d84a)

- **作者**: 0z5a
- **时间**: 2026-09-08T12:39:36Z
- **提交信息**: [dist, parallel] fix: preserve shared gather gradients (#1159)

Signed-off-by: 0z5a <0z5a@users.noreply.github.com>
Co-authored-by: 0z5a <0z5a@users.noreply.github.com>

### [c69a8e1](https://github.com/ByteDance-Seed/VeOmni/commit/c69a8e1163e219ee37cddafe2345f181e1214dbe)

- **作者**: Avaya Aggarwal
- **时间**: 2026-09-08T10:26:39Z
- **提交信息**: [model, ci] fix: Wan Ulysses SP sync-path attention correctness (#1158)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-09-09
**监控日期**: 2026-09-08
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2799
- **最后更新**: 2026-09-08T19:33:53Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-09-09
**监控日期**: 2026-09-08
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2241
- **最后更新**: 2026-09-08T19:04:31Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-09-09
**监控日期**: 2026-09-08
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6357
- **最后更新**: 2026-09-08T22:55:17Z

## 提交统计

- **昨日提交总数**: 12
- **提交者数量**: 12
- **主要提交者**: Gabriel Wu, Alex Yang, kangbintNV

## AI分析总结

# FlashInfer 提交分析总结

## 一、主要更新类型

本次提交以**Bug修复**为主，辅以**功能新增**、**性能优化**、**文档完善**和**依赖更新**，覆盖架构兼容性、编译基础设施、MoE推理效率及发布工程等多个维度。

## 二、关键变更点

**1. 架构兼容性扩展**
- 修复GDN WY ucache内核在SM121上的编译失败问题，将内核从`cute.experimental`迁移至统一的`@cute.jit`/`@cute.kernel`装饰器路径
- 为SM100/103的cute-dsl mm_bf16_fp4新增独立trace模板，解决6-D descale布局的解包错误
- 将NoPE MLA的`sparse_mla_top_k_lens`要求限定在非sparse后端，使SM120 GLM-5.3路径可用

**2. 编译缓存与性能优化**
- 为TVM-FFI GDN内核引入CuTe-DSL磁盘缓存，冷启动编译时间从604秒降至2.3秒（SM120），B200上从217秒降至110秒
- MoE NVFP4调度优化：为四个非对称负载分配专用线程资源，EP8在8192 tokens/rank时延迟降低68.7%（308μs→96μs），EP16在512 tokens/rank时降低25%

**3. 功能完善与正确性修复**
- 统一NVFP4 profiler工作区谓词逻辑，修复gated fc1 SF缓冲区尺寸不足问题
- 为TRT-LLM fused MoE内核新增valid维度参数，支持padding场景下的精确计算
- 新增MXFP8 MegaMoE EP16实验性后端（SM103a），实现分布式场景下的bitwise确定性输出
- KDA模块显式指定C++20标准，解决PyTorch 2.14的ATen头文件兼容问题，同时保持无关模块使用C++17

**4. 文档与发布流程**
- 将文档构建与生产部署分离，仅从发布标签部署生产文档，确保版本标签与实际内容一致
- 补充`cute_dsl_fused_moe_bf16`和`bsa_attn_sm120_blk64_sage_fwd`的API文档，解决0.6.18版本文档检查阻塞问题

## 三、项目影响与潜在意义

- **硬件覆盖扩展**：SM121修复和SM100/103 trace建模填补了Blackwell系列（B200/GB200等）的兼容性空白
- **工程效率提升**：磁盘缓存将编译开销降低两个数量级，显著改善多进程场景下的启动延迟
- **生态集成深化**：MoE valid参数和MLA sparse后端修复分别服务于TRT-LLM和vLLM集成，强化FlashInfer作为推理框架后端的基础设施地位
- **构建兼容性**：C++20修复确保与PyTorch 2.14的兼容，维持与最新深度学习生态的同步
- **发布可靠性**：文档部署修复解决了版本标签与内容不一致的信任问题

## 四、值得关注的技术点

- **装饰器统一迁移**：从`cute.experimental`迁移至统一路径，是消除实验性API依赖的战略性方向
- **有条件的编译标准**：仅在直接服务模块启用C++20，降低对其他模块的潜在影响
- **负载感知的线程分配**：根据NVFP4负载特征定制调度而非通用优化，体现对硬件细节的深入理解
- **CI/CD精细化**：文档验证与部署解耦，使用并发组作用域限制和权限最小化，是成熟的发布工程实践
- **布局感知的trace设计**：为不同硬件路径维护独立trace模板和判别逻辑，避免静默错误解析

## 五、对项目发展的影响

这些提交表明FlashInfer正沿着**多架构适配、编译基础设施优化、框架生态整合**三条主线稳步推进，强化了对最新NVIDIA架构（SM100+）的支持能力，同时通过缓存机制降低实际使用门槛。MoE相关修复和新增功能（NVFP4、MXFP8）反映了对MoE推理场景的持续投入。整体上，项目正从功能开发阶段向生产级稳定性阶段过渡，从单一内核库向具备完善编译工具链、多后端适配能力的推理基础设施演进。

## 详细提交记录

### [f32f740](https://github.com/flashinfer-ai/flashinfer/commit/f32f740ad2f228afa432c348904aef748f673ce3)

- **作者**: A*
- **时间**: 2026-09-08T22:42:01Z
- **提交信息**: fix(gdn): support WY ucache kernels on SM121 (#4528)

## 📌 Description

The WY ucache and ucache-flush kernels still use `cute.experimental`.
On SM121, that path emits
`#core.compute_capability<arch = sm_121>`, which
`nvidia-cutlass-dsl==4.7.0` cannot parse because the Core enum stops at
`sm_120`.

Neither kernel depends on experimental-only APIs. Move both to the
unified
`@cute.jit` / `@cute.kernel` decorators, matching the output-only WY fix
in
#4117. The existing device-target path can then compile native `sm_121a`
instead of failing during MLIR parsing.

## 🔍 Related Issues

Closes #4497.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request,
please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

> If you are unsure about how to set up `pre-commit`, see the pre-commit
documentation.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

GB10 (SM121), CUDA 13.0, PyTorch 2.13.0+cu130,
`nvidia-cutlass-dsl==4.7.0`; both CuTe architecture overrides unset:

- `pytest tests/gdn/test_decode_ucache.py -q` — 46 passed
- `use_pdl=True` / `pdl_trigger=True` correctness smoke — passed
- `pre-commit run --all-files` — passed

The existing ucache tests reproduce the parser failure on the unmodified
code, so this patch does not add a decorator-specific test.

## Reviewer Notes

I also checked the patch together with the current #4507 head: 59 passed
and
1 skipped in the affected test set. A paired GB10 smoke against the
experimental `sm120f` workaround showed no latency or kernel-resource
regression.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Improved compatibility and reliability for BF16 GDN decoding and
cache-flush operations.
* Updated GPU kernel integration to use the current supported interface.
* Removed obsolete internal references without changing public
functionality or user-facing behavior.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: hebo1221 <hebo1221@users.noreply.github.com>
Co-authored-by: Ka-Hyun Nam <knam@nvidia.com>

### [6b3d8b4](https://github.com/flashinfer-ai/flashinfer/commit/6b3d8b42b5d8c6c57bf271a320ae90033b89d556)

- **作者**: Lee Yong Jun
- **时间**: 2026-09-08T22:14:16Z
- **提交信息**: feat(gdn): adopt the CuTe-DSL disk cache for TVM-FFI GDN kernels (#4912)

## 📌 Description

Migrate the GDN CuTe-DSL call sites that already compile with
`--enable-tvm-ffi` to `build_and_load_cute_dsl_kernel`, so each
specialization is exported to the on-disk kernel cache and later
processes JITLink it instead of recompiling.

Covered call sites (8 compile sites in 5 files):

| File | Sites | Module |
| --- | --- | --- |
| `gdn_decode_nontranspose.py` | small/big batch |
`gdn_decode_nontranspose` |
| `gdn_decode_pretranspose.py` | 1 | `gdn_decode_pretranspose` |
| `gdn_decode_mtp.py` | inline, warp | `gdn_decode_mtp` |
| `gdn_decode_bf16_state.py` | wide_vec, wide_vec_t1, mtp_ilp4 |
`gdn_decode_bf16_state` |
| `blackwell/gdn_prefill.py` | 1 | `gdn_blackwell_prefill` |

How it works:

- Only the `cute.compile(...)` call is wrapped in a `compile_fn`
closure. Every in-process cache structure (getter dicts,
`defaults_by_B`, aux buffers) is unchanged, and on a disk hit the
closure never runs.
- Specialization names mirror the in-process cache keys, which #4219 and
#4436 already audited to cover every codegen parameter.
- Where several entry points share one module, the name adds a variant
tag. The Blackwell prefill name also adds `num_sm`, which the compile
bakes in as `max_active_clusters`.
- A small shared formatter (`gdn_kernels/cute_dsl_cache_naming.py`)
keeps names symbol-safe and caps their length.

Measurements with fresh processes and an isolated cache dir:

| GPU | Selection | Cold (compile + export) | Warm (disk hit) |
| --- | --- | --- | --- |
| RTX PRO 6000 (SM120) | bf16_state + fp32 MTP verify subsets (56 tests)
| 604s | **2.3s** |
| RTX PRO 6000 (SM120) | pretranspose + nontranspose basics (7 tests) |
2.9s | **1.4s** |
| B200 (SM100) | prefill suites (2835 tests, includes GPU test
execution) | 217s | **110s** |

## 🔍 Related Issues

#4214 (GDN-P1, PR 4 of the suggested implementation sequence)

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

Ran on RTX PRO 6000 (SM120) and B200 (SM100):

- `tests/gdn/test_cute_dsl_kernel_cache.py` (new, modeled on
`tests/jit/test_cute_dsl_cache.py`): 68 passed on both GPUs. Naming
contracts plus a disk-cache round trip (reload with `cute.compile`
forbidden, bit-identical results).
- `tests/jit/test_cute_dsl_cache.py`: 42 passed
- decode parity subsets from `tests/gdn/test_decode_delta_rule.py`
(SM120): passed cold, warm, and with
`FLASHINFER_CUTE_DSL_DISABLE_CACHE=1`
- `tests/gdn/test_multistream_overlap.py`: 4 passed on B200 (1 of them
skipped on SM120)
- prefill suites on B200: 2835 passed, 864 skipped, 24 failed, identical
cold/warm/cache-disabled. The 24 failures (fp8-state
`test_prefill_kernel_state_dtype` cases) fail identically on unmodified
main on the same machine, i.e. pre-existing in my environment.

## Reviewer Notes

Out of scope, as follow-ups:

- WY kernels: off the `gdn_decode.py` dispatch and not TVM-FFI yet
(persisting them needs a calling-convention change first).
- `delta_rule_dsl` kernels: use explicit `cute.compile[gpu_arch]`
targets, which the disk cache's arch keying does not reflect yet
(documented limitation).
- GDN-H2/H3 (explicit compile targets, PR 2 of the sequence) is
unchanged.

Open to adjusting the split if a different scope was intended for
GDN-P1.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **Performance**
- Added persistent caching for GDN GPU kernel builds, reducing
compilation overhead for repeated workloads.
- Cached kernels are reused across sessions when the relevant
configuration and source remain unchanged.
- Kernel builds automatically refresh when source code or compilation
settings change, helping ensure correct results across updates.
- Improved cache handling across multiple GDN decode and prefill kernel
variants for more consistent build reuse.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [020941c](https://github.com/flashinfer-ai/flashinfer/commit/020941c2b9b8cf662aae6438a8247dd4e736e503)

- **作者**: yichengj
- **时间**: 2026-09-08T22:07:08Z
- **提交信息**: fix(moe): unify the NVFP4 profiler workspace predicate and fix gated fc1 SF sizing (#4010)

## 📌 Description

Autotuning a native NVFP4 (FP4 activations x FP4 weights) CUTLASS MoE
crashed with `Assertion failed: quant_1 && quant_2 && quant_3 && quant_4
&& quant_5 && quant_6` (#4003): after #3738, the gemm profiler only
allocated its scratch quant-scale buffers for the FP8-activation FP4
flavor, so native NVFP4 got none. #4080 has since fixed that crash on
main. This PR is rebased on top of it and adds what's still missing:

- Replace the ad-hoc `is_nvfp4_quant` check with an
`isNativeWfp4Afp4Family()` helper used by both the allocation site
(`getProfilerWorkspaces`) and the consumption site
(`prepareQuantParams`), so the two can't drift apart again. This also
drops the `mSM >= 100` guard that the allocation side had but the
consumption side didn't.
- Size the fc1 weight scale-factor buffer (`quant_2`) with
`fc1_out_size` instead of `inter_size`. Gated activations make fc1
output 2x `inter_size`, so the old size under-allocated. #4308 has since
landed this sizing for the wfp4afp8 flavor; this PR applies it to native
NVFP4 and merges the two sizing branches so they cannot diverge.
- Add autotune coverage to `test_moe_nvfp4`, the regression test that
would have caught #4003.

Credit to @eugr for the proposed patch this builds on.

## 🔍 Related Issues

Fixes #4003 (crash itself already fixed on main by #4080). Regressed by
#3738.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

`test_moe_nvfp4` is now parametrized with `use_autotune`, same approach
as #3558. Pre-rebase on a GB10 (SM121): every autotune case died with
the assertion without the fix, and all 48 cases passed with it.
Post-rebase, re-ran gated and non-gated autotune cases plus a
non-autotune case on an RTX 5080 (SM120), all passing. After rebasing
onto current main (post-#4308), all 48 cases pass on an RTX 5080
(SM120).

## Reviewer Notes

The predicate deliberately has no SM version check, unlike its wfp4afp8
sibling: it must exactly match the consuming branch in
`prepareQuantParams`, which checks dtypes only. FP4 x FP4 doesn't exist
below SM100 anyway.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved Native NVFP4 fused Mixture-of-Experts (MoE) execution by
correcting workspace and scaling-factor handling.
* Fixed NVFP4 behavior when autotuning is enabled, preventing related
execution failures.

* **Tests**
* Expanded NVFP4 coverage to validate both autotuned and non-autotuned
execution paths.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [5cc867a](https://github.com/flashinfer-ai/flashinfer/commit/5cc867a9bb560bc89b91dbc738a9f63f09beb89b)

- **作者**: Gabriel Wu
- **时间**: 2026-09-08T21:53:37Z
- **提交信息**: fix(mla): scope NoPE sparse_mla_top_k_lens requirement to non-sparse backends (#4947)

## Summary

`trtllm_batch_decode_with_kv_cache_mla` rejects the native NoPE form
(`kv_lora_rank=512`, `qk_rope_head_dim=0`) at API entry unless
`sparse_mla_top_k_lens` is provided. That requirement belongs to the
native no-rope trtllm-gen/cute-dsl kernels (#4108), which consume the
per-token active top-k length. The SM120 sparse backend
(`backend="sparse"`, the v32 / GLM53_NOPE families) bounds each row by
its `-1` page-table entries and never reads `sparse_mla_top_k_lens` — so
the entry-level check makes the SM120 GLM-5.3-Flash NoPE path
uncallable. (#4842 hit the same wall and dropped the check wholesale;
this PR keeps the guard where the consuming kernels are instead.)

Move the requirement past backend resolution and apply it only when a
non-`sparse` backend will run. The `sparse_mla_top_k_lens` shape/dtype
validation for callers that do pass it is unchanged, as is the SM100
native-NoPE contract.

## Testing

- vLLM `FLASHINFER_MLA_SPARSE_SM120` + GLM-5.3-Flash-NVFP4, TP4 on 4×RTX
PRO 6000 (SM120): previously raised `Native qk_rope_head_dim=0
TRTLLM-GEN MLA requires sparse_mla_top_k_lens` during CUDA graph
capture; with this change the server boots and serves (companion vLLM
PR: vllm-project/vllm#55277). GSM8K strict-match 0.9325.
- Existing trtllm-gen NoPE callers are unaffected: the requirement still
fires for `trtllm-gen` / `cute-dsl` / `xqa` / unresolved `auto` on
non-SM120 parts.

Signed-off-by: Zihua Wu <zihuaw@nvidia.com>


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Improved validation for sparse attention configurations with positive
top-k values and per-token top-k lengths.
* Updated backend-specific handling so SM120 uses per-token sequence
lengths and rejects unsupported sparse top-k length settings.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: Zihua Wu <zihuaw@nvidia.com>
Co-authored-by: Kimi Code <noreply@moonshot.cn>

### [3e2fb70](https://github.com/flashinfer-ai/flashinfer/commit/3e2fb70777c5d79a816c0ce57ffb300c3189c7ec)

- **作者**: Ka-Hyun Nam
- **时间**: 2026-09-08T21:02:18Z
- **提交信息**: fix(trace): model the SM100/103 cute-dsl mm_bf16_fp4 prepared layout (#4620)

## 📌 Description


`tests/trace/test_mm_bf16_fp4_reference_correctness.py::test_mm_bf16_fp4_reference_correctness[*-cute-dsl]`
fails on the whole SM100 family (12 failures on B300 / GB200 / GB300,
both CUDA versions, in the `v0.6.18rc4` unit-test pipeline):

```
    device = b.device
>   k_sf, n = b_descale.shape
E   ValueError: too many values to unpack (expected 2)
flashinfer/trace/templates/gemm.py:550: ValueError
```

`prepare_bf16_fp4_weights` gained a **third** prepared layout when the
SM100 cute-dsl w4a16 GEMM landed. The trace layer only knew two:

| path | `b` | `b_descale` |
|---|---|---|
| cuDNN | canonical `(N, K//2)` uint8 | linear `(N, K_sf)` fp8-e4m3 |
| cute-dsl SM12x | `(K//16, N*2)` int32 tile-packed | `(K_sf, N)` uint8
S0E5M3 |
| cute-dsl SM100/103 | canonical `(N, K//2)` uint8 | **6-D** `(32, 4,
N//128, 4, K_sf//4, 1)` strided view over the 128x4-swizzled buffer |

Two consequences on SM100/103:

- `mm_bf16_fp4_cute_dsl_trace.reference` unpacks `b_descale.shape` as
2-D and raises the `ValueError` above.
- `mm_bf16_fp4_trace_dispatch` keys off the weight dtype (`int32` →
cute-dsl), and the SM100 weight is `uint8`, so a cute-dsl call silently
resolves to the **cuDNN** template. Shapes are not validated at trace
time, so this would have quietly dumped a definition labelled
`mm_bf16_fp4_cudnn` describing the wrong prepared layout.

This PR adds `mm_bf16_fp4_cute_dsl_sm100_trace` with its own init and
reference, restricts the SM12x init to SM12x, and gives the dispatch a
discriminator for all three layouts.

The new reference recovers the canonical scale buffer by permuting the
strided view back to its documented physical order —
`convert_sf_to_mma_layout` returns logical `(outer_m, inner_m, m_tile,
inner_k, k_tile, group)` over physical `(group, m_tile, k_tile, 32, 4,
4)`, which is exactly what `_unswizzle_sf_128x4` expects — then decodes
the canonical nvfp4 weight the same way the cuDNN reference does. I
checked that reconstruction against `_unswizzle_sf_128x4` of the
pre-`convert` buffer, and independently against the documented
element-wise index mapping; both are bit-exact.

## 🔍 Related Issues

Regression from #4466 (`feat: sm100 cute_dsl w4a16 gemm`), which added
the SM100 prepared layout without touching the trace layer. Not
previously reported upstream.

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

Verified on a B200 (SM100, CUDA 13.0, cutlass-dsl 4.7.0), where the test
reproduces the reported `ValueError` before the change:

- `tests/trace/test_mm_bf16_fp4_reference_correctness.py` — 4 failed → 4
passed
- `tests/gemm/test_mm_bf16_fp4.py` — 242 passed, 3 skipped
- `tests/trace/test_fi_trace_template_consistency.py`,
`test_template_registry.py`, `test_template_init.py`,
`test_rendered_source_standalone.py`, `test_fi_trace.py` — 1050 passed,
180 skipped

The reference test now picks the cute-dsl template matching the device
and asserts `mm_bf16_fp4_trace_dispatch` resolves a real prepared call
back to that template, so the misrouting cannot come back unnoticed.

## Reviewer Notes

Worth a second opinion on two judgement calls:

1. **A separate template rather than one branching reference.** The
declared `axes`/`inputs` are what land in the dumped definition, and the
SM100 weight and scale shapes differ from SM12x, so a single template
cannot describe both honestly. If you would rather not trace this layout
at all, the alternative is to make the SM12x init raise on SM100/103 and
stop there — that also turns the failure into a skip, but leaves the
dispatch mislabelling SM100 cute-dsl calls as cuDNN.
2. **Declaring a non-contiguous 6-D view as a template input.** It is an
odd thing to put in a bench definition since it is a view, not an
allocation. I described it as-is rather than substituting the underlying
canonical buffer, because that view is literally what callers pass to
`mm_bf16_fp4`. Happy to change the dim naming if you prefer something
else.

I have no SM103 hardware; the SM100 and SM103 paths share
`_prepare_cute_dsl_sm100`, so the gating treats them together.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added support for BF16×FP4 operations on SM100/103 GPUs with
six-dimensional scale tensors.
* Automatically selects the appropriate processing path based on tensor
format and GPU capability.

* **Bug Fixes**
* Improved scale reconstruction and dequantization accuracy for
supported SM100/103 workloads.

* **Tests**
* Expanded correctness coverage for backend and GPU-specific template
selection.
  * Tests now handle environments without CUDA gracefully.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [9c10d2e](https://github.com/flashinfer-ai/flashinfer/commit/9c10d2e8f23a18631dcf21551276910678249b3f)

- **作者**: Anerudhan Gopal
- **时间**: 2026-09-08T17:35:23Z
- **提交信息**: Nccl extensions dependency update (#5016)

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

## 🔬 Experimental Track

<!-- Only for PRs submitted under the experimental policy
(CONTRIBUTING.md → "Experimental APIs and Backends").
     Leave this section untouched for normal PRs. -->

- [ ] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.
Tracking issue: #
- [ ] The tracking issue names an owner, the reason for the experimental
path, and a graduation plan with a target release.
- [ ] Core changes are limited to a thin entry point (signature, shared
validation, feature-gate check, backend selection, handoff).
- [ ] Tests live in `tests/experimental/` and were validated on the
intended hardware; a runnable example is included.
- [ ] Nothing is registered in `flashinfer/aot.py`, and no experimental
backend is reachable from `backend="auto"` without
`FLASHINFER_ALLOW_EXPERIMENTAL_AUTO_BACKENDS=1`. (Calling an
`@flashinfer_experimental_api` or naming a backend explicitly is itself
the opt-in and needs no environment variable.)
- [ ] **Test scope declared below.** The experimental CI lane runs
exactly these targets, so keep them as narrow as the change allows.

<!-- Required for experimental PRs. Replace the commented lines below
with your targets.
Do not delete the fence or change its `experimental-tests` tag — the
experimental-track
watcher reads it verbatim to decide which targets to ask CI for. -->

```experimental-tests
# One target per line: a directory or a file. (A pytest ::selector is not
# supported -- the sharding runner cannot consume one.) Must be under
# tests/experimental/ and must exist. Delete these comment lines and add yours, e.g.
#
#   tests/experimental/test_my_backend.py
#   tests/experimental/my_backend/
#
# Declaring the whole tree (tests/experimental/) is allowed but means every
# experimental PR pays for every other feature's tests, in every matrix cell.
```

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

- **New Features**
- Added support for the `nccl-extensions` package as the provider of
NCCL-EP functionality.
- Improved runtime library selection across CUDA environments and
ensured the correct NCCL library version is loaded.
  - Added NCCL-EP package version reporting.

- **Bug Fixes**
- NCCL version checks now prioritize the actively loaded library, with
metadata fallback when unavailable.
- Updated container builds and installation scripts to use compatible
NCCL-EP packages and runtime libraries.

- **Documentation**
- Updated setup guidance, dependency references, architecture notes, and
troubleshooting messages to reflect the new package split.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [2fe65eb](https://github.com/flashinfer-ai/flashinfer/commit/2fe65eb0eda475d4bd8ecf3afd618fe2b09dec25)

- **作者**: Alex Yang
- **时间**: 2026-09-08T16:50:23Z
- **提交信息**: feat: Add valid_hidden_size and valid_intermediate_size params t… (#2482)

<!-- .github/pull_request_template.md -->

## 📌 Description

Expose padded vs valid dimension support in the TRT-LLM fused MOE
kernels. This allows tensors to be padded for alignment while computing
only the valid region.

- Add valid dimension fields to MoERunnerArgs
- Update batched GEMM runner to accept optional validM/N/K params
- Propagate valid dimensions through PermuteGemm1 and Gemm2 runners
- Add valid_hidden_size and valid_intermediate_size kwargs to Python API

## 🔍 Related Issues
https://github.com/flashinfer-ai/flashinfer/issues/2372

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
* Optional unpadded "valid" dimensions for batched GEMM and MoE GEMM
stages; MoE accepts valid_hidden_size/valid_intermediate_size and
supports hidden_size_output distinct from input hidden size.
* Autotuning/config validation now considers output hidden size when
selecting valid tactics.

* **Tests**
* Added unit tests for output-hidden-size inference and CUDA integration
tests validating behavior against unpadded references.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 4.5 <noreply@anthropic.com>

### [2f02420](https://github.com/flashinfer-ai/flashinfer/commit/2f0242067dd0879100b3c23d4e53c5b1b431cb5a)

- **作者**: Haozheng Fan
- **时间**: 2026-09-08T16:46:34Z
- **提交信息**: feat(cake_mega_moe): add optimized MXFP8 MegaMoE EP16 backend (#4970)

## 📌 Description

Adds an experimental exact-SM103a MXFP8 MegaMoE EP16 path for hidden
size
3072, intermediate size 5120, 512 experts, top-k 8, and 16/32/64 tokens
per
rank.

## API behavior

- `CakeMxfp8MegaMoeEp16(weights, topk_ids, process_group=...)` prepares
the
  immutable route and execution metadata once, then reuses caller-owned
  symmetric buffers.
- The execution path supports current-stream use and CUDA Graph capture
and
  replay without allocations in the submitted region.
- Output is written directly to the session's symmetric output buffer.
- Both public entry points are explicitly experimental and the
implementation,
  JIT loader, and generated sources are contained under
  `flashinfer.experimental`.

## Kernel design

- Each replay has three physical kernels: input quantization and
publication;
fused dispatch, FC1, SwiGLU, FC2, and top-k combine; and final reduction
  completion.
- The fused kernel uses N32/K128 tiles, four FC1 stages, eight FC2
stages, and
  a 128-CTA persistent grid.
- The SwiGLU intermediate remains FP32 through route weighting and MXFP8
quantization, avoiding an early BF16 rounding boundary. The sigmoid
follows
  FlashInfer's exp2/reciprocal arithmetic order.
- Intra-GPU phase synchronization uses GPU-scope release/acquire
operations
  with last-arrival reset. System scope is limited to required cross-GPU
  publication.

## Final validation

- All three balanced shapes pass finite-output and `atol=rtol=1e-2`
correctness. Maximum absolute error is 0.0078125 and maximum relative L2
is
  0.000637.
- Outputs are bitwise deterministic across three fresh distributed
processes
and 32 consecutive launches per process for every shape (288/288
candidate
  launches, each covering all 16 ranks).
- Every reportable replay has exactly three correlated GPU kernel
activities
  and zero device allocations or frees in the submitted region.
- Focused experimental API, layout, and generated-closure tests pass
(4/4),
  along with Python compilation, Ruff, and whitespace checks.

## Kernel performance

Measurements are same-device, order-balanced, cold-L2 CUPTI runs on 16
GB300
GPUs with CUDA Graph replay. Each shape uses three independent
counterbalanced
groups, 100 ms warmup, and a 1,000 ms reportable budget per arm per
group. The
baseline is FlashInfer `60b49158`; subsequent main changes through
`f67bc2ed`
do not modify the measured MXFP8 MegaMoE path.

| Global tokens | This PR (ms) | FlashInfer (ms) | Throughput speedup |
Max abs error | Relative L2 | GPU activities |
| ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| 256 | 0.286208 | 0.313088 | 1.093918x (+9.39%) | 0.0078125 | 0.000637
| 3 |
| 512 | 0.288513 | 0.318624 | 1.104366x (+10.44%) | 0.0078125 | 0.000500
| 3 |
| 1024 | 0.288448 | 0.320832 | 1.112270x (+11.23%) | 0.0078125 |
0.000451 | 3 |
| geometric mean | 0.287721 | 0.317498 | **1.103492x (+10.35%)** | - | -
| 3 |

## 🔍 Related Issues

Related to #4969.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used my preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed reported issues.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All focused tests are passing.

## 🔬 Experimental Track

- [x] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.
Tracking issue: #4969
- [x] The tracking issue names an owner, the reason for the experimental
path, and a graduation plan with a target release.
- [x] Core changes are limited to a thin entry point (signature, shared
validation, feature-gate check, backend selection, handoff).
- [x] Tests live in `tests/experimental/` and were validated on the
intended hardware; a runnable example is included.
- [x] Nothing is registered in `flashinfer/aot.py`, and the backend is
not reachable from `backend="auto"`.
  - [x] **Test scope declared below.**

```experimental-tests
tests/experimental/test_cake_mxfp8_megamoe_ep16.py
```

## Reviewer Notes

The main review surfaces are the reusable GPU-scope phase counter in the
fused
kernel and the direct symmetric-output ownership contract.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **New Features**
- Added an experimental MXFP8 MegaMoE inference backend for exact SM103a
devices.
- Supports 16-way expert parallelism, 512 experts, top-8 routing, and
BF16 activations and outputs.
- Added public APIs for weight preprocessing, session creation, and
inference execution.
  - Added a runnable 16-rank example.

- **Documentation**
- Added usage documentation covering supported configurations, JIT-only
availability, and limitations.

- **Tests**
- Added coverage for API flags, JIT manifests, and scale-packing
configurations.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Haozheng Fan <18756967+hzfan@users.noreply.github.com>
Co-authored-by: Yingyi Huang <yingyihuang2000@outlook.com>
Co-authored-by: Alex Yang <aleyang@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [6aa08ae](https://github.com/flashinfer-ai/flashinfer/commit/6aa08ae19868a26ad3997f3b464752e8cbe732e9)

- **作者**: Miguel
- **时间**: 2026-09-08T16:27:19Z
- **提交信息**: fix(kda): compile direct serving modules as C++20 (#5017)

## 📌 Description

Generated FlashKDA direct-M128 serving modules include ATen headers.
PyTorch 2.14 requires C++20, while the shared JIT helper defaults to
C++17. This adds an explicit standard only to direct serving specs, so
unrelated modules retain C++17.

## 🔍 Related Issues

Fixes #4995.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit`.
- [x] I have installed the hooks.
- [x] I have run `pre-commit run --all-files` and fixed any reported
issues.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

The focused regression passes locally. The full CUDA 13 and PyTorch 2.14
JIT-cache build requires project CI.

## 🔬 Experimental Track

- [ ] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.
Tracking issue: #
- [ ] The tracking issue names an owner, the reason for the experimental
path, and a graduation plan with a target release.
- [ ] Core changes are limited to a thin entry point (signature, shared
validation, feature-gate check, backend selection, handoff).
- [ ] Tests live in `tests/experimental/` and were validated on the
intended hardware; a runnable example is included.
- [ ] Nothing is registered in `flashinfer/aot.py`, and no experimental
backend is reachable from `backend="auto"` without
`FLASHINFER_ALLOW_EXPERIMENTAL_AUTO_BACKENDS=1`. (Calling an
`@flashinfer_experimental_api` or naming a backend explicitly is itself
the opt-in and needs no environment variable.)
- [ ] **Test scope declared below.** The experimental CI lane runs
exactly these targets, so keep them as narrow as the change allows.

```experimental-tests
# One target per line: a directory or a file. (A pytest ::selector is not
# supported; the sharding runner cannot consume one.) Must be under
# tests/experimental/ and must exist. Delete these comment lines and add yours, e.g.
#
#   tests/experimental/test_my_backend.py
#   tests/experimental/my_backend/
#
# Declaring the whole tree (tests/experimental/) is allowed but means every
# experimental PR pays for every other feature test, in every matrix cell.
```

## Reviewer Notes

Please verify the generated direct-NVRTC modules against PyTorch 2.14 in
the scheduled JIT-cache environment.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Updated generated FlashKDA direct-serving modules to compile with the
C++20 standard, improving compatibility with supported builds.

* **Tests**
* Expanded validation of generated direct-serving modules to cover both
`sm100a` and `sm103a` targets.
* Verified that each target selects and validates its matching generated
variant.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Miguel Garcia <miguelgarciaroman8@gmail.com>

### [291ce2e](https://github.com/flashinfer-ai/flashinfer/commit/291ce2ecddeb31eac5d8c373efb20d37c53700f8)

- **作者**: Cindy Zhang
- **时间**: 2026-09-08T15:47:30Z
- **提交信息**: fix(docs): deploy stable documentation from release tags (#4945)

<!-- .github/pull_request_template.md -->

## 📌 Description

The documentation site currently deploys on every push to `main`, while
its displayed version comes from `version.txt`. As a result, the site
can be labeled as a released version (currently `0.6.18`) while
documenting APIs that only exist on `main`.

  This PR separates documentation validation from production deployment:

- Continue building documentation for pull requests and pushes to
`main`.
- Build and validate documentation for `v*` tag pushes without deploying
it.
  - Deploy production documentation only:
    - after the release workflow completes successfully; or
    - through an explicit manual dispatch for an existing release tag.
  - Validate that the requested release tag:
    - has a supported version format;
    - matches `version.txt`; and
    - resolves to the checked-out commit.
  - Split documentation build and deployment into separate jobs.
- Scope the `pages` concurrency group to the deployment job so ordinary
`main`/PR builds cannot replace a pending release deployment.
- Restrict GitHub Pages write and OIDC permissions to the deployment
path.
  - Make the documentation workflow reusable from `release.yml`.
- Run documentation deployment only after the GitHub Release, PyPI
publication,and wheel-index update have all succeeded.

After this PR is merged, the current site can be repaired by manually
running the `Build FlashInfer Docs` workflow from `main` with:
  ```text
  release_tag: v0.6.18
```
  This rebuilds the site from the immutable v0.6.18 tag rather than from main.


## 🔍 Related Issues
https://github.com/flashinfer-ai/flashinfer/issues/4934

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit` (or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files` and fixed any reported issues.

> If you are unsure about how to set up `pre-commit`, see [the pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests
- [x] Tests have been added or updated as needed. No unit tests are applicable
    because this is a GitHub Actions workflow-only change.

- [x] Static validation completed:
      - both modified YAML files parse successfully;
      - the release dependency chain and deploy-job isolation were checked;
      - the release-tag validation script passes bash -n;
      - git diff --check passes;
      - the existing v0.6.18 tag matches its version.txt and checked-out commit.

## Reviewer Notes
Please focus on:

  1. Whether documentation should wait for all of create-release, publish-to-pypi, and update-wheel-index before deployment.
  2. The reusable-workflow permission chain for pages: write and id-token: write.
  3. The intentional behavior that a v* tag push builds and validates documentation but does not deploy it.
  4. The manual workflow_dispatch path used to restore the current site from v0.6.18.


<!-- This is an auto-generated comment: release notes by coderabbit.ai -->
## Summary by CodeRabbit

* **New Features**
  * Documentation builds now run automatically for pushes, pull requests, and version tags, or can be triggered manually and reused by other workflows.
  * Release workflows can deploy documentation for published releases.
  * Documentation deployment uses dedicated permissions and serialized runs to prevent overlapping deployments.

* **Bug Fixes**
  * Release-tag deployments validate the tag format, project version, and checked-out commit.
  * Prevented deployments from using a branch with the same name as a release tag.
  * Limited documentation artifacts and deployment to release-tag runs.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [af9b148](https://github.com/flashinfer-ai/flashinfer/commit/af9b148e9133880154e33dc22205403b8b9698e6)

- **作者**: Samuel Nordmann
- **时间**: 2026-09-08T15:44:35Z
- **提交信息**: perf(moe): phase NVFP4 dispatch payload copies at EP4/EP8/EP16 (#4067)

## Summary

Follow-up to #3846. The generic dispatch kernel makes every CTA thread
build remote destination pointers for every payload before determining
whether that thread owns any bytes. NVFP4 has four predictably
asymmetric payloads, so this change gives each payload only the workers
it needs:

- two warps for packed activations;
- the required lanes of one warp for scales;
- two lane groups in the final warp for expert IDs and routing weights.

EP4 retains its compact per-rank destination list. EP8 and EP16 retain
the existing top-k-sized representation; only their copy schedule
changes. The phased path is gated to EP `{4, 8, 16}`, a 128-thread CTA,
and validated four-payload NVFP4 layouts. Unsupported EP sizes, top-k
values, widths, and payload layouts use the existing generic kernel.

The H2048/top-k-22 target retains compile-time payload widths. Validated
smaller layouts use the same schedule with runtime activation and scale
widths.

## Performance

### Single op

GB200, H2048, top-k 22, CUDA graphs. EP8 and EP16 are true global
expert-parallel groups spanning two and four nodes.

| Global EP | Nodes | Tokens/rank | Baseline | Candidate | Delta |
|---:|---:|---:|---:|---:|---:|
| 4 | 1 | 1 | 13.480 us | 12.862 us | -4.58% |
| 4 | 1 | 4 | 14.408 us | 13.490 us | -6.37% |
| 4 | 1 | 64 | 16.511 us | 15.284 us | -7.43% |
| 4 | 1 | 512 | 18.155 us | 17.804 us | -1.93% |
| 4 | 1 | 8192 | 55.072 us | 54.689 us | -0.70% |
| 8 | 2 | 1 | 16.270 us | 13.877 us | -14.71% |
| 8 | 2 | 4 | 18.394 us | 14.679 us | -20.20% |
| 8 | 2 | 64 | 21.253 us | 17.358 us | -18.33% |
| 8 | 2 | 512 | 40.520 us | 27.275 us | -32.69% |
| 8 | 2 | 1024 | 64.713 us | 37.797 us | -41.59% |
| 8 | 2 | 8192 | 308.292 us | 96.494 us | -68.70% |
| 16 | 4 | 1 | 18.107 us | 15.733 us | -13.11% |
| 16 | 4 | 4 | 21.639 us | 17.328 us | -19.92% |
| 16 | 4 | 64 | 25.264 us | 20.652 us | -18.26% |
| 16 | 4 | 512 | 55.275 us | 41.484 us | -24.95% |
| 16 | 4 | 1024 | 100.321 us | 68.156 us | -32.06% |
| 16 | 4 | 8192 | 373.115 us | 176.750 us | -52.63% |

### E2e workload

On the **Nemotron Ultra NVFP4 end-to-end** workload (2 GB200 nodes,
TP1/DP8/EP8, FlashInfer one-sided, CUDA graphs, ISL/OSL 8192/8,
concurrency 8), mean TTFT improves from 860.8 ms to 839.9 ms
(**-2.43%**, 95% CI [-3.44%, -1.41%]). Throughput (+0.62%) and TPOT are
statistically on par.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

## Summary by CodeRabbit

* **New Features**
* Added support for additional phased NVFP4 layouts in
Mixture-of-Experts all-to-all dispatch.
* Added a specialized H2048 phased dispatch path, including top‑k=22
configurations.
* **Performance**
* Improved dispatch efficiency by optimizing activation, scale, and
routing-metadata movement.
* **Bug Fixes**
* Strengthened validation to ensure payload layouts match runtime
settings.
* **Tests**
* Updated NVFP4 payload generation and expanded phased H2048 coverage
across supported configurations.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: snordmann <snordmann@nvidia.com>

### [a056187](https://github.com/flashinfer-ai/flashinfer/commit/a056187dc4f6c5feb143182271650d63ddb04501)

- **作者**: kangbintNV
- **时间**: 2026-09-08T15:40:52Z
- **提交信息**: docs: resolve documentation check failures (#4927)

## Summary

Fix the blocking findings from the FlashInfer 0.6.18 documentation
report at `91bda04c`:

- document `cute_dsl_fused_moe_bf16` under the public fused-MoE API
surfaces
- add RST coverage and complete parameter documentation for
`bsa_attn_sm120_blk64_sage_fwd`

The `FLASHINFER_CACHE_DIR/autotune` finding is a checker false positive
handled in
[flashinfer_document_check!14](https://gitlab-master.nvidia.com/dlswqa/flashinfer/flashinfer_document_check/-/merge_requests/14),
not by changing FlashInfer documentation.

The 41 `STALE` warnings are intentionally left unchanged. This PR does
not add `@flashinfer_api` decorators or otherwise change those API
classifications.


## Validation

- full API/RST checker: `MISSING 0`, `STALE 41` (warnings unchanged)
- docstring checker: `0` completeness failures, `0` args-consistency
failures
- PR documentation checker against `origin/main`: `0 new finding(s)`
- targeted pre-commit: passed (mypy, ruff, formatting,
experimental-scope self-test, and repository hygiene hooks)
- Python compilation: passed for the modified Sage BSA module

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

- **Documentation**
- Added API documentation for block-sparse attention and four CuteDSL
fused MoE functions, including BF16 support.
- Expanded block-sparse attention reference documentation with
parameter, return-value, shape, and constraint details.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-09-09
**监控日期**: 2026-09-08
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4356
- **最后更新**: 2026-09-08T19:39:18Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Aryan Kumar

## AI分析总结

### 主要更新类型
- **Bug修复**：本次提交属于缺陷修复，移除了Spark FastH3预设中失效的`h3_sequential_load`参数。

### 关键变更点及其与项目整体方向的关系
- 变更内容：从FastH3预设中删除已废弃的`h3_sequential_load`配置项。该参数在Spark场景下已无实际作用，保留会导致配置冗余或潜在错误。
- 与项目方向的关系：FastVideo聚焦于高效视频生成与处理，其Spark集成用于大规模数据预处理。清理无效配置有助于保持代码库整洁，降低用户误用风险，符合项目对稳定性和易用性的追求。

### 对项目的影响和潜在意义
- **影响**：消除因无效参数引发的潜在运行时警告或错误，简化Spark用户的配置流程。
- **潜在意义**：减少维护成本，避免新用户复制旧配置时踩坑；同时为后续Spark相关功能迭代扫清障碍，提升整体可靠性。

### 值得关注的技术点
- 该修复体现了对Spark生态中API变更的及时跟进——`h3_sequential_load`可能因上游版本更新而废弃，项目团队主动清理，说明其依赖管理较为严谨。
- 提交由AI辅助（Cursor Agent）与人工协作完成，反映了开发流程中自动化工具与人工审查结合的趋势。

### 基于README背景，这些提交如何影响项目发展
- FastVideo定位于提供快速、可扩展的视频生成方案，其Spark集成服务于大规模数据处理环节。本次修复虽小，但直接关系到Spark用户的上手体验与任务稳定性。
- 持续清理技术债、紧跟上游变化，有助于项目在快速迭代中保持高质量，增强社区信任度，为后续吸引更多贡献者和企业用户奠定基础。
- 整体来看，这类细节修复虽不引入新功能，但对项目长期健康发展和用户留存具有积极意义。

## 详细提交记录

### [a943220](https://github.com/hao-ai-lab/FastVideo/commit/a943220c115228ade5d57b3bab9a6a87fd600a10)

- **作者**: Aryan Kumar
- **时间**: 2026-09-08T19:38:06Z
- **提交信息**: [bugfix]: drop dead h3_sequential_load from Spark FastH3 presets (#1831)

Co-authored-by: Cursor Agent <cursoragent@cursor.com>
Co-authored-by: Aryan Kumar <aryan5v@users.noreply.github.com>

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-09-09
**监控日期**: 2026-09-08
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34463
- **最后更新**: 2026-09-08T21:25:13Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Jeremy Schoemaker

## AI分析总结

### 提交分析总结

**1. 主要更新类型**  
本次提交属于 **Bug修复**，针对多个FlowMatch系列管线中调度器起始索引未正确设置的问题，属于性能与正确性修复范畴。

**2. 关键变更点与项目方向关系**  
变更将`set_begin_index(0)`修复从单一管线推广至HunyuanVideo、Mochi、Lumina2、AuraFlow及Chroma等文本到图像/视频管线。这些管线均基于FlowMatch调度器，是diffusers库中面向最新扩散模型（如视频生成、高分辨率图像）的核心组件。修复确保了调度器在首次去噪步骤中正确初始化索引，避免因设备同步导致的性能退化。这与项目追求**高效、可扩展的扩散模型工具链**目标一致，尤其强化了多模态（图像+视频）生成管线的稳定性。

**3. 项目影响与潜在意义**  
- **性能提升**：消除首个去噪步骤中的设备到主机（DtoH）同步，减少延迟，对实时或批量推理场景有直接收益。  
- **正确性保障**：避免因索引未初始化导致的潜在错误步进，确保生成质量一致。  
- **代码一致性**：将分散的修复统一至所有FlowMatch管线，降低后续维护成本，防止同类问题复发。  
- **用户影响**：修复了#14573问题，提升使用这些新管线（如HunyuanVideo）的开发体验，增强社区信任。

**4. 值得关注的技术点**  
- **设备同步瓶颈**：`nonzero().item()`在GPU上强制同步，是性能杀手。通过预置`begin_index`绕过`_init_step_index()`的隐式同步，是优化扩散模型推理的典型技巧。  
- **修复传播策略**：从单一管线（#11696）推广至全家桶，体现了“修复根因而非打补丁”的工程思维，值得借鉴。  
- **FlowMatch调度器特殊性**：其步进逻辑对索引初始化敏感，此修复可能为未来新管线提供默认最佳实践。

**5. 对项目发展的影响**  
基于README，diffusers致力于成为最全面、易用的扩散模型库。此次修复虽小，但直接巩固了其对**前沿视频生成模型**（如HunyuanVideo、Mochi）的支持质量，降低了用户采用新架构的门槛。通过消除隐性性能陷阱，项目能更自信地扩展新管线，同时保持“开箱即用”的承诺。长期看，此类系统性修复有助于积累技术信誉，吸引更多研究者贡献新模型，形成良性生态循环。整体上，提交是项目在成熟度与专业性上的一次稳健推进。

## 详细提交记录

### [040c7cd](https://github.com/huggingface/diffusers/commit/040c7cde626504d14caf63b13b8b25b6a9f62120)

- **作者**: Jeremy Schoemaker
- **时间**: 2026-09-08T21:24:39Z
- **提交信息**: Set scheduler begin index in remaining FlowMatch pipelines to avoid DtoH sync (#14576)

Propagate the set_begin_index(0) fix from #11696 to HunyuanVideo, Mochi,
Lumina2, AuraFlow, and Chroma text-to-image/video pipelines. Without it,
the first scheduler.step() routes through _init_step_index() ->
index_for_timestep(), whose nonzero().item() forces a device-to-host
sync on the first denoising step. Fixes #14573.

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-09-09
**监控日期**: 2026-09-08
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


**报告日期**: 2026-09-09
**监控日期**: 2026-09-08
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13068
- **最后更新**: 2026-09-08T17:49:08Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 2
- **主要提交者**: Zhongjie Duan, Hong Zhang

## AI分析总结

# DiffSynth-Studio 提交分析

## 主要更新类型
本次提交以**功能新增**为主，辅以版本更新和代码重构，无明显的Bug修复或性能优化内容。

## 关键变更点
1. **新增MiniMax-H3训练适配器**：为训练脚本添加可选的MiniMax-H3适配器预设，并同步更新了新闻条目。同时，从全量微调脚本中移除了适配器预设块，表明该功能仅面向特定训练场景（而非全量微调）。
2. **版本升级至2.1.7**：常规版本迭代，可能包含此前累积的修复或小改进。
3. **支持从状态字典加载模板模型**：增强了模型加载的灵活性，允许直接通过state dict初始化模板模型，而非仅依赖完整模型文件。

## 与项目方向的关系
DiffSynth-Studio作为面向视频/图像合成与编辑的扩散模型工具库，其核心价值在于**降低模型训练与推理的工程门槛**。MiniMax-H3适配器的加入，直接扩展了项目对**外部先进模型（如MiniMax系列）** 的兼容性，符合项目“集成多源模型生态”的定位。而“从state dict加载模板”则服务于**模型复用与迁移**场景，呼应了项目对灵活部署和二次开发的支持。

## 影响与潜在意义
- **生态扩展**：MiniMax-H3适配器使社区用户能更便捷地基于该模型进行定制训练，可能吸引MiniMax生态的开发者加入，扩大用户基础。
- **工程简化**：移除全量微调中的适配器块，避免了配置冗余，降低了误用风险；state dict加载则减少了模型文件管理的复杂度，有利于CI/CD或自动化流程。
- **版本节奏**：快速迭代至2.1.7，表明项目维护活跃，对社区反馈响应及时。

## 值得关注的技术点
- **适配器与全量微调的分离设计**：体现了对“参数高效微调”与“全量训练”两种范式的清晰划分，符合当前大模型训练的主流实践。
- **state dict加载的兼容性处理**：需关注其与现有模型注册机制的衔接，是否支持部分权重加载或跨架构迁移，这将是后续扩展性的关键。

## 对项目发展的影响
结合README中项目强调的“多模型支持”与“易用性”目标，本次提交通过**横向扩展模型兼容性**和**纵向优化加载机制**，双维度巩固了DiffSynth-Studio作为一站式合成工具的地位。MiniMax-H3适配器可能成为吸引新用户群体的亮点，而state dict加载则为高级用户提供了更细粒度的控制能力。整体上，这些变更推动项目向**更开放、更灵活**的方向演进，有助于在竞争激烈的生成式AI工具链中保持差异化优势。

## 详细提交记录

### [ce9f454](https://github.com/modelscope/DiffSynth-Studio/commit/ce9f4541d0f4ae47a138337e59066dd633207aa7)

- **作者**: Hong Zhang
- **时间**: 2026-09-08T10:46:42Z
- **提交信息**: Add optional MiniMax-H3 Training Adapter (#1678)

* Add optional MiniMax-H3 Training Adapter preset to training scripts and a news entry

* Drop the Training Adapter preset block from full fine-tuning scripts

* Mention the self-generated MiniMax-H3 dataset in the Training Adapter news entry

### [7822d17](https://github.com/modelscope/DiffSynth-Studio/commit/7822d1781287971d24bf94e09bd487ce21ee08d8)

- **作者**: Zhongjie Duan
- **时间**: 2026-09-08T07:42:37Z
- **提交信息**: update to version 2.1.7 (#1677)

### [a23ae53](https://github.com/modelscope/DiffSynth-Studio/commit/a23ae53d6527417ef16a85469d5f08c9dafb2338)

- **作者**: Zhongjie Duan
- **时间**: 2026-09-08T07:41:10Z
- **提交信息**: support loading template models from state dict (#1676)

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-09-09
**监控日期**: 2026-09-08
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 35655
- **最后更新**: 2026-09-08T23:45:10Z

## 提交统计

- **昨日提交总数**: 28
- **提交者数量**: 22
- **主要提交者**: Po-Han Huang (NVIDIA), Xinyuan Tong, amd-danli103

## AI分析总结

## 提交分析总结

### 1. 主要更新类型
- **性能优化**：占比最高，涵盖调度策略、内核优化、显存管理等多个层面
- **硬件适配**：AMD gfx950、Blackwell B200/B300、NPU等平台支持
- **功能新增**：MiniMax-M3模型优化、Ling-3.0-flash-VL cookbook、HiCache MLA去重
- **代码清理与重构**：废弃API移除、CP V1弃用过渡、类型清理
- **Bug修复**：DSA压缩容量、延迟追踪属性缺失等问题
- **文档更新**：模型部署指南、cookbook新增

### 2. 关键变更点与项目方向
- **调度策略革新**：引入HRRN调度策略显著降低TTFT，直击LLM服务核心痛点
- **模型专项优化**：MiniMax-M3的Triton split-K router与跨层稀疏索引共享，体现对MoE架构深度优化
- **硬件生态扩展**：AMD gfx950汇编级attention、NPU EAGLE支持，强化多硬件平台竞争力
- **架构清理**：移除get_global_server_args等废弃接口，推进CP V1弃用，为V2铺路
- **显存与传输优化**：HiCache MLA去重、流式权重映射、Mooncake传输批量限制，提升资源利用效率

### 3. 项目影响与潜在意义
- **服务体验提升**：HRRN调度与PD OOM修复直接改善用户感知的TTFT和稳定性
- **推理成本降低**：MoE路由优化、fp32权重保持、显存复用等技术减少计算与存储开销
- **平台覆盖扩大**：AMD/NPU/Blackwell适配使项目从NVIDIA独占走向多硬件生态
- **架构现代化**：废弃API清理和CP V1过渡表明项目正加速向更清晰、可维护的架构演进

### 4. 值得关注的技术点
- **HRRN调度策略**：在LLM推理中引入操作系统调度思想，是调度领域的新尝试
- **Triton split-K router**：利用Triton语言实现高性能MoE路由，兼顾灵活性与性能
- **gfx950汇编级优化**：针对AMD最新架构的手写汇编，体现极致性能追求
- **DSA压缩容量修复**：涉及PD场景下显存压缩的边界条件处理，细节影响稳定性
- **fp32路由权重保持**：在低精度量化下保留关键权重精度，平衡性能与质量

### 5. 对项目发展的影响
SGLang正从单一NVIDIA GPU推理框架向**多硬件、全场景、高可扩展**的通用LLM服务系统演进。调度策略创新和模型专项优化巩固其性能领先地位；AMD/NPU/Blackwell适配拓展用户基础；架构清理为长期可维护性奠基。同时，大量性能优化和显存管理改进表明项目正从“功能可用”迈向“生产级高效”，这对吸引企业用户和构建健康开源生态至关重要。整体呈现“性能驱动+生态扩张+架构现代化”的三线并行发展态势。

## 详细提交记录

### [db27220](https://github.com/sgl-project/sglang/commit/db272201a2dbd72e5699e443240a851f1313ad45)

- **作者**: Cheng Wan
- **时间**: 2026-09-08T23:42:12Z
- **提交信息**: [Config] Retire get_global_server_args, and clear the deprecated flags that have a replacement (#38375)

### [5177a3e](https://github.com/sgl-project/sglang/commit/5177a3ec08548b3d0f1a9eea43d0b721959116d9)

- **作者**: Chunan Zeng
- **时间**: 2026-09-08T23:39:41Z
- **提交信息**: MiniMax-M3: Triton split-K router GEMV with in-kernel fixup (#36557)

Co-authored-by: Kevin Mi <45493463+kevin-mii@users.noreply.github.com>

### [a25bbca](https://github.com/sgl-project/sglang/commit/a25bbca8edfae56c0513a8517401c20fd11cc6fa)

- **作者**: Chunan Zeng
- **时间**: 2026-09-08T23:39:01Z
- **提交信息**: MiniMax-M3: share the sparse index top-k across layers and reuse the decode top-k buffer (#36527)

Co-authored-by: Kevin Mi <mikevin920@yahoo.com>

### [ed183d4](https://github.com/sgl-project/sglang/commit/ed183d45acfb0f6d1a2b1cd6b6a34a579e1a3ad7)

- **作者**: Baizhou Zhang
- **时间**: 2026-09-08T23:03:36Z
- **提交信息**: [CP V1 Deprecation 4/5] Canonicalize prefill CP API names (#36229)

### [559c7fa](https://github.com/sgl-project/sglang/commit/559c7fa75b767cb7a56c1853c18b8cd093a952a7)

- **作者**: Qiaolin Yu
- **时间**: 2026-09-08T22:57:44Z
- **提交信息**: Revert "PD disaggregation, isolated transfer, prefill OOM fixed." (#38572)

### [52fecfd](https://github.com/sgl-project/sglang/commit/52fecfdf0908dca24f4c6799ff5967125cc4110e)

- **作者**: Qiaolin Yu
- **时间**: 2026-09-08T20:56:21Z
- **提交信息**: support qwen 3.8 flash next (#37500)

Co-authored-by: ch-wan <54331508+ch-wan@users.noreply.github.com>
Co-authored-by: ispobock <26454835+ispobock@users.noreply.github.com>
Co-authored-by: JustinTong0323 <115166877+JustinTong0323@users.noreply.github.com>
Co-authored-by: samuellees <26428561+samuellees@users.noreply.github.com>
Co-authored-by: YAMY1234 <74099316+YAMY1234@users.noreply.github.com>
Co-authored-by: yhyang201 <47235274+yhyang201@users.noreply.github.com>
Co-authored-by: yizhang2077 <25844240+yizhang2077@users.noreply.github.com>
Co-authored-by: zijiexia <37504505+zijiexia@users.noreply.github.com>
Co-authored-by: Shinto C V <cshintov@gmail.com>
Co-authored-by: Julian Huang <huangzhilin.hzl@antgroup.com>
Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>
Co-authored-by: yhyang201 <yhyang201@gmail.com>

### [afe90a8](https://github.com/sgl-project/sglang/commit/afe90a8bc908002219993794404c7c95dd3ced1d)

- **作者**: Xinyuan Tong
- **时间**: 2026-09-08T17:51:33Z
- **提交信息**: Point Ling-3.0-flash-VL cookbook install section at the model image (#38539)

### [30e7a30](https://github.com/sgl-project/sglang/commit/30e7a3072d3f1e9bd70cd5e44146ca27c80522c4)

- **作者**: Brayden Zhong
- **时间**: 2026-09-08T15:56:40Z
- **提交信息**: Keep fp32 routing weights in the fp8 block-scale and bf16 trtllm MoE (#33631)

Co-authored-by: Brayden Zhong <brayden@radixark.ai>

### [8a0863c](https://github.com/sgl-project/sglang/commit/8a0863c72840ce1ff4fd2e5e2e7b8dd20782c8d8)

- **作者**: HZY
- **时间**: 2026-09-08T15:40:21Z
- **提交信息**: [HiCache] Add MLA host-dedup primitives (#36800)


Co-authored-by: Zhangheng <hzh0425@apache.org>

### [482e9f2](https://github.com/sgl-project/sglang/commit/482e9f257bb9d9ac57c2245c93768a96ec70edbe)

- **作者**: Xinyuan Tong
- **时间**: 2026-09-08T15:00:24Z
- **提交信息**: Add Ling-3.0-flash-VL cookbook (#38434)

### [325ab24](https://github.com/sgl-project/sglang/commit/325ab245a182d07c62c51cc655e7b2dc2f0a31d6)

- **作者**: Thanhhao
- **时间**: 2026-09-08T14:55:36Z
- **提交信息**: [DCP] Allow fi_a2a on single-node systems Blackwell without MNNVL fabric ( ex B200 B300) (#37767)

Co-authored-by: Hao Phan <htphan@nvidia.com>
Co-authored-by: Khoa Pham <khoa.pham@radixark.ai>

### [beecfda](https://github.com/sgl-project/sglang/commit/beecfda314c39e6bd0ff2d5fe194d1deef686eaf)

- **作者**: Liu Ziming
- **时间**: 2026-09-08T14:50:55Z
- **提交信息**: [observability] Fix missing e2e/decode/inference latency span attributes (#37789)

### [15ff470](https://github.com/sgl-project/sglang/commit/15ff470472d32cbdbefd872f0e185f0c668c6b0e)

- **作者**: Mick
- **时间**: 2026-09-08T14:37:21Z
- **提交信息**: [diffusion] chore: key the VAE decode-dtype store by module layout (#38496)

Co-authored-by: Mick Qian <mickqian@radixark.ai>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [a6b5428](https://github.com/sgl-project/sglang/commit/a6b542813ff46de8ba3856e0236f1af35f4fca54)

- **作者**: HZY
- **时间**: 2026-09-08T14:14:33Z
- **提交信息**: fix(glm-5.2-nvfp4): bound Mooncake synchronous transfer batches (#32758)

### [4df5df9](https://github.com/sgl-project/sglang/commit/4df5df911ba9f1d1ffdeb1516e106f2df691fbdf)

- **作者**: SovietPower
- **时间**: 2026-09-08T14:14:03Z
- **提交信息**: [Scheduler] Add HRRN schedule policy to significantly reduce TTFT (#32911)

Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

### [5097f9a](https://github.com/sgl-project/sglang/commit/5097f9ac95b0916b7070e3d2c98225badbd964fb)

- **作者**: Po-Han Huang (NVIDIA)
- **时间**: 2026-09-08T13:16:36Z
- **提交信息**: Disable Hopper GLM shared-expert fusion for modelopt_fp4 Marlin (#37325)

### [2d339dd](https://github.com/sgl-project/sglang/commit/2d339ddef1a4e16480307f9e50d9dd56dc030af6)

- **作者**: pllimax
- **时间**: 2026-09-08T13:14:48Z
- **提交信息**: [NPU] Phase A calibration: full GSM8K eval for dp_attention mixed-chunk (#38422)

### [554f817](https://github.com/sgl-project/sglang/commit/554f817948c26e8e9c8338b4a33e94a609d6f0fb)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-09-08T11:05:02Z
- **提交信息**: [Diffusion] Optimize LTX-2 QKNorm and split RoPE on Hopper (#38396)

### [88a9bfd](https://github.com/sgl-project/sglang/commit/88a9bfd1ffdec1d13ebe86c7de53c93fd19d351d)

- **作者**: Mick
- **时间**: 2026-09-08T10:40:17Z
- **提交信息**: [diffusion] CI: add per-case timing tolerance for host-I/O-bound perf guards (#38457)

Co-authored-by: Mick Qian <mickqian@radixark.ai>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [e634ba7](https://github.com/sgl-project/sglang/commit/e634ba78a43b569226a8831ef1cfb719aab9aef8)

- **作者**: zijiec
- **时间**: 2026-09-08T10:10:09Z
- **提交信息**: [AMD] gfx950 assembly attention for EAGLE verify, draft extend and decode  (#37465)

Co-authored-by: Zijie Chen <300606707+zijiecode@users.noreply.github.com>

### [141febf](https://github.com/sgl-project/sglang/commit/141febf329125393d868094d13e46d254fe64247)

- **作者**: amd-danli103
- **时间**: 2026-09-08T10:01:53Z
- **提交信息**: [AMD] fix: use the hardware fp8 e4m3 convert on gfx950 (#37140)

Signed-off-by: amd-danli103 <danli103@amd.com>

### [775f17b](https://github.com/sgl-project/sglang/commit/775f17b07cdfed9c467d98d2f860cf4c90f847b8)

- **作者**: Mick
- **时间**: 2026-09-08T09:52:52Z
- **提交信息**: [diffusion] optimization: stream mapped weights on a shared host/device pool (#38441)

Co-authored-by: Mick Qian <mickqian@radixark.ai>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [7edcdd5](https://github.com/sgl-project/sglang/commit/7edcdd5ae618bf0386c95b43a69d741ff825acb9)

- **作者**: vorapolsiloai
- **时间**: 2026-09-08T09:49:47Z
- **提交信息**: [AMD] Skip AITER FP8 ASM prefill when GQA is unsupported (#38467)

### [ccfa120](https://github.com/sgl-project/sglang/commit/ccfa120daecabab4b9b4d7e89ec82f41e071a7e9)

- **作者**: Hank Han
- **时间**: 2026-09-08T08:50:07Z
- **提交信息**: Fix DSA compression tail capacity for PD decode request slots (#38417)

### [5ae4ccb](https://github.com/sgl-project/sglang/commit/5ae4ccb0fd97d2a903c07e52dea7949f429d1f42)

- **作者**: DavidLi
- **时间**: 2026-09-08T08:38:01Z
- **提交信息**: [Bench] Amortize the GDN ReplaySSM decode latency over the flush cycle (#38399)

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [4c3d47f](https://github.com/sgl-project/sglang/commit/4c3d47f1df9dee2d77794f6fc5ef11c64817e4fc)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-09-08T08:19:28Z
- **提交信息**: [AMD] Copy MoE weight views before H2D in slow-loading nightlies (#38456)

Co-authored-by: Chen <bingxche@amd.com>

### [f8f0391](https://github.com/sgl-project/sglang/commit/f8f03910f20329cb4f920ec8685eaa9f7eda81fc)

- **作者**: cen121212
- **时间**: 2026-09-08T07:45:36Z
- **提交信息**: 【NPU】Support EAGLE when PP enabled in prefill nodes (#32207)

### [b83a598](https://github.com/sgl-project/sglang/commit/b83a59835dcaabd0e606194df62a8b8601710cf9)

- **作者**: Rain Jiang
- **时间**: 2026-09-08T07:41:31Z
- **提交信息**: sglang-server remove opaque type (#38095)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-09-09
**监控日期**: 2026-09-08
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1274
- **最后更新**: 2026-09-08T05:41:43Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-09-09
**监控日期**: 2026-09-08
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 91273
- **最后更新**: 2026-09-09T00:03:47Z

## 提交统计

- **昨日提交总数**: 44
- **提交者数量**: 32
- **主要提交者**: Jing Wang, Stefano Castagnetta, Sun

## AI分析总结

# vLLM 昨日提交分析总结

## 一、主要更新类型

本次共44个提交，以**Bug修复**（约15个）和**性能优化**（约10个）为主，辅以**CI改进**（约7个）、**功能增强**（约5个）、**重构与清理**（约3个）及**依赖升级**（约2个）。

## 二、关键变更点与项目方向

1. **Speculative Decode（推测解码）系列修复**：多个提交修复DCP配置保留、Mamba状态缓存、EAGLE恢复位置等问题，体现vLLM对投机解码这一关键加速路径的持续打磨。
2. **NVFP4量化与KV Cache优化**：多项提交涉及NVFP4内核选择、scale分配方向修复及FMHA加速，反映项目对下一代低精度推理的投入。
3. **Kimi模型专项修复**：多个提交针对Kimi K3的CUDA graph、Triton错误、权重流加载等问题，显示对特定大模型生态的深度适配。
4. **ROCm/AMD平台支持增强**：多项提交涉及AMD MI300测试超时、Quark量化、AITER内核优化，体现多硬件平台战略。
5. **KV Connector与KV Offload**：支持per-region传输几何、修复SWA覆盖边界问题，推进跨节点KV缓存分发能力。
6. **Transformers后端改进**：合并列线性融合泛化、注意力sink应用，增强与HuggingFace生态的兼容性。

## 三、项目影响与潜在意义

- **稳定性提升**：大量针对特定模型（Kimi、Qwen3.8）和硬件（B200、MI300）的修复，显著增强生产环境可靠性。
- **性能优化**：消除推理扫描、融合内核、启用新硬件内核等优化，直接降低延迟、提升吞吐。
- **多硬件战略深化**：ROCm相关提交占比约15%，表明AMD平台已成为与NVIDIA并重的一等公民。
- **CI体系完善**：多项CI改进（超时调整、测试拆分、GPU状态清理）保障了项目在快速迭代下的质量门槛。

## 四、值得关注的技术点

1. **SWA层主块大小调整**（#53007）：避免KV块LCM膨胀，是内存效率的重要优化。
2. **GPTQ Group/Dynamic Activation Ordering移除**（#54809）：简化量化路径，可能影响兼容性策略。
3. **W4A4线性内核优先于weight-only**（#55170）：在SM120/121上追求更高计算密度。
4. **openai库升级至≥2.25.0**：支持namespace tools类型，扩展OpenAI兼容API能力。
5. **torch.compile支持Sarvam MLA**（#55817）：探索编译优化在新架构上的应用。

## 五、对项目发展的影响

vLLM正沿着“**性能极致优化 + 多硬件适配 + 生态兼容**”三条主线快速演进。本批提交显示：推理加速方面从通用优化转向模型/硬件特定调优；平台支持从NVIDIA独占走向AMD深度适配；同时通过大量Bugfix保障了复杂功能（投机解码、KV offload、量化）在生产环境的可用性。这些工作巩固了vLLM作为“Easy, fast, and cheap LLM serving”首选框架的定位，为支撑更大规模、更多样化的LLM服务场景奠定基础。

## 详细提交记录

### [c268198](https://github.com/vllm-project/vllm/commit/c268198715de0e78a56672c7e9d0b2fd9afdb141)

- **作者**: Jing Wang
- **时间**: 2026-09-08T23:59:10Z
- **提交信息**: [Bugfix][Spec Decode] Preserve target parallel config (DCP) for DSpark (#55472)

Signed-off-by: Jing Wang <jingwang96@qq.com>

### [5af4cc3](https://github.com/vllm-project/vllm/commit/5af4cc33ec0837ded8a18b368ec58a9fd4e4d5cd)

- **作者**: Taneem Ibrahim
- **时间**: 2026-09-08T23:53:59Z
- **提交信息**: [Bugfix] Fix OpenPangu multimodal embedding merge (#55941)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [9c2d210](https://github.com/vllm-project/vllm/commit/9c2d21046bb39f56ee93a5fab4f899714a5579ef)

- **作者**: Stefano Castagnetta
- **时间**: 2026-09-08T23:50:07Z
- **提交信息**: [Bugfix][Spec Decode] Honour the draft's moe_backend on Model Runner V2 (#54788)

Signed-off-by: Stefano Castagnetta <scastagnetta@nvidia.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [c0d8d54](https://github.com/vllm-project/vllm/commit/c0d8d5413e233466e09d4f2d80867204d72acb60)

- **作者**: Jim Ban
- **时间**: 2026-09-08T23:49:37Z
- **提交信息**: [Transformers] Generalize merged-column linear fusion (#55301)

Signed-off-by: BANANASJIM <bananasjim1@gmail.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [60ad959](https://github.com/vllm-project/vllm/commit/60ad959b6f1a5c8f602edbd608c8decbc0788c50)

- **作者**: sychen52
- **时间**: 2026-09-08T22:47:21Z
- **提交信息**: Fix block FP8 MTP in ModelOpt mixed checkpoints (#55513)

Signed-off-by: Shiyang Chen <shiychen@nvidia.com>
Signed-off-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>

### [28a2cce](https://github.com/vllm-project/vllm/commit/28a2ccee78699e90ad06c7e833dc018dea8fddbf)

- **作者**: Chaitanya Sri Krishna Lolla
- **时间**: 2026-09-08T22:06:36Z
- **提交信息**: [ROCm][DI][CI] Enable WideEP Intranode tests  (#53195)

Signed-off-by: lcskrishna <lollachaitanya@gmail.com>

### [05e52f6](https://github.com/vllm-project/vllm/commit/05e52f633655e1b336f7b1f3b9e3d6181de3b7bd)

- **作者**: Kevin H. Luu
- **时间**: 2026-09-08T21:27:13Z
- **提交信息**: [CI] Fix ARM64 test dependency builds with GCC 15 (#55877)

Signed-off-by: khluu <khluu000@gmail.com>

### [bf33961](https://github.com/vllm-project/vllm/commit/bf339618d1e292e61e274a1b5daa2b7a5a8d2bac)

- **作者**: cjackal
- **时间**: 2026-09-08T21:11:12Z
- **提交信息**: [Misc] Bump `openai` to `>=2.25.0` to support namespace tools types (#49104)

Signed-off-by: cjackal <44624812+cjackal@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Flora Feng <4florafeng@gmail.com>

### [bfb443a](https://github.com/vllm-project/vllm/commit/bfb443a6b6f670e68e211112a141d089f1cf956f)

- **作者**: Wentao Ye
- **时间**: 2026-09-08T21:07:54Z
- **提交信息**: [Kimi Bug] Fix kda ima `Triton Error [CUDA]: an illegal memory access was encountered` (#55924)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [0a742da](https://github.com/vllm-project/vllm/commit/0a742da274cc0a082cefe5951f9887e5ec77beea)

- **作者**: Flora Feng
- **时间**: 2026-09-08T21:07:22Z
- **提交信息**: [Perf] Eliminate full-history reasoning scans for structured outputs (#55223)

Signed-off-by: sfeng33 <4florafeng@gmail.com>
Signed-off-by: Flora Feng <4florafeng@gmail.com>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>

### [29f46ac](https://github.com/vllm-project/vllm/commit/29f46ac475322cfc14ced890825b9a149ada3608)

- **作者**: Flora Feng
- **时间**: 2026-09-08T21:07:16Z
- **提交信息**: [Perf] Eliminate full-history reasoning scans for structured outputs (#55223)

Signed-off-by: sfeng33 <4florafeng@gmail.com>
Signed-off-by: Flora Feng <4florafeng@gmail.com>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>

### [73f61d1](https://github.com/vllm-project/vllm/commit/73f61d12aa5cfa55092bb45b582475b4e2ba20ff)

- **作者**: djramic
- **时间**: 2026-09-08T21:06:05Z
- **提交信息**: [CI][ROCm] Increase timeouts for AMD MI300 jobs (#55919)

Signed-off-by: Djordje Ramic <djoramic@amd.com>
Co-authored-by: Kevin H. Luu <khluu000@gmail.com>

### [db3814a](https://github.com/vllm-project/vllm/commit/db3814a4f215e666098ffb74a5c21bf46c60bae9)

- **作者**: Andreas Karatzas
- **时间**: 2026-09-08T21:04:27Z
- **提交信息**: [Attention] Require explicit DCP support from attention implementations (#55780)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [cb22234](https://github.com/vllm-project/vllm/commit/cb222346875b1cec3152b9c882781115accc57e5)

- **作者**: Andreas Karatzas
- **时间**: 2026-09-08T21:03:54Z
- **提交信息**: [CI] Reuse ColQwen3 models across pooling tests (#55889)

Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>

### [d29c88f](https://github.com/vllm-project/vllm/commit/d29c88f162a3ec17ddb0afdf5f4f3b3ca6b84d59)

- **作者**: bnellnm
- **时间**: 2026-09-08T20:44:43Z
- **提交信息**: [Core] Let SWA layers take the primary block size to avoid inflating the KV block LCM (#53007)

Signed-off-by: Bill Nell <bnell@redhat.com>
Signed-off-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [808353f](https://github.com/vllm-project/vllm/commit/808353f477c21953a3a476b562775385e89da8e9)

- **作者**: Kevin H. Luu
- **时间**: 2026-09-08T20:44:14Z
- **提交信息**: [CI] Split long misc test groups by command (#52346)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Kimi Code <noreply@moonshot.cn>
Co-authored-by: Codex <noreply@openai.com>

### [18615ad](https://github.com/vllm-project/vllm/commit/18615ad1ee11ae54a996a0c49dd6860630b3bca0)

- **作者**: Andreas Karatzas
- **时间**: 2026-09-08T20:20:05Z
- **提交信息**: [Bugfix] Handle null RoPE parameters for NoPE layers (#55949)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [e0aaef8](https://github.com/vllm-project/vllm/commit/e0aaef85f3de7a2376aee3708a3cba96286b41b1)

- **作者**: Matthew Bonanni
- **时间**: 2026-09-08T20:01:12Z
- **提交信息**: [2/N][KV Connector][NIXL] Support per-region transfer geometry (#53780)

Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [2c9d68f](https://github.com/vllm-project/vllm/commit/2c9d68f80bd20af7af1bc539c044a4aebbe52f8e)

- **作者**: Roderick Wu
- **时间**: 2026-09-08T19:45:12Z
- **提交信息**: [Quant][Kernel] Remove GPTQ Group/Dynamic Activation Ordering (#54809)

Signed-off-by: Roderick-Wu <roderickwu2003@gmail.com>
Signed-off-by: Roderick Wu <roderickwu2003@gmail.com>
Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: mgoin <mgoin64@gmail.com>

### [1a522b6](https://github.com/vllm-project/vllm/commit/1a522b69491f1d4f9199769bf44137e0f1de0912)

- **作者**: shikamd123
- **时间**: 2026-09-08T19:21:18Z
- **提交信息**: [ROCm] [Docker] Upgrade default AINIC repo to ship libionic 54.0-187-1 (#54112)

Signed-off-by: Shiksha Patel <shiksha.patel@amd.com>

### [1b2c591](https://github.com/vllm-project/vllm/commit/1b2c591cd0c3bb5a85ac7f3d6cbaa2fa7df6bc7d)

- **作者**: sychen52
- **时间**: 2026-09-08T17:25:42Z
- **提交信息**: [Bugfix] speedup nvfp4 kv for FMHA (#55031)

Signed-off-by: Shiyang Chen <shiychen@nvidia.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>

### [bcca76e](https://github.com/vllm-project/vllm/commit/bcca76e7dbca608979deea55f589c7316393bc52)

- **作者**: Raya Elena Solano
- **时间**: 2026-09-08T17:13:39Z
- **提交信息**: [Test] Dequantize NVFP4 KV cache scales in the layout the kernel writes (#55908)

Signed-off-by: Raya Elena Solano <raya.solano@mbinf.de>
Co-authored-by: mgoin <mgoin64@gmail.com>

### [8ebc5b0](https://github.com/vllm-project/vllm/commit/8ebc5b0a182b3351a1c62fe73e97be2c489ed2a6)

- **作者**: Jiangyun Zhu
- **时间**: 2026-09-08T15:26:07Z
- **提交信息**: [Bugfix] Fix NVFP4 fused SiLU+mul scale allocation and global scale direction (#55643)

Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: khluu <khluu000@gmail.com>
Co-authored-by: jiahao <jxia77@terpmail.umd.edu>
Co-authored-by: Kimi Code <noreply@moonshot.cn>

### [6b15bea](https://github.com/vllm-project/vllm/commit/6b15bea080ac64c9e123982b48cbbffe34957ec0)

- **作者**: Wentao Ye
- **时间**: 2026-09-08T15:22:09Z
- **提交信息**: [Refactor] Remove utils dead code (#53941)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [7c2f1ff](https://github.com/vllm-project/vllm/commit/7c2f1ff4958eaf0818405e9192c71608fe4a16b1)

- **作者**: Qiu Chunshuo
- **时间**: 2026-09-08T15:18:01Z
- **提交信息**: [Core] Scope PCP-DP validation to GPU manager (#54523)

Signed-off-by: QiuChunshuo <qiuchunshuo@huawei.com>

### [8e1f97e](https://github.com/vllm-project/vllm/commit/8e1f97e70984192cc63c51a8af3e313cab8c5c73)

- **作者**: Canlin Guo
- **时间**: 2026-09-08T14:45:18Z
- **提交信息**: [Qwen3.8-Flash-Next] Tune FP8 TP2/TP4 Triton MoE on B200 (#55890)

Signed-off-by: Canlin <canlinguosdu@gmail.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [b105d82](https://github.com/vllm-project/vllm/commit/b105d8284f076be2e0e13629eed8825b791a4b14)

- **作者**: linitra24
- **时间**: 2026-09-08T14:30:15Z
- **提交信息**: [LoRA] Clarify target module matching logic (#55865)

Signed-off-by: linitra24 <renshuang.zhou@daocloud.io>

### [07950d4](https://github.com/vllm-project/vllm/commit/07950d47347f7fff41f98616096fd10349171e3d)

- **作者**: Wentao Ye
- **时间**: 2026-09-08T14:29:53Z
- **提交信息**: [Kimi Bug] Fix kimi k3 startup cuda graph issue with recoverSSM (#55774)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [6ddbab0](https://github.com/vllm-project/vllm/commit/6ddbab03defe20d536a8c9e6cb9d74d67aa62416)

- **作者**: Roberto L. Castro
- **时间**: 2026-09-08T14:25:48Z
- **提交信息**: [4/N][warmup][DSv4] Migrate common attention kernels (#50176)

Signed-off-by: LopezCastroRoberto <rocastro@redhat.com>
Co-authored-by: Codex <codex@openai.com>

### [f998862](https://github.com/vllm-project/vllm/commit/f998862d46e7af54467e10156f02cc51a67e268b)

- **作者**: Sherif Waly
- **时间**: 2026-09-08T14:08:51Z
- **提交信息**: [Bugfix] Fix Kimi K3 loading with interleaved weight streams (#53379)

Signed-off-by: Sherif Waly <sherif.waly@mistral.ai>
Co-authored-by: Nicolò Lucchesi <nicolo.lucchesi@mistral.ai>

### [613ab20](https://github.com/vllm-project/vllm/commit/613ab20f7f9082244240f4e9b2e7a4ee6769c38f)

- **作者**: Mohit Singla
- **时间**: 2026-09-08T14:01:30Z
- **提交信息**: [Model] Enable torch.compile for Sarvam MLA (#55817)

Signed-off-by: mohit-sarvam <mohit@sarvam.ai>
Co-authored-by: Codex <noreply@openai.com>

### [263c4ff](https://github.com/vllm-project/vllm/commit/263c4ff95fadb62d80f315171b17d4f623494e56)

- **作者**: akshaver
- **时间**: 2026-09-08T13:59:58Z
- **提交信息**: [Bugfix][Spec Decode] Cache the Mamba state at the block-grid position of EAGLE resume (#53945)

Signed-off-by: wzhao18 <wzhao18.sz@gmail.com>
Signed-off-by: Adam Shaver <ashaver@nvidia.com>
Signed-off-by: akshaver <168006157+akshaver@users.noreply.github.com>
Co-authored-by: wzhao18 <wzhao18.sz@gmail.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: roikoren755 <26850796+roikoren755@users.noreply.github.com>

### [414057a](https://github.com/vllm-project/vllm/commit/414057a3d3aa47915b10103e4a181604e0b3562f)

- **作者**: Thomas Parnell
- **时间**: 2026-09-08T13:54:07Z
- **提交信息**: [Bugfix] Apply attention sinks in the Transformers backend (#52156)

Signed-off-by: Thomas Parnell <tpa@zurich.ibm.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [472d8c9](https://github.com/vllm-project/vllm/commit/472d8c912566b539182c7154f582eaf1ba84bab1)

- **作者**: Sun
- **时间**: 2026-09-08T13:22:04Z
- **提交信息**: [Perf] Fuse DeepEncoder relative bias in Triton attention (#55629)

Signed-off-by: levius <2114377220@qq.com>
Signed-off-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: Codex <codex@openai.com>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>

### [5ebce23](https://github.com/vllm-project/vllm/commit/5ebce2391e772994a92f903bdb97b4631a05e851)

- **作者**: Andy Lo
- **时间**: 2026-09-08T13:14:19Z
- **提交信息**: [Bugfix][KV Offload] Respect prefix-cache bypass in SimpleCPUOffload (#54998)

Signed-off-by: Andy Lo <andy@mistral.ai>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [f6326f5](https://github.com/vllm-project/vllm/commit/f6326f53bda46898a331c2d24500332c285d9a2b)

- **作者**: Stefano Castagnetta
- **时间**: 2026-09-08T12:26:03Z
- **提交信息**: [Perf][GDN] Enable the FlashInfer GDN prefill kernel on SM12x (#55715)

Signed-off-by: Stefano Castagnetta <scastagnetta@nvidia.com>

### [2504760](https://github.com/vllm-project/vllm/commit/25047604fe5518ecb99929edc3fe2f5e76bc9f4a)

- **作者**: Shanshan Shen
- **时间**: 2026-09-08T11:58:26Z
- **提交信息**: [ROCm][Perf] Remove AITER paged-MQA outputs guard for DeepSeek-V4 (#55808)

Signed-off-by: Shanshan Shen <87969357+shen-shanshan@users.noreply.github.com>

### [34b9899](https://github.com/vllm-project/vllm/commit/34b9899c8f1361964fded8d331550828c9258909)

- **作者**: Kevin H. Luu
- **时间**: 2026-09-08T11:39:01Z
- **提交信息**: [CI] Increase ColQwen3 pooling test memory budget on H200 MIG (#55878)

Signed-off-by: khluu <khluu000@gmail.com>

### [13cf9e0](https://github.com/vllm-project/vllm/commit/13cf9e05c1eda0bfe5cbfb9344343ca2737d0723)

- **作者**: Stefano Castagnetta
- **时间**: 2026-09-08T11:06:45Z
- **提交信息**: [Perf][Quant][NVFP4] Prefer W4A4 linear kernels over weight-only ones on SM120/121 (#55170)

Signed-off-by: Stefano Castagnetta <scastagnetta@nvidia.com>

### [e41a17e](https://github.com/vllm-project/vllm/commit/e41a17e606c9a8ffa639ebde5bce885667ff27ea)

- **作者**: jimmy-adams
- **时间**: 2026-09-08T10:30:26Z
- **提交信息**: [ROCm][Quantization] Support AMD Quark per-block FP8 for fused MoE layers (#52263)

Signed-off-by: huji <huidong.ji@amd.com>
Signed-off-by: jimmy-adams <41593649+jimmy-adams@users.noreply.github.com>

### [5db6522](https://github.com/vllm-project/vllm/commit/5db652225f00b55783823ae6606d36925e3e3efe)

- **作者**: Kevin H. Luu
- **时间**: 2026-09-08T08:30:06Z
- **提交信息**: [Bugfix] Validate extension integers before engine serialization (#55606)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Codex <noreply@openai.com>

### [96eccb8](https://github.com/vllm-project/vllm/commit/96eccb8f49aff58aa2a11b431bf8331f4b368606)

- **作者**: Kevin H. Luu
- **时间**: 2026-09-08T08:15:21Z
- **提交信息**: [CI] Restore clean GPU state before OAI Triton MoE tests (#55453)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Codex <noreply@openai.com>

### [ce6c241](https://github.com/vllm-project/vllm/commit/ce6c241ddcc722ee7f26fb4db132461150dad18e)

- **作者**: Taoyu Zhu
- **时间**: 2026-09-08T07:21:49Z
- **提交信息**: [ROCm][Perf][M3] Fused allreduce+GemmaRMSNorm fast path (#54787)

Signed-off-by: Taoyu Zhu <zhutaoyu97@gmail.com>
Co-authored-by: Shanshan Shen <467638484@qq.com>

### [81dabe2](https://github.com/vllm-project/vllm/commit/81dabe2e5d613d107577c9b4238fc8d718b92887)

- **作者**: ahmed xijiaat
- **时间**: 2026-09-08T07:15:48Z
- **提交信息**: [Bugfix][KV Offload] Validate SWA coverage at unaligned cache-hit boundaries (#55712)

Signed-off-by: xijiade.aihemaiti <3146335281@qq.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-09-09
**监控日期**: 2026-09-08
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 6722
- **最后更新**: 2026-09-08T22:57:14Z

## 提交统计

- **昨日提交总数**: 16
- **提交者数量**: 13
- **主要提交者**: liangmenghuang, Harry Mellor, Alicia

## AI分析总结

## 分析总结

### 1. 主要更新类型

本次提交以**Bug修复**为主（约10项），辅以**功能新增**（2项）、**CI/测试优化**（2项）、**性能优化**（1项）和**前端能力增强**（1项），整体呈现“稳定优先、渐进增强”的节奏。

### 2. 关键变更点与项目方向的关系

- **多模态模型支持深化**：为GR00T-N1.7修复了流匹配噪声的per-request seed问题，并使其图像处理管线（albumentations、crop_fraction等）与Isaac-GR00T对齐，体现对具身智能/机器人基础模型的重视。新增JoyAI-VL-Interaction的原生多阶段pipeline，扩展了交互式视觉语言模型的支持面。
- **全模态服务能力增强**：新增**服务端VAD（语音活动检测）**，为turn-based全模态模型提供对话轮次管理能力，直接呼应项目“omni-modality”定位，是向实时语音交互场景迈进的关键一步。
- **工程健壮性加固**：修复forced-aligner提示词构建（词级时间戳偏移）、HWR存储扫描、LLM阶段additional_config保留等问题，提升多模态流水线的可靠性和一致性。
- **CI与基准测试优化**：包括ROCm平台LTX2测试路由、视频基准超时处理、omni基准默认15分钟超时限制等，反映项目在多硬件平台（NPU/ROCm）上的适配投入。

### 3. 对项目的影响和潜在意义

- 修复GR00T-N1.7的seed一致性和图像预处理对齐问题，对**可复现的生成结果**至关重要，直接影响科研和工业用户对模型的信任度。
- 服务端VAD的引入使vLLM-Omni从“模型推理引擎”向“完整对话服务”演进，为语音助手、实时交互应用铺路，是差异化竞争的重要筹码。
- 多项Bugfix（如additional_config保留、disable-log-stats处理）降低了多阶段pipeline配置丢失的风险，提升了复杂部署场景的稳定性。
- 向Hugging Face Hub请求中附加库信息，有助于**生态数据收集和用户行为分析**，为项目优化提供数据支撑。

### 4. 值得关注的技术点

- **GR00T-N1.7的seed处理**：在flow-matching噪声生成中正确传递per-request seed，涉及分布式推理下的随机状态管理，技术难度较高。
- **Boogu-Image跳过密集注意力掩码**：属于性能优化，通过避免不必要的mask计算提升图像模型推理效率。
- **服务端VAD实现**：涉及音频流处理与模型调度状态的协同，是前端架构的重要扩展。
- **MiniMax H3调制网格大小限制**：针对NPU平台的特定约束进行适配，体现硬件相关的精细化调优。

### 5. 对项目发展的综合影响

vLLM-Omni致力于“人人可用的全模态模型服务”，本次提交在**广度**（新增模型类型、VAD能力）和**深度**（多硬件适配、细粒度Bugfix）上均有推进。大量Bugfix集中在多阶段pipeline、基准测试和配置传递等“基础设施”层面，说明项目正从“能跑”向“跑得稳、跑得准”过渡。对GR00T等具身模型的持续投入，以及对NPU/ROCm等非NVIDIA平台的支持，表明项目瞄准**多元化硬件生态**和**前沿具身智能**两大战略方向。整体来看，这些提交巩固了项目的工程基础，同时为下一阶段的实时交互和更广泛模型支持做好了铺垫。

## 详细提交记录

### [b3dd458](https://github.com/vllm-project/vllm-omni/commit/b3dd45874a750f7edfa39bb02262804228e5ff7b)

- **作者**: Tianyao Wu
- **时间**: 2026-09-08T19:27:38Z
- **提交信息**: [Bugfix] Build the forced-aligner prompt without a chat template (word timestamps one bin late) (#7240)

Signed-off-by: Tianyao Wu <rayroy31@gmail.com>

### [5e4baea](https://github.com/vllm-project/vllm-omni/commit/5e4baea64d0f4cd1b6ce147e4f7a28f0f41d995f)

- **作者**: Lei Ke
- **时间**: 2026-09-08T16:08:46Z
- **提交信息**: [Bugfix][NPU] Limit MiniMax H3 modulation grid size (#6794)

Signed-off-by: KrystalRay <keeleiray@gmail.com>
Co-authored-by: KrystalRay <keeleiray@gmail.com>

### [fdaf4e3](https://github.com/vllm-project/vllm-omni/commit/fdaf4e31bd6638ddb472f93764aabc034c20bb6d)

- **作者**: Harry Mellor
- **时间**: 2026-09-08T16:08:38Z
- **提交信息**: Add vLLM-Omni library info to Hugging Face Hub requests (#5381)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [7a80b79](https://github.com/vllm-project/vllm-omni/commit/7a80b796986b15840bc30ef134f0d7158dce82ea)

- **作者**: liangmenghuang
- **时间**: 2026-09-08T15:53:20Z
- **提交信息**: [Bugfix][Model] GR00T-N1.7: honor the per-request seed for flow-matching noise (#7253)

Signed-off-by: liangmengh <liangmengh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [de1b070](https://github.com/vllm-project/vllm-omni/commit/de1b0708bdb912397ffa016bbbca4ccd42f48592)

- **作者**: andyluo7
- **时间**: 2026-09-08T14:59:37Z
- **提交信息**: [CI][ROCm] Route LTX2 Ulysses parity to two-GPU lane (#7234)

Signed-off-by: andyluo7 <andy.luo@amd.com>

### [7422a85](https://github.com/vllm-project/vllm-omni/commit/7422a85cc7a156a9131938ebe3afb6c8025c2a40)

- **作者**: Hongsheng Liu
- **时间**: 2026-09-08T14:54:49Z
- **提交信息**: [Bugfix] Skip HWR store-size scans when no limit is configured (#7131)

Signed-off-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [a316900](https://github.com/vllm-project/vllm-omni/commit/a31690041de9a19acfec8239c4bbb64bc3e051d4)

- **作者**: Yancy
- **时间**: 2026-09-08T13:56:27Z
- **提交信息**: [Bugfix][Examples] Use --profiler-config flag in offline TTS examples (#6763)

Signed-off-by: Asthenia <asthenia0412@gmail.com>
Co-authored-by: Asthenia <asthenia0412@gmail.com>

### [d59d166](https://github.com/vllm-project/vllm-omni/commit/d59d1664858956976a12797a8613bd4b1d803097)

- **作者**: Honghan Zhu
- **时间**: 2026-09-08T12:44:49Z
- **提交信息**: [Bugfix] Preserve additional_config for LLM stages (#7272)

Signed-off-by: zhuhh97 <zhuhonghan@huawei.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [5378b77](https://github.com/vllm-project/vllm-omni/commit/5378b77be4213887281613adc422887bfdcfae69)

- **作者**: Shuolei Wang
- **时间**: 2026-09-08T12:07:08Z
- **提交信息**: [Model][JoyAI-VL-Interaction] Add native multi-stage pipeline (#5352)

Signed-off-by: Shuolei Wang <shuoleiwang123@gmail.com>

### [d774033](https://github.com/vllm-project/vllm-omni/commit/d7740336ff94d23276d690e3cd74a1ddb25d23cb)

- **作者**: liangmenghuang
- **时间**: 2026-09-08T10:59:01Z
- **提交信息**: [Bugfix][Model] GR00T-N1.7: honor processor_config image pipeline (use_albumentations / crop_fraction / letter_box_transform) to match Isaac-GR00T (#7083)

Signed-off-by: liangmengh <liangmengh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [c9c25b3](https://github.com/vllm-project/vllm-omni/commit/c9c25b33c3210ba275917db32e0e5403d69051a5)

- **作者**: LHXuuu
- **时间**: 2026-09-08T10:17:00Z
- **提交信息**: [Frontend] Add server-side VAD for turn-based omni models (#6618)

Signed-off-by: LHXuuu <xulianhao.xlh@antgroup.com>

### [031612f](https://github.com/vllm-project/vllm-omni/commit/031612f2507594ef632f923379e04ee36ff98684)

- **作者**: Alicia
- **时间**: 2026-09-08T09:40:08Z
- **提交信息**: [Bugfix] Fix video benchmark timeout and failure accounting (#7259)

Signed-off-by: Alicia <115451386+congw729@users.noreply.github.com>

### [b58ff5c](https://github.com/vllm-project/vllm-omni/commit/b58ff5cb8b17250b76f9cdf9b9b46385cdda4376)

- **作者**: andyluo7
- **时间**: 2026-09-08T09:10:51Z
- **提交信息**: [CI/Build] Wait for duplex reaper recovery in retry test (#7225)

Signed-off-by: andyluo7 <andy.luo@amd.com>
Co-authored-by: wangyu <53896905+yenuo26@users.noreply.github.com>

### [7c2e30a](https://github.com/vllm-project/vllm-omni/commit/7c2e30afd3e8d5c66c8fd867f694550da45f6193)

- **作者**: tlysanhuo
- **时间**: 2026-09-08T09:00:25Z
- **提交信息**: [Bugfix] Bound omni benchmark per-request timeout to 15 min by default (#7130)

Signed-off-by: tly <2200895168@qq.com>

### [f3fabe4](https://github.com/vllm-project/vllm-omni/commit/f3fabe4145df06947bc853a808928caa037f5e8f)

- **作者**: Chenguang Zheng
- **时间**: 2026-09-08T08:19:07Z
- **提交信息**: [Bugfix] Keep --disable-log-stats out of stage config resolution (#7237)

Signed-off-by: Chenguang ZHENG <645327136@qq.com>

### [c086554](https://github.com/vllm-project/vllm-omni/commit/c086554d1fd02749bdc2bcad37636e90ade01fec)

- **作者**: Honghan Zhu
- **时间**: 2026-09-08T07:53:20Z
- **提交信息**: [Perf]Boogu-Image Skip dense attention masks (#6871)

Signed-off-by: zhuhh97 <zhuhonghan@huawei.com>

---
