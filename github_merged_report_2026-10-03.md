# GitHub Stars 合并报告 - 2026-10-03

**合并日期**: 2026-10-04
**监控日期**: 2026-10-03
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


**报告日期**: 2026-10-04
**监控日期**: 2026-10-03
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


**报告日期**: 2026-10-04
**监控日期**: 2026-10-03
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2876
- **最后更新**: 2026-10-04T00:36:44Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-10-04
**监控日期**: 2026-10-03
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


**报告日期**: 2026-10-04
**监控日期**: 2026-10-03
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6538
- **最后更新**: 2026-10-04T00:00:22Z

## 提交统计

- **昨日提交总数**: 39
- **提交者数量**: 5
- **主要提交者**: Wei Yihua, Chunan Zeng, eigen

## AI分析总结

# FlashInfer 昨日提交综合分析

## 一、主要更新概览

昨日 39 个提交呈现两条主线：一是围绕伞形 issue #5768 的大规模"deslop"去冗余化重构（约 35 条），覆盖注意力（MLA varq DCP、MiniMax Sparse Attention、XQA）、GEMM（BF16×FP4、分组 FP8）、MoE、Mamba/SSD 等全部 CAKE 内核家族；二是针对生产场景关键正确性的修复与新一代模型组件的性能优化。

## 二、关键变更

**架构中性化去重**：将 SM100/SM103（及部分 SM107/SM110）间近乎字节级相同的每架构源码副本合并为单一 `.cu`，由 JIT 按设备精确架构标志编译实例化。BF16×FP4 GEMM 删除逾 19 万行重复文件，GDN CP 与 VSA 分别删除 6.8 万与 1.6 万行，视觉塔与 MSA 清理数百文件。

**路由与宿主标准化**：删除按 `(M:N:K:num_sms)` 精确匹配的 JSON 目录与 token 表，改为按形状规则运行时路由，接受范围更广（如 SVDQuant 从 6 个 M 值扩展到任意 M ≥ 128）。宿主侧统一采用 tvm-ffi 薄启动器与共享工具，移除私有 device-guard、mutex 缓存与逐调用同步；TMA 描述符改为 `__grid_constant__` 按值传递，所有 launch（含首次）可被 CUDA Graph 捕获，逐调用开销下降 0.3–0.4 µs。

**性能优化**：CuTe DSL MLA 解码归约器引入批量预取与寄存器分组累积，消除拆分代价随 split 数线性增长的问题；DSA 稀疏注意力实现对调用方 fp32 行的直接累加（按 `S ≥ 4T` 形状启用），训练工作区缩小约 `S×2304` 字节；分块 LM head loss 将末块 scale+cast 融合进 GEMM epilogue；SM120 预填充优化 warp 分工与软重排。

**Bug 修复**：修复 CUDA 12.9 下 ptxas 对 `mov.b16`/`mov.b32` 行为不一致导致 SM120 DeepSeek FP4 字节解码错误的问题（#6027）；修复 TRT-LLM 融合归约核在 PDL 模式下读取过期 residual 的竞态；修复 CUTLASS ragged 后端首次 plan 拒绝 CUDA 图的回归；为 `mm_mxfp8`/`mm_fp4` 增加过期瓦片与 split-K 战术的运行时回退。

**测试与质量基建**：为 11 个 DeepGEMM 后端建立统一 catalog 加载器与基于 seed 的随机输入参考测试框架，以 SHA-256 校验约束生成源码不可手工改动。

## 三、项目影响

源码量净减数十万行，跨架构同步修改从"改两份副本"变为"改一处"，未来新增 SM 架构接入成本趋近于零。API 破坏性变更集中于 experimental 模块，公开 API 主体稳定。所有重构经 SASS 等价性验证或数值对比，基准持平或超越合并前基线。PDL 竞态与 CUDA 图回归修复消除了 vLLM、SGLang 等下游在生产场景下文本退化与崩溃的风险，CUDA 12.9 修复同步消除夜间 CI 的 22 个失败节点。

## 四、技术关注点

ptxas 跨版本工具链陷阱对 GPU 内核开发者具有普遍参考价值，32 位解包是跨版本安全写法。编译期常量与运行时参数的分层（SM_COUNT 折叠为编译定义、以 `-DQUANT_UNITS` 合并近似内核）以及两级注册表路由机制，为可扩展性提供了清晰模板。按工作负载形状选择累加路径与"保留必要非最优变体"的判断，体现了性能与可维护性的精细权衡。

## 五、整体意义

这批提交标志 FlashInfer 的 CAKE 内核生态正从"外部生成器导出的冻结产物"转型为与主干 JIT/tvm-ffi 深度整合的一等公民：统一注册表、加载路径、ABI 与验收流程齐备。项目由"单一架构高效内核集合"向"跨硬件、可演进、低维护成本的内核平台"演进，在保持性能 SOTA 的同时夯实生产可靠性，为 Blackwell 及后续架构服务更广泛推理负载奠定了可复制的架构基础。

## 详细提交记录

### [cff541a](https://github.com/flashinfer-ai/flashinfer/commit/cff541a4f6b1d6a076f8a64b52cc51a4959b5fc9)

- **作者**: eigen
- **时间**: 2026-10-03T23:04:17Z
- **提交信息**: fix(cake_dsv4_sparse_mla): regenerate the SM120 decode kernels with the 32-bit E2M1 unpack for CUDA 12.9 ptxas (#6027)

## 📌 Description

Follow-up to #5914 / #5949 / #6000 (SM120 Cake DeepSeek-V4 NVFP4
sparse-MLA decode) and #5983 (SM120 DeepSeek-V4.1 mixed-cache sparse-MLA
decode): regenerate the generated `csrc/cake_dsv4/sm_120a` **decode**
translation units so that the E2M1 → F16 convert sites extract the `.b8`
operand of `cvt.rn.f16x2.e2m1x2` with the 32-bit unpack `mov.b32 {b, _,
_, _}` instead of `mov.b16 {b, _}`. ptxas of CUDA 12.9 mis-assembles the
16-bit form at some sites of these kernels (wrong FP4 byte decoded,
finite and deterministic wrong results; CUDA 13.x assembles both forms
correctly). The internal CI's RTX Pro 6000 / CUDA 12.9 cell fails 22
nodes of `tests/attention/test_cake_sparse_mla_sm120_dsv4_nvfp4.py` on
`main` for this reason (the nightly shows the same failures); the
prefill units received the same change in #6004.

What changes:

- `cake_sparse_mla_dsv4_nvfp4_h{8,16,32,48,64,80,96,112,128}.cu` and
`cake_sparse_mla_dsv41_mixed_h{8,16,32,48,64,80,96,112,128}.cu`: 3 712
`mov.b16` → `mov.b32` unpack lines and their operand lines, plus the
provenance header. Same byte selected, same widened pair, so the
numerics do not change; kernel schedules, bindings, planners and the
Python route are untouched.
- The two manifests record the new identity / tree commit.

## 🔍 Related Issues

Internal CI pipeline for #6004 (RTX Pro 6000 / CUDA 12.9 cell): the
decode-file failures classified as pre-existing. Tracker #4254.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

- [x] Tests have been added or updated as needed (no test change: the
existing decode / prefill test files cover the change).
- [x] All tests are passing (`unittest`, etc.).
- `tests/attention/test_cake_sparse_mla_sm120_dsv4_nvfp4.py` inside the
FlashInfer CI `cu129` image (nvcc / ptxas 12.9) on RTX PRO 6000: 83
passed / 1 skipped (the planner-parity test, which needs the Cake kernel
module) — step `bf9e2d50`, `run-20261003-213228`; the family's JIT
module (`cake_sparse_mla_dsv4_nvfp4_sm120a_9137a41af15f`, one module
covering the nine decode units, the eight prefill units and the binding)
was built in that run by nvcc / ptxas 12.9 from the regenerated sources;
the prefill file in the same run: 71 passed (on `main` the same harness
fails 22 of them); the same file in the `cu130` image: 83 passed / 1
skipped (step `ffb17379`, `run-20261003-213404`; prefill file 71
passed).
- `tests/mla/test_cake_dsv41_mixed.py` (the DeepSeek-V4.1 mixed-cache
family, whose nine units are regenerated here as well; not part of the
internal CI run above): 95 passed / 1 skipped in the `cu129` image (step
`61523542`, `run-20261003-213900`), in the `cu130` image (step
`ad868a7b`, `run-20261003-214045`) and in the CUDA 13.3 fork environment
(step `c354990b`, `run-20261003-214231`), all on RTX PRO 6000; the
family's JIT module was built from the regenerated units in each run.
- `tests/attention/test_cake_sparse_mla_sm120_dsv4_nvfp4.py` and
`tests/attention/test_cake_sparse_mla_sm120_dsv4_nvfp4_prefill.py` on
RTX PRO 6000 and RTX 5090 (CUDA 13.3): PASS on both: RTX PRO 6000 policy
4 / prefill 71 / decode 83 + 1 skipped (step `2b387117`,
`run-20261003-213007`), RTX 5090 policy 4 / prefill 71 / decode 83 + 1
skipped (step `82f0c867`, `run-20261003-212049`).

## Reviewer Notes

Generated-source-only change (the Cake exporter regenerated both decode
families from the same kernel sources that produced the current `main`
units; the diff is the asm idiom lines and the provenance / manifest
lines). No performance claim is made for this PR; the unpack change
costs on the order of 0.2–0.4 % on the prefill kernels where it was
measured (#6004).

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Chores**
* Updated provenance and generation metadata for bundled GPU kernels,
aligning decode and prefill records with a consistent kernel revision.
* Kernel configurations and settings remain unchanged. This update does
not change user-facing behavior.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [a4493df](https://github.com/flashinfer-ai/flashinfer/commit/a4493df25fbe8bb625ea3a77722e9c74967fca75)

- **作者**: eigen
- **时间**: 2026-10-03T22:46:06Z
- **提交信息**: refactor(cake_msa_nvfp4_decode): regenerate as one source per program (#5875)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

Closes #5779

## Summary

Regenerates `flashinfer/experimental/msa_nvfp4_decode` (Cake-generated
NVFP4 sparse decode for
MSA top-k 16, SM100 / SM103 / SM107) from its producer with the
per-architecture duplication
removed, the kernel bindings reduced to thin launchers, and the dead
parts of the host path
retired. The persistent and short kernels are unchanged instruction for
instruction on every
architecture (see Validation); the kernel argument list loses six
parameters that no kernel ever
read, and the public preparation entry loses the workspace argument that
only fed them.

> **Public API change (experimental module).**
`flashinfer.msa_ops.prepare_msa_nvfp4_sparse_decode`
> no longer accepts `workspace_buffer`, and
>
`flashinfer.experimental.msa_nvfp4_decode.cake_backend.msa_nvfp4_decode_workspace_size`,
> `workspace_layout` and `bind_decode_payload` are removed. The split-KV
programs merge through
> distributed shared memory inside the cluster, so no caller-owned
scratch was ever read; the
> parameter existed only to size and zero buffers the kernels ignored.
Callers that passed a
> workspace drop the keyword; nothing else about the call changes. The
runner's `route` attribute
> now reads `"persistent"` or `"short"` (was `"swap_tsk"` / `"short"`),
and the launched program is
> exposed as `runner.program` / `runner.arch` instead of
`runner.module_name`. The module is
> documented as experimental and "may change without backward
compatibility".

## What changed

- **One source per program, shared across architectures.** The four
persistent kernels (split
factors 1 / 2 / 4 / 8) live once for SM100 and SM103, and the
short-sequence cluster kernel
once for all three architectures, under `csrc/cake_msa_nvfp4_decode/`;
the single architecture-dependent statement (the shared-memory
base materialization) is emitted under an exact `__CUDA_ARCH__` guard.
The `sm_100a/`,
`sm_103a/` and `sm_107a/` trees are deleted. SM107 keeps its own five
persistent programs (split
factors 1 / 2 / 4 / 8 and the last-round-split program) because its
persistent schedule differs in the V pipeline depth and the
PV-done wait — a tuning difference, not a copy — and the generator
cannot yet guard those
  differences inside one source (see "Not in this PR").
- **Shared headers.** The device helper preamble and the launch helpers
are emitted once
(`cake_msa_nvfp4_decode_device_common.cuh`,
`cake_msa_nvfp4_decode_host_common.cuh`) instead of
  once per kernel.
- **Thin launchers on `tvm_ffi_utils.h`.** Every binding uses
`ffi::CUDADeviceGuard`, `get_stream`
and the target's tensor checks; the private device-guard class, the
mutex + map around
`cudaFuncSetAttribute`, the device-attribute queries and the private
tensor-check helpers are
gone. The dynamic shared-memory opt-in is a one-time property of the
kernel handle.
- **Kernel ABI.** Six parameters that no kernel body read (`partial_O`,
`partial_M`, `partial_D`,
`split_completion`, `kv_indptr`, `task_request`) are removed from the
kernels and bindings;
the metadata kernels read the sequence table they were aliases of. This
is the only device-side
change and it is validated structurally (tests + paired timing), not by
SASS identity.
- **Registry.** `cake_jit.py` lists one argument plan per route and each
program once with the
architectures it serves (`PROGRAMS`: route, split factor, tail flag,
sources, compile flags,
per-SM-count cluster capacity for the tail program); the 750-line
per-module literal with its
repeated argument plans is gone. `select_program(arch, splits=...,
tail=...)` and
`short_program(arch)` replace the module-name lookups. The JIT library
is keyed `<program>_<arch>`.
- **Host path.** Device capability and SM count come from FlashInfer's
cached helpers; the
workspace sizing, carving and zeroing are removed; the optional `out` /
`lse` outputs are
  allocated with `new_empty` on the query tensor.
- **Packaging and tests.** `csrc/**` added to the package's
`package-data`; the two workspace
tests and the test that asserted the structure of the registry literal
are replaced by a
behavioural registry test (every architecture registers the 1 / 2 / 4 /
8 ladder and the short
program; each registered program builds a JIT spec) and a test that
drives every split factor
through its program; all other tests unchanged. README and benchmark
updated (the benchmark
  records `route` / `splits` / `tail` per row).

Net: 57,041 -> 24,697 lines (-32,344, -56.7 %), 36 -> 26 files under the
module; the generated kernel
sources go from 16 kernel/binding pairs (5 + 5 + 6 per architecture) to
10 (4 persistent shared by SM100 /
SM103, 1 short shared by all three, 5 SM107 persistent), each pair one
`_kernel.cu` + one `_binding.cu`,
plus the two shared headers.

## Validation

**Device code equivalence (mechanical steps).** With the kernel ABI
still in place (an intermediate commit of this branch), for
every program x architecture the SASS of the regenerated build equals
the SASS of the previous
per-architecture file after normalising the kernel symbol / namespace
hash (compiled with the
repository's JIT flags):

| program | sm_100a | sm_103a | sm_107a |
|---|---|---|---|
| persistent, splits 1 | equal | equal | not produced: the toolkit
available to this change lacks compute_107a |
| persistent, splits 2 | equal | equal | not produced |
| persistent, splits 4 | equal | equal | not produced |
| persistent, splits 8 | equal | equal | not produced |
| short (cluster 8) | equal | equal | not produced |
| persistent, splits 2, last-round split | n/a | n/a | not produced |

`equivalent: true` for `[sm_100a, sm_103a]`: 10 base kernels vs 10
regenerated, 5 distinct bodies per architecture, nothing missing or
introduced. The export protocol's own paired measurement of that stage
(same B200, production dispatcher vs regenerated module, CUPTI, CUDA
graphs, 3 counterbalanced groups) passed all 16 sm_100a rows at
0.983-1.018x with bitwise-equal outputs.

**Numerical tests (final tree).** `pytest
tests/experimental/test_cake_msa_nvfp4_decode.py
tests/msa_ops/test_msa_nvfp4_decode_sm100.py`
on a B200 (320 passed, 1 skipped) and a B300 (320 passed, 1 skipped) --
the one skip on each is the
last-round-split test, which skips where no such program is registered,
by design; the CPU planner tests (split-factor
rule, tail-plan rule, validation) on both. SM107 (R200, CUDA 13.5
toolkit): the published
`tests/experimental/test_cake_msa_nvfp4_decode.py` passes (63 passed);
the broader run of both files on the
same device was 320 passed / 1 failed, the failure being the first
version of the split-factor coverage test
(it assumed batch sizes that cannot request every factor on a
148-212-CTA part; the published test derives
one batch per registered factor from the device's resident-CTA capacity
and asserts the selection).

**Performance (final tree): the producer's export protocol, one sealed
run per architecture.** Each row
times the regenerated module (`module`) against the producer's reference
execution of the same program
(`ref`) on the same GPU: CUPTI GPU span, symmetric external CUDA graphs,
three counterbalanced groups,
200 ms warm-up + 100 ms reportable budget per arm and group, cold L2,
bitwise output parity between the two
arms, gate `ref/module >= 0.97` per row plus order-bias and drift
bounds. The three runs were measured on
different hosts (B200, B300 SXM6 AC, R200) and are reported as three
runs, not one merged table.

| row | program | SM100 (B200) ref us | module us | ratio | SM103 (B300)
ref us | module us | ratio | SM107 (R200) program | ref us | module us |
ratio |
|---|---|---:|---:|---:|---:|---:|---:|---|---:|---:|---:|
| `tp1_b128_kv8k_q1` | persistent, splits 1 | 45.312 | 45.407 | 0.9979x
| 43.904 | 44.001 | 0.9978x | persistent, splits 2, tail | 27.104 |
27.136 | 0.9988x |
| `tp1_b32_kv64k_q1` | persistent, splits 1 | 15.808 | 15.873 | 0.9959x
| 15.776 | 15.712 | 1.0041x | persistent, splits 1 | 12.384 | 12.320 |
1.0052x |
| `tp1_b32_kv64k_q1_ragged` | persistent, splits 1 | 15.840 | 15.904 |
0.9960x | 15.681 | 15.680 | 1.0001x | persistent, splits 1 | 12.448 |
12.384 | 1.0052x |
| `tp1_b8_kv100k_q1` | persistent, splits 4 | 9.759 | 9.759 | 1.0000x |
9.407 | 9.440 | 0.9965x | persistent, splits 4 | 7.808 | 7.808 | 1.0000x
|
| `tp1_b1_kv200k_q1` | persistent, splits 8 | 7.296 | 7.360 | 0.9913x |
7.104 | 7.136 | 0.9955x | persistent, splits 8 | 6.272 | 6.144 | 1.0208x
|
| `tp2_b64_kv16k_q1` | persistent, splits 1 | 15.808 | 15.872 | 0.9960x
| 15.521 | 15.520 | 1.0001x | persistent, splits 1 | 12.416 | 12.352 |
1.0052x |
| `tp4_b128_kv8k_q1` | persistent, splits 1 | 15.808 | 15.872 | 0.9960x
| 15.552 | 15.552 | 1.0000x | persistent, splits 1 | 12.384 | 12.384 |
1.0000x |
| `tp4_b1_kv1m_q1` | persistent, splits 8 | 7.328 | 7.168 | 1.0223x |
7.200 | 7.041 | 1.0226x | persistent, splits 8 | 5.824 | 5.664 | 1.0282x
|
| `tp8_b128_kv64k_q1` | persistent, splits 1 | 15.711 | 15.712 | 0.9999x
| 15.584 | 15.552 | 1.0021x | persistent, splits 1 | 12.416 | 12.416 |
1.0000x |
| `tp1_b2_kv257_q1_tail` | short (cluster 8) | 5.856 | 5.887 | 0.9947x |
5.760 | 5.728 | 1.0056x | short (cluster 8) | 5.344 | 5.248 | 1.0183x
(validity not established, see below) |
| `tp1_b32_kv8k_q2` | persistent, splits 1 | 25.631 | 25.728 | 0.9962x |
24.864 | 24.896 | 0.9987x | persistent, splits 2, tail | 18.080 | 18.016
| 1.0036x |
| `tp1_b32_kv8k_q4` | persistent, splits 1 | 45.023 | 45.056 | 0.9993x |
43.168 | 43.233 | 0.9985x | persistent, splits 2, tail | 26.112 | 26.048
| 1.0025x |
| `tp1_b32_kv8k_q8` | persistent, splits 1 | 74.272 | 74.303 | 0.9996x |
70.433 | 70.433 | 1.0000x | persistent, splits 1 | 43.552 | 43.456 |
1.0022x |
| `tp4_b32_kv64k_q8` | persistent, splits 1 | 25.983 | 26.047 | 0.9975x
| 25.345 | 25.408 | 0.9975x | persistent, splits 2, tail | 18.271 |
18.176 | 1.0052x |
| `tp1_b8_kv100k_q8` | persistent, splits 1 | 25.856 | 25.888 | 0.9988x
| 25.056 | 25.120 | 0.9975x | persistent, splits 2, tail | 18.272 |
18.208 | 1.0035x |
| `tp1_b16_kv64k_q1` | persistent, splits 2 | 12.192 | 12.160 | 1.0026x
| 11.840 | 11.808 | 1.0027x | persistent, splits 2 | 9.632 | 9.600 |
1.0033x |

SM100: 16/16 pass, geomean 0.9990x, min 0.9913x (`tp1_b1_kv200k_q1`),
max 1.0223x (`tp4_b1_kv1m_q1`); all outputs bitwise equal.
SM103: 16/16 pass, geomean 1.0012x, min 0.9955x (`tp1_b1_kv200k_q1`),
max 1.0226x; all outputs bitwise equal.
SM107: 15/16 pass, geomean (15 rows) 1.0056x, min 0.9988x, max 1.0282x;
all 16 outputs bitwise equal.
The SM100 row `tp4_b1_kv1m_q1` (6.8-7.3 us kernel) was measured twice
under the same protocol: 0.977x in the
first sealed run and 1.022x in a second measurement on another B200 of
the same node; both receipts are kept,
the table shows the second (the spread is one CUPTI timestamp quantum on
a 7 us launch; the row measured
1.023x / 1.028x on SM103 / SM107). The SM107 row
`tp1_b2_kv257_q1_tail` (5.3 us short kernel) passed correctness and
speed (1.018x) but not the protocol's
measurement-validity bounds on R200 (order-bias 0.081 vs 0.08; two
re-measures hit the 50k-sample cap of the
timing controller at ~5 us per launch); it is reported as "validity not
established", not as a regression.

The repository benchmark `benchmarks/bench_cake_msa_nvfp4_decode.py` was
not run as a paired before/after
of the FlashInfer tree in this change; the protocol measurement above is
the performance evidence. Per-call
launch count unchanged (one kernel per prepare; graph replay unchanged);
prepare no longer allocates or
zeroes a workspace.

`pre-commit` (`uvx pre-commit run --from-ref origin/main --to-ref HEAD`,
the repository pins): all hooks pass. Two findings were fixed at the
generator before the push so the shipped text is reproduced: ruff-format
re-wrapped three statements of the test module, and ruff-check B009
replaced one `getattr(module, "run")` in `cake_backend.py` with
attribute access.

## Not in this PR (follow-ups)

- **SM107 folded into the shared sources.** The SM107 persistent
schedule differs from SM100 /
SM103 in two pipeline constants (V pipeline depth, PV-done wait).
Guarding them inside one
source needs the generator to emit the differing region under an
architecture guard while the
loader still compiles one text per device; today the exporter requires
byte-identical sources
behind a shared file. When that lands the six SM107 programs collapse
into the shared five plus
  the tail program.
- **Split factor as a template parameter of one persistent kernel.** The
four split programs differ
structurally (cluster dimensions, barrier arrival counts, lane masks,
rank loops are all traced
constants), so a `template <int S>` kernel that reproduces the same SASS
needs these to become
compile-time expressions in the generator first. The last-round-split
program already subsumes
the plain two-way split on SM107 and would become a runtime flag at the
same time.
- **Runtime occupancy query for the tail program.** `tail_plan` reads a
measured per-SM-count table
of co-schedulable cluster CTAs (`cluster_capacity`, currently the 212-SM
part only). Replacing it
with `cudaOccupancyMaxActiveClusters` needs a host-only query entry next
to each program's launch
entry, which the generator will provide once for all Cake families; the
table stays until then,
  so the corresponding checkbox of #5779 remains open.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
  * Added MSA NVFP4 decode support for SM107 alongside SM100 and SM103.
* Added persistent and short-item execution routes, including split
processing and tail handling for supported workloads.
* Simplified decode preparation by removing the need to provide a
workspace buffer.

* **Bug Fixes**
* Improved architecture-specific shared-memory handling across supported
devices.

* **Documentation**
* Updated the decode guide and benchmark descriptions to cover supported
devices and execution routes.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [1a0da42](https://github.com/flashinfer-ai/flashinfer/commit/1a0da4294ad55da729541a3186d94d12f0b5468c)

- **作者**: eigen
- **时间**: 2026-10-03T22:36:21Z
- **提交信息**: feat(cake_lm_head_loss): fuse the last chunk's dW scale + cast into its GEMM epilogue; per-geometry GEMM programs (#5680) (#5897)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the
> **vast majority of performance benchmark shapes**, matching them
otherwise.

## Summary

Follow-up to #5752 (tracking issue #5680): the chunked LM-head loss
(`flashinfer.chunked_lm_head_loss` /
`chunked_lm_head_logprob`, `flashinfer/experimental/cake_lm_head_loss/`)
gets a shorter backward and faster `dX` / `dW` GEMMs on
SM100 (B200 / GB200) and SM103 (GB300). Same API, same input contract,
same memory rule; every change is bitwise against the
previous kernels on the tested shapes (see Numerics). Regenerated
programs for both architectures from one exporter run per
architecture; the two runs produce byte-identical files (sha256-verified
against the exporter's `applied.json`). The eighth push
regenerates the *delivered form* without touching the kernels'
arithmetic or tile schedules: one architecture-neutral program per
kernel form shared by the SM100 and SM103 records (the four logits GEMM
forms excepted: their SM103 lowering stages the C tile
in shared memory for a TMA store behind a six-stage operand pipeline
while SM100 stores from registers behind seven, so those
carry one unit per architecture), the call geometry and the per-chunk
rule outputs as launch scalars (one
geometry-free record per architecture), one shared host launcher per
distinct host contract and a compact registry --
27 kernel translation units / 20,580 generated lines against 160 /
153,144 before (Increment 8).

### What changed

- **Fused last-chunk `dW` cast.** The last chunk's `dW` GEMM is deferred
to the backward, where the upstream scalar is known,
and its epilogue writes the scaled, rounded gradient directly (two new
stages, `gemm_dw_cast_bf16` / `gemm_dw_cast_f32`, with
the `dW` GEMM's ABI). A one-chunk call (`T <= chunk_size`) no longer
allocates the FP32 `[V, H]` accumulator at all (3.54 GiB = 3.81 GB at
`H = 6144, V = 154880`) and no call runs the separate `scale_cast` pass
over `dW`. The forward keeps the deferred
chunk's BF16 `dlogits` rows and a view of the matching `X` rows (both
inside the chunk budget). Knob `fuse_dw_cast` on both
entry points (default on; `FLASHINFER_CAKE_LM_HEAD_LOSS_FUSE_DW_CAST=0`
restores the accumulate + cast path).
- **Preferred-cluster launch of the `dX` / `dW` GEMMs.** Both GEMMs run
as A-sharing two-pair clusters launched with the
preferred cluster dimension: the generated host binding passes
`cudaLaunchAttributePreferredClusterDimension` (4, 1, 1)
next to the required cluster (2, 1, 1), the hardware forms four-CTA
clusters where the GPC topology allows and pairs
elsewhere, and the kernel reads the runtime cluster size (barrier
counts, multicast masks, work-item indexing). The record
geometry declares the required cluster; the grid rules count the
four-CTA items. Same `dX` / `dW` values.
- **512-wide `dX` tile.** The `dX` GEMM's pair tile covers 512 columns
of `H` (two accumulator blocks per pair, one `A` tile
feeding both) where `H % 512 == 0` and the items fill a wave; 256
otherwise. Bitwise equal to the 256-wide form.
- **Raster height by geometry.** The logits and `dW` GEMMs pick their
grouped-raster height per chunk from the geometry and
the chunk's row count, mirroring the production launchers' rules
exactly: `H >= 7168` and chunk rows `> 2048` select the
`gemm_logits_g16` instance and the `_g32` `dW` instances (accumulate and
fused cast); the default 6144 x 154880
geometry's chunks of more than 4096 rows run the `dW` GEMMs with
`group_m` 16 on both architectures (`_g16`: -3.0..-3.4 %
`dW` GEMM time at chunk 8192 / 8039 on B200, 1.043 -> 1.008 / 1.011 x
cuBLAS; -3.1..-3.2 % on GB300, 1.042 -> 1.008 /
1.010 x; same-GPU power ABAB against the previous default, cuBLAS
control flat);
the default geometry's chunks of 2049..4096 rows run the `dW` accumulate
and the fp32 fused cast with a 2-D blocked
raster of 12 column tiles per block on both architectures (`_gn12`:
SM103 -1.9..-2.3 % `dW` GEMM time / -1.9 % J/TF at
rows 4096, -1.6..-1.9 % / -1.5..-1.6 % at 3943, 0.998-1.000 ->
0.976-0.977 x cuBLAS; SM100 -2.0..-2.3 % / -2.2..-2.5 % at rows 4096 /
4021,
-1.9 % / -1.9..-2.1 % at 3943, 1.009-1.011 -> 0.987-0.992 x cuBLAS; the
bf16 cast keeps the 1-D raster);
  every other chunk runs the default raster. Since the eighth push the
registered program carries one geometry-free record per architecture
(`cake_lm_head_loss_<arch>`): the raster heights, the
K-slice count and the call geometry (`H`, `V`, the chunk's row count)
are launch scalars of the GEMM kernels
(`cake_backend.gemm_scalars`, mirrored from the kernel source's own
launch contract and checked by the exporter), and the host
selects only *structural* forms by rule output, never by shape:
`gemm_logits[_mcnt]`, `gemm_dw_acc[_gn]`, `gemm_dw_cast_bf16`,
`gemm_dw_cast_f32[_gn]`, `gemm_dx[_s][_tn256|_st3]` (device-count form,
2-D blocked raster, K-sliced form, 512 -> 256 tile
  fallback, 3-deep operand ring). An explicit knob set
(`gemm_tuning=` / `FLASHINFER_CAKE_LM_HEAD_LOSS_GEMM_TUNING`, e.g.
`{"logits": {"group_m": 16}}`) wins over the rule
for the knobs it names, as the launchers' explicit tuning does.
Knob-only, bitwise (same reduction order per element).
- **Shorter logits raster for chunks of 31+ row tiles at the default
geometry.** Below hidden 7168 a chunk of at least 3841 rows
(31 row tiles of 128: the 3884 / 3943 / 4021 / 4096-row chunks of the
acceptance batches and every chunk of the 8192-row chunking) runs
the logits GEMM with the 16-row-tile grouped raster (`gemm_logits_g16` /
`gemm_logits_nostats_g16`, now registered for the default
geometry's records as well) instead of the 32-row one; chunks of up to
30 row tiles keep the default raster. Tile order only: which CTA
accumulates which element and the per-element K order are unchanged, so
logits, row statistics and every gradient are bitwise identical
to the previous programs (`torch.equal` at the ten default-geometry
chunk sizes on both architectures). Same-GPU A/B against the previous
raster (5 s x 3 windows, cuBLAS control): SM103 -0.1 / -0.4 / -0.8 /
-0.6 / -0.7 / -0.6 % logits-GEMM time at 3884 / 3943 / 4021 / 4096 /
8039 / 8192 rows, SM100 -0.2 / -0.6 / -1.5 / -1.5 / -1.0 / -1.2 % (J/TF
within 0.3 pt of the time), ties (identical schedule) at every
smaller chunk; the GEMM is 55-60 % of a cross-entropy step at chunk
4096, so about 0.3-0.9 % of the step. `raster_variant(hidden, rows,
arch)` now returns the pair `(logits group_m, dW group_m)` with `None`
for an unchanged slot.
- **`dW` epilogue on SM103.** The `dW` accumulate GEMM drains through
the staged shared-memory path with L2 reductions
(`red.global.add.v4.f32`; one FP32 add per element per chunk, fixed
order -- the same value as the TMA bulk reduce-add) at
every chunk size: under the `group_m` 16 raster it also beats the TMA
bulk reduce-add above 4096 rows, so that form is no
  longer selected. Bitwise accumulate.
- **`dX` TMA-store epilogue.** The `dX` GEMM stages its output tile in
shared memory and writes `dX` (and the K-slice slabs)
with TMA bulk stores on both architectures (GB300: -1.0 % `dX` GEMM time
/ -1.2..-1.5 % J/TF at chunk 4096, -0.7..-0.8 % /
-0.9..-1.0 % at 8192, 1.013-1.019 -> 1.001-1.004 x cuBLAS J/TF; B200:
-0.2..-1.5 % at 4096, -0.6..-1.1 % at 8192,
0.988-0.993 x cuBLAS; the drain between work items shrinks 37 %).
Bitwise identical to the per-thread stores.
- **`dX` operand ring at long chunks.** The 512-wide `dX` tile runs a
3-deep operand ring for the default geometry's
chunks of more than 4096 rows on both architectures
(`gemm_dx[_s<k>]_st3`: -0.3..-1.1 % `dX` GEMM sustained time at rows
8039-8192 on B200, -0.5..-0.6 % on GB300; the 256-wide fallback keeps
its depth). Bitwise: the ring depth only changes
  when a stage is refilled.

- **Workspace bound for compacted rows.**
`lm_head_loss_workspace_size(..., compact_rows=True)` now covers every
possible tail
row count of the compacted plan (the valid-row count modulo the chunk
may take more K slices than any full-`T` chunk); compacted
callers may receive a larger size, up to `(S_max - 1) * C * H * 4` bytes
(e.g. +384 MiB at `H = 8192`, chunk 4096). The previous
bound was too small for such tails (`prepare_lm_head_loss` refused the
buffer); the public entry points size from their own plan
  and are unchanged.
- **`dX` tile at wave-quantized tails (SM100).** On SM100 the `dX` GEMM
at one-slice, badly wave-quantized chunk tails (e.g. the
3591 / 3791-row tails of `T = 65031` / `32463` at chunk 4096) falls back
to the 256-wide cluster form (`gemm_dx_tn256`): -7.0..-8.8 %
sustained time, bitwise identical `dX`; SM103 unchanged
(`DX_WIDE_MIN_EFF`).

#### Increment 3 — fused dX finalize

The backward finalized `dX` in several passes: a K-sliced `dX` GEMM left
its FP32 K-slice slabs for the host to add with a chain of in-place
`add_` launches, and a compacted call cast the compact rows to BF16,
zero-filled a `[T, H]` tensor and `index_copy_`-scattered the rows into
it. Two row kernels now do this work in one pass each: `slab_sum` adds
the slabs into the chunk's rows of `dX_acc` in ascending slab order (one
RN add per element per slab — the evaluation order of the `add_` chain —
with `dX_acc` read and written once), and `scale_cast_scatter_bf16`
writes the `[T, H]` `dX` directly: `bf16(g * dX_acc[compact row])` on
the valid rows (addressed through the inclusive int32 scan of the
valid-row mask and validated against the compact index), exact zeros
elsewhere. The same FP32 operations in the same order, so `dX` is
bitwise the previous path's (`torch.equal` on both architectures for the
loss and log-probability entries, with and without ignored rows,
K-sliced and single-slice chunks);
`FLASHINFER_CAKE_LM_HEAD_LOSS_DX_FINALIZE=0` restores the previous host
path. Host mirror: `valid_rows(labels, mask=...)` keeps the bool
valid-row mask next to the compact index (`ForwardResult.row_valid`),
`finalize_dx` / `scale_cast_scatter` at the dX output boundary,
`slab_sum` launch keys per sliced chunk, `Plan.dx_finalize` / `dx_cast`,
binding keys, memory report, reference-engine forms, README / docs; the
tests cover the switch bitwise on the reference backend and on the
generated program. Generated programs: every record of both
architectures gains `slab_sum` and `scale_cast_scatter_bf16` (two new
units per architecture); the remaining units were regenerated by the
current exporter (identity vs the previous export: see the commit
message).

#### Increment 4 — dW accumulate GEMM on a side stream (host only)

Each chunk's weight-gradient accumulate GEMM depends on the chunk's row
gradients only, not on the dX GEMM launched right before
it, yet it queued behind that GEMM's last wave (GLM-class 4096-row
chunks: 768 dX work items on 76 CTA pairs = 11 waves at 0.919
fill). The host now forks a per-device side stream after the chunk's
`row_grad`, launches the accumulate there and joins before
the next chunk reuses the chunk buffer and before the call returns; a
deferred last chunk's cast GEMM and the flat casts stay on
the caller's stream. Kernels, buffers, launch order per kernel and
numerics are unchanged, so `loss` / `logp` / `dX` / `dW` are
bitwise the single-stream path's.
`FLASHINFER_CAKE_LM_HEAD_LOSS_DW_STREAM`: `auto` (default) = calls of
three or more chunks, `1`
= every multi-chunk call, `0` = never — two-chunk calls pay the
cross-stream join without an overlap gain and a one-chunk call
defers its only accumulate to the backward. The prepared runner and the
eager entry points share the key walk; a CUDA graph
captured from the runner records the fork / join. No generated program
changes: the packages of the third push are reused as-is.

#### Increment 5 — hidden valid-row count

A compacted call (some labels `-100`) no longer counts its valid rows on
the host
(`sum().item()`) and forms their index (`nonzero`) before its first
launch. The index is formed on the device
(`labels >= 0` -> inclusive int32 `cumsum` -> `searchsorted`), chunk 0's
rows of `X` are gathered by a new row kernel
(`gather_rows_bf16`: `out[r] = X[idx[r]]` for `r < min(count,
num_rows)`, exact zeros after, the count read from device
memory) and chunk 0's logits GEMM runs in a device-count form
(`gemm_logits_mcnt` / `gemm_logits_nostats_mcnt`, with
`_g16` at the long raster: every store and statistics write bounded by
`min(count, M)`, `M` and the raster at the buffer
extent `min(chunk_size, T)`); the count reaches the host through a
pinned cell and a CUDA event only after both are
queued, so the host waits for three small kernels and a 4-byte copy
instead of the count and the `nonzero`. Every row
valid -> the uncompacted plan with chunk 0's GEMM already done; every
row ignored -> zeros; otherwise the compacted plan
with chunk 0's gather and GEMM skipped. Same kernels per row: `loss` /
`logp` / `dX` / `dW` are bitwise the previous
path's on both architectures. Knob
`FLASHINFER_CAKE_LM_HEAD_LOSS_HIDDEN_COUNT` (default on; `0` restores
the previous
path); calls the device-count GEMM cannot serve (an `X` that needs a
contiguous copy or whose base is not 16-byte
aligned) and the prepared runner keep the previous path. Generated
programs: every record of both architectures gains
`gather_rows_bf16` and the four device-count logits instances (15 new
stages per architecture, 26 new unit files: the
gather kernel's unit is shared by the three geometry records); the other
134 unit files per architecture are
byte-identical against the previous delivery (sha256 lists in the
exporter's `applied.json`; the two architecture runs
produce byte-identical files).

#### Increment 6 — CUDA 13.0 on SM103

Host only, no generated-unit change.
`cake_jit.toolchain_workaround_flags(arch)` appends `-Xptxas -O0` to the
SM103 programs' nvcc flags on CUDA 13.0 (nvcc 13.0.x) (the sixth through
eighth pushes used -O1; the ninth push moves to -O0, see below), and
`cake_jit.toolchain_runs_hidden_count(arch)` is False for SM103 on that
toolchain, so `cake_backend.hidden_count_eligible` sends those calls
down the host-count path (valid rows counted and indexed on the host
before the first launch — the same kernels per row, bitwise the same
`loss` / `logp` / `dX` / `dW`) and `generated_program_available` does
not require the gather stage there. Every other architecture / toolchain
pair is untouched. Tests: `test_toolchain_workaround_flags`,
`test_toolchain_runs_hidden_count` and the eligibility-rule cases (13.4
→ eligible on both architectures; 13.0 → SM103 ineligible, SM100
unaffected). README toolchain note and the CLAUDE.md knob row describe
both. Validation: protocol re-check of the generated programs against
the source on B200 and GB300 (prepare() over every shape, no unit
change), this test file under nvcc 13.3 on both architectures (175
passed / 1 skipped on each), and under nvcc 13.0 on GB300 (172 passed /
3 skipped / 1 failed twice, cold and warm; the failure is the
pre-existing torch-2.9 tolerance row, and the three skips are the
hidden-count device tests).

#### Increment 7 — the hidden valid-row count for calls of three or more
chunks

Host only, no generated-unit change. `hidden_count_eligible` now also
requires `ceil(T / chunk_size) >= HIDDEN_COUNT_MIN_CHUNKS` (3). The
fifth push's hidden valid-row count carries a fixed host cost per call
ahead of chunk 0's logits GEMM — in the measured facade path about 1.2
ms (cross-entropy) / 1.0 ms (log-probability) of forward host time on
SM100 and 1.0 / 0.5 ms on SM103 — which that GEMM hides only from three
chunks on; a one- or two-chunk call paid it on the critical path (the
fifth push's adoption measurement timed the CUPTI kernel span, which
does not carry host time), so those calls had become 2–14 % slower per
step than the head before the hidden count while every longer call
gained. Shorter calls now take the host-count path on either value of
`FLASHINFER_CAKE_LM_HEAD_LOSS_HIDDEN_COUNT`; every output stays bitwise
the same. Tests: the eligibility rules cover one, exactly two, three and
four chunks at two chunk sizes; the device switch test runs one- to
four-chunk calls with the short ones asserted on the host-count path;
the device kernel test moves to four-chunk calls; the binding-cache test
follows the rule.

#### Increment 8 -- the delivered form: one program per kernel form,
launch scalars, shared launchers, compact registry

Regenerated from the same kernel source; no change to the kernels'
arithmetic, tile schedules, pipelines or epilogues, and no
change to the public API, the input contract, the numerics or the memory
rule. What the reviewer's duplication audit of the
seventh push flagged is gone by construction:

- **One translation unit per kernel form, shared by both
architectures.** The SM100 and SM103 records point at the same
`csrc/cake_lm_head_loss/<unit>_kernel.cu` (the per-architecture lowering
sits under `__CUDA_ARCH__` guards inside the unit)
instead of a copy per architecture directory: 54 architecture-copy pairs
before, 0 now.
- **Launch scalars instead of per-geometry / per-constant programs.**
The GEMM kernels take `M`, `m_tiles`, `k_iters`,
`first_chunk`, `ws_slab`, `ldc`, `k_slices`, `k_slice_iters`, `group_m`
and `group_n` as kernel arguments, so one program per
structural form serves every admissible geometry (`H` a multiple of the
`dX` / `dW` work item's 512 columns, `V` a multiple of
the logits work item's 256 columns) and every raster / K-slice setting:
18 constant-only clone groups
before, 0 now; the three per-geometry records collapse into one record
per architecture. The host computes the scalars per
chunk (`cake_backend.gemm_scalars`); the exporter refuses to export
unless that mirror agrees with the kernel source's own
launch contract on every form, and `validate_lm_head_inputs` rejects
geometries outside the admitted multiples up front.
- **One shared tvm-ffi launcher per distinct host contract**
(`csrc/cake_lm_head_loss/shim/`, the kernel symbol abstracted to
`CAKE_KERNEL_SYMBOL`) with a two-line launch stub per kernel instead of
a full binding translation unit per kernel; the
compiled host code is the same code that was delivered per kernel
before.
- **Compact registry.** `cake_jit.py` holds the argument plans, the
launch geometries and one row per stage as small tables and
expands them into the `MODULES` records at import (asserted by the test
suite).

| delivered form | seventh push | eighth push |
|---|---|---|
| kernel translation units (.cu) | 160 (80 per architecture) | 27
(shared) |
| host launcher units | 160 binding units | 20 shared launchers + 27
two-line stubs |
| generated source lines (csrc) | 153,144 | 20,580 |
| `cake_jit.py` lines | 6,105 | 476 |
| registry records | 6 (3 geometries x 2 architectures) | 2 (one per
architecture) |
| stage names per record | up to 42 | 23 |

Validation of the regenerated programs: the kernel source's own GPU
gates on both architectures (compute-sanitizer synccheck +
memcheck 0 errors on every GEMM form, the benchmark regression floor on
all 47 rows, same-GPU interleaved A/B against the
seventh-push kernels within the identical-code spread), the exporter's
per-shape receipts on both architectures with
byte-identical output between the two architecture runs, this test file
on the regenerated programs (176 passed / 1 skipped on B200,
176 passed / 1 skipped on GB300), and the backend's own wall-clock step
on the same GPU, seventh push vs eighth push (ratio eighth / seventh
of the CUDA-event step median, one fresh process per measurement, four
repetitions with alternating order, plus in-process ABBA
probes and a per-kernel CUPTI comparison with identical launch counts
and kernel sums within 0.4 %; GB300: fresh process per measurement
0.997–1.003, in-process 3 × 40 worst 1.038, in-process 2 × 20 worst
1.032; B200: fresh process per measurement 0.994–1.006, in-process 2 ×
20 worst 1.020).

### Evaluated, not shipped

- Straight-line `dW` epilogue drain: bitwise, -34 % instructions, slower
on SM103 beyond the paired spread.
- Wide TMEM load in the `dX` epilogue (`tcgen05.ld` x64 per 64-column
group): bitwise, drain time unchanged.
- `dlogits` generated inside the `dX` GEMM (exact `expf` on every landed
operand tile): +23 % (SM103) / +26 % (SM100) on the
  `dX` GEMM against a 0.37 ms row-gradient pass per 4096-row chunk.
- 2-D blocked raster for the `dW` GEMM at chunk rows 8192 (operand DRAM
re-reads): analysed, not shipped.
- Chunk-size auto-selection from the chunk x sequence-length table: `<=
0.5 %` for +1.2 GiB on SM100, negative on SM103.


#### Increment 9 — CUDA 13.0 on SM103, second ptxas instance (ninth
push)

Host only, no generated-unit change. The CUDA 13.0 SM103 CI job of the
eighth push failed:
`test_device_forward_backward_matches_reference[ce-4095]` raised
`cudaErrorIllegalInstruction` and the sticky context took the device
tests after it. Reproduced in a CUDA 13.0 container on SM103 with
`CUDA_LAUNCH_BLOCKING=1`: every call whose last chunk is partial (`T %
chunk_size != 0`: T = 1, 4095, 4097; T = 4096 passes) faults at the
launch of the last chunk's dW cast GEMM (`dz_c^T @ X_c`, the 2-CTA
structural form) built at ptxas -O1 — the eighth push's regenerated
program exposes a second instance of that toolchain's mis-scheduled
2-CTA TMA producer loop, this time at -O1 and in the tail chunk's short
K loop. Whole test file in that container: -O1 (eighth push) 20 failed /
154 passed / 3 skipped; `-Xptxas -O0` no device failure (2 failed / 172
passed / 3 skipped: the flag test that moves with this push and the
torch-tolerance row); the default level (no workaround) 3 failed / 171
passed / 3 skipped — the original -O3 instance (the dW accumulate GEMM's
short K loop, `test_device_dx_finalize_is_bitwise`) still fires.
`toolchain_workaround_flags` therefore returns `-Xptxas -O0` for SM103
on nvcc 13.0.x; CUDA 12.9, 13.3 and 13.4 keep the default level, the
host-count route of Increment 6 is unchanged, and the README toolchain
note and `test_toolchain_workaround_flags` follow. The performance
numbers of this description are nvcc 13.3 builds; a CUDA 13.0 SM103
build runs the -O0 code (correct, slower).

## Numerics and memory

Unchanged definition: BF16 GEMM outputs promoted to FP32 for the max /
log-sum-exp / loss arithmetic, BF16 `dlogits`, FP32 `dW`
accumulation in a fixed chunk order, one cast to the output dtypes, no
atomics, bitwise reproducible run to run.

- The fused cast applies the same `RN(g * (acc + tile))` rounding as the
previous accumulate-then-cast pass: `loss`, `logp`,
`dX`, `dW` are **bitwise identical** (`torch.equal`) to the previous
path on every tested shape (`T` 1 / 2048 / 4096 / 4097 /
16231 / 32463 at chunk 2048 / 4096, cross-entropy and policy, `g` 0.5 /
1 / 3, BF16 and FP32 `dW`, with and without ignored
rows) on both architectures. The preferred-cluster form, the 512-wide
tile and the raster rule are bitwise against their
  predecessors as well (same reduction order per output element).
- Accuracy gates against the token-chunked FP64 oracle of the same BF16
inputs (every metric within 1.05x the unchunked PyTorch
path on the same seeded inputs; loss relative error `max(1.05x, 4e-6)`;
ignored rows exact; three runs bitwise):
Worst errors vs the fp64 oracle over the acceptance rows on the final
tree (fresh-clone passes, two nodes per architecture) — B200: `dX`
rel-L2 ≤ 2.54e-03 (T2048_C4096_policy), `dW` rel-L2 ≤ 2.55e-03
(T2048_C4096_policy), `logp` max-abs ≤ 7.77e-03 (T16231_C4096_ce), loss
rel-err ≤ 1.88e-02 (T16231_C4096_policy; the policy objective's
clipped-ratio loss), `dX` vs the unchunked B0 ≤ 8.34e-04; 61 rows × 2
nodes, every gate PASS, 3× bitwise; GB300: `dX` rel-L2 ≤ 2.51e-03
(T16172_C4096_policy), `dW` rel-L2 ≤ 2.51e-03 (T16172_C4096_policy),
`logp` max-abs ≤ 7.79e-03 (T16231_C4096_policy_h8192v128256), loss
rel-err ≤ 2.04e-03 (T2048_C4096_policy; the policy objective's
clipped-ratio loss), `dX` vs the unchunked B0 ≤ 8.34e-04; 62 rows × 2
nodes, every gate PASS, 3× bitwise.
- **Memory.** The fused last-chunk `dW` cast (the default) trades the
finalize pass for `C * V * 2` bytes of saved
activation -- the deferred chunk's `dlogits`, BF16 `[C, V]`: at `T`
65031 / `C` 4096 on the default geometry the peak
backward memory is 8.66 GiB vs 7.47 GiB on the previous path (+1.19
GiB). Single-chunk calls (`T <= C`) drop the FP32 `dW`
accumulator entirely (peak backward 5.39 -> 2.42 GiB at `T` 2048), and
the vocab-sized intermediates still span at most `C`
tokens on every cell of the `C` 1024..8192 x `T` 2048..65031 sweep, both
architectures (120 / 120 cells within the step-plan
bound). `fuse_dw_cast=False` /
`FLASHINFER_CAKE_LM_HEAD_LOSS_FUSE_DW_CAST=0` restores the
accumulate-then-cast path, bitwise.

## Performance

Protocol: paired measurement on one GPU, ABAB-alternating independent
processes, 5 rounds x 20 timed steps after 3 warm-ups,
warm CUDA-event step medians (fwd / bwd in parentheses), loaded SM clock
and board power recorded per arm; two nodes per
architecture. Baselines: B0 = unchunked PyTorch trainer path and B1 =
chunked PyTorch reference at equal chunk (PyTorch
2.13.0a0+nv26.07, CUDA 13.3), L = Liger 0.8.4 fused linear cross-entropy
(BF16 `dW` default; its FP32-`dW` variant is the
equal-precision peer), C = Cut-Cross-Entropy 25.1.1 exact (`impl="cce",
filter_eps=None`). Ratio = best runnable baseline
step / this PR step (> 1 = this PR faster); `best` is Liger on the
cross-entropy rows at `T >= 16k`, B0 at `T = 4096`, B1 for
the policy and log-probability rows. The speedup tables below come from
the final-tree fresh-clone passes (two nodes per architecture;
previous-PR ratios from the round-start survey).

B200 (SM100), two nodes (node A / node B = two different B200 GPUs;
previous-PR ratios from the round-start survey on its own two
B200 nodes):

| row | node A: previous PR -> this PR (best / this PR) | node B | fwd /
bwd / step ms (this PR, node A) |
|---|---:|---:|---|
| t4096_c4096_ce | 1.47 -> 1.61 (torch_unchunked) | 1.39 -> 1.62
(torch_unchunked) | 11.46 / 4.88 / 16.34 |
| t16172_c4096_ce | 1.05 -> 1.10 (liger) | 1.00 -> 1.09 (liger) | 62.38
/ 4.35 / 66.68 |
| t16231_c2048_ce | 1.03 -> 1.05 (liger) | 1.00 -> 1.05 (liger) | 67.05
/ 2.56 / 69.56 |
| t16231_c4096_ce | 1.04 -> 1.09 (liger) | 1.01 -> 1.09 (liger) | 62.81
/ 4.41 / 67.33 |
| t16231_c8192_ce | 1.05 -> 1.10 (liger) | 0.98 -> 1.10 (liger) | 56.84
/ 9.97 / 66.89 |
| t32463_c4096_ce | 1.02 -> 1.05 (liger) | 0.97 -> 1.05 (liger) | 131.78
/ 3.32 / 135.04 |
| t65031_c4096_ce | 0.99 -> 1.04 (liger) | 0.94 -> 1.03 (liger) | 265.83
/ 2.45 / 268.28 |
| t16231_c4096_ce_h7168v129280 | 1.03 -> 1.08 (liger) | 0.99 -> 1.07
(liger) | 61.85 / 4.35 / 66.28 |
| t16231_c4096_ce_h8192v128256 | 1.04 -> 1.11 (liger) | 1.00 -> 1.10
(liger) | 68.96 / 5.12 / 74.08 |
| policy rows (11) / log-probability rows (9) | 1.58 (1.48-1.63) / 1.50
(1.47-1.59) | 1.60 (1.47-1.65) / 1.52 (1.49-1.59) | geomean (min-max) of
best / this PR |

GB300 (SM103), two nodes (node A / node B = two different GB300 GPUs;
previous-PR ratios from the round-start survey on its own two
GB300 nodes):

| row | node A: previous PR -> this PR (best / this PR) | node B | fwd /
bwd / step ms (this PR, node A) |
|---|---:|---:|---|
| t4096_c4096_ce | 1.53 -> 1.66 (torch_unchunked) | 1.52 -> 1.68
(torch_unchunked) | 9.42 / 3.92 / 13.34 |
| t16172_c4096_ce | 1.05 -> 1.10 (liger) | 1.05 -> 1.10 (liger) | 50.33
/ 3.52 / 53.95 |
| t16231_c2048_ce | 1.04 -> 1.07 (liger) | 1.04 -> 1.08 (liger) | 53.57
/ 2.15 / 55.68 |
| t16231_c4096_ce | 1.05 -> 1.11 (liger) | 1.06 -> 1.11 (liger) | 50.28
/ 3.61 / 53.86 |
| t16231_c8192_ce | 1.04 -> 1.12 (liger) | 1.04 -> 1.12 (liger) | 45.51
/ 8.05 / 53.69 |
| t32463_c4096_ce | 1.00 -> 1.06 (liger) | 0.99 -> 1.05 (liger) | 105.52
/ 2.68 / 108.20 |
| t65031_c4096_ce | 0.97 -> 1.03 (liger) | 0.97 -> 1.02 (liger) | 215.19
/ 2.14 / 217.35 |
| t16231_c4096_ce_h7168v129280 | 1.03 -> 1.08 (liger) | 1.04 -> 1.10
(liger) | 49.18 / 3.46 / 52.71 |
| t16231_c4096_ce_h8192v128256 | 1.00 -> 1.07 (liger) | 1.00 -> 1.08
(liger) | 56.03 / 4.07 / 60.10 |
| policy rows (11) / log-probability rows (9) | 1.63 (1.49-1.71) / 1.52
(1.48-1.64) | 1.64 (1.48-1.73) / 1.54 (1.50-1.65) | geomean (min-max) of
best / this PR |

`T = 65031`, chunk 4096, cross-entropy: measured per node, this PR's
step runs at 1.028 / 1.025x (GB300, two nodes) and 1.036 / 1.032x (B200,
two nodes) of
Liger's BF16-`dW` default, i.e. ahead on every measured node but inside
the run-to-run band. The low side of the spread is in the backward:
this path accumulates `dW` in FP32 across the 16 chunks (one rounded add
per element per chunk, fixed order, bitwise
reproducible) and casts once, while Liger's default accumulates into the
BF16 output; against Liger's FP32-`dW` variant, the
equal-precision peer, the row is 1.042-1.053x ahead (GB300 1.042 /
1.042, B200 1.053 / 1.045).

Memory (chunk 4096, `H = 6144, V = 154880`, BF16 `dW`): one-chunk step
`T = 4096` peak 3.63 -> 1.21 GiB on both architectures (the FP32 `[V,
H]`
accumulator is gone); multi-chunk rows unchanged peak, the deferred
chunk's rows counted in the saved-for-backward bucket.


Second push (shorter logits raster): the step tables above are the
fresh-clone passes of the previous head; this push changes the logits
GEMM only at chunks of 31+ row tiles at the default geometry (measured
per kernel above, bitwise identical outputs) and leaves every other
program byte-identical, so the rows it touches move by the per-kernel
deltas (SM100 up to about -0.9 % of the step at T 16231 / T 8117,
SM103 up to about -0.5 %; C 8192 rows about -0.6 %). The fresh-clone
step re-measurement of this head on two nodes per architecture is
scheduled with the next full acceptance pass and will replace the
tables.

Third push (fused dX finalize): the step tables still describe the
fresh-clone passes of the earlier head; this push replaces the
host-side dX finalize (slab adds, cast, zero fill, scatter) by the two
row kernels and leaves every GEMM program's device code
unchanged (regenerated by the current exporter; identity against the
previous packages: kernel sources differ in comments only, host
bindings in the shim text). Same-process paired steps (ABAB, 5 blocks,
CUPTI span, same GPU) of this change against the previous head:
SM103 -0.3..-0.7 % of the step (T 4096 / 16231 cross-entropy and policy,
chunk 2048 / 4096 / 8192, log-probability, no ignored rows),
SM100 -0.1..-0.9 %; bitwise identical `loss` / `logp` / `dX` / `dW` on
every row. The fresh-clone step re-measurement of this head on
two nodes per architecture is scheduled with the next full acceptance
pass and will replace the tables.

Fourth push (dW side stream): host-only, no generated program changes
(the `csrc/` packages are those of the third push, identical
bytes). Same-process paired steps (ABAB, 5 blocks, CUPTI span, same GPU,
two nodes per architecture) of the side stream against
the single-stream path on the same packages: SM103 −0.7..−0.9 % of the
step on four-chunk calls (T 16231, chunk 4096,
cross-entropy / policy / log-probability / no ignored rows: 0.9919 /
0.9928 / 0.9937 / 0.9944 on the second node, 0.9928 / 0.9950
/ 0.9963 / 0.9914 on the first), −0.5 % on eight-chunk calls (chunk
2048); SM100 −0.4..−0.7 % (0.9961 / 0.9959 / 0.9961 / 0.9933
second node, 0.9984 / 0.9945 / 0.9967 / 0.9931 first); two-chunk calls
0.997..1.003 (hence off at `auto`), one-chunk calls
untouched. Bitwise identical `loss` / `logp` / `dX` / `dW` on every row
and node. The fresh-clone step re-measurement of this head
on two nodes per architecture is scheduled with the next full acceptance
pass and will replace the tables.

Seventh push (hidden valid-row count for three or more chunks): host
only, no generated program changes. Same-GPU A/B of this head
against the sixth push's head (cake path of the pair harness, heads
interleaved per block, 3 blocks × 20 steps after 3 warm-ups,
warm CUDA-event step medians): SM103 T 2048 cross-entropy 7.726 → 6.709
ms (0.868), T 4096 cross-entropy 14.031 → 13.538 (0.965),
T 2048 log-probability 9.842 → 9.019 (0.916), T 8117 cross-entropy
27.406 → 26.822 (0.979), T 8117 log-probability 36.227 → 35.436
(0.978), and the four-chunk T 16231 cross-entropy row 53.855 → 54.379
(1.010, per-block ranges overlap: untouched path); SM100
8.583 → 8.283 (0.965), 16.614 → 16.330 (0.983), 11.334 → 10.900 (0.962),
33.260 → 33.166 (0.997), 43.803 → 43.102 (0.984), 65.726 →
65.306 (0.994). Across the heads on one SM100 GPU (same protocol): T
2048 cross-entropy 8.185 ms before the hidden count (third
push's head), 8.728 / 8.700 at the fifth / sixth push, 8.070 at this
head; T 2048 policy 7.985 / 8.688 / 8.626 / 8.092; T 4096
cross-entropy 16.481 / 16.770 / 16.843 / 16.578 — the short calls are
back at the pre-hidden-count step, and the forward's host time
returns from 1.88 to 0.79 ms per call (0.64 ms before the hidden count).
On this backend itself (one process per arm on one SM100 GPU, arms
interleaved over 2 blocks × 20 steps,
wall-clock step through the public entry points): T 2048 cross-entropy
8.40 / 8.54 ms with the sixth push's hidden count vs 8.25 / 7.77
at this head, T 4096 cross-entropy 16.76 / 16.93 vs 16.80 / 16.11, T
2048 log-probability 11.29 / 11.45 vs 11.17 / 11.24; the
two-chunk T 8117 rows are unchanged within noise (33.32 / 33.34 vs 33.26
/ 33.39; 43.95 / 44.23 vs 43.61 / 44.18). The fresh-clone
step re-measurement on two nodes per architecture has since run twice:
on the seventh push's kernel programs (124 / 124 row-nodes faster
than every runnable baseline, minimum ratio 1.018, accuracy gates 124 /
124; against the tabled pass 29 of 124 row-nodes moved by more
than 2 % in ratio, both directions, -3.9 to +5.8 %, within the
node-to-node scatter of the power-capped B200 nodes, no verdict changed)
and on this push's programs (B200 62 / 62 row-nodes faster than every
runnable baseline (minimum ratio 1.032), accuracy gates 62 / 62; GB300
62 / 62 row-nodes faster than every runnable baseline (minimum ratio
1.021), accuracy gates 62 / 62; against the previous pass of the same
kernel programs, 13 of 124 row-nodes moved by more than 2 % in ratio (at
most 4.3 %)). The tables above stand as the measured record of these
kernel programs, which this
push leaves byte-identical.

## Tests

`tests/experimental/test_cake_lm_head_loss.py`: 176 passed / 1 skipped
on B200 and 176 passed / 1 skipped on GB300 on the regenerated programs
of this push (head cf4715bfe9ca; the seventh push's head 1abf2aac83d ran
175 passed / 1 skipped on both -- this push adds
`test_gemm_scalars_mirror_the_kernel_contract`, the host check that the
launch scalars of each GEMM form follow the record geometry, the call
geometry and the rules' outputs; `test_all_ignored_rows[logprob-policy]`
is the skip: the log-probability entry has no objective). The fifth push
added the hidden-count tests (the switch inert on the reference backend
across objectives, ignored fractions and chunk counts;
`compaction_index` against `nonzero`; plan keys; the eligibility rule;
the stage grammar and rule closure; two device tests over the generated
program: the kernels against the torch gather and the host-bound GEMM,
and the switch bitwise on both entries with the count read only after
both launches are queued). CUDA 13.0 on SM103: under nvcc 13.0.x the
SM103 programs are built with `-Xptxas -O1`
(`cake_jit.toolchain_workaround_flags`) and take the host-count path
(`cake_jit.toolchain_runs_hidden_count`; the hidden valid-row count
stays on for every other architecture / toolchain pair). That
toolchain's ptxas mis-schedules the 2-CTA TMA producer loops of these
programs at -O2 / -O3 (an asynchronous `cudaErrorIllegalInstruction`
from the short-K `dW` accumulate GEMM, the `unit_test_gb300 [cu130]`
cell), and with the -O1 code the hidden count's launch schedule still
reaches the same fault in this test file while the host-count path
passes (two whole-file runs under nvcc 13.0 on GB300, cold and warm JIT
caches: 172 passed / 3 skipped -- the hidden-count device tests -- / 1
failed, the failure being the pre-existing host-tolerance row
`test_noncontiguous_x_strides[3-True]` on torch 2.9 nv25.09, unrelated
to this change; the same file with the hidden count on failed in every
run); CUDA 12.9, 13.3 and 13.4 build and run the same sources correctly
at the default optimization level with the hidden count on. Outputs are
bitwise the same on every path. These are mitigations of the observed
toolchain fault, not a root-cause fix. The fourth push added the
side-stream knob and rule, the key placement (joins / forks / sides over
the forward, recompute and cast key sequences), the
reference runner's indifference, and a device test over the generated
program: both entries bitwise across off / on / `auto` with
a spy on the stream contexts (two streams exactly when the side stream
is on), plus a three-chunk prepared runner across the
modes. New tests of the earlier pushes: the fused cast's host plan
(deferred chunk, one-chunk accumulator-free plan, memory
accounting), autograd bitwise vs `fuse_dw_cast=False`, the version
counter of the saved rows, the knob's environment default, the
preferred-cluster geometry checks of the binding step; the third push
added the fused dX finalize switch bitwise on the reference
backend (cross-entropy, policy, log-probability; ignored rows including
all of them), plan / launch keys, the scatter against the
torch form, a device test over the generated program, and the two row
kernels exercised by the device tests of both entries, with
and without ignored rows (the device binding-cache test reconstructs its
key with the resolved dX finalize form). The seventh push re-ran the
file on both architectures (175 passed / 1 skipped each, nvcc 13.3) and
under CUDA 13.0 on SM103 (172 passed / 3 skipped / 1 failed twice, cold
and warm; the failure is the torch-tolerance row above). The eighth push
re-ran the file on the
regenerated programs of both architectures (176 passed / 1 skipped on
B200, 176 passed / 1 skipped on GB300, nvcc 13.3) and added the tests of
the structural forms and launch scalars (`gemm_scalars` against the
kernel contract for every form, the stage grammar, the
reachable-form closure per architecture, the compact registry's
expansion). The ninth push (2b867fc9fe68, host only) re-ran the file on
SM103 at its head under nvcc 13.3 (176 passed / 1 skipped) and in a CUDA
13.0 container (1 failed / 173 passed / 3 skipped; the one failure there
is the torch-tolerance row above, as in the seventh push's CUDA 13.0
runs). The SM100 code path of this push is unchanged
(`toolchain_workaround_flags` returns `[]` for SM100 before any
toolchain check).

## Experimental track

- Owner: Cake team (NVIDIA). Tracking issue: #5680. JIT-only; not part
of automatic backend selection, autotuning or trace-apply.

## Checklist

- [x] Pre-commit (pinned hook versions) on every changed file; generated
sources are byte-exact exporter output, excluded from
      clang-format by the directory-scoped `.clang-format`.
- [x] Tests pass on B200 and GB300 on fresh clones with cold JIT caches
(counts above).
- [x] Tables filled from the paired measurements on both architectures;
the regenerated files of the two exporter runs are
      byte-identical (sha256 against `applied.json`).
- [x] The diff and the generated sources were scanned for non-public
references before each push: 0 hits.
- [x] Tracker bullets added (#4642, #4254); both CI trigger comments
posted once for the final push.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added optional fused weight-gradient casting for chunked
language-model-head loss and log-probability operations, combining
final-chunk accumulation and conversion in one step.
* Expanded support for registered model-head configurations across
additional tensor shapes and GPU architectures.
* Added per-GEMM tuning overrides for launch and tiling configurations.
  * Added configurable valid-row compaction and binding-cache settings.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [1728797](https://github.com/flashinfer-ai/flashinfer/commit/172879787a08d50691eec4e7c664e6c838f93098)

- **作者**: eigen
- **时间**: 2026-10-03T22:10:05Z
- **提交信息**: refactor(cake_grouped_mxfp8_quantize): use one dtype-templated kernel; cache target resolution (#5951)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

Closes #5819

## Summary

`mxfp8_grouped_quantize(backend="cake")` shipped the BF16 and FP16 input
paths as two independently hand-written
device files differing in 164 lines of load/widen assembly (the FP16
kernel still declared its input as
`__nv_bfloat16*`), checked availability on every call by reading the
device source off disk and searching for a
placeholder marker, queried the compute capability twice per call, and
copied the input and mask with
`.contiguous()` instead of rejecting non-dense views.

- One dtype-templated kernel schedule (BF16 widen-by-shift / FP16
`cvt.f32.f16`, selected by a trace-time constexpr)
delivered as two generated programs sharing one device-helper and one
host-launch-helper header, instead of two
  hand-maintained device files.
- No per-call disk read: availability is a cached table lookup keyed on
the resolved compile target; the compile
  target itself is resolved once per device index and cached.
- No `.contiguous()` copies: the public dispatch path requires a
contiguous input and mask and raises instead of
  silently copying a view.
- A static, checked-in binding translation unit per program instead of
an f-string rendered at JIT time.

Public names, JIT spec names
(`cake_grouped_mxfp8_quantize_<input>_<target>`) and import paths are
unchanged; no
registry or `__init__` file needed an edit. The kernel symbols are now
the generated program ids
(`kernel_cake_grouped_mxfp8_quantize_<program-hash>`) instead of the
hand-named `…_row2d_{bf16,f16}`.

Line count: +711 / −606 (net +105; `csrc/cake_grouped_mxfp8_quantize`
1,292 → 1,293 lines plus a 3-line `.clang-format` that exempts the
generated sources from the formatter hook, as the other generated Cake
directories do; the JIT loader 191 → 294 after the repository ruff
formatting and the restored launcher validation, AST-equivalent to the
generated text otherwise).
The two generated kernel files are 254 lines shorter than the two
hand-written ones, but each generated program
carries its own 180-line static launch binding (the two differ only in
the input dtype) and the loader now holds
the program/route table and the cached target resolution. The family is
too small for the removed duplication to
outweigh the per-program bindings; folding the two bindings into one
shared launch header is a generator-side
change that would apply to every generated family and is left as a
follow-up.

## Evidence

| check | sm_100a (B200) | sm_103a (B300) |
|---|---|---|
| SASS report base vs candidate, 2 kernel bodies (bfloat16, float16) | 2
vs 2 kernels, bodies regenerated (not byte-equivalent, as expected),
≥216 instruction lines each side | 2 vs 2 kernels, bodies regenerated,
≥216 instruction lines each side |
| `tests/utils/test_fp8_quantize.py -k cake` | 9 passed | 9 passed |
| paired CUPTI A/B (cold L2, 15 interleaved rounds, base = shipped
kernels), 14 rows (10 contract rows + 4 FlashInfer test rows): min row
ratio / geomean | 1.000 / 1.0000 | 1.000 / 1.0000 |
| outputs vs shipped kernels | all 14 rows: quantized tensor bitwise
equal; full-mask scale tensors bitwise equal | same |
| per-call host path | no disk read, one cached target resolution per
device, no `.contiguous()` copy (structural; the kernel-only A/B above
excludes host time) | same |

## Tests

`/bot run tests/utils/test_fp8_quantize.py`

## Not in this PR (follow-ups on the issue)

- All four proposed steps in the issue (merge the device files, remove
the placeholder mechanism and cache
availability, reject non-contiguous views instead of copying, check in a
static binding file) are delivered by
  this change.
- The scale divide (`absmax / 448`) in the promoted schedule
intentionally stays the same approximate-reciprocal
sequence the kernel already ships today, under the same default
fast-math build. A provably exact (IEEE
round-to-nearest) version of that divide was evaluated and measured at
~5-9% slower on the smallest shapes, so it
is not changed by default here; whether to pursue it is a maintainers'
decision pending on the issue, and it
  would land as a follow-up with its own measured cost if requested:

https://github.com/flashinfer-ai/flashinfer/issues/5819#issuecomment-5948058976

🤖 Generated with [Claude Code](https://claude.com/claude-code)

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added Cake grouped MXFP8 quantization for BF16 and FP16 inputs on
devices with compute capability 10.0 or 10.3.
* **Compatibility**
* Input and mask tensors must be contiguous; noncontiguous tensors are
rejected rather than copied automatically.
* Unsupported data types and devices are rejected with an error
identifying the supported compute capabilities.
* The K dimension must be divisible by 32. Batch size and row count must
not exceed 65,535.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: Yingyi Huang <yyihuang@nvidia.com>

### [77d4661](https://github.com/flashinfer-ai/flashinfer/commit/77d466141654c402f426f96551af8ad34b3e7e6f)

- **作者**: eigen
- **时间**: 2026-10-03T22:08:44Z
- **提交信息**: refactor(cake_bf16_bmm): share one source set across SM100/SM103; drop per-call device queries (#5937)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

Closes #5812

## Summary

`bmm_bf16(backend="cake")` shipped its 34 generated kernels twice
(`sm_100a/` and `sm_103a/`), byte-identical apart
from their content-derived names, with a binding and a declaration
header per architecture that differed only in those
names. The binding queried the compute capability twice and set the
dynamic shared-memory attribute on every call, and
a test asserted the dispatcher's internal route numbering.

- One copy of every kernel, one binding and one header at the family
root; the JIT loader compiles the same
translation units for each exact target with that target's nvcc flags
(separate cached libraries, unchanged JIT spec
  names and public loader entry point).
- No per-call device queries: the loader already selects the exact
target, so the compile-time target define and the
capability check are gone; every kernel is opted into its dynamic shared
memory once per device from a function-local
static initializer. Two never-called selection helpers and the
`route_of` export (used only by the replaced test)
  are removed.
- Numerical tests on random shapes (per supported K and output dtype:
random batch/M/N with partial tiles on both axes
and N below one tile width) and on the historical deployment and
tile-boundary shapes replace the route-id test;
  the rejection tests go through the public API only.

Kernel bodies, kernel symbols, binding ABI (`run`), public names and
import paths are unchanged.
74 files changed, +206 / -8,602 lines.

## Evidence

| check | sm_100a (B200) | sm_103a (B300) |
|---|---|---|
| SASS equivalence base vs candidate, 34 kernels (same kernel-body set,
nothing lost or added) | equivalent, 34/34, 0 missing / 0 introduced |
equivalent, 34/34, 0 missing / 0 introduced |
| `tests/gemm/test_bmm_bf16.py -k cake` | 129 passed | 129 passed |
| paired CUPTI A/B, 61 shapes (FlashInfer test rows, contract rows,
deployment and tile-boundary rows), 5 interleaved rounds: min ratio /
geomean | 0.982 / 1.0009, outputs bitwise equal | 1.000 / 1.0004,
outputs bitwise equal |
| per-call host time `run` before -> after (us) | 3.1 -> 3.1 | 3.3 ->
3.4 |

## Tests

`/bot run tests/gemm/test_bmm_bf16.py`

## Not in this PR (follow-ups on the issue)

- Removing the 31 fixed-shape kernel clones and taking K as a runtime
argument are regeneration steps: the lean
runtime-shape routes are measured against the exact-shape kernels on
both architectures first; a clone is dropped only
  where the generic route is within 2 %.
- Strided-input acceptance needs the shared
`flashinfer/gemm/gemm_base.py` requirement check to change together with
the
  binding; left to a dedicated change.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

- **New Features**
- CAKE BF16 batched matrix multiplication now supports both SM100a and
SM103a targets through a shared implementation.
- Kernel setup can accommodate devices with different shared-memory
limits.

- **Bug Fixes**
- Expanded numerical coverage across varied batch sizes, matrix shapes,
and output dtypes, including tile-boundary cases.

- **Changes**
- Removed route-ID reporting; operation tests now focus on numerical
results and output identity.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [d15f0ee](https://github.com/flashinfer-ai/flashinfer/commit/d15f0ee042bae52b313bca8ab8b9721a8a8b6264)

- **作者**: eigen
- **时间**: 2026-10-03T22:08:35Z
- **提交信息**: refactor(cake_grouped_fp8_gemm): regenerate grouped FP8 GEMM and fused SiLU-quant kernels for SM100/SM103 (#5993)

Closes #5817
Closes #5818

## Summary

Both Cake-generated grouped FP8 families — `cake_grouped_fp8_gemm`
(contiguous grouped FP8 GEMM, BF16 out) and
`cake_grouped_fp8_fused_silu_quant` (gate_up GEMM + SwiGLU +
per-token-group FP8 quantization) — are regenerated from their
producers with the current exporter. Public entry points, module names,
JIT spec names and import paths are unchanged
(`flashinfer/gemm/__init__.py`, `flashinfer/jit/gemm/__init__.py` and
`flashinfer/aot.py` are not touched); the benchmark
scripts run unmodified.

What changes in the delivered trees:

- **One device/binding pair per generated program, shared by SM100a and
SM103a.** The per-architecture
`csrc/<family>/sm_100a/` trees are removed; SM103a (B300) is served from
the same sources
  (`SUPPORTED_COMPUTE_CAPABILITIES = {(10, 0), (10, 3)}`).
- **Shared headers.** The PTX/helper preamble repeated in every kernel
TU (25 % of the GEMM family, 36 % of the fused family)
and the launcher-helper block repeated in every binding TU now live once
per family in
  `cake_<family>_{device,host}_common.cuh`.
- **Tensor maps by value.** Bindings take the TMA descriptors as kernel
parameters; the host keeps no descriptor storage,
no `cuMemcpyHtoD` workspace, no mutex/static cache or per-launch
device-attribute queries, and every launch — including the
  first — is CUDA-graph capturable (tested).
- **Small registry.** `MODULES` literals with a full positional argument
plan per module (999 / 489 lines) become an
interned `ARG_PLANS` / `PROGRAMS` / `MODULES` / `ROUTES` /
`ROUTE_GEOMETRY` table; `closure_sha256` is dropped.
- **Cached device facts.** SM count and architecture are queried once
per device (`functools.cache`); nothing on the
  prepare path calls `get_device_properties` per call.
- **Fused routing statistics without device work.**
`prepare_group_gemm_fp8_nt_groupwise_contiguous_silu_quant(...,
group_counts=...)` takes the caller's per-expert token counts and routes
in pure Python (no sync); the opt-in
`validate_indices=True` path does its min/max/sortedness/count checks on
the device with a single transfer (was three
  syncs plus `.unique().tolist()`).
- **Tests.** Route-name assertions are replaced by random token-count
tests (both families), MoE-shape tests, a
CUDA-graph capture of the *first* launch, and a
no-retained-device-memory re-preparation test. Fused tests compare
against
the FlashInfer three-kernel chain
(`group_gemm_fp8_nt_groupwise_contiguous` + `silu_and_mul` +
`per_token_group_quant_8bit`, bitwise scales) and a ulp-aware torch
reference.

Net: **59 files, +5,940 / −18,353 lines** (GEMM family 22 → 26 files,
20,918 → 14,010 lines; fused family 10 → 14 files,
11,810 → 7,459 lines) while adding SM103a. Exported kernels: 11 (GEMM) +
5 (fused) programs, one TU pair each.

## Evidence

| gate | SM100a (B200) | SM103a (B300) |
|---|---|---|
| Export protocol: source vs regenerated per row, cold-L2 CUPTI, 8
interleaved groups, correctness on every row | GEMM 29/29 rows pass
(correctness bitwise source == export). Fused 14/15 pass (0.996–1.000);
1 row (`[0,256,0,0,128,100]` tokens, 2H=256, K=1024) at 0.9386
attributed to the harness (see below), correct | GEMM 29/29 rows pass.
Fused 13/13 rows pass (correctness against the FlashInfer chain, scales
bitwise) |
| Family tests
(`tests/gemm/test_cake_group_gemm_fp8_nt_groupwise_contiguous*.py`) +
both benchmark scripts | **98 passed, 3 skipped** | **98 passed, 3
skipped** |
| SASS record (per-kernel inventory of the kernels at the base revision
vs the regenerated kernels) | 11 GEMM + 5 fused kernels at the base
revision vs 11 + 5 regenerated (0 missing); the two fused activation
kernels are bit-identical to the base | candidate-only record: 11 GEMM +
5 fused kernels (the base ships no SM103a kernels) |
| Paired CUPTI A/B, base checkout vs this branch, one GPU, interleaved
rounds, 61 rows (gate: every row ≥ 0.98, geomean ≥ 1.00 per family) |
**all four tables pass.** Base = this repository at the merge base, same
public API, same node, arm order rotated per round, cold L2, median GPU
time per `bench_gpu_time`. GEMM eager launch (37 rows, 3 instances × 10
rounds): geomean **1.0443**, worst row 0.9850. GEMM CUDA-graph replay
(37 rows, 8 instances × 10 rounds, arms alternating per instance):
geomean **1.0486**, worst row 0.9983 (`random_s13_m9000_n2048_k4096`).
SiLU-quant eager (24 rows, 3 × 10): geomean **1.0030**, worst 0.9872
(`random_s4_g16_b40_n2048_k4096`). SiLU-quant graph (24 rows, 8 × 10):
geomean **1.0080**, worst 0.9912 (`random_s2_g8_b16_n512_k1024`). Every
candidate output correct; the SiLU-quant scales are bitwise equal to the
three-kernel chain. The graph harness was accepted with an A/A control
(both arms = base tree) on the four most launch-sensitive rows:
0.9934–1.0090, geomean 1.0005 | no base family on SM103a (informational,
correctness-gated; all 61 rows correct): **GEMM vs eager CuTe-DSL** 37
rows, geomean 0.77 — tuned 128-aligned MoE/deployment shapes 1.03–1.15
(tp8 down 0.89), M ± 1 / random token counts 0.31–0.74 (generic route);
**fused vs the three-kernel chain** 24 rows, geomean **2.40** eager (min
1.64), 1.45 graph replay (min 1.20). The SM103a GEMM is explicit opt-in
only (`prepare_group_gemm_fp8_nt_groupwise_contiguous`; no automatic
selection, JIT-only until `aot.py` registers it) — decision pending:
[#5818 decision
item](https://github.com/flashinfer-ai/flashinfer/issues/5818#issuecomment-5963545058)
|
| CUDA-graph capture of the first launch, no retained device memory
across re-preparation | covered by the family tests | covered by the
family tests |

**The 0.9386 fused row.** Both arms launch the *same* grouped-GEMM
kernel through the same prepared launch and the same
activation kernel; per-kernel CUPTI medians are 6.85 µs (source) vs 7.42
µs (this branch) for that GEMM and 1.98 µs vs
1.98 µs for the activation kernel, while FlashInfer's existing
prepared-GEMM chain measures the same GEMM at 7.36 µs. The
difference is the launch's distance from the harness's zero-fill L2
flush (the slower-launching reference arm lets the dirty
L2 lines write back first); this branch's host launches ~6.5 µs sooner
end to end. Not a change in shipped code; see the
follow-up below.

`/bot run tests/gemm/test_cake_group_gemm_fp8_nt_groupwise_contiguous.py
tests/gemm/test_cake_group_gemm_fp8_nt_groupwise_contiguous_silu_quant.py`

## Not in this PR (follow-ups)

- **Decision pending (maintainers):** ship the SM103a grouped FP8 GEMM
as explicit opt-in with the measured ratios vs CuTe-DSL,
or hold it — options and per-row table in [#5818 decision
item](https://github.com/flashinfer-ai/flashinfer/issues/5818#issuecomment-5963545058).
- `flashinfer/aot.py`: register the SM103a records of both families (one
compute-capability filter line; maintainers).
- Exact-shape GEMM routes (the four `(M, N, K)` pairs): kept — on SM103a
the generic route at M ± 1 is 2.0–2.3× slower than the
exact routes, so they stay; tuning the generic (non-128-aligned) route
on both architectures is the follow-up.
- Fused family: merge the two activation kernels and the two fused
schedules into one; lift the `M <= 8192` kernel limit;
  stable generated file names (generator change).
- One helper header shared across the two families (today one per
family).
- Benchmark harness: a cold-L2 flush that leaves the cache clean
(read-sweep eviction or a write-back settle before the
timed bracket), so GPU-only timings do not depend on the launcher's host
latency.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Grouped FP8 GEMM and fused SiLU quantization now support SM103a GPUs
as well as SM100a.
* Fused SiLU quantization accepts optional group counts and a
caller-provided workspace.
* Prepared operations can be captured in a CUDA graph on the first
launch, without a warm-up call.

* **Improvements**
* Index validation combines checks into a single device-to-host
transfer.
* Improved validation for group counts, routing indices, and tensor
inputs.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [e51b068](https://github.com/flashinfer-ai/flashinfer/commit/e51b0681f6195847d2b11c6899c748ebc0c47e91)

- **作者**: eigen
- **时间**: 2026-10-03T22:08:25Z
- **提交信息**: refactor(cake_kda): drop import manifests and tools from the unbounded-softplus prefill kernels (#5917)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

Closes #5820

## Summary

The Cake unbounded-softplus prefill family
(`csrc/kda/cake_kda_affine_*`, `cake_kda_bf16_fused_m128*`) carried
three
import manifests and three `tools/import-cake-kda-*` scripts that only
work with producer-side export bundles. Two of
the manifests were read by nothing at runtime, in AOT or in tests. The
affine manifest was re-hashed on first use
(eight modules, about 1 MB of sources) and a `pending_generated_sources`
status silently disabled the affine route.

- Delete the three import manifests and the three import tools (nothing
in the tree reads them).
- `flashinfer/jit/cake_kda.py`: the eight affine target/role closures
are a plain module table; a missing source raises
instead of disabling the route. Hand-maintained hash pins are gone from
the JIT cache keys: freshness is owned by the
JIT dependency scan over the listed sources, and AOT artifacts are built
from the same tree.
- Drop the `FLASHINFER_CAKE_KDA_AFFINE_ARG_PLAN_SHA256` literal from the
four role bindings; it was consumed only by a
  `sizeof` static assertion.

Kernel bodies, kernel symbols, binding ABI, public names, JIT loader API
and import paths are unchanged.
13 files changed, +86 / -2,046 lines.

## Evidence

| check | sm_100a (B200) | sm_103a (B300) |
|---|---|---|
| SASS equivalence base vs candidate, 6 modules (2 fused variants + 4
affine roles) | equivalent: 18/18 kernels, 10 distinct bodies, 0 missing
/ 0 introduced | equivalent: 18/18 kernels, 10 distinct bodies, 0
missing / 0 introduced |
| `tests/kda/test_recurrent_kda_prefill.py` +
`tests/kda/test_kda_prefill_plan_cache.py` | 344 passed, 1 skipped | 345
passed |
| loader sweep (all 6 family modules build and load from the plain
module table) | 6/6 | 6/6 |

## Tests

`/bot run tests/kda/test_recurrent_kda_prefill.py
tests/kda/test_kda_prefill_plan_cache.py`

Not shipped here (follow-ups on the issue): one role-parameterized
affine body and a single affine implementation
shared with the generated and prepared routes; both are regeneration
steps.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Avery Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [0aaa01c](https://github.com/flashinfer-ai/flashinfer/commit/0aaa01ceccd1a3418e5a791222d6022a3481355e)

- **作者**: eigen
- **时间**: 2026-10-03T22:08:15Z
- **提交信息**: refactor(cake_kda): regenerate fused KDA decode kernels as generic stride-taking programs (#6026)

Closes #5814

Regenerates the Cake backend of `fused_kda_decode`
(`csrc/kda/cake_fused_kda_decode_*`) with the current Cake
generator: 17 generic, stride-taking schedules, each as a 64-bit /
32-bit slot-offset pair (34 programs), one
device/binding source pair per program shared by B200 (sm_100a) and B300
(sm_103a), a registry module that builds
each program through the standard JIT path, and a host that binds the
caller's strided tensors by the program's
argument plan. The 16 head-count / evaluation-layout clones of the
generic kernels and the permanently unreachable
`direct_positive_f32` pair are removed rather than edited (52 -> 34
kernel bodies); the 396-line hand-written
binding header template and the 4,180-line literal variant table in the
loader go with them.

What changes
- `csrc/kda/cake_fused_kda_decode_*`: 52 kernel bodies (59,224 lines)
plus the `cake_fused_kda_decode_binding.cuh`
template (396 lines) are replaced by 34 generated kernel bodies (24,343
lines) and 34 generated tvm-ffi bindings
(7,088 lines). Every body takes `H` and the five row/slot strides
(`x_row_stride`, `conv_slot_stride`,
`beta_row_stride`, `state_slot_stride`, `output_gate_row_stride`) at
runtime; the eight clone schedules that had
the head count and one evaluation layout's padded strides hard-coded in
(for example `high_work_positive_pr_eval_h12_f32`
with `4625` / `407040` in place of `x_row_stride` / `conv_slot_stride`,
selected only when every runtime stride matched)
and their eight `*_wide_slot_offsets` twins are gone:
`compact_async_pr_eval_h96_f32`, `high_work_positive_h96_f32`,
`high_work_positive_h96_pr_strides_f32`,
`high_work_positive_pr_eval_h{12,24,32,48}_f32`, `pr_eval_h32_f32`. The
generic program of the same schedule now serves those layouts, measured
against the shipped clone at exactly those
layouts (Evidence). `direct_positive_f32` and its twin are removed
because the positive-unique FP32 selector's wave
arithmetic never produced that name for any head count or row count (the
shipped GPU test could only reach it through
a direct factory call). `wide512_regcap128_positive_f32` stays: it is
the H=8 rows 10..18 instantiation of the wide512
positive-FP32 schedule with `LAUNCH_MIN_BLOCKS=1` as a named schedule
constant (one template, two instantiations),
  not a hand-maintained duplicate.
- Each generated binding checks rank, dimensions (in `H`, the row count
or `grid_y`) and every stride of `x`,
`conv_state`, `state` and `output_gate` against the scalars the host
passes, so the padded tensors travel as the
caller's strided tensors (no flat views, no staging, no allocation).
Repeated-slot programs (`repeated_safe_*`) take the
whole row set in one call; their `_rows_binding.cu` walks the rows with
one same-stream launch each so a slot shared by
several rows observes every earlier update. The launch grid is an
explicit argument the binding validates.
- `flashinfer/jit/cake_fused_kda_decode.py` (4,827 -> 2,276 lines): a
`MODULES` registry (per program: sources, kernel
symbol, argument plan, compile flags, launch block / dynamic shared
memory / cluster, per-architecture closure digest)
and a `ROUTES` map from the 34 logical variant names to programs,
written by the generator; the 4,180-line literal
eligibility table becomes ~50 lines of `_VARIANT_SPECS` built from
per-head row bands (`_WIDE512_BANDS`,
`_COMPACT_BANDS`, `_HIGH_WORK_BANDS`, `_DIRECT_NULLABLE_BANDS`) with
`_twins()` deriving each 64-bit / 32-bit pair
from one launch contract. Every eligibility rule leaves all strides open
(a test asserts no variant pins a layout or a
runtime configuration). `gen_cake_fused_kda_decode_module` builds the
program's two translation units with the standard
`sm100a` / `sm103a` flags; the string-rendered binding
(`_render_binding` / `_kernel_declaration`) is gone. Two
per-program flag overrides carry measured reasons in the source:
`-Xptxas=--minnctapersm=3` keeps three resident CTAs
for `compact_async_f32_wide_slot_offsets`, and the two
`cluster2_wide_positive_f32` programs build without fast math
(NVCC allocates 62 instead of 64 registers under fast math there, about
2 % slower; outputs are bitwise identical).
Route selection is unchanged: the positive-unique FP32 wave arithmetic
keeps its fixed, measured 148-SM constant on
every device, exactly as the shipped selector did. New helpers
`cake_fused_kda_decode_grid` and
`cake_fused_kda_decode_lower_bound_log2`; the previously exported names
(`get_cake_fused_kda_decode_variants`,
`select_cake_fused_kda_decode_variant`,
`gen_/load_cake_fused_kda_decode_module`, `CAKE_FUSED_KDA_DECODE_ABIS`,
...)
  and the JIT URI scheme are unchanged.
- `flashinfer/kda_kernels/fused_kda_decode.py` (+69 / -16):
`_run_cake_variant` computes the grid on the host
(`cake_fused_kda_decode_grid`, persistent programs sized from the
device's resident-CTA capacity), orders the arguments
with one comprehension over the program's argument plan, passes the
tensors as they are with their explicit strides,
and resolves the device index from `x.device`. The multiprocessor count
is queried once per device
(`_device_sm_count`, `functools.cache`);
`fused_kda_decode_multitoken.py` (+2 / -1) reuses the cached helper
instead of
a per-call `get_device_properties` query. Public API, signatures and
callers are untouched.
- `tests/kda/test_cake_fused_kda_decode_dispatch.py` (+284 / -181, 22 ->
26 tests): registry tests follow the
`MODULES` / `ROUTES` form (every variant routes to exactly one generated
program; no variant pins a layout or a runtime
configuration; `wide512_regcap128_positive_f32` is the one-wave
instantiation of wide512; cluster variants launch two
CTAs per work item; persistent programs size the grid by resident CTAs;
repeated-slot programs take a single-head grid;
the lower bound travels in log2 units) and the submit tests bind strided
caller tensors through the argument plan,
pass every repeated-slot row in one call and size the persistent grid.
The removed clones' route expectations now name
  the generic programs.
- `tests/kda/test_cake_fused_kda_decode_gpu.py` (+13 / -60): the
per-variant table runs every case through the public
dispatcher (`factory_only=False` everywhere): the former clone rows
(H=96 rows 4 / 13 on page and padded layouts,
H=12 rows 99, H=24 rows 50, H=32 rows 32, H=48 rows 25) now expect the
generic programs, the H=8 rows 16
`wide512_regcap128_positive_f32` case is added, and the two factory-only
cases (`direct_positive_f32`, `pr_eval_h32_f32`)
  are dropped with their kernels. Tolerances unchanged.

Line count: 92 files, +10,119 / -40,749 against the shipped tree (net
-30,630); `csrc/kda/cake_fused_kda_decode_*`
53 files / 59,620 lines -> 68 files / 31,431 lines; loader 4,827 ->
2,276 lines. `benchmarks/bench_cake_fused_kda_decode.py`
is unchanged.

Evidence
| Check | B200 (sm_100a) | B300 (sm_103a) |
|---|---|---|
| `tests/kda/test_cake_fused_kda_decode_dispatch.py` +
`tests/kda/test_cake_fused_kda_decode_gpu.py` | 406 passed; public
`run_fused_kda_decode(backend="cake")` smoke OK | 406 passed |
| Per-kernel SASS report, shipped vs regenerated (regenerated bodies;
identity not expected) | 34 paired kernels, 13 identical bodies, mean
abs. instruction delta 1.65, 7 register-count increases, no local memory
introduced | 34 paired kernels, 8 identical bodies, mean abs.
instruction delta 2.82 |
| Control paired CUPTI A/B, shipped vs shipped (measurement floor) |
135/135 rows, geomean 0.99997, worst 0.9961 | 135/135 rows, geomean
1.0004, worst 0.9941 |
| Paired CUPTI A/B, shipped vs regenerated (geomean / worst row), every
row >= 0.98 | PASS: 135/135 rows, geomean 1.0030, worst 0.9851
(`cov_h12_rows99_bf16_null`), every row bitwise identical to the shipped
kernels | PASS: 135/135 rows, geomean 1.0060, worst 0.9868, every row
bitwise identical to the shipped kernels |
| Export run, production kernels vs regenerated programs (135 rows;
correctness and bitwise parity on every row) | 115 passed, 20 rows in
the run's noise classes (directional disagreement, `stream_bf16`
compiler-path band) | 122 passed, 13 rows in the noise classes;
source/export geomean 1.0747, min 0.9708 |

Validation protocol: the paired CUPTI A/B runs the shipped kernels and
the regenerated programs in one process pair on
the same GPU (one FlashInfer package per interpreter), interleaved
rounds through a barrier, `bench_gpu_time` (CUPTI
activity tracing with L2 flush) per row, candidate outputs compared
bitwise with the shipped kernels' outputs and
against the torch reference. The 135 rows cover every shape the family's
benchmarks and tests use plus the evaluation
layouts the removed clones were specialised for. Acceptance per
architecture: every row >= 0.98 and geomean >= 1.00; the
control arm (shipped vs shipped) bounds the measurement noise. The
export run's own source-vs-export gate compares an
in-process NVRTC build with the nvcc JIT build and is reported for
completeness; acceptance is the paired A/B.

Follow-ups, not in this PR
- The 64-bit / 32-bit slot-offset twins stay separate programs (17
pairs) because they differ in the C integer type of
the cache-offset arithmetic, not in a literal the generator can
template; a typed axis in the generator would halve the
  generated sources.
- Ahead-of-time registration of the programs (`flashinfer/aot.py`) so
wheels ship them prebuilt.

Test paths for CI: `tests/kda/test_cake_fused_kda_decode_dispatch.py
tests/kda/test_cake_fused_kda_decode_gpu.py`

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Expanded fused KDA decode support across additional configurations,
including varied head sizes, row counts, and tensor layouts.
* Added row-by-row execution for decode variants that update shared
state.
* Added validation for input tensors and launch settings, with clearer
errors for invalid inputs.
* **Bug Fixes**
  * Improved handling of inactive state slots and large state offsets.
* Added architecture-specific handling for CUDA shared-memory
operations.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [ce007d3](https://github.com/flashinfer-ai/flashinfer/commit/ce007d39486a9bef8d4a7a7122178dd8fe20eee3)

- **作者**: eigen
- **时间**: 2026-10-03T22:08:04Z
- **提交信息**: refactor(cake_bf16_fp4_gemm): regenerate SM100/SM103 BF16 x FP4 GEMM kernels from one generator (#5990)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.


Closes #5811

Regenerates `csrc/blackwell_bf16_fp4/` with the current Cake generator:
one architecture-neutral source per distinct
kernel for B200 (sm_100a) and B300 (sm_103a), a registry module that
builds each program through the standard JIT
path, and a host that plans a launch once and binds the generated
argument plan by name. The two 95,027-line
per-architecture bundles, the hand-written 711-line binding and its
166-line kernel table are removed rather than
edited.

What changes
- `csrc/blackwell_bf16_fp4/`: one source pair per program (80 programs:
14 generic kernels x alpha x PDL x grid
mode, plus the three bucket-selected seed kernels the shipped binding
used -- the M16/K1024 kernel in its four
alpha/PDL variants and the exact `(17, 3072, 3072)` / `(768, 2112,
2048)` tiled kernels for alpha+PDL -- kept
because the generic kernels measured 0.49-0.84x on those shapes; they
read the lane index from `%laneid` as the
shipped kernels did, which keeps their instruction streams equal to the
shipped kernels -- deriving it from the
thread index folded differently and cost 4 % on B300 for the M16 kernel)
replaces 4 files / 190,931 lines. Tiled rows
with `M <= 16, K != 1024, K >= 128, K % 64 == 0` now run the generic M16
kernel (the previous binding sent them
to the M32 kernel; M16 measured 7-13 % faster on the M=1/7/13 contract
rows). The SM103 bundle differed from the SM100 bundle in 4 lines
(a `TARGET_SM` define no kernel reads and a manifest string). TMA
descriptors travel by value (`__grid_constant__`),
so the descriptor arena, its device allocations and the synchronous
host-to-device copies are gone.
- `flashinfer/jit/blackwell_bf16_fp4.py`: `MODULES` / `ROUTES` records,
`gen_jit_spec` per (program, architecture)
with the standard `sm100a` / `sm103a` nvcc flags; JIT names carry the
architecture. The `nvcc -cubin` shell-out,
  the string-patched binding and `cpp.load_inline` are removed.
- `flashinfer/gemm/gemm_bf16_fp4_blackwell.py`:
`_prepare_blackwell_bf16_fp4` / `_compute_blackwell_bf16_fp4` keep
their signatures (callers in `gemm_bf16_fp4.py` untouched). Route
selection in Python with the same tiled /
native / M-band / flat-grid rules as the binding, explicit `has_alpha`
instead of a pointer comparison, SM count and
architecture cached once, split-K partials from the torch allocator
instead of a never-freed `cuMemAlloc` cache,
per-launch work limited to shape checks and one launch per stage. Graph
capture works for unseen inputs.
- `tests/gemm/test_blackwell_bf16_fp4.py`: the 9 original cases plus
tiled K=16 / K=32 / K=80 rows, M>=33 tiled and
native rows, the two previously exact-shape rows `(768, 2112, 2048)` and
`(1, 4096, 4096)`, large-M flat-grid rows,
a many-distinct-activations test (4,200 inputs) and a CUDA-graph
capture/replay test. Tolerances unchanged
  (atol = rtol = 1e-2).
- `csrc/blackwell_bf16_fp4/.clang-format` (DisableFormat) keeps the
generated sources byte-faithful without
  changing the pre-commit configuration.
- Host allocations are by design: the output tensor when the caller
passes `out=None` (as before), one
split-K partial buffer per (device, stream, M, N) from the torch caching
allocator (allocated on the first
call for that key, bounded to 16 entries, replacing a driver allocation
that was never freed; a first call
inside CUDA Graph capture draws the buffer from the graph's pool and
does not cache it), and one cached
  unit-alpha tensor per device. Steady-state calls allocate nothing.

Line count: 168 files, +110,758 / -191,168 against the shipped tree (net
-80,410); 80 generated device/binding pairs, 163 generated files.

Evidence
| Check | B200 (sm_100a) | B300 (sm_103a) |
|---|---|---|
| Export run: production kernels vs regenerated, 27 contract rows + 9
test rows + coverage rows for every program, bitwise parity, min ratio
0.97, no allocations on submit | 98/98 shapes pass, source/export
1.000-1.003 | 98/98 shapes pass, source/export 1.000-1.003 |
| Shipped delivery vs regenerated, same rows, paired CUPTI timing | seed
rows: M16 pdl0 1.000 (`fi_tiled_m16_bf16` 1.006), M16 pdl1 1.033, exact
m17 1.052, exact m768 1.025 | seed rows: M16 pdl0 1.000, M16 pdl1
1.017-1.018, exact m17 0.997, exact m768 1.011 |
| `tests/gemm/test_blackwell_bf16_fp4.py` (25 tests) | 25 passed | 25
passed |
| Paired CUPTI A/B shipped vs regenerated, 28 production rows + 2
forced-generic rows, 10 interleaved rounds (geomean / worst row) | PASS:
geomean 1.076, worst 1.000 (`large_m_flat_native_k256`), every row >=
0.98, bitwise | PASS: geomean 1.075, worst 0.992
(`fi_native_m1_ragged_n_k16`), every row >= 0.98, bitwise |
| Host time per call, shipped vs regenerated (2,000 asynchronous calls)
| 11.7 us vs 39.6 us | 11.1 us vs 42.5 us |
| Per-kernel SASS report (regenerated bodies, by-value descriptors;
identity not expected) | 80/80 cells matched; seed M16 866/866 instr,
m17 1488/1489 | 80/80 cells matched; seed M16 866/866 instr, m17
1488/1488 |
| Build of all 80 programs for both architectures | 80/80 (SASS gate,
nvcc sm_100a) | 80/80 (SASS gate, nvcc sm_103a) |

Open for maintainers
- Exact-shape kernels: the `(768, 2112, 2048)` group-M128 kernel and the
`(1, 4096, 4096)` split-K pair are still
routed exactly as before; the paired A/B measured the generic kernels at
0.38-0.39x and 0.64x on those shapes,
so both routes stay. The three tiled seed kernels (M16/K1024, exact m17,
exact m768) likewise stay as
  bucket-selected programs (generic 0.49-0.84x there).
- Host time per call is higher than the shipped binding (11-12 us ->
40-42 us on the split-K row, 2,000
asynchronous calls): route selection moved to Python and every call
encodes its 3-5 tensor maps with
`cuTensorMapEncodeTiled`, where the shipped binding reused cached
device-side descriptor slots. Kernel time is
unchanged; graph-captured serving does not pay it. Options are in the
maintainer note on the issue.
- Follow-up, not in this PR: alpha and flat-grid are compile-time
variants today (80 programs); making them runtime
arguments in the generator would roughly halve the generated sources.
The PDL on/off pairs likewise stay separate
until the generator can pass the launch attribute at runtime instead of
baking it into the launcher.
- Follow-up, not in this PR: ahead-of-time registration of the programs
(`flashinfer/aot.py`) so wheels ship them
  prebuilt.

Test paths for CI: `tests/gemm/test_blackwell_bf16_fp4.py`

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added Blackwell GPU support for BF16 matrix multiplication with FP4
weights, including multiple kernel paths for different shapes and output
formats.
* Added launch planning for grouped and split-K workloads, plus handling
for large matrices that exceed standard grid limits.
* **Tests**
* Expanded coverage for varied shapes, alpha scaling, repeated runs with
different inputs, and CUDA Graph capture and replay. Tests check
numerical accuracy and output stability.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [2f9b429](https://github.com/flashinfer-ai/flashinfer/commit/2f9b429933f63e33e08c354958fd41c603948a6c)

- **作者**: eigen
- **时间**: 2026-10-03T22:01:54Z
- **提交信息**: refactor(cake_gdn): regenerate SM100/SM103 context-parallel prefill kernels as architecture-neutral programs (#6025)

Closes #5815

Regenerates `csrc/gdn/gdn_cp/` with the current Cake generator: one
architecture-neutral source per distinct
program for B200 (sm_100a) and B300 (sm_103a), each with a thin TVM-FFI
launcher, and a registry module rendered
from the generator's module records. The frozen `cuda/` + `host/` +
`sm_103a/` + `manifest.json` set (103 files,
including the eleven prepared-sequence bindings nothing loads and the
five manifest kernels the host never
selects) is removed rather than edited. The host dispatcher
(`flashinfer/gdn_kernels/blackwell/cake_gdn_cp_backend.py`) is
unchanged: it runs on the regenerated programs
through the loader's existing `load_gdn_cp_kernel` /
`prepare_gdn_cp_kernel` surface.

What changes
- `csrc/gdn/gdn_cp/`: 29 programs (one `*_kernel.cu` + one
`*_binding.cu` each; 28 compile for both
architectures, the equal-head H32 pipeline-depth variant is B300-only)
replace 103 files / 68,212 lines. The
per-architecture copies are gone: the three `*_checkpoint.sm_100a.cu`
kernels (byte-identical to the
`sm_103a` generation) and the B200 FP16 pipeline now come from the same
generated source as B300, so the
`*_checkpoint` logical names and `t_precompute_gb300_hv48_min6` (a
`__launch_bounds__(128, 6)` copy of
`t_precompute`) map onto the canonical programs in the registry instead
of carrying their own kernel text.
The twelve gather/scatter programs (state dtype x index dtype) are kept
as separate programs.
- `csrc/gdn/gdn_cp/*_binding.cu`: each launcher validates its arguments,
encodes its tensor maps by value and
derives the CP-prefill fast-division constants from the plain divisor
arguments, so no Python work sits
  between the host and the launch.
- `flashinfer/jit/cake_gdn_cp_backend.py`: `MODULES` (sources, kernel
symbol, argument plan, architectures) and
`KERNELS` (logical kernel -> program, per architecture) records rendered
by the generator; `gen_jit_spec` per
(program, architecture) with the standard `sm100a` / `sm103a` nvcc flags
and the architecture in the JIT
library name; no manifest and no digest check at import. `GDNCPArch`,
`load_gdn_cp_kernel`,
`prepare_gdn_cp_kernel` keep their names and signatures;
`flashinfer/jit/cake_gdn_cp_generated.py` (the
single-line program registry) is removed. `flashinfer/__init__.py` and
`flashinfer/jit/__init__.py` are
  untouched.
- `tests/gdn/test_cake_gdn_cp_backend.py`: the file-inventory /
header-digest / manifest tests are replaced by
registry checks (every logical kernel the host dispatches on maps to a
program that lists the architecture
and whose sources exist; no manifest is shipped; every delivered source
is referenced by the registry). GPU
  rows unchanged.
- `csrc/gdn/gdn_cp/.clang-format` (DisableFormat) keeps the generated
sources byte-faithful; `README.md`
  describes the new layout.

Line count: 144 files, +11,213 / -68,742 against the shipped tree (net
-57,529).

Evidence
| Check | B200 (sm_100a) | B300 (sm_103a) |
|---|---|---|
| Export run: production kernels vs regenerated, 150 contract rows + 9
test rows, source/regenerated min ratio 0.97; covering and test rows
additionally bitwise-identical between the production kernels and the
regenerated programs | 159/159 pass, 0 rows with a bitwise mismatch |
159/159 pass, 0 rows with a bitwise mismatch |
| `tests/gdn/test_cake_gdn_cp_backend.py` | 362 passed, 4 skipped | 362
passed, 4 skipped |
| Public `chunk_gated_delta_rule(..., use_cp=True, backend="cake_gdn")`
smoke | OK | OK |
| Paired CUPTI A/B shipped vs regenerated, 159 rows, 5 interleaved
rounds per row, ABBA order, both arms sampled at full SM clock (geomean
/ worst row) | PASS: geomean 1.0016, worst 0.9835 (`focus_axis_02`),
every row >= 0.98 | PASS: geomean 1.0472, worst 0.9842
(`perf_hq16_hv48_1x65536`), every row >= 0.98 |
| Per-kernel SASS report (regenerated bodies; identity not expected) |
31 shipped kernel bodies -> 28 regenerated | 40 shipped kernel bodies ->
29 regenerated |
| Build of all programs for the architecture | 28/28 | 29/29 |

Validation protocol: the shipped delivery and the regenerated delivery
run in one process pair on the same GPU
with interleaved rounds, timed with CUPTI activity tracing and a cold L2
before every launch; one row per
architecture (`focus_axis_07` on B200, `focus_axis_03` on B300) was
re-measured alone over 10 rounds after a
4-rows-per-node run put it below 0.98 under host contention (0.9973 and
1.007 alone). Six covering rows
(`focus_axis_10/11`, `focus_state_00/04/10/11`: BF16, Hv = 2, sequences
shorter than 128 tokens) differ from the
independent FP32 recurrence beyond atol = rtol = 1e-2 with both the
shipped and the regenerated kernels; they
are listed on the issue as a pre-existing finding, not changed by this
PR.

Open for maintainers
- FP16 on B200: SM100 FP16 rows ran the frozen
`cuda/*_checkpoint.sm_100a.cu` generation while SM103 ran the
current one; this PR ships the current generation for both. The B200 A/B
table above (every row >= 0.98,
geomean 1.0016) is the evidence; the frozen kernels are not kept
alongside.
- Exact-shape specialisations: the `min_blocks = 6` Stage-1 clone
selected for exactly (65536 tokens, 16 K heads,
48 SAB heads) on B300 is removed (`perf_hq16_hv48_1x65536` measures
0.9842 on B300 against the shipped clone).
The host's `cp_chunk_len = 4096` route for (65536, (16, 16, 64)) on B300
is unchanged because the host is not
  touched here.
- Not in this PR (listed on the issue with reasons): the host-side
cleanups (bounded multi-entry plan cache,
fewer `record_stream` calls, no per-launch `cu_seqlens` copy, strided
q/k/v acceptance), a runtime-indexed
gather/scatter program replacing the twelve typed ones, and runtime
SM-count planning for other SKUs.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added architecture-specific just-in-time loading for GDN
context-parallel kernels on SM100 and SM103.
* Added generated CUDA launchers and kernels for GDN operations,
including state gathering, scattering, normalization, and
context-parallel processing.
* Added input checks for tensor types, devices, dimensions, and launch
parameters.
* **Documentation**
* Updated the GDN kernel documentation to describe generated sources and
their supported architectures.
* **Refactor**
* Replaced manifest-based kernel loading with a registered JIT-based
approach.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [fb0060d](https://github.com/flashinfer-ai/flashinfer/commit/fb0060ddb29c84ec938e2c6df60a5161e7182a5b)

- **作者**: eigen
- **时间**: 2026-10-03T21:59:51Z
- **提交信息**: refactor(cake_deepgemm): share one catalog loader; add random-input reference checks (#5928)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

Closes #5813

Package-level pass over the eleven Cake-generated DeepGEMM-family
backends under `csrc/experimental/` and
`flashinfer/experimental/`. This PR adds only shared files plus one
package-level consolidation; it edits no
family's generated sources, Python module or test, so the per-family
regenerations (#5828–#5836, #5842, #5843)
rebase on it without conflicts and adopt the shared loader as a one-line
change.

What is shared
- `flashinfer/experimental/deepgemm_common/` (`cake_catalog.py`,
re-exported from `__init__.py`): one catalog
reader (per-architecture and architecture-merged layouts), one
compute-capability / SM-count lookup whose
`UnsupportedDevice` error names the device and the catalogued SM counts,
one JIT loader with unchanged spec
names. Nothing is hashed or re-verified at import. Family adoption
imports from the package
(`from flashinfer.experimental.deepgemm_common import Catalog,
load_catalog, ...`), so the `cake_` filename is
an internal detail and does not change the one-line adoption per family.
- `tests/experimental/deepgemm_common/`: seeded random operands in the
families' storage conventions (E2M1
pairs, UE8M0 scale words, FP8 with float32 per-row, 128x128 tile or
UE8M0 block scales) with their dequantized
views, a float64 reference GEMM and per-output-dtype tolerances. The
family tests currently use constant-filled
inputs whose analytic result is `K * alpha`;
`tests/experimental/test_deepgemm_common.py` runs random operands
through `prepare_fp4_gemm` and `prepare_fp8_batched_gemm` against the
reference.
- One `.clang-format` (DisableFormat) at `csrc/experimental/` covers ten
of the eleven family directories.
`deepgemm_kgroup_gemm`'s own copy is left untouched here; its own
in-flight regeneration PR removes it as
part of rebuilding that family's generated tree, and deleting it on both
branches would collide.

Not in this PR: a shared binding helper header. The regenerated family
bindings use the checks in
`csrc/tvm_ffi_utils.h` and carry no inlined helper block, so a package
header would be dead code once the
families land.

Line count: +899 / −18. The net is positive on purpose: this PR may not
touch any family file (the family PRs
are in flight), so the deletions it enables — the loader copies, the
inlined helper blocks and the NOTICE
copies — happen in the per-family PRs that adopt the loader and
regenerate.

Evidence
| Check | Result |
|---|---|
| Shared loader vs the eleven catalogs | SM sets and JIT spec names
identical to the family functions |
| Shared loader builds the identical JIT spec (one batched_gemm + one
mixed_gemm program, B200 and B300) | SASS equal on sm_103a; sm_100a
flagged NONDETERMINISTIC_TOOLCHAIN by the base-vs-base control
(build.ninja identical, candidate vs base-repeat 0 diff lines on the
batched kernel) — not a loader difference |
| `tests/experimental/test_deepgemm_common.py` (CPU unit tests + GPU
reference checks) | 29 passed on both B200 (sm_100a) and GB300 (sm_103a)
|

Open for maintainers: exact-SM-count routes keep raising
`NotImplementedError` on other SKUs (now naming the
device); runtime SM count is part of the per-family regenerations.

Test paths for CI: `tests/experimental/test_deepgemm_common.py`

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Experimental DeepGEMM workflows can now look up architecture-specific
configurations and detect unsupported device configurations.
* **Improvements**
* Shared experimental utilities now support generating reproducible
low-precision inputs and comparing GEMM results against reference
calculations.
* **Testing**
* Added coverage for configuration lookups, input generation, and GEMM
reference checks, including CUDA-gated cases.
* **Style**
* Experimental code now follows the project’s standard formatting and
include-sorting rules.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Avery Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [7c41f19](https://github.com/flashinfer-ai/flashinfer/commit/7c41f1995c979c135d75b9b98d1719e53f7aca42)

- **作者**: eigen
- **时间**: 2026-10-03T21:51:50Z
- **提交信息**: refactor(cake_gdn): collapse constant-clone kernels, merge SM100/SM103 copies, slim the manifest (#5939)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

Closes #5816

## Summary

The Cake-generated non-CP GDN backend (`csrc/gdn/cake`) shipped 112
kernel files that differed only in their
`#define` block, four SM100/SM103 copies that differed in one statement,
108 host shims with a shared 218-line
preamble, and a 56K-line manifest pinned by SHA-256. This PR keeps the
compiled kernels identical and removes the
duplication at the file level:

- One kernel source per distinct body (112 -> 41 files). The varying
constants of each variant are recorded in the
manifest as `defines` and passed to `nvcc` as `-D` flags, so every
variant still compiles to the same kernel. Three
prefill variants keep their original file with in-file defines
(`dvsplit_initial_bf16state_135bfa59984f`,
`..._d8b5b50285af`, `dvsplit_initial_f16io_f481beb70ea9`): for these
value sets nvcc 13.4 (sm_103a) schedules the
shared body with `-D` constants differently from the in-file form (same
instruction count; register assignment and one
uniform address computation differ), so they stay separate to keep every
variant SASS-identical to its original.
- The four SM100a/SM103a pairs are merged behind exact `__CUDA_ARCH__`
guards and carry both architectures in one output.
- The host-shim helpers (device guard, tensor checks, dynamic
shared-memory opt-in) live in one header; the unused
SM-count and dense-fold helpers and the `dlsym`-based oversized
shared-memory path (unreachable: every prefill kernel
  requests 226,048 B, below the SM100a/SM103a opt-in ceiling) are gone.
- The manifest keeps only what the loader reads; the 1,799
`contract_rows`, ABI/argument plans, row-count bookkeeping,
and checksum pins are removed. The loader no longer refuses to load
after a source edit.
- `RESULTS.md` and `validation-header.json` (benchmark dumps) are
removed; `README.md` documents the layout and no
  longer contains the unreplaced placeholder.
- Prefill host path: per-device facts are resolved once, placeholder
tensors are shared, and the metadata and resolver
  caches are bounded.

Public entry points, module and host symbol names, JIT cache idents and
import paths are unchanged.
`csrc/gdn/cake`: 471,619 -> 146,921 lines; branch: 225 files, +2,391 /
-327,042.

## Evidence

Every kernel variant was rebuilt from the deduplicated sources with the
loader's exact `nvcc` flags and compared with a
build of the original per-variant file at the SASS level, both sides
compiled under identical conditions (same staging
root length, same working directory) with a base-vs-base control; the
compiler's output for a few kernels of this
family depends on the compile path, so in-tree builds of two checkouts
are not directly comparable.

The final commit (57025dfd8) applies the repository's pinned
`clang-format` / `ruff format` to the shared host
header and the loader only (re-wrapping and include regrouping; no
kernel source touched), so the SASS and test
evidence below, gathered one commit earlier, applies unchanged.

| check | sm_100a (B200) | sm_103a (B300) |
|---|---|---|
| per-variant SASS equivalence vs original (108 / 101 kernels),
base-vs-base control | equivalent 108/108 (base-vs-base control 108/108,
0 serial recompiles) | 101/101 identical; control 101/101 |
| every variant loads (host shims compile) | 108/108 | 101/101 |
| family tests (`tests/gdn/test_cake_gdn_*`,
`test_prefill_state_indices.py`) | 322 passed / 3 skipped | 321 passed /
3 skipped; 1 CP-path case (`use_cp=True`, a code path this PR does not
touch) failed once and passed 6/6 on base and candidate in alternation
-- flaky in the existing suite, see below |
| bitwise outputs vs original (2 decode rows, 6 prefill rows incl.
checkpoints) | 8/8 rows EQUAL (out / state / checkpoints) | 8/8 rows
EQUAL (out / state / checkpoints) |
| prefill per-call host time, original vs this PR | 37-74 us -> 28-64 us
on the 6 prefill rows (lower on every row) | recorded (`HOST_TIME_US`) |

## Tests

/bot run tests/gdn/test_cake_gdn_decode.py
tests/gdn/test_cake_gdn_decode_gpu.py
tests/gdn/test_cake_gdn_prefill_gpu.py
tests/gdn/test_cake_gdn_decode_public_forwarding.py
tests/gdn/test_prefill_state_indices.py

## Decision for maintainers

Loader layout for the regenerated non-CP GDN backend (follow-up to this
PR): (a) keep the current standalone layout
-- a manifest of kernel variants, each compiled to a cubin with nvcc and
embedded into a per-variant TVM-FFI host
shim -- or (b) move to the registry layout the other Cake-generated
families use -- `flashinfer/jit/cake_gdn.py` lists
each generated program once and maps every logical kernel to its program
and compile-line defines, built through
`gen_jit_spec` like every other FlashInfer JIT module. (b) removes the
manifest, the custom cubin loader and the
per-variant host shims, and keeps the public resolver functions and
import paths unchanged. This PR's mechanical
cleanup works under either; the regenerated delivery is prepared for
(b).

## Not in this PR

- Auto-backend gating in `flashinfer/gdn_decode.py` (open PRs touch that
file).
- Regenerating the decode kernels depends on the same file: if the
regenerated argument plans do not match the
shipped host contract, the decode regeneration waits for PRs #4572/#4745
and this mechanical PR stands alone.
- Runtime head counts / scale / strides, dtype templates, caller-owned
prefill workspace, one host launcher per physical
  schedule: these need regeneration and follow separately.
-
`tests/gdn/test_prefill_state_indices.py::test_prefill_state_indices_matches_packed[...-cake_gdn-True]`
(CP path)
compares the final state bitwise against an `torch.empty` output buffer
of the packed baseline and failed once on
B300 without reproducing (6/6 passes on both trees); the CP family's
test, recorded as a follow-up there.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Cake GDN now compiles CUDA kernels from source and resolves only
variants listed in its registry.
* Cake prefill can be selected explicitly; automatic prefill continues
to use CuTe, while automatic decode tries listed Cake variants first.
* **Bug Fixes**
* Prefill now checks that indexed slots are within the state pool.
Decode accepts `-1` or a valid state index; optional asynchronous
validation is available through an environment setting.
* **Performance**
* Cake GDN reuses cached device details and placeholder tensors, with
bounded caches for host metadata and kernel variant selection.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [179006c](https://github.com/flashinfer-ai/flashinfer/commit/179006c333ed471c66296aef723ffd32535574a5)

- **作者**: eigen
- **时间**: 2026-10-03T21:43:34Z
- **提交信息**: refactor(cake_deepgemm_fp4_gemm): one runtime-shape program per schedule, no per-arch copies or per-shape catalog (SM100 / SM103) (#5935)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.


Closes #5830

## Summary

Regenerates the experimental native packed FP4 GEMM family
(`flashinfer.fp4_gemm.prepare_fp4_gemm`,
`flashinfer/experimental/deepgemm_fp4_gemm`,
SM100a + SM103a) from its Cake source with runtime problem sizes. The 20
per-shape,
per-architecture programs (10 exact `M:N:K:num_sms` routes per
architecture; the SM103a
copies differed from SM100a only in the hard-coded persistent stride 148
vs 152) and the
1.8K-line route catalog are replaced by **eight schedules, each one
source shared by both
architectures**: swap-AB BM16/32/48 x BN128 for M <= 128 and normal
BM128 x BN16/128/160/224/256.
Tile counts (`grid_m`, `grid_n`, `K_tiles`) and the SM count
(`gridDim.x`) are launch
arguments; the route is chosen per problem shape with DeepGEMM's wave
rule, which selects
the same schedule as before on every shipped shape. Any M is accepted (K
multiple of 256).

- The exact-key routes are gone: `alpha` is a runtime scalar on every
schedule and
  `num_stages` only validates against the selected schedule; `block_n`,
`epilogue_store_n` and `descriptor_workspace` keep their place in the
signature and
  accept their defaults (tensor maps are passed by value).
- Bindings are thin launchers on `tvm_ffi_utils.h` (device guard,
checks, one launch); the
previous private device-guard class, SM-count cache and mutex-guarded
attribute map are gone.
- The DeepGEMM raster group (16 M tiles per group for the normal
schedules, 8 N tiles for
swap-AB) stays a compile-time constant: it is identical for 148 and 152
SMs and in the
previous programs; tile counts and the SM count are the runtime values.
- The two routes reached only by the family test (the `alpha == 0.5` /
`num_stages == 7`
256x128x2048 row on the BN16 schedule and the 256^3 row) are kept, per
the maintainer
decision on the issue: the BN16 schedule stays a dispatcher candidate
(the wave rule picks it
only for N <= 128-class problems) and the 256^3 shape is served by the
BN128 schedule, so
  both rows remain in the regenerated test and in the A/B table below.
- 28,011 -> 7,360 lines (47 -> 25 files; 8 kernel bodies, 8 bindings, 2
shared headers, runtime, API, README, test, notice, clang-format).

## Validation

- `tests/experimental/test_native_fp4_gemm_generated.py` (regenerated:
shipped 10 shapes +
7 held-out shapes x alpha {1, -0.75}, analytical values with alpha 0.5
and CUDA-graph
replay, logical m < storage rows, rejection cases): 46 passed on B200
(69 s) and 46 passed on GB300 (34 s);
`examples/experimental/fp4_gemm.py` runs on both.
- Paired CUPTI A/B, same GPU and tensors, interleaved rounds, shipped
programs vs this
  branch, bitwise-identical outputs where the schedule is unchanged:

| shape (M x N x K) | schedule | B200 shipped us | B200 this PR us |
B200 ratio | GB300 shipped us | GB300 this PR us | GB300 ratio |
|---|---|---:|---:|---:|---:|---:|---:|
| 16 x 4608 x 5120 | `swap_ab_bm16_bn128_s11` | 7.424 | 7.488 | 0.991x |
7.200 | 7.232 | 0.996x |
| 16 x 5120 x 2304 | `swap_ab_bm16_bn128_s11` | 5.888 | 5.952 | 0.989x |
5.600 | 5.664 | 0.989x |
| 128 x 4608 x 5120 | `swap_ab_bm32_bn128_s10` | 7.616 | 7.648 | 0.996x
| 7.392 | 7.456 | 0.991x |
| 128 x 5120 x 2304 | `swap_ab_bm48_bn128_s10` | 6.016 | 6.049 | 0.995x
| 5.856 | 5.920 | 0.989x |
| 512 x 4608 x 5120 | `normal_bm128_bn128_s7` | 8.992 | 9.024 | 0.996x |
8.832 | 8.864 | 0.996x |
| 512 x 5120 x 2304 | `normal_bm128_bn160_s7` | 7.360 | 7.329 | 1.004x |
7.168 | 7.104 | 1.009x |
| 4096 x 4608 x 5120 | `normal_bm128_bn256_s6` | 34.240 | 34.368 |
0.996x | 30.496 | 30.656 | 0.995x |
| 4096 x 5120 x 2304 | `normal_bm128_bn224_s6` | 21.216 | 21.600 |
0.982x | 19.456 | 19.584 | 0.993x |
| 256 x 128 x 2048 | `normal_bm128_bn16_s7` | 4.704 | 4.736 | 0.993x |
4.448 | 4.512 | 0.986x |
| 256 x 128 x 256 | `normal_bm128_bn16_s7` | 5.471 | 3.968 | 1.379x |
4.960 | 3.520 | 1.409x |

Ratio = shipped time / this PR's time (> 1 is faster). B200: min 0.982x,
geomean 1.027x; GB300: min 0.986x, geomean 1.029x over the 10 shipped
shapes; the 7 held-out shapes have no shipped program and are covered by
the correctness test. The 256 x 128 x 256 row moves from the catalog's
generic BN128 program to the BN16 schedule (1.38x / 1.41x); every other
row is the same schedule and is within the paired measurement band.

## Test plan

```
pytest tests/experimental/test_native_fp4_gemm_generated.py -q
python examples/experimental/fp4_gemm.py
```

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added runtime schedule selection for FP4 GEMM across supported GPU
architectures and shapes.
* Made the logical output row count optional and added support for
outputs smaller than the input’s physical row storage.
* **Bug Fixes**
* Updated generated GEMM kernels to derive tile traversal and K-loop
bounds from runtime dimensions, improving support for varied shapes.
* **Documentation**
* Expanded FP4 GEMM guidance with input layouts, shape constraints,
scheduling details, and usage examples.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [7e5cfe4](https://github.com/flashinfer-ai/flashinfer/commit/7e5cfe4d557885aad79b51a4685da0ef421eb6ef)

- **作者**: eigen
- **时间**: 2026-10-03T21:43:01Z
- **提交信息**: refactor(cake_deepgemm_dense_mqa): one program set with runtime shapes and KV-range routes (SM100 / SM103) (#5988)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.


Closes #5829 (part of #5768).

## Summary

The dense FP4/FP8 MQA lightning-indexer logits
(`flashinfer.dense_mqa.prepare_dense_mqa_logits`,
`csrc/experimental/deepgemm_dense_mqa/generated`) shipped two
per-architecture source trees (11 programs
each) whose sm_103a copies differ from the sm_100a copies only in
literals derived from the SM count
(148 vs 152 and the metadata header offsets computed from it), four
metadata programs that differ only
in the query-block count they were traced for, four standalone FP4
bindings that no route launched (the
FP4 routes always ran the two-kernel prepared sequence), a catalog keyed
by the exact (precision, query
count, KV length, SM count) tuple with 20 routes per architecture, and
bindings carrying a per-process
SM-count cache, a mutex and private tensor checks. This PR regenerates
the family from its producer:

- **One program text per schedule for both architectures.** Ten
`*_kernel.cu` files (four of them the
metadata tiers) and their host bindings (plus five prepared-sequence
bindings for the FP4 routes)
replace 38 files; sixteen routes are validated on 33 shapes per
architecture. The metadata
producers take the query count at runtime. Every program takes the
launch grid of the logits
consumers -- the device's SM count -- as the compile-line definition
`SM_COUNT`: the delivered text
carries no SM count, the loader defines it per device from FlashInfer's
cached SM count (or from a
plan's CTA-budget override), and the per-SM cost partition and metadata
offsets fold at compile time
exactly as in the shipped kernels while one source text per program
serves every SM count (the
runtime-partition forms had measured 1-3.5 % slower on single-launch
rows with zero variance;
per-SM-count source copies are constant clones the export audit
rejects). The runtime compiles each program with the exact flags of the
device it runs on and
puts the target and the supplied definitions in the JIT spec name; the
catalog
  (`dense_mqa_catalog.json`, `dense_mqa.v5`)
  lists each program once with its per-architecture identities.
- **Routes by rule, not by table.** A problem selects its route from the
precision, the query count and
the KV length range (`route_name`): FP4 single-query or scheduled; FP8
single-query fused up to
K = 131072, 128-query fused up to K = 4096, otherwise metadata + indexer
(full or partial last query
block). The metadata producer comes in four query-ceiling tiers (`le16`,
`le128`, `le2048`, `any`;
the ceiling bounds its prefix arrays and boundary search at compile
time, the query count stays a
runtime argument) and a two-stage route carries the tier of its query
count in its name. Any query
count up to the schedule ceiling (`max_queries()`) and any KV length
that is a multiple of 256 are
accepted on both architectures with any SM count: the SM count is a
compile-time definition
(`SM_COUNT`) chosen per device at JIT time from FlashInfer's cached
device SM count, not a value
compiled into the delivered source. The base served 20 exact rows per
architecture and
  rejected every other shape.
- **Dead programs removed.** The four standalone FP4 bindings and the
sm_103a copies are gone; the FP4
routes keep their single prepared submission (`plan.launch_count == 1`).
- **Bindings** are the thin tvm-ffi launchers of the generated-program
export (no device-attribute cache,
  mutex or private checks).
- **Tests.** `tests/experimental/test_dense_mqa_generated.py` now checks
the twenty model rows and eight
rows outside the former route table (KV lengths 2048, 8192, 65536 and
1048576 at one query; query
counts 3, 7, 33, 130, 132, 2052 and 2053) against a PyTorch reference of
the indexer specification, the exact schedule
metadata (scalar specification of the DeepGEMM cost partition), the
`-inf` mask, a non-default stream
dependency and changed-input graph replay; DeepGEMM remains an
additional oracle when its build exposes the dense MQA logits API.
`test_dense_mqa_sm_count_definition[132|148|152]` builds the fused
single-query FP8 program on a CTA
budget of 132, 148 and 152 (the other SKU's count and a count outside
the catalogued SKUs; 152 exceeds
B200's SM count, so the grid runs a second wave) and checks the
per-count JIT module name, the exact
metadata and the reference: the coverage for SM counts no catalogued
device has.
`benchmarks/bench_dense_mqa_generated.py` reports CUPTI kernel time per
route.

Public entry point and signature are unchanged
(`examples/experimental/dense_mqa.py` runs as before).

## Validation

| gate | sm_100a (B200) | sm_103a (GB300) |
|---|---|---|
| export run: source (production launchers) vs export (FlashInfer plan),
36 rows: torch reference, exact metadata, exact mask, bitwise parity, no
allocation | 36/36 pass; source/export 0.955x-1.034x, geomean 1.000
(floor 0.90) | 36/36 pass; source/export 0.964x-1.074x, geomean 1.000
(floor 0.90) |
| SASS: FP4 logits kernel vs the shipped copy (REG 168 = 168, dynamic
smem 206336 B = 206336 B; bodies differ by construction: the shipped
sm_100a copy divides by a compiled-in SM count, and the current
generator renders warp-uniform lane/warp indices, unsigned index casts
and the arch-conditional shared-memory address differently; A/B-gated) |
logits kernel REG 168 = 168, dynamic shared memory 206336 B = 206336 B,
53 = 53 warp syncs, 14 = 14 TMA ops, stack 0 = 0, local 0 = 0; 1960 vs
2032 instructions | logits kernel REG 168 = 168, dynamic shared memory
206336 B = 206336 B, 53 = 53 warp syncs, 14 = 14 TMA ops, stack 0 = 0,
local 0 = 0; 1952 vs 2032 instructions |
| SASS: every program (compile-line SM count; metadata producers with a
runtime query count) expected equal to the shipped copies up to the
generator's rendering (A/B-gated) | 19 kernel symbols vs 14 shipped.
Every logits consumer keeps REG 168 and has fewer instructions than the
copy it replaces: FP4 1960 vs 2032, FP8 two-stage 1744 vs 1824, fused
q=1 1680 vs 1760, fused q=128 2000 vs 2080; the partial-last-block
consumer (1776) has no shipped counterpart. Metadata producers: REG
30/32 (14 for the fused q=1 producer) vs 24/28, 232/264/392/448 (80) vs
208/240/256/288 instructions -- one program per query tier taking the
query count at runtime instead of one per traced shape. stack 0 and
local 0 on every symbol | 19 kernel symbols vs 14 shipped. Every logits
consumer keeps REG 168 and has fewer instructions than the copy it
replaces: FP4 1952 vs 2032, FP8 two-stage 1760 vs 1824, fused q=1 1696
vs 1760, fused q=128 2016 vs 2080; the partial-last-block consumer
(1792) has no shipped counterpart. Metadata producers: REG 30/32 (14 for
the fused q=1 producer) vs 24/28, 232/264/392/448 (80) vs
208/240/256/288 instructions -- one program per query tier taking the
query count at runtime instead of one per traced shape. stack 0 and
local 0 on every symbol |
| `tests/experimental/test_dense_mqa_generated.py` | 51 passed | 51
passed |
| paired A/B base vs candidate, 20 model rows, CUPTI per-kernel GPU time
summed over the kernels of one call (`bench_gpu_time`), the two arms'
calls interleaved inside one profiling session with the order rotating,
cold L2 before every call; every row >= 0.98 and geomean >= 1.00 | 20/20
rows >= 0.98, min 0.9943 (`fp4:q128:k131072`), geomean 1.0180; 20/20
paired rows bitwise equal; 13/13 holdout rows correct | 20/20 rows >=
0.98, min 0.9911 (`fp8:q16:k4096`), geomean 1.0199; 20/20 paired rows
bitwise equal; 13/13 holdout rows correct |
| per-call host wall of `run()` in a backpressure-free regime: the
stream is drained, a device-side wait is queued so it stays busy for the
whole block, 20 calls are issued per block and the first 3 are discarded
as block setup, arms alternating per block (candidate p50 <= shipped p50
x 1.05, with p10 / p90 and the measured blocked fraction reported next
to it; a row that still shows blocked calls above 1 % is reported as
queue-bound and gated on p10, because its p50 then mixes enqueue cost
with GPU drain) | 20/20 rows measured backpressure-free; candidate p50
0.968x-0.996x of the shipped loader (median 0.977x), 13.4-17.0 us vs
13.7-17.4 us | 40/40 rows measured backpressure-free; candidate p50
0.954x-1.022x (median 0.993x), 18.1-25.4 us vs 18.0-25.0 us; no row
above the 1.05x limit |
| rows outside the old table (candidate only; reference + metadata) |
13/13 pass (PyTorch reference, exact schedule metadata, exact mask); Q =
1, 3, 7, 16, 33, 128, 130, 132, 2052, 2053 at K = 2048, 8192, 65536,
1048576 | 13/13 pass (PyTorch reference, exact schedule metadata, exact
mask); Q = 1, 3, 7, 16, 33, 128, 130, 132, 2052, 2053 at K = 2048, 8192,
65536, 1048576 |

Timing rule for the multi-kernel routes (metadata producer + logits
kernel, whether the two are
submitted separately or as one prepared sequence): the gate counts the
GPU time of both kernels of a
call. The time between them is not kernel time -- under programmatic
dependent launch the consumer
starts while the producer is still finishing, so a *shorter* producer
gives back exactly as much
overlap as it saves, and a metric that measures the extent of the call
rather than its kernels moves
with that overlap. The host side of a call is gated separately as
per-call host wall, and the
captured-graph span and the eager per-iteration span are reported as
diagnostics next to the gate.
Routes that launch a single kernel are the same measurement with one
kernel in the sum.

Why this metric: two earlier ones were rejected by a control
measurement. Running the *shipped*
loader in **both** arms (an A/A), the span of a captured-graph replay
read 0.962-1.034 across the
5-9 us two-kernel rows -- the per-capture offset and the overlap above
dominate there -- and neither
more captures (8 -> 32), nor releasing each row's captures and memory
pools, nor re-capturing every
round, nor balancing the measurement position brought it inside 1 %.
Per-kernel time, measured the
same way, puts the same A/A inside 1 % on every row, which is the
acceptance applied before any
comparison is read. Rows are measured one per process where the A/A
shows the allocator state left
by earlier rows biasing a row (one short row read 1.014-1.017 against
itself in a shared process and
0.998 measured alone); the isolation mode is whichever one that
architecture's own A/A admits, and
it is recorded with the run. Thresholds and tolerances are unchanged
throughout.

Host-wall rule: the per-call host wall is the cost of *enqueuing* a
call, so it is only a host
statistic while no call waits for the GPU. Issuing a long block of calls
back to back does not
measure that: the driver's command buffer fills (these routes pass five
128-byte tensor-map
parameters by value per launch), after which a call returns only when a
queued submission retires,
at 60+ us. That regime also cannot be gated on how often a call blocks,
because the arm with the
*cheaper* enqueue reaches the queue limit sooner and therefore blocks
more often. The gate therefore
drains the stream, queues a device-side wait so the stream is busy
without being saturated, issues
20 calls per block, discards the first 3 (block setup), and reports the
measured blocked fraction
next to p10/p50/p90 so the regime is visible per row.

The captured graph is structurally the same as the one the shipped
loader produces: two kernel nodes
and one dependency edge, no memset/memcpy/host/event nodes, the same
`<<<grid, block, dynamic
shared memory>>>` on each node (`<<<1, 256, 128>>>` for the schedule
producer and
`<<<SM count, 384, 224768>>>` / `<<<SM count, 384, 206336>>>` for the
FP8 / FP4 consumer),
`cooperative = 0`, `priority = 0` and no access-policy window on either
node, and the same single
`cudaLaunchAttributeProgrammaticStreamSerialization = 1` launch
attribute on both kernels. The only
difference is which kernel each node points at -- and the shipped tree
needs a different schedule
producer per KV length where the regenerated one uses a single
runtime-shaped producer. Because the
producer signals `griddepcontrol.launch_dependents` in its first
instructions, the overlap between
the two kernels is the producer's remaining runtime, so a shorter
producer gives back the same
amount of overlap: measured per capture, the inter-kernel gap moves by
exactly the producer's
duration difference. One captured graph carries a fixed per-capture
timing offset (0.45 us between captures of one arm on an 8 us route
here), so the graph span is
pooled over independently captured instances, and more of them when
their spread is large, and the
two arms time each instance back to back rather than one arm's instances
after the other's: an arm
whose whole block of instances is timed seconds away from the other
arm's picks up any excursion in
that window as a per-instance spread of its own.

Line count: family 25972 -> 14306 lines (46 -> 32 files); `generated/`
23039 -> 11697 lines (39 -> 25 files). Both architectures regenerate the
identical tree (`76ec361e56dd`).

## Follow-ups (not in this PR)

- The FP8 two-stage routes submit the metadata producer and the indexer
as two calls (as before); a
single prepared submission needs per-stage compile flags in the sequence
binding.

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [7c21894](https://github.com/flashinfer-ai/flashinfer/commit/7c218946f9da4c8ee9d086f4e6c2430cdd6373d8)

- **作者**: eigen
- **时间**: 2026-10-03T21:41:30Z
- **提交信息**: refactor(cake_vsa): one device source per profile, shared host shim, JIT loader, plan-time FP16 metadata (SM100 / SM103) (#5926)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

Closes #5826

### What changed

`csrc/cake_vsa` (SM100/SM103 block-sparse attention,
`BlockSparseAttentionWrapper(backend="cake")`):

- **One device source per profile for both architectures.** The ten
`*_sm_103a.cu` files were byte-identical to their `*_sm_100a.cu` twins;
each profile is now one `cake_vsa_<profile>.cu` compiled for `sm_100a`
and `sm_103a` (-16,302 duplicated lines).
- **One shared host shim.** The ten per-profile `*_host.cpp` launchers
(4,163 lines, each carrying private tensor-check copies, a mutex-guarded
per-device shared-memory cache and a dead oversized-SMEM branch) are
replaced by `cake_vsa_binding.cu`, compiled once per `(profile, arch)`
with the profile's route defines. It uses `tvm_ffi_utils.h` checks,
`ffi::CUDADeviceGuard`, `get_stream`, one static kernel handle
(`GetKernelWithMaxDynamicSharedMemory`) and one launch; kernel argument
order, TMA descriptors (dims, boxes, swizzle) and extent checks are
unchanged.
- **`gen_jit_spec` modules.** `flashinfer/jit/cake_vsa.py` registers
`cake_vsa_<profile>_<arch>` JIT specs (exact `sm100a` / `sm103a` flag
sets) whose cubin is produced by the JIT's embedded-cubin path with the
same compiler command the previous private `nvcc` subprocess used; the
manifest, its import-time digest re-verification and `cpp.load_inline`
are gone.
- **FP16 direct-route metadata in `plan()`.** The per-token selections,
sequence offsets and page table of the FP16 GQA route are built once at
plan time; `run()` validates tensor metadata and launches, with no
device reduction or host synchronization on any route. Architecture and
SM count are resolved once per device.
- **Behavioural tests** replace the manifest-digest and launch-tuple
mock tests: JIT spec contract per profile/arch, launch records against
the device sources, plan-time FP16 metadata, `run()` under
`torch.cuda.set_sync_debug_mode("error")`, FP16 GQA re-plan on the same
wrapper, custom softmax scale, plus a new dense-reference row (FP16 GQA,
three selected blocks, two query tiles, LSE).
`benchmarks/bench_cake_vsa.py` times every test and deployment row with
CUPTI.

Public API (`flashinfer.cake_vsa.plan_cake_vsa` / `run_cake_vsa`,
`BlockSparseAttentionWrapper(backend="cake")`) is unchanged;
`flashinfer/sparse.py` is untouched.

Not in this PR (recorded follow-ups): templating the dtype clone
(`blk128_compact` vs `blk128_fp16_compact`, 38 differing device lines)
and the head-dimension kernels (head64/head96 differ in pipeline depth,
TMA rank and shared-memory map, not only in head size) requires
regenerating the kernels from their producer; the workload gates of the
ultrasparse (`MB >= 625`, exactly six selected blocks, eight heads) and
long-sequence (`N >= 16384`, eight heads) routes are kernel contracts
and stay explicit errors.

### Size

`csrc/cake_vsa`: 31 files / 37,879 lines -> 11 files / 16,932 lines (10
device sources + 1 shared binding); 16,302 lines of per-architecture
copies and 10 duplicated host shims removed. Whole PR: 37 files changed,
+1,561 / -22,095.

### Validation

- SASS equivalence of every device source for `sm_100a` and `sm_103a`
(base per-arch files vs one file per profile): equivalent on both build
hosts (B200 host, CUDA 13.3 and GB300 host, CUDA 13.4): 20 base kernels
vs 20 candidate kernels, 10 distinct bodies per architecture, 0 missing,
0 introduced.
- Cubin identity of the previous private `nvcc` path vs the JIT cubin
factory, 10 profiles x 2 arches: 20/20 rows SASS-equal with
byte-identical cubins; each profile module (`cake_vsa_<profile>_<arch>`)
builds and loads.
- Family tests (`tests/attention/test_cake_vsa.py`,
`tests/attention/test_cake_vsa_planning.py`): 46 passed on B200
(sm_100a) and 46 passed on GB300 (sm_103a). The planning tests run
without a GPU.
- Bitwise-identical outputs base vs candidate over the test and
deployment rows; CUPTI median ratio: 19/19 rows bitwise-identical output
(8/8 LSE rows bitwise-identical) on both GPUs; CUPTI median ratio
candidate/base geomean 1.0007 on B200 (min 0.9886 on a ~14 us row, max
1.0336) and 1.0009 on GB300 (min 0.9987, max 1.0117).

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added a command-line benchmark for Cake block-sparse attention, with
test and deployment workloads, GPU timing results, and optional JSON
output.
* Cake VSA kernels can now be compiled and loaded at runtime for
supported GPU architectures.
* **Improvements**
* Attention planning now prepares FP16 GQA selection metadata ahead of
execution and refreshes it when plans are rebuilt.
* Custom softmax scaling is applied consistently across execution
routes.
* **Compatibility**
* Some previously available Cake VSA kernel variants and launch paths
have been removed.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [20e3d4e](https://github.com/flashinfer-ai/flashinfer/commit/20e3d4e6cac2765dafa3391aafb73c220a2e9a99)

- **作者**: eigen
- **时间**: 2026-10-03T21:40:49Z
- **提交信息**: refactor(cake_vsa_sm90): drop the planner-dead split stages, regenerate the Hopper VSA kernels with shared headers and thin launchers (SM90) (#5923)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

Closes #5827

### What changes

`backend="cake"` (Hopper SM90 variable block-sparse attention) ships the
same kernel family, regenerated by its Cake
producer:

* **Two split-KV stages removed** (`small_k1s`, `small_k3s`). The
wrapper's planner ranks the split-KV variants by
`chain_blocks(kmax) + 0.3 * (max_nsplit - 1)`. KMAX 3 has the same
two-block chain as KMAX 4 and never fewer slices,
so it is never selected (0 of 1,015,875 swept masks on 78/114/132 SMs).
KMAX 1 was selected only on a band of ragged
masks whose grid sits at the sliced-route edge (`2 * tiles` within two
of the SM count) with one 13..31-block outlier
selection, where KMAX 3/4/6 all exceed the one-wave item budget (28 of
1,015,875 masks); those masks now run the
persistent kernel. The split table is `SPLIT_KMAX_VARIANTS = (4, 6)`;
`plan_small` refuses a split plan for a variant
that does not ship. Tests cover the table, the edge-band mask and a
KMAX-4 two-slice case.
* **One flat `csrc/cake_vsa_sm90/` layout, shared headers, thin
launchers.** The 14 remaining kernels are rendered
as one device/binding pair each plus one shared device preamble
(`cake_vsa_sm90_device_common.cuh`, 155 lines) and
one shared launcher-helper header (`cake_vsa_sm90_host_common.cuh`, 52
lines). The launchers are plain
`tvm_ffi_utils.h` launchers (device guard, stream, checks, one launch):
the per-kernel RAII device guard, mutex,
per-device `unordered_map` cache and `cudaDeviceGetAttribute` query are
gone. The JIT loader adds the family
directory to the include path; module names come from the manifest as
before.
* **Kernel bodies unchanged.** All fourteen kernel bodies are
text-identical to main's (from the `__global__`
declaration on, modulo the program fingerprint in the symbol).
Compile-only sm_90a SASS equivalence against main:
14 of 14 kernels instruction-identical. The only preamble change is the
generator's dead-helper elimination:
18 helper units no kernel body references (`CakeTensorMap`, the unused
`mbarrier_*` wait variants, `desc_encode`,
  `make_smem_desc`, `fence_async_shared`) are no longer emitted.

Lines: `csrc/cake_vsa_sm90` 55,825 -> 50,632 (`.cu` + `.cuh`) after the
pinned clang-format pass below (41,572 as rendered); the PR is net
-3,001 lines against main (`git diff --numstat`).

* **Formatting of the generated sources.** `csrc/cake_vsa_sm90/` is
covered by the repository's clang-format hook (`.pre-commit-config.yaml`
pins `mirrors-clang-format` v19.1.1), so the fourteen kernel and binding
translation units and the two shared headers are delivered
post-formatted with that release in a separate commit. The pass is
whitespace, `#include` ordering and string-literal line breaking only:
every file is token-identical to the rendered output after
adjacent-literal concatenation, and the compile-only sm_90a SASS
equivalence below is re-run on the formatted commit. The source manifest
that pins the generated-source digests is refreshed in the same series
(`sha256` and `bytes` recomputed over the formatted files, canonical
JSON form unchanged), because the loader verifies every source against
it before building. The producer emits unformatted sources today; making
it format generated files before it records their digests is a follow-up
on the producer side.
* **CuTe test.** `test_cake_vsa_sm90_cute.py` no longer launches the
CuTe `small_k3s` stage directly: that test built its plan with
`plan_small(kmax=3, split=True)`, which this PR rejects (the split table
is KMAX 4 and 6), and it failed on the Hopper CI runner. The CuTe tree
keeps `small_k1s` and `small_k3s` until the build decision, but no route
produces a plan for either.

### What does not change

Public API (`VariableBlockSparseAttentionWrapper(backend="cake")`,
`plan`/`run`, DPS output ABI), the planner's
pair/split/small/cluster routes except the split table above, module/JIT
spec naming scheme, tolerances. The CuTe DSL
build (`backend="cake_cute"`) is untouched in this PR and keeps
dispatching to its own tree; its stage table test drops
the `small_k1s` case the planner can no longer produce.

**Build decision (separate item on #5827, maintainers' call).** The
family ships every kernel twice (CUDA and CuTe DSL)
with the same planner. Our proposal is to keep the CUDA build and accept
`backend="cake_cute"` as an alias of `cake`
(no API break): the recorded per-row numbers favour neither build
consistently (CuTe/CUDA 0.98..1.01 over the four
shape families) while the CuTe launch path adds ~11 us of host time per
call. The removal is prepared as one separable
commit on a follow-up branch and stays out of this PR until the
maintainers answer on the issue; if the CuTe build is
preferred instead, this PR still applies unchanged.

### Validation

* Planner sweep (CPU): 1,015,875 synthetic masks (uniform top-k,
one-outlier, two-level, random ragged) on 78 / 114 /
132 SMs with the real `small_route`: `small_k3s` never selected on main;
`small_k1s` only on the edge band described
  above; on this branch those masks route to the persistent kernel.
* Export slop audit on the regenerated family: clean except 14
`cxx_class` hits = the POD parameter carrier
`CakeParamArray<int16_t, N>` (trivially copyable, `operator[]` only);
audit-rule refinement tracked on the producer side.
* Compile-only SASS equivalence (sm_90a,
`FLASHINFER_CUDA_ARCH_LIST=9.0a`, nvcc from the same toolkit for main
and this
branch, `cuobjdump -sass` bodies normalised on the kernel symbol):
`equivalent=True`, 14 base / 14 candidate kernels, 14
  distinct bodies, none missing, none introduced.
* `tests/experimental/test_cake_vsa_sm90.py` +
`test_cake_vsa_sm90_cute.py` CPU subset (planner, plan layouts, split
table, stage tables): 37 passed / 105 skipped (Hopper-only) on both
x86_64 and aarch64 hosts (CPU-only torch). The GPU subset and
`benchmarks/bench_cake_vsa_sm90.py` need an H100 — **maintainer run
requested** (we have no Hopper in our
allocation): `pytest tests/experimental/test_cake_vsa_sm90.py` and the
paired benchmark on main vs this branch (same
GPU), plus one edge-band mask (h=6, mb=11, nb=16; 65 query blocks with 7
KV blocks, one with 13) before and after.
With 14/14 SASS-identical kernels the kernel-side risk is the planner
table only; the launcher change (thin
  `tvm_ffi_utils.h` launchers) is what the GPU run exercises.

### Maintainer run requested (no Hopper in our allocation)

This PR could only be validated compile-only: the fourteen remaining
kernels are SASS-identical to main's, and the two
removed split stages are never selected by the planner except
`small_k1s` on an edge band of ragged masks (2 * tiles
within two of the SM count, one 13..31-block selection), which now runs
the persistent kernel. Could a maintainer with
an H100 run `pytest tests/experimental/test_cake_vsa_sm90.py` and
`python benchmarks/bench_cake_vsa_sm90.py --output vsa-sm90.json` on
main and on this branch (same GPU), plus one
edge-band mask (h=6, mb=11, nb=16; 65 query blocks with 7 KV blocks, one
with 13) before and after? With identical
kernel SASS the GPU run exercises the thin launchers and the planner
table.

### Not in this PR (recorded on #5827)

* Templating the 14 small-selection kernels into one `template <int
KMAX, ...>`: the audit shows 14 distinct kernel
skeletons (every variant unrolls its KMAX stages), so a literal-template
fold does not apply; a real template needs
  an `if constexpr`-emitting generator path plus an H100 A/B.
* Dropping the debug timeline buffers from the persistent kernels' ABI:
`dbg[62:64]` are the queue kernel's live
tile-queue words; removing `tl` (and `dbg` on the static kernel) changes
the kernel signature and needs the GPU gate.
* Plan as a device buffer / plan-time TMA metadata: the CUDA build
already takes the plan as one by-value 3,500-byte
parameter array and encodes its three TMA descriptors per launch in the
launcher (Q/K/V addresses change per call);
the per-call expression evaluation and 438-scalar marshalling belong to
the CuTe build (build decision item).

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Split-KV planning now selects only supported KMAX 4 and 6 variants and
rejects plans using unsupported split sizes.
  * Small workloads with 66 tiles now fall back to the persistent route.
* **Internal Updates**
* Consolidated shared CUDA setup and validation across generated
kernels.
* Updated generated kernel registrations and removed obsolete SM90a
kernel launchers.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [508a098](https://github.com/flashinfer-ai/flashinfer/commit/508a098fac678f197d32ccb9312ff60f1ab1e0ab)

- **作者**: eigen
- **时间**: 2026-10-03T21:38:38Z
- **提交信息**: refactor(cake_selective_state_update): regenerate the checkpoint, MTP and FP32 STP programs as architecture-neutral sources, keep the shipped BF16 STP kernels (SM100 / SM103) (#6003)

Closes #5825 (part of #5768).

## What changed

The Cake selective-state-update backend shipped 14 generated device
programs per architecture plus a 14-way host preamble under
`csrc/cake_selective_state_update/{cuda,host}`; most of them were copies
of one another. This PR regenerates the checkpoint, MTP and FP32 STP
programs as architecture-neutral sources and keeps the five shipped BF16
single-token (STP) programs exactly as they are on `main`.

- **Checkpoint kernels.** The four `dynamic_checkpoint{0,1,3,7}`
programs differed only in a compiled-in checkpoint step and read the
step back to the host before every launch. They are replaced by one
program that reads the per-token destination table
(`dst_state_batch_indices`, shape `(batch, tokens)`) on the device and
writes the state of every non-padded destination slot. No `.item()`
remains in the route; the new test captures the route into a CUDA graph
and replays it.
- **SGLang projection layout.** The `mtp_cache_bf16_c4_t6_sglang_raw`
clone and its stride matcher are gone. The cache program is one source
whose `x`, `B`, `C`, `dt` batch/step strides (`*_BATCH_STRIDE`,
`*_STEP_STRIDE`), the storage dtypes of the SGLang ABI (BF16
`dt`/`D`/`dt_bias`, int32 slot tables: `COEFFICIENT_BF16`, `INDEX_I32`)
and, for that ABI, the model constants `nheads`/`ngroups`
(`NHEADS_STATIC`, `NGROUPS_STATIC`) are compile-time defines selected by
the loader from the tensor metadata: one instantiation per projection
layout, as the former clone was compiled (head/group rows must be dense,
the coefficient tensors carry one element per head). The canonical
layout and the SGLang projection layout run the same source; tests cover
both layouts against the FlashInfer reference.
- **`mtp_short`, `mtp_horizontal`, `stp_fp32_identity`** are regenerated
as one source each for both architectures (the SM100/SM103 copies were
identical up to the architecture guard).
- **Tensor maps by value.** Every regenerated program receives its TMA
descriptors as `__grid_constant__` kernel parameters; the process-wide
descriptor arena, its mutex and its allocation are deleted from those
programs.
- **Host path.** The per-program host preamble (device queries, SHA-256
pin table, argument-plan interpretation) is replaced by one thin loader,
`flashinfer/jit/mamba/cake_selective_state_update.py`, that caches the
device architecture and SM count per device index and compiles each
regenerated program once per architecture and define set (the JIT module
of an instantiation is named by a 16-hex digest of its define set; the
loader's `MODULES` manifest maps every delivered digest back to its
define values). The `flashinfer.mamba.cake_selective_state_update`
import path, `selective_state_update(..., backend="cake")` and the
public argument names are unchanged.
- **Kept as shipped: the BF16 STP programs.**
`cuda/cake_selective_state_update_stp_bf16_{direct,ratio8,ratio8_saturated,ratio16,persistent}.cu`
and their `host/*.cc` bindings are byte-identical to `main`. The loader
keeps their selection rules (`shipped_stp_program`: persistent above the
direct resident-wave cap, otherwise the clone of the head ratio), builds
them as before (nvcc cubin embedded by the host binding, unchanged JIT
module names) and only drops the SHA-256 pin check on their sources.
Why: the regenerated direct program measured 3.5-4 % slower than the
shipped clone on B200 at heads-per-group 1 (two identical rows, 0.9605 /
0.9666 in an isolated 21-round paired A/B; GB300 1.0136 / 1.0166 on
identical SASS), so the regenerated STP programs are kept out of this PR
and tracked as a follow-up below.
- **Route guards and fallbacks.** Every regenerated route plans a launch
only for the shapes its program indexes (`x`, `dt`, `B`, `C`, `A`, `D`,
`dt_bias`, `output`, the slot tables and, on the horizontal route, the
intermediate-state buffer) and only for broadcast coefficients (one
value per head for `dt`, `A`, `D`, `dt_bias`); other shapes plan no
launch. Layouts the shapes admit but a program cannot read
(non-contiguous buffers, tensor-map strides) are rejected by the
binding's argument validation, which runs before any launch; the loader
catches that rejection and the call runs on FlashInfer, so no caller
sees a `ValueError` from the Cake backend for a layout FlashInfer
serves. With `FLASHINFER_DISABLE_JIT` set and no build of the planned
program in the JIT cache, the loader catches `MissingJITCacheError` at
the program load and the call runs on FlashInfer; that is the one
fallback path for every program, with or without compile-time defines.
The generated sources are rendered through the repository's pinned
clang-format and the loader and tests through its pinned ruff, so
pre-commit sees them as already formatted.
- Tests that asserted file inventories or hashes are replaced by
behavioural tests: canonical and SGLang-layout parity with the
FlashInfer reference, per-sequence destination columns, CUDA-graph
capture of the checkpoint route, define selection for the cache program,
the shipped STP selection rules and presence of their sources, and
loader/registry consistency, the JIT-disabled fallback (with JIT enabled
the checkpoint and cache routes run on Cake, with JIT disabled and the
program's build missing from the cache the same calls return
FlashInfer's result; a cache layout outside the shipped instantiations
goes through the loader's real `MissingJITCacheError` path) and the
route fallbacks (a padded non-contiguous `x` on the identity, short and
dynamic routes and a strided slot table on the horizontal route reach
FlashInfer and match, a padded `x` stays on the horizontal program
through its tensor maps; a dense `A` on the identity route is refused by
both backends alike; mismatched head and state-size shapes plan no
launch). The STP test rows (ratio 1 / 8 / 8 saturated / 16 / persistent
/ FP32) are unchanged.

Generated lines: 11,386 (28 files: 14 CUDA sources + 14 host bindings)
-> 8,575 (20 files: 5 regenerated CUDA sources + 5 bindings, plus the 10
kept BF16 STP files); net diff -2,672 lines across the family (26 files,
+2,947 / -5,619).

## Not in this PR (follow-ups on the issue)

- **Regenerating the five BF16 STP programs** (one direct source with
the `HEADS_PER_GROUP_STATIC` / `DIRECT_UNROLL` defines plus the
persistent program). The regenerated direct program measured 3.5-4 %
slower on B200 at heads-per-group 1 and is kept out of this PR; the
shipped kernels' mbarrier waits carry a phase-check + nanosleep backoff
that the regenerated program's waits do not (identical SASS on both
architectures: -136 instructions, +118 uniform-datapath ops, -40
`SYNCS.PHASECHK.TRANS64` / `NANOSLEEP.SYNCS` pairs). It lands once that
row clears the floor on B200.
- The exact-shape route limits of the production dispatch (which shapes
reach each program) are kept as they are; widening them is recorded on
#5825.
- The `flashinfer.mamba.cake_selective_state_update` alias is kept
(decision requested on #5825).

## Validation

- SASS per architecture (sm_100a, sm_103a), normalised `cuobjdump -sass`
bodies of the regenerated programs vs. the production kernels they
replace: `stp_fp32_identity` is byte-equivalent to its clone
(`check-sass-equivalence`: one base kernel, one candidate kernel, one
distinct body per architecture; 272 instructions / 48 registers).
`mtp_short` is a regenerated program, not a byte-for-byte clone: 640
instructions / 62 registers on both sides, 8 normalised diff lines (two
`@!P FADD.FTZ` scheduled unpredicated), gated by the tests,
bitwise-identical outputs and the A/B rows. `mtp_cache_c4_t6`
instantiations vs. the clones they replace, identical on both
architectures: canonical define sets 952 instructions vs. 968 (generic
clone), registers 62 vs. 60; SGLang define set 840 vs. 840 (layout
clone), registers 65 vs. 65 (a folded group count drops the group offset
from the B/C address chain and a folded head count folds the state slot
strides, exactly as the clone had them); same shared memory; every
define set carries all six of the clone's read-only
(`LDG.E[.U16].CONSTANT`) coefficient and slot-table loads. The `dynamic`
program is text-identical to its source but nvcc 13.3 emits four
`LDS.U16` where NVRTC emits one `LDS.64` + `PRMT` for the four
consecutive BF16 `B`/`C` shared-memory reads (1800 vs. 1864
instructions, 48 vs. 51 registers); measured eager on both GPUs the nvcc
variant is equal (B200 2.816/2.816 us; GB300 2.848/2.848 us) or faster
(GB300 eight-token row 4.192 vs. 4.352 us). The kept BF16 STP sources
are byte-identical to `main` and are built with the same `nvcc -O3
--fmad=false` line as before, so their SASS is unchanged by
construction.
- `tests/mamba/test_cake_selective_state_update.py`: B200 36 passed;
GB300 36 passed (includes the CUDA-graph capture test of the checkpoint
route, the SGLang-layout tests, the five BF16 STP rows through the kept
programs, the JIT-disabled fallback and the route fallbacks).
- Host path of the guarded routes (per-call wall clock of the full
backend call, same process, interleaved with the FlashInfer reference
`base`): B200 identity 13.9 / 13.6 us vs base 15.5 / 15.5, short 16.1 /
16.0 vs 16.7 / 16.9, horizontal 17.4 vs 18.9, checkpoint 15.7 / 15.8 vs
96.2 / 96.6; GB300 identity 14.5 / 14.6 vs 15.8 / 15.6, short 21.5 /
21.3 vs 22.7 / 22.8, horizontal 23.2 vs 26.2, checkpoint 20.7 / 21.1 vs
146.5 / 151.0. Every guarded route plans and launches in less host time
than the reference call on both architectures.
- Formatting is a no-op on the binaries: every regenerated program and
delivered instantiation (7 kernels x 2 architectures) compiled from the
unformatted and the clang-formatted source gives byte-identical cubins
and identical SASS on sm_100a and sm_103a; the kept BF16 STP sources are
untouched.
- Paired CUPTI A/B against the base tree on the same GPU, interleaved
rounds (41 rows: 26 served contract shapes + 15 test-matrix shapes; 13
of them run the kept BF16 STP kernels in both arms), bitwise-identical
outputs, states and intermediate states on every row. GPU gate = kernel
time per row (CUPTI kernel records; the regenerated checkpoint route is
measured as a replayed CUDA graph, the base route eagerly since it
refuses capture): GB300 min 0.9844 (`granite_ngram_t6_c4_sglang_raw_b1`)
geomean 1.5739 over 15 interleaved rounds x 40 CUPTI iterations; B200
min 0.9811 (`granite_ngram_t6_c4_sglang_raw_b1`) geomean 1.6179, same 15
rounds. Every row >= 0.98 and geomean >= 1.00 on both architectures; the
lowest row is the 4 us SGLang cache instantiation at batch 1, re-read in
an isolated 21-round same-process A/B of the five 4-5 us cache rows at
0.9809 (B200, 4.111 vs. 4.192 us) and 0.9843 (GB300, 4.000 vs. 4.064
us), one to two 32 ns ticks inside the floor, with an A/A control of
identical trees reading 1.0000 on every row on both nodes. Host path
(per-call enqueue wall time, separate must-not-regress table, sampled
once per round under the same rotated arm order): no row regresses by
more than the 2 us `perf_counter` tolerance on either architecture;
median saved 1.3 us on GB300 and -0.4 us on B200. Allocations per call:
0 on both arms, every row.

## Test paths

`tests/mamba/test_cake_selective_state_update.py`

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

- **New Features**
- Added Cake selective state update routes for SM100 and SM103, covering
single-token, multi-token, cache, and dynamic updates.
- Added support for per-sequence checkpoint choices, CUDA graph capture,
padded projection layouts, and compatible coefficient and index formats.
- Dynamic updates now support canonical inputs across 1–8 token steps
without restricting checkpoint positions.
- **Bug Fixes**
  - State updates now use the destination slot selected for each token.
- **Removed Capabilities**
- Removed legacy update variants, including specific checkpoint,
raw-layout cache, horizontal, and identity paths.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <yyihuang@nvidia.com>

### [0d36444](https://github.com/flashinfer-ai/flashinfer/commit/0d364444a794c6a38639c60ec164ca57799e3aeb)

- **作者**: eigen
- **时间**: 2026-10-03T21:37:49Z
- **提交信息**: refactor(cake_mm_fp4): regenerate the per-token NVFP4 programs as architecture-neutral sources (SM100 / SM103) (#5971)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

Closes #5823.

## Summary

The experimental `flashinfer/experimental/cake_nvfp4_per_token` package
(the
`backend="cake"` per-token NVFP4 quantizer + GEMM for SM100 / SM103) is
regenerated from its generator with the structure the issue asks for:

Quantizer tiers: contiguous row sets of fewer than 8192 tokens at K in
{2688, 4096, 7168} take an instance with the row width compiled in (key
suffix `_k<K>`, defined on the compile line as `K_STATIC`): those widths
and row counts are the ones where the compiled-in build won or tied the
runtime-geometry build of the same CTA shape on both parts, and the
widths of one CTA shape are ONE delivered program that the build
specialises per width (tables and proof under "Quantizer tier selection"
below). Every other row set, row width or row-strided view takes the
runtime-geometry instance of the same CTA shape (K and the row stride as
kernel arguments).

The delivery is regenerated on top of #5944 (stream-K stripe tail of the
static 2-CTA
GEMM): its sliced programs and its host dispatch are part of the
regenerated tree, and
the plan assertions it added to `tests/gemm/test_cake_mm_fp4.py` are
kept in the rewritten
test.

Host shim: the generated launchers that encode TMA descriptors set the
device once per thread and device instead of before every launch (the
per-call form delayed the following launch by 0.3-0.4 us on B200 in the
paired quantize + GEMM chain).

- **One source pair per program for both architectures.**
`csrc/cake_nvfp4_per_token/`
holds `<program>_kernel.cu` + `<program>_binding.cu` compiled for every
architecture a program serves; the few lowering lines that differ
between
SM100 and SM103 sit under `__CUDA_ARCH__` guards. The per-architecture
trees
  `csrc/cake_nvfp4_per_token/sm_100a/` and `sm_103a/` are gone.
- **Shared headers.** The PTX wrappers (`mbarrier_*`, `tcgen05_*`,
`tma_*`) and
the device helpers live once in
`cake_nvfp4_per_token_device_common.cuh`;
the launch helpers (tensor-map encode, dynamic-smem attribute, checks)
once
in `cake_nvfp4_per_token_host_common.cuh`. Bindings are thin launchers:
no
private device guard class, SM-count helper, mutex or attribute cache
per file.
- **One program per kernel body.** The 128-wide one-token-tile GEMM
program was
shipped twice (with and without the 256 B TMA L2 promotion, a host
descriptor
attribute); the dispatch rule that disables the promotion for
one-token-tile
128-wide rows now covers the two-wave 8192x28672 M=128 row on 148-SM
parts
too, so one program serves every such row. _(Kept only on the A/B
evidence
  below; see "Validation".)_
- **Quantizer with runtime K and row stride.** The row length and the
row
stride of `x` are kernel arguments; the quantizer programs are keyed by
CTA
shape (`quant:t<threads>_b<blocks per thread>_mb<min
blocks>_<dtype>[_fold][_sl]`)
instead of by `K`, so every `K % 16 == 0` runs on a registered program
and
  row-strided activations are read in place.
- **Every dispatcher tactic registered.** The validated matrix gained 37
coverage rows (`M` in {9, 12, 16} on five families, the off-matrix pair
  (K, N) = (4096, 3200) at `M` in {16, 300}, and the quantizer alone at
`K` in {2688, 4096} for `M` in {1, 16, 130, 2048, 8192} with the output
scale
  folded and not folded);
the `n16_*` swapped-orientation programs that every `M` in 9..16 used to
  raise `NotImplementedError` on are registered on both architectures.
`generated_program_available()` no longer requires an exact SM count; a
shape whose tactic has no registered program raises at preparation
naming
  the key.
- **Host without per-call overhead.** Device facts come from the cached
  `flashinfer.utils` helpers; `nvfp4_quantize_per_token` and
`mm_fp4_per_token` cache the resolved plan, FFI entry and argument order
per
shape and device and allocate only their outputs; the global-scale
scalar is
one cached device tensor per value; no `.contiguous()` copies on the hot
  path (only a non-unit stride along the row of `x` is copied).
- **File names.** One pair
`cake_nvfp4_per_token_<identity>_{kernel,binding}.cu`
per program (no per-architecture copies); the identity is still the
program's
source fingerprint — see the checklist for why a key-based name is not
in
  this change.
- **Behavioural tests** for `M` 9..16 (bf16 output; the fp16-output
cases
assert the `NotImplementedError` that names the missing `gemm:n16_*_f16`
  program, see the checklist), the off-matrix (K, N), row-strided `x`,
allocation-free repeated calls and CUDA-graph replay replace the tests
that
pinned kernel-key strings and grids. `benchmarks/bench_cake_mm_fp4.py`
times
the chain (CUPTI, cold L2) and the eager host path, optionally paired
against
  another checkout in one process.

Backend string `"cake"`, module names, JIT spec names
(`<program>_<arch>_<identity>`),
import paths and the public host API are unchanged;
`flashinfer/gemm/gemm_base.py`
and `flashinfer/quantization/*` are not touched.

## Issue checklist

| Issue step | Status |
|---|---|
| Merge SM100 / SM103 sources | delivered |
| Remove duplicate L2-promotion kernels | delivered (one program per
body; dispatch rule extended, A/B-gated) |
| Quantizer programs that differ only in the compiled-in row width |
delivered: the width is the `K_STATIC` compile-line definition of one
source per CTA shape (text + SASS proof under "One source per CTA
shape"), so the tier is two programs per input dtype instead of one per
(width, shape) |
| Shared binding helpers + PTX wrappers in one header | delivered (two
headers: device / host) |
| Cache the prepared launch per shape and device; no per-call
`torch.tensor` / allocations | delivered |
| Quantizer with runtime K and row stride | delivered |
| GEMM as few schedule templates | **not delivered**: the GEMM programs
derive their constants non-linearly from the tile shape (stage counts
from the smem / TMEM budget, cache hints inside PTX strings), so the
generator cannot fold them into one templated source yet; each
registered tactic stays one guarded source pair |
| Register every dispatcher tactic + remove the exact-SM-count
dependency | delivered for every tactic the dispatcher returns over the
validated matrix incl. the coverage rows (the 16-token
swapped-orientation programs for `M` in 9..16 are registered for bf16
output); every bf16 quantizer CTA shape the dispatch reaches over the
validated row widths has a program for contiguous activations
(enumerated by
`test_every_reachable_bf16_quantizer_shape_has_a_program`); SM-count
gate removed. **Remaining gaps (follow-ups):** (a) the fp16-output twins
of the 16-token GEMM programs (`M` in 9..16 with `out_dtype=float16`)
raise `NotImplementedError` naming the key (15 more validated rows +
re-export); (b) fp16-input quantizer programs exist for the validated
fp16 rows only (K = 7168, as in the base); other fp16 shapes name their
missing program; (c) a row-strided activation of more than one row at K
= 2688 / 4096 falls back to the runtime-geometry program of its CTA
shape, and the two shapes that only these new widths reach have no
runtime-geometry sibling in the package yet, because every contiguous
row of them takes the compiled-in instance -- the dispatcher names the
missing key
(`test_row_strided_activation_at_a_new_width_names_its_missing_program`),
and today's package has no K = 4096 program at all, so these widths are
new coverage either way. Closing (c) needs a row-strided row in the
validated matrix (or row-stride addressing in the compiled-in program)
and a re-export |
| Stable non-hash file names | **not delivered**: the exporter derives
the program name (file name, kernel symbol, module identity) from the
source fingerprint and has no hook for a logical label; naming programs
after their dispatch key needs a generator change and a full
regeneration, planned as a follow-up |
| Behavioural tests for M 9..16 and non-listed K / N | delivered |

## Size

Against `1b578de5292`: 403 files changed, +9,432 / -86,807 lines. The
generated tree goes
from one source pair per architecture and program to one pair per
program (plus two shared
headers); per-file helper duplication is gone.

| | before | after |
| --- | ---: | ---: |
| package files | 383 | 227 |
| generated `.cu` | 376 | 218 (+2 `.cuh`) |
| generated CUDA lines | 154,102 | 78,021 |
| `__device__ __forceinline__` helper copies | 1,610 | 23 |
| inline PTX statements | 9,036 | 4,593 |
| `cake_jit.py` lines | 5,203 | 3,644 |
| package Python lines | 6,702 | 5,406 |

The 109 kernel sources carry 109 distinct kernel bodies over 71
skeletons; the shared
`cake_nvfp4_per_token_{device,host}_common.cuh` headers hold what every
program repeated.

## Quantizer tier selection (per-K probe)

Why `STATIC_K = {2688, 4096, 7168}`: the row-geometry-compiled-in
instance was
timed against the runtime-K instance of the same CTA shape at `M = 1`
(no fold)
and `M = 8` (fold) for every validated row width, 5 interleaved CUPTI
rounds
(cold L2, median of the per-round medians, `ratio = runtime /
compiled-in`,
`wins` = rounds the compiled-in instance was faster). A width is in the
set only
when some row wins at least 3/5 rounds and no row loses a majority, on
both
parts. Both instances are bitwise identical (15 shapes, dense and the `M
= 1`
row-strided view, both parts).

| K | B200 M=1 ratio (wins/losses) | B200 M=8 | GB300 M=1 | GB300 M=8 |
verdict |
|---|---|---|---|---|---|
| 2688 | 1.0000 (0/0, 5 equal) | 1.0147 (5/0) | 1.0141 (5/0) | 1.0152
(5/0) | compiled-in |
| 4096 | 1.0004 (5/0) | 1.0000 (1/0, 4 equal) | 1.0137 (5/0) | 1.0147
(5/0) | compiled-in |
| 7168 | 1.0267 (5/0) | 1.0000 (0/0, 5 equal) | 1.0139 (5/0) | 1.0000
(0/0, 5 equal) | compiled-in |
| 8192 | 1.0118 (5/0) | 0.9878 (0/5) | 1.0127 (5/0) | 0.9872 (0/5) |
runtime-K |
| 16384 | 0.9785 (0/5) | 0.9681 (0/5) | 0.9775 (0/5) | 0.9778 (0/5) |
runtime-K |
| 18432 | 0.9896 (0/5) | 0.9793 (0/5) | 0.9674 (0/5) | 0.9684 (0/5) |
runtime-K |
| 28672 | 0.9722 (0/5) | 0.9735 (0/5) | 0.9524 (0/5) | 0.9626 (0/5) |
runtime-K |

Absolute times are 2.1-3.6 us per call for these rows (B200 `M=1
K=7168`:
2.400 vs 2.464 us; GB300: 2.304 vs 2.336 us).

### Row counts that take the compiled-in instance

The same probe over the larger row counts puts the whole range below
8192 rows
in the tier: `cta_config` keeps one CTA shape per width for `2 <= M <
512` (the
shape the small-row programs already use) and one more for `512 <= M <
8192`
(256 threads, L2 evict-last stores), and the compiled-in build is ahead
of the
runtime-geometry build of that shape at every validated width on both
parts.
From 8192 rows on the shape changes (128 threads, more blocks per
thread) and
the compiled-in build loses at 4096 and 7168. The dispatch therefore
uses the
compiled-in instance for contiguous row sets of fewer than 8192 tokens
at a
width in the set, and the runtime-geometry instance everywhere else (5
interleaved CUPTI rounds per row, `ratio = runtime / compiled-in`,
`wins/losses`
= rounds the compiled-in build was faster / slower):

| K | M=32 | M=130 | M=300 | M=512 | M=2048 | M=8192 (not in the tier) |
|---|---|---|---|---|---|---|
| B200 2688 | 1.0139 (5/0) | 1.0250 (5/0) | 1.0230 (5/0) | 1.0306 (5/0)
| 1.0383 (5/0) | 1.0458 (5/0) |
| B200 4096 | 1.0263 (5/0) | 1.0119 (5/0) | 1.0103 (5/0) | 1.0087 (5/0)
| 1.0229 (5/0) | 0.9940 (0/5) |
| B200 7168 | 1.0004 (4/0) | 1.0000 (tie) | 0.9997 (0/5) | 1.0002 (tie)
| 1.0317 (5/0) | 0.9753 (0/5) |
| GB300 2688 | 1.0147 (5/0) | 1.0130 (5/0) | 1.0238 (5/0) | 1.0211 (5/0)
| 1.0393 (5/0) | 1.0404 (5/0) |
| GB300 4096 | 1.0135 (5/0) | 1.0125 (5/0) | 1.0106 (5/0) | 1.0182 (5/0)
| 1.0139 (5/0) | 0.9766 (0/5) |
| GB300 7168 | 1.0125 (5/0) | 1.0000 (tie) | 1.0000 (tie) | 1.0071 (5/0)
| 1.0186 (5/0) | 0.9906 (0/5) |

The one row below 1.0 inside the range (B200, K=7168, M=300: 3.777 vs
3.776 us)
is a single CUPTI tick on a 3.8 us kernel. 2688 and 4096 keep their 1-4
% margin
at 8192 rows as well, but the range ends where the CTA shape changes so
the tier
stays two programs per input dtype: the row counts below 512 reuse the
CTA
shapes the small-row programs already have, and the `512 <= M < 8192`
range adds
one shape. The row width is a compile-line definition, not program text
(next
section).

### One source per CTA shape: `K_STATIC`

The row width is the quantizer template's `K_STATIC` parameter: the
generated
source carries it in its schedule-constant block (`#define K_STATIC`,
next to
`THREADS` and `SMEM_TOTAL`) and uses it symbolically, so the widths of
one CTA
shape are one delivered program that each build specialises on its
compile line
(`-DK_STATIC=<K>`, carried by the JIT spec name and by
`DEFINITIONS[kernel_key]`
in the generated module table). Proof, per architecture and CTA shape,
over
every width the shape serves:

- the sources of one shape are byte-identical except the `#define
K_STATIC`
  line (16/16 pairs);
- against the previous per-width sources they differ only in five lines,
each a
K-derived constant that folds back to the previous literal when
`K_STATIC` is
substituted (`num_blocks`, `padded_cols`, `sf_tile_bytes` and the two
row byte
offsets), and the runtime-geometry sources are unchanged (68/68 checks);
- the compiled SASS of each `-DK_STATIC=<K>` build is identical to the
SASS of
the previous per-width source — same instruction sequence, same register
and
shared-memory use (52/52 builds, both architectures), and the production
  (NVRTC) build matches the downstream (`nvcc`) build instruction for
  instruction.

## Generated-code audit (`slop.json`) of the delivery

The exporter's generated-code audit over the delivered tree reports 11
findings: ten
`constant_clone` groups and one `python_smell`.

| group | programs | redundant lines | what differs | classification |
| --- | ---: | ---: | --- | --- |
| quantizer CTA shapes (6 groups) | 9, 9, 7, 7, 4, 4 | 1,600 / 1,584 /
1,200 / 1,188 / 603 / 597 | `THREADS`, `__launch_bounds__`, `words[N]`,
`block_max[N]`, the unrolled trip counts | recorded class: one program
per CTA shape; the constants *are* the shape |
| static / runtime pair of one shape (2 groups) | 2, 2 | 201, 199 |
`words[8]` vs `words[16]`, `block_max[1]` vs `[2]`, trip counts | same
class, the two members of a shape |
| GEMM raster pair (2 groups) | 2, 2 | 769, 769 | the tile-index
arithmetic of the two raster orders | recorded class, unchanged |
| `python_smell` | 1 | 0 | `contiguous_copy` x2, `allocation` x6 in
`cake_backend.py` | the host path's own copies / allocations |

No finding is K-derived any more: with the width as a compile-line
definition, the per-width
clones of the previous round are gone. Against that round (same audit,
same route) the package
goes 110 -> 109 programs, 110 -> 109 distinct bodies, 66 -> 71 skeletons
and **9,844 -> 8,710
redundant lines**; the finding count rises from 9 to 11 only because the
per-shape groups split
into their static and runtime members. Two programs remain single-shape.

## Validation

**Export protocol (generator-side, 309 shapes per architecture = 160
perf + 12
correctness + 100 quantize + 37 coverage rows):** every shape passed on
both
parts — B200 (sm_100a, 309/309) and GB300 (sm_103a, 309/309): quantizer
outputs bitwise equal to FlashInfer's CuTe-DSL
per-token quantizer (fp4 codes, swizzled scales incl. padding, per-token
scales), GEMM output within `1e-2 + 1e-2 |ref| + half an ulp` of the
FP32
product of the dequantized operands, bitwise parity between the
generator's own
launchers and the FlashInfer host path, no device allocation in the
FlashInfer
submit.

Both runs report no measurement-validity warning: the fixed-count
protocol (200 warmup +
1,000 reportable calls per arm and group, no sizing pilot) ran to
completion on every row,
with each sample preceded by an unmeasured same-arm launch, state
restoration and a cold-L2
flush, and the two architectures produced the identical delivery tree.

Timing (CUPTI, cold L2, 3 counterbalanced groups x 1000 calls per arm):
FlashInfer host path vs the generator's launchers geomean 1.006x (B200)
/ 0.988x
(GB300) over all 309 rows; vs FlashInfer's CuTe-DSL per-token route on
the 260 perf +
quantize rows: 1.126x (B200) / 1.107x (GB300). The two
architectures' runs produced the identical delivery tree.

**Tests / paired A/B / SASS record:**

*SASS record (sm_103a, GB300; base `1b578de5292` vs this branch,
name-agnostic body digests over every generated kernel, one build per
program and compile-line definition set):*

| metric | value |
|---|---|
| base kernels / candidate kernels | 94 / 111 |
| distinct bodies | 90 |
| bodies identical | 62 |
| **GEMM bodies changed or lost** | **0** |
| base bodies with no candidate match | 32 (all quantizer programs) |
| candidate bodies with no base match | 49 (44 quantizer programs + 5
new 16-token GEMM programs) |

The new GEMM bodies are the 16-token tactics this change adds for M
9..16:
`gemm:n16_bf16_aF_l2256b`, `..._o2`, `gemm:n16_sk2_bf16_aF_l2256b`,
`gemm:n16_sk4_bf16_l2256b`
and `gemm:n16_k512_bf16_aF_l2256b_s3`. Every GEMM program that exists in
both registries keeps
its SASS byte for byte, including the stream-K tail programs of #5944.
The quantizer bodies all
differ by design: the width and the activation row stride are no longer
compiled into one program
per (K, shape) pair, so no quantizer body can match.

*SASS record (sm_100a, B200; same base and method):* base 94 / candidate
108 kernels, 88 distinct
bodies, 62 identical, **0 GEMM bodies changed or lost**, 32 base-only
(all quantizer) and 48 new
(44 quantizer + the four 16-token GEMM programs; GB300 adds
`gemm:n16_bf16_aF_l2256b_o2` as well).

*Tests:* 90 tests in `tests/gemm/test_cake_mm_fp4.py` +
`tests/quantization/test_cake_nvfp4_quantize.py`, all passing on both
parts (B200 / sm_100a and GB300 / sm_103a), CPU host rules and GPU
correctness together.

*Paired CUPTI A/B (base `1b578de5292` vs this branch, cold L2, 9
interleaved rounds, `benchmarks/bench_cake_mm_fp4.py --base <base
checkout>`):*

Acceptance metric per row, per architecture (every row >= 0.98,
geometric mean >= 1.00):
- quantize + GEMM chain rows: the CUPTI span of the chain callable
(first kernel start to last kernel end) under **CUDA-graph replay** —
the deployment mode of these decode-shape chains, free of host launch
cadence. The eager span of the same callable is reported as a
diagnostic: with ~15 us of host work per call against 10-30 us of
kernels the eager chain is host-bound and its span measures
launch-arrival jitter (+-5 % per row on GB300, both directions; a
5-round sweep put one quantizer row at 0.977 that 9 rounds place at
0.998 with byte-identical SASS).
- single-launch rows (quantizer alone): the CUPTI kernel time.
- host side: per-call p50 / p90 of the prepared quantize and GEMM
entries and the eager wall time per call must not regress (candidate:
~2.1x less host time than the base).

| | B200 (sm_100a) | GB300 (sm_103a) |
| --- | ---: | ---: |
| rows compared | 33 | 33 |
| gate geomean | **1.0013** | **1.0026** |
| worst row | 0.9817 `quant_k7168_m1` | 0.9903 `chain_k7168_n18432_m130`
|
| best row | 1.0164 `chain_k16384_n7168_m130` | 1.0151
`chain_k16384_n7168_m130` |
| chain rows geomean | 1.0020 | 1.0027 |
| quantizer rows geomean | 0.9939 | 1.0013 |
| quantizer kernel time geomean | 1.0167 | 1.0102 |
| GEMM kernel time geomean | 1.0019 | 0.9990 |
| eager chain span geomean | 1.0122 | 1.0035 |
| host time geomean (base / candidate) | 2.303 | 2.042 |
| rows the shipped package refuses | 18 | 18 |
| rows this branch cannot serve | 0 | 0 |
| verdict | PASS | PASS |

The 18 rows the shipped package refuses are the M = 9..16 GEMM rows
(`gemm:n16_*` is not
registered there) and the K = 2688 / 4096 quantizer rows; the branch
serves all of them. Every
comparable row is bitwise equal between the two checkouts.
`quant_k7168_m2048` -- the row where
the 5-round run on GB300 had reported 0.9767 -- settles at 1.0054 (B200)
and 0.9982 (GB300) over
9 rounds, which matches the disassembly: the compiled-in instance and
the shipped per-K clone are
the same 264 SASS instructions with the same 40 registers, 1,024 B
shared memory and grid.

A separate `quant-large` sweep over the large-row quantizer tier (7
rounds, B200) gives geomean
1.0331 with a worst row of 0.9858 and 2.951x less host time.

---------

Co-authored-by: Yingyi Huang <yyihuang@nvidia.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [fad4432](https://github.com/flashinfer-ai/flashinfer/commit/fad4432db89420ea19b5fc171aa6d58aa5628564)

- **作者**: eigen
- **时间**: 2026-10-03T21:32:35Z
- **提交信息**: refactor(cake_deepgemm_batched_gemm): one source per schedule, dispatch by schedule rule (SM100 / SM103) (#5931)

Closes #5828 (part of #5768).

## Summary

The experimental batched FP8 projection
(`flashinfer.fp8_batched_gemm.prepare_fp8_batched_gemm`,
`csrc/experimental/deepgemm_batched_gemm`) shipped twelve
per-architecture generated file pairs whose
sm_103a texts equal the sm_100a texts apart from names, a JSON catalog
keyed by exact token counts, and
bindings carrying private device guards, tensor checks and a
mutex-guarded shared-memory cache. This PR
regenerates the family from its producer:

- **One source per schedule for both architectures.** Six `*_kernel.cu`
/ `*_binding.cu` pairs replace
twenty-four files; the loader compiles each with the exact flags of the
device it runs on
(`sm100a_nvcc_flags` / `sm103a_nvcc_flags`) and puts the architecture in
the JIT spec name.
The device code is regenerated by the current producer, so it is not
instruction-identical to the files it replaces (see
"Device code" below); outputs are bitwise equal to the previous files on
every shared route.
- **Dispatch by the schedule rule, not by an exact-token table.**
`batched_gemm.route_config` selects
the schedule from the token count, the device SM count and the epilogue
exactly as the producer does;
M, the M-tile count and the grid are launch arguments. Every token count
that selects an exported
program is served (the base served ten exact token counts; this is a
superset), e.g. FP8 T = 1..32,
97..128, 481..512, 961..1024 and BF16 with alpha for every T. A token
count whose selected schedule
was never exported (the general 128x128 schedule with dynamic-FP8 or
plain BF16 output) raises
  `NotImplementedError` naming the schedule at preparation.
- **Registry in the host module** (`PROGRAMS`, `ROUTES`);
`batched_gemm_catalog.json` removed.
- **Thin bindings** on `tvm_ffi_utils.h` (`CUDADeviceGuard`, `check_*`,
one static shared-memory opt-in);
  no private classes, caches, mutexes or device-attribute queries.

Public entry points, module paths and the public signature are unchanged
(`descriptor_workspace` is
accepted and ignored: tensor maps travel by value).

## Device code

The six kernels are regenerated by the producer at its current revision
rather than copied, so their SASS differs from the
files they replace. Per-kernel diff (name-agnostic, `cuobjdump -sass`,
CUDA 13.x toolchain of the test image):

| schedule program | arch | instructions before -> after | registers
before -> after |
|---|---|---|---|
| `44b3db5dcd94945d6530` swap_ab bm16 (FP8 T<=32) | sm_100a | 2210 ->
2210 | 23 -> 26 |
| `44b3db5dcd94945d6530` swap_ab bm16 (FP8 T<=32) | sm_103a | 2210 ->
2194 | 23 -> 24 |
| `4fed225332cf21378870` n256 (FP8 T 481..512, 961..1024, 4096) |
sm_100a | 4034 -> 4034 | 75 -> 75 |
| `4fed225332cf21378870` n256 (FP8 T 481..512, 961..1024, 4096) |
sm_103a | 4034 -> 4018 | 75 -> 75 |
| `9c78b5deea1e2a3f6d18` swap_ab bm64 (FP8 T 97..128) | sm_100a | 3154
-> 3138 | 24 -> 23 |
| `9c78b5deea1e2a3f6d18` swap_ab bm64 (FP8 T 97..128) | sm_103a | 3138
-> 3138 | 24 -> 23 |
| `c1767ea2214a0b0df04b` bf16 T 97..128 | sm_100a | 2450 -> 2450 | 25 ->
24 |
| `c1767ea2214a0b0df04b` bf16 T 97..128 | sm_103a | 2450 -> 2434 | 25 ->
24 |
| `df7ac68be53c4ef83047` bf16 T<=32 | sm_100a | 1826 -> 1826 | 23 -> 26
|
| `df7ac68be53c4ef83047` bf16 T<=32 | sm_103a | 1826 -> 1810 | 23 -> 23
|
| `ed2c9a5f2dfe74719dc3` general 128x128 alpha | sm_100a | 1906 -> 1890
| 37 -> 37 |
| `ed2c9a5f2dfe74719dc3` general 128x128 alpha | sm_103a | 1906 -> 1890
| 37 -> 37 |

Three producer changes since the previous export account for every
differing instruction (the generated CUDA differs by 11-12
lines per kernel body): (1) the warp/lane carrier is now a signed int
derived from `threadIdx.x` through a warp-uniform shuffle
(previously `__shfl_sync` of the warp index plus a `%laneid` read); (2)
on sm_100a only, the shared-memory base pointer is taken
through an explicit `cvta.to.shared` and made warp-uniform (this is the
one place the two architectures now compile to a
different instruction count); (3) index arithmetic is rendered with
explicit unsigned casts and literal suffixes. Unused barrier
helpers are no longer emitted (no SASS effect). Outputs of the
regenerated kernels are bitwise equal to the previous kernels'
on every shared route on both architectures (A/B table below), and the
FP8 output equals the per-32 quantisation of the
reference BF16 result on every FP8 row.

## Validation

| gate | sm_100a (B200, 148 SMs) | sm_103a (GB300, 152 SMs) |
|---|---|---|
| per-kernel SASS diff recorded (table above) | 6 kernels, 4 same
instruction count, 2 at -16 | 6 kernels, 1 same instruction count, 5 at
-16 |
| `tests/experimental/test_fp8_batched_gemm_generated.py` | 25 passed
(51.7 s) | 25 passed (27.0 s) |
| paired CUPTI A/B base vs candidate, 10 shared routes (revised protocol
below; first-protocol readings kept in the PR history) | 10 rows, every
row >= 0.9926, geomean **0.9994** over four admissibility-controlled
passes on two GPUs (1.0005 / 1.0003 with base loaded first, 0.9980 /
0.9987 with the candidate loaded first), outputs bitwise equal 10/10;
below the 1.00 line by 0.06 %, within the 0.1-0.2 % first-loaded-module
offset measured on identical machine code on this node | 10 rows, every
row >= 0.9976, geomean **1.0009 / 1.0005** in two admissible passes on
two GPUs, outputs bitwise equal 10/10 |
| non-listed token counts (FP8 2/8/17/32/100/127/500/1000; alpha
1/17/1000) | 11 rows served and validated (exporter correctness 11/11;
A/B measured, no base counterpart) | 11 rows served and validated
(exporter correctness 11/11; A/B measured, no base counterpart) |

Line count: family 17,517 -> 6,815 lines (32 -> 19 files).

Acceptance line for the A/B: every row >= 0.98 and geomean >= 1.00 per
architecture.

**Measurement protocol (revised).** The first protocol above (10
alternating-order rounds, row-major: all rounds of one
row before the next) read 0.9987 for an identical kernel pair on both
GPUs, a second-position bias that put the geomean
readings on the protocol's floor. The A/B was therefore re-run with a
round-major schedule: every round visits every row
and both arms, the arm order rotates per slot, 40 rounds x 60 cold-L2
CUPTI launches per arm per row, same 10 rows,
same gate. Each run proves its own admissibility: (1) order balance, the
base/candidate geomean when the candidate leads
vs when it trails within +-0.0005; (2) a `base_reload` arm, the same
compiled base library loaded a second time, whose
geomean against base must be within +-0.0005 of 1.0 (protocol noise on
identical machine code). An independently rebuilt
copy of base is reported as the build-to-build variance floor (0.1-0.2 %
per kernel, not gated).

| pass | balance cand / reload | base vs reload (rows) | base vs rebuilt
base (rows) | base vs candidate geomean (worst row) | bitwise |
|---|---|---|---|---|---|
| GB300, GPU 1 | 0.9999 / 1.0004 | 0.9999 (0.9985..1.0023) | 1.0009
(0.9990..1.0034) | **1.0009 (0.9988)** | 10/10 |
| GB300, GPU 2 | 1.0003 / 1.0000 | 0.9997 (0.9977..1.0008) | 1.0002
(0.9977..1.0031) | **1.0005 (0.9976)** | 10/10 |
| B200, GPU 1, base loaded first | 1.0006 / 1.0006 | 1.0011
(0.9975..1.0082) | 1.0019 (0.9997..1.0112) | **1.0005 (0.9976)** | 10/10
|
| B200, GPU 2, base loaded first | 1.0010 / 0.9994 | 1.0006
(0.9970..1.0074) | 1.0012 (0.9971..1.0097) | **1.0003 (0.9970)** | 10/10
|
| B200, GPU 1, candidate loaded first | 0.9996 / 1.0008 | 1.0002
(0.9976..1.0025) | 0.9998 (0.9976..1.0025) | **0.9980 (0.9926)** | 10/10
|
| B200, GPU 2, candidate loaded first | 1.0000 / 0.9999 | 1.0000
(0.9963..1.0030) | 1.0003 (0.9984..1.0026) | **0.9987 (0.9941)** | 10/10
|

On the B200 node the first module loaded into the process runs 0.1-0.2 %
slower than later-loaded copies of the same
machine code (the `base_reload` arm reads 1.0011 / 1.0006 when base is
loaded first and 1.0000 / 1.0002 when it is not),
so the B200 A/B was run in both load orders and the four passes are
reported together; only the candidate-first pass on
GPU 2 is admissible under the +-0.0005 bands. GB300 shows no load-order
effect (reload 0.9999 / 0.9997).

Acceptance line as measured under the revised protocol: GB300 meets it
(every row >= 0.9976, geomean 1.0009 and 1.0005). B200 does not: every
row >= 0.9926 but the geomean over the four passes is 0.9994 (0.9987 in
the single admissible pass), 0.06-0.13 % below the line, the same
magnitude as the first-loaded-module offset on that node; the
regenerated kernels are not shown to be faster than the shipped ones on
B200. The regenerated kernels are therefore reported as
performance-neutral on B200 (bitwise-equal outputs, within the
measurement floor, not shown faster) and faster on GB300; the PR is
marked ready for review on that basis. No gate, tolerance, row or kernel
changed.


## Follow-ups (not in this PR)

- Export the general 128x128 schedule for dynamic-FP8 and plain-BF16
output so every token count is served.
- Make heads / N runtime arguments of the regenerated kernels (today
H=8, K=4096, N=1024 are compiled in).
- Programmatic dependent launch (the producer builds without it).
- Drop the ignored `descriptor_workspace` parameter once callers no
longer pass it.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Batched GEMM preparation now selects schedules based on token count,
device SM count, and epilogue, with support documented for SM100a and
SM103a.
* Preparation reports a clear error naming the schedule when no exported
schedule is available.
* **Documentation**
* Clarified that `descriptor_workspace` is accepted but ignored, and
that tensor maps are passed with each launch.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [a59e689](https://github.com/flashinfer-ai/flashinfer/commit/a59e689917808a67fd382a0ef0b9fb5d1e798441)

- **作者**: eigen
- **时间**: 2026-10-03T21:31:55Z
- **提交信息**: refactor(cake_nvfp4_svdquant): one source set, shape-rule routing, by-value tensor maps (SM100 / SM103) (#5960)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

Closes #5824 (part of #5768).

## Summary

The Cake NVFP4 SVDQuant GEMM (`mm_nvfp4_svdquant(..., backend="cake")`,
`csrc/cake_nvfp4_svdquant_gemm`)
shipped two per-architecture source trees whose sm_103a kernels equal
the sm_100a kernels apart from the
content id, two 855-line catalogs enumerating 46 exact (M, N, K, rank,
bias) routes per architecture, a
loader that scanned that table three times per call, and four bindings
that kept a process-wide
descriptor workspace (mutex, string-keyed map, blocking host-to-device
refresh). This PR regenerates the
family from its producer:

- **One source set for both architectures.** Seven `*_kernel.cu` /
`*_binding.cu` pairs replace 28
files; the loader compiles each with the exact flags of the device it
runs on (`sm100a_nvcc_flags` /
`sm103a_nvcc_flags`) and puts the target in the JIT spec name. The two
catalogs are removed; the seven
program records live in `flashinfer/jit/cake_nvfp4_svdquant.py`
(`PROGRAMS`).
- **Routing by the shape rule, resolved once per call.**
`select_cake_nvfp4_svdquant_template` applies
the rule the table encoded (rank 96 -> compact-tail schedule, rank 64
with bias -> smem-bias schedule,
K = 12288 with rank 32 -> the K-pipelined schedule, the three
single-shape schedules for their shapes,
otherwise the exact-epilogue schedule) and accepts any M >= 128 (every
tensor map carries a 128-row
box); N must be a multiple of 128, K a multiple of the schedule's K
tile, rank a multiple of 32 in
  32..128. The base served six M values only.
  Unsupported shapes raise `ValueError` naming the violated alignment.
- **Tensor maps by value.** All seven kernels take `__grid_constant__
CUtensorMap` parameters; the
descriptor workspace, its mutex, the string-keyed cache and the blocking
copy are gone, and the public
path no longer allocates a workspace per call. Two layers with different
weights capture and replay
  independently under CUDA graphs.
- **Tests.** Shapes outside the old table (M = 128, 129, 135, 191, 200,
333, 2048, 4097 with rank 32..128),
rejected shapes, and two interleaved layers under CUDA graphs (one graph
and two alternating graphs).

Public entry points and the public signature are unchanged. SM120 is not
affected (the Cake backend is
limited to SM100/SM103, as before).

## Validation

| gate | sm_100a (B200) | sm_103a (GB300) |
|---|---|---|
| SASS (regenerated structural delivery; no equivalence claim) | 7 base
vs 7 candidate kernel bodies, none identical; per-kernel table below |
same |
| `tests/gemm/test_nvfp4_svdquant_gemm.py -k "cake or
backend_arch_support"` | 24 passed, 1 skipped (CUDA 13 gate) | 24
passed, 1 skipped (CUDA 13 gate) |
| paired CUPTI A/B base vs PR, 46 catalog names (28 distinct public
calls), 3 interleaved rounds x 300 ms, cold L2, one process per shape |
28/28 public calls >= 0.98: min 0.9836
(`fixed_m129_n3072_k12288_r32_bias0`, 2-CTA schedule, 15.4 vs 15.6 us),
max 1.1140 (`autotuned_m6912_n3072_k3072_r96`), geomean 1.0275; outputs
bitwise equal to the shipped kernels on all 28; 8 off-table shapes SQNR
52.6-53.4 dB | 28/28 >= 0.98: min 0.9823 (same row, 14.2 vs 14.5 us),
max 1.1057, geomean 1.0220; bitwise equal on all 28; off-table 8/8 |
| shapes outside the old route table (M = 128, 129, 135, 191, 200, 333,
2048, 4097; SQNR > 40 dB vs the FP32 reference) | 8/8 pass | 8/8 pass |
| host path per call, M = 129 shapes (steady state and two alternating
layers): wall, CUDA allocations, host synchronizations | 9 M = 129
shapes: steady 76 -> 42 us, two alternating layers 77 -> 42 us per call
(shipped 75-123 us, PR 41-44 us); CUDA allocations per call 0 -> 0; host
synchronizations per call 0 -> 0. `fixed_m129_n3072_k12288_r32_bias1`:
shipped arm stalled in the alternating-layers loop (see note), PR arm
completed 2 of 2 (41-42 us per call, 0 syncs, 0 allocations) | steady
106 -> 49 us, alternating 102 -> 49 us (shipped 92-156 us, PR 42-50 us);
0 -> 0; 0 -> 0. Same row: shipped arm stalled, PR arm completed 2 of 2
(55-60 us per call, 0 syncs, 0 allocations) |

### Paired A/B per public call (CUPTI kernel time, cold L2, median of 3
interleaved 300 ms rounds per arm; one process per call)

| shape (catalog name; +n = further catalog names of the same call) |
schedule | B200 base us | B200 PR us | B200 base/PR | GB300 base us |
GB300 PR us | GB300 base/PR | bitwise |
|---|---|---:|---:|---:|---:|---:|---:|---|
| autotuned_m129_n3072_k3072_r32 (+2) | tactic0_n128_exact_epilogue |
11.5 | 11.1 | 1.0406 | 10.9 | 10.6 | 1.0333 | True / True |
| fixed_m129_n3072_k3072_r32_bias0 | tactic14_m128n64k128_cluster1x2 |
6.5 | 6.5 | 1.0000 | 6.0 | 6.0 | 1.0054 | True / True |
| chunk_m129_n3072_k3072_r64_t0 (+3) | tactic0_rank64_bias_smem | 10.4 |
9.9 | 1.0518 | 9.8 | 9.4 | 1.0339 | True / True |
| autotuned_m129_n3072_k3072_r96 (+4) | tactic25_rank96_persistent | 8.2
| 8.2 | 1.0000 | 7.8 | 7.8 | 1.0000 | True / True |
| cuda_graph_m129_n3072_k3072_r128 (+1) | tactic0_n128_exact_epilogue |
12.1 | 11.7 | 1.0329 | 11.5 | 11.1 | 1.0316 | True / True |
| fixed_m129_n3072_k3072_r128_bias0 | tactic0_n128_exact_epilogue | 10.9
| 10.5 | 1.0366 | 10.3 | 9.9 | 1.0388 | True / True |
| fixed_m129_n3072_k12288_r32_bias0 | tactic18_2sm_m256n128k256 | 15.4 |
15.6 | 0.9836 | 14.2 | 14.5 | 0.9823 | True / True |
| fixed_m129_n3072_k12288_r32_bias1 | tactic25_k12288_r32 | 24.1 | 23.5
| 1.0231 | 22.6 | 22.2 | 1.0173 | True / True |
| fixed_m129_n3072_k12288_r128_bias0 | tactic0_n128_exact_epilogue |
26.4 | 25.9 | 1.0173 | 24.3 | 24.0 | 1.0133 | True / True |
| fixed_m129_n3072_k12288_r128_bias1 | tactic0_n128_exact_epilogue |
27.3 | 26.8 | 1.0179 | 25.5 | 25.2 | 1.0127 | True / True |
| bench_m4096_n3072_k3072_r32 | tactic0_n128_exact_epilogue | 59.5 |
57.3 | 1.0385 | 54.6 | 53.5 | 1.0203 | True / True |
| bench_m4096_n3072_k12288_r32 | tactic25_k12288_r32 | 134.9 | 132.8 |
1.0159 | 124.7 | 123.1 | 1.0133 | True / True |
| bench_m4096_n12288_k3072_r32 | tactic0_n128_exact_epilogue | 203.0 |
199.1 | 1.0196 | 185.7 | 182.0 | 1.0202 | True / True |
| bench_m6889_n3072_k3072_r32 | tactic0_n128_exact_epilogue | 90.6 |
86.3 | 1.0501 | 83.5 | 80.5 | 1.0366 | True / True |
| bench_m6889_n3072_k12288_r32 | tactic25_k12288_r32 | 203.5 | 198.8 |
1.0237 | 189.1 | 185.5 | 1.0191 | True / True |
| bench_m6889_n12288_k3072_r32 | tactic0_n128_exact_epilogue | 332.2 |
325.5 | 1.0207 | 303.6 | 298.8 | 1.0161 | True / True |
| autotuned_m6912_n3072_k3072_r32 (+1) | tactic0_n128_exact_epilogue |
90.6 | 86.3 | 1.0497 | 83.6 | 81.0 | 1.0328 | True / True |
| chunk_m6912_n3072_k3072_r64_t0 (+3) | tactic0_rank64_bias_smem | 86.0
| 82.2 | 1.0451 | 78.7 | 76.7 | 1.0267 | True / True |
| autotuned_m6912_n3072_k3072_r96 (+4) | tactic25_rank96_compact_tail |
77.5 | 69.6 | 1.1140 | 71.0 | 64.2 | 1.1057 | True / True |
| fixed_m6912_n3072_k3072_r128_bias1 | tactic0_n128_exact_epilogue |
97.3 | 93.8 | 1.0382 | 89.6 | 87.2 | 1.0275 | True / True |
| fixed_m6912_n3072_k12288_r32_bias1 | tactic25_k12288_r32 | 203.6 |
199.0 | 1.0228 | 188.8 | 185.5 | 1.0176 | True / True |
| fixed_m6912_n3072_k12288_r128_bias1 | tactic0_n128_exact_epilogue |
239.1 | 235.3 | 1.0162 | 219.4 | 216.5 | 1.0133 | True / True |
| bench_m9216_n3072_k3072_r32 | tactic0_n128_exact_epilogue | 118.0 |
114.0 | 1.0357 | 108.6 | 106.2 | 1.0226 | True / True |
| bench_m9216_n3072_k12288_r32 | tactic25_k12288_r32 | 266.6 | 261.8 |
1.0185 | 247.6 | 243.9 | 1.0148 | True / True |
| bench_m9216_n12288_k3072_r32 | tactic0_n128_exact_epilogue | 436.6 |
432.4 | 1.0096 | 400.5 | 392.6 | 1.0201 | True / True |
| bench_m16384_n3072_k3072_r32 | tactic0_n128_exact_epilogue | 200.2 |
195.8 | 1.0227 | 183.7 | 180.9 | 1.0154 | True / True |
| bench_m16384_n3072_k12288_r32 | tactic25_k12288_r32 | 458.0 | 450.8 |
1.0160 | 426.0 | 420.8 | 1.0125 | True / True |
| bench_m16384_n12288_k3072_r32 | tactic0_n128_exact_epilogue | 758.4 |
746.0 | 1.0168 | 697.5 | 685.6 | 1.0173 | True / True |
| offtable_m128_n3072_k3072_r32_bias1 | tactic0_n128_exact_epilogue | -
| 11.3 | - | - | 10.4 | - | sqnr 53.4 dB / sqnr 53.4 dB |
| offtable_m135_n3072_k3072_r32_bias0 | tactic0_n128_exact_epilogue | -
| 9.7 | - | - | 9.1 | - | sqnr 52.6 dB / sqnr 52.6 dB |
| offtable_m333_n4096_k4096_r64_bias0 | tactic0_n128_exact_epilogue | -
| 13.2 | - | - | 12.0 | - | sqnr 52.6 dB / sqnr 52.6 dB |
| offtable_m2048_n6144_k3072_r128_bias1 | tactic0_n128_exact_epilogue |
- | 61.6 | - | - | 57.3 | - | sqnr 53.4 dB / sqnr 53.4 dB |
| offtable_m4097_n3072_k12288_r32_bias1 | tactic25_k12288_r32 | - |
133.2 | - | - | 123.3 | - | sqnr 53.4 dB / sqnr 53.4 dB |
| offtable_m200_n3072_k3072_r96_bias1 | tactic25_rank96_compact_tail | -
| 9.4 | - | - | 9.1 | - | sqnr 53.4 dB / sqnr 53.4 dB |
| offtable_m191_n3072_k3072_r64_bias1 | tactic0_rank64_bias_smem | - |
9.9 | - | - | 9.1 | - | sqnr 53.4 dB / sqnr 53.4 dB |
| offtable_m129_n4096_k3072_r96_bias0 | tactic25_rank96_compact_tail | -
| 8.9 | - | - | 8.9 | - | sqnr 52.6 dB / sqnr 52.5 dB |

Off-table shapes have no shipped route (the current path raises); they
are listed with this PR's kernel time and the SQNR of the output against
the FP32 reference.

### Note: a stall in the current descriptor-workspace path, observed
while measuring

While running the host-path A/B for `fixed_m129_n3072_k12288_r32_bias1`
(M = 129, N = 3072,
K = 12288, rank 32, bias; current route `tactic25_k12288_r32`, six
descriptor slots) alternating
with a second layer (M = 129, N = 3072, K = 3072, rank 64, bias; current
route
`tactic0_rank64_bias_smem`, seven slots), the **current**
`backend="cake"` path never completed the
sequence: after the 200-call steady-state loop and one warm alternating
pair, the 100-pair alternating
loop did not return from `torch.cuda.synchronize()` (stack: `wall_us` ->
`torch.cuda.synchronize`,
faulthandler dumps every 2 min until the 300 s row limit). It reproduced
on every attempt on both
architectures with only the current path loaded in the process (B200: 2
of 2, GB300: 2 of 2), and the
same template transition had earlier stalled long single-process
sequences at the first launch of a
new shape. With only this PR's path loaded in the process, the identical
call sequence completed on every attempt on both architectures (2 of 2
each; 24.4 / 25.6 us kernel time, 55-60 us per call alternating on GB300
and 41-42 us on B200, no host synchronizations, no allocations). The two
layers share the process-wide descriptor workspace that this PR removes
(`_get_cache_buf("cake_nvfp4_svdquant_tma_workspace")` +
`CallerTmaWorkspaceSlot`, which rewrites the
same slot addresses with `cuMemcpyHtoD` whenever the binding changes).
This is reported as an
observation with the exact call sequence; the root cause inside the
current kernels was not
established here, and the PR's descriptors-by-value design means the
sequence has no shared state
left to contend for. The row's kernel-time ratio in the table comes from
its completed CUPTI rounds (1.0231 on B200, 1.0173 on GB300,
bitwise-equal outputs);
its host-path cell for the current path is "stalled" because that arm
never finished the measurement.

### SASS per kernel (base at 426d028e vs this PR; `cuobjdump -sass` /
`-res-usage`)

Registers and static shared memory are unchanged for every program on
both architectures; instruction
counts drop. The deltas are the by-value tensor maps (the pointer-ABI
programs lose the descriptor
pointer loads `LDCU.64`, the descriptor cache maintenance
`CCTL.E.C.LDCU.IV.DEEP` / `UTMACCTL.IV` /
`UTMACMDFLUSH` and their `DEPBAR`s, and gain uniform address arithmetic
`UIADD3`) and the current
generator's barrier-wait lowering (fewer `SYNCS.PHASECHK.TRANS64` /
`NANOSLEEP.SYNCS` pairs; uniform
`USEL` / `UISETP` selects in the cluster program). Performance is gated
by the paired A/B below.

| program | arch | instructions base -> PR | REG | static smem | main
opcode deltas |
|---|---|---:|---:|---:|---|
| exact epilogue (tactic0_n128) | sm_100a / sm_103a | 1208 -> 1184 /
1176 | 64 | 1024 | LDCU.64 -17, CCTL/UTMACCTL/UTMACMDFLUSH -7 each,
DEPBAR -7, SYNCS.PHASECHK -5, UIADD3(.X) +32 |
| rank-64 bias in smem (tactic0_rank64_bias_smem) | both | 1024 -> 992 |
78 | 1024 | LDCU.64 -18, CCTL/UTMACCTL/UTMACMDFLUSH -7 each, NOP -12,
SYNCS.PHASECHK -5, UIADD3(.X) +32 |
| K = 12288, rank 32 (tactic25_k12288_r32) | both | 696 -> 664 / 656 |
32 | 1024 | LDCU.64 -17, CCTL/UTMACCTL/UTMACMDFLUSH -6 each, DEPBAR -6,
SYNCS.PHASECHK -5, UIADD3(.X) +22 |
| rank 96 compact tail (tactic25_rank96_compact_tail) | both | 1056 ->
1016 | 70 | 1024 | LDCU.64 -23, CCTL/UTMACCTL/UTMACMDFLUSH -9 each,
DEPBAR -9, SYNCS.PHASECHK -5, UIADD3(.X) +40 |
| cluster 1x2, N tile 64 (tactic14) | both | 880 -> 832 | 80 | 1024 |
SYNCS.PHASECHK -20, NANOSLEEP -20, SEL -25 / USEL +25, ISETP -12 /
UISETP +12 |
| 2-CTA M256 (tactic18) | both | 1032 -> 992 / 1008 | 72 | 1024 |
SYNCS.PHASECHK -15, NANOSLEEP -15, MOV -14, IMAD.U32 -11, LOP3 +10 |
| rank 96 persistent (tactic25_rank96_persistent) | both | 1272 -> 1216
| 78 | 1024 | SYNCS.PHASECHK -23, NANOSLEEP -23, IMAD.U32 -25, IMAD.MOV
+10, LOP3 +9 |

Line count: family sources + catalogs + loader 26,761 -> 9,085 (14
generated `.cu` = 8,563 lines, loader 522; 28 per-architecture sources
and two 855-line catalogs removed; `gemm_svdquant.py` -20 lines; tests
+125); `git diff --shortstat`: 33 files changed, 1,810 insertions,
19,381 deletions.

Measurement plan of the generated-program export (source arm = the
producer's dispatcher, export arm =
`mm_nvfp4_svdquant(backend="cake")`, same tensors, CUPTI, cold L2, three
counterbalanced groups): fixed
400 warmup + 4000 reportable samples per arm per group; order-dependent
disagreement tolerance 5 %.
The first full runs used 1000 samples per arm and a 2 % tolerance; one
~11 us row per architecture
(`fixed_m129_n3072_k3072_r128_bias1` on GB300: 0.0226 at 11.200 vs
11.168 us, one 32 ns CUPTI tick;
`cuda_graph_m129_n3072_k3072_r128` on B200: 0.0202 at 11.072 vs 11.072
us) failed that tolerance with
ratio 1.000-1.003 and zero endpoint drift. Only the sampling plan
changed; the generated files, the
source/export ratio floor (0.97) and the paired A/B gate (every row >=
0.98, geomean >= 1.00 per
architecture) are unchanged.

## Follow-ups (not in this PR)

- M < 128 needs a schedule variant with a 64- or 32-row tensor-map box;
the shape rule rejects it today.
- Programmatic dependent launch for the six non-persistent schedules
(the producer builds them without it).
- A Cake row set in `benchmarks/bench_nvfp4_svdquant_gemm.py`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added shape-based selection among optimized NVFP4 SVD-quantized GEMM
kernels for supported NVIDIA GPUs, with improved support for varied
ranks and bias settings.
* Removed the need to provide a separate workspace when running the Cake
backend.

* **Bug Fixes**
* Improved handling of CUDA device selection and tensor validation
during kernel execution.

* **Tests**
* Added checks for numerical results across varied input shapes and
ranks, unsupported shapes, and CUDA Graph replay.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [f03ffdc](https://github.com/flashinfer-ai/flashinfer/commit/f03ffdcfc5f7c394c2338d3a7d3e29596bbe9c8b)

- **作者**: eigen
- **时间**: 2026-10-03T21:30:38Z
- **提交信息**: refactor(cake_mxfp8_megamoe_ep16): one fused source behind a return-protocol flag, admit SM100 (SM100 / SM103) (#5922)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

## 📌 Description

Deslop of the experimental `cake_mxfp8_megamoe_ep16` family (umbrella
#5768). The family shipped the same
two-kernel EP16 forward twice (CUDA and CuTe DSL) and, inside each
backend, two near-identical fused kernels
that differ only in the return-rendezvous protocol selected by the token
count. This PR keeps the compiled code
unchanged and removes the duplication at the source level:

- **One fused source per backend behind a compile-time flag.** CUDA:
`cake_mxfp8_megamoe_ep16_fused_kernel.cu`
holds the shared helpers once and includes
`cake_mxfp8_megamoe_ep16_fused_body.cuh` twice, with
`CAKE_MEGAMOE_RETURN_ALL_CTA` 0 (CTA-0 return coordinator, 16 and 64
tokens per rank) and 1 (all-CTA
protocol, 32 tokens). Both kernel symbols, the binding and its token
selector are unchanged. CuTe DSL: one
`cake_mxfp8_megamoe_ep16_fused.py` with `return_all_cta` as a
`cutlass.Constexpr` kernel parameter and
`compile_program(return_all_cta, arch)`. Preprocessing / trace-time
evaluation of each flag value reproduces
  the previously shipped text exactly.
- **SM100 admitted from the same source.** The device text has no
`__CUDA_ARCH__` dependence and uses only
instructions shared by SM100 and SM103 (`tcgen05.mma … kind::f16`, TMA,
mbarriers, clusters). The loader
builds one exact-architecture module per admitted capability that is
also a FlashInfer build target
(`FLASHINFER_CUDA_ARCH_LIST` or the visible devices); the backend
accepts compute capability 10.0 and 10.3.
- **Architecture-neutral generated paths** under the package `csrc/`
tree (CuTe sources beside the CUDA
closure); the manifest lists sources and launch facts and is no longer
digest-verified at import.
- Tests: loader target selection from `FLASHINFER_CUDA_ARCH_LIST`, exact
per-capability JIT spec, CuTe
`compile_program` signature and guard structure; the 16-rank test
accepts SM100 and SM103.

Family size: 42,591 → 23,774 lines (−18,817). Public API, module names,
backend strings and import paths are
unchanged. `examples/experimental/cake_mxfp8_megamoe_ep16.py` is
untouched.

Not in this PR (recorded on #5822): moving the generated sources under
the top-level `csrc/` (needs the
`pyproject.toml` package-data line owned by open PRs), sharing the top-k
reducer with `cake_megamoe_topk_reduce`
(owned by #5789), and the backend choice (CUDA vs CuTe), which is a
maintainer decision posted on the issue.

## 🔍 Related Issues

Closes #5822. Umbrella #5768.

## Validation

Base for every comparison: `426d028e18a270b60a1ac72306b29754bf087c67`
(the tree this PR branches from).

- **CUDA backend, SM103 — compiled code unchanged.** Both JIT modules
(base `cake_mxfp8_megamoe_ep16_sm103a_…` and this
PR's `cake_mxfp8_megamoe_ep16_sm_103a`) were built with
`FLASHINFER_CUDA_ARCH_LIST=10.3a` and compared per kernel symbol
after normalising addresses: 4 of 4 kernels equivalent (two fused
variants, top-k reducer, TMA descriptor upload), 8,584
SASS instruction lines on each side, no kernel missing or introduced.
The result is identical on an aarch64 (GB300) and
  an x86_64 (B200) build host.
- **SM100 admission — compile-only.** `FLASHINFER_CUDA_ARCH_LIST="10.0a
10.3a"` on the x86_64 host: the loader exposes
capabilities `(10, 0)` and `(10, 3)`;
`gen_cake_mxfp8_megamoe_ep16_module((10, 0))` builds
`cake_mxfp8_megamoe_ep16_sm_100a`
(nvcc 9.6 s, `compute_100a` flags, embedded arch `sm_100a` only) with
the same shape as the SM103 build: fused kernels
4,096 SASS instructions each, 80 registers, 1,024 B static smem, 32 B
stack, no local memory; reducer 168 instructions /
  40 registers; descriptor upload 216 instructions / 32 registers.
- **CuTe DSL backend, SM103 — per-variant SASS compare.** On a GB300
node, the base modules (`kernels/fused_cta0.py`,
`kernels/fused_all_ctas.py`, `kernels/topk_reduce.py`) and this PR's
`compile_program(False, "sm_103a")`,
`compile_program(True, "sm_103a")` and the reducer were compiled through
the FlashInfer CuTe JIT path and the cubins
disassembled (cuobjdump 13.3 + nvdisasm 13.4, rc 0 on every input):
fused CTA-0 variant 4,096 instructions, fused all-CTA
variant 4,096, reducer 120 — byte-identical normalised SASS per variant
between base and PR. `compile_program(…, "sm_100a")`
compiles for all three (fused 4,096 / reducer 120 instructions;
compile-only, no SM100 CuTe run).
- **Tests.** `tests/experimental/test_cake_mxfp8_megamoe_ep16.py -k "not
sparse_reference"`: 94 passed, 3 deselected on
both hosts (base: 89 passed, 3 deselected; the new tests cover loader
target selection, exact per-capability JIT specs and
the CuTe `compile_program` signature). `pre-commit run --all-files`
clean on the changed files.

The 16-GPU EP16 correctness test
(`tests/experimental/test_cake_mxfp8_megamoe_ep16.py -k
sparse_reference` under
`torchrun --nproc-per-node=16`) was not run for this PR: no 16× GB300 or
16× B200 allocation was available. Could a
maintainer with EP16 access run it on GB300 and, for the newly admitted
target, on 16× B200 with
`FLASHINFER_CUDA_ARCH_LIST=10.0a` before merge?

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## Reviewer Notes

The guarded body header and the CuTe constexpr guards are the only
textual changes to the kernels; every
flag value expands to the previously shipped source, and the compiled
kernels are compared per symbol against
the base tree (see Validation).

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added support for SM100 devices alongside SM103 for the Cake MXFP8
MegaMoE EP16 backend.
* Added architecture-specific kernel compilation and loading for both
supported device types.
* **Documentation**
* Clarified supported devices and testing status: correctness and
performance were measured on SM103; SM100 is compile-proven, but its
16-rank test has not been run.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [44995e0](https://github.com/flashinfer-ai/flashinfer/commit/44995e0197ea90c76eae342c47c79fbae30c2c43)

- **作者**: eigen
- **时间**: 2026-10-03T21:28:04Z
- **提交信息**: refactor(cake_mamba_ssd_combined): one source per kernel, one host launcher, table-driven loader (SM100 / SM103) (#5924)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

Closes #5821

## What changed

The Cake SSDCombined backend shipped 49.5K generated lines under
`csrc/cake_mamba_ssd_combined/generated`, most of them copies:

- **Architecture copies.** All 10 `device/sm_103a/*.cu` files were
byte-identical to `device/sm_100a/*.cu` and the 9 host pairs differed
only in a namespace hash. The device sources now live once under
`generated/device/` and the loader compiles the shared file for the
device's architecture (`-arch=sm_100a` or `-arch=sm_103a`). The device
sources are unchanged apart from the added license header; no kernel
text changed.
- **Eight program hosts (841 lines each)** differed in seven values
(preprocess module/kernel/block, scan module/kernel, state dtype code,
dynamic SMEM bytes). They are replaced by one launcher,
`generated/host/mamba_ssd_combined_sequence.cpp`, whose `CAKE_SSD_*`
placeholders the Python loader fills from a program table. Substituting
each program's values reproduces its former host byte for byte
(namespace hash aside).
- **Dead code.** The unused `factorized_persistent_segment_preprocess`
host translation unit is removed.
- **`source_catalog.json` (9.8K lines)** is replaced by the program
table in `flashinfer/mamba/cake_ssd_combined.py`. Stage arguments are
bound through a fixed positional order instead of interpreting a JSON
argument plan on every call, and no source hash is re-verified at load
time.
- **Host path.** Device capability and SM count are cached per device
index, and programs are compiled once per architecture instead of once
per GPU index. The functional API's per-stream runner cache in
`flashinfer/mamba/ssd_combined.py` is bounded
(`functools.lru_cache(maxsize=64)` instead of an unbounded
`functools.cache`); this one-line change is the only edit outside the
`cake_ssd_combined` files. `SSDCombined`, `ssd_combined_fwd` and the
`flashinfer.mamba.cake_ssd_combined` import path are unchanged.
- Tests that asserted the catalog inventory and the JSON launch ABI are
replaced by behavioural tests of the program table, launcher rendering,
argument order and the per-architecture loader.

Generated lines: 49,532 (39 files) -> 13,791 (11 files: device 12,937 +
host 854, including 4 header lines each); net diff +501 / -36,396 over
42 files.

## Not in this PR (follow-ups on the issue)

- Templating the state dtype (bf16/f16 scan kernels differ in three
lines) and the kernel ABI changes (unused `x`/`B_tensor`/`C` parameters,
stride-aware coefficient loads, token-major output, a prefix route for
any `nheads >= 8 * ngroups`) require regenerating the kernels; they are
recorded on #5821 with the reason.

## Validation

- SASS equivalence per architecture (sm_100a, sm_103a): the 20 candidate
kernels (10 per architecture) have exactly the 10 distinct SASS bodies
per architecture of the base's 40 kernels, nothing missing or
introduced; compiling each shipped source with the loader's own `nvcc
-cubin` command gives identical SASS digests base vs. candidate for all
20 (arch, file) pairs.
- `tests/mamba/test_cake_ssd_combined.py`: B200 141 passed, 2 skipped
(the two-device tests; the step had one GPU); GB300 143 passed.
- Paired CUPTI A/B against the base tree on the same GPU, interleaved
rounds (44 rows: 28 contract/benchmark shapes, 12 test-matrix shapes, 4
Nemotron-H H128/G8 deployment rows), bitwise-identical outputs and final
states on every row; GPU time ratio base/candidate: B200 min 0.981
(`perf_varlen_1x1`, 59 us row) geomean 1.010; GB300 min 0.991 geomean
1.011 (three varlen rows that compute the sequence cumsum inside the
call measure 1.13-1.14; the remaining 41 rows are within 0.991-1.009).
Host path (per-call wall time, 3 rows): GB300 75.6-80.7 us -> 58.0-64.4
us, allocations per call unchanged (2); B200 55.8-56.7 us -> 39.8-40.4
us, allocations per call unchanged (2).

## Test paths

`tests/mamba/test_cake_ssd_combined.py`

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [e6628b8](https://github.com/flashinfer-ai/flashinfer/commit/e6628b8c5d6df67519b87565922b8ed58e055777)

- **作者**: eigen
- **时间**: 2026-10-03T21:21:39Z
- **提交信息**: refactor(cake_fused_norm_combine): regenerate as one source per variant (#5874)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

Closes #5773

## Summary

Regenerates `csrc/cake_fused_norm_combine` (Cake-generated fused
residual-add + two-track
RMSNorm + eight-peer BF16 combine, SM100 / SM103) from its producer with
the per-architecture
duplication, the hand-rolled binding helpers and the generated loader
metadata removed. The
three kernels compute exactly what they computed before and compile to
the same instructions on
both architectures (see Validation); the launch-path changes are
measured.

## What changed

- **One source per variant, shared by SM100 and SM103.** The three
kernels
(`parallel_lamport` for T < 256, `owner_lamport` for T >= 256, the
persistent lag-2 pipelined
owner reduce for T >= 1024) now live once under
`csrc/cake_fused_norm_combine/`; the only
architecture-dependent statement (the dynamic shared-memory base) is
emitted under an exact
`__CUDA_ARCH__ == 1000` guard. The `sm_100a/` and `sm_103a/` trees (12
files) are deleted. Each
program is compiled once into a fatbin for every supported build target
(`FLASHINFER_CUDA_ARCH_LIST` when set, otherwise the visible devices;
compute capabilities 10.0
  and 10.3).
- **Thin launchers on `tvm_ffi_utils.h`.** Every binding uses
`ffi::CUDADeviceGuard`, `get_stream`
and the target's tensor checks. The private device-guard class, the
atomic SM-count cache, the
never-called `CheckCurrentCudaDevice` / `CheckDenseLeadingFold` helpers
and the unused
`<mutex>` / `<unordered_map>` / `<atomic>` / `<string>` / `<vector>`
includes are gone.
- **Plain PDL launches.** The kernels were launched as 1x1x1 clusters
with a spread scheduling
policy, mirroring the customer kernel they replaced; none of them uses a
cluster. The cluster
dimension and scheduling-policy attributes are dropped from the bindings
and the unused
cluster-id / cluster-rank prologue from the kernels (the only
device-text change in this PR; the
compiler had already eliminated that dead read, so the SASS is unchanged
— see Validation).
- **Readable poll conditions.** The Lamport poll loops' `while (...)`
conditions are written
four sentinel terms per line instead of one 7.9 KB line of 128-464
terms. Whitespace only: the
  expressions are unchanged, so the device code is unchanged.
- **Persistent grid sized from the device.** The persistent kernel's
grid was fixed by a recorded
capacity (4 CTAs per SM on exactly 148 SMs) and every other SM count
silently fell back to the
one-CTA-per-token kernel. The module now exports
`max_active_blocks_per_sm` (one
`cudaOccupancyMaxActiveBlocksPerMultiprocessor` on the compiled kernel),
the loader caches the
answer per device and launches `min(tokens, largest odd grid <=
capacity)` CTAs on any SM100 /
SM103 device. The recorded capacity stays as a receipt that the
eight-GPU test checks against
  the live answer.
- **Loader.** `flashinfer/jit/cake_fused_norm_combine.py` is a three-row
variant table (`module`,
`sources`, `kernel_symbol`, `block`, `dynamic_smem_bytes`, `grid_rule`)
plus the two dispatch
boundaries; compute capability and SM count are queried once per device;
the launcher is called
positionally (no per-call argument-plan interpretation); the per-file
SHA-256 check at import is
  removed; build targets come from `CompilationContext`.
- **Tests.** The two tests that asserted generated structure (module
inventory, `-gencode` flags
per module) are removed; the dispatch, grid-rule, build-target scope,
workspace-layout and
argument-validation tests stay, and the eight-GPU test additionally
checks the occupancy
  receipt.

Net: 6,340 -> 3,521 lines (-2,819, -44.5 %), 15 -> 10 files (12 -> 7
`.cu`, including the 60-line occupancy query).

## Validation

**Device code.** The arch merge, thin launchers, loader and
poll-condition formatting leave the
kernels' device text unchanged; the one intended device-code change is
the plain PDL launch
(dropping the forced unit-cluster launch removes the kernels'
`%cluster_ctarank` read). SASS of
the regenerated build vs the previous per-architecture files, kernel
symbol normalised, compiled
with the repository's JIT flags (the base ships one module per kernel
and architecture, the
regenerated build one module per kernel with both cubins, so bodies are
paired per architecture):

| program | sm_100a | sm_103a |
|---|---|---|
| `parallel_lamport` | identical (1,481 instructions) | identical
(1,481) |
| `owner_lamport` | identical (1,425) | identical (1,425) |
| `owner_lamport_pipelined` | identical (3,441) | identical (3,441) |

All six bodies are identical after symbol normalisation (no instruction
added or removed; the
dropped `%cluster_ctarank` read was already dead code to the compiler),
base 6 kernels = regenerated
6 kernels, 3 distinct bodies per architecture on both sides.

**Numerical tests.** `pytest
tests/comm/test_cake_fused_norm_combine.py`: 8xB200 23 passed and
8xB300 23 passed, each including the eight-rank distributed test at T =
1, 8, 64, 256, 1024, 2048
against the independent PyTorch reference and the occupancy-receipt
check. The paired measurement
below additionally runs all six token counts through eight NCCL ranks on
both nodes against the same
PyTorch reference, with bitwise agreement between the shipped and the
regenerated kernels.

**Performance.** Paired CUPTI measurement per shape on the same eight
GPUs (three interleaved
groups, rank-critical samples), every row `before/after >= 0.97` (the
floor this family's
export already uses):

| tokens | 8xB200 before (us) | after (us) | ratio | 8xB300 before (us)
| after (us) | ratio |
|---|---|---|---|---|---|---|
| 1 | 32.033 | 32.096 | 0.9980 | 38.177 | 38.304 | 0.9967 |
| 8 | 32.575 | 32.704 | 0.9961 | 37.344 | 37.345 | 1.0000 |
| 64 | 33.503 | 33.376 | 1.0038 | 37.376 | 37.313 | 1.0017 |
| 256 | 31.840 | 31.744 | 1.0030 | 37.633 | 37.441 | 1.0051 |
| 1024 | 33.440 | 33.280 | 1.0048 | 37.312 | 37.057 | 1.0069 |
| 2048 | 51.392 | 51.872 | 0.9907 | 52.800 | 53.921 | 0.9792 |

"before" launches the shipped kernels through their production
dispatcher (the same device code, see
the equivalence table above); "after" is the regenerated FlashInfer
entry point. 8xB200 geomean 0.9994,
min 0.9907; 8xB300 geomean 0.9982, min 0.9792 (tokens 2048). Against the
unchanged customer kernel (fused
residual-add + RMSNorm + one-shot combine) on the same nodes: 33.664 /
32.863 / 34.208 us at 1 / 8 / 64 tokens vs
32.096 / 32.704 / 33.376 us after on 8xB200 (1.049 / 1.005 / 1.025),
39.968 / 37.920 / 38.273 vs
38.304 / 37.345 / 37.313 us on 8xB300 (1.043 / 1.015 / 1.026); that
kernel does not resolve at 1024 / 2048 tokens, and the 256-token row is
measured without it because the interleaved order gives the two launches
different predecessors
(the owner-Lamport collective runs ~17 % faster on a rank right after
the customer kernel's full barrier).

Per-call launch count unchanged (one kernel); per-call host device
queries 3 -> 0 (cached).

`pre-commit` clean (`--all-files`, mypy included).

**Revision 2 (typing fix).** The first revision failed the `pre-commit`
workflow's mypy hook on
`flashinfer/jit/cake_fused_norm_combine.py`: `spec()` built the
per-source nvcc flag table as a
`dict[Path, list[str]]` while `gen_jit_spec` declares
`extra_cuda_cflags_by_source` as
`Mapping[str | Path, list[str]]`, and `Mapping` is invariant in its key
type. The loader now declares
`by_source: Optional[dict[str | Path, list[str]]]` (annotation only, no
behaviour change); the fix was made in
the generator template and the family re-rendered. Every other delivered
file is byte-identical to the
measured revision (per-file SHA-256 against the measured delivery: 10
identical, 1 differing = the loader,
whose unified diff is the annotation hunk), so the SASS, test and
performance results above stand;
`tests/comm/test_cake_fused_norm_combine.py` was re-run on the
re-rendered tree (22 passed, 1 skipped on a one-GPU node: the eight-GPU
distributed test self-skips there, the other 22 are host-only; the
8xB200 / 8xB300 results above come from the measured revision, whose
kernels, launchers, host module and test are byte-identical).

## Not in this PR (follow-ups)

- Gating the remaining architecture-independent prologue (tensor-map ABI
declarations,
`<cuda_fp8.h>`) that the generator emits into every kernel; about 12
lines per kernel.
- Reusing the existing Lamport IPC workspace allocator
  (`trtllm_create_ipc_workspace_for_all_reduce_fusion`) instead of
`cake_fused_norm_combine_create_workspace`: the two allocate the same `3
* world_size + 1`
pointer table, control words and triple-buffered negative-zero regions,
but sharing the
allocator changes the public workspace type and destroy path. Maintainer
input welcome.
- Runtime token strides: addressing is dense row-major inside the
kernels, so non-contiguous
inputs are still rejected (in Python and in the binding); accepting a
row stride needs a
  kernel ABI change.
- World size and hidden size as template parameters, and folding the
per-token owner reduce
  into the persistent kernel.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Fused normalization and combine operations support compatible SM100
and SM103 devices included in the build targets.
* Kernel variants are selected based on token count, with distinct
options for smaller workloads and larger, pipelined workloads.
* **Improvements**
  * Launch sizing now accounts for device execution capacity.
* Device compatibility and launch-capacity checks provide clearer errors
when requirements are not met.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [8e632d9](https://github.com/flashinfer-ai/flashinfer/commit/8e632d98aefc8c5713b1657e20c59bfcf54cb652)

- **作者**: eigen
- **时间**: 2026-10-03T21:21:01Z
- **提交信息**: refactor(cake_nvfp4_attention): regenerate without dead code and accept strided inputs (#5866)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

Closes #5781

## Summary

Regenerates `flashinfer/experimental/nvfp4_attention` (Cake-generated
NVFP4 attention, SM103)
from its producer with the unused generated code dropped, the host
binding reduced to a thin
launcher, and the Python preparation step moved off most of its eager
work. The attention
kernel is the same program regenerated with current codegen: same
instruction count and the same
grid-dependency and asynchronous-barrier structure, with a documented
idiom-level SASS difference
(see Validation); the delivery layout, the host binding and the
preparation path change.

## What changed

- **Generated kernel.** The 71 device helpers the kernel never
referenced (640 lines) are no
longer emitted. The kernel lives once under `csrc/cake_nvfp4_attention/`
(no `sm_103a/`
tree); the JIT loader compiles it with the exact flag set of the device
and keys the cached
  library by `<program>_<arch>`.
- **Thin launcher binding.** `ffi::CUDADeviceGuard`, `get_stream` and
the target's tensor
checks from `tvm_ffi_utils.h`; the private device-guard class, the
never-called SM-count
helper, the per-launch `cudaFuncSetAttribute` behind a mutex and map,
and the redundant
current-device check are gone. The dynamic shared-memory opt-in is set
once with the kernel
  handle.
- **Registry.** `cake_jit.py` carries one `PROGRAM` record (sources,
compile flags, argument
plan) instead of a `MODULES` literal with an unchecked `closure_sha256`.
- **Preparation path (`cake_backend.py`).**
- `q`, `k`, `v` may have any strides; the quantizer reads them in place
(an `[B,S,H,128]`
buffer viewed as `[B,H,S,128]` no longer costs four transpose copies).
`out` stays a
    contiguous `[B,H,S,128]` tensor (dense 2-D TMA view).
- Block scales come from one `inf`-norm reduction (no fp32 copy of the
input); E2M1 codes use
`int32` bucket indices; the threshold table and the device capability /
SM count are cached
    per device instead of being rebuilt or queried on every call.
- The transposed `V` operand is written directly in its packed layout:
no BF16
`transpose().contiguous()` copy of `V` (537 MB on the `(8, 32, 8192)`
row) and no fp32
    temporaries of `V^T`.
- The packed operands are byte-identical to the previous
implementation's (see Validation).
- **Public API.** `flashinfer.prefill.prepare_nvfp4_attention` no longer
takes `causal=`, which
  could only raise; the route is noncausal, `S % 512 == 0`, SM103.
- **Tests and benchmark.**
`tests/experimental/test_cake_nvfp4_attention.py` keeps the three
validated shapes and determinism, and adds: strided inputs produce the
contiguous result bit
for bit; the packing equals the previous eager implementation (kept
verbatim in the test as
the oracle) on CPU and CUDA for inputs seeded with zeros, exact
thresholds, saturated
  magnitudes and infinities; stride independence of the packing. New
`benchmarks/bench_cake_nvfp4_attention.py` reports attention time
(CUPTI, cold L2) and the
preparation step's host time, launch count, host-to-device copies and
peak memory per row. The
peak-memory column is the maximum over the benchmark's repeats, so
repeats that observe different
  peaks still print one number (review follow-up).

Net: 3,479 -> 2,651 lines in the family (-828), plus +176 lines of tests
and a 153-line benchmark.

## Validation

**Device code.** The regenerated `sm_103a` kernel is compared with the
previous one by `cuobjdump -sass`
after normalising the kernel symbol (both compiled with the repository's
JIT flags). It is **not
byte-identical**, for two reasons that are both understood:

- The first regeneration had no `griddepcontrol.wait` while its binding
set the programmatic-dependent-launch
attribute: the producer on Cake main lacked the wait that the original
#5283 build carried. The wait is
restored in the producer at its original position (after barrier/TMEM
setup, before the warp-role dispatch),
  and the final kernel carries it (`ACQBULK` 1 on both sides).
- The remainder is codegen drift since the original build: warp/lane
index idiom, cast placement in address
arithmetic and the shared-memory descriptor union. Both kernels have
2,553 instructions; the opcode histogram
differs in 16 opcode classes with a net count of 0 (`IADD3` -1,
`LOP3.LUT` +1, `MOV` +1, `NOP` +4, `S2R` -1,
`SHF.L.U32` +2, `UIADD3` -2, `UISETP.GT.AND` +3, `UISETP.GT.U32.AND` -1,
`ULEA` +1, `ULEA.HI` +1, `ULOP3.LUT`
-6, `UMOV` +4, `USHF.L.U32` -5, `USHF.R.S32.HI` +2, `USHF.R.U32.HI` -3),
i.e. uniform-datapath address and
predicate idioms only; the grid-dependency and asynchronous-barrier
opcodes are identical (`ACQBULK` 1,
`CGAERRBAR` 3, `DEPBAR.LE` 6). The normalised listings differ in 1,318
of 5,108 lines at equal instruction
count, consistent with register assignment and scheduling following the
changed idioms.

| program | sm_103a |
|---|---|
| `cake_nvfp4_attention` | regenerated with current codegen: 2,553
instructions on both sides, opcode histogram differs in 16 classes (net
0), PDL/async-barrier opcodes identical; behaviour and performance shown
by the tests, bitwise output parity and the paired benchmark below |

**Packed operands.** All seven packed tensors (`Q`, `K`, `Vt`, `SFQ`,
`SFK`, `SFVtLo`,
`SFVtHi`) of the new preparation equal the previous implementation's
byte for byte on every
validated shape (3/3), and the regenerated program's output equals the
producer's output
bit for bit on the same operands (3/3).

**Tests.** `pytest tests/experimental/test_cake_nvfp4_attention.py` on a
B300: passed (exit 0; the three validated shapes with determinism,
strided inputs bitwise equal to contiguous, the packing oracle and
stride-independence on CPU and CUDA).

**Performance.** Same B300 (B300 SXM6), paired runs in both orders
(base, candidate, candidate, base;
first block quoted) of `benchmarks/bench_cake_nvfp4_attention.py` on the
base and this branch. The attention
kernel's time is unchanged within noise (ratios 1.0007-1.0011, the same
in the second block); the preparation
step launches fewer kernels, copies nothing host to device and holds
less than half the peak memory:

| row | attention before (ms) | after (ms) | ratio | TFLOPS before ->
after | prepare launches before -> after | H2D copies | prepare peak MB
| prepare host ms |
|---|---|---|---|---|---|---|---|---|
| `b4_h8_s4096` | 0.28309 | 0.28278 | 1.0011 | 971 -> 972 | 74 -> 46 | 3
-> 0 | 414 -> 188 | 3.85 -> 3.26 |
| `b1_h8_s32768` | 3.54522 | 3.54284 | 1.0007 | 1241 -> 1241 | 74 -> 46
| 3 -> 0 | 828 -> 375 | 3.63 -> 3.12 |
| `b8_h32_s8192` | 7.24338 | 7.23803 | 1.0007 | 1214 -> 1215 | 74 -> 46
| 3 -> 0 | 6627 -> 3003 | 24.67 -> 19.14 |

The producer's own serving route (the same kernel launched by its
production module, before and after it
gained the programmatic-dependent-launch attribute and the
grid-dependency wait) measured identical medians on
the same rows (0.1179 / 0.1178 ms, 1.4764 / 1.4767 ms and 3.0148 /
3.0148 ms; p10-p90 overlap on every row),
and the export runner's paired source/export timing gave 1.000271x,
1.000021x and 1.000000x on the three rows
(geomean 1.000097x) with every correctness gate passing and an
allocation-free launch.

`pre-commit` clean.

## Not in this PR (follow-ups)

- A fused NVFP4 quantize + scale-pack kernel that writes the MMA operand
layouts directly
(removes the remaining preparation launches and the byte-wise `V^T`
scatter), bit-exact with
  the packing validated here.
- A strided (3-D/4-D) `out` descriptor so NHD outputs work without
copies; caching the encoded
tensor maps across launches; folding the eight per-buffer tensor-map
encoders of the binding
  into one parametrized helper (generator change); `causal` support.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

- **New Features**
- NVFP4 attention preparation now accepts Q, K, and V tensors with
arbitrary strides, including non-contiguous views.
  - Added helpers for quantizing and packing NVFP4 attention inputs.
- **Updates**
- Output tensors must remain contiguous, and sequence lengths must be
positive multiples of 512.
  - The preparation API no longer accepts a `causal` argument.
- Added an SM103 benchmark reporting preparation and attention timings,
memory use, and operation counts, with optional JSON output.
- **Documentation**
- Clarified supported tensor layouts, quantization and packing behavior,
validated shapes, and benchmark timings.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [0b1cf2f](https://github.com/flashinfer-ai/flashinfer/commit/0b1cf2f572aca1429f86ac26de94b51984e84173)

- **作者**: eigen
- **时间**: 2026-10-03T21:18:30Z
- **提交信息**: refactor(cake_all_gather_matmul): share kernel sources across SM100 and SM103 (#5881)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

Closes #5772

## Summary

Regenerates `csrc/cake_all_gather_matmul` and
`flashinfer/comm/all_gather_matmul/cake_all_gather_matmul.py`
(Cake-generated Blackwell push-wait all-gather matmul, SM100 / SM103,
TP2 / TP4 / TP8) from its
producer. The byte-identical per-architecture copy, both `manifest.json`
files, the SHA-256 pin, the
822-line C++ launcher embedded as a Python string and its bespoke `nvcc`
+ `load_inline` build are
gone; every kernel is one generated device translation unit plus one
generated thin tvm-ffi launcher,
compiled by the regular JIT spec machinery once per exact architecture.

## What changed

- **One source per kernel, shared by SM100 and SM103.**
`csrc/cake_all_gather_matmul/sm100a/` and
`sm103a/` (two byte-identical 2,640-line `.cu`, two manifests) are
replaced by one device/binding
pair per program under `csrc/cake_all_gather_matmul/` plus two shared
headers (device helper
preamble, launch helpers). The six symbol-only barrier clones collapse
to two programs (one per
phase; the world size was already a runtime argument). The JIT loader
compiles each program with
the exact flag set of the device it runs on and names the library
`<program>_<arch>`.
- **Generated thin launchers on `tvm_ffi_utils.h`** instead of the hand
C++ launcher: `ffi::CUDADeviceGuard`,
`get_stream`, the target's tensor checks, by-value `CUtensorMap`
parameters encoded per launch, the
peer table as a by-value aggregate. No static per-device shared-memory
cache, no 7-peer unrolled
50-parameter functions, no descriptor storage tensors, no
`cuEventRecord`/`cuStreamWaitEvent`
  in C++.
- **Loader.** `flashinfer/jit/cake_all_gather_matmul.py` holds a program
table (`sources`, `block`,
`dynamic_smem_bytes`), an architecture-free route table
(`barrier_p{phase}`,
`main_{dtype}_ws{ws}`, `fused_peer_copy`) and the compile flags; no
manifest re-derivation, no
  source hashing, no `SMEM_TOTAL` regex over the CUDA text.
- **Host path.** Device capability is cached per device; remote scratch
views and readiness rows are
resolved once per (group, shape) workspace instead of per call; the
descriptor LRU caches and their
pinned-host staging copies are gone (descriptors travel by value); the
prepared packed-QKV launcher
binds the weight and group once and validates only the new input per
call. Strided inputs are
  rejected, never copied (as before).
- **Public surface unchanged.** `all_gather_matmul(backend="cake")`
serves `N=2048` on two-, four- and
eight-rank groups; `prepare_all_gather_matmul` serves bfloat16 packed
QKV (`N=1280` on eight ranks,
`N=2560` on four SM103 ranks); both signatures are unchanged. The
backend callable
(`all_gather_matmul_cake` and the prepared launcher) accepts a
caller-provided output. The unused
private `_all_gather_matmul_cake_packed_qkv_sm103_tp4` entry point is
removed.
- **Barrier launch bound to the caller's stream (correctness).** During
validation the regenerated
barrier launcher ran on the default stream: the launcher takes no tensor
argument, so nothing bound
the caller's stream to it, and the rendezvous before the pushes was
neither ordered against the
caller's stream nor captured into a CUDA graph recorded on it. The
export protocol's kernel-activity
parity gate (every timed call of the production path and of the
regenerated path must launch the same
kernels) caught it; the numerical tests, which run on the default
stream, did not. The backend now
binds the barrier launch to the call stream explicitly; a CPU test pins
the binding.
- **Tests and docs.** The source-text tests (manifest identity,
`FlashInferTensorMap const*` counts,
`peer_scratch_6` in the rendered launcher, descriptor-cache LRU
behaviour) are replaced by
behavioural tests of the route table, launch geometry, validation and
dispatch; the multi-GPU test
keeps its correctness checks and adds the caller-provided-output and
strided-input cases. `docs/api/comm.rst`
  describes the current routes.

Net: 9,425 -> 5,614 lines (-3,811, -40.4 %), 7 -> 24 files in the family
(two 2,640-line
per-architecture `.cu` + two manifests -> 9 device sources + 9 launchers
+ 2 shared headers; backend
2,058 -> 632 + a 314-line loader; tests 1,847 -> 606). `git diff
--stat`: 29 files, +5,286 / -9,097.

## Validation

**Device code.** `cuobjdump -sass` of the regenerated build against the
previous per-architecture
file, kernel symbol normalised:

| program | sm_100a | sm_103a |
|---|---|---|
| `fused_peer_copy` | not routed (the fused push is the SM103 TP8
packed-QKV route) | equal (66 instructions, symbol normalised) |

The 2 barrier and 6 main programs change ABI (pointer tensor maps behind
a descriptor acquire fence
and a device-pointer peer table -> `__grid_constant__` descriptors and a
by-value peer table, as the
generated thin launcher binds them); the comparison reports them as 12
previous bodies without a
counterpart and 8 new bodies per architecture. They are covered by the
numerical tests, the
production-path/regenerated-path parity protocol and the per-row timing
below, not by SASS equality.

**Production-path parity.** Every shape is measured against the
generator's production launcher on
the same GPUs (CUPTI GPU span, symmetric CUDA graphs, three
counterbalanced groups, cold L2 before
every sample): bitwise-equal output, identical per-call kernel set, and
source/export >= 0.97 on
performance rows (directional disagreement <= 0.12, endpoint drift <=
0.08). 57 rows: 28 on eight B200
(TP2 / TP4 / TP8) and 29 on eight B300 (the same plus the TP4 N=2560
packed-QKV row). Output, kernel set
and allocation probe pass on all 57; the timing gates pass on 55:
geomean source/export 1.0009x on B200
(performance rows 1.0041x) and 1.0027x on B300 (performance rows
1.0043x), per-row 0.9734x-1.0378x. Two
TP8 rows on the B200 node (`tp8_perf_bf16_m8192`,
`tp8_correctness_llama_qkv_bf16_m512_n1280`) failed only
the endpoint-drift gate in each of three samples (ratios 0.9994 / 1.0692
/ 1.0001 and 0.9624 / 1.0519 /
0.9616): the per-rank launch spread on these 8-rank rows is 40-85 % of
the median on both arms with flat
SM clocks, so they are reported as measurement-invalid rather than
sampled further; the same bytes pass
both rows on B300 (0.9997x / 0.9996x).

**Numerical tests.** `pytest tests/comm/test_all_gather_matmul_cake.py
tests/comm/test_all_gather_matmul_dispatch.py`
(CPU): 58 passed on both nodes;
`tests/comm/test_all_gather_matmul_cake_e2e.py` with 2, 4 and 8 visible
GPUs:
2 passed each on 8xB200 and on 8xB300 (bfloat16 and float16).

**Performance.** Paired CUPTI before/after against the previous backend
on the same eight B200 (both
launch orders, per-rank maximum over the rank set; gate `before/after >=
0.98` on the 14 TP2 / TP8
performance rows, the TP4 rows are correctness rows and are reported
without a gate):

| row (world size, M, N=2048 bf16 unless noted) | before (ms) | after
(ms) | before/after order A | order B | gate |
|---|---:|---:|---:|---:|---|
| TP2 M=65536 | 6.0640 | 5.8773 | 1.0318 | 1.0097 | pass |
| TP2 M=32768 | 3.0457 | 2.9903 | 1.0185 | 1.0096 | pass |
| TP2 M=16384 | 1.3390 | 1.3299 | 1.0069 | 1.0124 | pass |
| TP2 M=8192 | 0.7321 | 0.7224 | 1.0134 | 1.0125 | pass |
| TP2 M=4096 | 0.3000 | 0.2970 | 1.0099 | 1.0027 | pass |
| TP2 M=2048 | 0.1937 | 0.1918 | 1.0099 | 1.0055 | pass |
| TP2 M=1024 | 0.1735 | 0.1736 | 0.9989 | 0.9976 | pass |
| TP2 M=16384 f16 / M=19456 | 1.4363 / 1.7079 | 1.4250 / 1.6948 | 1.0079
/ 1.0077 | 1.0112 / 1.0105 | correctness rows |
| TP4 M=65536 … 1024 (7 rows) | 13.0235 … 0.4229 | 12.8232 … 0.3980 |
1.0156-1.0626 | 1.0146-1.0659 | correctness rows |
| TP4 M=16384 f16 / M=19456 | 3.1587 / 3.8507 | 3.0828 / 3.7788 | 1.0246
/ 1.0190 | 1.0211 / 1.0179 | correctness rows |
| TP8 M=65536 | 46.8839 | 44.7819 | 1.0469 | 1.0070 | pass |
| TP8 M=32768 | 27.9003 | 30.7440 | 0.9075 | 1.0130 | fail (A) |
| TP8 M=16384 | 17.0866 | 17.1012 | 0.9991 | 0.9303 | fail (B) |
| TP8 M=8192 | 18.5084 | 18.4944 | 1.0008 | 0.9521 | fail (B) |
| TP8 M=4096 | 16.4344 | 17.0763 | 0.9624 | 0.9039 | fail |
| TP8 M=2048 | 20.4323 | 20.5171 | 0.9959 | 0.9920 | pass |
| TP8 M=1024 | 16.9770 | 16.5715 | 1.0245 | 1.0036 | pass |
| TP8 M=16384 f16 / M=19456 / packed QKV M=512 N=1280 | 17.1610 /
32.5558 / 22.8982 | 17.1663 / 30.0937 / 20.3752 | 0.9997 / 1.0818 /
1.1238 | 0.8845 / 1.0074 / 0.9686 | correctness rows |

All TP2 and TP4 rows are at or better than before in both orders. Four
TP8 rows miss the 0.98 gate in
one or both orders on this node; the per-rank data show why: within one
order the eight ranks' medians
spread 7-18 ms (TP8 M=8192: 6.9-13.8 ms before, 7.3-14.5 ms after), the
two orders of the same row
disagree by up to 10 % (M=32768: 0.9075 vs 1.0130), and the regenerated
path is faster on as many
ranks as the previous one — the rank-max aggregation lets one slow rank
decide. The same eight-rank
noise made two TP8 rows of the parity protocol above measurement-invalid
on this node while they
pass on B300, so these four rows are reported as measurement-limited
rather than as a regression;
the B300 before/after run did not fit the lease and is not reported.

Per-call host dispatches (Python call including the synchronize, rank
max): one-shot route TP2 M=1024
105 -> 104 us, TP4 M=1024 283 -> 232 us, TP8 M=1024 3044 -> 2919 us
(barrier launcher,
`(ws-1) * num_chunks` copy + signal pairs, main launcher — the copy loop
is unchanged); prepared TP8
packed-QKV route 851 -> 1186 us (one native call before; now two
launcher calls plus the Python pushes,
each call validating the input and binding the stream).

`pre-commit` clean.

## Not in this PR (follow-ups)

- Runtime barrier phase and runtime peer-loop world size (folds the two
barrier programs into one and
the six main programs into two), runtime `K`, a runtime output row pitch
(`ldc`) and a runtime
fused-copy length: each changes the device code and is a kernel-ABI
change.
- Moving the per-chunk push loop into C++: kept in Python (resolved
views, no per-call lookups) so
the generated launchers stay pure launchers; a dedicated host push
helper is a separate decision.
- `prepare_all_gather_matmul(backend="auto")` still routes only the two
packed-QKV shapes to the
  Cake backend; widening the automatic route is a maintainer decision.
- The packed widths on the one-shot `backend="cake"` route and lifting
the SM103-only gate of the
TP4 `N=2560` prepared route (the device code is the same on SM100):
public-surface changes left to
  the maintainer.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added a JIT-compiled all-gather matrix multiplication backend for
SM100 and SM103 GPUs, with support for up to eight ranks and supported
half-precision formats.
  * Added a fused peer-copy path for a specific SM103 configuration.
* Expanded supported preparation configurations to include eight-rank
and additional four-rank cases.
* **Tests**
* Updated coverage for backend routing, input validation, stream
handling, and end-to-end results.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [463fac3](https://github.com/flashinfer-ai/flashinfer/commit/463fac3366693fb9a68c20bdd599a4c14080cbbb)

- **作者**: eigen
- **时间**: 2026-10-03T21:17:18Z
- **提交信息**: refactor(cake_mla): for kimi_k3, share kernel sources across SM100 and SM103 (#5871)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

Closes #5776

## What changed

The Cake Kimi-K3 MLA FP8 paged-attention route behind
`trtllm_batch_decode_with_kv_cache_mla(backend="cake")` is regenerated
through its export adapter. No kernel schedule changes; the generated
device code for each (kernel, architecture) is the same program as
before (see SASS table below).

**Generated sources (`csrc/cake_kimi_k3_mla/`)**
- One source per kernel for both architectures: 9 of the 10 kernels
(`main_rt16` .. `main_rt96`, `reduce_w1` / `reduce_w2` / `reduce_w4`,
`reduce_cta`) are one program each; the shared-memory base conversion is
an `#if __CUDA_ARCH__` guard inside the one source and each
architecture's preprocessed text is its previous text. The wide decode
kernel (`main_wide`) keeps one program per architecture: its sm_103a
variant computes the row max with the TMEM reduction load, the sm_100a
variant with a three-input max tree, and the two lowerings differ in too
many statements to fold under architecture guards. 11 programs replace
the 20 per-architecture copies under `sm_100a/` and `sm_103a/`; the
README names the per-architecture kernel and the reason.
- Thin bindings: `ffi::CUDADeviceGuard`, `get_stream`, the
`tvm_ffi_utils.h` checks, by-value TMA descriptors, one launch. The
private device-guard class, SM-count cache, mutex/atomic/map includes
and unused helpers of the previous bindings are gone.
- README regenerated from the same constants as the host plan (the wide
route starts at a longest KV of 8192 tokens, as the code always did; the
old README said 16384).
- The directory's `.clang-format` (`DisableFormat: true`) stays: it
exempts the generated sources from the pre-commit formatter, so the
delivered bytes are the attested ones.

**Registry (`flashinfer/jit/cake_kimi_k3_mla.py`)**
- `MODULES`: one record per program (sources, compile flags, FFI entry,
argument plan, supported architectures). `KERNELS`: logical kernel key
-> program, or -> {architecture: program} for the wide kernel. The JIT
spec is built per (program, architecture) with the exact `sm100a` /
`sm103a` flag set, so the two architectures never share a cached
library. The previous `ROUTES["<kind>__<arch>"]` table, per-architecture
records and closure hashes are removed.

**Host path (`flashinfer/mla/cake_kimi_k3_mla.py`)**
- The plan (route, row tile, split count, grids, reducer) is a pure
function of the batch shape, the longest KV and the SM count, cached per
shape (`plan_attention`); device facts are read once per device. A
decode loop no longer re-queries device properties or re-plans every
step.
- The dense `cum_seq_lens_q` of a 4-D query is kept per (batch, q_len,
device) instead of being allocated on every call (never cached from
inside a CUDA-Graph capture).
- `query` and `kv_cache` accept row-strided views on every route (equal
row spacing, 16-byte multiple): the TMA descriptors of the row-tile
programs and of the two-CTA wide programs carry the caller's row stride,
no `.contiguous()` (the wide programs' bindings gained this contract in
the second revision of this PR: their five TMA sources now declare the
physical row pitch, so the bindings encode `stride(-2)` with dense
leading dimensions checked instead of requiring contiguous tensors).
`out` rows stay dense (the kernels write a 512-element row stride);
`block_tables`, `seq_lens`, `cum_seq_lens_q` stay contiguous int32.
- Public API semantics unchanged: `backend="cake"` still routes
dimension tuples served by the TRT-LLM-style Blackwell Cake programs
there first and everything else with `kv_lora_rank=512` /
`qk_rope_head_dim=64` here.

**Tests (`tests/mla/test_cake_kimi_k3_mla.py`)**
- Decode, MTP, incremental prefill, wide route, CUDA-Graph replay (dense
and wide), route selection and the split planners as before; new:
row-strided query / cache views match the contiguous result bitwise on a
row-tile route (12 heads, KV 5000 -> `main_rt48`) and on the wide route
(96 heads, KV 8192 -> `main_wide`; padded query, padded cache and both),
each test asserting the route it exercises, a wide output row stride is
rejected, the plan is shared across calls of one shape, every kernel key
resolves to a program of the running architecture (the per-architecture
key names one program per supported architecture).

Net: `csrc/cake_kimi_k3_mla/` 42 files / 39,506 lines + 1,788 lines of
loader, host runner and test at the base revision -> 24 tracked files /
20,759 lines under `csrc/cake_kimi_k3_mla/` (22 generated units + README
+ `.clang-format`) + 1,711 lines of loader, host runner and test in this
PR (second revision; the export's delivery audit counts 11 programs / 25
files / 21,390 lines over the generated root, loader and runner), about
-46 %; the generated files are produced by regeneration.

## Validation

**SASS equivalence** (same compile flags as the JIT loader; symbol /
namespace hash normalised; rows = kernels, columns = architectures)

| kernel | sm_100a | sm_103a |
|---|---|---|
| main_rt16 | equal | equal |
| main_rt32 | equal | equal |
| main_rt48 | equal | equal |
| main_rt64 | equal | equal |
| main_rt96 | equal | equal |
| main_wide | equal | equal |
| reduce_w1 | equal | equal |
| reduce_w2 | equal | equal |
| reduce_w4 | equal | equal |
| reduce_cta | equal | equal |

`tools/check-sass-equivalence` (nvcc of the same toolkit, both
architectures compiled; run once on the B200 host and once on the B300
host with the same verdict): base 20 kernels (10 per architecture) vs
regenerated 20 kernels (9 folded programs x 2 architectures + the two
wide programs), `equivalent: true`, 10 distinct bodies per architecture,
0 missing, 0 introduced. The wide kernel is one program per
architecture, so its two cells are two different programs, each equal to
its predecessor. Re-run for the second revision (row-stride contract on
the wide programs' bindings; kernel bodies untouched) on the B300 host
with the same verdict, 20 / 20 equal, and on the B200 host with the same
verdict (20 / 20 equal).

**GPU tests** — `pytest tests/mla/test_cake_kimi_k3_mla.py` (second
revision, 34 tests incl. the wide-route strided test): B200 (SM100,
NVIDIA B200): 34 passed in 86.6 s; B300 (SM103, NVIDIA B300 SXM6 AC): 34
passed in 46.3 s. Cake-side on both passes: the source harness
correctness on the two smoke shapes (0 failed) and the CPU tests
(planner, export adapter symbols, two-route helpers; 28 passed).

**Performance** — paired CUPTI kernel time of the previous generation
(source, the Cake producer) against the delivered programs (export;
rendered and measured at one Cake revision for the second revision of
this PR), same GPU, cold L2, 4 counterbalanced groups x 4000 samples per
arm, every registered row (29 shapes x 2 architectures: decode h12 /
h96, MTP q2-q8, prefill, 64- and 96-row-tile coverage rows). sm_100a on
NVIDIA B200 (148 SMs, driver 580.82.07), sm_103a on NVIDIA B300 SXM6 AC
(148 SMs, driver 580.126.09); ratio before / after per row:

| shape | arch | route | before (source, us) | after (export, us) |
ratio before/after | verdict |
|---|---|---|---|---|---|---|
| mirror_h96_b1_q1_kv76800 (perf) | sm_100a |
main_wide_reduce_cta_sm_100a | 24.19 | 24.29 | 0.9960 | pass |
| mirror_h96_b1_q1_kv76800 (perf) | sm_103a |
main_wide_reduce_cta_sm_103a | 24.13 | 24.16 | 0.9987 | pass |
| mirror_h96_b2_q1_kv77699 (perf) | sm_100a |
main_wide_reduce_cta_sm_100a | 33.70 | 34.18 | 0.9860 | pass |
| mirror_h96_b2_q1_kv77699 (perf) | sm_103a |
main_wide_reduce_cta_sm_103a | 33.66 | 33.98 | 0.9906 | pass |
| mirror_h96_b6_q1_kv467751 (perf) | sm_100a |
main_wide_reduce_w2_sm_100a | 332.70 | 333.02 | 0.9990 | pass |
| mirror_h96_b6_q1_kv467751 (perf) | sm_103a |
main_wide_reduce_w2_sm_103a | 324.77 | 325.32 | 0.9983 | pass |
| mirror_h96_b7_q1_kv299613 (perf) | sm_100a |
main_wide_reduce_w2_sm_100a | 244.42 | 244.77 | 0.9986 | pass |
| mirror_h96_b7_q1_kv299613 (perf) | sm_103a |
main_wide_reduce_w2_sm_103a | 236.80 | 237.09 | 0.9988 | pass |
| mirror_h96_b8_q1_kv342305 (perf) | sm_100a |
main_wide_reduce_w2_sm_100a | 324.58 | 324.83 | 0.9992 | pass |
| mirror_h96_b8_q1_kv342305 (perf) | sm_103a |
main_wide_reduce_w2_sm_103a | 314.88 | 315.17 | 0.9991 | pass |
| mtp_h12_b8_q2_kv342305 (perf) | sm_100a | main_rt32_reduce_w4_sm_100a
| 252.42 | 252.45 | 0.9999 | pass |
| mtp_h12_b8_q2_kv342305 (perf) | sm_103a | main_rt32_reduce_w4_sm_103a
| 253.47 | 253.57 | 0.9996 | pass |
| mtp_h12_b8_q4_kv342305 (perf) | sm_100a | main_rt48_reduce_w2_sm_100a
| 274.56 | 274.98 | 0.9985 | pass |
| mtp_h12_b8_q4_kv342305 (perf) | sm_103a | main_rt48_reduce_w2_sm_103a
| 262.66 | 262.56 | 1.0004 | pass |
| mtp_h12_b8_q8_kv342305 (perf) | sm_100a | main_wide_reduce_w2_sm_100a
| 324.61 | 324.48 | 1.0004 | pass |
| mtp_h12_b8_q8_kv342305 (perf) | sm_103a | main_wide_reduce_w2_sm_103a
| 315.24 | 315.24 | 1.0000 | pass |
| mtp_h12_fixed_q5 (correctness) | sm_100a | main_rt64_reduce_w2_sm_100a
| 288.06 | 287.74 | 1.0011 | pass |
| mtp_h12_fixed_q5 (correctness) | sm_103a | main_rt64_reduce_w2_sm_103a
| 268.07 | 267.84 | 1.0008 | pass |
| mtp_h96_b8_q2_kv342305 (perf) | sm_100a | main_wide_reduce_w1_sm_100a
| 623.58 | 623.36 | 1.0004 | pass |
| mtp_h96_b8_q2_kv342305 (perf) | sm_103a | main_wide_reduce_w1_sm_103a
| 602.92 | 603.05 | 0.9998 | pass |
| mtp_h96_b8_q4_kv342305 (perf) | sm_100a | main_wide_reduce_w1_sm_100a
| 941.38 | 940.99 | 1.0004 | pass |
| mtp_h96_b8_q4_kv342305 (perf) | sm_103a | main_wide_reduce_w1_sm_103a
| 913.87 | 914.12 | 0.9997 | pass |
| mtp_h96_b8_q8_kv342305 (perf) | sm_100a | main_wide_reduce_w1_sm_100a
| 1832.77 | 1832.38 | 1.0002 | pass |
| mtp_h96_b8_q8_kv342305 (perf) | sm_103a | main_wide_reduce_w1_sm_103a
| 1767.32 | 1767.35 | 1.0000 | pass |
| mtp_h96_fixed_q8_kv8000 (correctness) | sm_100a |
main_rt96_reduce_w1_sm_100a | 140.32 | 140.70 | 0.9973 | pass |
| mtp_h96_fixed_q8_kv8000 (correctness) | sm_103a |
main_rt96_reduce_w1_sm_103a | 123.01 | 123.27 | 0.9979 | pass |
| prefill_h12_b1_q2048_kv131072 (perf) | sm_100a |
main_wide_reduce_w1_sm_100a | 2609.21 | 2609.02 | 1.0001 | pass |
| prefill_h12_b1_q2048_kv131072 (perf) | sm_103a |
main_wide_reduce_w1_sm_103a | 2497.62 | 2497.73 | 1.0000 | pass |
| prefill_h12_b2_q512_kv32768 (perf) | sm_100a |
main_wide_reduce_w1_sm_100a | 336.32 | 335.71 | 1.0018 | pass |
| prefill_h12_b2_q512_kv32768 (perf) | sm_103a |
main_wide_reduce_w1_sm_103a | 319.62 | 319.20 | 1.0013 | pass |
| prefill_h12_b4_q1024_kv8192 (perf) | sm_100a |
main_wide_reduce_w1_sm_100a | 336.35 | 336.26 | 1.0003 | pass |
| prefill_h12_b4_q1024_kv8192 (perf) | sm_103a |
main_wide_reduce_w1_sm_103a | 310.25 | 310.15 | 1.0003 | pass |
| prefill_h96_b1_q2048_kv131072 (perf) | sm_100a |
main_wide_reduce_w1_sm_100a | 20893.64 | 20892.73 | 1.0000 | pass |
| prefill_h96_b1_q2048_kv131072 (perf) | sm_103a |
main_wide_reduce_w1_sm_103a | 20231.01 | 20236.18 | 0.9997 | pass |
| prefill_h96_b2_q512_kv32768 (perf) | sm_100a |
main_wide_reduce_w1_sm_100a | 2616.03 | 2616.22 | 0.9999 | pass |
| prefill_h96_b2_q512_kv32768 (perf) | sm_103a |
main_wide_reduce_w1_sm_103a | 2502.82 | 2502.40 | 1.0002 | pass |
| trace_h12_b10_q1_kv474166 (perf) | sm_100a |
main_rt16_reduce_w4_sm_100a | 407.14 | 407.49 | 0.9991 | pass |
| trace_h12_b10_q1_kv474166 (perf) | sm_103a |
main_rt16_reduce_w4_sm_103a | 411.88 | 411.97 | 0.9998 | pass |
| trace_h12_b11_q1_kv474405 (perf) | sm_100a |
main_rt16_reduce_w4_sm_100a | 444.77 | 444.80 | 0.9999 | pass |
| trace_h12_b11_q1_kv474405 (perf) | sm_103a |
main_rt16_reduce_w4_sm_103a | 450.01 | 449.99 | 1.0000 | pass |
| trace_h12_b1_q1_kv76800 (perf) | sm_100a |
main_rt16_reduce_cta_sm_100a | 21.50 | 21.12 | 1.0182 | pass |
| trace_h12_b1_q1_kv76800 (perf) | sm_103a |
main_rt16_reduce_cta_sm_103a | 21.02 | 20.77 | 1.0123 | pass |
| trace_h12_b2_q1_kv77699 (perf) | sm_100a |
main_rt16_reduce_cta_sm_100a | 29.25 | 28.86 | 1.0133 | pass |
| trace_h12_b2_q1_kv77699 (perf) | sm_103a |
main_rt16_reduce_cta_sm_103a | 28.54 | 28.38 | 1.0056 | pass |
| trace_h12_b3_q1_kv261120 (perf) | sm_100a |
main_rt16_reduce_cta_sm_100a | 89.86 | 90.02 | 0.9982 | pass |
| trace_h12_b3_q1_kv261120 (perf) | sm_103a |
main_rt16_reduce_cta_sm_103a | 90.18 | 90.43 | 0.9972 | pass |
| trace_h12_b4_q1_kv268800 (perf) | sm_100a |
main_rt16_reduce_cta_sm_100a | 112.32 | 111.68 | 1.0057 | pass |
| trace_h12_b4_q1_kv268800 (perf) | sm_103a |
main_rt16_reduce_cta_sm_103a | 113.31 | 112.99 | 1.0028 | pass |
| trace_h12_b5_q1_kv276480 (perf) | sm_100a |
main_rt16_reduce_w4_sm_100a | 139.55 | 139.33 | 1.0016 | pass |
| trace_h12_b5_q1_kv276480 (perf) | sm_103a |
main_rt16_reduce_w4_sm_103a | 141.54 | 141.41 | 1.0009 | pass |
| trace_h12_b6_q1_kv467751 (perf) | sm_100a |
main_rt16_reduce_w4_sm_100a | 250.82 | 250.43 | 1.0015 | pass |
| trace_h12_b6_q1_kv467751 (perf) | sm_103a |
main_rt16_reduce_w4_sm_103a | 254.88 | 254.60 | 1.0011 | pass |
| trace_h12_b7_q1_kv299613 (perf) | sm_100a |
main_rt16_reduce_w4_sm_100a | 193.44 | 193.18 | 1.0013 | pass |
| trace_h12_b7_q1_kv299613 (perf) | sm_103a |
main_rt16_reduce_w4_sm_103a | 196.99 | 196.93 | 1.0003 | pass |
| trace_h12_b8_q1_kv342305 (perf) | sm_100a |
main_rt16_reduce_w4_sm_100a | 244.42 | 244.61 | 0.9992 | pass |
| trace_h12_b8_q1_kv342305 (perf) | sm_103a |
main_rt16_reduce_w4_sm_103a | 248.96 | 249.16 | 0.9992 | pass |
| trace_h12_b9_q1_kv348705 (perf) | sm_100a |
main_rt16_reduce_w4_sm_100a | 276.26 | 276.22 | 1.0001 | pass |
| trace_h12_b9_q1_kv348705 (perf) | sm_103a |
main_rt16_reduce_w4_sm_103a | 280.45 | 280.52 | 0.9998 | pass |

All 58 rows >= 0.98: yes (min 0.9860, max 1.0182; geomean 1.00036 over
58 rows, 1.00044 over the 54 perf rows); 58 of 58 rows pass every
exporter gate; the merged result is complete on both architectures (58
receipts, all retained from the per-architecture runs through
exact-input equivalence proofs, each measured on one pinned GPU per
architecture). The first revision's order-bound row
(`mirror_h96_b1_q1_kv76800` on sm_100a, launch-order disagreement 0.023)
passes every gate in this measurement on both architectures (ratio
0.9960 on B200, 0.9987 on B300). **Host path** — one eager
`trtllm_batch_decode_with_kv_cache_mla(backend="cake")` call per step on
three decode / MTP shapes, previous main vs this PR, same GPU, both
orders (second revision; first-block numbers, the reversed block agrees
within 2 %):

| shape | GPU | GPU span of one call, before -> after (us) | kernels per
call | host dispatch per call, median / p90 (us) |
|---|---|---|---|---|
| decode h12 b8 kv8192 | B300 | 66.9 -> 17.7 | 3 -> 2 | 69.6 / 89.5 ->
58.3 / 75.4 |
| decode h96 b8 kv8192 | B300 | 76.0 -> 20.8 | 3 -> 2 | 77.2 / 98.7 ->
60.9 / 74.4 |
| MTP h12 b8 q4 kv8192 | B300 | 69.6 -> 20.5 | 3 -> 2 | 70.4 / 91.0 ->
60.3 / 77.7 |
| decode h12 b8 kv8192 | B200 | 63.9 -> 18.1 | 3 -> 2 | 65.4 / 77.2 ->
56.0 / 57.9 |
| decode h96 b8 kv8192 | B200 | 74.0 -> 21.7 | 3 -> 2 | 71.2 / 72.5 ->
57.5 / 59.8 |
| MTP h12 b8 q4 kv8192 | B200 | 66.7 -> 21.0 | 3 -> 2 | 65.0 / 67.8 ->
56.0 / 58.0 |

The attention and reduce kernels are the same programs (SASS table), so
the GPU-span change is not kernel time: the previous host path launched
a `torch.arange` for `cum_seq_lens_q` on every call and then re-planned
the step (device-properties query, split plan) before launching
attention, which left the GPU idle for ~50 us inside each call; the PR
removes that kernel (dense `cum_seq_lens_q` cached per shape and device)
and plans once per shape, so one call is two kernels back to back. Host
dispatch time per call drops 14-21 %. The CUDA-Graph replay path is
unchanged (kernels only).

GPU span and kernel counts from CUPTI activity (cold L2,
`bench_gpu_time`), host time = wall time of the Python call without
synchronisation, median of 200 calls after warm-up.

**Order-bound row of the first revision** — `mirror_h96_b1_q1_kv76800`
on sm_100a tripped only the exporter's launch-order disagreement gate in
the first revision's measurement (three B200 samples at 0.023 vs the
0.02 limit, symmetric +/- 1.2 % order split, ratio 0.9936, correctness
and SASS equal). In the second revision's measurement the row passes
every gate on both architectures, so no acceptance exception is
requested; the earlier samples stay recorded in the first revision's
history of this PR.

## Not in this PR (maintainer decision items from #5776)
- Templated regeneration of the five row-tile kernels (16 / 32 / 48 / 64
/ 96 rows) and the three warp-per-row reducers as one program per
schedule axis, and the output row stride as a runtime kernel argument:
both change device code and the kernel ABI; proposed as a follow-up with
its own before/after measurements.
- The shared `backend="cake"` selection between the two Cake MLA
families (dimension / head-count table): documented here, unchanged.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added architecture-aware kernel selection and support for planning
attention launches.
* Added support for row-strided query and cache inputs, provided rows
meet alignment requirements.
* Lowered the threshold for selecting the wide-kernel path to 8,192 KV
tokens when packed rows exceed 64.
* **Bug Fixes**
* Improved validation of tensor layouts and launch parameters, with
clearer errors for invalid inputs.
  * Updated shared-memory handling for supported GPU architectures.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [b41b357](https://github.com/flashinfer-ai/flashinfer/commit/b41b357d2e1645149144e56aa547406f19a22e3e)

- **作者**: eigen
- **时间**: 2026-10-03T21:15:50Z
- **提交信息**: refactor(cake_fp8_projection): for kimi_k3, share kernel sources across SM100 and SM103 (#5888)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.


Closes #5775

## What changed

The experimental Kimi-K3 FP8 projection
(`flashinfer.gemm.kimi_k3_fp8_projection` and its prepare / allocate
entry points, Cake backend under
`flashinfer/experimental/kimi_k3_fp8_projection/`) is regenerated
through its export adapter. No kernel schedule changes; the device code
of every (kernel, architecture) is the same program as before (SASS
table below). Public signatures are unchanged.

**Generated sources (`csrc/cake_kimi_k3_fp8_projection/`)**
- One kernel source and one launcher source per program for both
architectures: 18 programs (1 quantization, 3 GEMM epilogue variants, 14
decode instances) replace the 40 per-architecture copies under
`sm_100a/` and `sm_103a/`. The SM100 / SM103 lowering differences are
`#if __CUDA_ARCH__` guards inside the one source; the JIT compiles it
with the flag set of the device it runs on.
- The three activation-quantization widths (1 / 2 / 4 K-blocks per half
warp) were three near-identical kernels differing in inlined constants;
they are one program with `QUANT_UNITS` on the compile line
(`-DQUANT_UNITS=1|2|4`), selected by the host from `M` and the SM count
as before.
- Device-helper prelude and launcher helpers hoisted into two shared
headers (`cake_kimi_k3_fp8_projection_device_common.cuh`,
`..._host_common.cuh`).
- Thin launchers: `ffi::CUDADeviceGuard`, `get_stream`, the
`tvm_ffi_utils.h` checks, by-value TMA descriptors, one launch. The
private device-guard class, atomic SM-count cache and mutex / map
includes of the previous launchers are gone.

**Registry (`cake_jit.py`)**
- `MODULES`: one record per program (sources, supported architectures,
compile flags, FFI entry, argument plan, closure digest). `KERNELS`:
logical kernel key -> program and compile-line defines. The JIT spec is
built per (program, architecture, defines) with the exact `sm100a` /
`sm103a` flag set, so instantiations never share a cached library. The
previous per-architecture `KERNELS[arch]` table and 40 per-architecture
records are removed (1,588 -> 893 lines).

**Dispatch table (`decode_table.py`)**
- The measured table is stored once (`DECODE_TABLE`: the 65 of 70 cells
both architectures measured alike) plus the 5 cells per architecture
whose fastest route differs (`DECODE_TABLE_OVERRIDES`);
`decode_table(arch)` merges them. Same cells, same routes as before
(1,123 -> 638 lines).

**Host path (`cake_backend.py`)**
- Device architecture and SM count are read once per device and cached;
the SM count replaces the hard-coded 148 (the persistent decode grid,
resident eligibility and quantization width now follow the device).
- The route (path, decode instance, split, grids, workspace layout) is
resolved once in `prepare_kimi_k3_fp8_projection`; the placeholder TMA
descriptor the register-epilogue kernels ignore is cached per device.
- `allocate_kimi_k3_fp8_projection_workspace` zero-fills only the
scale-tile and counter bytes instead of the whole buffer (split-K
partials are written before they are read; the counters self-reset).
- `x` stays a contiguous `[M, K]` BF16 tensor (the quantization kernel
reads rows at stride `K`); `out` keeps accepting any even-row-stride
view.

**Tests (`tests/experimental/test_cake_kimi_k3_fp8_projection.py`)**
- As before: recipe bit-exactness, zero-budget correctness vs the
quantized-operand emulation across the representative families and M
buckets, strided outputs, CUDA-Graph replay, workspace reuse. New: the
registry resolves one quantization program with `QUANT_UNITS` 1 / 2 / 4,
the per-architecture table overrides, an untabulated architecture is
rejected.

Net: 78,698 -> 24,714 lines (-53,984, -68.6 %), 89 -> 47 tracked files
(`flashinfer/experimental/kimi_k3_fp8_projection/`, its test module and
the benchmark); `csrc/` 73,888 -> 20,972 lines, 82 -> 40 files (36
kernel + launcher sources, 2 shared headers, `README.md`,
`.clang-format`). Every generated file is produced by regeneration. The
benchmark `benchmarks/bench_cake_kimi_k3_fp8_projection.py` uses only
the public API and is unchanged.

## Validation

**SASS equivalence** (same compile flags as the JIT loader; symbol /
namespace hash normalised; one row per program, the quantization program
listed per define) — 40 of 40 (kernel, architecture) pairs equal, 20
distinct bodies per architecture, nothing missing or introduced:

| program | sm_100a | sm_103a |
|---|---|---|
| quant_act (QUANT_UNITS=1) | equal | equal |
| quant_act (QUANT_UNITS=2) | equal | equal |
| quant_act (QUANT_UNITS=4) | equal | equal |
| proj_gemm (register epilogue) | equal | equal |
| proj_gemm_rstaged | equal | equal |
| proj_gemm_tstore | equal | equal |
| decode t128_p3 | equal | equal |
| decode t16_p4 | equal | equal |
| decode t16_p4_fused | equal | equal |
| decode t16_p4_fused_cs2 | equal | equal |
| decode t16_p4_fused_cs4 | equal | equal |
| decode t32_p3_fused_cs8 | equal | equal |
| decode t32_p3_fused_r5_q4 | equal | equal |
| decode t32_p3_fused_res | equal | equal |
| decode t32_p4 | equal | equal |
| decode t32_p4_cs4 | equal | equal |
| decode t32_p4_cs8 | equal | equal |
| decode t64_p2_fused_r3_q4 | equal | equal |
| decode t64_p2_fused_res | equal | equal |
| decode t64_p4 | equal | equal |

**GPU tests** — `pytest
tests/experimental/test_cake_kimi_k3_fp8_projection.py`: B200 (SM100):
36 passed; B300 (SM103): 36 passed. Export protocol of the generator
(220 representative shapes per architecture, bitwise output parity
between the previous production launcher and this delivery, same launch
count and grids, no allocation in the launch): correctness 220/220 on
B200 and 220/220 on B300.

**Performance.** Two measurements, both CUPTI kernel time with cold L2,
previous main (909aa7b4) vs this PR on the same GPU.

1. *Interleaved per-shape protocol* (the generator's acceptance measure:
both launchers in one process, alternating arms, 3 groups x 2000 samples
per row, 220 representative shapes per architecture incl. padded-stride
rows; ratio before/after): B200 geomean 1.0013 over 220 rows, 215 rows
within the gates; B300 219 of 220. Rows outside the gates: four B200
rows and one B300 row of the `kv_a` / `fused_qkv_a` families at M =
64-256 (`decode:t64_p4`) where the pooled ratio is dominated by the
first launch after an arm switch (the arm measured second runs that
kernel 3.5-4 us slower for one launch, in either direction; steady state
within 3 %; identical device code) — a harness artefact being fixed on
our side; and `f_b` M = 129 (padded output stride) at 0.939 on B200 (see
the open item below).
2. *Sequential benchmark*
`benchmarks/bench_cake_kimi_k3_fp8_projection.py --cupti` (132 rows = 22
families x M in {1, 8, 64, 256, 4096, 16384}; one process per tree, run
as two blocks: base then PR, and PR then base). B200: block 1 median
1.0008 / geomean 1.0018, block 2 median 1.0000 / geomean 1.0004
(before/after). Rows below 0.98 in either block, with both block values
and the interleaved value of the same row:

| row | block 1 (base -> PR) | block 2 (PR -> base) | interleaved |
reading |
|---|---:|---:|---:|---|
| tp1_fused_qkvg_m16384 (4 ms GEMM) | 1.1180 | 0.8983 | 0.9999 | the
second pass of each block ran slower (sequential clock drift on a shared
node); the sign follows the pass order |
| tp1_o_proj_m16384 | 0.9408 | 1.0410 | 0.9998 | same |
| tp1_in_proj_qkvgfab_m16384 | 0.9628 | 1.0411 | 1.0000 | same |
| tp1_fused_qkv_a_m16384 | 0.9936 | 0.9558 | 0.9999 | same (block 2) |
| tp1_in_proj_qkvgfab_m4096 | 0.9835 | 0.9623 | 0.9998 | same; sibling
GEMMs tp1_fused_qkvg_m4096 1.078 / 1.073 and tp1_q_proj_m16384 1.049 /
1.046 swing the other way in the same blocks |
| tp8_in_proj_qkvgfab_m16384 | 0.9702 | 0.9828 | 0.9998 | same (block 1)
|
| tp8_fused_qkvg_m16384 | 1.0252 | 0.9718 | 1.0002 | same (block 2) |
| tp8_q_proj_m16384 | 0.9979 | 0.9796 | 1.0007 | block 2 only, at the
threshold |
| tp1_kv_a_m64 | 0.9962 | 0.9734 | 0.9846 | block 2 only |
| tp1_kv_b_m256 | 0.9896 | 0.9744 | 0.9765 | block 2 only; this row sits
in a 2-3 % band in every measurement |
| tp8_f_b_m1 | 0.9769 | 0.9921 | 1.0075 | block 1 only, 0.1 us on a 4.1
us launch |
| tp8_kv_b_m1 | 0.9416 | 0.9600 | 1.0201 | below 0.98 in both blocks,
while the interleaved protocol has the PR faster: in the sequential
bench each tree prepares its own weight tiles and this 4.6 us
single-launch row is sensitive to where that allocation lands (placement
effect measured at 0.8-3 % by a weight-buffer swap; launcher effect <=
0.4 %) |
| tp8_q_b_m1 | 0.9515 | 0.9706 | 1.0152 | same placement pattern
(interleaved 1.015 with a shared weight storage) |
| **tp1_f_b_m1** | **0.9740** | **0.9613** | **0.9565** | **regression
candidate**: below 0.98 in both blocks and in the interleaved protocol
(0.968 / 0.955 / 0.957 across three processes): the single-launch
`decode:t16_p4_fused` route of the `f_b` family (N = 12288, K = 128) is
0.13-0.17 us slower through the delivered launch path; same device code.
Together with `f_b` M = 129 (0.939) this is the open item below. |

B300 (sm_103a): block 1 (base then PR; aws-pdx B300 SXM6 AC, one process
per pass) median 1.0000 / geomean 0.9998 / min 0.9669 / max 1.0583 over
132 rows; 8 rows below 0.98, none below 0.96, all single-pass readings
with the interleaved value of the same row in brackets: tp8_b_proj_m1
0.9669 [0.9873], tp8_kv_b_m64 0.9695 [0.9873],
tp8_in_proj_qkvgfab_m16384 0.9722 [0.9995], tp1_q_b_m8 0.9744 [1.0033],
tp8_q_proj_m64 0.9771 [1.0132], tp8_f_b_m256 0.9792 [0.9722],
tp8_in_proj_qkvgfab_m256 0.9793 [0.9935], tp8_kv_a_m8 0.9796 [0.9793].
The B200 regression-candidate rows on B300: `f_b` M = 1 0.9932 [0.9799],
`f_b` M = 129 (interleaved) 0.98-1.00, tp8_kv_b_m1 1.0214 [0.9860],
tp8_q_b_m1 0.9947 [1.0267]. Block 2 (PR then base, second B300 node):
median 1.0000 / geomean 1.0004 / min 0.9465 / max 1.0620 over 132 rows;
9 rows below 0.98 (block-1 value in brackets): tp8_fused_qkv_a_m16384
0.9465 [0.9825]; tp8_o_proj_m4096 0.9696 [0.9842]; tp8_b_proj_m1 0.9710
[0.9669]; tp8_q_proj_m64 0.9739 [0.9771]; tp1_q_b_m8 0.9743 [0.9744];
tp8_in_proj_qkvgfab_m64 0.9746 [0.9880]; tp1_kv_a_m64 0.9766 [0.9961];
tp1_kv_b_m1 0.9784 [0.9870]; tp8_f_b_m256 0.9792 [0.9792]. Rows below
0.98 in both B300 blocks (interleaved value in brackets): tp8_b_proj_m1
0.9669 / 0.9710 [0.9873], tp8_q_proj_m64 0.9771 / 0.9739 [1.0132],
tp1_q_b_m8 0.9744 / 0.9743 [1.0033], **tp8_f_b_m256 0.9792 / 0.9792
[0.9722] — below 0.98 in both blocks and in the interleaved protocol, so
it is a regression candidate on B300 as well** (same `f_b` family as the
B200 item, single-launch `decode:t32_p3_fused_res`, 4.5 us, +0.1 us,
identical device code). The B200 regression-candidate row `f_b` M = 1
reads 0.9865 in block 2. The generator-side production route on B300 (8
rows, both orders): 0.991-1.013 / 0.990-1.012 before/after, launch
counts unchanged.

Cake-side production route (the kernels' serving path in the generator's
runtime, base vs this change, 8 rows, both orders): 0.974-1.011 /
0.969-1.007 before/after, launch counts unchanged; no row below 0.98 in
both orders.


Launch count per call is unchanged (1 for the fused decode routes, 2 for
the quantization + GEMM / split-K decode routes; checked for every row
by the protocol's activity parity). Host time per eager call was not
measured in this round.

## Not in this PR (for maintainers)

- **API placement.** Should these kernels become a `backend="cake"` of
`gemm_fp8_nt_groupwise` (which would need a fused or separate groupwise
activation quantization writing the tiled scale layout, an API home for
the one-time weight requantization / tiling, and caller-owned split-K
workspaces), or stay separate experimental entry points? This PR keeps
the separate entry points; see the question on #5775.
- **Open item (regression candidate): `f_b` family, single-launch fused
decode rows on B200.** `f_b` M = 1 is 0.13-0.17 us (3-4 %) slower
through the delivered launch path in both sequential blocks and in the
interleaved protocol (0.968 / 0.955 / 0.957 across three processes), and
`f_b` M = 129 with a padded output stride is 0.4-0.5 us (5-6 %) slower
in steady state across four processes and three B200s (0.957 / 0.957 /
0.953 / 0.939). On B300 these two rows read 0.98-1.00, but `f_b` M = 256
(tp8, `decode:t32_p3_fused_res`, 4.5 us) is 0.979 in both sequential
blocks and 0.972 in the interleaved protocol, so the B300 half carries
one regression candidate of the same family. The other M values of the
family and the other families' fused rows are within the gates on both
architectures. Device code is identical (SASS table above), so the
difference is in the host/launch path of this family's
`decode:t16_p4_fused` / `decode:t64_p2_fused_res` routes (candidates:
the by-value descriptor argument block for a strided `out`, or the
placement of the per-tree weight tiles). We are diagnosing it with a
launcher-only A/B on these rows and will post the result here; it is not
fixed in this PR.
- Kernel-side follow-ups that change device code or kernel ABI: dropping
the unused TMA-descriptor parameters of the register-epilogue GEMM and
the unfused decode kernels; a runtime row stride for `x`; retiring
decode instances only after per-shape measurements.
- `.pre-commit-config.yaml`: this family's generated `csrc/` directory
is not in the clang-format exclude list (other generated Cake families
are); the delivery carries a `csrc/.clang-format` and `pre-commit run
--from-ref origin/main --to-ref HEAD` passes on this PR, so no exclude
entry is added here.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [edc66c9](https://github.com/flashinfer-ai/flashinfer/commit/edc66c945c80ccc218e71fbcc84340312c8559a1)

- **作者**: eigen
- **时间**: 2026-10-03T21:15:16Z
- **提交信息**: refactor(cake_mla_varq_dcp_decode): regenerate as one source per schedule (#5868)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

Closes #5782

## Summary

Regenerates `flashinfer/experimental/cake_mla_varq_dcp_decode`
(Cake-generated Blackwell MLA
variable-query + DCP decode, SM100 / SM103) from its producer with the
per-architecture
duplication removed and a leaner host path. Device code is unchanged
instruction for
instruction (see Validation); only the delivery layout, the host
bindings and the Python host
path change.

## What changed

- **One source per schedule, shared by SM100 and SM103.** The nine
kernel translation units
(eight main-kernel variants + the split-KV merge kernel) now live once
under
`csrc/cake_mla_varq_dcp_decode/`; the only architecture-dependent
statement (the shared-memory
base materialization) is emitted under an exact `__CUDA_ARCH__` guard.
The `sm_100a/` and
`sm_103a/` trees (36 files) are deleted. The JIT loader compiles the
shared source with the
exact flag set of the device it runs on and keys the cached library by
`<program>_<arch>`.
- **Shared headers.** The ~1.2K-line device helper preamble and the
binding launch helpers are
emitted once (`cake_mla_varq_dcp_decode_device_common.cuh`,
`cake_mla_varq_dcp_decode_host_common.cuh`)
  instead of once per kernel.
- **Thin launchers on `tvm_ffi_utils.h`.** Every binding uses
`ffi::CUDADeviceGuard`,
`get_stream` and the target's tensor checks; the private device-guard
class, the per-launch
`cudaFuncSetAttribute` behind a mutex and map, the SM-count attribute
query and the two
never-called helpers are gone. The dynamic shared-memory opt-in is a
one-time property of the
  kernel handle.
- **Registry.** `cake_jit.py` lists one argument plan per stage role,
each program once with the
  architectures it serves, and an architecture-free route table
`"<dtype>_p<page>_g<groups>_pm<partition>" -> program`; the per-module
argument-plan copies and
  the unchecked `closure_sha256` fields are removed.
- **Stride-carrying K/V binding.** The K/V tensor maps take the cache's
physical strides, so one
layer of a `[num_pages, L, page_size, 576]` pool binds in place;
`prepare` no longer calls
  `kv_cache.contiguous()` (only the 576-wide row must be dense).
- **Host path.** Device capability and SM count are queried once per
device; the partial O / LSE
workspace regions are no longer zeroed at prepare (every read of them is
ordered after an
acquire of the per-slot flag; the counters, slot flags, split table and
control words are still
zeroed), removing a 44.6 MB memset per prepare on the h96 / W8 / batch
32 / MTP-3 / 32K row;
index tensors are converted only when they are not already dense int32.
- **Packaging and tests.** `csrc/**` added to the package's
`package-data`; the test that asserted
the structure of the generated registry is replaced by a behavioural
test of the strided KV pool;
  all other tests unchanged.

Net for the generated sources: 76,916 -> 28,296 lines (-63.2 %), 37 ->
21 files under `csrc/`; the family goes from 41 to 25 files (36
per-architecture files removed). Host modules: `cake_jit.py` 1,238 ->
267, `cake_backend.py` 1,025 -> 1,066, test module 984 -> 1,037.

## Validation

**Export protocol (paired CUPTI, source arm = the producer's production
runner, export arm = this package; 76 rows = 38 contract rows x {B200,
B300}; 3 counterbalanced groups x 2000 graph-replayed calls per arm,
cold L2).** All 76 rows pass (correctness against the production runner
on every row; source/export >= 0.80 and directional disagreement <= 0.15
on every row). Geomean source/export: 0.9959x over all rows, 1.0013x
over the 48 performance rows (min 0.9722x on
`perf_bf16_h128_w8_b16_q1_s32k` on B300, max 1.0238x), 0.9867x over the
28 short correctness rows (7-21 us launches, not performance-gated).
Against the upstream CuTe-DSL monolithic var-Q + DCP MLA decode at this
revision the package is faster on every one of the 48 performance rows:
geomean 1.1796x, min 1.0126x, max 1.4784x. The standalone family
benchmark (`benchmarks/bench_cake_mla_varq_dcp_decode.py`) agrees: 24/24
rows faster on each device, geomean 1.1984x on B200 and 1.2023x on B300.

**Device code equivalence (mechanical steps).** For every surviving
kernel x architecture the
SASS of the regenerated build equals the SASS of the previous
per-architecture file after
normalising the kernel symbol / namespace hash (compiled with the
repository's JIT flags):

| program (route) | sm_100a | sm_103a |
|---|---|---|
| `bf16_p32_g4_pm1` (`…_4ad9a542b809`) | equal | equal |
| `bf16_p64_g16_pm0` (`…_557713ccd289`) | equal | equal |
| `bf16_p64_g4_pm0` (`…_54bce6b66e69`) | equal | equal |
| `bf16_p64_g4_pm1` (`…_ffdb0eb3b15e`) | equal | equal |
| `fp8_p128_g4_pm1` (`…_9ccf6c8ca6b3`) | equal | equal |
| `fp8_p64_g16_pm0` (`…_2694148151c9`) | equal | equal |
| `fp8_p64_g4_pm0` (`…_be8f417457dc`) | equal | equal |
| `fp8_p64_g4_pm1` (`…_0a58ba24b313`) | equal | equal |
| `merge` (`…_a90f4c737cfc`) | equal | equal |

Comparison summary: equivalent, 18 base kernels (9 per architecture) vs
18 candidate builds (9 programs x 2 architectures), 9 distinct bodies
per architecture, nothing missing, nothing introduced.

**Numerical tests.** `pytest
tests/experimental/test_cake_mla_varq_dcp_decode.py` on a B300: 22
passed, 3 skipped (the two page-size variants no program is registered
for, each skip naming the variant, and the unsupported-device test on a
supported device); on a B200: 22 passed, 3 skipped (the same three). The
planner / workspace parity tests against the producer's host plan pass
on both.

**Performance (host-path changes).** Paired CUPTI before/after on the
same GPU, every row
`before/after >= 0.98`:

| row | sm_100a before (us) | after (us) | ratio | sm_103a before (us) |
after (us) | ratio |
|---|---:|---:|---:|---:|---:|---:|
| `perf_bf16_h128_w8_b16_q1_s32k` | 25.06 | 24.93 | 1.0052 | 23.81 |
23.78 | 1.0013 |
| `perf_bf16_h128_w8_b8_mtp3_s128k` | 57.25 | 57.22 | 1.0005 | 55.84 |
55.68 | 1.0029 |
| `perf_bf16_h128_w8_b64_q1_s8k` | 24.00 | 24.03 | 0.9988 | 23.23 |
23.20 | 1.0013 |
| `perf_bf16_h96_w8_b32_mtp3_s32k` | 52.32 | 52.32 | 1.0000 | 50.75 |
50.82 | 0.9986 |
| `perf_bf16_h96_w8_b16_q1_s128k` | 60.29 | 60.16 | 1.0022 | 59.30 |
59.39 | 0.9985 |
| `perf_bf16_h96_w8_b64_mtp3_s8k` | 32.64 | 32.64 | 1.0000 | 31.30 |
31.30 | 1.0000 |
| `perf_bf16_h48_w4_b32_mtp3_s32k` | 70.35 | 70.21 | 1.0020 | 68.45 |
68.61 | 0.9977 |
| `perf_bf16_h48_w4_b128_q1_s8k` | 52.54 | 52.61 | 0.9987 | 51.74 |
51.78 | 0.9992 |
| `perf_bf16_h24_w2_b64_mtp3_s16k` | 81.34 | 81.38 | 0.9995 | 81.28 |
81.12 | 1.0020 |
| `perf_bf16_h64_w4_b32_q4_s32k` | 73.76 | 73.82 | 0.9992 | 71.65 |
71.78 | 0.9982 |
| `perf_bf16_h32_w2_b128_q1_s16k` | 141.57 | 141.18 | 1.0028 | 140.74 |
140.61 | 1.0009 |
| `perf_bf16_h16_w1_b64_mtp3_s8k` | 83.14 | 83.07 | 1.0008 | 82.90 |
82.85 | 1.0006 |
| `perf_fp8_h128_w8_b16_q1_s32k` | 18.88 | 18.75 | 1.0069 | 17.82 |
17.76 | 1.0034 |
| `perf_fp8_h128_w8_b8_mtp3_s128k` | 35.90 | 35.84 | 1.0017 | 33.60 |
33.57 | 1.0009 |
| `perf_fp8_h128_w8_b64_q1_s8k` | 15.58 | 15.58 | 1.0000 | 14.24 | 14.24
| 1.0000 |
| `perf_fp8_h96_w8_b32_mtp3_s32k` | 34.05 | 34.08 | 0.9991 | 31.74 |
31.76 | 0.9994 |
| `perf_fp8_h96_w8_b16_q1_s128k` | 37.95 | 37.92 | 1.0008 | 36.67 |
36.67 | 1.0000 |
| `perf_fp8_h96_w8_b64_mtp3_s8k` | 25.28 | 25.31 | 0.9988 | 23.49 |
23.49 | 1.0000 |
| `perf_fp8_h48_w4_b32_mtp3_s32k` | 43.81 | 43.81 | 1.0000 | 42.18 |
42.14 | 1.0009 |
| `perf_fp8_h48_w4_b128_q1_s8k` | 34.17 | 34.17 | 1.0000 | 33.18 | 33.22
| 0.9988 |
| `perf_fp8_h24_w2_b64_mtp3_s16k` | 50.26 | 50.30 | 0.9992 | 49.86 |
49.82 | 1.0008 |
| `perf_fp8_h64_w4_b32_q4_s32k` | 48.03 | 48.00 | 1.0006 | 45.70 | 45.70
| 1.0000 |
| `perf_fp8_h32_w2_b128_q1_s16k` | 80.38 | 80.40 | 0.9998 | 79.50 |
79.49 | 1.0001 |
| `perf_fp8_h16_w1_b64_mtp3_s8k` | 52.29 | 52.32 | 0.9994 | 51.46 |
51.55 | 0.9983 |

First-block ratios shown; B200 0.9987..1.0069 (reversed order
0.9924..1.0053), B300 0.9977..1.0034 (reversed order 0.9974..1.0042): no
row below 0.98 on either device in either order; the selected variant is
identical before and after on every row. The 14 correctness rows (7-21
us launches) are covered by the export protocol above.

Per-call launch count unchanged (main + conditional merge). Prepare-time
zeroing of the partial O / LSE regions is gone: 44.6 MB on
`perf_bf16_h96_w8_b32_mtp3_s32k` (the row's `partial_rows x 512 x 2 B +
partial_rows x 4 B`) -> 0 B; the counters, slot flags, split table and
control words are still zeroed.

`pre-commit` clean.

## Not in this PR (follow-ups)

- Folding the item-group-capacity (`n_cache[4]` vs `[16]`) and page-size
(32 / 64 / 128) variants
into one parametrised source per (dtype, scheduler): the generator
currently folds these into
the traced body, so each fold needs a generator capability first; the
eight main variants stay.
- The ten (dtype, page size, scheduler) combinations that `page_size`
validation admits but no
registered program serves keep raising `NotImplementedError` naming the
variant and the
  registered set; registering them follows the fold above.
- A page-table row stride different from `max_pages`, dropping the
unused debug-timestamp kernel
argument, caching encoded TMA descriptors across launches, and strided
`out` / `lse` views: each
  is a kernel ABI change and is deferred.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added support for decoding from strided KV cache views, provided their
final dimension is contiguous.
* Expanded generated-kernel availability across supported device
architectures.
* Improved preparation memory use by reusing compatible index tensors
and avoiding unnecessary initialization of partial-result buffers.
* **Bug Fixes**
* Strengthened validation of tensor layouts, devices, and kernel launch
requirements.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [3d7acc0](https://github.com/flashinfer-ai/flashinfer/commit/3d7acc0541fc344d652b0bcbc5178d181b6b8cb7)

- **作者**: eigen
- **时间**: 2026-10-03T21:14:34Z
- **提交信息**: refactor(cake_msa): regenerate the Blackwell MSA family as one source per program (#5893)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

Closes #5778

## Summary

Regenerates the Cake-generated MiniMax Sparse Attention family for SM100
/ SM103
(`csrc/blackwell_msa/`, `flashinfer/jit/blackwell_msa.py`,
`flashinfer/msa_ops/_blackwell_sm100.py`)
from its generator instead of the frozen, hand-assembled snapshot that
#4355 shipped. The delivered
device code is the generator's current output for every surviving
(program, architecture): it is not
instruction-for-instruction the snapshot's code (the snapshot was a
differently specialised build of the
same programs; see "Device code" in Validation for the per-program
comparison), and it is validated by
the generator's acceptance protocol (correctness against an fp32
reference and paired CUPTI timing per
shape, both architectures) plus this repository's tests. The delivery
layout, the bindings, the JIT
registry and the Python host path change. Three public behaviour changes
are listed for the maintainers.

## What changed

- **One source per program, shared by SM100 and SM103.** 29 programs
(TopK select; 12 prefill-union
variants; 6 M16 decode variants; the 2 single-shape FP8-KV Q1 decode
programs; the uniform FP8 QKV
decode; 3 long-prefill forward programs + the SM100 direct-group
variant; 3 long-prefill reducers)
are delivered once as `<program>_kernel.cu` + `<program>_binding.cu`.
The SM100 / SM103 differences
of the long-prefill forwards (`exp2` lowering, `tcgen05.ld.red`
epilogue) are `#if __CUDA_ARCH__`
guards inside the one source; the JIT compiles it with the exact
`sm100a` / `sm103a` flag set of
the device it runs on. The 150 per-architecture `.cu` files (68
byte-identical name pairs) and
  `route_manifest.json` are deleted.
- **Thin launchers on `tvm_ffi_utils.h`.** Every binding uses
`ffi::CUDADeviceGuard`, `get_stream`
and the repository's tensor checks; the hand-assembled wrappers that
`#include` the device body
  behind `uint8_t` / `CUtensorMap` renames are gone.
- **Registry (`flashinfer/jit/blackwell_msa.py`).** `MODULES`: one
record per program (sources,
compile flags, FFI entry, argument plan, launch geometry, closure
digest, architectures). `ROUTES`:
`"<route key>:<stage>" -> program`, the same table for both targets.
`BLACKWELL_MSA_VARIANTS_BY_TARGET`
(used by `flashinfer/aot.py`) is derived from `MODULES`. The JIT spec is
built per (program, target)
  so the two architectures never share a cached library.
- **Host path (`flashinfer/msa_ops/_blackwell_sm100.py`, 3,191 + 694 ->
~1,900 lines).** Route keys
are computed from the call (dtype pair, layout, GQA group, causal mask
family, FP8 Q1 coordinate,
long-prefill predicate) and looked up in `ROUTES`; programs are launched
in their generated
argument order. Device target and SM count are read once per device. The
shape-exact routes, the
environment switches and the 694-line reverse-prefill planner are
removed (see below). The
CUDA-graph workspace contract (`MSASparseAttentionWorkspace`), the NVFP4
hand-offs and the public
  signatures are unchanged.
- **Tests.** `tests/msa_ops/test_blackwell_msa_sm100.py` (25 public-API
cases), `test_blackwell_msa_topk_dispatch.py`,
`test_msa_ops.py`, `test_msa_topk_per_token.py` unchanged. New:
`tests/jit/test_blackwell_msa_jit.py`
(every route resolves to a delivered program with sources present,
per-target variant list) and
`tests/msa_ops/test_blackwell_msa_routes.py` (CPU-only: every `ROUTES`
key is re-derived from the
host predicates; FP8 Q1 coordinates; long-prefill boundaries; GQA16
paged mask family; uniform FP8
grid). Removed: the four tests that asserted the structure of the frozen
snapshot
(`test_blackwell_msa_source.py`, `test_blackwell_msa_route_manifest.py`,
`test_blackwell_msa_benchmark_manifest.py`,
`test_blackwell_msa_reverse_plan.py`) and
`test_blackwell_msa_direct_decode_route.py` (imported private names of
the removed routes; its
  coverage is in the new route test).

Net: `csrc/blackwell_msa/` 170,947 -> `<N_after>` lines (`<delta>`), 151
-> `<files_after>` files;
Python host path 3,885 -> `<N_py_after>` lines.

### Public behaviour changes (for the maintainers)

1. **TopK16 only on compute capability 10.0 / 10.3.**
`msa_sparse_attention` and
`msa_sparse_decode_attention` accept `topk == 16` (the serving
contract). Previously `topk` in
{4, 8, 32} was admitted at exactly one benchmark coordinate each through
shape-exact kernels
(`decode_m16_bf16_paged_topk32`, `decode_m16_bf16_paged_topk4_exact512`,
`reverse_prefill_bf16_query_fp8_kv_flat_topk8_qagg_pdl`,
`reverse_prefill_bf16_paged_topk4_qload4`)
and rejected everywhere else; those coordinates now raise `ValueError`
like every other non-16
call, matching the SM120 path. Question on #5778: do the topk 32 / 8 / 4
coordinates have a consumer?
2. **Routes removed.** The two environment switches
`FLASHINFER_MSA_PREFILL_SCHEDULE` (`m64`) and
`FLASHINFER_MSA_FP8_Q1_SCHEDULE` (`q1_exact`) and the kernels they
selected
(`prefill_m64_bf16_gqa16_flat`,
`decode_q1_bf16_query_fp8_kv_exact_{flat,paged}`), the four
reverse-prefill variants above with their reducers, and the
reverse-prefill planner module
`_blackwell_sm100_reverse_plan.py`. Those calls take the general TopK16
kernels. The two
single-shape FP8-KV Q1 decode programs stay on their coordinates (paged
B128 / KV4096 / 4 KV heads;
   flat B32 / KV8192 / 4 KV heads).
3. **`out=` on every decode route.** `msa_sparse_decode_attention(...,
out=...)` previously landed in
`out` only on the packed-NVFP4 route and raised `NotImplementedError`
otherwise; every Blackwell
decode route now writes the caller's `out` (shape, dtype, device and
contiguity validated).

## Validation

**Device code.** The snapshot's kernels and the regenerated programs
were compared as SASS (same JIT
loader, same compile flags including the loader's default
`-use_fast_math`, `cuobjdump -sass`, kernel
symbol and section banners normalised) for every (program, architecture)
that both the old and the new
dispatcher route. No pair is instruction-identical: the snapshot was
built from an older, runtime-
parameterised specialisation of the same programs, while the regenerated
sources are per-program
specialisations, so the compiler produces different code for the same
arithmetic (for the Top-K
selection program on SM100: 496 vs 488 instructions, the snapshot
carries a runtime integer-division
idiom the specialised program does not need, 8 vs 1 global loads, 29 vs
7 branches; same MUFU count
(1 vs 1) and no fused/plain FP multiply-adds in either). Compiling the
regenerated programs with and
without `-use_fast_math` gives byte-identical SASS, so the flag is not a
numerics item for this family.
Per-pair summary (instruction count, registers / shared memory,
opcode-class deltas), one row per
routed (program, architecture):

| route stage | arch | insns before -> after | regs / smem B / local B
before -> after | seq. similarity | main opcode-class deltas (after -
before) |
|---|---|---|---|---|---|
| `decode_fp8_q1:q1_flat_xform2:main` | B200 | 4304 -> 4192 | 123 / 1024
/ 0 -> 122 / 1024 / 0 | 0.39 | mbar -34, ldc -33, ialu -30, other -14,
nop -2 |
| `decode_fp8_q1:q1_paged_xform2:main` | B200 | 4632 -> 4528 | 128 /
1024 / 0 -> 127 / 1024 / 0 | 0.34 | ialu -46, mbar -38, ldc -34, local
-18, cmp +16 |
| `decode_m16:bfloat16:bfloat16:flat:main` | B200 | 4120 -> 3952 | 127 /
1024 / 0 -> 117 / 1024 / 0 | 0.18 | ldc -63, mbar -50, ialu -42, other
-23, nop +5 |
| `decode_m16:bfloat16:bfloat16:paged:main` | B200 | 2536 -> 2480 | 126
/ 1024 / 0 -> 117 / 1024 / 0 | 0.18 | ldc -40, other +27, mbar -24, ialu
-22, cvt +6 |
| `decode_m16:bfloat16:float8_e4m3fn:flat:main` | B200 | 3760 -> 3704 |
127 / 1024 / 0 -> 117 / 1024 / 0 | 0.16 | ialu -45, mbar -30, other +8,
ldc +6, nop +5 |
| `decode_m16:bfloat16:float8_e4m3fn:paged:main` | B200 | 3808 -> 3752 |
127 / 1024 / 0 -> 117 / 1024 / 0 | 0.16 | ialu -44, mbar -30, other +10,
ldc +6, bra +3 |
| `decode_m16:float16:float16:flat:main` | B200 | 2496 -> 2432 | 126 /
1024 / 0 -> 117 / 1024 / 0 | 0.20 | ldc -35, mbar -24, ialu -20, other
+7, cvt +6 |
| `decode_m16:float16:float16:paged:main` | B200 | 2536 -> 2480 | 126 /
1024 / 0 -> 117 / 1024 / 0 | 0.18 | ldc -40, other +27, mbar -24, ialu
-22, cvt +6 |
| `decode_uniform_fp8:paged:main` | B200 | 3248 -> 3664 | 153 / 1024 / 0
-> 96 / 1024 / 0 | 0.16 | other +172, sel +137, ialu +90, mbar -31, cmp
+16 |
| `long_bf16_reverse:flat:gqa16:main` | B200 | 3168 -> 3080 | 128 / 1024
/ 0 -> 128 / 1024 / 0 | 0.69 | cvt -40, ialu -24, mbar -22, nop -4,
other +2 |
| `long_bf16_reverse:flat:gqa16:reduce` | B200 | 1072 -> 1016 | 60 /
1024 / 0 -> 60 / 1024 / 0 | 0.54 | ialu -16, falu -9, cmp -8, sel -7,
shfl -6 |
| `long_bf16_reverse:paged:gqa16:direct_group:main` | B200 | 2776 ->
2728 | 128 / 1024 / 0 -> 128 / 1024 / 0 | 0.45 | mbar -22, ialu -21, cvt
-16, nop +6, other +5 |
| `long_bf16_reverse:paged:gqa16:main` | B200 | 2832 -> 2776 | 128 /
1024 / 0 -> 128 / 1024 / 0 | 0.48 | mbar -22, ialu -21, cvt -16, other
+5, nop -2 |
| `long_bf16_reverse:paged:gqa16:reduce` | B200 | 1168 -> 1104 | 54 /
1024 / 0 -> 54 / 1024 / 0 | 0.23 | ialu -23, falu -11, cmp -10, sel -7,
shfl -6 |
| `long_bf16_reverse:paged:gqa8:main` | B200 | 3120 -> 3048 | 128 / 1024
/ 0 -> 128 / 1024 / 0 | 0.48 | ialu -23, mbar -22, cvt -16, other -12,
nop +1 |
| `long_bf16_reverse:paged:gqa8:reduce` | B200 | 1168 -> 1104 | 54 /
1024 / 0 -> 54 / 1024 / 0 | 0.25 | ialu -23, falu -11, cmp -10, sel -7,
shfl -6 |
| `prefill_union:bfloat16:bfloat16:flat:gqa0:any:main` | B200 | 4376 ->
4304 | 128 / 1024 / 0 -> 128 / 1024 / 0 | 0.68 | mbar -28, ialu -27,
other -17 |
| `prefill_union:bfloat16:bfloat16:flat:gqa16:any:main` | B200 | 4632 ->
4560 | 128 / 1024 / 0 -> 128 / 1024 / 0 | 0.54 | ialu -32, mbar -28,
other -15, bra +2, nop +2 |
| `prefill_union:bfloat16:bfloat16:flat:gqa8:any:main` | B200 | 4632 ->
4560 | 128 / 1024 / 0 -> 128 / 1024 / 0 | 0.54 | ialu -32, mbar -28,
other -15, bra +2, nop +2 |
| `prefill_union:bfloat16:bfloat16:paged:gqa0:any:main` | B200 | 4384 ->
4312 | 128 / 1024 / 0 -> 128 / 1024 / 0 | 0.65 | mbar -28, ialu -27,
other -18, nop +1 |
| `prefill_union:bfloat16:bfloat16:paged:gqa16:any:main` | B200 | 4640
-> 4576 | 128 / 1024 / 0 -> 128 / 1024 / 0 | 0.62 | ialu -28, mbar -28,
other -14, nop +6 |
| `prefill_union:bfloat16:bfloat16:paged:gqa16:causal_large:main` | B200
| 4688 -> 4624 | 128 / 1024 / 0 -> 128 / 1024 / 0 | 0.67 | ialu -28,
mbar -28, other -14, nop +6 |
| `prefill_union:bfloat16:bfloat16:paged:gqa16:causal_mask64:main` |
B200 | 4680 -> 4608 | 128 / 1024 / 0 -> 128 / 1024 / 0 | 0.70 | ialu
-28, mbar -28, other -14, nop -2 |
| `prefill_union:bfloat16:bfloat16:paged:gqa8:any:main` | B200 | 4640 ->
4576 | 128 / 1024 / 0 -> 128 / 1024 / 0 | 0.62 | ialu -28, mbar -28,
other -14, nop +6 |
| `prefill_union:bfloat16:float8_e4m3fn:flat:gqa0:any:main` | B200 |
4920 -> 5072 | 128 / 1024 / 0 -> 128 / 1024 / 0 | 0.46 | ialu +91, cvt
+44, mbar -24, bra +15, nop +10 |
| `prefill_union:bfloat16:float8_e4m3fn:paged:gqa0:any:main` | B200 |
4928 -> 5080 | 128 / 1024 / 0 -> 128 / 1024 / 0 | 0.45 | ialu +93, cvt
+44, mbar -24, bra +15, lds +7 |
| `prefill_union:float16:float16:flat:gqa0:any:main` | B200 | 4376 ->
4304 | 128 / 1024 / 0 -> 128 / 1024 / 0 | 0.68 | mbar -28, ialu -27,
other -17 |
| `prefill_union:float16:float16:paged:gqa0:any:main` | B200 | 4384 ->
4312 | 128 / 1024 / 0 -> 128 / 1024 / 0 | 0.65 | mbar -28, ialu -27,
other -18, nop +1 |
| `topk_select:main` | B200 | 496 -> 488 | 37 / 1024 / 0 -> 79 / 1024 /
0 | 0.09 | bra -40, sel +35, other +14, ldc -9, sts +8 |
| `decode_fp8_q1:q1_flat_xform2:main` | B300 | 4304 -> 4224 | 125 / 1024
/ 0 -> 124 / 1024 / 0 | 0.22 | mbar -34, ldc -34, ialu -19, other +11,
nop -3 |
| `decode_fp8_q1:q1_paged_xform2:main` | B300 | 4632 -> 4536 | 128 /
1024 / 0 -> 126 / 1024 / 0 | 0.15 | ialu -48, mbar -38, ldc -34, local
-18, cmp +16 |
| `decode_m16:bfloat16:bfloat16:flat:main` | B300 | 4120 -> 3984 | 127 /
1024 / 0 -> 118 / 1024 / 0 | 0.27 | ldc -63, mbar -50, ialu -40, other
+6, cvt +6 |
| `decode_m16:bfloat16:bfloat16:paged:main` | B300 | 2536 -> 2472 | 126
/ 1024 / 0 -> 118 / 1024 / 0 | 0.22 | ldc -46, mbar -24, other +23, ialu
-18, falu -4 |
| `decode_m16:bfloat16:float8_e4m3fn:flat:main` | B300 | 3760 -> 3712 |
127 / 1024 / 0 -> 118 / 1024 / 0 | 0.26 | ialu -35, mbar -30, other +7,
cvt +6, bra +3 |
| `decode_m16:bfloat16:float8_e4m3fn:paged:main` | B300 | 3808 -> 3760 |
127 / 1024 / 0 -> 118 / 1024 / 0 | 0.24 | ialu -35, mbar -30, other +7,
cvt +6, bra +3 |
| `decode_m16:float16:float16:flat:main` | B300 | 2504 -> 2432 | 126 /
1024 / 0 -> 118 / 1024 / 0 | 0.26 | ldc -41, mbar -24, ialu -20, other
+9, bra +3 |
| `decode_m16:float16:float16:paged:main` | B300 | 2536 -> 2472 | 126 /
1024 / 0 -> 118 / 1024 / 0 | 0.22 | ldc -46, mbar -24, other +23, ialu
-18, falu -4 |
| `decode_uniform_fp8:paged:main` | B300 | 3248 -> 3680 | 153 / 1024 / 0
-> 96 / 1024 / 0 | 0.26 | other +181, sel +137, ialu +98, mbar -31, cmp
+16 |
| `long_bf16_reverse:flat:gqa16:main` | B300 | 3040 -> 2952 | 128 / 1024
/ 0 -> 128 / 1024 / 0 | 0.76 | cvt -40, ialu -24, mbar -22, other -3,
nop +1 |
| `long_bf16_reverse:flat:gqa16:reduce` | B300 | 1072 -> 1008 | 60 /
1024 / 0 -> 60 / 1024 / 0 | 0.58 | ialu -16, falu -9, cmp -8, other -8,
sel -7 |
| `long_bf16_reverse:paged:gqa16:main` | B300 | 2632 -> 2568 | 128 /
1024 / 0 -> 128 / 1024 / 0 | 0.82 | ialu -22, mbar -22, cvt -16, other
-5, nop +1 |
| `long_bf16_reverse:paged:gqa16:reduce` | B300 | 1168 -> 1104 | 54 /
1024 / 0 -> 54 / 1024 / 0 | 0.27 | ialu -23, falu -11, cmp -10, sel -7,
shfl -6 |
| `long_bf16_reverse:paged:gqa8:main` | B300 | 2920 -> 2856 | 128 / 1024
/ 0 -> 128 / 1024 / 0 | 0.81 | mbar -22, ialu -19, cvt -16, other -7 |
| `long_bf16_reverse:paged:gqa8:reduce` | B300 | 1168 -> 1104 | 54 /
1024 / 0 -> 54 / 1024 / 0 | 0.29 | ialu -23, falu -11, cmp -10, sel -7,
shfl -6 |
| `prefill_union:bfloat16:bfloat16:flat:gqa0:any:main` | B300 | 4376 ->
4304 | 128 / 1024 / 0 -> 128 / 1024 / 0 | 0.76 | mbar -28, ialu -27,
other -16, nop -1 |
| `prefill_union:bfloat16:bfloat16:flat:gqa16:any:main` | B300 | 4632 ->
4560 | 128 / 1024 / 0 -> 128 / 1024 / 0 | 0.75 | ialu -28, mbar -28,
other -16 |
| `prefill_union:bfloat16:bfloat16:flat:gqa8:any:main` | B300 | 4632 ->
4560 | 128 / 1024 / 0 -> 128 / 1024 / 0 | 0.75 | ialu -28, mbar -28,
other -16 |
| `prefill_union:bfloat16:bfloat16:paged:gqa0:any:main` | B300 | 4384 ->
4312 | 128 / 1024 / 0 -> 128 / 1024 / 0 | 0.77 | mbar -28, ialu -27,
other -17 |
| `prefill_union:bfloat16:bfloat16:paged:gqa16:any:main` | B300 | 4640
-> 4568 | 128 / 1024 / 0 -> 128 / 1024 / 0 | 0.78 | ialu -28, mbar -28,
other -16 |
| `prefill_union:bfloat16:bfloat16:paged:gqa16:causal_large:main` | B300
| 4688 -> 4616 | 128 / 1024 / 0 -> 128 / 1024 / 0 | 0.79 | ialu -28,
mbar -28, other -16 |
| `prefill_union:bfloat16:bfloat16:paged:gqa16:causal_mask64:main` |
B300 | 4680 -> 4608 | 128 / 1024 / 0 -> 128 / 1024 / 0 | 0.79 | ialu
-28, mbar -28, other -16 |
| `prefill_union:bfloat16:bfloat16:paged:gqa8:any:main` | B300 | 4640 ->
4568 | 128 / 1024 / 0 -> 128 / 1024 / 0 | 0.78 | ialu -28, mbar -28,
other -16 |
| `prefill_union:bfloat16:float8_e4m3fn:flat:gqa0:any:main` | B300 |
4920 -> 5072 | 128 / 1024 / 0 -> 128 / 1024 / 0 | 0.47 | ialu +99, cvt
+44, mbar -24, bra +15, other -13 |
| `prefill_union:bfloat16:float8_e4m3fn:paged:gqa0:any:main` | B300 |
4928 -> 5072 | 128 / 1024 / 0 -> 128 / 1024 / 0 | 0.47 | ialu +96, cvt
+44, mbar -24, bra +15, other -11 |
| `prefill_union:float16:float16:flat:gqa0:any:main` | B300 | 4376 ->
4304 | 128 / 1024 / 0 -> 128 / 1024 / 0 | 0.76 | mbar -28, ialu -27,
other -16, nop -1 |
| `prefill_union:float16:float16:paged:gqa0:any:main` | B300 | 4384 ->
4312 | 128 / 1024 / 0 -> 128 / 1024 / 0 | 0.77 | mbar -28, ialu -27,
other -17 |
| `topk_select:main` | B300 | 496 -> 488 | 37 / 1024 / 0 -> 79 / 1024 /
0 | 0.09 | bra -40, sel +35, other +14, ldc -9, sts +8 |

Across the 57 pairs: 57 pairs, none instruction-identical; instruction
count after/before median 0.984 (min 0.940, max 1.133); mbarrier-class
delta range -50..0; integer-ALU delta range -48..99; MUFU delta nonzero
in 6 pairs (the three reducers, -3 each); local memory changed in 2
pairs; MMA-class delta nonzero in 2 pairs (uniform FP8 decode, +3);
register count changed in 20 pairs; static shared memory changed in 0
pairs; local memory nonzero after in 0 pairs The
per-arch base kernels of the long-prefill forwards pair with the single
shared program; the 9 shape-exact / private
snapshot variants that the TopK16-only dispatcher no longer routes
(decode topk32 / topk4-exact512 paged, the two
exact-shape FP8-KV Q1 decodes, the M64 GQA-16 flat prefill, the four
reverse-prefill topk4/topk8 programs) have no
counterpart and are not in the table.

Because kernel-body equality is not an applicable criterion for this
change, the validation of the
device code is the acceptance protocol below: every registered shape is
run on both architectures with
the previous kernels (source) and the delivered kernels (export) side by
side, correctness against the
fp32 reference on both arms, and paired CUPTI kernel time (same GPU,
cold L2, interleaved arms, steady
SM clock) with `before / after >= 0.97`, directional agreement within
0.05 and endpoint drift within
0.02 as the gates. Result: **153 of 163 (shape, arch) rows pass**; every
failing row is listed:

| row | arch | gate | values |
|---|---|---|---|
| serving_m3_prefill_tp8_b1_q8192_kv8192_h8_hkv1_k16_paged_bf16 | both |
correctness: per-row relative L2 | 0.02398 max / 0.01789 mean (bound
0.02), worst row 63944 of 65536; elementwise `out` (atol/rtol 1e-2) and
LSE pass; source and export bit-identical; identical on B200 and B300
(known, pre-existing: see "Long-prefill route accuracy") |
| coverage_prefill_mixed_fp8_b2_q64_kv512_h8_hkv2_k16_flat | both |
timing: directional disagreement | 0.085 (B200) / 0.097 (B300) > 0.05 on
a sub-10 us row; before/after 0.997 / 0.999 |
| prefill_fully_masked_row | both | timing: directional disagreement |
0.124 / 0.141 > 0.05 (sub-10 us row); before/after 0.986 / 0.984 |
| serving_m3_prefill_tp4_correctness_q17_kv257_h16_hkv1_k16_paged_bf16 |
B200 | timing: directional disagreement | 0.117 > 0.05 (sub-10 us row);
before/after 1.005 |
| prefill_flat_bf16_gqa16_ragged_batch | B300 | timing: directional
disagreement | 0.069 > 0.05; before/after 0.998 |
| perf_prefill_bf16_b1_q32768_kv32768_h64_hkv4_k16_flat_varlen | B300 |
timing: endpoint drift | 0.054 > 0.02 at 1.5 GHz sustained clock;
before/after 1.0014, directional 0.0002; second sample on the same GPU:
drift 0.052, before/after 0.9995, directional 0.0005, clocks 1500-1800
MHz |
| perf_prefill_bf16_b1_q65536_kv65536_h64_hkv4_k16_flat_varlen | B300 |
timing: endpoint drift | 0.029 > 0.02 at 1.47 GHz; before/after 1.0005,
directional 0.0015; second sample: drift 0.027, before/after 1.0016,
directional 0.0008, clocks 1470-1507 MHz |

The directional-disagreement rows are short kernels whose two arm orders
disagree by more than 5 % while
the before/after ratio itself is within 2 % of 1; the endpoint-drift
rows are the longest B300 kernels
(multi-second samples at a reduced sustained clock). None of the timing
rows fails correctness.

**Structural rows.** Three programs are, beyond the recompilation above,
different kernels from the
snapshot: the two paged long-prefill reducers regenerate to the
generator's current segment-combine
variants (the snapshot shipped an older combine), and the uniform FP8
Q/K/V decode program is the
generator's current 512-thread kernel (the snapshot vendored an earlier
384-thread build). The
uniform FP8 kernel also loses a `setmaxnreg` register plan that could
never be granted (it summed
to 79,872 registers on a 65,536-register file) and that the compiler had
been dropping, so the
generated register allocation is now what actually ran. Every benchmark
row that reaches these
programs is in the acceptance above (paired CUPTI time, same GPU, cold
L2); all of them pass.

**Generator fix found by the export run.** The first regenerated Top-K16
selection program never
terminated: its warp-level merge step was written as a loop over
compile-time widths, and the
generator rendered that loop with a frozen predicate (`while (1)`
without an exit), so the kernel spun
at full GPU utilisation on the first shape on both architectures. The
merge now iterates its widths
explicitly (the shipped program renders the same straight-line step as
the previous snapshot, see the
`topk` row above), and the generator refuses to emit a loop whose
predicate is a compile-time constant
without a `break`, so a recurrence fails at generation time instead of
hanging a GPU. The Top-K
semantics, interface and tests are unchanged.

**Long-prefill route accuracy (finding, no behaviour change).** The
regeneration run adds two coverage
coordinates for the paged GQA-16 long-prefill routes that no existing
test or benchmark reaches (more
than 64 pages; the SM100 direct-group variant at 8192 pages): `b1 /
q8192 / kv8320` and
`b1 / q8192 / kv1048576`, 16 Q heads / 1 KV head, bf16, causal, topk 16.
On both architectures the
regenerated programs produce bit-identical output to the pre-change
kernels, `out` passes the
elementwise bf16 check this repository's tests apply to the route
(atol/rtol 1e-2; 0 of 16.7M elements
outside) and LSE passes (atol 0.05 / rtol 0.01), but the per-row
relative L2 error against an fp32
reference is 0.034 max / 0.024 mean, above the 0.02 bound the
generator's acceptance contract applies
to bf16 attention rows. The cause is the route's design: the
long-prefill forward writes FP8 partial
accumulators that the reducer combines, so this is the production
kernel's numerics, not a
regeneration defect. Nothing changes here (kernels and test tolerances
as before; the two coordinates
are parity rows in the generator's acceptance: route reached, finite
output, source == export bitwise;
the contract bound is not loosened). Posted on #5778 as a question: is
the FP8-partial accuracy the
intended contract, or is a bf16-partial reducer variant wanted as a
follow-up (device-code change)? The same signature appears on the
existing paged
GQA-8 long-prefill coordinate `b1 / q8192 / kv8192`, 8 Q heads / 1 KV
head (per-row relative L2 0.024 max / 0.018
mean, bit-identical on B200 and B300, elementwise and LSE within
tolerance), so three long-route coordinates carry it. On that
coordinate the generator's acceptance records the row as failing the
0.02 bound deterministically on both
architectures (0.02398, worst row 63944), bit-identical between the
previous and regenerated kernels; the
corresponding end-to-end test in the generator's own suite fails at the
base revision for the same reason, so
this is a known, pre-existing property of the route and not a change
made here.

**Measurement note.** The long flat-varlen prefill benchmark rows (16K
to 512K tokens) run multi-second kernels per
sample and settle at 1.3-1.9 GHz on both B200 (max 1965 MHz) and B300
(max 2032 MHz) while every short row holds
the maximum clock. Both arms of a row are timed interleaved at the same
clock, so the generator's acceptance for
this family admits a sustained SM clock down to 1.2 GHz (0.6 of the
maximum) for those rows; the ratios in the
table are from that regime.

**Numerical tests.** `pytest tests/msa_ops/test_blackwell_msa_sm100.py
tests/msa_ops/test_blackwell_msa_routes.py
tests/msa_ops/test_blackwell_msa_topk_dispatch.py
tests/msa_ops/test_msa_ops.py tests/msa_ops/test_msa_topk_per_token.py
tests/jit/test_blackwell_msa_jit.py`:
B200 (SM100) 43 passed, 86 skipped, 0 failed; B300 (SM103) 43 passed, 86
skipped (the skips are the SM120/SM121-only `msa_ops` tests), 0 failed.

**Benchmark (production routes).** The generator's route benchmarks for
this family (21 registered names;
the 9 shape-exact / private variants have no route any more and no
benchmark) were run before (previous kernels) and
after (regenerated kernels) on the same GPU in two orders (before/after,
then after/before), paired CUPTI kernel time
with cold L2; ratio = before / after for time metrics and after / before
for throughput metrics (> 1 = regenerated faster).
**16 names comparable, 0 rows below 0.98 on either architecture**; the 5
non-comparable names are properties of the
previous kernels or the fixture, listed with their reason:

| route benchmark | B200 before -> after (pair 1) | ratio | B200 pair 2
| ratio | B300 pair 1 | ratio | B300 pair 2 | ratio |
|---|---|---|---|---|---|---|---|---|
| `customer_m3_uniform_fp8_q1` | not comparable: before: build rejected
(ungrantable register plan, see Structural rows); after 0.465 (B200) /
0.510 (B300) roofline efficiency | | | | | | | |
| `customer_m3_uniform_fp8_q2_q32` | not comparable: before: build
rejected (same); after 0.531 / 0.651 roofline efficiency | | | | | | | |
| `decode_bf16` | 4948 GB/s -> 4948 GB/s | 1.0000 | 4946 GB/s -> 4948
GB/s | 1.0004 | 4940 GB/s -> 4940 GB/s | 1.0000 | 4940 GB/s -> 4940 GB/s
| 1.0000 |
| `decode_bf16_m16_persistent_rollover` | not comparable: no CUPTI
timing metadata on either side (benchmark fixture), not comparable | | |
| | | | |
| `decode_bf16_paged_q8_kv65536_direct` | 0.3362 gpu_ms -> 0.3362 gpu_ms
| 1.0000 | 0.3362 gpu_ms -> 0.3361 gpu_ms | 1.0003 | 0.3398 gpu_ms ->
0.3398 gpu_ms | 1.0000 | 0.3398 gpu_ms -> 0.3398 gpu_ms | 1.0000 |
| `decode_bf16_q1_pr3655_b256_persistent` | 0.1808 gpu_ms -> 0.1811
gpu_ms | 0.9983 | 0.181 gpu_ms -> 0.1815 gpu_ms | 0.9972 | 0.1824 gpu_ms
-> 0.1823 gpu_ms | 1.0005 | 0.1821 gpu_ms -> 0.1817 gpu_ms | 1.0022 |
| `decode_bf16_q4_b128_persistent` | 0.2366 gpu_ms -> 0.2375 gpu_ms |
0.9962 | 0.2368 gpu_ms -> 0.237 gpu_ms | 0.9992 | 0.2406 gpu_ms ->
0.2404 gpu_ms | 1.0008 | 0.2399 gpu_ms -> 0.2402 gpu_ms | 0.9988 |
| `decode_bf16_q4_pr3655_trtllm_decode` | 0.0183 gpu_ms -> 0.0184 gpu_ms
| 0.9946 | 0.0184 gpu_ms -> 0.0185 gpu_ms | 0.9946 | 0.0179 gpu_ms ->
0.0178 gpu_ms | 1.0056 | 0.0179 gpu_ms -> 0.0178 gpu_ms | 1.0056 |
| `decode_fp16` | 4420 GB/s -> 4419 GB/s | 0.9998 | 4420 GB/s -> 4420
GB/s | 1.0000 | 4411 GB/s -> 4410 GB/s | 0.9998 | 4410 GB/s -> 4411 GB/s
| 1.0002 |
| `decode_fp16_paged_q4` | 0.0952 gpu_ms -> 0.0952 gpu_ms | 1.0000 |
0.0952 gpu_ms -> 0.0952 gpu_ms | 1.0000 | 0.0948 gpu_ms -> 0.0948 gpu_ms
| 1.0000 | 0.0948 gpu_ms -> 0.0947 gpu_ms | 1.0011 |
| `decode_fp8` | 922 GB/s -> 923 GB/s | 1.0011 | 922 GB/s -> 923 GB/s |
1.0011 | 956 GB/s -> 956 GB/s | 1.0000 | 956 GB/s -> 956 GB/s | 1.0000 |
| `decode_fp8_flat_q1_xform2` | 1.507 x -> 1.507 x | 1.0000 | 1.507 x ->
1.507 x | 1.0000 | 1.511 x -> 1.511 x | 1.0000 | 1.511 x -> 1.511 x |
1.0000 |
| `decode_fp8_paged_q1_xform2` | 1.51 x -> 1.51 x | 1.0000 | 1.51 x ->
1.51 x | 1.0000 | 1.51 x -> 1.51 x | 1.0000 | 1.51 x -> 1.51 x | 1.0000
|
| `decode_m16_bf16` | 4966 GB/s -> 4966 GB/s | 1.0000 | 4965 GB/s ->
4966 GB/s | 1.0002 | 4958 GB/s -> 4958 GB/s | 1.0000 | 4958 GB/s -> 4958
GB/s | 1.0000 |
| `long_prefill_selected_block` | 0.8095 kernel_ms -> 0.7894 kernel_ms |
1.0255 | 0.8213 kernel_ms -> 0.8295 kernel_ms | 0.9901 | 0.7168
kernel_ms -> 0.7073 kernel_ms | 1.0134 | 0.7118 kernel_ms -> 0.7154
kernel_ms | 0.9950 |
| `paged_long_prefill_selected_block` | 0.136 kernel_ms -> 0.1361
kernel_ms | 0.9993 | 0.1361 kernel_ms -> 0.136 kernel_ms | 1.0007 |
0.1201 kernel_ms -> 0.12 kernel_ms | 1.0008 | 0.1201 kernel_ms -> 0.1201
kernel_ms | 1.0000 |
| `paged_long_prefill_selected_block_tp4` | 0.2556 kernel_ms -> 0.2553
kernel_ms | 1.0012 | 0.2554 kernel_ms -> 0.2553 kernel_ms | 1.0004 |
0.2237 kernel_ms -> 0.224 kernel_ms | 0.9987 | 0.2237 kernel_ms ->
0.2237 kernel_ms | 1.0000 |
| `prefill_bf16` | 720 TFLOPS -> 720 TFLOPS | 1.0000 | 720 TFLOPS -> 720
TFLOPS | 1.0000 | 903 TFLOPS -> 902 TFLOPS | 0.9989 | 903 TFLOPS -> 903
TFLOPS | 1.0000 |
| `serving_prefill8k_tp4_bf16` | 0.2211 gpu_ms -> 0.2211 gpu_ms | 1.0000
| 0.2211 gpu_ms -> 0.2212 gpu_ms | 0.9995 | 0.1866 gpu_ms -> 0.1868
gpu_ms | 0.9989 | 0.1871 gpu_ms -> 0.1869 gpu_ms | 1.0011 |
| `serving_prefill8k_tp8_bf16` | not comparable: correctness failed on
both sides = the pre-existing row above | | | | | | | |
| `topk` | not comparable: before: hangs under the route benchmark (30 s
watchdog) on both GPUs, both orders; after 17 GB/s | | | | | | | |

The `long_prefill_selected_block` pair-1 / pair-2 spread (1.0255 /
0.9901 on B200, 1.0134 / 0.9950 on B300) is the
order effect of that benchmark's input rebuild, not a kernel difference.
`benchmarks/bench_blackwell_msa_sm100.py` was not
run (it needs the external MiniMax reference checkout); the per-shape
acceptance rows above cover the same routes.

`pre-commit` (ruff format + check 0.12.8 on the delivered Python) clean.

## Not in this PR

- The 9 shape-exact variants listed under behaviour changes 1 and 2 are
deleted, not generalised.
If the maintainers want the topk 32 / 8 / 4 coordinates served, the
follow-up is a runtime `topk`
parameter of the M16 decode kernel (device-code change), not a return of
the per-shape kernels.
- Two of them (`decode_m16_bf16_paged_topk32`,
`decode_m16_bf16_paged_topk4_exact512`) have no
generator program any more; the four reverse-prefill variants have
programs but no production
  call site. Neither can be regenerated through this PR's path.
- Stride-carrying K / V descriptors: the TMA descriptors derive K / V
strides from the shapes, so
the bindings keep the contiguity check on K / V; binding them in place
from a strided pool is a
  kernel / binding ABI change.
- The generator-side programs that only the removed routes used are
retained upstream for now and
  are not part of this delivery.
- The GQA-8 and GQA-16 prefill-union programs (flat and paged pairs)
differ only in six named
schedule constants (fold group, tokens per stage, Q tile, the Q-to-K
staging bytes / stride, total
shared memory) and are SASS-different by design; they stay two programs
each (about 4.6K lines).
Folding them into one source with two compile-line instantiations needs
the generator to emit the
  derived shared-memory constants as overridable macros; follow-up.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added Blackwell MSA attention kernel variants with support for scaled
inputs, split-task result aggregation, and additional workload routes.
* Added validated launch paths for supported CUDA targets, including
`sm100a` and `sm103a`.
* **Bug Fixes**
* Improved handling of split outputs and LSE values, including
temperature-LSE results.
* Improved top-k block selection while preserving forced begin and end
blocks.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [66c7ad1](https://github.com/flashinfer-ai/flashinfer/commit/66c7ad1fca45d7e7b1accb6fa1117ce17007b9ad)

- **作者**: eigen
- **时间**: 2026-10-03T21:13:28Z
- **提交信息**: refactor(cake_kimi_k3_vision_tower): regenerate as one source per program (#5884)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

Closes #5774

## Summary

Regenerates `flashinfer/experimental/kimi_k3_vision_tower`
(Cake-generated Kimi-K3 vision tower:
MoonViT-3D encoder + PatchMergerV2, SM100 / SM103) from its producer
with the per-architecture
duplication removed and a leaner host path. The GEMM, merge and RMSNorm
device code is unchanged
instruction for instruction (see Validation); the attention programs
move to the by-value
tensor-map ABI the rest of the family already uses; the delivery layout,
the registry, the host
bindings and the Python host path change.

## What changed

- **One source per program, shared by SM100 and SM103.** The 67 GEMM /
merge / RMSNorm programs
live once under `csrc/cake_kimi_k3_vision_tower/`; the only
architecture-dependent statement
(the shared-memory base materialisation) is emitted under an exact
`__CUDA_ARCH__` guard. The
`sm_100a/` and `sm_103a/` trees (300 files) are deleted. The JIT loader
compiles a source with
the exact flag set of the device it runs on and keys the cached library
by `<program>_<arch>`.
- **Attention programs per architecture.** The packed-varlen attention
kernel genuinely differs
between SM100 and SM103 (SM103 drains its scores with `tcgen05.ld.red`;
four of its forms are
selected on SM103 only), so its 14 programs stay architecture-specific
and each `MODULES`
record lists the one architecture it is built for. They now take their
tensor maps as
`__grid_constant__` parameters like every other program: the separate
descriptor-preparation
entry, the per-plan descriptor workspace and the `prepared_tma` state
are gone.
- **Registry.** `cake_jit.py` lists each program once with the
architectures it serves and its
closure identity per architecture, one argument plan per program kind
(`ARG_PLANS`, five
entries instead of 148 copies) and a per-architecture kernel-key table
(`KERNELS`). The
  3.9K-line per-module literal is replaced by these three tables.
- **Host path (`cake_backend.py`).** Token-sized workspaces are
allocated with `torch.empty`
(only the stream-K counters and the never-dereferenced dummies are
zeroed); device capability
and SM count are queried once per device; RoPE tables and position rows
are used in place
instead of copied; weights must be contiguous and are referenced, not
copied; the 22 tile
configurations the production rule never launches are removed (28
remain), together with the
  dead half-route exclusion and RoPE-base tables.
- **Tests.** The 1.3K lines of per-row kernel-key and attention-geometry
literals and the
registry-structure asserts are replaced by one behavioural test that
plans every contract and
coverage row on the CPU and checks each selected kernel key against the
registry for the
device's architecture; the host-policy, oracle and graph-replay tests
are unchanged.

Net (generated sources + package modules): 180,425 -> 99,883 lines
(-80,542, -44.6 %), 305 -> 167 files; 81 programs (67 shared by both
architectures, 14 attention programs per architecture).

## Validation

**Device code equivalence (mechanical steps).** For each of the 67
shared programs x 2
architectures the SASS of the regenerated build equals the SASS of the
previous per-architecture
file after normalising the kernel symbol / namespace hash (compiled with
the repository's JIT
flags):

| program kind | programs | sm_100a | sm_103a |
|---|---|---|---|
| GEMM (`pos`, `norm_qkv_rope`, `residual_wo`, `norm_gelu`,
`residual_fc1`, `gelu_erf`, `rmsnorm`; production + PDL-early + half-N
twins) | 64 | equal | equal |
| `attention_merge` | 1 | equal | equal |
| `merge` | 1 | equal | equal |
| `rmsnorm_apply` | 1 | equal | equal |

The 14 attention programs change ABI (pointer + descriptor prefetch ->
`__grid_constant__`
without prefetch) and are covered by the numerical tests and the per-row
timing below, not by
SASS equality.

**Numerical tests.** `pytest
tests/experimental/test_cake_kimi_k3_vision_tower.py` on a B200
(40 passed) and a B300 (40 passed; the SM103-only attention forms are
reachable
there only).

**Performance.** Paired CUPTI before/after on the same GPU over the
family's 22 benchmark rows
(19 timed, 3 correctness smoke rows), every row `before/after >= 0.98`:

Export-protocol measurement of the regenerated route against the Cake
source route (paired CUDA-graph replay, 3 counterbalanced groups, 100
reportable calls per arm and group; rule: every row >= 0.97
source/export, endpoint drift <= 0.02, directional disagreement <=
0.02):

sm_100a (B200, 29/29 rows pass, geomean 1.0005, min 0.9892, no row below
0.98):

| row | tag | source ms | export ms | source/export | correctness |
gates |
|---|---|---:|---:|---:|---|---|
| `img_224__sm_100a` | perf | 0.9356 | 0.9420 | 0.9932 | pass | valid |
| `img_336__sm_100a` | perf | 1.2997 | 1.2997 | 1.0000 | pass | valid |
| `img_448__sm_100a` | perf | 1.4853 | 1.4890 | 0.9975 | pass | valid |
| `img_640x480__sm_100a` | perf | 2.2847 | 2.2858 | 0.9995 | pass |
valid |
| `img_800x600__sm_100a` | perf | 3.4463 | 3.4381 | 1.0024 | pass |
valid |
| `img_1024x768__sm_100a` | perf | 5.8079 | 5.8112 | 0.9994 | pass |
valid |
| `img_1280x720__sm_100a` | perf | 7.1722 | 7.1852 | 0.9982 | pass |
valid |
| `img_1920x1080__sm_100a` | perf | 22.9858 | 23.0414 | 0.9976 | pass |
valid |
| `doc_1240x1754__sm_100a` | perf | 25.1258 | 25.1281 | 0.9999 | pass |
valid |
| `img_2560x1440__sm_100a` | perf | 59.1650 | 59.1166 | 1.0008 | pass |
valid |
| `img_3840x2160__sm_100a` | perf | 252.9382 | 252.9527 | 0.9999 | pass
| valid |
| `img_max_4096sq__sm_100a` | perf | 575.5627 | 575.5249 | 1.0001 | pass
| valid |
| `batch4_1024x768__sm_100a` | perf | 22.4663 | 22.4961 | 0.9987 | pass
| valid |
| `batch8_448__sm_100a` | perf | 7.5630 | 7.5611 | 1.0003 | pass | valid
|
| `mixed_1080p_xga_448_336__sm_100a` | perf | 29.9150 | 29.8728 | 1.0014
| pass | valid |
| `video_720p_4f__sm_100a` | perf | 58.2437 | 58.2297 | 1.0002 | pass |
valid |
| `video_1080p_4f__sm_100a` | perf | 249.0077 | 249.0232 | 0.9999 | pass
| valid |
| `video_720p_32f__sm_100a` | perf | 457.9101 | 457.5514 | 1.0008 | pass
| valid |
| `video_480p_64f__sm_100a` | perf | 159.9934 | 160.0199 | 0.9998 | pass
| valid |
| `smoke_2x2__sm_100a` | correctness | 0.9453 | 0.9010 | 1.0492 | pass |
valid |
| `smoke_ragged__sm_100a` | correctness | 1.0713 | 1.0830 | 0.9892 |
pass | valid |
| `smoke_t3__sm_100a` | correctness | 1.0896 | 1.0973 | 0.9930 | pass |
valid |
| `cov_batch11_224__sm_100a` | coverage | 2.8209 | 2.7964 | 1.0088 |
pass | valid |
| `cov_img_476x476__sm_100a` | coverage | 1.7328 | 1.7439 | 0.9936 |
pass | valid |
| `cov_img_2436x392__sm_100a` | coverage | 7.4420 | 7.4912 | 0.9934 |
pass | valid |
| `cov_img_3948x700__sm_100a` | coverage | 36.0553 | 36.0216 | 1.0009 |
pass | valid |
| `cov_img_2324x140__sm_100a` | coverage | 2.2628 | 2.2669 | 0.9982 |
pass | valid |
| `cov_img_4060x924__sm_100a` | coverage | 59.0579 | 59.0589 | 1.0000 |
pass | valid |
| `cov_img_3108x2716__sm_100a` | coverage | 253.1507 | 253.2566 | 0.9996
| pass | valid |

sm_103a (B300, 29/29 rows pass, geomean 1.0033, min 0.9891, no row below
0.98):

| row | tag | source ms | export ms | source/export | correctness |
gates |
|---|---|---:|---:|---:|---|---|
| `img_224__sm_103a` | perf | 0.9023 | 0.9080 | 0.9937 | pass | valid |
| `img_336__sm_103a` | perf | 1.2298 | 1.2326 | 0.9977 | pass | valid |
| `img_448__sm_103a` | perf | 1.4173 | 1.4171 | 1.0002 | pass | valid |
| `img_640x480__sm_103a` | perf | 2.1366 | 2.1398 | 0.9985 | pass |
valid |
| `img_800x600__sm_103a` | perf | 3.3374 | 3.3378 | 0.9999 | pass |
valid |
| `img_1024x768__sm_103a` | perf | 5.8524 | 5.8510 | 1.0002 | pass |
valid |
| `img_1280x720__sm_103a` | perf | 7.2059 | 7.2039 | 1.0003 | pass |
valid |
| `img_1920x1080__sm_103a` | perf | 22.1410 | 22.1400 | 1.0000 | pass |
valid |
| `doc_1240x1754__sm_103a` | perf | 23.9330 | 23.8979 | 1.0015 | pass |
valid |
| `img_2560x1440__sm_103a` | perf | 55.0049 | 54.9996 | 1.0001 | pass |
valid |
| `img_3840x2160__sm_103a` | perf | 230.2740 | 230.2820 | 1.0000 | pass
| valid |
| `img_max_4096sq__sm_103a` | perf | 524.5124 | 524.7609 | 0.9995 | pass
| valid |
| `batch4_1024x768__sm_103a` | perf | 21.6185 | 21.6007 | 1.0008 | pass
| valid |
| `batch8_448__sm_103a` | perf | 7.7817 | 7.7744 | 1.0010 | pass | valid
|
| `mixed_1080p_xga_448_336__sm_103a` | perf | 29.0024 | 29.0008 | 1.0001
| pass | valid |
| `video_720p_4f__sm_103a` | perf | 53.9730 | 53.9932 | 0.9996 | pass |
valid |
| `video_1080p_4f__sm_103a` | perf | 226.3635 | 226.4067 | 0.9998 | pass
| valid |
| `video_720p_32f__sm_103a` | perf | 426.8428 | 427.1117 | 0.9994 | pass
| valid |
| `video_480p_64f__sm_103a` | perf | 154.0367 | 153.9943 | 1.0003 | pass
| valid |
| `smoke_2x2__sm_103a` | correctness | 1.0043 | 0.8872 | 1.1320 | pass |
valid |
| `smoke_ragged__sm_103a` | correctness | 1.0367 | 1.0445 | 0.9926 |
pass | valid |
| `smoke_t3__sm_103a` | correctness | 1.0520 | 1.0594 | 0.9930 | pass |
valid |
| `cov_batch11_224__sm_103a` | coverage | 2.8607 | 2.8613 | 0.9998 |
pass | valid |
| `cov_img_476x476__sm_103a` | coverage | 1.6650 | 1.6555 | 1.0058 |
pass | valid |
| `cov_img_2436x392__sm_103a` | coverage | 7.3840 | 7.3966 | 0.9983 |
pass | valid |
| `cov_img_3948x700__sm_103a` | coverage | 34.3163 | 34.3120 | 1.0001 |
pass | valid |
| `cov_img_2324x140__sm_103a` | coverage | 2.1230 | 2.1463 | 0.9891 |
pass | valid |
| `cov_img_4060x924__sm_103a` | coverage | 54.9277 | 54.8507 | 1.0014 |
pass | valid |
| `cov_img_3108x2716__sm_103a` | coverage | 230.5308 | 230.5706 | 0.9998
| pass | valid |

Paired before/after benchmark
(`benchmarks/bench_cake_kimi_k3_vision_tower.py`, base tree vs this PR,
19 contract rows, one process per architecture running base, PR, PR,
base). The first base/PR pair is tabulated; on the B200 all 19 rows are
`before/after >= 0.98` (min 0.9813 `img_2560x1440`, max 1.0299
`img_1920x1080`). The second pair, taken after two full sweeps, has four
B200 rows at 0.91-0.98 (`img_2560x1440` 0.9116, `video_720p_4f` 0.9768,
`video_1080p_4f` 0.9665, `video_480p_64f` 0.9686); that is an order
effect of running both trees' sweeps back to back in one process (the
same rows measure 0.9998-1.0008 in the counterbalanced graph-replay
protocol above and the GEMM code is identical), reported here rather
than dropped. On the B300 all 19 rows are `before/after >= 0.98` in both
pairs (first pair min 0.9818 `video_720p_4f`, max 1.0317
`video_720p_32f`; second pair 0.9836-1.0170).

| row | sm_100a before (ms) | after (ms) | ratio | sm_103a before (ms) |
after (ms) | ratio |
|---|---:|---:|---:|---:|---:|---:|
| `img_224` | 0.9439 | 0.9373 | 1.0070 | 0.9024 | 0.9031 | 0.9991 |
| `img_336` | 1.3012 | 1.2995 | 1.0013 | 1.2310 | 1.2290 | 1.0016 |
| `img_448` | 1.4920 | 1.4887 | 1.0022 | 1.4179 | 1.4158 | 1.0015 |
| `img_640x480` | 2.2914 | 2.2916 | 0.9999 | 2.1302 | 2.1271 | 1.0015 |
| `img_800x600` | 3.4345 | 3.4704 | 0.9896 | 3.3971 | 3.3691 | 1.0083 |
| `img_1024x768` | 5.8918 | 5.8226 | 1.0119 | 5.9306 | 5.9190 | 1.0020 |
| `img_1280x720` | 7.1643 | 7.2004 | 0.9950 | 7.2592 | 7.2777 | 0.9975 |
| `img_1920x1080` | 23.3180 | 22.6405 | 1.0299 | 22.4327 | 22.2481 |
1.0083 |
| `doc_1240x1754` | 25.2527 | 25.5189 | 0.9896 | 24.1190 | 24.2053 |
0.9964 |
| `img_2560x1440` | 59.8769 | 61.0165 | 0.9813 | 55.2844 | 55.5357 |
0.9955 |
| `img_3840x2160` | 257.2440 | 254.3495 | 1.0114 | 228.0710 | 228.9242 |
0.9963 |
| `img_max_4096sq` | 578.4814 | 581.3074 | 0.9951 | 525.6168 | 524.2626
| 1.0026 |
| `batch4_1024x768` | 22.7316 | 22.3987 | 1.0149 | 21.7958 | 21.8559 |
0.9972 |
| `batch8_448` | 7.6137 | 7.5700 | 1.0058 | 7.8508 | 7.7640 | 1.0112 |
| `mixed_1080p_xga_448_336` | 30.6269 | 30.5298 | 1.0032 | 29.3229 |
29.5109 | 0.9936 |
| `video_720p_4f` | 57.5539 | 58.3000 | 0.9872 | 53.2703 | 54.2568 |
0.9818 |
| `video_1080p_4f` | 248.8034 | 249.9845 | 0.9953 | 225.3822 | 225.2509
| 1.0006 |
| `video_720p_32f` | 458.1415 | 457.7266 | 1.0009 | 425.9625 | 412.8605
| 1.0317 |
| `video_480p_64f` | 164.3622 | 164.0297 | 1.0020 | 148.6207 | 148.4880
| 1.0009 |

Per-call launch count unchanged (the attention descriptor-preparation
launch is gone).

`pre-commit` clean.

## Not in this PR (follow-ups)

- Folding the 64 GEMM programs into a parametrised source per variant
(tile, stage count and
K-loop bound are baked into the traced body today; four program pairs
differ only in the
  K-loop bound).
- One attention source for both architectures (the `tcgen05.ld.red`
drain needs an
  architecture-conditional lowering in the generator).
- Caching the encoded TMA descriptors across launches (a kernel-ABI
change; the by-value binding
  encodes them per launch, as the GEMM bindings already did).
- Dropping the two never-read kernel parameters (`pf_l2`, `probe`) from
142 programs (kernel-ABI
  change, changes SASS).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [c06c901](https://github.com/flashinfer-ai/flashinfer/commit/c06c901e9c6ee2892a4e2ba17ae4bda62121dd15)

- **作者**: eigen
- **时间**: 2026-10-03T21:13:12Z
- **提交信息**: refactor(cake_xqa): regenerate Thor (sm110) XQA as one templated source per program (#5872)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

Closes #5777

## Summary

Regenerates `flashinfer/experimental/sm110_xqa` (Cake-generated SM110 /
Thor XQA D512 tree attention:
`register_mma`, `register_mma_split`, `tmem` and `pair` families) from
its producer. The 40 per-GQA-ratio
`tmem` / `pair` kernel copies become 10 kernel templates, the per-file
helper preludes become one shared
header, the hand-written bindings become generated thin launchers, and
`manifest.json`, `validation.json`,
`RESULTS.md` and the unreachable `decode_merge` route are removed.
Device code is unchanged: every template
instantiation is the previous per-ratio kernel, instruction for
instruction (SASS table below).

## What changed

- **One kernel template per (cache mode, cluster form).** The 32
`tree_*_tmem*` and 8 `tree_fp8_*_pair_r*`
kernels differed from their siblings of another GQA ratio in the ratio
literal only (`actual_q * 8`,
`head_token / 8`, the Q tensor-map box). Each group is now one `template
<int kHeadGroupSize>` kernel with
explicit instantiations for 2, 4, 8 and 16; the generated launcher
dispatches on the `head_group_size`
argument the kernels already receive (`TVM_FFI_CHECK` on the set `{2, 4,
8, 16}`). The five register-MMA
  kernels take the ratio at runtime and stay one program each.
- **Shared helper header.** The 830-1,600-line helper prelude of every
kernel file is rendered once
(`csrc/sm110_xqa/cake_sm110_xqa_device_common.cuh`), the launchers'
helpers once
(`cake_sm110_xqa_host_common.cuh`): 15 kernel translation units + 15
launchers + 2 shared headers. The directory
carries the `.clang-format` opt-out the other generated `csrc`
directories use: the registry test checks the
generated sources' SHA-256, so the formatter hook must leave them byte
for byte.
- **Generated thin launchers on `tvm_ffi_utils.h`.**
`ffi::CUDADeviceGuard`, `get_stream`, the target's tensor
checks, by-value `CUtensorMap` parameters encoded per launch, the KV
cache record passed by value member by
member, one launch. Pointer arguments the kernels never dereference
(`q_cu_seq_lens` for uniform queries,
`attention_sinks`, `semaphores`, `scratch`) are bound as device
addresses with null allowed, exactly as the
  producer's own launcher passes them; no placeholder tensors.
- **Registry instead of manifest.** `jit.py` is written by the export:
`MODULES` (generated programs: two
translation units, nvcc flags, launch geometry, argument plan,
dispatched ratios), `FROZEN` (the routes kept
from the previous tree: sources, flags, content hash, launch facts) and
`ROUTES` (`<route>__<cluster form>` ->
program). The 1,500 never-read manifest lines, the SHA-256 pins and the
manifest validator are gone.
- **Host path.** `backend.py` resolves the program from `ROUTES`, binds
its `run(...)` by key in the recorded
argument-plan order, caches the device-capability guard per device and
allocates nothing per call; the
`torch.library` registration shims (identity functions in this tree) are
removed. Public signatures of
`prepare` / `attention` are unchanged; `PreparedAttention` gains
`program` and `inputs`.
- **Tests and docs.** The manifest-schema test file becomes five
registry/source-integrity tests (CPU); the GPU
test file keeps all numerical cases and reads `jit.FROZEN` /
`jit.ROUTES` where it read the manifest; the
ledger benchmark records the ledger hash and the program per row; the
README describes the registry.

Not regenerated (no producing program in the exporter): the four
`tcgen05` D512 tree routes and the D128 decode
producer with its single-partition specialization keep their frozen
kernel/binding pairs and are served through
`jit.FROZEN`; `decode_merge` is removed because the frozen decode
producer fuses its merge (`fused_merge: true`)
and the route was never loaded.

Net: 201,177 -> 57,520 lines (-143,657), 81 -> 53 files in the family
(tracked family files: kernels, bindings,
headers, Python, data); 11,862 of the remaining lines are the six frozen
`tcgen05` / decode pairs.

## Validation

**Device code (compile-only, CUDA 13.3 nvcc `-arch=sm_110a` /
`-arch=compute_110a`).** All 21 kernel translation
units (15 regenerated + 6 frozen) compile to PTX and cubin with the
registry's own flags; `cuobjdump
--dump-resource-usage`: 127-128 registers for the regenerated `tmem` /
`pair` / register-MMA programs, 146-147 for
the frozen `tcgen05` tree kernels, 89 for decode, no local memory. Every
program (kernel + launcher) also builds
through FlashInfer's JIT (`gen_sm110_xqa_module(name).build()`, 21/21).

**SASS equivalence.** `cuobjdump -sass` of the 45 previous kernels (32
`tmem`, 8 `pair`, 5 register-MMA, from the
base commit's modules) against the 45 regenerated kernels (10 templates
x {2, 4, 8, 16} + 5 register-MMA programs),
both built with the repository's JIT flags, kernel symbol normalised,
address comments dropped, labels renumbered
per kernel (the template instantiations share a translation unit, so
their raw label numbers continue across
kernels). **45 / 45 pairs are identical instruction for instruction**:
same instruction count, empty
opcode-histogram delta, same memory, TMA, `tcgen05` and
asynchronous-barrier opcodes. Per pair:

| previous kernel (base) | regenerated program, instantiation |
instructions | SASS |
|---|---|---:|---|
| `tree_fp16_contiguous_tmem_r2` / `_r4` / (r8) / `_r16` | FP16
contiguous `tmem`, (2,2,1) cluster, `<2>` / `<4>` / `<8>` / `<16>` |
5,801 / 5,800 / 5,808 / 5,808 | identical |
| `tree_fp16_contiguous_tmem_r2_q` / `_r4_q` / `_q` / `_r16_q` | FP16
contiguous `tmem`, (2,1,1) cluster, `<2>` .. `<16>` | 5,489 / 5,488 /
5,496 / 5,496 | identical |
| `tree_fp16_paged_tmem_r2` / `_r4` / (r8) / `_r16` | FP16 paged `tmem`,
(2,2,1), `<2>` .. `<16>` | 5,881 / 5,880 / 5,888 / 5,888 | identical |
| `tree_fp16_paged_tmem_r2_q` / `_r4_q` / `_q` / `_r16_q` | FP16 paged
`tmem`, (2,1,1), `<2>` .. `<16>` | 5,569 / 5,568 / 5,568 / 5,568 |
identical |
| `tree_fp8_contiguous_tmem_r2` / `_r4` / (r8) / `_r16` | FP8 contiguous
`tmem`, (2,2,1), `<2>` .. `<16>` | 5,793 / 5,792 / 5,808 / 5,808 |
identical |
| `tree_fp8_contiguous_tmem_r2_q` / `_r4_q` / `_q` / `_r16_q` | FP8
contiguous `tmem`, (2,1,1), `<2>` .. `<16>` | 5,401 / 5,400 / 5,408 /
5,408 | identical |
| `tree_fp8_paged_tmem_r2` / `_r4` / (r8) / `_r16` | FP8 paged `tmem`,
(2,2,1), `<2>` .. `<16>` | 5,873 / 5,872 / 5,880 / 5,880 | identical |
| `tree_fp8_paged_tmem_r2_q` / `_r4_q` / `_q` / `_r16_q` | FP8 paged
`tmem`, (2,1,1), `<2>` .. `<16>` | 5,633 / 5,632 / 5,648 / 5,648 |
identical |
| `tree_fp8_contiguous_pair_r2` / `_r4` / `_r8` / `_r16` | FP8
contiguous `pair`, `<2>` .. `<16>` | 5,961 / 5,960 / 5,968 / 5,968 |
identical |
| `tree_fp8_paged_pair_r2` / `_r4` / `_r8` / `_r16` | FP8 paged `pair`,
`<2>` .. `<16>` | 6,009 / 6,016 / 6,024 / 6,024 | identical |
| `tree_fp16_contiguous_mma` | FP16 contiguous register-MMA | 9,158 |
identical |
| `tree_fp16_paged_mma` | FP16 paged register-MMA | 9,911 | identical |
| `tree_fp16_paged_mma_split` | FP16 paged register-MMA, split-KV |
6,925 | identical |
| `tree_fp8_contiguous_mma` | FP8 contiguous register-MMA | 6,808 |
identical |
| `tree_fp8_paged_mma` | FP8 paged register-MMA | 7,947 | identical |

(The base kernel without a ratio suffix is the GQA-8 one; `_q` is the
(2,1,1)-cluster form. The six frozen
`tcgen05` / decode pairs are unchanged bytes and are not part of the
comparison.)

**CPU tests.** `pytest
tests/experimental/sm110_xqa/test_sm110_xqa_jit.py`: 5 tests. The first
four passed in the
proof run; the fifth,
`test_tree_family_grid_width_is_the_program_cluster_width`, was added
after review (it checks
every tree family's grid.x against the cluster width `jit.MODULES`
records for its programs; the previous `pair`
entry fails it) and has so far been run only outside pytest, with the
registry loaded and `torch` stubbed, where all
five pass; the CI run on this PR is its first pytest execution. `ruff
format --check` and
`ruff check` (the repository's pinned 0.12.8) clean on the delivered
Python; `pre-commit run` over the PR range
(clang-format, mypy, ruff) passes. The export's own audit of the
delivered tree: 15 programs, 15 distinct kernel bodies, no duplicated
kernel body, architecture copy or constant
clone left.

**GPU tests and benchmark: maintainer run requested.** We have no SM110
(Thor, compute capability 11.0) device
in our pool, so the GPU suite and the before/after benchmark of this PR
were not executed by us. The device code
is unchanged (SASS table above) and the host path is covered by the CPU
tests, but execution on Thor is the
acceptance evidence for this family. Requested from a maintainer with a
Thor and CUDA >= 13.0, from this PR's
checkout:

```bash
python -m pytest tests/experimental/sm110_xqa/test_sm110_xqa.py -q          # 341 collected GPU cases, FP32 oracle, atol=rtol=1e-2
python benchmarks/bench_sm110_xqa.py --warmup-ms 250 --output sm110-xqa-after.json
```

and the same benchmark from the base commit `909aa7b4050e` into
`sm110-xqa-before.json`. Acceptance: every one of
the 18 ledger rows (`benchmarks/sm110_xqa_shapes.json`: 15 D512 tree
rows at B1 / Q20 / Hq32 / Hkv4 / KV256 over
the cache modes and kernel families, 3 D128 decode rows) with
`before/after >= 0.98` on `median_us`; the
`program` field of each row names the regenerated program that served
it. We will attach the posted results to
this PR.

## Not in this PR (maintainer decision items from #5777)

- Retiring the nine superseded D512 routes (`tree_*` tcgen05 x4,
`tree_*_mma` x4, `tree_fp16_paged_mma_split`) and
the `kernel=` values `tcgen05` (D512), `register_mma`,
`register_mma_split`, `register_mma_auto`, making
`kernel="auto"` the default: the package's own measurements show `tmem`
/ `pair` 1.97-2.64x faster than
`tcgen05` on every D512 row and faster than `register_mma(_auto)` in
every cache mode. Kept selectable here.
- Regenerating the `tcgen05` D512 tree and D128 decode sources (no
producing program today): their frozen
  pairs stay as tracked, served through `jit.FROZEN`.
- Runtime GQA ratio inside the TMEM kernels (one instantiation instead
of four) and relaxed contiguity for the
TMA routes: both change device code; proposed as follow-ups with their
own before/after measurements.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [1b77e4c](https://github.com/flashinfer-ai/flashinfer/commit/1b77e4cd16df4de15044de3fa9e29966ed41e523)

- **作者**: eigen
- **时间**: 2026-10-03T21:07:23Z
- **提交信息**: perf(cake_dsv4_sparse_mla): speed up the SM120 DeepSeek-V4 NVFP4 sparse-MLA prefill kernels with exact-equivalent schedule changes (#6004)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

## 📌 Description

Round 2 of the `backend="cake"` SM120 DeepSeek-V4 NVFP4 sparse-MLA
**prefill** kernels (#5959): the same kernel family, re-scheduled with
exact-equivalent transforms only. Outputs and LSE are **bitwise
identical** to the kernels on `main` on every row of the 74-row coverage
set on both GB202 SKUs; the arithmetic, the softmax / accumulation
precision, the quantization and scale handling, the masking and the
boundary paths are unchanged.

What changed in the generated `csrc/cake_dsv4/sm_120a` prefill sources
(regenerated by the Cake exporter; the decode sources are kept from
`main`):

- The IO warps dequantize V (E2M1 to E4M3) for the four-tile kernels
while the math warps run QK, through a dedicated SMEM slot and the dead
ring stage behind a per-stage barrier.
- The eight math warps of a four-tile CTA run as two independent
four-warp groups, so one group's softmax overlaps the other group's
MMAs; the summation order of every value is the eight-warp form's, hence
bitwise identical.
- Per-stage index slots and a third cp.async ring stage for one-tile
CTAs with long candidate lists; L2 evict-first on the BF16 Q loads from
512 tokens (a runtime parameter, so there is still one kernel per form).
- A runtime grid-order parameter: candidate lists of at most 4 chunks
per block launch the grid as (head blocks, tokens) — only up to 65535
tokens, since that order puts the token count in grid.y (CUDA limit);
the binding applies the same cap before it builds the grid, and the
Python planner mirrors the rule
(`cake_sparse_mla_sm120_dsv4_nvfp4_plan_prefill_grid_head_blocks_first`,
parity-tested against the Cake planner).
- The E2M1 to F16 convert sites extract the `.b8` operand of
`cvt.rn.f16x2.e2m1x2` with the 32-bit unpack `mov.b32 {b, _, _, _}`
instead of `mov.b16 {b, _}`: ptxas of CUDA 12.9 mis-assembles the 16-bit
form at some sites of these kernels (the internal CI cu129 job on RTX
PRO 6000 saw sparse output deviations; CUDA 13.x was unaffected). Same
byte, same widened pair, so the numerics do not change. The eight
prefill translation units currently on `main` carry the 16-bit form as
well, so this PR also removes that exposure for the shipped kernel under
CUDA 12.9.
- Ring-depth forms of the chunk loops: the four-tile group-split loop
and the one-tile loop run one ring-stage body; the two-tile loop keeps
the ring-depth unroll. Per-group staged output stores for the four-tile
kernels.

Python: the planner gains the grid-order rule and the prefill op passes
the two new runtime parameters; the public API and the cache format are
unchanged.

## 🔍 Related Issues

Tracker: #4254. Follows #5959 (merged).

## 📈 Measurements

Paired same-process A/B against the prefill kernels on `main` (#5959) on
the same card: CUPTI active union of the single launch, cold L2,
ABAB/BABA groups of 3, pooled medians, clock-gated; 74 rows (T 128 / 512
/ 2048 / 8192 x H 16 / 32 / 64 / 128 x K 128 / 512, dual cache, NHD
layout, batched requests, K 256, page 32 / 128). Speedup = main time /
this PR's time.

| set (rows) | RTX PRO 6000 Blackwell SE | RTX 5090 |
|---|--:|--:|
| P: T 128 / 512 / 2048 / 8192 x H 16 / 32 / 64 / 128 x K 128 / 512 (32
rows) | 1.055x (0.998x – 1.137x) | 1.067x (1.001x – 1.147x) |
| D: dual cache, extra K 128 (page 2) / 512 (page 64) (24 rows) | 1.072x
(0.995x – 1.177x) | 1.071x (1.000x – 1.183x) |
| O: NHD layout (4 rows) | 1.055x (0.999x – 1.122x) | 1.054x (1.009x –
1.132x) |
| B: batched requests (4 rows) | 1.087x (1.019x – 1.173x) | 1.127x
(1.107x – 1.137x) |
| X256: K = 256 (6 rows) | 1.043x (0.998x – 1.148x) | 1.063x (0.998x –
1.131x) |
| XRP: page 32 / 128 (4 rows) | 1.081x (1.030x – 1.134x) | 1.143x
(1.138x – 1.150x) |
| all 74 rows (geomean) | **1.063x** | **1.075x** |

Rows faster than `main`: 70 / 74 on the RTX PRO 6000 (four one-tile H16
rows at 0.997x – 0.998x, reproduced with 6 groups) and 73 / 74 on the
RTX 5090 (one one-tile row at 0.998x); no row is more than 0.3 % slower.
Every row is bitwise identical to `main` (output and LSE).

## 🧪 Tests

- [x] `pytest
tests/attention/test_cake_sparse_mla_sm120_dsv4_nvfp4_prefill.py` on RTX
PRO 6000 Blackwell SE (sm_120a JIT, driver 595.84): 71 passed (+ 4
policy / planner-parity tests; the 71 include the 65536-token grid-cap
test)
- [x] `pytest tests/attention/test_cake_sparse_mla_sm120_dsv4_nvfp4.py`
(decode route, sources unchanged) on RTX PRO 6000: 83 passed, 1 skipped
- [x] the same two files on RTX 5090 (driver 615.36): prefill 71 passed
(+ 4 policy / planner-parity tests), decode 83 passed, 1 skipped
- [x] a 65536-token prefill (token-major grid by the grid.y cap) is
bitwise equal to its two 32768-token head-blocks-first halves on both
SKUs
- [x] the prefill test file inside the FlashInfer CI `cu129` image (nvcc
/ ptxas 12.9, torch 2.13+cu129) on RTX PRO 6000: 71 passed with these
sources (the previous head failed 24 of them there, matching the
internal pipeline); the same file in the `cu130` image: see the CI
matrix
- [x] compute-sanitizer synccheck + memcheck on the generating kernels
(both SKUs): 0 errors
- [x] pre-commit (ruff, ruff-format) with the upstream `main` hook pins

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## Reviewer Notes

The generated translation units are large by construction (one kernel
per head count x head tiles x cache form); the hand-written surface is
the planner rule, the op parameter plumbing and the tests. The only
behavioural change visible from Python is the grid order rule;
everything else is the kernels' schedule.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [eafe816](https://github.com/flashinfer-ai/flashinfer/commit/eafe816df2fea3d40d03e61842d8f7a383992292)

- **作者**: Chunan Zeng
- **时间**: 2026-10-03T21:03:36Z
- **提交信息**: perf(mla): prefetch split partials in the CuTe DSL MLA decode reducer (#5709)

## 📌 Description

The monolithic CuTe DSL MLA decode reducer (FP8 and FP16/BF16) walks the
splits in a runtime loop with one dependent L2 load per split, so its
cost grows with the split count (3.7 → 5.5 µs from 32 to 64 splits for
12 heads × 8 query tokens on SM107) and splitting long KV further does
not pay off.

**Reducer** (FP8 and FP16/BF16, shared)
- Each thread owns adjacent columns of its D band and issues its partial
loads for a set of splits up front (predicated, vectorized) before the
LSE phase, then accumulates from registers in split order, in groups of
four.
- Sets hold at most 64 splits and 128 floats per thread; larger
capacities issue later sets only when the row needs them.
- Every LSE weight slot is written (zero past the row's split count or
for a DCP rank with no valid key); the PDL dependents trigger moves to
kernel entry.
- Variable-Q, DCP, variable split-KV and `lse_scale` keep their
semantics.

### Why the reducer is faster

```text
Same partial-output data, different load schedule
(schematic timeline; widths are not measured)

BEFORE                                             time --->

  LSE weights   [ compute ][barrier]
  Split loads                      [load 0]   [load 1]   [load 2]
  Accumulate                               [A0]       [A1]       [A2] ...
                                   ^^^^^^^^   ^^^^^^^^   ^^^^^^^^
                                   exposed load waits, repeated per split

AFTER                                              time --->

  Split loads   [issue 0,1,2,...][.........in flight.........]
  LSE weights                  [ compute ][barrier]        |
                               <--- overlapped --->        |
  Registers                                                [ready]
  Accumulate                                                [A0 A1 A2 ...]
                                                            ^^^^^^^^^^^^^
                                                            register reads
                                                            between adds

  A_s = accumulate partial[s] * LSE_weight[s], in split order

  Per-thread column ownership (relative to one D band)

  BEFORE: t, t+128, t+256, t+384       AFTER: t*vec + [0 .. vec-1]
          |    |      |      |                            | | | |
          separate scalar loads                         vector load

  Before:  [LSE][wait][A0][wait][A1][wait][A2] ... [store]
  After:   [loads + LSE overlap][A0 A1 A2 ...][store]
                               <--- fewer exposed stalls --->

  One prefetched set: <= 64 splits, <= 128 partial floats/thread.
  More splits: repeat load + register accumulation for the next set.
  Invalid splits: masked loads + zero weights; no tail-data reads.
```

**Host heuristics** (`cute_dsl_mla_decode` and the `cute-dsl-monolithic`
planned backend)
- Split cap 32 → 48 (`_STATIC_REDUCER_MAX_SPLITS`); only reached at low
occupancy (`B * q_tiles <= 2` on 212 SMs).
- Reducer capacity is the covering power of two of the launched split
count (4..48) instead of a fixed 32, so launches with few splits don't
reserve registers for 32.
- Reducer bands: two while `rows * 4` fits in the SM count, else one.
Four bands leave one column per thread and measured 6–35% slower with
this reducer.

The second commit moves the now-identical FP8/FP16 reducer into
`MLAReducerMixin` (`mla_helpers.py`), with no functional change.

### Performance

SM107 (212 SMs),
`trtllm_batch_decode_with_kv_cache_mla(backend="cute-dsl")`,
`max_seq_len=1M` (split count fixed as under CUDA graphs), CUDA-graph
µs/call, cold KV, before → after:

| dtype | batch | q_len | heads | KV 4k | KV 16k | KV 60k | KV 128k |
|---|---|---|---|---|---|---|---|
| FP8 | 1 | 8 | 12 | 9.11 → 8.03 | 10.68 → 9.60 | 17.01 → 14.04 | 25.98
→ 20.69 |
| FP8 | 1 | 1 | 12 | 8.13 → 6.51 | 9.75 → 8.17 | 15.89 → 12.66 | 24.62 →
19.25 |
| FP8 | 1 | 1 | 128 | 9.20 → 8.07 | 10.81 → 10.59 | 17.07 → 14.89 |
26.00 → 21.44 |
| FP8 | 2 | 1 | 128 | 10.89 → 10.32 | 13.16 → 12.54 | 20.48 → 17.98 |
30.48 → 25.27 |
| FP8 | 8 | 8 | 12 | 13.19 → 12.00 | 19.76 → 17.66 | 42.62 → 40.47 |
57.36 → 55.41 |
| FP8 | 48 | 8 | 12 | 30.59 → 26.16 | 56.02 → 51.14 | 189.2 → 188.0 |
287.6 → 290.2 |
| BF16 | 1 | 8 | 12 | 9.80 → 8.66 | 13.34 → 11.72 | 28.09 → 21.95 |
49.33 → 37.76 |
| BF16 | 1 | 1 | 12 | 8.89 → 7.29 | 11.88 → 9.79 | 24.69 → 18.84 | 43.19
→ 32.53 |
| BF16 | 2 | 1 | 128 | 11.65 → 10.98 | 15.97 → 14.80 | 28.96 → 23.94 |
46.30 → 39.35 |

Across 88 configurations (FP8 and BF16; batch 1–48; q_len 1 and 8;
12–128 heads; KV 4k–128k) the change ranges from −36% to +2.6%.

### Numerics

Outputs are bit-identical wherever the launched split count is unchanged
(all batch ≥ 4 cases above). Where it changes (32 → 48 splits at batch
1–2), the output moves by 5e-3 (FP8) / 1e-3 (BF16) relative, which is
split-partition rounding: each split quantizes its own P, and against an
fp32 reference more splits measured equal or slightly better.

## 🔍 Related Issues

None.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues. (Ran `pre-commit run --files` on the
changed files: all hooks pass.)

## 🧪 Tests

- [x] Tests have been added or updated as needed.
(`test_mla_reducer_d_tile_selection` updated for the new band rule; new
`test_mla_split_kv_cap`.)
- [ ] All tests are passing (`unittest`, etc.). On SM107,
`tests/attention/test_cute_dsl_mla_decode.py`,
`test_cute_dsl_mla_dcp.py`, `test_mla_lse_base.py` and
`test_mla_wrapper.py` (`-k "cute or monolithic or reducer or mla_decode
or dcp"`): 699 passed, 41 skipped. The 16 `test_cute_dsl_vs_trtllm_gen`
cases fail in that environment before and after this change: it runs
from a source checkout without `flashinfer/data/csrc`, so the trtllm-gen
reference cannot JIT.

## Reviewer Notes

- Measured only on SM107 (212 SMs). The band rule and the 48-split cap
are expressed in SM count / occupancy, but they have not been measured
on SM100/SM103.
- Under CUDA graphs the host picks the split count from `max_seq_len`,
not the actual KV length. A per-request split count inside the kernel
would let long contexts use more splits (96 splits measured another −8
to −19% at 128k–512k) without hurting short ones; not in this PR.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* MLA decoding now supports up to 48 split-KV partitions, allowing
larger workloads to be processed with more partitions.
* Added support for combining split results across variable query
layouts and distributed cache processing.

* **Improvements**
* Split selection and result reduction now adapt to workload size,
helping use available GPU resources more efficiently.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Chunan Zeng <zcnrex@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [5965700](https://github.com/flashinfer-ai/flashinfer/commit/59657000e639e535c58ab7cce02a9228faec17ad)

- **作者**: eigen
- **时间**: 2026-10-03T20:55:11Z
- **提交信息**: perf(cake_dsa): direct accumulation into the caller's packed fp32 rows, key-range pass cap, in-kernel row lengths and fused index preparation for the native 64-head DSA sparse-attention kernels (#5657) (#6019)

## Summary

Round 3 of the native 64-query-head DSA sparse-attention kernels
(`flashinfer.experimental.cake_dsa_train`, #5704 / #5737 / #5865;
architecture-neutral programs since #5957), on `e4f94f948`:
index-distribution-independent structural levers only, same numerics
boundary (bf16 I/O, fp32 softmax statistics and dQ/dKV accumulation,
exact exp2 path), same rows and baselines as round 2.

- **Direct accumulation into the caller's packed fp32 rows**
(`bwd_main_natural` / `bwd_main_pass_natural`, registry field
`dkv_direct`): when the caller passes `dkv_acc` (+ `dkv_dst_map`) and
the row has at least four keys per query token (`S >= 4 T`), the main
stage's reduce warps add the dK/dV contributions straight into the
packed rows -- no fp32 accumulators in the workspace, no zero fill, no
cast launch (`dsa_train_workspace_size(..., dkv_acc=True)` shrinks by `S
x 2304` B). Rows with `S = T` keep the cast path (the natural drain's
lane transposes cost them more than the passes they remove);
`FLASHINFER_CAKE_DSA_DKV_DIRECT=1|0` forces or disables it. B200,
backward kernel, direct vs cast on the same rows: tail_2123x67923 -4.0
%, chunk_3884x267520 -3.4 %, packed_glm_a -1.4 %, packed_glm_b -0.5 %;
identical accuracy bands, dq bitwise.
- **Key-range pass cap** (`KeyPassPolicy.max_passes = 4`): the pass
formula's count is taken only up to four passes; beyond it the per-pass
fp32 dQ-partial round trip and pipeline fill outweigh the L2 benefit
(B200 iid: 3884 x 267520 six passes 8.07 -> one pass 7.01 ms, 4096 x
225280 five passes 7.85 -> 7.36 ms). No row of the benchmark table
changes its pass count.
- **L2 `evict_last` policy on the dK/dV reduction traffic** of every
main stage (-1.1..-1.4 % on the L2-pressure rows, same adds at the same
addresses).
- **Fused index preparation** (Cake-side `dsa_h64_index_prep`, counted
in the varlen entry's forward step on the Cake harness; the FlashInfer
varlen glue is unchanged in this PR): segment-relative top-k -> global
keys + per-row lengths in one launch (0.497 -> 0.048 ms at T = 16172).
- **In-kernel row lengths** (`derive_topk_length=`, ABI scalar
`derive_length`): the forward's metadata warp derives each row's key
count one query ahead of the tile loop (16-lane `shfl.xor` maximum under
the literal member mask `0xFFFF0000`, a 2-slot ring on the CLC response)
and writes `topk_length[query]` for the backward, so the entries no
longer launch the index preparation / `derive_topk_length` kernel before
the forward. On B200 this removes 52-102 us of host and launch time per
forward (doc_4096 / cptail_4k_131072 / doc_16231: 0.997 -> 1.030 of
FlashMLA's forward window on the 131072-key tail row).
- Regenerated programs (`csrc/cake_dsa_h64_train/`, one
architecture-neutral kernel / binding pair per stage with
`__CUDA_ARCH__`-guarded folds for `sm_100a` / `sm_103a` / `sm_107a`):
the main-stage kernels gain the five ABI operands of the direct form
(`dkv_stride, dkr_stride, dkr_col0, dkv_dst_map, dkv_has_map`; inert on
the permuted program) and the cache-hinted reductions; two new stages
(the natural-layout main and pass kernels), eight pairs in total, plus
the regenerated `cake_launch.py` and the registry record (`stages`,
`key_pass_policy.max_passes`, `dkv_direct`).
- Closed with paired data on B200 (kept as documented default-off knobs
on the Cake side, not in this PR): M128 PV forms of the forward (SwapAB
+3.2 %, PV-issuer warp +0.1..0.5 %), fused delta pre-pass (+2.6 % at the
best register budget), scalar natural drain (+20-30 %), setmaxnreg
re-budget (noise level).

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
needs; recompute step = 2 x forward + backward; median of >= 20 steps
(13 at >= 128k keys), 3 alternating rounds with rotated arm order, every
arm in its own process, bit-identical inputs, same GPU; CUPTI kernel
time per arm; SM clock recorded per arm, rows whose arms differ by more
than 3 % are flagged.

### SM100 (B200) -- delivered head `37d9cc7a8ff` (forward `631575ae7d5`,
backward `db958d9f336`)

| row | T | Tkv | segs | this PR fwd / bwd / step ms | A
(FlashMLA+cuDNN) step / recompute ms | FA #2914 step / recompute ms |
A/this step (fwd/bwd) | A/this recompute | FA/this step (fwd/bwd) |
FA/this recompute | peak / saved mem vs FA |
|---|---:|---:|---:|---|---|---|---|---:|---|---:|---|
| doc_4096 | - | - | - | 0.935 / 3.793 / 4.730 | 5.358 / 6.572 | 6.573 /
7.908 | 1.133 (1.298/1.093) | 1.160 | 1.390 (1.428/1.381) | 1.396 |
0.439 / 1.000 |
| doc_8192 | - | - | - | 2.100 / 9.236 / 11.351 | 11.847 / 14.294 |
13.659 / 16.099 | 1.044 (1.166/1.018) | 1.062 | 1.203 (1.178/1.213) |
1.196 | 0.608 / 1.000 |
| doc_16384 | - | - | - | 4.364 / 19.764 / 24.112 | 25.109 / 30.030 |
28.645 / 33.427 | 1.041 (1.128/1.021) | 1.056 | 1.188 (1.103/1.207) |
1.176 | 0.754 / 1.000 |
| doc_32768 | - | - | - | 8.913 / 41.425 / 50.427 | 53.345 / 63.489 |
59.526 / 69.088 | 1.058 (1.132/1.043) | 1.068 | 1.180 (1.063/1.208) |
1.162 | 0.857 / 1.000 |
| doc_65536 | - | - | - | 18.717 / 91.121 / 109.958 | 119.219 / 144.926
| 131.305 / 151.280 | 1.084 (1.367/1.028) | 1.124 | 1.194 (1.063/1.222)
| 1.174 | 0.920 / 1.000 |
| doc_131072 | - | - | - | 40.603 / 206.438 / 247.459 | 264.734 /
316.578 | 304.118 / 345.373 | 1.070 (1.265/1.038) | 1.097 | 1.229
(1.010/1.268) | 1.196 | 0.954 / 1.000 |
| cptail_4k_65536 | - | - | - | 1.279 / 6.173 / 7.440 | 8.208 / 9.597 |
9.336 / 10.737 | 1.103 (1.085/1.105) | 1.102 | 1.255 (1.123/1.281) |
1.233 | 0.443 / 1.000 |
| cptail_4k_131072 | - | - | - | 1.457 / 7.325 / 8.772 | 9.533 / 11.032
| 10.663 / 12.226 | 1.087 (1.030/1.097) | 1.080 | 1.216 (1.095/1.243) |
1.196 | 0.447 / 1.000 |
| packed_N1 | - | - | - | 12.385 / 62.567 / 75.070 | 77.990 / 90.410 |
91.165 / 103.601 | 1.039 (0.999/1.047) | 1.032 | 1.214 (0.999/1.259) |
1.183 | 0.835 / 1.000 |
| packed_N2 | - | - | - | 11.315 / 58.662 / 69.952 | 74.031 / 85.642 |
85.940 / 97.465 | 1.058 (1.018/1.065) | 1.054 | 1.229 (1.006/1.270) |
1.200 | 0.835 / 1.000 |
| packed_N4 | - | - | - | 10.571 / 49.807 / 60.379 | 65.869 / 77.150 |
75.436 / 85.987 | 1.091 (1.067/1.097) | 1.087 | 1.249 (0.996/1.302) |
1.212 | 0.835 / 1.000 |
| packed_N8 | - | - | - | 9.545 / 44.587 / 54.266 | 57.562 / 68.122 |
63.680 / 73.698 | 1.061 (1.107/1.054) | 1.068 | 1.173 (1.059/1.202) |
1.156 | 0.835 / 1.000 |
| packed_N16 | - | - | - | 9.170 / 42.712 / 51.882 | 54.741 / 64.980 |
59.546 / 69.035 | 1.055 (1.108/1.043) | 1.066 | 1.148 (1.035/1.172) |
1.132 | 0.835 / 1.000 |
| packed_N32 | - | - | - | 9.122 / 42.511 / 51.798 | 54.745 / 64.861 |
59.378 / 68.983 | 1.057 (1.108/1.049) | 1.064 | 1.146 (1.044/1.172) |
1.131 | 0.835 / 1.000 |
| skewed8 | - | - | - | 10.098 / 48.667 / 58.773 | 62.920 / 73.848 |
70.941 / 81.205 | 1.071 (1.077/1.069) | 1.073 | 1.207 (1.024/1.246) |
1.179 | 0.835 / 1.000 |
| spread_32k_65536 | - | - | - | 10.159 / 47.626 / 57.803 | 61.983 /
72.980 | 70.279 / 80.706 | 1.072 (1.082/1.071) | 1.073 | 1.216
(1.028/1.256) | 1.187 | 0.854 / 1.000 |
| spread_32k_131072 | - | - | - | 11.133 / 57.669 / 68.827 | 73.039 /
84.485 | 85.180 / 96.561 | 1.061 (1.028/1.067) | 1.057 | 1.238
(1.012/1.278) | 1.208 | 0.847 / 1.000 |
| spread_32k_196608 | - | - | - | 11.860 / 61.117 / 73.126 | 76.551 /
88.447 | 89.171 / 101.424 | 1.047 (1.000/1.057) | 1.040 | 1.219
(1.012/1.260) | 1.192 | 0.841 / 1.000 |
| packed_glm_a | - | - | - | 4.062 / 18.652 / 22.694 | 27.898 / 35.762 |
32.354 / 37.865 | 1.229 (1.934/1.072) | 1.336 | 1.426 (1.362/1.439) |
1.415 | 0.721 / 0.828 |
| packed_glm_b | - | - | - | 4.054 / 18.545 / 22.568 | 27.604 / 35.442 |
32.063 / 37.512 | 1.223 (1.920/1.068) | 1.333 | 1.421 (1.346/1.435) |
1.411 | 0.721 / 0.828 |
| packed_glm_a_s704 | - | - | - | 4.075 / 18.697 / 22.769 | 28.159 /
36.347 | 32.241 / 37.743 | 1.237 (2.011/1.067) | 1.355 | 1.416
(1.347/1.430) | 1.407 | 0.721 / 0.828 |
| tail_2123x67923 | - | - | - | 0.695 / 3.056 / 3.752 | 4.787 / 5.873 |
5.226 / 6.104 | 1.276 (1.563/1.211) | 1.320 | 1.393 (1.284/1.418) |
1.372 | 0.476 / 0.743 |
| doc_16231 | - | - | - | 4.318 / 19.569 / 23.886 | 27.120 / 34.737 |
28.475 / 33.312 | 1.135 (1.766/0.997) | 1.231 | 1.192 (1.121/1.207) |
1.181 | 0.732 / 0.934 |
| doc_4095 | - | - | - | 0.942 / 3.800 / 4.743 | 6.099 / 8.038 | 6.666 /
8.068 | 1.286 (2.058/1.095) | 1.414 | 1.406 (1.476/1.386) | 1.419 |
0.433 / 0.934 |
| doc_4097 | - | - | - | 0.942 / 3.797 / 4.739 | 6.105 / 8.045 | 6.823 /
8.216 | 1.288 (2.059/1.097) | 1.416 | 1.440 (1.478/1.431) | 1.446 |
0.432 / 0.934 |
| packed_glm_a_dstmap | - | - | - | 4.037 / 19.106 / 23.142 | 28.103 /
35.987 | 32.429 / 37.956 | 1.214 (1.957/1.058) | 1.324 | 1.401
(1.366/1.408) | 1.397 | 0.718 / 0.828 |
| packed_glm_b_dstmap | - | - | - | 4.007 / 18.982 / 22.983 | 27.758 /
35.564 | 32.045 / 37.490 | 1.208 (1.947/1.052) | 1.318 | 1.394
(1.359/1.402) | 1.389 | 0.717 / 0.828 |
| packed_glm_a_s704_dstmap | - | - | - | 4.044 / 19.146 / 23.189 |
28.450 / 36.676 | 32.475 / 37.968 | 1.227 (2.032/1.057) | 1.346 | 1.400
(1.361/1.409) | 1.394 | 0.718 / 0.828 |
| packed_glm_b_s704_dstmap | - | - | - | 3.983 / 18.927 / 22.909 |
28.077 / 36.204 | 32.135 / 37.590 | 1.226 (2.035/1.055) | 1.347 | 1.403
(1.369/1.410) | 1.398 | 0.717 / 0.828 |
| chunk_4096x268757 | - | - | - | 0.875 / 3.852 / 4.731 | 7.274 / 9.218
| 8.387 / 10.016 | 1.538 (2.223/1.383) | 1.638 | 1.773 (1.864/1.754) |
1.780 | 0.500 / 0.611 |
| chunk_3943x268757 | - | - | - | 1.050 / 4.815 / 5.850 | 8.198 / 10.124
| 8.931 / 10.551 | 1.401 (1.835/1.302) | 1.467 | 1.527 (1.543/1.519) |
1.528 | 0.502 / 0.602 |
| chunk_3884x267520 | - | - | - | 0.981 / 4.497 / 5.474 | 7.886 / 9.774
| 8.615 / 10.204 | 1.441 (1.924/1.333) | 1.514 | 1.574 (1.620/1.561) |
1.580 | 0.502 / 0.600 |

All 32 rows of the acceptance table (paired at the lever-e1 kernel
commit `631575ae7d5`, cubins byte-identical to the delivered head):
train step and recompute step faster than A and B on 32/32 (minima
A/this 1.039 / 1.032, FA/this 1.146 / 1.131); CUPTI kernel time: forward
ahead of FlashMLA's forward on 32/32 (>= 1.027) and backward ahead of
cuDNN's on 32/32 (>= 1.022); peak memory <= 0.954 of FA,
saved-activation memory equal. Wall-clock windows of the forward alone
trail FlashMLA's by 0.1 % or less on two rows that run at the 1000 W
power cap (packed_N1, spread_32k_196608) and the backward trails cuDNN's
by 0.3 % on doc_16231 (1-2 % more energy per call on the gather +
reduction traffic); a sustained-loop NVML probe shows this PR 2.8-3.4 %
faster and 1.6-2.0 % lower-energy on the two forwards. SM clocks differ
by more than 3 % between arms on 25 rows (this PR draws more power); the
clock-normalised ratios are all > 1.

### Varlen entry (this package's `dsa_sparse_attention_varlen`, B200,
regenerated programs, `benchmarks/bench_cake_dsa_train.py --rows ...
--arms cake --steps 5`)

| row | fwd ms | bwd ms | step ms | peak GiB |
|---|---:|---:|---:|---:|
| chunk_4096x268757 | 1.032 | 3.671 | 4.933 | 1.50 |
| packed_glm_a_dstmap | 4.342 | 18.041 | 23.242 | 4.28 |
| tail_2123x67923 | 0.882 | 3.088 | 4.139 | 0.88 |

(Steps of 5 with CUDA-event timing on the regenerated checkout, one B200
(driver 580.82.07); the paired table above is the CUPTI protocol.)

### Generated programs

One export run regenerates the eight architecture-neutral modules
(`fwd`, `bwd_delta`, `bwd_main`, `bwd_main_natural`, `bwd_compact`,
`bwd_main_pass`, `bwd_main_pass_natural`, `bwd_cast`; 16 program files +
`cake_launch.py` + the registry) and validates the shapes of the local
architecture. Source-vs-export timing gate (CUDA-graph replay, symmetric
arms, 3 groups, directional disagreement <= 2 %):

| run | GPU | selected shapes | source/export geomean (all / coverage /
perf) | tests on the regenerated checkout |
|---|---|---|---|---|
| B200 (driver 580.82.07) | sm_100a | 11/11 passed | 1.0004 / 1.0005 /
1.0002 | 100 passed |
| GB300 (driver 580.159.03) | sm_103a | 11/11 passed | 1.0004 / 1.0004 /
1.0005 | 100 passed (with the repository's CuTe-DSL typing shim loaded
first, see Numerics) |

Both runs wrote byte-identical deliveries (16 changed files, identical
sha256 lists: the regenerated kernel / binding sources of `fwd`,
`bwd_main`, `bwd_main_natural`, `bwd_main_pass` and
`bwd_main_pass_natural`, the regenerated `cake_launch.py` and registry,
`cake_backend.py`, the package README, the tests and the benchmark;
`bwd_delta`, `bwd_compact` and `bwd_cast` regenerate identically to
`main` and keep their files, the six superseded sources are removed);
this PR carries them.

The B200 varlen rows above come from the regenerated checkout.
Publication guard (`check_public`) passed on the regenerated tree.

### SM103 (GB300)

Same source revision, regenerated programs validated separately (see
Generated programs). Paired protocol as above on one GB300 of a 4 x
GB300 node (driver 580.159.03, loaded SM clock 2070 MHz on every arm of
every row, no clock flag), 10 rows (3 rounds, 20 steps / 13 at >= 128k,
90/90 arm processes rc=0):

| row | T | Tkv | segs | this PR fwd / bwd / step ms | A
(FlashMLA+cuDNN) step / recompute ms | FA #2914 step / recompute ms |
A/this step (fwd/bwd) | A/this recompute | FA/this step (fwd/bwd) |
FA/this recompute | peak / saved mem vs FA |
|---|---:|---:|---:|---|---|---|---|---:|---|---:|---|
| packed_glm_a_dstmap | 16231 | 268757 | 8 | 3.142 / 15.547 / 18.689 |
24.777 / 31.464 | 28.144 / 32.807 | 1.326 (2.128/1.164) | 1.441 | 1.506
(1.484/1.510) | 1.503 | 0.718 / 0.828 |
| packed_glm_b_dstmap | 16172 | 267520 | 8 | 3.130 / 15.433 / 18.566 |
24.629 / 31.291 | 28.029 / 32.678 | 1.327 (2.128/1.164) | 1.442 | 1.510
(1.485/1.515) | 1.506 | 0.717 / 0.828 |
| packed_glm_a_s704_dstmap | 16231 | 268757 | 8 | 3.147 / 15.568 /
18.715 | 25.093 / 32.087 | 28.145 / 32.809 | 1.341 (2.223/1.162) | 1.468
| 1.504 (1.481/1.508) | 1.501 | 0.718 / 0.828 |
| packed_glm_b_s704_dstmap | 16172 | 267520 | 8 | 3.137 / 15.455 /
18.592 | 24.940 / 31.913 | 28.033 / 32.685 | 1.341 (2.223/1.163) | 1.469
| 1.508 (1.483/1.513) | 1.504 | 0.717 / 0.828 |
| chunk_4096x268757 | 4096 | 268757 | 9 | 0.746 / 3.315 / 4.062 | 6.637
/ 8.349 | 7.651 / 9.116 | 1.634 (2.296/1.485) | 1.737 | 1.884
(1.964/1.866) | 1.896 | 0.500 / 0.611 |
| chunk_3943x268757 | 3943 | 268757 | 8 | 0.871 / 4.239 / 5.110 | 7.507
/ 9.185 | 8.077 / 9.494 | 1.469 (1.926/1.375) | 1.535 | 1.581
(1.626/1.571) | 1.587 | 0.502 / 0.602 |
| chunk_3884x267520 | 3884 | 267520 | 8 | 0.838 / 3.961 / 4.800 | 7.199
/ 8.854 | 7.852 / 9.262 | 1.500 (1.977/1.399) | 1.571 | 1.636
(1.681/1.627) | 1.643 | 0.502 / 0.600 |
| doc_4096 | 4096 | 4096 | 1 | 0.808 / 3.483 / 4.291 | 4.857 / 5.911 |
5.877 / 6.997 | 1.132 (1.304/1.092) | 1.159 | 1.370 (1.385/1.366) |
1.372 | 0.439 / 1.000 |
| tail_2123x67923 | 2123 | 67923 | 1 | 0.599 / 2.744 / 3.342 | 4.362 /
5.301 | 4.675 / 5.400 | 1.305 (1.567/1.248) | 1.345 | 1.399
(1.212/1.438) | 1.370 | 0.476 / 0.743 |
| doc_16231 | 16231 | 16231 | 1 | 3.568 / 16.494 / 20.065 | 24.364 /
31.116 | 24.068 / 28.171 | 1.214 (1.893/1.068) | 1.317 | 1.199
(1.150/1.210) | 1.192 | 0.732 / 0.934 |

Faster than A and B on step and recompute on 10/10 rows; forward ahead
of FlashMLA on 10/10 (1.30-2.30x), backward ahead of cuDNN on 10/10
(1.07-1.49x); peak and saved memory at or below B on 10/10. Versus the
round-2 GB300 table (baseline arms unchanged within 0.2 %): packed_glm
rows -4.0..-4.2 % step, chunk rows -7.9..-12.2 %, doc_4096 -1.7 %. The
in-kernel row lengths take the single-document and chunk forwards down
3.8-7.1 % on GB300 but cost the 16k-query packed forwards +1.0 % (3.11
-> 3.14 ms, step unchanged): on those rows the metadata warp's length
scan costs slightly more than the removed launch saved; a cheaper
derivation for very long query ranges is noted as follow-up work.

### SM107 (R200)

The sm_107a programs are the same generator output as the sm_100a /
sm_103a ones. Compiled with nvcc 13.4 (`-arch=sm_107a -Xptxas -v`) at
this head (regenerated architecture-neutral sources; the eight sm_100a
folds compile as the toolchain cross-check): forward 141 registers, no
spills (4272 SASS instructions); `bwd_delta` 41, `bwd_compact` 28 and
`bwd_cast` 70 registers, no spills; the four backward main / pass stages
96 registers with a 144-152 B stack frame and 168-220 B of spill stores
/ 544-572 B of spill loads (STL 42-55, LDL 136-143) -- the known Rubin
by-value tensor-map ABI spill, a little smaller than in round 2 (stack
200 B, STL 52 / LDL 149). No R200 device run in this round.

## Numerics

Boundary unchanged: bf16 inputs/outputs, fp32 softmax statistics, fp32
dQ / dK / dV accumulation, exact `ex2` path; no low-precision
intermediates, no approximate reciprocals, no key sampling. Accuracy on
B200 (8 cases x 3 seeds, direct and cast paths): every rel-L2 component
within the frozen round-2 table x 1.02, lse max-abs <= 2e-5, forward and
dq bitwise deterministic, the two paths' bands identical to four printed
digits (fp32 summation order only). Re-measured at the delivered head on
B200 (48/48 results): out 0.1605-0.2017 %, dq_latent 0.2154-0.2384 %,
dq_rope 0.2361-0.2397 %, dkv_latent 0.1586-0.2335 %, dk_rope
0.1663-0.2384 %, lse max-abs <= 9.17e-06 (peaked_099; <= 1.76e-06 on the
other cases), dq row-p99 0.236-0.429 % (peaked_099 0.399-0.429 %, gate
0.4 % applies to the 32k x 256k skewed case only); direct and cast paths
identical to the printed digits on every case and seed; strided-vs-copy
views bitwise equal. On GB300 the regenerated checkout's tests pass
100/100 once the repository's `quack_compat` typing shim is loaded first
(`torch.index_add_` of a test *reference* is routed into a CuTe-DSL
scatter_add on that container; the kernels under test are not involved).
On GB300 (8 cases x 3 seeds x 2 arms, 48/48 results): the two arms print
identical values on every case and seed; lse <= 9.4e-6; contract gates
pass on all three contract cases; 94/96 components are within the B200
frozen round-2 table x 1.02, the two misses being the same value in both
arms (`layout_kv704_perm_4k` dk_rope 0.1717 % vs 0.1672 % x 1.02 =
0.1705 %, i.e. 1.027x the B200 value on a case that takes the unchanged
cast path on both arms: an architecture accumulation-order difference,
not a change of this PR).

## Tests

```
pytest tests/experimental/test_cake_dsa_train.py
python benchmarks/bench_cake_dsa_train.py --rows chunk_4096x268757,packed_glm_a_dstmap,tail_2123x67923 --arms cake
```

New / extended tests: `KeyPassPolicy.max_passes` cap;
direct-accumulation rule, env override and record validation
(`plan_dkv_direct`, `record_direct_stages`, `DkvDirectPolicy`);
natural-stage binding through the contract aliases; direct vs cast paths
agree on the GPU (duplicating destination map, 704-column buffer,
untouched rows/columns); workspace layout without accumulators; registry
well-formedness of the natural stages (same argument plan and grid as
the regular main stage). compute-sanitizer synccheck + memcheck 0 errors
on the Cake side for the direct program, the index preparation and the
single-/multi-pass backward rows. Fresh checkout of the delivered Cake
head rebuilt only from the staged source bundles (native analysis
library built from source, cold caches): policy/harness CPU tests,
facade + index-preparation GPU e2e (73 passed / 3 skipped), the
registered-kernel slice (compile + static analysis + GPU correctness)
and the five bench-regression floors all pass; the regenerated
checkout's `tests/experimental/test_cake_dsa_train.py` passes 99/99 on
B200.

Coordination: #6007 (per-target key-range pass rule, same author)
touches the same `KeyPassPolicy` / registry record / README / tests;
this PR is based on `main`, whichever of the two lands second rebases,
and `max_passes` composes as a cap on the rule's pass count.

Tracker: #4642, #4254.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added an option to derive per-row top-k lengths during the forward
pass, with support for saving them to a caller-provided buffer.
* Added direct accumulation of key and value gradients into compatible
caller-provided buffers, reducing workspace requirements in supported
cases.
  * Updated key-range processing to cap policy-selected passes at four.

* **Bug Fixes**
* Improved handling of mapped gradient destinations and multi-segment
key rows.

* **Documentation**
* Documented options to automatically select, force, or disable direct
gradient accumulation.

* **Tests**
* Expanded coverage for derived lengths, direct accumulation, workspace
sizing, and key-pass limits.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [84fa85e](https://github.com/flashinfer-ai/flashinfer/commit/84fa85ebb5ac58f8f8fe7901dac509bcdace0988)

- **作者**: eigen
- **时间**: 2026-10-03T20:45:58Z
- **提交信息**: refactor(cake_moe_grouped_gemm): re-export with deduplicated sources and thin launchers (#6017)

## Summary

Re-export of the experimental Cake ragged BF16 MoE grouped GEMM family
(`flashinfer/experimental/cake_moe_grouped_gemm/**`) from the current
generator, with the generated sources deduplicated and the launch
binding thinned. Deslop / re-export follow-up of #5678 (original
request) and #5751 (original delivery); part of #5768.

Numerics, the public helpers (`grouped_gemm_fwd` / `grouped_gemm_dgrad`
/ `grouped_gemm_wgrad`, `prepare_grouped_gemm_*`, `cake_grouped_mm`,
`grouped_mm_bf16(..., backend="cake")`), the host plan and the
measurement protocol are unchanged. The three programs keep fwd / dgrad
/ wgrad, BF16 and FP32 weight gradients, ragged and empty groups, and
bitwise-deterministic weight gradients.

## What changed

- **One source pair per program instead of one per architecture.** The
kernel text is identical across `sm_100a`, `sm_103a` and `sm_107a`
except for one address-space line, which is now folded under a
`__CUDA_ARCH__` guard. The k256 / k512 tail-reduce clones become one
program compiled with `-DWGRAD_TILE=<tile>` (value-free `#define` with
`#error` when undefined).
- **By-value TMA descriptors.** The binding encodes the operands'
`CUtensorMap`s on the host from the bound tensors at every launch; no
descriptor workspaces, no per-call descriptor upload kernel. The
weight-gradient per-CTA descriptor slots and FP32 tail partials stay
caller-owned.
- **Registry.** `cake_jit.MODULES` (per-architecture records with
repeated argument plans) is replaced by `cake_jit.PROGRAMS` (each
program once: sources, compile flags, FFI entry, argument plan, launch
geometry, per-architecture closure digests) and `cake_jit.ROUTES`
(operation × output dtype × k tile → stage programs and their
specializations). `cake_backend.py` binds through the routes and caches
the per-device facts.

| | before (#5751) | after |
|---|---:|---:|
| files under the family (`csrc` + Python + README) | 56 | 20 |
| lines | 30,891 | 8,487 |
| generated `.cu` | 53 (26 kernels + 26 bindings + .clang-format) | 16
(8 kernels + 8 bindings) |
| distinct kernel bodies / skeletons | 16 / 14 | 8 / 8 |
| architecture copies (lines) | 10,965 | 0 |
| constant clones (lines) | 397 | 0 |
| `cake_jit.py` lines | 1,345 | 684 |

## Validation

Same contract, same 75 rows per architecture, same tolerances and gates
as #5678, measured on B200 (`sm_100a`), GB300 (`sm_103a`) and R200
(`sm_107a`):

- Source / export parity, correctness before and after timing against
the fp64 per-group reference, bitwise reproducibility of the exported
call, CUPTI activity-count parity, and the frozen interleaved timing
protocol (symmetric CUDA-graph capture of every arm, 6 interleaved
groups × 60 cold-L2 samples, order-symmetry and drift validity gates):
225 contract rows measured, 223 passed. B200 75/75 and R200 75/75. GB300
73/75: `corr_wgrad_bf16_ragged_e4` (a 10 µs row) measures source/export
0.955 in both arm orders on three attempts, below the 0.97 parity floor;
`wgrad_down_e32` fails only the order-symmetry gate of the per-expert
cuBLAS baseline arm (0.03 vs 0.02; source/export 0.998). Source/export
geomean over all 225 rows 0.9999; vs `torch._grouped_mm` 1.151 (183
rows), vs cuDNN grouped matmul 1.082 (80 rows), vs per-expert cuBLAS
1.033 (219 rows).
- Paired A/B against the delivered #5751 package in one process (graph
replay, cold L2, ABBA rounds, every contract row): B200 geomean 1.0097
(min row 0.9906; fwd 1.002 / dgrad 1.000 / wgrad 1.022); GB300 geomean
1.0100 (min row 0.9868; fwd 1.001 / dgrad 1.001 / wgrad 1.023); R200
geomean 1.0127 (min row 0.9906; fwd 1.005 / dgrad 1.004 / wgrad 1.025).
No row below 0.98 on any device; host launch overhead unchanged
(cand/base 1.001 GB300, 0.989 R200, 0.997 B200). The small
weight-gradient rows gain 5–28 % on R200 from dropping the descriptor
workspace fetch.
- Output of the delivered and the re-exported programs bitwise identical
on every row: 75/75 on each of the three devices.
- SASS against the delivered package: every tail-reduce kernel the A/B
built (bf16 k256 / k512 and fp32 k512 on B200 and GB300; bf16 / fp32
k256 on R200) is byte-identical to the corresponding delivered kernel.
The main kernels are 16–72 instructions shorter on every device; the
diff is the descriptor path only (`LDCU c[0x0][…]` param-space tensor
maps replace the workspace-pointer load and its `BSSY`/`ISETP` guard)
plus register renames, with no change to the MMA / TMA / shared-memory
data path.
- `tests/experimental/test_cake_moe_grouped_gemm.py` on all three
devices: 38 passed on each.
- compute-sanitizer memcheck / synccheck / racecheck on the four routes
(R200, CUDA 13.5): memcheck and synccheck 0 errors on the default
contract rows; racecheck 0 hazards on the six small correctness rows
(ragged, empty groups, tiny groups), while the full-size rows did not
finish under racecheck within the 50-minute step budget (no verdict for
those shapes).

Platform notes: the R200 numbers come from a power-capped node (SM
clocks oscillating 1.8–2.3 GHz); the protocol's drift gate rejected
heavy weight-gradient rows under the first measurement regime, so the
frozen protocol now primes the arm about to be measured once before each
reportable launch (an unmeasured warm launch; gates and sampling
unchanged). `sm_107a` builds need CUDA 13.5; the k512 weight-gradient
tile stays `sm_100a`/`sm_103a` only as before.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Cake grouped GEMM now uses shared launch paths across supported GPU
architectures, with additional weight-gradient tile support on select
architectures.
* Tensor-map descriptors are generated at launch, so callers no longer
need to prepare or provide a descriptor workspace.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [c3c3336](https://github.com/flashinfer-ai/flashinfer/commit/c3c33367f720b40603d82fd99b81c631410cb22f)

- **作者**: Wei Yihua
- **时间**: 2026-10-03T12:09:00Z
- **提交信息**: Sm120 cudnn frost moe bf16 (#5762)

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
* Added BF16 grouped-MoE support for SM120a GPUs, with packaged kernels
for common activation patterns.
* Expanded benchmark tooling to compare paired speedups, filter and rank
tile candidates, and validate and export shortlisted kernels.
* **Documentation**
* Clarified architecture support, admission limits, and benchmark
results for BF16 and block-scaled pipelines.
* **Bug Fixes**
* Improved benchmark resume validation and made cache eviction more
reliable.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [e4f94f9](https://github.com/flashinfer-ai/flashinfer/commit/e4f94f94848372b5019eb1d8b4e075a7393f7e1a)

- **作者**: Yuang Yao
- **时间**: 2026-10-03T09:42:26Z
- **提交信息**: fix(comm): construct FusedOp after the PDL grid dependency sync (#5081)

<!-- .github/pull_request_template.md -->

## 📌 Description

`FusedOp`'s constructor loads `rms_gamma` and this thread's first
`residual_in` row, and for the quantized patterns it dereferences
`scale_factor`. In both `allreduce_fusion_kernel_oneshot_lamport` and
`allreduce_fusion_kernel_twoshot_sync` it is constructed **before**
`cudaGridDependencySynchronize()`:


https://github.com/flashinfer-ai/flashinfer/blob/dd12b73b4461c37b467f77133c17c770adfd3a7b/include/flashinfer/comm/trtllm_allreduce_fusion.cuh#L1510-L1513


https://github.com/flashinfer-ai/flashinfer/blob/dd12b73b4461c37b467f77133c17c770adfd3a7b/include/flashinfer/comm/trtllm_allreduce_fusion.cuh#L1578-L1580

Launched with PDL, the kernel can begin before its stream predecessor
has finished writing `residual_in`, so those constructor loads may
observe the producer's pre-completion state. `FusedOp::update()` reloads
only when `m_access_id` changes, so each thread's first access is never
re-read and the stale value reaches `residual_out` and `norm_out`.

This PR moves both constructions after the grid dependency sync. Nothing
else moves. Without PDL, and below SM90 where the sync is compiled out,
the ordering is unchanged.

**Where it shows up.** vLLM's layer-0 `AllReduceRMSNormPattern` is
exactly this shape: one kernel writes the embedding output and a freshly
zeroed residual, then the fused op runs on that with
`launch_with_pdl=True`. How visible the stale read is depends on what
the residual buffer held before: zeros are invisible, a previous
occupant's values decode as subtly wrong text, and non-finite bytes give
NaN `norm_out` and a tail of token 0.

**Measured** on 4xH100, bf16, hidden 2688, 128 tokens, one-shot, one
CUDA graph per step, with a producer that triggers PDL early and then
writes zeros over a NaN-filled residual buffer (flashinfer 0.6.11.post2,
torch 2.11.0+cu128), 2000 steps per rank on all 4 ranks:

| Arm | steps with a non-finite `norm_out` |
|---|---|
| PDL on, unpatched | **2000 / 2000** on every rank |
| PDL on, both constructions moved | **0 / 2000** |
| PDL off, unpatched | **0 / 2000** |

The third row is the control: with the same producer and the same
buffer, disabling PDL alone removes the failure, which is what points at
the ordering rather than at the producer.

That harness drives the installed wheel rather than a source build, so
those particular numbers are not a re-run of this commit. They no longer
carry the argument on their own: the test added below reproduces the
same failure from source, on this branch, and is what I would ask you to
judge the change by.

**Compiled.** Both changed kernels build clean with `nvcc` 12.9 for
`sm_90`, `sm_100a` and `sm_120a`. I used explicit instantiations so the
kernel bodies are type-checked rather than only parsed: patterns
`kARResidualRMSNorm` and `kARResidualRMSNormFP8Quant`, `NRanks` 2, 4 and
8, both `TriggerCompletionAtEnd` values, bf16 and fp16. Stock `main`
compiles the same way as a control, and the resulting objects differ, so
the moved statement reaches codegen rather than being folded away.
Within each kernel every use of `fused_op` already follows the new
construction point.

**Scope.** These are the only two `FusedOp` constructions in the
repository; `trtllm_moe_allreduce_fusion.cuh` does not use `FusedOp`. I
did **not** audit the other `cudaGridDependencySynchronize()` call sites
for the same source-ordering hazard.

## 🔍 Related Issues

I did not find an existing issue for this. Two neighbours, neither
reporting it:

- #2558 is the same hazard family, PDL correctness, but a different
mechanism: `griddepcontrol.wait` written as inline asm without the
`"memory"` clobber in `norm.cuh` and `activation.cuh`. It closes by
asking for a general check for "this kind of issue"; this PR is a
source-ordering instance rather than a compiler-barrier one, in a file
that already uses the wrappers.
- #2887 concerns `trigger_completion_at_end` on this same kernel, as a
performance question.

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

Scope of that second box, so it is not read wider than I earned it: I
ran the test added by this PR, both arms, on 2xH100 with `world_size=2`.
I have not run the rest of the comm suite, and the `world_size=4`
parametrization skipped for want of free devices on the machine I have.

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

**On the test.** `tests/comm/test_trtllm_allreduce_fusion_pdl.py`, in
the shape of #3880: a focused `load_inline` test beside the existing
`tests/comm/` coverage.

`test_trtllm_allreduce_fusion.py` already parametrizes
`launch_with_pdl=[True, False]` and passes either way, because nothing
there puts a slow PDL producer in front of the fused op. What was
missing is the producer, not the flag. So the new test supplies one: a
kernel that issues `griddepcontrol.launch_dependents`, spins for a fixed
number of cycles, and only then writes `residual_in`. The buffer is
NaN-filled first, so a read issued before
`cudaGridDependencySynchronize()` reaches `residual_out` and `norm_out`
as a non-finite value rather than as a subtly wrong number, and the
assertion does not depend on a tolerance. Both constructions are
covered, through `use_oneshot` True and False.

Measured on 2xH100, bf16, hidden 4096, 128 tokens, `world_size=2`, 20
iterations per arm, running the same source tree twice with only this
patch differing:

| Header | `launch_with_pdl=True` | `launch_with_pdl=False` |
|---|---|---|
| without this patch | **fails** | passes |
| with this patch | **passes** | passes |

`launch_with_pdl=False` is the control: plain stream ordering makes the
producer's writes visible regardless, so it passes on both headers. That
is what distinguishes an ordering bug from a broken producer or a bad
harness.

On the timing worry I would have raised myself: the spin is about 2 ms,
against a fused kernel that runs in microseconds, so the window is not
marginal. If you would still rather not have a race-shaped test in CI,
say so and I will drop it to a manual marker or remove it — I would
rather you have the reproduction than have it merged over an objection.

One thing to flag while I was there: the comm CI scripts enumerate test
files rather than globbing `tests/comm/`, so a new file does not run
until it is listed. I added this one to `SPAWN_MANAGED_TEST_FILES` in
`scripts/task_test_multi_gpu_comm_kernels.sh`, which is the lane
documented for tests that create their own distributed workers. Please
move it if that is the wrong lane.

**On what is still not covered.** The `world_size=4` parametrization
skipped: the machine I have did not have four free devices, so the
four-rank path is exercised only by the original harness on the pinned
build, not from source. Please run CI rather than taking my word for any
of it.

**Rationale I can defend.** The claim is narrow: the constructor
performs global loads, PDL permits the kernel to start before the
producer's writes are visible, and the sync is the barrier that makes
them visible, so the loads belong after it. The measured arms above are
what convinced me it is real rather than theoretical.

---

AI assistance: this change was drafted with Claude Code, and the commit
carries a `Co-authored-by:` trailer. Opening as a draft while I do my
own line-by-line review; I will mark it ready once I have, and not
before.




<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Improved fused all-reduce operations to wait for dependent GPU work to
finish before reading input data, preventing stale or invalid results
when programmatic dependent launches are used.

* **Tests**
* Added multi-GPU coverage for synchronization ordering across supported
launch modes, data types, world sizes, and kernel variants.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Yuang Yao <yuang.yao@scale.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [7eb86aa](https://github.com/flashinfer-ai/flashinfer/commit/7eb86aa0fdc1248fab43c89801de4ed450e35e77)

- **作者**: Alex Yang
- **时间**: 2026-10-03T07:45:34Z
- **提交信息**: fix(prefill): allow plan-once CUDA-graph use of the CUTLASS ragged backend (v0.7.1 regression from #5133) (#5975)

## 📌 Description

**Fixes a v0.7.1 regression from #5133.** With `backend="cutlass"` and
`use_cuda_graph=True`, `BatchPrefillWithRaggedKVCacheWrapper.plan()` now
raises `ValueError ("... is not CUDA-graph safe")` on the **first**
plan. That blocks the plan-once-then-capture pattern that works in
v0.7.0. The graph-mode ragged run of `benchmarks/routines/attention.py`
also crashes. #5133 is in v0.7.1rc1/rc2 and not in v0.7.0.

Changes (`flashinfer/prefill.py`, +25/−14):
- **Re-plans are still refused.** A re-plan would invalidate captured
buffers, and `max_qo_len` is baked into the captured launch.
- **The refusal happens earlier.** It now comes *before* the qo/kv
indptr `copy_` into the registered buffers, so a refused re-plan leaves
the captured state untouched.
- **`backend="auto"` is unchanged.** It still declines CUTLASS in graph
mode, because it re-resolves on every `plan()` and could switch backends
under a captured graph.

This is the same guard relaxation as #5286's second commit (@Anerudhan),
split out as a minimal fix without that PR's `auto` change. If this
lands first, #5286 should drop that commit, and #5401 (benchmark runs
CUTLASS eagerly) becomes unnecessary.

## 🔍 Related Issues

Regression from #5133. Related: #5286, #5401.

## 🧪 Tests

`tests/attention/test_auto_backend_upgrade.py`:
`test_explicit_cutlass_refuses_cuda_graph` is replaced by two tests:
- `test_explicit_cutlass_plan_once_then_capture_under_cuda_graph`:
uneven ragged lengths, capture, then replays on fresh inputs. Output is
bit-exact against eager CUTLASS and within 2e-2 of fa2.
- `test_explicit_cutlass_refuses_replan_under_cuda_graph`: a re-plan
raises, and the indptr buffer and plan info are unchanged.

B200 (SM100), CI image `flashinfer-ci-cu130:20260822-9a0e83b`. Repro:
explicit cutlass, graph mode, plan once, capture, 5 replays vs eager
fa2, then a re-plan.

| Tree | First plan | `test_auto_backend_upgrade.py` |
|---|---|---|
| v0.7.0 | OK (re-plan silently accepted) | — |
| main / v0.7.1rc2 | **ValueError** | 35 passed, 1 xfailed (the new
tests fail on the old library) |
| this branch | OK, worst rel vs fa2 3.7e-3; re-plan raises | 36 passed,
1 xfailed |

Also on this branch:
- `test_blackwell_fmha.py`: 3128 passed, 240 skipped.
- `test_lse_base.py -k cutlass`: 2 passed.
- `test_trtllm_ragged_kv_stride.py -k cutlass`: 1 passed.
- Graph-mode ragged benchmark: refcheck clean (fa2 0.686 ms, cutlass
0.766 ms, cudnn 0.544 ms).

- [x] pre-commit run on changed files
- [x] Tests added/updated

## Reviewer Notes

- **Remaining difference from v0.7.0:** a *second* `plan()` on an
explicit-cutlass graph-mode wrapper now raises. In v0.7.0 that re-plan
was silently accepted while the captured graph replayed against freed
buffers.
- **v0.7.1:** labeled for rc3. A clean cherry-pick onto `release-v0.7.1`
(identical patch-id) is ready at `aleozlx:overnight/reg5133-rel-v0.7.1`.
- The internal GitLab bot is currently down, so the Blackwell evidence
above is from a manual computelab run.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* CUDA-graph mode now supports planning once with the explicit CUTLASS
backend, followed by capture and replay. Replayed results can be used
with fresh inputs.
* **Behavior Changes**
* A later attempt to replan with CUTLASS in CUDA-graph mode is rejected,
and the existing plan and registered buffers remain unchanged. Use the
`auto`, `cudnn`, or `fa2` backend when replanning; `auto` does not
select CUTLASS in graph mode.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Anerudhan Gopal <agopal@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: mingyangw <35635157+saltyminty@users.noreply.github.com>

### [233d8bd](https://github.com/flashinfer-ai/flashinfer/commit/233d8bd35d2707207c29769d57d8214636714664)

- **作者**: Alex Yang
- **时间**: 2026-10-03T07:45:17Z
- **提交信息**: fix(gemm): fall back from stale narrow-tile / split-K tactics in cute-dsl mm_mxfp8 and mm_fp4 (follow-up to #5890) (#5730)

<!-- .github/pull_request_template.md -->

## 📌 Description

**Follow-up to #5890.** #5890 restored
`Sm100BlockScaledPersistentDenseGemmKernel.can_implement`'s narrow-tile
bound (tile_n < 64 only at kernel N ≤ 32), so the autotuner no longer
*enumerates* the faulting tactics (#5725).

`can_implement` is only consulted at enumeration, though. A tactic tuned
for a low-M bucket can still be **replayed** at a runtime M it cannot
serve, through:
- floor mapping inside `autotune(tuning_buckets=...)`,
- a clamp above the top bucket, or
- a stale cache.

That replay still crashes, in both cute-dsl runners:

| Runner | Replayed tactic | Result on `main` |
|---|---|---|
| `mm_mxfp8` | swap-AB narrow tile tuned at M ≤ 32, run at M > 32 |
sticky `cudaErrorMisalignedAddress` |
| `mm_fp4` (NVFP4 / MXFP4) | narrow tile at kernel N > 32 |
`cudaErrorMisalignedAddress` |
| `mm_fp4` (NVFP4) | split-K tactic past the split-K kernel's M range |
`ValueError: Invalid FP4 split-K tactic` |

#5269 (now on `main`) covers only stale MXFP8 *split-K* tactics.

### Changes

1. `Sm100BlockScaledPersistentDenseGemmKernel.NARROW_TILE_MAX_N = 32`
plus `narrow_tile_ok(tile_n, kernel_n)` are the single source of truth
for the bound. `can_implement` uses it, keeping #5890's comment and
behaviour.
2. **`mm_mxfp8` forward:** after the #5269 split-K fallback, re-check
the tactic about to launch. If its narrow tile would run at kernel N >
32, switch to `fallback_tactic`.
3. **`mm_fp4` forward:**
- A narrow tile past `narrow_tile_ok`, or a structurally sound split-K
tactic that is shape-invalid for the runtime M, falls back to the
untuned selector. That is the same expression the `tactic=None` path
uses, now a local helper.
   - Structurally malformed split-K tactics still raise.
   - SM12x is unaffected: #5100 returns its own runner before this path.
4. **Tests:**
- `test_mm_mxfp8_cute_dsl_stale_narrow_tile_tactic_falls_back`: M 40/64
× tile_n 8/16/32.
- `test_mm_fp4_cute_dsl_stale_narrow_tile_tactic_falls_back`: NVFP4 and
MXFP4.
   - `test_mm_fp4_cute_dsl_stale_split_k_tactic_falls_back`
- CPU-only `test_narrow_tile_can_implement_boundary`: NVFP4 16/E4M3 and
MXFP4/MXFP8 32/E8M0. It accepts N=32 and rejects N=33, with a 64-wide
control.

This branch was opened before #5890 and #5269 merged, and carried both.
`main` has been merged in (signed merge commit `de5eaf7a7`). The diff
against `main` is now only the items above.

## 🔍 Related Issues

Refs #5725. #5890 fixed the enumerated-tactic crash; this PR covers the
replay path.

Related: #5269, #5890, #5609 (source of the narrow-tile addressing),
#5449 / #5450 (vLLM DSv4.1 MXFP8 warmup under `tuning_buckets`).

**For v0.7.1:** rc2 has #5269 but not #5890, so cute-dsl `mm_mxfp8`
autotune still hits #5725 there. rc3 needs #5890, and this PR for the
replay path.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues. (Ran on all changed files.)

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

GPU validation of the pre-merge head (`6e414635b`, which also carried
the #5890-equivalent bound). B200 (SM100) and B300 (SM103), CI image
`flashinfer-ci-cu130:20260822-9a0e83b`, comparing `main` of 2026-09-30
(`aafe22ff6`) with this branch:

| Suite | `main` | this branch |
|---|---|---|
| `tests/gemm/test_mm_mxfp8.py -k cute` | 510 fail (sticky misaligned
address) | 518 passed |
| FP4 stale-tactic tests | 16/16 fail (12 misaligned, 4 split-K
ValueError) | 16/16 pass |
| CPU `can_implement` boundary tests | fail (old `main` accepted N=33) |
pass |
| `tests/gemm/test_mm_fp4.py` | 136 passed, 12 skipped | 152 passed, 12
skipped |
| `tests/gemm/test_cute_dsl_blockscaled_gemm.py` | 258 passed, 128
xfailed | same |

**FP4 forced-tactic probe (`main`):** NVFP4 and MXFP4 at M=40/64 with a
(128,8)/(128,32) swap tactic fault with a misaligned address. The branch
falls back with cosine ≈ 0.991 (NVFP4) and 0.987 (MXFP4).

**NVFP4 perf on #5609's shapes:** neutral.

**Re-validation of the merged head:** coming from CI. GitLab is scoped
to the three gemm test files.

## Reviewer Notes

- The fallbacks only run on mismatched replays. Steady-state serving
outside `autotune()` uses the op-native round-up mapper and gets the
tuned tactic.
- `narrow_tile_ok` also applies to the SM107 kernel path of the FP4
runner. A narrow SM107 tactic past N=32 would fall back to the SM107
untuned selector, which is safe; at worst it is slower on a replay.
- @yyihuang: your #5890 comment is kept verbatim in `can_implement`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Ziming Huang <zelda.huanghuang@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-10-04
**监控日期**: 2026-10-03
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4542
- **最后更新**: 2026-10-03T11:32:33Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-10-04
**监控日期**: 2026-10-03
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34645
- **最后更新**: 2026-10-03T21:20:35Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-10-04
**监控日期**: 2026-10-03
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


**报告日期**: 2026-10-04
**监控日期**: 2026-10-03
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13201
- **最后更新**: 2026-10-03T23:29:52Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-10-04
**监控日期**: 2026-10-03
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 36756
- **最后更新**: 2026-10-04T00:12:59Z

## 提交统计

- **昨日提交总数**: 42
- **提交者数量**: 14
- **主要提交者**: Mohammad Miadh Angkad, FREETRUMP, Banruo Liu

## AI分析总结

# SGLang 近日提交分析

## 1. 主要更新类型
- **重构**占比最高：模型解码器构建方式的大规模重构（约 10 条），以及并行上下文、缓存接口等内部 API 清理。
- **Bug 修复**：HiCache、sgl-router、PD 分离、AMD/DeepSeek 后端、CUDA graph 等多个子系统的缺陷修复。
- **性能优化**：DeepSeek-V4.1 专用 kernel、扩散模型注意力、PD 分离请求吞吐优化。
- **工程与基础设施**：内核版本升级（sgl-kernel 0.4.9）、Torch 2.14 AOT 内核更新、CODEOWNERS 治理、metrics 暴露。

## 2. 关键变更点与项目方向的关系
- **解码器"stage boundaries"重构系列**：将 Qwen2、GLM、Llama、ERNIE/EXAONE MoE、Granite MoE 等十余种模型解码器统一迁移到基于 stage boundaries 的构建范式，并让 stage boundaries 负责完成各阶段输出求和、清除冗余的 reduction-skip/TBO 调度机制。这是把模型适配从"逐模型手写"转向"声明式统一构建"，直接服务于 SGLang 作为多模型高速推理引擎的核心定位。
- **PD 分离（Prefill-Decode disaggregation）持续演进**：新增可选的 prefill-complete 后再分配 decode KV、在 prefill 结果等待期间继续接收请求、集中化 drain-aware abort 语义，进一步优化 PD 分离下的吞吐与正确性。
- **HiCache（分层 KV 缓存）修复链**：cgroup 页缓存记账、SWA write-back 备份与断言冲突等修复，体现对大规模长上下文场景中 KV 缓存可靠性的重视。
- **sgl-router 健壮性**：KV 事件序列缺口修复、信用预扣、replay endpoint 通告，说明路由层正在完善 KV 事件驱动的调度闭环。
- **DeepSeek-V4.1 / AMD 后端投入**：融合 c1/c2 压缩、FP4 索引 kernel、HIP 后端 CP V2 移植，表明对国产/替代硬件与前沿模型架构的性能持续投入。
- **基础设施**：AOT kernel 对齐 Torch 2.14、AITER 权重切分修复，保障与上游框架和芯片生态同步。

## 3. 对项目的影响与意义
- 解码器重构大幅降低新增模型适配的边际成本，有利于 SGLang 扩展模型覆盖。
- PD 分离与 HiCache 的修复/优化提升超大模型服务的稳定性和有效吞吐，契合项目"Fast inference"的目标。
- metrics 与治理结构（CODEOWNERS）的完善有利于生产环境可观测性与长期维护。
- 部分提交由 Claude/AI 协同完成，反映社区开发流程的变化。

## 4. 值得关注的技术点
- "stage boundaries" 作为统一的阶段边界与求和收口机制，可能成为后续模型适配的默认范式。
- NCCL 端口选择规避内核临时端口范围的细节修复，体现对大规模集群部署稳健性的关注。
- `supports_prefix_sharing` 替代 `is_chunk_cache`/`is_tree_cache`，缓存能力抽象更清晰，利于支持混合缓存策略。
- Hf3fsMockClient 线程安全（pread/pwrite）修复，反映文件系统层并发正确性要求提升。

## 5. 对项目发展的整体影响
结合 README 中"SGLang 面向 LLM 与多模态模型的高速推理"定位，本批提交显示项目正处于**架构统一化与多硬件/多模型扩张期**：一边通过 stage boundaries 等重构夯实代码基座，一边在 PD 分离、分层缓存、DeepSeek/AMD 等前沿方向上补齐性能与可靠性短板。这有助于 SGLang 在高吞吐、长上下文、多模型混合服务场景中保持竞争力，同时降低社区贡献与模型集成门槛，为其生态扩张奠定基础。

## 详细提交记录

### [4ab720e](https://github.com/sgl-project/sglang/commit/4ab720e6557b44d07bde471ed52a178795298f1a)

- **作者**: metamergebot
- **时间**: 2026-10-03T23:01:32Z
- **提交信息**: [HiCache] Fix cgroup page-cache accounting and the sizing fallback when cgroup discovery fails (#42420)

Co-authored-by: merrymercy <merrymercy@users.noreply.github.com>
Co-authored-by: xiezhq-hermann <xiezhq-hermann@users.noreply.github.com>
Co-authored-by: nvjullin <nvjullin@users.noreply.github.com>

### [4301be7](https://github.com/sgl-project/sglang/commit/4301be7bdb70a078b5402fc83ee52b209f2256b3)

- **作者**: metamergebot
- **时间**: 2026-10-03T23:00:53Z
- **提交信息**: Pick the default nccl_port below the kernel ephemeral range (#42405)

Co-authored-by: merrymercy <merrymercy@users.noreply.github.com>

### [10edb05](https://github.com/sgl-project/sglang/commit/10edb05e72afb79ecfdf7dbe7603f90ba05ad3ee)

- **作者**: Cheng Wan
- **时间**: 2026-10-03T21:59:32Z
- **提交信息**: [Refactor] Let the remaining placement consumers read the parallel context (#42348)

### [07064fd](https://github.com/sgl-project/sglang/commit/07064fd4a486aeef6c4c648a1895389e0ae96880)

- **作者**: Kan Wu
- **时间**: 2026-10-03T21:57:49Z
- **提交信息**: [sgl-router] Credit routed prompts before their KV events arrive (#42276)

Co-authored-by: Kan Wu <kan.wu@radixark.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Kan Wu <kan.wu@MacBook-Pro.local>

### [b2aa993](https://github.com/sgl-project/sglang/commit/b2aa993cb8b760df1c0ffdcee79fd6d2f144101d)

- **作者**: Cheng Wan
- **时间**: 2026-10-03T21:54:12Z
- **提交信息**: [Fix] Skip a draft's decode recapture when it owns no decode graph (#42347)

### [1a18de4](https://github.com/sgl-project/sglang/commit/1a18de4b290c24cfb7d7256192da64912ce6d70c)

- **作者**: Cheng Wan
- **时间**: 2026-10-03T21:52:25Z
- **提交信息**: [Fix] Load a draft's tensor weight update from its deployment TP rank (#42346)

### [061e712](https://github.com/sgl-project/sglang/commit/061e712bab24454e5b08e88e83d26592e61fdce8)

- **作者**: sglang-bot
- **时间**: 2026-10-03T21:29:04Z
- **提交信息**: chore: bump sgl-kernel version to 0.4.9 (#42427)

Co-authored-by: sglang-bot <sglang-bot@users.noreply.github.com>

### [3122b9c](https://github.com/sgl-project/sglang/commit/3122b9c9951993dba6a780de8144c108f47c8181)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-10-03T21:26:34Z
- **提交信息**: Update AOT kernels for Torch 2.14 (#42366)

Co-authored-by: Mohammad Angkad <mohammad.angkad@radixark.ai>

### [df53c97](https://github.com/sgl-project/sglang/commit/df53c978f147a25b5fdbb1a6d40dab862fa8bcd2)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-03T21:11:13Z
- **提交信息**: [mem_cache] Run mamba models on `UnifiedRadixCache` when the radix cache is disabled (#42354)

### [3e9a120](https://github.com/sgl-project/sglang/commit/3e9a120adde240ba62abfe78c54ce367e32bfae9)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-03T21:02:24Z
- **提交信息**: [Fix] Make Hf3fsMockClient reads and writes thread-safe with pread/pwrite (#42425)

### [8bf780d](https://github.com/sgl-project/sglang/commit/8bf780dda5ab44c75ca835dca995a96ea8807433)

- **作者**: FREETRUMP
- **时间**: 2026-10-03T20:52:21Z
- **提交信息**: feat(metrics): expose deferred decode KV release metrics (#41128)

Co-authored-by: Shangming Cai <csmthu@gmail.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [749a89a](https://github.com/sgl-project/sglang/commit/749a89abd60af9351135480f70d7666f8b95e628)

- **作者**: Yanbin Jiang
- **时间**: 2026-10-03T20:43:40Z
- **提交信息**: [LoRA] Reorganize kernels and add CODEOWNERS (#42299)

### [fd5e68f](https://github.com/sgl-project/sglang/commit/fd5e68f99e552b98d1086e543b2a958899e8632b)

- **作者**: Kan Wu
- **时间**: 2026-10-03T20:43:17Z
- **提交信息**: [sgl-router] Repair KV-event sequence gaps from the engine's replay socket (#42275)

Co-authored-by: Kan Wu <kan.wu@radixark.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Kan Wu <kan.wu@MacBook-Pro.local>

### [aaf7ebe](https://github.com/sgl-project/sglang/commit/aaf7ebe0779f4eb8898fc396ee56ddf850253a83)

- **作者**: Kan Wu
- **时间**: 2026-10-03T20:42:33Z
- **提交信息**: Advertise the KV-event replay endpoint in /server_info (#42274)

Co-authored-by: Kan Wu <kan.wu@radixark.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [3dc7f4b](https://github.com/sgl-project/sglang/commit/3dc7f4b816707781716f30446433467c66c4c0ed)

- **作者**: AMD-yanfeiwang
- **时间**: 2026-10-03T19:14:28Z
- **提交信息**: fix(cuda-graph): remove unnecessary CP batch alignment (#40543)

### [e83c95b](https://github.com/sgl-project/sglang/commit/e83c95b6507d3cdaf1e9501144439d78dfd9c5de)

- **作者**: AMD-yanfeiwang
- **时间**: 2026-10-03T19:09:08Z
- **提交信息**: [AMD] Fix AITER weight slicing for CP decode TP (#39950)

### [f327f92](https://github.com/sgl-project/sglang/commit/f327f92424d4db6b37e9776b895d265882c6ba2c)

- **作者**: AMD-yanfeiwang
- **时间**: 2026-10-03T19:08:17Z
- **提交信息**: [AMD] Port CP V2 to the DeepSeek-V4 HIP backend (#34200)

### [6acf2f4](https://github.com/sgl-project/sglang/commit/6acf2f47365c3b9d4c69d05e8465d03d0a3b24e3)

- **作者**: metamergebot
- **时间**: 2026-10-03T19:02:21Z
- **提交信息**: [PD] Keep ingesting requests while a prefill forward result is pending (#42035)

Co-authored-by: merrymercy <merrymercy@users.noreply.github.com>
Co-authored-by: Jialin <Jialin@users.noreply.github.com>

### [b016ca4](https://github.com/sgl-project/sglang/commit/b016ca406fa7079625525f99d0fe638b1dcb7f5a)

- **作者**: metamergebot
- **时间**: 2026-10-03T16:54:20Z
- **提交信息**: Support post-capture KV sizing for the unified hybrid-SWA pool (#41961)

Co-authored-by: merrymercy <merrymercy@users.noreply.github.com>
Co-authored-by: ZYHowell <ZYHowell@users.noreply.github.com>

### [2bae12b](https://github.com/sgl-project/sglang/commit/2bae12b9b355b6d149b2db4ca30352aa20755f1c)

- **作者**: metamergebot
- **时间**: 2026-10-03T16:45:56Z
- **提交信息**: [HiCache] Fix write-back SWA insert backups tripping the write-through pending-ack assert (#42264)

Co-authored-by: merrymercy <merrymercy@users.noreply.github.com>
Co-authored-by: 842974287 <842974287@users.noreply.github.com>

### [5b5d721](https://github.com/sgl-project/sglang/commit/5b5d72123935dc2a3fb341790796ec1a987d31ce)

- **作者**: Evan Kriminger
- **时间**: 2026-10-03T13:03:09Z
- **提交信息**: [PD] Add opt-in prefill-complete decode KV allocation (#40703)

Co-authored-by: Po-Han Huang (NVIDIA) <53919306+nvpohanh@users.noreply.github.com>
Co-authored-by: Po-Han Huang <pohanh@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Shangming Cai <csmthu@gmail.com>

### [5916999](https://github.com/sgl-project/sglang/commit/5916999afbc595de62dffca077fd8249634b4e74)

- **作者**: DarkSharpness
- **时间**: 2026-10-03T11:31:05Z
- **提交信息**: [DSv4.1] Fused c1/c2 compress for eager extend, faster c2 decode (#41660)

Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: BBuf <1182563586@qq.com>

### [d75d5b3](https://github.com/sgl-project/sglang/commit/d75d5b33f71a64ef1d20ee19b0706046dbc3737f)

- **作者**: DarkSharpness
- **时间**: 2026-10-03T10:25:22Z
- **提交信息**: [DSv4.1] Faster fp4 index-K gather and combine_topk_swa_indices (#41658)

Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: BBuf <1182563586@qq.com>

### [379ec90](https://github.com/sgl-project/sglang/commit/379ec90fb24afd050e0721ee7482c573e8a213cc)

- **作者**: DarkSharpness
- **时间**: 2026-10-03T10:24:41Z
- **提交信息**: [DSv4.1] Fold q_rope_store into fused_q_norm_rope (#41657)

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [7be5e34](https://github.com/sgl-project/sglang/commit/7be5e3473cdbb2d2ffab252eed4b6b4bcfabdf0d)

- **作者**: Cheng Wan
- **时间**: 2026-10-03T09:21:55Z
- **提交信息**: [Refactor] Drop the reduction-skip mechanisms stage boundaries no longer use (#42312)

### [71b04e0](https://github.com/sgl-project/sglang/commit/71b04e02cfd8cf04353c183fd71a22efc9b91722)

- **作者**: Cheng Wan
- **时间**: 2026-10-03T09:21:34Z
- **提交信息**: [Refactor] Build the ZAYA1, IQuest-Q1 and Gemma 4 decoders from stage boundaries (#42311)

### [f85c2c4](https://github.com/sgl-project/sglang/commit/f85c2c492307471259f314a6fc195055a4154cb4)

- **作者**: Cheng Wan
- **时间**: 2026-10-03T09:21:10Z
- **提交信息**: [Fix] GigaChat 3.5: apply the sandwich norms to the complete sums (#42310)

### [6faccf3](https://github.com/sgl-project/sglang/commit/6faccf3e844837e1b4b86832b4fdf8b1a82904f1)

- **作者**: Cheng Wan
- **时间**: 2026-10-03T09:20:40Z
- **提交信息**: [Refactor] Build the GLM-4, GLM-Image and Granite MoE hybrid decoders from stage boundaries (#42309)

### [e4554fd](https://github.com/sgl-project/sglang/commit/e4554fd5e5fcc9a2d5b207760fc0e3fb6af9c7e2)

- **作者**: Cheng Wan
- **时间**: 2026-10-03T09:20:18Z
- **提交信息**: [Refactor] Build the Llama and Nemotron-NAS decoders from stage boundaries (#42308)

### [740a4d5](https://github.com/sgl-project/sglang/commit/740a4d59556fbcd0e04da22e3a20126d5fad0c77)

- **作者**: Cheng Wan
- **时间**: 2026-10-03T09:19:56Z
- **提交信息**: [Refactor] Build the Qwen2 decoders from stage boundaries (#42307)

### [2c739b2](https://github.com/sgl-project/sglang/commit/2c739b225b4171fda438e01e69f5f0f4505e7ebd)

- **作者**: Cheng Wan
- **时间**: 2026-10-03T09:19:33Z
- **提交信息**: [Fix] Jet-Nemotron build and Granite MoE hybrid final norm (#42306)

### [b7fc516](https://github.com/sgl-project/sglang/commit/b7fc51698601b4634a138ba6422c9b38a2e2cb10)

- **作者**: Cheng Wan
- **时间**: 2026-10-03T09:19:19Z
- **提交信息**: [Fix] EXAONE MoE under DP attention and DeepEP (#42305)

### [2fa17a6](https://github.com/sgl-project/sglang/commit/2fa17a64671b2c085e7792510b8d61f29849c730)

- **作者**: Cheng Wan
- **时间**: 2026-10-03T09:18:56Z
- **提交信息**: [Refactor] Build the ERNIE 4.5 VL MoE and EXAONE MoE decoders from stage boundaries (#42304)

### [f89ead1](https://github.com/sgl-project/sglang/commit/f89ead192f3cf7a541be88518691fd6a95e9ff3e)

- **作者**: Cheng Wan
- **时间**: 2026-10-03T09:18:33Z
- **提交信息**: [Fix] EXAONE and ERNIE 4.5 VL MoE architecture, backend and PP issues (#42303)

### [be20e74](https://github.com/sgl-project/sglang/commit/be20e7453cc8a65ce81cc827dfdfa5c4fd8ce43d)

- **作者**: Cheng Wan
- **时间**: 2026-10-03T09:18:11Z
- **提交信息**: [Fix] Step-3.5 DeepEP routed scaling and Sarvam shared expert under dense TP1 (#42302)

### [b157d54](https://github.com/sgl-project/sglang/commit/b157d548bb3a648a98f47559c6d7db2e84a80ba6)

- **作者**: Cheng Wan
- **时间**: 2026-10-03T09:17:48Z
- **提交信息**: [Refactor] Let stage boundaries complete every stage-output sum (#42301)

### [d5a8d76](https://github.com/sgl-project/sglang/commit/d5a8d76bf5061e0ecaae4e0db658b6cf66841cb5)

- **作者**: Cheng Wan
- **时间**: 2026-10-03T09:17:26Z
- **提交信息**: [Refactor] Drop TBO op methods that no strategy ever schedules (#42300)

### [122b591](https://github.com/sgl-project/sglang/commit/122b59152cb136dfcd240504cfe9abc374e4fc5a)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-03T09:07:55Z
- **提交信息**: [mem_cache] Replace `is_chunk_cache` / `is_tree_cache` with `supports_prefix_sharing` (#42362)

### [8293f9a](https://github.com/sgl-project/sglang/commit/8293f9af543a6adb8ae4269926e53c4c46d1f585)

- **作者**: Banruo Liu
- **时间**: 2026-10-03T08:51:11Z
- **提交信息**: [PD] Centralize drain-aware abort acknowledgements (#37077)

### [1093c50](https://github.com/sgl-project/sglang/commit/1093c501dfef0789b46fc3afe44949e35867a11a)

- **作者**: saatwiknagpal
- **时间**: 2026-10-03T07:54:54Z
- **提交信息**: [diffusion] optimization: route subBlock sparse attention in head chunks (#41985)

### [254aa41](https://github.com/sgl-project/sglang/commit/254aa41f7876ba75e56d22f609512dcf87e20d5a)

- **作者**: Yanbin Jiang
- **时间**: 2026-10-03T07:37:57Z
- **提交信息**: [Fix] Guard DeepSeek NVFP4 shared-expert fusion for LoRA and FP4 backends (#42203)

### [ce617d4](https://github.com/sgl-project/sglang/commit/ce617d410bce1a9db48bbada8ee97a1286729e84)

- **作者**: Tokha233
- **时间**: 2026-10-03T07:23:41Z
- **提交信息**: [diffusion] fix: fix native FP8 format handling for FLUX 3 row-wise linears (#42255)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-10-04
**监控日期**: 2026-10-03
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1288
- **最后更新**: 2026-10-03T18:50:23Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-10-04
**监控日期**: 2026-10-03
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 93129
- **最后更新**: 2026-10-04T00:38:19Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 6
- **主要提交者**: Hexiang Wang, aoshen02, Wei Zhao

## AI分析总结

# vLLM 仓库昨日提交分析（1/1 批，共 6 条）

## 1. 主要更新类型

- **功能新增**：DCP 下的 MLA TokenSpeed 启用、prefill 逐行候选 ID 评分（M2 阶段）、/inference/v1/generate 接口增加 output_mode
- **Bug 修复**：RDNA3 上 W4A16 split-K 精度/确定性问题、MoRIIO 工人持 GIL 时发现心跳中断、Mooncake KV 连接器空拉取误报完成

## 2. 关键变更点及与项目方向的关系

vLLM 的核心目标是"Easy, fast, and cheap LLM serving"。本次提交从三个层面支撑该目标：

- **推理性能与并行度**：DCP（分布式上下文并行）与 MLA（Multi-head Latent Attention）的 TokenSpeed 支持表明项目在持续扩展 MoE/MLA 模型的分布式推理路径，目标是让大模型在多 GPU 场景下更高效地服务。
- **硬件生态覆盖**：ROCm/RDNA3 的修复说明社区在维护 AMD GPU 兼容性，降低用户获取门槛、提升服务的可移植性，符合"cheap serving"的定位。
- **服务接口与可观测性**：output_mode 的加入以及 MoRIIO 心跳稳定性修复，体现了项目对在线服务能力（Serving 语义、健康检测、API 标准化）的持续投入，与 RFC #56851 等规范进程呼应。
- **高级 KV/调度能力**：Mooncake KV 连接器的修复表明项目在探索 KV 缓存共享与传输生态，这是提升多节点吞吐、降低服务成本的关键方向。
- **投机/评分基础设施**：逐行候选 ID 评分是投机解码（speculative decoding）类工作的推进（M2 阶段），有助于提高小模型辅助大模型的解码质量。

## 3. 对项目的影响和潜在意义

- **对用户**：更稳定的 AMD GPU 表现、更可靠的分布式 KV 拉取行为、更丰富的生成 API 选项，直接降低部署与调试成本。
- **对模型作者**：MLA/DCP 路径的打通让 MoE 系列模型的多卡服务路径更成熟，扩大了 vLLM 可覆盖的模型范围。
- **对生态**：RFC 驱动的接口演进（如 output_mode）和 MoRIIO、Mooncake 等协作组件的修复，显示出 vLLM 正从"单点推理引擎"向"可扩展的服务框架"演进。

## 4. 值得关注的技术点

- **GIL 与多线程/多进程协作模式**：MoRIIO 心跳问题揭示了在 Python 生态下长任务（如推理）持锁时，旁路管理线程（发现、心跳）仍需独立运行的常见陷阱，修复方案对其他扩展组件有借鉴意义。
- **W4A16 split-K 的确定性**：量化 + split-K + ROCm 组合出现精度/确定性偏差，是 GPU kernel 级别的底层问题，修复表明项目对推理数值稳定性的重视。
- **DCP × MLA 的 block-interleaved 设计**：这是并行策略与注意力算子的深度融合，值得关注其后续在不同模型/硬件上的推广。
- **投机解码评分的逐行粒度**：M2 阶段暗示该特性会分阶段上线，后续可能影响投机解码的整体实现架构。

## 5. 基于 README 背景的项目发展意义

README 明确 vLLM 的使命是面向所有人的高效、低成本 LLM 服务。昨日提交体现了两大主线：

1. **拓宽覆盖**：AMD GPU 修复、DCP/MLA 扩展，让更多硬件与模型类型进入服务范围；
2. **深化服务能力**：API 输出模式、KV 连接器稳定性、发现心跳可靠性，都是面向生产部署的打磨。

总体而言，vLLM 正在从追求峰值吞吐转向兼顾**可移植性、稳定性和标准化接口**的综合演进，这对"Easy, fast, and cheap"的愿景是必要且良性的推进。

## 详细提交记录

### [84bcbc6](https://github.com/vllm-project/vllm/commit/84bcbc62644356270aaaa5e2d0237d03adc9bb3a)

- **作者**: Wei Zhao
- **时间**: 2026-10-03T17:26:07Z
- **提交信息**: [DCP] Enable TokenSpeed MLA with block-interleaved DCP (#59462)

Signed-off-by: Wei Zhao <51183510+wzhao18@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [4ac0d0e](https://github.com/vllm-project/vllm/commit/4ac0d0eac25eecc98ff519887f2aa3d659dc75f3)

- **作者**: AIwork4me
- **时间**: 2026-10-03T15:44:17Z
- **提交信息**: [ROCm][RDNA3] Fix W4A16 split-K accuracy and determinism (#54706)

Signed-off-by: AIwork4me <AIwork4me@users.noreply.github.com>
Co-authored-by: AIwork4me <AIwork4me@users.noreply.github.com>
Co-authored-by: JartX <sagformas@epdcenter.es>

### [f03026a](https://github.com/vllm-project/vllm/commit/f03026a548b18ba0a99ca0a632b9343f25a66bc9)

- **作者**: Hexiang Wang
- **时间**: 2026-10-03T14:55:18Z
- **提交信息**: [Bugfix][MoRIIO] Keep discovery heartbeats running while workers hold the GIL (#59441)

Signed-off-by: whx-sjtu <xiaowang990929@gmail.com>
Co-authored-by: Codex <noreply@openai.com>

### [e319f86](https://github.com/vllm-project/vllm/commit/e319f86f15f3bf72d9016d5324500730a1f16e25)

- **作者**: aoshen02
- **时间**: 2026-10-03T14:17:09Z
- **提交信息**: [Feature] Per-row candidate IDs for prefill token scoring (M2 of #56860) (#56984)

Signed-off-by: aoshen02 <aoshen02@users.noreply.github.com>
Co-authored-by: aoshen02 <aoshen02@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [bc21cba](https://github.com/vllm-project/vllm/commit/bc21cba9673cfc2256a2726b4bc32f062237cd35)

- **作者**: Martin Hickey
- **时间**: 2026-10-03T11:38:25Z
- **提交信息**: [Frontend] Add output_mode to /inference/v1/generate (RFC #56851 Phase 1) (#58588)

Signed-off-by: Martin Hickey <martin.hickey@ie.ibm.com>

### [5f30fc7](https://github.com/vllm-project/vllm/commit/5f30fc7031cae49bf51073fc953d419b08f8887c)

- **作者**: Yicong Wang
- **时间**: 2026-10-03T07:28:00Z
- **提交信息**: [Bugfix][KV Connector][Mooncake] Suppress completion for empty pulls (#59347)

Signed-off-by: wangyicong <wangyicong@bytedance.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-10-04
**监控日期**: 2026-10-03
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7037
- **最后更新**: 2026-10-03T23:17:35Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---
