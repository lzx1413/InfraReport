# GitHub Stars 合并报告 - 2026-06-24

**合并日期**: 2026-06-25
**监控日期**: 2026-06-24
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


**报告日期**: 2026-06-25
**监控日期**: 2026-06-24
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2043
- **最后更新**: 2026-06-24T07:12:44Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-06-25
**监控日期**: 2026-06-24
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2438
- **最后更新**: 2026-06-24T14:49:43Z

## 提交统计

- **昨日提交总数**: 5
- **提交者数量**: 3
- **主要提交者**: Musisoul, Watebear, yihuiwen

## AI分析总结

根据提供的仓库 `ModelTC/LightX2V` 的 5 条提交记录，结合 README 中“轻量视频生成推理框架”的项目定位，以下是对昨日更新的要点总结：

---

### 1. 主要更新类型
- **功能新增**：全部 5 条提交均为新功能或训练支持，无 Bug 修复、性能优化或文档更新。

### 2. 关键变更点及其与项目整体方向的关系
- **训练能力扩展**：
  - 添加了 **longcat** 和 **flux** 的完整训练脚本（#1171）。
  - 支持 **longcat/flux-dev** 的 DMD/CDM 蒸馏训练，以及 **flux-dev** 的 LoRA 训练和 DMD/CDM 蒸馏训练（#1181）。
  - 添加了 **Qwen-image-edit** 的 LoRA 训练（#1151）。
  - 将 **CDM 方法集成到 DMD-LoRA 训练**中（#1165）。
- **API 增强**：
  - 在 OpenAI 风格的图像 API 响应中增加了 **token 用量计算**（input/output tokens），涉及 `/v1/images/generations` 和 `/v1/images/edits` 端点（#1180）。

> 这些变更与项目方向的关系：LightX2V 定位为视频生成推理框架，但此次提交显著扩展了其训练支持（多种模型的 LoRA、蒸馏训练），使框架同时具备训练与推理能力，并增强了 API 的可用性（token 计量），有利于吸引更多用户进行模型定制和部署。

### 3. 对项目的影响和潜在意义
- **提升模型生态兼容性**：支持 longcat、flux-dev、Qwen-image-edit 等主流模型，降低了用户定制门槛。
- **训练方法灵活化**：引入 DMD、CDM 蒸馏和 LoRA 训练，适合资源受限场景下的模型微调或轻量化。
- **API 完善**：token 计数符合 OpenAI 兼容标准，便于服务计费和监控，增强生产环境实用性。

### 4. 值得关注的技术点
- **CDM 集成到 DMD-LoRA**：这是蒸馏与参数高效微调（LoRA）的组合方法，可能有效平衡模型性能与训练效率。
- **flax-dev 的多训练模式**：同时支持 LoRA 和蒸馏训练，验证框架对扩散模型不同优化策略的适配。
- **token 用量计算机制**：通过 runner 引擎计算 token，而非简单的字符统计，体现了对内部推理流程的精确追踪。

### 5. 对项目发展的影响（结合 README 背景）
- 从纯推理框架向 **训练-推理一体化** 演进：虽然 README 强调“轻量视频生成推理”，但新增的训练脚本使框架能支撑模型蒸馏和定制，可能成为后续版本的核心竞争力。
- **强化视频生成基础**：longcat 和 flux 均为视频生成相关模型（longcat

## 详细提交记录

### [7102bfa](https://github.com/ModelTC/LightX2V/commit/7102bfaa943b9ca4a05fc205b304cb7683624521)

- **作者**: Watebear
- **时间**: 2026-06-24T08:53:22Z
- **提交信息**: [Train]: add longcat & flux full scripts (#1171)

Co-authored-by: chendingyu <chendingyu1@sensetime.com>

### [7d87dd7](https://github.com/ModelTC/LightX2V/commit/7d87dd7b7e282ae5daad2d8c00ac4cb896d4be00)

- **作者**: Musisoul
- **时间**: 2026-06-24T08:40:39Z
- **提交信息**: [Train] Support longcat/flux-dev dmd/cdm training (#1181)

1. longcat dmd/cdm distill training
2. flux-dev lora training
3. flux-dev dmd/cdm distill training

---------

Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>

### [6a7b8ae](https://github.com/ModelTC/LightX2V/commit/6a7b8ae7313ac9a3154c72e948d2a88bafd5b842)

- **作者**: Musisoul
- **时间**: 2026-06-24T07:12:33Z
- **提交信息**: [Train] Qwen-image-edit lora training (#1151)

### [222548f](https://github.com/ModelTC/LightX2V/commit/222548f32ed2ebf3b1fd24a75021f3a4f2f66d35)

- **作者**: Musisoul
- **时间**: 2026-06-24T07:11:05Z
- **提交信息**: [Train] Integrating the CDM method in DMD-LoRA training (#1165)

Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>

### [08bd4f9](https://github.com/ModelTC/LightX2V/commit/08bd4f94a1fa61b2094fc05b02302f8fa3efe48a)

- **作者**: yihuiwen
- **时间**: 2026-06-24T07:04:45Z
- **提交信息**: Add token usage computation to OpenAI image API response (#1180)

Compute input/output token counts via runner and return usage metadata
in /v1/images/generations and /v1/images/edits responses.

---------

Co-authored-by: yihuiwen <yihuiwen@sensetime.com>
Co-authored-by: Claude Opus 4.7 <noreply@anthropic.com>

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-06-25
**监控日期**: 2026-06-24
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2147
- **最后更新**: 2026-06-24T14:17:49Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-06-25
**监控日期**: 2026-06-24
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5851
- **最后更新**: 2026-06-24T23:26:07Z

## 提交统计

- **昨日提交总数**: 5
- **提交者数量**: 4
- **主要提交者**: Mingyang Wang, Brayden Zhong, Brian K. Ryu

## AI分析总结

根据提供的提交记录（共5个），以下是昨日更新的分析总结：

### 主要更新类型
- **功能新增**（3个）：MLA变长查询支持、ReLU²激活函数的MoE、基准测试新参数
- **Bug修复**（1个）：修复b12x MoE权重缓存无限增长的内存泄漏
- **性能优化**（1个）：FP4矩阵乘法启用SwapAB并改进自动调优，提升小批量解码速度

### 关键变更点与项目方向关系
1. **MLA支持`cum_seq_lens_q`**（#3238）  
   - 为`trtllm_batch_decode_with_kv_cache_mla`的trtllm-gen后端添加可变序列长度查询支持，使得MLA解码可处理不等长请求。这对部署多用户、动态长度的推理场景至关重要，补齐了MLA的重要功能缺口。

2. **CuteDSL MoE添加ReLU² + ungated激活**（#3642）  
   - 原先仅支持SwiGLU，新增ReLU²是为了支撑Nemotron-3模型（SGLang端已验证）。直接扩展了项目支持的主流模型范围，契合“通用推理内核库”定位。

3. **修复b12x MoE权重缓存内存泄漏**（#3709）  
   - `_WEIGHT_CACHE`和`_W4A16_WEIGHT_CACHE`两个缓存从未被清理，导致显存持续增长。通过`weakref.finalize`将缓存条目的生命周期绑定到源权重对象的GC时刻，彻底解决进程级内存泄漏，提升长时间服务稳定性。

4. **FP4 `mm_fp4` cute-dsl后端启用SwapAB**（#3667）  
   - 当M不是8的倍数时，自动进行SwapAB以提高矩阵乘法效率，并通过离线调优设定M≤32时启用。在DSV3形状上获得1.1x~1.26x速度提升，Llama 3.3 70B FP4解码TPS预计从135提升至140。说明项目持续深耕FP4低比特推理性能。

5. **MLA基准测试增加`--mla_is_var_seq`和`--mla_cute_dsl_impl`参数**（#3695）  
   - 之前基准测试始终使用API默认值（is_var_seq=True，cute_dsl_impl=auto），无法覆盖变长/固定长度路径或modular调度器。新增开关允许显式指定这些参数，并记录到CSV，便于回归检测特定路径（如#3132修复的modular+persistent路径）的性能变化。

### 对项目的影响与潜在意义
- **功能完整性**：MLA变长支持使项目的“注意力

## 详细提交记录

### [7f5b7d1](https://github.com/flashinfer-ai/flashinfer/commit/7f5b7d1b312126a59f8111a1c39f1580ab68e445)

- **作者**: Mingyang Wang
- **时间**: 2026-06-24T22:52:45Z
- **提交信息**: trtllm_batch_decode_with_kv_cache_mla trtllm-gen backend cum_seq_lens_q support (#3238)

## 📌 Description

Adds `cum_seq_lens_q` support to the `trtllm-gen` path in
`trtllm_batch_decode_with_kv_cache_mla`.

## 🔍 Related Issues

https://github.com/flashinfer-ai/flashinfer/issues/3131

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

Validation run:

- `pre-commit run --files flashinfer/mla/_core.py
flashinfer/trace/templates/attention.py
tests/attention/test_trtllm_gen_mla.py`
- `python3 -m py_compile flashinfer/mla/_core.py
flashinfer/trace/templates/attention.py
tests/attention/test_trtllm_gen_mla.py`
- `git diff --check`
- Remote SM100 GPU pytest in FlashInfer CI container:
-
`tests/attention/test_trtllm_gen_mla.py::test_trtllm_batch_decode_mla[True-True-False-trtllm-gen-False-False-2-64-dtype1-1.0-4-layer_dimensions0]`
-
`tests/attention/test_trtllm_gen_mla.py::test_trtllm_batch_decode_mla[True-False-False-trtllm-gen-False-False-2-64-dtype1-1.0-4-layer_dimensions0]`

## Reviewer Notes

The new argument is query-side metadata only. `seq_lens` and
`max_seq_len` continue to describe KV cache lengths; `max_q_len` is
derived from `cum_seq_lens_q` and is not exposed as a new public API
argument.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
- Support for variable-length per-request (ragged) MLA queries in batch
decode, with optional cumulated-sequence-lengths and max-query-length
handling and runtime dispatch between dense and ragged traces.
- New public trace variants for dense and ragged per-token MLA decodes
and a dispatching trace entrypoint.

* **Tests**
- Added and extended tests covering dense/ragged decode paths,
cumulated-sequence-lengths workflows, validation, and mismatch/error
cases.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [2f9a93b](https://github.com/flashinfer-ai/flashinfer/commit/2f9a93bda0ba31d6960437be91de4f54e5d5a258)

- **作者**: Brayden Zhong
- **时间**: 2026-06-24T17:46:51Z
- **提交信息**: Add Relu2 + ungated MoE to CuteDSL MoE (#3642)

<!-- .github/pull_request_template.md -->

## 📌 Description

It's needed for Nemotron-3 (currently, only SwiGLU is supported)

Validated E2E in SGLang. Ref:
https://github.com/sgl-project/sglang/pull/28309

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

## 🔍 Related Issues

N/A

<!-- Link any related issues here -->

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

SM103 test result:
```
python tests/moe/test_cute_dsl_fused_moe.py
=========================================================================================================== test session starts ===========================================================================================================
platform linux -- Python 3.12.3, pytest-9.0.3, pluggy-1.6.0 -- /usr/bin/python
cachedir: .pytest_cache
rootdir: /sgl-workspace/flashinfer
configfile: pytest.ini
plugins: anyio-4.13.0, typeguard-4.5.2
collected 205 items                                                                                                                                                                                                                       
...

============================================================================================================ warnings summary =============================================================================================================
tests/moe/test_cute_dsl_fused_moe.py: 80 warnings
  /usr/local/lib/python3.12/dist-packages/nvidia_cutlass_dsl/python_packages/cutlass/base_dsl/_mlir_helpers/op.py:121: DeprecationWarning: make_blockscaled_trivial_tiled_mma with ab_dtype is deprecated, use the overload with separate a_dtype and b_dtype instead
    res_or_list = opFunc(*args, **kwargs, loc=loc)

tests/moe/test_cute_dsl_fused_moe.py: 16 warnings
  /usr/local/lib/python3.12/dist-packages/nvidia_cutlass_dsl/python_packages/cutlass/base_dsl/_mlir_helpers/op.py:121: DeprecationWarning: API is deprecated, use setmaxregister_decrease instead
    res_or_list = opFunc(*args, **kwargs, loc=loc)

-- Docs: https://docs.pytest.org/en/stable/how-to/capture-warnings.html
============================================================================================== 205 passed, 96 warnings in 140.16s (0:02:20) ===============================================================================================
```

## Reviewer Notes

Does not break public APIs

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

## Summary

* **New Features**
* Added configurable FC1 activation to CuteDSL fused MoE via a new
`activation: str` parameter (default: `"silu"`), supporting both gated
(SiLU/SwiGLU) and non-gated (ReLU²) activation modes.
* Updated the fused MoE tracing/trace template to carry the activation
setting and adjust FC1 output sizing accordingly.

* **Tests**
* Extended reference computation and test tensor setup for
`activation="relu2"`.
* Updated numerical accuracy and wrapper autotune tests to validate both
`"silu"` and `"relu2"` paths.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Brayden Zhong <brayden@radixark.ai>

### [f53f5b0](https://github.com/flashinfer-ai/flashinfer/commit/f53f5b0d578d23fc2d93f0f4049225bf4e5caece)

- **作者**: Brian K. Ryu
- **时间**: 2026-06-24T17:20:34Z
- **提交信息**: fix(moe): Fix unbounded weight-cache growth in b12x MoE (#3709)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

The `b12x` fused-MoE dispatch keeps two weight caches, `_WEIGHT_CACHE`
and `_W4A16_WEIGHT_CACHE` in `moe_dispatch.py`. Both are never evicted,
so entries lived for the whole process.

The primary consequence is memory leak and unbounded growth.
`_WEIGHT_CACHE` stored views of the source weights, pinning that GPU
memory; `_W4A16_WEIGHT_CACHE` stored repacked weight copies → unbounded
growth.

### Fix
Tie each cache entry's lifetime to the source weight tensors via
[weakref.finalize](https://docs.python.org/3/library/weakref.html#weakref.finalize),
so an entry is evicted as soon as the weights it was derived from are
garbage-collected.
  
**No public API or kernel behavior changes; this is purely cache
lifecycle.**

On performance: No steady-state cost on the wrapper / CUDA-graph path
introduced. `B12xMoEWrapper` caches the resolved `_WeightViews` on the
instance and passes it during launch.

## 🔍 Related Issues

<!-- Link any related issues here -->

* Fixes #3354

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

* **Performance Improvements**
* Improved memory management for mixture-of-experts (MoE) weight
caching, reducing memory overhead and ensuring more reliable cleanup
when weights are no longer in use.
* Weight processing remains fully compatible across existing weight
formats and workflows.

* **Chores**
* Refined internal caching behavior to better align cache lifetimes with
the lifetime of the underlying weight tensors, improving overall runtime
resource utilization.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [01e65a0](https://github.com/flashinfer-ai/flashinfer/commit/01e65a02d43f53105c8759eaa194591c87077db7)

- **作者**: Brayden Zhong
- **时间**: 2026-06-24T16:13:59Z
- **提交信息**: Enable SwapAB in `mm_fp4` `cute-dsl` backend when M is not a multiple of 8. (#3667)

<!-- .github/pull_request_template.md -->

## 📌 Description

Enable SwapAB in `mm_fp4` `cute-dsl` backend when M is not a multiple of
8, and through offline tuning, use M <= 32 as a heuristic for SwapAB
(typically, this is the point where there is no benefit).

Note: it's very similar to
https://github.com/flashinfer-ai/flashinfer/pull/3464, except add the
cuda-graph and cold-L2 mode, since otherwise the autotuner will fail to
profile the correct timings. (Note: this is currently already used in
`trtllm_fp*_block_scale_moe` autotuning. This also fixes
https://github.com/flashinfer-ai/flashinfer/issues/3648, where the
autotuner fails to pick the fastest tile on Llama 3.3 70B FP4 shapes

As well, fix some warnings emitted from the DSL, with 4.5.0

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

## 🔍 Related Issues

<!-- Link any related issues here -->

For example, here are the speedups in the M = 1 case in DSV3 shapes:

| K | N | Before — Tile Size | Before — Cluster Shape | Before — Swap AB
| Before (µs) | After — Tile Size | After — Cluster Shape | After — Swap
AB | After (µs) | Speedup |

|-----:|-----:|:------------------:|:----------------------:|:----------------:|------------:|:-----------------:|:---------------------:|:---------------:|-----------:|:-------:|
| 256 | 7168 | 128 × 64 | 1 × 2 | No | 3.81 | 128 × 32 | 1 × 1 | Yes |
3.26 | 1.17× |
| 2048 | 7168 | 128 × 64 | 1 × 4 | No | 6.02 | 128 × 16 | 1 × 1 | Yes |
5.47 | 1.10× |
| 2304 | 7168 | 128 × 64 | 1 × 4 | No | 6.16 | 128 × 16 | 1 × 1 | Yes |
5.57 | 1.11× |
| 3584 | 1024 | 256 × 64 | 4 × 4 | No | 5.82 | 128 × 8 | 1 × 1 | Yes |
4.90 | 1.19× |
| 3584 | 9216 | 128 × 128 | 1 × 4 | No | 9.06 | 128 × 16 | 1 × 1 | Yes |
7.20 | 1.26× |

In the E2E framework speedup, it could be around 135 -> 140 TPS in BS =
1 decoding.

Here are the cases for Llama 3.3 70B FP4 + TP4:

| Shape (M × K) × (K × N) | Before — Tile Size | Before — Cluster Shape
| Before — Swap AB | Before (µs) | After — Tile Size | After — Cluster
Shape | After — Swap AB | After (µs) | Speedup |

|:------------------------:|:------------------:|:----------------------:|:----------------:|------------:|:-----------------:|:---------------------:|:---------------:|-----------:|:-------:|
| (1, 1024) × (1024, 8192) | 128 × 64 | 1 × 4 | No | 4.99 | 128 × 8 | 1
× 1 | Yes | 4.32 | 1.16× |
| (1, 3584) × (3584, 8192) | 128 × 64 | 1 × 4 | No | 7.90 | 128 × 16 | 1
× 1 | Yes | 6.94 | 1.14× |


### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

```
pytest tests/gemm/test_mm_fp4.py
=========================================================================================================== test session starts ===========================================================================================================
platform linux -- Python 3.12.3, pytest-9.0.3, pluggy-1.6.0
rootdir: /sgl-workspace/flashinfer
configfile: pytest.ini
plugins: anyio-4.13.0, typeguard-4.5.2
collected 23957 items  
...
============================================================================================================ warnings summary =============================================================================================================
tests/conftest.py:16
tests/conftest.py:16
  /sgl-workspace/flashinfer/tests/conftest.py:16: DeprecationWarning: tcgen05.OperandMajorMode is deprecated, use cute.nvgpu.OperandMajorMode instead
    from cutlass.cute.nvgpu.tcgen05 import OperandMajorMode

-- Docs: https://docs.pytest.org/en/stable/how-to/capture-warnings.html
======================================================================================= 6336 passed, 17621 skipped, 2 warnings in 797.85s (0:13:17) =======================================================================================
```

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Fixed SM100 block-scaled GEMM setup to consistently respect the B
operand dtype.
* Improved FP4 (SM100, cute-dsl) tactic selection and swap handling,
with updated validity rules based on N alignment and broader small-M
support.
* Added/strengthened FP4 validation so the cute-dsl backend is only used
when N is 8-aligned (otherwise it errors/falls back).

* **Performance**
* Improved FP4 autotuning defaults by enabling CUDA Graphs and cold L2
caching.

* **Tests**
* Expanded FP4 coverage and added a negative test for misaligned N
behavior.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Brayden Zhong <brayden@radixark.ai>
Co-authored-by: Vincent <34876120+Vinnie6167@users.noreply.github.com>

### [ba3dd07](https://github.com/flashinfer-ai/flashinfer/commit/ba3dd07f9b461badcf998a57d7461e5518d065ba)

- **作者**: lunarz-dev
- **时间**: 2026-06-24T16:11:16Z
- **提交信息**: feat(benchmark): add MLA --mla_is_var_seq / --mla_cute_dsl_impl knobs (#3695)

`testBatchMLAPagedAttentionWrapper` never passes `is_var_seq` or
`cute_dsl_impl` to `trtllm_batch_decode_with_kv_cache_mla`, so the MLA
decode benchmark always runs the API defaults (`is_var_seq=True`, the
var-seq scheduler; `cute_dsl_impl="auto"`, which runs monolithic and
only promotes to modular for modular-only features). The CuTe DSL FP8
MLA decode regression fixed in #3132 lives on the *modular + persistent*
path (`is_persistent = not is_var_seq`), which neither default reaches,
so it could not be benchmarked or guarded. This adds explicit knobs for
both.

- Add `--mla_is_var_seq {true,false,auto}` (MLA-only). **Default
unset**: `is_var_seq` is not passed and the API default (`True`) is
kept, so existing cases and perf baselines are unchanged. `auto`
resolves to `--random_actual_seq_len`.
- Add `--mla_cute_dsl_impl {auto,modular,monolithic}` (MLA-only).
**Default unset**: `cute_dsl_impl` is not passed and the API default
(`auto`) is kept. `modular` is required to benchmark/guard the path
#3132 regressed on.
- Forward the resolved values to the `trtllm-native` / `auto` /
`cute-dsl` direct-API branches, kept consistent across all three so
backend comparisons stay meaningful. `fa2`/`fa3`/`cutlass` wrapper
backends are unaffected.
- Record `is_var_seq` / `cute_dsl_impl` on MLA result rows only when
explicitly set, so legacy rows stay null and remain comparable to
historical baselines.

- Add `is_var_seq` and `cute_dsl_impl` to
`output_column_dict["attention"]` so they are emitted in the benchmark
CSV (empty for rows that do not set them).

The targeted PR#3132 perf case that sets `--mla_is_var_seq false
--mla_cute_dsl_impl modular` lives in the flashinfer-ci testlists, not
here.

- [x] Existing benchmark suite
(`benchmarks/test_flashinfer_benchmark.py`) remains green
(decode/prefill/gemm; not affected by the new MLA-only flags).
- [x] Without the new flags, an existing MLA case produces the same
`median_time` and empty `is_var_seq` / `cute_dsl_impl` CSV columns as
before.
- [x] With `--mla_is_var_seq false --mla_cute_dsl_impl modular`, a
cute-dsl FP8 MLA case runs the modular persistent scheduler on SM100 (cc
10.0 / B200) and records `is_var_seq=False`, `cute_dsl_impl=modular`.

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

* **New Features**
* Added `--mla_is_var_seq` and `--mla_cute_dsl_impl` CLI options to the
attention benchmark to control MLA sequence variability and CuTe
implementation selection.
* Extended benchmark output to report `is_var_seq` and `cute_dsl_impl`
as new columns when those options are explicitly provided, keeping
historical default output unchanged otherwise.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-06-25
**监控日期**: 2026-06-24
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3757
- **最后更新**: 2026-06-24T22:56:44Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Utkarsh Ranjan

## AI分析总结

### 更新总结

**提交范围**：共 1 个提交（b57180b）

---

#### 1. 主要更新类型
- **Bug 修复**：明确标记为 `[bugfix]`，关注用户使用不同注意力后端时的兼容性问题。

#### 2. 关键变更点
- 当用户请求的注意力后端（attention backend）在当前层（layer）不被支持时，不再直接报错或静默忽略，而是**输出警告**（warn），提示用户该请求无法被满足。

#### 3. 对项目的影响与潜在意义
- **提升用户友好性**：在不支持的后端被选中时，用户能立即得到反馈，便于排查配置错误或模型兼容性问题。
- **避免硬中断**：警告而非报错，允许流程继续执行（可能回退到默认后端），增强鲁棒性。
- **优化调试体验**：为开发者或高级用户提供清晰的上下文以供调试注意力后端选择逻辑。

#### 4. 值得关注的技术点
- **注意力后端的动态调度机制**：项目可能支持多种注意力实现（如 FlashAttention、xformers、PyTorch 原生等），不同层（如不同 Transformer 模块）可能因算子支持度不同而限制后端选择。
- **分层兼容性检查**：该提交暗示代码中对“层”级别进行了独立性判断，而非全局统一处理，体现了细粒度的硬件/库适配策略。

#### 5. 结合项目背景（FastVideo 视频加速方向）的影响
- FastVideo 专注于高效视频生成/处理，往往依赖优化的注意力算子来加速扩散模型或 Transformer 推理。此修复确保了**当用户启用特定后端（如 FlashAttention v2）时，项目不会因部分层的兼容问题而意外失败**，从而维持整体加速效果的可靠性。
- 与项目文档中“快速开始”和“开发会议”等强调的用户易用性一致，该提交降低了多后端场景下的使用门槛，有助于吸引更多社区用户尝试不同硬件配置。

**总结**：本次更新属于低风险、高实用性的防御性修复，强化了项目的稳定性与用户反馈透明度，间接支持了 FastVideo 作为通用视频加速框架的兼容性目标。

## 详细提交记录

### [b57180b](https://github.com/hao-ai-lab/FastVideo/commit/b57180bf972139518f5670364d3e887970d29fa4)

- **作者**: Utkarsh Ranjan
- **时间**: 2026-06-24T22:56:39Z
- **提交信息**: [bugfix] Warn when a requested attention backend is unsupported by a layer (#1254) (#1486)

Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-06-25
**监控日期**: 2026-06-24
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 33922
- **最后更新**: 2026-06-24T19:14:26Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Sayak Paul, YiYi Xu

## AI分析总结

### 1. 主要更新类型
- **文档/协定更新**（主要）：完善 `.ai/models.md` 和 `.ai/pipelines.md`，明确贡献者应遵循的编码约定。
- **Bug 修复**（次要）：修复 Claude 代码审查在 PR 中的问题（`eb0a900`）。

---

### 2. 关键变更点及其与项目整体方向的关系
- **新增「单文件模型布局」约定**（`models.md`）：  
  要求每个模型（如 transformer）自包含在一个 `transformer_<name>.py` 中，共享的标准化/注意力/嵌入模块从 `normalization.py` 等公共文件导入，模型特有的变体通过 `# Copied from` 内联，不创建额外的 `attention_processor_<name>.py` 等独立文件。  
  → 与 diffusers **高度模块化、易于扩展** 的方向一致，降低贡献者学习成本，避免文件碎片。

- **新增「不要重实现 DiffusionPipeline」提示**（`pipelines.md`, 编号 #8）：  
  强调子类只应添加 pipeline 特有步骤，设备放置、卸载、执行设备解析、模块注册等均由基类提供，不得在子类编写自定义设备/卸载管理器、`device=` 参数或 `set_<component>` 设置器。  
  → 保障框架的 **统一性与可维护性**，防止贡献者重复造轮子或破坏基类生命周期管理。

---

### 3. 对项目的影响和潜在意义
- **降低代码审查成本**：明确书面约定后，审查者可快速对照检查，减少主观判断分歧。
- **提升代码一致性**：所有新模型/pipeline 将遵循统一风格，便于跨模型比较、调试和自动化工具处理。
- **促进社区贡献**：清晰指南降低新贡献者的心理门槛，尤其对首次提交 pipeline 的用户友好。
- **避免潜在技术债务**：阻止因个人偏好引入的分散文件结构或重复的基类逻辑，长期保持架构清晰。

---

### 4. 值得关注的技术点
- **`# Copied from` 模式的标准化使用**：这是 HuggingFace 生态（如 transformers）常用的复用技巧，此处扩展至 diffusers，暗示未来可能在各模型间大量复制基础块。
- **Pipeline 基类的职责边界**：明确指出子类不应触碰设备/卸载等底层逻辑，说明基类已封装成熟，贡献者应信任其设计。
- **Claude AI 辅助文档生成**：提交中有 `Co-Authored-By: Claude Opus 4.8`，表明 HuggingFace 团队正尝试用 AI 加速贡献文档的编写与审查。

---

### 5. 这些提交如何影响项目发展（结合 README 背景）
鉴于 README 强调 diffusers 是“模块化扩散模型生态”，这些约定进一步强化了 **“框架强约定、贡献者专注核心逻辑”** 的理念。具体影响：
- **推动更多模型/ pipeline 的快速集成**：新模型只需关心自家创新（如 transformer 结构、采样逻辑），无需重新实现基础设施，加速社区模型移植。
- **为自动化审查工具铺路**：明确的文件布局和 API 限制可被 lint 工具或 CI 检查，提升 PR 合并效率。
- **为长期架构演进奠基**：统一的模型布局使得未来在单文件内做优化（如编译器支持、量化解耦）更容易落地，而无需跨文件调整。

## 详细提交记录

### [eb0a900](https://github.com/huggingface/diffusers/commit/eb0a900caac8625dd02d4c403b8e7c3ae12b8733)

- **作者**: Sayak Paul
- **时间**: 2026-06-24T19:02:38Z
- **提交信息**: fix claude code review fix in PRs. (#14058)

### [03040e5](https://github.com/huggingface/diffusers/commit/03040e5152286d16e1ce3e75d988979f720174d7)

- **作者**: YiYi Xu
- **时间**: 2026-06-24T18:23:59Z
- **提交信息**: [.ai] document single-file model layout and "don't reimplement Diffus… (#14048)

* [.ai] document single-file model layout and "don't reimplement DiffusionPipeline"

Two conventions that weren't written down, surfaced while reviewing a new
model/pipeline port:

- models.md: add a "Single-file model layout" section. A model lives in one
  self-contained `transformer_<name>.py`; reuse shared blocks from
  normalization.py/attention.py/embeddings.py and inline model-specific
  variants with `# Copied from` rather than creating per-model
  `attention_processor_<name>.py` / `block_<name>.py` / `rope_<name>.py`
  companion files (no precedent for these in the repo).

- pipelines.md: add gotcha #7, "Don't reimplement DiffusionPipeline." A
  subclass adds only pipeline-specific steps; device placement, offloading,
  execution-device resolution, and module registration already exist on the
  base class. No custom device/offload manager, no `device=` arg on
  `__call__`, no `set_<component>` setters.

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

* [.ai] generalize single-file model layout section

Drop the implementation-specific examples (Lumina class names, per-model
transformer_*.py citations) and state the single-file policy generally:
everything (attention, blocks, RoPE, model-specific layers) in one model
file, with shared blocks either imported from the common modules or brought
in via `# Copied from ... with Old->New`.

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

* [.ai] trim redundant don't-split sentence from single-file section

The positive statement (everything in one model file) already conveys it;
drop the companion-module filename list and the editorializing.

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

* [.ai] generalize the "don't reimplement DiffusionPipeline" gotcha

State the principle and the canonical base APIs; drop the implementation-
specific anti-pattern callouts (enable_*_flag booleans, set_<component>
setters, the device= arg, a shadow self.execution_device).

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

* [.ai] pare gotcha #7 down to the principle

Drop the per-category API bullets; one sentence — don't add device
placement, offloading, or component loading/registration logic on a
subclass, it's on the base class. Can expand later if needed.

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

* [.ai] renumber gotchas after merge: component-mutation #7, reimplement #8

main's newly merged "don't modify registered component on the fly" keeps #7;
our "don't reimplement DiffusionPipeline" becomes #8 (appended after it).

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

* [.ai] add blank line between gotchas 7 and 8

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

* Update .ai/models.md

Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

---------

Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>
Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-06-25
**监控日期**: 2026-06-24
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 417
- **最后更新**: 2026-06-22T04:30:42Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-06-25
**监控日期**: 2026-06-24
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12627
- **最后更新**: 2026-06-24T18:29:04Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Zhongjie Duan

## AI分析总结

根据你提供的仓库摘要和提交记录，以下是对昨日更新（提交 `d799831`）的分析总结：

### 1. 主要更新类型
- **功能新增**：核心是支持 Krea2（新模型/功能）。
- **版本发布**：更新至 `2.0.16`。
- **文档更新**：补充了 Krea2 的相关说明。
- **代码重构/优化**：多次 `refine code`，提升代码质量。

### 2. 关键变更点及其与项目整体方向的关系
- **关键变更**：集成 Krea2（推测为一种图像/视频生成模型或处理管线），并围绕该功能完善了文档和代码。
- **与项目方向的关系**：
  - DiffSynth-Studio 定位于“扩散合成工作室”，核心是提供多种扩散模型（如 Stable Diffusion、视频扩散等）的封装与交互。
  - 支持 Krea2 扩展了模型生态，增强项目的表现力与适用场景，符合“多渠道合成”的目标。

### 3. 对项目的影响和潜在意义
- **直接影响**：用户可直接调用 Krea2 进行生成任务，降低使用门槛。
- **潜在意义**：
  - 吸引原本使用 Krea2 的创作者，增加项目用户基数。
  - 体现项目对前沿模型（如 Krea AI 推出的第二代模型）的快速跟进能力。
  - 版本号跳至 `2.0.16` 表明持续迭代，保持活跃度。

### 4. 值得关注的技术点
- **模型集成方式**：如何将 Krea2 与现有 DiffSynth 管线对接（可能涉及模型加载、推理接口、LoRA 支持等）。
- **版本发布节奏**：单次提交就完成功能新增、文档更新并发布新版本，说明开发流程高效。
- **代码优化细节**：多次 `refine code` 表明在集成过程中有代码重构，可能涉及性能或可维护性改进。

### 5. 结合 README 背景，对项目发展的影响
- 项目已有 PyPI 包、Trendshift 热度、Logo 等成熟社区特征，说明需要持续新增功能以维持竞争力。
- 支持 Krea2 表明项目从“基础扩散模型聚合”向“先进模型快速适配”转型，提升对专业用户的吸引力。
- 作为 ModelScope 旗下项目，该更新也增强了阿里生态内 AI 创作工具的多样性。

## 详细提交记录

### [d799831](https://github.com/modelscope/DiffSynth-Studio/commit/d799831c6046138833bedfb959a22bd16166d4b5)

- **作者**: Zhongjie Duan
- **时间**: 2026-06-24T09:43:56Z
- **提交信息**: Support Krea2 (#1509)

* support Krea-2

* update Krea2 doc

* refine code

* refine code

* update to version 2.0.16

* refine code

* refine code

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-06-25
**监控日期**: 2026-06-24
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 29610
- **最后更新**: 2026-06-24T22:50:13Z

## 提交统计

- **昨日提交总数**: 35
- **提交者数量**: 23
- **主要提交者**: Mick, weireweire, nvjullin

## AI分析总结

根据昨日提交记录，结合SGLang项目定位（高性能LLM推理引擎，支持多硬件、多模态、推测解码、PD分离等），总结如下：

### 1. 主要更新类型
- **性能优化**：约占

## 详细提交记录

### [7e63fee](https://github.com/sgl-project/sglang/commit/7e63feee6f37480b62938e5c002676d777eb4115)

- **作者**: Lianmin Zheng
- **时间**: 2026-06-24T22:50:05Z
- **提交信息**: Add scheduler metrics extension hooks (#29207)

Co-authored-by: Yinghai Lu <yinghai@meta.com>

### [e26bceb](https://github.com/sgl-project/sglang/commit/e26bceb81e0744060434a6986d68b727aa8aa237)

- **作者**: Qiaolin Yu
- **时间**: 2026-06-24T22:45:26Z
- **提交信息**: [perf] simplify _apply_cuda_graph_metadata for draft extend in trtllm_mla backend (#29077)

### [85a3f1f](https://github.com/sgl-project/sglang/commit/85a3f1f75c5dea5571a2c7e8d2c5a32a95d8d422)

- **作者**: Liangsheng Yin
- **时间**: 2026-06-24T22:36:54Z
- **提交信息**: [Spec] Unify the overlap stash relay behind a RelayPayload dataclass (#29124)

### [c6822f8](https://github.com/sgl-project/sglang/commit/c6822f81b11ac5921afdd7df0ede74aa3c1eecd6)

- **作者**: Liangsheng Yin
- **时间**: 2026-06-24T22:34:02Z
- **提交信息**: [Spec] Make the overlap bonus-token relay unconditional (#29122)

### [d3dd184](https://github.com/sgl-project/sglang/commit/d3dd184e3e4f31283337b72cc9b96795a70c22f7)

- **作者**: Liangsheng Yin
- **时间**: 2026-06-24T22:30:29Z
- **提交信息**: [Spec] Fold DFlash verified_id into the shared bonus_tokens relay channel (#29118)

### [3c95a87](https://github.com/sgl-project/sglang/commit/3c95a87b662fd0b97b9ffe8cad3ec93ac3b48eff)

- **作者**: Brayden Zhong
- **时间**: 2026-06-24T22:26:46Z
- **提交信息**: Fix the CuDNN failure on bmm_fp8 when two libcudart.so exists. (#29201)

Co-authored-by: Brayden Zhong <brayden@radixark.ai>

### [5f30fa2](https://github.com/sgl-project/sglang/commit/5f30fa258c6c1a19e6b527510a30ac201cec3ab6)

- **作者**: weireweire
- **时间**: 2026-06-24T22:02:51Z
- **提交信息**: Support DP-aware PD router dispatch (#26245)

Co-authored-by: weireweire <20922698+weireweire@users.noreply.github.com>

### [fd87a85](https://github.com/sgl-project/sglang/commit/fd87a85388878b32117a7040f53ec185c38ddada)

- **作者**: Lianmin Zheng
- **时间**: 2026-06-24T20:42:45Z
- **提交信息**: Convert SamplingParams to msgspec Struct (#29198)

Co-authored-by: Rain Jiang <96632942+rainj-me@users.noreply.github.com>

### [d5e9176](https://github.com/sgl-project/sglang/commit/d5e9176f6581e3c9274dd33a95315033aa194df5)

- **作者**: Kaixi
- **时间**: 2026-06-24T20:13:35Z
- **提交信息**: [BCG][GLM5] perf: BCG support and prefill enhancements (#27053)

### [d46afbf](https://github.com/sgl-project/sglang/commit/d46afbf8b4bbdcfc8771820d7e881856d66ba7c4)

- **作者**: Brayden Zhong
- **时间**: 2026-06-24T19:34:11Z
- **提交信息**: Fix nightly CI test for GLM-4.6 + B200 (#28749)

Co-authored-by: Brayden Zhong <brayden@radixark.ai>

### [c01ad10](https://github.com/sgl-project/sglang/commit/c01ad10d1670f21ef4b544d723596f38bca2104c)

- **作者**: Qiaolin Yu
- **时间**: 2026-06-24T19:27:13Z
- **提交信息**: [perf] tiny optimize select_index op for draft extend (#29078)

### [2c697da](https://github.com/sgl-project/sglang/commit/2c697daf5f922d33e64c80f09ba9bba30a51e436)

- **作者**: Brayden Zhong
- **时间**: 2026-06-24T19:12:34Z
- **提交信息**: [Cookbook] Nemotron3-Ultra: align MTP draft depth with NVIDIA reference (num_steps 5) (#29200)

Co-authored-by: Brayden Zhong <brayden@radixark.ai>

### [e97cc33](https://github.com/sgl-project/sglang/commit/e97cc339e30ce2fcf9d6ea0bf79633c5d28028ce)

- **作者**: Anusha Pant
- **时间**: 2026-06-24T18:42:33Z
- **提交信息**: Add DeepSeek V4 Flash demo notebook (#28952)

### [d5c566e](https://github.com/sgl-project/sglang/commit/d5c566e59b7418f547ab6d1342b71a6e5eb5a7db)

- **作者**: Lianmin Zheng
- **时间**: 2026-06-24T18:22:58Z
- **提交信息**: Extract profile request cleanups (#29098)

### [d6aacd2](https://github.com/sgl-project/sglang/commit/d6aacd2801179054e2ea0d88aa30e6a738a0d5e5)

- **作者**: Lianmin Zheng
- **时间**: 2026-06-24T17:33:52Z
- **提交信息**: Handle input-embed-only batches in eager runner (#29121)

Co-authored-by: Cheng Wan <54331508+ch-wan@users.noreply.github.com>

### [76db6c9](https://github.com/sgl-project/sglang/commit/76db6c9d9e20419bdb57ef04edb9991b8c4f13bb)

- **作者**: cctry
- **时间**: 2026-06-24T17:18:20Z
- **提交信息**: [Refactor] Share CUDA graph memory pool across prefill and decode (#28973)

Co-authored-by: cctry <cctry@fb.com>

### [dd4caf9](https://github.com/sgl-project/sglang/commit/dd4caf945912981c42e57834f320f826b74a9f70)

- **作者**: Yihao Wang
- **时间**: 2026-06-24T16:46:06Z
- **提交信息**: [Docs] fix SGLang-diffusion installation links (#29139)

### [4a4f063](https://github.com/sgl-project/sglang/commit/4a4f063b792b1ed90d2168efe8c595cccbcf8961)

- **作者**: Mick
- **时间**: 2026-06-24T15:54:01Z
- **提交信息**: [diffusion] fix: paint multiview vae must follow unit dtype (#29041)

### [03773ae](https://github.com/sgl-project/sglang/commit/03773ae35b6271f11a2e512d96e57d7de91b1fce)

- **作者**: qiaozp
- **时间**: 2026-06-24T15:13:55Z
- **提交信息**: [HiCache] Add NIXL FILE cache cleaner (#28258)

Co-authored-by: ishandhanani <82981111+ishandhanani@users.noreply.github.com>

### [09b808a](https://github.com/sgl-project/sglang/commit/09b808ab7e7029c089a19b8a8e5ebd848e124425)

- **作者**: Mick
- **时间**: 2026-06-24T12:57:54Z
- **提交信息**: [diffusion] fix: fix Qwen-Image-Layered latent shape (#28832)

### [84a7a84](https://github.com/sgl-project/sglang/commit/84a7a8401842b47b9e372df8136b7b7dc0b7e166)

- **作者**: nvjullin
- **时间**: 2026-06-24T10:11:01Z
- **提交信息**: [PD] Fix data race in NixlKVManager for NIXL backend (#28897)

### [7430c56](https://github.com/sgl-project/sglang/commit/7430c56b20f8845362e00af448f68a7d0a162c65)

- **作者**: hirakunaramuka2
- **时间**: 2026-06-24T09:45:01Z
- **提交信息**: [Misc] Use logger instead of print() in utils/common.py (#29004)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [10e0bcd](https://github.com/sgl-project/sglang/commit/10e0bcd6227bb84a9b824598ed6ee0a9387ac623)

- **作者**: zhaozx-cn
- **时间**: 2026-06-24T09:33:02Z
- **提交信息**: [NPU] fix dcp break (#29140)

### [73d976e](https://github.com/sgl-project/sglang/commit/73d976e375b6f652a0fdd3ec406e6b6e18f42b0c)

- **作者**: amote-i
- **时间**: 2026-06-24T08:47:10Z
- **提交信息**: [NPU] [DOC] Fix TOC of Ascend NPU Docs (#29129)

### [4992f7a](https://github.com/sgl-project/sglang/commit/4992f7a108b3d6f38b43be139ff54f590f260b32)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-06-24T08:43:50Z
- **提交信息**: Fix TRTLLM MHA FP8 KV cache scale handling (#28144)

### [0fc815a](https://github.com/sgl-project/sglang/commit/0fc815aa2c1d13eeffc5f35e8622569fb3e7c546)

- **作者**: Yuhao Yang
- **时间**: 2026-06-24T08:39:44Z
- **提交信息**: [CI] Temporarily disable openbmb MiniCPM tests (#29095)

### [8e1988b](https://github.com/sgl-project/sglang/commit/8e1988b746f7ee3072ea2b0199efb01d8273c2eb)

- **作者**: Liangsheng Yin
- **时间**: 2026-06-24T08:34:02Z
- **提交信息**: [Perf] Overlap result D2H copy with the next forward step (#29075)

### [e04ed05](https://github.com/sgl-project/sglang/commit/e04ed0519385b6779e77573626d2650b8f47420b)

- **作者**: jundu
- **时间**: 2026-06-24T08:18:06Z
- **提交信息**: [CI] reduce CPU CI scope with base-c suite (#28623)

### [4da23fd](https://github.com/sgl-project/sglang/commit/4da23fdc354406de8a9031b4c649b50ca6df655d)

- **作者**: Even Zhou
- **时间**: 2026-06-24T08:06:45Z
- **提交信息**: [NPU] removes deprecated pr testing files (#27859)

### [dd2d919](https://github.com/sgl-project/sglang/commit/dd2d919e21a560c6624666d093c0cfee9638ec11)

- **作者**: zijiexia
- **时间**: 2026-06-24T08:05:06Z
- **提交信息**: [Docs] Fix mem-fraction-static default and document how it is computed (#29135)

Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>

### [39f5de9](https://github.com/sgl-project/sglang/commit/39f5de9ba1b4b53e335c0fb1c7636fcc53fa943e)

- **作者**: Even Zhou
- **时间**: 2026-06-24T07:59:41Z
- **提交信息**: [NPU] bump sgl-kernel-npu to 2026.6.2 (#29101)

### [00eac7e](https://github.com/sgl-project/sglang/commit/00eac7ec9b27c8e1e90616b805684000ceddc8e0)

- **作者**: Tai An
- **时间**: 2026-06-24T07:58:44Z
- **提交信息**: [diffusion] fix: disable proxy env in warmup health probe (#28503)

### [a707b20](https://github.com/sgl-project/sglang/commit/a707b2054db7bb8b07a3128a55cd4857b20bb404)

- **作者**: zijiexia
- **时间**: 2026-06-24T07:56:52Z
- **提交信息**: [CI] Fix pre-commit failures in MLX backend tests (#29141)

Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>

### [5f76736](https://github.com/sgl-project/sglang/commit/5f767364279ccc483aceaee1c5fce9c0fbbdf7f3)

- **作者**: Rohit Harkhani
- **时间**: 2026-06-24T07:53:22Z
- **提交信息**: kimik2_detector fix the normal text detection before tool call.  (#25071)

Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>
Co-authored-by: Rohit Harkhani <rharkhani@gmail.com>

### [b6a8000](https://github.com/sgl-project/sglang/commit/b6a8000473052dac2504439a9ddd58e092c0c283)

- **作者**: weibingo
- **时间**: 2026-06-24T07:13:48Z
- **提交信息**: [bugfix][decode hicache] _storage_hit_query use HybridPrefetchOperation (#28422)

Co-authored-by: Zhangheng <hzh0425@apache.org>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-06-25
**监控日期**: 2026-06-24
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1209
- **最后更新**: 2026-06-24T07:26:28Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-06-25
**监控日期**: 2026-06-24
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 84055
- **最后更新**: 2026-06-24T23:34:44Z

## 提交统计

- **昨日提交总数**: 45
- **提交者数量**: 39
- **主要提交者**: Ronen Schaffer, Fadi Arafeh, Kunshang Ji

## AI分析总结

好的，以下是对 vllm-project/vllm 仓库昨日（基于提交记录）更新的分析总结。

---

### 1. 主要更新类型概览

| 类型 | 提交数量 | 关键示例 |
|------|----------|----------|
| **Bug修复** | ~15个

## 详细提交记录

### [fc7fc42](https://github.com/vllm-project/vllm/commit/fc7fc421e98863c4ffb1aa02d46bd6e4d0202c26)

- **作者**: Kaihang Jiang
- **时间**: 2026-06-24T23:32:50Z
- **提交信息**: [Kernel][MoE] Allow FlashInfer MXINT4 MoE for gated SiLU (#46518)

Signed-off-by: Kaihang Jiang <kaihangj@nvidia.com>

### [e06a834](https://github.com/vllm-project/vllm/commit/e06a83445c0be30b0dc874dccb059c3e0d8dea5e)

- **作者**: cyq
- **时间**: 2026-06-24T23:22:49Z
- **提交信息**: [Bugfix] Normalize slashes in Helion GPU names (#46101)

Signed-off-by: cyq <15000851237@163.com>

### [d7ab9be](https://github.com/vllm-project/vllm/commit/d7ab9be775526cca1042009e3754f8a4ef14b56c)

- **作者**: Woosuk Kwon
- **时间**: 2026-06-24T20:59:42Z
- **提交信息**: [Bugfix] Support -1 (invalid/non-local) slots in topk_ids for Triton MoE (#46408)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: Claude <noreply@anthropic.com>

### [6a15707](https://github.com/vllm-project/vllm/commit/6a1570711c9ab6dd356f68f5728b845711901e45)

- **作者**: Woosuk Kwon
- **时间**: 2026-06-24T20:52:09Z
- **提交信息**: [Bugfix] Support non-power-of-2 top_k in legacy triton_kernels routing (#46406)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: Claude <noreply@anthropic.com>

### [d6696e2](https://github.com/vllm-project/vllm/commit/d6696e2385ccf6b058885e7ea422c088d7112b15)

- **作者**: Micah Williamson
- **时间**: 2026-06-24T20:40:28Z
- **提交信息**: [ROCm] Begin Deprecation Window for CUDA_VISIBLE_DEVICES on ROCm (#46636)

Signed-off-by: Micah Williamson <micah.williamson@amd.com>

### [84c2f9f](https://github.com/vllm-project/vllm/commit/84c2f9f0fb3f12b79e68d20b62ff7ec154dc860e)

- **作者**: Chauncey
- **时间**: 2026-06-24T19:59:40Z
- **提交信息**: [Frontend] Fix Kimi K2 tool call IDs for required tool choice (#46344)

Signed-off-by: chaunceyjiang <chaunceyjiang@gmail.com>

### [49f2104](https://github.com/vllm-project/vllm/commit/49f2104c53c910033aae05524af120e7c39c5c48)

- **作者**: shivampr
- **时间**: 2026-06-24T19:28:17Z
- **提交信息**: [Feature] Support DCP with FP8 KV cache in MLA decode path (#44044)

Signed-off-by: shivampr <shivampr.dev@gmail.com>
Signed-off-by: Shivam <shivamprasad91@gmail.com>
Co-authored-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [d511b5b](https://github.com/vllm-project/vllm/commit/d511b5bae91423c212457d37936813efeb2646dc)

- **作者**: Ashwin Phadke
- **时间**: 2026-06-24T18:58:24Z
- **提交信息**: Chore: Fix minor doc sentence, grammar, quote errors (#40469)

Signed-off-by: Ashwin Phadke <23502062+ashwin-phadke@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [3c43237](https://github.com/vllm-project/vllm/commit/3c43237233a8f753a0ed24d95c0978b09f009d29)

- **作者**: JessieWei
- **时间**: 2026-06-24T18:00:57Z
- **提交信息**: [Bugfix][Model Runner V2][Spec Decode] Fix int32 offset overflow in sampler kernels (#46560)

Signed-off-by: xiaojun.wei <jessiewei747@gmail.com>
Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>
Co-authored-by: Robert Shaw <114415538+robertgshaw2-redhat@users.noreply.github.com>

### [56ca599](https://github.com/vllm-project/vllm/commit/56ca5997eac9a6c69c7af482c18ced4c184f35dc)

- **作者**: HDCharles
- **时间**: 2026-06-24T17:53:54Z
- **提交信息**: Humming support for 2/3/5/6/7-bit pack-quantized weight-only inference (#46389)

Signed-off-by: HDCharles <charlesdavidhernandez@gmail.com>
Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>

### [cf57311](https://github.com/vllm-project/vllm/commit/cf5731118756858337689d1980ca898f3b9d5936)

- **作者**: Aarushi Jain
- **时间**: 2026-06-24T17:25:57Z
- **提交信息**: Run DeepSeek-V2-Lite prefetch-offload eval eager on ROCm (#46386)

Signed-off-by: aarushjain29 <Aarushi.Jain2@amd.com>

### [e7df232](https://github.com/vllm-project/vllm/commit/e7df23228895c32982856051aeb50a89acb5d8c8)

- **作者**: Lucas Wilkinson
- **时间**: 2026-06-24T15:55:30Z
- **提交信息**: [KV Offload] Gate packed HMA KV cache on cross-layer config (#46252)

Signed-off-by: Lucas Wilkinson <lwilkins@redhat.com>

### [b3a688c](https://github.com/vllm-project/vllm/commit/b3a688cb9eb72172259fa4719dbc86c77fd40c04)

- **作者**: Micah Williamson
- **时间**: 2026-06-24T15:53:21Z
- **提交信息**: [ROCm] Fix OOB During Model Warmup With `ROCM_ATTN` and MRV2 (#46548)

Signed-off-by: Micah Williamson <micah.williamson@amd.com>
Signed-off-by: Matthew Wong <Matthew.Wong2@amd.com>
Co-authored-by: Matthew Wong <Matthew.Wong2@amd.com>

### [1cd3e0e](https://github.com/vllm-project/vllm/commit/1cd3e0e945c9216819ad816969b6ca1be71e637d)

- **作者**: Wentao Ye
- **时间**: 2026-06-24T15:14:17Z
- **提交信息**: [Bug] Fix `IndentationError: expected an indented block after 'with' statement` (#46627)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [f889325](https://github.com/vllm-project/vllm/commit/f889325c511b9e647f432a5838e82ca1494f7ac9)

- **作者**: Yiwei Hu
- **时间**: 2026-06-24T15:13:27Z
- **提交信息**: [KV Offload] Use background thread for mmap / cpu_tensors pinning (#45850)

Signed-off-by: Sorryhorizon <arikara6666@gmail.com>

### [bb61177](https://github.com/vllm-project/vllm/commit/bb61177e49dd781645b39a99bb2abdb9d37552cd)

- **作者**: Ronen Schaffer
- **时间**: 2026-06-24T15:06:08Z
- **提交信息**: [KV Offloading] Replace `bool|None` lookup return with LookupResult enum (#46363)

Signed-off-by: Ronen Schaffer <ronen.schaffer@ibm.com>
Co-authored-by: Or Ozeri <oro@il.ibm.com>

### [7f99e80](https://github.com/vllm-project/vllm/commit/7f99e80c3b69e11bb3a257a90aacbb2af182816c)

- **作者**: Walter Beller-Morales
- **时间**: 2026-06-24T15:02:25Z
- **提交信息**: [Perf][ThinkingBudget] reduce search space for thinking tokens (#46425)

Signed-off-by: walterbm <walter.beller.morales@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [2801b11](https://github.com/vllm-project/vllm/commit/2801b11156402ac4f3abb6c26ccbadf3cc502e58)

- **作者**: Liangliang Ma
- **时间**: 2026-06-24T14:56:21Z
- **提交信息**: [Test] Pin block_size in auto-fit max_model_len test (#45914)

Signed-off-by: Ma, Liangliang <liangliang.ma@intel.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [007b5a5](https://github.com/vllm-project/vllm/commit/007b5a52edf8e81a018be1df35164f98b730db9f)

- **作者**: Wentao Ye
- **时间**: 2026-06-24T14:45:16Z
- **提交信息**: [Log] Update to log once  (#46511)

Signed-off-by: yewentao256 <zhyanwentao@126.com>
Co-authored-by: TJian <tunjian.tan@embeddedllm.com>

### [24d5186](https://github.com/vllm-project/vllm/commit/24d5186138448a4b484bbbb387fe2541eed89b72)

- **作者**: Cyrus Leung
- **时间**: 2026-06-24T14:35:46Z
- **提交信息**: [Bugfix] Re-enable FP8 MoE on NVIDIA Thor (#46339)

Signed-off-by: DarkLight1337 <tlleungac@connect.ust.hk>

### [7dc0360](https://github.com/vllm-project/vllm/commit/7dc036058b73b0efb75465e1e0815486d7b532fc)

- **作者**: Nemani Harsha Vardhan
- **时间**: 2026-06-24T14:35:08Z
- **提交信息**: [Doc] Document Qwen3.6 (dense + MoE) ViT CUDA graph support (#44720)

Signed-off-by: harsha20032020 <nhvardhan2020@gmail.com>

### [61ee183](https://github.com/vllm-project/vllm/commit/61ee183d28ff3dbd169b61e0205e693a2314337f)

- **作者**: djramic
- **时间**: 2026-06-24T14:29:19Z
- **提交信息**: [ROCm] Fix AITER FP8 quantization schema tests (#46414)

Signed-off-by: Djordje Ramic <djoramic@amd.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [84c62e1](https://github.com/vllm-project/vllm/commit/84c62e1cbdef4250fbfda83782fd250e07ad0256)

- **作者**: Nick Hill
- **时间**: 2026-06-24T14:18:56Z
- **提交信息**: [Model Runner V2][MM] Support EVS (#46535)

Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [061043e](https://github.com/vllm-project/vllm/commit/061043eacac0473769d86a1babb9adeb8402e833)

- **作者**: Fadi Arafeh
- **时间**: 2026-06-24T14:14:35Z
- **提交信息**: [CPU][Perf] Accelerate unquantized MoE for AArch64 (#46353)

Signed-off-by: Fadi Arafeh <fadi.arafeh@arm.com>

### [93ec645](https://github.com/vllm-project/vllm/commit/93ec6458781b50a89f967126419312388c5505a3)

- **作者**: meihanc
- **时间**: 2026-06-24T14:12:23Z
- **提交信息**: [Bugfix] Fix illegal memory access from a forward during a partial wake_up (#44483)

Signed-off-by: Meihan-chen <zr010426ztt@outlook.com>
Signed-off-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: Nick Hill <nickhill123@gmail.com>

### [563c628](https://github.com/vllm-project/vllm/commit/563c628968c07e388fd78c4fa5dc9336a0fd8c97)

- **作者**: Kunshang Ji
- **时间**: 2026-06-24T14:05:31Z
- **提交信息**: [XPU] bump up vllm_xpu_kernels to v0.1.10.1 (#46607)

Signed-off-by: Kunshang Ji <kunshang.ji@intel.com>

### [0bc479e](https://github.com/vllm-project/vllm/commit/0bc479e6eb2b9fcdd27bb28a7ce09b88347949f1)

- **作者**: Lynn
- **时间**: 2026-06-24T13:41:46Z
- **提交信息**: [Perf][LoRA] Replace O(n) list.index() with a dict in convert_mapping (#46542)

Signed-off-by: Lynn <lynnhe02@gmail.com>
Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [62890e2](https://github.com/vllm-project/vllm/commit/62890e204c2096c7627da00aadaf30adeed83bff)

- **作者**: Tae Jeong
- **时间**: 2026-06-24T13:14:13Z
- **提交信息**: Fix duplicated logging when loading a corrupt or partial video (#46467)

Signed-off-by: hhhhhhhhhhhhhhhhho <man2719@naver.com>

### [a2cb08b](https://github.com/vllm-project/vllm/commit/a2cb08b3d50ecbe3dbc18227aaa774f9b309683e)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-06-24T13:14:05Z
- **提交信息**: [Misc][PD] Disable bidirectional xfer mode for NixlPushConnector (#46473)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [cf9fd64](https://github.com/vllm-project/vllm/commit/cf9fd6457eb7bc18942bf242365a3aa7d6f49ad8)

- **作者**: Rui Yin
- **时间**: 2026-06-24T12:42:40Z
- **提交信息**: Fix KV offload request-finished lifecycle contract (#46284)

Signed-off-by: test test <2260891073@qq.com>
Signed-off-by: Rui Yin <2260891073@qq.com>
Co-authored-by: Or Ozeri <oro@il.ibm.com>

### [d4448b5](https://github.com/vllm-project/vllm/commit/d4448b511d75449cc5ee4c3f292f685209e8b777)

- **作者**: Kunshang Ji
- **时间**: 2026-06-24T12:39:20Z
- **提交信息**: [XPU][Docker] switch to ubuntu 24.04 as base image (#45973)

Signed-off-by: Kunshang Ji <kunshang.ji@intel.com>

### [f1a6703](https://github.com/vllm-project/vllm/commit/f1a6703edd9f0e99743549408a323a3bd6e49085)

- **作者**: Ting SUN
- **时间**: 2026-06-24T12:25:50Z
- **提交信息**: [Bugfix][Config] Keep pydantic validation for fields with a TYPE_CHECKING Literal alias (#46220)

Signed-off-by: Ting Sun <suntcrick@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [160c80a](https://github.com/vllm-project/vllm/commit/160c80a34ca2f94ca22886ec807e66d875d27b66)

- **作者**: Roy Wang
- **时间**: 2026-06-24T12:15:31Z
- **提交信息**: [Rust Frontend] Raise frontend JSON body limit (#46582)

Signed-off-by: esmeetu <jasonailu87@gmail.com>

### [f237e16](https://github.com/vllm-project/vllm/commit/f237e16b41bb444b3c9994260a36f9c2388bd019)

- **作者**: Martin Hickey
- **时间**: 2026-06-24T11:44:24Z
- **提交信息**: [KV Offload] Replace OffloadingHandler with OffloadingWorker (#45053)

Signed-off-by: Martin Hickey <martin.hickey@ie.ibm.com>

### [70749fd](https://github.com/vllm-project/vllm/commit/70749fdcca7da31be7206101e6f6fc77de9e6839)

- **作者**: JartX
- **时间**: 2026-06-24T10:21:25Z
- **提交信息**: [Feature] Triton INT4 per-token-head KV cache quantization (#40835)

Signed-off-by: JartX <sagformas@epdcenter.es>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [d20dbf9](https://github.com/vllm-project/vllm/commit/d20dbf921b9074c68cd36181cbd961fb46c62caf)

- **作者**: Wei Zhao
- **时间**: 2026-06-24T10:10:50Z
- **提交信息**: [Mooncake] Only check and store new KV cache range (#46412)

Signed-off-by: wzhao18 <wzhao18.sz@gmail.com>
Signed-off-by: Yifan Qiao <yifanqiao@inferact.ai>
Co-authored-by: Yifan Qiao <yifanqiao@inferact.ai>

### [ede54b9](https://github.com/vllm-project/vllm/commit/ede54b926ebeb1bbb2d2f622599157d868daf803)

- **作者**: Xinyu Chen
- **时间**: 2026-06-24T10:05:02Z
- **提交信息**: set AttentionCGSupport.UNIFORM_BATCH for fa2 on xpu (#46555)

Signed-off-by: Xinyu Chen <xinyu1.chen@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [52fbe12](https://github.com/vllm-project/vllm/commit/52fbe12283f030c6bbfeb835bab634cbf2be045e)

- **作者**: Lynn
- **时间**: 2026-06-24T09:38:27Z
- **提交信息**: [Perf][Multimodal] Avoid building a full timestamps list in video frame sampling (#46543)

Signed-off-by: Lynn <lynnhe02@gmail.com>
Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [dc0d318](https://github.com/vllm-project/vllm/commit/dc0d318177e1086d483bff12ad71f1d3b5b980e7)

- **作者**: Dakai An
- **时间**: 2026-06-24T09:33:10Z
- **提交信息**: [Attention] Add FLASH_ATTN_MLA_SPARSE backend for Hopper sparse MLA (#46189)

Signed-off-by: Dakai An <dakaian108@gmail.com>

### [d7c1821](https://github.com/vllm-project/vllm/commit/d7c1821b5a31c886cf130e50f353e49af5b79659)

- **作者**: soaringk
- **时间**: 2026-06-24T08:23:03Z
- **提交信息**: [Model][MiniMax-M3] Add pipeline parallelism support (#45810)

Signed-off-by: soaringk <k3vin.zhang@gmail.com>

### [4cd1a84](https://github.com/vllm-project/vllm/commit/4cd1a84c88895ed863d1e74ed413fcb159e53aec)

- **作者**: Tiezhen WANG
- **时间**: 2026-06-24T08:13:57Z
- **提交信息**: [Model] Remove BaiChuanForCausalLM and BaichuanForCausalLM (#46362)

Signed-off-by: Xianbao QIAN <xianbao.qian@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [191826e](https://github.com/vllm-project/vllm/commit/191826ec612dc6648b176ed4e94c3e6e551e9c09)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-06-24T07:51:11Z
- **提交信息**: [CI/Build] Fix topk histogram build on SM75 (#46550)

Signed-off-by: Mohammad Miadh Angkad <176301910+mmangkad@users.noreply.github.com>

### [549c707](https://github.com/vllm-project/vllm/commit/549c7074cd7e8f7ca0914f277be5e7a6c3e9a1cf)

- **作者**: Andreas Karatzas
- **时间**: 2026-06-24T07:31:33Z
- **提交信息**: [ROCm][CI] Skip the MoE Marlin tile-padding helper assertion (#46580)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [489abad](https://github.com/vllm-project/vllm/commit/489abadfb808e1255577f4fb51b6092ec8ca771f)

- **作者**: hurukawa
- **时间**: 2026-06-24T07:08:13Z
- **提交信息**: feat: support to OpenMOSS-Team (#44124)

Signed-off-by: nagisa-kun <1434936049@qq.com>
Signed-off-by: nagisa19 <1434936049@qq.com>
Signed-off-by: nagisa <1434936049@qq.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: Roger Wang <hey@rogerw.io>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [96de8bb](https://github.com/vllm-project/vllm/commit/96de8bb389ae2c32d5fb6ab42c430423efeb9486)

- **作者**: Woosuk Kwon
- **时间**: 2026-06-24T07:06:41Z
- **提交信息**: [MoE] Free unused MXFP4 scales in OAI Triton Backend (#46549)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-06-25
**监控日期**: 2026-06-24
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 5261
- **最后更新**: 2026-06-24T22:28:31Z

## 提交统计

- **昨日提交总数**: 5
- **提交者数量**: 5
- **主要提交者**: Zeng Chuang, rein yang, Nick Cao

## AI分析总结

根据仓库 `vllm-project/vllm-omni` 的提交记录，结合README中“Easy, fast, and cheap omni-modality model serving for everyone”的目标，昨日更新总结如下：

---

### 1. 主要更新类型
- **Bug修复**：2项（SSRF防护、TTS自定义语音模式）
- **功能新增**：1项（流式CoT显示）
- **重构**：2项（示例迁移、参数扁平化）

---

### 2. 关键变更点及与项目整体方向的关系
| 提交 | 变更内容 | 关联项目方向 |
|------|----------|--------------|
| d8edf0c | 使用`MediaConnector`获取图片/视频URL，防止SSRF攻击 | **安全加固**：保障多模态输入（图片/视频）的网络安全，降低服务端风险 |
| 67bd02f | 为HunyuanImage-3.0 AR生成启用流式CoT（Chain-of-Thought）显示 | **多模态增强**：提升图像生成过程的透明度和交互体验，支持流式推理 |
| 0814d84 | 将VACE示例迁移至标准task examples + `model_extras` | **开发体验优化**：统一示例和扩展机制，降低集成门槛，符合“Easy”目标 |
| bb973cb | 修正qwen3-tts自定义语音模式下的aura结果 | **多模态修复**：修复TTS（语音合成）模块中的特定问题，提升语音服务可靠性 |
| fb3abb3 | 扁平化Ming-flash-omni-2.0 imagegen参数 | **易用性提升**：简化API参数结构，使图像生成配置更直观，匹配“Cheap（低成本使用）” |

---

### 3. 对项目的影响和潜在意义
- **安全性提升**：SSRF防护是基础安全改进，避免通过URL注入攻击内部网络，对生产环境部署至关重要。
- **功能扩展**：流式CoT显示使HunyuanImage-3.0的图像生成过程可观察，可应用于调试、用户交互场景。
- **标准化推进**：将VACE示例迁移至标准框架，降低新增模型或任务时的重复工作，促进社区贡献。
- **稳定性增强**：修复TTS模块的特定bug，尤其针对自定义语音场景，提升了多模态服务的质量一致性。
- **易用性改进**：参数扁平化降低了用户理解成本，与其他模型API风格更统一，有助于快速上手。

---

### 4. 值得关注的技术点
- **MediaConnector**：作为抽象层统一处理多种媒体资源获取，同时内置安全策略，防止SSRF。后续可能扩展支持更多协议或缓存机制。
- **流式CoT显示**：图像生成中的CoT机制类似LLM的思维链，可公开生成步骤，为可解释AI和多模态推理提供示范。
- **model_extras机制**：重构引入`model_extras`目录，允许模型特定代码（如VACE）独立于核心流水线，便于维护和模块化扩展。
- **参数扁平化**：将嵌套参数展平为顶层args，减少配置复杂度，体现了对API设计简洁性的追求。

---

### 5. 对项目发展的影响（结合README背景）
- **推动“Omni-Modality”覆盖**：图像生成流式显示、TTS修复、图片/视频安全处理，直接增强了项目对图像、视频、语音的多模态支持。
- **追求“Easy & Cheap”**：参数扁平化、示例标准化降低了使用和开发成本，符合“便宜、易用”的定位。
- **吸纳社区贡献**：多个提交来自外部开发者（如Red Hat、华为），表明项目社区活跃，持续接收安全、功能类PR，加速生态建设。
- **为未来扩展铺路**：MediaConnector和model_extras作为基础架构改进，为后续集成更多模型（如多模态生成、理解）奠定稳健基础。

总体而言，昨日的更新在安全、功能、开发体验三个维度同步推进，强化了vllm-omni作为多模态服务引擎的可靠性和易用性。

## 详细提交记录

### [d8edf0c](https://github.com/vllm-project/vllm-omni/commit/d8edf0c9d516268917cc84e21ac561264a4cc093)

- **作者**: Nick Cao
- **时间**: 2026-06-24T22:28:26Z
- **提交信息**: [Bugfix] Use MediaConnector for image/video URL fetching to prevent SSRF (#2565)

Signed-off-by: Nick Cao <ncao@redhat.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [67bd02f](https://github.com/vllm-project/vllm-omni/commit/67bd02f76782e75680e12d37a2241dc030ec3004)

- **作者**: Zeng Chuang
- **时间**: 2026-06-24T14:08:30Z
- **提交信息**: [Feat] Enable streaming CoT display for HunyuanImage-3.0 AR generation (#4148)

Signed-off-by: zengchuang <zengchuang3@huawei.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [0814d84](https://github.com/vllm-project/vllm-omni/commit/0814d845dcaa81c679224cfadac0f9458066eca9)

- **作者**: Zhisen Zhang
- **时间**: 2026-06-24T13:54:36Z
- **提交信息**: [Refactor] Migrate VACE example to standard task examples + model_extras (#4648)

Signed-off-by: ForestWisdom <zszhang01@gmail.com>

### [bb973cb](https://github.com/vllm-project/vllm-omni/commit/bb973cb10cb81fa51712be43bac752567ecb8569)

- **作者**: rein yang
- **时间**: 2026-06-24T09:29:48Z
- **提交信息**: [Bugfix] [AURA] Correct aura results when use qwen3-tts in custom voice mode (#4650)

Signed-off-by: R2-Y <ruiruyang2@gmail.com>

### [fb3abb3](https://github.com/vllm-project/vllm-omni/commit/fb3abb38fb1916d0a963fe736b22285a7a508b48)

- **作者**: Yuanheng Zhao
- **时间**: 2026-06-24T09:01:58Z
- **提交信息**: [refactor] Flatten Ming-flash-omni-2.0 imagegen args (#4587)

Signed-off-by: Yuanheng <jonathan.zhaoyh@gmail.com>

---
