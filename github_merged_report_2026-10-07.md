# GitHub Stars 合并报告 - 2026-10-07

**合并日期**: 2026-10-08
**监控日期**: 2026-10-07
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


**报告日期**: 2026-10-08
**监控日期**: 2026-10-07
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2234
- **最后更新**: 2026-10-07T19:45:08Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-10-08
**监控日期**: 2026-10-07
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2881
- **最后更新**: 2026-10-06T22:28:41Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-10-08
**监控日期**: 2026-10-07
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2285
- **最后更新**: 2026-10-07T06:20:59Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-10-08
**监控日期**: 2026-10-07
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6556
- **最后更新**: 2026-10-08T01:04:56Z

## 提交统计

- **昨日提交总数**: 14
- **提交者数量**: 9
- **主要提交者**: Vedaanta Agarwalla, Qidong Su, eigen

## AI分析总结

# FlashInfer 近期提交综合分析

## 一、主要更新类型

本次提交以**功能新增**与**性能优化**为核心，辅以多条健壮性修复。功能层面覆盖 Blackwell 系列（SM120/SM107）内核新增、MoE 统一后端完善与融合量化算子；优化层面集中在 MLAA 稀疏注意力与 cuDNN 自动调度；修复层面针对架构能力差异、上游缺陷和 CI 环境问题。整体方向是深度覆盖新一代 NVIDIA 硬件与前沿模型结构。

## 二、关键变更点与项目方向的关系

FlashInfer 定位为"高推理 GPU 内核库"，各提交高度契合该目标：

- **DeepSeek 稀疏注意力打通消费级 Blackwell**：CAKE 团队为 RTX PRO 6000 / RTX 5090（SM120）实现 DeepSeek 稀疏注意力"lightning indexer"的分页 FP8 MQA-logits 内核，其中 `next_n=4` 采用单 Q 原子方案，KV 仅读取一次，在大 batch/长上下文场景达到 DeepGEMM 的 0.56–0.73× 耗时并保持位级一致，直接支撑 vLLM 等框架在消费级 Blackwell 上运行 DeepSeek 系列模型。
- **Rubin（SM107）适配加速**：集中解除 KDA prefill 与 TRTLLM-GEN FP8/FP4 MoE 路径的架构白名单；W4A4 MoE 新增局部性域执行（双域并行 FC1/FC2 与绿色上下文流），为 Rubin 多芯片推理铺路。
- **MoE 后端完善**：Prims-TS 后端补齐 MXFP4×MXFP8、MXFP8、FP8 per-tensor、DeepSeek-FP8 等量化配对；针对 DeepSeek-V3 路由的跨后端一致性测试覆盖真实 logit、tie-heavy、大 T 等极端输入，以输出 dtype 一个 ulp 容差断言。
- **融合量化 MLP 算子**：新增 MiniMax-H3 SM120 融合算子——RMSNorm + AdaLN + FC1 + SwiGLU + FC2 + 门控残差，支持 FP8（W8A8）与 NVFP4（W4A4），并通过 `flashinfer.diffusion_ops` 公开 API 服务扩散模型。
- **cuDNN 自动调度优化**：`backend="auto"` 在单 token d256 分页解码及特定 CTA 区间自动选择 cuDNN；CUDA graph 包装器声明 replay 意图，使复用场景选中 GPU 时间最优的 split-KV 计划。
- **性能打磨与缺陷修复**：SM100/SM103 上 DSv4 稀疏 MLA 的 FP8 前奏汇合与 BF16 在线 softmax 调优；MXFP4 组 GEMM 测试经分块量化将 32GB GPU 上峰值内存从约 11GB 降至约 2GB；cuTile RoPE FP8 在 SM89 以下改为显式抛出 `NotImplementedError`；修复 NVSHMEM 对称内存释放后句柄被地址缓存复用的问题；隔离 nightly 环境变量导致的 CI 测试误报。

## 三、对项目的影响与潜在意义

- 显著扩大 DeepSeek 稀疏注意力在**消费级/工作站级 Blackwell GPU** 的可用性，利好成本敏感的推理场景；MiniMax-H3 融合算子使生产级扩散算子在该平台落地。
- Rubin 平台的抢先适配（MoE、KDA prefill）为下一代 NVIDIA 硬件储备了成熟的内核路径。
- Prims-TS 量化配对补齐后具备更完整的实验价值，为未来切换默认后端积累数据。
- 三条健壮性修复分别防御硬件能力差异、torch 上游缺陷与 CI 环境不一致，提升误报率与运行时崩溃率。

## 四、值得关注的技术点

- **位级一致性保证**：多内核强调与 DeepGEMM 逐位相同或 BF16 容差内一致，是高质量移植的标杆。
- **分布式一致性原语**：NVSHMEM 修复以一次小型 `all_reduce` 位掩码投票替代 barrier 统一各 rank 的重分配决策，设计模式值得借鉴。
- **CUDA graph 感知调度**：cuDNN 前端的 replay 声明影响 KV 分割策略，说明 graph 感知是性能优化的重要维度。
- **生成式内核管线**：CAKE 团队通过 Weave/Cake DSL 外部编译器生成内核并哈希校验来源，TMA 描述符支持步幅缓存视图以兼容多样化引擎布局。
- **CUDA 原子数策略与 `next_n` 绑定**：在元数据无头数信息的约束下 `policy.next_n_atoms` 统一置 1，体现受限元数据下的工程妥协。

## 五、整体影响总结

FlashInfer 正从通用 GPU 内核库快速向**深度覆盖新一代 NVIDIA 硬件（Blackwell SM120/SM107/Rubin）与前沿模型结构（DeepSeek 稀疏注意力、MoE、MLA、扩散模型融合算子）**方向演进。其策略可概括为：上游内核（DeepGEMM、TRTLLM-GEN）兼容或超越、新硬件抢先适配、性能极致打磨、工程质量持续加固。这些工作共同支撑 FlashInfer 在多硬件、多量化格式、多框架生态下保持高性能与高可靠性，为下一阶段支持更多前沿模型的推理优化奠定坚实基础。

## 详细提交记录

### [b5e50c2](https://github.com/flashinfer-ai/flashinfer/commit/b5e50c20ba71b3d400c95b732d4abbf6fdb59335)

- **作者**: eigen
- **时间**: 2026-10-07T19:42:09Z
- **提交信息**: feat(cake_deepgemm): SM120 paged MQA-logits indexer: one Q atom per request for next_n 4, strided per-layer cache views (#6199)

<!-- .github/pull_request_template.md -->

## 📌 Description

Developed by the **CAKE team**. Follow-up to #6180 (merged as 52863f595;
same family `deepgemm_sm120_paged_mqa_logits`, same public API). Rebased
onto `main` after that merge; the diff is this PR's single commit.

**1. `next_n` 4 programs: one Q atom per request.** DeepGEMM's SM120
kernel (and the first delivery, an exact port) scores a request with
`next_n` 4 as two 2-token Q atoms, streaming every KV tile twice. The
regenerated `next_n` 4 programs score all four tokens from one 4-token
atom with the same per-logit MMA / epilogue sequence, so the logits stay
**bitwise identical** to DeepGEMM while the KV is read once per request.
Measured on RTX PRO 6000 Blackwell Server Edition against DeepGEMM on
identical inputs (15 `next_n` 4 rows, CUPTI, cold L2): geomean 0.87× the
DeepGEMM time; 0.56–0.73× at batch ≥ 64 × 16K context and at batch 32 ×
64K, 0.91–0.95× at batch 32 × 16K, 0.94–1.01× on the remaining batch
1–32 rows (4K–16K); the only loss beyond 1 % is the 64-head program at
batch 8 × 4K (1.08×, its 4×64-row atom leaves shared memory for one Q
stage). `next_n` 1 and 2 are unchanged (already one atom per request).
Because the atom rule must stay a function of `next_n` alone (the
metadata entry has no head count), `policy.next_n_atoms` is now 1 for
every shipped `next_n`; the DeepGEMM-shaped signatures are unchanged.

**2. Strided per-layer cache views.** `fused_cache_rows` /
`prepare_sm120_paged_mqa_logits` accepted only a contiguous 4-D cache or
a dense 2-D view. Engines with block-outermost KV layouts (every layer's
page in one block) hand the indexer a strided `[pages, page_kv, 1, 132]`
view (`stride(0) > page_kv * 132`), and alignment padding does the same.
The kernel has always read pages through a TMA descriptor that carries
the physical block stride (as DeepGEMM does), so the host contract now
accepts any view with dense 132-byte token rows and a 16-byte-aligned
block stride ≥ the row, read in place without a copy. New test
`test_sm120_paged_strided_per_layer_view` (two-layer block: bitwise
equal to the dense plan on every valid cell; a row-skipping view is
refused).

**3. Full re-delivery of the generated directory.** Program file names
are a hash of the normalized generated text and launch contract, so
every program whose generated text changed gets a new name. Since #6180
the generated sources include the shared Cake device helpers from
`csrc/cake_device_helpers/` (nine content-addressed headers, included
only from the generated sources) through a per-family
`_device_common.cuh` instead of carrying their own copies, and the
`next_n` 4 programs are regenerated; all ten kernel programs and their
bindings are therefore renamed, the previous files removed, and the
catalog regenerated (its `closure_sha256` and per-file digests are
computed from the delivered, clang-formatted text). No orphaned kernels
remain.

Producer: Cake MR !1286 (commit
`2ea2a82ed7ea8c2c503f7c64ae01b8eef72a736c`), on top of the #6180
producer MR !1283.

## 🔍 Related Issues

Tracking issue: #4254 (entry for this experimental route; owner, reason
and graduation plan unchanged). Motivation as in #6180:
vllm-project/vllm#59725, vllm-project/DeepGEMM#28.

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

- `tests/experimental/test_sm120_paged_mqa_logits.py`: 11 passed on RTX
PRO 6000 Blackwell Server Edition (driver 595.84.01): FP32 torch
reference at FP8-class tolerance over heads × pages × next_n × batch,
padded block strides, the strided per-layer view (bitwise equal to the
dense plan), CUDA-graph plan replay (bitwise equal to eager), one-shot
call bitwise equal to the plan.
- Export receipts (source = Cake production plan vs the generated
FlashInfer programs; same-session paired CUPTI cold-L2 medians,
symmetric external CUDA-graph replay): 21/21 gates passed with a
complete denominator (per-shape correctness gate: torch dequant
reference at FP8 tolerance, exact schedule metadata, and bitwise
source/export parity of logits and metadata); geomean source / export
1.0014× over the 21 rows (logits 1.0011×, metadata 1.0050×), per-row
0.9917×–1.0111×. Table below.
- Producer gates (Cake MR !1286, final tree): exporter unit tests 44 +
16 passed on the final tree; GPU gates on the kernel tree the final tree
inherits unchanged (later commits touch exporter formatting, test data
and docs only): e2e CPU slice 32 passed, GPU slice 8 passed, self-test
8/8 bitwise vs DeepGEMM, bench-regression 234 TFLOPS vs the 200 TFLOPS
floor, compute-sanitizer synccheck + memcheck 0 errors.

### Performance

`next_n` 4 rows vs DeepGEMM's SM120 kernel on identical inputs (time
ratio, lower is better; 32 heads / page 128 unless noted): B256×16K
0.56, B128×16K 0.71, B32×64K 0.73, B32×16K 0.91, B32×4K 0.98, B16×8K
0.96, B8×16K 0.99, B8×4K 0.98, B1×16K 0.94, B1×4K 1.01; 32 heads / page
64: B64×16K 0.72, B8×4K 0.99; 64 heads / page 64: B128×16K 0.72, B32×16K
0.95, B8×4K 1.08 (geomean 0.87 over the 15 rows). `next_n` 1–2 programs
keep the exact-port schedule of #6180 (which measured geomean 0.9995 vs
DeepGEMM over 21 rows spanning `next_n` 1/2/4, all bitwise-equal); their
source/export receipts are in the table below.

## 🔬 Experimental Track

<!-- Only for PRs submitted under the experimental policy
(CONTRIBUTING.md → "Experimental APIs and Backends").
     Leave this section untouched for normal PRs. -->

- [x] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.
Tracking issue: #4254
- [x] The tracking issue names an owner, the reason for the experimental
path, and a graduation plan with a target release.
- [x] Core changes are limited to a thin entry point (signature, shared
validation, feature-gate check, backend selection, handoff):
`flashinfer/sm120_paged_mqa_logits.py` (docstring-only change in this
PR), plus the new shared helper directory `csrc/cake_device_helpers/`
(nine content-addressed device-helper headers shared by Cake exports,
included only from the generated sources, never edited by hand);
everything else lives in
`flashinfer/experimental/deepgemm_sm120_paged_mqa_logits/`,
`csrc/experimental/deepgemm_sm120_paged_mqa_logits/` and
`tests/experimental/`, and the runnable example
`benchmarks/bench_sm120_paged_mqa_logits.py` is unchanged from #6180.
- [x] Tests live in `tests/experimental/` and were validated on the
intended hardware (RTX PRO 6000 Blackwell Server Edition); runnable
example: `benchmarks/bench_sm120_paged_mqa_logits.py`.
- [x] Nothing is registered in `flashinfer/aot.py`, and no experimental
backend is reachable from `backend="auto"` without
`FLASHINFER_ALLOW_EXPERIMENTAL_AUTO_BACKENDS=1`. The route is reached
only through the three `@flashinfer_experimental_api` entry points.
- [x] **Test scope declared below.** The experimental CI lane runs
exactly these targets, so keep them as narrow as the change allows.

<!-- Required for experimental PRs. Replace the commented lines below
with your targets.
Do not delete the fence or change its `experimental-tests` tag — the
experimental-track
watcher reads it verbatim to decide which targets to ask CI for. -->

```experimental-tests
tests/experimental/test_sm120_paged_mqa_logits.py
```

## Reviewer Notes

**Unsupported (unchanged).** `clean_logits=True`, varlen `indices`,
next_n 3, FP4 (E2M1) indexer caches, head counts other than 32/64, page
sizes other than those listed, non-SM120 devices.

**Formatting.** The generated `.cu` sources are delivered already
formatted with the repository's pinned clang-format release, so the
pre-commit hooks leave every delivered file unchanged (verified with
`pre-commit run --files` over all 39 files); the catalog's
`closure_sha256` and per-file digests derive from the formatted text.

<details><summary>Export receipts: 21 shapes on RTX PRO 6000 Blackwell
Server Edition (driver 595.84.01), Cake production plan (source) vs the
delivered FlashInfer programs (export)</summary>

#### Per-shape results

|Shape|Route|Source ms|Export ms|Source / Export|Baseline|Baseline
ms|Baseline / Export|Verdict|
|---|---|---:|---:|---:|---|---:|---:|---|

|sm120_paged_h32_p128_n1_b8_c4096_sm_120a|R3|0.014976|0.014944|1.0021x|—|—|—|pass|

|sm120_paged_h32_p128_n1_b64_c16384_sm_120a|R1|0.135905|0.135872|1.0002x|—|—|—|pass|

|sm120_paged_h32_p128_n2_b8_c4096_sm_120a|R5|0.015488|0.015520|0.9979x|—|—|—|pass|

|sm120_paged_h32_p128_n2_b64_c16384_sm_120a|R4|0.139265|0.138945|1.0023x|—|—|—|pass|

|sm120_paged_h32_p128_n4_b8_c4096_sm_120a|R7|0.015968|0.015904|1.0040x|—|—|—|pass|

|sm120_paged_h32_p128_n4_b64_c16384_sm_120a|R6|0.145825|0.147041|0.9917x|—|—|—|pass|

|sm120_paged_h32_p64_n1_b8_c4096_sm_120a|R9|0.014688|0.014656|1.0022x|—|—|—|pass|

|sm120_paged_h32_p64_n1_b64_c16384_sm_120a|R8|0.145313|0.145248|1.0004x|—|—|—|pass|

|sm120_paged_h32_p64_n2_b8_c4096_sm_120a|R11|0.015520|0.015520|1.0000x|—|—|—|pass|

|sm120_paged_h32_p64_n2_b64_c16384_sm_120a|R10|0.146160|0.146016|1.0010x|—|—|—|pass|

|sm120_paged_h32_p64_n4_b8_c4096_sm_120a|R13|0.016256|0.016192|1.0040x|—|—|—|pass|

|sm120_paged_h32_p64_n4_b64_c16384_sm_120a|R12|0.151937|0.153152|0.9921x|—|—|—|pass|

|sm120_paged_h64_p64_n1_b8_c4096_sm_120a|R15|0.014848|0.014816|1.0022x|—|—|—|pass|

|sm120_paged_h64_p64_n1_b64_c16384_sm_120a|R14|0.145696|0.145761|0.9996x|—|—|—|pass|

|sm120_paged_h64_p64_n2_b8_c4096_sm_120a|R17|0.015648|0.015584|1.0041x|—|—|—|pass|

|sm120_paged_h64_p64_n2_b64_c16384_sm_120a|R16|0.143104|0.143297|0.9987x|—|—|—|pass|

|sm120_paged_h64_p64_n4_b8_c4096_sm_120a|R19|0.017504|0.017312|1.0111x|—|—|—|pass|

|sm120_paged_h64_p64_n4_b64_c16384_sm_120a|R18|0.157024|0.156400|1.0040x|—|—|—|pass|

|sm120_paged_h32_p128_n1_b64_c4096_pad512_sm_120a|R2|0.044673|0.044544|1.0029x|—|—|—|pass|
|sm120_meta_b64_n1_sm_120a|R21|0.005120|0.005088|1.0063x|—|—|—|pass|
|sm120_meta_b256_n4_sm_120a|R20|0.008512|0.008480|1.0038x|—|—|—|pass|

#### Route legend

|Key|Route|
|---|---|

|R1|deepgemm_sm120_paged_sm120_fp8_h32_p128_n1_sm120_paged_h32_p128_n1_b64_c16384_sm_120a|

|R2|deepgemm_sm120_paged_sm120_fp8_h32_p128_n1_sm120_paged_h32_p128_n1_b64_c4096_pad512_sm_120a|

|R3|deepgemm_sm120_paged_sm120_fp8_h32_p128_n1_sm120_paged_h32_p128_n1_b8_c4096_sm_120a|

|R4|deepgemm_sm120_paged_sm120_fp8_h32_p128_n2_sm120_paged_h32_p128_n2_b64_c16384_sm_120a|

|R5|deepgemm_sm120_paged_sm120_fp8_h32_p128_n2_sm120_paged_h32_p128_n2_b8_c4096_sm_120a|

|R6|deepgemm_sm120_paged_sm120_fp8_h32_p128_n4_sm120_paged_h32_p128_n4_b64_c16384_sm_120a|

|R7|deepgemm_sm120_paged_sm120_fp8_h32_p128_n4_sm120_paged_h32_p128_n4_b8_c4096_sm_120a|

|R8|deepgemm_sm120_paged_sm120_fp8_h32_p64_n1_sm120_paged_h32_p64_n1_b64_c16384_sm_120a|

|R9|deepgemm_sm120_paged_sm120_fp8_h32_p64_n1_sm120_paged_h32_p64_n1_b8_c4096_sm_120a|

|R10|deepgemm_sm120_paged_sm120_fp8_h32_p64_n2_sm120_paged_h32_p64_n2_b64_c16384_sm_120a|

|R11|deepgemm_sm120_paged_sm120_fp8_h32_p64_n2_sm120_paged_h32_p64_n2_b8_c4096_sm_120a|

|R12|deepgemm_sm120_paged_sm120_fp8_h32_p64_n4_sm120_paged_h32_p64_n4_b64_c16384_sm_120a|

|R13|deepgemm_sm120_paged_sm120_fp8_h32_p64_n4_sm120_paged_h32_p64_n4_b8_c4096_sm_120a|

|R14|deepgemm_sm120_paged_sm120_fp8_h64_p64_n1_sm120_paged_h64_p64_n1_b64_c16384_sm_120a|

|R15|deepgemm_sm120_paged_sm120_fp8_h64_p64_n1_sm120_paged_h64_p64_n1_b8_c4096_sm_120a|

|R16|deepgemm_sm120_paged_sm120_fp8_h64_p64_n2_sm120_paged_h64_p64_n2_b64_c16384_sm_120a|

|R17|deepgemm_sm120_paged_sm120_fp8_h64_p64_n2_sm120_paged_h64_p64_n2_b8_c4096_sm_120a|

|R18|deepgemm_sm120_paged_sm120_fp8_h64_p64_n4_sm120_paged_h64_p64_n4_b64_c16384_sm_120a|

|R19|deepgemm_sm120_paged_sm120_fp8_h64_p64_n4_sm120_paged_h64_p64_n4_b8_c4096_sm_120a|
|R20|deepgemm_sm120_paged_sm120_metadata_sm120_meta_b256_n4_sm_120a|
|R21|deepgemm_sm120_paged_sm120_metadata_sm120_meta_b64_n1_sm_120a|

#### Geomeans over all correct timed rows

Gate-failing performance rows remain in these geomeans; only rows
without valid correctness and timing are excluded and remain visible
above.

|Shape tag|Timed rows|Denominator|Source ms|Export ms|Source / Export|
|---|---:|---:|---:|---:|---:|
|all|21|21|0.039380|0.039324|1.001445x|
|logits|19|19|0.047525|0.047475|1.001068x|
|metadata|2|2|0.006602|0.006569|1.005031x|

Complete denominator: **true** (21/21).

All gates passed: **true** (21/21).

</details>

🤖 Generated with [Claude Code](https://claude.com/claude-code)

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [ea5d272](https://github.com/flashinfer-ai/flashinfer/commit/ea5d2728dc87f95ffe2bc72de1e100bcf0eb363a)

- **作者**: feih-nv
- **时间**: 2026-10-07T19:20:25Z
- **提交信息**: feat(moe): add the remaining Prims-TS quant pairs to the unified API (#5718)

## 📌 Description

Follow-up to #5289. The opt-in unified Prims-TS backend (`PrimsTsConfig`
/ `PrimsTsRunner`) already covers NVFP4×NVFP4 and BF16×BF16. This PR
wires the remaining quant pairs through the same adapter. It stays
opt-in: `PrimsTsConfig` is still not in `_DEFAULT_BACKEND`, so
`backend="auto"` never selects it.

### Quant pairs

| Pair | Weight view |
| --- | --- |
| MXFP4×MXFP8, MXFP4×BF16 | Same dictionary as `TrtllmFp4Config`
(`trtllm_fp4_routed`) |
| MXFP8×MXFP8 | Same dictionary as `TrtllmFp8BlockConfig`
(`trtllm_fp8_block`) |
| FP8PerTensor×FP8PerTensor | Same dictionary as
`TrtllmFp8PerTensorConfig` (`trtllm_fp8_per_tensor`) |
| DeepSeekFp8×DeepSeekFp8 | Scales and activations match
`TrtllmFp8BlockConfig`. Weight payloads are shuffled with epilogue tile
64 and must not be registered under `trtllm_fp8_block` |

MXFP4×MXFP8 keeps the public activation pack on the TRT-LLM compact
linear layout. `pack_inputs` pads that scale to the 16-column alignment
the Prims-TS GEMM reads, and views it back as `float8_e4m3fn` for the
staged routing kernel.

Activations follow the matching TRT-LLM runner: MXFP4×MXFP8 is SwiGLU /
GeGLU / SiTU / ReLU2, MXFP4×BF16 and DeepSeekFp8 are SwiGLU, FP8
per-tensor is SwiGLU / ReLU2, and MXFP8 is SwiGLU / GeGLU / ReLU2.
`intermediate_size` must be a multiple of 128. SM100 / SM103 only.

## 🔍 Related Issues

Follow-up to #5289.

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

`tests/moe/test_unified_moe_prims_ts.py` covers the new pairs. On SM100,
each pair was compared with the matching TRT-LLM runner (MXFP4×MXFP8,
MXFP4×BF16, MXFP8×MXFP8, DeepSeekFp8, FP8 per-tensor). CPU checks cover
the capability table and the generated activation matrix.

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

DeepSeekFp8 is the one view that is not interchangeable with TRT-LLM:
only the weight payload is shuffled. MXFP4×BF16 still xfails on SM103
because the TRT-LLM reference is disabled there.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

## Summary

* **New Features**
* Added Prims-TS support for MXFP4×MXFP8, MXFP4×BF16, per-tensor FP8,
DeepSeek FP8, and MXFP8 quantization pairs, with activation support
varying by pair.
* Added per-tensor FP8 scale handling and DeepSeek FP8 weight
preparation.
* **Bug Fixes**
* Added validation for unsupported quantization combinations, missing
scales, and unsupported routing or activation settings.
* **Documentation**
* Expanded quantization coverage and weight-preparation guidance, and
clarified that LoRA is out of scope.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [686d2fb](https://github.com/flashinfer-ai/flashinfer/commit/686d2fba0709962143f17160fe0b39072480f92b)

- **作者**: eigen
- **时间**: 2026-10-07T18:57:06Z
- **提交信息**: perf(cake_sparse_mla): FP8 H128 prologue rendezvous + BF16 SWA128 two-chunk online softmax (SM100/SM103) (#6193)

## Summary

`backend="cake"` DSv4 sparse-MLA (SM100 / SM103), performance-only
follow-up of the round-5 release, two changes: the
two FP8 H128 persistent programs (`fp8_h128_prefill_source_persistent`,
`fp8_h128_prefill_source_persistent_uniform`,
both architectures) trim their kernel prologue to a single cluster
rendezvous, and the BF16 SWA128 single-CTA program
(`bf16_swa128_single_cta`, Cake source
`flashinfer_blackwell_trtllm_sparse_mla_dsv4_seed_bf16_swa128_single_cta`,
both
architectures) runs a two-chunk online softmax over its two key halves.
Sparse-validity semantics, the host contract
(`flashinfer/mla/cake_dsv4.py`, `flashinfer/mla/_core.py`) and every
other program are unchanged. The prologue change
keeps the FP8 output bits; the SWA128 change keeps the precision class
(f32 accumulation, exact exp2/rcp paths, masks)
and moves output bits within the BF16 tolerance.

## What changed
- `csrc/cake_dsv4/{sm_103a,sm_100a}/`: the FP8 H128 persistent programs'
and the BF16 SWA128 single-CTA program's unit
sources regenerated from Cake `71583f34863` (Cake base `ee3118b9bc1`;
content-hashed `*_kernel.cu` names, the exact
files are listed below). Two prologue changes, each adopted on its own
paired measurement:
1. the persistent 2-CTA body ended its setup with a third cluster
barrier after the mbarrier/TMEM publication; the
backend already publishes the mbarrier inits and the allocated TMEM
address to both CTAs of the pair, so the
     trailing rendezvous ordered nothing further and is removed;
2. the TMEM allocation now overlaps the mbarrier-init publication: the
`barrier.cluster.arrive/wait` pair before
`tcgen05.alloc` becomes a `__syncwarp`, and the single remaining
post-allocation cluster barrier publishes both the
inits and the TMEM address to the pair (the setup order the
DeepGEMM-derived programs already use).
- `bf16_swa128_single_cta` (two-chunk online softmax): QK of each key
half lands in its own TMEM S half; the softmax of
half 0 and its P overlap the second half's K stages; the halves are
merged exactly in f32 (`alpha0 = exp2(m0*c - m*c)`,
`l = fma(l0, alpha0, l1)` plus the sink term); PV0/PV1 accumulate into
separate f32 TMEM O0/O1 accumulators and the
epilogue forms `O = fma(O0, alpha0, O1)` before the unchanged `rcp(l) *
bmm2` scale.
The render diff against the round-5 tree shows the two FP8 H128
persistent programs and the SWA128 single-CTA program
differing per architecture; everything else renders byte-identically
(the SWA128 step alone, against the prologue-only
tree `8d7ee6699ee`: 30 sm_100a / 29 sm_103a programs rendered, only
`bf16_swa128_single_cta` changed).
- Export protocol unchanged (197 shapes per arch = 94 canonical + 103
hardening/export rows, correctness + source/export
timing parity gates; rows that fail only a timing gate on byte-identical
programs are re-measured in place from the
closed prior, as in the previous release). sm_103a: 197/197 shapes
passed (correctness 197/197) after one in-place re-measure of
decode-000005 (bf16_h64_compressed; source_over_export 0.9567 in the
full run, 1.0000 on the re-measure; output correct in both). sm_100a:
196/197 shapes passed (correctness 197/197) after one in-place
re-measure: hardening-000105 (bf16_h64_compressed) passed on the
re-measure; hardening-000016 (bf16_h64_prefill) fails only the
directional_disagreement measurement gate in both the full run and the
re-measure with correct output (source_over_export 0.9885 / 1.0007) -
the documented arm-order artifact of the export gate, gate not relaxed,
exception subject to review. Release commit: `94742c9cdd56`
(sm_103a `47e59b6201dd`, sm_100a `94742c9cdd56`); it supersedes the
previous head of this branch (`e7b528e330f0`), which
  carried the prologue change only.
- Further programs appear as renames in the diff because the kernel
symbol and the host-shim namespace are content-hashed
over the export identity: their kernel bodies are byte-identical (the
1-line change in each `*_kernel.cu` is the
symbol, the 16-line change in each `*_binding.cu` the symbol/namespace
tokens); the exact files are listed below.
Three architecture-neutral programs (`bf16_h32_topk128x_early_v47`,
`bf16_h64_compressed_reduce`, `split_reduce`) move
from the per-arch directories to `common/` with unchanged text, and the
previous release's now-unreferenced hashed units
  are retired.

## Measured (paired CUPTI ABBA, kernel-sum medians, identical-text
control within +-0.5 %)
- fp8_h128 persistent rows (32 = 2 shards). Change 1 against the release
programs: geomean B/A **0.984 on GB300** and
**0.9826 on B200**, every row faster, A/A spread <= 0.36 %. Change 2
against change 1: geomean B/A **0.9783 on GB300**
and **0.9778 on B200**, 27/32 rows <= 0.99 and none >= 1.01 on both,
controls 0.9999 / 1.0003. The two paired steps
compound to about -3.7 % (GB300) / -3.9 % (B200); both are fixed
per-launch costs, so short rows gain the most (the floor
  microbenchmarks put one cluster barrier at ~0.3 us on B200).
- bf16 swa128 single-CTA rows (8 decode/hardening rows = the full
single-CTA set). Two-chunk online softmax against the
prologue-only programs: **B200** geomean B2/A2 **0.9441**, 8/8 rows <=
0.99, identical-text control 0.9963, A/A spread
0.46 % (about -5.6 %); **GB300** geomean B2/A2 0.9836 (4/8 rows <= 0.99,
0 rows >= 1.01, identical-text control 0.9981, A/A spread 0.00 %), about
-1.6 %.
- No other route changes (render diff), so no regression check is needed
elsewhere.

## Gates
- Prologue change (Cake tree `8d7ee6699ee`): compute-sanitizer synccheck
(decode-000030, hardening-000050,
hardening-000003) and memcheck (decode-000030, hardening-000050): `ERROR
SUMMARY: 0 errors`, every per-row process
exit 0, on both architectures (B200 and GB300); `check_rows` 134 rows x
all mutation axes **839/839 passed** on both
architectures; CPU rule tests 194 passed (both); checksel bit report on
the 13 affected fp8_h128 rows: 13/13 passed on
both architectures (informational; bits may change across the prologue
changes but did not).
- Two-chunk online softmax (Cake tree `71583f34863`, both
architectures): compute-sanitizer synccheck (decode-000000,
hardening-000006, hardening-000071) and memcheck (decode-000000,
hardening-000006): `ERROR SUMMARY: 0 errors`, exit 0,
on B200 and GB300; `check_rows` **839/839 passed** on both; CPU rule
tests 194 passed (both); checksel bit report on the
8 affected bf16 swa128 single-CTA rows: 8/8 passed on both; ptxas
resource line unchanged against the prologue-only
program (128 registers, 0 B stack, 0 B spills, both architectures) (bits
change against the prologue-only programs, within the BF16 tolerance, as
expected for the
  re-associated merge).
- Fresh-clone FlashInfer DSv4 tests at the release commit: `519 passed,
4 skipped in 168 s (fresh clone at 94742c9cdd56)` / `519 passed, 4
skipped in 216 s (fresh clone at 94742c9cdd56)`.

## Changed files
```
     ...ke_dsv4_bf16_h32_topk128x_early_v47_binding.cu} |    0
     ...ake_dsv4_bf16_h32_topk128x_early_v47_kernel.cu} |    0
     ...ake_dsv4_bf16_h64_compressed_reduce_binding.cu} |    0
     ...cake_dsv4_bf16_h64_compressed_reduce_kernel.cu} |    0
     .../cake_dsv4_split_reduce_binding.cu}             |    0
     .../cake_dsv4_split_reduce_kernel.cu}              |    0
     .../cake_dsv4_2beee9997128cc45a86b_binding.cu}     |   16 +-
     ...cu => cake_dsv4_2beee9997128cc45a86b_kernel.cu} |    2 +-
     .../cake_dsv4_4f1bc4343283f1ba5536_binding.cu}     |   16 +-
     ...cu => cake_dsv4_4f1bc4343283f1ba5536_kernel.cu} |    7 +-
     .../cake_dsv4_74706ad372b69a30483d_binding.cu}     |   16 +-
     ...cu => cake_dsv4_74706ad372b69a30483d_kernel.cu} |    2 +-
     .../cake_dsv4_8e62179077cf2a4d12f9_kernel.cu       | 1036 -------------
     ...u => cake_dsv4_afe09a82c14f8bd895f4_binding.cu} |   16 +-
     ...cu => cake_dsv4_afe09a82c14f8bd895f4_kernel.cu} |    7 +-
     ...u => cake_dsv4_b3138c1168ef949b4019_binding.cu} |   16 +-
     ...cu => cake_dsv4_b3138c1168ef949b4019_kernel.cu} |    2 +-
     ...u => cake_dsv4_c42c0d4632dca5f570a8_binding.cu} |   16 +-
     ...cu => cake_dsv4_c42c0d4632dca5f570a8_kernel.cu} |    2 +-
     ...u => cake_dsv4_c602c3f805921b955ae5_binding.cu} |   16 +-
     ...cu => cake_dsv4_c602c3f805921b955ae5_kernel.cu} |    2 +-
     ...u => cake_dsv4_d59492e451e80c110411_binding.cu} |   16 +-
     ...cu => cake_dsv4_d59492e451e80c110411_kernel.cu} |    2 +-
     ...u => cake_dsv4_fa5539cb1afb7555dff5_binding.cu} |   14 +-
     ...cu => cake_dsv4_fa5539cb1afb7555dff5_kernel.cu} |    2 +-
     .../cake_dsv4_fd59534f8fb24edd3529_binding.cu}     |   18 +-
     .../cake_dsv4_fd59534f8fb24edd3529_kernel.cu       | 1574 +++++++++++++++++++
     .../cake_dsv4_1a99f26bd105cfc54a61_binding.cu}     |   16 +-
     ...cu => cake_dsv4_1a99f26bd105cfc54a61_kernel.cu} |    2 +-
     .../cake_dsv4_27b20805ac082d6893b4_kernel.cu       | 1064 -------------
     .../cake_dsv4_385acfbc8606f3d335b2_binding.cu}     |   18 +-
     .../cake_dsv4_385acfbc8606f3d335b2_kernel.cu       | 1604 ++++++++++++++++++++
     .../cake_dsv4_51c1b1cf8ced19ef9080_binding.cu      |   85 --
     .../cake_dsv4_51c1b1cf8ced19ef9080_kernel.cu       |  156 --
     .../cake_dsv4_8a0ab008d1081aaee107_binding.cu      |  357 -----
     .../cake_dsv4_8a0ab008d1081aaee107_kernel.cu       | 1435 -----------------
     ...u => cake_dsv4_8c012a14f26c0b3fc996_binding.cu} |   16 +-
     ...cu => cake_dsv4_8c012a14f26c0b3fc996_kernel.cu} |    2 +-
     .../cake_dsv4_985b70c1f95a44b1a915_binding.cu}     |   16 +-
     ...cu => cake_dsv4_985b70c1f95a44b1a915_kernel.cu} |    2 +-
     ...u => cake_dsv4_a3e160c0c67071fa998a_binding.cu} |   16 +-
     ...cu => cake_dsv4_a3e160c0c67071fa998a_kernel.cu} |    2 +-
     .../cake_dsv4_ac39da4cf9885a0981e8_binding.cu}     |   16 +-
     ...cu => cake_dsv4_ac39da4cf9885a0981e8_kernel.cu} |    7 +-
     .../cake_dsv4_b9c4afa107e20bf48d99_binding.cu      |   85 --
     .../cake_dsv4_b9c4afa107e20bf48d99_kernel.cu       |  261 ----
     ...u => cake_dsv4_c3cf2c612e13bf182910_binding.cu} |   16 +-
     ...cu => cake_dsv4_c3cf2c612e13bf182910_kernel.cu} |    2 +-
     ...u => cake_dsv4_f1ee6630f05cf65f5f69_binding.cu} |   14 +-
     ...cu => cake_dsv4_f1ee6630f05cf65f5f69_kernel.cu} |    2 +-
     ...u => cake_dsv4_f3b968292b4c99769293_binding.cu} |   16 +-
     ...cu => cake_dsv4_f3b968292b4c99769293_kernel.cu} |    2 +-
     ...u => cake_dsv4_f4f571730c20919320eb_binding.cu} |   16 +-
     ...cu => cake_dsv4_f4f571730c20919320eb_kernel.cu} |    7 +-
     flashinfer/jit/cake_dsv4.py                        |  150 +-
     55 files changed, 3435 insertions(+), 4748 deletions(-)
```

## Tests
- `tests/mla/test_cake_dsv4.py`,
`tests/mla/test_cake_dsv4_hardening.py`: unchanged; run on a fresh clone
at the
release commit on both architectures (results above). The 8 bf16 swa128
single-CTA rows are part of the 197 export
rows per architecture, whose correctness gate is reported in the export
summaries above.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [52863f5](https://github.com/flashinfer-ai/flashinfer/commit/52863f595355eba946fcc2ab01c121662443b30e)

- **作者**: eigen
- **时间**: 2026-10-07T18:25:33Z
- **提交信息**: feat(cake_deepgemm): SM120 paged FP8 MQA lightning-indexer logits for RTX PRO 6000 / RTX 5090 (experimental generated-program export) (#6180)

<!-- .github/pull_request_template.md -->

## 📌 Description

Developed by the **CAKE team**.

Adds the **SM120a** (RTX PRO 6000 Blackwell / RTX 5090, compute
capability 12.0) paged FP8 MQA-logits route of the DeepSeek
sparse-attention "lightning indexer" decode path as a Cake
generated-program export, family `deepgemm_sm120_paged_mqa_logits`.
Until now the only CUDA implementation of this stage on SM120 was
DeepGEMM's `fp8_fp4_paged_mqa_logits` (vLLM: "Sparse Attention Indexer
CUDA op requires DeepGEMM support"; see vllm-project/vllm#59725 and
vllm-project/DeepGEMM#28). The FlashInfer Cake MQA-logits / DSA-indexer
families (`deepgemm_dense_mqa`, `cake_dsa_indexer`) are tcgen05/TMEM
programs and do not compile on SM120.

**Kernel.** An exact Weave-IR reproduction of DeepGEMM's
`sm120_fp8_paged_mqa_logits.cuh` +
`scheduler/sm120_paged_mqa_logits.cuh` (DeepGEMM `dev` + #28): 384
threads = 8 math warps in 64-row groups (`mma.sync.m16n8k32` E4M3 →
FP32, KV as the A operand via 128B-swizzled `ldmatrix`, Q as the B
operand) + 4 TMA warps (per-group 3-stage KV ring of 64-row tiles with
their FP32 scales, 2-stage Q/weights pipe), `setmaxnreg` 232/40,
persistent per-SM schedule, weighted ReLU + quad shuffle reduction +
FP32 store, PDL. Logits are **bitwise identical** to DeepGEMM's SM120
kernel on every validated configuration (Cake MR: gitlab-master
`averyh/r94494673bb0150eeffa896f7!1283`, producer commit
`aaee55d92d461a5e3740181f9e3a639f2e42b20a`).

**Programs / API** (`flashinfer/sm120_paged_mqa_logits.py`, backend
package `flashinfer/experimental/deepgemm_sm120_paged_mqa_logits/`,
generated sources
`csrc/experimental/deepgemm_sm120_paged_mqa_logits/generated/`): 9
logits programs — 32 heads × pages {128, 64} × next_n {1, 2, 4}
(DeepSeek-V4.1-Flash geometry; 128-state pages native, i.e. the
host-side change of DeepGEMM#28 is not needed) and 64 heads × page 64 ×
next_n {1, 2, 4} (DeepSeek-V3.2) — plus the single-warp
scheduler-metadata program. The Python surface mirrors DeepGEMM's call
shape so a serving engine can switch routes without re-plumbing:
`get_paged_mqa_logits_metadata(context_lens, page_kv, num_sms)` (a real
launch) and `fp8_paged_mqa_logits(q, kv_cache, weights, context_lens,
block_table, schedule_meta, max_context_len, clean_logits=False)` (one
FFI submission, two launches with per-stage PDL), plus
`prepare_sm120_paged_mqa_logits(...)` returning a CUDA-graph-replayable
plan. The fused `u8 [pages, page_kv, 1, 132]` cache (values block, then
one FP32 scale per token) is read in place; a row-padded 2-D view is
accepted. `clean_logits=False` semantics: cells at or past a token's own
context length are unspecified (the consumer masks by length).
`clean_logits=True`, varlen `indices`, next_n 3 and FP4 caches are
rejected explicitly.

## 🔍 Related Issues

Tracking issue: #4254 (the CAKE generated-kernel progress tracker; its
entry for this PR names the owner, the reason for the experimental path
and the graduation plan). Motivation: vllm-project/vllm#59725 (the SM120
"Sparse Attention Indexer CUDA op requires DeepGEMM support" path) and
vllm-project/DeepGEMM#28.

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

- `tests/experimental/test_sm120_paged_mqa_logits.py`: 10 passed on RTX
PRO 6000 Blackwell Server Edition (driver 595.84.01): FP32 torch
reference at FP8-class tolerance (atol/rtol 0.1) over heads × pages ×
next_n × batch, bitwise source/export parity, padded block strides,
CUDA-graph plan replay.
- Export receipts (source = Cake production plan vs the generated
FlashInfer programs; same-session paired CUPTI cold-L2 medians,
symmetric external CUDA-graph replay, 3 counterbalanced groups × 8
graphs): **21/21 gates passed**, complete denominator, geomean
source/export **1.0013x (logits 1.0014x over 19 rows, metadata 1.0000x
over 2)** (per-row 0.9959x–1.0172x). Table below.
- Producer gates (Cake MR !1283): e2e compile + static analysis 24
passed, GPU correctness 6 passed, `bench-regression` 212–213 TFLOPS vs
the calibrated sm_120a floor 200, `compute-sanitizer` synccheck +
memcheck 0 errors.

### Performance

Exact port ⇒ parity with DeepGEMM's SM120 kernel on identical inputs:
geomean Cake/DeepGEMM 0.9995 over 21 representative decode rows (batch
1–256, next_n 1/2/4, context 4K–64K, pages 128/64, 32/64 heads), all
rows bitwise-equal. next_n 1 rows at large batch reach 0.82–0.89 of the
HBM floor; a lever round on the producer (same programs regenerated)
follows separately.

## 🔬 Experimental Track

<!-- Only for PRs submitted under the experimental policy
(CONTRIBUTING.md → "Experimental APIs and Backends").
     Leave this section untouched for normal PRs. -->

- [x] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.
Tracking issue: #4254
- [x] The tracking issue names an owner, the reason for the experimental
path, and a graduation plan with a target release.
- [x] Core changes are limited to a thin entry point (signature, shared
validation, feature-gate check, backend selection, handoff):
`flashinfer/sm120_paged_mqa_logits.py` only; everything else lives in
`flashinfer/experimental/deepgemm_sm120_paged_mqa_logits/`,
`csrc/experimental/deepgemm_sm120_paged_mqa_logits/` and
`tests/experimental/`.
- [x] Tests live in `tests/experimental/` and were validated on the
intended hardware (RTX PRO 6000 Blackwell Server Edition); runnable
example: `benchmarks/bench_sm120_paged_mqa_logits.py`.
- [x] Nothing is registered in `flashinfer/aot.py`, and no experimental
backend is reachable from `backend="auto"` without
`FLASHINFER_ALLOW_EXPERIMENTAL_AUTO_BACKENDS=1`. (Calling an
`@flashinfer_experimental_api` or naming a backend explicitly is itself
the opt-in and needs no environment variable.) The route is reached only
through the three `@flashinfer_experimental_api` entry points.
- [x] **Test scope declared below.** The experimental CI lane runs
exactly these targets, so keep them as narrow as the change allows.

<!-- Required for experimental PRs. Replace the commented lines below
with your targets.
Do not delete the fence or change its `experimental-tests` tag — the
experimental-track
watcher reads it verbatim to decide which targets to ask CI for. -->

```experimental-tests
tests/experimental/test_sm120_paged_mqa_logits.py
```

## Reviewer Notes

**Unsupported (rejected explicitly).** `clean_logits=True`, varlen
`indices`, next_n 3, FP4 (E2M1) indexer caches, head counts other than
32/64, page sizes other than those listed, non-SM120 devices (the
programs are `sm_120a` fatbins; SM121 is not shipped in this PR).

**Formatting.** The generated `.cu` sources are formatted with the
repository's pinned clang-format (the `mirrors-clang-format` v19.1.1
pre-commit hook); the delivered test file passes on the formatted tree
(10 passed). The producer-side exporter now formats these sources with
the same pinned release at delivery time; verified by a re-export: its
sources pass the hook unchanged and the delivered Python / test /
benchmark files are byte-identical to this tree. Because this first
delivery was formatted by the hook after the programs had been named,
the generated file names (content hashes) and the catalog's
informational `closure_sha256` fields derive from the pre-format text;
the next export (the planned lever round) renames the programs and
regenerates the catalog as a full re-delivery, with no functional
difference.

**Pre-commit.** The `clang-format` hook was run with `pre-commit` on the
delivered device sources and its reformat is part of this commit; the
repository's `pre-commit` CI job passes on the full diff.

<details><summary>Export receipts (21 shapes, source = Cake production
plan vs the generated FlashInfer programs; same-session paired CUPTI
cold-L2 medians, symmetric external CUDA-graph replay, 8 graphs per arm,
3 counterbalanced groups × 600 calls; RTX PRO 6000 Blackwell Server
Edition, driver 595.84.01)</summary>

|Shape|Route|Source ms|Export ms|Source / Export|Baseline|Baseline
ms|Baseline / Export|Verdict|
|---|---|---:|---:|---:|---|---:|---:|---|

|sm120_paged_h32_p128_n1_b8_c4096_sm_120a|R3|0.015040|0.015040|1.0000x|—|—|—|pass|

|sm120_paged_h32_p128_n1_b64_c16384_sm_120a|R1|0.136032|0.136033|1.0000x|—|—|—|pass|

|sm120_paged_h32_p128_n2_b8_c4096_sm_120a|R5|0.015680|0.015744|0.9959x|—|—|—|pass|

|sm120_paged_h32_p128_n2_b64_c16384_sm_120a|R4|0.139744|0.139680|1.0005x|—|—|—|pass|

|sm120_paged_h32_p128_n4_b8_c4096_sm_120a|R7|0.015168|0.014912|1.0172x|—|—|—|pass|

|sm120_paged_h32_p128_n4_b64_c16384_sm_120a|R6|0.190625|0.191280|0.9966x|—|—|—|pass|

|sm120_paged_h32_p64_n1_b8_c4096_sm_120a|R9|0.014720|0.014720|1.0000x|—|—|—|pass|

|sm120_paged_h32_p64_n1_b64_c16384_sm_120a|R8|0.145217|0.145024|1.0013x|—|—|—|pass|

|sm120_paged_h32_p64_n2_b8_c4096_sm_120a|R11|0.015489|0.015424|1.0042x|—|—|—|pass|

|sm120_paged_h32_p64_n2_b64_c16384_sm_120a|R10|0.146336|0.146721|0.9974x|—|—|—|pass|

|sm120_paged_h32_p64_n4_b8_c4096_sm_120a|R13|0.015585|0.015584|1.0001x|—|—|—|pass|

|sm120_paged_h32_p64_n4_b64_c16384_sm_120a|R12|0.201953|0.202369|0.9979x|—|—|—|pass|

|sm120_paged_h64_p64_n1_b8_c4096_sm_120a|R15|0.014657|0.014560|1.0067x|—|—|—|pass|

|sm120_paged_h64_p64_n1_b64_c16384_sm_120a|R14|0.146337|0.146113|1.0015x|—|—|—|pass|

|sm120_paged_h64_p64_n2_b8_c4096_sm_120a|R17|0.015840|0.015840|1.0000x|—|—|—|pass|

|sm120_paged_h64_p64_n2_b64_c16384_sm_120a|R16|0.143937|0.143744|1.0013x|—|—|—|pass|

|sm120_paged_h64_p64_n4_b8_c4096_sm_120a|R19|0.016240|0.016224|1.0010x|—|—|—|pass|

|sm120_paged_h64_p64_n4_b64_c16384_sm_120a|R18|0.196385|0.195425|1.0049x|—|—|—|pass|

|sm120_paged_h32_p128_n1_b64_c4096_pad512_sm_120a|R2|0.044576|0.044576|1.0000x|—|—|—|pass|
|sm120_meta_b64_n1_sm_120a|R21|0.005184|0.005184|1.0000x|—|—|—|pass|
|sm120_meta_b256_n4_sm_120a|R20|0.008736|0.008736|1.0000x|—|—|—|pass|

**Route legend**

|Key|Route|
|---|---|

|R1|deepgemm_sm120_paged_sm120_fp8_h32_p128_n1_sm120_paged_h32_p128_n1_b64_c16384_sm_120a|

|R2|deepgemm_sm120_paged_sm120_fp8_h32_p128_n1_sm120_paged_h32_p128_n1_b64_c4096_pad512_sm_120a|

|R3|deepgemm_sm120_paged_sm120_fp8_h32_p128_n1_sm120_paged_h32_p128_n1_b8_c4096_sm_120a|

|R4|deepgemm_sm120_paged_sm120_fp8_h32_p128_n2_sm120_paged_h32_p128_n2_b64_c16384_sm_120a|

|R5|deepgemm_sm120_paged_sm120_fp8_h32_p128_n2_sm120_paged_h32_p128_n2_b8_c4096_sm_120a|

|R6|deepgemm_sm120_paged_sm120_fp8_h32_p128_n4_sm120_paged_h32_p128_n4_b64_c16384_sm_120a|

|R7|deepgemm_sm120_paged_sm120_fp8_h32_p128_n4_sm120_paged_h32_p128_n4_b8_c4096_sm_120a|

|R8|deepgemm_sm120_paged_sm120_fp8_h32_p64_n1_sm120_paged_h32_p64_n1_b64_c16384_sm_120a|

|R9|deepgemm_sm120_paged_sm120_fp8_h32_p64_n1_sm120_paged_h32_p64_n1_b8_c4096_sm_120a|

|R10|deepgemm_sm120_paged_sm120_fp8_h32_p64_n2_sm120_paged_h32_p64_n2_b64_c16384_sm_120a|

|R11|deepgemm_sm120_paged_sm120_fp8_h32_p64_n2_sm120_paged_h32_p64_n2_b8_c4096_sm_120a|

|R12|deepgemm_sm120_paged_sm120_fp8_h32_p64_n4_sm120_paged_h32_p64_n4_b64_c16384_sm_120a|

|R13|deepgemm_sm120_paged_sm120_fp8_h32_p64_n4_sm120_paged_h32_p64_n4_b8_c4096_sm_120a|

|R14|deepgemm_sm120_paged_sm120_fp8_h64_p64_n1_sm120_paged_h64_p64_n1_b64_c16384_sm_120a|

|R15|deepgemm_sm120_paged_sm120_fp8_h64_p64_n1_sm120_paged_h64_p64_n1_b8_c4096_sm_120a|

|R16|deepgemm_sm120_paged_sm120_fp8_h64_p64_n2_sm120_paged_h64_p64_n2_b64_c16384_sm_120a|

|R17|deepgemm_sm120_paged_sm120_fp8_h64_p64_n2_sm120_paged_h64_p64_n2_b8_c4096_sm_120a|

|R18|deepgemm_sm120_paged_sm120_fp8_h64_p64_n4_sm120_paged_h64_p64_n4_b64_c16384_sm_120a|

|R19|deepgemm_sm120_paged_sm120_fp8_h64_p64_n4_sm120_paged_h64_p64_n4_b8_c4096_sm_120a|
|R20|deepgemm_sm120_paged_sm120_metadata_sm120_meta_b256_n4_sm_120a|
|R21|deepgemm_sm120_paged_sm120_metadata_sm120_meta_b64_n1_sm_120a|

</details>

🤖 Generated with [Claude Code](https://claude.com/claude-code)

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [059c01a](https://github.com/flashinfer-ai/flashinfer/commit/059c01ac307faea8cef1bc69bae68d3e6cd1ae32)

- **作者**: John Calderon
- **时间**: 2026-10-07T18:11:37Z
- **提交信息**: [Patch] Enable SM107 on kda-prefill-cute (#6201)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->
This PR enables SM107 for kda prefill in cute dsl, this change is added
to support running Unit Test in VLLM project that depend on this.
Such as:
tests/models/kimi_k3/test_kda.py.

- test_kda_prefill_correctness[flashinfer-bf16]

- test_kda_prefill_near_collinear_keys_remain_finite[flashinfer]

- test_flashinfer_kda_prefill_breakable_graph_cross_stream

## 🔍 Related Issues

<!-- Link any related issues here -->
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


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* KDA prefill using CuTe DSL now supports devices with compute
capability 10.7, alongside previously supported 10.0 and 10.3 devices.
These devices can now pass the architecture eligibility checks for this
prefill path. No other user-facing changes are included in this update.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: John Calderon <jcalderon@nvidia.com>

### [a9966bf](https://github.com/flashinfer-ai/flashinfer/commit/a9966bff43fd7e5ae59845461d80d02d0e48149c)

- **作者**: Vincent
- **时间**: 2026-10-07T17:46:25Z
- **提交信息**: feat(moe): enable TRTLLM-GEN FP8 routed MoE on SM107 (Rubin) (#5390)

## What

Enables the TRTLLM-GEN FP8 routed MoE path on SM107 (Rubin), held back
by a static architecture allowlist.

| path | gate(s) removed | GR100 (cc 10.7) result |
|---|---|---|
| TRTLLM-GEN FP8 routed MoE (block + per-tensor) | `fused_moe/api.py`
`_TRTLLM_ROUTED_FP8_ARCHS = (100, 103)` → `+107`; two test predicates |
`tests/moe/test_unified_moe_fp8.py`: 49 skipped → **49 passed** |

## Why these are safe

**TRTLLM-GEN FP8.** The sibling BF16 / MxInt4 / FP4 table already listed
107; only the FP8 one didn't. Everything below the Python allowlist was
already in place: the consolidated `batched_gemm` package ships the
sm107a FP8 set (192 `E4m3xE4m3` + 276 `dsFp8` kernels, a 1:1 mirror of
the sm100f set), `csrc/trtllm_batched_gemm_runner.cu` dispatches
`CudaArch::Sm107a`, and `fused_moe/core.py` already selects the Rubin
cubin set for cc 10.7.

## Validation

GR100 (cc 10.7, driver 620.05), image
`flashinfer-ci:cu134-nightly-py3.67144516-whl-amd64` with the CI job's
own `nvidia-cutlass-dsl[cu13]==4.8.0.dev0` override, against an
`upstream/main` baseline on the same tree/image — numbers in the table
above; **zero new failures**.

## Caveats

- Validated on x86_64 only; the Rubin CI nodes are arm64.
- The `_TRTLLM_ROUTED_FP8_ARCHS` widening also wires the FP8 / MXFP8 /
DeepSeek-FP8 **in-kernel-routing** fuzz backends on SM107 (they are
`TrtllmFp8BlockConfig` / `TrtllmFp8PerTensorConfig` under the hood):
`tests/moe/test_unified_moe_fuzz.py` 164 passed / 95 skipped → **247
passed / 12 skipped**, 0 failures; the remaining 12 skips are non-SM107
backends (cutlass_fp8_block / w4a8 / humming, b12x on SM120) and an
MxInt4 divisibility constraint.
- Also includes a test-only fix: `tests/moe_ep/test_compute_bridge.py`
pinned MXFP8 quantization to 10.0/10.3 (10 passed on SM107 once
widened).
- Not in this PR: the `trtllm_gen_routing.py`
`_TRTLLM_GEN_ROUTING_SUPPORTED_CC` list also lacks 107 but no test
currently exercises it.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
  * TensorRT-LLM FP8 backends now support SM107 (Rubin) GPUs.
* **Tests**
* Updated FP8 routed MoE architecture checks to recognize SM107 support.
* Extended MXFP8 pre-dispatch quantization test coverage to run on
SM107; other unsupported architectures remain skipped.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Vincent Tombari <Vinnie6167@users.noreply.github.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [b6b4f1e](https://github.com/flashinfer-ai/flashinfer/commit/b6b4f1ec35c40995b9901fba8fb93267c45ffb6b)

- **作者**: Wei-Cheng (Wayne) Chiu
- **时间**: 2026-10-07T16:45:35Z
- **提交信息**: test: bound peak memory in mxfp4 groupwise group GEMM test (32GB OOM) (#3594)

## Description

`test_mxfp8_mxfp4_groupwise_group_gemm` OOMs on ~32GB GPUs (5090 CI
runner) in several large cases (#3527). Profiling the failing ids shows
the dominant allocation is the **reference quantization**:
`quantize_e2m1` + the tiled-scale math materialize ~10 fp32 temporaries
the size of the operand, so a single case peaks at ~11GB; on a 32GB card
the accumulated test session then dies inside `assert_close` (the 360MB
allocation in the issue is just the straw).

Fix (test-only):
- `quantize_tensor`: chunk over the leading dim (~32M elements/chunk) —
**byte-identical output** (verified `torch.equal` chunked vs unchunked
for both 2-D A and 3-D B operands), bounds the temporary footprint.
- free the fp32 sources (`a_val`/`b_val`) after quantization + the
padded scale chunk list.
- `assert_close_chunked`: row-chunked comparison, same elements checked,
caps the comparison temporaries.

Measured peak (RTX PRO 6000 Blackwell, the failing ids from the issue,
`torch.cuda.max_memory_allocated`):

| case (g, m, n, k) | before | after |
|---|---|---|
| 8, 128, 2879, 8192 | 10.96 GiB | **2.10 GiB** |
| 8, 128, 4096, 4096 | 7.36 GiB | **2.33 GiB** |
| 8, 256, 2879, 4096 | 5.57 GiB | **1.77 GiB** |
| 8, 256, 4096, 4096 | 7.38 GiB | **2.35 GiB** |
| 8, 512, 2879, 4096 | 5.61 GiB | **1.81 GiB** |

The failing ids also pass under a 31.36GiB
`set_per_process_memory_fraction` cap emulating the CI runner, with the
real SM120 kernels.

## Related Issues

Fixes #3527.

## Pull Request Checklist

### Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

## Reviewer Notes

Test-only change; kernels untouched. The honest caveat: individual
failing ids fit even unfixed when run alone under the 32GB cap — the CI
OOM needs the accumulated multi-case session, so the validation here is
the measured 3–5× peak reduction + byte-identity rather than an exact CI
reproduction. AI-assisted (Claude Code), reviewed and measured by me on
hardware.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Tests**
* Improved reliability of large-data GEMM test runs by reducing memory
pressure during verification and cleanup.
* Large tensor results are now checked in manageable portions, while
smaller cases continue to use direct comparisons.
* Test data and intermediate results are released when no longer needed,
helping reduce memory use during execution.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: Cindy Zhang <cindyz@nvidia.com>

### [35821bc](https://github.com/flashinfer-ai/flashinfer/commit/35821bcbf5e967e3b53ff33e6552639e54fcf551)

- **作者**: Qidong Su
- **时间**: 2026-10-07T16:23:25Z
- **提交信息**: feat(moe): add Rubin locality-domain execution (#5276)

Add per-domain weight sharding and green-context fan-out for W4A4 MoE,
including localized/full-path autotuning.

<!-- .github/pull_request_template.md -->

## 📌 Description

Add locality-domain execution support to the Rubin SM107 CuTe DSL W4A4
fused-MoE path.

The caller can provide one weight shard and one long-lived green-context
stream per locality domain, together with the per-domain SM count.
FlashInfer then:

- runs FC1 concurrently across the two domains, with each domain
producing a disjoint half of the intermediate output;
- runs FC2 concurrently across the two domains, with each domain
producing a disjoint half of the hidden output;
- optionally overlaps the fused-finalize output memset on a separate
stream;
- sizes each persistent grid using the per-domain SM count;
- gives localized and full-width runners distinct autotuning cache keys;
- optionally autotunes both runners and dispatches the faster path for
each profiled shape;

The localized path is intentionally restricted to the configuration
implemented and validated here: Rubin SM107, W4A4, exactly two
equal-width shards, fused finalize, and no per-token activation scales.
Unsupported combinations fail explicitly instead of silently falling
back.



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
- [] All tests are passing (`unittest`, etc.).

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

* **New Features**
* Added localized W4A4 MoE execution on supported Rubin GPUs, processing
output partitions with two weight shards.
* Added controls for SM allocation and stream selection, plus an option
to include standard execution during autotuning.
* Preserved float16 and bfloat16 output dtypes in localized and standard
execution.

* **Bug Fixes**
  * Adjusted active-cluster counts when using fewer SMs.
* Added validation to reject unsupported localized output buffers and
execution settings.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Qidong Su <qidongs@nvidia.com>
Co-authored-by: Max Hu <maxhu@nvidia.com>
Co-authored-by: Alex Yang <aleyang@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [d71cc4b](https://github.com/flashinfer-ai/flashinfer/commit/d71cc4b38c2ebf4c289171bfbaf702c1353c9d19)

- **作者**: Cindy Zhang
- **时间**: 2026-10-07T16:13:31Z
- **提交信息**: fix(rope): gate cuTile FP8 quantization on SM89+ (#6188)

Fail fast before cuTile autotuning on architectures that do not support
FP8 output, and skip only the unsupported SM86 parameter matrix while
preserving other cuTile coverage.

<!-- .github/pull_request_template.md -->

## 📌 Description

Fix the cuTile RoPE FP8 test failures on SM86 GPUs.

The cuTile implementation produces FP8 (`float8_e4m3fn`) output, which
is unsupported on SM86. This caused 48 parameterized failures during
cuTile autotuning, eventually reported as `No valid config found in
search space`.

- Reject `backend="cutile"` FP8 RoPE quantization on architectures older
than SM89 with a clear `NotImplementedError`.
- Skip only the unsupported cuTile FP8 parameter combinations on
pre-SM89 GPUs.
  - Preserve the remaining cuTile test coverage on SM86.
- Add a CPU-safe regression test that verifies the architecture guard
runs before cuTile import or autotuning.

## 🔍 Related Issues

https://github.com/flashinfer-ai/flashinfer/issues/6184

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
- [ ] All tests are passing (`unittest`, etc.).
The targeted regression test passed in the CUDA 13.0 FlashInfer CI
image:

  ```text

tests/attention/test_rope.py::test_rope_quantize_fp8_cutile_rejects_pre_sm89
```

## 🔬 Experimental Track

<!-- Only for PRs submitted under the experimental policy (CONTRIBUTING.md → "Experimental APIs and Backends").
     Leave this section untouched for normal PRs. -->

- [ ] This PR is **experimental**: it adds or changes code under `flashinfer/experimental/` and/or an `@flashinfer_experimental_api`. Tracking issue: #
  - [ ] The tracking issue names an owner, the reason for the experimental path, and a graduation plan with a target release.
  - [ ] Core changes are limited to a thin entry point (signature, shared validation, feature-gate check, backend selection, handoff).
  - [ ] Tests live in `tests/experimental/` and were validated on the intended hardware; a runnable example is included.
  - [ ] Nothing is registered in `flashinfer/aot.py`, and no experimental backend is reachable from `backend="auto"` without `FLASHINFER_ALLOW_EXPERIMENTAL_AUTO_BACKENDS=1`. (Calling an `@flashinfer_experimental_api` or naming a backend explicitly is itself the opt-in and needs no environment variable.)
  - [ ] **Test scope declared below.** The experimental CI lane runs exactly these targets, so keep them as narrow as the change allows.

<!-- Required for experimental PRs. Replace the commented lines below with your targets.
     Do not delete the fence or change its `experimental-tests` tag — the experimental-track
     watcher reads it verbatim to decide which targets to ask CI for. -->

```experimental-tests
# One target per line: a directory or a file. (A pytest ::selector is
not
# supported -- the sharding runner cannot consume one.) Must be under
# tests/experimental/ and must exist. Delete these comment lines and add
yours, e.g.
#
#   tests/experimental/test_my_backend.py
#   tests/experimental/my_backend/
#
# Declaring the whole tree (tests/experimental/) is allowed but means
every
# experimental PR pays for every other feature's tests, in every matrix
cell.
```

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc. -->


<!-- This is an auto-generated comment: release notes by coderabbit.ai -->

## Summary by CodeRabbit

* **Compatibility**
  * cuTile-based FP8 RoPE quantization requires an NVIDIA GPU with compute capability SM89 or higher. Calls on older GPUs now report that this operation is unsupported.
* **Documentation**
  * Updated the backend requirements to specify the SM89 minimum.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [cc91c96](https://github.com/flashinfer-ai/flashinfer/commit/cc91c96f992697a247ac69ea87ebb4528f63994e)

- **作者**: nvamyt
- **时间**: 2026-10-07T16:12:56Z
- **提交信息**: fix(ci): isolate test_sharding child pytest runs from nightly PYTEST_ADDOPTSFix sharding plugin test pytest addopts (#5722)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->
Fix: simulate the nightly `PYTEST_ADDOPTS="--full"` for every
`tests/test_sharding` test via an autouse conftest fixture, so a child
pytest that inherits it fails in regular PR CI instead of only in
nightly. Tests that spawn isolated child pytest processes now drop the
variable explicitly (same approach as #5673): subprocess helpers pop it
from the child env, and tests whose runner spawns pytest in-process use
the new `isolated_pytest_addopts` fixture. The `--rootdir` override in
test_plan_run_and_completed_reuse_publish_resumable_artifacts` is passed
via `env_override` so it still reaches the child.

## 🔍 Related Issues
#5670
<!-- Link any related issues here -->
Job #[460176900](https://nv/flashinfer-ci/-/jobs/460176900)

Failed test files:
- tests/moe_ep/test_sm107_qualification.py (4 failed nodes) Fixed by PR
#5673
  - tests/test_sharding/test_pytest_plugin.py (3 failed nodes)
  - tests/test_sharding/test_runner_cli.py (27 failed nodes)
  - tests/test_sharding/test_shell_entrypoint.py (1 failed node)
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

* **Tests**
  * Test runs now use pytest’s full mode by default.
* The timeout check runs without inherited pytest options and continues
to verify that marked deadlines produce a failure with a timeout
message.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [e77db99](https://github.com/flashinfer-ai/flashinfer/commit/e77db996ca17d46d0a23fb7e7005cb191f61402f)

- **作者**: eigen
- **时间**: 2026-10-07T09:17:01Z
- **提交信息**: fix(cake_all_gather_matmul): re-allocate past torch's stale NVSHMEM rendezvous handle on workspace growth (SM100a, SM103a) (#6157)

## Summary

The Cake all-gather matmul backend grows its per-(device, group, dtype)
symmetric scratch collectively. torch's NVSHMEM symmetric-memory
allocator before
[pytorch#192579](https://github.com/pytorch/pytorch/pull/192579)
(2026-08-11) keeps the rendezvous handle of a freed allocation cached
under its address, so a new allocation that lands on a freed address is
handed the freed buffer's handle (its `buffer_size` and peer tables).
Every torch build based on an earlier commit (all 26.07 NGC containers,
torch `2.13.0a0+9186a08b2c`) has the defect; the backend hit it as

```
RuntimeError: SymmetricMemory::get_buffer: the requested size (67108864 bytes) exceeds the allocated size (33554432 bytes)
  cake_all_gather_matmul.py _grow_workspace -> handle.get_remote_tensor(...)
```

whenever a growth followed another symmetric-memory user's free (the
cuTile all-gather matmul's gathered-A buffer in the same process), on
the one-shot and the prepared path alike. torch's CUDA and NCCL
symmetric-memory backends drop the handle together with the allocation.

This PR makes every symmetric rendezvous of the backend (barrier flags,
scratch growth) validate the returned handle and re-allocate past a
stale one:

* `_rendezvous(call, group, allocations, clear=)`: `_prepare_session`
hands it the round's plan (the barrier flag pad when the group has none
yet, the scratch when the capacity grows); the guard allocates and
rendezvouses each entry, checks rank / world size and `buffer_size >=
numel * element_size`, zeroes the local pads of the fresh allocations,
synchronizes the stream and votes once per round with one small
`all_reduce(MAX)` of a bitmask over the group. The vote makes the
decision rank-uniform (every rank performs the same collective
allocation sequence) and replaces the post-allocation `dist.barrier` the
backend already issued, so a growth issues exactly one collective, as
before. Stale allocations are parked so the retry cannot land on the
same address and only they are re-allocated in the next round; after 8
rounds a `StaleSymmetricHandleError` (a `RuntimeError`) names the cause
and the mitigation (`prepare_all_gather_matmul(..., max_rows=final
capacity)`) and leaves the previous workspace usable.
* `_prepare_session`: any other failure inside the collective allocation
sequence poisons the launch state (a rank that failed part-way leaves
the group desynchronized); the rank-uniform stale exhaustion does not.
* One `RuntimeWarning` on the first detection per process;
`_RENDEZVOUS_STATS["stale_retries"]` counts re-allocations.
* A stale handle at least as large as the tensor is used as is (its peer
addresses derive from the reused address and its signal pad is a
separate live allocation in the affected torch versions).

No device program, host sequence or steady-state per-call path changes.
The files are byte copies of the Cake export templates.

## Tests

* `tests/comm/test_all_gather_matmul_cake.py` (CPU, fake symmetric
memory, 10 new tests): stale-then-fresh recovery with the parked
allocation released, a peer's stale vote re-allocating this rank too,
one vote per round that re-allocates only the stale entries, pads
cleared and stream synchronized before the single vote, bounded
exhaustion with the named error, topology mismatch before any vote,
flag-pad publication, the flag pad and the scratch in one rendezvous
round, `_prepare_session` poisoning rules.
* `tests/comm/test_all_gather_matmul_cake_e2e.py` (NVSHMEM, 2/4/8
SM100/SM103 GPUs): a foreign symmetric buffer freed right before a
growth (the failing pattern; detections printed) and a deterministic
undersized-handle injection on the real 1152 -> 2048-row growth through
the prepared path (recovery, parked allocation released, one-time
warning, correct output).

Results in the affected torch (`2.13.0a0+9186a08b2c`, NGC 26.07, NVSHMEM
backend):

| machine | CPU tests | e2e tests |
|---|---|---|
| 8x B200 (sm_100a) | 158 passed (148 existing + 10 new) | 2 passed |
| 8x B300 (sm_103a) | 158 passed | 2 passed |

Stand-alone reproduction on both machines (torch only, no backend code):
two NVSHMEM allocations freed and re-allocated at the same address
return the freed buffer's handle (`get_buffer` 67108864 > 33554432
bytes); the unpatched backend fails the 8192-row growth after a foreign
free (1073741824 > 805306368 bytes), the patched backend detects the
stale handle once, re-allocates and produces correct output.

## Performance

No kernel, host sequence or steady-state path changed, and a growth
issues the same number of collectives as before (the guard's vote is the
post-allocation barrier). One-time growth / prepare cost of
`prepare_all_gather_matmul` (8 ranks, wall ms per growth step, old =
main `a0bfe30a`, new = this PR, same node and warm JIT cache; growth
steps 128 -> 512 -> 1152 -> 2048 -> 4096 rows x 1280 of a 7168 -> 1280
layer):

| step | B200 old | B200 new | B300 old | B300 new |
|---|---:|---:|---:|---:|
| grow 512 rows | 0.71 | 0.77 | 0.96 | 0.85 |
| grow 1152 rows | 0.59 | 0.67 | 0.68 | 0.74 |
| grow 2048 rows | 0.55 | 0.62 | 0.57 | 0.60 |
| grow 4096 rows | 22.5 | 22.8 | 57.6 | 47.3 |
| prepare without growth (3 calls) | 0.09 / 0.08 / 0.07 | 0.10 / 0.08 /
0.08 | 0.11 / 0.09 / 0.13 | 0.09 / 0.06 / 0.05 |
| grow 8192 rows after a foreign symmetric free | fails (stale handle) |
153.9 (1 re-allocation) | fails (stale handle) | 28.8 (1 re-allocation)
|
| grow 16384 rows with an injected stale handle | - | 59.2 (1
re-allocation) | - | 76.4 (1 re-allocation) |

The 4096-row step varies by tens of ms between identical runs
(collective allocation, peer mapping and rendezvous of the 0.5 GiB
symmetric scratch; the backend zeroes only its signal pad), not by arm.

Old/new over the whole export denominator (ws2 12 rows, ws4 24 rows, ws8
24 rows; both weight layouts, Llama TP8/TP4 qkv + gate_up rows, tails)
on 8x B300 and 8x B200: deployed prepared launcher, cold-L2 CUPTI
rank-max medians, 3 counterbalanced groups per pass, separate processes
per pass in old/new/new/old order, with the unchanged source launcher in
the same processes as the A/A control. Delivered guard on the current
base (old = main `a0bfe30a`, new = this PR; four passes old/new/new/old
per machine, same protocol, per world size median over the two old
passes / median over the two new passes of the per-row medians; the A/A
column is the unchanged source launcher in the same processes):

| machine | ws | rows | old/new: min / median / max | rows < 0.98 (2+2)
| A/A: min / median / max |
|---|---:|---:|---|---:|---|
| 8x B200 | 2 | 12 | 0.926 / 1.004 / 1.064 | 2 | 0.973 / 0.992 / 1.004 |
| 8x B200 | 4 | 24 | 0.971 / 0.995 / 1.031 | 1 | 0.909 / 0.988 / 1.009 |
| 8x B200 | 8 | 24 | 0.921 / 1.006 / 1.123 | 3 | 0.950 / 0.998 / 1.075 |
| 8x B300 | 2 | 12 | 0.970 / 0.998 / 1.032 | 2 | 0.979 / 0.995 / 1.001 |
| 8x B300 | 4 | 24 | 0.969 / 1.002 / 1.036 | 1 | 0.964 / 0.997 / 1.033 |
| 8x B300 | 8 | 24 | 0.961 / 0.997 / 1.064 | 3 | 0.954 / 0.999 / 1.048 |

The twelve rows below 0.98 at the 2+2 median were re-measured with a
focused protocol (2 x (old, new, new, old) separate processes on those
rows only, 9 groups per arm per process): all twelve read >= 0.98 (8x
B200 0.984-1.017, 8x B300 0.980-1.016); the two rows at the threshold
under focus (B200 ws4 M=512 N=2560 K-major bf16 at 0.984, B300 ws8
M=1025 N=7168 K-major bf16 at 0.9799) read 1.001 and 1.002 in 12-process
re-checks (3 x (old, new, new, old); the B200 one on a second node). The
unchanged source launcher measured in the same processes reads 0.99-1.02
throughout. No row shows a same-sign loss: the guard reads as the
unguarded backend on both architectures.

The same guard was also measured before the rebase against the previous
main (`50a180ed0`, four passes per machine): 8x B300 60/60 rows >= 0.98
(min 0.983); 8x B200 56/60, the four rows below re-measured under the
focused protocol at 0.991-1.037.

An earlier revision of this PR voted after every symmetric allocation
(one extra all-reduce per allocation on top of the barrier). Over the
same denominator it read 0.98-1.04 on every row except one on 8x B300
(ws4, M=8192, N=2048, N-major bf16, a row whose eager-path timing is
bimodal), which read 0.94 at the median in every process of that
revision while its fastest samples were unchanged. A bisect on that row
(identical-code control 1.017; the revision minus its vote 1.041; main
plus one early all-reduce 0.970; one vote per round plus the old barrier
0.973; this revision 1.023) showed that the presence of one extra
prepare-time collective, not its position, shifts that row's
steady-state distribution; folding the vote into the barrier removes it.

## Notes

* Rebased on #6153 (`a0bfe30a`, the persistent arrival-ordered schedule
/ SM push / PDL round), which landed in this file while the PR was open;
the guard wraps that backend's growth path unchanged (`_publish_scratch`
resets the SM-push tables the way `_grow_workspace` did).
* Same file as #6104 (CUDA symmetric-memory backend + capture);
whichever lands second rebases (the guard is backend-agnostic).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [aa65104](https://github.com/flashinfer-ai/flashinfer/commit/aa651045756128d2fb6b26fa4bbc21a49a576572)

- **作者**: eigen
- **时间**: 2026-10-07T08:19:36Z
- **提交信息**: test(cake_backend): cross-backend DeepSeek-V3 routing coverage on real-logit, tie and large-T inputs (#6171)

## Summary

Tests only, no kernel or Python changes. Adds
`test_cake_backend_matches_default` to
`tests/model_optimizations/test_dsv3_fused_routing.py`:
`fused_topk_deepseek(backend="cake")` against `backend="default"` on

- four input profiles: i.i.d. normal, correlated real-logit-like logits
(RMS-normalised hidden states x gate weight + per-expert offsets, O(1)
fp32 correction bias), tie-heavy coarse value grids, and very negative
logits where the `+1e-20` term matters;
- `num_tokens` in {1, 64, 4096, 65536} (large-T rows on one dtype pair
per score dtype);
- nine score/bias dtype pairs and four routing configs (E=256 g8/kg4 k8,
E=128 g4/kg2 k4, E=96 g3/kg2 k5, single-group E=128 k=1), PDL on/off,
exact and oversized `routing_replay_out`.

Assertions: expert ids, their order and `routing_replay_out` must be
identical (both backends evaluate the same sigmoid, add the same bias
and select on identical FP32 values); weights must agree within one ulp
of the output dtype (|dw| <= 1e-6 for float32), because the two backends
normalise in different precision (FP32 reciprocal vs FP64 division).

## Motivation

A DeepSeek-V3-0324 FP8 TP4 e2e run (sglang, `--moe-runner-backend
triton`) found expert ids identical to the default router on ~1M routed
rows per rank with weights within 1 FP32 ulp, while the existing
cross-backend check only covered i.i.d. normal rows at T <= 64. This
test pins that behaviour on the input regimes that matter (correlated
logits, ties, large T, near-zero sigmoid sums).

No single-group config with `num_experts > 128` is included: the default
backend's 384/256-expert single-group instances read unwritten
`smemInterTop*` shared-memory slots when `topk < 8` (the only admissible
single-group top-k is 1), so their output is not a usable reference;
reported in #6172.

## Validation

SM100 (B200): the new test and the whole file pass against this base
with the current Cake kernels (details in the first comment).

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Tests**
* Added cross-backend checks for routing results across varied input
distributions, token counts, and data types.
* Tests verify expert selections, output replay, and weight accuracy on
supported GPUs.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [491d453](https://github.com/flashinfer-ai/flashinfer/commit/491d453377f92b1f1704a2d45c82fa32e4448a7b)

- **作者**: eigen
- **时间**: 2026-10-07T08:04:49Z
- **提交信息**: feat(cake_diffusion): MiniMax-H3 SM120 fused quantized full MLP, FC1 + SwiGLU + FC2 + gated residual (RTX 5090 / RTX PRO 6000) (#6169)

## Summary

SM120 (GB202: GeForce RTX 5090 and RTX PRO 6000 Blackwell) fused
MiniMax-H3 MLP block, candidate
5090-K5 of the MiniMax-H3 kernel tracker (#4254 / #4532): RMSNorm +
indexed AdaLN + FC1 (5376 -> 28672)
+ SwiGLU + FC2 (14336 -> 5376) + indexed output gate + residual, with
FP8 (W8A8, per-token / per-channel
E4M3) and NVFP4 (W4A4, block-16 E2M1 + UE4M3 scales) operands. Batch 1,
no sequence parallelism; the
production token counts are 33472 / 38592 / 48768 / 58944 / 74240 /
109952 plus the 128-row tails.

New public API (`flashinfer.diffusion_ops`):

- `minimax_h3_mlp_fp8_sm120(x, x_norm_weight, adaln_scale, adaln_shift,
adaln_index, gate, residual, fc1_weight_q, fc1_weight_scale,
fc2_weight_q, fc2_weight_scale, *, out=None, workspace_*=None, eps=1e-5,
fp8_mma_form=-1)`
- `minimax_h3_mlp_nvfp4_sm120(x, ..., gate, residual, a_global_scale,
fc1_weight_q, fc1_scale_tiles, fc1_alpha, y_global_scale, fc2_weight_q,
fc2_weight_sf, fc2_alpha, *, out=None, workspace_*=None, eps=1e-5)`
- `prepare_minimax_h3_fc2_weight_fp8(fc2_weight)` and
`prepare_minimax_h3_fc2_weight_nvfp4_sm120(fc2_weight, w_global_scale)`
(the FC1 weights reuse the existing SM120 FC1 preparation of #4532
candidate K4).

The tables (`adaln_scale`, `adaln_shift`, `gate`) are `[rows, 5376]`
BF16 views with a unit column stride
and 16-byte-aligned base / row pitch, so column chunks of a wider
modulation projection work without a
copy; `adaln_index` is int64 and rows whose index is out of range get a
zero activation and a zero gate
(the output row equals the residual). `out` may alias `residual` or `x`.
All intermediates are caller-
visible optional workspaces (quantized activation, `y`, quantized `y`,
the FC2 tile flags).

## Implementation

Three kernels per call on the current stream, all `mma.sync` +
`ldmatrix` register pipelines (SM120
has no tcgen05 / TMEM): a one-CTA-per-row norm / AdaLN / quantization
kernel, the persistent FC1 GEMM
with the SwiGLU epilogue (the K4 kernel; in the NVFP4 path a variant
whose epilogue emits `y` directly
as block-16 E2M1 codes plus dense UE4M3 scales, so `y` never touches HBM
in BF16), and a persistent FC2
GEMM (256x128 tiles, K = 14336, 4-stage TMA ring) whose producer warps
quantize `y` per token (FP8)
and whose epilogue applies the indexed gate and the residual. The FC2
M-tile flags order the producer
behind the FC1 tiles of the same rows.

On GeForce GB202 the dense FP8 `mma.sync` forms run at half rate when
the accumulator is FP32; the
operator issues the FP8 MMAs there as `kind::mxf8f6f4` with unit UE8M0
scales (every scale byte
`0x7F` = 2^0), which keeps full FP32 accumulation at the full rate and
produces bitwise-identical
results to the legacy form (checked on both boards; a test asserts it).
The RTX PRO 6000 issues every
form at full rate and keeps the legacy form (`fp8_mma_form=-1`
dispatches on the device name; `0` / `2`
force a form).

The CUDA source is generated by a typed kernel IR toolchain and
committed as
`csrc/cake_minimax_h3_sm120_quant_mlp_sm120a.cu` (seven namespaced
`sm_120a` kernels and a TVM-FFI
host that validates arguments, builds the TMA descriptors and dispatches
the FP8 form); it builds with
the SM120 JIT flags only (`requires CUDA >= 12.9`).

## Correctness

`tests/diffusion_ops/test_minimax_h3_sm120_quant_mlp.py` (22 tests, run
on an RTX 5090 and an RTX
PRO 6000 Blackwell, CUDA 13.3 / torch 2.13 nightly container):
stage-wise definitional checks against
an exact torch emulation -- the quantized activation against the
per-token FP8 recipe (derived bound,
zero violations) or the `nvfp4_quantize` recipe (tie-excluded mismatch
budgets); the kernel's BF16 `y`
against the FP32 reference on its own quantized activation (the K4 rule:
`atol 1e-2 / rtol 1.6e-2`,
`max(4, 2e-7 numel)` violations); the FP8 `y` scale exactly
`RN(max(amax, 1e-12) / 448)` of the
kernel's own `y` and the codes its nearest E4M3; the NVFP4 `y` block
scales within one UE4M3 code and
values within half an E2M1 step of the reference; the output against
`BF16(residual + BF16(gate *
BF16(FC2(y_q))))` with the round points of the intermediates in the
bound. Rows 1 / 127 / 128 / 129 /
255 / 257 / 4097 for both variants, plus out-of-range index rows, `out`
aliasing `residual`, strided
tables, caller workspaces, argument validation and the FP8 form
identity. The tests skip without a
compute-capability-12 device.

## Performance

CUPTI cold-L2 medians of the complete operator against the fastest
same-session segmented chain of
the same operand variant (the SM120 FC1 operator -> production `y`
quantization -> fastest library FC2
GEMM among `torch._scaled_mm` tensorwise / rowwise, `bmm_fp8`, CUTLASS
groupwise, `mm_fp4` auto /
CUTLASS / cuDNN -> fused gated-residual tail), ten timed row counts per
board (six production centers,
two aligned and two unaligned tails around 38592):

| board | FP8: operator vs fastest chain | NVFP4: operator vs fastest
chain | vs bare FC1 + bare FC2 library GEMMs |
|---|---|---|---|
| RTX 5090 | 1.24-1.32x faster (24.7-90.1 ms, 564-628 TF) | 1.09-1.12x
faster (12.7-44.5 ms, 1142-1222 TF) | FP8 0.86-0.89x of the GEMM-only
time; NVFP4 1.02-1.05x |
| RTX PRO 6000 Blackwell | 1.06-1.07x faster (21.3-71.9 ms, 706-727 TF)
| 1.14-1.16x faster (11.3-37.5 ms, 1357-1374 TF) | FP8 0.81-0.83x; NVFP4
0.99-1.03x |

Peak operator memory at the production centers: 3.5-10.3 GiB (FP8),
2.8-6.7 GiB (NVFP4), against
8-9 GiB (FP8) and 6-7 GiB (NVFP4) for the chains at 33472-38592 rows.

`benchmarks/bench_minimax_h3_sm120_quant_mlp.py` is a CUDA-event
convenience comparison against a
plain torch / FlashInfer chain (per-token quantization in torch,
`_scaled_mm` / `mm_fp4`,
`silu_and_mul`): RTX 5090 FP8 25.7 ms vs 61.8 ms and NVFP4 12.8 ms vs
19.2 ms at 33472 rows; RTX PRO
6000 FP8 21.2 vs 60.6 ms and NVFP4 11.2 vs 17.7 ms.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added fused MiniMax-H3 MLP operations for SM120 GPUs, supporting FP8
and NVFP4 quantization.
* Added utilities to prepare FC2 weights for both quantization formats.
* Made the new operations and weight-preparation utilities available
through the diffusion operations API.
* **Documentation**
* Added the new operations and utilities to the diffusion API reference.
* **Benchmarks**
* Added a benchmark comparing fused operations with equivalent
PyTorch/FlashInfer chains. Configure row counts, warmup, iterations, and
FP8 instruction form, or export results as JSON.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [526180c](https://github.com/flashinfer-ai/flashinfer/commit/526180c42d82ab3739b418afd1cc4385ace68fdf)

- **作者**: Vedaanta Agarwalla
- **时间**: 2026-10-07T08:00:26Z
- **提交信息**: feat(cudnn): backend="auto" takes cuDNN for single-token d256 paged decode in the measured CTA band; CUDA-graph wrappers declare replay to cudnn-frontend 1.31+ (#6152)

<!-- .github/pull_request_template.md -->

## 📌 Description

Follow-up to #5508 (`auto` -> cuDNN for multi-token paged decode) in two
pieces, both on the decode wrapper's cuDNN path.

**1. CUDA-graph wrappers declare replay to cudnn-frontend.** A wrapper
built with `use_cuda_graph=True` now passes
`is_cuda_graph_replay_expected=True` when it builds its cuDNN graph
(cudnn-frontend 1.31+: NVIDIA/cudnn-frontend#1423, merged to develop as
39e350cd0; probed from the `pygraph` / `cudnn.graph` signatures by
`cudnn_frontend_accepts_cuda_graph_replay_hint()` in
`flashinfer/cudnn/utils.py`, so an older frontend is simply not handed
the keyword). The frontend's d256 decode tile charges the split-KV
plan's second host launch against an eager caller and so leads with the
unsplit plan; a caller that replays a captured graph pays that launch
once, and with the hint the tile leads with the split (the GPU-time
optimum). The flag is part of the decode graph-cache key and of the
prepared graph's signature (a graph built for eager execution never
serves a captured wrapper or the other way round);
`prepare_cudnn_batch_decode` takes it, and the public
`cudnn_batch_decode_with_kv_cache` passes its existing
`is_cuda_graph_compatible` through. No numerics change: the split plan's
output matches the unsplit plan's (tests compare both against fa2).

**2. `auto` takes cuDNN for single-token d256 decode in the measured
band.** `_auto_decode_prefers_cudnn` resolves to `cudnn` for
single-token decode of fp16/bf16 head_dim-256 GQA models (groups 4, 8,
16: the rows the d256 decode tile packs into one CTA) with `batch_size *
num_kv_heads` in [96, 256] CTAs, and from 64 CTAs when the wrapper
declares replay (the tile then splits KV below one wave instead of
idling most SMs). Everything else at d256 stays on fa2: 32 CTAs (mixed
even with the split), 512+ CTAs (mixed), multi-token rows (cuDNN's
prefill tile; the 32-row decode tile is not routed), groups 1 / 2 / 32
and non-dividing groups, windows. The d128 rule is unchanged.

Measured on B200 (148 SMs; this host's clocks are capped at 1155 MHz, so
absolute times run high; cudnn-frontend develop at 1.31 with #1423,
default placement, cuDNN 9.26.0.51; bf16, HND, page 16,
`BatchDecodeWithPagedKVCacheWrapper`, `bench_gpu_time` under CUDA-graph
replay, median of 20; cuDNN vs fa2 with tensor cores; `eager` = a
wrapper without `use_cuda_graph` (unsplit tile), `graph` = a
`use_cuda_graph=True` wrapper with a caller-owned table (hinted lead);
the GPU was shared with another job, so cells above ~400 us carry 20-50
% noise):

| heads | CTAs (b x KV heads) | KV | fa2 | cuDNN eager (split) | cuDNN
graph (split) |
|---|---|---|---|---|---|
| 32/4 | 64 (b=16) | 1000 / 4096 / 16384 | 29.9 / 68.0 / 408.8 us | 27.1
(1) / 84.3 (1) / 279.2 (2) | 27.3 (1) / 58.5 (2) / 327.4 (2) |
| 32/4 | 96 (b=24) | 1000 / 4096 / 16384 | 36.9 / 88.0 / 468.6 | 27.7
(1) / 85.4 (1) / 425.2 (1) | 27.5 / 85.2 / 505.2 |
| 32/4 | 128 (b=32) | 1000 / 4096 / 16384 | 46.5 / 165.4 / 691.9 | 30.3
/ 140.3 / 498.0 | 30.5 / 145.3 / 502.5 |
| 32/4 | 148 (b=37) | 1000 / 4096 / 16384 | 47.0 / 133.5 / 627.7 | 33.9
/ 103.6 / 625.7 | 32.9 / 103.9 / 543.3 |
| 32/4 | 256 (b=64) | 1000 / 4096 / 16384 | 63.0 / 414.7 / 1665.8 | 58.8
/ 247.9 / 1290.7 | 58.8 / 271.0 / 1173.8 |
| 64/8 | 64 (b=8) | 1000 / 4096 / 16384 | 29.5 / 74.8 / 333.6 | 26.6 (1)
/ 84.7 (1) / 302.4 (2) | 26.6 (1) / 58.1 (2) / 273.3 (2) |
| 64/8 | 128 (b=16) | 1000 / 4096 / 16384 | 45.3 / 154.3 / 662.6 | 30.3
/ 122.5 / 573.7 | 30.3 / 91.5 / 376.4 |
| 64/8 | 256 (b=32) | 1000 / 4096 / 16384 | 70.1 / 324.4 / 1443.8 | 59.2
/ 198.3 / 1391.9 | 59.2 / 250.2 / 1490.1 |
| 16/4 | 64 (b=16) | 1000 / 4096 / 16384 | 29.3 / 68.2 / 329.8 | 27.5
(1) / 84.9 (1) / 277.7 (2) | 27.5 (1) / 59.2 (2) / 258.0 (2) |
| 16/4 | 128 (b=32) | 1000 / 4096 / 16384 | 45.3 / 165.3 / 651.2 | 30.6
/ 98.7 / 465.1 | 30.8 / 93.2 / 598.5 |
| 16/4 | 256 (b=64) | 1000 / 4096 / 16384 | 83.8 / 387.0 / 1356.6 | 59.4
/ 260.7 / 1308.3 | 59.2 / 189.8 / 1373.7 |
| 8/1 | 128 (b=128) | 1000 / 4096 / 16384 | 45.5 / 178.9 / 532.3 | 30.9
/ 110.1 / 513.4 | 33.8 / 95.3 / 574.9 |
| 64/4 | 128 (b=32) | 1000 / 4096 / 16384 | 48.1 / 187.3 / 788.4 | 30.5
/ 94.0 / 535.9 | 30.4 / 150.2 / 637.1 |
| 32/2 | 128 (b=64) | 1000 / 4096 / 16384 | 48.2 / 179.8 / 539.2 | 31.2
/ 124.3 / 543.3 | 31.2 / 96.0 / 586.9 |

Outside the band, for the record: 32 CTAs (32/4 at b=8) 1000 / 4096 /
16384: fa2 24.2 / 44.9 / 138.7 vs eager 26.6 / 82.0 / 150.4 (1 / 1 / 4)
vs graph 22.3 / 37.9 / 117.4 (4 / 4 / 4), and 32/2 at b=16 16384 loses
1.2x even split; 512 CTAs (32/4 at b=128): 121.2 / 836.5 / 3353.7 vs
161.3 / 533.6 / 3481.9. fa2 without tensor cores
(`use_tensor_cores=False`) is 1.5-9x slower than its tensor-core kernel
at these shapes (32/4 b=32 4096: 600 vs 116 us), so the rule holds for
both wrapper modes.

**After #6150 (merged):** this branch now carries main, so the d256 band
inherits the shared predicate's gates from #6150's second round: the
performance route requires cudnn-frontend's own FROST runtime check
(`cudnn_frontend_frost_runtime_available()`, CuTe DSL present and at the
frontend's 4.7.0 floor) and fa2's explicit split controls
(`fixed_split_size` / `disable_split_kv`) keep fa2; the new GPU tests
use the same `_auto_cudnn_available()` skip helper. The replay flag sits
in the decode graph-cache key ahead of `stats_use_log2`, which the
prepared graph reads as the key's last entry (the native-log2 LSE
plumbing that also landed on main).

## 🔍 Related Issues

- Follows #5508 (the `auto` -> cuDNN rule) and #6150 (caller-owned table
gate).
- NVIDIA/cudnn-frontend#1423 (merged 2026-10-07, develop 39e350cd0,
ships in 1.31) adds the `is_cuda_graph_replay_expected` hint this PR
passes; on 1.30 and older the probe says no and the keyword is never
sent.

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

- `tests/utils/test_cudnn_decode_auto_rule.py`: the signature probe
(keyword present / absent, helper with and without `**kwargs`, no
`pygraph`, package missing) and the d256 band in the rule tables (128 /
96 / 256 CTAs, group 16, MQA 8/1, 64 CTAs only with `replay_hint`; 32
and 512 CTAs with and without it, groups 1 / 2 / 12 / 32, two rows,
window, page 24, fp8 KV, Hopper, older frontend; `replay_hint` leaves
the d128 verdicts alone).
- `tests/attention/test_cudnn_decode.py`:
`test_cudnn_wrapper_cuda_graph_passes_the_replay_hint` (the captured
wrapper's graph carries the hint, its prepared key differs from the
eager wrapper's, outputs match, the captured graph replays; on a 148-SM
part the hinted lead splits 2 where the eager lead does not; the
probe-says-no case builds without the keyword),
`test_auto_backend_resolves_cudnn_for_single_token_d256` (32/4 b=32,
64/8 b=12, 16/4 b=64 resolve `cudnn` and match fa2 on output and LSE),
`test_auto_backend_d256_band_starts_lower_under_cuda_graph_replay` (32/4
at b=16: eager stays fa2, the CUDA-graph wrapper with a caller table
resolves `cudnn` on a 1.31 frontend and matches fa2 through capture and
replay; keeps fa2 on an older frontend).

Run on B200 (branch merged with main at #6150):

| stack | result |
|---|---|
| cudnn-frontend develop 1.31 (#1420, #1423) + cuDNN 9.26, default
placement | 431 passed, 3 skipped (the two short-table cases skip on a
1.31 frontend; one two-device test) |
| cudnn-frontend 1.30.0 wheel + cuDNN 9.26 | 430 passed, 4 skipped (the
hinted case of the wrapper hint test needs 1.31; two-device; two
frontend-feature skips from main's own tests) |
| 1.30.0 wheel with a `nvidia-cutlass-dsl` 4.6.2 dist-info ahead of the
4.7.0 DSL (`test_cudnn_decode.py` + the rule file) | 268 passed, 17
skipped: every no-flag auto positive, the d256 band tests included,
skips because the probe says FROST cannot run; nothing resolves to cudnn
|
| pip: cudnn-frontend 1.29 + cuDNN 9.26 | 414 passed, 20 skipped (the
auto positives that need 1.30+, two-device, main's frontend-feature
skips) |
| pip stack, `tests/attention/test_batch_decode_kernels.py` CUDA-graph /
tensor-core / fast-plan subset | 1170 passed |

`ruff format` / `ruff check` (0.12.8) and `mypy` 1.17.1 clean on the
changed files.

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

- The band's lower edge is where the unsplit tile's one-wave floor meets
fa2's rising cost: at 4096 keys the tile costs ~85 us for any CTA count
up to one wave while fa2 costs 45 / 68 / 88 / 133-165 us at 32 / 64 / 96
/ 128-148 CTAs. The replay hint moves that edge to 64 CTAs because the
frontend then splits KV (2 ways at 4096, 4 at 32 CTAs); 32 CTAs stay out
because the split-4 plan is still mixed at 16k.
- The upper edge (256 CTAs, ~1.7 waves) is conservative: 512 and 1024
CTAs win at 4096 keys but lose or tie at 1000 and 16384, so they stay on
fa2 until there is a reason to believe otherwise.
- `replay_hint` is computed in the wrapper's shared selector, so `plan`,
`workspace_size` and `fast_decode_plan` agree; under CUDA graphs `auto`
still requires a caller-owned `block_tables`, so the 64-CTA band is
reachable only there (and the resolution is frozen after the first plan
as before).
- The `is_cuda_graph_compatible` cache-key entry means a process that
builds both an eager and a captured wrapper for the same shape holds two
cuDNN graphs; that is intended (they lead with different plans).

AI-assisted (Claude Code); validated by the author on B200.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Automatic backend selection can now route eligible single-token,
256-dimension grouped-query decode workloads to cuDNN. CUDA graph replay
expands eligibility for certain workload sizes when supported.
* cuDNN decode supports replay-aware graph preparation, with fallback
behavior for frontends that do not support replay hints.
* **Documentation**
* Updated cuDNN backend-selection guidance, including workload
thresholds and fallback behavior.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-10-08
**监控日期**: 2026-10-07
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4565
- **最后更新**: 2026-10-08T01:47:48Z

## 提交统计

- **昨日提交总数**: 71
- **提交者数量**: 35
- **主要提交者**: pkisfaludi-nv, William Lin, Zhang Peiyuan

## AI分析总结

# FastVideo 昨日（71 次提交）总结

## 一、主要更新类型

**新模型/新功能（约 20 条，增量最大）**：LTX-2.5、Wan2.2-Animate、Cosmos Predict 2.5、MMAudio V2A 音视频联动、LingBot-World、MiniMax H3 系列（Ref2VA、LoRA、FP8 文本编码器）、HunyuanVideo 1.5 训练、Wan2.2-S2V 语音生成视频、Helios 蒸馏 T2V、Dreamverse 多模态输入、Infinite Livestream、VQeval 长视频质量指标，另有 LoRA 抽取、外部启动器多机推理、训练 pipeline runner 分离重构。

**性能优化（约 10 条）**：注意力内核、MoE/VSA 布局、VSA 稀疏与粗粒度组合避免全序列物化、FP8 动态激活融入 Triton、因果推理移除每步 host 同步、ROCm 稀疏注意力路由至 Triton，并针对 GB200、SM100（DGX Spark/RTX 5090）做位级无损加速。

**Bug 修复（约 20 条）**：流式生成、分布式调度、OpenAI 兼容 API（批量图片返回、参数校验返回 400、JPEG/WebP 输出路径）、Parquet 分片写入、Ray 多 GPU 设备失败、NVFP4/MXFP8 权重量化、Ulysses SP 与 LongCat BSA 并行崩溃、LoRA 与量化/分布式状态交互、ROCm 平台检测、激活检查点重计算、HunyuanVideo 1.5 i2v 参考图条件。

**CI 与工程治理（约 10 条）**：测试隔离、IPC 信号量残留覆盖测试通道、性能行为测试拆分、性能回归测试与仪表盘分组、merge-gate 可靠性、硬回归日志、profiler 区域补全、进程感知日志与分布式 fixture 端口隔离。

## 二、关键变更与项目方向

一天内新增或增强约 12 个模型系列，表明 FastVideo 正从 Wan 单一模型演进为多模型统一训练与推理平台，持续兑现全栈框架路线图。服务端明显投入生产级部署，非法参数由静默处理改为返回 400，下游调用方契约更严格。同时项目向 AMD 与嵌入式 GPU 扩展，通过 Ray、外部启动器及 GB200/SM100 支持，把多机能力从单卡延伸到异构集群。

## 三、对项目的影响

稳定性与可复现性显著提升，集群启动、数据写入与分布式低精度场景的隐性故障风险被系统性消除。性能提升严格保持位级一致，如 VSA 布局融合 15.7ms→8.6ms、Attn-QAT 前向 9.14→6.96ms，且全部通过开关默认关闭、逐个验证，体现成熟的渐进式性能工程方法。量化修复与 profiler 补全提升了用户在分布式低精度场景下正确性与性能数据的可信度。CI 治理强化为高速迭代提供了质量护栏。已知风险在于 profiler 区域退出会关闭 CUDA 采集、GPU kernel 级追踪仍有盲区，且大量新模型移植后需要持续的回归测试覆盖。

## 四、值得关注的技术点

Triton 自定义算子在与 eager 路径相同的 bf16 舍入点上保持 bit-identical，是训练与 QAT 场景下可信的无损加速范式。Wan 训练器支持按区域 torch.compile，FA4 与 modulation 封装为 opaque custom op，兼顾 FSDP 与检查点包装交互。LoRA 与 MXFP8 重量化、NVFP4 保留及 FSDP 副本同步的交互修复，表明框架开始处理此类复合训练工作流。VSA 粗细粒度组合的内存优化对长视频生成的显存瓶颈意义重大。环境变量覆盖助手、进程感知日志与端口隔离则体现了对 CI 可复现性的系统性治理。

## 五、发展意义

本批提交呈现"稳定地基、扩展生态、冲刺性能、夯实治理"四线并进的态势。短期内，用户将获得更稳定的低精度分布式训练与推理能力，以及更丰富可用的模型集合；长期看，这为构建标准化的视频生成训练、评测与服务生态奠定了基础，推动项目从研究原型走向可持续维护的工程化项目。

## 详细提交记录

### [2b16440](https://github.com/hao-ai-lab/FastVideo/commit/2b164405c3d15ed2d222d0582d6db09ffc5ee6b2)

- **作者**: William Lin
- **时间**: 2026-10-07T22:58:03Z
- **提交信息**: [bugfix] Accept log_queue in StreamingVideoGenerator.from_fastvideo_args (#1937)

VideoGenerator.from_config calls from_fastvideo_args with a log_queue keyword
argument. The StreamingVideoGenerator override did not accept it, so
StreamingVideoGenerator.from_pretrained raised TypeError. The override now
accepts log_queue and passes it to the executor through VideoGenerator.__init__.
A new test covers the call.

### [1033fa8](https://github.com/hao-ai-lab/FastVideo/commit/1033fa8e1c8902e31758906abc07587f00e1ce41)

- **作者**: William Lin
- **时间**: 2026-10-07T22:39:39Z
- **提交信息**: [tests] Use the env helpers in the HunyuanVideo batch test (#1935)

The HunyuanVideo batch test wrote MASTER_PORT, MASTER_ADDR and
FASTVIDEO_ATTENTION_BACKEND with monkeypatch.setenv, so the environment-variable
contract test failed. The fixture now uses envs.override_external and the
registry override. The values and the restore behavior do not change.

### [e1e2559](https://github.com/hao-ai-lab/FastVideo/commit/e1e2559359656cc15cbdd0248d941cd31cf24f5a)

- **作者**: Davide Locatelli
- **时间**: 2026-10-07T22:35:37Z
- **提交信息**: [perf] FastH3 OmniRef: lossless speed-ups behind default-off switches (#1930)

These speed-ups for the MiniMax-H3 pipelines keep the output bit-identical. Each
one has a switch that is off by default:

- FASTVIDEO_MINIMAX_H3_EXACT_KERNELS: Triton RoPE, AdaLN modulation, gated
  residual and SwiGLU kernels that round to bf16 at the same points as the
  eager ops.
- FASTVIDEO_H3_VSA_HEADS_FIRST_TILE: VSA-H3 tiles are written directly in the
  heads-first layout of the kernel.
- FASTVIDEO_H3_VAE_TILE_PARALLEL: VAE spatial tiles are split across the
  sequence-parallel ranks.
- FASTVIDEO_H3_REF2VA_MEMO_ENTRIES: repeat reference encodes are reused.

The example basic_fasth3_omniref_pdd.py --lossless-accel turns them all on.

On GB200 with 4 GPUs, MiniMax-H3 text to video with audio (124 frames,
1344x768) gives bit-identical frames and audio with the first three switches
on and off.

### [8d2e1cf](https://github.com/hao-ai-lab/FastVideo/commit/8d2e1cf328851e17122d3c5d28943cb5acb568ed)

- **作者**: Wenbo Ji　嵇文博
- **时间**: 2026-10-07T22:33:11Z
- **提交信息**: [bugfix] Skip streaming IPC queues for standard VideoGenerator (#1902)

MultiprocExecutor created two streaming multiprocessing queues for every
generator, but only StreamingVideoGenerator uses them. Each queue uses POSIX
named semaphores in /dev/shm. When a job epilog deleted these files, spawned
workers failed to start. The executor now creates the queues only when
FastVideoArgs.enable_streaming_ipc_queues is set. StreamingVideoGenerator sets
it on a copy of its arguments in queue mode. Standard generation creates no
streaming semaphores.

### [4ebf11f](https://github.com/hao-ai-lab/FastVideo/commit/4ebf11f7d9887db33a5f50490d1cfecdb2d928a6)

- **作者**: Wenbo Ji　嵇文博
- **时间**: 2026-10-07T22:32:22Z
- **提交信息**: [bugfix] Fix test env defaults and server dependencies (#1901)

The distributed_setup test fixture now sets MASTER_ADDR and MASTER_PORT when
they are not set, with a new port for each test, and restores them after the
test. pyproject.toml now declares orjson and python-multipart, which the
OpenAI-compatible server needs. Two documents about the SSIM reference
bootstrap are corrected.

### [ef63de1](https://github.com/hao-ai-lab/FastVideo/commit/ef63de1f6029ed76799e995c73b7a09936ff69f2)

- **作者**: Wenbo Ji　嵇文博
- **时间**: 2026-10-07T22:31:58Z
- **提交信息**: [perf] Fuse VSA64 tile layout for SM100 inference (#1900)

For Wan VSA inference with 64-token tiles, each attention layer scattered Q, K,
V and the gate into a tile buffer and then made four transposed copies. On
SM100, one Triton kernel (tile_to_bhsd) now does the scatter and the transposes
in one pass. Training, 256-token tiles, other GPUs and builds without the kernel
use the previous path. FASTVIDEO_DISABLE_VSA64_FUSED_LAYOUT=1 turns the fused
path off.

On GB200 the layout and attention step goes from 15.7 ms to 8.6 ms. FastWan 1.3B
frames are bit-exact with the previous path at sequence parallel 1 and 2.

### [e5f31c1](https://github.com/hao-ai-lab/FastVideo/commit/e5f31c1b4c6633dacb6ea2df000687a09deed770)

- **作者**: Michael Yang
- **时间**: 2026-10-07T22:15:12Z
- **提交信息**: [bugfix] Fix HunyuanVideo forward pass with batch size greater than one (#1921)

The HunyuanVideo and HunyuanVideo 1.5 transformers failed on the first forward
pass when the batch had more than one sample. The modulation inputs had the
shape [B, C], but the fused ops expect [B, 1, C], so they could not broadcast
over the sequence. The models now add the sequence axis, as the refiner and the
final layer already do. Results for batch size 1 do not change.

### [b7bd777](https://github.com/hao-ai-lab/FastVideo/commit/b7bd7775ede5be8aa03f139d701dd922d489623b)

- **作者**: Wenbo Ji　嵇文博
- **时间**: 2026-10-07T22:14:38Z
- **提交信息**: [perf] Default SM100 long-sequence Attn-QAT tiling (#1899)

On SM100, the Attn-QAT training kernel now uses a faster route for non-causal
BF16 attention with equal query and key lengths of 16384 tokens or more. The
forward pass processes full KV tiles without bounds masks, and a separate masked
step handles the partial tail tile. The backward pass uses 64x128 dQ and dK/dV
tiles. Outputs, softmax statistics and all gradients are bitwise identical to the
previous route. FASTVIDEO_ATTN_QAT_SM100_OPTIMIZED=0 turns off the SM100 route,
and FASTVIDEO_ATTN_QAT_SM100_WIDE_BWD=0 keeps the 64x64 backward tiles.

On GB200 with 6 heads and 31200 tokens, the forward kernel time goes from 9.14 ms
to 6.96 ms and the backward kernel time from 17.41 ms to 15.85 ms.

### [dc72a35](https://github.com/hao-ai-lab/FastVideo/commit/dc72a35f4e5615b26f8e7e08ce5fcd8d3ddf557b)

- **作者**: Boyang ZHONG
- **时间**: 2026-10-07T22:06:02Z
- **提交信息**: [bugfix] Return individual images for batched image API requests (#1917)

For n > 1, the image endpoints returned one preview grid instead of n images.
The endpoints now run one model batch, save each decoded sample as its own file,
and return one URL or base64 item for each image. This applies to generations
and edits.

A keyword-only return_samples field (default False) is added to OutputConfig,
SamplingParam and ForwardBatch. Batched image requests set it and do not build
preview frames. The worker keeps the sample tensor for these requests, and
non-output ranks clear the field. Defaults and positional arguments do not
change.

### [7d61590](https://github.com/hao-ai-lab/FastVideo/commit/7d61590213dd724ccf9702b500dd5f1bfdc17dda)

- **作者**: William Lin
- **时间**: 2026-10-07T22:00:23Z
- **提交信息**: [bugfix] Fix the CUDA device of Ray workers on multi-GPU nodes (#1932)

Ray sets CUDA_VISIBLE_DEVICES of each GPU actor to the GPU of that actor. The
import of fastvideo initializes CUDA, so the executor cannot change the device
list later. On a node with more than one GPU, each worker after the first worker
failed with "invalid device ordinal".

On NVIDIA GPUs, each worker actor now keeps the device list of its raylet
(RAY_EXPERIMENTAL_NOSET_CUDA_VISIBLE_DEVICES=1). Each worker uses the position of
its GPU in that list as its local rank. The safetensors loader now reads each
file on node-group rank 0, which is the rank that sends the broadcast.

### [3c713d8](https://github.com/hao-ai-lab/FastVideo/commit/3c713d808a20008e3a9d9ce496c08a68c66a4b5e)

- **作者**: Chanu Ollala
- **时间**: 2026-10-07T21:56:53Z
- **提交信息**: [bugfix] Prevent ParquetDatasetWriter from overwriting shards across flushes (#1922)

ParquetDatasetWriter.flush() named each shard from the chunk index plus the number
of files in the worker directory. When two flushes split the chunks in different
ways, a new shard could get the name of an existing shard and replace it. The
data in the old shard was lost without an error.

New shards now get numbers after the highest existing shard number in all worker
directories. One helper writes each shard to a temporary file and renames it. It
raises FileExistsError instead of an overwrite. flush(write_remainder=True) now
also counts the remainder rows in its return value.

### [6ef5b78](https://github.com/hao-ai-lab/FastVideo/commit/6ef5b78020133257eba1c095056fd4afef93ac4f)

- **作者**: alanhuangyoo
- **时间**: 2026-10-07T21:54:34Z
- **提交信息**: [bugfix] LTX-2: train temporal RoPE at the clip's fps (#1892)

The legacy LTX-2 trainer did not give the clip fps to the DiT. The DiT then
kept temporal RoPE positions in frames during training, but inference uses
seconds (fps 24). The trainer now passes the fps of the stored latents (24 when
the value is missing).

The video transform stage resampled frames to train_fps but kept the source fps
in the batch. The saved clips then had the source fps, and the audio was cut to
the wrong length. The stage now sets the batch fps to train_fps.

The new regression test runs in the CI unit lane.

### [6275ac2](https://github.com/hao-ai-lab/FastVideo/commit/6275ac2c8e9b7af06a706359f5e3b6b64f401a8a)

- **作者**: Boyang ZHONG
- **时间**: 2026-10-07T21:52:15Z
- **提交信息**: [bugfix] Validate image parameters before generation and uploads (#1916)

The image endpoints now validate size, output format and count before they
create output directories, save uploads or start generation. An invalid value
returns HTTP 400. Omitted or null values keep their defaults.

Behavior change: an explicit empty size or output format, and a count outside
1-10, now return HTTP 400. Before, the server replaced them with defaults or
clamped the count.

### [73e878a](https://github.com/hao-ai-lab/FastVideo/commit/73e878a01c756f50b911b36f7d999a417efa2df0)

- **作者**: William Lin
- **时间**: 2026-10-07T21:35:05Z
- **提交信息**: [bugfix]: fix the MLX server and a GPU-only test leak after the 2026-10-07 merges (#1931)

- create_app reads distributed_executor_backend with getattr(..., None): the MLX
  server passes a SimpleNamespace without it, so since #1746 the server could not
  start (28 test_openai_video_client failures). An explicit external_launcher
  request is still rejected.
- test_cpu_sdpa patches fastvideo.platforms._current_platform instead of
  current_platform. monkeypatch restored the real platform as a module attribute
  that shadowed the lazy __getattr__, so later tests that fake _current_platform
  (gpu_worker dist timeout, ROCm detection, selector role override) failed on
  GPU hosts.

GB200 unit lane, A/B on one tray: main 36 failures, this change 0 (2720 passed).

### [3907a69](https://github.com/hao-ai-lab/FastVideo/commit/3907a69727af6aab846bb68014e9da2a62c77b1a)

- **作者**: Boyang ZHONG
- **时间**: 2026-10-07T21:23:15Z
- **提交信息**: [bugfix] Preserve image output formats (#1915)

The OpenAI image endpoint defaults to a .jpg output path, but the shared
output-path helper treated every non-PNG image path as a directory, so JPEG and
WebP requests were written somewhere other than where the endpoint read them.
Recognized PNG/JPEG/WebP extensions are now preserved, and existing directories
are checked first so a directory named e.g. renders.jpg still receives its
output inside it. Collision handling and filename sanitization are unchanged.

### [d1416b5](https://github.com/hao-ai-lab/FastVideo/commit/d1416b59301d830f12c48f08b08f825f206b6328)

- **作者**: William Lin
- **时间**: 2026-10-07T13:13:43Z
- **提交信息**: [misc]: re-run pre-commit after the 2026-10-07 merges (#1929)

Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [c520878](https://github.com/hao-ai-lab/FastVideo/commit/c520878fd27ae79381674134071d421fea7875cf)

- **作者**: Zhang Peiyuan
- **时间**: 2026-10-07T12:24:24Z
- **提交信息**: [perf]: QAT/QAD add safe regional compile for modular training (#1718)

Adds opt-in regional torch.compile to the YAML-driven modular Wan trainer (training.model.enable_torch_compile / torch_compile_kwargs) with FA4 and Wan modulation forward/backward as opaque custom ops, compiled repeated DiT blocks after FSDP setup, and activation checkpointing applied before FSDP for trainable Wan transformers.

Merged with main's #1716 (WanModel resolves the checkpointing type in __init__; the PR's pre-FSDP wrap uses it and the post-load wrap is gone) and #1757 (pre_fsdp_model_transform runs before this PR's pre_fsdp_transform). Maintainer review (Swarm order #776): AdaLN skip names are canonicalized through checkpoint-wrapper prefixes, test_inference_regional_compile.py joins the unit lane, the Wan modulation custom-op test moved to the transformer lane, regional_compile is classified in the schema inventory, and a 1/2-GPU training smoke covers fully_shard(CheckpointWrapper) in eager and regional-compile modes. Validated on GB200: the FA4 CuTe forward/backward parity and fullgraph-backward tests and all four smoke cases pass.

Also exempts MMAudio recipes, whose student builds its pipeline config at init, from the fine-tuning recipe construction check that #1648 left failing on main.

Co-Authored-By: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [99f8f3e](https://github.com/hao-ai-lab/FastVideo/commit/99f8f3e7a7ca0e0cb4c0ceb6a192f1ca4e619866)

- **作者**: Shao Duan
- **时间**: 2026-10-07T11:48:35Z
- **提交信息**: [feat] Add streaming and GPU-accelerated LoRA extraction (#1784)

Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [14e4b71](https://github.com/hao-ai-lab/FastVideo/commit/14e4b7189bad57427e6c563a69879bc1f3c30846)

- **作者**: Raghav K
- **时间**: 2026-10-07T11:46:54Z
- **提交信息**: [feat] Add Cosmos Predict2.5 DFD continuation to DreamVerse (#1768)

Adds a DreamVerse generation backend for Cosmos Predict 2.5 DFD video-to-world continuation (cosmos25_dfd_generation.py), its config wiring and worker hook, README notes, and tests.

This PR stacked on #1767, which landed first with the review fixes for the Cosmos 2.5 pipelines; what lands here is the DreamVerse integration only. The fixes requested in this PR's maintainer review (Swarm order #748: shared fps, FloatingPointError on non-finite rollouts, DFD detector anchoring, 24 fps defaults, FP64 distilled rollout) all reached main through #1767.

Co-Authored-By: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [8530fdc](https://github.com/hao-ai-lab/FastVideo/commit/8530fdc55007ca30e76e816aa850507718d14015)

- **作者**: William Lin
- **时间**: 2026-10-07T11:46:26Z
- **提交信息**: [feat] Add external-launcher executor for multi-node inference (#1746)

Co-authored-by: Will Lin <willlin@nvidia.com>
Co-authored-by: William Lin <8941107+SolitaryThinker@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [315b25d](https://github.com/hao-ai-lab/FastVideo/commit/315b25d26deba32de43ebc42c78c37af9e9471df)

- **作者**: Raghav K
- **时间**: 2026-10-07T11:42:44Z
- **提交信息**: [new-model] Add Cosmos Predict2.5 distilled T2W and DFD V2W inference (#1767)

Adds the Cosmos Predict 2.5 distilled text-to-world sampler (sCM, per-frame timesteps) and the DFD video-to-world pipeline, with their schedulers, registry entries, presets and examples.

Maintainer review fixes (Swarm orders #718 and #748): the DiT receives one shared fps value (its RoPE table is batch-independent, so per-sample vectors crashed batch > 1; differing values now raise), non-finite rollouts raise FloatingPointError instead of being zeroed by nan_to_num, the DFD detector matches "dfd" only in the last path component, the distilled example defaults to 24 fps, and the distilled rollout keeps its state in FP64 through the scheduler step as the official driver does.

Co-Authored-By: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [b8920ba](https://github.com/hao-ai-lab/FastVideo/commit/b8920ba50aae3e4dc9cc88a93fc8edc4bf2a07ef)

- **作者**: Achintya Rai
- **时间**: 2026-10-07T11:31:52Z
- **提交信息**: [misc]: add env var to control process-aware logging (#1680)

Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>
Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>

### [3467f8b](https://github.com/hao-ai-lab/FastVideo/commit/3467f8befbd77c40cc5941fdfa37bd3e2c069eb2)

- **作者**: Kai
- **时间**: 2026-10-07T11:25:00Z
- **提交信息**: [feat] Add end-to-end MMAudio V2A training, inference, and evaluation (#1648)

Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [7320d9d](https://github.com/hao-ai-lab/FastVideo/commit/7320d9d3501585f3662e9686ef75f12d10c496b0)

- **作者**: Kun Lin
- **时间**: 2026-10-07T11:20:58Z
- **提交信息**: [feat] Add HunyuanVideo 1.5 embedding preprocessing pipeline (#1663)

Adds preprocess_hunyuan15_overfit.py, which writes VAE latents plus Qwen and ByT5 text embeddings in the dual-text parquet schema (pyarrow_schema_t2v_dual_text) that main's HunyuanVideo 1.5 training (#1662) reads; main's guide and overfit config pointed at this script, but nothing in-tree produced text_embedding_2 before.

Reconciled with #1662 during maintainer review (Swarm orders #723 and #777): main's schema and collate are the base. On top of them, both text streams now share one CFG-dropout decision per row also when _sample_index is absent, and a row missing the primary text_embedding raises instead of training unconditioned. The PR's widening of the shared t2v schema and its writer changes were dropped. docs/training/hunyuan15_overfit.md now describes the in-tree script.

Co-Authored-By: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [af78c75](https://github.com/hao-ai-lab/FastVideo/commit/af78c759f1f7bc1157954d31b8915c8e9712a048)

- **作者**: Suhaan Khurana
- **时间**: 2026-10-07T11:19:37Z
- **提交信息**: [new-model] Add Wan2.2-Animate-14B character animation/replacement inference (#1765)

Co-authored-by: SuhaanCommits <suhaan@cedar.build>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>

### [f82c190](https://github.com/hao-ai-lab/FastVideo/commit/f82c190cbb297ca93430521c9518f3e239fe9c4e)

- **作者**: Raghav K
- **时间**: 2026-10-07T11:09:39Z
- **提交信息**: [kernel] Build + allow attn_qat_infer FP4 attention on sm_121a (DGX Spark) (#1598)

Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [e722023](https://github.com/hao-ai-lab/FastVideo/commit/e722023bd69b7a44b5caed58ec10e60bd5d58ed2)

- **作者**: Haochen Jiang
- **时间**: 2026-10-07T11:08:07Z
- **提交信息**: [perf] Wan kernel fusion: Triton-fused residual+LayerNorm+modulate inference path (#1708)

Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [bc0191d](https://github.com/hao-ai-lab/FastVideo/commit/bc0191d7755cbf676278dc31ea5a1287393f2d2f)

- **作者**: Shao Duan
- **时间**: 2026-10-07T11:01:53Z
- **提交信息**: [perf] Harden Ulysses agreement and tune bounded H3 transfers (#1807)

Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [2d6e7d9](https://github.com/hao-ai-lab/FastVideo/commit/2d6e7d9b6b9b77e98170a18432be62b01186751b)

- **作者**: MagicBear
- **时间**: 2026-10-07T10:46:33Z
- **提交信息**: [feat]: MiniMax-H3 encoder split: dedicated text-encoder node group for 720p on DGX Spark (#1877)

Co-authored-by: magicbear <magicbear@users.noreply.github.com>
Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [5e61acc](https://github.com/hao-ai-lab/FastVideo/commit/5e61accc37981c379248309af9ccf7ede32489c7)

- **作者**: Kevin Lin
- **时间**: 2026-10-07T10:44:49Z
- **提交信息**: [misc] Clean up QAD 5090 example inference scripts (#1496)

Split the FastWan-QAD Wan2.1-1.3B examples into per-recipe scripts (fp8, nvfp4_qat, nvfp4_sa2) with a shared _qad_common.py and a standalone multi-run benchmark harness, replacing FastWan_QAD_TAEHV.py.

The PR's fastvideo-kernel build changes (sm_121a arch probe and build.sh mapping) were dropped during maintainer review (Swarm order #664) in favour of #1598, which owns the kernel arch policy; the RTX 5090 (sm_120a) recipes need nothing beyond main's kernels.

Co-Authored-By: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [f605141](https://github.com/hao-ai-lab/FastVideo/commit/f60514183c613deb8d9b37767f8c408e8eb6e060)

- **作者**: Mac Lee
- **时间**: 2026-10-07T10:43:12Z
- **提交信息**: [ci] Separate performance behavior tests (#1620)

Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [156611b](https://github.com/hao-ai-lab/FastVideo/commit/156611bab3e9044578ac10e6f7bf4133adc96e34)

- **作者**: William Lin
- **时间**: 2026-10-07T10:37:46Z
- **提交信息**: [ci]: run the full attention test directory in the unit lane (#1658)

Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [6d6195a](https://github.com/hao-ai-lab/FastVideo/commit/6d6195a9f1a50eb349505897b74eaba7dcc44ccc)

- **作者**: William Lin
- **时间**: 2026-10-07T10:36:54Z
- **提交信息**: [feat]: fp8 PV mode for the FA4-FP4 attention path (#1654)

Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [8348e83](https://github.com/hao-ai-lab/FastVideo/commit/8348e83e803435062179d2e5bdd2047f58a72755)

- **作者**: Lele
- **时间**: 2026-10-07T10:34:40Z
- **提交信息**: [feat] Import MiniMax H3 Comfy NVFP4-AWQ text encoder (#1865)

Co-authored-by: 武垚乐 <wuyaole@mininglamp.com>
Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [2452022](https://github.com/hao-ai-lab/FastVideo/commit/2452022f156ff6dd55fbe5eacaba050d2f17189d)

- **作者**: Aryan Kumar
- **时间**: 2026-10-07T10:34:18Z
- **提交信息**: [new-model] Add LTX-2.5 inference support (#1704)

Co-authored-by: Aryan Kumar <aryan5v@users.noreply.github.com>
Co-authored-by: coderabbitai[bot] <136622811+coderabbitai[bot]@users.noreply.github.com>
Co-authored-by: CodeRabbit <noreply@coderabbit.ai>
Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [4b3f99b](https://github.com/hao-ai-lab/FastVideo/commit/4b3f99b224fb05b33df9783e5636f75d4ac3ac52)

- **作者**: Ishan
- **时间**: 2026-10-07T10:32:38Z
- **提交信息**: [new-model] Added LingBot-World-Fast image-to-video support (#1665)

Co-authored-by: Claude Sonnet 5 <noreply@anthropic.com>
Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>

### [d967b99](https://github.com/hao-ai-lab/FastVideo/commit/d967b9992885998d9a87058cd1337e59fe65fa4b)

- **作者**: William Lin
- **时间**: 2026-10-07T10:30:55Z
- **提交信息**: [bugfix]: registry ambiguity warning by specificity + QAD weights file path (#1649)

Registry: when several model detectors match a path, the first registered match still wins (main's pinned precedence, e.g. test_local_manifest_detectors_keep_first_match). Path specificity against each entry's registered HF paths now only decides whether to warn: the resolution is silent when the first match is strictly more specific than every other match (e.g. LTX-2.3 distilled directories that the LTX-2 base detector also claims through the shared pipeline class name), and warns otherwise, including when a later match is more specific than the one chosen. The PR originally re-ranked matches by specificity; that changed main's tested first-match resolution for local manifest directories, so it was narrowed during maintainer review (Swarm order #720).

Also fixes the QAD weights file path.

Co-Authored-By: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [8f1eb29](https://github.com/hao-ai-lab/FastVideo/commit/8f1eb2992c5291c0b3c06d12afe607f95df88bb1)

- **作者**: Aryan Kumar
- **时间**: 2026-10-07T10:29:46Z
- **提交信息**: [bugfix]: retain NVFP4 weights for LTX2 refinement LoRA (#1705)

Co-authored-by: Aryan Kumar <aryan5v@users.noreply.github.com>
Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [683689d](https://github.com/hao-ai-lab/FastVideo/commit/683689de4fb721021d30b4956b371d790b24e218)

- **作者**: pkisfaludi-nv
- **时间**: 2026-10-07T10:29:22Z
- **提交信息**: [bugfix] Fix Ulysses sequence-parallel crash in self-forcing causal Wan DiT (#1627)

Retargeted onto fastvideo/models/wan/causal_transformer.py, where main moved the causal Wan implementation (fastvideo/models/dits/causal_wanvideo.py is now a compatibility shim), with the guarded flex-attention trim prepared during the maintainer review (Swarm order #657).

Co-Authored-By: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [d5287f8](https://github.com/hao-ai-lab/FastVideo/commit/d5287f83520ffc5f848bd4b52fb6b22cbc6e5ddb)

- **作者**: Yanghao
- **时间**: 2026-10-07T10:21:45Z
- **提交信息**: [feat]: add MiniMax H3 Ref2VA and LoRA training support (#1757)

Co-authored-by: William Lin <8941107+SolitaryThinker@users.noreply.github.com>
Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [cdfbd64](https://github.com/hao-ai-lab/FastVideo/commit/cdfbd64b042bd0586e3bf7ec63e847573f2bc31c)

- **作者**: Keith
- **时间**: 2026-10-07T10:20:04Z
- **提交信息**: [perf] FP8: fuse the dynamic activation quantization into Triton kernels (#1861)

Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [299d0f6](https://github.com/hao-ai-lab/FastVideo/commit/299d0f683846c0544de50d7bd8bb939f08d18c50)

- **作者**: Haochen Jiang
- **时间**: 2026-10-07T10:19:42Z
- **提交信息**: [bugfix] wrap the generic DenoisingStage in the inference_denoising profiler region (#1707)

profiler_region_inference_denoising was wrapped in exactly one place (minimax_h3_denoising.py), so every model using the generic DenoisingStage (Wan among them) exported a trace with no denoising region. Wrap the denoising loops in DenoisingStage and DmdDenoisingStage with profiler_region("inference_denoising"); the loop bodies are untouched.

These are the two classes STAGE_METRIC_MAP names directly. The perf harness also reports dit_time_s for every stage that inherits performance_component_metric, and those forward overrides (Cosmos*, LongCat*, Gen3C, GameCraft, HYWorld, MatrixGame2/3, Causal*, DreamXWorldAR, LingBot, GlmImage) remain outside the region for now. With no profiler configured the wrap is a no-op; SSIM is exactly 1.0 on FLASH_ATTN and TORCH_SDPA.

Caveat: the region span now appears in exported traces, but a pre-existing profiler behaviour (region exit toggles CUDA collection off, fastvideo/profiler.py) may leave GPU kernel rows out of the trace.

Co-Authored-By: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [c184361](https://github.com/hao-ai-lab/FastVideo/commit/c18436125a9bc575d1022360921b4a13c04c40f1)

- **作者**: Joy Jefferson
- **时间**: 2026-10-07T10:19:21Z
- **提交信息**: [misc]: Refactor separate training pipeline runner (#1696)

Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [5d515ee](https://github.com/hao-ai-lab/FastVideo/commit/5d515ee617d9ef44aa7d9a4403635195a6b5a783)

- **作者**: Ishan
- **时间**: 2026-10-07T10:18:56Z
- **提交信息**: [perf]: remove per-step host syncs and repeated work from causal inference (#1687)

Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [37b9dc1](https://github.com/hao-ai-lab/FastVideo/commit/37b9dc1836bd2c71d441d5bfda647976dec81e7c)

- **作者**: page: FlappyBob
- **时间**: 2026-10-07T10:18:24Z
- **提交信息**: [new-model] Add native Helios-Distilled T2V pipeline (#1670)

Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [a0291a5](https://github.com/hao-ai-lab/FastVideo/commit/a0291a57c1d67965d2f75f05cd2d7a052ac1d611)

- **作者**: Suhaan Khurana
- **时间**: 2026-10-07T09:44:24Z
- **提交信息**: [ci] Add Wan2.2-TI2V-5B SSIM regression test (#1772)

Co-authored-by: SuhaanCommits <suhaan@cedar.build>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>

### [6102fac](https://github.com/hao-ai-lab/FastVideo/commit/6102fac00da5fce055dc219662ed6374638dc48d)

- **作者**: Shao Duan
- **时间**: 2026-10-07T09:41:12Z
- **提交信息**: [bugfix]: fix modular ops activation checkpoint recomputation (#1716)

Co-authored-by: William Lin <8941107+SolitaryThinker@users.noreply.github.com>
Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [1ad33c1](https://github.com/hao-ai-lab/FastVideo/commit/1ad33c18320e48e0d8536255889a8ef62cbb38fb)

- **作者**: alanhuangyoo
- **时间**: 2026-10-07T09:38:42Z
- **提交信息**: [feat] Support training_cfg_rate > 0 for LTX-2 (#1752)

Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [da87973](https://github.com/hao-ai-lab/FastVideo/commit/da87973412ceadf3d0c43f20f748a23b66830476)

- **作者**: Mac Lee
- **时间**: 2026-10-07T09:33:18Z
- **提交信息**: [ci] Clarify dashboard cohort grouping for legacy v1 records (#1613)

Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [a3fd1d0](https://github.com/hao-ai-lab/FastVideo/commit/a3fd1d0bab442b171e23006e2b4094a7104a99ec)

- **作者**: William Lin
- **时间**: 2026-10-07T09:32:48Z
- **提交信息**: [ci]: prevent direct tests from minting suite gates (#1615)

Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [3e87d6f](https://github.com/hao-ai-lab/FastVideo/commit/3e87d6f4ae04449b3ed3153554acbeaa92463634)

- **作者**: Keith
- **时间**: 2026-10-07T09:32:27Z
- **提交信息**: [feat] ROCm: route the video sparse attention backends to their Triton kernels (#1851)

Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [4bb5627](https://github.com/hao-ai-lab/FastVideo/commit/4bb5627fa8c4267dc576b5433119f77f31259456)

- **作者**: Keith
- **时间**: 2026-10-07T09:31:52Z
- **提交信息**: [feat] MiniMax H3: block-FP8 text encoder on Hopper, its converter, and a 4xH100 FastH3 profile (#1829)

Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [08ab8b5](https://github.com/hao-ai-lab/FastVideo/commit/08ab8b5c00524d69204604704e1c9f5a2e5ca4f3)

- **作者**: Keith
- **时间**: 2026-10-07T09:20:47Z
- **提交信息**: [bugfix] ROCm: detect the platform from a HIP torch build when amdsmi is unavailable (#1849)

Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [fb5efeb](https://github.com/hao-ai-lab/FastVideo/commit/fb5efebdab2d47ed465d4062ecc6b194204ff173)

- **作者**: Kyle Hu
- **时间**: 2026-10-07T09:19:22Z
- **提交信息**: [feat] Add HunyuanVideo 1.5 T2V training support (#1662)

Co-authored-by: William Lin <willlin@nvidia.com>
Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [6e4813f](https://github.com/hao-ai-lab/FastVideo/commit/6e4813f8b408ed789ce6015370c7e386163d3c38)

- **作者**: YZJF
- **时间**: 2026-10-07T09:18:23Z
- **提交信息**: [bugfix] use in-process executor for num_gpus=1 (#1755) (#1879)

Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [13ef81e](https://github.com/hao-ai-lab/FastVideo/commit/13ef81e6da5546d8eff0e8ea99fd187912e7c1ca)

- **作者**: Yogya Mehrotra
- **时间**: 2026-10-07T09:14:02Z
- **提交信息**: [ci] Surface worker process logs on perf hard regressions (#1701)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>

### [13b3b36](https://github.com/hao-ai-lab/FastVideo/commit/13b3b36b8b47b7ec298cfd9e22cb3529c9691544)

- **作者**: Shao Duan
- **时间**: 2026-10-07T09:07:37Z
- **提交信息**: [feat] Add Infinite Livestream app (#1878)

Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [72795d0](https://github.com/hao-ai-lab/FastVideo/commit/72795d0af88ca498f7d46bdb2727521274942403)

- **作者**: boxwrench
- **时间**: 2026-10-07T08:54:35Z
- **提交信息**: [perf] avoid full-sequence materialization in VSA coarse/sparse combine (#1813)

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>
Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>

### [af63a92](https://github.com/hao-ai-lab/FastVideo/commit/af63a92f6a594677630566a61a8b67f39fde407a)

- **作者**: Satyam Srivastava
- **时间**: 2026-10-07T08:54:03Z
- **提交信息**: [bugfix] Shut down Inductor workers gracefully (#1786)

Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [a4e7322](https://github.com/hao-ai-lab/FastVideo/commit/a4e7322ba6d039c2ca7dcd5c71af13c70acce312)

- **作者**: Suckl
- **时间**: 2026-10-07T08:53:30Z
- **提交信息**: [bugfix]: synchronize post-FSDP LoRA replicas (#1666)

Co-authored-by: Suckl <Suckl@users.noreply.github.com>
Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [d6e13f9](https://github.com/hao-ai-lab/FastVideo/commit/d6e13f9cc849af253b5539631242aed2f8535fbd)

- **作者**: Raghav K
- **时间**: 2026-10-07T08:39:11Z
- **提交信息**: [feat] Add VQeval long-video quality metric (#1727)

Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [6c4c186](https://github.com/hao-ai-lab/FastVideo/commit/6c4c18690e6798722c766489d3e9c4a1e6341db8)

- **作者**: Jie Luo
- **时间**: 2026-10-07T08:38:43Z
- **提交信息**: [bugfix] Enable SP for LongCat BSA refinement (#1862)

Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [a8688dd](https://github.com/hao-ai-lab/FastVideo/commit/a8688dddd9a199728862ab8b40079565481e2197)

- **作者**: YZJF
- **时间**: 2026-10-07T08:38:02Z
- **提交信息**: [bugfix]: requantize MXFP8 weights after LoRA unmerge (#1876)

Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [cacc8cf](https://github.com/hao-ai-lab/FastVideo/commit/cacc8cfcb3bbd7b9a09caa02b7c400cd5f46e3e8)

- **作者**: Kyle Hu
- **时间**: 2026-10-07T08:36:35Z
- **提交信息**: [bugfix]: condition HunyuanVideo 1.5 i2v on the reference image (#1693)

Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [ef62ac4](https://github.com/hao-ai-lab/FastVideo/commit/ef62ac48d1a4a7eec7f42733b363b03638359156)

- **作者**: Suhaan Khurana
- **时间**: 2026-10-07T08:36:01Z
- **提交信息**: [new-model] Add Wan2.2-S2V-14B speech-to-video (model port + checkpoint converter) (#1683)

Co-authored-by: SuhaanCommits <suhaan@cedar.build>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>

### [00cb7d0](https://github.com/hao-ai-lab/FastVideo/commit/00cb7d0ba2412eafe4c944dd3643c71da5b1f936)

- **作者**: Raghav K
- **时间**: 2026-10-07T08:30:42Z
- **提交信息**: [ci] Add DGX Spark (GB10) single-GPU perf config + gpu_types gating (#1679)

Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [69a6215](https://github.com/hao-ai-lab/FastVideo/commit/69a6215e7f8173bf7122360c92c9ff6c1a603132)

- **作者**: jayzou
- **时间**: 2026-10-07T08:30:26Z
- **提交信息**: [feat] Add Dreamverse multimodal inputs and H3 routing (#1835)

Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [abe98e8](https://github.com/hao-ai-lab/FastVideo/commit/abe98e87f529f6ae44f3aadb7020a8a5145f9566)

- **作者**: Jack Chen
- **时间**: 2026-10-07T08:30:11Z
- **提交信息**: [feat] Add phase-aware modular training performance metrics (#1826)

Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [274b922](https://github.com/hao-ai-lab/FastVideo/commit/274b922d399880f617017372bc8130e4373cd165)

- **作者**: Kyle Hu
- **时间**: 2026-10-07T08:29:56Z
- **提交信息**: [misc]: surface GenerationResult.peak_memory_mb in the MiniMax H3 examples (#1785)

Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [3896605](https://github.com/hao-ai-lab/FastVideo/commit/38966056d0907a1b5b6216442694278562eab3a5)

- **作者**: Kyle Hu
- **时间**: 2026-10-07T08:29:42Z
- **提交信息**: [ci]: make merge-gate startup reliable (#1762)

Co-authored-by: William Lin <8941107+SolitaryThinker@users.noreply.github.com>
Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [d8ca702](https://github.com/hao-ai-lab/FastVideo/commit/d8ca702dfdb5140ab649252bafaff34db43cb02f)

- **作者**: alanhuangyoo
- **时间**: 2026-10-07T08:28:53Z
- **提交信息**: [bugfix] registry: register magi_human presets (#1751)

Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-10-08
**监控日期**: 2026-10-07
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34684
- **最后更新**: 2026-10-07T20:18:36Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Steven Liu

## AI分析总结

## 分析总结：`huggingface/diffusers` 昨日提交（[122b1e1] [docs] Community methods, PR #14973）

### 1. 主要更新类型
**纯文档更新**。该提交不涉及核心代码逻辑改动，而是在项目文档体系中新增/整理了社区方法（Community methods）的介绍内容，涉及 FreeU 与 CacheEdit 两个社区贡献的扩散模型技术。

### 2. 关键变更点及其与项目整体方向的关系
- **FreeU**：一种通过在 U-Net 各阶段重新加权低频与高频特征、在无需额外参数的前提下提升生成质量的社区方法。
- **CacheEdit**：围绕推理缓存优化（复用部分去噪步骤的中间结果）的社区方案，目标是加速扩散模型的采样过程。
- 这些方法本身并非由 diffusers 官方核心团队开发，而是社区研究者的成果。将它们收录进项目文档，体现了 diffusers 一贯的 **"社区驱动 + 方法汇聚"** 的生态战略：官方库作为扩散模型研究成果转化与传播的公共枢纽。

### 3. 对项目的影响和潜在意义
- **降低用户的采纳门槛**：开发者无需自行检索论文或零散代码，即可在 diffusers 的文档/示例中找到 FreeU、CacheEdit 的实现思路与用法指引，促进方法的快速复现与二次开发。
- **增强生态黏性**：持续收录社区方法让项目始终保持对前沿研究的覆盖度，吸引研究者把实现贡献回 diffusers，形成正向循环。
- **潜在风险**：文档中社区方法的维护责任相对松散，若缺乏持续更新，示例可能与最新版本 API 脱节，需要社区维护者跟进。

### 4. 值得关注的技术点
- FreeU 代表了一类 **"零成本质量提升"** 方法——不改动训练流程，仅在推理阶段做特征调制，这类思路对边缘/低算力场景尤其有价值。
- CacheEdit 属于 **缓存感知加速** 方向（与 DeepCache、TeaCache 等同源），是当前扩散模型推理优化的热点领域，提示用户可以在不牺牲明显质量的前提下降低延迟。
- 两者的组合（质量提升 + 推理加速）恰好覆盖了扩散模型应用最关心的两个维度，收录它们显示了文档编排上的前瞻性取向。

### 5. 基于项目背景对发展路径的影响
diffusers 的愿景（Apache-2.0 许可的开源库）天然要求它既做官方核心功能的开发，又做社区研究成果的“落地载体”。本次文档提交虽小，但强化了以下发展路径：
- **保持方法谱系的广度与新鲜度**，让项目始终与扩散模型学术界同步；
- **通过文档而非代码侵入的方式引入社区方法**，避免了核心库膨胀，维持了代码库的稳定性与可信度；
- 为后续将这些社区方法 **正式吸收进 `diffusers` 原生管道/调度器** 打下了认知基础——一旦某方法被验证稳定且有广泛需求，团队更容易评估将其核心化。

总体而言，这是一次典型的生态维护型提交：它不改变库的功能边界，却持续巩固 diffusers 作为扩散模型 **事实标准实现库** 的社区地位，对项目的长期影响力提升具有不可忽视的累积作用。

## 详细提交记录

### [122b1e1](https://github.com/huggingface/diffusers/commit/122b1e11fd497c3eeef14b3b98ca26a60166e48b)

- **作者**: Steven Liu
- **时间**: 2026-10-07T15:04:42Z
- **提交信息**: [docs] Community methods (#14973)

* freeu

* cachedit

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-10-08
**监控日期**: 2026-10-07
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 433
- **最后更新**: 2026-09-26T17:57:59Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-10-08
**监控日期**: 2026-10-07
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13208
- **最后更新**: 2026-10-07T22:42:18Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-10-08
**监控日期**: 2026-10-07
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 36844
- **最后更新**: 2026-10-08T01:41:51Z

## 提交统计

- **昨日提交总数**: 30
- **提交者数量**: 15
- **主要提交者**: Yihao Wang, Po-Han Huang (NVIDIA), Артем Савкин

## AI分析总结

# sgl-project/sglang 昨日提交分析（第 1/1 批）

## 1. 主要更新类型

- **重构（Refactor）为主**：并行分组（parallel group）选择机制与 checkpoint 加载架构的系统性重构，涉及模型线性层、MLP、MLA 投影、视觉编码器等多个模块。
- **Scheduler 调度器逻辑精简**：多处内部数据结构与预填充进度追踪的改造。
- **Bug 修复**：涵盖 FP8 量化、dLLM、diffusion（DiT 缓存、hybrid SP+TP）、GLM-V 视觉塔分片、K2 Horizon 等多个子系统。
- **功能新增**：HiCache 引入 SeaweedFS L3 存储后端、API 规范文档。
- **依赖与文档**：transformers 升级到 5.19.0，新增 GLM-5.3-Flash MI355X MXFP4 实测配方文档。

## 2. 关键变更点与项目方向的关系

- **并行分组选择机制下放**（#42426–#42590 系列）：将 parallel group 的选择从中央配置下沉到各模型组件（线性层、MLP、MLA、视觉编码器）自行选择，并保留进程组在并行线性层中。这一方向直接服务于 SGLang 支持**更多异构并行策略**（如 DP attention + TP 混合、视觉塔在 attention-TP 组上分片，#42931）的目标。
- **Checkpoint 加载重构**：使用目标布局映射和 owner partitions 加载辅助/专家权重，简化 MoE 大模型权重的加载路径。
- **Scheduler 内部语义重构**（#42822–#42825）：用 `prefix_len` + `extend_end` 替代 `extend_range`，从 `last_node` 推导前缀 KV 索引，删除 `Req.prefix_indices`，将匹配写回折叠进 `match_kv_cache`——统一前缀 KV 缓存的语义，为 HiCache 等分层缓存铺路。
- **硬件平台适配**：AMD gfx1250（MI355X）上 diffusion 内核的多次适配、ROCm DSA indexer 适配，体现项目对**多硬件后端**的持续投入。

## 3. 对项目的影响和潜在意义

- 重构类提交通常不改变外部 API，但降低了多模态、MoE 与异构并行场景下的维护成本，为未来模型/并行组合快速落地扫清障碍。
- SeaweedFS L3 后端拓展了 HiCache 的存储层级选择，提升长上下文缓存的可扩展性。
- Scheduler 精简减少了状态冗余，降低 prefix caching 路径的出错概率。

## 4. 值得关注的技术点

- **并行分组选择权的下放模式**：组件级自治选择替代集中配置，是 SGLang 架构演进的一个清晰信号。
- **FP8 重载量化**（#42858、#42825）：原生分片后对重载 FP8 权重重新量化，避免精度退化。
- **FA4 SM100 MLA kernel**：保持 stream 在末位以支持磁盘缓存对象加载，属 GPU 内核层的细节优化。
- **diffusion 模块的 CI 分层**：diffusion 专属内核与测试移出 srt 阶段，反映项目多模态（图像/视频生成）模块已成长到需要独立 CI 管道的规模。

## 5. 对项目发展的总体影响

结合 README（SGLang 致力于 LLM 与多模态模型的快速推理），这一批提交表明项目正处于**架构加固期**：通过系统性重构并行与调度基础设施，强化多模态（GLM-V、diffusion）和多硬件（AMD、ROCm）支持，同时借助分层缓存（HiCache + SeaweedFS）扩展长上下文推理的可扩展性。这些变更为后续更多模型形态和更大规模部署奠定了基础，而多个提交由 AI 协作生成（Claude 系列署名）也体现出 AI 辅助开发在该项目中的常态化应用。

## 详细提交记录

### [7760d52](https://github.com/sgl-project/sglang/commit/7760d5264ac16b85392aefb1bf5c13ce38d9632e)

- **作者**: Cheng Wan
- **时间**: 2026-10-07T23:24:22Z
- **提交信息**: [Refactor] Use destination layouts for model checkpoint mappings (#42590)

### [5e12831](https://github.com/sgl-project/sglang/commit/5e12831cec1c093202cfeecfc2ff3918e8cb6cd9)

- **作者**: Cheng Wan
- **时间**: 2026-10-07T23:24:03Z
- **提交信息**: [Refactor] Load auxiliary and expert checkpoints using owner partitions (#42589)

### [64c7f65](https://github.com/sgl-project/sglang/commit/64c7f65eaccc748b11a1199590ea91648e332628)

- **作者**: Cheng Wan
- **时间**: 2026-10-07T23:23:40Z
- **提交信息**: [Refactor] Retain process groups in parallel linear layers (#42588)

### [267e345](https://github.com/sgl-project/sglang/commit/267e34516cae2f259702a400b7e1e4630b2e225c)

- **作者**: Cheng Wan
- **时间**: 2026-10-07T23:22:57Z
- **提交信息**: [Refactor] Select parallel groups for remaining model projections (#42587)

### [dec5d9d](https://github.com/sgl-project/sglang/commit/dec5d9d6fc70cd341b793a8259fb346d792ade36)

- **作者**: Cheng Wan
- **时间**: 2026-10-07T23:22:32Z
- **提交信息**: [Refactor] Let vision encoders select their parallel group (#42586)

### [b83827e](https://github.com/sgl-project/sglang/commit/b83827ea02618332f4bc8b60dec92baec80a3c37)

- **作者**: Cheng Wan
- **时间**: 2026-10-07T23:20:47Z
- **提交信息**: [Fix] Quantize reloaded FP8 weights after native sharding (#42585)

### [59740a7](https://github.com/sgl-project/sglang/commit/59740a728fe3dc62d231b8519b4c32557a22188c)

- **作者**: Cheng Wan
- **时间**: 2026-10-07T23:19:33Z
- **提交信息**: [Refactor] Let MLA projections select their parallel group (#42484)

### [961d729](https://github.com/sgl-project/sglang/commit/961d7290fe272f3263a5dd52624f9ec250b95ea7)

- **作者**: Cheng Wan
- **时间**: 2026-10-07T23:18:14Z
- **提交信息**: [Refactor] Let model MLPs select their parallel group (#42468)

### [4c5130a](https://github.com/sgl-project/sglang/commit/4c5130ac5ab9ff8446cddd9fbaddfa4b45153206)

- **作者**: Cheng Wan
- **时间**: 2026-10-07T23:15:26Z
- **提交信息**: [Refactor] Let linear layers select their parallel group (#42426)

### [1066dec](https://github.com/sgl-project/sglang/commit/1066decce698d8fcca214946ad7d4f8356805b0b)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-07T23:07:16Z
- **提交信息**: [Scheduler] Replace `extend_range` with `extend_end` derived from `prefix_len` (#42822)

### [5349d3e](https://github.com/sgl-project/sglang/commit/5349d3e9d2e42653dff28632e7b27df67209da46)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-07T23:03:09Z
- **提交信息**: [Scheduler] Derive prefix KV indices from `last_node` at allocation; drop `Req.prefix_indices` (#42825)

### [e9240b3](https://github.com/sgl-project/sglang/commit/e9240b32436e67e3a845c04209089da2d926f848)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-07T22:59:06Z
- **提交信息**: [Scheduler] Track prefill progress as `prefix_len` (#42824)

### [79ef49c](https://github.com/sgl-project/sglang/commit/79ef49cb6bf94cb9f14f10b205f6ee506cd8b652)

- **作者**: Kevin Mi
- **时间**: 2026-10-07T22:49:49Z
- **提交信息**: [Docs] GLM-5.3-Flash: measured MI355X MXFP4 agentic recipe (#43015)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [4bf8f28](https://github.com/sgl-project/sglang/commit/4bf8f28d15b01843a290c33fa918c001f8f32afd)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-07T22:43:05Z
- **提交信息**: [Scheduler] Fold match write-back into `match_kv_cache` (#42823)

### [b1ffe5c](https://github.com/sgl-project/sglang/commit/b1ffe5c16a6cede33860918595c8e186be317da2)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-07T22:39:33Z
- **提交信息**: [dLLM] Keep the request row across FDFO blocks (#42846)

### [685d4d4](https://github.com/sgl-project/sglang/commit/685d4d453d2e1627eba0f933ea04d0e44f1dd4da)

- **作者**: Ping Qiu
- **时间**: 2026-10-07T22:05:37Z
- **提交信息**: [HiCache] Add SeaweedFS L3 storage backend (#42399)

Co-authored-by: Zhiqiang Xie <xiezhq@stanford.edu>

### [0b63526](https://github.com/sgl-project/sglang/commit/0b635266d4a09f8db2d12bdcb793b085199faa8f)

- **作者**: WenhaoZhang
- **时间**: 2026-10-07T15:26:36Z
- **提交信息**: [diffusion] CI: warm up CI cases at the request's quality level (#42958)

### [00b21d6](https://github.com/sgl-project/sglang/commit/00b21d64151e7b5793bdde5dcb5b6420225a4987)

- **作者**: Wenbo Ji　嵇文博
- **时间**: 2026-10-07T15:25:49Z
- **提交信息**: [diffusion] fix: reset DiT cache state at the start of each request (#42437)

Co-authored-by: Mick <mickjagger19@icloud.com>
Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [44d10ea](https://github.com/sgl-project/sglang/commit/44d10eab5e7d31e9deab73b142d1288e1bfc74a4)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-10-07T15:17:06Z
- **提交信息**: [GLM-V] Shard the vision tower over the attention-TP group under DP attention (#42931)

Co-authored-by: Mohammad Angkad <mohammad.angkad@radixark.ai>

### [d9a0f1c](https://github.com/sgl-project/sglang/commit/d9a0f1cb340cdbf1842bf9526015d846eb72f25d)

- **作者**: Артем Савкин
- **时间**: 2026-10-07T14:33:03Z
- **提交信息**: [diffusion] fix: fix hybrid SP+TP for I2V models   (#41917)

Co-authored-by: Mick <mickjagger19@icloud.com>
Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [1e86143](https://github.com/sgl-project/sglang/commit/1e86143bf06d40082de878f05b8782b043f61ad2)

- **作者**: Po-Han Huang (NVIDIA)
- **时间**: 2026-10-07T13:02:40Z
- **提交信息**: [Bugfix] Return None for empty reasoning_content outside K2 Horizon (#42962)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [492dbd0](https://github.com/sgl-project/sglang/commit/492dbd0807d21e0faa72a55a2c09f541cb4696b6)

- **作者**: WenhaoZhang
- **时间**: 2026-10-07T12:28:53Z
- **提交信息**: [CI] keep diffusion-only kernels and tests out of the srt stages (#42706)

### [aa5551d](https://github.com/sgl-project/sglang/commit/aa5551d9b6ebe133427a8a0b368c2643f79d5440)

- **作者**: Tianyang Gu
- **时间**: 2026-10-07T09:56:39Z
- **提交信息**: [diffusion] fix: do not interleave comfy-kitchen MXFP8 scales twice (#38028)

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [c389cba](https://github.com/sgl-project/sglang/commit/c389cbaf99e1b1ddd77005c9107bb3dae7bb89d7)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-10-07T09:37:43Z
- **提交信息**: [AMD][diffusion] Route bf16 fuse_scale_shift to the native fallback on gfx1250 (#42859)

### [49d7d60](https://github.com/sgl-project/sglang/commit/49d7d60dfa5f6f9fade9986a80627279d044d20c)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-10-07T09:32:02Z
- **提交信息**: [AMD][diffusion] VAE attention to the math SDPA backend on gfx1250 (#42858)

### [11972e5](https://github.com/sgl-project/sglang/commit/11972e520709a76766f91744a672e92727fdcb09)

- **作者**: Yihao Wang
- **时间**: 2026-10-07T09:04:08Z
- **提交信息**: [deps] bump transformers to 5.19.0 (#42784)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [c52dcc5](https://github.com/sgl-project/sglang/commit/c52dcc5a01744b3ba236c44fd3eb995142cb1919)

- **作者**: Rain Jiang
- **时间**: 2026-10-07T08:55:01Z
- **提交信息**: The sgalng api specs (#41585)

### [ba77d30](https://github.com/sgl-project/sglang/commit/ba77d30256bfb1d1e0d53cd877c87f0b2e279ef1)

- **作者**: Po-Han Huang (NVIDIA)
- **时间**: 2026-10-07T07:58:55Z
- **提交信息**: [FA4] Keep stream last in the SM100 MLA kernel so disk-cached objects load (#42926)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [e230930](https://github.com/sgl-project/sglang/commit/e23093077e4698af434e3d5c2fc52b1b10414dca)

- **作者**: Khoa Pham
- **时间**: 2026-10-07T07:53:17Z
- **提交信息**: [DSv4] Fix shared index cache accessor page size (#42832)

### [1c42ad3](https://github.com/sgl-project/sglang/commit/1c42ad3679fcad7fa4609189763b01ee9f5bd28b)

- **作者**: jiaryang
- **时间**: 2026-10-07T07:16:46Z
- **提交信息**: [ROCm] Skip the tilelang act_quant in the DSA indexer on gfx1250 (#42747)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-10-08
**监控日期**: 2026-10-07
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1289
- **最后更新**: 2026-10-07T00:36:25Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-10-08
**监控日期**: 2026-10-07
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 93352
- **最后更新**: 2026-10-08T01:58:05Z

## 提交统计

- **昨日提交总数**: 43
- **提交者数量**: 38
- **主要提交者**: Moein Khazraee, Mikko Tukiainen, Andy Lo

## AI分析总结

## vLLM 昨日提交分析总结（第 1/1 批，43 条）

### 一、主要更新类型分布

- **Bug修复（约 22 条）**：占比最高，覆盖 tool-parser/tokenizer 兼容性校验、KV cache offload、MoE/量化、调度器、多模型（DSv4.1、GlmMoeDsa、Qwen4Exp、Hybrid Mamba）等领域。
- **性能优化（约 12 条）**：以 ROCm/NVIDIA 硬件相关为主，包括 AITER 融合算子、NVFP4 量化 KV cache、RDNAHybridW4A16、Intel XPU MoE 调优等。
- **CI/构建与测试（约 10 条）**：依赖版本升级、测试修复与跳过策略、Rubin 镜像构建、provenance 标签等。
- **文档/开发规范（3 条）**：PR 检查清单、review 区域说明。
- **功能新增/重构（少量）**：Rust 前端的 gRPC 限制与 Schema 共享、spec decode 命名重构。

### 二、关键变更点与项目方向的关系

vLLM 的核心目标是“为所有人提供简单、快速、低成本的 LLM 服务”，这批提交精准呼应这一使命：

1. **多硬件后端持续深化（NVIDIA / ROCm / XPU）**：NVFP4 KV cache 支持扩展到 SM8x/SM12x、AITER MegaMoEV2、FlyDSL GDN 后端、Rubin 镜像构建——体现 vLLM 从单一 CUDA 生态向多平台推理的演进，是降低硬件成本的关键路径。
2. **量化技术栈完善**：per-token NVFP4 MoE（ReLU2）、Humming A16 折叠 scale、fp8 KV cache 限制在 SM100——量化直接服务于“低成本”目标，同时以兼容性修复保证正确性。
3. **KV Cache Offload 与内存管理**：KVCR 工厂恢复、pool-and-index API、同步 READ 目标排除——支撑多层级存储架构，缓解显存瓶颈。
4. **前端与开发体验**：Rust 前端共享 Schema、gRPC 禁止 token 序列、安全文本回溯、MTP 检查点分片跳过——提升服务稳定性和部署体验。

### 三、对项目的影响与潜在意义

- **稳定性显著增强**：大量 bugfix 集中在启动期校验、加载路径、硬件能力边界（如 SWA bounded replay、非因果能力范围限定），可减少生产环境的隐性崩溃与精度问题。
- **生态覆盖扩大**：DeepSeek V4.1、MiniMax-M3、Gemma、GLM-5.3、Qwen4Exp、EmbeddingGemma 等模型获得针对性优化，强化 vLLM 作为“模型无关”推理引擎的地位。
- **社区协作活跃**：43 条提交来自 AMD、NVIDIA、Red Hat、Mistral、Ant Group、Daocloud 等多方，AI 辅助编码（Claude、Codex、Cursor、Kimi）参与度明显提升，反映项目已进入高吞吐维护模式。

### 四、值得关注的技术点

1. **FlashInfer + NVFP4 KV cache 跨架构支持（#46963）**：低精度 KV cache 与注意力后端深度结合，是推理成本下探的重要方向。
2. **spec decode 与量化协同修复（FlashInfer warmup 崩溃、MXFP8 split-K）**：投机解码+低精度组合已成为易碎但高收益的组合，需持续维护。
3. **Rust 前端的 Schema 复用与回溯机制**：暗示 vLLM 正在打造独立、高性能的网关层，与 Python 核心解耦。
4. **Transformer 版本升级至 5.19.0（#60381）**：版本联动将影响模型加载与 EmbeddingGemma 等测试矩阵，需关注后续兼容性。

### 五、对项目整体发展的判断

基于 README 定位——“Easy, fast, and cheap LLM serving for everyone”，这批提交表明 vLLM 当前的发展策略是：**以硬件后端广度 + 量化深度驱动“cheap”，以 bugfix 和 CI 健壮性驱动“easy”，以多模型/多平台适配驱动“fast”**。项目的重心已从单纯的速度竞赛，转向在复杂异构硬件与低精度算子组合下的可靠性与可运维性。这为进入更多企业级部署场景奠定了基础，也对新贡献者提出了更高的跨硬件、跨精度协同维护要求。

## 详细提交记录

### [38dc8ee](https://github.com/vllm-project/vllm/commit/38dc8ee50055622ab0d5fe6bb32a5aee526bcbf5)

- **作者**: www6v
- **时间**: 2026-10-07T23:46:41Z
- **提交信息**: [Bugfix] Validate tool-parser/tokenizer compatibility at startup (#59749)

Signed-off-by: www6v <www6v@126.com>
Signed-off-by: sfeng33 <4florafeng@gmail.com>
Co-authored-by: sfeng33 <4florafeng@gmail.com>

### [d6fe5dc](https://github.com/vllm-project/vllm/commit/d6fe5dca686b3f6c5f018d399f4f119fedf842f1)

- **作者**: Dhairyashil R G
- **时间**: 2026-10-07T23:21:51Z
- **提交信息**: [Bugfix][Parser] Emit buffered post-reasoning text when no tool parser is configured (#58911)

Signed-off-by: Dhairyashil R G <18738735+dhairyashilRG@users.noreply.github.com>
Signed-off-by: sfeng33 <4florafeng@gmail.com>
Co-authored-by: sfeng33 <4florafeng@gmail.com>

### [4ac5a36](https://github.com/vllm-project/vllm/commit/4ac5a36a8e38b79c8084589b0bc4f2a249bf7c2a)

- **作者**: Artem Perevedentsev
- **时间**: 2026-10-07T22:44:17Z
- **提交信息**: [CI/Build][NVIDIA] Build NIXL with NIXL EP from source in Rubin image (#60090)

Signed-off-by: Artem Perevedentsev <aperevedents@nvidia.com>

### [ef63c23](https://github.com/vllm-project/vllm/commit/ef63c23d35acccbba8e014fc88da19d541da38a9)

- **作者**: Yifan Qiao
- **时间**: 2026-10-07T22:28:42Z
- **提交信息**: [Bugfix][DSv4.1] Skip SWA bounded replay for KV loads that carry the window (#59197)

Signed-off-by: Yifan Qiao <yifanqiao@inferact.ai>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [d169c5a](https://github.com/vllm-project/vllm/commit/d169c5a90354233d2acec687aec201971fa135fb)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-10-07T22:16:05Z
- **提交信息**: [Docs] Add disagg PD flow-example guidance to /pr-checklist skill (#60111)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>
Co-authored-by: Mistral Vibe <noreply@mistral.ai>

### [f38c677](https://github.com/vllm-project/vllm/commit/f38c6778ce4cf62b1ca7a8e091892f5bfdf79f98)

- **作者**: Xuanteng Huang
- **时间**: 2026-10-07T22:01:09Z
- **提交信息**: [quantization] Add per-token NVFP4 quantization MoE support for ReLU2 (#56740)

Signed-off-by: Xuanteng Huang <xuantengh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [b803edb](https://github.com/vllm-project/vllm/commit/b803edbc9fa5adbbf31136bf128d88533f7d39c2)

- **作者**: Luciano Martins
- **时间**: 2026-10-07T21:56:40Z
- **提交信息**: [Model] Streamline EmbeddingGemma 2 config resolution and harmonize Triton prefill attention (#60289)

Signed-off-by: Luciano Martins <lucianommartins@users.noreply.github.com>
Co-authored-by: Luciano Martins <lucianommartins@users.noreply.github.com>
Co-authored-by: Matthew Bonanni <mbonanni@redhat.com>

### [947dd62](https://github.com/vllm-project/vllm/commit/947dd62c0700851a79b0a8f32cb823e25a003b31)

- **作者**: Simon Danielsson
- **时间**: 2026-10-07T21:18:19Z
- **提交信息**: [CI] Fix failing test_deepseek_v4_rocm_dspark* tests (#60462)

Signed-off-by: simondanielsson <simon.danielsson99@hotmail.com>

### [b47ec44](https://github.com/vllm-project/vllm/commit/b47ec440bc0f2342848d6f1d99942cc3e909a66a)

- **作者**: Thang Nguyen
- **时间**: 2026-10-07T21:15:39Z
- **提交信息**: [CI] Stamp provenance labels on the torch-nightly image so Initialized Snapshot E2E can run (#59487)

Signed-off-by: Thang Nguyen <thangnguyenvn647@gmail.com>
Co-authored-by: Kimi <noreply@moonshot.cn>

### [a982c81](https://github.com/vllm-project/vllm/commit/a982c81e3ed337f76b116338192c83f776a3225c)

- **作者**: Misha Goin
- **时间**: 2026-10-07T20:37:13Z
- **提交信息**: [Bugfix] Limit GlmMoeDsaForCausalLM fp8 KV cache default to SM100 (#60281)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [0856750](https://github.com/vllm-project/vllm/commit/08567505b09324f891797f4a13c1bd73fc75a827)

- **作者**: Rui
- **时间**: 2026-10-07T19:36:57Z
- **提交信息**: [Bugfix][KV Offload] Restore KVCR construction through the secondary-tier factory (#58088)

### [e572e02](https://github.com/vllm-project/vllm/commit/e572e02d21b2b3559b3ce33adb117dca3f50ccd7)

- **作者**: Robert Shaw
- **时间**: 2026-10-07T19:16:19Z
- **提交信息**: [UX] Skip checkpoint shards an MTP head does not load  (#60152)

Signed-off-by: Robert Shaw <robshaw@redhat.com>
Co-authored-by: Robert Shaw <robshaw@redhat.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [17c70c8](https://github.com/vllm-project/vllm/commit/17c70c895359f7c941199bdf49b723c602ba75de)

- **作者**: Moein Khazraee
- **时间**: 2026-10-07T19:14:07Z
- **提交信息**: [KV Offload] Update KVCR adapter to pool-and-index API (#59899)

### [b976729](https://github.com/vllm-project/vllm/commit/b9767299db6d5c0226e6879dadb079a477524d3a)

- **作者**: Cheese Cake
- **时间**: 2026-10-07T19:08:11Z
- **提交信息**: [Bugfix] Respect Inductor deterministic mode in combo-kernel defaults (#59074)

Signed-off-by: cheesecake <farzanaman99@gmail.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [32fbfa1](https://github.com/vllm-project/vllm/commit/32fbfa15e8bacc64182cb1286831bd63d7e4fc12)

- **作者**: Jinzhen Lin
- **时间**: 2026-10-07T18:04:43Z
- **提交信息**: [Bugfix][Quantization] Accept folded NVFP4 scales for Humming A16 (#60337)

Signed-off-by: jinzhen.ljz <jinzhen.ljz@antgroup.com>
Co-authored-by: Kevin H. Luu <khluu000@gmail.com>

### [6ee9be6](https://github.com/vllm-project/vllm/commit/6ee9be6b3c2dd5557ad72cf714b9d8fe3c2009d4)

- **作者**: Giancarlo Delfin
- **时间**: 2026-10-07T18:01:59Z
- **提交信息**: [Spec Decode] Rename AR speculators to StandaloneAR / TargetDependentAR (#60335)

Signed-off-by: Giancarlo Delfin <gdelfin@inferact.ai>

### [fba462e](https://github.com/vllm-project/vllm/commit/fba462e008f0faa16745d1539c339db692d41f13)

- **作者**: Eduardo Fonseca
- **时间**: 2026-10-07T18:01:21Z
- **提交信息**: [Bugfix]Fix FlashInfer warmup crash: autotune(tuning_buckets=...) must round M up, not down (Invalid MXFP8 split-K tactic with spec-decode) (#58165)

Signed-off-by: Yongye Zhu <zyy1102000@gmail.com>
Co-authored-by: Yongye Zhu <zyy1102000@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [554340f](https://github.com/vllm-project/vllm/commit/554340f3d3259e321be4c07282be7a02a5aeef83)

- **作者**: SeongJun Lee
- **时间**: 2026-10-07T17:24:21Z
- **提交信息**: [Attention] Support NVFP4 KV cache on SM8x and SM12x with FlashInfer (#46963)

Signed-off-by: lesj0610 <lesj0610@users.noreply.github.com>
Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: lesj0610 <lesj0610@users.noreply.github.com>
Co-authored-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [3d6853b](https://github.com/vllm-project/vllm/commit/3d6853b32c7c872df00d9e3489f642dc22e974e0)

- **作者**: pondzikk
- **时间**: 2026-10-07T17:09:50Z
- **提交信息**: [Bugfix] Seed hybrid mamba state index with mamba_block_size on prefix-cache hits (#55601)

Signed-off-by: pondzikk <pondzik@gmail.com>
Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: ptorsten <1652174+ptorsten@users.noreply.github.com>

### [a8260cb](https://github.com/vllm-project/vllm/commit/a8260cbc5c020d250b3964141cde8fd839152714)

- **作者**: Harry Mellor
- **时间**: 2026-10-07T17:01:41Z
- **提交信息**: [CI] Bump Transformers version to 5.19.0 (#60381)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [d64a188](https://github.com/vllm-project/vllm/commit/d64a18832bcb97816f3ee88d7594457c2f50d224)

- **作者**: Daniel Chan
- **时间**: 2026-10-07T16:49:59Z
- **提交信息**: [ROCm][Triton] Migrating MiniMax-M3 kernels from make_block_ptr to tensor descriptors (#59285)

Signed-off-by: jpvillam <juan.villamizar@amd.com>
Signed-off-by: Daniel <danichan@amd.com>
Co-authored-by: jpvillam <juan.villamizar@amd.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: Rohan Potdar <rohan.potdar@amd.com>
Co-authored-by: Daniel <danichan@amd.com>

### [240ee8d](https://github.com/vllm-project/vllm/commit/240ee8de9eb98d4e9269b82054df121adf522c17)

- **作者**: MohitAMD
- **时间**: 2026-10-07T16:33:30Z
- **提交信息**: [Bugfix][KV Connector][ROCm] Fix MoRI-IO KV block-offset for speculative decoding (MTP) (#55053)

Signed-off-by: Mohit Deopujari <Mohit.Deopujari@amd.com>
Signed-off-by: MohitAMD <mohit.deopujari@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [c741bfc](https://github.com/vllm-project/vllm/commit/c741bfca70cfb777e2016f827eae31f6e215fe9f)

- **作者**: Andy Lo
- **时间**: 2026-10-07T16:05:29Z
- **提交信息**: [Docs] Add review areas for andylolu2 (#60416)

Signed-off-by: Andy Lo <andy@mistral.ai>

### [f7f62d1](https://github.com/vllm-project/vllm/commit/f7f62d19160010bdc84b31af407bb8b88e5392d6)

- **作者**: pmanczak
- **时间**: 2026-10-07T16:02:13Z
- **提交信息**: [XPU][MoE] Tune Triton fused MoE for Intel XPU (#53065)

### [9367d8b](https://github.com/vllm-project/vllm/commit/9367d8b9693c3d2fb6c3f99d8ccb4aa7673c0981)

- **作者**: xaguilar-amd
- **时间**: 2026-10-07T15:22:32Z
- **提交信息**: [Bugfix][MLA] Scope DSpark non-causal capability to builder layers (#57992)

Signed-off-by: Xavier Aguilar <xavier.aguilarfruto@amd.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [71f9a74](https://github.com/vllm-project/vllm/commit/71f9a749203c31a263ccad03395623b1d6fc5538)

- **作者**: stefankoncarevic
- **时间**: 2026-10-07T14:57:52Z
- **提交信息**: [CI][ROCm] Re-enable the DSv4.1 decoder replay graph test on ROCm (#60392)

Signed-off-by: Stefan Koncarevic <Stefan.Koncarevic@amd.com>

### [14e3902](https://github.com/vllm-project/vllm/commit/14e3902d5136e2fb00ef86c05fdc8d098f736283)

- **作者**: Alec
- **时间**: 2026-10-07T14:46:44Z
- **提交信息**: [Frontend][Rust] Add gRPC forbidden token sequences and cache usage (#59837)

Signed-off-by: Alec Flowers <aflowers@nvidia.com>

### [5485973](https://github.com/vllm-project/vllm/commit/548597367e66dcc90e24576c08e0e25f88c9ee6c)

- **作者**: Mikko Tukiainen
- **时间**: 2026-10-07T14:44:22Z
- **提交信息**: [ROCm][Perf] Add AITER FlyDSL GDN prefill backend (#57560)

Signed-off-by: Mikko Tukiainen <Mikko.Tukiainen@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [f6e3944](https://github.com/vllm-project/vllm/commit/f6e3944e3100fcb526e5cc24248080c31812be0f)

- **作者**: Micah Williamson
- **时间**: 2026-10-07T14:35:53Z
- **提交信息**: [ROCm][DSv4] AITER MegaMoEV2 Integration For DeepSeek V4 (#59685)

Signed-off-by: Micah Williamson <micah.williamson@amd.com>
Co-authored-by: Fangzhou Ai <31551580+Fangzhou-Ai@users.noreply.github.com>

### [c83935b](https://github.com/vllm-project/vllm/commit/c83935b3008553c72b1bad09f842b4c99b7fa47f)

- **作者**: viktorkou
- **时间**: 2026-10-07T14:04:35Z
- **提交信息**: [Bugfix][Model Loader] Support reload_weights with runai_streamer load format (#58124)

Signed-off-by: Viktor Koukouliev <vkoukouliev@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>

### [5281e49](https://github.com/vllm-project/vllm/commit/5281e49908960f490c8faa789eee221d4ab5001d)

- **作者**: 00CC
- **时间**: 2026-10-07T13:21:43Z
- **提交信息**: [ROCm][Perf] Enable medium-skinny dispatch in RDNAHybridW4A16LinearKernel (#52619)

Signed-off-by: tangzzycc <3081129260@qq.com>

### [efb8d85](https://github.com/vllm-project/vllm/commit/efb8d85f24bd270bf20c143b32b5e7db6df61716)

- **作者**: Divakar Verma
- **时间**: 2026-10-07T13:19:22Z
- **提交信息**: [ROCm][CI] Add FP32 rounding slack to accuracy test near-tie upper bounds (#60292)

Signed-off-by: Divakar Verma <divakar.verma@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [2a54f6b](https://github.com/vllm-project/vllm/commit/2a54f6b625f28109180b072b704c0b0d372a277d)

- **作者**: Jin Tao
- **时间**: 2026-10-07T12:53:40Z
- **提交信息**: [ROCm][Perf][GLM-5.3-Flash] Enable AITER fused shared experts on gfx950 (#59221)

Signed-off-by: Jin Tao <jin.tao@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Simon Danielsson <70206058+simondanielsson@users.noreply.github.com>

### [d9503dc](https://github.com/vllm-project/vllm/commit/d9503dc503e75193d2128908b59c0d141d4b5fb1)

- **作者**: SeongJun Lee
- **时间**: 2026-10-07T12:24:40Z
- **提交信息**: [Bugfix][Qwen4Exp] Derive the QSA head_dim from the unsharded head count (#59945)

Signed-off-by: lesj0610 <lesj0610@godoiksan.org>
Co-authored-by: lesj0610 <lesj0610@godoiksan.org>
Co-authored-by: Thien Tran <gau.nernst@yahoo.com.sg>

### [3ca00a8](https://github.com/vllm-project/vllm/commit/3ca00a8261c7790ba7487e2001ab9004ad8065f2)

- **作者**: stefankoncarevic
- **时间**: 2026-10-07T10:22:31Z
- **提交信息**: [CI] Skip EmbeddingGemma2 pooling tests needing transformers >= 5.19.0 (#60371)

Signed-off-by: Stefan Koncarevic <stefan.koncarevic@amd.com>

### [6b75dfb](https://github.com/vllm-project/vllm/commit/6b75dfb8a101dcf23c9e2b9e627433c61030cbcf)

- **作者**: SeongJun Lee
- **时间**: 2026-10-07T09:53:17Z
- **提交信息**: [Misc] Report a missing DeepSelect extension only when it is requested (#60242)

Signed-off-by: lesj0610 <lesj0610@gmail.com>

### [02d8a94](https://github.com/vllm-project/vllm/commit/02d8a94e610f515449d3bc3f44c592e3022e19d8)

- **作者**: Kevin H. Luu
- **时间**: 2026-10-07T09:38:31Z
- **提交信息**: [CI][ROCm] Skip DSv4.1 decoder replay graph test on ROCm (#60378)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [df417f7](https://github.com/vllm-project/vllm/commit/df417f780a19b68cebc4379942de6ea0e6f6aceb)

- **作者**: Hexiang Wang
- **时间**: 2026-10-07T08:35:56Z
- **提交信息**: [Bugfix][MoRIIO] Exclude synchronous READ destinations from KV zeroing (#59164)

Signed-off-by: Yichao Zhu <Yichao.Zhu@amd.com>
Signed-off-by: whx-sjtu <xiaowang990929@gmail.com>
Signed-off-by: Hexiang Wang <56632993+whx-sjtu@users.noreply.github.com>
Co-authored-by: Yichao Zhu <Yichao.Zhu@amd.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Yifan Qiao <yifanqiao@inferact.ai>

### [42ecc8e](https://github.com/vllm-project/vllm/commit/42ecc8eebe701faf07e7d6f33dbf5a8218825b5b)

- **作者**: aoshen02
- **时间**: 2026-10-07T08:29:09Z
- **提交信息**: [CI][RL] Consolidate RL entrypoint tests under tests/entrypoints/rl (#59948)

Signed-off-by: wang.yuqi <yuqi.wang@daocloud.io>
Signed-off-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: wang.yuqi <yuqi.wang@daocloud.io>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [bc8dd4a](https://github.com/vllm-project/vllm/commit/bc8dd4ad275c838d6315389432b2010d9348c900)

- **作者**: Bugen Zhao
- **时间**: 2026-10-07T08:28:27Z
- **提交信息**: [Rust Frontend] Share `SchemaRoot` between argument coercion and grammars (#59408)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [90f4936](https://github.com/vllm-project/vllm/commit/90f4936d9ee05f6108a401a3acc5c5631f5835f7)

- **作者**: stefankoncarevic
- **时间**: 2026-10-07T08:21:47Z
- **提交信息**: [CI/Build] Widen the ragged prefill scoring tolerance, drop batch invariance (#60192)

Signed-off-by: Stefan Koncarevic <Stefan.Koncarevic@amd.com>

### [7436a7f](https://github.com/vllm-project/vllm/commit/7436a7f119dedd0c4d5f4d745aa6c2305ee82252)

- **作者**: Bugen Zhao
- **时间**: 2026-10-07T07:45:15Z
- **提交信息**: [Rust Frontend] Backtrack from safe text at a complete marker (#59563)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [e6fc81b](https://github.com/vllm-project/vllm/commit/e6fc81bc7892f2f58c0e347a701fc060ceef44bb)

- **作者**: Tommy
- **时间**: 2026-10-07T07:32:00Z
- **提交信息**: [Bugfix][Scheduler] Let pooling chunked prefill use full context (#48039)

Signed-off-by: Tommy <tran.tommy@hotmail.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-10-08
**监控日期**: 2026-10-07
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7068
- **最后更新**: 2026-10-08T00:50:59Z

## 提交统计

- **昨日提交总数**: 12
- **提交者数量**: 10
- **主要提交者**: haic0, Alex Brooks, NumberWan

## AI分析总结

## vllm-omni 昨日提交分析（12 commits）

### 1. 主要更新类型
- **功能新增 / 新模型支持**：新增 Qwen-Image-2.1 图像生成模型；引入序列并行（SP）内存优化特性
- **硬件与平台扩展**：Intel XPU 部署 overlay、华为 NPU 升级至 v0.31.0、AMD ROCm 平台选择稳定化
- **Bug 修复**：修复 sender 地址传播、realtime 转轮自动截断、Qwen3Omni embeddings 在 TP>1 时的原地编译覆盖问题
- **性能优化**：Klein TP 避免重复 attention/MLP 计算、将 generation payload 的 host 等待延迟到输出消费阶段
- **CI/构建修复**：分布式 VAE 测试 mock 中的 CPU 分组、ROCm 平台选择稳定性

### 2. 关键变更点与项目方向的关系
vllm-omni 的目标是"为所有人提供简单、快速、廉价的全模态模型服务"。昨日提交集中体现在三个方向：
- **多硬件普惠**：同时在 Intel XPU、Huawei NPU、AMD ROCm 三条异构硬件链路上推进，降低全模态服务的部署门槛，直接呼应"easy and cheap"的定位
- **全模态能力扩展**：新增 Qwen-Image-2.1 支持，与已有 Qwen3Omni 等模型形成更完整的文本+语音+图像全模态矩阵
- **服务稳定性与效率**：多处 bugfix 针对 realtime（实时对话）场景和多卡 TP 并行场景，这是全模态服务中最复杂、最易出问题的路径

### 3. 对项目的影响与潜在意义
- **市场覆盖扩大**：XPU/NPU/ROCm 同步推进意味着 vllm-omni 正在脱离对单一 GPU 生态的依赖，可服务国产芯片与数据中心多平台用户
- **实时服务可靠性提升**：realtime 截断修复和 sender 地址修复直接改善了实时语音/全模态对话的正确性，这是产品级部署的关键指标
- **资源成本下降**：SP 内存优化与 TP 重复计算消除可显著降低推理内存占用与算力浪费，契合"cheap"的核心卖点
- **多模态内容生成能力补齐**：图像生成模型的加入使 vllm-omni 从"全模态理解+语音生成"走向"全模态生成"，能力边界进一步拓宽

### 4. 值得关注的技术点
- **Qwen3Omni TP>1 下的原地编译覆盖修复**：这是一个隐蔽的并发/编译陷阱，体现了多卡推理场景下编译器与运行时状态管理的复杂性，修复后对大规模部署意义重大
- **SP（序列并行）内存优化**：由 NVIDIA 工程师贡献，说明主流推理厂商开始在 vllm-omni 这一层做内存优化，而非仅在 vllm 核心层
- **延迟 host 等待至输出消费**：通过异步化解耦 CPU/GPU 同步点，是推理服务性能调优的经典且有效的手段
- **分布式 VAE 测试 mock 修复**：看似是 CI 细节，实则反映出项目对多模态（VAE）分布式测试覆盖的重视

### 5. 对项目发展的整体影响
昨日提交呈现出明显的"横向铺开 + 纵向打磨"并进的节奏。横向铺开体现在硬件平台、新模型类型的同步推进，使 vllm-omni 在全模态服务赛道的生态位更加独特；纵向打磨体现在对实时场景、多卡并行、内存效率等核心链路的持续修复与优化。两者结合，说明项目正从"功能可用"阶段迈向"生产可用"阶段，为后续吸引更多企业级用户和贡献者奠定了基础。短期内最值得关注的是 Intel XPU 支持的成熟度和 Qwen-Image-2.1 在 vllm-omni 上的实际推理表现，这两项将直接影响项目在异构硬件和图像生成两个方向上的竞争力。

## 详细提交记录

### [c32a26a](https://github.com/vllm-project/vllm-omni/commit/c32a26a8450b553d60436d211fa4f67fca31bf52)

- **作者**: Joshna-Medisetty
- **时间**: 2026-10-07T22:19:07Z
- **提交信息**: Add XPU deploy overlays and mark Intel GPU support (#8409)

Signed-off-by: Joshna Medisetty <joshna.medisetty@intel.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Chendi.Xue <chendi.xue@intel.com>

### [8484d85](https://github.com/vllm-project/vllm-omni/commit/8484d85d1f78bf9e9002af879d0a47849957cadf)

- **作者**: Alex Brooks
- **时间**: 2026-10-07T21:04:01Z
- **提交信息**: [Bugfix] Fix Sender Address Propagation (#8599)

Signed-off-by: Alex Brooks <albrooks@redhat.com>

### [744c202](https://github.com/vllm-project/vllm-omni/commit/744c202d860bf9c7c04b736279aabd80c419ccad)

- **作者**: Nick Cao
- **时间**: 2026-10-07T19:57:09Z
- **提交信息**: [BugFix] Optimize turn-based /v1/realtime auto truncation (#8566)

Signed-off-by: Nick Cao <ncao@redhat.com>
Co-authored-by: Codex <noreply@openai.com>

### [f3743eb](https://github.com/vllm-project/vllm-omni/commit/f3743ebdb62fa0842ce27d244878b61d7815d134)

- **作者**: Alex Brooks
- **时间**: 2026-10-07T17:01:45Z
- **提交信息**: [Bugfix] Fix In Place Compile Overwrites for Qwen3Omni Embeddings with TP > 1 (#8532)

Signed-off-by: Alex Brooks <albrooks@redhat.com>

### [3345fb7](https://github.com/vllm-project/vllm-omni/commit/3345fb7498c9844797ae9e2faca3331f93d482bc)

- **作者**: amy-why-3459
- **时间**: 2026-10-07T16:24:15Z
- **提交信息**: [CI/Build] Fix CPU groups in distributed VAE test mocks (#8591)

### [32ead8e](https://github.com/vllm-project/vllm-omni/commit/32ead8e5c8930d4f4f48e74c72d26dc8c9abb88b)

- **作者**: Weiming Liao
- **时间**: 2026-10-07T15:35:09Z
- **提交信息**: [NPU] upgrade to v0.31.0 (#8588)

Signed-off-by: Weiming Liao <liaowm5@gmail.com>

### [c8e69c0](https://github.com/vllm-project/vllm-omni/commit/c8e69c08fbf7a28af74bf3e1d4b3e008b49b3d79)

- **作者**: haic0
- **时间**: 2026-10-07T15:03:03Z
- **提交信息**: [CI/Build][ROCm] Stabilize R2-01 platform selection (#8561)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>
Signed-off-by: andyluo7 <andy.luo@amd.com>
Co-authored-by: andyluo7 <andy.luo@amd.com>

### [e54e185](https://github.com/vllm-project/vllm-omni/commit/e54e185593ff84bb532fe8ca166147e142ae1f43)

- **作者**: MaciejBalaNV
- **时间**: 2026-10-07T14:36:32Z
- **提交信息**: [feature] Reduce memory usage with SP (#7728)

Signed-off-by: Maciej Bala <mbala@nvidia.com>

### [3dc3569](https://github.com/vllm-project/vllm-omni/commit/3dc35694b3d458fc1461a8fe71832ac12e8c8cea)

- **作者**: NumberWan
- **时间**: 2026-10-07T13:23:59Z
- **提交信息**: [New model] Qwen-Image-2.1 support (rebase + review follow-ups) (#8099)

Signed-off-by: NumberWan <wantszkin2003@gmail.com>
Signed-off-by: SamitHuang <285365963@qq.com>
Signed-off-by: Samit <285365963@qq.com>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: Tianyu Guo <guoty9@mail2.sysu.edu.cn>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: SamitHuang <285365963@qq.com>
Co-authored-by: Gao Han <hgaoaf@connect.ust.hk>

### [8ef77be](https://github.com/vllm-project/vllm-omni/commit/8ef77be66ea3d95582ad37b68fb5c7c421bb7d5f)

- **作者**: QianCyrus
- **时间**: 2026-10-07T13:21:05Z
- **提交信息**: [Model] Avoid repeated attention and MLP work in Klein TP (#8553)

Signed-off-by: QianCyrus <101633534+QianCyrus@users.noreply.github.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [b21df3b](https://github.com/vllm-project/vllm-omni/commit/b21df3bcb6761dcb5f6489ccfa9c65dd1a6a1c0f)

- **作者**: NATURE
- **时间**: 2026-10-07T10:49:34Z
- **提交信息**: [Frontend] Share regular and duplex chat initialization (#7646)

Signed-off-by: natureofnature <wzliu@connect.hku.hk>

### [de25341](https://github.com/vllm-project/vllm-omni/commit/de253412b0f3afea7a705c1d1ad5e346e0f95c36)

- **作者**: amy-why-3459
- **时间**: 2026-10-07T09:20:54Z
- **提交信息**: [Core] Defer generation payload host waits to output consumption (#8540)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

---
