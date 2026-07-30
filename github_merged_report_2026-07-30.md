# GitHub Stars 合并报告 - 2026-07-30

**合并日期**: 2026-07-31
**监控日期**: 2026-07-30
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


**报告日期**: 2026-07-31
**监控日期**: 2026-07-30
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2116
- **最后更新**: 2026-07-30T10:46:54Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-07-31
**监控日期**: 2026-07-30
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2545
- **最后更新**: 2026-07-30T09:27:36Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Bilang ZHANG

## AI分析总结

### 主要更新类型
- **重构/代码清理**：移除了旧的编译相关配置（`"compile": true`），属于内部清理和优化。

### 关键变更点及其与项目整体方向的关系
- **变更点**：删除了与旧编译模式（`compile: true`）有关的代码或配置。
- **与项目方向的关系**：LightX2V 定位为轻量视频生成推理框架，删除过时/冗余的编译选项有助于降低代码复杂度、减少维护成本，符合“轻量化”和“高效推理”的核心目标。

### 对项目的影响和潜在意义
- **影响**：消除对旧编译路径的依赖，可能简化模型加载或推理的默认行为；小幅减少包体积和构建时间。
- **潜在意义**：
  - 为后续引入新的编译策略（如动态编译、图优化）腾出空间。
  - 减少因新旧编译模式共存可能引发的兼容性隐患。

### 值得关注的技术点
- **编译选项的演进**：`compile=true` 可能关联 `torch.compile` 或自定义 JIT 编译，删除旧选项暗示团队已转向更稳定或更高效的编译方案。
- **向后兼容性**：需确认下游用户配置中是否仍依赖此选项，但 #1312 作为清理提交通常已考虑兼容性。

### 基于 README 背景，该提交如何影响项目发展
- 项目强调“轻量”和“高效”，删除旧编译代码是对该理念的贯彻——精简不必要的功能分支，聚焦核心推理能力。
- 此举可能为后续加速视频生成推理（如引入更细粒度的算子编译、量化编译）扫清障碍，推动项目向更专业、更易维护的方向演进。

## 详细提交记录

### [054fc61](https://github.com/ModelTC/LightX2V/commit/054fc61041b02e560bbf677b7cf99da4ae28774b)

- **作者**: Bilang ZHANG
- **时间**: 2026-07-30T09:27:19Z
- **提交信息**: delete: old compile ("compile": true) (#1312)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-07-31
**监控日期**: 2026-07-30
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2181
- **最后更新**: 2026-07-29T08:35:53Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-07-31
**监控日期**: 2026-07-30
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 6070
- **最后更新**: 2026-07-30T22:16:45Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Ziang Li, Xinyuan Tong

## AI分析总结

### 1. 主要更新类型
- **功能新增**：两笔提交均为新特性（feat），未包含 Bug 修复、性能优化或文档更新。

### 2. 关键变更点与项目整体方向的关系
- **独立页表行起始（第一笔）**：
  - 在 `top_k_page_table_transform` 中新增可选的 `page_table_row_starts` 参数，允许评分窗口与页表翻译窗口使用不同的起始偏移量。
  - 解决 SGLang 融合 PAGED DSA 路径中只能回退到 SGL 内核的问题，使 FlashInfer 的 fused top-k 能原生支持该场景。
  - 项目方向：增强 paged attention 场景下的灵活性，减少对外部内核的依赖，提升确定性和图安全性。

- **无 RoPE 尾部 MLA 解码（第二笔）**：
  - 为 `kv_lora_rank=512, qk_rope_head_dim=0` 的稀疏 MLA 解码提供原生支持，新增可选 `sparse_mla_top_k_lens` 张量传入活动长度。
  - 注册新的 `nope_mla_dimensions` 维度集，修改 launcher 以适配单缓存池动态稀疏 gather。
  - 项目方向：拓展 MLA 注意力机制的覆盖范围，尤其针对 DeepSeek 等无旋转尾部的变体，使其能被 TRTLLM-GEN 原生服务。

### 3. 对项目的影响与潜在意义
- **影响**：
  - 第一笔使 FlashInfer 的 fused top-k 可处理更复杂的分页窗口分离场景，提升在推理框架（如 SGLang）中的可用性。
  - 第二笔填补稀疏 MLA 解码的形态空白，减少用户因形状不支持而回退到其他内核的情况。
- **意义**：
  - 增加 API 的灵活性（向后

## 详细提交记录

### [b1055a7](https://github.com/flashinfer-ai/flashinfer/commit/b1055a7aaf47a4a70ba26acd1cece329f4a828d2)

- **作者**: Ziang Li
- **时间**: 2026-07-30T22:16:40Z
- **提交信息**: feat(topk): support separate page table row starts (#4169)

<!-- .github/pull_request_template.md -->

## 📌 Description

@humansand

SGLang needs `top_k_page_table_transform` to support independent
score-window and page-table starts in its fused packed PAGED DSA path:

- `row_starts` identifies the score window used for top-k selection.
- `page_table_row_starts` identifies the page-table window used to
translate the selected local indices.

The current FlashInfer API applies `row_starts` to both operations, so
it cannot represent this case. SGLang must therefore fall back to the
SGL kernel even when `--dsa-topk-backend flashinfer` is selected. That
produces correct indices, but it bypasses FlashInfer's deterministic,
tie-break, and graph-safe fused top-k behavior for this path.

This PR adds optional `page_table_row_starts` support. When it is
omitted, FlashInfer continues to use `row_starts` for both operations,
preserving the existing API behavior. The separate start is propagated
through the Python and trace APIs, TVM FFI binding, radix and filtered
implementations, deterministic post-sort, graph-safe dispatch, and the
trivial `length <= k` path.

Once SGLang adopts a FlashInfer release containing this API, it can
remove the packed PAGED fallback and use FlashInfer fused top-k with the
intended backend semantics. This PR does not change the SGLang call
site.

### API Design

For each output row `i`, define:

```text
batch_i       = row_to_batch[i]             if row_to_batch is provided, else i
score_start_i = row_starts[i]               if row_starts is provided, else 0
page_start_i  = page_table_row_starts[i]    if page_table_row_starts is provided,
                else score_start_i
length_i      = lengths[i]
```

Top-k selection produces local offsets `local_idx[i, j]` in `[0,
length_i)` by ranking:

```text
input[i, score_start_i + local_idx[i, j]]
```

The page-table transform uses the same local offsets but an independent
page-table origin:

```text
output[i, j] = src_page_table[batch_i, page_start_i + local_idx[i, j]]
```

**`page_table_row_starts` affects only the page-table lookup used to
produce output values.** It does not change the input score window, the
selected local offsets, or the output tensor shape; it only changes
which columns of `src_page_table` are gathered into the output.

The argument responsibilities are therefore orthogonal:

- `row_to_batch` selects only the row of `src_page_table`; multiple
score rows may map to the same page-table row.
- `row_starts` selects only the score-window origin.
- `page_table_row_starts` selects only the page-table-window origin. It
may be provided independently of `row_starts`; when omitted, it reuses
`row_starts` for backward compatibility.

If `length_i <= k`, all local offsets `0..length_i-1` are transformed
and the remaining output positions are `-1`. Otherwise, exactly `k`
local offsets are selected according to the existing deterministic and
tie-break semantics.

Each optional mapping/start tensor has shape `(num_rows,)`, dtype
`int32`, and resides on the same CUDA device as `input`. Callers must
satisfy `0 <= length_i`, `0 <= batch_i < src_page_table.shape[0]`, `0 <=
score_start_i`, `score_start_i + length_i <= input.shape[1]`, `0 <=
page_start_i`, and `page_start_i + length_i <= src_page_table.shape[1]`.

This selection-plus-gather contract is not specific to SGLang: it
represents any packed layout where score storage and lookup-table
storage use different origins. Absolute starts are used instead of
deltas so the API does not assume a relationship between the two windows
or expose framework-specific metadata such as `cu_seqlens`.

## 🔍 Related Issues

- SGLang DSA top-k backend integration:
https://github.com/sgl-project/sglang/pull/22851
- SGLang packed PAGED correctness fallback and backend-selection
cleanup: https://github.com/sgl-project/sglang/pull/32490

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

Validation on an NVIDIA B200 using the editable source build and source
JIT:

```text
pre-commit run --all-files
Passed

python3 -m pytest -vv -s tests/utils/test_topk.py -k 'test_top_k_transform_with_row_starts'
48 passed, 1334 deselected, 2 warnings in 0.61s
```

The test extends the existing `test_top_k_transform_with_row_starts`
Cartesian product across radix/filtered dispatch, graph-safe mode,
deterministic mode, shared/separate starts, and both trivial and
selected rows.

## Reviewer Notes

Review focus is welcome on propagation through the deterministic
post-sort and graph-safe filtered paths, where page-table translation
occurs separately from score selection.



<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added optional `page_table_row_starts` support to the fused Top‑K
page-table transform for independent per-row destination window offsets.
* Updated tracing and reference implementations to model separate
score-window (`row_starts`) and destination page-table-window
(`page_table_row_starts`) offsets.
* **Bug Fixes**
* Corrected page-table addressing when the score and destination windows
start at different offsets.
* **Tests**
* Expanded Top‑K transform coverage to include deterministic mode and
separate `page_table_row_starts`, with additional trace-based reference
checks.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [a02d94d](https://github.com/flashinfer-ai/flashinfer/commit/a02d94de5796650ead1c6be27b834c3a063bf45d)

- **作者**: Xinyuan Tong
- **时间**: 2026-07-30T16:46:12Z
- **提交信息**: feat: support native qk_rope_head_dim=0 sparse MLA decode in trtllm-gen (#4108)

## 📌 Description

Adds a native TRTLLM-GEN sparse MLA decode path for the shape with **no
rotary tail**: `kv_lora_rank=512`, `qk_rope_head_dim=0`.

For this shape the query carries no RoPE component, and both KV TMA
descriptors address a **single 512-wide cache pool**, so the kernel
needs the per-request active lengths to bound the sparse gather. Today
`trtllm_batch_decode_with_kv_cache_mla` only accepts
`deepseek_mla_dimensions` and `smaller_mla_dimensions`, so a
`qk_rope_head_dim=0` request is rejected as an unsupported MLA
dimension.

This PR registers the new dimension set and threads an optional
`sparse_mla_top_k_lens` tensor down to the launcher so the shape can be
served natively.

**Changes**

- **`csrc/trtllm_fmha_kernel_launcher.cu`** — add an optional
`sparse_mla_top_k_lens` argument to `trtllm_paged_attention_decode`.
When the single-pool dynamic sparse MLA shape is detected
(`sparse_mla_top_k_lens` present and MLA decode), pass the key cache as
the sliding-window KV pool so the kernel reads the active per-token
lengths. The launcher already rejects combining block-sparse attention
with sparse MLA (`sparse_mla_top_k <= 0` check), so the two stay
mutually exclusive.
- **`flashinfer/mla/_core.py`** — register `nope_mla_dimensions`
(`kv_lora_rank=512`, `qk_rope_head_dim=0`); require `sparse_mla_top_k >
0` and a `sparse_mla_top_k_lens` tensor for this shape; thread the
autotune profiling length through the decode tuning config so different
`top_k` values key distinct autotune configs; expose
`sparse_mla_top_k_lens` on the public
`trtllm_batch_decode_with_kv_cache_mla`.
- **`flashinfer/decode.py`** — forward the new optional argument at the
two existing kernel call sites.
- **`flashinfer/trace/templates/attention.py`** — declare the optional
`sparse_mla_top_k_lens` input on the sparse MLA decode trace template so
the trace schema matches the kernel signature.

The new argument is **optional and defaults to `None`**, so the
`deepseek_mla_dimensions` / `smaller_mla_dimensions` decode paths are
unchanged. `sparse_mla_top_k_lens` (one `int32` active length per query
token) is supplied by the caller.

## 🔍 Related Issues

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

- [ ] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

Static checks pass (`clang-format` / `ruff` / `mypy` via `pre-commit`).
The new path has been exercised end-to-end in a downstream serving stack
that computes `sparse_mla_top_k_lens` from the page table and drives
this decode path. Happy to add a focused in-tree unit test for the
`qk_rope_head_dim=0` dimension registration + argument threading — see
Reviewer Notes.

## Reviewer Notes

- **Backward compatibility**: `sparse_mla_top_k_lens` is optional and
defaults to `None`; all existing callers and the two established MLA
dimension sets keep their current behavior.
- **Mutual exclusion**: block-sparse attention and sparse MLA are
already mutually exclusive in the launcher (`sparse_mla_top_k <= 0`
check), so the new single-pool path cannot be entered together with
block-sparse.
- **Autotune keying**: the profiling length is threaded through the
decode tuning config and into the cache key, so a dense request
(`len(inputs)==4`) and a sparse request (`len(inputs)==5`) resolve to
distinct autotune configs rather than mis-keying.
- I can add a unit test covering the dimension registration and the
optional-argument threading if you'd like it in-tree — let me know the
preferred test shape.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
  * Added support for native no-RoPE MLA decoding.
* Added optional per-query sparse attention lengths for supported MLA
decode workloads.
* Added validation for sparse attention length tensor type, shape,
device, and contiguity.
* Integrated sparse MLA inputs with direct decoding and autotuning
paths.

* **Bug Fixes**
* Improved handling of supported MLA head configurations during decode
dispatch.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-07-31
**监控日期**: 2026-07-30
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3897
- **最后更新**: 2026-07-30T17:32:26Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-07-31
**监控日期**: 2026-07-30
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34196
- **最后更新**: 2026-07-30T20:52:08Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: David El Malih, Álvaro Somoza

## AI分析总结

### 总结分析

#### 1. 主要更新类型
- **文档更新**：提交 #14330 改进了 `scheduling` 文件夹中文档字符串的质量（最后一批）。
- **功能新增**：提交 #14277 引入了量化模块 `SDNQ` 的核心加载功能。

#### 2. 关键变更点及其与项目整体方向的关系
- **文档优化**：聚焦于调度器（scheduler）的 API 文档，提升可读性和易用性。这与 Diffusers 作为开源库强调“易用性”和“社区友好”的方向一致，有助于降低用户对复杂调度参数的理解门槛。
- **量化支持**：新增 `SDNQ` 量化加载，允许模型在推理时以更低的精度运行。这属于性能优化/模型压缩方向，直接命中 Diffusers 在部署场景（边缘设备、低显存环境）中的痛点，扩展了项目的实用性。

#### 3. 对项目的影响和潜在意义
- **文档更新**：提升了库的完整度和专业度，减少因文档缺失导致的用户疑问，间接降低维护成本。
- **量化功能**：使 Diffusers 能够支持新一代量化技术（SDNQ），可能为后续模型压缩（如蒸馏、剪枝）提供基础组件。对商业部署和资源受限场景有实际价值，增强项目竞争力。

#### 4. 值得关注的技术点
- **SDNQ 量化**：提交中涉及“transformers 注册、版本检查、环境标志、模块级测试”等实现细节，表明这是一个经过架构设计的模块，而非临时补丁。未来可能作为标准量化入口。
- **文档规范化**：提交者特意标注“last batch”，暗示此次是系列文档改进的收尾，说明团队有系统地梳理调度器文档的计划。

#### 5. 基于项目背景对项目发展的影响
- 基于 Diffusers 作为扩散模型生态核心库的定位，**文档更新**直接提升开发者体验，吸引更多用户贡献和二次开发。
- **量化支持**直接对应“从研究到生产”的转化需求，使 Diffusers 从实验性代码库向生产级推理框架演进。结合已有功能（如 ONNX、Dynamo），进一步完善了模型压缩与部署工具链。

## 详细提交记录

### [7685bff](https://github.com/huggingface/diffusers/commit/7685bffe89041496c2c0ae07ea933df1c80d1f43)

- **作者**: David El Malih
- **时间**: 2026-07-30T15:10:30Z
- **提交信息**: docs: improve docstring scheduling folder - last batch (#14330)

* Improve docstring scheduling - last batch

* docs: améliorer la documentation des arguments de SchedulerMixin

### [8b33b47](https://github.com/huggingface/diffusers/commit/8b33b473324423a9773d121c7caccb13601493a1)

- **作者**: Álvaro Somoza
- **时间**: 2026-07-30T07:39:11Z
- **提交信息**: [quantization] SDNQ core loading (#14277)

* initial

* fix code quality

* dependency test fix

* apply review suggestions

* add extras and version check

* fix gating and prefer local cache for modular

* simplify transformers registration and make the version warning silenceable

* remove pipeline level test

* only model level testing

* layers to quantizze, change em dashes

* env flag for transformers

---------

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-07-31
**监控日期**: 2026-07-30
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 427
- **最后更新**: 2026-07-28T14:17:53Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-07-31
**监控日期**: 2026-07-30
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12782
- **最后更新**: 2026-07-30T20:43:56Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-07-31
**监控日期**: 2026-07-30
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 30976
- **最后更新**: 2026-07-30T22:21:58Z

## 提交统计

- **昨日提交总数**: 34
- **提交者数量**: 21
- **主要提交者**: Zheng Wengang, Henning Thieß, Ho-Ren (Jack) Chuang

## AI分析总结

分析生成失败

## 详细提交记录

### [3a53c26](https://github.com/sgl-project/sglang/commit/3a53c26c27c8e2b705f2cc99fc81c53afa3921e1)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-07-30T22:21:51Z
- **提交信息**: [CI] Fix MoE compile and DSA indexer regressions (#32937)

### [85f9998](https://github.com/sgl-project/sglang/commit/85f9998524a357d55e9f24f1021a5f7affe32f18)

- **作者**: sglang-bot
- **时间**: 2026-07-30T21:56:22Z
- **提交信息**: docs: sync LMSYS SGLang blog cards (#32838)

Co-authored-by: sglang-bot <sglang-bot@users.noreply.github.com>

### [a6221d7](https://github.com/sgl-project/sglang/commit/a6221d776fe11d0e5859e1fa749f3a22c6c0c637)

- **作者**: Trevor Morris
- **时间**: 2026-07-30T21:32:03Z
- **提交信息**: feat: Support nvidia/MiniMax-M3-NVFP4 (#31989)

### [c4af6cf](https://github.com/sgl-project/sglang/commit/c4af6cf26397c16c1d3436d1f181c8d70790a16c)

- **作者**: Henning Thieß
- **时间**: 2026-07-30T21:30:26Z
- **提交信息**: Qwen3.5-MoE: support modelopt_fp4 checkpoints that quantize attention (+ load baked FP8 KV scales) (#31220)

### [5339450](https://github.com/sgl-project/sglang/commit/5339450ed46a323712409c5878fc03b3aa8e6846)

- **作者**: saatwiknagpal
- **时间**: 2026-07-30T21:10:06Z
- **提交信息**: Support SGLANG_SIMULATE_ACC_LEN for DFLASH (#32595)

### [3312645](https://github.com/sgl-project/sglang/commit/3312645a307453893a00778592f105581e3d1c3d)

- **作者**: Rain Jiang
- **时间**: 2026-07-30T19:46:19Z
- **提交信息**: wire the rust server modules into lib, runtime, and tokenizer manager (#32877)

### [047635e](https://github.com/sgl-project/sglang/commit/047635ee357debe0ae6bc1c03cb0b4fa15ba2148)

- **作者**: Rain Jiang
- **时间**: 2026-07-30T19:46:19Z
- **提交信息**: add the rust server native api handlers and runtime threads (#32876)

### [30643f8](https://github.com/sgl-project/sglang/commit/30643f88bc9145f41ae3c86fd60ada57b914e126)

- **作者**: Rain Jiang
- **时间**: 2026-07-30T19:46:19Z
- **提交信息**: add the rust server api frame codec and http server entry (#32875)

### [4facc0e](https://github.com/sgl-project/sglang/commit/4facc0e18a6c0ceffa840a034761d609fece641f)

- **作者**: Rain Jiang
- **时间**: 2026-07-30T19:46:18Z
- **提交信息**: add the rust server ingress tests, guard, and submit modules (#32874)

### [e2c65af](https://github.com/sgl-project/sglang/commit/e2c65af2299c17de11d66af09a8e1f5ba45f04a5)

- **作者**: Rain Jiang
- **时间**: 2026-07-30T19:46:17Z
- **提交信息**: add the rust server ingress request validation and api server common types (#32873)

### [922d6e5](https://github.com/sgl-project/sglang/commit/922d6e55427f702395958fe42cf0503a103aac60)

- **作者**: Rain Jiang
- **时间**: 2026-07-30T19:46:17Z
- **提交信息**: add the rust server tokenizer, detokenizer, and egress modules (#32872)

### [35f2e6a](https://github.com/sgl-project/sglang/commit/35f2e6ab58a20899d959e16da924b439ed6dabe2)

- **作者**: Rain Jiang
- **时间**: 2026-07-30T19:32:27Z
- **提交信息**: update Cargo.lock for the rust sglang-server dependencies (#32871)

### [04edadb](https://github.com/sgl-project/sglang/commit/04edadb34d774df2a58968e164802f43fb3f99d4)

- **作者**: Ke Bao
- **时间**: 2026-07-30T17:59:11Z
- **提交信息**: Add Inkling-Small cookbook (#32951)

Co-authored-by: Zijie Xia <zijie.xia@radixark.ai>
Co-authored-by: Yanbin Jiang <jybsuper@gmail.com>

### [b61cb5f](https://github.com/sgl-project/sglang/commit/b61cb5f9de87f07770ba216fab4fba1e6496f4e3)

- **作者**: Broduker
- **时间**: 2026-07-30T15:03:34Z
- **提交信息**: Fix DeepSeek V4 loading with RunAI Model Streamer. (#30240)

### [c5bd3d7](https://github.com/sgl-project/sglang/commit/c5bd3d7dce7623b8d2ffe3e662d3fd5198e6f4ba)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-07-30T14:11:18Z
- **提交信息**: [diffusion][benchmark] Add reproducible request-manifest offline benchmark (#32917)

### [7784ac8](https://github.com/sgl-project/sglang/commit/7784ac8f913aea30945fb7d5f339c7792ccb0f29)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-07-30T14:10:23Z
- **提交信息**: [diffusion][docs] Fix Cosmos3 model sizes (#32916)

### [2e9c82b](https://github.com/sgl-project/sglang/commit/2e9c82b35984d435430045b035e304dd7bd8eea1)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-07-30T14:08:57Z
- **提交信息**: [Kernel] Remove unreachable AOT headers (#32842)

### [48c1b37](https://github.com/sgl-project/sglang/commit/48c1b37a33813fb0816cb1a739c7df2a88404737)

- **作者**: Bingxu Chen
- **时间**: 2026-07-30T14:05:03Z
- **提交信息**: [AMD] Update ROCm AITER pin to d9e5ef7 (#32939)

Co-authored-by: Cursor Agent <cursoragent@cursor.com>

### [b78d399](https://github.com/sgl-project/sglang/commit/b78d3999b54b89219239f1eae2c4c59142d7b9b6)

- **作者**: cen121212
- **时间**: 2026-07-30T13:34:16Z
- **提交信息**: 【NPU】fix decode MTP + eagle shape error (#32791)

### [b129e8a](https://github.com/sgl-project/sglang/commit/b129e8a2999d465fb54d358dfbf4e612e0617bb9)

- **作者**: Mick
- **时间**: 2026-07-30T13:05:54Z
- **提交信息**: [diffusion] docs: surface diffusion AR and PE guides (#32932)

### [db3da62](https://github.com/sgl-project/sglang/commit/db3da62333c96e48bb1cc96448b78a79bdec4d51)

- **作者**: Mick
- **时间**: 2026-07-30T12:15:22Z
- **提交信息**: [diffusion] feat: unify encoder folding and batch data-parallel encoding (#30211)

### [1f04eaa](https://github.com/sgl-project/sglang/commit/1f04eaab6ac5756c28c8637e1f23b99cd25822a2)

- **作者**: Yi (Vincent) Zhong
- **时间**: 2026-07-30T10:15:08Z
- **提交信息**: Fix LFM 2 tool parser. (#27614)

### [fd86795](https://github.com/sgl-project/sglang/commit/fd8679510737e632e74255520bb21606caa04cf7)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-07-30T09:56:07Z
- **提交信息**: [AMD] MiniMax-M3: opt-in custom/quick all-reduce on ROCm (#32230)

### [9f56553](https://github.com/sgl-project/sglang/commit/9f5655340897ae0af9425acd528e809cf223c2dc)

- **作者**: Liangsheng Yin
- **时间**: 2026-07-30T09:55:21Z
- **提交信息**: [Perf] Fast-path chain-style draft token organization in multi-layer EAGLE (#32887)

### [04d6fb4](https://github.com/sgl-project/sglang/commit/04d6fb4d6c5ea9a2fe2ab27d8ccfb8f16e9e678e)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-07-30T09:43:27Z
- **提交信息**: [AMD] Minimax-M3 : unblock mxfp8 block convert on gfx950 (#32036)

### [4ba7d5a](https://github.com/sgl-project/sglang/commit/4ba7d5ad93a6c5efa1c44b34f53084cd81062dc7)

- **作者**: Zheng Wengang
- **时间**: 2026-07-30T09:36:55Z
- **提交信息**: [BugFix][EPD] Early-release mooncake GPU embeddings; fix gpu_id via scheduler.ps (#31591)

### [6ab3231](https://github.com/sgl-project/sglang/commit/6ab3231b976f0bf4cb257d8a0c57287005b22e73)

- **作者**: Liangsheng Yin
- **时间**: 2026-07-30T09:32:38Z
- **提交信息**: [Perf] Skip the target-verify tree mask fill when the backend never reads it (#32886)

Co-authored-by: Kaixi <kaiximatteoc@nvidia.com>

### [4b52758](https://github.com/sgl-project/sglang/commit/4b52758c76ca09c2f615d7325425de2be748ecb2)

- **作者**: kangwangamd
- **时间**: 2026-07-30T09:32:09Z
- **提交信息**: [AMD] Skip test_update_weights_from_disk on ROCm pending reload fix (#31924) (#31925)

### [fc007e1](https://github.com/sgl-project/sglang/commit/fc007e1f00fdadc25e831364a2df63a64af61fb9)

- **作者**: Ding Yin
- **时间**: 2026-07-30T08:48:10Z
- **提交信息**: Add SM90 FP8 MegaMoE support for DeepSeek-V4 (#29016)

Co-authored-by: yinding <yinding@bytedance.com>

### [f46d5f2](https://github.com/sgl-project/sglang/commit/f46d5f25b4c3b943167c6021aedb60415c4bfcd9)

- **作者**: Zhangheng
- **时间**: 2026-07-30T08:45:32Z
- **提交信息**: [4/N][CP] Support interleave strategy for cp v2 (#30482)

Co-authored-by: Xinyuan Tong <xinyuantong.cs@gmail.com>
Co-authored-by: Baizhou Zhang <sobereddiezhang@gmail.com>

### [c192145](https://github.com/sgl-project/sglang/commit/c192145830bf240f3fd3eedda6b6c111474f0d8b)

- **作者**: Liangsheng Yin
- **时间**: 2026-07-30T07:26:10Z
- **提交信息**: [Kernel] Fuse KV-cache writes for asymmetric K/V (head_dim != v_head_dim) (#32813)

### [2625fdf](https://github.com/sgl-project/sglang/commit/2625fdfe6b3d308b7e4e5caa07896e084d2692aa)

- **作者**: Liangsheng Yin
- **时间**: 2026-07-30T07:21:34Z
- **提交信息**: [Fix] Count multi-layer draft-extend replays in the fwd-occupancy device timer (#32867)

### [92b3a51](https://github.com/sgl-project/sglang/commit/92b3a51ba6192600d7c454983205041b18c733d0)

- **作者**: Yanbin Jiang
- **时间**: 2026-07-30T07:17:29Z
- **提交信息**: [LoRA] Fix Marlin MoE kernel import (#32884)

### [e4a40a7](https://github.com/sgl-project/sglang/commit/e4a40a71f84c73196e9b189fbeb01d0752733b43)

- **作者**: Ho-Ren (Jack) Chuang
- **时间**: 2026-07-30T07:15:11Z
- **提交信息**: [DSA] Q8KV8 FP8 Sparse Prefill on GLM-5.2 & DeepSeek-V3.2: Q8-Path & Shared-Path Optimizations (#31888)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-07-31
**监控日期**: 2026-07-30
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1240
- **最后更新**: 2026-07-30T09:22:20Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-07-31
**监控日期**: 2026-07-30
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 87717
- **最后更新**: 2026-07-30T22:26:03Z

## 提交统计

- **昨日提交总数**: 30
- **提交者数量**: 20
- **主要提交者**: Aaron Hao, Jiangyun Zhu, Wentao Ye

## AI分析总结

分析生成失败

## 详细提交记录

### [7fe5312](https://github.com/vllm-project/vllm/commit/7fe5312332cbc4a974a54a8be2e87e280f1c5bfa)

- **作者**: jcotant-inferact
- **时间**: 2026-07-30T22:25:28Z
- **提交信息**: [CI] Retire the v1 PR label rule, add mrv2 (#50475)

Signed-off-by: Joe Cotant <joe@inferact.ai>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [68fb303](https://github.com/vllm-project/vllm/commit/68fb303a4177f52b2a2795abe602031a6d330b83)

- **作者**: Ryan Clark
- **时间**: 2026-07-30T21:50:03Z
- **提交信息**: [Bugfix] Preserve Marlin runtime tensor storage across weight reload (#48438)

Signed-off-by: Ryan Clark <ryanclark2k@gmail.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [e9096fc](https://github.com/vllm-project/vllm/commit/e9096fcb123181467a6fff5326fe8387d578760c)

- **作者**: Bugen Zhao
- **时间**: 2026-07-30T21:18:17Z
- **提交信息**: [Rust Frontend] Improve startup failure and readiness logs (#50406)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [45b60e3](https://github.com/vllm-project/vllm/commit/45b60e39140a5576505d986c37b382b3985a3d9e)

- **作者**: Shangdi Yu
- **时间**: 2026-07-30T20:37:52Z
- **提交信息**: [Kernel][Helion] Disable unsafe B200 RMS reduction warp specialization (#50345)

Signed-off-by: Shangdi Yu <shangdiy@meta.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [0eec856](https://github.com/vllm-project/vllm/commit/0eec856cc31cf9d9518b547c37a610d3f02ccddb)

- **作者**: Michael Goin
- **时间**: 2026-07-30T20:26:24Z
- **提交信息**: Add Humming indexed-MoE regression test (#50468)

Signed-off-by: mgoin <mgoin64@gmail.com>

### [70bd109](https://github.com/vllm-project/vllm/commit/70bd10930bbb91af38fc243c53df4b94da80a8c9)

- **作者**: Netanel Haber
- **时间**: 2026-07-30T20:19:56Z
- **提交信息**: [Quantization] Honor `--linear-backend` for ModelOpt W4A16 (#50273)

Signed-off-by: Netanel Haber <58652339+netanel-haber@users.noreply.github.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [c27b080](https://github.com/vllm-project/vllm/commit/c27b080d262ee5966cf8d362d3a9d0cefd930908)

- **作者**: Richard Zou
- **时间**: 2026-07-30T19:50:02Z
- **提交信息**: [compile] Fix fake kernel return dtype (#50444)

Signed-off-by: Richard Zou <zou3519@gmail.com>
Co-authored-by: Codex <noreply@openai.com>

### [3f90c7e](https://github.com/vllm-project/vllm/commit/3f90c7e9e6d3f8e874756ada2dbcd353bf0803d9)

- **作者**: Andreas Karatzas
- **时间**: 2026-07-30T19:49:26Z
- **提交信息**: [ROCm] Pass pointers to FlyDSL MoE kernels (#50378)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [bdc98bf](https://github.com/vllm-project/vllm/commit/bdc98bf5060db48f5844fa35f9ffe1608710ba51)

- **作者**: Andreas Karatzas
- **时间**: 2026-07-30T19:34:08Z
- **提交信息**: [CI] Initialize fused gated RMSNorm weights (#50377)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [30e333c](https://github.com/vllm-project/vllm/commit/30e333ca5f0119385123e7e713462ffc7c8d7e45)

- **作者**: Andreas Karatzas
- **时间**: 2026-07-30T19:33:22Z
- **提交信息**: [Bugfix] Shut down private Tensorizer engines (#49840)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [629a938](https://github.com/vllm-project/vllm/commit/629a938a928476a167efc6428bf2fbd43b1dc888)

- **作者**: Bugen Zhao
- **时间**: 2026-07-30T19:25:10Z
- **提交信息**: [Frontend] Preserve bare Inkling text in Python and Rust parsers (#50403)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>

### [12a34a6](https://github.com/vllm-project/vllm/commit/12a34a6bc794135e3b93dd721a6bdcdb1bf734b9)

- **作者**: Mehmet Cagri
- **时间**: 2026-07-30T18:59:52Z
- **提交信息**: [ROCm][DSV4] B-preshuffle the attention fp8 projections (#46720)

Signed-off-by: Mehmet Cagri Kaymak <mehmet.kaymak@amd.com>
Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [5f8f728](https://github.com/vllm-project/vllm/commit/5f8f72866c4923fb06902cf60cf219a2340982e8)

- **作者**: Kevin H. Luu
- **时间**: 2026-07-30T18:48:09Z
- **提交信息**: [Build] Fix CUDA release wheel builds (#50243)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Michael Goin <mgoin64@gmail.com>

### [61cacd2](https://github.com/vllm-project/vllm/commit/61cacd272f5a95aa2a091d711ed91a4aa85522d5)

- **作者**: Netanel Haber
- **时间**: 2026-07-30T18:34:10Z
- **提交信息**: [Bugfix][MoE] Write Humming results to the supplied output buffer (#50338)

Signed-off-by: Netanel Haber <58652339+netanel-haber@users.noreply.github.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [837eae6](https://github.com/vllm-project/vllm/commit/837eae64580c885101ee95b073aafb27a485e7ce)

- **作者**: Wentao Ye
- **时间**: 2026-07-30T15:39:07Z
- **提交信息**: [DSv4 Perf] Remove redundant full kernel for dsv4, 1.88x kernel performance improvement (#50298)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [904fae8](https://github.com/vllm-project/vllm/commit/904fae8be12f1592b8e489fc0f1004fa49460a89)

- **作者**: Wentao Ye
- **时间**: 2026-07-30T15:38:51Z
- **提交信息**: [DSv4 Perf] Fix redundant memory allocation and copy for dsv4 pp buffer, 448 MiB GPU memory saved (#50312)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [f388dd6](https://github.com/vllm-project/vllm/commit/f388dd6592a3873636a3b5325e9db4849eb9e70f)

- **作者**: Kunshang Ji
- **时间**: 2026-07-30T15:27:28Z
- **提交信息**: [XPU][CI] skip kimi-k3 test (#50447)

Signed-off-by: Kunshang Ji <kunshang.ji@intel.com>

### [5b95890](https://github.com/vllm-project/vllm/commit/5b958907420e3e4dcbccd47ce912218475c885cc)

- **作者**: Andreas Karatzas
- **时间**: 2026-07-30T15:24:13Z
- **提交信息**: [FlexAttention] Avoid encoder block-mask compile explosion (#50339)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [30b4e7f](https://github.com/vllm-project/vllm/commit/30b4e7f479674a9c4d8889d4857294d3bd5e6849)

- **作者**: Aaron Hao
- **时间**: 2026-07-30T13:59:08Z
- **提交信息**: [rl] Stateful Trainer Send: IPC [2/N] (#48981)

Signed-off-by: haoaaron <ahao@anyscale.com>

### [59e831c](https://github.com/vllm-project/vllm/commit/59e831c09a22bdd2732b86a158ff771584b14793)

- **作者**: BadrBasowid
- **时间**: 2026-07-30T13:46:36Z
- **提交信息**: [Compilation]Fuse Transformers Residual Add + RMSNorm (#48757)

Signed-off-by: BadrBasowid <badr.basowid@gmail.com>

### [1a20d23](https://github.com/vllm-project/vllm/commit/1a20d23dab6eef0ce6ab97b7e03c944683cdf90b)

- **作者**: Julien Denize
- **时间**: 2026-07-30T13:38:00Z
- **提交信息**: [PARSER][Mistral] unified engine-based parser for reasoning and tool calls (#48947)

### [e2efe79](https://github.com/vllm-project/vllm/commit/e2efe79695e0f92395c029a6a7907c02a0374678)

- **作者**: sroberts-amd
- **时间**: 2026-07-30T13:37:43Z
- **提交信息**: [ROCm]Migrating Deepseek V3.2 to vllm/models/deepseek_v32/ (#47207)

Signed-off-by: sroberts-amd <sroberts@amd.com>
Signed-off-by: Stacy Roberts <sroberts@amd.com>
Co-authored-by: Elvir Crncevic <elvircrn@gmail.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [38a267c](https://github.com/vllm-project/vllm/commit/38a267cdd5b30841bb2e2913d67ba18544098c3a)

- **作者**: Martin Hickey
- **时间**: 2026-07-30T12:02:51Z
- **提交信息**: [MyPy][1/N] Fix mypy errors in some tests/ directories and enforce follow-imports=silent (#49570)

Signed-off-by: Martin Hickey <martin.hickey@ie.ibm.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [89d97d9](https://github.com/vllm-project/vllm/commit/89d97d9a165a7fb2c84ffb77c8da816093bba0ed)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-07-30T11:52:55Z
- **提交信息**: docs(security): document Ray cluster trust model and env var propagation (#50397)

Signed-off-by: jperezde <jperezde@redhat.com>

### [072a472](https://github.com/vllm-project/vllm/commit/072a4727820732fb9e1480dd3deffb9070520b41)

- **作者**: Li, Jiang
- **时间**: 2026-07-30T11:18:43Z
- **提交信息**: [CPU] Bump up CPU kernels to latest version (#50387)

Signed-off-by: jiang1.li <jiang1.li@intel.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [aeeb36b](https://github.com/vllm-project/vllm/commit/aeeb36b1f17145975c6713242f2447bb8b98782b)

- **作者**: Jiangyun Zhu
- **时间**: 2026-07-30T10:49:58Z
- **提交信息**: [New model] Kimi K3 (#50000)

Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>
Signed-off-by: Isotr0py <Isotr0py@outlook.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>
Signed-off-by: Yifan Qiao <yifanqiao@inferact.ai>
Signed-off-by: Yongye Zhu <zyy1102000@gmail.com>
Signed-off-by: wzhao18 <wzhao18.sz@gmail.com>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: Thien Tran <gau.nernst@yahoo.com.sg>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Yongye Zhu <zyy1102000@gmail.com>
Co-authored-by: Ziming Huang <zelda.huanghuang@gmail.com>
Co-authored-by: Roger Wang <hey@rogerw.io>
Co-authored-by: Isotr0py <mozf@inferact.ai>
Co-authored-by: aoshen02 <aoshen02@users.noreply.github.com>
Co-authored-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: Jee Jee Li <jeejeelee@inferact.ai>
Co-authored-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: Summer Yang <girasoleyang@gmail.com>
Co-authored-by: Kevin H. Luu <khluu000@gmail.com>
Co-authored-by: Bowen Wang <abmfy@icloud.com>
Co-authored-by: gnovack <novackgm@gmail.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Yifan Qiao <yifanqiao@inferact.ai>
Co-authored-by: xiaozhoupy <peiyuanzhou1994@gmail.com>
Co-authored-by: Roy Wang <yasong.wang@inferact.ai>
Co-authored-by: Jeff (Junze) Ma <93145857+majunze2001@users.noreply.github.com>
Co-authored-by: Codex <codex@openai.com>
Co-authored-by: Wei Zhao <51183510+wzhao18@users.noreply.github.com>

### [0c64be8](https://github.com/vllm-project/vllm/commit/0c64be8873307c8db5901178f00945ce41866f2d)

- **作者**: Andreas Karatzas
- **时间**: 2026-07-30T10:46:37Z
- **提交信息**: [Test][ROCm] Account for gfx950 FP8 RMSNorm rounding (#49839)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [61c1d09](https://github.com/vllm-project/vllm/commit/61c1d098e5124f3566b22a3178ef46551a4bd8e3)

- **作者**: Andreas Karatzas
- **时间**: 2026-07-30T10:42:55Z
- **提交信息**: [CI] Stabilize speculator memory teardown (#50284)

Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>

### [165ed33](https://github.com/vllm-project/vllm/commit/165ed33327c04db3e26c6e433f721a1f68754558)

- **作者**: Andreas Karatzas
- **时间**: 2026-07-30T10:42:03Z
- **提交信息**: [CI][ROCm] Stabilize LLM GC teardown check (#50340)

Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>

### [48a077e](https://github.com/vllm-project/vllm/commit/48a077e4cfaa5425ac5df67ce95f07a99c6d26d5)

- **作者**: Kevin H. Luu
- **时间**: 2026-07-30T09:48:36Z
- **提交信息**: [CI] Improve comment-triggered authorization and retries (#50414)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-07-31
**监控日期**: 2026-07-30
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 5748
- **最后更新**: 2026-07-30T21:02:40Z

## 提交统计

- **昨日提交总数**: 14
- **提交者数量**: 13
- **主要提交者**: Alex Brooks, akshatvishu, SYLAR

## AI分析总结

### 主要更新类型
- **Bug修复**：共8个（占57%），涉及扩散模型、音频生成、模型加载等边界条件与稳定性问题。
- **重构**：共3个（占21%），聚焦部署配置统一与请求参数标准化。
- **功能新增**：1个（分布式分层卸载，提升显存效率）。
- **CI/构建**：1个（MiniCPM-o自动响应前输入提交）。
- **模型支持**：1个（移除Flux2文本编码器输出层硬编码，添加Cosmos3-Edge预设）。

### 关键变更点与项目方向的关系
- **扩散模型稳定性**：修复CFG bundle不完整分发、缺少CPU LAPACK降级、MagCache跳过步应用、HF_HUB_OFFLINE兼容性等问题，直接支撑项目“**easy & fast**”的多模态服务目标，减少用户部署障碍。
- **音频生成质量**：解决流式音频卡顿、TTS权重加载遗漏、Qwen3-TTS占位帧输出问题，提升语音模态的可靠性。
- **架构统一化**：重构Step-Audio2和Qwen3 Omni thinker的部署配置，并标准化扩散请求额外参数，有助于项目“**cheap**”的规模化

## 详细提交记录

### [a951dd0](https://github.com/vllm-project/vllm-omni/commit/a951dd0cb4eeb9a6c28b2a075e62c2144b1bc272)

- **作者**: Zhou Taichang
- **时间**: 2026-07-30T15:17:24Z
- **提交信息**: [BugFix] Never dispatch diffusion with an incomplete CFG companion bundle (#5482)

Signed-off-by: tzhouam <tzhouam@gmail.com>
Co-authored-by: tzhouam <tzhouam@gmail.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [4563999](https://github.com/vllm-project/vllm-omni/commit/4563999ec0e4376e81df21168542b1ccd1ae2fad)

- **作者**: akshatvishu
- **时间**: 2026-07-30T15:09:48Z
- **提交信息**:  [BugFix][Diffusion] Add CPU LAPACK fallback for FlowUniPC (#5329)

Signed-off-by: akshatvishu <akshatnayak197@gmail.com>

### [86d7864](https://github.com/vllm-project/vllm-omni/commit/86d78645883b501f60f185ef290af91c495d2ac7)

- **作者**: Weiming Liao
- **时间**: 2026-07-30T15:07:46Z
- **提交信息**: [Bugfix][Diffusion] Honor HF_HUB_OFFLINE in OmniDiffusionConfig (align with AR stage) (#5403)

Signed-off-by: Weiming Liao <liaowm5@gmail.com>
Signed-off-by: Weiming Liao <fayespica@outlook.com>
Co-authored-by: 汪志鹏 <wangzhipeng628@gmail.com>

### [3b0718f](https://github.com/vllm-project/vllm-omni/commit/3b0718f22e5df5f384ae05c2ec9c8d65976e069c)

- **作者**: Shenglei Fu
- **时间**: 2026-07-30T14:56:18Z
- **提交信息**: [Bugfix] Fix active_stream_window silently stalling audio generation (#5349) (#5373)

Signed-off-by: Shenglei Fu <sfu@confluent.io>
Co-authored-by: Claude <noreply@anthropic.com>

### [ce3d8e4](https://github.com/vllm-project/vllm-omni/commit/ce3d8e4bacee8411f20f9c3ebbbe62938f8e6c64)

- **作者**: Yuanheng Zhao
- **时间**: 2026-07-30T14:38:40Z
- **提交信息**: [Bufix] Ming-omni-tts-16.8B Skip rejected and unused weights loading (#5607)

Signed-off-by: Yuanheng Zhao <jonathan.zhaoyh@gmail.com>

### [81cd796](https://github.com/vllm-project/vllm-omni/commit/81cd7964d4eb831a9eeff38ce7e439abaac10c5d)

- **作者**: Henry J
- **时间**: 2026-07-30T14:27:39Z
- **提交信息**: [Bugfix] Qwen3-TTS full-payload: emit one placeholder frame on a degenerate take instead of an empty payload (#5472)

Signed-off-by: henryj <349043+henryj@users.noreply.github.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [09c6ad4](https://github.com/vllm-project/vllm-omni/commit/09c6ad4204942536dfec3be5d3e20d934e1696a6)

- **作者**: Sy03
- **时间**: 2026-07-30T14:14:19Z
- **提交信息**: [CI/Build][MiniCPM-o] Allow auto-response before input commit (#5567)

Signed-off-by: Sy03 <1370724210@qq.com>

### [f7e87e7](https://github.com/vllm-project/vllm-omni/commit/f7e87e7cfdf56bdb0fbb748ea6f2df376e89ee9e)

- **作者**: Yash Jain
- **时间**: 2026-07-30T14:09:25Z
- **提交信息**: [Bugfix][Diffusion] Apply MagCache residual once per skipped step (#5561)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [744c65b](https://github.com/vllm-project/vllm-omni/commit/744c65b730e8820732610161efe0aa2375825799)

- **作者**: evanchueng
- **时间**: 2026-07-30T13:35:38Z
- **提交信息**: [Feature] Distributed layerwise offload with DP multi-concurrency + mmap weight… (#5397)

Signed-off-by: evanchueng <evanchueng@outlook.com>
Signed-off-by: david6666666 <530634352@qq.com>
Co-authored-by: david6666666 <530634352@qq.com>

### [b3f4fbf](https://github.com/vllm-project/vllm-omni/commit/b3f4fbf9e217ab6174fc0c475e33a478006ac34c)

- **作者**: Yukim1
- **时间**: 2026-07-30T09:59:05Z
- **提交信息**: [Refactor] Migrate Step-Audio2 offline test to deploy config (#5319)

Signed-off-by: zwhzzz0821 <2831474076@qq.com>

### [1752e8e](https://github.com/vllm-project/vllm-omni/commit/1752e8ee5b75e1169116560a6c2820b6fc9cc863)

- **作者**: Yukim1
- **时间**: 2026-07-30T09:57:33Z
- **提交信息**: [Refactor] Migrate Qwen3 Omni thinker-only deploy config (#5285)

Signed-off-by: zwhzzz0821 <2831474076@qq.com>

### [089bb88](https://github.com/vllm-project/vllm-omni/commit/089bb88706d4e3038f370981a4d3d4b7e2910eec)

- **作者**: Alex Brooks
- **时间**: 2026-07-30T09:55:42Z
- **提交信息**: [Model] Remove Text Encoder Output Layer Hardcoding in Flux2 (#5589)

Signed-off-by: Alex Brooks <albrooks@redhat.com>

### [04b408f](https://github.com/vllm-project/vllm-omni/commit/04b408ffd2251e7e24db250b5174209a6838735c)

- **作者**: SYLAR
- **时间**: 2026-07-30T08:41:30Z
- **提交信息**: [Bugfix] Add Cosmos3-Edge preset (fix wrong Nano/Super defaults in T2V/I2V examples) (#5596)

Signed-off-by: lishunyang12 <lishunyang03@gmail.com>
Co-authored-by: lishunyang12 <lishunyang03@gmail.com>

### [0c88f8a](https://github.com/vllm-project/vllm-omni/commit/0c88f8a0b662ae497a6485db6f3b91b79620608c)

- **作者**: TaffyOfficial
- **时间**: 2026-07-30T07:08:12Z
- **提交信息**: [Refactor] Normalize diffusion request extra arguments in Chat serving (#5171)

Signed-off-by: TaffyOfficial <2324465096@qq.com>
Co-authored-by: TaffyOfficial <2324465096@qq.com>

---
