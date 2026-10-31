# GitHub Stars 合并报告 - 2026-10-30

**合并日期**: 2026-10-31
**监控日期**: 2026-10-30
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


**报告日期**: 2026-10-31
**监控日期**: 2026-10-30
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2269
- **最后更新**: 2026-10-30T06:39:32Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-10-31
**监控日期**: 2026-10-30
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2977
- **最后更新**: 2026-10-31T01:10:00Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-10-31
**监控日期**: 2026-10-30
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2320
- **最后更新**: 2026-10-30T16:13:05Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-10-31
**监控日期**: 2026-10-30
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6823
- **最后更新**: 2026-10-31T01:11:42Z

## 提交统计

- **昨日提交总数**: 41
- **提交者数量**: 12
- **主要提交者**: lunarz-dev, Artem Perevedentsev, Adrian

## AI分析总结

# FlashInfer 昨日 41 项提交综合总结

## 一、总览
昨日 flashinfer-ai/flashinfer 共 41 项提交，以**性能优化为绝对主线**（约占七成），且多数严格限定在宿主侧调度、通信与 launch 逻辑层面，不改动 kernel 数学计算，输出与梯度声明逐位一致。其余包括 2 项关键 Bug 修复、实验性功能推进、API 重命名重构及 CI/治理工作。调优对象覆盖 Blackwell 全系（B200/B300/GB200/GB300/RTX 50 系）乃至 Rubin（R200），量化路径（NVFP4、MXFP8、FP8）、MoE 路由、稀疏注意力与长序列 prefill 为主要方向。

## 二、关键变更

**性能与调度优化**：
- **Context Parallel 通信融合（#7985）**：将 causal conv1d 的 q/k/v 三次独立 halo 交换合并为每方向一次，每层通信点由 3 降至 1，直接缓解 CP16 下的同步等待瓶颈。
- **稀疏 MLA 调度补全（#7984）**：将 12/24/48/96 等非标头数映射到最近合格头数，消除调度死角，最差场景提速 23.5 倍。
- **Kimi-K3 LatentMoE 增量优化（#7979）**：优化 front/tail 投影的 decode 尾部与 prefill 路径，并按 GPU 型号选择差异化 tile 形态。
- **MoE grouped GEMM 自适应 die 拆分（#7975）**：GB300 上以一次性探针实测双 die 实际 SM 数（如 36/40 不对称），据此拆分 tile 队列而非固定均分，提升约 1–4%。
- **KDA prefill（#7978）**：引入 next-state 预取、逐 warp checkpoint，并为 B200 构建 bin-mix 协作 launch，空闲 CTA 协助长任务 bin 以均衡负载。
- **PDL 自动化与微调**：BF16 GEMM 由调优器自动选择 PDL 开关，MXFP8 将启动信号提前至量化上游，端到端 TPOT 降低约 1%–2%；多条 Cake 内核仅改宿主侧调度即获 1%–18% 提升。DSA 索引器融合两趟 radix-select 扫描；Top-K 缓存将每次调用的 memset/分配改为按流缓存，消除 CI 二分出的延迟回归。

**Bug 修复**：
- 修复 SM90 稀疏 prefill 在 CUDA 12 下的编译崩溃与输出错误，恢复老驱动 H100 大上下文推理能力。
- 修复 `cake_kda` 跨流共享 workspace 的内存生命周期漏洞——换流时旧队列仍访问已释放内存导致 NaN，通过流等待规则保障复用安全。

**功能与治理**：Qwen 3.8 Flash-Next 注意力块补齐 extend/prefill 链路；单头 indexer 支持 paged MQA logits（SDSA 稀疏注意力）；确定性 Gated DeltaNet、MoE grouped GEMM、mHC autograd 统一引入 `det` 后缀命名，旧名保留为别名；CODEOWNERS 增设负责人，通信测试修复静默通过问题。

## 三、项目影响
本批工作巩固了 FlashInfer 作为 vLLM 等服务栈底层的三重支柱：**性能**（Blackwell/Rubin 亚百分比级微调与调优器自动化）、**正确性**（跨流安全修复、CUDA 12 兼容、逐位一致性验收）、**生态覆盖**（Kimi-K3、DeepSeek-V3.2、Qwen 新架构孵化后沉淀为核心 API）。CP 通信融合显著改善大规模上下文并行扩展性；稀疏 MLA 调度补全减少用户手动调参；差异化硬件支持巩固前沿地位；生产级延迟治理与 CI 回归响应直接提升真实服务吞吐与稳定性。

## 四、技术关注点
- **流感知缓冲缓存**：以 `(name, device, stream)` 为键缓存 scratch buffer，利用同流有序性免重复清零，CUDA graph 捕获时回退原路径，是可复用的 GPU 编程范式。
- **运行时拓扑探测**：die-split 探针体现"运行时发现拓扑并反馈到调度"的设计，对 GB 系列非对称 die 芯片具有示范意义。
- **通信原语聚合**：多张量共享一次 all_to_all 后再拷贝分发，是通信融合的典型范式。
- **工具链陷阱**：cu12 ptxas 下 PV GEMM 的 P 值计算需在 f32 暂存后整片写入 fp8 fragment。
- **确定性作为一等公民**：多个 PR 以位级一致为验收标准，489 个内核配置 SASS 仅符号变化，重构纪律严谨。

## 五、发展趋势
FlashInfer 正从"单 kernel 极致优化"转向"系统级协同优化"——不仅追求单个 GEMM/Attention 的延迟，还处理通信聚合、多 die 拓扑感知、CP 同步开销等部署级问题，进入成熟维护与高速迭代并行阶段，在前沿模型适配、新硬件抢占与工程严谨性三线并进。

## 详细提交记录

### [e7ee923](https://github.com/flashinfer-ai/flashinfer/commit/e7ee9232eb2f6a1ec23312e29b3a9383c7feef36)

- **作者**: Adrian
- **时间**: 2026-10-30T23:51:03Z
- **提交信息**: test: fix staged MoE FFI signature checks (#8025)

<!-- .github/pull_request_template.md -->

## 📌 Description

The six staged-routing FFI signature tests fail with `ValueError:
substring not found` because their source lookup hard-codes
`Array<Tensor>`, while the launchers now return
`Array<Optional<Tensor>>`.

Locate each function using `f" {name}("`, independently of its return
type. The assertions validate the input contract: weight parameters use
`Optional<TensorView> const&`, arguments retain their expected order,
and `routing_replay_out` is last. A change from `Array<Tensor>` to
`Array<Optional<Tensor>>` changes the output contract without changing
those input requirements, so it should not prevent the parameter
assertions from running.

Updating the lookup to hard-code `Array<Optional<Tensor>>` would fix the
immediate failure but retain that unrelated dependency. This test does
not enforce the return type; any intended output-type requirement should
be checked explicitly rather than implicitly through the function
lookup.

## 🔍 Related Issues

No separate tracking issue.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

Changed-file hooks passed at commit time; repository-wide hooks were not
run.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- Replayed all six existing test functions against the actual C++ source
on the rebased branch, without importing GPU dependencies: **0/6 pass
before, 6/6 pass after**.
- Ruff lint/format and `git diff --check` pass; commit hooks passed.
- The full test module was not run because this host has no PyTorch/CUDA
environment.

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust):
`tests/cpu/prims_ts/test_moe_runner_ffi_tensors.py`

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

Test-only change; no launcher or kernel behavior changes. The CPU replay
executes the existing parameter assertions rather than replacing them
with a separate oracle. AI-assisted.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Tests**
* Updated the staged-routing FFI signature test to locate function
declarations by name, regardless of their return type.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [9ef460e](https://github.com/flashinfer-ai/flashinfer/commit/9ef460e35c0c0efee8a45ec574503d76d7a32cef)

- **作者**: Artem Perevedentsev
- **时间**: 2026-10-30T23:19:06Z
- **提交信息**: perf(gemm): autotune PDL variants for mm_bf16 with pdl=None (#8032)

<!-- .github/pull_request_template.md -->

## 📌 Description

Let callers opt into tuning PDL on/off for BF16 GEMM by passing
`pdl=None`. TGV, TinyGEMM and the low-M CuTeDSL runners contribute both
variants; the selected variant is cached. Explicit `True` and `False`
remain respected, and the default stays `False`.

The default is deliberately preserved: some PDL kernels preload weights
before their activation dependency wait, so automatically enabling PDL
would change the correctness contract for callers with dynamically
produced weights. `pdl=None`, like `pdl=True`, requires the documented
input-dependency precondition. Untuned opt-in calls run without PDL.

Both `autotune` and `autotune_v2` use the same runner selection.
PDL-auto entries use a separate op identity, the variants have distinct
persisted keys, and `skip_ops={"bf16_gemm"}` continues to skip them. V2
regression tests force either variant to win, discard tuner/runner
identities, verify managed-cache strict hits without profiling, and
capture/replay with changed inputs.

### Author-provided GB300 measurements

The original measurements below are retained from the author's
submission. After the review follow-up, callers must explicitly pass
`pdl=None` to exercise that candidate set. These are kernel-level
results, not serving-throughput claims; the reviewer has not
independently reproduced the GB300 timings.

<details>
<summary>Qwen3.8-27B decode shapes (M = 4 / 8 / 16) GB300</summary>

| layer | N × K | M | main picks | main, µs | branch picks | branch, µs
| speedup | tuning main → branch, s |
|---|---|---|---|---|---|---|---|---|
| gdn.in_proj_qkvz | 16384 × 5120 | 4 | cute-warp | 26.77 | cute-warp
+PDL | 26.66 | +0.4% | 0.61 → 0.84 |
| gdn.in_proj_qkvz | 16384 × 5120 | 8 | cute-warp | 26.81 | cute-warp
+PDL | 26.75 | +0.2% | 0.59 → 0.84 |
| gdn.in_proj_qkvz | 16384 × 5120 | 16 | cuBLASLt | 28.62 | cute-warp
+PDL | 28.43 | +0.7% | 0.63 → 0.97 |
| gdn.in_proj_ba \* | 96 × 5120 | 4 | cute-direct | 1.93 | cute-direct
+PDL / cute-direct | 1.73 | +12.3% | 0.31 → 0.46 |
| gdn.in_proj_ba \* | 96 × 5120 | 8 | cute-direct | 2.30 | cute-direct
+PDL | 1.86 | +23.8% | 0.33 → 0.48 |
| gdn.in_proj_ba \* | 96 × 5120 | 16 | cute-direct | 2.89 | cute-direct
+PDL | 2.45 | +17.9% | 0.35 → 0.49 |
| out_proj / o_proj | 5120 × 6144 | 4 | cute-warp | 12.11 | cute-warp
+PDL | 11.29 | +7.3% | 0.49 → 0.71 |
| out_proj / o_proj | 5120 × 6144 | 8 | cute-warp | 12.54 | cute-warp
+PDL | 11.35 | +10.5% | 0.50 → 0.72 |
| out_proj / o_proj | 5120 × 6144 | 16 | cute-warp | 13.27 | cute-warp
+PDL | 12.37 | +7.3% | 0.52 → 0.86 |
| attn.qkv_proj | 14336 × 5120 | 4 | cute-warp | 24.31 | cute-warp +PDL
| 23.90 | +1.7% | 0.57 → 0.83 |
| attn.qkv_proj | 14336 × 5120 | 8 | cute-warp | 24.05 | cute-warp +PDL
| 23.96 | +0.4% | 0.57 → 0.81 |
| attn.qkv_proj | 14336 × 5120 | 16 | cute-warp | 24.90 | cute-warp +PDL
| 24.72 | +0.7% | 0.58 → 0.88 |
| mlp.gate_up_proj | 34816 × 5120 | 4 | cute-warp | 53.26 | cute-warp
+PDL | 52.76 | +0.9% | 0.81 → 1.16 |
| mlp.gate_up_proj | 34816 × 5120 | 8 | cute-warp | 54.08 | cute-warp
+PDL | 53.41 | +1.3% | 0.81 → 1.16 |
| mlp.gate_up_proj | 34816 × 5120 | 16 | cuBLASLt | 55.18 | cuBLASLt /
cute-warp +PDL | 54.70 | +0.9% | 0.91 → 1.37 |
| mlp.down_proj | 5120 × 17408 | 4 | TGV | 31.08 | cute-splitk +PDL |
30.20 | +2.9% | 0.60 → 0.80 |
| mlp.down_proj | 5120 × 17408 | 8 | TGV | 30.64 | TGV +PDL /
cute-splitk +PDL | 30.35 | +0.9% | 0.59 → 0.80 |
| mlp.down_proj | 5120 × 17408 | 16 | TGV | 31.02 | TGV +PDL | 30.71 |
+1.0% | 0.61 → 0.84 |
| mtp.fc | 5120 × 10240 | 4 | cute-warp | 18.47 | cute-warp +PDL | 17.74
| +4.1% | 0.55 → 0.78 |
| mtp.fc | 5120 × 10240 | 8 | cute-warp | 18.58 | cute-warp +PDL | 18.20
| +2.1% | 0.52 → 0.75 |
| mtp.fc | 5120 × 10240 | 16 | TGV | 19.85 | TGV +PDL | 19.00 | +4.5% |
0.56 → 0.84 |

</details>

<details>
<summary>All 154 shapes: picks, time and tuning time, main vs this PR on
GB300</summary>

| model | layer | N × K | M | main picks | main, µs | branch picks |
branch, µs | speedup | tuning main → branch, s |
|---|---|---|---|---|---|---|---|---|---|
| qwen3.8-27b | gdn.in_proj_qkvz | 16384 × 5120 | 1 | cute-direct |
26.05 | cute-direct / cute-direct +PDL | 25.70 | +1.4% | 0.63 → 0.92 |
| qwen3.8-27b | gdn.in_proj_qkvz | 16384 × 5120 | 2 | cute-direct |
26.17 | cute-direct / cute-direct +PDL | 26.19 | -0.1% | 0.62 → 0.90 |
| qwen3.8-27b | gdn.in_proj_qkvz | 16384 × 5120 | 4 | cute-warp | 26.77
| cute-warp +PDL | 26.66 | +0.4% | 0.61 → 0.84 |
| qwen3.8-27b | gdn.in_proj_qkvz | 16384 × 5120 | 8 | cute-warp | 26.81
| cute-warp +PDL | 26.75 | +0.2% | 0.59 → 0.84 |
| qwen3.8-27b | gdn.in_proj_qkvz | 16384 × 5120 | 16 | cuBLASLt | 28.62
| cute-warp +PDL | 28.43 | +0.7% | 0.63 → 0.97 |
| qwen3.8-27b | gdn.in_proj_qkvz | 16384 × 5120 | 32 | cuBLASLt / cuDNN
| 28.76 | cuDNN / cute-splitk +PDL | 28.93 | -0.6% | 0.68 → 1.06 |
| qwen3.8-27b | gdn.in_proj_qkvz | 16384 × 5120 | 64 | cuBLASLt | 29.20
| cute-fallback / TGV +PDL | 29.66 | -1.5% | 0.60 → 0.85 |
| qwen3.8-27b | gdn.in_proj_qkvz | 16384 × 5120 | 128 | cuDNN | 31.14 |
cuBLASLt / cute-fallback | 31.46 | -1.0% | 0.67 → 1.00 |
| qwen3.8-27b | gdn.in_proj_qkvz | 16384 × 5120 | 256 | cuBLASLt | 34.93
| cuBLASLt / cute-fallback | 35.06 | -0.4% | 0.80 → 1.19 |
| qwen3.8-27b | gdn.in_proj_qkvz | 16384 × 5120 | 512 | cuDNN /
cute-fallback | 51.58 | cuBLASLt / cute-fallback | 51.83 | -0.5% | 1.04
→ 1.56 |
| qwen3.8-27b | gdn.in_proj_qkvz | 16384 × 5120 | 1024 | cute-fallback |
98.81 | cute-fallback | 96.44 | +2.5% | 1.54 → 2.38 |
| qwen3.8-27b | gdn.in_proj_qkvz | 16384 × 5120 | 2048 | cuDNN | 186.69
| cuDNN | 177.21 | **+5.3%** | 2.29 → 3.84 |
| qwen3.8-27b | gdn.in_proj_qkvz | 16384 × 5120 | 4096 | cuDNN | 388.75
| cuDNN | 388.41 | +0.1% | 3.93 → 6.96 |
| qwen3.8-27b | gdn.in_proj_qkvz | 16384 × 5120 | 8192 | cuBLASLt |
776.67 | cuBLASLt / cuDNN | 775.31 | +0.2% | 7.43 → 13.39 |
| qwen3.8-27b | gdn.in_proj_ba | 96 × 5120 | 1 | cute-direct | 1.70 |
cute-direct +PDL | 1.19 | **+43.0%** | 0.33 → 0.48 |
| qwen3.8-27b | gdn.in_proj_ba | 96 × 5120 | 2 | cute-direct | 1.77 |
cute-direct +PDL | 1.26 | **+40.2%** | 0.30 → 0.45 |
| qwen3.8-27b | gdn.in_proj_ba | 96 × 5120 | 4 | cute-direct | 1.93 |
cute-direct +PDL / cute-direct | 1.73 | **+12.3%** | 0.31 → 0.46 |
| qwen3.8-27b | gdn.in_proj_ba | 96 × 5120 | 8 | cute-direct | 2.30 |
cute-direct +PDL | 1.86 | **+23.8%** | 0.33 → 0.48 |
| qwen3.8-27b | gdn.in_proj_ba | 96 × 5120 | 16 | cute-direct | 2.89 |
cute-direct +PDL | 2.45 | **+17.9%** | 0.35 → 0.49 |
| qwen3.8-27b | gdn.in_proj_ba | 96 × 5120 | 32 | cute-direct | 3.53 |
TinyGEMM +PDL | 2.68 | **+31.9%** | 0.41 → 0.62 |
| qwen3.8-27b | gdn.in_proj_ba | 96 × 5120 | 64 | TinyGEMM | 3.62 |
TinyGEMM +PDL | 2.63 | **+37.7%** | 0.29 → 0.38 |
| qwen3.8-27b | gdn.in_proj_ba | 96 × 5120 | 128 | TinyGEMM | 3.70 |
TinyGEMM +PDL | 2.82 | **+30.9%** | 0.28 → 0.37 |
| qwen3.8-27b | gdn.in_proj_ba | 96 × 5120 | 256 | cuDNN / cuBLASLt |
4.62 | cuDNN / cuBLASLt | 4.49 | +2.8% | 0.29 → 0.37 |
| qwen3.8-27b | gdn.in_proj_ba | 96 × 5120 | 512 | cuBLASLt | 5.45 | TGV
+PDL | 4.88 | **+11.8%** | 0.29 → 0.38 |
| qwen3.8-27b | gdn.in_proj_ba | 96 × 5120 | 1024 | cute-fallback /
cuBLASLt | 5.99 | TGV +PDL | 5.26 | **+14.0%** | 0.29 → 0.39 |
| qwen3.8-27b | gdn.in_proj_ba | 96 × 5120 | 2048 | cute-fallback /
cuBLASLt | 5.97 | TGV +PDL | 5.58 | **+7.0%** | 0.30 → 0.40 |
| qwen3.8-27b | gdn.in_proj_ba | 96 × 5120 | 4096 | TGV | 7.89 | TGV
+PDL | 6.77 | **+16.5%** | 0.35 → 0.46 |
| qwen3.8-27b | gdn.in_proj_ba | 96 × 5120 | 8192 | cuDNN / cuBLASLt |
10.93 | cuDNN | 10.30 | **+6.4%** | 0.43 → 0.59 |
| qwen3.8-27b | gdn.out_proj, attn.o_proj | 5120 × 6144 | 1 |
cute-direct | 10.86 | cute-direct +PDL | 10.63 | +2.2% | 0.56 → 0.84 |
| qwen3.8-27b | gdn.out_proj, attn.o_proj | 5120 × 6144 | 2 |
cute-direct | 11.58 | cute-direct +PDL / cute-direct | 11.36 | +2.0% |
0.54 → 0.83 |
| qwen3.8-27b | gdn.out_proj, attn.o_proj | 5120 × 6144 | 4 | cute-warp
| 12.11 | cute-warp +PDL | 11.29 | **+7.3%** | 0.49 → 0.71 |
| qwen3.8-27b | gdn.out_proj, attn.o_proj | 5120 × 6144 | 8 | cute-warp
| 12.54 | cute-warp +PDL | 11.35 | **+10.5%** | 0.50 → 0.72 |
| qwen3.8-27b | gdn.out_proj, attn.o_proj | 5120 × 6144 | 16 | cute-warp
| 13.27 | cute-warp +PDL | 12.37 | **+7.3%** | 0.52 → 0.86 |
| qwen3.8-27b | gdn.out_proj, attn.o_proj | 5120 × 6144 | 32 | TGV |
13.57 | TGV +PDL | 12.26 | **+10.7%** | 0.52 → 0.80 |
| qwen3.8-27b | gdn.out_proj, attn.o_proj | 5120 × 6144 | 64 | TGV |
14.34 | TGV +PDL | 13.04 | **+10.0%** | 0.41 → 0.53 |
| qwen3.8-27b | gdn.out_proj, attn.o_proj | 5120 × 6144 | 128 | cuDNN /
cute-fallback | 14.38 | cuDNN / cuBLASLt | 14.25 | +0.9% | 0.45 → 0.62 |
| qwen3.8-27b | gdn.out_proj, attn.o_proj | 5120 × 6144 | 256 |
cute-fallback / cuDNN | 16.85 | cute-fallback / cuBLASLt | 16.92 | -0.4%
| 0.51 → 0.75 |
| qwen3.8-27b | gdn.out_proj, attn.o_proj | 5120 × 6144 | 512 |
cute-fallback / cuBLASLt | 21.35 | cute-fallback / cuDNN | 21.34 | +0.0%
| 0.64 → 0.93 |
| qwen3.8-27b | gdn.out_proj, attn.o_proj | 5120 × 6144 | 1024 | cuDNN /
cute-fallback | 37.63 | cuDNN / cute-fallback | 37.68 | -0.1% | 0.83 →
1.20 |
| qwen3.8-27b | gdn.out_proj, attn.o_proj | 5120 × 6144 | 2048 |
cuBLASLt / cute-fallback | 71.55 | cuDNN | 69.06 | +3.6% | 1.09 → 1.54 |
| qwen3.8-27b | gdn.out_proj, attn.o_proj | 5120 × 6144 | 4096 |
cuBLASLt | 158.78 | cuBLASLt / cuDNN | 160.39 | -1.0% | 1.40 → 2.06 |
| qwen3.8-27b | gdn.out_proj, attn.o_proj | 5120 × 6144 | 8192 |
cuBLASLt / cute-fallback | 311.22 | cute-fallback / cuDNN | 307.85 |
+1.1% | 1.95 → 3.04 |
| qwen3.8-27b | attn.qkv_proj | 14336 × 5120 | 1 | cute-direct | 23.06 |
cute-direct +PDL | 23.00 | +0.3% | 0.62 → 0.91 |
| qwen3.8-27b | attn.qkv_proj | 14336 × 5120 | 2 | cute-direct | 23.71 |
cute-direct +PDL | 23.80 | -0.4% | 0.62 → 0.92 |
| qwen3.8-27b | attn.qkv_proj | 14336 × 5120 | 4 | cute-warp | 24.31 |
cute-warp +PDL | 23.90 | +1.7% | 0.57 → 0.83 |
| qwen3.8-27b | attn.qkv_proj | 14336 × 5120 | 8 | cute-warp | 24.05 |
cute-warp +PDL | 23.96 | +0.4% | 0.57 → 0.81 |
| qwen3.8-27b | attn.qkv_proj | 14336 × 5120 | 16 | cute-warp | 24.90 |
cute-warp +PDL | 24.72 | +0.7% | 0.58 → 0.88 |
| qwen3.8-27b | attn.qkv_proj | 14336 × 5120 | 32 | cuBLASLt / cuDNN |
26.00 | TGV +PDL | 25.91 | +0.3% | 0.60 → 0.94 |
| qwen3.8-27b | attn.qkv_proj | 14336 × 5120 | 64 | cuDNN | 26.78 |
cuDNN | 26.75 | +0.1% | 0.56 → 0.80 |
| qwen3.8-27b | attn.qkv_proj | 14336 × 5120 | 128 | cute-fallback /
cuBLASLt | 27.29 | cute-fallback | 27.45 | -0.6% | 0.62 → 0.93 |
| qwen3.8-27b | attn.qkv_proj | 14336 × 5120 | 256 | cute-fallback |
31.01 | cute-fallback / cuDNN | 30.98 | +0.1% | 0.73 → 1.09 |
| qwen3.8-27b | attn.qkv_proj | 14336 × 5120 | 512 | cuBLASLt /
cute-fallback | 43.68 | cuBLASLt / cuDNN | 43.80 | -0.3% | 0.95 → 1.43 |
| qwen3.8-27b | attn.qkv_proj | 14336 × 5120 | 1024 | cuDNN | 92.13 |
cuBLASLt / cuDNN | 80.42 | **+14.6%** | 1.38 → 2.11 |
| qwen3.8-27b | attn.qkv_proj | 14336 × 5120 | 2048 | cuDNN | 159.48 |
cuDNN | 155.44 | +2.6% | 2.07 → 3.37 |
| qwen3.8-27b | attn.qkv_proj | 14336 × 5120 | 4096 | cuDNN | 336.20 |
cuDNN | 316.93 | **+6.3%** | 3.40 → 5.93 |
| qwen3.8-27b | attn.qkv_proj | 14336 × 5120 | 8192 | cuDNN / cuBLASLt |
695.61 | cute-fallback | 692.52 | +0.4% | 6.34 → 11.36 |
| qwen3.8-27b | mlp.gate_up_proj | 34816 × 5120 | 1 | cute-direct |
51.48 | cute-direct +PDL | 51.50 | -0.1% | 0.90 → 1.28 |
| qwen3.8-27b | mlp.gate_up_proj | 34816 × 5120 | 2 | cute-direct |
52.09 | cute-direct +PDL | 51.96 | +0.2% | 0.88 → 1.28 |
| qwen3.8-27b | mlp.gate_up_proj | 34816 × 5120 | 4 | cute-warp | 53.26
| cute-warp +PDL | 52.76 | +0.9% | 0.81 → 1.16 |
| qwen3.8-27b | mlp.gate_up_proj | 34816 × 5120 | 8 | cute-warp | 54.08
| cute-warp +PDL | 53.41 | +1.3% | 0.81 → 1.16 |
| qwen3.8-27b | mlp.gate_up_proj | 34816 × 5120 | 16 | cuBLASLt | 55.18
| cuBLASLt / cute-warp +PDL | 54.70 | +0.9% | 0.91 → 1.37 |
| qwen3.8-27b | mlp.gate_up_proj | 34816 × 5120 | 32 | cuDNN | 55.33 |
cuBLASLt | 55.31 | +0.0% | 0.99 → 1.54 |
| qwen3.8-27b | mlp.gate_up_proj | 34816 × 5120 | 64 | cute-fallback /
cuBLASLt | 57.00 | cute-fallback / cuBLASLt | 56.90 | +0.2% | 0.85 →
1.21 |
| qwen3.8-27b | mlp.gate_up_proj | 34816 × 5120 | 128 | cuDNN / cuBLASLt
| 61.73 | cute-fallback / CUTLASS | 61.42 | +0.5% | 0.93 → 1.34 |
| qwen3.8-27b | mlp.gate_up_proj | 34816 × 5120 | 256 | cuDNN | 67.90 |
cuDNN / cuBLASLt | 67.95 | -0.1% | 1.14 → 1.69 |
| qwen3.8-27b | mlp.gate_up_proj | 34816 × 5120 | 512 | cuBLASLt / cuDNN
| 107.63 | cuDNN | 103.44 | +4.1% | 1.62 → 2.50 |
| qwen3.8-27b | mlp.gate_up_proj | 34816 × 5120 | 1024 | cuDNN | 207.39
| cuDNN | 202.49 | +2.5% | 2.43 → 4.07 |
| qwen3.8-27b | mlp.gate_up_proj | 34816 × 5120 | 2048 | cuDNN | 417.48
| cuDNN | 416.78 | +0.2% | 4.14 → 7.36 |
| qwen3.8-27b | mlp.gate_up_proj | 34816 × 5120 | 4096 | cuDNN | 840.38
| cuDNN | 839.01 | +0.2% | 7.78 → 14.16 |
| qwen3.8-27b | mlp.gate_up_proj | 34816 × 5120 | 8192 | cuDNN | 1711.24
| cuBLASLt / cuDNN | 1687.73 | +1.4% | 15.80 → 28.52 |
| qwen3.8-27b | mlp.down_proj | 5120 × 17408 | 1 | cute-direct | 28.76 |
cute-direct +PDL | 28.59 | +0.6% | 0.67 → 0.91 |
| qwen3.8-27b | mlp.down_proj | 5120 × 17408 | 2 | cute-direct | 28.78 |
cute-direct +PDL | 28.50 | +1.0% | 0.67 → 0.90 |
| qwen3.8-27b | mlp.down_proj | 5120 × 17408 | 4 | TGV | 31.08 |
cute-splitk +PDL | 30.20 | +2.9% | 0.60 → 0.80 |
| qwen3.8-27b | mlp.down_proj | 5120 × 17408 | 8 | TGV | 30.64 | TGV
+PDL / cute-splitk +PDL | 30.35 | +0.9% | 0.59 → 0.80 |
| qwen3.8-27b | mlp.down_proj | 5120 × 17408 | 16 | TGV | 31.02 | TGV
+PDL | 30.71 | +1.0% | 0.61 → 0.84 |
| qwen3.8-27b | mlp.down_proj | 5120 × 17408 | 32 | TGV | 31.80 | TGV
+PDL | 31.27 | +1.7% | 0.65 → 0.90 |
| qwen3.8-27b | mlp.down_proj | 5120 × 17408 | 64 | TGV | 33.97 | TGV
+PDL | 32.86 | +3.4% | 0.68 → 0.92 |
| qwen3.8-27b | mlp.down_proj | 5120 × 17408 | 128 | cuDNN | 38.24 | TGV
+PDL | 36.47 | +4.9% | 0.75 → 1.06 |
| qwen3.8-27b | mlp.down_proj | 5120 × 17408 | 256 | cuDNN /
cute-fallback | 42.04 | cuBLASLt | 42.07 | -0.1% | 0.85 → 1.22 |
| qwen3.8-27b | mlp.down_proj | 5120 × 17408 | 512 | cuDNN / cuBLASLt |
55.82 | cuBLASLt / cuDNN | 56.33 | -0.9% | 1.06 → 1.51 |
| qwen3.8-27b | mlp.down_proj | 5120 × 17408 | 1024 | cuBLASLt | 109.94
| cuDNN | 106.91 | +2.8% | 1.36 → 1.98 |
| qwen3.8-27b | mlp.down_proj | 5120 × 17408 | 2048 | cuBLASLt /
cute-fallback | 208.33 | cuBLASLt / cute-fallback | 210.51 | -0.9% |
1.81 → 2.82 |
| qwen3.8-27b | mlp.down_proj | 5120 × 17408 | 4096 | cuDNN /
cute-fallback | 425.23 | cuDNN | 423.96 | +0.3% | 2.94 → 4.87 |
| qwen3.8-27b | mlp.down_proj | 5120 × 17408 | 8192 | cute-fallback |
863.05 | cute-fallback / cuDNN | 867.03 | -0.5% | 5.47 → 9.29 |
| qwen3.8-27b | mtp.fc | 5120 × 10240 | 1 | cute-direct | 17.29 |
cute-direct +PDL | 16.74 | +3.3% | 0.60 → 0.86 |
| qwen3.8-27b | mtp.fc | 5120 × 10240 | 2 | cute-direct | 18.38 |
cute-warp +PDL | 17.20 | **+6.9%** | 0.59 → 0.84 |
| qwen3.8-27b | mtp.fc | 5120 × 10240 | 4 | cute-warp | 18.47 |
cute-warp +PDL | 17.74 | +4.1% | 0.55 → 0.78 |
| qwen3.8-27b | mtp.fc | 5120 × 10240 | 8 | cute-warp | 18.58 |
cute-warp +PDL | 18.20 | +2.1% | 0.52 → 0.75 |
| qwen3.8-27b | mtp.fc | 5120 × 10240 | 16 | TGV | 19.85 | TGV +PDL |
19.00 | +4.5% | 0.56 → 0.84 |
| qwen3.8-27b | mtp.fc | 5120 × 10240 | 32 | TGV | 20.05 | TGV +PDL |
19.19 | +4.5% | 0.55 → 0.79 |
| qwen3.8-27b | mtp.fc | 5120 × 10240 | 64 | TGV | 22.02 | TGV +PDL |
20.76 | **+6.0%** | 0.52 → 0.71 |
| qwen3.8-27b | mtp.fc | 5120 × 10240 | 128 | cuDNN | 24.74 | TGV +PDL |
23.28 | **+6.3%** | 0.58 → 0.84 |
| qwen3.8-27b | mtp.fc | 5120 × 10240 | 256 | cuDNN | 26.76 | cuBLASLt /
cuDNN | 26.65 | +0.4% | 0.68 → 1.00 |
| qwen3.8-27b | mtp.fc | 5120 × 10240 | 512 | cuDNN / cuBLASLt | 34.56 |
cuDNN | 34.47 | +0.3% | 0.84 → 1.22 |
| qwen3.8-27b | mtp.fc | 5120 × 10240 | 1024 | cute-fallback | 64.59 |
cuBLASLt | 64.75 | -0.3% | 1.07 → 1.55 |
| qwen3.8-27b | mtp.fc | 5120 × 10240 | 2048 | cuBLASLt / cuDNN | 127.86
| cuBLASLt | 119.20 | **+7.3%** | 1.43 → 2.11 |
| qwen3.8-27b | mtp.fc | 5120 × 10240 | 4096 | cuBLASLt | 261.01 |
cute-fallback / cuBLASLt | 272.12 | -4.1% | 1.99 → 3.17 |
| qwen3.8-27b | mtp.fc | 5120 × 10240 | 8192 | cute-fallback | 520.07 |
cuDNN / cute-fallback | 519.31 | +0.2% | 3.61 → 5.61 |
| llama-3.1-8b | attn.qkv_proj | 6144 × 4096 | 1 | cute-direct | 9.09 |
cute-warp +PDL | 8.73 | +4.1% | 0.47 → 0.71 |
| llama-3.1-8b | attn.qkv_proj | 6144 × 4096 | 2 | cute-direct | 9.67 |
cute-warp +PDL | 8.59 | **+12.5%** | 0.47 → 0.72 |
| llama-3.1-8b | attn.qkv_proj | 6144 × 4096 | 4 | cute-warp | 9.83 |
cute-warp +PDL | 8.83 | **+11.3%** | 0.43 → 0.65 |
| llama-3.1-8b | attn.qkv_proj | 6144 × 4096 | 8 | cute-warp | 9.77 |
cute-warp +PDL | 8.85 | **+10.4%** | 0.43 → 0.64 |
| llama-3.1-8b | attn.qkv_proj | 6144 × 4096 | 16 | cute-warp | 10.60 |
cute-warp +PDL | 9.48 | **+11.8%** | 0.46 → 0.74 |
| llama-3.1-8b | attn.qkv_proj | 6144 × 4096 | 32 | cuDNN | 10.57 | TGV
+PDL | 10.02 | **+5.5%** | 0.45 → 0.72 |
| llama-3.1-8b | attn.qkv_proj | 6144 × 4096 | 64 | cuDNN | 11.31 | TGV
+PDL | 10.46 | **+8.1%** | 0.34 → 0.47 |
| llama-3.1-8b | attn.qkv_proj | 6144 × 4096 | 128 | cuBLASLt | 11.01 |
cuDNN / cuBLASLt | 10.98 | +0.2% | 0.38 → 0.52 |
| llama-3.1-8b | attn.qkv_proj | 6144 × 4096 | 256 | cuDNN / cuBLASLt |
13.02 | cuBLASLt / cuDNN | 13.05 | -0.2% | 0.44 → 0.65 |
| llama-3.1-8b | attn.qkv_proj | 6144 × 4096 | 512 | cuDNN /
cute-fallback | 17.44 | cuBLASLt / cute-fallback | 17.34 | +0.6% | 0.56
→ 0.85 |
| llama-3.1-8b | attn.qkv_proj | 6144 × 4096 | 1024 | cuDNN /
cute-fallback | 30.53 | cute-fallback / cuDNN | 30.27 | +0.8% | 0.71 →
1.06 |
| llama-3.1-8b | attn.qkv_proj | 6144 × 4096 | 2048 | cuDNN /
cute-fallback | 57.08 | cuDNN | 56.76 | +0.6% | 0.97 → 1.39 |
| llama-3.1-8b | attn.qkv_proj | 6144 × 4096 | 4096 | cuDNN /
cute-fallback | 118.30 | cuDNN | 124.19 | -4.8% | 1.31 → 1.88 |
| llama-3.1-8b | attn.qkv_proj | 6144 × 4096 | 8192 | cute-fallback /
cuBLASLt | 241.83 | cuDNN / cuBLASLt | 242.04 | -0.1% | 1.75 → 2.71 |
| llama-3.1-8b | attn.o_proj | 4096 × 4096 | 1 | cute-direct | 6.72 |
cute-warp +PDL | 5.66 | **+18.6%** | 0.44 → 0.70 |
| llama-3.1-8b | attn.o_proj | 4096 × 4096 | 2 | cute-direct | 7.13 |
cute-warp +PDL | 5.69 | **+25.2%** | 0.44 → 0.66 |
| llama-3.1-8b | attn.o_proj | 4096 × 4096 | 4 | cute-warp | 7.15 |
cute-warp +PDL | 5.85 | **+22.2%** | 0.40 → 0.61 |
| llama-3.1-8b | attn.o_proj | 4096 × 4096 | 8 | cute-warp | 7.23 |
cute-warp +PDL | 6.03 | **+20.0%** | 0.40 → 0.64 |
| llama-3.1-8b | attn.o_proj | 4096 × 4096 | 16 | cute-warp | 7.57 |
cute-warp +PDL | 6.08 | **+24.4%** | 0.43 → 0.69 |
| llama-3.1-8b | attn.o_proj | 4096 × 4096 | 32 | cute-warp | 8.23 |
cute-warp +PDL | 6.91 | **+19.1%** | 0.42 → 0.64 |
| llama-3.1-8b | attn.o_proj | 4096 × 4096 | 64 | cuDNN | 8.65 | TGV
+PDL | 7.92 | **+9.1%** | 0.31 → 0.41 |
| llama-3.1-8b | attn.o_proj | 4096 × 4096 | 128 | cuDNN | 8.93 | TGV
+PDL | 8.36 | **+6.8%** | 0.33 → 0.47 |
| llama-3.1-8b | attn.o_proj | 4096 × 4096 | 256 | cuDNN / cute-fallback
| 9.57 | cuDNN / cuBLASLt | 9.67 | -1.1% | 0.37 → 0.55 |
| llama-3.1-8b | attn.o_proj | 4096 × 4096 | 512 | cute-fallback / cuDNN
| 12.58 | cuDNN | 12.54 | +0.3% | 0.46 → 0.68 |
| llama-3.1-8b | attn.o_proj | 4096 × 4096 | 1024 | cute-fallback |
20.46 | cuDNN / cute-fallback | 20.50 | -0.2% | 0.60 → 0.91 |
| llama-3.1-8b | attn.o_proj | 4096 × 4096 | 2048 | cute-fallback |
39.50 | cuDNN | 39.49 | +0.0% | 0.81 → 1.21 |
| llama-3.1-8b | attn.o_proj | 4096 × 4096 | 4096 | cute-fallback /
cuBLASLt | 79.01 | cuBLASLt / cuDNN | 81.63 | -3.2% | 1.11 → 1.61 |
| llama-3.1-8b | attn.o_proj | 4096 × 4096 | 8192 | cuDNN | 161.35 |
cuDNN | 162.02 | -0.4% | 1.48 → 2.17 |
| llama-3.1-8b | mlp.gate_up_proj | 28672 × 4096 | 1 | cute-direct |
34.54 | cute-direct +PDL | 34.82 | -0.8% | 0.79 → 1.09 |
| llama-3.1-8b | mlp.gate_up_proj | 28672 × 4096 | 2 | cute-direct |
35.52 | cute-direct +PDL | 35.53 | -0.0% | 0.75 → 1.15 |
| llama-3.1-8b | mlp.gate_up_proj | 28672 × 4096 | 4 | cute-warp | 35.19
| cute-warp +PDL | 34.87 | +0.9% | 0.71 → 0.98 |
| llama-3.1-8b | mlp.gate_up_proj | 28672 × 4096 | 8 | cuBLASLt /
cute-warp | 35.80 | cute-warp +PDL | 35.01 | +2.2% | 0.70 → 0.98 |
| llama-3.1-8b | mlp.gate_up_proj | 28672 × 4096 | 16 | cuBLASLt / cuDNN
| 36.88 | cuBLASLt | 36.93 | -0.1% | 0.68 → 1.00 |
| llama-3.1-8b | mlp.gate_up_proj | 28672 × 4096 | 32 | cuBLASLt | 37.31
| cuDNN | 37.48 | -0.4% | 0.76 → 1.19 |
| llama-3.1-8b | mlp.gate_up_proj | 28672 × 4096 | 64 | cuDNN / cuBLASLt
| 37.68 | cute-fallback / cuDNN | 37.89 | -0.5% | 0.69 → 1.02 |
| llama-3.1-8b | mlp.gate_up_proj | 28672 × 4096 | 128 | cuBLASLt /
CUTLASS | 41.22 | CUTLASS | 41.06 | +0.4% | 0.78 → 1.13 |
| llama-3.1-8b | mlp.gate_up_proj | 28672 × 4096 | 256 | cuDNN /
cuBLASLt | 48.34 | cute-fallback / cuDNN | 48.23 | +0.3% | 0.92 → 1.37 |
| llama-3.1-8b | mlp.gate_up_proj | 28672 × 4096 | 512 | cuBLASLt /
cute-fallback | 69.52 | cuDNN / cuBLASLt | 69.05 | +0.7% | 1.26 → 1.93 |
| llama-3.1-8b | mlp.gate_up_proj | 28672 × 4096 | 1024 | cuDNN | 137.04
| cuDNN | 129.93 | **+5.5%** | 1.86 → 2.98 |
| llama-3.1-8b | mlp.gate_up_proj | 28672 × 4096 | 2048 | cuDNN | 251.62
| cuDNN | 252.52 | -0.3% | 2.93 → 5.02 |
| llama-3.1-8b | mlp.gate_up_proj | 28672 × 4096 | 4096 | cuDNN | 532.10
| cuDNN | 533.71 | -0.3% | 5.21 → 9.34 |
| llama-3.1-8b | mlp.gate_up_proj | 28672 × 4096 | 8192 | cute-fallback
/ cuDNN | 1104.38 | cuDNN / cuBLASLt | 1108.28 | -0.4% | 10.23 → 18.48 |
| llama-3.1-8b | mlp.down_proj | 4096 × 14336 | 1 | cute-direct | 18.54
| cute-direct +PDL | 18.21 | +1.8% | 0.65 → 0.96 |
| llama-3.1-8b | mlp.down_proj | 4096 × 14336 | 2 | cute-direct | 19.75
| cute-warp +PDL | 18.49 | **+6.8%** | 0.64 → 0.94 |
| llama-3.1-8b | mlp.down_proj | 4096 × 14336 | 4 | cute-warp | 19.58 |
cute-warp +PDL | 18.51 | **+5.8%** | 0.60 → 0.83 |
| llama-3.1-8b | mlp.down_proj | 4096 × 14336 | 8 | cute-warp | 19.46 |
cute-warp +PDL | 18.65 | +4.4% | 0.57 → 0.79 |
| llama-3.1-8b | mlp.down_proj | 4096 × 14336 | 16 | cute-warp | 20.32 |
cute-warp +PDL | 19.23 | **+5.7%** | 0.60 → 0.90 |
| llama-3.1-8b | mlp.down_proj | 4096 × 14336 | 32 | cute-warp | 22.03 |
cute-warp +PDL | 21.04 | +4.7% | 0.58 → 0.86 |
| llama-3.1-8b | mlp.down_proj | 4096 × 14336 | 64 | TGV | 23.36 | TGV |
23.53 | -0.7% | 0.54 → 0.73 |
| llama-3.1-8b | mlp.down_proj | 4096 × 14336 | 128 | TGV | 25.20 | TGV
+PDL | 24.48 | +2.9% | 0.62 → 0.84 |
| llama-3.1-8b | mlp.down_proj | 4096 × 14336 | 256 | TGV | 29.22 | TGV
+PDL | 28.26 | +3.4% | 0.69 → 1.01 |
| llama-3.1-8b | mlp.down_proj | 4096 × 14336 | 512 | cuDNN /
cute-fallback | 38.15 | cuDNN / cuBLASLt | 38.25 | -0.3% | 0.82 → 1.22 |
| llama-3.1-8b | mlp.down_proj | 4096 × 14336 | 1024 | cuBLASLt /
cute-fallback | 65.94 | cuDNN / cute-fallback | 65.98 | -0.1% | 1.10 →
1.59 |
| llama-3.1-8b | mlp.down_proj | 4096 × 14336 | 2048 | cute-fallback |
136.55 | cuDNN | 130.58 | +4.6% | 1.49 → 2.20 |
| llama-3.1-8b | mlp.down_proj | 4096 × 14336 | 4096 | cute-fallback |
293.94 | cute-fallback / cuDNN | 284.58 | +3.3% | 2.08 → 3.28 |
| llama-3.1-8b | mlp.down_proj | 4096 × 14336 | 8192 | cute-fallback /
cuBLASLt | 587.03 | cuDNN | 582.79 | +0.7% | 3.51 → 5.84 |

</details>

## 🔍 Related Issues

Addresses the PDL dependency concern raised in the CodeRabbit review of
this PR.

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

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/gemm/test_mm_bf16.py
tests/autotuner/test_autotune_cache_v2.py
tests/autotuner/test_autotune_cache_scope.py`

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

The input-dependency hazard was also reproduced on SM100: a producer
signals PDL availability, then writes the weights later. TGV with PDL
read old weights in all three trials; non-PDL returned the correct
result in all three. This demonstrates why `pdl=None` must be an
explicit opt-in while these kernels assume resident weights. It is not a
claim that the documented static-weight use case is incorrect.

Maintainer follow-up preserves the default `pdl=False` and adds v2
persistence/capture coverage. The partner's PDL candidate expansion is
unchanged for explicit `pdl=None`.

Local source validation on SM100 (Torch 2.14.0+cu130, CuTe DSL 4.8.0):
PDL dispatch/key/managed-reload tests: **9 passed**, with one unrelated
cuTile test skipped because cuda-tile is unavailable. V2 cache/scope
suites: **112 passed**. Changed-file pre-commit hooks passed. The
complete BF16 GEMM file passed: **40 passed, 3 skipped** (cuda-tile
unavailable). Upstream required CI is still in progress.

The managed-cache tests use deterministic candidate scores to verify
selection and persistence, then execute the real native kernels and
check numerics. They do not claim a timing or selection-quality
improvement. AI-assisted review and follow-up.

---------

Signed-off-by: Artem Perevedentsev <aperevedents@nvidia.com>
Co-authored-by: Yang Xu <yanxu@nvidia.com>

### [36ec610](https://github.com/flashinfer-ai/flashinfer/commit/36ec6101e76d34f364d7dee51a90e7660ac780a7)

- **作者**: eigen
- **时间**: 2026-10-30T23:09:02Z
- **提交信息**: perf(cake_warp_decode): launch choices for two SM100 decode rows (#8049)

`cake_warp_decode` is Cake's NVFP4 routed fused-MoE decode kernel. It is
called through
`flashinfer.fused_moe.trtllm_fp4_block_scale_routed_moe(...)` with
`CakeWarpDecodeConfig(backend="cake")`. It has one data type (NVFP4
W4A4, BF16 output), several activation variants and one fused form: FC1
with the activation, FC2 and the top-k finalize. This PR updates that
one fused form. Cake ships no other data type, layout or fused form of
this kernel. All of its activation variants use this fused form, and the
family ships on sm_100a and sm_103a.

This PR changes which kernels two decode rows on sm_100a launch, and
how. No kernel source or compiled kernel changes. No sm_103a launch
changes.

- **sm_100a, `e128_i1536_k8` at 8 tokens.** FC2 now launches an existing
sibling build of its FC2 kernel. In that build, the warp that claims
work takes work items before it waits on FC1. The neighbouring rows at
1, 2, 4, 5, 7 and 9 tokens already use it. Work items, K order, MMA and
epilogue are the same.
- **sm_100a, `h3072_e256_i768_k8` at 3 tokens.** The fused route-pack
FC1 launch now caps its task pool at 128 work slots and launches 120
CTAs (grid 12 x 10 instead of 12 x 12). The existing pools of
`h3072_e256_i384_k8` at 7 tokens and `h4096_e512_i512_k10` at 2 tokens
work the same way. The kernel and its work items are unchanged; fewer
CTAs claim them.
- **Other sm_100a rows.** The other 510 sm_100a rows launch the same
kernels as before.
- **sm_103a.** No launch changes.

The baseline is the current Cake version on FlashInfer main (merged as
FlashInfer #7995).

- On sm_100a (NVIDIA GB200, CUDA 13.4), no row of the 512 rows in 16
geometries is faster in both cold-L2 modes. One row is faster with the
memset flush and none with the read flush. That row is a changed row.
- `e128_i1536_k8` at 8 tokens is faster with the memset flush: 107.28 us
to 106.67 us (1.006x). With the read flush, it prints 91.44 us to 91.01
us (1.005x), but it does not count as faster in that mode, because two
of its four measurements are within noise.
- `h3072_e256_i768_k8` at 3 tokens does not count as faster in either
mode. With the memset flush, it prints 25.18 us to 25.06 us (1.005x),
and all four measurements are within noise. With the read flush, it
prints 22.48 us to 22.12 us (1.016x), and one of its four measurements
is within noise.
- No unchanged row counts as faster in either mode.
- One row is slower in one mode, and this PR does not change it:
`e192_i1536_k4_silu` at 14 tokens, read, 71.70 us previous and 72.15 us
new (ratio 1.006).

There is no sm_103a timing table because no sm_103a launch changes.

The "memset" and "read" column groups are two cold-L2 modes. Before
every call, we flush L2 with either a memset of a large buffer or a read
of one. Latency covers one routed-MoE call: FC1, FC2 and finalize.

Each table value is the mean of four measurements: two GPUs (one on each
of two nodes), each measured in two separate processes. Each measurement
is the median over 6 rounds of the per-round median over 40 calls, after
5 warmup calls.

A row counts as faster (or slower) in a mode only when all four
measurements show it faster (or slower) by more than run-to-run noise.
That means every round agrees, and the median beats both a 0.5 % floor
and the A/A noise band.

Speedups in the summary table are previous / new, so higher is better.
The per-row tables give ratio = new / previous, so lower is better
there.

**sm_100a** (NVIDIA GB200, driver 580.126.20, nvcc 13.4, CUDA driver API
13.4)

| Geometry | Rows faster in both modes (of 32) | Best speedup, memset
(tokens) | Best speedup, read (tokens) |
|---|---|---|---|
| `e128_i1536_k8` | 0 | 1.006x (8) | — |
| `e128_i3072_k4_swiglu_oa` | 0 | — | — |
| `e128_i768_k8` | 0 | — | — |
| `e192_i1536_k4_silu` | 0 | — | — |
| `e256_i1536_k8` | 0 | — | — |
| `e256_i2048_k6_clamp10` | 0 | — | — |
| `e256_i512_k8` | 0 | — | — |
| `e384_i768_k4` | 0 | — | — |
| `e512_i1024_k10` | 0 | — | — |
| `e512_i512_k10` | 0 | — | — |
| `e60_i1536_k4` | 0 | — | — |
| `e896_i3072_k16_situ` | 0 | — | — |
| `h3072_e256_i384_k8` | 0 | — | — |
| `h3072_e256_i768_k8` | 0 | — | — |
| `h4096_e512_i256_k10` | 0 | — | — |
| `h4096_e512_i512_k10` | 0 | — | — |

`e192_i1536_k4_silu` at 14 tokens is slower in the read mode: 71.70 us
previous, 72.15 us new (ratio 1.006).

**sm_100a** (NVIDIA GB200, driver 580.126.20, nvcc 13.4, CUDA driver API
13.4). Latency in us of one routed-MoE call (FC1, FC2, finalize), cold
L2; previous = the current Cake version (FlashInfer main), new = this
PR; ratio = new / previous. **Bold** num_tokens: this PR changes the
row's launches. Plain: the row launches the same kernels as the previous
version.

`e128_i768_k8`: hidden 2048, intermediate 768, 128 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|14.37|14.37|1.000|12.62|12.55|0.994|
|2|18.26|18.16|0.995|15.81|15.77|0.997|
|3|21.72|21.77|1.002|18.39|18.36|0.998|
|4|24.01|23.97|0.998|19.52|19.69|1.009|
|5|28.09|28.18|1.003|22.98|22.90|0.997|
|6|31.11|31.11|1.000|24.81|24.76|0.998|
|7|35.92|35.87|0.999|27.97|27.78|0.993|
|8|39.66|39.63|0.999|30.75|30.80|1.002|
|9|42.66|42.65|1.000|33.28|33.22|0.998|
|10|44.91|44.94|1.001|35.18|35.28|1.003|
|11|48.08|48.07|1.000|37.66|37.63|0.999|
|12|51.34|51.35|1.000|40.06|39.99|0.998|
|13|54.84|54.86|1.000|42.73|42.78|1.001|
|14|57.99|58.04|1.001|45.26|45.25|1.000|
|15|61.07|61.06|1.000|47.81|47.83|1.000|
|16|64.66|64.71|1.001|51.13|51.12|1.000|
|17|66.84|66.75|0.999|52.98|53.04|1.001|
|18|69.43|69.47|1.001|55.40|55.40|1.000|
|19|71.48|71.52|1.001|57.11|57.04|0.999|
|20|70.73|70.77|1.001|56.50|56.46|0.999|
|21|70.73|70.63|0.999|56.54|56.56|1.000|
|22|70.77|70.72|0.999|56.64|56.59|0.999|
|23|70.74|70.82|1.001|56.63|56.61|1.000|
|24|70.59|70.62|1.000|56.52|56.58|1.001|
|25|70.84|70.80|0.999|56.70|56.78|1.001|
|26|70.88|70.65|0.997|56.74|56.69|0.999|
|27|70.85|70.80|0.999|56.70|56.81|1.002|
|28|70.41|70.83|1.006|56.73|56.75|1.000|
|29|70.91|70.87|0.999|56.79|56.82|1.001|
|30|70.91|70.87|0.999|56.85|56.83|1.000|
|31|70.80|70.83|1.000|56.76|56.84|1.001|
|32|72.28|72.28|1.000|58.01|58.08|1.001|

`h4096_e512_i512_k10`: hidden 4096, intermediate 512, 512 experts,
top-10, swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|16.76|16.85|1.005|15.62|15.74|1.008|
|2|21.61|21.63|1.001|19.86|19.75|0.994|
|3|25.98|25.95|0.999|23.86|23.90|1.002|
|4|31.92|31.67|0.992|28.77|28.71|0.998|
|5|36.09|35.99|0.997|32.70|32.73|1.001|
|6|41.12|41.09|0.999|37.21|37.18|0.999|
|7|45.69|45.75|1.001|41.33|41.53|1.005|
|8|49.99|50.07|1.002|45.35|45.41|1.001|
|9|55.21|55.44|1.004|49.78|50.14|1.007|
|10|59.45|59.65|1.003|53.58|53.82|1.004|
|11|64.65|64.54|0.998|58.37|58.38|1.000|
|12|68.46|68.43|1.000|62.01|62.05|1.001|
|13|73.50|73.59|1.001|66.67|66.79|1.002|
|14|78.02|77.86|0.998|70.72|70.60|0.998|
|15|82.66|82.55|0.999|74.97|74.76|0.997|
|16|86.75|86.98|1.003|78.60|78.67|1.001|
|17|91.78|91.55|0.997|83.23|83.02|0.997|
|18|96.00|96.10|1.001|86.95|87.19|1.003|
|19|100.63|100.60|1.000|91.55|91.33|0.998|
|20|105.28|105.36|1.001|95.48|95.56|1.001|
|21|110.17|110.34|1.002|99.89|100.23|1.003|
|22|114.59|114.29|0.997|104.10|103.96|0.999|
|23|118.80|118.78|1.000|107.95|107.91|1.000|
|24|123.05|123.36|1.003|111.83|112.37|1.005|
|25|128.19|128.28|1.001|116.89|116.70|0.998|
|26|132.89|132.84|1.000|120.93|120.88|1.000|
|27|137.04|137.28|1.002|124.72|124.84|1.001|
|28|141.39|141.48|1.001|128.70|128.80|1.001|
|29|145.76|146.00|1.002|132.79|133.00|1.002|
|30|150.16|150.23|1.000|136.75|137.02|1.002|
|31|154.69|154.61|0.999|141.31|141.13|0.999|
|32|159.02|158.85|0.999|145.12|144.74|0.997|

`h4096_e512_i256_k10`: hidden 4096, intermediate 256, 512 experts,
top-10, swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|14.45|14.43|0.999|13.57|13.55|0.999|
|2|16.65|16.68|1.002|15.45|15.54|1.006|
|3|19.64|19.63|0.999|18.09|18.13|1.002|
|4|22.94|22.87|0.997|20.93|20.99|1.003|
|5|25.24|25.15|0.996|23.19|23.28|1.004|
|6|27.33|27.26|0.997|25.20|25.16|0.998|
|7|30.12|30.11|1.000|27.60|27.53|0.997|
|8|33.07|32.87|0.994|30.25|30.27|1.001|
|9|35.47|35.42|0.999|32.51|32.51|1.000|
|10|37.91|37.95|1.001|34.68|34.76|1.002|
|11|40.38|40.37|1.000|37.12|37.07|0.999|
|12|42.81|42.96|1.004|39.56|39.71|1.004|
|13|45.36|45.50|1.003|41.98|42.12|1.003|
|14|47.90|47.95|1.001|44.16|44.22|1.001|
|15|50.48|50.41|0.999|46.64|46.58|0.999|
|16|52.59|52.70|1.002|48.69|48.69|1.000|
|17|55.32|55.13|0.997|51.22|51.08|0.997|
|18|57.80|57.70|0.998|53.44|53.53|1.002|
|19|60.31|60.45|1.002|56.14|56.19|1.001|
|20|62.72|62.69|1.000|58.42|58.24|0.997|
|21|65.26|65.27|1.000|60.71|60.80|1.001|
|22|67.70|67.91|1.003|63.14|63.31|1.003|
|23|70.46|70.39|0.999|65.64|65.54|0.998|
|24|72.81|72.78|1.000|67.83|67.83|1.000|
|25|75.18|75.32|1.002|69.78|70.42|1.009|
|26|77.76|77.72|0.999|72.65|72.55|0.999|
|27|80.35|80.30|0.999|75.26|75.05|0.997|
|28|82.79|82.56|0.997|77.42|77.25|0.998|
|29|85.29|85.11|0.998|79.67|79.49|0.998|
|30|87.75|87.71|1.000|81.85|81.98|1.002|
|31|90.35|90.21|0.998|84.65|84.42|0.997|
|32|92.83|92.48|0.996|86.88|86.50|0.996|

`h3072_e256_i768_k8`: hidden 3072, intermediate 768, 256 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|16.36|16.20|0.990|14.72|14.68|0.997|
|2|21.61|21.59|0.999|19.67|19.64|0.998|
|**3**|25.18|25.06|0.995|22.48|22.12|0.984|
|4|28.71|28.80|1.003|25.85|25.82|0.999|
|5|34.09|34.09|1.000|30.25|30.17|0.997|
|6|37.94|37.85|0.998|33.61|33.54|0.998|
|7|42.00|42.05|1.001|37.51|37.48|0.999|
|8|46.16|46.18|1.000|40.94|41.00|1.001|
|9|50.31|50.45|1.003|45.11|45.11|1.000|
|10|54.67|54.53|0.997|48.73|48.75|1.000|
|11|58.47|58.33|0.998|52.23|52.25|1.000|
|12|62.30|62.24|0.999|55.80|55.77|0.999|
|13|66.50|66.52|1.000|59.41|59.50|1.002|
|14|70.38|70.36|1.000|63.09|63.12|1.000|
|15|74.40|74.50|1.001|67.06|67.04|1.000|
|16|74.46|74.45|1.000|66.83|66.78|0.999|
|17|74.74|74.66|0.999|67.05|66.98|0.999|
|18|74.63|74.60|1.000|66.92|67.05|1.002|
|19|74.74|74.75|1.000|67.09|66.94|0.998|
|20|74.62|74.59|1.000|66.90|66.92|1.000|
|21|74.71|74.77|1.001|67.03|67.13|1.001|
|22|74.69|74.66|1.000|67.02|67.17|1.002|
|23|74.76|74.70|0.999|67.12|66.95|0.997|
|24|74.66|74.72|1.001|66.92|67.04|1.002|
|25|74.85|74.79|0.999|67.13|67.28|1.002|
|26|74.91|74.80|0.999|67.21|67.19|1.000|
|27|74.92|74.76|0.998|67.20|67.17|1.000|
|28|74.91|74.78|0.998|67.15|67.10|0.999|
|29|75.01|74.87|0.998|67.29|67.27|1.000|
|30|74.92|74.91|1.000|67.25|67.18|0.999|
|31|74.94|75.03|1.001|67.23|67.35|1.002|
|32|74.93|74.99|1.001|67.16|67.15|1.000|

`h3072_e256_i384_k8`: hidden 3072, intermediate 384, 256 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|13.76|13.76|1.000|13.01|12.91|0.992|
|2|16.52|16.60|1.005|15.27|15.32|1.003|
|3|19.10|19.11|1.001|17.33|17.34|1.001|
|4|21.28|21.20|0.996|19.35|19.36|1.001|
|5|23.58|23.53|0.998|21.48|21.56|1.004|
|6|25.92|25.92|1.000|23.37|23.27|0.996|
|7|27.73|27.50|0.992|24.64|24.74|1.004|
|8|29.93|29.97|1.001|27.06|27.09|1.001|
|9|32.72|32.73|1.000|29.42|29.47|1.002|
|10|34.49|34.48|1.000|31.17|31.10|0.998|
|11|36.56|36.50|0.998|32.92|33.01|1.003|
|12|38.41|38.40|1.000|34.80|34.76|0.999|
|13|40.55|40.61|1.001|36.80|36.79|1.000|
|14|42.58|42.55|0.999|38.70|38.64|0.998|
|15|44.39|44.43|1.001|40.53|40.47|0.999|
|16|44.45|44.36|0.998|40.45|40.48|1.001|
|17|44.47|44.48|1.000|40.62|40.56|0.999|
|18|44.48|44.60|1.003|40.63|40.61|1.000|
|19|44.60|44.56|0.999|40.67|40.68|1.000|
|20|44.59|44.59|1.000|40.66|40.58|0.998|
|21|44.52|44.57|1.001|40.61|40.62|1.000|
|22|44.63|44.65|1.000|40.68|40.74|1.001|
|23|44.63|44.59|0.999|40.69|40.76|1.002|
|24|44.52|44.56|1.001|40.76|40.71|0.999|
|25|44.85|44.80|0.999|40.86|40.83|0.999|
|26|44.86|44.76|0.998|40.86|40.92|1.001|
|27|44.78|44.84|1.001|40.87|40.89|1.000|
|28|44.84|44.81|0.999|40.92|40.92|1.000|
|29|44.82|44.83|1.000|40.89|40.97|1.002|
|30|44.91|44.91|1.000|41.00|40.95|0.999|
|31|44.95|44.89|0.999|41.01|40.96|0.999|
|32|44.97|44.94|0.999|40.99|40.92|0.998|

`e512_i512_k10`: hidden 2048, intermediate 512, 512 experts, top-10,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|13.75|13.74|0.999|12.22|12.39|1.014|
|2|17.05|17.13|1.005|14.88|14.84|0.997|
|3|20.03|19.96|0.997|17.14|17.09|0.997|
|4|23.21|23.40|1.008|19.06|19.24|1.009|
|5|25.23|25.14|0.996|20.53|20.44|0.996|
|6|28.75|28.76|1.000|23.13|23.20|1.003|
|7|32.69|32.70|1.000|25.79|25.84|1.002|
|8|35.48|35.56|1.002|27.96|28.19|1.008|
|9|38.40|38.42|1.001|30.12|30.07|0.998|
|10|41.02|41.05|1.001|32.48|32.48|1.000|
|11|43.99|44.03|1.001|34.64|34.67|1.001|
|12|46.60|46.62|1.000|36.85|36.95|1.003|
|13|49.49|49.53|1.001|39.14|39.13|1.000|
|14|52.12|52.17|1.001|41.29|41.30|1.000|
|15|55.06|55.04|1.000|43.82|43.86|1.001|
|16|57.58|57.49|0.998|46.02|45.91|0.998|
|17|60.18|60.17|1.000|48.14|48.17|1.001|
|18|62.84|62.72|0.998|50.40|50.47|1.001|
|19|65.28|65.24|0.999|52.51|52.68|1.003|
|20|67.70|67.72|1.000|54.93|54.98|1.001|
|21|69.99|70.00|1.000|57.26|57.25|1.000|
|22|72.30|72.28|1.000|59.44|59.35|0.998|
|23|74.66|74.64|1.000|61.67|61.63|0.999|
|24|77.03|77.07|1.001|63.78|63.77|1.000|
|25|79.56|79.59|1.000|66.13|66.26|1.002|
|26|81.98|82.00|1.000|68.37|68.40|1.000|
|27|84.96|84.96|1.000|71.13|71.18|1.001|
|28|87.42|87.34|0.999|73.23|73.29|1.001|
|29|90.04|90.02|1.000|75.51|75.54|1.000|
|30|93.62|93.62|1.000|78.57|78.50|0.999|
|31|95.89|96.10|1.002|80.65|80.75|1.001|
|32|97.44|97.57|1.001|82.20|82.29|1.001|

`e60_i1536_k4`: hidden 2048, intermediate 1536, 60 experts, top-4,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|13.74|13.68|0.996|12.48|12.36|0.990|
|2|16.94|16.92|0.999|15.10|15.10|1.000|
|3|20.44|20.36|0.996|17.72|17.56|0.991|
|4|23.25|23.26|1.000|19.81|19.91|1.005|
|5|26.74|26.71|0.999|21.78|21.86|1.004|
|6|28.84|28.84|1.000|23.06|23.07|1.000|
|7|31.67|31.77|1.003|25.00|25.04|1.002|
|8|34.35|34.35|1.000|27.29|27.51|1.008|
|9|36.78|36.81|1.001|28.70|28.71|1.000|
|10|39.43|39.47|1.001|30.77|30.86|1.003|
|11|41.59|41.53|0.999|32.24|32.22|0.999|
|12|42.20|42.21|1.000|33.25|33.29|1.001|
|13|44.06|44.02|0.999|34.58|34.60|1.001|
|14|45.29|45.31|1.000|35.67|35.42|0.993|
|15|47.68|47.62|0.999|37.47|37.45|0.999|
|16|49.00|49.09|1.002|38.37|38.22|0.996|
|17|51.49|51.55|1.001|40.40|40.36|0.999|
|18|53.50|53.47|0.999|41.99|41.97|1.000|
|19|55.24|55.26|1.000|43.33|43.43|1.002|
|20|56.79|56.78|1.000|44.71|44.78|1.002|
|21|58.45|58.46|1.000|46.13|46.16|1.001|
|22|60.35|60.33|1.000|47.64|47.54|0.998|
|23|61.91|61.86|0.999|48.99|48.96|0.999|
|24|63.50|63.53|1.000|50.46|50.50|1.001|
|25|65.63|65.60|1.000|52.04|52.04|1.000|
|26|67.37|67.32|0.999|53.57|53.55|1.000|
|27|67.36|67.30|0.999|53.53|53.57|1.001|
|28|67.31|67.31|1.000|53.64|53.59|0.999|
|29|67.32|67.32|1.000|53.58|53.52|0.999|
|30|67.36|67.35|1.000|53.66|53.64|1.000|
|31|67.34|67.24|0.999|53.58|53.58|1.000|
|32|66.78|66.78|1.000|53.04|52.96|0.998|

`e192_i1536_k4_silu`: hidden 6144, intermediate 1536, 192 experts,
top-4, silu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|19.45|19.53|1.004|17.16|17.30|1.008|
|2|25.31|25.36|1.002|20.54|20.41|0.994|
|3|30.67|30.76|1.003|24.67|24.79|1.005|
|4|38.00|38.31|1.008|29.86|29.97|1.004|
|5|42.66|42.41|0.994|33.24|33.03|0.994|
|6|47.61|47.51|0.998|37.16|37.20|1.001|
|7|54.20|54.34|1.003|42.16|42.18|1.000|
|8|59.07|59.10|1.001|46.07|45.84|0.995|
|9|63.53|63.58|1.001|49.75|49.65|0.998|
|10|68.71|68.71|1.000|54.96|54.80|0.997|
|11|72.78|72.84|1.001|58.61|58.61|1.000|
|12|77.28|77.25|1.000|62.79|62.63|0.997|
|13|82.08|82.12|1.000|67.52|67.80|1.004|
|14|86.59|86.52|0.999|71.70|72.15|1.006|
|15|90.95|90.97|1.000|75.84|75.94|1.001|
|16|95.49|95.59|1.001|80.71|80.57|0.998|
|17|99.78|99.86|1.001|84.96|84.91|0.999|
|18|104.12|104.19|1.001|88.89|89.24|1.004|
|19|108.96|109.06|1.001|93.57|93.59|1.000|
|20|113.05|113.08|1.000|97.81|97.92|1.001|
|21|117.58|117.34|0.998|102.21|101.99|0.998|
|22|122.05|121.82|0.998|106.53|106.36|0.998|
|23|126.70|126.74|1.000|110.94|110.78|0.999|
|24|130.77|130.66|0.999|114.96|114.80|0.999|
|25|135.39|135.46|1.001|119.34|119.39|1.000|
|26|139.77|140.15|1.003|123.70|123.87|1.001|
|27|144.44|144.19|0.998|127.95|127.68|0.998|
|28|148.78|148.82|1.000|132.26|132.40|1.001|
|29|153.21|153.41|1.001|136.64|136.86|1.002|
|30|157.35|157.46|1.001|140.72|140.85|1.001|
|31|161.71|161.83|1.001|144.90|144.98|1.001|
|32|165.97|166.29|1.002|149.37|149.63|1.002|

`e384_i768_k4`: hidden 2560, intermediate 768, 384 experts, top-4,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|11.92|11.94|1.002|11.07|10.98|0.992|
|2|14.24|14.13|0.992|12.71|12.63|0.994|
|3|16.34|16.33|0.999|14.61|14.61|1.000|
|4|18.84|18.85|1.001|16.79|16.87|1.005|
|5|20.64|20.63|1.000|17.67|17.66|0.999|
|6|22.62|22.60|0.999|18.93|18.81|0.994|
|7|24.98|25.14|1.006|21.16|21.08|0.996|
|8|27.11|27.11|1.000|22.10|22.00|0.995|
|9|28.42|28.51|1.003|23.13|22.98|0.994|
|10|31.00|30.74|0.992|25.49|25.45|0.998|
|11|32.34|32.25|0.997|26.45|26.22|0.991|
|12|34.05|33.80|0.993|27.27|27.15|0.996|
|13|35.85|35.69|0.996|28.84|28.79|0.998|
|14|37.50|37.52|1.001|30.02|30.00|0.999|
|15|39.01|39.02|1.000|31.00|30.89|0.996|
|16|40.75|40.62|0.997|32.33|32.28|0.998|
|17|42.36|42.42|1.001|33.76|33.82|1.002|
|18|43.99|44.00|1.000|34.79|35.01|1.006|
|19|45.67|45.79|1.003|36.18|36.28|1.003|
|20|47.31|47.31|1.000|37.53|37.44|0.998|
|21|49.06|48.99|0.999|38.88|38.84|0.999|
|22|50.94|50.91|0.999|40.35|40.29|0.999|
|23|52.55|52.60|1.001|41.70|41.84|1.003|
|24|54.41|54.34|0.999|42.84|42.86|1.000|
|25|56.10|56.00|0.998|44.48|44.59|1.002|
|26|57.85|57.73|0.998|45.84|45.84|1.000|
|27|59.67|59.50|0.997|47.13|47.25|1.003|
|28|61.15|61.12|1.000|48.53|48.51|1.000|
|29|62.76|62.73|1.000|50.07|49.94|0.997|
|30|64.04|64.18|1.002|51.21|51.20|1.000|
|31|65.70|65.74|1.001|52.58|52.62|1.001|
|32|67.19|67.12|0.999|54.05|54.08|1.001|

`e128_i1536_k8`: hidden 4096, intermediate 1536, 128 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|24.77|24.65|0.995|20.53|20.46|0.997|
|2|38.43|38.34|0.998|30.06|29.99|0.998|
|3|52.90|52.88|1.000|41.45|41.44|1.000|
|4|63.74|63.60|0.998|50.38|50.30|0.998|
|5|75.29|75.20|0.999|60.90|60.90|1.000|
|6|86.19|86.35|1.002|71.10|71.03|0.999|
|7|96.69|96.68|1.000|81.67|81.58|0.999|
|**8**|107.28|106.67|0.994|91.44|91.01|0.995|
|9|117.63|117.88|1.002|101.72|101.86|1.001|
|10|127.92|127.91|1.000|111.56|111.62|1.001|
|11|138.16|137.92|0.998|121.52|121.40|0.999|
|12|147.27|147.20|1.000|130.46|130.42|1.000|
|13|157.03|157.04|1.000|140.22|140.25|1.000|
|14|167.06|166.85|0.999|150.11|149.94|0.999|
|15|176.70|176.73|1.000|159.86|159.86|1.000|
|16|186.44|186.39|1.000|169.57|169.47|0.999|
|17|193.95|194.11|1.001|176.93|176.99|1.000|
|18|200.99|200.93|1.000|183.97|183.75|0.999|
|19|207.78|208.03|1.001|190.83|190.86|1.000|
|20|208.12|208.04|1.000|191.02|190.86|0.999|
|21|208.09|208.08|1.000|191.09|190.99|0.999|
|22|208.13|208.14|1.000|191.24|191.09|0.999|
|23|208.11|208.22|1.001|191.08|191.18|1.001|
|24|208.16|208.15|1.000|191.34|191.21|0.999|
|25|208.91|208.83|1.000|192.23|192.14|1.000|
|26|208.82|208.73|1.000|192.09|192.14|1.000|
|27|208.87|208.91|1.000|192.21|192.26|1.000|
|28|208.99|208.80|0.999|192.33|192.33|1.000|
|29|208.89|209.07|1.001|192.25|192.37|1.001|
|30|209.05|209.07|1.000|192.55|192.43|0.999|
|31|209.15|209.19|1.000|192.49|192.57|1.000|
|32|209.11|209.09|1.000|192.49|192.59|1.001|

`e256_i512_k8`: hidden 2048, intermediate 512, 256 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|12.91|12.96|1.004|11.62|11.62|1.000|
|2|15.44|15.38|0.996|13.91|13.90|0.999|
|3|18.33|18.27|0.997|15.97|15.93|0.997|
|4|19.55|19.46|0.995|16.57|16.57|1.000|
|5|23.51|23.48|0.999|19.52|19.51|0.999|
|6|25.07|24.97|0.996|20.40|20.37|0.999|
|7|27.64|27.74|1.004|22.00|22.22|1.010|
|8|29.53|29.54|1.000|23.27|23.27|1.000|
|9|32.59|32.63|1.001|25.36|25.40|1.002|
|10|34.64|34.75|1.003|27.22|27.40|1.007|
|11|37.02|36.95|0.998|28.82|28.85|1.001|
|12|39.07|39.11|1.001|30.72|30.68|0.999|
|13|41.30|41.33|1.001|32.28|32.30|1.001|
|14|43.34|43.42|1.002|34.06|34.05|1.000|
|15|45.41|45.52|1.002|35.85|35.85|1.000|
|16|45.33|45.36|1.001|35.79|35.88|1.003|
|17|45.44|45.38|0.999|35.90|35.84|0.998|
|18|45.42|45.48|1.001|35.86|35.83|0.999|
|19|45.39|45.50|1.002|35.90|35.93|1.001|
|20|45.43|45.44|1.000|35.95|35.93|0.999|
|21|45.59|45.54|0.999|35.95|35.90|0.999|
|22|45.56|45.59|1.001|35.97|36.05|1.002|
|23|45.54|45.56|1.000|36.01|35.91|0.997|
|24|45.52|45.51|1.000|35.95|35.92|0.999|
|25|45.53|45.55|1.000|35.91|35.99|1.002|
|26|45.59|45.56|0.999|35.98|35.97|1.000|
|27|45.53|45.53|1.000|36.11|36.04|0.998|
|28|45.58|45.49|0.998|36.14|36.05|0.998|
|29|45.63|45.69|1.001|36.10|36.25|1.004|
|30|45.54|45.69|1.003|36.04|36.11|1.002|
|31|45.59|45.60|1.000|36.10|36.05|0.999|
|32|45.56|45.56|1.000|36.00|36.20|1.006|

`e512_i1024_k10`: hidden 4096, intermediate 1024, 512 experts, top-10,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|23.99|23.90|0.996|20.25|20.18|0.997|
|2|34.29|34.31|1.001|27.27|27.27|1.000|
|3|44.98|44.97|1.000|35.43|35.30|0.996|
|4|55.64|55.56|0.999|43.46|43.63|1.004|
|5|65.65|65.60|0.999|52.28|52.31|1.001|
|6|75.43|75.48|1.001|60.93|60.96|1.000|
|7|84.61|84.72|1.001|69.79|69.86|1.001|
|8|94.19|94.15|1.000|78.90|78.82|0.999|
|9|103.61|103.49|0.999|87.48|87.43|0.999|
|10|112.45|112.51|1.001|96.01|96.08|1.001|
|11|122.18|122.27|1.001|105.44|105.54|1.001|
|12|130.80|130.61|0.999|113.85|113.76|0.999|
|13|139.03|139.17|1.001|122.24|122.31|1.001|
|14|147.71|147.63|0.999|130.66|130.57|0.999|
|15|156.21|156.08|0.999|139.12|139.03|0.999|
|16|164.62|164.55|1.000|147.30|147.38|1.001|
|17|173.29|173.46|1.001|156.10|156.20|1.001|
|18|181.74|181.62|0.999|164.42|164.40|1.000|
|19|189.93|190.20|1.001|172.75|172.89|1.001|
|20|198.39|198.47|1.000|181.13|181.07|1.000|
|21|206.89|206.89|1.000|189.55|189.55|1.000|
|22|215.18|215.39|1.001|197.87|197.92|1.000|
|23|223.60|223.54|1.000|206.19|206.18|1.000|
|24|232.15|231.92|0.999|214.78|214.54|0.999|
|25|240.79|240.75|1.000|223.44|223.48|1.000|
|26|249.76|249.53|0.999|232.30|232.11|0.999|
|27|257.83|258.16|1.001|240.32|240.63|1.001|
|28|266.54|266.34|0.999|249.03|248.90|0.999|
|29|274.51|274.72|1.001|257.36|257.37|1.000|
|30|283.00|282.95|1.000|265.53|265.50|1.000|
|31|291.51|291.34|0.999|274.04|273.88|0.999|
|32|299.20|299.40|1.001|281.85|282.07|1.001|

`e256_i1536_k8`: hidden 3072, intermediate 1536, 256 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|21.74|21.78|1.002|18.51|18.39|0.994|
|2|32.69|32.83|1.004|26.01|26.11|1.004|
|3|42.73|42.62|0.997|33.59|33.51|0.998|
|4|52.06|52.22|1.003|40.96|40.88|0.998|
|5|61.81|61.82|1.000|48.32|48.33|1.000|
|6|70.12|70.08|0.999|56.07|56.15|1.001|
|7|78.14|78.16|1.000|63.72|63.59|0.998|
|8|86.33|86.27|0.999|71.35|71.20|0.998|
|9|94.00|94.15|1.002|78.88|78.82|0.999|
|10|101.79|101.70|0.999|86.41|86.32|0.999|
|11|109.72|109.78|1.001|93.91|93.86|0.999|
|12|117.41|117.41|1.000|101.41|101.35|0.999|
|13|125.18|125.29|1.001|108.97|108.92|1.000|
|14|132.74|132.75|1.000|116.30|116.28|1.000|
|15|140.29|140.22|1.000|123.86|123.75|0.999|
|16|140.64|140.55|0.999|123.68|123.54|0.999|
|17|141.07|141.11|1.000|124.00|123.98|1.000|
|18|141.06|141.06|1.000|123.94|124.00|1.000|
|19|141.19|141.22|1.000|124.08|124.11|1.000|
|20|141.24|141.25|1.000|124.16|124.16|1.000|
|21|141.32|141.26|1.000|124.24|124.26|1.000|
|22|141.31|141.36|1.000|124.27|124.26|1.000|
|23|141.27|141.24|1.000|124.27|124.24|1.000|
|24|141.25|141.31|1.000|124.34|124.31|1.000|
|25|141.76|141.81|1.000|125.09|124.97|0.999|
|26|141.84|141.84|1.000|125.05|125.01|1.000|
|27|141.25|141.21|1.000|124.40|124.39|1.000|
|28|141.23|141.29|1.000|124.50|124.54|1.000|
|29|141.82|141.79|1.000|125.14|125.06|0.999|
|30|141.31|141.28|1.000|124.57|124.55|1.000|
|31|141.88|142.01|1.001|125.06|125.17|1.001|
|32|141.36|141.31|1.000|124.59|124.64|1.000|

`e128_i3072_k4_swiglu_oa`: hidden 6144, intermediate 3072, 128 experts,
top-4, swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|35.43|35.57|1.004|28.13|28.27|1.005|
|2|51.60|51.69|1.002|39.72|39.69|0.999|
|3|67.36|67.48|1.002|52.71|52.88|1.003|
|4|80.87|80.87|1.000|65.85|65.75|0.998|
|5|93.53|93.48|0.999|77.70|77.59|0.999|
|6|107.37|107.13|0.998|90.99|90.45|0.994|
|7|120.29|120.54|1.002|103.15|103.60|1.004|
|8|132.89|132.94|1.000|115.86|115.93|1.001|
|9|146.20|146.07|0.999|128.46|128.47|1.000|
|10|159.01|159.06|1.000|141.41|141.42|1.000|
|11|171.51|171.58|1.000|154.18|154.16|1.000|
|12|184.53|184.52|1.000|166.95|166.85|0.999|
|13|196.55|196.66|1.001|178.85|178.96|1.001|
|14|208.85|209.03|1.001|191.48|191.47|1.000|
|15|221.49|221.61|1.001|203.91|203.85|1.000|
|16|234.38|234.22|0.999|216.42|216.31|0.999|
|17|248.51|248.52|1.000|230.95|231.08|1.001|
|18|261.10|260.99|1.000|243.47|243.51|1.000|
|19|273.36|273.36|1.000|256.02|256.03|1.000|
|20|281.66|281.43|0.999|264.32|264.28|1.000|
|21|289.94|289.85|1.000|272.68|272.82|1.001|
|22|298.22|298.35|1.000|281.02|281.04|1.000|
|23|306.53|306.53|1.000|289.47|289.50|1.000|
|24|315.07|314.88|0.999|297.97|297.85|1.000|
|25|323.61|323.53|1.000|306.53|306.66|1.000|
|26|332.35|332.03|0.999|315.01|315.17|1.001|
|27|340.44|340.35|1.000|323.28|323.35|1.000|
|28|348.74|348.54|0.999|331.72|331.81|1.000|
|29|357.00|356.98|1.000|339.91|340.18|1.001|
|30|365.48|365.25|0.999|348.48|348.38|1.000|
|31|373.83|373.88|1.000|356.78|356.96|1.001|
|32|382.02|382.00|1.000|365.07|365.03|1.000|

`e256_i2048_k6_clamp10`: hidden 4096, intermediate 2048, 256 experts,
top-6, swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|24.41|24.41|1.000|20.00|19.91|0.996|
|2|37.81|37.83|1.001|29.50|29.39|0.996|
|3|49.98|50.06|1.002|38.59|38.60|1.000|
|4|61.26|61.33|1.001|48.22|48.24|1.000|
|5|72.45|72.48|1.000|58.15|58.32|1.003|
|6|82.53|82.53|1.000|67.46|67.55|1.001|
|7|92.76|92.80|1.000|77.55|77.54|1.000|
|8|104.86|104.87|1.000|89.19|89.31|1.001|
|9|114.38|114.39|1.000|98.44|98.34|0.999|
|10|124.12|124.02|0.999|107.58|107.65|1.001|
|11|133.86|133.92|1.000|117.13|117.16|1.000|
|12|142.97|142.99|1.000|126.26|126.28|1.000|
|13|152.90|152.93|1.000|135.96|135.97|1.000|
|14|162.04|162.05|1.000|144.72|144.74|1.000|
|15|171.66|171.60|1.000|154.29|154.26|1.000|
|16|171.67|171.66|1.000|154.45|154.46|1.000|
|17|172.34|172.31|1.000|155.01|154.97|1.000|
|18|172.41|172.35|1.000|155.09|155.12|1.000|
|19|172.45|172.37|1.000|155.26|155.25|1.000|
|20|172.36|172.45|1.001|155.21|155.22|1.000|
|21|172.56|172.50|1.000|155.34|155.17|0.999|
|22|172.65|172.56|0.999|155.30|155.36|1.000|
|23|172.74|172.73|1.000|155.72|155.75|1.000|
|24|172.47|172.61|1.001|155.31|155.27|1.000|
|25|173.44|173.60|1.001|156.21|156.26|1.000|
|26|173.66|173.55|0.999|156.30|156.21|0.999|
|27|173.66|173.79|1.001|156.35|156.43|1.001|
|28|173.72|173.67|1.000|156.32|156.52|1.001|
|29|173.78|173.72|1.000|156.52|156.44|0.999|
|30|174.14|173.95|0.999|156.91|156.79|0.999|
|31|173.83|173.83|1.000|156.88|157.02|1.001|
|32|174.00|173.94|1.000|157.04|157.10|1.000|

`e896_i3072_k16_situ`: hidden 3584, intermediate 3072, 896 experts,
top-16, situ

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|70.41|70.54|1.002|59.45|59.41|0.999|
|2|113.40|113.78|1.003|102.63|102.58|1.000|
|3|151.64|151.79|1.001|142.53|142.62|1.001|
|4|193.23|193.50|1.001|185.67|185.17|0.997|
|5|232.00|232.03|1.000|224.71|224.28|0.998|
|6|272.90|272.90|1.000|265.47|265.39|1.000|
|7|313.41|313.63|1.001|306.60|306.61|1.000|
|8|354.22|354.09|1.000|347.23|347.25|1.000|
|9|394.85|394.83|1.000|388.19|387.69|0.999|
|10|435.56|435.71|1.000|428.72|428.80|1.000|
|11|478.49|478.71|1.000|471.90|471.79|1.000|
|12|519.40|519.45|1.000|512.59|512.61|1.000|
|13|560.43|560.21|1.000|553.59|553.46|1.000|
|14|600.82|600.95|1.000|594.05|594.45|1.001|
|15|639.98|639.77|1.000|633.89|633.63|1.000|
|16|681.92|682.11|1.000|675.50|675.57|1.000|
|17|722.45|722.27|1.000|716.39|716.16|1.000|
|18|762.79|762.96|1.000|756.88|757.08|1.000|
|19|803.48|803.75|1.000|797.26|797.40|1.000|
|20|844.01|843.82|1.000|837.87|837.90|1.000|
|21|884.62|884.69|1.000|878.65|878.28|1.000|
|22|925.53|925.42|1.000|919.53|919.52|1.000|
|23|965.97|965.74|1.000|959.81|959.57|1.000|
|24|1007.14|1006.59|0.999|1000.80|1000.32|1.000|
|25|1047.28|1047.65|1.000|1040.83|1041.54|1.001|
|26|1088.01|1087.90|1.000|1081.66|1081.43|1.000|
|27|1128.42|1128.60|1.000|1122.24|1121.99|1.000|
|28|1169.10|1169.05|1.000|1162.67|1162.70|1.000|
|29|1209.12|1208.97|1.000|1202.86|1202.56|1.000|
|30|1250.26|1249.05|0.999|1244.25|1243.52|0.999|
|31|1290.57|1290.85|1.000|1284.33|1284.28|1.000|
|32|1330.71|1331.37|1.000|1324.46|1325.17|1.001|

Co-authored-by: Avery Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [7832229](https://github.com/flashinfer-ai/flashinfer/commit/7832229f4a7336d480d1221c04dfb49be7265903)

- **作者**: eigen
- **时间**: 2026-10-30T23:08:07Z
- **提交信息**: perf(cake_deepgemm_mega_mhc): speed up the sm_107a FP8 group-128 raw-scale programs (#8047)

`flashinfer.mega_mhc` (`prepare_mega_mhc`) runs the fused
manifold-constrained hyper-connection (mHC) inference step. FlashInfer
main ships 36 programs for it:

- 14 hidden-5120 FP8-E4M3-output programs on sm_100a and sm_103a.
- For hidden 4096, five programs on each of sm_107a, sm_100a and
sm_103a: BF16 output, its tailpipe twin, its weight-staging tailpipe
twin, FP8 group-128 output and NVFP4 output.
- Four sm_107a-only tailpipe and weight-staging tailpipe forms of the
FP8 group-128 and NVFP4 variants.
- Three sm_107a-only FP8 group-128 UE8M0-scale-mode programs (plain,
tailpipe and weight-staging tailpipe).

This PR changes two of the existing sm_107a programs and adds one
sm_107a program, so main will ship 37. All three serve **FP8 group-128
output in raw scale mode** (`sf_layout="fp8_group128"`,
`fp8_sf_ue8m0=False`):

- **Tailpipe program (changed).** It serves T = 385–832 and T =
1281–3328 on 208 SMs, and T = 385–832 and T = 1345–3456 on 216 SMs. In
the tables below, that covers T = 512 and T = 2048.
- **Weight-staging tailpipe program (changed).** It serves T ≥ 3329 on
208 SMs and T ≥ 3457 on 216 SMs. In the tables below, that covers T =
4096 and T = 8192.
- **Fast-division form of the plain FP8 group-128 program (new).** This
is a second form of the plain program that uses the fast store. The PR
also changes the loader's routes and `select_program`. The new form
serves raw-mode T = 1–128, raw-mode T ≥ 1024 up to the plain program's
limit (1280 on 208 SMs, 1344 on 216 SMs), and every deterministic launch
of the plain program. In the tables below, that covers T = 1–128 and T =
1024.

The plain FP8 group-128 program is unchanged and keeps T = 129–384 and T
= 833–1023. The T = 256 row therefore runs the same unchanged plain
program on both sides.

In these three programs, the FP8 store divides each value by its group
scale using one reciprocal per lane (`rcp.approx` plus one Newton step)
and an FMA remainder correction. A warp with any scale outside [2^-60,
2^60) keeps IEEE division. Outputs (E4M3 codes and scales) are bitwise
identical to main.

The baseline is the previous Cake version of the kernel, which is what
FlashInfer main dispatches today. A is the program main dispatches, and
B is the program this PR dispatches. On the fast-division rows, A is the
plain FP8 group-128 program. Speedup = A / B. Both sides run through
FlashInfer's loader on the same GPU with the same inputs in one process.
Both use programmatic dependent launch, as main already does. The tables
show medians.

- FP8 group-128 fast-division form, T = 1–128 and T = 1024: 1.030–1.080×
on the 208-SM GPU, 1.031–1.077× on the 216-SM GPU.
- Tailpipe, T = 512 and T = 2048: 1.023× and 1.043× on the 208-SM GPU,
1.022× and 1.049× on the 216-SM GPU.
- Weight-staging tailpipe, T = 4096 and T = 8192: 1.047× and 1.023× on
the 208-SM GPU, 1.044× and 1.022× on the 216-SM GPU.
- Unchanged plain program, T = 256: 1.000× on the 208-SM GPU, 0.997× on
the 216-SM GPU.

**FP8 group-128 output, raw scale mode, hidden 4096. NVIDIA R200
(sm_107a), 208 SMs, driver 615.71.10, CUDA 13.4 (nvcc 13.4.92), SM clock
2324–2364 MHz.**

| T (tokens) | Program dispatched by this PR | Splits | Previous
program, µs (A) | This PR, µs (B) | Speedup (A / B) |
|---:|:--|---:|---:|---:|---:|
| 1 | FP8 group-128 (fast-division form) | 64 | 10.016 | 9.544 | 1.049×
|
| 4 | FP8 group-128 (fast-division form) | 64 | 10.160 | 9.664 | 1.051×
|
| 8 | FP8 group-128 (fast-division form) | 64 | 10.272 | 9.760 | 1.052×
|
| 16 | FP8 group-128 (fast-division form) | 64 | 9.792 | 9.472 | 1.034×
|
| 32 | FP8 group-128 (fast-division form) | 64 | 9.888 | 9.600 | 1.030×
|
| 64 | FP8 group-128 (fast-division form) | 64 | 10.400 | 10.000 |
1.040× |
| 128 | FP8 group-128 (fast-division form) | 64 | 10.960 | 10.600 |
1.034× |
| 256 | FP8 group-128 | 32 | 12.320 | 12.320 | 1.000× |
| 512 | tailpipe | 22 | 14.336 | 14.017 | 1.023× |
| 1024 | FP8 group-128 (fast-division form) | 13 | 21.728 | 20.112 |
1.080× |
| 2048 | tailpipe | 13 | 31.672 | 30.368 | 1.043× |
| 4096 | tailpipe (weight staged) | 16 | 61.104 | 58.336 | 1.047× |
| 8192 | tailpipe (weight staged) | 8 | 117.504 | 114.912 | 1.023× |

**FP8 group-128 output, raw scale mode, hidden 4096. NVIDIA R200
(sm_107a), 216 SMs, driver 615.71.10, CUDA 13.4 (nvcc 13.4.92), SM clock
2384–2413 MHz.**

| T (tokens) | Program dispatched by this PR | Splits | Previous
program, µs (A) | This PR, µs (B) | Speedup (A / B) |
|---:|:--|---:|---:|---:|---:|
| 1 | FP8 group-128 (fast-division form) | 64 | 9.841 | 9.408 | 1.046× |
| 4 | FP8 group-128 (fast-division form) | 64 | 9.856 | 9.344 | 1.055× |
| 8 | FP8 group-128 (fast-division form) | 64 | 10.088 | 9.624 | 1.048×
|
| 16 | FP8 group-128 (fast-division form) | 64 | 9.600 | 9.312 | 1.031×
|
| 32 | FP8 group-128 (fast-division form) | 64 | 9.760 | 9.440 | 1.034×
|
| 64 | FP8 group-128 (fast-division form) | 64 | 10.048 | 9.696 | 1.036×
|
| 128 | FP8 group-128 (fast-division form) | 64 | 10.720 | 10.368 |
1.034× |
| 256 | FP8 group-128 | 32 | 12.064 | 12.096 | 0.997× |
| 512 | tailpipe | 22 | 14.000 | 13.696 | 1.022× |
| 1024 | FP8 group-128 (fast-division form) | 13 | 20.848 | 19.352 |
1.077× |
| 2048 | tailpipe | 13 | 30.544 | 29.120 | 1.049× |
| 4096 | tailpipe (weight staged) | 16 | 58.328 | 55.872 | 1.044× |
| 8192 | tailpipe (weight staged) | 8 | 114.840 | 112.400 | 1.022× |

The kernel's other Cake variants (BF16 output, NVFP4 output, the FP8
group-128 UE8M0 scale mode, the hidden-5120 programs and all sm_100a and
sm_103a programs) compile to the same machine code as on main, and the
family ships on sm_107a, sm_100a and sm_103a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added support for an optimized FP8 processing path on compatible
hardware for hidden size 4096. The application selects the path based on
input size and deterministic mode, while retaining existing processing
paths for other configurations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery Huang <averyh@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [eaa5494](https://github.com/flashinfer-ai/flashinfer/commit/eaa549454984e19e5da4686ba92ef5e65dc1ddd5)

- **作者**: eigen
- **时间**: 2026-10-30T23:07:55Z
- **提交信息**: refactor(cake_moe_grouped_det_gemm): deterministic names for the MoE grouped GEMM auto grad package (#8043)

Cake's ragged BF16 MoE grouped GEMM training kernel runs over E groups
of rows given by device offsets. It has four variants: the forward pass
Y = X W[e]^T and the data gradient dX = G W[e], both with BF16 output,
and the weight gradient dW[e] = G^T X, with BF16 or FP32 output. This PR
ships all four under deterministic names. The package
`flashinfer.experimental.cake_moe_grouped_gemm` becomes
`flashinfer.experimental.cake_moe_grouped_det_gemm`. `grouped_gemm_fwd`
/ `grouped_gemm_dgrad` / `grouped_gemm_wgrad` become
`grouped_det_gemm_fwd` / `grouped_det_gemm_dgrad` /
`grouped_det_gemm_wgrad`. The `prepare_*` planners, `GroupedGemmLaunch`,
`CakeGroupedMm` and `cake_grouped_mm` are renamed the same way.
`grouped_mm_bf16(..., backend="cake")` does not change, and the old
import path and old names remain as aliases of the same objects. Only
the names of the generated kernels change. Compared with the previous
Cake version of this package on FlashInfer main, speed does not change:
across 58 shapes, per-shape speedups range from 0.992x to 1.003x, with a
median of 1.000x.

NVIDIA GB300, sm_103a (152 SMs), CUDA 13.4 (kernels built with nvcc
13.4.92; PyTorch 2.14.1+cu130), driver 580.159.03; main = FlashInfer
main's package, this PR = the det package; median kernel time with a
cold L2, paired ABBA groups in one process on one GPU; speedup = 1 /
median of the per-group this PR / main ratios.

| shape | main ms | this PR ms | speedup |
|---|---:|---:|---:|
| fwd gate_up (N=4096, K=6144), E=4, M=112576, balanced | 3.1611 |
3.1595 | 1.000x |
| fwd gate_up (N=4096, K=6144), E=4, M=112576, skewed | 3.1695 | 3.1727
| 0.999x |
| fwd gate_up (N=4096, K=6144), E=4, M=112576, one-empty | 3.1633 |
3.1676 | 0.998x |
| fwd gate_up (N=4096, K=6144), E=4, M=136064, balanced | 3.8368 |
3.8380 | 1.000x |
| fwd gate_up (N=4096, K=6144), E=4, M=136064, skewed | 3.8403 | 3.8403
| 1.000x |
| fwd gate_up (N=4096, K=6144), E=4, M=136064, one-empty | 3.8352 |
3.8376 | 0.999x |
| dgrad gate_up (N=4096, K=6144), E=4, M=112576, balanced | 3.1135 |
3.1377 | 0.992x |
| dgrad gate_up (N=4096, K=6144), E=4, M=112576, skewed | 3.1124 |
3.0960 | 1.001x |
| dgrad gate_up (N=4096, K=6144), E=4, M=112576, one-empty | 3.1065 |
3.1271 | 0.995x |
| dgrad gate_up (N=4096, K=6144), E=4, M=136064, balanced | 3.7810 |
3.7809 | 1.000x |
| dgrad gate_up (N=4096, K=6144), E=4, M=136064, skewed | 3.7874 |
3.7943 | 0.999x |
| dgrad gate_up (N=4096, K=6144), E=4, M=136064, one-empty | 3.7818 |
3.7846 | 0.999x |
| wgrad gate_up (N=4096, K=6144), E=4, M=112576, balanced | 3.2129 |
3.2112 | 1.001x |
| wgrad gate_up (N=4096, K=6144), E=4, M=112576, skewed | 3.3025 |
3.2974 | 1.001x |
| wgrad gate_up (N=4096, K=6144), E=4, M=112576, one-empty | 3.3397 |
3.3400 | 1.000x |
| wgrad gate_up (N=4096, K=6144), E=4, M=136064, balanced | 3.8797 |
3.8762 | 1.001x |
| wgrad gate_up (N=4096, K=6144), E=4, M=136064, skewed | 4.0019 |
4.0004 | 1.000x |
| wgrad gate_up (N=4096, K=6144), E=4, M=136064, one-empty | 4.0321 |
4.0328 | 1.000x |
| fwd down (N=6144, K=2048), E=4, M=112576, balanced | 1.5910 | 1.5874 |
1.003x |
| fwd down (N=6144, K=2048), E=4, M=112576, skewed | 1.5872 | 1.5915 |
0.997x |
| fwd down (N=6144, K=2048), E=4, M=112576, one-empty | 1.5917 | 1.5881
| 1.003x |
| fwd down (N=6144, K=2048), E=4, M=136064, balanced | 1.9157 | 1.9177 |
1.000x |
| fwd down (N=6144, K=2048), E=4, M=136064, skewed | 1.9272 | 1.9227 |
1.001x |
| fwd down (N=6144, K=2048), E=4, M=136064, one-empty | 1.9197 | 1.9199
| 1.000x |
| dgrad down (N=6144, K=2048), E=4, M=112576, balanced | 1.5927 | 1.5889
| 1.001x |
| dgrad down (N=6144, K=2048), E=4, M=112576, skewed | 1.5961 | 1.5940 |
1.001x |
| dgrad down (N=6144, K=2048), E=4, M=112576, one-empty | 1.5947 |
1.5890 | 1.002x |
| dgrad down (N=6144, K=2048), E=4, M=136064, balanced | 1.8890 | 1.8891
| 1.000x |
| dgrad down (N=6144, K=2048), E=4, M=136064, skewed | 1.9206 | 1.9226 |
0.999x |
| dgrad down (N=6144, K=2048), E=4, M=136064, one-empty | 1.9177 |
1.9183 | 1.000x |
| wgrad down (N=6144, K=2048), E=4, M=112576, balanced | 1.5956 | 1.5959
| 1.000x |
| wgrad down (N=6144, K=2048), E=4, M=112576, skewed | 1.6423 | 1.6413 |
1.000x |
| wgrad down (N=6144, K=2048), E=4, M=112576, one-empty | 1.6245 |
1.6253 | 0.999x |
| wgrad down (N=6144, K=2048), E=4, M=136064, balanced | 1.9430 | 1.9426
| 1.000x |
| wgrad down (N=6144, K=2048), E=4, M=136064, skewed | 1.9816 | 1.9821 |
1.000x |
| wgrad down (N=6144, K=2048), E=4, M=136064, one-empty | 1.9592 |
1.9590 | 1.000x |
| wgrad gate_up (N=4096, K=6144), E=4, M=112576, balanced, FP32 dW |
3.2608 | 3.2595 | 1.000x |
| wgrad gate_up (N=4096, K=6144), E=4, M=136064, balanced, FP32 dW |
3.9353 | 3.9345 | 1.001x |
| wgrad down (N=6144, K=2048), E=4, M=112576, balanced, FP32 dW | 1.6242
| 1.6269 | 0.999x |
| wgrad down (N=6144, K=2048), E=4, M=136064, balanced, FP32 dW | 1.9769
| 1.9754 | 1.000x |
| fwd gate_up (N=4096, K=6144), E=8, M=131072, balanced | 3.6791 |
3.6821 | 0.999x |
| dgrad gate_up (N=4096, K=6144), E=8, M=131072, balanced | 3.6521 |
3.6521 | 1.000x |
| wgrad gate_up (N=4096, K=6144), E=8, M=131072, balanced | 3.7328 |
3.7302 | 1.001x |
| fwd down (N=6144, K=2048), E=8, M=131072, balanced | 1.8566 | 1.8565 |
1.000x |
| dgrad down (N=6144, K=2048), E=8, M=131072, balanced | 1.8251 | 1.8251
| 1.000x |
| wgrad down (N=6144, K=2048), E=8, M=131072, balanced | 1.8741 | 1.8737
| 1.000x |
| fwd gate_up (N=4096, K=6144), E=16, M=131072, balanced | 3.7168 |
3.7164 | 1.001x |
| dgrad gate_up (N=4096, K=6144), E=16, M=131072, balanced | 3.6735 |
3.6760 | 0.999x |
| wgrad gate_up (N=4096, K=6144), E=16, M=131072, balanced | 3.7487 |
3.7461 | 1.001x |
| fwd down (N=6144, K=2048), E=16, M=131072, balanced | 1.8600 | 1.8594
| 1.000x |
| dgrad down (N=6144, K=2048), E=16, M=131072, balanced | 1.8319 |
1.8309 | 1.000x |
| wgrad down (N=6144, K=2048), E=16, M=131072, balanced | 1.8802 |
1.8798 | 1.000x |
| fwd gate_up (N=4096, K=6144), E=32, M=131072, balanced | 3.7382 |
3.7374 | 1.000x |
| dgrad gate_up (N=4096, K=6144), E=32, M=131072, balanced | 3.7309 |
3.7309 | 1.000x |
| wgrad gate_up (N=4096, K=6144), E=32, M=131072, balanced | 3.7728 |
3.7698 | 1.001x |
| fwd down (N=6144, K=2048), E=32, M=131072, balanced | 1.8613 | 1.8622
| 1.000x |
| dgrad down (N=6144, K=2048), E=32, M=131072, balanced | 1.8542 |
1.8552 | 0.999x |
| wgrad down (N=6144, K=2048), E=32, M=131072, balanced | 1.8872 |
1.8889 | 0.999x |

Cake ships no other data type or layout of this kernel beyond these four
variants, and the family ships kernels for sm_100a, sm_103a and sm_107a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added deterministically named Cake APIs for BF16 grouped GEMM forward,
data-gradient, and weight-gradient operations, including an autograd
interface.
* The existing Cake backend option for grouped matrix multiplication now
uses the deterministically named implementation.
* **Compatibility**
* Former API names and package paths remain available as deprecated
aliases.
* **Documentation**
* Updated API references, examples, and benchmark instructions to use
the new names.
* **Tests**
* Added checks for repeatable results across launches and fresh
processes.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [386c7c7](https://github.com/flashinfer-ai/flashinfer/commit/386c7c76b71470d830fdfb6300813ad840d57360)

- **作者**: eigen
- **时间**: 2026-10-30T22:56:08Z
- **提交信息**: perf(cake_minimax_h3): longest-first drain order for two-class overlapped SM120 NVFP4 varlen attention plans (#8040)

FlashInfer has four Cake variants of MiniMax-H3 non-causal packed-varlen
attention on sm_120a: three NVFP4-QK forms and one FP8 form. This PR
changes two of the NVFP4-QK forms. The first is
`minimax_h3_sm120_varlen_attention_nvfp4`, the compensated
SageAttention3 FP4 recipe (columns "D"). The second is
`minimax_h3_sm120_varlen_attention_nvfp4_nodelta`, the uncompensated
form (columns "N").

The change affects only the host-side unit order of the overlapped form.
Some plans have non-empty segments with at most two key-tile counts. In
those plans, the last 4 x (plan grid) units now run longest first. All
other plans keep the head-major order.

The baseline is the same ops on FlashInfer main. Latency is the median
GPU time per call of the whole op with cold L2. Each cell is the mean
over two GPUs. Only seg3_ragged changes its plan. Rows marked
"(unchanged)" launch the same programs, grids and unit tables as
FlashInfer main. Their small differences are run-to-run noise.

### NVIDIA RTX PRO 6000 Blackwell Server Edition (sm_120, CUDA 13.4)

FI main vs this PR, latency per call in us (mean of two GPUs), speedup =
FI main / this PR.

| shape | tokens | D: FI main (us) | D: this PR (us) | D: speedup | N:
FI main (us) | N: this PR (us) | N: speedup |
|---|---|---|---|---|---|---|---|
| center_4s | 33472 | 32,638.51 | 32,651.69 | 1.000x (unchanged) |
29,618.58 | 29,624.25 | 1.000x (unchanged) |
| center_5s | 38592 | 43,472.38 | 43,385.52 | 1.002x (unchanged) |
39,578.19 | 39,557.30 | 1.001x (unchanged) |
| center_6s | 48768 | 68,861.76 | 68,887.42 | 1.000x (unchanged) |
62,940.24 | 62,850.04 | 1.001x (unchanged) |
| center_8s | 58944 | 100,695.82 | 100,707.26 | 1.000x (unchanged) |
91,955.51 | 91,955.33 | 1.000x (unchanged) |
| center_10s | 74240 | 158,528.32 | 158,462.13 | 1.000x (unchanged) |
144,345.66 | 144,356.03 | 1.000x (unchanged) |
| center_15s | 109952 | 345,733.76 | 345,724.42 | 1.000x (unchanged) |
312,901.86 | 312,977.22 | 1.000x (unchanged) |
| tail_5s_a | 38531 | 43,264.54 | 43,268.52 | 1.000x (unchanged) |
39,472.91 | 39,446.70 | 1.001x (unchanged) |
| tail_5s_b | 38629 | 43,333.25 | 43,337.99 | 1.000x (unchanged) |
39,638.77 | 39,629.09 | 1.000x (unchanged) |
| pad_15s | 109952 | 345,410.34 | 345,430.53 | 1.000x (unchanged) |
312,947.18 | 312,871.69 | 1.000x (unchanged) |
| seg4 | 33472 | 9,019.51 | 9,018.98 | 1.000x (unchanged) | 8,193.85 |
8,193.95 | 1.000x (unchanged) |
| seg3_ragged | 4824 | 730.96 | 712.24 | 1.026x | 668.64 | 662.09 |
1.010x |
| seg_empty | 500 | 49.19 | 49.38 | 0.996x (unchanged) | 47.67 | 47.68 |
1.000x (unchanged) |
| single_4096 | 4096 | 635.55 | 636.43 | 0.999x (unchanged) | 578.99 |
578.62 | 1.001x (unchanged) |
| m1 | 1 | 16.56 | 16.53 | 1.002x (unchanged) | 16.11 | 16.02 | 1.006x
(unchanged) |
| m128 | 128 | 20.89 | 20.84 | 1.002x (unchanged) | 20.55 | 20.36 |
1.009x (unchanged) |
| m129 | 129 | 22.97 | 22.99 | 0.999x (unchanged) | 22.26 | 22.36 |
0.996x (unchanged) |
| seg_133_300_900 | 900 | 86.80 | 86.62 | 1.002x (unchanged) | 83.62 |
83.58 | 1.000x (unchanged) |

### NVIDIA GeForce RTX 5090 (sm_120, CUDA 13.4)

FI main vs this PR, latency per call in us (mean of two GPUs), speedup =
FI main / this PR.

| shape | tokens | D: FI main (us) | D: this PR (us) | D: speedup | N:
FI main (us) | N: this PR (us) | N: speedup |
|---|---|---|---|---|---|---|---|
| center_4s | 33472 | 35,556.23 | 35,543.69 | 1.000x (unchanged) |
32,302.41 | 32,314.57 | 1.000x (unchanged) |
| center_5s | 38592 | 47,541.78 | 47,526.17 | 1.000x (unchanged) |
43,145.66 | 43,165.22 | 1.000x (unchanged) |
| center_6s | 48768 | 76,354.98 | 76,430.92 | 0.999x (unchanged) |
69,106.73 | 69,093.60 | 1.000x (unchanged) |
| center_8s | 58944 | 112,581.54 | 112,591.28 | 1.000x (unchanged) |
101,918.44 | 101,935.73 | 1.000x (unchanged) |
| center_10s | 74240 | 178,216.33 | 178,232.86 | 1.000x (unchanged) |
161,685.18 | 161,729.03 | 1.000x (unchanged) |
| center_15s | 109952 | 389,638.35 | 389,498.43 | 1.000x (unchanged) |
353,118.55 | 353,131.12 | 1.000x (unchanged) |
| tail_5s_a | 38531 | 48,034.43 | 48,001.22 | 1.001x (unchanged) |
43,482.78 | 43,512.09 | 0.999x (unchanged) |
| tail_5s_b | 38629 | 47,902.52 | 47,888.91 | 1.000x (unchanged) |
43,348.81 | 43,371.40 | 0.999x (unchanged) |
| pad_15s | 109952 | 389,410.18 | 389,334.99 | 1.000x (unchanged) |
352,876.48 | 352,719.08 | 1.000x (unchanged) |
| seg4 | 33472 | 9,863.36 | 9,859.58 | 1.000x (unchanged) | 9,054.60 |
9,056.32 | 1.000x (unchanged) |
| seg3_ragged | 4824 | 751.90 | 746.74 | 1.007x | 694.77 | 686.12 |
1.013x |
| seg_empty | 500 | 38.57 | 38.55 | 1.001x (unchanged) | 37.07 | 37.11 |
0.999x (unchanged) |
| single_4096 | 4096 | 654.45 | 654.17 | 1.000x (unchanged) | 600.47 |
600.01 | 1.001x (unchanged) |
| m1 | 1 | 15.59 | 15.54 | 1.003x (unchanged) | 15.18 | 15.17 | 1.001x
(unchanged) |
| m128 | 128 | 16.90 | 16.88 | 1.001x (unchanged) | 16.80 | 16.75 |
1.003x (unchanged) |
| m129 | 129 | 19.22 | 19.23 | 0.999x (unchanged) | 18.50 | 18.46 |
1.002x (unchanged) |
| seg_133_300_900 | 900 | 72.38 | 72.49 | 0.998x (unchanged) | 69.30 |
69.26 | 1.001x (unchanged) |

This SM120 family ships for sm_120a only, with two other Cake variants:
the NVFP4-QK / FP8-PV form (`pv_mode="fp8"`) and the FP8 form
`minimax_h3_sm120_varlen_attention_fp8`. On sm_100a (B200) and sm_103a
(GB300), `minimax_h3_varlen_attention` provides the same op in BF16,
`pv_mode="fp4"` and `pv_mode="fp8"` forms.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* Updated processing order for attention workloads with up to two
distinct non-empty segment sizes, prioritizing longer segments near the
end of the schedule. Workloads with more than two distinct sizes retain
their existing head-major order.

* **Tests**
* Added coverage for the updated ordering and for cases that retain the
existing order.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [10cfb36](https://github.com/flashinfer-ai/flashinfer/commit/10cfb36faf430479120d134929f75c3b9465d4d2)

- **作者**: eigen
- **时间**: 2026-10-30T22:38:06Z
- **提交信息**: perf(cake_ulysses): faster world-8 bf16 direct scatter, two-unit zone copied in one round (#8044)

Cake's Ulysses all-to-all for `flashinfer.comm` sequence parallelism
(scatter heads / gather heads over NVLink) has 48 programs: bf16 / f16 /
f32 × world sizes 2 / 4 / 6 / 8 × both directions × two routes. The
staged route serves plain outputs. The direct route writes straight into
peers' registered outputs from `allocate_output`. This PR updates 1 of
them: the direct-route program at world size 8 for bf16, scatter heads.
Since #7891, this program loads the first unit of each lane before it
waits for the destination's entry token. If the destination has not
entered the launch yet, that unit goes into a zone at the tail of the
destination's signal allocation, and the destination copies it into its
output before its launch ends. With this PR, the zone holds the first
two units of each lane's first trip. The destination now copies both
into its output in one round of its warps 1 to 15, after a single vote
across the CTA on whether the zone was used. The signal allocation size
is unchanged (1,138,688 32-bit words). Outputs are bit-identical. The
baseline is the previous Cake version of the same programs, which
FlashInfer main ships today (including #7891 and #7808). At world size 8
with scatter heads the speedup over it is 1.004x on B300 and 1.004x on
B200. On the other seven rows both columns run the same program, so
their differences are spread between two builds of the same code (0.997x
to 1.001x on B300, 0.999x to 1.001x on B200).

**NVIDIA B300 SXM6 AC (sm_103a), 8 GPUs, CUDA 13.4, PyTorch
2.14.1+cu130.** bf16, batch 1, global sequence length 32760, head dim
128, heads 40 at world 2 / 4 / 8 and 48 at world 6 (local sequence 16380
/ 8190 / 5460 / 4095 at world 2 / 4 / 6 / 8), outputs allocated with
`allocate_output` (registered). Latency is in us per call, measured from
the beginning of the last rank's kernel to the end of the last rank's
kernel (max over ranks of kernel end time minus max over ranks of kernel
begin time), median over 20 rounds (two sessions of 10 interleaved
rounds, 15 calls per round), with both versions measured in the same
process on the same outputs. Speedup = previous Cake / this PR.

| world | heads | direction | previous Cake (us) | this PR (us) |
speedup |
|---:|---:|---|---:|---:|---:|
| 2 | 40 | scatter heads | 128.267 | 128.190 | 1.001x |
| 2 | 40 | gather heads | 128.249 | 128.185 | 1.000x |
| 4 | 40 | scatter heads | 103.338 | 103.256 | 1.001x |
| 4 | 40 | gather heads | 103.499 | 103.428 | 1.001x |
| 6 | 48 | scatter heads | 94.119 | 94.405 | 0.997x |
| 6 | 48 | gather heads | 95.494 | 95.548 | 0.999x |
| 8 | 40 | scatter heads | 64.800 | 64.544 | 1.004x |
| 8 | 40 | gather heads | 66.240 | 66.225 | 1.000x |

**NVIDIA B200 (sm_100a), 8 GPUs, CUDA 13.4, PyTorch 2.14.1+cu130.**
bf16, batch 1, global sequence length 32760, head dim 128, heads 40 at
world 2 / 4 / 8 and 48 at world 6 (local sequence 16380 / 8190 / 5460 /
4095 at world 2 / 4 / 6 / 8), outputs allocated with `allocate_output`
(registered). Latency is in us per call, measured from the beginning of
the last rank's kernel to the end of the last rank's kernel (max over
ranks of kernel end time minus max over ranks of kernel begin time),
median over 20 rounds (two sessions of 10 interleaved rounds, 15 calls
per round), with both versions measured in the same process on the same
outputs. Speedup = previous Cake / this PR.

| world | heads | direction | previous Cake (us) | this PR (us) |
speedup |
|---:|---:|---|---:|---:|---:|
| 2 | 40 | scatter heads | 127.588 | 127.526 | 1.000x |
| 2 | 40 | gather heads | 127.331 | 127.303 | 1.000x |
| 4 | 40 | scatter heads | 101.571 | 101.632 | 0.999x |
| 4 | 40 | gather heads | 102.128 | 102.013 | 1.001x |
| 6 | 48 | scatter heads | 92.165 | 92.192 | 1.000x |
| 6 | 48 | gather heads | 93.155 | 93.028 | 1.001x |
| 8 | 40 | scatter heads | 63.728 | 63.456 | 1.004x |
| 8 | 40 | gather heads | 65.409 | 65.457 | 0.999x |

Cake also ships the staged route (plain outputs) for all three data
types and the direct route for the other 23 programs (world sizes 2, 4
and 6 for bf16 / f16 / f32 in both directions, world size 8 for f16 /
f32 in both directions, and the world-8 bf16 gather-heads program), all
unchanged by this PR, and the whole family ships on sm_100a and sm_103a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Tests**
* Expanded communication test coverage for scatter and gather
operations, including cases where scatter writes multiple slots per
lane.
* Added checks around a stripe boundary to verify expected write counts
across chunks and lane offsets.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [e9eb884](https://github.com/flashinfer-ai/flashinfer/commit/e9eb884a2444278f7bf76d5a102571e9c33ac078)

- **作者**: Netanel Haber
- **时间**: 2026-10-30T22:10:23Z
- **提交信息**: [SDSA 3/6][Indexer] Add paged MQA logits for a one-head indexer (BF16 keys) (#6422)

`fp8_paged_mqa_logits` scores keys for an indexer with many heads. An
indexer with one head has no head weights and no ReLU. Its score is the
dot product of a query row and a key.

This PR adds `single_head_paged_mqa_logits` for SM10x:
- The keys are BF16. Each key has 128 values, and each page has 64 keys.
- Each request has 1 to 8 query rows, for example a decode token and its
draft tokens.
- The grid size comes from the context capacity and not from the
lengths. Because of this, you can capture the call in a CUDA graph.

This PR is part 3 of 6 of SDSA: sparse attention with a one-head indexer
and an MQA core. The indexer selects the Top-K keys of each query token,
and the MQA core attends to these keys. Parts 1-2 (#6420, #6421) add
token-sparse attention, and they are merged. Parts 3-6 add the indexer.
The next part is #6423.

I used AI assistance.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added paged multi-query attention scoring for BF16 queries and keys on
supported GPUs, with results available through the package’s public API.
* Added tracing support for the new scoring operation, including
configurable input shapes and correctness checks.
* **Tests**
* Added coverage for score accuracy, preserved output values beyond
context lengths, CUDA graph replay, and invalid inputs.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Netanel Haber <nhaber@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [6336f3e](https://github.com/flashinfer-ai/flashinfer/commit/6336f3ee5f8a0050ea65a6647c0fa72ad081b673)

- **作者**: Alex Yang
- **时间**: 2026-10-30T22:09:34Z
- **提交信息**: perf(topk): cache multi-CTA radix row_states per stream instead of zeroing per call (#7964)

<!-- .github/pull_request_template.md -->

## 📌 Description

#3625 (1b7a90a05) gave concurrent streams disjoint `row_states` scratch
for the multi-CTA radix top-k
kernels by allocating a zeroed buffer with `torch.zeros` on every call,
in nine producers
(`top_k`, `top_k_page_table_transform`, `top_k_ragged_transform`,
`top_k_renorm_probs`,
`top_k_mask_logits`, their `logits_processor` operators, and the `radix`
/ `radix_cutlass` backends of
`top_k_varlen`). The memset and allocation are paid on every launch,
although the kernels zero the state they
dirty before they exit and never touch the buffer in the single-CTA
regime. NVIDIA's GPU SWQA performance CI
bisected a latency regression to that commit (NVBug 6946353): +3-6% on
`top_k_mask_logits`,
`top_k_renorm_probs` and `top_k_top_p_sampling_from_logits`, and
+63-229% on `top_k_varlen`'s `radix`
backend, on B200, GB300 and VR_NVL72.

This PR keeps #3625's isolation and removes the per-call zeroing:

- `flashinfer/utils.py`: `_get_stream_cache_buf()` caches a scratch
buffer per `(name, device, current CUDA
stream)`, zero-initialised once at allocation. Launches on one stream
are ordered, so each leaves the buffer
zeroed for the next; launches on other streams get their own buffer
(#3618). PyTorch draws stream handles
  from a fixed per-device pool, which bounds the number of buffers.
- `flashinfer/topk.py`: `_get_row_states_buffer()` returns that cached
buffer outside CUDA graph capture.
Under capture it keeps the per-call allocation from #3625 (graph-pool
storage, captured memset), because the
replay stream is unknown at capture time and two graphs may replay
concurrently.
- `flashinfer/topk_varlen/topk_varlen.py`: the CuTe-DSL `radix` backend
passes no `row_states` at all when
`ctas_per_group == 1`, where the kernel guards every access with
`const_expr(ctas_per_group > 1)` and
compiles it away (`_compile_radix` compiles that regime with a `None`
fake tensor, the same pattern as the
absent `output_values`). The multi-CTA regime slices a per-stream
worst-case `(num_sms, STATE_SIZE)` int32
buffer to the grid, so it never grows between calls with different
`ctas_per_group`.

Why dirty reuse on one stream is safe (verified by reading the kernels):

- `include/flashinfer/topk.cuh`: `RadixGroupResetStateLastCTA` zeroes
the three histograms, the deterministic
collect scratch and `arrival_counter` as the last CTA of each group
exits; all three kernels call it.
`output_counter` is reset per row by CTA 0 after the initial barrier;
`sum_topk` / `sum_topk_fixed` are
initialised per row before accumulation. The single-CTA path runs with
`state == nullptr`.
- `flashinfer/topk_varlen/kernels/radix_topk.py`:
`griddepcontrol_wait()` precedes any global access, CTA 0
resets `output_counter` per row after the barrier, and CTA 0 zeroes the
histograms and the arrival counter
  before the kernel exits.

No environment variables and no kernel changes. Thanks to the GPU SWQA
team for the bisection
(NVBug 6946353).

### Performance

Measured for this PR on 2026-10-30 with
`benchmarks/flashinfer_benchmark.py` (CUPTI timing, 30 timed + 5 warm-up
iterations per run, L2 flushed before every call), using the CI image
`flashinfer-ci-cu130:20260930-b1420f1`
(torch 2.14.0+cu130, nvidia-cutlass-dsl 4.7.0) plus `cupti-python`
13.4.0. Three source checkouts ran in one
container, interleaved parent / main / PR for 10 runs each; a cell is
the median over the 10 per-run CUPTI medians,
with the min–max of those per-run medians in parentheses (µs):

- `6c23f96` = parent of #3625 (before the regression);
- `5d60811` = `main` at measurement time;
- PR = `8e5b50d` merged onto `5d60811` (clean merge, the 7 files of this
PR).

"PR vs main" is the clean A/B for this change. The parent column also
carries the 1049 other commits between
`6c23f96` and `5d60811`, so "vs parent" mixes in unrelated changes
(visible in the `radix_cutlass` and
`top_k_top_p_sampling_*` rows).

**B200** (148 SMs, 178 GiB, 600 W power limit, driver 615.71.10; an
internal bring-up board that `nvidia-smi`
reports as "NVIDIA Graphics Device"):

| Routine / backend | Case | Mode | `6c23f96` parent (µs) | `5d60811`
main (µs) | PR on main (µs) | PR vs main | PR vs parent | main vs parent
|
|---|---|---|---|---|---|---|---|---|
| `top_k_mask_logits` / `cuda` | DeepSeek-R1 | eager | 31.40
(31.30–31.49) | 46.30 (45.87–46.59) | 31.38 (31.31–31.42) | -32.2% |
-0.1% | +47.5% |
| `top_k_mask_logits` / `cuda` | DeepSeek-R1 | graph | 31.62
(31.58–31.70) | 32.51 (32.38–32.54) | 32.66 (32.59–32.73) | +0.4% |
+3.3% | +2.8% |
| `top_k_mask_logits` / `cuda` | Llama-3.1-8B | eager | 31.13
(31.09–31.23) | 46.31 (46.02–46.93) | 31.19 (31.14–31.25) | -32.6% |
+0.2% | +48.8% |
| `top_k_mask_logits` / `cuda` | Llama-3.1-8B | graph | 31.42
(31.34–31.49) | 32.70 (32.62–32.77) | 32.74 (32.67–32.80) | +0.1% |
+4.2% | +4.1% |
| `top_k_mask_logits` / `cuda` | Qwen3-30B-A3B | eager | 34.18
(34.06–34.26) | 49.69 (49.18–49.98) | 34.10 (34.03–34.14) | -31.4% |
-0.2% | +45.4% |
| `top_k_mask_logits` / `cuda` | Qwen3-30B-A3B | graph | 34.60
(34.53–34.75) | 36.03 (35.92–36.06) | 35.90 (35.81–35.97) | -0.4% |
+3.8% | +4.1% |
| `top_k_renorm_probs` / `cuda` | DeepSeek-R1 | eager | 37.12
(37.07–37.18) | 52.30 (51.78–52.73) | 37.13 (37.04–37.26) | -29.0% |
+0.0% | +40.9% |
| `top_k_renorm_probs` / `cuda` | DeepSeek-R1 | graph | 37.39
(37.33–37.44) | 38.46 (38.40–38.54) | 38.55 (38.43–38.64) | +0.2% |
+3.1% | +2.8% |
| `top_k_renorm_probs` / `cuda` | Llama-3.1-8B | eager | 36.86
(36.80–36.91) | 52.47 (51.87–53.02) | 36.88 (36.83–36.96) | -29.7% |
+0.0% | +42.3% |
| `top_k_renorm_probs` / `cuda` | Llama-3.1-8B | graph | 37.14
(37.09–37.18) | 38.66 (38.58–38.70) | 38.57 (38.46–38.64) | -0.2% |
+3.8% | +4.1% |
| `top_k_renorm_probs` / `cuda` | Qwen3-30B-A3B | eager | 40.70
(40.58–40.75) | 56.38 (55.76–56.85) | 40.64 (40.58–40.70) | -27.9% |
-0.1% | +38.6% |
| `top_k_renorm_probs` / `cuda` | Qwen3-30B-A3B | graph | 41.22
(41.12–41.33) | 42.60 (42.50–42.74) | 42.55 (42.41–42.62) | -0.1% |
+3.2% | +3.3% |
| `top_k_top_p_sampling_from_logits` / `cuda` | DeepSeek-R1 | eager |
101.80 (100.16–105.20) | 125.70 (124.41–127.58) | 105.52 (103.53–108.83)
| -16.1% | +3.7% | +23.5% |
| `top_k_top_p_sampling_from_logits` / `cuda` | DeepSeek-R1 | graph |
63.29 (63.17–63.41) | 63.98 (63.90–64.05) | 63.42 (63.38–63.49) | -0.9%
| +0.2% | +1.1% |
| `top_k_top_p_sampling_from_probs` / `cuda` | DeepSeek-R1 | eager |
111.42 (109.95–116.22) | 130.64 (130.16–132.70) | 113.57 (112.11–116.17)
| -13.1% | +1.9% | +17.2% |
| `top_k_top_p_sampling_from_probs` / `cuda` | DeepSeek-R1 | graph |
94.56 (94.32–94.70) | 95.07 (94.94–95.17) | 95.17 (95.02–95.38) | +0.1%
| +0.6% | +0.5% |
| `top_k_varlen` / `radix` | sparse-kv-topk-32k | eager | 20.41
(20.35–20.50) | 27.99 (27.69–28.27) | 20.42 (20.35–20.48) | -27.0% |
+0.1% | +37.2% |
| `top_k_varlen` / `radix_cutlass` | sparse-kv-topk-32k | eager | 61.49
(60.74–65.50) | 67.30 (66.54–68.94) | 69.56 (69.17–71.52) | +3.4% |
+13.1% | +9.4% |
| `top_k_varlen` / `radix` | sparse-kv-topk-8k | eager | 8.98
(8.96–8.99) | 16.95 (16.50–17.09) | 8.96 (8.94–8.99) | -47.1% | -0.2% |
+88.9% |
| `top_k_varlen` / `radix_cutlass` | sparse-kv-topk-8k | eager | 51.46
(51.18–54.13) | 57.69 (57.17–59.18) | 60.22 (58.77–61.49) | +4.4% |
+17.0% | +12.1% |

<details>
<summary><b>GB200</b> (152 SMs, 184 GiB, driver 580.159.04), same image
and procedure</summary>

| Routine / backend | Case | Mode | `6c23f96` parent (µs) | `5d60811`
main (µs) | PR on main (µs) | PR vs main | PR vs parent | main vs parent
|
|---|---|---|---|---|---|---|---|---|
| `top_k_mask_logits` / `cuda` | DeepSeek-R1 | eager | 30.08
(29.99–30.18) | 68.66 (66.62–74.94) | 30.10 (30.03–30.13) | -56.2% |
+0.1% | +128.2% |
| `top_k_mask_logits` / `cuda` | DeepSeek-R1 | graph | 30.16
(30.13–30.22) | 31.45 (31.36–31.49) | 31.34 (31.31–31.39) | -0.4% |
+3.9% | +4.3% |
| `top_k_mask_logits` / `cuda` | Llama-3.1-8B | eager | 29.94
(29.86–29.98) | 68.64 (65.46–70.62) | 29.89 (29.84–29.98) | -56.5% |
-0.2% | +129.3% |
| `top_k_mask_logits` / `cuda` | Llama-3.1-8B | graph | 30.02
(29.90–30.08) | 31.77 (31.71–31.86) | 31.79 (31.68–31.86) | +0.1% |
+5.9% | +5.8% |
| `top_k_mask_logits` / `cuda` | Qwen3-30B-A3B | eager | 32.61
(32.53–32.74) | 72.43 (69.07–74.38) | 32.79 (32.72–32.83) | -54.7% |
+0.6% | +122.1% |
| `top_k_mask_logits` / `cuda` | Qwen3-30B-A3B | graph | 32.78
(32.61–32.88) | 34.20 (34.08–34.32) | 34.19 (34.11–34.26) | -0.0% |
+4.3% | +4.3% |
| `top_k_renorm_probs` / `cuda` | DeepSeek-R1 | eager | 35.60
(35.49–35.65) | 75.63 (71.78–80.10) | 35.59 (35.50–35.66) | -52.9% |
-0.0% | +112.5% |
| `top_k_renorm_probs` / `cuda` | DeepSeek-R1 | graph | 35.70
(35.58–35.78) | 37.41 (37.31–37.47) | 37.34 (36.90–37.44) | -0.2% |
+4.6% | +4.8% |
| `top_k_renorm_probs` / `cuda` | Llama-3.1-8B | eager | 35.41
(35.39–35.44) | 74.75 (71.89–77.68) | 35.38 (35.34–35.49) | -52.7% |
-0.1% | +111.1% |
| `top_k_renorm_probs` / `cuda` | Llama-3.1-8B | graph | 35.59
(35.52–35.65) | 37.18 (37.06–37.26) | 37.11 (36.99–37.25) | -0.2% |
+4.3% | +4.5% |
| `top_k_renorm_probs` / `cuda` | Qwen3-30B-A3B | eager | 38.73
(38.61–38.78) | 79.62 (76.08–82.16) | 38.79 (38.70–38.88) | -51.3% |
+0.2% | +105.6% |
| `top_k_renorm_probs` / `cuda` | Qwen3-30B-A3B | graph | 38.84
(38.74–38.88) | 40.50 (40.45–40.67) | 40.38 (40.26–40.43) | -0.3% |
+4.0% | +4.3% |
| `top_k_top_p_sampling_from_logits` / `cuda` | DeepSeek-R1 | eager |
237.83 (199.94–257.81) | 293.13 (276.27–314.24) | 243.76 (229.28–266.26)
| -16.8% | +2.5% | +23.2% |
| `top_k_top_p_sampling_from_logits` / `cuda` | DeepSeek-R1 | graph |
63.96 (63.81–64.03) | 64.42 (61.42–64.51) | 63.91 (63.73–64.08) | -0.8%
| -0.1% | +0.7% |
| `top_k_top_p_sampling_from_probs` / `cuda` | DeepSeek-R1 | eager |
257.12 (223.46–269.81) | 310.74 (259.20–320.43) | 262.18 (244.53–285.47)
| -15.6% | +2.0% | +20.9% |
| `top_k_top_p_sampling_from_probs` / `cuda` | DeepSeek-R1 | graph |
78.14 (78.05–78.38) | 79.94 (79.86–80.02) | 80.50 (80.26–80.61) | +0.7%
| +3.0% | +2.3% |
| `top_k_varlen` / `radix` | sparse-kv-topk-32k | eager | 20.11
(20.03–20.16) | 39.59 (37.41–40.50) | 20.03 (19.97–20.08) | -49.4% |
-0.4% | +96.9% |
| `top_k_varlen` / `radix_cutlass` | sparse-kv-topk-32k | eager | 122.06
(115.76–129.06) | 130.46 (122.77–141.78) | 138.26 (133.78–150.82) |
+6.0% | +13.3% | +6.9% |
| `top_k_varlen` / `radix` | sparse-kv-topk-8k | eager | 8.75
(8.70–8.77) | 29.34 (28.99–30.70) | 8.77 (8.74–8.80) | -70.1% | +0.2% |
+235.3% |
| `top_k_varlen` / `radix_cutlass` | sparse-kv-topk-8k | eager | 112.00
(104.93–120.66) | 127.67 (118.24–134.74) | 129.77 (119.75–142.62) |
+1.6% | +15.9% | +14.0% |

</details>

What the numbers say:

- **`top_k_varlen` / `radix`** (the backend the NVBug flagged, always
timed eagerly): back to the parent within
0.1% on both GPUs (B200: 17.0 → 8.96 µs at 8k, 27.9 → 20.4 µs at 32k;
GB200: 29.3 → 8.77 µs and 39.6 → 20.0 µs).
- **`top_k_mask_logits` / `top_k_renorm_probs`, eager** (what the APIs
run in a serving loop without graphs):
back to the parent within ±0.6% on both GPUs; −28% to −33% vs `main` on
B200, −49% to −56% on GB200.
`top_k_top_p_sampling_from_logits` / `_from_probs` eager: −14% to −17%
vs `main` on both GPUs.
- **CUDA-graph mode** (the perf CI's default for the sampling routines):
unchanged vs `main` within ±1% on both
GPUs, by design — the captured memset from #3625 is kept, so the +3–5%
graph-mode gap vs the parent that the
NVBug reports for these routines remains (see Reviewer Notes for the
follow-up).
- **`top_k_varlen` / `radix_cutlass`** (the any-GPU fallback backend,
not flagged in the NVBug): eager medians
+3–4% vs `main` on B200 and +6–9% on GB200, with wide run-to-run bands.
This is not a cost of the new code path:
running the PR tree with the buffer provider monkeypatched (GB200, 200
iterations × 3 runs per variant,
`radix_cutlass`, 8k / 32k) gave per-call `torch.zeros` as in `main` 125
/ 136 µs (= `main`), the cached buffer
as in this PR 135 / 144 µs, the same cached address re-zeroed every call
153 / 157 µs, and a different fixed
address 105 / 114 µs — all with the reference check passing. The
multi-CTA C++ kernel's time depends on where the
1 MiB `row_states` buffer lands; a per-call allocation averages over
addresses, a cached buffer (this PR, and the
code before #3625) fixes one. The same experiment on the B200 (runs
within ±0.3 µs) gave per-call `torch.zeros` 56.4 / 66.2 µs (= `main`
56.3 / 66.0), the cached buffer 58.5 / 68.1, the same address re-zeroed
per call 66.1 / 75.4, and a different fixed address 46.4 / 56.2. Since
the perf CI compares nightlies with the same methodology, it may flag
`radix_cutlass` by +3–4% after this PR. This PR accepts that rather than
keeping the per-call allocation for `radix_cutlass` only: the per-call
allocation hides the kernel's address sensitivity by averaging over
addresses instead of removing it, and the regression the NVBug reports
is in the `radix` backend and the sampling kernels. The address
sensitivity itself is a follow-up for the kernel.
- Why the eager `main` numbers are so much higher than the kernel cost
of a 1 MiB memset: the benchmark's per-call
time is the span from the first to the last GPU activity of the call, so
on `main` it includes the `torch.zeros`
fill kernel and the launch gap before the top-k kernel (≈15 µs on the
B200 host, ≈38 µs on the GB200's Grace host).
  That is also what the perf CI measured (+63–229% on `top_k_varlen`).

Reference check: `--refcheck` passed for `top_k_renorm_probs` and both
`top_k_varlen` backends on every run and
commit. `top_k_mask_logits --refcheck` reports a mask mismatch (82–177
of the k-th-boundary positions, bf16 ties)
identically on the parent, `main` and the PR, so those rows ran with
`--allow_output_mismatch`; this is a
pre-existing benchmark reference issue, not this PR.

Perf CI numbers from NVBug 6946353 for the GPUs not re-measured here
(CUPTI, best of two; `6c23f96` is #3625's
parent, `1b7a90a` is #3625):

| GPU | Routine / backend | Case | 6c23f96 (µs) | 1b7a90a (µs) | Change
|
|---|---|---|---|---|---|
| GB300 | top_k_mask_logits / cuda | DeepSeek-R1 (b64, v129280, k100,
bf16) | 28.19 | 29.87 | +5.96% |
| GB300 | top_k_renorm_probs / cuda | DeepSeek-R1 | 33.41 | 35.15 |
+5.22% |
| GB300 | top_k_top_p_sampling_from_logits / cuda | DeepSeek-R1 (p0.9,
top_k_first) | 60.80 | 63.01 | +3.63% |
| GB300 | top_k_varlen / radix | sparse-kv-topk-8k (b64, s8192, k512,
fp32) | 8.58 | 28.26 | +229.48% |
| GB300 | top_k_varlen / radix | sparse-kv-topk-32k (b16, s32768, k1024,
fp32) | 19.65 | 40.80 | +107.66% |
| VR_NVL72 | top_k_mask_logits / cuda | DeepSeek-R1 | 26.39 | 28.06 |
+6.36% |
| VR_NVL72 | top_k_renorm_probs / cuda | DeepSeek-R1 | 31.57 | 33.02 |
+4.61% |
| VR_NVL72 | top_k_varlen / radix | sparse-kv-topk-8k | 7.50 | 12.24 |
+63.11% |
| VR_NVL72 | top_k_varlen / radix | sparse-kv-topk-32k | 17.62 | 22.37 |
+26.98% |

The Llama-3.1-8B (v128256) and Qwen3-30B-A3B (b32, v151936) cases the
NVBug also lists are the corresponding rows
in the tables above (the NVBug's exact batch sizes and top-k for those
two models are not recorded; b64 / b32 and
k100 were used).

Reproduce (from `benchmarks/`; sampling routines once as given and once
with `--no_cuda_graph`):

```
python3 flashinfer_benchmark.py --routine top_k_varlen --batch_size 64 --max_seq_len 8192 --top_k 512 --input_dtype float32 --backends radix radix_cutlass --refcheck -vv
python3 flashinfer_benchmark.py --routine top_k_varlen --batch_size 16 --max_seq_len 32768 --top_k 1024 --input_dtype float32 --backends radix radix_cutlass --refcheck -vv
python3 flashinfer_benchmark.py --routine top_k_mask_logits --batch_size 64 --vocab_size 129280 --top_k 100 --input_dtype bfloat16 --refcheck --allow_output_mismatch -vv
python3 flashinfer_benchmark.py --routine top_k_renorm_probs --batch_size 64 --vocab_size 129280 --top_k 100 --input_dtype bfloat16 --refcheck -vv
python3 flashinfer_benchmark.py --routine top_k_top_p_sampling_from_logits --batch_size 64 --vocab_size 129280 --top_k 100 --top_p 0.9 --filter_apply_order top_k_first --input_dtype bfloat16 -vv
python3 flashinfer_benchmark.py --routine top_k_top_p_sampling_from_probs --batch_size 64 --vocab_size 129280 --top_k 100 --top_p 0.9 --filter_apply_order top_k_first -vv
```

## 🔍 Related Issues

- #3618 (the cross-stream sharing this keeps fixed), #3625 (the per-call
zeroing this replaces)
- NVBug 6946353 (internal perf CI; source of the measurements above)

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
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust):
`tests/utils/test_topk.py tests/utils/test_sampling.py
tests/utils/test_logits_processor.py
tests/topk_varlen/test_topk_varlen.py`

New tests:

- `tests/utils/test_topk.py`
-
`test_multi_cta_row_states_isolated_across_streams_with_different_row_counts`:
a 2-row and a 32-row
deterministic launch interleaved on two streams, so the per-group
collect scratch lands at different
offsets; every result checked against its reference, and the two
streams' cached buffers asserted distinct.
-
`test_multi_cta_reuses_row_states_buffer_on_one_stream_across_regimes`:
one stream reuses the same buffer
object across non-deterministic, deterministic and single-CTA launches
with exact expectations (restores
    the mode-transition coverage #3625 removed).
- `test_multi_cta_row_states_graph_replay_isolated_from_eager_stream`:
graph replay on one stream concurrent
    with eager launches on another.
- `tests/topk_varlen/test_topk_varlen.py`
-
`test_multi_cta_row_states_isolated_across_streams_with_different_batches`
(`radix`, `radix_cutlass`):
    1-row and 8-row multi-CTA launches interleaved on two streams.
- `test_radix_single_and_multi_cta_alternate_on_one_stream`: single-CTA
launches (no `row_states`) alternating
    with multi-CTA launches on one stream.
- The existing stream, graph and varlen graph tests from #3625 are
unchanged.
- Run on 2026-10-30 at the PR merged onto `5d60811`, `pytest
tests/utils/test_topk.py tests/utils/test_sampling.py
tests/topk_varlen/test_topk_varlen.py -x -q` (CI image
`flashinfer-ci-cu130:20260930-b1420f1`): B200 4103 passed, 151 skipped,
0 failed in 4 min 16 s; GB200 3759 passed, 495 skipped, 0 failed in 5
min 12 s. The scoped GitLab CI run requested above on `8e5b50d` passed
(29/29 executed test jobs).

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

- The memory footprint moves from one transient 1 MiB allocation per
call to one 1 MiB buffer per stream per
buffer name (three names for the C++ kernels, kept from before #3625,
plus one `num_sms x 770` int32 buffer
per stream for the varlen backend). Streams come from PyTorch's fixed
per-device pool, so this is bounded.
- Under CUDA graph capture nothing changes relative to #3625: each
captured call still allocates and
re-zeroes its own buffer on replay. A design that also drops that memset
(a per-graph buffer zeroed outside
the graph) needs a keep-alive registry or a self-initialising kernel
protocol and is left for a follow-up.
- The `row_states=None` compile for the single-CTA varlen kernel follows
the existing `output_values=None`
pattern in `_compile_radix`;
`tests/topk_varlen/test_topk_varlen.py::test_radix_basic` exercises it.
- Reuse relies on every launch reaching the kernels' exit reset: none of
the three C++ kernels has an early
`return`, and `RadixGroupResetStateLastCTA` runs after the row loop in
each. `_get_row_states_buffer` is only
reached for CUDA inputs, but a CPU input now fails in
`torch.cuda.current_stream` with a `ValueError` instead
  of in the kernel binding.
- Seen while reading, not changed here: the CuTe varlen kernel's exit
resets `arrival_counter` from CTA 0 right
after the final barrier, while a peer's thread 0 may still be spinning
to observe the target (the hazard the
C++ kernels close with the last-CTA exit protocol). Independent of where
the buffer comes from; follow-up.
- AI-assisted (Claude Code), reviewed by the author.

🤖 Generated with [Claude Code](https://claude.com/claude-code)




<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* Top-K operations reuse temporary workspace across calls, reducing
repeated buffer allocation and initialization.

* **Reliability**
* Improved handling of top-K operations running on multiple CUDA
streams, including concurrent calls with different batch sizes.
* Added coverage for CUDA graph replay and for switching between
single-CTA and multi-CTA operations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [b8551cc](https://github.com/flashinfer-ai/flashinfer/commit/b8551cc9ef7852d3e1fd76193be08c686c08c178)

- **作者**: rmhaskar
- **时间**: 2026-10-30T21:50:59Z
- **提交信息**: fix(msa_ops sm90): make the single-token CuTe prefill compile and run correctly on the cu12 CuTe DSL (#8037)

## 📌 Description

nvidia-cutlass-dsl ≥ 4.8 ships cu12 and cu13 builds of its compiler and
loads the newest one the CUDA driver supports. CUDA 12 installs on a
driver older than R580, including the cu129 H100 nightly lane, therefore
run the cu12 build. There, the SM90 one-token-per-CTA sparse prefill
(`sparse_prefill_single_sm90.py`) has two bugs:

- **Segfault at compile time (f16 PV body).** `cute.compile` crashes
inside the DSL when the last block is peeled after the block loop. The
last block now runs inside the loop, with its next-block refills
predicated off.
- **Wrong output at GQA 16 (fp8 PV body).** The cu12 build's ptxas feeds
the PV gemm a wrong P for query rows 8–15, giving wrong or NaN output. P
is now staged in f32 and each fp8 fragment is written whole.

Output is bit-identical to before on cu13, and cu12 now matches it. No
dispatch or API changes.

## 🔍 Related Issues

Fixes #7915. Supersedes #7969, which refused this schedule on cu12
instead. That makes prefill above 4096 pages fail there, because this is
the only route at that size.

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

- [ x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

Suggested CI test targets: `tests/msa_ops/test_msa_sm90.py`

Adds `test_single_token_prefill_short_block_lists`, which covers both PV
bodies at GQA 8 and 16 with short (`-1`-padded) block lists. On H100,
`tests/msa_ops` passes with both the cu12 and cu13 builds (282 passed,
421 skipped); unpatched main crashes on cu12.

## Reviewer Notes

Both bugs are in the cu12 toolchain, not the kernel math; these changes
work around them.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved sparse attention results for inputs with short block
selections and padded entries.
* **Tests**
* Added coverage across multiple query sizes and head counts, checking
that outputs remain finite and close to the reference.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [fca8897](https://github.com/flashinfer-ai/flashinfer/commit/fca8897833d7b8daac9485aa7f29d2da3c65e6b5)

- **作者**: RomanAnders90
- **时间**: 2026-10-30T21:02:45Z
- **提交信息**: [Experimental] Qwen 3.5 block: the Qwen3.8-27B dense attention layer as a validated member (#8036)

The Qwen 3.5 gated attention block package now serves the Qwen3.8-27B dense attention layer (24 query heads / 4 KV heads x 256, d_model 5120, rope dim 64) as a validated member: 14 cells at that geometry (decode at pages 16 / 32 and batch 1 / 4, extend behind a prefix, prefill) against the module's oracle at its existing bound, and the serving stack's packed K|V pool bound as two half views (KV_LAYOUTS gains UNIFIED, append-only; bitwise the HND twin). README and docs carry the member row and the layout; the vendored cuDNN Frontend pin is unchanged.

Co-Authored-By: Claude Fable 5.1 <noreply@anthropic.com>

### [1d2cd26](https://github.com/flashinfer-ai/flashinfer/commit/1d2cd26629cdd4e70e7eef92ddc17e685f3ff9da)

- **作者**: Ziang Li
- **时间**: 2026-10-30T20:21:42Z
- **提交信息**: perf: hoist NVFP4 global reciprocal before the zero-scale check (#7976)

## 📌 Description

@humansand

Reduce standard-fast CUDA NVFP4 quantization latency after #7501 while
preserving its zero-E4M3-scale contract.

- **Kernel:** compute `rcp.approx.ftz(SFScaleVal)` before the E4M3
conversion/zero check. Keep `fp8SFVal != 0`, the multiplication order,
and the final approximate reciprocal unchanged. A nonzero block whose
E4M3 scale rounds to zero still selects `0.0f` for its encode scale.
- **Scheduling:** the measured SM103a kernel moves the independent
global reciprocal ahead of the byte predicate. For the reported BF16 TMA
specialization, register counts remain 80 across the historical
comparison and 72 across the main/PR pair; both comparisons retain 0
local bytes and 1024 shared bytes.
- **Coverage:** add 12 exact boundary cases for FP16/BF16, ordinary/TMA
paths, and the FP32 neighbors below/at/above the E4M3 zero midpoint.
Each case checks packed payload and scale bytes through both single and
batched CUDA APIs.
- **Benchmark:** extend the existing
`bench_nvfp4_quantize_backend_comparison.py` with explicit M/K
selection, iteration counts, CUDA graphs, deterministic same-input
backend comparisons, per-sample CSV output, and optional heatmap
suppression. Its default sweep, 30 measured/5 warmup iterations, eager
timing, both-backend correctness verification, and CuTe-only bandwidth
mode are retained. CUDA per-token timing materializes the scalar before
capture. Graph mode requires CUPTI and rejects the event fallback to
preserve cold-L2 measurements; eager event fallback still flushes L2.
CSV headers derive from the row metadata, and heatmap suppression avoids
reindenting the existing plotting code.
- **Scope:** standard-fast CUDA NVFP4 only. The strict, 4over6, MX, and
CuTe quantizer implementations are unchanged. The unused
`cvt_warp_fp16_to_fp4_with_vec_max` helper already receives the
reciprocal as an argument.

## 🔍 Related Issues

Addresses #7962. The relevant change in #7501 was the production CUDA
predicate from `vecMax != 0` to `fp8SFVal != 0`; it was not limited to
test utilities.

## Validation and performance

### Environment and revisions

- **Hardware:** C3, NVIDIA B300 SXM6 AC (SM103a); one GPU for serial
timing. GPU UUID `GPU-55ba4050-98dc-a313-f475-531a0b6f7934`. An 8-GPU
devbox was allocated; validation used a separate GPU and completed
before counted measurements. Requested SM clock lock: 1980 MHz; memory
clock: 3996 MHz. Clock request is not a claim that every instantaneous
clock reading was exactly 1980 MHz.
- **Container:** `nvcr.io/nvidia/pytorch:26.05-py3`, selected as the
latest NGC PyTorch image with CUDA 13.2 when provisioning. Driver
`595.91.07`, nvcc `13.2.78`, PyTorch `2.12.0a0+5aff3928d8.nv26.05`,
Python `3.12.3`, g++ `13.3.0`, CUTLASS DSL `4.8.0`, TVM FFI
`0.1.15.post2`, `cupti-python==13.4.0`, `nvidia-cuda-cupti==13.4.92`.
- **Historical comparison:** exact parent
`03d7f4a399a47e72d93631e19becd804147fc47b`; merged #7501
`fb022756415cc9cad1e1a64ee918860e17638fe8`; that merged commit plus only
this PR's reciprocal-hoist header patch.
- **Causal comparison:** dispatch/scheduling changed between the
historical and main trees. The matched historical and main pairs isolate
this optimization from those intervening changes.
- **Upstream comparison:** baseline
`3472ad3ab194141353be7199807cb29f0d20af09`; measured PR
`9ac7ef83e8013cc0d37d5fd8ee62f325f211f6c4`. Benchmark review follow-up
`2bd125681b8d34c1835c1bd1916f8b9e3a630f6a` leaves the quantizer and test
files byte-for-byte unchanged. Performance tables and the full numerical
suite below remain evidence from `9ac7ef83`; the follow-up has separate
benchmark-mode validation below. Later upstream commits through
`c472a430bdc4f0196e042e58bbd92d4047b43fc8` do not change the measured
quantizer, dispatch, timing utility, or dedicated benchmark files.
- **Build:** native JIT uses `-O3 -use_fast_math -std=c++17` with
`compute_103a`/`sm_103a`; each arm has an isolated native/CuTe/Triton
cache.
- **Method:** six serial rounds with source-arm order rotated/reversed;
100 warmups and 1000 measured iterations per case/backend; CUPTI, CUDA
graphs, cold L2, seed 42, BF16, standard NVFP4 fast math, PDL disabled.
JIT/precompile runs are excluded. Every source arm runs the same
dedicated benchmark script from `9ac7ef83`. It derives the global scale
with its existing `make_nvfp4_global_scale` helper. CuTe timings are
retained as a control. Summaries are medians of the six run medians; raw
run medians and full precision samples are retained.
- **Supplemental batched cases:** the existing `flashinfer_benchmark.py`
exercises the exact `nvfp4_batched_quantize` API cases from #7962, with
global scale 1 and the same CUPTI/graph/cold-L2/repetition policy. These
results are reported separately because the dedicated backend comparison
uses `nvfp4_quantize`.

### SASS: why #7501 regressed and why the hoist helps

#7501 changed the standard-fast CUDA guard from `vecMax != 0` to
`fp8SFVal != 0`: a nonzero block maximum can still round to a zero E4M3
scale, so the encoded-byte check is needed for the numerical contract.
In the measured BF16/SF16 TMA specialization, this also changed the
dependency of the **global** reciprocal, although that reciprocal only
needs `SFScaleVal`.

Selected instructions dumped from the actual measured SM103a binaries
with `cuobjdump -arch sm_103a -fun <kernel-symbol> -sass
<fp4_quantization_103.so>`; intervening instructions and
instruction-encoding words are omitted. Here `R0` holds the global scale
and `R71` its reciprocal. Offsets identify instructions, not cycle
counts.

```text
Parent 03d7f4a — P3 comes from vecMax before the conversion:
/*2140*/     FSETP.NEU.FTZ.AND P3, PT, R69.reuse, RZ, PT;
/*2170*/     F2FP.SATFINITE.E4M3.F32.PACK_AB_MERGE_C R69, RZ, R69, RZ;
/*2180*/ @P3 MUFU.RCP R71, R0;

#7501 fb02275 — P3 now depends on the converted E4M3 byte:
/*2160*/     F2FP.SATFINITE.E4M3.F32.PACK_AB_MERGE_C R69, RZ, R69, RZ;
/*2170*/     LOP3.LUT P3, R64, R69, 0xff, RZ, 0xc0, !PT;
/*2190*/ @P3 MUFU.RCP R71, R0;

fb02275 + fix — global reciprocal is unconditional and scheduled earlier:
/*1ff0*/     MUFU.RCP R71, R0;
             ... block-maximum reduction and scale computation ...
/*21a0*/     F2FP.SATFINITE.E4M3.F32.PACK_AB_MERGE_C R69, RZ, R69, RZ;
/*21b0*/     LOP3.LUT P3, R64, R69, 0xff, RZ, 0xc0, !PT;
/*2200*/ @P3 FMUL.FTZ R66, R71, R66;
/*2240*/ @P3 MUFU.RCP R64, R66;
```

The fix removes the `E4M3 conversion → byte predicate → global
reciprocal` dependency and permits that reciprocal to overlap the
reduction/conversion work. The encoded-byte predicate still gates the
final scale computation, preserving zero-scale behavior and the original
multiply/reciprocal arithmetic. The main/PR binaries show the same
removal of predication (`@P3 MUFU.RCP R62, R2` at `0x24b0` becomes an
unconditional `MUFU.RCP R62, R2` at `0x2450`). This is scheduling
evidence consistent with the matched timing improvements below; no
instruction-latency or stall-cycle count is inferred from the dump.

**Results:** the dedicated sweep is 0.38–1.22% faster than #7501; five
of six shapes meet or beat the exact parent, while `M=2048, K=4096`
retains a 0.35% gap. All three exact issue cases recover past the parent
on the historical tree. On the main/PR pair, the dedicated sweep is flat
to 0.86% faster; the supplemental single case improves 1.16%, while the
two batched cases increase by about 32 ns (+0.26% and +0.05%). Those
small increases are retained in the results rather than reported as
universal recovery.

**Strict-mode control:** #7501 left the standard-strict `vecMax != 0`
guard, `__fdiv_rn` operations, and `FLT_MAX` clamp unchanged. We also
compiled an equivalent source hoist of `__fdiv_rn(1.0f, SFScaleVal)`
before strict scale construction. With the same CUDA 13.2/SM103a
toolchain, the complete quantization module's SASS is byte-for-byte
identical across both builds (605 function sections; SHA-256
`be35aae82417da9af8f0b12bf41015a5cd6e2b89bd395896a86fb627dd4f234d`). The
strict BF16 TMA kernel retains 72 registers and 0 local/stack bytes.
NVCC sinks the nonvolatile strict divide back into the nonzero-block
branch; the fast path's volatile inline PTX reciprocal stays hoisted.
This source-only strict extension is therefore excluded from the PR; no
strict performance improvement is claimed.

### Dedicated backend benchmark: CUDA latency (µs)

Lower is better. Each cell is the median of six run medians. `#7501 +
fix` changes only the reciprocal-hoist header code on the merged #7501
tree.

| M × K | Parent | #7501 | #7501 + fix | Regression vs parent | Fix vs
#7501 | Fix vs parent |
|---|---:|---:|---:|---:|---:|---:|
| 1024 × 4096 | 7.776 | 7.840 | 7.744 | +0.82% | -1.22% | -0.41% |
| 1024 × 7168 | 10.944 | 11.040 | 10.912 | +0.88% | -1.16% | -0.29% |
| 1024 × 8192 | 11.896 | 11.968 | 11.840 | +0.61% | -1.07% | -0.47% |
| 2048 × 4096 | 8.736 | 8.800 | 8.767 | +0.73% | -0.38% | +0.35% |
| 2048 × 7168 | 12.000 | 12.096 | 12.000 | +0.80% | -0.79% | +0.00% |
| 2048 × 8192 | 13.504 | 13.600 | 13.504 | +0.71% | -0.71% | +0.00% |

### Main baseline versus PR: CUDA latency (µs)

| M × K | Main baseline | PR | PR vs baseline |
|---|---:|---:|---:|
| 1024 × 4096 | 7.967 | 7.936 | -0.39% |
| 1024 × 7168 | 11.104 | 11.008 | -0.86% |
| 1024 × 8192 | 12.032 | 11.936 | -0.80% |
| 2048 × 4096 | 8.896 | 8.896 | -0.01% |
| 2048 × 7168 | 12.223 | 12.176 | -0.39% |
| 2048 × 8192 | 13.664 | 13.664 | +0.00% |

### Supplemental exact issue cases: CUDA latency (µs)

| API / shape | Parent | #7501 | #7501 + fix | Main baseline | PR | Fix
vs #7501 | PR vs main |
|---|---:|---:|---:|---:|---:|---:|---:|
| Single 1024 × 7168 | 10.848 | 10.944 | 10.816 | 11.008 | 10.880 |
-1.17% | -1.16% |
| B4 × 1024 × 4096 | 20.128 | 20.256 | 19.969 | 12.160 | 12.192 | -1.42%
| +0.26% |
| B8 × 2048 × 8192 | 74.304 | 74.729 | 73.961 | 62.369 | 62.401 | -1.03%
| +0.05% |

<details>
<summary>Complete raw dedicated-benchmark run medians, including CuTe
control (milliseconds)</summary>

Every run median below uses all 1000 exported timing samples. Precompile
runs are excluded. Values are listed in chronological run order; source
arms were interleaved.

| M × K | Backend | Source arm | R1 | R2 | R3 | R4 | R5 | R6 |
|---|---|---|---:|---:|---:|---:|---:|---:|
| 1024 × 4096 | cuda | Parent | 0.00777500 | 0.00777600 | 0.00777600 |
0.00777600 | 0.00774500 | 0.00777600 |
| 1024 × 4096 | cuda | #7501 | 0.00784000 | 0.00784000 | 0.00784000 |
0.00784000 | 0.00784000 | 0.00784000 |
| 1024 × 4096 | cuda | #7501 + fix | 0.00774400 | 0.00774500 |
0.00774500 | 0.00774400 | 0.00774400 | 0.00774500 |
| 1024 × 4096 | cuda | Main baseline | 0.00796700 | 0.00796800 |
0.00796700 | 0.00793700 | 0.00796800 | 0.00796750 |
| 1024 × 4096 | cuda | PR | 0.00793600 | 0.00793600 | 0.00793600 |
0.00793600 | 0.00793600 | 0.00790500 |
| 1024 × 4096 | cute-dsl | Parent | 0.00448000 | 0.00448000 | 0.00448000
| 0.00448000 | 0.00448000 | 0.00448000 |
| 1024 × 4096 | cute-dsl | #7501 | 0.00448000 | 0.00448000 | 0.00448000
| 0.00448000 | 0.00448000 | 0.00448000 |
| 1024 × 4096 | cute-dsl | #7501 + fix | 0.00448000 | 0.00448000 |
0.00448000 | 0.00448000 | 0.00448000 | 0.00448000 |
| 1024 × 4096 | cute-dsl | Main baseline | 0.00448000 | 0.00448000 |
0.00448000 | 0.00448000 | 0.00448000 | 0.00448000 |
| 1024 × 4096 | cute-dsl | PR | 0.00448000 | 0.00448000 | 0.00448000 |
0.00448000 | 0.00448000 | 0.00448000 |
| 1024 × 7168 | cuda | Parent | 0.01094400 | 0.01094400 | 0.01094400 |
0.01094400 | 0.01094400 | 0.01094400 |
| 1024 × 7168 | cuda | #7501 | 0.01104000 | 0.01104000 | 0.01104000 |
0.01100800 | 0.01104000 | 0.01100900 |
| 1024 × 7168 | cuda | #7501 + fix | 0.01091200 | 0.01091200 |
0.01091200 | 0.01091200 | 0.01091200 | 0.01091200 |
| 1024 × 7168 | cuda | Main baseline | 0.01110400 | 0.01110400 |
0.01110400 | 0.01110400 | 0.01110400 | 0.01110400 |
| 1024 × 7168 | cuda | PR | 0.01100800 | 0.01100800 | 0.01100800 |
0.01097700 | 0.01100800 | 0.01100800 |
| 1024 × 7168 | cute-dsl | Parent | 0.00640000 | 0.00640000 | 0.00640000
| 0.00640000 | 0.00640000 | 0.00643200 |
| 1024 × 7168 | cute-dsl | #7501 | 0.00640000 | 0.00640000 | 0.00640000
| 0.00640000 | 0.00643100 | 0.00640000 |
| 1024 × 7168 | cute-dsl | #7501 + fix | 0.00640000 | 0.00640000 |
0.00646400 | 0.00640000 | 0.00640000 | 0.00643100 |
| 1024 × 7168 | cute-dsl | Main baseline | 0.00640000 | 0.00643200 |
0.00640000 | 0.00640000 | 0.00640000 | 0.00640000 |
| 1024 × 7168 | cute-dsl | PR | 0.00640000 | 0.00640000 | 0.00640000 |
0.00640000 | 0.00640000 | 0.00640000 |
| 1024 × 8192 | cuda | Parent | 0.01188800 | 0.01190400 | 0.01187200 |
0.01190300 | 0.01190350 | 0.01187200 |
| 1024 × 8192 | cuda | #7501 | 0.01193700 | 0.01196800 | 0.01196800 |
0.01196800 | 0.01193700 | 0.01196800 |
| 1024 × 8192 | cuda | #7501 + fix | 0.01184000 | 0.01184000 |
0.01184000 | 0.01184000 | 0.01184000 | 0.01184000 |
| 1024 × 8192 | cuda | Main baseline | 0.01200100 | 0.01203200 |
0.01203200 | 0.01203200 | 0.01203200 | 0.01203200 |
| 1024 × 8192 | cuda | PR | 0.01193600 | 0.01193600 | 0.01193600 |
0.01193600 | 0.01193600 | 0.01193600 |
| 1024 × 8192 | cute-dsl | Parent | 0.00662400 | 0.00659300 | 0.00662400
| 0.00662350 | 0.00659300 | 0.00662300 |
| 1024 × 8192 | cute-dsl | #7501 | 0.00665600 | 0.00659300 | 0.00662400
| 0.00659300 | 0.00662300 | 0.00662400 |
| 1024 × 8192 | cute-dsl | #7501 + fix | 0.00662400 | 0.00662400 |
0.00662400 | 0.00662500 | 0.00662400 | 0.00662350 |
| 1024 × 8192 | cute-dsl | Main baseline | 0.00662400 | 0.00662400 |
0.00662400 | 0.00659300 | 0.00659300 | 0.00662400 |
| 1024 × 8192 | cute-dsl | PR | 0.00662300 | 0.00659300 | 0.00662400 |
0.00659300 | 0.00662400 | 0.00659300 |
| 2048 × 4096 | cuda | Parent | 0.00873600 | 0.00873700 | 0.00873600 |
0.00873600 | 0.00873600 | 0.00873600 |
| 2048 × 4096 | cuda | #7501 | 0.00880000 | 0.00880000 | 0.00880000 |
0.00880000 | 0.00880000 | 0.00880000 |
| 2048 × 4096 | cuda | #7501 + fix | 0.00876700 | 0.00876700 |
0.00876800 | 0.00876800 | 0.00876700 | 0.00873700 |
| 2048 × 4096 | cuda | Main baseline | 0.00889600 | 0.00889600 |
0.00892800 | 0.00889700 | 0.00889600 | 0.00892800 |
| 2048 × 4096 | cuda | PR | 0.00889600 | 0.00889600 | 0.00889600 |
0.00889600 | 0.00892800 | 0.00889600 |
| 2048 × 4096 | cute-dsl | Parent | 0.00659200 | 0.00659200 | 0.00659200
| 0.00659200 | 0.00659200 | 0.00659200 |
| 2048 × 4096 | cute-dsl | #7501 | 0.00659200 | 0.00656100 | 0.00659200
| 0.00656100 | 0.00659200 | 0.00656000 |
| 2048 × 4096 | cute-dsl | #7501 + fix | 0.00659200 | 0.00656000 |
0.00659200 | 0.00659200 | 0.00659200 | 0.00659200 |
| 2048 × 4096 | cute-dsl | Main baseline | 0.00659100 | 0.00659200 |
0.00659200 | 0.00659200 | 0.00659200 | 0.00659200 |
| 2048 × 4096 | cute-dsl | PR | 0.00659200 | 0.00659200 | 0.00656000 |
0.00656000 | 0.00659200 | 0.00659200 |
| 2048 × 7168 | cuda | Parent | 0.01200000 | 0.01200000 | 0.01200000 |
0.01200000 | 0.01200000 | 0.01200000 |
| 2048 × 7168 | cuda | #7501 | 0.01209600 | 0.01209600 | 0.01209600 |
0.01209600 | 0.01209600 | 0.01209600 |
| 2048 × 7168 | cuda | #7501 + fix | 0.01200000 | 0.01200000 |
0.01200000 | 0.01200000 | 0.01200000 | 0.01200000 |
| 2048 × 7168 | cuda | Main baseline | 0.01219300 | 0.01222400 |
0.01222400 | 0.01224000 | 0.01219300 | 0.01222300 |
| 2048 × 7168 | cuda | PR | 0.01216000 | 0.01216000 | 0.01216000 |
0.01219150 | 0.01219200 | 0.01219200 |
| 2048 × 7168 | cute-dsl | Parent | 0.00995200 | 0.00995200 | 0.00992000
| 0.00992000 | 0.00995200 | 0.00995200 |
| 2048 × 7168 | cute-dsl | #7501 | 0.00992000 | 0.00993600 | 0.00995200
| 0.00995200 | 0.00995200 | 0.00992050 |
| 2048 × 7168 | cute-dsl | #7501 + fix | 0.00995200 | 0.00993600 |
0.00992000 | 0.00995200 | 0.00995200 | 0.00995200 |
| 2048 × 7168 | cute-dsl | Main baseline | 0.00995200 | 0.00995200 |
0.00992000 | 0.00995200 | 0.00992000 | 0.00995100 |
| 2048 × 7168 | cute-dsl | PR | 0.00992000 | 0.00995200 | 0.00992000 |
0.00995100 | 0.00992100 | 0.00992000 |
| 2048 × 8192 | cuda | Parent | 0.01350400 | 0.01350400 | 0.01350400 |
0.01350400 | 0.01350500 | 0.01350400 |
| 2048 × 8192 | cuda | #7501 | 0.01360000 | 0.01356800 | 0.01356800 |
0.01360000 | 0.01360000 | 0.01360000 |
| 2048 × 8192 | cuda | #7501 + fix | 0.01350400 | 0.01350400 |
0.01350400 | 0.01347300 | 0.01350400 | 0.01350400 |
| 2048 × 8192 | cuda | Main baseline | 0.01366400 | 0.01369600 |
0.01366400 | 0.01366400 | 0.01369600 | 0.01366400 |
| 2048 × 8192 | cuda | PR | 0.01366400 | 0.01366400 | 0.01366400 |
0.01366400 | 0.01366400 | 0.01366400 |
| 2048 × 8192 | cute-dsl | Parent | 0.01081600 | 0.01081600 | 0.01081600
| 0.01081600 | 0.01081600 | 0.01081600 |
| 2048 × 8192 | cute-dsl | #7501 | 0.01081600 | 0.01078500 | 0.01081650
| 0.01081600 | 0.01081600 | 0.01081600 |
| 2048 × 8192 | cute-dsl | #7501 + fix | 0.01081700 | 0.01081600 |
0.01081600 | 0.01081600 | 0.01081600 | 0.01084800 |
| 2048 × 8192 | cute-dsl | Main baseline | 0.01081600 | 0.01081600 |
0.01081600 | 0.01081600 | 0.01081600 | 0.01081600 |
| 2048 × 8192 | cute-dsl | PR | 0.01081600 | 0.01081600 | 0.01081600 |
0.01081600 | 0.01081600 | 0.01078500 |

</details>

<details>
<summary>Complete raw supplemental run medians (milliseconds)</summary>

| API / shape | Source arm | R1 | R2 | R3 | R4 | R5 | R6 |
|---|---|---:|---:|---:|---:|---:|---:|
| Single 1024 × 7168 | Parent | 0.01084800 | 0.01084800 | 0.01084800 |
0.01084800 | 0.01084800 | 0.01084800 |
| Single 1024 × 7168 | #7501 | 0.01094400 | 0.01094400 | 0.01094400 |
0.01091300 | 0.01094400 | 0.01094400 |
| Single 1024 × 7168 | #7501 + fix | 0.01081600 | 0.01081600 |
0.01081600 | 0.01081600 | 0.01081600 | 0.01081600 |
| Single 1024 × 7168 | Main baseline | 0.01100800 | 0.01100800 |
0.01100800 | 0.01100800 | 0.01100800 | 0.01100800 |
| Single 1024 × 7168 | PR | 0.01088000 | 0.01088000 | 0.01088000 |
0.01088000 | 0.01088000 | 0.01088000 |
| B4 × 1024 × 4096 | Parent | 0.02012800 | 0.02009650 | 0.02012750 |
0.02012800 | 0.02012800 | 0.02009600 |
| B4 × 1024 × 4096 | #7501 | 0.02025600 | 0.02025600 | 0.02025600 |
0.02025600 | 0.02025600 | 0.02025600 |
| B4 × 1024 × 4096 | #7501 + fix | 0.01996900 | 0.02000000 | 0.01996900
| 0.01996800 | 0.01996800 | 0.02000000 |
| B4 × 1024 × 4096 | Main baseline | 0.01216000 | 0.01216000 |
0.01216000 | 0.01216000 | 0.01216000 | 0.01219100 |
| B4 × 1024 × 4096 | PR | 0.01219200 | 0.01216100 | 0.01219200 |
0.01219200 | 0.01219100 | 0.01219200 |
| B8 × 2048 × 8192 | Parent | 0.07433700 | 0.07430400 | 0.07430400 |
0.07430400 | 0.07430500 | 0.07430400 |
| B8 × 2048 × 8192 | #7501 | 0.07472100 | 0.07472100 | 0.07473650 |
0.07475300 | 0.07472100 | 0.07476850 |
| B8 × 2048 × 8192 | #7501 + fix | 0.07395300 | 0.07398400 | 0.07396850
| 0.07392100 | 0.07398400 | 0.07392000 |
| B8 × 2048 × 8192 | Main baseline | 0.06235250 | 0.06233700 |
0.06240050 | 0.06236900 | 0.06246400 | 0.06236900 |
| B8 × 2048 × 8192 | PR | 0.06240100 | 0.06236900 | 0.06246400 |
0.06236800 | 0.06240100 | 0.06243200 |

</details>


### Reproduction

Run inside `nvcr.io/nvidia/pytorch:26.05-py3`, preserving its
PyTorch/CUDA installation. Each source arm has its own checkout and JIT
cache. This script pins the measured `9ac7ef83` dedicated benchmark for
every arm. The benchmark review follow-up can be checked with the
commands below.

```bash
mkdir -p nvfp4-regression
cd nvfp4-regression
NVFP4_WORKSPACE_ROOT="$PWD"
mkdir -p "$NVFP4_WORKSPACE_ROOT/results" "$NVFP4_WORKSPACE_ROOT/caches"
git clone --recursive https://github.com/flashinfer-ai/flashinfer.git flashinfer
git -C flashinfer fetch https://github.com/zianglih/flashinfer.git \
  9ac7ef83e8013cc0d37d5fd8ee62f325f211f6c4
git -C flashinfer checkout --detach 9ac7ef83e8013cc0d37d5fd8ee62f325f211f6c4
git -C flashinfer worktree add --detach ../before 03d7f4a399a47e72d93631e19becd804147fc47b
git -C flashinfer worktree add --detach ../regressed fb022756415cc9cad1e1a64ee918860e17638fe8
git -C flashinfer worktree add --detach ../historical-fixed fb022756415cc9cad1e1a64ee918860e17638fe8
git -C flashinfer worktree add --detach ../main-before 3472ad3ab194141353be7199807cb29f0d20af09
git -C flashinfer diff 3472ad3 9ac7ef83 -- \
  csrc/nv_internal/tensorrt_llm/kernels/quantization_utils.cuh | \
  git -C historical-fixed apply

PIP_CONSTRAINT= python -m pip install \
  apache-tvm-ffi==0.1.15.post2 'nvidia-cutlass-dsl[cu13]==4.8.0' \
  nvidia-cudnn-frontend==1.32.0 cuda-tile==1.7.0 \
  cupti-python==13.4.0 nvidia-cuda-cupti==13.4.92 \
  pytest==9.2.0 ninja==1.13.2 pre-commit==4.6.1 einops tabulate packaging
for arm in before regressed historical-fixed main-before flashinfer; do
  git -C "$arm" submodule update --init 3rdparty/cutlass 3rdparty/spdlog 3rdparty/cccl
  (cd "$NVFP4_WORKSPACE_ROOT/$arm" && \
    BUILD_NVEP=0 PIP_CONSTRAINT= python -m pip install --no-deps --no-build-isolation -e .)
done

export CUDA_VISIBLE_DEVICES=0 FLASHINFER_CUDA_ARCH_LIST=10.3a
export MAX_JOBS=8 FLASHINFER_NVCC_THREADS=2 OMP_NUM_THREADS=1
export TRTLLM_ENABLE_PDL=0 FLASHINFER_DISABLE_FP4_QUANT_FAST_MATH=0
export TRTLLM_DISABLE_FP4_QUANT_FAST_MATH=0
# Remove inherited recipe-selection variables, including legacy aliases.
for name in $(compgen -v | grep -E '^(FLASHINFER|TRTLLM)_NVFP4_4OVER6'); do
  unset "$name"
done
nvidia-smi -i 0 -lgc 1980,1980
NVFP4_PR_RUNNER="$NVFP4_WORKSPACE_ROOT/flashinfer/benchmarks/bench_nvfp4_quantize_backend_comparison.py"

run_nvfp4_arm() {
  local arm="$1" round="$2" warmups="$3" iterations="$4"
  (
    cd "$NVFP4_WORKSPACE_ROOT/$arm"
    export PYTHONPATH="$PWD"
    export FLASHINFER_WORKSPACE_BASE="$NVFP4_WORKSPACE_ROOT/caches/$arm/native"
    export CUTE_DSL_CACHE_DIR="$NVFP4_WORKSPACE_ROOT/caches/$arm/cute"
    export TRITON_CACHE_DIR="$NVFP4_WORKSPACE_ROOT/caches/$arm/triton"
    python "$NVFP4_PR_RUNNER" \
      --m-values 1024 2048 --k-values 4096 7168 8192 \
      --layouts swizzled_128x4 --dtype bfloat16 --seed 42 \
      --num-iters "$iterations" --dry-run-iters "$warmups" --cuda-graph \
      --csv-output "$NVFP4_WORKSPACE_ROOT/results/$arm-r$round.csv" --no-heatmap
  )
}
# Compilation/warmup is excluded from measured results.
for arm in before regressed historical-fixed main-before flashinfer; do
  run_nvfp4_arm "$arm" 0 1 1
done
orders=(
  'before regressed historical-fixed main-before flashinfer'
  'before flashinfer main-before historical-fixed regressed'
  'historical-fixed main-before flashinfer before regressed'
  'historical-fixed regressed before flashinfer main-before'
  'flashinfer before regressed historical-fixed main-before'
  'flashinfer main-before historical-fixed regressed before'
)
round=1
for order in "${orders[@]}"; do
  for arm in $order; do run_nvfp4_arm "$arm" "$round" 100 1000; done
  round=$((round + 1))
done
```

Every measured dedicated CSV has 12,000 rows: six shapes × two backends
× 1000 samples. Require successful backend verification and no CUPTI
fallback. The historical-fixed header used for measurement has the same
executable changes as the patch above; comments/formatting do not affect
its measured instructions.

Supplemental exact issue cases use the existing unified runner. The
following writes its testlist and runs one arm/round; repeat across the
same five arms for six serial rounds with unique output files and
isolated caches.

```bash
cat > "$NVFP4_WORKSPACE_ROOT/issue-cases.txt" <<'CASES'
--routine nvfp4_quantize --m 1024 --k 7168 --input_dtype bfloat16 --global_scale 1.0 --sf_vec_size 16 --backends cuda --sf_layout 128x4 --random_seed 42 --num_iters 1000 --dry_run_iters 100 --use_cupti --case_tag nvfp4_m1024_k7168
--routine nvfp4_batched_quantize --batch_size 4 --m 1024 --k 4096 --input_dtype bfloat16 --global_scale 1.0 --sf_vec_size 16 --backends cuda --random_seed 42 --num_iters 1000 --dry_run_iters 100 --use_cupti --case_tag nvfp4_batched_basic
--routine nvfp4_batched_quantize --batch_size 8 --m 2048 --k 8192 --input_dtype bfloat16 --global_scale 1.0 --sf_vec_size 16 --backends cuda --random_seed 42 --num_iters 1000 --dry_run_iters 100 --use_cupti --case_tag nvfp4_batched_large
CASES
arm=flashinfer
round=1
(
  cd "$NVFP4_WORKSPACE_ROOT/$arm"
  export PYTHONPATH="$PWD"
  export FLASHINFER_WORKSPACE_BASE="$NVFP4_WORKSPACE_ROOT/caches/$arm/native"
  export CUTE_DSL_CACHE_DIR="$NVFP4_WORKSPACE_ROOT/caches/$arm/cute"
  python benchmarks/flashinfer_benchmark.py \
    --testlist "$NVFP4_WORKSPACE_ROOT/issue-cases.txt" \
    --output_path "$NVFP4_WORKSPACE_ROOT/results/issue-$arm-r$round.csv"
)
# Validate the actual PR checkout. GPU1 was used for these tests.
cd "$NVFP4_WORKSPACE_ROOT/flashinfer"
export PYTHONPATH="$PWD"
export FLASHINFER_WORKSPACE_BASE="$NVFP4_WORKSPACE_ROOT/caches/flashinfer/native"
export CUTE_DSL_CACHE_DIR="$NVFP4_WORKSPACE_ROOT/caches/flashinfer/cute"
CUDA_VISIBLE_DEVICES=1 python -m pytest -q --disable-warnings \
  tests/utils/test_fp4_quantize.py tests/utils/test_fp4_quantize_padding.py
CUDA_VISIBLE_DEVICES=1 python -m pytest -q --disable-warnings \
  tests/utils/test_fp4_quantize.py::test_nvfp4_quantize_cute_dsl_device_scale_cuda_graph
pre-commit run --all-files
nvidia-smi -i 0 -rgc
```

### Test results and limitations

```text
PR 9ac7ef83 — full FP4 quantization + padding files:
1 failed, 1507 passed, 628 warnings in 233.19s (0:03:53)

Unmodified main 3472ad3 — same two files, without the 12 new cases:
1 failed, 1495 passed, 628 warnings in 278.54s (0:04:38)

PR 9ac7ef83 — isolated CuTe graph test:
1 passed, 20 warnings in 1.56s

pre-commit run --all-files: all checks passed
Dedicated benchmark CLI integration checks: comparison, bandwidth,
default timing controls, per-sample precision, and invalid arguments passed.
GPU bandwidth-mode smoke test: 3 measured samples exported successfully.
```

The sole combined-suite failure in both trees is
`test_nvfp4_quantize_cute_dsl_device_scale_cuda_graph[cuda:0]`: the
first output `torch.empty` during graph capture raises
`cudaErrorStreamCaptureUnsupported`, before the CuTe kernel launch. It
also passes in isolation on the baseline. This is a reproduced existing
suite-context failure; its underlying allocator/capture interaction is
not diagnosed here. All 12 new boundary cases passed, as did the rest of
both files. The complete-suite checkbox remains unchecked for this
reason.


### Benchmark review validation

- **Follow-up:** `2bd125681b8d34c1835c1bd1916f8b9e3a630f6a`; only the
dedicated benchmark changes. The benchmark diff against main shrinks
from 214 to 152 changed lines while retaining the reproduction options.
No `--fail-on-error` option is added.
- **C3 checks:** same B300/container/software above, BF16 M128×K64,
layout128x4, one warmup and three measured samples per backend. Each
case runs in a separate process. These are functional checks, not new
performance comparisons. The source SHA-256 is
`5535996f9117e89c457fae73155ff0eb6e819a7ef347a1fe26ff011cd907108b`.
- **Failure injection:** process-local CUPTI import failures
(`ModuleNotFoundError` and a multiline `RuntimeError`) and a mocked
`cupti-python` version of `12.0.0`. All three graph cases raise before
the event fallback and export zero rows; eager fallback still completes
with cold-L2 flushing. No package installation is changed.

```text
per-token-graph:             PASS, exit=0, rows=6
standard-graph:              PASS, exit=0, rows=6
graph-missing-cupti:         PASS, exit=1, rows=0 (expected rejection)
graph-old-cupti:             PASS, exit=1, rows=0 (expected rejection)
graph-multiline-cupti-error:  PASS, exit=1, rows=0 (expected rejection)
eager-missing-cupti:         PASS, exit=0, rows=6
bandwidth-graph:             PASS, exit=0, rows=3

CPU CLI checks: comparison (6 rows), bandwidth (3 rows), default timing
(60 rows), full sample precision, identical input seeds, and 4 invalid
shape/iteration controls passed.
pre-commit run --all-files: all checks passed
```

<details>
<summary>Reproduce the benchmark-mode checks</summary>

After the environment setup above, check out
`2bd125681b8d34c1835c1bd1916f8b9e3a630f6a`. Run from the checkout with
`PYTHONPATH="$PWD"`. This loop handles the three expected fallback
exceptions and verifies the exported sample counts.

```bash
git fetch https://github.com/zianglih/flashinfer.git 2bd125681b8d34c1835c1bd1916f8b9e3a630f6a
git checkout --detach 2bd125681b8d34c1835c1bd1916f8b9e3a630f6a
export PYTHONPATH="$PWD" FLASHINFER_NVCC_THREADS=1
for mode in per-token standard missing old multiline eager-missing bandwidth; do
  NVFP4_REVIEW_MODE="$mode" python - <<'PY'
import builtins, csv, importlib.metadata, os, pathlib, runpy, sys
mode = os.environ["NVFP4_REVIEW_MODE"]
script = "benchmarks/bench_nvfp4_quantize_backend_comparison.py"
output = pathlib.Path(f"review-{mode}.csv")
reject = mode in ("missing", "old", "multiline")
if mode in ("missing", "eager-missing", "multiline"):
    original_import = builtins.__import__
    def injected_import(name, *args, **kwargs):
        if name == "cupti" or name.startswith("cupti."):
            if mode == "multiline":
                raise RuntimeError("line one\nline two")
            raise ModuleNotFoundError("CUPTI intentionally absent")
        return original_import(name, *args, **kwargs)
    builtins.__import__ = injected_import
elif mode == "old":
    original_version = importlib.metadata.version
    importlib.metadata.version = lambda name: (
        "12.0.0" if name == "cupti-python" else original_version(name)
    )
sys.argv = [script, "--m-values", "128", "--k-values", "64",
            "--dtype", "bfloat16", "--layouts", "swizzled_128x4",
            "--num-iters", "3", "--dry-run-iters", "1", "--seed", "42",
            "--no-heatmap", "--csv-output", str(output)]
if mode != "eager-missing":
    sys.argv.append("--cuda-graph")
if mode == "per-token":
    sys.argv.append("--per-token-activation")
if mode == "bandwidth":
    sys.argv.append("--bandwidth")
try:
    runpy.run_path(script, run_name="__main__")
except UserWarning as exc:
    assert reject and "Falling back to CUDA events for benchmarking." in str(exc)
else:
    assert not reject
with output.open(newline="") as stream:
    rows = list(csv.DictReader(stream))
assert len(rows) == (0 if reject else 3 if mode == "bandwidth" else 6)
assert all(row["cold_l2_cache"] == "True" for row in rows)
print(f"PASS: {mode}, rows={len(rows)}")
PY
done
```

</details>


## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).

Suggested CI test targets: `tests/utils/test_fp4_quantize.py
tests/utils/test_fp4_quantize_padding.py`

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

Performance evidence is from B300/SM103a and the pinned CUDA 13.2
compiler. Other GPU architectures and compiler versions have not been
benchmarked. No end-to-end model benchmark is claimed. Eager timing can
fall back to CUDA events with L2 flushing. Graph timing requires CUPTI
and raises on its fallback warning before exporting samples. The
reported measurements all used CUPTI; the campaign also rejected failed
correctness checks, missing configurations, or missing samples.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added configurable shape sweeps, warmup and timing iterations, CUDA
graph replay, reproducible inputs, and CSV output with per-sample
timings and run details for NVFP4 benchmarks.
  * Added an option to skip heatmap generation.
* **Bug Fixes**
* Improved NVFP4 quantization accuracy near the zero-scale boundary,
with consistent results across standard and batched quantization.
* Added validation for benchmark dimensions, iteration counts, and
K-dimension divisibility.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [80ece84](https://github.com/flashinfer-ai/flashinfer/commit/80ece849ce79daa38cdb767b8cedf66908357b4a)

- **作者**: Hanlin Bi
- **时间**: 2026-10-30T20:21:07Z
- **提交信息**: perf(quantization): launch MXFP8 consumers earlier with PDL (#5982)

<!-- .github/pull_request_template.md -->

## 📌 Description

Signal PDL consumers immediately after the swizzled MXFP8 quantizer's
upstream wait, allowing GEMM initialization to overlap quantization.
Quantization arithmetic and dependency waits are unchanged; the
production change adds one executable line and one comment. A CUDA-graph
regression test covers changing-input quantization followed by the
CuTe-DSL GEMM.

**GB200 quant → GEMM:** M/N/K = 4/6144/1024, fixed split-K=4 tactic,
CUDA Graphs, rotating weights exceeding 2×L2, three paired rounds:
**8.559 → 8.175 µs**, a **4.51%** median paired latency reduction.

**Fixed-tactic serving:** MiniMax-M3-NVFP4, vLLM `9ea8f3ffc`, 8×GB200,
TP8/EP1, AGG, CUDA Graphs, MTP/prefix caching off. Three paired rounds;
24 runs / 1,536 requests; no observed JIT in measured windows and no
exclusions. Median paired latency changes (negative is better):

| Input/output tokens | Concurrency | TPOT | Request latency | TTFT |
|---|---:|---:|---:|---:|
| 128/1024 | 1 | −0.96% | −0.88% | +0.63% |
| 128/1024 | 16 | −2.01% | −1.85% | +0.84% |
| 8192/1024 | 1 | −0.92% | −0.83% | +0.76% |
| 8192/1024 | 16 | −1.76% | −1.47% | +0.41% |

TPOT, request latency, and TPOT P95/P99 improved in all 12 paired
comparisons. TTFT shows a small regression. These are measurements on
one allocation. Microbenchmark latencies are medians of round medians;
its percentage is the median paired change.

## 🔍 Related Issues

None. No duplicate standalone-quantizer PDL change found in the open-PR
search.

<details>
<summary>PR checklist</summary>

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

</details>

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

- Historical validation on the measured serving-image source: 72
changing-input CUDA Graph checks on GB200, exact FP8/scale bytes,
BF16/FP16, both swizzled layouts, including padded rows.
- Passed on `d63be2f1`: `pytest tests/gemm/test_mm_mxfp8.py -k
test_mm_mxfp8_cute_dsl_quantize_pdl_cuda_graph --full -v` — **6 passed**
on one GB200, CUDA 13.4, PyTorch `2.15.0.dev20260923+cu134`, CuTe DSL
4.7.0. Shapes M/N/K = 4/6144/1024, 129/256/4096, 2048/256/4096, each in
BF16 and FP16. Eight changing-input replays per case compare FP8
payload, scale, and output bytes against a synchronized reference using
the same GEMM tactic; captured buffers are poisoned before replay.
- Scoped internal CI was [requested on this
head](https://github.com/flashinfer-ai/flashinfer/pull/5982#issuecomment-6454717225),
but the [bot rejected the request because `wolfcomos` is not
authorized](https://github.com/flashinfer-ai/flashinfer/pull/5982#issuecomment-6454723090).
An authorized maintainer still needs to run
`tests/utils/test_fp8_quantize.py tests/gemm/test_mm_mxfp8.py`.
- Passed on this PR head: `pre-commit run --files
flashinfer/quantization/kernels/mxfp8_quantize.py
tests/gemm/test_mm_mxfp8.py` and `git diff --check`.

<details>
<summary>Experimental track template — not applicable</summary>

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

</details>

## Reviewer Notes

Performance results above use the measured FlashInfer 0.7.0.post1
serving-image source with this patch. The new graph regression passed on
PR head `d63be2f1`; performance was not remeasured. FP32/additional
architectures and the scoped internal CI run remain pending. The
`cutedsl_low_latency` weight-operand wait remains a separate consumer
fix and merge-sequencing discussion; the added test uses the ordinary
`cute-dsl` GEMM requested in review. AI-assisted implementation,
testing, and benchmark preparation.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* MXFP8 quantization can now allow dependent GPU work to begin earlier
when PDL is enabled, while preserving synchronization before dependent
operations read the results.
* **Bug Fixes**
* Improved reliability of MXFP8 quantization followed by GEMM in CUDA
graphs, including across changing input magnitudes and supported input
types.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Hanlin Bi <hanlinb@nvidia.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: flashinfer-bot <flashinfer-bot@users.noreply.github.com>

### [c2f7902](https://github.com/flashinfer-ai/flashinfer/commit/c2f7902d64e4d736f3a3da0e6cf16c709838273b)

- **作者**: Adrian
- **时间**: 2026-10-30T19:38:37Z
- **提交信息**: ci: fail communication test wrappers on missing results (#8026)

<!-- .github/pull_request_template.md -->

## 📌 Description

A communication-test worker can segfault before writing JUnit, be
reported as `No result: 1`, and still leave the wrapper exit status at
zero. This was observed in the VR multi-node lane.

Mark no-result files as unsuccessful while retaining their separate
diagnostic summary. Crashes, missing JUnit output and file timeouts now
fail the wrapper even when optional completion reporting is disabled.
Strengthen the existing wrapper assertions and add regression coverage
for real pytest crashes in full/sanity modes and a file timeout.

## 🔍 Related Issues

No separate tracking issue.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

Changed-file hooks passed at commit time; repository-wide hooks were not
run.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- **43 CPU tests pass**:
  ```bash
  python -m pytest --confcutdir=tests/test_sharding \
    tests/test_sharding/test_test_run_status.py \
    tests/test_sharding/test_shell_entrypoint.py -q
  ```
- Regression checks fail before the fix because the wrapper returns
zero, then pass afterward.
- Bash syntax, Ruff lint/format and `git diff --check` pass; commit
hooks passed.

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/test_sharding/test_test_run_status.py
tests/test_sharding/test_shell_entrypoint.py`

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

The change propagates unsuccessful execution; it does not fix the
underlying worker segfault. The existing completion-report tests still
distinguish completed assertion failures from incomplete/crashed runs
for cache publication. The listed coordinator tests are CPU-only and
were run locally with `--confcutdir`; nightly GPU discovery normally
excludes `tests/test_sharding`. AI-assisted.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Test runs now fail with a nonzero exit status when a test file
produces no result artifacts, including when reporting is disabled.
* Missing results are identified in the output, helping surface crashes
and timeouts instead of allowing the CI job to pass.

* **Tests**
* Added coverage for missing-result behavior across full and sanity test
runs, including a timed-out full run.

* **Documentation**
* Clarified that missing results and file timeouts still fail the
wrapper when reporting is disabled, and that CPU tests cover this
behavior without GPU dependencies.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [fcf68a8](https://github.com/flashinfer-ai/flashinfer/commit/fcf68a8622358f0d66a474e0fc24ca58afbe06bf)

- **作者**: eigen
- **时间**: 2026-10-30T19:35:16Z
- **提交信息**: perf(cake_kimi_k3_fused_router): faster one-token routing on GB300 (#8031)

`flashinfer.fused_moe.kimi_k3_fused_router` is FlashInfer's experimental
Kimi-K3 fused MoE router. It takes FP32 gate logits and bias (896
experts, top-16). In one launch, it selects the top-16 experts per token
and builds the `moe_align_block_size` route plan that grouped MoE GEMMs
consume. Its one variant, FP32 logits and bias with `block_m` 8 and 16,
is covered on sm_100a and sm_103a. This PR changes the 1-token cells at
`block_m` 8 and 16 on sm_103a. Their programs now rank their 16 winners
from a certified window, and the idle warps zero the expert counts and
scatter offsets while the winners are ranked. Outputs are bitwise
identical to FlashInfer main. No other cell's device program changes on
either GPU, so sm_100a is unchanged. "FlashInfer main" in the tables is
the previous Cake version of this kernel: the router programs FlashInfer
main ships today (from #8016; its sm_103a programs are those of #7941).
On GB300, the 1-token cell drops from 2.704 us to 2.576 us at `block_m`
8 (1.05x) and from 2.656 us to 2.560 us at `block_m` 16 (1.04x).

NVIDIA GB300 (sm_103a, 152 SMs), CUDA 13.4, median kernel latency per
cell (28 cells), median over 3 GB300 nodes of per-node medians; speedup
= FlashInfer main / this PR. `new` marks the 2 cells whose device
program this PR changes, with both programs measured in the same
process. `same` cells run a byte-identical program, so both columns hold
one measurement of that unchanged program and their 1.00x is not a
speedup.

| tokens | block_m | FlashInfer main (us) | this PR (us) | speedup |
kernel |
|---:|---:|---:|---:|---:|---|
| 1 | 8 | 2.704 | 2.576 | 1.05x | new |
| 1 | 16 | 2.656 | 2.560 | 1.04x | new |
| 2 | 8 | 3.088 | 3.088 | 1.00x | same |
| 2 | 16 | 3.040 | 3.040 | 1.00x | same |
| 4 | 8 | 2.928 | 2.928 | 1.00x | same |
| 4 | 16 | 3.040 | 3.040 | 1.00x | same |
| 8 | 8 | 3.184 | 3.184 | 1.00x | same |
| 8 | 16 | 3.328 | 3.328 | 1.00x | same |
| 16 | 8 | 3.104 | 3.104 | 1.00x | same |
| 16 | 16 | 3.168 | 3.168 | 1.00x | same |
| 32 | 8 | 3.424 | 3.424 | 1.00x | same |
| 32 | 16 | 3.392 | 3.392 | 1.00x | same |
| 64 | 8 | 5.088 | 5.088 | 1.00x | same |
| 64 | 16 | 4.896 | 4.896 | 1.00x | same |
| 128 | 8 | 5.376 | 5.376 | 1.00x | same |
| 128 | 16 | 5.408 | 5.408 | 1.00x | same |
| 256 | 8 | 5.584 | 5.584 | 1.00x | same |
| 256 | 16 | 5.632 | 5.632 | 1.00x | same |
| 512 | 8 | 6.976 | 6.976 | 1.00x | same |
| 512 | 16 | 7.072 | 7.072 | 1.00x | same |
| 1024 | 8 | 8.928 | 8.928 | 1.00x | same |
| 1024 | 16 | 8.960 | 8.960 | 1.00x | same |
| 2048 | 8 | 11.776 | 11.776 | 1.00x | same |
| 2048 | 16 | 11.904 | 11.904 | 1.00x | same |
| 4096 | 8 | 16.416 | 16.416 | 1.00x | same |
| 4096 | 16 | 16.577 | 16.577 | 1.00x | same |
| 8192 | 8 | 21.712 | 21.712 | 1.00x | same |
| 8192 | 16 | 21.680 | 21.680 | 1.00x | same |

NVIDIA B200 (sm_100a, 148 SMs), CUDA 13.4, median kernel latency per
cell (28 cells); speedup = FlashInfer main / this PR. This PR changes no
device program on sm_100a, so every cell is `same`: both columns hold
one measurement of the unchanged program, and the 1.00x is not a
speedup.

| tokens | block_m | FlashInfer main (us) | this PR (us) | speedup |
kernel |
|---:|---:|---:|---:|---:|---|
| 1 | 8 | 2.655 | 2.655 | 1.00x | same |
| 1 | 16 | 2.591 | 2.591 | 1.00x | same |
| 2 | 8 | 3.039 | 3.039 | 1.00x | same |
| 2 | 16 | 3.056 | 3.056 | 1.00x | same |
| 4 | 8 | 3.216 | 3.216 | 1.00x | same |
| 4 | 16 | 2.976 | 2.976 | 1.00x | same |
| 8 | 8 | 3.264 | 3.264 | 1.00x | same |
| 8 | 16 | 3.232 | 3.232 | 1.00x | same |
| 16 | 8 | 3.200 | 3.200 | 1.00x | same |
| 16 | 16 | 3.296 | 3.296 | 1.00x | same |
| 32 | 8 | 3.552 | 3.552 | 1.00x | same |
| 32 | 16 | 3.488 | 3.488 | 1.00x | same |
| 64 | 8 | 5.216 | 5.216 | 1.00x | same |
| 64 | 16 | 5.088 | 5.088 | 1.00x | same |
| 128 | 8 | 5.440 | 5.440 | 1.00x | same |
| 128 | 16 | 5.409 | 5.409 | 1.00x | same |
| 256 | 8 | 5.728 | 5.728 | 1.00x | same |
| 256 | 16 | 5.728 | 5.728 | 1.00x | same |
| 512 | 8 | 7.136 | 7.136 | 1.00x | same |
| 512 | 16 | 7.136 | 7.136 | 1.00x | same |
| 1024 | 8 | 9.632 | 9.632 | 1.00x | same |
| 1024 | 16 | 9.504 | 9.504 | 1.00x | same |
| 2048 | 8 | 12.576 | 12.576 | 1.00x | same |
| 2048 | 16 | 12.544 | 12.544 | 1.00x | same |
| 4096 | 8 | 17.248 | 17.248 | 1.00x | same |
| 4096 | 16 | 17.392 | 17.392 | 1.00x | same |
| 8192 | 8 | 22.960 | 22.960 | 1.00x | same |
| 8192 | 16 | 22.976 | 22.976 | 1.00x | same |

Cake ships no other data type, layout or fused form of this router, and
the family ships on sm_100a and sm_103a only, so these two tables cover
all of its variants and architectures.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added fused-router program coverage for one-token workloads on SM100
and SM103 GPUs.
* **Improvements**
* Updated expert selection to use a revised winner-selection strategy
and write routing counts and offsets for selected experts.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [a600d11](https://github.com/flashinfer-ai/flashinfer/commit/a600d11a39ed6b005082d8dbde6e6259d193a806)

- **作者**: eigen
- **时间**: 2026-10-30T19:30:52Z
- **提交信息**: perf(cake_deepgemm): SM120 paged MQA-logits: route more shapes to tuned programs on RTX 5090 and RTX PRO 6000 (#8029)

The SM120a paged FP8 MQA logits kernel
(`flashinfer/experimental/deepgemm_sm120_paged_mqa_logits`, the
DeepSeek-V3.2 / V4.1-Flash decode lightning indexer) selects per-device
routes by the GPU's SM count. This PR adds no new kernel program. It
adds more routing rows that point existing tuned programs at more
shapes: 48 more of the 216 measured shapes on RTX 5090 (170 SMs) and 17
more on RTX PRO 6000 (188 SMs). Each new row is enabled only on a GPU
that measured faster with it, and 3 of these shapes are enabled on both
GPUs. In total, RTX 5090 now routes 186 of the 216 shapes to tuned
programs and RTX PRO 6000 routes 155. The other shapes keep the shipped
programs. The baseline is the shipped Cake routes on current main, which
already include the previous PR's 138 routed shapes per GPU. Against
that baseline, the geometric-mean speedup on the newly routed shapes
over two independent runs is 1.070x / 1.066x on RTX 5090 (per shape
1.002x-1.289x) and 1.088x / 1.088x on RTX PRO 6000 (per shape
1.022x-1.510x). The logits stay bitwise identical to DeepGEMM.

Table: kernel time of one call (scheduler + logits kernels) on NVIDIA
GeForce RTX 5090 (170 SMs) and NVIDIA RTX PRO 6000 Blackwell Server
Edition (188 SMs), both sm_120a with the CUDA 13.4 JIT toolchain. There
is one row per shape (heads, page size, next_n, batch, context tokens),
with shipped and new latency in µs and the speedup for two independent
runs. Rows marked ¹ keep the shipped program, so both sides run the same
program. ² marks a run where the GPU clock fell below the clock floor
because of the power limit; those numbers are shown as measured and
appear only on unchanged rows.

**RTX 5090**

| heads | page | next_n | batch | context | shipped µs | new µs |
speedup | shipped µs | new µs | speedup |
|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 32 | 64 | 1 | 8 | 4096 | 10.30 | 9.95 | 1.035× | 10.14 | 9.82 | 1.032×
|
| 32 | 64 | 1 | 64 | 4096 | 32.77 | 32.61 | 1.005× | 32.45 | 32.29 |
1.005× |
| 32 | 64 | 1 | 256 | 4096 | 106.53 | 106.53 | 1.000× | 105.79 | 105.79
| 1.000× ¹ |
| 32 | 64 | 1 | 1 | 16384 | 9.06 | 9.06 | 1.000× | 8.80 | 8.80 | 1.000×
¹ |
| 32 | 64 | 1 | 8 | 16384 | 19.74 | 19.49 | 1.013× | 19.42 | 19.20 |
1.012× |
| 32 | 64 | 1 | 32 | 16384 | 55.20 | 55.20 | 1.000× | 54.56 | 54.56 |
1.000× ¹ |
| 32 | 64 | 1 | 64 | 16384 | 104.32 | 104.32 | 1.000× | 103.01 | 103.01
| 1.000× ¹ |
| 32 | 64 | 1 | 128 | 16384 | 196.89 | 196.86 | 1.000× | 195.61 | 195.61
| 1.000× ¹ |
| 32 | 64 | 1 | 256 | 16384 | 380.06 | 380.09 | 1.000× | 378.36 | 378.30
| 1.000× ¹ |
| 32 | 64 | 1 | 8 | 65536 | 58.56 | 58.56 | 1.000× | 57.98 | 57.98 |
1.000× ¹ |
| 32 | 64 | 1 | 32 | 65536 | 191.49 | 191.45 | 1.000× | 190.27 | 190.27
| 1.000× ¹ |
| 32 | 64 | 1 | 128 | 65536 | 725.00 | 724.99 | 1.000× | 721.85 | 721.79
| 1.000× ¹ |
| 32 | 64 | 2 | 8 | 4096 | 11.10 | 10.30 | 1.078× | 10.88 | 10.14 |
1.073× |
| 32 | 64 | 2 | 64 | 4096 | 35.10 | 33.50 | 1.048× | 34.40 | 33.12 |
1.039× |
| 32 | 64 | 2 | 256 | 4096 | 110.85 | 110.88 | 1.000× | 109.38 | 109.38
| 1.000× ¹ |
| 32 | 64 | 2 | 1 | 16384 | 9.25 | 9.25 | 1.000× | 9.09 | 9.09 | 1.000×
¹ |
| 32 | 64 | 2 | 8 | 16384 | 21.02 | 20.22 | 1.040× | 20.58 | 19.90 |
1.034× |
| 32 | 64 | 2 | 32 | 16384 | 56.61 | 56.61 | 1.000× | 55.87 | 55.90 |
0.999× ¹ |
| 32 | 64 | 2 | 64 | 16384 | 107.74 | 107.74 | 1.000× | 106.56 | 106.56
| 1.000× ¹ |
| 32 | 64 | 2 | 128 | 16384 | 207.42 | 207.39 | 1.000× | 206.08 | 206.08
| 1.000× ¹ |
| 32 | 64 | 2 | 256 | 16384 | 400.09 | 400.31 | 0.999× | 398.81 | 398.88
| 1.000× ¹ |
| 32 | 64 | 2 | 8 | 65536 | 60.16 | 60.16 | 1.000× | 59.45 | 59.45 |
1.000× ¹ |
| 32 | 64 | 2 | 32 | 65536 | 200.64 | 200.64 | 1.000× | 199.23 | 199.23
| 1.000× ¹ |
| 32 | 64 | 2 | 128 | 65536 | 763.86 | 763.48 | 1.001× | 755.48 | 755.70
| 1.000× ¹ |
| 32 | 64 | 3 | 8 | 4096 | 11.36 | 11.36 | 1.000× | 11.20 | 11.20 |
1.000× ¹ |
| 32 | 64 | 3 | 64 | 4096 | 37.05 | 35.04 | 1.058× | 36.77 | 34.69 |
1.060× |
| 32 | 64 | 3 | 256 | 4096 | 118.02 | 118.05 | 1.000× | 116.32 | 116.32
| 1.000× ¹ |
| 32 | 64 | 3 | 1 | 16384 | 9.34 | 9.34 | 1.000× | 9.25 | 9.25 | 1.000×
¹ |
| 32 | 64 | 3 | 8 | 16384 | 22.14 | 20.80 | 1.065× | 21.92 | 20.61 |
1.064× |
| 32 | 64 | 3 | 32 | 16384 | 59.23 | 59.23 | 1.000× | 58.59 | 58.59 |
1.000× ¹ |
| 32 | 64 | 3 | 64 | 16384 | 113.95 | 113.95 | 1.000× | 113.09 | 113.12
| 1.000× ¹ |
| 32 | 64 | 3 | 128 | 16384 | 219.04 | 219.04 | 1.000× | 216.93 | 216.93
| 1.000× ¹ |
| 32 | 64 | 3 | 256 | 16384 | 424.78 | 425.21 | 0.999× | 422.78 | 422.91
| 1.000× ¹ |
| 32 | 64 | 3 | 8 | 65536 | 62.62 | 62.62 | 1.000× | 61.85 | 61.85 |
1.000× ¹ |
| 32 | 64 | 3 | 32 | 65536 | 211.39 | 211.36 | 1.000× | 209.92 | 209.89
| 1.000× ¹ |
| 32 | 64 | 3 | 128 | 65536 | 808.87 | 808.85 | 1.000× | 804.02 | 803.61
| 1.001× ¹ |
| 32 | 64 | 4 | 8 | 4096 | 10.46 | 10.46 | 1.000× | 10.40 | 10.40 |
1.000× ¹ |
| 32 | 64 | 4 | 64 | 4096 | 40.26 | 36.83 | 1.093× | 39.84 | 36.16 |
1.102× |
| 32 | 64 | 4 | 256 | 4096 | 124.86 | 124.86 | 1.000× | 124.03 | 124.06
| 1.000× ¹ |
| 32 | 64 | 4 | 1 | 16384 | 9.54 | 9.54 | 1.000× | 9.38 | 9.38 | 1.000×
¹ |
| 32 | 64 | 4 | 8 | 16384 | 23.52 | 21.31 | 1.104× | 23.23 | 21.41 |
1.085× |
| 32 | 64 | 4 | 32 | 16384 | 67.87 | 62.21 | 1.091× | 67.10 | 61.44 |
1.092× |
| 32 | 64 | 4 | 64 | 16384 | 120.29 | 120.29 | 1.000× | 119.20 | 119.17
| 1.000× ¹ |
| 32 | 64 | 4 | 128 | 16384 | 230.43 | 230.36 | 1.000× | 229.05 | 229.02
| 1.000× ¹ |
| 32 | 64 | 4 | 256 | 16384 | 446.39 | 445.53 | 1.002× | 444.22 | 444.15
| 1.000× ¹ |
| 32 | 64 | 4 | 8 | 65536 | 65.15 | 65.18 | 1.000× | 64.86 | 64.86 |
1.000× ¹ |
| 32 | 64 | 4 | 32 | 65536 | 223.36 | 223.36 | 1.000× | 220.86 | 220.83
| 1.000× ¹ |
| 32 | 64 | 4 | 128 | 65536 | 860.26 | 860.18 | 1.000× | 855.29 | 854.46
| 1.001× ¹ |
| 32 | 64 | 5 | 8 | 4096 | 11.65 | 11.65 | 1.000× | 11.46 | 11.46 |
1.000× ¹ |
| 32 | 64 | 5 | 64 | 4096 | 42.98 | 38.46 | 1.117× | 43.10 | 38.94 |
1.107× |
| 32 | 64 | 5 | 256 | 4096 | 138.59 | 138.59 | 1.000× | 138.50 | 138.53
| 1.000× ¹ |
| 32 | 64 | 5 | 1 | 16384 | 10.18 | 10.18 | 1.000× | 9.95 | 9.98 |
0.997× ¹ |
| 32 | 64 | 5 | 8 | 16384 | 24.32 | 22.85 | 1.064× | 24.22 | 22.62 |
1.071× |
| 32 | 64 | 5 | 32 | 16384 | 67.45 | 67.49 | 1.000× | 67.26 | 67.26 |
1.000× ¹ |
| 32 | 64 | 5 | 64 | 16384 | 134.05 | 134.08 | 1.000× | 133.18 | 133.15
| 1.000× ¹ |
| 32 | 64 | 5 | 128 | 16384 | 244.32 | 244.41 | 1.000× | 240.57 | 240.57
| 1.000× ¹ |
| 32 | 64 | 5 | 256 | 16384 | 461.34 | 461.24 | 1.000× | 454.43 | 454.70
| 0.999× ¹ |
| 32 | 64 | 5 | 8 | 65536 | 69.47 | 69.47 | 1.000× | 71.14 | 71.17 |
1.000× ¹ |
| 32 | 64 | 5 | 32 | 65536 | 236.89 | 236.76 | 1.001× | 233.69 | 233.63
| 1.000× ¹ |
| 32 | 64 | 5 | 128 | 65536 | 914.10 | 894.45 | 1.022× | 873.11 | 853.53
| 1.023× |
| 32 | 64 | 6 | 8 | 4096 | 11.58 | 11.58 | 1.000× | 11.42 | 11.42 |
1.000× ¹ |
| 32 | 64 | 6 | 64 | 4096 | 42.37 | 42.37 | 1.000× | 42.05 | 42.08 |
0.999× ¹ |
| 32 | 64 | 6 | 256 | 4096 | 155.58 | 155.58 | 1.000× | 155.17 | 155.17
| 1.000× ¹ |
| 32 | 64 | 6 | 1 | 16384 | 10.02 | 10.02 | 1.000× | 9.86 | 9.86 |
1.000× ¹ |
| 32 | 64 | 6 | 8 | 16384 | 25.25 | 25.25 | 1.000× | 24.54 | 24.54 |
1.000× ¹ |
| 32 | 64 | 6 | 32 | 16384 | 72.70 | 72.70 | 1.000× | 76.32 | 76.32 |
1.000× ¹ |
| 32 | 64 | 6 | 64 | 16384 | 149.50 | 149.47 | 1.000× | 148.61 | 148.61
| 1.000× ¹ |
| 32 | 64 | 6 | 128 | 16384 | 275.39 | 275.64 | 0.999× | 271.58 | 271.58
| 1.000× ¹ |
| 32 | 64 | 6 | 256 | 16384 | 536.63 | 536.66 | 1.000× | 520.89 | 520.84
| 1.000× ¹ |
| 32 | 64 | 6 | 8 | 65536 | 74.75 | 74.78 | 1.000× | 78.14 | 78.21 |
0.999× ¹ |
| 32 | 64 | 6 | 32 | 65536 | 266.62 | 266.40 | 1.001× | 261.89 | 261.92
| 1.000× ¹ |
| 32 | 64 | 6 | 128 | 65536 | 1090.86 | 1051.73 | 1.037× | 1027.08 |
990.33 | 1.037× |
| 32 | 128 | 1 | 8 | 4096 | 10.34 | 9.98 | 1.035× | 10.18 | 9.89 |
1.029× |
| 32 | 128 | 1 | 64 | 4096 | 32.83 | 32.83 | 1.000× | 32.51 | 32.51 |
1.000× ¹ |
| 32 | 128 | 1 | 256 | 4096 | 106.37 | 106.37 | 1.000× | 105.60 | 105.60
| 1.000× ¹ |
| 32 | 128 | 1 | 1 | 16384 | 9.25 | 9.02 | 1.025× | 9.12 | 8.93 | 1.022×
|
| 32 | 128 | 1 | 8 | 16384 | 19.90 | 19.68 | 1.011× | 19.62 | 19.36 |
1.013× |
| 32 | 128 | 1 | 32 | 16384 | 56.70 | 55.17 | 1.028× | 56.19 | 54.56 |
1.030× |
| 32 | 128 | 1 | 64 | 16384 | 103.74 | 103.74 | 1.000× | 102.88 | 102.88
| 1.000× ¹ |
| 32 | 128 | 1 | 128 | 16384 | 197.18 | 197.21 | 1.000× | 195.97 |
195.97 | 1.000× ¹ |
| 32 | 128 | 1 | 256 | 16384 | 379.74 | 379.45 | 1.001× | 377.76 |
377.95 | 0.999× ¹ |
| 32 | 128 | 1 | 8 | 65536 | 58.53 | 58.53 | 1.000× | 57.92 | 57.92 |
1.000× ¹ |
| 32 | 128 | 1 | 32 | 65536 | 191.33 | 191.36 | 1.000× | 190.07 | 190.05
| 1.000× ¹ |
| 32 | 128 | 1 | 128 | 65536 | 724.12 | 724.25 | 1.000× | 720.31 |
720.54 | 1.000× ¹ |
| 32 | 128 | 2 | 8 | 4096 | 11.17 | 10.34 | 1.080× | 10.91 | 10.21 |
1.069× |
| 32 | 128 | 2 | 64 | 4096 | 34.91 | 33.73 | 1.035× | 34.24 | 33.18 |
1.032× |
| 32 | 128 | 2 | 256 | 4096 | 111.61 | 111.58 | 1.000× | 110.56 | 110.59
| 1.000× ¹ |
| 32 | 128 | 2 | 1 | 16384 | 9.31 | 9.31 | 1.000× | 9.18 | 9.18 | 1.000×
¹ |
| 32 | 128 | 2 | 8 | 16384 | 20.74 | 20.00 | 1.037× | 20.45 | 19.65 |
1.041× |
| 32 | 128 | 2 | 32 | 16384 | 59.39 | 56.70 | 1.047× | 58.78 | 56.06 |
1.048× |
| 32 | 128 | 2 | 64 | 16384 | 107.97 | 107.97 | 1.000× | 107.20 | 107.23
| 1.000× ¹ |
| 32 | 128 | 2 | 128 | 16384 | 207.65 | 207.68 | 1.000× | 206.05 |
206.11 | 1.000× ¹ |
| 32 | 128 | 2 | 256 | 16384 | 401.31 | 401.08 | 1.001× | 398.65 |
398.65 | 1.000× ¹ |
| 32 | 128 | 2 | 8 | 65536 | 60.06 | 60.06 | 1.000× | 59.45 | 59.46 |
1.000× ¹ |
| 32 | 128 | 2 | 32 | 65536 | 201.09 | 201.12 | 1.000× | 199.33 | 199.33
| 1.000× ¹ |
| 32 | 128 | 2 | 128 | 65536 | 766.26 | 766.26 | 1.000× | 759.26 |
759.66 | 0.999× ¹ |
| 32 | 128 | 3 | 8 | 4096 | 11.39 | 11.39 | 1.000× | 11.42 | 11.42 |
1.000× ¹ |
| 32 | 128 | 3 | 64 | 4096 | 37.05 | 35.26 | 1.051× | 36.70 | 34.98 |
1.049× |
| 32 | 128 | 3 | 256 | 4096 | 117.79 | 117.79 | 1.000× | 117.28 | 117.28
| 1.000× ¹ |
| 32 | 128 | 3 | 1 | 16384 | 10.14 | 9.66 | 1.050× | 9.95 | 9.50 |
1.047× |
| 32 | 128 | 3 | 8 | 16384 | 22.18 | 21.09 | 1.052× | 21.86 | 20.93 |
1.044× |
| 32 | 128 | 3 | 32 | 16384 | 59.49 | 59.49 | 1.000× | 58.75 | 58.75 |
1.000× ¹ |
| 32 | 128 | 3 | 64 | 16384 | 114.69 | 114.69 | 1.000× | 112.73 | 112.73
| 1.000× ¹ |
| 32 | 128 | 3 | 128 | 16384 | 218.56 | 218.56 | 1.000× | 216.89 |
216.99 | 1.000× ¹ |
| 32 | 128 | 3 | 256 | 16384 | 423.96 | 423.45 | 1.001× | 420.91 |
421.53 | 0.999× ¹ |
| 32 | 128 | 3 | 8 | 65536 | 62.98 | 62.98 | 1.000× | 62.37 | 62.37 |
1.000× ¹ |
| 32 | 128 | 3 | 32 | 65536 | 212.64 | 212.64 | 1.000× | 210.05 | 210.05
| 1.000× ¹ |
| 32 | 128 | 3 | 128 | 65536 | 806.71 | 806.10 | 1.001× | 811.32 |
811.33 | 1.000× ¹ |
| 32 | 128 | 4 | 8 | 4096 | 11.68 | 11.68 | 1.000× | 11.62 | 11.62 |
1.000× ¹ |
| 32 | 128 | 4 | 64 | 4096 | 40.54 | 36.48 | 1.111× | 40.61 | 36.26 |
1.120× |
| 32 | 128 | 4 | 256 | 4096 | 124.09 | 124.13 | 1.000× | 123.97 | 123.94
| 1.000× ¹ |
| 32 | 128 | 4 | 1 | 16384 | 10.43 | 10.40 | 1.003× | 10.21 | 10.21 |
1.000× ¹ |
| 32 | 128 | 4 | 8 | 16384 | 24.86 | 21.66 | 1.148× | 23.58 | 21.12 |
1.117× |
| 32 | 128 | 4 | 32 | 16384 | 67.45 | 61.85 | 1.091× | 67.39 | 61.25 |
1.100× |
| 32 | 128 | 4 | 64 | 16384 | 120.22 | 120.19 | 1.000× | 120.35 | 120.29
| 1.001× ¹ |
| 32 | 128 | 4 | 128 | 16384 | 230.04 | 230.04 | 1.000× | 228.38 |
228.41 | 1.000× ¹ |
| 32 | 128 | 4 | 256 | 16384 | 445.47 | 445.66 | 1.000× | 443.00 |
443.21 | 1.000× ¹ |
| 32 | 128 | 4 | 8 | 65536 | 65.21 | 65.18 | 1.000× | 64.35 | 64.35 |
1.000× ¹ |
| 32 | 128 | 4 | 32 | 65536 | 223.29 | 223.32 | 1.000× | 220.91 | 220.83
| 1.000× ¹ |
| 32 | 128 | 4 | 128 | 65536 | 851.00 | 850.44 | 1.001× | 849.74 |
849.88 | 1.000× ¹ |
| 32 | 128 | 5 | 8 | 4096 | 11.71 | 11.68 | 1.003× | 11.49 | 11.49 |
1.000× ¹ |
| 32 | 128 | 5 | 64 | 4096 | 43.01 | 38.62 | 1.114× | 42.46 | 38.78 |
1.095× |
| 32 | 128 | 5 | 256 | 4096 | 138.78 | 138.78 | 1.000× | 137.98 | 137.92
| 1.000× ¹ |
| 32 | 128 | 5 | 1 | 16384 | 10.21 | 10.21 | 1.000× | 10.02 | 10.02 |
1.000× ¹ |
| 32 | 128 | 5 | 8 | 16384 | 22.50 | 22.50 | 1.000× | 22.30 | 22.30 |
1.000× ¹ |
| 32 | 128 | 5 | 32 | 16384 | 72.89 | 67.23 | 1.084× | 73.60 | 67.55 |
1.090× |
| 32 | 128 | 5 | 64 | 16384 | 134.17 | 134.21 | 1.000× | 132.51 | 132.54
| 1.000× ¹ |
| 32 | 128 | 5 | 128 | 16384 | 245.05 | 245.12 | 1.000× | 244.51 |
244.77 | 0.999× ¹ |
| 32 | 128 | 5 | 256 | 16384 | 458.14 | 458.59 | 0.999× | 451.80 |
451.93 | 1.000× ¹ |
| 32 | 128 | 5 | 8 | 65536 | 69.95 | 69.92 | 1.000× | 70.24 | 70.24 |
1.000× ¹ |
| 32 | 128 | 5 | 32 | 65536 | 236.16 | 236.16 | 1.000× | 234.73 | 234.65
| 1.000× ¹ |
| 32 | 128 | 5 | 128 | 65536 | 903.60 | 881.36 | 1.025× | 872.29 |
853.50 | 1.022× |
| 32 | 128 | 6 | 8 | 4096 | 11.58 | 11.58 | 1.000× | 11.36 | 11.36 |
1.000× ¹ |
| 32 | 128 | 6 | 64 | 4096 | 42.50 | 42.50 | 1.000× | 41.18 | 41.18 |
1.000× ¹ |
| 32 | 128 | 6 | 256 | 4096 | 154.85 | 154.85 | 1.000× | 155.45 | 155.39
| 1.000× ¹ |
| 32 | 128 | 6 | 1 | 16384 | 10.14 | 10.14 | 1.000× | 9.98 | 9.98 |
1.000× ¹ |
| 32 | 128 | 6 | 8 | 16384 | 24.58 | 24.58 | 1.000× | 24.73 | 24.73 |
1.000× ¹ |
| 32 | 128 | 6 | 32 | 16384 | 72.48 | 72.48 | 1.000× | 75.97 | 75.97 |
1.000× ¹ |
| 32 | 128 | 6 | 64 | 16384 | 148.35 | 148.32 | 1.000× | 148.99 | 149.02
| 1.000× ¹ |
| 32 | 128 | 6 | 128 | 16384 | 274.30 | 274.33 | 1.000× | 271.36 |
271.36 | 1.000× ¹ |
| 32 | 128 | 6 | 256 | 16384 | 546.20 | 547.26 | 0.998× | 536.89 |
537.02 | 1.000× ¹ |
| 32 | 128 | 6 | 8 | 65536 | 75.13 | 75.13 | 1.000× | 78.34 | 78.30 |
1.000× ¹ |
| 32 | 128 | 6 | 32 | 65536 | 265.02 | 264.99 | 1.000× | 262.01 | 262.17
| 0.999× ¹ |
| 32 | 128 | 6 | 128 | 65536 | 1079.57 | 1079.15 | 1.000× | 1032.85 |
1032.45 | 1.000× ¹ |
| 64 | 64 | 1 | 8 | 4096 | 11.07 | 10.27 | 1.078× | 10.85 | 10.11 |
1.073× |
| 64 | 64 | 1 | 64 | 4096 | 34.17 | 33.31 | 1.026× | 33.73 | 32.93 |
1.024× |
| 64 | 64 | 1 | 256 | 4096 | 108.03 | 108.03 | 1.000× | 106.85 | 106.85
| 1.000× ¹ |
| 64 | 64 | 1 | 1 | 16384 | 9.25 | 9.25 | 1.000× | 8.99 | 8.99 | 1.000×
¹ |
| 64 | 64 | 1 | 8 | 16384 | 20.64 | 19.97 | 1.034× | 20.32 | 19.52 |
1.041× |
| 64 | 64 | 1 | 32 | 16384 | 55.61 | 55.61 | 1.000× | 55.01 | 55.01 |
1.000× ¹ |
| 64 | 64 | 1 | 64 | 16384 | 104.67 | 104.67 | 1.000× | 103.81 | 103.84
| 1.000× ¹ |
| 64 | 64 | 1 | 128 | 16384 | 198.59 | 198.59 | 1.000× | 196.73 | 196.73
| 1.000× ¹ |
| 64 | 64 | 1 | 256 | 16384 | 381.79 | 381.82 | 1.000× | 380.40 | 380.28
| 1.000× ¹ |
| 64 | 64 | 1 | 8 | 65536 | 59.01 | 59.01 | 1.000× | 58.37 | 58.37 |
1.000× ¹ |
| 64 | 64 | 1 | 32 | 65536 | 192.06 | 192.09 | 1.000× | 191.01 | 191.04
| 1.000× ¹ |
| 64 | 64 | 1 | 128 | 65536 | 726.60 | 726.45 | 1.000× | 725.91 | 726.30
| 0.999× ¹ |
| 64 | 64 | 2 | 8 | 4096 | 11.04 | 11.04 | 1.000× | 10.91 | 10.88 |
1.003× ¹ |
| 64 | 64 | 2 | 64 | 4096 | 38.72 | 35.39 | 1.094× | 38.27 | 34.88 |
1.097× |
| 64 | 64 | 2 | 256 | 4096 | 115.20 | 115.17 | 1.000× | 114.50 | 114.53
| 1.000× ¹ |
| 64 | 64 | 2 | 1 | 16384 | 9.73 | 9.73 | 1.000× | 9.41 | 9.41 | 1.000×
¹ |
| 64 | 64 | 2 | 8 | 16384 | 22.94 | 20.93 | 1.096× | 22.78 | 20.77 |
1.097× |
| 64 | 64 | 2 | 32 | 16384 | 63.49 | 58.49 | 1.085× | 62.91 | 57.76 |
1.089× |
| 64 | 64 | 2 | 64 | 16384 | 111.42 | 111.45 | 1.000× | 110.02 | 110.02
| 1.000× ¹ |
| 64 | 64 | 2 | 128 | 16384 | 212.41 | 212.41 | 1.000× | 210.64 | 210.62
| 1.000× ¹ |
| 64 | 64 | 2 | 256 | 16384 | 409.40 | 409.43 | 1.000× | 409.24 | 409.08
| 1.000× ¹ |
| 64 | 64 | 2 | 8 | 65536 | 61.79 | 61.82 | 0.999× | 61.18 | 61.18 |
1.000× ¹ |
| 64 | 64 | 2 | 32 | 65536 | 205.21 | 205.28 | 1.000× | 203.45 | 203.52
| 1.000× ¹ |
| 64 | 64 | 2 | 128 | 65536 | 783.54 | 783.81 | 1.000× | 775.86 | 775.53
| 1.000× ¹ |
| 64 | 64 | 3 | 8 | 4096 | 11.97 | 11.97 | 1.000× | 11.78 | 11.78 |
1.000× ¹ |
| 64 | 64 | 3 | 64 | 4096 | 38.98 | 39.01 | 0.999× | 38.98 | 39.01 |
0.999× ¹ |
| 64 | 64 | 3 | 256 | 4096 | 150.97 | 151.01 | 1.000× | 151.10 | 151.13
| 1.000× ¹ |
| 64 | 64 | 3 | 1 | 16384 | 10.43 | 10.43 | 1.000× | 10.08 | 10.08 |
1.000× ¹ |
| 64 | 64 | 3 | 8 | 16384 | 23.49 | 23.49 | 1.000× | 23.04 | 23.04 |
1.000× ¹ |
| 64 | 64 | 3 | 32 | 16384 | 65.06 | 65.06 | 1.000× | 68.80 | 68.77 |
1.000× ¹ |
| 64 | 64 | 3 | 64 | 16384 | 145.50 | 145.57 | 1.000× | 145.09 | 145.15
| 1.000× ¹ |
| 64 | 64 | 3 | 128 | 16384 | 269.05 | 269.15 | 1.000× | 265.98 | 266.40
| 0.998× ¹ |
| 64 | 64 | 3 | 256 | 16384 | 520.38 | 520.79 | 0.999× | 510.91 | 511.10
| 1.000× ¹ |
| 64 | 64 | 3 | 8 | 65536 | 67.58 | 67.58 | 1.000× | 72.26 | 72.25 |
1.000× ¹ |
| 64 | 64 | 3 | 32 | 65536 | 259.68 | 259.58 | 1.000× | 257.05 | 256.86
| 1.001× ¹ |
| 64 | 64 | 3 | 128 | 65536 | 1022.87 | 1022.77 | 1.000× | 980.76 |
980.90 | 1.000× ¹ |
| 64 | 64 | 4 | 8 | 4096 | 11.84 | 11.84 | 1.000× | 11.78 | 11.78 |
1.000× ¹ |
| 64 | 64 | 4 | 64 | 4096 | 54.82 | 42.53 | 1.289× | 54.02 | 42.78 |
1.263× |
| 64 | 64 | 4 | 256 | 4096 | 186.65 | 186.53 | 1.001× | 187.01 | 187.01
| 1.000× ¹ |
| 64 | 64 | 4 | 1 | 16384 | 10.40 | 10.40 | 1.000× | 10.14 | 10.14 |
1.000× ¹ |
| 64 | 64 | 4 | 8 | 16384 | 32.67 | 25.63 | 1.275× | 32.22 | 25.18 |
1.280× |
| 64 | 64 | 4 | 32 | 16384 | 95.36 | 75.20 | 1.268× | 96.61 | 83.39 |
1.158× |
| 64 | 64 | 4 | 64 | 16384 | 181.92 | 181.85 | 1.000× | 180.54 | 180.45
| 1.001× ¹ |
| 64 | 64 | 4 | 128 | 16384 | 346.84 | 342.52 | 1.013× | 342.05 | 337.76
| 1.013× |
| 64 | 64 | 4 | 256 | 16384 | 681.01 | 671.77 | 1.014× | 662.59 | 652.76
| 1.015× |
| 64 | 64 | 4 | 8 | 65536 | 77.38 | 77.41 | 1.000× | 85.50 | 85.44 |
1.001× ¹ |
| 64 | 64 | 4 | 32 | 65536 | 335.29 | 331.45 | 1.012× | 331.20 | 326.72
| 1.014× |
| 64 | 64 | 4 | 128 | 65536 | 1347.82 | 1328.24 | 1.015× | 1300.98 |
1274.32 | 1.021× |
| 64 | 64 | 5 | 8 | 4096 | 13.82 | 13.82 | 1.000× | 13.76 | 13.76 |
1.000× ¹ |
| 64 | 64 | 5 | 64 | 4096 | 53.34 | 53.34 | 1.000× | 56.09 | 56.10 |
1.000× ¹ |
| 64 | 64 | 5 | 256 | 4096 | 253.47 | 253.50 | 1.000× | 251.00 | 251.03
| 1.000× ¹ |
| 64 | 64 | 5 | 1 | 16384 | 11.46 | 11.46 | 1.000× | 11.17 | 11.17 |
1.000× ¹ |
| 64 | 64 | 5 | 8 | 16384 | 31.23 | 31.23 | 1.000× | 30.72 | 30.72 |
1.000× ¹ |
| 64 | 64 | 5 | 32 | 16384 | 116.22 | 116.25 | 1.000× | 116.51 | 116.48
| 1.000× ¹ |
| 64 | 64 | 5 | 64 | 16384 | 216.89 | 216.89 | 1.000× | 216.64 | 216.64
| 1.000× ¹ |
| 64 | 64 | 5 | 128 | 16384 | 495.32 | 495.71 | 0.999× | 489.37 | 489.34
| 1.000× ¹ |
| 64 | 64 | 5 | 256 | 16384 | 929.64 | 929.17 | 1.000× | 908.60 | 909.27
| 0.999× ¹ |
| 64 | 64 | 5 | 8 | 65536 | 122.17 | 122.24 | 0.999× | 121.08 | 121.09 |
1.000× ¹ |
| 64 | 64 | 5 | 32 | 65536 | 551.86 | 521.02 | 1.059× | 546.14 | 516.57
| 1.057× |
| 64 | 64 | 5 | 128 | 65536 | 1909.99 | 1906.38 | 1.002× | 1857.69 |
1857.10 | 1.000× ¹ |
| 64 | 64 | 6 | 8 | 4096 | 13.82 | 13.82 | 1.000× | 13.82 | 13.82 |
1.000× ¹ |
| 64 | 64 | 6 | 64 | 4096 | 52.67 | 52.67 | 1.000× | 58.85 | 58.81 |
1.001× ¹ |
| 64 | 64 | 6 | 256 | 4096 | 275.29 | 275.26 | 1.000× | 274.40 | 274.30
| 1.000× ¹ |
| 64 | 64 | 6 | 1 | 16384 | 13.57 | 11.36 | 1.194× | 13.44 | 11.17 |
1.203× |
| 64 | 64 | 6 | 8 | 16384 | 30.98 | 30.98 | 1.000× | 30.30 | 30.30 |
1.000× ¹ |
| 64 | 64 | 6 | 32 | 16384 | 117.02 | 117.09 | 0.999× | 118.75 | 118.91
| 0.999× ¹ |
| 64 | 64 | 6 | 64 | 16384 | 269.18 | 269.21 | 1.000× | 265.09 | 265.09
| 1.000× ¹ |
| 64 | 64 | 6 | 128 | 16384 | 517.46 | 516.95 | 1.001× | 508.03 | 508.19
| 1.000× ¹ |
| 64 | 64 | 6 | 256 | 16384 | 1038.48 | 1039.12 | 0.999× | 998.89 |
996.82 | 1.002× ¹ |
| 64 | 64 | 6 | 8 | 65536 | 120.48 | 120.51 | 1.000× | 120.54 | 120.58 |
1.000× ¹ |
| 64 | 64 | 6 | 32 | 65536 | 534.84 | 528.31 | 1.012× | 530.01 | 528.84
| 1.002× |
| 64 | 64 | 6 | 128 | 65536 | 2049.21 | 2049.30 | 1.000× | 1980.49 |
1984.11 | 0.998× ¹ |

**RTX PRO 6000**

| heads | page | next_n | batch | context | shipped µs | new µs |
speedup | shipped µs | new µs | speedup |
|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 32 | 64 | 1 | 8 | 4096 | 14.37 | 14.37 | 1.000× | 14.37 | 14.37 |
1.000× ¹ |
| 32 | 64 | 1 | 64 | 4096 | 44.54 | 44.54 | 1.000× | 44.32 | 44.32 |
1.000× ¹ |
| 32 | 64 | 1 | 256 | 4096 | 131.97 | 131.97 | 1.000× | 132.45 | 132.45
| 1.000× ¹ |
| 32 | 64 | 1 | 1 | 16384 | 11.55 | 11.55 | 1.000× | 11.55 | 11.55 |
1.000× ¹ |
| 32 | 64 | 1 | 8 | 16384 | 27.33 | 27.33 | 1.000× | 27.17 | 27.17 |
1.000× ¹ |
| 32 | 64 | 1 | 32 | 16384 | 73.41 | 73.41 | 1.000× | 73.70 | 73.70 |
1.000× ¹ |
| 32 | 64 | 1 | 64 | 16384 | 128.48 | 128.48 | 1.000× | 129.22 | 129.22
| 1.000× ¹ |
| 32 | 64 | 1 | 128 | 16384 | 229.99 | 230.02 | 1.000× | 229.82 | 229.82
| 1.000× ¹ |
| 32 | 64 | 1 | 256 | 16384 | 431.56 | 431.36 | 1.000× | 431.23 | 431.23
| 1.000× ¹ |
| 32 | 64 | 1 | 8 | 65536 | 79.07 | 79.07 | 1.000× | 79.01 | 78.98 |
1.000× ¹ |
| 32 | 64 | 1 | 32 | 65536 | 223.07 | 223.07 | 1.000× | 223.55 | 223.55
| 1.000× ¹ |
| 32 | 64 | 1 | 128 | 65536 | 818.31 | 818.23 | 1.000× | 821.48 | 821.48
| 1.000× ¹ |
| 32 | 64 | 2 | 8 | 4096 | 14.75 | 14.75 | 1.000× | 14.78 | 14.78 |
1.000× ¹ |
| 32 | 64 | 2 | 64 | 4096 | 44.83 | 44.83 | 1.000× | 44.96 | 44.96 |
1.000× ¹ |
| 32 | 64 | 2 | 256 | 4096 | 136.70 | 136.70 | 1.000× | 136.70 | 136.70
| 1.000× ¹ |
| 32 | 64 | 2 | 1 | 16384 | 12.00 | 12.00 | 1.000× | 11.87 | 11.87 |
1.000× ¹ |
| 32 | 64 | 2 | 8 | 16384 | 27.39 | 27.39 | 1.000× | 27.42 | 27.42 |
1.000× ¹ |
| 32 | 64 | 2 | 32 | 16384 | 74.02 | 74.02 | 1.000× | 74.66 | 74.66 |
1.000× ¹ |
| 32 | 64 | 2 | 64 | 16384 | 132.70 | 132.70 | 1.000× | 132.70 | 132.70
| 1.000× ¹ |
| 32 | 64 | 2 | 128 | 16384 | 236.77 | 236.74 | 1.000× | 237.47 | 237.50
| 1.000× ¹ |
| 32 | 64 | 2 | 256 | 16384 | 447.04 | 447.07 | 1.000× | 446.95 | 446.91
| 1.000× ¹ |
| 32 | 64 | 2 | 8 | 65536 | 80.06 | 80.06 | 1.000× | 79.78 | 79.78 |
1.000× ¹ |
| 32 | 64 | 2 | 32 | 65536 | 230.50 | 230.50 | 1.000× | 230.56 | 230.56
| 1.000× ¹ |
| 32 | 64 | 2 | 128 | 65536 | 848.74 | 848.93 | 1.000× | 849.12 | 849.12
| 1.000× ¹ |
| 32 | 64 | 3 | 8 | 4096 | 15.17 | 15.17 | 1.000× | 15.20 | 15.20 |
1.000× ¹ |
| 32 | 64 | 3 | 64 | 4096 | 45.50 | 45.50 | 1.000× | 45.38 | 45.38 |
1.000× ¹ |
| 32 | 64 | 3 | 256 | 4096 | 140.42 | 140.39 | 1.000× | 140.74 | 140.74
| 1.000× ¹ |
| 32 | 64 | 3 | 1 | 16384 | 12.42 | 12.42 | 1.000× | 12.35 | 12.35 |
1.000× ¹ |
| 32 | 64 | 3 | 8 | 16384 | 27.84 | 27.84 | 1.000× | 27.65 | 27.62 |
1.001× ¹ |
| 32 | 64 | 3 | 32 | 16384 | 75.94 | 75.97 | 1.000× | 75.07 | 75.07 |
1.000× ¹ |
| 32 | 64 | 3 | 64 | 16384 | 136.54 | 136.54 | 1.000× | 136.45 | 136.45
| 1.000× ¹ |
| 32 | 64 | 3 | 128 | 16384 | 245.70 | 245.67 | 1.000× | 245.76 | 245.79
| 1.000× ¹ |
| 32 | 64 | 3 | 256 | 16384 | 460.87 | 460.93 | 1.000× | 460.93 | 461.00
| 1.000× ¹ |
| 32 | 64 | 3 | 8 | 65536 | 79.78 | 79.78 | 1.000× | 79.68 | 79.68 |
1.000× ¹ |
| 32 | 64 | 3 | 32 | 65536 | 237.15 | 237.15 | 1.000× | 236.96 | 236.93
| 1.000× ¹ |
| 32 | 64 | 3 | 128 | 65536 | 875.40 | 875.40 | 1.000× | 874.95 | 874.88
| 1.000× ¹ |
| 32 | 64 | 4 | 8 | 4096 | 15.07 | 15.07 | 1.000× | 15.01 | 15.01 |
1.000× ¹ |
| 32 | 64 | 4 | 64 | 4096 | 46.53 | 46.53 | 1.000× | 46.34 | 46.30 |
1.001× ¹ |
| 32 | 64 | 4 | 256 | 4096 | 145.22 | 145.25 | 1.000× | 146.08 | 146.08
| 1.000× ¹ |
| 32 | 64 | 4 | 1 | 16384 | 13.31 | 13.31 | 1.000× | 13.34 | 13.34 |
1.000× ¹ |
| 32 | 64 | 4 | 8 | 16384 | 28.10 | 28.10 | 1.000× | 28.00 | 28.00 |
1.000× ¹ |
| 32 | 64 | 4 | 32 | 16384 | 76.96 | 76.96 | 1.000× | 77.09 | 77.09 |
1.000× ¹ |
| 32 | 64 | 4 | 64 | 16384 | 140.45 | 140.48 | 1.000× | 140.61 | 140.64
| 1.000× ¹ |
| 32 | 64 | 4 | 128 | 16384 | 253.38 | 253.41 | 1.000× | 252.32 | 252.32
| 1.000× ¹ |
| 32 | 64 | 4 | 256 | 16384 | 475.14 | 475.27 | 1.000× | 476.96 | 476.90
| 1.000× ¹ |
| 32 | 64 | 4 | 8 | 65536 | 80.80 | 80.80 | 1.000× | 80.13 | 80.13 |
1.000× ¹ |
| 32 | 64 | 4 | 32 | 65536 | 243.52 | 243.55 | 1.000× | 243.52 | 243.49
| 1.000× ¹ |
| 32 | 64 | 4 | 128 | 65536 | 923.62 | 900.92 | 1.025× | 923.30 | 900.74
| 1.025× |
| 32 | 64 | 5 | 8 | 4096 | 15.87 | 15.87 | 1.000× | 15.84 | 15.84 |
1.000× ¹ |
| 32 | 64 | 5 | 64 | 4096 | 47.10 | 47.11 | 1.000× | 47.26 | 47.26 |
1.000× ¹ |
| 32 | 64 | 5 | 256 | 4096 | 159.68 | 151.75 | 1.052× | 159.62 | 151.71
| 1.052× |
| 32 | 64 | 5 | 1 | 16384 | 13.44 | 13.44 | 1.000× | 13.54 | 13.54 |
1.000× ¹ |
| 32 | 64 | 5 | 8 | 16384 | 28.22 | 28.19 | 1.001× | 28.22 | 28.22 |
1.000× ¹ |
| 32 | 64 | 5 | 32 | 16384 | 77.92 | 77.92 | 1.000× | 77.79 | 77.82 |
1.000× ¹ |
| 32 | 64 | 5 | 64 | 16384 | 152.48 | 146.66 | 1.040× | 152.16 | 146.78
| 1.037× |
| 32 | 64 | 5 | 128 | 16384 | 262.47 | 262.47 | 1.000× | 261.09 | 261.12
| 1.000× ¹ |
| 32 | 64 | 5 | 256 | 16384 | 492.71 | 492.71 | 1.000× | 491.44 | 491.40
| 1.000× ¹ |
| 32 | 64 | 5 | 8 | 65536 | 83.78 | 83.78 | 1.000× | 81.18 | 81.18 |
1.000× ¹ |
| 32 | 64 | 5 | 32 | 65536 | 272.39 | 252.96 | 1.077× | 271.20 | 251.14
| 1.080× |
| 32 | 64 | 5 | 128 | 65536 | 947.62 | 927.41 | 1.022× | 950.53 | 929.57
| 1.023× |
| 32 | 64 | 6 | 8 | 4096 | 15.87 | 15.87 | 1.000× | 15.90 | 15.90 |
1.000× ¹ |
| 32 | 64 | 6 | 64 | 4096 | 48.13 | 48.13 | 1.000× | 47.62 | 47.62 |
1.000× ¹ |
| 32 | 64 | 6 | 256 | 4096 | 156.10 | 156.06 | 1.000× | 155.71 | 155.71
| 1.000× ¹ |
| 32 | 64 | 6 | 1 | 16384 | 13.47 | 13.47 | 1.000× | 13.44 | 13.44 |
1.000× ¹ |
| 32 | 64 | 6 | 8 | 16384 | 28.64 | 28.64 | 1.000× | 28.45 | 28.45 |
1.000× ¹ |
| 32 | 64 | 6 | 32 | 16384 | 82.24 | 82.24 | 1.000× | 81.82 | 81.82 |
1.000× ¹ |
| 32 | 64 | 6 | 64 | 16384 | 149.34 | 149.34 | 1.000× | 149.50 | 149.50
| 1.000× ¹ |
| 32 | 64 | 6 | 128 | 16384 | 267.97 | 267.97 | 1.000× | 267.94 | 267.91
| 1.000× ¹ |
| 32 | 64 | 6 | 256 | 16384 | 511.94 | 511.72 | 1.000× | 510.75 | 510.88
| 1.000× ¹ |
| 32 | 64 | 6 | 8 | 65536 | 84.55 | 84.55 | 1.000× | 85.28 | 85.31 |
1.000× ¹ |
| 32 | 64 | 6 | 32 | 65536 | 259.07 | 259.07 | 1.000× | 259.46 | 259.43
| 1.000× ¹ |
| 32 | 64 | 6 | 128 | 65536 | 975.72 | 975.67 | 1.000× | 975.94 | 976.04
| 1.000× ¹ |
| 32 | 128 | 1 | 8 | 4096 | 14.37 | 14.37 | 1.000× | 14.40 | 14.40 |
1.000× ¹ |
| 32 | 128 | 1 | 64 | 4096 | 44.90 | 44.90 | 1.000× | 44.86 | 44.86 |
1.000× ¹ |
| 32 | 128 | 1 | 256 | 4096 | 131.84 | 131.84 | 1.000× | 131.84 | 131.84
| 1.000× ¹ |
| 32 | 128 | 1 | 1 | 16384 | 11.74 | 11.74 | 1.000× | 11.68 | 11.68 |
1.000× ¹ |
| 32 | 128 | 1 | 8 | 16384 | 27.42 | 27.42 | 1.000× | 27.30 | 27.30 |
1.000× ¹ |
| 32 | 128 | 1 | 32 | 16384 | 75.68 | 75.68 | 1.000× | 75.84 | 75.84 |
1.000× ¹ |
| 32 | 128 | 1 | 64 | 16384 | 128.90 | 128.90 | 1.000× | 128.67 | 128.67
| 1.000× ¹ |
| 32 | 128 | 1 | 128 | 16384 | 229.41 | 229.41 | 1.000× | 229.35 |
229.34 | 1.000× ¹ |
| 32 | 128 | 1 | 256 | 16384 | 430.63 | 430.63 | 1.000× | 430.37 |
430.21 | 1.000× ¹ |
| 32 | 128 | 1 | 8 | 65536 | 79.42 | 79.42 | 1.000× | 78.85 | 78.85 |
1.000× ¹ |
| 32 | 128 | 1 | 32 | 65536 | 222.72 | 222.75 | 1.000× | 222.85 | 222.85
| 1.000× ¹ |
| 32 | 128 | 1 | 128 | 65536 | 818.82 | 818.74 | 1.000× | 816.79 |
816.61 | 1.000× ¹ |
| 32 | 128 | 2 | 8 | 4096 | 14.85 | 14.85 | 1.000× | 14.81 | 14.79 |
1.002× ¹ |
| 32 | 128 | 2 | 64 | 4096 | 45.18 | 45.18 | 1.000× | 44.86 | 44.86 |
1.000× ¹ |
| 32 | 128 | 2 | 256 | 4096 | 136.61 | 136.61 | 1.000× | 136.48 | 136.48
| 1.000× ¹ |
| 32 | 128 | 2 | 1 | 16384 | 12.00 | 12.00 | 1.000× | 11.90 | 11.90 |
1.000× ¹ |
| 32 | 128 | 2 | 8 | 16384 | 27.49 | 27.49 | 1.000× | 27.55 | 27.55 |
1.000× ¹ |
| 32 | 128 | 2 | 32 | 16384 | 75.49 | 75.49 | 1.000× | 75.46 | 75.46 |
1.000× ¹ |
| 32 | 128 | 2 | 64 | 16384 | 132.77 | 132.77 | 1.000× | 131.97 | 131.97
| 1.000× ¹ |
| 32 | 128 | 2 | 128 | 16384 | 237.47 | 237.44 | 1.000× | 237.60 |
237.60 | 1.000× ¹ |
| 32 | 128 | 2 | 256 | 16384 | 446.15 | 446.21 | 1.000× | 444.87 |
444.87 | 1.000× ¹ |
| 32 | 128 | 2 | 8 | 65536 | 79.49 | 79.49 | 1.000× | 79.20 | 79.20 |
1.000× ¹ |
| 32 | 128 | 2 | 32 | 65536 | 229.50 | 229.54 | 1.000× | 229.41 | 229.38
| 1.000× ¹ |
| 32 | 128 | 2 | 128 | 65536 | 847.37 | 847.52 | 1.000× | 846.25 |
846.25 | 1.000× ¹ |
| 32 | 128 | 3 | 8 | 4096 | 15.17 | 15.17 | 1.000× | 15.17 | 15.17 |
1.000× ¹ |
| 32 | 128 | 3 | 64 | 4096 | 45.66 | 45.66 | 1.000× | 45.79 | 45.79 |
1.000× ¹ |
| 32 | 128 | 3 | 256 | 4096 | 141.38 | 141.38 | 1.000× | 141.09 | 141.12
| 1.000× ¹ |
| 32 | 128 | 3 | 1 | 16384 | 12.70 | 12.70 | 1.000× | 12.64 | 12.64 |
1.000× ¹ |
| 32 | 128 | 3 | 8 | 16384 | 27.78 | 27.78 | 1.000× | 27.78 | 27.78 |
1.000× ¹ |
| 32 | 128 | 3 | 32 | 16384 | 75.30 | 75.27 | 1.000× | 74.75 | 74.72 |
1.000× ¹ |
| 32 | 128 | 3 | 64 | 16384 | 136.93 | 136.96 | 1.000× | 136.93 | 136.93
| 1.000× ¹ |
| 32 | 128 | 3 | 128 | 16384 | 245.15 | 245.15 | 1.000× | 244.48 |
244.48 | 1.000× ¹ |
| 32 | 128 | 3 | 256 | 16384 | 461.76 | 461.86 | 1.000× | 460.10 |
460.05 | 1.000× ¹ |
| 32 | 128 | 3 | 8 | 65536 | 80.22 | 80.22 | 1.000× | 79.81 | 79.81 |
1.000× ¹ |
| 32 | 128 | 3 | 32 | 65536 | 236.39 | 236.42 | 1.000× | 236.22 | 236.19
| 1.000× ¹ |
| 32 | 128 | 3 | 128 | 65536 | 871.91 | 871.73 | 1.000× | 873.33 |
873.75 | 1.000× ¹ |
| 32 | 128 | 4 | 8 | 4096 | 15.20 | 15.20 | 1.000× | 15.07 | 15.07 |
1.000× ¹ |
| 32 | 128 | 4 | 64 | 4096 | 46.08 | 46.05 | 1.001× | 46.27 | 46.27 |
1.000× ¹ |
| 32 | 128 | 4 | 256 | 4096 | 146.30 | 146.27 | 1.000× | 146.62 | 146.62
| 1.000× ¹ |
| 32 | 128 | 4 | 1 | 16384 | 13.54 | 13.50 | 1.002× | 13.47 | 13.47 |
1.000× ¹ |
| 32 | 128 | 4 | 8 | 16384 | 28.00 | 28.00 | 1.000× | 28.03 | 28.03 |
1.000× ¹ |
| 32 | 128 | 4 | 32 | 16384 | 77.60 | 77.60 | 1.000× | 77.25 | 77.25 |
1.000× ¹ |
| 32 | 128 | 4 | 64 | 16384 | 141.25 | 141.25 | 1.000× | 140.54 | 140.54
| 1.000× ¹ |
| 32 | 128 | 4 | 128 | 16384 | 252.06 | 252.06 | 1.000× | 251.87 |
251.87 | 1.000× ¹ |
| 32 | 128 | 4 | 256 | 16384 | 474.75 | 474.91 | 1.000× | 474.05 |
473.89 | 1.000× ¹ |
| 32 | 128 | 4 | 8 | 65536 | 80.00 | 79.97 | 1.000× | 80.26 | 80.26 |
1.000× ¹ |
| 32 | 128 | 4 | 32 | 65536 | 244.80 | 244.80 | 1.000× | 244.00 | 244.06
| 1.000× ¹ |
| 32 | 128 | 4 | 128 | 65536 | 897.45 | 897.57 | 1.000× | 899.27 |
899.49 | 1.000× ¹ |
| 32 | 128 | 5 | 8 | 4096 | 15.84 | 15.84 | 1.000× | 15.78 | 15.78 |
1.000× ¹ |
| 32 | 128 | 5 | 64 | 4096 | 47.52 | 47.52 | 1.000× | 47.30 | 47.30 |
1.000× ¹ |
| 32 | 128 | 5 | 256 | 4096 | 160.67 | 152.16 | 1.056× | 161.09 | 152.35
| 1.057× |
| 32 | 128 | 5 | 1 | 16384 | 13.47 | 13.47 | 1.000× | 13.44 | 13.44 |
1.000× ¹ |
| 32 | 128 | 5 | 8 | 16384 | 28.29 | 28.29 | 1.000× | 28.45 | 28.45 |
1.000× ¹ |
| 32 | 128 | 5 | 32 | 16384 | 78.75 | 78.75 | 1.000× | 78.78 | 78.82 |
1.000× ¹ |
| 32 | 128 | 5 | 64 | 16384 | 152.48 | 146.53 | 1.041× | 153.12 | 147.01
| 1.042× |
| 32 | 128 | 5 | 128 | 16384 | 283.91 | 261.99 | 1.084× | 283.01 |
261.22 | 1.083× |
| 32 | 128 | 5 | 256 | 16384 | 493.22 | 493.35 | 1.000× | 491.75 |
491.78 | 1.000× ¹ |
| 32 | 128 | 5 | 8 | 65536 | 83.75 | 83.74 | 1.000× | 83.39 | 83.39 |
1.000× ¹ |
| 32 | 128 | 5 | 32 | 65536 | 272.83 | 252.29 | 1.081× | 272.13 | 251.75
| 1.081× |
| 32 | 128 | 5 | 128 | 65536 | 948.61 | 928.58 | 1.022× | 947.85 |
926.53 | 1.023× |
| 32 | 128 | 6 | 8 | 4096 | 15.94 | 15.94 | 1.000× | 15.87 | 15.87 |
1.000× ¹ |
| 32 | 128 | 6 | 64 | 4096 | 47.81 | 47.81 | 1.000× | 47.94 | 47.94 |
1.000× ¹ |
| 32 | 128 | 6 | 256 | 4096 | 156.00 | 156.00 | 1.000× | 156.00 | 155.97
| 1.000× ¹ |
| 32 | 128 | 6 | 1 | 16384 | 13.44 | 13.42 | 1.001× | 13.50 | 13.50 |
1.000× ¹ |
| 32 | 128 | 6 | 8 | 16384 | 28.45 | 28.45 | 1.000× | 28.64 | 28.64 |
1.000× ¹ |
| 32 | 128 | 6 | 32 | 16384 | 80.06 | 80.06 | 1.000× | 79.68 | 79.65 |
1.000× ¹ |
| 32 | 128 | 6 | 64 | 16384 | 149.79 | 149.82 | 1.000× | 149.57 | 149.60
| 1.000× ¹ |
| 32 | 128 | 6 | 128 | 16384 | 272.03 | 272.07 | 1.000× | 269.86 |
269.83 | 1.000× ¹ |
| 32 | 128 | 6 | 256 | 16384 | 527.33 | 508.77 | 1.036× | 528.74 |
509.54 | 1.038× |
| 32 | 128 | 6 | 8 | 65536 | 84.64 | 84.67 | 1.000× | 85.98 | 85.98 |
1.000× ¹ |
| 32 | 128 | 6 | 32 | 65536 | 258.21 | 258.21 | 1.000× | 258.11 | 258.11
| 1.000× ¹ |
| 32 | 128 | 6 | 128 | 65536 | 973.80 | 973.89 | 1.000× | 973.43 |
973.61 | 1.000× ¹ |
| 64 | 64 | 1 | 8 | 4096 | 14.59 | 14.59 | 1.000× | 14.62 | 14.62 |
1.000× ¹ |
| 64 | 64 | 1 | 64 | 4096 | 45.09 | 45.09 | 1.000× | 44.93 | 44.93 |
1.000× ¹ |
| 64 | 64 | 1 | 256 | 4096 | 133.44 | 133.44 | 1.000× | 133.22 | 133.22
| 1.000× ¹ |
| 64 | 64 | 1 | 1 | 16384 | 11.87 | 11.87 | 1.000× | 11.81 | 11.81 |
1.000× ¹ |
| 64 | 64 | 1 | 8 | 16384 | 27.55 | 27.55 | 1.000× | 27.52 | 27.52 |
1.000× ¹ |
| 64 | 64 | 1 | 32 | 16384 | 73.89 | 73.89 | 1.000× | 74.05 | 74.05 |
1.000× ¹ |
| 64 | 64 | 1 | 64 | 16384 | 129.44 | 129.41 | 1.000× | 129.73 | 129.73
| 1.000× ¹ |
| 64 | 64 | 1 | 128 | 16384 | 230.75 | 230.75 | 1.000× | 231.17 | 231.17
| 1.000× ¹ |
| 64 | 64 | 1 | 256 | 16384 | 434.37 | 434.40 | 1.000× | 434.72 | 434.98
| 0.999× ¹ |
| 64 | 64 | 1 | 8 | 65536 | 79.36 | 79.36 | 1.000× | 79.42 | 79.42 |
1.000× ¹ |
| 64 | 64 | 1 | 32 | 65536 | 223.91 | 223.91 | 1.000× | 224.23 | 224.26
| 1.000× ¹ |
| 64 | 64 | 1 | 128 | 65536 | 822.60 | 822.63 | 1.000× | 822.28 | 821.96
| 1.000× ¹ |
| 64 | 64 | 2 | 8 | 4096 | 15.17 | 15.17 | 1.000× | 15.23 | 15.23 |
1.000× ¹ |
| 64 | 64 | 2 | 64 | 4096 | 45.82 | 45.82 | 1.000× | 45.95 | 45.95 |
1.000× ¹ |
| 64 | 64 | 2 | 256 | 4096 | 139.81 | 139.81 | 1.000× | 139.78 | 139.78
| 1.000× ¹ |
| 64 | 64 | 2 | 1 | 16384 | 12.35 | 12.35 | 1.000× | 12.38 | 12.38 |
1.000× ¹ |
| 64 | 64 | 2 | 8 | 16384 | 28.10 | 28.10 | 1.000× | 27.97 | 27.97 |
1.000× ¹ |
| 64 | 64 | 2 | 32 | 16384 | 77.02 | 77.02 | 1.000× | 77.63 | 77.63 |
1.000× ¹ |
| 64 | 64 | 2 | 64 | 16384 | 135.30 | 135.30 | 1.000× | 135.33 | 135.33
| 1.000× ¹ |
| 64 | 64 | 2 | 128 | 16384 | 240.74 | 240.74 | 1.000× | 241.06 | 241.02
| 1.000× ¹ |
| 64 | 64 | 2 | 256 | 16384 | 453.54 | 453.54 | 1.000× | 453.54 | 453.60
| 1.000× ¹ |
| 64 | 64 | 2 | 8 | 65536 | 79.58 | 79.58 | 1.000× | 79.33 | 79.33 |
1.000× ¹ |
| 64 | 64 | 2 | 32 | 65536 | 233.41 | 233.44 | 1.000× | 233.50 | 233.50
| 1.000× ¹ |
| 64 | 64 | 2 | 128 | 65536 | 858.02 | 858.16 | 1.000× | 856.36 | 856.36
| 1.000× ¹ |
| 64 | 64 | 3 | 8 | 4096 | 15.55 | 15.55 | 1.000× | 15.55 | 15.55 |
1.000× ¹ |
| 64 | 64 | 3 | 64 | 4096 | 47.68 | 47.68 | 1.000× | 47.43 | 47.43 |
1.000× ¹ |
| 64 | 64 | 3 | 256 | 4096 | 161.03 | 146.27 | 1.101× | 159.11 | 145.15
| 1.096× |
| 64 | 64 | 3 | 1 | 16384 | 13.02 | 13.02 | 1.000× | 12.99 | 12.99 |
1.000× ¹ |
| 64 | 64 | 3 | 8 | 16384 | 28.16 | 28.16 | 1.000× | 28.00 | 28.00 |
1.000× ¹ |
| 64 | 64 | 3 | 32 | 16384 | 77.54 | 77.54 | 1.000× | 77.54 | 77.54 |
1.000× ¹ |
| 64 | 64 | 3 | 64 | 16384 | 151.94 | 140.03 | 1.085× | 150.91 | 140.10
| 1.077× |
| 64 | 64 | 3 | 128 | 16384 | 278.66 | 278.63 | 1.000× | 279.07 | 279.01
| 1.000× ¹ |
| 64 | 64 | 3 | 256 | 16384 | 499.27 | 499.23 | 1.000× | 501.99 | 502.15
| 1.000× ¹ |
| 64 | 64 | 3 | 8 | 65536 | 82.21 | 82.21 | 1.000× | 81.95 | 81.95 |
1.000× ¹ |
| 64 | 64 | 3 | 32 | 65536 | 268.51 | 241.79 | 1.111× | 268.74 | 241.57
| 1.112× |
| 64 | 64 | 3 | 128 | 65536 | 913.89 | 914.05 | 1.000× | 913.70 | 913.73
| 1.000×² ¹ |
| 64 | 64 | 4 | 8 | 4096 | 15.55 | 15.55 | 1.000× | 15.55 | 15.58 |
0.998× ¹ |
| 64 | 64 | 4 | 64 | 4096 | 50.59 | 50.59 | 1.000× | 50.21 | 50.21 |
1.000× ¹ |
| 64 | 64 | 4 | 256 | 4096 | 156.77 | 156.80 | 1.000× | 156.77 | 156.80
| 1.000× ¹ |
| 64 | 64 | 4 | 1 | 16384 | 13.95 | 13.95 | 1.000× | 13.92 | 13.89 |
1.002× ¹ |
| 64 | 64 | 4 | 8 | 16384 | 30.78 | 30.78 | 1.000× | 30.53 | 30.53 |
1.000× ¹ |
| 64 | 64 | 4 | 32 | 16384 | 83.39 | 83.39 | 1.000× | 83.71 | 83.74 |
1.000× ¹ |
| 64 | 64 | 4 | 64 | 16384 | 148.38 | 148.42 | 1.000× | 147.30 | 147.33
| 1.000× ¹ |
| 64 | 64 | 4 | 128 | 16384 | 290.67 | 290.66 | 1.000× | 288.93 | 288.99
| 1.000×² ¹ |
| 64 | 64 | 4 | 256 | 16384 | 517.22 | 517.22 | 1.000×² | 518.53 |
518.50 | 1.000×² ¹ |
| 64 | 64 | 4 | 8 | 65536 | 85.66 | 85.63 | 1.000× | 86.24 | 86.24 |
1.000× ¹ |
| 64 | 64 | 4 | 32 | 65536 | 278.66 | 278.62 | 1.000×² | 278.75 | 278.79
| 1.000×² ¹ |
| 64 | 64 | 4 | 128 | 65536 | 942.95 | 943.27 | 1.000×² | 944.76 |
944.61 | 1.000×² ¹ |
| 64 | 64 | 5 | 8 | 4096 | 16.90 | 16.90 | 1.000× | 16.99 | 16.96 |
1.002× ¹ |
| 64 | 64 | 5 | 64 | 4096 | 54.30 | 54.34 | 0.999× | 54.43 | 54.43 |
1.000× ¹ |
| 64 | 64 | 5 | 256 | 4096 | 254.72 | 168.64 | 1.510× | 254.75 | 168.90
| 1.508× |
| 64 | 64 | 5 | 1 | 16384 | 14.56 | 14.56 | 1.000× | 14.66 | 14.66 |
1.000× ¹ |
| 64 | 64 | 5 | 8 | 16384 | 34.14 | 34.14 | 1.000× | 34.05 | 34.05 |
1.000× ¹ |
| 64 | 64 | 5 | 32 | 16384 | 87.81 | 87.78 | 1.000× | 87.84 | 87.81 |
1.000× ¹ |
| 64 | 64 | 5 | 64 | 16384 | 160.45 | 160.48 | 1.000× | 159.78 | 159.75
| 1.000× ¹ |
| 64 | 64 | 5 | 128 | 16384 | 415.62 | 415.59 | 1.000× | 416.52 | 416.58
| 1.000×² ¹ |
| 64 | 64 | 5 | 256 | 16384 | 919.53 | 919.65 | 1.000× | 919.62 | 919.68
| 1.000× ¹ |
| 64 | 64 | 5 | 8 | 65536 | 91.33 | 91.33 | 1.000× | 92.03 | 92.00 |
1.000× ¹ |
| 64 | 64 | 5 | 32 | 65536 | 508.99 | 508.96 | 1.000× | 510.95 | 511.07
| 1.000× ¹ |
| 64 | 64 | 5 | 128 | 65536 | 1739.72 | 1739.47 | 1.000× | 1740.12 |
1740.27 | 1.000× ¹ |
| 64 | 64 | 6 | 8 | 4096 | 17.28 | 17.25 | 1.002× | 17.34 | 17.34 |
1.000× ¹ |
| 64 | 64 | 6 | 64 | 4096 | 55.46 | 55.49 | 0.999× | 55.62 | 55.59 |
1.001× ¹ |
| 64 | 64 | 6 | 256 | 4096 | 261.50 | 261.49 | 1.000× | 261.44 | 261.57
| 1.000× ¹ |
| 64 | 64 | 6 | 1 | 16384 | 14.78 | 14.43 | 1.024× | 14.85 | 14.43 |
1.029× |
| 64 | 64 | 6 | 8 | 16384 | 32.74 | 32.74 | 1.000× | 32.67 | 32.70 |
0.999× ¹ |
| 64 | 64 | 6 | 32 | 16384 | 92.38 | 92.42 | 1.000× | 91.20 | 91.20 |
1.000× ¹ |
| 64 | 64 | 6 | 64 | 16384 | 215.68 | 177.57 | 1.215× | 216.10 | 177.15
| 1.220× |
| 64 | 64 | 6 | 128 | 16384 | 419.46 | 419.49 | 1.000×² | 418.88 |
418.88 | 1.000×² ¹ |
| 64 | 64 | 6 | 256 | 16384 | 931.33 | 931.40 | 1.000× | 931.46 | 931.53
| 1.000×² ¹ |
| 64 | 64 | 6 | 8 | 65536 | 96.64 | 96.67 | 1.000× | 95.81 | 95.84 |
1.000× ¹ |
| 64 | 64 | 6 | 32 | 65536 | 521.16 | 521.09 | 1.000× | 517.88 | 517.99
| 1.000× ¹ |
| 64 | 64 | 6 | 128 | 65536 | 1738.95 | 1738.51 | 1.000×² | 1737.15 |
1737.19 | 1.000×² ¹ |

The kernel's other Cake variants are the dense FP4 and FP8
lightning-indexer logits and the paged FP8 MQA logits for SM100a/SM103a
(`deepgemm_dense_mqa`), while this paged FP8 package ships on sm_120a
only.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Expanded SM120 FP8 logits support for additional batch-size
configurations across head counts 32 and 64, page sizes 64 and 128, and
selected context-window variants.
* Added coverage for selected `c4k` configurations. Unchanged
configurations retain their existing behavior.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [b754f7e](https://github.com/flashinfer-ai/flashinfer/commit/b754f7e6bdeb69667903566ff8afe4d66fb4d093)

- **作者**: Alex Yang
- **时间**: 2026-10-30T19:00:17Z
- **提交信息**: Add MSA section to CODEOWNERS file (#8039)

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
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/...`

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
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Chores**
* Updated repository maintenance metadata to clarify review ownership
for MSA-related work areas.
* No changes were made to user-facing functionality, workflows, or
available features. Application behavior and the way users interact with
it remain unchanged.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [e5b74c0](https://github.com/flashinfer-ai/flashinfer/commit/e5b74c056710162be3803ed742ea84e9d1e57aa7)

- **作者**: eigen
- **时间**: 2026-10-30T18:50:35Z
- **提交信息**: refactor(cake_mhc): deterministic names for the mHC autograd backend (#8028)

This PR renames the mHC with-grad training backend to deterministic
("det") canonical names. Here, deterministic means that for a fixed
input, GPU, execution plan and initial accumulator state, repeated runs
produce bitwise-identical outputs and gradients. The guarantee holds per
architecture and plan. It does not extend across architectures, shapes
or reduction plans.

**Renames**

- Modules: `flashinfer.cake_mhc_train`,
`flashinfer.cake_mhc_train_backend` and
`flashinfer.cake_mhc_train_head_backend` become
`flashinfer.cake_mhc_det_train`, `flashinfer.cake_mhc_det_train_backend`
and `flashinfer.cake_mhc_det_train_head_backend`.
- Autograd classes: `CakeMHCTrain{Prepare,Finish,Head}Function` become
`CakeMHCDetTrain{Prepare,Finish,Head}Function`.
- Functions: `cake_mhc_train_*` becomes `cake_mhc_det_train_*`. Examples
are `cake_mhc_det_train_forward_prepare`,
`cake_mhc_det_train_backward_finish` and the head functions.
- Generated kernel sources, CUDA symbols and libraries now use the
`cake_mhc_det_train_*` names.

**Compatibility**

- The old module paths and old top-level names still import as explicit
aliases of the same objects.
`tests/cpu/mhc/test_cake_mhc_det_train_aliases.py` checks that each
alias is the same object as its new name.
- Behavior is unchanged. For all 489 kernel configurations, the SASS is
byte-identical to before except for symbol names. Routing is also
unchanged.

**Validation**

Tested on B200 (sm_100a) and GB300 (sm_103a), one node each, with CUDA
13.4 and PyTorch 2.14.1+cu130:

- `tests/mhc` and `tests/cpu/mhc`: 367 passed, 0 failed on each GPU.
- Bitwise comparison against `main` across 552 outputs and gradients
found 0 mismatches. This covered training at T ∈ {1, 1024, 4096, 8192,
14928, 16263} with hidden 4096, and the head at hidden 4096/5120/7168.
There were two separate runs per GPU.
- Repeated runs were bitwise identical.
- sm_107a was not tested for this change.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added deterministic four-stream mHC training and training-head APIs,
including forward and backward operations, autograd support, and
workspace management.
* Added support for selected NVIDIA GPU architectures and hidden sizes.

* **Compatibility**
* Existing mHC training and training-head API names remain available as
aliases to the deterministic APIs.

* **Documentation**
  * Updated mHC training guidance to use the deterministic API names.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [ed68b15](https://github.com/flashinfer-ai/flashinfer/commit/ed68b15bef1c6ce5e2cf6a0b233ab127b9713ec4)

- **作者**: kangbintNV
- **时间**: 2026-10-30T18:33:21Z
- **提交信息**: docs: fix v0.7.3 API reference gaps (#7993)

<!-- .github/pull_request_template.md -->

## 📌 Description

Fix the public API documentation findings identified for v0.7.3rc1:

- add the three missing autosummary entries for
  `nvfp4_kv_materialize_fp8`, `token_sparse_kv_indices`, and
  `group_union_masks`;
- document that `MSASparseAttentionWorkspace` supports SM107 only for
the
  packed-NVFP4 paged-KV prefill/decode routes;
- preserve the complete `GDNPagedPrefillSlots.output_state_indices`
meaning in
  generated docs;
- annotate Unified `BatchAttention.plan(sm_scale)` as `Optional[float]`,
  matching its existing `None` behavior;

This PR changes documentation and one type annotation only. Runtime
behavior is
unchanged.

## 🔍 Related Issues

N/A

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

## 🧪 Tests

- [x] Tests have been added or updated as needed
(documentation/type-only; no runtime test changes needed).
- [ ] All tests are passing (`unittest`, etc.).

Validation performed:

- targeted `pre-commit run --files ...`: passed
- full docstring checker: 445 APIs scanned, 0 completeness failures, 0
  argument mismatches
- full API/RST checker: all three report targets cleared; one unrelated
  pre-existing `sampling_softmax` gap remains on `main`
- `python scripts/check_pr_document.py --base origin/main --head HEAD
--strict`:
  0 new findings

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

- The global checker currently also reports a pre-existing, unrelated
`flashinfer.logits_processor.operators.sampling_softmax` gap on `main`;
this
  PR intentionally does not expand into that separate issue.
- GitHub documentation checks are rerun for every PR update.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Documentation**
* Added guidance on converting active NVFP4 KV-cache pages to FP8 for
attention kernels that cannot read NVFP4 directly.
* Documented token-sparse attention inputs, including cache-slot lists
and grouped key unions and masks.
* Clarified NVFP4 cache dimensions, scale-factor formats, backend
requirements, output and LSE shapes, and storage-width constraints.
* Updated guidance on output-state indices and SM107 workspace support.
  * Clarified that `sm_scale` is optional and defaults to `None`.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [60cb4a0](https://github.com/flashinfer-ai/flashinfer/commit/60cb4a0d1c82d78f9354168891f9849d256a5326)

- **作者**: eigen
- **时间**: 2026-10-30T18:22:44Z
- **提交信息**: feat(cake_gdn): Add det to public entry-point names with grad (#8027)

The public entry points of `flashinfer.experimental.cake_gdn_det_train`
now include `det` in their names. The package provides deterministic,
packed, variable-length Gated DeltaNet chunked training (forward and
backward) on one GPU. The new names match the package name and the
deterministic naming used by the other training backends:

- `chunk_gated_delta_rule` -> `chunk_gated_delta_rule_det`
- `ChunkGatedDeltaRuleFunction` -> `ChunkGatedDeltaRuleDetFunction`
- `gdn_chunk_forward` -> `gdn_chunk_det_forward`
- `gdn_chunk_backward` -> `gdn_chunk_det_backward`

The old names are still exported in `__all__` of both the package and
`cake_chain`. They are aliases bound to the same objects, so existing
callers keep working, and a test checks that each old name is its det
counterpart. Text that cites FLA's `chunk_gated_delta_rule` signature
keeps FLA's name. The README example and the tests now use the det
names.

The kernel sources were renamed to the same det convention, so the
generated CUDA sources are regenerated. 58 csrc files get new file names
and program identifiers, and `build.json` and `cake_jit.py` are updated
to match. The kernel code is unchanged. On sm_100a, sm_103a and sm_107a
(29 programs each), the SASS of the built libraries is identical to the
current package's, so performance does not change. Outputs and gradients
are bitwise equal to the current package on B200, GB300 and R200.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added explicitly named deterministic APIs for gated delta rule
operations, while keeping the previous API names available as aliases.
* **Documentation**
* Updated the example to use the deterministic entry point and
documented the compatibility aliases.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [4cad15c](https://github.com/flashinfer-ai/flashinfer/commit/4cad15cac63da3ff297436b167706f20a95baf3d)

- **作者**: eigen
- **时间**: 2026-10-30T18:07:31Z
- **提交信息**: refactor(cake_gdn): deterministic KCP names for the context-parallel GDN autograd package (#8022)

Cake's context-parallel GDN (gated delta rule, scalar gate) training
kernel has one data-type variant. Q, K, V, out and dout are BF16, while
the scalar log-decay g and beta are FP32 per token and value head. dq
and dk are reduced in FP32 over the value heads of each Q/K head and
converted to the output type once. The grouped head counts (H_qk, HV)
are runtime parameters, and the production shape is (16, 48). The kernel
supports three partition layouts: contiguous, whole-buffer zigzag, and
per-document zigzag + ragged. Its fused forms are a forward pass, a
backward pass from the saved set, and checkpoint replay (non-reentrant
and reentrant). It also has an optional causal-conv1d halo exchange and
exact cross-rank state passing. This PR delivers the same variant under
deterministic names. The package moves to
`flashinfer.experimental.cake_gdn_det_train_kcp`, and the entry module
is now `flashinfer.cake_gdn_det_train_kcp`. The public functions become
`chunk_gdn_det_kcp`, `chunk_gdn_det_fwd_kcp`, `chunk_gdn_det_bwd_kcp`,
`partition_det_kcp` and `build_context_det_kcp`. The workspace, saved
and comm byte helpers and the option and context types are renamed the
same way. The old import paths `flashinfer.experimental.cake_gdn_train`
and `flashinfer.gdn_train` and the old names stay as aliases of the same
objects. Kernel libraries are renamed `cake_gdn_det_train_<digest>`,
with a `_kcp` suffix on the context-parallel-only programs. The
generated kernels are unchanged. The baseline is the previous Cake
version of this package (FlashInfer main 30fe579) on an NVIDIA B200
(sm_100a, CUDA 13.4). The comparison covers 60 shapes (5 packs x CP {2,
4, 8, 16} x 3 layouts). Against that baseline, the geometric-mean
speedup is 1.000x for forward and 1.001x for the training step, and
per-row values range from 0.99x to 1.03x. Because the kernels are
identical, this spread is measurement noise around 1.00x. The table
below has one row per shape.

**NVIDIA B200 (sm_100a, CUDA 13.4)** — context-parallel GDN layer,
`(H_qk, HV) = (16, 48)`, head dim 128, CP = 2, 4, 8, 16; latency per
call of the slowest rank (median over repeats); CP 2: median over 2
back-to-back session(s) on the same nodes; CP 4: median over 2
back-to-back session(s) on the same nodes; CP 8: median over 2
back-to-back session(s) on the same nodes; CP 16: median over 4
back-to-back session(s) on the same nodes. Forward = module forward;
training step = forward + checkpoint recompute + backward, communication
included. Baseline: the previous version of this package (FlashInfer
main 30fe579) on the same layout.

| Pack (tokens / docs) | CP | Layout | Forward: this PR ms | previous ms
| Speedup | Training step: this PR ms | previous ms | Speedup |
|---|---:|---|---:|---:|---:|---:|---:|---:|
| P1 (241,817 tokens / 6 docs) | 2 | contiguous | 8.763 | 8.773 | 1.00x
| 26.511 | 26.553 | 1.00x |
| P1 (241,817 tokens / 6 docs) | 2 | zigzag | 8.575 | 8.570 | 1.00x |
26.683 | 26.695 | 1.00x |
| P1 (241,817 tokens / 6 docs) | 2 | per-document zigzag + ragged |
8.886 | 8.888 | 1.00x | 27.249 | 27.167 | 1.00x |
| P1 (241,817 tokens / 6 docs) | 4 | contiguous | 4.675 | 4.679 | 1.00x
| 14.125 | 14.138 | 1.00x |
| P1 (241,817 tokens / 6 docs) | 4 | zigzag | 4.600 | 4.605 | 1.00x |
13.894 | 13.898 | 1.00x |
| P1 (241,817 tokens / 6 docs) | 4 | per-document zigzag + ragged |
4.788 | 4.788 | 1.00x | 14.453 | 14.457 | 1.00x |
| P1 (241,817 tokens / 6 docs) | 8 | contiguous | 2.529 | 2.524 | 1.00x
| 7.645 | 7.631 | 1.00x |
| P1 (241,817 tokens / 6 docs) | 8 | zigzag | 2.709 | 2.713 | 1.00x |
8.086 | 8.086 | 1.00x |
| P1 (241,817 tokens / 6 docs) | 8 | per-document zigzag + ragged |
2.748 | 2.746 | 1.00x | 8.306 | 8.299 | 1.00x |
| P1 (241,817 tokens / 6 docs) | 16 | contiguous | 1.924 | 1.952 | 1.01x
| 6.354 | 6.364 | 1.00x |
| P1 (241,817 tokens / 6 docs) | 16 | zigzag | 2.035 | 2.037 | 1.00x |
5.952 | 5.927 | 1.00x |
| P1 (241,817 tokens / 6 docs) | 16 | per-document zigzag + ragged |
3.077 | 3.073 | 1.00x | 8.568 | 8.585 | 1.00x |
| P2 (261,987 / 3) | 2 | contiguous | 9.198 | 9.218 | 1.00x | 28.730 |
28.739 | 1.00x |
| P2 (261,987 / 3) | 2 | zigzag | 9.254 | 9.257 | 1.00x | 28.814 |
28.882 | 1.00x |
| P2 (261,987 / 3) | 2 | per-document zigzag + ragged | 9.351 | 9.359 |
1.00x | 29.352 | 29.265 | 1.00x |
| P2 (261,987 / 3) | 4 | contiguous | 4.733 | 4.738 | 1.00x | 14.249 |
14.247 | 1.00x |
| P2 (261,987 / 3) | 4 | zigzag | 5.004 | 4.999 | 1.00x | 15.081 |
15.084 | 1.00x |
| P2 (261,987 / 3) | 4 | per-document zigzag + ragged | 5.337 | 5.342 |
1.00x | 15.975 | 15.984 | 1.00x |
| P2 (261,987 / 3) | 8 | contiguous | 2.606 | 2.604 | 1.00x | 7.829 |
7.823 | 1.00x |
| P2 (261,987 / 3) | 8 | zigzag | 2.928 | 2.932 | 1.00x | 8.671 | 8.672
| 1.00x |
| P2 (261,987 / 3) | 8 | per-document zigzag + ragged | 2.850 | 2.851 |
1.00x | 8.573 | 8.566 | 1.00x |
| P2 (261,987 / 3) | 16 | contiguous | 1.972 | 1.977 | 1.00x | 6.346 |
6.368 | 1.00x |
| P2 (261,987 / 3) | 16 | zigzag | 2.114 | 2.116 | 1.00x | 6.176 | 6.159
| 1.00x |
| P2 (261,987 / 3) | 16 | per-document zigzag + ragged | 2.553 | 2.551 |
1.00x | 7.162 | 7.183 | 1.00x |
| P3 (259,174 / 2) | 2 | contiguous | 9.407 | 9.405 | 1.00x | 28.754 |
28.713 | 1.00x |
| P3 (259,174 / 2) | 2 | zigzag | 8.986 | 8.992 | 1.00x | 28.395 |
28.549 | 1.01x |
| P3 (259,174 / 2) | 2 | per-document zigzag + ragged | 8.993 | 8.987 |
1.00x | 28.307 | 28.326 | 1.00x |
| P3 (259,174 / 2) | 4 | contiguous | 4.701 | 4.708 | 1.00x | 14.410 |
14.414 | 1.00x |
| P3 (259,174 / 2) | 4 | zigzag | 4.710 | 4.704 | 1.00x | 14.388 |
14.392 | 1.00x |
| P3 (259,174 / 2) | 4 | per-document zigzag + ragged | 5.323 | 5.322 |
1.00x | 15.931 | 15.935 | 1.00x |
| P3 (259,174 / 2) | 8 | contiguous | 2.665 | 2.661 | 1.00x | 7.892 |
7.894 | 1.00x |
| P3 (259,174 / 2) | 8 | zigzag | 2.899 | 2.900 | 1.00x | 8.604 | 8.606
| 1.00x |
| P3 (259,174 / 2) | 8 | per-document zigzag + ragged | 2.899 | 2.899 |
1.00x | 8.706 | 8.703 | 1.00x |
| P3 (259,174 / 2) | 16 | contiguous | 2.094 | 2.092 | 1.00x | 6.365 |
6.455 | 1.01x |
| P3 (259,174 / 2) | 16 | zigzag | 2.104 | 2.102 | 1.00x | 6.097 | 6.146
| 1.01x |
| P3 (259,174 / 2) | 16 | per-document zigzag + ragged | 2.371 | 2.369 |
1.00x | 6.709 | 6.741 | 1.00x |
| P4 (254,976 / 1) | 2 | contiguous | 9.229 | 9.229 | 1.00x | 28.245 |
28.249 | 1.00x |
| P4 (254,976 / 1) | 2 | zigzag | 8.840 | 8.840 | 1.00x | 27.853 |
27.915 | 1.00x |
| P4 (254,976 / 1) | 2 | per-document zigzag + ragged | 8.869 | 8.866 |
1.00x | 28.059 | 28.112 | 1.00x |
| P4 (254,976 / 1) | 4 | contiguous | 4.588 | 4.596 | 1.00x | 13.877 |
13.884 | 1.00x |
| P4 (254,976 / 1) | 4 | zigzag | 4.624 | 4.617 | 1.00x | 13.969 |
13.967 | 1.00x |
| P4 (254,976 / 1) | 4 | per-document zigzag + ragged | 4.772 | 4.767 |
1.00x | 14.431 | 14.428 | 1.00x |
| P4 (254,976 / 1) | 8 | contiguous | 2.530 | 2.550 | 1.01x | 7.589 |
7.596 | 1.00x |
| P4 (254,976 / 1) | 8 | zigzag | 2.875 | 2.876 | 1.00x | 8.524 | 8.527
| 1.00x |
| P4 (254,976 / 1) | 8 | per-document zigzag + ragged | 2.918 | 2.917 |
1.00x | 8.768 | 8.756 | 1.00x |
| P4 (254,976 / 1) | 16 | contiguous | 1.872 | 1.873 | 1.00x | 6.420 |
6.382 | 0.99x |
| P4 (254,976 / 1) | 16 | zigzag | 2.132 | 2.128 | 1.00x | 6.213 | 6.130
| 0.99x |
| P4 (254,976 / 1) | 16 | per-document zigzag + ragged | 2.271 | 2.277 |
1.00x | 6.875 | 6.875 | 1.00x |
| P5 (249,856 / 4) | 2 | contiguous | 8.909 | 8.896 | 1.00x | 27.656 |
27.644 | 1.00x |
| P5 (249,856 / 4) | 2 | zigzag | 9.302 | 9.299 | 1.00x | 28.366 |
28.412 | 1.00x |
| P5 (249,856 / 4) | 2 | per-document zigzag + ragged | 9.101 | 9.094 |
1.00x | 28.059 | 28.015 | 1.00x |
| P5 (249,856 / 4) | 4 | contiguous | 4.551 | 4.552 | 1.00x | 13.967 |
13.973 | 1.00x |
| P5 (249,856 / 4) | 4 | zigzag | 4.627 | 4.631 | 1.00x | 14.082 |
14.084 | 1.00x |
| P5 (249,856 / 4) | 4 | per-document zigzag + ragged | 4.849 | 4.844 |
1.00x | 14.682 | 14.679 | 1.00x |
| P5 (249,856 / 4) | 8 | contiguous | 2.563 | 2.564 | 1.00x | 7.647 |
7.656 | 1.00x |
| P5 (249,856 / 4) | 8 | zigzag | 2.795 | 2.795 | 1.00x | 8.295 | 8.296
| 1.00x |
| P5 (249,856 / 4) | 8 | per-document zigzag + ragged | 2.706 | 2.701 |
1.00x | 8.213 | 8.211 | 1.00x |
| P5 (249,856 / 4) | 16 | contiguous | 1.990 | 1.991 | 1.00x | 6.131 |
6.307 | 1.03x |
| P5 (249,856 / 4) | 16 | zigzag | 2.061 | 2.059 | 1.00x | 5.925 | 5.996
| 1.01x |
| P5 (249,856 / 4) | 16 | per-document zigzag + ragged | 2.661 | 2.666 |
1.00x | 7.476 | 7.474 | 1.00x |

This kernel's other Cake variant is the single-rank deterministic GDN
training package `flashinfer.experimental.cake_gdn_det_train`, which
follows FLA's `chunk_gated_delta_rule` signature, and this package
covers sm_100a, sm_103a and sm_107a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added a deterministic, context-parallel GDN training API with forward,
backward, autograd, and memory-estimation helpers.
* Added support checks and configurable options for partitioning,
checkpointing, recomputation, and workspace management.
* **Compatibility**
* Preserved legacy GDN training import paths and names as aliases to the
new API.
* **Documentation**
* Updated usage examples and benchmark guidance for the deterministic
training API.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [78515ec](https://github.com/flashinfer-ai/flashinfer/commit/78515ec558b9f8d3eaefc1f5e3b2c6e220aa01e3)

- **作者**: eigen
- **时间**: 2026-10-30T18:04:45Z
- **提交信息**: perf(cake_gated_act_mxfp8): band-path program for the SM107 forward both entry below 2^20 (#8023)

The Cake fused SwiGLU + MXFP8 quantization kernel computes silu(gate) *
up from a BF16 input [M, 2K] and quantizes the result to MXFP8. It
stores one E8M0 scale (RCEIL rounding) per 32 E4M3 values, in the
swizzled 128 x 4 layout. The kernel has one data type and six forms. The
forward form is `flashinfer.silu_and_mul_mxfp8_quantize` and the
backward form is `flashinfer.silu_and_mul_mxfp8_quantize_backward`. Each
can write rowwise, colwise or both outputs.
`flashinfer.cake_gated_act_mxfp8_backend` runs one program per call and
picks it by M * K for each architecture. This PR changes program
selection for one forward entry on sm_107a (R200). When M * K is below
2^20, forward both now runs the called band path at 4 CTAs per SM. From
2^20 up to 2^23, the previous program still runs, with no band-path or
occupancy setting. Sizes above that are unchanged. The sm_100a and
sm_103a programs are unchanged. The package goes from 74 to 75 per-arch
programs across 62 records. One record is new and applies to sm_107a
only, and one existing record now starts at 2^20 on sm_107a. The other
libraries keep the same machine code.

The baseline is the previous Cake version of this kernel, which is the
package on FlashInfer main from #7880. With block-scaled inputs the
changed owner row is faster: 128 x 128 forward both is 1.076x (2.36 us
-> 2.20 us). The same entry also covers 256 x 256 and 512 x 512 forward
both. Measured outside the owner list, these are 1.085x and 1.081x with
block-scaled inputs. With unit-normal inputs the changed rows tie within
the run-to-run spread (128 x 128 forward both is 1.004x). Every other
row runs the same machine code as before and stays within run-to-run
noise. Over all 30 rows, unit normals range from 0.998x to 1.004x and
block-scaled inputs from 0.999x to 1.076x.

The table covers the owner rows on NVIDIA R200 (sm_107a, 216 SMs) with
CUDA 13.4: 5 shapes x 6 passes, 30 rows. Both versions run in the same
process on the same GPU, in 8 alternating paired rounds, with a cold L2
before every launch. Latency is the mean over pairs of each sample's
median CUPTI kernel time, in microseconds. Speedup is the previous
latency divided by this PR's latency, so a value above 1 means this PR
is faster. Block-scaled inputs are normals with per-32-block scales
spread over a wide exponent range. Outputs are byte-identical to the
previous version, and the public API is unchanged.

### NVIDIA R200 (sm_107a, 216 SMs), CUDA 13.4

| M x K | Pass | Unit normals: previous Cake (µs) | This PR (µs) |
Speedup | Block-scaled: previous Cake (µs) | This PR (µs) | Speedup |
|---|---|---:|---:|---:|---:|---:|---:|
| 128 x 128 | fwd rowwise | 1.87 | 1.87 | 0.998x | 2.01 | 2.01 | 0.999x
|
| 128 x 128 | fwd colwise | 2.03 | 2.03 | 0.998x | 2.17 | 2.17 | 1.001x
|
| 128 x 128 | fwd both | 2.10 | 2.09 | 1.004x | 2.36 | 2.20 | 1.076x |
| 128 x 128 | bwd rowwise | 2.13 | 2.12 | 1.000x | 2.31 | 2.31 | 1.000x
|
| 128 x 128 | bwd colwise | 2.23 | 2.23 | 1.001x | 2.28 | 2.28 | 1.000x
|
| 128 x 128 | bwd both | 2.35 | 2.35 | 1.000x | 2.45 | 2.45 | 0.999x |
| 4096 x 2048 | fwd rowwise | 7.12 | 7.13 | 1.000x | 8.12 | 8.11 |
1.001x |
| 4096 x 2048 | fwd colwise | 7.18 | 7.18 | 1.000x | 8.69 | 8.70 |
1.000x |
| 4096 x 2048 | fwd both | 8.51 | 8.51 | 1.000x | 10.07 | 10.07 | 1.000x
|
| 4096 x 2048 | bwd rowwise | 10.10 | 10.10 | 1.000x | 10.35 | 10.35 |
1.000x |
| 4096 x 2048 | bwd colwise | 10.63 | 10.63 | 1.000x | 11.24 | 11.25 |
1.000x |
| 4096 x 2048 | bwd both | 12.67 | 12.66 | 1.000x | 13.31 | 13.29 |
1.002x |
| 4096 x 7168 | fwd rowwise | 17.75 | 17.75 | 1.000x | 19.17 | 19.17 |
1.000x |
| 4096 x 7168 | fwd colwise | 18.04 | 18.04 | 1.000x | 20.95 | 20.94 |
1.000x |
| 4096 x 7168 | fwd both | 21.02 | 21.02 | 1.000x | 25.41 | 25.40 |
1.000x |
| 4096 x 7168 | bwd rowwise | 27.05 | 27.05 | 1.000x | 27.71 | 27.72 |
1.000x |
| 4096 x 7168 | bwd colwise | 27.51 | 27.51 | 1.000x | 29.19 | 29.20 |
1.000x |
| 4096 x 7168 | bwd both | 33.91 | 33.90 | 1.000x | 34.94 | 34.86 |
1.002x |
| 16384 x 7168 | fwd rowwise | 56.92 | 56.93 | 1.000x | 64.34 | 64.30 |
1.001x |
| 16384 x 7168 | fwd colwise | 57.79 | 57.78 | 1.000x | 67.11 | 67.11 |
1.000x |
| 16384 x 7168 | fwd both | 70.39 | 70.39 | 1.000x | 75.77 | 75.74 |
1.000x |
| 16384 x 7168 | bwd rowwise | 92.87 | 92.86 | 1.000x | 96.73 | 96.77 |
1.000x |
| 16384 x 7168 | bwd colwise | 93.98 | 93.98 | 1.000x | 103.08 | 103.05
| 1.000x |
| 16384 x 7168 | bwd both | 123.56 | 123.55 | 1.000x | 125.56 | 125.50 |
1.000x |
| 131072 x 8192 | fwd rowwise | 462.66 | 462.66 | 1.000x | 515.03 |
514.74 | 1.001x |
| 131072 x 8192 | fwd colwise | 483.20 | 483.20 | 1.000x | 539.91 |
539.75 | 1.000x |
| 131072 x 8192 | fwd both | 610.50 | 610.56 | 1.000x | 621.14 | 621.18
| 1.000x |
| 131072 x 8192 | bwd rowwise | 796.30 | 796.29 | 1.000x | 829.40 |
829.42 | 1.000x |
| 131072 x 8192 | bwd colwise | 810.45 | 810.46 | 1.000x | 869.06 |
869.34 | 1.000x |
| 131072 x 8192 | bwd both | 1095.04 | 1095.07 | 1.000x | 1109.63 |
1109.66 | 1.000x |

Cake has no other variants of this kernel beyond these six BF16-to-MXFP8
forms with the swizzled scale layout, and the family ships on sm_100a
(B200), sm_103a (GB300) and sm_107a (R200).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added support for gated-activation MXFP8 processing on a new GPU
architecture.
* Added an optimized processing path for compatible workloads, with
performance routing based on workload size.
  * This support requires CUDA 13.4.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [d1bed93](https://github.com/flashinfer-ai/flashinfer/commit/d1bed93d69d172fd8f9af96cf14f4f869ac488ef)

- **作者**: eigen
- **时间**: 2026-10-30T17:02:11Z
- **提交信息**: perf(cake_tinygemm2_tcgen05): add 4 unbiased routing windows on sm_100a (B200) (#8018)

`cake_tinygemm2_tcgen05` is the Cake backend of
`flashinfer.gemm.tinygemm_bf16`, which computes BF16 `out = input @
weight.T (+ bias)` for small batches. It supports only BF16. It contains
36 generated tcgen05 programs: nine tiles, each built with and without
bias and with and without PDL. #7302 added the backend, and #7370
unrolled its narrow tile and retuned its windows. #7519 added the
swap-AB per-chain-accumulator tile, early tensor-memory free, two M=64
packed tiles and retuned windows. #7588 promoted the sm_107a narrow
tile's tensor maps to L2 256 B and sent 17-23-row unbiased GEMMs with
small activations to the packed tile on sm_107a. #7656 added
PACKED_BOX8, the packed tile with an 8-row activation box and 8 batch
rows per CTA. #7735 added PACKED_M64_N8, an M=64 tile that computes 16
output features and 8 batch rows per CTA with an exact 8-row activation
box, built for sm_107a only, and widened the sm_107a windows for 8-row
unbiased GEMMs. #7826 built PACKED_M64_N8 for sm_100a and sm_103a and
added unbiased routing windows on sm_100a, sm_103a and sm_107a. #7973
added unbiased routing windows on sm_100a, sm_103a and sm_107a,
including PACKED for 9-16-row shapes on B200 and GB300.

This PR changes routing only, and only on sm_100a (B200). It adds 4
routing windows for unbiased GEMMs to the sm_100a table and changes no
program: no generated source changes, and every program's machine code
is unchanged. Routing on sm_103a and sm_107a does not change. The
windows send shapes that no existing window admits to existing tiles:
PACKED_BOX8 for 8-row shapes with 3584-4608 output features,
PACKED_M64_N8 for 1-7-row shapes with 8193-9215 output features (only
when K is a multiple of 64), and PACKED for 9-16-row shapes with
4097-4223 output features. Routing with a bias does not change, shapes
outside the new windows keep their current kernel, and outputs stay
bit-for-bit equal to `csrc/tinygemm2.cu`. The baseline is what
`tinygemm_bf16` runs on FlashInfer main today: the reference `tinygemm2`
kernel in every rerouted case, and `tinygemm2_sm100` (with bias) or the
reference kernel (without bias) for shapes that main does not route to
Cake. Per-case speedup is baseline median / Cake median, each median
over 3 runs on 3 GPUs. The new routing is 1.05-2.18x faster than main on
B200 across 200 measured unbiased cases (196 shapes; 38 with PDL on, 162
with PDL off). The largest gains are on the 9-16-row shapes that now run
PACKED: 1.60-2.18x.

The table below gives B200 CUPTI kernel times in µs for 16 shapes (batch
x out x K), with and without bias, PDL off, cold L2. Each time is the
median over 3 runs on 3 B200 GPUs. None of these shapes changes kernel,
so the 1.00x-1.01x ratios are noise. A † marks rows that neither side
routes to a Cake program. A ‡ marks rows where both sides run the same
Cake program, and this PR does not change that program's machine code.

**NVIDIA B200 (sm_100a, 148 SMs), CUDA 13.4, PyTorch 2.14.1+cu130**

| batch x out x K | with bias: baseline / Cake (µs) | speedup | without
bias: baseline / Cake (µs) | speedup |
| --- | --- | --- | --- | --- |
| 1 x 128 x 720 | 2.70 / 2.69 | 1.01x † | 2.83 / 2.82 | 1.01x † |
| 1 x 128 x 14336 | 6.21 / 6.21 | 1.00x ‡ | 6.21 / 6.21 | 1.00x ‡ |
| 2 x 16 x 256 | 2.61 / 2.59 | 1.01x † | 2.66 / 2.66 | 1.00x † |
| 4 x 2880 x 2880 | 6.78 / 6.78 | 1.00x † | 7.17 / 7.17 | 1.00x ‡ |
| 7 x 128 x 4096 | 3.87 / 3.87 | 1.00x ‡ | 3.84 / 3.84 | 1.00x ‡ |
| 8 x 128 x 7168 | 4.59 / 4.61 | 1.00x ‡ | 4.58 / 4.58 | 1.00x ‡ |
| 8 x 1024 x 1024 | 3.01 / 3.01 | 1.00x † | 3.17 / 3.17 | 1.00x † |
| 13 x 1024 x 2048 | 3.97 / 3.97 | 1.00x † | 4.10 / 4.10 | 1.00x † |
| 16 x 2880 x 2880 | 7.07 / 7.07 | 1.00x ‡ | 7.17 / 7.17 | 1.00x ‡ |
| 64 x 4096 x 3072 | 9.03 / 9.06 | 1.00x ‡ | 8.99 / 9.02 | 1.00x ‡ |
| 16 x 1024 x 1024 | 3.07 / 3.07 | 1.00x † | 3.17 / 3.17 | 1.00x † |
| 8 x 2048 x 2048 | 4.61 / 4.61 | 1.00x † | 4.77 / 4.77 | 1.00x † |
| 8 x 4096 x 4096 | 9.76 / 9.76 | 1.00x † | 10.08 / 10.08 | 1.00x ‡ |
| 16 x 4096 x 3072 | 8.26 / 8.26 | 1.00x ‡ | 8.26 / 8.26 | 1.00x ‡ |
| 64 x 4096 x 4096 | 11.58 / 11.58 | 1.00x ‡ | 11.68 / 11.65 | 1.00x ‡ |
| 4 x 128 x 256 | 2.53 / 2.53 | 1.00x † | 2.72 / 2.72 | 1.00x † |

The window table has one row per new window, in routing order. Its
columns are the batch, output-feature and K ranges ("multiple of 64"
where required), the tile, the measured cases (PDL-on count in
parentheses), the speedup range, and the baseline / Cake times of the
cases with the smallest and largest speedup. A shape uses the first
window that admits it. "PDL" marks PDL-on cases.

| GPU | batch | out | K | tile | cases (PDL on) | speedup | slowest
gain: baseline / Cake (µs) | fastest gain: baseline / Cake (µs) |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| B200 | 8 | 4480-4608 | 2048-8192 | PACKED_BOX8 | 26 (12) | 1.05-1.32x
| 8x4480x5568 PDL: 14.75 / 14.03 | 8x4480x2056: 10.40 / 7.90 |
| B200 | 8 | 3584-4479 | 6152-8192 | PACKED_BOX8 | 23 (11) | 1.08-1.16x
| 8x4448x7168 PDL: 17.06 / 15.81 | 8x3584x6152 PDL: 15.82 / 13.68 |
| B200 | 1-7 | 8193-9215 | 2048-4096, multiple of 64 | PACKED_M64_N8 |
59 (7) | 1.11-1.37x | 1x8208x3072: 16.00 / 14.40 | 5x8208x2048: 13.89 /
10.14 |
| B200 | 9-16 | 4097-4223 | 2048-12288 | PACKED | 92 (8) | 1.60-2.18x |
14x4192x5120: 19.01 / 11.90 | 11x4208x2056: 16.64 / 7.65 |

Cake has no other data type, layout or fused form of this kernel,
`tinygemm2_sm100` remains the with-bias path outside the windows, and
the family covers sm_100a, sm_103a and sm_107a (B200, GB300 and R200
class GPUs), with every tile built for all three.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Expanded SM100 GEMM kernel selection for additional matrix shapes,
including cases with 8 rows, 1–7 rows, and 9–16 rows.
* Updated selection at several output-feature boundaries, allowing more
shapes to use a matching kernel.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [5874ad0](https://github.com/flashinfer-ai/flashinfer/commit/5874ad06a2cdaf3e617d63be4144a65182adf098)

- **作者**: eigen
- **时间**: 2026-10-30T16:02:21Z
- **提交信息**: perf(cake_kimi_k3_fused_router): faster one-token routing on B200 (#8016)

`flashinfer.fused_moe.kimi_k3_fused_router` is FlashInfer's experimental
Kimi-K3 fused MoE router. It takes FP32 gate logits and bias (896
experts, top-16). In one launch, it selects the top-16 experts per token
and builds the `moe_align_block_size` route plan that grouped MoE GEMMs
consume. Its one variant, FP32 logits and bias with `block_m` 8 and 16,
is covered on sm_100a and sm_103a. This PR changes the 1-token cells at
`block_m` 8 and 16 on sm_100a. Their programs now rank their 16 winners
from a certified window and zero the expert counts and scatter offsets
at kernel entry. Outputs are bitwise identical to FlashInfer main. No
other cell's device program changes on either GPU, so sm_103a is
unchanged. "FlashInfer main" in the tables is the previous Cake version
of this kernel: the router programs FlashInfer main ships today (from
#7941). On B200, the 1-token cell drops from 2.768 us to 2.655 us at
`block_m` 8 (1.04x) and from 2.704 us to 2.591 us at `block_m` 16
(1.04x).

NVIDIA B200 (sm_100a, 148 SMs), CUDA 13.4, median kernel latency per
cell (28 cells); speedup = FlashInfer main / this PR. `new` marks the 2
cells whose device program this PR changes, with both programs measured
in the same process. `same` cells run a byte-identical program, so both
columns hold one measurement of that unchanged program and their 1.00x
is not a speedup.

| tokens | block_m | FlashInfer main (us) | this PR (us) | speedup |
kernel |
|---:|---:|---:|---:|---:|---|
| 1 | 8 | 2.768 | 2.655 | 1.04x | new |
| 1 | 16 | 2.704 | 2.591 | 1.04x | new |
| 2 | 8 | 3.039 | 3.039 | 1.00x | same |
| 2 | 16 | 3.056 | 3.056 | 1.00x | same |
| 4 | 8 | 3.216 | 3.216 | 1.00x | same |
| 4 | 16 | 2.976 | 2.976 | 1.00x | same |
| 8 | 8 | 3.264 | 3.264 | 1.00x | same |
| 8 | 16 | 3.232 | 3.232 | 1.00x | same |
| 16 | 8 | 3.200 | 3.200 | 1.00x | same |
| 16 | 16 | 3.296 | 3.296 | 1.00x | same |
| 32 | 8 | 3.552 | 3.552 | 1.00x | same |
| 32 | 16 | 3.488 | 3.488 | 1.00x | same |
| 64 | 8 | 5.216 | 5.216 | 1.00x | same |
| 64 | 16 | 5.088 | 5.088 | 1.00x | same |
| 128 | 8 | 5.440 | 5.440 | 1.00x | same |
| 128 | 16 | 5.409 | 5.409 | 1.00x | same |
| 256 | 8 | 5.728 | 5.728 | 1.00x | same |
| 256 | 16 | 5.728 | 5.728 | 1.00x | same |
| 512 | 8 | 7.136 | 7.136 | 1.00x | same |
| 512 | 16 | 7.136 | 7.136 | 1.00x | same |
| 1024 | 8 | 9.632 | 9.632 | 1.00x | same |
| 1024 | 16 | 9.504 | 9.504 | 1.00x | same |
| 2048 | 8 | 12.576 | 12.576 | 1.00x | same |
| 2048 | 16 | 12.544 | 12.544 | 1.00x | same |
| 4096 | 8 | 17.248 | 17.248 | 1.00x | same |
| 4096 | 16 | 17.392 | 17.392 | 1.00x | same |
| 8192 | 8 | 22.960 | 22.960 | 1.00x | same |
| 8192 | 16 | 22.976 | 22.976 | 1.00x | same |

NVIDIA GB300 (sm_103a, 152 SMs), CUDA 13.4, median kernel latency per
cell (28 cells); speedup = FlashInfer main / this PR. This PR changes no
device program on sm_103a, so every cell is `same`: both columns hold
one measurement of the unchanged program, and the 1.00x is not a
speedup.

| tokens | block_m | FlashInfer main (us) | this PR (us) | speedup |
kernel |
|---:|---:|---:|---:|---:|---|
| 1 | 8 | 2.880 | 2.880 | 1.00x | same |
| 1 | 16 | 2.656 | 2.656 | 1.00x | same |
| 2 | 8 | 3.088 | 3.088 | 1.00x | same |
| 2 | 16 | 3.040 | 3.040 | 1.00x | same |
| 4 | 8 | 2.928 | 2.928 | 1.00x | same |
| 4 | 16 | 3.040 | 3.040 | 1.00x | same |
| 8 | 8 | 3.184 | 3.184 | 1.00x | same |
| 8 | 16 | 3.328 | 3.328 | 1.00x | same |
| 16 | 8 | 3.104 | 3.104 | 1.00x | same |
| 16 | 16 | 3.168 | 3.168 | 1.00x | same |
| 32 | 8 | 3.424 | 3.424 | 1.00x | same |
| 32 | 16 | 3.392 | 3.392 | 1.00x | same |
| 64 | 8 | 5.088 | 5.088 | 1.00x | same |
| 64 | 16 | 4.896 | 4.896 | 1.00x | same |
| 128 | 8 | 5.376 | 5.376 | 1.00x | same |
| 128 | 16 | 5.408 | 5.408 | 1.00x | same |
| 256 | 8 | 5.584 | 5.584 | 1.00x | same |
| 256 | 16 | 5.632 | 5.632 | 1.00x | same |
| 512 | 8 | 6.976 | 6.976 | 1.00x | same |
| 512 | 16 | 7.072 | 7.072 | 1.00x | same |
| 1024 | 8 | 8.928 | 8.928 | 1.00x | same |
| 1024 | 16 | 8.960 | 8.960 | 1.00x | same |
| 2048 | 8 | 11.776 | 11.776 | 1.00x | same |
| 2048 | 16 | 11.904 | 11.904 | 1.00x | same |
| 4096 | 8 | 16.416 | 16.416 | 1.00x | same |
| 4096 | 16 | 16.577 | 16.577 | 1.00x | same |
| 8192 | 8 | 21.712 | 21.712 | 1.00x | same |
| 8192 | 16 | 21.680 | 21.680 | 1.00x | same |

Cake ships no other data type, layout or fused form of this router, and
the family ships on sm_100a and sm_103a only, so these two tables cover
all of its variants and architectures.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added specialized Kimi K3 fused routing support for SM100 and SM103
GPUs, selecting 16 experts from 896 and producing routing weights,
expert IDs, and related routing data.
* Added checks for input tensor types, layouts, devices, and launch
dimensions, with errors reported for invalid inputs or failed launches.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [6fc0938](https://github.com/flashinfer-ai/flashinfer/commit/6fc09388a8cd9e4f2a0af8c7f29990a08817156a)

- **作者**: eigen
- **时间**: 2026-10-30T15:23:50Z
- **提交信息**: perf(cake_fused_qk_rope_fp8_append): persistent stage for GB300 prefill of few long requests (#8012)

The Cake fused QK RMSNorm + NeoX RoPE + paged KV-cache append kernel has
two data-type variants in FlashInfer: BF16 (`cake_fused_qk_rope_append`)
and FP8 E4M3 (`cake_fused_qk_rope_fp8_append`). This PR changes only the
FP8 variant. It adds no new stage or program. The stage
`fp8_e4m3_min_blocks10_persistent1` already ships for sm_100a and
sm_103a. This PR changes only the GB300 stage policy. On GB300 (sm_103a,
152 SMs), some prefill calls now use this stage. Each call must meet
three conditions. It has 1 to 16 requests. It has more than four waves
(`(num_rows + num_requests) x num_kv_heads` above 4 x 9 x 152 CTAs). It
averages at least 64 new rows per request (`num_rows >= 64 x
num_requests`). This rule is checked first in the GB300 table. Before
this PR, the changed row used `fp8_e4m3_grid_order3` on GB300. Shorter
requests keep their previous GB300 stages. This includes the swapped
grid order `fp8_e4m3_grid_order2` for multi-request prefill of many KV
heads. All other calls keep their stages. The stage launches a
persistent grid: ten resident CTAs per SM times the SM count, rounded
down to a multiple of the KV-head count and capped at the item count
(`(num_rows + num_requests) x num_kv_heads`). Each resident CTA runs the
table validation scan, the scale loads and the validity vote once. It
then loops over its items of one KV head with the same per-item math and
stores as the existing stages. Its outputs are bitwise identical to the
previous stage on every measured row. The baseline is the FP8 package on
FlashInfer main (9f5c44ea10), which is the previous Cake version and
includes #7842. The changed row, `X_prefill_64x8_B1_Q1024_q1_n2`, goes
from 15.906 to 14.218 µs, a 1.1187x speedup (1.1154x to 1.1211x per
session). The other 43 rows run identical device code and launch grids
in both packages. Their ratios of 0.9884 to 1.0092 are measurement
spread, and the 44-row geomean is 1.0019x. Stage selection on H100
(sm_90a), B200 (sm_100a) and B300 (sm_103a, 148 SMs) is unchanged.

Measured with the same harness as #7772. Speedup = FlashInfer main /
this PR, from CUPTI kernel time with a cold L2 and CUDA-graph replay.
For each side, the value is the mean over 8 sessions of the 10 %-trimmed
mean. Both packages are built by FlashInfer's JIT with CUDA 13.4, called
through the public API and timed interleaved on the same GPU in one
process. "This PR" is the mean of the PR package and a second, identical
build of it. A `*` after a shape name marks the row whose stage changes.
Row names: `64x8`/`8x1` are query/KV heads (head_dim 128). `q1`/`q2`
mean Q is quantized with a dynamic per-token/per-head scale (`q1`) or a
static scale (`q2`). `n0`/`n1`/`n2` mean no RMSNorm, RoPE then RMSNorm,
or RMSNorm then RoPE. `P_decode` is 32 requests x 1 new token and
`P_prefill` is 8 requests x 16 new tokens, with 2048 cached tokens and
page size 64 unless the name says otherwise.
`E_prefill_*_q127/q128/q129` is 4 requests x 127/128/129 new tokens,
which is the 128-row scale-padding boundary. In `X_*` rows,
`B1`/`B128`/`B256` = 1/128/256 requests, `Q1024` = 1024 new tokens,
`page16`/`page128` = page size 16/128, `ctx32768` = 32768 cached tokens,
`outkv` = caller-owned `out_k`/`out_v`, `ragged` = 8 requests with
ragged new-token counts, and `maxseq1024` = 8 requests x 16 new tokens
with max_seqlen 1024.

**NVIDIA GB300, sm_103a (152 SMs), CUDA 13.4. Speedup = FlashInfer main
/ this PR.**

| shape | FlashInfer main (µs) | this PR (µs) | speedup (main / this PR)
|
|---|---:|---:|---:|
| `E_prefill_64x8_q127` | 9.124 | 9.074 | 1.0054 |
| `E_prefill_64x8_q128` | 9.116 | 9.118 | 0.9997 |
| `E_prefill_64x8_q129` | 9.678 | 9.629 | 1.0051 |
| `E_prefill_8x1_q127` | 3.589 | 3.600 | 0.9969 |
| `E_prefill_8x1_q128` | 3.605 | 3.605 | 1.0001 |
| `E_prefill_8x1_q129` | 3.601 | 3.643 | 0.9884 |
| `P_decode_64x8_q1_n0` | 3.475 | 3.482 | 0.9981 |
| `P_decode_64x8_q1_n1` | 3.612 | 3.600 | 1.0034 |
| `P_decode_64x8_q1_n2` | 3.567 | 3.588 | 0.9942 |
| `P_decode_64x8_q2_n0` | 3.463 | 3.458 | 1.0015 |
| `P_decode_64x8_q2_n1` | 3.523 | 3.541 | 0.9948 |
| `P_decode_64x8_q2_n2` | 3.524 | 3.513 | 1.0032 |
| `P_decode_8x1_q1_n0` | 2.991 | 3.012 | 0.9930 |
| `P_decode_8x1_q1_n1` | 3.164 | 3.151 | 1.0042 |
| `P_decode_8x1_q1_n2` | 3.153 | 3.149 | 1.0013 |
| `P_decode_8x1_q2_n0` | 3.031 | 3.010 | 1.0069 |
| `P_decode_8x1_q2_n1` | 3.155 | 3.158 | 0.9989 |
| `P_decode_8x1_q2_n2` | 3.179 | 3.150 | 1.0092 |
| `P_prefill_64x8_q1_n0` | 3.938 | 3.932 | 1.0014 |
| `P_prefill_64x8_q1_n1` | 4.164 | 4.148 | 1.0039 |
| `P_prefill_64x8_q1_n2` | 4.143 | 4.142 | 1.0001 |
| `P_prefill_64x8_q2_n0` | 3.900 | 3.893 | 1.0018 |
| `P_prefill_64x8_q2_n1` | 4.145 | 4.138 | 1.0017 |
| `P_prefill_64x8_q2_n2` | 4.140 | 4.134 | 1.0015 |
| `P_prefill_8x1_q1_n0` | 3.118 | 3.152 | 0.9893 |
| `P_prefill_8x1_q1_n1` | 3.251 | 3.257 | 0.9981 |
| `P_prefill_8x1_q1_n2` | 3.227 | 3.238 | 0.9964 |
| `P_prefill_8x1_q2_n0` | 3.087 | 3.080 | 1.0026 |
| `P_prefill_8x1_q2_n1` | 3.190 | 3.206 | 0.9952 |
| `P_prefill_8x1_q2_n2` | 3.172 | 3.171 | 1.0005 |
| `X_decode_64x8_B128_q1_n2` | 6.783 | 6.782 | 1.0002 |
| `X_decode_64x8_B1_q1_n2` | 2.955 | 2.975 | 0.9933 |
| `X_decode_64x8_B256_q1_n2` | 11.370 | 11.387 | 0.9985 |
| `X_decode_8x1_B128_q1_n2` | 3.424 | 3.423 | 1.0001 |
| `X_decode_8x1_B1_q1_n2` | 2.881 | 2.911 | 0.9899 |
| `X_decode_8x1_B256_q1_n2` | 3.881 | 3.903 | 0.9944 |
| `X_decode_8x1_q1_n2_ctx32768` | 3.157 | 3.164 | 0.9977 |
| `X_decode_8x1_q1_n2_outkv` | 2.983 | 2.968 | 1.0049 |
| `X_decode_8x1_q1_n2_page128` | 3.189 | 3.174 | 1.0048 |
| `X_decode_8x1_q1_n2_page16` | 3.110 | 3.132 | 0.9930 |
| `X_prefill_64x8_B1_Q1024_q1_n2` * | 15.906 | 14.218 | 1.1187 |
| `X_prefill_8x1_B1_Q1024_q1_n2` | 4.345 | 4.335 | 1.0023 |
| `X_prefill_8x1_q1_n2_maxseq1024` | 3.232 | 3.237 | 0.9983 |
| `X_prefill_8x1_ragged_q1_n2` | 3.324 | 3.327 | 0.9990 |

The BF16 variant `cake_fused_qk_rope_append` is unchanged, and the FP8
package ships programs for sm_90a, sm_100a and sm_103a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* Updated prefill execution selection for qualifying GB300 workloads,
including larger row counts and request patterns. Long-prefill workloads
may benefit from improved performance.
* Persistent execution is now selected consistently across tested cases
on supported GPU architectures.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [85be8d0](https://github.com/flashinfer-ai/flashinfer/commit/85be8d0392ed6801da94788ac0a8a3e262f96070)

- **作者**: eigen
- **时间**: 2026-10-30T13:36:13Z
- **提交信息**: perf(cake_dsa_indexer): fuse the first two radix-select passes of the sampled sm_100a scan program (#8009)

This PR speeds up `flashinfer.dsa_indexer.dsa_indexer_topk`, the Cake
DSA indexer top-k scan (BF16 queries and keys, FP32 head weights and
scores), on GB200 (sm_100a). It changes only the sampled sm_100a l6 scan
program and its longest-first copy. These programs now fuse the first
two radix-select passes, the same method #7971 applied to the sm_103a
pair program: the first pass also histograms the next key byte of
candidates that share the top byte, and when the first pass selects that
byte, the second pass skips its sweep, while selection stays exact and
results stay bitwise identical. The baseline is the previous Cake
version, which is the package on FlashInfer main (its sm_100a programs
are the ones #7953 shipped), on GB200 with CUDA 13.4. Speedup is the
previous time divided by this PR's time. Four kernel shapes run the
changed program: S2 (single 16k document) gains 1.02x (1.263 -> 1.236
ms), Z3 (packed 4k-64k documents, full causal) 1.02x (25.523 -> 25.020
ms), Z3cp (packed 4k-64k documents, CP16 rank 0) 1.02x (1.420 -> 1.386
ms) and S1 (single 8k document) 1.01x (0.438 -> 0.434 ms). Rows that use
unchanged programs run the same binary on both sides; their 0.98x-1.03x
spread is run-to-run variation, and the lowest of them is P1 at 0.98x
(3.279 -> 3.333 ms). On the reporter's rank files from #7549
(equal-clock timing), output bits are identical, the packed 4k-64k ranks
gain 1.00x (rank 5: 2.264 -> 2.256 ms) and the 262k-document ranks are
unchanged. Across the 80 packed CP16 rank inputs that run the changed
program, the gain is 1.01x-1.03x (median 1.02x).

**GB200** (NVIDIA GB200, sm_100a, 152 SMs, CUDA 13.4). Reporter's rank
files (equal-clock timing); ms = mean over 2 runs of the per-run median;
rank / median = the rank's time over its mix's median rank.

| rank file | previous ms | previous sampling-off ms | previous rank /
median | this PR ms | this PR rank / median | speedup |
|---|---|---|---|---|---|---|
| doc262k_rank03_slow | 11.571 | 12.635 | 1.007 | 11.568 | 1.008 | 1.00x
|
| doc262k_rank13_fast | 11.403 | 12.768 | 0.993 | 11.392 | 0.992 | 1.00x
|
| pack4k-64k_rank05_slow | 2.264 | 3.176 | 1.006 | 2.256 | 1.006 | 1.00x
|
| pack4k-64k_rank08_fast | 2.235 | 3.203 | 0.994 | 2.228 | 0.994 | 1.00x
|

**GB200** kernel rows; ms = median over processes (both arm orders) of
the CUPTI kernel time; speedup = previous / this PR.

| row | shape | T (queries) | Tkv (keys) | segments | top-k | previous
ms | this PR ms | speedup |
|---|---|---|---|---|---|---|---|---|
| P1 | recorded packed call | 16231 | 268757 | 8 | 2048 | 3.279 | 3.333
| 0.98x |
| P1_peaked | P1 with dominating keys | 16231 | 268757 | 8 | 2048 |
3.362 | 3.306 | 1.02x |
| P2 | second recorded token count, boundaries derived | 16172 | 267520
| 8 | 2048 | 3.317 | 3.257 | 1.02x |
| P3 | P1 with top-k 4096 | 16231 | 268757 | 8 | 4096 | 3.559 | 3.541 |
1.01x |
| S1 | single causal document N = 8192 | 8192 | 8192 | 1 | 2048 | 0.438
| 0.434 | 1.01x |
| S2 | single causal document N = 16384 | 16384 | 16384 | 1 | 2048 |
1.263 | 1.236 | 1.02x |
| S3 | single causal document N = 32768 | 32768 | 32768 | 1 | 2048 |
3.999 | 4.013 | 1.00x |
| S4 | single causal document N = 65536 | 65536 | 65536 | 1 | 2048 |
14.975 | 14.895 | 1.01x |
| S5 | single causal document N = 131072 | 131072 | 131072 | 1 | 2048 |
54.391 | 54.429 | 1.00x |
| S6 | single causal document N = 262144 | 262144 | 262144 | 1 | 2048 |
210.870 | 211.360 | 1.00x |
| S7 | single causal document N = 524288 | 524288 | 524288 | 1 | 2048 |
859.770 | 859.470 | 1.00x |
| S4_peaked | S4 with dominating keys | 65536 | 65536 | 1 | 2048 |
14.608 | 14.620 | 1.00x |
| C1 | CP tail 4096 x 65536 | 4096 | 65536 | 1 | 2048 | 1.731 | 1.738 |
1.00x |
| C2 | CP tail 4096 x 131072 | 4096 | 131072 | 1 | 2048 | 3.312 | 3.311
| 1.00x |
| C3 | packed 8 x (2048 x 32768) | 16384 | 262144 | 8 | 2048 | 3.428 |
3.394 | 1.01x |
| V1 | N = 65536, ratio 2 | 65536 | 32768 | 1 | 2048 | 8.054 | 8.057 |
1.00x |
| V2 | N = 65536, top-k 256 | 65536 | 65536 | 1 | 256 | 13.375 | 13.380
| 1.00x |
| V3 | N = 65536, top-k 4096 | 65536 | 65536 | 1 | 4096 | 15.744 |
15.773 | 1.00x |
| S8 | single causal document N = 1048576 | 1048576 | 1048576 | 1 | 2048
| 3814.466 | 3817.691 | 1.00x |
| Z1 | #7042 repro: 262k document, CP16 zigzag rank 0 | 16384 | 270336 |
2 | 2048 | 13.488 | 13.423 | 1.00x |
| Z1k4096 | Z1 with top-k 4096 | 16384 | 270336 | 2 | 4096 | 13.923 |
13.921 | 1.00x |
| Z1k256 | Z1 with top-k 256 | 16384 | 270336 | 2 | 256 | 13.119 |
13.150 | 1.00x |
| Z2 | 8 x 32k documents, full causal | 262144 | 262144 | 8 | 2048 |
34.303 | 34.481 | 0.99x |
| Z2cp | 8 x 32k documents, CP16 zigzag rank 0 | 16384 | 270336 | 16 |
2048 | 1.946 | 1.951 | 1.00x |
| Z3 | packed 4k-64k documents, full causal | 169984 | 169984 | 8 | 2048
| 25.523 | 25.020 | 1.02x |
| Z3cp | packed 4k-64k documents, CP16 zigzag rank 0 | 10624 | 175296 |
16 | 2048 | 1.420 | 1.386 | 1.02x |
| P1sink | recorded P1 geometry with sink statistics | 16231 | 268757 |
8 | 2048 | 3.297 | 3.204 | 1.03x |
| S4sink | one 64k causal document, sink statistics | 65536 | 65536 | 1
| 2048 | 15.198 | 15.111 | 1.01x |
| S6sink | one 262k causal document, sink statistics | 262144 | 262144 |
1 | 2048 | 216.686 | 216.794 | 1.00x |
| A1 | split tail: 4 queries in one segment | 4 | 22018 | 1 | 2048 |
0.123 | 0.123 | 1.00x |
| A2 | split tail: 4 queries in one segment | 4 | 30466 | 1 | 2048 |
0.126 | 0.126 | 1.00x |
| A3 | split tail: 4 queries in one segment | 4 | 41986 | 1 | 2048 |
0.106 | 0.107 | 0.99x |

Cake ships no other variant of this kernel; this variant ships on
sm_100a (B200/GB200), sm_103a (GB300) and sm_107a, and this PR changes
only sm_100a programs.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* Optimized candidate selection on supported GPUs by reusing
intermediate results in some selection steps.
* Added architecture-specific handling for candidate filtering and
output generation. Other GPU architectures retain their existing
behavior.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery Huang <averyh@nvidia.com>

### [9a7f792](https://github.com/flashinfer-ai/flashinfer/commit/9a7f7923fc11a9f2412d3403553a28ac79aec0b4)

- **作者**: eigen
- **时间**: 2026-10-30T13:30:17Z
- **提交信息**: fix(cake_kda): record a shared KCP workspace's storages on a stream switch, with grad (#8008)

Part of #7815.

## Problem

#7955 (merged) added one `KcpWorkspace` shared by prepared packs, plus a
stream rule: a call on another stream does one `wait_stream` on the
workspace's last stream. Review feedback on #7955 pointed out the gap
this PR fixes, but #7955 merged before the fix landed.

- A call on a new stream can make the workspace replace or drop a pool,
the arena or a scratch buffer. When that happens, the caching allocator
returns the freed block to the free list of the stream that allocated
it. Work queued on the old stream may still be using that block.
- With only `wait_stream` (current main), the new stream waits for the
old one, but the storages are never recorded on the new stream. A block
freed while the new stream's queued work still uses it can therefore be
handed to another allocation on the old stream.
- The new tests reproduce this on merged main in 3 of 3 runs on GB300,
GB200 and R200:
- **Allocator row fails:** while the other stream is busy, a fresh
allocation on the first stream receives all 5 released blocks (90-114 MB
arena, pools, scratch).
  - **Census row fails:** 0 of 7 live storages are recorded.
- **Bitwise row fails** on GB300 and GB200, with NaN outputs after
poisoned reuse.

## Change

`cake_kcp.py` (+66/-12), README (6 lines).

- `ensure()` and `reserve()` call the stream rule before any pool or
arena can be sized, replaced or released.
- A call on a stream other than the workspace's last one waits for that
stream (wait_stream) and records every live workspace storage on its own
stream (record_stream) before any pool or arena can be released, so a
replaced or dropped storage is reused only after every stream that used
it has run its queued work; calls on one stream do neither, and nothing
is recorded during CUDA-graph capture.
- These live storages are recorded:
  - distinct pools
  - the local arena and its identity buffer
  - the scratch buffer of the arena and of each view
  - the uploads of the knob table sets the workspace holds
- Same-stream calls take the existing early return, with no wait and no
record. Nothing is recorded during CUDA graph capture because capture
allocations live in the graph pool.
- Host time per call on GB200 (this PR / main, same-stream path):
forward 0.949-0.996, backward 0.963-0.993.

## Tests

`tests/experimental/test_cake_kda_train_kcp_shared_ws.py` (+212/-18)

- **3 new rows:**
- **Allocator row:** a storage from a switched stream is not reused
while the other stream still runs.
- **Census row:** every live storage is recorded exactly on a stream
switch and never on same-stream calls.
  - **Bitwise row:** checks outputs after poisoned reuse.
- **De-flaked stream-rule row:**
`test_gpu_call_on_another_stream_waits_for_the_last_one` now uses event
ordering instead of timing.
- **Why it was flaky:** it asserted that the second stream was still
pending after a 0.3 s host sleep while the first stream ran a nominal
1.5 s `torch.cuda._sleep`. The sleep calibration reads low on an idle
GPU (1.66e6 vs 2.07e6 cycles/ms on GB300), so the sleep lasted about 1.2
s and the assertion depended on node speed. It failed on one slower
node.
- **What it does now:** it records an event on the first stream after
that stream's call, synchronizes the dependent work and asserts that the
event completed. The switch rows retry an inconclusive attempt with a
longer sleep instead of failing.
- **Mutant check:** with `wait_stream` removed, the new stream-rule row
fails 30 of 30 in each of 4 runs on GB300 and GB200. The runs covered
repeat, cold calibration, and a second process loading the GPU. With
this PR, the row passes 30/30 in each run, 50/50 in-process and 10/10
isolated.

Counts are passed/skipped/failed, main vs this PR. There are 0 failures
everywhere.

| file | GB300 (sm_103a) | GB200 (sm_100a) | R200 (sm_107a), 1 GPU |
|---|---|---|---|
| test_cake_kda_train_kcp | 722/0/0 both | 722/0/0 both | 722 both |
| test_cake_kda_train_kcp_shared_ws | 25/3/0 -> 28/3/0 | 25/3/0 ->
28/3/0 | 19 -> 22 passed (multi-GPU rows not applicable on 1 GPU) |
| test_cake_kda_train_kcp_dist | 23/3/0 both | 23/3/0 both | 3 passed
(multi-GPU rows n/a) |
| kcp_build / kcp_upload / api | 25 / 18 / 12 both | same | same |
| conv kcp / build / knobs / api / kcp_dist | 38 / 8 / 11 / 3 / 7+3
skipped both | same | 38 / 8 / 11 / 3 |

- On 4-GPU nodes, the skipped rows are 8-GPU rows.
- The 4-GPU rows of shared_ws pass on GB300 and GB200. These are 3
shared-workspace rows and 3 recompute-handle rows.
- pre-commit is clean.

Validated on main `3472ad3ab`, then rebased cleanly onto current main;
range-diff is unchanged for both commits. Between the two bases, main
changed no line of `cake_kcp.py` or this test file. The only change was
a new #7985 section in the KDA README.

## Not covered

- R200 multi-GPU rows (shared_ws 4-GPU rows, kcp_dist) have not been run
yet. R200 ran only the single-GPU rows.
- 8-GPU rows have not been run.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Workspace storage is now safely reused across CUDA streams only after
previously queued work has completed, preventing premature reuse while
another stream is still using it.
* Switching streams preserves correct results without blocking the host.
Calls on the same stream avoid unnecessary synchronization and storage
tracking.
* **Documentation**
* Clarified when workspace storage is reused and when stream tracking
occurs.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [5d60811](https://github.com/flashinfer-ai/flashinfer/commit/5d60811431d040ed62f85c7a7906a77a6e72cccc)

- **作者**: lunarz-dev
- **时间**: 2026-10-30T11:42:16Z
- **提交信息**: feat(benchmarks): allow prims-ts attention backends on SM107 (#7997)

### [30fe579](https://github.com/flashinfer-ai/flashinfer/commit/30fe579954f6e92ec265361505124d3f72acb361)

- **作者**: eigen
- **时间**: 2026-10-30T10:48:28Z
- **提交信息**: perf(cake_moe_grouped_gemm): probed die split of the tile queues for the sm_100a dgrad down projection (#7998)

FlashInfer's experimental ragged BF16 MoE grouped GEMM has a Cake
backend (`flashinfer.experimental.cake_moe_grouped_gemm`, also reached
through `grouped_mm_bf16(..., backend="cake")`) with four variants. They
are three operations over E groups of rows given by device offsets: the
forward Y = X W[e]^T and the data gradient dX = G W[e], both with BF16
output, and the weight gradient dW[e] = G^T X, with BF16 or FP32 output.
This PR is a host-side change that extends the probed die split of the
tile claim queues from PR #7975 (sm_103a) to sm_100a (B200), with the
same scope: the data gradient of the down projection (weights of at most
6144 x 2048 elements per group). B200 dies can hold unequal SM pair
counts (for example 35 / 39). Kernels and output bits are unchanged, and
GPUs whose two dies hold equal SM pair counts keep the even split's
behavior. The baseline (main in the table) is the Cake version currently
on FlashInfer main, which includes PR #7975. It was timed in the same
process on the same GPU, interleaved with this PR, over the 58 shape
rows; the ms columns are each side's median kernel time with a cold L2,
and the speedup column is the median of the per-round paired ratios
(main / this PR). The bold rows are the 9 data-gradient down-projection
rows, which take the probed split. On node 1 they are 1.016x-1.038x
faster, and each is faster in every interleaved round. Node 2 runs at
its power limit on these shapes. There, the 3 E=4, M=112576 bold rows
are 1.016x-1.021x faster, each faster in every round. The 3 E=4,
M=136064 bold rows are 0.998x, slower in every round. The E=8, E=16 and
E=32 bold rows read 0.994x-1.008x and overlap the run-to-run spread. A
third B200 GPU (35 / 39 die split), timed on the 9 bold rows only, reads
1.025x-1.037x; 8 of the 9 are faster in every round, and the other
overlaps the spread. The other 49 rows run exactly what main runs, and
their readings of 0.994x-1.011x on both nodes are measurement spread.

NVIDIA B200, sm_100a, CUDA 13.4 (node 1 and node 2 are two different
B200 GPUs, each with a 35 / 39 die split):

| shape | B200 node 1: main ms | B200 node 1: this PR ms | B200 node 1:
speedup | B200 node 2: main ms | B200 node 2: this PR ms | B200 node 2:
speedup |
|---|---:|---:|---:|---:|---:|---:|
| fwd gate_up (N=4096, K=6144), E=4, M=112576, balanced | 4.1376 |
4.1370 | 1.000x | 4.0238 | 4.0233 | 1.000x |
| fwd gate_up (N=4096, K=6144), E=4, M=112576, skewed | 4.1377 | 4.1373
| 1.000x | 4.0258 | 4.0271 | 1.000x |
| fwd gate_up (N=4096, K=6144), E=4, M=112576, one-empty | 4.1376 |
4.1371 | 1.000x | 4.0261 | 4.0250 | 1.000x |
| fwd gate_up (N=4096, K=6144), E=4, M=136064, balanced | 4.9985 |
4.9979 | 1.000x | 4.8507 | 4.8477 | 1.000x |
| fwd gate_up (N=4096, K=6144), E=4, M=136064, skewed | 4.9958 | 5.0050
| 0.998x | 4.8699 | 4.8723 | 0.999x |
| fwd gate_up (N=4096, K=6144), E=4, M=136064, one-empty | 4.9961 |
4.9956 | 1.000x | 4.8673 | 4.8672 | 1.000x |
| dgrad gate_up (N=4096, K=6144), E=4, M=112576, balanced | 4.0599 |
4.0607 | 1.000x | 3.9661 | 3.9274 | 1.008x |
| dgrad gate_up (N=4096, K=6144), E=4, M=112576, skewed | 4.1042 |
4.1042 | 1.000x | 3.9507 | 3.9513 | 1.000x |
| dgrad gate_up (N=4096, K=6144), E=4, M=112576, one-empty | 4.0721 |
4.0848 | 0.998x | 3.9507 | 3.9512 | 1.000x |
| dgrad gate_up (N=4096, K=6144), E=4, M=136064, balanced | 4.9632 |
4.9621 | 1.000x | 4.7817 | 4.7843 | 0.999x |
| dgrad gate_up (N=4096, K=6144), E=4, M=136064, skewed | 5.0170 |
4.9827 | 1.002x | 4.7857 | 4.7947 | 1.000x |
| dgrad gate_up (N=4096, K=6144), E=4, M=136064, one-empty | 4.9066 |
4.9078 | 1.000x | 4.7893 | 4.7896 | 1.000x |
| wgrad gate_up (N=4096, K=6144), E=4, M=112576, balanced | 4.1672 |
4.1649 | 1.000x | 4.2806 | 4.2335 | 1.011x |
| wgrad gate_up (N=4096, K=6144), E=4, M=112576, skewed | 4.2882 |
4.2865 | 1.000x | 4.3414 | 4.3419 | 1.000x |
| wgrad gate_up (N=4096, K=6144), E=4, M=112576, one-empty | 4.2982 |
4.2978 | 1.000x | 4.2878 | 4.2879 | 1.000x |
| wgrad gate_up (N=4096, K=6144), E=4, M=136064, balanced | 5.0618 |
5.0190 | 1.008x | 5.1556 | 5.1558 | 1.000x |
| wgrad gate_up (N=4096, K=6144), E=4, M=136064, skewed | 5.2525 |
5.2523 | 1.000x | 5.2289 | 5.2295 | 1.000x |
| wgrad gate_up (N=4096, K=6144), E=4, M=136064, one-empty | 5.1923 |
5.1925 | 1.000x | 5.1882 | 5.1800 | 1.001x |
| fwd down (N=6144, K=2048), E=4, M=112576, balanced | 2.0463 | 2.0467 |
1.000x | 1.9966 | 1.9968 | 1.000x |
| fwd down (N=6144, K=2048), E=4, M=112576, skewed | 2.0448 | 2.0446 |
1.000x | 1.9938 | 1.9941 | 1.000x |
| fwd down (N=6144, K=2048), E=4, M=112576, one-empty | 2.0333 | 2.0411
| 0.998x | 1.9938 | 1.9942 | 1.000x |
| fwd down (N=6144, K=2048), E=4, M=136064, balanced | 2.4591 | 2.4599 |
1.000x | 2.4369 | 2.4365 | 1.000x |
| fwd down (N=6144, K=2048), E=4, M=136064, skewed | 2.4705 | 2.4703 |
1.000x | 2.4415 | 2.4417 | 1.000x |
| fwd down (N=6144, K=2048), E=4, M=136064, one-empty | 2.4619 | 2.4642
| 0.999x | 2.4272 | 2.4315 | 1.000x |
| **dgrad down (N=6144, K=2048), E=4, M=112576, balanced** | 2.1110 |
2.0391 | 1.035x | 2.0397 | 2.0010 | 1.019x |
| **dgrad down (N=6144, K=2048), E=4, M=112576, skewed** | 2.1059 |
2.0391 | 1.033x | 2.0378 | 2.0044 | 1.016x |
| **dgrad down (N=6144, K=2048), E=4, M=112576, one-empty** | 2.1065 |
2.0395 | 1.033x | 2.0371 | 1.9948 | 1.021x |
| **dgrad down (N=6144, K=2048), E=4, M=136064, balanced** | 2.5472 |
2.4537 | 1.038x | 2.4500 | 2.4556 | 0.998x |
| **dgrad down (N=6144, K=2048), E=4, M=136064, skewed** | 2.5477 |
2.4571 | 1.037x | 2.4513 | 2.4548 | 0.998x |
| **dgrad down (N=6144, K=2048), E=4, M=136064, one-empty** | 2.5465 |
2.4538 | 1.038x | 2.4501 | 2.4555 | 0.998x |
| wgrad down (N=6144, K=2048), E=4, M=112576, balanced | 2.0822 | 2.0845
| 0.999x | 2.1095 | 2.1483 | 0.999x |
| wgrad down (N=6144, K=2048), E=4, M=112576, skewed | 2.1177 | 2.1169 |
1.000x | 2.1241 | 2.1241 | 1.000x |
| wgrad down (N=6144, K=2048), E=4, M=112576, one-empty | 2.0774 |
2.0778 | 1.000x | 2.1589 | 2.1588 | 1.000x |
| wgrad down (N=6144, K=2048), E=4, M=136064, balanced | 2.5224 | 2.5237
| 1.000x | 2.5973 | 2.6000 | 0.998x |
| wgrad down (N=6144, K=2048), E=4, M=136064, skewed | 2.5581 | 2.5588 |
1.000x | 2.6354 | 2.6360 | 1.000x |
| wgrad down (N=6144, K=2048), E=4, M=136064, one-empty | 2.5224 |
2.5223 | 1.000x | 2.5996 | 2.5994 | 1.001x |
| wgrad gate_up (N=4096, K=6144), E=4, M=112576, balanced, FP32 dW |
4.2349 | 4.2349 | 1.000x | 4.2775 | 4.2824 | 1.001x |
| wgrad gate_up (N=4096, K=6144), E=4, M=136064, balanced, FP32 dW |
5.1389 | 5.0893 | 1.002x | 5.2276 | 5.2271 | 1.000x |
| wgrad down (N=6144, K=2048), E=4, M=112576, balanced, FP32 dW | 2.1239
| 2.1233 | 1.000x | 2.1299 | 2.1300 | 1.000x |
| wgrad down (N=6144, K=2048), E=4, M=136064, balanced, FP32 dW | 2.5624
| 2.5627 | 1.000x | 2.6353 | 2.6354 | 1.000x |
| fwd gate_up (N=4096, K=6144), E=8, M=131072, balanced | 4.8719 |
4.8871 | 1.000x | 4.6687 | 4.6707 | 1.000x |
| dgrad gate_up (N=4096, K=6144), E=8, M=131072, balanced | 4.7917 |
4.7441 | 1.001x | 4.6191 | 4.6200 | 1.000x |
| wgrad gate_up (N=4096, K=6144), E=8, M=131072, balanced | 4.7910 |
4.8044 | 1.000x | 4.7146 | 4.7059 | 1.000x |
| fwd down (N=6144, K=2048), E=8, M=131072, balanced | 2.3975 | 2.3973 |
1.000x | 2.3205 | 2.3489 | 0.994x |
| **dgrad down (N=6144, K=2048), E=8, M=131072, balanced** | 2.4548 |
2.4006 | 1.022x | 2.3677 | 2.3731 | 1.008x |
| wgrad down (N=6144, K=2048), E=8, M=131072, balanced | 2.4530 | 2.4537
| 1.000x | 2.5263 | 2.5265 | 1.000x |
| fwd gate_up (N=4096, K=6144), E=16, M=131072, balanced | 4.8931 |
4.8927 | 1.000x | 4.7266 | 4.7252 | 0.997x |
| dgrad gate_up (N=4096, K=6144), E=16, M=131072, balanced | 4.8524 |
4.8537 | 1.000x | 4.6292 | 4.6311 | 1.000x |
| wgrad gate_up (N=4096, K=6144), E=16, M=131072, balanced | 4.8426 |
4.8332 | 1.000x | 4.7100 | 4.7101 | 1.000x |
| fwd down (N=6144, K=2048), E=16, M=131072, balanced | 2.4020 | 2.4021
| 1.000x | 2.3554 | 2.3541 | 1.000x |
| **dgrad down (N=6144, K=2048), E=16, M=131072, balanced** | 2.4589 |
2.4193 | 1.016x | 2.4103 | 2.3750 | 1.008x |
| wgrad down (N=6144, K=2048), E=16, M=131072, balanced | 2.4397 |
2.4397 | 1.000x | 2.5143 | 2.5152 | 1.000x |
| fwd gate_up (N=4096, K=6144), E=32, M=131072, balanced | 4.9087 |
4.9387 | 0.994x | 4.8029 | 4.8031 | 1.000x |
| dgrad gate_up (N=4096, K=6144), E=32, M=131072, balanced | 4.9328 |
4.9115 | 1.004x | 4.7053 | 4.6825 | 1.000x |
| wgrad gate_up (N=4096, K=6144), E=32, M=131072, balanced | 4.8553 |
4.8713 | 0.999x | 4.7175 | 4.7287 | 0.998x |
| fwd down (N=6144, K=2048), E=32, M=131072, balanced | 2.4380 | 2.4378
| 1.000x | 2.3803 | 2.3906 | 1.000x |
| **dgrad down (N=6144, K=2048), E=32, M=131072, balanced** | 2.5134 |
2.4219 | 1.031x | 2.3835 | 2.4210 | 0.994x |
| wgrad down (N=6144, K=2048), E=32, M=131072, balanced | 2.4533 |
2.4533 | 1.000x | 2.4527 | 2.4514 | 1.000x |

Cake ships all four variants of this kernel for sm_100a, sm_103a and
sm_107a, and this PR changes only the sm_100a data-gradient
down-projection routing (sm_103a already takes the probed split).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* Updated data-gradient launch scheduling for supported GPU
architectures, applying the probed queue split across all
down-projection rows on GB300- and B200-class systems.
* **Documentation**
  * Updated unequal SM-pair examples for GB300 and B200.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [9377d72](https://github.com/flashinfer-ai/flashinfer/commit/9377d725268b0ee63250fef0504568303400c4f3)

- **作者**: eigen
- **时间**: 2026-10-30T10:33:47Z
- **提交信息**: perf(cake_sampling): lean-scan twin of the (4, 16) resident for V = 32768, top-k 769-1024 on GB300 and B200 (#7989)

`cake_sampling` is FlashInfer's Cake top-k/top-p sampling from float32
probability rows (`top_k_top_p_sampling_from_probs` with a Philox
seed/offset). It has one data type, one layout and one fused form.
Inside that variant, stage 1 (radix top-k select) has 136 builds in
resident and streaming forms, with clusters of 1, 2, 4 or 8 CTAs and 4
to 48 entries per thread. Stages 2/3 (top-p renormalize and sample) have
15 kernels. This PR adds one stage-1 build, a lean-scan twin of the (4,
16) resident (cluster 4, 16 entries per thread). GB300 and B200 run it
at vocab 32768 with batch 1, 2, 4, 8 or 16 and top-k 769-1024. In the
192-shape list below, this changes 10 shapes per GPU: top-k 1000, vocab
32768, batch 1-16, eager and graph. The baseline is the previous shipped
version, `cake_sampling` on FlashInfer main (#7830). Against it, the
changed shapes run 1.022x-1.024x on B200 and 1.022x-1.023x in graph mode
on GB300. GB300 eager measured 0.971x-0.998x.

Latency is in µs per sampling call, the median of each side over 12
rounds. Speedup = baseline / this PR, the median of the 12 paired
per-round ratios, so it can differ from the quotient of the two latency
columns.

| GPU | rows whose launch changes | speedup on those rows: eager |
speedup on those rows: graph | other rows |
|---|---:|---:|---:|---:|
| GB300 | 10 | 0.971x-0.998x | 1.022x-1.023x | 0.987x-1.001x (182 rows)
|
| B200 | 10 | 1.022x-1.024x | 1.022x-1.024x | 0.998x-1.004x (182 rows) |

**NVIDIA GB300 (sm_103a, 152 SMs), CUDA 13.4: the 10 shapes whose launch
changes**

| top-k | vocab | batch | mode | baseline µs | this PR µs | speedup |
|---:|---:|---:|---|---:|---:|---:|
| 1000 | 32768 | 1 | eager | 14.584 | 15.312 | 0.978x |
| 1000 | 32768 | 1 | graph | 14.016 | 13.664 | 1.023x |
| 1000 | 32768 | 2 | eager | 15.616 | 15.792 | 0.980x |
| 1000 | 32768 | 2 | graph | 14.080 | 13.808 | 1.023x |
| 1000 | 32768 | 4 | eager | 15.504 | 16.560 | 0.971x |
| 1000 | 32768 | 4 | graph | 14.192 | 13.888 | 1.023x |
| 1000 | 32768 | 8 | eager | 15.792 | 15.888 | 0.998x |
| 1000 | 32768 | 8 | graph | 14.352 | 13.968 | 1.023x |
| 1000 | 32768 | 16 | eager | 16.480 | 16.912 | 0.986x |
| 1000 | 32768 | 16 | graph | 14.704 | 14.384 | 1.022x |

<details>
<summary>NVIDIA GB300 (sm_103a), CUDA 13.4: all 192 shapes</summary>

| top-k | vocab | batch | mode | baseline µs | this PR µs | speedup |
|---:|---:|---:|---|---:|---:|---:|
| 10 | 32768 | 1 | eager | 6.784 | 6.784 | 1.000x |
| 10 | 32768 | 1 | graph | 7.136 | 7.136 | 1.000x |
| 10 | 32768 | 2 | eager | 6.976 | 6.976 | 1.000x |
| 10 | 32768 | 2 | graph | 7.328 | 7.328 | 1.000x |
| 10 | 32768 | 4 | eager | 7.008 | 7.024 | 1.000x |
| 10 | 32768 | 4 | graph | 7.360 | 7.360 | 1.000x |
| 10 | 32768 | 8 | eager | 7.264 | 7.264 | 0.998x |
| 10 | 32768 | 8 | graph | 7.520 | 7.520 | 1.000x |
| 10 | 32768 | 16 | eager | 7.488 | 7.488 | 1.000x |
| 10 | 32768 | 16 | graph | 7.744 | 7.760 | 1.000x |
| 10 | 32768 | 32 | eager | 8.064 | 8.064 | 1.000x |
| 10 | 32768 | 32 | graph | 8.352 | 8.352 | 1.000x |
| 10 | 32768 | 64 | eager | 9.632 | 9.632 | 1.000x |
| 10 | 32768 | 64 | graph | 9.856 | 9.856 | 1.000x |
| 10 | 32768 | 128 | eager | 10.624 | 10.624 | 1.000x |
| 10 | 32768 | 128 | graph | 10.880 | 10.880 | 1.000x |
| 10 | 128256 | 1 | eager | 7.776 | 7.760 | 1.000x |
| 10 | 128256 | 1 | graph | 8.096 | 8.080 | 1.000x |
| 10 | 128256 | 2 | eager | 7.904 | 7.904 | 1.000x |
| 10 | 128256 | 2 | graph | 8.256 | 8.256 | 1.000x |
| 10 | 128256 | 4 | eager | 8.096 | 8.096 | 1.000x |
| 10 | 128256 | 4 | graph | 8.448 | 8.448 | 1.000x |
| 10 | 128256 | 8 | eager | 8.576 | 8.576 | 1.000x |
| 10 | 128256 | 8 | graph | 8.864 | 8.848 | 1.000x |
| 10 | 128256 | 16 | eager | 10.368 | 10.368 | 1.000x |
| 10 | 128256 | 16 | graph | 10.640 | 10.656 | 1.000x |
| 10 | 128256 | 32 | eager | 11.568 | 11.584 | 1.000x |
| 10 | 128256 | 32 | graph | 11.904 | 11.872 | 1.000x |
| 10 | 128256 | 64 | eager | 14.688 | 14.688 | 1.000x |
| 10 | 128256 | 64 | graph | 14.976 | 14.976 | 1.000x |
| 10 | 128256 | 128 | eager | 20.736 | 20.736 | 1.000x |
| 10 | 128256 | 128 | graph | 20.960 | 20.960 | 1.000x |
| 10 | 151936 | 1 | eager | 8.640 | 8.672 | 0.998x |
| 10 | 151936 | 1 | graph | 9.040 | 9.040 | 1.000x |
| 10 | 151936 | 2 | eager | 8.736 | 8.736 | 1.000x |
| 10 | 151936 | 2 | graph | 9.120 | 9.120 | 1.000x |
| 10 | 151936 | 4 | eager | 9.024 | 9.024 | 1.000x |
| 10 | 151936 | 4 | graph | 9.408 | 9.376 | 1.000x |
| 10 | 151936 | 8 | eager | 9.536 | 9.536 | 1.000x |
| 10 | 151936 | 8 | graph | 9.824 | 9.824 | 1.000x |
| 10 | 151936 | 16 | eager | 11.056 | 11.056 | 1.000x |
| 10 | 151936 | 16 | graph | 11.328 | 11.328 | 1.000x |
| 10 | 151936 | 32 | eager | 12.128 | 12.128 | 1.000x |
| 10 | 151936 | 32 | graph | 12.448 | 12.431 | 1.000x |
| 10 | 151936 | 64 | eager | 16.096 | 16.096 | 1.000x |
| 10 | 151936 | 64 | graph | 16.368 | 16.384 | 0.998x |
| 10 | 151936 | 128 | eager | 24.296 | 24.320 | 1.000x |
| 10 | 151936 | 128 | graph | 24.512 | 24.512 | 1.000x |
| 10 | 262144 | 1 | eager | 9.216 | 9.216 | 0.998x |
| 10 | 262144 | 1 | graph | 9.568 | 9.568 | 1.000x |
| 10 | 262144 | 2 | eager | 9.376 | 9.376 | 1.000x |
| 10 | 262144 | 2 | graph | 9.712 | 9.712 | 1.000x |
| 10 | 262144 | 4 | eager | 9.696 | 9.696 | 1.000x |
| 10 | 262144 | 4 | graph | 10.048 | 10.048 | 1.000x |
| 10 | 262144 | 8 | eager | 10.464 | 10.464 | 1.000x |
| 10 | 262144 | 8 | graph | 10.720 | 10.720 | 1.000x |
| 10 | 262144 | 16 | eager | 12.800 | 12.800 | 1.000x |
| 10 | 262144 | 16 | graph | 13.024 | 13.008 | 1.000x |
| 10 | 262144 | 32 | eager | 14.816 | 14.800 | 1.000x |
| 10 | 262144 | 32 | graph | 15.072 | 15.072 | 1.000x |
| 10 | 262144 | 64 | eager | 23.712 | 23.712 | 0.999x |
| 10 | 262144 | 64 | graph | 23.968 | 23.968 | 1.000x |
| 10 | 262144 | 128 | eager | 35.456 | 35.440 | 1.001x |
| 10 | 262144 | 128 | graph | 35.744 | 35.744 | 1.000x |
| 50 | 32768 | 1 | eager | 7.392 | 7.392 | 1.000x |
| 50 | 32768 | 1 | graph | 7.744 | 7.744 | 1.000x |
| 50 | 32768 | 2 | eager | 7.552 | 7.552 | 1.000x |
| 50 | 32768 | 2 | graph | 7.904 | 7.904 | 1.000x |
| 50 | 32768 | 4 | eager | 7.616 | 7.616 | 1.000x |
| 50 | 32768 | 4 | graph | 7.968 | 7.952 | 1.000x |
| 50 | 32768 | 8 | eager | 7.936 | 7.936 | 1.000x |
| 50 | 32768 | 8 | graph | 8.160 | 8.160 | 1.000x |
| 50 | 32768 | 16 | eager | 8.160 | 8.160 | 1.000x |
| 50 | 32768 | 16 | graph | 8.416 | 8.416 | 1.000x |
| 50 | 32768 | 32 | eager | 8.704 | 8.704 | 1.000x |
| 50 | 32768 | 32 | graph | 8.960 | 8.960 | 1.000x |
| 50 | 32768 | 64 | eager | 10.176 | 10.176 | 1.000x |
| 50 | 32768 | 64 | graph | 10.336 | 10.336 | 1.000x |
| 50 | 32768 | 128 | eager | 11.232 | 11.232 | 1.000x |
| 50 | 32768 | 128 | graph | 11.456 | 11.456 | 1.000x |
| 50 | 128256 | 1 | eager | 9.056 | 9.088 | 1.000x |
| 50 | 128256 | 1 | graph | 9.376 | 9.376 | 1.000x |
| 50 | 128256 | 2 | eager | 9.312 | 9.312 | 1.000x |
| 50 | 128256 | 2 | graph | 9.664 | 9.664 | 1.000x |
| 50 | 128256 | 4 | eager | 9.472 | 9.472 | 1.000x |
| 50 | 128256 | 4 | graph | 9.824 | 9.824 | 1.000x |
| 50 | 128256 | 8 | eager | 10.016 | 10.016 | 1.000x |
| 50 | 128256 | 8 | graph | 10.272 | 10.272 | 1.000x |
| 50 | 128256 | 16 | eager | 11.712 | 11.712 | 1.000x |
| 50 | 128256 | 16 | graph | 12.000 | 12.000 | 1.000x |
| 50 | 128256 | 32 | eager | 13.024 | 13.024 | 1.000x |
| 50 | 128256 | 32 | graph | 13.344 | 13.344 | 1.000x |
| 50 | 128256 | 64 | eager | 15.744 | 15.744 | 1.000x |
| 50 | 128256 | 64 | graph | 16.032 | 16.032 | 1.000x |
| 50 | 128256 | 128 | eager | 21.536 | 21.536 | 1.000x |
| 50 | 128256 | 128 | graph | 21.792 | 21.792 | 1.000x |
| 50 | 151936 | 1 | eager | 9.920 | 9.952 | 1.000x |
| 50 | 151936 | 1 | graph | 10.240 | 10.240 | 1.000x |
| 50 | 151936 | 2 | eager | 10.016 | 10.016 | 1.000x |
| 50 | 151936 | 2 | graph | 10.368 | 10.368 | 1.000x |
| 50 | 151936 | 4 | eager | 10.336 | 10.336 | 1.000x |
| 50 | 151936 | 4 | graph | 10.688 | 10.704 | 1.000x |
| 50 | 151936 | 8 | eager | 10.912 | 10.912 | 1.000x |
| 50 | 151936 | 8 | graph | 11.168 | 11.168 | 1.000x |
| 50 | 151936 | 16 | eager | 12.448 | 12.447 | 1.000x |
| 50 | 151936 | 16 | graph | 12.704 | 12.704 | 1.000x |
| 50 | 151936 | 32 | eager | 13.504 | 13.504 | 1.000x |
| 50 | 151936 | 32 | graph | 13.792 | 13.808 | 1.000x |
| 50 | 151936 | 64 | eager | 17.248 | 17.248 | 1.000x |
| 50 | 151936 | 64 | graph | 17.536 | 17.536 | 1.000x |
| 50 | 151936 | 128 | eager | 24.896 | 24.928 | 1.000x |
| 50 | 151936 | 128 | graph | 25.120 | 25.120 | 1.000x |
| 50 | 262144 | 1 | eager | 10.400 | 10.400 | 0.999x |
| 50 | 262144 | 1 | graph | 10.720 | 10.720 | 1.000x |
| 50 | 262144 | 2 | eager | 10.688 | 10.688 | 1.000x |
| 50 | 262144 | 2 | graph | 11.040 | 11.040 | 1.000x |
| 50 | 262144 | 4 | eager | 10.976 | 10.976 | 1.000x |
| 50 | 262144 | 4 | graph | 11.328 | 11.296 | 1.000x |
| 50 | 262144 | 8 | eager | 11.808 | 11.808 | 1.000x |
| 50 | 262144 | 8 | graph | 12.064 | 12.064 | 1.000x |
| 50 | 262144 | 16 | eager | 13.888 | 13.888 | 1.000x |
| 50 | 262144 | 16 | graph | 14.160 | 14.176 | 1.000x |
| 50 | 262144 | 32 | eager | 16.064 | 16.064 | 1.000x |
| 50 | 262144 | 32 | graph | 16.336 | 16.352 | 1.000x |
| 50 | 262144 | 64 | eager | 24.064 | 24.064 | 1.000x |
| 50 | 262144 | 64 | graph | 24.352 | 24.352 | 1.000x |
| 50 | 262144 | 128 | eager | 35.808 | 35.840 | 1.000x |
| 50 | 262144 | 128 | graph | 36.128 | 36.128 | 1.000x |
| 1000 | 32768 | 1 | eager | 14.584 | 15.312 | 0.978x |
| 1000 | 32768 | 1 | graph | 14.016 | 13.664 | 1.023x |
| 1000 | 32768 | 2 | eager | 15.616 | 15.792 | 0.980x |
| 1000 | 32768 | 2 | graph | 14.080 | 13.808 | 1.023x |
| 1000 | 32768 | 4 | eager | 15.504 | 16.560 | 0.971x |
| 1000 | 32768 | 4 | graph | 14.192 | 13.888 | 1.023x |
| 1000 | 32768 | 8 | eager | 15.792 | 15.888 | 0.998x |
| 1000 | 32768 | 8 | graph | 14.352 | 13.968 | 1.023x |
| 1000 | 32768 | 16 | eager | 16.480 | 16.912 | 0.986x |
| 1000 | 32768 | 16 | graph | 14.704 | 14.384 | 1.022x |
| 1000 | 32768 | 32 | eager | 15.728 | 16.128 | 0.987x |
| 1000 | 32768 | 32 | graph | 15.552 | 15.552 | 1.000x |
| 1000 | 32768 | 64 | eager | 16.256 | 16.240 | 1.000x |
| 1000 | 32768 | 64 | graph | 16.448 | 16.480 | 1.000x |
| 1000 | 32768 | 128 | eager | 17.632 | 17.840 | 0.999x |
| 1000 | 32768 | 128 | graph | 18.016 | 18.000 | 1.000x |
| 1000 | 128256 | 1 | eager | 14.816 | 14.784 | 1.000x |
| 1000 | 128256 | 1 | graph | 15.104 | 15.200 | 1.000x |
| 1000 | 128256 | 2 | eager | 15.008 | 14.992 | 1.000x |
| 1000 | 128256 | 2 | graph | 15.360 | 15.360 | 1.000x |
| 1000 | 128256 | 4 | eager | 15.040 | 15.040 | 1.000x |
| 1000 | 128256 | 4 | graph | 15.392 | 15.392 | 1.000x |
| 1000 | 128256 | 8 | eager | 15.712 | 15.744 | 1.000x |
| 1000 | 128256 | 8 | graph | 16.000 | 16.000 | 1.000x |
| 1000 | 128256 | 16 | eager | 18.832 | 18.816 | 1.000x |
| 1000 | 128256 | 16 | graph | 19.072 | 19.040 | 1.000x |
| 1000 | 128256 | 32 | eager | 20.112 | 20.080 | 1.000x |
| 1000 | 128256 | 32 | graph | 20.560 | 20.608 | 1.000x |
| 1000 | 128256 | 64 | eager | 22.960 | 22.864 | 1.000x |
| 1000 | 128256 | 64 | graph | 23.312 | 23.328 | 1.000x |
| 1000 | 128256 | 128 | eager | 32.360 | 32.384 | 1.000x |
| 1000 | 128256 | 128 | graph | 32.784 | 32.776 | 1.000x |
| 1000 | 151936 | 1 | eager | 16.112 | 16.128 | 1.000x |
| 1000 | 151936 | 1 | graph | 16.432 | 16.448 | 1.000x |
| 1000 | 151936 | 2 | eager | 16.544 | 16.544 | 1.000x |
| 1000 | 151936 | 2 | graph | 16.896 | 16.896 | 1.000x |
| 1000 | 151936 | 4 | eager | 16.768 | 16.768 | 1.000x |
| 1000 | 151936 | 4 | graph | 17.152 | 17.152 | 1.000x |
| 1000 | 151936 | 8 | eager | 17.392 | 17.568 | 1.000x |
| 1000 | 151936 | 8 | graph | 17.664 | 17.664 | 1.000x |
| 1000 | 151936 | 16 | eager | 19.760 | 19.776 | 1.000x |
| 1000 | 151936 | 16 | graph | 20.080 | 20.016 | 1.000x |
| 1000 | 151936 | 32 | eager | 20.688 | 20.656 | 1.000x |
| 1000 | 151936 | 32 | graph | 21.152 | 21.184 | 1.000x |
| 1000 | 151936 | 64 | eager | 24.992 | 25.040 | 1.000x |
| 1000 | 151936 | 64 | graph | 25.600 | 25.600 | 1.000x |
| 1000 | 151936 | 128 | eager | 32.000 | 32.000 | 1.000x |
| 1000 | 151936 | 128 | graph | 32.192 | 32.224 | 1.000x |
| 1000 | 262144 | 1 | eager | 16.672 | 16.624 | 1.000x |
| 1000 | 262144 | 1 | graph | 16.960 | 16.960 | 1.000x |
| 1000 | 262144 | 2 | eager | 16.704 | 16.704 | 1.000x |
| 1000 | 262144 | 2 | graph | 17.056 | 17.056 | 1.000x |
| 1000 | 262144 | 4 | eager | 17.568 | 17.568 | 1.000x |
| 1000 | 262144 | 4 | graph | 17.952 | 17.952 | 1.000x |
| 1000 | 262144 | 8 | eager | 18.240 | 18.272 | 0.997x |
| 1000 | 262144 | 8 | graph | 18.496 | 18.496 | 1.000x |
| 1000 | 262144 | 16 | eager | 22.336 | 22.320 | 1.000x |
| 1000 | 262144 | 16 | graph | 22.576 | 22.544 | 1.000x |
| 1000 | 262144 | 32 | eager | 23.488 | 23.520 | 1.000x |
| 1000 | 262144 | 32 | graph | 24.064 | 24.080 | 1.000x |
| 1000 | 262144 | 64 | eager | 31.184 | 30.960 | 1.001x |
| 1000 | 262144 | 64 | graph | 31.728 | 31.712 | 1.000x |
| 1000 | 262144 | 128 | eager | 46.608 | 46.480 | 1.000x |
| 1000 | 262144 | 128 | graph | 46.928 | 46.944 | 0.997x |

</details>

**NVIDIA B200 (sm_100a, 148 SMs), CUDA 13.4: the 10 shapes whose launch
changes**

| top-k | vocab | batch | mode | baseline µs | this PR µs | speedup |
|---:|---:|---:|---|---:|---:|---:|
| 1000 | 32768 | 1 | eager | 13.888 | 13.553 | 1.024x |
| 1000 | 32768 | 1 | graph | 14.415 | 14.096 | 1.023x |
| 1000 | 32768 | 2 | eager | 14.127 | 13.792 | 1.023x |
| 1000 | 32768 | 2 | graph | 14.512 | 14.159 | 1.023x |
| 1000 | 32768 | 4 | eager | 14.272 | 13.952 | 1.023x |
| 1000 | 32768 | 4 | graph | 14.639 | 14.288 | 1.024x |
| 1000 | 32768 | 8 | eager | 14.368 | 14.113 | 1.022x |
| 1000 | 32768 | 8 | graph | 14.688 | 14.336 | 1.024x |
| 1000 | 32768 | 16 | eager | 14.784 | 14.464 | 1.022x |
| 1000 | 32768 | 16 | graph | 15.104 | 14.784 | 1.022x |

<details>
<summary>NVIDIA B200 (sm_100a), CUDA 13.4: all 192 shapes</summary>

| top-k | vocab | batch | mode | baseline µs | this PR µs | speedup |
|---:|---:|---:|---|---:|---:|---:|
| 10 | 32768 | 1 | eager | 6.848 | 6.848 | 1.000x |
| 10 | 32768 | 1 | graph | 7.200 | 7.200 | 1.000x |
| 10 | 32768 | 2 | eager | 7.040 | 7.040 | 1.000x |
| 10 | 32768 | 2 | graph | 7.424 | 7.425 | 1.000x |
| 10 | 32768 | 4 | eager | 7.200 | 7.200 | 1.000x |
| 10 | 32768 | 4 | graph | 7.520 | 7.520 | 1.000x |
| 10 | 32768 | 8 | eager | 7.360 | 7.360 | 1.002x |
| 10 | 32768 | 8 | graph | 7.617 | 7.616 | 1.000x |
| 10 | 32768 | 16 | eager | 7.616 | 7.600 | 1.000x |
| 10 | 32768 | 16 | graph | 7.872 | 7.872 | 1.000x |
| 10 | 32768 | 32 | eager | 8.128 | 8.128 | 1.000x |
| 10 | 32768 | 32 | graph | 8.416 | 8.416 | 1.000x |
| 10 | 32768 | 64 | eager | 9.280 | 9.280 | 1.000x |
| 10 | 32768 | 64 | graph | 9.536 | 9.536 | 1.000x |
| 10 | 32768 | 128 | eager | 10.848 | 10.880 | 1.000x |
| 10 | 32768 | 128 | graph | 11.088 | 11.088 | 1.000x |
| 10 | 128256 | 1 | eager | 7.871 | 7.872 | 1.000x |
| 10 | 128256 | 1 | graph | 8.193 | 8.193 | 1.000x |
| 10 | 128256 | 2 | eager | 8.032 | 8.032 | 1.002x |
| 10 | 128256 | 2 | graph | 8.399 | 8.416 | 1.000x |
| 10 | 128256 | 4 | eager | 8.304 | 8.288 | 1.000x |
| 10 | 128256 | 4 | graph | 8.655 | 8.640 | 1.000x |
| 10 | 128256 | 8 | eager | 8.736 | 8.736 | 1.000x |
| 10 | 128256 | 8 | graph | 8.992 | 8.992 | 1.000x |
| 10 | 128256 | 16 | eager | 10.368 | 10.368 | 1.000x |
| 10 | 128256 | 16 | graph | 10.624 | 10.624 | 1.000x |
| 10 | 128256 | 32 | eager | 11.552 | 11.553 | 1.000x |
| 10 | 128256 | 32 | graph | 11.840 | 11.840 | 1.000x |
| 10 | 128256 | 64 | eager | 14.640 | 14.624 | 1.000x |
| 10 | 128256 | 64 | graph | 14.896 | 14.928 | 1.000x |
| 10 | 128256 | 128 | eager | 21.216 | 21.216 | 1.000x |
| 10 | 128256 | 128 | graph | 21.520 | 21.536 | 1.000x |
| 10 | 151936 | 1 | eager | 8.736 | 8.736 | 1.000x |
| 10 | 151936 | 1 | graph | 9.120 | 9.120 | 1.000x |
| 10 | 151936 | 2 | eager | 8.864 | 8.849 | 1.000x |
| 10 | 151936 | 2 | graph | 9.247 | 9.248 | 1.000x |
| 10 | 151936 | 4 | eager | 9.152 | 9.160 | 1.000x |
| 10 | 151936 | 4 | graph | 9.440 | 9.440 | 1.000x |
| 10 | 151936 | 8 | eager | 9.615 | 9.600 | 1.000x |
| 10 | 151936 | 8 | graph | 9.857 | 9.856 | 1.000x |
| 10 | 151936 | 16 | eager | 11.104 | 11.104 | 1.000x |
| 10 | 151936 | 16 | graph | 11.360 | 11.345 | 1.000x |
| 10 | 151936 | 32 | eager | 12.320 | 12.320 | 1.000x |
| 10 | 151936 | 32 | graph | 12.608 | 12.608 | 1.000x |
| 10 | 151936 | 64 | eager | 16.288 | 16.288 | 1.000x |
| 10 | 151936 | 64 | graph | 16.608 | 16.623 | 1.000x |
| 10 | 151936 | 128 | eager | 24.032 | 24.032 | 1.001x |
| 10 | 151936 | 128 | graph | 24.320 | 24.320 | 1.000x |
| 10 | 262144 | 1 | eager | 9.376 | 9.376 | 1.000x |
| 10 | 262144 | 1 | graph | 9.728 | 9.744 | 1.000x |
| 10 | 262144 | 2 | eager | 9.600 | 9.600 | 1.000x |
| 10 | 262144 | 2 | graph | 9.984 | 10.000 | 1.000x |
| 10 | 262144 | 4 | eager | 9.952 | 9.952 | 1.000x |
| 10 | 262144 | 4 | graph | 10.240 | 10.256 | 1.000x |
| 10 | 262144 | 8 | eager | 10.576 | 10.544 | 1.000x |
| 10 | 262144 | 8 | graph | 10.848 | 10.848 | 1.000x |
| 10 | 262144 | 16 | eager | 13.088 | 13.120 | 1.000x |
| 10 | 262144 | 16 | graph | 13.376 | 13.376 | 1.000x |
| 10 | 262144 | 32 | eager | 15.456 | 15.456 | 1.000x |
| 10 | 262144 | 32 | graph | 15.776 | 15.793 | 1.000x |
| 10 | 262144 | 64 | eager | 21.888 | 21.872 | 1.000x |
| 10 | 262144 | 64 | graph | 22.176 | 22.176 | 1.000x |
| 10 | 262144 | 128 | eager | 37.359 | 37.360 | 1.000x |
| 10 | 262144 | 128 | graph | 37.680 | 37.672 | 1.000x |
| 50 | 32768 | 1 | eager | 7.520 | 7.520 | 1.000x |
| 50 | 32768 | 1 | graph | 7.904 | 7.905 | 0.998x |
| 50 | 32768 | 2 | eager | 7.680 | 7.680 | 1.000x |
| 50 | 32768 | 2 | graph | 8.056 | 8.064 | 1.000x |
| 50 | 32768 | 4 | eager | 7.840 | 7.840 | 1.000x |
| 50 | 32768 | 4 | graph | 8.144 | 8.160 | 1.000x |
| 50 | 32768 | 8 | eager | 8.096 | 8.096 | 1.000x |
| 50 | 32768 | 8 | graph | 8.320 | 8.320 | 1.000x |
| 50 | 32768 | 16 | eager | 8.320 | 8.320 | 1.000x |
| 50 | 32768 | 16 | graph | 8.576 | 8.568 | 1.000x |
| 50 | 32768 | 32 | eager | 8.896 | 8.896 | 1.000x |
| 50 | 32768 | 32 | graph | 9.152 | 9.152 | 1.000x |
| 50 | 32768 | 64 | eager | 10.240 | 10.240 | 1.000x |
| 50 | 32768 | 64 | graph | 10.448 | 10.432 | 1.000x |
| 50 | 32768 | 128 | eager | 11.456 | 11.456 | 1.000x |
| 50 | 32768 | 128 | graph | 11.679 | 11.680 | 1.000x |
| 50 | 128256 | 1 | eager | 9.248 | 9.232 | 1.000x |
| 50 | 128256 | 1 | graph | 9.552 | 9.559 | 1.000x |
| 50 | 128256 | 2 | eager | 9.504 | 9.504 | 1.000x |
| 50 | 128256 | 2 | graph | 9.888 | 9.888 | 1.000x |
| 50 | 128256 | 4 | eager | 9.760 | 9.791 | 1.000x |
| 50 | 128256 | 4 | graph | 10.048 | 10.063 | 0.999x |
| 50 | 128256 | 8 | eager | 10.207 | 10.208 | 1.000x |
| 50 | 128256 | 8 | graph | 10.448 | 10.464 | 1.000x |
| 50 | 128256 | 16 | eager | 11.569 | 11.584 | 1.000x |
| 50 | 128256 | 16 | graph | 11.840 | 11.840 | 1.000x |
| 50 | 128256 | 32 | eager | 12.960 | 12.960 | 1.000x |
| 50 | 128256 | 32 | graph | 13.248 | 13.248 | 1.000x |
| 50 | 128256 | 64 | eager | 15.744 | 15.744 | 1.000x |
| 50 | 128256 | 64 | graph | 16.032 | 16.064 | 1.000x |
| 50 | 128256 | 128 | eager | 22.032 | 22.016 | 1.000x |
| 50 | 128256 | 128 | graph | 22.304 | 22.320 | 1.000x |
| 50 | 151936 | 1 | eager | 10.080 | 10.080 | 1.000x |
| 50 | 151936 | 1 | graph | 10.416 | 10.400 | 1.000x |
| 50 | 151936 | 2 | eager | 10.240 | 10.240 | 1.000x |
| 50 | 151936 | 2 | graph | 10.576 | 10.591 | 1.000x |
| 50 | 151936 | 4 | eager | 10.608 | 10.592 | 1.000x |
| 50 | 151936 | 4 | graph | 10.848 | 10.848 | 1.000x |
| 50 | 151936 | 8 | eager | 11.040 | 11.040 | 1.000x |
| 50 | 151936 | 8 | graph | 11.327 | 11.296 | 1.000x |
| 50 | 151936 | 16 | eager | 12.272 | 12.272 | 1.000x |
| 50 | 151936 | 16 | graph | 12.560 | 12.544 | 1.000x |
| 50 | 151936 | 32 | eager | 13.697 | 13.696 | 1.000x |
| 50 | 151936 | 32 | graph | 14.032 | 14.016 | 1.000x |
| 50 | 151936 | 64 | eager | 17.504 | 17.504 | 1.000x |
| 50 | 151936 | 64 | graph | 17.824 | 17.816 | 1.002x |
| 50 | 151936 | 128 | eager | 24.704 | 24.736 | 1.000x |
| 50 | 151936 | 128 | graph | 25.009 | 25.024 | 1.000x |
| 50 | 262144 | 1 | eager | 10.592 | 10.592 | 1.000x |
| 50 | 262144 | 1 | graph | 10.960 | 10.976 | 1.000x |
| 50 | 262144 | 2 | eager | 10.848 | 10.816 | 1.000x |
| 50 | 262144 | 2 | graph | 11.200 | 11.200 | 1.000x |
| 50 | 262144 | 4 | eager | 11.264 | 11.264 | 1.000x |
| 50 | 262144 | 4 | graph | 11.553 | 11.552 | 1.000x |
| 50 | 262144 | 8 | eager | 12.032 | 12.032 | 1.000x |
| 50 | 262144 | 8 | graph | 12.320 | 12.320 | 1.000x |
| 50 | 262144 | 16 | eager | 14.369 | 14.368 | 1.000x |
| 50 | 262144 | 16 | graph | 14.688 | 14.688 | 1.000x |
| 50 | 262144 | 32 | eager | 16.896 | 16.896 | 1.000x |
| 50 | 262144 | 32 | graph | 17.216 | 17.216 | 1.000x |
| 50 | 262144 | 64 | eager | 23.007 | 23.008 | 1.000x |
| 50 | 262144 | 64 | graph | 23.296 | 23.296 | 1.000x |
| 50 | 262144 | 128 | eager | 37.864 | 37.888 | 1.000x |
| 50 | 262144 | 128 | graph | 38.256 | 38.240 | 1.000x |
| 1000 | 32768 | 1 | eager | 13.888 | 13.553 | 1.024x |
| 1000 | 32768 | 1 | graph | 14.415 | 14.096 | 1.023x |
| 1000 | 32768 | 2 | eager | 14.127 | 13.792 | 1.023x |
| 1000 | 32768 | 2 | graph | 14.512 | 14.159 | 1.023x |
| 1000 | 32768 | 4 | eager | 14.272 | 13.952 | 1.023x |
| 1000 | 32768 | 4 | graph | 14.639 | 14.288 | 1.024x |
| 1000 | 32768 | 8 | eager | 14.368 | 14.113 | 1.022x |
| 1000 | 32768 | 8 | graph | 14.688 | 14.336 | 1.024x |
| 1000 | 32768 | 16 | eager | 14.784 | 14.464 | 1.022x |
| 1000 | 32768 | 16 | graph | 15.104 | 14.784 | 1.022x |
| 1000 | 32768 | 32 | eager | 15.456 | 15.456 | 1.000x |
| 1000 | 32768 | 32 | graph | 16.000 | 16.000 | 1.000x |
| 1000 | 32768 | 64 | eager | 17.088 | 17.040 | 1.000x |
| 1000 | 32768 | 64 | graph | 17.504 | 17.440 | 0.999x |
| 1000 | 32768 | 128 | eager | 18.576 | 18.576 | 1.000x |
| 1000 | 32768 | 128 | graph | 18.752 | 18.752 | 1.000x |
| 1000 | 128256 | 1 | eager | 14.704 | 14.720 | 1.000x |
| 1000 | 128256 | 1 | graph | 15.072 | 15.073 | 1.000x |
| 1000 | 128256 | 2 | eager | 14.912 | 14.912 | 1.001x |
| 1000 | 128256 | 2 | graph | 15.296 | 15.280 | 1.000x |
| 1000 | 128256 | 4 | eager | 15.264 | 15.248 | 1.000x |
| 1000 | 128256 | 4 | graph | 15.584 | 15.584 | 1.000x |
| 1000 | 128256 | 8 | eager | 15.632 | 15.633 | 1.000x |
| 1000 | 128256 | 8 | graph | 15.920 | 15.904 | 1.000x |
| 1000 | 128256 | 16 | eager | 18.848 | 18.800 | 1.000x |
| 1000 | 128256 | 16 | graph | 19.072 | 19.056 | 1.001x |
| 1000 | 128256 | 32 | eager | 20.383 | 20.416 | 1.000x |
| 1000 | 128256 | 32 | graph | 20.672 | 20.656 | 1.000x |
| 1000 | 128256 | 64 | eager | 23.760 | 23.792 | 1.000x |
| 1000 | 128256 | 64 | graph | 24.016 | 23.999 | 1.001x |
| 1000 | 128256 | 128 | eager | 33.184 | 33.168 | 1.000x |
| 1000 | 128256 | 128 | graph | 33.488 | 33.472 | 1.001x |
| 1000 | 151936 | 1 | eager | 16.064 | 16.064 | 1.000x |
| 1000 | 151936 | 1 | graph | 16.432 | 16.431 | 1.000x |
| 1000 | 151936 | 2 | eager | 16.512 | 16.544 | 1.000x |
| 1000 | 151936 | 2 | graph | 16.912 | 16.928 | 1.000x |
| 1000 | 151936 | 4 | eager | 16.864 | 16.849 | 1.000x |
| 1000 | 151936 | 4 | graph | 17.184 | 17.184 | 1.000x |
| 1000 | 151936 | 8 | eager | 17.281 | 17.264 | 0.999x |
| 1000 | 151936 | 8 | graph | 17.584 | 17.584 | 1.000x |
| 1000 | 151936 | 16 | eager | 20.096 | 20.144 | 0.998x |
| 1000 | 151936 | 16 | graph | 20.464 | 20.416 | 0.999x |
| 1000 | 151936 | 32 | eager | 21.360 | 21.216 | 1.000x |
| 1000 | 151936 | 32 | graph | 21.872 | 21.887 | 1.000x |
| 1000 | 151936 | 64 | eager | 25.904 | 25.696 | 1.000x |
| 1000 | 151936 | 64 | graph | 26.319 | 26.336 | 1.000x |
| 1000 | 151936 | 128 | eager | 37.648 | 37.520 | 1.002x |
| 1000 | 151936 | 128 | graph | 38.048 | 37.856 | 1.004x |
| 1000 | 262144 | 1 | eager | 16.752 | 16.736 | 1.000x |
| 1000 | 262144 | 1 | graph | 17.120 | 17.104 | 1.001x |
| 1000 | 262144 | 2 | eager | 17.504 | 17.488 | 1.000x |
| 1000 | 262144 | 2 | graph | 17.889 | 17.889 | 1.000x |
| 1000 | 262144 | 4 | eager | 17.856 | 17.887 | 1.000x |
| 1000 | 262144 | 4 | graph | 18.112 | 18.112 | 1.000x |
| 1000 | 262144 | 8 | eager | 18.432 | 18.432 | 1.000x |
| 1000 | 262144 | 8 | graph | 18.656 | 18.656 | 1.000x |
| 1000 | 262144 | 16 | eager | 22.112 | 22.129 | 1.000x |
| 1000 | 262144 | 16 | graph | 22.416 | 22.432 | 1.000x |
| 1000 | 262144 | 32 | eager | 23.824 | 23.840 | 1.000x |
| 1000 | 262144 | 32 | graph | 24.416 | 24.433 | 1.000x |
| 1000 | 262144 | 64 | eager | 31.136 | 31.120 | 1.000x |
| 1000 | 262144 | 64 | graph | 31.840 | 31.808 | 1.000x |
| 1000 | 262144 | 128 | eager | 47.984 | 47.952 | 1.001x |
| 1000 | 262144 | 128 | graph | 48.175 | 48.224 | 0.999x |

</details>

Cake ships no other data type, layout or fused form of this kernel, and
its single source compiles into one module with one `-gencode` per
target on every compute capability 9.x, 10.x, 11.x and 12.x target
FlashInfer builds (sm_90a, sm_100a, sm_103a, sm_107a, sm_110a, sm_120a,
sm_120f, sm_121a).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* Added an automatically selected lean-scan option for eligible top-k
sampling workloads on B200 and GB300 devices.
* The option applies only to supported batch sizes and configurations;
other workloads continue using their existing sampling path.
* **Reliability**
* Improved handling of incompatible launch-option combinations, which
are now rejected.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [e0c3efc](https://github.com/flashinfer-ai/flashinfer/commit/e0c3efca66d1104cc86655e4173ac522567225b3)

- **作者**: eigen
- **时间**: 2026-10-30T10:20:16Z
- **提交信息**: perf(cake_warp_decode): pre-wait-claims K512 FC2 sibling on 20 SM100 decode rows (#7995)

`cake_warp_decode` is Cake's NVFP4 routed fused-MoE decode for 1 to 32
tokens. It is called through
`flashinfer.fused_moe.trtllm_fp4_block_scale_routed_moe(...)` with
`CakeWarpDecodeConfig(backend="cake")`. It has one data type (NVFP4
W4A4, BF16 output), several activation variants and one fused form: FC1
with the activation, FC2 and the top-k finalize. This PR updates that
one fused form. Cake ships no other data type, layout or fused form of
this kernel. Its activation variants all use this fused form, and the
family ships on sm_100a and sm_103a.

This PR changes the FC2 kernel of 20 decode rows on sm_100a. It does not
change any sm_103a launch.

- **sm_100a, `e256_i512_k8` at 16 to 32 tokens (17 rows) and
`e512_i1024_k10` at 8, 9 and 10 tokens (3 rows).** These rows used the
K512 device-workfeed FC2 kernel. In that kernel, the warp that claims
work waits for FC1 (`griddepcontrol.wait`) before it takes its first
work item. They now use a sibling build of the same kernel. Its
work-claiming warp takes up to min(3, ceil(grid_m * route_tiles /
launch_ctas) - 1) work items before it waits for FC1. Work items, K
order, MMA and epilogue are unchanged, and so are FC1, finalize and the
grid.
- **Other sm_100a rows.** `e512_i1024_k10` at 11 tokens and every other
sm_100a row launch the same kernels as before (492 rows).
- **sm_103a.** No launch changes. The new FC2 kernel is declared for
sm_103a, but no sm_103a row selects it.
- **Re-generated kernels.** The previous K512 FC2 kernel is re-generated
under a new name. Eight other shipped kernels are re-generated; the
changes are text-only. On sm_100a and sm_103a, the compiled code (SASS)
of all of them is identical to the previous version.

The baseline is the current Cake version on FlashInfer main (merged as
FlashInfer #7968).

- On sm_100a (NVIDIA GB200, CUDA 13.4), 19 of 512 rows in 16 geometries
are faster in both cold-L2 modes, and all 19 are changed rows. 20 rows
are faster with the memset flush and 19 with the read flush. All 20
changed rows are faster in at least one mode.
- The largest speedup is on `e256_i512_k8` at 23 tokens. With the memset
flush it goes from 47.17 us to 45.76 us (1.031x), and with the read
flush from 36.94 us to 35.93 us (1.028x).
- On `e512_i1024_k10`, the changed rows are faster in both modes:
- 8 tokens: 95.67 us to 94.16 us with memset (1.016x), 80.01 us to 78.80
us with read (1.015x).
- 9 tokens: 104.85 us to 103.53 us with memset (1.013x), 88.61 us to
87.45 us with read (1.013x).
- 10 tokens: 113.73 us to 112.52 us with memset (1.011x), 97.17 us to
96.05 us with read (1.012x).
- One changed row is faster in only one mode. `e256_i512_k8` at 25
tokens is faster with memset: 47.03 us to 45.79 us (1.027x). With read,
it prints 36.87 us to 36.02 us (1.024x), but it does not count as faster
in that mode, because one of its four measurements is within noise.
- One row is slower in one mode, and this PR does not change it:
`e192_i1536_k4_silu` at 14 tokens, read, 71.71 us previous and 72.16 us
new (ratio 1.006).

Across the 20 changed rows and both modes (40 values), the printed
speedup ranges from 1.011x to 1.031x (median 1.024x). No changed row
prints a ratio above 1.000. The largest is 0.989 (`e512_i1024_k10`, 10
tokens, memset). No unchanged row counts as faster in either mode. 230
unchanged rows print a ratio above 1.000 in at least one mode. The
largest is 1.010 (`e192_i1536_k4_silu`, 1 token, read).

There is no sm_103a timing table. No sm_103a launch changes, and the
compiled code of every previously shipped kernel is identical on
sm_103a.

The "memset" and "read" column groups are two cold-L2 modes. Before
every call, we flush L2 with either a memset of a large buffer or a read
of one. Latency covers one routed-MoE call: FC1, FC2 and finalize.

Each table value is the mean of four measurements: two GPUs (one on each
of two nodes), each measured in two separate processes. Each measurement
is the median over 6 rounds of the per-round median over 40 calls, after
5 warmup calls.

A row counts as faster (or slower) in a mode only when all four
measurements show it faster (or slower) by more than run-to-run noise.
That means every round agrees, and the median beats both a 0.5 % floor
and the A/A noise band.

Speedups in the summary table are previous / new, so higher is better.
The per-row tables give ratio = new / previous, so lower is better
there.

**sm_100a** (NVIDIA GB200, driver 580.126.20, nvcc 13.4, CUDA driver API
13.4)

| Geometry | Rows faster in both modes (of 32) | Best speedup, memset
(tokens) | Best speedup, read (tokens) |
|---|---|---|---|
| `e256_i512_k8` | 16 | 1.031x (23) | 1.028x (23) |
| `e512_i1024_k10` | 3 | 1.016x (8) | 1.015x (8) |
| `e128_i1536_k8` | 0 | — | — |
| `e128_i3072_k4_swiglu_oa` | 0 | — | — |
| `e128_i768_k8` | 0 | — | — |
| `e192_i1536_k4_silu` | 0 | — | — |
| `e256_i1536_k8` | 0 | — | — |
| `e256_i2048_k6_clamp10` | 0 | — | — |
| `e384_i768_k4` | 0 | — | — |
| `e512_i512_k10` | 0 | — | — |
| `e60_i1536_k4` | 0 | — | — |
| `e896_i3072_k16_situ` | 0 | — | — |
| `h3072_e256_i384_k8` | 0 | — | — |
| `h3072_e256_i768_k8` | 0 | — | — |
| `h4096_e512_i256_k10` | 0 | — | — |
| `h4096_e512_i512_k10` | 0 | — | — |

`e192_i1536_k4_silu` at 14 tokens is slower in the read mode: 71.71 us
previous, 72.16 us new (ratio 1.006).

**sm_100a** (NVIDIA GB200, driver 580.126.20, nvcc 13.4, CUDA driver API
13.4). Latency in us of one routed-MoE call (FC1, FC2, finalize), cold
L2; previous = the current Cake version (FlashInfer main), new = this
PR; ratio = new / previous. **Bold** num_tokens: this PR changes the
row's launches. Plain: the row launches the same kernels as the previous
version.

`e128_i768_k8`: hidden 2048, intermediate 768, 128 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|14.30|14.28|0.999|12.57|12.55|0.998|
|2|18.17|18.16|0.999|15.80|15.73|0.996|
|3|21.79|21.83|1.002|18.39|18.33|0.997|
|4|23.96|23.96|1.000|19.68|19.78|1.005|
|5|28.12|28.20|1.003|22.95|22.93|0.999|
|6|31.12|31.14|1.001|24.82|24.77|0.998|
|7|36.00|35.92|0.998|27.99|27.82|0.994|
|8|39.67|39.64|0.999|30.77|30.75|0.999|
|9|42.72|42.64|0.998|33.32|33.23|0.997|
|10|44.91|44.93|1.000|35.24|35.27|1.001|
|11|48.06|48.11|1.001|37.67|37.58|0.998|
|12|51.35|51.37|1.000|40.11|39.98|0.997|
|13|54.84|54.88|1.001|42.73|42.82|1.002|
|14|58.03|58.08|1.001|45.27|45.27|1.000|
|15|61.07|61.09|1.000|47.84|47.76|0.998|
|16|64.74|64.76|1.000|51.14|51.12|1.000|
|17|66.88|66.77|0.998|53.00|53.06|1.001|
|18|69.46|69.52|1.001|55.39|55.40|1.000|
|19|71.50|71.54|1.001|57.09|57.03|0.999|
|20|70.76|70.78|1.000|56.55|56.44|0.998|
|21|70.70|70.71|1.000|56.54|56.53|1.000|
|22|70.79|70.75|0.999|56.65|56.61|0.999|
|23|70.82|70.86|1.001|56.64|56.63|1.000|
|24|70.63|70.71|1.001|56.52|56.58|1.001|
|25|70.87|70.80|0.999|56.70|56.79|1.002|
|26|70.91|70.67|0.997|56.77|56.69|0.999|
|27|70.87|70.86|1.000|56.73|56.79|1.001|
|28|70.47|70.84|1.005|56.76|56.80|1.001|
|29|70.94|70.91|1.000|56.82|56.81|1.000|
|30|70.91|70.84|0.999|56.89|56.81|0.999|
|31|70.86|70.83|1.000|56.80|56.84|1.001|
|32|72.26|72.23|1.000|57.98|57.98|1.000|

`h4096_e512_i512_k10`: hidden 4096, intermediate 512, 512 experts,
top-10, swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|16.83|16.93|1.006|15.60|15.69|1.006|
|2|21.60|21.64|1.002|19.83|19.74|0.995|
|3|25.98|25.97|1.000|23.90|23.92|1.001|
|4|31.88|31.74|0.996|28.77|28.73|0.999|
|5|36.18|36.06|0.997|32.77|32.70|0.998|
|6|41.13|41.07|0.999|37.22|37.24|1.001|
|7|45.77|45.87|1.002|41.39|41.58|1.005|
|8|50.08|50.16|1.002|45.36|45.45|1.002|
|9|55.27|55.43|1.003|49.78|50.15|1.007|
|10|59.47|59.64|1.003|53.60|53.80|1.004|
|11|64.65|64.57|0.999|58.43|58.45|1.000|
|12|68.66|68.55|0.998|61.98|61.95|1.000|
|13|73.51|73.52|1.000|66.72|66.90|1.003|
|14|78.01|77.92|0.999|70.65|70.54|0.998|
|15|82.63|82.65|1.000|75.04|74.70|0.995|
|16|86.85|86.96|1.001|78.54|78.73|1.002|
|17|91.80|91.58|0.998|83.27|82.97|0.996|
|18|96.04|96.18|1.001|86.99|87.23|1.003|
|19|100.64|100.62|1.000|91.46|91.33|0.999|
|20|105.18|105.33|1.001|95.54|95.59|1.001|
|21|110.14|110.34|1.002|99.87|100.28|1.004|
|22|114.57|114.40|0.999|104.03|103.87|0.998|
|23|118.81|118.85|1.000|108.01|107.92|0.999|
|24|123.14|123.29|1.001|111.83|112.36|1.005|
|25|128.20|128.29|1.001|116.90|116.69|0.998|
|26|132.90|132.88|1.000|120.92|120.90|1.000|
|27|137.04|137.33|1.002|124.65|124.83|1.001|
|28|141.41|141.52|1.001|128.69|128.81|1.001|
|29|145.80|146.12|1.002|132.81|133.01|1.002|
|30|150.21|150.24|1.000|136.83|137.02|1.001|
|31|154.70|154.65|1.000|141.28|141.07|0.999|
|32|159.02|158.85|0.999|145.24|144.87|0.997|

`h4096_e512_i256_k10`: hidden 4096, intermediate 256, 512 experts,
top-10, swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|14.49|14.44|0.997|13.59|13.54|0.996|
|2|16.69|16.72|1.002|15.45|15.54|1.006|
|3|19.65|19.66|1.001|18.09|18.12|1.002|
|4|22.82|22.83|1.000|20.90|20.99|1.004|
|5|25.26|25.23|0.999|23.25|23.31|1.003|
|6|27.37|27.32|0.998|25.20|25.19|1.000|
|7|30.14|30.12|0.999|27.58|27.54|0.999|
|8|32.98|32.98|1.000|30.20|30.25|1.002|
|9|35.40|35.39|1.000|32.50|32.49|1.000|
|10|37.83|37.93|1.003|34.67|34.73|1.002|
|11|40.36|40.33|0.999|37.07|37.11|1.001|
|12|42.76|42.83|1.002|39.50|39.70|1.005|
|13|45.37|45.42|1.001|42.01|42.11|1.002|
|14|47.82|47.88|1.001|44.16|44.25|1.002|
|15|50.41|50.47|1.001|46.62|46.54|0.998|
|16|52.54|52.56|1.000|48.55|48.71|1.003|
|17|55.13|55.09|0.999|51.23|51.05|0.996|
|18|57.56|57.71|1.003|53.53|53.49|0.999|
|19|60.34|60.48|1.002|56.15|56.31|1.003|
|20|62.69|62.73|1.001|58.39|58.21|0.997|
|21|65.28|65.37|1.001|60.79|60.79|1.000|
|22|67.71|67.87|1.002|63.12|63.25|1.002|
|23|70.43|70.31|0.998|65.70|65.54|0.998|
|24|72.86|72.77|0.999|67.68|67.72|1.001|
|25|75.07|75.52|1.006|69.79|70.44|1.009|
|26|77.80|77.75|0.999|72.68|72.51|0.998|
|27|80.45|80.35|0.999|75.15|75.09|0.999|
|28|82.91|82.63|0.997|77.39|77.25|0.998|
|29|85.19|85.13|0.999|79.58|79.49|0.999|
|30|87.68|87.72|1.000|81.87|81.90|1.000|
|31|90.41|90.15|0.997|84.61|84.34|0.997|
|32|92.73|92.51|0.998|86.93|86.65|0.997|

`h3072_e256_i768_k8`: hidden 3072, intermediate 768, 256 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|16.33|16.27|0.996|14.71|14.64|0.995|
|2|21.75|21.66|0.996|19.66|19.62|0.998|
|3|25.18|25.12|0.998|22.56|22.53|0.999|
|4|28.87|28.90|1.001|25.89|25.85|0.998|
|5|34.10|34.16|1.002|30.23|30.15|0.997|
|6|37.90|37.82|0.998|33.65|33.58|0.998|
|7|42.16|42.19|1.001|37.47|37.46|1.000|
|8|46.13|46.12|1.000|40.95|41.07|1.003|
|9|50.43|50.45|1.000|45.11|45.10|1.000|
|10|54.62|54.61|1.000|48.73|48.75|1.000|
|11|58.43|58.44|1.000|52.20|52.26|1.001|
|12|62.36|62.28|0.999|55.83|55.80|0.999|
|13|66.42|66.54|1.002|59.37|59.50|1.002|
|14|70.43|70.39|0.999|63.09|63.13|1.001|
|15|74.62|74.62|1.000|67.04|67.01|1.000|
|16|74.51|74.48|1.000|66.77|66.80|1.000|
|17|74.69|74.58|0.999|67.02|66.94|0.999|
|18|74.60|74.67|1.001|66.87|67.04|1.003|
|19|74.72|74.64|0.999|67.10|66.90|0.997|
|20|74.63|74.64|1.000|66.84|66.94|1.001|
|21|74.80|74.85|1.001|67.02|67.12|1.001|
|22|74.74|74.68|0.999|66.97|67.08|1.002|
|23|74.72|74.61|0.999|67.09|66.87|0.997|
|24|74.59|74.72|1.002|66.93|67.00|1.001|
|25|74.84|74.83|1.000|67.13|67.24|1.002|
|26|74.92|74.84|0.999|67.25|67.19|0.999|
|27|74.96|74.82|0.998|67.23|67.17|0.999|
|28|74.82|74.76|0.999|67.10|67.08|1.000|
|29|74.98|74.91|0.999|67.25|67.34|1.001|
|30|74.86|74.88|1.000|67.15|67.21|1.001|
|31|74.96|75.01|1.001|67.26|67.31|1.001|
|32|74.90|74.83|0.999|67.10|67.12|1.000|

`h3072_e256_i384_k8`: hidden 3072, intermediate 384, 256 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|13.86|13.75|0.992|12.99|12.88|0.992|
|2|16.66|16.63|0.998|15.25|15.24|0.999|
|3|19.11|19.08|0.998|17.35|17.33|0.999|
|4|21.44|21.31|0.994|19.37|19.38|1.001|
|5|23.63|23.62|1.000|21.50|21.54|1.002|
|6|26.01|25.98|0.999|23.43|23.28|0.994|
|7|27.69|27.76|1.003|24.64|24.75|1.004|
|8|29.90|29.96|1.002|27.04|27.08|1.001|
|9|32.76|32.75|1.000|29.40|29.48|1.003|
|10|34.52|34.52|1.000|31.11|31.04|0.998|
|11|36.48|36.55|1.002|32.89|32.94|1.002|
|12|38.42|38.41|1.000|34.74|34.69|0.999|
|13|40.57|40.56|1.000|36.69|36.71|1.001|
|14|42.60|42.55|0.999|38.61|38.57|0.999|
|15|44.46|44.42|0.999|40.44|40.43|1.000|
|16|44.41|44.37|0.999|40.38|40.34|0.999|
|17|44.54|44.52|1.000|40.50|40.50|1.000|
|18|44.52|44.61|1.002|40.51|40.55|1.001|
|19|44.62|44.57|0.999|40.57|40.56|1.000|
|20|44.59|44.61|1.000|40.60|40.53|0.998|
|21|44.56|44.57|1.000|40.57|40.59|1.000|
|22|44.65|44.63|1.000|40.61|40.63|1.000|
|23|44.63|44.65|1.000|40.64|40.68|1.001|
|24|44.54|44.60|1.001|40.68|40.64|0.999|
|25|44.85|44.79|0.999|40.77|40.75|1.000|
|26|44.85|44.84|1.000|40.79|40.86|1.002|
|27|44.83|44.87|1.001|40.81|40.81|1.000|
|28|44.87|44.84|0.999|40.82|40.83|1.000|
|29|44.86|44.87|1.000|40.78|40.88|1.002|
|30|44.99|44.95|0.999|40.90|40.84|0.999|
|31|44.95|44.90|0.999|40.89|40.86|0.999|
|32|44.98|44.96|1.000|40.88|40.80|0.998|

`e512_i512_k10`: hidden 2048, intermediate 512, 512 experts, top-10,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|13.80|13.75|0.996|12.27|12.33|1.005|
|2|17.14|17.25|1.006|14.87|14.83|0.997|
|3|20.11|20.03|0.996|17.13|17.07|0.996|
|4|23.40|23.53|1.006|19.13|19.22|1.005|
|5|25.30|25.21|0.996|20.54|20.54|1.000|
|6|28.84|28.86|1.001|23.07|23.28|1.009|
|7|32.70|32.72|1.001|25.80|25.89|1.003|
|8|35.49|35.61|1.003|27.96|28.22|1.009|
|9|38.47|38.43|0.999|30.08|30.06|0.999|
|10|41.09|41.07|1.000|32.46|32.49|1.001|
|11|44.06|44.09|1.001|34.65|34.65|1.000|
|12|46.65|46.68|1.001|36.83|36.91|1.002|
|13|49.54|49.61|1.001|39.16|39.14|0.999|
|14|52.19|52.20|1.000|41.32|41.28|0.999|
|15|55.07|55.11|1.001|43.83|43.81|1.000|
|16|57.65|57.47|0.997|46.05|45.92|0.997|
|17|60.18|60.22|1.001|48.09|48.14|1.001|
|18|62.88|62.83|0.999|50.47|50.44|0.999|
|19|65.31|65.20|0.998|52.48|52.71|1.004|
|20|67.71|67.70|1.000|54.94|54.97|1.001|
|21|69.99|70.02|1.000|57.20|57.23|1.001|
|22|72.31|72.23|0.999|59.39|59.24|0.997|
|23|74.64|74.63|1.000|61.62|61.57|0.999|
|24|77.04|77.07|1.000|63.76|63.74|1.000|
|25|79.54|79.56|1.000|66.09|66.21|1.002|
|26|82.01|82.04|1.000|68.30|68.38|1.001|
|27|84.92|84.88|1.000|71.07|71.11|1.001|
|28|87.31|87.36|1.001|73.36|73.19|0.998|
|29|89.95|89.98|1.000|75.52|75.44|0.999|
|30|93.56|93.57|1.000|78.56|78.52|0.999|
|31|95.90|96.06|1.002|80.62|80.69|1.001|
|32|97.49|97.53|1.000|82.15|82.23|1.001|

`e60_i1536_k4`: hidden 2048, intermediate 1536, 60 experts, top-4,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|13.90|13.73|0.988|12.43|12.30|0.990|
|2|16.99|16.97|0.999|15.12|15.17|1.003|
|3|20.57|20.46|0.995|17.72|17.65|0.996|
|4|23.27|23.44|1.007|19.78|19.78|1.000|
|5|26.87|26.84|0.999|21.74|21.92|1.008|
|6|28.91|28.93|1.001|23.11|23.10|1.000|
|7|31.73|31.81|1.003|24.97|25.07|1.004|
|8|34.45|34.47|1.001|27.29|27.43|1.005|
|9|36.87|36.91|1.001|28.71|28.75|1.001|
|10|39.51|39.51|1.000|30.80|30.86|1.002|
|11|41.64|41.60|0.999|32.20|32.25|1.002|
|12|42.26|42.24|1.000|33.29|33.27|0.999|
|13|44.02|44.00|1.000|34.59|34.58|1.000|
|14|45.31|45.24|0.998|35.62|35.37|0.993|
|15|47.69|47.61|0.998|37.46|37.47|1.000|
|16|49.08|49.08|1.000|38.33|38.22|0.997|
|17|51.55|51.62|1.001|40.39|40.37|1.000|
|18|53.55|53.37|0.997|41.97|41.98|1.000|
|19|55.19|55.28|1.002|43.30|43.45|1.003|
|20|56.87|56.80|0.999|44.71|44.72|1.000|
|21|58.52|58.53|1.000|46.11|46.17|1.001|
|22|60.27|60.32|1.001|47.65|47.57|0.998|
|23|61.92|61.92|1.000|48.96|48.96|1.000|
|24|63.52|63.54|1.000|50.41|50.47|1.001|
|25|65.61|65.57|0.999|52.05|52.03|1.000|
|26|67.34|67.31|1.000|53.50|53.56|1.001|
|27|67.29|67.25|0.999|53.53|53.55|1.000|
|28|67.29|67.29|1.000|53.61|53.57|0.999|
|29|67.32|67.32|1.000|53.56|53.48|0.999|
|30|67.35|67.31|0.999|53.63|53.58|0.999|
|31|67.33|67.26|0.999|53.56|53.61|1.001|
|32|66.74|66.72|1.000|53.00|52.96|0.999|

`e192_i1536_k4_silu`: hidden 6144, intermediate 1536, 192 experts,
top-4, silu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|19.52|19.62|1.005|17.16|17.33|1.010|
|2|25.34|25.38|1.002|20.57|20.41|0.992|
|3|30.80|30.88|1.003|24.76|24.83|1.003|
|4|38.19|38.35|1.004|29.97|30.07|1.003|
|5|42.80|42.48|0.993|33.25|33.15|0.997|
|6|47.73|47.64|0.998|37.24|37.28|1.001|
|7|54.28|54.46|1.003|42.20|42.24|1.001|
|8|59.06|59.14|1.001|46.04|45.89|0.997|
|9|63.60|63.62|1.000|49.66|49.61|0.999|
|10|68.71|68.73|1.000|54.93|54.80|0.998|
|11|72.89|72.86|1.000|58.57|58.57|1.000|
|12|77.31|77.33|1.000|62.77|62.59|0.997|
|13|82.13|82.12|1.000|67.50|67.77|1.004|
|14|86.67|86.53|0.998|71.71|72.16|1.006|
|15|90.99|90.97|1.000|75.86|75.91|1.001|
|16|95.54|95.66|1.001|80.68|80.56|0.999|
|17|99.85|99.90|1.001|84.88|84.84|1.000|
|18|104.18|104.22|1.000|88.86|89.16|1.003|
|19|109.09|109.16|1.001|93.50|93.54|1.000|
|20|113.09|113.05|1.000|97.78|97.84|1.001|
|21|117.74|117.29|0.996|102.18|101.97|0.998|
|22|122.16|121.94|0.998|106.51|106.29|0.998|
|23|126.83|126.82|1.000|110.89|110.68|0.998|
|24|130.86|130.76|0.999|114.86|114.79|0.999|
|25|135.49|135.59|1.001|119.32|119.40|1.001|
|26|139.94|140.32|1.003|123.64|123.77|1.001|
|27|144.53|144.30|0.998|127.84|127.61|0.998|
|28|148.80|148.92|1.001|132.19|132.21|1.000|
|29|153.24|153.39|1.001|136.51|136.71|1.001|
|30|157.41|157.58|1.001|140.56|140.72|1.001|
|31|161.81|161.87|1.000|144.83|144.99|1.001|
|32|166.05|166.33|1.002|149.28|149.50|1.001|

`e384_i768_k4`: hidden 2560, intermediate 768, 384 experts, top-4,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|12.05|12.02|0.998|11.06|11.00|0.995|
|2|14.27|14.17|0.993|12.64|12.59|0.996|
|3|16.42|16.38|0.998|14.58|14.57|0.999|
|4|18.89|18.93|1.002|16.73|16.83|1.006|
|5|20.69|20.67|0.999|17.69|17.70|1.001|
|6|22.66|22.68|1.001|18.92|18.89|0.998|
|7|25.11|25.17|1.002|21.17|21.11|0.997|
|8|27.08|27.03|0.998|22.19|22.06|0.994|
|9|28.48|28.50|1.001|23.20|23.08|0.995|
|10|31.14|30.84|0.990|25.51|25.47|0.998|
|11|32.50|32.33|0.995|26.43|26.23|0.992|
|12|34.14|33.94|0.994|27.35|27.18|0.994|
|13|35.91|35.77|0.996|28.87|28.81|0.998|
|14|37.51|37.53|1.001|29.98|29.99|1.000|
|15|39.13|39.13|1.000|30.97|30.85|0.996|
|16|40.85|40.70|0.996|32.32|32.27|0.998|
|17|42.33|42.49|1.004|33.74|33.80|1.002|
|18|44.04|44.04|1.000|34.78|34.86|1.002|
|19|45.78|45.91|1.003|36.16|36.24|1.002|
|20|47.41|47.36|0.999|37.50|37.44|0.998|
|21|49.09|49.05|0.999|38.89|38.88|1.000|
|22|51.06|51.08|1.000|40.33|40.30|0.999|
|23|52.64|52.66|1.000|41.69|41.82|1.003|
|24|54.49|54.42|0.999|42.93|42.82|0.997|
|25|56.16|56.15|1.000|44.40|44.58|1.004|
|26|58.01|57.82|0.997|45.81|45.88|1.002|
|27|59.73|59.59|0.998|47.16|47.22|1.001|
|28|61.17|61.15|1.000|48.53|48.62|1.002|
|29|62.77|62.81|1.001|50.01|49.93|0.998|
|30|64.13|64.19|1.001|51.15|51.18|1.001|
|31|65.72|65.76|1.001|52.59|52.64|1.001|
|32|67.21|67.15|0.999|54.00|53.89|0.998|

`e128_i1536_k8`: hidden 4096, intermediate 1536, 128 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|24.76|24.66|0.996|20.58|20.61|1.001|
|2|38.42|38.34|0.998|30.10|30.02|0.997|
|3|52.97|52.92|0.999|41.50|41.45|0.999|
|4|63.73|63.62|0.998|50.30|50.19|0.998|
|5|75.27|75.20|0.999|60.81|60.84|1.000|
|6|86.26|86.38|1.001|71.04|71.06|1.000|
|7|96.68|96.65|1.000|81.56|81.56|1.000|
|8|107.30|107.50|1.002|91.46|91.49|1.000|
|9|117.61|117.88|1.002|101.64|101.82|1.002|
|10|127.90|127.90|1.000|111.49|111.60|1.001|
|11|138.10|137.96|0.999|121.46|121.30|0.999|
|12|147.43|147.40|1.000|130.44|130.46|1.000|
|13|157.16|157.17|1.000|140.17|140.22|1.000|
|14|167.16|167.13|1.000|150.08|149.93|0.999|
|15|176.86|176.87|1.000|159.84|159.87|1.000|
|16|186.63|186.52|0.999|169.59|169.50|0.999|
|17|194.09|194.26|1.001|176.96|177.08|1.001|
|18|201.06|200.98|1.000|183.96|183.83|0.999|
|19|207.90|208.11|1.001|190.84|190.94|1.001|
|20|208.14|208.03|0.999|191.00|190.88|0.999|
|21|208.13|208.17|1.000|191.15|191.01|0.999|
|22|208.27|208.22|1.000|191.20|191.07|0.999|
|23|208.16|208.24|1.000|191.07|191.21|1.001|
|24|208.29|208.27|1.000|191.31|191.21|0.999|
|25|208.90|208.92|1.000|192.20|192.15|1.000|
|26|208.88|208.95|1.000|192.17|192.12|1.000|
|27|208.85|209.05|1.001|192.23|192.31|1.000|
|28|209.20|208.90|0.999|192.33|192.29|1.000|
|29|208.95|209.13|1.001|192.33|192.45|1.001|
|30|209.20|209.15|1.000|192.51|192.40|0.999|
|31|209.29|209.36|1.000|192.48|192.43|1.000|
|32|209.22|209.25|1.000|192.52|192.58|1.000|

`e256_i512_k8`: hidden 2048, intermediate 512, 256 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|13.00|12.99|0.999|11.61|11.57|0.997|
|2|15.49|15.47|0.999|13.92|13.89|0.998|
|3|18.38|18.35|0.998|15.94|15.93|0.999|
|4|19.61|19.53|0.996|16.53|16.55|1.001|
|5|23.61|23.58|0.999|19.51|19.53|1.001|
|6|25.06|24.98|0.997|20.49|20.39|0.995|
|7|27.72|27.80|1.003|22.06|22.21|1.007|
|8|29.59|29.64|1.002|23.31|23.29|0.999|
|9|32.62|32.57|0.998|25.38|25.45|1.003|
|10|34.68|34.79|1.003|27.27|27.42|1.006|
|11|37.03|37.00|0.999|28.84|28.84|1.000|
|12|39.10|39.14|1.001|30.71|30.69|0.999|
|13|41.28|41.35|1.002|32.27|32.33|1.002|
|14|43.37|43.41|1.001|34.05|34.01|0.999|
|15|45.38|45.50|1.003|35.82|35.86|1.001|
|**16**|46.73|45.63|0.976|36.67|35.88|0.978|
|**17**|46.86|45.60|0.973|36.66|35.89|0.979|
|**18**|46.86|45.67|0.975|36.67|35.88|0.978|
|**19**|46.89|45.72|0.975|36.80|35.93|0.976|
|**20**|46.81|45.66|0.975|36.76|35.94|0.978|
|**21**|47.02|45.78|0.974|36.73|35.91|0.978|
|**22**|47.01|45.83|0.975|36.88|36.07|0.978|
|**23**|47.17|45.76|0.970|36.94|35.93|0.973|
|**24**|47.05|45.74|0.972|36.85|35.93|0.975|
|**25**|47.03|45.79|0.974|36.87|36.02|0.977|
|**26**|47.01|45.78|0.974|36.88|36.00|0.976|
|**27**|47.00|45.78|0.974|36.99|36.04|0.974|
|**28**|47.06|45.75|0.972|37.00|36.12|0.976|
|**29**|47.12|45.94|0.975|36.96|36.23|0.980|
|**30**|47.05|45.89|0.975|36.97|36.19|0.979|
|**31**|47.06|45.86|0.975|36.90|36.07|0.978|
|**32**|47.07|45.84|0.974|36.94|36.27|0.982|

`e512_i1024_k10`: hidden 4096, intermediate 1024, 512 experts, top-10,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|24.09|23.88|0.991|20.45|20.15|0.985|
|2|34.27|34.30|1.001|27.34|27.32|0.999|
|3|44.95|44.93|1.000|35.49|35.33|0.995|
|4|55.64|55.57|0.999|43.50|43.70|1.005|
|5|65.68|65.55|0.998|52.31|52.33|1.000|
|6|75.48|75.58|1.001|60.95|60.99|1.001|
|7|84.75|84.77|1.000|69.81|69.83|1.000|
|**8**|95.67|94.16|0.984|80.01|78.80|0.985|
|**9**|104.85|103.53|0.987|88.61|87.45|0.987|
|**10**|113.73|112.52|0.989|97.17|96.05|0.988|
|11|122.17|122.27|1.001|105.48|105.55|1.001|
|12|130.78|130.63|0.999|113.86|113.83|1.000|
|13|139.03|139.15|1.001|122.25|122.32|1.001|
|14|147.68|147.67|1.000|130.69|130.58|0.999|
|15|156.28|156.10|0.999|139.12|139.04|0.999|
|16|164.54|164.57|1.000|147.37|147.41|1.000|
|17|173.43|173.56|1.001|156.08|156.17|1.001|
|18|181.75|181.67|1.000|164.44|164.39|1.000|
|19|190.04|190.21|1.001|172.83|172.87|1.000|
|20|198.41|198.46|1.000|181.13|181.11|1.000|
|21|206.88|206.93|1.000|189.50|189.48|1.000|
|22|215.15|215.39|1.001|197.90|197.93|1.000|
|23|223.62|223.52|1.000|206.21|206.18|1.000|
|24|232.18|231.98|0.999|214.76|214.59|0.999|
|25|240.81|240.78|1.000|223.43|223.43|1.000|
|26|249.75|249.52|0.999|232.29|232.11|0.999|
|27|257.78|258.19|1.002|240.29|240.55|1.001|
|28|266.49|266.36|1.000|249.08|248.84|0.999|
|29|274.46|274.79|1.001|257.29|257.39|1.000|
|30|283.01|282.94|1.000|265.47|265.55|1.000|
|31|291.47|291.25|0.999|274.02|273.87|0.999|
|32|299.16|299.38|1.001|281.78|282.06|1.001|

`e256_i1536_k8`: hidden 3072, intermediate 1536, 256 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|21.83|21.81|0.999|18.45|18.37|0.996|
|2|32.80|32.88|1.002|26.04|26.09|1.002|
|3|42.79|42.69|0.998|33.58|33.55|0.999|
|4|52.12|52.29|1.003|40.89|40.85|0.999|
|5|61.84|61.89|1.001|48.31|48.34|1.001|
|6|70.07|70.07|1.000|56.10|56.14|1.001|
|7|78.19|78.17|1.000|63.71|63.58|0.998|
|8|86.32|86.26|0.999|71.33|71.22|0.998|
|9|94.02|94.17|1.002|78.86|78.81|0.999|
|10|101.81|101.68|0.999|86.37|86.33|1.000|
|11|109.73|109.78|1.000|93.84|93.85|1.000|
|12|117.40|117.37|1.000|101.39|101.32|0.999|
|13|125.28|125.26|1.000|108.94|108.88|0.999|
|14|132.77|132.81|1.000|116.31|116.27|1.000|
|15|140.31|140.27|1.000|123.85|123.75|0.999|
|16|140.72|140.62|0.999|123.69|123.53|0.999|
|17|141.14|141.14|1.000|124.00|123.97|1.000|
|18|141.09|141.08|1.000|123.96|124.01|1.000|
|19|141.25|141.24|1.000|124.12|124.16|1.000|
|20|141.21|141.26|1.000|124.10|124.12|1.000|
|21|141.31|141.29|1.000|124.24|124.22|1.000|
|22|141.32|141.27|1.000|124.21|124.26|1.000|
|23|141.36|141.29|1.000|124.31|124.26|1.000|
|24|141.30|141.28|1.000|124.35|124.23|0.999|
|25|141.84|141.78|1.000|124.94|124.96|1.000|
|26|141.80|141.81|1.000|124.98|124.97|1.000|
|27|141.21|141.20|1.000|124.44|124.40|1.000|
|28|141.32|141.33|1.000|124.53|124.56|1.000|
|29|141.91|141.85|1.000|125.12|125.01|0.999|
|30|141.30|141.28|1.000|124.55|124.55|1.000|
|31|141.87|141.93|1.000|125.06|125.20|1.001|
|32|141.41|141.39|1.000|124.60|124.60|1.000|

`e128_i3072_k4_swiglu_oa`: hidden 6144, intermediate 3072, 128 experts,
top-4, swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|35.57|35.63|1.002|28.32|28.33|1.000|
|2|51.64|51.74|1.002|39.74|39.62|0.997|
|3|67.32|67.41|1.001|52.70|52.91|1.004|
|4|80.85|80.88|1.000|65.85|65.71|0.998|
|5|93.82|93.75|0.999|77.56|77.53|1.000|
|6|107.23|107.14|0.999|90.69|90.42|0.997|
|7|120.22|120.33|1.001|103.08|103.47|1.004|
|8|132.99|133.02|1.000|115.85|115.90|1.000|
|9|146.35|146.21|0.999|128.42|128.45|1.000|
|10|159.46|159.52|1.000|141.47|141.58|1.001|
|11|171.80|171.86|1.000|154.28|154.36|1.001|
|12|184.57|184.59|1.000|167.01|166.89|0.999|
|13|196.73|196.87|1.001|178.93|179.01|1.000|
|14|209.11|209.26|1.001|191.53|191.45|1.000|
|15|221.64|221.80|1.001|203.99|203.86|0.999|
|16|234.47|234.31|0.999|216.45|216.35|1.000|
|17|248.59|248.58|1.000|230.88|230.95|1.000|
|18|261.19|261.08|1.000|243.42|243.31|1.000|
|19|273.53|273.45|1.000|255.90|255.89|1.000|
|20|281.74|281.58|0.999|264.24|264.24|1.000|
|21|290.09|290.00|1.000|272.54|272.73|1.001|
|22|298.33|298.43|1.000|281.00|280.97|1.000|
|23|306.63|306.72|1.000|289.33|289.40|1.000|
|24|315.19|315.03|0.999|297.92|297.74|0.999|
|25|323.76|323.65|1.000|306.44|306.44|1.000|
|26|332.36|332.09|0.999|315.05|315.07|1.000|
|27|340.54|340.42|1.000|323.21|323.26|1.000|
|28|348.79|348.73|1.000|331.56|331.68|1.000|
|29|357.16|357.10|1.000|339.91|339.99|1.000|
|30|365.56|365.40|1.000|348.40|348.29|1.000|
|31|373.91|373.94|1.000|356.66|356.80|1.000|
|32|382.14|382.16|1.000|365.05|364.99|1.000|

`e256_i2048_k6_clamp10`: hidden 4096, intermediate 2048, 256 experts,
top-6, swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|24.46|24.40|0.998|20.00|19.99|0.999|
|2|37.92|37.91|1.000|29.50|29.46|0.999|
|3|50.11|50.11|1.000|38.51|38.49|0.999|
|4|61.48|61.46|1.000|48.19|48.19|1.000|
|5|72.43|72.34|0.999|58.16|58.22|1.001|
|6|82.65|82.57|0.999|67.42|67.54|1.002|
|7|92.84|92.88|1.000|77.45|77.49|1.001|
|8|104.65|104.70|1.000|89.02|89.15|1.001|
|9|114.54|114.52|1.000|98.36|98.26|0.999|
|10|124.13|124.10|1.000|107.44|107.54|1.001|
|11|133.90|133.97|1.001|117.02|117.00|1.000|
|12|143.11|143.15|1.000|126.21|126.19|1.000|
|13|152.92|152.91|1.000|135.87|135.92|1.000|
|14|162.06|162.10|1.000|144.65|144.71|1.000|
|15|171.57|171.64|1.000|154.20|154.19|1.000|
|16|171.62|171.68|1.000|154.29|154.36|1.000|
|17|172.32|172.32|1.000|154.97|154.97|1.000|
|18|172.42|172.39|1.000|155.07|155.07|1.000|
|19|172.52|172.42|0.999|155.17|155.19|1.000|
|20|172.35|172.41|1.000|155.09|155.17|1.001|
|21|172.48|172.53|1.000|155.27|155.18|0.999|
|22|172.45|172.50|1.000|155.20|155.30|1.001|
|23|172.74|172.78|1.000|155.64|155.60|1.000|
|24|172.49|172.60|1.001|155.24|155.27|1.000|
|25|173.51|173.58|1.000|156.16|156.10|1.000|
|26|173.60|173.52|1.000|156.18|156.07|0.999|
|27|173.68|173.70|1.000|156.25|156.35|1.001|
|28|173.68|173.63|1.000|156.20|156.43|1.001|
|29|173.74|173.73|1.000|156.40|156.31|0.999|
|30|174.07|173.91|0.999|156.78|156.62|0.999|
|31|173.75|173.83|1.000|156.70|156.86|1.001|
|32|173.92|173.92|1.000|156.94|156.97|1.000|

`e896_i3072_k16_situ`: hidden 3584, intermediate 3072, 896 experts,
top-16, situ

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|70.52|70.48|0.999|59.65|59.41|0.996|
|2|113.56|113.72|1.001|102.67|102.64|1.000|
|3|151.51|151.81|1.002|142.70|142.76|1.000|
|4|193.34|193.33|1.000|185.64|185.55|1.000|
|5|232.03|231.97|1.000|224.79|224.54|0.999|
|6|272.75|272.91|1.001|265.53|265.79|1.001|
|7|313.60|313.77|1.001|306.96|306.82|1.000|
|8|354.32|354.02|0.999|347.11|347.10|1.000|
|9|394.85|394.74|1.000|388.05|387.62|0.999|
|10|435.73|435.74|1.000|428.66|429.13|1.001|
|11|478.68|478.80|1.000|471.98|471.97|1.000|
|12|519.53|519.80|1.001|512.93|512.86|1.000|
|13|560.52|560.27|1.000|553.93|553.83|1.000|
|14|600.96|601.25|1.000|594.63|594.76|1.000|
|15|640.55|640.21|0.999|634.10|633.75|0.999|
|16|682.49|682.58|1.000|675.60|676.01|1.001|
|17|722.63|722.52|1.000|716.41|716.39|1.000|
|18|763.34|763.67|1.000|757.07|757.35|1.000|
|19|804.03|804.21|1.000|797.19|797.86|1.001|
|20|844.46|844.40|1.000|837.73|838.24|1.001|
|21|885.26|885.12|1.000|878.37|878.19|1.000|
|22|926.27|926.13|1.000|919.58|919.64|1.000|
|23|966.68|966.20|1.000|960.15|959.98|1.000|
|24|1007.81|1007.18|0.999|1001.04|1000.91|1.000|
|25|1047.91|1048.09|1.000|1041.13|1041.78|1.001|
|26|1088.88|1087.98|0.999|1081.96|1081.78|1.000|
|27|1129.12|1128.95|1.000|1122.38|1122.41|1.000|
|28|1169.78|1169.48|1.000|1163.07|1162.92|1.000|
|29|1209.81|1209.68|1.000|1202.86|1203.29|1.000|
|30|1250.92|1249.84|0.999|1244.14|1243.60|1.000|
|31|1291.39|1291.33|1.000|1284.66|1284.99|1.000|
|32|1331.35|1331.85|1.000|1324.64|1325.50|1.001|


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Chores**
* Updated the available warp-decode implementations. No user-facing
behavior changes are noted.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [2e1789d](https://github.com/flashinfer-ai/flashinfer/commit/2e1789dd0157d4e9c1ad05587070687e97d42264)

- **作者**: eigen
- **时间**: 2026-10-30T10:08:46Z
- **提交信息**: perf(cake_kimi_k3_fp8_projection): SM103a resident fused decode for TP8 f_b M 257..512 (#7992)

`flashinfer.gemm.kimi_k3_fp8_projection` (experimental, backend
`"cake"`) computes TP-local projection GEMMs. Cake ships one
data-type/layout variant of this kernel: row-major BF16 activations
quantized per token to E4M3 with 1x128 UE8M0 scales, E4M3 `[N, K]`
weights with 128x128 UE8M0 block scales, FP32 accumulation and BF16
output. This PR updates that variant. The baseline is the previous Cake
version, merged in #7715, which is current FlashInfer main.

What changes:
- sm_103a (GB300) only: TP8 f_b (N 1536, K 128) at M 257..512 now uses
the resident 32-token fused decode program with a TMA-store epilogue.
Row strides with padding use its register-epilogue twin. Previously this
shape range used the two-stage 64-token decode program plus a separate
quantization launch. No shape on sm_103a uses the two-stage 64-token
decode program anymore, so it is removed from the package. Affected
shape: TP8 f_b M = 512.
- sm_100a (B200): no route change.

On GB300, TP8 f_b M = 512 goes from 5.472 us to 4.640 us, a 1.179x
speedup (median of 16 paired interleaved rounds; per-round range
1.131-1.222). The other 197 shapes run the same GEMM, quantization and
decode machine code as FlashInfer main. Their ratios are run-to-run
variation: 0.992-1.012 (median 1.000), with 31 above and 41 below 1.000
at 3 decimals.

On B200, all 198 shapes run the same machine code as FlashInfer main.
Their ratios are run-to-run variation: 0.983-1.022 (median 1.000), with
18 above and 28 below 1.000 at 3 decimals. The lowest, TP8
in_proj_qkvgfab M = 16384 (0.983), and the highest, TP1 fused_qkvg M =
4096 (1.022), are run-to-run outliers. Their per-round ratios span
0.937-1.049 and 0.905-1.123.

NVIDIA B200 (sm_100a, driver 580.82.07) and NVIDIA GB300 (sm_103a,
driver 580.159.03), CUDA 13.4 on both. For each GPU, `main (us)` and `PR
(us)` are the median per-call latency in microseconds for FlashInfer
main and this PR. `speedup` is the median of per-round paired ratios
(FlashInfer main / this PR) over 10 to 16 interleaved rounds on the same
GPU, so it can differ from the ratio of the two medians.

| TP | projection | M | N | K | B200 main (us) | B200 PR (us) | B200
speedup | GB300 main (us) | GB300 PR (us) | GB300 speedup |
|---|---|--:|--:|--:|--:|--:|--:|--:|--:|--:|
| TP8 | q_proj | 1 | 1536 | 7168 | 7.648 | 7.632 | 1.000 | 7.232 | 7.248
| 1.000 |
| TP8 | q_proj | 8 | 1536 | 7168 | 7.904 | 7.888 | 1.000 | 7.472 | 7.480
| 1.000 |
| TP8 | q_proj | 64 | 1536 | 7168 | 9.376 | 9.376 | 1.000 | 9.032 |
9.056 | 0.999 |
| TP8 | q_proj | 256 | 1536 | 7168 | 13.136 | 13.144 | 1.000 | 12.608 |
12.608 | 1.001 |
| TP8 | q_proj | 4096 | 1536 | 7168 | 50.920 | 50.944 | 1.000 | 45.688 |
45.664 | 1.000 |
| TP8 | q_proj | 16384 | 1536 | 7168 | 170.655 | 170.775 | 1.000 |
164.520 | 164.191 | 1.001 |
| TP8 | fused_qkvg | 1 | 6144 | 7168 | 12.952 | 12.960 | 1.000 | 12.624
| 12.632 | 1.000 |
| TP8 | fused_qkvg | 8 | 6144 | 7168 | 13.160 | 13.136 | 1.001 | 12.744
| 12.752 | 1.000 |
| TP8 | fused_qkvg | 64 | 6144 | 7168 | 16.288 | 16.273 | 1.001 | 15.648
| 15.640 | 1.000 |
| TP8 | fused_qkvg | 256 | 6144 | 7168 | 19.840 | 19.880 | 0.999 |
18.456 | 18.368 | 1.001 |
| TP8 | fused_qkvg | 4096 | 6144 | 7168 | 122.112 | 122.176 | 1.000 |
115.440 | 115.360 | 1.002 |
| TP8 | fused_qkvg | 16384 | 6144 | 7168 | 508.188 | 509.316 | 0.998 |
456.209 | 456.400 | 1.000 |
| TP8 | in_proj_qkvgfab | 1 | 6284 | 7168 | 13.376 | 13.376 | 0.999 |
12.800 | 12.784 | 1.000 |
| TP8 | in_proj_qkvgfab | 8 | 6284 | 7168 | 13.384 | 13.408 | 1.000 |
12.968 | 12.944 | 1.000 |
| TP8 | in_proj_qkvgfab | 64 | 6284 | 7168 | 16.656 | 16.624 | 1.000 |
16.160 | 16.248 | 0.998 |
| TP8 | in_proj_qkvgfab | 256 | 6284 | 7168 | 20.576 | 20.592 | 1.000 |
19.296 | 19.344 | 1.000 |
| TP8 | in_proj_qkvgfab | 4096 | 6284 | 7168 | 127.896 | 128.000 | 1.000
| 118.824 | 118.935 | 0.999 |
| TP8 | in_proj_qkvgfab | 16384 | 6284 | 7168 | 551.373 | 555.309 |
0.983 | 470.273 | 468.775 | 1.003 |
| TP8 | f_a | 1 | 128 | 7168 | 5.064 | 5.088 | 1.000 | 4.904 | 4.904 |
1.000 |
| TP8 | f_a | 8 | 128 | 7168 | 5.792 | 5.800 | 1.000 | 5.760 | 5.760 |
1.000 |
| TP8 | f_a | 64 | 128 | 7168 | 6.496 | 6.496 | 1.000 | 6.128 | 6.112 |
1.000 |
| TP8 | f_a | 256 | 128 | 7168 | 7.824 | 7.808 | 1.000 | 7.104 | 7.104 |
1.000 |
| TP8 | f_a | 4096 | 128 | 7168 | 18.960 | 18.944 | 1.001 | 18.032 |
18.025 | 1.000 |
| TP8 | f_a | 16384 | 128 | 7168 | 48.432 | 48.432 | 0.999 | 47.624 |
47.656 | 1.000 |
| TP8 | f_b | 1 | 1536 | 128 | 3.920 | 3.904 | 1.000 | 3.760 | 3.768 |
1.000 |
| TP8 | f_b | 8 | 1536 | 128 | 3.985 | 4.000 | 1.000 | 3.872 | 3.872 |
1.000 |
| TP8 | f_b | 64 | 1536 | 128 | 4.064 | 4.064 | 1.000 | 3.936 | 3.936 |
1.000 |
| TP8 | f_b | 256 | 1536 | 128 | 4.320 | 4.320 | 1.000 | 4.160 | 4.160 |
1.000 |
| TP8 | f_b | 4096 | 1536 | 128 | 9.088 | 9.072 | 1.002 | 8.544 | 8.544
| 1.000 |
| TP8 | f_b | 16384 | 1536 | 128 | 16.880 | 16.912 | 1.000 | 16.000 |
16.032 | 0.997 |
| TP8 | b_proj | 1 | 12 | 7168 | 5.080 | 5.088 | 1.000 | 4.864 | 4.864 |
1.000 |
| TP8 | b_proj | 8 | 12 | 7168 | 5.839 | 5.840 | 1.000 | 5.328 | 5.320 |
1.000 |
| TP8 | b_proj | 64 | 12 | 7168 | 6.528 | 6.528 | 1.000 | 6.080 | 6.048
| 1.000 |
| TP8 | b_proj | 256 | 12 | 7168 | 7.744 | 7.760 | 1.000 | 7.232 | 7.232
| 1.000 |
| TP8 | b_proj | 4096 | 12 | 7168 | 19.232 | 19.232 | 1.000 | 17.856 |
17.872 | 1.000 |
| TP8 | b_proj | 16384 | 12 | 7168 | 48.991 | 48.975 | 1.001 | 47.696 |
47.696 | 1.000 |
| TP8 | kv_a | 1 | 576 | 7168 | 6.191 | 6.192 | 1.000 | 5.944 | 5.952 |
1.000 |
| TP8 | kv_a | 8 | 576 | 7168 | 6.527 | 6.496 | 1.000 | 6.192 | 6.176 |
1.000 |
| TP8 | kv_a | 64 | 576 | 7168 | 8.416 | 8.416 | 1.002 | 8.032 | 8.032 |
1.000 |
| TP8 | kv_a | 256 | 576 | 7168 | 10.912 | 10.864 | 1.001 | 10.208 |
10.176 | 1.000 |
| TP8 | kv_a | 4096 | 576 | 7168 | 35.040 | 35.040 | 1.000 | 32.032 |
32.032 | 1.000 |
| TP8 | kv_a | 16384 | 576 | 7168 | 109.295 | 109.319 | 1.000 | 103.584
| 103.664 | 1.000 |
| TP8 | fused_qkv_a | 1 | 2112 | 7168 | 8.576 | 8.560 | 1.000 | 8.352 |
8.320 | 1.002 |
| TP8 | fused_qkv_a | 8 | 2112 | 7168 | 8.776 | 8.768 | 1.000 | 8.392 |
8.400 | 1.000 |
| TP8 | fused_qkv_a | 64 | 2112 | 7168 | 11.759 | 11.760 | 0.999 |
11.744 | 11.728 | 1.000 |
| TP8 | fused_qkv_a | 256 | 2112 | 7168 | 13.696 | 13.744 | 0.999 |
13.000 | 13.016 | 0.999 |
| TP8 | fused_qkv_a | 4096 | 2112 | 7168 | 58.975 | 58.960 | 1.000 |
52.584 | 52.592 | 1.001 |
| TP8 | fused_qkv_a | 16384 | 2112 | 7168 | 220.927 | 220.952 | 1.000 |
201.440 | 201.432 | 1.000 |
| TP8 | q_b | 1 | 2304 | 1536 | 6.128 | 6.144 | 0.999 | 5.768 | 5.744 |
1.000 |
| TP8 | q_b | 8 | 2304 | 1536 | 5.952 | 5.952 | 1.000 | 5.632 | 5.632 |
1.000 |
| TP8 | q_b | 64 | 2304 | 1536 | 6.960 | 6.960 | 1.000 | 6.864 | 6.864 |
1.000 |
| TP8 | q_b | 256 | 2304 | 1536 | 7.408 | 7.392 | 1.004 | 7.072 | 7.120
| 0.999 |
| TP8 | q_b | 4096 | 2304 | 1536 | 20.128 | 20.143 | 1.000 | 18.432 |
18.432 | 1.000 |
| TP8 | q_b | 16384 | 2304 | 1536 | 56.496 | 56.480 | 1.000 | 51.040 |
51.056 | 1.000 |
| TP8 | kv_b | 1 | 3072 | 512 | 4.512 | 4.512 | 1.000 | 4.416 | 4.384 |
1.000 |
| TP8 | kv_b | 8 | 3072 | 512 | 4.480 | 4.480 | 1.000 | 4.288 | 4.288 |
1.000 |
| TP8 | kv_b | 64 | 3072 | 512 | 4.800 | 4.800 | 1.000 | 4.576 | 4.560 |
1.000 |
| TP8 | kv_b | 256 | 3072 | 512 | 6.143 | 6.128 | 1.000 | 5.952 | 5.952
| 1.000 |
| TP8 | kv_b | 4096 | 3072 | 512 | 14.368 | 14.368 | 1.000 | 13.704 |
13.720 | 1.000 |
| TP8 | kv_b | 16384 | 3072 | 512 | 33.728 | 33.728 | 1.001 | 30.304 |
30.320 | 1.000 |
| TP8 | o_proj | 1 | 7168 | 1536 | 7.007 | 7.008 | 1.000 | 6.800 | 6.784
| 1.000 |
| TP8 | o_proj | 8 | 7168 | 1536 | 7.136 | 7.144 | 1.000 | 6.848 | 6.832
| 1.000 |
| TP8 | o_proj | 64 | 7168 | 1536 | 8.416 | 8.416 | 1.000 | 7.888 |
7.872 | 1.001 |
| TP8 | o_proj | 256 | 7168 | 1536 | 9.377 | 9.392 | 1.000 | 9.504 |
9.536 | 1.000 |
| TP8 | o_proj | 4096 | 7168 | 1536 | 40.712 | 40.704 | 1.000 | 34.640 |
34.624 | 1.000 |
| TP8 | o_proj | 16384 | 7168 | 1536 | 134.512 | 134.623 | 1.000 |
123.864 | 123.760 | 1.000 |
| TP1 | q_proj | 1 | 12288 | 7168 | 19.616 | 19.568 | 1.000 | 18.952 |
18.944 | 1.001 |
| TP1 | q_proj | 8 | 12288 | 7168 | 19.440 | 19.424 | 1.000 | 18.672 |
18.704 | 1.001 |
| TP1 | q_proj | 64 | 12288 | 7168 | 21.552 | 21.584 | 0.999 | 21.104 |
21.120 | 0.999 |
| TP1 | q_proj | 256 | 12288 | 7168 | 25.872 | 25.856 | 1.001 | 24.544 |
24.528 | 1.001 |
| TP1 | q_proj | 4096 | 12288 | 7168 | 230.334 | 230.238 | 1.001 |
208.983 | 209.296 | 0.999 |
| TP1 | q_proj | 16384 | 12288 | 7168 | 1037.972 | 1018.500 | 0.999 |
833.392 | 833.480 | 1.001 |
| TP1 | fused_qkvg | 1 | 49152 | 7168 | 62.583 | 62.511 | 1.000 | 59.832
| 59.840 | 1.000 |
| TP1 | fused_qkvg | 8 | 49152 | 7168 | 67.016 | 67.000 | 1.000 | 64.896
| 64.904 | 0.999 |
| TP1 | fused_qkvg | 64 | 49152 | 7168 | 63.719 | 63.743 | 0.999 |
62.400 | 62.384 | 1.000 |
| TP1 | fused_qkvg | 256 | 49152 | 7168 | 76.672 | 76.680 | 0.999 |
73.560 | 73.472 | 1.001 |
| TP1 | fused_qkvg | 4096 | 49152 | 7168 | 951.889 | 913.697 | 1.022 |
807.912 | 795.792 | 1.012 |
| TP1 | fused_qkvg | 16384 | 49152 | 7168 | 4177.629 | 4195.900 | 1.000
| 3477.736 | 3471.568 | 1.002 |
| TP1 | in_proj_qkvgfab | 1 | 49376 | 7168 | 62.712 | 62.664 | 1.000 |
60.432 | 60.432 | 0.999 |
| TP1 | in_proj_qkvgfab | 8 | 49376 | 7168 | 67.896 | 67.912 | 1.000 |
64.688 | 64.672 | 0.999 |
| TP1 | in_proj_qkvgfab | 64 | 49376 | 7168 | 64.520 | 64.559 | 0.999 |
62.896 | 62.904 | 1.000 |
| TP1 | in_proj_qkvgfab | 256 | 49376 | 7168 | 77.120 | 77.215 | 0.999 |
74.088 | 74.112 | 1.000 |
| TP1 | in_proj_qkvgfab | 4096 | 49376 | 7168 | 968.420 | 1015.303 |
0.989 | 798.016 | 802.408 | 0.992 |
| TP1 | in_proj_qkvgfab | 16384 | 49376 | 7168 | 4310.479 | 4321.247 |
0.998 | 3542.440 | 3542.352 | 0.999 |
| TP1 | f_a | 1 | 128 | 7168 | 5.072 | 5.072 | 1.000 | 4.848 | 4.832 |
1.000 |
| TP1 | f_a | 8 | 128 | 7168 | 5.792 | 5.776 | 1.000 | 5.344 | 5.336 |
1.000 |
| TP1 | f_a | 64 | 128 | 7168 | 6.528 | 6.528 | 1.000 | 6.088 | 6.080 |
1.000 |
| TP1 | f_a | 256 | 128 | 7168 | 7.808 | 7.808 | 0.999 | 7.152 | 7.160 |
1.000 |
| TP1 | f_a | 4096 | 128 | 7168 | 18.960 | 18.953 | 1.000 | 18.008 |
18.008 | 1.000 |
| TP1 | f_a | 16384 | 128 | 7168 | 48.808 | 48.792 | 1.000 | 47.648 |
47.696 | 1.000 |
| TP1 | f_b | 1 | 12288 | 128 | 4.656 | 4.656 | 1.000 | 4.400 | 4.416 |
1.000 |
| TP1 | f_b | 8 | 12288 | 128 | 4.688 | 4.688 | 1.000 | 4.544 | 4.544 |
1.000 |
| TP1 | f_b | 64 | 12288 | 128 | 5.088 | 5.087 | 1.000 | 4.960 | 4.952 |
1.000 |
| TP1 | f_b | 256 | 12288 | 128 | 6.672 | 6.656 | 1.002 | 6.352 | 6.344
| 1.003 |
| TP1 | f_b | 4096 | 12288 | 128 | 23.888 | 23.880 | 1.001 | 22.368 |
22.328 | 1.000 |
| TP1 | f_b | 16384 | 12288 | 128 | 76.616 | 76.583 | 1.000 | 69.544 |
69.632 | 0.999 |
| TP1 | b_proj | 1 | 96 | 7168 | 5.216 | 5.216 | 1.000 | 4.976 | 4.960 |
1.000 |
| TP1 | b_proj | 8 | 96 | 7168 | 5.888 | 5.887 | 1.000 | 5.568 | 5.568 |
1.000 |
| TP1 | b_proj | 64 | 96 | 7168 | 6.464 | 6.480 | 1.000 | 6.240 | 6.224
| 1.000 |
| TP1 | b_proj | 256 | 96 | 7168 | 7.824 | 7.839 | 1.000 | 7.168 | 7.168
| 1.000 |
| TP1 | b_proj | 4096 | 96 | 7168 | 18.904 | 18.936 | 1.000 | 17.920 |
17.928 | 0.999 |
| TP1 | b_proj | 16384 | 96 | 7168 | 48.400 | 48.440 | 0.999 | 47.544 |
47.520 | 0.999 |
| TP1 | kv_a | 1 | 576 | 7168 | 6.176 | 6.176 | 1.000 | 5.888 | 5.888 |
1.000 |
| TP1 | kv_a | 8 | 576 | 7168 | 6.520 | 6.528 | 1.000 | 6.160 | 6.160 |
1.000 |
| TP1 | kv_a | 64 | 576 | 7168 | 8.440 | 8.399 | 1.000 | 7.984 | 7.968 |
1.000 |
| TP1 | kv_a | 256 | 576 | 7168 | 10.744 | 10.728 | 1.000 | 10.200 |
10.208 | 0.998 |
| TP1 | kv_a | 4096 | 576 | 7168 | 35.056 | 35.040 | 1.000 | 32.032 |
32.016 | 1.000 |
| TP1 | kv_a | 16384 | 576 | 7168 | 109.616 | 109.648 | 1.000 | 103.464
| 103.392 | 1.000 |
| TP1 | fused_qkv_a | 1 | 2112 | 7168 | 8.512 | 8.544 | 1.000 | 8.416 |
8.416 | 1.000 |
| TP1 | fused_qkv_a | 8 | 2112 | 7168 | 8.784 | 8.800 | 1.000 | 8.328 |
8.320 | 1.003 |
| TP1 | fused_qkv_a | 64 | 2112 | 7168 | 12.008 | 11.983 | 1.000 |
11.768 | 11.792 | 1.001 |
| TP1 | fused_qkv_a | 256 | 2112 | 7168 | 13.760 | 13.800 | 1.000 |
13.024 | 12.968 | 1.001 |
| TP1 | fused_qkv_a | 4096 | 2112 | 7168 | 58.976 | 58.976 | 1.000 |
52.672 | 52.688 | 0.999 |
| TP1 | fused_qkv_a | 16384 | 2112 | 7168 | 218.423 | 218.768 | 1.000 |
200.488 | 200.496 | 1.000 |
| TP1 | q_b | 1 | 18432 | 1536 | 9.472 | 9.472 | 1.000 | 9.248 | 9.248 |
1.000 |
| TP1 | q_b | 8 | 18432 | 1536 | 9.568 | 9.568 | 1.000 | 9.216 | 9.200 |
1.000 |
| TP1 | q_b | 64 | 18432 | 1536 | 11.280 | 11.296 | 1.000 | 10.592 |
10.576 | 1.000 |
| TP1 | q_b | 256 | 18432 | 1536 | 14.368 | 14.399 | 1.000 | 13.536 |
13.536 | 1.000 |
| TP1 | q_b | 4096 | 18432 | 1536 | 83.168 | 83.208 | 1.000 | 75.168 |
75.200 | 0.999 |
| TP1 | q_b | 16384 | 18432 | 1536 | 340.999 | 341.071 | 1.000 | 287.968
| 287.136 | 1.002 |
| TP1 | kv_b | 1 | 24576 | 512 | 7.320 | 7.344 | 0.999 | 7.056 | 7.080 |
1.000 |
| TP1 | kv_b | 8 | 24576 | 512 | 7.280 | 7.280 | 1.000 | 6.968 | 6.968 |
1.000 |
| TP1 | kv_b | 64 | 24576 | 512 | 9.080 | 9.080 | 1.000 | 8.704 | 8.704
| 1.000 |
| TP1 | kv_b | 256 | 24576 | 512 | 11.456 | 11.456 | 0.999 | 10.752 |
10.736 | 0.999 |
| TP1 | kv_b | 4096 | 24576 | 512 | 51.816 | 51.935 | 0.998 | 49.368 |
49.344 | 1.000 |
| TP1 | kv_b | 16384 | 24576 | 512 | 183.678 | 183.615 | 1.000 | 170.664
| 170.624 | 1.000 |
| TP1 | o_proj | 1 | 7168 | 12288 | 20.104 | 20.128 | 1.000 | 19.584 |
19.584 | 0.999 |
| TP1 | o_proj | 8 | 7168 | 12288 | 20.176 | 20.160 | 1.000 | 19.456 |
19.472 | 1.000 |
| TP1 | o_proj | 64 | 7168 | 12288 | 24.064 | 24.088 | 1.000 | 22.912 |
22.952 | 0.999 |
| TP1 | o_proj | 256 | 7168 | 12288 | 29.416 | 29.424 | 1.000 | 26.288 |
26.272 | 0.999 |
| TP1 | o_proj | 4096 | 7168 | 12288 | 251.111 | 251.310 | 0.999 |
221.008 | 220.584 | 1.000 |
| TP1 | o_proj | 16384 | 7168 | 12288 | 1074.562 | 1077.514 | 0.999 |
898.000 | 898.616 | 1.001 |
| TP8 | q_proj | 512 | 1536 | 7168 | 16.176 | 16.176 | 1.000 | 14.912 |
14.912 | 1.000 |
| TP8 | q_proj | 1024 | 1536 | 7168 | 21.152 | 21.152 | 1.000 | 19.808 |
19.824 | 0.999 |
| TP8 | q_proj | 2048 | 1536 | 7168 | 29.408 | 29.408 | 1.000 | 26.432 |
26.433 | 1.000 |
| TP8 | fused_qkvg | 512 | 6144 | 7168 | 24.952 | 24.944 | 0.999 |
22.560 | 22.600 | 0.999 |
| TP8 | fused_qkvg | 1024 | 6144 | 7168 | 40.416 | 40.416 | 1.000 |
36.064 | 36.048 | 1.000 |
| TP8 | fused_qkvg | 2048 | 6144 | 7168 | 66.016 | 65.944 | 1.000 |
58.432 | 58.424 | 1.000 |
| TP8 | in_proj_qkvgfab | 512 | 6284 | 7168 | 25.343 | 25.344 | 1.000 |
25.544 | 25.536 | 1.000 |
| TP8 | in_proj_qkvgfab | 1024 | 6284 | 7168 | 42.240 | 42.240 | 1.000 |
37.999 | 37.976 | 1.000 |
| TP8 | in_proj_qkvgfab | 2048 | 6284 | 7168 | 69.856 | 69.872 | 1.000 |
62.128 | 62.288 | 0.999 |
| TP8 | f_a | 512 | 128 | 7168 | 10.912 | 10.912 | 1.000 | 10.512 |
10.512 | 1.000 |
| TP8 | f_a | 1024 | 128 | 7168 | 12.880 | 12.880 | 1.000 | 11.584 |
11.584 | 1.000 |
| TP8 | f_a | 2048 | 128 | 7168 | 14.416 | 14.416 | 1.000 | 13.456 |
13.448 | 1.000 |
| TP8 | f_b | 512 | 1536 | 128 | 5.024 | 5.024 | 1.000 | 5.472 | 4.640 |
1.179 |
| TP8 | f_b | 1024 | 1536 | 128 | 6.176 | 6.175 | 1.000 | 5.952 | 5.976
| 1.000 |
| TP8 | f_b | 2048 | 1536 | 128 | 7.776 | 7.776 | 1.000 | 7.584 | 7.584
| 1.000 |
| TP8 | b_proj | 512 | 12 | 7168 | 10.912 | 10.928 | 0.999 | 10.528 |
10.560 | 0.999 |
| TP8 | b_proj | 1024 | 12 | 7168 | 12.831 | 12.832 | 1.000 | 11.584 |
11.584 | 0.999 |
| TP8 | b_proj | 2048 | 12 | 7168 | 14.432 | 14.432 | 1.000 | 13.584 |
13.576 | 1.000 |
| TP8 | kv_a | 512 | 576 | 7168 | 13.312 | 13.344 | 1.000 | 12.640 |
12.624 | 1.000 |
| TP8 | kv_a | 1024 | 576 | 7168 | 17.024 | 17.024 | 1.000 | 16.224 |
16.224 | 1.001 |
| TP8 | kv_a | 2048 | 576 | 7168 | 23.840 | 23.840 | 1.000 | 22.432 |
22.400 | 1.000 |
| TP8 | fused_qkv_a | 512 | 2112 | 7168 | 16.576 | 16.576 | 1.000 |
15.288 | 15.296 | 1.000 |
| TP8 | fused_qkv_a | 1024 | 2112 | 7168 | 21.904 | 21.920 | 1.000 |
20.992 | 20.976 | 1.002 |
| TP8 | fused_qkv_a | 2048 | 2112 | 7168 | 33.760 | 33.752 | 1.000 |
30.688 | 30.720 | 0.999 |
| TP8 | q_b | 512 | 2304 | 1536 | 7.952 | 7.952 | 1.000 | 7.656 | 7.632
| 1.000 |
| TP8 | q_b | 1024 | 2304 | 1536 | 9.584 | 9.568 | 1.000 | 9.056 | 9.040
| 0.999 |
| TP8 | q_b | 2048 | 2304 | 1536 | 13.344 | 13.344 | 1.000 | 12.960 |
12.944 | 1.001 |
| TP8 | kv_b | 512 | 3072 | 512 | 6.832 | 6.824 | 1.000 | 6.416 | 6.400
| 1.000 |
| TP8 | kv_b | 1024 | 3072 | 512 | 8.736 | 8.736 | 1.001 | 8.400 | 8.400
| 1.000 |
| TP8 | kv_b | 2048 | 3072 | 512 | 10.656 | 10.656 | 1.000 | 9.984 |
9.952 | 1.001 |
| TP8 | o_proj | 512 | 7168 | 1536 | 12.640 | 12.640 | 1.000 | 11.592 |
11.592 | 0.999 |
| TP8 | o_proj | 1024 | 7168 | 1536 | 17.472 | 17.472 | 1.000 | 15.280 |
15.336 | 1.000 |
| TP8 | o_proj | 2048 | 7168 | 1536 | 26.032 | 26.000 | 1.000 | 21.184 |
21.184 | 1.000 |
| TP1 | q_proj | 512 | 12288 | 7168 | 40.376 | 40.400 | 0.999 | 38.256 |
38.208 | 1.000 |
| TP1 | q_proj | 1024 | 12288 | 7168 | 64.927 | 64.896 | 1.000 | 59.688
| 59.656 | 0.999 |
| TP1 | q_proj | 2048 | 12288 | 7168 | 114.415 | 114.448 | 1.000 |
107.080 | 107.056 | 1.000 |
| TP1 | fused_qkvg | 512 | 49152 | 7168 | 121.440 | 121.583 | 1.000 |
115.896 | 116.239 | 1.000 |
| TP1 | fused_qkvg | 1024 | 49152 | 7168 | 231.231 | 231.414 | 0.999 |
211.320 | 211.936 | 0.997 |
| TP1 | fused_qkvg | 2048 | 49152 | 7168 | 455.868 | 455.237 | 1.000 |
406.960 | 406.544 | 1.002 |
| TP1 | in_proj_qkvgfab | 512 | 49376 | 7168 | 118.439 | 118.543 | 1.000
| 115.888 | 115.695 | 1.001 |
| TP1 | in_proj_qkvgfab | 1024 | 49376 | 7168 | 242.135 | 242.792 |
1.000 | 212.936 | 213.288 | 0.998 |
| TP1 | in_proj_qkvgfab | 2048 | 49376 | 7168 | 469.344 | 468.688 |
1.004 | 404.416 | 406.144 | 0.998 |
| TP1 | f_a | 512 | 128 | 7168 | 10.880 | 10.880 | 1.000 | 10.464 |
10.464 | 1.000 |
| TP1 | f_a | 1024 | 128 | 7168 | 12.896 | 12.896 | 1.000 | 11.552 |
11.568 | 0.999 |
| TP1 | f_a | 2048 | 128 | 7168 | 14.400 | 14.400 | 1.000 | 13.432 |
13.440 | 0.999 |
| TP1 | f_b | 512 | 12288 | 128 | 9.480 | 9.488 | 0.998 | 8.800 | 8.785
| 1.000 |
| TP1 | f_b | 1024 | 12288 | 128 | 11.696 | 11.680 | 1.001 | 10.944 |
10.944 | 1.000 |
| TP1 | f_b | 2048 | 12288 | 128 | 15.792 | 15.824 | 1.000 | 14.464 |
14.432 | 1.002 |
| TP1 | b_proj | 512 | 96 | 7168 | 10.888 | 10.896 | 1.000 | 10.432 |
10.432 | 1.002 |
| TP1 | b_proj | 1024 | 96 | 7168 | 12.864 | 12.840 | 1.000 | 11.496 |
11.520 | 0.998 |
| TP1 | b_proj | 2048 | 96 | 7168 | 14.384 | 14.384 | 1.000 | 13.472 |
13.496 | 1.000 |
| TP1 | kv_a | 512 | 576 | 7168 | 13.256 | 13.280 | 1.000 | 12.624 |
12.608 | 1.000 |
| TP1 | kv_a | 1024 | 576 | 7168 | 16.992 | 16.991 | 1.000 | 16.240 |
16.240 | 1.000 |
| TP1 | kv_a | 2048 | 576 | 7168 | 23.792 | 23.839 | 1.000 | 22.448 |
22.432 | 1.000 |
| TP1 | fused_qkv_a | 512 | 2112 | 7168 | 16.608 | 16.608 | 1.000 |
15.280 | 15.312 | 1.000 |
| TP1 | fused_qkv_a | 1024 | 2112 | 7168 | 22.056 | 22.095 | 1.000 |
20.976 | 20.976 | 1.000 |
| TP1 | fused_qkv_a | 2048 | 2112 | 7168 | 34.008 | 34.032 | 1.000 |
31.104 | 31.112 | 1.000 |
| TP1 | q_b | 512 | 18432 | 1536 | 18.320 | 18.336 | 1.000 | 17.120 |
17.128 | 1.000 |
| TP1 | q_b | 1024 | 18432 | 1536 | 27.296 | 27.296 | 1.000 | 24.800 |
24.832 | 0.999 |
| TP1 | q_b | 2048 | 18432 | 1536 | 46.560 | 46.575 | 1.000 | 42.048 |
42.080 | 0.999 |
| TP1 | kv_b | 512 | 24576 | 512 | 14.344 | 14.304 | 1.000 | 13.584 |
13.600 | 1.000 |
| TP1 | kv_b | 1024 | 24576 | 512 | 19.872 | 19.872 | 1.000 | 18.720 |
18.720 | 1.000 |
| TP1 | kv_b | 2048 | 24576 | 512 | 30.840 | 30.895 | 1.000 | 28.872 |
28.896 | 1.001 |
| TP1 | o_proj | 512 | 7168 | 12288 | 39.824 | 39.856 | 1.000 | 34.288 |
34.384 | 1.000 |
| TP1 | o_proj | 1024 | 7168 | 12288 | 66.623 | 66.623 | 1.000 | 57.336
| 57.208 | 1.004 |
| TP1 | o_proj | 2048 | 7168 | 12288 | 119.856 | 119.744 | 1.001 |
108.696 | 108.984 | 0.998 |

Cake ships no other data-type, layout or fused variant of this kernel;
the family ships on sm_100a and sm_103a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* Updated a GPU decode configuration to use a fused, persistent route
with smaller token tiles and TMA-based output stores.
* **Bug Fixes**
  * Expanded projection output coverage for affected workloads.
* **Tests**
* Updated GPU dispatch expectations for the revised decode
configuration.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Avery Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [ec856af](https://github.com/flashinfer-ai/flashinfer/commit/ec856af63624f38457860d0c85b710cfefdd2848)

- **作者**: eigen
- **时间**: 2026-10-30T09:55:42Z
- **提交信息**: perf(cake_deepgemm_mega_mhc): speed up sm_107a NVFP4 and FP8 group-128 raw-scale programs (#7994)

`flashinfer.mega_mhc` (`prepare_mega_mhc`) runs the fused
manifold-constrained hyper-connection (mHC) inference step. FlashInfer
main ships 36 programs for it:

- 14 hidden-5120 FP8-E4M3-output programs on sm_100a and sm_103a.
- For hidden 4096, five programs on each of sm_107a, sm_100a and
sm_103a: BF16 output, its tailpipe twin, its weight-staging tailpipe
twin, FP8 group-128 output and NVFP4 output.
- Four sm_107a-only tailpipe and weight-staging tailpipe forms of the
FP8 group-128 and NVFP4 variants.
- Three sm_107a-only FP8 group-128 UE8M0-scale-mode programs (plain,
tailpipe and weight-staging tailpipe).

This PR changes two of the existing sm_107a programs. It adds no program
and does not change the loader, so main still ships 36.

- **NVFP4 output** (`sf_layout="nvfp4"`): The PR changes the plain
sm_107a program, which serves T ≤ 832 on both 208 and 216 SMs (T = 1–512
in the tables below). The tailpipe forms that serve larger T are
unchanged, so the T ≥ 1024 rows run the same program on both sides.
- **FP8 group-128 output, raw scale mode** (`sf_layout="fp8_group128"`,
`fp8_sf_ue8m0=False`): The PR changes the sm_107a tailpipe program,
which serves T = 385–832 and T = 1281–3328 on 208 SMs, and T = 385–832
and T = 1345–3456 on 216 SMs. In the tables below, that covers T = 512
and T = 2048. The other rows run unchanged programs on both sides.

Both programs now compute the mixing-coefficient chain with a fast,
correctly rounded division. A range check guards it and falls back to
IEEE division. Outputs are bitwise identical to main.

The baseline is the previous Cake version of the kernel, which is what
FlashInfer main dispatches today. A is the program main dispatches, and
B is the program this PR dispatches. Speedup = A / B. Both sides run
through FlashInfer's loader on the same GPU with the same inputs in one
process, and both use programmatic dependent launch, as main already
does. The tables show medians.

- NVFP4, T = 1–512: 1.027–1.048× on the 208-SM GPU, 1.028–1.049× on the
216-SM GPU.
- FP8 group-128 raw, T = 512: 1.018× on the 208-SM GPU, 1.021× on the
216-SM GPU.
- FP8 group-128 raw, T = 2048: 1.009× on the 208-SM GPU, 1.008× on the
216-SM GPU.

Rows served by unchanged programs read about 1.00× (0.997–1.002×).

**NVFP4 output, hidden 4096. NVIDIA R200 (sm_107a), 208 SMs, driver
615.71.10, CUDA 13.4 (nvcc 13.4.92), SM clock 2326–2362 MHz.**

| T (tokens) | Program dispatched | Splits | Previous program, µs (A) |
This PR, µs (B) | Speedup (A / B) |
|---:|:--|---:|---:|---:|---:|
| 1 | NVFP4 | 64 | 9.056 | 8.640 | 1.048× |
| 4 | NVFP4 | 64 | 9.344 | 8.928 | 1.047× |
| 8 | NVFP4 | 64 | 9.296 | 8.880 | 1.047× |
| 16 | NVFP4 | 64 | 9.567 | 9.152 | 1.045× |
| 32 | NVFP4 | 64 | 9.568 | 9.152 | 1.045× |
| 64 | NVFP4 | 64 | 9.920 | 9.472 | 1.047× |
| 128 | NVFP4 | 64 | 10.720 | 10.288 | 1.042× |
| 256 | NVFP4 | 32 | 12.160 | 11.752 | 1.035× |
| 512 | NVFP4 | 22 | 14.688 | 14.304 | 1.027× |
| 1024 | tailpipe | 13 | 18.936 | 18.904 | 1.002× |
| 2048 | tailpipe | 13 | 29.352 | 29.376 | 0.999× |
| 4096 | tailpipe (weight staged) | 16 | 55.800 | 55.856 | 0.999× |
| 8192 | tailpipe (weight staged) | 8 | 110.817 | 110.816 | 1.000× |

**NVFP4 output, hidden 4096. NVIDIA R200 (sm_107a), 216 SMs, driver
615.71.10, CUDA 13.4 (nvcc 13.4.92), SM clock 2379–2412 MHz.**

| T (tokens) | Program dispatched | Splits | Previous program, µs (A) |
This PR, µs (B) | Speedup (A / B) |
|---:|:--|---:|---:|---:|---:|
| 1 | NVFP4 | 64 | 8.864 | 8.448 | 1.049× |
| 4 | NVFP4 | 64 | 9.024 | 8.616 | 1.047× |
| 8 | NVFP4 | 64 | 9.096 | 8.704 | 1.045× |
| 16 | NVFP4 | 64 | 9.280 | 8.864 | 1.047× |
| 32 | NVFP4 | 64 | 9.448 | 9.056 | 1.043× |
| 64 | NVFP4 | 64 | 9.824 | 9.408 | 1.044× |
| 128 | NVFP4 | 64 | 10.336 | 9.920 | 1.042× |
| 256 | NVFP4 | 32 | 12.024 | 11.616 | 1.035× |
| 512 | NVFP4 | 22 | 14.336 | 13.952 | 1.028× |
| 1024 | tailpipe | 13 | 18.112 | 18.144 | 0.998× |
| 2048 | tailpipe | 13 | 28.032 | 28.048 | 0.999× |
| 4096 | tailpipe (weight staged) | 16 | 53.376 | 53.352 | 1.000× |
| 8192 | tailpipe (weight staged) | 8 | 107.784 | 107.744 | 1.000× |

**FP8 group-128 output, raw scale mode, hidden 4096. NVIDIA R200
(sm_107a), 208 SMs, driver 615.71.10, CUDA 13.4 (nvcc 13.4.92), SM clock
2329–2362 MHz.**

| T (tokens) | Program dispatched | Splits | Previous program, µs (A) |
This PR, µs (B) | Speedup (A / B) |
|---:|:--|---:|---:|---:|---:|
| 1 | FP8 group-128 | 64 | 10.048 | 10.040 | 1.001× |
| 4 | FP8 group-128 | 64 | 10.160 | 10.160 | 1.000× |
| 8 | FP8 group-128 | 64 | 10.264 | 10.272 | 0.999× |
| 16 | FP8 group-128 | 64 | 9.792 | 9.776 | 1.002× |
| 32 | FP8 group-128 | 64 | 9.888 | 9.888 | 1.000× |
| 64 | FP8 group-128 | 64 | 10.400 | 10.400 | 1.000× |
| 128 | FP8 group-128 | 64 | 10.953 | 10.952 | 1.000× |
| 256 | FP8 group-128 | 32 | 12.320 | 12.320 | 1.000× |
| 512 | tailpipe | 22 | 14.600 | 14.336 | 1.018× |
| 1024 | FP8 group-128 | 13 | 21.736 | 21.720 | 1.001× |
| 2048 | tailpipe | 13 | 31.968 | 31.680 | 1.009× |
| 4096 | tailpipe (weight staged) | 16 | 61.072 | 60.992 | 1.001× |
| 8192 | tailpipe (weight staged) | 8 | 117.449 | 117.448 | 1.000× |

**FP8 group-128 output, raw scale mode, hidden 4096. NVIDIA R200
(sm_107a), 216 SMs, driver 615.71.10, CUDA 13.4 (nvcc 13.4.92), SM clock
2385–2413 MHz.**

| T (tokens) | Program dispatched | Splits | Previous program, µs (A) |
This PR, µs (B) | Speedup (A / B) |
|---:|:--|---:|---:|---:|---:|
| 1 | FP8 group-128 | 64 | 9.880 | 9.888 | 0.999× |
| 4 | FP8 group-128 | 64 | 9.832 | 9.824 | 1.001× |
| 8 | FP8 group-128 | 64 | 10.104 | 10.112 | 0.999× |
| 16 | FP8 group-128 | 64 | 9.600 | 9.608 | 0.999× |
| 32 | FP8 group-128 | 64 | 9.784 | 9.760 | 1.002× |
| 64 | FP8 group-128 | 64 | 10.080 | 10.072 | 1.001× |
| 128 | FP8 group-128 | 64 | 10.720 | 10.736 | 0.999× |
| 256 | FP8 group-128 | 32 | 12.096 | 12.096 | 1.000× |
| 512 | tailpipe | 22 | 14.304 | 14.016 | 1.021× |
| 1024 | FP8 group-128 | 13 | 20.816 | 20.888 | 0.997× |
| 2048 | tailpipe | 13 | 30.784 | 30.528 | 1.008× |
| 4096 | tailpipe (weight staged) | 16 | 58.400 | 58.344 | 1.001× |
| 8192 | tailpipe (weight staged) | 8 | 114.944 | 114.976 | 1.000× |

The kernel's other Cake variants (BF16 output, the FP8 group-128 UE8M0
scale mode, the hidden-5120 programs and all sm_100a and sm_103a
programs) compile to the same machine code as on main, and the family
ships on sm_107a, sm_100a and sm_103a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Tests**
* Added stream synchronization checks after replay and validation work
in the experimental CUDA tests.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Avery Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [81d96fe](https://github.com/flashinfer-ai/flashinfer/commit/81d96fe8daf148c453fc328a1f049b504f754c5a)

- **作者**: eigen
- **时间**: 2026-10-30T09:44:49Z
- **提交信息**: perf(cake_minimax_h3_varlen_attention): B200 two-stream NVFP4 two-launch schedules (#7991)

`cake_minimax_h3_varlen_attention` is the MiniMax-H3 packed-varlen
attention kernel. It has a BF16 variant and two NVFP4 variants: `fp4pv`
uses fp4 P·V and `fp8pv` uses fp8 P·V. This PR changes only the B200
(sm_100a) NVFP4 schedules that use two launches, the tail-first and
tail-grid plans. These used to run their launches one after another on
the caller's stream. They now use two streams, so the second quantizer
or attention part overlaps the first. Outputs are bitwise unchanged, and
the BF16 and one-launch NVFP4 plans keep their existing launch. The
baseline is the previous Cake version, which is current FlashInfer main.
Every two-stream row is faster in both runs: the `fp4pv` tail-grid rows
by 1.0017–1.0080, the `fp4pv` tail-first rows by 1.0225–1.0254 and the
`fp8pv` tail-first rows by 1.0198–1.0238.

**NVIDIA B200 (sm_100a, 148 SMs), CUDA 13.0 (torch 2.14.1+cu130).**
Latency is in µs per call with a cold L2. The table has two independent
runs on different B200 GPUs, each with FI main and this PR interleaved
A/B in the same session. Speedup = FI main / this PR (> 1 means this PR
is faster). It is the median of per-group medians, so it can differ from
the ratio of the two pooled absolute medians shown. `c` marks a value
clock-corrected for a GPU clock difference between the arms. Only
`two-stream` rows run different launch code. `unchanged` rows (BF16 and
one-launch NVFP4) run identical launches in both arms, so their spread
(about ±2 % on power-limited BF16 rows) is measurement noise.

| shape | mode | launch | run 1 FI main (µs) | run 1 this PR (µs) | run
1 speedup | run 2 FI main (µs) | run 2 this PR (µs) | run 2 speedup |
|---|---|---|---|---|---|---|---|---|
| center_4s_p1_m33472 | fp4pv | two-stream | 16125.4 | 16058.9 | 1.0041
| 16176.0 | 16048.6 | 1.0080 |
| center_4s_p1_m33472 | fp8pv | unchanged | 16452.1 | 16413.9 | 1.0003 c
| 16608.3 | 16650.2 | 0.9968 c |
| center_4s_p2_m16736 | fp4pv | two-stream | 2147.2 | 2142.7 | 1.0021 |
2152.8 | 2148.4 | 1.0021 |
| center_4s_p2_m16736 | fp8pv | unchanged | 2159.9 | 2160.1 | 0.9999 |
2166.7 | 2166.8 | 0.9999 |
| center_5s_p8_m4824 | fp4pv | unchanged | 65.6 | 65.6 | 1.0005 | 65.9 |
65.8 | 1.0005 |
| center_5s_p8_m4824 | fp8pv | unchanged | 65.6 | 65.6 | 1.0000 | 65.6 |
65.6 | 1.0000 |
| center_6s_p1_m48768 | fp4pv | two-stream | 33704.0 | 33618.0 | 1.0027
| 33791.4 | 33629.4 | 1.0047 |
| center_6s_p1_m48768 | fp8pv | unchanged | 34931.8 | 34988.6 | 1.0000 |
35287.6 | 35349.8 | 0.9992 |
| center_6s_p2_m24384 | fp4pv | two-stream | 4476.1 | 4365.8 | 1.0254 |
4486.1 | 4377.1 | 1.0250 |
| center_6s_p2_m24384 | fp8pv | two-stream | 4496.9 | 4392.6 | 1.0235 |
4508.1 | 4403.3 | 1.0238 |
| center_8s_p4_m14736 | fp4pv | unchanged | 878.8 | 879.0 | 0.9999 |
879.9 | 879.9 | 0.9999 |
| center_8s_p4_m14736 | fp8pv | unchanged | 891.2 | 891.3 | 0.9998 |
894.4 | 894.6 | 0.9997 |
| center_10s_p8_m9280 | fp4pv | unchanged | 213.7 | 213.6 | 1.0001 |
214.5 | 214.5 | 1.0000 |
| center_10s_p8_m9280 | fp8pv | unchanged | 211.6 | 211.5 | 1.0000 |
213.6 | 213.6 | 1.0000 |
| center_15s_p1_m109952 | fp4pv | two-stream | 168524.4 | 168109.3 |
1.0024 | 168919.7 | 168281.4 | 1.0038 |
| center_15s_p1_m109952 | fp8pv | unchanged | 176337.2 | 176112.8 |
1.0015 | 177466.3 | 177853.0 | 0.9989 |
| center_15s_p4_m27488 | fp4pv | two-stream | 2888.5 | 2824.7 | 1.0226 |
2894.5 | 2831.0 | 1.0225 |
| center_15s_p4_m27488 | fp8pv | two-stream | 2908.1 | 2851.5 | 1.0198 |
2912.5 | 2851.9 | 1.0213 |
| tail_5s_p2_m19235 | fp4pv | two-stream | 2828.1 | 2818.7 | 1.0033 |
2834.5 | 2821.9 | 1.0045 |
| tail_5s_p2_m19235 | fp8pv | unchanged | 2842.2 | 2841.7 | 1.0002 |
2847.3 | 2847.5 | 0.9999 |
| tail_5s_p4_m9685 | fp4pv | unchanged | 418.9 | 418.9 | 1.0000 | 421.1
| 421.0 | 1.0001 |
| tail_5s_p4_m9685 | fp8pv | unchanged | 414.4 | 414.5 | 1.0000 | 417.1
| 417.1 | 0.9999 |
| center_4s_p8_m4184 | fp4pv | unchanged | 58.0 | 58.0 | 1.0000 | 57.8 |
57.8 | 1.0000 |
| center_4s_p8_m4184 | fp8pv | unchanged | 59.1 | 59.1 | 1.0000 | 57.3 |
57.4 | 1.0000 |
| center_5s_p2_m19296 | fp4pv | two-stream | 2831.2 | 2821.3 | 1.0035 |
2823.5 | 2814.5 | 1.0031 |
| center_5s_p2_m19296 | fp8pv | unchanged | 2845.1 | 2845.2 | 1.0000 |
2838.0 | 2837.3 | 1.0002 |
| center_6s_p4_m12192 | fp4pv | unchanged | 653.8 | 653.8 | 1.0000 |
652.2 | 652.3 | 1.0000 |
| center_6s_p4_m12192 | fp8pv | unchanged | 655.5 | 655.5 | 1.0000 |
649.5 | 649.6 | 0.9999 |
| center_8s_p1_m58944 | fp4pv | two-stream | 49247.5 | 48999.7 | 1.0051
| 49238.6 | 49004.3 | 1.0048 |
| center_8s_p1_m58944 | fp8pv | unchanged | 52050.8 | 52068.9 | 0.9996 |
51656.4 | 51721.3 | 0.9967 c |
| center_8s_p8_m7368 | fp4pv | unchanged | 145.8 | 145.8 | 1.0002 |
145.3 | 145.3 | 1.0000 |
| center_8s_p8_m7368 | fp8pv | unchanged | 144.0 | 144.0 | 1.0000 |
141.9 | 141.9 | 1.0002 |
| center_10s_p4_m18560 | fp4pv | two-stream | 1328.9 | 1322.9 | 1.0045 |
1325.2 | 1320.1 | 1.0041 |
| center_10s_p4_m18560 | fp8pv | unchanged | 1317.7 | 1317.8 | 1.0001 |
1308.8 | 1308.9 | 0.9999 |
| center_15s_p2_m54976 | fp4pv | two-stream | 21467.0 | 21393.5 | 1.0034
| 21452.8 | 21380.9 | 1.0033 |
| center_15s_p2_m54976 | fp8pv | unchanged | 22481.1 | 22425.1 | 0.9988
c | 22132.9 | 22192.8 | 1.0003 c |
| tail_5s_p1_m38531 | fp4pv | two-stream | 21363.7 | 21258.9 | 1.0049 |
21352.0 | 21260.2 | 1.0043 |
| tail_5s_p1_m38531 | fp8pv | unchanged | 22478.2 | 22429.0 | 1.0008 |
22230.7 | 22349.8 | 0.9905 c |
| tail_5s_p2_m19333 | fp4pv | two-stream | 2851.2 | 2840.7 | 1.0037 |
2842.3 | 2832.9 | 1.0033 |
| tail_5s_p2_m19333 | fp8pv | unchanged | 2863.8 | 2863.8 | 1.0000 |
2854.2 | 2855.2 | 0.9997 |
| tail_5s_p8_m4763 | fp4pv | unchanged | 65.7 | 65.7 | 0.9995 | 65.4 |
65.4 | 0.9995 |
| tail_5s_p8_m4763 | fp8pv | unchanged | 67.0 | 67.0 | 1.0000 | 65.3 |
65.3 | 1.0000 |
| pad_15s_p1_used109901_total109952 | fp4pv | two-stream | 168612.4 |
168201.2 | 1.0025 | 168620.9 | 168146.7 | 1.0028 |
| pad_15s_p1_used109901_total109952 | fp8pv | unchanged | 179171.6 |
179288.3 | 0.9993 c | 178325.5 | 178189.9 | 1.0017 |
| center_4s_p4_m8368 | fp4pv | unchanged | 330.5 | 330.5 | 1.0000 |
331.4 | 331.4 | 1.0000 |
| center_4s_p4_m8368 | fp8pv | unchanged | 327.6 | 327.6 | 0.9999 |
328.0 | 328.0 | 1.0000 |
| center_5s_p1_m38592 | fp4pv | two-stream | 21393.6 | 21290.0 | 1.0048
| 21358.3 | 21261.8 | 1.0043 |
| center_5s_p1_m38592 | fp8pv | unchanged | 22495.8 | 22528.0 | 0.9933 c
| 22045.4 | 22244.3 | 0.9952 |
| center_5s_p4_m9648 | fp4pv | unchanged | 421.1 | 421.2 | 0.9999 |
421.7 | 421.7 | 1.0000 |
| center_5s_p4_m9648 | fp8pv | unchanged | 417.1 | 417.1 | 1.0003 |
416.1 | 416.1 | 1.0000 |
| center_6s_p8_m6096 | fp4pv | unchanged | 100.2 | 100.2 | 1.0000 |
101.3 | 101.3 | 1.0003 |
| center_6s_p8_m6096 | fp8pv | unchanged | 98.3 | 98.3 | 1.0000 | 98.6 |
98.7 | 1.0000 |
| center_8s_p2_m29472 | fp4pv | two-stream | 6330.9 | 6319.3 | 1.0018 |
6314.6 | 6303.7 | 1.0017 |
| center_8s_p2_m29472 | fp8pv | unchanged | 6356.1 | 6341.2 | 1.0004 c |
6300.4 | 6272.0 | 1.0005 c |
| center_10s_p1_m74240 | fp4pv | two-stream | 77239.1 | 77077.6 | 1.0021
| 77123.2 | 76965.2 | 1.0021 |
| center_10s_p1_m74240 | fp8pv | unchanged | 82442.5 | 82366.9 | 1.0010
| 81243.0 | 81219.8 | 1.0000 c |
| center_10s_p2_m37120 | fp4pv | two-stream | 9884.7 | 9861.4 | 1.0024 |
9865.0 | 9846.8 | 1.0019 |
| center_10s_p2_m37120 | fp8pv | unchanged | 10178.1 | 10185.1 | 0.9992
c | 10054.0 | 10067.0 | 0.9995 c |
| center_15s_p8_m13744 | fp4pv | unchanged | 418.4 | 418.3 | 1.0001 |
419.5 | 419.4 | 1.0000 |
| center_15s_p8_m13744 | fp8pv | unchanged | 412.6 | 412.5 | 1.0000 |
412.4 | 412.4 | 1.0002 |
| tail_5s_p1_m38629 | fp4pv | two-stream | 21387.8 | 21288.9 | 1.0046 |
21355.0 | 21264.6 | 1.0042 |
| tail_5s_p1_m38629 | fp8pv | unchanged | 22482.1 | 22592.7 | 0.9944 |
22071.1 | 22139.8 | 0.9968 c |
| tail_5s_p4_m9587 | fp4pv | unchanged | 416.3 | 416.3 | 0.9999 | 416.6
| 416.5 | 1.0000 |
| tail_5s_p4_m9587 | fp8pv | unchanged | 411.4 | 411.4 | 1.0000 | 411.9
| 411.9 | 1.0000 |
| tail_5s_p8_m4861 | fp4pv | unchanged | 65.6 | 65.6 | 1.0000 | 66.0 |
65.9 | 1.0010 |
| tail_5s_p8_m4861 | fp8pv | unchanged | 65.8 | 65.9 | 0.9995 | 65.4 |
65.4 | 1.0000 |
| pad_5s_p4_used9611_total9664 | fp4pv | unchanged | 431.1 | 431.0 |
1.0001 | 431.3 | 431.4 | 1.0000 |
| pad_5s_p4_used9611_total9664 | fp8pv | unchanged | 421.7 | 421.8 |
0.9999 | 421.9 | 422.0 | 0.9999 |
| center_4s_p1_m33472 | bf16 | unchanged | 22492.3 | 22468.7 | 0.9978 |
22340.1 | 22239.9 | 1.0045 |
| center_4s_p2_m16736 | bf16 | unchanged | 2609.8 | 2602.1 | 1.0038 |
2522.5 | 2515.2 | 1.0042 |
| center_4s_p8_m4184 | bf16 | unchanged | 55.1 | 55.1 | 1.0000 | 54.9 |
54.9 | 1.0000 |
| center_5s_p4_m9648 | bf16 | unchanged | 424.1 | 424.2 | 1.0000 | 422.6
| 422.6 | 1.0000 |
| center_6s_p1_m48768 | bf16 | unchanged | 47921.2 | 47811.9 | 0.9998 |
47139.8 | 47127.1 | 1.0011 |
| center_6s_p2_m24384 | bf16 | unchanged | 5813.5 | 5830.9 | 0.9963 |
5647.5 | 5593.6 | 1.0053 c |
| center_6s_p8_m6096 | bf16 | unchanged | 96.5 | 96.5 | 1.0000 | 97.6 |
97.6 | 1.0000 |
| center_8s_p4_m14736 | bf16 | unchanged | 1009.1 | 1000.0 | 1.0091 c |
998.4 | 996.6 | 0.9969 |
| center_10s_p1_m74240 | bf16 | unchanged | 110280.6 | 110611.2 | 1.0000
| 108834.0 | 109027.0 | 1.0001 |
| center_10s_p2_m37120 | bf16 | unchanged | 13195.1 | 13206.1 | 0.9839 |
12993.7 | 13215.8 | 0.9832 |
| center_10s_p8_m9280 | bf16 | unchanged | 209.1 | 209.1 | 1.0000 |
209.1 | 209.1 | 1.0000 |
| center_15s_p4_m27488 | bf16 | unchanged | 3591.6 | 3565.7 | 1.0143 |
3527.5 | 3515.3 | 1.0037 |
| tail_5s_p1_m38531 | bf16 | unchanged | 30002.7 | 30073.5 | 0.9898 c |
29495.7 | 29677.0 | 0.9922 |
| tail_5s_p2_m19235 | bf16 | unchanged | 3507.6 | 3508.3 | 1.0013 |
3462.0 | 3464.8 | 0.9996 |
| tail_5s_p4_m9587 | bf16 | unchanged | 420.9 | 420.9 | 1.0000 | 418.0 |
418.0 | 1.0002 |
| tail_5s_p8_m4763 | bf16 | unchanged | 63.1 | 63.1 | 1.0000 | 63.4 |
63.4 | 1.0000 |
| pad_5s_p4_used9611_total9664 | bf16 | unchanged | 431.0 | 431.0 |
1.0000 | 425.3 | 425.3 | 1.0000 |
| pad_15s_p1_used109901_total109952 | bf16 | unchanged | 242234.4 |
242286.8 | 0.9998 | 240892.5 | 240896.4 | 0.9925 c |
| dit_2seg_p1_m16320x2 | bf16 | unchanged | 10358.4 | 10361.3 | 1.0004 c
| 10192.1 | 10192.8 | 0.9989 |
| dit_tiny_p1_m9_9 | bf16 | unchanged | 3.6 | 3.6 | 1.0000 | 3.8 | 3.8 |
1.0000 |
| dit_2seg_p1_m16320x2_fused_qkv_view | bf16 | unchanged | 10362.4 |
10364.1 | 0.9999 | 10218.4 | 10345.8 | 1.0000 |
| dit_tiny_p1_m9_9_fused_qkv_view | bf16 | unchanged | 3.6 | 3.6 |
1.0000 | 3.7 | 3.7 | 1.0000 |
| center_4s_p4_m8368 | bf16 | unchanged | 323.6 | 323.7 | 0.9999 | 322.5
| 322.4 | 1.0001 |
| center_5s_p1_m38592 | bf16 | unchanged | 29372.8 | 29422.0 | 1.0003 |
28976.9 | 28980.2 | 0.9999 |
| center_5s_p2_m19296 | bf16 | unchanged | 3381.4 | 3388.0 | 1.0025 |
3535.7 | 3533.7 | 1.0004 |
| center_5s_p8_m4824 | bf16 | unchanged | 63.2 | 63.2 | 1.0000 | 62.5 |
62.5 | 1.0000 |
| center_6s_p4_m12192 | bf16 | unchanged | 701.6 | 702.5 | 0.9987 |
696.7 | 696.4 | 0.9999 |
| center_8s_p1_m58944 | bf16 | unchanged | 68872.2 | 68876.0 | 0.9995 |
68072.9 | 68127.8 | 0.9996 |
| center_8s_p2_m29472 | bf16 | unchanged | 8162.4 | 8158.4 | 0.9783 c |
8239.5 | 8191.6 | 1.0087 |
| center_8s_p8_m7368 | bf16 | unchanged | 140.6 | 140.6 | 1.0000 | 139.6
| 139.6 | 1.0000 |
| center_10s_p4_m18560 | bf16 | unchanged | 1596.9 | 1577.2 | 1.0083 |
1565.8 | 1566.4 | 1.0035 |
| center_15s_p1_m109952 | bf16 | unchanged | 239303.3 | 239324.4 |
0.9999 | 236415.6 | 236431.5 | 1.0005 |
| center_15s_p2_m54976 | bf16 | unchanged | 29757.1 | 29760.1 | 0.9999 |
29395.0 | 29402.3 | 0.9960 |
| center_15s_p8_m13744 | bf16 | unchanged | 422.1 | 422.1 | 1.0000 |
419.2 | 419.2 | 1.0000 |
| tail_5s_p1_m38629 | bf16 | unchanged | 29417.2 | 29386.7 | 1.0021 |
29047.9 | 29204.0 | 0.9947 |
| tail_5s_p2_m19333 | bf16 | unchanged | 3448.7 | 3443.4 | 1.0043 |
3395.4 | 3395.9 | 0.9909 |
| tail_5s_p4_m9685 | bf16 | unchanged | 418.1 | 418.1 | 0.9999 | 414.9 |
414.9 | 1.0000 |
| tail_5s_p8_m4861 | bf16 | unchanged | 63.3 | 63.3 | 1.0000 | 62.6 |
62.6 | 1.0000 |
| dit_t2va_p1_m32640 | bf16 | unchanged | 21397.1 | 21305.8 | 1.0010 |
20397.7 | 20343.4 | 1.0037 |
| dit_short_p1_m3072_1024 | bf16 | unchanged | 195.3 | 195.3 | 1.0000 |
193.5 | 193.5 | 1.0000 |
| dit_t2va_p1_m32640_fused_qkv_view | bf16 | unchanged | 20925.8 |
20613.0 | 1.0153 | 20473.1 | 20264.0 | 0.9968 c |
| dit_short_p1_m3072_1024_fused_qkv_view | bf16 | unchanged | 195.3 |
195.3 | 1.0000 | 193.3 | 193.3 | 1.0000 |

Cake ships the BF16, NVFP4 `fp4pv` and NVFP4 `fp8pv` variants of this
kernel in contiguous and fused-QKV view layouts on sm_100a (B200) and
sm_103a (GB300); sm_103a has no two-launch schedule and is unchanged by
this PR.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved the reliability of NVFP4 variable-length attention results
across repeated calls, concurrent CUDA streams, delayed operations, and
graph replays.
* Preserved expected output behavior across supported execution paths,
including single-stream configurations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [5aec638](https://github.com/flashinfer-ai/flashinfer/commit/5aec638eec2c48bd8d3771bd6ba31b3b0146464f)

- **作者**: RomanAnders90
- **时间**: 2026-10-30T09:42:47Z
- **提交信息**: [Experimental] Qwen 3.8 Flash-Next block: the indexer's extend / prefill entries (chunked prefill through the serving caches) and the cuDNN Frontend 4c8e24355 re-vendor (#7983)

The Qwen 3.8 Flash-Next gated attention block gains the indexer's extend / prefill entries: a uniform chunk of every sequence behind a cached prefix (prefill = the same form at an empty prefix) selects over the prefix's compressed keys plus its own complete blocks and writes the serving caches (the K / V pools, the paged compressed-key cache, the raw-key ring) under one rounding convention, so a decode step reads what a chunk wrote. The vendored cuDNN Frontend subset is re-exported at commit 4c8e24355 (160 manifest files, byte-faithful, the recorded patch rows applied once each). 18 extend cells (the two-stage oracle, bitwise cache rows, chunked prefill then carried decode steps, typed declines, capture after one warm-up, the launch census, the device-value reports) and the reading-B output bound mirror; the Qwen 3.5 package follows the pin.

Co-Authored-By: Claude Fable 5.1 <noreply@anthropic.com>

### [9da5a60](https://github.com/flashinfer-ai/flashinfer/commit/9da5a602ae4cd6bd0823fd77abafa65f96136adc)

- **作者**: eigen
- **时间**: 2026-10-30T09:13:38Z
- **提交信息**: perf(cake_mhc): late-claim column-slab backward on SM100 so backward_finish runs under a full-SM hold (#7988)

`cake_mhc_train` is Cake's four-stream mHC training backend, and its
with-grad entry points are `forward_prepare` and `backward_finish`.
`backward_finish` runs a backward slab kernel in one of three forms: a
static schedule, a dynamic-claim schedule or a late-claim dynamic
schedule. The static form waits for every CTA to become resident, so it
does not complete while another stream holds every SM. On sm_100a (B200
/ GB200), for 1024 < T <= 4096, this PR routes `backward_finish` to the
late-claim dynamic form on the token ranges where that form showed no
unloaded cost: T 2049–2112, 2433–2496, 2945–3072, 3457–3520 and
4033–4096 on B200 (148 SMs), and T 1153–1344, 2433–2688, 2881–3584 and
3649–4096 on GB200 (152 SMs). That form is also updated: in its first
round, each CTA now works through four units of the same slab with one
shared operand load, then releases that operand earlier. As a result,
`backward_finish` completes while a side stream holds every SM and runs
faster under a 16 x 640 side load. Unloaded time is unchanged. The
baseline is the previous Cake version of these kernels on FlashInfer
`main`.

Input is BF16 X `[T, 4, 4096]`, and each load runs on a side stream.
**none** means no load. **16 x 640** means 16 CTAs of 640 threads.
**full-SM hold** means one 128-thread CTA per SM at maximum
shared-memory carveout (148 CTAs on B200, 152 on GB200). Times are the
median per-call time in ms. For each group, the median is taken over
CUDA-event timings of back-to-back calls, and the table shows the median
of those group medians. Speedup = main / PR, taken as the median of
per-group ratios and rounded to two decimals; above 1 means the PR is
faster. **blocked** means main does not complete while the hold is
resident.

**NVIDIA B200 (sm_100a, 148 SMs), CUDA 13.4, PyTorch 2.14.1+cu130**

| Kernel | T | Load | main ms | PR ms | Speedup |
|---|---|---|---|---|---|
| backward_finish | 2049 | none | 0.0810 | 0.0809 | 1.00x |
| backward_finish | 2049 | 16 x 640 | 0.1065 | 0.0872 | 1.22x |
| backward_finish | 2049 | full-SM hold | blocked | 0.0850 | — |
| backward_finish | 3072 | none | 0.1138 | 0.1143 | 1.00x |
| backward_finish | 3072 | 16 x 640 | 0.1679 | 0.1190 | 1.41x |
| backward_finish | 3072 | full-SM hold | blocked | 0.1183 | — |
| backward_finish | 4096 | none | 0.1341 | 0.1343 | 1.00x |
| backward_finish | 4096 | 16 x 640 | 0.2048 | 0.1434 | 1.43x |
| backward_finish | 4096 | full-SM hold | blocked | 0.1381 | — |

**NVIDIA GB200 (sm_100a, 152 SMs), CUDA 13.4, PyTorch 2.14.1+cu130**

| Kernel | T | Load | main ms | PR ms | Speedup |
|---|---|---|---|---|---|
| backward_finish | 1216 | none | 0.0564 | 0.0569 | 0.99x |
| backward_finish | 1216 | 16 x 640 | 0.0778 | 0.0614 | 1.27x |
| backward_finish | 1216 | full-SM hold | blocked | 0.0594 | — |
| backward_finish | 2560 | none | 0.0973 | 0.0975 | 1.00x |
| backward_finish | 2560 | 16 x 640 | 0.1352 | 0.1065 | 1.27x |
| backward_finish | 2560 | full-SM hold | blocked | 0.1004 | — |
| backward_finish | 4032 | none | 0.1239 | 0.1245 | 0.99x |
| backward_finish | 4032 | 16 x 640 | 0.1864 | 0.1414 | 1.32x |
| backward_finish | 4032 | full-SM hold | blocked | 0.1279 | — |
| backward_finish | 4096 | none | 0.1338 | 0.1311 | 1.02x |
| backward_finish | 4096 | 16 x 640 | 0.1823 | 0.1393 | 1.31x |
| backward_finish | 4096 | full-SM hold | blocked | 0.1352 | — |

Cake also ships the mHC training head (forward mean, writing backward
and accumulating backward) in `cake_mhc_train_head`, and the mHC
training family ships on sm_100a, sm_103a and sm_107a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added a backward-training execution path for supported NVIDIA sm_100a
workloads. The runtime selects the path based on workload shape and
available GPU resources.
* **Bug Fixes**
* Improved synchronization and ticket handling in backward-training
execution.
* **Performance**
* Updated workload routing to choose between available execution paths
for supported cases.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Avery Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [39f41e9](https://github.com/flashinfer-ai/flashinfer/commit/39f41e9a46c3b8f0bb34fd52f82687e4a7f98093)

- **作者**: eigen
- **时间**: 2026-10-30T08:23:44Z
- **提交信息**: perf(cake_causal_conv1d): one halo exchange for a layer's q/k/v KCP convolutions (#7985)

Part of #7815 (communication stalls under uneven rank arrival times).

## Problem
The issue reports that in the full model at CP16 with a reused
workspace, the compute stream waits at the first program after each
exchange. It measured 0.58 s/update of waiting after convolution halo
exchanges and 0.17 s/update after state exchanges. These waits are small
in the isolated benchmark because ranks arrive together there. In the
full model, they absorb the arrival-time skew that follows MoE layers.

On main, each of a layer's q, k and v KCP convolutions runs its own halo
exchange. That gives 3 global synchronization points per direction per
layer, and each one can absorb skew.

## What changed
- New public entry:
  ```python
cake_causal_conv1d_kcp_multi(xs, weights, ctx, *, recompute_handle=None)
-> tuple[Tensor, ...]
  ```
It runs the KCP convolutions of `n >= 1` tensors that share a context
with one halo collective per direction. The history rows of all tensors
travel side by side in one `all_to_all_single`. After the wait, they are
copied out into each tensor's own contiguous pool. Each tensor then runs
the same kernels as the single call.
- The result is bitwise equal to `tuple(cake_causal_conv1d_kcp(x, w,
ctx) for x, w in zip(xs, weights))`, both outputs and every gradient
(`dx` and `dweight`). Each tensor keeps its own kernels and its
fixed-order reduction. Channel counts may differ between tensors (each
`C_i` is a multiple of 8).
- Recompute handle: one handle serves the whole call. Its `"conv"` entry
holds the `n` history pools. The same handle may also carry the layer's
`"kda"` entry. Per layer, the halo collectives (original forward /
recompute / backward) change as follows:
  - with handles: 3 / 0 / 3 -> 1 / 0 / 1
  - without handles: 3 / 3 / 3 -> 1 / 1 / 1
- Per-rank contract: every rank of the group calls the entry once per
layer, in the same order, with the same tensor count and channel counts.
The ranks are not compared, because that would cost a collective. A
different count, channel count or order hangs the exchange or silently
corrupts the history rows, just as a mismatch of the single entry's
per-rank contract does. There is no new check and no extra collective.
- Docs: one entry in `docs/api/mamba.rst` and a new section in
`flashinfer/experimental/cake_kda_train/README.md`.
- The existing single entry `cake_causal_conv1d_kcp` is unchanged. On
the single-call path, main and this PR were compared tensor by tensor at
world sizes 1, 2 and 4: 312 tensors compared, 0 differ.
- Diff: 7 files, +1606/-50.

Usage, from the README (one handle for a checkpointed layer):

```python
def layer(xq, xk, xv, g, beta, h):
    q, k, v = cake_causal_conv1d_kcp_multi((xq, xk, xv), (wq, wk, wv), ctx, recompute_handle=h)
    ...
    return chunk_kda_kcp(q, k, v, g, beta, ctx, recompute_handle=h)

out = torch.utils.checkpoint.checkpoint(layer, xq, xk, xv, g, beta, KcpRecomputeHandle(),
                                        use_reentrant=False)
```

## Results
Full-model proxy. Setup: GB200, torch 2.14.1, 34 layers, 4 layer-packs
per step, prep thread, skew `lognormal:1,1` where noted, palindromic
visit order, bootstrap 95 % CI of the step-time ratio against main.
Gradients were bitwise equal in every visit of every row, and the FP64
gate passed.

Columns:
- **main step ms**: median step time on main, with three single conv
calls per layer.
- **this PR ratio**: this PR using `cake_causal_conv1d_kcp_multi`,
divided by main.
- **A/A control ratio**: this PR still making three single calls,
divided by main.
- The remaining columns show main -> this PR (multi entry).

| row | main step ms | this PR ratio (95 % CI) | A/A control ratio (95 %
CI) | KCP global syncs / layer-pack | halo stall ms / update | total KCP
stall ms / update | colls / step | peak GiB |
|---|---:|---|---|---|---|---|---|---:|
| CP16 none | 5860.8 | 0.9976 (0.9894-1.0014) | 1.0033 (0.9943-1.0099) |
10.00 -> 6.00 | 80 -> 46 | 350 -> 348 | 1361 -> 817 | 80.16 |
| CP16 skew | 7089.2 | 0.9941 (0.9879-0.9980) | 0.9991 (0.9924-1.0067) |
10.00 -> 6.00 | 290 -> 146 | 1254 -> 1234 | 1361 -> 817 | 80.16 |
| CP16 none, no conv/KDA handles | 5915.9 | 1.0000 (0.9963-1.0105) |
1.0007 (0.9966-1.0069) | 15.00 -> 9.00 | 122 -> 73 | 369 -> 351 | 2041
-> 1225 | 78.65 |
| CP8 none | 11492.1 | 0.9975 (0.9905-1.0031) | 1.0011 (0.9949-1.0079) |
10.00 -> 6.00 | 164 -> 91 | 651 -> 618 | 1361 -> 817 | 125.09 |
| CP8 skew | 12196.7 | 0.9914 (0.9863-1.0041) | 1.0007 (0.9897-1.0100) |
10.00 -> 6.00 | 321 -> 171 | 947 -> 892 | 1361 -> 817 | 125.09 |

The CP16 no-handle row and both CP8 rows ran 1 group, so their CIs are
wider.

What the table shows:
- **Step time:** the gain is within noise in every row except CP16 with
skew, where the ratio is 0.9941 (CI 0.9879-0.9980). CP8 with skew gives
0.9914, but its CI (0.9863-1.0041) includes 1.
- **Stalls:** halo stall roughly halves in every row. The waits move to
the KDA state exchange, so total KCP stall drops by only 1-8 %.
- **Synchronization and memory:** global syncs per layer-pack and
collectives per step drop as expected. Peak memory is unchanged.

## Tests
Single node, 4 GPUs. Counts are passed/skipped/failed and are identical
on GB300 (sm_103a), GB200 (sm_100a) and R200 (sm_107a), with 0 failed:

| file | counts |
|---|---|
| `test_cake_causal_conv1d_train_kcp` (main and this PR) | 38/0/0 |
| `test_cake_causal_conv1d_train_kcp_build` (main and this PR) | 8/0/0 |
| `test_cake_causal_conv1d_train_kcp_knobs` (main and this PR) | 11/0/0
|
| `test_cake_causal_conv1d_train_api` (main and this PR) | 3/0/0 |
| `test_cake_causal_conv1d_train_kcp_dist` | 7/3/0 |
| `test_cake_causal_conv1d_train_kcp_multi` (new) | 43/0/0 |
| `test_cake_causal_conv1d_train_kcp_multi_dist` (new) | 9/4/0 |
| `test_cake_kda_train_kcp_dist` (with the new layer rows) | 23/3/0 |

All skips are 8-GPU rows.

What the new tests cover:
- **Single-GPU and NCCL rows:** each compares
`cake_causal_conv1d_kcp_multi` against one `cake_causal_conv1d_kcp` call
per tensor. They check bitwise `y` / `dx` / `dweight`, collectives per
phase, the recompute handle, graph replay, and KDA and GDN contexts.
- **KDA KCP checkpoint test:** a new multi-convolution layer row.

Also:
- **CP8 on 2 nodes x 4 GPUs (GB300 and GB200):** all 8 ranks pass on
both architectures, with 0 failed:
  - the 4 8-GPU rows of the new `multi_dist` file;
- the 3 8-GPU rows of the conv `kcp_dist` file, on main and on this PR;
  - the 6 8-GPU rows of the KDA `kcp_dist` file, on main and on this PR.
- **GDN pre-existing failure:** in `test_cake_gdn_train_kcp_dist`,
`test_conv_halo_row` passes. `test_layer_checkpoint_rows` fails
identically on main and on this PR with `ImportError: cannot import name
'cake_gdn_train_inputs' from 'tests.test_helpers'`. With 8 tasks, that
row's failure on ranks 0-3 desyncs the collectives, and the run exits
with rc 134 on both trees. No GDN file is changed by this PR. The multi
entry through a GDN context is covered by the GDN-context checks
(`gdn_ctx_*` flags) in `test_cake_causal_conv1d_train_kcp_multi_dist`.
- **Pre-commit:** clean.

### Rebase onto current main
- The rebase onto current main was clean. The only change afterwards is
one added docstring sentence, in the backend and facade `ctx` docs: the
rank-mismatch sentence quoted under "What changed". It adds no check and
no collective.
- Between the earlier base and current main, the conv path is identical:
the diff of the conv facade, conv backend, conv KCP tests and collective
shims is empty. Main changed only the KDA state path in between (#7951,
#7955). So the proxy and CP8 results above still apply.
- **GB300 on the rebased tree:** pre-commit is clean, and the unit
counts are identical to those above, including 312 tensors compared with
0 differing on the single-call path. KDA `kcp_dist` is 23/3/0 on both
main and this PR.
- **Flaky test on main:** `test_cake_kda_train_kcp_shared_ws` is 24/3/1
on both main and this PR. The failing test in both cases is
`test_gpu_call_on_another_stream_waits_for_the_last_one`, a timing-based
check from #7955. It is a pre-existing flaky test on main, unrelated to
this PR, and is being fixed separately.
- **R200 and GB200 on the rebased tree:** reruns are queued. The R200
and GB200 results above were measured on the earlier base.

## Not covered
- **GDN:** GDN keeps its single packed conv.
`test_layer_checkpoint_rows` needs an external input helper that is
absent on main (it fails identically on main). No GDN file changed.
- **Step time:** within noise without skew. With skew `lognormal:1,1`,
CP16 is x0.9941 (CI 0.9879-0.9980) and CP8 is x0.9914 (CI
0.9863-1.0041). Halo stall roughly halves, but the waits move to the KDA
state exchange, so total KCP stall drops by only 1-8 %. The remaining
rank-skew item on #7815 is the state exchange.
- **Wider CIs:** the CP16 no-handle and CP8 proxy rows ran 1 group.
- **No rank-mismatch check:** a mismatch in tensor count, channel count
or call order across ranks is not detected (see "What changed").


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added support for training multiple context-parallel causal
convolutions together, sharing halo exchanges while preserving each
convolution’s outputs and gradients.
* Supports checkpointing, recomputation, and graph replay for
multi-convolution workloads.
* The q/k/v convolution workflow can now reduce halo exchanges from
three to one during forward and backward passes.
* **Documentation**
* Added usage details for combining q/k/v convolutions and sharing
recomputation state.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [26bb6dc](https://github.com/flashinfer-ai/flashinfer/commit/26bb6dc93831c0192e524357dd25d7092917ae9b)

- **作者**: Perkz Zheng
- **时间**: 2026-10-30T08:20:49Z
- **提交信息**: perf(prims-ts): schedule D576 sparse MLA head counts between qualified ones (#7984)

<!-- .github/pull_request_template.md -->

## 📌 Description

D576 sparse MLA with FP8 MMA (native FP8 and NVFP4 caches) selected its
schedule by the exact head count, but the measured crossovers cover
8/16/32/64/128 heads. Other counts, such as 12/24/48/96, fell through to
a default M16 Swap-AB grid that repeats every KV tile once per 16-head
tile.

- Map these head counts to the next qualified count's schedule. Its Q
tile already pads the count, and the kernel masks the extra rows. If the
mapped schedule uses cluster reduction and the heads are not a multiple
of 16, keep the raw-count schedule.
- Retune D576 top-k 2048 crossovers for H16 prefill, H32 decode and
prefill, and NVFP4 H64/H128 grids below 16 rows.
- D512 and BF16 schedules are unchanged. Policy only: no kernel,
compile-key or API changes.

GB300, top-k 2048, 128k-token KV, CUDA graph with cold L2, CUPTI median.
The kernels are identical; only the schedule differs.

| Heads | Cache | Batch x Sq | main (us) | this PR (us) |
|---:|---|---|---:|---:|
| 24 | FP8 | 1 x 8192 | 5347.2 | 1498.5 |
| 48 | NVFP4 | 64 x 4 | 1638.7 | 78.1 |
| 96 | FP8 | 64 x 8 | 350.9 | 144.8 |
| 96 | NVFP4 | 1 x 8192 | 7895.7 | 2680.2 |
| 16 | FP8 | 1 x 8192 | 1634.6 | 1365.1 |
| 32 | FP8 | 4 x 8 | 30.2 | 20.7 |
| 64 | NVFP4 | 1 x 4 | 31.2 | 13.0 |

Over 238 decode/prefill points (heads 12/16/24/32/48/64/96/128, 128k and
256k KV), the 103 with a changed schedule are 1.03-23.5x faster. Points
with an unchanged schedule stay within 2%.

## 🔍 Related Issues

Follows #7106.

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

`pre-commit run --files` on the two changed files passes all hooks.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/attention/test_attention_ts_sparse_mla.py`

Added D576 graph accuracy cases for H24/H48/H96: masked rows in
persistent M64 and 2CTA tiles, split M64, and the cluster-reduction
fallback. `tests/attention/test_attention_ts_sparse_mla.py`: 182 passed
on GB300.

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

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Sparse MLA decoding now uses D576-specific scheduling for additional
FP8 workloads, including small-batch cases. Schedule selection also
covers more head-count configurations, broadening optimized execution
coverage across varied batch sizes and sequence lengths.
* **Tests**
* Added coverage for D576 sparse decoding across additional FP8 and
NVFP4 configurations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: Perkz Zheng <67892460+PerkzZheng@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [9643349](https://github.com/flashinfer-ai/flashinfer/commit/9643349fca9162cb292dbb0fbab50b8e73b4712b)

- **作者**: eigen
- **时间**: 2026-10-30T07:45:44Z
- **提交信息**: perf(cake_kimi_k3_latent_moe): faster Kimi-K3 LatentMoE decode tails and prefill (#7979)

This PR updates the Cake programs for the Kimi-K3 Stable LatentMoE front
and tail projections of one rank in
`flashinfer.experimental.kimi_k3_latent_moe` (BF16, `sm_100a` and
`sm_103a`). The package has four variants: the front and the tail
projection, each for TP1 and TP8. Decode-sized token counts run a decode
instance, and the tail fuses the RMSNorm and the reduction of P routed
partials into it. Larger token counts run a prefill GEMM. The baseline
is the Cake programs of #7948, which are now on FlashInfer main
("previous"). Speedup = previous / this PR. This PR changes all four
variants, each on some parts only. The TP8 tail prefill path does not
change. On every changed row the outputs stay bitwise those of the
previous program. On every GPU, the TP8 decode tail rows of 1-4 tokens
with 3 or more routed partials now split rows across the epilogue warps.
These rows gain 1.186-1.551x. On `sm_103a` GPUs (NVIDIA B300 SXM6 AC,
NVIDIA GB300), the TP1 decode tail rows of 1-8 tokens with 8 or more
partials take the same split rows and gain 1.019-1.193x. On NVIDIA
GB300, the TP1 rows of 3 tokens take the split rows only from 9
partials. Its row at 8 partials therefore keeps its route and shows
1.000x. On 148-SM GPUs (NVIDIA B200, NVIDIA B300 SXM6 AC), the TP1 tail
prefill rows of 129-256 tokens now run the 224-wide pair tile with a
lean split-K finisher in place of the wider tile. They gain
1.092-1.098x. On 152-SM GPUs (NVIDIA GB200, NVIDIA GB300), the TP8 front
prefill rows of 769-1024 tokens run the fold form with a table of lane
bounds and gain 1.063-1.083x. On NVIDIA GB300, the TP8 front rows of
1793-2048 tokens run the 224-wide pair tile in place of the fold form
and gain 1.054-1.055x. The TP1 front rows of 513-768 tokens there also
run the 224-wide pair tile and gain 1.086x. The PR changes 25 rows on
NVIDIA B200, 41 on NVIDIA B300 SXM6 AC, 29 on NVIDIA GB200 and 48 on
NVIDIA GB300. These rows gain 1.019-1.551x. On changed rows both sides
are measured in the same run, so the previous column there is a new
measurement of the #7948 program and not a copy of the #7948 table. All
other rows run the same machine code and routes as #7948. Both of their
columns show one value, taken from the table of #7948. The rows that
#7948 changed therefore show no speedup here.

| Projection | TP | Tokens | B200 previous (µs) | B200 this PR (µs) |
B200 speedup | B300 previous (µs) | B300 this PR (µs) | B300 speedup |
GB200 previous (µs) | GB200 this PR (µs) | GB200 speedup | GB300
previous (µs) | GB300 this PR (µs) | GB300 speedup |
|:--|--:|--:|--:|--:|--:|--:|--:|--:|--:|--:|--:|--:|--:|--:|
| front | 1 | 1 | 42.88 | 42.88 | 1.000x | 42.90 | 42.90 | 1.000x |
41.50 | 41.50 | 1.000x | 41.49 | 41.49 | 1.000x |
| front | 1 | 2 | 42.13 | 42.13 | 1.000x | 43.02 | 43.02 | 1.000x |
41.50 | 41.50 | 1.000x | 41.60 | 41.60 | 1.000x |
| front | 1 | 4 | 42.05 | 42.05 | 1.000x | 42.93 | 42.93 | 1.000x |
41.41 | 41.41 | 1.000x | 41.70 | 41.70 | 1.000x |
| front | 1 | 5 | 42.05 | 42.05 | 1.000x | 43.12 | 43.12 | 1.000x |
41.39 | 41.39 | 1.000x | 41.71 | 41.71 | 1.000x |
| front | 1 | 8 | 41.86 | 41.86 | 1.000x | 42.85 | 42.85 | 1.000x |
41.31 | 41.31 | 1.000x | 41.79 | 41.79 | 1.000x |
| front | 1 | 9 | 42.06 | 42.06 | 1.000x | 42.91 | 42.91 | 1.000x |
41.49 | 41.49 | 1.000x | 41.97 | 41.97 | 1.000x |
| front | 1 | 16 | 42.34 | 42.34 | 1.000x | 43.34 | 43.34 | 1.000x |
41.94 | 41.94 | 1.000x | 42.53 | 42.53 | 1.000x |
| front | 1 | 32 | 42.66 | 42.66 | 1.000x | 43.49 | 43.49 | 1.000x |
41.92 | 41.92 | 1.000x | 42.42 | 42.42 | 1.000x |
| front | 1 | 64 | 44.26 | 44.26 | 1.000x | 44.43 | 44.43 | 1.000x |
43.25 | 43.25 | 1.000x | 43.58 | 43.58 | 1.000x |
| front | 1 | 128 | 49.09 | 49.09 | 1.000x | 48.90 | 48.90 | 1.000x |
48.46 | 48.46 | 1.000x | 48.03 | 48.03 | 1.000x |
| front | 1 | 200 | 50.78 | 50.78 | 1.000x | 52.29 | 52.29 | 1.000x |
51.15 | 51.15 | 1.000x | 48.53 | 48.53 | 1.000x |
| front | 1 | 256 | 51.04 | 51.04 | 1.000x | 52.48 | 52.48 | 1.000x |
52.03 | 52.03 | 1.000x | 48.83 | 48.83 | 1.000x |
| front | 1 | 512 | 85.44 | 85.44 | 1.000x | 79.71 | 79.71 | 1.000x |
92.45 | 92.45 | 1.000x | 68.21 | 68.21 | 1.000x |
| front | 1 | 768 | 126.77 | 126.77 | 1.000x | 128.29 | 128.29 | 1.000x
| 141.66 | 141.66 | 1.000x | 109.89 | 101.22 | 1.086x |
| front | 1 | 1024 | 167.33 | 167.33 | 1.000x | 165.51 | 165.51 | 1.000x
| 170.29 | 170.29 | 1.000x | 131.97 | 131.97 | 1.000x |
| front | 1 | 2048 | 324.30 | 324.30 | 1.000x | 314.63 | 314.63 | 1.000x
| 312.98 | 312.98 | 1.000x | 250.75 | 250.75 | 1.000x |
| front | 1 | 4096 | 614.83 | 614.83 | 1.000x | 547.78 | 547.78 | 1.000x
| 640.60 | 640.60 | 1.000x | 528.51 | 528.51 | 1.000x |
| front | 1 | 8192 | 1220.26 | 1220.26 | 1.000x | 1080.59 | 1080.59 |
1.000x | 1317.63 | 1317.63 | 1.000x | 1092.76 | 1092.76 | 1.000x |
| front | 1 | 16384 | 2404.14 | 2404.14 | 1.000x | 2213.30 | 2213.30 |
1.000x | 2668.08 | 2668.08 | 1.000x | 2193.13 | 2193.13 | 1.000x |
| front | 8 | 1 | 18.99 | 18.99 | 1.000x | 18.88 | 18.88 | 1.000x |
18.32 | 18.32 | 1.000x | 18.40 | 18.40 | 1.000x |
| front | 8 | 2 | 18.93 | 18.93 | 1.000x | 19.02 | 19.02 | 1.000x |
18.32 | 18.32 | 1.000x | 18.43 | 18.43 | 1.000x |
| front | 8 | 4 | 18.94 | 18.94 | 1.000x | 19.02 | 19.02 | 1.000x |
18.32 | 18.32 | 1.000x | 18.46 | 18.46 | 1.000x |
| front | 8 | 5 | 19.12 | 19.12 | 1.000x | 18.93 | 18.93 | 1.000x |
18.38 | 18.38 | 1.000x | 18.38 | 18.38 | 1.000x |
| front | 8 | 8 | 19.10 | 19.10 | 1.000x | 18.99 | 18.99 | 1.000x |
18.37 | 18.37 | 1.000x | 18.37 | 18.37 | 1.000x |
| front | 8 | 9 | 19.18 | 19.18 | 1.000x | 19.10 | 19.10 | 1.000x |
18.46 | 18.46 | 1.000x | 18.43 | 18.43 | 1.000x |
| front | 8 | 16 | 19.14 | 19.14 | 1.000x | 19.20 | 19.20 | 1.000x |
18.54 | 18.54 | 1.000x | 18.51 | 18.51 | 1.000x |
| front | 8 | 32 | 19.65 | 19.65 | 1.000x | 19.70 | 19.70 | 1.000x |
18.88 | 18.88 | 1.000x | 18.94 | 18.94 | 1.000x |
| front | 8 | 64 | 20.51 | 20.51 | 1.000x | 20.38 | 20.38 | 1.000x |
19.73 | 19.73 | 1.000x | 19.82 | 19.82 | 1.000x |
| front | 8 | 128 | 25.74 | 25.74 | 1.000x | 25.68 | 25.68 | 1.000x |
25.30 | 25.30 | 1.000x | 24.62 | 24.62 | 1.000x |
| front | 8 | 200 | 29.92 | 29.92 | 1.000x | 29.12 | 29.12 | 1.000x |
29.47 | 29.47 | 1.000x | 28.03 | 28.03 | 1.000x |
| front | 8 | 256 | 29.95 | 29.95 | 1.000x | 29.38 | 29.38 | 1.000x |
29.82 | 29.82 | 1.000x | 27.97 | 27.97 | 1.000x |
| front | 8 | 512 | 40.37 | 40.37 | 1.000x | 38.11 | 38.11 | 1.000x |
38.86 | 38.86 | 1.000x | 36.21 | 36.21 | 1.000x |
| front | 8 | 640 | 46.96 | 46.96 | 1.000x | 44.06 | 44.06 | 1.000x |
46.80 | 46.80 | 1.000x | 41.84 | 41.84 | 1.000x |
| front | 8 | 768 | 47.28 | 47.28 | 1.000x | 46.26 | 46.26 | 1.000x |
47.71 | 47.71 | 1.000x | 42.27 | 42.27 | 1.000x |
| front | 8 | 769 | — | — | — | — | — | — | 74.41 | 68.71 | 1.083x |
58.29 | 54.43 | 1.071x |
| front | 8 | 800 | — | — | — | — | — | — | 73.20 | 68.69 | 1.066x |
58.61 | 54.56 | 1.074x |
| front | 8 | 897 | — | — | — | — | — | — | 76.14 | 70.63 | 1.078x |
58.82 | 55.11 | 1.067x |
| front | 8 | 960 | — | — | — | — | — | — | 75.31 | 70.74 | 1.065x |
59.26 | 55.09 | 1.076x |
| front | 8 | 1000 | — | — | — | — | — | — | 75.84 | 71.36 | 1.063x |
59.49 | 55.25 | 1.077x |
| front | 8 | 1024 | 67.18 | 67.18 | 1.000x | 65.47 | 65.47 | 1.000x |
77.95 | 72.38 | 1.077x | 59.46 | 55.88 | 1.064x |
| front | 8 | 1793 | 114.55 | 114.55 | 1.000x | — | — | — | — | — | — |
— | — | — |
| front | 8 | 1800 | 114.91 | 114.91 | 1.000x | 110.59 | 110.59 | 1.000x
| 123.63 | 123.63 | 1.000x | 98.62 | 93.52 | 1.055x |
| front | 8 | 1900 | 116.06 | 116.06 | 1.000x | — | — | — | — | — | — |
— | — | — |
| front | 8 | 2000 | 114.52 | 114.52 | 1.000x | 112.45 | 112.45 | 1.000x
| 127.89 | 127.89 | 1.000x | 100.29 | 95.16 | 1.054x |
| front | 8 | 2048 | 119.73 | 119.73 | 1.000x | 114.37 | 114.37 | 1.000x
| 129.41 | 129.41 | 1.000x | 100.74 | 95.55 | 1.054x |
| front | 8 | 4096 | 235.01 | 235.01 | 1.000x | 230.29 | 230.29 | 1.000x
| 240.68 | 240.68 | 1.000x | 190.99 | 190.99 | 1.000x |
| front | 8 | 8192 | 492.32 | 492.32 | 1.000x | 480.21 | 480.21 | 1.000x
| 471.60 | 471.60 | 1.000x | 383.97 | 383.97 | 1.000x |
| front | 8 | 16384 | 909.49 | 909.49 | 1.000x | 800.25 | 800.25 |
1.000x | 959.91 | 959.91 | 1.000x | 804.95 | 804.95 | 1.000x |
| tail | 1 | 1 | 26.42 | 26.42 | 1.000x | 26.64 | 26.64 | 1.000x | 25.71
| 25.71 | 1.000x | 25.76 | 25.76 | 1.000x |
| tail | 1 | 2 | 26.42 | 26.42 | 1.000x | 26.72 | 26.72 | 1.000x | 25.70
| 25.70 | 1.000x | 25.86 | 25.86 | 1.000x |
| tail | 1 | 4 | 26.54 | 26.54 | 1.000x | 26.82 | 26.82 | 1.000x | 25.74
| 25.74 | 1.000x | 25.92 | 25.92 | 1.000x |
| tail | 1 | 5 | 26.48 | 26.48 | 1.000x | 26.88 | 26.88 | 1.000x | 25.74
| 25.74 | 1.000x | 26.03 | 26.03 | 1.000x |
| tail | 1 | 8 | 26.50 | 26.50 | 1.000x | 26.78 | 26.78 | 1.000x | 25.78
| 25.78 | 1.000x | 26.03 | 26.03 | 1.000x |
| tail | 1 | 9 | 27.98 | 27.98 | 1.000x | 27.66 | 27.66 | 1.000x | 26.88
| 26.88 | 1.000x | 26.82 | 26.82 | 1.000x |
| tail | 1 | 16 | 28.02 | 28.02 | 1.000x | 27.76 | 27.76 | 1.000x |
26.88 | 26.88 | 1.000x | 27.01 | 27.01 | 1.000x |
| tail | 1 | 32 | 27.63 | 27.63 | 1.000x | 27.59 | 27.59 | 1.000x |
26.78 | 26.78 | 1.000x | 26.80 | 26.80 | 1.000x |
| tail | 1 | 64 | 27.58 | 27.58 | 1.000x | 27.89 | 27.89 | 1.000x |
27.06 | 27.06 | 1.000x | 26.83 | 26.83 | 1.000x |
| tail | 1 | 128 | 29.60 | 29.60 | 1.000x | 30.02 | 30.02 | 1.000x |
28.80 | 28.80 | 1.000x | 28.62 | 28.62 | 1.000x |
| tail | 1 | 129 | 41.04 | 37.39 | 1.098x | 40.95 | 37.41 | 1.095x |
36.98 | 36.98 | 1.000x | 35.84 | 35.84 | 1.000x |
| tail | 1 | 256 | 42.21 | 38.46 | 1.097x | 42.27 | 38.70 | 1.092x |
38.19 | 38.19 | 1.000x | 36.67 | 36.67 | 1.000x |
| tail | 1 | 300 | 54.00 | 54.00 | 1.000x | 52.64 | 52.64 | 1.000x |
48.35 | 48.35 | 1.000x | 41.57 | 41.57 | 1.000x |
| tail | 1 | 384 | 54.62 | 54.62 | 1.000x | 52.67 | 52.67 | 1.000x |
47.63 | 47.63 | 1.000x | 41.42 | 41.42 | 1.000x |
| tail | 1 | 512 | 55.70 | 55.70 | 1.000x | 53.33 | 53.33 | 1.000x |
51.68 | 51.68 | 1.000x | 42.50 | 42.50 | 1.000x |
| tail | 1 | 1024 | 98.61 | 98.61 | 1.000x | 95.79 | 95.79 | 1.000x |
105.65 | 105.65 | 1.000x | 83.09 | 83.09 | 1.000x |
| tail | 1 | 2048 | 192.64 | 192.64 | 1.000x | 188.91 | 188.91 | 1.000x
| 189.74 | 189.74 | 1.000x | 147.74 | 147.74 | 1.000x |
| tail | 1 | 4096 | 387.46 | 387.46 | 1.000x | 385.22 | 385.22 | 1.000x
| 368.18 | 368.18 | 1.000x | 293.95 | 293.95 | 1.000x |
| tail | 1 | 8192 | 718.12 | 718.12 | 1.000x | 651.83 | 651.83 | 1.000x
| 743.41 | 743.41 | 1.000x | 625.10 | 625.10 | 1.000x |
| tail | 1 | 16384 | 1446.74 | 1446.74 | 1.000x | 1291.42 | 1291.42 |
1.000x | 1521.33 | 1521.33 | 1.000x | 1284.41 | 1284.41 | 1.000x |
| tail | 8 | 1 | 7.87 | 7.87 | 1.000x | 7.86 | 7.86 | 1.000x | 7.74 |
7.74 | 1.000x | 7.58 | 7.58 | 1.000x |
| tail | 8 | 2 | 7.90 | 7.90 | 1.000x | 7.84 | 7.84 | 1.000x | 7.65 |
7.65 | 1.000x | 7.58 | 7.58 | 1.000x |
| tail | 8 | 4 | 7.92 | 7.92 | 1.000x | 7.86 | 7.86 | 1.000x | 7.70 |
7.70 | 1.000x | 7.65 | 7.65 | 1.000x |
| tail | 8 | 5 | 7.95 | 7.95 | 1.000x | 7.79 | 7.79 | 1.000x | 7.70 |
7.70 | 1.000x | 7.65 | 7.65 | 1.000x |
| tail | 8 | 8 | 8.00 | 8.00 | 1.000x | 7.97 | 7.97 | 1.000x | 7.76 |
7.76 | 1.000x | 7.68 | 7.68 | 1.000x |
| tail | 8 | 9 | 8.70 | 8.70 | 1.000x | 8.59 | 8.59 | 1.000x | 8.45 |
8.45 | 1.000x | 8.40 | 8.40 | 1.000x |
| tail | 8 | 16 | 9.34 | 9.34 | 1.000x | 8.94 | 8.94 | 1.000x | 9.16 |
9.16 | 1.000x | 8.94 | 8.94 | 1.000x |
| tail | 8 | 32 | 10.26 | 10.26 | 1.000x | 10.32 | 10.32 | 1.000x | 9.87
| 9.87 | 1.000x | 9.95 | 9.95 | 1.000x |
| tail | 8 | 64 | 10.85 | 10.85 | 1.000x | 10.67 | 10.67 | 1.000x |
10.45 | 10.45 | 1.000x | 10.45 | 10.45 | 1.000x |
| tail | 8 | 128 | 12.58 | 12.58 | 1.000x | 12.24 | 12.24 | 1.000x |
12.19 | 12.19 | 1.000x | 12.05 | 12.05 | 1.000x |
| tail | 8 | 256 | 14.94 | 14.94 | 1.000x | 14.05 | 14.05 | 1.000x |
14.51 | 14.51 | 1.000x | 14.03 | 14.03 | 1.000x |
| tail | 8 | 300 | 17.09 | 17.09 | 1.000x | 17.62 | 17.62 | 1.000x |
16.67 | 16.67 | 1.000x | 17.90 | 17.90 | 1.000x |
| tail | 8 | 512 | 18.69 | 18.69 | 1.000x | 17.66 | 17.66 | 1.000x |
18.66 | 18.66 | 1.000x | 17.68 | 17.68 | 1.000x |
| tail | 8 | 1024 | 26.00 | 26.00 | 1.000x | 23.97 | 23.97 | 1.000x |
23.81 | 23.81 | 1.000x | 22.67 | 22.67 | 1.000x |
| tail | 8 | 2048 | 39.12 | 39.12 | 1.000x | 36.48 | 36.48 | 1.000x |
32.83 | 32.83 | 1.000x | 30.80 | 30.80 | 1.000x |
| tail | 8 | 4096 | 62.72 | 62.72 | 1.000x | 58.86 | 58.86 | 1.000x |
57.54 | 57.54 | 1.000x | 51.84 | 51.84 | 1.000x |
| tail | 8 | 8192 | 111.60 | 111.60 | 1.000x | 102.42 | 102.42 | 1.000x
| 112.70 | 112.70 | 1.000x | 93.39 | 93.39 | 1.000x |
| tail | 8 | 16384 | 219.62 | 219.62 | 1.000x | 213.55 | 213.55 | 1.000x
| 222.29 | 222.29 | 1.000x | 182.40 | 182.40 | 1.000x |

*Times are µs per call on one rank from `bench_gpu_time_with_cupti` with
cold L2 and CUDA graph replay; both sides interleave in groups over two
passes, the second in reversed order; each value is the mean of the two
per-pass medians on one GPU; changed rows measure both sides in the same
run; rows this PR does not change show the value of #7948 in both
columns; speedup = previous / this PR; tail rows reduce one routed
partial; NVIDIA B200 (`sm_100a`, 148 SMs), NVIDIA B300 SXM6 AC
(`sm_103a`, 148 SMs), NVIDIA GB200 (`sm_100a`, 152 SMs), NVIDIA GB300
(`sm_103a`, 152 SMs); CUDA 13.4; "—" = the row is not on that part's
shape list.*

| Projection | TP | Tokens | Partials | B200 previous (µs) | B200 this
PR (µs) | B200 speedup | B300 previous (µs) | B300 this PR (µs) | B300
speedup | GB200 previous (µs) | GB200 this PR (µs) | GB200 speedup |
GB300 previous (µs) | GB300 this PR (µs) | GB300 speedup |
|:--|--:|--:|--:|--:|--:|--:|--:|--:|--:|--:|--:|--:|--:|--:|--:|
| tail | 1 | 1 | 2 | 26.45 | 26.45 | 1.000x | 26.67 | 26.67 | 1.000x |
25.68 | 25.68 | 1.000x | 25.66 | 25.66 | 1.000x |
| tail | 1 | 1 | 5 | 26.70 | 26.70 | 1.000x | 26.77 | 26.77 | 1.000x |
25.78 | 25.78 | 1.000x | 25.97 | 25.97 | 1.000x |
| tail | 1 | 1 | 6 | 28.32 | 28.32 | 1.000x | 27.42 | 27.42 | 1.000x |
27.47 | 27.47 | 1.000x | 27.02 | 27.02 | 1.000x |
| tail | 1 | 1 | 7 | 29.36 | 29.36 | 1.000x | 29.31 | 29.31 | 1.000x |
28.18 | 28.18 | 1.000x | 28.27 | 28.27 | 1.000x |
| tail | 1 | 1 | 8 | 29.90 | 29.90 | 1.000x | 29.49 | 28.77 | 1.025x |
28.75 | 28.75 | 1.000x | 28.50 | 27.86 | 1.023x |
| tail | 1 | 1 | 16 | 34.21 | 34.21 | 1.000x | 34.10 | 28.93 | 1.179x |
32.86 | 32.86 | 1.000x | 33.28 | 28.02 | 1.188x |
| tail | 1 | 2 | 5 | 27.01 | 27.01 | 1.000x | 26.88 | 26.88 | 1.000x |
26.51 | 26.51 | 1.000x | 26.06 | 26.06 | 1.000x |
| tail | 1 | 2 | 6 | 28.90 | 28.90 | 1.000x | 28.32 | 28.32 | 1.000x |
27.26 | 27.26 | 1.000x | 26.58 | 26.58 | 1.000x |
| tail | 1 | 2 | 7 | 29.34 | 29.34 | 1.000x | 29.46 | 29.46 | 1.000x |
28.32 | 28.32 | 1.000x | 28.34 | 28.34 | 1.000x |
| tail | 1 | 2 | 8 | 29.71 | 29.71 | 1.000x | 29.41 | 28.77 | 1.022x |
28.54 | 28.54 | 1.000x | 28.08 | 27.55 | 1.019x |
| tail | 1 | 2 | 16 | 34.88 | 34.88 | 1.000x | 33.92 | 28.99 | 1.170x |
33.36 | 33.36 | 1.000x | 32.48 | 27.70 | 1.173x |
| tail | 1 | 3 | 5 | 27.07 | 27.07 | 1.000x | 26.85 | 26.85 | 1.000x |
26.75 | 26.75 | 1.000x | 26.16 | 26.16 | 1.000x |
| tail | 1 | 3 | 6 | 29.39 | 29.39 | 1.000x | 28.62 | 28.62 | 1.000x |
28.34 | 28.34 | 1.000x | 27.71 | 27.71 | 1.000x |
| tail | 1 | 3 | 7 | 29.39 | 29.39 | 1.000x | 29.52 | 29.52 | 1.000x |
28.18 | 28.18 | 1.000x | 28.38 | 28.38 | 1.000x |
| tail | 1 | 3 | 8 | 29.87 | 29.87 | 1.000x | 29.46 | 28.83 | 1.022x |
28.43 | 28.43 | 1.000x | 28.56 | 28.56 | 1.000x |
| tail | 1 | 3 | 16 | 34.66 | 34.66 | 1.000x | 33.86 | 28.99 | 1.168x |
33.39 | 33.39 | 1.000x | 32.85 | 28.06 | 1.170x |
| tail | 1 | 4 | 5 | 26.91 | 26.91 | 1.000x | 26.88 | 26.88 | 1.000x |
26.05 | 26.05 | 1.000x | 25.95 | 25.95 | 1.000x |
| tail | 1 | 4 | 6 | 28.59 | 28.59 | 1.000x | 27.87 | 27.87 | 1.000x |
28.08 | 28.08 | 1.000x | 27.42 | 27.42 | 1.000x |
| tail | 1 | 4 | 7 | 29.70 | 29.70 | 1.000x | 29.41 | 29.41 | 1.000x |
28.34 | 28.34 | 1.000x | 28.43 | 28.43 | 1.000x |
| tail | 1 | 4 | 8 | 29.68 | 29.68 | 1.000x | 29.42 | 28.80 | 1.022x |
28.59 | 28.59 | 1.000x | 28.18 | 27.54 | 1.023x |
| tail | 1 | 4 | 16 | 34.93 | 34.93 | 1.000x | 33.82 | 28.98 | 1.167x |
33.46 | 33.46 | 1.000x | 32.77 | 27.71 | 1.182x |
| tail | 1 | 5 | 2 | 26.56 | 26.56 | 1.000x | 26.86 | 26.86 | 1.000x |
25.76 | 25.76 | 1.000x | 25.78 | 25.78 | 1.000x |
| tail | 1 | 5 | 3 | 26.85 | 26.85 | 1.000x | 26.93 | 26.93 | 1.000x |
26.26 | 26.26 | 1.000x | 26.06 | 26.06 | 1.000x |
| tail | 1 | 5 | 4 | 28.66 | 28.66 | 1.000x | 28.94 | 28.94 | 1.000x |
27.94 | 27.94 | 1.000x | 28.02 | 28.02 | 1.000x |
| tail | 1 | 5 | 5 | 28.96 | 28.96 | 1.000x | 28.90 | 28.90 | 1.000x |
27.89 | 27.89 | 1.000x | 27.95 | 27.95 | 1.000x |
| tail | 1 | 5 | 6 | 29.33 | 29.33 | 1.000x | 29.01 | 29.01 | 1.000x |
28.05 | 28.05 | 1.000x | 28.08 | 28.08 | 1.000x |
| tail | 1 | 5 | 7 | 29.23 | 29.23 | 1.000x | 29.30 | 29.30 | 1.000x |
28.38 | 28.38 | 1.000x | 28.46 | 28.46 | 1.000x |
| tail | 1 | 5 | 8 | 29.76 | 29.76 | 1.000x | 29.49 | 28.83 | 1.023x |
28.51 | 28.51 | 1.000x | 28.56 | 27.94 | 1.022x |
| tail | 1 | 5 | 16 | 34.96 | 34.96 | 1.000x | 34.14 | 29.04 | 1.176x |
33.39 | 33.39 | 1.000x | 32.98 | 28.08 | 1.174x |
| tail | 1 | 6 | 3 | 27.07 | 27.07 | 1.000x | 27.12 | 27.12 | 1.000x |
26.32 | 26.32 | 1.000x | 26.19 | 26.19 | 1.000x |
| tail | 1 | 6 | 4 | 28.74 | 28.74 | 1.000x | 28.98 | 28.98 | 1.000x |
28.02 | 28.02 | 1.000x | 27.98 | 27.98 | 1.000x |
| tail | 1 | 6 | 5 | 28.98 | 28.98 | 1.000x | 28.85 | 28.85 | 1.000x |
27.90 | 27.90 | 1.000x | 27.95 | 27.95 | 1.000x |
| tail | 1 | 6 | 6 | 29.01 | 29.01 | 1.000x | 29.12 | 29.12 | 1.000x |
28.05 | 28.05 | 1.000x | 28.19 | 28.19 | 1.000x |
| tail | 1 | 6 | 7 | 29.46 | 29.46 | 1.000x | 29.25 | 29.25 | 1.000x |
28.38 | 28.38 | 1.000x | 28.45 | 28.45 | 1.000x |
| tail | 1 | 6 | 8 | 29.90 | 29.90 | 1.000x | 29.44 | 28.85 | 1.021x |
28.61 | 28.61 | 1.000x | 28.24 | 27.55 | 1.025x |
| tail | 1 | 6 | 16 | 34.37 | 34.37 | 1.000x | 33.98 | 29.06 | 1.170x |
33.76 | 33.76 | 1.000x | 32.85 | 27.76 | 1.183x |
| tail | 1 | 7 | 3 | 27.06 | 27.06 | 1.000x | 26.91 | 26.91 | 1.000x |
26.69 | 26.69 | 1.000x | 26.37 | 26.37 | 1.000x |
| tail | 1 | 7 | 4 | 28.78 | 28.78 | 1.000x | 28.96 | 28.96 | 1.000x |
27.92 | 27.92 | 1.000x | 27.98 | 27.98 | 1.000x |
| tail | 1 | 7 | 5 | 29.12 | 29.12 | 1.000x | 29.06 | 29.06 | 1.000x |
27.89 | 27.89 | 1.000x | 27.95 | 27.95 | 1.000x |
| tail | 1 | 7 | 6 | 28.96 | 28.96 | 1.000x | 29.06 | 29.06 | 1.000x |
28.00 | 28.00 | 1.000x | 28.03 | 28.03 | 1.000x |
| tail | 1 | 7 | 7 | 29.76 | 29.76 | 1.000x | 29.30 | 29.30 | 1.000x |
28.27 | 28.27 | 1.000x | 28.40 | 28.40 | 1.000x |
| tail | 1 | 7 | 8 | 29.55 | 29.55 | 1.000x | 29.44 | 28.86 | 1.020x |
28.54 | 28.54 | 1.000x | 28.29 | 27.58 | 1.026x |
| tail | 1 | 7 | 16 | 34.64 | 34.64 | 1.000x | 33.98 | 29.06 | 1.170x |
33.65 | 33.65 | 1.000x | 33.04 | 27.81 | 1.188x |
| tail | 1 | 8 | 2 | 26.82 | 26.82 | 1.000x | 27.07 | 27.07 | 1.000x |
25.82 | 25.82 | 1.000x | 25.84 | 25.84 | 1.000x |
| tail | 1 | 8 | 3 | 27.74 | 27.74 | 1.000x | 27.22 | 27.22 | 1.000x |
26.69 | 26.69 | 1.000x | 26.35 | 26.35 | 1.000x |
| tail | 1 | 8 | 4 | 28.69 | 28.69 | 1.000x | 28.91 | 28.91 | 1.000x |
28.00 | 28.00 | 1.000x | 28.03 | 28.03 | 1.000x |
| tail | 1 | 8 | 5 | 28.88 | 28.88 | 1.000x | 28.94 | 28.94 | 1.000x |
28.02 | 28.02 | 1.000x | 27.92 | 27.92 | 1.000x |
| tail | 1 | 8 | 6 | 29.02 | 29.02 | 1.000x | 28.99 | 28.99 | 1.000x |
28.03 | 28.03 | 1.000x | 28.13 | 28.13 | 1.000x |
| tail | 1 | 8 | 7 | 29.74 | 29.74 | 1.000x | 29.39 | 29.39 | 1.000x |
28.40 | 28.40 | 1.000x | 28.43 | 28.43 | 1.000x |
| tail | 1 | 8 | 8 | 29.73 | 29.73 | 1.000x | 29.49 | 28.90 | 1.020x |
28.58 | 28.58 | 1.000x | 28.30 | 27.63 | 1.024x |
| tail | 1 | 8 | 16 | 35.01 | 35.01 | 1.000x | 34.21 | 29.09 | 1.176x |
33.70 | 33.70 | 1.000x | 33.26 | 27.89 | 1.193x |
| tail | 1 | 9 | 2 | 28.38 | 28.38 | 1.000x | 28.40 | 28.40 | 1.000x |
27.49 | 27.49 | 1.000x | 27.25 | 27.25 | 1.000x |
| tail | 1 | 9 | 8 | 30.16 | 30.16 | 1.000x | 29.97 | 29.97 | 1.000x |
29.38 | 29.38 | 1.000x | 29.10 | 29.10 | 1.000x |
| tail | 1 | 16 | 2 | 28.35 | 28.35 | 1.000x | 28.56 | 28.56 | 1.000x |
27.60 | 27.60 | 1.000x | 27.33 | 27.33 | 1.000x |
| tail | 1 | 16 | 8 | 30.21 | 30.21 | 1.000x | 30.08 | 30.08 | 1.000x |
29.63 | 29.63 | 1.000x | 29.66 | 29.66 | 1.000x |
| tail | 1 | 32 | 2 | 28.08 | 28.08 | 1.000x | 28.02 | 28.02 | 1.000x |
27.28 | 27.28 | 1.000x | 27.18 | 27.18 | 1.000x |
| tail | 1 | 32 | 8 | 29.98 | 29.98 | 1.000x | 30.02 | 30.02 | 1.000x |
28.99 | 28.99 | 1.000x | 29.04 | 29.04 | 1.000x |
| tail | 1 | 64 | 2 | 28.42 | 28.42 | 1.000x | 28.50 | 28.50 | 1.000x |
27.61 | 27.61 | 1.000x | 27.52 | 27.52 | 1.000x |
| tail | 1 | 64 | 8 | 30.45 | 30.45 | 1.000x | 30.64 | 30.64 | 1.000x |
29.54 | 29.54 | 1.000x | 29.46 | 29.46 | 1.000x |
| tail | 1 | 128 | 2 | 30.21 | 30.21 | 1.000x | 30.38 | 30.38 | 1.000x |
29.52 | 29.52 | 1.000x | 29.31 | 29.31 | 1.000x |
| tail | 1 | 128 | 8 | 32.94 | 32.94 | 1.000x | 33.17 | 33.17 | 1.000x |
31.89 | 31.89 | 1.000x | 31.78 | 31.78 | 1.000x |
| tail | 8 | 1 | 2 | 10.86 | 10.86 | 1.000x | 10.40 | 10.40 | 1.000x |
10.53 | 10.53 | 1.000x | 10.35 | 10.35 | 1.000x |
| tail | 8 | 1 | 5 | 13.60 | 10.54 | 1.290x | 13.07 | 10.34 | 1.265x |
13.34 | 10.35 | 1.289x | 13.54 | 10.51 | 1.288x |
| tail | 8 | 1 | 6 | 14.80 | 11.38 | 1.301x | 13.81 | 10.94 | 1.262x |
13.96 | 10.66 | 1.310x | 13.46 | 10.61 | 1.268x |
| tail | 8 | 1 | 7 | 14.66 | 11.09 | 1.322x | 14.30 | 10.96 | 1.305x |
14.42 | 10.86 | 1.327x | 14.62 | 11.07 | 1.321x |
| tail | 8 | 1 | 8 | 15.92 | 11.62 | 1.370x | 14.86 | 11.09 | 1.341x |
14.99 | 10.91 | 1.374x | 14.64 | 10.71 | 1.367x |
| tail | 8 | 1 | 16 | 20.18 | 13.17 | 1.532x | 19.21 | 12.77 | 1.504x |
19.28 | 12.43 | 1.551x | 18.82 | 12.18 | 1.544x |
| tail | 8 | 2 | 4 | 12.98 | 10.37 | 1.251x | 12.54 | 10.48 | 1.197x |
12.74 | 10.35 | 1.230x | 12.77 | 10.67 | 1.196x |
| tail | 8 | 2 | 5 | 13.47 | 10.64 | 1.266x | 13.01 | 10.56 | 1.232x |
13.25 | 10.48 | 1.264x | 13.25 | 10.69 | 1.240x |
| tail | 8 | 2 | 6 | 14.18 | 11.10 | 1.277x | 13.55 | 10.90 | 1.244x |
13.78 | 10.91 | 1.262x | 13.81 | 11.09 | 1.245x |
| tail | 8 | 2 | 7 | 14.66 | 11.09 | 1.322x | 14.02 | 11.02 | 1.271x |
14.32 | 10.93 | 1.310x | 14.22 | 11.18 | 1.272x |
| tail | 8 | 2 | 8 | 15.22 | 11.18 | 1.361x | 14.51 | 11.09 | 1.309x |
14.83 | 11.02 | 1.345x | 14.77 | 11.17 | 1.322x |
| tail | 8 | 2 | 16 | 19.76 | 13.18 | 1.499x | 18.83 | 12.77 | 1.475x |
19.30 | 12.77 | 1.511x | 18.90 | 12.70 | 1.487x |
| tail | 8 | 3 | 4 | 12.82 | 10.53 | 1.217x | 12.54 | 10.42 | 1.204x |
12.58 | 10.38 | 1.211x | 12.64 | 10.53 | 1.201x |
| tail | 8 | 3 | 5 | 13.36 | 10.67 | 1.252x | 13.04 | 10.58 | 1.233x |
13.07 | 10.50 | 1.245x | 13.09 | 10.69 | 1.225x |
| tail | 8 | 3 | 6 | 13.90 | 11.10 | 1.252x | 13.58 | 11.04 | 1.230x |
13.57 | 10.90 | 1.245x | 13.65 | 11.10 | 1.229x |
| tail | 8 | 3 | 7 | 14.45 | 11.17 | 1.294x | 14.03 | 11.06 | 1.269x |
14.10 | 10.99 | 1.282x | 14.18 | 11.15 | 1.271x |
| tail | 8 | 3 | 8 | 15.01 | 11.25 | 1.334x | 14.56 | 11.12 | 1.309x |
14.69 | 11.04 | 1.330x | 14.72 | 11.28 | 1.305x |
| tail | 8 | 3 | 16 | 19.47 | 13.20 | 1.475x | 18.74 | 12.75 | 1.469x |
18.96 | 12.77 | 1.485x | 18.83 | 12.78 | 1.473x |
| tail | 8 | 4 | 2 | 11.33 | 11.33 | 1.000x | 11.01 | 11.01 | 1.000x |
10.96 | 10.96 | 1.000x | 10.82 | 10.82 | 1.000x |
| tail | 8 | 4 | 4 | 12.74 | 10.42 | 1.223x | 12.48 | 10.32 | 1.209x |
12.43 | 10.48 | 1.186x | 12.53 | 10.54 | 1.188x |
| tail | 8 | 4 | 5 | 13.26 | 10.69 | 1.241x | 12.94 | 10.51 | 1.231x |
12.96 | 10.50 | 1.235x | 13.04 | 10.67 | 1.222x |
| tail | 8 | 4 | 6 | 14.27 | 11.41 | 1.251x | 13.60 | 11.12 | 1.223x |
13.60 | 10.90 | 1.247x | 13.25 | 10.78 | 1.228x |
| tail | 8 | 4 | 7 | 14.40 | 11.20 | 1.286x | 13.98 | 11.04 | 1.267x |
14.03 | 11.01 | 1.275x | 14.10 | 11.18 | 1.260x |
| tail | 8 | 4 | 8 | 15.41 | 11.65 | 1.323x | 14.64 | 11.26 | 1.301x |
14.65 | 11.10 | 1.319x | 14.22 | 10.86 | 1.309x |
| tail | 8 | 4 | 16 | 19.89 | 13.30 | 1.495x | 19.02 | 12.90 | 1.475x |
18.94 | 12.82 | 1.478x | 18.72 | 12.70 | 1.474x |
| tail | 8 | 5 | 2 | 11.12 | 11.12 | 1.000x | 11.06 | 11.06 | 1.000x |
10.77 | 10.77 | 1.000x | 10.80 | 10.80 | 1.000x |
| tail | 8 | 5 | 8 | 15.55 | 15.55 | 1.000x | 15.30 | 15.30 | 1.000x |
15.18 | 15.18 | 1.000x | 15.12 | 15.12 | 1.000x |
| tail | 8 | 8 | 2 | 11.12 | 11.12 | 1.000x | 10.94 | 10.94 | 1.000x |
10.82 | 10.82 | 1.000x | 10.69 | 10.69 | 1.000x |
| tail | 8 | 8 | 8 | 15.57 | 15.57 | 1.000x | 15.49 | 15.49 | 1.000x |
15.36 | 15.36 | 1.000x | 15.17 | 15.17 | 1.000x |
| tail | 8 | 9 | 2 | 11.23 | 11.23 | 1.000x | 11.01 | 11.01 | 1.000x |
10.91 | 10.91 | 1.000x | 10.82 | 10.82 | 1.000x |
| tail | 8 | 9 | 8 | 15.89 | 15.89 | 1.000x | 15.62 | 15.62 | 1.000x |
15.42 | 15.42 | 1.000x | 15.14 | 15.14 | 1.000x |
| tail | 8 | 16 | 2 | 11.25 | 11.25 | 1.000x | 11.26 | 11.26 | 1.000x |
10.98 | 10.98 | 1.000x | 10.85 | 10.85 | 1.000x |
| tail | 8 | 16 | 8 | 15.97 | 15.97 | 1.000x | 15.66 | 15.66 | 1.000x |
15.46 | 15.46 | 1.000x | 15.34 | 15.34 | 1.000x |
| tail | 8 | 32 | 2 | 11.74 | 11.74 | 1.000x | 11.62 | 11.62 | 1.000x |
11.52 | 11.52 | 1.000x | 11.46 | 11.46 | 1.000x |
| tail | 8 | 32 | 8 | 16.40 | 16.40 | 1.000x | 16.10 | 16.10 | 1.000x |
15.92 | 15.92 | 1.000x | 15.94 | 15.94 | 1.000x |
| tail | 8 | 64 | 2 | 11.87 | 11.87 | 1.000x | 11.66 | 11.66 | 1.000x |
11.63 | 11.63 | 1.000x | 11.50 | 11.50 | 1.000x |
| tail | 8 | 64 | 8 | 16.48 | 16.48 | 1.000x | 16.26 | 16.26 | 1.000x |
16.18 | 16.18 | 1.000x | 16.05 | 16.05 | 1.000x |
| tail | 8 | 128 | 2 | 13.36 | 13.36 | 1.000x | 13.22 | 13.22 | 1.000x |
13.22 | 13.22 | 1.000x | 12.90 | 12.90 | 1.000x |
| tail | 8 | 128 | 8 | 18.35 | 18.35 | 1.000x | 18.05 | 18.05 | 1.000x |
17.86 | 17.86 | 1.000x | 17.52 | 17.52 | 1.000x |

*Times are µs per call on one rank from `bench_gpu_time_with_cupti` with
cold L2 and CUDA graph replay; both sides interleave in groups over two
passes, the second in reversed order; each value is the mean of the two
per-pass medians on one GPU; changed rows measure both sides in the same
run; rows this PR does not change show the value of #7948 in both
columns; speedup = previous / this PR; decode tail rows reduce P routed
partials; NVIDIA B200 (`sm_100a`, 148 SMs), NVIDIA B300 SXM6 AC
(`sm_103a`, 148 SMs), NVIDIA GB200 (`sm_100a`, 152 SMs), NVIDIA GB300
(`sm_103a`, 152 SMs); CUDA 13.4.*

Cake also ships a TP12 fused tail of this block in `kimi_k3_tp12_tail`;
both packages are BF16 only and target `sm_100a` and `sm_103a`.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added optimized Kimi K3 latent MoE routes for supported GPU
architectures and workloads, including additional tile sizes, front-fold
variants, and split-row decode paths.
* Extended route selection to account for GPU architecture and SM count.
* **Bug Fixes**
* Improved coverage for new routes with reference comparisons, repeated
launches, and graph replay checks.
* **Documentation**
* Updated route and GPU residency guidance for the supported
configurations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [fb97a29](https://github.com/flashinfer-ai/flashinfer/commit/fb97a29c11880198696830a6f0f2cb52eb53bf6b)

- **作者**: eigen
- **时间**: 2026-10-30T07:35:29Z
- **提交信息**: perf(cake_kda): next-state prefetch, per-warp checkpoint stores and a B200 bin-mix build for BF16-input KDA prefill (#7978)

The Cake chunked KDA (Kimi Delta Attention) prefill behind
`flashinfer.recurrent_kda(..., backend="cake")` has 85 modules: 51 with
BF16 inputs and 34 with TF32 inputs. They come in a fused single-kernel
form (M128, M64 value split, N16 chain) and a split form (map prefix,
carry scan, affine apply), with FP32 or BF16 state and optional
checkpoint rows. This PR adds no module. It changes the prepared
BF16-input path with FP32 state (`flashinfer.prepare_bf16_kda_prefill`).
It adds 4 generated programs, and 3 of them replace existing programs.
The baseline is the previous Cake version on FlashInfer main. Outputs
are bit-identical to main on every measured row.

- Next-state prefetch: new builds replace the bounded work-binned direct
N32 and N16 M128 programs. If a task has at most 256 tokens, the prep
warps that run last prefetch the next task's entry state into L2 at the
end of the task.
- Per-warp checkpoint stores: a new build replaces the M128 owner/helper
program. Each warp writes its own 32 checkpoint rows.
- Bin-mix, sm_100a only: this is a new build of the unbounded
work-binned turnover program. Some CTAs have a work bin that holds only
one short task. In bin-mix, such a CTA also runs part of a longer bin's
chunks and hands the result to that bin's owner through a global ring.
The launch is cooperative, with one CTA per SM.
- Bin-mix route: a launch takes the bin-mix build only if some owner bin
paired with a single-task bin hands over g = min(8, d//2 + d//8, owner
chunks - 1) >= 1 chunks, where d = owner chunks - helper chunks. Other
launches keep their program. On GB300, every launch keeps its existing
program.

B200: NVIDIA B200, sm_100a, 148 SMs, driver 580.82.07. GB300: NVIDIA
GB300, sm_103a, 152 SMs, driver 580.159.03. CUDA 13.4 (nvcc), PyTorch
2.14.1+cu130.

| heads | gate lower bound | sequence lengths | B200 main | B200 this PR
| speedup | GB300 main | GB300 this PR | speedup |
|---:|---|---|---:|---:|---:|---:|---:|---:|
| 12 | none | 8192 | 219.04 | 219.23 | 1.00x TIE | 212.09 | 212.13 |
1.00x TIE |
| 12 | none | 16384 | 377.66 | 378.08 | 1.00x TIE | 360.16 | 360.35 |
1.00x TIE |
| 12 | none | 32768 | 683.18 | 683.96 | 1.00x TIE | 645.44 | 645.79 |
1.00x TIE |
| 12 | none | 2x8192 | 371.10 | 371.13 | 1.00x TIE | 359.66 | 359.68 |
1.00x TIE |
| 12 | none | 3000+13384 | 391.90 | 392.22 | 1.00x TIE | 382.83 | 383.39
| 1.00x TIE |
| 12 | none | 4x4096 | 251.01 | 233.92 | 1.07x | 235.79 | 218.94 | 1.08x
|
| 12 | none | 2x(8128+64) | 375.13 | 375.10 | 1.00x TIE | 363.73 |
364.70 | 1.00x TIE |
| 12 | none | 8x(1024+64) | 107.36 | 107.33 | 1.00x TIE | 101.76 |
101.71 | 1.00x TIE |
| 12 | none | BS4 x T64 | 16.13 | 16.13 | 1.00x TIE | 15.20 | 15.23 |
1.00x TIE |
| 12 | none | BS16 x T64 | 25.34 | 22.82 | 1.11x | 23.17 | 23.17 | 1.00x
TIE |
| 12 | none | BS64 x T64 | 59.10 | 59.07 | 1.00x TIE | 54.11 | 54.18 |
1.00x TIE |
| 12 | none | BS16 x T128 | 38.21 | 36.29 | 1.05x | 34.14 | 34.24 |
1.00x TIE |
| 12 | none | BS16 x T256 | 64.13 | 56.54 | 1.13x | 56.67 | 56.67 |
1.00x TIE |
| 12 | none | BS16 x T(17..255) | 37.31 | 37.31 | 1.00x TIE | 35.23 |
35.23 | 1.00x TIE |
| 16 | none | 8192 | 268.51 | 268.25 | 1.00x TIE | 260.42 | 260.64 |
1.00x TIE |
| 16 | none | 16384 | 464.11 | 463.79 | 1.00x TIE | 443.22 | 443.84 |
1.00x TIE |
| 16 | none | 32768 | 874.97 | 873.90 | 1.00x TIE | 822.42 | 821.89 |
1.00x TIE |
| 16 | none | 2x8192 | 484.92 | 484.84 | 1.00x TIE | 466.02 | 466.50 |
1.00x TIE |
| 16 | none | 3000+13384 | 476.44 | 476.73 | 1.00x TIE | 453.39 | 453.25
| 1.00x TIE |
| 16 | none | 4x4096 | 264.22 | 264.19 | 1.00x TIE | 245.76 | 245.81 |
1.00x TIE |
| 16 | none | 2x(8128+64) | 489.34 | 489.05 | 1.00x TIE | 470.42 |
471.01 | 1.00x TIE |
| 16 | none | 8x(1024+64) | 111.55 | 111.50 | 1.00x TIE | 104.48 |
104.46 | 1.00x TIE |
| 16 | none | BS4 x T64 | 16.32 | 16.32 | 1.00x TIE | 15.42 | 15.42 |
1.00x TIE |
| 16 | none | BS16 x T64 | 25.76 | 25.79 | 1.00x TIE | 23.55 | 23.55 |
1.00x TIE |
| 16 | none | BS64 x T64 | 68.86 | 68.90 | 1.00x TIE | 65.34 | 65.38 |
1.00x TIE |
| 16 | none | BS16 x T128 | 39.14 | 39.10 | 1.00x TIE | 35.33 | 35.33 |
1.00x TIE |
| 16 | none | BS16 x T256 | 65.95 | 66.02 | 1.00x TIE | 58.62 | 58.67 |
1.00x TIE |
| 16 | none | BS16 x T(17..255) | 41.70 | 41.63 | 1.00x TIE | 37.34 |
37.36 | 1.00x TIE |
| 12 | -5 | 8192 | 159.04 | 159.97 | 0.99x TIE | 155.71 | 156.45 | 1.00x
TIE |
| 12 | -5 | 16384 | 260.64 | 261.12 | 1.00x TIE | 254.13 | 253.82 |
1.00x TIE |
| 12 | -5 | 32768 | 454.14 | 454.32 | 1.00x TIE | 436.38 | 435.84 |
1.00x TIE |
| 12 | -5 | 2x8192 | 282.53 | 282.53 | 1.00x TIE | 251.20 | 250.53 |
1.00x TIE |
| 12 | -5 | 3000+13384 | 273.56 | 273.53 | 1.00x TIE | 264.06 | 263.76 |
1.00x TIE |
| 12 | -5 | 4x4096 | 198.30 | 198.24 | 1.00x TIE | 180.06 | 180.06 |
1.00x TIE |
| 12 | -5 | 2x(8128+64) | 364.92 | 364.89 | 1.00x TIE | 251.86 | 252.02
| 1.00x TIE |
| 12 | -5 | 8x(1024+64) | 110.40 | 110.43 | 1.00x TIE | 103.14 | 103.10
| 1.00x TIE |
| 12 | -5 | BS4 x T64 | 11.23 | 11.23 | 1.00x TIE | 10.50 | 10.50 |
1.00x TIE |
| 12 | -5 | BS16 x T64 | 28.16 | 27.68 | 1.02x | 26.69 | 25.94 | 1.03x |
| 12 | -5 | BS64 x T64 | 73.82 | 67.74 | 1.09x | 69.41 | 63.14 | 1.10x |
| 12 | -5 | BS16 x T128 | 33.28 | 33.25 | 1.00x TIE | 31.23 | 31.20 |
1.00x TIE |
| 12 | -5 | BS16 x T256 | 47.79 | 47.74 | 1.00x TIE | 44.93 | 44.90 |
1.00x TIE |
| 12 | -5 | BS16 x T(17..255) | 30.88 | 30.91 | 1.00x TIE | 29.41 |
29.41 | 1.00x TIE |
| 16 | -5 | 8192 | 194.88 | 194.91 | 1.00x TIE | 191.76 | 192.06 | 1.00x
TIE |
| 16 | -5 | 16384 | 321.63 | 321.82 | 1.00x TIE | 306.53 | 306.46 |
1.00x TIE |
| 16 | -5 | 32768 | 582.38 | 578.14 | 1.01x TIE | 552.10 | 550.91 |
1.00x TIE |
| 16 | -5 | 2x8192 | 285.95 | 286.37 | 1.00x TIE | 273.50 | 273.70 |
1.00x TIE |
| 16 | -5 | 3000+13384 | 333.72 | 333.21 | 1.00x TIE | 322.26 | 323.30 |
1.00x TIE |
| 16 | -5 | 4x4096 | 205.66 | 205.65 | 1.00x TIE | 182.27 | 182.27 |
1.00x TIE |
| 16 | -5 | 2x(8128+64) | 360.86 | 360.80 | 1.00x TIE | 341.44 | 341.50
| 1.00x TIE |
| 16 | -5 | 8x(1024+64) | 88.64 | 88.64 | 1.00x TIE | 76.38 | 76.32 |
1.00x TIE |
| 16 | -5 | BS4 x T64 | 11.62 | 11.62 | 1.00x TIE | 10.82 | 10.82 |
1.00x TIE |
| 16 | -5 | BS16 x T64 | 25.82 | 24.99 | 1.03x | 24.00 | 23.30 | 1.03x |
| 16 | -5 | BS64 x T64 | 72.03 | 67.58 | 1.07x | 67.65 | 63.94 | 1.06x |
| 16 | -5 | BS16 x T128 | 34.14 | 34.14 | 1.00x TIE | 32.10 | 32.06 |
1.00x TIE |
| 16 | -5 | BS16 x T256 | 48.93 | 48.96 | 1.00x TIE | 45.82 | 45.86 |
1.00x TIE |
| 16 | -5 | BS16 x T(17..255) | 36.74 | 36.29 | 1.01x | 34.21 | 33.78 |
1.01x |

- B200: speedup 0.99x .. 1.13x over 56 rows (9 faster, 47 TIE: no
difference beyond the measurement band)
- GB300: speedup 1.00x .. 1.10x over 56 rows (6 faster, 50 TIE: no
difference beyond the measurement band)

The kernel's other Cake variants, the TF32-input modules and the
BF16-state forms, keep their behavior; the family ships on sm_100a and
sm_103a, and this PR covers both.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added an optimized work-bin mixing option for eligible KDA prefill
workloads on supported hardware.
* **Performance Improvements**
* Improved prefill scheduling and initial-state handling for selected
workloads.
* **Reliability**
* When the device driver cannot run the optimized option, execution
falls back to the standard turnover path.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Avery Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [96f25e1](https://github.com/flashinfer-ai/flashinfer/commit/96f25e197b62550c3a5209d1deee1fd99ed8ba9e)

- **作者**: eigen
- **时间**: 2026-10-30T07:04:00Z
- **提交信息**: perf(cake_moe_grouped_gemm): probed die split of the tile queues for the sm_103a dgrad down projection (#7975)

FlashInfer's experimental ragged BF16 MoE grouped GEMM has a Cake
backend (`flashinfer.experimental.cake_moe_grouped_gemm`, also reached
through `grouped_mm_bf16(..., backend="cake")`) with four variants. They
are three operations over E groups of rows given by device offsets: the
forward Y = X W[e]^T and the data gradient dX = G W[e], both with BF16
output, and the weight gradient dW[e] = G^T X, with BF16 or FP32 output.
This PR makes a host-side change on sm_103a (GB300) only, for the data
gradient of the down projection (weights of at most 6144 x 2048 elements
per group). The domain-scheduled program splits each row block's tiles
between two claim queues, one per die. Until now the host always passed
an even split. GB300 dies can hold unequal SM pair counts (for example
36 / 40), so this PR runs a short probe once per stream workspace to
measure each die's pair count and passes those counts as the split.
Kernels and output bits are unchanged, and GPUs whose two dies hold
equal SM pair counts keep the even split's behavior. The baseline (main
in the table) is the Cake version currently on FlashInfer main, which
includes PR #7881. It was timed in the same process on the same GPU,
interleaved with this PR, over the package's 58 shape rows; latency is
the median kernel time with a cold L2. The bold rows are the 9
data-gradient down-projection rows, which take the probed split. Their
medians are 1.007x-1.040x faster, and each of them is faster in every
interleaved round on both GPUs. The other 49 rows run exactly what main
runs, and their readings of 0.993x-1.007x are measurement spread.

NVIDIA GB300, sm_103a, CUDA 13.4 (node 1 and node 2 are two different
GB300 GPUs, each with a 36 / 40 die split):

| shape | GB300 node 1: main ms | GB300 node 1: this PR ms | GB300 node
1: speedup | GB300 node 2: main ms | GB300 node 2: this PR ms | GB300
node 2: speedup |
|---|---:|---:|---:|---:|---:|---:|
| fwd gate_up (N=4096, K=6144), E=4, M=112576, balanced | 3.3291 |
3.3271 | 1.001x | 3.2870 | 3.2815 | 1.002x |
| fwd gate_up (N=4096, K=6144), E=4, M=112576, skewed | 3.3279 | 3.3271
| 1.000x | 3.2810 | 3.2847 | 0.999x |
| fwd gate_up (N=4096, K=6144), E=4, M=112576, one-empty | 3.3277 |
3.3266 | 1.000x | 3.2752 | 3.2788 | 0.999x |
| fwd gate_up (N=4096, K=6144), E=4, M=136064, balanced | 4.0133 |
4.0138 | 1.000x | 4.0650 | 4.0672 | 0.999x |
| fwd gate_up (N=4096, K=6144), E=4, M=136064, skewed | 4.0297 | 4.0291
| 1.000x | 4.0196 | 4.0261 | 0.998x |
| fwd gate_up (N=4096, K=6144), E=4, M=136064, one-empty | 4.0269 |
4.0303 | 0.999x | 4.0119 | 4.0184 | 0.998x |
| dgrad gate_up (N=4096, K=6144), E=4, M=112576, balanced | 3.2695 |
3.2745 | 0.998x | 3.2507 | 3.2508 | 1.000x |
| dgrad gate_up (N=4096, K=6144), E=4, M=112576, skewed | 3.2619 |
3.2642 | 0.999x | 3.2431 | 3.2454 | 0.999x |
| dgrad gate_up (N=4096, K=6144), E=4, M=112576, one-empty | 3.2632 |
3.2668 | 0.999x | 3.2429 | 3.2454 | 0.999x |
| dgrad gate_up (N=4096, K=6144), E=4, M=136064, balanced | 3.9688 |
3.9703 | 1.000x | 3.9121 | 3.9076 | 1.001x |
| dgrad gate_up (N=4096, K=6144), E=4, M=136064, skewed | 3.9769 |
3.9775 | 1.000x | 3.9373 | 3.9271 | 1.003x |
| dgrad gate_up (N=4096, K=6144), E=4, M=136064, one-empty | 3.9708 |
3.9720 | 1.000x | 3.9191 | 3.9256 | 0.998x |
| wgrad gate_up (N=4096, K=6144), E=4, M=112576, balanced | 3.3243 |
3.3258 | 1.000x | 3.2773 | 3.2776 | 1.000x |
| wgrad gate_up (N=4096, K=6144), E=4, M=112576, skewed | 3.4330 |
3.4341 | 1.000x | 3.3771 | 3.3751 | 1.001x |
| wgrad gate_up (N=4096, K=6144), E=4, M=112576, one-empty | 3.4198 |
3.4238 | 0.999x | 3.4195 | 3.4227 | 0.999x |
| wgrad gate_up (N=4096, K=6144), E=4, M=136064, balanced | 4.0161 |
4.0168 | 1.000x | 4.0908 | 4.0906 | 1.000x |
| wgrad gate_up (N=4096, K=6144), E=4, M=136064, skewed | 4.1491 |
4.1523 | 0.999x | 4.1032 | 4.1042 | 1.000x |
| wgrad gate_up (N=4096, K=6144), E=4, M=136064, one-empty | 4.1335 |
4.1377 | 0.999x | 4.1303 | 4.1576 | 0.993x |
| fwd down (N=6144, K=2048), E=4, M=112576, balanced | 1.6475 | 1.6598 |
0.993x | 1.6445 | 1.6451 | 1.000x |
| fwd down (N=6144, K=2048), E=4, M=112576, skewed | 1.6457 | 1.6440 |
1.001x | 1.6410 | 1.6421 | 0.999x |
| fwd down (N=6144, K=2048), E=4, M=112576, one-empty | 1.6453 | 1.6542
| 0.995x | 1.6413 | 1.6432 | 0.999x |
| fwd down (N=6144, K=2048), E=4, M=136064, balanced | 2.0056 | 2.0071 |
0.999x | 1.9866 | 1.9852 | 1.001x |
| fwd down (N=6144, K=2048), E=4, M=136064, skewed | 2.0117 | 2.0119 |
1.000x | 1.9878 | 1.9916 | 0.998x |
| fwd down (N=6144, K=2048), E=4, M=136064, one-empty | 2.0082 | 2.0099
| 0.999x | 1.9830 | 1.9851 | 0.999x |
| **dgrad down (N=6144, K=2048), E=4, M=112576, balanced** | 1.6591 |
1.6390 | 1.012x | 1.6458 | 1.6302 | 1.010x |
| **dgrad down (N=6144, K=2048), E=4, M=112576, skewed** | 1.6573 |
1.6395 | 1.011x | 1.6422 | 1.6305 | 1.007x |
| **dgrad down (N=6144, K=2048), E=4, M=112576, one-empty** | 1.6572 |
1.6384 | 1.012x | 1.6423 | 1.6307 | 1.007x |
| **dgrad down (N=6144, K=2048), E=4, M=136064, balanced** | 2.0330 |
1.9550 | 1.040x | 1.9738 | 1.9546 | 1.010x |
| **dgrad down (N=6144, K=2048), E=4, M=136064, skewed** | 2.0287 |
1.9854 | 1.022x | 2.0221 | 1.9805 | 1.021x |
| **dgrad down (N=6144, K=2048), E=4, M=136064, one-empty** | 2.0289 |
1.9812 | 1.024x | 2.0154 | 1.9733 | 1.021x |
| wgrad down (N=6144, K=2048), E=4, M=112576, balanced | 1.6473 | 1.6492
| 0.999x | 1.6477 | 1.6472 | 1.000x |
| wgrad down (N=6144, K=2048), E=4, M=112576, skewed | 1.6780 | 1.6804 |
0.999x | 1.6693 | 1.6733 | 0.998x |
| wgrad down (N=6144, K=2048), E=4, M=112576, one-empty | 1.6590 |
1.6602 | 0.999x | 1.6510 | 1.6517 | 1.000x |
| wgrad down (N=6144, K=2048), E=4, M=136064, balanced | 2.0271 | 2.0281
| 1.000x | 1.9879 | 1.9883 | 1.000x |
| wgrad down (N=6144, K=2048), E=4, M=136064, skewed | 2.0249 | 2.0303 |
0.997x | 2.0226 | 2.0227 | 1.000x |
| wgrad down (N=6144, K=2048), E=4, M=136064, one-empty | 2.0037 |
2.0050 | 0.999x | 2.0019 | 2.0035 | 0.999x |
| wgrad gate_up (N=4096, K=6144), E=4, M=112576, balanced, FP32 dW |
3.3755 | 3.3751 | 1.000x | 3.3308 | 3.3399 | 0.997x |
| wgrad gate_up (N=4096, K=6144), E=4, M=136064, balanced, FP32 dW |
4.0761 | 4.0768 | 1.000x | 4.1440 | 4.1443 | 1.000x |
| wgrad down (N=6144, K=2048), E=4, M=112576, balanced, FP32 dW | 1.6758
| 1.6768 | 0.999x | 1.6793 | 1.6795 | 1.000x |
| wgrad down (N=6144, K=2048), E=4, M=136064, balanced, FP32 dW | 2.0586
| 2.0589 | 1.000x | 2.0231 | 2.0233 | 1.000x |
| fwd gate_up (N=4096, K=6144), E=8, M=131072, balanced | 3.8575 |
3.8558 | 1.000x | 3.8030 | 3.7955 | 1.002x |
| dgrad gate_up (N=4096, K=6144), E=8, M=131072, balanced | 3.8102 |
3.8091 | 1.000x | 3.8025 | 3.7763 | 1.007x |
| wgrad gate_up (N=4096, K=6144), E=8, M=131072, balanced | 3.8634 |
3.8655 | 0.999x | 3.7785 | 3.7950 | 0.996x |
| fwd down (N=6144, K=2048), E=8, M=131072, balanced | 1.9366 | 1.9372 |
1.000x | 1.9173 | 1.9167 | 1.000x |
| **dgrad down (N=6144, K=2048), E=8, M=131072, balanced** | 1.9811 |
1.9294 | 1.027x | 1.9042 | 1.8714 | 1.018x |
| wgrad down (N=6144, K=2048), E=8, M=131072, balanced | 1.9519 | 1.9516
| 1.000x | 1.9129 | 1.9189 | 0.997x |
| fwd gate_up (N=4096, K=6144), E=16, M=131072, balanced | 3.8767 |
3.8711 | 1.001x | 3.8356 | 3.8363 | 1.000x |
| dgrad gate_up (N=4096, K=6144), E=16, M=131072, balanced | 3.8234 |
3.8287 | 0.999x | 3.7960 | 3.8108 | 0.996x |
| wgrad gate_up (N=4096, K=6144), E=16, M=131072, balanced | 3.8841 |
3.8820 | 1.001x | 3.8121 | 3.8280 | 0.996x |
| fwd down (N=6144, K=2048), E=16, M=131072, balanced | 1.9450 | 1.9444
| 1.000x | 1.9347 | 1.9327 | 1.001x |
| **dgrad down (N=6144, K=2048), E=16, M=131072, balanced** | 1.9866 |
1.9333 | 1.028x | 1.9208 | 1.8900 | 1.016x |
| wgrad down (N=6144, K=2048), E=16, M=131072, balanced | 1.9578 |
1.9576 | 1.000x | 1.9190 | 1.9174 | 1.001x |
| fwd gate_up (N=4096, K=6144), E=32, M=131072, balanced | 3.9531 |
3.9531 | 1.000x | 3.9302 | 3.9305 | 1.000x |
| dgrad gate_up (N=4096, K=6144), E=32, M=131072, balanced | 3.9312 |
3.9318 | 1.000x | 3.9453 | 3.9462 | 1.000x |
| wgrad gate_up (N=4096, K=6144), E=32, M=131072, balanced | 3.9135 |
3.9053 | 1.002x | 3.8264 | 3.8347 | 0.998x |
| fwd down (N=6144, K=2048), E=32, M=131072, balanced | 1.9485 | 1.9494
| 1.000x | 1.9730 | 1.9732 | 1.000x |
| **dgrad down (N=6144, K=2048), E=32, M=131072, balanced** | 1.9910 |
1.9396 | 1.026x | 1.9644 | 1.9074 | 1.030x |
| wgrad down (N=6144, K=2048), E=32, M=131072, balanced | 1.9699 |
1.9691 | 1.000x | 1.9327 | 1.9321 | 1.000x |

Cake ships all four variants of this kernel for sm_100a, sm_103a and
sm_107a, and this PR changes only the sm_103a data-gradient
down-projection routing.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Eligible data-gradient launches can use a measured queue split based
on GPU locality. Until measurements are available—or when probing is
unavailable or incomplete—launches retain the even split. Results remain
unchanged, and CUDA graph capture does not start a probe.
* Added a query for checking the probed queue split on a device and
stream.
* **Documentation**
* Updated guidance on when locality-based splitting applies and when
launches use the even split.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-10-31
**监控日期**: 2026-10-30
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4763
- **最后更新**: 2026-10-31T00:22:45Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-10-31
**监控日期**: 2026-10-30
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34843
- **最后更新**: 2026-10-31T01:08:06Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-10-31
**监控日期**: 2026-10-30
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 432
- **最后更新**: 2026-10-19T05:38:59Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-10-31
**监控日期**: 2026-10-30
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13325
- **最后更新**: 2026-10-30T18:42:07Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-10-31
**监控日期**: 2026-10-30
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 38308
- **最后更新**: 2026-10-31T01:19:20Z

## 提交统计

- **昨日提交总数**: 61
- **提交者数量**: 32
- **主要提交者**: fzyzcjy, Avaya Aggarwal, Michael

## AI分析总结

# SGLang 昨日提交综合分析（61 个提交）

## 一、主要更新类型分布

整体以**Bug 修复**（约 23 条）和**性能优化**（约 13 条）为主，辅以**功能新增**（约 11 条）、**文档**（5 条）、测试/CI/重构/杂项若干。整体格局是"核心推理链路持续打磨 + 新模型与新硬件不断铺开"双线推进，并伴有 CI 分层化等工程收敛实践。

## 二、关键变更点及与项目方向的关系

- **Rust 服务端快速成熟**：native `/generate` 钩子、日志概率扁平化输出、指标刷新竞争修复、多节点 DP attention 下 `/v1/loads`、调度器逐请求统计上报等，表明 Rust 版服务层正被推向生产可用，以更低开销衔接外部生态。
- **PD 分离与调度器优化**：去除最后 chunk 状态页索引的 host 同步、overlap 下无同步发布解码 KV 目标位置、hicache 预填充提前发布，均指向减少 CPU/GPU 同步点这一核心性能主线；调度器移除 PD 复用、队列弹出中止就地完成、修复回收请求 KV 重建失败时的中止逻辑，提升了请求生命周期管理的正确性。
- **CUDA Graph 正确性与性能并重**：去重可执行图在私有流预上传、attention 元数据与 SP 工作区跨图变体保活、新增生命周期验证工具，说明 graph 捕获已成为高风险高收益区域，需要工具化保障。
- **多模态与扩散模型扩张**：HunyuanImage-3 前缀 KV 缓存与 FA3、Wan-Animate-2 解码裁剪、LTX-2.5 原生 Gemma 文本编码器、Qwen3-VL 视觉特征跨请求缓存跳过等，体现项目向多模态推理纵深发展。
- **多硬件生态铺开**：NVIDIA H20 块 FP8 Triton 配置、AMD mono-kernel 与 AITER CI 修复、Intel XPU 测试整合、Ascend 950 DSpark 支持；此外将 Kimi-K2.5 MXFP4 BCG 测试从 PR 阶段迁至 nightly，体现 AMD/MXFP4 等前沿量化路线的持续验证与 CI 分层优化。
- **RL 与运维可观测性**：权重按名哈希校验、prompt KV 权重版本上报、KV-canary 透传、调度器迭代总数指标，为强化学习闭环与线上运维提供数据基础。

## 三、值得关注的技术点

- 用**私有 CUDA 流并行上传去重后的 graph 可执行体**隐藏首次启动成本。
- **无 host 同步的 KV 目的地/页索引发布**依赖 overlap 调度的正确时序假设。
- detokenizer 改为**一次性接收扁平列 + 行偏移**，减少每步传输量。
- ragged-verify 超出捕获 grid 时**回退 eager** 的健壮性策略。
- 分解式部署中**每 chunk 状态页索引拷贝的批量化**。
- msgpack IPC 下多模态载荷与权重 dtype 往返一致性处理。
- **MXFP4**（AMD 块缩放 FP4）与 Kimi-K2.5 组合的量化正确性测试，反映低比特推理路线的验证深度。
- **CI 分层**（PR smoke vs nightly full）：平衡覆盖面与迭代速度，降低贡献者反馈周期。

## 四、对项目的影响与潜在意义

这些提交共同降低同步开销与内存复制成本，直接提升吞吐与首 token 延迟；调度器与 CUDA Graph 修复减少罕见但严重的失败模式；Rust 服务端完善使高性能核心与外部接口（Anthropic 兼容、hooks、指标）衔接更紧密；CI 优化与 AMD 后端投入则为高频功能合入提供稳定的质量基线，虽量化回归可能延后到 nightly 暴露，但整体换取了更快的 PR 反馈。扩散模型与新硬件支持拓宽了 SGLang 的适用边界。

## 五、总体评估

结合"为 LLM 与多模态模型提供快速推理"的定位，本批提交表明 SGLang 正从"能跑"向"高可靠、高吞吐、多后端"阶段演进：性能主线聚焦同步消除与数据通路精简，稳定性主线聚焦请求生命周期与图捕获边界，生态主线覆盖更多模型、量化格式与硬件，并通过 CI 分层化保障工程效率。这些改进共同巩固了项目在高吞吐推理服务领域的竞争力，为更大规模部署和 RL 训练一体化奠定基础。

## 详细提交记录

### [a959f31](https://github.com/sgl-project/sglang/commit/a959f319f4bd4c44ebfa4b44f6067725fb097468)

- **作者**: Yuan Luo
- **时间**: 2026-10-30T23:51:54Z
- **提交信息**: [Perf] GLM-5.3: Restore TP decode fusion and graph sizing with CP prefill (#46857)

Co-authored-by: luoyuan.luo <luoyuan.luo@antgroup.com>
Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

### [3e83f3a](https://github.com/sgl-project/sglang/commit/3e83f3a71a15b3bac41d040afae290c745eadc9d)

- **作者**: metamergebot
- **时间**: 2026-10-30T23:41:38Z
- **提交信息**: [Perf] pd: Copy the last chunk's state page indices to the host without a scheduler sync (#47177)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: pranjalssh <pranjalssh@users.noreply.github.com>

### [319b982](https://github.com/sgl-project/sglang/commit/319b98226f9e2feaf3b6179f7d41798f8ee8cbeb)

- **作者**: Bryan
- **时间**: 2026-10-30T23:37:20Z
- **提交信息**: [Perf] [NVIDIA] moe: Add H20 block-FP8 Triton configs for Qwen3-30B-A3B (#47070)

Co-authored-by: bryanzhao <bryanzhao@tencent.com>

### [9897930](https://github.com/sgl-project/sglang/commit/98979301a188f3d98f41a83ea00c1ca4eb4adefd)

- **作者**: Baizhou Zhang
- **时间**: 2026-10-30T23:36:58Z
- **提交信息**: [Feat] muse-spark: Infer hardware launch defaults and simplify cookbook recipes (#45683)

### [be556ff](https://github.com/sgl-project/sglang/commit/be556ff0e9ce48716149e824d054ceda555b38cb)

- **作者**: metamergebot
- **时间**: 2026-10-30T23:35:19Z
- **提交信息**: [Perf] cuda-graph: Upload each deduplicated executable on a private stream before its first launch (#47295)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: pranjalssh <pranjalssh@users.noreply.github.com>

### [b5a0c9d](https://github.com/sgl-project/sglang/commit/b5a0c9dc18832959d71df69faca1ce07e043c97c)

- **作者**: Avaya Aggarwal
- **时间**: 2026-10-30T23:25:25Z
- **提交信息**: [Fix] diffusion: LoRA merge cache key identity and eviction (#45834)

### [e83c9d5](https://github.com/sgl-project/sglang/commit/e83c9d57bcd9efaf3a3f1552b8800021d7543fc7)

- **作者**: Christopher Krah
- **时间**: 2026-10-30T23:22:42Z
- **提交信息**: [Fix] multimodal: Return 400 for images Pillow refuses as decompression bombs (#43866)

Signed-off-by: Christopher Krah <48338417+chrikrah@users.noreply.github.com>
Co-authored-by: Lianmin Zheng <lianminzheng@gmail.com>

### [c105a91](https://github.com/sgl-project/sglang/commit/c105a91b436c3af8dea28bbc829462db6eac38b0)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-30T23:19:32Z
- **提交信息**: [Fix] scheduler: Abort retracted requests whose KV the recompute cannot rebuild (#47521)

### [9f44526](https://github.com/sgl-project/sglang/commit/9f445266c2556a377b2aa16410b77f0c0ff92f78)

- **作者**: metamergebot
- **时间**: 2026-10-30T23:13:17Z
- **提交信息**: [Perf] hicache: Publish prefill read-done when offload copies are fenced on the forward stream (#46884)

Co-authored-by: metamergebot <metamergebot@users.noreply.github.com>
Co-authored-by: ZYHowell <ZYHowell@users.noreply.github.com>

### [6441f6b](https://github.com/sgl-project/sglang/commit/6441f6ba8dbbe5b16219eec794e7c76885e5fa97)

- **作者**: metamergebot
- **时间**: 2026-10-30T23:08:01Z
- **提交信息**: [Feat] fpm: Retain captured intervals and support multiple FpmTiming listeners (#47353)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: larryliu0820 <larryliu0820@users.noreply.github.com>

### [05fb1c9](https://github.com/sgl-project/sglang/commit/05fb1c98ad0605d79c5475c11201fdf3758eb195)

- **作者**: Baizhou Zhang
- **时间**: 2026-10-30T23:05:38Z
- **提交信息**: [Doc] cookbook: add Muse Spark unified memory control (#45360)

### [47783ad](https://github.com/sgl-project/sglang/commit/47783adde0adcd678f81589a67163fe7493f55b3)

- **作者**: Yanbin Jiang
- **时间**: 2026-10-30T23:04:43Z
- **提交信息**: [Test] cuda-graph: Add a standalone CUDA-graph lifetime validation tool and its skill (#46721)

### [e4bb047](https://github.com/sgl-project/sglang/commit/e4bb0478c5893d0387310f280a9073c21104b83c)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-30T22:57:14Z
- **提交信息**: [Fix] spec: Seed the DSpark MLA draft weights in the verify-rows test (#47540)

### [a076243](https://github.com/sgl-project/sglang/commit/a076243ceacf376b9632d8da37dc8e17005595bd)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-30T22:56:50Z
- **提交信息**: [Refactor] scheduler: Remove PD multiplexing (#43898)

### [93aefdf](https://github.com/sgl-project/sglang/commit/93aefdf0c540ac50cfdbf918604cccac8dac0d2c)

- **作者**: Baizhou Zhang
- **时间**: 2026-10-30T22:55:21Z
- **提交信息**: [Doc] cookbook: Use latest image for Muse Spark Open deployment (#47539)

### [783b390](https://github.com/sgl-project/sglang/commit/783b3905b14ab0383b604bf45dfe873393680922)

- **作者**: I-Ting
- **时间**: 2026-10-30T22:50:50Z
- **提交信息**: [Perf] srt: Native tensor output and prefill scoring optimizations (#42248)

Co-authored-by: I-Ting Chen <ichen@linkedin.com>
Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>
Co-authored-by: Sundara Raman Ramachandran <sundar24295@gmail.com>
Co-authored-by: t06085 <272660760+t06085@users.noreply.github.com>

### [c096c8f](https://github.com/sgl-project/sglang/commit/c096c8fda719b9b9a06a1121929c5e4e2b68193e)

- **作者**: shodoco
- **时间**: 2026-10-30T22:39:44Z
- **提交信息**: [Fix] rust-server: Give the mixed-logprob frame test's payload flat output ids with row offsets (#47537)

### [a351797](https://github.com/sgl-project/sglang/commit/a3517976f8a84c0e8050746c410674fe40dcb14f)

- **作者**: metamergebot
- **时间**: 2026-10-30T21:46:12Z
- **提交信息**: [Fix] rust-server: Let an HTTP layer start a native /generate request's timing (#47160)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>
Co-authored-by: Lu Fang <30275821+houseroad@users.noreply.github.com>

### [6fb0fd9](https://github.com/sgl-project/sglang/commit/6fb0fd97fdc5ef0336663fb8134ead490956816a)

- **作者**: metamergebot
- **时间**: 2026-10-30T21:34:19Z
- **提交信息**: [Fix] bench: Size the one-batch KV-capacity skip by the heaviest attention-DP rank for ragged batches (#47130)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: luccafong <luccafong@users.noreply.github.com>

### [7146002](https://github.com/sgl-project/sglang/commit/7146002be8a7c65a482c27778eadb21fcf34034d)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-30T21:09:44Z
- **提交信息**: [Refactor] scheduler: Finish queue-popped aborts in place (#43897)

### [039f1f7](https://github.com/sgl-project/sglang/commit/039f1f786d8ff964ca16bc023268f7710dd6e874)

- **作者**: metamergebot
- **时间**: 2026-10-30T21:06:10Z
- **提交信息**: [Feat] rust-server: Give the native /generate hook the request, its headers and its outcome (#47112)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [734aa55](https://github.com/sgl-project/sglang/commit/734aa5503ea8a299d1f742962f4f73a27bb0c7f8)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-30T20:46:00Z
- **提交信息**: [Fix] ipc: Make multimodal payloads, hidden states and weight-update dtypes round-trip under msgpack IPC (#47445)

### [76820e8](https://github.com/sgl-project/sglang/commit/76820e89a97b652d62a54b3990edb3c5d065860d)

- **作者**: metamergebot
- **时间**: 2026-10-30T20:45:26Z
- **提交信息**: [Feat] rust-server: Report the scheduler's per-request stats in native /generate meta_info (#46963)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [60e84e9](https://github.com/sgl-project/sglang/commit/60e84e91cd41ea85203b1954d5d4e1a502c20c09)

- **作者**: Avaya Aggarwal
- **时间**: 2026-10-30T20:24:30Z
- **提交信息**: [Perf] diffusion: HunyuanImage-3 prefix K/V cache, opt-in FA3 attention and think-prompt support (#46454)

### [a8d944f](https://github.com/sgl-project/sglang/commit/a8d944f5e4a027a1e069b19e115919fbdf793510)

- **作者**: Qiaolin Yu
- **时间**: 2026-10-30T20:21:12Z
- **提交信息**: [Fix] Spec: Fall back to eager when the ragged-verify tier exceeds the captured grid (#47333)

### [5628058](https://github.com/sgl-project/sglang/commit/56280587141d2eb558ffcfee99c60e48b54a8ba6)

- **作者**: Zhang, Jiejing
- **时间**: 2026-10-30T20:11:40Z
- **提交信息**: [Doc] [AMD] cookbook: Add DCP4 to the GLM-5.2 MI355X MXFP4 high-throughput recipe (#47331)

### [8ecabd3](https://github.com/sgl-project/sglang/commit/8ecabd3c1e1227ca91b0bbb48d75cf33b4626a73)

- **作者**: Yanbin Jiang
- **时间**: 2026-10-30T19:32:29Z
- **提交信息**: [Fix] cuda-graph: Keep attention metadata and SP workspaces alive across graph variants of a batch size (#46720)

### [dde1ef2](https://github.com/sgl-project/sglang/commit/dde1ef21a03da18fe226308fb27043013297e38e)

- **作者**: metamergebot
- **时间**: 2026-10-30T17:57:43Z
- **提交信息**: [Fix] rust-server: Serve /v1/loads from every listener under multi-node DP attention (#47319)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [60a347b](https://github.com/sgl-project/sglang/commit/60a347b6f304e7fd953c5cf823081cf90a2ad0b2)

- **作者**: metamergebot
- **时间**: 2026-10-30T17:57:37Z
- **提交信息**: [Perf] rust-server: Flatten egress logprob columns only for rows that carry them (#47106)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [dfade83](https://github.com/sgl-project/sglang/commit/dfade835a612d6148353c8f704d416c89f3c999e)

- **作者**: metamergebot
- **时间**: 2026-10-30T17:57:27Z
- **提交信息**: [Fix] rust-server: Fix the metrics flush race and the default-priority label (#47113)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [5008726](https://github.com/sgl-project/sglang/commit/5008726431693ef0883f83b230c08f77434e9b3b)

- **作者**: Liu Cao
- **时间**: 2026-10-30T17:13:30Z
- **提交信息**: [Fix] anthropic: Preserve cache_salt for Messages requests (#46937)

### [60725d0](https://github.com/sgl-project/sglang/commit/60725d0e176b0f08c4e45863e1ae74cdef7900f9)

- **作者**: Avaya Aggarwal
- **时间**: 2026-10-30T17:06:30Z
- **提交信息**: [Perf] diffusion: Wan-Animate-2 decode clamp, LTX-2 Bongmath closed form, rollout log-prob/CPU-copy, validators NaN gate, in-place decode normalize (#46277)

### [dee613b](https://github.com/sgl-project/sglang/commit/dee613b283fc17b82ed573926921b3b4ebd3da60)

- **作者**: Mick
- **时间**: 2026-10-30T16:57:25Z
- **提交信息**: [Perf] diffusion: Skip the cross-request cache for Qwen3-VL vision features (#47466)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [51d5502](https://github.com/sgl-project/sglang/commit/51d5502aff999cf3a80e0c2d211d56523310561c)

- **作者**: Zheng Gong
- **时间**: 2026-10-30T15:37:35Z
- **提交信息**: [Fix] moe: Fix --enable-fused-moe-sum-all-reduce outside CUDA and with LoRA hooks (#44268)

Signed-off-by: ZhengGong-amd <zgong@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [d51a1e5](https://github.com/sgl-project/sglang/commit/d51a1e5d971892d2406441bbdd3d78a9f1c100e6)

- **作者**: nvjullin
- **时间**: 2026-10-30T15:16:33Z
- **提交信息**: [Perf] pd: Publish decode KV destinations without host syncs under overlap (#45328)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Shangming Cai <csmthu@gmail.com>

### [c575b8f](https://github.com/sgl-project/sglang/commit/c575b8f36df2739cddf61c8ee667e0c44a8381bd)

- **作者**: Christian Gilli
- **时间**: 2026-10-30T15:03:14Z
- **提交信息**: [Chore] [AMD] mono-kernel: Bump sgl-amd-mono for Qwen3.8-Flash-Next (#47483)

### [75a5da7](https://github.com/sgl-project/sglang/commit/75a5da7fb9319d9e83a39a20e720b86390b9727f)

- **作者**: fzyzcjy
- **时间**: 2026-10-30T14:12:54Z
- **提交信息**: [Feat] RL: Hash raw received weights by name in check_weights (#47087)

### [9cf2bc8](https://github.com/sgl-project/sglang/commit/9cf2bc89250d50ccd0915d41747992f15ac8268d)

- **作者**: fzyzcjy
- **时间**: 2026-10-30T14:12:27Z
- **提交信息**: [Feat] kv-canary: Pass through canary info when the KV-canary is enabled (#47086)

### [e7dd1d0](https://github.com/sgl-project/sglang/commit/e7dd1d094dfe91194b665d403ff1da7cebf1d418)

- **作者**: fzyzcjy
- **时间**: 2026-10-30T14:09:00Z
- **提交信息**: [Feat] RL: Report prompt KV weight versions in generation metadata (#47085)

### [f3c9f0a](https://github.com/sgl-project/sglang/commit/f3c9f0a5ab82ba33bbcace72c98bbd261a3dcaff)

- **作者**: fzyzcjy
- **时间**: 2026-10-30T14:08:00Z
- **提交信息**: [Fix] environ: Register the batch-invariant matmul fallback flag in Envs (#47084)

### [e3e3729](https://github.com/sgl-project/sglang/commit/e3e372931a31dd285bbaf95216327635a640333d)

- **作者**: Mick
- **时间**: 2026-10-30T14:02:45Z
- **提交信息**: [Feat] diffusion: Native Gemma-4-Unified text encoder for LTX-2.5 (#47411)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [24268cc](https://github.com/sgl-project/sglang/commit/24268cc92bcdfebf9c61d697dac318217884c0ca)

- **作者**: Mick
- **时间**: 2026-10-30T13:59:33Z
- **提交信息**: [Fix] diffusion: recover LTX eager performance without disabling fusion (#47270)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [2271894](https://github.com/sgl-project/sglang/commit/227189488449d97d89d8da2fd5c1ee4bf1e2f955)

- **作者**: Dang Truong
- **时间**: 2026-10-30T13:33:57Z
- **提交信息**: [Fix] data_parallel_controller: Fix active ranks update and simplify round-robin dispatch (#45496)

### [5d4a6f4](https://github.com/sgl-project/sglang/commit/5d4a6f499e028405ecd4c8362c1e8b2443df1758)

- **作者**: Fadi Saady
- **时间**: 2026-10-30T12:59:27Z
- **提交信息**: [Fix] nemotron-h: Allow explicit CuTe DSL W4A16 MoE (#44750)

Signed-off-by: Fadi Saady <fsaady@nvidia.com>
Co-authored-by: Po-Han Huang (NVIDIA) <53919306+nvpohanh@users.noreply.github.com>

### [8776a94](https://github.com/sgl-project/sglang/commit/8776a94f2935e9a58b6dfc164c0d0e86f4d6b748)

- **作者**: yszhao2004
- **时间**: 2026-10-30T12:58:55Z
- **提交信息**: [Fix] minimax-h3: Swap the fc1 halves of the Acc LoRA in build_minimax_h3_pdd_weights (#46907)

### [c805455](https://github.com/sgl-project/sglang/commit/c8054551012b3df729a0f7c409af95f74286e416)

- **作者**: labAxiaoming
- **时间**: 2026-10-30T12:51:40Z
- **提交信息**: [Fix] minimax_h3: Support out-of-tree platforms (#44725)

### [9691e71](https://github.com/sgl-project/sglang/commit/9691e711cd03f8afd155eb5afe832bf2f44bb5a6)

- **作者**: Po-Han Huang (NVIDIA)
- **时间**: 2026-10-30T11:23:24Z
- **提交信息**: [Doc] cookbook: Refresh SemiAnalysis AgentX launches to InferenceX main ea8b3439 (#47464)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [56a8d3a](https://github.com/sgl-project/sglang/commit/56a8d3a8d76ddb43d4697ae56972294364dbcd94)

- **作者**: Aarne Talman
- **时间**: 2026-10-30T11:01:11Z
- **提交信息**: [Fix] deterministic: Validate the per-phase attention backends (#44438)

Co-authored-by: Thomas Wang <thomawan@amd.com>

### [02cd9ff](https://github.com/sgl-project/sglang/commit/02cd9ff0a21f68d8adc716350baff653cc0eaaab)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-10-30T10:11:56Z
- **提交信息**: [Fix] [AMD] scripts: Run and correctly test Dockerfile-only PRs (CI filter + AITER rebuild) (#47395)

Co-authored-by: Bingxu Chen <Bingxu.Chen@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [e371881](https://github.com/sgl-project/sglang/commit/e3718813ec5f47df0ad368b9a4713fbd3ad0a3bf)

- **作者**: Chao Shi
- **时间**: 2026-10-30T09:34:04Z
- **提交信息**: [Feat] observability: Add scheduler_iterations_total metric (#46485)

### [72576df](https://github.com/sgl-project/sglang/commit/72576df88dbc9837878c7c2c6ad007ccd906447f)

- **作者**: Kelon
- **时间**: 2026-10-30T09:23:56Z
- **提交信息**: [Feat] [NPU] DSpark: Support dsv4 dspark on ascend 950 (#39947)

Co-authored-by: lilDss <115407039+lilDss@users.noreply.github.com>

### [17e94c4](https://github.com/sgl-project/sglang/commit/17e94c4677d7beb58a89b104fd61b3768994e45e)

- **作者**: ashwini rathi
- **时间**: 2026-10-30T08:46:04Z
- **提交信息**: [CI] [Intel] ci/xpu: Rename rolling Docker tag and add release-cut results CSV (#46394)

### [a8559ca](https://github.com/sgl-project/sglang/commit/a8559ca77560eb8f7012c6c6dcf731936c2adb59)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-30T08:24:31Z
- **提交信息**: [Test] managers: Give the chunked-abort test scheduler an output_streamer (#47424)

### [464187f](https://github.com/sgl-project/sglang/commit/464187fa95297a640c56a8fb86c9dfc93a77ec21)

- **作者**: Thomas Wang
- **时间**: 2026-10-30T08:18:39Z
- **提交信息**: [Doc] [AMD] cookbook: Update muse-spark recipe 1030 (#47422)

### [f96a6e4](https://github.com/sgl-project/sglang/commit/f96a6e42f6048fa5175e3de603d146daaaa95a29)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-30T08:09:05Z
- **提交信息**: [Fix] scheduler: Retire the beam group of an aborted chunked leader (#47381)

### [15ef675](https://github.com/sgl-project/sglang/commit/15ef67584698eec9459d780ec47aaffaefc020f2)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-30T08:03:04Z
- **提交信息**: [Perf] detokenizer: Send each step's output ids as one flat column with row offsets (#47415)

### [a63ea54](https://github.com/sgl-project/sglang/commit/a63ea5442b16460ee0ce68ff44c75522cd0ccc52)

- **作者**: sglang-bot
- **时间**: 2026-10-30T07:56:47Z
- **提交信息**: [Chore] release: Bump docs install version to 0.5.23 (#47419)

Co-authored-by: sglang-bot <sglang-bot@users.noreply.github.com>

### [2b354b0](https://github.com/sgl-project/sglang/commit/2b354b0006445a41d428deeb7d61f895f63a1098)

- **作者**: ashwini rathi
- **时间**: 2026-10-30T07:53:01Z
- **提交信息**: [CI] [Intel] xpu-eval: Add sgl-eval to XPU test deps and move all GSM8K tests to it (#47056)

### [e337bb1](https://github.com/sgl-project/sglang/commit/e337bb10b5e1ef4a4753180fe023b2fd5925f54f)

- **作者**: snadampal
- **时间**: 2026-10-30T07:35:40Z
- **提交信息**: [Feat] docker: Update the EFA images to EFA installer 1.51.0 (#46892)

Signed-off-by: Sunita Nadampalli <nadampal@amazon.com>

### [8080507](https://github.com/sgl-project/sglang/commit/8080507c3e578458af6749c8e428efdff737de93)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-30T07:22:24Z
- **提交信息**: [Perf] detokenizer: Send per-request decode inputs once and keep them in the detokenizer (#47260)

### [93f4f1a](https://github.com/sgl-project/sglang/commit/93f4f1a87dbf356833e5d2ec777ee4b006b631fd)

- **作者**: Michael
- **时间**: 2026-10-30T07:06:52Z
- **提交信息**: [CI] [AMD] pr-test: Move the Kimi-K2.5 MXFP4 BCG test to nightly (#47152)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-10-31
**监控日期**: 2026-10-30
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for 100+ DiTs.
- **语言**: Python
- **星标数**: 1297
- **最后更新**: 2026-10-31T00:14:00Z

## 提交统计

- **昨日提交总数**: 5
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

# cache-dit 昨日提交分析

## 1. 主要更新类型

| 提交 | 类型 |
|------|------|
| docs: render support matrix tables (#1199) | 文档修复 |
| Update README.md | 文档更新 |
| chore(release): drop Python 3.10 (#1196) | 构建/发布策略调整 |
| refactor(kernels): split attention-state merge (#1195) | 架构重构 |
| feat: support FastH3 (#1186) | 功能新增（重量级） |

总体来看，当日工作以 **功能新增** 为核心，辅以**架构重构**、**构建策略调整**和**文档修复**。

## 2. 关键变更点及与项目方向的关系

- **FastH3 支持**（e0a59e1）是本次最重要的提交。项目定位是 PyTorch 原生的 DiT 推理引擎，涵盖缓存、并行、量化与 CPU Offload。FastH3 是 MiniMax-H3 的 DMD2 少步蒸馏学生模型（带 VSA 视频稀疏注意力），属于**新一代少步/加速生成**方向的核心能力扩展。新增内容包括专用 Pipeline、门控注意力处理器、VSA 的两种可互换实现（flex/gather），以及在上下文并行（CP）和张量并行（TP）下的 VSA 支持，说明项目持续在"更多模型 × 更多并行策略"的矩阵上扩展。

- **attention 扩展独立**（e819911）将 `merge_attn_states` 内核从通信扩展（`_C_comm`）中拆出，单独构建为 `cache_dit._C_attn`。这是一次关注点分离的重构，使三个扩展（comm / attn / svdquant）各自职责清晰，也为后续 attention 算子的独立演进奠定基础。

- **移除 Python 3.10**（9eb4518）紧跟 PyTorch 官方不再发布 3.10 轮子的事实，将发布目标收紧为 cp311–cp314，同时修正了 `python_requires` 被 `setup.py` 覆盖导致元数据不一致的问题。

## 3. 对项目的影响和潜在意义

- **产品力提升**：FastH3 的引入直接扩展了 cache-dit 支持的模型矩阵，尤其是少步蒸馏模型这一热门方向；VSA 在 CP/TP 下的精确支持进一步验证了项目在"稀疏注意力 + 分布式推理"交叉领域的技术深度。
- **可维护性改善**：attention 扩展独立后，内核编译和 Python 加载路径解耦，新增算子或调试 attention 相关问题将更直接。
- **用户面收紧**：Python 最低版本升至 3.11 意味着部分旧环境用户需要升级，但与生态保持一致，减少兼容负担。

## 4. 值得关注的技术点

- **VSA 的双实现策略**：`flex`（BlockMask）与 `gather`（chunked SDPA）可互换，后者作为可移植基线和精确测试参照，体现了对正确性验证的严谨性。
- **CP 下 VSA 的精确支持**：通过一次 `all_to_all_single` 将序列 gather 完成 tile 选择，避免了近似方案，且门控放置参考了 FastVideo/vllm-omni 的实践而非 sglang 的延迟折叠方案。
- **构建系统防错设计**：显式 ATTN 构建时若无法解析 SM 目标会直接 raise 而非静默跳过，发布检查脚本也会验证 wheel 中包含 `_C_attn`，体现了对发布质量的把控。
- **mkdocs 渲染问题的根因**：`md_in_html` 开启导致 `<div>` 内 Markdown 表格未被解析，通过 `markdown="1"` 修复，是使用 mkdocs + HTML 混排时的常见坑。

## 5. 对项目发展方向的影响

结合 README 可知，cache-dit 的目标是成为 DiT 模型（视频生成等）的全栈 PyTorch 推理加速引擎。本次提交在三个层面推进了这一目标：

1. **模型覆盖度**：FastH3 代表了"少步蒸馏 + 稀疏注意力"这一前沿推理路径的落地，使 cache-dit 在与 sglang、ComfyUI 等生态的竞争中保持模型跟进速度。
2. **工程成熟度**：扩展拆分和 Python 版本收紧表明项目正从快速迭代期走向结构清晰、版本策略明确的稳定期。
3. **并行能力纵深**：VSA 与 CP/TP 的结合证明项目在"稀疏化 × 分布式"的组合场景下已具备系统性的方案设计能力，这将是 DiT 推理效率持续提升的关键方向。

总体而言，这一批提交展示了 cache-dit 在功能广度和工程深度上的同步推进，是一个活跃且方向明确的项目。

## 详细提交记录

### [9ae7ab9](https://github.com/vipshop/cache-dit/commit/9ae7ab9d9d2ead89d5da9f91b229a598bd7a64a9)

- **作者**: DefTruth
- **时间**: 2026-10-30T14:33:35Z
- **提交信息**: docs: render support matrix tables on the mkdocs site (#1199)

* docs: fix support matrix tables not rendered on mkdocs site

'md_in_html' is enabled in mkdocs.yml, so '<div align="center">' blocks are
treated as raw HTML and the markdown tables inside them were emitted verbatim
(shown as plain '|'-separated text on Read the Docs). Mark the wrapping divs
with markdown="1" (same as user_guide/CACHE_API.md) so the tables are parsed.

* docs: shorten Ascend NPU and AMD GPU nav titles

### [da9b96c](https://github.com/vipshop/cache-dit/commit/da9b96cf17a2d1452a5f0295452106c0aeddc6d3)

- **作者**: DefTruth
- **时间**: 2026-10-30T13:53:39Z
- **提交信息**: Update README.md

### [9eb4518](https://github.com/vipshop/cache-dit/commit/9eb4518d6a82bc408b5745d20e9dd7167846ba78)

- **作者**: DefTruth
- **时间**: 2026-10-30T08:55:39Z
- **提交信息**: chore(release): drop Python 3.10 from the release build (#1196)

* chore(release): drop Python 3.10 from the release build

torch no longer ships Python 3.10, so 3.10 stops being a release target: the
published CPython set becomes cp311-cp314.

- tools/build_releases.sh: full profile defaults to py311 py312 py313 py314, the
  env/python-tag tables lose py310, and a CACHE_DIT_RELEASE_ENVS that still names
  py310 now fails before anything is built
- cache-dit-build-release skill: wheel set, preflight env loop, build command and
  both references updated to cp311-cp314 (the v1.5.3+cu13 asset record stays as
  history)

* chore: require Python 3.11+

The wheel metadata still advertised 3.10 because setup.py passed
python_requires=">=3.10", which overrides the PEP 621 requires-python, so
editing pyproject.toml alone changed nothing.

Set both to >=3.11 and keep them in step with the release set (cp311-cp314).

* docs(install): require Python 3.11+

Keep the installation prerequisites in step with the package metadata, which now
advertises Requires-Python >=3.11.

---------

Co-authored-by: DefTruth <DefTruth@users.noreply.github.com>

### [e819911](https://github.com/vipshop/cache-dit/commit/e8199119ac074618ec0ef47bf6e709ca47fc6583)

- **作者**: DefTruth
- **时间**: 2026-10-30T08:55:24Z
- **提交信息**: refactor(kernels): split attention-state merge into its own extension (#1195)

The merge_attn_states kernel lived in csrc/kernels/attn but was compiled into
cache_dit._C_comm, declared in comm_ops.h and registered in comm_ops.cpp, so the
attention operators were owned by the communication extension.

- csrc/kernels/attn: add attn.h/attn.cpp as the family's pybind TU and move the
  kernels into namespace cache_dit::attn
- csrc/kernels/comm: drop the merge declaration and binding, leaving the FP8
  communication operators alone
- setup.py: build cache_dit._C_attn from its own sources, gated by
  CACHE_DIT_BUILD_ATTN (COMM and SVDQUANT builds also produce it); an explicit
  ATTN build raises instead of silently skipping when no SM target resolves
- kernels/_merge_states.py -> kernels/_attn.py, which loads cache_dit._C_attn
  itself instead of borrowing the comm loader
- tools/inspect_release_wheel.py: the CUDA wheel must carry _C_attn too
- docs and operator-migration/release skills updated for the three-extension
  layout

Co-authored-by: DefTruth <DefTruth@users.noreply.github.com>

### [e0a59e1](https://github.com/vipshop/cache-dit/commit/e0a59e18a45eeb1fdc9fcf84a6b447797fdd3e24)

- **作者**: DefTruth
- **时间**: 2026-10-30T08:24:44Z
- **提交信息**: feat: support FastH3 (MiniMax-H3 few-step DMD2 students with VSA) (#1186)

* docs: update docs

* docs: update docs

* docs: sync docs/README.md with README.md

* feat: support FastH3 (MiniMax-H3 few-step DMD2 students with VSA)

FastH3 checkpoints share the MiniMax-H3 architecture but add a per-block
`attn.to_gate_compress` projection, a fixed DMD sigma ladder and video sparse
attention. Loading them through the plain H3 path silently drops the 50 gate
tensors and degrades attention to dense, i.e. a different model.

- models/pipelines/fast_h3.py: FastH3ModularPipeline / FastH3Transformer3DModel
  (gate built before from_pretrained, zero-initialised, resolved once after
  load) and FastH3AttnProcessor; the DMD ladder is applied per modality because
  MiniMaxH3Scheduler.set_timesteps(sigmas=...) uses it verbatim.
- attention/vsa_h3{,_geometry}.py: tile-64 selection (fp32 tile pooling, per
  (b,h,query tile) top-k, dense prefix), gated compression branch, and two
  interchangeable kernels: `flex` (BlockMask.from_kv_blocks) and `gather`
  (chunked SDPA, kept as the portable baseline and exact test reference).
- adapter/planner registration for the new class names, `fasth3` / `fasth3_v2`
  examples with their own cache preset and `to_gate_compress` quantisation
  exclusion, docs and GPU matrix rows, plus 31 new CPU tests wired into CI.

* docs: use the Fast-H3 row naming in both READMEs

* feat(fasth3): run video sparse attention under context and tensor parallelism

VSA was refused under CP/TP even though both are exact: tile selection is
per head, and the Ulysses all-to-all already gathers the packed sequence that
selection needs.

- CP: the processor owns the exchange. Q/K/V and the compression gate go
  through one `all_to_all_single` (heads scattered, sequence gathered), VSA runs
  on the full sequence exactly like the single-GPU path, and the reverse
  exchange restores the row shard. Gate placement follows FastVideo/vllm-omni
  rather than sglang's deferred fold: it is per head and per channel, so it must
  land in Q's layout.
- TP: Q/K/V/gate are unwrapped to their local shard before the sparse kernel
  (index_select/gather/topk/BlockMask have no DTensor strategy) and the output
  is rewrapped with the inputs' placement; `to_gate_compress` stays Colwise.
- Both planners stop refusing VSA, the head/degree divisibility guard gives the
  allowed values, and the GPU matrix rows go back to CP/TP supported.

Verified on 2x RTX PRO 5000: the CP data path (gate-carried Ulysses exchange
then reverse) and the TP head shard both reproduce the single-GPU attention
bit-exactly (max|diff| = 0).

* fix(fasth3): harden the contract and shard probe against real checkpoints

* refactor(fasth3): define FastH3Transformer3DModel and FastH3ModularPipeline directly

The factory functions only existed to keep diffusers out of module import, but
this module is already the lazy boundary (models/pipelines/__init__.py re-exports
nothing, the examples import it inside the factory). Direct class definition
restores the real __name__/__qualname__/__module__, which the class-name prefix
registries and any introspection read, and removes the leftover factory machinery.

* fix(fasth3): take the modality shift from the contract when it is stated

The 8-step V2 contract carries video_scheduler_shift=10.0 / audio_scheduler_shift=3.0;
the 4-step preview does not. Prefer the contract (it is the distillation record),
fall back to the scheduler configs, and warn when the two disagree instead of
silently resampling the student off its ladder.

* fix(fasth3): use a package-level relative import in the example factory

The example lives in cache_dit/_utils/, so the model import needs two dots; three
dots walked above the package and raised ImportError on the first CLI run.

* docs: mark Fast-H3 as parallel-supported and repair the docs table

The parallel column still said no for Fast-H3, but VSA now runs under both
Ulysses CP (gate carried with Q/K/V in one all-to-all) and TP (head-sharded
local attention, Colwise gate), and the GPU matrix rows were already updated.

Also drop the stray whitespace-only line that split the docs/README.md model
table in two, which made every row after MiniMax-H3 (Ref2VA) render as a
paragraph, and restore the trailing hard break on that row so the file differs
from main only by the added Fast-H3 line.

* docs: update docs

* docs: update docs

* revert: drop the FastH3 CI test steps

CI configuration and the MiniMax-H3 implementation are out of scope for this
change; the workflow is restored to main byte-for-byte, so the FastH3 tests are
run locally only.

* fix(fasth3): keep the CP exchange out of the compiled graph

all_to_all_single cannot run under Dynamo's fake-tensor tracing, so a
'--parallel ulysses --compile' run died with 'RuntimeError when making fake tensor
call'. The two context-parallel helpers are now graph breaks, which is also what the
reference implementations do with their collectives; the sparse attention itself
stays compilable.

* fix(cp): graph-break the ulysses-anything all-to-all instead of allow_in_graph

The four `_all_to_all_single_any_*` primitives return a closure (`wait`), not a
tensor, which violates `torch.compiler.allow_in_graph`'s contract (tensor or None
returns only). Dynamo therefore built a fake-tensor call and failed with
"RuntimeError when making fake tensor call".

These four are exclusively the `ulysses_anything` branch of the primitive
selector, so nothing regresses: the non-UAA primitives never had the decorator,
graph-break naturally, and that is why CP+compile works for models whose sequence
divides evenly. A model that needs `--uaa` (uneven packed sequence, e.g. FastH3
with 1024 text + audio + 13663 video rows) reaches the decorated functions and
fails for every model, not just this one.

Reproduced without any model in the loop (2 ranks, trivial tensor):
  allow_in_graph + closure -> compiled: RuntimeError when making fake tensor call
  compiler.disable + closure -> compiled: ok
  shipped UAA primitive (now disabled) -> eager ok, compiled ok

* docs(cp): record why the UAA exchange cannot use allow_in_graph

torch 2.15 enforces allow_in_graph's return-tensor contract; torch 2.11 tolerated
the closure return, which is why UAA+compile was seen working there.

* docs(skill): mark Stable Audio 3 as supported and refresh the chart rules

- rfc_pending_models.md: Stable Audio 3 moves to done (adapter/CLI/CP/TP/TE-P/offload
  facts from #1188), and R.5 logs both Stable Audio 3 and FastH3 (#1186).
- perf_matrix.md §8: per-configuration palette (one hue per row, same hue in both
  panels), hatch carries repro/gate semantics, legend must survive the PR thumbnail
  (>=9.5pt, framed, dpi 150, dashed-line labels at the top, white backing box on the
  inline values).

* docs(skill): LingBot-Video dense 1.3B is supported, MoE still pending

#1190 vendored the dense checkpoint's own pipeline plus a LingBotVideo adapter
and CP/TP planners; only the MoE 30B-A3B variant remains in R.6.

* docs(skill): keep the latency|quality chart as a style reference

Adds perf_chart_example.png (an 18-row FastH3 run) to references/ and points §8
at it, so the palette / hatch / legend rules have a concrete target instead of
only prose. Rule 10 now distinguishes this one documentation image from a run's
own PNG, which still goes to pr-assets.

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-10-31
**监控日期**: 2026-10-30
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 95936
- **最后更新**: 2026-10-31T01:37:35Z

## 提交统计

- **昨日提交总数**: 78
- **提交者数量**: 47
- **主要提交者**: kourosh hakhamaneshi, AlexHuang, CharlesWu

## AI分析总结

# vLLM 昨日 78 项提交综合分析

## 一、主要更新类型

**Rust 前端（约 18 条）**：最大主题。补齐 API 兼容性（`--root-path`、`--max-log-len`、`return_prompt_text`、`return_weight_versions`、UMBP 指标导出、访问日志结构化、`bad_words` 修复、流式 logprobs、completion_tokens_details 等），并构建分布式并行能力：支持混合/外部数据并行负载均衡、握手进程服务 DP rank 范围、协调式 DP 初始化 rendezvous 修复、拒绝原生渲染器的 chat 模板。

**CI 基础设施（约 9 条）**：Thang Nguyen 连续多波推进 CI 任务自动分片，将 LM Eval、Misc、Compile、Distributed、Spec Decode（21 个任务）、Kernels（30 个任务）及 AMD 镜像共约百个任务纳入分片机制，是 CI 降本提速的核心举措。

**Bug 修复（约 19 条）**：多层 MTP 模块选择、int32 token offset 溢出、tokenizer/processor 快照保留模型标识、HF 路径解析、KV offload 事件顺序、睡眠模式 pinned 内存、XPU 流式输入与 MLA 稀疏算子、HTTP 响应体重试、音频批处理错误码、Fast Start 预加载组退出停止、DiffusionGemma tiled logits 投影 OOM 等。

**性能优化（约 12 条）**：Qwen3.5 融合 norm+quant 与 gate+quant、DSA persistent top-k 直读 BF16、DSpark split-vocab Triton argmax、Muse Spark hybrid MoE 的 all-gather+norm 融合、GLM5.3 FP8 KV cache draft、gfx942 MXFP4-to-int4 requant、FlashMLA 向 MegaAttn 传递 int64 位置编码（面向 DeepSeek v4.1）、MegaMoE 32 行 tile 输入准备、silu_and_mul_nvfp4_quant 的 PDL 调度、compile_on_one_rank 编译缓存设备中立化。

**多硬件与新特性**：AITER 升级至 v0.1.27、MI355 MoE 内核测试迁移、预构建 mamba-ssm、DeepSeek-V3 NIXL 精度测试、OOT 硬件插件 opt-in 基础设施（IBM 贡献）、容错 EP scale-down、KV connector 异构 TP 共享（Mooncake）、模型加载 hook 时机修正。

## 二、关键变更与项目方向

README 定位 vLLM 为"人人可用的快速、廉价 LLM 服务"，本日提交从三个维度强化该定位：

**"快"**：Rust 前端作为 Python API 的高性能替代，密集补齐兼容性与分布式能力，有望消除 GIL 与序列化开销，成为高吞吐生产部署首选入口；内核级融合（MoE、量化、FP8 KV）与投机解码工程化（DSpark split-vocab argmax、批分片顺序 block、MRv2 speculator 配置）持续压低时延。

**"廉"**：CI 自动分片与 AMD 测试镜像优化缩短反馈周期、降低算力成本；FP8 KV cache、pinned 备份、offload、HiSparse、Mooncake/UMBP connector 多线并进，指向低成本长上下文与多实例部署；ROCm、XPU、CPU（MRv2 non-triton）并行推进，硬件中立性显著增强。

**"易"**：OOT 插件基础设施降低新硬件接入门槛；huggingface_hub 升级至 v2 属破坏性依赖变更，需下游注意兼容；文档与 API 对齐持续改善开箱体验。

## 三、值得关注的技术点

**AI 辅助开发常态化**：超过半数提交含 Claude、Codex、vllm-agent、Cursor 等 AI 署名，vLLM 已成为 AI 参与开源开发的典型样本，其协作与审核模式值得同行研究。

**Rust 前端的 DP 架构成型**：握手进程、rendezvous 修复与负载均衡共同表明 Rust 端正在构建完整的分布式并行能力，是架构现代化的重要信号。

**编译缓存设备中立化**：compile_on_one_rank 解决多设备环境缓存不一致，对混合部署场景实用价值高。

**PagedAttention 衍生能力**：混合 KV cache 异构 TP 共享展示 paged 架构在跨实例共享上的扩展潜力。

## 四、整体意义

本日 78 项提交体现了 vLLM 从 Python 单体向多前端、多硬件、可运维系统演进的关键阶段：容错 EP scale-down 为大规模 MoE 部署提供韧性，是从"能跑"到"能运维"的跨越；CI 分片与内核优化夯实工程底座；多硬件与多模型（DeepSeek、Qwen、Gemma）适配扩大覆盖面。若 Rust 前端走向成熟，可能成为 vLLM 服务层的关键演进方向，整体工程成熟度显著提升。

## 详细提交记录

### [d90e35c](https://github.com/vllm-project/vllm/commit/d90e35cffa21729ac55bb0477a0d64f5127dbcda)

- **作者**: hshrivastava-droid
- **时间**: 2026-10-30T23:57:20Z
- **提交信息**: [Doc] MiniMax-M3.1-Flash: add GB300 InferenceX AgentX presets (#64821)

Signed-off-by: hshrivastava-droid <hshrivastava@nvidia.com>
Co-authored-by: Claude Sonnet 5.5 <noreply@anthropic.com>

### [59d58fd](https://github.com/vllm-project/vllm/commit/59d58fd261b1e0726bcc9030b756c1e923183583)

- **作者**: djramic
- **时间**: 2026-10-30T23:17:08Z
- **提交信息**: [ROCm][CI] Run MI355 MoE Kernels on a full MI355 instead of DPX (#64740)

Signed-off-by: Djordje Ramic <djoramic@amd.com>

### [dd5f5ee](https://github.com/vllm-project/vllm/commit/dd5f5eebd7a004b7366e38927417fb0748bcbbd1)

- **作者**: Spandan Tiwari
- **时间**: 2026-10-30T23:08:28Z
- **提交信息**: [Bugfix] Fix multi-layer MTP module selection for Qwen3.5 and Qwen3-Next (#62111)

Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Shanshan Shen <467638484@qq.com>

### [4c38b65](https://github.com/vllm-project/vllm/commit/4c38b653af940bdd8e70e1e92d9ce7b114facb02)

- **作者**: Juntian Liu
- **时间**: 2026-10-30T23:07:05Z
- **提交信息**: [Bugfix][Core] Keep offline DP ranks' collectives aligned with async scheduling (#64457)

Signed-off-by: Juntian Liu <Juntianl777@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [6c19299](https://github.com/vllm-project/vllm/commit/6c19299fca37eabb719002b0249501a89430c3e6)

- **作者**: Thien Tran
- **时间**: 2026-10-30T23:04:15Z
- **提交信息**: [Perf][Qwen3.5] (NVIDIA-only) Fused norm+quant and gate+quant (#64509)

Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>

### [d2d550c](https://github.com/vllm-project/vllm/commit/d2d550c3fc121e2cdd4556a5696e3e4e2667650b)

- **作者**: Thang Nguyen
- **时间**: 2026-10-30T23:00:41Z
- **提交信息**: [CI] Remove the retired A100 queue's steps; keep their live AMD mirrors standalone (#64602)

Signed-off-by: Thang Nguyen <thangnguyenvn647@gmail.com>
Co-authored-by: Kimi Code <noreply@moonshot.ai>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [14a5bb4](https://github.com/vllm-project/vllm/commit/14a5bb4adcc86e4c953236e048bae28512c92427)

- **作者**: Aaron Hao
- **时间**: 2026-10-30T22:53:15Z
- **提交信息**: [Model Loader] Run the model-level post-load hook once at the end of every load and reload (#64357)

Signed-off-by: aoshen02 <aoshen@inferact.ai>
Signed-off-by: Aaron Hao <aaronhao@inferact.ai>
Signed-off-by: Aaron Hao <hao-aaron@users.noreply.github.com>
Co-authored-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: nicole-lihui <44200120+nicole-lihui@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Aaron Hao <hao-aaron@users.noreply.github.com>

### [040abb2](https://github.com/vllm-project/vllm/commit/040abb262c5b09b8325abe0379ff70246fd92bba)

- **作者**: Fadi Arafeh
- **时间**: 2026-10-30T22:52:03Z
- **提交信息**: [CPU][MRv2] Enable MRv2 for non-triton CPU backends (#61995)

Signed-off-by: Fadi Arafeh <fadi.arafeh@arm.com>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [e31cf3d](https://github.com/vllm-project/vllm/commit/e31cf3dec7cf14369b0c7a8447cdfb8b387af6e0)

- **作者**: Bo Pang
- **时间**: 2026-10-30T22:43:09Z
- **提交信息**: [Perf][DSA] Read BF16 logits directly in persistent top-k (#64138)

Signed-off-by: Bo Pang <bopang314@gmail.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Woosuk Kwon <woosuk@inferact.ai>

### [be712f5](https://github.com/vllm-project/vllm/commit/be712f5601dc7eebf43aa42848be6a84256dcada)

- **作者**: Aaron Hao
- **时间**: 2026-10-30T22:41:04Z
- **提交信息**: [RL] NCCL weight transfer: release cached memory after a weight update (#64691)

Signed-off-by: aoshen02 <aoshen@inferact.ai>
Signed-off-by: Aaron Hao <hao-aaron@users.noreply.github.com>
Co-authored-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Aaron Hao <hao-aaron@users.noreply.github.com>

### [67d677b](https://github.com/vllm-project/vllm/commit/67d677bdef939cb95b433dfcd43a4eca234aa29b)

- **作者**: Aarushi Jain
- **时间**: 2026-10-30T22:11:11Z
- **提交信息**: [ROCm][CI] Prebuild mamba-ssm and causal-conv1d into the CI test image (#64577)

Signed-off-by: aarushjain29 <aarushi.jain2@amd.com>
Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [7495e9e](https://github.com/vllm-project/vllm/commit/7495e9e5a4b705a16bec8ecba43ed7c317067db1)

- **作者**: Josh Schell
- **时间**: 2026-10-30T21:40:43Z
- **提交信息**: [ROCm] Bump AITER to v0.1.27 (#63774)

Signed-off-by: josh schell <josh.schell@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [212f366](https://github.com/vllm-project/vllm/commit/212f3666a84e3943b3b1b1658d8162d8ba5baef5)

- **作者**: Yan Ma
- **时间**: 2026-10-30T20:31:40Z
- **提交信息**: [Bugfix] [Tokenizer] Preserve Hub model identity when loading tokenizer snapshots (#63482)

Signed-off-by: Yan Ma <yan.ma@intel.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [644a9f5](https://github.com/vllm-project/vllm/commit/644a9f5d278cc24cea5ad5a7990f397df0fa26b7)

- **作者**: Harry Mellor
- **时间**: 2026-10-30T20:31:17Z
- **提交信息**: [Deps] Upgrade to huggingface_hub 2 (#64779)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [2f6f786](https://github.com/vllm-project/vllm/commit/2f6f7861ba075b72b530b3d0b7889fc55b500ae4)

- **作者**: simon-veitner-redhat
- **时间**: 2026-10-30T20:27:50Z
- **提交信息**: [Bugfix] Fix int32 token offset overflows in Qwen3.5 attention and GDN prefill kernels (#63761)

Signed-off-by: Simon Veitner <sveitner@redhat.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Roberto L. Castro <38211239+LopezCastroRoberto@users.noreply.github.com>

### [c8dbb1c](https://github.com/vllm-project/vllm/commit/c8dbb1cb262ee5663f8983ef5536e1d57e1b47e1)

- **作者**: Juntian Liu
- **时间**: 2026-10-30T20:20:43Z
- **提交信息**: [Perf][Spec Decode] Split-vocabulary Triton argmax for the DSpark greedy draft (#57770)

Signed-off-by: Juntian Liu <Juntianl777@gmail.com>
Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: mgoin <mgoin64@gmail.com>

### [ed14230](https://github.com/vllm-project/vllm/commit/ed14230f4fc4d889a6a60c187a4b6449ef9fd77c)

- **作者**: Prakash Saini
- **时间**: 2026-10-30T20:14:05Z
- **提交信息**: [Bugfix] Skip more weight formats in the tokenizer/processor snapshot (#63922)

Signed-off-by: Prakash-sa <sainiprakash525@gmail.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [2fab358](https://github.com/vllm-project/vllm/commit/2fab35893b1a0ef78cb2392363cc7de3b00cb425)

- **作者**: stefankoncarevic
- **时间**: 2026-10-30T20:04:40Z
- **提交信息**: [Bugfix] Fix depyf incompatibility with Inductor's set_sys_modules (#60873)

Signed-off-by: Stefan Koncarevic <Stefan.Koncarevic@amd.com>

### [c9af9ac](https://github.com/vllm-project/vllm/commit/c9af9acc6ac22f6351e214eb0d7d9a7a26dfa870)

- **作者**: bzsuni
- **时间**: 2026-10-30T19:18:38Z
- **提交信息**: [Bugfix] Resolve HF paths when loading sharded state (#61380)

Signed-off-by: bzsuni <bingzhe.sun@daocloud.io>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [913fccd](https://github.com/vllm-project/vllm/commit/913fccd11847f5b4d4769e3a69c8925f955bc29e)

- **作者**: fangyuchu
- **时间**: 2026-10-30T18:16:01Z
- **提交信息**: [Feature] Initial support for fault tolerant ep using scale-down (#46370)

Signed-off-by: fangyuchu <fangyuchu@qq.com>
Signed-off-by: TianZhuo <2770730562@qq.com>
Signed-off-by: zWaNg3 <389750525@qq.com>
Signed-off-by: Tyler Michael Smith <tlrmchlsmth@gmail.com>
Co-authored-by: Tzu-Ling <tzulingk@nvidia.com>
Co-authored-by: tianzhuo <2770730562@qq.com>
Co-authored-by: zWaNg3 <389750525@qq.com>
Co-authored-by: Tyler Michael Smith <tlrmchlsmth@gmail.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [d731ff9](https://github.com/vllm-project/vllm/commit/d731ff928049d98a2bb050b72848cb858045772a)

- **作者**: Lize Cai
- **时间**: 2026-10-30T18:09:41Z
- **提交信息**: [Doc] Fix %% rendering in CLI reference for --safetensors-load-strategy (#46335)

Signed-off-by: Lize Cai <lize.cai@sap.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [a93c7fb](https://github.com/vllm-project/vllm/commit/a93c7fb73b3a97ab93639c7fd5c66c9fb3a16fa9)

- **作者**: hechengkai
- **时间**: 2026-10-30T18:07:16Z
- **提交信息**: [Doc] Fix Case 4 math rendering in hybrid KV cache manager (#64188)

Signed-off-by: hechengkai <hechengkaiedu@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [75d14e8](https://github.com/vllm-project/vllm/commit/75d14e84e332d34b56782aae8852f94b03bf3c10)

- **作者**: sarankumar
- **时间**: 2026-10-30T17:53:42Z
- **提交信息**: [Docs] Fix dead links to moved llm-d, Dynamo, TPU, Ray and Tensorizer pages (#64666)

Signed-off-by: sarankumar1325 <120080287+sarankumar1325@users.noreply.github.com>

### [42379a4](https://github.com/vllm-project/vllm/commit/42379a4c246ce48472f165571d89f962e6c8d97e)

- **作者**: Nick Hill
- **时间**: 2026-10-30T17:52:23Z
- **提交信息**: [Model Runner V2][Spec Decode] Speculator config classes and custom speculators (#63205)

Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [5423fb8](https://github.com/vllm-project/vllm/commit/5423fb8b93a539b24e7f80075d132d4f4dcab95b)

- **作者**: Giancarlo Delfin
- **时间**: 2026-10-30T17:23:15Z
- **提交信息**: [Spec Decode][DSpark] Batch-sharded sequential block (#63886)

Signed-off-by: Giancarlo Delfin <gdelfin@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [e811e50](https://github.com/vllm-project/vllm/commit/e811e502efb2b77c7d664b20b68e8dc27e726067)

- **作者**: djramic
- **时间**: 2026-10-30T16:28:03Z
- **提交信息**: [ROCm][CI] Fix AITER MXFP4 padding tests failing instead of skipping on MI300 (#64727)

Signed-off-by: Djordje Ramic <djoramic@amd.com>

### [dc4dd5a](https://github.com/vllm-project/vllm/commit/dc4dd5a2217bc757232e9fa4d8a8b59e207ca068)

- **作者**: Avinash Paul
- **时间**: 2026-10-30T16:12:22Z
- **提交信息**: [ROCm][DI][CI]  Add DeepSeek-V3 NIXL accuracy steps (#62007)

Signed-off-by: avininjamay8 <avpaul@amd.com>
Co-authored-by: avininjamay8 <avpaul@amd.com>
Co-authored-by: Shanshan Shen <467638484@qq.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Chaitanya Sri Krishna Lolla <lollachaitanya@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [becbaea](https://github.com/vllm-project/vllm/commit/becbaea9f58f5a492f36d4b932fbc0484fa68198)

- **作者**: Jee Jee Li
- **时间**: 2026-10-30T16:06:03Z
- **提交信息**: [Perf] Fuse all-gather and norm for Muse Spark hybrid MoE (#64638)

Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>

### [ca5c2d7](https://github.com/vllm-project/vllm/commit/ca5c2d7843a5de396f1a3e4aee137fa16decd720)

- **作者**: djramic
- **时间**: 2026-10-30T15:27:03Z
- **提交信息**: [ROCm][CI] Drop LD_PRELOAD from the subprocess env in test_amd_ci_fast_exit (#64708)

Signed-off-by: Djordje Ramic <djoramic@amd.com>

### [d15be08](https://github.com/vllm-project/vllm/commit/d15be0856ded087df49b67a82efaa75243b98251)

- **作者**: Wentao Ye
- **时间**: 2026-10-30T15:22:10Z
- **提交信息**: [GLM5.3 Perf] Switching dlfash fp8 kv cache draft model, 2.85 GB memory saved per rank (#64612)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [6a95c89](https://github.com/vllm-project/vllm/commit/6a95c89c371939997d9ce3b616360b529760f0bc)

- **作者**: Brandon Pelfrey
- **时间**: 2026-10-30T13:45:47Z
- **提交信息**: [Multimodal] Cache PyNvVideoCodec decoder caps (#64618)

Signed-off-by: Brandon Pelfrey <bpelfrey@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [b44a48c](https://github.com/vllm-project/vllm/commit/b44a48cef1c08cbdc30a0953c724f18cd434e612)

- **作者**: Stefano Castagnetta
- **时间**: 2026-10-30T13:28:29Z
- **提交信息**: [Qwen4Exp] PLE disk offload (#59958)

Signed-off-by: Stefano Castagnetta <scastagnetta@nvidia.com>
Signed-off-by: Trosfy <61226342+Trosfy@users.noreply.github.com>
Co-authored-by: Kartikey Vyas <kartikey@artificialanalysis.ai>
Co-authored-by: Trosfy <61226342+Trosfy@users.noreply.github.com>
Co-authored-by: Artem Perevedentsev <aperevedents@nvidia.com>

### [32b30df](https://github.com/vllm-project/vllm/commit/32b30dfe46d7ac700bc30a1a798b90d874a96dd9)

- **作者**: hshrivastava-droid
- **时间**: 2026-10-30T13:15:12Z
- **提交信息**: [Recipe] Kimi-K3: add B300 AgentX aggregated Mooncake preset (#64617)

Signed-off-by: hshrivastava-droid <hshrivastava@nvidia.com>
Co-authored-by: Claude Sonnet 5.5 <noreply@anthropic.com>
Co-authored-by: Wei Zhao <51183510+wzhao18@users.noreply.github.com>

### [8493b34](https://github.com/vllm-project/vllm/commit/8493b34b7b8738b379c6cc6850e1117bc66814d8)

- **作者**: Matthew Bonanni
- **时间**: 2026-10-30T12:56:05Z
- **提交信息**: [Bugfix][HiSparse] Reserve in-flight imports' host pages at admission (#62979)

Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [dfe4d99](https://github.com/vllm-project/vllm/commit/dfe4d99e42fa7c49426fe3fe1ad134eaaf544765)

- **作者**: AlexHuang
- **时间**: 2026-10-30T12:28:32Z
- **提交信息**: [Bugfix][KV Offload] Preserve stored event prefix order (#63249)

Signed-off-by: Alex <alex.tech.lab@outlook.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Or Ozeri <oro@il.ibm.com>

### [24420b7](https://github.com/vllm-project/vllm/commit/24420b7a341af37a9bc3186e6fc6062512e0aa58)

- **作者**: Thomas Ortner
- **时间**: 2026-10-30T11:16:02Z
- **提交信息**: [hw-agnostic] Opt-in infrastructure for OOT plugins (#60218)

Signed-off-by: Thomas Ortner <boh@zurich.ibm.com>
Signed-off-by: Thomas Ortner <bohnstinglthomas@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [8a2a5e4](https://github.com/vllm-project/vllm/commit/8a2a5e4c40f92914fa670d28e348e6ffffe19632)

- **作者**: xaguilar-amd
- **时间**: 2026-10-30T11:07:17Z
- **提交信息**: [ROCm][Kimi-K3][Perf] Cut gfx942 MXFP4-to-int4 requant time under pure TP (#64004)

Signed-off-by: Xavier Aguilar <xavier.aguilarfruto@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Shanshan Shen <467638484@qq.com>

### [6de8c7b](https://github.com/vllm-project/vllm/commit/6de8c7ba51c75437f95571a94ab70ce8f1508466)

- **作者**: Bugen Zhao
- **时间**: 2026-10-30T11:05:48Z
- **提交信息**: [Rust Frontend] Support return_prompt_text (#64526)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [4d1376a](https://github.com/vllm-project/vllm/commit/4d1376a4922e28d814d79fae3b16d8de9d2d46cf)

- **作者**: Guanyi Chen
- **时间**: 2026-10-30T10:30:28Z
- **提交信息**: [KV Connector] Support heterogeneous TP sharing for hybrid KV cache in Mooncake Store (#54307)

Signed-off-by: Guanyi Chen <939416532@qq.com>
Signed-off-by: Zheng Zhou <zhouzh93@mail2.sysu.edu.cn>
Signed-off-by: z-zanez <zhouzh93@mail2.sysu.edu.cn>
Co-authored-by: Zheng Zhou <zhouzh93@mail2.sysu.edu.cn>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [c817cc0](https://github.com/vllm-project/vllm/commit/c817cc0f8be5f41477ca1944129d36c93724eba3)

- **作者**: Bugen Zhao
- **时间**: 2026-10-30T10:14:17Z
- **提交信息**: [Rust Frontend] Report completion_tokens_details only when reasoning tokens are counted (#64219)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [1114488](https://github.com/vllm-project/vllm/commit/1114488f15ebcaa600101f9b22f7a42b5440fc7a)

- **作者**: Bugen Zhao
- **时间**: 2026-10-30T10:12:00Z
- **提交信息**: [Rust Frontend] Support VLLM_SKIP_MODEL_NAME_VALIDATION (#64514)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [5cae6fd](https://github.com/vllm-project/vllm/commit/5cae6fd0c9292c3afc4167ea79241cd6b41685e0)

- **作者**: Bugen Zhao
- **时间**: 2026-10-30T10:09:19Z
- **提交信息**: [Rust Frontend] Log one structured access log event per HTTP response (#64232)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [deacc36](https://github.com/vllm-project/vllm/commit/deacc3670153845db2f013ea24085d6eaf338874)

- **作者**: aoshen02
- **时间**: 2026-10-30T09:44:53Z
- **提交信息**: [Bugfix][SleepMode] Exact-size, reusable pinned CPU backup for level-1 sleep (#64630)

Signed-off-by: Ao Shen <aoshen524@gmail.com>
Co-authored-by: Ao Shen <aoshen524@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [fac2ce2](https://github.com/vllm-project/vllm/commit/fac2ce2eb3633c44a104a66dbb30d0e6c7f4493e)

- **作者**: Dong Xu
- **时间**: 2026-10-30T09:24:25Z
- **提交信息**: [KV Offload] Emit self-describing events for recurrent state groups (#62613)

Signed-off-by: doxu <doxu@nvidia.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Or Ozeri <oro@il.ibm.com>

### [8472c01](https://github.com/vllm-project/vllm/commit/8472c01d81cbaeeccb3f18407282f23f3f1d101e)

- **作者**: Sherif Waly
- **时间**: 2026-10-30T09:21:13Z
- **提交信息**: [Bugfix] Preserve multimodal processor-cache hits during request eviction (#64495)

Signed-off-by: Sherif Waly <sherif.waly@mistral.ai>

### [96c80f8](https://github.com/vllm-project/vllm/commit/96c80f8af766a1d206d92d2fb01bb92234b9b443)

- **作者**: InChang Jeong
- **时间**: 2026-10-30T09:09:54Z
- **提交信息**: [Perf][Frontend] Build run-batch TypeAdapters once instead of per request (#63005)

Signed-off-by: inc-jeong <inc.jeong@navercorp.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [a23fd99](https://github.com/vllm-project/vllm/commit/a23fd9903418de0e1d3757bb23e2f1697eb066f3)

- **作者**: Bugen Zhao
- **时间**: 2026-10-30T09:06:50Z
- **提交信息**: [Rust Frontend] Support --root-path (#64222)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [b8141bd](https://github.com/vllm-project/vllm/commit/b8141bd33e1a586628426342464423c5b3f9a03b)

- **作者**: Thang Nguyen
- **时间**: 2026-10-30T09:04:23Z
- **提交信息**: [CI] Continue automatic PyTorch Fullgraph sharding (#64635)

Signed-off-by: Thang Nguyen <thangnguyenvn647@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [617135e](https://github.com/vllm-project/vllm/commit/617135eed34b9d0628028724951f16d5f1f78e1f)

- **作者**: CharlesWu
- **时间**: 2026-10-30T08:57:13Z
- **提交信息**: [Test][UMBP][6/10] Add embedded runtime and MORI integration coverage (#61794)

Signed-off-by: CharlesWu <Charles.Wu@amd.com>
Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [e152c70](https://github.com/vllm-project/vllm/commit/e152c70570f7850dc72a522b82339dc373b74ba9)

- **作者**: Bugen Zhao
- **时间**: 2026-10-30T08:47:09Z
- **提交信息**: [Rust Frontend] Report the generate response envelope like Python (#64513)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [515b875](https://github.com/vllm-project/vllm/commit/515b8753e32fd7e89c25270f423653822ba3ef3f)

- **作者**: Bugen Zhao
- **时间**: 2026-10-30T08:45:29Z
- **提交信息**: [Rust Frontend] Support --max-log-len (#64223)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [00ba900](https://github.com/vllm-project/vllm/commit/00ba900aa8e8bb766d37664c61f2dd1cfc710c2d)

- **作者**: Kunshang Ji
- **时间**: 2026-10-30T08:45:02Z
- **提交信息**: [XPU] Use GitHub release page index URL for vllm-xpu-kernels (#64633)

Signed-off-by: Kunshang Ji <jikunshang95@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [d8a7945](https://github.com/vllm-project/vllm/commit/d8a7945791c66440cdc4024112f7ff27d5cfe3e1)

- **作者**: Bugen Zhao
- **时间**: 2026-10-30T08:44:15Z
- **提交信息**: [Rust Frontend] Report prompt logprobs on streamed completions echo like Python (#64220)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [52737e0](https://github.com/vllm-project/vllm/commit/52737e03b85a31a57e524a0d070823a0e8318777)

- **作者**: Bugen Zhao
- **时间**: 2026-10-30T08:43:18Z
- **提交信息**: [Rust Frontend] Support return_weight_versions (#64218)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [2b313cd](https://github.com/vllm-project/vllm/commit/2b313cd97bf6052f213be407ca32fef1c2f991b6)

- **作者**: Bugen Zhao
- **时间**: 2026-10-30T08:42:21Z
- **提交信息**: [Rust Frontend] Export UMBP connector transfer metrics like Python (#64512)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [8bad43e](https://github.com/vllm-project/vllm/commit/8bad43e2c04bee07bf76366b5d89c39a3da03a73)

- **作者**: Reid
- **时间**: 2026-10-30T08:33:47Z
- **提交信息**: [Rust Frontend] Fix bad_words handling in /v1/completions (#48951)

Signed-off-by: reidliu41 <reid201711@gmail.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [0e34db7](https://github.com/vllm-project/vllm/commit/0e34db705f3bc120d17e955b39b2363dee37a1d3)

- **作者**: Thang Nguyen
- **时间**: 2026-10-30T08:33:40Z
- **提交信息**: [CI] Enroll the remaining LM Eval jobs in automatic sharding (30 jobs) (#64590)

Signed-off-by: Thang Nguyen <thangnguyenvn647@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [15a9677](https://github.com/vllm-project/vllm/commit/15a9677306b19201c21f54f668334d1a2531d2d7)

- **作者**: Thang Nguyen
- **时间**: 2026-10-30T08:33:11Z
- **提交信息**: [CI] Enroll the remaining Misc and Samplers jobs in automatic sharding (17 jobs) (#64596)

Signed-off-by: Thang Nguyen <thangnguyenvn647@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [4a8dc13](https://github.com/vllm-project/vllm/commit/4a8dc13adc0ecf5af962e5ad45e03b00618e7173)

- **作者**: Thang Nguyen
- **时间**: 2026-10-30T08:32:52Z
- **提交信息**: [CI] Enroll the remaining Compile, PyTorch, CUDA and ABI jobs in automatic sharding (29 jobs) (#64595)

Signed-off-by: Thang Nguyen <thangnguyenvn647@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [c5e37f1](https://github.com/vllm-project/vllm/commit/c5e37f1922f4481b320f019d6b1f3ac07dfe12ea)

- **作者**: Thang Nguyen
- **时间**: 2026-10-30T08:32:32Z
- **提交信息**: [CI] Enroll the remaining Distributed, EP and fault-tolerance jobs in automatic sharding (25 jobs) (#64593)

Signed-off-by: Thang Nguyen <thangnguyenvn647@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [fc84d05](https://github.com/vllm-project/vllm/commit/fc84d05acb202859be93c490001b6c9f968bca2c)

- **作者**: Thang Nguyen
- **时间**: 2026-10-30T08:32:12Z
- **提交信息**: [CI] Enroll the remaining Spec Decode jobs in automatic sharding (21 jobs) (#64592)

Signed-off-by: Thang Nguyen <thangnguyenvn647@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [a9a8222](https://github.com/vllm-project/vllm/commit/a9a822292611f9f29baca898212e05e40c768810)

- **作者**: Thang Nguyen
- **时间**: 2026-10-30T08:31:50Z
- **提交信息**: [CI] Enroll the remaining Kernels jobs in automatic sharding (30 jobs) (#64591)

Signed-off-by: Thang Nguyen <thangnguyenvn647@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [336d883](https://github.com/vllm-project/vllm/commit/336d883f41d8ded362febd5e5d6de7f227155e8e)

- **作者**: Thang Nguyen
- **时间**: 2026-10-30T08:31:13Z
- **提交信息**: [CI] Enroll 6 steps and 10 AMD mirrors in automatic sharding (#64569)

Signed-off-by: Thang Nguyen <thangnguyenvn647@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [8b10bda](https://github.com/vllm-project/vllm/commit/8b10bda57ceab3a741d2fb3718af48cef691023e)

- **作者**: Thien Tran
- **时间**: 2026-10-30T08:23:13Z
- **提交信息**: [Kernel] Add size-gated PDL to silu_and_mul_nvfp4_quant (#64494)

Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>

### [a20280f](https://github.com/vllm-project/vllm/commit/a20280f30e3169d33a7e21d1d117e9719bace00b)

- **作者**: kourosh hakhamaneshi
- **时间**: 2026-10-30T08:01:15Z
- **提交信息**: [Compile] Make the compile cache device-neutral with compile_on_one_rank (#63247)

Signed-off-by: Kourosh Hakhamaneshi <kourosh@anyscale.com>
Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: zjy0516 <riverclouds.zhu@qq.com>

### [8559100](https://github.com/vllm-project/vllm/commit/85591000403fc3bc3b4d0303e3a97bedab007763)

- **作者**: Bugen Zhao
- **时间**: 2026-10-30T07:49:14Z
- **提交信息**: [Rust Frontend] Support hybrid and external DP LB in `vllm-rs serve` (#64451)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [c20fc8a](https://github.com/vllm-project/vllm/commit/c20fc8a8570b5cfda377cf9a7ce5f10056bd3eaf)

- **作者**: Bugen Zhao
- **时间**: 2026-10-30T07:49:14Z
- **提交信息**: [Rust Frontend] Let the handshake owner serve a range of DP ranks (#64450)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [aa85ff7](https://github.com/vllm-project/vllm/commit/aa85ff7f13c6822bbfd183f8c4193bc12cd3e6a6)

- **作者**: Bugen Zhao
- **时间**: 2026-10-30T07:49:13Z
- **提交信息**: [Bugfix][Rust Frontend] Send the DP rendezvous in coordinated-DP INIT (#64449)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [8b9a434](https://github.com/vllm-project/vllm/commit/8b9a4341dbad4979a03e1776fe86e33944a72963)

- **作者**: bzsuni
- **时间**: 2026-10-30T07:41:34Z
- **提交信息**: [Bugfix] Retry incomplete HTTP response bodies (#62674)

Signed-off-by: bzsuni <bingzhe.sun@daocloud.io>

### [53624fc](https://github.com/vllm-project/vllm/commit/53624fc952d1a98af0ac77f51ab6fe0de9a669f4)

- **作者**: Juntian Liu
- **时间**: 2026-10-30T07:32:47Z
- **提交信息**: [Perf][DSv4.1] Bump FlashMLA to pass int64 positions to MegaAttn (#61971)

Signed-off-by: Juntian Liu <Juntianl777@gmail.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [2bfb8f1](https://github.com/vllm-project/vllm/commit/2bfb8f1674640c4cf91f525111a7757c9c9e2940)

- **作者**: Juntian Liu
- **时间**: 2026-10-30T07:32:32Z
- **提交信息**: [Perf][MoE] Use 32-row tiles in prepare_megamoe_inputs from 1024 tokens (#64467)

Signed-off-by: Juntian Liu <Juntianl777@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [c827025](https://github.com/vllm-project/vllm/commit/c82702543cc98c163e82d13b81b88aafcb7c218c)

- **作者**: Fanli Lin
- **时间**: 2026-10-30T07:26:51Z
- **提交信息**: [XPU][CI] Enable streaming input e2e test on XPU (#64285)

Signed-off-by: Lin, Fanli <fanli.lin@intel.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [fa9356a](https://github.com/vllm-project/vllm/commit/fa9356aba6bff6adde15f3e3b273675fe3852741)

- **作者**: Artur Fierka
- **时间**: 2026-10-30T07:26:29Z
- **提交信息**: [Bugfix][XPU] Add record_logical_topk_ready to XPUMLASparseImpl (#64065)

Signed-off-by: Artur Fierka <artur.fierka@intel.com>
Co-authored-by: Claude Sonnet 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [19e24f0](https://github.com/vllm-project/vllm/commit/19e24f0ca807e2938a3373674bc4b6cbe6994685)

- **作者**: siyu
- **时间**: 2026-10-30T07:23:23Z
- **提交信息**: [Fast Start] Stop preload groups when a daemon rank exits (#63692)

Signed-off-by: liusy58 <mg21330037@smail.nju.edu.cn>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [a70e48d](https://github.com/vllm-project/vllm/commit/a70e48deba60c53fd1c171bdb3d8adac1e0c070d)

- **作者**: Bugen Zhao
- **时间**: 2026-10-30T07:19:25Z
- **提交信息**: [Rust Frontend] Reject chat templates for native renderers (#64274)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [c05e9ed](https://github.com/vllm-project/vllm/commit/c05e9edb788ec87a65ca366a8fb45771d8002062)

- **作者**: Dilber
- **时间**: 2026-10-30T07:15:50Z
- **提交信息**: [Bugfix][Benchmark] Count tool call deltas as generated tokens in openai-responses (#62753)

Signed-off-by: Dilber P Shakir <dilbersha@gmail.com>
Co-authored-by: Chauncey <chaunceyjiang@gmail.com>

### [89a9a03](https://github.com/vllm-project/vllm/commit/89a9a03710810bea21cc42e2c52a85526a606655)

- **作者**: Guan-Ming Chiu
- **时间**: 2026-10-30T07:10:58Z
- **提交信息**: [Bugfix][MRV2] Fix DiffusionGemma runtime OOM via tiled logits projection (#51953)

Signed-off-by: Guan-Ming (Wesley) Chiu <105915352+guan404ming@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [e7aad41](https://github.com/vllm-project/vllm/commit/e7aad419dee663aa19ed199715d174cb94477525)

- **作者**: bzsuni
- **时间**: 2026-10-30T07:04:39Z
- **提交信息**: [Bugfix] Preserve batch audio handler error status codes (#61973)

Signed-off-by: bzsuni <bingzhe.sun@daocloud.io>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-10-31
**监控日期**: 2026-10-30
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7431
- **最后更新**: 2026-10-31T00:55:28Z

## 提交统计

- **昨日提交总数**: 14
- **提交者数量**: 11
- **主要提交者**: Weiming Liao, 汪志鹏, haic0

## AI分析总结

## 提交记录分析总结

### 1. 主要更新类型

本次 14 个提交分布较为均衡：
- **CI/构建优化**：5 个（占最大比例），集中在 ROCm 硬件验证和测试流程调整
- **Bug 修复**：5 个，涉及双工模式、TTS 编解码器、延迟门控等
- **功能新增**：2 个（独立阶段执行与外部路由、TTS 前缀缓存盐值）
- **硬件适配**：1 个（Ascend 升级 MindIE-SD 至 3.2.0）
- **模型改进**：1 个（MiniMax-H3 跨请求视频续传）

### 2. 关键变更点及与项目方向的关系

vllm-omni 的核心目标是提供"人人可用的简单、快速、低成本全模态模型服务"。本次提交与该方向高度一致：

- **多模态推理链路完善**：`[Frontend]` TTS 前缀缓存盐值、Qwen3-TTS 编解码器输出保留、双工模式终端监听时完成回合——这些直接服务于语音/视频模态的服务稳定性。
- **双工（Duplex）对话深化**：独立阶段执行与外部路由（#6883）是核心架构级功能，允许全模态流水线各阶段独立调度；配合 RTF 测量（#9182）和双工回合补全，说明项目正在系统性推进实时交互式全模态服务。
- **多硬件生态扩张**：ROCm 在 MI300 上的 READY 套件持续扩充（分布式缓冲区、扩散基线用例、VeRL-Omni 用例），Ascend 侧同步升级 MindIE，表明项目正加速 AMD 和国产芯片的生产级就绪。
- **视频生成连续性**：MiniMax-H3 支持跨请求基于缓存 latent 续传视频，为长视频/交互式视频生成奠定基础。

### 3. 对项目的影响和潜在意义

- **生产就绪度提升**：MI300 READY 套件扩展和 Ascend MindIE 升级意味着 vllm-omni 正从功能验证走向硬件厂商认可的稳定基线，有利于扩大部署场景。
- **架构灵活性增强**：独立阶段执行 + 外部路由让集成方可以自定义全模态编排（如自建路由、分阶段部署），这对"omni"定位至关重要。
- **CI 战略调整**：移除 Simple Test 合并、CPU 覆盖率移入 nightly、删除 MiniCPM-o 双工性能测试，反映 CI 在提速同时更依赖 nightly 深度测试，为频繁合入全模态功能腾出空间。
- **交互延迟可观测**：服务器端 RTF 测量提供了双工对话质量的量化手段，为后续性能优化建立基准。

### 4. 值得关注的技术点

- **#6883 独立阶段执行与外部路由**：这是本批中最重要的架构级变更，将全模态流水线的阶段解耦为可独立调度的单元，配合外部路由机制，是面向生产场景的关键能力。
- **AI 辅助开发常态化**：多个提交出现 Cursor、Claude Opus 5.5、Grok 4.7 等 Co-author，显示项目已广泛使用 AI 代理参与开发（包括代码生成与联合署名）。
- **奇数中位数延迟门控**：Qwen-Image 扩散延迟门控采用奇数中位数，是处理偶数样本延迟抖动的实用工程手法，减少 CI 误报。

### 5. 对项目发展的影响

结合 README 定位，本批提交体现出三条清晰的发展主线：

**其一**，全模态服务的实时性与交互性在持续深化——双工对话的回合完整性、RTF 基准、独立阶段执行共同指向低延迟的流式交互体验。**其二**，硬件覆盖矩阵在加速成熟——ROCm MI300 READY 套件已扩展到分布式缓冲、扩散模型和 VeRL-Omni 领域，加上 Ascend 适配，项目正构建广泛的硬件支持面。**其三**，CI/构建体系在向"高吞吐合入 + nightly 深度验证"模式演进，为持续快速迭代全模态功能提供保障。

总体而言，这批提交标志着 vllm-omni 正从多模态推理框架向具备生产级调度能力、多硬件覆盖和可观测性的全模态服务平台演进。

## 详细提交记录

### [8bcce47](https://github.com/vllm-project/vllm-omni/commit/8bcce4762205b35c2a25746791463fec4bc285be)

- **作者**: haic0
- **时间**: 2026-10-30T23:16:57Z
- **提交信息**: [CI/Build][ROCm] Add distributed buffer GPU smokes to MI300 READY (#9659)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Grok 4.7 <noreply@x.ai>

### [41d4790](https://github.com/vllm-project/vllm-omni/commit/41d479021214c8a6cce56008951ad7c8b986ce5d)

- **作者**: Rishabh Saini
- **时间**: 2026-10-30T22:00:19Z
- **提交信息**: [Feature / Core] Support Independent Stage Execution & External Routing (#6883)

Signed-off-by: Alex Brooks <albrooks@redhat.com>
Co-authored-by: Alex Brooks <albrooks@redhat.com>

### [ad2e585](https://github.com/vllm-project/vllm-omni/commit/ad2e58542d5c4621afee42dacb7f07a7b38cd00f)

- **作者**: haic0
- **时间**: 2026-10-30T20:26:54Z
- **提交信息**: [Bugfix][ROCm] Disable mbtree in the chunked MP4 byte compare (#9658)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [0817721](https://github.com/vllm-project/vllm-omni/commit/08177216af4b44cef54ec5bdc75c265a9f0cd697)

- **作者**: Rishabh Saini
- **时间**: 2026-10-30T16:25:17Z
- **提交信息**: [Frontend] TTS prefix-cache salts: default and caller-supplied (#8298)

Signed-off-by: RishabhSaini <rishabhsaini01@gmail.com>

### [1c8d26d](https://github.com/vllm-project/vllm-omni/commit/1c8d26d03fc27d1c104010489fcd6fda309908b5)

- **作者**: zzx
- **时间**: 2026-10-30T12:49:08Z
- **提交信息**: [Bugfix] Complete the duplex turn on a terminal listen (#8661)

Signed-off-by: zxy <1335108150@qq.com>
Signed-off-by: zxy <u7905843@anu.edu.au>

### [cda4a1e](https://github.com/vllm-project/vllm-omni/commit/cda4a1ef83b295ba332146a7709e6277725edc9f)

- **作者**: Weiming Liao
- **时间**: 2026-10-30T10:00:45Z
- **提交信息**: [Hardware][Ascend] Bump MindIE-SD to 3.2.0 [skip-CI] (#9573)

Signed-off-by: Weiming Liao <liaowm5@gmail.com>

### [da53f47](https://github.com/vllm-project/vllm-omni/commit/da53f47b81393eb8003a8824ffd447aecc8da414)

- **作者**: boatman
- **时间**: 2026-10-30T09:46:32Z
- **提交信息**: [Bugfix] Preserve MRv2 codec output without hidden states for Qwen3-TTS (#9626)

Signed-off-by: boatman <109857087+sphinxkkkbc@users.noreply.github.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [b5a6fd8](https://github.com/vllm-project/vllm-omni/commit/b5a6fd836185ed059980b9bbaac82f57a4e74142)

- **作者**: 汪志鹏
- **时间**: 2026-10-30T09:44:11Z
- **提交信息**: [Model] MiniMax-H3: Continue a previous video from cached latents across requests (#9342)

Signed-off-by: princepride <wangzhipeng628@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [7069e93](https://github.com/vllm-project/vllm-omni/commit/7069e93db1135b569f183629214d2c71eba4a00c)

- **作者**: hac17
- **时间**: 2026-10-30T09:40:01Z
- **提交信息**: [CI/Build][ROCm] Add one-card tiny diffusion base cases to MI300 READY (#9604)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>
Signed-off-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>
Co-authored-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>

### [3a936ae](https://github.com/vllm-project/vllm-omni/commit/3a936aee8fc31d1ba3cf25083dbad5338c100bfa)

- **作者**: chickeyton
- **时间**: 2026-10-30T08:47:49Z
- **提交信息**: [Core][Duplex] Measure server-side busy RTF per turn (RFC #8325) (#9182)

Signed-off-by: chickeyton <ngton2014@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [13b1b85](https://github.com/vllm-project/vllm-omni/commit/13b1b857d30084b2ba711d23065a80de73be8f9e)

- **作者**: wangyu
- **时间**: 2026-10-30T08:42:06Z
- **提交信息**: [CI/Build] Drop merge Simple Test and move CPU coverage to nightly (#9298)

Signed-off-by: wangyu <410167048@qq.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [630bd10](https://github.com/vllm-project/vllm-omni/commit/630bd10d83b4c6942f11fdc5fb49394096daac10)

- **作者**: amy-why-3459
- **时间**: 2026-10-30T08:07:16Z
- **提交信息**: [CI/Build] Remove MiniCPM-o duplex Seed-TTS performance test (#9635)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [4560304](https://github.com/vllm-project/vllm-omni/commit/45603043133fda3fe486d8e558c226d3391940f0)

- **作者**: hac17
- **时间**: 2026-10-30T07:19:01Z
- **提交信息**: [CI/Build][ROCm] Select the marked VeRL-Omni generate case on MI300 READY (#9605)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>
Signed-off-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>
Co-authored-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>

### [5af63b2](https://github.com/vllm-project/vllm-omni/commit/5af63b268a889a2d0594a9147461a90ca1e51de6)

- **作者**: NumberWan
- **时间**: 2026-10-30T07:11:15Z
- **提交信息**: [Bugfix] Take an odd median for the Qwen-Image diffusers latency gate (#9520)

Signed-off-by: NumberWan <wantszkin2003@gmail.com>
Co-authored-by: wangyu <53896905+yenuo26@users.noreply.github.com>

---
