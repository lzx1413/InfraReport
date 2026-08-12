# GitHub Stars 合并报告 - 2026-08-12

**合并日期**: 2026-08-13
**监控日期**: 2026-08-12
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


**报告日期**: 2026-08-13
**监控日期**: 2026-08-12
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2145
- **最后更新**: 2026-08-12T12:14:44Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-08-13
**监控日期**: 2026-08-12
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2652
- **最后更新**: 2026-08-12T17:12:14Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 3
- **主要提交者**: Shankun Wang, Bilang ZHANG, Xin Qiu

## AI分析总结

## 提交分析总结

### 1. 主要更新类型
本次提交以**功能新增**为主，辅以**Bug修复**和**性能优化**。具体包括：新增注意力机制实现、新增FP8量化支持、修复预热逻辑缺陷、新增Intel XPU分布式推理能力。

### 2. 关键变更点及与项目方向的关系
- **`sol attn` 注意力机制**：为视频生成模型引入新的注意力实现，直接服务于LightX2V“轻量高效视频推理”的核心目标，可能通过优化注意力计算路径降低显存占用或提升吞吐。
- **MiniMax-H3 FP8量化**：对编码器实施FP8量化，契合项目对推理效率的极致追求，通过降低精度换取更快的计算速度和更小的显存 footprint。
- **预热逻辑修复**：修正了MiniMax-H3的warmup prompt处理，属于稳定性改进，确保模型在正式推理前正确初始化状态，避免生成质量波动。
- **Intel XPU分布式支持**：新增8卡XPU的SP+TP组合并行脚本，显著扩展了项目的硬件适配范围，使LightX2V能覆盖Intel加速卡生态，符合“轻量”理念下多硬件平台兼容的长期方向。

### 3. 对项目的影响和潜在意义
- **生态扩展**：XPU支持使项目从依赖单一GPU厂商（如NVIDIA）走向多硬件平台，降低用户使用门槛，吸引Intel生态开发者。
- **效率提升**：FP8量化与新型注意力机制共同推动推理速度与资源效率的优化，强化“Light”定位。
- **稳定性增强**：预热修复减少边缘场景下的生成异常，提升生产环境可靠性，有利于企业级采用。

### 4. 值得关注的技术点
- **SP+TP组合并行**：在XPU上同时使用序列并行和张量并行，体现对长视频序列推理的针对性优化，是分布式推理中的高级策略。
- **FP8量化落地**：在编码器而非全模型上应用FP8，显示精细化量化策略，平衡精度与性能。
- **注意力机制创新**：`sol attn`可能涉及稀疏或线性注意力变体，值得关注其与视频长序列的适配性。

### 5. 对项目发展的影响
结合README中“轻量视频生成推理框架”的定位，本次提交从三个维度推动项目前进：**硬件广度**（XPU）、**性能深度**（FP8+新注意力）、**稳定性精度**（预热修复）。这些变化使LightX2V在保持轻量特性的同时，向“多平台、高效率、高可靠”的成熟推理框架迈进，有望吸引更多社区贡献者并扩大实际部署场景。特别是XPU支持，可能为项目打开Intel数据中心市场，而FP8和注意力优化则持续巩固其在视频生成推理领域的性能优势。整体来看，这批提交体现了项目在工程化落地和生态建设上的积极进展。

## 详细提交记录

### [1bcaeb8](https://github.com/ModelTC/LightX2V/commit/1bcaeb8ecf1f14ee58e85aa1e3ef2e678567bed0)

- **作者**: Shankun Wang
- **时间**: 2026-08-12T13:05:26Z
- **提交信息**: Dev/sol attn (#1372)

### [2484f82](https://github.com/ModelTC/LightX2V/commit/2484f82fee357585e29b7fd346546b6b8ad0d681)

- **作者**: Bilang ZHANG
- **时间**: 2026-08-12T11:46:40Z
- **提交信息**: minimax-h3 encoder fp8 quant (#1373)

### [82a4cb5](https://github.com/ModelTC/LightX2V/commit/82a4cb5ce9e1007ddbbe696f21cb1f10bfeaa23e)

- **作者**: Bilang ZHANG
- **时间**: 2026-08-12T10:32:18Z
- **提交信息**: fix: minimax-h3 warmup prompt (#1371)

### [1de08aa](https://github.com/ModelTC/LightX2V/commit/1de08aab6256fd13a477fc275333526457a5b8a3)

- **作者**: Xin Qiu
- **时间**: 2026-08-12T07:51:58Z
- **提交信息**: feat(intel-xpu): add MiniMax H3 T2AV SP TP support (#1370)

## Summary

Add an Intel XPU distributed inference script and configuration for
MiniMax-H3 T2AV using combined sequence parallelism and tensor
parallelism.

  ## Changes

  - Add an 8-XPU MiniMax-H3 T2AV launch script.

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-08-13
**监控日期**: 2026-08-12
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2196
- **最后更新**: 2026-08-12T11:03:22Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-08-13
**监控日期**: 2026-08-12
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 6154
- **最后更新**: 2026-08-12T21:57:26Z

## 提交统计

- **昨日提交总数**: 8
- **提交者数量**: 7
- **主要提交者**: Lee Nau, FlashInfer Bot, Prasun Gera

## AI分析总结

# FlashInfer 提交分析总结

## 1. 主要更新类型

本次提交包含**3个Bug修复、2个功能新增、1个基础设施更新、1个代码所有权调整和1个CI配置更新**，以Bug修复和功能扩展为主。

## 2. 关键变更点与项目方向的关系

- **MNNVL通信对齐修复**：修复了多节点NVLink通信中工作区16字节对齐导致的两阶段all-reduce内存地址错位问题，直接保障大规模多节点推理的稳定性。
- **SM90 FP8 mega-MoE后端**：为Hopper架构新增专家并行MoE推理后端，支持去重分发、分组合并、融合FC1等优化，扩展了FlashInfer在MoE场景的硬件覆盖。
- **CuTe-DSL Blackwell预填充分页KV缓存**：为SM100预填充内核添加分页KV缓存支持，使模块化内核与现有ragged内核在分页场景下达到性能持平。
- **HCA Gather4兼容性修复**：解决了公开CuTe DSL 4.6 wheel中Gather4操作不可用的问题，确保Blackwell系列GPU上的注意力流水线正常运行。
- **GDN解码FP16转换修复**：修复了FP16操作数被静默重解释为BF16的问题，并完善编译缓存身份标识，避免混合精度序列冲突。

## 3. 对项目的影响和潜在意义

这些变更显著增强了FlashInfer在**多节点通信、MoE推理、Blackwell架构支持**三个维度的生产可用性。MNNVL修复直接解决Kimi K3四节点部署中的崩溃问题；FP8 MoE后端填补了Hopper上大规模专家并行的高性能选项；分页KV缓存使Blackwell预填充内核达到与既有实现同等水平，为后续统一内核架构奠定基础。

## 4. 值得关注的技术点

- **对齐不变量设计**：将Lamport缓冲区对齐从16字节提升至32字节，并统一请求与分配大小，体现了对底层硬件向量化访问约束的精细处理。
- **去重分发优化**：按token+目标rank存储而非按路由存储，在K=6、EP=4配置下减少约43%分发数据量。
- **融合FC1 epilogue**：在DeepGEMM epilogue中融合SwiGLU和量化，消除每rank约1GiB的中间激活缓冲。
- **编译缓存身份扩展**：将操作数dtype纳入缓存键，防止混合精度序列错误复用缓存。
- **warp专用化角色分配**：分页内核中为page_size=8场景专门分配page-table producer warp，展示了对极端配置的细致调优。

## 5. 对项目发展的影响

结合README中“面向推理的高性能GPU内核”定位，这些提交体现了FlashInfer**持续扩展硬件覆盖（Hopper/Blackwell）、完善生产级稳定性（多节点通信、错误传播）、深化MoE和长上下文场景优化**的发展路径。特别是CuTe-DSL模块化内核的持续演进，表明项目正从单一内核库向可组合、可扩展的内核框架转型，同时通过CI镜像更新和CODEOWNERS机制强化了工程基础设施。

## 详细提交记录

### [b8c2192](https://github.com/flashinfer-ai/flashinfer/commit/b8c21928b3202988867787a98526914a3c7f2c7f)

- **作者**: aoshen02
- **时间**: 2026-08-12T21:57:20Z
- **提交信息**: fix(comm): align MNNVL two-shot workspace stages (#4473)

## Summary

- align each MNNVL Lamport buffer to 32 bytes so both 16-byte two-shot
stages remain aligned
- round requested and allocated workspace sizes to the same invariant
- add a large-workspace regression test matching the failing Kimi K3
configuration

## Root cause

The workspace previously aligned each Lamport buffer to 16 bytes.
Two-shot all-reduce then divides that buffer into two stages and
accesses each stage with 16-byte vector operations. A buffer whose size
is 16 modulo 32 therefore places the second stage at an 8-byte-aligned
address, causing `CUDA error: misaligned address`.

For the reproduced `max_num_tokens=16384`, BF16, hidden-size 7168 case,
the old per-buffer size was 536,870,224 bytes (`size % 32 == 16`). The
fixed size is 536,870,208 bytes (`size % 32 == 0`).

## Duplicate check

I searched open FlashInfer PRs for MNNVL stage/workspace alignment,
Lamport two-shot alignment, and MNNVL misaligned-address fixes. No open
PR fixes this issue. The closest historical changes (#2074, #2118, and
#2955) add large-workspace support or change allocation, but retain the
16-byte per-buffer alignment that causes this failure.

## Validation

- `pre-commit run --files flashinfer/comm/trtllm_mnnvl_ar.py
tests/comm/test_trtllm_mnnvl_allreduce.py`
- TP2 GB200 regression: `1 passed, 275 deselected`
- standalone TP4 GB200 large-workspace two-shot all-reduce
- four-node Kimi K3 startup with TP4 / DP4 / EP16 and FlashInfer
all-reduce: all 51 piecewise and 35 full CUDA graphs captured; no
misaligned-address error

OpenAI Codex was used to assist with diagnosis and implementation. The
submitter reviewed the complete diff and validation results.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Improved workspace allocation alignment for more reliable
communication operations.
* Fixed capacity calculations when using larger workspaces, including
workspaces exceeding the tested sequence length.
* Improved support for two-stage operations with large workspace
configurations.
* Increased reliability for operations using varied workspace sizes and
aligned memory buffers.

* **Tests**
* Added regression coverage for large-workspace alignment and two-stage
operation scenarios.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: OpenAI Codex <codex@openai.com>

### [f9b13ef](https://github.com/flashinfer-ai/flashinfer/commit/f9b13ef11472d994ec02210e7a6fe62df3254636)

- **作者**: leonardHONG
- **时间**: 2026-08-12T21:15:39Z
- **提交信息**: feat(moe_ep): add SM90 push FP8 mega-MoE backend for Hopper (#4069)

## 📌 Description

This PR registers `sm90_push_fp8`, a whole-layer expert-parallel MoE
backend for SM90 GPUs connected through single-node NVLink, as a fourth
mega backend behind the existing `register_mega_kernel` plugin surface.

The public entry point is `MoEEpLayer` with `Sm90PushFp8MegaMoeConfig`.
Existing backend behavior is unchanged.

The steady-state forward path covers dispatch, FP8 block-scale expert
FFN, and combine without host-side synchronization, and supports CUDA
Graph capture after initialization. The diagram below shows the path
with all three optional optimizations enabled:

```text
bump_tag
  -> wait_acks
  -> deduplicated dispatch
  -> wait_prefix
  -> compact
  -> FC1 with fused SwiGLU + 1x128 quantization
  -> FC2
  -> grouped combine with owner-side FP32 route reduction
  -> BF16 reduction of received owner rows
  -> ack
```

The backend provides three independently configurable optimizations.
Validation and performance results below use all three unless stated
otherwise.

* **Deduplicated dispatch** stores one payload row per token and
destination rank instead of one per route. In the tested configurations,
with all other options fixed, its output matched the per-route path
under `torch.equal`. For `K=6`, `EP=4`, and random routing, it reduces
dispatch payload bytes by approximately 43%.
* **Grouped combine** performs FP32 route reduction on the owner rank
before pushing one quantized row per token. Its correctness gate
compares the final output against the same reference used by the
per-route path because the quantization point moves.
* **Fused FC1 epilogue** performs SwiGLU and 1x128 activation
quantization inside the FC1 DeepGEMM epilogue, eliminating an
approximately 1 GiB intermediate BF16 activation buffer per rank at the
DSV3 EP8 shape. In the tested configurations, with all other options
fixed, its output matched the unfused path under `torch.equal`. The
unfused path remains the default and maintained reference; the fused
path is opt-in.

## Motivation

The existing Hopper EP stack composes NCCL all-to-all with a local
fused-MoE operator, paying for additional launches, intermediate
buffers, and quantization boundaries.

`sm90_push_fp8` writes quantized payloads directly into peer-mapped
symmetric memory and feeds received rows directly into the expert GEMM
pipeline.

## Contracts introduced by this PR

* `capacity_factor` bounds the GEMM, TMA, and scale buffers, rather than
only the protocol window. The workspace query takes explicit
`expected_m` and `max_rows`, so block-M tactics and cubin keys remain
independent of the memory bound.
* Building the grouped GEMM requires CUDA Toolkit 12.8 or newer. The
generator explicitly rejects older toolkits, and AOT skips this module
below CUDA 12.8, allowing JIT-cache wheels to continue building on CUDA
12.6. Loading and running the generated module also requires a CUDA
runtime version 12.8 or newer.
* Runner initialization elects one NVCC-capable rank per cache and
tactic group to compile cold DeepGEMM cubins. Other ranks load the
resulting cubins from disk.

  * A warm cache works without NVCC.
* A cold cache without NVCC fails during initialization with an error
explaining how to select the fallback.
* `TRTLLM_DG_ENABLED=0` selects the fixed-tactic CUTLASS fallback on the
unfused path.
* Wait kernels use a `%globaltimer` deadline and publish a shared abort
marker before trapping. Peers polling the same protocol window observe
the marker and fail. Because a trap leaves a sticky CUDA error, the
process launcher must terminate the full rank group from the CPU.
* This backend is a stateful variant of the mega-kernel contract:

  * construction binds transformed static weights;
  * `stage_inputs` pre-binds the caller's output tensor.

The architecture and runbook documentation are updated accordingly,
including narrowing the two-entry wording to buffer-oriented kernels.
The `MegaKernelBackend` lifecycle itself is unchanged.

## Correctness

Full kernel acceptance ran on an 8× H800 NVLink node:

| Suite | Scale | Result |
| --------------------------------------------------------- |
--------------: | ---------------------------- |
| Single-GPU suite, 105 configurations | 1 GPU | all passed |
| Distributed suites | EP2 / EP4 / EP8 | all passed |
| Uneven token distributions, zero-token ranks, launch skew | EP2–EP8 |
all passed |
| CUDA Graph capture and replay | tested configurations | all passed |
| 200-round oracle-checked soaks | every tested configuration | all
passed |
| Eight-GPU acceptance matrix at DSV3 shapes | EP8 | all passed, no
skipped cases |

The final PR tree was then revalidated across three Hopper variants:

| Suite | Hardware | Result |
|
------------------------------------------------------------------------------
| -------------- | -------------------: |
| Single-GPU suite, all configurations | 1× H20 | 130 passed, 0 failed |
| `torchrun` EP2 | 2× H100 NVLink | 15 passed, 0 failed |
| `torchrun` EP4 | 4× H20 NVLink | 15 passed, 0 failed |
| `compute-sanitizer` memcheck / racecheck / initcheck, excluding trap
and soaks | 1× H20 | Clean |

Additional hardware-verified properties on the final PR tree:

* In the tested configurations, the fused FC1 output matched the unfused
reference under `torch.equal`.
* Leader deduplication was verified by counting NVCC invocations against
a shared cold cache: exactly one compilation per cubin across four
ranks.
* Warm-cache execution without NVCC was exercised end to end.
* Cold-cache fail-fast behavior was exercised end to end.
* The CUTLASS fallback was exercised end to end.

## Performance

Performance numbers were collected during kernel acceptance on the 8×
H800 node. The final PR tree was functionally revalidated as listed
above.

### Setup

* H800 NVLink
* CUDA 12.9
* PyTorch 2.8
* barrier-aligned timing
* maximum latency across ranks
* autotuned baseline tactics
* identical correctness gates on both sides
* `T` denotes live tokens per rank

The tables report `baseline latency / sm90_push_fp8 latency`; values
greater than `1×` favor this backend. `H`, `E`, and `K` denote hidden
size, expert count, and top-k routes. `random` distributes routes across
experts, while `hot1` concentrates routes on one expert.

### Versus NCCL all-to-all with the same FP8 block-scale compute

| Configuration           | Decode T64 | Throughput T2048 |
| ----------------------- | ---------: | ---------------: |
| EP4 SMALL, H4096 E32 K6 |   1.1–1.5× |         2.0–2.3× |
| EP4 DSV3, H7168 E256 K8 |      1.01× |         2.0–2.3× |

Against a wire-only NCCL transport reference that excludes compaction
and combine reduction, the push transport measured **1.9–3.2×** faster.

This number should be interpreted only as a comparison against that
specific measured reference. It is not a claim against third-party EP
libraries.

### Versus NCCL + `cutlass_fused_moe` FP8

| Configuration | Decode T64 | T2048 random |      T2048 hot1 |
| ------------- | ---------: | -----------: | --------------: |
| EP4 DSV3      |      1.06× |         2.3× |            2.0× |
| EP8 DSV3      |      1.10× |     2.2–2.4× |            1.6× |
| EP4 SMALL     |       3.1× |         2.1× | See limitations |

At EP1 and equal FP8 precision, `sm90_push_fp8` measured **2.3–3.4×**
faster than `cutlass_fused_moe` over `T64–T2048`.

### EP8 scaling

Configuration:

```text
DSV3
capacity = 2048
all three optimizations enabled
```

Results:

```text
T64:    0.758 ms
T2048:  3.238 ms
```

With capacity fixed at 2048, a 32× increase in live token count
increased latency by 4.27×.

Additional observations:

* no scheduling cliff near `T128`;
* all-remote routing adds approximately 5%;
* running 64 live tokens with buffers sized for 2048 adds approximately
0.7%.

## Limitations

* Supports:

  * SM90;
  * single-node, peer-accessible NVLink;
* protocol limit `ep_size <= 32`, with hardware validation in this PR
covering up to EP8;
  * `top_k` in `{1, 2, 4, 6, 8}`;
  * DeepSeek-style FP8 block scaling;
  * SwiGLU.

Unsupported configurations raise an explicit error rather than silently
falling back.

* The unfused FC1 path supports `intermediate_size <= 16384`; larger
configurations require `fuse_fc1_epilogue=True`.

* At DSV3 decode shapes, the advantage over NCCL + `cutlass_fused_moe`
is **1.06–1.10×**, because computation dominates.

* In the artificial SMALL `T2048` case where all `K` routes target one
expert, the backend is 25% slower than the autotuned CUTLASS stack.
Realistic `hot1` routing remains faster at EP4 and EP8.

* The fused FC1 epilogue does not yet have a small-M `swapAB` variant
and can be disabled independently below its break-even point.

* Round tags use `uint32`. Reuse after `2^32` forwards on one pipe is a
documented limit.

* Custom raw-stream execution through `bootstrap.stream` is rejected
explicitly rather than silently ignored.

## How to run

### Single-GPU and host-only suites

```bash
pytest \
  tests/moe_ep/test_sm90_push_fp8_kernel.py \
  tests/moe_ep/test_sm90_push_fp8_backend.py \
  tests/gemm/test_sm90_moe_gemm.py \
  tests/gemm/test_sm90_moe_gemm_contract.py
```

### Multi-rank tests

Requires at least two SM90 GPUs and uses `torch.distributed` only.

```bash
bash tests/moe_ep/run_tests.sh sm90_push
```

### Soak tests

```bash
SM90_PUSH_SOAK_ROUNDS=200 \
  bash tests/moe_ep/run_tests.sh sm90_push
```

### Benchmark

```bash
torchrun \
  --standalone \
  --nproc-per-node=8 \
  benchmarks/bench_sm90_push_megamoe.py \
  --config DSV3 \
  --dedup \
  --grouped-combine \
  --fuse-fc1 \
  --assert-cos-min 0.997
```

## 🔍 Related issues

This PR contributes the Hopper FP8 block-scale milestone under #3692 and
the SM90 sub-issue #3780, and follows the whole-layer integration
direction described in #3704.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
  - [x] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

* [x] Tests added and updated.
* [x] Single-GPU suite passes.
* [x] EP2 distributed suite passes.
* [x] EP4 distributed suite passes.
* [x] CUDA Graph tests pass.
* [x] Soak tests pass on the listed hardware.

## Reviewer notes

Native NVFP4 and MXFP8 execution are out of scope because SM90 does not
provide native block-scaled tensor-core instructions for those formats.
A follow-up PR stacked on this one adds NVFP4 checkpoint support for
SM90 on top of this backend, through online W4A8 decode kernels and a
one-time requantization path that rides this FP8 backend unchanged.
The highest-value review areas are:



Entry points for the highest-risk areas:

* **Symmetric-window ordering and the acknowledgement protocol:**
  `kernel_src/sm90_push_megamoe/src/a2a/sm90_push_a2a_ops.cu`

* **Grouped-combine numerical behavior, where the quantization point
moves:**
The combine kernels in
`kernel_src/sm90_push_megamoe/src/a2a/sm90_push_a2a_ops.cu`, gated by
the reference comparison in `tests/moe_ep/test_sm90_push_fp8_kernel.py`

* **DeepGEMM fused-epilogue and workspace contracts:**
  `src/fp8_gemm/fp8_moe_fc1_fused.cuh``shim/gemm.py`

* **CUDA 12.8 gating and the AOT skip:**
  `shim/gemm.py``flashinfer/aot.py`

* **Collective initialization failure handling:**
  `shim/protocol.py`



<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added SM90 FP8 MegaMoE support with pull- and push-style execution
paths.
* Added configurable FP8 formats, scaling modes, routing, reduction,
CUDA graph, and distributed execution options.
  * Added weight preprocessing and public configuration interfaces.
* Added benchmark tools for correctness, performance, token sweeps, and
peer-to-peer bandwidth.

* **Documentation**
* Expanded architecture guidance, setup instructions, tuning
information, and reproducibility runbooks.

* **Tests**
* Added broad correctness, validation, packaging, lifecycle,
distributed, and CUDA graph coverage.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [2d132e6](https://github.com/flashinfer-ai/flashinfer/commit/2d132e68c9c70e17efa2a0c81c56508ba2cf421d)

- **作者**: myu-guo
- **时间**: 2026-08-12T20:24:37Z
- **提交信息**: Fix HCA Gather4 support for public CuTe DSL (#4368)

## Summary

- construct the two-CTA HCA Gather4 atom through the IR API available in
public `nvidia-cutlass-dsl` 4.6 wheels
- route HCA sliding-window K/V loads through the local compatibility
helper without changing the public HCA API
- raise active Cutlass DSL dependency floors to 4.6.0 and select the
CUDA 13 package extra in CUDA 13 build paths
- add a regression check for the required Gather4 IR capability

## Context

#3943 was merged while the attention pipeline still failed on B300,
GB200, and GB300. The HCA implementation referenced a high-level Gather4
copy operation that is not exported by public Cutlass DSL wheels. Public
4.6 wheels do contain the underlying Gather4 dialect operation and
lowering, so this change isolates the small compatibility adapter next
to the HCA implementation.

## Validation

- B200 HCA suite: 27 passed, 1 skipped
- public Cutlass DSL 4.6 CUDA 12 and CUDA 13 capability probes: passed
- Ruff format/check, shell syntax checks, and `git diff --check`: passed

Implementation and validation were AI-assisted.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **New Features**
- Added support for Gather4 2D TMA operations in compatible CuTe DSL
attention workflows.
- Improved support for CUDA 13 environments by selecting the appropriate
optional packages and CUTLASS DSL configuration automatically.

- **Bug Fixes**
- Updated CUDA version detection to recognize both numeric and formatted
CUDA 13 version values.
- Increased the minimum supported CUTLASS DSL version for improved
compatibility.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [9ffd995](https://github.com/flashinfer-ai/flashinfer/commit/9ffd99510d92b883f154fc9f2e3d5aac93e231ca)

- **作者**: Ka-Hyun Nam
- **时间**: 2026-08-12T18:01:31Z
- **提交信息**: chore: add KDA CODEOWNERS (#4482)

## Summary
- Add a dedicated KDA section to `.github/CODEOWNERS` for linear
attention PIC group.
- Primary owner `@kahyunnam`; secondary reviewer `@jimmyzho`, alternate
general owners`@yzh119 @bkryu`.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Chores**
* Added ownership rules for KDA benchmarks, source code, documentation,
implementations, kernels, tracing, and tests.
  * Assigned designated maintainers to review changes in these areas.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [147739b](https://github.com/flashinfer-ai/flashinfer/commit/147739bc61c7d78a637c10f8ce1d72315e937185)

- **作者**: Prasun Gera
- **时间**: 2026-08-12T17:51:32Z
- **提交信息**: feat: paged KV cache support for the modular CuTe-DSL Blackwell prefill (#4212)

## Summary

Adds paged KV cache support to the modular CuTe-DSL Blackwell (SM100)
prefill kernel and routes
`BatchPrefillWithPagedKVCacheWrapper(backend="cute-dsl")` to it. Paged
execution runs at parity with the modular ragged kernel across page
sizes 16–128, and within a few percent at page size 8 (dedicated
page-table producer warp — see below), with bitwise-identical outputs on
identical logical problems at every page size.

## Architecture

**Kernel structure** (context for where paging plugs in — unchanged by
this PR): the modular prefill is a warp-specialized kernel, one CTA per
(256-row Q tile, KV head group, batch item), 16 warps in fixed roles
with per-role `setmaxnreg` budgets:

| warps | role | regs/thread |
|---|---|---|
| 0–3 / 4–7 | softmax warpgroups (one per 128-row Q half-tile) | 192 |
| 8–11 | correction (online-softmax rescale of O partials) | 96 (88
paged) |
| 12 | MMA (tcgen05 QK^T and PV) | 32 (40 paged) |
| 13 | load (TMA Q/K/V) | 32 (40 paged) |
| 14 | epilogue (TMA store O / LSE) | 32 (40 paged) |
| 15 | empty (page-table producer at page_size 8) | 24 |

Roles communicate through mbarrier pipelines: the load warp fills a
double-buffered Q ring and a shared K/V smem ring (3 stages bf16, 4
stages fp8); the MMA warp consumes them into TMEM S tiles; softmax reads
S and writes P; MMA runs PV; correction rescales output partials; the
epilogue stores O. Wall time in the small-band regime is set by the
per-KV-tile cadence of this pipeline, which is what paging must not
disturb.

**Paged design** (per-page TMA mechanism from the in-repo MLA decode
loader):

- **Layout**: the kernel reads K and V from page pools viewed as
`(num_pages, page_size, H_kv, head_dim)`. Only `head_dim` must be
contiguous; the other three strides are runtime arguments of a single
compiled kernel (one per page size), so the same binary handles an
NHD-contiguous pool, an HND pool passed as a transposed view, or the K/V
slices of a combined `(num_pages, 2, ...)` cache. The TMA descriptor is
built once on the host over the entire pool, and a copy selects which
page to load by passing that page's physical index as one of its TMA
coordinates — the page-table indirection is a coordinate, not per-page
pointer arithmetic.
- **Logical/physical split**: the load warp is the only role that sees
pages. It takes `kv_page_table` + `kv_page_indptr`; mask, softmax,
correction and epilogue operate on logical token cumsums, untouched.
- **Zero-fill contract**: out-of-range page ids become −1 → the TMA
coordinate goes out of bounds, the smem box is zero-filled, and
complete-tx still credits the full byte count. This covers pages past
the sequence tail *and*, on sliding-window kernels, table slots below
the window start: serving frameworks repoint reclaimed slots at a shared
null block that may hold garbage/NaN, and score masking cannot save the
V path (P = +0.0, but 0×NaN = NaN through the PV MMA), so the load
itself must be skipped. The window clamp runs only on an item's first KV
tile (the window lower bound falls inside it by construction); the table
read is min-clamped to the item's slice (on the page-table-ring path
below, the same clamps are applied at produce time instead).
- **Page-table ring (page_size 8)**: at 16 pages per KV tile the
loader's in-loop id loads — one global-latency load per TMA copy, twice
per tile across the K and V loops — dominate its issue cadence. The
otherwise-idle empty warp therefore stages each tile's ids into a
4-stage smem ring (`cp.async`, its own tile-scheduler instance,
tail/window → −1 clamps applied at produce time), and the load warp
reads them back at LDS latency — the MLA-decode pt-loader design.
Compile-time gated to `pages_per_kv_tile >= 16`: at larger page sizes
the ring's fixed per-tile handshake measured worse than the id loads it
removes.
- **Register rebalance** (paged-only): one 8-register `setmaxnreg`
quantum moves from correction to the mma/load/epilogue group. Spill-free
either way; measured ~1–2% at ps16/32.

Non-paged kernels are unaffected: all paged code is `const_expr`-gated
and ragged cubins compile byte-identical.

## Performance

B200, CUPTI cold-L2 interleaved, 3-pass medians (9 passes for the two >4
ms cells, which drift at 3), hq/hk = 32/8, scrambled page tables, ratio
= paged / modular-ragged on identical logical problems
(bitwise-identical outputs; sliding-N = sliding window of N + causal):

| dtype | d | B | S | mask | ragged (µs) | ps8 | ps16 | ps32 | ps64 |
ps128 |
|---|---|---|---|---|---|---|---|---|---|---|
| bf16 | 128 | 1 | 16K | sliding-1024 | 374 | 1.071 | 1.027 | 1.017 |
1.024 | 1.013 |
| bf16 | 128 | 4 | 2K | sliding-512 | 158 | 1.069 | 1.025 | 1.019 |
1.026 | 1.009 |
| bf16 | 128 | 4 | 2K | causal | 172 | 1.072 | 1.041 | 1.007 | 1.014 |
1.000 |
| bf16 | 128 | 16 | 512 | causal | 97 | 1.058 | 1.015 | 1.011 | 1.019 |
1.000 |
| bf16 | 128 | 8 | 8K | causal | 4498 | 1.015 | 1.014 | 1.014 | 1.006 |
0.977 |
| bf16 | 128 | 2 | 16K | causal | 4221 | 1.031 | 1.018 | 1.009 | 1.019 |
1.021 |
| bf16 | 128 | 4 | 2K | full | 243 | 1.075 | 1.072 | 1.039 | 1.010 |
1.024 |
| bf16 | 128 | 16 | 512 | full | 94 | 1.091 | 1.080 | 1.028 | 1.018 |
1.013 |
| bf16 | 64 | 4 | 2K | sliding-512 | 132 | 1.066 | 1.013 | 0.995 | 0.998
| 0.992 |
| bf16 | 64 | 4 | 2K | causal | 150 | 1.080 | 1.058 | 1.037 | 1.035 |
1.009 |
| bf16 | 64 | 16 | 512 | causal | 79 | 1.083 | 1.052 | 1.034 | 1.028 |
1.013 |
| bf16 | 64 | 8 | 8K | causal | 3043 | 1.043 | 1.021 | 1.007 | 1.004 |
0.999 |
| fp8 | 128 | 4 | 2K | sliding-512 | 144 | 1.050 | 1.005 | 1.005 | 1.009
| 0.993 |
| fp8 | 128 | 4 | 2K | causal | 160 | 1.050 | 1.025 | 1.025 | 1.028 |
1.007 |
| fp8 | 128 | 8 | 8K | causal | 3160 | 1.023 | 1.015 | 1.008 | 1.010 |
0.999 |

## Tests

`tests/attention/test_modular_fmha_prefill_paged.py`: bitwise-vs-ragged
anchor (identity + scrambled tables × masks × page sizes 8–128 × varlen
incl. 1/7-token seqs × partial last page), pool-garbage immunity, NaN
canaries (tail + null-block window slots) at head dims 64 and 128,
window clamp boundary cases, LSE/fp8/mixed-dtype feature matrix, wrapper
integration + rejection paths (dtype universe,
combined-cache-with-mixed-dtypes, unsupported page size).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
  * Added paged KV-cache support for CuTe DSL prefill attention.
* Added page-table execution for variable-length pages and NHD/HND cache
layouts.
* Added support for causal and windowed attention, FP8 and mixed-dtype
caches, LSE output, ALiBi, soft-capping, and selected ragged-cache
workloads.
* Added validation for cache shapes, layouts, dtypes, page sizes, and
unsupported options.

* **Bug Fixes**
  * Improved handling of invalid, trailing, and window-excluded pages.

* **Tests**
* Added comprehensive paged-versus-ragged output coverage across
supported configurations.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [aaf97df](https://github.com/flashinfer-ai/flashinfer/commit/aaf97df45e73ccdc5e3854960a35792427a5a883)

- **作者**: Lee Nau
- **时间**: 2026-08-12T17:42:24Z
- **提交信息**: fix(fmha): propagate LSE reduction launch errors (#4389)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

Propagate errors returned by `ComputeLSEFromMD` using the existing
`FLASHINFER_CUDA_CHECK` convention.

Previously, a failed kernel launch could remain pending and surface
during an unrelated later CUDA operation, obscuring the true source.
Successful execution is unchanged.

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
* Improved CUDA error detection during LSE computation, helping surface
kernel execution issues more reliably.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [fb5a69a](https://github.com/flashinfer-ai/flashinfer/commit/fb5a69a982a4a5b846558735746e5bc5fc5805fd)

- **作者**: Ka-Hyun Nam
- **时间**: 2026-08-12T16:05:13Z
- **提交信息**: fix(gdn): convert fp16 decode operands and fix cache identity (#4219)

## Issue
https://github.com/flashinfer-ai/flashinfer/issues/4214
Addresses GDN-C1 / GDN-C2 / GDN-C3 / GDN-H1 from the GDN CuTe-DSL cache
audit (PR #1 of the suggested sequence).

## Summary

- Documented FP16 `q/k/v/a/b` on the BF16-state and FP32-state MTP
decode paths were silently reinterpreted as BF16 because the kernels
hard-code `cutlass.BFloat16` fragments. Convert those operands to BF16
at the kernel boundary (and stage non-BF16 caller `output=` on MTP).
- Add polymorphic operand dtypes (`A_log`, `dt_bias`, slot indices) to
the compile-cache identities so mixed-dtype sequences no longer collide.
- Stop returning a cached per-batch default `output` buffer from
BF16-state paths when `output=None`.
- Apply the same FP16 conversion on the WY output-only kernel; convert
slot indices to int32 when needed.
- Follow-up: non-BF16 MTP `output=` staging uses `output.to(bfloat16)`
(not `empty_like`) so negative-index padding rows keep
caller-initialized values.
- Assert documented `dt_bias` (bf16/fp32) and `initial_state_indices`
(int32/int64) dtypes at the public API.

## Test plan

- [x] New regressions in `tests/gdn/test_decode_delta_rule.py` (8
parametrizations): FP16 conversion, dtype / `dt_bias` interleaving,
default-output non-aliasing, non-BF16 `output=`, padding-slot
preservation, WY FP16
- [x] Those regressions fail on unmodified `main` (most on main) and
pass on this branch
- [x] Full `tests/gdn/test_decode_delta_rule.py`: **838 passed** on H100
NVL (`CUDA_VISIBLE_DEVICES=1`, `-x -vv`, ~38 min)
- [ ] GPU CI: `@flashinfer-bot run`

## Review

Independent re-review at `024e7c4f`: **approve-with-nits** (padding
critical fixed). Follow-up commits add comment trim + API dtype asserts.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
  * Improved validation for tensor data types, shapes, and index values.
* Fixed mixed-precision decode workflows, including proper BF16
conversion and preservation of requested output types.
* Prevented stale output reuse and preserved padding in partially filled
output buffers.
* Improved compilation behavior when switching between supported input
data types.

* **Tests**
* Added coverage for FP16/BF16 conversion, output handling, cache
isolation, index validation, and mixed-precision correctness.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [c285307](https://github.com/flashinfer-ai/flashinfer/commit/c2853079cfc6c5bdaaeb12a3c1602a4380dbe89f)

- **作者**: FlashInfer Bot
- **时间**: 2026-08-12T15:49:31Z
- **提交信息**: Update Docker CI tags to 20260811-e673f7f (#4457)

This PR updates the Docker CI image tags to the latest version:
`20260811-e673f7f`

Updated images:
- flashinfer/flashinfer-ci-cu126:20260811-e673f7f
- flashinfer/flashinfer-ci-cu128:20260811-e673f7f
- flashinfer/flashinfer-ci-cu129:20260811-e673f7f
- flashinfer/flashinfer-ci-cu130:20260811-e673f7f
- flashinfer/flashinfer-ci-cu132:20260811-e673f7f

Auto-generated by [release-ci-docker
workflow](https://github.com/flashinfer-ai/flashinfer/actions/runs/31462760669)

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Improved FP8 E4M3 conversion by saturating overflowing and infinite
values to the maximum finite range instead of producing NaN.
* Applied consistent behavior across supported FP16 and BF16
quantization paths.

* **Chores**
* Updated CI Docker image tags for CUDA 12.6, 12.8, 12.9, 13.0, and
13.2.
  * Ensures automated builds use the latest configured image versions.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: qsang-nv <200703406+qsang-nv@users.noreply.github.com>
Co-authored-by: Brian K. Ryu <bryu@nvidia.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-08-13
**监控日期**: 2026-08-12
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3941
- **最后更新**: 2026-08-12T13:24:12Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-08-13
**监控日期**: 2026-08-12
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34294
- **最后更新**: 2026-08-12T22:34:38Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: YiYi Xu

## AI分析总结

# 提交分析：Wan-Animate-2 支持

## 1. 主要更新类型
**功能新增**——为diffusers库新增Wan-Animate-2模型的完整支持，属于新模型集成类更新。

## 2. 关键变更点
- 新增Wan-Animate-2的推理pipeline，包括模型加载、去噪调度和视频生成流程
- 集成对应的VAE、文本编码器和UNet等组件
- 添加相关配置类、示例脚本和文档说明

## 3. 对项目的影响
Wan-Animate-2是阿里系视频生成模型，此次集成使diffusers用户可直接调用该模型进行动画/视频生成，扩展了库在视频生成领域的能力边界。作为HuggingFace生态的核心扩散模型库，持续集成前沿视频模型是保持竞争力的关键策略。

## 4. 值得关注的技术点
- 视频生成pipeline的时序建模与帧间一致性处理
- 与现有图像生成pipeline的代码复用和架构兼容性
- 多模态（文本+图像）条件输入的融合方式

## 5. 对项目发展的意义
diffusers定位于统一、易用的扩散模型工具库。Wan-Animate-2的加入延续了"快速跟进SOTA模型"的发展路径，丰富了视频生成模型矩阵（已有AnimateDiff、ModelScope等），巩固其作为社区首选扩散模型平台的地位，同时为后续视频生成能力的统一抽象奠定基础。

## 详细提交记录

### [3a2f35d](https://github.com/huggingface/diffusers/commit/3a2f35d4efa4c059c8bfb3bc0d6c906264895c81)

- **作者**: YiYi Xu
- **时间**: 2026-08-12T18:48:05Z
- **提交信息**: Wan-Animate-2 (authored by @kelseyee) (#14413)

* support wan-animate-2

---------

Co-authored-by: kelseyee <971704395@qq.com>
Co-authored-by: yiyi@huggingface.co <yiyi@huggingface.co>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>
Co-authored-by: sayakpaul <spsayakpaul@gmail.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-08-13
**监控日期**: 2026-08-12
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 431
- **最后更新**: 2026-08-11T01:47:46Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-08-13
**监控日期**: 2026-08-12
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12922
- **最后更新**: 2026-08-12T16:02:15Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 3
- **主要提交者**: Jinyan Ye, Hong Zhang, NancyFyong

## AI分析总结

# DiffSynth-Studio 提交分析报告

## 一、主要更新类型

本次提交记录包含三类核心更新：**新模型支持**（MiniMax-H3 Turbo LoRA、LingBot-Video MoE）、**量化框架重构**（QuantBackend 契约机制）、以及**文档与示例完善**。整体以功能新增为主，辅以框架级架构优化。

## 二、关键变更点与项目方向

1. **MiniMax-H3 Turbo LoRA 支持**：新增文本生成模型的 LoRA 微调与低显存推理能力，扩展了项目从视频/图像生成向多模态文本生成方向的覆盖。

2. **量化框架重构**：引入可机器验证的 `QuantBackend` 契约接口，统一了 torchao 和 ideogram4_fp8 的量化实现，修复了序列化、低显存推理等多项问题。这属于基础设施级优化，直接服务于项目"高效生成"的核心目标。

3. **LingBot-Video MoE 支持**：这是最大规模的更新，包含 Dense-1.3B 和 MoE-30B-A3B 两个版本，实现了两阶段高分辨率视频精修、注意力层 LoRA 训练、T2V/V2V 推理管线，并配套了完整的文档、提示词重写工具和低显存示例。

## 三、项目影响与意义

- **模型生态扩展**：新增两个模型家族，使 DiffSynth-Studio 从图像/视频生成工具向更广泛的生成式 AI 平台演进。
- **训练能力增强**：LingBot-Video 的 SFT 训练支持填补了项目在视频模型微调方面的空白，配合 LoRA 机制降低了训练门槛。
- **工程化水平提升**：量化框架的契约化设计增强了代码可维护性和可扩展性，为后续接入更多量化后端奠定基础。

## 四、值得关注的技术点

1. **QuantBackend 契约设计**：通过 `quantized_linear_classes`、`checkpoint_key_patterns` 等接口定义，实现了量化后端的标准化接入，这是工程架构上的重要进步。
2. **MoE 模型的 VRAM 管理**：针对 MoE 专家权重（grouped nn.Parameter）的特殊处理，避免整模型包装导致显存浪费，体现了对大规模模型推理的深度优化。
3. **5D 视频编解码路径**：在 QwenImageVAE 上以向后兼容方式扩展视频支持，展示了模块复用与扩展的优雅设计。
4. **UniPC 调度器**：为流匹配训练与 UniPC 多步推理提供统一调度，兼顾训练与推理效率。

## 五、对项目发展的影响

从 README 可知，DiffSynth-Studio 定位为多模态生成工具集，强调"高效、灵活、易用"。本次提交在三个维度推动项目发展：

1. **广度扩展**：从图像/视频生成扩展到文本生成（MiniMax-H3），并新增视频 MoE 模型，强化了"多模态"定位。
2. **深度强化**：量化框架重构和 VRAM 管理优化，直接响应了低显存推理这一社区高频需求，有助于吸引更多资源受限的用户。
3. **生态建设**：完整的文档、训练脚本和验证工具，降低了二次开发门槛，有利于构建活跃的开发者社区。

总体而言，这是一次"功能+架构"双轮驱动的更新，既满足了用户对新模型的需求，又为长期技术演进打下了更稳固的基础。

## 详细提交记录

### [ea0bf33](https://github.com/modelscope/DiffSynth-Studio/commit/ea0bf335d0d4a05c9b8ad90c476e1f5964dd842c)

- **作者**: Jinyan Ye
- **时间**: 2026-08-12T11:03:05Z
- **提交信息**: Support MiniMax-H3 Turbo LoRA (#1586)

* add: MiniMax-H3-Turbo

* fix: LoRA Loader of Minimax-H3

* add: minimax-h3 turbo LoRA low vram inference

* update docs

* fix: low vram inference

### [676bc96](https://github.com/modelscope/DiffSynth-Studio/commit/676bc96f1318c44b7be6312bd2f98f63c1dfe0df)

- **作者**: Hong Zhang
- **时间**: 2026-08-12T08:40:51Z
- **提交信息**: Update quantization framework (#1581)

* Add machine-verifiable quant backend contract and torchao serialization fix

Adds the QuantBackend contract (quantized_linear_classes, checkpoint_key_patterns,
resolve_checkpoint_keys, check_backend_contract, build_quantized_shell) and wires it
through QuantizeConfig/MixedQuantizeConfig and VRAM management; refactors torchao and
ideogram4_fp8 onto it. Fixes torchao unflatten crashing on root-level (dotless) tensors.

* fix zimage disk offload

* fix ideogram

* comments refactored

* fix training disclaimer

* fix ideogram rope

* fix mixedconfig serialization

* fix multimodel mixed device

* add serialization

* fix quant lora patch

### [1af4c26](https://github.com/modelscope/DiffSynth-Studio/commit/1af4c261114a13d7e83c25d89c6b66b9ff76f86a)

- **作者**: NancyFyong
- **时间**: 2026-08-12T08:26:19Z
- **提交信息**: Support the LingBot-Video MoE refiner (two-stage high-resolution refinement) (#1546)

* Add LingBot-Video (Dense-1.3B) support with attention-only LoRA SFT

Model code:
- LingBotVideoDiT (diffsynth/models/lingbot_video_dit.py) video denoiser
- Qwen3-VL text-encoder wrapper (lingbot_video_text_encoder.py)
- T2V/V2V pipeline (diffsynth/pipelines/lingbot_video.py)
- LingBotVideoUniPCScheduler (FlowMatchScheduler subclass): UniPC multistep
  for inference, flow-matching schedule for training
- Reuse QwenImageVAE via an additive, backward-compatible 5D-video
  encode/decode path in qwen_image_vae.py
- Register models + state-dict converters in model_configs.py

Training (issue's core deliverable):
- LingBotVideoTrainingModule (examples/lingbot_video/model_training/train.py)
  with the flow-matching SFT objective
- Attention-only LoRA launch script (to_q,to_k,to_v,to_out; MoE/FFN/router
  left frozen)

Examples + docs:
- T2V/V2V inference and low-VRAM examples
- examples/lingbot_video/README.md

Part of the SFT training support for modelscope/DiffSynth-Studio#1530.

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

* Add docs, prompt rewriting, LoRA validation, and low-VRAM example for LingBot-Video

- docs/{en,zh}/Model_Details/LingBot-Video.md + index.rst toctree entries
- two-stage prompt rewriter (structured JSON captions) + offline caption rewrite tool
- LoRA training validation script
- relocate low-VRAM inference into model_inference_low_vram/

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

* Add LingBot-Video MoE-30B-A3B support

Register the MoE 30B-A3B DiT (128 experts, top-8 group-limited routing, 1
shared expert) and add VRAM management module maps for the LingBot-Video DiT
and text encoder, which previously had no entry and fell back to whole-model
wrapping. The MoE experts store their weights as grouped nn.Parameter rather
than nn.Linear, so the expert container itself is wrapped -- without that the
experts, which are the bulk of the model, would stay resident.

Also fixes three issues surfaced while validating the MoE path:

- _run_grouped_experts guarded the fast path with hasattr(torch, "_grouped_mm"),
  which is True on CPU even though the kernel is CUDA-only. Now device-aware.
- The block and DiT forwards derived the activation dtype from .weight.dtype.
  Under VRAM management the wrapped layer holds its weight in the offload dtype
  (or on meta for disk offload), so this read the wrong dtype. Resolved from
  computation_dtype instead.
- The fp32-pinned timestep and modulation MLPs were fed fp32 activations while
  VRAM management wraps every nn.Linear at computation_dtype, raising a dtype
  mismatch on any low-VRAM run. Resolved per-layer.

The dense low-VRAM example set only vram_limit, which is a no-op without
offload_dtype/offload_device, so VRAM management never activated; corrected
along with the same claim in the docs.

Validated against the official implementation with identical weights: router
selection and gate scores are bit-exact, and the full DiT matches bit-exactly
at fp32 (bf16 differs only because diffusers' .to() downcasts the fp32-pinned
modules). The registered model_hash matches the released checkpoint headers
across all 977 keys with no shape mismatches.

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

* Address PR #1539 review: unify scheduler, restore VAE, split rewriter

- Scheduler: use FlowMatchScheduler (Wan template) instead of a bespoke
  UniPC scheduler; flow_match.py restored byte-identical to main.
- VAE: restore QwenImageVAE to upstream; the 5D-video encode/decode and
  latent normalisation now live in LingBotVideoPipeline (encode_video /
  decode_video).
- Rewriter: keep only normalize_caption in diffsynth core; move the
  two-stage prompt rewriter + system prompts into the inference examples.
- Examples: merge into one lingbot-video-dense-1.3b.py (T2V / V2V /
  optional rewrite); drop the separate _rewrite.py.
- Training .sh: use --model_id_with_origin_paths instead of local --model_paths.
- Docs: sync en/zh Model_Details + example README.

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

* Fix low-VRAM fp32/bf16 dtype mismatch in LingBot-Video DiT

Under low-VRAM offload the AutoWrapped modules compute weights in bf16 but do
not cast their inputs, and reading `.weight.dtype` from outside the wrapper
returns the resident fp8 dtype. The parameter-free sinusoidal `time_proj`
always returns fp32, so feeding it straight into the bf16 `time_embedder` MLP
raised "mat1 and mat2 must have the same dtype, but got Float and BFloat16";
`proj_out` had the mirror bug via `self.proj_out.weight.dtype` (fp8 under
offload). Cast both inputs to the running compute dtype (`joint`) instead,
which is bf16 under offload and matches the weight dtype in a full-precision
run. No effect on the normal (non-offload) path.

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

* Fold normalize_caption into lingbot_video pipeline module

The trimmed diffsynth/pipelines/lingbot_video_prompt_rewriter.py held only
normalize_caption (caption -> compact-JSON serialisation) after the prompt
rewriter was moved to the examples. Its sole core consumer is the pipeline,
which already calls it internally, so keeping a separate one-function module
added a misleadingly-named file ("prompt_rewriter" that no longer rewrites)
for no benefit.

Move normalize_caption (and its _serialize_caption/_caption_from_sample
helpers) into diffsynth/pipelines/lingbot_video.py as module-level functions
and delete the old module. All importers now pull it from lingbot_video; the
example inference/training scripts already imported the pipeline, so this only
tidies their imports. The prompt-rewriting logic stays out of core, in
examples/lingbot_video/model_inference/prompt_rewriter.py.

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

* Add normalize_caption to lingbot_video and fix importers

Companion to the previous commit, which only recorded the deletion of
lingbot_video_prompt_rewriter.py. This commit adds normalize_caption (and its
_serialize_caption/_caption_from_sample helpers) into
diffsynth/pipelines/lingbot_video.py as module-level functions, and repoints
every importer (the pipeline itself, the model_inference / low_vram example
scripts, the example prompt_rewriter, train.py and rewrite_captions.py) at
diffsynth.pipelines.lingbot_video. Restores a working tree: the two commits
together move the single remaining function into the pipeline module.

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

* Trim verbose comments in LingBot-Video code

Collapse the AI-generated multi-paragraph banners and docstrings to concise
one-line "why" comments matching DiffSynth's light comment style. No code changes.

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

* Fix dtype mismatch feeding the fp32-pinned time_embedder

time_embedder is fp32-pinned (LINGBOT_VIDEO_FP32_MODULES), so under a standard
load its weights stay fp32 while joint (the bulk hidden state) is bf16. Casting
the fp32 timestep_proj to joint.dtype fed bf16 into the fp32 Linear, raising
"mat1 and mat2 must have the same dtype" on any non-offload run. Cast to the
layer's own weight dtype instead: fp32 under standard load, bf16 under low-VRAM
offload (where the wrapper casts these MLPs to the compute dtype). proj_out keeps
joint.dtype since it is a bulk layer held in fp8 under offload.

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

* Add t2v_example_4 structured caption

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

* Add TI2V (image-to-video) support to LingBot-Video pipeline

Condition generation on a first frame via a new `input_image` argument.
Dense-1.3B reuses its T2V checkpoint (DiT unchanged, in_channels=16); the
condition frame is used twice, matching the original LingBot-Video i2v
pipeline: fed to the Qwen3-VL text encoder as a visual reference (image
tokens prepended to the prompt), and VAE-encoded to a clean latent pinned
into the first temporal slot before sampling and after every scheduler step.

- LingBotVideoUnit_ImageEmbedder builds the cond latent (via encode_video)
  and the smart-resized VLM image; no-op for T2V/V2V.
- LingBotVideoUnit_PromptEmbedder passes the image to the processor when present.
- Ported smart_resize / cover-resize+center-crop / _vlm_image helpers.
- Example lingbot-video-dense-1.3b_ti2v.py + released first frame and caption.
- EN/ZH docs and example README document the TI2V path and `input_image`.

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

* Add text-to-image (t2i) support and example to LingBot-Video

t2i is text-to-video with num_frames=1 through the same pipeline and DiT
(no separate image weight), matching the official runner which sets
num_frames=1 and swaps in the still-image negative prompt.

- Add DEFAULT_NEGATIVE_PROMPT_IMAGE (verbatim from the official pipeline):
  drops the temporal/motion terms that cannot apply to a single frame.
- Example lingbot-video-dense-1.3b_t2i.py + released still-image caption
  prompts/t2i_example.json; saves the single returned frame as PNG.
- EN/ZH docs and example README document the t2i path.

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

* Add ti2v/t2i low-VRAM inference + ti2v LoRA training examples

- model_inference_low_vram: add ti2v (input_image) and t2i (num_frames=1 +
  DEFAULT_NEGATIVE_PROMPT_IMAGE) low-VRAM variants, mirroring the t2v script.
- train.py: add opt-in --first_frame_as_condition for image-to-video LoRA. It
  conditions each clip on its own first frame; FlowMatchSFTLoss already pins the
  clean first-frame latent and excludes it from the loss, so no core change is
  needed. A distinct condition column still works via --extra_inputs input_image.
- model_training: add ti2v LoRA launch script and validate_lora example.
- docs (en/zh) + example README: reference the new scripts and TI2V LoRA.

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

* update vae&inner_func

* tmp commit for code refactor

* low vram patch&refactor scripts

* remove fp32 cast to keep compatibility with low-vram-inference

* add support for full train

* style refactor

* pop changes for ti2v pipeline

* Align TI2V / T2I examples, LoRA + full training, docs and README with reviewer's refactor (531ba56)

- TI2V + T2I inference / low-VRAM examples rewritten to the new pipeline API: read
  structured captions from JSON, pass pipe.default_negative_prompt(_image), drop the
  removed module-level normalize_caption / DEFAULT_NEGATIVE_PROMPT_IMAGE imports.
- Add default_negative_prompt_image attribute to LingBotVideoPipeline (T2I variant
  with temporal terms removed) so t2i examples can reference it symmetrically with
  default_negative_prompt.
- TI2V LoRA training script aligned to the reviewer's new t2v LoRA (dataset path,
  num_frames=81, num_epochs=5, dataset_repeat=50); validate_lora rewritten to use
  pipe.default_negative_prompt + json.load.
- New TI2V full-parameter training script + validate_full script (parallel to the
  reviewer's t2v full training), toggled via --first_frame_as_condition.
- Docs rewritten to match the standard Model_Details template: single-checkpoint
  overview covering T2V / TI2V / T2I with 3-row Examples table, input_image param
  documented, prompt-rewriter moved under Model Inference, VAE-internals text
  dropped per reviewer's "keep it about model info + usage" directive.
- README.md / README_zh.md: add Update History entry and Video Synthesis series
  block (Quick Start + Examples table) for LingBot-Video.

* fix: manage Qwen3-VL vision tower in LingBotVideoTextEncoder VRAM map

Low-VRAM TI2V feeds the condition frame through the Qwen3-VL vision tower,
but the LingBotVideoTextEncoder VRAM-management map did not cover its module
types. The vision LayerNorm / patch-embed weights stayed on `meta` and the
vision RoPE `inv_freq` (a non-persistent buffer, absent from the checkpoint)
stayed on CPU, so a TI2V run under offload died with a cuda/cpu device
mismatch. T2V / T2I never touch that path.

Add LayerNorm, Qwen3VLVisionPatchEmbed and Qwen3VLVisionRotaryEmbedding to
the map. PatchEmbed is wrapped whole (not its inner Conv3d) because its
forward reads `self.proj.weight.dtype` to cast the input, which under offload
would otherwise pick up the fp8 dtype and crash on the bf16 bias.

Co-Authored-By: Claude Opus 5 <noreply@anthropic.com>

* style: group input_image under image-to-video in pipeline __call__

The input_image param (the TI2V condition frame) was grouped under a
'# Video-to-video' comment. Relabel it '# Image-to-video (TI2V)' to match
wan_video.py's param grouping and the file's own TI2V terminology.

Co-Authored-By: Claude Opus 5 <noreply@anthropic.com>

* refactor: move TI2V helpers into the units that use them

Address reviewer comments on lingbot_video.py (:20, :185, :214):

- Move the module-level TI2V constants (IMAGE_MIN/MAX_TOKEN_NUM, MAX_RATIO,
  SPATIAL_MERGE_SIZE) and helpers (smart_resize, _round/_ceil/_floor_by_factor,
  _pixel_tensor_to_pil) plus the pipeline methods preprocess_cond_image,
  _vision_patch_size and _vlm_image into LingBotVideoUnit_ImageEmbedder, the
  only consumer. Move IMG_PROMPT_TEMPLATE into LingBotVideoUnit_PromptEmbedder.
- Move the pre-loop first-frame latent pin out of __call__ and into
  LingBotVideoUnit_ImageEmbedder.process; reorder self.units so
  InputVideoEmbedder (which produces `latents`) runs before ImageEmbedder
  (which pins into it) and before PromptEmbedder (which consumes vlm_image).
  __call__ keeps only the per-step re-pin inside the denoise loop.

Behavior-preserving for inference and training (the loss overwrites `latents`
and does its own first-frame pin, so the unit-level pin is inert there).
Verified on GPU: TI2V pins frame 0 to the condition frame; T2V no-op path OK.

Co-Authored-By: Claude Opus 5 <noreply@anthropic.com>

* style: strip comments and align MoE-30B-A3B integration with repo conventions

- lingbot_video_dit.py: drop unused LINGBOT_VIDEO_FP32_MODULES /
  should_keep_in_fp32, remove docstring and inline comments, keep
  norm_out_modulation call on one line
- model_configs.py: keep only the ModelConfig example comment, collapse
  extra_kwargs onto a single line
- vram_management_module_maps.py: drop explanatory comments
- MoE inference examples: remove all comments and section dividers
- docs: restore the standard template layout, fold the MoE description
  into the model overview section
- README / README_zh: add the missing MoE row so the examples table
  matches the docs model overview table

* style: align MoE examples with the Dense inference examples

- use the released structured-JSON caption from prompts/t2v_example_1.json
  instead of free-form prose, matching the Dense T2V / TI2V / T2I examples
- switch the low-VRAM example to the Dense disk-offload profile
  (disk -> cpu fp8 -> cuda bf16, vram_limit - 0.5)
- add the video-to-video block to the low-VRAM example so it covers the
  same tasks as the Dense low-VRAM T2V example

* feat: add TI2V / T2I MoE-30B-A3B examples and load captions from the example dataset

- T2V examples now download the released structured caption through
  dataset_snapshot_download, reusing the lingbot-video-dense-1.3b dataset
  directory, exactly like the Dense T2V examples
- add TI2V and T2I MoE examples (inference + low VRAM) mirroring the Dense
  templates: shared prompts/ captions, assets/ti2v_first_frame.png,
  default_negative_prompt_image and num_frames=1 for T2I
- docs and README: split the MoE row into T2V / TI2V / T2I rows and mention
  the MoE variant in the release note

* fix: restore every DiT parameter under low-VRAM offload for the MoE map

Disk offload only materialises weights for module types listed in the VRAM
map, so the per-type MoE map left two owners of raw parameters on `meta`:
`LingBotVideoBlock.scale_shift_table` and the router weight / correction
bias. Both bf16 and low VRAM Dense and MoE inference crashed with
"Tensor on device meta is not on the expected device cuda:0".

- map `LingBotVideoBlock` and `LingBotVideoRouter` to
  `AutoWrappedNonRecurseModule`, which manages a module's own parameters
  while its children keep their individual wrappers, and drop the dead
  `torch.nn.LayerNorm` entry (`norm_out` has no affine parameters)
- cast `scale_shift_table` to the modulation dtype/device in the block
  forward, following `wan_video_dit.DiTBlock`
- keep `e_score_correction_bias` as a non-trainable parameter so the disk
  loader restores its checkpoint values instead of leaving CPU zeros, and
  add it in float32

Verified on Robbyant/lingbot-video-moe-30b-a3b: all six MoE examples and
the Dense low VRAM examples run, low VRAM peaks at 29.5 GiB versus 74.5 GiB
for bf16, and the low VRAM T2I output matches the bf16 output to 16.9/255.

* fix: point the MoE examples at the published Dense example-dataset directories

Dense and MoE share one example dataset on ModelScope; only
lingbot_video/lingbot-video-dense-1.3b_{t2v,ti2v,t2i}/ exists, so the MoE
examples read the same captions and condition frame instead of a MoE-specific
directory that was never published.

* refactor: drop the resolve_bulk_dtype helper from the MoE DiT

The bulk dtype is already the dtype of the incoming hidden states, and the
wrapped linears cast their own weights, so the helper only restated what
x.dtype / joint.dtype already carry. Removing it makes the file identical to
the Dense implementation except for the offload fixes; TI2V output stays
bit-identical in bf16 and under low-VRAM offload.

* fix: cast the MoE router and expert weights inside the model under offload

AutoWrappedNonRecurseModule leaves parameter casting to the model, and the
grouped-expert matmuls read experts.w1/w2/w3 directly instead of going through
a forward, so an AutoWrappedModule wrapper never got the chance to cast them.
With a vram_limit that actually forces layers to stay on CPU, the router
projection and the expert matmuls therefore hit CPU weights:

    RuntimeError: Expected all tensors to be on the same device,
    but got mat2 is on cpu

Move the experts to AutoWrappedNonRecurseModule as well and cast the router
weight, the correction bias and the three expert tensors to the token device
and dtype at use, matching how scale_shift_table is already handled. bf16 and
default low-VRAM outputs stay bit-identical.

* feat: add LoRA and full-parameter training examples for MoE-30B-A3B

* style: align the MoE accelerate config with the 14B training config

* feat: support the LingBot-Video MoE refiner for two-stage high-resolution refinement

* style: drop the '# --- Stage N' decorative separators from refiner examples

Matches the repo-wide no-decorative-separator rule already applied to the
other lingbot_video examples.

* review: address PR #1546 comments

- pipelines/lingbot_video.py:
  * shorten the refiner param comment to 'High-Resolution Refinement' (mi804 comment #3)
  * drop the in-loop step-after re-pin; the refiner reuses the existing
    'first_frame_latents' pin inside model_fn_lingbot_video (mi804 comment #2)
- docs/{en,zh}/Model_Details/LingBot-Video.md: remove the explanatory notes
  next to the model-overview table and inside the training section
  (mi804 comments #4/#6 and #5/#7)
- examples/lingbot_video/model_inference{,_low_vram}/*_refiner.py: drop the
  stage-1 base pass and load the reference clip straight from the example
  dataset (mi804 comments #8/#9)

* support cpu offload

* refine docs

---------

Co-authored-by: NancyFyong <NancyFyong@users.noreply.github.com>
Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>
Co-authored-by: mi804 <1576993271@qq.com>

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-08-13
**监控日期**: 2026-08-12
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 31718
- **最后更新**: 2026-08-12T22:40:27Z

## 提交统计

- **昨日提交总数**: 28
- **提交者数量**: 19
- **主要提交者**: Xiaoyu Zhang, Yuzhen Zhou, Mick

## AI分析总结

## 提交分析总结

### 1. 主要更新类型

本批次提交涵盖**性能优化**（占比最高）、**Bug修复**、**文档更新**、**新硬件/模型支持**、**CI/CD改进**及**功能新增**六大类。其中性能优化集中在FlashInfer内核、扩散模型（Diffusion）算子融合与调度优化；Bug修复涉及预填充计划内核竞态条件、MoE权重切分等关键问题；文档更新围绕Qwen3.8、GLM-5.2等新模型的部署配置与Cookbook。

### 2. 关键变更点与项目方向

- **Kimi K3系列优化**：融合MLA门控投影到QKV-A GEMM（#33623）、支持NPU平台（#33465）、升级FlashInfer至0.6.17并移除workaround（#33997），体现对前沿模型架构的深度适配与跨硬件支持战略。
- **扩散模型（Diffusion）专项优化**：连续多个提交（#34275、#34564、#34563、#34508、#34507、#34506、#34505、#34503）聚焦Cosmos、LTX-2、Z-Image、MiniMax H3等模型的算子融合、内存分配优化与SM103架构调优，显示项目正积极扩展多模态生成能力。
- **GLM系列支持**：修复MoE权重在流水线并行层间的切分（#33793）、新增MXFP4宽EP16的AMD夜间测试配方（#34476）及Cookbook（#34379），强化对国产大模型和AMD ROCm生态的支持。
- **CI/CD体系升级**：修复夜间测试失败（#34523）、AMD PR门禁切换至ROCm 7.2（#34204）、更新CI权限配置（#34610），提升工程稳定性与硬件覆盖。

### 3. 项目影响与潜在意义

- **性能提升**：FlashInfer MLA解码计划移除阻塞式D2H拷贝（#27689）可显著降低推理延迟；扩散模型算子融合与内存优化（#34508、#34275）有望加速视频生成任务。
- **硬件生态扩展**：Kimi K3 NPU支持（#33465）和AMD ROCm 7.2升级（#34204）表明项目正从NVIDIA独占走向多硬件平台适配，扩大用户基础。
- **模型覆盖增强**：新增Qwen3.8、GLM-5.2、Nemotron 3.5等模型的配置与Cookbook，持续跟进业界最新模型，保持框架竞争力。
- **稳定性保障**：修复c128预填充计划内核竞态（#32467）和MoE权重切分问题（#33793），提升大规模部署可靠性。

### 4. 值得关注的技术点

- **确定性FA4支持**（#33945）：为GLM-4.7-Flash提供确定性4比特浮点量化，对可复现推理有重要意义。
- **统一Radix缓存KL测试**（#34607）：针对混合SWA+Mamba架构的位精确测试，确保缓存一致性。
- **多模态运行时分配优化**（#34141）：预留分配并保持填充输入对齐，减少动态内存碎片。
- **扩散模型流式并行保存**（#34564）：视频输出保存的流式与并行化，降低I/O瓶颈。
- **QKNorm+RoPE精度调优**（#34505、#34507）：针对SM103架构的逐算子精度对齐，体现对位精确推理的极致追求。

### 5. 对项目发展的影响

结合README中SGLang作为高性能LLM推理框架的定位，本批次提交清晰呈现三条发展主线：**一是持续深化对前沿模型（Kimi K3、GLM-5.2、Qwen3.8）的推理优化**，通过内核级融合和硬件适配保持性能领先；**二是积极拓展多模态能力**，对扩散模型的密集投入表明SGLang正从纯文本LLM向视频/图像生成领域延伸；**三是构建更健壮的工程体系**，通过CI改进、多硬件支持和详尽的Cookbook文档，降低用户采用门槛。这些变更共同推动SGLang向**全模态、多硬件、生产级**推理框架演进，巩固其在开源社区的技术领导地位。

## 详细提交记录

### [c05eb85](https://github.com/sgl-project/sglang/commit/c05eb856f79ca98e2b36c225d95f0433869120c7)

- **作者**: Liangsheng Yin
- **时间**: 2026-08-12T22:40:20Z
- **提交信息**: [CI] Fix nightly test failures (#34523)

### [2b43819](https://github.com/sgl-project/sglang/commit/2b4381956f2dfc302ddb4c48a9ab30be41958838)

- **作者**: binbin Deng
- **时间**: 2026-08-12T19:32:08Z
- **提交信息**: fix(glm5.2): restrict MoE weights to local PP layers (#33793)

### [4f88363](https://github.com/sgl-project/sglang/commit/4f883636a2b386509a88ae25e240af940dbb3fef)

- **作者**: elvischenv
- **时间**: 2026-08-12T19:29:03Z
- **提交信息**: [Perf] FlashInfer MLA: remove blocking D2H in spec-decode plan (#27689)

### [3974b00](https://github.com/sgl-project/sglang/commit/3974b00359776e24aa257031b951ce8841c9b64a)

- **作者**: Ke Bao
- **时间**: 2026-08-12T18:15:36Z
- **提交信息**: Add bit-exact unified radix cache KL test for hybrid SWA + mamba (#34607)

### [773faf9](https://github.com/sgl-project/sglang/commit/773faf992d1160c69b234dce0dd56e36c74f1dde)

- **作者**: Oguz Ulgen
- **时间**: 2026-08-12T18:04:07Z
- **提交信息**: Reserve multimodal runtime allocations and keep padded inputs aligned (#34141)

Co-authored-by: Hanming Lu <69857889+hanming-lu@users.noreply.github.com>
Co-authored-by: Lianmin Zheng <lianminzheng@gmail.com>
Co-authored-by: wangwenchen0407 <wangwenchen@meta.com>
Co-authored-by: Hanming Lu <hanminglu@meta.com>

### [e6250c7](https://github.com/sgl-project/sglang/commit/e6250c7c70b03bcb007840a4d202c8730da1cf5f)

- **作者**: YAMY
- **时间**: 2026-08-12T18:02:35Z
- **提交信息**: docs: update Qwen3.8 disaggregated serving configs (#34601)

### [126010c](https://github.com/sgl-project/sglang/commit/126010c3734cd5d67f56183beb2e870d39cb9b25)

- **作者**: Ke Bao
- **时间**: 2026-08-12T17:58:21Z
- **提交信息**: [misc] update CI_PERMISSIONS.json (#34610)

### [b501311](https://github.com/sgl-project/sglang/commit/b501311fa147c05fa45e45d318417ba285d85bc8)

- **作者**: Chenchen Hong
- **时间**: 2026-08-12T16:21:34Z
- **提交信息**: [Kimi K3] Fuse MLA gate projection into QKV-A GEMM (#33623)

Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>
Co-authored-by: Brayden Zhong <b8zhong@uwaterloo.ca>

### [8549cce](https://github.com/sgl-project/sglang/commit/8549cce11b878d2fbf814d5e27bcc5e626890e70)

- **作者**: yiheng
- **时间**: 2026-08-12T16:15:41Z
- **提交信息**: [BugFix] Fix race in c128 prefill plan kernel on ragged extend (#32467)

Signed-off-by: EanWang211123 <wangyiheng@sangfor.com.cn>

### [d21eefc](https://github.com/sgl-project/sglang/commit/d21eefc94ff8e95ea70ba54ddde83b35ff26d340)

- **作者**: Xinyuan Tong
- **时间**: 2026-08-12T15:25:48Z
- **提交信息**: [Docs] Rename Qwen3.8-Max-DSpark to Qwen3.8-2.4T-A95B-DSpark (#34590)

### [ad47dde](https://github.com/sgl-project/sglang/commit/ad47dde65c0f5e4812e72c0eb8b3e98acbba8e1a)

- **作者**: Mick
- **时间**: 2026-08-12T15:18:16Z
- **提交信息**: [diffusion] optimize: fuse cosmos qk norm, rope, and kv packing (#34275)

### [f28bc5a](https://github.com/sgl-project/sglang/commit/f28bc5a6de37895552320bdd08167a260b1a762a)

- **作者**: Yichi Zhang
- **时间**: 2026-08-12T15:15:34Z
- **提交信息**: docs(cookbook): add BF16 recipes to Nemotron 3.5 Lightning (#34573)

### [8e7c07f](https://github.com/sgl-project/sglang/commit/8e7c07fae73445622ba4814ab99e4582666e8bd1)

- **作者**: zijiexia
- **时间**: 2026-08-12T15:07:46Z
- **提交信息**: [Docs] Add Qwen3.8 cookbook (#34587)

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [197832b](https://github.com/sgl-project/sglang/commit/197832bcf536543092e621e03d61ae2602a392d0)

- **作者**: McZyWu
- **时间**: 2026-08-12T13:20:14Z
- **提交信息**: [Kimi-K3][NPU]  Support Kimi-K3 on NPU (#33465)

### [dc5f6c4](https://github.com/sgl-project/sglang/commit/dc5f6c488317645d96dc630b1f410e4dfb6f9667)

- **作者**: Mick
- **时间**: 2026-08-12T12:03:37Z
- **提交信息**: [diffusion] optimize: stream and parallelize bit-exact video output saves (#34564)

### [9701cc1](https://github.com/sgl-project/sglang/commit/9701cc138cc80063a911139f82d16083226faa9e)

- **作者**: Mick
- **时间**: 2026-08-12T12:02:49Z
- **提交信息**: [diffusion] optimize: optimize bit-exact h3 reference video ingress (#34563)

### [9deb695](https://github.com/sgl-project/sglang/commit/9deb6952afa483e38f96385a375b96f463da5303)

- **作者**: Zhaoyi Li
- **时间**: 2026-08-12T10:53:14Z
- **提交信息**: [AMD][DI][CI] Add GLM-5.2 MXFP4 wide-EP16 2P1D nightly recipes (#34476)

### [b5d1453](https://github.com/sgl-project/sglang/commit/b5d1453ed26be6af77d4332cab3609c79a0c1120)

- **作者**: ajith-sirra-amd
- **时间**: 2026-08-12T10:39:25Z
- **提交信息**: [AMD] GLM 5.2 MXFP4 SGLANG COOKBOOK (#34379)

Signed-off-by: Sirra <asirra@amd.com>
Co-authored-by: giovanniguastiamd <giovanni.guasti@amd.com>

### [00bdafe](https://github.com/sgl-project/sglang/commit/00bdafe944d9be54d2b9817e9a20462b3587edb6)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-08-12T10:31:03Z
- **提交信息**: [AMD][CI] Swap the AMD PR gate to ROCm 7.2 and demote ROCm 7.0 to a daily shadow (#34204)

Co-authored-by: yctseng0211 <yctseng@smci355-ccs-aus-m12-17.cs-aus.dcgpu>
Co-authored-by: Chen <bingxche@amd.com>

### [b3bffef](https://github.com/sgl-project/sglang/commit/b3bffef70aa17733b48af91e4b529e72c913bc6e)

- **作者**: Mick
- **时间**: 2026-08-12T09:53:45Z
- **提交信息**: [diffusion] UX: suppress noisy worker startup warnings (#34512)

### [644d55e](https://github.com/sgl-project/sglang/commit/644d55ebfae18914e8d0ac7bbc67fa425bb87c8e)

- **作者**: Mick
- **时间**: 2026-08-12T09:52:40Z
- **提交信息**: [diffusion] feat: support native and peft minimax h3 loras (#34359)

### [00e57d7](https://github.com/sgl-project/sglang/commit/00e57d74f07b02a4a83a5b53938a8e5d075c5cde)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-08-12T09:17:26Z
- **提交信息**: Bump FlashInfer to 0.6.17 and remove Kimi K3 workarounds (#33997)

### [2d76d53](https://github.com/sgl-project/sglang/commit/2d76d537e5510dd8dcaa466d4f5d78ffaad7b6cb)

- **作者**: Yuzhen Zhou
- **时间**: 2026-08-12T08:57:34Z
- **提交信息**: feat: support deterministic FA4 for GLM-4.7-Flash (#33945)

### [1f008dc](https://github.com/sgl-project/sglang/commit/1f008dc226cd25b0b6cb1ab068249c03adccd7af)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-08-12T08:28:27Z
- **提交信息**: [Diffusion][LTX-2] Allocate AdaLN outputs from one contiguous slab (#34508)

### [daae3ac](https://github.com/sgl-project/sglang/commit/daae3acb3642f99f8ef0393c74188eea6d31b60d)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-08-12T08:27:44Z
- **提交信息**: [Diffusion][Z-Image] Tune native QK RMSNorm launch for SM103 (#34507)

### [4827061](https://github.com/sgl-project/sglang/commit/48270612478adfba1274ebc1f7bd084402bfc17a)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-08-12T08:26:31Z
- **提交信息**: [Diffusion] Make weight-only FP8 dequant cache torch.compile-safe (#34506)

### [84ce750](https://github.com/sgl-project/sglang/commit/84ce7502cf728e8f8f8c3ca45a0dd0103b8bcb02)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-08-12T08:25:24Z
- **提交信息**: [Diffusion][MiniMax H3] Extend exact QKNorm+RoPE rounding to SM103 (#34505)

### [45f7063](https://github.com/sgl-project/sglang/commit/45f706333536466479d8977be14768abda11e438)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-08-12T08:24:18Z
- **提交信息**: [Diffusion] Tune QK head LayerNorm for SM103 (#34503)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-08-13
**监控日期**: 2026-08-12
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1246
- **最后更新**: 2026-08-11T12:09:41Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-08-13
**监控日期**: 2026-08-12
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 88901
- **最后更新**: 2026-08-12T22:35:19Z

## 提交统计

- **昨日提交总数**: 25
- **提交者数量**: 21
- **主要提交者**: stefankoncarevic, 范裕达, Kunshang Ji

## AI分析总结

# vLLM 昨日提交分析（第1/1批，共25个提交）

## 一、主要更新类型

- **Bug修复**（约10个）：CI测试修复、DeepEP/DeepGEMM依赖固定、KV缓存布局兼容性、视频解码器错误处理、Anthropic停止序列边界、MiniMax-M3模型参数等
- **性能优化**（约5个）：Flash KDA输出内核（prefill性能提升1.1~1.4倍）、ViT避免长阻塞H2D拷贝、GDN注意力eager模式优化、context_lens计算路径优化
- **新功能支持**（约4个）：Dots3 NOTE多模态支持、DeepGEMM MegaMoE的R3捕获、DSpark置信度调度验证、XPU块量化FP8权重路由
- **平台适配**（约5个）：ROCm（AITER MXFP4测试、FP8解码查询反量化、Triton更新）、XPU（Triton shim、GDN注意力、W8A8内核）
- **文档与CI**（约3个）：API-key文档警告、x86 CPU镜像构建缓存、Qwen3.5 CI修复

## 二、关键变更点与项目方向

1. **多模态能力扩展**：Dots3 NOTE支持表明vLLM持续扩展多模态模型覆盖，与“为所有人提供LLM服务”的愿景一致
2. **MoE系统完善**：多个提交涉及MoE相关修复（DeepGEMM、DeepEP、AITER MXFP4），体现对高效MoE推理的持续投入
3. **硬件平台覆盖**：ROCm和XPU的适配工作显示vLLM正从NVIDIA独占走向多平台支持，扩大生态覆盖面
4. **投机解码创新**：DSpark置信度调度验证是推理加速的新探索，与vLLM“快速”定位契合

## 三、项目影响与潜在意义

- **稳定性提升**：依赖固定（DeepEP完整哈希、DeepGEMM pin更新）和CI修复降低了构建和测试的不确定性
- **性能竞争力增强**：Flash KDA内核的1.1~1.4倍prefill提升直接增强核心推理性能
- **多平台战略推进**：ROCm和XPU的持续适配使vLLM在非NVIDIA硬件上更具可用性
- **多模态生态扩展**：新模型支持吸引更广泛的用户群体

## 四、值得关注的技术点

1. **Flash KDA输出内核**：针对prefill阶段的kernel优化，收益显著
2. **DSpark置信度调度**：投机解码的新思路，可能影响未来推理加速方向
3. **DeepGEMM MegaMoE的R3捕获**：结合DeepGEMM的MoE优化，体现软硬件协同设计趋势
4. **ViT H2D拷贝优化**：减少长阻塞拷贝，改善多模态推理延迟
5. **混合KV缓存布局兼容性修复**：保证前缀缓存命中在复杂布局下的正确性

## 五、对项目发展的影响

vLLM正沿着“性能领先、多平台覆盖、多模态扩展”三条主线稳步推进。本批提交中，性能优化（Flash KDA、DSpark）巩固其“快速”定位；ROCm/XPU适配扩大硬件覆盖；多模态支持（Dots3）和MoE优化则回应了大模型推理的最新趋势。同时，大量Bugfix和CI改进表明项目在快速迭代中注重工程质量。整体来看，vLLM正在从“NVIDIA GPU上的高性能推理引擎”向“多硬件、多模态、多场景的通用LLM服务平台”演进，与README中“Easy, fast, and cheap LLM serving for everyone”的愿景高度一致。

## 详细提交记录

### [23f360e](https://github.com/vllm-project/vllm/commit/23f360edaaa39e2e933857eeab6babf64e57f8b6)

- **作者**: Wentao Ye
- **时间**: 2026-08-12T21:28:53Z
- **提交信息**: [CI Bug] Fix ci moe test (#52009)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [025d56a](https://github.com/vllm-project/vllm/commit/025d56a11e8f9bdf614af26e5386cdd8d322aaef)

- **作者**: Yongye Zhu
- **时间**: 2026-08-12T20:49:04Z
- **提交信息**: [Build] Update DeepGEMM pin to deepseek-ai nv_dev tip (#52035)

Signed-off-by: Yongye Zhu <zyy1102000@gmail.com>
Co-authored-by: Kimi Code <noreply@moonshot.ai>

### [34735ac](https://github.com/vllm-project/vllm/commit/34735aceda0be9d79d8f440fcb74a21825bde0b6)

- **作者**: Tyler Michael Smith
- **时间**: 2026-08-12T20:01:32Z
- **提交信息**: [Bugfix] Pin DeepEP by its full commit hash (#52028)

Signed-off-by: Tyler Michael Smith <tlrmchlsmth@gmail.com>

### [e62abc3](https://github.com/vllm-project/vllm/commit/e62abc37d4c341b6026b945d7aff7e7537cce75d)

- **作者**: xiao feng
- **时间**: 2026-08-12T19:54:45Z
- **提交信息**: [Bugfix][Kernel] Fix persistent top-k histogram reuse after short rows (#49139)

Signed-off-by: fxfxfxfxfxfxfxfx <227935476@qq.com>
Co-authored-by: Michael Goin <mgoin64@gmail.com>

### [7f7a32c](https://github.com/vllm-project/vllm/commit/7f7a32cfec0f1bc5b73c37200b86631523a1ea8f)

- **作者**: Lucas Wilkinson
- **时间**: 2026-08-12T19:27:48Z
- **提交信息**: [Spec Decode] DSpark confidence-scheduled verification (#47808)

Signed-off-by: Lucas Wilkinson <lwilkins@redhat.com>
Signed-off-by: Lucas Wilkinson <LucasWilkinson@users.noreply.github.com>
Signed-off-by: Benjamin Chislett <chislett.ben@gmail.com>
Signed-off-by: Lucas Wilkinson <wilkinson.lucas@gmail.com>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: Benjamin Chislett <chislett.ben@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [fe889ac](https://github.com/vllm-project/vllm/commit/fe889ac9255491e82e58012d7787e920c6c7fbc2)

- **作者**: Wentao Ye
- **时间**: 2026-08-12T18:51:48Z
- **提交信息**: [K3 Perf] Flash kda out kernel for prefill, 1.1~1.4x kernel performance improvement (#51311)

Signed-off-by: yewentao256 <zhyanwentao@126.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [19d61b1](https://github.com/vllm-project/vllm/commit/19d61b1273a56e0ebd8a9160bffb2e75dccad82b)

- **作者**: kiroxu
- **时间**: 2026-08-12T18:27:50Z
- **提交信息**: [Bugfix] Initialize DeepGemmQuantScaleFMT oracle lazily; bound QuantFP8 UE8M0 packed path to group_size 128 (#51359)

Signed-off-by: BabyDrangoner <148877251+BabyDrangoner@users.noreply.github.com>
Signed-off-by: kiroxu <148877251+BabyDrangoner@users.noreply.github.com>
Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [d20a031](https://github.com/vllm-project/vllm/commit/d20a031d33fb8d56cfe090681872319544040da7)

- **作者**: stefankoncarevic
- **时间**: 2026-08-12T17:45:45Z
- **提交信息**: [Bugfix][ROCm][MoE] Update AITER MXFP4 W4A16 tests to the renamed expert_mask (#51980)

Signed-off-by: Stefan Koncarevic <Stefan.Koncarevic@amd.com>

### [0fb168e](https://github.com/vllm-project/vllm/commit/0fb168e6ee546466573dd3b920149417e82d9123)

- **作者**: Wentao Ye
- **时间**: 2026-08-12T17:22:09Z
- **提交信息**: [CI Bug] Fix ci qwen3.5 (#52007)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [b745d08](https://github.com/vllm-project/vllm/commit/b745d08de14fddf0cbb843c686b5d335f7d658cc)

- **作者**: Hongxia Yang
- **时间**: 2026-08-12T16:40:41Z
- **提交信息**: [ROCm][K3] Dequantize the fp8 decode query for MLA backends without quant-query support - TRITON_MLA (#51860)

Signed-off-by: Hongxia Yang <hongxia.yang@amd.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [324f452](https://github.com/vllm-project/vllm/commit/324f452f640015e9616b5ad5615fae6c25eb6353)

- **作者**: Hongxia Yang
- **时间**: 2026-08-12T16:26:17Z
- **提交信息**: [ROCm] update triton in base docker for gluon compatibility (#51464)

Signed-off-by: Hongxia Yang <hongxia.yang@amd.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [6ea6c42](https://github.com/vllm-project/vllm/commit/6ea6c4265938df98e8797254c591be4d9fc04158)

- **作者**: Taneem Ibrahim
- **时间**: 2026-08-12T16:05:12Z
- **提交信息**: [Bugfix] Bound Anthropic stop sequences (#51997)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [8151f2a](https://github.com/vllm-project/vllm/commit/8151f2ad4366e3c3770be015ba949905c0a99f0c)

- **作者**: Russell Bryant
- **时间**: 2026-08-12T15:16:35Z
- **提交信息**: [Docs] Warn that --api-key does not gate all endpoints (#51999)

Signed-off-by: Russell Bryant <rbryant@redhat.com>
Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [9035151](https://github.com/vllm-project/vllm/commit/9035151d6c9fb726181469f9e6aa9ccbf9a5dacb)

- **作者**: 范裕达
- **时间**: 2026-08-12T15:13:20Z
- **提交信息**: [Model] Add native Dots3 NOTE multimodal support (#51255)

Signed-off-by: KurodaKanbei <mistergalahad@gmail.com>
Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: Jee Jee Li <jeejeelee@inferact.ai>
Co-authored-by: Jee Jee Li <pandaleefree@gmail.com>

### [b1b7520](https://github.com/vllm-project/vllm/commit/b1b752042f622c692d5019c3ea122f2f7ee9d6ac)

- **作者**: Max Hu
- **时间**: 2026-08-12T14:54:04Z
- **提交信息**: Avoid long-blocking H2D copies in ViT (#51841)

Signed-off-by: Max Hu <hyoung2991@gmail.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>

### [7aa248f](https://github.com/vllm-project/vllm/commit/7aa248fcfef5ba7a6bfb0ce314e328ce63abb9f9)

- **作者**: Kunshang Ji
- **时间**: 2026-08-12T12:10:10Z
- **提交信息**: [XPU][CI/Release][2/N] add triton shim in xpu requirements (#51935)

Signed-off-by: Kunshang Ji <kunshang.ji@intel.com>

### [8e95890](https://github.com/vllm-project/vllm/commit/8e958902eee56ca5158728f1dd5a32246f0246f3)

- **作者**: Michael Goin
- **时间**: 2026-08-12T11:08:40Z
- **提交信息**: [Bugfix] Disable fine-grained prefix-cache hits for incompatible hybrid KV layouts (#51843)

Signed-off-by: mgoin <mgoin64@gmail.com>

### [4c51ceb](https://github.com/vllm-project/vllm/commit/4c51ceb11bbc2177a3639dfae2592cd34b83a7ef)

- **作者**: dmai-afk
- **时间**: 2026-08-12T11:02:10Z
- **提交信息**: [Bugfix][Multimodal] Invalidate retained PyNvVideoCodec decoder after failure (#51139)

Signed-off-by: Dat Mai <dmai@nvidia.com>

### [86e2ab5](https://github.com/vllm-project/vllm/commit/86e2ab50aa24ed8be79e7b6b73da025d997992eb)

- **作者**: dmai-afk
- **时间**: 2026-08-12T10:58:46Z
- **提交信息**: [Bugfix][Frontend] Return 400 for invalid PyNvVideoCodec video input (#51120)

Signed-off-by: Dat Mai <dmai@nvidia.com>

### [e60f3c4](https://github.com/vllm-project/vllm/commit/e60f3c4c137f23bb870524b937719d24bde8715b)

- **作者**: Tan Pin Siang
- **时间**: 2026-08-12T10:52:30Z
- **提交信息**: [Bugfix] Fix MiniMax-M3 compressed-tensors FP8 MoE SwiGLU params (#46845)

Signed-off-by: Tan Pin Siang <tanpinsiang@gmail.com>

### [6accb77](https://github.com/vllm-project/vllm/commit/6accb779a361c723cded3f9422b48d3fe4da0901)

- **作者**: Li, Jiang
- **时间**: 2026-08-12T09:58:01Z
- **提交信息**: [CI] Add registry layer cache to x86 CPU image build (#51911)

Signed-off-by: jiang1.li <jiang1.li@intel.com>

### [8c011da](https://github.com/vllm-project/vllm/commit/8c011da6d0a45f2c9316ea3c658da754f770a178)

- **作者**: Chaojun Zhang
- **时间**: 2026-08-12T08:57:22Z
- **提交信息**: [XPU] Route block-quantized FP8 weights to the W8A8 kernel (#50787)

Signed-off-by: Chaojun Zhang <chaojun.zhang@intel.com>

### [aeece10](https://github.com/vllm-project/vllm/commit/aeece10c061b8ef708b1962c175f5600f05c1933)

- **作者**: Huanxing
- **时间**: 2026-08-12T08:23:39Z
- **提交信息**: [Bugfix][XPU] Run GDN attention as eager break under breakable cudagraph (#51928)

Signed-off-by: Huanxing <huanxing.shen@intel.com>
Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>

### [4eef91c](https://github.com/vllm-project/vllm/commit/4eef91c03cad3f080e46db1eeeadf121c9e6c136)

- **作者**: aoshen02
- **时间**: 2026-08-12T08:07:07Z
- **提交信息**: [Model] Support R3 capture with DeepGEMM MegaMoE (#51831)

Signed-off-by: aoshen02 <aoshen@inferact.ai>

### [10b7766](https://github.com/vllm-project/vllm/commit/10b7766a901c06ca35ca9fd995d5d43b3a585622)

- **作者**: Xin Yang
- **时间**: 2026-08-12T07:35:44Z
- **提交信息**: [Attention] Move context_lens_tensor compute into GDN prefill path (#51913)

Signed-off-by: Xin Yang <xyangx@amazon.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-08-13
**监控日期**: 2026-08-12
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 6071
- **最后更新**: 2026-08-12T21:52:55Z

## 提交统计

- **昨日提交总数**: 10
- **提交者数量**: 9
- **主要提交者**: Nick Cao, Shi Boao Bowie, amy-why-3459

## AI分析总结

## 提交分析总结

### 1. 主要更新类型

本批次提交涵盖**性能优化**（3项）、**Bug修复**（2项）、**功能新增**（1项）、**重构**（1项）、**测试增强**（1项）及**CI/CD改进**（1项），整体以性能优化和稳定性提升为核心。

### 2. 关键变更点与项目方向

- **TTS性能优化**（#5174、#5068）：针对OmniVoice和GLM-TTS的推理热路径进行深度优化，包括D2H批量传输、掩码缓存、文本嵌入缓存，以及将循环不变计算（文本嵌入、RoPE、掩码、CFG批处理）移出Euler循环。这与项目"快速、低成本"的定位高度契合。
- **输出处理器重构**（#5146）：OmniRequestOutput改为继承RequestOutput，消除嵌套包装，是8步重构计划的第2步，为统一输出处理架构奠定基础。
- **新模型支持**（#5842）：新增NVIDIA Nemotron VoiceChat-11B离线语音到语音能力，扩展了多模态模型生态。
- **Qwen-Image Edit测试**（#5656）：启用小模型测试，降低测试资源门槛，提升CI效率。
- **Diffusion TTS适配器修复**（#6121）：修复语音服务中的适配器查找问题，保障TTS功能稳定性。

### 3. 对项目的影响与意义

性能优化直接提升TTS服务的吞吐量和延迟表现，增强项目在实时语音交互场景的竞争力。输出处理器重构为后续多模态输出统一管理铺路，降低维护复杂度。新模型支持扩大了项目覆盖面，吸引更多用户场景。CI改进（夜间DockerHub发布）提升发布自动化水平，加快迭代节奏。

### 4. 值得关注的技术点

- **热路径优化策略**：D2H批量传输减少设备间通信开销，掩码缓存和文本嵌入缓存避免重复计算，这些技术对长序列TTS推理尤为有效。
- **循环不变代码外提**：将RoPE、CFG批处理等计算移出Euler迭代循环，是典型的编译器优化思想在推理引擎中的应用。
- **NPU融合RMSNorm**（#5915）：针对MiniMax H3 Qwen3-VL在NPU上的算子融合，体现对异构硬件的适配能力。
- **输出继承重构**：通过继承而非包装，简化了输出对象的类型层次，有利于后续功能扩展。

### 5. 对项目发展的影响

vllm-omni致力于提供"简单、快速、廉价"的全模态模型服务。本批次提交在三个维度推动这一目标：**性能维度**通过TTS热路径优化提升实时性；**生态维度**通过新增VoiceChat模型和Qwen-Image Edit测试扩大支持范围；**架构维度**通过输出处理器重构为多模态统一处理奠定基础。同时，NPU支持和CI改进表明项目正积极拥抱多样化硬件生态并提升工程效率。整体来看，项目正处于性能打磨和架构演进并行的阶段，为后续更广泛的多模态场景落地做准备。

## 详细提交记录

### [12f8168](https://github.com/vllm-project/vllm-omni/commit/12f81681793441632ffb7d68b200b9d61821e1f8)

- **作者**: Nick Cao
- **时间**: 2026-08-12T20:03:49Z
- **提交信息**: [Tests] Enable tiny model testing for Qwen-Image Edit and EditPlus (#5656)

Signed-off-by: Nick Cao <ncao@redhat.com>

### [72a02b4](https://github.com/vllm-project/vllm-omni/commit/72a02b492a6957acc4659fde09be85c00ad0f90b)

- **作者**: Zhenghan Song
- **时间**: 2026-08-12T19:20:12Z
- **提交信息**: [Bugfix] Fix diffusion TTS adapter lookup in speech serving (#6121)

Signed-off-by: HaningZS <resossr0v0@gmail.com>

### [5358f5d](https://github.com/vllm-project/vllm-omni/commit/5358f5db01e512dc20fcc29a1d122e82c8546780)

- **作者**: Juan Pablo Zuluaga
- **时间**: 2026-08-12T17:15:35Z
- **提交信息**: [Perf][TTS] omnivoice hot path: D2H batching, mask caching, cached text embeddings (#5174)

Signed-off-by: JuanPZuluaga <juanz9312@gmail.com>
Co-authored-by: Yueqian Lin <70319226+linyueqian@users.noreply.github.com>

### [e677360](https://github.com/vllm-project/vllm-omni/commit/e677360168d7d4f512bcebd50fbb1cbfc422d133)

- **作者**: MaciejBalaNV
- **时间**: 2026-08-12T17:04:07Z
- **提交信息**: Add cosmos-guardrail dependency and update error message (#6107)

Signed-off-by: Maciej Bala <mbala@nvidia.com>

### [208c677](https://github.com/vllm-project/vllm-omni/commit/208c6776a89f9dfa1598457196d71538bb9b24ac)

- **作者**: Juan Pablo Zuluaga
- **时间**: 2026-08-12T17:02:02Z
- **提交信息**: [Perf][TTS] glm_tts: hoist loop-invariant text embed, RoPE, mask and CFG batch out of Euler loop (#5068)

Signed-off-by: JuanPZuluaga <juanz9312@gmail.com>
Co-authored-by: Yueqian Lin <70319226+linyueqian@users.noreply.github.com>

### [fcf1085](https://github.com/vllm-project/vllm-omni/commit/fcf1085395940df1f9486e2f1b6f11581d8002c9)

- **作者**: Shi Boao Bowie
- **时间**: 2026-08-12T14:58:23Z
- **提交信息**: [Refactor][OutputProcessor 2/8]: OmniRequestOutput should inherit RequestOutput and no nested wrap-up (#5146)

Signed-off-by: Boao Shi <aoibosh@connect.hku.hk>
Signed-off-by: bowieshi <aoibosh@connect.hku.hk>
Signed-off-by: princepride <wangzhipeng628@gmail.com>
Signed-off-by: R2-Y <ruiruyang2@gmail.com>
Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>
Signed-off-by: Shi Boao Bowie <aoibosh@connect.hku.hk>
Co-authored-by: 汪志鹏 <wangzhipeng628@gmail.com>
Co-authored-by: ruirui(rein) yang <73573651+R2-Y@users.noreply.github.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>
Co-authored-by: Gao Han <hgaoaf@connect.ust.hk>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [38a2500](https://github.com/vllm-project/vllm-omni/commit/38a2500bdf887cd0d23c1c1616c59faec6ffd317)

- **作者**: Wenjia Li
- **时间**: 2026-08-12T11:12:54Z
- **提交信息**: [Perf] MiniMax H3 Qwen3-VL support fused RMSNorm on NPU (#5915)

Signed-off-by: Wenjia Li <wjialish@gmail.com>
Signed-off-by: Hongsheng Liu <liuhongsheng4@huawei.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [7cd826d](https://github.com/vllm-project/vllm-omni/commit/7cd826d28c7e986bbcdd740f099b4eb256b52c4f)

- **作者**: amy-why-3459
- **时间**: 2026-08-12T10:36:31Z
- **提交信息**: [Bugfix][MiniCPM-o] Align Daily-Omni offline loading and duplex soft-… (#6095)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [31384cb](https://github.com/vllm-project/vllm-omni/commit/31384cb39cf107809e64338519de55e119361221)

- **作者**: wangyu
- **时间**: 2026-08-12T09:30:55Z
- **提交信息**: [CI/Build] Add nightly DockerHub publish and cleanup to release pipeline (#6048)

Signed-off-by: wangyu <410167048@qq.com>
Signed-off-by: [Your Name] [Your Email]
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [5be7541](https://github.com/vllm-project/vllm-omni/commit/5be7541d01ccc4f34f8d2049cc9780ba67a7f26f)

- **作者**: Yuekai Zhang
- **时间**: 2026-08-12T08:25:48Z
- **提交信息**: [Model] Support NVIDIA-NemotronLabs-VoiceChat-11B offline speech-to-speech (#5842)

Signed-off-by: Yuekai Zhang <zhangyuekai@foxmail.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

---
