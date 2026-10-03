# GitHub Stars 合并报告 - 2026-10-02

**合并日期**: 2026-10-03
**监控日期**: 2026-10-02
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


**报告日期**: 2026-10-03
**监控日期**: 2026-10-02
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2231
- **最后更新**: 2026-10-02T12:23:04Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-10-03
**监控日期**: 2026-10-02
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2871
- **最后更新**: 2026-10-02T17:14:47Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-10-03
**监控日期**: 2026-10-02
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2279
- **最后更新**: 2026-10-02T21:29:28Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-10-03
**监控日期**: 2026-10-02
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6534
- **最后更新**: 2026-10-02T23:16:57Z

## 提交统计

- **昨日提交总数**: 23
- **提交者数量**: 8
- **主要提交者**: Vincent, eigen, Bo Li

## AI分析总结

# FlashInfer 昨日提交合并分析（23 个提交）

## 一、主要更新类型

- **性能优化**：占绝对主导。涵盖 MoE（MegaMoE、BGMV MoE）、DSA 稀疏注意力、KV 缓存融合算子、KDA 解码、SM100 cake FP4 GEMM 的 stream-K 尾部切分、GB10 SM 感知规划器及 Cake 采样多轮优化。
- **功能新增**：SM90 BF16 MegaMoE 后端、Rubin MXFP4/MXFP8 MoE、CuTe DSL NVFP4 W4A16 MoE、SM120/121 NVFP4 稀疏 MLA prefill 支持、SM107 Rubin DSA 训练与 MoE 激活函数扩展、DSA indexer 精确 top-k、BF16 QK 融合算子、MoE 可移植回退路径。
- **重构**：MoE 专家并行（EP）通信接口统一，纳入 NVLink one-sided 与 two-sided 多后端。
- **Bug 修复与文档**：`backend="auto"` 低效探测消除、采样内核逐行 seed/offset 修复、SM12x cuTile MLA NaN 修复、MoE 内核流同步修复、弃用警告版本指向，以及 sparse-MLA 参数文档补充。

## 二、关键变更点与项目方向

FlashInfer 正以两条主线推进：一是 **MoE 全链路深水区建设**，从 SM90 原生 BF16 端到端路径到 Rubin MXFP4/MXFP8、SM120/121 NVFP4 W4A16（与 W4A4 共享权重布局、可按 token 数动态选择量化方案），形成"统一 MoE API + 按场景自动选核"的架构；二是 **从推理走向训练**，DSA 训练内核支持 GLM-5.2 风格打包布局、Rubin 生成程序与单遍 key 优化，为预训练/后训练提供底层支撑。

CAKE 团队深度介入生成式内核路线，成为项目第二增长曲线。SM107 Rubin 的视频稀疏注意力、量化、DSv4 稀疏 MLA 与 MoE 内核均已真正可用；EP 通信接口统一后，服务框架可用一套 dispatch/combine API 部署 NCCL/NIXL/NVLink 多种方案。MoE 回退策略兼顾鲁棒性：默认降级并告警，`fallback=False` 保持 fail-closed，且修复了内核硬编码 stream 0 导致 CUDA Graph 捕获静默失效、输出全零的隐患。MLA 自动调度在 SM12x 上以实测数据偏好 FA2/XQA 路径，体现"按实测做架构决策"的成熟框架。

## 三、对项目的影响与潜在意义

- **性能与硬件覆盖**：多条内核声称超越 SOTA 基线，SM90/SM100/SM103/SM107/SM120/SM121 六代架构均有落地，保障 B200、GB200、GB300、Rubin 上的前瞻性；GB10 geomean 从 1.430x 提升至 1.462x。
- **生态整合**：MoE、KV 缓存、RoPE、稀疏注意力均提供单 launch 融合版本，降低 launch 开销，利好 vLLM/SGLang 等引擎集成；权重布局共享避免 decode 场景二次内存开销。
- **生产化与工程规范**：规划器决策抽离为纯 Python 规则并以字节一致 manifest 校验；弃用窗口纪律严格；文档检查驱动的 docstring 规范化逐步推进。

## 四、值得关注的技术点

- **确定性与位级可复现**：BGMV MoE、DSA 训练内核、stream-K 尾部分片均强调 bitwise-reproducible，用确定性归约与生成标志轮转替代原子操作，无竞态且可 A/B 验证。
- **测量方法论**：采用 CUDA graph、冷 L2、CUPTI 图模式中位数与 AB+BA 交错测量，数据公开可复现。
- **上游同步模式**：MoE 内核以注释标注与类名别名保留差异，实现与 TensorRT-LLM 上游的"drop-in"同步，是维护多方 kernel 的良好实践。

## 五、总结

这些提交显著强化了 FlashInfer 在大模型推理内核领域的技术领先性：量化格式多元化（BF16/FP8/FP4/NVFP4）、跨代硬件全栈覆盖、推理与训练双向延伸，使其从 kernel 库向"可组合的推理系统层"演进，进一步巩固作为下一代大模型推理基础设施的地位。

## 详细提交记录

### [4634068](https://github.com/flashinfer-ai/flashinfer/commit/46340689a5ab5665ab39f6281dac4d021d7ae94b)

- **作者**: eigen
- **时间**: 2026-10-02T23:16:51Z
- **提交信息**: feat(cake_mega_moe): SM90 native BF16 MegaMoE expert compute through MoEEpLayer (sm90_bf16_bf16_bf16_push_cake) (#5958)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

## SM90: native BF16 MegaMoE expert compute through `MoEEpLayer`
(`sm90_bf16_bf16_bf16_push_cake`)

Closes #5708 (part of #4254).

### What
A Hopper mega backend that runs the whole expert-parallel MoE round in
native BF16: bf16 dispatch payload on the SM90 push protocol,
expert-major bf16 compaction, generated WGMMA expert-grouped GEMMs (FC1
with fused SwiGLU and optional clamp, FC2) with fp32 accumulation and a
bf16 intermediate, bf16 combine wire with fp32 route weighting, bf16
output. No FP8 anywhere in the path.

Selected with
```python
MegaConfig(
    megakernel=Sm90_Bf16_Bf16_Bf16_PushCake_MegaMoeConfig(intermediate_size=I, top_k=K, capacity_factor=1.0, dedup_dispatch=True, clamp_limit=None),
    quantize_input=True, preprocess_weights=True,
)
```
Supported: `hidden % 256 == 0`, `intermediate % 128 == 0`, `top_k ∈
{1,2,4,6,8}`, `num_experts % world_size == 0`, one node, world ≤ 32;
everything else raises `MoEEpConfigError` at construction.

Two protocol kernels keep the vendored wire format bit-identically while
cutting the launch count per round from 15 to 10: a fused combine tail
(wait for every source, fp32 top-k reduce, ack; no per-round
combine-inbox fill) and a fused small-T dispatch (count, reserve and
store_publish in one cooperative launch for dedup rounds with `T ≤ 128`,
`T·top_k ≤ 1024`). Both are toggleable for A/B checks
(`FLASHINFER_SM90_CAKE_BF16_FUSED_TAIL=0`,
`FLASHINFER_SM90_CAKE_BF16_FUSED_DISPATCH=0`); a peer rank may run
either setting.

### Files
-
`flashinfer/moe_ep/backends/mega/kernel/sm90/bf16_bf16_bf16_push_cake/`
— config, backend, staging/weight validation (`cake_*.py`).
- `flashinfer/moe_ep/kernel_src/sm90/cake_bf16_megamoe/` —
`src/cake_compact_bf16.cu`, `src/cake_combine_tail_bf16.cu`,
`src/cake_dispatch_fused_bf16.cu`, generated GEMM sources + tvm-ffi
bindings sealed by `cake_sm90_bf16_megamoe_manifest.json`, Python shim
(`shim/cake_{jit,gemm,weights,runner}.py`; the JIT loader re-hashes
every unit before building, `use_fast_math=False`). The development
launcher that builds the GEMMs from the generator is outside this
repository; `FLASHINFER_SM90_CAKE_BF16_DEV_LAUNCHER=<module[:factory]>`
selects it for the parity test.
- `tests/moe_ep/test_sm90_bf16_push_cake_frozen_sources.py` (CPU seal
guard), `tests/moe_ep/test_sm90_bf16_push_cake_backend.py` (EP1 +
torchrun EP≥2 against an independent bf16 torch reference at
`atol=rtol=1e-2`), `tests/moe_ep/_sm90_bf16_reference.py`,
`run_tests.sh` section `sm90_bf16_push_cake`.
- `benchmarks/bench_moe_ep_sm90_bf16_mega.py` (paired CUPTI A/B against
the same-precision split route), docs (architecture table, runbook).

### Correctness (H100 SXM ×2 / ×4, torchrun)
- Backend tests: EP1 13/13, EP2 14/14 — uniform, skewed-remote,
hot-expert, empty-rank, masked (`-1` slots, incl. all-masked tokens),
duplicate-rank, token-boundary and uneven-T routing; repeated calls
bitwise equal; CUDA-graph capture + replay equal to eager;
frozen-sources guard 9/9; exported modules bit-identical to the
generator's in-process build on both layers (parity test).
- Independent-reference matrix (harness, every rank checked, 3
consecutive calls/replays compared bitwise): EP2 and EP4 at T ∈ {8, 128}
× 9 routing modes × eager + graph: 0 mismatches at `atol=rtol=1e-2` on
every row; T ∈ {1024, 4096} uniform rows likewise 0 mismatches.
- Fused protocol kernels vs the vendored kernels: output bitwise equal
on all routing cases at EP1 and EP2, dedup on and off.
- `compute-sanitizer` synccheck + memcheck on the grouped GEMMs: 0
errors (negative control flagged under both tools).

### Performance (H100 SXM, CUPTI spans with cold L2 over dispatch + FC1
+ FC2 + combine, same-process paired ABBA blocks, max-rank medians; B1 =
`SplitConfig(nccl_ep + CUTLASS BF16 fused MoE)` through the same
`MoEEpLayer`, autotuned, fastest numerically valid transport per row: LL
rank-major at T ≤ 128, high-throughput at T ≥ 1024)

Geometry A = hidden 7168 / intermediate 2048 / 256 experts / top-8, T =
tokens per rank; ratio = this backend / B1 (lower is better).

| EP | T | eager (s1 / s2) | graph (s1 / s2) |
|---|---|---|---|
| 2 | 8 | 0.871 / 0.868 | 0.990 / 0.985 |
| 2 | 128 | 0.885 / 0.882 | 0.931 / 0.928 |
| 2 | 1024 | 0.821 / 0.819 | 0.842 / 0.843 |
| 2 | 4096 | 0.886 / 0.902 | 0.870 / 0.893 |
| 4 | 8 | 0.852 / 0.814 | 0.996 / 0.956 |
| 4 | 128 | 0.807 / 0.805 | 0.881 / 0.878 |
| 4 | 1024 | 0.646 / 0.648 | 0.681 / 0.683 |
| 4 | 4096 | 0.683 / 0.693 | 0.691 / 0.691 |

Absolute EP2 graph times (ms, session 1): T=8 1.673 vs 1.690; T=128
3.892 vs 4.180; T=1024 4.490 vs 5.336; T=4096 7.469 vs 8.586. The decode
GEMMs of both routes run at the HBM ceiling (weights stream at ~3.0
TB/s), so the T=8 graph rows are decided by protocol overhead (≈87
µs/round here vs ≈64 µs for NCCL-EP LL + CUTLASS prep); the prefill
GEMMs run at 0.99-1.05× cuBLAS dense on the same node. Absolute EP4
graph times (ms, session 1): T=8 1.380 vs 1.386; T=128 2.054 vs 2.330
(HT; LL rank-major is numerically invalid there); T=1024 2.806 vs 4.123;
T=4096 7.024 vs 10.164. Informational T=8192 row (EP2, both arms ran,
max_tokens_per_rank = 8192): 0.819 eager / 0.803 graph (13.40 vs 16.36
ms, 13.34 vs 16.62 ms). EP8 rows: see the three tables below. FP8 push
arms were measured for information only (≈0.6× of these times at ≈52 %
of elements outside BF16 tolerance).

EP8 (8 × H100, one node per session: session 1 seed 0, session 2 seed 1
on a different node; same protocol, B1 = fastest numerically valid split
arm, LL rank-major at T ≤ 32 and high-throughput from T = 64 where LL
rank-major produces 7-17 % wrong elements). Ratio = this backend / B1
(graph; eager in parentheses), session 1 / session 2.

| T | A = 7168/2048/256/top-8 | B = 7168/3072/384/top-6 | C =
4096/2048/256/top-6 |
|---|---|---|---|
| 8 | 0.902 / 0.907 (0.741 / 0.751) | 0.915 / 0.906 (0.816 / 0.802) |
0.908 / 0.983 (0.668 / 0.699) |
| 16 | 0.243 / 0.241 (0.233 / 0.231) † | 0.852 / 0.864 (0.778 / 0.791) |
0.850 / 0.857 (0.649 / 0.650) |
| 32 | 0.714 / 0.715 (0.621 / 0.622) | 0.263 † / 0.802 (0.258 † / 0.741)
| 0.753 / 0.745 (0.591 / 0.589) |
| 64 | 0.722 / 0.727 (0.665 / 0.653) | 0.874 / 0.855 (0.823 / 0.813) |
0.728 / 0.689 (0.588 / 0.584) |
| 128 | 0.735 / 0.716 (0.683 / 0.671) | 0.756 / 0.769 (0.725 / 0.729) |
0.679 / 0.674 (0.567 / 0.560) |
| 512 | 0.656 / 0.646 (0.624 / 0.618) | 0.689 / 0.706 (0.638 / 0.641) |
0.641 / 0.626 (0.493 / 0.553) |
| 1024 | 0.582 / 0.567 (0.556 / 0.541) | 0.560 / 0.536 (0.538 / 0.516) |
0.569 / 0.556 (0.484 / 0.479) |
| 2048 | 0.528 / 0.535 (0.521 / 0.526) | 0.450 / 0.485 (0.441 / 0.476) |
0.478 / 0.482 (0.455 / 0.458) |
| 4096 | 0.529 / 0.530 (0.530 / 0.531) | 0.429 / 0.429 (0.417 / 0.419) |
0.507 / 0.503 (0.503 / 0.501) |

Absolute EP8 graph times (ms, session 1, B1 vs this backend): A 1.075 vs
0.970 (T=8), 1.552 vs 1.141 (T=128), 3.881 vs 2.257 (T=1024), 13.374 vs
7.073 (T=4096); B 1.922 vs 1.758, 3.066 vs 2.319, 5.323 vs 2.979, 17.564
vs 7.531; C 0.649 vs 0.589, 1.011 vs 0.687, 1.931 vs 1.099, 6.471 vs
3.283. Informational A T=8192 (both arms ran): 0.530 / 0.525 graph (26.4
vs 14.0 ms). Every EP8 cell is below 1.0 in both sessions; the only cell
inside ±3 % is C T=8 graph in session 2 (0.983; 0.908 in session 1). † =
baseline-autotune anomaly: on those cells the CUTLASS autotuner of the
B1 arm picked a tactic that runs the split path at 4.2-8.8 ms (vs
1.3-2.7 ms on the neighbouring T buckets and, for B T=32, on the other
node), so the ratio is not representative of a well-tuned baseline;
re-measuring those cells with the neighbouring bucket's tactic forced on
the B1 arm (informational, session-1 node) gives 0.862 / 0.806 graph and
0.716 / 0.678 eager for A T=16 (tactics (43,101) / (40,102)) and 0.804
graph / 0.745 eager for B T=32 (tactic (40,104)). The autotuned numbers
are kept as the B1 rows.

Baseline note: at the base commit the stock
`FusedMoeKernelConfig(CutlassBf16Config)` cannot run expert-parallel on
H100 (no BF16 CUTLASS weight branch; `supports_expert_parallelism =
False`), so B1 is a test-registered split-kernel wrapper over the same
`fused_moe_90` CUTLASS kernel and the same `nccl_ep` transports. NCCL-EP
LL rank-major produced wrong tokens at T ≥ 1024 (EP2) and at EP4 T=128,
LL expert-major runs out of memory at T=4096; those rows use the
high-throughput transport.

### Test plan
```
bash tests/moe_ep/run_tests.sh sm90_bf16_push_cake
python -m torch.distributed.run --nproc_per_node=2 benchmarks/bench_moe_ep_sm90_bf16_mega.py --geometry A --tokens 8,128,1024,4096
```

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added a native BF16 MegaMoE backend for SM90 Hopper GPUs, with
expert-weight preparation and support for routing, dispatch
deduplication, and optional clamping.
* Added a benchmark to compare the backend with BF16 split baselines,
including eager and CUDA-graph timings, CSV results, and optional output
checks.
* Added a correctness test target and documented backend configuration,
supported geometry, and benchmark usage.
* **Bug Fixes**
* Expanded source-integrity exclusions to cover the new sealed BF16 GEMM
sources while retaining existing exclusions.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [4af32c0](https://github.com/flashinfer-ai/flashinfer/commit/4af32c083c1af82d0fef65d318c05b05b3bb8122)

- **作者**: Ka-Hyun Nam
- **时间**: 2026-10-02T23:14:23Z
- **提交信息**: perf(kda): stop probing Cake for explicit T=1 cu_seqlens decode under "auto" (#5760)

<!-- .github/PULL_REQUEST_TEMPLATE.md -->

## 📌 Description

`backend="cake"` refuses explicit T=1 `cu_seqlens` decode outright — it
raises in `run_recurrent_kda` before the selector runs. `backend="auto"`
did not. Because `auto_unbounded_softplus_candidate` never tested
`cu_seqlens`, `auto` probed the Cake selector on every such call and,
whenever the selector agreed, **quietly served the contract the explicit
backend rejects**. This PR aligns the candidate with that guard.

The probe is not free in either outcome. The selector is a ~257-line
pure-Python predicate chain costing **~17 µs when it rejects** and **~69
µs when it accepts** (of which ~48 µs, or 70%, is `_tensors_overlap` —
21 calls producing 42 `_tensor_byte_range` calls). Against a decode
whose entire host path is 11–25 µs, probing cost up to **1.4x the work
it was deciding about**.

Which outcome you get is not intuitive:

- **rejects** when `num_accepted_tokens` falls through to the 1-element
dummy (`dc["i32_1"]`) and N > 1, since the selector wants one entry per
sequence;
- **accepts** at N = 1, where that check is trivially satisfied (`1 ==
1`);
- **accepts at every N** when the caller supplies a per-sequence
`num_accepted_tokens`, which is a public parameter of
`run_recurrent_kda`.

So this is not a case of removing an impossible route — the route
worked. It is removing one that `backend="cake"` already declines, and
that costs more to decide on than to perform.

Worth stating plainly because the intuitive reading is wrong: **the Cake
schedule is not the problem.** With selection stubbed to a constant,
Cake *beats* CuTe on this contract — 1.37x at N=1, and 1.49x/1.39x at
N=8/64 in the explicit-`num_accepted_tokens` variant. What this PR
removes is the cost of deciding, not a slow kernel.

### Measurements (B200, H=16, K=V=128, explicit `cu_seqlens`, µs/call)

| N | before: auto | before: cute | delta | after ratio |
|---|---|---|---|---|
| 1 | 88.06 | 24.54 | +63.5 | 1.00 |
| 2 | 43.53 | 24.48 | +19.1 | 1.00 |
| 8 | 30.19 | 11.69 | +18.5 | 1.01 |
| 16 | 30.76 | 11.97 | +18.8 | 1.01 |
| 64 | 30.54 | 13.64 | +16.9 | 1.01 |
| 128 | 30.15 | 25.20 | +5.0 | 1.00 |
| 256 | 68.28 | 68.23 | +0.05 | 1.00 |

For N = 2…64 the delta is near-constant at 16.9–19.1 µs, and
selector-plus-kwargs measures 17.8 µs — 94–105% of it, flipping sign
across N, so no second mechanism hides in the residual. The delta then
decays to nothing: profiled device time grows from 2.4 µs (N=1) through
13.8 (N=64) and 26.0 (N=128) to 69.2 µs (N=256), so this is host-bound
**only up to about N=64** and fully hidden behind the device by N=256.
`set_sync_debug_mode("error")` confirms no host-device sync; cProfile
shows only `stride`, `numel`, `data_ptr` and `element_size`.

Numerics are bitwise identical wherever the probe was already rejecting.
Where it was accepting, the route changes from Cake to CuTe and results
move by 1–2 bf16 ulps (max *relative* difference 0.4–1.3% on a handful
of elements out of ~10⁶; absolute state `max|diff|` 1.2e-7…3.9e-3
depending on seed, and up to 1.6e-2 at N=512 in the
explicit-`num_accepted_tokens` variant). Both results are valid, and
`auto` already documents that returned state follows whichever backend
ran.

### What this PR does not fix

1. **The same pathology remains on the dense (no-`cu_seqlens`) Cake
route**, which is deliberately left alone here. The ~69 µs accept cost
is paid there too, so `auto` is slower than `cute-dsl` below a crossover
of roughly N≈24 with `ssm_state_indices` and N≈200 without, winning only
once device work dominates (1.87x at B=128, 4.03x at B=256). That is a
bigger problem than this PR fixes and needs its own change; note that
cheapening `_tensors_overlap` alone would not close it, since ~31 µs of
non-selector host cost (view synthesis plus launch) remains.
2. **Two more candidate-says-yes-but-selector-always-rejects cases**, of
exactly the same shape as this one: the candidate never tests
`use_qk_l2norm_in_kernel` or `initial_state_source`, while the selector
rejects both unconditionally and `backend="cake"` raises on both. The
former costs 1.67x vs `cute-dsl`. Left out to keep this diff to one
line; each deserves its own measurement.
3. **A narrow regression.** With an explicit per-sequence
`num_accepted_tokens`, Cake is ~26% faster at N ≥ 512 (105.6 vs 133.8 µs
at N=512), and this PR forfeits that, costing ~21% there. In the same
configuration Cake is 1.34–8.0x slower for N ≤ 256 — again the selector,
not the schedule — so the trade nets out clearly positive, but it is a
trade.
4. **It leaves ~25% on the table at N=1**, since Cake is the faster
schedule there; the ideal is cheap selection *plus* Cake (~18.9 µs)
rather than the ~23.8 µs here. Still a strict improvement on main's 88
µs.

## 🔍 Related Issues

Surfaced while migrating downstream callers off the deprecated
`flashinfer.kda_decode.recurrent_kda` facade (#5248). SGLang's KDA
decode matches this contract exactly. vLLM is unaffected: its
eligibility check requires `lower_bound is not None`, which disqualifies
the Cake path.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] **Dependencies installed**: `pip install pre-commit && pre-commit
install`
- [x] **Checks pass**: `pre-commit run` (mypy, ruff check, ruff format
all pass)

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests passing: **437 passed, 5 skipped** across
`tests/kda/test_recurrent_kda_decode_export.py`,
`tests/kda/test_recurrent_kda.py`,
`tests/kda/test_cake_fused_kda_decode_dispatch.py`,
`tests/kda/test_kda_output_only.py`.


`test_t1_unbounded_softplus_auto_falls_back_to_cute_with_explicit_cu_seqlens`
already pinned the *numerical* fallback and passed throughout, because
it asserts on the executor (`_run_flash_kda_decode`) rather than the
selector. It now also asserts the selector is never consulted, and is
parametrised over `num_sequences=1` and over an explicit per-sequence
`num_accepted_tokens` — the two configurations in which the probe
actually *accepted*, neither of which was previously covered. Reverting
the kernel change fails all 12 parametrisations, splitting between
`frozen_calls` (Cake genuinely ran) and `select_calls` (probe consulted,
then rejected), so both outcomes are pinned.

## Reviewer Notes

The one-line predicate change is the whole fix; the rest is test. The
docstring on that test previously claimed this contract was "unservable
by Cake for any input", which was inaccurate at N=1 and with an explicit
`num_accepted_tokens`; it now describes consistency with the
`backend="cake"` guard.

One alternative considered and rejected: testing the real disqualifier
(`num_accepted_tokens.numel() != num_sequences`) instead of
`cu_seqlens`. That does not fire when the caller supplies `[N]`, so a
disqualifier-shaped candidate would leave `auto` serving a contract
`cake` refuses — and 3.8x slower than CuTe at N=1. Mirroring the guard
is the correct predicate.

All figures are from isolated per-process runs with a build-identity
guard, after earlier rounds of numbers proved contaminated by harness
state and by GPU contention.

### [9178cf0](https://github.com/flashinfer-ai/flashinfer/commit/9178cf06a97fedb4544ef5bb0bd57a4562458450)

- **作者**: eigen
- **时间**: 2026-10-02T22:45:59Z
- **提交信息**: perf(cake_dsa): single-pass key ranges for packed multi-segment rows, GB200-trace bench rows and fused varlen index glue for the native 64-head DSA sparse-attention kernels (#5657) (#5865)

## Summary

Stacked on #5737 (CAKE-756 layout extension, same fork): until #5737
merges this diff also shows its commits; the round-2 commits are the
last nine (`08809c3c8` … `d9a799ded`).

Round 2 of the native 64-query-head DSA sparse-attention kernels
(`flashinfer.experimental.cake_dsa_train`, #5704 / #5737), driven by a
GB200 GLM-5.2 trainer trace (job 102784, rank 0) — stacked on #5737
(CAKE-756), which must merge first.

- **Packed multi-segment rows take one key pass**
(`KeyPassPolicy.passes(..., num_segments)`, `plan_key_passes(...,
num_segments=)`, `dsa_train_workspace_size(..., num_segments=)`): the
backward's whole-row key-range passes (which split the key row into
ranges and compact each token's indices per range) only pay off when a
token's keys can be anywhere in the row. In a packed batch every token's
keys are confined to its own segment, so for a 4k-token recompute chunk
of a 268k-key batch the old planner ran six passes of which three or
four were empty for every token (Q / dO reloads, fp32 dQ partial round
trips, compaction for nothing). `dsa_sparse_attention_varlen` passes
`len(cu_seqlens_k) - 1` as `num_segments`; the flat entry defaults to
one segment (unchanged behaviour); `key_passes=` still overrides.
Results are bitwise identical for `out` / `lse` / `dq`; `dkv` differs
only by fp32 summation order (same gates).
- **Row lengths derived by default**: when the caller passes no
`topk_length`, the public entries derive it (last valid slot + 1 per
row; `derive_topk_length`) instead of running the full-row kernel path
over `-1` tails — the Cake facade already did this; results identical to
the explicit full-length call for `out` / `lse` / `dq` (bitwise) and
within the fp32 reduction spread for `dkv`.
- **Varlen index glue in int32 and fused with the length derivation**
(`offset_gather_kv_indices(..., return_topk_length=True)`): the `[T,
topk]` passes stay int32 / bool (int64 temporaries tripled the traffic),
two compares + one `where`, the per-row lengths from the same validity
mask; `~12` launches instead of `~27`. No device synchronisation.
- **`bwd_cast` skips all-zero accumulator groups in the
packed-accumulate mode** (regenerated programs): a recompute chunk
references only the key rows of its own segments, the other rows' fp32
accumulators are zero and their read-modify-write into the caller's
`dkv_acc` added exact zeros. Bitwise identical (the destination is never
`-0.0`).
- **Bench rows from the trace** (`benchmarks/bench_cake_dsa_train.py`):
`packed_glm_a_dstmap` / `packed_glm_b_dstmap` (T 16231 / 16172, Tkv
268757 / 267520, the trainer's fp32 dKV destination map with 260611 /
259412 rows and 8146 / 8108 duplicated keys), their `s704` variants,
`chunk_4096x268757`, `chunk_3943x268757`, `chunk_3884x267520`.
- Regenerated programs for `sm_100a` / `sm_103a` / `sm_107a` from one
source revision (`csrc/cake_dsa_h64_train/`, one module table). Numerics
boundary unchanged: bf16 I/O, fp32 softmax statistics, fp32 `dQ` / `dKV`
accumulation, no bf16 atomics, no approximate math, no sampled /
truncated keys.

## Baselines and their source PRs / versions

- **A (hard gate)**: FlashMLA sparse forward (`ba89a34`) + cuDNN
frontend 1.30.0 `DSA.sparse_attention_backward_wrapper`, timed with the
`contiguous` / `cat` / `index_add_` glue those APIs need.
- **B (precision / memory reference, also compared row by row)**:
FlashAttention PR #2914 head `c9e2e5eb` (`flash_attn.cute` sparse MLA,
`recompute_p`, `token_chunk = 4096`).
- Test oracle: chunked fp64 reference on the same bf16 inputs
(`tests/experimental/test_cake_dsa_train.py`).

## Performance

Train step = forward + backward including the layout glue each arm
needs; median of >= 20 steps (13 at 128k), 3 alternating rounds, every
arm in its own process, bit-identical inputs, same GPU; CUPTI kernel
time alongside. Ratios > 1 mean this PR is faster. `recompute` = 2 x
forward + backward (activation recomputation). `peak / saved mem vs FA`
< 1 = less memory; no `P` tensor is kept.

### SM100 (B200) — final tree `ec1efb65c9c (kernel sources) /
f83a96a855e (export pin)`

Of the 32 rows, 17 are clock-flagged by the harness (the FlashMLA+cuDNN
arm ran at a 3-8 % higher loaded SM clock than this PR's arm; B200 power
capping) -- the ratios are reported uncorrected, so on those rows they
understate the speedup over A.

| row | T | Tkv | segs | this PR fwd / bwd / step ms | A
(FlashMLA+cuDNN) step / recompute ms | FA #2914 step / recompute ms |
A/this step (fwd/bwd) | A/this recompute | FA/this step (fwd/bwd) |
FA/this recompute | peak / saved mem vs FA |
|---|---:|---:|---:|---|---|---|---|---:|---|---:|---|
| packed_glm_a_dstmap | 16231 | 268757 | 8 | 3.897 / 18.554 / 22.443 |
27.531 / 35.145 | 31.577 / 36.921 | 1.227 (1.949/1.073) | 1.334 | 1.407
(1.367/1.414) | 1.402 | 0.718 / 0.828 |
| packed_glm_b_dstmap | 16172 | 267520 | 8 | 3.893 / 18.500 / 22.388 |
27.480 / 35.123 | 31.448 / 36.766 | 1.227 (1.957/1.074) | 1.337 | 1.405
(1.366/1.412) | 1.400 | 0.717 / 0.828 |
| packed_glm_a_s704_dstmap | 16231 | 268757 | 8 | 3.887 / 18.557 /
22.431 | 27.963 / 35.945 | 31.602 / 36.945 | 1.247 (2.051/1.076) | 1.366
| 1.409 (1.375/1.415) | 1.404 | 0.718 / 0.828 |
| packed_glm_b_s704_dstmap | 16172 | 267520 | 8 | 3.876 / 18.437 /
22.307 | 27.718 / 35.626 | 31.387 / 36.683 | 1.243 (2.037/1.073) | 1.360
| 1.407 (1.367/1.415) | 1.401 | 0.717 / 0.828 |
| chunk_4096x268757 | 4096 | 268757 | 9 | 0.893 / 3.975 / 4.870 | 7.311
/ 9.250 | 8.405 / 10.036 | 1.501 (2.169/1.352) | 1.605 | 1.726
(1.825/1.704) | 1.741 | 0.500 / 0.611 |
| chunk_3943x268757 | 3943 | 268757 | 8 | 1.053 / 5.002 / 6.054 | 8.229
/ 10.139 | 8.870 / 10.473 | 1.359 (1.814/1.263) | 1.427 | 1.465
(1.520/1.453) | 1.474 | 0.502 / 0.602 |
| chunk_3884x267520 | 3884 | 267520 | 8 | 1.048 / 4.968 / 6.022 | 8.177
/ 10.066 | 8.787 / 10.382 | 1.358 (1.804/1.266) | 1.424 | 1.459
(1.521/1.448) | 1.468 | 0.502 / 0.600 |
| packed_glm_a | 16231 | 268757 | 8 | 3.896 / 18.631 / 22.527 | 27.280 /
34.891 | 31.490 / 36.855 | 1.211 (1.948/1.056) | 1.320 | 1.398
(1.377/1.403) | 1.395 | 0.721 / 0.828 |
| packed_glm_b | 16172 | 267520 | 8 | 3.864 / 18.512 / 22.382 | 27.241 /
34.865 | 31.357 / 36.666 | 1.217 (1.970/1.062) | 1.329 | 1.401
(1.371/1.407) | 1.398 | 0.721 / 0.828 |
| packed_glm_a_s704 | 16231 | 268757 | 8 | 3.886 / 18.603 / 22.488 |
27.764 / 35.804 | 31.553 / 36.898 | 1.235 (2.055/1.064) | 1.358 | 1.403
(1.377/1.409) | 1.399 | 0.721 / 0.828 |
| tail_2123x67923 | 2123 | 67923 | 1 | 0.736 / 3.200 / 3.936 | 4.783 /
5.857 | 5.201 / 6.081 | 1.215 (1.462/1.159) | 1.254 | 1.321
(1.189/1.352) | 1.302 | 0.476 / 0.743 |
| doc_16231 | 16231 | 16231 | 1 | 4.423 / 19.288 / 23.737 | 27.458 /
35.221 | 28.551 / 33.439 | 1.157 (1.748/1.021) | 1.251 | 1.203
(1.108/1.226) | 1.188 | 0.732 / 0.934 |
| doc_4095 | 4095 | 4095 | 1 | 0.989 / 3.817 / 4.817 | 6.116 / 8.059 |
6.662 / 8.045 | 1.270 (1.964/1.093) | 1.388 | 1.383 (1.402/1.380) |
1.386 | 0.433 / 0.934 |
| doc_4097 | 4097 | 4097 | 1 | 0.989 / 3.820 / 4.818 | 6.120 / 8.064 |
6.823 / 8.213 | 1.270 (1.965/1.093) | 1.387 | 1.416 (1.404/1.422) |
1.412 | 0.432 / 0.934 |
| doc_4096 | 4096 | 4096 | 1 | 1.005 / 3.814 / 4.822 | 5.389 / 6.609 |
6.572 / 7.905 | 1.118 (1.212/1.092) | 1.134 | 1.363 (1.326/1.374) |
1.357 | 0.439 / 1.000 |
| doc_8192 | 8192 | 8192 | 1 | 2.119 / 9.004 / 11.134 | 11.983 / 14.454
| 13.846 / 16.364 | 1.076 (1.167/1.056) | 1.090 | 1.244 (1.187/1.263) |
1.234 | 0.608 / 1.000 |
| doc_16384 | 16384 | 16384 | 1 | 4.459 / 19.399 / 23.853 | 25.332 /
30.296 | 28.564 / 33.421 | 1.062 (1.113/1.050) | 1.070 | 1.198
(1.093/1.222) | 1.181 | 0.754 / 1.000 |
| doc_32768 | 32768 | 32768 | 1 | 9.295 / 41.653 / 50.926 | 53.661 /
63.819 | 59.711 / 69.317 | 1.054 (1.098/1.043) | 1.060 | 1.173
(1.033/1.203) | 1.151 | 0.857 / 1.000 |
| doc_65536 | 65536 | 65536 | 1 | 19.891 / 90.626 / 110.637 | 119.828 /
145.084 | 131.265 / 151.227 | 1.083 (1.272/1.046) | 1.112 | 1.186
(0.994/1.230) | 1.159 | 0.920 / 1.000 |
| doc_131072 | 131072 | 131072 | 1 | 40.262 / 208.598 / 249.092 |
264.912 / 316.163 | 301.428 / 342.111 | 1.064 (1.265/1.027) | 1.092 |
1.210 (1.011/1.250) | 1.181 | 0.954 / 1.000 |
| cptail_4k_65536 | 4096 | 65536 | 1 | 1.317 / 6.068 / 7.390 | 8.097 /
9.451 | 9.218 / 10.618 | 1.096 (1.030/1.111) | 1.081 | 1.247
(1.053/1.293) | 1.214 | 0.443 / 1.000 |
| cptail_4k_131072 | 4096 | 131072 | 1 | 1.457 / 6.949 / 8.423 | 9.420 /
10.872 | 10.551 / 12.090 | 1.118 (0.999/1.147) | 1.093 | 1.253
(1.073/1.301) | 1.216 | 0.447 / 1.000 |
| packed_N1 | 32768 | 262144 | 1 | 12.075 / 61.510 / 73.582 | 75.662 /
87.574 | 88.659 / 100.668 | 1.028 (0.988/1.036) | 1.022 | 1.205
(0.990/1.246) | 1.175 | 0.835 / 1.000 |
| packed_N2 | 32768 | 262144 | 2 | 10.927 / 59.169 / 70.029 | 72.175 /
83.150 | 83.462 / 94.591 | 1.031 (1.004/1.035) | 1.026 | 1.192
(1.010/1.223) | 1.167 | 0.835 / 1.000 |
| packed_N4 | 32768 | 262144 | 4 | 10.217 / 50.240 / 60.471 | 64.240 /
74.979 | 73.883 / 84.050 | 1.062 (1.053/1.064) | 1.061 | 1.222
(0.992/1.266) | 1.189 | 0.835 / 1.000 |
| packed_N8 | 32768 | 262144 | 8 | 9.693 / 43.873 / 53.585 | 56.777 /
67.168 | 61.898 / 71.710 | 1.060 (1.071/1.057) | 1.061 | 1.155
(1.015/1.189) | 1.133 | 0.835 / 1.000 |
| packed_N16 | 32768 | 262144 | 16 | 9.300 / 41.982 / 51.334 | 54.412 /
64.492 | 59.620 / 69.300 | 1.060 (1.085/1.056) | 1.064 | 1.161
(1.013/1.190) | 1.143 | 0.835 / 1.000 |
| packed_N32 | 32768 | 262144 | 32 | 9.280 / 41.854 / 51.196 | 54.361 /
64.438 | 59.231 / 68.846 | 1.062 (1.087/1.058) | 1.064 | 1.157
(1.021/1.185) | 1.136 | 0.835 / 1.000 |
| skewed8 | 32768 | 262144 | 8 | 9.891 / 48.428 / 58.295 | 61.662 /
72.204 | 69.394 / 79.421 | 1.058 (1.063/1.055) | 1.059 | 1.190
(1.011/1.224) | 1.165 | 0.835 / 1.000 |
| spread_32k_65536 | 32768 | 65536 | 1 | 10.086 / 46.833 / 56.940 |
60.452 / 71.086 | 68.812 / 79.049 | 1.062 (1.056/1.064) | 1.060 | 1.209
(0.998/1.253) | 1.179 | 0.854 / 1.000 |
| spread_32k_131072 | 32768 | 131072 | 1 | 10.741 / 58.435 / 69.196 |
71.203 / 82.095 | 82.638 / 93.600 | 1.029 (1.009/1.030) | 1.028 | 1.194
(1.015/1.227) | 1.172 | 0.847 / 1.000 |
| spread_32k_196608 | 32768 | 196608 | 1 | 11.579 / 60.799 / 72.386 |
74.194 / 85.620 | 86.733 / 98.372 | 1.025 (0.987/1.033) | 1.020 | 1.198
(0.997/1.236) | 1.172 | 0.841 / 1.000 |

### Varlen entry (this package's `dsa_sparse_attention_varlen`, B200,
regenerated programs, `benchmarks/bench_cake_dsa_train.py --rows ...
--arms cake --steps 5`)

| row | fwd ms | bwd ms | step ms | peak GiB |
|---|---|---|---|---|
| chunk_4096x268757 | 1.047 | 3.970 | 5.145 | 1.95 |
| packed_glm_a_dstmap | 4.400 | 18.043 | 23.421 | 4.36 |
| packed_glm_a_s704_dstmap | 4.250 | 18.536 | 23.321 | 4.36 |
| tail_2123x67923 | 0.939 | 3.299 | 4.219 | 1.02 |

The entry's index glue (segment-relative top-k -> global keys, per-row
lengths) is fused into two compares and one `where`; the remaining
gap to the Cake harness numbers above is launch-bound host glue (~0.15
ms on the chunk row, ~0.4 ms on the packed batch).

### Generated programs

The exporter regenerates the programs of all three architectures from
one source revision in a single run; only the backward
module changed in this round (one new kernel + binding pair per
architecture, the superseded pair removed, module table updated).
Export validation (exported program vs the production source, same
inputs, `min_source_over_export` 0.97, correctness on the
chunked fp64 oracle): sm_100a (B200, nsc-svg job 2113566, run
`export-20261001T105850Z`): 11/11 selected shapes passed, timed-correct
11, source/export geomean 0.9990 (coverage 0.9998, perf 0.9957),
FlashInfer tests on the regenerated checkout 95 passed, publication
guard passed. sm_103a (GB300, oci-jhb job 734747, run
`export-20261001T105745Z`): 11/11 passed, geomean 0.9992 (coverage
0.9996, perf 0.9976), FlashInfer tests 95 passed with the repo's
CuTe-DSL compat shim loaded first (`pytest -p
flashinfer.cute_dsl.sparse.sm100_blk64.quack_compat`); the stock run
fails one test in its *reference* path (`torch.index_add_` is routed by
torch 2.13 nv26.07's native-op router on GB300 into a CuTe-DSL
scatter_add whose vendored quack imports `cutlass.cute.core.ThrMma`,
absent from the CuTe DSL 4.7.1 overlay the FlashInfer source tree needs
on that container; the kernel under test is not involved). Both runs
produced byte-identical generated files (sha256 prefixes: cake_jit.py
6e22b081, sm_100a bbcc80f7 / 78fecd12, sm_103a 24d650c9 / c505d1f7,
sm_107a c4df09de / 599559d2).

### SM103 (GB300)

GB300 (oci-jhb job 734747, node nvl72d395-T14, same sources, tree
`f83a96a855e`; A and FA #2914 re-measured on the same GPU; 3 alternating
rounds, 20 steps / 13 at >= 128k keys; no clock-flagged rows):

| row | T | Tkv | segs | this PR fwd / bwd / step ms | A
(FlashMLA+cuDNN) step / recompute ms | FA #2914 step / recompute ms |
A/this step (fwd/bwd) | A/this recompute | FA/this step (fwd/bwd) |
FA/this recompute | peak / saved mem vs FA |
|---|---:|---:|---:|---|---|---|---|---:|---|---:|---|
| packed_glm_a_dstmap | 16231 | 268757 | 8 | 3.259 / 16.220 / 19.481 |
24.931 / 31.628 | 28.310 / 33.022 | 1.280 (2.055/1.124) | 1.391 | 1.453
(1.446/1.455) | 1.452 | 0.718 / 0.828 |
| packed_glm_b_dstmap | 16172 | 267520 | 8 | 3.243 / 16.131 / 19.374 |
24.802 / 31.473 | 28.189 / 32.887 | 1.280 (2.057/1.124) | 1.392 | 1.455
(1.449/1.456) | 1.454 | 0.717 / 0.828 |
| packed_glm_a_s704_dstmap | 16231 | 268757 | 8 | 3.269 / 16.234 /
19.503 | 25.255 / 32.274 | 28.314 / 33.029 | 1.295 (2.147/1.123) | 1.417
| 1.452 (1.443/1.454) | 1.450 | 0.718 / 0.828 |
| packed_glm_b_s704_dstmap | 16172 | 267520 | 8 | 3.247 / 16.146 /
19.396 | 25.128 / 32.123 | 28.185 / 32.885 | 1.296 (2.154/1.123) | 1.419
| 1.453 (1.447/1.455) | 1.452 | 0.717 / 0.828 |
| chunk_4096x268757 | 4096 | 268757 | 9 | 0.816 / 3.634 / 4.451 | 6.682
/ 8.390 | 7.706 / 9.186 | 1.501 (2.094/1.368) | 1.593 | 1.731
(1.813/1.713) | 1.744 | 0.500 / 0.611 |
| chunk_3943x268757 | 3943 | 268757 | 8 | 0.961 / 4.589 / 5.548 | 7.553
/ 9.230 | 8.140 / 9.582 | 1.361 (1.747/1.280) | 1.418 | 1.467
(1.501/1.460) | 1.472 | 0.502 / 0.602 |
| chunk_3884x267520 | 3884 | 267520 | 8 | 0.945 / 4.524 / 5.469 | 7.487
/ 9.146 | 8.051 / 9.479 | 1.369 (1.756/1.288) | 1.426 | 1.472
(1.511/1.464) | 1.478 | 0.502 / 0.600 |
| doc_4096 | 4096 | 4096 | 1 | 0.884 / 3.482 / 4.367 | 4.872 / 5.924 |
5.902 / 7.030 | 1.115 (1.191/1.097) | 1.128 | 1.351 (1.277/1.371) |
1.339 | 0.439 / 1.000 |

All 8 rows are faster than A and FA on both the train step and the
recompute step (minima: A/this step 1.115, A/this recompute 1.128,
FA/this step 1.351, FA/this recompute 1.339); peak / saved memory vs FA
<= 0.718 / 1.000. The remaining 24 rows were measured on GB300 in #5737
at the same source revision except for the two round-2 kernel changes
(host-side key-pass planning, all-zero-group skip in the dKV cast).

flashinfer-ci on this PR (pipeline 70965965, head `1cb4e3988`; the
generated programs and tests are unchanged in `d9a799ded`) also ran the
95 package tests on GB300 without any shim: `unit_test_gb300` cu129 /
cu130 / cu134 lanes 95 passed each (the B200, GB200 and R200 lanes of
the same pipeline passed 95/95 as well).

### SM107 (R200)

The sm_107a programs in this PR are the same generator output as the
sm_100a / sm_103a ones (the exporter regenerates all three architectures
in one run; the B200 and GB300 runs produced byte-identical files).
On-device test coverage: the flashinfer-ci `unit_test_vr200_cu134` lane
of pipeline 70899883 (R200 node, JIT arch 10.7a; pipeline of the
previous head `013f189cb`, generated programs unchanged since) ran this
PR's test file: 95 passed, 0 failed, 0 skipped. The
`unit_test_gb200_cu134` and `unit_test_b200_cu134` lanes of the same
pipeline also passed 95/95. What has not been run on R200 is the
exporter's source-vs-export timing gate (the 11-shape protocol run
reported above for B200 and GB300): the Rubin queue (`batch-xdr`) stayed
~750 higher-priority jobs deep for the whole round and the allocation
request was withdrawn after delivery. The round-2 kernel change is
host-side planning plus an all-zero-group skip in the dKV cast (bitwise
identical output); the sm_107a program family was validated on R200 in
#5737. The R200 export run can be added here before merge when a Rubin
node is available.

## Tests

```
pytest tests/experimental/test_cake_dsa_train.py
python benchmarks/bench_cake_dsa_train.py --rows chunk_4096x268757,packed_glm_a_dstmap --arms cake
```

Fresh-clone re-test of the Cake side (cold checkout, native build, CPU
tests 8, GPU e2e 49 passed / 2 skipped, bench-regression 3/3 above
floor) recorded in the Cake MR.

New / extended tests: key-pass policy rule and planner with
`num_segments`; varlen multi-segment row plans a single pass and matches
the flat call (bitwise `out` / `lse` / `dq`); public entry derives row
lengths and matches the explicit full-length call;
`offset_gather_kv_indices` causal table with fused lengths, a document
with more queries than keys, `out=`; bench helpers for the trace rows.
compute-sanitizer synccheck + memcheck: 0 errors (B200, final tree).
Repeat-run determinism: `out` / `lse` / `dq` bitwise, `dkv` run-to-run
spread recorded.

Tracker: #4642, #4254.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [ae783f9](https://github.com/flashinfer-ai/flashinfer/commit/ae783f9ffd19caf0eb01409bc73d44d213ff94ca)

- **作者**: eigen
- **时间**: 2026-10-02T22:42:34Z
- **提交信息**: feat(cake_dsa_indexer): fused DSA indexer scoring + deterministic exact top-k for training (SM100/SM103/SM107) (#5972)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

## Summary

Experimental fused DeepSeek-Sparse-Attention indexer for training stacks
(issue #5676): scoring of every visible key (`s = Σ_h w_h · ReLU(scale ·
q_h · k_j)` in FP32, documented reduction order) and the deterministic
exact top-k selection with aligned scores in one device-side pipeline.
Generated programs for SM100 (B200/GB200), SM103 (B300/GB300) and SM107
(Rubin) under `flashinfer/experimental/cake_dsa_indexer/`, public entry
points `flashinfer.dsa_indexer.dsa_indexer_topk` /
`dsa_indexer_topk_workspace_size`. JIT-only, not part of automatic
backend selection or autotuning.

Contract as in #5676: `q [T, 32, 128]` BF16, `k [Tkv, 128]` BF16 (a
row-strided `[Tkv, 704][:, :128]` view is read in place), `w [T, 32]`
FP32, `cu_seqlens_q/k`, optional `q_causal_offsets`, `top_k ≤ 4096`;
outputs `indices [T, top_k]` int32 ascending with `-1` padding and
aligned `scores` FP32 with `-inf` padding; exact global top-min(top_k,
visible) with ties ordered score-descending then id-descending, ±0 equal
with bits preserved; bitwise repeatable and independent of internal
tiling; no `[T, Tkv]` materialisation; explicit workspace bound; no host
synchronisation; non-finite inputs documented in the README.

## Performance (paired, same card, bit-identical inputs, cold-L2 CUPTI
span of the complete operator, AB + BA + interleaved medians)

Baselines: A = the trainer pipeline from the issue (chunked scoring →
coarse deterministic top-(k+256) → gather → FP32 re-score → sort → pad);
A2 = best existing exact composition (BF16 MMA / FP32-accumulate chunked
scores + `flashinfer.top_k` deterministic + ascending reorder with
aligned scores).

| row | T | Tkv | K | SM107 ms | A / this | A2 / this | SM100 ms | A /
this | A2 / this | SM103 ms | A / this | A2 / this |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| P1 | 16231 | 268757 | 2048 | 3.510 | 23.97x | 21.35x | 5.800 | 20.41x
| 19.60x | 5.434 | 20.49x | 19.80x |
| P1_strided | 16231 | 268757 | 2048 | 3.505 | 23.99x | 21.54x | 5.905 |
20.06x | 19.27x | 5.427 | 20.54x | 19.84x |
| P1_peaked | 16231 | 268757 | 2048 | 3.506 | 23.96x | 21.25x | 5.903 |
20.03x | 19.24x | 5.423 | 20.54x | 19.82x |
| P2 | 16172 | 267520 | 2048 | 3.294 | 23.45x | 21.20x | 5.888 | 17.85x
| 17.86x | 5.393 | 18.39x | 18.49x |
| P2_strided | 16172 | 267520 | 2048 | 3.302 | 23.41x | 21.24x | 5.891 |
17.87x | 17.86x | 5.413 | 18.37x | 18.43x |
| P3 | 16231 | 268757 | 4096 | 4.341 | 23.21x | 17.21x | 7.025 | 19.75x
| 16.26x | 6.814 | 19.19x | 15.85x |
| S1 | 8192 | 8192 | 2048 | 0.675 | 28.48x | 9.85x | 1.173 | 20.31x |
8.43x | 1.099 | 20.66x | 8.43x |
| S2 | 16384 | 16384 | 2048 | 1.693 | 24.51x | 12.55x | 3.025 | 17.11x |
10.37x | 2.783 | 17.72x | 10.72x |
| S3 | 32768 | 32768 | 2048 | 4.494 | 20.94x | 16.91x | 8.242 | 14.24x |
13.59x | 7.508 | 15.04x | 14.34x |
| S4 | 65536 | 65536 | 2048 | 13.190 | 18.01x | 17.41x | 23.775 | 12.22x
| 13.31x | 22.119 | 12.63x | 14.22x |
| S4_peaked | 65536 | 65536 | 2048 | 13.342 | 17.78x | 17.19x | 24.180 |
11.97x | 13.06x | 22.568 | 12.39x | 13.81x |
| S5 | 131072 | 131072 | 2048 | 42.786 | 14.97x | 20.48x | 79.215 |
10.11x | 15.72x | 72.079 | 10.58x | 16.96x |
| S6 | 262144 | 262144 | 2048 | 152.058 | 13.01x | 23.03x | 305.258 |
8.22x | 16.45x | 256.910 | 9.18x | 19.20x |
| S7 | 524288 | 524288 | 2048 | 616.152 | 10.99x | 21.24x | 1286.147 |
6.89x | 14.83x | 1012.906 | 7.99x | 17.97x |
| S8 | 1048576 | 1048576 | 2048 | 2736.272 | 9.21x | 18.50x | 5675.661 |
5.84x | 13.04x | 4409.072 | 6.87x | 15.93x |
| C1 | 4096 | 65536 | 2048 | 1.391 | 14.17x | 17.83x | 2.538 | 9.82x |
14.11x | 2.335 | 10.11x | 14.71x |
| C2 | 4096 | 131072 | 2048 | 2.462 | 12.48x | 20.09x | 4.568 | 8.45x |
15.66x | 4.134 | 8.90x | 16.58x |
| C3 | 16384 | 262144 | 2048 | 3.387 | 16.99x | 20.34x | 6.205 | 11.67x
| 16.57x | 5.526 | 12.54x | 17.62x |
| V1 | 65536 | 32768 | 2048 | 8.907 | 21.41x | 17.54x | 16.138 | 14.32x
| 13.80x | 14.927 | 15.04x | 14.43x |
| V2 | 65536 | 65536 | 256 | 13.293 | 10.84x | 16.72x | 22.494 | 7.53x |
13.69x | 21.119 | 7.95x | 14.46x |
| V3 | 65536 | 65536 | 4096 | 17.413 | 20.79x | 13.30x | 30.018 | 14.75x
| 10.80x | 28.848 | 14.72x | 11.18x |
| RC1 | 8192 | 131072 | 2048 | 4.796 | 12.58x | 20.24x | 8.760 | 8.69x |
16.02x | 8.100 | 8.92x | 16.61x |
| RC2 | 8192 | 262144 | 2048 | 9.132 | 11.49x | 21.81x | 16.541 | 8.02x
| 17.38x | 15.368 | 8.15x | 17.90x |
| RC3 | 8192 | 524288 | 2048 | 17.783 | 10.73x | 22.01x | 33.427 | 7.46x
| 17.08x | 30.263 | 7.57x | 17.98x |
| RC4 | 8192 | 1048576 | 2048 | 35.129 | 10.78x | 22.02x | 64.980 |
7.51x | 17.47x | 59.128 | 7.63x | 18.13x |

All 25 rows (incl. the strided-k rows) are faster than both baselines on
SM107, SM100 and SM103 (min A / this 9.21x / 5.84x / 6.87x at the 1M
row; min A2 / this 9.85x / 8.43x / 8.43x at the 8k row). Workspace 53
MiB on SM107 and 37–38 MiB on SM100/SM103 at top_k 2048 (double at
4096); no extra device memory. The issue's reference kernel (fp8,
SM100-only, no sort / scores) is reported separately in the README with
the ceiling attribution.

## Tests

`tests/experimental/test_cake_dsa_indexer.py` (independent FP64/FP32
reference in `tests/test_helpers/cake_dsa_indexer_reference.py`):
exact-semantics cases (cut-off ties, all-equal, mixed ±0 bit checks,
negative scores, large tie with few winners), packed causal (unequal
lengths, positive / negative offsets, ratio = 2, empty and singleton
segments, short rows, K = 1 / 4096), random-input precision bound,
near-ties, dynamic shapes and bitwise repeatability across tile
boundaries, non-finite inputs, CUDA-graph capture, workspace bound,
strided k. compute-sanitizer synccheck + memcheck: 0 errors on SM107,
SM100, SM103 (negative controls verified).

Generated-program parity (export protocol, every shape on every
architecture): the exported program and its source are launched into one
shared benchmark fixture under CUDA graphs (eight independently captured
graph instances per arm, three counterbalanced ABBA groups, 2 warmup +
40 reportable calls per arm and group; fewer reportable calls only for
the 0.25-5.7 s rows); outputs are checked structure-exact on every row
against an FP64/FP32 reference over every visible pair (exact ranking
rule, error bound, near-tie rule, bit-exact scores under the declared
zero-sign policy), and source and exported outputs are bitwise
identical. Timing parity is a measurement-validity check, not a
performance claim: source/export ratio >= 0.97, directional disagreement
between the two measurement orders <= 0.02, endpoint drift <= 0.02, SM
clock >= 0.85 of the device maximum with a steady-state requirement (no
absolute MHz floor: B200 sustains 1820-1880 MHz at its 1000 W TDP on the
heavier rows). Result per architecture (45 rows each, all retained from
one GPU per architecture):

- `sm_100a` (SM100, B200, cc 10.0): 45/45 protocol rows correct and
measurement-valid; source/export time ratio over the 45 rows: min
0.9961, median 1.0001, geomean 1.0000, max 1.0012.
- `sm_103a` (SM103, GB300, cc 10.3): 45/45 protocol rows correct and
measurement-valid; source/export time ratio over the 45 rows: min
0.9979, median 0.9999, geomean 0.9998, max 1.0003.
- `sm_107a` (SM107, Rubin, cc 10.7): 45/45 protocol rows correct and
measurement-valid; source/export time ratio over the 45 rows: min
0.9993, median 1.0000, geomean 1.0001, max 1.0022.


## Benchmark

`benchmarks/bench_cake_dsa_indexer.py` — the paired protocol above
against A and A2 for the representative rows (packed trainer call T =
16231 / Tkv = 268757 / 8 segments, causal single documents 8k … 1M, CP
tails, packed 8 × (2048 × 32768), ratio = 2, K = 256 / 4096).

## Known limitations

- `cake_jit.toolchain_supports()` is a static table of the nvcc
architecture flags the registry carries (SM100 / SM103 / SM107); it does
not probe the installed nvcc. A toolchain without `sm_107a` support
fails at JIT time with the nvcc error rather than at selection time.
- Experimental: not part of automatic backend selection or autotuning;
JIT-only; `max_seqlen_q/k` are accepted host mirrors (validated as
non-negative integers) that no launch decision reads.
- Non-finite inputs do not hang and keep the finite segments exact; the
order of NaN/infinite scores inside a row is documented in the README
rather than specified by the contract.

## Checklist
- [x] Pre-commit (ruff format / check with the pinned version) clean
- [x] Public-API docs:
`flashinfer/experimental/cake_dsa_indexer/README.md`
- [ ] CI: `/bot run` + `@flashinfer-bot run` posted after the final push

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added experimental DSA indexer top-k selection with configurable
scoring, visibility, output, and workspace options on supported NVIDIA
GPU architectures.
* **Documentation**
  * Added guidance on the feature’s inputs, outputs, and behavior.
* **Tests**
* Added coverage for accuracy, edge cases, repeatability, and workspace
handling.
* **Benchmarks**
* Added comparisons with reference approaches across multiple workloads.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [f2230d7](https://github.com/flashinfer-ai/flashinfer/commit/f2230d79f39c7f65de67db3647f5cfa2e6dbd1b6)

- **作者**: eigen
- **时间**: 2026-10-02T22:37:42Z
- **提交信息**: feat(cake_bgmv_moe): generic-shape Cake BGMV MoE bundles (hidden % 8 == 0, rank 8/16/32/64) and a token->pair route index for arbitrary pair order (#5850)

## Description

Follow-up to #4821 / #5727 (prepared Cake BGMV MoE backend,
SM90/SM100/SM103) and the fallback PR (`prepare_bgmv_moe(...,
fallback=True)`): the generated Cake programs now cover **any hidden
size that is a positive multiple of 8 at LoRA rank 8, 16, 32 or 64**,
instead of only hidden 2688/3072 at rank 32.

- **Generic-shape bundles**
`csrc/cake_bgmv_moe/cake_bgmv_moe_generic_{bf16,f16}_r{8,16,32,64}.cu`
(generated; one body per dtype × rank serves sm_90a, sm_100a and
sm_103a):
- shrink: one CTA per (pair, 8 rank rows) streams 1024-wide cp.async
tiles over a **runtime `hidden`** with a masked tail (hidden sizes that
are not multiples of 1024, e.g. 736, 1344, 2112, 2880, run without
padding); each lane keeps its 8 partial dot products in registers across
all tiles (one barrier per tile, one reduction at the end). At small
pair counts the hidden tiles are **split over extra CTAs** (grid z):
every split writes an FP32 partial, arrives on a per-tile counter and
the last arrival sums the partials in split order, so the result is
deterministic and the workspace is never reset
(`select_cake_bgmv_moe_generic_shrink` picks the split count; a 4-pair
decode kernel is still in the bundle but measured slower on every
small-pair row, so it is not selected);
- expand: deterministic token-owned accumulation (no output atomics,
bitwise-reproducible replays), rank-templated: each warp's lanes are
split `rank/8` ways along the rank so every 16-byte weight load is
coalesced across whole rows, each lane carries `rank/8` output columns
and the column sums are reduced across the rank lanes once at the end;
64 or 128 lanes per token. The contiguous top-k=2 layout takes the
direct two-route path, any other routing goes through the token→pair
route index below (no extra launch).
- **Token→pair route index (both variants).** Any pair order other than
contiguous top-k=2 (e.g. expert-sorted dispatch, the S4 rows) used to
make every token-owned expand CTA scan all `num_pairs` entries, which
cost 7–50× against the portable kernels at 1024–4096 tokens. The shrink
kernels now publish every routed pair that is not already in its
contiguous top-k=2 position under its token (one `atomicAdd` per such
pair into a plan-owned `int32` workspace, `plan.route_index`, 19 words
per token plus the shrink's hidden-split partials and counters; a
contiguous launch publishes nothing), the expand kernels read a token's
routes in O(1), merge the two implicit contiguous slots with the
published exceptions and restore ascending pair order with a rank sort
(so replays stay bitwise reproducible; tokens with more than 16
published routes take the exact serial scan). Counts are monotonic
across launches: each launch reads them against a per-parity base that
the expand records for the next launch, so nothing is reset and no
memset node is added to the captured graph. The specialized hidden
2688/3072 bundles are re-rendered with this prologue as well; each
bundle now also emits the dynamic shared-memory sizes its binding
launches with.
- **Routing.** `prepare_bgmv_moe` keeps the specialized measured bodies
for hidden 2688/3072 × rank 32 at up to 2048 tokens (`plan.variant ==
"specialized"`) and uses the generic bundle otherwise (`plan.variant ==
"generic"`), including those two hidden sizes above 2048 tokens where
the generic kernels are faster (GB300 shrink+expand 388 vs 449 µs
contiguous, 437 vs 495 µs expert-sorted at 4096 tokens); the portable
fallback is now only taken for multi-slice inputs and non-SM90/100/103
devices. `fallback=False` rejects ranks outside {8,16,32,64}, hidden % 8
!= 0 and multiple slices with explicit reasons.
- **JIT/AOT.** One module per (dtype, rank, arch):
`cake_bgmv_moe_generic_<bf16|f16>_r<rank>_<sm90a|sm100a|sm103a>`
(`gen_cake_bgmv_moe_generic_module`), registered in `flashinfer/aot.py`
next to the specialized modules; the binding fails closed on a
compute-capability mismatch and reads its launch shared-memory sizes
from constants the generator emits into each bundle.
- **Generator.** The bundles are rendered by the Cake exporter
(`tools/export_flashinfer_cake_bgmv_moe.py --flashinfer-source .
--check` in the Cake tree verifies the checked-in files against a fresh
render, clang-format 19.1.1 included); the generator change ships with
the Cake side of this work.

## Tests

**Head note.** The measurements and the per-GPU validation tables below
were taken at `dd2ab7c4d`. The branch has since been rebased onto `main`
(which now contains #5809) and gained one test-only commit
(`_require_cake_arch()` on the expert-sorted test), so CI's VR200
(SM107) and RTX PRO 6000 (SM120) runners skip the generated-program
tests instead of failing on the device check. The BGMV MoE sources,
bundles, tests and docs at the current head are identical to the
validated `db1d52f3`; the only differences versus `dd2ab7c4d` are in
`tests/moe/test_cake_bgmv_moe.py`. Re-validated on H100 (127 JIT + 66
GPU tests, and 8 passed / 58 skipped with the dispatcher seeing
capability (12,0) and (10,7)).


- `tests/jit/test_cake_bgmv_moe_jit.py`: variant routing table (incl.
the 2048-token crossover), generic schedule and shrink-split selectors,
workspace sizing, per-arch generic JIT spec (URIs, binding macros,
generated symbols, emitted shared-memory constants), URI disjointness,
binding contract (127 tests, CPU).
- `tests/moe/test_cake_bgmv_moe.py`: generic correctness + bitwise
replay ×3 over tail hidden sizes (736/1344/1472/1856/2112/2880/4096),
ranks 8/16/64, decode and prefill shrink, top-k 2/4/8 with interleaved
routing, top-k 20 (route-index overflow → serial scan), expert-sorted
dispatch order through both variants (hidden 3072/2688/2048/1344 at
4–4096 tokens, incl. the S4 shapes) with the rearmed index checked,
hidden-split shrink rows (hidden 4096–7168 at 4–16 tokens, 2–4 splits),
two-slice fallback, outer-graph capture of the generic plan,
specialized-preferred check (66 GPU tests). The reference's non-vacuous
guard (every active token must carry |out|max > 10× atol) rejects a
zeroed output without rejecting legitimate low-magnitude top-k=8 rows.

| GPU | JIT tests | GPU tests | `bench_cake_bgmv_moe.py` (specialized
rows, cake vs portable geomean) | pre-commit |
|---|---|---|---|---|
| H100 (SM90) | 127 passed | 66 passed | 1.325× | clean |
| B200 (SM100) | 127 passed | 66 passed | 1.410× | clean |
| GB300 (SM103) | 127 passed | 66 passed | 1.639× | clean |

## Performance (three-arm A/B, same protocol as #5727)

Arms: `portable_pre` = `60f0bc0f960f` (portable kernels before
#3535/#3542, i.e. `main` after #5764), `portable_post` = `2b8f80cd4eec`
(with #3535/#3542), `cake` = this branch (`fallback=False`, so every
cake row below is a generated Cake program). CUPTI cold-L2 median of
zero + shrink + expand, 2 interleaved reps, correctness at
atol=rtol=1e-2 and bitwise ×3 per row. 128 experts, top-k 2, 8 LoRAs.

### H100 80GB HBM3 (SM90)

`NVIDIA H100 80GB HBM3`, uuid `1535d44e-aaf9-aabd-59fd-287272ecc0a8`,
132 SMs, cake tree `dd2ab7c4d4aec40aca229fe28303f53ad0a961a3`.

Per set (2 interleaved reps, median of CUPTI medians per row; ratios are
portable/cake, i.e. cake speedup):

| set | rows | pre->post (post/pre) geomean | cake/pre geomean |
cake/pre min | cake/post geomean | cake/post min | rows cake<post |
|---|---|---|---|---|---|---|---|
| S1 | 28 | 1.490 | 1.987 | 1.558 | 1.333 | 1.154 | 0 |
| S2 | 5 | 1.745 | 3.851 | 2.065 | 2.206 | 1.158 | 0 |
| S3 | 84 | 1.596 | 2.621 | 1.370 | 1.642 | 1.081 | 0 |
| S4 | 4 | 1.457 | 1.972 | 1.763 | 1.353 | 1.094 | 0 |
| S5 | 16 | 1.847 | 3.932 | 1.712 | 2.129 | 1.246 | 0 |

Rows where cake is slower than portable_post:

_none_

Existing hidden 2688/3072 x rank 32 rows, cake time vs the #5727 kernels
(pre-route-index) under the same protocol: geomean 1.000, max 1.050,
rows > 1.02: 14/35 (per-row table in `GATE.md`/`SUMMARY_PR.md`, see
manifest).

S4 expert-sorted rows, before (#5727 kernels, serial scan) -> final
(route index):

| hidden | rank | tokens | pre us | post us | cake before us | cake
final us | cake/post before | cake/post final |
|---|---|---|---|---|---|---|---|---|
| 2688 | 32 | 1024 | 331.64 | 227.28 | 1299.89 | 166.73 | 0.175 | 1.363
|
| 3072 | 32 | 32 | 35.28 | 33.71 | 20.90 | 19.84 | 1.613 | 1.699 |
| 3072 | 32 | 1024 | 321.31 | 199.37 | 1424.49 | 182.24 | 0.140 | 1.094
|
| 3072 | 32 | 4096 | 1191.49 | 649.79 | 26658.70 | 491.69 | 0.024 |
1.322 |

### B200 (SM100)

`NVIDIA B200`, uuid `1cd6b054-20c4-9c7c-c085-c8071aa40ed1`, 148 SMs,
cake tree `dd2ab7c4d4aec40aca229fe28303f53ad0a961a3`.

Per set (2 interleaved reps, median of CUPTI medians per row; ratios are
portable/cake, i.e. cake speedup):

| set | rows | pre->post (post/pre) geomean | cake/pre geomean |
cake/pre min | cake/post geomean | cake/post min | rows cake<post |
|---|---|---|---|---|---|---|---|
| S1 | 28 | 1.596 | 2.280 | 1.755 | 1.428 | 1.163 | 0 |
| S2 | 5 | 1.720 | 3.123 | 2.002 | 1.816 | 1.172 | 0 |
| S3 | 84 | 1.766 | 2.800 | 1.654 | 1.585 | 1.047 | 0 |
| S4 | 4 | 1.619 | 2.253 | 2.118 | 1.391 | 1.137 | 0 |
| S5 | 16 | 1.926 | 3.554 | 1.955 | 1.846 | 1.172 | 0 |

Rows where cake is slower than portable_post:

_none_

Existing hidden 2688/3072 x rank 32 rows, cake time vs the #5727 kernels
(pre-route-index) under the same protocol: geomean 1.017, max 1.054,
rows > 1.02: 26/35 (per-row table in `GATE.md`/`SUMMARY_PR.md`, see
manifest).

S4 expert-sorted rows, before (#5727 kernels, serial scan) -> final
(route index):

| hidden | rank | tokens | pre us | post us | cake before us | cake
final us | cake/post before | cake/post final |
|---|---|---|---|---|---|---|---|---|
| 2688 | 32 | 1024 | 303.12 | 187.28 | 2190.58 | 129.06 | 0.085 | 1.451
|
| 3072 | 32 | 32 | 31.97 | 28.19 | 17.22 | 14.66 | 1.637 | 1.924 |
| 3072 | 32 | 1024 | 291.34 | 156.40 | 2412.49 | 137.57 | 0.065 | 1.137
|
| 3072 | 32 | 4096 | 1097.02 | 545.96 | 48760.92 | 462.14 | 0.011 |
1.181 |

### GB300 (SM103)

`NVIDIA GB300`, uuid `030ec1d4-f71b-1444-2e52-6d10dc9c1327`, 152 SMs,
cake tree `2e0493ff91f6f513ed0a42a9917ed3ad5098fb59`.

Per set (2 interleaved reps, median of CUPTI medians per row; ratios are
portable/cake, i.e. cake speedup):

| set | rows | pre->post (post/pre) geomean | cake/pre geomean |
cake/pre min | cake/post geomean | cake/post min | rows cake<post |
|---|---|---|---|---|---|---|---|
| S1 | 28 | 1.530 | 2.485 | 2.071 | 1.624 | 1.224 | 0 |
| S2 | 5 | 1.567 | 3.530 | 2.374 | 2.253 | 1.546 | 0 |
| S3 | 84 | 1.711 | 2.856 | 1.659 | 1.669 | 1.016 | 0 |
| S4 | 4 | 1.621 | 2.372 | 2.146 | 1.463 | 1.173 | 0 |
| S5 | 16 | 1.820 | 3.697 | 1.973 | 2.031 | 1.207 | 0 |

Rows where cake is slower than portable_post:

_none_

Existing hidden 2688/3072 x rank 32 rows, cake time vs the #5727 kernels
(pre-route-index) under the same protocol: geomean 1.005, max 1.050,
rows > 1.02: 21/35 (per-row table in `GATE.md`/`SUMMARY_PR.md`, see
manifest).

S4 expert-sorted rows, before (#5727 kernels, serial scan) -> final
(route index):

| hidden | rank | tokens | pre us | post us | cake before us | cake
final us | cake/post before | cake/post final |
|---|---|---|---|---|---|---|---|---|
| 2688 | 32 | 1024 | 283.30 | 176.58 | 2040.02 | 120.05 | 0.087 | 1.471
|
| 3072 | 32 | 32 | 37.02 | 31.44 | 16.66 | 14.00 | 1.888 | 2.246 |
| 3072 | 32 | 1024 | 274.59 | 150.05 | 2254.78 | 127.95 | 0.067 | 1.173
|
| 3072 | 32 | 4096 | 1019.17 | 510.02 | 45094.40 | 431.52 | 0.011 |
1.182 |

**Existing hidden 2688/3072 x rank 32 rows (specialized bodies, up to
1024 tokens).** These kernels are unchanged in this round apart from the
route-index prologue carried over from the previous revision; measured
end to end against the #5727 kernels under the same three-arm protocol
they are slower by a geomean of H100 80GB HBM3 +0.0 % (max +5.0 %, 14/35
rows above 2 %); B200 +1.7 % (max +5.4 %, 26/35 rows above 2 %); GB300
+0.5 % (max +5.0 %, 21/35 rows above 2 %). Per-kernel attribution
(CUPTI, route flags compiled off one at a time, register dumps) shows a
code-structure effect of the added expand code (register count 64->68 /
86->96, identical hot-path source), not executed route work. Stated
plainly: these rows do not meet a 2 % no-regression bar against #5727 on
Blackwell; every one of them is still at least 1.14x faster than
`portable_post` (S1 min columns above) and the dedicated benchmark
geomeans are at or above the #5727 numbers.

## Artifacts

Full per-row results (CUPTI medians per rep and arm, correctness and
bitwise flags, per-stage times, logs; 128 files per GPU) are archived on
the measurement clusters with a host/path/size/SHA-256 manifest per GPU;
the gate reports (`GATE.md`, `SUMMARY_PR.md`) carry the per-row tables
summarized above.

## Checklist

- [x] pre-commit clean on all changed files
- [x] GPU tests on H100, B200, GB300
- [x] Docs: `docs/api/fused_moe.rst` support-set paragraph;
`prepare_bgmv_moe` docstring
- [x] Tracker #4254 entry (`- #5850`)

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [37acd64](https://github.com/flashinfer-ai/flashinfer/commit/37acd64562cce3185c7867e066c37b30dc85776e)

- **作者**: eigen
- **时间**: 2026-10-02T22:37:21Z
- **提交信息**: docs(cake_dsv4_sparse_mla): add Parameters / Returns sections to the documented SM120 sparse-MLA functions (#5986)

## 📌 Description

Follow-up to #5959: the documentation check on that PR reported "Missing
'Parameters' / 'Args' section" for the seven
`flashinfer.mla.cake_sparse_mla_sm120_dsv4_nvfp4_*` functions it
documents (`decode`, `prefill`, `select_kernel`, `plan_prefill`,
`plan_head_tiles`, `plan_splits`, `scratch_bytes`). This adds
NumPy-style `Parameters` / `Returns` sections to those docstrings
(tensor shapes, dtypes and layouts as the functions validate them).
Docstrings only; no code change.

## 🔍 Related Issues

Tracker: #4254. Follows #5914 / #5949 / #5959.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues (ruff 0.12.8 format + check and mypy
1.17.1 with the `main` hook pins on the changed file;
`scripts/pr_checks/check_docstrings.py` and `check_api_docs.py` report
no finding for the module).

## 🧪 Tests

- [x] Tests have been added or updated as needed (none needed:
docstrings only).
- [x] All tests are passing (`unittest`, etc.) (no behaviour change; the
two SM120 test files are unchanged from #5959).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [a973cfc](https://github.com/flashinfer-ai/flashinfer/commit/a973cfc9245355ce4d036d51cba043c842d2fe1e)

- **作者**: eigen
- **时间**: 2026-10-02T22:14:10Z
- **提交信息**: feat(cake_fused_qk_rope_append): fused BF16 QK RMSNorm + NeoX RoPE + paged KV append for SM90 / SM100 / SM103 (#5952)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

Part of #4254. Closes #5368 (BF16 output / cache variant; the FP8 E4M3
variant is tracked in #5956).

## Cake fused BF16 QK RMSNorm + NeoX RoPE + paged KV append (SM90 /
SM100 / SM103)

Adds `flashinfer.cake_fused_qk_rmsnorm_rope_append_paged_kv_cache`
(re-exported from `flashinfer.rope`): one launch that
unpacks a packed BF16 `qkv [T, (Hq + 2 Hkv) * 128]`, applies optional
per-head FP32 RMSNorm (`qk_norm_policy` 0 none / 1
RoPE→norm / 2 norm→RoPE), NeoX RoPE from an FP32 `cos_sin [max_pos,
128]` table, writes BF16 `out_q [T, Hq, 128]`, appends K/V
into paged NHD BF16 caches through a dense `[B, max_pages]` page table
(or caller-owned `out_k`/`out_v`) and zeroes the unused
tail of each request's last page. `(Hq, Hkv)` in {(8, 1), (64, 8)};
sm_90a (H100/H200), sm_100a (B200), sm_103a (B300).

Generated sources:
`csrc/cake_fused_qk_rope_append/{sm_90a,sm_100a,sm_103a}/*` + manifest
(rendered by Cake
`loom.export.flashinfer_fused_qk_rope_append`, CAKE-892). JIT loader:
`flashinfer/jit/cake_fused_qk_rope_append.py`.

### Performance (graph-mode CUPTI medians, us;
`benchmarks/bench_cake_fused_qk_rope_append.py`)

| row | B200 cake / #5405 / stable 3-op | H200 cake / #5405 / stable |
H100 cake / #5405 / stable |
|---|---|---|---|
| M1 8/1 B32 decode | 2.85 / 5.33 / 11.98 | 2.42 / 4.43 / 12.30 | 2.59 /
4.69 / 12.59 |
| M2 8/1 B8 Q16 | 2.94 / 5.25 / 13.47 | 2.62 / 4.48 / 12.45 | 2.82 /
4.74 / 13.46 |
| H1 64/8 B32 decode | 3.97 / 6.34 / 18.51 | 4.54 / 5.54 / 17.15 | 5.14
/ 6.30 / 17.63 |
| H3 64/8 B128 decode | 8.51 / 10.56 / 21.82 | 11.07 / 12.05 / 20.59 |
14.18 / 16.77 / 21.06 |
| H4 64/8 B1 Q128 | 4.19 / 5.79 / 21.60 | 4.29 / 5.54 / 20.53 | 4.70 /
5.98 / 20.93 |
| D4 8/1 B256 decode | 4.35 / 6.59 / 12.77 | 4.42 / 6.21 / 13.46 | 4.96
/ 6.83 / 14.10 |
| E2 8/1 B32 page 128 | 3.33 / 5.62 / 11.87 | 2.77 / 5.06 / 12.06 | 2.83
/ 5.30 / 12.67 |

Under the Cake paired protocol (3 groups x 30 repeats) the kernel is
faster than the #5405 fused kernel on all 28 representative
rows on all three cards (lowest 95 % CI lower bound of the ratio 1.058
on B200). `#5405` is used only as the baseline here; the
interface is independent of it.

### Tests

`tests/attention/test_cake_fused_qk_rope_append.py` (21 tests:
decode/prefill x heads x policy x page size, cross-page appends,
ragged/empty/caller-owned, no-clear, B=300 lookup fallback, CUDA-graph
replay, argument validation) — passed on H100, H200 and B200.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [04935ca](https://github.com/flashinfer-ai/flashinfer/commit/04935caeba8bc17ca162eee0497858c192ecc715)

- **作者**: Akaash Parthasarathy
- **时间**: 2026-10-02T21:01:29Z
- **提交信息**: feat(moe_ep): support Rubin MXFP4 weights with MXFP8 activations (#5699)

<!-- .github/pull_request_template.md -->

## 📌 Description

Add a Rubin MegaMoE backend for MXFP4 weights and MXFP8 E4M3
activations, using the existing vendored kernel. It accepts canonical
prequantized weights without requantizing them and supports
floating-point weight preprocessing, SiTU, and BF16 output.

Wire the format into offline tuning and add layout, numerical, and
distributed correctness coverage, including K3 routed-expert geometry.

## 🔍 Related Issues

Builds on #5662, which is now merged.

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

The vendored kernel source is unchanged. This covers the routed-expert
operator; engine integration and full-model K3 qualification remain
follow-ups.

Portable checks, native Rubin single-GPU and EP2/EP4/EP8 correctness
tests, and a tuner smoke test pass.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added SM107 support for MXFP8 activations with MXFP4 weights,
including prequantized weight inputs.
* Added SiTU activation and configurable NVFP4 input normalization and
per-expert scaling.
* Expanded tuning and benchmarking options for the new quantization
format and activation settings.
* **Bug Fixes**
* Improved handling and validation of quantized weights, scaling values,
and activation settings.
* **Documentation**
* Updated SM107 usage, tuning, and qualification guidance for supported
formats and configuration options.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [b4abddb](https://github.com/flashinfer-ai/flashinfer/commit/b4abddb4e77202ccf5ef444fa98665322de058ae)

- **作者**: eigen
- **时间**: 2026-10-02T20:46:21Z
- **提交信息**: feat(cake_dsa): SM107 (Rubin) generated programs and strided / packed GLM-5.2 trainer layouts for the native 64-head DSA sparse-attention training kernels (#5675) (#5737)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

## Summary

Extends the native 64-query-head DSA sparse-attention training kernels
(`flashinfer.experimental.cake_dsa_train`, #5704) with:

- **SM107 (Rubin R200) generated programs** for the forward and backward
kernels (`csrc/cake_dsa_h64_train/sm_107a/`), regenerated
together with the SM100 and SM103 programs from the same source revision
(one module table for the three architectures).
- **Strided / packed trainer layouts** (GLM-5.2 style, #5675): `q_rope`
taken directly from the pre-absorb `q[T,64,256]` slice
(channels 192:256, head stride 256), `kv` rows read in place from packed
`[Tkv,576]` or `[Tkv,704]` buffers (latent `0:512` ‖
rope `512:576`, optional 128-channel indexer key), `dq` written into
caller views, and the backward's latent+rope `dK/dV`
accumulated straight into a caller-provided packed fp32 `[Tkv,576]`
buffer (`dkv_acc`) with an optional destination-row map
applied in the kernel epilogue — no `contiguous()` / `cat` /
`index_add_` copies.
- Separate `cu_seqlens_q` / `cu_seqlens_k` with an opt-in in-segment
causal rule (`causal=True` on the varlen entry: a slot that
selects a key after the query's own position `(seqlen_k - seqlen_q) +
local_q` is dropped; the default `causal=False` keeps the
first release's plain offsetting), `-1`-padded local key indices, empty
rows (`out = 0`, `lse = -inf`, zero gradients), arbitrary
`T` / `Tkv` / segment lengths (no padding, no dropped tokens, no
cross-segment reads).
- Backward recomputes `P` from `lse` in 4096-token chunks (no `P`
tensor), bf16 I/O, fp32 softmax statistics and fp32 `dK/dV`
accumulation. The existing #5704 entry points keep their signatures and
default behaviour; the new options are keyword-only
(`causal`, `dkv_acc`, `dkv_dst_map`). `dkv_dst_map` values are the
caller's invariant (the kernel does not range-check them);
  `FLASHINFER_CAKE_DSA_CHECK_DST_MAP=1` validates them on every call.

## Baselines and their source PRs / versions

- **A (hard gate)**: FlashMLA sparse forward (`ba89a34`) + cuDNN
frontend 1.30.0 `DSA.sparse_attention_backward_wrapper`, timed
with the `contiguous` / `cat` / `index_add_` glue those APIs need.
FlashMLA's SM100 kernels do not run on SM107 (the CUTLASS
TMA/TMEM arch macros are not enabled for `__CUDA_ARCH__` 1070); on SM107
the A backward is still compared through cuDNN.
- **B (precision / memory reference, also compared row by row)**:
FlashAttention PR #2914 head `c9e2e5eb` (`flash_attn.cute` sparse
  MLA, `recompute_p`, `token_chunk = 4096`).
- Test oracle: chunked fp64 reference on the same bf16 inputs
(`tests/experimental/test_cake_dsa_train.py`), as in #5704.

## Performance

Train step = forward + backward including the layout glue each arm
needs; CUPTI kernel time; median of >= 20 steps (13 at 128k),
3 alternating rounds, every arm in its own process, bit-identical
inputs, same GPU. Ratios > 1 mean this PR is faster. `peak / saved
mem vs FA` = peak allocated / saved-activation bytes of this PR divided
by FA #2914 (< 1 = less memory). No `P` tensor is kept.

### SM107 (Rubin R200, 212 SMs) — final (no clock-flagged rows, all arms
at 2412 MHz)

| row | T | Tkv | segs | this PR fwd / bwd / step ms | FA #2914 step ms
| cuDNN DSA bwd ms | FA/this step (fwd/bwd) | cuDNN bwd / this bwd |
peak / saved mem vs FA |
|---|---:|---:|---:|---|---:|---:|---|---:|---|
| packed_glm_a | 16231 | 268757 | 8 | 2.003 / 9.554 / 11.557 | 17.197 |
12.043 | 1.488 (1.621/1.460) | 1.260 | 0.721 / 0.828 |
| packed_glm_b | 16172 | 267520 | 8 | 1.993 / 9.497 / 11.491 | 17.111 |
11.980 | 1.489 (1.621/1.462) | 1.261 | 0.721 / 0.828 |
| packed_glm_a_s704 | 16231 | 268757 | 8 | 2.008 / 9.549 / 11.558 |
17.201 | 12.040 | 1.488 (1.617/1.461) | 1.261 | 0.721 / 0.828 |
| tail_2123x67923 | 2123 | 67923 | 1 | 0.403 / 1.882 / 2.285 | 2.965 |
2.329 | 1.298 (1.358/1.285) | 1.238 | 0.476 / 0.743 |
| doc_16231 | 16231 | 16231 | 1 | 2.173 / 10.019 / 12.192 | 14.013 |
11.133 | 1.149 (1.182/1.142) | 1.111 | 0.732 / 0.934 |
| doc_4095 | 4095 | 4095 | 1 | 0.491 / 2.148 / 2.640 | 3.469 | 2.480 |
1.314 (1.453/1.282) | 1.154 | 0.433 / 0.934 |
| doc_4097 | 4097 | 4097 | 1 | 0.495 / 2.151 / 2.646 | 3.592 | 2.484 |
1.357 (1.446/1.337) | 1.155 | 0.432 / 0.934 |
| doc_4096 | 4096 | 4096 | 1 | 0.489 / 2.151 / 2.645 | 3.476 | 2.487 |
1.314 (1.455/1.285) | 1.156 | 0.433 / 0.934 |
| doc_8192 | 8192 | 8192 | 1 | 1.054 / 4.816 / 5.870 | 7.052 | 5.402 |
1.201 (1.269/1.187) | 1.122 | 0.596 / 0.935 |
| doc_16384 | 16384 | 16384 | 1 | 2.195 / 10.126 / 12.321 | 14.183 |
11.251 | 1.151 (1.180/1.145) | 1.111 | 0.733 / 0.934 |
| doc_32768 | 32768 | 32768 | 1 | 4.448 / 20.816 / 25.264 | 28.692 |
23.165 | 1.136 (1.148/1.133) | 1.113 | 0.830 / 0.934 |
| doc_65536 | 65536 | 65536 | 1 | 9.217 / 44.031 / 53.282 | 63.036 |
49.894 | 1.183 (1.156/1.190) | 1.133 | 0.888 / 0.934 |
| doc_131072 | 131072 | 131072 | 1 | 20.354 / 102.968 / 123.321 |
151.650 | 115.831 | 1.230 (1.142/1.247) | 1.125 | 0.920 / 0.934 |
| cptail_4k_65536 | 4096 | 65536 | 1 | 0.670 / 3.332 / 4.003 | 5.159 |
3.939 | 1.289 (1.314/1.284) | 1.182 | 0.455 / 0.831 |
| cptail_4k_131072 | 4096 | 131072 | 1 | 0.803 / 3.963 / 4.766 | 6.657 |
5.074 | 1.397 (1.347/1.407) | 1.281 | 0.475 / 0.745 |
| packed_N1 | 32768 | 262144 | 1 | 7.192 / 36.287 / 43.479 | 54.642 |
40.322 | 1.257 (1.099/1.288) | 1.111 | 0.815 / 0.883 |
| packed_N2 | 32768 | 262144 | 2 | 5.988 / 32.132 / 38.122 | 48.438 |
36.300 | 1.271 (1.160/1.291) | 1.130 | 0.815 / 0.883 |
| packed_N4 | 32768 | 262144 | 4 | 5.057 / 25.181 / 30.239 | 39.046 |
29.741 | 1.291 (1.230/1.304) | 1.181 | 0.815 / 0.883 |
| packed_N8 | 32768 | 262144 | 8 | 4.598 / 21.996 / 26.595 | 30.741 |
25.634 | 1.156 (1.215/1.143) | 1.165 | 0.815 / 0.883 |
| packed_N16 | 32768 | 262144 | 16 | 4.570 / 21.721 / 26.292 | 29.804 |
24.660 | 1.134 (1.195/1.121) | 1.135 | 0.815 / 0.883 |
| packed_N32 | 32768 | 262144 | 32 | 4.567 / 21.710 / 26.280 | 29.718 |
24.615 | 1.131 (1.194/1.118) | 1.134 | 0.815 / 0.883 |
| skewed8 | 32768 | 262144 | 8 | 4.945 / 24.494 / 29.441 | 36.342 |
28.498 | 1.234 (1.212/1.239) | 1.163 | 0.815 / 0.883 |
| spread_32k_65536 | 32768 | 65536 | 1 | 4.819 / 23.193 / 28.013 |
34.637 | 26.985 | 1.236 (1.180/1.248) | 1.163 | 0.827 / 0.926 |
| spread_32k_131072 | 32768 | 131072 | 1 | 5.852 / 31.301 / 37.155 |
47.000 | 35.068 | 1.265 (1.136/1.289) | 1.120 | 0.823 / 0.911 |
| spread_32k_196608 | 32768 | 196608 | 1 | 6.668 / 34.621 / 41.289 |
51.932 | 38.498 | 1.258 (1.107/1.287) | 1.112 | 0.819 / 0.897 |

### SM100 (B200) — final (18 of 25 rows are clock-flagged by the
harness: on every flagged row the FlashMLA+cuDNN arm ran at a higher
loaded SM clock than this PR's arm — up to 11 % — and the FA arm between
3 % lower and 5 % higher; B200 power capping. The ratios are reported
uncorrected, so on those rows they understate the speedup over A)

| row | T | Tkv | segs | this PR fwd / bwd / step ms | A
(FlashMLA+cuDNN) step ms | FA #2914 step ms | A/this step (fwd/bwd) |
FA/this step (fwd/bwd) | peak / saved mem vs FA |
|---|---:|---:|---:|---|---:|---:|---|---|---|
| packed_glm_a | 16231 | 268757 | 8 | 4.060 / 19.089 / 23.150 | 27.852 |
32.489 | 1.203 (1.935/1.048) | 1.403 (1.361/1.413) | 0.721 / 0.828 |
| packed_glm_b | 16172 | 267520 | 8 | 4.034 / 18.890 / 22.912 | 27.876 |
32.379 | 1.217 (1.949/1.058) | 1.413 (1.367/1.422) | 0.721 / 0.828 |
| packed_glm_a_s704 | 16231 | 268757 | 8 | 4.026 / 19.014 / 23.036 |
28.255 | 32.563 | 1.227 (2.043/1.055) | 1.414 (1.376/1.421) | 0.721 /
0.828 |
| tail_2123x67923 | 2123 | 67923 | 1 | 0.749 / 3.192 / 3.942 | 4.792 |
5.208 | 1.216 (1.448/1.161) | 1.321 (1.186/1.358) | 0.476 / 0.743 |
| doc_16231 | 16231 | 16231 | 1 | 4.453 / 19.480 / 23.948 | 27.351 |
28.709 | 1.142 (1.728/1.009) | 1.199 (1.096/1.223) | 0.732 / 0.934 |
| doc_4095 | 4095 | 4095 | 1 | 0.992 / 3.821 / 4.819 | 6.099 | 6.654 |
1.266 (1.955/1.089) | 1.381 (1.398/1.378) | 0.433 / 0.934 |
| doc_4097 | 4097 | 4097 | 1 | 0.992 / 3.811 / 4.807 | 6.104 | 6.812 |
1.270 (1.957/1.092) | 1.417 (1.399/1.424) | 0.432 / 0.934 |
| doc_4096 | 4096 | 4096 | 1 | 0.992 / 3.818 / 4.809 | 6.100 | 6.641 |
1.268 (1.955/1.090) | 1.381 (1.398/1.377) | 0.433 / 0.934 |
| doc_8192 | 8192 | 8192 | 1 | 2.125 / 9.082 / 11.213 | 13.094 | 13.931
| 1.168 (1.815/1.017) | 1.242 (1.204/1.255) | 0.596 / 0.935 |
| doc_16384 | 16384 | 16384 | 1 | 4.505 / 19.657 / 24.152 | 27.710 |
28.914 | 1.147 (1.732/1.013) | 1.197 (1.100/1.220) | 0.733 / 0.934 |
| doc_32768 | 32768 | 32768 | 1 | 9.334 / 41.864 / 51.163 | 58.238 |
59.949 | 1.138 (1.704/1.009) | 1.172 (1.058/1.196) | 0.830 / 0.934 |
| cptail_4k_65536 | 4096 | 65536 | 1 | 1.312 / 5.801 / 7.144 | 8.844 |
9.618 | 1.238 (1.589/1.165) | 1.346 (1.138/1.404) | 0.455 / 0.831 |
| packed_N8 | 32768 | 262144 | 8 | 9.904 / 45.422 / 55.278 | 62.594 |
64.909 | 1.132 (1.661/1.018) | 1.174 (1.080/1.192) | 0.815 / 0.883 |
| packed_N16 | 32768 | 262144 | 16 | 9.489 / 42.965 / 52.501 | 60.019 |
61.027 | 1.143 (1.676/1.028) | 1.162 (1.079/1.183) | 0.815 / 0.883 |
| packed_N32 | 32768 | 262144 | 32 | 9.466 / 42.887 / 52.408 | 60.102 |
60.996 | 1.147 (1.679/1.030) | 1.164 (1.081/1.182) | 0.815 / 0.883 |
| skewed8 | 32768 | 262144 | 8 | 10.318 / 50.242 / 60.516 | 68.150 |
72.538 | 1.126 (1.655/1.017) | 1.199 (1.060/1.226) | 0.815 / 0.883 |
| doc_65536 | 65536 | 65536 | 1 | 20.189 / 91.097 / 110.966 | 119.821 |
132.797 | 1.080 (1.286/1.035) | 1.197 (1.024/1.229) | 0.888 / 0.934 |
| doc_131072 | 131072 | 131072 | 1 | 41.674 / 210.433 / 252.272 |
269.006 | 301.742 | 1.066 (1.257/1.030) | 1.196 (1.023/1.231) | 0.920 /
0.934 |
| cptail_4k_131072 | 4096 | 131072 | 1 | 1.486 / 7.440 / 8.928 | 10.233
| 11.140 | 1.146 (1.469/1.081) | 1.248 (1.129/1.272) | 0.475 / 0.745 |
| packed_N1 | 32768 | 262144 | 1 | 12.473 / 63.709 / 76.167 | 83.852 |
92.914 | 1.101 (1.526/1.019) | 1.220 (1.047/1.253) | 0.815 / 0.883 |
| packed_N2 | 32768 | 262144 | 2 | 11.451 / 61.090 / 72.623 | 80.408 |
87.830 | 1.107 (1.579/1.019) | 1.209 (1.055/1.237) | 0.815 / 0.883 |
| packed_N4 | 32768 | 262144 | 4 | 10.821 / 51.622 / 62.423 | 71.691 |
77.446 | 1.148 (1.621/1.050) | 1.241 (1.046/1.280) | 0.815 / 0.883 |
| spread_32k_65536 | 32768 | 65536 | 1 | 10.591 / 48.700 / 59.302 |
67.528 | 70.991 | 1.139 (1.631/1.034) | 1.197 (1.019/1.236) | 0.827 /
0.926 |
| spread_32k_131072 | 32768 | 131072 | 1 | 11.278 / 60.008 / 71.298 |
79.902 | 86.836 | 1.121 (1.611/1.029) | 1.218 (1.052/1.245) | 0.823 /
0.911 |
| spread_32k_196608 | 32768 | 196608 | 1 | 12.034 / 62.765 / 74.955 |
82.066 | 90.886 | 1.095 (1.541/1.014) | 1.213 (1.042/1.247) | 0.819 /
0.897 |

### SM103 (GB300) — final (no clock-flagged rows, all arms at 2070 MHz)

| row | T | Tkv | segs | this PR fwd / bwd / step ms | A
(FlashMLA+cuDNN) step ms | FA #2914 step ms | A/this step (fwd/bwd) |
FA/this step (fwd/bwd) | peak / saved mem vs FA |
|---|---:|---:|---:|---|---:|---:|---|---|---|
| packed_glm_a | 16231 | 268757 | 8 | 3.237 / 16.186 / 19.422 | 24.590 |
28.008 | 1.266 (2.065/1.106) | 1.442 (1.438/1.443) | 0.721 / 0.828 |
| packed_glm_b | 16172 | 267520 | 8 | 3.224 / 16.095 / 19.321 | 24.465 |
27.890 | 1.266 (2.066/1.106) | 1.444 (1.439/1.445) | 0.721 / 0.828 |
| packed_glm_a_s704 | 16231 | 268757 | 8 | 3.244 / 16.201 / 19.444 |
24.901 | 28.014 | 1.281 (2.157/1.105) | 1.441 (1.435/1.442) | 0.721 /
0.828 |
| tail_2123x67923 | 2123 | 67923 | 1 | 0.672 / 2.853 / 3.528 | 4.362 |
4.684 | 1.236 (1.395/1.200) | 1.328 (1.093/1.384) | 0.476 / 0.743 |
| doc_16231 | 16231 | 16231 | 1 | 3.698 / 16.398 / 20.097 | 24.373 |
24.090 | 1.213 (1.827/1.074) | 1.199 (1.111/1.219) | 0.732 / 0.934 |
| doc_4095 | 4095 | 4095 | 1 | 0.889 / 3.484 / 4.375 | 5.534 | 5.975 |
1.265 (1.936/1.095) | 1.366 (1.340/1.373) | 0.433 / 0.934 |
| doc_4097 | 4097 | 4097 | 1 | 0.890 / 3.477 / 4.366 | 5.539 | 6.134 |
1.269 (1.933/1.098) | 1.405 (1.344/1.420) | 0.432 / 0.934 |
| doc_4096 | 4096 | 4096 | 1 | 0.891 / 3.486 / 4.379 | 5.538 | 5.983 |
1.265 (1.933/1.095) | 1.366 (1.342/1.373) | 0.433 / 0.934 |
| doc_8192 | 8192 | 8192 | 1 | 1.823 / 7.866 / 9.690 | 11.895 | 12.101 |
1.228 (1.879/1.077) | 1.249 (1.193/1.262) | 0.596 / 0.935 |
| doc_16384 | 16384 | 16384 | 1 | 3.735 / 16.604 / 20.339 | 24.625 |
24.325 | 1.211 (1.827/1.072) | 1.196 (1.110/1.215) | 0.733 / 0.934 |
| doc_32768 | 32768 | 32768 | 1 | 7.603 / 34.089 / 41.694 | 50.310 |
49.102 | 1.207 (1.790/1.077) | 1.178 (1.076/1.200) | 0.830 / 0.934 |
| cptail_4k_65536 | 4096 | 65536 | 1 | 1.143 / 5.249 / 6.391 | 7.835 |
8.426 | 1.226 (1.544/1.157) | 1.318 (1.073/1.371) | 0.455 / 0.831 |
| packed_N8 | 32768 | 262144 | 8 | 7.812 / 35.828 / 43.638 | 53.048 |
51.136 | 1.216 (1.746/1.100) | 1.172 (1.085/1.191) | 0.815 / 0.883 |
| packed_N16 | 32768 | 262144 | 16 | 7.803 / 35.535 / 43.344 | 52.118 |
50.301 | 1.202 (1.749/1.083) | 1.161 (1.083/1.178) | 0.815 / 0.883 |
| packed_N32 | 32768 | 262144 | 32 | 7.799 / 35.540 / 43.340 | 52.084 |
50.262 | 1.202 (1.749/1.082) | 1.160 (1.086/1.176) | 0.815 / 0.883 |
| skewed8 | 32768 | 262144 | 8 | 8.129 / 41.780 / 49.910 | 58.081 |
60.142 | 1.164 (1.687/1.062) | 1.205 (1.086/1.228) | 0.815 / 0.883 |
| doc_65536 | 65536 | 65536 | 1 | 15.492 / 72.742 / 88.228 | 98.831 |
106.811 | 1.120 (1.307/1.080) | 1.211 (1.065/1.242) | 0.888 / 0.934 |
| doc_131072 | 131072 | 131072 | 1 | 33.024 / 174.869 / 207.900 |
224.633 | 251.308 | 1.080 (1.251/1.048) | 1.209 (1.062/1.237) | 0.920 /
0.934 |
| cptail_4k_131072 | 4096 | 131072 | 1 | 1.304 / 6.191 / 7.498 | 9.344 |
10.115 | 1.246 (1.421/1.210) | 1.349 (1.104/1.402) | 0.475 / 0.745 |
| packed_N1 | 32768 | 262144 | 1 | 10.753 / 58.064 / 68.814 | 75.739 |
83.386 | 1.101 (1.463/1.034) | 1.212 (1.056/1.241) | 0.815 / 0.883 |
| packed_N2 | 32768 | 262144 | 2 | 9.353 / 54.171 / 63.525 | 70.383 |
76.434 | 1.108 (1.537/1.034) | 1.203 (1.075/1.225) | 0.815 / 0.883 |
| packed_N4 | 32768 | 262144 | 4 | 8.223 / 44.003 / 52.230 | 59.971 |
64.863 | 1.148 (1.666/1.052) | 1.242 (1.089/1.271) | 0.815 / 0.883 |
| spread_32k_65536 | 32768 | 65536 | 1 | 7.992 / 38.824 / 46.831 |
55.811 | 58.052 | 1.192 (1.708/1.086) | 1.240 (1.056/1.278) | 0.827 /
0.926 |
| spread_32k_131072 | 32768 | 131072 | 1 | 9.213 / 53.166 / 62.377 |
68.951 | 74.947 | 1.105 (1.544/1.029) | 1.202 (1.060/1.226) | 0.823 /
0.911 |
| spread_32k_196608 | 32768 | 196608 | 1 | 10.189 / 56.609 / 66.797 |
73.564 | 80.458 | 1.101 (1.493/1.031) | 1.205 (1.053/1.232) | 0.819 /
0.897 |

## Accuracy

**SM107 (R200)** — rel-L2 in %, `this PR / FA`; gate = FA on the same
case x 1.05 (iid: canonical gate; 32k x 256k: per-row dq-latent p99 <=
0.4 % absolute)

| case | out | dq latent | dq rope | dkv latent | dk rope | dq-latent
row p99 | lse max abs err | bitwise out/dq | verdict |
|---|---|---|---|---|---|---|---|---|---|
| iid 4k x 4k | 0.201 / 0.196 | 0.217 / 0.217 | 0.237 / 0.237 | 0.235 /
0.235 | 0.234 / 0.234 | 0.238 / 0.238 | 1.7e-06 | True/True | PASS
(canonical gate) |
| peaked 4k (self-weight 0.53) | 0.166 / 0.166 | 0.235 / 0.235 | 0.237 /
0.237 | 0.225 / 0.225 | 0.235 / 0.235 | 0.272 / 0.272 | 6.1e-06 |
True/True | PASS (own gate) |
| peaked 4k (self-weight 0.99) | 0.161 / 0.161 | 0.237 / 0.237 | 0.238 /
0.237 | 0.201 / 0.201 | 0.236 / 0.237 | 0.409 / 0.389 | 8.8e-06 |
True/True | PASS (own gate) |
| top-k 4k (short-list rows) | 0.195 / 0.192 | 0.230 / 0.230 | 0.238 /
0.238 | 0.233 / 0.233 | 0.237 / 0.238 | 0.248 / 0.248 | 1.6e-06 |
True/True | PASS (own gate) |
| 32k x 256k skewed (row p99) | 0.169 / 0.169 | 0.238 / 0.237 | 0.238 /
0.237 | - | - | 0.340 / 0.317 | 9.7e-06 | True/True | PASS (row_p99
gate) |

**SM100 (B200)** — rel-L2 in %, `this PR / FA`; gate = FA on the same
case x 1.05 (iid: canonical gate; 32k x 256k: per-row dq-latent p99 <=
0.4 % absolute)

| case | out | dq latent | dq rope | dkv latent | dk rope | dq-latent
row p99 | lse max abs err | bitwise out/dq | verdict |
|---|---|---|---|---|---|---|---|---|---|
| iid 4k x 4k | 0.201 / 0.196 | 0.215 / 0.215 | 0.236 / 0.236 | 0.232 /
0.232 | 0.237 / 0.238 | 0.238 / 0.238 | 1.7e-06 | True/True | PASS
(canonical gate) |
| peaked 4k (self-weight 0.53) | 0.166 / 0.166 | 0.235 / 0.235 | 0.236 /
0.236 | 0.225 / 0.225 | 0.235 / 0.235 | 0.276 / 0.276 | 5.9e-06 |
True/True | PASS (own gate) |
| peaked 4k (self-weight 0.99) | 0.161 / 0.161 | 0.238 / 0.238 | 0.240 /
0.239 | 0.201 / 0.201 | 0.234 / 0.234 | 0.429 / 0.404 | 9.1e-06 |
True/True | PASS (own gate) |
| top-k 4k (short-list rows) | 0.194 / 0.191 | 0.230 / 0.230 | 0.238 /
0.238 | 0.233 / 0.233 | 0.237 / 0.237 | 0.247 / 0.247 | 1.8e-06 |
True/True | PASS (own gate) |
| 32k x 256k skewed (row p99) | 0.169 / 0.169 | 0.238 / 0.237 | 0.238 /
0.237 | - | - | 0.341 / 0.318 | 9.6e-06 | True/True | PASS (row_p99
gate) |

**SM103 (GB300)** — rel-L2 in %, `this PR / FA`; gate = FA on the same
case x 1.05 (iid: canonical gate; 32k x 256k: per-row dq-latent p99 <=
0.4 % absolute)

| case | out | dq latent | dq rope | dkv latent | dk rope | dq-latent
row p99 | lse max abs err | bitwise out/dq | verdict |
|---|---|---|---|---|---|---|---|---|---|
| iid 4k x 4k | 0.202 / 0.197 | 0.216 / 0.216 | 0.238 / 0.238 | 0.232 /
0.232 | 0.240 / 0.240 | 0.238 / 0.238 | 1.7e-06 | True/True | PASS
(canonical gate) |
| peaked 4k (self-weight 0.53) | 0.166 / 0.166 | 0.235 / 0.235 | 0.236 /
0.236 | 0.225 / 0.225 | 0.234 / 0.234 | 0.276 / 0.275 | 6.3e-06 |
True/True | PASS (own gate) |
| peaked 4k (self-weight 0.99) | 0.161 / 0.161 | 0.238 / 0.237 | 0.239 /
0.238 | 0.201 / 0.201 | 0.236 / 0.236 | 0.412 / 0.388 | 9.0e-06 |
True/True | PASS (own gate) |
| top-k 4k (short-list rows) | 0.196 / 0.193 | 0.229 / 0.229 | 0.237 /
0.237 | 0.232 / 0.232 | 0.238 / 0.238 | 0.246 / 0.246 | 1.6e-06 |
True/True | PASS (own gate) |
| 32k x 256k skewed (row p99) | 0.168 / 0.168 | 0.238 / 0.237 | 0.238 /
0.238 | - | - | 0.343 / 0.318 | 1.0e-05 | True/True | PASS (row_p99
gate) |

Forward `out` / `lse` and `dq` are bitwise repeatable run to run; the
fp32 `dK/dV` accumulation is order-dependent (scatter-add) as in the
baselines. Peak memory and saved activations are <= 0.94x FA #2914 on
every row. No NaN on any case.

## Validation

- `tests/experimental/test_cake_dsa_train.py`: 92 passed on SM107, SM100
and SM103 in the regenerated export checkouts and in fresh
shallow clones of the branch head `7d8a666355a0` (sha256 of the 37
delivered files verified); the final commit on top of it is
  formatting-only (ruff) and leaves those 37 files byte-identical.
- compute-sanitizer synccheck + memcheck: 0 errors on the forward,
backward, key-pass backward and full train-step programs on SM107,
  SM100 and SM103.
- Export protocol (fresh trace -> codegen -> NVRTC -> correctness
against the module reference on 10 registered shapes per
architecture): all PASS on the three architectures; the generated
programs are byte-identical to the ones produced by the source
  checkout on each host.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added sparse-attention support for SM107, packed and strided query/key
layouts, and causal filtering for variable-length inputs.
* Added optional in-place FP32 key/value gradient accumulation,
including destination-row mapping.
* Expanded benchmark coverage with GLM-5.2 trainer layouts and
layout-aware accuracy comparisons.
* **Documentation**
* Updated guidance for supported hardware, tensor layouts, causal
behavior, and gradient accumulation.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [6fa97dd](https://github.com/flashinfer-ai/flashinfer/commit/6fa97dda2af9651a2159e9199d4d6ee6e8fd8307)

- **作者**: eigen
- **时间**: 2026-10-02T20:39:00Z
- **提交信息**: feat(cake_bgmv_moe): fall back to the portable BGMV MoE path for unsupported inputs and launch the portable kernels on the current stream (#5809)

## Description

`prepare_bgmv_moe(..., backend="cake")` currently raises for every input
outside the generated Cake support set (one LoRA slice, rank 32, hidden
2688/3072, exact SM90/SM100/SM103). This PR makes it a complete entry
point:

- **Portable fallback plan.** `prepare_bgmv_moe(..., fallback=True)`
(new default) returns a `BGMVMoEPortablePlan` for unsupported inputs. It
has the same interface as `BGMVMoECakePlan` (`run()` → caller-visible
FP32 accumulator, pointer-stable workspaces, first eager call captures a
CUDA Graph, later calls replay it, `close()`), builds the `w_ptr` tables
once at prepare time, and runs the portable `bgmv_moe_shrink` +
`bgmv_moe_expand` kernels. `plan.backend_used` is `"cake"` or
`"portable"`; `plan.fallback_reason` carries the reason;
`plan.schedule_id` is `None` for the portable plan. One `RuntimeWarning`
is emitted per distinct reason per process. `fallback=False` keeps the
previous fail-closed `ValueError`.
- **Generalized validation.** Shape/dtype/index checks now cover any
rank, multiple slices (equal `feat_out`), FP16 and BF16 weights with
matching activations; invalid inputs (shape mismatches, FP32
activations, out-of-range routing indices, CPU tensors) always raise
regardless of `fallback`.
- **Portable kernels now launch on the caller's current stream.**
`csrc/bgmv_moe/moe_bgmv_impl.cuh` hard-coded `BGMV_MOE_GET_STREAM()` to
stream 0, so `bgmv_moe_shrink`/`bgmv_moe_expand` ignored the current
stream and could not be captured into a CUDA Graph: during capture their
launches were silently dropped and the replayed graph contained only the
zero-fills (all-zero output, bitwise stable, eager exact). The stream is
now threaded through `moe_bgmv_shrink_sliced` / `moe_bgmv_expand_sliced`
(`get_stream(x.device())`) and each dispatch checks `cudaGetLastError`,
so a dropped launch fails loudly. This defect predates #3535/#3542
(reproduced on `60f0bc0f960f` and on current `main`).

Context: #4821 added the prepared Cake backend and its perf results;
#5727 extended it to SM90/SM100/SM103 with the detailed re-measurement;
#5764 reverts the portable fast paths that the Cake backend supersedes
on the serving shapes. This PR is the fallback half of the "cover every
shape" follow-up; the generic-shape Cake bundles (any hidden % 8 == 0,
rank 8/16/32/64) follow in a separate PR.

## Tests

`tests/moe/test_cake_bgmv_moe.py`
- inputs rescaled so the FP32 reference is O(1) and the reference
asserts `|out|max > 0.5` on every active token. The former `x*0.1,
A*0.01, B*0.01` scales produced outputs below the `atol=1e-2` tolerance,
so an all-zero result passed vacuously (which is exactly how the stream
bug hid).
- new: `test_cake_plan_reports_backend_used`,
`test_fallback_plan_matches_reference[rank|hidden|slices]` (eager +
replay), `test_strict_mode_raises_for_unsupported_inputs`,
`test_fallback_on_unsupported_capability` (capability monkeypatched to
(8,0)), `test_fallback_warning_is_emitted_once_per_reason`,
`test_fallback_plan_outer_graph_capture_and_stream_check`,
`test_invalid_inputs_raise_even_with_fallback`.

`tests/moe/test_bgmv_moe.py`
- new
`TestBgmvMoeStreams::test_graph_capture_and_side_stream_match_eager[{4,64}
tokens × {bf16,fp16}]`: eager vs side-stream vs CUDA-Graph replay of the
prepared shrink+expand pipeline (outputs poisoned with NaN before
replay).

Validation on this branch (sglang 26.07 container, JIT build from
source):

| GPU | `tests/jit/test_cake_bgmv_moe_jit.py` |
`tests/moe/test_cake_bgmv_moe.py` | `tests/moe/test_bgmv_moe.py` |
`benchmarks/bench_cake_bgmv_moe.py` (cake vs portable, geomean) |
pre-commit |
|---|---|---|---|---|---|
| H100 80GB HBM3 (SM90) | 64 passed | 42 passed | 151 passed | 1.351× |
clean |
| B200 (SM100) | 64 passed | 42 passed | 151 passed | 1.457× | clean |

The dedicated benchmark numbers match #5727 (H100 1.37×, B200 1.47×
geomean over the same rows) within run-to-run noise; the Cake path
itself is untouched by this PR.

## Checklist

- [x] `pre-commit run --files <changed files>` clean
- [x] GPU tests on H100 and B200 (tables above)
- [x] Docs: `BGMVMoEPortablePlan` added to `docs/api/fused_moe.rst`;
`prepare_bgmv_moe` docstring describes the fallback

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added portable BGMV MoE execution for multiple LoRA slices and CUDA
configurations not supported by the Cake backend.
* Added an option to require Cake execution instead of falling back, and
plans now report the backend in use.
* **Bug Fixes**
* BGMV MoE operations now use the caller’s CUDA stream, supporting
stream ordering and CUDA Graph capture and replay. CUDA kernel launch
failures are now reported.
* **Documentation**
  * Added the portable BGMV MoE plan to the API reference.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [7026bd8](https://github.com/flashinfer-ai/flashinfer/commit/7026bd818f0d15b31a810974237b000688390f29)

- **作者**: eigen
- **时间**: 2026-10-02T20:33:53Z
- **提交信息**: fix(cake_dsv4): SM-count-aware split and head-tile planners for GB10 (48 SMs) (#5949)

## Summary

Follow-up to #5914 (`backend="cake"` SM120 DeepSeek-V4 NVFP4 sparse-MLA
decode): SM-count-aware split and head-tile planners so the route also
picks good schedules on GB10 (DGX Spark, SM121, 48 SMs). No kernel
change: the generated `csrc/cake_dsv4/sm_120a` sources are untouched
(regeneration from the kernel source reproduces manifest identity
`8dac14b4511f` byte for byte).

- `flashinfer/mla/_sparse_mla_sm120/_cake_dsv4_nvfp4.py`: below 64 SMs
the split loop keeps the split grid within SMs/3 CTAs and the distinct
gather streams (tokens x splits) within SMs/6, every CTA keeps at least
two 64-candidate chunks, and the full-grid wave-quantization split is
off; the head-tile planner pairs full-wave two-chunk rows only for 32
heads or while the one-tile grid is at most two waves. Decisions for 170
and 188 SMs (RTX 5090 / RTX PRO 6000) are unchanged.
- `tests/attention/test_cake_sparse_mla_sm120_dsv4_nvfp4.py`: GB10 cells
in the split and head-tile rule tests; the planner parity test against
the generating kernel module now covers `num_sms` 48, 170 and 188.

## Measurements (GB10, kernel unchanged)

Sweep of splits {1,2,4,8,16} x head tiles {1,2} over 108 C/D/O rows: the
previous planner was within 1 % of the best measured arm on 85/108 cells
(worst +28.3 %); the new rule is within 1 % on 106/108 (98.1 %), within
3 % on 108/108 (worst +2.65 %, inside the row's p10-p90 band).

GB10 validation of this branch (DGX Spark, JIT for sm_121a):
`tests/attention/test_cake_sparse_mla_sm120_dsv4_nvfp4.py` 84 passed,
baseline nvfp4 subset 18 passed; in-tree paired benchmark vs the
`SparseMLASm120Wrapper` route (28 shapes, medians):

| shape (T, H, topk, page[, extra]) | before (round-1 planner) | this PR
| note |
|---|--:|--:|---|
| geomean over 28 shapes | 1.430x | 1.462x | |
| T=8 H=8 topk=512 page 32 | 1.000x | 1.074x | over-split fixed (4-way
-> unsplit, 8 chunks per CTA) |
| T=8 H=8 topk=512 page 64 | 1.028x | 1.105x | same |
| T=32 H=8 topk=128 page 32 | 0.966x | 1.037x | |
| T=8 H=8 topk=512 + extra 512 (dual) | 0.961x | 0.939x | kernel-level
parity on GB10: every split/tile arm of the sweep is slower than the
route here |
| T=32 H=8 topk=128 page 64 | 1.034x | 1.000x | identical plan in both
runs; medians equal the route's at the timer resolution |

RTX 5090 / RTX PRO 6000 decisions are unchanged (planner fixtures for
170 and 188 SMs), so the GB202 numbers of #5914 are unaffected.

## Test plan

- [x] `pytest tests/attention/test_cake_sparse_mla_sm120_dsv4_nvfp4.py`
on GB10 (SM121): 84 passed (+ baseline nvfp4 subset 18 passed)
- [x] the same test file on RTX 5090 (GB202, SM120, sm_120a JIT): 84
passed (+ baseline nvfp4 subset 18 passed)
- [x] planner parity test (`num_sms` 48 / 170 / 188) against the
generating kernel module (part of the test file; also mirrored in the
Cake tree's `loom/tests/test_sm120_dsv4_nvfp4_planner.py`, 5940 split +
2970 head-tile cells vs the round-1 planner)
- [x] pre-commit (ruff, ruff-format, mypy) with the upstream `main` hook
pins

Tracker: #4254.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [ddcaaa7](https://github.com/flashinfer-ai/flashinfer/commit/ddcaaa74f313470d1829140f457e05e823650a2a)

- **作者**: Vincent
- **时间**: 2026-10-02T20:26:01Z
- **提交信息**: feat(attention): enable CuTe DSL VSA/BSA and Sage-quant tests on SM107 (Rubin) (#5397)

## What

Enables the CuTe DSL VSA/BSA backends on SM107 (Rubin) plus two
test-only pins. One commit per path; each is independent. (The Cake
video-sparse-attention enablement that was here moved to the dedicated
Cake PR #5467.)

| path | gate(s) removed | GR100 (cc 10.7) result |
|---|---|---|
| **CuTe DSL VSA/BSA blk64 + blk128** (incl. Sage-FP8) | `sparse.py`
dispatch tuples, `bsa_attn_sm100_blk{64,128}.py` entry asserts, the
blk128 kernel's own `Arch.sm_100..sm_100f / sm_103..sm_103f` range
assert, test predicate | `tests/attention/test_vsa_block_sparse.py`: 56
skipped → **47 passed / 9 skipped** (with `quack-kernels==0.6.4`
installed; the 9 are `FLASHINFER_TEST_PERF` sweeps) |
| **tests/trace reference-correctness** (test pin only) |
`tests/trace/reference_utils.py::_skip_if_not_sm100_or_103`
exact-(10,0)/(10,3) → SM100 family | six trace files: 16 skipped → **15
passed / 1 skipped** (the skip is the test's own graceful "kernel
unavailable" path for one decode-MLA variant, also partial on GB300) |
| **trtllm-gen SageAttention quantization** (test pin only) |
`test_trtllm_ragged_dit.py` exact-(10,0) → SM100 family | 3 skipped →
**3 passed** |

## Why these are safe

**CuTe VSA/BSA.** The blk64 kernel already asserted
`arch.is_family_of(sm_100f)`; the blk128 kernel had an explicit
SM100/SM103 range assert. Both compile natively for `sm_107a` with CuTe
DSL ≥ 4.8.0.dev0 and pass their numerics tests. Note the nightly image
does not ship `quack`, so in CI these tests keep skipping with "requires
the quack package" until the image installs it.

**Sage quant.** `trtllm_sage_attention_quantize` is plain JIT-compiled
CUDA (`csrc/trtllm_sage_quant.cu`, no architecture-specific
instructions) and already built for sm_100f on Rubin; the pin also
excluded SM103.

## Deliberately not included

- **PrimTS FMHA decode / block-sparse / q-token metadata** (~230 cases).
The library already accepts SM107 (`prims_ts/decode.py`); un-skipping
the tests makes every kernel launch fail with `TypeError:
Task._run_task_body_impl() got an unexpected keyword argument 'context'`
(and siblings). Root cause:
`flashinfer/attention/prims_ts/kernels/fmha_decode/fmha_decode_tasks.py`
calls the DSL's `task_scheduling.Task` base with `context=`, which the
image's baked **4.7.0** has but the **4.8.0.dev0** wheel the Rubin CI
job installs does **not** (`task.py:3193,3415,3561`). Arch-independent
DSL-version mismatch; tracked separately, test tuples left alone.
- **int8 DiT** (`test_trtllm_ragged_dit_sage_qdq`, 48 cases): the int8
tiles ship for sm_100a only — `Missing TRTLLM-GEN kernel ragged` 48/48
on SM107 (and on SM103, which is why the pin was exact-SM100). Pin kept;
its reason now says why.

## Validation

Image `flashinfer-ci:cu134-nightly-py3.67144516-whl-amd64` with the CI
job's `nvidia-cutlass-dsl[cu13]==4.8.0.dev0` override, against an
`upstream/main` baseline on the same tree/image; **zero new failures**.
x86_64 only; the Rubin CI nodes are arm64.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added SM107 support for block-sparse attention backends and compatible
attention operations. SM107 support for some operations requires a
compatible CuTe DSL installation.
* **Tests**
* Expanded attention and tracing test coverage to include SM107 where
supported. SM100a-only ragged attention tests remain limited to SM100.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Vincent Tombari <Vinnie6167@users.noreply.github.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [759bd6f](https://github.com/flashinfer-ai/flashinfer/commit/759bd6ff99ed9110372f1d629bff2d9ef5253678)

- **作者**: eigen
- **时间**: 2026-10-02T20:24:04Z
- **提交信息**: feat(cake_dsv4): SM120 DeepSeek-V4 NVFP4 sparse-MLA prefill for backend="cake" (#5959)

## Summary

Prefill companion to #5914 / #5949 (`backend="cake"` SM120 DeepSeek-V4
NVFP4 sparse-MLA decode): a native streaming-prefill kernel family for
the same NVFP4 384 B paged-KV format on GB202 (RTX PRO 6000 Blackwell
SE, RTX 5090), routed through the existing sparse-MLA entry points with
a measured decode/prefill crossover and head-tile planner. Kernels are
register-MMA only (`mma.sync` mxf4nvf4 QK / f8f6f4 PV, `cp.async`
gather, fp32 online softmax); one CTA per token tile and head-tile group
(one, two or four 16-head tiles share one gather), direct epilogue, no
merge pass.

- `csrc/cake_dsv4/sm_120a`: generated
`cake_sparse_mla_dsv4_nvfp4_prefill_h<N>.cu` (N = 16 .. 128) with every
valid head-tile count x single / dual cache, the binding's prefill
entry, kernel ABI header and manifest (manifest identity `7e53b649ece7`;
the decode units are #5949's byte for byte, `decode_sources_kept` in the
manifest). The decode sources are unchanged.
- `flashinfer/jit/cake_sparse_mla_sm120_dsv4_nvfp4.py`,
`flashinfer/mla/_sparse_mla_sm120/_cake_dsv4_nvfp4.py`: the prefill JIT
spec and launch, `select_kernel` (decode for 8 heads and for more than
16 chunks; otherwise decode through T=8 for >= 64 heads with >= 512
candidates, T=16 with fewer, T=8 (188 SMs) / T=32 (170 SMs) for narrower
heads with >= 512 candidates; prefill at every token count for narrow
heads with fewer candidates) and `plan_prefill` (two tiles through 96
tokens for wide head counts, through 128 tokens for 128 heads with
512-639 candidates on the 188-SM die; the largest instance above).
- `flashinfer/mla/_sparse_mla_sm120/_api.py`, `flashinfer/mla/_core.py`:
the `backend="cake"` route takes the prefill; the main-page / H8 /
extra-page gates are lifted for the cake backend only.
- `tests/attention/test_cake_sparse_mla_sm120_dsv4_nvfp4_prefill.py`:
FP32-oracle parity against the dequantized reference, dual cache,
independent lengths, -1 padding, zero-length KV with and without sink,
masked tails, token counts 3 / 65 / 257, HND / NHD layouts, caller
workspace, CUDA-graph replay, bitwise repeat, policy rule tests, planner
parity with the generating kernel module over `num_sms` x T x heads x
candidates.
- `benchmarks/bench_cake_sparse_mla_sm120_dsv4_nvfp4_prefill.py`,
`docs/api/attention.rst`.

## Measurements

Paired A/B against the FlashInfer prefill route on the same card (CUPTI
active union of every GPU launch of the call, cold L2, ABAB/BABA groups
>= 3, pooled medians; 384 MB pool, page 64 unless noted). Baselines:
`main` 9f5837054; K=256 rows against PR #5033 head a30f0018;
runtime-page rows (page 32 / 128) against PR #5763 head 7b5ef6eb, where
the baseline's H8 prefill runs the decode kernel.

| set (rows) | RTX PRO 6000 Blackwell SE | RTX 5090 |
|---|--:|--:|
| P: T 128 / 512 / 2048 / 8192 x H 16 / 32 / 64 / 128 x K 128 / 512 (32
rows) | 2.34x (min 1.53x) | 2.32x (min 1.57x) |
| D: dual cache, extra K 128 (page 2) / 512 (page 64) (24 rows) | 2.98x
| 2.86x |
| O: NHD layout (4 rows) | 2.57x | 2.63x |
| B: batched requests (4 rows) | 2.34x | 2.04x |
| X256: K=256 vs #5033 (6 rows) | 2.73x | 2.77x |
| XRP: page 32 / 128 vs #5763 (4 rows) | 2.65x | 2.27x |
| rows faster than the baseline | 74 / 74 | 74 / 74 |

Three consecutive rounds within 1 % (Cake-time geomean) on each SKU; the
crossover tables (T 1..128 for H16 / H128 x K128 / K512, decode vs one-,
two- and four-tile prefill) are what the planner encodes. RTX 5090 rows
at T=8192 run under the card's 575 W power limit (both arms, paired).

## Test plan

- [x] `pytest
tests/attention/test_cake_sparse_mla_sm120_dsv4_nvfp4_prefill.py` on RTX
PRO 6000 Blackwell SE (sm_120a JIT, driver 595.84): 67 passed (+ 4
policy / planner-parity tests)
- [x] `pytest tests/attention/test_cake_sparse_mla_sm120_dsv4_nvfp4.py`
(decode route, sources unchanged from #5949) on RTX PRO 6000: 83 passed,
1 skipped
- [x] the same two files on RTX 5090 (driver 615.36): 67 passed (+ 4),
83 passed, 1 skipped
- [x] compute-sanitizer synccheck + memcheck on the generating kernels
(both SKUs): 0 errors
- [x] pre-commit (ruff, ruff-format) with the upstream `main` hook pins

Depends on #5949 (stacked; the first commit of this branch is its head).
Tracker: #4254.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added single-launch NVFP4 sparse MLA prefill for supported SM120/SM121
GPUs. The kernel selector chooses between prefill and split decode based
on workload characteristics.
* Added prefill planning and head-tile options, with support for
optional extra caches and caller-provided buffers.
  * Added a benchmark comparing sparse MLA prefill paths.

* **Documentation**
* Expanded API and usage guidance for prefill, kernel selection,
planning, and benchmarking.

* **Tests**
* Added coverage for prefill correctness, workload planning, API
routing, and supported hardware configurations.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [3dea410](https://github.com/flashinfer-ai/flashinfer/commit/3dea41055e232fddca253ea814913d41b0e3727b)

- **作者**: eigen
- **时间**: 2026-10-02T20:22:53Z
- **提交信息**: perf(cake_sampling): round 8 -- slab-tail twins of the sample builds, pushed-coarse-sums twin of the cluster-8 default build, Hopper whole-CTA tail policy (#5950)

## Cake radix sampling, round 8: slab-tail twins of the sample builds
and a pushed-coarse-sums twin of the cluster-8 default build

Follow-up of #5439, #5482, #5585, #5607, #5636, #5684, #5731 and #5847
(the round-7 host 1cad3816 / bundle e68d4b47 is the baseline).

### What changes

- **Slab-tail twins (`_cs_lb`, `_sp_lb`; launch flag bit 7, manifest
`slab_tail`, 16 new stage-1 kernels).** In the
fused launches of the two sample builds the stage-1 CTAs push their
selected (value, index) pairs into the lead CTA's
shared-memory slab over DSM instead of a global round trip through the
candidate workspace before the two-warp fused
tail. The host adds bit 7 for fused sample-build launches on compute
capability 10.0 / 10.3 only, for rows of at most
5 register chunks per CTA; Hopper and Rubin keep the plain `_cs` / `_sp`
builds (the slab is slower on the single-row
cluster-8 cells there), and so do the long cluster-1 / cluster-2 rows
(8-16 chunks per CTA: B >= 64 at V >= 128256,
0-2 % slower with the slab on B200 / GB300 in both matrix orders and in
same-node interleaved A/Bs). Bit 7 is
host-side like bits 4 and 6 and is rejected without bit 0 and one of
bits 4 / 6.
- **Pushed-coarse-sums twin (`_lg`; launch flag bit 8, manifest
`coarse_push`, 2 new stage-1 kernels).** The cluster-8
default stream builds get a form whose CTAs push their coarse histogram
sums into every rank's shared memory before the
cluster barrier so the select warp reads them locally. The host adds bit
8 for two-launch chains of the ept-32 build
on compute capability 9.0 / 10.3 only (default builds serve only
chains); B200 keeps the plain build, and so does the
ept-16 build everywhere (its four-chunk cluster-8 chains at V = 262144
measured 1.4-5.6 % slower with it on GB300).
Bit 8 needs a stream variant, excludes bits 3 / 4 / 6 / 7 and is
rejected with bit 0.
- **Whole-CTA tail on Hopper (host policy only; the `_bt` kernels are
round 7's).** `_BLOCK_TAIL_CAPABILITIES` gains
compute capability 9.0 with no vocabulary bound: on H100 the one-wave
cluster-8 cells with 64 < k <= slab run the
bit-3 whole-CTA tail instead of the two-launch chain (graph replay V =
151936 0.93-0.97, V = 262144 0.96-0.99; two-wave
  grids keep the chain).
- The 73 round-7 kernels are byte-identical to the shipped bundle: raw
(un-normalised) source identity of the generated
bundle and per-architecture cubin `.text` identity of the JIT modules
(sm_90a / sm_100a / sm_103a / sm_107a); the 18
new kernels are twins, so every unchanged route keeps its binary. The
generator pins the explicit shared-memory base
conversion on every target for these kernels
(`SmemBaseMaterialization.EXPLICIT_WARP_UNIFORM`); without the pin the
round-8 tree's arch default changed the Hopper / GB300 / Rubin machine
code of the shipped kernels (GB300 +4.7 % on
the cluster-8 ept-16 stream kernel) while a normalised source gate
stayed green.
- Manifest validation: `slab_tail` only on coarse / speculative entries
with a plain sibling, `coarse_push` only on
cluster >= 8 stream entries of the default build with a plain sibling;
the loader rejects a manifest that lacks either.
- Tests: `tests/utils/test_cake_sampling.py` gains
`test_slab_tail_build_matches_sample_build` and
`test_coarse_push_build_matches_default_build` (bitwise against the
plain builds) and pins the three host policies
(chunk bound, ept bound, Hopper block tail); the native chain binding of
the earlier draft is not part of this PR
  (measured neutral).

### Speedup (same node / run CUPTI medians, round-7 bundle -> round-8
bundle; eager = median over four fresh processes)

| GPU | k | mode | cells | round-8 / round-7 time (median, min .. max) |
rows > +0.5 % in both tree orders | speedup vs top_k_first (min .. max)
|
|---|---|---|---|---|---|---|
| B200 | 10 | eager | 32 | 0.972 (0.952 .. 1.000) | 0 | 3.1x .. 9.2x |
| B200 | 10 | graph | 32 | 0.987 (0.972 .. 1.004) | 0 | 2.1x .. 4.5x |
| B200 | 50 | eager | 32 | 0.974 (0.952 .. 1.000) | 0 | 3.1x .. 9.5x |
| B200 | 50 | graph | 32 | 0.982 (0.884 .. 1.095) | 0 | 2.3x .. 4.6x |
| B200 | 1000 | eager | 32 | 1.000 (0.995 .. 1.002) | 0 | 2.9x .. 7.8x |
| B200 | 1000 | graph | 32 | 0.964 (0.957 .. 0.982) | 0 | 1.7x .. 6.0x |
| B200 | all | | 192 | summary: FLAGGED_BOTH_ORDERS 0, NOT_FASTER 0,
worst single-order row +20.8% at (50, 'graph', 32768, 128) | | |
| GB300 | 10 | eager | 32 | 0.974 (0.952 .. 1.000) | 4 | 5.3x .. 17.0x |
| GB300 | 10 | graph | 32 | 0.994 (0.976 .. 1.020) | 2 | 2.0x .. 4.3x |
| GB300 | 50 | eager | 32 | 0.975 (0.949 .. 1.000) | 3 | 5.1x .. 16.5x |
| GB300 | 50 | graph | 32 | 0.991 (0.961 .. 1.022) | 4 | 2.1x .. 4.3x |
| GB300 | 1000 | eager | 32 | 1.000 (0.927 .. 1.144) | 2 | 3.5x .. 7.8x
|
| GB300 | 1000 | graph | 32 | 1.005 (0.961 .. 1.035) | 7 | 1.6x .. 6.0x
|
| GB300 | all | | 192 | summary: FLAGGED_BOTH_ORDERS 22, NOT_FASTER 0,
worst single-order row +26.4% at (1000, 'eager', 262144, 8) | | |
| H100 | 10 | eager | 32 | 1.000 (1.000 .. 1.003) | 0 | 2.4x .. 8.6x |
| H100 | 10 | graph | 32 | 0.998 (0.992 .. 1.003) | 0 | 2.1x .. 3.6x |
| H100 | 50 | eager | 32 | 1.000 (0.996 .. 1.003) | 0 | 2.5x .. 8.6x |
| H100 | 50 | graph | 32 | 1.000 (0.996 .. 1.004) | 0 | 2.3x .. 3.7x |
| H100 | 1000 | eager | 32 | 1.000 (0.867 .. 1.003) | 0 | 2.5x .. 6.6x |
| H100 | 1000 | graph | 32 | 0.997 (0.895 .. 1.004) | 0 | 1.7x .. 5.8x |
| H100 | all | | 192 | summary: FLAGGED_BOTH_ORDERS 0, NOT_FASTER 0,
worst single-order row +1.5% at (1000, 'eager', 128256, 1) | | |
| R200 | 10 | eager | 32 | 1.000 (0.995 .. 1.005) | 0 | 3.2x .. 6.3x |
| R200 | 10 | graph | 32 | 0.997 (0.988 .. 1.014) | 1 | 2.0x .. 3.8x |
| R200 | 50 | eager | 32 | 1.000 (0.993 .. 1.004) | 0 | 3.2x .. 7.1x |
| R200 | 50 | graph | 32 | 1.005 (0.998 .. 1.009) | 3 | 2.0x .. 3.7x |
| R200 | 1000 | eager | 32 | 1.000 (0.994 .. 1.013) | 1 | 2.3x .. 7.7x |
| R200 | 1000 | graph | 32 | 0.998 (0.925 .. 1.004) | 0 | 1.5x .. 6.4x |
| R200 | all | | 192 | summary: FLAGGED_BOTH_ORDERS 5, NOT_FASTER 0,
worst single-order row +7.4% at (1000, 'graph', 32768, 1) | | |

Rows above +0.5 % in both tree orders were re-measured with a same-node
interleaved A/B of the round-7 and round-8 host
policies in one process (7 alternating pairs, bitwise-equal outputs):
**0 confirmed regressions on every GPU** (B200 0 flagged,
H100 0 flagged; R200 5 flagged -> A/B 0.991-1.010 with identical arms on
cc 10.7 = the graph-replay noise band; GB300 22
flagged -> 21 cells 0.91-1.005 in the A/B, the twin-served cells faster,
and the single cell above the line in one process
(V262144 B1 k10 graph 1.015) reads 0.907-0.927 graph / 0.942-0.953 eager
over perturbed allocation histories). Nodes:
B200 nsc-svg gpu-19, GB300 oci-jhb nvl72d362-T14, H100 cw-dfw
pool0-01646, R200 hecate0339.


### Correctness

- Exactness suite (bitwise vs the plain builds) on B200 / GB300 / H100 /
R200; FlashInfer tests at this head:
255 passed / 18 skipped per GPU (GB300, B200, H100, R200); RTX PRO 6000
(sm_120, this head fc134a40): 250 passed / 23 skipped.
- compute-sanitizer synccheck + memcheck: 0 errors on B200 and R200 for
every new kernel.
- sglang GSM8K parity (Qwen3.5-35B-A3B, n = 1319): cake arm within the
top_k_first spread, 0 samples outside the support.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [3e72f50](https://github.com/flashinfer-ai/flashinfer/commit/3e72f5025304833392f4e228b4f23ac711e7ab0e)

- **作者**: Vincent
- **时间**: 2026-10-02T19:56:36Z
- **提交信息**: feat(mla): enable TRTLLM-GEN DSv4 sparse MLA/RopeQuant on SM107 (Rubin) (#5391)

## What

Enables the TRTLLM-GEN DeepSeek V4 sparse MLA + RopeQuant path on SM107
(Rubin), held back by a static architecture allowlist. (The Cake
concat-MLA-K enablement that was here moved to the dedicated Cake PR
#5467.)

| path | gate(s) removed | GR100 (cc 10.7) result |
|---|---|---|
| TRTLLM-GEN DeepSeek V4 sparse MLA + RopeQuant
(`trtllm_batch_decode_sparse_mla_dsv4`) | `flashinfer/mla/_core.py`
`is_sm100_family = cc in ((10, 0), (10, 3))` + the two backend checks it
feeds; two test predicates |
`tests/attention/test_trtllm_gen_sparse_mla_dsv4.py`: 9 passed / 110
skipped → **119 passed** (sparse MLA incl. strided pages and CUDA-graph
replay, plus the RopeQuant correctness tests) |

## Why these are safe

**DSv4 sparse MLA / RopeQuant.** These are precompiled TRTLLM-GEN
cubins. The published FMHA package is multi-architecture (sm100f /
sm103a / sm107a), the runtime selector already maps `kSM_107` onto the
sm100f kernels (`include/flashinfer/trtllm/fmha/fmhaKernels.cuh`), and
the host launcher builds with the default `map_sm107_to_100f` flags. The
only thing excluding Rubin was the Python family check, and the 110
previously-skipped cases all pass — so the DSv4 tiles really are in the
package (the existing "Missing TRTLLM-GEN kernel" skip would have fired
otherwise).

## Deliberately not included

- **CuTe DSL HCA** (`test_cute_dsl_hca_dsv4.py`, 5 cases). Widening its
gate compiles the kernel natively for `sm_107a`, and the kernel body's
`const_expr` architecture arms (`hca_fp8.py` ~L3046) cover only
`sm_100..sm_100f` / `sm_103..sm_103f`, so the accumulator TMEM load is
compiled out and the output is non-finite. Enabling it properly is a
kernel change to discuss with the HCA author.
- **PrimTS MLA decode** (`test_attention_ts_mla_decode.py`, 119 cases).
The library already accepts SM107; the tests skip because, under the
`nvidia-cutlass-dsl==4.8.0.dev0` the Rubin CI job installs, the DSL's
`task_scheduling.Task` API lacks the `context` parameter prims_ts passes
(4.7.0 has it) — an arch-independent DSL-version mismatch, tracked
separately.

## Validation

GR100 (cc 10.7, driver 620.05), image
`flashinfer-ci:cu134-nightly-py3.67144516-whl-amd64` with the CI job's
own `nvidia-cutlass-dsl[cu13]==4.8.0.dev0` override, against an
`upstream/main` baseline on the same tree/image — numbers in the table
above; **zero new failures**. Validated on x86_64 only; the Rubin CI
nodes are arm64.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Sparse MLA on SM107 GPUs now supports automatic backend selection and
explicit TRTLLM-GEN selection, alongside SM100 and SM103.
* The DSv4 API documentation now describes the prebuilt-cubin path and
BF16/FP8 E4M3 query support on SM107.
  * CuTe DSL and CAKE remain limited to SM100 and SM103.

* **Bug Fixes**
* Selecting CuTe DSL or CAKE on SM107 now reports the supported GPU
architectures.

* **Tests**
* Expanded sparse MLA backend-selection and correctness coverage to
include SM107.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Vincent Tombari <Vinnie6167@users.noreply.github.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: mingyangw <35635157+saltyminty@users.noreply.github.com>

### [e6866d8](https://github.com/flashinfer-ai/flashinfer/commit/e6866d83fc7576905fb1c6af912c937e9261571c)

- **作者**: Ka-Hyun Nam
- **时间**: 2026-10-02T19:03:22Z
- **提交信息**: fix(gdn): point the gated_delta_rule_mtp deprecation marker at 0.8.0 (#5306)

<!-- .github/pull_request_template.md -->

## 📌 Description

`gated_delta_rule_mtp()`'s `disable_state_update` deprecation marker
names **0.7.0** as the
release where the implicit default flips to `False` — in three places,
one of which is a runtime
`warning_once`. `main` and `release-v0.7.0` are both 0.7.0, and the
default there is still `True`
(`gdn_decode.py` resolves `None` → `True`). So 0.7.0 ships a warning
promising a change that
0.7.0 does not make, naming itself as the release.

**0.8.0 is the correct target, not a deferral.** The deprecation first
shipped in **v0.6.7** —
`git tag --contains 7cb016df` (PR #2730), earliest non-rc, non-nightly
tag. Under the window
documented in `docs/deprecation_survey_v0.7.0.md`:

> **Window.** A deprecated public API is guaranteed for **two minor
releases**, then may be
> removed. Deprecated in 0.5.x → removable at **0.7.0**. Deprecated in
0.6.x → removable at
> **0.8.0**.

a 0.6.x deprecation is not eligible until 0.8.0. The marker was written
one minor early; honouring
it in 0.7.0 would itself violate the two-minor guarantee. This is the
same failure mode the survey
records in its §3 for two `bsa_attn` docstrings: *"Trust git, not the
docstring."*

This PR amends the three strings and changes nothing else. The resolved
default is still `True`.


## 🔍 Related Issues

Follows up #5218 (`chore: remove deprecated APIs eligible at the 0.7.0
boundary`), which surveyed
this symbol and left the decision open. Deprecation introduced in #2730.

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

No tests added: the change is three user-facing strings with no
reachable behavior change. The
resolved default is unchanged, and no test asserts the marker text.

## Reviewer Notes

Intended for cherry-pick onto `release-v0.7.0` — kept to one file and
three lines for that reason.

One loose end, deliberately **not** fixed here to keep the cherry-pick
clean: the survey (§2) and
PR #2730's title both describe this deprecation as covering the
`intermediate_states_buffer=True`
default, while the live marker and warning are about
`disable_state_update`. Both trace to the same
commit and release, so eligibility is unaffected, but the two describe
different parameters and it
is worth checking whether the warning was reworded or whether there were
originally two
deprecations and only one survived.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Documentation**
* Updated deprecation messaging to clarify that the default behavior
will change in FlashInfer 0.8.0.
* **Bug Fixes**
* Corrected runtime warning text to reference the appropriate upcoming
version.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [158ebeb](https://github.com/flashinfer-ai/flashinfer/commit/158ebeb5ea7b0b20fa8d3570ff2e1e525e903dd9)

- **作者**: wdykas
- **时间**: 2026-10-02T19:01:27Z
- **提交信息**: fix(sampling): honor per-row seed and offset tensors (#5745)

<!-- .github/pull_request_template.md -->

## 📌 Description

Honor batch-length seed and offset tensors in the sampling kernels. The
Python APIs accept singleton or batch-length RNG tensors, but all seven
CUDA kernels currently read only element zero. Consequently, later
output rows ignore their supplied seeds and offsets.

Pass independently computed seed/offset strides from tensor metadata
through the launchers: zero for singleton broadcasting, one for
per-output-row arrays. Index RNG arrays by output row, including when
`indices` gathers or repeats input rows. Validate tensor lengths at the
FFI boundary and return the validated seed/offset strides together
before launching.

This covers logits, probability, top-k, top-p, min-p, joint top-k/top-p,
and chain speculative sampling. The top-k/top-p logits API is covered
through its joint sampling path. The change adds no tensor copies, CPU
readbacks, or extra kernel launches.

### Release note

Batch-length `seed` and `offset` tensors now apply one value per output
row instead of broadcasting element zero. Calls with distinct values can
therefore produce different samples after this fix. Scalar values,
length-one tensors and shared `torch.Generator` calls retain their
existing behavior. The output row index still feeds the Philox
subsequence, so identical seed/offset values at different batch
positions do not guarantee identical samples.

## 🔍 Related Issues

No linked issue. Found while testing per-request RNG tensors for
reproducible generation.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

Ran `pre-commit run --files csrc/sampling.cu
include/flashinfer/sampling.cuh
tests/utils/test_sampling_seed_offset.py`; all applicable hooks passed,
including clang-format and Ruff. Hooks were invoked through `uv tool
run`; the repository-wide hook run and hook installation checkboxes
above remain unchecked.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

Targeted GPU checks passed; the full repository suite was not run.

- On unmodified main (`1c84d0eae49bd956f8fcc51d741acc18179a21e2`), the
initial regression matrix produced **110 failures and 42 passes**. The
broadcast controls passed; per-row seed/offset checks failed.
- Final patch: **179 passed**, comprising all **158 new tests** plus
**21 existing scalar seed/offset tests**:
  ```bash
pytest tests/utils/test_sampling_seed_offset.py
tests/utils/test_sampling.py \
    -k 'row_seed_offset or rng_tensor or seed_offset' -q --tb=short
  ```
- Coverage includes int64/uint64 RNG tensors, independent
singleton/per-row lengths, repeated input indices with different
input/output batch sizes, speculative rejection/final-token draws,
CUDA-graph replay before and after in-place RNG updates, and direct-FFI
rejection of invalid array lengths.
- Each output row is compared exactly with a scalar-seed/offset
reference at the same output position.
- Hardware/environment: NVIDIA GB200 (SM100a), CUDA 13.2.78 compiler,
Python 3.13.14, PyTorch 2.11.0, FlashInfer 0.7.1 source checkout.
Sampling kernels were JIT-built from this checkout.

Review follow-up validation on GB200: **195 passed** (158 per-row RNG
tests, 21 existing scalar seed/offset tests, and 16 tests across the
eight sampling trace-reference files requested in review). The validator
now returns both checked strides; all seven launchers consume that
result. All 16 seed/offset docstrings specify output-row indexing, and
all eight seed docstrings explain the Philox subsequence limitation.
Changed-file pre-commit checks passed, including clang-format, mypy and
Ruff. The full repository suite was not run.

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

Python signatures are unchanged. The seven C++ launcher signatures
append optional stride arguments after `stream` to retain existing
positional calls; default stride zero preserves legacy pointer
broadcasting. Scalar RNG inputs, shared `torch.Generator` calls, and
length-one tensor inputs retain their existing behavior. Batch-length
tensors intentionally change to honor each row's values.

This fixes tensor interpretation, not batch-position invariance: the
existing Philox subsequence still incorporates the output row. The tests
preserve that position in their scalar references.

Reviewed the kernel indexing, launch argument order, FFI bounds checks
and the complete diff using the repository's self-review guidance. No
dependency or submodule changes are included.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Sampling operations support separate random seeds and offsets for each
output row. A single value can still be shared across rows; batch-length
tensors apply values by output position.
* **Bug Fixes**
* Sampling validates that seed and offset inputs contain either one
value or one value per output row, and reports an error for unsupported
lengths.
* **Documentation**
* Clarified that moving an output row can change its random-number
sequence, even when its seed and offset stay the same.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: wdykas <wdykas@nvidia.com>

### [f44d2e6](https://github.com/flashinfer-ai/flashinfer/commit/f44d2e6c12328bdb4e8972506ed357f10de2d3f2)

- **作者**: Vincent
- **时间**: 2026-10-02T18:54:55Z
- **提交信息**: feat(moe): refresh the SM107 CuTe DSL gather+activation MoE kernel from TensorRT-LLM (SiTU, Relu2) (#5462)

## What

Refreshes the SM107 (Rubin) CuTe DSL gather + activation grouped-GEMM
MoE kernel
(`flashinfer/fused_moe/cute_dsl/rubin/blockscaled_contiguous_gather_grouped_gemm_swiglu_fusion.py`)
from the current TensorRT-LLM source
(`tensorrt_llm/_torch/cute_dsl_kernels/rubin/moe/rubin_contiguous_gather_grouped_blockscaled_gemm_act_fusion.py`
@ `ef34db4`, 2026-09-22), and enables the tests the refresh makes pass
on SM107.

The FlashInfer copy predates upstream's `activation_type` support and
hardcoded SwiGLU. The upstream kernel now implements **SwiGLU, SiTU and
Relu2** (`validate_activation_type`, `_apply_swiglu_epilogue` /
`_apply_situ_epilogue` / `_apply_relu2_epilogue`; Relu2 keeps N
un-halved through `mma_tiler_c`, `interm_size` and the epilogue subtile
count) and renamed `ugpu_half_gemm` to `locality_domain_half_gemm`.

## FlashInfer adaptations kept on top of the drop

All are marked with `flashinfer` comments in the kernel; the header
records the upstream commit.

- `ActivationType` / `is_gated_activation` come from
`flashinfer.tllm_enums` (TRT-LLM's `ActivationType.SiTu` is
`ActivationType.Situ` here).
- The class keeps its FlashInfer name
(`Sm107BlockScaledContiguousGatherGroupedGemmSwigluFusionKernel`) so no
caller changes; the TRT-LLM name is exported as an alias.
- Constructor shims: `enable_pdl` → `use_pdl`, `ugpu_half_gemm` →
`locality_domain_half_gemm`.
- SiTU follows the convention the Blackwell kernel and
`validate_cute_dsl_moe_situ_config` already use: requested as
`ActivationType.Swiglu` + `situ_beta`, with `situ_linear_beta=None`
leaving the up branch unclamped (`tanh_u = u`). TRT-LLM requires both
betas; the optional-beta path is a `const_expr` branch in
`_apply_situ_epilogue`. Explicit `ActivationType.Situ` is accepted too.

## Dispatcher / tuner

- `blockscaled_contiguous_gather_grouped_gemm_act_fusion.py`: the Rubin
branch now accepts Swiglu (incl. SiTU) and Relu2 and passes
`activation_type`, `situ_beta`, `situ_linear_beta` to the kernel. Still
`NotImplementedError` for GegluTanh, for non-default
`swiglu_alpha/beta/limit`, and for `use_a_per_token_scale` (the SM107
wrapper still has 12 pointers and no `a_per_token_scale_ptr` upstream
either). The cache key already carried activation and SiTU betas.
- `tuner.py`: Rubin tactics are rejected only for GegluTanh instead of
every non-gated activation.

## Tests

`tests/moe/test_cute_dsl_fused_moe.py`: removed the three SM107 skips
this makes stale — Relu2 in
`TestNumericalAccuracy._run_numerical_accuracy` and
`test_wrapper_with_autotune`, and the SiTU skip in `test_situ_accuracy`
(both the gate-clamp `(1.75, None)` and gate-and-up-clamp `(0.8, 1.5)`
cases). The GegluTanh, custom-SwiGLU-constant,
per-token-activation-scale and non-fused-finalize skips stay: those
remain unimplemented upstream.

Not synced: the finalize kernel and `utils.py` / `custom_pipeline.py` /
`inline_ptx.py` (upstream deltas there are formatting/comments only; the
gather kernel needs no new symbols from them).

## Validation

SM107 part, cu134 nightly image + the CI job's
`nvidia-cutlass-dsl[cu13]==4.8.0.dev0` override,
`tests/moe/test_cute_dsl_fused_moe.py`, against an `upstream/main`
(`2268a1aeb`) baseline on the same tree/image:

| | passed | failed | skipped |
|---|---|---|---|
| `upstream/main` | 312 | 0 | 309 |
| this branch | **392** | 0 | 229 |

+80 newly passing, zero new failures. The skip-reason histogram loses
exactly the three removed reasons (76 "only implement the gated (SwiGLU)
activation path" + 4 SiTU), and the remaining SM107 skips are the
documented upstream gaps: 116 `a_per_token_scale` pointer, 66 non-fused
finalize, 19 custom SwiGLU constants, 7 W4A8, 5 GeGLU-tanh, 16
Blackwell-only.

Validated on x86_64 only; the Rubin CI nodes are arm64. No Blackwell
code path is touched (the Rubin kernel is only selected for cc 10.7).

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Rubin grouped matrix operations now support SwiGLU, SiTU, and Relu2
activation options.
* SiTU supports configurable beta values, including an optional clamp
for its up branch.
* Relu2 preserves the output width, while gated activations use a
reduced output width.
* Locality-domain half-GEMM is available for gated activations; the
previous option remains supported for compatibility.
* **Bug Fixes**
* Rubin tuning can now consider Relu2 instead of excluding it.
GeGLU-tanh remains unsupported.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Vincent Tombari <Vinnie6167@users.noreply.github.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [0be3eb2](https://github.com/flashinfer-ai/flashinfer/commit/0be3eb28ca78b3e6d8a9d125eab09a12e96940aa)

- **作者**: Stefano Castagnetta
- **时间**: 2026-10-02T18:07:04Z
- **提交信息**: Canonical-layout NVFP4 W4A16 MoE in CuTe DSL on SM12x (#5735)

## 📌 Description

Add a CuTe DSL NVFP4 W4A16 routed-MoE backend for SM120/SM121 that
consumes the same prepared NVFP4 expert weights and scales as the cuTile
W4A4 path, **without additional weight preparation or a second weight
copy**. Sharing one expert layout enables serving frameworks to select
W4A16 or W4A4 dynamically for each call, using W4A16 where avoiding
activation quantization helps (decode) and W4A4 where its throughput is
better (prefill).

Use it through the unified MoE API with `SM12xNvfp4Bf16Config` (runner
`SM12xNvfp4Bf16Runner`, backend key `sm12x_nvfp4_bf16`).
`prepare_weights` returns the cuTile NVFP4 view (`CuTileNvfp4Config` /
`CuTileNvfp4Bf16Config`): packed E2M1 weights, 128x4-swizzled E4M3 block
scales and per-expert FP32 global scales, which the kernel reads in
place. Listed next to `CuTileNvfp4Bf16Config`, `MoELayer` autotunes the
two per token bucket.

On **DGX Spark (SM121), Qwen3.8-Flash-Next MoE layer** (H=2560, I=640,
512 experts, top-10), the new backend achieves **1.36x versus Marlin,
1.24x versus the existing CuTe DSL W4A16 MoE and 2.06x versus cuTile
W4A16** at 1 token, and stays ahead of cuTile through 64 tokens. Timing
is the complete MoE layer (routing, both GEMMs, activation, combine),
CUDA graphs and cold L2, with preparation excluded. At large token
counts cuTile is faster, and `MoELayer` selects it there.

Small token counts run one persistent kernel (routing, GEMM1,
activation, GEMM2 and the router-weighted combine) with work-stealing
tile dispatch; larger counts use expert-sorted routing, per-expert tiled
GEMM1/GEMM2 and a BF16 finalize. Weights are decoded in registers from
128-bit loads, with split-K where the grid would otherwise be too small.
Not added to the default backend list, so default dispatch is unchanged.

Supports SwiGLU (default scalars) and ReLU2, any hidden and intermediate
size accepted by the cuTile NVFP4 view (multiples of 64, including
intermediate sizes that are not multiples of 128), per-expert `[E]`
global scales and BF16 activations. Expert parallelism and fused shared
experts are not supported. Kernels are specialized per token bucket; the
runner pads each call to the layer's hybrid bucket (padded rows reuse
row 0's experts with zero router weight), so JIT is bounded by the
bucket set and buckets must be warmed before CUDA graph capture. Routing
slots whose expert id is outside `[0, E)` (CUDA-graph padding, non-local
experts) contribute nothing. Scratch is allocated per runner and token
bucket (`allocate_workspace`), so layers never share it.

## Performance

### DGX Spark (SM121): complete MoE layer versus existing W4A16 MoE
backends

Complete routed-MoE layer with preparation excluded. CUDA graph replay,
cold L2 between replays, median of 100 replays, two alternating rounds,
SM clock locked at 1500 MHz (1475 MHz sustained). **Speedup = baseline
time / new backend time; higher is better.** All providers use the same
logical weights and routing and pass a full-output reference check.
Measured on the kernel before its final cleanup (dead branches and
research knobs removed, no functional change); the `MoELayer` table
below is on this PR's code.

| Tokens | New backend (us) | vs Marlin W4A16 | vs existing CuTe DSL
W4A16 | vs cuTile W4A16 |
| ---: | ---: | ---: | ---: | ---: |
| 1 | 159.2 | 1.36x | 1.24x | 2.06x |
| 2 | 280.5 | 1.18x | 1.10x | 2.06x |
| 4 | 496.9 | 1.09x | 1.09x | 1.39x |
| 8 | 929.8 | 1.03x | 1.19x | 1.32x |
| 16 | 1697.2 | 1.00x | 1.07x | 1.27x |
| 64 | 4313.3 | 1.00x | 1.03x | 1.23x |
| 256 | 6551.3 | 0.96x | 1.06x | 1.19x |
| 1024 | 17300.7 | 0.41x | 0.58x | 0.64x |

The out-of-range id handling and per-runner scratch were re-measured
against the previous head on the same node: within 1.5% at 1 to 256
tokens, and 1 to 3% slower at 1024 tokens, where `MoELayer` selects
cuTile.

<details>
<summary>All shapes: absolute timings in microseconds</summary>

Qwen3.8-Flash-Next (H=2560, I=640, 512 experts, top-10, SwiGLU):

| Tokens | New backend | Marlin | Existing CuTe DSL W4A16 | cuTile W4A16
|
| ---: | ---: | ---: | ---: | ---: |
| 1 | 159.2 | 217.0 | 197.5 | 327.6 |
| 2 | 280.5 | 331.8 | 307.6 | 576.5 |
| 4 | 496.9 | 542.6 | 540.1 | 691.5 |
| 8 | 929.8 | 956.6 | 1105.0 | 1227.7 |
| 16 | 1697.2 | 1701.9 | 1816.5 | 2153.8 |
| 32 | 2846.9 | 2826.6 | 2928.8 | 3488.4 |
| 64 | 4313.3 | 4295.3 | 4426.1 | 5299.5 |
| 128 | 5737.7 | 5671.3 | 5923.0 | 7049.9 |
| 256 | 6551.3 | 6317.0 | 6929.3 | 7774.3 |
| 1024 | 17300.7 | 7055.8 | 9987.4 | 11096.8 |

Qwen3.6-35B-A3B (H=2048, I=512, 256 experts, top-8, SwiGLU):

| Tokens | New backend | Marlin | Existing CuTe DSL W4A16 | cuTile W4A16
|
| ---: | ---: | ---: | ---: | ---: |
| 1 | 100.8 | 146.6 | not supported (tile config) | 174.0 |
| 4 | 287.7 | 324.5 | 307.9 | 406.9 |
| 16 | 915.8 | 858.0 | 872.9 | 1025.5 |
| 64 | 1770.4 | 1742.3 | 1774.5 | 2044.0 |

Nemotron-3.5 (H=2688, I=1856, 128 experts, top-6, ReLU2):

| Tokens | New backend | Marlin | Existing CuTe DSL W4A16 | cuTile W4A16
|
| ---: | ---: | ---: | ---: | ---: |
| 1 | 244.6 | 242.2 | 221.5 | 312.5 |
| 16 | 2040.6 | 1607.6 | 1617.3 | 2077.7 |

The new backend is decode-oriented: it leads at small token counts on
the SwiGLU shapes, is at parity with Marlin from about 16 tokens, and
trails at 1024 tokens and on the Nemotron ReLU2 shape.

Marlin: vLLM `fused_marlin_moe` NVFP4 path (repacked weights). Existing
CuTe DSL W4A16: `B12xW4A16Config` (repacked weight cache). cuTile W4A16:
`CuTileNvfp4Bf16Config`, autotuned. Torch 2.13.0+cu130, CuTe DSL 4.7.1.

</details>

### DGX Spark (SM121): `MoELayer` cross-backend selection

Qwen3.8-Flash-Next MoE layer through `MoELayer` with both
`CuTileNvfp4Bf16Config` and `SM12xNvfp4Bf16Config` listed, median over
two rounds, CUDA graph replay with L2 warm across replays, SM clock
locked at 1500 MHz (1495 MHz sustained).

| Tokens | cuTile W4A16 (us) | New backend (us) | Speedup | Autotuned
winner |
| ---: | ---: | ---: | ---: | --- |
| 1 | 233.7 | 89.2 | 2.62x | sm12x_nvfp4_bf16 |
| 2 | 454.6 | 228.2 | 1.99x | sm12x_nvfp4_bf16 |
| 4 | 683.3 | 475.6 | 1.44x | sm12x_nvfp4_bf16 |
| 8 | 1183.5 | 897.9 | 1.32x | sm12x_nvfp4_bf16 |
| 16 | 2122.0 | 1663.2 | 1.28x | sm12x_nvfp4_bf16 |
| 64 | 5297.8 | 4328.5 | 1.22x | sm12x_nvfp4_bf16 |
| 1024 | 10986.5 | 17095.3 | 0.64x | cutile_nvfp4 |

`MoELayer` selects the faster backend in every row (within 0.3%).
Outputs of the two backends agree to 5.2e-4 maximum absolute difference.

FlashInfer foundation: `fdb08a89`. Torch 2.13.0+cu130, cuda-tile 1.6.0,
CuTe DSL 4.7.1.

## 🧪 Tests

SM121 validation covers **37 new tests**: reference match for
Qwen3.8-Flash-Next at 1, 3 (padded to a bucket), 16 and 128 tokens and
for **every MoE geometry in `benchmarks/samples/sample_testlist.txt`**
at its listed token count (including ReLU2 with I=1856, H=7168, Mixtral
I=14336 and top-22); CUDA graph capture then replay with new hidden
states and new routing; pointer equality between the kernel's
weight/scale tensors and the prepared cuTile view, including a view
registered only under `"cutile_nvfp4"`; `MoELayer` with both candidates;
out-of-range expert ids (`-1` and `E`) contributing nothing, including
when the fallback expert overflows FP16; and two layers of the same
geometry interleaved on two streams returning the reference result. The
**39 existing cuTile NVFP4 tests** still pass.

```bash
pytest tests/moe/test_unified_moe_cutile.py -k sm12x -v
pytest tests/moe/test_unified_moe_cutile.py -k "nvfp4 and not sm12x" -v
```

## 🔍 Related Issues

Builds on the cuTile NVFP4 MoE (#4646, #5099), whose prepared view it
shares. Pairs with the dense canonical-layout W4A16 backend (#5242).
[vLLM #54617](https://github.com/vllm-project/vllm/pull/54617) will
consume it for per-call W4A4/W4A16 MoE selection. Duplicate checks found
no equivalent canonical-layout W4A16 MoE proposal.

## 🚀 Pull Request Checklist

- [x] Pre-commit installed; changed-file hooks passed.
- [ ] Complete upstream GPU CI, which requires maintainer authorization.

AI assistance was used for implementation, experiments and drafting.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added SM120/SM121 support for routed MoE inference with NVFP4 weights
and BF16 activations, including SwiGLU and ReLU².
  * Added a unified API and MoE layer backend selection for this option.
* Added a benchmark case for the Qwen3.8 Flash Next NVFP4 W4A16 decode
workload.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Stefano Castagnetta <scastagnetta@nvidia.com>

### [77904ba](https://github.com/flashinfer-ai/flashinfer/commit/77904ba805cc769d3400e30a9c3e934d458d90dd)

- **作者**: Mingyang Wang
- **时间**: 2026-10-02T17:47:56Z
- **提交信息**: fix(mla): prefer measured SM12x backends and guard cuTile CTA tiles (#5896)

<!-- .github/pull_request_template.md -->

## 📌 Description

Make planned MLA auto-selection explicitly prefer FA2, XQA, then opt-in
cuTile on SM120/SM121. Suppress the poor-performance FA2 warning on
those architectures, where measurements favor FA2. Architecture policies
now express preferences over the complete concrete-backend list, so
typed unsupported results can reach other eligible implementations. The
default order is FA2, FA3, TRT, monolithic CuTe, modular CuTe, CUTLASS,
XQA, cuTile; existing SM100 leading preferences and predicates are
preserved.

Also prevent cuTile NaNs on SM120/SM121 by using one CTA for computed
head/key tiles 64×8, 128×8 and 128×16. Other tiles retain their existing
CTA selection. Add coverage for architecture/toolchain routing, fallback
contracts and CTA configuration boundaries while keeping explicit
selection, experimental opt-in, unexpected-error propagation and graph
backend retention intact.

## 🔍 Related Issues

Related: #4031. Follow-up to #5712.

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

Changed-file pre-commit hooks passed for all four modified files. The
whole-repository `--all-files` checkbox is left unchecked because
validation was scoped to the changed files.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

Targeted validation on RTX 5080 (SM120) and GB10 (SM121): **309 passed,
32 architecture skips on each GPU**, using:

```sh
python -m pytest -q tests/attention/test_mla_auto_backend.py tests/attention/test_mla_auto_backend_warning.py tests/attention/test_mla_decode_cutile.py::test_cutile_configuration_cta_guards
```

Separate native FP16/BF16 eager/graph probes reproduced two-CTA NaNs for
the guarded tiles on both GPUs and passed with one CTA. The permanent
regression tests assert configuration selection; the standalone
numerical probes are not added to this PR. The full repository test
suite was not run.

A fresh bounded comparison after rebasing onto `08776e742` used six
fixed `(batch, heads, page, KV length)` tuples, each FP16/BF16 and
eager/graph: `(16,64,16,3247)`, `(16,128,32,3247)`, `(64,64,16,8192)`,
`(64,128,32,8192)`, `(16,128,128,8192)`, `(64,128,128,1024)`. Q1 decode,
CKV512/KPE64, causal, default scales, no LSE. Compare FA2, current
two-CTA cuTile and the same configuration forced to one CTA; six
balanced rounds, 100 warm-L2 CUDA-event samples per role, independent
FP32 correctness checks before timing, planning/JIT excluded. All 432
measured and 72 preparation rows per GPU passed correctness.

| GPU / representative case | FA2 | cuTile, one CTA | cuTile, two CTAs |
| --- | ---: | ---: | ---: |
| RTX 5080, B64/H128/page32/KV8192, FP16 eager | 3.642 ms | 38.290 ms |
21.890 ms |
| GB10, B64/H128/page32/KV8192, BF16 graph replay | 4.175 ms | 67.705 ms
| 29.152 ms |

These are the closest sampled cuTile cases to FA2. Across all 24
shape/mode comparisons per GPU, current cuTile was 6.0–16.6× slower than
FA2 on RTX 5080 and 7.0–11.6× slower on GB10. Two CTAs improved cuTile
over one CTA in 16/24 comparisons on each GPU and worsened it in eight.
This supports retaining FA2 first in the measured scope, not a universal
speedup claim.

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

The complete fallback tails are an intentional behavior change.
Backend-owned support checks remain authoritative; only typed
unsupported results advance to another backend. cuTile automatic
selection still requires
`FLASHINFER_ALLOW_EXPERIMENTAL_AUTO_BACKENDS=1`.

Nondefault-scale, FP8, layout and LSE oracle coverage remains
incomplete. The broader SM121 core campaign stopped at its predeclared
confirmation bound with 93 inconclusive comparisons and no confirmed
regression; this is not proof of universal noninferiority. Native
SM100/Hopper cases were skipped on the measured GPUs; routing contracts
and preserved SM100 preference tests cover the local policy logic. No
kernel implementation was changed.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Improvements**
* Automatic MLA backend selection now supports SM120 and SM121 GPUs,
with architecture- and workload-specific backend preferences across
supported devices.
* For other unmatched architectures, automatic selection tries the
shared default backend order rather than only FA2.
* Some cuTile configurations on SM120 and SM121 now use a fixed CTA
count for specified tile sizes.
* Fallback warnings now describe trying the default backend order and
are not issued for SM120 and SM121.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [11e1884](https://github.com/flashinfer-ai/flashinfer/commit/11e188412d119dbf5f1d5fea8e22ea76bd1f6294)

- **作者**: Bo Li
- **时间**: 2026-10-02T15:42:27Z
- **提交信息**: refactor(moe_ep): add a MoE-level communication interface for EP dispatch/combine (#5532)

<!-- .github/pull_request_template.md -->

## 📌 Description

MoE expert-parallel (EP) communication in FlashInfer is currently spread
across unrelated entry points:
- `flashinfer.comm.MoeAlltoAll`: NVLink one-sided, with a
`backend="trtllm" | "cake"` switch since #4784;
- `flashinfer.comm.MnnvlMoe`: NVLink two-sided;
- `flashinfer.moe_ep`'s `Fleet`/`Handle`: NCCL-EP / NIXL-EP.

This PR brings the NVLink backends into the MoE EP API as split-path
comm backends under `flashinfer/moe_ep/backends/split/comm/`, so users
pick one of several comm backends and one of several compute kernels
through `SplitConfig`. It is the interface step; porting the updated
NVLink one-sided kernels from TensorRT-LLM will follow on top of it.

### Architecture

```
MoEEpLayer(backend=SplitConfig(comm=..., kernel=...))
└─ MoEEpSplitLayer: dispatch → inner kernel (identity | fused_moe) → combine
   ├─ MoEEpCommunication (core/comm/communication.py): self-contained dispatch/combine objects
   │   ├─ nvlink_one_sided       NVLinkOneSidedAlltoAll      (MoeAlltoAll, TRT-LLM kernels)
   │   ├─ cake                   CakeAlltoAll                (MoeAlltoAll, generated Cake kernels, SM100/SM103)
   │   └─ nvlink_two_sided       NVLinkTwoSidedAlltoAll      (MnnvlMoe all-to-all-v)
   └─ Fleet / Handle (core/comm/fleet.py, handle.py): native group / per-step-handle API
       ├─ nccl_ep
       └─ nixl_ep
```

The two comm interfaces are peers that differ in object model, not in
role. In `Fleet` / `Handle`, a step's routing is a separate `Handle`
object. A `MoEEpCommunication` takes the routing with each `dispatch`.
Both register the same way: `@register_fleet(name)` and
`@register_communication(name)`.

Every `MoEEpCommunication` backend implements one rank-major contract:
- `dispatch(hidden_states, topk_ids, topk_weights, *,
hidden_states_scale=None, max_tokens_per_rank=None,
eplb_local_stats=None)` returns `ep_size * tokens_per_rank` receive rows
with global top-k ids. Rows without a token carry `invalid_expert_id`.
- The expert computation weights and reduces over the rank's local
experts.
- `combine(expert_output, *, output=None)` sums each token's per-rank
results on its source rank.
- `get_combine_input_buffer(dtype)` optionally returns a zero-copy
combine buffer (one-sided).

Backend-specific conventions are normalized inside each backend. For
example, two-sided marks padding rows with `num_experts`, which is
remapped to `invalid_expert_id`.

Backends register with `register_communication` and are created by
`create_communication(bootstrap, MoEEpCommParams(...),
backend=<config>)`, or by `MoEEpSplitLayer` from
`SplitConfig(comm=NVLinkOneSidedConfig())`. The split layer requires
`FleetParams(algorithm=LOW_LATENCY, layout=RANK_MAJOR)` for these
backends.

### Split layer: two peer comm paths

`MoEEpSplitLayer` runs a comm backend on one of two self-contained
paths, one per interface:
- `_fleet_*` methods for Fleet/Handle backends;
- `_communication_*` methods for `MoEEpCommunication` backends.

Each path has its own config validation, lazy transport creation,
graph-state creation, forward, and dispatch → compute → combine. Each
turns its dispatch output into the same `SplitKernelContext`, so the
inner kernels are shared. `forward` / `create_graph_state` do the shared
checks, then hand off to the backend's path.

Paths are chosen by registry. A backend must be registered as exactly
one kind; one registered as neither or both is rejected at construction,
whereas before it fell through to the Fleet path. Per-stage timing
(`enable_timing`) is one shared helper.

The Fleet registry is renamed `_BACKEND_REGISTRY` → `_FLEET_REGISTRY`.
`nccl_ep` / `nixl_ep` register through the new `@register_fleet`
decorator. Behavior is unchanged for registered backends.

### Workspace sizing by dispatch format

`MoEEpCommParams.dispatch_format` names the
`flashinfer.fused_moe.QuantFormat` the activations are dispatched in:
BF16, FP8PerTensor, MXFP8, NVFP4, MXFP4, or DeepSeekFp8; `None` means
unquantized `dtype` rows. The one-sided backend sizes its dispatch
region from it (values plus per-block scales, plus ids/weights), and
sizes the combine region by `dtype`. Callers describe the format instead
of computing byte counts.

### CUDA graphs

- `MoEEpSplitLayer.create_graph_state()` / `forward(graph_state=...)`
now also cover `MoEEpCommunication` backends. The communication object
is long-lived, so the graph state only pins the bound buffers.
- `create_graph_state()` rejects backends with
`supports_cuda_graph=False`.
- Fleet transports keep their persistent-handle graph state.

### Platform checks

- NVLink backends agree on platform support across the EP group before
any symmetric memory is allocated. An unsupported rank logs its reason,
and all ranks raise together instead of leaving peers waiting.
- `MnnvlMemory.support_nvlink()` now initializes NVML itself, so
`supports_mnnvl()` works before `MnnvlMemory.initialize()`.

### Deprecations

- `MoeAlltoAll` and `MnnvlMoe` are marked deprecated
(`typing_extensions.deprecated`) in favor of `NVLinkOneSidedAlltoAll` /
`CakeAlltoAll` and `NVLinkTwoSidedAlltoAll`. Their implementations will
move into those classes rather than being wrapped by them.
- The new backends still build on them and suppress that warning
internally, so only direct users see it.
- The functional `moe_a2a_*` ops are unchanged.

### Benchmarks

All moe_ep benchmarks now live under `benchmarks/moe_ep/`, mirroring
`flashinfer/moe_ep/` the way `benchmarks/comm/` mirrors
`flashinfer/comm/`:

```
benchmarks/moe_ep/
├── bench_moe_ep.py                  MoEEpLayer (layer.py)
├── MoE_benchmarks.md
├── core/comm/
│   ├── bench_moe_ep_comm.py         MoEEpCommunication (new)
│   ├── bench_ep_matrix.py           Fleet/Handle (NCCL-EP)
│   └── run_ep_matrix{,_one,_one_pt}.sh
└── backends/mega/kernel/
    ├── sm100/bench_bf16_cutedsl_megamoe.py
    ├── sm107/bench_moe_ep_sm107_block_scaled_mega.py
    └── sm90/bench_moe_ep_sm90_mega.py
```

Docs, kernel TUNING notes and tests point to the new paths.

The new `benchmarks/moe_ep/core/comm/bench_moe_ep_comm.py` times
`dispatch()`/`combine()` of any `MoEEpCommunication` backend under
torchrun:
- sweeps local batch sizes over model profiles (DeepSeek-V3/V4, GPT-OSS,
Kimi-K3, ...);
- replays warmup and timed iterations in one CUDA graph;
- reports per-phase CUPTI kernel spans (needs `cupti-python>=13.4`; it
falls back to CUDA events otherwise), with an optional per-kernel
breakdown.

Activations are quantized to the dispatched format by self-contained
PyTorch reference quantizers outside the timed region.

```bash
torchrun --nproc-per-node=8 benchmarks/moe_ep/core/comm/bench_moe_ep_comm.py \
    --backend nvlink_one_sided --profile deepseek_v4_pro -b 1 -e 1024 -f 2
```

## 🔍 Related Issues

Follow-up to #4784 (Cake MoE all-to-all backend).

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually and fixed any reported issues (run
on the changed files).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

Validated on 4x B300:
- `tests/moe_ep/test_moe_ep_communication_multirank.py` (`bash
tests/moe_ep/run_tests.sh comm`), 7 passed:
- dispatch → synthetic expert computation → combine against a local
reference for one-sided, Cake and two-sided;
  - `MoEEpLayer` end to end over one-sided;
- split-layer CUDA-graph capture over all three backends, replaying
inputs rewritten in place.
- `tests/moe_ep/test_communication.py` (host-only, kernels/transports
stubbed), 19 passed. It covers parameter validation, the registry,
dispatch-format sizing, split-layer path selection and graph states,
payload plumbing, and the Cake platform check.
- The moe_ep unit suite plus the related `tests/comm` tests pass (890
passed, 101 skipped).
- All moved benchmarks import and parse arguments from their new paths.
The SM107 tuning test, which loads its bench by path, passes.
`bench_moe_ep_comm.py` runs from its new path with unchanged results.
- `bench_moe_ep_comm.py` sweeps with MXFP8 and NVFP4 dispatch run all
three NVLink backends in CUDA-graph mode at full capacity, with CUPTI
kernel spans.

Not yet validated on GPU:
- NVLink comm combined with `fused_moe` compute;
- the Fleet/Handle path against real NCCL-EP / NIXL-EP after the
split-layer restructuring (`nccl.ep` / `nixl_ep` are not installed on
the test machine; covered by stub transports only).

## Reviewer Notes

- NCCL-EP is not wrapped in `MoEEpCommunication`. Engines and the split
layer use its Fleet/Handle API directly, which covers its full feature
set, including persistent-handle CUDA-graph capture. An earlier
revision's `NcclEpCommunication` wrapper was dropped after discussion
with the moe_ep owners.
- Open questions for the moe_ep owners, deliberately out of scope here:
- `MoEEpLayer(bootstrap, fleet_params, weights, fleet_knobs, ...)`
describes every split layer in Fleet vocabulary. The
`MoEEpCommunication` path derives its parameters from `FleetParams` and
requires `algorithm=LOW_LATENCY, layout=RANK_MAJOR`. A neutral
layer-level parameter set would make the two paths fully symmetric.
- `SplitKernelContext` takes local expert ids, with -1 for non-local
picks. The `MoEEpCommunication` path converts its global ids to that
form, and the fused_moe bridge converts them back to global ids.
- The move under `benchmarks/moe_ep/` includes owner-maintained
benchmarks and harness scripts (`bench_ep_matrix.py`,
`run_ep_matrix*.sh`, the mega benches, `MoE_benchmarks.md`). Their
contents are unchanged except paths. The SM90 bench now derives the
repository root from its new depth for `--output-csv auto`.
- `bench_moe_ep.py` (split-layer bench) still lists only `nccl_ep` /
`nixl_ep`; adding the NVLink backends there is a small follow-up.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added MoE expert-parallel communication backends for NVLink one-sided
and two-sided transfers, Cake, and NCCL-EP, with shared dispatch and
combine support.
* Added a benchmark for comparing communication backend performance
across payload formats and routing patterns.
* **Documentation**
  * Expanded backend setup, configuration, and CUDA graph guidance.
* Marked older all-to-all interfaces as deprecated and documented
recommended replacements.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Bo Li <22713281+bobboli@users.noreply.github.com>

### [1b578de](https://github.com/flashinfer-ai/flashinfer/commit/1b578de52924c973bd229fe4fd147499ead2781d)

- **作者**: eigen
- **时间**: 2026-10-02T09:19:34Z
- **提交信息**: perf(cake_mm_fp4): stream-K stripe tail for the partial last wave of the per-token NVFP4 2-CTA GEMM (SM100) (#5944)

## Summary

`mm_fp4(..., backend="cake")` per-token NVFP4: the static 2-CTA
persistent GEMM now shares its partial last wave. Each tail tile is cut
into `S` equal K slices held by `S` consecutive CTA pairs; every holder
publishes the output subtiles it does not own (FP32, coalesced), bumps a
per-slot generation flag, waits for its siblings to reach the same
generation and sums its owned subtiles in fixed K-slice order (`((P0 +
P1) + ...) + P_last`, own slice straight from TMEM). No atomics, no
arrival-order dependence, no flag resets. The host (`stream_k_tail`)
runs the sliced program only where at least three slices fit; every
other row keeps its previous program and key (bitwise identical output).

Changes to the public API: none (no new operator, parameter, default or
backend semantics).

## Speedup (paired, 6 x 100 cold-L2 CUPTI medians, vs the current cake
programs)

| row (B200, 148 SMs) | tail tiles / slices | before us | after us |
speedup |
|---|---|---|---|---|
| K=16384 N=7168 M=2048 | 8 / 6 | 88.77 | 81.53 | 1.089 |
| K=18432 N=7168 M=2048 | 8 / 6 | 99.07 | 90.21 | 1.098 |
| K=8192 N=28672 M=257 | 4 / 6 | 48.83 | 48.00 | 1.017 |
| K=8192 N=28672 M=512 | 4 / 6 | 51.10 | 49.95 | 1.023 |

GB300 (152 SMs): no validated row has a shareable tail (40 or 72 tail
tiles over 76 pairs); every program is unchanged (null A/B 1.000-1.005).

### Export-arm tables (delivered programs vs the #5869 programs and vs
`backend="cute-dsl"` untuned; 6 x 100 cold-L2 CUPTI, rows below the band
re-measured at 12 x 100 and merged; roof = share of the measured HBM /
dense-FP4 peak)

<details><summary>B200 (148 SMs)</summary>

#### GEMM per-token — vs #5869: bf16 rows 80, geomean 1.0022, min
0.9971, rows <= 1.00: 58; fp16 rows 80, geomean 1.0023, min 0.9958, rows
<= 1.00: 61. vs cute-dsl: bf16 rows 80, geomean 1.0590, min 0.9855, rows
<= 1.00: 2; fp16 rows 80, geomean 1.0592, min 0.9838, rows <= 1.00: 2

|K|N|M|tactic|vs #5869 bf16|vs #5869 fp16|vs cute-dsl bf16|vs cute-dsl
fp16|roof (share of measured peak; Nf = N x launch floor)|
|---|---|---|---|---|---|---|---|---|

|7168|2112|1|n8sk4|1.000(1.000/1.000)|1.000(1.005/1.000)|1.037(1.037/1.035)|1.026(1.042/1.038)|22%h
4.1f|

|7168|2112|8|n8sk4|1.005(1.000/1.004)|1.000(1.000/1.001)|1.026(1.037/1.036)|1.042(1.031/1.032)|22%h
4.1f|

|7168|2112|17|n8sk2|1.000(1.000/1.000)|1.000(1.000/1.000)|1.030(1.025/1.028)|1.025(1.025/1.024)|21%h
4.4f|

|7168|2112|32|n8sk2|1.000(1.000/1.001)|1.000(1.000/1.001)|1.029(1.034/1.031)|1.029(1.034/1.032)|21%h
4.5f|

|7168|2112|128|2xm64|1.000(1.000/1.000)|1.000(0.996/0.998)|1.102(1.103/1.104)|1.102(1.098/1.100)|19%h
5.3f|

|7168|2112|130|2xm64|1.000(1.000/1.000)|1.000(1.000/1.000)|1.085(1.089/1.088)|1.089(1.089/1.089)|19%h
5.4f|

|7168|2112|257|2xm64|1.000(1.000/1.001)|0.996(1.000/1.000)|1.050(1.046/1.047)|1.046(1.046/1.045)|20%h
5.7f|

|7168|2112|512|2xm64|1.000(1.000/1.000)|1.000(1.000/0.999)|1.048(1.044/1.046)|1.045(1.044/1.045)|25%c
5.8f|

|7168|2112|2048|2xm256|0.998(1.000/0.999)|1.002(1.000/1.001)|1.039(1.039/1.039)|1.039(1.039/1.039)|57%c|

|7168|2112|8192|2xm192g8|0.999(0.999/0.999)|1.000(1.000/1.000)|1.045(1.047/1.046)|1.046(1.047/1.047)|76%c|

|7168|1536|1|n8sk4|1.000(1.000/1.000)|1.000(1.000/0.999)|1.023(1.023/1.024)|1.023(1.022/1.023)|17%h
3.9f|

|7168|1536|8|n8sk4|1.000(1.000/1.001)|1.000(1.000/0.998)|1.017(1.017/1.017)|1.017(1.017/1.017)|17%h
4.0f|

|7168|1536|17|n8sk3|1.000(0.994/0.999)|1.005(1.000/1.000)|1.102(1.107/1.105)|1.102(1.107/1.103)|17%h
3.9f|

|7168|1536|32|n8sk2|1.000(1.005/1.002)|1.000(1.000/1.001)|1.037(1.037/1.038)|1.043(1.037/1.040)|16%h
4.2f|

|7168|1536|128|2xm64|1.000(1.000/1.000)|0.996(1.000/1.000)|1.079(1.087/1.085)|1.088(1.087/1.088)|15%h
5.2f|

|7168|1536|130|2xm64|1.000(1.000/1.001)|1.000(1.000/1.000)|1.066(1.066/1.066)|1.066(1.066/1.066)|14%h
5.3f|

|7168|1536|257|2xm64|1.000(1.000/0.998)|0.996(1.000/0.999)|1.044(1.044/1.043)|1.044(1.044/1.042)|15%h
5.5f|

|7168|1536|512|2xm64|1.000(1.000/0.999)|1.000(1.000/0.999)|1.039(1.043/1.042)|1.043(1.043/1.042)|19%h
5.7f|

|7168|1536|2048|2xm192|1.000(1.000/1.001)|1.000(0.997/0.999)|1.048(1.045/1.047)|1.045(1.045/1.045)|51%c|

|7168|1536|8192|2xm256g8|1.000(1.000/1.000)|1.000(1.000/1.000)|1.073(1.073/1.073)|1.073(1.072/1.073)|70%c|

|16384|7168|1|n8sk2|1.000(1.000/1.000)|0.998(1.002/1.000)|1.116(1.118/1.116)|1.118(1.118/1.117)|68%h|

|16384|7168|8|n8sk2|1.000(1.000/1.000)|1.000(0.998/1.000)|1.118(1.118/1.118)|1.116(1.116/1.116)|68%h|

|16384|7168|17|n32sk2|1.002(1.002/1.002)|1.000(1.000/1.005)|1.148(1.143/1.148)|1.148(1.148/1.148)|66%h|

|16384|7168|32|n32sk2|1.000(1.000/1.000)|1.000(0.998/1.000)|1.141(1.145/1.145)|1.145(1.143/1.145)|66%h|

|16384|7168|128|m64|1.002(1.000/1.000)|1.000(1.000/1.000)|1.018(1.016/1.017)|1.016(1.016/1.016)|61%h|

|16384|7168|130|2xm128|1.000(1.000/1.000)|1.000(0.998/0.999)|1.048(1.048/1.048)|1.046(1.048/1.048)|58%h|

|16384|7168|257|2xm256|1.001(1.000/1.001)|1.000(1.000/1.000)|1.038(1.038/1.038)|1.036(1.036/1.037)|43%h|

|16384|7168|512|2xm256|1.000(1.000/1.000)|1.000(1.000/1.000)|1.039(1.041/1.041)|1.041(1.042/1.042)|61%c|

|16384|7168|2048*|2xm192|1.079(1.079/1.079)|1.078(1.078/1.078)|1.142(1.142/1.142)|1.142(1.143/1.143)|80%c|

|16384|7168|8192|2xm256g16clc|1.001(0.996/0.980)|1.005(0.996/1.003)|1.128(1.124/1.108)|1.125(1.125/1.124)|90%c|

|7168|18432|1|n8s3|1.002(1.000/1.000)|1.002(1.000/1.000)|1.029(1.025/1.026)|1.027(1.023/1.025)|72%h|

|7168|18432|8|n8s3|1.000(1.000/1.000)|0.998(1.000/0.998)|1.031(1.029/1.029)|1.027(1.027/1.028)|72%h|

|7168|18432|17|n32s3|1.002(1.000/1.001)|1.000(1.000/1.001)|1.014(1.012/1.012)|1.010(1.012/1.011)|72%h|

|7168|18432|32|n32s3|0.998(1.000/1.000)|0.998(1.002/1.001)|1.008(1.006/1.006)|1.012(1.006/1.008)|72%h|

|7168|18432|128|m128l2n|0.998(0.998/0.999)|1.002(1.000/1.001)|0.986(0.986/0.984)|0.984(0.984/0.984)|72%h|

|7168|18432|130|2xm256|1.000(1.000/1.000)|0.998(1.000/1.000)|1.031(1.029/1.030)|1.029(1.027/1.028)|68%h|

|7168|18432|257|2xm256|1.001(1.000/1.000)|1.000(1.000/1.000)|1.039(1.039/1.039)|1.041(1.039/1.039)|51%h|

|7168|18432|512|2xm256|0.999(1.000/1.000)|1.000(1.000/1.000)|1.038(1.038/1.037)|1.039(1.039/1.038)|68%c|

|7168|18432|2048|2xm256|1.000(1.000/1.000)|0.999(1.000/1.000)|1.036(1.036/1.036)|1.036(1.036/1.036)|86%c|

|7168|18432|8192|2xm256clc|1.002(1.004/1.014)|1.000(0.992/0.997)|1.032(1.039/1.034)|1.029(1.032/1.042)|89%c|

|18432|7168|1|n8|1.000(1.000/1.000)|1.000(1.000/1.000)|1.137(1.135/1.135)|1.135(1.138/1.137)|69%h|

|18432|7168|8|n8|1.000(1.000/1.001)|1.000(0.998/0.999)|1.135(1.136/1.135)|1.137(1.138/1.137)|69%h|

|18432|7168|17|n32sk2|0.998(1.000/1.001)|1.000(1.000/1.000)|1.151(1.150/1.152)|1.151(1.146/1.149)|66%h|

|18432|7168|32|n32sk2|1.000(1.000/1.001)|1.002(0.998/1.000)|1.144(1.144/1.145)|1.148(1.147/1.148)|66%h|

|18432|7168|128|m64|0.998(0.998/0.999)|0.998(0.998/1.000)|1.021(1.018/1.020)|1.023(1.024/1.023)|62%h|

|18432|7168|130|2xm128|1.000(1.000/1.001)|1.000(1.000/0.999)|1.052(1.052/1.052)|1.052(1.052/1.053)|59%h|

|18432|7168|257|2xm256|0.999(0.999/0.999)|1.001(1.001/1.001)|1.043(1.045/1.044)|1.044(1.044/1.044)|44%h|

|18432|7168|512|2xm256|1.000(1.000/1.000)|1.002(1.000/1.000)|1.050(1.052/1.051)|1.050(1.051/1.051)|62%c|

|18432|7168|2048*|2xm192|1.088(1.088/1.089)|1.089(1.089/1.089)|1.152(1.153/1.153)|1.151(1.152/1.152)|81%c|

|18432|7168|8192|2xm256g16clc|1.002(0.998/1.014)|0.998(1.003/1.006)|1.124(1.120/1.123)|1.132(1.126/1.121)|89%c|

|8192|8192|1|n8|1.000(0.997/0.999)|1.000(1.003/1.001)|1.009(1.012/1.011)|1.012(1.012/1.012)|55%h|

|8192|8192|8|n8|0.997(1.000/0.999)|1.000(1.000/1.000)|1.018(1.021/1.021)|1.021(1.021/1.021)|55%h|

|8192|8192|17|n32|0.997(1.000/0.999)|0.997(0.997/0.998)|1.018(1.018/1.018)|1.018(1.015/1.017)|54%h|

|8192|8192|32|n32|0.997(0.997/0.998)|0.997(1.000/0.999)|1.015(1.012/1.014)|1.015(1.015/1.014)|54%h|

|8192|8192|128|m64|1.000(1.000/1.000)|1.000(1.000/1.000)|1.008(1.008/1.010)|1.008(1.008/1.008)|54%h|

|8192|8192|130|2xm128|1.000(1.000/1.000)|1.000(1.000/1.000)|1.052(1.047/1.049)|1.049(1.049/1.048)|51%h|

|8192|8192|257|2xm256|1.000(1.000/1.000)|1.000(1.000/0.999)|1.045(1.047/1.046)|1.047(1.047/1.046)|41%h|

|8192|8192|512|2xm256|0.998(1.000/1.000)|0.998(1.002/1.001)|1.046(1.048/1.048)|1.050(1.048/1.048)|56%c|

|8192|8192|2048|2xm192|0.999(0.999/0.999)|0.999(0.999/0.999)|1.057(1.057/1.057)|1.058(1.057/1.057)|76%c|

|8192|8192|8192|2xm256g16clc|1.000(0.997/1.001)|1.000(1.000/0.999)|1.037(1.035/1.036)|1.036(1.036/1.031)|91%c|

|8192|28672|1|n8|1.000(1.000/1.000)|1.001(1.000/1.001)|0.999(0.999/0.999)|0.999(0.999/0.999)|83%h|

|8192|28672|8|n8|0.999(1.000/1.000)|1.000(1.000/1.001)|1.003(1.001/1.002)|1.008(1.008/1.007)|83%h|

|8192|28672|17|n32|1.001(1.001/1.002)|1.000(1.000/1.002)|1.009(1.010/1.013)|1.010(1.010/1.012)|84%h|

|8192|28672|32|n32|1.001(1.000/1.001)|0.999(1.001/1.000)|1.013(1.013/1.012)|1.009(1.010/1.010)|84%h|

|8192|28672|128|m128|0.999(1.001/1.000)|1.000(1.000/1.000)|1.028(1.027/1.027)|1.028(1.027/1.027)|77%h|

|8192|28672|130|2xm256|1.001(1.000/1.000)|1.001(0.999/1.000)|1.032(1.034/1.033)|1.031(1.032/1.032)|71%h|

|8192|28672|257*|2xm192|1.011(1.011/1.011)|1.012(1.011/1.012)|1.071(1.070/1.070)|1.069(1.070/1.070)|49%h|

|8192|28672|512*|2xm192|1.014(1.015/1.015)|1.015(1.016/1.016)|1.074(1.075/1.075)|1.075(1.075/1.075)|66%c|

|8192|28672|2048|2xm256clc|1.000(1.000/1.001)|1.000(0.999/0.997)|1.025(1.025/1.026)|1.026(1.026/1.025)|87%c|

|8192|28672|8192|2xm256clc|1.004(0.996/0.993)|1.012(1.002/0.995)|1.024(1.083/1.063)|1.018(1.039/1.047)|87%c|

|28672|8192|1|n8|1.000(1.001/1.000)|0.999(1.000/1.000)|1.183(1.182/1.183)|1.181(1.184/1.183)|82%h|

|28672|8192|8|n8|1.000(1.000/1.001)|0.999(0.999/1.000)|1.185(1.186/1.186)|1.186(1.186/1.186)|82%h|

|28672|8192|17|n32sk2|0.998(1.000/1.007)|1.001(1.000/1.007)|1.167(1.167/1.173)|1.168(1.174/1.175)|79%h|

|28672|8192|32|n32sk2|0.999(0.999/1.000)|1.000(1.000/1.000)|1.166(1.170/1.169)|1.167(1.166/1.168)|79%h|

|28672|8192|128|m64|0.998(1.000/0.999)|1.000(1.000/1.000)|1.018(1.017/1.018)|1.016(1.017/1.017)|74%h|

|28672|8192|130|2xm128|0.998(1.000/1.000)|1.002(1.001/1.001)|1.044(1.042/1.042)|1.042(1.042/1.042)|71%h|

|28672|8192|257|2xm256|1.001(1.000/1.000)|1.001(1.001/1.000)|1.043(1.043/1.044)|1.044(1.045/1.044)|52%h|

|28672|8192|512|2xm256|1.000(1.001/1.000)|0.999(0.999/0.999)|1.058(1.060/1.059)|1.060(1.060/1.060)|75%c|

|28672|8192|2048|2xm192|0.999(0.997/0.996)|1.000(0.997/0.997)|1.051(1.051/1.053)|1.051(1.050/1.048)|86%c|

|28672|8192|8192|2xm256g8clc|0.998(0.997/1.003)|0.996(0.978/0.974)|1.099(1.109/1.105)|1.098(1.104/1.099)|87%c|

#### Fused quantize + GEMM chain (CUDA-graph replay, PDL edge included)
— vs #5869: bf16 rows 80, geomean 1.0035, min 0.9916, rows <= 1.00: 41;
fp16 rows 80, geomean 1.0042, min 0.9968, rows <= 1.00: 33. vs cute-dsl
(bf16): rows 80, geomean 1.0893, min 1.0115, rows <= 1.00: 0

|K|N|M|GEMM tactic|vs #5869 bf16|vs #5869 fp16|vs cute-dsl bf16|
|---|---|---|---|---|---|---|

|7168|2112|1|n8sk4|1.017(1.026/1.020)|1.017(1.026/1.018)|1.140(1.190/1.172)|

|7168|2112|8|n8sk4|1.004(1.008/1.002)|1.004(1.004/1.003)|1.110(1.142/1.138)|

|7168|2112|17|n8sk2|1.004(1.008/1.005)|1.004(1.008/1.004)|1.114(1.140/1.130)|

|7168|2112|32|n8sk2|1.004(1.004/1.003)|1.000(1.004/1.004)|1.109(1.134/1.137)|

|7168|2112|128|2xm64|1.000(0.994/0.996)|1.000(0.994/0.995)|1.143(1.150/1.147)|

|7168|2112|130|2xm64|1.006(1.016/1.010)|1.003(1.016/1.010)|1.131(1.156/1.146)|

|7168|2112|257|2xm64|1.000(0.997/0.996)|0.997(0.994/0.995)|1.115(1.125/1.118)|

|7168|2112|512|2xm64|1.005(1.011/1.009)|1.005(1.011/1.008)|1.126(1.150/1.141)|

|7168|2112|2048|2xm256|1.006(0.976/0.985)|1.006(0.987/0.994)|1.232(1.220/1.222)|

|7168|2112|8192|2xm192g8|1.001(1.002/1.002)|1.004(1.002/1.003)|1.057(1.058/1.058)|

|7168|1536|1|n8sk4|1.004(0.991/0.998)|1.000(0.991/0.998)|1.163(1.152/1.158)|

|7168|1536|8|n8sk4|0.996(0.987/0.989)|1.000(0.987/0.993)|1.118(1.107/1.115)|

|7168|1536|17|n8sk3|1.005(1.000/1.003)|1.013(1.004/1.004)|1.130(1.142/1.144)|

|7168|1536|32|n8sk2|1.000(0.996/1.001)|1.008(0.984/1.000)|1.129(1.143/1.132)|

|7168|1536|128|2xm64|0.997(0.987/0.992)|0.997(0.990/0.992)|1.109(1.093/1.099)|

|7168|1536|130|2xm64|1.000(0.994/0.992)|1.000(0.990/0.991)|1.098(1.080/1.082)|

|7168|1536|257|2xm64|0.997(0.985/0.995)|0.997(0.985/0.995)|1.075(1.073/1.078)|

|7168|1536|512|2xm64|1.017(1.020/1.017)|1.017(1.017/1.016)|1.119(1.125/1.122)|

|7168|1536|2048|2xm192|1.000(1.002/1.001)|1.003(1.002/1.001)|1.202(1.214/1.207)|

|7168|1536|8192|2xm256g8|0.999(0.998/0.998)|1.001(0.999/0.999)|1.084(1.084/1.085)|

|16384|7168|1|n8sk2|1.004(1.011/1.010)|1.000(1.013/1.011)|1.118(1.121/1.119)|

|16384|7168|8|n8sk2|0.996(1.005/1.000)|1.000(1.004/1.005)|1.105(1.094/1.095)|

|16384|7168|17|n32sk2|0.996(0.993/0.995)|0.998(0.996/0.997)|1.133(1.123/1.126)|

|16384|7168|32|n32sk2|1.000(1.007/1.001)|0.998(1.005/1.001)|1.138(1.153/1.148)|

|16384|7168|128|m64|1.008(1.003/1.003)|1.006(1.005/1.003)|1.043(1.048/1.045)|

|16384|7168|130|2xm128|1.002(1.000/1.000)|0.997(1.001/0.999)|1.080(1.098/1.092)|

|16384|7168|257|2xm256|1.000(1.000/1.001)|1.002(1.001/1.001)|1.035(1.028/1.032)|

|16384|7168|512|2xm256|0.995(0.993/0.994)|0.998(0.989/0.991)|1.080(1.084/1.084)|

|16384|7168|2048*|2xm192|1.066(1.064/1.065)|1.068(1.065/1.066)|1.184(1.185/1.185)|

|16384|7168|8192|2xm256g16clc|1.004(1.013/1.010)|0.997(1.005/1.000)|1.123(1.138/1.124)|

|7168|18432|1|n8s3|1.000(1.004/1.002)|0.998(1.004/1.002)|1.072(1.084/1.078)|

|7168|18432|8|n8s3|1.000(1.007/1.006)|1.004(1.007/1.005)|1.066(1.075/1.074)|

|7168|18432|17|n32s3|1.004(1.002/1.002)|1.002(1.004/1.003)|1.037(1.049/1.043)|

|7168|18432|32|n32s3|1.005(1.003/1.005)|1.005(1.003/1.005)|1.062(1.060/1.061)|

|7168|18432|128|m128l2n|0.997(0.997/0.998)|1.002(0.998/0.999)|1.028(1.028/1.029)|

|7168|18432|130|2xm256|1.000(0.998/1.000)|1.002(0.995/1.000)|1.052(1.047/1.049)|

|7168|18432|257|2xm256|1.000(0.998/0.998)|0.999(0.998/0.998)|1.058(1.059/1.059)|

|7168|18432|512|2xm256|1.001(1.005/1.004)|1.002(1.004/1.003)|1.067(1.067/1.067)|

|7168|18432|2048|2xm256|1.000(0.999/0.999)|1.000(1.000/1.000)|1.052(1.051/1.052)|

|7168|18432|8192|2xm256clc|0.998(0.992/0.991)|1.008(1.009/1.003)|1.011(1.032/1.023)|

|18432|7168|1|n8|1.002(0.997/0.994)|1.002(0.981/0.989)|1.073(1.079/1.076)|

|18432|7168|8|n8|1.008(1.046/1.033)|1.011(1.042/1.030)|1.065(1.066/1.066)|

|18432|7168|17|n32sk2|1.010(1.014/1.011)|1.006(1.011/1.009)|1.154(1.137/1.140)|

|18432|7168|32|n32sk2|1.003(1.003/1.003)|1.000(0.997/0.998)|1.146(1.149/1.148)|

|18432|7168|128|m64|1.001(1.004/1.003)|1.000(0.997/0.997)|1.046(1.046/1.047)|

|18432|7168|130|2xm128|1.005(1.008/1.007)|1.004(1.008/1.007)|1.075(1.075/1.075)|

|18432|7168|257|2xm256|1.005(1.013/1.010)|1.006(1.013/1.010)|1.041(1.045/1.044)|

|18432|7168|512|2xm256|0.996(0.991/0.992)|0.997(0.990/0.992)|1.096(1.088/1.091)|

|18432|7168|2048*|2xm192|1.077(1.077/1.077)|1.075(1.076/1.076)|1.191(1.192/1.192)|

|18432|7168|8192|2xm256g16clc|0.999(0.997/0.993)|0.999(1.001/1.003)|1.086(1.085/1.078)|

|8192|8192|1|n8|0.997(1.000/0.999)|1.005(1.003/1.007)|1.069(1.068/1.068)|

|8192|8192|8|n8|1.000(1.008/1.004)|1.000(1.008/1.005)|1.044(1.049/1.046)|

|8192|8192|17|n32|0.995(0.990/0.992)|0.998(0.993/0.994)|1.038(1.027/1.030)|

|8192|8192|32|n32|1.010(1.005/1.004)|1.007(1.000/1.003)|1.050(1.063/1.057)|

|8192|8192|128|m64|1.000(1.000/0.999)|0.998(1.000/0.999)|1.052(1.054/1.053)|

|8192|8192|130|2xm128|1.002(1.004/1.006)|1.007(1.002/1.005)|1.087(1.084/1.086)|

|8192|8192|257|2xm256|0.997(0.992/0.994)|1.000(0.990/0.994)|1.067(1.058/1.062)|

|8192|8192|512|2xm256|1.000(0.998/0.999)|1.000(0.995/0.998)|1.079(1.083/1.082)|

|8192|8192|2048|2xm192|0.997(0.996/0.996)|0.997(0.998/0.997)|1.086(1.082/1.083)|

|8192|8192|8192|2xm256g16clc|1.003(0.994/0.996)|1.002(0.997/1.000)|1.018(1.022/1.016)|

|8192|28672|1|n8|1.000(0.996/0.998)|1.000(0.994/0.997)|1.039(1.037/1.038)|

|8192|28672|8|n8|0.992(0.995/0.996)|1.001(0.998/0.998)|1.050(1.046/1.049)|

|8192|28672|17|n32|0.999(1.000/1.000)|1.000(1.004/1.002)|1.027(1.029/1.029)|

|8192|28672|32|n32|1.001(1.006/1.003)|1.005(1.005/1.006)|1.039(1.048/1.043)|

|8192|28672|128|m128|0.999(0.994/0.996)|0.999(0.997/0.998)|1.014(1.023/1.020)|

|8192|28672|130|2xm256|1.004(1.005/1.005)|1.003(1.001/1.000)|1.041(1.045/1.044)|

|8192|28672|257*|2xm192|1.024(1.025/1.024)|1.026(1.025/1.025)|1.085(1.086/1.085)|

|8192|28672|512*|2xm192|1.019(1.022/1.021)|1.021(1.022/1.022)|1.087(1.091/1.089)|

|8192|28672|2048|2xm256clc|0.999(0.999/0.995)|1.001(1.001/1.003)|1.026(1.027/1.032)|

|8192|28672|8192|2xm256clc|1.004(1.005/1.013)|1.003(1.000/0.982)|1.012(1.019/1.001)|

|28672|8192|1|n8|0.999(0.999/0.999)|0.998(1.000/0.998)|1.182(1.192/1.182)|

|28672|8192|8|n8|0.999(1.000/1.000)|1.000(0.999/1.000)|1.222(1.174/1.182)|

|28672|8192|17|n32sk2|1.000(0.996/0.998)|0.998(0.997/0.998)|1.185(1.184/1.184)|

|28672|8192|32|n32sk2|1.002(0.998/1.000)|1.001(0.998/0.999)|1.184(1.188/1.187)|

|28672|8192|128|m64|0.999(0.997/0.997)|0.997(0.996/0.997)|1.050(1.049/1.049)|

|28672|8192|130|2xm128|0.999(0.996/0.997)|1.001(0.998/0.998)|1.078(1.079/1.078)|

|28672|8192|257|2xm256|1.003(1.003/1.003)|1.004(1.007/1.005)|1.070(1.070/1.070)|

|28672|8192|512|2xm256|1.001(1.004/1.002)|1.001(1.004/1.003)|1.090(1.086/1.087)|

|28672|8192|2048|2xm192|1.004(0.999/1.025)|1.003(1.009/0.993)|1.066(1.066/1.058)|

|28672|8192|8192|2xm256g8clc|0.997(1.000/1.011)|1.000(1.005/1.009)|1.081(1.106/1.074)|

#### Quantize kernel (fold = out_scale folded into the per-token scale)
— vs #5869: bf16 rows 100, geomean 1.0003, min 0.9966, rows <= 1.00: 87;
fp16 (8 registered rows) rows 8, geomean 1.0014, min 0.9996, rows <=
1.00: 7. vs cute-dsl: bf16 rows 100, geomean 1.1244, min 1.0132, rows <=
1.00: 0; fp16 rows 8, geomean 1.1199, min 1.0704, rows <= 1.00: 0

|K|M|fold|vs #5869 bf16|vs cute-dsl bf16|roof|
|---|---|---|---|---|---|
|7168|1|0|1.000(1.000/1.000)|1.203(1.203/1.203)|LB 1.8f|
|7168|1|1|1.000(1.000/1.001)|1.169(1.169/1.173)|LB 1.8f|
|7168|8|0|1.000(1.000/1.000)|1.164(1.164/1.156)|LB 1.8f|
|7168|8|1|1.000(1.000/1.000)|1.095(1.095/1.092)|LB 1.8f|
|7168|17|0|1.000(1.000/0.999)|1.096(1.096/1.102)|LB 1.8f|
|7168|17|1|1.000(1.000/1.000)|1.137(1.137/1.136)|LB 1.8f|
|7168|32|0|1.000(1.000/1.000)|1.082(1.082/1.085)|LB 1.8f|
|7168|32|1|1.000(1.000/1.001)|1.094(1.094/1.094)|LB 1.8f|
|7168|128|0|1.000(1.000/1.001)|1.099(1.099/1.094)|13%h 2.0f|
|7168|128|1|1.000(1.000/1.001)|1.099(1.099/1.094)|13%h 2.0f|
|7168|130|0|1.000(1.000/0.998)|1.085(1.085/1.087)|13%h 2.0f|
|7168|130|1|1.000(1.000/1.002)|1.096(1.096/1.099)|12%h 2.1f|
|7168|257|0|1.000(1.000/1.000)|1.062(1.062/1.063)|21%h 2.4f|
|7168|257|1|1.000(1.000/1.000)|1.080(1.080/1.077)|21%h 2.5f|
|7168|512|0|1.000(1.000/1.000)|1.062(1.062/1.062)|32%h 3.2f|
|7168|512|1|1.000(1.000/0.999)|1.083(1.083/1.080)|32%h 3.2f|
|7168|2048|0|0.997(0.997/0.999)|1.276(1.276/1.277)|65%h|
|7168|2048|1|1.000(1.000/0.998)|1.318(1.318/1.322)|65%h|
|7168|8192|0|1.001(1.001/1.002)|1.155(1.155/1.156)|95%h|
|7168|8192|1|1.001(1.001/1.002)|1.176(1.176/1.175)|94%h|
|8192|1|0|1.000(1.000/1.000)|1.186(1.186/1.185)|LB 1.9f|
|8192|1|1|1.000(1.000/0.999)|1.186(1.186/1.191)|LB 1.8f|
|8192|8|0|1.000(1.000/1.001)|1.082(1.082/1.083)|LB 1.8f|
|8192|8|1|1.000(1.000/0.999)|1.069(1.069/1.074)|LB 1.9f|
|8192|17|0|1.000(1.000/1.000)|1.070(1.070/1.072)|LB 1.9f|
|8192|17|1|1.000(1.000/0.999)|1.070(1.070/1.073)|LB 1.9f|
|8192|32|0|1.000(1.000/0.999)|1.080(1.080/1.085)|LB 1.9f|
|8192|32|1|1.011(1.011/1.005)|1.068(1.068/1.065)|LB 1.9f|
|8192|128|0|1.000(1.000/0.998)|1.084(1.084/1.083)|14%h 2.1f|
|8192|128|1|1.000(1.000/1.000)|1.073(1.073/1.070)|14%h 2.1f|
|8192|130|0|1.000(1.000/0.998)|1.113(1.113/1.112)|14%h 2.1f|
|8192|130|1|1.000(1.000/1.000)|1.071(1.071/1.072)|14%h 2.1f|
|8192|257|0|1.000(1.000/0.999)|1.051(1.051/1.050)|22%h 2.6f|
|8192|257|1|1.000(1.000/1.000)|1.042(1.042/1.043)|22%h 2.6f|
|8192|512|0|1.000(1.000/0.998)|1.051(1.051/1.056)|34%h 3.4f|
|8192|512|1|1.000(1.000/1.000)|1.039(1.039/1.041)|34%h 3.4f|
|8192|2048|0|0.997(0.997/0.998)|1.201(1.201/1.199)|65%h|
|8192|2048|1|1.000(1.000/1.004)|1.181(1.181/1.182)|65%h|
|8192|8192|0|1.001(1.001/1.000)|1.146(1.146/1.146)|96%h|
|8192|8192|1|1.000(1.000/1.001)|1.142(1.142/1.142)|98%h|
|16384|1|0|1.000(1.000/1.002)|1.155(1.155/1.158)|LB 2.1f|
|16384|1|1|1.000(1.000/1.002)|1.098(1.098/1.101)|LB 2.3f|
|16384|8|0|1.000(1.000/0.997)|1.092(1.092/1.091)|LB 2.2f|
|16384|8|1|1.000(1.000/1.000)|1.092(1.092/1.092)|LB 2.2f|
|16384|17|0|1.000(1.000/0.998)|1.080(1.080/1.082)|LB 2.2f|
|16384|17|1|1.000(1.000/1.001)|1.070(1.070/1.071)|LB 2.2f|
|16384|32|0|1.000(1.000/0.999)|1.038(1.038/1.042)|LB 2.2f|
|16384|32|1|1.000(1.000/1.000)|1.078(1.078/1.079)|LB 2.2f|
|16384|128|0|1.000(1.000/1.001)|1.048(1.048/1.043)|21%h 2.7f|
|16384|128|1|1.000(1.000/1.000)|1.033(1.033/1.038)|21%h 2.7f|
|16384|130|0|1.007(1.007/1.002)|1.053(1.053/1.056)|20%h 3.0f|
|16384|130|1|1.000(1.000/1.001)|1.047(1.047/1.044)|21%h 2.8f|
|16384|257|0|1.006(1.006/1.002)|1.042(1.042/1.041)|32%h 3.6f|
|16384|257|1|1.000(1.000/0.999)|1.024(1.024/1.019)|32%h 3.5f|
|16384|512|0|1.000(1.000/1.000)|1.185(1.185/1.188)|46%h 5.0f|
|16384|512|1|1.000(1.000/1.001)|1.187(1.187/1.184)|46%h 5.0f|
|16384|2048|0|0.998(0.998/0.999)|1.480(1.480/1.481)|81%h|
|16384|2048|1|1.002(1.002/1.001)|1.442(1.442/1.442)|78%h|
|16384|8192|0|1.000(1.000/1.000)|1.339(1.339/1.340)|101%h|
|16384|8192|1|1.000(1.000/1.000)|1.336(1.336/1.336)|100%h|
|18432|1|0|1.000(1.000/1.001)|1.149(1.149/1.149)|LB 2.2f|
|18432|1|1|1.000(1.000/0.998)|1.132(1.132/1.140)|LB 2.3f|
|18432|8|0|1.000(1.000/1.001)|1.129(1.129/1.125)|LB 2.1f|
|18432|8|1|1.000(1.000/0.998)|1.106(1.106/1.099)|LB 2.3f|
|18432|17|0|1.000(1.000/0.998)|1.096(1.096/1.096)|LB 2.3f|
|18432|17|1|1.000(1.000/0.999)|1.093(1.093/1.093)|LB 2.3f|
|18432|32|0|1.000(1.000/1.002)|1.065(1.065/1.059)|LB 2.3f|
|18432|32|1|1.000(1.000/0.999)|1.104(1.104/1.104)|LB 2.4f|
|18432|128|0|1.000(1.000/1.001)|1.046(1.046/1.047)|23%h 2.8f|
|18432|128|1|1.000(1.000/0.999)|1.053(1.053/1.049)|22%h 2.9f|
|18432|130|0|1.000(1.000/0.999)|1.065(1.065/1.062)|22%h 3.0f|
|18432|130|1|1.007(1.007/1.001)|1.038(1.038/1.040)|20%h 3.2f|
|18432|257|0|1.000(1.000/1.000)|1.034(1.034/1.034)|34%h 3.8f|
|18432|257|1|1.000(1.000/1.000)|1.022(1.022/1.021)|32%h 4.0f|
|18432|512|0|1.000(1.000/0.998)|1.196(1.196/1.195)|49%h 5.3f|
|18432|512|1|1.000(1.000/1.001)|1.236(1.236/1.233)|49%h 5.2f|
|18432|2048|0|0.998(0.998/0.999)|1.488(1.488/1.487)|84%h|
|18432|2048|1|1.000(1.000/1.000)|1.472(1.472/1.471)|82%h|
|18432|8192|0|1.000(1.000/1.001)|1.079(1.079/1.079)|99%h|
|18432|8192|1|1.000(1.000/1.000)|1.061(1.061/1.061)|100%h|
|28672|1|0|1.000(1.000/1.000)|1.174(1.174/1.172)|LB 2.4f|
|28672|1|1|1.000(1.000/1.000)|1.198(1.198/1.199)|LB 2.5f|
|28672|8|0|1.000(1.000/1.001)|1.148(1.148/1.143)|LB 2.4f|
|28672|8|1|1.000(1.000/1.001)|1.162(1.162/1.162)|LB 2.6f|
|28672|17|0|1.000(1.000/0.999)|1.126(1.126/1.128)|LB 2.6f|
|28672|17|1|1.000(1.000/0.999)|1.140(1.140/1.139)|LB 2.6f|
|28672|32|0|1.000(1.000/0.999)|1.105(1.105/1.105)|LB 2.7f|
|28672|32|1|1.000(1.000/0.998)|1.119(1.119/1.125)|LB 2.8f|
|28672|128|0|1.000(1.000/1.000)|1.050(1.050/1.049)|29%h 3.5f|
|28672|128|1|1.000(1.000/0.999)|1.069(1.069/1.068)|29%h 3.5f|
|28672|130|0|1.000(1.000/1.002)|1.048(1.048/1.049)|27%h 3.7f|
|28672|130|1|1.000(1.000/1.000)|1.062(1.062/1.063)|27%h 3.7f|
|28672|257|0|1.000(1.000/1.000)|1.013(1.013/1.017)|41%h 4.9f|
|28672|257|1|1.004(1.004/1.000)|1.062(1.062/1.061)|42%h 4.9f|
|28672|512|0|1.000(1.000/1.000)|1.137(1.137/1.138)|55%h|
|28672|512|1|1.000(1.000/1.001)|1.152(1.152/1.151)|53%h|
|28672|2048|0|1.000(1.000/1.000)|1.309(1.309/1.310)|89%h|
|28672|2048|1|0.999(0.999/0.999)|1.317(1.317/1.317)|87%h|
|28672|8192|0|1.000(1.000/1.000)|1.110(1.110/1.111)|100%h|
|28672|8192|1|1.000(1.000/1.000)|1.119(1.119/1.119)|99%h|

fp16 activations (the registered fp16 quantizer rows):

|K|M|fold|vs #5869 fp16|vs cute-dsl fp16|
|---|---|---|---|---|
|7168|8|0|1.000(1.000/1.000)|1.096(1.096/1.095)|
|7168|17|0|1.000(1.000/1.000)|1.096(1.096/1.094)|
|7168|32|0|1.012(1.012/1.004)|1.096(1.096/1.102)|
|7168|128|0|1.000(1.000/1.000)|1.111(1.111/1.106)|
|7168|130|0|1.000(1.000/1.000)|1.094(1.094/1.089)|
|7168|257|0|1.000(1.000/0.999)|1.073(1.073/1.073)|
|7168|512|0|1.000(1.000/1.001)|1.070(1.070/1.072)|
|7168|2048|0|1.000(1.000/0.998)|1.347(1.347/1.346)|

</details>

<details><summary>GB300 (152 SMs)</summary>

#### GEMM per-token — vs #5869: bf16 rows 80, geomean 1.0003, min
0.9959, rows <= 1.00: 60; fp16 rows 80, geomean 1.0002, min 0.9970, rows
<= 1.00: 60. vs cute-dsl: bf16 rows 80, geomean 1.0546, min 0.9962, rows
<= 1.00: 1; fp16 rows 80, geomean 1.0543, min 0.9943, rows <= 1.00: 1

|K|N|M|tactic|vs #5869 bf16|vs #5869 fp16|vs cute-dsl bf16|vs cute-dsl
fp16|roof (share of measured peak; Nf = N x launch floor)|
|---|---|---|---|---|---|---|---|---|

|7168|2112|1|n8sk4|1.000(1.006/1.002)|1.000(1.000/0.999)|1.022(1.028/1.025)|1.022(1.028/1.026)|22%h
4.6f|

|7168|2112|8|n8sk4|1.000(1.000/1.000)|1.006(1.000/1.001)|1.016(1.022/1.021)|1.022(1.022/1.022)|22%h
4.7f|

|7168|2112|17|n8sk2|1.000(1.000/1.000)|1.000(1.000/1.001)|1.031(1.031/1.031)|1.036(1.031/1.032)|21%h
4.9f|

|7168|2112|32|n8sk2|1.000(1.000/1.001)|1.000(1.000/0.999)|1.031(1.036/1.032)|1.031(1.036/1.033)|21%h
5.0f|

|7168|2112|128|2xm64|1.004(1.000/1.001)|1.000(1.000/1.000)|1.113(1.117/1.113)|1.113(1.113/1.112)|19%h
5.9f|

|7168|2112|130|2xm64|1.000(1.000/1.000)|1.000(0.996/1.000)|1.103(1.103/1.105)|1.103(1.103/1.105)|19%h
5.9f|

|7168|2112|257|2xm64|0.996(0.996/0.998)|1.000(1.000/1.000)|1.048(1.044/1.047)|1.048(1.044/1.046)|20%h|

|7168|2112|512|2xm64|1.000(1.000/1.000)|1.000(1.000/1.000)|1.047(1.047/1.045)|1.043(1.047/1.045)|23%h|

|7168|2112|2048|2xm256|1.000(1.000/1.000)|1.000(1.000/1.000)|1.039(1.039/1.040)|1.039(1.039/1.040)|58%c|

|7168|2112|8192|2xm192g8|1.000(1.000/1.000)|1.001(1.000/1.000)|1.017(1.017/1.017)|1.019(1.017/1.017)|74%c|

|7168|1536|1|n8sk4|1.000(1.000/1.000)|1.000(1.000/1.000)|1.030(1.024/1.025)|1.024(1.024/1.024)|17%h
4.3f|

|7168|1536|8|n8sk4|1.000(1.000/1.000)|1.000(1.000/1.001)|1.030(1.030/1.029)|1.024(1.030/1.028)|17%h
4.4f|

|7168|1536|17|n8sk3|1.006(1.000/1.001)|1.000(1.000/0.999)|1.082(1.082/1.081)|1.076(1.076/1.078)|17%h
4.4f|

|7168|1536|32|n8sk2|1.000(1.000/1.000)|1.000(1.000/1.000)|1.028(1.027/1.027)|1.028(1.022/1.024)|16%h
4.7f|

|7168|1536|128|2xm64|1.000(1.000/1.000)|1.000(1.000/0.999)|1.102(1.102/1.103)|1.098(1.102/1.101)|15%h
5.8f|

|7168|1536|130|2xm64|1.000(1.000/1.000)|1.000(1.000/1.000)|1.089(1.084/1.088)|1.089(1.084/1.091)|15%h
5.8f|

|7168|1536|257|2xm64|1.000(1.000/0.999)|1.000(1.000/0.999)|1.042(1.042/1.044)|1.042(1.046/1.045)|15%h|

|7168|1536|512|2xm64|0.996(1.000/0.999)|1.000(1.000/0.999)|1.050(1.041/1.045)|1.046(1.046/1.046)|19%h|

|7168|1536|2048|2xm192|1.003(1.000/1.000)|1.000(1.000/1.000)|1.050(1.050/1.052)|1.050(1.050/1.050)|50%c|

|7168|1536|8192|2xm256g8|1.001(1.000/1.000)|1.002(1.000/1.000)|1.054(1.053/1.053)|1.055(1.053/1.054)|68%c|

|16384|7168|1|n8sk2|1.000(0.998/0.999)|1.000(0.998/1.000)|1.128(1.128/1.129)|1.130(1.128/1.129)|66%h|

|16384|7168|8|n8sk2|1.000(1.002/1.001)|1.000(1.000/1.000)|1.135(1.134/1.134)|1.135(1.134/1.134)|66%h|

|16384|7168|17|n32sk2|1.000(1.000/0.999)|1.002(1.000/1.000)|1.151(1.152/1.152)|1.155(1.153/1.153)|64%h|

|16384|7168|32|n32sk2|1.000(0.998/1.000)|1.002(1.000/1.000)|1.143(1.143/1.143)|1.148(1.150/1.149)|64%h|

|16384|7168|128|m64|1.002(1.000/1.000)|0.998(1.000/1.000)|1.020(1.018/1.020)|1.022(1.022/1.022)|60%h|

|16384|7168|130|2xm128|1.000(0.998/0.998)|1.000(1.002/1.001)|1.046(1.050/1.050)|1.050(1.052/1.052)|57%h|

|16384|7168|257|2xm192|0.998(1.000/0.999)|0.998(1.000/0.999)|1.038(1.038/1.038)|1.038(1.038/1.037)|51%h|

|16384|7168|512|2xm192|1.000(1.000/1.000)|1.002(1.000/1.000)|1.047(1.042/1.044)|1.044(1.045/1.044)|69%c|

|16384|7168|2048|2xm256g8|1.000(1.001/1.001)|1.000(1.000/1.000)|1.025(1.023/1.022)|1.025(1.022/1.022)|90%c|

|16384|7168|8192|2xm256g16clc|0.999(0.999/1.001)|0.999(1.000/1.000)|1.111(1.113/1.111)|1.109(1.107/1.107)|95%c|

|7168|18432|1|n8s3|1.004(1.002/1.001)|1.000(1.000/1.000)|1.029(1.033/1.031)|1.035(1.030/1.032)|70%h|

|7168|18432|8|n8s3|1.000(1.002/1.001)|1.000(0.998/0.999)|1.041(1.041/1.040)|1.043(1.043/1.041)|70%h|

|7168|18432|17|n32s3|0.998(1.000/1.000)|1.000(1.000/1.000)|1.022(1.022/1.021)|1.022(1.020/1.022)|70%h|

|7168|18432|32|n32s3|0.998(0.998/0.998)|1.002(1.002/1.000)|1.016(1.016/1.016)|1.014(1.016/1.016)|70%h|

|7168|18432|128|m128l2n|1.004(1.000/1.000)|1.002(1.000/1.000)|0.996(0.994/0.994)|0.994(0.994/0.996)|70%h|

|7168|18432|130|2xm256|1.000(1.000/1.000)|0.998(1.000/1.000)|1.029(1.027/1.028)|1.031(1.027/1.028)|67%h|

|7168|18432|257|2xm256|1.000(1.000/1.000)|0.999(1.000/0.999)|1.042(1.040/1.041)|1.040(1.042/1.040)|53%h|

|7168|18432|512|2xm256|1.000(1.001/1.000)|1.001(0.999/1.000)|1.035(1.035/1.033)|1.036(1.035/1.034)|66%c|

|7168|18432|2048|2xm256|1.000(1.001/1.001)|1.000(1.000/1.000)|1.016(1.015/1.015)|1.015(1.014/1.014)|83%c|

|7168|18432|8192|2xm256clc|1.000(1.000/1.000)|0.999(1.000/1.000)|1.007(1.009/1.009)|1.010(1.011/1.012)|92%c|

|18432|7168|1|n8|1.002(1.000/1.001)|1.000(1.000/0.999)|1.127(1.128/1.128)|1.127(1.126/1.125)|67%h|

|18432|7168|8|n8|1.000(1.002/1.001)|1.000(1.000/1.000)|1.129(1.126/1.126)|1.129(1.128/1.128)|67%h|

|18432|7168|17|n32sk2|1.002(1.000/1.000)|1.000(1.000/1.000)|1.158(1.158/1.158)|1.158(1.158/1.157)|65%h|

|18432|7168|32|n32sk2|1.002(1.002/1.001)|0.998(1.000/1.000)|1.158(1.155/1.156)|1.156(1.154/1.154)|65%h|

|18432|7168|128|m64|1.000(1.002/1.001)|1.002(0.998/1.000)|1.024(1.024/1.023)|1.024(1.026/1.025)|61%h|

|18432|7168|130|2xm128|0.998(1.002/1.000)|1.000(1.000/1.000)|1.052(1.052/1.052)|1.054(1.054/1.053)|58%h|

|18432|7168|257|2xm192|1.003(1.000/1.000)|1.000(0.999/1.000)|1.042(1.042/1.042)|1.043(1.042/1.043)|52%h|

|18432|7168|512|2xm192|0.999(1.000/1.000)|1.000(1.001/1.001)|1.044(1.044/1.043)|1.042(1.045/1.044)|70%c|

|18432|7168|2048|2xm256g8|1.000(1.000/1.000)|1.000(1.000/1.000)|1.019(1.018/1.023)|1.018(1.018/1.018)|91%c|

|18432|7168|8192|2xm256g16clc|0.999(1.001/1.000)|1.000(1.000/1.000)|1.114(1.110/1.112)|1.115(1.114/1.114)|95%c|

|8192|8192|1|n8|1.000(0.997/0.999)|1.000(1.003/1.000)|1.012(1.012/1.011)|1.009(1.012/1.010)|55%h|

|8192|8192|8|n8|1.000(1.000/1.001)|1.000(1.000/0.999)|1.019(1.019/1.018)|1.019(1.019/1.019)|55%h|

|8192|8192|17|n32|1.000(1.000/1.000)|1.000(1.003/1.001)|1.027(1.027/1.025)|1.021(1.024/1.023)|54%h|

|8192|8192|32|n32|1.003(1.000/1.001)|0.997(1.000/1.000)|1.018(1.018/1.019)|1.018(1.018/1.017)|54%h|

|8192|8192|128|m64|1.000(1.000/1.000)|1.000(1.000/1.001)|1.014(1.017/1.015)|1.017(1.014/1.014)|53%h|

|8192|8192|130|2xm128|1.000(1.000/1.000)|1.000(1.000/1.001)|1.054(1.054/1.051)|1.051(1.051/1.051)|51%h|

|8192|8192|257|2xm256|1.000(1.000/1.000)|1.000(1.000/1.000)|1.044(1.044/1.045)|1.047(1.042/1.045)|42%h|

|8192|8192|512|2xm256|1.000(1.000/0.999)|1.000(1.000/1.000)|1.042(1.042/1.042)|1.044(1.042/1.042)|54%c|

|8192|8192|2048|2xm192|0.999(1.000/0.999)|0.999(1.001/1.000)|1.049(1.050/1.050)|1.050(1.050/1.049)|75%c|

|8192|8192|8192|2xm256g16clc|1.000(0.998/0.999)|0.998(0.999/0.999)|1.010(1.009/1.009)|1.009(1.008/1.009)|89%c|

|8192|28672|1|n8|1.000(1.001/1.001)|1.000(1.000/1.000)|1.008(1.009/1.009)|1.005(1.008/1.007)|80%h|

|8192|28672|8|n8|1.000(1.003/1.001)|1.001(1.001/1.000)|1.009(1.009/1.009)|1.009(1.009/1.009)|81%h|

|8192|28672|17|n32|1.000(1.000/1.000)|1.000(0.999/0.999)|1.017(1.018/1.017)|1.014(1.015/1.016)|80%h|

|8192|28672|32|n32|1.000(0.999/0.999)|1.001(1.000/0.999)|1.014(1.015/1.015)|1.010(1.008/1.009)|80%h|

|8192|28672|128|m192|1.002(1.000/1.000)|1.000(1.000/1.000)|1.008(1.008/1.008)|1.005(1.006/1.006)|77%h|

|8192|28672|130|2xm192|1.000(0.999/0.999)|1.000(1.000/1.000)|1.018(1.016/1.017)|1.015(1.016/1.015)|78%h|

|8192|28672|257|2xm256|1.000(1.001/1.000)|1.001(1.001/1.000)|1.035(1.035/1.034)|1.035(1.035/1.035)|59%h|

|8192|28672|512|2xm256|1.000(0.999/1.000)|1.000(0.999/1.000)|1.036(1.036/1.036)|1.036(1.037/1.036)|75%c|

|8192|28672|2048|2xm256clc|0.998(1.001/0.996)|1.002(1.000/1.000)|1.014(1.008/1.010)|1.011(1.009/1.009)|89%c|

|8192|28672|8192|2xm256clc|1.000(0.999/0.999)|1.001(1.000/1.000)|1.008(1.008/1.009)|1.008(1.009/1.011)|94%c|

|28672|8192|1|n8|1.003(1.000/1.000)|1.000(1.001/1.000)|1.192(1.190/1.189)|1.188(1.187/1.186)|78%h|

|28672|8192|8|n8|1.000(1.001/1.000)|1.001(1.000/1.000)|1.188(1.184/1.185)|1.183(1.183/1.183)|78%h|

|28672|8192|17|n32sk2|1.000(1.002/1.001)|1.000(1.000/1.000)|1.197(1.197/1.197)|1.199(1.197/1.197)|75%h|

|28672|8192|32|n32sk2|1.001(1.000/1.001)|1.001(1.001/1.001)|1.193(1.192/1.192)|1.193(1.195/1.194)|76%h|

|28672|8192|128|m64|1.000(1.000/1.000)|0.999(1.001/1.000)|1.019(1.018/1.018)|1.020(1.019/1.019)|71%h|

|28672|8192|130|2xm128|0.999(1.000/0.993)|1.000(1.000/1.000)|1.037(1.037/1.037)|1.035(1.036/1.035)|69%h|

|28672|8192|257|2xm256|1.000(0.999/1.000)|1.001(1.000/1.000)|1.032(1.033/1.032)|1.033(1.032/1.033)|53%h|

|28672|8192|512|2xm256|1.002(1.001/1.001)|0.998(1.001/1.000)|1.037(1.037/1.037)|1.039(1.038/1.038)|72%c|

|28672|8192|2048|2xm192|0.999(1.000/1.000)|1.000(1.000/1.000)|1.032(1.031/1.031)|1.032(1.030/1.030)|83%c|

|28672|8192|8192|2xm256g8clc|1.003(1.001/1.001)|1.001(0.999/1.000)|1.110(1.110/1.110)|1.115(1.111/1.116)|92%c|

#### Fused quantize + GEMM chain (CUDA-graph replay, PDL edge included)
— vs #5869: bf16 rows 80, geomean 1.0017, min 0.9950, rows <= 1.00: 41;
fp16 rows 80, geomean 1.0019, min 0.9950, rows <= 1.00: 36. vs cute-dsl
(bf16): rows 80, geomean 1.0912, min 1.0024, rows <= 1.00: 0

|K|N|M|GEMM tactic|vs #5869 bf16|vs #5869 fp16|vs cute-dsl bf16|
|---|---|---|---|---|---|---|

|7168|2112|1|n8sk4|0.996(0.991/0.991)|1.000(0.991/0.992)|1.106(1.124/1.119)|

|7168|2112|8|n8sk4|1.000(0.962/0.981)|1.004(0.962/0.984)|1.123(1.084/1.113)|

|7168|2112|17|n8sk2|0.996(0.972/0.985)|0.996(0.980/0.986)|1.143(1.108/1.122)|

|7168|2112|32|n8sk2|1.020(1.008/1.012)|1.020(1.008/1.013)|1.160(1.155/1.155)|

|7168|2112|128|2xm64|1.003(0.990/0.996)|0.997(1.000/0.995)|1.146(1.153/1.156)|

|7168|2112|130|2xm64|1.000(0.990/0.996)|1.000(0.990/0.996)|1.142(1.130/1.140)|

|7168|2112|257|2xm64|1.000(1.012/1.005)|1.000(1.012/1.005)|1.111(1.126/1.124)|

|7168|2112|512|2xm64|1.003(0.997/1.000)|1.003(0.997/1.000)|1.131(1.124/1.129)|

|7168|2112|2048|2xm256|1.002(1.000/1.000)|1.003(0.998/0.999)|1.217(1.214/1.215)|

|7168|2112|8192|2xm192g8|1.002(1.003/1.008)|1.002(1.003/1.003)|1.048(1.054/1.054)|

|7168|1536|1|n8sk4|1.000(1.014/1.010)|1.005(1.014/1.011)|1.110(1.150/1.131)|

|7168|1536|8|n8sk4|1.000(0.995/0.993)|1.000(0.995/0.995)|1.118(1.111/1.117)|

|7168|1536|17|n8sk3|1.005(0.983/0.988)|1.000(0.983/0.988)|1.142(1.118/1.130)|

|7168|1536|32|n8sk2|1.026(1.017/1.019)|1.017(1.017/1.018)|1.122(1.111/1.115)|

|7168|1536|128|2xm64|0.997(0.997/0.999)|1.000(1.000/0.998)|1.097(1.113/1.111)|

|7168|1536|130|2xm64|1.017(1.017/1.015)|1.017(1.017/1.015)|1.110(1.113/1.110)|

|7168|1536|257|2xm64|1.000(0.984/0.989)|0.997(0.997/0.999)|1.070(1.091/1.085)|

|7168|1536|512|2xm64|1.003(0.991/0.992)|1.006(0.988/0.993)|1.108(1.097/1.098)|

|7168|1536|2048|2xm192|0.998(0.956/0.971)|1.000(0.956/0.971)|1.232(1.222/1.227)|

|7168|1536|8192|2xm256g8|1.000(1.005/1.003)|1.005(1.006/1.005)|1.097(1.101/1.099)|

|16384|7168|1|n8sk2|1.006(1.000/1.005)|1.004(1.004/1.006)|1.118(1.123/1.121)|

|16384|7168|8|n8sk2|1.000(0.981/0.985)|1.002(0.979/0.985)|1.132(1.106/1.111)|

|16384|7168|17|n32sk2|1.002(0.993/0.995)|0.998(0.989/0.994)|1.166(1.156/1.157)|

|16384|7168|32|n32sk2|1.007(1.004/1.006)|1.007(1.005/1.007)|1.166(1.163/1.166)|

|16384|7168|128|m64|0.995(0.990/0.992)|0.995(0.990/0.993)|1.070(1.069/1.068)|

|16384|7168|130|2xm128|0.998(1.002/1.005)|0.998(0.998/0.999)|1.072(1.070/1.074)|

|16384|7168|257|2xm192|1.001(1.005/1.004)|1.000(1.005/1.003)|1.068(1.070/1.070)|

|16384|7168|512|2xm192|0.999(1.002/1.002)|1.001(1.002/1.005)|1.121(1.120/1.128)|

|16384|7168|2048|2xm256g8|1.000(1.002/1.001)|1.001(1.002/1.001)|1.085(1.085/1.084)|

|16384|7168|8192|2xm256g16clc|1.000(1.000/1.000)|1.001(1.000/1.001)|1.154(1.154/1.154)|

|7168|18432|1|n8s3|0.996(1.006/1.002)|1.000(1.004/1.003)|1.067(1.069/1.070)|

|7168|18432|8|n8s3|0.996(1.002/1.003)|0.998(0.984/0.988)|1.059(1.060/1.059)|

|7168|18432|17|n32s3|1.000(1.004/1.006)|0.996(0.998/0.994)|1.046(1.047/1.046)|

|7168|18432|32|n32s3|1.000(1.002/1.003)|1.000(1.000/1.002)|1.036(1.043/1.045)|

|7168|18432|128|m128l2n|1.002(1.000/0.999)|0.997(0.997/0.997)|1.031(1.027/1.031)|

|7168|18432|130|2xm256|1.002(1.002/1.001)|1.002(1.005/1.003)|1.049(1.054/1.052)|

|7168|18432|257|2xm256|1.004(1.004/1.003)|1.001(1.004/1.002)|1.070(1.067/1.070)|

|7168|18432|512|2xm256|0.999(0.998/0.999)|0.999(0.998/0.995)|1.072(1.067/1.067)|

|7168|18432|2048|2xm256|1.001(1.002/1.002)|1.000(1.001/1.001)|1.051(1.046/1.047)|

|7168|18432|8192|2xm256clc|1.001(1.000/1.000)|1.001(1.001/1.001)|1.019(1.019/1.019)|

|18432|7168|1|n8|1.008(0.985/0.991)|1.005(0.984/0.990)|1.078(1.082/1.079)|

|18432|7168|8|n8|0.997(0.993/0.995)|1.000(0.992/0.994)|1.062(1.045/1.050)|

|18432|7168|17|n32sk2|0.998(0.984/0.989)|0.995(0.977/0.982)|1.151(1.133/1.136)|

|18432|7168|32|n32sk2|1.010(1.016/1.011)|1.008(1.016/1.012)|1.158(1.164/1.159)|

|18432|7168|128|m64|1.002(1.003/1.002)|1.000(1.005/1.003)|1.058(1.071/1.067)|

|18432|7168|130|2xm128|0.996(0.996/0.996)|1.000(1.001/1.000)|1.055(1.070/1.065)|

|18432|7168|257|2xm192|1.001(0.998/0.999)|0.999(0.998/0.999)|1.058(1.055/1.057)|

|18432|7168|512|2xm192|1.003(1.004/1.004)|1.003(1.006/1.005)|1.121(1.121/1.120)|

|18432|7168|2048|2xm256g8|1.002(0.999/1.001)|0.997(0.996/0.997)|1.088(1.089/1.088)|

|18432|7168|8192|2xm256g16clc|1.000(1.001/1.002)|1.000(1.000/1.001)|1.101(1.106/1.104)|

|8192|8192|1|n8|1.014(1.008/1.013)|1.019(1.008/1.013)|1.072(1.063/1.067)|

|8192|8192|8|n8|0.997(0.976/0.986)|0.997(1.003/1.005)|1.052(1.051/1.048)|

|8192|8192|17|n32|1.013(1.000/1.002)|1.013(1.000/1.002)|1.094(1.082/1.083)|

|8192|8192|32|n32|0.997(1.000/1.000)|1.000(1.000/1.001)|1.082(1.078/1.078)|

|8192|8192|128|m64|0.998(0.993/0.994)|0.998(0.993/0.996)|1.057(1.051/1.055)|

|8192|8192|130|2xm128|1.005(0.993/0.999)|1.000(0.993/1.000)|1.090(1.086/1.087)|

|8192|8192|257|2xm256|1.000(1.005/1.003)|1.002(1.004/1.003)|1.081(1.084/1.082)|

|8192|8192|512|2xm256|0.996(0.995/0.998)|1.002(0.993/0.998)|1.087(1.084/1.086)|

|8192|8192|2048|2xm192|0.998(0.998/0.999)|1.001(1.005/1.004)|1.087(1.078/1.080)|

|8192|8192|8192|2xm256g16clc|1.003(1.003/1.002)|1.001(1.001/1.001)|1.017(1.019/1.018)|

|8192|28672|1|n8|1.010(1.011/1.009)|1.007(1.011/1.009)|1.012(1.014/1.013)|

|8192|28672|8|n8|0.999(1.000/1.001)|1.002(1.001/1.001)|1.016(1.013/1.015)|

|8192|28672|17|n32|1.002(0.994/0.997)|1.001(1.001/1.001)|1.002(1.000/1.003)|

|8192|28672|32|n32|1.002(0.999/0.999)|1.005(1.000/1.000)|1.006(1.008/1.009)|

|8192|28672|128|m192|0.998(1.002/1.001)|1.000(1.003/1.002)|1.028(1.031/1.031)|

|8192|28672|130|2xm192|1.000(0.999/1.000)|0.998(0.999/0.999)|1.048(1.043/1.046)|

|8192|28672|257|2xm256|1.000(0.997/0.997)|0.999(0.997/0.997)|1.066(1.061/1.063)|

|8192|28672|512|2xm256|1.002(0.999/1.000)|1.002(0.999/0.998)|1.062(1.068/1.067)|

|8192|28672|2048|2xm256clc|1.001(0.999/0.998)|0.998(0.998/0.998)|1.032(1.027/1.027)|

|8192|28672|8192|2xm256clc|1.000(1.001/1.000)|1.003(1.003/1.002)|1.018(1.017/1.018)|

|28672|8192|1|n8|1.005(1.026/1.019)|1.006(1.027/1.018)|1.201(1.201/1.197)|

|28672|8192|8|n8|0.995(0.976/0.983)|0.995(0.981/0.983)|1.181(1.157/1.160)|

|28672|8192|17|n32sk2|0.998(0.996/0.997)|1.002(0.989/0.994)|1.203(1.198/1.199)|

|28672|8192|32|n32sk2|1.007(1.012/1.010)|1.008(1.011/1.009)|1.199(1.198/1.199)|

|28672|8192|128|m64|1.000(1.003/1.002)|1.003(1.002/0.996)|1.061(1.062/1.062)|

|28672|8192|130|2xm128|0.999(1.005/1.003)|1.002(1.006/1.005)|1.077(1.078/1.079)|

|28672|8192|257|2xm256|0.999(0.997/0.998)|0.999(0.997/0.998)|1.077(1.075/1.076)|

|28672|8192|512|2xm256|1.005(1.005/1.004)|1.003(1.006/1.005)|1.093(1.093/1.091)|

|28672|8192|2048|2xm192|1.001(0.999/0.999)|1.006(0.998/1.000)|1.058(1.056/1.057)|

|28672|8192|8192|2xm256g8clc|1.001(1.001/1.001)|1.001(0.999/1.001)|1.114(1.111/1.114)|

#### Quantize kernel (fold = out_scale folded into the per-token scale)
— vs #5869: bf16 rows 100, geomean 1.0002, min 0.9968, rows <= 1.00: 92;
fp16 (8 registered rows) rows 8, geomean 1.0010, min 0.9963, rows <=
1.00: 7. vs cute-dsl: bf16 rows 100, geomean 1.1166, min 1.0116, rows <=
1.00: 0; fp16 rows 8, geomean 1.1091, min 1.0576, rows <= 1.00: 0

|K|M|fold|vs #5869 bf16|vs cute-dsl bf16|roof|
|---|---|---|---|---|---|
|7168|1|0|1.000(1.000/0.998)|1.186(1.186/1.183)|LB 1.8f|
|7168|1|1|1.000(1.000/0.999)|1.145(1.145/1.139)|LB 1.8f|
|7168|8|0|1.000(1.000/0.999)|1.092(1.092/1.093)|LB 1.9f|
|7168|8|1|1.000(1.000/1.001)|1.092(1.092/1.083)|LB 2.0f|
|7168|17|0|1.000(1.000/1.000)|1.092(1.092/1.096)|LB 1.9f|
|7168|17|1|1.000(1.000/0.998)|1.171(1.171/1.167)|LB 2.0f|
|7168|32|0|1.000(1.000/1.002)|1.105(1.105/1.098)|LB 1.9f|
|7168|32|1|1.000(1.000/0.997)|1.118(1.118/1.109)|LB 2.0f|
|7168|128|0|1.000(1.000/1.002)|1.091(1.091/1.093)|12%h 2.3f|
|7168|128|1|1.000(1.000/1.001)|1.102(1.102/1.097)|12%h 2.3f|
|7168|130|0|1.000(1.000/1.000)|1.101(1.101/1.100)|12%h 2.3f|
|7168|130|1|1.000(1.000/1.000)|1.101(1.101/1.099)|12%h 2.3f|
|7168|257|0|1.000(1.000/1.000)|1.056(1.056/1.059)|21%h 2.7f|
|7168|257|1|1.000(1.000/0.998)|1.065(1.065/1.064)|20%h 2.8f|
|7168|512|0|1.000(1.000/0.999)|1.058(1.058/1.060)|31%h 3.6f|
|7168|512|1|1.000(1.000/0.999)|1.072(1.072/1.072)|31%h 3.6f|
|7168|2048|0|1.000(1.000/1.000)|1.306(1.306/1.309)|64%h|
|7168|2048|1|1.000(1.000/1.001)|1.298(1.298/1.296)|63%h|
|7168|8192|0|0.999(0.999/0.996)|1.158(1.158/1.158)|93%h|
|7168|8192|1|0.997(0.997/0.999)|1.173(1.173/1.173)|94%h|
|8192|1|0|1.000(1.000/1.000)|1.101(1.101/1.104)|LB 1.9f|
|8192|1|1|1.000(1.000/0.999)|1.128(1.128/1.128)|LB 2.0f|
|8192|8|0|1.000(1.000/1.002)|1.063(1.063/1.059)|LB 2.0f|
|8192|8|1|1.000(1.000/1.000)|1.064(1.064/1.063)|LB 2.0f|
|8192|17|0|1.000(1.000/1.001)|1.063(1.063/1.071)|LB 2.0f|
|8192|17|1|1.000(1.000/1.001)|1.112(1.112/1.108)|LB 2.0f|
|8192|32|0|1.000(1.000/0.997)|1.076(1.076/1.071)|LB 2.0f|
|8192|32|1|1.000(1.000/1.001)|1.089(1.089/1.091)|LB 2.0f|
|8192|128|0|1.000(1.000/1.001)|1.065(1.065/1.069)|13%h 2.4f|
|8192|128|1|1.000(1.000/1.001)|1.077(1.077/1.080)|14%h 2.3f|
|8192|130|0|1.000(1.000/0.998)|1.064(1.064/1.071)|13%h 2.4f|
|8192|130|1|1.000(1.000/0.997)|1.098(1.098/1.090)|14%h 2.4f|
|8192|257|0|1.000(1.000/0.999)|1.053(1.053/1.050)|22%h 2.9f|
|8192|257|1|1.000(1.000/0.999)|1.043(1.043/1.049)|22%h 3.0f|
|8192|512|0|1.000(1.000/1.001)|1.068(1.068/1.065)|33%h 3.8f|
|8192|512|1|1.000(1.000/0.999)|1.033(1.033/1.037)|33%h 3.8f|
|8192|2048|0|0.997(0.997/0.999)|1.201(1.201/1.199)|64%h|
|8192|2048|1|0.997(0.997/0.998)|1.164(1.164/1.164)|64%h|
|8192|8192|0|1.000(1.000/1.001)|1.164(1.164/1.165)|95%h|
|8192|8192|1|1.002(1.002/1.002)|1.171(1.171/1.174)|95%h|
|16384|1|0|1.000(1.000/1.002)|1.101(1.101/1.103)|LB 2.3f|
|16384|1|1|1.000(1.000/1.001)|1.112(1.112/1.106)|LB 2.3f|
|16384|8|0|1.000(1.000/1.001)|1.067(1.067/1.064)|LB 2.3f|
|16384|8|1|1.000(1.000/1.000)|1.141(1.141/1.136)|LB 2.3f|
|16384|17|0|1.000(1.000/1.001)|1.065(1.065/1.072)|LB 2.4f|
|16384|17|1|1.000(1.000/0.997)|1.118(1.118/1.117)|LB 2.4f|
|16384|32|0|1.000(1.000/1.004)|1.052(1.052/1.052)|LB 2.4f|
|16384|32|1|1.000(1.000/0.998)|1.084(1.084/1.080)|LB 2.5f|
|16384|128|0|1.000(1.000/1.001)|1.043(1.043/1.046)|21%h 3.0f|
|16384|128|1|1.008(1.008/1.001)|1.050(1.050/1.049)|21%h 3.1f|
|16384|130|0|1.000(1.000/1.001)|1.050(1.050/1.051)|20%h 3.2f|
|16384|130|1|1.009(1.009/1.004)|1.074(1.074/1.067)|22%h 3.0f|
|16384|257|0|1.000(1.000/0.999)|1.044(1.044/1.046)|31%h 4.1f|
|16384|257|1|1.000(1.000/1.000)|1.019(1.019/1.021)|31%h 4.2f|
|16384|512|0|1.000(1.000/1.000)|1.150(1.150/1.150)|45%h 5.7f|
|16384|512|1|1.000(1.000/1.000)|1.165(1.165/1.167)|45%h 5.7f|
|16384|2048|0|1.002(1.002/1.000)|1.418(1.418/1.419)|77%h|
|16384|2048|1|1.002(1.002/1.001)|1.382(1.382/1.374)|76%h|
|16384|8192|0|0.999(0.999/0.999)|1.317(1.317/1.318)|98%h|
|16384|8192|1|1.001(1.001/1.001)|1.328(1.328/1.328)|97%h|
|18432|1|0|1.000(1.000/0.999)|1.110(1.110/1.107)|LB 2.4f|
|18432|1|1|1.000(1.000/0.999)|1.122(1.122/1.121)|LB 2.4f|
|18432|8|0|1.000(1.000/1.001)|1.098(1.098/1.096)|LB 2.4f|
|18432|8|1|1.000(1.000/0.997)|1.113(1.113/1.118)|LB 2.5f|
|18432|17|0|1.000(1.000/0.999)|1.074(1.074/1.074)|LB 2.5f|
|18432|17|1|1.000(1.000/1.000)|1.110(1.110/1.115)|LB 2.5f|
|18432|32|0|1.000(1.000/1.003)|1.051(1.051/1.052)|LB 2.6f|
|18432|32|1|1.000(1.000/1.000)|1.079(1.079/1.078)|LB 2.6f|
|18432|128|0|1.000(1.000/0.999)|1.032(1.032/1.034)|22%h 3.2f|
|18432|128|1|1.000(1.000/1.001)|1.056(1.056/1.051)|22%h 3.2f|
|18432|130|0|1.000(1.000/1.001)|1.070(1.070/1.068)|23%h 3.2f|
|18432|130|1|1.008(1.008/1.005)|1.038(1.038/1.039)|22%h 3.3f|
|18432|257|0|1.006(1.006/1.002)|1.030(1.030/1.030)|33%h 4.4f|
|18432|257|1|1.000(1.000/1.000)|1.012(1.012/1.014)|32%h 4.5f|
|18432|512|0|1.000(1.000/0.999)|1.176(1.176/1.175)|48%h|
|18432|512|1|1.000(1.000/1.000)|1.218(1.218/1.214)|47%h|
|18432|2048|0|1.000(1.000/1.000)|1.438(1.438/1.437)|82%h|
|18432|2048|1|0.998(0.998/0.998)|1.398(1.398/1.398)|79%h|
|18432|8192|0|1.000(1.000/1.000)|1.078(1.078/1.078)|97%h|
|18432|8192|1|0.999(0.999/1.000)|1.066(1.066/1.066)|96%h|
|28672|1|0|1.000(1.000/0.999)|1.114(1.114/1.120)|LB 2.7f|
|28672|1|1|1.000(1.000/1.002)|1.170(1.170/1.168)|LB 2.8f|
|28672|8|0|1.000(1.000/1.002)|1.123(1.123/1.123)|LB 2.8f|
|28672|8|1|1.000(1.000/0.999)|1.147(1.147/1.145)|LB 2.8f|
|28672|17|0|1.000(1.000/0.999)|1.110(1.110/1.108)|LB 2.8f|
|28672|17|1|1.000(1.000/0.999)|1.168(1.168/1.170)|LB 2.8f|
|28672|32|0|1.000(1.000/1.000)|1.085(1.085/1.087)|LB 3.0f|
|28672|32|1|1.000(1.000/1.001)|1.126(1.126/1.124)|LB 3.2f|
|28672|128|0|1.000(1.000/1.001)|1.046(1.046/1.046)|29%h 3.9f|
|28672|128|1|1.000(1.000/1.000)|1.064(1.064/1.067)|29%h 3.9f|
|28672|130|0|1.000(1.000/0.999)|1.055(1.055/1.056)|26%h 4.3f|
|28672|130|1|1.000(1.000/1.002)|1.024(1.024/1.022)|27%h 4.3f|
|28672|257|0|1.000(1.000/0.999)|1.014(1.014/1.013)|40%h 5.5f|
|28672|257|1|1.000(1.000/1.000)|1.065(1.065/1.065)|41%h 5.5f|
|28672|512|0|1.000(1.000/1.001)|1.083(1.083/1.085)|53%h|
|28672|512|1|1.000(1.000/1.000)|1.134(1.134/1.135)|52%h|
|28672|2048|0|1.000(1.000/1.000)|1.272(1.272/1.272)|85%h|
|28672|2048|1|0.999(0.999/0.999)|1.327(1.327/1.327)|86%h|
|28672|8192|0|1.000(1.000/1.000)|1.114(1.114/1.115)|97%h|
|28672|8192|1|1.000(1.000/1.000)|1.110(1.110/1.110)|96%h|

fp16 activations (the registered fp16 quantizer rows):

|K|M|fold|vs #5869 fp16|vs cute-dsl fp16|
|---|---|---|---|---|
|7168|8|0|1.000(1.000/1.000)|1.079(1.079/1.079)|
|7168|17|0|1.000(1.000/0.999)|1.092(1.092/1.090)|
|7168|32|0|1.000(1.000/1.002)|1.091(1.091/1.094)|
|7168|128|0|1.011(1.011/1.004)|1.116(1.116/1.110)|
|7168|130|0|1.000(1.000/1.000)|1.091(1.091/1.095)|
|7168|257|0|1.000(1.000/0.998)|1.075(1.075/1.073)|
|7168|512|0|1.000(1.000/1.001)|1.058(1.058/1.062)|
|7168|2048|0|0.996(0.996/0.998)|1.286(1.286/1.282)|

</details>

## Accumulation order change (sliced rows only)

Partials are FP32; the per-row order is fixed by the slice index and
independent of grid or timing. Plain random inputs are bitwise equal to
the single-chain program (every FP32 partial sum of FP4 x E4M3 products
is exact); wide block-scale inputs (scales spanning 2^-12..2^12) differ
by the association only:

| row (B200, S=6) | dtype / inputs | max abs (sliced - single-chain) |
ulp histogram 0 / 1 / 2 / 3 / >=4 (max) | rel-L2 vs FP32 ref: before /
after | max rel on significant elements: before / after |
|---|---|---|---|---|---|
| 16384x7168 M=2048 | bf16 plain | 0 (bitwise) | all 0 | 0.00166 /
0.00166 | 0.00389 / 0.00389 |
| 16384x7168 M=2048 | bf16 wide | 0.0156 | 14679673 / 365 / 10 / 5 / 11
(21) | 0.00166 / 0.00166 | 0.00454 / 0.00603 |
| 16384x7168 M=2048 | fp16 wide | 0.0039 | 14677915 / 1968 / 79 / 30 /
72 (149) | 0.000207 / 0.000207 | 0.00194 / 0.00320 |
| 18432x7168 M=2048 | bf16 wide | 0.0156 | 14679681 / 360 / 9 / 7 / 7 |
0.00166 / 0.00166 | 0.00488 / 0.00488 |
| 18432x7168 M=2048 | fp16 wide | 0.0039 | 14677518 / 2331 / 96 / 33 /
86 (78) | 0.000207 / 0.000207 | 0.00195 / 0.00195 |
| 8192x28672 M=257 | bf16 wide | 0.0156 | 7368628 / 72 / 2 / 0 / 2 (10)
| 0.00166 / 0.00166 | 0.00405 / 0.00410 |
| 8192x28672 M=257 | fp16 wide | 0.0020 | 7368156 / 515 / 10 / 7 / 16
(75) | 0.000207 / 0.000207 | 0.00137 / 0.00137 |
| 8192x28672 M=512 | bf16 wide | 0.0312 | 14679893 / 158 / 3 / 1 / 9
(93) | 0.00166 / 0.00166 | 0.00409 / 0.00409 |
| 8192x28672 M=512 | fp16 wide | 0.0039 | 14678950 / 1011 / 41 / 16 / 46
(53) | 0.000207 / 0.000207 | 0.00115 / 0.00115 |

Plain inputs of every row and dtype: bitwise equal. The large "max ulp"
values of a few bf16 wide elements are elements near zero where a 1-ulp
FP32 difference crosses a bf16 exponent boundary; the max abs column
bounds them. The rel-L2 against the FP32 reference is identical to three
digits on every row; the element-wise max relative error moves both
ways.

Seed sweep (8 seeds, wide inputs, the four rows above, bf16 and fp16):
against an **FP64 reference** the sliced order has the lower rel-L2 on
8/8 seeds in every cell (e.g. bf16 1.658127431e-3 -> 1.658127342e-3,
fp16 2.072994147e-4 -> 2.072986636e-4), the maximum relative and
absolute errors tie 8/8, and among the output elements where the two
programs differ (0.001-0.02 % of the outputs) the sliced value is the
one closer to the exact result in ~92 % of them (six shorter MMA chains
plus one fixed-order FP32 combination round less than one long chain).
Against the FP32 cuBLAS reference the same sweep reads 1e-7 (bf16) /
1e-5 (fp16) of the error *worse*: that reference is itself one long FP32
chain per output and its own ~1e-7 error is the size of the difference
being measured, so it is reported but not used as the verdict. A
compensated (TwoSum) cross-slice combination was tried and dropped: it
produced bitwise-identical bf16 outputs (the FP32 partials share the
block-scale grid, so their adds are exact) and cost 3-10 % per launch.

Run-to-run: 100 launches interleaved with plain launches bitwise
identical and CUDA-graph replay bitwise identical (both GPUs); on each
shipped sliced row (bf16/fp16, plain and wide inputs) 20 interleaved
launches, 20 CUDA-graph replays and 20 launches under a high-priority
contender stream (so the slice holders are scheduled and publish in a
different order) are all bitwise equal to the first launch, and the
per-launch flag generations stay invariant. compute-sanitizer memcheck /
synccheck / racecheck: 0 errors on the sliced programs (both GPUs).

Same-program null A/B (the current programs timed against themselves,
same harness) on every table of both GPUs bounds the rows that read
below 1.00: every such row is an unchanged program inside that band;
flagged rows were re-measured at 12 x 100 and merged (per-row numbers in
the tables above). The two rows at or below cute-dsl after that are the
one-wave weight-streaming rows 8192x28672 M=1 (0.999, 83 % of the
measured HBM peak in both arms) and 7168x18432 M=128 (unchanged program;
0.986 / 0.984 on this harness, 1.0075 / 1.0054 for the same program
launched directly through the kernel's own launcher, 12 paired rounds
each).

## Baselines

- Progress baseline: the cake programs of #5869 (+ #5890).
- Threshold baseline: `backend="cute-dsl"` per-token untuned at the same
main.
- Earlier rounds: #5744, #5697, #5609, #5504.

## Tests

`tests/gemm/test_cake_mm_fp4.py` (plan + stream-K rule),
`tests/quantization/test_cake_nvfp4_quantize.py`,
`tests/gemm/test_mm_fp4.py`, `tests/gemm/test_mm_mxfp8.py` (cute-dsl
subset, 511 passed per GPU), `tests/jit/test_cute_dsl_cache.py` incl.
CUDA graph; all green on B200 and GB300 at this head (test_mm_fp4 136
passed / 12 skipped per GPU).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [3c848fe](https://github.com/flashinfer-ai/flashinfer/commit/3c848fe0b8d6d010436a67d315f324a25ddeb257)

- **作者**: eigen
- **时间**: 2026-10-02T07:12:26Z
- **提交信息**: feat(cake_kimi_k3_attn_res): regenerate the Kimi-K3 AttnRes programs after the schedule-selection round (SM100 / SM103) (#5916)

## Generated-program export evidence

Baseline: **Cake production AttnRes launcher (launch_for_eval)** at Cake
revision `f125b4d83bdcc16af9e1c372c6827bca17ee26d9`.

## Hardware stages

- `sm_100a` / world size `1`: GPUs `NVIDIA B200`, capabilities `10.0`,
drivers `580.82.07`, UUIDs `GPU-79f60bde-265c-7161-f69c-e5d3a594e23f`;
75 shapes (named in the per-shape tables below).
- `sm_100a` / world size `1`: GPUs `NVIDIA B200`, capabilities `10.0`,
drivers `580.82.07`, UUIDs `GPU-cb4983fc-f8e6-aa1b-07f6-e43082875978`;
75 shapes (named in the per-shape tables below).
- `sm_103a` / world size `1`: GPUs `NVIDIA B300 SXM6 AC`, capabilities
`10.3`, drivers `580.126.09`, UUIDs
`GPU-1076f64c-92d3-0ef6-027b-e94c9c539fe7`; 50 shapes (named in the
per-shape tables below).
- `sm_103a` / world size `1`: GPUs `NVIDIA B300 SXM6 AC`, capabilities
`10.3`, drivers `580.126.09`, UUIDs
`GPU-d56fcb33-905d-3133-fa56-711c97e7e647`; 50 shapes (named in the
per-shape tables below).
- `sm_103a` / world size `1`: GPUs `NVIDIA B300 SXM6 AC`, capabilities
`10.3`, drivers `580.126.09`, UUIDs
`GPU-821f7b13-897a-6d34-f966-61066b4813f0`; 50 shapes (named in the
per-shape tables below).

Target revision: `c82391fc11830b9719900f3a2089ab59b0a0ca41`.

Benchmark execution: `symmetric_external_cuda_graph` with 8
independently captured graph instances per arm, replayed round-robin; 3
counterbalanced groups, 100 warmup calls and 1000 reportable calls per
arm/group (fixed counts; no sizing pilot).
Each sample follows one unmeasured same-arm launch, state restoration,
and a fresh cold-L2 flush.

The complete semantic arguments and machine-readable receipts remain in
`summary.json`; the tables below retain every registered shape without
repeating those arguments.

## Per-shape results

|Shape|GPU|Route|Source ms|Export ms|Source /
Export|Correctness|Verdict|
|---|---|---|---:|---:|---:|---|---|

|primary_m1_k0__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m1_k0_sm_100a_pdl0|0.003232|0.003168|1.020202x|pass|pass|

|primary_m1_k1__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m1_k1_sm_100a_pdl0|0.003808|0.003808|1.000000x|pass|pass|

|primary_m1_k4__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m1_k4_sm_100a_pdl0|0.004993|0.004992|1.000200x|pass|pass|

|primary_m1_k8__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m1_k8_sm_100a_pdl0|0.005984|0.005984|1.000000x|pass|pass|

|primary_m2_k0__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m2_k0_sm_100a_pdl0|0.003169|0.003169|1.000000x|pass|pass|

|primary_m2_k1__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m2_k1_sm_100a_pdl0|0.003808|0.003808|1.000000x|pass|pass|

|primary_m2_k4__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m2_k4_sm_100a_pdl0|0.005024|0.005023|1.000199x|pass|pass|

|primary_m2_k8__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m2_k8_sm_100a_pdl0|0.006047|0.006017|1.004986x|pass|pass|

|primary_m4_k0__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m4_k0_sm_100a_pdl0|0.003200|0.003231|0.990405x|pass|pass|

|primary_m4_k1__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m4_k1_sm_100a_pdl0|0.003871|0.003871|1.000000x|pass|pass|

|primary_m4_k4__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m4_k4_sm_100a_pdl0|0.005056|0.005056|1.000000x|pass|pass|

|primary_m4_k8__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m4_k8_sm_100a_pdl0|0.006080|0.006080|1.000000x|pass|pass|

|primary_m8_k0__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m8_k0_sm_100a_pdl0|0.003264|0.003264|1.000000x|pass|pass|

|primary_m8_k1__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m8_k1_sm_100a_pdl0|0.003936|0.003936|1.000000x|pass|pass|

|primary_m8_k4__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m8_k4_sm_100a_pdl0|0.005184|0.005184|1.000000x|pass|pass|

|primary_m8_k8__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m8_k8_sm_100a_pdl0|0.006143|0.006143|1.000000x|pass|pass|

|primary_m16_k0__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m16_k0_sm_100a_pdl0|0.003296|0.003296|1.000000x|pass|pass|

|primary_m16_k1__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m16_k1_sm_100a_pdl0|0.004000|0.004000|1.000000x|pass|pass|

|primary_m16_k4__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m16_k4_sm_100a_pdl0|0.005312|0.005312|1.000000x|pass|pass|

|primary_m16_k8__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m16_k8_sm_100a_pdl0|0.006624|0.006625|0.999849x|pass|pass|

|primary_m32_k0__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m32_k0_sm_100a_pdl0|0.003424|0.003423|1.000292x|pass|pass|

|primary_m32_k1__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m32_k1_sm_100a_pdl0|0.004160|0.004160|1.000000x|pass|pass|

|primary_m32_k4__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m32_k4_sm_100a_pdl0|0.005696|0.005728|0.994413x|pass|pass|

|primary_m32_k8__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m32_k8_sm_100a_pdl0|0.006784|0.006784|1.000000x|pass|pass|

|primary_m64_k0__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m64_k0_sm_100a_pdl0|0.003616|0.003616|1.000000x|pass|pass|

|primary_m64_k1__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m64_k1_sm_100a_pdl0|0.004480|0.004480|1.000000x|pass|pass|

|primary_m64_k4__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m64_k4_sm_100a_pdl0|0.006271|0.006272|0.999841x|pass|pass|

|primary_m64_k8__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m64_k8_sm_100a_pdl0|0.007617|0.007616|1.000131x|pass|pass|

|primary_m128_k0__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m128_k0_sm_100a_pdl0|0.004160|0.004160|1.000000x|pass|pass|

|primary_m128_k1__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m128_k1_sm_100a_pdl0|0.005248|0.005280|0.993939x|pass|pass|

|primary_m128_k4__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m128_k4_sm_100a_pdl0|0.007136|0.007136|1.000000x|pass|pass|

|primary_m128_k8__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m128_k8_sm_100a_pdl0|0.008576|0.008544|1.003745x|pass|pass|

|primary_m256_k0__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m256_k0_sm_100a_pdl0|0.005312|0.005313|0.999812x|pass|pass|

|primary_m256_k1__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m256_k1_sm_100a_pdl0|0.007488|0.007488|1.000000x|pass|pass|

|primary_m256_k4__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m256_k4_sm_100a_pdl0|0.009920|0.009920|1.000000x|pass|pass|

|primary_m256_k8__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m256_k8_sm_100a_pdl0|0.012384|0.012384|1.000000x|pass|pass|

|primary_m512_k0__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m512_k0_sm_100a_pdl0|0.007680|0.007680|1.000000x|pass|pass|

|primary_m512_k1__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m512_k1_sm_100a_pdl0|0.010304|0.010304|1.000000x|pass|pass|

|primary_m512_k4__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m512_k4_sm_100a_pdl0|0.015136|0.015168|0.997890x|pass|pass|

|primary_m512_k8__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m512_k8_sm_100a_pdl0|0.021088|0.021087|1.000047x|pass|pass|

|primary_m1024_k0__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m1024_k0_sm_100a_pdl0|0.011745|0.011776|0.997368x|pass|pass|

|primary_m1024_k1__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m1024_k1_sm_100a_pdl0|0.015456|0.015424|1.002075x|pass|pass|

|primary_m1024_k4__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m1024_k4_sm_100a_pdl0|0.023552|0.023551|1.000042x|pass|pass|

|primary_m1024_k8__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m1024_k8_sm_100a_pdl0|0.033760|0.033728|1.000949x|pass|pass|

|primary_m2048_k0__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m2048_k0_sm_100a_pdl0|0.021440|0.021471|0.998556x|pass|pass|

|primary_m2048_k1__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m2048_k1_sm_100a_pdl0|0.026945|0.026976|0.998851x|pass|pass|

|primary_m2048_k4__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m2048_k4_sm_100a_pdl0|0.040544|0.040608|0.998424x|pass|pass|

|primary_m2048_k8__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m2048_k8_sm_100a_pdl0|0.060736|0.060768|0.999473x|pass|pass|

|primary_m4096_k0__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m4096_k0_sm_100a_pdl0|0.039520|0.039520|1.000000x|pass|pass|

|primary_m4096_k1__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m4096_k1_sm_100a_pdl0|0.048768|0.048736|1.000657x|pass|pass|

|primary_m4096_k4__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m4096_k4_sm_100a_pdl0|0.074368|0.074336|1.000430x|pass|pass|

|primary_m4096_k8__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m4096_k8_sm_100a_pdl0|0.114336|0.114304|1.000280x|pass|pass|

|primary_m8192_k0__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m8192_k0_sm_100a_pdl0|0.074720|0.074688|1.000428x|pass|pass|

|primary_m8192_k1__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m8192_k1_sm_100a_pdl0|0.092208|0.092192|1.000174x|pass|pass|

|primary_m8192_k4__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m8192_k4_sm_100a_pdl0|0.140768|0.140736|1.000227x|pass|pass|

|primary_m8192_k8__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m8192_k8_sm_100a_pdl0|0.212833|0.212800|1.000155x|pass|pass|

|primary_m16384_k0__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m16384_k0_sm_100a_pdl0|0.145071|0.145056|1.000107x|pass|pass|

|primary_m16384_k1__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m16384_k1_sm_100a_pdl0|0.180288|0.180287|1.000003x|pass|pass|

|primary_m16384_k4__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m16384_k4_sm_100a_pdl0|0.271904|0.271873|1.000114x|pass|pass|

|primary_m16384_k8__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m16384_k8_sm_100a_pdl0|0.410049|0.410081|0.999922x|pass|pass|

|k_sweep_m1_k2__sm_100a__pdl0|G0|kimi_k3_attn_res_k_sweep_m1_k2_sm_100a_pdl0|0.004064|0.004096|0.992188x|pass|pass|

|k_sweep_m1_k3__sm_100a__pdl0|G1|kimi_k3_attn_res_k_sweep_m1_k3_sm_100a_pdl0|0.004896|0.004896|1.000000x|pass|pass|

|k_sweep_m1_k5__sm_100a__pdl0|G0|kimi_k3_attn_res_k_sweep_m1_k5_sm_100a_pdl0|0.005088|0.005088|0.999902x|pass|pass|

|k_sweep_m1_k6__sm_100a__pdl0|G0|kimi_k3_attn_res_k_sweep_m1_k6_sm_100a_pdl0|0.005568|0.005568|1.000000x|pass|pass|

|k_sweep_m1_k7__sm_100a__pdl0|G1|kimi_k3_attn_res_k_sweep_m1_k7_sm_100a_pdl0|0.005729|0.005760|0.994618x|pass|pass|

|k_sweep_m4096_k2__sm_100a__pdl0|G1|kimi_k3_attn_res_k_sweep_m4096_k2_sm_100a_pdl0|0.059520|0.059552|0.999463x|pass|pass|

|k_sweep_m4096_k3__sm_100a__pdl0|G0|kimi_k3_attn_res_k_sweep_m4096_k3_sm_100a_pdl0|0.066751|0.066751|1.000000x|pass|pass|

|k_sweep_m4096_k5__sm_100a__pdl0|G1|kimi_k3_attn_res_k_sweep_m4096_k5_sm_100a_pdl0|0.084192|0.084192|1.000000x|pass|pass|

|k_sweep_m4096_k6__sm_100a__pdl0|G0|kimi_k3_attn_res_k_sweep_m4096_k6_sm_100a_pdl0|0.095040|0.094976|1.000674x|pass|pass|

|k_sweep_m4096_k7__sm_100a__pdl0|G0|kimi_k3_attn_res_k_sweep_m4096_k7_sm_100a_pdl0|0.105856|0.105856|1.000000x|pass|pass|

|semantic_layer0_m1_k0_write0__sm_100a__pdl0|G1|kimi_k3_attn_res_semantic_layer0_m1_k0_write0_sm_100a_pdl0|0.005024|0.004992|1.006410x|pass|pass|

|semantic_boundary_m17_k4_write4__sm_100a__pdl0|G1|kimi_k3_attn_res_semantic_boundary_m17_k4_write4_sm_100a_pdl0|0.023840|0.023904|0.997323x|pass|pass|

|semantic_boundary_tail_m3_k7_write7__sm_100a__pdl0|G0|kimi_k3_attn_res_semantic_boundary_tail_m3_k7_write7_sm_100a_pdl0|0.026400|0.026400|1.000000x|pass|pass|

|semantic_post_boundary_m17_k4_no_delta__sm_100a__pdl0|G1|kimi_k3_attn_res_semantic_post_boundary_m17_k4_no_delta_sm_100a_pdl0|0.009600|0.009824|0.977199x|pass|pass|

|semantic_final_m7_k8_no_output_norm__sm_100a__pdl0|G0|kimi_k3_attn_res_semantic_final_m7_k8_no_output_norm_sm_100a_pdl0|0.015968|0.015968|1.000000x|pass|pass|

|primary_m1_k0__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m1_k0_sm_100a_pdl1|0.003168|0.003200|0.990000x|pass|pass|

|primary_m1_k1__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m1_k1_sm_100a_pdl1|0.003776|0.003776|1.000000x|pass|pass|

|primary_m1_k4__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m1_k4_sm_100a_pdl1|0.005023|0.004992|1.006210x|pass|pass|

|primary_m1_k8__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m1_k8_sm_100a_pdl1|0.006016|0.006016|1.000000x|pass|pass|

|primary_m2_k0__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m2_k0_sm_100a_pdl1|0.003169|0.003168|1.000316x|pass|pass|

|primary_m2_k1__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m2_k1_sm_100a_pdl1|0.003840|0.003840|1.000000x|pass|pass|

|primary_m2_k4__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m2_k4_sm_100a_pdl1|0.005024|0.004993|1.006209x|pass|pass|

|primary_m2_k8__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m2_k8_sm_100a_pdl1|0.005985|0.005984|1.000167x|pass|pass|

|primary_m4_k0__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m4_k0_sm_100a_pdl1|0.003200|0.003200|1.000000x|pass|pass|

|primary_m4_k1__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m4_k1_sm_100a_pdl1|0.003872|0.003872|1.000000x|pass|pass|

|primary_m4_k4__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m4_k4_sm_100a_pdl1|0.005024|0.005056|0.993671x|pass|pass|

|primary_m4_k8__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m4_k8_sm_100a_pdl1|0.006143|0.006144|0.999837x|pass|pass|

|primary_m8_k0__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m8_k0_sm_100a_pdl1|0.003231|0.003200|1.009687x|pass|pass|

|primary_m8_k1__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m8_k1_sm_100a_pdl1|0.003936|0.003936|1.000000x|pass|pass|

|primary_m8_k4__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m8_k4_sm_100a_pdl1|0.005216|0.005216|1.000000x|pass|pass|

|primary_m8_k8__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m8_k8_sm_100a_pdl1|0.006176|0.006176|1.000000x|pass|pass|

|primary_m16_k0__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m16_k0_sm_100a_pdl1|0.003265|0.003265|1.000000x|pass|pass|

|primary_m16_k1__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m16_k1_sm_100a_pdl1|0.003936|0.003936|1.000000x|pass|pass|

|primary_m16_k4__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m16_k4_sm_100a_pdl1|0.005344|0.005344|1.000000x|pass|pass|

|primary_m16_k8__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m16_k8_sm_100a_pdl1|0.006432|0.006432|1.000000x|pass|pass|

|primary_m32_k0__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m32_k0_sm_100a_pdl1|0.003392|0.003392|1.000000x|pass|pass|

|primary_m32_k1__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m32_k1_sm_100a_pdl1|0.004160|0.004160|1.000000x|pass|pass|

|primary_m32_k4__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m32_k4_sm_100a_pdl1|0.005696|0.005728|0.994413x|pass|pass|

|primary_m32_k8__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m32_k8_sm_100a_pdl1|0.006816|0.006816|1.000000x|pass|pass|

|primary_m64_k0__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m64_k0_sm_100a_pdl1|0.003616|0.003616|1.000000x|pass|pass|

|primary_m64_k1__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m64_k1_sm_100a_pdl1|0.004544|0.004544|1.000000x|pass|pass|

|primary_m64_k4__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m64_k4_sm_100a_pdl1|0.006304|0.006272|1.005022x|pass|pass|

|primary_m64_k8__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m64_k8_sm_100a_pdl1|0.007647|0.007647|1.000000x|pass|pass|

|primary_m128_k0__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m128_k0_sm_100a_pdl1|0.004096|0.004096|1.000000x|pass|pass|

|primary_m128_k1__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m128_k1_sm_100a_pdl1|0.005280|0.005280|1.000000x|pass|pass|

|primary_m128_k4__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m128_k4_sm_100a_pdl1|0.007296|0.007264|1.004405x|pass|pass|

|primary_m128_k8__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m128_k8_sm_100a_pdl1|0.008608|0.008576|1.003673x|pass|pass|

|primary_m256_k0__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m256_k0_sm_100a_pdl1|0.005312|0.005312|1.000000x|pass|pass|

|primary_m256_k1__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m256_k1_sm_100a_pdl1|0.007520|0.007520|1.000000x|pass|pass|

|primary_m256_k4__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m256_k4_sm_100a_pdl1|0.009952|0.009952|1.000000x|pass|pass|

|primary_m256_k8__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m256_k8_sm_100a_pdl1|0.012513|0.012512|1.000080x|pass|pass|

|primary_m512_k0__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m512_k0_sm_100a_pdl1|0.007585|0.007616|0.995930x|pass|pass|

|primary_m512_k1__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m512_k1_sm_100a_pdl1|0.010240|0.010240|1.000000x|pass|pass|

|primary_m512_k4__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m512_k4_sm_100a_pdl1|0.015072|0.015104|0.997881x|pass|pass|

|primary_m512_k8__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m512_k8_sm_100a_pdl1|0.021120|0.021120|1.000000x|pass|pass|

|primary_m1024_k0__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m1024_k0_sm_100a_pdl1|0.011745|0.011744|1.000085x|pass|pass|

|primary_m1024_k1__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m1024_k1_sm_100a_pdl1|0.015776|0.015744|1.002033x|pass|pass|

|primary_m1024_k4__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m1024_k4_sm_100a_pdl1|0.023712|0.023712|1.000000x|pass|pass|

|primary_m1024_k8__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m1024_k8_sm_100a_pdl1|0.033601|0.033600|1.000030x|pass|pass|

|primary_m2048_k0__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m2048_k0_sm_100a_pdl1|0.021472|0.021472|1.000000x|pass|pass|

|primary_m2048_k1__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m2048_k1_sm_100a_pdl1|0.026848|0.026847|1.000037x|pass|pass|

|primary_m2048_k4__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m2048_k4_sm_100a_pdl1|0.040352|0.040384|0.999208x|pass|pass|

|primary_m2048_k8__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m2048_k8_sm_100a_pdl1|0.060672|0.060736|0.998946x|pass|pass|

|primary_m4096_k0__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m4096_k0_sm_100a_pdl1|0.039424|0.039424|1.000000x|pass|pass|

|primary_m4096_k1__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m4096_k1_sm_100a_pdl1|0.049344|0.049344|1.000000x|pass|pass|

|primary_m4096_k4__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m4096_k4_sm_100a_pdl1|0.075232|0.075200|1.000426x|pass|pass|

|primary_m4096_k8__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m4096_k8_sm_100a_pdl1|0.114144|0.114144|1.000000x|pass|pass|

|primary_m8192_k0__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m8192_k0_sm_100a_pdl1|0.074592|0.074592|1.000000x|pass|pass|

|primary_m8192_k1__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m8192_k1_sm_100a_pdl1|0.091904|0.091935|0.999663x|pass|pass|

|primary_m8192_k4__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m8192_k4_sm_100a_pdl1|0.141056|0.141088|0.999773x|pass|pass|

|primary_m8192_k8__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m8192_k8_sm_100a_pdl1|0.213248|0.213120|1.000601x|pass|pass|

|primary_m16384_k0__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m16384_k0_sm_100a_pdl1|0.144864|0.144928|0.999558x|pass|pass|

|primary_m16384_k1__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m16384_k1_sm_100a_pdl1|0.178912|0.179071|0.999112x|pass|pass|

|primary_m16384_k4__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m16384_k4_sm_100a_pdl1|0.271969|0.272000|0.999886x|pass|pass|

|primary_m16384_k8__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m16384_k8_sm_100a_pdl1|0.411072|0.411040|1.000078x|pass|pass|

|k_sweep_m1_k2__sm_100a__pdl1|G0|kimi_k3_attn_res_k_sweep_m1_k2_sm_100a_pdl1|0.004096|0.004096|1.000000x|pass|pass|

|k_sweep_m1_k3__sm_100a__pdl1|G1|kimi_k3_attn_res_k_sweep_m1_k3_sm_100a_pdl1|0.004896|0.004927|0.993708x|pass|pass|

|k_sweep_m1_k5__sm_100a__pdl1|G1|kimi_k3_attn_res_k_sweep_m1_k5_sm_100a_pdl1|0.005152|0.005184|0.993923x|pass|pass|

|k_sweep_m1_k6__sm_100a__pdl1|G0|kimi_k3_attn_res_k_sweep_m1_k6_sm_100a_pdl1|0.005568|0.005568|1.000000x|pass|pass|

|k_sweep_m1_k7__sm_100a__pdl1|G1|kimi_k3_attn_res_k_sweep_m1_k7_sm_100a_pdl1|0.005952|0.005920|1.005405x|pass|pass|

|k_sweep_m4096_k2__sm_100a__pdl1|G0|kimi_k3_attn_res_k_sweep_m4096_k2_sm_100a_pdl1|0.058752|0.058720|1.000545x|pass|pass|

|k_sweep_m4096_k3__sm_100a__pdl1|G0|kimi_k3_attn_res_k_sweep_m4096_k3_sm_100a_pdl1|0.066624|0.066624|1.000000x|pass|pass|

|k_sweep_m4096_k5__sm_100a__pdl1|G1|kimi_k3_attn_res_k_sweep_m4096_k5_sm_100a_pdl1|0.084320|0.084256|1.000760x|pass|pass|

|k_sweep_m4096_k6__sm_100a__pdl1|G1|kimi_k3_attn_res_k_sweep_m4096_k6_sm_100a_pdl1|0.094465|0.094496|0.999667x|pass|pass|

|k_sweep_m4096_k7__sm_100a__pdl1|G0|kimi_k3_attn_res_k_sweep_m4096_k7_sm_100a_pdl1|0.105952|0.106016|0.999396x|pass|pass|

|semantic_layer0_m1_k0_write0__sm_100a__pdl1|G1|kimi_k3_attn_res_semantic_layer0_m1_k0_write0_sm_100a_pdl1|0.005024|0.005024|1.000000x|pass|pass|

|semantic_boundary_m17_k4_write4__sm_100a__pdl1|G0|kimi_k3_attn_res_semantic_boundary_m17_k4_write4_sm_100a_pdl1|0.023072|0.023073|0.999957x|pass|pass|

|semantic_boundary_tail_m3_k7_write7__sm_100a__pdl1|G0|kimi_k3_attn_res_semantic_boundary_tail_m3_k7_write7_sm_100a_pdl1|0.026848|0.026848|1.000000x|pass|pass|

|semantic_post_boundary_m17_k4_no_delta__sm_100a__pdl1|G1|kimi_k3_attn_res_semantic_post_boundary_m17_k4_no_delta_sm_100a_pdl1|0.009600|0.009920|0.967742x|pass|pass|

|semantic_final_m7_k8_no_output_norm__sm_100a__pdl1|G1|kimi_k3_attn_res_semantic_final_m7_k8_no_output_norm_sm_100a_pdl1|0.016000|0.016000|1.000000x|pass|pass|

|primary_m1_k0__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m1_k0_sm_103a_pdl0|0.003200|0.003232|0.990099x|pass|pass|

|primary_m1_k1__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m1_k1_sm_103a_pdl0|0.003489|0.003488|1.000287x|pass|pass|

|primary_m1_k4__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m1_k4_sm_103a_pdl0|0.005024|0.004865|1.032682x|pass|pass|

|primary_m1_k8__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m1_k8_sm_103a_pdl0|0.005920|0.005888|1.005435x|pass|pass|

|primary_m2_k0__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m2_k0_sm_103a_pdl0|0.002912|0.002976|0.978495x|pass|pass|

|primary_m2_k1__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m2_k1_sm_103a_pdl0|0.003808|0.003744|1.017094x|pass|pass|

|primary_m2_k4__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m2_k4_sm_103a_pdl0|0.004992|0.004800|1.040000x|pass|pass|

|primary_m2_k8__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m2_k8_sm_103a_pdl0|0.005729|0.005824|0.983688x|pass|pass|

|primary_m4_k0__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m4_k0_sm_103a_pdl0|0.003169|0.003232|0.980507x|pass|pass|

|primary_m4_k1__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m4_k1_sm_103a_pdl0|0.003808|0.003776|1.008341x|pass|pass|

|primary_m4_k4__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m4_k4_sm_103a_pdl0|0.004960|0.004800|1.033333x|pass|pass|

|primary_m4_k8__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m4_k8_sm_103a_pdl0|0.006080|0.006177|0.984297x|pass|pass|

|primary_m8_k0__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m8_k0_sm_103a_pdl0|0.003232|0.003264|0.990196x|pass|pass|

|primary_m8_k1__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m8_k1_sm_103a_pdl0|0.003680|0.003648|1.008772x|pass|pass|

|primary_m8_k4__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m8_k4_sm_103a_pdl0|0.005120|0.004992|1.025641x|pass|pass|

|primary_m8_k8__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m8_k8_sm_103a_pdl0|0.006049|0.006080|0.994901x|pass|pass|

|primary_m16_k0__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m16_k0_sm_103a_pdl0|0.003200|0.003200|1.000000x|pass|pass|

|primary_m16_k1__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m16_k1_sm_103a_pdl0|0.003872|0.003872|1.000000x|pass|pass|

|primary_m16_k4__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m16_k4_sm_103a_pdl0|0.005313|0.005183|1.025082x|pass|pass|

|primary_m16_k8__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m16_k8_sm_103a_pdl0|0.006144|0.006176|0.994819x|pass|pass|

|primary_m32_k0__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m32_k0_sm_103a_pdl0|0.003360|0.003392|0.990566x|pass|pass|

|primary_m32_k1__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m32_k1_sm_103a_pdl0|0.004064|0.004064|1.000000x|pass|pass|

|primary_m32_k4__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m32_k4_sm_103a_pdl0|0.005632|0.005472|1.029240x|pass|pass|

|primary_m32_k8__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m32_k8_sm_103a_pdl0|0.006656|0.006720|0.990476x|pass|pass|

|primary_m64_k0__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m64_k0_sm_103a_pdl0|0.003552|0.003616|0.982301x|pass|pass|

|primary_m64_k1__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m64_k1_sm_103a_pdl0|0.004416|0.004384|1.007299x|pass|pass|

|primary_m64_k4__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m64_k4_sm_103a_pdl0|0.006367|0.006177|1.030759x|pass|pass|

|primary_m64_k8__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m64_k8_sm_103a_pdl0|0.007488|0.007520|0.995745x|pass|pass|

|primary_m128_k0__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m128_k0_sm_103a_pdl0|0.004127|0.004096|1.007568x|pass|pass|

|primary_m128_k1__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m128_k1_sm_103a_pdl0|0.005184|0.005152|1.006211x|pass|pass|

|primary_m128_k4__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m128_k4_sm_103a_pdl0|0.007168|0.007040|1.018182x|pass|pass|

|primary_m128_k8__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m128_k8_sm_103a_pdl0|0.008416|0.008448|0.996212x|pass|pass|

|primary_m256_k0__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m256_k0_sm_103a_pdl0|0.005312|0.005281|1.005870x|pass|pass|

|primary_m256_k1__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m256_k1_sm_103a_pdl0|0.007392|0.007329|1.008596x|pass|pass|

|primary_m256_k4__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m256_k4_sm_103a_pdl0|0.009727|0.009504|1.023464x|pass|pass|

|primary_m256_k8__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m256_k8_sm_103a_pdl0|0.012608|0.012576|1.002545x|pass|pass|

|primary_m512_k0__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m512_k0_sm_103a_pdl0|0.007681|0.007681|1.000000x|pass|pass|

|primary_m512_k1__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m512_k1_sm_103a_pdl0|0.010080|0.010017|1.006289x|pass|pass|

|primary_m512_k4__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m512_k4_sm_103a_pdl0|0.015232|0.015105|1.008408x|pass|pass|

|primary_m512_k8__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m512_k8_sm_103a_pdl0|0.021536|0.021472|1.002981x|pass|pass|

|primary_m1024_k0__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m1024_k0_sm_103a_pdl0|0.011681|0.011712|0.997353x|pass|pass|

|primary_m1024_k1__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m1024_k1_sm_103a_pdl0|0.015776|0.015776|1.000000x|pass|pass|

|primary_m1024_k4__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m1024_k4_sm_103a_pdl0|0.023808|0.023936|0.994632x|pass|pass|

|primary_m1024_k8__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m1024_k8_sm_103a_pdl0|0.034689|0.034849|0.995409x|pass|pass|

|primary_m2048_k0__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m2048_k0_sm_103a_pdl0|0.022016|0.022080|0.997101x|pass|pass|

|primary_m2048_k1__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m2048_k1_sm_103a_pdl0|0.027361|0.027361|1.000000x|pass|pass|

|primary_m2048_k4__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m2048_k4_sm_103a_pdl0|0.040993|0.041153|0.996112x|pass|pass|

|primary_m2048_k8__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m2048_k8_sm_103a_pdl0|0.062337|0.062529|0.996929x|pass|pass|

|primary_m4096_k0__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m4096_k0_sm_103a_pdl0|0.040096|0.040161|0.998382x|pass|pass|

|primary_m4096_k1__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m4096_k1_sm_103a_pdl0|0.049376|0.049328|1.000963x|pass|pass|

|primary_m4096_k4__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m4096_k4_sm_103a_pdl0|0.075841|0.076097|0.996636x|pass|pass|

|primary_m4096_k8__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m4096_k8_sm_103a_pdl0|0.116834|0.116962|0.998906x|pass|pass|

|primary_m8192_k0__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m8192_k0_sm_103a_pdl0|0.076577|0.076705|0.998331x|pass|pass|

|primary_m8192_k1__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m8192_k1_sm_103a_pdl0|0.093953|0.093953|1.000000x|pass|pass|

|primary_m8192_k4__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m8192_k4_sm_103a_pdl0|0.145826|0.146338|0.996501x|pass|pass|

|primary_m8192_k8__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m8192_k8_sm_103a_pdl0|0.217762|0.217987|0.998968x|pass|pass|

|primary_m16384_k0__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m16384_k0_sm_103a_pdl0|0.147809|0.148001|0.998703x|pass|pass|

|primary_m16384_k1__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m16384_k1_sm_103a_pdl0|0.180963|0.181091|0.999293x|pass|pass|

|primary_m16384_k4__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m16384_k4_sm_103a_pdl0|0.279635|0.280260|0.997772x|pass|pass|

|primary_m16384_k8__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m16384_k8_sm_103a_pdl0|0.419269|0.419462|0.999540x|pass|pass|

|k_sweep_m1_k2__sm_103a__pdl0|G2|kimi_k3_attn_res_k_sweep_m1_k2_sm_103a_pdl0|0.004032|0.004001|1.007748x|pass|pass|

|k_sweep_m1_k3__sm_103a__pdl0|G3|kimi_k3_attn_res_k_sweep_m1_k3_sm_103a_pdl0|0.004576|0.004544|1.007042x|pass|pass|

|k_sweep_m1_k5__sm_103a__pdl0|G4|kimi_k3_attn_res_k_sweep_m1_k5_sm_103a_pdl0|0.005056|0.005088|0.993711x|pass|pass|

|k_sweep_m1_k6__sm_103a__pdl0|G2|kimi_k3_attn_res_k_sweep_m1_k6_sm_103a_pdl0|0.005504|0.005536|0.994220x|pass|pass|

|k_sweep_m1_k7__sm_103a__pdl0|G3|kimi_k3_attn_res_k_sweep_m1_k7_sm_103a_pdl0|0.005504|0.005632|0.977273x|pass|pass|

|k_sweep_m4096_k2__sm_103a__pdl0|G4|kimi_k3_attn_res_k_sweep_m4096_k2_sm_103a_pdl0|0.059232|0.059168|1.001082x|pass|pass|

|k_sweep_m4096_k3__sm_103a__pdl0|G2|kimi_k3_attn_res_k_sweep_m4096_k3_sm_103a_pdl0|0.067537|0.067489|1.000711x|pass|pass|

|k_sweep_m4096_k5__sm_103a__pdl0|G3|kimi_k3_attn_res_k_sweep_m4096_k5_sm_103a_pdl0|0.087009|0.088449|0.983719x|pass|pass|

|k_sweep_m4096_k6__sm_103a__pdl0|G4|kimi_k3_attn_res_k_sweep_m4096_k6_sm_103a_pdl0|0.097954|0.098241|0.997079x|pass|pass|

|k_sweep_m4096_k7__sm_103a__pdl0|G2|kimi_k3_attn_res_k_sweep_m4096_k7_sm_103a_pdl0|0.108322|0.108225|1.000896x|pass|pass|

|semantic_layer0_m1_k0_write0__sm_103a__pdl0|G3|kimi_k3_attn_res_semantic_layer0_m1_k0_write0_sm_103a_pdl0|0.004480|0.004480|1.000000x|pass|pass|

|semantic_boundary_m17_k4_write4__sm_103a__pdl0|G4|kimi_k3_attn_res_semantic_boundary_m17_k4_write4_sm_103a_pdl0|0.022177|0.022208|0.998604x|pass|pass|

|semantic_boundary_tail_m3_k7_write7__sm_103a__pdl0|G2|kimi_k3_attn_res_semantic_boundary_tail_m3_k7_write7_sm_103a_pdl0|0.026592|0.026593|0.999962x|pass|pass|

|semantic_post_boundary_m17_k4_no_delta__sm_103a__pdl0|G3|kimi_k3_attn_res_semantic_post_boundary_m17_k4_no_delta_sm_103a_pdl0|0.009152|0.009152|1.000000x|pass|pass|

|semantic_final_m7_k8_no_output_norm__sm_103a__pdl0|G4|kimi_k3_attn_res_semantic_final_m7_k8_no_output_norm_sm_103a_pdl0|0.015424|0.015425|0.999935x|pass|pass|

|primary_m1_k0__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m1_k0_sm_103a_pdl1|0.003168|0.003168|1.000000x|pass|pass|

|primary_m1_k1__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m1_k1_sm_103a_pdl1|0.003583|0.003520|1.017898x|pass|pass|

|primary_m1_k4__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m1_k4_sm_103a_pdl1|0.004992|0.004833|1.032899x|pass|pass|

|primary_m1_k8__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m1_k8_sm_103a_pdl1|0.005952|0.005920|1.005405x|pass|pass|

|primary_m2_k0__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m2_k0_sm_103a_pdl1|0.002976|0.003008|0.989362x|pass|pass|

|primary_m2_k1__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m2_k1_sm_103a_pdl1|0.003775|0.003744|1.008280x|pass|pass|

|primary_m2_k4__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m2_k4_sm_103a_pdl1|0.004960|0.004832|1.026490x|pass|pass|

|primary_m2_k8__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m2_k8_sm_103a_pdl1|0.005792|0.005760|1.005556x|pass|pass|

|primary_m4_k0__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m4_k0_sm_103a_pdl1|0.003232|0.003264|0.990196x|pass|pass|

|primary_m4_k1__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m4_k1_sm_103a_pdl1|0.003808|0.003776|1.008475x|pass|pass|

|primary_m4_k4__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m4_k4_sm_103a_pdl1|0.004960|0.004800|1.033333x|pass|pass|

|primary_m4_k8__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m4_k8_sm_103a_pdl1|0.006016|0.006016|1.000000x|pass|pass|

|primary_m8_k0__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m8_k0_sm_103a_pdl1|0.003264|0.003296|0.990291x|pass|pass|

|primary_m8_k1__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m8_k1_sm_103a_pdl1|0.003648|0.003616|1.008850x|pass|pass|

|primary_m8_k4__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m8_k4_sm_103a_pdl1|0.005120|0.004928|1.038961x|pass|pass|

|primary_m8_k8__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m8_k8_sm_103a_pdl1|0.006048|0.006048|1.000000x|pass|pass|

|primary_m16_k0__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m16_k0_sm_103a_pdl1|0.003168|0.003169|0.999684x|pass|pass|

|primary_m16_k1__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m16_k1_sm_103a_pdl1|0.003904|0.003872|1.008264x|pass|pass|

|primary_m16_k4__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m16_k4_sm_103a_pdl1|0.005281|0.005152|1.025039x|pass|pass|

|primary_m16_k8__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m16_k8_sm_103a_pdl1|0.006208|0.006176|1.005181x|pass|pass|

|primary_m32_k0__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m32_k0_sm_103a_pdl1|0.003360|0.003424|0.981308x|pass|pass|

|primary_m32_k1__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m32_k1_sm_103a_pdl1|0.004064|0.004032|1.007937x|pass|pass|

|primary_m32_k4__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m32_k4_sm_103a_pdl1|0.005600|0.005472|1.023392x|pass|pass|

|primary_m32_k8__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m32_k8_sm_103a_pdl1|0.006720|0.006688|1.004785x|pass|pass|

|primary_m64_k0__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m64_k0_sm_103a_pdl1|0.003616|0.003616|1.000000x|pass|pass|

|primary_m64_k1__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m64_k1_sm_103a_pdl1|0.004448|0.004416|1.007246x|pass|pass|

|primary_m64_k4__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m64_k4_sm_103a_pdl1|0.006336|0.006144|1.031250x|pass|pass|

|primary_m64_k8__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m64_k8_sm_103a_pdl1|0.007457|0.007393|1.008657x|pass|pass|

|primary_m128_k0__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m128_k0_sm_103a_pdl1|0.004096|0.004096|1.000000x|pass|pass|

|primary_m128_k1__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m128_k1_sm_103a_pdl1|0.005217|0.005216|1.000192x|pass|pass|

|primary_m128_k4__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m128_k4_sm_103a_pdl1|0.007232|0.007104|1.018018x|pass|pass|

|primary_m128_k8__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m128_k8_sm_103a_pdl1|0.008384|0.008352|1.003831x|pass|pass|

|primary_m256_k0__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m256_k0_sm_103a_pdl1|0.005440|0.005441|0.999816x|pass|pass|

|primary_m256_k1__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m256_k1_sm_103a_pdl1|0.007456|0.007392|1.008658x|pass|pass|

|primary_m256_k4__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m256_k4_sm_103a_pdl1|0.009727|0.009505|1.023356x|pass|pass|

|primary_m256_k8__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m256_k8_sm_103a_pdl1|0.012513|0.012544|0.997529x|pass|pass|

|primary_m512_k0__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m512_k0_sm_103a_pdl1|0.007776|0.007745|1.004003x|pass|pass|

|primary_m512_k1__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m512_k1_sm_103a_pdl1|0.010048|0.009984|1.006410x|pass|pass|

|primary_m512_k4__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m512_k4_sm_103a_pdl1|0.015137|0.015040|1.006449x|pass|pass|

|primary_m512_k8__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m512_k8_sm_103a_pdl1|0.021568|0.021536|1.001486x|pass|pass|

|primary_m1024_k0__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m1024_k0_sm_103a_pdl1|0.011136|0.011168|0.997135x|pass|pass|

|primary_m1024_k1__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m1024_k1_sm_103a_pdl1|0.015744|0.015744|1.000000x|pass|pass|

|primary_m1024_k4__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m1024_k4_sm_103a_pdl1|0.023488|0.023584|0.995929x|pass|pass|

|primary_m1024_k8__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m1024_k8_sm_103a_pdl1|0.034336|0.034497|0.995333x|pass|pass|

|primary_m2048_k0__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m2048_k0_sm_103a_pdl1|0.022112|0.022176|0.997114x|pass|pass|

|primary_m2048_k1__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m2048_k1_sm_103a_pdl1|0.027392|0.027392|1.000000x|pass|pass|

|primary_m2048_k4__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m2048_k4_sm_103a_pdl1|0.040929|0.041089|0.996106x|pass|pass|

|primary_m2048_k8__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m2048_k8_sm_103a_pdl1|0.062529|0.062656|0.997973x|pass|pass|

|primary_m4096_k0__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m4096_k0_sm_103a_pdl1|0.040032|0.040128|0.997608x|pass|pass|

|primary_m4096_k1__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m4096_k1_sm_103a_pdl1|0.049345|0.049281|1.001299x|pass|pass|

|primary_m4096_k4__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m4096_k4_sm_103a_pdl1|0.076257|0.076417|0.997906x|pass|pass|

|primary_m4096_k8__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m4096_k8_sm_103a_pdl1|0.117986|0.118178|0.998375x|pass|pass|

|primary_m8192_k0__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m8192_k0_sm_103a_pdl1|0.076705|0.076864|0.997931x|pass|pass|

|primary_m8192_k1__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m8192_k1_sm_103a_pdl1|0.093985|0.093953|1.000341x|pass|pass|

|primary_m8192_k4__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m8192_k4_sm_103a_pdl1|0.146146|0.146595|0.996937x|pass|pass|

|primary_m8192_k8__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m8192_k8_sm_103a_pdl1|0.218338|0.218530|0.999121x|pass|pass|

|primary_m16384_k0__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m16384_k0_sm_103a_pdl1|0.147777|0.147970|0.998696x|pass|pass|

|primary_m16384_k1__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m16384_k1_sm_103a_pdl1|0.181314|0.181315|0.999997x|pass|pass|

|primary_m16384_k4__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m16384_k4_sm_103a_pdl1|0.279556|0.280420|0.996919x|pass|pass|

|primary_m16384_k8__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m16384_k8_sm_103a_pdl1|0.418757|0.419013|0.999389x|pass|pass|

|k_sweep_m1_k2__sm_103a__pdl1|G2|kimi_k3_attn_res_k_sweep_m1_k2_sm_103a_pdl1|0.004000|0.003969|1.007811x|pass|pass|

|k_sweep_m1_k3__sm_103a__pdl1|G3|kimi_k3_attn_res_k_sweep_m1_k3_sm_103a_pdl1|0.004544|0.004512|1.007092x|pass|pass|

|k_sweep_m1_k5__sm_103a__pdl1|G4|kimi_k3_attn_res_k_sweep_m1_k5_sm_103a_pdl1|0.005024|0.005088|0.987421x|pass|pass|

|k_sweep_m1_k6__sm_103a__pdl1|G2|kimi_k3_attn_res_k_sweep_m1_k6_sm_103a_pdl1|0.005504|0.005536|0.994220x|pass|pass|

|k_sweep_m1_k7__sm_103a__pdl1|G3|kimi_k3_attn_res_k_sweep_m1_k7_sm_103a_pdl1|0.005600|0.005568|1.005747x|pass|pass|

|k_sweep_m4096_k2__sm_103a__pdl1|G4|kimi_k3_attn_res_k_sweep_m4096_k2_sm_103a_pdl1|0.059457|0.059457|1.000000x|pass|pass|

|k_sweep_m4096_k3__sm_103a__pdl1|G2|kimi_k3_attn_res_k_sweep_m4096_k3_sm_103a_pdl1|0.067457|0.067394|1.000935x|pass|pass|

|k_sweep_m4096_k5__sm_103a__pdl1|G3|kimi_k3_attn_res_k_sweep_m4096_k5_sm_103a_pdl1|0.086305|0.088352|0.976831x|pass|pass|

|k_sweep_m4096_k6__sm_103a__pdl1|G4|kimi_k3_attn_res_k_sweep_m4096_k6_sm_103a_pdl1|0.098049|0.098274|0.997710x|pass|pass|

|k_sweep_m4096_k7__sm_103a__pdl1|G2|kimi_k3_attn_res_k_sweep_m4096_k7_sm_103a_pdl1|0.108770|0.108610|1.001473x|pass|pass|

|semantic_layer0_m1_k0_write0__sm_103a__pdl1|G3|kimi_k3_attn_res_semantic_layer0_m1_k0_write0_sm_103a_pdl1|0.004480|0.004480|1.000000x|pass|pass|

|semantic_boundary_m17_k4_write4__sm_103a__pdl1|G4|kimi_k3_attn_res_semantic_boundary_m17_k4_write4_sm_103a_pdl1|0.023104|0.023136|0.998617x|pass|pass|

|semantic_boundary_tail_m3_k7_write7__sm_103a__pdl1|G2|kimi_k3_attn_res_semantic_boundary_tail_m3_k7_write7_sm_103a_pdl1|0.026208|0.026177|1.001184x|pass|pass|

|semantic_post_boundary_m17_k4_no_delta__sm_103a__pdl1|G3|kimi_k3_attn_res_semantic_post_boundary_m17_k4_no_delta_sm_103a_pdl1|0.009247|0.009184|1.006860x|pass|pass|

|semantic_final_m7_k8_no_output_norm__sm_103a__pdl1|G4|kimi_k3_attn_res_semantic_final_m7_k8_no_output_norm_sm_103a_pdl1|0.015489|0.015457|1.002070x|pass|pass|

## Per-shape comparison: pinned vLLM SM100f native CUDA AttnRes op
(csrc/libtorch_stable/kimi_k3/attn_res_kernel.cu)

|Shape|Baseline ms|Paired export ms|Baseline / Export|
|---|---:|---:|---:|
|primary_m1_k0__sm_100a__pdl0|0.004160|0.003168|1.313131x|
|primary_m1_k1__sm_100a__pdl0|0.004480|0.003808|1.176471x|
|primary_m1_k4__sm_100a__pdl0|0.005344|0.004992|1.070513x|
|primary_m1_k8__sm_100a__pdl0|0.006337|0.005984|1.058991x|
|primary_m2_k0__sm_100a__pdl0|0.004160|0.003169|1.312717x|
|primary_m2_k1__sm_100a__pdl0|0.004480|0.003808|1.176471x|
|primary_m2_k4__sm_100a__pdl0|0.005344|0.005023|1.063906x|
|primary_m2_k8__sm_100a__pdl0|0.006432|0.006017|1.068971x|
|primary_m4_k0__sm_100a__pdl0|0.004192|0.003231|1.297431x|
|primary_m4_k1__sm_100a__pdl0|0.004576|0.003871|1.182123x|
|primary_m4_k4__sm_100a__pdl0|0.005376|0.005056|1.063291x|
|primary_m4_k8__sm_100a__pdl0|0.006433|0.006080|1.058059x|
|primary_m8_k0__sm_100a__pdl0|0.004224|0.003264|1.294118x|
|primary_m8_k1__sm_100a__pdl0|0.004608|0.003936|1.170732x|
|primary_m8_k4__sm_100a__pdl0|0.005473|0.005184|1.055748x|
|primary_m8_k8__sm_100a__pdl0|0.006496|0.006143|1.057464x|
|primary_m16_k0__sm_100a__pdl0|0.004256|0.003296|1.291262x|
|primary_m16_k1__sm_100a__pdl0|0.004736|0.004000|1.184000x|
|primary_m16_k4__sm_100a__pdl0|0.005632|0.005312|1.060241x|
|primary_m16_k8__sm_100a__pdl0|0.006816|0.006625|1.028830x|
|primary_m32_k0__sm_100a__pdl0|0.004384|0.003423|1.280748x|
|primary_m32_k1__sm_100a__pdl0|0.004832|0.004160|1.161538x|
|primary_m32_k4__sm_100a__pdl0|0.006016|0.005728|1.050279x|
|primary_m32_k8__sm_100a__pdl0|0.007168|0.006784|1.056604x|
|primary_m64_k0__sm_100a__pdl0|0.004576|0.003616|1.265487x|
|primary_m64_k1__sm_100a__pdl0|0.005184|0.004480|1.157143x|
|primary_m64_k4__sm_100a__pdl0|0.006560|0.006272|1.045918x|
|primary_m64_k8__sm_100a__pdl0|0.007744|0.007616|1.016807x|
|primary_m128_k0__sm_100a__pdl0|0.005088|0.004160|1.223077x|
|primary_m128_k1__sm_100a__pdl0|0.005888|0.005280|1.115152x|
|primary_m128_k4__sm_100a__pdl0|0.007488|0.007136|1.049327x|
|primary_m128_k8__sm_100a__pdl0|0.008704|0.008544|1.018727x|
|primary_m256_k0__sm_100a__pdl0|0.006656|0.005313|1.252776x|
|primary_m256_k1__sm_100a__pdl0|0.008064|0.007488|1.076923x|
|primary_m256_k4__sm_100a__pdl0|0.010016|0.009920|1.009677x|
|primary_m256_k8__sm_100a__pdl0|0.012864|0.012384|1.038760x|
|primary_m512_k0__sm_100a__pdl0|0.008896|0.007680|1.158333x|
|primary_m512_k1__sm_100a__pdl0|0.010943|0.010304|1.062015x|
|primary_m512_k4__sm_100a__pdl0|0.015456|0.015168|1.018987x|
|primary_m512_k8__sm_100a__pdl0|0.021888|0.021087|1.037985x|
|primary_m1024_k0__sm_100a__pdl0|0.013312|0.011776|1.130435x|
|primary_m1024_k1__sm_100a__pdl0|0.016000|0.015424|1.037344x|
|primary_m1024_k4__sm_100a__pdl0|0.024160|0.023551|1.025859x|
|primary_m1024_k8__sm_100a__pdl0|0.036064|0.033728|1.069260x|
|primary_m2048_k0__sm_100a__pdl0|0.022496|0.021471|1.047739x|
|primary_m2048_k1__sm_100a__pdl0|0.027552|0.026976|1.021352x|
|primary_m2048_k4__sm_100a__pdl0|0.043136|0.040608|1.062254x|
|primary_m2048_k8__sm_100a__pdl0|0.064256|0.060768|1.057399x|
|primary_m4096_k0__sm_100a__pdl0|0.040639|0.039520|1.028315x|
|primary_m4096_k1__sm_100a__pdl0|0.049536|0.048736|1.016415x|
|primary_m4096_k4__sm_100a__pdl0|0.078784|0.074336|1.059836x|
|primary_m4096_k8__sm_100a__pdl0|0.118272|0.114304|1.034714x|
|primary_m8192_k0__sm_100a__pdl0|0.075792|0.074688|1.014781x|
|primary_m8192_k1__sm_100a__pdl0|0.093088|0.092192|1.009719x|
|primary_m8192_k4__sm_100a__pdl0|0.147840|0.140736|1.050477x|
|primary_m8192_k8__sm_100a__pdl0|0.223457|0.212800|1.050078x|
|primary_m16384_k0__sm_100a__pdl0|0.146176|0.145056|1.007721x|
|primary_m16384_k1__sm_100a__pdl0|0.184096|0.180287|1.021125x|
|primary_m16384_k4__sm_100a__pdl0|0.284608|0.271873|1.046842x|
|primary_m16384_k8__sm_100a__pdl0|0.433153|0.410081|1.056262x|
|k_sweep_m1_k2__sm_100a__pdl0|0.004704|0.004096|1.148438x|
|k_sweep_m1_k3__sm_100a__pdl0|0.005120|0.004896|1.045752x|
|k_sweep_m1_k5__sm_100a__pdl0|0.005536|0.005088|1.088050x|
|k_sweep_m1_k6__sm_100a__pdl0|0.005920|0.005568|1.063218x|
|k_sweep_m1_k7__sm_100a__pdl0|0.006112|0.005760|1.061111x|
|k_sweep_m4096_k2__sm_100a__pdl0|0.060352|0.059552|1.013434x|
|k_sweep_m4096_k3__sm_100a__pdl0|0.072864|0.066751|1.091579x|
|k_sweep_m4096_k5__sm_100a__pdl0|0.087008|0.084192|1.033447x|
|k_sweep_m4096_k6__sm_100a__pdl0|0.101728|0.094976|1.071092x|
|k_sweep_m4096_k7__sm_100a__pdl0|0.108896|0.105856|1.028718x|
|primary_m1_k0__sm_100a__pdl1|0.004128|0.003200|1.290000x|
|primary_m1_k1__sm_100a__pdl1|0.004480|0.003776|1.186441x|
|primary_m1_k4__sm_100a__pdl1|0.005344|0.004992|1.070513x|
|primary_m1_k8__sm_100a__pdl1|0.006400|0.006016|1.063830x|
|primary_m2_k0__sm_100a__pdl1|0.004128|0.003168|1.303030x|
|primary_m2_k1__sm_100a__pdl1|0.004512|0.003840|1.175000x|
|primary_m2_k4__sm_100a__pdl1|0.005376|0.004993|1.076707x|
|primary_m2_k8__sm_100a__pdl1|0.006336|0.005984|1.058824x|
|primary_m4_k0__sm_100a__pdl1|0.004192|0.003200|1.310000x|
|primary_m4_k1__sm_100a__pdl1|0.004512|0.003872|1.165289x|
|primary_m4_k4__sm_100a__pdl1|0.005376|0.005056|1.063291x|
|primary_m4_k8__sm_100a__pdl1|0.006496|0.006144|1.057292x|
|primary_m8_k0__sm_100a__pdl1|0.004192|0.003200|1.310000x|
|primary_m8_k1__sm_100a__pdl1|0.004576|0.003936|1.162602x|
|primary_m8_k4__sm_100a__pdl1|0.005536|0.005216|1.061350x|
|primary_m8_k8__sm_100a__pdl1|0.006528|0.006176|1.056995x|
|primary_m16_k0__sm_100a__pdl1|0.004287|0.003265|1.313017x|
|primary_m16_k1__sm_100a__pdl1|0.004703|0.003936|1.194868x|
|primary_m16_k4__sm_100a__pdl1|0.005664|0.005344|1.059880x|
|primary_m16_k8__sm_100a__pdl1|0.006784|0.006432|1.054726x|
|primary_m32_k0__sm_100a__pdl1|0.004352|0.003392|1.283019x|
|primary_m32_k1__sm_100a__pdl1|0.004832|0.004160|1.161538x|
|primary_m32_k4__sm_100a__pdl1|0.006016|0.005728|1.050279x|
|primary_m32_k8__sm_100a__pdl1|0.007168|0.006816|1.051643x|
|primary_m64_k0__sm_100a__pdl1|0.004575|0.003616|1.265210x|
|primary_m64_k1__sm_100a__pdl1|0.005184|0.004544|1.140845x|
|primary_m64_k4__sm_100a__pdl1|0.006560|0.006272|1.045918x|
|primary_m64_k8__sm_100a__pdl1|0.007745|0.007647|1.012815x|
|primary_m128_k0__sm_100a__pdl1|0.005025|0.004096|1.226807x|
|primary_m128_k1__sm_100a__pdl1|0.005888|0.005280|1.115152x|
|primary_m128_k4__sm_100a__pdl1|0.007648|0.007264|1.052863x|
|primary_m128_k8__sm_100a__pdl1|0.008640|0.008576|1.007463x|
|primary_m256_k0__sm_100a__pdl1|0.006656|0.005312|1.253012x|
|primary_m256_k1__sm_100a__pdl1|0.008032|0.007520|1.068085x|
|primary_m256_k4__sm_100a__pdl1|0.010048|0.009952|1.009646x|
|primary_m256_k8__sm_100a__pdl1|0.012896|0.012512|1.030691x|
|primary_m512_k0__sm_100a__pdl1|0.009056|0.007616|1.189076x|
|primary_m512_k1__sm_100a__pdl1|0.010912|0.010240|1.065625x|
|primary_m512_k4__sm_100a__pdl1|0.015360|0.015104|1.016949x|
|primary_m512_k8__sm_100a__pdl1|0.021920|0.021120|1.037879x|
|primary_m1024_k0__sm_100a__pdl1|0.013215|0.011744|1.125255x|
|primary_m1024_k1__sm_100a__pdl1|0.016320|0.015744|1.036585x|
|primary_m1024_k4__sm_100a__pdl1|0.024352|0.023712|1.026991x|
|primary_m1024_k8__sm_100a__pdl1|0.036032|0.033600|1.072381x|
|primary_m2048_k0__sm_100a__pdl1|0.022464|0.021472|1.046200x|
|primary_m2048_k1__sm_100a__pdl1|0.027264|0.026847|1.015532x|
|primary_m2048_k4__sm_100a__pdl1|0.043008|0.040384|1.064976x|
|primary_m2048_k8__sm_100a__pdl1|0.064288|0.060736|1.058483x|
|primary_m4096_k0__sm_100a__pdl1|0.040576|0.039424|1.029221x|
|primary_m4096_k1__sm_100a__pdl1|0.050016|0.049344|1.013619x|
|primary_m4096_k4__sm_100a__pdl1|0.078592|0.075200|1.045106x|
|primary_m4096_k8__sm_100a__pdl1|0.118143|0.114144|1.035035x|
|primary_m8192_k0__sm_100a__pdl1|0.075712|0.074592|1.015015x|
|primary_m8192_k1__sm_100a__pdl1|0.092608|0.091935|1.007320x|
|primary_m8192_k4__sm_100a__pdl1|0.147743|0.141088|1.047169x|
|primary_m8192_k8__sm_100a__pdl1|0.223617|0.213120|1.049254x|
|primary_m16384_k0__sm_100a__pdl1|0.145921|0.144928|1.006848x|
|primary_m16384_k1__sm_100a__pdl1|0.182495|0.179071|1.019121x|
|primary_m16384_k4__sm_100a__pdl1|0.284769|0.272000|1.046945x|
|primary_m16384_k8__sm_100a__pdl1|0.433471|0.411040|1.054571x|
|k_sweep_m1_k2__sm_100a__pdl1|0.004736|0.004096|1.156250x|
|k_sweep_m1_k3__sm_100a__pdl1|0.005153|0.004927|1.045870x|
|k_sweep_m1_k5__sm_100a__pdl1|0.005569|0.005184|1.074371x|
|k_sweep_m1_k6__sm_100a__pdl1|0.005952|0.005568|1.068966x|
|k_sweep_m1_k7__sm_100a__pdl1|0.006176|0.005920|1.043243x|
|k_sweep_m4096_k2__sm_100a__pdl1|0.059584|0.058720|1.014714x|
|k_sweep_m4096_k3__sm_100a__pdl1|0.072896|0.066624|1.094140x|
|k_sweep_m4096_k5__sm_100a__pdl1|0.086944|0.084256|1.031903x|
|k_sweep_m4096_k6__sm_100a__pdl1|0.101504|0.094496|1.074162x|
|k_sweep_m4096_k7__sm_100a__pdl1|0.109312|0.106016|1.031090x|
|primary_m1_k0__sm_103a__pdl0|0.003936|0.003232|1.217822x|
|primary_m1_k1__sm_103a__pdl0|0.004097|0.003488|1.174599x|
|primary_m1_k4__sm_103a__pdl0|0.005055|0.004865|1.039054x|
|primary_m1_k8__sm_103a__pdl0|0.006144|0.005888|1.043478x|
|primary_m2_k0__sm_103a__pdl0|0.003808|0.002976|1.279570x|
|primary_m2_k1__sm_103a__pdl0|0.004257|0.003744|1.137019x|
|primary_m2_k4__sm_103a__pdl0|0.005024|0.004800|1.046667x|
|primary_m2_k8__sm_103a__pdl0|0.005953|0.005824|1.022150x|
|primary_m4_k0__sm_103a__pdl0|0.003904|0.003232|1.207921x|
|primary_m4_k1__sm_103a__pdl0|0.004256|0.003776|1.126969x|
|primary_m4_k4__sm_103a__pdl0|0.005023|0.004800|1.046458x|
|primary_m4_k8__sm_103a__pdl0|0.006176|0.006177|0.999838x|
|primary_m8_k0__sm_103a__pdl0|0.003968|0.003264|1.215686x|
|primary_m8_k1__sm_103a__pdl0|0.004224|0.003648|1.157895x|
|primary_m8_k4__sm_103a__pdl0|0.005152|0.004992|1.032051x|
|primary_m8_k8__sm_103a__pdl0|0.006272|0.006080|1.031579x|
|primary_m16_k0__sm_103a__pdl0|0.003936|0.003200|1.230000x|
|primary_m16_k1__sm_103a__pdl0|0.004352|0.003872|1.123967x|
|primary_m16_k4__sm_103a__pdl0|0.005408|0.005183|1.043411x|
|primary_m16_k8__sm_103a__pdl0|0.006272|0.006176|1.015544x|
|primary_m32_k0__sm_103a__pdl0|0.004128|0.003392|1.216981x|
|primary_m32_k1__sm_103a__pdl0|0.004512|0.004064|1.110236x|
|primary_m32_k4__sm_103a__pdl0|0.005632|0.005472|1.029240x|
|primary_m32_k8__sm_103a__pdl0|0.006816|0.006720|1.014286x|
|primary_m64_k0__sm_103a__pdl0|0.004320|0.003616|1.194690x|
|primary_m64_k1__sm_103a__pdl0|0.004865|0.004384|1.109717x|
|primary_m64_k4__sm_103a__pdl0|0.006464|0.006177|1.046463x|
|primary_m64_k8__sm_103a__pdl0|0.007584|0.007520|1.008511x|
|primary_m128_k0__sm_103a__pdl0|0.004864|0.004096|1.187500x|
|primary_m128_k1__sm_103a__pdl0|0.005601|0.005152|1.087151x|
|primary_m128_k4__sm_103a__pdl0|0.007264|0.007040|1.031818x|
|primary_m128_k8__sm_103a__pdl0|0.008512|0.008448|1.007576x|
|primary_m256_k0__sm_103a__pdl0|0.006368|0.005281|1.205832x|
|primary_m256_k1__sm_103a__pdl0|0.007744|0.007329|1.056624x|
|primary_m256_k4__sm_103a__pdl0|0.009792|0.009504|1.030303x|
|primary_m256_k8__sm_103a__pdl0|0.012672|0.012576|1.007634x|
|primary_m512_k0__sm_103a__pdl0|0.008672|0.007681|1.129085x|
|primary_m512_k1__sm_103a__pdl0|0.010592|0.010017|1.057402x|
|primary_m512_k4__sm_103a__pdl0|0.015264|0.015105|1.010526x|
|primary_m512_k8__sm_103a__pdl0|0.021952|0.021472|1.022355x|
|primary_m1024_k0__sm_103a__pdl0|0.013216|0.011712|1.128415x|
|primary_m1024_k1__sm_103a__pdl0|0.016033|0.015776|1.016291x|
|primary_m1024_k4__sm_103a__pdl0|0.024544|0.023936|1.025380x|
|primary_m1024_k8__sm_103a__pdl0|0.036545|0.034849|1.048667x|
|primary_m2048_k0__sm_103a__pdl0|0.022752|0.022080|1.030435x|
|primary_m2048_k1__sm_103a__pdl0|0.027553|0.027361|1.007017x|
|primary_m2048_k4__sm_103a__pdl0|0.044064|0.041153|1.070736x|
|primary_m2048_k8__sm_103a__pdl0|0.064865|0.062529|1.037359x|
|primary_m4096_k0__sm_103a__pdl0|0.040768|0.040161|1.015114x|
|primary_m4096_k1__sm_103a__pdl0|0.049376|0.049328|1.000963x|
|primary_m4096_k4__sm_103a__pdl0|0.080288|0.076097|1.055074x|
|primary_m4096_k8__sm_103a__pdl0|0.119042|0.116962|1.017784x|
|primary_m8192_k0__sm_103a__pdl0|0.077409|0.076705|1.009178x|
|primary_m8192_k1__sm_103a__pdl0|0.093921|0.093953|0.999659x|
|primary_m8192_k4__sm_103a__pdl0|0.151010|0.146338|1.031926x|
|primary_m8192_k8__sm_103a__pdl0|0.225986|0.217987|1.036695x|
|primary_m16384_k0__sm_103a__pdl0|0.148290|0.148001|1.001953x|
|primary_m16384_k1__sm_103a__pdl0|0.181507|0.181091|1.002297x|
|primary_m16384_k4__sm_103a__pdl0|0.291012|0.280260|1.038364x|
|primary_m16384_k8__sm_103a__pdl0|0.436870|0.419462|1.041501x|
|k_sweep_m1_k2__sm_103a__pdl0|0.004480|0.004001|1.119720x|
|k_sweep_m1_k3__sm_103a__pdl0|0.004768|0.004544|1.049296x|
|k_sweep_m1_k5__sm_103a__pdl0|0.005184|0.005088|1.018868x|
|k_sweep_m1_k6__sm_103a__pdl0|0.005728|0.005536|1.034682x|
|k_sweep_m1_k7__sm_103a__pdl0|0.005760|0.005632|1.022727x|
|k_sweep_m4096_k2__sm_103a__pdl0|0.059073|0.059168|0.998394x|
|k_sweep_m4096_k3__sm_103a__pdl0|0.073729|0.067489|1.092460x|
|k_sweep_m4096_k5__sm_103a__pdl0|0.088385|0.088449|0.999276x|
|k_sweep_m4096_k6__sm_103a__pdl0|0.102593|0.098241|1.044299x|
|k_sweep_m4096_k7__sm_103a__pdl0|0.110530|0.108225|1.021298x|
|primary_m1_k0__sm_103a__pdl1|0.003936|0.003168|1.242424x|
|primary_m1_k1__sm_103a__pdl1|0.004129|0.003520|1.173011x|
|primary_m1_k4__sm_103a__pdl1|0.005056|0.004833|1.046141x|
|primary_m1_k8__sm_103a__pdl1|0.006176|0.005920|1.043243x|
|primary_m2_k0__sm_103a__pdl1|0.003808|0.003008|1.265957x|
|primary_m2_k1__sm_103a__pdl1|0.004224|0.003744|1.128205x|
|primary_m2_k4__sm_103a__pdl1|0.005056|0.004832|1.046358x|
|primary_m2_k8__sm_103a__pdl1|0.006016|0.005760|1.044444x|
|primary_m4_k0__sm_103a__pdl1|0.003968|0.003264|1.215686x|
|primary_m4_k1__sm_103a__pdl1|0.004257|0.003776|1.127383x|
|primary_m4_k4__sm_103a__pdl1|0.004992|0.004800|1.040000x|
|primary_m4_k8__sm_103a__pdl1|0.006176|0.006016|1.026596x|
|primary_m8_k0__sm_103a__pdl1|0.004000|0.003296|1.213592x|
|primary_m8_k1__sm_103a__pdl1|0.004192|0.003616|1.159292x|
|primary_m8_k4__sm_103a__pdl1|0.005152|0.004928|1.045455x|
|primary_m8_k8__sm_103a__pdl1|0.006240|0.006048|1.031746x|
|primary_m16_k0__sm_103a__pdl1|0.003904|0.003169|1.231934x|
|primary_m16_k1__sm_103a__pdl1|0.004384|0.003872|1.132231x|
|primary_m16_k4__sm_103a__pdl1|0.005345|0.005152|1.037461x|
|primary_m16_k8__sm_103a__pdl1|0.006368|0.006176|1.031088x|
|primary_m32_k0__sm_103a__pdl1|0.004128|0.003424|1.205607x|
|primary_m32_k1__sm_103a__pdl1|0.004544|0.004032|1.126984x|
|primary_m32_k4__sm_103a__pdl1|0.005664|0.005472|1.035088x|
|primary_m32_k8__sm_103a__pdl1|0.006848|0.006688|1.023923x|
|primary_m64_k0__sm_103a__pdl1|0.004321|0.003616|1.194967x|
|primary_m64_k1__sm_103a__pdl1|0.004897|0.004416|1.108922x|
|primary_m64_k4__sm_103a__pdl1|0.006400|0.006144|1.041667x|
|primary_m64_k8__sm_103a__pdl1|0.007616|0.007393|1.030164x|
|primary_m128_k0__sm_103a__pdl1|0.004800|0.004096|1.171875x|
|primary_m128_k1__sm_103a__pdl1|0.005632|0.005216|1.079755x|
|primary_m128_k4__sm_103a__pdl1|0.007392|0.007104|1.040541x|
|primary_m128_k8__sm_103a__pdl1|0.008512|0.008352|1.019157x|
|primary_m256_k0__sm_103a__pdl1|0.006528|0.005441|1.199779x|
|primary_m256_k1__sm_103a__pdl1|0.007712|0.007392|1.043290x|
|primary_m256_k4__sm_103a__pdl1|0.009761|0.009505|1.026933x|
|primary_m256_k8__sm_103a__pdl1|0.012641|0.012544|1.007733x|
|primary_m512_k0__sm_103a__pdl1|0.008768|0.007745|1.132085x|
|primary_m512_k1__sm_103a__pdl1|0.010496|0.009984|1.051282x|
|primary_m512_k4__sm_103a__pdl1|0.015296|0.015040|1.017021x|
|primary_m512_k8__sm_103a__pdl1|0.021824|0.021536|1.013373x|
|primary_m1024_k0__sm_103a__pdl1|0.013248|0.011168|1.186246x|
|primary_m1024_k1__sm_103a__pdl1|0.016032|0.015744|1.018293x|
|primary_m1024_k4__sm_103a__pdl1|0.024545|0.023584|1.040748x|
|primary_m1024_k8__sm_103a__pdl1|0.036512|0.034497|1.058411x|
|primary_m2048_k0__sm_103a__pdl1|0.022816|0.022176|1.028860x|
|primary_m2048_k1__sm_103a__pdl1|0.027648|0.027392|1.009346x|
|primary_m2048_k4__sm_103a__pdl1|0.044097|0.041089|1.073207x|
|primary_m2048_k8__sm_103a__pdl1|0.065008|0.062656|1.037546x|
|primary_m4096_k0__sm_103a__pdl1|0.040736|0.040128|1.015152x|
|primary_m4096_k1__sm_103a__pdl1|0.049536|0.049281|1.005174x|
|primary_m4096_k4__sm_103a__pdl1|0.080577|0.076417|1.054438x|
|primary_m4096_k8__sm_103a__pdl1|0.119426|0.118178|1.010560x|
|primary_m8192_k0__sm_103a__pdl1|0.077537|0.076864|1.008756x|
|primary_m8192_k1__sm_103a__pdl1|0.094081|0.093953|1.001362x|
|primary_m8192_k4__sm_103a__pdl1|0.151202|0.146595|1.031427x|
|primary_m8192_k8__sm_103a__pdl1|0.226147|0.218530|1.034856x|
|primary_m16384_k0__sm_103a__pdl1|0.148354|0.147970|1.002595x|
|primary_m16384_k1__sm_103a__pdl1|0.181955|0.181315|1.003530x|
|primary_m16384_k4__sm_103a__pdl1|0.290916|0.280420|1.037430x|
|primary_m16384_k8__sm_103a__pdl1|0.436677|0.419013|1.042157x|
|k_sweep_m1_k2__sm_103a__pdl1|0.004480|0.003969|1.128748x|
|k_sweep_m1_k3__sm_103a__pdl1|0.004672|0.004512|1.035461x|
|k_sweep_m1_k5__sm_103a__pdl1|0.005215|0.005088|1.024961x|
|k_sweep_m1_k6__sm_103a__pdl1|0.005728|0.005536|1.034682x|
|k_sweep_m1_k7__sm_103a__pdl1|0.005729|0.005568|1.028915x|
|k_sweep_m4096_k2__sm_103a__pdl1|0.059425|0.059457|0.999462x|
|k_sweep_m4096_k3__sm_103a__pdl1|0.073633|0.067394|1.092575x|
|k_sweep_m4096_k5__sm_103a__pdl1|0.088674|0.088352|1.003645x|
|k_sweep_m4096_k6__sm_103a__pdl1|0.102785|0.098274|1.045902x|
|k_sweep_m4096_k7__sm_103a__pdl1|0.110338|0.108610|1.015910x|

## Geomeans over all correct timed rows

Gate-failing performance rows remain in these geomeans; only rows
without valid correctness and timing are excluded and remain visible
above.

|Shape tag|Timed rows|Denominator|Source ms|Export ms|Source / Export|
|---|---:|---:|---:|---:|---:|
|all|300|300|0.013486|0.013471|1.001128x|
|correctness|20|20|0.013375|0.013405|0.997753x|
|full_k_sweep|72|72|0.018496|0.018492|1.000188x|
|pdl_off|150|150|0.013481|0.013473|1.000636x|
|pdl_on|150|150|0.013491|0.013470|1.001620x|
|perf|280|280|0.013494|0.013476|1.001369x|
|primary_geomean|240|240|0.012628|0.012603|1.001923x|

### Geomeans: pinned vLLM SM100f native CUDA AttnRes op
(csrc/libtorch_stable/kimi_k3/attn_res_kernel.cu)

|Shape tag|Timed rows|Denominator|Baseline ms|Paired export ms|Baseline
/ Export|
|---|---:|---:|---:|---:|---:|
|all|280|280|0.014539|0.013476|1.078924x|
|full_k_sweep|72|72|0.019673|0.018492|1.063868x|
|pdl_off|140|140|0.014534|0.013479|1.078270x|
|pdl_on|140|140|0.014545|0.013473|1.079579x|
|perf|280|280|0.014539|0.013476|1.078924x|
|primary_geomean|240|240|0.013657|0.012603|1.083556x|

Complete denominator: **true** (300/300).

All gates passed: **true** (300/300).
## What changed in this revision

This revision regenerates the delivery after a schedule-selection round
on the generator side; no emitted file was hand-edited, no kernel math,
tolerance or cast point changed, and every row keeps the same
correctness oracle (FP32 reference, BF16 outputs at atol 0.08 / rtol
0.03, in-place state bit-exact).

- **sm_100a (B200)**: `primary_m256_k8` moves to the dedicated K8
program (the row that was at 0.9805 against vLLM); the K0 rows use the
unpacked norm cache and a 2x TMA grid at M 256-1024; `primary_m512_k1`
runs two sources per chunk; the K4 rows at M 2048-16384 and the K3/K5
rows at M 4096 run three sources per chunk with a depth-3 pipeline.
- **sm_103a (B300)**: K0 TMA grid 2x/3x/3x at M 256/512/1024; the K4
rows at M 1024-4096 run three sources per chunk with a depth-3 pipeline;
`primary_m1_k8`, `primary_m8_k8` and the PDL-off `k_sweep_m1_k7` move to
the dedicated K8/K7 programs.
- Same-GPU ABBA timing (CUPTI, cold L2, first block authoritative) of
each adopted change against the previous delivery: adopted rows
0.910-0.988 (new / delivered time), control rows 1.000-1.0001 (26 rows;
every other row is a byte-identical program).
- Generated kernel files: 47 (from 50) (47 distinct bodies); PDL stays a
launch argument; architecture-identical programs stay shared.

## Baselines and their source PRs

- **Cake production AttnRes launcher** (parity arm, `source / export`
ratios): the same generated programs launched through the Cake
production dispatcher at the producer revision recorded in the summary.
- **vLLM native CUDA AttnRes op** (external baseline, `baseline /
export` ratios): `csrc/libtorch_stable/kimi_k3/attn_res_kernel.cu` from
https://github.com/vllm-project/vllm at revision
`ee3c00bbf47e0ef7e975705cc980b06ee5576bb0`, built from source on the
measuring node:
- vllm-project/vllm#50090 (`61ac3680`, 2026-07-28) — add AttnRes kernels
- vllm-project/vllm#50567 (`41ba11b8`, 2026-08-04) — enforce packed rows
and op availability in AttnRes dispatch
- vllm-project/vllm#50185 (`7b4ed496`, 2026-08-06) — attn_res kernel
latency improvements
- vllm-project/vllm#54261 (`d6d66585`, 2026-08-31) — make native CUDA
AttnRes the SM100 default
- **Correctness oracle**: FP32 PyTorch reference of the AttnRes op (BF16
outputs checked at atol 0.08 / rtol 0.03; in-place state bit-exact),
applied to source, export and vLLM arms before and after each timing
block.

## Acceptance

Every perf row must satisfy `vLLM / export >= 0.97` (owner decision
2026-10-01). Final measurement at Cake producer `f125b4d83bd` against
this scaffold (`c82391fc118`; sm_100a on 3x B200, sm_103a on 3x B300):
**300 / 300 rows pass**, 275 / 280 perf rows at or above 1.0. Rows below
1.0:

| row | vLLM / export |
| --- | --- |
| k_sweep_m4096_k2 (sm_103a, pdl0 / pdl1) | 0.9984 / 0.9995 |
| k_sweep_m4096_k5 (sm_103a, pdl0) | 0.9993 |
| primary_m8192_k1 (sm_103a, pdl0) | 0.9997 |
| primary_m4_k8 (sm_103a, pdl0) | 0.9998 |

All five run programs unchanged from the previous delivery; every
sm_100a perf row is at or above 1.0 (previous delivery:
`primary_m256_k8` 0.9805 -> 1.025 / 1.033, `primary_m16384_k0` 0.9961 ->
1.0075 / 1.0073).

Geomean of `vLLM / export` over the perf rows: 1.090 (sm_100a), 1.067
(sm_103a); previous delivery 1.080 / 1.067. Per-row `vLLM / export`
against the previous delivery: 61 rows > 1 % faster, 23 rows > 1 %
slower of which 21 are unchanged sm_103a small-M programs measured on a
different B300 node; a same-GPU ABBA of the previous delivery against
this one on those rows is 0.996-1.0045 (one 32 ns tick), so no program
regressed.

## CI

```
/bot run tests/experimental/test_cake_kimi_k3_attn_res.py
@flashinfer-bot run tests/experimental/test_cake_kimi_k3_attn_res.py
```

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Performance**
* Updated attention-kernel scheduling across supported GPU architectures
and workload sizes, including configurations for processing up to three
sources per chunk.
* Adjusted grid sizing and persistent-kernel selection for selected
workloads.
* **Documentation**
* Updated the documented routing ranges and grid configuration for
selected routes.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-10-03
**监控日期**: 2026-10-02
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4540
- **最后更新**: 2026-10-02T19:37:40Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: lpc0220, William Lin

## AI分析总结

# FastVideo 昨日提交分析（第 1/1 批）

## 1. 主要更新类型
本次提交为 **Bug 修复 + 功能新增** 的组合：
- 提交 #1904 属于底层 GPU 内存一致性 Bug 修复
- 提交 #1907 属于推理功能新增（参考视频驱动的稀疏推理）

## 2. 关键变更点及其与项目整体方向的关系

**Bug 修复（#1904）**：修复了 sm_100a（NVIDIA Blackwell 架构指令集）上 VSA（视频稀疏注意力）模块中 CLC（硬件协同处理单元）响应读取与槽位释放之间的竞态条件，引入内存屏障（fence）保证顺序性，同时理顺了 PV（point-value）描述符的生命周期传递。

**功能新增（#1907）**：实现了 FastH3 Ref2VA 模型的 PDD（并行解码发散）推理路径，支持**参考视频（reference-video）场景下的 VSA 稀疏注意力**。

这两个变更与 FastVideo 以“极致推理效率”为核心的目标高度一致：前者夯实了新硬件平台的正确性底座，后者把视频稀疏注意力这一核心性能抓手扩展到了参考视频生成这一热门场景，延续了“效率优先”的框架哲学。

## 3. 对项目的影响和潜在意义
- **稳定性提升**：内存屏障修复直接消除了一类难以复现的 GPU 竞态崩溃，对 Blackwell（sm_100a）用户意义重大，说明项目已开始为下一代 GPU 做前瞻适配。
- **能力边界扩展**：Ref2VA + PDD + VSA 稀疏的组合，意味着参考视频生成推理也能享受稀疏加速，有助于降低长视频、多视频输入下的显存与计算开销。
- **开发模式信号**：两个提交均带有 Claude Opus 5.5 的 Co-authored-by 署名，显示该项目正在积极探索 AI 辅助开发的工作流。

## 4. 值得关注的技术点
- **指令级内存一致性**：`fence` 指令在 CLC 响应读取前的插入，属于 PTX/CUDA 底层优化，说明项目维护者对 GPU 并行原语（stream、slot、descriptor）有深入掌控。
- **描述符生命周期管理**：PV descriptor 的 forward 处理涉及跨 kernel 的资源释放顺序，是典型的 GPU 异步编程陷阱。
- **VSA 稀疏模式的场景复用**：将原有视频稀疏注意力机制迁移到参考视频路径，体现了框架内注意力模块的高度可复用性设计。
- **PDD 调度策略**：PDD 是 FastVideo 提高吞吐的核心调度机制，其在 Ref2VA 上的落地值得关注后续的性能基准数据。

## 5. 结合 README 背景对项目发展的影响
FastVideo（hao-ai-lab）定位于视频生成与推理的高效框架，README 中的 Quick Start、Cookbook、Weekly Dev Meeting 与 Slack 社区表明项目正处于活跃的工程化与社区建设阶段。上述提交从两个维度支撑了这一发展主线：

- **硬件兼容性层面**：sm_100a 的 bug 修复意味着项目在为 Blackwell 平台提前铺路，这与“Fast”定位相匹配，能在新硬件发布时第一时间兑现性能优势。
- **功能成熟度层面**：Ref2VA PDD 推理的引入丰富了参考视频这一重要用例，配合 VSA 稀疏性，有望形成“参考视频生成也能跑得快”的差异化卖点，吸引更多研究者与工程团队采用。

总体而言，这批提交虽不多，但一修一增分别夯实了地基与上层能力，对 FastVideo 巩固其在高效视频推理赛道的技术领先地位具有积极意义。

## 详细提交记录

### [0cc41a2](https://github.com/hao-ai-lab/FastVideo/commit/0cc41a22dc651a7b77a559225f0cbdfe384e8c98)

- **作者**: lpc0220
- **时间**: 2026-10-02T19:37:34Z
- **提交信息**: [bugfix] sm_100a VSA: fence the CLC response read before the slot release; forward PV descriptor lifetime (#1904)


Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [8444c08](https://github.com/hao-ai-lab/FastVideo/commit/8444c0897a8b96848eb85b6e5750ef486f79fc92)

- **作者**: William Lin
- **时间**: 2026-10-02T18:28:07Z
- **提交信息**: [feat] FastH3 Ref2VA PDD inference with reference-video VSA sparsity (#1907)

Co-authored-by: Davids048 <jundasu@ucsd.edu>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-10-03
**监控日期**: 2026-10-02
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34642
- **最后更新**: 2026-10-03T01:11:52Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 3
- **主要提交者**: YiYi Xu, TB, yzhautouskay

## AI分析总结

## huggingface/diffusers 昨日提交分析（第 1/1 批）

### 1. 主要更新类型
本次共 3 个提交，构成以 **Bug修复** 为主、**文档更新** 为辅的组合：涉及一个文档澄清类提交和两个模型层面的技术修复（分别针对 Cosmos3 和 Krea 2 两个新模型）。

### 2. 关键变更点及与项目整体方向的关系
- **文档收敛（8b33bfc）**：对 agent 相关文档做了"仅保留已发布 checkpoint 实际使用内容"的收紧，多人协作审核（Steven Liu、yiyixuxu 多轮 review），体现了项目对**文档与实际能力对齐**的重视，减少用户按文档尝试但模型不支持的误导。
- **Cosmos3 FP8 张量并行修复（357f873）**：修复 Cosmos3 在 FP8 精度下的张量并行（Tensor Parallelism）问题，属于高性能/低精度训练推理场景的关键修复，与 diffusers 持续集成**新架构（如 Cosmos 系列）和分布式/量化支持**的方向一致。
- **Krea 2 字段标记（4156630）**：为 Krea 2 的 text encoder 输出打上 `denoiser_input_fields` 标记，这是管道流水线内部的接口一致性修复，确保 Krea 2 模型在 diffusers 管道中正确消费文本编码输出。

### 3. 对项目的影响和潜在意义
- **可用性提升**：Cosmos3 FP8 张量并行修复可直接让使用该模型进行多卡 FP8 推理/训练的用户恢复功能，避免实际部署踩坑。
- **维护质量**：文档只保留已验证能力，降低了开源社区的"文档-代码"不一致成本；两处新模型修复表明项目近期正快速集成多个新模型（Cosmos、Krea），这些提交是保证这些新集成真正可用的收尾工作。
- **协作模式**：Cosmos3 的修复几乎无人工 review 说明是小而确定的补丁；文档提交经过多轮 review，反映社区对用户可见内容的严谨态度。

### 4. 值得关注的技术点
- **FP8 + 张量并行**：FP8 是低比特量化的重要方向，其与张量并行的组合涉及通信与精度的平衡，是大模型高效部署的热点技术栈，diffusers 在此持续修复说明该组合仍有边界问题需打磨。
- **`denoiser_input_fields` 机制**：这是 diffusers 管道中用于描述模型输入字段的内部协议，Krea 2 依赖该标记说明 diffusers 正在为不同新模型建立统一的流水线输入约定，这有助于后续新模型接入的一致性。
- **文档与 checkpoint 版本绑定**：按"已发布 checkpoint"而非"理论支持范围"撰写文档，是大型模型库文档治理的成熟实践。

### 5. 对项目发展的整体影响
基于 README 可知 diffusers 是 Apache 2.0 开源许可的扩散模型库，以 HuggingFace 生态为核心。这些提交体现了项目当前的两条发展主线：**一是持续快速接入前沿新模型**（Cosmos3、Krea 2 等），提交记录显示这些新模型的集成仍在迭代打磨阶段，尚未完全稳定；**二是重视工程质量**，通过文档收敛、低精度分布式修复、流水线接口统一等方式保证新增能力的可靠性。整体上，这些提交虽单个规模不大，但共同支撑了项目从"能跑"向"好用、可信"的演进方向，是大型开源 ML 库进入成熟期后的典型维护节奏。

## 详细提交记录

### [8b33bfc](https://github.com/huggingface/diffusers/commit/8b33bfc04b6b5e8bb58a58e55f68746c1bbee4cd)

- **作者**: YiYi Xu
- **时间**: 2026-10-02T23:59:22Z
- **提交信息**: agent docs: support only what released checkpoints use (#14750)

* agent docs: support only what released checkpoints use

Co-Authored-By: Claude Fable 5 <noreply@anthropic.com>

* Apply suggestion from @stevhliu

Co-authored-by: Steven Liu <59462357+stevhliu@users.noreply.github.com>

* Apply suggestion from @stevhliu

Co-authored-by: Steven Liu <59462357+stevhliu@users.noreply.github.com>

* Apply suggestion from @stevhliu

Co-authored-by: Steven Liu <59462357+stevhliu@users.noreply.github.com>

* Apply suggestion from @stevhliu

Co-authored-by: Steven Liu <59462357+stevhliu@users.noreply.github.com>

* Apply suggestion from @stevhliu

Co-authored-by: Steven Liu <59462357+stevhliu@users.noreply.github.com>

* Apply suggestion from @yiyixuxu

---------

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: Steven Liu <59462357+stevhliu@users.noreply.github.com>

### [357f873](https://github.com/huggingface/diffusers/commit/357f8738cdc050e3435e920ff3968a0bc101d4bb)

- **作者**: yzhautouskay
- **时间**: 2026-10-02T19:49:42Z
- **提交信息**: [Bugfix] Fix Cosmos3 FP8 tensor parallelism (#14921)

Fix Cosmos3 FP8 tensor parallelism

### [4156630](https://github.com/huggingface/diffusers/commit/41566305ceeee4e84880df3eb64f86bc84e7994b)

- **作者**: TB
- **时间**: 2026-10-02T19:17:50Z
- **提交信息**: Tag Krea 2 text encoder outputs as denoiser_input_fields (#14925)

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-10-03
**监控日期**: 2026-10-02
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


**报告日期**: 2026-10-03
**监控日期**: 2026-10-02
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13200
- **最后更新**: 2026-10-02T17:43:38Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-10-03
**监控日期**: 2026-10-02
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 36729
- **最后更新**: 2026-10-03T01:03:22Z

## 提交统计

- **昨日提交总数**: 33
- **提交者数量**: 19
- **主要提交者**: Kan Wu, kk, Po-Han Huang (NVIDIA)

## AI分析总结

## sglang 昨日提交分析总结

### 1. 主要更新类型
- **性能优化与内核增强**（占比最大）：包括 MXFP8 激活量化融合、ConvRot INT8 在线 W8A8 量化、Cake softmax 采样、VMM 输入交换大小调整、H2D 拷贝非阻塞化等。
- **新功能新增**：sgl-router 扩展 OpenAI 兼容接口（/v1/embeddings、/v1/rerank、/v1/classify、/generate 原生端点）、MiniMax-M3 TP4 上下文分区、统一内存 compaction 优化。
- **Bug 修复**：Qwen3.5 EAGLE3/DFLASH 捕获修复、NIXL 下不同长度 KV 条目的 dlist 修复、AMD AITER 补丁跳过、测试修复等。
- **重构与清理**：移除 CP adapter、mem_cache 的 `insert_req` 改名为 `checkpoint`、统一 sgl-router 的 session/cache affinity 模式。
- **文档与 CI 更新**：AMD 文档镜像更新、CUDA 12 镜像标签固定、AMD CI 测试超时修复与分片。

### 2. 关键变更点及与项目方向的关系
- **路由器能力大幅增强**：sgl-router 连续添加 OpenAI 兼容的 embeddings/rerank/classify 及原生 generate 端点，并统一了 affinity 模式，表明项目正将路由器从纯 LLM 路由器扩展为全能力的推理网关。
- **多硬件生态深化**：AMD/ROCm 路线活跃（gfx950 MXFP8 融合、MI355X 镜像、AITER 补丁处理），NVIDIA SM103/SM120 也同步优化，反映项目对异构硬件推理的持续投入。
- **投机解码与内存子系统持续迭代**：EAGLE3/DFLASH 修复、Mamba COW 内核预热、HiCache 回退到宿主内存、mem_cache 语义清理，均为提升长上下文与高吞吐场景的稳定性。
- **PD 分离与分布式通信优化**：PD 重叠下非阻塞 H2D、EPLB NCCL P2P 预热、NIXL 修复，直接服务于大规模分离式部署的正确性与性能。

### 3. 对项目的影响和潜在意义
- 路由器接口的统一与补全降低了用户从 vLLM/OpenAI 栈迁移的成本，有利于生态扩张。
- 多硬件支持的成熟度提升（尤其 AMD MI355X 路线）使 SGLang 在企业级推理市场更具竞争力。
- 大量内存/内核层微优化的积累，将持续推动 SGLang 在"Fast inference"这一核心定位上的性能优势。

### 4. 值得关注的技术点
- **MXFP8 激活量化融入 producer 内核**：减少 kernel launch 与中间拷贝，对 Blackwell 之外的新硬件也有借鉴意义。
- **ConvRot INT8 在线 W8A8**：将量化成本摊入算子内部，对 diffusion 模型推理开销有实质改善。
- **Cake softmax（SM103）**：针对新采样硬件的专用路径选择机制。
- **`checkpoint` 命名重构**：暗示 mem_cache 请求级树结构正朝更接近传统 KV cache 抽象演进。
- **统一内存 compaction 中 page envelope 的 in-place 拷贝**：减少 compaction 停顿的细节优化。
- 本次提交中出现多个 Claude Opus 协作者署名，反映 AI 辅助编程在该项目中的常态化。

### 5. 对项目整体发展的影响
基于 README 中"Fast inference for LLMs and multimodal models"的定位，这批提交体现了三条清晰的演进脉络：其一，以多硬件内核优化夯实性能底座；其二，以路由器的 OpenAI 兼容接口完善产品化出口；其三，以投机解码、PD 分离、HiCache 等组件的稳定性修复强化生产级部署能力。这些工作共同推动 SGLang 从一个研究性推理框架向可支撑多硬件、多模态、大规模生产部署的基础设施演进，同时其多供应商协同（AMD、NVIDIA、AI 实验室）的开发模式也强化了项目作为开源推理枢纽的地位。

## 详细提交记录

### [3bde8eb](https://github.com/sgl-project/sglang/commit/3bde8eb2d871f3840d317bc670873193b4f63725)

- **作者**: Baizhou Zhang
- **时间**: 2026-10-02T23:50:20Z
- **提交信息**: [CP 1/5] Remove the CP adapter and separate interleave transport from boundary reduction (#42036)

### [cbe070b](https://github.com/sgl-project/sglang/commit/cbe070b6bfce18936620f406b9b0d71bdc17452b)

- **作者**: Zhang, Jiejing
- **时间**: 2026-10-02T22:39:07Z
- **提交信息**: [Docs][AMD] Update GLM-5.2 MI355X daily image to 20260930 (#42278)

### [b69a5f2](https://github.com/sgl-project/sglang/commit/b69a5f296ae79444b5537f6a36f80c731f7e9ac2)

- **作者**: Thomas Ning
- **时间**: 2026-10-02T22:34:29Z
- **提交信息**: [AMD] Add opt-in MiniMax-M3 TP4 indexer context partitioning (#41488)

Co-authored-by: ThomasNing <thomas.ning@amd.com>
Co-authored-by: Kevin Mi <mikevin920@yahoo.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>
Co-authored-by: Kevin Mi <45493463+kevin-mii@users.noreply.github.com>

### [fa7784d](https://github.com/sgl-project/sglang/commit/fa7784d140eef70223cabf942ab81d53a48fdb0a)

- **作者**: metamergebot
- **时间**: 2026-10-02T22:12:14Z
- **提交信息**: [unified-memory] Copy page envelopes in place during compaction (#42252)

Co-authored-by: merrymercy <merrymercy@users.noreply.github.com>
Co-authored-by: ZYHowell <ZYHowell@users.noreply.github.com>

### [e8fab85](https://github.com/sgl-project/sglang/commit/e8fab85a02c23e01260fb1adb030b00886f5999d)

- **作者**: metamergebot
- **时间**: 2026-10-02T21:59:56Z
- **提交信息**: [KDA] Add an opt-in decode-parity mode to the Triton multi-token recurrence (#42251)

Co-authored-by: merrymercy <merrymercy@users.noreply.github.com>
Co-authored-by: jiayisuse <jiayisuse@users.noreply.github.com>

### [19794f5](https://github.com/sgl-project/sglang/commit/19794f5743b08e40eefc39ae5974b9b6cb3877c7)

- **作者**: Kan Wu
- **时间**: 2026-10-02T21:56:16Z
- **提交信息**: [sgl-router] Add SGLang's /v1/classify (#42258)

Co-authored-by: Kan Wu <kan.wu@radixark.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [8a328e8](https://github.com/sgl-project/sglang/commit/8a328e867bec900dc18558f3c2d818fd5e827cf5)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-02T21:42:35Z
- **提交信息**: [mem_cache] Rename the tree's request-level `insert_req` to `checkpoint` (#42202)

### [2ec9e3b](https://github.com/sgl-project/sglang/commit/2ec9e3b11d5cc5d76716dfbfc3874420833f6961)

- **作者**: metamergebot
- **时间**: 2026-10-02T21:34:55Z
- **提交信息**: [eplb] Warm default-group NCCL P2P transports before KV-cache sizing (#42026)

Co-authored-by: merrymercy <merrymercy@users.noreply.github.com>
Co-authored-by: luccafong <luccafong@users.noreply.github.com>

### [ebf161c](https://github.com/sgl-project/sglang/commit/ebf161cea42c0204d9dd2e18338ceb0954b83a01)

- **作者**: Kan Wu
- **时间**: 2026-10-02T21:33:40Z
- **提交信息**: [sgl-router] Add SGLang's /v1/rerank (#42205)

Co-authored-by: Kan Wu <kan.wu@radixark.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [8c9030c](https://github.com/sgl-project/sglang/commit/8c9030ce3f58eec16ad3b9912d37480d34d6de52)

- **作者**: Kan Wu
- **时间**: 2026-10-02T21:21:22Z
- **提交信息**: [sgl-router] Unify reorg session and cache affinity modes (#41990)

Co-authored-by: Kan Wu <kan.wu@radixark.ai>

### [0098b9d](https://github.com/sgl-project/sglang/commit/0098b9d29d5b00f2791edde2afd54db829aa723a)

- **作者**: Yuhao Wang
- **时间**: 2026-10-02T21:05:01Z
- **提交信息**: [Spec] Fix Qwen3.5 text model EAGLE3/DFLASH aux-layer capture (#42002)

### [a64725d](https://github.com/sgl-project/sglang/commit/a64725d407e525652fb7679a7e9c0bf9f356f01e)

- **作者**: raghotham
- **时间**: 2026-10-02T20:59:40Z
- **提交信息**: [HiCache] Fall back to host memory when no cgroup fs is mounted (#42120)

### [7dd93b0](https://github.com/sgl-project/sglang/commit/7dd93b01a5421bd0a52cd78a9ef1dce3457db07b)

- **作者**: metamergebot
- **时间**: 2026-10-02T20:48:39Z
- **提交信息**: [PD] Make the prebuilt last-token H2D copy non-blocking under overlap (#42113)

Co-authored-by: merrymercy <merrymercy@users.noreply.github.com>
Co-authored-by: bbus <bbus@users.noreply.github.com>

### [07e1a4f](https://github.com/sgl-project/sglang/commit/07e1a4f0821ef09a1bf87e2fcb7f326183658295)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-02T20:46:32Z
- **提交信息**: [mem_cache] Skip the release-time insert on optimistic prefill requeue; make `refresh_fill_ids` public (#42194)

### [354ed2a](https://github.com/sgl-project/sglang/commit/354ed2a7b653c7e440d276c5cf67b465f28f746f)

- **作者**: metamergebot
- **时间**: 2026-10-02T20:45:32Z
- **提交信息**: Size the VMM graph-input exchange by the widest input across ranks (#42125)

Co-authored-by: merrymercy <merrymercy@users.noreply.github.com>
Co-authored-by: oulgen <oulgen@users.noreply.github.com>

### [4a4dad1](https://github.com/sgl-project/sglang/commit/4a4dad1cf119ba48627419d0689afbf1378d260d)

- **作者**: metamergebot
- **时间**: 2026-10-02T20:43:53Z
- **提交信息**: [Metrics] Label scheduler stage wall time by sampled forward overlap (#42025)

Co-authored-by: merrymercy <merrymercy@users.noreply.github.com>
Co-authored-by: Jialin <Jialin@users.noreply.github.com>

### [f6fcda8](https://github.com/sgl-project/sglang/commit/f6fcda8827e5d8a2f0b999cd3b32f5096ee6a82c)

- **作者**: ChangLiu0709
- **时间**: 2026-10-02T18:57:03Z
- **提交信息**: [AMD][ROCm] Keep cos_sin_cache fp32 on HIP for fused QSA indexer kernel (#41282)

Co-authored-by: Nikolai Protasov <289648307+amd-nprotaso@users.noreply.github.com>

### [89f2167](https://github.com/sgl-project/sglang/commit/89f21671bb4f1b070e1eb72ed06ebb90882948bf)

- **作者**: Shuwen Wang
- **时间**: 2026-10-02T15:49:38Z
- **提交信息**: fix: preserve QSA indexer state through HiCache (#39893)

### [a74f259](https://github.com/sgl-project/sglang/commit/a74f259f38152e2e15cdd7590c0072cdf70b4e61)

- **作者**: kk
- **时间**: 2026-10-02T15:34:44Z
- **提交信息**: [AMD][V4.1][*/N] Fuse MXFP8 activation quant into producer kernels on gfx950 (#42055)

Co-authored-by: wunhuang <wunhuang@amd.com>

### [e667ab1](https://github.com/sgl-project/sglang/commit/e667ab10d5f76f34e3a949ec0e82f5568f7a0afc)

- **作者**: Alex O. P.
- **时间**: 2026-10-02T15:26:28Z
- **提交信息**: [diffusion] quantization: ConvRot INT8 online W8A8 for DiTs (sgl-kernel + `convrot_int8_customkernel`) (#38040)

Co-authored-by: Po-Han Huang (NVIDIA) <53919306+nvpohanh@users.noreply.github.com>

### [1a2eb6c](https://github.com/sgl-project/sglang/commit/1a2eb6c426219312bfb000dfb36cf4afcfcf79b0)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-10-02T15:06:43Z
- **提交信息**: [Kernel] Use Cake softmax for qualified SM103 sampling workloads (#42004)

### [bb9a820](https://github.com/sgl-project/sglang/commit/bb9a820f09f97480bfc6d07564fb2b691b8857a3)

- **作者**: Mick
- **时间**: 2026-10-02T13:44:10Z
- **提交信息**: [diffusion] chore: make perf dump one writer per replica with no first-request NCCL setup (#41711)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [2cd92d1](https://github.com/sgl-project/sglang/commit/2cd92d10b98a73de3952eafca915ae8954fcd375)

- **作者**: Michael
- **时间**: 2026-10-02T13:10:01Z
- **提交信息**: [AMD] Skip the AITER #6042/#5967 patches on gfx1250 (#42219)

### [edee430](https://github.com/sgl-project/sglang/commit/edee4308bcd7204d550234189d52a4cc25d93348)

- **作者**: Kan Wu
- **时间**: 2026-10-02T12:18:24Z
- **提交信息**: [sgl-router] Add OpenAI /v1/embeddings (#42191)

Co-authored-by: Kan Wu <kan.wu@radixark.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [1330e43](https://github.com/sgl-project/sglang/commit/1330e437e1b9c1ee02c1c0cdeba63b78bf029706)

- **作者**: Kan Wu
- **时间**: 2026-10-02T12:09:04Z
- **提交信息**: [sgl-router] Add native /generate endpoint (#42147)

Co-authored-by: Kan Wu <kan.wu@radixark.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [e020b38](https://github.com/sgl-project/sglang/commit/e020b389b62b8a349074c895651ea0c56e725649)

- **作者**: Michael
- **时间**: 2026-10-02T11:29:20Z
- **提交信息**: [AMD][CI] Partition stage-b-test-1-gpu-small-amd-mi35x to stop the 30-min timeout (#41973)

### [0f71ec8](https://github.com/sgl-project/sglang/commit/0f71ec8656374b80da728c55217a2a073fac9ef5)

- **作者**: Mick
- **时间**: 2026-10-02T11:25:15Z
- **提交信息**: [diffusion] UX: deduplicate SM120 FP8 fallback warnings across layers (#41542)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [544e46c](https://github.com/sgl-project/sglang/commit/544e46c0806df652f700574c36530b24efb02c4f)

- **作者**: Michael
- **时间**: 2026-10-02T10:59:05Z
- **提交信息**: [AMD][CI] Fix VLM MMMU nightly max_tokens for CoT prompt (#41979)

### [895525f](https://github.com/sgl-project/sglang/commit/895525f062a303bc7f0457d0d4bef202a4ea2397)

- **作者**: YAMY
- **时间**: 2026-10-02T10:52:37Z
- **提交信息**: [Mamba] Warm cache COW kernel before serving (#36266)

Signed-off-by: Yangmin Li <yangminl@nvidia.com>
Co-authored-by: Po-Han Huang (NVIDIA) <53919306+nvpohanh@users.noreply.github.com>

### [1db33bc](https://github.com/sgl-project/sglang/commit/1db33bc367e89fd7f429c989ba04d38c8a34128d)

- **作者**: Alex
- **时间**: 2026-10-02T09:59:31Z
- **提交信息**: [PD][NIXL] Fix prepared dlists for KV entries of different lengths (DeepSeek-V4) (#42005)

### [41bd213](https://github.com/sgl-project/sglang/commit/41bd213c5f2d7d13b77bd2bd3b370e46022139b3)

- **作者**: Po-Han Huang (NVIDIA)
- **时间**: 2026-10-02T08:00:15Z
- **提交信息**: [Test] Add get_swa_key_page_size to the Q8KV8 sparse-prefill fake KV pool (#42211)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [d954c88](https://github.com/sgl-project/sglang/commit/d954c88a4f8b81d93066883ba1a079f146f33748)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-10-02T07:37:37Z
- **提交信息**: [Fix] Update stale source-patch match in dumper comparator e2e test (#42179)

Co-authored-by: Mohammad Angkad <mohammad.angkad@radixark.ai>

### [e7d9c02](https://github.com/sgl-project/sglang/commit/e7d9c0299baa68797736f866d1850cdddfc7677b)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-10-02T07:17:13Z
- **提交信息**: [Docs] Keep the last CUDA 12 image tag fixed during install version bumps (#42201)

Co-authored-by: Mohammad Angkad <mohammad.angkad@radixark.ai>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-10-03
**监控日期**: 2026-10-02
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1287
- **最后更新**: 2026-09-29T13:34:55Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-10-03
**监控日期**: 2026-10-02
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 93082
- **最后更新**: 2026-10-03T01:00:58Z

## 提交统计

- **昨日提交总数**: 46
- **提交者数量**: 38
- **主要提交者**: Isotr0py, Chaoying, Julien Debache

## AI分析总结

# vLLM 昨日提交批次分析

## 一、主要更新类型

| 类型 | 占比 | 数量 |
|------|------|------|
| Bug修复 | 37% | 17条 |
| 性能优化 | 22% | 10条 |
| CI/测试 | 13% | 6条 |
| 重构与清理 | 7% | 3条 |
| 模型支持 | 7% | 3条 |
| 文档更新 | 7% | 3条 |
| 功能新增 | 4% | 2条 |

---

## 二、关键变更点及与项目方向的关系

### 1. MoE 架构深度优化（核心方向）
- FlashInfer CuteDSL MegaMoE 集成、all2all FP8 combine、weighted-sum kernel 调优、routed-experts capture 修复
- **关系**：MoE 是当前大模型主流架构，直接支撑项目"fast"目标，提升混合专家模型的推理效率

### 2. 多模型针对性优化（GLM-5.3、Qwen4Exp、Minimax-M3）
- GLM-5.3 sparse MLA 复用（3.5~3.9x加速）、GLM-5.3-Flash vision tower修复、Qwen4Exp SM121 GEMM计划
- **关系**：展示项目对前沿模型的快速适配能力，"Easy"目标的核心体现

### 3. 量化与低精度计算
- FP8 combine、value-only reduction、NVFP4检测、W8A8 FP8 GEMM
- **关系**：支撑"cheap"目标，降低显存占用和计算成本

### 4. Transformers 后端统一
- 迁移GPT-NeoX/Phi/Seed-OSS/Jais2、移除<5.16.1代码、设置版本上界
- **关系**：简化架构，减少维护负担，提高代码质量

### 5. 多模态与安全
- SHM处理器缓存引用计数修复、DeepSeek-OCR安全加固、图像编码器缓存优化
- **关系**：提升多模态推理的稳定性与安全性

---

## 三、对项目的影响和潜在意义

1. **性能层面**：MoE/量化优化使吞吐量提升，直接服务"fast"定位
2. **稳定性层面**：17条bug修复降低生产环境崩溃风险，涵盖CUDA graphs、并发、缓存等关键场景
3. **生态层面**：覆盖NVIDIA/AMD/Intel/Google TPU四大硬件平台，体现硬件中立性
4. **架构层面**：Transformers后端统一为长期可维护性奠定基础
5. **开发者体验**：gRPC端口暴露、agents预提交检查、CI重构改善开发流程

---

## 四、值得关注的技术点

- **FlashInfer MegaMoE集成**：CuTeDSL是NVIDIA新一代DSL，预示未来kernel开发方向
- **Sparse MLA索引复用**：3.5~3.9x的kernel优化幅度显著，对GLM系列模型意义重大
- **CKPT/LoRA的MoE兼容**：LoRA回退机制支持高秩MoE，扩展应用场景
- **TPU推理升级至v0.30.0**：Google TPU支持加强，多云部署能力提升
- **AI辅助开发痕迹明显**：大量提交含Claude/Codex/mergify协作记录

---

## 五、对项目发展的整体影响

基于README背景（"Easy, fast, cheap LLM serving for everyone"），本次提交批次体现项目正处于**生产就绪期**：

1. **"Fast"目标**：通过MoE内核优化、量化技术、多模型针对性调优持续推进性能
2. **"Easy"目标**：Transformers后端统一、文档更新、CI改善降低使用和维护门槛
3. **"Cheap"目标**：FP8/NVFP4量化优化持续降低推理成本
4. **生态成熟度**：多硬件支持、多模态修复、安全加固表明项目正在从研究级走向企业级
5. **社区活跃度**：大量来自NVIDIA/AMD/RedHat/Google等企业的贡献，项目已形成良性生态

**结论**：这些提交表明vLLM正从性能优化转向稳定性与生态完备性建设，为商业化部署做好准备。

## 详细提交记录

### [6e517b1](https://github.com/vllm-project/vllm/commit/6e517b15c1833cf72a7f557ee32524d98682e617)

- **作者**: yifanFengg
- **时间**: 2026-10-02T20:37:32Z
- **提交信息**: [Docs] Add ERNIE 4.5 to batch invariance tested models (#58476)

Signed-off-by: yifanFengg <evanfengff@gmail.com>
Signed-off-by: yifanFengg <yifanfen@amazon.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>

### [8459395](https://github.com/vllm-project/vllm/commit/84593955fa44d70a129dd3a51738a9a732a91120)

- **作者**: Ayaan Nadamal
- **时间**: 2026-10-02T20:29:16Z
- **提交信息**: [Perf][MoE] Support fp8 combine in FlashInfer one-sided MoE all2all (#57995)

Signed-off-by: Ayaan Nadamal <anadamal@nvidia.com>

### [111f71a](https://github.com/vllm-project/vllm/commit/111f71a6dbf1fe517f6164e1059a2837bb0a8b4e)

- **作者**: Julien Debache
- **时间**: 2026-10-02T19:43:33Z
- **提交信息**: [feat] FlashInfer CuteDSL MegaMoE integration  (#54049)

Signed-off-by: jdebache <jdebache@nvidia.com>

### [c4973d9](https://github.com/vllm-project/vllm/commit/c4973d94fed25a3bf32d601873755a9bcd951886)

- **作者**: Benedikt Falk
- **时间**: 2026-10-02T18:48:43Z
- **提交信息**: [Bugfix][Frontend] Avoid generation for empty streaming input (#59015)

Signed-off-by: Benedikt Falk <bfalk@nvidia.com>

### [10f6ab0](https://github.com/vllm-project/vllm/commit/10f6ab01a931cee9cc3ec4a141d47be7ee7f111c)

- **作者**: jackLei
- **时间**: 2026-10-02T18:37:17Z
- **提交信息**: [Perf] Use value-only reduction for native per-token FP8 quantization (#59800)

Signed-off-by: jackLei0901 <841747318@qq.com>
Co-authored-by: Misha Goin <mgoin64@gmail.com>

### [8882b83](https://github.com/vllm-project/vllm/commit/8882b83b34718ae8103a178ac1dfa84bb502cb29)

- **作者**: djramic
- **时间**: 2026-10-02T18:33:50Z
- **提交信息**: [Bugfix] Bump tokenizers to 0.23.2 for duplicate-pattern support (#59796)

Signed-off-by: Djordje Ramic <djoramic@amd.com>

### [202d497](https://github.com/vllm-project/vllm/commit/202d497aa897edef87fc291b7f428d7dd473aa06)

- **作者**: simon-veitner-redhat
- **时间**: 2026-10-02T18:32:11Z
- **提交信息**: [Bugfix][Watermarking] Keep draft prompt lengths valid under CUDA graphs (#59779)

Signed-off-by: Simon Veitner <sveitner@redhat.com>
Co-authored-by: Lucas Wilkinson <LucasWilkinson@users.noreply.github.com>

### [d1a974c](https://github.com/vllm-project/vllm/commit/d1a974c14031014c18253e201b3f11ea3f565f37)

- **作者**: Shijin Zhang
- **时间**: 2026-10-02T18:31:53Z
- **提交信息**: [Frontend] Constrain non-strict GLM-4.7 tool calls with a shallow structural tag (#56403)

Signed-off-by: Shijin Zhang <75300765+Dovis01@users.noreply.github.com>
Co-authored-by: Flora Feng <4florafeng@gmail.com>

### [f700178](https://github.com/vllm-project/vllm/commit/f700178f90d21f21fea2b495475e83b267290c01)

- **作者**: Wentao Ye
- **时间**: 2026-10-02T18:07:20Z
- **提交信息**: [Refactor] Remove dead env and config (#59781)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [4e4d75c](https://github.com/vllm-project/vllm/commit/4e4d75c4594b1072729ffe335c9bcea601749f71)

- **作者**: Wentao Ye
- **时间**: 2026-10-02T17:37:45Z
- **提交信息**: [GLM5.3 Perf] Reuse sparse MLA index conversion across layers, 3.5~3.9x kernel performance improvement (#59464)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [7cfd233](https://github.com/vllm-project/vllm/commit/7cfd233538805f4a34607263a144bfb0f3943f32)

- **作者**: Thang Nguyen
- **时间**: 2026-10-02T17:19:25Z
- **提交信息**: Revert "[Bugfix] Tie lm_head.weight for Nemotron Parse when checkpoint omits it" (#53020) (#59805)

Signed-off-by: Thang Nguyen <thangnguyenvn647@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [f590eb2](https://github.com/vllm-project/vllm/commit/f590eb2448a51028f6044c6f60104ce0ef3189e9)

- **作者**: Stefano Castagnetta
- **时间**: 2026-10-02T17:17:45Z
- **提交信息**: [Perf][Qwen4Exp] Add SM121 TP=1 skinny-GEMM plans (#59753)

Signed-off-by: Stefano Castagnetta <scastagnetta@nvidia.com>
Co-authored-by: Benjamin Chislett <bchislett@nvidia.com>

### [9cf087f](https://github.com/vllm-project/vllm/commit/9cf087fd14bf2219a24cfc1de728e5cebe5d59d4)

- **作者**: Jinzhen Lin
- **时间**: 2026-10-02T17:09:29Z
- **提交信息**: [Perf] Tune MoE weighted-sum kernel launch configuration (#59731)

Signed-off-by: Jinzhen Lin <jinzhen.ljz@antgroup.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Misha Goin <mgoin64@gmail.com>

### [8442117](https://github.com/vllm-project/vllm/commit/8442117446e0e317662f02d63d0ab9e1592a8253)

- **作者**: Jeff-Tseng-dev
- **时间**: 2026-10-02T16:39:03Z
- **提交信息**: Upgrade tpu-inference to v0.30.0 (#59396)

Signed-off-by: Jeff Tseng <tsengjeff@google.com>
Co-authored-by: Jeff Tseng <tsengjeff@google.com>
Co-authored-by: Misha Goin <mgoin64@gmail.com>

### [1ab1859](https://github.com/vllm-project/vllm/commit/1ab18599ca683a18d7cac6e87ef900e5a85b62aa)

- **作者**: Misha Goin
- **时间**: 2026-10-02T16:38:22Z
- **提交信息**: [Agents] Add pre-commit check for agent files and skills (#59657)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [e42d35d](https://github.com/vllm-project/vllm/commit/e42d35d4f3b4782e4fa692939b638360f44c7ead)

- **作者**: rmhaskar
- **时间**: 2026-10-02T16:30:39Z
- **提交信息**: [Minimax-M3] Keep the native FP8 MMA in the Triton indexer scorers (#59481)

Signed-off-by: Rajas Mhaskar <rmhaskar@nvidia.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [167a81f](https://github.com/vllm-project/vllm/commit/167a81fa9cb39878dd04ca9fa756eb8be34f9fe1)

- **作者**: djramic
- **时间**: 2026-10-02T16:30:01Z
- **提交信息**: [CI] Fix ModelExpress handling in weight transfer tests (#59772)

Signed-off-by: Djordje Ramic <djoramic@amd.com>

### [6abadc2](https://github.com/vllm-project/vllm/commit/6abadc2aa78ad00476583c594ecd442144795ec5)

- **作者**: Divakar Verma
- **时间**: 2026-10-02T16:23:22Z
- **提交信息**: [ROCm][CI] Add test coverage for VLLM_ROCM_MOE_PADDING memory-stride padding transparency (#59332)

Signed-off-by: Divakar Verma <divakar.verma@amd.com>

### [2a53788](https://github.com/vllm-project/vllm/commit/2a537887de7a103baa49bbfdce93e99d48d19441)

- **作者**: Divakar Verma
- **时间**: 2026-10-02T16:21:21Z
- **提交信息**: [CI] Use vllm_runner in fusions_e2e conftest for reliable GPU cleanup (#59525)

Signed-off-by: Divakar Verma <divakar.verma@amd.com>

### [7b6be2f](https://github.com/vllm-project/vllm/commit/7b6be2f1f41ec9ee69fbe3cd08c76a64a041706e)

- **作者**: Lucas Wilkinson
- **时间**: 2026-10-02T16:11:31Z
- **提交信息**: [Docs] Add Reviewers page (#59459)

Signed-off-by: Lucas Wilkinson <lwilkins@redhat.com>
Signed-off-by: JartX <sagformas@epdcenter.es>
Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>
Signed-off-by: bnellnm <49004751+bnellnm@users.noreply.github.com>
Signed-off-by: Itay Etelis <92247226+Etelis@users.noreply.github.com>
Signed-off-by: simondanielsson <simon.danielsson99@hotmail.com>
Signed-off-by: Roberto L. Castro <38211239+LopezCastroRoberto@users.noreply.github.com>
Signed-off-by: Netanel Haber <58652339+netanel-haber@users.noreply.github.com>
Signed-off-by: Itay Alroy <ialroy@nvidia.com>
Signed-off-by: Felix Marty <Felix.Marty@amd.com>
Signed-off-by: Varun Sundar Rabindranath <vsundarr@redhat.com>
Signed-off-by: Micah Williamson <micah.williamson@amd.com>
Signed-off-by: cjackal <44624812+cjackal@users.noreply.github.com>
Signed-off-by: Summer Yang <girasoleyang@gmail.com>
Signed-off-by: Rohan138 <rohanpotdar138@gmail.com>
Signed-off-by: kliuae <kuanfu.liu@embeddedllm.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: JartX <sagformas@epdcenter.es>
Co-authored-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>
Co-authored-by: bnellnm <49004751+bnellnm@users.noreply.github.com>
Co-authored-by: Itay Etelis <92247226+Etelis@users.noreply.github.com>
Co-authored-by: simondanielsson <simon.danielsson99@hotmail.com>
Co-authored-by: Roberto L. Castro <38211239+LopezCastroRoberto@users.noreply.github.com>
Co-authored-by: Netanel Haber <58652339+netanel-haber@users.noreply.github.com>
Co-authored-by: Itay Alroy <ialroy@nvidia.com>
Co-authored-by: Felix Marty <Felix.Marty@amd.com>
Co-authored-by: Varun Sundar Rabindranath <vsundarr@redhat.com>
Co-authored-by: Micah Williamson <micah.williamson@amd.com>
Co-authored-by: cjackal <44624812+cjackal@users.noreply.github.com>
Co-authored-by: Summer Yang <girasoleyang@gmail.com>
Co-authored-by: Rohan138 <rohanpotdar138@gmail.com>
Co-authored-by: kliuae <kuanfu.liu@embeddedllm.com>
Co-authored-by: Misha Goin <mgoin64@gmail.com>

### [4c4003b](https://github.com/vllm-project/vllm/commit/4c4003bb5f847e7a84152cbf0e6ff58cadfceb52)

- **作者**: Eric Tang
- **时间**: 2026-10-02T15:50:38Z
- **提交信息**: [Bugfix] Bind routed-experts capture to the MoE layer, not the kernel (#59455)

Signed-off-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [0979892](https://github.com/vllm-project/vllm/commit/097989299222f94db6703ee0902972943f01aa7e)

- **作者**: Juan Calderon-Perez
- **时间**: 2026-10-02T15:25:37Z
- **提交信息**: [Bugfix][Multimodal] Fix GLM-5.3-Flash vision tower crashes on image input (#59126)

Signed-off-by: Juan Calderon-Perez <835733+gaby@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>

### [f0c44cc](https://github.com/vllm-project/vllm/commit/f0c44cc7d5c5672192ff79da4c7657d65f85ab4d)

- **作者**: Taneem Ibrahim
- **时间**: 2026-10-02T14:47:55Z
- **提交信息**: [Bugfix] Fix stalled local-only Elastic EP scale-up (#57820)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [592c6f3](https://github.com/vllm-project/vllm/commit/592c6f3fbcefeb3a4e0c0b461531329bf4ee0489)

- **作者**: Chaoying
- **时间**: 2026-10-02T14:14:33Z
- **提交信息**: [Bugfix][Pooling] Handle multimodal cache misses without crashing (#58975)

Signed-off-by: linchaoying6 <linchaoying6@jd.com>
Co-authored-by: linchaoying6 <linchaoying6@jd.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [443dccd](https://github.com/vllm-project/vllm/commit/443dccd3c9448f586634bfdb7079acd7eab35ead)

- **作者**: tenotek
- **时间**: 2026-10-02T14:14:13Z
- **提交信息**: [Bugfix][Multimodal] Fix reference counting of the SHM processor cache (#59695)

Signed-off-by: tenotek <50898317+hdq66666@users.noreply.github.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [c91dccc](https://github.com/vllm-project/vllm/commit/c91dccc08044b1269f351ceec13070fe8f075e10)

- **作者**: aoshen02
- **时间**: 2026-10-02T13:46:48Z
- **提交信息**: [Bugfix][Quark] Pass grouped-routing arguments to OCP MX monolithic kernels (#59752)

Signed-off-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [e429414](https://github.com/vllm-project/vllm/commit/e4294144a8ca4e57da712934dca33f89bef8fe78)

- **作者**: DimensionSTP
- **时间**: 2026-10-02T13:44:53Z
- **提交信息**: [Perf] Keep non-speculative GDN decode on the standard path (#59735)

Signed-off-by: DimensionSTP <65501090+DimensionSTP@users.noreply.github.com>
Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>
Co-authored-by: Thien Tran <gau.nernst@yahoo.com.sg>
Co-authored-by: Kimi Code <noreply@moonshot.ai>

### [24df2d3](https://github.com/vllm-project/vllm/commit/24df2d3fc7e5aa1ce8ac97f839905481eb966223)

- **作者**: SeongJun Lee
- **时间**: 2026-10-02T13:38:15Z
- **提交信息**: [Model] Add Qwen4Exp to the Qwen GDN Triton warmup (#56742)

Signed-off-by: lesj0610 <lesj0610@users.noreply.github.com>
Co-authored-by: lesj0610 <lesj0610@users.noreply.github.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: Thien Tran <gau.nernst@yahoo.com.sg>

### [30e956f](https://github.com/vllm-project/vllm/commit/30e956fad3b4f3d79420321d608aaba262d3cebe)

- **作者**: Rajeev Warrier
- **时间**: 2026-10-02T13:21:43Z
- **提交信息**: [Docs] Fix stale W4A16 NVFP4 default kernel in ModelOpt docs (#59135)

Signed-off-by: Rajeev Warrier <warrier.rajeev.95@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [d648847](https://github.com/vllm-project/vllm/commit/d648847fe451a6a0366f8dd0e1ae96804a49a299)

- **作者**: Jiangyun Zhu
- **时间**: 2026-10-02T12:58:35Z
- **提交信息**: [CI][Kimi-K3] Test prefix cache reuse with KV offload, P/D and DCP (#59229)

Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [f0b4b36](https://github.com/vllm-project/vllm/commit/f0b4b36890ad0465c0564a31ec34fc2bb12ab745)

- **作者**: Stefano Castagnetta
- **时间**: 2026-10-02T12:30:22Z
- **提交信息**: [Bugfix][Quantization] Detect NVFP4 in ModelOpt mixed-precision checkpoints (#56050)

Signed-off-by: Stefano Castagnetta <scastagnetta@nvidia.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [fa212b8](https://github.com/vllm-project/vllm/commit/fa212b8dc5de5f0cd7b3171e7c7f584bb5a69c53)

- **作者**: Abhay Shukla
- **时间**: 2026-10-02T11:59:40Z
- **提交信息**: [Test] Re-enable Ovis2.5 and Ovis2.6-MoE vLLM tests on Transformers v5 (#59763)

Signed-off-by: AbhayShuklaIIT <abhay.shukla@live.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [bdfb026](https://github.com/vllm-project/vllm/commit/bdfb02674fc0eaa2b9023420b02a8d4e23a69957)

- **作者**: pmanczak
- **时间**: 2026-10-02T11:56:11Z
- **提交信息**: [XPU][Kernel] Tune Triton W8A8 block-FP8 GEMM for Intel B70 (#56063)

Signed-off-by: Pawel Manczak <203671809+pmanczak@users.noreply.github.com>
Co-authored-by: Pawel Manczak <203671809+pmanczak@users.noreply.github.com>

### [e2cb5ee](https://github.com/vllm-project/vllm/commit/e2cb5ee46c31d0d7a10b95560e8d38ef119042d0)

- **作者**: Turner Jabbour
- **时间**: 2026-10-02T11:30:04Z
- **提交信息**: [CI] Replace shellcheck-suppressed patterns flagged in #52572 with clean equivalents (#53341)

Signed-off-by: Turner Jabbour <doubleujabbour@gmail.com>
Co-authored-by: Claude Sonnet 5 <noreply@anthropic.com>

### [6e4efaf](https://github.com/vllm-project/vllm/commit/6e4efafc6edfee8be31c3c147164a1daa4650051)

- **作者**: Harry Mellor
- **时间**: 2026-10-02T11:18:35Z
- **提交信息**: [Model] Migrate GPT-NeoX, Phi, Seed-OSS and Jais2 to the Transformers modeling backend (#59701)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [5d20979](https://github.com/vllm-project/vllm/commit/5d20979fc90a38f450e0fb89661b271926a3061a)

- **作者**: Harry Mellor
- **时间**: 2026-10-02T11:17:24Z
- **提交信息**: [Misc] Remove code paths for Transformers < 5.16.1 (#59762)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [8c60714](https://github.com/vllm-project/vllm/commit/8c60714da541992a883a138b4f08df9558018b76)

- **作者**: xiaoyu-xyz
- **时间**: 2026-10-02T10:59:28Z
- **提交信息**: [Bugfix][LoRA] Fall back for high-rank MoE LoRA (#55161)

Signed-off-by: Raina Zhong <yuweiz@nvidia.com>
Co-authored-by: Raina Zhong <yuweiz@nvidia.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [98b29aa](https://github.com/vllm-project/vllm/commit/98b29aa99aee8fe58a21b168b45a5dcb910f63c0)

- **作者**: Simon Danielsson
- **时间**: 2026-10-02T10:47:41Z
- **提交信息**: [ROCm][Perf][GLM-5.3-Flash] Add AITER topk backend for decodes (#58167)

Signed-off-by: simondanielsson <simon.danielsson99@hotmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [751fa96](https://github.com/vllm-project/vllm/commit/751fa96a497fdba67ca594db832c02140478208f)

- **作者**: Simon Danielsson
- **时间**: 2026-10-02T10:45:51Z
- **提交信息**: [ROCm][Perf][GLM-5.3-Flash] Remove redundant copy after ragged sparse MLA (#58569)

Signed-off-by: simondanielsson <simon.danielsson99@hotmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [5688a4d](https://github.com/vllm-project/vllm/commit/5688a4dd4a1ebb5d2d7b6fa863d20cc903f8b341)

- **作者**: Yufeng He
- **时间**: 2026-10-02T10:43:29Z
- **提交信息**: [Bugfix][GLM-5.3] Size the image encoder cache from the exact token ceiling (#59565)

Signed-off-by: Yufeng He <40085740+he-yufeng@users.noreply.github.com>
Co-authored-by: Kimi Code <kimi-code@moonshot.cn>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>

### [af2a582](https://github.com/vllm-project/vllm/commit/af2a582d5c8e3ec1edccc304a3d2527f1ea3e3e3)

- **作者**: Farhad Al-Amin
- **时间**: 2026-10-02T10:21:20Z
- **提交信息**: [Bugfix][Spec Decode] Qualify Transformers backend attention layer names with the model prefix (#59293)

Signed-off-by: Farhad Al-Amin <99006654+Legend-2727@users.noreply.github.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [8e58ac2](https://github.com/vllm-project/vllm/commit/8e58ac22aff66f06f49b5ed0ce95ec9c92f8d022)

- **作者**: aoshen02
- **时间**: 2026-10-02T09:49:21Z
- **提交信息**: [Feature] Offload KV-init runtime state on sleep (#59158)

Signed-off-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [c15672c](https://github.com/vllm-project/vllm/commit/c15672cfb49152ebf65cfd188e71b84593ec5686)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-10-02T09:17:12Z
- **提交信息**: [Security] Accept zero-sum DeepSeek-OCR pixel tensors (#59417)

Signed-off-by: Juan Pérez de Algaba <jperezde@redhat.com>

### [58b3298](https://github.com/vllm-project/vllm/commit/58b3298457dde7b4554b3b4e20b238c0ac2c3a65)

- **作者**: Isotr0py
- **时间**: 2026-10-02T08:27:11Z
- **提交信息**: [Misc] Add Transformers version upper bound in requirements (#59614)

Signed-off-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [9d2a6f5](https://github.com/vllm-project/vllm/commit/9d2a6f52b264c20b5816c5a094b191bfbcadd74b)

- **作者**: Alec
- **时间**: 2026-10-02T08:14:37Z
- **提交信息**: [Rust Frontend] Expose gRPC port in Python vllm serve (#59659)

Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Signed-off-by: Alec Flowers <aflowers@nvidia.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>

### [b558f16](https://github.com/vllm-project/vllm/commit/b558f160a2c0abcb5902acc3c91a14c38a4af173)

- **作者**: Isotr0py
- **时间**: 2026-10-02T07:29:49Z
- **提交信息**: [Bugfix] Fix minimax-m3 multimodal processor compatability with Transformers v5.18 (#59613)

Signed-off-by: Isotr0py <Isotr0py@outlook.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-10-03
**监控日期**: 2026-10-02
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7028
- **最后更新**: 2026-10-02T20:32:55Z

## 提交统计

- **昨日提交总数**: 14
- **提交者数量**: 8
- **主要提交者**: Yueqian Lin, 汪志鹏, Rahul Steiger

## AI分析总结

# vllm-omni 昨日提交分析

## 1. 主要更新类型
本次提交以**模型性能优化与功能新增**为主，辅以若干 **Bug 修复**和**测试/CI 修复**：
- 性能优化（约 6 条）：CUDA Graph、GEMM 融合、预计算等
- 功能新增（约 4 条）：新模型支持、流式推理能力、分布式训练选项
- Bug 修复与测试修复（约 4 条）

## 2. 关键变更点与项目方向的关系
vllm-omni 的目标是为"全模态模型"提供**低成本、高速率**的推理服务，这批提交高度契合这一方向：

- **流式音频/视频推理持续深化**：包括 CosyVoice3 打包流式推理、Qwen3-TTS 单阶段流式解码、Fish Speech/CosyVoice3 高并发音质修复、MOSS 1.5 分块流式优化，以及前端的增量式预填充实时视频流支持。这表明项目正在系统性地打磨多模态流式服务能力。
- **底层性能压榨**：YuE2 的 CUDA Graph 加速、adaLN 调制的每请求预计算、编码器预填充的图化与缓存参考隐变量、扩散注意力的 FA4 原型——均聚焦于降低延迟与吞吐开销，是"fast and cheap"目标的直接支撑。
- **AR-Diffusion 可用性修复**：通过分页加载 kernel-legal 块，使默认分辨率可运行，属于实用化推进。
- **工程基础设施**：HSDP 预分片选项、测试夹具与 CI 修复，保障大规模训练与持续集成的稳定性。

## 3. 对项目的影响和潜在意义
- 音频流式能力的多项改进将显著改善**高并发语音场景**下的吞吐与音质稳定性，为生产级部署扫清障碍。
- 流式视频增量预填充补齐了项目在**视频模态实时服务**上的短板，扩大了全模态覆盖范围。
- 性能类提交累计可能带来端到端延迟和推理成本的可观下降，强化项目在与通用 vLLM 生态差异化中的竞争力。
- 多位外部贡献者（如华为、Red Hat 等）的参与，说明社区活跃度良好，项目正走向更成熟的协作治理。

## 4. 值得关注的技术点
- **CUDA Graph 与单阶段合成**（YuE2、CosyVoice3）：减少控制流开销对流式低延迟推理至关重要。
- **每请求 adaLN 预计算 + 卷积位置编码合并为单一 GEMM**：典型的 kernel 级融合优化，体现对 Transformer 扩散模型推理瓶颈的精准识别。
- **异步 chunk 共享内存（SHM）写入的边界处理**（stage-0-final 请求跳过）：揭示了流式执行器在多请求并发下的资源竞态问题，修复具有示范价值。
- **FA4（FlashAttention 4）注意力执行契约原型**：前瞻性布局新一代注意力库接口，值得关注后续演进。
- **HSDP 预分片选项**：为大规模全模态模型训练提供分布式效率优化。

## 5. 对项目发展的整体影响
结合 README 中"Easy, fast, and cheap omni-modality model serving"的定位，这批提交呈现出**两条清晰主线**：一是**流式多模态服务的打磨完善**（音频与视频流式能力同步推进），使项目从"能跑"走向"能稳定服务"；二是**推理内核与执行图层的深度优化**，为全模态模型的低成本高效服务奠定底层基础。两者共同推动 vllm-omni 向生产可用的全模态推理平台演进，同时社区协作与 CI 基建的完善预示项目正处于快速成长期。建议重点关注 FA4 契约与 HSDP 选项等前瞻性改动的后续落地情况。

## 详细提交记录

### [3bc3f1a](https://github.com/vllm-project/vllm-omni/commit/3bc3f1a7d0a139df23e19566e502276e5d998e49)

- **作者**: Sy03
- **时间**: 2026-10-02T18:03:14Z
- **提交信息**: [Model] Optimize MOSS Local 1.5 MRV2 serving and progressive chunks (#8213)

Signed-off-by: Sy03 <1370724210@qq.com>
Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: Yueqian Lin <linyueqian@outlook.com>

### [527982d](https://github.com/vllm-project/vllm-omni/commit/527982d886db4da88f205a576cbc0333f9b8eac5)

- **作者**: Zheng Wengang
- **时间**: 2026-10-02T16:14:39Z
- **提交信息**: [Bugfix] Skip async-chunk SHM put for stage-0-final requests (#7245)

Signed-off-by: ZhengWG <zwg0606@gmail.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [2ba5074](https://github.com/vllm-project/vllm-omni/commit/2ba5074ca039a94698e7a021243d98577430d84f)

- **作者**: Sy03
- **时间**: 2026-10-02T15:49:50Z
- **提交信息**: [Model] Optimize CosyVoice3 packed streaming with bounded HiFT graphs (#8420)

Signed-off-by: Sy03 <1370724210@qq.com>

### [4025bb3](https://github.com/vllm-project/vllm-omni/commit/4025bb30f670c83649a4dce6779227d01f2b58ec)

- **作者**: Yueqian Lin
- **时间**: 2026-10-02T15:43:55Z
- **提交信息**: [Perf][AuK] Graph the encoder prefill, cache reference latents and fuse the codec activation (#8305)

Signed-off-by: Yueqian Lin <linyueqian@outlook.com>

### [13c66da](https://github.com/vllm-project/vllm-omni/commit/13c66da75219d8c5ab752618039d254dd9a19eb6)

- **作者**: Yueqian Lin
- **时间**: 2026-10-02T15:12:29Z
- **提交信息**: [Perf][AuK] Precompute adaLN modulations per request and run the conv position embedding as one GEMM (#8328)

Signed-off-by: Yueqian Lin <linyueqian@outlook.com>

### [0e6791e](https://github.com/vllm-project/vllm-omni/commit/0e6791e9c4925c3539352cff2c2738bd48a1a65a)

- **作者**: Nick Cao
- **时间**: 2026-10-02T14:22:52Z
- **提交信息**: [Bugfix] Initialize eager state in Higgs test fixture (#8426)

Signed-off-by: Nick Cao <ncao@redhat.com>
Co-authored-by: Codex <noreply@openai.com>

### [eb1699b](https://github.com/vllm-project/vllm-omni/commit/eb1699bfca2ca6f1bb074afdad7236b6809c3514)

- **作者**: Zheng Wengang
- **时间**: 2026-10-02T14:18:51Z
- **提交信息**: [FEAT][Fronted] Support incremental prefill for realtime video streaming (#5894)

Signed-off-by: ZhengWG <zwg0606@gmail.com>
Signed-off-by: Zheng Wengang <zwg0606@gmail.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [e372aa3](https://github.com/vllm-project/vllm-omni/commit/e372aa3a4137bca513827b37e6080b908cd977c7)

- **作者**: Sy03
- **时间**: 2026-10-02T14:11:04Z
- **提交信息**: [Bugfix] Restore Fish Speech and CosyVoice3 audio quality at high concurrency (#8422)

Signed-off-by: Sy03 <1370724210@qq.com>

### [ae58c2d](https://github.com/vllm-project/vllm-omni/commit/ae58c2d8b9e7ce0044054a817b695aadb1924342)

- **作者**: Sy03
- **时间**: 2026-10-02T12:17:06Z
- **提交信息**: [Model] YuE2: async single-stage synthesis and CUDA graph acceleration (#8407)

Signed-off-by: Sy03 <1370724210@qq.com>
Signed-off-by: princepride <wangzhipeng628@gmail.com>
Signed-off-by: Wang Zhipeng <wangzhipeng628@gmail.com>
Co-authored-by: princepride <wangzhipeng628@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [b10270a](https://github.com/vllm-project/vllm-omni/commit/b10270a01ce6a1691120951a3969202e5f785957)

- **作者**: linzhenpl07
- **时间**: 2026-10-02T12:05:04Z
- **提交信息**: [AR-Diffusion] Page in kernel-legal blocks so the default resolution can run (#6481)

Signed-off-by: linzhenpl07 <linzhenpl07@gmail.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>
Co-authored-by: Zhou Taichang <tzhouam@connect.ust.hk>

### [e84014d](https://github.com/vllm-project/vllm-omni/commit/e84014dffb972c62ca35d83437d6248425fbad18)

- **作者**: Sy03
- **时间**: 2026-10-02T11:34:30Z
- **提交信息**: [Model] Add single-stage Qwen3-TTS with in-Talker streaming codec decode (#8259)

Signed-off-by: Sy03 <1370724210@qq.com>

### [596487f](https://github.com/vllm-project/vllm-omni/commit/596487fe62bad27df5a9257e7b5dbdeb6e22d51e)

- **作者**: Rahul Steiger
- **时间**: 2026-10-02T09:58:47Z
- **提交信息**: [Core] Prototype diffusion attention execution contracts with FA4 (#7379)

### [97d6c69](https://github.com/vllm-project/vllm-omni/commit/97d6c693a684299d3696460d8942417231bfdd7f)

- **作者**: MaciejBalaNV
- **时间**: 2026-10-02T09:35:09Z
- **提交信息**: [feature] Add HSDP pre-sharded option (#7948)

Signed-off-by: Maciej Bala <mbala@nvidia.com>
Co-authored-by: 汪志鹏 <wangzhipeng628@gmail.com>

### [b742f86](https://github.com/vllm-project/vllm-omni/commit/b742f86136d28423903a1213adde2a62a11067a2)

- **作者**: 汪志鹏
- **时间**: 2026-10-02T08:45:56Z
- **提交信息**: [CI/Build] Restore streaming executor fixture contract (#8418)

Signed-off-by: princepride <wangzhipeng628@gmail.com>

---
