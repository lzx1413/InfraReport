# GitHub Stars 合并报告 - 2026-09-04

**合并日期**: 2026-09-05
**监控日期**: 2026-09-04
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


**报告日期**: 2026-09-05
**监控日期**: 2026-09-04
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2192
- **最后更新**: 2026-09-04T09:26:00Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: 顾立辉

## AI分析总结

### 提交分析总结

**1. 主要更新类型**  
功能新增（Feature）与硬件适配优化。该提交为VeOmni框架新增了对Qwen3.5 MoE模型在昇腾（Ascend）硬件上使用Muon优化器进行训练的支持。

**2. 关键变更点与项目方向的关系**  
- **核心变更**：在优化器（optim）与检查点（ckpt）模块中，为Qwen3.5 MoE架构适配了Muon优化器，并确保其在昇腾平台上的正确执行与状态保存/恢复。  
- **与项目方向关联**：VeOmni的定位是“模型中心化的分布式训练配方集”，旨在跨多种硬件（如GPU、昇腾）和模型架构（稠密/稀疏MoE）提供高效训练方案。此次提交直接扩展了“配方”的覆盖范围，将前沿的MoE模型（Qwen3.5）与新兴优化器（Muon）结合，并下沉到昇腾这一国产算力生态，强化了项目“多模态、多硬件、多架构”的通用性承诺。

**3. 对项目的影响与潜在意义**  
- **生态扩展**：显著提升VeOmni对昇腾开发者的吸引力，降低在国产芯片上训练大型MoE模型的技术门槛。  
- **训练效率**：Muon优化器在MoE场景下通常能带来更好的收敛性与显存效率，该支持有助于用户复现或探索Qwen3.5的高效训练。  
- **检查点兼容性**：确保昇腾上训练的模型检查点可正确保存与加载，为长训、断点续训及模型发布提供基础保障，增强框架的工程可靠性。

**4. 值得关注的技术点**  
- **MoE + Muon的适配细节**：MoE模型的稀疏激活特性与Muon（基于矩阵正交化更新）的结合需要特殊处理，如专家并行下的梯度通信与优化器状态分布，该提交可能涉及对昇腾通信原语的优化。  
- **昇腾算子映射**：Muon中的矩阵分解或正交化操作需映射到昇腾的算子库，可能包含自定义算子或性能调优，这是跨硬件支持的关键难点。  
- **检查点格式统一**：在昇腾上保存的检查点需与现有框架格式兼容，便于模型在不同硬件间迁移，这体现了VeOmni“配方”的可移植性设计。

**5. 对项目发展的影响（结合README背景）**  
VeOmni以“配方动物园”为核心，强调通过可复现的配置组合（模型+数据+优化器+硬件）来简化任意模态模型的训练。此次提交正是这一理念的落地：  
- **横向扩展**：新增一个“配方”实例（Qwen3.5 MoE + Muon + Ascend），丰富了配方库的多样性，吸引更多研究者和工程师贡献或使用。  
- **纵向深化**：针对昇腾的专项优化，表明项目正从“支持主流GPU”向“全硬件覆盖”演进，有助于在国产算力政策背景下获得更广泛的工业界采用。  
- **技术引领**：率先支持Qwen3.5这类最新开源模型，体现了项目对前沿模型训练的快速响应能力，巩固其作为分布式训练基础设施的领先地位。

**总结**：该提交是VeOmni在“多硬件适配”与“前沿模型支持”双维度上的重要一步，通过解决MoE+Muon在昇腾上的工程难题，既增强了框架的实用性，也为其生态扩张奠定了技术基础。

## 详细提交记录

### [a281fb9](https://github.com/ByteDance-Seed/VeOmni/commit/a281fb9b254e072db3e3d92c9ef034fb7ff3a355)

- **作者**: 顾立辉
- **时间**: 2026-09-04T07:45:19Z
- **提交信息**: [optim, ckpt] feat: support Qwen3.5 MoE Muon training on Ascend (#1036) (#1092)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-09-05
**监控日期**: 2026-09-04
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2779
- **最后更新**: 2026-09-04T09:54:05Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 3
- **主要提交者**: blian6, PengGao, Yang Yong (雍洋)

## AI分析总结

# LightX2V 提交分析总结

## 1. 主要更新类型

本次提交包含**功能新增**（Ascend NPU 的 MindIE-SD 编译后端与 MiniMax-H3 融合 RoPE）、**Bug 修复**（SekoTalk-AR 缓存 RoPE 参数缺失）以及**性能优化**（通过算子融合大幅降低内核数量与通信开销），整体以昇腾硬件适配和推理效率提升为核心。

## 2. 关键变更点与项目方向的关系

- **MindIE-SD 编译后端**：在运行时 RMS/ROPE 融合基础上，进一步将 DiTBlock 中的 adaln、swiglu、residual-gate 等算子编译为三个融合内核，同时将 Ulysses A2A 保留在 eager 路径以避免 HCCL alltoallv 退化。这与 LightX2V 作为轻量视频生成推理框架的目标高度一致——通过算子级优化降低 NPU 上的推理延迟。
- **MiniMax-H3 融合 RoPE**：为 Ascend USP4 架构实现 split-half 部分融合，属于硬件特定优化，扩展了模型在国产芯片上的支持范围。
- **SekoTalk-AR 修复**：补齐非序列并行 AR 缓存 RoPE 调用中缺失的 `phase` 参数，属于正确性修复，确保模型在特定配置下可正常运行。

## 3. 对项目的影响与潜在意义

性能数据（kernel 数量 -15.3%、kernel 时间 -9.9%、通信 -35%）表明编译后端能显著降低 NPU 推理开销，尤其消除了 alltoallv 这一严重性能瓶颈。15 秒 profiling 显示通信占 kernel 时间 57.6%，提示 Ulysses 级别通信是当前主要瓶颈，且随序列长度线性增长——这为后续优化指明了方向（如通信-计算重叠或序列并行策略调整）。SekoTalk 修复则保障了多硬件环境下模型输出的正确性。

## 4. 值得关注的技术点

- **编译与 eager 混合执行策略**：将计算密集算子编译融合，同时将集合通信保留在 eager 路径，避免 HCCL 因 `split_sizes` 推断退化到变长 alltoallv 路径，这一设计思路值得借鉴。
- **算子融合的量化收益**：Mul -90%、Add -77%、Silu -99%、IndexSelect -87% 的消除幅度展示了编译后端对算子链的深度优化能力。
- **CANN profiler 驱动的优化方法**：以 warmup+profiled step 的标准化测量方式验证优化效果，体现了严谨的性能工程实践。

## 5. 对项目发展的影响

LightX2V 定位为轻量视频生成推理框架，本次提交显著增强了其在**昇腾 NPU 生态**的竞争力：通过编译后端实现接近手写内核的性能，同时保持框架的灵活性。MiniMax-H3 的硬件适配扩大了支持的模型范围，而通信瓶颈的量化分析为未来优化提供了数据基础。整体上，这些变更推动项目向**多硬件后端 + 模型级优化**的方向演进，有助于吸引更多昇腾用户并提升框架在国产算力平台上的实用性。

## 详细提交记录

### [0318b44](https://github.com/ModelTC/LightX2V/commit/0318b4400624a293a41d4056449088678f7f4634)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-09-04T09:52:59Z
- **提交信息**: [Train]: remove bucket_by_size & fix qwen dmd2 (#1478)

### [5c22582](https://github.com/ModelTC/LightX2V/commit/5c2258254e448f4a64c7d584fec1771eae9586a0)

- **作者**: blian6
- **时间**: 2026-09-04T09:37:21Z
- **提交信息**: feat(ascend): add MiniMax-H3 fused RoPE and MindIE SD compile backend (#1471)

## Summary

Enable an optional MindIE-SD compile backend and a fused partial
split-half RoPE for MiniMax-H3 on Ascend NPU (USP4). The MindIE compile
fuses the remaining DiTBlock ops (adaln / swiglu / residual-gate) on top
of the runtime rms/rope fusion, and keeping the Ulysses A2A on the eager
path removes an HCCL alltoallv regression. Kernel-level (CANN profiler,
rank0): kernel count **-15.3%**, kernel time **-9.9%**, communication
**-35%**.

## Performance (kernel-level)

Measured with CANN profiler (warmup 5 + 1 profiled step, rank0, 768p
t2av, USP4, 4x Ascend950PR). Compile vs the runtime-fused config
(`npu_rms_norm` + `minimax_h3_npu_rope`, no compile):

| metric (5s) | runtime-fused | MindIE compile | change |
|---|---|---|---|
| kernel count | 3600 | 3050 | **-15.3%** |
| kernel time | 3968ms | 3576ms | **-9.9%** |
| communication | 962ms | 621ms | **-35%** |

The DiTBlock op chains are replaced by three fused kernels, and the
Ulysses A2A regression is removed:

- new fused kernels: `swiglu` 50x32ms, `gather_scale_shift` 200x19ms,
`gather_residual_gate` 100x11ms
- eliminated op chains: Mul **-90%**, Add **-77%**, Silu **-99%**,
IndexSelect **-87%**
- `hcom_alltoallv` **eliminated**: tracing `dist.all_to_all_single`
infers `split_sizes=[1,1,...]` and degrades HCCL to the variable-length
alltoallv path (200-270ms/call); with the collective kept on the eager
path it stays on the fixed-size alltoall and overlaps better with the
compiled compute (-35% communication)

15s: `swiglu` 93.7ms + `gather_scale_shift` 55.5ms +
`gather_residual_gate` 32.3ms replace the 99.4ms old Silu/split/Add/Mul
chain; kernel count -550 (-15.3%), kernel time -333ms (-0.7%).
Communication dominates the 15s kernel time (57.6%, 28002ms/48584ms) — a
Ulysses-level bottleneck that grows linearly with sequence length and is
outside compile's reach.

Known residual: the gate-msa residual (`residual + gate * attn_out`)
spans a graph-break boundary (its `index_select` lands in subgraph 1,
the attention output in subgraph 6) and cannot be fused by a single
pattern; a dedicated 2D residual-gate kernel was prototyped and reverted
(its contiguous-copy and launch overhead outweighed the ~15ms/step
fusion saving). All other DiTBlock ops are fused.

## Changes

- Add `minimax_h3_npu_rope` (Ascend): fuses the 96/128 rotate-half
rotary part through MindIE-SD `rotary_position_embedding` (input guards
live in mindiesd); falls back to `TorchRealRope` when mindiesd is absent
- `BaseTransformerInfer`: support `compile_backend` ("default" |
"mindie") and `compile_dynamic` config keys; reuse ONE MindieSDBackend
instance to avoid BACKEND_MATCH recompilation and silent eager fallback
- Keep `TorchUlyssesA2A.exchange` out of the compiled graph
(`torch._dynamo.disable`) so HCCL keeps the fast fixed-size alltoall.
This changes compiled-graph behavior for all Ulysses + compile users
across platforms (the collective now runs eager)
- Add ascend_npu configs: `minimax_h3_t2av_sp_compile_5s.json`,
`minimax_h3_t2av_sp_compile_15s.json`

## Usage

`mindiesd` is an optional out-of-tree dependency. Without it, both the
compile backend and the fused rope degrade gracefully to the default
`torch.compile` / `TorchRealRope` paths. Enable the feature in the model
config:

```json
"rope_type": "minimax_h3_npu_rope",
"use_compile": true,
"compile_backend": "mindie"
```

## Verification

- mindiesd op path numerically matches rotate-half semantics (bf16,
within 1 ULP of the fp32 reference); no-mindiesd fallback equals
`TorchRealRope` bitwise
- `ruff check` and `ruff format --check` pass on all changed files

---------

Co-authored-by: blian <lianbin@huawei.com>
Co-authored-by: helloyongyang <yongyang1030@163.com>

### [ac22071](https://github.com/ModelTC/LightX2V/commit/ac22071bc0e63e4559504c4734bad57e7cd94fb8)

- **作者**: PengGao
- **时间**: 2026-09-04T08:07:30Z
- **提交信息**: fix(sekotalk-ar): pass phase to cached RoPE (#1477)

## Summary
- pass the missing `phase` argument in non-sequence-parallel AR cached
RoPE calls
- fix argument shifting that caused `missing 1 required positional
argument: local_per_frame`

## Validation
- single-card H100 SekoTalk AR FP8 test completed 60/60 chunks
- FFmpeg exited successfully and generated the MP4 output

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-09-05
**监控日期**: 2026-09-04
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2236
- **最后更新**: 2026-09-04T17:45:19Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: hkz

## AI分析总结

### 提交分析总结

**主要更新类型**：功能新增（文档/设计补充）。

**关键变更点**：新增了针对 MiniMax-H3 模型的 PDD（Product Design Document，产品设计文档），编号关联 PR #515。该文档旨在规划或说明如何将 MiniMax-H3 集成到 VideoX-Fun 的现有视频生成工作流中。

**与项目方向的关系**：VideoX-Fun 的核心是提供多模型（如 CogVideoX-Fun、Wan-Fun）的统一视频生成框架，强调易用性和可扩展性。新增 MiniMax-H3 的 PDD 表明项目正积极扩展对更多前沿视频生成模型的支持，符合其“多模型适配”的长期技术路线。

**对项目的影响与潜在意义**：
- **架构层面**：PDD 的引入意味着未来可能新增一个模型适配模块，需要抽象统一的接口以兼容 MiniMax-H3 的输入输出格式。
- **生态层面**：MiniMax-H3 作为国内头部大模型厂商的产品，其集成将吸引更多开发者，提升项目在中文社区的覆盖度和影响力。
- **风险提示**：目前仅为设计文档，实际代码落地仍需时间，且需关注 MiniMax-H3 的 API 授权与算力成本。

**值得关注的技术点**：
- 文档中可能涉及对 MiniMax-H3 视频生成能力的评测基准（如时序一致性、运动幅度）与现有模型的对比策略。
- 如何复用 VideoX-Fun 现有的扩散模型后处理管线（如 VAE 解码、视频超分）是技术难点。

**对项目发展的影响**：该提交是项目从“单一模型工具”向“多模型平台”演进的关键一步。通过提前规划 PDD，项目团队能更系统地管理多模型兼容性，降低后续集成风险。长期看，这有助于 VideoX-Fun 成为类似 Hugging Face Diffusers 的通用视频生成中间层，巩固其作为阿里云 PAI 生态入口的地位。

## 详细提交记录

### [968f0e2](https://github.com/aigc-apps/VideoX-Fun/commit/968f0e2192ba4c7a12868bf36d73260d135424ca)

- **作者**: hkz
- **时间**: 2026-09-04T09:02:21Z
- **提交信息**: Add PDD for MiniMax-H3 (#515)

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-09-05
**监控日期**: 2026-09-04
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 6336
- **最后更新**: 2026-09-04T22:10:58Z

## 提交统计

- **昨日提交总数**: 7
- **提交者数量**: 7
- **主要提交者**: Brian K. Ryu, Wei Zhao, Cindy Zhang

## AI分析总结

# FlashInfer 昨日提交分析总结

## 主要更新类型

- **功能新增**：GVR V2 top-K后端、warp级split-K BF16 GEMM、实验性API/后端策略框架
- **性能优化**：TRTLLM ragged prefill跳过active rows检查
- **Bug修复**：V1 GVR阈值正确性问题、CI token权限问题
- **CI/基础设施**：CUDA 13 cuTile编译器配置、测试硬件适配

## 关键变更点与项目方向

1. **GVR V2自采样后端**：从TRT-LLM移植，采用Floyd-Rivest风格阈值阶梯和单次流式遍历，消除主机同步，支持CUDA Graph，与项目"高性能推理内核"目标高度一致。
2. **Warp级split-K BF16 GEMM**：针对SM100/103低M形状优化，解决vLLM fused-A路径性能瓶颈，体现对新一代硬件和实际部署场景的持续优化。
3. **实验性API/后端策略**：建立正式框架区分实验与稳定功能，支持快速迭代新内核（如SM12x）而不影响核心稳定性，是项目治理结构的重要完善。
4. **TRTLLM性能回归修复**：通过可选跳过检查消除CUDA同步，默认关闭保持向后兼容，体现对生态兼容性的重视。

## 项目影响与意义

- 性能优化提交直接解决用户报告的生产问题，提升TRTLLM MLA场景效率
- 新内核后端显著扩展了SM100/103上的解码性能覆盖
- 实验性框架为快速演进提供制度保障，平衡创新与稳定
- CI修复确保自动化测试链路可靠运行

## 值得关注的技术点

- GVR V2的**设备端长度读取**实现sync-free和CUDA-graph安全
- Warp split-K的**cp.async环形缓冲**配合L2 evict_first提示
- ptxas 13.0工作区处理（非法指令规避）
- 实验性后端通过环境变量门控自动选择

## 对项目发展的影响

这些提交体现了FlashInfer作为高性能推理内核库的成熟化进程：持续针对新一代GPU架构优化、建立清晰的API演进策略、完善CI基础设施，同时保持对现有生态（TRTLLM、vLLM）的兼容与性能支持，推动项目向生产级、架构前瞻性的方向发展。

## 详细提交记录

### [e48ab39](https://github.com/flashinfer-ai/flashinfer/commit/e48ab3982e491799b609d7f69809ea3a743317a2)

- **作者**: Wei Zhao
- **时间**: 2026-09-04T22:10:53Z
- **提交信息**: Add option to skip checking active rows in TRTLLM ragged prefill (#4931)

## 📌 Description

Fix performance regression mentioned in issue
https://github.com/flashinfer-ai/flashinfer/issues/4928 in TRTLLM MLA
ragged prefill caused by CUDA synchronization for checking active rows
in query_lens and kv_lens by adding option to skip the checks so that
the guarantee can be handled outside the kernel API. The flag is by
default False and thus will have no impact on existing behavior.

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
* Added an option to skip empty-row activity checks for ragged attention
operations.
  * Added support for configuring this option in trace-based workflows.
* Added validation to prevent combining the skip option with CPU
sequence-length mirrors.

* **Tests**
* Added coverage for skipped activity checks, CUDA graph capture and
replay, output consistency, and invalid option combinations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Wei Zhao <weizha@oci-aga-slurm-1-vscode-02.cm.cluster>
Co-authored-by: Wei Zhao <weizha@oci-aga-slurm-1-vscode-02.cm.cluster>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [8613260](https://github.com/flashinfer-ai/flashinfer/commit/8613260ab8793c30e05c7de941773aac502c9be2)

- **作者**: Mingyang Wang
- **时间**: 2026-09-04T21:22:03Z
- **提交信息**: ci: provision cuTile compiler in CUDA 13 images (#4939)

<!-- .github/pull_request_template.md -->

## 📌 Description

This is Stage 1 of a staged CUDA 13 cuTile CI rollout.

- Keep one compiler-only TileIRAS dependency list shared by the build
backend and CI-image installer.
- Install that compiler chain with `--no-deps` only when `CUDA_MAJOR ==
13`, before the final cuDNN override.
- Extend image smoke to require the cuTile API, package metadata,
compiler discovery, and a runnable compiler for CUDA 13 images.
- Validate that installed `nvidia-cuda-runtime*` distributions match the
requested CUDA major for every image.
- Preserve ordinary image smoke and availability-based cuTile skips for
CUDA 12 images.

NVIDIA requires a CUDA 13.1+ compiler toolchain for cuTile. Treating a
CUDA 12.9 runtime plus CUDA 13 TileIRAS as official cu129 support would
create a hybrid environment, so compiler provisioning is intentionally
limited to CUDA 13.

The rollout is split because pull-request Docker jobs build candidate
images but do not publish them, while PR GPU tests consume published
tags. After this stage merges and the multi-architecture cu130 image/tag
update is available, a separate Stage 2 PR will enable one fail-closed
cu130 GPU lane.

## 🔍 Related Issues

No public issue.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

Changed-file hooks passed for all six files in this PR, including mypy,
Ruff check, and Ruff format. The full-repository hook suite was not run.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

Targeted validation:

- `python -m pytest -q tests/test_cuda_tile_ci.py`: 12 passed.
- Bash syntax, ShellCheck, Python compilation, and
`ci/validate_cuda_versions.py`: passed.
- Native amd64 and arm64 no-cache cu130 image builds: image smoke
passed.
- B200 cu130 execution: preflight passed and eight focused cuTile cases
executed with zero skips.
- Cu129 image validation: ordinary smoke passed with cuTile remaining
availability-skipped.

The full repository test suite and hosted PR CI have not been run for
this branch yet.

## Reviewer Notes

This PR intentionally contains image provisioning and smoke enforcement
only. It does not change the PR GPU matrix or add the fail-closed
test-runner preflight. Those changes must wait until the cu130 image
produced from this stage is published and adopted in
`ci/docker-tags.yml`; enabling them against the current published image
would bootstrap-fail because it lacks TileIRAS.

The project dependency remains bare `cuda-tile>=1.4.0`. The CI installer
does not resolve `cuda-tile[tileiras]`, avoiding transitive CUDA runtime
packages that could conflict with the Torch-selected runtime.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

- **New Features**
- CUDA 13 environments now automatically install the required CUDA Tile
compiler dependencies.
- Added validation that the CUDA Tile compiler, compiler toolchain, and
CUDA runtime distributions are correctly installed and compatible.

- **Bug Fixes**
- Improved consistency of CUDA Tile dependency installation across
supported build and container workflows.

- **Tests**
- Added comprehensive CI coverage for dependency setup, compiler
discovery, runtime compatibility, and failure scenarios.


<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Jonathan Dierksen <1507580+dierksen@users.noreply.github.com>

### [df8b5c1](https://github.com/flashinfer-ai/flashinfer/commit/df8b5c1745c51f44b1e8a492b11c3f6cb157cfd2)

- **作者**: Dhiraj Reddy (cuDNN/FlashInfer)
- **时间**: 2026-09-04T17:56:39Z
- **提交信息**: feat(topk): self-sampling GVR V2 backend (SM100/103/107), oracle-tracking auto, and the V1 threshold repair (#4811)

# feat(topk): self-sampling GVR V2 backend, oracle-tracking `auto`, and
the V1 threshold repair

Three commits, one arc: port TRT-LLM's self-sampling GVR V2 top-K decode
as a new `top_k_varlen` backend, make `backend="auto"` track the
measured per-config winner, and fix the correctness bug in the existing
V1 `gvr` backend that the new benchmark sweep uncovered.

## 1. `gvr_2` — self-sampling GVR V2 port (NVIDIA/TensorRT-LLM#17821,
commit `ed94d4cfbf`)

**Algorithm** — V1 GVR guesses its selection threshold from the previous
step's `pre_idx` hint and pays full-row refinement rescans when the hint
is stale. V2 instead derives a *bracketed ladder* of candidate
thresholds from an in-kernel sample of the row itself
(Floyd–Rivest-style) and resolves exact, tie-interchangeable top-K in a
**single streaming pass**; exactness is guaranteed by count-crossing
invariants, never by the estimate, and the hint survives only as a
degenerate-case anchor. Four kernel families (streaming `main` with
multi-CTA SPLIT, register-resident `reg`/`regimg`, clustered
`clus`/`reg_clus`) are chosen by a pure host dispatch `route(b, n, npad,
k)`; per-request lengths are read **on device**, so one launch serves
the whole ragged batch — no prepare kernel, no LJF sort, no host reads
(sync-free and CUDA-graph safe; the length envelope comes from the
logits row width).

**Port notes**
- `flashinfer/topk_varlen/kernels/gvr2_topk_decode.py` (device) and
`gvr2_topk_host.py` (dispatch/workspace/entry) are near-verbatim
upstream drops, excluded from ruff/mypy like the repo's other verbatim
kernel ports so future syncs stay mechanical. Local changes: module
rename, provenance notes, a `_persist()` hook routing the four
`get_compiled*` builders through the persistent CuTe-DSL kernel cache
(the upstream compile closures already use `--enable-tvm-ffi` + fully
symbolic shapes, matching the cache's TVM-FFI reload convention), and a
fixed missing kv-arg in the `regclus_topk` debug entry.
- Backend contract: fp32 logits only (bf16/fp16 are an upstream
follow-up), `top_k ∈ {512, 1024, 2048}`, `compress_ratio ∈ {1, 4}`,
`pre_idx` required with width == `top_k`, datacenter Blackwell
(sm_100/103). The ~21 MB per-device workspace slab is zero-initialized
once and self-restoring; multi-stream callers can pass
`workspace={"gvr2_workspace": ...}`.
- Upstream caveat found by this PR's adversarial tests and reproduced
**bit-identically by the TRT-LLM implementation**: literal `+inf` logits
may not be selected (at least in the clustered-register family); all
finite values — including 3.1e38, above the kernel's 3e38 pad sentinel —
and `-inf` are tie-aware exact. Documented in the API docs + a
non-strict `xfail` (`test_gvr2_plus_inf_upstream_caveat`) that flips
visible if a future upstream sync fixes it. Same class as upstream's
implementation-specific NaN ordering.

**Performance** (B200, fp32, CUDA-graph timing, tie-aware output
validation before every timing; 213 configs across uniform/mixed/short
lengths, K ∈ {512, 1024, 2048}, B ∈ [1, 256], N ∈ [1K, 128K], cr ∈ {1,
4}, next_n ∈ {1, 2}):

| vs backend | geomean | gvr_2 faster | range |
|---|---|---|---|
| `gvr` (existing, LB) | **2.58×** | 210/211 | 0.47–6.23× |
| `gvr` (non-LB) | 3.80× | 210/211 | 0.76–10.94× |
| `radix` (CuTe DSL) | 2.13× | 211/213 | 0.30–10.05× |
| `radix_cutlass` | 3.29× | 211/213 | 0.56–5.92× |
| TRT-LLM upstream twin (port parity) | **1.00×** | — | 0.95–1.05× |

The only losing regime is batches whose rows are mostly barely longer
than K (upstream's own documented short-row trade-off).

## 2. Shape/dtype-aware `auto` (oracle-tracking)

The previous static gvr-first `auto` never reached `gvr_2`, always
picked `gvr` for hinted bf16/fp16 where `radix` wins by up to 2.8×, and
never reached `radix_cutlass` in its fp32 big corner (up to 2.8×). The
new ranking uses only capture-stable host facts (dtype, N, B — never
`seq_lens` contents, which would cost a D2H sync), derived from a
500+-cell sweep:

1. hinted fp32 → **`gvr_2`**;
2. `gvr` outranks `radix` only when `B·N ≥ 2²²` (fp32) / `2²³`
(bf16/fp16);
3. `radix_cutlass` outranks `radix` only in the fp32 corner `N ≥ 65536`
and `B·N ≥ 2²³`; in half precision `radix` always leads.

**Validated on 100 off-grid configs** (shapes never used to fit the
thresholds), regret = t(auto's pick) / t(fastest backend):

| policy | geomean | max | oracle hits |
|---|---|---|---|
| new | **1.004×** | 1.16× | 97/100 |
| old | 1.317× (hinted 1.694×) | 3.05× | 55/100 |

Documented static blind spot: mostly-short rows inside a wide N favor
`radix` but are indistinguishable without reading `seq_lens`; such
callers should pass `backend="radix"` explicitly.
`benchmarks/bench_topk_varlen_gvr2.py` (new comparison benchmark, with
an upstream-twin mode) gained `--dtype`; the bf16/fp16 sweeps drove
rules 2–3.

## 3. V1 `gvr` threshold-search repair (folded from #4813)

This PR's sweep found the existing `gvr` backend shipping silently wrong
top-K when its Phase-2 threshold search terminates without converging:
identity indices `row[0:K]` on degenerate hint brackets, or underfilled
rows (stale/−1 output slots) on hostile hints, tie plateaus wider than
the candidate buffer, and `N_eff = K+1` batches. Fixed by porting the
correctness-relevant subset of three upstream commits FlashInfer's V1
snapshot (~Jul 22) predates:

- NVIDIA/TensorRT-LLM#16457 + #16877: the tie-plateau layer —
adjacent-float bracket terminal (`done=3`) in both
`phase2_secant_search` copies, `s_iscalars (6,)→(8,)`, plateau
flag/ticket, gated Branch-C pad, and a post-Phase-4 fill completing the
row from the bitwise-equal tie class;
- NVIDIA/TensorRT-LLM#18094 (the upstream tip for this kernel, verified
via live GitHub): the two-sided repair — Phase 3's overflow-only retry
becomes an anchored bisection on the signed fp32 order-key image
(provable collapse in ≤32 steps), handling undershoot, restoring to
`val_lo` when a collapse ends under K, and handing collapsed plateaus to
the `done=3` machinery; the degenerate-hint identity emit becomes a
synthetic-bracket fall-through, so correctness no longer depends on the
hint at all.

Both LB paths are covered automatically (`GvrTopKLBKernel` reuses
`GvrTopKKernel.run_one_row`). Before/after: the fix is ~4% *faster*
geomean in the converging common case (the repair shrinks oversized
candidate sets) and turns the previously-wrong regimes correct at 1.1–7×
cost (their old timings were the price of not computing the answer).
Full A/B table and root-cause discussion preserved in the #4813 thread.
Ported with a 3-lens adversarial review against the upstream reference
(port fidelity, DSL/barrier execution, FlashInfer-divergence
interactions) — all clean.

## Testing

- `tests/topk_varlen/test_topk_varlen_gvr2.py` (79 tests): tie-aware
exactness with poisoned pads, short-row identity+pad contract,
degenerate hints, varlen/MTP/compress-ratio grids, zero-kv-slot rows,
per-family admission parity, CUDA-graph capture/replay with in-place
growing `seq_lens`, warmup-then-capture, non-contiguous arena views,
workspace override, adversarial tie/huge-value/denormal patterns, a
>10k-point `route_split == route` dispatch fuzz, and the `+inf` caveat
xfail.
- `tests/topk_varlen/test_gvr_threshold_repair.py` (31 tests): upstream
#18094's regression patterns on the FlashInfer API (hostile/degenerate
hints × K × LB modes, ReLU-sparse plateaus, MTP hostile hints) plus the
FlashInfer-found `N_eff = K+1` case — all fail pre-fix.
- Cross-backend value-multiset consistency and the shape-aware
heuristic-priority unit test (meta tensors, runs off-GPU) extended in
`test_topk_varlen.py`.
- Results: see section 4 for the post-rebase sweep on SM80/89/90/100
(B200 and B100)/107 (Rubin)/120.

## 4. Rubin (SM107) enablement and rebase onto #4621

Rebased onto current `main`, which now includes #4621 (Rubin support for
`top_k_varlen` plus the `radix_filter` backend). Conflicts were confined
to `topk_varlen.py` (docstrings, the backend `Literal`/registration, the
`auto` heuristic body, and the `next_n` validation), `pyproject.toml`,
and `.pre-commit-config.yaml` (both sides added vendored-kernel
exclusions; union kept). Resolutions of note:

- The `next_n`/`seq_lens` grouped-row validation lands as #4621's
`ValueError` raises (they hold under `python -O`); this branch's
equivalent asserts were dropped and its up-front-validation test now
expects `ValueError`.
- `auto` keeps this branch's shape-aware ranking; `radix_filter` stays
explicit-only, with #4621's rationale comment retained.

`gvr_2` on Rubin (commit `feat(topk): enable gvr_2 on Rubin (SM107)`):

- Admission comes through the shared `_GVR_CCS = [100, 103, 107]` list
from #4621; the gvr_2 checker now uses #4621's per-device
`_cute_dsl_ready()` probe instead of the process-wide DSL flag, so a DSL
predating the device degrades `auto` cleanly.
- No kernel changes: the device module uses only family-portable ops (no
`tcgen05` / block-scaled MMA), so the same source compiles for
`sm_107a`; the compile target follows the current device and the
persistent CuTe-DSL cache is arch-namespaced.
- The host router's `148` (B200 SM count, mirrored from the upstream
CUDA dispatch) is documented as an occupancy heuristic only; on Rubin's
208 SMs the same constants are conservative, never incorrect. Per-arch
retuning is a perf follow-up.

Verification after the rebase (full `tests/topk_varlen/`, which now
includes #4621's `test_radix_filter.py`):

| Arch | GPU | `tests/topk_varlen/` at `9f518813` (identical to the
swept tree except one unused loop index in a test) |
|---|---|---|
| SM80 | A100-PCIE-40GB | 54 passed, 203 skipped |
| SM89 | L40S | 54 passed, 203 skipped |
| SM90 | H100 NVL | 54 passed, 203 skipped |
| SM100 | B200 | 252 passed, 3 skipped, 2 xfailed |
| SM100 | B100 | 252 passed, 3 skipped, 2 xfailed |
| **SM107** | **Rubin GR100** | **253 passed, 2 skipped, 2 xfailed** (7
min 19 s cold, including the first `sm_107a` compiles of every gvr_2
family) |
| SM120 | RTX 5080 | 54 passed, 203 skipped |

The skips on SM100/107 are all in `test_radix_filter.py` (two need a
second visible GPU; one wants an async-TMA default that is active on
SM107 but not SM100, hence Rubin's extra pass). The two xfails are the
known upstream caveats (radix_filter's padded-merge tie, gvr_2's
`+inf`). Every gvr_2 test ran on SM100 and SM107.

Basic perf after the rebase (`benchmarks/bench_topk_varlen_gvr2.py`,
fp32, K = 1024, B ∈ {1, 16, 64, 256}, N ∈ {8K, 32K, 128K}, uniform and
mixed lengths, CUDA-graph timing, tie-aware validation before every
timing):

| GPU | vs `gvr` | vs `radix` | vs `radix_cutlass` | gvr_2 wins |
|---|---|---|---|---|
| B100 (SM100) | 2.40× | 2.49× | 3.40× | 24/24 vs each |
| Rubin GR100 (SM107) | 2.31× | 2.55× | 3.37× | 24/24 vs each |

Consistent with the B200 sweep in section 1, and Rubin lands there with
the router's B200 occupancy constants untouched.

## Follow-ups (out of scope)

- Consider an `N_eff`-aware escape for gvr_2's short-row regime if it is
ever promoted for length-skewed workloads.
- bf16/fp16 gvr_2 tracks the upstream roadmap; once ported, the V1 `gvr`
backend's last winning corner (hinted bf16/fp16 at large B·N) disappears
and it can be deprecated.
- Report the `+inf` selection caveat upstream (reproducer in the xfail
test).

AI-assisted (Claude Code).

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

- **New Features**
- Added the GVR V2 backend for variable-length top-k operations on
supported Blackwell hardware.
- Added support for variable sequence lengths, returned values,
workspace controls, warmup, and CUDA Graph workflows.
- Added automatic backend selection based on input shape and data type.
  - Added a configurable benchmark for comparing top-k implementations.

- **Bug Fixes**
- Improved handling of ties, plateaus, sparse results, short rows, and
challenging threshold-search cases.
- Added validation and clearer handling for unsupported configurations.

- **Tests**
- Expanded correctness, consistency, validation, and CUDA Graph
coverage.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## 5. Review follow-up (`ea069804`)

Addresses the open review threads:

* **Row-length clamp on arena views.** `gvr_main`'s varlen prologue
clamped each row's kv-derived length to the row stride; the other three
families clamp to the envelope. It now clamps to the envelope too
(carried in the previously dead `n` launch slot), so an oversized
`seq_lens` value on a wider-stride view can never classify arena columns
in `[width, stride)`. Contiguous inputs are unchanged. New test
`test_gvr2_arena_view_oversized_seq_lens` covers all families; it fails
on the previous kernel for both `gvr_main` parametrisations.
* **Heterogeneous multi-GPU processes.** `run` / `run_ws` / `run_varlen`
re-enter under `torch.cuda.device(logits.device)` when the logits are
not on the current device, so the launcher cache key, the DSL compile
target and the launch agree by construction. Every gvr_2 `cute.compile`
also passes an explicit `--gpu-arch` for the current device: the DSL
otherwise detects its target once per process from device 0, so a kernel
compiled while another device is current was built for device 0's
architecture and failed to load (`cudaErrorNoKernelImageForDevice`). New
test `test_gvr2_logits_on_non_current_device` (exercised with device 0 =
L40S, device 1 = B100; failed before both fixes).
* Benchmark: `mixed`/`short` rows drawn from the documented domain,
GVR-family backends report `n/a` outside `top_k ∈ {512, 1024, 2048}`,
summary no longer requires `fi_gvr2`;
`benchmarks/routines/topk_varlen.py` drops `gvr_2` when `max_seq_len % 4
!= 0`; raw-string regex patterns in tests.
* The `+inf` caveat stays an `xfail` with the upstream tracking issue;
see the thread for the rationale.

**Public API note.** The "potential breaking change" advisory is the
`backend` `Literal` gaining the `"gvr_2"` member. That is additive:
every previously valid call, including positional ones, is unchanged.

## 6. Known kernel defect: DKG issue #58 (`+inf` / NaN dropped) and the
TRT-LLM #18501 port (`8e76f056`)

While validating this port I filed DKG issue #58 (internal GitLab,
`dlarch-fastkernels/dynamic-kernel-generator`) against the upstream
self-sampling GVR V2 kernel: a row containing a literal `+inf` returns a
top-k without it, and NaN is not ranked on top the way `torch.topk`
does. The result does not depend on hint quality (oracle and `-1` hints
fail identically). The `+inf` case is inside the kernel's documented
"finite + inf exact" contract; the NaN case is a torch-parity gap
(upstream documents NaN ordering as implementation-specific).

The kernel owner pointed at TensorRT-LLM PR #18501 as the latest fix.
**Reproduced on this branch and ported here** (register family
`GvrTopkRegKernel.kern`, verbatim apart from our module rename):
count-crossing enforcement when the hint-derived bracket makes the
histogram total fall short of k, a radix-descent escape replacing the
32-step key-space bisection, and the `-inf` fill-lane bound. Before the
port, the two upstream regressions were severe on this branch: a
cold-start hint buffer (all zeros plus an argmax anchor) left 130,304 of
131,072 output slots unwritten across 256 rows, and an in-window `-inf`
in a row's tail column left every row entirely unwritten. After the port
both are exact with every slot written, on B100, B200 and Rubin
(`test_gvr2_high_anchor_hint_completeness`,
`test_gvr2_neginf_tail_completeness`).

**`+inf` closed (`48572ef2` + `274fad3e`):** the kernel owner's
follow-up TensorRT-LLM PR #18625 is ported in full. Its first commit
fixes `GvrTopkRegKernel.kern` (an infinite bracket width fails the
collapse guard and the row takes the key-space escape); its second
commit, written after the repro posted on DKG issue #58, fixes
`GvrRegClusKernel.kern` the same way (bounded guard, and an
infinite-width bracket forces the whole-row `degen` fallback instead of
the collapsed histogram, which used to turn the `+inf` into NaN in the
trash bin and return the true top-K with the `+inf` replaced by the
(K+1)-th value). Verified on B200, B100 and Rubin against upstream at
`9f920331` and through `top_k_varlen(backend="gvr_2")`: `+inf` inside or
outside the bracket sample, K in {512, 1024, 2048}, more `+inf` than K,
the 4 x 32K and 4 x 64K `reg_clus` shapes, with oracle, `-1` and random
hints; `main` and `clus` were already exact.
`test_gvr2_posinf_completeness` (register family) and
`test_gvr2_posinf_reg_clus` (clustered-register family, replaces the
former strict `xfail`) pin it; the API docstring caveat is gone. NaN
ordering stays implementation-specific upstream, although NaN now ranks
on top in every shape tested. Perf of the reg_clus hunks (B100, graph
replay, 5 alternating passes, deterministic to the nanosecond): 4 x 32K
+2.5%, 8 x 32K +2.8% (about 0.15 us each), 16 x 32K and the register
family unchanged.

## 7. `auto` heuristic refinement (`993f6c9e`): radix_filter admission
and the half-precision gvr rule

Measured `auto` against an oracle (fastest explicit backend per cell,
CUDA-graph replay, tie-aware validation) over 4 batch sizes x 5 lengths
(8K..1M) x uniform/mixed/short lengths x hinted/hint-free, fp32 and
bf16, K=1024, on B100/B200 (SM100) and Rubin (SM107). Efficiency =
best-of-all time / auto time (1.00 = auto matched the oracle). Findings
and the resulting rules (one rule set for every arch; the SM100
crossovers are conservative on SM107, where radix_filter's margins are
larger):

* Hinted fp32 (the DSA decode path) was already at 0.95-1.00: gvr_2
first stays. The remaining sub-0.95 cells are rows whose valid length is
within 1-4 of K, a register-family fallback path (perf follow-up).
* Hint-free fp32 sat at 0.83 (SM100) / 0.72 (SM107) and bf16 at 0.86 /
0.82 purely because `radix_filter` was excluded from `auto` while being
the fastest hint-free backend in most cells from 32K columns up. It is
now admitted where it measured fastest: fp32 for N >= 32K (except the
single-row case at N >= 512K) and at every N once B >= 256; half
precision for 32K <= N <= 128K with B <= 16, N >= 128K with B >= 64, and
N <= 8K with B >= 256. Its checker no longer rejects `pre_idx`: the hint
is optional steering for the GVR family, so a hinted caller may use any
hint-free backend, explicitly or via `auto`, exactly as radix and
radix_cutlass already allowed; the hint is accepted and ignored.
* One genuine ranking error: for half precision the old `B*N >= 2^23`
rule chose gvr (V1) at B <= 64 for N >= 512K, where it loses 1.5-7x to
radix (16 rows x 2M: 1518 us vs 210 us). gvr is now chosen for half
precision only when B >= 256 and 32K <= N <= 512K, where it measured
fastest. The fp32 gvr rule is unchanged (it only matters when gvr_2 is
unsuitable; radix_filter ranks ahead of it there).

Re-measured with the refined heuristic (cells >= 0.95 in parentheses;
worst remaining cell listed):

| dtype, K | hint | GPU | before | after | worst cell after |
|---|---|---|---|---|---|
| fp32, K=1024 | yes | SM100 (B100) | 0.95 (46/48) | **0.99** (57/60) |
short B=64 N=8K |
| fp32, K=1024 | yes | SM107 (Rubin) | 0.95 (45/48) | not re-measured
(GPU shared with another job at the time; same rule set, radix_filter's
margins are larger on SM107 so the SM100 crossovers are conservative
there) | |
| fp32, K=1024 | no | SM100 (B100) | 0.83 (19/48) | **0.99** (58/60) |
short B=256 N=128K |
| bf16, K=1024 | yes | SM100 (B100) | 0.92 (29/48) | **0.97** (53/60) |
short B=64 N=1024K |
| bf16, K=1024 | no | SM100 (B100) | 0.86 (26/48) | **1.00** (59/60) |
mixed B=16 N=128K |

`test_backend_heuristic_priority` pins the new boundaries off-GPU; the
public docstring's `backend` section now documents `radix_filter` and
the refined `auto` order.

---------

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [f67bc2e](https://github.com/flashinfer-ai/flashinfer/commit/f67bc2ed555c1ad6a764ad68f7aa9622178e9eae)

- **作者**: Cindy Zhang
- **时间**: 2026-09-04T11:59:10Z
- **提交信息**: test: skip MonoMoE on GPUs with fewer than 128 SMs (#4954)

<!-- .github/pull_request_template.md -->

## 📌 Description

The MonoMoE kernel uses a fixed `GRID_SIZE=128` and requires all blocks
to be co-resident to avoid deadlock. The launcher therefore requires the
GPU's SM count to be at least 128.

Previously, `tests/moe/test_monomoe.py` only checked for SM90a support.
This allowed the tests to run on SM90a GPUs with fewer than 128 SMs,
where they failed at the launcher's expected co-residency check.

  This PR updates `_require_monomoe()` to:

  - Query the target GPU's `multi_processor_count`.
  - Skip MonoMoE tests when the GPU has fewer than 128 SMs.
  - Perform the check before loading or running the kernel.

The existing C++ runtime check remains unchanged as a safety guard for
public API callers.

## 🔍 Related Issues

https://github.com/flashinfer-ai/flashinfer/issues/4953

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
- [x] Verified on an SM90a GPU with 114 SMs. The MonoMoE tests are now
skipped with the expected co-residency requirement instead of failing in
the C++ launcher.

## Reviewer Notes
`_MONOMOE_GRID_SIZE=128` mirrors the fixed kernel configuration in
`csrc/fused_moe/monomoe/src/moe_interface.h`.

A deterministic hardware capability check uses `pytest.skip` rather than
catching the launcher exception and marking it as `xfail`. This also
avoids unnecessary test-data allocation, reference computation, and JIT
loading on unsupported devices.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Tests**
* Updated Monomoe test requirements to skip tests on CUDA devices with
fewer than 128 streaming multiprocessors.
* Preserved existing compatibility checks for supported GPU
architectures and Monomoe availability.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [dbc4741](https://github.com/flashinfer-ai/flashinfer/commit/dbc474144efa9a787bcc4211d053a67887191ac0)

- **作者**: Alex Yang
- **时间**: 2026-09-04T09:15:58Z
- **提交信息**: fix(ci): publish the test scope with GITHUB_TOKEN, not the bot PAT (#4962)

<!-- .github/pull_request_template.md -->

## 📌 Description

A valid scoped command fails in production:

```
gh: Resource not accessible by personal access token (HTTP 403)
##[error]Process completed with exit code 1
```

The `Handle` step runs with `GH_TOKEN` set to the bot PAT. The
`permissions:` block at the top
of the file grants `statuses: write` to **`GITHUB_TOKEN`** — it does not
apply to a PAT — and the
bot PAT carries no commit-status permission. So `POST
/repos/.../statuses/{sha}`, which is how a
scope reaches the test job, is refused.

**Effect: the targeted-testing path does not work at all.** A valid
scoped command fails the
handler, applies no label, and starts no CI. Bare and malformed commands
are unaffected, because
neither touches the statuses API.

**Fix:** publish the scope with `${{ github.token }}`. The PAT is still
required for the label,
because a `labeled` event raised by `GITHUB_TOKEN` does not trigger
workflows. A status needs to
trigger nothing, and `pr-test.yml` already reads it with `GITHUB_TOKEN`.
Splitting by purpose also
keeps the privileged token's blast radius smaller. Alternative would be
granting the PAT
`repo:status`, which needs token administration and widens it instead.

## 🔍 Related Issues

Fixes the scoped path introduced in #4880. Found by driving the merged
handler on throwaway PR
#4959.

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

**This file cannot be tested by CI**, on this PR or any other:
`issue_comment` workflows load from
the default branch, so it takes effect only once merged. That is also
why the bug reached `main`.

Verification therefore has to be post-merge: after this lands, re-issue
a scoped command on #4959
and confirm the scope publishes and `Targeted Unittest` lanes appear.

**Why the pre-merge sandbox missed it.** The scoped path *was* exercised
end to end before merge,
in a scratch repository running byte-identical logic — publish, chunk,
reassemble, matrix, all the
way into the runner's parsed argv. But that mirror ran the step under
`${{ github.token }}`, while
production runs it under the PAT. Faithful in behaviour, wrong in
identity — and authorization is a
property of identity, so no amount of logic fidelity could have caught
it. The check that would
have: diffing the two workflows' `GH_TOKEN:` lines against their
`permissions:` blocks.

## Reviewer Notes

Three lines of substance: one added `env:` entry and two
`GH_TOKEN="$STATUS_TOKEN"` prefixes. No
control flow changes.

<sub>🤖 Generated with [Claude
Code](https://claude.com/claude-code)</sub>


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Fixed commit status publishing for the “run” bot command by using the
appropriate authorization token.
* Preserved workflow-triggering capabilities while ensuring status
updates are successfully posted.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [f32157a](https://github.com/flashinfer-ai/flashinfer/commit/f32157a3a6b7a44f8cb643cb8dabf206d0f25d6d)

- **作者**: Brian K. Ryu
- **时间**: 2026-09-04T08:56:47Z
- **提交信息**: feat: add experimental API/backend policy, `@flashinfer_experimental_api`, and `flashinfer.experimental` namespace (#4880)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

Introduces a formal path for experimental functionality, separating
**experimental APIs** (interfaces that may change or disappear) from
**experimental backends** (implementations not yet ready for stable
support), so fast-moving work — SM12x kernels, new ops from the latest
models, specialized kernels — can land without lowering expectations for
stable core.

**Design.** Experimental APIs live in core marked with
`@flashinfer_experimental_api`; experimental backends live under
`flashinfer/experimental/`.

Automatic experimental backend selection selection is gated:
`backend="auto"` (dispatch and autotuning) skips backends marked
`@experimental_backend` unless
`FLASHINFER_ALLOW_EXPERIMENTAL_AUTO_BACKENDS=1`.

Design record:
[`docs/design_docs/experimental_apis_and_backends.md`](docs/design_docs/experimental_apis_and_backends.md).

Normative policy with a worked example:
[`flashinfer/experimental/README.md`](flashinfer/experimental/README.md).

**Changes**
- `flashinfer/api_logging.py` — `@flashinfer_experimental_api`,
`require_experimental_auto_backends()`, `ExperimentalWarning`.
- `flashinfer/utils.py` — `@experimental_backend` marker;
`backend_requirement` filters marked backends out of `"auto"`
(autotuning inherits it), warns once per API/backend pair, and rejects
unmarked checkers under `flashinfer.experimental` at import.
- **Experimental CI test scope** (with @aleozlx): PR template gains an
Experimental Track section with an `experimental-tests` block;
`@flashinfer-bot run <paths>` publishes the scope as `ci/test-scope-N`
commit statuses (`ci-bot-commands.yml`), and
- Docs: design record, README, `docs/experimental.rst`,
`CONTRIBUTING.md`, `code_review_guidance.md`, experimental + root
`CLAUDE.md`.

**Stable behavior**: unchanged. No backend is marked yet, nothing in
core calls the primitives, and `import flashinfer` does not load
`flashinfer.experimental`.

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
* Experimental APIs and explicitly named experimental backends can now
be used directly, with one-time warnings.
* Automatic backend selection can include experimental backends when
`FLASHINFER_ALLOW_EXPERIMENTAL_AUTO_BACKENDS=1` is set.
  * Added scoped test runs through pull request commands.

* **Documentation**
* Added guidance covering experimental feature usage, support
expectations, lifecycle, testing, and contribution policies.
  * Added experimental features to the documentation navigation.

* **Tests**
* Added coverage for backend selection, warnings, metadata, and exports.
* Experimental features remain excluded from stable API and trace
inventories.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Alex Yang <aleyang@nvidia.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [2534442](https://github.com/flashinfer-ai/flashinfer/commit/25344422a43d09538d446cb5c99bf046096a2da3)

- **作者**: Jiahan Chang (Cyrus)
- **时间**: 2026-09-04T08:14:43Z
- **提交信息**: [feat] Add warp level split k bf16 gemm (#4908)

## 📌 Description

Three changes on the `cute-dsl` BF16 GEMM path for decode-sized M on
SM100/SM103, targeting the low-M shapes vLLM routes to
`dsv3_fused_a_gemm` (vllm-project/vllm#54524), where the existing direct
/ cluster split-K kernels were behind fused-A on most cells.

### 1. Warp split-K kernel
(`flashinfer/gemm/kernels/dense_bf16_gemm_warp_splitk.py`)

- The four compute warps of a CTA each own one K quarter of every tile
and reduce through a shared-memory mailbox; the kernel is the first
`cute-dsl` runner whenever it is eligible (M <= 32, N % 16 == 0, K % 128
== 0, <= 64 K tiles).
- 2 weight-loader warps stream the [N, K] weight through a `cp.async`
ring with an `L2::evict_first` hint (the activation rows every CTA
re-reads stay L2-resident); 1-2 activation-loader warps; 4 compute warps
(`mma.sync` m16n8k16 BF16 -> FP32), each on its own K quarter of every
stage; the first compute warp reduces the four partials and stores BF16
(plus an optional bias, added in FP32).
- The first weight tile is issued before the mbarrier init/CTA barrier,
and the consumer K loop is fully unrolled (the K-tile count is static)
so every `ldmatrix` is `[R_lane + imm]` — a rolled loop kept the stage
index in a vector register and cost 3-16% on K=7168.
- Tactic space: `(output_tile 16|32, token_tile 8|16|32, k_tile 128|256,
stages <= 16, b_loader_warps 1|2)`, bounded to 64 K tiles;
`default_tactic` picks by wave count and CTA residency (counting the 1
KB per-CTA reservation).
- Two ptxas 13.0 workarounds are documented in the source: the
pre-barrier tile stays unhinted and single-stage rings are excluded when
K spans several tiles, because the hinted `LDGSTS` is otherwise
mis-encoded (`[R+UR], desc[UR<odd>]`, illegal instruction).

### 2. `cute-dsl` runner selection refactor
(`flashinfer/gemm/gemm_base.py`)

- One base class, `_CuteDSLBf16Runner`, for the backend's runners:
shared cache-key extras plus `supports_inputs` / `is_tactic_compatible`,
so no runner is special-cased by name.
- `_cute_dsl_bf16_runners(inputs)` owns the ordering: direct where its
measured k=8192 heuristic applies, otherwise warp split-K when eligible,
otherwise cluster split-K; direct is excluded with bias.
- `bf16_gemm_sm100` is now: build the runner list -> `choose_one` ->
check the cached runner and tactic against the real inputs -> fall back
to `runners[0]` with the default tactic. No behavior change for M <= 32;
the CuTe-DSL BF16 autotune cache version is bumped.

### 3. Autotuner

- `TuningConfig.use_cold_l2_graph_replay` (opt-in, set only by the BF16
GEMM config): an untimed warm-up replay and an L2 eviction before the
timed replay, with one input copy per launch, so tactics are ranked from
the cold-L2 state the harness measures. Without it the tuner picks
cluster split-K over the warp kernel at M=9-16 N=1536 K=7168 (8 cells of
the table below).
- One autotune call covers both M ranges: `mm_bf16(backend="cute-dsl")`
no longer pre-dispatches M > 32 to `backend="cublaslt"`.
`_cute_dsl_bf16_runners` lists every runner whatever the real M, the
three CuTe-DSL kernels (M <= 32) plus a fallback-only cuBLASLt runner
(`CuteDSLCublasltFallbackBf16Runner`: M > 32, own cache identity,
cuBLASLt's exact-shape key, pdl ignored), and each returns no tactics
for a profile outside its range. A single large-M warm-up therefore
tunes the low-M kernels on the M <= 32 buckets and cuBLASLt above them,
custom `tuning_buckets` go to the runner owning their range,
`runners[0]` follows the real M, and a cached entry from across the
boundary (or with a tactic illegal for the real M) falls back to it.
vLLM can drop the dedicated 32-token warm-up it added in
vllm-project/vllm#50572.


## 🔍 Related Issues

- vllm-project/vllm#54524 — the fused-A vs FlashInfer benchmark and the
Kimi-K3 / GLM-5.2 shape tables this kernel targets.

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
- [x] All tests are passing (`tests/gemm/test_mm_bf16.py`: 26 passed, 1
skipped on B300 / SM103, nvidia-cutlass-dsl 4.7.0, CUDA 13.0, torch
2.13).

```
pytest tests/gemm/test_mm_bf16.py -q   # 26 passed, 1 skipped
```

Three new `cute-dsl` smoke cases: tuned low-M with bias and PDL (M=8
N=768 K=7168), M=17 on the default tactic (32-token tile with tail rows,
N=2304 K=1536), and K above the warp kernel's tile bound (K=8320, served
by the other runners). Every `cute-dsl` case is also checked elementwise
against an FP32 reference. The M=33 and M=64 `cute-dsl` cases (bias +
PDL) run through the cuBLASLt fallback runner of the same runner set.
Not yet run on SM100/B200.

## 📊 Kernel benchmark

Same method as vllm-project/vllm#54524's
`benchmark_fused_a_vs_flashinfer_bf16.py`: every `(N, K, M)` of the
Kimi-K3 / GLM-5.2 fused-A tables, CUPTI kernel time under CUDA graph
replay with a cold L2 (memset 2x L2 before each launch), PDL enabled,
FP32 reference check on every cell. B300 SXM6 (148 SMs), fused-A from
vLLM at c0cab8ca30. FlashInfer = `mm_bf16(..., backend="cute-dsl")`
after an autotuning pass over the direct, cluster split-K and warp
split-K tactic spaces.

Over 210 measured cases (autotuned): **FlashInfer faster in 209, tie in
1, fused-A faster in 0**. Median fused-A/FlashInfer speedup 1.08x (range
1.00x–1.37x).

| N | K | projection | M | cuBLAS µs | fused-A µs | FlashInfer µs |
FlashInfer vs fused-A | winner |
|---:|---:|:---|:---:|---:|---:|---:|:---:|:---|
| 768 | 128 | f_b_proj (TP16) | 1-16 | 2.91 | 2.32 | 2.14 | 1.02-1.14x |
**FlashInfer** |
| 1536 | 128 | f_b_proj | 1-16 | 3.01 | 2.42 | 2.24 | 1.04-1.10x |
**FlashInfer** |
| 3072 | 128 | f_b_proj | 1-16 | 2.85 | 2.62 | 2.45 | 1.05-1.11x |
**FlashInfer** |
| 7168 | 384 | shared_down_proj (TP16) | 1-8 | 4.13 | 4.14 | 3.62 |
1.12-1.18x | **FlashInfer** |
| 7168 | 768 | shared_down_proj | 1-16 | 5.44 | 5.41 | 5.04 | 1.05-1.09x
| **FlashInfer** |
| 1152 | 1536 | q_b_proj (TP16) | 2-16 | 4.93 | 3.97 | 3.78 | 1.04-1.10x
| **FlashInfer** |
| 2304 | 1536 | q_b_proj | 1-16 | 6.08 | 4.43 | 4.34 | 1.00-1.07x |
FlashInfer |
| 4608 | 1536 | q_b_proj | 1-16 | 6.24 | 5.81 | 5.58 | 1.02-1.08x |
**FlashInfer** |
| 2048 | 2048 | GLM-5.2 q_b_proj | 3-16 | 5.98 | 5.22 | 4.75 |
1.07-1.11x | **FlashInfer** |
| 2624 | 6144 | GLM-5.2 qkv_a_proj | 3-16 | 12.03 | 9.97 | 9.14 |
1.07-1.09x | **FlashInfer** |
| 768 | 7168 | mla_g_proj / shared_gate_up_proj (TP16) | 5-16 | 8.90 |
7.17 | 6.08 | 1.11-1.19x | **FlashInfer** |
| 1536 | 7168 | shared_gate_up_proj / mla_g_proj | 1-16 | 10.03 | 8.08 |
7.46 | 1.06-1.10x | **FlashInfer** |
| 2112 | 7168 | fused_qkv_a_proj | 1-16 | 11.38 | 9.33 | 8.54 |
1.08-1.10x | **FlashInfer** |
| 3216 | 7168 | in_proj_qkvgfab (TP16) | 9-15 | 16.26 | 15.39 | 11.58 |
1.32-1.34x | **FlashInfer** |
| 3584 | 7168 | routed_expert_down_proj | 2-8 | 15.68 | 15.62 | 11.65 |
1.33-1.37x | **FlashInfer** |
| 4224 | 7168 | dense_gate_up_proj (TP16) | 4-8 | 17.41 | 16.99 | 13.02
| 1.30-1.32x | **FlashInfer** |

Medians over the M range per shape; the one tie is N=2304 K=1536 M=11
(4.480 µs both). Five cells are within 1%; the rest win by more than 1%.
The largest gains are the K=7168 shapes (1.08-1.37x) where the kernel
runs within ~6% of the measured cold-read floor of the weight stream.


## Reviewer Notes

- All measurements are from B300 (SM103); SM100/B200 has not been
validated yet, although the runner ordering applies to both.
- The warp kernel is BF16-in / BF16-out only; other dtypes keep their
existing runners.





<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added configurable profiling repetition counts for individual
operations.
* Added an optional cold-L2 CUDA Graph replay mode for more consistent
profiling.
* Added a warp Split-K BF16 GEMM execution path with autotuned tactics
and optional bias support.
* Improved BF16 GEMM runner selection and fallback handling across
supported workloads.

* **Bug Fixes**
* Improved profiling behavior to avoid first-launch initialization and
warmed input batches affecting results.

* **Tests**
* Expanded BF16 GEMM coverage for warp Split-K tuning, tail-row
workloads, larger K dimensions, and strict numerical accuracy.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-09-05
**监控日期**: 2026-09-04
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4328
- **最后更新**: 2026-09-04T23:27:36Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-09-05
**监控日期**: 2026-09-04
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34444
- **最后更新**: 2026-09-04T13:47:21Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-09-05
**监控日期**: 2026-09-04
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


**报告日期**: 2026-09-05
**监控日期**: 2026-09-04
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13053
- **最后更新**: 2026-09-04T23:07:36Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-09-05
**监控日期**: 2026-09-04
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 35477
- **最后更新**: 2026-09-05T00:01:17Z

## 提交统计

- **昨日提交总数**: 34
- **提交者数量**: 27
- **主要提交者**: Faradawn Yang, Cherry_ming, Jialin Ouyang

## AI分析总结

# SGLang 昨日提交分析报告

## 一、主要更新类型

本次共34条提交，涵盖功能新增、Bug修复、性能优化、文档更新、代码重构、CI优化及硬件适配等多方面。其中性能优化和Bug修复占比最高，其次是文档更新和功能扩展，体现了项目在稳定性和效率上的持续投入。

## 二、关键变更点与项目方向

- **功能扩展**：新增response级token ids输出（#34488）、Cosmos3 reasoner推理支持（#33572）、HiCache buffer模式sidecar池（#37424），持续丰富多模态和缓存能力。
- **性能优化**：Qwen3.5 GDN预填充投影布局优化（#36267）、AMD DSv4融合inverse-RoPE（#37658）、SM120显存档位提升decode CUDA-graph上限（#37898），针对不同硬件深度调优。
- **架构重构**：多模态代码重构以适配Rust tokenizer管理器（#34660）、attention-TP序列分片改为per-forward属性（#37546），为Rust核心和序列并行架构演进铺路。
- **内存与缓存修复**：graph borrow池退役时机（#37966）、Mamba radix缓存索引修复（#37836）、混合SWA KV行释放路由（#37876），提升缓存系统正确性。

## 三、项目影响与意义

提交集中体现了SGLang在**多模态推理、缓存效率、硬件适配**三大方向的持续深耕。Rust radix tree核心相关提交（#38021、#37278、#37967）表明项目正加速向Rust高性能内核迁移；DeepSeek-V4 Pro的B200 FP4配置更新（#38026）紧跟前沿模型需求；多个AMD/NPU相关提交（#37580、#38015）显示对非NVIDIA平台的支持力度加大。

## 四、值得关注的技术点

- **Rust核心演进**：多模态代码重构（#34660）和radix tree代码所有者设立（#38021）标志着Rust化进程进入深水区。
- **缓存机制精细化**：write-through pending对齐（#37278）、graph borrow池生命周期管理（#37966）等修复体现了对缓存一致性的极致追求。
- **性能分析增强**：新增scheduler阶段wall time导出（#37636）和滚动利用率计数器（#37461），为系统调优提供更细粒度观测手段。
- **硬件适配深化**：SM120显存档位提升、AMD TOPK v2 kernel跳过等提交展现了针对特定硬件特性的深度优化。

## 五、对项目发展的影响

SGLang正从“高性能推理框架”向**全栈式推理基础设施**演进：通过Rust核心重写提升底层效率，通过多模态支持扩展应用边界，通过细粒度缓存管理优化长上下文场景，通过多硬件适配扩大部署范围。文档更新（#37989、#32172、#37750）同步跟进，确保功能演进与用户认知保持一致。整体来看，项目在保持快速迭代节奏的同时，正逐步夯实底层架构的稳定性和可扩展性，为支撑更大规模、更复杂的推理工作负载奠定基础。

## 详细提交记录

### [8a98f11](https://github.com/sgl-project/sglang/commit/8a98f11078b0fc7beff6f7ce2b1ea59682d83171)

- **作者**: Amy Chang
- **时间**: 2026-09-04T23:45:13Z
- **提交信息**: [feature] Add response-level input/output token ids to chat completions via SglExt (#34488)

### [9c254df](https://github.com/sgl-project/sglang/commit/9c254df8cdbe99ef5f58e7fcd932da052f258538)

- **作者**: PengYuan
- **时间**: 2026-09-04T23:41:47Z
- **提交信息**: [diffusion] fix: preserve mapped courier tensor lifetime (#37965)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [db89f63](https://github.com/sgl-project/sglang/commit/db89f639ef475821e6669958cfe22caf914df022)

- **作者**: YAMY
- **时间**: 2026-09-04T22:13:20Z
- **提交信息**: [GDN] Amortize ReplaySSM checkpoint materialization (#35544)

### [e3eeabb](https://github.com/sgl-project/sglang/commit/e3eeabbbfa9d6a089e3ae7787dfb733915bdea20)

- **作者**: Hanming Lu
- **时间**: 2026-09-04T22:12:55Z
- **提交信息**: [Profiler] Add SGLANG_PROFILE_BY_STAGE_DECODE_MIN_BS to defer the decode-stage capture (#38067)

### [0eff0f7](https://github.com/sgl-project/sglang/commit/0eff0f74608fef93a19a7ab058f1cba5e94cab57)

- **作者**: cctry
- **时间**: 2026-09-04T22:05:57Z
- **提交信息**: Add num_prealloc_ready_tokens to decode load snapshot (#38065)

### [320bdd1](https://github.com/sgl-project/sglang/commit/320bdd1ee2d6aface704c53d4674fd91a671fa74)

- **作者**: Martin Hickey
- **时间**: 2026-09-04T21:26:28Z
- **提交信息**: [Docs] Document --retraction-policy, --return-hidden-states-mode, --language-model-only (#37989)

Signed-off-by: Martin Hickey <martin.hickey@ie.ibm.com>
Co-authored-by: mottopanikeiku <fcetin@hawk.iit.edu>
Co-authored-by: alp <falpercetin@gmail.com>
Co-authored-by: Xinyuan Tong <xinyuantong.cs@gmail.com>

### [3e873c2](https://github.com/sgl-project/sglang/commit/3e873c2110e7ee98aa66fb821828420fdfa2ea47)

- **作者**: alp
- **时间**: 2026-09-04T21:22:05Z
- **提交信息**: [Docs] Clarify OpenAI chat template defaults (#32172)

Co-authored-by: Xinyuan Tong <xinyuantong.cs@gmail.com>

### [fbf8f1d](https://github.com/sgl-project/sglang/commit/fbf8f1dbf69f4f91ac6654383227e82a8a932217)

- **作者**: Yongji Wu
- **时间**: 2026-09-04T18:29:30Z
- **提交信息**: [Fix] Coordinate FullCG prefix variants across DP ranks (#37888)

Co-authored-by: Lianmin Zheng <lianminzheng@gmail.com>

### [c8ba899](https://github.com/sgl-project/sglang/commit/c8ba8996c48831014480c2378f03995ffb8ea724)

- **作者**: Faradawn Yang
- **时间**: 2026-09-04T18:09:24Z
- **提交信息**: Update DeepSeek-V4 Pro for B200 FP4 agentic HiCache DSpark (#38026)

### [010dc95](https://github.com/sgl-project/sglang/commit/010dc955be76cfb07693d2b988023f6b7d30130e)

- **作者**: Jialin Ouyang
- **时间**: 2026-09-04T17:45:53Z
- **提交信息**: [Metrics] Export scheduler stage wall time (#37636)

Co-authored-by: Pranjal Shankhdhar <pranjal.ssh@gmail.com>

### [07199fa](https://github.com/sgl-project/sglang/commit/07199fa220cc353a2b5230b8bf47a0dead7ea96c)

- **作者**: YAMY
- **时间**: 2026-09-04T17:32:44Z
- **提交信息**: [Performance] Optimize Qwen3.5 GDN prefill projection layouts (#36267)

### [55509b3](https://github.com/sgl-project/sglang/commit/55509b3f421a25c631f89de8a139772f625038d8)

- **作者**: Cherry_ming
- **时间**: 2026-09-04T16:19:50Z
- **提交信息**: [NPU] Optimize the execution logic of NPU pr‑test tasks (#38015)

Co-authored-by: Even Zhou <even.y.zhou@outlook.com>
Co-authored-by: sglang-npu-bot <sglangnpu@163.com>

### [01e19dd](https://github.com/sgl-project/sglang/commit/01e19ddf55ad93b7e7459a03aeee43b3892bb567)

- **作者**: Shuwen Wang
- **时间**: 2026-09-04T15:40:34Z
- **提交信息**: chore: add code owners for the Rust radix tree core (#38021)

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [5cd2a76](https://github.com/sgl-project/sglang/commit/5cd2a7661da350080ecf33c2c85141ba0265b8bc)

- **作者**: Shuwen Wang
- **时间**: 2026-09-04T15:39:36Z
- **提交信息**: fix: reformat cosmos3_edge.py to satisfy ruff-format (#38023)

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [0d0e2f9](https://github.com/sgl-project/sglang/commit/0d0e2f92be9be32a3ae2c0eb49b0f2d030614e0c)

- **作者**: huangtingwei
- **时间**: 2026-09-04T15:24:18Z
- **提交信息**: [HiCache] Buffer mode support sidecar pool (#37424)

Co-authored-by: Zhiqiang Xie <xiezhq@stanford.edu>

### [8b1d8c1](https://github.com/sgl-project/sglang/commit/8b1d8c170360c24c48bdb5a001d891b4c3c51f21)

- **作者**: Jialin Ouyang
- **时间**: 2026-09-04T15:06:17Z
- **提交信息**: [Metrics] Add rolling scheduler utilization counters (#37461)

Co-authored-by: Lianmin Zheng <lianminzheng@gmail.com>
Co-authored-by: pranjalssh <pranjalssh@fb.com>

### [4349538](https://github.com/sgl-project/sglang/commit/4349538c02e1566a1424510d5ac3ae853f49feef)

- **作者**: Zhylko Dima
- **时间**: 2026-09-04T14:11:58Z
- **提交信息**: [model] add cosmos3 reasoner to llm only inference (#33572)

Signed-off-by: joeltg <joel@reflection.ai>
Signed-off-by: Joe Rowell <joe@poolside.ai>
Co-authored-by: Dawid Majchrowski <dmajchrowski@nvidia.com>
Co-authored-by: Kedi Wu <kediw@nvidia.com>
Co-authored-by: Kedi Wu <31940276+kediwu0331@users.noreply.github.com>
Co-authored-by: Joel Gustafson <joelgustafson@protonmail.com>

### [19b4686](https://github.com/sgl-project/sglang/commit/19b46863f3514236f299df75607d9c487099a1da)

- **作者**: Shuwen Wang
- **时间**: 2026-09-04T14:08:25Z
- **提交信息**: fix: align write-through pending across tree cores (#37278)

### [88021b0](https://github.com/sgl-project/sglang/commit/88021b0734937c1efc19c2ceb2c1250a507d1fc8)

- **作者**: Mick
- **时间**: 2026-09-04T14:03:25Z
- **提交信息**: [diffusion] chore: make nightly performance measurements robust (#37915)

### [dc6b5d1](https://github.com/sgl-project/sglang/commit/dc6b5d1f5ac2ab45176c5fee7ed9b55aec97ddc2)

- **作者**: hhhh1252023
- **时间**: 2026-09-04T13:26:52Z
- **提交信息**: [CI][NPU] Remove model tests from PR-test pipeline (#38011)

### [978cc22](https://github.com/sgl-project/sglang/commit/978cc228caabaaaab19fa5ca88f50d6170cb4326)

- **作者**: Lianmin Zheng
- **时间**: 2026-09-04T12:22:44Z
- **提交信息**: [Rust] Bound multimodal media ingress (#37967)

### [e4adf63](https://github.com/sgl-project/sglang/commit/e4adf63275005f4b3e6f8d74ae4ff203a75d05df)

- **作者**: Shuwen Wang
- **时间**: 2026-09-04T11:43:17Z
- **提交信息**: [Fix] Vacuous marker writes in the cache tests, and an undebited Mamba admission slot (#36415)

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [3b67854](https://github.com/sgl-project/sglang/commit/3b678549c33c8f025100f16eab814bd308c51ec1)

- **作者**: Kevin Mi
- **时间**: 2026-09-04T11:18:02Z
- **提交信息**: [diffusion] chore: warm up minimax-h3 at the served clip shape (#37945)

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [f3b2725](https://github.com/sgl-project/sglang/commit/f3b2725609d9a733cad13eb3bd4ee3d802d4c167)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-09-04T10:47:26Z
- **提交信息**: sm120 32GB mem-tier: raise decode cuda-graph max_bs 24->48 + chunked_prefill 2k->4k (#37898)

### [12735c2](https://github.com/sgl-project/sglang/commit/12735c2d7684647454efb033a143cad92bfd305a)

- **作者**: Kan Wu
- **时间**: 2026-09-04T10:03:25Z
- **提交信息**: [mm] refactor mm code for rust tokenizer manager (#34660)

Co-authored-by: Rain Jiang <rain-jiang@outlook.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [b42569a](https://github.com/sgl-project/sglang/commit/b42569a0f13585a391e15d735067d91b5a686c13)

- **作者**: CSWYF3634076
- **时间**: 2026-09-04T10:03:21Z
- **提交信息**: [Quant][ue8m0 fix] group requant_weight_ue8m0 reduce reserved gpu memory (#31755)

Co-authored-by: root <root@johor-edge-gpu-a17-13.bec-host.baidu.com>

### [d7f235d](https://github.com/sgl-project/sglang/commit/d7f235daca1e56eb42d3b81a8f91c5748a3160b9)

- **作者**: Lianmin Zheng
- **时间**: 2026-09-04T09:59:52Z
- **提交信息**: [Memory] Retire graph borrow pool before updating static runs (#37966)

Co-authored-by: Shiyan Deng <dsy842974287@meta.com>

### [2216697](https://github.com/sgl-project/sglang/commit/2216697f901b98be632391589f45d3c586de2cec)

- **作者**: Brian
- **时间**: 2026-09-04T09:28:57Z
- **提交信息**: [Docs] Refresh TPU model list and link cookbooks (#37750)

### [44c7866](https://github.com/sgl-project/sglang/commit/44c786679fa0bdd9917df58391705a35250c6ae3)

- **作者**: Ming Yang
- **时间**: 2026-09-04T09:11:03Z
- **提交信息**: [sp] Make attention-TP sequence sharding a per-forward batch property (#37546)

Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Lianmin Zheng <lianminzheng@gmail.com>

### [67248e0](https://github.com/sgl-project/sglang/commit/67248e04b4945bbf34981323f95d643e9161b63f)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-04T08:48:33Z
- **提交信息**: [mem_cache] Route hybrid SWA full-side kv-row frees through `free_segment` (#37876)

Co-authored-by: weireweire <20922698+weireweire@users.noreply.github.com>
Co-authored-by: Sam Shleifer <sshleifer@gmail.com>

### [dae126d](https://github.com/sgl-project/sglang/commit/dae126d510b786a2424684c17ca4e5e70d74e8f7)

- **作者**: karverma-amd
- **时间**: 2026-09-04T07:51:29Z
- **提交信息**: [AMD][DSv4] Fuse inverse-RoPE into the fp8 wo_a quant (stacked on #37423) (#37658)

Co-authored-by: wunhuang <wunhuang@amd.com>

### [0b57847](https://github.com/sgl-project/sglang/commit/0b57847ebfd4e28a2c371892b9d4ac778e34b3fa)

- **作者**: Ke Bao
- **时间**: 2026-09-04T07:46:33Z
- **提交信息**: Fix mamba radix cache ssm state indexing (#37836)

Co-authored-by: adityakamat24 <adityakamat007@gmail.com>

### [01e66a6](https://github.com/sgl-project/sglang/commit/01e66a62db889b6ed921eaf08360119ea4e2ba75)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-09-04T07:05:24Z
- **提交信息**: [Diffusion] Improve BCG warmup frame-count diagnostics for video models (#37890)

### [7f89cc5](https://github.com/sgl-project/sglang/commit/7f89cc5286c34debc98a77b447022387311945f8)

- **作者**: AMD-yanfeiwang
- **时间**: 2026-09-04T07:00:38Z
- **提交信息**: [AMD] Skip unused TOPK v2 plan kernel on ROCm (#37580)

Co-authored-by: kk <43161300+kkHuang-amd@users.noreply.github.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-09-05
**监控日期**: 2026-09-04
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1272
- **最后更新**: 2026-09-04T17:56:54Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

### 1. 主要更新类型
- **Bug修复**：修复了CPU offload场景下权重共享（weight tying）导致的严重状态管理错误。

### 2. 关键变更点及其与项目整体方向的关系
- **问题根源**：当模型存在共享权重（如Qwen3-4B的`lm_head.weight`与`embed_tokens.weight`指向同一参数）时，分层offload机制会为同一参数创建多个独立的pinned镜像和状态机。这导致一个目标（target）的CPU重绑定会破坏另一个目标的GPU驻留记账，异步预取还会暴露半拷贝张量，引发错误的conditioning或设备不匹配崩溃。
- **解决方案**：引入去重机制——共享状态由第一个目标独占，后续目标仅保留记账用的`tie_deduped`标记；强制共享张量的所有者保持持久驻留，确保整个句柄生命周期内张量不迁移；去重后重新计算`prefetch_residency_bytes`。
- **与项目方向的关系**：cache-dit的核心卖点是面向DiT的CPU offload与缓存推理。权重共享在主流大模型中普遍存在（如Qwen、LLaMA系列），此修复直接消除了offload路径上的一个致命缺陷，是提升框架通用性和可靠性的关键一步。

### 3. 对项目的影响和潜在意义
- **正确性保障**：修复了可能导致模型输出错误（torn embedding读取）或直接崩溃的严重问题，使offload功能在带权重共享的模型上达到与GPU驻留基线**逐位一致**的精度。
- **可用性提升**：扩展了框架支持的模型范围，用户无需担心权重共享模型在offload时产生不可预测行为。
- **工程成熟度**：通过结构断言（owner-forced-persistent、tie_deduped）和37个layerwise测试全量通过，展示了严谨的验证流程，增强了用户信任。

### 4. 值得关注的技术点
- **状态机去重**：通过“首目标拥有、后续目标记账”的模式，优雅地解决了多目标共享同一活参数的并发状态管理难题。
- **强制持久驻留的权衡**：共享张量（如Qwen3-4B的fp16 embedding约778MB）将始终占用GPU显存，绕过了`persistent_buckets`的优化路径——这是为正确性付出的显存代价。
- **临时内存峰值**：挂载GPU驻留模型时，去重释放前会短暂分配重复的pinned镜像，属于可接受的瞬时开销。
- **明确边界**：非CPU镜像的offload设备（如NVMe）不在本次修复范围内，体现了对问题域的清晰界定。

### 5. 基于README背景，这些提交如何影响项目发展
cache-dit定位为“PyTorch原生、带缓存/并行/量化/CPU offload的DiT推理引擎”。此次提交虽非新功能，但直接加固了offload子系统的核心可靠性。考虑到DiT类模型（如视频生成、图像生成）常采用大规模embedding和共享投影层，此修复使框架能安全处理这些真实架构，避免了“能跑但结果错”的隐性陷阱。从项目发展看，这标志着从“功能可用”向“生产级可靠”迈进，为后续吸引更广泛用户、支持更大规模模型（如Qwen3-4B这类权重共享模型）扫清了关键障碍，是提升框架在开源生态中竞争力的重要基石。

## 详细提交记录

### [51979f0](https://github.com/vipshop/cache-dit/commit/51979f00725c0799743236d33b1a6c019cbd1608)

- **作者**: DefTruth
- **时间**: 2026-09-04T10:16:44Z
- **提交信息**: fix(offload): dedupe tied weights across layerwise targets (#1111)

* fix(offload): dedupe tied weights across layerwise targets

Weight tying (e.g. lm_head.weight is embed_tokens.weight, Qwen3-4B) made two
targets reference the same live parameter with independent pinned mirrors and
onload/offload state machines: one target's CPU rebind poisoned the other's
GPU residency bookkeeping, and async prefetch exposed half-copied tensors to
the other's forward (torn vocab embedding reads -> wrong conditioning; with
prefetch_limit it crashed on device mismatch instead).

Shared states are now owned by their first target: duplicates are dropped from
later targets (tie_deduped, bookkeeping-only transport), owners are forced
persistent so the shared tensor stays resident for the handle lifetime, and
prefetch_residency_bytes is recomputed after the drop.

Trade-offs: tied tensors stay GPU-resident (bypassing persistent_buckets,
Qwen3-4B fp16 embedding ~778MB), and attaching a GPU-resident model briefly
allocates the duplicate pinned mirror before dedupe frees it. Non-CPU-mirror
offload devices are out of scope.

Verified: tied toy LM (Embedding + blocks + norm + tied lm_head) is
bitwise-equal to the GPU-resident baseline across sync / async /
async+prefetch_limit, with owner-forced-persistent and tie_deduped structure
asserts; real klein_fit TE outputs are bitwise-stable across offload variants;
all 37 layerwise offload tests pass.

Co-authored-by: copilot-swe-agent[bot] <198982749+Copilot@users.noreply.github.com>

* chore: update logs

---------

Co-authored-by: copilot-swe-agent[bot] <198982749+Copilot@users.noreply.github.com>

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-09-05
**监控日期**: 2026-09-04
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 90981
- **最后更新**: 2026-09-04T23:44:35Z

## 提交统计

- **昨日提交总数**: 36
- **提交者数量**: 30
- **主要提交者**: Yizheng Jiao, Summer Yang, Jared Wen

## AI分析总结

# vLLM 昨日提交分析报告

## 一、主要更新类型

本次提交涵盖**Bug修复**（约12项）、**性能优化**（约5项）、**CI/测试改进**（约6项）、**功能新增**（约4项）、**类型系统完善**（2项）及**安全加固**（1项），整体以稳定性和效率提升为主导。

## 二、关键变更点与项目方向

1. **Model Runner V2 持续推进**：多项提交围绕MRV2展开，包括DBO支持（eager模式）、CUDAGraph统计指标、Spec Decode对draft attention_backend的兼容等，表明vLLM正在加速向新一代执行引擎迁移。
2. **Speculative Decode 生态完善**：修复FlashAttention AOT调度问题、优化warmup设备选择，提升投机解码在滑动窗口场景下的可靠性。
3. **多模态能力增强**：新增torchcodec音频加载器、修复多模态模型LLM.chat()双重BOS问题、限制GLMGA视频采样防资源耗尽，体现对多模态推理场景的持续投入。
4. **量化与硬件适配**：支持在线量化与部分预量化checkpoint混合使用，修复TRTLLM FP8 MoE的SwiGLU clamp问题，扩展硬件兼容性。
5. **CI/CD 基础设施优化**：多项超时调整、镜像构建修复、仅主仓库运行Actions等，提升开发效率与稳定性。

## 三、项目影响与潜在意义

- **MRV2 加速落地**：DBO支持和指标统计补齐了MRV2的核心能力，为后续全面替换V1奠定基础。
- **稳定性显著提升**：Mamba状态保留、MoE偏移修复、双BOS修复等直接解决用户可感知的正确性问题。
- **安全加固**：视频采样上限设置防止请求驱动的资源耗尽，体现对生产环境安全性的重视。

## 四、值得关注的技术点

- **Mamba状态保留修复**：针对padded prompt tails场景，确保状态一致性，对SSM类模型部署有重要意义。
- **CUDA Graph捕获前内核预热**：避免捕获过程中的首次执行开销，提升图捕获质量。
- **MoE fused sum行偏移修复**：直接影响MoE层输出正确性，属于底层计算核心问题。
- **Qwen3.8-Flash-Next稀疏注意力优化**：针对prefill和短上下文decode场景的QSA改进，体现对特定模型架构的深度调优。

## 五、对项目发展的影响

vLLM正处在**架构升级与生态扩展并行**的关键阶段。一方面，MRV2相关提交持续增加，表明项目正稳步推进下一代执行引擎的落地；另一方面，对多模态、MoE、MLA等前沿模型结构的支持不断深化，巩固其作为“易用、快速、廉价”LLM服务框架的定位。大量CI和类型系统修复虽不直接面向用户，但提升了项目自身的工程质量和协作效率，为长期发展奠定基础。整体来看，vLLM在保持快速迭代的同时，正着力解决规模化部署中的正确性、安全性和硬件适配问题，向生产级推理基础设施迈进。

## 详细提交记录

### [874df93](https://github.com/vllm-project/vllm/commit/874df9373dab532543a0229fb2f144f7c14093ae)

- **作者**: Nathan Sala
- **时间**: 2026-09-04T23:44:28Z
- **提交信息**: [Bugfix] Preserve Mamba state for padded prompt tails (#55178)

Signed-off-by: Nathan Sala <natouda@gmail.com>
Signed-off-by: Nathan Sala <33957625+natsala13@users.noreply.github.com>

### [eb74fbb](https://github.com/vllm-project/vllm/commit/eb74fbb3e7f0a917e93fff90ef68da23dbd2b34b)

- **作者**: Yizheng Jiao
- **时间**: 2026-09-04T23:20:32Z
- **提交信息**: [Bugfix][NIXL] Don't assert when a failed transfer is cleaned up twice (#54518)

Signed-off-by: Yizheng Jiao <jyizheng@gmail.com>
Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: NickLucche <nicolo.lucchesi@mistral.ai>
Co-authored-by: Nick Hill <nickhill123@gmail.com>

### [685074c](https://github.com/vllm-project/vllm/commit/685074cd61d6b8432575d11b38341559992cf9dd)

- **作者**: aoshen02
- **时间**: 2026-09-04T22:44:18Z
- **提交信息**: [Bugfix][V2] Warm up kernels before capturing CUDA graphs (#55341)

Signed-off-by: aoshen02 <aoshen02@users.noreply.github.com>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: aoshen02 <aoshen02@users.noreply.github.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>

### [8f269a9](https://github.com/vllm-project/vllm/commit/8f269a93bbcca6e2737616d76365a5ac771c4d27)

- **作者**: Misha Goin
- **时间**: 2026-09-04T21:45:24Z
- **提交信息**: Revert "[CI] Remove deleted nvidia/Nemotron-3-Nano-Omni-30B-A3B-Reasoning-BF16 and its arch aliases" (#55392)

### [3f41d10](https://github.com/vllm-project/vllm/commit/3f41d102c5b8636f7206a5fd5949dd8ae0b30a0d)

- **作者**: Anjie Hou
- **时间**: 2026-09-04T21:17:39Z
- **提交信息**: [1/2][Model Runner V2] DBO support, eager mode (#50945)

Signed-off-by: specture724 <specture724@gmail.com>
Signed-off-by: Anjie Hou <149605198+specture724@users.noreply.github.com>
Co-authored-by: jiangkuaixue123 <jiangxiaozhou111@163.com>
Co-authored-by: Lucas Wilkinson <lwilkins@redhat.com>

### [784cac7](https://github.com/vllm-project/vllm/commit/784cac7c424db2f2fdc879b672abad7e231f5698)

- **作者**: Taneem Ibrahim
- **时间**: 2026-09-04T20:47:11Z
- **提交信息**: [Mypy] Fix mypy typing for P models (#54169)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [5093e48](https://github.com/vllm-project/vllm/commit/5093e4844a75f279d1921d7e34ccd23d68529f27)

- **作者**: Zihan Zhang
- **时间**: 2026-09-04T20:42:01Z
- **提交信息**: [Bugfix][Spec Decode] Drop FlashAttention's AOT schedule for a sliding-window DFlash drafter (#54374)

### [c81ace1](https://github.com/vllm-project/vllm/commit/c81ace18596f75660bbc04efc2075a5f17a76791)

- **作者**: Sun
- **时间**: 2026-09-04T20:11:42Z
- **提交信息**: [Perf] Read VidCom2 frame budgets once (#55331)

Signed-off-by: levius <2114377220@qq.com>

### [3284af6](https://github.com/vllm-project/vllm/commit/3284af6bf1be8429c332bd5fafba579c2d7557da)

- **作者**: Taneem Ibrahim
- **时间**: 2026-09-04T19:59:29Z
- **提交信息**: [Bugfix] Reject 0 or non-positive max concurrency (#54887)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [2524051](https://github.com/vllm-project/vllm/commit/25240513856e9aca9b07e9381f2a4513b6954bd8)

- **作者**: Stefano Castagnetta
- **时间**: 2026-09-04T19:23:19Z
- **提交信息**: [Bugfix][Spec Decode] Honour the draft's attention_backend on Model Runner V2 (#54826)

Signed-off-by: Stefano Castagnetta <scastagnetta@nvidia.com>

### [5690b02](https://github.com/vllm-project/vllm/commit/5690b02c03832a4ac3af231d3ecebe649c188095)

- **作者**: fxmarty-amd
- **时间**: 2026-09-04T18:46:06Z
- **提交信息**: [Quantization] Support online quantization with partially pre-quantized checkpoints (#51392)

Signed-off-by: Felix Marty <Felix.Marty@amd.com>
Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Codex <codex@openai.com>
Co-authored-by: mgoin <mgoin64@gmail.com>

### [a11dfcf](https://github.com/vllm-project/vllm/commit/a11dfcff8921247c119b9356ae1c4bbd3a7f7f57)

- **作者**: Andrey Talman
- **时间**: 2026-09-04T18:10:30Z
- **提交信息**: [CI] Surface why the CRCR nightly report cannot read its Buildkite secret (#54860)

Signed-off-by: Andrey Talman <atalman@fb.com>

### [701a744](https://github.com/vllm-project/vllm/commit/701a7444909d1ef1521f71abca56ed3448cc89fb)

- **作者**: Jared Wen
- **时间**: 2026-09-04T17:31:54Z
- **提交信息**: [CI] Raise AMD Spec Decode Eagle 1 job timeout to 35min (#55136)

Signed-off-by: JaredforReal <w13431838023@gmail.com>
Co-authored-by: Kimi <noreply@moonshot.cn>

### [8cd95f7](https://github.com/vllm-project/vllm/commit/8cd95f7de70df6ff15002168a048891c708428fd)

- **作者**: Summer Yang
- **时间**: 2026-09-04T17:24:31Z
- **提交信息**: [Bugfix][MLA] Restore DSpark cache-group capability under optimized Python (#55234)

Signed-off-by: Summer Yang <girasoleyang@gmail.com>

### [1ff5edb](https://github.com/vllm-project/vllm/commit/1ff5edb02327583cd9c88f6bda3c485dbd504938)

- **作者**: yzyyzyhhh
- **时间**: 2026-09-04T16:39:02Z
- **提交信息**: [Bug-fix] Fix MoE fused sum row offsets (#50220)

Signed-off-by: yaozhiyuan.666 <yaozhiyuan.666@bytedance.com>
Co-authored-by: yaozhiyuan.666 <yaozhiyuan.666@bytedance.com>

### [761c586](https://github.com/vllm-project/vllm/commit/761c5861e34edb52c290e3171feb3763732ba8ca)

- **作者**: Connor Carpenter
- **时间**: 2026-09-04T16:37:53Z
- **提交信息**: [Rust Frontend][gRPC] Preserve multimodal metadata for remote-prefill decode (#54814)

### [8ad2076](https://github.com/vllm-project/vllm/commit/8ad2076c4a0e2a7e5ccf5b11455f737430ad12db)

- **作者**: Thomas Ortner
- **时间**: 2026-09-04T16:26:01Z
- **提交信息**: [Transformers backend] Find attention with a fuser and attach vLLM's layer to it (#54941)

Signed-off-by: Thomas Ortner <boh@zurich.ibm.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [99a1ab8](https://github.com/vllm-project/vllm/commit/99a1ab8e4c9fa21cafdd460ac826a445052ac1eb)

- **作者**: Rohan Potdar
- **时间**: 2026-09-04T16:16:54Z
- **提交信息**: [ROCm][CI] Bump ROCk release image build timeout to 3h (#55354)

Signed-off-by: Rohan Potdar <rohan.potdar@amd.com>
Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>

### [6a039f4](https://github.com/vllm-project/vllm/commit/6a039f465e3770192085e551f642c7a218797d2d)

- **作者**: Jared Wen
- **时间**: 2026-09-04T16:16:10Z
- **提交信息**: [feat] add torchcodec as audio loader and implement selective audio backend (#51826)

Signed-off-by: JaredforReal <w13431838023@gmail.com>
Co-authored-by: saltman155 <saltman155@outlook.com>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>

### [131e028](https://github.com/vllm-project/vllm/commit/131e0285f60faad78a13ae79573b7b38ddb52a85)

- **作者**: erdholion
- **时间**: 2026-09-04T16:15:40Z
- **提交信息**: [Frontend] Warn when removed guided-decoding fields are present in a request (#54285)

Signed-off-by: Ilir <ljeci.ilir@gmail.com>
Co-authored-by: Ilir <ljeci.ilir@gmail.com>

### [5e729d8](https://github.com/vllm-project/vllm/commit/5e729d84eb4c91411172f2245c37cf05579ea5b9)

- **作者**: Harry Mellor
- **时间**: 2026-09-04T16:09:49Z
- **提交信息**: [CI] Only run GitHub Actions on the main repo (#55349)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [f19431e](https://github.com/vllm-project/vllm/commit/f19431e5c8634cd0d1641d3f7f4a01043f0eddab)

- **作者**: aoshen02
- **时间**: 2026-09-04T15:34:21Z
- **提交信息**: [Bugfix][MoE] Allow TRTLLM FP8 block-scale MoE with SwiGLU clamp (#55069)

Signed-off-by: aoshen02 <aoshen02@users.noreply.github.com>
Co-authored-by: aoshen02 <aoshen524@gmail.com>
Co-authored-by: aoshen02 <aoshen02@users.noreply.github.com>
Co-authored-by: Codex <noreply@openai.com>

### [a85d073](https://github.com/vllm-project/vllm/commit/a85d0738da311ce4ad5814787e61a12826e232df)

- **作者**: summer
- **时间**: 2026-09-04T14:23:15Z
- **提交信息**: [Bugfix] Fix double BOS in LLM.chat() for multimodal models (#55288)

Signed-off-by: summer <128961079+zhang-keliang@users.noreply.github.com>

### [a69e75b](https://github.com/vllm-project/vllm/commit/a69e75b9b6d6a26d90b6790e2eb75b3419a47c16)

- **作者**: siyu
- **时间**: 2026-09-04T13:32:06Z
- **提交信息**: Fast Start (#54921)

Signed-off-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: liusy58 <liusy58@smail.nju.edu.cn>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>

### [07ee97e](https://github.com/vllm-project/vllm/commit/07ee97e0230e0ff8759cdc95a1bb09ba2e462720)

- **作者**: Qiming Zhang
- **时间**: 2026-09-04T13:16:50Z
- **提交信息**: [Test] Split test_sampling_mask_preserves_top_k_boundary_ties to remove Triton-kernel-specific assumption Description (#55315)

Signed-off-by: mayuyuace <qiming1.zhang@intel.com>

### [31a8a26](https://github.com/vllm-project/vllm/commit/31a8a266622781917cef482d01db415cfa3cbd92)

- **作者**: Thien Tran
- **时间**: 2026-09-04T13:08:02Z
- **提交信息**: [Qwen3.8-Flash-Next] Improve QSA sparse GQA for prefill and short-ctx decode (#54873)

Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>
Co-authored-by: Kimi <noreply@moonshot.cn>

### [8340fe1](https://github.com/vllm-project/vllm/commit/8340fe1bb99c187ebec08ad03bbe0d06b45d1d40)

- **作者**: Li, Jiang
- **时间**: 2026-09-04T12:27:02Z
- **提交信息**: [CI/Build] Fix flaky failures in CPU CI image building (#55317)

Signed-off-by: jiang1.li <jiang1.li@intel.com>

### [8b6de0e](https://github.com/vllm-project/vllm/commit/8b6de0eb9a09ef53f20cf06bd4d17ee264b9c2a7)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-09-04T12:02:41Z
- **提交信息**: [Security] Cap GLMGA video sampling to prevent request-driven resource exhaustion (#54935)

Signed-off-by: jperezde <jperezde@redhat.com>
Signed-off-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>

### [c615b1f](https://github.com/vllm-project/vllm/commit/c615b1fd67f5b149c75aea592de8e563cb0c2da9)

- **作者**: Taneem Ibrahim
- **时间**: 2026-09-04T11:50:43Z
- **提交信息**: [Mypy] Fix mypy typing for L models (#54177)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [3ff4f02](https://github.com/vllm-project/vllm/commit/3ff4f02dfe69abc1a0375d1ea8d8d5cb25609fcc)

- **作者**: Rita Brugarolas
- **时间**: 2026-09-04T10:14:51Z
- **提交信息**: [AMD][kimik3][ROCm][Perf] Fuse MLA q/kv RMSNorm in AMD Kimi-K3 MLA wrapper (#52494)

Signed-off-by: Rita Brugarolas Brufau <rita.brugarolasbrufau@amd.com>

### [fd4a151](https://github.com/vllm-project/vllm/commit/fd4a1512628ad17944095263c1fe89598710a3ce)

- **作者**: Canlin Guo
- **时间**: 2026-09-04T09:57:56Z
- **提交信息**: [Kernel] Reuse Qwen4Exp HC combine-norm for MTP input (#54687)

Signed-off-by: Canlin Guo <canlinguosdu@gmail.com>
Signed-off-by: Canlin <canlinguosdu@gmail.com>

### [9cd956c](https://github.com/vllm-project/vllm/commit/9cd956c7e6cf54efa366b803cafa15ec6c2df827)

- **作者**: Tony Lin
- **时间**: 2026-09-04T07:56:59Z
- **提交信息**: [CI/Test] Add expert parallelism coverage to external LB tests (#53497)

Signed-off-by: Tony Lin <tony.lin@intel.com>
Co-authored-by: Kevin H. Luu <khluu000@gmail.com>

### [605ca45](https://github.com/vllm-project/vllm/commit/605ca45b917ac0614958c63851c31a3f1c82e20d)

- **作者**: Tony Lin
- **时间**: 2026-09-04T07:51:25Z
- **提交信息**: [XPU] Fix device assignment for DP external LB (#53037)

Signed-off-by: Tony Lin <tony.lin@intel.com>

### [a8693df](https://github.com/vllm-project/vllm/commit/a8693df504404ea0288e480165143d8a216f4220)

- **作者**: Kunshang Ji
- **时间**: 2026-09-04T07:48:45Z
- **提交信息**: [SpecDecode]Fix spec decode warmup device selection (#55245)

Signed-off-by: Kunshang Ji <jikunshang95@gmail.com>
Co-authored-by: GitHub Copilot <copilot@github.com>

### [a5c9179](https://github.com/vllm-project/vllm/commit/a5c9179e731e8d2ec7e03485a3ab0754a5a27182)

- **作者**: Thien Tran
- **时间**: 2026-09-04T07:43:20Z
- **提交信息**: [Qwen3.8-Flash-Next] Compact indexer logits workspace to improve prefill efficiency (#54915)

Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>

### [8f816a3](https://github.com/vllm-project/vllm/commit/8f816a3f665489d7f0d222115d4f72ebab01076b)

- **作者**: Yizhou
- **时间**: 2026-09-04T07:19:50Z
- **提交信息**: [MRV2][Metrics] Support `CUDAGraphStat` in MRV2 (#52358)

Signed-off-by: Yizhou Liu <liu_yizhou@outlook.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-09-05
**监控日期**: 2026-09-04
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 6663
- **最后更新**: 2026-09-04T23:36:31Z

## 提交统计

- **昨日提交总数**: 12
- **提交者数量**: 11
- **主要提交者**: Inesh Reddy Chappidi, Weiming Liao, MikeyDong1

## AI分析总结

## 提交分析总结

### 1. 主要更新类型
本批12个提交涵盖**功能新增**（3项）、**Bug修复**（6项）、**性能优化**（2项）及**CI改进**（1项），无纯文档或重构类提交。

### 2. 关键变更点与项目方向
- **音频/语音模型支持扩展**：Moss-TTS参考音频预处理、dots.tts在线服务支持、Higgs Audio v3语音克隆token校验修复，持续强化多模态音频能力。
- **多模态模型适配**：Qwen3-Omni MoE后端选择修复、exact-shape codec模型input_ids视图修复，确保主流模型正确运行。
- **推理性能与资源优化**：Whisper在显存允许时使用GPU、DreamZero移除冗余CUDA编译守卫、扩散worker RPC结果释放优化，提升资源利用效率。
- **批处理能力增强**：Boogu-Image启用请求级批处理，扩展了图像生成的并发处理能力。

### 3. 项目影响与潜在意义
- **稳定性提升**：多项Bug修复（BAGEL去噪步数恢复、Hub内核依赖下限更新）直接增强推理可靠性。
- **生态扩展**：新增TTS在线服务与参考音频支持，使vllm-omni向“全模态”服务目标迈进，覆盖语音合成场景。
- **CI质量保障**：口语单元文本比较规范化，减少测试误判，提升持续集成可信度。

### 4. 值得关注的技术点
- **MoE后端选择修复**（Qwen3-Omni）涉及专家并行策略正确性，对大规模稀疏模型部署至关重要。
- **扩散模型RPC结果释放**解决多rank场景下的资源泄漏问题，体现分布式推理的工程深度。
- **请求级批处理**（Boogu-Image）是图像生成服务吞吐量提升的关键架构改进。

### 5. 对项目发展的影响
vllm-omni定位为“人人可用的全模态模型服务”，本批提交清晰体现了三个发展路径：**一是音频模态从理解向生成延伸**（TTS相关3项），**二是主流多模态模型的兼容性加固**（Qwen3-Omni、Higgs Audio等），**三是服务化能力的工程优化**（批处理、GPU利用、分布式资源管理）。这些改动共同推动项目从“能跑”向“跑得稳、跑得快、覆盖广”演进，为后续支持更多模态组合与生产级部署奠定基础。

## 详细提交记录

### [1e74807](https://github.com/vllm-project/vllm-omni/commit/1e74807c356be5cba4239faae7c38763fe1a44be)

- **作者**: BruceLoveDecimal
- **时间**: 2026-09-04T23:36:26Z
- **提交信息**: [Feature][Moss-TTS] Reference Audio Preprocessing (#4982)

Signed-off-by: BruceLoveDecimal <39156883+BruceLoveDecimal@users.noreply.github.com>
Signed-off-by: liuqihao <liuqihao970610@gmail.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [ae57e40](https://github.com/vllm-project/vllm-omni/commit/ae57e406fd02516ef5ee8cd40a1458328e13a2a5)

- **作者**: akshatvishu
- **时间**: 2026-09-04T23:35:48Z
- **提交信息**: [Perf][CI] Use Whisper on GPU when memory permits (#5675)

Signed-off-by: akshatvishu <akshatnayak197@gmail.com>
Signed-off-by: andyluo7 <andy.luo@amd.com>
Co-authored-by: andyluo7 <andy.luo@amd.com>

### [b6b992a](https://github.com/vllm-project/vllm-omni/commit/b6b992ac7baa7896c9123cea6abcd9151612a697)

- **作者**: LOGO127
- **时间**: 2026-09-04T23:06:47Z
- **提交信息**: [Bugfix] Fix Higgs Audio v3 voice-clone token validation (#7065)

Signed-off-by: luozijian <luozijian0924@gmail.com>

### [66d9381](https://github.com/vllm-project/vllm-omni/commit/66d938100b9bf00a34369bfbdc206b94b14d0ad8)

- **作者**: Inesh Reddy Chappidi
- **时间**: 2026-09-04T22:28:49Z
- **提交信息**: [Bugfix] Give exact-shape codec models an unpadded input_ids view (#6775)

Signed-off-by: Inesh Reddy <ineshreddy249@gmail.com>
Signed-off-by: IneshReddy249 <ineshreddy249@gmail.com>
Co-authored-by: Gao Han <hgaoaf@connect.ust.hk>

### [348fd0f](https://github.com/vllm-project/vllm-omni/commit/348fd0fc07258a02732b07c7f32a9f3ba3b56ff9)

- **作者**: boatman
- **时间**: 2026-09-04T21:44:10Z
- **提交信息**: [Feat][dots.tts] Add Online Serving Support (#6235)

Signed-off-by: boatman <109857087+sphinxkkkbc@users.noreply.github.com>

### [ea14b04](https://github.com/vllm-project/vllm-omni/commit/ea14b04e9f086495eb253535e6c17cf380e0fa19)

- **作者**: Trigger
- **时间**: 2026-09-04T17:05:05Z
- **提交信息**: [Bugfix][BAGEL] Restore original denoise step count (#7049)

Signed-off-by: Trigger <Meng.Bo.Wang@outlook.com>
Signed-off-by: Gao Han <hgaoaf@connect.ust.hk>
Co-authored-by: Gao Han <hgaoaf@connect.ust.hk>

### [0f9ee6a](https://github.com/vllm-project/vllm-omni/commit/0f9ee6afd83c5e1dc02fe834d8d2c4c51ecd4d3b)

- **作者**: Weiming Liao
- **时间**: 2026-09-04T15:18:01Z
- **提交信息**: [CI][Bugfix] Normalize spoken units in text comparison (#6947)

Signed-off-by: Weiming Liao <liaowm5@gmail.com>

### [22cefe0](https://github.com/vllm-project/vllm-omni/commit/22cefe04b4007607ff235ea8520cd404ad44df3e)

- **作者**: SYLAR
- **时间**: 2026-09-04T14:15:55Z
- **提交信息**: [Bugfix] Update Hub kernel dependency floor (#7020)

Signed-off-by: hsliuustc0106 <liuhongsheng4@huawei.com>
Co-authored-by: hsliuustc0106 <liuhongsheng4@huawei.com>

### [7493cbd](https://github.com/vllm-project/vllm-omni/commit/7493cbd3c24befd9628fe679ebc65f4c00a57701)

- **作者**: SYLAR
- **时间**: 2026-09-04T13:16:58Z
- **提交信息**: [Bugfix] Fix Qwen3-Omni MoE backend selection (#7019)

Signed-off-by: hsliuustc0106 <liuhongsheng4@huawei.com>
Co-authored-by: hsliuustc0106 <liuhongsheng4@huawei.com>

### [41f4f9d](https://github.com/vllm-project/vllm-omni/commit/41f4f9d8c91a15b6d2f3b65516bfd885559d8e27)

- **作者**: MikeyDong1
- **时间**: 2026-09-04T13:01:05Z
- **提交信息**: [Perf][DreamZero] Remove redundant CUDA compile guard (#6983)

Signed-off-by: MikeyDong1 <xdong-1219@outlook.com>

### [10701e1](https://github.com/vllm-project/vllm-omni/commit/10701e18389fe282ca8c2510cd2022a76a9dad2a)

- **作者**: heyuanliu-intel
- **时间**: 2026-09-04T08:45:17Z
- **提交信息**: [Bugfix] Release diffusion worker RPC results on ranks that do not reply (#6989)

Signed-off-by: heyuanliu-intel <heyuan.liu@intel.com>

### [0e903e9](https://github.com/vllm-project/vllm-omni/commit/0e903e9695a68817b9817885e834cd7c02148aae)

- **作者**: Shenglei Fu
- **时间**: 2026-09-04T08:27:51Z
- **提交信息**: [Diffusion] Enable request-level batching for Boogu-Image (T2I) (#6968)

Signed-off-by: Shenglei Fu <117230642+ShengleiFu@users.noreply.github.com>
Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

---
