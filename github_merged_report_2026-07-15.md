# GitHub Stars 合并报告 - 2026-07-15

**合并日期**: 2026-07-16
**监控日期**: 2026-07-15
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


**报告日期**: 2026-07-16
**监控日期**: 2026-07-15
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2088
- **最后更新**: 2026-07-15T20:00:45Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 2
- **主要提交者**: Wenzhe_Wang, Coach257

## AI分析总结

### 昨日更新要点总结

#### 1. 主要更新类型
- **功能新增**（2项）：`packed ChunkMBS` 支持、`per-module local parallel state` 机制
- **文档更新**（1项）：同步文档与主分支
- **破坏性变更**：其中 `per-module local parallel state` 标记为 `BREAKING`

#### 2. 关键变更点及其与项目方向的关系
- **`packed ChunkMBS`（提交 1）**  
  - 新增对打包式分块微批次（Chunked Micro Batch Size）的支持  
  - 与项目“Scaling Any Modality Model Training”目标紧密相关：通过更灵活的微批量管理，提升内存效率和训练吞吐量，适配不同模态模型的大小差异。

- **`per-module local parallel state via context manager`（提交 3）**  
  - 通过上下文管理器（`context manager`）为每个模型模块独立管理局部并行状态  
  - 直接契合项目“Model-Centric Distributed Recipe Zoo”理念：允许用户为不同模块（如注意力层、FFN层）定制不同的并行策略（如数据并行、张量并行、序列并行等），实现精细化的分布式配方编排。

- **文档同步（提交 2）**  
  - 将文档更新至与主分支一致，确保用户可准确了解最新功能，属于常规维护。

#### 3. 对项目的影响和潜在意义
- **灵活性大幅提升**：`per-module local parallel state` 标志着从全局并行配置向局部、模块化并行控制的转变，用户可针对模型不同部分进行差异化优化，降低瓶颈。
- **内存与性能优化**：`packed ChunkMBS` 有助于减小微批次内存碎片，尤其在大规模训练或长序列场景下，可能显著提高内存利用率。
- **兼容性提醒**：`BREAKING` 标注意味着用户需升级训练脚本（如替换并行状态设置或上下文管理器用法），短期可能带来迁移成本，但长期收益更高。

#### 4. 值得关注的技术点
- **上下文管理器模式**：`with per_module_parallel_state(module, strategy):` 可能成为后续配置并行策略的标准接口，需学习其使用方式。
- **ChunkMBS 实现细节**：关注其如何与现有数据加载、梯度累积、流水线并行等机制交互，以及是否支持自动打包或需手动指定。
- **模块级并行状态的生命周期**：如何在不同训练阶段（前向、反向、优化器更新）保证状态切换正确性。

#### 5. 结合 README 背景的项目发展影响
- **强化“Recipe Zoo”价值**：`per-module` 特性使得可配置的并行“配方”颗粒度更细，用户可以像组装积木一样为每个模块选择最佳分布式策略，丰富配方库。
- **推进多模态泛化**：不同模态模型（视觉、语音、文本）内部结构差异大，模块级并行可让 VeOmni 更灵活地适配 Transformer、混合专家（MoE）、

## 详细提交记录

### [af327de](https://github.com/ByteDance-Seed/VeOmni/commit/af327de1947ad71187aeb6f7e2e711df81c40416)

- **作者**: Wenzhe_Wang
- **时间**: 2026-07-15T20:00:27Z
- **提交信息**: [dist, trainer, config, docs, ci, task] feat: add packed ChunkMBS support (#898)

### [f413895](https://github.com/ByteDance-Seed/VeOmni/commit/f413895a2a0354102564ce4eedb9ddd45ee97a73)

- **作者**: Wenzhe_Wang
- **时间**: 2026-07-15T18:47:25Z
- **提交信息**: [agent, config, docs] fix: sync documentation with main (#914)

### [0b2096d](https://github.com/ByteDance-Seed/VeOmni/commit/0b2096d963d81802ae4be1f8aaa162bb4f8c117c)

- **作者**: Coach257
- **时间**: 2026-07-15T10:59:32Z
- **提交信息**: [BREAKING][dist, trainer] feat: per-module local parallel state via context manager (#893)

Co-authored-by: Cursor <cursoragent@cursor.com>

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-07-16
**监控日期**: 2026-07-15
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2499
- **最后更新**: 2026-07-15T12:22:26Z

## 提交统计

- **昨日提交总数**: 5
- **提交者数量**: 4
- **主要提交者**: Bilang ZHANG, Yang Yong (雍洋), Shiqiao Gu (谷石桥)

## AI分析总结

### 昨日更新要点总结

#### 1. 主要更新类型
- **功能新增**：编译支持、添加序列并行（sp）、预热支持
- **性能优化**：预热机制更新、模型并行策略引入
- **重构**：训练数据类统一、新增模型支持

#### 2. 关键变更点及与项目方向的关系
- **编译支持 Wan2.1/2.2 完整模型变体（i2v/t2v）**（#1255）  
  扩展了框架支持的模型范围，契合“轻量视频生成推理”目标，覆盖更多主流视频生成任务（图生视频、文生视频）。
- **Wan2.2 MoE 模型预热**（#1254）  
  预热机制是推理优化关键，MoE（混合专家）版本需要额外初始化，该更新降低了首次推理延迟，提升了用户体验。
- **添加 Wan22 Extreme 的 sp（序列并行）**（#1252）  
  引入序列并行技术，可加速长视频生成或高分辨率场景，提升框架在高负载下的吞吐能力。
- **更新 Wan 预热逻辑**（#1253）  
  修复或优化预热流程，可能解决之前存在的兼容性或效率问题。
- **重构训练数据类，增加 LTX2 支持**（#1244）  
  统一数据类结构，降低维护成本；新增 LTX2 模型支持（推测为 Long-term eXtension 变体），拓展框架在长视频生成领域的应用。

#### 3. 对项目的影响和潜在意义
- **模型生态扩展**：Wan 系列从早期版本延伸至 2.1/2.2 及 Extreme，覆盖更多用户场景。
- **推理性能提升**：预热优化和序列并行引入，直接改善推理延迟和吞吐，符合“轻量”定位。
- **训练基础设施改进**：数据重构便于后续新增模型，提升团队开发效率，间接加速项目迭代。

#### 4. 值得关注的技术点
- **编译支持**：表明框架可能采用 JIT 编译（如 FlashAttention 内核）来优化模型运行速度。
- **MoE 预热**：MoE 模型有多个专家，预热需要正确加载路由权重，该提交可能包含缓存机制。
- **序列并行（sp）**：常用于大模型推理时切片计算，需关注其对显存和通信开销的权衡。
- **LTX2 模型**：可能是框架内部对长视频生成任务的特殊优化，值得进一步查看实现细节。

#### 5. 结合项目背景，这些提交如何影响项目发展
LightX2V 定位为 **轻量视频生成推理框架**，核心优势在于快速部署和高效推理。昨日更新：
- **拓宽模型支持**，吸引更多使用 Wan 系列生成视频的用户。
- **优化推理性能**，强化“轻量”核心竞争力，尤其在大分辨率或生成长视频场景中。
- **重构训练

## 详细提交记录

### [a2e4753](https://github.com/ModelTC/LightX2V/commit/a2e475323f2fed64e786c032cf6bff1e6a21a336)

- **作者**: Bilang ZHANG
- **时间**: 2026-07-15T12:22:04Z
- **提交信息**: compile:wan2.1 i2v t2v  wan2.2 t2v i2v (#1255)

### [1046d5f](https://github.com/ModelTC/LightX2V/commit/1046d5fb0607c5ff9394d4c57d8f0a6d8d52a4c4)

- **作者**: Bilang ZHANG
- **时间**: 2026-07-15T12:08:05Z
- **提交信息**: warmup: wan2.2 moe i2v t2v (#1254)

### [90bb178](https://github.com/ModelTC/LightX2V/commit/90bb178c16fe5c9f272178d393631cd0b076bd78)

- **作者**: Shiqiao Gu (谷石桥)
- **时间**: 2026-07-15T10:44:47Z
- **提交信息**: refactor(train): unify data classes and add LTX2 support (#1244)

### [7ff9a7c](https://github.com/ModelTC/LightX2V/commit/7ff9a7cd03778fe8c93027aad55b62425e9e10c0)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-07-15T08:38:16Z
- **提交信息**: update wan warmup (#1253)

### [a3bb254](https://github.com/ModelTC/LightX2V/commit/a3bb254f4d14b1536a78f2b4efb2354d37c39df8)

- **作者**: Chengtao Lv
- **时间**: 2026-07-15T08:28:10Z
- **提交信息**: add sp for wan22 extreme (#1252)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-07-16
**监控日期**: 2026-07-15
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2171
- **最后更新**: 2026-07-15T07:12:20Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-07-16
**监控日期**: 2026-07-15
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5962
- **最后更新**: 2026-07-15T23:11:57Z

## 提交统计

- **昨日提交总数**: 9
- **提交者数量**: 8
- **主要提交者**: Lain, kangbintNV, Yang Xu

## AI分析总结

## 昨日更新要点总结

### 1. 主要更新类型
- **功能新增**（3项）：MiniMax稀疏注意力(MSA)支持、CuTe-DSL JIT磁盘缓存、MXFP4×FP8 MoE后端
- **Bug修复**（4项）：MoE 2CTA挂起、cuDNN批预填充测试、CuTe-DSL API兼容性、测试架构验证
- **性能优化**（2项）：MXFP4×BF16/INT4×FP8路径优化、JIT缓存减少重复编译
- **文档更新**（2项）：补充缺失API引用、添加fused_moe LoRA delta文档
- **重构**（1项）：JitSpec抽象基类设计

### 2. 关键变更点与项目关系
- **MSA支持**：将MiniMax稀疏注意力移植到消费级Blackwell (SM120/121)，符合项目"高性能推理内核"定位，扩展了在新型attention模式上的支持
- **JIT磁盘缓存**：CuTe-DSL内核从进程内记忆化升级为磁盘持久缓存，解决了多进程重复编译问题，提升了生产部署实用性
- **MoE低精度优化**：在Hopper上添加MXFP4×FP8路径

## 详细提交记录

### [07d9b92](https://github.com/flashinfer-ai/flashinfer/commit/07d9b92d0db7e3b60be8d2e4a4d2f5823fd17112)

- **作者**: Brian K. Ryu
- **时间**: 2026-07-15T23:11:52Z
- **提交信息**: feat(jit): JitSpec ABC + disk cache for JIT-compiled CuTe-DSL kernels (#3874)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->
FlashInfer's nvcc-compiled kernels are cached on disk and load instantly
in new processes; CuTe-DSL kernels were memoized only in-process, so
every new process recompiled every kernel.

The PR adds the core disk caching functionality and applies it to
`nvfp4_quantize(backend='cute-dsl')` by:
- **`JitSpec` becomes an abstract base class (ABC)** with a shared
`build_and_load()` template method (caching, locking,
`FLASHINFER_DISABLE_JIT`); the former dataclass is now `JitSpecNvcc`
(behavior unchanged), and the new
- **`JitSpecCuteDsl`** persists CuTe-DSL kernels as `export_to_c()`
object files under `cached_ops/`, reloaded via JITLink in 3–30 ms.
Future DSLs (e.g. cutile) implement the same three methods.
- **Wires up `nvfp4_quantize`** as the first user. Example kernel cache
path:
  ``` 
  .../cached_ops/
  ├── fp4_quantization_100/                  # nvcc module (unchanged)
  ├── nvfp4_quantize_sm100a_cute_dsl/        # CuTe-DSL module (new)
│ ├── meta.json # one per module (invalidation)
│ ├── swizzled_bfloat16_k4096_sf0_pdl0.o # one .o per specialization
(~28 KB)
  │   └── ...
  ```
- **Design doc**: `docs/design_docs/cute_dsl_kernel_cache.md` covers the
lifecycle, cache layout, invalidation keys, concurrency/crash safety,
and alternatives considered (including the measured-and-rejected
K-agnostic compilation). Please start there for review.


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
* Added persistent on-disk caching for CuTe-DSL JIT kernels to reduce
repeated compile time, including automatic cache invalidation based on
relevant build inputs.
* Added `FLASHINFER_CUTE_DSL_DISABLE_CACHE=1` to bypass the disk cache
and force recompilation.
  * Re-exported additional JIT specification classes for direct use.
* **Bug Fixes**
* Improved cache correctness with strict metadata validation and safer
concurrent, crash-tolerant cache writes/updates.
* **Documentation**
* Added design docs describing the CuTe-DSL cache layout, validity
rules, and locking behavior.
* **Tests**
* Updated the JIT spec construction in the C++ extension test to match
the new JIT lifecycle.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [8680059](https://github.com/flashinfer-ai/flashinfer/commit/86800591065eae209e6688f1a250e390135ab3df)

- **作者**: yichengj
- **时间**: 2026-07-15T22:45:00Z
- **提交信息**: feat(attn): Enable MiniMax Sparse Attention (MSA) for Consumer Blackwell GPUs (SM120/121) (#3655)

## 📌 Description

MiniMax-M3 introduces MiniMax Sparse Attention (MSA). The official
[MSA](https://github.com/MiniMax-AI/MSA) release provides kernels for
SM10x, which do not run on consumer Blackwell (SM120/SM121) GPUs.

MSA has two components:

- **indexer**: `proxy` (per-KV-block max of QK^T), then `top-k`
- **sparse attention**: `prefill`, `decode` (one query token per
request), and `combine`

This PR enables both on SM120/121:

- The tensor-core kernels are rebuilt on SM12x's warp-level `mma.sync`:
a union-tile sparse prefill and an adaptive split-K sparse decode that
fuses away the combine when the grid is full.
- `top-k` and `combine` are rewritten in CuTe-DSL.
- An optional NVFP4 indexer (ported from MSA) reads about 2.3x less
K-cache traffic, and prefill/decode take FP8 or NVFP4 KV, paged or flat.
BF16 stays M3's default and the precision reference.
- At decode (one query token per request) the proxy's score tile is too
thin to fill the MMA shape, so it computes on plain CUDA cores instead,
streaming index-K straight from GMEM to registers; the NVFP4 proxy sizes
its KV split to balance work across SMs.

### Added APIs

All of these live under `flashinfer.msa_ops`. "MSA:" names the ported
MSA function.

Indexer:
- **`msa_proxy_score`**: scores each KV block by the largest query-key
dot product among its tokens (bf16/fp16), which top-k then ranks. No
standalone MSA function (MSA's attention `OnlyScore` mode).
- **`msa_proxy_score_fp4`**: same scoring on the FP4 tensor cores. MSA:
`fp4_indexer_block_scores`.
- **`msa_topk_select`**: top-K KV blocks per query token. MSA:
`sparse_topk_select`.

Sparse attention:
- **`msa_sparse_attention`**: sparse prefill; each query attends only
its top-K KV blocks. Takes bf16/fp16, FP8, or NVFP4 KV, flat or paged.
MSA: `sparse_atten_func` / `sparse_atten_nvfp4_kv_func`.
- **`msa_sparse_decode_attention`**: top-K block decode, same KV options
plus FP8 queries. MSA: `sparse_decode_atten_func`.

### M3 coverage

Covers all ops on M3's sparse-attention path (prefill and decode),
verified by running a reduced-depth MiniMax-M3 model end to end.

### Performance

M3's default configuration in BF16, swept over sequence length S (2k to
32k) and decode batch (1 to 256) on RTX PRO 6000 Blackwell (Server
Edition), RTX 5080, and GB10 (SM121). Timing is the median GPU time over
30 CUDA-graph replays. Baselines run on the same GPUs, shapes, and
timer, cross-checked for identical results: vLLM's MiniMax-M3 Triton MSA
kernels, and [b12x](https://github.com/lukealonso/b12x) for bf16 sparse
prefill/decode (its indexer is FP8-only). Each side is measured as
shipped (PDL on).

One table per kernel below. Every cell is a PRO 6000 / RTX 5080 / GB10
triple ("—" where a configuration was not measured on that GPU). Speedup
= baseline ms / FlashInfer ms, so >1 means FlashInfer is faster. The
compute-bound prefill kernels report TFLOP/s with measured tensor-pipe
utilization; the memory-bound decode kernels report achieved DRAM GB/s
with % of peak (Nsight Compute). Decode tables cover batch 1-8 plus a
saturated-batch row.

#### 1. Indexer, prefill (bs1)

The indexer is the two ops that produce `q2k_indices` (`msa_proxy_score`
+ `msa_topk_select`), timed end to end; vLLM's equivalent is its score +
top-k kernels. TFLOP/s is the proxy kernel alone. The NVFP4 column is
the optional FP4 proxy's speedup over the BF16 proxy (vLLM has no SM12x
FP4 indexer to compare against).

| S | vs vLLM | proxy TFLOP/s (pipe %) | NVFP4 vs BF16 speedup |
|--:|:--:|:--:|:--:|
| 2k | 1.15 / 1.02 / 0.91 | 54 (20%) / 43 (37%) / 22 (26%) | 0.90 / 1.59
/ 0.82 |
| 4k | 0.92 / 1.11 / 1.00 | 118 (23%) / 91 (55%) / 54 (34%) | 1.65 /
2.18 / 1.26 |
| 8k | 1.04 / 1.14 / 1.01 | 249 (37%) / 143 (70%) / 87 (43%) | 1.73 /
2.52 / 1.53 |
| 16k | 1.04 / 1.18 / 1.02 | 367 (46%) / 180 (80%) / 105 (51%) | 2.04 /
2.61 / 1.59 |
| 32k | 0.90 / 1.08 / 0.89 | 469 (52%) / 200 (88%) / 107 (54%) | 1.92 /
2.62 / 1.54 |

#### 2. Indexer, decode (bs1, one query token)

vLLM's equivalent is its `index_decode` op, which runs scoring and top-k
in one call; FlashInfer runs them as two kernels. The rows are roughly
6-21 µs absolute on PRO 6000 and RTX 5080 (10-83 µs on GB10). The MTP
column is the same call with 4 draft tokens per request, a
speculative-decoding verify step. DRAM GB/s is the proxy kernel alone.

| S | vs vLLM | vs vLLM (4-token MTP) | proxy DRAM GB/s (% peak) | NVFP4
vs BF16 speedup |
|--:|:--:|:--:|:--:|:--:|
| 2k | 1.31 / 1.43 / 1.33 | 0.73 / 0.71 / 0.91 | 118 (8%) / 136 (15%) /
44 (16%) | 0.33 / 0.38 / 0.40 |
| 4k | 1.40 / 1.39 / 1.21 | 0.87 / 0.86 / 1.03 | 227 (14%) / 248 (26%) /
63 (23%) | 0.35 / 0.39 / 0.50 |
| 8k | 1.18 / 1.10 / 1.08 | 0.82 / 0.90 / 0.95 | 414 (26%) / 394 (42%) /
117 (43%) | 0.42 / 0.44 / 0.56 |
| 16k | 1.18 / 1.09 / 1.02 | 0.95 / 0.85 / 0.97 | 672 (42%) / 517 (55%)
/ 155 (57%) | 0.60 / 0.58 / 0.79 |
| 32k | 0.90 / 0.98 / 0.98 | 0.95 / 0.94 / 0.96 | 850 (54%) / 657 (70%)
/ 168 (62%) | 0.84 / 0.72 / 1.13 |

At batch 128 the proxy reaches 87-96% of DRAM peak on PRO 6000 and RTX
5080 (74-88% on GB10) and the vs-vLLM ratio is 1.00-1.03 at every S;
NVFP4 pays off there, running 1.35-2.26x faster than BF16.

<details>
<summary>Indexer, decode at batch 128 (saturated)</summary>

At short S these shapes are tens of microseconds and fixed overheads
dominate. DRAM GB/s is the proxy kernel alone.

| S | vs vLLM | proxy DRAM GB/s (% peak) | NVFP4 vs BF16 speedup |
|--:|:--:|:--:|:--:|
| 2k | 1.02 / 1.00 / 1.00 | 1389 (87%) / 866 (92%) / 203 (74%) | 1.35 /
1.34 / 1.69 |
| 4k | 1.00 / 1.02 / 1.03 | 1456 (91%) / 893 (94%) / 217 (80%) | 1.71 /
1.65 / 1.96 |
| 8k | 1.01 / 1.02 / 1.02 | 1496 (94%) / 902 (95%) / 230 (84%) | 2.03 /
1.79 / 2.14 |
| 16k | 1.01 / 1.02 / 1.01 | 1522 (95%) / 908 (96%) / 232 (85%) | 1.95 /
1.92 / 2.22 |
| 32k | 1.01 / 1.01 / 1.03 | 1532 (96%) / 911 (96%) / 241 (88%) | 2.08 /
2.04 / 2.26 |

</details>

#### 3. Sparse prefill (bs1)

Sparse-prefill cost depends on how similar consecutive queries' selected
KV blocks are, so FlashInfer is reported at both overlap extremes; vLLM
is overlap-insensitive. With block selections taken from a real M3 run
(S=16k), FlashInfer is 3.0x / 2.1x / 2.3x faster than vLLM, matching the
high-overlap end.

| S | vs vLLM (high overlap) | vs vLLM (low overlap) | vs b12x (high
overlap) | TFLOP/s (pipe %) |
|--:|:--:|:--:|:--:|:--:|
| 2k | 4.41 / 3.98 / 4.62 | 4.41 / 3.98 / 4.59 | 1.64 / 1.19 / 0.99 |
385 (57%) / 153 (76%) / 85 (53%) |
| 4k | 3.90 / 3.09 / 3.59 | 3.06 / 2.35 / 2.83 | 1.28 / 1.14 / 0.98 |
335 (64%) / 115 (81%) / 65 (57%) |
| 8k | 3.75 / 2.75 / 3.21 | 1.89 / 1.30 / 1.57 | 1.13 / 1.08 / 0.99 |
308 (66%) / 103 (83%) / 57 (57%) |
| 16k | 3.76 / 2.62 / 3.04 | 1.05 / 0.70 / 0.85 | 1.16 / 1.07 / 1.01 |
297 (67%) / 98 (84%) / 53 (57%) |
| 32k | 3.61 / 2.56 / 2.93 | 0.69 / 0.46 / 0.55 | 1.16 / 1.06 / 0.99 |
293 (67%) / 95 (84%) / 48 (57%) |

#### 4. Sparse decode (s_kv 8192, one query token)

Context-invariant in S (checked 2k to 32k), so swept over batch; batch
256 shows the saturated end. At or near parity with vLLM across the
range (the batch 1-2 rows are 13 to 18 µs absolute on PRO 6000 and RTX
5080), and faster than b12x at every batch size on all three GPUs. The
MTP column is the same kernel with 4 draft tokens per request; b12x has
no MTP path (its decode fixes the query at the last cache position).

| batch | vs vLLM | vs vLLM (4-token MTP) | vs b12x | DRAM GB/s (% peak)
|
|--:|:--:|:--:|:--:|:--:|
| 1 | 0.99 / 0.85 / 1.03 | 1.05 / 1.10 / 1.03 | 1.57 / 1.39 / 1.16 | 345
(32%) / 329 (47%) / 110 (40%) |
| 2 | 0.97 / 1.00 / 1.02 | 0.95 / 0.99 / 0.97 | 1.38 / 1.29 / 1.06 | 607
(52%) / 479 (62%) / 138 (51%) |
| 4 | 1.06 / 1.02 / 1.01 | 0.88 / 0.93 / 1.02 | 1.28 / 1.27 / 1.03 | 846
(66%) / 637 (76%) / 171 (63%) |
| 8 | 0.94 / 1.02 / 0.98 | 0.88 / 0.89 / 1.00 | 1.14 / 1.21 / 1.04 |
1087 (77%) / 738 (83%) / 198 (73%) |
| 256 | 1.02 / 0.97 / 1.01 | — | 1.21 / 1.16 / 1.23 | 1510 (95%) / 857
(91%) / 233 (85%) |

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

Covered by `pytest tests/msa_ops/` (correctness, fp4, and end-to-end
pipeline) and `pytest tests/trace/`. `compute-sanitizer`
racecheck/memcheck is clean on the new kernels.

---------

Co-authored-by: Brian <bryu@nvidia.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [ff55913](https://github.com/flashinfer-ai/flashinfer/commit/ff559138df23542c2dd43850d9e502e13efc1811)

- **作者**: kangbintNV
- **时间**: 2026-07-15T21:04:22Z
- **提交信息**: docs: cover remaining @flashinfer_api symbols missing from rst (#3942)

## Summary
- Add API reference coverage for the remaining nightly doc-check MISSING
symbols not handled by #3911 / #3941: `concat_mla_k`, CuTe-DSL BSA
kernels, `mhc_*`, `recurrent_kda`, `is_gated_activation`, and
`prepare_low_latency_gemm_weights`.
- Fix a false-positive `flashinfer.sampling._radix_top_k` finding by
importing the `topk` module instead of aliasing `top_k as _radix_top_k`
inside the sampling fast path.
- Wire new pages (`concat_ops`, `kda_decode`, `mhc`) into
`docs/index.rst`.

## Out of scope (covered elsewhere)
- #3911: `hash_topk`, `checkpoint_restore` Parameters, `CLAUDE.md`
autotuner path
- #3941: `bgmv_moe_gemm1/2_lora_delta`

## Test plan
- [x] Local MISSING-check simulation: remaining target symbols are
present in `docs/api/*.rst` / no longer aliased
- [ ] Nightly / PR doc coverage check should drop the corresponding
MISSING entries after merge (alongside #3911/#3941)
- [ ] Spot-check Sphinx API pages build for the new/updated `.rst` files

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

- **Documentation**
- Added API reference pages for tensor concatenation, key-driven
attention decoding, and multi-head convolution operations.
- Expanded documentation for block-sparse attention, gated activations,
and low-latency FP8 GEMM weight preparation.
  - Updated the API navigation to include the new reference pages.


<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [f94d533](https://github.com/flashinfer-ai/flashinfer/commit/f94d5336fa08a81c7ec8cb648ab4f2cb73cb7dcb)

- **作者**: kangbintNV
- **时间**: 2026-07-15T21:04:07Z
- **提交信息**: docs: add fused_moe LoRA delta APIs to rst (#3941)

Adds the missing `flashinfer.fused_moe` LoRA delta APIs to
`docs/api/fused_moe.rst` so the documentation coverage check includes
them.

Fixes the 4 new documentation issues reported by the nightly doc check.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Documentation**
* Added documentation entries for two Multi-LoRA MoE BGMV kernel
operations.
* These operations are now included in the public `flashinfer.fused_moe`
API reference.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [5823159](https://github.com/flashinfer-ai/flashinfer/commit/5823159c3b7774e5e01bf7d935763f75b2f3731f)

- **作者**: NVJiangShao
- **时间**: 2026-07-15T16:48:29Z
- **提交信息**: perf: optimize MXFP4xBF16 & INT4xFP8 and add MXFP4xFP8 CUTLASS MoE backend for SM90 (#3738)

## 📌 Description

This PR updates the Hopper CUTLASS grouped MoE backend for mixed
low-precision
inputs. It improves the existing Hopper W4 grouped GEMM paths and adds a
new
MXFP4 weight + FP8 activation path:

- MXFP4xBF16: optimize the existing MXFP4 weight + BF16 activation path.
- INT4xFP8: optimize the existing INT4 weight + FP8 activation path.
- MXFP4xFP8: add MXFP4 weight + FP8 activation with pre-MMA E8M0 scale
fusion and runtime
  per-token FP8 activation quantization.

The MXFP4xFP8 path follows the high-level weight preprocessing and
dequantization idea used by
[Humming](https://github.com/inclusionAI/humming):
the MXFP4 weight scale is transformed into a bounded E8M0 exponent
offset and
folded into the FP8 operand before MMA. FlashInfer keeps this flow
integrated
with its fused MoE runtime, autotune, and CUTLASS extension backend.

The implementation keeps the changes inside FlashInfer's CUTLASS
extension
layer rather than modifying vendored CUTLASS. The main changes are:

- Enable Hopper FP4 kernels without requiring CUDA native FP4 headers on
SM90
  by using CUTLASS subbyte FP4 types.
- Add optimized mixed-input mainloops for post-MMA scaling and pre-MMA
E8M0
  scale fusion.
- Precompute grouped GEMM work scheduling and TMA descriptor state
before the
  main GEMM kernel.
- Use folded weight-scale storage so the weight-scale layout is
independent of
  the profiled `TileK`.
- Add precomputed scheduler kernels for ping-pong and cooperative
grouped GEMM
  schedulers.
- Add runtime activation expansion and per-token FP8 quantization
support for
  the pre-MMA E8M0 scale-fusion path.
- Add per-token scale epilogue callbacks for the FP8 activation + MXFP4
weight
  path.
- Extend autotune and tactic validation so Hopper mixed-input tactics
are
  checked for correctness before being selected.
- Add and update tests for Hopper MXFP4xBF16, INT4xFP8, and MXFP4xFP8
pre-MMA scale
  paths.

## 🔍 Related Issues

N/A

## Performance

Benchmarks were run on NVIDIA H20 and H200 GPUs using MoE workload
configurations matching DeepSeek-V3 (256 experts, top-8, hidden size
7168, intermediate size 2048) and DeepSeek-V4-Pro (384 experts, top-6,
hidden size 7168, intermediate size 3072).
https://huggingface.co/deepseek-ai/DeepSeek-V3
https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro
The plots below summarize the PR performance results. Raw benchmark
tables are intentionally not embedded in this PR text.

### INT4xFP8 and MXFP4xBF16 vs Same-Path Baseline

The existing INT4xFP8 and MXFP4xBF16 paths generally improve over the
same-path
baseline after the Hopper mixed-input backend changes.

| **Current fused MoE speedup vs same-path baseline**
<img width="3240" height="1530"
alt="fused_moe_current_vs_baseline_w4a8_w4a16_nonuniform_percent"
src="https://github.com/user-attachments/assets/8a611edf-af95-4a19-a53c-38a3bb314c4d"
/>
<img width="3240" height="1530"
alt="H200_fused_moe_current_vs_baseline_w4a8_w4a16_nonuniform_percent"
src="https://github.com/user-attachments/assets/857b6f74-91ff-46b7-b0ff-0fc07e7ceb6e"
/>


### Current Paths vs Current FP8 Per-Tensor Baseline

This compares the current fused MoE mixed-input paths against the
current FP8
per-tensor path.

| **Current fused MoE path speedup vs current FP8 per-tensor**
<img width="3240" height="1530"
alt="H20_fused_moe_current_paths_vs_current_fp8_pt_percent_no_humming_upstream"
src="https://github.com/user-attachments/assets/2be2d3ad-85f3-4510-82ad-b33ca2417ab3"
/>
<img width="3240" height="1530"
alt="H200_fused_moe_current_paths_vs_current_fp8_pt_percent"
src="https://github.com/user-attachments/assets/bc43aaf2-a1ad-491c-a9e4-4dc2b0681ac3"
/>


### MXFP4xFP8 Pre-MMA Scale Path vs Upstream Humming (2026/06/23 commit
f6241bb)

The pre-MMA E8M0 scale-fusion path is compared against upstream Humming
GEMM
timings. Positive values mean FlashInfer is faster.

| **DS4 FlashInfer Humming GEMM speedup vs upstream Humming**
<img width="3240" height="1530"
alt="H20_humming_fi_vs_upstream_ncu_percent"
src="https://github.com/user-attachments/assets/df8287e8-f2d3-41e6-99b8-8878f5dd5c88"
/>
<img width="3240" height="1530"
alt="H200_humming_fi_vs_upstream_ncu_percent"
src="https://github.com/user-attachments/assets/badb8b07-6d26-4e61-bbed-74111207620e"
/>



## Implementation Notes

- The Hopper FP4 compatibility path uses CUTLASS FP4 storage on SM90 and
keeps
  CUDA native FP4 as a toolkit-dependent feature instead of a Hopper
  requirement.
- The mixed-input grouped GEMM scheduler now supports a precomputed work
map.
This avoids doing grouped tile lookup and descriptor updates in the main
GEMM
  hot path.
- The folded weight-scale layout decouples model preprocessing from the
selected `TileK`, which lets autotune choose among multiple `TileK`
values
  without requiring multiple prepacked weight-scale layouts.
- The pre-MMA E8M0 scale path fuses the weight scale into FP8 operands
before
  WGMMA and applies the activation token scale in the epilogue.
- The MXFP4xFP8 pre-MMA scale path is inspired by Humming's weight
  preprocessing/dequantization flow:
  https://github.com/inclusionAI/humming
- The runtime FP8 activation quantization path computes per-token
activation
  scales while expanding routed MoE rows.
- The autotune validation path now rejects tactics that fail correctness
before
  timing and selection.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request,
please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used
  your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed
  any reported issues.

> If you are unsure about how to set up `pre-commit`, see
> [the pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] Hopper MXFP4xBF16 correctness and coverage tests were
added/updated.
- [x] Hopper INT4xFP8 correctness and autotune tests were added/updated.
- [x] Hopper MXFP4xFP8 pre-MMA E8M0 scale-fusion correctness and
autotune tests
  were added.
- [x] All selectable Hopper mixed-input tactics are validated for
correctness
  during autotune.

Local validation focused on Hopper mixed-input MoE paths:

```bash
pytest -q tests/moe/test_trtllm_cutlass_fused_moe.py::test_moe_bf16_mxfp4_hopper_correctness
pytest -q tests/moe/test_trtllm_cutlass_fused_moe.py::test_moe_bf16_mxfp4_hopper_coverage
pytest -q tests/moe/test_trtllm_cutlass_fused_moe.py::test_moe_w4a8_hopper_correctness
pytest -q tests/moe/test_trtllm_cutlass_fused_moe.py::test_moe_w4a8_hopper_autotune
pytest -q tests/moe/test_trtllm_cutlass_fused_moe.py::test_moe_fp8_mxfp4_humming_prescale_hopper_correctness
```

## Reviewer Notes

- The CUTLASS changes are intentionally placed under
`csrc/nv_internal/tensorrt_llm/cutlass_extensions/`; this PR does not
modify
  vendored CUTLASS under `3rdparty/`.
- The pre-MMA E8M0 scale-fusion path has a distinct runtime path from
the
standard post-MMA scale paths because it changes where MXFP4 weight
scaling is
  applied.
- The MXFP4xFP8 weight preprocessing and dequantization strategy is
based on
the Humming approach for fusing E8M0 scale offsets into the FP8 MMA
operand:
  https://github.com/inclusionAI/humming
- Autotune now validates candidate Hopper mixed-input tactics against
reference
  output before using their timing result for tactic selection.
- The benchmark figures above compare fused MoE or GEMM timing scopes as
noted
  in each plot title.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

## Release Notes

* **New Features**
* Added SM90 “Humming” MXFP4→FP8 fused MoE with per-token FP8
quantization scaling.
* Extended the fused MoE API with `use_wfp4afp8_humming` and optional
`profile_ids` to steer tactic selection.
* Added Humming-focused weight preprocessing/ interleaving utilities and
exposed `preprocess_moe_weights_for_sm90_mixed_gemm_humming`.
* **Bug Fixes**
* Improved FP4 compatibility by using the project’s FP4-compatible type
handling.
* **Tests**
* Added Hopper correctness tests for the SM90 Humming prescale and
end-to-end path.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Jiang Shao <91270701+StudyingShao@users.noreply.github.com>
Co-authored-by: Sam (Kesen Li) <lsam@nvidia.com>

### [59c60f9](https://github.com/flashinfer-ai/flashinfer/commit/59c60f966aaa49d7bcc391b47bc3372d21190ecb)

- **作者**: Lain
- **时间**: 2026-07-15T14:21:35Z
- **提交信息**: Update moe cubins to fix 2CTA hanging issue (#3973)

<!-- .github/pull_request_template.md -->

## 📌 Description

- Update the MoE cubins to fix a hanging issue of 2CTA kernels after
v0.6.8

## 🔍 Related Issues

- https://github.com/flashinfer-ai/flashinfer/issues/3279

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

* **Chores**
  * Updated metadata for the TRTLLM GEN BMM artifact.
  * Corrected its download path and integrity checksum.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: Siyuan Fu <siyuanf@nvidia.com>

### [621447a](https://github.com/flashinfer-ai/flashinfer/commit/621447a36cb16f73439122dddc38dadda22f464d)

- **作者**: Josh Park
- **时间**: 2026-07-15T12:45:53Z
- **提交信息**: Fix cuDNN batch prefill test (#3784)

<!-- .github/pull_request_template.md -->

## 📌 Description

This adds missing batch offsets to the
`test_cudnn_batch_prefill_reference_correctness.py` file. It fixes
previous failures in CI.

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

* **Tests**
* Updated cuDNN batch prefill reference to use cumulative “packed”
ragged offsets derived from sequence-lengths, with updated
sequence-length tensor shaping.
* Added a test to confirm that omitting required batch offset inputs
raises a `ValueError` when batching multiple sequences.

* **Documentation**
* Clarified `batch_offsets_*` semantics as cumulative element offsets
with shape `(batch_size + 1)`, and documented cuDNN graph-path input
requirements.

* **Bug Fixes**
* Added runtime validation for the cuDNN graph path: when `batch_size >
1`, missing `batch_offsets_q` or `batch_offsets_o` now fails fast with a
clear error.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>
Co-authored-by: Yang Xu <yanxu@nvidia.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [22f8151](https://github.com/flashinfer-ai/flashinfer/commit/22f8151fd7c9173860364a96267e6cf3dd00b7ef)

- **作者**: Yang Xu
- **时间**: 2026-07-15T10:02:54Z
- **提交信息**: fix(cute_dsl): migrate off APIs removed in nvidia-cutlass-dsl 4.6 (keeps 4.5.x compat) (#3922)

## 📌 Description

`nvidia-cutlass-dsl` 4.6.0 (released 2026-07-02) executed its
long-deprecated API clean-up:

- `cute.make_fragment` removed → `cute.make_rmem_tensor`
- `cute.core.ThrMma` / `cute.core.ThrCopy` removed → `cute.ThrMma` /
`cute.ThrCopy`

Since `requirements.txt` floats on `nvidia-cutlass-dsl>=4.5.0`, a fresh
install now resolves to 4.6.0, and the blk128 sparse-attention path and
the SM120 b12x dense block-scaled GEMM path raise `AttributeError` at
trace time.

This PR is a pure rename (±31 lines, 4 files):

- `cute.make_fragment(` → `cute.make_rmem_tensor(` — 18 sites
- `cute.core.ThrMma` → `cute.ThrMma` — 13 sites

**No version guard and no requirements change needed**: the replacement
names already exist in 4.5.0/4.5.1/4.5.2 (verified against the v4.5.x
tags), so the same code works across 4.5.x and 4.6.x.
`cute.make_fragment_like` (79 sites) is *not* touched — it is still
shipped in 4.6.0 and in the current internal nightly.

## ✅ Verification

- Live probes on both versions: `make_rmem_tensor`/`ThrMma`/`ThrCopy`
present in 4.5.2 and 4.6.0; `make_fragment` confirmed absent in 4.6.0.
- A `make_rmem_tensor` smoke kernel traces, compiles, and runs with
correct output on SM100 under **both** cutlass-dsl 4.5.2 and 4.6.0.
- Repo-wide grep for the removed spellings is clean (`flashinfer/`,
`tests/`, `benchmarks/`).
- pre-commit (ruff, mypy, formatters) passes.

Not covered here (needs CI/QA hardware): full blk128/VSA suite on SM100
(requires `quack`; note quack must be version-paired — quack 0.5.x for
DSL 4.5.x, quack ≥0.6 pins `==4.6.0`), and SM120 b12x GEMM/MoE suites.

## 🔍 Related Issues

Follow-up (separate PR):
`flashinfer/cute_dsl/sparse/blk128/mma_sm100_desc.py` references
`cutlass.FloatE4M3FN`/`cutlass.FloatE5M2`, which do not exist in any of
4.5.x/4.6.0 — latent `AttributeError` on the fp8 branch, independent of
this migration.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Improved compatibility and reliability across sparse attention and
dense GEMM kernels.
* Updated internal temporary tensor handling used by softmax,
correction, reduction, and epilogue paths to improve consistent
execution on supported GPU workloads.
* Adjusted predicate and intermediate tensor staging to maintain
existing computation while improving stability under varied shapes and
configurations.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yang Xu <yanxu@nvidia.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [92651ff](https://github.com/flashinfer-ai/flashinfer/commit/92651ff60b835ba178a45ae61d3e2c6e31610354)

- **作者**: Cindy Zhang
- **时间**: 2026-07-15T09:34:22Z
- **提交信息**: fix (test): mock MoE EP arch validation in split unit tests (#3964)

<!-- .github/pull_request_template.md -->

## 📌 Description

In the CUDA 13.0 nightly `test-nightly-build` job, the MoE EP unit/mock
test section fails on the `sm86` runner:

https://github.com/flashinfer-ai/flashinfer/actions/runs/29303176529/job/87009219403

  ```text
FAILED
tests/moe_ep/nixl_ep/test_fleet_mock.py::test_fleet_init_calls_update_memory_and_connect
FAILED
tests/moe_ep/nixl_ep/test_fleet_mock.py::test_handle_combine_requires_topk_weights
FAILED
tests/moe_ep/nixl_ep/test_fleet_mock.py::test_update_topology_diffs_ranks
FAILED
tests/moe_ep/test_layer_factory.py::test_factory_returns_split_for_string_backend
FAILED
tests/moe_ep/test_layer_factory.py::test_factory_returns_split_for_nvep_config
```
  The failure is caused by these mock/factory tests reaching the real MoE EP arch gate:

  MoEEpArchError: nccl_ep/nixl_ep requires sm_90+, host has sm_86

  The sm_90+ validation is correct for real nccl_ep / nixl_ep runtime usage, but these tests validate mocked Buffer call sequencing and MoEEpLayer factory routing. They should not require Hopper/Blackwell hardware. 

  This PR patches validate_arch_for_backend only inside the affected mock/factory tests, while keeping the production arch validation unchanged. The dedicated arch validation tests still cover the pre-Hopper rejection path.

## 🔍 Related Issues

https://github.com/flashinfer-ai/flashinfer/issues/3963 

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit` (or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files` and fixed any reported issues.

> If you are unsure about how to set up `pre-commit`, see [the pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

-  tests/moe_ep/test_arch_and_build.py::test_validate_arch_rejects_pre_hopper PASSED on A100 / sm80
-  tests/moe_ep/test_layer_factory.py PASSED on A100 / sm80
-  tests/moe_ep/nixl_ep/test_fleet_mock.py PASSED on A100 / sm80

## Suggested CI:

  /bot run tests/moe_ep

## Reviewer Notes

  The production sm_90+ gate is intentionally unchanged. This PR only avoids applying that runtime hardware gate to mock/factory unit tests whose purpose is not to validate real backend support.


<!-- This is an auto-generated comment: release notes by coderabbit.ai -->
## Summary by CodeRabbit

* **Tests**
  * Improved host-only test isolation by updating documentation for mocked backend assumptions.
  * Mocked backend architecture validation during unit tests to ensure they validate call sequencing and argument marshalling rather than runtime/CUDA arch behavior.
  * Updated layer factory split-layer tests to patch out backend validation during construction, while preserving existing environment and CUDA-related skips.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-07-16
**监控日期**: 2026-07-15
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3840
- **最后更新**: 2026-07-15T21:59:14Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Mac Lee

## AI分析总结

根据提供的仓库README摘要和提交记录，以下是对昨日更新（仅一条CI提交）的分析总结：

---

### 1. 主要更新类型
- **CI/性能优化**（基础设施改进）

### 2. 关键变更点及其与项目整体方向的关系
- **变更点**：在CI流程中新增了“精确身份性能状态”（exact identity performance statuses）。
- **关系**：FastVideo作为视频处理/生成工具，其输出结果的一致性和运行性能至关重要。该变更通过CI自动监控输出与预期完全一致的场景下的性能指标，确保在代码迭代中不会引入性能退化或输出差异，与项目追求高效、可靠的核心目标一致。

### 3. 对项目的影响和潜在意义
- **影响**：CI流水线现在能够更精细地捕获性能变化，尤其是针对“精确匹配”这一严格基准。开发者可以快速发现因修改模型、优化逻辑或调整数据路径导致的性能波动，提高回归检测的敏感度。
- **潜在意义**：为后续性能调优提供了量化依据，并降低了合并新代码时引入隐性性能问题的风险，有助于维持项目高速迭代下的质量稳定性。

### 4. 值得关注的技术点
- **“exact identity”性能状态**：可能指向输出张量、像素值或推理结果的精确一致性验证，而非通常的近似比较（如PSNR/SSIM）。这种严格指标对视频生成、帧重建等对像素级精度敏感的任务尤为重要。
- **CI集成方式**：提交所属模块为`ci`，表明该功能直接嵌入在自动化测试套件中，开发者无需手动执行即可获取状态反馈。

### 5. 结合README背景对项目发展的影响
- FastVideo文档强调“快速开始”和“每周开发会议”，说明项目处于活跃开发阶段，频繁合并新功能。该CI提交通过**强化性能回归防线**，间接支撑了项目的快速迭代策略——既保证新特性顺利融入，又避免性能下降影响用户体验。
- 社区可通过CI状态快速评估自己贡献的代码是否导致性能问题，降低协作门槛，有利于吸引更多贡献者。

## 详细提交记录

### [a253856](https://github.com/hao-ai-lab/FastVideo/commit/a253856147d1adac074652df5b6bc07e71d0c3dc)

- **作者**: Mac Lee
- **时间**: 2026-07-15T21:59:09Z
- **提交信息**: [ci] Add exact identity performance statuses (#1560)

Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-07-16
**监控日期**: 2026-07-15
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34067
- **最后更新**: 2026-07-15T23:42:38Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 3
- **主要提交者**: Sayak Paul, David El Malih, Linoy Tsaban

## AI分析总结

以下是针对 `huggingface/diffusers` 仓库昨日提交记录的分析总结：

---

### 1. 主要更新类型
- **文档改进**：3 次 docstring 优化（`scheduling_repaint.py`、`scheduling_unclip.py`、`scheduling_tcd.py`）
- **功能增强**：LoRA 训练标签改进（为 KREA2 LoRA 卡增加 Turbo 基础模型标签，启用推理小部件）
- **文档/示例补充**：Skills（教程）中添加模型实现说明
- **依赖兼容性修复**：`snapshot_download` 函数与 `huggingface_hub`（HFH）最新版本对齐，修复离线下载校验逻辑，提升稳定性

---

### 2. 关键变更点与项目方向的关系
- **Docstring 改进**：覆盖 `repaint`、`unclip`、`tcd` 三种调度器（scheduler），属于**代码可读性和开发者体验**的持续优化，符合 `diffusers` 作为面向开发者社区的开源库的定位。
- **LoRA 训练标签增强**：通过为 KREA2 LoRA 卡添加 `Turbo` 基础模型标签，使推理 widget 能正确识别并展示该模型。这直接支持了 **LoRA 模型在 Hugging Face Hub 上的可视化与交互**，推动模型生态建设。
- **Skills 模型实现说明**：在官方教程中补充模型实现细节，降低用户实现自定义模型的门槛，符合项目「降低扩散模型使用和定制难度」的核心目标。
- **`snapshot_download` 对齐**：确保 `diffusers` 内部下载逻辑与 `huggingface_hub` 的最新行为一致，离线时自动校验缓存完整性，报告 `IncompleteSnapshotError` 而非神秘崩溃。这是**后端基础设施优化**，直接影响模型加载的稳定性和用户排查问题的效率。

---

### 3. 对项目的影响和潜在意义
- **文档改进**：减少用户对调度器 API 的困惑，提高代码自文档化程度，间接降低问题反馈量。
- **LoRA 标签调整**：提升 KREA2 等社区 LoRA 模型的曝光度，鼓励用户上传和分享 LoRA 权重，丰富 `diffusers` 生态。
- **Skills 补充**：帮助进阶用户快速实现自定义模型，可能催生更多社区贡献的创新模型。
- **下载兼容性修复**：消除因 `huggingface_hub` 版本差异导致的偶发加载失败，特别是离线/弱网场景下的体验提升；修复测试断言使其适配新版本错误消息，保证 CI 健康。

---

### 4. 值得关注的技术点
- **`snapshot_download` 逻辑重写**：采用 `get_cached_repo_tree` 替代旧的目录校验，并统一在线/离线路径的 allow/ignore patterns，使得离线时也能从缓存快照中获取文件列表进行验证。这体现了对 `huggingface_hub` 新版 API 的追随。
- **`force_download=True` 的引入**：在某些测试场景中强制重新下载，避免缓存干扰。
- **测试断言适配**：将断言从绝对路径改为文件名匹配，以兼容新版 `huggingface_hub` 的错误消息格式。

---

### 5. 基于项目背景的发展影响
- `diffusers` 定位为开源、模块化的扩散模型库，昨日提交体现了**三线并进**的策略：
  - **文档/开发者体验**（docstring、skills）——降低使用门槛，吸引新用户。
  - **生态建设**（LoRA 标签）——促进 Hub 上模型的可发现性和交互性，巩固 Hugging Face 生态。
  - **工程稳定性**（下载对齐）——确保底层基础设施与周边依赖同步演进，减少兼容性摩擦。
- 整体上，这些提交既服务了**入门用户**（更好的文档和导引），也服务了**高级使用者**（LoRA 发布便利、模型实现指南），同时保障了**项目维护成本**（稳健的下载逻辑）。

## 详细提交记录

### [612036a](https://github.com/huggingface/diffusers/commit/612036aa14e416902fc38c3f3ef30fe8357acf7f)

- **作者**: David El Malih
- **时间**: 2026-07-15T23:42:32Z
- **提交信息**: docs: improve docstring scheduling_repaint.py (#14199)

Improve docstring scheduling repaint

### [3eed247](https://github.com/huggingface/diffusers/commit/3eed2477f8edd64406bf1642ba7ff773f3514c86)

- **作者**: David El Malih
- **时间**: 2026-07-15T20:16:39Z
- **提交信息**: docs: improve docstring scheduling_unclip.py (#14196)

Improve docstring scheduling unclip

### [bc529a5](https://github.com/huggingface/diffusers/commit/bc529a5f677db9c4b3fc72c76962c4e2f61567e1)

- **作者**: David El Malih
- **时间**: 2026-07-15T15:51:53Z
- **提交信息**: docs: improve docstring scheduling_tcd.py (#14192)

* Improve docstring scheduling tcd

* Improve docstring scheduling tcd

### [273f337](https://github.com/huggingface/diffusers/commit/273f337137e329eb0268058389f17608e5f5b633)

- **作者**: Linoy Tsaban
- **时间**: 2026-07-15T14:26:10Z
- **提交信息**: [lora training] tag krea2 LoRA card with Turbo base model first to enable inference widget (#14171)

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

### [a437794](https://github.com/huggingface/diffusers/commit/a437794c0b3c13a4385135c1adc96dac55325db2)

- **作者**: Sayak Paul
- **时间**: 2026-07-15T09:03:06Z
- **提交信息**: [skills] add notes about model implementation in our skills. (#14191)

add notes about model implementation in our skills.

### [a50c7a2](https://github.com/huggingface/diffusers/commit/a50c7a2303bf229675b793f3a9be5d2932d90408)

- **作者**: Sayak Paul
- **时间**: 2026-07-15T08:55:02Z
- **提交信息**: align snapshot_download to respect hfh latest version (#14118)

* align snapshot_download to respect hfh latest version

* fix

* compute the same snapshot_download patterns offline as online

Instead of returning the cached snapshot folder without validation when
offline, compute the same allow/ignore patterns as the online path
(sourcing the file listing from the cached snapshot instead of
model_info) and let snapshot_download validate the cached snapshot
against them, so an interrupted download surfaces hfh's
IncompleteSnapshotError instead of failing later at model load time.
Also revert the _get_checkpoint_shard_files divergence: its patterns
were already identical in both modes.

Co-Authored-By: Claude Fable 5 <noreply@anthropic.com>

* match missing-shard test on the shard filename

huggingface_hub>=1.22.0 reports a missing cached shard via
IncompleteSnapshotError (repo-relative path) before diffusers' own
cached-folder check (absolute path) runs, so assert on the shard's
filename, which both messages contain.

Co-Authored-By: Claude Fable 5 <noreply@anthropic.com>

* use get_cached_repo_tree

* remove the requirement decorator from tests

* force_download=True

---------

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-07-16
**监控日期**: 2026-07-15
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 424
- **最后更新**: 2026-07-10T06:55:40Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-07-16
**监控日期**: 2026-07-15
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12704
- **最后更新**: 2026-07-15T18:12:32Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-07-16
**监控日期**: 2026-07-15
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 30346
- **最后更新**: 2026-07-15T23:29:33Z

## 提交统计

- **昨日提交总数**: 32
- **提交者数量**: 27
- **主要提交者**: Ma Mingfei, Jorge António, Yuzhen Zhou

## AI分析总结

好的，以下是对仓库 `sgl-project/sglang` 昨日提交记录的分析总结，结合项目背景（高性能推理框架，支持多模型、多硬件、多模态）进行解读。

---

### 1. 主要更新类型

| 类型 | 涉及提交（部分） | 说明 |
|------|----------------|------|
| **功能新增** | `#31375` `#30706` `#30036` `#30113` `#30904` `#31360` | 新增 Spec 解码优化、fp4 组合 dtype、RL rollout for diffusion、FlashInfer SM100 KDA 解码后端、多模态特征统一传输、Inkling cookbook |
| **Bug修复** | `#31367` `#31232` `#31321` `#30997` `#30355` `#31343` `#30976` | 修复多层 EAGLE 统计、Ministral3 RoPE、Mamba 缓存释放、异构注意力 TP 传输、AMD DeepSeek MLA、Blackwell FA3、MTP 量化加载等 |
| **性能优化** | `#31375` `#30012` `#29007` `#31257` | 提取共享 draft() tail、BF16 索引器、MoE TP allreduce 使用对称内存、Eagle 辅助提取 |
| **文档/示例** | `#31333` `#31360` `#30651` | CUDA crash dump 文档、Inkling cookbook、DeepSeek V4 AMD disagg cookbook |
| **重构** | `#25663` `#31257` `#30182` | Ascend MoE 重构、Eagle worker 公共提取、msgpack IPC 空字段清理 |
| **CI/测试** | `#31088` `#31371` `#31289` `#31332` | 新增 AMD 测试、移除冗余 nightly、调整 GLM 阈值、修复 TRTLLM 测试 |
| **硬件支持** | `#31088` `#30355` `#30359` `#31131` `#31171` `#31343` | AMD (ROCm/MI355)、Blackwell (FA3)、NPU (CPU/昇腾) |

---

### 2. 关键变更点与项目方向的关系

- **Speculative Decoding 强化** (`#31375`, `#31257`, `#31367`)：提取共享 draft 尾部逻辑、构建 Eagle verify 输入，并修复多层 EAGLE 的捕获时 num_tokens_per_req 统计。方向：提升 Spec 解码的效率和准确性，这是 sglang 低延迟推理的核心竞争力。

- **多模型/多模态生态扩展** (`#31027`, `#30904`, `#30621`, `#30036`)：支持 GLM-Image 生成的多输出、统一多模态特征传输、修复多输出图像 URL 响应、支持 Wan diffusion pipeline 的 RL rollout。方向：从纯 LLM 向多模态生成（图像、视频）延伸，拓宽应用场景。

- **多后端硬件适配**（AMD `#30355` `#30359` `#31131` `#31088`，NPU `#25663` `#31107`，CPU `#31171`，Blackwell `#31343`）：修复 AMD MI355 上 DeepSeek MLA 的 Triton 后端、启用 Qwen3.5 Mamba-extra-buffer、修复 DSV4 JIT 构建；重构 Ascend MoE 减少重复代码；CPU 添加 Qwen3.5 融合输入投影；修复 Blackwell 上 MiMo-V2 的 FA3 回退。方向：坚持多硬件兼容，特别是 AMD 和国产 NPU 的深度适配，释放市场潜力。



## 详细提交记录

### [b0b2dfb](https://github.com/sgl-project/sglang/commit/b0b2dfbda1173e15f4707d63c9f4a7263971f41c)

- **作者**: Liangsheng Yin
- **时间**: 2026-07-15T22:59:31Z
- **提交信息**: [Spec] Extract the shared draft() tail into build_eagle_verify_input (#31375)

### [7a973c0](https://github.com/sgl-project/sglang/commit/7a973c03a0f650d2da6aad5b55d2c4ab698100b3)

- **作者**: Yuzhen Zhou
- **时间**: 2026-07-15T22:24:32Z
- **提交信息**: [Bugfix] Stamp capture-time num_tokens_per_req in multi-layer EAGLE; close jit_kernel CI filter gaps (#31367)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: hnyls2002 <lsyincs@gmail.com>

### [3101c12](https://github.com/sgl-project/sglang/commit/3101c1258c4d5dc4884868259278fb6370a92617)

- **作者**: Lewis
- **时间**: 2026-07-15T22:06:55Z
- **提交信息**: [DSv4] Use BF16 instead of FP32 for indexer score computation (#30012)

Co-authored-by: 百麒 <yaozhong.lyz@alibaba-inc.com>

### [26cb0fc](https://github.com/sgl-project/sglang/commit/26cb0fcddae38541f4b4250d8f3f519f8964c0a3)

- **作者**: Jorge António
- **时间**: 2026-07-15T21:55:06Z
- **提交信息**: Empty `_REQ_TYPES_WITH_OPAQUE_FIELDS` on the msgpack IPC path (#29465 Task 4) (#30182)

### [6714844](https://github.com/sgl-project/sglang/commit/67148447a6ad13e9dbd60f1ba30c5166e6fd23d9)

- **作者**: Michael
- **时间**: 2026-07-15T21:36:05Z
- **提交信息**: [AMD] Register 3 CPU-bound / triton unit + light-integration tests for AMD 1-GPU PR CI (#31088)

### [ec32590](https://github.com/sgl-project/sglang/commit/ec325900257223ac62cebc759c12f782864647b2)

- **作者**: karverma-amd
- **时间**: 2026-07-15T21:21:41Z
- **提交信息**: feat(moriep): add fp4 combine dtype (SGLANG_MORI_COMBINE_DTYPE=fp4) (#30706)

### [e78051a](https://github.com/sgl-project/sglang/commit/e78051a4192af778c94d269c9621aae9ed74f7c4)

- **作者**: jacky.cheng
- **时间**: 2026-07-15T21:19:23Z
- **提交信息**: [AMD] [Fix] Fix --attention-backend triton work for DeepSeek MLA on MI355 (null-K + decode dispatch + RoPE) (#30355)

### [e76cc75](https://github.com/sgl-project/sglang/commit/e76cc75cfa5b4031f194849f363cdb29f834f58d)

- **作者**: Liangsheng Yin
- **时间**: 2026-07-15T21:12:07Z
- **提交信息**: [CI] Remove nightly registrations redundant with scheduled stage runs (#31371)

### [5abec3f](https://github.com/sgl-project/sglang/commit/5abec3fbf879a4d017e7e481bceb4a6276f04073)

- **作者**: Yuhao Yang
- **时间**: 2026-07-15T20:26:27Z
- **提交信息**: Fix MiMo-V2 on Blackwell: FA3 fallback and TP-aware audio weight loading (#31343)

### [18043ae](https://github.com/sgl-project/sglang/commit/18043aec20e8fa2870ac5918d82c71eed3a939f4)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-07-15T19:44:51Z
- **提交信息**: [CI] Fix TRTLLM MHA graph metadata test fixture (#31332)

### [ab627e5](https://github.com/sgl-project/sglang/commit/ab627e5d756094311973f7e00adda6075503115d)

- **作者**: Shaun Kotek
- **时间**: 2026-07-15T19:12:04Z
- **提交信息**: fix: load the right mtp lm head quantization (#30976)

### [7e7129a](https://github.com/sgl-project/sglang/commit/7e7129acd702355e55f68a30f0fcedcce4080b22)

- **作者**: Xuwei
- **时间**: 2026-07-15T18:32:07Z
- **提交信息**: [Bugfix] Release Mamba cache after PP dynamic chunk profiling (#31321)

### [2d00e20](https://github.com/sgl-project/sglang/commit/2d00e20a5230725df68a46dd58b496fc30bd1e19)

- **作者**: YAMY
- **时间**: 2026-07-15T18:31:37Z
- **提交信息**: [Disagg][Qwen3.5] Fix heterogeneous attn-TP scatter transfer: GDN conv sub-block slice + GQA replicated-KV head map (#30997)

Co-authored-by: Xuwei Li <lixuwei.xy@gmail.com>

### [dd2e4cd](https://github.com/sgl-project/sglang/commit/dd2e4cdc9921043f15abff47006fed945eba3666)

- **作者**: Yuhao Yang
- **时间**: 2026-07-15T18:24:31Z
- **提交信息**: Add Inkling cookbook (#31360)

### [9d147fd](https://github.com/sgl-project/sglang/commit/9d147fdca149119d14b288a9df587549d12505a6)

- **作者**: AuFlow
- **时间**: 2026-07-15T17:55:19Z
- **提交信息**: [Multimodal] Support n>1 outputs for GLM-Image generation (#31027)

Co-authored-by: AuFlow <AuFlow@users.noreply.github.com>

### [dc078dd](https://github.com/sgl-project/sglang/commit/dc078ddd2a97c2d7aa4c7b26fe1269ed23b48e1b)

- **作者**: Liangsheng Yin
- **时间**: 2026-07-15T17:54:31Z
- **提交信息**: [Spec] Extract stateless draft prepare helpers into eagle_worker_common (#31257)

### [d36e96c](https://github.com/sgl-project/sglang/commit/d36e96ce234a502013e254d47f2f5bf6ceb65acb)

- **作者**: Bingxu Chen
- **时间**: 2026-07-15T17:18:12Z
- **提交信息**: [AMD] Enable mamba-extra-buffer for Qwen3.5 on ROCm (#30359)

Co-authored-by: ntgiang71096 <nguyentruonggiang71096@gmail.com>

### [a8b6043](https://github.com/sgl-project/sglang/commit/a8b60433c29cdf1ffdfe9071d498c1268f7e2651)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-07-15T16:58:12Z
- **提交信息**: [AMD] Fix DSV4 JIT build on rocm  (#31131)

Co-authored-by: kangwangamd <kangwang@amd.com>

### [c879f3d](https://github.com/sgl-project/sglang/commit/c879f3da5ceaaef3cb197c4e59ce683d420ce96c)

- **作者**: Andy Ye
- **时间**: 2026-07-15T14:30:51Z
- **提交信息**: [diffusion] rl: support rl rollout for the wan pipeline via a per-request scheduler switch (#30036)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [d2b1243](https://github.com/sgl-project/sglang/commit/d2b1243be0c3f67e6bf78ace97b2c1b2382cb1c6)

- **作者**: Jun Liu
- **时间**: 2026-07-15T14:18:36Z
- **提交信息**: docs: document CUDA crash dump output (#31333)

Co-authored-by: Xinyuan Tong <xinyuantong.cs@gmail.com>

### [495ae9a](https://github.com/sgl-project/sglang/commit/495ae9aaa609d39fd4e294d4f64faf52e29f50a6)

- **作者**: Elizaveta Martirosian
- **时间**: 2026-07-15T12:23:04Z
- **提交信息**: Fix Ministral3 accuracy issue by aligning YaRN RoPE scaling with Transformers implementation (#31232)

Co-authored-by: Elizaveta Martirosian <elizaveta.martirosian@gmail.com>
Co-authored-by: ronnie_zheng <zl19940307@163.com>

### [8ed82af](https://github.com/sgl-project/sglang/commit/8ed82afcc8c1713137801559736557f32db7636e)

- **作者**: Артем Савкин
- **时间**: 2026-07-15T11:59:42Z
- **提交信息**: [MoE Refactor] [NPU] Refactor Ascend MoE implementation to reduce code duplication and align with community design (#25663)

Co-authored-by: ronnie_zheng <zl19940307@163.com>

### [c9b1740](https://github.com/sgl-project/sglang/commit/c9b17403e7c2409ac9603a582685b098a399926d)

- **作者**: AuFlow
- **时间**: 2026-07-15T11:49:04Z
- **提交信息**: Fix image URL response for multiple outputs (#30621)

Co-authored-by: AuFlow <AuFlow@users.noreply.github.com>
Co-authored-by: ronnie_zheng <zl19940307@163.com>

### [947a14d](https://github.com/sgl-project/sglang/commit/947a14d617f02b95fc1a04061810a73a2db962d1)

- **作者**: Mick
- **时间**: 2026-07-15T09:42:38Z
- **提交信息**: feat: unify multimodal feature transport (#30904)

### [f2c875d](https://github.com/sgl-project/sglang/commit/f2c875d1c8d1a35392992a9611d4bf5dd84d8e5c)

- **作者**: weireweire
- **时间**: 2026-07-15T07:59:41Z
- **提交信息**: [PD] Route PD server warmup to every DP rank (#30748)

Co-authored-by: weireweire <20922698+weireweire@users.noreply.github.com>

### [5af6702](https://github.com/sgl-project/sglang/commit/5af670284e785ee1193af3239dcf1556e41cf154)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-07-15T07:39:58Z
- **提交信息**: [CI] Lower GLM-5.2 NVFP4 MTP speed threshold (#31289)

### [fbcbe0a](https://github.com/sgl-project/sglang/commit/fbcbe0a986f1c7ef303f133802d8fdf9be4d1b57)

- **作者**: ChangLiu0709
- **时间**: 2026-07-15T07:33:05Z
- **提交信息**: cookbook(deepseek-v4): add MORI disagg backend for AMD + bump MI355X image (#30651)

Co-authored-by: Zijie Xia <zijie.xia@radixark.ai>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: zijiexia <37504505+zijiexia@users.noreply.github.com>

### [241937a](https://github.com/sgl-project/sglang/commit/241937af874d0309c95444bd26e84d0a2c2101db)

- **作者**: McZyWu
- **时间**: 2026-07-15T07:26:44Z
- **提交信息**: [NPU] Determine the topk norm_type through scoring_func (#31107)

Co-authored-by: iridiumine <42236072+iridiumine@users.noreply.github.com>
Co-authored-by: zhaozx-cn <59479021+zhaozx-cn@users.noreply.github.com>
Co-authored-by: sglang-npu-bot <sglangnpu@163.com>

### [dec0836](https://github.com/sgl-project/sglang/commit/dec083630260b239cd49e4735846ae168be2c37a)

- **作者**: Sam Shleifer
- **时间**: 2026-07-15T07:21:31Z
- **提交信息**: Fix processor config loading for object-storage model paths (#31211)

Co-authored-by: Alex Nails <alex.nails@radixark.ai>

### [980acd6](https://github.com/sgl-project/sglang/commit/980acd6eca1a1b0a3265f0a76a145901c8265a20)

- **作者**: sky
- **时间**: 2026-07-15T07:06:37Z
- **提交信息**: Fix MoE TP allreduce to use NCCL symmetric memory via in-pool output allocation (#29007)

Signed-off-by: wangfakang <fakangwang@gmail.com>
Co-authored-by: Brayden Zhong <b8zhong@uwaterloo.ca>

### [41e0b4b](https://github.com/sgl-project/sglang/commit/41e0b4b3695ebd3b653852fa7f69507f5b66127e)

- **作者**: Ma Mingfei
- **时间**: 2026-07-15T07:06:24Z
- **提交信息**: [CPU] add fused input proj for qwen3.5 (#31171)

### [a649b5a](https://github.com/sgl-project/sglang/commit/a649b5a9dba40c6bf05406e55e315356b96c62d2)

- **作者**: Yuan Luo
- **时间**: 2026-07-15T07:04:20Z
- **提交信息**: [KDA] Add FlashInfer SM100 KDA decode + MTP (target_verify) backend (#30113)

Co-authored-by: luoyuan.luo <luoyuan.luo@antgroup.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-07-16
**监控日期**: 2026-07-15
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1230
- **最后更新**: 2026-07-15T18:21:49Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

### 1. 主要更新类型
- **功能新增**：为 CLI（命令行界面）增加了使用本地测试数据的能力。

### 2. 关键变更点及其与项目整体方向的关系
- **变更点**：允许用户通过 CLI 直接指定本地文件作为测试数据输入，而不是依赖远程或内置测试数据。
- **方向关系**：该项目是一个面向 DiT 模型的 PyTorch 原生推理引擎，核心目标是**易用性**与**部署灵活性**。本地测试数据支持降低了用户验证模型或评估性能的门槛，使 CLI 更贴近实际生产环境的使用习惯，符合项目降低用户使用成本的初衷。

### 3. 对项目的影响和潜在意义
- **影响**：提升了 CLI 的实用性，开发者或用户在无需网络或自定义数据准备时，可以快速进行本地验证。
- **潜在意义**：有助于吸引更多用户尝试项目，加速社区反馈；同时为后续更复杂的测试流程（如批量处理、自定义数据集基准测试）奠定基础。

### 4. 值得关注的技术点
- **本地测试数据解析**：推测实现方式可能涉及支持文件路径参数、数据格式自动识别（如图片、张量文件等），以及与已有推理管道的集成。这体现了对用户输入容错性和灵活性的设计考量。

### 5. 基于项目背景，该提交如何影响项目发展
- **促进实验迭代**：结合 README 中提到的缓存、并行、量化、CPU 卸载等优化技术，用户可先用本地小规模数据快速验证效果，再切换到大规模生产数据，缩短了从探索到部署的周期。
- **强化 CLI 生态**：作为推理引擎，CLI 是用户与项目交互的主要入口之一。此更新使 CLI 更完善，有望吸引更多开发者贡献其他 CLI 改进（如输出格式自定义、多模型支持）。
- **契合开源推广**：降低测试数据获取难度，便于其他开发者复现结果或对比性能，有利于扩大项目在 DiT 推理领域的影响力。

## 详细提交记录

### [ad9335f](https://github.com/vipshop/cache-dit/commit/ad9335fdcc7d648b50a7d4ff46b1f25e2abdaf45)

- **作者**: DefTruth
- **时间**: 2026-07-15T08:02:28Z
- **提交信息**: CLI: allow use local test data (#1092)

* CLI: allow use local test data

* CLI: allow use local test data

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-07-16
**监控日期**: 2026-07-15
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 86350
- **最后更新**: 2026-07-15T23:41:02Z

## 提交统计

- **昨日提交总数**: 30
- **提交者数量**: 24
- **主要提交者**: peizhang56, Sage, Giuseppe Grossi

## AI分析总结

以下是基于 vllm-project/vllm 项目背景（提供简单、快速、廉价的 LLM 服务）对昨日提交记录的分析总结：

---

### 1. 主要更新类型

| 类型 | 数量 | 说明 |
|------|------|------|
| **性能优化** | 4 | DSv4 `fused_topk_bias` 1.5~2x 提速、DSv4 HCA 预填充两阶段压缩器、NVFP4 MoE 填充对齐、ROCm fp32 head_dtype fast path |
| **Bug 修复** | 9 | FlashInfer 草稿注意力、并行工具调用崩溃、GLM5 配置、缓存形状验证、草稿 CUDA 图键、Rust JSON 解析、GPTQ qzeros 布局等 |
| **新功能** | 5 | GLM5.2 MoE SP 非 torch 编译路径、Roberta/XLMRoberta Token 分类模型、MM 音频支持、XPU 批量不变内核注册、KV Offload P2P 默认环境变量 |
| **CI/测试** | 6 | DSv4 可选评估、ROCm Docker 重试、CI base 哈希稳定、测试修复、release 注解分割 |
| **文档** | 1 | 池化配置解析说明 |
| **Rust 前端** | 2 | 修复 TLS 超时测试、容忍 JSON 空白符 |

---

### 2. 关键变更点与项目方向关系

- **DSv4 深度优化**（Perf）——直接提升大模型推理吞吐，紧扣“快速”目标。
- **MoE 相关修复与改进**（NVFP4 填充、GLM5.2 非 torch 路径）——增强混合专家模型在 vLLM 上的兼容性与效率。
- **新模型支持**（Roberta/XLMRoberta 分类、GLM5 配置修复）——扩展模型生态，使 vLLM 更“易用”。
- **硬件平台扩展**（ROCm MI350 调优、XPU 内核实录、Helion 内核懒加载与基准）——降低对特定硬件的依赖，推动“廉价”服务。
- **Rust 前端能力增强**（MM 音频支持、JSON 工具调用解析容错）——提升 API 的兼容性和功能完整性。
- **KV Offload 改进**（默认环境变量、DP-rank 控制端口）——优化分布式推理与显存卸载，适合大规模部署。

---

### 3. 对项目的影响和潜在意义

- **性能提升**：`fused_topk_bias` 优化 1.5

## 详细提交记录

### [2dab187](https://github.com/vllm-project/vllm/commit/2dab187f756f2c4549fd5e57019413f3415365a4)

- **作者**: Wentao Ye
- **时间**: 2026-07-15T23:40:55Z
- **提交信息**: [Perf] Optimize `fused_topk_bias` for DSv4, 1.5~2x kernel performance improvement (#47463)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [015b032](https://github.com/vllm-project/vllm/commit/015b0320ded125947ee444314921fc818dc6e5ed)

- **作者**: Giuseppe Grossi
- **时间**: 2026-07-15T23:38:56Z
- **提交信息**: Add giuseppegrossi to rocm label auto cc action (#48643)

Signed-off-by: giuseppegrossi <ggrossi@amd.com>

### [4238b01](https://github.com/vllm-project/vllm/commit/4238b011a76629104b00ecf999d5390b94a1d289)

- **作者**: Wentao Ye
- **时间**: 2026-07-15T23:33:15Z
- **提交信息**: [Feature] Migrate moe sp support to non-torch compiled path for GLM5.2 (#47881)

Signed-off-by: yewentao256 <zhyanwentao@126.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [eb33ff3](https://github.com/vllm-project/vllm/commit/eb33ff34dd6501f23f5be92a5c842d34ab05d7fd)

- **作者**: kliuae
- **时间**: 2026-07-15T23:31:51Z
- **提交信息**: [ROCm][Perf] DSv4 two-stage compressor kernel for HCA prefill (#47718)

Signed-off-by: kliuae <kuanfu.liu@embeddedllm.com>

### [2bd8957](https://github.com/vllm-project/vllm/commit/2bd8957627bfb5668c46f2bc359bef47d371270c)

- **作者**: Mike G
- **时间**: 2026-07-15T21:37:15Z
- **提交信息**: [Bugfix][NVFP4 MoE] Pad gated intermediate to 64 for FlashInfer TRT-LLM shuffle (M%128) (#46880)

Signed-off-by: Mike G <180722391+mikekg@users.noreply.github.com>

### [3034c8d](https://github.com/vllm-project/vllm/commit/3034c8d389edaf4a131c30304eee76bb9aef5022)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-07-15T21:04:54Z
- **提交信息**: [CI][PD] Add optional/nightly DSv4 Disaggregated eval (#42310)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [ecf4aa5](https://github.com/vllm-project/vllm/commit/ecf4aa5ce2ccd4069f12318ca9d3fcef7c9f6257)

- **作者**: Michael Goin
- **时间**: 2026-07-15T19:44:01Z
- **提交信息**: [Bugfix] Fix FlashInfer non-causal draft attention (DFlash/DSpark) on Blackwell (#48167)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [49e777c](https://github.com/vllm-project/vllm/commit/49e777cf08e05ffb017233dc114b0791cb307004)

- **作者**: Micah Williamson
- **时间**: 2026-07-15T19:31:23Z
- **提交信息**: [CI][ROCm] Retry failed Docker build steps once (#48773)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [b7950e7](https://github.com/vllm-project/vllm/commit/b7950e798f2094b1163c22787c0ba2e3231bf01b)

- **作者**: avalliappan-nvidia
- **时间**: 2026-07-15T19:09:00Z
- **提交信息**: [Bugfix] Initialize draft CUDA-graph keys for the native draft_model proposer (#47460)

Signed-off-by: Alagappan Valliappan <avalliappan@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [de100ff](https://github.com/vllm-project/vllm/commit/de100ffb622f435b727177fc751c8de5f41c4d3b)

- **作者**: Taneem Ibrahim
- **时间**: 2026-07-15T18:24:16Z
- **提交信息**: [Docs] Document pooling config resolution (#48497)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [43cd340](https://github.com/vllm-project/vllm/commit/43cd340247f442cfccaa8bef24c0867493af8e7b)

- **作者**: Sage
- **时间**: 2026-07-15T17:48:24Z
- **提交信息**: [Fix] Align OpenAI vllm_xargs value types across request schemas (#48252)

Signed-off-by: Sage Ahrac <sagiahrak@gmail.com>
Signed-off-by: Sage <80211083+sagearc@users.noreply.github.com>

### [1d99f0f](https://github.com/vllm-project/vllm/commit/1d99f0f42152a1459e4b54804b44fc1f989558bb)

- **作者**: Giuseppe Grossi
- **时间**: 2026-07-15T16:55:47Z
- **提交信息**: [ROCm][BugFix] Triton W4A16 handling for GPTQ/AutoGPTQ qzeros layout  (#47770)

Signed-off-by: giuseppegrossi <ggrossi@amd.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [0885b51](https://github.com/vllm-project/vllm/commit/0885b51981d09089e7a067276046b04a20e5b59d)

- **作者**: Andreas Karatzas
- **时间**: 2026-07-15T15:56:56Z
- **提交信息**: [CI][ROCm] Stabilize ci_base hash calculation and image handoff (#48746)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [6036bf1](https://github.com/vllm-project/vllm/commit/6036bf110a9f4d313c38c257ddcf5b8ba4210383)

- **作者**: Xiaohong (Sean) Chen
- **时间**: 2026-07-15T15:43:06Z
- **提交信息**: [Kernel][Helion] Add Helion kernel benchmark script (#48512)

Signed-off-by: Sean Chen <seachen@redhat.com>

### [2fa63e0](https://github.com/vllm-project/vllm/commit/2fa63e0fff41e2f6187a6d3b9bf49b25f9e065f8)

- **作者**: Xiaohong (Sean) Chen
- **时间**: 2026-07-15T15:42:46Z
- **提交信息**: [Kernel][Helion] Helion kernel lazy registration (#48264)

Signed-off-by: Sean Chen <seachen@redhat.com>

### [61141ed](https://github.com/vllm-project/vllm/commit/61141ed265bfef41a0ca19e992567ea980919b96)

- **作者**: Tomasz Zielinski
- **时间**: 2026-07-15T15:19:44Z
- **提交信息**: [Hardware][XPU] Register batch-invariant kernels for XPU (#41934)

Signed-off-by: tzielinski-habana <tomasz.zielinski@intel.com>
Signed-off-by: Tomasz Zielinski <85164140+tzielinski-habana@users.noreply.github.com>
Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>
Co-authored-by: Chendi.Xue <chendi.xue@intel.com>

### [05eed72](https://github.com/vllm-project/vllm/commit/05eed72aec6c05e6d500c7276b47f7652bb37af6)

- **作者**: peizhang56
- **时间**: 2026-07-15T15:03:48Z
- **提交信息**: [ROCm] Re-enable cudagraph memory profiling, captured on the current stream (#48526)

Signed-off-by: pei.zhang <pei.zhang@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [5810e88](https://github.com/vllm-project/vllm/commit/5810e884f11875b46fbae0871754d855d8891105)

- **作者**: Gopala-Krishna Char
- **时间**: 2026-07-15T14:30:33Z
- **提交信息**: [Model] Add RobertaForTokenClassification / XLMRobertaForTokenClassification (#47991)

Signed-off-by: krishy91 <crgkc.r@gmail.com>

### [615834e](https://github.com/vllm-project/vllm/commit/615834ee584fd6395f1ac4d2257cb29c47895295)

- **作者**: liranschour
- **时间**: 2026-07-15T12:22:56Z
- **提交信息**: [KVOffload][P2P] Well-known default host/port env vars and per-DP-rank control port (#47636)

Signed-off-by: Liran Schour <lirans@il.ibm.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [5811ed6](https://github.com/vllm-project/vllm/commit/5811ed6a05158b5d2f953e3b8d3e3082ee36e635)

- **作者**: Chaojun Zhang
- **时间**: 2026-07-15T11:53:47Z
- **提交信息**: [Test][kv_offload] Fix flaky drain() helper in test_fs_tier.py (#48545)

Signed-off-by: Chaojun Zhang <chaojun.zhang@intel.com>

### [1b30ae4](https://github.com/vllm-project/vllm/commit/1b30ae4ca403588f1df37901d3b530d1fe5c48c4)

- **作者**: Tahsin Tunan
- **时间**: 2026-07-15T11:05:38Z
- **提交信息**: [Rust Frontend] Fix flaky `tls_handshake_timeout_drops_silent_client` test (#47873)

Signed-off-by: Tahsin Tunan <tahsintunan@gmail.com>

### [4e04bcb](https://github.com/vllm-project/vllm/commit/4e04bcbce6f0852017d26660dd2d027de9bed7d5)

- **作者**: Tahsin Tunan
- **时间**: 2026-07-15T11:03:37Z
- **提交信息**: [Rust Frontend] Tolerate whitespace before the outer brace in JSON tool-call parsers (#48034)

Signed-off-by: Tahsin Tunan <tahsintunan@gmail.com>

### [66b6c68](https://github.com/vllm-project/vllm/commit/66b6c684ab5a32dabcd2e69daaa60ff5d5198392)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-07-15T10:26:02Z
- **提交信息**: [PD][Bugfix] Fix validation of cache shape for attn backends enforcing different `kernel_block_size` (#48125)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [c0302d9](https://github.com/vllm-project/vllm/commit/c0302d949740321c145b6b19852706b6f1b43854)

- **作者**: Mahad Rehman
- **时间**: 2026-07-15T10:01:17Z
- **提交信息**: [Bugfix] Fix parallel_tool_calls=null crash in Responses API from_request() (#48098)

Signed-off-by: mahadrehmann <mahadrehman04@gmail.com>
Signed-off-by: Mahad Rehman <114791389+mahadrehmann@users.noreply.github.com>
Co-authored-by: muhammadfawaz1 <135441198+professorsab@users.noreply.github.com>
Co-authored-by: Copilot Autofix powered by AI <175728472+Copilot@users.noreply.github.com>
Co-authored-by: Chauncey <chaunceyjiang@gmail.com>

### [313fae3](https://github.com/vllm-project/vllm/commit/313fae3e89daeb7f5183064912933c328bbb6e48)

- **作者**: Jee Jee Li
- **时间**: 2026-07-15T09:55:39Z
- **提交信息**: [Bugfix] Fix GLM5 config (#48711)

Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>

### [7aab6e2](https://github.com/vllm-project/vllm/commit/7aab6e2684894fb1dba17cae117f8e84c5a7bbb3)

- **作者**: Turner Jabbour
- **时间**: 2026-07-15T08:18:22Z
- **提交信息**: [ROCm][Bugfix] Enable the fp32 head_dtype torch.mm fast path on ROCm (#48688)

Signed-off-by: Turner Jabbour <doubleujabbour@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [9dd2e72](https://github.com/vllm-project/vllm/commit/9dd2e72828c13bf088403ed789c4672ffef99564)

- **作者**: Aarushi Jain
- **时间**: 2026-07-15T07:20:34Z
- **提交信息**: fix flaky multi example connector consistency (#48206)

Signed-off-by: aarushjain29 <aarushi.jain2@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [d119beb](https://github.com/vllm-project/vllm/commit/d119beb1b90804f55e5c1d70f1c1961b8a852bd1)

- **作者**: Giuseppe Grossi
- **时间**: 2026-07-15T07:18:09Z
- **提交信息**: [ROCm] Add tuned selective_state_update config for AMD MI350 (#48159)

Signed-off-by: Giuseppe Grossi <ggrossi@amd.com>

### [12a8057](https://github.com/vllm-project/vllm/commit/12a8057bfe5b5fc327f9f32de296ac3b3cbc9830)

- **作者**: Kevin H. Luu
- **时间**: 2026-07-15T07:00:52Z
- **提交信息**: [CI/Build] Split release artifact annotations by type (#48600)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [e281ac6](https://github.com/vllm-project/vllm/commit/e281ac663a7b772f8b988f270521cd1155f12aa3)

- **作者**: Bugen Zhao
- **时间**: 2026-07-15T07:00:17Z
- **提交信息**: [Rust Frontend] Integrate MM audio support (#48554)

Co-authored-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Signed-off-by: Isotr0py <Isotr0py@outlook.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-07-16
**监控日期**: 2026-07-15
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 5588
- **最后更新**: 2026-07-15T18:01:27Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Shi Boao Bowie

## AI分析总结

根据提供的仓库 `vllm-project/vllm-omni` 的提交记录与 README 背景，以下是昨日更新的要点分析：

### 1. 主要更新类型
- **重构（Refactor）**：属于代码结构优化与模块化改进，为后续 OutputProcessor 系列更新（1/8）打下基础。

### 2. 关键变更点及其与项目整体方向的关系
- **清理多模态负载累积**：移除冗余或混乱的代码，将负载（payload）相关的逻辑从分散位置集中到 `MultimodalPayload` 类中。
- **目录结构重构**：调整文件组织结构，使代码更清晰。
- **关系**：项目方向是提供“简单、快速、便宜的全模态模型服务”。重构动作直接服务于长期的可维护性与扩展性，使得未来增加新模态（如视频、音频流等）时更容易集成，符合“omni-modality”目标。

### 3. 对项目的影响和潜在意义
- **影响**：短期内不影响用户功能，但提升了内部代码质量，降低了后续开发技术债。
- **潜在意义**：
  - 为即将到来的 OutputProcessor 完整系列（共8个）铺路，预示输出处理逻辑将迎来系统性优化。
  - 将负载逻辑集中到 `MultimodalPayload` 类后，可统一管理多模态数据流，可能带来性能提升（减少重复计算）和错误率下降。

### 4. 值得关注的技术点
- **MultimodalPayload 类设计**：负载逻辑的集中化意味着该类可能成为多模态数据结构的核心抽象，其接口设计将影响所有与多模态交互的模块（如编码器、解码器、调度器）。
- **目录重构范围**：未具体说明变更了哪些目录，但通常涉及 `vllm/multimodal/` 或 `output_processor/` 等核心模块，值得观察后续提交对文件路径的调整。

### 5. 基于项目背景的发展影响
- **推动代码成熟度**：项目处于快速发展阶段（考虑 PR 编号 #4980），重构表明团队在加速功能迭代的同时关注工程质量，有利于降低社区贡献门槛。
- **支撑“多模态服务”易用性**：通过模块化清理，未来用户自定义扩展（如添加新模态的处理逻辑）将更加直观，契合“easy”定位。
- **潜在性能优化**：集中后的负载逻辑可能允许向量化或缓存优化，有助于实现“fast”和“cheap”的目标。

**总结**：此次提交是 OutputProcessor 重构系列的开端，旨在清理多模态负载管理并重构目录结构，为后续输出处理的大规模改进奠定基础。虽然表面是内部代码优化，但直接影响项目长期的可扩展性、性能与维护性，符合 vllm-omni 全模态服务的技术路线。

## 详细提交记录

### [a432b8a](https://github.com/vllm-project/vllm-omni/commit/a432b8a325846a63c87f23b6e5731a67dd44771b)

- **作者**: Shi Boao Bowie
- **时间**: 2026-07-15T07:50:19Z
- **提交信息**: [Refactor][OutputProcessor 1/8]: clean up multimodal payload accumulation and move payload logic into MultimodalPayload & directory refactor (#4980)

Signed-off-by: Boao Shi <aoibosh@connect.hku.hk>
Signed-off-by: bjf-frz <frz123db@gmail.com>
Co-authored-by: bjf-frz <frz123db@gmail.com>

---
