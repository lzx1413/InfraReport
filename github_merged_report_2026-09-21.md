# GitHub Stars 合并报告 - 2026-09-21

**合并日期**: 2026-09-22
**监控日期**: 2026-09-21
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


**报告日期**: 2026-09-22
**监控日期**: 2026-09-21
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2215
- **最后更新**: 2026-09-21T03:06:20Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-09-22
**监控日期**: 2026-09-21
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2845
- **最后更新**: 2026-09-21T16:30:57Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Bilang ZHANG

## AI分析总结

**1. 主要更新类型**
*   **性能优化**：核心变更在于降低`ReAE`模块的内存使用。
*   **文档更新**：同步新增了相关的部署指南。

**2. 关键变更点及其与项目整体方向的关系**
*   **减少ReAE内存占用**：这是直接服务于项目“轻量级视频生成推理”核心目标的关键技术优化，旨在降低框架对硬件资源的要求。
*   **添加部署指南**：旨在降低用户的使用门槛，使框架的部署和运行更加便捷，与提升框架易用性和推广性的方向一致。

**3. 对项目的影响和潜在意义**
*   **提升框架实用性**：内存占用的降低意味着框架可以在更多显存受限的硬件设备上流畅运行，扩大了潜在用户群。
*   **增强工程化水平**：部署指南的补充使项目从“代码库”向“可用工具”迈进了一步，有助于用户快速上手和社区协作。
*   **持续优化信号**：该提交表明项目仍在活跃地进行性能深耕和工程打磨，而非仅添加新功能。

**4. 值得关注的技术点**
*   **`ReAE`模块的内存优化**：具体优化了视频生成模型中的某个关键组件（推测为“残差增强”或相关模块）的实现，可能涉及更高效的内存管理策略或算法调整，这是评估优化效果的核心。
*   **部署指南的具体内容**：指南可能涵盖了从环境配置、模型转换到具体推理服务的完整流程，对其他开发者具有参考价值。

**5. 基于项目背景对项目发展的影响**
LightX2V项目定位为**轻量级视频生成推理框架**。本次提交直接强化了这一核心定位：
*   **“轻量”特性的具体体现**：内存优化是实现“轻量”的关键技术路径之一，使框架名副其实。
*   **降低使用与部署成本**：部署指南的完善，使得这个“轻量”框架更容易被实际采用，推动了项目从研究代码向生产工具链的转化。
*   **巩固社区基础**：性能提升和文档完善能吸引更多开发者尝试和贡献，是项目长期健康发展的基石。此次提交是项目在优化核心性能与完善用户体验两个维度上的一次均衡推进。

## 详细提交记录

### [a680eba](https://github.com/ModelTC/LightX2V/commit/a680eba5f1d2ce75dbd9fba8bddf8d1aa88f6aad)

- **作者**: Bilang ZHANG
- **时间**: 2026-09-21T11:52:06Z
- **提交信息**: perf(swiftvr): reduce ReAE memory usage and add deployment guides (#1547)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-09-22
**监控日期**: 2026-09-21
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2254
- **最后更新**: 2026-09-21T05:46:50Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-09-22
**监控日期**: 2026-09-21
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6473
- **最后更新**: 2026-09-21T21:28:04Z

## 提交统计

- **昨日提交总数**: 8
- **提交者数量**: 7
- **主要提交者**: Ke Wen, Akaash Parthasarathy, Harrison Zhang

## AI分析总结

根据对 `flashinfer-ai/flashinfer` 仓库昨日8条提交记录的分析，结合其“高性能GPU推理内核”的项目目标，总结如下：

### 1. 主要更新类型
提交主要涵盖**性能优化**、**功能新增**、**Bug修复**和**代码重构**四类。其中性能优化和功能新增占比最高，体现了项目持续提升性能和扩展能力的导向。

### 2. 关键变更点与项目方向
*   **混合精度与量化支持深化**：提交 #5150 为解码核心引入了 QK-BF16/PV-FP8 的混合精度计算，与此前上下文端的 #4879 形成完整支持。这直接呼应了项目“高性能推理”的核心，通过更灵活的精度组合平衡计算效率与模型质量。
*   **硬件架构适配与代码组织**：提交 #5371 将 Blackwell (SM100) 的MegaMoE内核代码整理至专用架构目录，为未来支持新架构（如Rubin）做好准备。这体现了项目对多代GPU硬件进行系统化、模块化管理的架构演进方向。
*   **通信与并行能力扩展**：提交 #4929 新增了融合的上下文并行解码（CP）All-to-All与LSE归约内核。这是支撑大规模分布式推理的关键通信原语，表明项目正积极拓展其在分布式场景下的能力边界。
*   **API语义统一与健壮性**：提交 #4650 统一了MLA后端返回对数-求和-指数（LSE）的数学基准（base-2或base-e），消除了不同内核路径可能引发的语义歧义，提升了API的一致性和可靠性。

### 3. 对项目的影响和潜在意义
*   **性能与精度**：混合精度支持（#5150）和BF16内核的调度优化（#5363, #5370）共同提升了推理速度和内存效率，巩固了项目的高性能定位。
*   **稳定性与可靠性**：针对CUDA Graph预填充（#5176）和Blackwell GEMM边界处理（#5108）的Bug修复，消除了特定场景下的崩溃和内存访问错误，增强了生产环境部署的健壮性。
*   **架构扩展性**：通过代码重构（#5371）和新增融合通信内核（#4929），项目为支持更复杂模型结构（如MoE）和更大规模分布式推理奠定了更坚实的基础。

### 4. 值得关注的技术点
*   **内核级混合精度调度**：#5150 中实现的按操作数分离数据类型，并将其贯穿至TMA描述符、共享内存和MMA选择的全链路改造，是一项深入硬件细节的复杂工程。
*   **CUDA Graph兼容性修复**：#5176 揭示了在CUDA Graph模式下，当使用非确定性推理或特定KV缓存格式时，因网格启动过多而缺少有效块掩码导致的越界访问问题，其解决方案具有通用参考价值。
*   **高性能通信融合**：#4929 将集合通信与后续计算融合为单一内核，减少了内核启动开销和全局内存访问，是优化分布式训练/推理通信模式的典型范例。

### 5. 对项目发展的影响
这些提交共同推动FlashInfer项目向 **“全场景、高精度、高性能”的推理内核库** 发展：
*   **在精度控制上**，从支持单一类型向灵活的混合精度演进，满足不同模型和硬件的优化需求。
*   **在硬件覆盖上**，保持对主流及新兴GPU架构（如Blackwell）的快速适配，并为未来架构做好代码储备。
*   **在功能广度上**，从单卡高效计算，逐步扩展到支持多卡通信融合，以应对大模型分布式推理的挑战。
*   **在工程实践上**，通过持续的性能调优、Bug修复和API规范化，提升了作为基础库的可靠性和易用性。

总之，昨日的提交集反映了项目团队在**深化硬件优化、提升计算与通信效率、保障系统稳定性**方面的持续努力，这些更新共同强化了FlashInfer作为高性能AI推理基础设施的核心竞争力。

## 详细提交记录

### [c62cf66](https://github.com/flashinfer-ai/flashinfer/commit/c62cf664117a34ccfc746df5076efab546ea9736)

- **作者**: Harrison Zhang
- **时间**: 2026-09-21T21:27:58Z
- **提交信息**: feat(prims-ts): support QK-BF16/PV-FP8 in FMHA decode (#5150)

<!-- .github/pull_request_template.md -->

## 📌 Description

Adds QK-BF16/PV-FP8 support to the prims-ts decode kernel. V can be kept
in `float8_e4m3` while Q and K stay `bfloat16`. This is the decode
counterpart to
[#4879](https://github.com/flashinfer-ai/flashinfer/pull/4879) and
stacks on top.

Most of the change is removing the assumption that Q, K, V share one
dtype. `qkv_dtype`/`kv_dtype` are split into per-operand
`q_dtype`/`k_dtype`/`v_dtype` and threaded through the public API, TMA
descriptors, SMEM tile sizing, and MMA-kind and P-quantization
selection. Note that most of the old `use_fp8_qkv` gates were asking
whether a given operand is one byte wide, so they now ask that per
operand. For all-BF16 and all-FP8 configs, every one of those predicates
evaluates as before (see reviewer notes for correctness and perf
verification).

Mixed K/V dtypes take the split-resource path with one K ring and one V
ring shared by both instances, i.e. K and V are each staged once. To
allow this, `SmemKvTileResource` takes the instance from the calling
`load_k0`/`load_k1`. Note that this does not affect existing modes.

Changes public API for .plan() to support the new mixed QK-BF16/PV-FP8
types for KV. See below for changes.

## 🔍 Related Issues

Stacks on [#4879](https://github.com/flashinfer-ai/flashinfer/pull/4879)
(context-side QK-BF16/PV-FP8), which is merged.

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

`tests/attention/test_attention_ts_decode.py` passes. Four tests were
added for
the mixed-dtype path, which include accuracy against `trtllm-gen`, the
config
profile gate, resource construction, and that the auto-tuner is able to
select
an MMA mode.

## 📊 Performance

Tested on B200:

**No performance regression for QKV-BF16 decode.**

[qkvbf16-decode-b200.md](https://github.com/user-attachments/files/32128842/qkvbf16-decode-b200.md)

**Average of 3-32% performance gain with QK-BF16/PV-FP8 quantization
over QKV-BF16 baseline, positive across all 86 configs measured.**
Smallest gains cluster around latency-bound small-batch configs and
split-KV reduction-heavy baselines at +0.7-6%.
Largest gains cluster around large-batch/large-context, bandwidth-bound
configs at +26-32%. Moreover, max abs error against trtllm-gen is what
we expect for PV-FP8 quantization.

[qkbf16-pvfp8-decode-b200.md](https://github.com/user-attachments/files/32128845/qkbf16-pvfp8-decode-b200.md)


## 🔬 Experimental Track

<!-- Only for PRs submitted under the experimental policy
(CONTRIBUTING.md → "Experimental APIs and Backends").
     Leave this section untouched for normal PRs. -->

## Reviewer Notes

Builds on top of
[#4879](https://github.com/flashinfer-ai/flashinfer/pull/4879), which is
supporting QK-BF16/PV-FP8 in PrimsTS FMHA context. This is already
merged.

Changes public API for `.plan()` by introducing new datatype param to
support the new mixed QK-BF16/PV-FP8 types for KV. See below for
changes.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **New Features**
  - Added mixed key/value cache dtype support for PrimTS decode.
  - BF16 query/key caches can use FP8 value caches with output scaling.
- Planning, execution, workspace sizing, and metrics now accept separate
key and value dtype settings.
- Added validation and profile support for supported combinations;
block-sparse routes retain matching-dtype requirements.

- **Documentation**
- Updated decode documentation and examples with separate key/value
types and limitations.

- **Tests**
- Added coverage for mixed-dtype accuracy, validation, profiles, and
resource configurations.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [2268a1a](https://github.com/flashinfer-ai/flashinfer/commit/2268a1aeb756872aba8690a33ad1eaf288573a75)

- **作者**: eigen
- **时间**: 2026-09-21T20:08:04Z
- **提交信息**: perf(cake_kda): regenerate the BF16 KDA modules from the current Cake revision (#5370)

<!-- .github/pull_request_template.md -->

## 📌 Description

Follow-up to #5363 (merged as `c6ec2cc`); this branch is rebased on
`main`
and contains only the regeneration commit.

The BF16 KDA prefill modules published by #5278 were generated before
the Cake
codegen changed its lane-id derivation and `griddepcontrol` placement.
The
346-row source-versus-export replay in #5363 measured those modules
1-22%
slower than the kernels the current Cake revision generates for the same
schedule (largest: `fused_checkpoint_direct_m128_page64_n32x2`, 1.18x on
B200
and 1.21x on GB300), while the one module #5363 generated from the
current
revision replayed at parity. Output was bitwise identical in both cases.

This PR regenerates every SM100a and SM103a BF16 module from Cake
`74220f6`
(the #5363 source revision) with `export_bf16.py --replace-existing`:
each
published specialization now points at its regenerated module, the
superseded
generated sources are removed, and modules whose generated code did not
change
keep their identity. No host dispatch, public API or routing change.

### Export parity and Triton comparison

Same protocol as #5363: for every one of the 346 inventory rows, in one
process per row, the Cake source dispatcher (Cake `74220f6`) and the
exported
FlashInfer API are prepared on identical fixtures, must select the same
schedule, are compared bitwise on output, final state and checkpoints,
and are
then captured into caller-owned CUDA graphs and replayed under cold-L2
CUPTI
(three alternating groups, median). The pinned SGLang FLA `chunk_kda`
Triton
baseline (`24c9251a`, the #5278 baseline) is captured and replayed the
same way
in the same process, with sigmoid applied to logit beta on the host as
in the
#5278 campaign. "Before" is the #5363 head measured in #5363; "after" is
this
branch with a fresh JIT workspace. B200 rows ran on NSC (148 SMs), GB300
rows
on OCI AGA (152 SMs).

**B200 (sm_100a, 148 SMs)**: 346 rows, 0 errors; schedule parity
346/346; bitwise output/state/checkpoint parity 346/346; export/source
graph-replay ratio min 0.974, median 1.000, max 1.013; rows above 1.03:
0. Triton/export speedup over 346 rows: min 1.20x, median 3.34x, max
12.88x; rows below 1.0x: 0.

<details open><summary>B200 (sm_100a, 148 SMs): export/source
graph-replay ratio per schedule, before (#5363 head) and after
regeneration</summary>

| Schedule | Rows | Before median | Before max | After median | After
max |
|---|---:|---:|---:|---:|---:|
| `fused_checkpoint_direct_m128_page64_n32x2` | 9 | 1.179 | 1.182 |
1.001 | 1.007 |
| `fused_active_beta_checkpoint_dvsplit_m64` | 44 | 1.065 | 1.102 |
0.999 | 1.013 |
| `fused_unbounded_softplus_direct_m128` | 8 | 1.041 | 1.056 | 1.001 |
1.010 |
| `fused_direct_m128` | 39 | 1.018 | 1.109 | 1.000 | 1.008 |
| `split_seq_affine_prefix_direct_m128_fp32_state` | 24 | 1.004 | 1.018
| 1.000 | 1.008 |
| `fused_checkpoint_direct_m128_n32` | 49 | 1.001 | 1.115 | 1.000 |
1.012 |
| `fused_m64_independent_dvsplit_fp32_state` | 98 | 1.000 | 1.049 |
1.000 | 1.011 |
| `fused_h12_direct_m128_n16` | 4 | 0.999 | 1.004 | 0.995 | 1.001 |
| `split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | 63 |
0.999 | 1.040 | 1.000 | 1.005 |
| `fused_checkpoint_tma_direct_m128_n16` | 8 | 0.995 | 1.007 | 1.001 |
1.013 |

</details>

<details><summary>B200 (sm_100a, 148 SMs): all rows, Triton versus
export (graph replay, cold-L2 CUPTI)</summary>

| Row | Shape | Schedule (export) | Bitwise | Triton µs | Export µs
(before) | Export µs (after) | Triton/Export |
|---:|---|---|---|---:|---:|---:|---:|
| 0 | `contract/h6_fixed_512` |
`fused_active_beta_checkpoint_dvsplit_m64` | yes | 72.1 | 44.3 | 41.3 |
1.75x |
| 1 | `contract/h6_fixed_8192` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
444.3 | 239.6 | 238.1 | 1.87x |
| 2 | `contract/h6_fixed_16384` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
910.6 | 374.1 | 371.7 | 2.45x |
| 3 | `contract/h6_packed_128x8` |
`fused_active_beta_checkpoint_dvsplit_m64` | yes | 66.2 | 19.3 | 18.2 |
3.64x |
| 4 | `contract/h6_packed_512x32` | `fused_checkpoint_direct_m128_n32` |
yes | 377.4 | 112.8 | 112.9 | 3.34x |
| 5 | `contract/h6_packed_1024x8` |
`fused_active_beta_checkpoint_dvsplit_m64` | yes | 212.7 | 81.8 | 76.5 |
2.78x |
| 6 | `contract/h6_packed_mixed_8192` |
`fused_active_beta_checkpoint_dvsplit_m64` | yes | 281.6 | 220.8 | 206.6
| 1.36x |
| 7 | `contract/h6_packed_4096x4` |
`fused_active_beta_checkpoint_dvsplit_m64` | yes | 481.5 | 291.0 | 271.9
| 1.77x |
| 8 | `contract/h6_fixed_63` |
`fused_active_beta_checkpoint_dvsplit_m64` | yes | 58.3 | 14.9 | 14.8 |
3.94x |
| 9 | `contract/h6_fixed_64` |
`fused_active_beta_checkpoint_dvsplit_m64` | yes | 62.0 | 13.2 | 12.2 |
5.09x |
| 10 | `contract/h6_fixed_65` |
`fused_active_beta_checkpoint_dvsplit_m64` | yes | 61.1 | 15.7 | 14.7 |
4.15x |
| 11 | `contract/h6_packed_17_33_65` |
`fused_active_beta_checkpoint_dvsplit_m64` | yes | 59.1 | 15.7 | 14.9 |
3.96x |
| 12 | `contract/h12_fixed_512` |
`fused_active_beta_checkpoint_dvsplit_m64` | yes | 75.1 | 44.7 | 41.6 |
1.81x |
| 13 | `contract/h12_fixed_8192` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
623.7 | 347.1 | 343.7 | 1.81x |
| 14 | `contract/h12_fixed_16384` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
1176.0 | 598.7 | 595.5 | 1.97x |
| 15 | `contract/h12_packed_128x8` |
`fused_checkpoint_direct_m128_page64_n32x2` | yes | 83.3 | 45.1 | 38.7 |
2.15x |
| 16 | `contract/h12_packed_512x32` | `fused_checkpoint_direct_m128_n32`
| yes | 699.4 | 162.4 | 161.5 | 4.33x |
| 17 | `contract/h12_packed_1024x8` | `fused_checkpoint_direct_m128_n32`
| yes | 389.7 | 97.7 | 98.5 | 3.96x |
| 18 | `contract/h12_packed_mixed_8192` |
`fused_active_beta_checkpoint_dvsplit_m64` | yes | 460.1 | 227.7 | 212.1
| 2.17x |
| 19 | `contract/h12_packed_4096x4` |
`fused_active_beta_checkpoint_dvsplit_m64` | yes | 765.1 | 293.5 | 274.4
| 2.79x |
| 20 | `contract/h12_fixed_63` |
`fused_active_beta_checkpoint_dvsplit_m64` | yes | 58.5 | 15.1 | 15.0 |
3.89x |
| 21 | `contract/h12_fixed_64` |
`fused_active_beta_checkpoint_dvsplit_m64` | yes | 60.2 | 13.2 | 12.3 |
4.89x |
| 22 | `contract/h12_fixed_65` |
`fused_active_beta_checkpoint_dvsplit_m64` | yes | 60.1 | 15.6 | 14.7 |
4.09x |
| 23 | `contract/h12_packed_17_33_65` |
`fused_active_beta_checkpoint_dvsplit_m64` | yes | 64.1 | 16.1 | 15.2 |
4.22x |
| 24 | `contract/h96_fixed_512` | `fused_checkpoint_direct_m128_n32` |
yes | 189.1 | 57.5 | 57.9 | 3.26x |
| 25 | `contract/h96_fixed_8192` | `fused_checkpoint_direct_m128_n32` |
yes | 2463.5 | 660.5 | 664.2 | 3.71x |
| 26 | `contract/h96_fixed_16384` | `fused_checkpoint_direct_m128_n32` |
yes | 4831.4 | 1305.3 | 1307.2 | 3.70x |
| 27 | `contract/h96_packed_128x8` | `fused_checkpoint_direct_m128_n32`
| yes | 392.8 | 134.1 | 127.8 | 3.07x |
| 28 | `contract/h96_packed_512x32` | `fused_checkpoint_direct_m128_n32`
| yes | 5023.8 | 1090.4 | 1098.8 | 4.57x |
| 29 | `contract/h96_packed_1024x8` | `fused_checkpoint_direct_m128_n32`
| yes | 2510.8 | 555.9 | 556.4 | 4.51x |
| 30 | `contract/h96_packed_mixed_8192` |
`fused_checkpoint_direct_m128_n32` | yes | 2544.2 | 500.9 | 500.5 |
5.08x |
| 31 | `contract/h96_packed_4096x4` | `fused_checkpoint_direct_m128_n32`
| yes | 4979.1 | 1011.1 | 1011.8 | 4.92x |
| 32 | `contract/h96_fixed_63` | `fused_checkpoint_direct_m128_n32` |
yes | 66.0 | 23.0 | 21.7 | 3.04x |
| 33 | `contract/h96_fixed_64` | `fused_checkpoint_direct_m128_n32` |
yes | 66.6 | 21.2 | 19.9 | 3.34x |
| 34 | `contract/h96_fixed_65` | `fused_checkpoint_direct_m128_n32` |
yes | 80.1 | 24.0 | 23.6 | 3.40x |
| 35 | `contract/h96_packed_17_33_65` |
`fused_checkpoint_direct_m128_n32` | yes | 107.5 | 40.8 | 38.6 | 2.79x |
| 36 | `contract/h6_fixed_32768` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
1779.0 | 624.6 | 623.2 | 2.85x |
| 37 | `contract/h6_fixed_65536` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
3493.5 | 1109.3 | 1108.9 | 3.15x |
| 38 | `contract/h6_packed_8192x4` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
896.1 | 627.2 | 623.7 | 1.44x |
| 39 | `contract/h6_packed_16384x2` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
1195.3 | 626.1 | 621.8 | 1.92x |
| 40 | `contract/h12_fixed_32768` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
2347.8 | 1077.2 | 1076.6 | 2.18x |
| 41 | `contract/h12_fixed_65536` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
4550.3 | 2050.9 | 2048.3 | 2.22x |
| 42 | `contract/h12_packed_8192x4` |
`fused_active_beta_checkpoint_dvsplit_m64` | yes | 1478.0 | 573.2 |
536.5 | 2.75x |
| 43 | `contract/h12_packed_16384x2` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
1783.8 | 1090.8 | 1084.0 | 1.65x |
| 44 | `contract/h96_fixed_32768` | `fused_checkpoint_direct_m128_n32` |
yes | 9817.1 | 2589.3 | 2598.9 | 3.78x |
| 45 | `contract/h96_fixed_65536` | `fused_checkpoint_direct_m128_n32` |
yes | 19190.8 | 5165.5 | 5180.1 | 3.70x |
| 46 | `contract/h96_packed_8192x4` | `fused_checkpoint_direct_m128_n32`
| yes | 9880.0 | 1988.2 | 1981.7 | 4.99x |
| 47 | `contract/h96_packed_16384x2` |
`fused_checkpoint_direct_m128_n32` | yes | 9942.1 | 2606.2 | 2605.3 |
3.82x |
| 48 | `contract/h12_short_t64_bs4` |
`fused_active_beta_checkpoint_dvsplit_m64` | yes | 60.7 | 13.9 | 13.2 |
4.62x |
| 49 | `contract/h12_short_t64_bs16` |
`fused_checkpoint_tma_direct_m128_n16` | yes | 86.5 | 34.0 | 34.5 |
2.51x |
| 50 | `contract/h12_short_t64_bs64` |
`fused_checkpoint_tma_direct_m128_n16` | yes | 210.0 | 98.2 | 98.8 |
2.13x |
| 51 | `contract/h12_short_t128_bs4` |
`fused_active_beta_checkpoint_dvsplit_m64` | yes | 71.0 | 25.6 | 24.5 |
2.90x |
| 52 | `contract/h12_short_t128_bs16` |
`fused_checkpoint_direct_m128_page64_n32x2` | yes | 118.6 | 88.3 | 75.2
| 1.58x |
| 53 | `contract/h12_short_t128_bs64` |
`fused_checkpoint_direct_m128_page64_n32x2` | yes | 379.0 | 260.8 |
222.6 | 1.70x |
| 54 | `contract/h12_short_t256_bs4` |
`fused_active_beta_checkpoint_dvsplit_m64` | yes | 85.0 | 29.0 | 26.8 |
3.18x |
| 55 | `contract/h12_short_t256_bs16` |
`fused_checkpoint_direct_m128_page64_n32x2` | yes | 192.8 | 150.8 |
127.5 | 1.51x |
| 56 | `contract/h12_short_t256_bs64` |
`fused_checkpoint_direct_m128_page64_n32x2` | yes | 674.0 | 448.6 |
382.9 | 1.76x |
| 57 | `contract/h12_short_varlen_17_64_65_127_128_255` |
`fused_active_beta_checkpoint_dvsplit_m64` | yes | 82.4 | 31.9 | 30.0 |
2.75x |
| 58 | `contract/h12_observed_gate_pad_26_28` |
`fused_active_beta_checkpoint_dvsplit_m64` | yes | 49.3 | 14.5 | 14.1 |
3.51x |
| 59 | `contract/h12_observed_gate_pad_68_80` |
`fused_active_beta_checkpoint_dvsplit_m64` | yes | 63.4 | 15.7 | 15.0 |
4.24x |
| 60 | `contract/h12_observed_gate_pad_502_512` |
`fused_active_beta_checkpoint_dvsplit_m64` | yes | 80.7 | 46.4 | 43.9 |
1.84x |
| 61 | `contract/h12_observed_gate_pad_1495_1536` |
`fused_active_beta_checkpoint_dvsplit_m64` | yes | 133.5 | 114.2 | 106.6
| 1.25x |
| 62 | `contract/h12_observed_gate_pad_2241_2241` |
`fused_active_beta_checkpoint_dvsplit_m64` | yes | 185.7 | 165.2 | 154.3
| 1.20x |
| 63 | `bounded/cp/1023:27` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 156.5 | 71.9 | 71.9 | 2.18x |
| 64 | `bounded/cp/1023:30` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 170.8 | 72.5 | 72.6 | 2.35x |
| 65 | `bounded/cp/1023:33` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 175.1 | 72.4 | 72.7 | 2.41x |
| 66 | `bounded/cp/1023:38` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 201.4 | 72.9 | 72.7 | 2.77x |
| 67 | `bounded/cp/1023:76` | `fused_checkpoint_direct_m128_n32` | yes |
346.2 | 94.8 | 94.9 | 3.65x |
| 68 | `bounded/cp/1024+1024+1024+1024:6` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 146.9 | 69.3 | 69.7 |
2.11x |
| 69 | `bounded/cp/1024+1024:12` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 156.5 | 64.8 | 65.3 |
2.40x |
| 70 | `bounded/cp/1024+1024:15` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 171.1 | 69.7 | 69.7 |
2.46x |
| 71 | `bounded/cp/1024:24` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 147.7 | 69.2 | 69.1 | 2.14x |
| 72 | `bounded/cp/1024:25` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 150.0 | 69.1 | 69.5 | 2.16x |
| 73 | `bounded/cp/1024:26` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 154.9 | 69.3 | 69.6 | 2.23x |
| 74 | `bounded/cp/1024:27` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 158.7 | 69.8 | 69.5 | 2.28x |
| 75 | `bounded/cp/1024:28` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 162.7 | 65.4 | 65.4 | 2.49x |
| 76 | `bounded/cp/1024:29` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 166.9 | 69.5 | 69.6 | 2.40x |
| 77 | `bounded/cp/1024:30` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 170.1 | 69.4 | 69.6 | 2.44x |
| 78 | `bounded/cp/1024:31` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 173.4 | 70.0 | 69.8 | 2.49x |
| 79 | `bounded/cp/1024:32` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 176.9 | 70.3 | 70.0 | 2.53x |
| 80 | `bounded/cp/1024:33` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 176.5 | 69.2 | 69.4 | 2.54x |
| 81 | `bounded/cp/1024:34` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 176.7 | 69.5 | 70.0 | 2.52x |
| 82 | `bounded/cp/1024:35` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 181.2 | 70.0 | 70.1 | 2.58x |
| 83 | `bounded/cp/1024:36` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 185.0 | 65.9 | 66.1 | 2.80x |
| 84 | `bounded/cp/1024:37` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 187.6 | 69.7 | 69.9 | 2.68x |
| 85 | `bounded/cp/1024:38` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 201.5 | 70.4 | 70.3 | 2.87x |
| 86 | `bounded/cp/1024:39` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 206.4 | 70.5 | 70.3 | 2.94x |
| 87 | `bounded/cp/1024:48` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 231.1 | 71.9 | 70.7 | 3.27x |
| 88 | `bounded/cp/1024:54` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 248.5 | 71.3 | 71.5 | 3.48x |
| 89 | `bounded/cp/1024:60` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 274.4 | 67.8 | 67.9 | 4.04x |
| 90 | `bounded/cp/1024:61` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 276.4 | 72.2 | 71.7 | 3.86x |
| 91 | `bounded/cp/1024:64` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 281.7 | 73.5 | 72.0 | 3.91x |
| 92 | `bounded/cp/1024:76` | `fused_checkpoint_direct_m128_n32` | yes |
345.8 | 93.2 | 94.1 | 3.67x |
| 93 | `bounded/cp/1024:77` | `fused_checkpoint_direct_m128_n32` | yes |
352.9 | 97.6 | 98.3 | 3.59x |
| 94 | `bounded/cp/1024:78` | `fused_checkpoint_direct_m128_n32` | yes |
355.9 | 97.8 | 97.7 | 3.64x |
| 95 | `bounded/cp/1025:24` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 149.5 | 71.2 | 71.4 | 2.09x |
| 96 | `bounded/cp/1025:27` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 163.9 | 71.0 | 71.4 | 2.29x |
| 97 |
`bounded/cp/128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128:12`
| `fused_checkpoint_direct_m128_n32` | yes | 445.4 | 134.0 | 122.0 |
3.65x |
| 98 |
`bounded/cp/128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128:6`
| `fused_checkpoint_direct_m128_n32` | yes | 229.3 | 71.0 | 68.7 | 3.34x
|
| 99 |
`bounded/cp/128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128:12`
| `fused_checkpoint_direct_m128_n32` | yes | 140.5 | 47.1 | 42.6 | 3.30x
|
| 100 | `bounded/cp/1537:36` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 271.0 | 95.7 | 96.1 |
2.82x |
| 101 | `bounded/cp/2048:24` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 270.6 | 125.7 | 126.0
| 2.15x |
| 102 | `bounded/cp/2048:27` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 287.9 | 125.4 | 125.5
| 2.29x |
| 103 | `bounded/cp/2048:30` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 307.7 | 126.0 | 125.7
| 2.45x |
| 104 | `bounded/cp/2048:31` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 313.4 | 125.8 | 125.7
| 2.49x |
| 105 | `bounded/cp/2048:32` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 332.7 | 126.4 | 127.2
| 2.62x |
| 106 | `bounded/cp/2048:33` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 325.8 | 126.6 | 125.4
| 2.60x |
| 107 | `bounded/cp/2048:38` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 379.5 | 127.5 | 126.9
| 2.99x |
| 108 | `bounded/cp/2048:48` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 442.9 | 127.4 | 127.4
| 3.48x |
| 109 | `bounded/cp/2048:60` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 511.1 | 123.9 | 125.0
| 4.09x |
| 110 | `bounded/cp/2048:76` | `fused_checkpoint_direct_m128_n32` | yes
| 629.2 | 174.8 | 175.3 | 3.59x |
| 111 |
`bounded/cp/255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255:6`
| `fused_checkpoint_direct_m128_n32` | yes | 421.5 | 110.2 | 103.7 |
4.06x |
| 112 |
`bounded/cp/255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255:12`
| `fused_checkpoint_direct_m128_n32` | yes | 227.8 | 67.0 | 65.9 | 3.46x
|
| 113 | `bounded/cp/255+255+255+255+255+255+255+255:12` |
`fused_checkpoint_direct_m128_n32` | yes | 141.5 | 34.8 | 35.0 | 4.04x |
| 114 |
`bounded/cp/256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256:12`
| `fused_checkpoint_direct_m128_n32` | yes | 769.9 | 191.9 | 189.3 |
4.07x |
| 115 |
`bounded/cp/256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256:5`
| `fused_checkpoint_direct_m128_n32` | yes | 370.4 | 99.6 | 98.8 | 3.75x
|
| 116 |
`bounded/cp/256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256:6`
| `fused_checkpoint_direct_m128_n32` | yes | 420.5 | 101.4 | 101.0 |
4.16x |
| 117 |
`bounded/cp/256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256:7`
| `fused_checkpoint_direct_m128_n32` | yes | 485.9 | 129.9 | 128.9 |
3.77x |
| 118 |
`bounded/cp/256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256:8`
| `fused_checkpoint_direct_m128_n32` | yes | 500.4 | 129.0 | 128.5 |
3.90x |
| 119 |
`bounded/cp/256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256:12`
| `fused_checkpoint_direct_m128_n32` | yes | 228.2 | 65.0 | 64.0 | 3.56x
|
| 120 |
`bounded/cp/256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256:6`
| `fused_checkpoint_direct_m128_n32` | yes | 133.4 | 37.1 | 36.9 | 3.61x
|
| 121 | `bounded/cp/32+512:18` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 96.7 | 40.8 | 41.0 |
2.36x |
| 122 | `bounded/cp/33+1025:12` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 116.8 | 66.6 | 66.6 |
1.75x |
| 123 | `bounded/cp/33+1025:14` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 120.5 | 70.5 | 71.0 |
1.70x |
| 124 | `bounded/cp/33+1025:20` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 148.7 | 66.9 | 66.9 |
2.22x |
| 125 | `bounded/cp/4096:24` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 520.5 | 237.8 | 238.4
| 2.18x |
| 126 | `bounded/cp/4096:27` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 553.2 | 237.7 | 236.7
| 2.34x |
| 127 | `bounded/cp/4096:30` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 581.5 | 239.2 | 238.1
| 2.44x |
| 128 | `bounded/cp/4096:31` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 593.5 | 236.7 | 237.2
| 2.50x |
| 129 | `bounded/cp/4096:32` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 628.7 | 238.0 | 238.5
| 2.64x |
| 130 | `bounded/cp/4096:33` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 617.5 | 237.7 | 236.9
| 2.61x |
| 131 | `bounded/cp/4096:38` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 697.1 | 237.9 | 237.7
| 2.93x |
| 132 | `bounded/cp/4096:48` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 806.0 | 239.9 | 239.5
| 3.36x |
| 133 | `bounded/cp/4096:60` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 975.8 | 234.7 | 236.4
| 4.13x |
| 134 | `bounded/cp/511:23` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 102.4 | 44.2 | 44.1 | 2.32x |
| 135 | `bounded/cp/511:30` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 108.6 | 44.5 | 44.4 | 2.45x |
| 136 | `bounded/cp/511:48` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 136.9 | 45.1 | 45.1 | 3.03x |
| 137 | `bounded/cp/512+512+512+512:12` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 145.7 | 38.4 | 38.4 |
3.79x |
| 138 | `bounded/cp/512+512+512+512:16` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 172.4 | 44.1 | 43.3 |
3.98x |
| 139 | `bounded/cp/512:23` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 101.5 | 40.8 | 41.1 | 2.47x |
| 140 | `bounded/cp/512:24` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 102.6 | 41.2 | 41.1 | 2.50x |
| 141 | `bounded/cp/512:30` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 106.6 | 41.3 | 41.5 | 2.57x |
| 142 | `bounded/cp/512:38` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 128.2 | 42.0 | 41.6 | 3.08x |
| 143 | `bounded/cp/512:39` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 127.5 | 41.8 | 42.0 | 3.04x |
| 144 | `bounded/cp/512:48` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 136.4 | 42.2 | 42.4 | 3.22x |
| 145 | `bounded/cp/512:60` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 156.2 | 39.0 | 39.5 | 3.95x |
| 146 | `bounded/cp/512:76` | `fused_checkpoint_direct_m128_n32` | yes |
190.9 | 53.2 | 52.9 | 3.61x |
| 147 | `bounded/cp/512:77` | `fused_checkpoint_direct_m128_n32` | yes |
186.0 | 57.2 | 57.2 | 3.25x |
| 148 | `bounded/cp/513+256:18` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 105.0 | 43.0 | 43.2 |
2.43x |
| 149 | `bounded/cp/513:24` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 101.2 | 43.3 | 43.4 | 2.33x |
| 150 | `bounded/cp/513:38` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 131.6 | 44.3 | 43.8 | 3.01x |
| 151 | `bounded/cp/513:76` | `fused_checkpoint_direct_m128_n32` | yes |
192.4 | 55.8 | 56.1 | 3.43x |
| 152 | `bounded/cp/513:77` | `fused_checkpoint_direct_m128_n32` | yes |
193.3 | 59.9 | 60.6 | 3.19x |
| 153 |
`bounded/cp/64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64:12`
| `fused_checkpoint_tma_direct_m128_n16` | yes | 248.5 | 94.0 | 96.2 |
2.58x |
| 154 |
`bounded/cp/64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64:6`
| `fused_checkpoint_direct_m128_n32` | yes | 149.4 | 52.5 | 49.6 | 3.01x
|
| 155 | `bounded/cp/64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64:12`
| `fused_checkpoint_tma_direct_m128_n16` | yes | 98.9 | 34.1 | 34.7 |
2.85x |
| 156 | `bounded/cp/64+64+64+64+64+64+64+64:12` |
`fused_checkpoint_tma_direct_m128_n16` | yes | 86.0 | 17.8 | 17.9 |
4.81x |
| 157 | `bounded/cp/65+65+65+65+65+65+65+65:12` |
`fused_checkpoint_direct_m128_n32` | yes | 89.5 | 23.4 | 21.3 | 4.19x |
| 158 | `bounded/cp/768:30` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 139.6 | 55.7 | 55.3 | 2.52x |
| 159 | `bounded/nocp/1023:76` | `fused_direct_m128` | yes | 347.0 |
70.2 | 69.2 | 5.02x |
| 160 | `bounded/nocp/1024:48` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 230.4 | 60.6 | 60.4 |
3.81x |
| 161 | `bounded/nocp/1024:64` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 293.8 | 61.7 | 61.7 |
4.76x |
| 162 | `bounded/nocp/1024:75` | `fused_direct_m128` | yes | 343.8 |
72.8 | 72.1 | 4.77x |
| 163 | `bounded/nocp/1024:76` | `fused_direct_m128` | yes | 345.9 |
68.8 | 67.8 | 5.10x |
| 164 | `bounded/nocp/1024:77` | `fused_direct_m128` | yes | 350.1 |
72.6 | 72.5 | 4.83x |
| 165 | `bounded/nocp/1024:78` | `fused_direct_m128` | yes | 355.0 |
72.6 | 72.9 | 4.87x |
| 166 | `bounded/nocp/1025:40` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 213.6 | 62.0 | 61.6 |
3.47x |
| 167 |
`bounded/nocp/128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128:1`
| `fused_m64_independent_dvsplit_fp32_state` | yes | 79.3 | 19.8 | 19.9
| 3.98x |
| 168 |
`bounded/nocp/128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128:12`
| `fused_direct_m128` | yes | 442.4 | 119.5 | 108.7 | 4.07x |
| 169 |
`bounded/nocp/128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128:6`
| `fused_direct_m128` | yes | 233.0 | 64.8 | 62.2 | 3.75x |
| 170 |
`bounded/nocp/128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128:7`
| `fused_direct_m128` | yes | 269.0 | 81.2 | 76.1 | 3.53x |
| 171 |
`bounded/nocp/128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128:1`
| `fused_m64_independent_dvsplit_fp32_state` | yes | 70.0 | 18.0 | 18.1
| 3.87x |
| 172 |
`bounded/nocp/128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128:12`
| `fused_direct_m128` | yes | 141.1 | 41.3 | 37.2 | 3.79x |
| 173 |
`bounded/nocp/128+128+128+128+128+128+128+128+128+128+128+128+128+128+128+128:6`
| `fused_direct_m128` | yes | 97.9 | 24.4 | 23.7 | 4.13x |
| 174 | `bounded/nocp/128+128+128+128:1` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 72.2 | 17.1 | 17.6 |
4.10x |
| 175 | `bounded/nocp/128+128+128+128:12` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 84.3 | 15.5 | 15.7 |
5.38x |
| 176 | `bounded/nocp/128+128+128+128:6` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 73.9 | 18.7 | 18.6 |
3.97x |
| 177 |
`bounded/nocp/129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129:7`
| `fused_direct_m128` | yes | 319.9 | 84.9 | 80.6 | 3.97x |
| 178 |
`bounded/nocp/129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129+129:7`
| `fused_direct_m128` | yes | 266.1 | 70.0 | 67.0 | 3.97x |
| 179 |
`bounded/nocp/129+255+129+255+129+255+129+255+129+255+129+255+129+255+129+255+129+255+129+255+129+255+129+255+129+255+129+255+129+255+129+255+129+255+129+255+129+255+129+255+129+255+129+255+129+255+129+255+129+255+129+255+129+255+129+255+129+255+129+255+129+255+129+255:6`
| `fused_direct_m128` | yes | 355.1 | 79.0 | 75.3 | 4.72x |
| 180 |
`bounded/nocp/192+192+192+192+192+192+192+192+192+192+192+192+192+192+192+192+192+192+192+192+192+192+192+192+192+192+192+192+192+192+192+192+192+192+192+192+192+192+192+192+192+192+192+192+192+192+192+192+192+192+192+192+192+192+192+192+192+192+192+192+192+192+192+192:7`
| `fused_direct_m128` | yes | 396.0 | 99.6 | 90.3 | 4.38x |
| 181 | `bounded/nocp/2048:32` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 332.9 | 104.9 | 105.5
| 3.15x |
| 182 |
`bounded/nocp/255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255:6`
| `fused_direct_m128` | yes | 423.5 | 96.1 | 89.2 | 4.75x |
| 183 |
`bounded/nocp/255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255:7`
| `fused_direct_m128` | yes | 485.2 | 118.2 | 108.4 | 4.47x |
| 184 |
`bounded/nocp/255+255+255+255+255+255+255+255+255+255+255+255+255+255+255+255:12`
| `fused_direct_m128` | yes | 227.1 | 57.9 | 56.8 | 4.00x |
| 185 | `bounded/nocp/255+255+255+255+255+255+255+255:12` |
`fused_direct_m128` | yes | 140.8 | 29.9 | 29.6 | 4.76x |
| 186 | `bounded/nocp/255+255+255+255:12` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 98.1 | 25.5 | 25.3 |
3.87x |
| 187 |
`bounded/nocp/255+256+255+256+255+256+255+256+255+256+255+256+255+256+255+256+255+256+255+256+255+256+255+256+255+256+255+256+255+256+255+256+255+256+255+256+255+256+255+256+255+256+255+256+255+256+255+256+255+256+255+256+255+256+255+256+255+256+255+256+255+256+255+256:7`
| `fused_direct_m128` | yes | 485.7 | 110.3 | 107.8 | 4.50x |
| 188 |
`bounded/nocp/256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256:3`
| `fused_direct_m128` | yes | 442.2 | 87.1 | 85.3 | 5.18x |
| 189 |
`bounded/nocp/256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256:5`
| `fused_direct_m128` | yes | 433.8 | 85.6 | 83.7 | 5.18x |
| 190 |
`bounded/nocp/256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256:7`
| `fused_direct_m128` | yes | 497.4 | 109.2 | 108.2 | 4.60x |
| 191 |
`bounded/nocp/256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256:7`
| `fused_direct_m128` | yes | 492.9 | 108.2 | 106.1 | 4.65x |
| 192 |
`bounded/nocp/256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256:1`
| `fused_m64_independent_dvsplit_fp32_state` | yes | 102.5 | 25.9 | 25.9
| 3.96x |
| 193 |
`bounded/nocp/256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256:12`
| `fused_direct_m128` | yes | 769.6 | 155.9 | 153.1 | 5.03x |
| 194 |
`bounded/nocp/256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256:5`
| `fused_direct_m128` | yes | 370.5 | 85.6 | 83.5 | 4.44x |
| 195 |
`bounded/nocp/256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256:6`
| `fused_direct_m128` | yes | 422.8 | 85.7 | 84.1 | 5.03x |
| 196 |
`bounded/nocp/256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256:7`
| `fused_direct_m128` | yes | 486.3 | 107.9 | 107.2 | 4.54x |
| 197 |
`bounded/nocp/256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256:6`
| `fused_direct_m128` | yes | 420.2 | 85.5 | 84.2 | 4.99x |
| 198 |
`bounded/nocp/256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256:5`
| `fused_direct_m128` | yes | 358.2 | 83.8 | 82.4 | 4.35x |
| 199 |
`bounded/nocp/256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256:5`
| `fused_direct_m128` | yes | 352.6 | 82.8 | 79.7 | 4.42x |
| 200 |
`bounded/nocp/256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256:8`
| `fused_direct_m128` | yes | 454.5 | 109.9 | 107.2 | 4.24x |
| 201 |
`bounded/nocp/256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256:7`
| `fused_direct_m128` | yes | 433.4 | 86.0 | 84.5 | 5.13x |
| 202 |
`bounded/nocp/256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256:1`
| `fused_m64_independent_dvsplit_fp32_state` | yes | 78.6 | 23.7 | 24.1
| 3.26x |
| 203 |
`bounded/nocp/256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256:12`
| `fused_direct_m128` | yes | 228.2 | 54.8 | 52.8 | 4.32x |
| 204 |
`bounded/nocp/256+256+256+256+256+256+256+256+256+256+256+256+256+256+256+256:6`
| `fused_direct_m128` | yes | 133.2 | 32.2 | 31.9 | 4.17x |
| 205 | `bounded/nocp/256+256+256+256:1` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 76.4 | 23.6 | 23.3 |
3.27x |
| 206 | `bounded/nocp/256+256+256+256:11` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 96.2 | 25.4 | 25.0 |
3.85x |
| 207 | `bounded/nocp/256+256+256+256:12` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 96.7 | 21.6 | 21.5 |
4.50x |
| 208 | `bounded/nocp/256+256+256+256:13` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 100.2 | 25.5 | 25.5 |
3.92x |
| 209 | `bounded/nocp/256+256+256+256:6` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 79.3 | 24.4 | 24.4 |
3.25x |
| 210 | `bounded/nocp/257+257+257+257:12` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 97.5 | 23.4 | 23.3 |
4.18x |
| 211 | `bounded/nocp/33+1025:12` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 116.3 | 56.3 | 56.7 |
2.05x |
| 212 | `bounded/nocp/4096:1` |
`split_seq_affine_prefix_direct_m128_fp32_state` | yes | 177.8 | 112.7 |
112.5 | 1.58x |
| 213 | `bounded/nocp/4096:12` |
`split_seq_affine_prefix_direct_m128_fp32_state` | yes | 346.1 | 147.2 |
146.5 | 2.36x |
| 214 | `bounded/nocp/4096:6` |
`split_seq_affine_prefix_direct_m128_fp32_state` | yes | 234.8 | 129.8 |
129.4 | 1.81x |
| 215 | `bounded/nocp/512:32` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 108.2 | 36.2 | 36.2 |
2.99x |
| 216 | `bounded/nocp/512:48` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 137.1 | 36.9 | 37.0 |
3.71x |
| 217 | `bounded/nocp/512:64` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 165.9 | 37.9 | 38.0 |
4.36x |
| 218 | `bounded/nocp/512:76` | `fused_direct_m128` | yes | 190.5 | 41.4
| 41.1 | 4.64x |
| 219 | `bounded/nocp/512:77` | `fused_direct_m128` | yes | 186.8 | 45.4
| 44.8 | 4.17x |
| 220 | `bounded/nocp/513:77` | `fused_direct_m128` | yes | 193.5 | 47.2
| 47.0 | 4.12x |
| 221 |
`bounded/nocp/64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64:1`
| `fused_m64_independent_dvsplit_fp32_state` | yes | 74.5 | 15.9 | 15.8
| 4.70x |
| 222 |
`bounded/nocp/64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64:12`
| `fused_h12_direct_m128_n16` | yes | 249.1 | 89.1 | 88.3 | 2.82x |
| 223 |
`bounded/nocp/64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64:6`
| `fused_direct_m128` | yes | 145.2 | 50.4 | 47.0 | 3.09x |
| 224 | `bounded/nocp/64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64:1`
| `fused_m64_independent_dvsplit_fp32_state` | yes | 67.1 | 14.9 | 14.7
| 4.58x |
| 225 |
`bounded/nocp/64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64:12` |
`fused_h12_direct_m128_n16` | yes | 99.8 | 31.0 | 31.1 | 3.21x |
| 226 | `bounded/nocp/64+64+64+64+64+64+64+64+64+64+64+64+64+64+64+64:6`
| `fused_direct_m128` | yes | 77.9 | 20.3 | 19.3 | 4.04x |
| 227 | `bounded/nocp/64+64+64+64+64+64+64+64:12` |
`fused_h12_direct_m128_n16` | yes | 84.7 | 15.9 | 16.0 | 5.29x |
| 228 | `bounded/nocp/64+64+64+64:1` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 65.3 | 13.6 | 13.3 |
4.90x |
| 229 | `bounded/nocp/64+64+64+64:12` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 82.4 | 11.8 | 11.8 |
6.96x |
| 230 | `bounded/nocp/64+64+64+64:6` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 71.4 | 14.8 | 15.1 |
4.73x |
| 231 | `bounded/nocp/65+65+65+65+65+65+65+65:12` |
`fused_h12_direct_m128_n16` | yes | 88.5 | 17.1 | 17.0 | 5.22x |
| 232 | `affine/2` | `split_seq_affine_prefix_direct_m128_fp32_state` |
yes | 293.5 | 132.7 | 133.6 | 2.20x |
| 233 | `affine/5` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
295.2 | 158.3 | 158.6 | 1.86x |
| 234 | `affine/8` | `split_seq_affine_prefix_direct_m128_fp32_state` |
yes | 299.2 | 133.1 | 133.6 | 2.24x |
| 235 | `affine/11` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
296.5 | 163.9 | 165.7 | 1.79x |
| 236 | `affine/14` | `split_seq_affine_prefix_direct_m128_fp32_state` |
yes | 1271.3 | 331.6 | 327.9 | 3.88x |
| 237 | `affine/17` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
1274.0 | 595.8 | 597.0 | 2.13x |
| 238 | `affine/20` | `split_seq_affine_prefix_direct_m128_fp32_state` |
yes | 1273.4 | 332.9 | 329.1 | 3.87x |
| 239 | `affine/23` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
1280.1 | 599.0 | 595.1 | 2.15x |
| 240 | `affine/26` | `split_seq_affine_prefix_direct_m128_fp32_state` |
yes | 3658.9 | 598.2 | 595.0 | 6.15x |
| 241 | `affine/29` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
3671.7 | 1107.1 | 1106.7 | 3.32x |
| 242 | `affine/32` | `split_seq_affine_prefix_direct_m128_fp32_state` |
yes | 3669.2 | 601.0 | 594.3 | 6.17x |
| 243 | `affine/35` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
3682.8 | 1110.5 | 1103.8 | 3.34x |
| 244 | `affine/38` | `split_seq_affine_prefix_direct_m128_fp32_state` |
yes | 595.4 | 178.4 | 177.5 | 3.35x |
| 245 | `affine/41` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
613.6 | 225.9 | 224.5 | 2.73x |
| 246 | `affine/44` | `split_seq_affine_prefix_direct_m128_fp32_state` |
yes | 824.6 | 190.9 | 188.9 | 4.37x |
| 247 | `affine/47` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
829.9 | 275.9 | 274.6 | 3.02x |
| 248 | `affine/60` | `split_seq_affine_prefix_direct_m128_fp32_state` |
yes | 294.2 | 141.7 | 142.1 | 2.07x |
| 249 | `affine/73` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
297.3 | 175.0 | 175.8 | 1.69x |
| 250 | `affine/82` | `split_seq_affine_prefix_direct_m128_fp32_state` |
yes | 321.8 | 150.8 | 150.0 | 2.15x |
| 251 | `affine/91` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
320.4 | 190.0 | 192.2 | 1.67x |
| 252 | `affine/104` | `split_seq_affine_prefix_direct_m128_fp32_state`
| yes | 321.1 | 143.7 | 144.4 | 2.22x |
| 253 | `affine/117` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
322.9 | 185.5 | 184.9 | 1.75x |
| 254 | `affine/130` | `split_seq_affine_prefix_direct_m128_fp32_state`
| yes | 1972.9 | 409.4 | 406.1 | 4.86x |
| 255 | `affine/143` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
1970.3 | 719.0 | 715.4 | 2.75x |
| 256 | `affine/152` | `split_seq_affine_prefix_direct_m128_fp32_state`
| yes | 2632.8 | 669.8 | 662.9 | 3.97x |
| 257 | `affine/161` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
2628.6 | 1259.9 | 1259.3 | 2.09x |
| 258 | `affine/170` | `split_seq_affine_prefix_direct_m128_fp32_state`
| yes | 3580.9 | 1306.2 | 1276.8 | 2.80x |
| 259 | `affine/179` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
3649.1 | 2305.4 | 2299.0 | 1.59x |
| 260 | `unbounded/226` | `fused_unbounded_softplus_direct_m128` | yes |
82.1 | 19.9 | 19.5 | 4.20x |
| 261 | `unbounded/233` | `fused_unbounded_softplus_direct_m128` | yes |
83.0 | 20.1 | 19.8 | 4.19x |
| 262 | `unbounded/240` | `fused_unbounded_softplus_direct_m128` | yes |
231.5 | 83.6 | 79.0 | 2.93x |
| 263 | `unbounded/247` | `fused_unbounded_softplus_direct_m128` | yes |
231.5 | 86.1 | 82.3 | 2.81x |
| 264 | `unbounded/254` | `fused_unbounded_softplus_direct_m128` | yes |
82.1 | 44.0 | 41.8 | 1.96x |
| 265 | `unbounded/261` | `fused_unbounded_softplus_direct_m128` | yes |
83.0 | 45.6 | 43.7 | 1.90x |
| 266 | `unbounded/268` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
236.1 | 197.3 | 190.3 | 1.24x |
| 267 | `unbounded/275` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
232.1 | 201.1 | 193.7 | 1.20x |
| 268 | `unbounded/282` | `fused_unbounded_softplus_direct_m128` | yes |
67.0 | 28.2 | 27.0 | 2.48x |
| 269 | `unbounded/289` | `fused_unbounded_softplus_direct_m128` | yes |
68.3 | 28.1 | 26.7 | 2.56x |
| 270 | `long/H1/cp0/chain0` |
`split_seq_affine_prefix_direct_m128_fp32_state` | yes | 5011.5 | 404.8
| 402.0 | 12.47x |
| 271 | `long/H1/cp0/chain1` |
`split_seq_affine_prefix_direct_m128_fp32_state` | yes | 5174.6 | 403.3
| 401.8 | 12.88x |
| 272 | `long/H1/cp1/chain0` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
4986.8 | 581.1 | 582.8 | 8.56x |
| 273 | `long/H1/cp1/chain1` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
5191.3 | 580.5 | 581.1 | 8.93x |
| 274 | `pressure/H1/shift0/chain0` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
5013.2 | 581.5 | 583.0 | 8.60x |
| 275 | `pressure/H1/shift0/chain1` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
5174.4 | 580.7 | 582.7 | 8.88x |
| 276 | `pressure/H1/shift2/chain0` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
4967.8 | 580.2 | 582.8 | 8.52x |
| 277 | `pressure/H1/shift2/chain1` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
5209.9 | 579.9 | 583.1 | 8.94x |
| 278 | `pressure/H1/shift4/chain0` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
5015.0 | 579.6 | 582.5 | 8.61x |
| 279 | `pressure/H1/shift4/chain1` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
5171.9 | 580.5 | 582.2 | 8.88x |
| 280 | `pressure/H1/shift6/chain0` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
4969.4 | 579.4 | 582.2 | 8.54x |
| 281 | `pressure/H1/shift6/chain1` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
5195.1 | 579.6 | 582.5 | 8.92x |
| 282 | `pressure/H1/shift8/chain0` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
5020.8 | 579.5 | 581.6 | 8.63x |
| 283 | `pressure/H1/shift8/chain1` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
5173.2 | 581.1 | 580.8 | 8.91x |
| 284 | `long/H6/cp0/chain0` |
`split_seq_affine_prefix_direct_m128_fp32_state` | yes | 7236.7 | 1074.5
| 1068.8 | 6.77x |
| 285 | `long/H6/cp0/chain1` |
`split_seq_affine_prefix_direct_m128_fp32_state` | yes | 7257.8 | 1076.4
| 1070.8 | 6.78x |
| 286 | `long/H6/cp1/chain0` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
7235.7 | 2090.5 | 2091.0 | 3.46x |
| 287 | `long/H6/cp1/chain1` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
7268.9 | 2092.5 | 2085.8 | 3.48x |
| 288 | `pressure/H6/shift0/chain0` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
7235.5 | 2084.2 | 2090.4 | 3.46x |
| 289 | `pressure/H6/shift0/chain1` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
7259.7 | 2090.4 | 2091.7 | 3.47x |
| 290 | `pressure/H6/shift2/chain0` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
7228.8 | 2089.8 | 2093.0 | 3.45x |
| 291 | `pressure/H6/shift2/chain1` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
7269.8 | 2092.1 | 2087.5 | 3.48x |
| 292 | `pressure/H6/shift4/chain0` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
7234.8 | 2084.4 | 2091.6 | 3.46x |
| 293 | `pressure/H6/shift4/chain1` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
7261.6 | 2087.5 | 2093.4 | 3.47x |
| 294 | `pressure/H6/shift6/chain0` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
7231.6 | 2091.5 | 2093.9 | 3.45x |
| 295 | `pressure/H6/shift6/chain1` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
7276.9 | 2092.1 | 2089.6 | 3.48x |
| 296 | `pressure/H6/shift8/chain0` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
7235.4 | 2086.8 | 2091.3 | 3.46x |
| 297 | `pressure/H6/shift8/chain1` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
7262.3 | 2089.6 | 2091.0 | 3.47x |
| 298 | `long/H12/cp0/chain0` |
`split_seq_affine_prefix_direct_m128_fp32_state` | yes | 9697.0 | 2015.8
| 1988.2 | 4.88x |
| 299 | `long/H12/cp0/chain1` |
`split_seq_affine_prefix_direct_m128_fp32_state` | yes | 9775.7 | 2017.4
| 1994.5 | 4.90x |
| 300 | `long/H12/cp1/chain0` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
9722.2 | 3979.2 | 3985.8 | 2.44x |
| 301 | `long/H12/cp1/chain1` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
9711.4 | 3985.0 | 3987.3 | 2.44x |
| 302 | `pressure/H12/shift0/chain0` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
9696.7 | 3992.1 | 3986.6 | 2.43x |
| 303 | `pressure/H12/shift0/chain1` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
9772.7 | 3994.9 | 3989.9 | 2.45x |
| 304 | `pressure/H12/shift2/chain0` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
9725.5 | 3976.7 | 3984.5 | 2.44x |
| 305 | `pressure/H12/shift2/chain1` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
9710.9 | 3985.7 | 3990.2 | 2.43x |
| 306 | `pressure/H12/shift4/chain0` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
9694.8 | 3993.0 | 3986.8 | 2.43x |
| 307 | `pressure/H12/shift4/chain1` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
9772.3 | 3992.9 | 3989.8 | 2.45x |
| 308 | `pressure/H12/shift6/chain0` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
9722.5 | 3977.8 | 3986.7 | 2.44x |
| 309 | `pressure/H12/shift6/chain1` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
9710.6 | 3985.9 | 3989.8 | 2.43x |
| 310 | `pressure/H12/shift8/chain0` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
9697.0 | 3992.3 | 3986.1 | 2.43x |
| 311 | `pressure/H12/shift8/chain1` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
9775.4 | 3994.4 | 3987.9 | 2.45x |
| 312 | `short/H1/t64_b4` | `fused_active_beta_checkpoint_dvsplit_m64` |
yes | 56.4 | 13.2 | 12.5 | 4.50x |
| 313 | `short/H1/t64_b16` | `fused_active_beta_checkpoint_dvsplit_m64`
| yes | 60.8 | 13.3 | 12.8 | 4.76x |
| 314 | `short/H1/t64_b64` | `fused_active_beta_checkpoint_dvsplit_m64`
| yes | 63.7 | 14.6 | 14.0 | 4.56x |
| 315 | `short/H1/t128_b4` | `fused_active_beta_checkpoint_dvsplit_m64`
| yes | 58.3 | 18.1 | 17.2 | 3.39x |
| 316 | `short/H1/t128_b16` | `fused_active_beta_checkpoint_dvsplit_m64`
| yes | 59.6 | 18.3 | 17.6 | 3.39x |
| 317 | `short/H1/t128_b64` | `fused_active_beta_checkpoint_dvsplit_m64`
| yes | 68.2 | 20.3 | 18.9 | 3.60x |
| 318 | `short/H1/t256_b4` | `fused_active_beta_checkpoint_dvsplit_m64`
| yes | 65.9 | 27.0 | 25.2 | 2.62x |
| 319 | `short/H1/t256_b16` | `fused_active_beta_checkpoint_dvsplit_m64`
| yes | 64.8 | 27.4 | 25.7 | 2.52x |
| 320 | `short/H1/t256_b64` | `fused_active_beta_checkpoint_dvsplit_m64`
| yes | 89.6 | 29.8 | 27.7 | 3.23x |
| 321 | `short/H1/mixed` | `fused_active_beta_checkpoint_dvsplit_m64` |
yes | 66.0 | 29.3 | 28.1 | 2.35x |
| 322 | `short/H6/t64_b4` | `fused_active_beta_checkpoint_dvsplit_m64` |
yes | 61.4 | 13.4 | 12.8 | 4.79x |
| 323 | `short/H6/t64_b16` | `fused_checkpoint_direct_m128_n32` | yes |
65.0 | 22.6 | 22.0 | 2.95x |
| 324 | `short/H6/t64_b64` | `fused_checkpoint_direct_m128_n32` | yes |
124.9 | 55.0 | 52.5 | 2.38x |
| 325 | `short/H6/t128_b4` | `fused_active_beta_checkpoint_dvsplit_m64`
| yes | 63.6 | 18.7 | 17.6 | 3.62x |
| 326 | `short/H6/t128_b16` | `fused_checkpoint_direct_m128_n32` | yes |
84.1 | 28.5 | 29.1 | 2.89x |
| 327 | `short/H6/t128_b64` | `fused_checkpoint_direct_m128_n32` | yes |
201.2 | 73.7 | 71.2 | 2.82x |
| 328 | `short/H6/t256_b4` | `fused_active_beta_checkpoint_dvsplit_m64`
| yes | 66.6 | 27.7 | 25.9 | 2.57x |
| 329 | `short/H6/t256_b16` | `fused_checkpoint_direct_m128_n32` | yes |
116.5 | 39.3 | 39.8 | 2.93x |
| 330 | `short/H6/t256_b64` | `fused_checkpoint_direct_m128_n32` | yes |
371.8 | 103.9 | 103.8 | 3.58x |
| 331 | `short/H6/mixed` | `fused_active_beta_checkpoint_dvsplit_m64` |
yes | 66.5 | 30.6 | 28.9 | 2.30x |
| 332 | `short/H12/t64_b4` | `fused_active_beta_checkpoint_dvsplit_m64`
| yes | 61.0 | 14.1 | 13.2 | 4.61x |
| 333 | `short/H12/t64_b16` | `fused_checkpoint_tma_direct_m128_n16` |
yes | 86.7 | 33.8 | 33.7 | 2.57x |
| 334 | `short/H12/t64_b64` | `fused_checkpoint_tma_direct_m128_n16` |
yes | 211.2 | 96.5 | 97.0 | 2.18x |
| 335 | `short/H12/t128_b4` | `fused_active_beta_checkpoint_dvsplit_m64`
| yes | 64.1 | 19.6 | 18.3 | 3.51x |
| 336 | `short/H12/t128_b16` |
`fused_checkpoint_direct_m128_page64_n32x2` | yes | 118.4 | 87.7 | 74.4
| 1.59x |
| 337 | `short/H12/t128_b64` |
`fused_checkpoint_direct_m128_page64_n32x2` | yes | 379.4 | 260.5 |
220.4 | 1.72x |
| 338 | `short/H12/t256_b4` | `fused_active_beta_checkpoint_dvsplit_m64`
| yes | 84.9 | 29.0 | 26.8 | 3.17x |
| 339 | `short/H12/t256_b16` |
`fused_checkpoint_direct_m128_page64_n32x2` | yes | 192.6 | 150.2 |
126.8 | 1.52x |
| 340 | `short/H12/t256_b64` |
`fused_checkpoint_direct_m128_page64_n32x2` | yes | 674.0 | 447.3 |
380.7 | 1.77x |
| 341 | `short/H12/mixed` | `fused_active_beta_checkpoint_dvsplit_m64` |
yes | 75.4 | 31.7 | 30.1 | 2.51x |
| 342 | `export_holdout/H1/t64_b1_logits` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 66.4 | 12.9 | 13.1 |
5.07x |
| 343 | `export_holdout/H6/t64_b1_logits` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 64.4 | 13.7 | 14.2 |
4.55x |
| 344 | `export_holdout/H12/t64_b1_logits` |
`fused_checkpoint_tma_direct_m128_n16` | yes | 75.1 | 16.6 | 16.8 |
4.46x |
| 345 | `export_holdout/H6/t8193_b1_active_nocp` |
`split_seq_affine_prefix_direct_m128_fp32_state` | yes | 473.6 | 172.5 |
171.0 | 2.77x |

</details>

**GB300 (sm_103a, 152 SMs)**: 346 rows, 0 errors; schedule parity
346/346; bitwise output/state/checkpoint parity 346/346; export/source
graph-replay ratio min 0.971, median 1.000, max 1.046; rows above 1.03:
1. Triton/export speedup over 346 rows: min 1.16x, median 3.32x, max
12.85x; rows below 1.0x: 0. The one row above 1.03 is
`export_holdout/H1/t64_b1_logits` (1.046: 12.06 versus 12.61 µs, all
three groups), served by the `fused_m64_independent_dvsplit_fp32_state`
module that this PR leaves byte-identical; the same row measured 0.998
on GB300 before this change and 0.994 on B200 after it, so it is a 0.5
µs run-to-run offset on a 12 µs kernel, not a regeneration effect.

<details open><summary>GB300 (sm_103a, 152 SMs): export/source
graph-replay ratio per schedule, before (#5363 head) and after
regeneration</summary>

| Schedule | Rows | Before median | Before max | After median | After
max |
|---|---:|---:|---:|---:|---:|
| `fused_checkpoint_direct_m128_page64_n32x2` | 9 | 1.211 | 1.222 |
1.000 | 1.005 |
| `fused_unbounded_softplus_direct_m128` | 8 | 1.086 | 1.116 | 0.999 |
1.002 |
| `fused_active_beta_checkpoint_dvsplit_m64` | 44 | 1.057 | 1.097 |
1.000 | 1.012 |
| `fused_direct_m128` | 31 | 1.034 | 1.127 | 1.002 | 1.010 |
| `fused_prediction_first_direct_m128` | 4 | 1.017 | 1.018 | 1.001 |
1.003 |
| `fused_checkpoint_direct_m128_n32` | 44 | 1.013 | 1.120 | 1.000 |
1.017 |
| `split_seq_affine_prefix_direct_m128_fp32_state` | 24 | 1.013 | 1.036
| 1.000 | 1.015 |
| `fused_checkpoint_tma_direct_m128_n16` | 8 | 1.007 | 1.022 | 1.002 |
1.007 |
| `split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | 63 |
1.001 | 1.072 | 1.000 | 1.012 |
| `fused_h12_direct_m128_n16` | 4 | 1.000 | 1.020 | 0.998 | 1.008 |
| `fused_m64_independent_dvsplit_fp32_state` | 107 | 1.000 | 1.011 |
1.000 | 1.046 |

</details>

<details><summary>GB300 (sm_103a, 152 SMs): all rows, Triton versus
export (graph replay, cold-L2 CUPTI)</summary>

| Row | Shape | Schedule (export) | Bitwise | Triton µs | Export µs
(before) | Export µs (after) | Triton/Export |
|---:|---|---|---|---:|---:|---:|---:|
| 0 | `contract/h6_fixed_512` |
`fused_active_beta_checkpoint_dvsplit_m64` | yes | 66.6 | 41.3 | 39.1 |
1.70x |
| 1 | `contract/h6_fixed_8192` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
416.3 | 224.9 | 222.2 | 1.87x |
| 2 | `contract/h6_fixed_16384` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
859.9 | 347.7 | 346.5 | 2.48x |
| 3 | `contract/h6_packed_128x8` |
`fused_active_beta_checkpoint_dvsplit_m64` | yes | 67.8 | 17.9 | 16.9 |
4.02x |
| 4 | `contract/h6_packed_512x32` | `fused_checkpoint_direct_m128_n32` |
yes | 344.7 | 105.1 | 105.1 | 3.28x |
| 5 | `contract/h6_packed_1024x8` |
`fused_active_beta_checkpoint_dvsplit_m64` | yes | 193.8 | 75.2 | 71.1 |
2.73x |
| 6 | `contract/h6_packed_mixed_8192` |
`fused_active_beta_checkpoint_dvsplit_m64` | yes | 259.1 | 205.3 | 195.0
| 1.33x |
| 7 | `contract/h6_packed_4096x4` |
`fused_active_beta_checkpoint_dvsplit_m64` | yes | 446.6 | 269.6 | 255.7
| 1.75x |
| 8 | `contract/h6_fixed_63` |
`fused_active_beta_checkpoint_dvsplit_m64` | yes | 56.4 | 14.3 | 13.9 |
4.06x |
| 9 | `contract/h6_fixed_64` |
`fused_active_beta_checkpoint_dvsplit_m64` | yes | 58.0 | 12.2 | 11.5 |
5.04x |
| 10 | `contract/h6_fixed_65` |
`fused_active_beta_checkpoint_dvsplit_m64` | yes | 56.7 | 14.9 | 13.9 |
4.09x |
| 11 | `contract/h6_packed_17_33_65` |
`fused_active_beta_checkpoint_dvsplit_m64` | yes | 57.5 | 14.5 | 13.8 |
4.16x |
| 12 | `contract/h12_fixed_512` |
`fused_active_beta_checkpoint_dvsplit_m64` | yes | 68.6 | 41.3 | 39.1 |
1.75x |
| 13 | `contract/h12_fixed_8192` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
578.9 | 324.2 | 320.9 | 1.80x |
| 14 | `contract/h12_fixed_16384` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
1095.7 | 558.4 | 553.7 | 1.98x |
| 15 | `contract/h12_packed_128x8` |
`fused_checkpoint_direct_m128_page64_n32x2` | yes | 78.1 | 43.9 | 36.8 |
2.12x |
| 16 | `contract/h12_packed_512x32` | `fused_checkpoint_direct_m128_n32`
| yes | 620.1 | 150.8 | 150.1 | 4.13x |
| 17 | `contract/h12_packed_1024x8` | `fused_checkpoint_direct_m128_n32`
| yes | 341.7 | 91.1 | 91.3 | 3.74x |
| 18 | `contract/h12_packed_mixed_8192` |
`fused_active_beta_checkpoint_dvsplit_m64` | yes | 412.6 | 211.3 | 198.3
| 2.08x |
| 19 | `contract/h12_packed_4096x4` |
`fused_active_beta_checkpoint_dvsplit_m64` | yes | 686.9 | 272.4 | 257.9
| 2.66x |
| 20 | `contract/h12_fixed_63` |
`fused_active_beta_checkpoint_dvsplit_m64` | yes | 54.4 | 14.6 | 14.1 |
3.87x |
| 21 | `contract/h12_fixed_64` |
`fused_active_beta_checkpoint_dvsplit_m64` | yes | 56.3 | 12.3 | 11.5 |
4.90x |
| 22 | `contract/h12_fixed_65` |
`fused_active_beta_checkpoint_dvsplit_m64` | yes | 55.5 | 14.7 | 13.9 |
4.00x |
| 23 | `contract/h12_packed_17_33_65` |
`fused_active_beta_checkpoint_dvsplit_m64` | yes | 60.1 | 14.9 | 14.0 |
4.30x |
| 24 | `contract/h96_fixed_512` | `fused_checkpoint_direct_m128_n32` |
yes | 175.3 | 53.3 | 53.0 | 3.31x |
| 25 | `contract/h96_fixed_8192` | `fused_checkpoint_direct_m128_n32` |
yes | 2269.3 | 610.3 | 613.5 | 3.70x |
| 26 | `contract/h96_fixed_16384` | `fused_checkpoint_direct_m128_n32` |
yes | 4468.2 | 1205.8 | 1212.7 | 3.68x |
| 27 | `contract/h96_packed_128x8` | `fused_checkpoint_direct_m128_n32`
| yes | 362.8 | 121.5 | 118.1 | 3.07x |
| 28 | `contract/h96_packed_512x32` | `fused_checkpoint_direct_m128_n32`
| yes | 4519.1 | 1010.3 | 1004.7 | 4.50x |
| 29 | `contract/h96_packed_1024x8` | `fused_checkpoint_direct_m128_n32`
| yes | 2267.8 | 513.6 | 513.8 | 4.41x |
| 30 | `contract/h96_packed_mixed_8192` |
`fused_checkpoint_direct_m128_n32` | yes | 2295.3 | 442.5 | 441.1 |
5.20x |
| 31 | `contract/h96_packed_4096x4` | `fused_checkpoint_direct_m128_n32`
| yes | 4588.3 | 930.0 | 934.8 | 4.91x |
| 32 | `contract/h96_fixed_63` | `fused_checkpoint_direct_m128_n32` |
yes | 61.6 | 21.0 | 20.5 | 3.01x |
| 33 | `contract/h96_fixed_64` | `fused_checkpoint_direct_m128_n32` |
yes | 64.2 | 19.7 | 19.2 | 3.35x |
| 34 | `contract/h96_fixed_65` | `fused_checkpoint_direct_m128_n32` |
yes | 77.2 | 22.2 | 21.9 | 3.53x |
| 35 | `contract/h96_packed_17_33_65` |
`fused_checkpoint_direct_m128_n32` | yes | 100.0 | 37.2 | 35.9 | 2.78x |
| 36 | `contract/h6_fixed_32768` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
1681.8 | 571.1 | 569.8 | 2.95x |
| 37 | `contract/h6_fixed_65536` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
3281.1 | 1010.0 | 1007.2 | 3.26x |
| 38 | `contract/h6_packed_8192x4` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
819.0 | 584.8 | 582.5 | 1.41x |
| 39 | `contract/h6_packed_16384x2` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
1113.9 | 582.5 | 579.7 | 1.92x |
| 40 | `contract/h12_fixed_32768` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
2177.4 | 1004.2 | 1002.3 | 2.17x |
| 41 | `contract/h12_fixed_65536` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
4237.7 | 1911.6 | 1905.6 | 2.22x |
| 42 | `contract/h12_packed_8192x4` |
`fused_active_beta_checkpoint_dvsplit_m64` | yes | 1317.3 | 531.1 |
507.0 | 2.60x |
| 43 | `contract/h12_packed_16384x2` |
`split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | yes |
1613.2 | 1015.6 | 1012.2 | 1.59x |
| 44 | `contract/h96_fixed_32768` | `fused_checkpoint_direct_m128_n32` |
yes | 9101.4 | 2392.5 | 2411.8 | 3.77x |
| 45 | `contract/h96_fixed_65536` | `fused_checkpoint_direct_m128_n32` |
yes | 17684.7 | 4761.4 | 4793.3 | 3.69x |
| 46 | `contract/h96_packed_8192x4` | `fused_checkpoint_direct_m128_n32`
| yes | 8917.7 | 1820.8 | 1831.5 | 4.87x |
| 47 | `contract/h96_packed_16384x2` |
`fused_checkpoint_direct_m128_n32` | yes | 9121.0 | 2401.9 | 2414.6 |
3.78x |
| 48 | `contract/h12_short_t64_bs4` |
`fused_active_beta_checkpoint_dvsplit_m64` | yes | 56.4 | 12.8 | 12.1 |
4.67x |
| 49 | `contract/h12_short_t64_bs16` |
`fused_checkpoint_tma_direct_m128_n16` | yes | 79.9 | 32.6 | 32.3 |
2.47x |
| 50 | `contract/h12_short_t64_bs64` |
`fused_checkpoint_tma_direct_m128_n16` | yes | 193.5 | 91.5 | 90.8 |
2.13x |
| 51 | `contract/h12_short_t128_bs4` |
`fused_active_beta_checkpoint_dvsplit_m64` | yes | 67.4 | 23.7 | 23.0 |
2.93x |
| 52 | `contract/h12_short_t128_bs16` |
`fused_checkpoint_direct_m128_page64_n32x2` | yes | 110.6 | 86.3 | 71.9
| 1.54x |
| 53 | `contract/h12_short_t128_bs64` |
`fused_checkpoint_direct_m128_page64_n32x2` | yes | 349.3 | 253.2 |
208.4 | 1.68x |
| 54 | `contract/h12_short_t256_bs4` |
`fused_active_beta_checkpoint_dvsplit_m64` | yes | 78.6 | 26.5 | 24.8 |
3.17x |
| 55 | `contract/h12_short_t256_bs16` |
`fused_checkpoint_direct_m128_page64_n32x2` | yes | 177.3 | 145.7 |
121.2 | 1.46x |
| 56 | `contract/h12_short_t256_bs64` |
`fused_checkpoint_direct_m128_page64_n32x2` | yes | 622.0 | 436.5 |
361.8 | 1.72x |
| 57 | `contract/h12_short_varlen_17_64_65_127_128_255` |
`fused_active_beta_checkpoint_dvsplit_m64` | yes | 76.7 | 29.6 | 28.1 |
2.73x |
| 58 | `contract/h12_observed_gate_pad_26_28` |
`fused_active_beta_checkpoint_dvsplit_m64` | yes | 46.5 | 13.6 | 13.1 |
3.56x |
| 59 | `contract/h12_observed_gate_pad_68_80` |
`fused_active_beta_checkpoint_dvsplit_m64` | yes | 60.8 | 14.9 | 14.0 |
4.35x |
| 60 | `contract/h12_observed_gate_pad_502_512` |
`fused_active_beta_checkpoint_dvsplit_m64` | yes | 76.2 | 43.3 | 41.1 |
1.85x |
| 61 | `contract/h12_observed_gate_pad_1495_1536` |
`fused_active_beta_checkpoint_dvsplit_m64` | yes | 125.9 | 106.0 | 100.5
| 1.25x |
| 62 | `contract/h12_observed_gate_pad_2241_2241` |
`fused_active_beta_checkpoint_dvsplit_m64` | yes | 169.9 | 153.2 | 145.8
| 1.16x |
| 63 | `bounded/cp/1023:27` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 145.2 | 68.0 | 68.1 | 2.13x |
| 64 | `bounded/cp/1023:30` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 156.6 | 68.3 | 68.3 | 2.29x |
| 65 | `bounded/cp/1023:33` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 162.8 | 68.9 | 68.8 | 2.36x |
| 66 | `bounded/cp/1023:38` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 174.6 | 68.5 | 68.5 | 2.55x |
| 67 | `bounded/cp/1023:76` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 290.7 | 66.3 | 66.1 | 4.40x |
| 68 | `bounded/cp/1024+1024+1024+1024:6` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 140.3 | 65.5 | 65.5 |
2.14x |
| 69 | `bounded/cp/1024+1024:12` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 139.4 | 61.5 | 61.4 |
2.27x |
| 70 | `bounded/cp/1024+1024:15` |
`fused_m64_independent_dvsplit_fp32_state` | yes | 158.4 | 65.5 | 65.9 |
2.40x |
| 71 | `bounded/cp/1024:24` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 137.8 | 65.3 | 65.2 | 2.11x |
| 72 | `bounded/cp/1024:25` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 141.8 | 65.8 | 65.7 | 2.16x |
| 73 | `bounded/cp/1024:26` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 143.7 | 65.7 | 65.6 | 2.19x |
| 74 | `bounded/cp/1024:27` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 146.3 | 65.4 | 65.5 | 2.23x |
| 75 | `bounded/cp/1024:28` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 145.7 | 61.9 | 61.7 | 2.36x |
| 76 | `bounded/cp/1024:29` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 153.8 | 65.4 | 65.5 | 2.35x |
| 77 | `bounded/cp/1024:30` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 156.1 | 65.4 | 65.3 | 2.39x |
| 78 | `bounded/cp/1024:31` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 159.4 | 65.8 | 65.9 | 2.42x |
| 79 | `bounded/cp/1024:32` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 162.5 | 66.0 | 65.7 | 2.47x |
| 80 | `bounded/cp/1024:33` | `fused_m64_independent_dvsplit_fp32_state`
| yes | 162.9 | 65.7 | 65.9 | 2.47x |
| 81 | `bounded/cp/1024:34` | `fused_m64_independent_dvsplit_fp32_state`
| yes …

### [b549eff](https://github.com/flashinfer-ai/flashinfer/commit/b549effe17fa450624c315b8fe1748ac0388d00e)

- **作者**: Akaash Parthasarathy
- **时间**: 2026-09-21T20:01:00Z
- **提交信息**: refactor(moe_ep): move the SM100 vendor package under sm100 (#5371)

<!-- .github/pull_request_template.md -->

## 📌 Description

Move `flashinfer/moe_ep/kernel_src/cutedsl_megamoe` to
`flashinfer/moe_ep/kernel_src/sm100/cutedsl_megamoe`. This puts the
Blackwell
package under its architecture directory, as Hopper and SM120 already
are,
and keeps the move out of the upcoming Rubin PR.

Imports, packaging, lint exclusions and docs now use the new path. The
vendored kernels are unchanged.

## 🔍 Related Issues

Preparation for the Rubin MegaMoE work based on #4601.

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

The CPU test run passed 103 tests and skipped three that need a GPU.
`pre-commit run --all-files` passed. I also built a wheel, installed it
outside
the checkout and checked that the SM100 backends import from that
installation.

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

`tune.py` also aliases the SM90 `run_tuning` import to fix a mypy
redefinition
error exposed by the commit hook.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

- **Refactor**
- Relocated the SM100 CuTeDSL MegaMoE kernel package under an
architecture-specific path.
- Updated MegaMoE backends, tuning workflows, benchmarks, and packaged
resources to use the new location.
  - Preserved existing runtime behavior and tuning logic.

- **Documentation**
- Updated architecture guides, runbooks, README content, usage examples,
warnings, and provenance references to reflect the reorganized kernel
layout.

- **Tests**
- Updated integration, multirank, configuration, CUDA graph, workspace,
and reference tests to use the relocated kernel package.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [d7a7447](https://github.com/flashinfer-ai/flashinfer/commit/d7a7447cb4bb29b4637f7fa02fe5eaeeb5e61a6e)

- **作者**: alex.
- **时间**: 2026-09-21T18:55:25Z
- **提交信息**: feat(mla): uniform LSE base semantics via return_lse_base_on_e (#4650)

## 📌 Description

`return_lse_base_on_e` is a guarantee about the *units* of the returned
LSE, not a
transformation request: `True` yields base-e and `False` base-2
whichever backend ran,
while `None` preserves each backend's historical default. Before this PR
the parameter
was only honored by some paths, so the same flag could return different
units depending
on which kernel the dispatcher picked.

All three MLA backends compute LSE in base 2 internally, so the
parameter is realized as
a float multiplier applied **at the store site** rather than as a Python
post-scale. That
keeps the semantics uniform instead of having one backend scale in
Python and the others
in the kernel.

- **trtllm-gen** — `lseScale` on `TllmGenFmhaRunnerParams`, applied in
`lse.cuh` as
  `lse[out_idx] = lse_scale * (log2e * m + log2(d))`.
- **cute-dsl monolithic** — log scale plumbed through `mla_dispatch`
into both the fp16
  and fp8 decode kernels, which carry separate LSE stores.
- **sparse (SM120/SM121)** — threaded to the three user-facing stores:
the decode merge
kernel shared by both decode entries, plus the SG and MG prefill
epilogues.
`double` at the three TVM-FFI entries, `float` below, mirroring
`sm_scale`.

`None` keeps existing behavior per backend: base-2 for trtllm-gen and
sparse, base-e for
monolithic cute-dsl. The non-MLA trtllm-gen decode/prefill entry points
pass
`lse_scale = 1.0`; that ABI widening is signature-only, no behavior
change.

AI-assisted: analysis, debugging, and the tests were written with Claude
Code; the kernel
and plumbing changes are the author's.

Co-Authored-By: Claude Opus 5 (1M context) <noreply@anthropic.com>

## 🔍 Related Issues

Closes #4485

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

Two new suites, both gated on the hardware they need:

- `tests/attention/test_mla_lse_base.py` — 25 cases, green on **B200**
(trtllm-gen and
cute-dsl). Covers both `split_kv` branches of the monolithic kernel,
since the epilogue
and the reduction kernel each own a user-facing LSE store, and both bf16
and fp8, since
  `mla_decode_fp16.py` and `mla_decode_fp8.py` are near-duplicate files.
- `tests/attention/test_sparse_mla_sm120_lse_base.py` — 44 cases, green
on **8× RTX PRO
6000 Blackwell** (sparse). Pins one shape per kernel store, since SG and
MG prefill are
separate templates with their own epilogues, and additionally covers the
`attn_sink`
merge, per-token `topk_length`, caller-supplied `lse` buffers, and the
empty-row
  sentinel.

Both suites assert the *other* base is not returned, so a no-op wiring
can't pass on
tolerance alone, and assert `None`/`False` are bit-identical where the
backend's native
base is 2.

## Reviewer Notes

A few deliberate choices worth a look:

1. **The `-1e30f` empty-row sentinel is written unscaled** at every
sparse store
(`(x != -1e30f) ? lse_scale * x : x`). It marks a row with no candidates
rather than a
log-domain value, and callers compare against the literal, so scaling it
would
silently break that comparison. Happy to flip this if you'd rather it
scale — it's
   three call sites and one test assertion.
2. **The scale arithmetic is duplicated inline at the three sparse
stores** rather than
factored into a helper, so the multiply is visible at the point of the
store. Same
reasoning for the three `return_lse_base_on_e` → float derivations in
`_core.py`
(trtllm-gen, cute-dsl, sparse): they differ only in what `None` means,
and a shared
helper would need a `default_base_e` keyword plus a decision about
non-`bool` input
that the three sites currently answer differently. Easy to unify if you
prefer it.
3. `lse_scale` sits **immediately after the LSE output** in every
signature, C++ and
Python alike. TVM-FFI is positional, so this was chosen to make a
misordering a
   compile or type error rather than a silent swap with `sm_scale`.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **New Features**
- Added configurable log-sum-exp (LSE) output scaling across MLA
prefill, paged-attention, and decode operations.
- MLA decoding now supports selecting natural-log or base-2 LSE output
through the public API.
- Preserved backend-specific defaults when no LSE base preference is
specified.
- Added consistent LSE scaling across sparse MLA, TRT-LLM, and CuTeDSL
backends.

- **Tests**
- Added coverage for LSE base selection, numerical accuracy, backend
consistency, split-KV execution, and output buffers.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: mingyangw <mingyangw@nvidia.com>

### [1c0d553](https://github.com/flashinfer-ai/flashinfer/commit/1c0d5535708c2cd411d0d90e3eb3cfa0f0170092)

- **作者**: Ke Wen
- **时间**: 2026-09-21T18:34:35Z
- **提交信息**: feat(comm): add fused decode CP A2A + LSE reduce (#4929)

## 📌 Description

### Why this is needed

In context-parallel decode, the KV cache is sharded by sequence across
ranks. Each rank runs attention against
its local KV shard and produces, for every query token and head:

- `o_r`: a partial attention output
- `lse_r`: the log-sum-exp that records that shard's softmax
normalization

The `o_r` values cannot be summed directly: each was normalized over a
different KV shard. To reconstruct
full-context attention, the partial outputs must be exchanged and merged
with weights derived from all ranks'
LSEs:

`out = Σ_r softmax(lse)_r * o_r`

Each rank's input carries a `cp_size` axis containing the slices
destined for the CP ranks. The `heads` axis may
contain either local or total heads: this op treats every batch/head
entry independently and does not shard or
otherwise reinterpret the head axis.

### What this PR adds

Adds experimental `decode_cp_a2a_lse_reduce`, which fuses that
all-to-all exchange and LSE-weighted merge into one
cooperative CUDA kernel.

```python
decode_cp_a2a_lse_reduce(
    partial_o: torch.Tensor,
    partial_lse: torch.Tensor,
    workspace: torch.Tensor,
    cp_rank: int,
    cp_size: int,
    lse_mode: Literal["base2", "basee"] = "base2",
) -> torch.Tensor
```

Input and output shapes:

- `partial_o`: `[batch, heads, cp_size, head_dim]` (`float16` or
`bfloat16`)
- `partial_lse`: `[batch, heads, cp_size]` (`float32`)
- output: `[batch, heads, head_dim]`, with the same dtype as `partial_o`

More generally, arbitrary matching leading dimensions are supported:
`[..., cp_size, head_dim]` + `[..., cp_size]` → `[..., head_dim]`.

`lse_mode="base2"` accepts the base-2 LSE produced by FlashInfer MLA;
`lse_mode="basee"` accepts natural-log
LSE. The op does not expose `enable_pdl` because its NCCL device kernel
does not use programmatic dependent launch.

- Sends each peer's partial output and LSE together, then merges
received contributions in the same kernel.
- Uses NCCL device load/store-accessible (LSA) symmetric memory rather
than composing separate framework collectives.
- Supports eager execution and CUDA Graph replay with a collectively
created, rendezvoused workspace.
- Requires all CP ranks to be in one NCCL LSA/NVLink domain. A workspace
is single-stream; concurrent streams or
  graph-capture streams need separate workspaces.

This implements the NCCL-LSA scope of #4575.

## 🔍 Related Issues

- Implements the NCCL-LSA scope of #4575.
- Related design RFC:
https://github.com/NVIDIA/nccl-extensions/issues/10

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items
are complete.

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

Focused validation:

- ✅ Distributed DCP LSE-reduce test: `15 passed` per rank with 4
processes
- ✅ CPU-safe DCP API/reference tests: `12 passed`
- ✅ DCP trace signature, axes, and completeness checks: `3 passed`
- ✅ All configured pre-commit hooks on the modified PR files
- ✅ Python syntax compilation for modified Python sources
- ✅ `git diff --check`
- ✅ Four-process BF16 benchmark on four H100 80 GB GPUs in one
NVLink-connected LSA domain versus unfused legacy
A2A plus LSE merge (max-rank median; 10 warm-ups, 30 samples, 50
launches/sample):

| Shape | Fused eager | Fused + graph* | Legacy A2A + merge | Speedup |
|---|---:|---:|---:|---:|
| batch 1, heads 2, dim 64 | 12.14 µs | 10.15 µs | 178.91 µs | 14.7× |
| batch 1, heads 8, dim 128 | 15.04 µs | 13.24 µs | 179.22 µs | 11.9× |
| batch 4, heads 8, dim 128 | 18.04 µs | 16.40 µs | 178.73 µs | 9.9× |
| batch 16, heads 8, dim 128 | 18.96 µs | 17.02 µs | 180.88 µs | 9.5× |

* Fused + graph: groups 50 ops in one graph, reporting per-op average.

The largely flat legacy baseline shows that these decode-sized cases are
dominated by fixed launch/collective
overhead; the speedup primarily reflects eliminating that overhead
rather than a bandwidth improvement.

## Reviewer Notes

- This is the first FlashInfer op that directly uses NCCL device APIs.
The new public API, AOT registration,
trace template, documentation, tests, and benchmark are included in this
PR.
- The restricted LSA/NVLink scope and the
one-workspace-per-ordered-stream contract are intentional.

## Fused-kernel algorithm

For each token and attention head, every rank starts with a partial
attention output $O_r$ and log-sum-exp $L_r$
from its local KV shard. The cooperative kernel completes the exchange
and merge in one launch:

1. Block 0 advances a device-side epoch and selects one of two workspace
slots, allowing safe slot rotation during
   CUDA Graph replay.
2. Each source rank writes its destination-specific output and LSE
directly into the destination's NCCL
   symmetric-memory window using LSA/NVLink stores.
3. Sources publish system-scope release flags after their payloads are
visible. Each destination acquire-waits for
   every source, then the cooperative grid synchronizes.
4. One block processes each token/head row. It computes stable rank-axis
softmax weights:

$$
m = \max_r L_r, \qquad
w_r = \frac{\exp(L_r-m)}{\sum_j \exp(L_j-m)}.
$$

It then accumulates the combined output in FP32:

$$
O_{\mathrm{combined}}[d] = \sum_r w_r O_r[d].
$$

Base-2 LSE mode uses $2^{L_r-m}$. NaN and $+\infty$ LSEs are treated as
$-\infty$; if every shard is empty, the
output is zero. The result is converted back to FP16 or BF16.

This removes the separate NCCL all-to-all and reduction launches by
fusing peer transfer, readiness synchronization,
and the LSE-weighted merge. The implementation supports up to 64 ranks,
requires one NCCL LSA/NVLink domain, and
requires each workspace to stay on one ordered CUDA stream.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

- **New Features**
- Added an experimental context-parallel communication API that combines
all-to-all exchange with
    log-sum-exp-weighted attention-output reduction.
- Added workspace sizing and creation utilities for supported NCCL-based
distributed workloads.
- Supports natural-log and base-2 log-sum-exp calculations, including
robust handling of special values.
  - Added CUDA graph and tracing support for the new operation.

- **Documentation**
- Added API documentation covering the new communication functions and
workspace requirements.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Ke Wen <kwen@nvidia.com>

### [e0a1890](https://github.com/flashinfer-ai/flashinfer/commit/e0a18900ca81228b9b30c7963d8462d8b8ac20da)

- **作者**: Greg Fishman
- **时间**: 2026-09-21T18:21:35Z
- **提交信息**: fix(attention): materialize block_valid_mask for padded CUDA-graph prefill launches (#5176)

## 📌 Description

With CUDA graphs on and split-KV off, FA2 prefill can crash with
`illegal memory access`.

Under CUDA graphs the kernel launches more blocks than the batch needs.
The extra blocks must be masked off.
The mask was only created when split-KV was on.
Without it the extra blocks read plan entries that were never written.
If the workspace still holds an earlier plan, they read out of bounds.

Who hits it:
- SGLang with `--enable-deterministic-inference` (tensor-core decode
uses this planner).
- NVFP4 KV cache on Blackwell, where FlashInfer turns split-KV off
itself.

Reproduced on an RTX 6000 Ada with the calls SGLang makes (16 requests,
SGLang itself not run).
Fresh workspace: output happens to be correct.
Workspace reused from an earlier plan: crash.
With this PR both are correct.

Fix: create the mask whenever CUDA graphs are on.
Pass it to the kernel in every run function that uses the plan: ragged,
paged, POD, batch POD.
Cost: `padded_batch_size` bytes of int workspace.
Plans without CUDA graphs no longer allocate the unused mask.

## 🔍 Related Issues

- Fixes #4002.
- #4794 uses an exact grid when all requests have the same query length.
With it applied, the two new prefill tests still fail. The new decode
test no longer pads, so that case #4794 covers.
- sgl-project/sglang#36785 works around the same crash in SGLang.

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

| new test | main | with this PR |
| --- | --- | --- |
| `test_batch_prefill_cuda_graph_padding_without_split_kv[paged]` |
fails | passes |
| `test_batch_prefill_cuda_graph_padding_without_split_kv[ragged]` |
fails | passes |
| `test_tensor_core_decode_cuda_graph_padding_without_split_kv` | fails
| passes |

Same on RTX 4090 and RTX 3080.
A fourth new test checks that a padded no-split CUDA-graph plan fits the
buffers `workspace_size` reports.

On RTX 4090, the prefill, decode, POD and workspace-size test files give
the same per-test results with and without this PR.

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

The paged run moved to `csrc/batch_prefill_paged.cuh` in #4736. The fix
is applied there too.

Generated with Claude Code and Human In The Loop 🙈


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Fixed CUDA-graph execution for padded batch prefill and decode
workloads when KV splitting is disabled.
* Padding is now correctly identified and prevented from accessing stale
workspace data.
* Improved output consistency between CUDA-graph and non-graph execution
paths.

* **Tests**
* Added coverage for padded CUDA-graph batches using paged and ragged KV
caches.
* Strengthened validation of padding masks and workspace sizing in
unsplit execution scenarios.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: gf239 <gf239@users.noreply.github.com>
Co-authored-by: gf239 <gf239@users.noreply.github.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [6870e3f](https://github.com/flashinfer-ai/flashinfer/commit/6870e3fff46b1e768ad423ea48d286e6f3e250fe)

- **作者**: Matt Murphy
- **时间**: 2026-09-21T10:03:10Z
- **提交信息**: fix: guard K-tail loads in Blackwell gather GEMM (#5108)

<!-- .github/pull_request_template.md -->

## 📌 Description

Fix partial K-tile handling in the Blackwell block-scaled gather GEMM
used by FP4 MoE workloads. The activation and scale-factor copies
currently guard rows but can read past the logical K extent on the final
tile.

Add K bounds to both copy predicates. Include a synthetic regression in
`tests/moe/test_cute_dsl_fused_moe.py` that poisons scale-factor storage
beyond the logical input to detect tail reads without depending on
allocator placement.

## 🔍 Related Issues

No linked issue.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

Installed the hooks with `pre-commit install` and ran `pre-commit run
--all-files` successfully. All applicable hooks passed, including
clang-format, mypy, Ruff, and the experimental test-scope selftest; no
files were changed.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

Targeted validation on B300:
- Original kernel: eight partial-K cases fail; eight aligned-K controls
pass.
- Corrected kernel: all 16 cases pass.
- Compute Sanitizer memcheck with allocation caching disabled: all 16
cases pass with zero errors.

The synthetic matrix covers K=128/256/384/512, 1/17 input rows, and
one-/two-CTA tactics. The candidate wrapper and kernel were loaded into
an existing CUDA test environment for local validation; the full
upstream test suite was not run.

The regression test now lives in the existing fused MoE test module,
with all 16 parameter combinations preserved. Pre-commit hooks, syntax,
and diff checks passed after the move; the GPU test was not rerun
because the active Python environment has no `pytest`.

Reproduce in a source-enabled environment:
```bash
pytest tests/moe/test_cute_dsl_fused_moe.py::test_gather_gemm_k_tail -q
PYTORCH_NO_CUDA_MEMORY_CACHING=1 compute-sanitizer --tool memcheck \
  --padding 32 --error-exitcode 86 python -m pytest \
  tests/moe/test_cute_dsl_fused_moe.py::test_gather_gemm_k_tail -q
```

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

Please review the activation/scale K-coordinate bounds and the synthetic
tail-poisoning coverage. This is a correctness fix; no performance
improvement is claimed.

Keep this PR in draft pending author approval.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **Bug Fixes**
- Fixed fused MoE gather GEMM operations for inputs whose K dimension
does not evenly fill the final tile, preventing invalid reads during
processing.

- **Tests**
- Added coverage for K-tail handling across multiple K sizes, token
counts, and tile configurations on supported Blackwell GPUs.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [c6ec2cc](https://github.com/flashinfer-ai/flashinfer/commit/c6ec2cce64d70f28dce7d5d4c3ec6e4316965dcf)

- **作者**: eigen
- **时间**: 2026-09-21T08:54:56Z
- **提交信息**: perf(cake_kda): route one-wave BF16 grids to the M64 value split (#5363)

<!-- .github/pull_request_template.md -->

## 📌 Description

Follow-up to #5278. The BF16 KDA prefill export was slower than the
pinned
SGLang FLA Triton baseline on B200 for `short/H12/mixed` (0.935x) and
near
parity on three more packed rows, while the same rows ran 2-4x faster in
TF32. The export reproduced its source bit for bit; the source BF16
dispatcher
selected direct M128 tiles for those grids where its existing two-CTA
M64
value split is faster.

This PR updates the BF16 host dispatch in
`flashinfer/cake_kda_tf32_runtime.py`
(mirroring the source change) and adds the generated M64 modules that
the new
routes select:

- One-wave rule: BF16 compute, bounded gate, 32-token aligned checkpoint
  interval and `2 * tasks <= sm_count` (both M64 value CTAs of every
`(sequence, head)` task resident in one wave) replace a resolved direct
M128
route with the M64 value split. Forced tiles and TF32 are unchanged.
Logit
  beta whose token pitch is not TMA-encodable is refreshed into a padded
carrier every launch; short H12 grids (<= 256 tokens) that would need
that
copy keep their direct tile, because the H12 direct tiles load scalar
beta.
- Active FP32 beta (`beta_is_logit=False`) takes the native M64 path on
those
grids instead of the per-launch `logit` + BF16 copy, except where the
BF16
  affine split is eligible.
- Enabled on SM100a and SM103a.

### Measurement basis (source dispatcher, cold-L2 CUPTI)

Automatic route versus forced N16 / N32 / M64 / BT16 schedules on every
case (cold-L2 CUPTI, `bench_gpu_time`, 8 warmups / 48 samples):

| Sweep | Hardware | Cases | One-wave cases | M64 versus the automatic
tile inside one wave |
|---|---|---:|---:|---|
| Shape grid: H1/H6/H12/H24, 64-4096 tokens, uniform and mixed packed,
CP64/NoCP, logit and active beta | B200 (148 SM) | 369 | 290 | never
slower beyond 2% noise; median 1.25x |
| Short grid: 8-65 tokens, same axes | B200 | 120 | 120 | min 1.01x,
median 1.25x, max 5.71x |
| Shape grid | GB300 (152 SM) | 340 | 269 | never slower beyond 2%
except 3 affine-eligible grids, which stay on the affine split; median
1.31x |

Outside one wave the direct tiles win (B200 H12 96x128: N16 24.7 us
versus M64
34.3 us) and are retained. M64 output/state/checkpoint differ from the
direct
tiles by at most 2.7e-4 / 4.8e-3 / 5.9e-3 (BF16 tolerance 1e-2).


### Per-shape effect on the 346-row inventory

Source dispatcher, automatic BF16 route, same fixtures as the #5278
campaign.
B200: paired same-GPU old/new on every row whose route changes; 138 rows
change route with old/new min 1.04x, median 1.38x, max 2.70x (17
same-schedule
control rows: 0.995-1.029). GB300: all 346 rows old and new on one GPU;
143
rows change route with min 1.06x, median 1.32x, max 3.71x (unchanged
rows
0.955-1.085 single-pass noise). No row gets slower.

| Row | Shape | B200 old -> new us | GB300 old -> new us |
|---:|---|---|---|
| 341 | `short/H12/mixed` (Triton 71.3 / 66.4 us in #5278) | 63.6 ->
29.8 | 28.1 -> 27.8 (already M64) |
| 57 | `contract/h12_short_varlen_17_64_65_127_128_255` | 63.9 -> 30.3 |
28.0 -> 27.9 (already M64) |
| 122 | `bounded/cp/33+1025:12` | 113.6 -> 66.6 | 107.9 -> 63.5 |
| 6 | `contract/h6_packed_mixed_8192` | 272.7 -> 206.7 | 267.4 -> 195.0
|
| 342 | `export_holdout/H1/t64_b1_logits` | 40.1 -> 31.1 | 61.0 -> 47.5
|
| 343 | `export_holdout/H6/t64_b1_logits` | 39.8 -> 30.4 | 60.5 -> 46.5
|
| 344 | `export_holdout/H12/t64_b1_logits` | 17.0 (N16 kept) | 15.8 (N16
kept) |

<details><summary>B200: every changed row</summary>

| Row | Shape | Old schedule | New schedule | Old µs | New µs | Old/New
|
|---:|---|---|---|---:|---:|---:|
| 3 | H6 8x128 CP64 serving | `fused_checkpoint_direct_m128_n32` |
`fused_active_beta_checkpoint_dvsplit_m64` | 40.5 | 18.0 | 2.25x |
| 5 | H6 8x1024 CP64 serving | `fused_checkpoint_direct_m128_n32` |
`fused_active_beta_checkpoint_dvsplit_m64` | 111.3 | 76.2 | 1.46x |
| 6 | H6 1300+547+2048+963+271+3063 CP64 serving |
`fused_checkpoint_direct_m128_n32` |
`fused_active_beta_checkpoint_dvsplit_m64` | 272.2 | 206.8 | 1.32x |
| 7 | H6 4x4096 CP64 serving | `fused_checkpoint_direct_m128_n32` |
`fused_active_beta_checkpoint_dvsplit_m64` | 352.4 | 270.9 | 1.30x |
| 8 | H6 1x63 CP64 serving | `fused_checkpoint_direct_m128_n32` |
`fused_active_beta_checkpoint_dvsplit_m64` | 33.9 | 14.5 | 2.33x |
| 9 | H6 1x64 CP64 serving | `fused_checkpoint_direct_m128_n32` |
`fused_active_beta_checkpoint_dvsplit_m64` | 33.0 | 12.2 | 2.70x |
| 10 | H6 1x65 CP64 serving | `fused_checkpoint_direct_m128_n32` |
`fused_active_beta_checkpoint_dvsplit_m64` | 36.9 | 14.6 | 2.53x |
| 11 | H6 17+33+65 CP64 serving | `fused_checkpoint_direct_m128_n32` |
`fused_active_beta_checkpoint_dvsplit_m64` | 36.3 | 14.7 | 2.46x |
| 18 | H12 1300+547+2048+963+271+3063 CP64 serving |
`fused_checkpoint_tma_direct_m128_n16` |
`fused_active_beta_checkpoint_dvsplit_m64` | 357.2 | 212.7 | 1.68x |
| 19 | H12 4x4096 CP64 serving | `fused_checkpoint_tma_direct_m128_n16`
| `fused_active_beta_checkpoint_dvsplit_m64` | 458.4 | 273.7 | 1.67x |
| 20 | H12 1x63 CP64 serving | `fused_checkpoint_tma_direct_m128_n16` |
`fused_active_beta_checkpoint_dvsplit_m64` | 17.5 | 14.9 | 1.17x |
| 21 | H12 1x64 CP64 serving | `fused_checkpoint_tma_direct_m128_n16` |
`fused_active_beta_checkpoint_dvsplit_m64` | 17.0 | 12.2 | 1.40x |
| 22 | H12 1x65 CP64 serving |
`fused_checkpoint_direct_m128_page64_n32x2` |
`fused_active_beta_checkpoint_dvsplit_m64` | 37.3 | 14.7 | 2.55x |
| 23 | H12 17+33+65 CP64 serving |
`fused_checkpoint_direct_m128_page64_n32x2` |
`fused_active_beta_checkpoint_dvsplit_m64` | 37.0 | 15.0 | 2.47x |
| 42 | H12 4x8192 CP64 serving | `fused_checkpoint_tma_direct_m128_n16`
| `fused_active_beta_checkpoint_dvsplit_m64` | 864.3 | 537.9 | 1.61x |
| 48 | H12 4x64 CP64 serving | `fused_checkpoint_tma_direct_m128_n16` |
`fused_active_beta_checkpoint_dvsplit_m64` | 17.4 | 13.0 | 1.34x |
| 51 | H12 4x128 CP64 serving |
`fused_checkpoint_direct_m128_page64_n32x2` |
`fused_active_beta_checkpoint_dvsplit_m64` | 70.6 | 43.6 | 1.62x |
| 54 | H12 4x256 CP64 serving |
`fused_checkpoint_direct_m128_page64_n32x2` |
`fused_active_beta_checkpoint_dvsplit_m64` | 63.6 | 26.5 | 2.40x |
| 57 | H12 17+64+65+127+128+255 CP64 serving |
`fused_checkpoint_direct_m128_page64_n32x2` |
`fused_active_beta_checkpoint_dvsplit_m64` | 64.7 | 29.9 | 2.16x |
| 58 | H12 1x26 CP64 serving | `fused_checkpoint_tma_direct_m128_n16` |
`fused_active_beta_checkpoint_dvsplit_m64` | 14.4 | 13.9 | 1.04x |
| 59 | H12 1x68 CP64 serving |
`fused_checkpoint_direct_m128_page64_n32x2` |
`fused_active_beta_checkpoint_dvsplit_m64` | 37.6 | 14.8 | 2.53x |
| 60 | H12 1x502 CP64 serving | `fused_checkpoint_tma_direct_m128_n16` |
`fused_active_beta_checkpoint_dvsplit_m64` | 103.7 | 43.5 | 2.38x |
| 63 | H27 1x1023 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 117.3 | 87.5 |
1.34x |
| 64 | H30 1x1023 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 117.9 | 87.5 |
1.35x |
| 65 | H33 1x1023 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 117.9 | 87.8 |
1.34x |
| 66 | H38 1x1023 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 118.1 | 88.2 |
1.34x |
| 68 | H6 4x1024 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 116.5 | 84.8 |
1.37x |
| 69 | H12 2x1024 CP64 logits | `fused_checkpoint_tma_direct_m128_n16` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 112.1 | 64.7 |
1.73x |
| 70 | H15 2x1024 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 116.5 | 84.9 |
1.37x |
| 71 | H24 1x1024 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 116.9 | 84.8 |
1.38x |
| 72 | H25 1x1024 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 116.7 | 84.7 |
1.38x |
| 73 | H26 1x1024 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 116.8 | 84.6 |
1.38x |
| 74 | H27 1x1024 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 116.4 | 84.5 |
1.38x |
| 75 | H28 1x1024 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 91.8 | 65.3 |
1.41x |
| 76 | H29 1x1024 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 116.5 | 85.2 |
1.37x |
| 77 | H30 1x1024 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 116.9 | 85.1 |
1.37x |
| 78 | H31 1x1024 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 116.7 | 85.1 |
1.37x |
| 79 | H32 1x1024 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 117.0 | 85.1 |
1.37x |
| 80 | H33 1x1024 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 116.7 | 85.4 |
1.37x |
| 81 | H34 1x1024 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 116.5 | 85.2 |
1.37x |
| 82 | H35 1x1024 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 116.0 | 85.7 |
1.35x |
| 83 | H36 1x1024 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 92.2 | 65.9 |
1.40x |
| 84 | H37 1x1024 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 116.4 | 85.2 |
1.37x |
| 85 | H38 1x1024 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 117.0 | 86.3 |
1.36x |
| 86 | H39 1x1024 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 117.3 | 85.5 |
1.37x |
| 87 | H48 1x1024 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 117.4 | 86.5 |
1.36x |
| 88 | H54 1x1024 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 119.9 | 87.0 |
1.38x |
| 89 | H60 1x1024 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 92.9 | 67.5 |
1.38x |
| 90 | H61 1x1024 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 117.3 | 87.3 |
1.34x |
| 91 | H64 1x1024 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 117.9 | 87.4 |
1.35x |
| 95 | H24 1x1025 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 119.3 | 86.5 |
1.38x |
| 96 | H27 1x1025 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 120.2 | 86.5 |
1.39x |
| 100 | H36 1x1537 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 136.2 | 95.5 |
1.43x |
| 101 | H24 1x2048 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 197.3 | 140.8 |
1.40x |
| 102 | H27 1x2048 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 197.5 | 140.5 |
1.41x |
| 103 | H30 1x2048 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 198.1 | 141.2 |
1.40x |
| 104 | H31 1x2048 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 197.9 | 141.0 |
1.40x |
| 105 | H32 1x2048 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 197.9 | 141.4 |
1.40x |
| 106 | H33 1x2048 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 197.4 | 141.4 |
1.40x |
| 107 | H38 1x2048 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 197.7 | 142.1 |
1.39x |
| 108 | H48 1x2048 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 197.9 | 142.1 |
1.39x |
| 109 | H60 1x2048 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 174.2 | 123.6 |
1.41x |
| 121 | H18 32+512 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 75.8 | 57.0 |
1.33x |
| 122 | H12 33+1025 CP64 logits | `fused_checkpoint_tma_direct_m128_n16`
| `fused_source599_m64_independent_dvsplit_fp32_state` | 114.3 | 66.1 |
1.73x |
| 123 | H14 33+1025 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 119.8 | 86.4 |
1.39x |
| 124 | H20 33+1025 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 95.4 | 66.7 |
1.43x |
| 125 | H24 1x4096 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 358.3 | 252.1 |
1.42x |
| 126 | H27 1x4096 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 358.7 | 251.9 |
1.42x |
| 127 | H30 1x4096 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 359.1 | 253.2 |
1.42x |
| 128 | H31 1x4096 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 358.7 | 251.9 |
1.42x |
| 129 | H32 1x4096 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 359.0 | 252.9 |
1.42x |
| 130 | H33 1x4096 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 359.2 | 252.3 |
1.42x |
| 131 | H38 1x4096 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 359.8 | 253.1 |
1.42x |
| 132 | H48 1x4096 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 359.7 | 253.5 |
1.42x |
| 133 | H60 1x4096 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 335.0 | 236.1 |
1.42x |
| 134 | H23 1x511 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 77.4 | 60.0 |
1.29x |
| 135 | H30 1x511 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 76.9 | 59.9 |
1.28x |
| 136 | H48 1x511 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 77.6 | 61.4 |
1.26x |
| 137 | H12 4x512 CP64 logits | `fused_checkpoint_tma_direct_m128_n16` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 61.3 | 38.0 |
1.61x |
| 138 | H16 4x512 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 77.1 | 59.1 |
1.31x |
| 139 | H23 1x512 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 76.5 | 56.5 |
1.35x |
| 140 | H24 1x512 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 76.5 | 56.8 |
1.35x |
| 141 | H30 1x512 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 76.7 | 57.0 |
1.35x |
| 142 | H38 1x512 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 76.9 | 57.2 |
1.34x |
| 143 | H39 1x512 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 76.6 | 57.5 |
1.33x |
| 144 | H48 1x512 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 77.4 | 58.0 |
1.34x |
| 145 | H60 1x512 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 52.7 | 38.8 |
1.36x |
| 148 | H18 513+256 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 79.5 | 59.3 |
1.34x |
| 149 | H24 1x513 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 79.8 | 58.6 |
1.36x |
| 150 | H38 1x513 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 79.6 | 59.3 |
1.34x |
| 158 | H30 1x768 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 96.0 | 71.2 |
1.35x |
| 160 | H48 1x1024 NoCP logits | `fused_mr526_direct_m128` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 92.0 | 76.6 |
1.20x |
| 161 | H64 1x1024 NoCP logits | `fused_mr526_direct_m128` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 91.7 | 77.5 |
1.18x |
| 166 | H40 1x1025 NoCP logits | `fused_mr526_direct_m128` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 93.4 | 77.4 |
1.21x |
| 167 | H1 64x128 NoCP logits | `fused_mr526_direct_m128` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 43.7 | 35.3 |
1.24x |
| 171 | H1 16x128 NoCP logits | `fused_mr526_direct_m128` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 42.2 | 34.0 |
1.24x |
| 174 | H1 4x128 NoCP logits | `fused_mr526_direct_m128` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 42.3 | 34.1 |
1.24x |
| 175 | H12 4x128 NoCP logits | `fused_mr526_direct_m128` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 18.2 | 15.5 |
1.17x |
| 176 | H6 4x128 NoCP logits | `fused_mr526_direct_m128` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 42.9 | 34.1 |
1.26x |
| 181 | H32 1x2048 NoCP logits | `fused_mr526_direct_m128` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 144.8 | 120.8 |
1.20x |
| 186 | H12 4x255 NoCP logits | `fused_mr526_direct_m128` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 27.8 | 25.1 |
1.11x |
| 192 | H1 64x256 NoCP logits | `fused_mr526_direct_m128` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 54.4 | 41.5 |
1.31x |
| 202 | H1 16x256 NoCP logits | `fused_mr526_direct_m128` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 49.9 | 39.6 |
1.26x |
| 205 | H1 4x256 NoCP logits | `fused_mr526_direct_m128` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 50.2 | 39.3 |
1.28x |
| 206 | H11 4x256 NoCP logits | `fused_mr526_direct_m128` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 50.8 | 41.0 |
1.24x |
| 207 | H12 4x256 NoCP logits | `fused_mr526_direct_m128` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 26.5 | 21.3 |
1.25x |
| 208 | H13 4x256 NoCP logits | `fused_mr526_direct_m128` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 51.0 | 41.2 |
1.24x |
| 209 | H6 4x256 NoCP logits | `fused_mr526_direct_m128` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 49.9 | 39.6 |
1.26x |
| 210 | H12 4x257 NoCP logits | `fused_h12_direct_m128_n16` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 31.6 | 23.2 |
1.36x |
| 211 | H12 33+1025 NoCP logits | `fused_h12_direct_m128_n16` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 91.3 | 56.1 |
1.63x |
| 215 | H32 1x512 NoCP logits | `fused_mr526_direct_m128` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 64.3 | 51.3 |
1.25x |
| 216 | H48 1x512 NoCP logits | `fused_mr526_direct_m128` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 64.9 | 52.6 |
1.23x |
| 217 | H64 1x512 NoCP logits | `fused_mr526_direct_m128` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 65.6 | 53.7 |
1.22x |
| 221 | H1 64x64 NoCP logits | `fused_mr526_direct_m128` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 39.5 | 31.4 |
1.26x |
| 224 | H1 16x64 NoCP logits | `fused_mr526_direct_m128` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 38.2 | 30.6 |
1.25x |
| 228 | H1 4x64 NoCP logits | `fused_mr526_direct_m128` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 38.9 | 30.4 |
1.28x |
| 229 | H12 4x64 NoCP logits | `fused_h12_direct_m128_n16` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 15.6 | 11.5 |
1.36x |
| 230 | H6 4x64 NoCP logits | `fused_mr526_direct_m128` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 39.5 | 30.8 |
1.28x |
| 312 | H1 4x64 CP64 serving | `fused_checkpoint_direct_m128_n32` |
`fused_active_beta_checkpoint_dvsplit_m64` | 33.2 | 12.5 | 2.66x |
| 313 | H1 16x64 CP64 serving | `fused_checkpoint_direct_m128_n32` |
`fused_active_beta_checkpoint_dvsplit_m64` | 33.4 | 12.5 | 2.67x |
| 314 | H1 64x64 CP64 serving | `fused_checkpoint_direct_m128_n32` |
`fused_active_beta_checkpoint_dvsplit_m64` | 33.6 | 13.8 | 2.43x |
| 315 | H1 4x128 CP64 serving | `fused_checkpoint_direct_m128_n32` |
`fused_active_beta_checkpoint_dvsplit_m64` | 38.9 | 17.0 | 2.29x |
| 316 | H1 16x128 CP64 serving | `fused_checkpoint_direct_m128_n32` |
`fused_active_beta_checkpoint_dvsplit_m64` | 38.9 | 17.2 | 2.26x |
| 317 | H1 64x128 CP64 serving | `fused_checkpoint_direct_m128_n32` |
`fused_active_beta_checkpoint_dvsplit_m64` | 40.0 | 18.8 | 2.13x |
| 318 | H1 4x256 CP64 serving | `fused_checkpoint_direct_m128_n32` |
`fused_active_beta_checkpoint_dvsplit_m64` | 48.7 | 25.2 | 1.93x |
| 319 | H1 16x256 CP64 serving | `fused_checkpoint_direct_m128_n32` |
`fused_active_beta_checkpoint_dvsplit_m64` | 49.2 | 25.3 | 1.94x |
| 320 | H1 64x256 CP64 serving | `fused_checkpoint_direct_m128_n32` |
`fused_active_beta_checkpoint_dvsplit_m64` | 50.4 | 27.4 | 1.84x |
| 321 | H1 17+64+65+127+128+255 CP64 serving |
`fused_checkpoint_direct_m128_n32` |
`fused_active_beta_checkpoint_dvsplit_m64` | 48.9 | 28.0 | 1.74x |
| 322 | H6 4x64 CP64 serving | `fused_checkpoint_direct_m128_n32` |
`fused_active_beta_checkpoint_dvsplit_m64` | 32.9 | 12.4 | 2.65x |
| 325 | H6 4x128 CP64 serving | `fused_checkpoint_direct_m128_n32` |
`fused_active_beta_checkpoint_dvsplit_m64` | 38.6 | 17.3 | 2.23x |
| 328 | H6 4x256 CP64 serving | `fused_checkpoint_direct_m128_n32` |
`fused_active_beta_checkpoint_dvsplit_m64` | 49.9 | 25.6 | 1.95x |
| 331 | H6 17+64+65+127+128+255 CP64 serving |
`fused_checkpoint_direct_m128_n32` |
`fused_active_beta_checkpoint_dvsplit_m64` | 49.2 | 28.9 | 1.70x |
| 332 | H12 4x64 CP64 serving | `fused_checkpoint_tma_direct_m128_n16` |
`fused_active_beta_checkpoint_dvsplit_m64` | 17.2 | 13.0 | 1.32x |
| 335 | H12 4x128 CP64 serving |
`fused_checkpoint_direct_m128_page64_n32x2` |
`fused_active_beta_checkpoint_dvsplit_m64` | 36.9 | 18.0 | 2.05x |
| 338 | H12 4x256 CP64 serving |
`fused_checkpoint_direct_m128_page64_n32x2` |
`fused_active_beta_checkpoint_dvsplit_m64` | 63.0 | 26.5 | 2.38x |
| 341 | H12 17+64+65+127+128+255 CP64 serving |
`fused_checkpoint_direct_m128_page64_n32x2` |
`fused_active_beta_checkpoint_dvsplit_m64` | 64.0 | 30.2 | 2.12x |
| 342 | H1 1x64 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 40.2 | 31.1 |
1.30x |
| 343 | H6 1x64 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 39.8 | 30.8 |
1.29x |

</details>

<details><summary>GB300: every changed row</summary>

| Row | Shape | Old schedule | New schedule | Old µs | New µs | Old/New
|
|---:|---|---|---|---:|---:|---:|
| 3 | H6 8x128 CP64 serving | `fused_checkpoint_direct_m128_n32` |
`fused_active_beta_checkpoint_dvsplit_m64` | 48.5 | 16.8 | 2.88x |
| 5 | H6 8x1024 CP64 serving | `fused_checkpoint_direct_m128_n32` |
`fused_active_beta_checkpoint_dvsplit_m64` | 115.0 | 71.2 | 1.61x |
| 6 | H6 1300+547+2048+963+271+3063 CP64 serving |
`fused_checkpoint_direct_m128_n32` |
`fused_active_beta_checkpoint_dvsplit_m64` | 267.4 | 195.0 | 1.37x |
| 7 | H6 4x4096 CP64 serving | `fused_checkpoint_direct_m128_n32` |
`fused_active_beta_checkpoint_dvsplit_m64` | 342.5 | 255.9 | 1.34x |
| 8 | H6 1x63 CP64 serving | `fused_checkpoint_direct_m128_n32` |
`fused_active_beta_checkpoint_dvsplit_m64` | 43.0 | 13.6 | 3.15x |
| 9 | H6 1x64 CP64 serving | `fused_checkpoint_direct_m128_n32` |
`fused_active_beta_checkpoint_dvsplit_m64` | 41.9 | 11.3 | 3.71x |
| 10 | H6 1x65 CP64 serving | `fused_checkpoint_direct_m128_n32` |
`fused_active_beta_checkpoint_dvsplit_m64` | 45.1 | 13.5 | 3.35x |
| 11 | H6 17+33+65 CP64 serving | `fused_checkpoint_direct_m128_n32` |
`fused_active_beta_checkpoint_dvsplit_m64` | 44.9 | 13.6 | 3.31x |
| 18 | H12 1300+547+2048+963+271+3063 CP64 serving |
`fused_checkpoint_tma_direct_m128_n16` |
`fused_active_beta_checkpoint_dvsplit_m64` | 380.2 | 198.8 | 1.91x |
| 19 | H12 4x4096 CP64 serving | `fused_checkpoint_tma_direct_m128_n16`
| `fused_active_beta_checkpoint_dvsplit_m64` | 478.5 | 257.5 | 1.86x |
| 20 | H12 1x63 CP64 serving | `fused_checkpoint_tma_direct_m128_n16` |
`fused_active_beta_checkpoint_dvsplit_m64` | 16.6 | 13.8 | 1.20x |
| 21 | H12 1x64 CP64 serving | `fused_checkpoint_tma_direct_m128_n16` |
`fused_active_beta_checkpoint_dvsplit_m64` | 16.2 | 11.3 | 1.44x |
| 22 | H12 1x65 CP64 serving |
`fused_checkpoint_direct_m128_page64_n32x2` |
`fused_active_beta_checkpoint_dvsplit_m64` | 35.1 | 13.7 | 2.57x |
| 23 | H12 17+33+65 CP64 serving |
`fused_checkpoint_direct_m128_page64_n32x2` |
`fused_active_beta_checkpoint_dvsplit_m64` | 35.0 | 13.9 | 2.52x |
| 42 | H12 4x8192 CP64 serving | `fused_checkpoint_tma_direct_m128_n16`
| `fused_active_beta_checkpoint_dvsplit_m64` | 861.7 | 506.9 | 1.70x |
| 48 | H12 4x64 CP64 serving | `fused_checkpoint_tma_direct_m128_n16` |
`fused_active_beta_checkpoint_dvsplit_m64` | 16.5 | 12.0 | 1.37x |
| 51 | H12 4x128 CP64 serving |
`fused_checkpoint_direct_m128_page64_n32x2` |
`fused_active_beta_checkpoint_dvsplit_m64` | 94.3 | 63.9 | 1.48x |
| 58 | H12 1x26 CP64 serving | `fused_checkpoint_tma_direct_m128_n16` |
`fused_active_beta_checkpoint_dvsplit_m64` | 13.8 | 13.0 | 1.06x |
| 59 | H12 1x68 CP64 serving |
`fused_checkpoint_direct_m128_page64_n32x2` |
`fused_active_beta_checkpoint_dvsplit_m64` | 35.8 | 14.0 | 2.56x |
| 60 | H12 1x502 CP64 serving | `fused_checkpoint_tma_direct_m128_n16` |
`fused_active_beta_checkpoint_dvsplit_m64` | 137.9 | 41.1 | 3.35x |
| 63 | H27 1x1023 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 134.1 | 102.2 |
1.31x |
| 64 | H30 1x1023 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 131.7 | 104.0 |
1.27x |
| 65 | H33 1x1023 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 131.1 | 102.8 |
1.27x |
| 66 | H38 1x1023 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 131.3 | 101.6 |
1.29x |
| 67 | H76 1x1023 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 87.4 | 66.3 |
1.32x |
| 68 | H6 4x1024 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 130.8 | 98.7 |
1.33x |
| 69 | H12 2x1024 CP64 logits | `fused_checkpoint_tma_direct_m128_n16` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 105.5 | 61.5 |
1.72x |
| 70 | H15 2x1024 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 131.7 | 99.0 |
1.33x |
| 71 | H24 1x1024 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 131.6 | 99.3 |
1.33x |
| 72 | H25 1x1024 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 129.9 | 100.9 |
1.29x |
| 73 | H26 1x1024 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 130.3 | 100.3 |
1.30x |
| 74 | H27 1x1024 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 132.3 | 101.9 |
1.30x |
| 75 | H28 1x1024 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 85.4 | 61.5 |
1.39x |
| 76 | H29 1x1024 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 131.2 | 100.8 |
1.30x |
| 77 | H30 1x1024 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 131.0 | 98.8 |
1.33x |
| 78 | H31 1x1024 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 131.8 | 99.6 |
1.32x |
| 79 | H32 1x1024 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 131.7 | 100.1 |
1.32x |
| 80 | H33 1x1024 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 131.1 | 100.5 |
1.30x |
| 81 | H34 1x1024 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 131.7 | 101.0 |
1.30x |
| 82 | H35 1x1024 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 130.8 | 101.0 |
1.30x |
| 83 | H36 1x1024 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 85.4 | 61.7 |
1.38x |
| 84 | H37 1x1024 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 131.1 | 100.6 |
1.30x |
| 85 | H38 1x1024 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 130.5 | 102.0 |
1.28x |
| 86 | H39 1x1024 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 130.5 | 101.2 |
1.29x |
| 87 | H48 1x1024 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 131.0 | 102.0 |
1.28x |
| 88 | H54 1x1024 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 131.1 | 101.8 |
1.29x |
| 89 | H60 1x1024 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 86.3 | 62.9 |
1.37x |
| 90 | H61 1x1024 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 132.5 | 101.0 |
1.31x |
| 91 | H64 1x1024 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 130.6 | 101.1 |
1.29x |
| 92 | H76 1x1024 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 86.6 | 64.2 |
1.35x |
| 95 | H24 1x1025 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 134.2 | 102.7 |
1.31x |
| 96 | H27 1x1025 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 132.8 | 102.3 |
1.30x |
| 100 | H36 1x1537 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 125.5 | 90.5 |
1.39x |
| 101 | H24 1x2048 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 207.3 | 155.3 |
1.33x |
| 102 | H27 1x2048 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 207.5 | 154.3 |
1.34x |
| 103 | H30 1x2048 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 206.5 | 156.0 |
1.32x |
| 104 | H31 1x2048 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 206.6 | 153.7 |
1.34x |
| 105 | H32 1x2048 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 205.6 | 155.3 |
1.32x |
| 106 | H33 1x2048 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 207.0 | 155.0 |
1.34x |
| 107 | H38 1x2048 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 205.8 | 155.0 |
1.33x |
| 108 | H48 1x2048 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 206.7 | 155.3 |
1.33x |
| 109 | H60 1x2048 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 160.8 | 116.0 |
1.39x |
| 110 | H76 1x2048 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 161.5 | 117.5 |
1.37x |
| 121 | H18 32+512 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 94.4 | 74.3 |
1.27x |
| 122 | H12 33+1025 CP64 logits | `fused_checkpoint_tma_direct_m128_n16`
| `fused_source599_m64_independent_dvsplit_fp32_state` | 107.9 | 63.5 |
1.70x |
| 123 | H14 33+1025 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 134.7 | 102.0 |
1.32x |
| 124 | H20 33+1025 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 88.8 | 63.4 |
1.40x |
| 125 | H24 1x4096 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 356.1 | 260.2 |
1.37x |
| 126 | H27 1x4096 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 354.5 | 260.6 |
1.36x |
| 127 | H30 1x4096 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 355.0 | 261.6 |
1.36x |
| 128 | H31 1x4096 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 356.1 | 259.6 |
1.37x |
| 129 | H32 1x4096 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 356.0 | 258.9 |
1.37x |
| 130 | H33 1x4096 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 356.1 | 259.5 |
1.37x |
| 131 | H38 1x4096 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 356.0 | 259.9 |
1.37x |
| 132 | H48 1x4096 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 358.4 | 260.8 |
1.37x |
| 133 | H60 1x4096 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 309.6 | 222.0 |
1.39x |
| 134 | H23 1x511 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 94.6 | 75.5 |
1.25x |
| 135 | H30 1x511 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 93.7 | 76.3 |
1.23x |
| 136 | H48 1x511 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 94.6 | 75.9 |
1.25x |
| 137 | H12 4x512 CP64 logits | `fused_checkpoint_tma_direct_m128_n16` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 58.1 | 35.6 |
1.63x |
| 138 | H16 4x512 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 94.5 | 74.6 |
1.27x |
| 139 | H23 1x512 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 95.0 | 72.4 |
1.31x |
| 140 | H24 1x512 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 93.8 | 73.6 |
1.28x |
| 141 | H30 1x512 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 95.3 | 72.3 |
1.32x |
| 142 | H38 1x512 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 94.6 | 73.9 |
1.28x |
| 143 | H39 1x512 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 94.5 | 72.7 |
1.30x |
| 144 | H48 1x512 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 95.1 | 73.3 |
1.30x |
| 145 | H60 1x512 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 48.8 | 36.3 |
1.34x |
| 146 | H76 1x512 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 49.0 | 37.5 |
1.31x |
| 148 | H18 513+256 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 98.1 | 75.2 |
1.30x |
| 149 | H24 1x513 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 95.1 | 75.4 |
1.26x |
| 150 | H38 1x513 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 96.0 | 75.4 |
1.27x |
| 151 | H76 1x513 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 51.8 | 39.0 |
1.33x |
| 158 | H30 1x768 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 127.2 | 87.4 |
1.46x |
| 159 | H76 1x1023 NoCP logits | `fused_prediction_first_direct_m128` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 64.5 | 56.9 |
1.13x |
| 160 | H48 1x1024 NoCP logits | `fused_prediction_first_direct_m128` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 115.4 | 90.9 |
1.27x |
| 161 | H64 1x1024 NoCP logits | `fused_prediction_first_direct_m128` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 113.1 | 91.1 |
1.24x |
| 162 | H75 1x1024 NoCP logits | `fused_prediction_first_direct_m128` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 114.2 | 91.6 |
1.25x |
| 163 | H76 1x1024 NoCP logits | `fused_prediction_first_direct_m128` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 63.0 | 53.0 |
1.19x |
| 166 | H40 1x1025 NoCP logits | `fused_prediction_first_direct_m128` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 109.8 | 92.6 |
1.19x |
| 167 | H1 64x128 NoCP logits | `fused_mr526_direct_m128` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 64.1 | 52.8 |
1.21x |
| 171 | H1 16x128 NoCP logits | `fused_mr526_direct_m128` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 63.0 | 51.6 |
1.22x |
| 174 | H1 4x128 NoCP logits | `fused_mr526_direct_m128` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 63.0 | 52.0 |
1.21x |
| 175 | H12 4x128 NoCP logits | `fused_mr526_direct_m128` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 16.9 | 14.5 |
1.17x |
| 176 | H6 4x128 NoCP logits | `fused_mr526_direct_m128` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 62.7 | 52.5 |
1.19x |
| 181 | H32 1x2048 NoCP logits | `fused_prediction_first_direct_m128` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 158.9 | 131.9 |
1.20x |
| 186 | H12 4x255 NoCP logits | `fused_mr526_direct_m128` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 26.2 | 23.9 |
1.10x |
| 192 | H1 64x256 NoCP logits | `fused_mr526_direct_m128` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 69.4 | 60.4 |
1.15x |
| 202 | H1 16x256 NoCP logits | `fused_mr526_direct_m128` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 67.6 | 57.4 |
1.18x |
| 205 | H1 4x256 NoCP logits | `fused_mr526_direct_m128` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 69.5 | 56.8 |
1.23x |
| 206 | H11 4x256 NoCP logits | `fused_mr526_direct_m128` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 70.0 | 58.7 |
1.19x |
| 207 | H12 4x256 NoCP logits | `fused_mr526_direct_m128` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 24.8 | 19.9 |
1.25x |
| 208 | H13 4x256 NoCP logits | `fused_mr526_direct_m128` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 71.4 | 58.4 |
1.22x |
| 209 | H6 4x256 NoCP logits | `fused_mr526_direct_m128` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 68.3 | 57.3 |
1.19x |
| 210 | H12 4x257 NoCP logits | `fused_h12_direct_m128_n16` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 29.6 | 21.6 |
1.37x |
| 211 | H12 33+1025 NoCP logits | `fused_h12_direct_m128_n16` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 86.0 | 52.3 |
1.64x |
| 215 | H32 1x512 NoCP logits | `fused_prediction_first_direct_m128` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 82.6 | 67.7 |
1.22x |
| 216 | H48 1x512 NoCP logits | `fused_prediction_first_direct_m128` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 83.5 | 68.6 |
1.22x |
| 217 | H64 1x512 NoCP logits | `fused_prediction_first_direct_m128` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 83.9 | 69.6 |
1.21x |
| 218 | H76 1x512 NoCP logits | `fused_prediction_first_direct_m128` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 37.6 | 31.8 |
1.18x |
| 221 | H1 64x64 NoCP logits | `fused_mr526_direct_m128` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 80.5 | 48.1 |
1.67x |
| 224 | H1 16x64 NoCP logits | `fused_mr526_direct_m128` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 66.5 | 50.5 |
1.32x |
| 228 | H1 4x64 NoCP logits | `fused_mr526_direct_m128` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 62.0 | 48.0 |
1.29x |
| 229 | H12 4x64 NoCP logits | `fused_h12_direct_m128_n16` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 14.5 | 11.1 |
1.31x |
| 230 | H6 4x64 NoCP logits | `fused_mr526_direct_m128` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 60.3 | 48.0 |
1.26x |
| 312 | H1 4x64 CP64 serving | `fused_checkpoint_direct_m128_n32` |
`fused_active_beta_checkpoint_dvsplit_m64` | 41.9 | 11.4 | 3.68x |
| 313 | H1 16x64 CP64 serving | `fused_checkpoint_direct_m128_n32` |
`fused_active_beta_checkpoint_dvsplit_m64` | 42.6 | 11.5 | 3.70x |
| 314 | H1 64x64 CP64 serving | `fused_checkpoint_direct_m128_n32` |
`fused_active_beta_checkpoint_dvsplit_m64` | 43.8 | 12.7 | 3.45x |
| 315 | H1 4x128 CP64 serving | `fused_checkpoint_direct_m128_n32` |
`fused_active_beta_checkpoint_dvsplit_m64` | 46.3 | 15.7 | 2.95x |
| 316 | H1 16x128 CP64 serving | `fused_checkpoint_direct_m128_n32` |
`fused_active_beta_checkpoint_dvsplit_m64` | 46.3 | 16.0 | 2.90x |
| 317 | H1 64x128 CP64 serving | `fused_checkpoint_direct_m128_n32` |
`fused_active_beta_checkpoint_dvsplit_m64` | 48.0 | 17.4 | 2.76x |
| 318 | H1 4x256 CP64 serving | `fused_checkpoint_direct_m128_n32` |
`fused_active_beta_checkpoint_dvsplit_m64` | 55.8 | 23.5 | 2.37x |
| 319 | H1 16x256 CP64 serving | `fused_checkpoint_direct_m128_n32` |
`fused_active_beta_checkpoint_dvsplit_m64` | 55.3 | 23.9 | 2.31x |
| 320 | H1 64x256 CP64 serving | `fused_checkpoint_direct_m128_n32` |
`fused_active_beta_checkpoint_dvsplit_m64` | 56.5 | 25.6 | 2.20x |
| 321 | H1 17+64+65+127+128+255 CP64 serving |
`fused_checkpoint_direct_m128_n32` |
`fused_active_beta_checkpoint_dvsplit_m64` | 55.6 | 25.9 | 2.15x |
| 322 | H6 4x64 CP64 serving | `fused_checkpoint_direct_m128_n32` |
`fused_active_beta_checkpoint_dvsplit_m64` | 41.1 | 11.7 | 3.51x |
| 325 | H6 4x128 CP64 serving | `fused_checkpoint_direct_m128_n32` |
`fused_active_beta_checkpoint_dvsplit_m64` | 46.5 | 16.2 | 2.88x |
| 328 | H6 4x256 CP64 serving | `fused_checkpoint_direct_m128_n32` |
`fused_active_beta_checkpoint_dvsplit_m64` | 57.1 | 23.8 | 2.39x |
| 331 | H6 17+64+65+127+128+255 CP64 serving |
`fused_checkpoint_direct_m128_n32` |
`fused_active_beta_checkpoint_dvsplit_m64` | 57.2 | 27.2 | 2.11x |
| 332 | H12 4x64 CP64 serving | `fused_checkpoint_tma_direct_m128_n16` |
`fused_active_beta_checkpoint_dvsplit_m64` | 16.2 | 11.9 | 1.36x |
| 335 | H12 4x128 CP64 serving |
`fused_checkpoint_direct_m128_page64_n32x2` |
`fused_active_beta_checkpoint_dvsplit_m64` | 35.4 | 16.9 | 2.09x |
| 342 | H1 1x64 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 61.8 | 47.5 |
1.30x |
| 343 | H6 1x64 CP64 logits | `fused_checkpoint_direct_m128_n32` |
`fused_source599_m64_independent_dvsplit_fp32_state` | 63.0 | 46.5 |
1.35x |

</details>


### Export parity

Source dispatcher versus the exported FlashInfer API on every one of the
346
inventory rows, in one process per row: same fixtures, same reset,
identical
selected schedule required, bitwise comparison of output, final state
and
checkpoints, then both prepared calls captured into caller-owned CUDA
graphs
and replayed under cold-L2 CUPTI (three alternating groups, median).
Graph
replay removes host launch overhead, so these ratios compare device time
only
(the per-row tables above use direct uncaptured calls).

**B200 (sm_100a, 148 SMs)**: 346 rows, 0 errors; schedule parity
346/346; bitwise output/state/checkpoint parity 346/346.
Export/source graph-replay latency: min 0.980, median 1.002, max 1.182.
Rows served by the module generated in this PR: 98 (ratio min 0.986,
median 1.000, max 1.049); rows served by modules kept from #5278: 248
(min 0.980, median 1.005, max 1.182; 84 above 1.03).

<details><summary>B200 (sm_100a, 148 SMs): export/source ratio per
exported module</summary>

| Schedule (export) | Module origin | Rows | min | median | max |
|---|---|---:|---:|---:|---:|
| `fused_checkpoint_direct_m128_page64_n32x2` | kept from #5278 | 9 |
1.168 | 1.179 | 1.182 |
| `fused_active_beta_checkpoint_dvsplit_m64` | kept from #5278 | 44 |
1.015 | 1.065 | 1.102 |
| `fused_unbounded_softplus_direct_m128` | kept from #5278 | 8 | 1.014 |
1.041 | 1.056 |
| `fused_direct_m128` | kept from #5278 | 39 | 1.001 | 1.018 | 1.109 |
| `split_seq_affine_prefix_direct_m128_fp32_state` | kept from #5278 |
24 | 0.992 | 1.004 | 1.018 |
| `fused_checkpoint_direct_m128_n32` | kept from #5278 | 49 | 0.980 |
1.001 | 1.115 |
| `fused_m64_independent_dvsplit_fp32_state` | generated in this PR | 98
| 0.986 | 1.000 | 1.049 |
| `fused_h12_direct_m128_n16` | kept from #5278 | 4 | 0.995 | 0.999 |
1.004 |
| `split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | kept
from #5278 | 63 | 0.991 | 0.999 | 1.040 |
| `fused_checkpoint_tma_direct_m128_n16` | kept from #5278 | 8 | 0.985 |
0.995 | 1.007 |

</details>

**GB300 (sm_103a, 152 SMs)**: 346 rows, 0 errors; schedule parity
346/346; bitwise output/state/checkpoint parity 346/346.
Export/source graph-replay latency: min 0.966, median 1.005, max 1.222.
Rows served by the module generated in this PR: 107 (ratio min 0.983,
median 1.000, max 1.011); rows served by modules kept from #5278: 239
(min 0.966, median 1.017, max 1.222; 94 above 1.03).

<details><summary>GB300 (sm_103a, 152 SMs): export/source ratio per
exported module</summary>

| Schedule (export) | Module origin | Rows | min | median | max |
|---|---|---:|---:|---:|---:|
| `fused_checkpoint_direct_m128_page64_n32x2` | kept from #5278 | 9 |
1.197 | 1.211 | 1.222 |
| `fused_unbounded_softplus_direct_m128` | kept from #5278 | 8 | 1.070 |
1.086 | 1.116 |
| `fused_active_beta_checkpoint_dvsplit_m64` | kept from #5278 | 44 |
1.034 | 1.057 | 1.097 |
| `fused_direct_m128` | kept from #5278 | 31 | 1.016 | 1.034 | 1.127 |
| `fused_prediction_first_direct_m128` | kept from #5278 | 4 | 1.017 |
1.017 | 1.018 |
| `fused_checkpoint_direct_m128_n32` | kept from #5278 | 44 | 0.993 |
1.013 | 1.120 |
| `split_seq_affine_prefix_direct_m128_fp32_state` | kept from #5278 |
24 | 1.002 | 1.013 | 1.036 |
| `fused_checkpoint_tma_direct_m128_n16` | kept from #5278 | 8 | 0.966 |
1.007 | 1.022 |
| `split_seq_affine_prefix_direct_m128_fp32_state_checkpoint64` | kept
from #5278 | 63 | 0.996 | 1.001 | 1.072 |
| `fused_h12_direct_m128_n16` | kept from #5278 | 4 | 0.991 | 1.000 |
1.020 |
| `fused_m64_independent_dvsplit_fp32_state` | generated in this PR |
107 | 0.983 | 1.000 | 1.011 |

</details>

The module generated in this PR replays at parity with its source kernel
on
both architectures. The modules kept from #5278 replay 1-22% slower than
what
the current Cake revision generates for the same schedule (largest:
`fused_checkpoint_direct_m128_page64_n32x2`, H12 128/256-token batches,
1.18x on B200 and 1.21x on GB300): the source arm is compiled from the
current revision, whose codegen has changed since those modules were
exported
(lane-id and `griddepcontrol` placement). Output stays bitwise
identical.
Regenerating the kept modules is a mechanical follow-up
(`export_bf16.py`
without `--keep-existing`) and is left out of this PR to keep the module
identities of #5278 unchanged.

## 🔍 Related Issues

Follow-up to #5278.

## 🚀 Pull Request Checklist

- [x] Pre-commit checks run locally on the changed Python files.
- [x] Generated modules validated against the source dispatcher (bitwise
parity on all 346 rows, both architectures).

## 🧪 Tests

- `tests/kda/test_bf16_one_wave_route.py` (new): one-wave packed H12 /
H6
grids with active and logit beta select the M64 split, the short H12
logit
grid keeps its direct N16 tile, and a 96-task grid keeps the direct
family;
each case launches and checks finite output/state/checkpoints. Passed
with
`tests/kda/test_tf32_prefill.py` on B200 (31 passed) and GB300 (see CI
bot
  run on this head).
- Cake source: `loom/tests/test_flashkda_runtime.py` (193 passed on B200
and
GB300); FlashKDA GPU e2e slice, branch versus `origin/main` in the same
  container: B200 6 shared failures on both trees (contract schema and
Triton-tolerance failures present on main), no new failures; GB300 14
shared
  failures, no new failures.
- Export: `export_bf16.py resolve` inventory check on all 346 rows for
both
  architectures (30 / 31 modules, one new specialization each); additive
  registry merge keeps every existing module identity.
- Source-versus-export parity/latency on all 346 rows for both
architectures:
  see "Export parity".

## Reviewer Notes

The host dispatch change is confined to
`_should_use_bf16_one_wave_dvsplit`,
its call in the fused launch constructor, and the active-beta
direct-path
predicate in `PreparedBF16ActiveBetaKDA`. The JIT registry gains one
`compiled_bf16_fused_m64` specialization per architecture (FP32 external
state, BF16 logit beta) plus its generated device/binding sources; the
existing specializations and module identities are unchanged.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-09-22
**监控日期**: 2026-09-21
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4497
- **最后更新**: 2026-09-21T23:44:08Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Yixing Wang, Keith

## AI分析总结

根据仓库README与提供的提交记录，以下是对昨日提交的总结分析：

**1. 主要更新类型**
本次提交为**纯粹的Bug修复**，未包含新功能、性能优化或文档更新。

**2. 关键变更点及其与项目整体方向的关系**
*   **修复前端交互流程 (#1869)**：解决了在“创建任务”模态框关闭或成功创建任务后，页面交互功能异常（如按钮失效）的问题。此修复直接优化了用户操作流程的顺畅性与可靠性，确保了项目强调的“快速、易用”的用户体验目标。
*   **增强内核安装兼容性 (#1871)**：在`fastvideo-kernel`的安装脚本中，增加了当AMD GPU的HIP工具链无法配置时，**回退安装标准的Python和Triton包**的逻辑。此举显著提升了项目在不同硬件环境下的健壮性与可安装性，降低了用户的配置门槛。

**3. 对项目的影响和潜在意义**
*   **提升用户体验与软件质量**：两个修复分别从**前端交互**和**后端安装**两个关键环节入手，消除了用户在使用过程中的具体障碍，直接提升了产品的成熟度和可靠性。
*   **扩大硬件支持范围**：对HIP工具链失败的处理，表明项目正在更积极地适配和兼容非NVIDIA的GPU环境（如AMD），这有助于吸引更多元化的开发者社区。
*   **维护社区活跃度**：及时响应并修复用户可能遇到的问题（如issue #1869和#1871），展现了项目维护者对社区反馈的重视，有利于维系健康的开源生态。

**4. 值得关注的技术点**
*   **前端状态管理**：修复页面交互可能涉及React等框架中模态框（Modal）生命周期与父组件状态同步的技术细节。
*   **构建系统的容错设计**：在安装脚本中实现**优雅降级**（从HIP到Triton），体现了对复杂硬件生态的工程化考量，是一个值得参考的实践。

**5. 基于README了解的项目背景，这些提交如何影响项目发展**
README显示FastVideo是一个注重**文档、快速入门和社区协作**的项目。本次提交：
*   **强化了“Quick Start”承诺**：使安装和任务创建这两个核心路径更加可靠，让新用户能更顺利地开始使用，符合项目快速上手的理念。
*   **夯实了项目基础**：通过解决具体的技术债（UI交互、环境兼容），为后续新功能开发和社区协作提供了更稳定的基础平台，支持项目的可持续发展。

## 详细提交记录

### [d995516](https://github.com/hao-ai-lab/FastVideo/commit/d995516da00c24105aa841df1e690d3cd8a6c173)

- **作者**: Yixing Wang
- **时间**: 2026-09-21T19:03:54Z
- **提交信息**: [bugfix] Restore page interaction after dismissing Create Job or successfully creating a job (#1869)

Co-authored-by: leo <yixingwang@YIXINGs-MacBook-Pro.local>

### [f47ad3f](https://github.com/hao-ai-lab/FastVideo/commit/f47ad3f5b7a54c1a976e1821dd9ad082f7f5b7ef)

- **作者**: Keith
- **时间**: 2026-09-21T18:59:13Z
- **提交信息**: [bugfix] fastvideo-kernel: install the Python + Triton package when the HIP toolchain cannot be configured (#1871)

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-09-22
**监控日期**: 2026-09-21
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34564
- **最后更新**: 2026-09-21T22:53:30Z

## 提交统计

- **昨日提交总数**: 5
- **提交者数量**: 5
- **主要提交者**: Steven Liu, Ch Revanth reddy, Aritra Roy Gosthipaty

## AI分析总结

1. **主要更新类型**：本次提交主要涵盖**文档更新**（占60%）与**Bug修复**（占40%），包含针对核心功能的稳定性修复。

2. **关键变更点及其与项目整体方向的关系**：
   * **文档优化**：更新了扩散管道的使用文档和图表，并修复了多处文档字符串与函数签名不匹配的错误，提升了文档的准确性与可用性，这与项目作为易用、可靠库的目标一致。
   * **硬件兼容性修复**：修复了 Ascend NPU（华为昇腾）上的 RMSNorm 和注意力掩码形状问题，体现了项目对国产 AI 加速硬件生态的持续支持与适配。
   * **核心管道稳定性修复**：解决了在混合设备（如 CPU 与 GPU）部署管道时，因组件设备放置不当导致的运行时错误。这是对 DiffusionPipeline 执行设备逻辑的重要巩固，确保了管道在复杂硬件环境下的鲁棒性，是迈向生产级部署的关键一步。

3. **对项目的影响和潜在意义**：
   * 提升了项目的**文档质量**和**代码健壮性**，减少了用户因文档错误或运行时设备不匹配而遇到的问题。
   * 增强了 diffusers 在**异构计算环境**下的可靠性，使其能更安全地应用于组件分布在不同设备上的场景。
   * 对 Ascend NPU 的支持有助于扩大项目的硬件适用范围，特别是在国内 AI 生态中。

4. **值得关注的技术点**：
   * **跨设备管道执行**：修复涉及 `encode_prompt`、`vae.encode/decode`、`image_encoder` 等核心组件，确保它们从自身设备获取输入，而非盲目使用全局执行设备。这是管理复杂模型流水线设备状态的重要实践。
   * **硬件后端适配**：对 Ascend NPU 的修复涉及底层算子（如 RMSNorm），表明项目正在深入维护对各类硬件加速器的支持。

5. **基于项目背景，这些提交如何影响项目发展**：
   * 这些提交主要属于**维护与巩固**性质，旨在提升现有功能的**稳定性、准确性和可移植性**。它们没有引入新模型，但通过修复关键缺陷和改善文档，降低了用户的使用门槛和出错概率，增强了库的成熟度和可信度，为后续集成更多新功能或模型奠定了坚实的基础。

## 详细提交记录

### [7263f33](https://github.com/huggingface/diffusers/commit/7263f3317f6b392d62f41e9d75ed9d7e21fc5a5c)

- **作者**: Steven Liu
- **时间**: 2026-09-21T16:52:06Z
- **提交信息**: [docs] Using diffusion pipelines (#14805)

* refactor

* more refactor

* improve diagram, fix link

* legacy ckpts

### [93d88c1](https://github.com/huggingface/diffusers/commit/93d88c18985697a5b8ac823d139541311d45044f)

- **作者**: Ch Revanth reddy
- **时间**: 2026-09-21T15:44:04Z
- **提交信息**: [docs] Fix docstring arguments that don't match the signatures (#14778)

- TransformerSpatioTemporalModel.forward: no num_frames parameter
- get_2d_rotary_pos_embed_lumina: parameters are len_h / len_w, not grid
- AutoencoderKLHunyuanImageRefiner / AutoencoderKLHunyuanVideo15.tiled_decode:
  no return_dict parameter; they return a plain tensor

Co-authored-by: revanth-045 <revanthreddych159@gmail.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [71f7c96](https://github.com/huggingface/diffusers/commit/71f7c96a47a08797ec53b954adb10429e9f39743)

- **作者**: Aritra Roy Gosthipaty
- **时间**: 2026-09-21T15:19:24Z
- **提交信息**: [docs] typo with hyperlink (#14826)

typo with link

### [cc8644b](https://github.com/huggingface/diffusers/commit/cc8644b447d8f11074d3df06d0ee0e3e7c91bf75)

- **作者**: TMC
- **时间**: 2026-09-21T11:14:39Z
- **提交信息**: Fix Ascend NPU RMSNorm and fused-attention mask shapes (#14288)

Co-authored-by: Dhruv Nair <dhruv.nair@gmail.com>

### [9f12469](https://github.com/huggingface/diffusers/commit/9f1246971270c84dcbe71233edb7a519596a5d02)

- **作者**: Jingya HUANG
- **时间**: 2026-09-21T07:17:32Z
- **提交信息**: [core] Fix component device placement for split-device pipelines (#14739)

* fix: component device placement for split-device pipelines

DiffusionPipeline.device/`_execution_device` (#14383) already prefer any
non-CPU, non-meta component so a pipeline with components split across
devices (e.g. text encoder on CPU, denoising backbone on an accelerator)
reports the right execution device. But several component call sites
still moved a tensor to that execution `device` before handing it to a
specific submodule, instead of the submodule's own device -- so encoding
a prompt, encoding an IP-Adapter image, or decoding latents would crash
with a device-mismatch error as soon as that submodule wasn't already
sitting on the same device as everything else.

Fixes three component types across the major pipeline families
(StableDiffusionPipeline, StableDiffusionXLPipeline,
StableDiffusion3Pipeline, FluxPipeline, Flux2(Klein)Pipeline, WanPipeline,
WanImageToVideoPipeline):

- Text encoder(s): `encode_prompt` / `_get_t5_prompt_embeds` /
  `_get_clip_prompt_embeds` now read the encoder's own `.device` instead
  of trusting the passed-in `device`.
- VAE: the `vae.encode`/`vae.decode` calls in each `__call__`, plus
  `Flux2Pipeline.prepare_image_latents` (whose output also wasn't being
  moved back to the execution device).
- image_encoder (IP-Adapter): `encode_image`, plus
  `run_safety_checker`'s feature-extractor input.

Also fixes a cross-device bug in `WanImageToVideoPipeline.prepare_latents`
and `Flux2KleinInpaintPipeline.prepare_latents`, where a vae-encoded
tensor and the freshly-sampled noise tensor could end up on different
devices before being combined by the scheduler.

Fixed the canonical/root pipelines by hand, then ran `make fix-copies` to
propagate the text-encoder/image-encoder fixes to every `# Copied from`
derivative.

Co-Authored-By: Claude Sonnet 5 <noreply@anthropic.com>

* review:reduce scope

* fix: fix not failing test while offloading

---------

Co-authored-by: Claude Sonnet 5 <noreply@anthropic.com>
Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-09-22
**监控日期**: 2026-09-21
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


**报告日期**: 2026-09-22
**监控日期**: 2026-09-21
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13156
- **最后更新**: 2026-09-21T22:19:48Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-09-22
**监控日期**: 2026-09-21
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 36274
- **最后更新**: 2026-09-22T00:50:54Z

## 提交统计

- **昨日提交总数**: 52
- **提交者数量**: 28
- **主要提交者**: Bingxu Chen, Kan Wu, Liangsheng Yin

## AI分析总结

### 1. 主要更新类型
本次提交涵盖了 **性能优化**、**硬件/模型适配**、**Bug修复**、**文档更新** 与 **架构重构**。其中，针对AMD硬件的支持和推理内核优化占据了显著比重，同时也有对CI/CD流程、路由组件（sgl-router）和并行运行时（parallel runtime）的重要重构。

### 2. 关键变更点及其与项目整体方向的关系
*   **AMD生态与硬件支持增强**：大量提交旨在提升AMD GPU（如gfx950）及国产NPU的性能与适配性，包括针对GLM、Qwen等模型的专用内核（DSA, Triton softmax routing）和吞吐配方。这直接响应了项目支持多硬件平台、构建开放生态的目标。
*   **推理能力与模型适配升级**：新增或优化了对GLM-5.3-Flash、DeepSeek-V4 Pro、MiMo-V2.6等模型的支持，并集成了XGrammar V4.1进行约束解码。同时，对Diffusion模型的配置管理进行了重构，扩展了项目的模型兼容性。
*   **性能与稳定性提升**：通过引入统一内存池的层级缓存（HiCache）、优化KV缓存管理（如跳过保留槽位、修复计数器释放）、以及实现高效的数据传输内核（TMA-staged KV transfer），直接提升了系统的内存效率和吞吐量。
*   **基础设施与工程化**：对CI/CD标签系统进行拆分、重构并行运行时的启动与接口（从公开API到内部化）、改进测试框架的阈值管理，这些工作旨在提升开发效率、代码质量和项目长期可维护性。

### 3. 对项目的影响和潜在意义
*   **短期影响**：显著增强了SGLang在AMD硬件上的性能和竞争力，同时通过修复关键Bug（如KV counter释放）和优化性能测试，提升了核心组件的稳定性和可靠性。
*   **长期意义**：持续的硬件适配和模型支持拓宽了项目的应用边界，有助于形成更活跃的硬件与模型生态。基础设施的现代化为未来更复杂的特性开发（如更高级的调度和资源管理）奠定了更坚实的基础。

### 4. 值得关注的技术点
*   **HiCache与统一内存池**：实现了层级缓存和高效的Host-Device KV传输内核（利用TMA），是解决大模型推理中内存墙问题的关键技术路径。
*   **混合注意力与CPU卸载**：支持GLM-5.3-Flash的混合注意力及PD索引映射，展示了处理超长序列或大上下文窗口的灵活策略。
*   **并行运行时重构**：通过一系列提交将并行运行时的启动、状态管理和API进行了彻底的清理和封装，提升了架构的清晰度和健壮性。
*   **sgl-router增强**：新增了对多个模型（DeepSeek, Kimi-K3）的渲染支持，并实现了更通用的准入策略，增强了路由层的功能性和可扩展性。

### 5. 基于项目背景的提交影响分析
结合项目“易用、高速、强健壮的高性能推理引擎”的目标，这些提交从多方面巩固并拓展了项目定位：
*   **性能**：直接通过内核优化和内存管理提升吞吐量。
*   **易用性与广泛性**：持续的模型和硬件适配降低了用户的使用门槛。
*   **健壮性**：关键Bug修复、测试框架改进和基础设施重构增强了系统的稳定性和开发流程的可靠性。
*   **生态**：对AMD和NPU的持续投入，以及开源的路由器组件，都在构建一个更开放、多元的技术生态系统，符合项目长远发展的需要。

## 详细提交记录

### [5066987](https://github.com/sgl-project/sglang/commit/506698761d9e0ebe3b7095ea5f639c238e99f7dc)

- **作者**: Cheng Wan
- **时间**: 2026-09-21T23:50:37Z
- **提交信息**: [unified-memory] Hierarchical cache for every unified pool shape (#37507)

### [22587fb](https://github.com/sgl-project/sglang/commit/22587fb15ce90a31c55e684495dfd16a9e5bf8e7)

- **作者**: Cheng Wan
- **时间**: 2026-09-21T23:46:22Z
- **提交信息**: [Fix] Run KV canary hooks for context-parallel prefill (#40642)

### [00986c8](https://github.com/sgl-project/sglang/commit/00986c81be687d82e66651fb3ce9a096070b06e6)

- **作者**: Yuxuan Zhang
- **时间**: 2026-09-21T23:03:03Z
- **提交信息**: Support GLM-5.3-Flash hybrid attention CPU offload and PD index mapping (#40310)

Co-authored-by: Xinyuan Tong <115166877+JustinTong0323@users.noreply.github.com>

### [0229025](https://github.com/sgl-project/sglang/commit/0229025127f3928353c7af3bd1583e87bacaa397)

- **作者**: YAMY
- **时间**: 2026-09-21T22:47:03Z
- **提交信息**: [Spec][PP] Launch extend microbatches before the spec output exchange (#40499)

### [0c53fec](https://github.com/sgl-project/sglang/commit/0c53fec4768a46a003a7afe27c938469db956368)

- **作者**: RuibinCheung
- **时间**: 2026-09-21T22:43:21Z
- **提交信息**: [ROCm] fix: remove extra bf16 -> fp32 cast in jit grouped topk kernel path (#39775)

### [d47b8c4](https://github.com/sgl-project/sglang/commit/d47b8c454c59121f8676e3d666d0542b628919d2)

- **作者**: Kan Wu
- **时间**: 2026-09-21T22:39:50Z
- **提交信息**: [sgl-router] Release cancelled circuit-breaker probes (#40603)

### [a5c2cc5](https://github.com/sgl-project/sglang/commit/a5c2cc517c5f0b6db398eb22f99a5dca840e9f20)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-21T22:37:28Z
- **提交信息**: [CI] Split the CI control labels into four axes and resolve them live (#40527)

### [66f19f5](https://github.com/sgl-project/sglang/commit/66f19f5c468f11a75d09a31ccde7b3ac3fd6814d)

- **作者**: Zhang, Jiejing
- **时间**: 2026-09-21T22:28:27Z
- **提交信息**: [AMD] Enable HiCache for GLM-5.2 MI355X throughput recipe (#40570)

### [8bde82c](https://github.com/sgl-project/sglang/commit/8bde82c0ad46e2c59dc0e1e511fdbf6b5bcf4028)

- **作者**: Jacob0226
- **时间**: 2026-09-21T22:24:44Z
- **提交信息**: [AMD] [GLM-5.3-Flash Day 0] Build the fused DSA k-pool top-k JIT kernel on HIP (#39339)

Co-authored-by: Raiden-Makoto <Raiden-Makoto@users.noreply.github.com>
Co-authored-by: Thomas Wang <thomawan@amd.com>
Co-authored-by: Kevin Mi <mikevin920@yahoo.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [2261c2e](https://github.com/sgl-project/sglang/commit/2261c2e6188a4a8e11f077eee7bd0edbbdc738a1)

- **作者**: Yingchun Lai
- **时间**: 2026-09-21T21:58:53Z
- **提交信息**: Add MiMo-V2.6 cookbook (#40622)

Co-authored-by: zijiexia <37504505+zijiexia@users.noreply.github.com>
Co-authored-by: Zijie Xia <zijie.xia@radixark.ai>

### [acac4dd](https://github.com/sgl-project/sglang/commit/acac4dd9d9ecf415628fd0ab99f101903c86f653)

- **作者**: Cheng Wan
- **时间**: 2026-09-21T21:32:22Z
- **提交信息**: [Refactor] Clean up parallel runtime comments (#40632)

### [f532ad1](https://github.com/sgl-project/sglang/commit/f532ad1f9aef2397cc86a00756f0758f8de31956)

- **作者**: William Hu
- **时间**: 2026-09-21T20:52:26Z
- **提交信息**: Fix GLM-5.3 forget-gate shape for nvCUTEDSL verify (#40607)

### [e0c2e8d](https://github.com/sgl-project/sglang/commit/e0c2e8dc4d3728bb78e50ffd73362a26efcb7d6a)

- **作者**: jacky.cheng
- **时间**: 2026-09-21T20:20:54Z
- **提交信息**: [AMD] Tune Qwen3.5 TP4 GDN recurrent launch on gfx950 (#39987)

### [1ed6822](https://github.com/sgl-project/sglang/commit/1ed68220394444d336a50e0401a3dcf3dd3d434a)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-21T20:02:10Z
- **提交信息**: [Test] Anchor `basic_perf` thresholds to each metric's measured spread (#40617)

### [b18ca9c](https://github.com/sgl-project/sglang/commit/b18ca9ca443302501b009ecc7b3f065b691f3f13)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-21T20:00:54Z
- **提交信息**: [CI] Bump sgl-eval to 0.1.2 (#40620)

### [11e661f](https://github.com/sgl-project/sglang/commit/11e661fd450d21dfc75d918b2bbc126cc6a01b50)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-09-21T19:58:48Z
- **提交信息**: [Fix] Don't free the multi-CTAs KV counter the decode graphs captured (#39175)

Co-authored-by: mmangkad <mohammad.angkad@radixark.ai>
Co-authored-by: kpham-sgl <khoa.pham@radixark.ai>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [44bdf22](https://github.com/sgl-project/sglang/commit/44bdf225d85f34a605f66a1d2c6a4eafa33b2f0e)

- **作者**: Cheng Wan
- **时间**: 2026-09-21T19:31:11Z
- **提交信息**: Fix lint failure from MXFP8 reserved-slot test location (#40618)

### [bccf691](https://github.com/sgl-project/sglang/commit/bccf691b221835689450ef601e73fd6ee79c2ac3)

- **作者**: Cheng Wan
- **时间**: 2026-09-21T19:29:50Z
- **提交信息**: Bringing the parallel runtime up becomes a phase, not a side effect (#40345)

### [1d3243d](https://github.com/sgl-project/sglang/commit/1d3243d05f614e55eec759390f91a80026df30c2)

- **作者**: Cheng Wan
- **时间**: 2026-09-21T19:27:50Z
- **提交信息**: Take the parallel getters off the package's public surface (#40344)

### [970e946](https://github.com/sgl-project/sglang/commit/970e946e4fdaa1271a4044fd36850650d315fecf)

- **作者**: Cheng Wan
- **时间**: 2026-09-21T19:26:40Z
- **提交信息**: Retire the per-runner parallel record (#40343)

### [73f071d](https://github.com/sgl-project/sglang/commit/73f071db52e87f56f9d44546fc81b7dbc2aaa72e)

- **作者**: Cheng Wan
- **时间**: 2026-09-21T19:25:32Z
- **提交信息**: Deprecate the parallel getters the context answers, and ratchet them shut (#40342)

### [65be3fa](https://github.com/sgl-project/sglang/commit/65be3fa71a4d35c5166cd1b510e5e9203989455c)

- **作者**: Cheng Wan
- **时间**: 2026-09-21T19:24:17Z
- **提交信息**: A runner and the objects it builds freeze the placement they describe (#40341)

### [2d0e94e](https://github.com/sgl-project/sglang/commit/2d0e94e3a36cbf125d52eaf20bfb26117a6e72ca)

- **作者**: Cheng Wan
- **时间**: 2026-09-21T19:22:59Z
- **提交信息**: Check the topology identities where the layout is written, and build at the published widths (#40340)

### [d5fdab7](https://github.com/sgl-project/sglang/commit/d5fdab7022bd19b302e207c2d3c67a169bf4d162)

- **作者**: ishandhanani
- **时间**: 2026-09-21T19:21:30Z
- **提交信息**: chore: add NIXL owners and CI access (#40602)

Co-authored-by: Kangyan-Zhou <zky314343421@gmail.com>

### [0db1a93](https://github.com/sgl-project/sglang/commit/0db1a93adb098e8651c07d51bb26492b9587ca52)

- **作者**: Cheng Wan
- **时间**: 2026-09-21T19:19:38Z
- **提交信息**: State the draft's whole topology in its scope, and read the rest from the context (#40339)

### [ae7a516](https://github.com/sgl-project/sglang/commit/ae7a516ba723e3504966d2cfb54fba8e7c9aa710)

- **作者**: Yixin Dong
- **时间**: 2026-09-21T19:12:28Z
- **提交信息**: feat: use XGrammar V4.1 DSML parameter constraints (#39026)

Co-authored-by: yuchuan <yuchuan.7streams@gmail.com>
Co-authored-by: Xinyuan Tong <115166877+JustinTong0323@users.noreply.github.com>
Co-authored-by: Xinyuan Tong <xinyuantong.cs@gmail.com>

### [f0940fe](https://github.com/sgl-project/sglang/commit/f0940fe3a6d2f2761d04ecc4cdf64349a4a1c022)

- **作者**: Faradawn Yang
- **时间**: 2026-09-21T19:10:03Z
- **提交信息**: Update DeepSeek-V4 Pro for B200 FP4 agentic PD disaggregation (#40610)

Signed-off-by: Faradawn Yang <73060648+faradawn@users.noreply.github.com>

### [90b3f85](https://github.com/sgl-project/sglang/commit/90b3f8544ca23452481e6b0267b7b72b6021a7b3)

- **作者**: jacky.cheng
- **时间**: 2026-09-21T19:02:29Z
- **提交信息**: [AMD] Use Triton softmax routing for Qwen3.5 on gfx950 (#39986)

### [f702a0b](https://github.com/sgl-project/sglang/commit/f702a0be29c598f5b02b4f1a8032a963b1b8f621)

- **作者**: ronnie_zheng
- **时间**: 2026-09-21T18:05:19Z
- **提交信息**: Revert "[Diffusion] migrate the whole _register_configs from registry.py to the model own config file" (#40611)

### [632919e](https://github.com/sgl-project/sglang/commit/632919e49865429f10af9a4976c219ff4ea53487)

- **作者**: Bingxu Chen
- **时间**: 2026-09-21T17:51:37Z
- **提交信息**: [AMD] Fix DeepSeek-R1-MXFP4 accuracy with AITER FP8 (#37762)

### [e6931ca](https://github.com/sgl-project/sglang/commit/e6931ca88991c4b1bd9d633b5e4232e5611e7cc8)

- **作者**: ronnie_zheng
- **时间**: 2026-09-21T17:45:53Z
- **提交信息**: [Diffusion] migrate the whole _register_configs from registry.py to the model own config file (#40475)

### [7a6191c](https://github.com/sgl-project/sglang/commit/7a6191c4b95f269d6108bbf2412c420f42655594)

- **作者**: cctry
- **时间**: 2026-09-21T17:44:29Z
- **提交信息**: Preallocate HiCache MHA staging before post-capture KV sizing (#40256)

### [7ad55e4](https://github.com/sgl-project/sglang/commit/7ad55e43865c3555bad01360743f0a8d92c09677)

- **作者**: cctry
- **时间**: 2026-09-21T17:38:23Z
- **提交信息**: [HiCache] TMA-staged host<->device KV transfer kernel (sm_90+) (#40278)

### [0cb37c0](https://github.com/sgl-project/sglang/commit/0cb37c018c2227c4c41685587b840a3bb06dbc6b)

- **作者**: William Hu
- **时间**: 2026-09-21T17:34:08Z
- **提交信息**: [KDA] Enable ReplaySSM for GLM-5.3 Flash (#40517)

### [3c71bb0](https://github.com/sgl-project/sglang/commit/3c71bb018aa5811eea9c0f8c43736834dea8b2b9)

- **作者**: Eric.Chin.AMD
- **时间**: 2026-09-21T17:31:07Z
- **提交信息**: [AMD] Enable GLM DSA prefill top-k to the v2 kernel (#37889)

Co-authored-by: Thomas Wang <thomawan@amd.com>

### [5a6a1bb](https://github.com/sgl-project/sglang/commit/5a6a1bb88354b4d0ed13c0424cb6e3bc7539c674)

- **作者**: Sam Shleifer
- **时间**: 2026-09-21T17:21:25Z
- **提交信息**: [mxfp8-kv] Skip writes to the reserved CUDA-graph padding slot (#35351)

Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>
Co-authored-by: Ke Bao <ispobaoke@gmail.com>
Co-authored-by: Sam Shleifer <sam@thinkingmachines.ai>

### [008470a](https://github.com/sgl-project/sglang/commit/008470abd80a3c50c95c16aa41ac97d51586819e)

- **作者**: Kan Wu
- **时间**: 2026-09-21T17:07:07Z
- **提交信息**: [sgl-router] Bound streaming lifetimes and release guards on idle disconnect (#40391)

Co-authored-by: Shangming Cai <csmthu@gmail.com>

### [800613a](https://github.com/sgl-project/sglang/commit/800613a74bc1febbe0804f3b458468d9bdb32700)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-21T17:05:57Z
- **提交信息**: [Test] Split the serving perf tests by topic into `basic_perf/` and route their thresholds through a kit (#40505)

### [14e9c40](https://github.com/sgl-project/sglang/commit/14e9c40a72aa247ceb07b93b32b1fe353317bcf2)

- **作者**: Sage
- **时间**: 2026-09-21T15:32:52Z
- **提交信息**: [Observability] Expose python/rust frontend identity in `/server_info` (#39993)

Signed-off-by: Sage Ahrac <sagiahrak@gmail.com>

### [50ec970](https://github.com/sgl-project/sglang/commit/50ec9702d0dc680d114c311a4df83d96a15062a0)

- **作者**: Mick
- **时间**: 2026-09-21T13:23:11Z
- **提交信息**: [diffusion] docs: update ComfyUI sections, trimmed examples, and the RTX 5090 DiT-resident recipe (1.42x) for Qwen-Image-2.1 cookbook (#40573)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [69d1e5c](https://github.com/sgl-project/sglang/commit/69d1e5cfe06ed544b88aa38dc7a39f2a66cdd558)

- **作者**: iridiumine
- **时间**: 2026-09-21T12:32:52Z
- **提交信息**: [Docs][NPU] Add MiMo-V2.5-Pro FP4 DFlash best practice on Ascend NPU (#40577)

### [b410010](https://github.com/sgl-project/sglang/commit/b410010087e31b06f675425e0d1c05dc49b6aa8f)

- **作者**: amote-i
- **时间**: 2026-09-21T12:18:03Z
- **提交信息**: [NPU] [DOC] Add kimi k3 cookbook for 950PR/DT Series (#40575)

### [0f6761b](https://github.com/sgl-project/sglang/commit/0f6761b54facebb47f2068f87ecccd8f14da3a0e)

- **作者**: Kan Wu
- **时间**: 2026-09-21T10:35:09Z
- **提交信息**: [sgl-router] Add SGLang-compatible DeepSeek V4.1 Flash rendering (#40532)

### [0abb251](https://github.com/sgl-project/sglang/commit/0abb251a201c5b7eda37fb2012b8ecc31b0e7cd1)

- **作者**: Kan Wu
- **时间**: 2026-09-21T09:56:41Z
- **提交信息**: [sgl-router] Match DeepSeek V4 rendering to SGLang (#40530)

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: Shangming Cai <csmthu@gmail.com>

### [2016f5e](https://github.com/sgl-project/sglang/commit/2016f5e7a12ec7dc80c1e1f633f9ced8dbe419ad)

- **作者**: Kan Wu
- **时间**: 2026-09-21T09:38:49Z
- **提交信息**: [sgl-router] Add Kimi-K3 rendering with SGLang parity (#40390)

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [b86a30a](https://github.com/sgl-project/sglang/commit/b86a30afbae389eec8763f4bcf38f14904d2d00c)

- **作者**: Zhaoyi Li
- **时间**: 2026-09-21T08:56:46Z
- **提交信息**: [AMD][DI][CI] Add a SPUR cluster profile to AMD DI CI  (#40113)

### [8faa2d6](https://github.com/sgl-project/sglang/commit/8faa2d6731812fbcfe3a7f906333f92988882ad3)

- **作者**: hanwlax
- **时间**: 2026-09-21T08:56:35Z
- **提交信息**: [NPU][Diffusion] Disable loading latency checks in Ascend fixtures (#40544)

### [630b1ef](https://github.com/sgl-project/sglang/commit/630b1ef322c2f995adf7ecafa067b67289d1b9e0)

- **作者**: Shangming Cai
- **时间**: 2026-09-21T08:42:29Z
- **提交信息**: [sgl-router] Fix reorg admission proxy test build after BucketResolver::new (#40537)

Co-authored-by: Kan Wu <wukanustc@gmail.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [8d08dfd](https://github.com/sgl-project/sglang/commit/8d08dfdab7b7086486677aacf2e63814496a385c)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-09-21T08:34:43Z
- **提交信息**: [Fix] Add gigachat35 to the tool-call and reasoning parser name lists (#40554)

Co-authored-by: Mohammad Angkad <mohammad.angkad@radixark.ai>

### [a987101](https://github.com/sgl-project/sglang/commit/a9871012acb768dc94a43a6542cc32626c7b7b0b)

- **作者**: Kan Wu
- **时间**: 2026-09-21T08:26:30Z
- **提交信息**: [sgl-router] refactor - generalized admission policy definitions (#40271)

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [70b5b03](https://github.com/sgl-project/sglang/commit/70b5b03e78612c94f86ac98eb4d2d8d19ceda738)

- **作者**: Shangming Cai
- **时间**: 2026-09-21T08:07:27Z
- **提交信息**: [NPU][CI] Fix paths-filter negation that makes every PR run the NPU tier (#40549)

### [c2f860a](https://github.com/sgl-project/sglang/commit/c2f860af1c925770183a1aa7ca6ea70076c13952)

- **作者**: ashwini rathi
- **时间**: 2026-09-21T07:39:29Z
- **提交信息**: [ci][xpu] Record device time in the multimodal_gen perf lane (#39956)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-09-22
**监控日期**: 2026-09-21
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1284
- **最后更新**: 2026-09-21T06:50:36Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-09-22
**监控日期**: 2026-09-21
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 92365
- **最后更新**: 2026-09-22T00:31:33Z

## 提交统计

- **昨日提交总数**: 40
- **提交者数量**: 29
- **主要提交者**: Juan Pérez de Algaba, Fangzhou Ai, weitliao

## AI分析总结

根据vllm仓库昨日的提交记录，并结合其“提供快速、低成本LLM服务”的项目目标，分析总结如下：

### 1. 主要更新类型
*   **Bug修复 (9个):** 涵盖内核、前端、多模态、MoE、NIXL等多个模块，修复了计算逻辑、参数处理、兼容性等问题。
*   **性能优化 (8个):** 集中在AMD/ROCm平台，包括GEMM、Attention、MoE路由等关键路径的优化，以及模型特定的融合内核。
*   **功能新增 (2个):** 包括为编程式KV管理添加一等公民的请求信封，以及为Engram特性添加文档页面。
*   **CI/构建改进 (9个):** 主要针对ROCm平台的测试、覆盖率、镜像构建（如使用zstd压缩）和稳定性进行强化。
*   **重构 (2个):** 主要涉及多模态处理代码结构的优化，将相关功能移入处理器。
*   **其他:** 包括文档更新、安全修复（防止过期缓存）及针对AMD新硬件（如MI300）的验证。

### 2. 关键变更点及与项目方向的关系
*   **深化硬件生态支持 (特别是AMD/ROCm):** 大量提交针对ROCm平台进行性能调优、Bug修复和测试加固，直接响应了项目扩展硬件兼容性、追求更广泛“低成本”部署的核心方向。
*   **增强生产环境稳定性与可靠性:** 密集的Bug修复（如内存处理、DP rank、MoE后端支持）和CI鲁棒性提升，旨在提高模型服务在不同配置下的稳定运行能力，符合“易用、可靠”的目标。
*   **优化核心计算与调度路径:** 对Attention元数据操作、MoE路由输出、平台调度器等底层机制的优化，旨在降低延迟、提升吞吐量，直接服务于“快速”服务的核心承诺。
*   **推进多模态与新特性集成:** 如Engram、多模态处理的重构以及相关文档，表明项目在持续扩展支持的模型类型和功能边界，保持技术先进性。

### 3. 对项目的影响和潜在意义
*   **短期影响:** 提升了在AMD GPU上运行特定模型（如DeepSeek V4.1, MiniMax-M3）的性能与稳定性，修复了多个已知问题，增强了CI流水线的可靠性。
*   **长期意义:** 这些提交共同推动vLLM向一个更健壮、性能更高、支持硬件更广泛的平台演进。特别是ROCm生态的持续完善，降低了在不同硬件上部署高性能LLM的门槛，有利于项目社区和用户群的扩大。

### 4. 值得关注的技术点
*   **性能优化细节:** 提交`[97dc6b1]`避免了稀疏注意力的元数据冗余操作，体现了对性能热点的精细优化；`[b8cf275]`针对特定模型启用了融合QK-norm内核。
*   **架构与功能设计:** 提交`[0b7f11a]`为MoE引入了基于块的路由专家输出存储，这是一种新的辅助输出管理机制；`[986e217]`引入的KV hints信封为更灵活的KV Cache管理提供了编程接口。
*   **硬件适配与验证:** 提交`[20e3468]`启用了DeepSeek V4.1 ViT在ROCm上的测试，`[31c471]`针对DeepSeek V4.1模型禁用了特定的滑动窗口注意力优化，显示了对新模型和硬件的积极适配与验证。

### 5. 对项目发展的影响
这些提交体现了vLLM项目活跃的社区贡献和明确的技术路线：**在持续巩固和优化核心推理引擎性能的同时，大力拓展硬件生态（尤其是AMD），并不断丰富和稳定其多模态、新模型及编程接口等高级功能。** 这完全符合其README中描述的“易用、快速、低成本”的普惠愿景，使得项目不仅在NVIDIA GPU上保持领先，也在其他硬件平台上具备了更强的竞争力和实用性，从而巩固其作为通用LLM服务基础设施的地位。

## 详细提交记录

### [7d06dd1](https://github.com/vllm-project/vllm/commit/7d06dd1ffaab13bb6b9a34e86a8a62e4d715bd1e)

- **作者**: Taneem Ibrahim
- **时间**: 2026-09-21T23:54:57Z
- **提交信息**: [Pooling] MRV2 pooling shutdown model ref (#57737)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [13058fa](https://github.com/vllm-project/vllm/commit/13058faa49f5e4a4d50e1ca562ba0c2fdd73c7bc)

- **作者**: Nils Matteson
- **时间**: 2026-09-21T23:18:49Z
- **提交信息**: [Frontend] Add reusable TP1 initialized-engine snapshots (#51360)

Signed-off-by: Nils Matteson <nilsmatteson@icloud.com>
Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>
Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>
Co-authored-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>
Co-authored-by: elehayym <52448798+Yuzu23@users.noreply.github.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [8bf051c](https://github.com/vllm-project/vllm/commit/8bf051cd51adff79e1bc94e910adaea543aaa2e1)

- **作者**: Garrett Goon
- **时间**: 2026-09-21T22:38:38Z
- **提交信息**: [Bugfix][Kernel] Skip the fused silu-mul block-quant fast path when a swiglu clamp is set (#57984)

Signed-off-by: Garrett Goon <garrett@primeintellect.ai>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [8644d2a](https://github.com/vllm-project/vllm/commit/8644d2af2fb7c4588190a8d7f6c26a3cbef78a0f)

- **作者**: vllm-agent
- **时间**: 2026-09-21T22:30:14Z
- **提交信息**: [CI][Build] Harden triton-cpu sleef submodule fetch in CPU image build (#57871)

Signed-off-by: kimi-no-na-wa <kimi-no-na-wa@users.noreply.github.com>
Co-authored-by: kimi-no-na-wa <kimi-no-na-wa@users.noreply.github.com>

### [382970e](https://github.com/vllm-project/vllm/commit/382970ee6ca490aeaaaf4e32c53695b581ff61ba)

- **作者**: yinfengLiu
- **时间**: 2026-09-21T20:44:41Z
- **提交信息**: [Kimi-K3][AMD] Return KDA and MLA projection outputs directly (#50592)

Signed-off-by: Liuyinfeng01 <yinfeliu@amd.com>
Co-authored-by: Liuyinfeng01 <199041580+LiuYinfeng01@users.noreply.github.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [9fe1cbd](https://github.com/vllm-project/vllm/commit/9fe1cbd463055314863a6de210d5f898200a0a9a)

- **作者**: Nils Matteson
- **时间**: 2026-09-21T20:40:15Z
- **提交信息**: [Docker] Use zstd for CI images and offer a Docker Hub variant (#55608)

Signed-off-by: Nils Matteson <nilsmatteson@icloud.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [12972ae](https://github.com/vllm-project/vllm/commit/12972ae40bece6f9b9898fadd0c50d6a317df6fd)

- **作者**: Andreas Karatzas
- **时间**: 2026-09-21T20:30:21Z
- **提交信息**: [Bugfix][ROCm] Reject unsupported EP for monolithic AITER MXFP4 MoE (#57866)

Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [9179bcd](https://github.com/vllm-project/vllm/commit/9179bcd4166bd03f4903aafed39d2c284eeb8c91)

- **作者**: Andreas Karatzas
- **时间**: 2026-09-21T20:28:35Z
- **提交信息**: [Bugfix][MoE] Reject hash routing for unsupported monolithic backends (#57867)

Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [54020c3](https://github.com/vllm-project/vllm/commit/54020c3c3ec9de219929a5a956010a0251b87520)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-09-21T18:16:02Z
- **提交信息**: [Engram] Drop redundant VLLM_PLE_CPU_OFFLOAD env var (#57937)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [1732237](https://github.com/vllm-project/vllm/commit/17322375a2d7815ed3d7c9c3ffd718196564314e)

- **作者**: Mikko Tukiainen
- **时间**: 2026-09-21T17:17:55Z
- **提交信息**: [ROCm][Perf] Route the fused shared-expert gate GEMM through the platform dispatcher (#54185)

Signed-off-by: Mikko Tukiainen <Mikko.Tukiainen@amd.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [fba33e3](https://github.com/vllm-project/vllm/commit/fba33e39cb74c7c31cc648ae530a85e0c6636f92)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-09-21T17:15:28Z
- **提交信息**: [Docs] Add an Engram feature page explaining Engram usage in vLLM (#57910)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [986e217](https://github.com/vllm-project/vllm/commit/986e217158a9ed54eca8307c6bb9abac7c5b2278)

- **作者**: Karen Chung
- **时间**: 2026-09-21T16:56:11Z
- **提交信息**: [Feature] Add first-class KV hints request envelope for programmatic KV management (#53423)

Signed-off-by: Karen Chung <karenc@nvidia.com>

### [4f14516](https://github.com/vllm-project/vllm/commit/4f1451679088e5832bce0965a254295c854aaa09)

- **作者**: djramic
- **时间**: 2026-09-21T16:39:31Z
- **提交信息**: [ROCm][CI] Use ROCm backend for DeepSeek V4.1 ViT test (#57931)

Signed-off-by: Djordje Ramic <djoramic@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [7853700](https://github.com/vllm-project/vllm/commit/7853700d4cdc2b84c728c840114ed42cda7454a7)

- **作者**: Cyrus Leung
- **时间**: 2026-09-21T16:39:20Z
- **提交信息**: [MM] Move get_dummy_processor_inputs into MM processor (#57967)

Signed-off-by: DarkLight1337 <tlleungac@connect.ust.hk>

### [4e61ad8](https://github.com/vllm-project/vllm/commit/4e61ad8ee126bf01dbc4d28979014a30628309ed)

- **作者**: Sahil Patel
- **时间**: 2026-09-21T16:38:25Z
- **提交信息**: [Bugfix] unskip InternViT test for transformers v5 compatibility (#55767)

Signed-off-by: sahil <sahil@example.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>

### [874a6b5](https://github.com/vllm-project/vllm/commit/874a6b5a06f19c9d565d14ebe64131d6aaab91cd)

- **作者**: afriedri
- **时间**: 2026-09-21T16:30:16Z
- **提交信息**: [ROCm] Refactor tuned gemms (#55001)

Signed-off-by: Andy Friedrich <afriedri@amd.com>
Signed-off-by: afriedri <afriedri@amd.com>
Co-authored-by: Douglas Lehr <91553416+dllehr-amd@users.noreply.github.com>
Co-authored-by: Shanshan Shen <467638484@qq.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [8c08250](https://github.com/vllm-project/vllm/commit/8c0825090df8b7939a92ff22b02bc7d03cb3605a)

- **作者**: Lucas Wilkinson
- **时间**: 2026-09-21T15:57:49Z
- **提交信息**: [Bugfix][NIXL] Fix DCP pulls across MLA cache regions (#57389)

Signed-off-by: Lucas Wilkinson <lwilkinson@neuralmagic.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [6b85875](https://github.com/vllm-project/vllm/commit/6b858751f6e99c4f33913657dc0c2afd34ff13e6)

- **作者**: Lucain
- **时间**: 2026-09-21T15:32:27Z
- **提交信息**: [docs] Fix legacy hf CLI references (vllm) (#57958)

Signed-off-by: Wauplin <lucainp@gmail.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [dc479a2](https://github.com/vllm-project/vllm/commit/dc479a2d839d5c474b36ac521dc5a72294bcb186)

- **作者**: Tony Lin
- **时间**: 2026-09-21T15:19:14Z
- **提交信息**: [Bugfix] Fix external LB DP rank handling when replicas share nodes (#53743)

Signed-off-by: Tony Lin <tony.lin@intel.com>

### [e34685d](https://github.com/vllm-project/vllm/commit/e34685dfc0c9f46ae58650fe7b08cc89b615a5fe)

- **作者**: Tuukka Sarvi
- **时间**: 2026-09-21T15:03:41Z
- **提交信息**: [ROCm][DSv4] Enable DSpark adaptive verification (#52362)

Signed-off-by: Tuukka Sarvi <tuukka.sarvi@amd.com>
Signed-off-by: larryli2-amd <larryli2@amd.com>
Co-authored-by: larryli2-amd <larryli2@amd.com>

### [21aa17c](https://github.com/vllm-project/vllm/commit/21aa17c1289f9c376c941b5a5e3d140590d4cae1)

- **作者**: sfigs
- **时间**: 2026-09-21T14:55:38Z
- **提交信息**: [Bugfix][Frontend] Accept diarized transcription responses in run-batch (#57948)

Signed-off-by: Sergio Figueras <sergio@yourecm.com>

### [887cf91](https://github.com/vllm-project/vllm/commit/887cf91e30545373f90eb967c981b456c9cbbf8d)

- **作者**: Taneem Ibrahim
- **时间**: 2026-09-21T14:46:39Z
- **提交信息**: [Pooling] Fix normalization of chunked long-text embeddings (#57498)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [c8824a1](https://github.com/vllm-project/vllm/commit/c8824a1e42bbd674751f808d657d58024c68fb0f)

- **作者**: Cyrus Leung
- **时间**: 2026-09-21T14:43:07Z
- **提交信息**: [MM] Move `supports_multimodal_inputs` and cache out of registry (#57913)

Signed-off-by: DarkLight1337 <tlleungac@connect.ust.hk>

### [7488b57](https://github.com/vllm-project/vllm/commit/7488b5780f585fc0a00a6ab28b6a2477696574d1)

- **作者**: Andreas Karatzas
- **时间**: 2026-09-21T14:42:47Z
- **提交信息**: [ROCm][Tests] Reduce host memory when downcasting FP32 HF references (#57869)

Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [8b98b7d](https://github.com/vllm-project/vllm/commit/8b98b7d0b465920740cfa1acf5dde1b6a57d8d52)

- **作者**: Martin Hickey
- **时间**: 2026-09-21T14:13:52Z
- **提交信息**: [Frontend] Add streaming parity tests and docs for derender (#57922)

Signed-off-by: Martin Hickey <martin.hickey@ie.ibm.com>

### [606d124](https://github.com/vllm-project/vllm/commit/606d124b377e6462fe0f9076df4d50c88e4dcf48)

- **作者**: Hotragn Pettugani
- **时间**: 2026-09-21T13:27:40Z
- **提交信息**: [Bugfix][Multimodal] Tolerate malformed EXIF in Molmo 2 image preprocessing (#57234)

Signed-off-by: hotragn <hotragn.pettugani_2024@woxsen.edu.in>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [db7f1f6](https://github.com/vllm-project/vllm/commit/db7f1f671419535b85fa73e29ff061e287e39459)

- **作者**: Chaojun Zhang
- **时间**: 2026-09-21T12:54:58Z
- **提交信息**: [CI][XPU] Deselect Ray UT in XPU V1 test Job (#57889)

Signed-off-by: Chaojun Zhang <chaojun.zhang@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [7268f6e](https://github.com/vllm-project/vllm/commit/7268f6e38ebbb3d61700f16c638c6eba0c88bb0c)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-09-21T12:50:48Z
- **提交信息**: [Security] Prefer fresh multimodal payloads over a stale receiver cache (#57833)

Signed-off-by: Juan Pérez de Algaba <jperezde@redhat.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [82daf9f](https://github.com/vllm-project/vllm/commit/82daf9f5756e1868be0aa751afaec4726beca12a)

- **作者**: Andreas Karatzas
- **时间**: 2026-09-21T11:08:06Z
- **提交信息**: [CI][ROCm] Add ten AMD parity groups (#57876)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [15859bb](https://github.com/vllm-project/vllm/commit/15859bb3a1d81a709b64eff2a1d1f38a958a362b)

- **作者**: CaiJohn
- **时间**: 2026-09-21T10:56:28Z
- **提交信息**: [Test] Organize structured output utility tests (#57545)

Signed-off-by: john <6712432+CaiJohn@users.noreply.github.com>
Co-authored-by: john <6712432+CaiJohn@users.noreply.github.com>

### [04c1f4a](https://github.com/vllm-project/vllm/commit/04c1f4a407962a37d01b573f3a2aba91dd2ed3a9)

- **作者**: Fangzhou Ai
- **时间**: 2026-09-21T10:29:14Z
- **提交信息**: [Bugfix][ROCm][DSv4.1] Disable SWA bounded replay on ROCm (#57906)

Signed-off-by: Fangzhou Ai <fangzhou.ai@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [0b7f11a](https://github.com/vllm-project/vllm/commit/0b7f11a1eece3dc9c689f1b5ab90d60c03b10793)

- **作者**: Hongxin Xu
- **时间**: 2026-09-21T10:25:05Z
- **提交信息**: [AuxOutput] Add block-keyed storage for routed-expert outputs (#45635)

Signed-off-by: aoshen02 <aoshen@inferact.ai>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: Roger Wang <hey@rogerw.io>
Co-authored-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Codex <noreply@openai.com>

### [0aee727](https://github.com/vllm-project/vllm/commit/0aee727ff6131a1b647941186ceef8f4777bdac2)

- **作者**: djramic
- **时间**: 2026-09-21T09:18:59Z
- **提交信息**: [CI][ROCm] Increase timeout for MI300 Distributed DP Extended (#57903)

Signed-off-by: Djordje Ramic <djoramic@amd.com>

### [8902dbb](https://github.com/vllm-project/vllm/commit/8902dbb1770b7b1780bf3d978f16cd208702472a)

- **作者**: Andreas Karatzas
- **时间**: 2026-09-21T09:16:26Z
- **提交信息**: [CI][ROCm] Mirror remaining portable suites without duplicate coverage (#57877)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [b8cf275](https://github.com/vllm-project/vllm/commit/b8cf2753825d05d7f41eb4747480b78934953aac)

- **作者**: weitliao
- **时间**: 2026-09-21T08:38:30Z
- **提交信息**: [AMD][Minimax-M3][perf] Enable packed LBHNC AITER QK-norm fusion for MiniMax-M3 on ROCm (#54535)

Signed-off-by: Wei-Ting Liao <wei-ting.liao@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Shanshan Shen <467638484@qq.com>

### [f05b887](https://github.com/vllm-project/vllm/commit/f05b88751ec74b66ee27eb38f65fdfdda6161239)

- **作者**: Andreas Karatzas
- **时间**: 2026-09-21T08:29:02Z
- **提交信息**: [CI][ROCm] Make Python-only installation failures blocking (#57870)

Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [76ffb0d](https://github.com/vllm-project/vllm/commit/76ffb0d37488988ec158cab609d5569e9f9ca34c)

- **作者**: Juntian Liu
- **时间**: 2026-09-21T08:26:56Z
- **提交信息**: [Model][Engram] Share host tables across co-located DP replicas by default (#57651)

Signed-off-by: Juntian Liu <Juntianl777@gmail.com>
Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: zjy0516 <riverclouds.zhu@qq.com>

### [0ff0477](https://github.com/vllm-project/vllm/commit/0ff0477ff955154f37db48791260cdf27fa35e60)

- **作者**: akii96
- **时间**: 2026-09-21T08:20:43Z
- **提交信息**: [Perf][ROCm] Add a ROCm path for Hy4 and compile the backbone (#57526)

Signed-off-by: Aakif Nawaz <aakif.nawaz@amd.com>

### [67513c8](https://github.com/vllm-project/vllm/commit/67513c8b67e2439934ce7c0ba5a18c2e859f5c53)

- **作者**: Woosuk Kwon
- **时间**: 2026-09-21T08:16:59Z
- **提交信息**: [Bugfix][DSV4.1] Restrict mHC overlap to full CUDA graphs (#57874)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [97dc6b1](https://github.com/vllm-project/vllm/commit/97dc6b19d2fe92b794b49e684677a2e1a8b2c540)

- **作者**: Woosuk Kwon
- **时间**: 2026-09-21T07:08:43Z
- **提交信息**: [Perf][Attention] Avoid redundant sparse attention metadata operations (#57885)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: OpenAI Codex <noreply@openai.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-09-22
**监控日期**: 2026-09-21
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 6974
- **最后更新**: 2026-09-22T00:32:40Z

## 提交统计

- **昨日提交总数**: 21
- **提交者数量**: 17
- **主要提交者**: zhumingjue138, Ding Zuhao, tsinghua-code

## AI分析总结

根据提供的提交记录和项目README，对仓库 `vllm-project/vllm-omni` 昨日（第1批）的提交分析总结如下：

### 1. 主要更新类型
本次提交批次涵盖了多方面的改进，主要包括：
*   **Bug修复**：占比最高，涉及推理引擎、前端交互、模型精度、测试环境等多个模块的修复与稳定性提升。
*   **性能优化**：在特定模型（如Qwen3-TTS、LingBot World）上启用事件驱动编排、FP8线性层及KV缓存重用等技术。
*   **功能新增与模型集成**：新增多NPU部署配置、扩散模型生成控制，并集成AURA模型到全双工运行时，为MiniMax-H3新增前端工作流。
*   **模型支持与配置更新**：为Qwen3-TTS默认启用新版模型运行器，并更新多个模型（如LingBot-World）的默认配置。
*   **文档、CI/基准测试与测试**：更新项目文档二维码，优化CI配置以集成新基准测试和稳定测试。

### 2. 关键变更点及其与项目方向的关系
*   **深化全模态支持**：对TTS（Qwen3-TTS）、扩散模型、视频模型（LingBot-World）以及全双工对话（AURA集成）的持续集成与优化，直接推进了项目“Omni-Modality”（全模态）的核心目标。
*   **优化性能与资源效率**：事件驱动编排、FP8量化、KV缓存重用以及VAE解码分片等变更，旨在降低延迟和成本，契合“Fast”与“Cheap”的项目愿景。
*   **提升易用性与稳定性**：大量的Bug修复（如保持配置隔离、修复精度错误）以及测试隔离，致力于提供更可靠、易用的服务，符合“Easy”的目标。
*   **硬件适配与部署扩展**：新增针对国产NPU的多卡部署配置，增强了项目的硬件兼容性和部署灵活性。

### 3. 对项目的影响和潜在意义
*   **提升生产就绪度**：密集的Bug修复和稳定性测试显著提高了系统的可靠性，为更广泛的生产部署扫清障碍。
*   **巩固技术领先地位**：通过持续集成最新开源模型（如Qwen3-TTS）和先进的优化技术（如FP8、KV重用），项目保持了在多模态服务领域的技术前沿性。
*   **拓展应用场景**：新增的部署配置、模型支持和前端工作流，使得vllm-omni能够服务更多样的硬件环境和应用需求（如实时交互、创作工作流）。

### 4. 值得关注的技术点
*   **多NPU解耦部署**：为特定模型（MOSS-TTS-Local）提供2卡和3卡NPU的分离式部署配置，是针对异构计算环境的重要适配。
*   **生成过程精细控制**：为扩散模型阶段新增`pause_generation(mode="keep")`功能，提供了对长序列生成过程更灵活的控制能力。
*   **事件驱动架构推进**：在TTS等场景将事件驱动编排设为默认，标志着系统向更低延迟、更高吞吐的异步处理架构演进。
*   **全双工与实时交互**：将AURA模型集成到全双工运行时，并修复客户端会话同步问题，增强了实时对话场景的体验。

### 5. 对项目发展的影响
本次提交批次在“全模态”、“易用”、“快速”三个方向上均有实质推进。项目正通过广泛集成和优化各类前沿模型（语音、视觉、对话）来兑现“全模态”的承诺；同时，通过密集的工程修复、性能调优和硬件适配，不断夯实其作为“易用、快速、低成本”服务平台的基础设施角色。这些提交使vllm-omni从一个支持基础模型的服务，向一个更加稳定、高效、覆盖更广专业领域的多模态服务平台演进，巩固了其在多模态AI服务生态中的定位。

## 详细提交记录

### [0b5f883](https://github.com/vllm-project/vllm-omni/commit/0b5f8832b91e10537f1c96f33fbbd2bedb7bca51)

- **作者**: jingchengtian
- **时间**: 2026-09-21T23:14:52Z
- **提交信息**: [tts][feature][NPU] Add 2-NPU and 3-NPU disaggregated deploy profiles for MOSS-TTS-Local (#7052)

Signed-off-by: jingchengtian <tjc1995@126.com>

### [381b12f](https://github.com/vllm-project/vllm-omni/commit/381b12fa876e26495c7b76e356a823f5b0f4254a)

- **作者**: Sun
- **时间**: 2026-09-21T19:18:30Z
- **提交信息**: [Bugfix] Keep --no-guardrails out of diffusion stage config (#7917)

Signed-off-by: levius <2114377220@qq.com>

### [473da2c](https://github.com/vllm-project/vllm-omni/commit/473da2cf8228fa26285731fe22d1325900d89ae9)

- **作者**: Sy03
- **时间**: 2026-09-21T19:09:19Z
- **提交信息**: [Perf][Qwen3-TTS] Enable event-driven orchestration by default (#7088)

Signed-off-by: Sy03 <1370724210@qq.com>

### [60a933b](https://github.com/vllm-project/vllm-omni/commit/60a933b9ab522a02d83002fde0342c27a54217ef)

- **作者**: Sy03
- **时间**: 2026-09-21T18:56:06Z
- **提交信息**: [Model] Default Qwen3-TTS to experimental Model Runner V2 (#7930)

Signed-off-by: Sy03 <1370724210@qq.com>

### [d8d162d](https://github.com/vllm-project/vllm-omni/commit/d8d162d810c622319015090455a9035d4e2cc275)

- **作者**: vOv
- **时间**: 2026-09-21T17:31:22Z
- **提交信息**: [Core][Diffusion] Add pause_generation(mode="keep") for diffusion stages (#7685)

Signed-off-by: cr-gao <gaochenrui@sjtu.edu.cn>

### [62b1514](https://github.com/vllm-project/vllm-omni/commit/62b15142bdab8c80eb83473f65e51774d1a2521b)

- **作者**: NumberWan
- **时间**: 2026-09-21T16:26:54Z
- **提交信息**: [Model] Integrate AURA into Full-Duplex Runtime (#7633)

### [d397a2f](https://github.com/vllm-project/vllm-omni/commit/d397a2f547a368643f10e2b0dd65ccc5bcf48edb)

- **作者**: wuli666
- **时间**: 2026-09-21T16:24:42Z
- **提交信息**: [Bugfix] Refresh duplex client defaults after session updates (#7784)

Signed-off-by: wuli666 <421774554@qq.com>

### [279b1b9](https://github.com/vllm-project/vllm-omni/commit/279b1b96879469047cacbf3fc688eba02cb7a291)

- **作者**: wangyu
- **时间**: 2026-09-21T15:55:00Z
- **提交信息**: [Bugfix] Isolate weekly CPU tests from inherited attention env and hf_api mocks (#7565)

Signed-off-by: wangyu <410167048@qq.com>
Signed-off-by: [Your Name] <your.email@example.com>
Signed-off-by: [Your Name] [Your Email]

### [2c2cffd](https://github.com/vllm-project/vllm-omni/commit/2c2cffd2aacda119e1708a6302163d9b9684f071)

- **作者**: 0z5a
- **时间**: 2026-09-21T15:26:14Z
- **提交信息**: [Bugfix] Preserve NextStep rectangular latent dimensions (#7853)

Signed-off-by: 0z5a <dezhen.lu@student.uni-tuebingen.de>

### [e01655f](https://github.com/vllm-project/vllm-omni/commit/e01655f4a9051d5fc2becf94fd83ed90cbbd0ec0)

- **作者**: akshatvishu
- **时间**: 2026-09-21T15:09:32Z
- **提交信息**: [BugFix] Fix diffusion TTS voice error responses (#7798)

Signed-off-by: akshatvishu <akshatnayak197@gmail.com>

### [ef644b6](https://github.com/vllm-project/vllm-omni/commit/ef644b611288e7d0c415e28c3420424fe4a61261)

- **作者**: wangyu
- **时间**: 2026-09-21T14:45:32Z
- **提交信息**: [CI/Build] Promote LingBot-Video dense smoke to ready/merge and wire L4 expansion (#7892)

Signed-off-by: wangyu <410167048@qq.com>

### [44ea368](https://github.com/vllm-project/vllm-omni/commit/44ea3688433cb068a398e38067a493bff043a8c6)

- **作者**: WeiQing Chen
- **时间**: 2026-09-21T14:18:28Z
- **提交信息**: [Doc] Update vLLM-Omni WeChat QR code (#7911)

Signed-off-by: David Chen <530634352@qq.com>

### [856d19f](https://github.com/vllm-project/vllm-omni/commit/856d19f42cfccb1ae97aea1131b89662368baadb)

- **作者**: Zhou Taichang
- **时间**: 2026-09-21T13:12:00Z
- **提交信息**: [Benchmark] Add LingBot-World realtime streaming benchmark (#7645)

Signed-off-by: tzhouam <tzhouam@connect.ust.hk>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [fa1d03a](https://github.com/vllm-project/vllm-omni/commit/fa1d03ab8d5111b81968e2173bf61981c43aa0c7)

- **作者**: Weiming Liao
- **时间**: 2026-09-21T13:07:21Z
- **提交信息**: [Frontend] Add MiniMax-H3 latent editing workflows (WF-05) (#7898)

Signed-off-by: chen hongwei <1792043268@qq.com>
Signed-off-by: Weiming Liao <liaowm5@gmail.com>
Co-authored-by: chen hongwei <1792043268@qq.com>
Co-authored-by: chen hongwei <54873389+avicii-forever@users.noreply.github.com>

### [e5c0afc](https://github.com/vllm-project/vllm-omni/commit/e5c0afc99432dba767dcb66f28b0fb9aa43ab1af)

- **作者**: tsinghua-code
- **时间**: 2026-09-21T12:21:46Z
- **提交信息**: [Model] Enable online FP8 linears for LingBot World (#7549)

Signed-off-by: tsinghua-code <zr-liu25@mails.tsinghua.edu.cn>

### [5e28163](https://github.com/vllm-project/vllm-omni/commit/5e28163ba5b329f5bed36272aca2f9f65e53ef88)

- **作者**: zhumingjue138
- **时间**: 2026-09-21T11:03:18Z
- **提交信息**: [Test] add stability test case for High-priority model (#7571)

Signed-off-by: zhumingjue <zhumingjue@huawei.com>

### [5356357](https://github.com/vllm-project/vllm-omni/commit/5356357cf0bf95a7818ba2452b2248b5a0e59af2)

- **作者**: Zhou Taichang
- **时间**: 2026-09-21T11:00:46Z
- **提交信息**: [LingBot World] Shard the streaming VAE decode across the Ulysses ranks (#7651)

Signed-off-by: tzhouam <tzhouam@connect.ust.hk>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [8efd3c2](https://github.com/vllm-project/vllm-omni/commit/8efd3c2f6dbf3fd3852168d77852c3528c7932fc)

- **作者**: wtz2333
- **时间**: 2026-09-21T09:02:15Z
- **提交信息**: [Feature] Add experimental LingBot World last-step KV reuse (#7816)

Signed-off-by: wtz2333 <2955110911@qq.com>

### [fb2e353](https://github.com/vllm-project/vllm-omni/commit/fb2e3535af3745d27f6932ba81439e784f39c459)

- **作者**: shiyichuan
- **时间**: 2026-09-21T09:01:03Z
- **提交信息**: [Bugfix][Engine] Preserve text_encoder_tp_size in OmniEngineArgs (#7652)

Signed-off-by: mershi <mershi@tencent.com>
Co-authored-by: mershi <mershi@tencent.com>

### [84977d9](https://github.com/vllm-project/vllm-omni/commit/84977d95436f14c347b4284a23f6a64c3015c190)

- **作者**: WeiQing Chen
- **时间**: 2026-09-21T08:26:09Z
- **提交信息**: [Bugfix][MiniMax-H3] Fix Hopper keyframe and modulation precision (#7913)

Signed-off-by: david6666666 <530634352@qq.com>

### [154a1f2](https://github.com/vllm-project/vllm-omni/commit/154a1f25f537c19180ce4abfdcf3163db7c57956)

- **作者**: Ding Zuhao
- **时间**: 2026-09-21T07:29:24Z
- **提交信息**: [Bugfix] Honor the requested output canvas in BAGEL img2img (#7287)

Signed-off-by: Ding Zuhao <e1583181@u.nus.edu>
Co-authored-by: Cursor <cursoragent@cursor.com>

---
