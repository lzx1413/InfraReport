# GitHub Stars 合并报告 - 2026-07-01

**合并日期**: 2026-07-02
**监控日期**: 2026-07-01
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


**报告日期**: 2026-07-02
**监控日期**: 2026-07-01
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2052
- **最后更新**: 2026-07-01T09:47:46Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-07-02
**监控日期**: 2026-07-01
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2453
- **最后更新**: 2026-07-01T18:19:22Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-07-02
**监控日期**: 2026-07-01
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2153
- **最后更新**: 2026-07-01T19:17:19Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-07-02
**监控日期**: 2026-07-01
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5887
- **最后更新**: 2026-07-01T23:47:14Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 2
- **主要提交者**: Guangyun Han, Elias Stehle

## AI分析总结

好的，以下是对仓库 `flashinfer-ai/flashinfer` 昨日提交记录的分析总结：

---

### 1. 主要更新类型
- **新功能 (feat)**：新增 `varlen` 变长 Top-K 变换基准测试（`bench_topk.py`）
- **性能优化 (perf)**：优化 SM90 (Hopper) 的 `cp delta rule`，融合 QK 与逆变 epilogue，移除冗余缓冲区清零
- **Bug 修复 (fix)**：限制旋转缓冲区大小，避免大问题尺寸时内存溢出 (OOM)

---

### 2. 关键变更点及其与项目方向的关系

| 提交 | 关键变更 | 与项目整体方向的关系 |
|------|----------|----------------------|
| `651d877` | 为 `top_k_page_table_transform`、`top_k_ragged_transform` 增加变长模式基准测试，支持 `decode`（单行变长）和 `prefill`（因果单调增长长度）两种场景，并添加 `length-dist`、`varlen-k`、`varlen-q-len` 等 CLI 标志。 | **加强生产场景覆盖**：FlashInfer 定位为推理高性能 GPU 内核库，变长稀疏注意力（如 DeepSeek-V3.2 DSA）是前沿生产需求。此提交使基准测试更贴近真实负载（行间不平衡、短路径优化），便于后续内核优化。 |
| `8fc7f07` | 在 SM90 内核中融合 QK 与逆变 epilogue，减少内核调用和中间缓冲区访问；避免不必要的缓冲区清零。 | **性能极致优化**：针对 Hopper 架构微调，是 FlashInfer 核心竞争力（超越 FLA/Triton 数倍）的延续。基于 H100 上的详细数据（表内加速比 1.07x ~ 5.78x）验证了端到端约 10% 提升。 |
| `cec0791` | 限制旋转缓冲区数量（`rotate_buffer`）以避免 `--iters` 过大时 OOM。 | **提升基准测试健壮性**：保证用户在大问题尺寸或多次迭代下不会意外崩溃，属于稳定性改进，间接支持项目长期可靠性。 |

---

### 3. 对项目的影响和潜在意义
- **定性基准对齐生产**：`varlen` 基准测试填补了目前统一长度基准测试的盲区。未来其他算子（如注意力、采样）也可能借鉴这种区分 `decode/prefill`、支持变长分布的基准模式，提升 FlashInfer 在**真实推理服务**中的可复现性和调优能力。
- **性能标杆进一步拔高**：SM90 优化后，在各类模型（Qwen3.5 家族 397B~0.8B）和 TP 配置下，FlashInfer 相比 FLA/Triton 的加速比达到 **1.07x 至 5.93x**，巩固了其在 Hopper 上的领先地位，也为后续 Blackwell (SM100) 内核提供基线。
- **稳定性增强**：修复 OOM bug 避免用户在大规模基准测试时流失，提升项目成熟度。

---

### 4. 值得关注的技术点
- **变长基准设计**：
  - 区分 `decode`（单行独立长度分布）和 `prefill`（因果单调增长，通过 `row_to_batch` 映射），精准模拟生产稀疏注意力。
  - 引入 `triv%`（`length <= k` 的行比例）和 `length stats`，使不同长度分布的跑分可比。
  - 保留确定性模式 (`--deterministic`) 和 tie-break 选项，支持结果可复现。
  - `torch(mask)` 基线特意将 mask 放到计时区域外，避免不公平地惩罚 torch（因内核直接读取 `lengths` 无需 materialize mask）。
- **SM90 融合技巧**：将 QK 与 inversion epilogue 融合减少了全局/共享内存访问；无意义清零的移除降低延迟。
- **旋转

## 详细提交记录

### [651d877](https://github.com/flashinfer-ai/flashinfer/commit/651d877827a825d73bd304e7f54bff0649a69904)

- **作者**: Elias Stehle
- **时间**: 2026-07-01T21:59:19Z
- **提交信息**: feat(bench): adds variable-length top-k transform benchmark for decode/prefill (#3772)

## 📌 Description

Adds a `varlen` benchmark mode to `benchmarks/bench_topk.py` that
exercises the fused top-k transform APIs (`top_k_page_table_transform`,
`top_k_ragged_transform`) with realistic per-row variable segment
lengths, instead of the fixed `lengths == seq_len` that the existing
transform benchmarks use for every row.

**Why:** production sparse-attention top-k (e.g. DeepSeek-V3.2 DSA,
ragged/paged KV) selects top-k over a per-row valid window described by
`lengths` (and a `row_to_batch` mapping). The existing benchmarks always
pass a uniform length, which hides the behaviors that matter most in
production: load imbalance across rows/CTAs, the trivial `length <= k`
short-circuit, and multi-CTA scheduling. This mode gives a realistic
comparison to production workloads.

**What it adds:**

- Two regimes:
- `decode`: one row per request; independent context lengths drawn from
a distribution (`uniform`, `lognormal` short-skewed serving mix,
`bimodal` short/long mix that stresses imbalance and the trivial path).
- `prefill` (`causal`): `q_len` rows per request with causal-monotonic
lengths that grow across query positions, wired via a `row_to_batch`
mapping.
- Baselines per case (non-deterministic mode): FlashInfer default,
FlashInfer `clusters` (SM100 only), and `torch.topk` over a tensor that
is masked to the valid window once, outside the timed region, so it
isolates selection cost rather than masking overhead.
- Deterministic and tie-break parity with the existing top-k ops, via
the shared `--deterministic` and `--tie-break` flags: `--deterministic`
also times the deterministic path and reports its slowdown versus
non-deterministic, and `--tie-break` (which implies deterministic) adds
tie-small and tie-large columns. The `clusters` column is omitted in
these modes because that path is non-deterministic only.
- Ragged `offsets` are built as the exclusive prefix-sum of `lengths` (a
packed KV layout); the value does not affect timing, so this only
affects realism.
- Reports per-case length stats (`min`/`mean`/`max`) and `triv%`
(fraction of rows with `length <= k`) so runs with different length
distributions stay comparable.
- New flags: `--op varlen` (also included in `--op all`),
`--length-dist`, `--varlen-k`, `--varlen-q-len`. Length draws use a
fixed-seed generator for reproducibility, and per-case
`RuntimeError`/OOM is caught and reported.

No library or kernel code is changed; this is a benchmark-script-only
change.

## 🔍 Related Issues

N/A. Motivated by variable-length sparse-attention top-k (DeepSeek-V3.2
DSA).

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

> Benchmark-only change (no pytest coverage). Variable-length
correctness for these APIs is already covered in
`tests/utils/test_topk.py` (e.g.
`test_page_table_transform_variable_lengths`,
`test_ragged_transform_variable_lengths`,
`test_top_k_transform_with_row_starts`), which pass on B200 (SM100).
Smoke-tested on B200 via `python benchmarks/bench_topk.py --op varlen`,
including the `--deterministic` and `--tie-break` modes.

## Reviewer Notes

- Scoped as a separate `varlen` op rather than extending the existing
fixed-length transform sweeps, so the scaling numbers are preserved and
the SGLang-comparison paths (which assume uniform lengths) are
untouched.
- The `torch(mask)` baseline masks invalid positions outside the timed
region on purpose; including the mask would unfairly penalize torch,
since the kernel reads `lengths` directly without materializing a masked
tensor.
- `Clusters` column is omitted off SM100 (the clusters path requires
Blackwell) and under `--deterministic`/`--tie-break` (the clusters path
runs only in the non-deterministic mode).
- Memory note: the prefill regime expands rows (`num_requests x q_len`),
so the heaviest default case (`r16 x q128 x l131072`, fp32) allocates
about 2 GB for scores plus a matching masked copy. Fine on datacenter
GPUs and OOM-guarded; happy to trim the default grid or make the batch
and `max_len` sets CLI-configurable if preferred.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

## Summary by CodeRabbit

* **New Features**
* Added a new variable-length benchmark mode for top-k operations to
better reflect realistic per-request workloads.
* Extended CLI options to select the new mode and configure length
distribution, query length, and top-k.

* **Benchmarking Improvements**
* Added detailed generation of variable-length inputs and summary
statistics for each benchmark case.
* Benchmarks now compare page-table and ragged-style transforms, with
optional cluster-path timing when supported.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [8fc7f07](https://github.com/flashinfer-ai/flashinfer/commit/8fc7f079203cfa6242d1fe250ef7028b22c5efd2)

- **作者**: Guangyun Han
- **时间**: 2026-07-01T14:44:27Z
- **提交信息**: perf: optimize sm90 cp delta rule (#3788)

## 📌 Description

1. Fused qk and inversion epilogue.
2. Removed unnecessary intermediate buffer zeroing.

## 🔍 Related Issues

Similar optimization has been integrated in
e9ad55ce884e5d87c15a3a0e853b11b42ff5d245
93050535021a9421781f7b5b85259527da4d762e and
171e5edbcc2ac1573a14dc5ffea7f13590d646c8

## 🚀 Pull Request Checklist

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

Compared to record in #3481, it is about ~10% E2E improvement.

```
GPU: NVIDIA H100 80GB HBM3 [Hopper (SM90)]
Models: Qwen3.5 family (397B, 122B, 35B, 27B, 9B, 4B, 2B, 0.8B), d=128

Heads            Seqlens           h_qk  h_v        FI Hopper (SM90)   TFLOPS  FLA/Triton   Speedup
---------------------------------------------------------------------------------------------------
397B/122B TP8    1x65536              2    8                  0.449ms    76.5      2.006ms     4.47x +
397B/122B TP8    1x32768              2    8                  0.284ms    60.6      0.998ms     3.52x +
397B/122B TP8    1x16384              2    8                  0.197ms    43.7      0.505ms     2.56x +
397B/122B TP8    1x8192               2    8                  0.153ms    28.2      0.258ms     1.69x +
397B/122B TP8    1x4096               2    8                  0.102ms    21.0      0.143ms     1.40x +
397B/122B TP8    1x2048               2    8                  0.080ms    13.4      0.086ms     1.07x +
397B/122B TP8    6144+2048            2    8                  0.136ms    31.6      0.221ms     1.63x +
397B/122B TP8    4096+4096            2    8                  0.120ms    35.7      0.184ms     1.53x +
397B/122B TP8    2048+6144            2    8                  0.136ms    31.6      0.221ms     1.63x +
397B/122B TP8    1024+7168            2    8                  0.146ms    29.5      0.241ms     1.65x +
397B/122B TP8    2048x4               2    8                  0.114ms    37.8      0.149ms     1.31x +
397B/122B TP8    1024x8               2    8                  0.128ms    33.7      0.155ms     1.22x +
397B/122B TP8    8192x8               2    8                  0.460ms    74.8      1.087ms     2.37x +
397B/122B TP8    8192x16              2    8                  0.370ms   185.8      2.140ms     5.78x +
397B/122B TP8    8192x32              2    8                  0.802ms   171.5      4.232ms     5.28x +

397B/122B TP4    1x65536              4   16                  0.782ms    87.9      2.744ms     3.51x +
397B/122B TP4    1x32768              4   16                  0.424ms    81.1      1.388ms     3.28x +
397B/122B TP4    1x16384              4   16                  0.252ms    68.1      0.707ms     2.80x +
397B/122B TP4    1x8192               4   16                  0.164ms    52.2      0.361ms     2.19x +
397B/122B TP4    1x4096               4   16                  0.119ms    36.0      0.187ms     1.56x +
397B/122B TP4    1x2048               4   16                  0.084ms    25.6      0.107ms     1.28x +
397B/122B TP4    6144+2048            4   16                  0.156ms    55.1      0.324ms     2.08x +
397B/122B TP4    4096+4096            4   16                  0.150ms    57.3      0.287ms     1.91x +
397B/122B TP4    2048+6144            4   16                  0.157ms    54.6      0.324ms     2.06x +
397B/122B TP4    1024+7168            4   16                  0.162ms    53.1      0.343ms     2.12x +
397B/122B TP4    2048x4               4   16                  0.153ms    56.1      0.293ms     1.92x +
397B/122B TP4    1024x8               4   16                  0.058ms   147.4      0.305ms     5.24x +
397B/122B TP4    8192x8               4   16                  0.368ms   186.8      2.181ms     5.93x +
397B/122B TP4    8192x16              4   16                  0.792ms   173.5      4.351ms     5.49x +
397B/122B TP4    8192x32              4   16                  1.641ms   167.5      8.707ms     5.31x +

397B/122B TP2    1x65536              8   32                  1.549ms    88.7      4.408ms     2.84x +
397B/122B TP2    1x32768              8   32                  0.771ms    89.1      2.202ms     2.86x +
397B/122B TP2    1x16384              8   32                  0.411ms    83.6      1.091ms     2.66x +
397B/122B TP2    1x8192               8   32                  0.238ms    72.3      0.554ms     2.33x +
397B/122B TP2    1x4096               8   32                  0.150ms    57.1      0.288ms     1.91x +
397B/122B TP2    1x2048               8   32                  0.105ms    40.8      0.152ms     1.45x +
397B/122B TP2    6144+2048            8   32                  0.238ms    72.3      0.559ms     2.35x +
397B/122B TP2    4096+4096            8   32                  0.236ms    72.7      0.560ms     2.37x +
397B/122B TP2    2048+6144            8   32                  0.240ms    71.5      0.558ms     2.32x +
397B/122B TP2    1024+7168            8   32                  0.256ms    67.1      0.561ms     2.19x +
397B/122B TP2    2048x4               8   32                  0.104ms   165.7      0.571ms     5.51x +
397B/122B TP2    1024x8               8   32                  0.113ms   152.0      0.592ms     5.24x +
397B/122B TP2    8192x8               8   32                  0.742ms   185.2      4.446ms     5.99x +
397B/122B TP2    8192x16              8   32                  1.656ms   165.9      8.935ms     5.39x +
397B/122B TP2    8192x32              8   32                  3.211ms   171.2     18.081ms     5.63x +

397B/122B TP1    1x65536             16   64                  3.022ms    91.0      8.633ms     2.86x +
397B/122B TP1    1x32768             16   64                  1.541ms    89.2      4.273ms     2.77x +
397B/122B TP1    1x16384             16   64                  0.747ms    91.9      2.090ms     2.80x +
397B/122B TP1    1x8192              16   64                  0.404ms    85.0      1.045ms     2.59x +
397B/122B TP1    1x4096              16   64                  0.231ms    74.3      0.536ms     2.32x +
397B/122B TP1    1x2048              16   64                  0.143ms    60.0      0.279ms     1.94x +
397B/122B TP1    6144+2048           16   64                  0.281ms   122.2      1.049ms     3.73x +
397B/122B TP1    4096+4096           16   64                  0.192ms   178.9      1.055ms     5.49x +
397B/122B TP1    2048+6144           16   64                  0.282ms   122.0      1.059ms     3.76x +
397B/122B TP1    1024+7168           16   64                  0.325ms   105.7      1.060ms     3.26x +
397B/122B TP1    2048x4              16   64                  0.203ms   169.4      1.068ms     5.27x +
397B/122B TP1    1024x8              16   64                  0.220ms   156.3      1.089ms     4.95x +
397B/122B TP1    8192x8              16   64                  1.644ms   167.2      8.676ms     5.28x +
397B/122B TP1    8192x16             16   64                  3.204ms   171.6     17.469ms     5.45x +
397B/122B TP1    8192x32             16   64                  6.415ms   171.4     35.823ms     5.58x +

35B/9B/4B TP1    1x65536             16   32                  1.623ms    84.7      4.409ms     2.72x +
35B/9B/4B TP1    1x32768             16   32                  0.806ms    85.3      2.203ms     2.73x +
35B/9B/4B TP1    1x16384             16   32                  0.423ms    81.2      1.089ms     2.57x +
35B/9B/4B TP1    1x8192              16   32                  0.246ms    69.9      0.553ms     2.25x +
35B/9B/4B TP1    1x4096              16   32                  0.155ms    55.5      0.288ms     1.86x +
35B/9B/4B TP1    1x2048              16   32                  0.108ms    39.7      0.153ms     1.41x +
35B/9B/4B TP1    6144+2048           16   32                  0.248ms    69.4      0.559ms     2.26x +
35B/9B/4B TP1    4096+4096           16   32                  0.244ms    70.3      0.558ms     2.29x +
35B/9B/4B TP1    2048+6144           16   32                  0.249ms    69.0      0.562ms     2.26x +
35B/9B/4B TP1    1024+7168           16   32                  0.263ms    65.4      0.562ms     2.14x +
35B/9B/4B TP1    2048x4              16   32                  0.105ms   164.2      0.571ms     5.46x +
35B/9B/4B TP1    1024x8              16   32                  0.115ms   149.4      0.594ms     5.17x +
35B/9B/4B TP1    8192x8              16   32                  0.820ms   167.5      4.462ms     5.44x +
35B/9B/4B TP1    8192x16             16   32                  1.707ms   161.1      8.931ms     5.23x +
35B/9B/4B TP1    8192x32             16   32                  3.226ms   170.4     18.087ms     5.61x +

27B TP1          1x65536             16   48                  2.614ms    78.9      6.524ms     2.50x +
27B TP1          1x32768             16   48                  1.319ms    78.2      3.280ms     2.49x +
27B TP1          1x16384             16   48                  0.670ms    76.9      1.607ms     2.40x +
27B TP1          1x8192              16   48                  0.368ms    69.9      0.805ms     2.18x +
27B TP1          1x4096              16   48                  0.210ms    61.4      0.417ms     1.99x +
27B TP1          1x2048              16   48                  0.132ms    48.8      0.229ms     1.73x +
27B TP1          6144+2048           16   48                  0.279ms    92.4      0.822ms     2.95x +
27B TP1          4096+4096           16   48                  0.191ms   135.2      0.844ms     4.43x +
27B TP1          2048+6144           16   48                  0.279ms    92.5      0.835ms     3.00x +
27B TP1          1024+7168           16   48                  0.321ms    80.2      0.825ms     2.57x +
27B TP1          2048x4              16   48                  0.199ms   129.5      0.824ms     4.14x +
27B TP1          1024x8              16   48                  0.167ms   154.4      0.839ms     5.03x +
27B TP1          8192x8              16   48                  1.238ms   166.6      6.571ms     5.31x +
27B TP1          8192x16             16   48                  2.421ms   170.3     13.185ms     5.45x +
27B TP1          8192x32             16   48                  4.838ms   170.5     26.763ms     5.53x +

2B/0.8B TP1      1x65536             16   16                  0.879ms    78.2      2.755ms     3.13x +
2B/0.8B TP1      1x32768             16   16                  0.482ms    71.3      1.393ms     2.89x +
2B/0.8B TP1      1x16384             16   16                  0.284ms    60.5      0.701ms     2.47x +
2B/0.8B TP1      1x8192              16   16                  0.185ms    46.4      0.360ms     1.95x +
2B/0.8B TP1      1x4096              16   16                  0.131ms    32.9      0.187ms     1.43x +
2B/0.8B TP1      1x2048              16   16                  0.086ms    24.9      0.107ms     1.24x +
2B/0.8B TP1      6144+2048           16   16                  0.177ms    48.5      0.324ms     1.83x +
2B/0.8B TP1      4096+4096           16   16                  0.171ms    50.2      0.287ms     1.68x +
2B/0.8B TP1      2048+6144           16   16                  0.177ms    48.4      0.324ms     1.83x +
2B/0.8B TP1      1024+7168           16   16                  0.181ms    47.4      0.341ms     1.89x +
2B/0.8B TP1      2048x4              16   16                  0.170ms    50.5      0.294ms     1.73x +
2B/0.8B TP1      1024x8              16   16                  0.062ms   139.3      0.305ms     4.94x +
2B/0.8B TP1      8192x8              16   16                  0.380ms   180.6      2.179ms     5.73x +
2B/0.8B TP1      8192x16             16   16                  0.852ms   161.4      4.356ms     5.11x +
2B/0.8B TP1      8192x32             16   16                  1.711ms   160.7      8.707ms     5.09x +

Sym h32          1x65536             32   32                  1.734ms    79.3      4.405ms     2.54x +
Sym h32          1x32768             32   32                  0.879ms    78.2      2.208ms     2.51x +
Sym h32          1x16384             32   32                  0.472ms    72.9      1.089ms     2.31x +
Sym h32          1x8192              32   32                  0.272ms    63.2      0.552ms     2.03x +
Sym h32          1x4096              32   32                  0.172ms    50.0      0.287ms     1.67x +
Sym h32          1x2048              32   32                  0.117ms    36.8      0.152ms     1.30x +
Sym h32          6144+2048           32   32                  0.274ms    62.7      0.561ms     2.05x +
Sym h32          4096+4096           32   32                  0.274ms    62.8      0.559ms     2.05x +
Sym h32          2048+6144           32   32                  0.278ms    61.7      0.559ms     2.01x +
Sym h32          1024+7168           32   32                  0.287ms    59.8      0.560ms     1.95x +
Sym h32          2048x4              32   32                  0.107ms   160.4      0.572ms     5.34x +
Sym h32          1024x8              32   32                  0.120ms   142.8      0.593ms     4.93x +
Sym h32          8192x8              32   32                  0.849ms   161.9      4.453ms     5.25x +
Sym h32          8192x16             32   32                  1.760ms   156.2      8.929ms     5.07x +
Sym h32          8192x32             32   32                  3.374ms   162.9     18.091ms     5.36x +
```

### [cec0791](https://github.com/flashinfer-ai/flashinfer/commit/cec079139d0eb986d950929058411cfff2e16305)

- **作者**: Guangyun Han
- **时间**: 2026-07-01T07:08:50Z
- **提交信息**: fix: limit rotating buffer to avoid OOM on large problem size (#3662)

## 📌 Description

Unlimited number of rotating buffer caused OOM it `--iters` is large
enough. Limiting it to avoid the issue.

## 🔍 Related Issues

## 🚀 Pull Request Checklist
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


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

## Release Notes

* **Chores**
* Optimized benchmark memory allocation and buffer rotation logic to
improve performance testing efficiency.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-07-02
**监控日期**: 2026-07-01
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3791
- **最后更新**: 2026-07-01T22:33:53Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-07-02
**监控日期**: 2026-07-01
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 33962
- **最后更新**: 2026-07-01T23:16:00Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: apolinário, Hz_Zhang

## AI分析总结

好的，以下是对 huggingface/diffusers 仓库昨日两条提交记录的分析总结，结合项目背景（扩散模型库，提供模型加载、管道、训练微调功能）。

---

### 1. 主要更新类型
- **Bug 修复 + 代码重构 / 测试增强**（提交 `1ffa423`）：修复 Ovis 图像管道的多处问题，并添加完整的管道测试。
- **新功能新增**（提交 `26ec30e`）：为 Ideogram 4 模型新增 DreamBooth LoRA 训练脚本及配套文档。

### 2. 关键变更点与项目方向的关系
- **`ovis_image` 管道修复**：  
  - 修复 `guidance_scale`、`max_sequence_length`、批处理 CFG（`batched CFG`）和预计算嵌入（`precomputed embeds`）的错误，同时将测试从简单版本升级到完整的 `PipelineTesterMixin`。  
  - 方向关联：扩散库注重管道的一致性和可靠性，这些修复确保用户在使用 Ovis 模型时获得正确的条件生成和高效的批处理能力；完善测试也提升了库质量。

- **`Ideogram4 DreamBooth LoRA` 训练脚本**：  
  - 新增独立的训练示例，支持 flow-matching、双 transformer 架构、Qwen3-VL 文本编码器，以及 nf4 QLoRA 和 fp8 基底训练。  
  - 方向关联：diffusers 积极跟进前沿模型（Ideogram 4），并提供开箱即用的训练工具，降低用户微调门槛。LoRA 和 QLoRA 支持符合社区对高效个性化微调的需求。

### 3. 对项目的影响与潜在意义
- **稳定性提升**：Ovis 管道修复消除了几个影响生成质量的 bug，预计算嵌入的完善使 pipeline 更易于集成到生产环境。
- **模型生态扩展**：Ideogram 4 训练脚本的加入使 diffusers 支持更多闭环模型，尤其是采用了 `dual transformer` 和非传统架构（flow-matching）的模型，有助于保持库的领先地位。
- **社区贡献友好**：Co-authored-by 中多次提及 Claude Opus 等工具，体现 Hugging Face 鼓励使用 AI 辅助开发，同时严格的 review 流程（如提及 `#13630` issue）保证了代码质量。

### 4. 值得关注的技术点
- **`batched CFG`（批处理无分类器引导）**：对于 Ovis 管道，修复批处理 CFG 意味着在推理时能同时计算正负条件，提升吞吐量而不改动接口。
- **`precomputed embeds`**：`encode_prompt` 同时返回正负嵌入，采用类似 PixArt 的 `z_image` 约定，简化了外部预计算嵌入的使用流程。
- **`--disable_training_autocast`**：Ideogram 4 训练中，显式禁用 `autocast` 避免前向传播被破坏，这与传统 LoRA 训练不同，值得其他新模型参考。
- **结构化 JSON 字幕 + `--upsample_prompt`**：训练脚本支持更灵活的数据格式，便于处理复杂描述。
- **`PipelineTesterMixin`**：标准化的管道测试 mixin 减少了测试样板代码，提高了测试覆盖率。

### 5. 结合项目背景（Diffusers 定位）看影响
- Diffusers 目标是成为社区扩散模型的统一入口，不仅提供推理管道，更要提供训练微调工具。  
- **Ovis 管道修复**强化了“稳定可靠”的承诺，尤其对于较新的模型（Ovis 可能相对小众），修复带来更好的用户体验。  
- **Ideogram 4 训练脚本**证明了 Diffusers 愿意及时适配非 Stable Diffusion 系的先进模型（Ideogram

## 详细提交记录

### [1ffa423](https://github.com/huggingface/diffusers/commit/1ffa4236a48af8d1d2eaeed6c84027af19acfc39)

- **作者**: Hz_Zhang
- **时间**: 2026-07-01T23:15:50Z
- **提交信息**: ovis_image: fix guidance_scale / max_sequence_length / batched CFG / precomputed embeds + add pipeline test (#13944)

* ovis_image: fix guidance_scale / max_sequence_length / batched-CFG / precomputed embeds + add pipeline test

Addresses items 3/4/5/6/7 of #13630.

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

* ovis_image: complete pipeline review (#13630)

- thread joint_attention_kwargs through the transformer forward + blocks
  (item 2) and pass it from the pipeline's transformer calls.
- encode_prompt now returns both positive and negative embeds (the z_image /
  PixArt convention) so precomputed embeds work end-to-end and the prompt is
  encoded in a single call.
- switch the pipeline test to the full PipelineTesterMixin.

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

* ovis_image: remove now-unused tokenizer_max_length

The pipeline computes max_length inline from max_sequence_length, so the attribute is dead. Addresses review feedback.

---------

Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>
Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

### [26ec30e](https://github.com/huggingface/diffusers/commit/26ec30e8add5faec242aed6a4bfe0d23a6e9befd)

- **作者**: apolinário
- **时间**: 2026-07-01T15:10:33Z
- **提交信息**: Ideogram4 lora training (#13861)

* Ideogram4 DreamBooth LoRA training

Add examples/dreambooth/train_dreambooth_lora_ideogram4.py + README + requirements:
- DreamBooth LoRA training for Ideogram 4 (flow-matching, dual transformer, Qwen3-VL TE)
- nf4 QLoRA and SDNQ fp8 bases: --do_fp8_training trains the fp8 checkpoint in place
  (scaled matmul), or omit it to dequantize the SDNQ base to bf16
- --disable_training_autocast (Ideogram4's forward is corrupted by autocast)
- structured JSON caption support + --upsample_prompt
- model card with a validation-image gallery

Co-Authored-By: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

* Apply style fixes

* Fix base model repo reference in Ideogram4 LoRA README

* Align Ideogram4 script deps with requirements file

---------

Co-authored-by: linoytsaban <linoy.tsaban@gmail.com>
Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>
Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>
Co-authored-by: github-actions[bot] <github-actions[bot]@users.noreply.github.com>
Co-authored-by: Linoy Tsaban <57615435+linoytsaban@users.noreply.github.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-07-02
**监控日期**: 2026-07-01
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 421
- **最后更新**: 2026-07-01T07:58:35Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-07-02
**监控日期**: 2026-07-01
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12651
- **最后更新**: 2026-07-01T20:04:49Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-07-02
**监控日期**: 2026-07-01
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 29873
- **最后更新**: 2026-07-01T23:10:14Z

## 提交统计

- **昨日提交总数**: 33
- **提交者数量**: 22
- **主要提交者**: Xiaoyu Zhang, YAMY, Shijin Zhang

## AI分析总结

根据提交记录，sglang 昨日更新集中在以下方面：

### 📌 主要更新类型
- **Bug 修复**：约 8 项（MoE 权重更新、端口冲突、量化内核、缓存类型等）
- **新功能**：约 6 项（统一内存池、fused EH norm、分层 SSD 缓存、FlashInfer 自动调优、NIXL 路径模式等）
- **CI / 测试增强**：约 11 项（AMD/NVIDIA/NPU 新测试注册、超时修复、阈值收紧等）
- **性能优化**：约 3 项（FlashMLA 默认启用、HiCache 哈希优化、内核形状覆盖加强）
- **重构/清理**：约 3 项（规则细化、死代码清理

## 详细提交记录

### [1a5977d](https://github.com/sgl-project/sglang/commit/1a5977d41b3670c03705000258b8510e158430ab)

- **作者**: Lianmin Zheng
- **时间**: 2026-07-01T22:31:34Z
- **提交信息**: [chore] Add no-getattr rule; refine no-dataclasses rule (#29871)

### [76d828a](https://github.com/sgl-project/sglang/commit/76d828a4e8f8c371cffb9ce517c53cc82a4fa27f)

- **作者**: Lianmin Zheng
- **时间**: 2026-07-01T21:52:02Z
- **提交信息**: Add pranjalssh to CI_PERMISSIONS.json (#29870)

### [5ae214f](https://github.com/sgl-project/sglang/commit/5ae214f18bc4d2231433b21863283e83e8f313a8)

- **作者**: Ming Yang
- **时间**: 2026-07-01T21:02:00Z
- **提交信息**: Extract reusable VMM shareable-handle helpers from register_graph_inputs (#29621)

### [c865347](https://github.com/sgl-project/sglang/commit/c865347b98ae84b95ec54060530cd8ba2641147c)

- **作者**: YAMY
- **时间**: 2026-07-01T20:50:05Z
- **提交信息**: [DeepSeek V4] Enable FlashMLA sparse prefill by default (#29775)

Co-authored-by: Baizhou Zhang <sobereddiezhang@gmail.com>

### [8f0d320](https://github.com/sgl-project/sglang/commit/8f0d320d3162f3586c323f2c024b45d0a4fd3fc6)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-07-01T20:36:07Z
- **提交信息**: [Spec] Enable FlashInfer autotune for spec draft (#29595)

### [4a8e768](https://github.com/sgl-project/sglang/commit/4a8e76805c27d8fffed4b8759593310a6ebde298)

- **作者**: Cheng Wan
- **时间**: 2026-07-01T20:21:59Z
- **提交信息**: feat(mem_cache): unified memory pool for hybrid Mamba / SWA models (#29678)

Co-authored-by: lch1475369 <lch1475369@gmail.com>

### [3adfd0f](https://github.com/sgl-project/sglang/commit/3adfd0f34b4844f7e91d91956de7e9712df5c53c)

- **作者**: Michael
- **时间**: 2026-07-01T19:57:48Z
- **提交信息**: [AMD] Register 3 unit mem_cache + utils tests for stage-b-test-1-gpu-small-amd (#29782)

### [8361561](https://github.com/sgl-project/sglang/commit/8361561c24a58df6404bb8c9aea0f7d516b046c1)

- **作者**: Michael
- **时间**: 2026-07-01T19:56:33Z
- **提交信息**: [AMD] Fix int8 per-token quant Triton portability + register test for AMD nightly CI (#29694)

### [c312cdd](https://github.com/sgl-project/sglang/commit/c312cdd3a7dba789a6603abfc06d4514466daec6)

- **作者**: Baizhou Zhang
- **时间**: 2026-07-01T19:32:18Z
- **提交信息**: Upgrading tvm-ffi/sgl-deep-gemm/tilelang (#29554)

### [779ea4a](https://github.com/sgl-project/sglang/commit/779ea4a9b5f465a96173987ce0f71fbc609e49cf)

- **作者**: Zhihao Wang
- **时间**: 2026-07-01T19:29:08Z
- **提交信息**: [RL] fix deepseek v4 MXFP8 flashinfer_trtllm_routed MoE weight update (#28676)

Signed-off-by: zhihaow6 <zhihaow6@illinois.edu>

### [eb75d99](https://github.com/sgl-project/sglang/commit/eb75d990f7fbf6aa0f4ae77dc94246933d7a11e3)

- **作者**: Joe Rowell
- **时间**: 2026-07-01T18:08:09Z
- **提交信息**: [Bugfix] compressed-tensors WNA16 MoE: don't assume a "Linear" config group (#29761)

Signed-off-by: Joe Rowell <joerowell4@gmail.com>
Co-authored-by: Jiminator <jimmysh341@gmail.com>
Co-authored-by: Jimmy Shong <69131491+Jiminator@users.noreply.github.com>

### [30c9801](https://github.com/sgl-project/sglang/commit/30c9801b399cee2c58098195961a7221f7a5012f)

- **作者**: Kangyan-Zhou
- **时间**: 2026-07-01T17:57:34Z
- **提交信息**: [disagg] Fix KV-event publisher port collision under pure data parallelism (#29211)

Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [03b9278](https://github.com/sgl-project/sglang/commit/03b9278da06c7b93e5affaf9796f144241710490)

- **作者**: Mick
- **时间**: 2026-07-01T17:32:51Z
- **提交信息**: [diffusion] CI: tighten multimodal-gen consistency thresholds (#29824)

### [9bb7de9](https://github.com/sgl-project/sglang/commit/9bb7de92583f7a18650e0ef857e58c591f973961)

- **作者**: Zhaoyi Li
- **时间**: 2026-07-01T15:46:48Z
- **提交信息**: [AMD][DI][CI] 2/N Add DSV4 DP8/EP8 and MTP MI355X 1P1D nightly recipes (#29784)

Co-authored-by: bingxche <bingxche@amd.com>

### [2a6e5c6](https://github.com/sgl-project/sglang/commit/2a6e5c60fe33a9882b8911d8e946c4daa849b515)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-07-01T15:17:00Z
- **提交信息**: [AMD] Rebalance stage-c-large-8-gpu-mi35x partitions to fix 60-min timeout (#29726)

### [13dc5f2](https://github.com/sgl-project/sglang/commit/13dc5f2dc789e7012a7fd4266e368940a93b7a52)

- **作者**: inkcherry
- **时间**: 2026-07-01T14:21:37Z
- **提交信息**: [HiCache][AMD] Add UMBP tiered DRAM + SSD L3 storage backend with hugepage host allocator   (#25377)


Co-authored-by: TianDi101 ditian12@amd.com
Co-authored-by: Niko Ma nima@amd.com
Co-authored-by: Wu, Yutong yutong.wu@amd.com
Co-authored-by: figo fizhang@amd.com
Co-authored-by: AMD-yanfeiwang <yanfei.wang@amd.com>
Co-authored-by: Zhangheng <hzh0425@apache.org>

### [a0d9791](https://github.com/sgl-project/sglang/commit/a0d97918105d2c985e409f5bb0891e44b8bfe221)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-07-01T13:27:07Z
- **提交信息**: [CI] Fix fused EH norm CI registration (#29845)

### [1e80d93](https://github.com/sgl-project/sglang/commit/1e80d938ff9a460ed3bc7f3c8e08e3d9e3402d85)

- **作者**: huangtingwei
- **时间**: 2026-07-01T11:31:16Z
- **提交信息**: [HiCache]fix draft host pool allocator type (#29823)

### [79f334b](https://github.com/sgl-project/sglang/commit/79f334b1aac3ff4755aa98af4870de41e5f9b145)

- **作者**: Mick
- **时间**: 2026-07-01T11:09:43Z
- **提交信息**: [diffusion] CI: add 5090 job (#29791)

### [7d9de81](https://github.com/sgl-project/sglang/commit/7d9de81cda08d7fb63cf5f56266cd0ed82a96541)

- **作者**: Lukas Humbel
- **时间**: 2026-07-01T09:59:45Z
- **提交信息**: feat(hicache): Use NIXL path-mode (#27060)

### [07ca243](https://github.com/sgl-project/sglang/commit/07ca24372bbefd0a356a38996f74e01126fbe876)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-07-01T09:46:21Z
- **提交信息**: Add fused EH norm for DeepSeek NextN (#29667)

### [8ee2009](https://github.com/sgl-project/sglang/commit/8ee200972ed1f99989dd43c8ee6662987c412901)

- **作者**: Daniel Stokes
- **时间**: 2026-07-01T08:59:54Z
- **提交信息**: [fix] Add support for flashinfer MOE A2A to Qwen3 BF16 model path (#26255)

### [677a11b](https://github.com/sgl-project/sglang/commit/677a11bfa960155ec9fc59a36eff770cc6501828)

- **作者**: Baizhou Zhang
- **时间**: 2026-07-01T08:47:35Z
- **提交信息**: [Doc] Tiny update dsv4 doc (#29827)

### [5134dcd](https://github.com/sgl-project/sglang/commit/5134dcdcab3e4d3929d7b40ac7ba4ac994f467e9)

- **作者**: ashwini rathi
- **时间**: 2026-07-01T08:27:24Z
- **提交信息**: [Intel XPU] Initially add nightly GSM8K accuracy tests for Llama-3.1-8B (TP=2) and Qwen3-32B (TP=4) (#28908)

Co-authored-by: Singhal, Shubham <shubham.singhal@intel.com>

### [548f505](https://github.com/sgl-project/sglang/commit/548f505cc54aeef6729cad163adaf0ee2dd7cc3f)

- **作者**: Bingxu Chen
- **时间**: 2026-07-01T08:21:17Z
- **提交信息**: [AMD] Cover DeepSeek-R1 MXFP4 TP4 MTP nightly CI (#29290)

### [69ce720](https://github.com/sgl-project/sglang/commit/69ce72020af20a18ea886bf3768b6b7562790643)

- **作者**: Michael
- **时间**: 2026-07-01T08:13:55Z
- **提交信息**: [AMD] Register ltx2_ada_values JIT kernel test for AMD nightly CI (#29693)

### [81a472e](https://github.com/sgl-project/sglang/commit/81a472efcc535c0e9494d48849c52b5aea89881f)

- **作者**: Bingxu Chen
- **时间**: 2026-07-01T08:09:11Z
- **提交信息**: [AMD] Update ROCm AITER pin to 9127c94 (#29816)

### [5e1ccd9](https://github.com/sgl-project/sglang/commit/5e1ccd932053427595f2e9b92dc70e7cb0e99ac9)

- **作者**: huangtingwei
- **时间**: 2026-07-01T07:44:23Z
- **提交信息**: [HiCache] Optimize HiCache hash generation with bulk token byte conversion (#28287)

### [df0dfba](https://github.com/sgl-project/sglang/commit/df0dfbaa45297ba47b9b29a2494d9116eb8e299e)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-07-01T07:44:20Z
- **提交信息**: [Kernel] Strengthen kernel shape coverage (#29636)

Co-authored-by: Khoa Pham <khoa.pham@radixark.ai>
Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>
Co-authored-by: Mohammad Miadh Angkad <176301910+mmangkad@users.noreply.github.com>

### [8205aa3](https://github.com/sgl-project/sglang/commit/8205aa36030fd3182f67e037a952c0e21c4b7c5b)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-07-01T07:42:16Z
- **提交信息**: chore: clean diffusion dead code (#29789)

### [308d89e](https://github.com/sgl-project/sglang/commit/308d89e042e0bbdc33514baca7147e467865ecdf)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-07-01T07:39:39Z
- **提交信息**: [AMD] Split qwen3.5 triton DCP test into its own nightly job (#29409)

### [00e12ce](https://github.com/sgl-project/sglang/commit/00e12cebb4f574c578431db920cf7533cc7835f9)

- **作者**: Shijin Zhang
- **时间**: 2026-07-01T07:20:12Z
- **提交信息**: [Fix]: Defer DSA MLA CP KV gather for fp8 trtllm prefill in PD mode (#29161)

Signed-off-by: Shijin Zhang <75300765+Dovis01@users.noreply.github.com>

### [7213506](https://github.com/sgl-project/sglang/commit/721350656d844af35118e97fd2a3d6e54192676f)

- **作者**: zhaozx-cn
- **时间**: 2026-07-01T07:13:48Z
- **提交信息**: [NPU] Fix glm 4.6v (#29381)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-07-02
**监控日期**: 2026-07-01
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1214
- **最后更新**: 2026-07-01T10:20:33Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

根据提供的提交记录，结合项目背景（一个针对 DiT 的 PyTorch 原生推理引擎，支持缓存、并行、量化和 CPU 卸载），以下是对昨日更新的分析总结：

### 1. 主要更新类型
- **功能新增**（feat）

### 2. 关键变更点
- **添加 Agent 工作流**：引入了 `agent` 相关的工作流（workflow）机制，可能用于自动化推理任务编排、模型调用或部署流程。
- **支持 krea-2**：新增对 `krea-2` 模型/服务的集成，推测是一种新的扩散变换器架构或第三方推理服务（如 Krea AI 平台）。

### 3. 对项目的影响与潜在意义
- **扩展模型生态**：支持 krea-2 使项目兼容更多 DiT 类模型，提升通用性和覆盖范围。
- **增强自动化与可扩展性**：Agent 工作流提供了更灵活的推理执行方式，可能允许用户自定义多步推理、条件分支或外部服务集成，降低手动调用的复杂度。
- **与项目方向一致**：项目定位为“推理引擎”，新增工作流和模型支持均服务于“高效、可扩展地运行 DiT 模型”的核心目标。

### 4. 值得关注的技术点
- **Agent 实现逻辑**：关注工作流是如何定义的（基于配置文件或代码动态生成），是否支持并行/异步执行，以及如何与现有缓存、量化等优化结合。
- **krea-2 集成方式**：是直接实现模型前向逻辑，还是通过 API 调用外部服务？这关系到推理速度、延迟和对齐其他优化模块的能力。

### 5. 对项目发展的影响（结合 README 背景）
- **加速生产化部署**：Agent 工作流可能简化从开发到生产的推理链路，让项目更易用于实际业务（如文生图、视频生成等需要复杂管线的场景）。
- **吸引更广泛用户**：支持 krea-2 这类流行模型，能吸引更多社区贡献者使用和反馈，推动项目在 DiT 推理性能上持续优化（缓存、量化等）。
- **潜在风险**：新增模块可能引入额外依赖或复杂性，需要关注与现有推理核心的兼容性及性能开销。

> 注：提交中有大量重复的描述（约 15 次“agent: add cache-dit agent workflows”），最终合并为一次提交，可能是开发过程中的多次修正或压缩，实际变更内容应视为同一次功能合并。

## 详细提交记录

### [c4a838a](https://github.com/vipshop/cache-dit/commit/c4a838ad3777ead6d549c42d88b08efe1f4522ff)

- **作者**: DefTruth
- **时间**: 2026-07-01T10:20:28Z
- **提交信息**: feat: agent workflows && support krea-2 (#1074)

* agent: add cache-dit agent workflows

* agent: add cache-dit agent workflows

* agent: add cache-dit agent workflows

* agent: add cache-dit agent workflows

* agent: add cache-dit agent workflows

* agent: add cache-dit agent workflows

* agent: add cache-dit agent workflows

* agent: add cache-dit agent workflows

* agent: add cache-dit agent workflows

* agent: add cache-dit agent workflows

* agent: add cache-dit agent workflows

* agent: add cache-dit agent workflows

* agent: add cache-dit agent workflows

* agent: add cache-dit agent workflows

* agent: add cache-dit agent workflows

* agent: add cache-dit agent workflows

* agent: add cache-dit agent workflows

* agent: add cache-dit agent workflows

* agent: add cache-dit agent workflows

* agent: add cache-dit agent workflows

* agent: add cache-dit agent workflows

* agent: add cache-dit agent workflows && support kera-2

* agent: add cache-dit agent workflows && support kera-2

* agent: add cache-dit agent workflows && support kera-2

* agent: add cache-dit agent workflows && support kera-2

* agent: add cache-dit agent workflows && support kera-2

* agent: add cache-dit agent workflows && support kera-2

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-07-02
**监控日期**: 2026-07-01
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 85054
- **最后更新**: 2026-07-01T23:54:59Z

## 提交统计

- **昨日提交总数**: 31
- **提交者数量**: 23
- **主要提交者**: Jee Jee Li, Juan Pérez de Algaba, Bugen Zhao

## AI分析总结

好的，作为专业的代码分析助手，以下是对 vllm-project/vllm 仓库昨日（2025-05-25）提交记录的分析总结。

### 1. 主要更新类型

- **Bug修复**：占比最高，涵盖KV缓存读取越界、编码器-解码器预热、填充占位符泄漏、模型权重加载错误、Beam Search候选索引、Whisper滑动窗口大小、CI测试崩溃等关键问题。
- **功能新增/改进**：包括MoE FP8 GEMM参数传递、MXFP8量化内核优化、DSpark推测解码、ROCm端JSON Content-Type支持、Cross-layer top-k共享、Hy3 Token后缀支持等。
- **重构/清理**：Rust前端DTO拆分、权重同步重构、迁移GPTBigCode/Starcoder2到Transformers后端、移除陈旧模型（AyaVision, MusicFlamingo, mantis）、Docker/CI镜像清理。
- **性能优化**：MXFP8量化内核、ROCm DSV4使用aiter mHC默认路径、weight sync refactor减少开销。
- **文档更新**：安全文档说明gRPC接口仅限私有使用。
- **测试改进**：SageMaker in-process测试、LoRA测试修复、XPU单元测试启用了qk_norm_rope_fusion。

### 2. 关键变更点及其与项目整体方向的关系

| 关键提交 | 变更点 | 与项目方向的关系 |
|---------|--------|----------------|
| [3] [MoE] Plumb gemm1_alpha/beta/clamp_limit into TRT-LLM FP8 MoE | 允许更细粒度控制FP8 MoE GEMM参数 | 契合“cheap”（更优量化精度）和“fast”（更灵活的计算调度） |
| [4] [DSV4] Better MXFP8 quantization kernel | 优化MXFP8量化内核，提升效率 | 直接提升推理性价比，符合“fast, cheap” |
| [10] [Spec Decode] DSpark | 引入新的推测解码后端（DSpark） | 加速生成，降低延迟，显著提升“fast”体验 |
| [15] Migrate GPTBigCode/Starcoder2 to Transformers backend | 迁移模型后端的标准实现 | 统一架构，降低维护成本，提升模型兼容性 |
| [26] Weight sync refactor + move sparse nccl engine | 重构权重同步逻辑，解耦NCCL引擎 | 提升分布式推理稳定性和可扩展性 |
| [29] Make sleep-mode backend capability flags communicator-agnostic | 使休眠模式后端不依赖特定通信库 | 增强异构硬件（ROCm, XPU, CPU）兼容性，体现“easy” |
| [30] Remove mantis | 移除不再维护的mantis模型 | 清理代码，聚焦主流模型支持 |
| [18] Remove AyaVision, MusicFlamingo | 删除低使用率模型 | 精简仓库，降低维护负担 |

### 3. 对项目的影响和潜在意义

- **稳定性提升**：多个Bugfix修复了KV缓存、权重加载、Beam Search等核心路径的潜在崩溃或错误结果，对生产环境的可靠性至关重要。
- **性能优化**：MoE FP8参数调优、MXFP8量化内核改进、DSpark推测解码等直接提升推理吞吐量和延迟，进一步巩固vLLM作为高性能推理框架的地位。
- **硬件生态扩展**：ROCm相关提交（JSON Content-Type、DSV4优化、Cross-layer top-k）和XPU改进表明项目持续投入AMD/Intel硬件优化，扩大“for everyone”的承诺。
- **工程质量**：重构（权重同步、Rust D

## 详细提交记录

### [e196268](https://github.com/vllm-project/vllm/commit/e196268bade5291c3fd80906bf9cd8c64851b21b)

- **作者**: Andrey Talman
- **时间**: 2026-07-01T23:19:42Z
- **提交信息**: [Docker] Remove unused Dockerfile.nightly_torch (#47338)

Co-authored-by: Andrey Talman <atalman@users.noreply.github.com>

### [e91f5f8](https://github.com/vllm-project/vllm/commit/e91f5f8439f4b2479ee53d8c993003185b83d024)

- **作者**: Andrey Talman
- **时间**: 2026-07-01T23:19:06Z
- **提交信息**: [CI] Remove torch_nightly mirror tags (superseded by TORCH_NIGHTLY full-nightly build) (#47342)

Co-authored-by: Andrey Talman <atalman@users.noreply.github.com>

### [fa24813](https://github.com/vllm-project/vllm/commit/fa248139a0206b3e39780296e3f056a978957f63)

- **作者**: Yongye Zhu
- **时间**: 2026-07-01T21:34:05Z
- **提交信息**: [MoE] Plumb gemm1_alpha/beta/clamp_limit into TRT-LLM FP8 MoE (#45723)

Signed-off-by: Yongye Zhu <zyy1102000@gmail.com>
Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [d322943](https://github.com/vllm-project/vllm/commit/d3229431f958a159ac8d9b79969e0068e547d1b0)

- **作者**: Yongye Zhu
- **时间**: 2026-07-01T21:33:51Z
- **提交信息**: [DSV4] Better MXFP8 quantization kernel (#47229)

Signed-off-by: Yongye Zhu <zyy1102000@gmail.com>

### [4787f2d](https://github.com/vllm-project/vllm/commit/4787f2dd1b5705b92c095885f2f07f7253f5aed8)

- **作者**: Nick Hill
- **时间**: 2026-07-01T19:43:00Z
- **提交信息**: [Bugfix] Don't read KV cache past `seq_len` in triton paged attn kernels (#47305)

### [8cfeb84](https://github.com/vllm-project/vllm/commit/8cfeb84dba41a0c56570334757d921abd71e5288)

- **作者**: Nick Hill
- **时间**: 2026-07-01T19:36:48Z
- **提交信息**: [ModelRunner V2] Warmup cross-attn properly in encoder-decoder case (#47308)

### [5fd4421](https://github.com/vllm-project/vllm/commit/5fd442187cdefc1c64f48ef8aa50fb9d269bd1cc)

- **作者**: Chaitanya Sri Krishna Lolla
- **时间**: 2026-07-01T19:17:05Z
- **提交信息**: [ROCm][P/D] MoRIIO toy proxy: support JSON Content-Type for OpenAI clients. (#46482)

Signed-off-by: lcskrishna <lollachaitanya@gmail.com>

### [00eb7ce](https://github.com/vllm-project/vllm/commit/00eb7cefa31e32585fb419db5bb945f6a42480fe)

- **作者**: Yiliu Dong
- **时间**: 2026-07-01T16:26:03Z
- **提交信息**: [Bugfix] Prevent padding placeholders from reaching embeddings (#47029)

Signed-off-by: qianlihuang <91178480+qianlihuang@users.noreply.github.com>
Signed-off-by: Yiliu Dong <91178480+qianlihuang@users.noreply.github.com>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>

### [c8bdcc0](https://github.com/vllm-project/vllm/commit/c8bdcc011623de64dbab64813a184ab083730a81)

- **作者**: Michał Ganczarenko
- **时间**: 2026-07-01T15:42:27Z
- **提交信息**: [Bench][BugFix] Fix empty decoder prompt for Cohere ASR in throughput benchmark (#47135)

Signed-off-by: Michal Ganczarenko <michal.ganczarenko@intel.com>

### [f5a8d73](https://github.com/vllm-project/vllm/commit/f5a8d73377d0f0a4e00cba172f9fbd0d50471b07)

- **作者**: Benjamin Chislett
- **时间**: 2026-07-01T15:30:24Z
- **提交信息**: [Spec Decode] DSpark (#46995)

Signed-off-by: Benjamin Chislett <bchislett@nvidia.com>
Signed-off-by: Giancarlo Delfin <gdelfin@inferact.ai>
Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Giancarlo Delfin <gdelfin@inferact.ai>
Co-authored-by: mgoin <mgoin64@gmail.com>

### [63fcce4](https://github.com/vllm-project/vllm/commit/63fcce4de1563309ea5195ba98d0a2e1ba4f5831)

- **作者**: Michał Ganczarenko
- **时间**: 2026-07-01T14:39:12Z
- **提交信息**: [Bugfix] Fix GraniteMoeShared weight loading broken by #41184 (#47031)

Signed-off-by: <Michal Ganczarenko> <michal.ganczarenko@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [c638f92](https://github.com/vllm-project/vllm/commit/c638f9216a08bfb5644d8a266ddd35421e04118d)

- **作者**: Bugen Zhao
- **时间**: 2026-07-01T14:28:21Z
- **提交信息**: [Rust Frontend] Split engine core DTOs into separate modules (#47265)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>

### [13c49f9](https://github.com/vllm-project/vllm/commit/13c49f9845d5f64c53a75d7b5c44c3997c4f6ee6)

- **作者**: Chaojun Zhang
- **时间**: 2026-07-01T14:14:04Z
- **提交信息**: [xpu][lora]: Align LoRA implementation with Punica GPU: fix _apply_expand rank mismatch, add_inputs hardcode, and MoE EP (#45368)

Signed-off-by: Chaojun Zhang <chaojun.zhang@intel.com>

### [f1cf6b0](https://github.com/vllm-project/vllm/commit/f1cf6b0086b95c9594ea685673b9cf8d95ed9b0a)

- **作者**: Nick Hill
- **时间**: 2026-07-01T14:00:37Z
- **提交信息**: [CI] Fix segfault in tracing test (#47299)

Signed-off-by: Nick Hill <nickhill123@gmail.com>

### [a78c156](https://github.com/vllm-project/vllm/commit/a78c15616f927745444ed6a783d98d865643e1ff)

- **作者**: Harry Mellor
- **时间**: 2026-07-01T13:41:36Z
- **提交信息**: Migrate GPTBigCode and Starcoder2 to the Transformers modeling backend (#30966)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [5c4db60](https://github.com/vllm-project/vllm/commit/5c4db60f019a183231cf020e5679baaf1e8c293f)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-07-01T12:39:57Z
- **提交信息**: docs(security): document gRPC interface as insecure for private use only (#45903)

Signed-off-by: jperezde <jperezde@redhat.com>
Signed-off-by: Russell Bryant <russell.bryant@gmail.com>
Co-authored-by: Russell Bryant <russell.bryant@gmail.com>
Co-authored-by: Russell Bryant <rbryant@redhat.com>

### [4e5ca89](https://github.com/vllm-project/vllm/commit/4e5ca89cfe98121642d76b40e32a006f4d0fbf3b)

- **作者**: Fangzhou Ai
- **时间**: 2026-07-01T10:50:09Z
- **提交信息**: [ROCm][MiniMax-M3] Cross-layer lightning-indexer top-k sharing (#47269)

Signed-off-by: Fangzhou Ai <fangzhouai@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [a22e0df](https://github.com/vllm-project/vllm/commit/a22e0dfc69a0fe9e058ccea865fbc4868bb187e1)

- **作者**: Harry Mellor
- **时间**: 2026-07-01T10:39:33Z
- **提交信息**: [Model] Remove AyaVision, MusicFlamingo (#47263)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [cc56379](https://github.com/vllm-project/vllm/commit/cc56379e28a0600cbabe290508ef49d88cc2afd5)

- **作者**: stevenkuang
- **时间**: 2026-07-01T10:16:07Z
- **提交信息**: [Model] Support Hy3 token suffix and JSON Schema array types (#47192)

Signed-off-by: stevenkuang-tencent <stevenkuang@tencent.com>

### [024b06b](https://github.com/vllm-project/vllm/commit/024b06b0dc0c0a6e5ec45bcdea21d35e43fcc23f)

- **作者**: Aleksei Ivashov
- **时间**: 2026-07-01T10:00:19Z
- **提交信息**: [Bugfix] Expose usage field in GenerateResponse for disaggregated serving (#42748)

Signed-off-by: AIvashov <ivashov.aleksey@proton.me>
Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>
Co-authored-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [e7d0fcb](https://github.com/vllm-project/vllm/commit/e7d0fcbc0954382f10fb4c9cee1df6f3a16113e8)

- **作者**: Harry Mellor
- **时间**: 2026-07-01T09:35:34Z
- **提交信息**: [CI] Fix various failures on `main` (#47197)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [aa8bb55](https://github.com/vllm-project/vllm/commit/aa8bb5562ebe435bb19276d094a021e9721f5bce)

- **作者**: akii96
- **时间**: 2026-07-01T09:33:55Z
- **提交信息**: [ROCm][Perf][Bugfix] DSv4 indexer: use platform FP8 dtype (fnuz) for Q-quant on gfx942 (#46730)

Signed-off-by: Aakif Nawaz <aakif.nawaz@amd.com>

### [fa4bec9](https://github.com/vllm-project/vllm/commit/fa4bec90567715d1482b01fb6ad6c16bc5c1ed36)

- **作者**: Andy Lo
- **时间**: 2026-07-01T09:33:19Z
- **提交信息**: [Bugfix] Fix pooled Whisper sliding-window KV sizing (#47071)

Signed-off-by: Andy Lo <andy@mistral.ai>

### [dee5da1](https://github.com/vllm-project/vllm/commit/dee5da1dec8c508cba430fd8536510afd7b80f60)

- **作者**: Jyothirmai Kottu
- **时间**: 2026-07-01T09:14:00Z
- **提交信息**: [Test] Run SageMaker handler-override tests in-process via TestClient (#47250)

Signed-off-by: Jyothirmai Kottu <jkottu@amazon.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [ed41aa2](https://github.com/vllm-project/vllm/commit/ed41aa270a9e01320e55ff9a069a826acb764101)

- **作者**: Fangzhou Ai
- **时间**: 2026-07-01T08:27:42Z
- **提交信息**: [ROCm][DSV4] Use aiter mHC pre/post as the default ROCm path (#43950)

Signed-off-by: Fangzhou Ai <fangzhou.ai@amd.com>
Signed-off-by: Fangzhou-Ai <fangzhouai@gmail.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [77a9c5a](https://github.com/vllm-project/vllm/commit/77a9c5ae28a3d054e6caf60c7e14082453b3ae47)

- **作者**: Aaron Hao
- **时间**: 2026-07-01T08:25:19Z
- **提交信息**: Weight sync refactor + move sparse nccl engine (#44353)

Signed-off-by: hao-aaron <ahao@anyscale.com>
Signed-off-by: haoaaron <ahao@anyscale.com>
Co-authored-by: Claude Sonnet 4.6 <noreply@anthropic.com>

### [f651a8a](https://github.com/vllm-project/vllm/commit/f651a8a9a444e5ef7eb88003d45ab908b8d4dc25)

- **作者**: Yejing Lai
- **时间**: 2026-07-01T07:38:03Z
- **提交信息**: [XPU][UT]Enable ut qk_norm_rope_fusion (#42486)

Signed-off-by: Lai, Yejing <yejing.lai@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [8f82be5](https://github.com/vllm-project/vllm/commit/8f82be5705692f5e45b65186051e8bcf7f8ef8c2)

- **作者**: Jee Jee Li
- **时间**: 2026-07-01T07:36:13Z
- **提交信息**: [CI/Build]  Fix LoRA testing  (#47242)

Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>

### [a461070](https://github.com/vllm-project/vllm/commit/a461070d1c534885e8d092e1cf2be452d6cec7a0)

- **作者**: Nils Matteson
- **时间**: 2026-07-01T07:17:44Z
- **提交信息**: [Core] Make sleep-mode backend capability flags communicator-agnostic (#47243)

### [4470ae8](https://github.com/vllm-project/vllm/commit/4470ae84de525640a6ed8701a28882ff392e06b6)

- **作者**: Tiezhen WANG
- **时间**: 2026-07-01T07:13:58Z
- **提交信息**: Remove mantis (#46806)

Signed-off-by: Xianbao QIAN <xianbao.qian@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [697c34b](https://github.com/vllm-project/vllm/commit/697c34b97b4d7a5377ab223e846f545111a9a352)

- **作者**: Chauncey
- **时间**: 2026-07-01T07:07:06Z
- **提交信息**: [Bugfix] Fix beam search candidate indexing when logprobs count varies (#47126)

Signed-off-by: chaunceyjiang <chaunceyjiang@gmail.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-07-02
**监控日期**: 2026-07-01
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 5388
- **最后更新**: 2026-07-01T23:41:21Z

## 提交统计

- **昨日提交总数**: 5
- **提交者数量**: 5
- **主要提交者**: Thanaji Rao Thakkalapelli, TJian, Renzheng Wang

## AI分析总结

### 昨日更新要点分析

基于仓库 `vllm-project/vllm-omni` 的 README（专注于易用、快速、低成本的多模态模型服务），结合昨日提交记录，总结如下：

---

#### 1. 主要更新类型
- **功能新增/改进**：1 项（SDXL 扩散 LoRA 兼容性提升）
- **Bug 修复**：3 项（SenseNova pipeline 修复、量化门控修复、AMD CI 修复）
- **项目管理/文档**：1 项（维护者和代码所有者更新）

---

#### 2. 关键变更点及其与项目整体方向的关系
| 提交 | 变更要点 | 与项目方向关联 |
|------|----------|----------------|
| [1788d76] | 改进 SDXL 扩散模型的 LoRA 兼容性 | 直接服务“多模态”与“低成本”目标：扩散模型是多模态（图像生成）核心组件，LoRA 可降低微调与部署成本。 |
| [d526dc9] | 设置 SenseNova pipeline 的 `.transformer` 属性，并在 CacheDiT 缺乏该属性时给出警告 | 修复可能引入的运行时错误，提升**稳定性**和**易用性**（避免无提示失败）。 |
| [6b11f6b] | 限制 quack FP8 量化仅用于数据中心 Blackwell 架构（sm_100.x） | 量化是降低推理成本的关键技术；此修复避免在不支持的硬件上产生错误，确保**正确性**与**安全性**。 |
| [e4a2d36] | 更新维护者和代码所有者列表 | 项目治理透明化，配合社区长期发展（与“for everyone”精神一致）。 |
| [efc6b39] | 修复 AMD CI 在 v0.24.0 重基后的问题 | 保障**跨平台兼容性**（AMD GPU 支持是重要扩展方向）。 |

---

#### 3. 对项目的影响和潜在意义
- **功能增强**：SDXL LoRA 兼容性提升，意味着下游用户可更灵活地适配个性化模型，直接增强项目在图像生成领域的竞争力。
- **稳定性提升**：SenseNova pipeline 和量化门控的修复减少了潜在崩溃或错误行为，有助于建立用户信任。
- **基础设施强化**：AMD CI 的修复确保持续集成可正确验证 AMD GPU 支持，为后续扩大硬件覆盖范围奠定基础。
- **治理规范化**：维护者和代码所有者列表更新体现了开源项目的健康迭代。

---

#### 4. 值得关注的技术点
- **扩散 LoRA 兼容性**：具体实现可能涉及模型结构适配或注意力注入优化，值得关注后续文档或代码注释。
- **FP8 量化硬件门控**：`sm_100.x` 对应 NVIDIA Blackwell 架构，显示项目正积极跟进最新硬件特性，以充分利用 FP8 精度带来的吞吐优势。
- **CacheDiT 警告机制**：这表明项目在处理 Transformer 类扩散模型时注重内部结构的完整性检查，是一种防御性编程实践。

---

#### 5. 基于项目背景的发展影响
- **多模态能力深化**：SDXL 的 LoRA 支持扩展了图像模态的定制化能力，与 README “omn-modality” 使命高度一致。
- **成本优化路径**：量化门控修复保证了 FP8 量化仅在高效硬件上启用，避免因不兼容导致的性能损失，符合“cheap”原则。
- **易用性提升**：SenseNova 修复 + LoRA 兼容性改进共同降低了用户使用门槛，呼应“easy”定位。
- **社区与硬件支持**：维护者更新和 AMD CI 修复表明项目正在建立可持续的贡献生态，并积极拥抱多厂商硬件（ROCm），扩大覆盖面。

## 详细提交记录

### [1788d76](https://github.com/vllm-project/vllm-omni/commit/1788d76eb32ff68b8069a07185253245367090f4)

- **作者**: Thanaji Rao Thakkalapelli
- **时间**: 2026-07-01T23:41:16Z
- **提交信息**: [Feature] Improve diffusion LoRA compatibility for SDXL (#4825)

Signed-off-by: Thanaji Rao Thakkalapelli <thanaji.rao.thakkalapelli@intel.com>

### [d526dc9](https://github.com/vllm-project/vllm-omni/commit/d526dc93e89aa4d806a9111aab496b0bc04c8937)

- **作者**: Alex Brooks
- **时间**: 2026-07-01T17:40:07Z
- **提交信息**: [Fix]: Set .transformer on SenseNova pipeline, warn if no .transformer in CacheDiT summary (#4326)

Signed-off-by: Alex Brooks <albrooks@redhat.com>
Co-authored-by: Didan Deng <33117903+wtomin@users.noreply.github.com>

### [6b11f6b](https://github.com/vllm-project/vllm-omni/commit/6b11f6b41dbff59a4f5ad49c19f1de7567d26f2b)

- **作者**: Renzheng Wang
- **时间**: 2026-07-01T16:51:17Z
- **提交信息**: [Bugfix][Quant] Gate quack FP8 to datacenter Blackwell (sm_100.x) only (#4817)

Signed-off-by: wangrzneu <wangrzneu@gmail.com>

### [e4a2d36](https://github.com/vllm-project/vllm-omni/commit/e4a2d3676e666df63fa73a1e17085743b34e1c28)

- **作者**: Hongsheng Liu
- **时间**: 2026-07-01T16:11:11Z
- **提交信息**: [codex] Update maintainers and code owners (#4823)

Signed-off-by: hsliuustc0106 <liuhongsheng4@huawei.com>

### [efc6b39](https://github.com/vllm-project/vllm-omni/commit/efc6b391e4eb88c2488cc1342842bc9ee7b0ff7d)

- **作者**: TJian
- **时间**: 2026-07-01T13:18:24Z
- **提交信息**: [ROCm] [CI] Fix AMD CI after v0.24.0 rebase (#4821)

Signed-off-by: tjtanaa <tunjian.tan@embeddedllm.com>

---
