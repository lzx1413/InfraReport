# GitHub Stars 合并报告 - 2026-08-05

**合并日期**: 2026-08-06
**监控日期**: 2026-08-05
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


**报告日期**: 2026-08-06
**监控日期**: 2026-08-05
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2126
- **最后更新**: 2026-08-05T14:29:28Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 2
- **主要提交者**: zhangxin.zzzzz, Zhichao Liu

## AI分析总结

### 主要更新类型
本次提交全部为**功能新增**与**性能优化**，无Bug修复或文档更新，聚焦于数据加载与训练流程的效率提升。

### 关键变更点及与项目方向的关系
1. **数据加载灵活性增强**：支持map-style数据集在worker-side动态批处理（#853），并暴露dataloader调度参数（#940）。这直接服务于VeOmni“多模态模型训练”的核心目标——不同模态（图像、视频、音频）的数据格式差异大，动态批处理能更高效地处理变长样本，减少填充浪费。
2. **训练流程精简**：复用损失函数分母（#941）和可选关闭train step同步（#938），减少冗余计算与通信开销。这与项目“模型中心化分布式训练配方”的定位一致，旨在降低大规模多模态训练的资源消耗。

### 对项目的影响和潜在意义
- **性能提升**：损失分母复用可减少梯度计算中的重复操作；关闭同步则允许异步训练，提升GPU利用率，尤其适合多节点环境。
- **易用性增强**：暴露调度参数使研究者能针对不同模态数据微调加载策略，降低使用门槛，吸引更多社区用户。
- **架构演进**：worker-side动态批处理是数据管线的关键升级，为未来支持流式数据或更复杂采样策略奠定基础。

### 值得关注的技术点
- **worker-side动态批处理**：将批处理逻辑从主进程下放到worker，减少主进程瓶颈，是分布式训练中常见优化手段，但需注意数据一致性与内存管理。
- **异步训练的可控性**：关闭同步虽提升速度，但可能影响梯度收敛稳定性，需配合学习率调度或梯度累积策略使用。

### 对项目发展的影响
VeOmni作为“多模态训练配方库”，其核心价值在于提供高效、可复用的训练方案。本次提交通过优化数据加载与训练循环，直接提升了配方的执行效率与灵活性，使项目能更好地支撑更大规模、更多模态的模型训练实验。同时，这些改进降低了用户自定义训练流程的复杂度，有助于扩大项目在学术与工业界的采用范围，推动多模态AI研究的落地。

## 详细提交记录

### [8224d14](https://github.com/ByteDance-Seed/VeOmni/commit/8224d143345295fbc2ab00e19870a1d5eb701a41)

- **作者**: Zhichao Liu
- **时间**: 2026-08-05T14:25:26Z
- **提交信息**: [data] feat: support map-style datasets in worker-side dynamic batching (#853)

### [7bb4b62](https://github.com/ByteDance-Seed/VeOmni/commit/7bb4b621d4d79a1e6da700e6060dc63491b28df2)

- **作者**: zhangxin.zzzzz
- **时间**: 2026-08-05T10:16:33Z
- **提交信息**: [trainer, perf] feat: reuse reduced loss denominators (#941)

### [bf6e59a](https://github.com/ByteDance-Seed/VeOmni/commit/bf6e59a96b011b2c23e0c19dd2c0e9399e38d032)

- **作者**: zhangxin.zzzzz
- **时间**: 2026-08-05T10:15:26Z
- **提交信息**: [data, perf] feat: expose dataloader scheduling knobs (#940)

### [bb8e1d2](https://github.com/ByteDance-Seed/VeOmni/commit/bb8e1d2ce519f0434421528cecfc1195ba6e4e20)

- **作者**: zhangxin.zzzzz
- **时间**: 2026-08-05T10:11:14Z
- **提交信息**: [trainer, perf] feat: make train step sync optional (#938)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-08-06
**监控日期**: 2026-08-05
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2571
- **最后更新**: 2026-08-05T17:17:15Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Watebear, Chernobyllight

## AI分析总结

### 主要更新类型
本次提交以 **Bug修复** 为主，同时包含对模型兼容性和推理稳定性的针对性优化，未涉及新功能或大规模重构。

### 关键变更点及与项目方向的关系
1. **LTX2 模型修复**：支持复数旋转位置编码（complex RoPE）并允许归一化方式可配置。这直接提升了 LightX2V 对 LTX2 视频生成模型的适配精度，与项目“轻量级视频生成推理框架”的核心目标一致——通过精确的底层算子支持，确保不同模型在框架内高效、正确运行。
2. **HunyuanImage3 分词器修复**：在加载 tokenizer.json 时优先使用 Tokenizers 后端，防止 Transformers 5.x 静默丢弃自定义 ByteLevel 解码器，并在失败时快速报错。这保障了提示词 BPE 编码和思维链（COT）解码的完整性，对依赖精确文本编码的图像/视频生成任务至关重要。

### 对项目的影响与潜在意义
- **提升模型兼容性**：修复了特定模型（LTX2、HunyuanImage3）在框架内的已知缺陷，降低了用户在这些模型上遇到推理错误或结果异常的概率。
- **增强鲁棒性**：通过“快速失败”机制，避免在分词器后端不匹配时静默产生错误结果，提高了框架的可诊断性和可靠性。
- **巩固生态定位**：作为视频生成推理框架，对多模型（视频+图像）的精细支持有助于吸引更广泛的用户群体，强化其在生成式 AI 工具链中的实用性。

### 值得关注的技术点
- **复数 RoPE 支持**：表明框架正在跟进前沿位置编码实现，对长序列视频生成中的空间-时间建模有直接帮助。
- **分词器后端选择策略**：优先使用 Tokenizers 后端并显式校验解码器保留，体现了对 Transformers 库版本演进（5.x）的主动适配，避免依赖隐式行为。
- **可配置归一化**：为不同模型或硬件环境提供灵活性，是框架“轻量”与“通用”平衡的体现。

### 对项目发展的影响
结合 README 中“轻量级视频生成推理框架”的定位，这两项修复虽小但精准，分别解决了 **底层模型算子正确性** 和 **文本编码链路完整性** 两个关键环节。它们有助于：
- 增强框架对新兴视频/图像生成模型的吸引力，扩大模型覆盖矩阵；
- 减少用户因底层细节（如 RoPE 或分词器）导致的失败，提升开箱即用的体验；
- 为后续支持更多依赖复杂位置编码或特殊分词器的模型奠定基础，推动框架向更通用、更稳定的方向演进。

总体而言，本次提交是典型的“夯实基础”型更新，虽无显性功能亮点，但对框架的成熟度和用户信任度有积极贡献。

## 详细提交记录

### [a76c32e](https://github.com/ModelTC/LightX2V/commit/a76c32ef00cd483c48b7c49971b379cd2e8fb4e6)

- **作者**: Watebear
- **时间**: 2026-08-05T17:15:42Z
- **提交信息**: fix(ltx2): support complex RoPE and configurable normalization (#1333)

Co-authored-by: Super User <root@dev-metax-0.dev-metax.3b1febd2-0246-40a8-a771-04544a47aa0d.svc.cluster.local>

### [91c3ac6](https://github.com/ModelTC/LightX2V/commit/91c3ac6f416a5af779084a57363cd15d1d375c6f)

- **作者**: Chernobyllight
- **时间**: 2026-08-05T09:28:23Z
- **提交信息**: fix(hunyuan-image3): preserve serialized tokenizer backend (#1332)

Load tokenizer.json as a Tokenizers backend when available so
Transformers 5.x cannot silently drop the custom ByteLevel decoder. Fail
fast if decoder preservation does not succeed, protecting prompt BPE
encoding and COT decoding.

Co-authored-by: liuhongda <liuhongda@sensetime.com>

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-08-06
**监控日期**: 2026-08-05
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2185
- **最后更新**: 2026-08-05T06:06:59Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-08-06
**监控日期**: 2026-08-05
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 6107
- **最后更新**: 2026-08-05T22:40:07Z

## 提交统计

- **昨日提交总数**: 9
- **提交者数量**: 9
- **主要提交者**: Ziang Li, Brian K. Ryu, myu-guo

## AI分析总结

# FlashInfer 昨日提交分析

## 一、主要更新类型

本次提交涵盖**功能新增**（CuTe DSL HCA后端、新cubin支持）、**Bug修复**（MoE monokernel计数器重置与数值溢出、CuTe DSL finalize输出尾部处理、非对齐head count支持）、**性能优化**（MSA decode路径消除冗余前缀和、topk跳过索引排序）、**代码维护**（CODEOWNERS更新、测试脚本回滚）。

## 二、关键变更点与项目方向的关系

1. **DeepSeek V4稀疏MLA的CuTe DSL HCA后端**：为Blackwell GPU新增SM100/SM103内核，支持两CTA集群、split-K归约、持久/非持久调度器，并通过`backend="cute-dsl"`暴露。这是对前沿模型架构的主动适配，体现项目紧跟LLM推理需求演进的定位。

2. **MoE monokernel重写**：用哨兵/标志跨块交接替代软件grid barrier，修复scratchpad重用时的计数器污染；同时用epsilon钳制解决近次正规块最大值的inv_scale溢出。这直接提升MoE推理的数值稳定性和CUDA Graph可捕获性。

3. **MSA decode路径优化**：消除paged路径中不必要的prefix sum重建，并让`msa_topk_select`支持per-token语义的`num_valid_pages`张量，避免vLLM集成时的host端后处理开销。

4. **CuTe DSL FMHA cubin升级**：新增混合QK/PV dtype、block-scaled、Rubin cubin，支持sm_107a架构和JIT编译回退，扩展了注意力内核的硬件覆盖和配置灵活性。

5. **topk tie-break与deterministic解耦**：将“确定性选择”与“确定性输出排序”分离，tie-break模式不再强制触发索引排序finalizer，减少不必要开销。

## 三、项目影响与潜在意义

- **性能层面**：MSA decode路径和topk的优化直接降低per-call开销，对decode这种延迟敏感场景意义重大；MoE内核重写消除了潜在的正确性风险。
- **功能层面**：HCA后端和cubin升级扩展了支持的模型架构（DeepSeek V4）和GPU平台（sm_107a），增强项目在高端推理市场的竞争力。
- **稳定性层面**：非对齐head count修复和finalize输出尾部处理消除了特定配置下的崩溃或错误结果风险，提升框架健壮性。

## 四、值得关注的技术点

- **无barrier的跨块同步设计**：用release-published标志和parity-selected arrival counter实现自维护的交接状态，兼顾正确性与CUDA Graph可捕获性。
- **数值稳定性处理**：`blk_max = fmaxf(blk_max, 1e-10f)`的epsilon钳制，精确匹配vLLM的group-quant eps，体现对跨框架一致性的重视。
- **per-token语义下放**：将原本host端模拟的per-token causal KV范围控制下沉到kernel内，减少显存往返和kernel launch次数。
- **TMA描述符对齐修复**：对H=12等非8倍数head count，通过padding TMA源到16 heads解决`cuTensorMapEncodeTiled`的stride限制。

## 五、对项目发展的影响

这些提交表明FlashInfer正沿着**“广度扩展+深度优化”**双轨前进：一方面积极适配最新模型（DeepSeek V4）和硬件（Blackwell、sm_107a），保持技术领先性；另一方面持续打磨内核质量——修复数值边界、消除冗余计算、简化同步机制，提升生产环境的可靠性。特别是MoE和topk的优化，直接服务于vLLM等主流推理框架的集成需求，巩固其作为高性能推理内核库的生态地位。整体来看，项目正从“覆盖主流场景”向“极致优化每个路径”的阶段迈进。

## 详细提交记录

### [b567143](https://github.com/flashinfer-ai/flashinfer/commit/b567143b99fabdd671171385766bbbe302e1712c)

- **作者**: Alex Yang
- **时间**: 2026-08-05T22:40:00Z
- **提交信息**: Add @StudyingShao to CODEOWNERS for multiple sections (#4364)

Added @StudyingShao as a code owner for GEMM, Grouped GEMM, MOE, and
MOE_EP sections.

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

* **Chores**
* Updated code ownership assignments for GEMM, Grouped GEMM, and MOE
components.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [985302c](https://github.com/flashinfer-ai/flashinfer/commit/985302cb8ec7c9cb86c6f56c871d0a3f13031758)

- **作者**: myu-guo
- **时间**: 2026-08-05T21:59:52Z
- **提交信息**: Add CuTe DSL HCA backend for DeepSeek V4 sparse MLA (#3943)

## Summary

This PR adds a CuTe DSL implementation of DeepSeek V4 FP8 Heavily
Compressed Attention (HCA) for Blackwell GPUs.

- Add the SM100/SM103 HCA kernel, two-CTA clusters, split-K reduction,
persistent and non-persistent schedulers, and FlashInfer wrapper.
- Expose HCA through `trtllm_batch_decode_sparse_mla_dsv4(...,
backend="cute-dsl")` while preserving the existing `backend="auto"`
policy.
- Keep the existing API name and add the backend-neutral
`batch_decode_sparse_mla_dsv4` alias.
- Support arbitrary SWA token-row order, including ring rotation and
wraparound, while keeping the compressed cache paged.
- Add explicit metadata validation, compatibility conversion for
combined sparse tables, CUDA Graph-safe reuse of precomputed metadata,
correctness tests, and a reproducible benchmark.

The latest kernel revision distributes the four SWA K and V gather4
subtiles across W12-W15 and synchronizes them with the canonical W9/W10
producer states. It also shortens causal-mask, correction, and epilogue
live ranges while preserving full-backing causal masking and empty
split-K handling.

## Public API and metadata contract

The native CuTe DSL HCA ABI uses two addressing schemes:

- `hca_swa_indices`: INT32 absolute row indices into the flattened SWA
cache, shape `[B * Q, 128]`. Each query row may use arbitrary order,
rotation, and wraparound.
- `hca_compressed_block_tables`: INT32 physical page IDs into the
compressed cache, shape `[B * Q, max_pages]`.
- `hca_seq_lens`: INT32 backing HCA slot counts, shape `[B]`. These
drive tile-rounded TMA scheduling and count the fixed 128 SWA slots plus
compressed slots; they are neither raw sequence lengths nor effective
top-k lengths.
- `swa_topk_lens`: INT32 visible SWA lengths, shape `[B * Q]`, with
values in `[0, 128]`.
- `sparse_topk_lens`: INT32 visible total HCA lengths, shape `[B * Q]`.

This replaces the SWA page-table representation used by earlier
revisions of this PR. The compressed stream remains page-based.

Every `hca_swa_indices` entry, including masked padding, must contain a
legal flattened-cache row because gather4 reads all coordinates before
masking. Each compressed block-table row must likewise provide legal
page IDs for the complete `hca_seq_lens` footprint rounded up to
128-slot tiles, including slots later masked by a shorter
`sparse_topk_lens`.

### Explicit hot-loop path

```python
from flashinfer.mla import trtllm_batch_decode_sparse_mla_dsv4

out = trtllm_batch_decode_sparse_mla_dsv4(
    query=query,
    swa_kv_cache=swa_kv_cache,
    workspace_buffer=workspace,
    sparse_indices=None,
    compressed_kv_cache=compressed_kv_cache,
    sparse_topk_lens=sparse_topk_lens,
    swa_topk_lens=swa_topk_lens,
    backend="cute-dsl",
    hca_swa_indices=hca_swa_indices,
    hca_compressed_block_tables=hca_compressed_block_tables,
    hca_seq_lens=hca_seq_lens,
    hca_use_persistent=True,
)
```

### Compatibility conversion

The native explicit HCA ABI has no page-alignment requirement for SWA
rows. Callers whose existing combined `sparse_indices` tensor uses a
canonical page expansion for the compressed segment can precompute
reusable HCA metadata:

```python
from flashinfer.mla import (
    convert_compressed_page_aligned_sparse_indices_to_hca_metadata,
    trtllm_batch_decode_sparse_mla_dsv4,
)

metadata = convert_compressed_page_aligned_sparse_indices_to_hca_metadata(
    sparse_indices,
    sparse_topk_lens,
    seq_lens,
    swa_kv_cache,
    compressed_kv_cache,
    q_len=query.shape[1],
)

out = trtllm_batch_decode_sparse_mla_dsv4(
    query=query,
    swa_kv_cache=swa_kv_cache,
    workspace_buffer=workspace,
    sparse_indices=None,
    compressed_kv_cache=compressed_kv_cache,
    sparse_topk_lens=sparse_topk_lens,
    swa_topk_lens=metadata.swa_topk_lens,
    backend="cute-dsl",
    hca_swa_indices=metadata.hca_swa_indices,
    hca_compressed_block_tables=metadata.hca_compressed_block_tables,
    hca_seq_lens=metadata.hca_seq_lens,
    hca_is_causal=metadata.hca_is_causal,
    hca_use_persistent=True,
)
```

For `hca_sparse_indices_format="compressed-page-aligned"`, active SWA
entries may be arbitrary absolute rows. Only the compressed segment must
be a canonical expansion of `page_id * page_size + page_offset`. The old
ambiguous `"page-aligned"` tag is rejected.

The inline tagged conversion validates values, allocates metadata,
synchronizes the device, and immediately launches the kernel. It is not
CUDA Graph capture safe or intended for a latency-sensitive loop.
Precompute once and reuse the explicit metadata instead.

## Supported configuration

- SM100 and SM103 implementation target; this revision was validated on
SM100 silicon.
- Dense causal query layout `[B, Q, H, 512]`.
- FP8 E4M3 query and KV with BF16 output.
- DeepSeek V4 production configuration of 128 heads; partial final head
tiles are masked and tested.
- HND and NHD public cache-layout normalization.
- Optional per-head attention sinks, split-K reduction, and persistent
or non-persistent scheduling.
- Non-persistent launches require `B * Q <= 65535`.
- `backend="cute-dsl"` is explicit opt-in; `backend="auto"` remains
unchanged.
- CuTe DSL HCA currently requires `hca_is_causal=True`, Python-float BMM
scales, and does not support PDL or varlen `cum_seq_lens_q` input.

## Correctness and validation

Validated at final head `d847a2e6a948b283d439d2edcf3cc08226e98594` on an
NVIDIA B200:

```text
pytest -q tests/attention/test_cute_dsl_hca_dsv4.py
27 passed
```

The targeted suite covers backend routing and aliasing, HND/NHD
forwarding, rotated and wrapped SWA rows, compressed-page-aligned
conversion and rejection of the old ambiguous tag, FP8-to-BF16 numerical
comparison, sinks, partial head tiles, multiple page sizes, split-K and
all-empty contributions, full-backing causal masking, CUDA Graph
capture, persistent scheduling, and the W12-W15 four-warp gather
contract. Its randomized B=2, Q=2 parity case sends the same query, KV
pools, active logical rows, lengths, scales, and sinks to CuTe DSL and
TRTLLM-GEN; each backend is checked against the same independent PyTorch
reference and against the other backend.

Static checks also passed:

```text
git diff --check
ruff format --check --no-cache
ruff check --no-cache
```

## Final B200 CuTe DSL vs. TRTLLM-GEN comparison

The final comparison was run at
`d847a2e6a948b283d439d2edcf3cc08226e98594` on an NVIDIA B200. Here `DKG`
denotes the DKG-derived CuTe DSL backend integrated into this checkout.
Both backends consume the same logical HCA rows and are selected
explicitly; `backend="auto"` remains unchanged.

Each shape was run twice with reversed backend order. The configuration
uses 128 heads, head dimension 512, FP8 E4M3 query/cache, BF16 output,
shuffled compressed pages, rotated SWA rows, the persistent scheduler,
split-K 1, hot-L2 CUDA-event timing, a 512 MiB workspace, 100 warmups,
and 200 measured samples per round.

`DKG latency reduction` is `(TRTLLM-GEN - DKG) / TRTLLM-GEN`; positive
values favor DKG.

| B | Q | Raw KV | Max active HCA | DKG medians -> mean (us) |
TRTLLM-GEN medians -> mean (us) | DKG latency reduction | Diff
raw/public/max |
|---:|---:|---:|---:|---:|---:|---:|---:|
| 32 | 4 | 8,192 | 192 | 20.928 / 20.928 -> 20.928 | 22.880 / 22.848 ->
22.864 | 8.47% | 0 / 0 / 0 |
| 32 | 4 | 32,768 | 384 | 22.848 / 22.848 -> 22.848 | 24.896 / 24.864 ->
24.880 | 8.17% | 0 / 0 / 0 |
| 32 | 7 | 8,192 | 192 | 31.296 / 31.200 -> 31.248 | 33.184 / 33.184 ->
33.184 | 5.83% | 0 / 0 / 0 |
| 32 | 7 | 32,768 | 384 | 33.248 / 33.216 -> 33.232 | 39.264 / 39.136 ->
39.200 | 15.22% | 0 / 0 / 0 |
| 1 | 1,024 | 1,048,576 | 8,320 | 616.832 / 618.848 -> 617.840 |
1,144.096 / 1,145.136 -> 1,144.616 | 46.02% | 0 / 0 / 0 |
| 8 | 1,024 | 32,768 | 384 | 833.936 / 833.920 -> 833.928 | 848.160 /
849.088 -> 848.624 | 1.73% | 0 / 0 / 0 |

All six shapes completed both rounds. Raw and public outputs were finite
and identical between backends, and logical and encoded active-slot
counts matched. Public API execution was checked for correctness but is
excluded from this raw-kernel latency table.

---------

Co-authored-by: mingyangw <mingyangw@nvidia.com>

### [f8ca34a](https://github.com/flashinfer-ai/flashinfer/commit/f8ca34a3dbaa9a2e4d6a94888617e5f09976ef00)

- **作者**: rmhaskar
- **时间**: 2026-08-05T20:59:36Z
- **提交信息**: MSA decode path improvements (#4324)

<!-- .github/pull_request_template.md -->

## 📌 Description
Two independent changes to the SM120/SM121 MSA ops, both aimed at
per-call overhead on the decode path --

1. Paged paths rebuilt a prefix sum they did not need 
`msa_proxy_score`, `msa_proxy_score_fp4` and
`msa_sparse_decode_attention` each did this on every paged call:
```
cu_k = torch.zeros(batch_size + 1, dtype=torch.int32, device=dev)
cu_k[1:] = seqused_k.to(dev).cumsum(0)
```
so the kernel could do `seqlen_k = mCuK[b + 1] - mCuK[b]` and recover a
number the caller already had in `seqused_k`.

On the paged path `page_table` supplies every KV address, so `k_start`
is dead — it is read only in the flat branches (`sparse_decode_sm12x.py`
lines 470/474/ 633/637/648, and the equivalents in the proxy kernels).
Only `seqlen_k` is used, for masking.

The fix passes `seqused_k` straight through and takes the length
directly under a `const_expr` paged branch, so there is no runtime cost
to the distinction:

```python
if cutlass.const_expr(self._paged):
    k_start = cutlass.Int32(0)
    seqlen_k = mCuK[batch_idx]
else:
    k_start = mCuK[batch_idx]
    seqlen_k = mCuK[batch_idx + 1] - k_start
```
2. `msa_topk_select` takes only batch-wide scalars
.`num_valid_pages` and `force_end_blocks` were ints, so a caller whose
query tokens have differing causal KV extents — any decode batch, any
chunked prefill — could not express per-token semantics. The only
recourse was to post-process on the host. vLLM's MiniMax-M3 integration
does exactly that: bias each token's local window with a `scatter_` of
`FLT_MAX`, then repair the output with a comparison, a `masked_fill_`
and a `sort`.

`num_valid_pages` may now be an int32 tensor of shape `(total_qo_len,)`.
The kernel then clamps each token's candidate range to its own extent
and forces that token's own trailing `force_end_blocks`, which is what
the scatter was emulating. Consequences:

* no selected index can exceed its token's extent, so no masking pass
* the ascending, `-1`-tail-padded contract holds by construction, so no
sort
* the forced region is clamped in-kernel against `nvp`, so tokens
shorter than the local window are handled instead of underflowing to
negative blocks

Dispatch between the count-rank and radix kernels bounds by
`max_k_tiles` on this path rather than the valid-page count: reading the
tensor on the host would sync the stream, which is illegal under CUDA
graph capture.

### Measurements
RTX PRO 6000 Blackwell Server Edition (SM120), MiniMax-M3 per-GPU TP4
indexer geometry (`num_idx_heads` 1, `head_dim` 128, page 128, topk 16,
`init_blocks` 0, `local_blocks` 1), context 8192, heterogeneous
per-request extents.

Indexer selection (proxy score + top-k), kernel launches and eager wall
time per call:

| batch | launches before | after | before | after |
|-------|-----------------|-------|--------|-------|
| 1 | 27 | 7 | 341.1 us | 107.1 us |
| 4 | 27 | 7 | 337.8 us | 107.1 us |
| 16 | 27 | 7 | 334.8 us | 106.1 us |
| 64 | 27 | 7 | 337.9 us | 108.9 us |

Paged sparse decode: **7 -\> 2** launches per call
Selections are identical to the host-side sequence they replace,
verified per-token across the batch.

### End-to-end
vLLM serving MiniMax-M3 NVFP4 on 4x RTX PRO 6000, TP4, ISL 8192 / OSL
1024. . Requires the matching vLLM-side change to use FI backend for MSA

| conc | TPOT Triton | TPOT FlashInfer | ΔTPOT | TTFT Triton | TTFT
FlashInfer | ΔTTFT |

|------|-------------|-----------------|-------|-------------|-----------------|-------|
| 1 | 9.28 ms | 9.38 ms | +1.1% | 1030.1 ms | 977.4 ms | −5.1% |
| 4 | 16.17 ms | 16.16 ms | −0.1% | 1229.7 ms | 1171.6 ms | −4.7% |
| 16 | 38.99 ms | 38.24 ms | −1.9% | 2023.9 ms | 1938.4 ms | −4.2% |
| 64 | 112.68 ms | **109.63 ms** | **−2.7%** | 4699.7 ms | **4460.5 ms**
| **−5.1%** |

Before these changes the FlashInfer backend was a **+16.7% TPOT
regression at concurrency 1 and aborted outright at 4 and 16** with an
illegal memory access.

### Tests
New `tests/msa_ops/test_msa_topk_per_token.py`:

* per-token tensor equals invoking the scalar path once per token,
across `force_begin`/`force_end` combinations and at both `max_k_tiles`
values that straddle the count-rank/radix dispatch boundary (so it
cross-checks the two kernels against each other on distinct-score
inputs)
* output contract for every token, including extents shorter than the
forced region — which the scalar API rejects, so only the in-kernel
clamp handles it
* `force_end_blocks` forces each token's _own_ trailing blocks
* input guards
* CUDA-graph capture safety

The existing `tests/msa_ops/` suite passes (63 passed after fixing one
test that called the private `_get_compiled_topk` positionally).
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

- **New Features**
- Added per-token valid-page counts for top-k page selection, including
input validation and bounded results.
- Improved paged KV-cache handling with direct per-request sequence
lengths.
- Added variable-length paged FP4 decoding for general and packed
execution modes.

- **Bug Fixes**
- Corrected sequence lengths, offsets, and page boundaries across paged
and flat cache paths.
  - Improved forced-region clamping for variable-length requests.

- **Tests**
- Added coverage for heterogeneous sequences, ragged pages, validation,
bounded output, and CUDA Graph compatibility.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [af3f5e4](https://github.com/flashinfer-ai/flashinfer/commit/af3f5e45ff79eb9fd39ae161662ea07e50cf33ba)

- **作者**: yugong333
- **时间**: 2026-08-05T20:34:31Z
- **提交信息**: MoE monokernel Bug fix, barrrier remove and kernel rewrite. (#4027)

Find two bugs in previous design:
1. The cross-block handoffs counters are not reset correctly in the
scratchpad. If the scratchpad is reused the down projection will fetch
the wrong data based on the wrong status of the counter
2. inv_scale overflow on near-subnormal block maxima.

Fixes:

1. Kernel rewrite. Replace the software grid barriers with sentinel/flag
cross-block handoffs:
- Delete moe_grid_barrier.h and the grid/partial-barrier counter
protocol.
- Phase 3->4 handoff: each temp_act_scale cell is release-published
after its fp8 payload segment and doubles as the readiness flag; the
down-projection polls exactly the cells it consumes (per-expert
granularity), so no barrier-counter rendezvous is needed.
- Phase 4->5 handoff: each block bumps its column stripe's
parity-selected arrival counter; only that stripe's Phase-5 writer polls
it.
- The launch-parity double-buffer makes the handoff state
self-maintaining across CUDA-graph replays; the kernel stays capturable
with a plain launch.

2. Replace the too-narrow subnormal check with an epsilon clamp on the
block max, before computing either scale:

```
// Eps-clamp tiny maxima: blk_max slightly above FLT_MIN still overflows
// blk_inv_scale (448/blk_max > FLT_MAX for blk_max < ~1.32e-36), NaN-ing
// the whole block after the fp8 cast. 1e-10 matches vLLM's group-quant eps.
blk_max = fmaxf(blk_max, 1e-10f);

const float blk_act_scale = blk_max * FP8_MAX_INV;  // stored dequant scale
const float blk_inv_scale = FP8_MAX / blk_max;      // quant multiplier, now finite
```


3. Tests: tests/moe/test_monomoe.py gains scratchpad-reuse (no
cross-launch contamination) and small-scale correctness coverage on top
of the accuracy sweep (M in {1,2,8} x top_k {1,8}); all pass on H200.


| M | Old Kernel | Fixed Kernel |
|---|---|---|
| 1 | FAILED (reuse vs fresh: cos=0.000) | PASS (all > 0.9999) |
| 2 | FAILED (stale barrier race) | PASS (all > 0.9999) |
| 4 | FAILED (stale barrier race) | PASS (all > 0.9999) |
| 8 | PASS | PASS |


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added/standardized support for the fixed block-FP8 configuration
(E=256, N=512, K=2048).

* **Bug Fixes**
* Strengthened runtime shape and routing-input validation, including
token-cap checks and clearer failure messages.
* Improved numerical stability for small-scales and ensured scratchpad
reuse does not contaminate results.

* **Documentation**
* Refreshed MonoMoe design/docs to reflect the supported hardware,
fixed-shape constraints, and execution flow.

* **Tests**
* Updated and expanded MonoMoe FP8 reference comparisons and new
stability/scratchpad reuse coverage.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: ygkyle <ygkyle@amazon.com>
Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [aa81e71](https://github.com/flashinfer-ai/flashinfer/commit/aa81e71063afe811ca9c83edec7956db1aae54f0)

- **作者**: Matej Sirovatka
- **时间**: 2026-08-05T20:28:03Z
- **提交信息**: fix(moe): handle CuTe DSL finalize output tails (#4186)

## Summary

- clamp each fused-finalize bulk copy/reduction to the output columns
remaining
  in the current N tile
- skip the output transfer when a cluster-padding CTA has no remaining
columns
- remove the finalize-only exact-N-tiling restriction introduced by
#4086
- retain the exact-N-tiling restriction for GEMM1, whose scale-factor
output
  uses a separate unpredicated store path

## Why

The fused-finalize epilogue previously transferred one full compile-time
CTA
tile for every valid row. This is unsafe when:

1. the final N tile is only partially populated, or
2. the persistent scheduler adds a padding CTA to complete an N cluster.

#4086 prevents those cases by rejecting any finalize configuration where
`N % (mma_n * cluster_n) != 0`. That is safe, but it removes otherwise
useful
kernel configurations and can leave some widths with no eligible
configuration.

This PR fixes the transfer itself. It computes the remaining columns for
the
current tile, transfers only that many bytes, and performs no transfer
when the
tile starts beyond the output width. All CTAs still execute the existing
commit/wait/barrier sequence.

## Validation

### Correctness

Validated on NVIDIA GB200 with the newly enabled
`tile_m=256, mma_n=256, cluster_n=2` finalize configuration forced:

- `N=256`: exercises an empty cluster-padding CTA
- `N=384`: exercises a partially populated final N tile
- both numerical tests pass against the FP4 reference
- an additional 100 consecutive launches per case produced finite output
and
  left a sentinel row immediately after the output unchanged

The focused host-side `can_implement` checks, Ruff checks, and
formatting checks
also pass.

### Configuration coverage

The table counts complete GEMM1 + GEMM2 configurations exposed by the
MoE
runner:

| Output width N | #4086 base | This PR |
| ---: | ---: | ---: |
| 256 | 12 / 16 | 16 / 16 |
| 384 | 4 / 16 | 16 / 16 |
| 512 | 16 / 16 | 16 / 16 |
| 2880 | 0 / 16 | 16 / 16 |
| 4096 | 16 / 16 | 16 / 16 |

For `N=2880`, all eight newly eligible finalize configurations were also
launched directly and produced finite output.

### Existing-case performance

The finalize kernel was benchmarked in isolation so the epilogue change
was not
hidden by routing or GEMM1. The #4086 base and this PR were loaded in
the same
process and measured in alternating pairs on one GB200:

- SM clock locked to 2062 MHz
- exact-tile widths `N=512, K=512` and `N=4096, K=1024`
- all eight previously valid finalize configurations at each width
- 31 hot-cache pairs with 250 launches per measurement
- compilation excluded from timing

Lower is better. Across the 16 exact-tile comparisons:

| Measurement | Median head/base | Range of per-configuration medians |
| --- | ---: | ---: |
| Hot cache | 0.9943 | 0.9882–0.9971 |
| Cold cache | 0.9934 | 0.9629–1.0249 |

No previously supported configuration showed a hot-cache slowdown.
Cold-cache
single-launch measurements were noisier, but showed no systematic
regression.

## Scope and dependencies

This PR changes only the finalize output transfer. GEMM1 keeps the
conservative
guard from #4086.

The PR is stacked on #4086 and targets its upstream
`fix-3957-cluster-padding` branch so this diff contains only the durable
tail-handling change. It should be retargeted to `main` after #4086
merges.

The vLLM consumer is vllm-project/vllm#50030.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved fused MoE handling for partial output tiles and cluster
padding.
* Prevented unsupported configurations from being selected during
autotuning.
* Limited output operations to valid columns, avoiding incorrect or
out-of-bounds results.

* **Tests**
* Added coverage for partial and exact tile sizes across multiple hidden
dimensions.
* Added validation for configuration acceptance and rejection without
requiring GPU execution.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yang Xu <yanxu@nvidia.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: Alex Yang <aleyang@nvidia.com>

### [dc4d214](https://github.com/flashinfer-ai/flashinfer/commit/dc4d21447d04b6153c7408f2a596aee6ab0dcea9)

- **作者**: RuQing Xu
- **时间**: 2026-08-05T19:48:48Z
- **提交信息**: Upgrade CuTe DSL FMHA cubins (#4291)

<!-- .github/pull_request_template.md -->

## 📌 Description

Our internal cubin artifact has published a new set of CuTe DSL FMHA
cubins:

New cubins supported by this PR:

- mixed QK/PV dtype cubins
- blocksclaed cubins
- Rubin cubins

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
  * Added support for GPU architecture `sm_107a`.
* Enabled separate data type configuration for query/key and value
tensors, including mixed FP8 attention configurations.
* Added support for loading precompiled attention kernels with JIT
compilation fallback.

* **Improvements**
  * Enhanced sliding-window and block-scaled attention support.
  * Improved quantization-scale handling and skip-softmax configuration.
* Expanded support for different output data types, including bfloat16
and float8.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [d9c97ac](https://github.com/flashinfer-ai/flashinfer/commit/d9c97ac13247a30f5bbc29d39f88d6a415bb7dca)

- **作者**: Ziang Li
- **时间**: 2026-08-05T17:19:40Z
- **提交信息**: perf(topk): skip output index sort for tie-break selection (#4295)

<!-- .github/pull_request_template.md -->

## 📌 Description

@humansand

Follow-up to #3095.

`tie_break` determines which equal-valued elements are selected at the
top-k boundary. Today, requesting a tie-break also promotes the public
`deterministic` flag, which runs the index-ordering finalizer even
though the default API output is unsorted.

This PR separates deterministic selection from deterministic output
ordering:

- tie-break modes still use deterministic filtered selection so
`SMALL`/`LARGE` choose the intended boundary indices;
- the shared `FinalizeTopKIndicesKernel` always finalizes/remaps
indices, with `SORT_LOCAL_INDICES` as the compile-time switch for its
optional local-index radix sort;
- explicit `deterministic=True` retains the existing CUB index sort and
repeatable output order;
- tie-break with `deterministic=False` skips the finalizer entirely for
plain Top-K, while page-table/ragged transforms run only the required
remapping work;
- `can_use_clusters_topk` now receives `tie_break` and rejects tie-break
modes at the same early-exit boundary as `dsa_graph_safe`;
- API documentation, exact-set/remapping tests, and the Top-K benchmark
driver reflect that tie-breaking controls selection, not output order.

`sorted=True` remains unchanged and still requests descending value
order.

#### `sorted` and `deterministic` use different sort keys

These options are independent and should not be conflated:

| Option | Contract | Sort key/order |
|---|---|---|
| `sorted=True` | Return the selected top-k elements in score order,
matching `torch.topk(..., sorted=True)` | value descending, carrying the
corresponding index |
| `deterministic=True` | Make selection and output ordering repeatable
for a fixed input and system | on the filtered path, local/original
index ascending, carrying the corresponding value |

The deterministic filtered-path index sort is a canonicalization step;
it does **not** imply descending score order. If both options are
enabled, FlashInfer first establishes deterministic index order and then
applies a stable descending value sort. Equal values therefore retain
the deterministic prior order. For page-table and ragged transforms,
local indices are canonicalized before remapping, so the returned mapped
IDs are not necessarily numerically sorted.

`tie_break` is separate from both: it controls which equal-valued
elements are selected at the top-k boundary, not the final output order.

### Performance

Both sides used the same final benchmark driver and ran on the same
physical GPU (`CUDA_VISIBLE_DEVICES=2`) in the `flashinfer-pr4048-cu132`
devbox from the `hell` queue. Speedup is `BEFORE / AFTER`.

| Environment | Value |
|---|---|
| GPU | NVIDIA B200 (`sm100`) |
| CUDA toolkit | 13.2.1 |
| PyTorch | 2.13.0+cu132 |
| Driver | 580.126.09 |
| CUPTI Python/native | 13.2.0 / 13.2.75 |
| FlashInfer source version | 0.6.17 |
| BEFORE | `upstream/main` at `668a1ba1ca86432c79f6adad37ecfce8d06ec083`
|
| AFTER | `89c649679af75792b2cad1020c91b41bf2262adc` |
| Timing | CUPTI activity timing, no CUDA graph replay, cold L2, 10 dry
runs, 100 measured iterations, median |

The shared timer supports CUPTI with and without CUDA graphs. A control
sweep with CUPTI + CUDA graphs + cold-L2 reproduced the same
illegal-memory-access failure on both upstream `main` and this branch at
the first 128K page-table row, so it is not specific to this PR's kernel
changes. The final benchmark follows existing FlashInfer CUPTI
microbenchmarks by using `enable_cupti=True` with
`use_cuda_graph=False`; no benchmark-specific environment, global, or
CLI escape hatch remains.

Commands:

```bash
export CUDA_VISIBLE_DEVICES=2

python benchmarks/bench_topk.py \
  --op dsa_topk \
  --dtype bf16 \
  --dsa-input-pattern dsa_relu \
  --dsa-case all \
  --dsa-topk 2048 \
  --tie-break

python benchmarks/bench_topk.py \
  --op varlen \
  --dtype bf16 \
  --length-dist causal \
  --varlen-k 2048 \
  --varlen-q-len 128 \
  --tie-break
```

Summary (geometric mean across cases):

| Suite | Tie-break | Geomean speedup | Case range |
|---|---:|---:|---:|
| DSA Top-K | small | **1.141x** | 1.123x–1.182x |
| DSA Top-K | large | **1.135x** | 1.071x–1.170x |
| Varlen page-table | small | **1.080x** | 1.034x–1.145x |
| Varlen page-table | large | **1.078x** | 1.035x–1.139x |
| Varlen ragged | small | **1.121x** | 1.061x–1.186x |
| Varlen ragged | large | **1.119x** | 1.061x–1.195x |

DSA Top-K results (latency in µs):

| Case | Small BEFORE | Small AFTER | Speedup | Large BEFORE | Large
AFTER | Speedup |
|---|---:|---:|---:|---:|---:|---:|
| `decode_b1_q1_l128k` | 83.17 | 74.08 | **1.123x** | 84.54 | 72.24 |
**1.170x** |
| `decode_b8_q1_l64k` | 80.69 | 68.29 | **1.182x** | 79.04 | 67.86 |
**1.165x** |
| `decode_b32_q1_l128k` | 90.56 | 80.51 | **1.125x** | 85.92 | 80.19 |
**1.071x** |
| `prefill_b1_q128_l128k` | 91.41 | 80.51 | **1.135x** | 91.33 | 80.43 |
**1.136x** |

Variable-length transform results (latency in µs):

| Transform | Rows | Max length | Small BEFORE | Small AFTER | Speedup |
Large BEFORE | Large AFTER | Speedup |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| page-table | 512 | 16,384 | 49.06 | 42.85 | **1.145x** | 49.09 | 43.10
| **1.139x** |
| ragged | 512 | 16,384 | 47.87 | 40.35 | **1.186x** | 48.10 | 40.26 |
**1.195x** |
| page-table | 512 | 65,536 | 86.38 | 79.07 | **1.092x** | 87.66 | 80.67
| **1.087x** |
| ragged | 512 | 65,536 | 84.80 | 75.50 | **1.123x** | 85.39 | 76.99 |
**1.109x** |
| page-table | 512 | 131,072 | 99.63 | 92.54 | **1.077x** | 99.92 |
92.80 | **1.077x** |
| ragged | 512 | 131,072 | 98.61 | 89.41 | **1.103x** | 98.75 | 89.68 |
**1.101x** |
| page-table | 2,048 | 16,384 | 172.29 | 157.33 | **1.095x** | 173.63 |
158.94 | **1.092x** |
| ragged | 2,048 | 16,384 | 170.30 | 144.35 | **1.180x** | 171.66 |
145.87 | **1.177x** |
| page-table | 2,048 | 65,536 | 442.69 | 424.46 | **1.043x** | 444.54 |
426.35 | **1.043x** |
| ragged | 2,048 | 65,536 | 437.07 | 405.06 | **1.079x** | 438.82 |
406.80 | **1.079x** |
| page-table | 2,048 | 131,072 | 565.89 | 547.06 | **1.034x** | 568.35 |
548.93 | **1.035x** |
| ragged | 2,048 | 131,072 | 558.54 | 526.56 | **1.061x** | 561.33 |
529.02 | **1.061x** |

<details>
<summary>Raw BEFORE output: DSA Top-K</summary>

```text
====================================================================================================
dsa_topk: DeepSeek DSA-like indexer top-k workload (dtype=BF16, deterministic=False, dsa_pattern=dsa_relu, k=2048, tie_break=True)
NOTE: tie-break columns use deterministic=False; slowdowns use the non-deterministic baseline
====================================================================================================
                    case     rows    seq_len      k |   FlashInfer FlashInfer(det) DetSlowdown FlashInfer(tie-small)  TieSmallSlowdown FlashInfer(tie-large)  TieLargeSlowdown   torch.topk    Speedup
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
      decode_b1_q1_l128k        1     131072   2048 |      40.90us            n/a         n/a               83.17us             2.03x               84.54us             2.07x      75.44us      1.84x
       decode_b8_q1_l64k        8      65536   2048 |      40.75us            n/a         n/a               80.69us             1.98x               79.04us             1.94x      82.86us      2.03x
     decode_b32_q1_l128k       32     131072   2048 |      45.66us            n/a         n/a               90.56us             1.98x               85.92us             1.88x     112.77us      2.47x
   prefill_b1_q128_l128k      128     131072   2048 |      82.61us            n/a         n/a               91.41us             1.11x               91.33us             1.11x     197.28us      2.39x
```

</details>

<details>
<summary>Raw AFTER output: DSA Top-K</summary>

```text
====================================================================================================
dsa_topk: DeepSeek DSA-like indexer top-k workload (dtype=BF16, deterministic=False, dsa_pattern=dsa_relu, k=2048, tie_break=True)
NOTE: tie-break columns use deterministic=False; slowdowns use the non-deterministic baseline
====================================================================================================
                    case     rows    seq_len      k |   FlashInfer FlashInfer(det) DetSlowdown FlashInfer(tie-small)  TieSmallSlowdown FlashInfer(tie-large)  TieLargeSlowdown   torch.topk    Speedup
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
      decode_b1_q1_l128k        1     131072   2048 |      41.02us            n/a         n/a               74.08us             1.81x               72.24us             1.76x      73.60us      1.79x
       decode_b8_q1_l64k        8      65536   2048 |      40.69us            n/a         n/a               68.29us             1.68x               67.86us             1.67x      82.58us      2.03x
     decode_b32_q1_l128k       32     131072   2048 |      45.89us            n/a         n/a               80.51us             1.75x               80.19us             1.75x     112.69us      2.46x
   prefill_b1_q128_l128k      128     131072   2048 |      82.59us            n/a         n/a               80.51us             0.97x               80.43us             0.97x     198.18us      2.40x
```

</details>

<details>
<summary>Raw BEFORE output: variable-length transforms</summary>

```text
====================================================================================================
varlen: Variable-length segment top-k transforms (production-realistic) (dtype=BF16, length_dist=causal, k=2048, deterministic=False, tie_break=True)
NOTE: lengths model per-row valid windows; decode = independent context lengths, prefill(causal) = monotonic growth within a request (q_len=128)
NOTE: torch(mask) masks invalid positions once (outside timing) then torch.topk, isolating selection cost vs the length-aware kernel
NOTE: tie-break columns use deterministic=False; slowdowns use the non-deterministic baseline
NOTE: Clusters column omitted under deterministic/tie-break (clusters requires the non-deterministic path)
====================================================================================================
  regime       dist   transform     rows   reqs   max_len      k |  len_min  len_mean  len_max  triv% |   FlashInfer FlashInfer(det) DetSlowdown FlashInfer(tie-small)  TieSmallSlowdown FlashInfer(tie-large)  TieLargeSlowdown   torch(mask)   Speedup
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 prefill     causal  page_table      512      4     16384   2048 |      375    7109.2    12411  25.0% |      30.34us            n/a         n/a               49.06us             1.62x               49.09us             1.62x      153.26us     5.05x
 prefill     causal      ragged      512      4     16384   2048 |      375    7109.2    12411  25.0% |      27.33us            n/a         n/a               47.87us             1.75x               48.10us             1.76x      152.34us     5.57x
 prefill     causal  page_table      512      4     65536   2048 |     2039   22253.8    37156   2.0% |      65.44us            n/a         n/a               86.38us             1.32x               87.66us             1.34x      308.99us     4.72x
 prefill     causal      ragged      512      4     65536   2048 |     2039   22253.8    37156   2.0% |      60.43us            n/a         n/a               84.80us             1.40x               85.39us             1.41x      309.34us     5.12x
 prefill     causal  page_table      512      4    131072   2048 |      524   33177.8   101452  25.0% |     152.19us            n/a         n/a               99.63us             0.65x               99.92us             0.66x      592.27us     3.89x
 prefill     causal      ragged      512      4    131072   2048 |      524   33177.8   101452  25.0% |     144.70us            n/a         n/a               98.61us             0.68x               98.75us             0.68x      591.23us     4.09x
 prefill     causal  page_table     2048     16     16384   2048 |      416    7917.1    15346  12.5% |     122.30us            n/a         n/a              172.29us             1.41x              173.63us             1.42x      366.67us     3.00x
 prefill     causal      ragged     2048     16     16384   2048 |      416    7917.1    15346  12.5% |     111.49us            n/a         n/a              170.30us             1.53x              171.66us             1.54x      367.58us     3.30x
 prefill     causal  page_table     2048     16     65536   2048 |     7804   36260.2    63720   0.0% |     318.27us            n/a         n/a              442.69us             1.39x              444.54us             1.40x     1114.34us     3.50x
 prefill     causal      ragged     2048     16     65536   2048 |     7804   36260.2    63720   0.0% |     298.85us            n/a         n/a              437.07us             1.46x              438.82us             1.47x     1114.48us     3.73x
 prefill     causal  page_table     2048     16    131072   2048 |     7095   60508.9   124975   0.0% |     870.77us            n/a         n/a              565.89us             0.65x              568.35us             0.65x     2000.19us     2.30x
 prefill     causal      ragged     2048     16    131072   2048 |     7095   60508.9   124975   0.0% |     849.74us            n/a         n/a              558.54us             0.66x              561.33us             0.66x     2001.38us     2.36x
```

</details>

<details>
<summary>Raw AFTER output: variable-length transforms</summary>

```text
====================================================================================================
varlen: Variable-length segment top-k transforms (production-realistic) (dtype=BF16, length_dist=causal, k=2048, deterministic=False, tie_break=True)
NOTE: lengths model per-row valid windows; decode = independent context lengths, prefill(causal) = monotonic growth within a request (q_len=128)
NOTE: torch(mask) masks invalid positions once (outside timing) then torch.topk, isolating selection cost vs the length-aware kernel
NOTE: tie-break columns use deterministic=False; slowdowns use the non-deterministic baseline
NOTE: Clusters column omitted under deterministic/tie-break (clusters requires the non-deterministic path)
====================================================================================================
  regime       dist   transform     rows   reqs   max_len      k |  len_min  len_mean  len_max  triv% |   FlashInfer FlashInfer(det) DetSlowdown FlashInfer(tie-small)  TieSmallSlowdown FlashInfer(tie-large)  TieLargeSlowdown   torch(mask)   Speedup
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 prefill     causal  page_table      512      4     16384   2048 |      375    7109.2    12411  25.0% |      30.30us            n/a         n/a               42.85us             1.41x               43.10us             1.42x      153.52us     5.07x
 prefill     causal      ragged      512      4     16384   2048 |      375    7109.2    12411  25.0% |      27.39us            n/a         n/a               40.35us             1.47x               40.26us             1.47x      152.86us     5.58x
 prefill     causal  page_table      512      4     65536   2048 |     2039   22253.8    37156   2.0% |      65.34us            n/a         n/a               79.07us             1.21x               80.67us             1.23x      309.01us     4.73x
 prefill     causal      ragged      512      4     65536   2048 |     2039   22253.8    37156   2.0% |      60.45us            n/a         n/a               75.50us             1.25x               76.99us             1.27x      310.05us     5.13x
 prefill     causal  page_table      512      4    131072   2048 |      524   33177.8   101452  25.0% |     152.22us            n/a         n/a               92.54us             0.61x               92.80us             0.61x      591.52us     3.89x
 prefill     causal      ragged      512      4    131072   2048 |      524   33177.8   101452  25.0% |     144.75us            n/a         n/a               89.41us             0.62x               89.68us             0.62x      591.46us     4.09x
 prefill     causal  page_table     2048     16     16384   2048 |      416    7917.1    15346  12.5% |     122.27us            n/a         n/a              157.33us             1.29x              158.94us             1.30x      366.85us     3.00x
 prefill     causal      ragged     2048     16     16384   2048 |      416    7917.1    15346  12.5% |     111.52us            n/a         n/a              144.35us             1.29x              145.87us             1.31x      366.70us     3.29x
 prefill     causal  page_table     2048     16     65536   2048 |     7804   36260.2    63720   0.0% |     318.19us            n/a         n/a              424.46us             1.33x              426.35us             1.34x     1113.92us     3.50x
 prefill     causal      ragged     2048     16     65536   2048 |     7804   36260.2    63720   0.0% |     298.83us            n/a         n/a              405.06us             1.36x              406.80us             1.36x     1114.29us     3.73x
 prefill     causal  page_table     2048     16    131072   2048 |     7095   60508.9   124975   0.0% |     870.80us            n/a         n/a              547.06us             0.63x              548.93us             0.63x     1999.70us     2.30x
 prefill     causal      ragged     2048     16    131072   2048 |     7095   60508.9   124975   0.0% |     849.66us            n/a         n/a              526.56us             0.62x              529.02us             0.62x     2000.72us     2.35x
```

</details>

## 🔍 Related Issues

- Follow-up to #3095.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used my preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

```text
python -m pytest -q tests/utils/test_topk.py
1396 passed, 2 warnings in 75.78s

pre-commit run --all-files
all hooks passed
```

Coverage includes:

- unordered exact-set checks for `SMALL`/`LARGE` tie-break output;
- an explicit clusters override that verifies tie-break modes take the
filtered path;
- page-table/ragged transforms with non-identity remapping;
- explicit `deterministic=True` ordering for plain and transform APIs;
- BF16 long-context filtered Top-K at 128K sequence length and `k=2048`.

## Reviewer Notes

The intended contract is:

- `tie_break` controls deterministic boundary selection only;
- `deterministic=True` additionally requests repeatable output ordering;
- `sorted=True` continues to request descending value order.

The key implementation detail is keeping `DETERMINISTIC` for filtered
selection. The shared `FinalizeTopKIndicesKernel` always performs final
mapping/writeback; `SORT_LOCAL_INDICES` independently controls its
pre-writeback CUB sort. Transformed tie-break outputs retain the remap
path with sorting disabled, while plain tie-break output skips the
finalizer entirely.

The benchmark driver keeps CUPTI enabled and disables CUDA graph replay,
matching other FlashInfer CUPTI microbenchmarks. This avoids adding a
benchmark-global variable, environment setting, or CLI fallback solely
for this workload.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Behavior Updates**
* Tie-breaking and deterministic ordering are now controlled
independently.
* Selecting a tie-break option no longer automatically enables
deterministic execution.
* Deterministic mode provides consistent index ordering; tie-breaking
alone does not guarantee output order.
* Clustered execution avoids unsupported tie-break and graph-safe
combinations.
* Page-table and ragged Top-K transformations preserve correct ordering
and index mappings.

* **Benchmarking**
* Top-K benchmarks now provide more consistent timing comparisons
against the nondeterministic baseline.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [6c85301](https://github.com/flashinfer-ai/flashinfer/commit/6c85301d3bb5d9dae06c4bdc098df7e12c9af4f2)

- **作者**: Brian K. Ryu
- **时间**: 2026-08-05T11:41:30Z
- **提交信息**: Revert "test: Add sharding support to scripts/task_run_unit_tests.sh" (#4344)

Reverts flashinfer-ai/flashinfer#4141

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Unit test execution now discovers tests automatically from the
configured test path or default test directory.
* Tests can run in parallel, with improved handling for missing optional
packages.
  * Added clearer errors when no tests are found.
  * Added automatic preparation for specific CUDA 13 test scenarios.

* **Bug Fixes**
* NVFP4 quantization regression tests now skip unsupported GPU
architectures safely.

* **Refactor**
* Simplified test execution by removing legacy sharding and
estimate-management workflows.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [38bf507](https://github.com/flashinfer-ai/flashinfer/commit/38bf507f9c9eba6b4544bee016d2bdf9c4fed02b)

- **作者**: eigen
- **时间**: 2026-08-05T08:22:49Z
- **提交信息**: fix(cake_kda): support non-aligned recurrent prefill head counts (#4351)

Follow-up to merged #4262 and #4313.

## What changed

- pad the beta-only TMA source to `round_up(H, 8)` instead of only
padding `H < 8`;
- teach the beta pack kernel and binding validation to use the dynamic
padded-head stride;
- retain the caller-visible `H`, state shape, launch grid, and frozen
M64/M128 CUDA bodies unchanged;
- add H=12 eager, packed, full-chunk-plus-tail, final-state, and CUDA
graph replay coverage.

The frozen kernels load beta in 8-head TMA boxes. For H=12, the original
BF16 row stride is 24 bytes and `cuTensorMapEncodeTiled` rejects it.
Padding the descriptor source to 16 heads gives a 32-byte row stride;
heads 12–15 are padding only and are never assigned CTAs.

This generalizes the fix to every positive head count that is not
divisible by eight, while aligned head counts retain the existing
zero-copy beta path.

## Correctness

Both runs used the public `flashinfer.recurrent_kda` facade and compared
BF16 output plus the complete final state against the PyTorch reference
with `atol=rtol=1e-2`.

| GPU | Compute capability | CUDA | Result |
| --- | --- | --- | --- |
| NVIDIA B200 | 10.0 | 12.9 | `62 passed, 0 skipped, 0 failed` |
| NVIDIA GB300 | 10.3 | 12.9 | `62 passed, 0 skipped, 0 failed` |

The test gate runs:

```text
tests/jit/test_flash_kda_jit.py
tests/kda/test_recurrent_kda_prefill.py
```

H=12 coverage includes fixed T=32, fixed T=33 (one full TMA chunk plus
the direct-load tail), packed sequence lengths `[32, 3]`, in-place
initial/final state, and CUDA graph replay after beta is changed. The
JIT contract test also verifies that the frozen generated M64/M128
bodies remain unchanged.

`pre-commit run --files <changed files>` passes.

## Performance

The H=12 path was benchmarked through the public
`flashinfer.recurrent_kda` facade with fallback forbidden. Speedup is
the official FlashKDA raw GPU span divided by this PR's public-API GPU
span. The baseline is the same official FlashKDA source used for #4262:
[`MoonshotAI/FlashKDA@d2ff19a`](https://github.com/MoonshotAI/FlashKDA/commit/d2ff19a6a0c82f39f796f637ebd1c36090b1268f),
with CUTLASS `5c149f5`.

Measurements use strict CUPTI first-to-last correlated compute-kernel
span, cold L2, no CUDA Graph, and two independent 128-sample blocks in
symmetric ABCCBA order. The PR span includes both the beta pack and
frozen M128 recurrence kernels. All six benchmark shapes passed output
and complete-final-state correctness against the official peer with BF16
`atol=rtol=1e-2`.

| H=12 shape | SM100 / B200: PR / baseline | Speedup | SM103 / GB300: PR
/ baseline | Speedup |
| --- | ---: | ---: | ---: | ---: |
| packed `[512] x 32` | 136.159 / 240.239 us | **1.7644x** | 128.264 /
233.496 us | **1.8204x** |
| packed `[128] x 8` | 23.760 / 46.448 us | **1.9549x** | 25.712 /
52.904 us | **2.0576x** |
| fixed `[512]` | 46.184 / 76.383 us | **1.6539x** | 47.712 / 82.240 us
| **1.7237x** |
| fixed `[8192]` | 514.197 / 814.435 us | **1.5839x** | 487.161 /
779.426 us | **1.5999x** |
| mixed `[1300, 547, 2048, 963, 271, 3063]` | 208.647 / 351.550 us |
**1.6849x** | 198.216 / 340.913 us | **1.7199x** |
| uniform `[1024] x 8` | 82.080 / 162.703 us | **1.9823x** | 78.440 /
162.505 us | **2.0717x** |
| **Six-shape geometric mean** | | **1.7645x** | | **1.8238x** |

| Comparison | Result |
| --- | --- |
| FlashInfer upstream main at H=12 | `unsupported / N/A` |

Upstream main fails before kernel launch with `cuTensorMapEncodeTiled
failed for beta_tma with CUresult=1`, so there is no valid upstream H=12
timing or speedup claim. This PR leaves the frozen compute kernel
unchanged; it adds the required beta packing only for non-8-aligned head
counts.

Related to #4254.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

- **Bug Fixes**
- Improved beta padding for head counts that are not divisible by eight.
- Ensured packed inputs correctly handle larger, non-aligned head
counts.
  - Added validation for padded storage requirements.

- **Documentation**
  - Clarified beta padding behavior and public tensor shapes.

- **Tests**
- Expanded coverage for 12-head inputs, varied sequence lengths, chunk
boundaries, packed inputs, and CUDA graph updates.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-08-06
**监控日期**: 2026-08-05
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3922
- **最后更新**: 2026-08-05T19:47:11Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 2
- **主要提交者**: William Lin, Shao Duan

## AI分析总结

### 主要更新类型
本次提交包含 **1项CI/测试基础设施增强** 和 **2项Bug修复**，无新功能或性能优化。

### 关键变更点与项目方向
1. **CI黄金通道（fb7be2f）**：为所有SSIM覆盖的模型家族添加单层位级DiT指纹比对，用于CI回归测试。这强化了FastVideo作为**高可靠性视频生成框架**的定位，确保模型输出在迭代中不退化。
2. **GB200设备表修复（ab00392）**：补充NVIDIA GB200到SSIM设备白名单，修正此前遗漏，保证新硬件平台上的测试正确性。
3. **Wan I2V训练修复（9f1e7c1）**：修复Wan图像到视频（I2V）模型中，CLIP图像条件以张量形式传入训练时被静默丢弃的问题——这是**直接影响训练质量的关键缺陷**。

### 项目影响与潜在意义
- **CI指纹机制**是质量保障的里程碑，使多模型、多硬件场景下的回归检测自动化，降低社区贡献引入隐性破坏的风险。
- **GB200修复**确保最新GPU架构被正确识别，为高端硬件用户提供无缝体验。
- **Wan I2V修复**直接提升训练效果，避免模型忽略图像条件导致生成视频与输入图像脱节，对依赖I2V能力的用户（如电商、创意工具）意义重大。

### 值得关注的技术点
- **位级DiT指纹**：通过单层位运算生成模型输出指纹，比传统数值比较更高效且对微小变化敏感，适合大规模CI。
- **SSIM设备白名单**：表明项目使用结构相似性指标作为质量门禁，且需按硬件型号动态管理，体现对跨平台一致性的重视。
- **张量条件传递**：修复揭示了训练管线中条件编码路径的脆弱性，提示未来需加强输入格式的单元测试覆盖。

### 对项目发展的影响
FastVideo定位为**高效、可扩展的视频生成框架**，本次提交在三个维度巩固其基础：
- **可信度**：CI指纹机制让社区协作更安全，吸引更多外部贡献。
- **硬件适配**：及时跟进GB200等新平台，保持对前沿算力的支持。
- **核心能力**：Wan I2V修复直接提升模型实用性，强化其在图像驱动视频生成场景的竞争力。

整体来看，这些提交虽小，但精准补齐了质量保障、硬件兼容和训练正确性的短板，为后续功能迭代奠定了更稳固的工程基础。

## 详细提交记录

### [fb7be2f](https://github.com/hao-ai-lab/FastVideo/commit/fb7be2fe2cf726cf6ffee92f4f96082a77056d7e)

- **作者**: William Lin
- **时间**: 2026-08-05T19:47:03Z
- **提交信息**: [ci]: add golden-gate lane — single-layer bitwise DiT fingerprints for all SSIM-covered families (#1682)

### [ab00392](https://github.com/hao-ai-lab/FastVideo/commit/ab00392664fe30a282c2b8ad2d5f357b00b7732f)

- **作者**: William Lin
- **时间**: 2026-08-05T17:33:46Z
- **提交信息**: [bugfix]: add GB200 to the inline SSIM device tables #1676 missed (#1681)

### [9f1e7c1](https://github.com/hao-ai-lab/FastVideo/commit/9f1e7c19d283a1ee11749b4fd74e45c9a9bb2b1d)

- **作者**: Shao Duan
- **时间**: 2026-08-05T08:35:09Z
- **提交信息**: [bugfix] Wan I2V: CLIP image conditioning silently dropped when passed as a tensor during training (#1673)

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-08-06
**监控日期**: 2026-08-05
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34240
- **最后更新**: 2026-08-05T20:15:24Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 3
- **主要提交者**: apolinário, Álvaro Somoza, Akshan Krithick

## AI分析总结

## 提交分析总结

### 1. 主要更新类型
- **功能新增**：引入 MiniMax-H3 模型支持（#14355）
- **Bug修复**：修复量化加载问题（#14398）、修正测试失败（#14371）
- **测试优化**：迁移测试使用 `assert_tensors_close` 断言（#14369）
- **重构与文档**：模块化重构、自动文档字符串更新

### 2. 关键变更点与项目方向
- **MiniMax-H3 集成**：这是核心变更，为 diffusers 添加了新模型架构支持，符合项目持续扩展模型生态的方向。提交中特别强调“模块化”设计，与 diffusers 的模块化架构理念一致。
- **量化支持**：SDNQ Minimax H3 加载修复，表明项目在推进低资源部署能力，与 HuggingFace 生态对推理效率的重视相符。
- **测试基础设施改进**：统一使用 `assert_tensors_close`，提升测试可靠性和可维护性。

### 3. 对项目的影响与意义
- **模型覆盖扩展**：MiniMax-H3 的加入丰富了视频生成/编辑能力，增强项目在多媒体生成领域的竞争力。
- **工程实践优化**：模块化重构和文档自动化（`make modular-autodoctrings`）降低了维护成本，提高了代码质量门槛。
- **社区协作模式**：提交中提及 Claude Opus 5 的合著，反映了 AI 辅助开发在开源项目中的实际应用趋势。

### 4. 值得关注的技术点
- **VAE float32 固定策略**：在 `torch_dtype` 转换下保持 VAE 为 float32，这是数值稳定性的关键设计决策。
- **流式卸载下的量化范围控制**：明确“禁用低 CPU 内存使用”在流式卸载场景下的限制，体现对资源管理的精细考量。
- **模块化自动文档陷阱**：`modular_auto_docstring.py` 对 `ruff` 的静默降级问题，暴露了工具链依赖的脆弱性，值得后续改进。
- **状态契约重构**：`condition_latents` 的语义澄清（编码器输出 vs 去噪后状态），反映了对模型内部数据流的深入理解。

### 5. 对项目发展的影响
基于 README 中 diffusers 作为“最先进的扩散模型库”的定位，这些提交：
- **巩固技术领先地位**：通过快速集成新模型（MiniMax-H3）和优化量化路径，保持对前沿研究的响应速度。
- **强化工程可靠性**：测试迁移和文档自动化提升了项目可持续维护性，为社区贡献者降低参与门槛。
- **推动生态整合**：与 HuggingFace 内部工具链（如 `hf-internal-testing` 仓库）的协同，强化了平台生态的闭环。

总体而言，这批提交体现了 diffusers 在“广度扩展”（新模型）与“深度优化”（量化、测试、文档）上的平衡发展，符合其作为生产级工具库的定位。

## 详细提交记录

### [9f169d9](https://github.com/huggingface/diffusers/commit/9f169d98d0bce392a889c3b6524d0d97734dfc0e)

- **作者**: Álvaro Somoza
- **时间**: 2026-08-05T20:14:36Z
- **提交信息**: [Quantization] SDNQ Minimax H3 loading (#14398)

fix

### [f53d552](https://github.com/huggingface/diffusers/commit/f53d552036a0d1bd5570782a39cd40cfabf112bc)

- **作者**: apolinário
- **时间**: 2026-08-05T17:00:38Z
- **提交信息**: Add MiniMax-H3 (#14355)

* Add MiniMax-H3

* Keep the MiniMax-H3 VAEs in float32 under torch_dtype casts

* Make MiniMax-H3 modular only

* Assert the VAE float32 pin as a positive contract

* Point the modular tests at the hf-internal-testing tiny repo

* Document performance recipes per hardware class

* Slim hardware loading snippets and PR install note

* Use pinnable int8 config and freeze quantized components

* Scope load time quantization and disable low cpu mem usage under streamed offload

* Minimax h3 follow up (review & refactor) (#14371)

review & refactor

* Regenerate the modular auto docstrings and restyle the H3 docstrings

`make modular-autodoctrings` and `make quality` both failed on CI. The nine
`# auto_docstring` blocks in `modular_blocks_minimax_h3.py` were stale, and the
docstrings of eleven files had not been through `doc-builder style`.

Nothing but docstrings and comments changes here.

One trap worth recording: `utils/modular_auto_docstring.py` shells out to
`ruff` and degrades silently when it is not on `PATH` ("Warning: tool not
found ... Skipping formatting"), which makes it rewrite 42 unrelated pipelines
instead of the one that is stale.

Co-Authored-By: Claude Opus 5 <noreply@anthropic.com>

* Fix the H3 fast tests against the refactored state contract

`condition_latents` is the VAE encoder block's own output — a list of one latent
per condition — and the after-denoise step unpacks `latents` and drops the
conditioning rows, so neither is meaningful once a request has come back. The
end-to-end tests no longer reach for them; a new standalone test runs
`MiniMaxH3KeyframeVaeEncoderStep` on its own, which is where the list is real.

Three other tests were failing for reasons of their own:

- `test_check_inputs_references` was missing its `@parametrize` and errored at
  collection. Added four cases that hit real validation.
- The duration ceiling had drifted between the two blocks that check it.
  `before_denoise` warned and reassigned before validating, so it reported `got
  362` — a count the caller never passed, right after warning it had rounded
  their 346. It now validates first, like `before_encoder` already did, and both
  messages read `got 346 (rounded up to 362)`.
- `height` without `width` raised `TypeError: unsupported operand type(s) for %:
  'NoneType' and 'int'` on `t2va`, and died inside the resize on `fl2va`. Both
  blocks now raise the same error `MiniMaxH3Ref2VASetupStep` already raised.

58 passed -> 71 passed, 5 failed, no errors. What is left: `output_type="latent"`
has no opt-out in the video decode block, `reference_image_short_edge` is a
constructor argument so it does not survive save/reload, an image reference is
PIL-only where the test expects three layouts, and `test_float16_inference`,
which fails on the base branch too.

Co-Authored-By: Claude Opus 5 <noreply@anthropic.com>

* Stop claiming `num_inference_steps` is optional in the H3 tests

The block declares it `InputParam.template("num_inference_steps", required=True)`
and `expected_workflow_defaults` lists it under `required_inputs` for all three
workflows, so `optional_params` said the opposite in the same file. It was
inherited from the mixin's default set and never examined.

Nothing enforces the requirement today: `_check_inputs` substitutes the declared
default before it tests `required`, and the template carries `default=50`, so
omitting the input runs 50 steps rather than raising. That is not specific to
H3 — 14 call sites on main are in the same position — and it is tracked in #14388.

Co-Authored-By: Claude Opus 5 <noreply@anthropic.com>

* Fix the two-card recipe, and stop accepting `output_type="latent"`

The two-card section did not run, on this branch or on the base one. A pipeline
resolves a single execution device for all of its components, so the documented
shape — one pipeline whose conditioner is `device_map`ped to the second card and
whose denoiser is moved to the first — built the rotary positions on `cuda:1` and
handed them to a transformer on `cuda:0`:

    transformer_minimax_h3.py, in Rope.forward
    RuntimeError: Expected all tensors to be on the same device, but found at
    least two devices, cuda:1 and cuda:0!

Reproduced against `abc5e9bf7` too, so it is not something the refactor broke;
the section went in as a plausible recipe that was never executed.

The split is therefore between pipelines rather than inside one: pop the text
encoder block into a conditioner of its own, give each pipeline a
`ComponentsManager` pinned to a card, and pass the state from one call to the
other. The managers' hooks are what align `prompt_embeds` onto the denoiser's
card; placing the components by hand instead works too, but then that one tensor
has to be moved explicitly. Verified end to end against the tiny fixture.

`output_type="latent"` is separate. It is not an output format — a request that
wants latents runs a pipeline without the decode blocks — and it used to run the
whole VAE decode before dying inside `postprocess_video` with "latent does not
exist", which does not say what to do instead. The video decode block now rejects
anything it cannot postprocess, before decoding. `test_output_type` covers the
three formats it does accept, and the rejection is a `test_check_inputs` case.

Co-Authored-By: Claude Opus 5 <noreply@anthropic.com>

* Skip the workflow tests whose tiny repositories cannot serve them

`test_from_pretrained_workflow`, `test_load_components_workflow` and
`test_unload_components` build a pipeline from `pretrained_model_name_or_path`
and compare it against the test class's own blocks. Three fixtures cannot answer
that, in three different ways, and none of them is about the pipelines' code:

- `tiny-anima-modular-pipe` has no `modular_model_index.json`. Anima assembles
  its dummy components in `get_pipeline` and never loads from a repository, so
  the path it declares had never been exercised.
- `tiny-flux2-klein-modular` names `Flux2KleinBaseAutoBlocks` while its
  `_class_name` and `is_distilled` both say distilled. `from_pretrained` honours
  `_blocks_class_name`, so it builds base blocks, which declare a `guider` the
  distilled ones do not.
- `tiny-qwenimage-edit-modular` names `QwenImageModularPipeline`, so
  `from_pretrained` falls back to `QwenImageAutoBlocks`, which declares no
  `image_conditioned` workflow.

Skipped with a TODO each, since the fixes are Hub-side. The klein and qwenimage
ones are a single key in `modular_model_index.json`; Anima needs a repository
published.

Co-Authored-By: Claude Opus 5 <noreply@anthropic.com>

* Declare `reference_image_short_edge` as pipeline config

`MiniMaxH3Ref2VASetupStep` resolves three pieces of released-checkpoint geometry
— the canvas short edge, the canvas area cap, and the separate short edge an
image reference is encoded at — and declared only the first two as `ConfigSpec`s.
The third was a constructor argument, so it did not survive a save and reload:
the reloaded pipeline rebuilt the block from the repository, took the 2048
default instead of the 64 the tests configure, resized reference images at a
different resolution, and landed 0.398 away from the original output.

All three now sit together, which is also what lets the test fixture stop
reaching into the block tree to swap in a configured copy — the shrunken
geometry is one `update_components` call next to the canvas rule it belongs
with, and `test_reference_image_geometry` exercises the released default rather
than constructing the block with an explicit 2048.

Co-Authored-By: Claude Opus 5 <noreply@anthropic.com>

* Accept a reference image in the three layouts a video reference takes

`MiniMaxH3VideoReference.frames` takes a list of images, a channels-last array
or a channels-first tensor; `MiniMaxH3ImageReference.image` took a PIL image
only, and the two array layouts failed on `entry.image.size` — an element count
on numpy, a bound method on torch — with `TypeError: 'int' object is not
subscriptable`.

Passing an array through as-is would have been worse than the crash. The resize
would silently drop to `F.interpolate`'s nearest-neighbour where a PIL image
gets LANCZOS, and the VAE encode does `np.array(image).permute(2, 0, 1)`, which
fixes the axes of an image and scrambles those of a channels-first tensor. So
the layouts are normalized onto a PIL image before any of that, through the
processor component the block already declares: `pt_to_numpy` for the channel
axis and `numpy_to_pil` for the array. Neither converts dtype, and
`numpy_to_pil` scales by 255, so `uint8` is normalized on the original object
first — after `pt_to_numpy` a `uint8` tensor is floats over `[0, 255]` and a
later dtype check would miss it.

Co-Authored-By: Claude Opus 5 <noreply@anthropic.com>

* Read the model's constants off the pipeline rather than the module

`before_denoise.py` imported `MINIMAX_H3_AUDIO_CHANNELS`, `MINIMAX_H3_AUDIO_TAG`
and `MINIMAX_H3_VIDEO_TAG` and read them inside its layout builders, even though
two of the three were already exposed as pipeline properties and used that way
everywhere else. They are arguments now, passed from `components.*` at the two
`__call__` sites; `audio_tag` needed the property `text_tag` and `video_tag`
already had, which is presumably why it was the one still reaching for the
global.

Same treatment where a helper cannot see a pipeline: `resolve_canvas_size` and
`audio_latent_num_frames` take the constants as default arguments instead of
closing over them, and `_normalize_video_condition` takes the rate it resamples
onto, so `before_encoder.py` imports none of them at all. What is left of the
constants is their definitions, the properties that expose them, and default
argument values.

Two helpers with a single caller each are inlined at it: the two rotary-time
sums, which are a parity contract — the reference sums the same series pairwise
in one place and sequentially in the other, and the orders differ in the last
ulp from 16 latent frames onwards. Both inlined sums are bit-identical to the
functions they replace across 1..399 latent frames, and the two still disagree
on 373 of those counts. `_frame_position_grid` stays, and `build_packed_sequence`
now calls it rather than repeating its five lines.

Co-Authored-By: Claude Opus 5 <noreply@anthropic.com>

* Reject a reference video too short for the conditioner to read

The conditioner reads a reference video at 2 fps and Qwen3-VL merges the sampled
frames in groups of two, so anything under 13 frames at 24 fps samples down to a
single frame and dies inside transformers:

    image_processing_glm4v.py
    ValueError: t:1 must be larger than temporal_factor:2

which names neither the reference nor the rate that produced it, and only fires
on the versions carrying that check — it passed locally and failed on CI.
`_sample_video_condition_frames` now rejects it where the sampling happens, with
the bound derived from the rates rather than hardcoded: "must run at least 13
frames at 24 fps (0.54 seconds), got 4".

`test_reference_media_layouts` was building exactly such a reference, four
frames, which is what surfaced this. It uses a second of video now, like
`test_reference_combinations` already did.

Co-Authored-By: Claude Opus 5 <noreply@anthropic.com>

* Drop the padded-layout attention mask

`forward` built a boolean attention mask whenever a row carried a negative
modality tag, reproducing the reference implementation's `cu_seqlens = [0, used,
S]` split of the padding tail it adds for FlashAttention. Nothing in this port
ever produces such a row: both packers partition `[0, sequence_length)` and write
only the text, audio and video tags, so the branch was unreachable and the mask
was never built. The `clamp(min=0)` that kept a `-1` from indexing the AdaLN
table backwards goes with it.

Removing it is not only dead-code removal. `if bool(is_pad.any())` is a
data-dependent branch, which has no fullgraph representation, and it was the
reason whole-model `fullgraph=True` compilation and `torch.export` were skipped:

    4 passed, 1 skipped     tests -k "compile or export or aot"

Both now run. The model tests go from 40 passed / 4 skipped to 41 passed /
2 skipped, against the same 8 pre-existing memory-offload failures.

`attention_mask` stays on the processor, attention and block signatures — it is
the signature every other processor in diffusers has, and a custom one may want
it — but the model itself never passes anything but `None`, so attention runs
unmasked over the one document and every backend stays available.

Two of the four documentation examples have been re-run against this and come
back bit-identical, frames and audio: `t2va` at the full 768x1344 canvas and
`fl2va`. The two `ref2va` ones are still to run.

Co-Authored-By: Claude Opus 5 <noreply@anthropic.com>

* Apply suggestions from code review

Co-authored-by: Steven Liu <59462357+stevhliu@users.noreply.github.com>

---------

Co-authored-by: YiYi Xu <yixu310@gmail.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>
Co-authored-by: Steven Liu <59462357+stevhliu@users.noreply.github.com>

### [191984b](https://github.com/huggingface/diffusers/commit/191984ba60b2c9bd3e8477157e7ea0173f84f97d)

- **作者**: Akshan Krithick
- **时间**: 2026-08-05T14:06:11Z
- **提交信息**: use assert_tensors_close in the migrated pipeline tests (#14369)

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-08-06
**监控日期**: 2026-08-05
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 430
- **最后更新**: 2026-08-05T05:40:44Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-08-06
**监控日期**: 2026-08-05
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12841
- **最后更新**: 2026-08-05T17:56:01Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Zhongjie Duan

## AI分析总结

1. **主要更新类型**：Bug修复。提交标题明确为“Fix audio resampling issues”，属于音频处理模块的缺陷修复，不涉及新功能或重构。

2. **关键变更点**：修复了音频重采样（resampling）过程中的问题。在DiffSynth-Studio中，音频重采样通常用于视频生成任务中同步音频与视频帧率，或在不同采样率之间转换音频数据。该修复直接关联项目核心能力——多模态内容生成（如图像、视频、音频的协同合成），确保生成结果在时间轴上音频与视觉内容对齐。

3. **对项目的影响**：修复音频重采样可提升生成视频的音频质量，减少因采样率不匹配导致的音画不同步、噪声或失真。这对依赖音频-视频联合生成的用户（如AI视频创作、数字人）至关重要，能增强工具在专业场景下的可靠性，减少用户手动后处理成本。

4. **值得关注的技术点**：重采样算法通常涉及插值、滤波或时域/频域变换，修复可能针对特定采样率组合（如44.1kHz与48kHz）的边界情况，或处理浮点精度导致的累积误差。此类修复往往需要平衡计算效率与音频保真度，可能涉及对现有音频管线的局部优化，而非全局重构。

5. **对项目发展的影响**：DiffSynth-Studio定位为“可定制、可扩展的生成式AI工具包”，强调多模态创作。音频修复虽是小改动，但直接提升用户体验的“完成度”——用户更可能将生成内容直接用于成品，而非仅作原型。这有助于项目在竞争激烈的生成式AI工具中建立“精细打磨”的口碑，吸引对输出质量要求高的创作者。长期看，此类针对性修复积累可降低技术债务，为后续扩展更复杂的音频-视频交互功能（如语音驱动动画）奠定稳定基础。

## 详细提交记录

### [928e04b](https://github.com/modelscope/DiffSynth-Studio/commit/928e04b70c7ddeb13d5992ef2b0e9a78a2a7a254)

- **作者**: Zhongjie Duan
- **时间**: 2026-08-05T11:05:09Z
- **提交信息**: Fix audio resampling issues (#1565)

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-08-06
**监控日期**: 2026-08-05
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 31360
- **最后更新**: 2026-08-05T23:07:20Z

## 提交统计

- **昨日提交总数**: 41
- **提交者数量**: 31
- **主要提交者**: Jialin Ouyang, Seraphim Volochaev, Xinyuan Tong

## AI分析总结

# sglang 项目提交分析报告

## 一、主要更新类型

本次提交涵盖多种类型：**性能优化**（约40%）、**Bug修复**（约25%）、**CI/测试改进**（约20%）、**新功能支持**（约10%）、**代码重构**（约5%）。整体以提升推理效率和系统稳定性为核心。

## 二、关键变更点与项目方向

1. **硬件适配扩展**：多提交针对Intel XPU、NPU、AMD MI35X等平台优化，包括DeepSeek V4的XPU内核实现、NPU causal conv1d和layernorm加速，体现项目多硬件生态布局战略。

2. **内核与算子优化**：统一MLA scaling初始化、DeepGEMM布局选择优化、fused TopK支持、FlashMLA改用sm_100f架构，持续深化底层计算效率。

3. **调度与内存管理**：修复CUDA Graph注意力填充位置、对齐WAR fences、统一编译内核缓存目录、优化draft KV池页粒度，强化系统级资源管理。

4. **CI/CD体系优化**：大量提交精简测试矩阵、跳过冗余安装、合并测试套件，提升开发效率与交付质量。

## 三、项目影响与意义

- **性能提升显著**：Wan VAE融合使H200端到端从9.611s降至9.125s，diffusion模型Ulysses通信合并减少集体调用次数，直接改善用户体验。
- **架构清晰化**：拆分多模态调度逻辑、完善树形Radix Cache接口边界，为后续扩展奠定基础。
- **部署便捷性**：新增srt_empty安装组、优化Dockerfile分支引用，降低用户接入门槛。

## 四、值得关注的技术点

1. **DeepGEMM内存预算感知布局选择**：根据显存预算动态选择标准布局，平衡性能与资源占用。
2. **SageAttention packed varlen路径**：为minimax-h3提供高效注意力实现，拓展diffusion模型支持。
3. **HiCache可观测性增强**：提升缓存系统监控能力，便于生产环境诊断。
4. **服务时Triton工作风险警告**：提前暴露潜在性能风险，增强系统健壮性。
5. **NVFP4 4over6量化设置固定**：稳定量化推理行为，保证结果可复现性。

## 五、对项目发展的影响

结合README中sglang作为高性能LLM推理框架的定位，这些提交呈现三大趋势：**一是深度硬件适配**，从NVIDIA扩展到Intel、AMD、NPU等多元算力，扩大用户基础；**二是极致性能追求**，通过内核融合、布局优化、通信压缩等手段持续压低延迟；**三是工程成熟度提升**，CI精简、缓存统一、安装简化等举措表明项目正从快速迭代期转向稳定期，为大规模生产部署做准备。特别是DeepSeek V4系列优化和GLM-5.2 MTP支持，显示项目正紧跟前沿模型架构演进，保持技术领先性。整体而言，本次提交体现了sglang在性能、兼容性和工程化三线并进的健康发展态势。

## 详细提交记录

### [070fde7](https://github.com/sgl-project/sglang/commit/070fde72bf3b77d34bc6b46019c3f1e10122f44c)

- **作者**: Baizhou Zhang
- **时间**: 2026-08-05T23:07:14Z
- **提交信息**: [CI] Remove some unneeded CP tests (#33763)

### [a1cc286](https://github.com/sgl-project/sglang/commit/a1cc2860626c879cd5d093d9297d9e48e33bdf8c)

- **作者**: Polisetty V R K Jyothendra Varma
- **时间**: 2026-08-05T23:04:35Z
- **提交信息**: [Intel GPU] DeepSeek V4 4/N: use sgl-kernel implementation of fused_q_norm_rope on XPU (#27790)

Signed-off-by: P V R K Jyothendra Varma <polisettyvarma@gmail.com>

### [c0ef548](https://github.com/sgl-project/sglang/commit/c0ef548eefe5da67b880ed16220436f89d4ba48a)

- **作者**: Liangsheng Yin
- **时间**: 2026-08-05T22:59:33Z
- **提交信息**: [misc] Unify MLA `scaling` init and remove dead buffer / scaling code (#33363)

### [990a446](https://github.com/sgl-project/sglang/commit/990a44677319c7b237d531a720fdb406d9039559)

- **作者**: YAMY
- **时间**: 2026-08-05T22:53:28Z
- **提交信息**: Fix padded positions in breakable CUDA Graph attention (#33253)

TestBreakableCUDAGraphBasic and all NVIDIA CI tests pass.

### [7bc90ab](https://github.com/sgl-project/sglang/commit/7bc90ab394449f2fcb385c62e8f9dd6ace335948)

- **作者**: YAMY
- **时间**: 2026-08-05T22:50:43Z
- **提交信息**: Select DeepGEMM standard layouts by memory budget (#33474)

Co-authored-by: Chunan Zeng <zcnrex@gmail.com>

### [25035bf](https://github.com/sgl-project/sglang/commit/25035bff8d34f3fcce2c1a2a5b1fe610225e84ed)

- **作者**: Baizhou Zhang
- **时间**: 2026-08-05T22:33:14Z
- **提交信息**: Use main branch in Kimi Dockerfiles (#33760)

### [02cd44c](https://github.com/sgl-project/sglang/commit/02cd44c59a69f4176978698c5e907f808af288a0)

- **作者**: yvbbrjdr
- **时间**: 2026-08-05T22:06:59Z
- **提交信息**: feat(dgx-spark): add inkling-small MoE support for sm_121 (#33108)

Co-authored-by: hnyls2002 <lsyincs@gmail.com>

### [b9d572e](https://github.com/sgl-project/sglang/commit/b9d572ee0245f222ddcde362ea6ab4fc2149f180)

- **作者**: Yanbin Jiang
- **时间**: 2026-08-05T22:06:28Z
- **提交信息**: [test] Re-enable a pruned Inkling LoRA unit-test set (68 -> 9 cases) (#33752)

### [2d27133](https://github.com/sgl-project/sglang/commit/2d27133fcfcd44b70d2c4cb7a7ab4ed65e7d4d7d)

- **作者**: Liangsheng Yin
- **时间**: 2026-08-05T22:06:01Z
- **提交信息**: [CI] Skip `apt-get` when the required packages are already installed (#33757)

### [a3a1ebc](https://github.com/sgl-project/sglang/commit/a3a1ebc7b7ee7ab185213b1a58ad6e482b7e15b1)

- **作者**: cctry
- **时间**: 2026-08-05T21:55:03Z
- **提交信息**: Warn on risky serving-time Triton work (#33120)

### [988c6e6](https://github.com/sgl-project/sglang/commit/988c6e6aeb5664e6e5a117e19d821318f07149c4)

- **作者**: Ziang Li
- **时间**: 2026-08-05T21:29:32Z
- **提交信息**: Pin online NVFP4 4over6 quantization settings (#33621)

### [a14c870](https://github.com/sgl-project/sglang/commit/a14c870886bc273706c25fe9cc06b2cbd9a80c20)

- **作者**: Brayden Zhong
- **时间**: 2026-08-05T21:27:05Z
- **提交信息**: Fix broken Nemotron DP attention (#33123)

Co-authored-by: Brayden Zhong <brayden@radixark.ai>

### [9436de7](https://github.com/sgl-project/sglang/commit/9436de717fca7f1c246acfcf0167e4e9cd7625b7)

- **作者**: Hank Han
- **时间**: 2026-08-05T21:17:42Z
- **提交信息**: [Spec][PD] Enable fused TopK for GLM-5.2 MTP IndexShare (#31477)

### [106bcc1](https://github.com/sgl-project/sglang/commit/106bcc12935569d32a3f2a241f4f17cf76fe8a30)

- **作者**: Zhiqiang Xie
- **时间**: 2026-08-05T21:13:06Z
- **提交信息**: Observability enhancement for HiCache (#32388)

### [55b1c09](https://github.com/sgl-project/sglang/commit/55b1c09e730785abbec49901048b9177feca3d5d)

- **作者**: Shu Wang
- **时间**: 2026-08-05T20:54:27Z
- **提交信息**: [core] Consolidate compiled-kernel caches under SGLANG_CACHE_DIR (#32434)

### [717a559](https://github.com/sgl-project/sglang/commit/717a559f02b3ad85ba4bb4623772a1672e9e3e9c)

- **作者**: Jialin Ouyang
- **时间**: 2026-08-05T20:52:20Z
- **提交信息**: [Scheduler] Align WAR fences with CUDA graph metadata reads (#33587)

### [ea65f8d](https://github.com/sgl-project/sglang/commit/ea65f8ddc905bde2a7a44e00e4eba2a1997f9b9f)

- **作者**: Leon Hibnik
- **时间**: 2026-08-05T20:23:17Z
- **提交信息**: Feat/spectrum (#31491)

Co-authored-by: jaron1990 <jaron1990@gmail.com>
Co-authored-by: jaron1990 <34618972+jaron1990@users.noreply.github.com>
Co-authored-by: Copilot Autofix powered by AI <175728472+Copilot@users.noreply.github.com>
Co-authored-by: copilot-swe-agent[bot] <198982749+Copilot@users.noreply.github.com>
Co-authored-by: alexnails <alex.nails@radixark.ai>

### [5c4f72f](https://github.com/sgl-project/sglang/commit/5c4f72f92a9089a6393dd6c5474b847b6be50489)

- **作者**: John
- **时间**: 2026-08-05T20:17:46Z
- **提交信息**: [Build] Add srt_empty extra group for device-agnostic install (#31300)

Co-authored-by: yixiaodapeng <yixiaodapeng@example.com>
Co-authored-by: Alex Nails <alex.nails@radixark.ai>

### [de34dd1](https://github.com/sgl-project/sglang/commit/de34dd11e9793379d1229813595be77b8d488608)

- **作者**: Liangsheng Yin
- **时间**: 2026-08-05T19:41:51Z
- **提交信息**: [CI] Fold duplicate-server suites and prune the retract matrix on 1-gpu-5090 (#33745)

### [36853b8](https://github.com/sgl-project/sglang/commit/36853b8ffc78e03501f9a1d9b9f0b5f04cb8797b)

- **作者**: Jason Mancuso
- **时间**: 2026-08-05T19:37:12Z
- **提交信息**: [Spec] Support logprobs with DFlash (#33459)

### [1a04566](https://github.com/sgl-project/sglang/commit/1a045669e497c72868b64eba29a36af463686b6f)

- **作者**: Liangsheng Yin
- **时间**: 2026-08-05T18:55:11Z
- **提交信息**: [CI] Merge tokenizer worker tests and drop redundant triton attention e2e (#33641)

### [5f79cf3](https://github.com/sgl-project/sglang/commit/5f79cf35110d6a0be828f266160b75d83a2a6276)

- **作者**: Khoa Pham
- **时间**: 2026-08-05T18:40:28Z
- **提交信息**: [DCP] Match the replicated draft KV pool's page granularity to its allocator (#33348)

### [b1bd871](https://github.com/sgl-project/sglang/commit/b1bd871df5217cb8e3b6d4ddf97c8a81da2e4ffb)

- **作者**: Jialin Ouyang
- **时间**: 2026-08-05T18:39:28Z
- **提交信息**: [Unified Radix Cache] Complete the tree-core interface boundary (#33580)

### [96c8986](https://github.com/sgl-project/sglang/commit/96c89863a34276bf622fe5bc568f77e794a78684)

- **作者**: cctry
- **时间**: 2026-08-05T18:26:27Z
- **提交信息**: Measure prefill busy time between launches (#33595)

### [acaab22](https://github.com/sgl-project/sglang/commit/acaab22d098594579dc3d2e04ea78474b0a60d7f)

- **作者**: WenhaoZhang
- **时间**: 2026-08-05T17:19:58Z
- **提交信息**: [diffusion] feat: add SageAttention packed varlen path for minimax-h3 (#33703)

### [b3cdd01](https://github.com/sgl-project/sglang/commit/b3cdd016baebc6b61787ffc196115986460ba981)

- **作者**: Xinyuan Tong
- **时间**: 2026-08-05T14:53:34Z
- **提交信息**: Add Ling-3.0-flash cookbook (#33556)

Co-authored-by: Zijie Xia <zijie.xia@radixark.ai>

### [4e7209c](https://github.com/sgl-project/sglang/commit/4e7209caa81694f679855720cd9433632a1ee26a)

- **作者**: zhaozx-cn
- **时间**: 2026-08-05T14:22:49Z
- **提交信息**: [NPU] Add causal conv1d (#28267)

### [3425c93](https://github.com/sgl-project/sglang/commit/3425c93666c39ac6979b2223bca96586a601b377)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-08-05T13:33:35Z
- **提交信息**: [diffusion] Wan VAE RMSNorm+SiLU fusion behind quality=high (H200 FastWan2.2 e2e 9.611 -> 9.125 s) (#33546)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [593777c](https://github.com/sgl-project/sglang/commit/593777c0465890fb466d0008a2d0417e48fcea61)

- **作者**: silencejade
- **时间**: 2026-08-05T13:27:43Z
- **提交信息**: [FIX] [benchmark] Fix flush_cache failure after warmup by waiting for server idle (#33527)

### [3b4fac5](https://github.com/sgl-project/sglang/commit/3b4fac5b99670f3e8bcb5bc9ecf04b821e7b8de5)

- **作者**: Xuan Liao
- **时间**: 2026-08-05T13:05:53Z
- **提交信息**: [XPU] DeepSeek V4: use sgl-kernel-xpu implemetation of flash_mla_sparse_fwd for prefill (#31865)

Co-authored-by: Ma Mingfei <mingfei.ma@intel.com>

### [99709f7](https://github.com/sgl-project/sglang/commit/99709f734d8362282d4cec44d3b62465a87c9678)

- **作者**: Mick
- **时间**: 2026-08-05T12:24:12Z
- **提交信息**: [VLM] split multimodal scheduling from mm_utils (#32415)

### [a5888c9](https://github.com/sgl-project/sglang/commit/a5888c956f9051f29ea05e1ed6896c004f8d4950)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-08-05T11:15:46Z
- **提交信息**: [diffusion] Pack Ulysses Q/K/V input all-to-all into one collective + reusable a2a staging buffers (#33667)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [2f22ed5](https://github.com/sgl-project/sglang/commit/2f22ed58ea907802abbaf6145a9236f6c86f9e7f)

- **作者**: Seraphim Volochaev
- **时间**: 2026-08-05T11:06:00Z
- **提交信息**: [NPU] Adding a fast layernorm for diffusion models and fix BSA (#29027)

Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>
Co-authored-by: ronnie_zheng <zl19940307@163.com>

### [22d558b](https://github.com/sgl-project/sglang/commit/22d558b10379cc9edd0a01780e988ad040143c84)

- **作者**: Yuefeng Wu
- **时间**: 2026-08-05T10:59:49Z
- **提交信息**: [Feature] Add GLM Image usage report (#33378)

Co-authored-by: wuyuefeng <wuyuefeng@noreply.gitcode.com>
Co-authored-by: ronnie_zheng <zl19940307@163.com>

### [8279702](https://github.com/sgl-project/sglang/commit/8279702e0b8f159c29ed201d05503a0548fefef9)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-08-05T09:53:23Z
- **提交信息**: [AMD] Stop publishing the K3 MI35X nightly image (#33689)

Co-authored-by: Chen <bingxche@amd.com>

### [6fa3f9d](https://github.com/sgl-project/sglang/commit/6fa3f9df11c8bdbc0e3b4ddc87a3d873343aca72)

- **作者**: Alex Nails
- **时间**: 2026-08-05T08:54:46Z
- **提交信息**: [Bugfix] Treat unsharded model.safetensors as HF weights in Mistral-native format detection (#33671)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [4a3d6ca](https://github.com/sgl-project/sglang/commit/4a3d6ca88c9e2d676a89a10564bab87acd1fd2ed)

- **作者**: Liangsheng Yin
- **时间**: 2026-08-05T08:46:16Z
- **提交信息**: [CI] Skip sglang-kernel and sgl-deep-gemm reinstall on version match (#33637)

### [a6e5fa7](https://github.com/sgl-project/sglang/commit/a6e5fa7081c7df5ac984d3a936420f7a73385497)

- **作者**: paulzhang-tm
- **时间**: 2026-08-05T08:44:18Z
- **提交信息**: [Scheduler] Honor explicit min-free-slots thresholds (#33403)

Co-authored-by: hnyls2002 <lsyincs@gmail.com>
Co-authored-by: Liangsheng Yin <hnyls2002@gmail.com>

### [c0d5ebd](https://github.com/sgl-project/sglang/commit/c0d5ebd6c4e0cf34525b69fd5ba784417104ad71)

- **作者**: Liangsheng Yin
- **时间**: 2026-08-05T08:43:29Z
- **提交信息**: [CI] Move CPU-only unit tests to the CPU suite and trim dead 5090 registrations (#33654)

### [98ed555](https://github.com/sgl-project/sglang/commit/98ed5554bbc45e82bb11a3796da548194cea3e84)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-08-05T08:38:28Z
- **提交信息**: Stop testing cu129 DeepGEMM wheels (#33675)

### [81c7a54](https://github.com/sgl-project/sglang/commit/81c7a54ecda118d30f350a99578c357c2df2ebfd)

- **作者**: Trevor Morris
- **时间**: 2026-08-05T08:36:46Z
- **提交信息**: [NVIDIA] Use sm_100f instead of sm_100a for sgl-kernel and FlashMLA (#33433)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-08-06
**监控日期**: 2026-08-05
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1242
- **最后更新**: 2026-08-03T09:04:55Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-08-06
**监控日期**: 2026-08-05
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 88278
- **最后更新**: 2026-08-05T23:05:22Z

## 提交统计

- **昨日提交总数**: 34
- **提交者数量**: 27
- **主要提交者**: Ziming Huang, fxmarty-amd, Schatten

## AI分析总结

## 提交分析总结

### 1. 主要更新类型

- **Bug修复**（约10项）：涵盖FP8权重维度、MLA激活dtype、KDA NaN、CPU offload空间检查、CI验证错误等
- **性能优化**（约6项）：SP多all gather合并、ARC批驱逐优化、FA4 mm_prefix范围查找、KV offload前缀复用等
- **重构与架构改进**（约5项）：PCPManager可扩展性、MoE legacy代码移除、Rust前端去重、模型加载revision解析优化
- **CI/测试改进**（约6项）：新增AITER测试、修复CI授权通知、精简PyTorch Fullgraph测试、ROCm测试容差调整
- **新功能支持**（约4项）：Ling 3.0 Flash模型支持、Mooncake store group语义、KV offload外部管理器支持

### 2. 关键变更点与项目方向

- **MoE架构演进**：移除legacy代码、共享apply_moe_activation元数据，表明MoE实现正走向统一和模块化
- **KV Offload深化**：支持外部二级存储管理器、细粒度前缀匹配、优化ARC驱逐，强化长上下文场景能力
- **ROCm生态强化**：多项ROCm相关修复和测试增强，体现AMD平台作为一等公民的战略
- **K3内核性能**：SP通信优化和KDA修复，聚焦新一代模型架构的推理效率

### 3. 项目影响与潜在意义

- **稳定性提升**：大量CI修复和验证错误处理，减少社区贡献者的接入摩擦
- **多硬件支持**：XPU、ROCm、CUDA三线并进，扩大部署覆盖面
- **架构清晰化**：PCPManager和MoE重构降低后续扩展成本，吸引更多外部贡献
- **推理成本优化**：内核级性能改进直接降低服务商运营成本

### 4. 值得关注的技术点

- **K3 SP多all gather合并**：1.5~3x内核级性能提升，对大规模张量并行有显著收益
- **FA4 mm_prefix范围查找优化**：针对FP4量化推理的查找效率改进
- **HuggingFace resolve_revision**：模型加载时一次性解析commit hash，减少重复网络请求
- **Rust前端去重**：`/tokenize`请求预处理复用，体现Rust前端架构的持续演进

### 5. 对项目发展的影响

vLLM正从“快速推理框架”向“生产级多硬件服务平台”演进。本批提交显示三个核心方向：**性能极致化**（内核级优化）、**生态扩展**（ROCm/XPU/多存储后端）、**架构现代化**（MoE重构、Rust前端）。大量CI和Bugfix投入表明项目处于快速迭代期，社区活跃度高，正在为大规模生产部署夯实稳定性基础。KV Offload和Mooncake集成则指向分布式推理和异构存储的未来架构。

## 详细提交记录

### [811622c](https://github.com/vllm-project/vllm/commit/811622c410c2f1baf2fa7056ca19753264b95815)

- **作者**: Qiu
- **时间**: 2026-08-05T23:05:14Z
- **提交信息**: [Refactor][PCP] Make PCPManager construction extensible (#50066)

Signed-off-by: QiuChunshuo <qiuchunshuo@huawei.com>
Co-authored-by: Lucas Wilkinson <LucasWilkinson@users.noreply.github.com>

### [b30291c](https://github.com/vllm-project/vllm/commit/b30291cf0c9a15898589f0347906bad07f3b538b)

- **作者**: Tianyu Guo
- **时间**: 2026-08-05T22:59:54Z
- **提交信息**: [EPD] Remove duplicate image preprocessing in EPD and enable preprocess on GPU (#50390)

Signed-off-by: Tianyu Guo <guoty@inferact.ai>

### [38ebd97](https://github.com/vllm-project/vllm/commit/38ebd97bcab958cbca63eeca87eb1fb57116b772)

- **作者**: Rohan Potdar
- **时间**: 2026-08-05T22:50:52Z
- **提交信息**: [ROCm] Relax MLA rope+cache test tolerances for bf16 (#51083)

Signed-off-by: Rohan138 <rohanpotdar138@gmail.com>
Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [8779758](https://github.com/vllm-project/vllm/commit/877975897d68f5e837e25d2f8ba80f5355adbe5b)

- **作者**: Wentao Ye
- **时间**: 2026-08-05T21:42:41Z
- **提交信息**: [K3 Perf] Combine multiple all gather together for SP, 1.5~3x kernel level performance improvement (#51070)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [373fe8b](https://github.com/vllm-project/vllm/commit/373fe8b83ee772d27b1a5b2b908618a1a414bb11)

- **作者**: bnellnm
- **时间**: 2026-08-05T21:35:36Z
- **提交信息**: [MoE Refactor] Remove MoE legacy code (#51078)

Signed-off-by: Bill Nell <bnell@redhat.com>

### [4282fe5](https://github.com/vllm-project/vllm/commit/4282fe52d5353084a5773e924a508e9346dc2718)

- **作者**: Micah Williamson
- **时间**: 2026-08-05T21:27:33Z
- **提交信息**: [ROCm][CI] Add More AITER quantization/MoE kernel tests (#49375)

Signed-off-by: Micah Williamson <micah.williamson@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [482c613](https://github.com/vllm-project/vllm/commit/482c6134236d96ebab3c749cd02d245516adad1d)

- **作者**: Netanel Haber
- **时间**: 2026-08-05T21:08:55Z
- **提交信息**: [Bugfix][Humming] Preserve ModelOpt FP8 weight dimensions (#51093)

Signed-off-by: Netanel Haber <58652339+netanel-haber@users.noreply.github.com>

### [e76b71f](https://github.com/vllm-project/vllm/commit/e76b71f659859f1793ab730e798eb4b4236bce1f)

- **作者**: Wentao Ye
- **时间**: 2026-08-05T20:57:47Z
- **提交信息**: [CI Bug] Fix `pydantic_core._pydantic_core.ValidationError: Input should be a valid integer` (#51179)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [65addac](https://github.com/vllm-project/vllm/commit/65addac701c0f019152cc00ffedb6edec442a3e2)

- **作者**: stefankoncarevic
- **时间**: 2026-08-05T20:28:41Z
- **提交信息**: [ROCm][CI] Keep rocprofiler-sdk out of DeepEP HT MoE test workers (#51173)

Signed-off-by: Stefan Koncarevic <Stefan.Koncarevic@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [c2d8009](https://github.com/vllm-project/vllm/commit/c2d8009044abb174576dab6439dda56d66c83847)

- **作者**: Rohan Potdar
- **时间**: 2026-08-05T19:44:42Z
- **提交信息**: [ROCm] Work around DeepEP teardown SIGSEGV in MoE test harness (#51174)

Signed-off-by: Rohan138 <rohanpotdar138@gmail.com>
Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [e6d67fd](https://github.com/vllm-project/vllm/commit/e6d67fddb4b27d4772ae714348a22af7fe7e35e5)

- **作者**: Michael Goin
- **时间**: 2026-08-05T19:27:27Z
- **提交信息**: [CI] Prune PyTorch Fullgraph Test (#51074)

Signed-off-by: mgoin <mgoin64@gmail.com>

### [8f158d0](https://github.com/vllm-project/vllm/commit/8f158d0ee2475c64f66ee9ebd55a3606209db92f)

- **作者**: Michael Goin
- **时间**: 2026-08-05T19:05:47Z
- **提交信息**: [MoE] Share apply_moe_activation support metadata (#44359)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [14e57ad](https://github.com/vllm-project/vllm/commit/14e57ad47dec65059f4f04700439a8465ea83a87)

- **作者**: Zhewen Li
- **时间**: 2026-08-05T18:58:44Z
- **提交信息**: [Docker][KVConnector] Install mooncake from official wheels instead of a custom build (#51067)

Signed-off-by: Zhewen Li <zhewenli@inferact.ai>
Co-authored-by: Zhewen Li <zhewenli@inferact.ai>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [613411a](https://github.com/vllm-project/vllm/commit/613411a90ccfd884383aab84875ce95fe2871a3c)

- **作者**: Wentao Ye
- **时间**: 2026-08-05T18:33:45Z
- **提交信息**: [CI Bug] Fix `Chunked prefill is required for mamba cache mode 'align'.` (#51177)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [bc37fc9](https://github.com/vllm-project/vllm/commit/bc37fc970eb04a0e393e5517d39700acaad8aee3)

- **作者**: fxmarty-amd
- **时间**: 2026-08-05T18:04:40Z
- **提交信息**: Revert [Misc] Avoid importing `nixl_ep` on every `vllm serve` config (#50879) (#51176)

Signed-off-by: Felix Marty <Felix.Marty@amd.com>

### [23c0f33](https://github.com/vllm-project/vllm/commit/23c0f337b7c25508fce2b98cbf655bdc8cf166b4)

- **作者**: Wentao Ye
- **时间**: 2026-08-05T18:03:17Z
- **提交信息**: [CI bug] Fix `Each KV cache group's real block_size must be divisible by has h_block_size` (#51180)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [9833aa5](https://github.com/vllm-project/vllm/commit/9833aa53d5a9559b4cc8d174ae49d6e282c30423)

- **作者**: AlexHuang
- **时间**: 2026-08-05T17:59:55Z
- **提交信息**: [Bugfix] Fail fast with a clear error when CPU offload region exceeds available space (#50358)

Signed-off-by: Alex <jihui.huang@daocloud.io>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: Or Ozeri <oro@il.ibm.com>

### [e8586b2](https://github.com/vllm-project/vllm/commit/e8586b28788ee9ef2286bca9d6e98724041f185b)

- **作者**: Michael Goin
- **时间**: 2026-08-05T17:50:58Z
- **提交信息**: [Build] Remove Ubuntu build-stage option from the CUDA dockerfile (#51060)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Shengqi Chen <harry-chen@outlook.com>

### [8543522](https://github.com/vllm-project/vllm/commit/8543522ca792de824c026e1b9e3eb51ca809550d)

- **作者**: Ronen Schaffer
- **时间**: 2026-08-05T17:30:53Z
- **提交信息**: [KV Offload] Support out-of-tree secondary tier managers via `module_path` (#51007)

Signed-off-by: Ronen Schaffer <ronen.schaffer@ibm.com>
Co-authored-by: Or Ozeri <oro@il.ibm.com>

### [d4da0c5](https://github.com/vllm-project/vllm/commit/d4da0c55af3aa231b6209bf77871f3ed36eab0d2)

- **作者**: zexplorerhj
- **时间**: 2026-08-05T16:38:28Z
- **提交信息**: [Model][Frontend] Add Ling 3.0 Flash BF16, MTP, and parser support (#51045)

Signed-off-by: zexplorerhj <zhjoneson@163.com>

### [66b3c0e](https://github.com/vllm-project/vllm/commit/66b3c0e61f1e477820212201adf1ed871df7ee98)

- **作者**: Li Juqi
- **时间**: 2026-08-05T14:33:49Z
- **提交信息**: [Kernel][Model] Optimize FA4 mm_prefix range lookup (#50294)

Signed-off-by: Juqi Li <2223621784@qq.com>
Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [62c5e21](https://github.com/vllm-project/vllm/commit/62c5e2162186a369d9fba40b8795d06b9144e8fe)

- **作者**: Chauncey
- **时间**: 2026-08-05T14:31:50Z
- **提交信息**: [KV Offloading] Support partial-tail prefix reuse with fine-grained prefix matching (#50507)

Signed-off-by: chaunceyjiang <chaunceyjiang@gmail.com>
Co-authored-by: Or Ozeri <oro@il.ibm.com>

### [08b8613](https://github.com/vllm-project/vllm/commit/08b8613b7b15643e9675595997968b307724596b)

- **作者**: Gabriel Wu
- **时间**: 2026-08-05T14:25:46Z
- **提交信息**: [Bugfix][Model] Fix MiniMax-M3 NVFP4 inference correctness (#48929)

Signed-off-by: Zihua Wu <13583761+lucifer1004@users.noreply.github.com>
Co-authored-by: Pavani Majety <pmajety@nvidia.com>

### [cd930c8](https://github.com/vllm-project/vllm/commit/cd930c8e786bcfb84397e0aa424d789ebec58433)

- **作者**: Jacob Zhang
- **时间**: 2026-08-05T14:25:41Z
- **提交信息**: [Bugfix] Fix MLA kv_b_proj activation dtype with Marlin FP8 (#38771)

Signed-off-by: Jacob Zhang <jaco8123@gmail.com>
Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [397094d](https://github.com/vllm-project/vllm/commit/397094da1768c7a6f29dfa4f70079d793ac747df)

- **作者**: Lucain
- **时间**: 2026-08-05T13:49:56Z
- **提交信息**: Resolve revision to commit_hash once per model load, via huggingface_hub's `resolve_revision` (#49990)

Signed-off-by: Wauplin <lucainp@gmail.com>
Signed-off-by: Lucain <lucainp@gmail.com>
Signed-off-by: Lucain Pouget <lucain@huggingface.co>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [a9b39d6](https://github.com/vllm-project/vllm/commit/a9b39d6dcbe9970a33b5d1ceb9848ba975167b1b)

- **作者**: music-dino
- **时间**: 2026-08-05T13:21:43Z
- **提交信息**: [Bugfix] Enable chunked prefill for qwen3.5-0.8B ppl test (#51153)

Signed-off-by: Dino Music <Dino.Music@amd.com>

### [beca88e](https://github.com/vllm-project/vllm/commit/beca88e59ea75a7aa1af72a5ae50188fa91d4e3d)

- **作者**: Ziming Huang
- **时间**: 2026-08-05T09:22:55Z
- **提交信息**: [BugFix][K3] Skip moe_intermediate padding when EP is enabled (#51131)

### [a3b8675](https://github.com/vllm-project/vllm/commit/a3b86752fbcd2fb1a9adfe44634ac0d955228e2a)

- **作者**: Kevin H. Luu
- **时间**: 2026-08-05T08:34:48Z
- **提交信息**: [CI] Fix CI authorization notification fallback (#51095)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [5bf3260](https://github.com/vllm-project/vllm/commit/5bf32605a950ee50ed05f230243d54e0baf7d12d)

- **作者**: Sage
- **时间**: 2026-08-05T08:27:35Z
- **提交信息**: [Rust Frontend] Deduplicate request preprocessing for `/tokenize` (#50448)

Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Signed-off-by: Sage Ahrac <sagiahrak@gmail.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>

### [fd859d2](https://github.com/vllm-project/vllm/commit/fd859d2e0689ce254bfb0e67483fba76405ca9df)

- **作者**: Schatten
- **时间**: 2026-08-05T08:25:38Z
- **提交信息**: [KV Connector][Mooncake] Add store group semantics (#44956)

Signed-off-by: Schatten <czhengt@qq.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: Yifan Qiao <yifanqiao@inferact.ai>

### [f5cd862](https://github.com/vllm-project/vllm/commit/f5cd862dbdafb9d9870945a4f61454f90d87e2ae)

- **作者**: kliuae
- **时间**: 2026-08-05T08:07:21Z
- **提交信息**: [ROCm][Bugfix] Kimi-K3 Fix KDA NaN on mixed batches and racy autotune config (#50649)

Signed-off-by: kliuae <kuanfu.liu@embeddedllm.com>

### [b92352c](https://github.com/vllm-project/vllm/commit/b92352ca2c5625a8ca61da597046d50a121c54ad)

- **作者**: MINJUN GIL
- **时间**: 2026-08-05T07:58:36Z
- **提交信息**: [Perf][KV Offload] Avoid quadratic ARC batch eviction (#50992)

Signed-off-by: MINJUN GIL <alswnsrlf12@naver.com>

### [96e333e](https://github.com/vllm-project/vllm/commit/96e333e81ad3203fc3980426daa136c213339b46)

- **作者**: Kevin H. Luu
- **时间**: 2026-08-05T07:14:27Z
- **提交信息**: [CI] Run control-plane workflows on vLLM runners (#51127)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [999dd8b](https://github.com/vllm-project/vllm/commit/999dd8b49031a7bc0f98a0fe88a1ddc2ead6a754)

- **作者**: Sundaresan G
- **时间**: 2026-08-05T07:10:17Z
- **提交信息**: [XPU] Alias is_current_stream_capturing to XPU in cuda wrapper (#50526)

Signed-off-by: Sundaresan-G <sundaresan.g@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-08-06
**监控日期**: 2026-08-05
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 5880
- **最后更新**: 2026-08-05T21:57:28Z

## 提交统计

- **昨日提交总数**: 9
- **提交者数量**: 9
- **主要提交者**: Nick Cao, zhengjia, ooooooye

## AI分析总结

## 提交分析总结

### 1. 主要更新类型
本次提交涵盖**文档更新**（3项）、**Bug修复**（3项）、**硬件适配**（2项）、**功能对齐**（1项）和**CI优化**（1项），整体以稳定性和兼容性提升为主。

### 2. 关键变更点与项目方向
- **多模态模型支持深化**：MiniMax H3相关提交（RNG设备感知、输入矩阵对齐）和MOSS-TTS编解码器修复，直接强化了项目“omni-modality”（全模态）的核心定位，确保不同模态模型在异构硬件上行为一致。
- **硬件生态扩展**：新增Cosmos3-Nano在AMD MI350X上的ROCm部署指南，以及MUSA（摩尔线程）后端的RNG设备适配，体现了项目“easy, fast, cheap”的跨平台承诺，降低特定硬件使用门槛。
- **Diffusion执行模式整合**：文档层面的模式梳理配合DLO AllGather大小不匹配的Bug修复，表明项目正在系统化完善扩散模型的分布式推理路径。

### 3. 项目影响与潜在意义
- **稳定性提升**：MOSS-TTS的tokenizer对齐上游和编解码器检测修复，直接改善语音模态输出的正确性；DLO AllGather修复则避免了大模型分布式推理中的隐性崩溃。
- **可维护性增强**：CODEOWNERS新增维护者、NPU CI按硬件标签分层性能基线，分别优化了社区协作效率和CI可观测性，为项目规模化发展奠定基础。
- **用户友好度提升**：ComfyUI集成提示和ROCm部署指南降低了社区用户的上手成本，符合“for everyone”的项目愿景。

### 4. 值得关注的技术点
- **RNG设备感知**（提交5）：将随机数生成器绑定到具体计算设备，解决了多设备环境下VAE采样结果不一致的问题，是推理可复现性的关键细节。
- **输入矩阵对齐**（提交9）：与官方实现逐元素对齐输入格式，体现了对模型行为精确复刻的严谨态度，对保证第三方模型兼容性至关重要。
- **CI硬件标签化**（提交6）：按H100/A3等硬件标签分别建立性能基线，避免了跨硬件性能比较的误导，是MLOps领域的良好实践。

### 5. 对项目发展的整体影响
这批提交体现了vllm-omni在**广度**（新增硬件支持、模态覆盖）和**深度**（修复边缘案例、对齐官方行为）上的并行推进。文档与CI的完善表明项目正从“功能可用”迈向“生产可靠”阶段。MiniMax H3和MOSS-TTS的密集修复显示团队对热门多模态模型的响应速度，而ROCm/MUSA适配则巩固了其作为“硬件无关”统一推理层的战略定位。整体上，这些变更增强了项目的鲁棒性、可访问性和社区健康度，为吸引更广泛的用户和贡献者创造了条件。

## 详细提交记录

### [b4581b2](https://github.com/vllm-project/vllm-omni/commit/b4581b293beb837a2936b16c0cad6d2834fed9f6)

- **作者**: zhengjia
- **时间**: 2026-08-05T14:50:15Z
- **提交信息**: [Doc] Add Cosmos3-Nano ROCm recipe (1x MI350X) (#5634)

Signed-off-by: zjli2013 <leezhengjiang@126.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [9f97892](https://github.com/vllm-project/vllm-omni/commit/9f978923f2f537da6adac700f0d2330dc377ec33)

- **作者**: bjf-frz
- **时间**: 2026-08-05T14:41:18Z
- **提交信息**: [docs] consolidate diffusion execution modes (#5599)

Signed-off-by: bjf-frz <frz123db@gmail.com>

### [589afce](https://github.com/vllm-project/vllm-omni/commit/589afcef6c555c9b682fca1a3670a40fba507879)

- **作者**: Nick Cao
- **时间**: 2026-08-05T13:50:48Z
- **提交信息**: Add @NickCao to CODEOWNERS (#5807)

Signed-off-by: Nick Cao <ncao@redhat.com>

### [556c5f8](https://github.com/vllm-project/vllm-omni/commit/556c5f88a0f4b1d2e7285c6c69feecf0e3e39505)

- **作者**: Zeyu Huang | 黃澤宇
- **时间**: 2026-08-05T11:12:06Z
- **提交信息**: [skip ci][Doc] add comfyui hint for Minimal-H3 (#5785)

Signed-off-by: Huang, Zeyu <11222265+fhfuih@users.noreply.github.com>

### [2eada79](https://github.com/vllm-project/vllm-omni/commit/2eada79b99ae64acd835e5ca3794eb6ff60f4424)

- **作者**: R0CKSTAR
- **时间**: 2026-08-05T10:11:46Z
- **提交信息**: [Hardware][MUSA] Make MiniMax H3 conditioned VAE RNG device-aware (#5703)

Signed-off-by: Xiaodong Ye <xiaodong.ye@mthreads.com>

### [7fb62db](https://github.com/vllm-project/vllm-omni/commit/7fb62db5c226558162dbee5b204d8d57479d28a0)

- **作者**: wangyu
- **时间**: 2026-08-05T09:35:41Z
- **提交信息**: [CI]For NPU CI, Nest perf baselines by hardware label (H100/A3) (#5402)

Signed-off-by: wangyu <410167048@qq.com>

### [6510de3](https://github.com/vllm-project/vllm-omni/commit/6510de344ebff729e9e066bef1a23ff120ce422c)

- **作者**: ooooooye
- **时间**: 2026-08-05T09:32:41Z
- **提交信息**: [Bugfix][Diffusion] Fix DLO AllGather size mismatch for models with h… (#5802)

Signed-off-by: brandneway <gyuan4892@gmail.com>

### [740cb35](https://github.com/vllm-project/vllm-omni/commit/740cb35a595409fdd7c081ff9d4ebbaeb6520e39)

- **作者**: Wallbreazzz
- **时间**: 2026-08-05T08:24:32Z
- **提交信息**: [BugFix] Fix MOSS-TTS codec v1/v2 detection and align vendored tokenizer with upstream (#5635)

Signed-off-by: Wallbreazzz <110282866+Wallbreazzz@users.noreply.github.com>

### [ae7bee0](https://github.com/vllm-project/vllm-omni/commit/ae7bee0c43c780a8e21d0b5e4b92a7eaeaea8783)

- **作者**: WeiQing Chen
- **时间**: 2026-08-05T07:12:01Z
- **提交信息**: [Feature] Align MiniMax H3 official input matrix (#5752)

Signed-off-by: david6666666 <530634352@qq.com>

---
