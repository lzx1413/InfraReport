# GitHub Stars 合并报告 - 2026-06-30

**合并日期**: 2026-07-01
**监控日期**: 2026-06-30
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


**报告日期**: 2026-07-01
**监控日期**: 2026-06-30
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2048
- **最后更新**: 2026-06-30T16:49:51Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-07-01
**监控日期**: 2026-06-30
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2449
- **最后更新**: 2026-06-30T16:33:09Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 1
- **主要提交者**: yihuiwen

## AI分析总结

好的，根据你提供的仓库背景和提交记录，以下是昨日更新的分析总结：

---

### 1. 主要更新类型
- **功能新增**：添加构建镜像脚本（`add build image script`）。
- **Bug修复**：修复异步任务管理中可能存在的阻塞问题（`remove blocking asyncio gather after cancelling disconnect watch`）。

### 2. 关键变更点及其与项目整体方向的关系
- **构建镜像脚本**：为项目提供了自动化容器化部署的能力。这与 LightX2V 作为“轻量视频生成推理框架”的定位一致——降低用户环境配置门槛，方便快速上手和规模化部署。
- **修复异步阻塞**：修复了在取消 watch 连接后仍可能存在的 `asyncio.gather` 阻塞问题。这直接关系到框架的**响应性与稳定性**，尤其是多客户端并发请求场景下，避免因遗留协程导致的服务卡顿或资源泄露。

### 3. 对项目的影响和潜在意义
- **部署效率提升**：镜像脚本使得用户可以通过 Docker 一键构建运行环境，极大简化了从源码到服务的流程，适合快速演示、团队协作或生产环境标准化部署。
- **系统鲁棒性增强**：阻塞消除后，框架在客户端断开/重连时能更及时地释放资源，降低长连接场景下的资源占用，提升高并发下的吞吐能力。对于视频生成这种计算密集型任务，稳定性的优化尤其重要。

### 4. 值得关注的技术点
- **异步编程模式**：使用了 `asyncio.gather` 进行并发管理，修复中强调“取消后移除阻塞”，体现了对 Python 异步事件循环的精细控制，避免僵尸任务。
- **Dockerfile 或构建脚本**：具体脚本内容可能涉及 CUDA、PyTorch、FFmpeg 等依赖的安装，与视频生成的底层库绑定紧密，对跨平台兼容性有参考价值。

### 5. 这些提交如何影响项目发展
- **推动工程化成熟度**：从纯研究原型向可部署产品迈进。镜像脚本是基础设施的关键一步，有助于项目吸引更多用户（尤其是不熟悉环境搭建的开发者）。
- **维护长期可靠性**：主动清理遗留异步任务，说明项目已关注到高负载下的极限场景。这类修复能提升项目口碑，为后续更复杂的多模态生成、流式推理等功能打下稳定基础。

---

综上，昨日的更新兼顾了**易用性**（部署脚本）与**健壮性**（异步修复），体现了 LightX2V 从实验框架向生产级推理引擎的演进趋势。

## 详细提交记录

### [16d7202](https://github.com/ModelTC/LightX2V/commit/16d7202472584953044a257c6a576399da0653c9)

- **作者**: yihuiwen
- **时间**: 2026-06-30T13:42:50Z
- **提交信息**: add build image script (#1203)

Co-authored-by: yihuiwen <yihuiwen@sensetime.com>

### [152ac49](https://github.com/ModelTC/LightX2V/commit/152ac492ca70dd5d42e60859b302ef5c94c6a525)

- **作者**: yihuiwen
- **时间**: 2026-06-30T08:05:19Z
- **提交信息**: fix: remove blocking asyncio gather after cancelling disconnect watch… (#1202)


Co-authored-by: yihuiwen <yihuiwen@sensetime.com>

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-07-01
**监控日期**: 2026-06-30
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2150
- **最后更新**: 2026-06-30T09:58:47Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-07-01
**监控日期**: 2026-06-30
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5878
- **最后更新**: 2026-06-30T23:14:00Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 6
- **主要提交者**: Brian K. Ryu, Anerudhan Gopal, Sam (Kesen Li)

## AI分析总结

好的，以下是对 `flashinfer-ai/flashinfer` 仓库昨日提交记录的分析总结，结合项目背景（高性能 GPU 推理内核）进行解读：

---

## 1. 主要更新类型

| 类型 | 对应提交 |
|------|----------|
| **功能新增** | fe88845（MoE-EP 专家并行）、c046462（融合共享专家 FP8）、b43c480（SM120 CP delta rule） |
| **Bug 修复 / 构建优化** | 54a6156（排除 head_dim=512 FA2 模块） |
| **文档/API 纠正** | 900515a（MoE 最终 allreduce 输入形状说明） |
| **性能优化 / 重构** | e3acc34（移除冗余 MoE tensor 分配） |

---

## 2. 关键变更点及其与项目方向的关系

- **MoE-EP（fe88845）**：  
  将 FlashInfer 的统一 MoE 计算 API 接入 **专家并行（Expert Parallelism）** 框架，支持 NCCL-EP 和 NIXL-EP 两种可插拔传输后端，并提供低延迟（LL）和高吞吐（HT）两种算法布局。这是项目向大规模分布式推理演进的关键一步，直接对齐现代大模型（如 Mixture of Experts）的多卡/多节点部署需求。

- **融合共享专家 FP8（c046462）**：  
  为 TensorRT-LLM 生成的 MoE 增加 fused shared expert 支持，允许专家计数和

## 详细提交记录

### [fe88845](https://github.com/flashinfer-ai/flashinfer/commit/fe8884576c30aa49bba1e96b48b759150f79c7ec)

- **作者**: Anerudhan Gopal
- **时间**: 2026-06-30T22:51:14Z
- **提交信息**: MoE-EP: wire unified MoE compute into NCCL-EP / NIXL-EP expert parallel (LL + HT) (#3686)

## Summary

Wires FlashInfer's unified MoE compute API into **expert parallelism**:
a new
`flashinfer.moe_ep.MoEEpLayer` runs one MoE layer split across ranks as
**dispatch → per-expert grouped GEMM → combine**, over a pluggable
transport
(**NCCL-EP** via `nccl.ep`/`nccl4py`, and **NIXL-EP**). The expert GEMM
reuses the
unified `flashinfer.fused_moe.MoELayer` as a pure per-expert grouped
GEMM (routing
lives in dispatch/combine).

## What's included

- **`MoEEpLayer`** (`flashinfer/moe_ep/`) with both algorithms and all
three receive
  layouts:
- **Low-Latency** — `EXPERT_MAJOR` (combine reweights on receive) and
`RANK_MAJOR`
    (received-routing, combine sums across ranks).
- **High-Throughput** — `FLAT` (token-major received routing, unweighted
combine).
- **Backends**: `nccl_ep` (nccl4py ≥ 0.3.1, `nccl.ep` v0.1.0) and
`nixl_ep`; built via
  the `[nvep]` extra (`BUILD_NCCL_EP=1`).
- **Container**: `docker/Dockerfile.flashinfer-ep-pytorch` (PyTorch
base, CUDA 13.2) —
required for cross-node HT (GIN/GDAKI); the CUDA-13.0 image aborts
multi-node HT at
`nccl_ep.cc:2884` (shown to be the base image's IB/GPUDirect runtime,
not FlashInfer).
- **Benchmarks**: `bench_moe_ep.py` (full MoE) and `bench_ep_matrix.py`
(comm-only,
ep_bench-comparable), plus a SLURM matrix harness. An opt-in host-call
fast path
(`NV_FI_EP_FAST_PATH=1`) and a per-step host-wall burn-down
(`EP_PROFILE_HOST=1`).
- **Tests**: `tests/moe_ep/` — multi-GPU numerical correctness
(`test_moe_ep_compute_correctness.py`, `test_moe_ep_ht_correctness.py`),
layout-bridge
  unit tests, config/constraints, and transport smokes.
- **Docs**: `benchmarks/MoE_benchmarks.md` (container/run/results vs
ep_bench) and
`docs/design_docs/MoE_EP_impl.md` (API + call stack + correctness-test
walkthrough).

## Correctness

8× B200, bf16: EP `dispatch→compute→combine` matches the same `MoELayer`
kernel run
non-EP to **rel-err ≈ 0.0045** for both LL layouts and **≈ 0.007** for
HT FLAT
(4096/8192 tok/rank). Two multi-rank bugs found & fixed (global-vs-local
expert ids;
local→global `topk_idx` for RANK_MAJOR/HT).

## Benchmarks (Pre-Nyx B200) vs ep_bench

FlashInfer and the upstream `contrib/nccl_ep/ep_bench` reference launch
**byte-identical**
dispatch/combine kernels with the **same GPU time**, single-node and to
64 GPU (verified by
Nsight Systems). The Python host-call overhead was profiled and reduced
behind the opt-in
`NV_FI_EP_FAST_PATH` (LL dispatch host-wall 101→17 µs); validated
multi-node
(`--validate` dispatch+combine OK at 8/16/32/64 GPU). HT is
library-bound on the blocking
`nccl.ep` dispatch. See `benchmarks/MoE_benchmarks.md`.

Validated bf16 end-to-end on GB200 (SM100), GB300 (SM103), GB200-NVL36,
and Pre-Nyx B200,
on both `nccl_ep` and `nixl_ep`.

## Known limitations / follow-ups

- LL **64-GPU** (8-node) `nccl_ep` fails at `nccl_ep.cc:1491` (LL-GIN
dev-comm setup) —
  library-side; HT 64-GPU passes on the same nodes.
- **NVFP4** compute path is a tracked follow-up (illegal memory access
in the fused GEMM).
- `NV_FI_EP_FAST_PATH` stays **opt-in**: it currently covers LL
EXPERT_MAJOR + HT and
changes the `num_tokens`/buffer-aliasing contracts (see doc); to be
extended + audited
  before defaulting.

## Notes

- Depends on `nccl4py >= 0.3.1` (the `nccl.ep` API); no in-tree NCCL
build. NCCL-EP's GIN
transport needs the GDAKI/GPUDirect stack at runtime, and **NCCL ≥
2.30.7** on B200
  (with `NCCL_MNNVL_ENABLE=1` for multi-node).

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

## Release Notes

* **New Features**
* Added Mixture-of-Experts Expert-Parallel benchmarking (comm matrix +
end-to-end compute) with ready-to-run SLURM/PyTorch launchers.
* Enhanced `MoEEpLayer` with an optional layout-aware dispatch → compute
→ combine path.
* Introduced EP layout support (`EpLayout`) and improved backend/quant
variant validation.

* **Documentation**
* Added an EP implementation design doc and a benchmarking guide with
example commands/results.

* **Build & Infrastructure**
* Updated NCCL-EP to a wheel-based flow, refreshed Docker images, and
tightened runtime version pinning.

* **Tests**
* Added compute-bridge and LL/HT correctness suites; updated NCCL-EP
mocking for the new API surface.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [e3acc34](https://github.com/flashinfer-ai/flashinfer/commit/e3acc340652e50d2e0d80b1cd039e6f48ebc4599)

- **作者**: Lain
- **时间**: 2026-06-30T21:42:22Z
- **提交信息**: feat: [MoE] remove redundent trtllm-gen moe tensor allocation (#3721)

<!-- .github/pull_request_template.md -->

## 📌 Description

Remove the redundant `activation_output`, and the `output` when
`do_finalize` is false.

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

* **Bug Fixes**
* Improved MoE output handling so intermediate (non-finalize) runs use a
placeholder output when no output tensor is provided.
* Reduced unnecessary activation/workspace buffer allocations across
BF16/FP8/FP4 MoE variants to lower memory usage.
* Limited output compatibility checks to finalize steps, avoiding
redundant validation during intermediate execution.
* **Refactor**
* Centralized MoE output-buffer allocation logic and aligned all MoE
wrapper behavior with the finalize vs. non-finalize flow.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Siyuan Fu <siyuanf@nvidia.com>

### [c046462](https://github.com/flashinfer-ai/flashinfer/commit/c0464625d0ab3fb02cbb8b0c3785e4d8014af848)

- **作者**: nv-yunzheq
- **时间**: 2026-06-30T20:44:01Z
- **提交信息**: feat: Fuse shared experts into trtllm_gen moe (fp8) (#2625)

<!-- .github/pull_request_template.md -->

For #2551 
Integrating https://github.com/NVIDIA/TensorRT-LLM/pull/11143

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

* **New Features**
* Support for fused shared experts in MoE runtime and kernels, expanding
per-token expert counts and routing behavior.

* **Bug Fixes**
* Improved runtime validations and sizing for fused-expert
configurations; clearer error messages for weight/scale sizing.

* **Tests**
* Added and extended tests covering fused shared expert scenarios and
routing variants.

* **Documentation**
  * Clarified num_experts meaning in FP8 block-scale MoE docs.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Alex Yang <aleyang@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [54a6156](https://github.com/flashinfer-ai/flashinfer/commit/54a6156f66d4d98a9aaa0ba78d64d3f6a3050860)

- **作者**: Brian K. Ryu
- **时间**: 2026-06-30T18:30:19Z
- **提交信息**: fix(aot): exclude head_dim=512 FA2 modules from AOT jit-cache wheel (#3769)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

#3757 reports that the `flashinfer-jit-cache` wheel for CUDA 12.9 x86_64
exceeded GitHub Releases' asset upload limit. The head_dim=512 FA2
support added in #3576 is one of the contributors.

The `(512, 512)` entry in the default `fa2_head_dim` AOT list adds ~326
MB. This PR removes `(512, 512)` from the **default** AOT configuration
so those modules are no longer baked into the released wheel.
**head_dim=512 remains fully functional** — it now JIT-compiles on
demand on first use (FlashInfer's default behavior), exactly
  like any non-precompiled configuration.
  
This is **not a regression**: no released wheel has ever shipped
head_dim=512 precompiled (the feature landed in #3576, after the last
release).

## 🔍 Related Issues

* #3757
* #3576

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
* Updated the default build configuration to exclude one large
head-dimension option.
* This reduces the size of the generated cache wheel and can help keep
installs leaner.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [900515a](https://github.com/flashinfer-ai/flashinfer/commit/900515ab335f21640b52c22130db32de0262c252)

- **作者**: Sam (Kesen Li)
- **时间**: 2026-06-30T17:55:49Z
- **提交信息**: fix(comm): clarify MoE finalize allreduce input shape (#3754)

<!-- .github/pull_request_template.md -->

Fix doc issue mentioned in
https://github.com/flashinfer-ai/flashinfer/issues/3671

## Summary

Fixes the MoE finalize allreduce fusion API documentation and Lamport
workspace size check.

`trtllm_moe_finalize_allreduce_fusion` takes a permuted/padded MoE
expert output buffer as `allreduce_in`, not a logical `[token_num,
top_k, hidden_dim]` tensor. The kernel indexes this buffer by
`expanded_idx_to_permuted_idx`, so the correct shape is
`[num_permuted_rows, hidden_dim]`.

This also updates the one-shot Lamport size check to use the actual
allreduce payload size, which is the finalized token output `[token_num,
hidden_dim]`, represented by `residual_in.numel()`, instead of the
padded expert buffer size.

## Changes

- Clarify `allreduce_in` shape for
`trtllm_moe_finalize_allreduce_fusion`.
- Compute `required_lamport_comm_size` from `residual_in.numel() *
residual_in.element_size() * world_size`.
- Add a performance note to `allreduce_fusion` docs that
`kMoEFinalizeARResidualRMSNorm` is a TRT-LLM fused implementation and
should be benchmarked before being used as a default replacement for
optimized standalone MoE finalize + standard AR/RMSNorm fusion.

## Evidence

- `csrc/trtllm_moe_allreduce_fusion.cu` sets `params.size =
residual_in.numel()`, so the allreduce payload is the finalized token
output `[token_num, hidden_dim]`.
- `include/flashinfer/comm/trtllm_moe_allreduce_fusion.cuh` loads
`params.allreduce_in + permuted_idx * hidden_dim + offset`, where
`permuted_idx` comes from `expanded_idx_to_permuted_idx`. This means
`allreduce_in` is a row-addressed permuted/padded expert output buffer.
- The previous Python wrapper docstring described `allreduce_in` as
`[token_num, top_k, hidden_dim]`, and the previous size check used
`allreduce_in.numel() * 2 * world_size`, which over-counts when the
expert buffer is padded.


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

* **Documentation**
* Clarified the expected tensor shape and usage for all-reduce fusion in
MoE workflows.
* Added a note that one fused path is TRT-LLM only and may not be the
fastest option for every workload.

* **Bug Fixes**
* Corrected communication size calculation for the MoE finalize
all-reduce path, improving when the optimized one-shot route is
selected.
* Updated payload descriptions to better match the finalized token
output.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [b43c480](https://github.com/flashinfer-ai/flashinfer/commit/b43c480141ef8793f5f48ab831cfc803d720598a)

- **作者**: Guangyun Han
- **时间**: 2026-06-30T15:24:24Z
- **提交信息**: feat: add sm120 cp delta rule (#3659)

## 📌 Description
depends on 
- [x] #3479
- [x] #3481 

## 🔍 Related Issues

- [ ] #3491 

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

## Reviewer Notes

```
GPU: NVIDIA RTX PRO 6000 Blackwell Workstation Edition [SM120]
Models: Qwen3.5 family (397B, 122B, 35B, 27B, 9B, 4B, 2B, 0.8B), d=128

Heads            Seqlens           h_qk  h_v                FI SM120   TFLOPS  FLA/Triton   Speedup
---------------------------------------------------------------------------------------------------
397B/122B TP8    1x65536              2    8                  0.677ms    50.8      2.338ms     3.45x +
397B/122B TP8    1x32768              2    8                  0.403ms    42.6      1.123ms     2.78x +
397B/122B TP8    1x16384              2    8                  0.257ms    33.4      0.518ms     2.01x +
397B/122B TP8    1x8192               2    8                  0.173ms    24.8      0.211ms     1.22x +
397B/122B TP8    1x4096               2    8                  0.123ms    17.4      0.104ms     0.84x -
397B/122B TP8    1x2048               2    8                  0.102ms    10.5      0.063ms     0.62x -
397B/122B TP8    6144+2048            2    8                  0.155ms    27.8      0.180ms     1.17x +
397B/122B TP8    4096+4096            2    8                  0.133ms    32.2      0.146ms     1.09x +
397B/122B TP8    2048+6144            2    8                  0.153ms    28.0      0.179ms     1.17x +
397B/122B TP8    1024+7168            2    8                  0.164ms    26.3      0.195ms     1.19x +
397B/122B TP8    2048x4               2    8                  0.115ms    37.4      0.121ms     1.06x +
397B/122B TP8    1024x8               2    8                  0.077ms    55.7      0.118ms     1.53x +
397B/122B TP8    8192x8               2    8                  0.571ms    60.2      1.662ms     2.91x +
397B/122B TP8    8192x16              2    8                  0.622ms   110.5      3.457ms     5.56x +
397B/122B TP8    8192x32              2    8                  1.324ms   103.8      7.172ms     5.42x +

397B/122B TP4    1x65536              4   16                  1.188ms    57.9      3.734ms     3.14x +
397B/122B TP4    1x32768              4   16                  0.624ms    55.0      1.816ms     2.91x +
397B/122B TP4    1x16384              4   16                  0.351ms    49.0      0.864ms     2.47x +
397B/122B TP4    1x8192               4   16                  0.216ms    39.8      0.380ms     1.76x +
397B/122B TP4    1x4096               4   16                  0.133ms    32.3      0.157ms     1.18x +
397B/122B TP4    1x2048               4   16                  0.104ms    20.6      0.074ms     0.70x -
397B/122B TP4    6144+2048            4   16                  0.208ms    41.4      0.360ms     1.73x +
397B/122B TP4    4096+4096            4   16                  0.197ms    43.6      0.337ms     1.71x +
397B/122B TP4    2048+6144            4   16                  0.207ms    41.5      0.357ms     1.73x +
397B/122B TP4    1024+7168            4   16                  0.212ms    40.5      0.368ms     1.74x +
397B/122B TP4    2048x4               4   16                  0.148ms    58.2      0.344ms     2.33x +
397B/122B TP4    1024x8               4   16                  0.081ms   105.8      0.363ms     4.47x +
397B/122B TP4    8192x8               4   16                  0.618ms   111.2      3.510ms     5.68x +
397B/122B TP4    8192x16              4   16                  1.324ms   103.8      7.247ms     5.47x +
397B/122B TP4    8192x32              4   16                  2.464ms   111.6     14.276ms     5.79x +

397B/122B TP2    1x65536              8   32                  2.604ms    52.8      6.836ms     2.63x +
397B/122B TP2    1x32768              8   32                  1.203ms    57.1      3.331ms     2.77x +
397B/122B TP2    1x16384              8   32                  0.636ms    54.1      1.614ms     2.54x +
397B/122B TP2    1x8192               8   32                  0.359ms    47.9      0.770ms     2.15x +
397B/122B TP2    1x4096               8   32                  0.198ms    43.4      0.332ms     1.68x +
397B/122B TP2    1x2048               8   32                  0.113ms    38.0      0.125ms     1.11x +
397B/122B TP2    6144+2048            8   32                  0.432ms    39.7      0.773ms     1.79x +
397B/122B TP2    4096+4096            8   32                  0.291ms    59.0      0.776ms     2.66x +
397B/122B TP2    2048+6144            8   32                  0.433ms    39.7      0.776ms     1.79x +
397B/122B TP2    1024+7168            8   32                  0.502ms    34.2      0.777ms     1.55x +
397B/122B TP2    2048x4               8   32                  0.164ms   104.9      0.791ms     4.83x +
397B/122B TP2    1024x8               8   32                  0.189ms    91.0      0.811ms     4.30x +
397B/122B TP2    8192x8               8   32                  1.332ms   103.2      7.033ms     5.28x +
397B/122B TP2    8192x16              8   32                  2.472ms   111.2     14.113ms     5.71x +
397B/122B TP2    8192x32              8   32                  4.978ms   110.4     28.748ms     5.78x +

397B/122B TP1    1x65536             16   64                  4.561ms    60.3     13.806ms     3.03x +
397B/122B TP1    1x32768             16   64                  2.290ms    60.0      6.762ms     2.95x +
397B/122B TP1    1x16384             16   64                  1.137ms    60.4      3.316ms     2.92x +
397B/122B TP1    1x8192              16   64                  0.575ms    59.7      1.614ms     2.81x +
397B/122B TP1    1x4096              16   64                  0.292ms    58.9      0.767ms     2.63x +
397B/122B TP1    1x2048              16   64                  0.148ms    58.0      0.338ms     2.28x +
397B/122B TP1    6144+2048           16   64                  0.446ms    77.1      1.636ms     3.67x +
397B/122B TP1    4096+4096           16   64                  0.317ms   108.3      1.647ms     5.19x +
397B/122B TP1    2048+6144           16   64                  0.447ms    76.8      1.640ms     3.67x +
397B/122B TP1    1024+7168           16   64                  0.515ms    66.7      1.636ms     3.18x +
397B/122B TP1    2048x4              16   64                  0.345ms    99.5      1.650ms     4.78x +
397B/122B TP1    1024x8              16   64                  0.301ms   114.2      1.691ms     5.62x +
397B/122B TP1    8192x8              16   64                  2.482ms   110.7     13.944ms     5.62x +
397B/122B TP1    8192x16             16   64                  5.005ms   109.8     28.290ms     5.65x +
397B/122B TP1    8192x32             16   64                  9.828ms   111.9     57.370ms     5.84x +

35B/9B/4B TP1    1x65536             16   32                  2.740ms    50.2      6.835ms     2.49x +
35B/9B/4B TP1    1x32768             16   32                  1.280ms    53.7      3.329ms     2.60x +
35B/9B/4B TP1    1x16384             16   32                  0.658ms    52.2      1.615ms     2.45x +
35B/9B/4B TP1    1x8192              16   32                  0.370ms    46.4      0.769ms     2.08x +
35B/9B/4B TP1    1x4096              16   32                  0.203ms    42.4      0.332ms     1.64x +
35B/9B/4B TP1    1x2048              16   32                  0.114ms    37.7      0.125ms     1.10x +
35B/9B/4B TP1    6144+2048           16   32                  0.434ms    39.6      0.776ms     1.79x +
35B/9B/4B TP1    4096+4096           16   32                  0.294ms    58.5      0.775ms     2.64x +
35B/9B/4B TP1    2048+6144           16   32                  0.434ms    39.5      0.774ms     1.78x +
35B/9B/4B TP1    1024+7168           16   32                  0.505ms    34.0      0.775ms     1.54x +
35B/9B/4B TP1    2048x4              16   32                  0.167ms   103.1      0.789ms     4.74x +
35B/9B/4B TP1    1024x8              16   32                  0.192ms    89.4      0.813ms     4.23x +
35B/9B/4B TP1    8192x8              16   32                  1.372ms   100.1      7.014ms     5.11x +
35B/9B/4B TP1    8192x16             16   32                  2.542ms   108.1     14.138ms     5.56x +
35B/9B/4B TP1    8192x32             16   32                  5.133ms   107.1     28.718ms     5.60x +

27B TP1          1x65536             16   48                  4.101ms    50.3     10.462ms     2.55x +
27B TP1          1x32768             16   48                  2.082ms    49.5      5.125ms     2.46x +
27B TP1          1x16384             16   48                  0.964ms    53.5      2.507ms     2.60x +
27B TP1          1x8192              16   48                  0.521ms    49.5      1.220ms     2.34x +
27B TP1          1x4096              16   48                  0.278ms    46.4      0.566ms     2.04x +
27B TP1          1x2048              16   48                  0.175ms    36.8      0.230ms     1.31x +
27B TP1          6144+2048           16   48                  0.440ms    58.5      1.233ms     2.80x +
27B TP1          4096+4096           16   48                  0.296ms    86.9      1.339ms     4.52x +
27B TP1          2048+6144           16   48                  0.441ms    58.4      1.283ms     2.91x +
27B TP1          1024+7168           16   48                  0.511ms    50.4      1.251ms     2.45x +
27B TP1          2048x4              16   48                  0.353ms    72.9      1.297ms     3.67x +
27B TP1          1024x8              16   48                  0.298ms    86.3      1.294ms     4.33x +
27B TP1          8192x8              16   48                  2.106ms    97.9     10.699ms     5.08x +
27B TP1          8192x16             16   48                  3.888ms   106.1     21.659ms     5.57x +
27B TP1          8192x32             16   48                  7.592ms   108.6     43.738ms     5.76x +

2B/0.8B TP1      1x65536             16   16                  1.572ms    43.7      3.748ms     2.38x +
2B/0.8B TP1      1x32768             16   16                  0.809ms    42.5      1.824ms     2.25x +
2B/0.8B TP1      1x16384             16   16                  0.429ms    40.0      0.865ms     2.02x +
2B/0.8B TP1      1x8192              16   16                  0.237ms    36.3      0.383ms     1.62x +
2B/0.8B TP1      1x4096              16   16                  0.138ms    31.2      0.157ms     1.14x +
2B/0.8B TP1      1x2048              16   16                  0.105ms    20.4      0.074ms     0.70x -
2B/0.8B TP1      6144+2048           16   16                  0.226ms    38.0      0.364ms     1.61x +
2B/0.8B TP1      4096+4096           16   16                  0.213ms    40.3      0.343ms     1.61x +
2B/0.8B TP1      2048+6144           16   16                  0.225ms    38.2      0.366ms     1.63x +
2B/0.8B TP1      1024+7168           16   16                  0.229ms    37.5      0.374ms     1.63x +
2B/0.8B TP1      2048x4              16   16                  0.151ms    57.0      0.354ms     2.35x +
2B/0.8B TP1      1024x8              16   16                  0.091ms    94.5      0.366ms     4.03x +
2B/0.8B TP1      8192x8              16   16                  0.729ms    94.3      3.527ms     4.84x +
2B/0.8B TP1      8192x16             16   16                  1.612ms    85.2      7.277ms     4.51x +
2B/0.8B TP1      8192x32             16   16                  2.898ms    94.8     14.301ms     4.93x +

Sym h32          1x65536             32   32                  3.151ms    43.6      6.828ms     2.17x +
Sym h32          1x32768             32   32                  1.533ms    44.8      3.329ms     2.17x +
Sym h32          1x16384             32   32                  0.765ms    44.9      1.617ms     2.11x +
Sym h32          1x8192              32   32                  0.398ms    43.1      0.768ms     1.93x +
Sym h32          1x4096              32   32                  0.218ms    39.4      0.333ms     1.53x +
Sym h32          1x2048              32   32                  0.118ms    36.3      0.126ms     1.06x +
Sym h32          6144+2048           32   32                  0.435ms    39.5      0.772ms     1.78x +
Sym h32          4096+4096           32   32                  0.294ms    58.4      0.777ms     2.64x +
Sym h32          2048+6144           32   32                  0.437ms    39.3      0.776ms     1.77x +
Sym h32          1024+7168           32   32                  0.506ms    34.0      0.777ms     1.54x +
Sym h32          2048x4              32   32                  0.179ms    96.1      0.790ms     4.42x +
Sym h32          1024x8              32   32                  0.208ms    82.6      0.812ms     3.90x +
Sym h32          8192x8              32   32                  1.613ms    85.2      7.047ms     4.37x +
Sym h32          8192x16             32   32                  2.911ms    94.4     14.111ms     4.85x +
Sym h32          8192x32             32   32                  5.952ms    92.4     28.698ms     4.82x +
```

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

## Summary by CodeRabbit

* **New Features**
* Added SM120 support for context-parallel delta-rule operations with
architecture-aware kernel routing (SM90 vs SM120).
* Enhanced CP dispatch decisions using device-aware parallelism
thresholds (HBM vs GDDR-like).
* Extended public delta-rule CP DSL exports to include SM120 variants
when available.
* Added a new helper to load B operands into the delta-rule DSL,
including optional dtype conversion.

* **Tests**
* Updated CP delta-rule tests to select SM90/SM120 implementations
dynamically and adjusted GPU skip conditions accordingly.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-07-01
**监控日期**: 2026-06-30
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3786
- **最后更新**: 2026-06-30T22:29:13Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: sumyyyyy, William Lin

## AI分析总结

根据提供的提交记录，总结昨日更新要点如下：

### 1. 主要更新类型
- **功能重构与模块化**：将VSA（Video Spatial Attention？）工具函数提取至独立库 `fastvideo_kernel`。
- **版本发布**：正式发布 `fastvideo-kernel` 的 `0.3.1` 版本。

### 2. 关键变更点及其与项目整体方向的关系
- **变更点**：
  - 将原仓库中与VSA相关的工具函数抽离并整合到 `fastvideo_kernel` 包中（PR #1408）。
  - 通过版本号 `0.3.1` 发布该独立库（PR #1520）。
- **与项目方向的关系**：
  - FastVideo 定位为高效视频处理框架，目标包括推理、训练等。将核心kernel代码剥离为独立包，符合**模块化、可复用**的发展方向，便于不同场景（如推理、训练）按需集成。
  - 版本发布意味着该组件已具备独立使用和版本管理的能力，有利于社区贡献者单独关注底层算法优化。

### 3. 对项目的影响和潜在意义
- **正向影响**：
  - 减少核心仓库的代码冗余，提升可维护性。
  - 为后续其他子模块（如推理加速、训练内核）的独立发布提供参考模式。
- **潜在意义**：
  - VSA工具函数可能是视频注意力机制（如空间注意力、时间注意力）的关键实现，独立成库可促进相关算法在不同视频任务（如生成、理解）中的复用。
  - 版本号从0.3.0升至0.3.1，暗示可能存在细微优化或修复，但提交记录未显式注明。

### 4. 值得关注的技术点
- **VSA工具函数**：需进一步查看 `fastvideo_kernel` 源代码，了解其具体功能（例如：是否支持高效注意力计算、是否适配视频帧序列等）。
- **包依赖性**：主项目 `FastVideo` 后续可能将 `fastvideo_kernel` 作为依赖引入，需关注版本兼容性。
- **发布流程**：本次发布由 `SolitaryThinker` 协作完成，说明该项目已有多人协作的版本管理规范。

### 5. 基于README背景，这些提交如何影响项目发展
- README强调项目有完善的文档、快速开始指南及周开发会议，表明社区活跃且注重可用性。
- 剥离kernel库后，用户可在自定义推理管道中直接引用 `fastvideo_kernel` 的优化实现，降低使用门槛。
- 版本化发布（尤其是语义化版本）有利于项目**长期演进**，也为后续发布更多独立子包（如 `fastvideo-distributed`, `fastvideo-train`）奠定基础，提升整体生态的灵活性。

## 详细提交记录

### [31e26ab](https://github.com/hao-ai-lab/FastVideo/commit/31e26abec43bec9b25a68dd1f2618db4972fe293)

- **作者**: William Lin
- **时间**: 2026-06-30T19:25:27Z
- **提交信息**: [chore] release fastvideo-kernel 0.3.1 (#1520)

### [9e83ba6](https://github.com/hao-ai-lab/FastVideo/commit/9e83ba630c2ad337090365c81e18412e054f1110)

- **作者**: sumyyyyy
- **时间**: 2026-06-30T19:19:25Z
- **提交信息**: [kernel] Extract VSA utility functions into fastvideo_kernel (#1408)

Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-07-01
**监控日期**: 2026-06-30
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 33958
- **最后更新**: 2026-06-30T18:00:55Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: dxqb

## AI分析总结

### 1. 主要更新类型
- **Bug修复**：针对Kohya LoRA格式向Diffusers格式的转换逻辑，修复了Z-Image和Qwen两类模型的兼容性问题。

### 2. 关键变更点及其与项目整体方向的关系
- **Z-Image模块名称过度拆分修复**：  
  原本的转换逻辑将模块名中的下划线统一替换为点号（例如 `all_final_layer` → `all.final.layer`），导致无法匹配Diffusers内部命名。本次通过**扩展点号→下划线的后归一化**，将这些被错误拆分的名字重新合并，使Kohya训练的Z-Image LoRA能被正确加载。  
  *与项目方向的关系*：diffusers作为社区通用扩散模型库，必须兼容主流第三方训练框架（如Kohya）的输出，此修复填补了特定模型（Z-Image）的转换空白。

- **Qwen顶层模块转换修复**：  
  原代码硬编码 `transformer_blocks` 前缀，导致 `img_in`、`txt_in`、`proj_out` 等非块级模块被错误归并到 `transformer_blocks.` 之下，引发 `state_dict` 空值检查错误。本次通过**显式映射六个顶层模块名称**，保留 `.lora_down/.lora_up/.alpha` 后缀，确保转换后的权重键名正确。  
  *与项目方向的关系*：Qwen模型架构可能包含不同于标准Transformer Block的顶层结构，此修复扩展了转换逻辑的通用性，支持更多模型变体。

### 3. 对项目的影响和潜在意义
- **提升与Kohya生态的互操作性**：使得大量使用Kohya训练Z-Image/Qwen LoRA的用户能够直接在diffusers中加载和使用，减少格式转换障碍。
- **降低用户门槛**：不再需要手动调整转换脚本或等待社区补丁，一键式加载成为可能。
- **为后续扩展奠定基础**：新增的映射模式（如顶层模块显式映射）可被复用至其他含类似命名模式的模型（如Flux、SD3等），减少重复修复成本。

### 4. 值得关注的技术点
- **命名约定冲突处理**：Kohya使用点号扁平化（`module.name` → `module_name`），但模型内部模块名可能天然包含下划线。本次采用**“拆分-后恢复”策略**，既保留通用转换规则，又通过白名单机制保护特定名称。
- **模块层级判断**：通过遍历映射表而非靠前缀假设，避免硬编码导致的顶层模块丢失问题，体现了**防御性编码**思想。
- **AI辅助协作**：提交中注明Co-Authored-By Claude，表明AI被用于分析具体bug或生成修复逻辑，反映现代开源协作中AI工具的辅助角色。

### 5. 结合README背景的项目发展影响
- **强化“格式转换枢纽”定位**

## 详细提交记录

### [6d71b76](https://github.com/huggingface/diffusers/commit/6d71b76aceff935192e58fee38c5cc5d8d227cf0)

- **作者**: dxqb
- **时间**: 2026-06-30T17:02:49Z
- **提交信息**: Complete Kohya LoRA conversion for Qwen and Z-Image (#14080)

* Fix Kohya LoRA conversion for Z-Image modules whose names contain underscores

_convert_non_diffusers_z_image_lora_to_diffusers reverses Kohya's `.`->`_`
flattening with a blanket `_`->`.` split, guarded only by a small
protected-n-gram list (attention to_q/k/v/out, feed_forward) plus post-hoc
fixes for context_refiner/noise_refiner. Z-Image's other modules whose names
contain underscores were over-split: all_final_layer, all_x_embedder,
adaLN_modulation, cap_embedder and t_embedder came out as all.final.layer,
adaLN.modulation, ... and failed to load with "unexpected keys".

Extend the existing dot->underscore post-normalization to re-merge these
names, so Kohya (lora_unet_) Z-Image LoRAs load.

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

* Fix Kohya LoRA conversion for Qwen top-level (non-block) modules

_convert_non_diffusers_qwen_lora_to_diffusers's convert_key hardcodes the
transformer_blocks prefix and assumes every lora_unet_ key lives under a block:
it strips a transformer_blocks_ prefix and re-prepends transformer_blocks.,
which collapses the top-level modules (img_in, txt_in, proj_out, norm_out.linear,
time_text_embed.timestep_embedder.linear_1/2) onto each other. They end up as
transformer_blocks..weight / ...a.down.weight and trip the 'state_dict should be
empty' guard.

Resolve these six modules via an explicit flattened->dotted map before the block
logic runs, preserving the .lora_down/.lora_up/.alpha suffix, so Kohya (lora_unet_)
Qwen LoRAs load.

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

---------

Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>
Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-07-01
**监控日期**: 2026-06-30
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 420
- **最后更新**: 2026-06-30T02:34:11Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-07-01
**监控日期**: 2026-06-30
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12647
- **最后更新**: 2026-06-30T16:45:11Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Jinyan Ye

## AI分析总结

根据提交记录和仓库背景，总结昨日更新要点如下：

### 1. 主要更新类型
- **功能新增（实验性）**：添加了 DMD2 训练功能。

### 2. 关键变更点及与项目方向的关系
- 支持针对 `flux2-klein-base-4B` 模型的 DMD2 训练，并修复了相关示例代码。
- **与项目方向的关系**：DiffSynth-Studio 专注于扩散合成（Diffusion Synthesis）相关技术，DMD2 训练是一种新的训练范式（可能涉及模型蒸馏或高效训练），直接扩展了项目在模型训练能力上的深度，与项目“探索先进合成方法”的目标一致。

### 3. 对项目的影响和潜在意义
- **影响**：为使用 `flux2` 系列大型模型（4B 参数）的用户提供了一个实验性的高效训练方案，可能降低训练资源需求或提升生成质量。
- **潜在意义**：若 DMD2 技术成熟，可推动项目在**模型轻量化**或**控制能力**上取得突破，吸引更多研究人员参与；标记为“实验性”表明团队正在积极迭代核心技术。

### 4. 值得关注的技术点
- **DMD2**：具体含义未公开，推测为 Diffusion Model Distillation 或 Denoising Mode Distillation 的变体，结合 `flux2-klein-base-4B` 这一大型基础模型，可能涉及**知识蒸馏**或**潜在空间优化**。
- **模型适配**：提交针对 `flux2` 系列进行特化适配，表明项目在**多模型兼容性**上持续投入。

### 5. 对项目发展的影响（结合README背景）
- README 强调项目有活跃的 Trendshift 排名和 PyPI 包，说明其社区关注度高。新增 DMD2 训练功能：
  - **提升技术壁垒**：使项目区别于普通扩散代码库，吸引需要**定制化训练**的用户。
  - **推动垂直应用**：未来可能将 DMD2 与视频合成、图像编辑等下游任务结合，加速“扩散合成”场景的落地。
  - **风险提示**：实验性功能需充分测试，否则可能影响生产环境稳定性，但体现了项目在**前沿技术探索**上的积极态度。

## 详细提交记录

### [3f5fa52](https://github.com/modelscope/DiffSynth-Studio/commit/3f5fa5286fa6d35b3b12a739b4dde5500b191e5d)

- **作者**: Jinyan Ye
- **时间**: 2026-06-30T12:26:07Z
- **提交信息**: Experimental Feature: DMD2 training (#1503)

* add: dmd2 for flux2-klein-base-4B

* fix: examples

* fix: examples

* fix: examples

* fix: examples

* fix: dmd2 for flux2-klein-base-4B

* fix: dmd2 trainer for flux2-klein-base-4B

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-07-01
**监控日期**: 2026-06-30
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 29833
- **最后更新**: 2026-06-30T23:07:13Z

## 提交统计

- **昨日提交总数**: 18
- **提交者数量**: 16
- **主要提交者**: cctry, sglang-bot, DarkSharpness

## AI分析总结

### 昨日更新要点总结（基于 sgl-project/sglang 仓库）

---

#### 1. 主要更新类型
- **功能新增**：4项（Triton MoE 融合门控、扩散模型 Krea-2 支持、预算草稿 KV

## 详细提交记录

### [53c61bd](https://github.com/sgl-project/sglang/commit/53c61bd5e62ca90a8e488821917abf9303c8b94d)

- **作者**: Feng Yao
- **时间**: 2026-06-30T23:07:06Z
- **提交信息**: [bug2] skip swa recovery on locked full kv (#29352)

Co-authored-by: Zhangheng <hzh0425@apache.org>
Co-authored-by: Hanming Lu <69857889+hanming-lu@users.noreply.github.com>

### [99b8f36](https://github.com/sgl-project/sglang/commit/99b8f36cb1f1616e4a152af334a86c0cb365ca55)

- **作者**: Yuzhen Zhou
- **时间**: 2026-06-30T21:53:29Z
- **提交信息**: Skip custom all-reduce v2 CUDA graph capture with torch memory saver. (#27948)

### [bb98629](https://github.com/sgl-project/sglang/commit/bb98629157e2d10eb9408611849a7b909e242c22)

- **作者**: andyluo7
- **时间**: 2026-06-30T21:08:51Z
- **提交信息**: docs(cookbook): add AMD MI300X/MI325X/MI355X support for GLM-5.2 (#28471)

Co-authored-by: Claude Opus 4 (1M context) <noreply@anthropic.com>
Co-authored-by: zijiexia <37504505+zijiexia@users.noreply.github.com>
Co-authored-by: Zijie Xia <zijie.xia@radixark.ai>

### [081a01c](https://github.com/sgl-project/sglang/commit/081a01c37d92ba41b9e58b83f1eb2cfc70cd3c87)

- **作者**: sglang-bot
- **时间**: 2026-06-30T20:48:10Z
- **提交信息**: docs: sync LMSYS SGLang blog cards (#29307)

Co-authored-by: sglang-bot <sglang-bot@users.noreply.github.com>

### [e721259](https://github.com/sgl-project/sglang/commit/e721259079493d61463398d8c7b7d2ecbaf6171b)

- **作者**: TzZtzt
- **时间**: 2026-06-30T18:54:36Z
- **提交信息**: typo-fix: correct mooncake package name to "mooncake-transfer-engine" (#25153)

### [97fc4df](https://github.com/sgl-project/sglang/commit/97fc4dfd73c3f907b25885887196676b0dc071e3)

- **作者**: a60124901
- **时间**: 2026-06-30T17:27:38Z
- **提交信息**: [Doc]Checking and modifying Markdown formatting issues and link validity (#28586)

Signed-off-by: a60124901 <anyuxin4@h-partners.com>
Co-authored-by: sglang-npu-bot <sglangnpu@163.com>
Co-authored-by: ronnie_zheng <zl19940307@163.com>

### [1c2523b](https://github.com/sgl-project/sglang/commit/1c2523b719d1e8a55c43bf1a9526b0c52b05e118)

- **作者**: Feng Yao
- **时间**: 2026-06-30T16:51:18Z
- **提交信息**: [bug1] keep full kv when swa skips leaf data (#29351)

Co-authored-by: ispobock <ispobaoke@gmail.com>

### [c70cc96](https://github.com/sgl-project/sglang/commit/c70cc969053f104a24e5101b554ceae7d89474b7)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-06-30T15:58:25Z
- **提交信息**: [AMD] Stop rocm720 pr auto-runs (#29768)

Co-authored-by: bingxche <bingxche@users.noreply.github.com>

### [f2756f5](https://github.com/sgl-project/sglang/commit/f2756f53f325dc09b431239e218bf19f52bb91a8)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-06-30T15:40:00Z
- **提交信息**: [AMD] Update AMD local registry address (#29765)

Co-authored-by: bingxche <bingxche@amd.com>

### [cf36dca](https://github.com/sgl-project/sglang/commit/cf36dca6d4ca371c44e426fe168aa153796c75a1)

- **作者**: DarkSharpness
- **时间**: 2026-06-30T15:26:18Z
- **提交信息**: [JIT Kernel] Triton moe fused gate (#25835)

Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>
Co-authored-by: ziyi.xu <ziyi.xu@radixark.ai>
Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

### [a531d81](https://github.com/sgl-project/sglang/commit/a531d81c194ae7b2da93d2e4fe567026e69a0d23)

- **作者**: Yihao Wang
- **时间**: 2026-06-30T15:22:05Z
- **提交信息**: [diffusion][cache-dit] support Krea-2 + run-driven `has_separate_cfg` (#29688)

Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [c6a7c98](https://github.com/sgl-project/sglang/commit/c6a7c98ae429760ed3b2df8d3a11600c3855d74a)

- **作者**: Estrella-xx
- **时间**: 2026-06-30T11:22:19Z
- **提交信息**: [NPU]GLM-4.7-Flash optimize with fused kernels (#29509)

### [2f730e2](https://github.com/sgl-project/sglang/commit/2f730e299f3b574e3bee2c6ef9669fa2a5b26dbc)

- **作者**: nvjullin
- **时间**: 2026-06-30T08:34:44Z
- **提交信息**: Disable dsr1 prefill cudagraphs by default (#28053)

### [a5e6dd3](https://github.com/sgl-project/sglang/commit/a5e6dd37677f1672e355a4b1e56b3969879bd25e)

- **作者**: Stanley Winata
- **时间**: 2026-06-30T08:24:22Z
- **提交信息**: [AMD] Implement QuarkW4A8MXFp4MoE to support amd/gpt-oss-120b-w-mxfp4-a-fp8 (#27204)

Signed-off-by: Stanley Winata <stanley.winata@amd.com>

### [89620b9](https://github.com/sgl-project/sglang/commit/89620b9169e67525000e804fc443444ecea0944b)

- **作者**: qyb233
- **时间**: 2026-06-30T08:22:13Z
- **提交信息**: [NPU] Support DeepSeek V4 Flash MTP on Ascend (#28980)

Co-authored-by: Kurkur <mccllm@qq.com>
Co-authored-by: gjsheu <gjsheu@163.com>
Co-authored-by: root <root@localhost.localdomain>
Co-authored-by: khalil2ji3mp6 <khalilzhk@gmail.com>

### [4b4b4af](https://github.com/sgl-project/sglang/commit/4b4b4af583390637a807d48f6df81c474a25c5c4)

- **作者**: cctry
- **时间**: 2026-06-30T07:58:33Z
- **提交信息**: Budget EAGLE/STANDALONE draft KV pool in SWA pool configurators (#29622)

Co-authored-by: cctry <cctry@fb.com>

### [ff51acd](https://github.com/sgl-project/sglang/commit/ff51acd67b228bae35d73ce8d36a8f44c8cf9697)

- **作者**: silencejade
- **时间**: 2026-06-30T07:55:50Z
- **提交信息**: [NPU] Qwen3-VL-8B use split_qkv_rmsnorm_rope for extend (#29627)

### [bae78a4](https://github.com/sgl-project/sglang/commit/bae78a44da62ad98ee501adbc2823af37fe3f94b)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-06-30T07:54:01Z
- **提交信息**: [Deps] Bump transformers to 5.12.1 (#29393)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-07-01
**监控日期**: 2026-06-30
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1213
- **最后更新**: 2026-06-30T21:32:33Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-07-01
**监控日期**: 2026-06-30
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 84925
- **最后更新**: 2026-06-30T23:23:27Z

## 提交统计

- **昨日提交总数**: 52
- **提交者数量**: 41
- **主要提交者**: Matt, liuzhenwei, Nicolò Lucchesi

## AI分析总结

以下是针对 vllm-project/vllm 昨日（基于提交时间）主要更新的分析总结，结合项目愿景（

## 详细提交记录

### [b1190d0](https://github.com/vllm-project/vllm/commit/b1190d03cc13531ede563c4466215f9840baa933)

- **作者**: yzong-rh
- **时间**: 2026-06-30T23:23:20Z
- **提交信息**: [Refactor][GPT-OSS] Harmony Responses API Refactor to use HarmonyParser (#47185)

Signed-off-by: Yifan Zong <yzong@redhat.com>

### [92c7fac](https://github.com/vllm-project/vllm/commit/92c7fac640fa7f230f63e6e2e571965570010bc6)

- **作者**: Albert Cheng
- **时间**: 2026-06-30T22:56:56Z
- **提交信息**: [Perf] Restore zero-init of swizzled NVFP4 scale buffer to recover Blackwell decode throughput (#45739)

Signed-off-by: Albert Cheng <albertching0112@gmail.com>
Co-authored-by: Vadim Gimpelson <156319763+vadiklyutiy@users.noreply.github.com>

### [ac521f6](https://github.com/vllm-project/vllm/commit/ac521f623706b74ac12a01e6ed8f7297a39257fe)

- **作者**: Ting SUN
- **时间**: 2026-06-30T22:41:33Z
- **提交信息**: [Bugfix][Structured Outputs] Reject degenerate `structured_outputs` that crash EngineCore (#45346)

Signed-off-by: Ting Sun <suntcrick@gmail.com>

### [2824282](https://github.com/vllm-project/vllm/commit/28242824e00856cf4f3d3f45c959ab1e6501a91b)

- **作者**: tarjan1
- **时间**: 2026-06-30T21:33:10Z
- **提交信息**: [Bugfix][Frontend] Normalize constrained Harmony recipients (#45657)

Signed-off-by: shaojunjie <626650687@qq.com>
Co-authored-by: Ben Browning <bbrownin@redhat.com>

### [6829473](https://github.com/vllm-project/vllm/commit/68294739d1b5caaa1d537adcd79762a1ee9283fc)

- **作者**: VectorPeak
- **时间**: 2026-06-30T20:43:42Z
- **提交信息**: [Bugfix] Align OpenCV video metadata timeline (#47099)

Signed-off-by: VectorPeak <73048950+VectorPeak@users.noreply.github.com>

### [c8d2f3c](https://github.com/vllm-project/vllm/commit/c8d2f3cb1485fcca725653fb92a445b6cc10ade7)

- **作者**: Joe Rowell
- **时间**: 2026-06-30T19:50:46Z
- **提交信息**: [Bugfix] compressed-tensors: allow int8 grouped WNA16 MoE on Marlin (#47154)

Signed-off-by: Joe Rowell <joerowell4@gmail.com>
Co-authored-by: Robert Shaw <114415538+robertgshaw2-redhat@users.noreply.github.com>

### [345b28f](https://github.com/vllm-project/vllm/commit/345b28ff2f75a94e3ab91eb5e50f104dd7b933c2)

- **作者**: Matt
- **时间**: 2026-06-30T19:30:53Z
- **提交信息**: [Hardware][AMD][CI] Bump timeouts of various test groups on AMD CI (#47195)

Signed-off-by: Matthew Wong <Matthew.Wong2@amd.com>

### [248d1fb](https://github.com/vllm-project/vllm/commit/248d1fbb711b210784ab880593403d665a4731bd)

- **作者**: Roberto L. Castro
- **时间**: 2026-06-30T19:17:34Z
- **提交信息**: [Feat][1/N] CuTeDSL warmup infrastructure, FA4 MLA (#46182)

Signed-off-by: LopezCastroRoberto <rocastro@redhat.com>
Signed-off-by: Roberto L. Castro <38211239+LopezCastroRoberto@users.noreply.github.com>
Co-authored-by: Lucas Wilkinson <LucasWilkinson@users.noreply.github.com>

### [11b26c5](https://github.com/vllm-project/vllm/commit/11b26c5528b57ccbebd3e7da49892a8f2257cb83)

- **作者**: Joe Rowell
- **时间**: 2026-06-30T19:14:09Z
- **提交信息**: [Bugfix][Tool Parser] PoolsideV1: fix logprobs AttributeError on Responses API (#47138)

Signed-off-by: Joe Rowell <joerowell4@gmail.com>
Co-authored-by: Robert Shaw <114415538+robertgshaw2-redhat@users.noreply.github.com>

### [20434c4](https://github.com/vllm-project/vllm/commit/20434c472e07d6e4116b5dd02058697331f3d1af)

- **作者**: Roberto L. Castro
- **时间**: 2026-06-30T18:50:15Z
- **提交信息**: [Feat] Improve Triton JIT diagnostics (#46621)

Signed-off-by: LopezCastroRoberto <rocastro@redhat.com>

### [c8f9c15](https://github.com/vllm-project/vllm/commit/c8f9c156a5f823209f7373b2e842f82335cbbd08)

- **作者**: Andreas Karatzas
- **时间**: 2026-06-30T18:43:54Z
- **提交信息**: [ROCm][V1][MLA] Clone prefill backend state per metadata builder (#46993)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [953bba4](https://github.com/vllm-project/vllm/commit/953bba488dee45b1136379a823ef8a93d6d4e19e)

- **作者**: Woosuk Kwon
- **时间**: 2026-06-30T18:38:18Z
- **提交信息**: [PERF] Extend NCCL symmetric memory to AllGather and ReduceScatter (#46703)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: snordmann <snordmann@nvidia.com>

### [3a9784b](https://github.com/vllm-project/vllm/commit/3a9784b82ca59133c47c16a4ce77858eae9a9a02)

- **作者**: Wentao Ye
- **时间**: 2026-06-30T18:34:05Z
- **提交信息**: [Feature] DP supervisor using rust frontend (#47076)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [3cecee4](https://github.com/vllm-project/vllm/commit/3cecee40f34cec995b4705b7ec928e8ce3327f97)

- **作者**: Giancarlo Delfin
- **时间**: 2026-06-30T18:25:32Z
- **提交信息**: [Model Runner V2][Spec Decode] Fix stale values in idx_mapping from CG num reqs padding (#47066)

### [a773253](https://github.com/vllm-project/vllm/commit/a7732537f4304a36c8067fde0937999fff939b63)

- **作者**: Nikita Shapovalov
- **时间**: 2026-06-30T18:07:59Z
- **提交信息**: [Bugfix] Restore part of bugfix #42650 after accidental deletion in #43241 (#47039)

Signed-off-by: zhanda <zhandazhu@gmail.com>
Signed-off-by: Nikita Shapovalov <nikita@poolside.ai>
Co-authored-by: Zhanda Zhu <49645678+zhandaz@users.noreply.github.com>
Co-authored-by: Shang Wang <shangw@nvidia.com>
Co-authored-by: Michael Goin <mgoin64@gmail.com>

### [727971f](https://github.com/vllm-project/vllm/commit/727971f1c1056f7b8a3ea89713526756e6f7c8cf)

- **作者**: Rishi Puri
- **时间**: 2026-06-30T18:02:22Z
- **提交信息**: Add Medusa speculative decoding e2e test (#41396)

Signed-off-by: Anshika Ojha <anshikao@nvidia.com>
Signed-off-by: Rishi Puri <riship@nvidia.com>
Signed-off-by: Rishi Puri <puririshi98@berkeley.edu>
Signed-off-by: Stefano Castagnetta <scastagnetta@nvidia.com>
Co-authored-by: Anshika Ojha <215760622+ojhaanshika@users.noreply.github.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>
Co-authored-by: Stefano Castagnetta <scastagnetta@nvidia.com>

### [25671cb](https://github.com/vllm-project/vllm/commit/25671cb520e01c7b1c0eabeb65f38a6cf9052b4c)

- **作者**: Ben Browning
- **时间**: 2026-06-30T17:46:53Z
- **提交信息**: [Parser][Bugfix] Ensure tool call or other special tokens don't leak in non-streaming tool parsing (#46875)

Signed-off-by: Ben Browning <bbrownin@redhat.com>
Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>

### [27d5f78](https://github.com/vllm-project/vllm/commit/27d5f78b638d385904b7409ca398272fc08eead7)

- **作者**: Lucas Wilkinson
- **时间**: 2026-06-30T17:34:25Z
- **提交信息**: [CI] Move distributed small LM eval to B200 (#47048)

Signed-off-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [7a341fa](https://github.com/vllm-project/vllm/commit/7a341fa109e569c8d265545adfca756f42451244)

- **作者**: liuzhenwei
- **时间**: 2026-06-30T17:06:12Z
- **提交信息**: [XPU] Support ZE_AFFINITY_MASK passthrough in xpu_disagg_acc_test (#47105)

Signed-off-by: zhenwei-intel <zhenwei.liu@intel.com>

### [f41e8dd](https://github.com/vllm-project/vllm/commit/f41e8ddc97ad055647dbcd5a39daca3c13544ca5)

- **作者**: Charlie Fu
- **时间**: 2026-06-30T16:32:58Z
- **提交信息**: [ROCm][CI] Move PyTorch Compilation Unit Tests to MI300(gfx942) (#47065)

Signed-off-by: charlifu <charlifu@amd.com>

### [245888f](https://github.com/vllm-project/vllm/commit/245888ff77d4754a76bc899727fcf4290733dfd4)

- **作者**: fangyuchu
- **时间**: 2026-06-30T16:00:25Z
- **提交信息**: [Feature] Detect all2all peer fault with fault tolerance backend and prevent corrupted output (#43637)

Signed-off-by: fangyuchu <fangyuchu@qq.com>
Co-authored-by: Tyler Michael Smith <tlrmchlsmth@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [e840f0d](https://github.com/vllm-project/vllm/commit/e840f0d3f5d26803e907d64a84be521d9568900a)

- **作者**: Kunshang Ji
- **时间**: 2026-06-30T15:39:59Z
- **提交信息**: [Platform] Replace `torch.cuda.Event` with `torch.Event` (#47140)

Signed-off-by: Kunshang Ji <kunshang.ji@intel.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [fcaa84e](https://github.com/vllm-project/vllm/commit/fcaa84efa7a980cee3681976ecfe36133c48251a)

- **作者**: Nick Hill
- **时间**: 2026-06-30T15:31:27Z
- **提交信息**: [BugFix] Gate MRV2 mixed sparse-MLA warmup on `max_num_seqs` > 1 (#47050)

Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: ziminghuang <ziminghuang@inferact.ai>

### [9e84ec8](https://github.com/vllm-project/vllm/commit/9e84ec86486df4aa5872c43a813e70772ab15f3c)

- **作者**: Wentao Ye
- **时间**: 2026-06-30T15:29:21Z
- **提交信息**: [Refactor] Remove dead minimax allreduce rms kernel (#46842)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [d8f483d](https://github.com/vllm-project/vllm/commit/d8f483dc30a9a74b8fdf1c6dcb11cff503fe40a3)

- **作者**: Igor Margulis
- **时间**: 2026-06-30T15:19:51Z
- **提交信息**: [Spec Decode] Fix hidden-state extraction block size for hybrid verifiers (#46301)

Signed-off-by: Igor Margulis <igor.margulis@intel.com>
Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: mgoin <mgoin64@gmail.com>

### [dc148dc](https://github.com/vllm-project/vllm/commit/dc148dc4d7633f749409f4b724a25669fd455d3d)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-06-30T15:14:13Z
- **提交信息**: [CI][Bugfix] Fix `Hybrid SSM NixlConnector PD prefix cache test (2 GPUs)` (#47157)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [7cf7cbc](https://github.com/vllm-project/vllm/commit/7cf7cbcd9500028f230deff5d194da2f00a2728b)

- **作者**: tc-mb
- **时间**: 2026-06-30T15:12:44Z
- **提交信息**: [Bugfix] MiniCPM-V 4.6: fix grid rows/cols swap in placeholder generation (#45918)

Signed-off-by: tc-mb <tianchi_cai@icloud.com>

### [c231d1f](https://github.com/vllm-project/vllm/commit/c231d1f2906ed3f9a995d84a6c7ba67e6914fb16)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-06-30T15:08:51Z
- **提交信息**: fix(security): bound tokenizer work when explicit truncation_side is set (#47007)

Signed-off-by: jperezde <jperezde@redhat.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [db808b3](https://github.com/vllm-project/vllm/commit/db808b39614384a0349378268a46a1a0feabcec3)

- **作者**: Giancarlo Delfin
- **时间**: 2026-06-30T15:07:24Z
- **提交信息**: [Model Runner V2][Spec Decode] Implement block verification for rejection sampling (#46781)

Signed-off-by: Giancarlo Delfin <gdelfin@inferact.ai>

### [00ebf19](https://github.com/vllm-project/vllm/commit/00ebf19ccaa30d6a4c671baa29ec43ed8c933772)

- **作者**: Arsalan Shakil
- **时间**: 2026-06-30T14:57:14Z
- **提交信息**: [Bugfix][Quant] Raise actionable error instead of bare assert for group-size/TP mismatch (#46230) (#46236)

Signed-off-by: Arsalan Shakil <shakil.arsalan@yahoo.com>

### [ded6676](https://github.com/vllm-project/vllm/commit/ded66764586d547851a7f53c79f5770b1b01c9df)

- **作者**: Seiji Eicher
- **时间**: 2026-06-30T14:37:34Z
- **提交信息**: [Bugfix] Seed RayExecutorV2 TCPStore port by DP rank to avoid collisions (#45960)

Signed-off-by: Seiji Eicher <seiji@anyscale.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [7a327f0](https://github.com/vllm-project/vllm/commit/7a327f0b4f8f6886df77996d0e35ce547c9c2bd1)

- **作者**: Bugen Zhao
- **时间**: 2026-06-30T14:34:43Z
- **提交信息**: [Rust Frontend] Simplify unit tests with shared `TestTokenizer` (#47125)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>

### [1ab9522](https://github.com/vllm-project/vllm/commit/1ab952293587a53dd80c339324596f4168482290)

- **作者**: Harry Mellor
- **时间**: 2026-06-30T14:22:16Z
- **提交信息**: Remove more unnecessary `load_weights` methods (#47058)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [0fc2512](https://github.com/vllm-project/vllm/commit/0fc251209454db524e15487bbca3b0bb5451ae8b)

- **作者**: Ronen Schaffer
- **时间**: 2026-06-30T14:07:12Z
- **提交信息**: [KV Offload] Pass `ScheduleEndContext` to `on_schedule_end` hook (#46450)

Signed-off-by: Ronen Schaffer <ronen.schaffer@ibm.com>
Co-authored-by: Or Ozeri <oro@il.ibm.com>

### [62c7d80](https://github.com/vllm-project/vllm/commit/62c7d8009f33e3cd45b09bbd57dc0a2adca1a949)

- **作者**: Harry Mellor
- **时间**: 2026-06-30T14:02:34Z
- **提交信息**: Forward fix nightly errors from #44589 (#47151)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [ab80b3d](https://github.com/vllm-project/vllm/commit/ab80b3dff4829768347b322c7a5d444e522ef7b3)

- **作者**: Isotr0py
- **时间**: 2026-06-30T13:38:46Z
- **提交信息**: [CI/Build] Bump PyNvVideoCodec version (#47139)

### [91055ef](https://github.com/vllm-project/vllm/commit/91055efd363a42b79a7236a485b5079704e76ec6)

- **作者**: Qiming Zhang
- **时间**: 2026-06-30T13:34:47Z
- **提交信息**: [XPU] C++ implementation for get_memory_info (#47134)

Signed-off-by: mayuyuace <qiming1.zhang@intel.com>

### [3675bcf](https://github.com/vllm-project/vllm/commit/3675bcff67ad5688efef74a0948e879962c4bc38)

- **作者**: Bugen Zhao
- **时间**: 2026-06-30T13:31:58Z
- **提交信息**: [Rust Frontend] Refactor TLS serve path with unified `MaybeTlsListener` (#47101)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>

### [bdbd727](https://github.com/vllm-project/vllm/commit/bdbd7278b6b169c2b188bc1e3f9541468a9e6f4b)

- **作者**: Bugen Zhao
- **时间**: 2026-06-30T13:27:45Z
- **提交信息**: [Rust Frontend] Extend renderer/parser roundtrip tests to support token ids (#47110)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>

### [5dc36a4](https://github.com/vllm-project/vllm/commit/5dc36a4fa507740c94ad30c8dcde3d7620e766d3)

- **作者**: Harry Mellor
- **时间**: 2026-06-30T13:20:33Z
- **提交信息**: [Model] Remove Tarsier, Tarsier2 (#47143)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [aab7af0](https://github.com/vllm-project/vllm/commit/aab7af0bcbf99e2a9462e112dfbcd8a15528ff09)

- **作者**: peizhang56
- **时间**: 2026-06-30T12:31:16Z
- **提交信息**: [Bugfix][ROCm][MLA] Pass q/kv dtypes to get_mla_metadata_v1 in FP8 decode (#46997)

Signed-off-by: pei.zhang <pei.zhang@amd.com>
Co-authored-by: TJian <tunjian.tan@embeddedllm.com>

### [5360477](https://github.com/vllm-project/vllm/commit/536047755e78e25f5bbb67e389d67c6f53fe7f8a)

- **作者**: dependabot[bot]
- **时间**: 2026-06-30T12:16:20Z
- **提交信息**: Bump actions/checkout from 6.0.1 to 7.0.0 (#33057)

Signed-off-by: dependabot[bot] <support@github.com>
Co-authored-by: dependabot[bot] <49699333+dependabot[bot]@users.noreply.github.com>

### [1907d38](https://github.com/vllm-project/vllm/commit/1907d3854ae7dd0e1a5755fafbe93165ae6413a6)

- **作者**: JianweiZheng
- **时间**: 2026-06-30T12:01:03Z
- **提交信息**: [Bugfix] Reject negative values for max_logprobs and long_prefill_token_threshold (#44002)

Signed-off-by: jwzheng96 <jianweizheng@pku.edu.cn>
Signed-off-by: JianweiZheng <32029023+jwzheng96@users.noreply.github.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [ea9ddf5](https://github.com/vllm-project/vllm/commit/ea9ddf59fc9d262da7467699959d8c84600c073c)

- **作者**: Chaojun Zhang
- **时间**: 2026-06-30T11:20:33Z
- **提交信息**: [XPU][CI] Enable shared loader test (#45977)

Signed-off-by: Chaojun Zhang <chaojun.zhang@intel.com>

### [8cf7c4d](https://github.com/vllm-project/vllm/commit/8cf7c4d8ad602d73ff2ec72a101420d47163c136)

- **作者**: Cheng Jiang
- **时间**: 2026-06-30T10:17:43Z
- **提交信息**: [Attention Backend] add HPC-Ops Attention backend (#46020)

Signed-off-by: chengvjiang <chengvjiang@tencent.com>
Co-authored-by: chengvjiang <chengvjiang@tencent.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [8e9d70f](https://github.com/vllm-project/vllm/commit/8e9d70fdd5842a3bc0ef2a45e5413be1f4ffd2d6)

- **作者**: Agata Dobrzyniewicz
- **时间**: 2026-06-30T09:57:27Z
- **提交信息**: [Kernel][XPU] Adjust kernel unit tests for XPU (#45140)

Signed-off-by: Dobrzyniewicz, Agata <agata.dobrzyniewicz@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [364ee36](https://github.com/vllm-project/vllm/commit/364ee36af1ed72a7ae3700b14db8099bc1b94e6c)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-06-30T09:39:22Z
- **提交信息**: fix(security): prevent image decompression bomb OOM denial of service (#47010)

Signed-off-by: jperezde <jperezde@redhat.com>

### [06fae69](https://github.com/vllm-project/vllm/commit/06fae6911406524ecd89fcce5c6095f920f6b730)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-06-30T09:02:07Z
- **提交信息**: [Misc] Mistral label alert (#47132)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [14f8660](https://github.com/vllm-project/vllm/commit/14f8660a18029f0e20c1224327127025f8a30465)

- **作者**: Li, Jiang
- **时间**: 2026-06-30T07:59:13Z
- **提交信息**: [CI/Build] Add CPU test dependency pre-commit hooks (#47032)

Signed-off-by: jiang1.li <jiang1.li@intel.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [aed541d](https://github.com/vllm-project/vllm/commit/aed541def40c127c8d3c1ec72d7f8e99bd58851a)

- **作者**: Aman Paswan
- **时间**: 2026-06-30T07:55:14Z
- **提交信息**: [Bugfix][Responses] Set completed status for Harmony function calls (#46945)

Signed-off-by: amanambak <aman.paswan@ambak.com>
Co-authored-by: amanambak <aman.paswan@ambak.com>
Co-authored-by: Chauncey <chaunceyjiang@gmail.com>

### [2bc20e8](https://github.com/vllm-project/vllm/commit/2bc20e8abaf7a82ecc068d879ebb925c9317bd40)

- **作者**: Chauncey
- **时间**: 2026-06-30T07:53:17Z
- **提交信息**: [Frontend] Add Streaming Parser Engine and new Kimi k2.5/k2.6/k2.7 Parser (#46610)

Signed-off-by: chaunceyjiang <chaunceyjiang@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [8cc2423](https://github.com/vllm-project/vllm/commit/8cc242335de805cac390580f0dcd9e69b6ed86c0)

- **作者**: Chaojun Zhang
- **时间**: 2026-06-30T07:27:21Z
- **提交信息**: [XPU] Optimize XPU worker shutdown logic to prevent resource leak (#46433)

Signed-off-by: Chaojun Zhang <chaojun.zhang@intel.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-07-01
**监控日期**: 2026-06-30
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 5371
- **最后更新**: 2026-06-30T22:36:40Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 5
- **主要提交者**: boatman, Yi Liu, fywc

## AI分析总结

### 昨日更新要点总结

#### 1. 主要更新类型
- **基础框架更新（Rebase）**：将整个项目基底升级至 vLLM v0.24.0
- **功能新增（Feat）**：SenseNova-U1 模型获得 TeaCache 缓存支持及 CFG-Parallel 并行支持
- **Bug 修复（BugFix）**：Cosmos3 模型修复了声音 latent 的填充问题，确保视频+声音可在序列并行下正常运行
- **性能优化（Perf）**：SenseNova-U1 模型引入融合 RMSNorm+3D Rope 的 kernel
- **量化支持（Quant）**：Qwen-Image 模型新增 W4A16 量化方案（基于 AutoRound）

#### 2. 关键变更点与项目方向
| 变更 | 关联模型/模块 | 与“易用、快速、低成本多模态服务”的关联 |
|------|--------------|----------------------------------------|
| Rebase 到 vLLM v0.24.0 | 全项目 | 紧跟上游最新架构，兼容更多模型与特性 |
| TeaCache / CFG-Parallel | SenseNova-U1 | 提升推理速度（缓存避免重复计算，并行降低延迟） |
| 融合 kernel（RMSNorm+3D Rope） | SenseNova-U1 | 减少算子调优开销，直接加速核心计算 |
| 声音 latent padding 修复 | Cosmos3 | 保证视频+声音多模态同时推理的稳定性 |
| W4A16 量化 | Qwen-Image | 降低显存占用，实现更低的部署成本 |

#### 3. 对项目的影响与潜在意义
- **基础升级**：Rebase 到 v0.24.0 可继承 vLLM 新特性（如更优的调度、新硬件支持），为后续多模态支持提供更稳定的底座。
- **模型覆盖扩展**：SenseNova-U1 和 Cosmos3 获得专门优化，表明项目正系统性地纳入更多多模态模型家族。
- **成本与速度双提升**：融合 kernel、量化、并行策略直接减少计算与显存需求，符合“快且便宜”的目标。
- **多模态稳定性增强**：Cosmos3 的 Bug fix 解决了音视频联合推理的序列并行兼容问题，提升实际使用可靠性。

#### 4. 值得关注的技术点
- **TeaCache**：一种针对多模态 transformer 的缓存机制，可有效减少重复计算，特别适用于长序列或实时交互场景。
- **CFG-Parallel**：Classifier-Free Guidance 的并行实现，在不牺牲生成质量前提下加速条件控制。
- **融合 RMSNorm+3D Rope**：将归一化与旋转位置编码合并为单一 kernel，减少内存访问和 kernel launch 开销。
- **W4A16 量化（AutoRound）**：使用 Intel AutoRound 算法实现 4-bit 权重 16-bit 激活的量化，相比传统 GPTQ 可能更适配 Qwen-Image 这类多模态模型。
- **序列并行下的 latent padding**：在视频生成模型中，声音 latent 长度往往不等于视频帧数，需填充后才能参与序列并行切分，该修复展示了多模态数据对齐的工程细节。

#### 5. 对项目发展的作用（结合 README 背景）
- **推进“易用”**：Rebase 后可直接利用 vLLM 新 API 和配置，降低用户接入门槛；量化支持让用户能在更廉价 GPU 上运行 Qwen-Image。
- **强化“快速”**：缓存、并行、融合 kernel 均针对推理速度优化，SenseNova-U1 和 Cosmos3 的更新代表项目正针对不同多模态模型定制加速方案。
- **落地“低成本”**：量化与并行

## 详细提交记录

### [a560ed1](https://github.com/vllm-project/vllm-omni/commit/a560ed184d9197855f1cccf46cb1cac87b0a7138)

- **作者**: Zhou Taichang
- **时间**: 2026-06-30T11:41:06Z
- **提交信息**: [Rebase] Rebase to vllm v0.24.0 (#4709)

### [9a105bf](https://github.com/vllm-project/vllm-omni/commit/9a105bf90de3d10b7b18f93551ac7978d49cd9db)

- **作者**: fywc
- **时间**: 2026-06-30T09:24:46Z
- **提交信息**: [Feat] Support teacache for SenseNova-U1 (#4164)

Signed-off-by: hanzheli <hanzheli@kuaishou.com>
Signed-off-by: princepride <wangzhipeng628@gmail.com>
Signed-off-by: 汪志鹏 <wangzhipeng628@gmail.com>
Co-authored-by: princepride <wangzhipeng628@gmail.com>

### [bb86145](https://github.com/vllm-project/vllm-omni/commit/bb8614595d44e578ce91d2e49fd44989150661e7)

- **作者**: SYLAR
- **时间**: 2026-06-30T09:23:36Z
- **提交信息**: [BugFix][Cosmos3] Pad sound latents so video+sound runs under sequence parallelism (#4678)

Signed-off-by: lishunyang12 <125541396+lishunyang12@users.noreply.github.com>
Signed-off-by: lishunyang <lishunyang12@163.com>

### [4028680](https://github.com/vllm-project/vllm-omni/commit/4028680b7edb0882f1e50442ad1a58d92fcada5e)

- **作者**: boatman
- **时间**: 2026-06-30T08:32:47Z
- **提交信息**: [Perf]: Fused RMSNorm+3D Rope kernel in Sensenova-U1 (#4669)

Signed-off-by: boatman <109857087+sphinxkkkbc@users.noreply.github.com>

### [9923488](https://github.com/vllm-project/vllm-omni/commit/99234881f5da5c5442fdeae85eaf013be77ac3e2)

- **作者**: Yi Liu
- **时间**: 2026-06-30T08:27:28Z
- **提交信息**: [Quant][AutoRound] Add W4A16 support for Qwen-Image (#3588)

Signed-off-by: yiliu30 <yi4.liu@intel.com>
Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>

### [dd3a4d0](https://github.com/vllm-project/vllm-omni/commit/dd3a4d0a29756429f703244db5cac13c2d082f33)

- **作者**: boatman
- **时间**: 2026-06-30T08:03:26Z
- **提交信息**: [Feat] Support CFG-Parallel For Sensenova-U1-8B-MoT (#4188)

Signed-off-by: sphinxkkkbc <binchengkang8@gmail.com>
Signed-off-by: 汪志鹏 <wangzhipeng628@gmail.com>
Co-authored-by: sphinxkkkbc <binchengkang8@gmail.com>
Co-authored-by: 汪志鹏 <wangzhipeng628@gmail.com>

---
