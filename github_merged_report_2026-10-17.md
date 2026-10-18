# GitHub Stars 合并报告 - 2026-10-17

**合并日期**: 2026-10-18
**监控日期**: 2026-10-17
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


**报告日期**: 2026-10-18
**监控日期**: 2026-10-17
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2247
- **最后更新**: 2026-10-17T14:52:47Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: dzy00897185

## AI分析总结

# VeOmni 昨日提交分析（607b2af）

## 1. 主要更新类型
- **功能新增**：扩展对国产NPU硬件及新模型的训练支持，属于硬件适配与模型覆盖面拓展的特性提交。

## 2. 关键变更点与项目方向的关系
- **NPU支持 Qwen-Image-Edit**：为字节自研的多模态图像编辑模型打通NPU训练路径，契合VeOmni"Model-Centric Distributed Recipe Zoo"的核心定位——为各类模型提供统一、可扩展的分布式训练配方。
- **Wan2.2 I2V（5B/14B）支持**：覆盖字节视频生成模型Wan2.2的图生视频（Image-to-Video）两个规格，将分布式训练recipe从语言/图像模态进一步延伸到视频生成领域。
- 两者共同强化了README中"Scaling **Any Modality** Model Training"的承诺，体现"模型为中心的配方库"思路：新模型接入只需提供对应的分布式训练recipe，而非修改框架核心。

## 3. 对项目的影响和潜在意义
- **硬件生态扩展**：NPU支持降低对NVIDIA GPU的依赖，为昇腾等国产芯片用户提供可用的多模态训练方案，有助于在国内AI基础设施环境下的落地与推广。
- **模态版图完善**：视频生成（I2V）是当前多模态训练算力需求最大的方向之一，加入Wan2.2两个规模使VeOmni在视频大模型训练赛道具备直接可用的recipe，吸引视频生成领域的研究者和工程师。
- **规模覆盖（5B→14B）**：证明其分布式策略（推测涉及张量并行/序列并行/重计算等）可随模型规模平滑扩展，增强了框架的说服力。

## 4. 值得关注的技术点
- NPU上的分布式算子适配与混合精度/重计算策略，是工程上较有挑战的部分，值得关注其实现方式。
- Wan2.2 I2V 14B这类大模型在多卡NPU/GPU上的并行策略选择（如视频序列的序列并行切分），体现了VeOmni在长序列、高分辨率视频训练场景的工程能力。
- PR编号#1234显示项目迭代活跃度较高，社区协作流程成熟。

## 5. 对项目发展的影响
结合README，VeOmni的目标是构建覆盖任意模态的分布式训练配方库。本次提交一次性新增NPU后端+图像编辑+视频生成三类支持，显著提升了：
- **广度**（模态与硬件矩阵更完整）和**深度**（更大规模模型的实战验证），
- 使项目从"多模态训练框架"向"字节系核心生成模型（Qwen-Image-Edit、Wan系列）的官方训练基建"演进，
- 有望吸引更多国产算力用户和视频生成研究者加入生态，进一步巩固其作为多模态分布式训练参考实现的地位。

## 详细提交记录

### [607b2af](https://github.com/ByteDance-Seed/VeOmni/commit/607b2af677ee22997f5934c3970e65016f49aacb)

- **作者**: dzy00897185
- **时间**: 2026-10-17T08:08:14Z
- **提交信息**: [model] feat: support NPU qwen_image_edit、Wan2.2 I2V 5B/14B  (#1234)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-10-18
**监控日期**: 2026-10-17
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2917
- **最后更新**: 2026-10-17T16:48:23Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-10-18
**监控日期**: 2026-10-17
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2304
- **最后更新**: 2026-10-17T17:04:13Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-10-18
**监控日期**: 2026-10-17
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6676
- **最后更新**: 2026-10-17T22:36:50Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 5
- **主要提交者**: Yanqin Zhai, Stu Cao, eigen

## AI分析总结

# FlashInfer 昨日提交分析（6 条记录）

## 1. 主要更新类型

- **性能优化（主导）**：3 条提交针对 GPU kernel 性能微调（LoRA GEMM、MSA 稀疏注意力、MoE 启发式）
- **功能新增**：1 条实验性 NVFP4 稠密 MLA decode 后端
- **Bug 修复**：2 条（dispatch 参数修正、wheel 打包缺失）
- **测试优化**：1 条（采样测试提速 8.8x）

## 2. 关键变更点与项目方向的关系

- **CAKE 生态深度整合**：6 条中有 4 条直接涉及 "CAKE"（内部 kernel 生成/调优体系），包括 SM90 LoRA、Blackwell MSA、MoE 启发式、MLA decode。FlashInfer 正在将自动生成的 kernel 家族系统性地接入主线，覆盖 H100（SM90）、B200/GB300（SM100/103）等多代硬件。
- **量化格式前沿推进**：新增 NVFP4（E2M1）paged latent cache 的 MLA decode，支持 Kimi-K3 / DeepSeek-V3 几何结构，体现了对低精度推理格式（FP8、NVFP4、MXFP8）的持续投入。
- **生产可用性打磨**：修复非编辑安装下 JIT 源文件缺失导致的运行时崩溃，说明项目正关注下游集成（如 vLLM）的实际部署路径。

## 3. 影响与潜在意义

- **性能层面**：MSA uniform-FP8 decode 与 Top-K 路径在 B200/GB300 上提速约 3–13%；MoE GenPhase 在 B300 上降低 8–20% 延迟；LoRA GEMM 特定形状提速 7–35%。这些均为稀疏注意力和 MoE 场景（长上下文 LLM 推理的核心瓶颈）带来实际收益。
- **可用性层面**：wheel 打包修复消除了 pip 安装用户的致命错误，降低集成门槛；采样测试提速使 CI 反馈更快。
- **生态层面**：MLA decode 与 vLLM 的 `nvfp4_ds_mla` 测试对接，表明 FlashInfer 与主流推理框架的耦合在加深。

## 4. 值得关注的技术点

- **TMA L2 rasterization group 调优**：通过详尽的 H100 实测矩阵（1–8 组、冷/热 L2、back-to-back/冷却对比）确定 group 1 优于 group 4，展现了对 GPU 底层调度参数的精细掌控。
- **硬件级特性使用**：MLA decode 使用 tcgen05 block-scaled MMA（mxf4nvf4、f8f6f4）和 on-chip V 转换，充分利用 Blackwell 专用指令。
- **软件工程实践**：每条 PR 附带可复现的 benchmark 表格（CUPTI 计时、交替进程、冷 L2），bitwise 精度一致性验证，以及 workload-aware 自适应启发式 + 离线调优缓存的设计。

## 5. 对项目发展的整体影响

结合 README 定位（"High-Performance GPU Kernels for Inference"），这批提交清晰展示了 FlashInfer 的三条发展主线：(1) **多架构覆盖**——从 H100 到 B200/GB300 的持续性能调优；(2) **低精度推理前沿**——FP8/NVFP4/MXFP8 在 attention、LoRA、MoE 中的落地；(3) **生态成熟度**——CAKE 自动生成体系从实验走向主线集成，同时补齐打包、测试、CI 等工程短板。这些工作共同强化了 FlashInfer 作为 LLM 推理 kernel 基础设施的竞争力。

## 详细提交记录

### [78cfe71](https://github.com/flashinfer-ai/flashinfer/commit/78cfe71127c59988ebafb600bd98e0178542f887)

- **作者**: eigen
- **时间**: 2026-10-17T22:36:45Z
- **提交信息**: fix(cake_quant_lora_gemm): launch the gated SM90 FP8 LoRA program with raster group 1 (#6705)

## 📌 Description

The SM90 FP8 LoRA dispatch rule (`sm90_fp8_lora_dispatch_v0`) still
sends long persistent runs over large-K panels to `fp8_sm90_hint` (TMA
L2 policies). It now launches that program with raster group 1 instead
of 4. Of the 62 H100 performance rows of the CAKE kernel harness, the
rule picks this program for only one: M 131072 x N 8192 x K 32768, rank
64. On that row this program takes 60.1-60.7 ms back to back and
58.7-60.4 ms cooled at group 1 (six runs), against 64.3-67.7 / 69.0-80.0
ms at group 4 (the four runs that swept the group): 1.07-1.12x back to
back and 1.17-1.35x cooled. Group 2 measures 60.5-62.2 / 59.4-63.0 ms,
within noise of group 1 (group 1 was faster in 7 of the 8 run medians;
in the other, gm2 back to back, it was 0.05 ms slower). Against the CAKE
acceptance reference, the legacy Cake kernel's production launch at
group 4 (62.6-65.3 / 65.8-78.5 ms), group 1 is 1.04-1.08x / 1.12-1.31x
faster per run.

- `flashinfer/jit/cake_quant_lora_gemm.py`: `gated_group_m` changes from
4 to 1 in both places in `PROGRAMS`. The `fp8_sm90_hint` record's
`group_m` also changes from 4 to 1, and the docstring is updated.
`default_group_m` stays 8.
- `tests/gemm/test_cake_quant_lora_gemm.py`:
`test_fp8_sm90_dispatch_rule` now expects `(8, 1)`. A new comment
records the measurements.

Each cell shows two medians in ms: windows run back to back / windows
run after a pause (cooled). The timings come from H100 runs in the CAKE
team's kernel harness, not from the FlashInfer launcher. Two processes
took turns on the same GPU in interleaved rounds, timed with CUPTI and a
cold L2.

| run (node) | group 1 | group 2 | group 4 | group 8 | legacy kernel,
group 4 (baseline) | legacy kernel, group 1 |
|---|---:|---:|---:|---:|---:|---:|
| gm1 (pool0-01789) | 60.57 / 59.04 | 62.17 / 59.35 | 67.66 / 70.25 |
79.49 / 86.34 | 65.03 / 68.54 | - |
| gm2 (pool0-01789) | 60.55 / 59.20 | 60.50 / 60.53 | 64.83 / 68.96 | -
| 65.30 / 67.18 | 60.36 / 58.58 |
| gm3 (pool0-01789) | 60.71 / 58.74 | 61.12 / 59.37 | 66.06 / 75.15 | -
| 64.28 / 66.78 | 60.64 / 57.94 |
| n2hint (pool0-01781) | 60.33 / 59.42 | 60.99 / 63.03 | 64.32 / 80.02 |
- | 62.60 / 78.04 | 60.03 / 59.56 |

The legacy kernel gets the same speedup at group 1, so the gain comes
from the raster order, not from the kernel.

Acceptance runs compared group 1 against the legacy group-4 baseline in
10 back-to-back and 5 cooled interleaved rounds per node. Each value is
the median of per-round legacy / new time:
- pool0-01789: 1.048 back to back (10/10 rounds >= 1.00), 1.121 cooled
(5/5).
- pool0-01781: 1.038 back to back (9/10), 1.270 cooled (5/5). In the one
losing round (0.960), the legacy kernel ran 57.65 ms, its fastest
group-4 window within that acceptance run (the second fastest of the
whole CAKE record, after a 57.31 ms window on the other node).

## 🔍 Related Issues

- #6324 added the SM90 programs (`fp8_sm90`, `fp8_sm90_hint`) and the
`sm90_fp8_lora_dispatch_v0` rule, with raster group 4 for the gated
program; #6581 left them unchanged.
- CAKE-2550 step 2 (CAKE team internal issue, no public link).

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] `pre-commit run --files flashinfer/jit/cake_quant_lora_gemm.py
tests/gemm/test_cake_quant_lora_gemm.py` (pre-commit 4.3.0, on a CPU
node, at `5e9fb1571d4a`): every hook passed (mypy, ruff check, ruff
format, end-of-file / whitespace / line-ending checks); the tree was
clean afterwards.
- [ ] `pre-commit run --all-files` was not run.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.): the host tests below
pass; the module's GPU tests were not re-run for this host-constant
change.

Host tests ran on a CPU node with no GPU, on tree `5e9fb1571d4a` (and
before the comment-only amend on `f37c19a06d7e`) with torch
2.13.0+cu130:
- `tests/gemm/test_cake_quant_lora_gemm.py` collects 164 tests.
- `pytest -k "fp8_sm90_dispatch or programs_table or select_template"`:
34 passed, 0 failed, 0 skipped.

## Reviewer Notes

- The kernel binary and numerics are unchanged. `group_m` is a runtime
scalar of the same program, and the output is bit-identical across
groups: there were 0 output mismatches in every measurement run,
including against the legacy kernel.
- Only the gated program's raster group changes. The default program
`fp8_sm90` keeps group 8, and the rule that decides which problems go to
`fp8_sm90_hint` is unchanged.
- The module's GPU tests were not re-run because this PR only changes a
host constant.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [eb9f0d2](https://github.com/flashinfer-ai/flashinfer/commit/eb9f0d28d08ac2b7275a1be4ad423044bc8e7569)

- **作者**: Adrian
- **时间**: 2026-10-17T22:24:18Z
- **提交信息**: test(cake_sampling): size frequency trials by effective support (#6515)

<!-- .github/pull_request_template.md -->

## 📌 Description

Replace five million fixed draws in the two frequency tests in
`tests/utils/test_cake_sampling_upstream.py` with an effective-support
budget computed from the filtered probabilities. These tests compare
frequencies with known probabilities, using `compare_two_samples=False`.
Round the budget up to whole 1,000-row batches and normalize by the
actual draw count. Keep the existing 0.99 cosine threshold and support
checks.


Measured with warm JIT caches on one GPU reported by `nvidia-smi` as
**NVIDIA Graphics Device**, SM100 (compute capability 10.0), 183,359
MiB, PyTorch 2.10.0+cu130. All cases below use
`normal_distribution(std=1)` and vocabulary size **128,256**. Values are
pytest case durations (setup/call/teardown) from JUnit XML, one
sequential run per revision. Cold JIT compilation is excluded.

| Case | Before | After |
|---|---:|---:|
| `test_top_k_sampling_freq[500-normal_distribution(std=1)-128256]` |
1.165 s | 0.178 s |
|
`test_top_k_top_p_sampling_freq[0.9-normal_distribution(std=1)-128256]`
| 0.773 s | 0.042 s |
| **Sum** | **1.938 s** | **0.220 s** |

The measured sum is 8.81x faster. The same six-case benchmark command
was run on the helper-only revision (fixed five-million-trial baseline)
and then on the combined follow-ups; only this file's cases are summed
above.

```bash
PYENV_VERSION=pt python -m pytest \
  'tests/utils/test_sampling.py::test_sampling_freq[0.0-normal_distribution(std=1)-128256]' \
  'tests/utils/test_sampling.py::test_top_p_sampling_freq[0.9-normal_distribution(std=1)-128256]' \
  'tests/utils/test_sampling.py::test_top_k_sampling_freq[500-normal_distribution(std=1)-128256]' \
  'tests/utils/test_sampling.py::test_sampling_from_logits_freq[normal_distribution(std=1)-128256]' \
  'tests/utils/test_cake_sampling_upstream.py::test_top_k_sampling_freq[500-normal_distribution(std=1)-128256]' \
  'tests/utils/test_cake_sampling_upstream.py::test_top_k_top_p_sampling_freq[0.9-normal_distribution(std=1)-128256]' \
  -q --durations=0 --junitxml=/tmp/sampling-benchmark.xml
```
## 🔍 Related Issues

Follow-up to #5515. Uses the shared helper merged in #6513.

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

Rebased onto current main after #6513 merged. This PR changes only
`tests/utils/test_cake_sampling_upstream.py` and can merge independently
of the other sampling follow-up. The rebase preserves the previously
validated test file and helper exactly; changed-file pre-commit hooks
and diff checks pass.

Validation on SM100:

```bash
PYENV_VERSION=pt python -m pytest tests/utils/test_sampling.py tests/utils/test_cake_sampling_upstream.py -k freq -q --durations=0
```

Original and optimized frequency matrices both passed: **138 passed, 6
skipped**. This file: **51 passed, 3 skipped**. The logits-processor
regression suite also passed: **591 passed, 12 skipped**. Scope is the
full affected frequency parameter matrix and the full logits-processor
file; other tests in the sampling files were not run.

Commit pre-commit hooks pass for the changed files. The trial formula is
a variance approximation with a safety factor, not a formal tail bound.
The helper retains #5515's 1.25 safety factor and 10,000-trial floor.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Tests**
* Sampling validation now adjusts trial counts to the filtered
probability distribution and rounds requested counts up to complete
batches. This provides more consistent coverage across probability
distributions without changing end-user functionality.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [ccce213](https://github.com/flashinfer-ai/flashinfer/commit/ccce2135a71dee8d50cb37cb5bacb5656879985e)

- **作者**: eigen
- **时间**: 2026-10-17T19:05:12Z
- **提交信息**: perf(cake_msa): faster Blackwell MSA uniform-FP8 decode and Top-K programs — epilogue overlap and QK ahead of PV (D-U1, D-U2, D-U2b), streaming Top-K merge network (S2), tradix v2 radix layout, per-architecture topk_select (CAKE-1183 round 10) (#6518)

> Developed by the **CAKE team**, this PR re-exports the Cake-generated
MiniMax Sparse Attention family for SM100 / SM103 with the CAKE-1183
levers accepted in rounds 9–10 that are not yet on `main` (S2, tradix
v2, D-U1, D-U2, D-U2b).
> Two route groups change: uniform-FP8 decode and Top-K select. Cake
knock-outs on the 12 uniform-FP8 q8 decode rows give these shares.
> D-U1: 4.0–5.8 % on B200 and 4.9–6.2 % on GB300 (share = 1 / knock-out
ratio − 1). D-U2: 2.3–2.6 % on the b128 rows on B200 and 2.6–3.0 % on
GB300.
> Against its base, S2 makes the streaming Top-K t64 rows **1.1339 /
1.1398×** faster on B200 and **1.1292 / 1.1355×** faster on GB300.
> Against its base, tradix v2 makes the radix t256 rows **1.1207 /
1.1230×** faster on B200 (t1024 1.0276 / 1.0285, t2 1.0358). On GB300 it
reads t8 1.075 / 1.082 and t256 1.072 / 1.069.
> No lever changes the arithmetic. Outputs and Top-K indices are bitwise
identical in every Cake A/B listed under "Precision".
> The exporter now delivers `topk_select` per architecture. Prefill
routes do not change. This is one commit directly on `main` `fb83b0ee`
and is not stacked.

## Summary

This PR regenerates the Cake-generated MiniMax Sparse Attention family
for SM100 / SM103. The family is in `csrc/blackwell_msa/`,
`flashinfer/jit/blackwell_msa.py` and
`flashinfer/msa_ops/_blackwell_sm100.py`. This commit changes the first
two; the host file `_blackwell_sm100.py` is regenerated byte-identical
to `main`.

- **Source.** Cake producer `951efcee1df5abcc98674c59ca2e4239e3649377`
(CAKE-1183 MSA ceiling round 10; exporter branch
`averyh/msa-ceiling-mr-export-topk-perarch`). Its kernel texts are the
same as the wave-4 code head `0585a6d479316c18659c144e81b47f1b111e123d`.
That head contains the levers of Cake MRs !1439 (wave 2), !1444 (wave 3)
and !1445 (wave 4).
- **Target.** One commit directly on FlashInfer `main`
`fb83b0ee9d41df4e24fb0b2ce1e671accadcef85`. It does not stack on another
open PR. `main` already contains #6443 (decode round 8), #6459 (Top-K
round 9) and #6463 (prefill round 9).
- **Routes.** 46 uniform-FP8 decode routes and 11 Top-K routes change.
The 59 prefill routes, the other 54 decode routes and the other 5 Top-K
routes are identical.
- **Exporter.** The exporter now traces `topk_select` per architecture,
so sm_100a gets its own unpadded layout.
- **Precision.** The Cake A/Bs of all delivered levers are bitwise. The
Cake MRs record no change to dtype, tolerance, selected-block set or
public signature.
- **Validation.** GB300 export leg: 88 / 88 shapes are correct, 78 pass
all gates and 10 fail timing gates only. The B200 leg, pair compare,
B200 tests and pre-commit results are under "Validation".

## What changed

### Route changes

These are the changes in the export protocol's route diff against the
round-9 prefill protocol.

| route group / program | lever (Cake MR) | mechanism (details below) |
launch SMEM, bytes |
|---|---|---|---|
| uniform-FP8 decode (46 routes) | D-U1, D-U2, D-U2b (!1445) | The item
epilogue overlaps the next item's first QK. QK(pair+1) issues before
PV(pair), with P in two SMEM tiles and a `p_free` barrier. Correction
waits on `p_free` before each TMEM rescale. | `dynamic_smem_bytes`
183296 → 216064 (the two P tiles of D-U2) |
| Top-K streaming `topk_select_streaming` | S2 (!1439) | A warp-local
bitonic top-16 merge replaces 16 CTA-wide argmax rounds. | 33024 → 33792
|
| Top-K radix `topk_select` | tradix v2 (!1439) + exporter change |
Bank-disjoint segment visits. Padded strides on sm_103a only. One
program per architecture. | sm_100a 75520 (unpadded); sm_103a 75520 →
75648 |
| Top-K radix `topk_select_keq` | tradix v2 (!1439) | Bank-disjoint
segment visits and padded strides. | 75520 → 75648 (both architectures)
|
| Top-K radix `topk_select_q32` | tradix v2 (!1439) | Bank-disjoint
segment visits, padded strides and rank index `q_local + 16·w`. | 85376
→ 85632 |
| prefill (59 routes) | — | unchanged | unchanged |

### Mechanisms

**D-U1: the epilogue overlaps the next item's first QK.** Before this
change, the MMA warp committed `o_full` for item k. It then waited for
correction's `decode_done` before it issued work for item k+1. The
tensor pipe and the softmax warps were idle during the epilogue. Now the
wait sits between item k+1's QK(0)/QK(1) and its first PV. Only the last
item of a CTA keeps the end-of-item wait. The overlap is safe because
the epilogue reads only `output0/1`. QK writes `scores0/1`, and
correction does not read them. The end-of-item `row_sum` / `row_max`
publish uses a new `softmax_done` barrier. No touched barrier gets more
than one phase ahead. ptxas: 128 registers and 0 spill on both
architectures. The change adds 2 mbarriers.

**D-U2: QK runs ahead of PV, with P in SMEM.** Before this change, P
aliased part of the FP32 score tile in TMEM. QK(pair+1) would overwrite
P(pair), so PV(pair) had to issue first. Now softmax writes P as E4M3
into two 128B-swizzled K-major SMEM tiles. It no longer stores P into
TMEM. A new `p_free` barrier protects the tiles. The MMA warp issues
QK(pair+1) before PV(pair), so the next softmax step overlaps PV(pair).
PV reads its A operand from SMEM in one K=128 issue instead of two TMEM
issues.

**D-U2b: correction waits on `p_free` before each rescale.** A
`tcgen05.commit` arrives only after all earlier tcgen05 operations of
the issuing thread have completed. In the original order, `s_full(p)`
therefore also meant "PV(s, p−1) is done". QK-ahead order commits
`s_full[s]` before PV(s, pair), which removes that implicit edge.
Correction could then rescale `output_s` in TMEM while PV(s, p−1) was
still accumulating into the same columns. D-U2b makes the stage-s
correction warps wait on `p_free[s]` before the rescale of pair >= 1.
The 4-stage KV ring (sm_100a) exposes the race; with the 8-stage ring
(sm_103a) timing hides it and Cake never observed it there, but the
sm_103a text carried the same latent race, so D-U2b is in both texts.
compute-sanitizer does not report this race: synccheck sees an intact
mbarrier protocol, and racecheck does not instrument TMEM. The evidence
for the fix is a set of bitwise probes. B200 `0aab69bb` is deterministic
over 5 launches and bitwise identical to the shipped-order text. GB300
`b27a85c6` shows all 4 variants deterministic and bitwise identical.

**S2: streaming Top-K16 merge network.** Before this change, the
streaming program ran 16 rounds of CTA-wide argmax. Each round needed a
warp reduce, a publish, one CTA barrier and a warp-0 second-level reduce
(#6459's C1-S had already removed the second per-round barrier). Now
each of the 8 warps selects its local top-16 with a bitonic network
(`_merge_warp_top16`). Each warp publishes 16 (score, index) pairs. Warp
0 merges the 8 × 16 candidates with the same network and writes the 16
indices. Ties break by index, the same as in the reference. Per CTA,
dynamic barriers drop from 19 to 2 and static barriers drop from 5 to 2.

**Tradix v2: radix select layout (C2-R-A(d) + C2-R-B).** An ncu probe
attributed part of `sm__cycles_elapsed` to shared-memory bank conflicts:
9.35 / 9.54 % on keq t256 and 4.62 / 4.36 % on q32 t1024 (B200 / GB300).

- **A(d)** visits the odd segments as `j ^ (seg & 1)`. The two
half-warps no longer alias banks. A(d) adds no SMEM and no hot-loop
instructions.
- **B** pads the candidate stride from 64 to 65 u64 and the output-count
stride from 16 to 17. It also remaps the q32 rank index to `q_local +
16·w`.
- **v2 applies B per instance and per architecture.** On sm_100a, the
stage-only k64 `topk_select` instance keeps the unpadded stride. With
the padding (v1), that row lost on sm_100a: t3 h2 k64 read 0.9765 and
0.9611 on re-measurement. With v2 it reads 0.9966 PARITY. On sm_103a,
the v2 text is the same as v1 `45511dac`.
- **Register note.** On sm_100a, `topk_select_keq` compiles to 127
registers (base 75, 0 spill). Its production shapes go from 3 to 2
CTAs/SM. Cake accepted this on the measured A/B, because no row
regresses beyond the band on either architecture.

### Exporter change: per-architecture `topk_select`

This is a change to the exporter, not a kernel change. Before, the
exporter traced the module-level Top-K instance once and delivered one
text to both architectures. Up to the round-9 deliveries (#6459 / #6463)
this did not matter: the Top-K layout did not depend on the
architecture, and `main` `fb83b0ee` serves every Top-K program,
`topk_select` included, with `arches` `["sm_100a", "sm_103a"]` and
`dynamic_smem_bytes` 75520 on both; its only per-architecture pair is
the uniform-FP8 decode program, whose kernels differ. Tradix v2 (this
delivery) pads the `topk_select` layout on sm_103a only (75648) and
keeps sm_100a unpadded (75520). With one traced text, the export host
would have chosen the layout for both targets.

Now `_build("topk", arch)` traces the instance per architecture. The
engine declares `ARCH_LAYOUT_TEMPLATES = ("topk_select",)` and emits two
`topk_select` programs:

- `cake_blackwell_msa_c14b5fe5d3aa9f47ab07`, arches [sm_100a];
- `cake_blackwell_msa_f35ca4f807d8df7077ed`, arches [sm_103a].

`topk_select_keq` and `topk_select_q32` stay one program for both
architectures. The FlashInfer loader already supports per-target
programs (`MODULES[name]["arches"]`, nested `ROUTES[target][key]`). The
loader does not change.

### Not in this PR: NVFP4 decode levers of the same producer

The producer also contains three NVFP4 decode levers (N9a-2 in !1439; C2
short-epilogue and N8a v2 in !1444). The NVFP4 decode family is exported
separately (`exports/msa_nvfp4_decode`) and is outside this family's
denominator. No NVFP4 program is in the delivered files
(`flashinfer/jit/blackwell_msa.py` has no `nvfp4` entry).

### Files

Dev worktree against `fb83b0ee` after both legs, the FI test runs and
the pre-commit restore: `git diff` shows 14 files, +227 / −14,797 (12
deleted, 2 modified) plus 14 untracked new files, 28 status lines in
total. Commit stat (this PR, `b157c343` on `fb83b0ee`): 17 files
changed, +6,936 / −1,940 with git rename detection (11 renamed kernel
files, 3 added, 1 deleted, 2 modified); all paths are under
`csrc/blackwell_msa/` (27) plus `flashinfer/jit/blackwell_msa.py`.
`flashinfer/msa_ops/_blackwell_sm100.py` is delivered verbatim and is
byte-identical to `main`, so it does not appear in the diff; no
`csrc/cake_device_helpers` file changes (helpers new = 0, modified = 0).

## Precision

The delivered levers change scheduling, barrier placement, SMEM layout
or the location of P. They do not change the arithmetic. The Cake A/Bs
compare the output SHA-256 of both arms.

- **S2:** bitwise 8/8 per architecture, against the frozen baseline
`08e48b26` and against its lane base. Top-K indices are the same as the
exact reference (`topk_v2_check`: 98 / 98 exact cases).
- **Tradix v2:** bitwise 10/10 in each of its two A/Bs per architecture.
On sm_103a the v2 text is the same as v1 (equivalence A/B `4cf831fb`,
bitwise 10/10).
- **D-U1:** bitwise 3/3 rows per architecture in the lane A/B and 14/14
in the closure A/Bs.
- **D-U2 + D-U2b:** bitwise in four A/Bs:
  - 12/12 in the sm_103a lane A/B;
  - 14/14 in the sm_103a closure A/B `51e44d45`;
  - 14/14 in the sm_100a head-vs-head A/B `45db447c`;
  - 14/14 in the sm_100a final-head closure A/B `9c8e75c7`.

The B200 and GB300 probes on `59028e26` are bitwise identical to the
shipped-order text (qka0_s4).
- **First D-U2 text (history).** The first D-U2 text, without D-U2b,
failed correctness on sm_100a. Lane A/B `341873d9` / `ccc3657b` read
0/12 bitwise, and 6/12 rows failed the FP8 contract check. Cake served
it off on sm_100a (`eafc1b2e`). D-U2b fixed it before `0585a6d4` turned
it on for sm_100a. The delivered text contains D-U2b on both
architectures.
The levers make no change to dtype, tolerance, selected-block set or
public signature. The export protocol's correctness check against the
FP32 reference passes on all 88 GB300 shapes.

## Performance (Cake A/B, numbers from the Cake MRs)

Protocol: Cake `tools/msa_rebench`, with the baseline and candidate arms
in the same job. Timing uses CUPTI with a cold L2, 11 × 5 samples and
two interleaved passes. The band has a floor of 0.02. Ratio = baseline
median / candidate median.

The frozen baseline `08e48b26` is the generator state of #6315. A
knock-out (KO) runs the same tree with one lever off in the candidate
arm. A KO ratio below 1 therefore measures that lever's share. "Lane
base" is the tree the lever was developed on.

| lever, rows | B200 (sm_100a) | GB300 (sm_103a) |
|---|---|---|
| D-U1 + D-U2 + D-U2b, 14-row FP8 decode set, vs `08e48b26` | final head
`0585a6d4`, A/B `02fe1f7a` → absum `9c8e75c7`: **14/14 WIN**; b32
1.0530–1.0555 (81.9 → 77.6 µs), b64 1.0740–1.0767 (156.5 → 145.5), b128
1.0817–1.0890 (302.5 → 278.9) | tree `59028e26` (same served text), A/B
`51e44d45` / absum `b8f0d2c9`: **14/14 WIN**; b32 1.1481–1.1528 (72.0 →
62.6 µs), b64 1.1353–1.1378 (136.0 → 119.6), b128 1.1360–1.1370 (256.7 →
225.9) |
| KO D-U1, 12 q8 rows | `0044b41f` → `74dc5f82`: LOSS 0.9450–0.9620 with
D-U1 off (share 4.0–5.8 %) | `ab_r10w4fkou1_sm_103a.json`: 0.9413–0.9530
(share 4.9–6.2 %) |
| KO D-U2, 12 q8 rows | `63c7f1ef` → `d34b0067`: b128 ×4 LOSS
0.9751–0.9776 (share 2.3–2.6 %); b64 PARITY 0.9825–0.9876; b32 PARITY
0.9878–0.9952 | `ab_r10w4fkou2_sm_103a.json`: 0.9706–0.9743 (share
2.6–3.0 %) |
| S2, 8 Top-K rows, vs lane base `ca24c86c` | absum `a9e547b9`: t64
**1.1339 / 1.1398** (10.16 → 8.96 / 10.18 → 8.93 µs); 6 control rows
PARITY 0.9967–1.0044 | absum `fe434133`: t64 **1.1292 / 1.1355** (9.79 →
8.67 / 9.79 → 8.62 µs, two-pass means); 6 control rows PARITY
0.9964–1.0021 |
| S2, vs `08e48b26` | absum `50874e7c`: DEV_WIN 7 / PARITY 1 / LOSS 0;
t64 1.5882 / 1.5972 | absum `779e7a76`: DEV_WIN 7 / PARITY 1 / LOSS 0;
t64 1.5804 / 1.5852 |
| tradix v2, 10 Top-K rows, vs lane base `809c79b5` | absum `c3e26987`:
DEV_WIN 5 / PARITY 5 / LOSS 0; t256 **1.1207 / 1.1230**, t2 1.0358,
t1024 1.0276 / 1.0285; t3 0.9965 PARITY | absum `3d1bb822` (v1 head
`45511dac`, byte-identical to v2 on sm_103a): DEV_WIN 7 / PARITY 3;
t1024 1.027 / 1.025, t2 1.034, t256 1.072 / 1.069, t8 1.075 / 1.082 |
| tradix v2, vs `08e48b26` | absum `4077caee`: DEV_WIN 7 / PARITY 3 /
LOSS 0; t3 h2 k64 0.9966 PARITY | v1 `45511dac` absum `337b2ad8`:
DEV_WIN 7 / PARITY 3 / LOSS 0; v2 vs v1 `4cf831fb`: PARITY 10
(0.9953–1.0092) |

The 14-row FP8 decode set also holds 2 legacy q1 rows. Their gains come
from decode levers that were already in the Cake stack, not from D-U1 /
D-U2. On B200, the D-U2 gain is measurable on the b128 rows only.
Head-vs-head `45db447c` / `35b46224` reads WIN 1.0210–1.0230 on the b128
kv16K / 32K / 64K rows (the b128 kv8192 row 1.0187 PARITY) and PARITY on
the other 11 rows.

## Validation

### Export protocol

- **Protocol.** `blackwell_msa.protocol.r10exp3-951efcee1df5.json`
(sha256 `9c61d88c9df3b883`, 663,700 B): 175 shapes (B200 87 / GB300 88),
175 routes and 10 templates. The definition is
`blackwell_msa_contract51_customer_m323_serving_m34_final132_coverage9`,
the same as round 9.
- **Freezes.** NSC `24faaec3` (0 GPU, producer checkout `951efcee`,
dirty_tracked=0; denominator 175 shapes / 175 routes / 10 templates).
Review against the previous producer's protocol (`8387d4f5`; its own
freezes NSC `0eabe3d4` / JHB `0de19af0` and review `16f5575f` passed):
PASS (step `a517c484`, NSC, 0 GPU): provenance 2 leaf diffs only
(`export_py` path, `producer_revision` `8387d4f5` → `951efcee`); schema
identical; shapes 175 = 175, 0 changed; routes identical by family
(decode 100 / prefill 59 / topk 16); template coverage identical.
- **Review against the round-9 prefill protocol (`803d25e1`): PASS, via
the `8387d4f5` protocol** (`protocol_review_r10exp8387_vs_r9pfx.txt`;
step `a517c484` shows this PR's protocol differs from the `8387d4f5` one
in the two provenance leaves only). `benchmark_floor_seconds`,
definition, template coverage and schema are identical. Shapes are 175 =
175 (0 added, 0 removed, 0 changed). Routes: 46 decode and 11 Top-K
changed. 54 decode, 59 prefill and 5 Top-K are identical.
- **Acceptance rule.** The protocol checks correctness against an FP32
reference, source/export timing parity and timing consistency. #6397 /
#6410 / #6443 / #6459 / #6463 accepted rows with `correctness: true`
that fail only timing-validity gates (`measurement_valid: false`). This
PR uses the same rule. The runner still exits 1 on these rows
(`ExportError: selected shape rows did not pass`).

| | B200 (sm_100a) | GB300 (sm_103a) |
|---|---|---|
| export step | `351f90d96741d901407f4ecd` (NSC 2257427, 2 GPUs,
03:55–04:26Z) | `aba1dfeee4a9f86e42a4bf26` (JHB 1015740, 2 GPUs,
03:56–04:39Z) |
| protocol shapes | 87 | 88 |
| result | completed 87 / 87, correctness 87 / 87, 76 passed; 11
timing-only rows fail a timing gate (all `correct=True`);
`source_over_export` geomean 0.9978; slop `arch_layout_clones = 1`
(`topk_select`); step exit 1 by design (ExportError on the timing-only
rows) | completed 88 / 88, correctness 88 / 88, 78 passed; 10
timing-only rows fail a timing gate (all `correct=True`);
`source_over_export` geomean 0.9994; slop `arch_layout_clones = 1`
(`topk_select`); step exit 1 by design (ExportError on the timing-only
rows) |

Timing-only non-passing rows (correctness passed on every one; the gates
`directional_disagreement` / `endpoint_drift` / `source_over_export`
compare the exported module against the Cake source arm on short shapes
(≤ 35 µs) or on the long flat-varlen prefill shapes and are accepted by
the round-9/10 precedent):
- B200 (11): topk_small_forced_clamped (directional_disagreement),
topk_tied_threshold_forced (directional_disagreement),
topk_nvp_le16_t5_h2_k64_nvp9_fb2_fe1 (source_over_export,
directional_disagreement; 0.0047 vs 0.0052 ms),
prefill_flat_bf16_gqa16_folded_tail (directional_disagreement,
endpoint_drift), prefill_flat_bf16_gqa16_ragged_batch
(directional_disagreement, endpoint_drift), prefill_fully_masked_row
(directional_disagreement),
perf_prefill_bf16_b1_q8192_kv8192_h64_hkv4_k16_flat_varlen
(endpoint_drift; 0.7576 vs 0.7616 ms),
perf_prefill_bf16_b1_q16384_kv16384_h64_hkv4_k16_flat_varlen
(endpoint_drift; 1.6884 vs 1.7008),
perf_prefill_bf16_b1_q32768_kv32768_h64_hkv4_k16_flat_varlen
(endpoint_drift; 3.5858 vs 3.6171),
perf_prefill_bf16_b2_q32768_kv32768_h64_hkv4_k16_flat_varlen
(endpoint_drift; 7.3033 vs 7.3688),
coverage_prefill_mixed_fp8_b2_q64_kv512_h8_hkv2_k16_flat
(directional_disagreement).
- GB300 (10): topk_small_forced_clamped (directional_disagreement,
endpoint_drift), topk_tied_threshold_forced (source_over_export,
directional_disagreement; 0.0054 vs 0.0057 ms), topk_large_radix_domain
(directional_disagreement), topk_nvp_le16_t5_h2_k64_nvp9_fb2_fe1
(source_over_export, directional_disagreement; 0.0047 vs 0.0049),
prefill_flat_bf16_gqa16_folded_tail (directional_disagreement),
prefill_flat_bf16_gqa16_ragged_batch (directional_disagreement),
prefill_fully_masked_row (directional_disagreement),
serving_m3_prefill_tp8_correctness_q17_kv257_h8_hkv1_k16_paged_bf16
(directional_disagreement),
coverage_prefill_mixed_fp8_b2_q64_kv512_h8_hkv2_k16_flat
(directional_disagreement),
coverage_prefill_bf16_b2_q64_kv512_h16_hkv1_k16_paged_noncausal
(directional_disagreement).

**Module census.** `flashinfer/jit/blackwell_msa.py` now lists 32
programs: 28 serve both architectures, 2 are sm_100a-only and 2 are
sm_103a-only. The two per-architecture pairs are the declared
`topk_select` layout pair (`cake_blackwell_msa_c14b5fe5d3aa9f47ab07`
[sm_100a] / `cake_blackwell_msa_f35ca4f807d8df7077ed` [sm_103a];
`slop.json` has exactly this 1 `arch_layout_clones` entry, kernel
`kernel_minimax_sparse_topk_select_sm100`) and the
`uniform_fp8_direct_decode` pair, whose kernels differ per architecture
(KV ring depth 4 on sm_100a, 8 on sm_103a). The exporter log reports
`[arch_layout_clone]` for `topk_select` and `[arch_fold_unpaired]` for
`topk_select`, `uniform_fp8_direct_decode` ("kernels differ"),
`union_prefill_m128` and `long_bf16_reverse_combine`; the last two did
not produce extra per-architecture programs.

**PAIR_IDENTICAL** (byte compare of the B200 and GB300 deliveries):
delivered files NSC 101 = JHB 101, identical 101, differing 0,
only-on-one-side 0; `removed_files` equal; both records `target_revision
= fb83b0ee9d41…` (`export_pair_compare.sh msa-rebench-expr10exp3-b200
msa-rebench-expr10exp3-gb300`, 04:40Z)

### Repository tests

Command: `pytest tests/msa_ops tests/jit/test_blackwell_msa_jit.py`, run
on the dev worktree (`fb83b0ee` + this delivery).

- GB300: `394 passed, 155 skipped, 21 warnings in 68.70s` (`pytest
tests/msa_ops tests/jit/test_blackwell_msa_jit.py`, step
`fd8982998d902f0ede42553c`, JHB 1015740, 1 GPU, exit 0; log
`$R/results/msa-rebench-fitests-r10exp3-gb300/pytest.log`)
- B200: `394 passed, 155 skipped, 21 warnings` (`pytest tests/msa_ops
tests/jit/test_blackwell_msa_jit.py`, step `65193f2cd78e1eb47f5e952f`,
NSC 2257427, 1 GPU, exit 0; log
`$R/results/msa-rebench-fitests-r10exp3-b200/pytest.log`)

### Pre-commit

`pre-commit run --all-files` with the repository configuration (ruff
0.12.8 check and format): PASS — `ruff check` 0 findings, `ruff format`
0 changes, all 15 hooks passed (including the CRLF remover,
clang-format, mypy, ruff check, ruff check SM12x import order, ruff
format and the experimental test scope selftest), `hook_modified = 0`,
`deleted_resurrected = 0` (step `ad6b1179bc402201488ed232`, NSC 2257427,
0 GPU, ruff 0.12.8, `pre-commit run --all-files` with the 16 delivered
paths (2 modified + 14 new) staged, 17 paths staged in total; log
`$R/results/msa-rebench-fiprecommit2-r10exp3-b200/`)

The first re-export from producer `8387d4f5` failed this gate (NSC step
`329d74018be3fa67250e049a`): `ruff check` reported B905 on three `zip()`
calls of `flashinfer/msa_ops/_blackwell_sm100.py` and `ruff format`
wanted to re-wrap nine over-long statements in `_prefill_union_census`
and the long-prefill work-splitting helpers (prefill rounds 7–9 host
code that is already on FlashInfer `main`; the lines exceed FlashInfer's
88 columns). FlashInfer `main` already carried `strict=False` on those
calls (a hand fix in the round-9 PR branch that never reached the Cake
template). Cake commit `951efcee` ports the hook's own autofix and the
`strict=False` arguments into the exporter template, and this PR is the
re-export from that producer. All other hooks (mypy, clang-format, the
SM12x import-order check, the test-scope self-test) passed on the first
re-export as well.

## Known items inherited from main

### CAKE-1132 Part B rows are not in the denominator

Cake main commit `681d272c` (CAKE-1132 Part B) appended 79 speculative
sparse-decode rows to the contract's canonical list. The exporter
already skipped 67 of them (NVFP4). The other 12 rows per architecture
(`cake1132_*`) use vocabulary that the FlashInfer host mirror does not
implement: `use_cache_hit_arms`, `packed_kv_256`, identity global scales
and `perf_gate_cake_1132`.

The first legs ran on a 199-shape protocol that included these rows:
`blackwell_msa.protocol.r10exp-35699cfe1c3d.json`, with B200 99 / GB300
100. All 12 rows failed on both legs with `NotImplementedError: global
K/V scales require uniform FP8 Q/K/V decode`. The host mirror
`backend_sm100.py::_validate_scale_arguments` raises this error; the
same guard is already in the mirror on Cake `main`, and the Cake
production dispatcher rejects these rows with its own
`NotImplementedError` ("global K/V scales require uniform FP8 Q/K/V or
NVFP4 KV decode"). First-leg results:

- B200 `ab5db70b`: completed 99 / passed 77.
- GB300 `ee2f1136`: completed 100 / passed 78.

Cake commit `8387d4f5` skips these rows by vocabulary, not by name:
`CAKE1132_PART_B_KEYS = {use_cache_hit_arms, perf_gate_cake_1132}` in
`_rows()`. The CPU test is
`loom/tests/export/test_blackwell_msa_export_denominator.py`. The
denominator is again the 175 round-9 shapes. The FlashInfer counterpart
of these rows belongs to the CAKE-1132 delivery.

### fp8mma 0.06 rel-L2 row

The Cake NVFP4 decode A/B sets contain
`nvfp4_decode_qfp8kvnvfp4_paged_b128_q1_kv8192_hq16_hkv1` (fp8mma
route). This row reads rel-L2 0.0753 against the harness row line of
0.06. It fails on the baseline arm too. The contract tolerance of 0.15
passes. The item has not changed since round 9. Under the recorded
ruling, Cake judges candidates against the baseline: "<= baseline x 1.02
and within contract tolerance".

## Stacking and provenance

- **Not stacked.** Commit `b157c34386d38ac21cdc02c143f136a344a25dee`
sits directly on `main` `fb83b0ee9d41df4e24fb0b2ce1e671accadcef85`.
Branch `cake/blackwell-msa-r10-cake1183-20261015` on fork
`yyihuang/flashinfer`.
- **Producer.** The protocol and the provenance record Cake producer
`951efcee1df5abcc98674c59ca2e4239e3649377`, the head of branch
`averyh/msa-ceiling-mr-export-topk-perarch` (Cake exporter MR
[!1453](https://gitlab-master.nvidia.com/averyh/r94494673bb0150eeffa896f7/-/merge_requests/1453)).
Its base is the wave-4 MR !1445 head `abafc332`.
- **Producer is the branch head.** `951efcee` = `8387d4f5` (first
re-export producer) + `9b1130e4` (review edits, docs and tests) +
`bbd17ff0` (CHANGELOG) + `951efcee` (host template pre-commit fix). None
of these change a generated kernel text; the only delivered-text
difference against the `8387d4f5` export is the host file formatting and
the three `strict=False` arguments.
- **Earlier producers.** `35699cfe` (first legs, target pin) →
`8387d4f5` (+ CAKE-1132 Part B denominator exclusion; second legs) →
`951efcee` (+ template pre-commit fix; this PR).
- **Kernel texts.** The kernel texts are the wave-4 code head
`0585a6d479316c18659c144e81b47f1b111e123d`. `abafc332` adds two
docs-only commits to it. `git diff --stat abafc332c96..35699cfe` touches
no kernel example. The exporter branch adds only exporter, engine, test
and doc changes and the target pin.
- **Cake MR chain.** !1445 (`abafc332`, wave 4: D-U1, D-U2, D-U2b) →
!1444 (`3a888dc9`, wave 3: C2 short-epi, N8a v2) → !1439 (`80a78e60`,
wave 2: S2, tradix v2, N9a-2) → Cake main.
- **Frozen A/B baseline.** `08e48b26`, the generator state of #6315.
- **Linear:** CAKE-1183.

## Reproduce

- **Export.** From Cake `951efcee1df5abcc98674c59ca2e4239e3649377`, run
`tools/export-generated-programs protocol
exports/blackwell_msa/export.py <fresh FlashInfer worktree at
fb83b0ee9d41df4e24fb0b2ce1e671accadcef85> --output <protocol.json>`,
then `tools/export-generated-programs run
exports/blackwell_msa/export.py <worktree> --protocol <protocol.json>
--devices 0,1 --max-wall-minutes 80 --json` with `--shape <name>` for
the protocol shapes whose `arch` matches the node (sm_100a: B200, 87
shapes, step `351f90d96741d901407f4ecd`; sm_103a: GB300, 88 shapes, step
`aba1dfeee4a9f86e42a4bf26`). Use protocol
`blackwell_msa.protocol.r10exp3-951efcee1df5.json` (sha256
`9c61d88c9df3b883`; frozen from `951efcee`, NSC step `24faaec3`). The
runner exits 1 when a row fails a timing gate. Make sure every row has
`correctness: true`.
- **Pair compare.** Run `export_pair_compare.sh` on the B200 and GB300
runs.
- **Tests.** `pytest tests/msa_ops tests/jit/test_blackwell_msa_jit.py`
- **Pre-commit.** `pre-commit run --all-files`

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Performance**
* Updated Blackwell MSA attention kernels with revised probability
buffering and synchronization, plus adjusted top-k selection and
histogram processing.
* Updated kernel launch configurations and routing for supported
Blackwell variants.
* **Compatibility**
* Removed an older page-selection kernel; its functionality is no longer
available through that implementation.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [0504102](https://github.com/flashinfer-ai/flashinfer/commit/05041022c3b283ca49c93316b628d4179fe8a962)

- **作者**: Yanqin Zhai
- **时间**: 2026-10-17T17:58:58Z
- **提交信息**: update-blackwell-magemoe-heuristics (#6612)

<!-- .github/pull_request_template.md -->

## 📌 Description

Add workload-aware heuristics, collective `knobs="auto"` tuning, and an
offline tuning cache to Blackwell GenPhase, adapted from \#6575.
GenPhase remains opt-in.

Performance on **4×B300, EP4, unlocked clocks**, MXFP8 W8A8/BF16 output,
H4096/I1024/E256/top-k8, capacity 1024:

| Active tokens/rank | Post-\#6565 default (µs) | New heuristics (µs) |
Reduction |
|---:|---:|---:|---:|
| 1 | 53\.81 | 47\.53 | 11\.7% |
| 64 | 217\.61 | 174\.63 | 19\.7% |
| 1024 | 273\.18 | 252\.05 | 7\.7% |

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
- [ ] All tests are passing (`unittest`, etc.).

Targeted validation on follow-up `29c4022d` (Torch 2.13.0+cu130, CuTe
DSL 4.7.1):

- 101 host workspace/tuning/cache tests passed. The new cache-identity
regression first reproduced four failures on `d71679f5` (SM100/SM103,
unset or bare native target), then passed all six cases after the fix.
- Five invalid benchmark `--active` inputs exit with an argument error
before CUDA imports; scoped pre-commit passed for all five follow-up
files.
- B200 EP2 and EP4 on the exact follow-up commit: 18 native graph cases
and one public auto/cache/graph test passed per rank, including all 12
candidates, delayed rank-0 cache publication, stable I/O pointers,
alternate geometry, and empty/masked/restored routes across graph
replay.

The full repository suite has not been run locally. These
cache/validation fixes add no new kernel performance claim; the
performance table above measures the configuration-selection change.


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

Native compiler targets now have the same cache key before and after the
first workspace initializes CuTe DSL. The cache keeps the v3
implementation revision, compiler-options isolation and explicit-target
validation. The multirank test delays rank 0's cache write and verifies
every rank can resolve the winner immediately after collective tuning
returns. The raw kernels and candidate domain are unchanged by this
follow-up.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added automatic GenPhase performance selection for supported Blackwell
MXFP8 workloads, using cached tuning results when available and
workload-based estimates otherwise.
* Added warmup-time tuning and reuse of selected settings for matching
workloads. Explicit performance settings can constrain the available
choices.
  * Expanded offline tuning support to eligible SM100 MXFP8 workloads.
* **Documentation**
* Updated guidance on performance selection, tuning, and workspace
behavior.
* **Testing**
* Added coverage for automatic selection, cache reuse, multi-rank
behavior, and CUDA graph replay.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yang Xu <yanxu@nvidia.com>

### [0405452](https://github.com/flashinfer-ai/flashinfer/commit/04054522fe3fd7a520714283075731aa80dc3cdf)

- **作者**: Zihao Ye
- **时间**: 2026-10-17T10:50:38Z
- **提交信息**: feat(cake_mla): experimental Cake dense NVFP4 MLA decode for the NVFP4 paged latent cache (SM100a/SM103a, CUDA 13.4) (#6242)

## 📌 Description

Experimental Cake backend for **dense absorbed-MLA decode over the NVFP4
paged latent cache** written by #4676 (`ckv_cache` uint8 `[pages,
page_size, 256]` packed E2M1, `ckv_sf_cache` float8_e4m3fn `[pages,
page_size, 32]` block-16 scales, `kpe_cache` float8_e4m3fn `[pages,
page_size, 64]` rope), answering #4644 under the Cake tracker #4254.

New experimental APIs in `flashinfer.mla`
(`@flashinfer_experimental_api`, thin entry points):

- `cake_mla_nvfp4_paged_decode(...)` and
`prepare_cake_mla_nvfp4_paged_decode(...)`: Kimi-K3 / DeepSeek-V3
geometry (512 latent + 64 rope per key, 512-wide value), NVFP4 query
(`q_nope` / `q_sf` / `q_rope` + per-row FP32 `q_scale`), dense `[B,
q_len, H, .]` or packed variable-length `[total_q, H, .]` queries
(`cum_seq_lens_q` / `max_q_len`, bottom-right causal), 6..128 heads,
page sizes that are powers of two from 32, BF16 output, optional
natural-log LSE, decode context parallelism (`cp_world` / `cp_rank` /
`kv_len_global`), and a CUDA-Graph replayable launch-only runner. The
caller owns every buffer the call writes (`out`, `lse`, the workspace):
nothing is allocated per call.
- `quantize_mla_nvfp4_query(...)`: BF16 `[.., 576]` query to the four
NVFP4 operands (`q_scale = max(amax(nope)/(6·448),
amax(rope)·kpe_scale/(448·ckv_scale))`, so the rope product lands in the
latent logit unit), written into caller-owned buffers carved from one
uint8 workspace (`cake_backend.mla_nvfp4_query_buffers`).

Package `flashinfer/experimental/cake_mla_nvfp4_paged_decode/`:
generated CUDA for seven programs, one source per program shared by
`sm_100a` and `sm_103a`:
- four attention programs: three row-tile programs (16 / 32 / 48 packed
(token, head) rows per CTA; swapped-AB tcgen05 schedule with two
`kind::mxf4nvf4` block-scaled QK MMAs plus one `kind::f8f6f4` rope MMA,
on-chip V conversion with the hardware `QMUL4`, `kind::f8f6f4` PV) for
requests with at most 48 rows, and a two-CTA wide program (`main_wide`,
a cluster of two CTAs with `cta_group::2` MMAs: 128 rows per cluster,
the V conversion shared by the pair, M128 N256 PV) for H96 / H128 and
MTP requests with more rows;
- two split-KV merge programs: one `template <int W>` program for 1, 2
or 4 warps per row (up to 32 splits) and a CTA reducer above that;
- the query quantizer.

Registry `cake_jit.py`; host runner `cake_backend.py` (the plan — route,
row tile, split count, grids, reducer — depends only on the batch shape,
the longest KV and the device's SM count; nothing reads device tensor
contents); README with the tensor table and an example.

**Requires CUDA 13.4 or newer.** The attention programs spell the
Blackwell QMUL4 (E2M1 × E4M3 → E4M3) in PTX ISA 9.4
(`mul.rn.e4m3x4.e2m1x4.e4m3x4.satfinite`); older ptxas reject it, and
the loader refuses the attention programs below the registered
`min_cuda_version` instead of falling back to a slower emulation (the
public cvt / mul / cvt emulation measured 2.2x slower on this kernel).

### Measurements

Latency of one call of this package (µs, median of 400 samples per row:
CUPTI GPU span from the first kernel's start to the last kernel's end,
every kernel the call launches, cold L2 before each sample, CUDA-graph
replay). Page size 64; the "trace" rows use requests of `max - 64·i`
tokens.

| Shape | Heads, requests | KV tokens | KV read | Program | GB300 | B300
| GB200 | B200 |
| --- | --- | ---: | ---: | --- | ---: | ---: | ---: | ---: |
| long_split_h12_kv65536_lse | H12, 2 req | 105,536 | 37 MB | row tile
16, CTA merge | 21.0 | 21.5 | 21.6 | 22.6 |
| trace_h12_b1_q1_kv76800 | H12, 1 req | 76,800 | 27 MB | row tile 16,
CTA merge | 19.3 | 20.6 | 19.8 | 21.2 |
| trace_h12_b2_q1_kv77699 | H12, 2 req | 155,334 | 55 MB | row tile 16,
CTA merge | 23.8 | 24.8 | 24.1 | 26.4 |
| trace_h12_b4_q1_kv268800 | H12, 4 req | 1,074,816 | 378 MB | row tile
16, CTA merge | 85.3 | 86.3 | 87.5 | 86.9 |
| trace_h12_b8_q1_kv342305 | H12, 8 req | 2,736,648 | 963 MB | row tile
16, warp merge W=4 | 178.9 | 189.6 | 181.0 | 195.6 |
| trace_h12_b11_q1_kv474405 | H12, 11 req | 5,214,935 | 1,836 MB | row
tile 16, warp merge W=4 | 332.1 | 341.2 | 339.4 | 357.5 |
| mirror_h96_b1_q1_kv76800 | H96, 1 req | 76,800 | 27 MB | wide, CTA
merge | 23.1 | 25.0 | 24.5 | 25.9 |
| mirror_h96_b8_q1_kv342305 | H96, 8 req | 2,736,648 | 963 MB | wide,
warp merge W=2 | 272.6 | 286.5 | 318.3 | 330.2 |
| mtp_h12_b8_q2_kv342305 | H12, 8 req, q_len 2 | 2,736,648 | 963 MB |
row tile 32, warp merge W=4 | 201.0 | 215.9 | 213.7 | 234.8 |
| mtp_h12_b8_q4_kv342305 | H12, 8 req, q_len 4 | 2,736,648 | 963 MB |
row tile 48, warp merge W=4 | 267.1 | 288.3 | 269.6 | 296.2 |
| mtp_h12_b8_q8_kv342305 | H12, 8 req, q_len 8 | 2,736,648 | 963 MB |
wide, warp merge W=2 | 272.4 | 284.8 | 316.3 | 324.4 |
| mtp_h96_b8_q2_kv342305 | H96, 8 req, q_len 2 | 2,736,648 | 963 MB |
wide, warp merge W=2 | 532.9 | 565.1 | 631.6 | 717.2 |
| tp_h48_b8_q1_kv131072 | H48, 8 req | 1,048,576 | 369 MB | row tile 48,
warp merge W=4 | 123.5 | 132.6 | 126.3 | 136.4 |
| tp_h24_b8_q1_kv131072 | H24, 8 req | 1,048,576 | 369 MB | row tile 32,
warp merge W=4 | 94.6 | 101.7 | 102.0 | 107.1 |
| tp_h6_b16_q1_kv131072 | H6, 16 req | 2,097,152 | 738 MB | row tile 16,
warp merge W=4 | 145.4 | 149.3 | 148.7 | 153.2 |
| ctx_h12_b8_q1_kv32768 | H12, 8 req | 262,144 | 92 MB | row tile 16,
warp merge W=4 | 33.2 | 34.8 | 34.5 | 34.9 |
| ctx_h12_b4_q1_kv196608 | H12, 4 req | 786,432 | 277 MB | row tile 16,
CTA merge | 67.4 | 70.4 | 68.3 | 71.0 |
| ctx_h12_b1_q1_kv1048576 | H12, 1 req | 1,048,576 | 369 MB | row tile
16, CTA merge | 83.7 | 86.5 | 84.9 | 87.1 |
| ctx_h96_b4_q1_kv131072 | H96, 4 req | 524,288 | 185 MB | wide, warp
merge W=4 | 66.3 | 71.3 | 76.1 | 73.9 |
| deepseek_h128_b8_q1_kv32768 | H128, 8 req | 262,144 | 92 MB | wide,
warp merge W=2 | 42.9 | 44.8 | 45.7 | 45.8 |
| deepseek_h128_b32_q1_kv8192 | H128, 32 req | 262,144 | 92 MB | wide,
warp merge W=1 | 45.9 | 47.7 | 49.0 | 49.1 |
| complete_call_h12_b8_q1_kv131072 (BF16 query, quantizer in the call) |
H12, 8 req | 1,048,576 | 369 MB | row tile 16, warp merge W=4, +
quantizer | 87.0 | 88.7 | 88.5 | 89.4 |

Throughput: the memory-bound H6 / H12 decode reads the KV cache at
**4.8–5.5 TB/s** on the larger batches (`trace_h12_b8`, `trace_h12_b11`,
`tp_h6_b16`, all four GPUs), against a nominal 8 TB/s of HBM3e on these
parts. The wide program (H96 / H128, MTP q_len 8; rows with at least 4
requests) reaches up to **2.1 PFLOPS** on GB300, 2.0 on B300, 1.8 on
GB200 and 1.8 on B200 (FP4 QK, FP8 PV). Here KV read = 352 B/token × KV
tokens (the bytes the call must read; the query, outputs and page table
are small), and FLOPs = 2·(576 + 512) per key per query row.

<details>
<summary>KV-cache bandwidth and TFLOPS for every row on all four
GPUs</summary>

| Shape | GB300 TB/s | B300 TB/s | GB200 TB/s | B200 TB/s | GB300 TFLOPS
| B300 TFLOPS | GB200 TFLOPS | B200 TFLOPS |
| --- | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| long_split_h12_kv65536_lse | 1.77 | 1.73 | 1.72 | 1.64 | 131 | 128 |
127 | 122 |
| trace_h12_b1_q1_kv76800 | 1.40 | 1.31 | 1.37 | 1.28 | 104 | 97 | 101 |
95 |
| trace_h12_b2_q1_kv77699 | 2.29 | 2.20 | 2.27 | 2.07 | 170 | 164 | 168
| 153 |
| trace_h12_b4_q1_kv268800 | 4.43 | 4.38 | 4.33 | 4.35 | 329 | 325 | 321
| 323 |
| trace_h12_b8_q1_kv342305 | 5.39 | 5.08 | 5.32 | 4.92 | 399 | 377 | 395
| 365 |
| trace_h12_b11_q1_kv474405 | 5.53 | 5.38 | 5.41 | 5.13 | 410 | 399 |
401 | 381 |
| mirror_h96_b1_q1_kv76800 | 1.17 | 1.08 | 1.10 | 1.04 | 693 | 643 | 655
| 620 |
| mirror_h96_b8_q1_kv342305 | 3.53 | 3.36 | 3.03 | 2.92 | 2,097 | 1,995
| 1,796 | 1,731 |
| mtp_h12_b8_q2_kv342305 | 4.79 | 4.46 | 4.51 | 4.10 | 711 | 662 | 669 |
609 |
| mtp_h12_b8_q4_kv342305 | 3.61 | 3.34 | 3.57 | 3.25 | 1,070 | 991 |
1,060 | 965 |
| mtp_h12_b8_q8_kv342305 | 3.54 | 3.38 | 3.05 | 2.97 | 2,099 | 2,007 |
1,807 | 1,762 |
| mtp_h96_b8_q2_kv342305 | 1.81 | 1.70 | 1.53 | 1.34 | 2,146 | 2,023 |
1,810 | 1,594 |
| tp_h48_b8_q1_kv131072 | 2.99 | 2.78 | 2.92 | 2.71 | 887 | 826 | 867 |
803 |
| tp_h24_b8_q1_kv131072 | 3.90 | 3.63 | 3.62 | 3.45 | 579 | 538 | 537 |
511 |
| tp_h6_b16_q1_kv131072 | 5.08 | 4.95 | 4.97 | 4.82 | 188 | 183 | 184 |
179 |
| ctx_h12_b8_q1_kv32768 | 2.78 | 2.65 | 2.68 | 2.64 | 206 | 197 | 199 |
196 |
| ctx_h12_b4_q1_kv196608 | 4.11 | 3.93 | 4.05 | 3.90 | 305 | 292 | 301 |
289 |
| ctx_h12_b1_q1_kv1048576 | 4.41 | 4.27 | 4.35 | 4.24 | 327 | 317 | 322
| 314 |
| ctx_h96_b4_q1_kv131072 | 2.78 | 2.59 | 2.43 | 2.50 | 1,653 | 1,537 |
1,439 | 1,483 |
| deepseek_h128_b8_q1_kv32768 | 2.15 | 2.06 | 2.02 | 2.02 | 1,703 |
1,630 | 1,599 | 1,596 |
| deepseek_h128_b32_q1_kv8192 | 2.01 | 1.93 | 1.88 | 1.88 | 1,591 |
1,529 | 1,489 | 1,487 |
| complete_call_h12_b8_q1_kv131072 | 4.24 | 4.16 | 4.17 | 4.13 | 315 |
309 | 309 | 306 |

</details>

The same rows are also the export's correctness and parity check: the
Cake source (Cake launcher, NVRTC 13.4) against this package (nvcc
13.4). Every one of the 88 rows passes correctness against an FP32
reference over the decoded NVFP4 operands, and passes the performance
gate. The four runs delivered the same package, byte for byte.

| GPU | Arch | SMs | Rows passed | Source / export | Geomean |
| --- | --- | ---: | ---: | --- | ---: |
| NVIDIA GB300 | sm_103a | 152 | 22 / 22 | 0.997 – 1.032 | 1.004 |
| NVIDIA B300 SXM6 AC | sm_103a | 148 | 22 / 22 | 0.991 – 1.037 | 1.004
|
| NVIDIA GB200 | sm_100a | 152 | 22 / 22 | 0.981 – 1.038 | 1.002 |
| NVIDIA B200 | sm_100a | 148 | 22 / 22 | 0.977 – 1.033 | 1.003 |

Over all 88 rows the geomean source / export is 1.003. The cache is 352
B/token against 576 B/token for FP8.

<details>
<summary>Full export evidence: hardware, method and all 88
rows</summary>

## Generated-program export evidence

Baseline: **Cake production launcher** at Cake revision
`35b68cf30119072d1a773522e570a18f37bce72e`.

## Hardware stages

- `sm_100a` / world size `1`: GPUs `NVIDIA B200`, capabilities `10.0`,
drivers `615.71.09`, UUIDs `GPU-8a66a624-18d0-b6e2-3a57-51f9c8ee79d5`; 6
shapes (named in the per-shape tables below).
- `sm_100a` / world size `1`: GPUs `NVIDIA GB200`, capabilities `10.0`,
drivers `580.126.20`, UUIDs `GPU-25836029-83e9-053f-2b5c-12f48910f851`;
6 shapes (named in the per-shape tables below).
- `sm_100a` / world size `1`: GPUs `NVIDIA B200`, capabilities `10.0`,
drivers `615.71.09`, UUIDs `GPU-43eb1646-5a5c-dae1-8224-2915cd8310c0`; 6
shapes (named in the per-shape tables below).
- `sm_100a` / world size `1`: GPUs `NVIDIA GB200`, capabilities `10.0`,
drivers `580.126.20`, UUIDs `GPU-20eb0152-50d7-dd47-873a-d3a208840f0e`;
6 shapes (named in the per-shape tables below).
- `sm_100a` / world size `1`: GPUs `NVIDIA B200`, capabilities `10.0`,
drivers `615.71.09`, UUIDs `GPU-b86f4c01-79e3-92e3-287a-78d01ef792fd`; 5
shapes (named in the per-shape tables below).
- `sm_100a` / world size `1`: GPUs `NVIDIA GB200`, capabilities `10.0`,
drivers `580.126.20`, UUIDs `GPU-65d92c08-be0c-8ebf-b33c-485014edc5c8`;
5 shapes (named in the per-shape tables below).
- `sm_100a` / world size `1`: GPUs `NVIDIA B200`, capabilities `10.0`,
drivers `615.71.09`, UUIDs `GPU-f6a76f64-75da-d5be-1a7c-7156bd2cff2e`; 5
shapes (named in the per-shape tables below).
- `sm_100a` / world size `1`: GPUs `NVIDIA GB200`, capabilities `10.0`,
drivers `580.126.20`, UUIDs `GPU-4c10862d-7699-7f20-a9d7-6b24ca115254`;
5 shapes (named in the per-shape tables below).
- `sm_103a` / world size `1`: GPUs `NVIDIA B300 SXM6 AC`, capabilities
`10.3`, drivers `615.71.09`, UUIDs
`GPU-9c23a1e2-80d4-6c95-0c51-2fa1e406d3d4`; 6 shapes (named in the
per-shape tables below).
- `sm_103a` / world size `1`: GPUs `NVIDIA GB300`, capabilities `10.3`,
drivers `580.159.03`, UUIDs `GPU-03f51971-a886-2f09-d649-687f664cf4c6`;
11 shapes (named in the per-shape tables below).
- `sm_103a` / world size `1`: GPUs `NVIDIA B300 SXM6 AC`, capabilities
`10.3`, drivers `615.71.09`, UUIDs
`GPU-e01f9fc6-6cfd-8a68-a589-3923731c2013`; 6 shapes (named in the
per-shape tables below).
- `sm_103a` / world size `1`: GPUs `NVIDIA GB300`, capabilities `10.3`,
drivers `580.159.03`, UUIDs `GPU-daded3bd-5473-4a2a-1d06-9c0164023ba9`;
11 shapes (named in the per-shape tables below).
- `sm_103a` / world size `1`: GPUs `NVIDIA B300 SXM6 AC`, capabilities
`10.3`, drivers `615.71.09`, UUIDs
`GPU-4f25543d-330c-dbea-c7ff-0187aa84f19a`; 5 shapes (named in the
per-shape tables below).
- `sm_103a` / world size `1`: GPUs `NVIDIA B300 SXM6 AC`, capabilities
`10.3`, drivers `615.71.09`, UUIDs
`GPU-f131b770-cf03-1a7f-38b4-3f50b3353ea1`; 5 shapes (named in the
per-shape tables below).

Target revision: `e028488f2076c66da1866c797b11ea72507ccf0a`.

Benchmark execution: `symmetric_external_cuda_graph`; 4 counterbalanced
groups, 20 warmup calls and 100 reportable calls per arm/group (fixed
counts; no sizing pilot).
Latency metric: CUPTI GPU span per sample, first compute-kernel start to
last compute-kernel end of one arm call (every kernel the call launches,
asynchronous copies excluded), after a cold-L2 flush before each
measured sample; the reported value is the per-arm median. Each row's
``sm_clock_mhz_range`` in the summary JSON is the SM clock range
observed while the row was timed (group-boundary probes and, in the
symmetric graph mode, every sampled warmup/measurement phase).
Each sample follows one unmeasured same-arm launch, state restoration,
and a fresh cold-L2 flush.

The complete semantic arguments and machine-readable receipts remain in
`summary.json`; the table below retains every registered shape without
repeating those arguments, keys routes and external baselines against
the legends that follow it, and inlines each shape's external
comparison.

## Per-shape results

|Shape|GPU|Route|Source ms|Export ms|Source / Export|Baseline|Baseline
ms|Baseline / Export|Verdict|
|---|---|---|---:|---:|---:|---|---:|---:|---|

|long_split_h12_kv65536_lse__sm_100a__sm148|G0|R1|0.023072|0.022592|1.0212x|—|—|—|pass|

|trace_h12_b1_q1_kv76800__sm_100a__sm148|G2|R1|0.021856|0.021152|1.0333x|—|—|—|pass|

|trace_h12_b2_q1_kv77699__sm_100a__sm148|G4|R1|0.025824|0.026432|0.9770x|—|—|—|pass|

|trace_h12_b4_q1_kv268800__sm_100a__sm148|G6|R1|0.087360|0.086944|1.0048x|—|—|—|pass|

|trace_h12_b8_q1_kv342305__sm_100a__sm148|G0|R5|0.197152|0.195615|1.0079x|—|—|—|pass|

|trace_h12_b11_q1_kv474405__sm_100a__sm148|G2|R5|0.360320|0.357535|1.0078x|—|—|—|pass|

|mirror_h96_b1_q1_kv76800__sm_100a__sm148|G4|R11|0.025888|0.025888|1.0000x|—|—|—|pass|

|mirror_h96_b8_q1_kv342305__sm_100a__sm148|G6|R15|0.330113|0.330178|0.9998x|—|—|—|pass|

|mtp_h12_b8_q2_kv342305__sm_100a__sm148|G0|R7|0.236448|0.234848|1.0068x|—|—|—|pass|

|mtp_h12_b8_q4_kv342305__sm_100a__sm148|G2|R9|0.296832|0.296160|1.0023x|—|—|—|pass|

|mtp_h12_b8_q8_kv342305__sm_100a__sm148|G4|R15|0.324705|0.324448|1.0008x|—|—|—|pass|

|mtp_h96_b8_q2_kv342305__sm_100a__sm148|G6|R15|0.717411|0.717187|1.0003x|—|—|—|pass|

|tp_h48_b8_q1_kv131072__sm_100a__sm148|G0|R9|0.136704|0.136352|1.0026x|—|—|—|pass|

|tp_h24_b8_q1_kv131072__sm_100a__sm148|G2|R7|0.106591|0.107072|0.9955x|—|—|—|pass|

|tp_h6_b16_q1_kv131072__sm_100a__sm148|G4|R5|0.153952|0.153248|1.0046x|—|—|—|pass|

|ctx_h12_b8_q1_kv32768__sm_100a__sm148|G6|R5|0.034944|0.034944|1.0000x|—|—|—|pass|

|ctx_h12_b4_q1_kv196608__sm_100a__sm148|G0|R1|0.071008|0.071008|1.0000x|—|—|—|pass|

|ctx_h12_b1_q1_kv1048576__sm_100a__sm148|G2|R1|0.086943|0.087135|0.9978x|—|—|—|pass|

|ctx_h96_b4_q1_kv131072__sm_100a__sm148|G4|R17|0.073760|0.073856|0.9987x|—|—|—|pass|

|deepseek_h128_b8_q1_kv32768__sm_100a__sm148|G6|R15|0.045600|0.045760|0.9965x|—|—|—|pass|

|deepseek_h128_b32_q1_kv8192__sm_100a__sm148|G0|R13|0.049216|0.049088|1.0026x|—|—|—|pass|

|complete_call_h12_b8_q1_kv131072__sm_100a__sm148|G2|R3|0.089696|0.089408|1.0032x|—|—|—|pass|

|long_split_h12_kv65536_lse__sm_100a__sm152|G1|R1|0.022464|0.021632|1.0385x|—|—|—|pass|

|trace_h12_b1_q1_kv76800__sm_100a__sm152|G3|R1|0.019392|0.019776|0.9806x|—|—|—|pass|

|trace_h12_b2_q1_kv77699__sm_100a__sm152|G5|R1|0.023904|0.024096|0.9920x|—|—|—|pass|

|trace_h12_b4_q1_kv268800__sm_100a__sm152|G7|R1|0.087521|0.087456|1.0007x|—|—|—|pass|

|trace_h12_b8_q1_kv342305__sm_100a__sm152|G1|R5|0.182304|0.180961|1.0074x|—|—|—|pass|

|trace_h12_b11_q1_kv474405__sm_100a__sm152|G3|R5|0.341825|0.339425|1.0071x|—|—|—|pass|

|mirror_h96_b1_q1_kv76800__sm_100a__sm152|G5|R11|0.024544|0.024512|1.0013x|—|—|—|pass|

|mirror_h96_b8_q1_kv342305__sm_100a__sm152|G7|R15|0.318208|0.318305|0.9997x|—|—|—|pass|

|mtp_h12_b8_q2_kv342305__sm_100a__sm152|G1|R7|0.214753|0.213728|1.0048x|—|—|—|pass|

|mtp_h12_b8_q4_kv342305__sm_100a__sm152|G3|R9|0.270369|0.269568|1.0030x|—|—|—|pass|

|mtp_h12_b8_q8_kv342305__sm_100a__sm152|G5|R15|0.316352|0.316289|1.0002x|—|—|—|pass|

|mtp_h96_b8_q2_kv342305__sm_100a__sm152|G7|R15|0.632129|0.631553|1.0009x|—|—|—|pass|

|tp_h48_b8_q1_kv131072__sm_100a__sm152|G1|R9|0.126208|0.126304|0.9992x|—|—|—|pass|

|tp_h24_b8_q1_kv131072__sm_100a__sm152|G3|R7|0.102112|0.101953|1.0016x|—|—|—|pass|

|tp_h6_b16_q1_kv131072__sm_100a__sm152|G5|R5|0.149120|0.148672|1.0030x|—|—|—|pass|

|ctx_h12_b8_q1_kv32768__sm_100a__sm152|G7|R5|0.034240|0.034464|0.9935x|—|—|—|pass|

|ctx_h12_b4_q1_kv196608__sm_100a__sm152|G1|R1|0.068960|0.068320|1.0094x|—|—|—|pass|

|ctx_h12_b1_q1_kv1048576__sm_100a__sm152|G3|R1|0.084993|0.084928|1.0008x|—|—|—|pass|

|ctx_h96_b4_q1_kv131072__sm_100a__sm152|G5|R17|0.076384|0.076096|1.0038x|—|—|—|pass|

|deepseek_h128_b8_q1_kv32768__sm_100a__sm152|G7|R15|0.045696|0.045664|1.0007x|—|—|—|pass|

|deepseek_h128_b32_q1_kv8192__sm_100a__sm152|G1|R13|0.048800|0.049024|0.9954x|—|—|—|pass|

|complete_call_h12_b8_q1_kv131072__sm_100a__sm152|G3|R3|0.088704|0.088480|1.0025x|—|—|—|pass|

|long_split_h12_kv65536_lse__sm_103a__sm148|G8|R2|0.022304|0.021504|1.0372x|—|—|—|pass|

|trace_h12_b1_q1_kv76800__sm_103a__sm148|G10|R2|0.021120|0.020576|1.0264x|—|—|—|pass|

|trace_h12_b2_q1_kv77699__sm_103a__sm148|G12|R2|0.025248|0.024800|1.0181x|—|—|—|pass|

|trace_h12_b4_q1_kv268800__sm_103a__sm148|G13|R2|0.086273|0.086305|0.9996x|—|—|—|pass|

|trace_h12_b8_q1_kv342305__sm_103a__sm148|G8|R6|0.190179|0.189635|1.0029x|—|—|—|pass|

|trace_h12_b11_q1_kv474405__sm_103a__sm148|G10|R6|0.342916|0.341220|1.0050x|—|—|—|pass|

|mirror_h96_b1_q1_kv76800__sm_103a__sm148|G12|R12|0.024896|0.024960|0.9974x|—|—|—|pass|

|mirror_h96_b8_q1_kv342305__sm_103a__sm148|G13|R16|0.286435|0.286500|0.9998x|—|—|—|pass|

|mtp_h12_b8_q2_kv342305__sm_103a__sm148|G8|R8|0.216675|0.215908|1.0036x|—|—|—|pass|

|mtp_h12_b8_q4_kv342305__sm_103a__sm148|G10|R10|0.288835|0.288292|1.0019x|—|—|—|pass|

|mtp_h12_b8_q8_kv342305__sm_103a__sm148|G12|R16|0.284836|0.284803|1.0001x|—|—|—|pass|

|mtp_h96_b8_q2_kv342305__sm_103a__sm148|G13|R16|0.565223|0.565096|1.0002x|—|—|—|pass|

|tp_h48_b8_q1_kv131072__sm_103a__sm148|G8|R10|0.132130|0.132642|0.9961x|—|—|—|pass|

|tp_h24_b8_q1_kv131072__sm_103a__sm148|G10|R8|0.102369|0.101729|1.0063x|—|—|—|pass|

|tp_h6_b16_q1_kv131072__sm_103a__sm148|G12|R6|0.149634|0.149281|1.0024x|—|—|—|pass|

|ctx_h12_b8_q1_kv32768__sm_103a__sm148|G13|R6|0.034465|0.034785|0.9908x|—|—|—|pass|

|ctx_h12_b4_q1_kv196608__sm_103a__sm148|G8|R2|0.070273|0.070401|0.9982x|—|—|—|pass|

|ctx_h12_b1_q1_kv1048576__sm_103a__sm148|G10|R2|0.086497|0.086497|1.0000x|—|—|—|pass|

|ctx_h96_b4_q1_kv131072__sm_103a__sm148|G12|R18|0.071264|0.071265|1.0000x|—|—|—|pass|

|deepseek_h128_b8_q1_kv32768__sm_103a__sm148|G13|R16|0.044705|0.044785|0.9982x|—|—|—|pass|

|deepseek_h128_b32_q1_kv8192__sm_103a__sm148|G8|R14|0.047808|0.047744|1.0013x|—|—|—|pass|

|complete_call_h12_b8_q1_kv131072__sm_103a__sm148|G10|R4|0.088898|0.088673|1.0025x|—|—|—|pass|

|long_split_h12_kv65536_lse__sm_103a__sm152|G9|R2|0.021440|0.020960|1.0229x|—|—|—|pass|

|trace_h12_b1_q1_kv76800__sm_103a__sm152|G11|R2|0.019264|0.019296|0.9983x|—|—|—|pass|

|trace_h12_b2_q1_kv77699__sm_103a__sm152|G9|R2|0.024608|0.023840|1.0322x|—|—|—|pass|

|trace_h12_b4_q1_kv268800__sm_103a__sm152|G11|R2|0.085472|0.085313|1.0019x|—|—|—|pass|

|trace_h12_b8_q1_kv342305__sm_103a__sm152|G9|R6|0.179361|0.178880|1.0027x|—|—|—|pass|

|trace_h12_b11_q1_kv474405__sm_103a__sm152|G11|R6|0.332897|0.332065|1.0025x|—|—|—|pass|

|mirror_h96_b1_q1_kv76800__sm_103a__sm152|G9|R12|0.023072|0.023136|0.9972x|—|—|—|pass|

|mirror_h96_b8_q1_kv342305__sm_103a__sm152|G11|R16|0.272577|0.272641|0.9998x|—|—|—|pass|

|mtp_h12_b8_q2_kv342305__sm_103a__sm152|G9|R8|0.201697|0.200993|1.0035x|—|—|—|pass|

|mtp_h12_b8_q4_kv342305__sm_103a__sm152|G11|R10|0.268609|0.267105|1.0056x|—|—|—|pass|

|mtp_h12_b8_q8_kv342305__sm_103a__sm152|G9|R16|0.272641|0.272417|1.0008x|—|—|—|pass|

|mtp_h96_b8_q2_kv342305__sm_103a__sm152|G11|R16|0.532993|0.532866|1.0002x|—|—|—|pass|

|tp_h48_b8_q1_kv131072__sm_103a__sm152|G9|R10|0.124768|0.123520|1.0101x|—|—|—|pass|

|tp_h24_b8_q1_kv131072__sm_103a__sm152|G11|R8|0.094624|0.094592|1.0003x|—|—|—|pass|

|tp_h6_b16_q1_kv131072__sm_103a__sm152|G9|R6|0.145889|0.145377|1.0035x|—|—|—|pass|

|ctx_h12_b8_q1_kv32768__sm_103a__sm152|G11|R6|0.033536|0.033185|1.0106x|—|—|—|pass|

|ctx_h12_b4_q1_kv196608__sm_103a__sm152|G9|R2|0.067297|0.067393|0.9986x|—|—|—|pass|

|ctx_h12_b1_q1_kv1048576__sm_103a__sm152|G11|R2|0.083488|0.083712|0.9973x|—|—|—|pass|

|ctx_h96_b4_q1_kv131072__sm_103a__sm152|G9|R18|0.066144|0.066272|0.9981x|—|—|—|pass|

|deepseek_h128_b8_q1_kv32768__sm_103a__sm152|G11|R16|0.042784|0.042881|0.9977x|—|—|—|pass|

|deepseek_h128_b32_q1_kv8192__sm_103a__sm152|G9|R14|0.045856|0.045888|0.9993x|—|—|—|pass|

|complete_call_h12_b8_q1_kv131072__sm_103a__sm152|G11|R4|0.087073|0.086976|1.0011x|—|—|—|pass|

## Route legend

|Key|Route|
|---|---|
|R1|main_rt16_reduce_cta_sm_100a|
|R2|main_rt16_reduce_cta_sm_103a|
|R3|main_rt16_reduce_w4_quantize_sm_100a|
|R4|main_rt16_reduce_w4_quantize_sm_103a|
|R5|main_rt16_reduce_w4_sm_100a|
|R6|main_rt16_reduce_w4_sm_103a|
|R7|main_rt32_reduce_w4_sm_100a|
|R8|main_rt32_reduce_w4_sm_103a|
|R9|main_rt48_reduce_w4_sm_100a|
|R10|main_rt48_reduce_w4_sm_103a|
|R11|main_wide_reduce_cta_sm_100a|
|R12|main_wide_reduce_cta_sm_103a|
|R13|main_wide_reduce_w1_sm_100a|
|R14|main_wide_reduce_w1_sm_103a|
|R15|main_wide_reduce_w2_sm_100a|
|R16|main_wide_reduce_w2_sm_103a|
|R17|main_wide_reduce_w4_sm_100a|
|R18|main_wide_reduce_w4_sm_103a|

## Baseline legend

Each shape row above inlines its applicable external baselines (paired
export ms is the shape's Export ms column); keys resolve here.

|Key|Baseline|Label|Rows|Gate|
|---|---|---|---:|---|

## Geomeans over all correct timed rows

Gate-failing performance rows remain in these geomeans; only rows
without valid correctness and timing are excluded and remain visible
above.

|Shape tag|Timed rows|Denominator|Source ms|Export ms|Source / Export|
|---|---:|---:|---:|---:|---:|
|all|88|88|0.094409|0.094112|1.003158x|
|correctness|4|4|0.022312|0.021664|1.029922x|
|perf|84|84|0.101122|0.100931|1.001901x|

Complete denominator: **true** (88/88).

All gates passed: **true** (88/88).

</details>

## 🔍 Related Issues

#4644 (request), #4676 (cache layout), #4254 (Cake tracker)

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

`tests/experimental/test_cake_mla_nvfp4_paged_decode.py`: 34 passed with
CUDA 13.4 on each of GB300, GB200, B300 and B200. They cover: an FP32
reference over the decoded operands; dense and packed variable-length
queries; LSE; DCP; page sizes 32 / 128; the single-buffer 352-byte cache
layout; the CTA reducer and the three warp-reducer instantiations (W =
1, 2, 4); caller-owned result and query buffers; the quantizer
bit-for-bit against its torch reference; CUDA-Graph replay with a
changed page table; launch allocates nothing; host plan invariants at
148, 152 and 160 SMs and the wide-route selection. The tests skip on
toolkits older than CUDA 13.4.

## 🔬 Experimental Track

- [x] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.
Tracking issue: #4644
- [x] The tracking issue names an owner, the reason for the experimental
path, and a graduation plan with a target release.
- [x] Core changes are limited to a thin entry point (signature, shared
validation, feature-gate check, backend selection, handoff).
- [x] Tests live in `tests/experimental/` and were validated on the
intended hardware; a runnable example is included.
- [x] Nothing is registered in `flashinfer/aot.py`, and no experimental
backend is reachable from `backend="auto"` without
`FLASHINFER_ALLOW_EXPERIMENTAL_AUTO_BACKENDS=1`. (Calling an
`@flashinfer_experimental_api` or naming a backend explicitly is itself
the opt-in and needs no environment variable.)
- [x] **Test scope declared below.** The experimental CI lane runs
exactly these targets, so keep them as narrow as the change allows.

```experimental-tests
tests/experimental/test_cake_mla_nvfp4_paged_decode.py
```

## Reviewer Notes

- The generated sources under `csrc/cake_mla_nvfp4_paged_decode/` are
byte-faithful exports (`.clang-format` with `DisableFormat` in that
root); regenerate them, do not edit by hand.
- The attention programs are delivered as `<program>_cu134_kernel.cu`
(QMUL4 spelled in PTX ISA 9.4); the merge and quantizer units are
toolkit-neutral.
- The warp merge for 1, 2 and 4 warps per row is one `template <int W>`
program; each instantiation was checked SASS-equivalent to the separate
program it replaces.
- Known gap: the entry points in `flashinfer/mla/_core.py` still declare
`out` as `Optional` (`cake_mla_nvfp4_paged_decode`,
`quantize_mla_nvfp4_query`), while the backend now requires the caller's
buffers and raises a `ValueError` naming them when they are missing.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [4ffa04a](https://github.com/flashinfer-ai/flashinfer/commit/4ffa04a2675e1aea57b50a9360f3d4b91a187a12)

- **作者**: Stu Cao
- **时间**: 2026-10-17T10:43:13Z
- **提交信息**: fix(nvfp4_sparse_mla_decode): ship the JIT sources in wheels (#6454)

## 📌 Description

`include-package-data = false` means a feature's `csrc/` only reaches a
wheel when it is listed under `[tool.setuptools.package-data]`. The
entry for `flashinfer.experimental.nvfp4_sparse_mla_decode` was missing,
so a non-editable install (wheel, or `pip install git+...@main`) ships
the Python but not `csrc/nvfp4_sparse_mla_decode.cu`; the first call
then fails in `gen_nvfp4_sparse_mla_decode_module` → `_source_digest`
with `FileNotFoundError` instead of compiling. Editable installs, which
is how the feature was developed and tested, are unaffected. This adds
the same `"csrc/**"` entry every neighbouring experimental feature has;
it also covers the `csrc/cake_nvfp4_sparse_mla_decode/` sources of the
`cake` backend.

Verified by building wheels from `main` (53e3168a) on the same machine:
without this line the wheel holds 5 files for the feature (all `.py`);
with it, 22, including `csrc/nvfp4_sparse_mla_decode.cu`, `.cuh`,
`_jit_binding.cu` and the 14 Cake `*_kernel.cu` / `*_binding.cu` files.
Found while running vLLM's `nvfp4_ds_mla` decode tests
(vllm-project/vllm#59342) against `pip install git+...flashinfer@main`:
all 10 native-decode cases failed with the `FileNotFoundError` above and
pass again with an editable install of the same commit.

## 🔍 Related Issues

Tracking: #5716 (DSA NVFP4 sparse MLA decode); kernel landed in #5717 /
#5970.

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
- [x] All tests are passing (`unittest`, etc.).

No test change: packaging only.
`tests/experimental/test_nvfp4_sparse_mla_decode.py` exercises the
kernel; the missing-file failure only reproduces from a built wheel,
which the wheel listing above covers.

## 🔬 Experimental Track

- [x] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.
Tracking issue: #5716
- [x] The tracking issue names an owner, the reason for the experimental
path, and a graduation plan with a target release.
- [x] Core changes are limited to a thin entry point (signature, shared
validation, feature-gate check, backend selection, handoff).
- [x] Tests live in `tests/experimental/` and were validated on the
intended hardware; a runnable example is included.
- [x] Nothing is registered in `flashinfer/aot.py`, and no experimental
backend is reachable from `backend="auto"` without
`FLASHINFER_ALLOW_EXPERIMENTAL_AUTO_BACKENDS=1`. (Calling an
`@flashinfer_experimental_api` or naming a backend explicitly is itself
the opt-in and needs no environment variable.)
- [x] **Test scope declared below.** The experimental CI lane runs
exactly these targets, so keep them as narrow as the change allows.

```experimental-tests
tests/experimental/test_nvfp4_sparse_mla_decode.py
```

## Reviewer Notes

One line in `pyproject.toml`. AI assistance (Claude) was used to track
the failure down and draft this; I reviewed the change.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **Improvements**
- Package distributions now include the source assets needed by the
NVFP4 sparse MLA decode component. These assets are available when the
package is installed, improving the completeness of installed
distributions. This packaging update does not change the component’s
behavior or public interface.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: Stu Cao <stu@primeintellect.ai>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-10-18
**监控日期**: 2026-10-17
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4613
- **最后更新**: 2026-10-17T12:56:10Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-10-18
**监控日期**: 2026-10-17
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34747
- **最后更新**: 2026-10-17T22:43:04Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-10-18
**监控日期**: 2026-10-17
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


**报告日期**: 2026-10-18
**监控日期**: 2026-10-17
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13256
- **最后更新**: 2026-10-17T16:55:56Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-10-18
**监控日期**: 2026-10-17
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 37256
- **最后更新**: 2026-10-17T23:06:30Z

## 提交统计

- **昨日提交总数**: 30
- **提交者数量**: 15
- **主要提交者**: 内緒, SuperSong, YAMY

## AI分析总结

## sgl-project/sglang 昨日提交分析总结

### 1. 主要更新类型分布

- **Bug修复**：约12项，占比最高，集中在DeepSeek-V4.1、扩散模型和unified-cache模块
- **性能优化**：约8项，涉及NVIDIA GPU、AMD ROCm、分布式通信等
- **功能新增**：约7项，包括扩散模型新特性、Rust前端API、NPU支持
- **重构**：3项，涉及注意力策略、多模态padding、Engram分片
- **CI调整**：1项

### 2. 关键变更点及与项目方向的关系

SGLang的核心方向是"为LLM和多模态模型提供快速推理"，本次提交紧密围绕这一目标：

- **DeepSeek-V4.1深度适配**：多项修复围绕decoder SWA bounded replay、encoder折叠、prompt-logprob等机制，说明该项目正全力支持DeepSeek-V4.1这一前沿模型的生产级推理，涉及AMD和NVIDIA双平台。
- **扩散模型生态扩展**：FLUX.2/FLUX.3（Klein upsampler）、pi0.5动作批量处理、VSA-H3支持A100，表明SGLang正将推理能力从LLM扩展到图像/视频/机器人动作等扩散模型领域。
- **混合架构与统一内存管理**：hybrid SWA + Mamba在Mooncake中的支持、Mamba checkpoint修复、联合回收策略优化，体现了对新一代混合注意力架构的系统性支持。
- **推理硬件覆盖面扩大**：NPU（昇腾）、AMD ROCm、A100（sm80）、SM10x等多硬件路径的完善。

### 3. 对项目的影响和潜在意义

- **生产稳定性提升**：DeepSeek-V4.1系列大量修复（ZMQ端口、缓存误对齐、CUDA图同步竞态等）使该模型的推理更可靠，降低线上风险。
- **内存效率显著改善**：FP8 scratch保持、元数据内存削减、DLPack跳过、条件缓存复用等，直接降低显存占用并提升吞吐。
- **生态壁垒构建**：扩散模型支持（FLUX系列、pi0.5、LoRA兼容性）使SGLang成为多模态推理的统一入口，区别于纯LLM推理框架。

### 4. 值得关注的技术点

- **FlashInfer autotune for block-FP8-as-MXFP8**：解决块FP8检查点以MXFP8方式服务时的自动调优问题，对DeepSeek系模型量化推理意义重大。
- **Inkling策略隔离与TCPCG重构**：注意力调度策略的模块化，为后续可插拔策略打基础。
- **Rust前端提供tokenize/detokenize API**：减少Python往返开销，提升API网关性能。
- **MegaAttention查询布局折叠进wq_b**：通过布局变换消除运行时开销，是零成本优化的典型。
- **扩散LoRA合并决策日志优化**：细节打磨体现工程成熟度。
- **多处Co-authored-by Claude等AI**：AI辅助开发在该项目中已成常态。

### 5. 对项目发展的影响

结合README定位（快速的LLM与多模态推理），这批提交呈现出三条清晰的发展主线：**(1) 深度绑定顶级开源模型**（DeepSeek-V4.1的系统性打磨），保持推理性能领先；**(2) 从LLM推理平台向多模态统一推理平台演进**（扩散模型模块快速迭代）；**(3) 硬件与架构多元化**（NVIDIA/AMD/NPU、混合注意力/状态空间模型）。频繁的修复与优化表明项目已进入生产成熟期，正通过稳定性、内存效率和硬件覆盖来巩固其在开源推理引擎中的竞争力。总体而言，这批提交将增强SGLang作为多模态、多硬件推理基础设施的核心地位。

## 详细提交记录

### [b234b5c](https://github.com/sgl-project/sglang/commit/b234b5c32e0d65e04a61912f85fc09e95e74a328)

- **作者**: Yuwei An
- **时间**: 2026-10-17T23:06:24Z
- **提交信息**: [Refactor] TCPCG: Consolidate attention eager regions and isolate Inkling policy (4/9) (#42288)

### [e4512a5](https://github.com/sgl-project/sglang/commit/e4512a5a17bac4a050df738e984682c88af06e56)

- **作者**: Yuwei An
- **时间**: 2026-10-17T23:05:28Z
- **提交信息**: [Perf] DSv4.1: Reduce BCG metadata memory (#44920)

### [563cd60](https://github.com/sgl-project/sglang/commit/563cd60345e0d8940b6ae04e96e638f483d69036)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-17T22:47:41Z
- **提交信息**: [Fix] [AMD] deepseek-v4.1: Reject attention DP with encoder SWA bounded replay on ROCm (#44934)

### [05ce0e9](https://github.com/sgl-project/sglang/commit/05ce0e980f00aa80864190d6f1cd5d9b685802f1)

- **作者**: Yi (Vincent) Zhong
- **时间**: 2026-10-17T21:12:00Z
- **提交信息**: [Perf] deepseek-v4.1: Skip wasted layer 20 work on earlier prompt tokens under decoder bounded replay (#42901)

### [05c1539](https://github.com/sgl-project/sglang/commit/05c15390984d80a8bb4bbc415a7653e174c27c0b)

- **作者**: Shuwen Wang
- **时间**: 2026-10-17T20:24:08Z
- **提交信息**: [Feat] unified_cache: Support hybrid SWA + Mamba models in the Mooncake direct linker (#41343)

Co-authored-by: Zhangheng <hzh0425@apache.org>
Co-authored-by: Teng Ma <sima.mt@alibaba-inc.com>

### [3b34d9f](https://github.com/sgl-project/sglang/commit/3b34d9f8b6edc23216f29c1edf02d1ff0306f9de)

- **作者**: YAMY
- **时间**: 2026-10-17T18:50:38Z
- **提交信息**: [Perf] [NVIDIA] qsa: Keep sparse decode scratch in FP8 for FP8 KV pools (#44114)

With an FP8 KV pool on SM10x, keep the packed sparse-decode K/V scratch in FP8 instead of dequantizing to BF16 (BF16-q + FP8-KV TRTLLM-gen decode). Tests cover FP8 pool -> FP8 scratch.

Co-Authored-By: Claude Opus 5.5 <noreply@anthropic.com>

### [4eb606b](https://github.com/sgl-project/sglang/commit/4eb606b2aee8a9165e16352fd4c08d998ba37990)

- **作者**: Mick
- **时间**: 2026-10-17T12:49:44Z
- **提交信息**: [Feat] diffusion: support opt-in pi0.5 completion-boundary action batching (#44634)

Co-authored-by: Jiahua Huang <35223412+dadiaokua@users.noreply.github.com>
Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [b15a78a](https://github.com/sgl-project/sglang/commit/b15a78a88191e7ac9f7685e1de50c8652f8f52b3)

- **作者**: 内緒
- **时间**: 2026-10-17T12:48:14Z
- **提交信息**: [Fix] diffusion/lora: revalidate FLUX.2 FP8/NVFP4 fast paths after LoRA attach (#40171)

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: Mick <mickjagger19@icloud.com>

### [23f8e6f](https://github.com/sgl-project/sglang/commit/23f8e6f7ec6453758ace0874b0b1af8e060d4ee0)

- **作者**: Sylvan Liu
- **时间**: 2026-10-17T12:47:29Z
- **提交信息**: [Fix] diffusion: keep ZMQ ingress sockets on their configured port (#43732)

Co-authored-by: Sylvan Liu <syliu@cse-ai-16.amd.com>
Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Mick <mickjagger19@icloud.com>

### [d4191a4](https://github.com/sgl-project/sglang/commit/d4191a4624751b7fd3322f425162c235264d4c38)

- **作者**: Mick
- **时间**: 2026-10-17T12:46:13Z
- **提交信息**: [Fix] diffusion: stabilize FLUX.3 serving and reuse static conditioning (#44493)

Co-authored-by: Yihao Wang <42559837+AgainstEntropy@users.noreply.github.com>
Co-authored-by: Dom Brown <3886319+DomBrown@users.noreply.github.com>
Co-authored-by: niehen6174 <1639206518@qq.com>
Co-authored-by: Mick Qian <mickqian@radixark.ai>
Co-authored-by: Nikita Korobov <14355239+nekorobov@users.noreply.github.com>
Co-authored-by: Daniel Campora <961215+dcampora@users.noreply.github.com>
Co-authored-by: Richard Wang <11150595+rwang5203@users.noreply.github.com>
Co-authored-by: BBuf <1182563586@qq.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Fabio Camaiora <fcamaiora@nvidia.com>
Co-authored-by: Linda-Stadter <lstadter@nvidia.com>

### [9771e5a](https://github.com/sgl-project/sglang/commit/9771e5a4f0bee54f78135703aeed5ad43681f088)

- **作者**: Mick
- **时间**: 2026-10-17T12:45:07Z
- **提交信息**: [Feat] diffusion: Per-task prompt enhancer config and the FLUX.3 Klein upsampler protocol (#44662)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [e01dfd3](https://github.com/sgl-project/sglang/commit/e01dfd3cbc53e88e71b15929ebb0ee219f4b88c2)

- **作者**: Mick
- **时间**: 2026-10-17T12:43:02Z
- **提交信息**: [Refactor] multimodal: Replace padding strategies with helpers (#44845)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [86e67f7](https://github.com/sgl-project/sglang/commit/86e67f7d93cb8720538d25123c5ff45a8683c4ba)

- **作者**: Shuwen Wang
- **时间**: 2026-10-17T12:20:49Z
- **提交信息**: [Fix] unified_cache: Prevent misaligned Mamba checkpoints after speculative truncation (#43387)

### [0256550](https://github.com/sgl-project/sglang/commit/025655068ca9d3c571200d0210221416445de619)

- **作者**: SuperSong
- **时间**: 2026-10-17T11:56:41Z
- **提交信息**: [Fix] unified-memory: Avoid gather scratch during Mamba and Conv compaction (#44097)

### [ee30dc4](https://github.com/sgl-project/sglang/commit/ee30dc4d40993045273f0a90260db7efa302c214)

- **作者**: SuperSong
- **时间**: 2026-10-17T11:46:48Z
- **提交信息**: [Fix] unified-memory: Bound joint reclaim and preserve cached prefixes (#39294)

Bound joint FULL/SWA/Mamba reclaim so feasible allocations recover capacity without evicting unnecessary cached prefixes, and impossible demands preserve the cache. Use exact unsharded paged-extend demand and update allocation regression fixtures.

### [ae28306](https://github.com/sgl-project/sglang/commit/ae28306a74fc9ba56daab9ccb06dcf45659f58af)

- **作者**: Shuwen Wang
- **时间**: 2026-10-17T11:13:57Z
- **提交信息**: [Fix] cuda_graph: Wait for in-flight layer-wise cache loads before prefill graph replay (#44220)

### [5fcb07d](https://github.com/sgl-project/sglang/commit/5fcb07da34abb98a5210ff40d03290a74ac0df01)

- **作者**: Shuwen Wang
- **时间**: 2026-10-17T11:08:17Z
- **提交信息**: [Fix] hicache: Key MLA Mamba state per TP rank in the HF3FS backend (#43817)

Co-authored-by: Zhangheng <hzh0425@apache.org>

### [465ddf9](https://github.com/sgl-project/sglang/commit/465ddf9758878a678aecb65f713655afe5ede518)

- **作者**: Woody-Hu
- **时间**: 2026-10-17T10:47:19Z
- **提交信息**: [Feat] diffusion/VSA-H3: support sm80 (A100) with a raw-pointer Triton load path (#43823)

Co-authored-by: Mick <mickjagger19@icloud.com>

### [400c1df](https://github.com/sgl-project/sglang/commit/400c1dfe6eb42b2b3ff79c8a1f773227c84094ec)

- **作者**: Mick
- **时间**: 2026-10-17T10:44:31Z
- **提交信息**: [Perf] distributed: skip the DLPack re-wrap of custom all-reduce results (#44251)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [eb5739b](https://github.com/sgl-project/sglang/commit/eb5739b30e7e5cb2d7833a8952a24e4e470718f8)

- **作者**: pllimax
- **时间**: 2026-10-17T10:21:17Z
- **提交信息**: [CI] pr-test-npu: Temporarily disable recommend-tests-from-coverage job (#44881)

### [a126e8d](https://github.com/sgl-project/sglang/commit/a126e8d640c707f855e8da31f906035883f4ff70)

- **作者**: Khoa Pham
- **时间**: 2026-10-17T09:45:53Z
- **提交信息**: [Perf] deepseek_v4: fold the MegaAttention query layout into wq_b for block-FP8-as-MXFP8 checkpoints (#44838)

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [80f4052](https://github.com/sgl-project/sglang/commit/80f40522cdc53a000577c57a9b0285c204e4c74b)

- **作者**: Mick
- **时间**: 2026-10-17T08:47:07Z
- **提交信息**: [UX] diffusion: log LoRA merge decisions only on first evaluation (#44376)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [56a20d7](https://github.com/sgl-project/sglang/commit/56a20d7e3436005278be612fd1623ac9d488f124)

- **作者**: Mick
- **时间**: 2026-10-17T08:43:27Z
- **提交信息**: [Perf] kernels: Enter a JIT kernel's device guard only when the device differs (#44644)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [f75232c](https://github.com/sgl-project/sglang/commit/f75232cb42a80a267f56e5547ace5c35a648e39c)

- **作者**: metamergebot
- **时间**: 2026-10-17T08:31:40Z
- **提交信息**: [Fix] hicache: Order write-back host copies after the forward that produced the KV (#44800)

Co-authored-by: metamergebot <metamergebot@users.noreply.github.com>
Co-authored-by: xiezhq-hermann <xiezhq-hermann@users.noreply.github.com>

### [0d13efb](https://github.com/sgl-project/sglang/commit/0d13efb2b8df90487ab7fdb7867a298b6c0c30ec)

- **作者**: metamergebot
- **时间**: 2026-10-17T08:30:50Z
- **提交信息**: [Feat] rust-server: Serve /v1/tokenize and /v1/detokenize from the Rust frontend (#44767)

Co-authored-by: metamergebot <metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [a2953d7](https://github.com/sgl-project/sglang/commit/a2953d7b7fe9c7bb705e681e5011d3db80adfac7)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-17T08:25:33Z
- **提交信息**: [Fix] deepseek-v4.1: Serve prompt-logprob requests under decoder SWA bounded replay (#44850)

Co-authored-by: Pedram Ghazi <pedram.ghazi@amd.com>
Co-authored-by: David Orman <ormandj@corenode.com>

### [7a8804e](https://github.com/sgl-project/sglang/commit/7a8804edb5fcf72687fc9e352e6517969c3c497b)

- **作者**: McZyWu
- **时间**: 2026-10-17T08:19:44Z
- **提交信息**: [Fix] [NPU] qwen: Fix shared-expert routing with Ascend FuseEP (#40516)

### [ef26f6a](https://github.com/sgl-project/sglang/commit/ef26f6ad49b03d85bea33d080c2c7d46e2f84097)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-17T07:56:18Z
- **提交信息**: [Fix] deepseek-v4.1: Keep the cached KV of folded encoder replay rows (#44857)

### [bce7b27](https://github.com/sgl-project/sglang/commit/bce7b27aa6aabda681351f8f4c20776981b5d5d4)

- **作者**: Khoa Pham
- **时间**: 2026-10-17T07:19:35Z
- **提交信息**: [Perf] deepseek_v4: run FlashInfer autotune for block-FP8 models served as MXFP8 (#44842)

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [01dc08e](https://github.com/sgl-project/sglang/commit/01dc08e23f689d0577494042fe7456f424421e64)

- **作者**: Ziyi Xu
- **时间**: 2026-10-17T07:15:49Z
- **提交信息**: [Refactor] dsv41: Shard Engram tables on hash-column boundaries (#42787)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: hnyls2002 <lsyincs@gmail.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-10-18
**监控日期**: 2026-10-17
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1291
- **最后更新**: 2026-10-16T11:34:01Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-10-18
**监控日期**: 2026-10-17
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 94007
- **最后更新**: 2026-10-17T23:36:48Z

## 提交统计

- **昨日提交总数**: 30
- **提交者数量**: 23
- **主要提交者**: afriedri, djramic, Alec

## AI分析总结

# vLLM 昨日提交分析总结

## 1. 主要更新类型分布

- **Bug 修复**（约 15 条）：占比最大，覆盖推理引擎核心（会话恢复、block-table、CUDA graph OOM）、投机解码、内核、前端等领域。
- **性能优化**（约 5 条）：包括 Qwen3 工具参数流式解析、DeepSeek-V4 VL 权重流式加载、ROCm AITER 内核选择、单节点 FlashInfer allreduce 回归 MNNVL、MLA 权重吸收跳过等。
- **功能新增/增强**（约 6 条）：Expert LoRA（FlashInfer TRTLLM MXFP4）、Step-5/Muse Spark norm 融合内核、per-case 内核性能分析、Rust 前端 bad_words 校验等。
- **文档与 CI**（约 4 条）：DeepSeek-V4.1 Flash 配方同步、模型配方集中到 recipes/、AMD CI webhook 优化；另有一条"添加后又回滚"的 agent skill 文档提交。

## 2. 关键变更点与项目方向的关系

- **分布式推理与 MoE 生态持续深化**：EPLB（专家并行负载均衡）与 NIXL 传输层的多个修复（#62081、#62210）表明项目正稳定 RDMA/NIXL 后端的专家权重传输路径，这是大规模 MoE 推理（如 DeepSeek 系列）可靠落地的关键。
- **投机解码（Spec Decode）成熟化**：动态投机解码降级而非崩溃（#46399）、EAGLE 启发式改为显式 draft-layer 标签（#61455）、共享 block-table 清理（#61174）、MRV2 中先收集 KV 传输结果再运行 drafter（#62041）——一系列修复说明投机解码正从"能用"走向"稳健"。
- **前端与 API 正确性**：beam search 中 allowed_token_ids 生效（#47630）、completion derender 保留 token IDs（#62114）、会话在抢占后恢复（#58778）等，提升 OpenAI 兼容 API 的语义正确性。
- **硬件多平台扩展**：ROCm（AMD）、XPU（Intel）均有贡献，且 AMD 出现了 a4w4 GEMM 内核自动调优选择的性能提交，说明异构硬件支持进入"调优+自动化"阶段。
- **新模型适配提速**：Step-5 Preview、Muse Spark、Gemma 4、DeepSeek-V4/V4.1 VL 均有专属修复或优化，体现 vLLM 作为"模型快速上车平台"的定位。

## 3. 对项目的影响

- 核心稳定性：EPLB/NIXL、会话恢复、CUDA graph OOM 等修复直接降低生产环境的失败率和冷启动开销。
- 性能收益显著：Qwen3 工具解析从 2.1 秒降至 11 毫秒、DeepSeek 权重流式加载避免排序开销，对长上下文和大模型加载体验有量级改善。
- 开发体验：vllm bench forward 新增 per-case 内核 profile、tokenizer 对齐探针给出真实失败原因，便于贡献者定位问题。

## 4. 值得关注的技术点

- **AI 代理协作已成常态**：约半数提交含 Claude Opus 5.5 / vllm-agent / Codex 作为 co-author，说明 AI 辅助编程已深度融入 vLLM 的日常开发流程。
- **EAGLE 投机解码的"显式 draft-layer 标签"设计**（#61455）是一次重要的内部 API 收敛，用显式元数据替代启发式猜测，有利于后续模型扩展。
- **hadacore 内核部分 warp 越界读修复**（#61944）体现了对 GPU 内存安全边界的细致审查。
- **MLA 权重吸收可跳过**（#57320）为已预处理权重的部署场景省去重复计算，对 DeepSeek 类 MLA 架构有直接价值。

## 5. 对项目发展的整体意义

结合 README "Easy, fast, and cheap LLM serving for everyone" 的定位，昨日提交呈现出典型的"平台成熟期"特征：重心从新增大功能转向把已落地的高级特性（MoE EPLB、投机解码、NIXL 传输、多硬件后端）打磨到生产可用，同时以极快节奏适配新模型（DeepSeek-V4、Gemma 4、Step-5）。这将进一步巩固 vLLM 作为开源 LLM 服务事实标准的地位——尤其在大规模 MoE 与投机解码两条性能主线上，项目的工程深度正持续拉开与竞品的差距。

## 详细提交记录

### [9c778e9](https://github.com/vllm-project/vllm/commit/9c778e9ff8d0c78a241d7f530c441c2dc1d67533)

- **作者**: djramic
- **时间**: 2026-10-17T23:18:02Z
- **提交信息**: [Bugfix][EPLB] Wait for pending expert buffer copies before NIXL READs (#62081)

Signed-off-by: Djordje Ramic <djoramic@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [7879f36](https://github.com/vllm-project/vllm/commit/7879f3687b5b6a4be4754242e70b9c21cf7b4183)

- **作者**: David Cheung
- **时间**: 2026-10-17T21:24:35Z
- **提交信息**: [NIXL] Drop unreachable producer-side notif counting in push mode (#62210)

Signed-off-by: David Cheung <d7cheung@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [255f145](https://github.com/vllm-project/vllm/commit/255f14599ec0544c35539414810abdfa7e4e1c86)

- **作者**: Kevin H. Luu
- **时间**: 2026-10-17T18:56:28Z
- **提交信息**: [Bugfix][Rust Frontend] Fix macOS build: read inherited listener family from its address (#62177)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [03e8300](https://github.com/vllm-project/vllm/commit/03e8300d2cac77b24f7ab6013a803369ee64c19e)

- **作者**: yifanFengg
- **时间**: 2026-10-17T18:53:06Z
- **提交信息**: [Bugfix] Enable inductor batch-invariant mode under VLLM_BATCH_INVARIANT (#61118)

Signed-off-by: Yifan Feng <evanfengff@gmail.com>
Signed-off-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>
Co-authored-by: Kevin H. Luu <khluu000@gmail.com>

### [5c1c903](https://github.com/vllm-project/vllm/commit/5c1c903501927ea7c6c699aabd4c271015e66e71)

- **作者**: Afonso Ribeiro
- **时间**: 2026-10-17T18:49:06Z
- **提交信息**: [Perf][Parser] Stream Qwen3 tool argument values incrementally (12 KB call: 2.1 s to 11 ms) (#62027)

Signed-off-by: Afonso Ribeiro <afonso.diamantino2@gmail.com>
Co-authored-by: Flora Feng <4florafeng@gmail.com>

### [bafb263](https://github.com/vllm-project/vllm/commit/bafb263664e87daea420f47bd07f4831b7b31bcc)

- **作者**: Tyrone
- **时间**: 2026-10-17T18:47:52Z
- **提交信息**: [Bugfix][Benchmarks] Name the real cause when the /tokenize alignment probe fails (#59888)

### [0c5dd18](https://github.com/vllm-project/vllm/commit/0c5dd18e7a0ace18d99438fb16b8375572ea76b5)

- **作者**: Nick Hill
- **时间**: 2026-10-17T17:27:57Z
- **提交信息**: [MRV2] Collect KV transfer results before the drafter runs (#62041)

Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [763e3f7](https://github.com/vllm-project/vllm/commit/763e3f7c911308fa609fb9437642929efe955798)

- **作者**: Ting SUN
- **时间**: 2026-10-17T16:41:04Z
- **提交信息**: [Bugfix][Spec Decode] Disable dynamic speculative decoding for fixed-K proposers instead of crashing (#46399)

Signed-off-by: Ting Sun <suntcrick@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>

### [e744eac](https://github.com/vllm-project/vllm/commit/e744eacf682f2b1c7f91d2dcf348a015046e56b9)

- **作者**: Alec
- **时间**: 2026-10-17T16:10:40Z
- **提交信息**: [Rust Frontend] Validate bad_words limits during request lowering (#61933)

Signed-off-by: Alec Flowers <aflowers@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [c0b6f74](https://github.com/vllm-project/vllm/commit/c0b6f74bee518aeaf5d72b200a0216e72fbb5e7c)

- **作者**: Woosuk Kwon
- **时间**: 2026-10-17T15:27:11Z
- **提交信息**: [Benchmark] Add per-case kernel profiles to vllm bench forward (#61692)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [c61a1e7](https://github.com/vllm-project/vllm/commit/c61a1e73c664ef59e4dd496e6b32eb4ba0c95b9a)

- **作者**: siyu
- **时间**: 2026-10-17T15:10:04Z
- **提交信息**: [Feature] Skip MLA weight absorption when weights are pre-processed (#57320)

Co-authored-by: Xun Sun <UNIDY2002@outlook.com>

### [237d99b](https://github.com/vllm-project/vllm/commit/237d99b4aff67ecfedacca7acb0ee93f299fa54e)

- **作者**: aoshen02
- **时间**: 2026-10-17T13:54:30Z
- **提交信息**: Revert "[Docs] Add train-inference consistency agent skill" (#61551) (#62186)

Signed-off-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [2d8efee](https://github.com/vllm-project/vllm/commit/2d8efee9a73366d6b4e753780af32443d2fef91a)

- **作者**: aoshen02
- **时间**: 2026-10-17T12:49:50Z
- **提交信息**: [Docs] Add train-inference consistency agent skill (#61551)

Signed-off-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [21e09ea](https://github.com/vllm-project/vllm/commit/21e09ea95926fcfe4df1c57bf2eb95123cab70c3)

- **作者**: Roy Wang
- **时间**: 2026-10-17T12:27:52Z
- **提交信息**: [Doc] Sync DeepSeek-V4.1-Flash recipe with vllm-project/recipes#1136, #1137 (#62179)

Signed-off-by: esmeetu <jasonailu87@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [837e87e](https://github.com/vllm-project/vllm/commit/837e87e1c5024843b66383ef1bd60ca5672a9575)

- **作者**: aoshen02
- **时间**: 2026-10-17T12:17:56Z
- **提交信息**: [Feature][LoRA][MoE] Expert LoRA for FlashInfer TRTLLM MXFP4 experts (#61979)

Signed-off-by: aoshen524 <aoshen524@gmail.com>
Co-authored-by: aoshen524 <aoshen524@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [4e964b2](https://github.com/vllm-project/vllm/commit/4e964b2623c951d063f4b7f23790d16f2d6b7f94)

- **作者**: liuzhenwei
- **时间**: 2026-10-17T11:10:39Z
- **提交信息**: [XPU] Fix Event init failure w/ external (#61743)

Signed-off-by: zhenwei-intel <zhenwei.liu@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [ec8b20f](https://github.com/vllm-project/vllm/commit/ec8b20fbf01e04d33bb059e555a9b5f39fb4cc46)

- **作者**: Vadim Gimpelson
- **时间**: 2026-10-17T11:04:49Z
- **提交信息**: [Bugfix] Fix Gemma 4 encoder CUDA graph capture OOM at startup (#61365)

Signed-off-by: Vadim Gimpelson <vadim.gimpelson@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [2b85d9c](https://github.com/vllm-project/vllm/commit/2b85d9cb65c1f56c347cb7f56f1596a6b8b28373)

- **作者**: Kevin H. Luu
- **时间**: 2026-10-17T09:55:28Z
- **提交信息**: [Perf][Bugfix] Prefer MNNVL for single-node FlashInfer allreduce again (#61989)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Wei Zhao <51183510+wzhao18@users.noreply.github.com>

### [026f6ab](https://github.com/vllm-project/vllm/commit/026f6ab2689397e64c1f53a5ac57d37c4dc46b67)

- **作者**: gitbisector
- **时间**: 2026-10-17T09:37:56Z
- **提交信息**: [Model] DeepSeek-V4/V4.1 VL: stream language-model weights instead of sorting the checkpoint (#58857)

Signed-off-by: git bisector <gitbisector@gmail.com>
Signed-off-by: Yifan Qiao <yifanqiao@inferact.ai>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Yifan Qiao <yifanqiao@inferact.ai>

### [b515648](https://github.com/vllm-project/vllm/commit/b515648641227afe0d0fe92be7efac80471b295e)

- **作者**: Roy Wang
- **时间**: 2026-10-17T09:14:36Z
- **提交信息**: [Doc] Host model recipes in recipes/ (#61302)

Signed-off-by: esmeetu <jasonailu87@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [f98ae6a](https://github.com/vllm-project/vllm/commit/f98ae6a9fd2c73a2f80dd9fe4c534676f689394d)

- **作者**: David Cheung
- **时间**: 2026-10-17T09:08:14Z
- **提交信息**: [Bugfix][Core] Keep resumable sessions that stop while preempted (#58778)

Signed-off-by: David Cheung <d7cheung@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Yifan Zong <yzong@redhat.com>

### [2067297](https://github.com/vllm-project/vllm/commit/2067297b2f15f0776be6d2a7e1b435bd20af60c1)

- **作者**: afriedri
- **时间**: 2026-10-17T09:00:28Z
- **提交信息**: [ROCm][Perf] Use AITER tuned configs to select a4w4 gemm kernel instead of env var (#61278)

Signed-off-by: Andy Friedrich <afriedri@amd.com>
Signed-off-by: afriedri <afriedri@amd.com>
Co-authored-by: Simon Danielsson <70206058+simondanielsson@users.noreply.github.com>
Co-authored-by: Kevin H. Luu <khluu000@gmail.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [3bf25c5](https://github.com/vllm-project/vllm/commit/3bf25c50971e8a7dd4da550dc815d8972b51db61)

- **作者**: Aarushi Jain
- **时间**: 2026-10-17T08:54:31Z
- **提交信息**:  [CI][Bugfix] Ignore AMD CI webhook no-op builds in /amd-ci run and retry (#62087)

Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [e56b160](https://github.com/vllm-project/vllm/commit/e56b1603afd94d4da880972eeca47491b5dfaaf6)

- **作者**: Jee Jee Li
- **时间**: 2026-10-17T08:53:00Z
- **提交信息**: [Kernel]Add norm fused kernel for Step-5 Preview and Muse Spark Open (#62132)

Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>

### [eb8de8d](https://github.com/vllm-project/vllm/commit/eb8de8d1a1a79fce8bb2ce90be8620768d0f8347)

- **作者**: Ting SUN
- **时间**: 2026-10-17T08:50:40Z
- **提交信息**: [Bugfix][OpenAI] Respect allowed_token_ids in beam search (#47630)

Signed-off-by: Ting Sun <suntcrick@gmail.com>

### [b05ede5](https://github.com/vllm-project/vllm/commit/b05ede56168b5718c425c1493914e5e79f6b8181)

- **作者**: dskwe
- **时间**: 2026-10-17T08:27:48Z
- **提交信息**: [Bugfix][Frontend] Preserve token IDs in completion derender responses (#62114)

Signed-off-by: Yuan Li <dskwelmcy@163.com>

### [61bb590](https://github.com/vllm-project/vllm/commit/61bb590877521e2f4516912297a40f593e222ee9)

- **作者**: Cheng Rui
- **时间**: 2026-10-17T08:25:02Z
- **提交信息**: [Bugfix][Spec Decode] Clear stale shared block-table rows (#61174)

Signed-off-by: Cheng Rui <286040359@qq.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Giancarlo Delfin <32987265+TheEpicDolphin@users.noreply.github.com>

### [c3de0b3](https://github.com/vllm-project/vllm/commit/c3de0b37e25fb4b59eaa3e292df928c61b3dc172)

- **作者**: Dakai An
- **时间**: 2026-10-17T08:22:33Z
- **提交信息**: [Core][Spec Decode] Replace EAGLE group heuristics with explicit draft-layer tags (#61455)

Signed-off-by: Dakai An <dakaian108@gmail.com>
Signed-off-by: Yifan Qiao <yifanqiao@inferact.ai>
Co-authored-by: Yifan Qiao <yifanqiao@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [08a65e2](https://github.com/vllm-project/vllm/commit/08a65e287e55099255ce178c5b5f58ce42dfd461)

- **作者**: Kevin H. Luu
- **时间**: 2026-10-17T07:52:17Z
- **提交信息**: [Bugfix][Kernel] hadacore: don't load past the input on a partial last warp (#61944)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Jee Jee Li <pandaleefree@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [ad2688a](https://github.com/vllm-project/vllm/commit/ad2688ab302a24661a3eb4a4754ebd5743cba71a)

- **作者**: znzryb
- **时间**: 2026-10-17T07:51:36Z
- **提交信息**: [Bugfix] Validate draft-token capacity in forward benchmark (#61809)

Signed-off-by: znzryb <znzryb34@gmail.com>
Co-authored-by: Woosuk Kwon <woosuk@inferact.ai>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-10-18
**监控日期**: 2026-10-17
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7225
- **最后更新**: 2026-10-17T22:24:07Z

## 提交统计

- **昨日提交总数**: 10
- **提交者数量**: 9
- **主要提交者**: amy-why-3459, tsinghua-code, haic0

## AI分析总结

## vllm-omni 昨日提交分析

### 1. 主要更新类型

本次提交以**性能优化**为主（约5/10），其次是**功能新增**（2-3个），另有少量CI/文档与核心架构变更。整体呈现"持续打磨性能 + 扩展新模态支持"的节奏。

### 2. 关键变更点及与项目方向的关系

- **NPU/Ascend 硬件适配持续深化**：CAM++ 说话人嵌入迁移到 NPU、MiniCPM-o 的 CFM DiT body 在 NPU 上融合。这与 vllm-omni "低成本全模态推理"的目标一致，特别是针对华为昇腾生态的国产芯片落地。
- **调度器算法优化**：chunk 队列分区从 O(N²) 降到 O(N)，移除了循环内 `remove` 的低效写法，属于底层调度核心的正向改进。
- **PersonaPlex 性能大改**：引入批量执行、CUDA Graphs 和内存优化，覆盖 Stage 0/Depformer/Stage 1，是一次系统性的推理提速。
- **新增 LTX 2.5 文本到音频（T2A）单阶段 pipeline**：扩展了项目的音频生成模态能力，丰富"omni-modality"版图。
- **全双工（Duplex）服务能力**：引入会话感知的副本放置与多前端全双工服务，对语音实时交互场景意义重大，是走向实用对话系统的关键一步。
- **跨注意力抽象层**：引入通用 cross-attention 并集成 LingBot，属于架构层面的可复用性提升。
- **Qwen-Image-2.1 优化**：复用重复 conditioning 与共享 modulation，减少冗余计算。
- **MAGI-2 优化**：固定 attention head 布局以优化输出投影。
- **ROCm 文档/CI**：为 MI300 夜间构建添加 Qwen2.5-Omni 示例，覆盖 AMD GPU 生态。

### 3. 对项目的影响和潜在意义

- **多硬件生态覆盖增强**：本次同时推进了 Ascend NPU、CUDA、ROCm 三条线，体现项目"跨平台全模态推理"的定位正在加速兑现。
- **性能持续收敛**：多处计算冗余消除和算法复杂度降低，长期看有助于降低 serving 成本——这正是 README 中 "cheap" 承诺的落地。
- **模态版图扩展**：T2A pipeline 和全双工服务让项目从"能推理多模态"向"能实用部署多模态应用"演进。

### 4. 值得关注的技术点

- **CUDA Graphs 在 PersonaPlex 中的应用**，对降低 kernel launch 开销效果显著。
- **会话感知副本放置**（session-aware replica placement），对全双工语音场景下的状态一致性和延迟优化有参考价值。
- **NPU CFM DiT body 融合**展示了对 diffusion 类模型在非 CUDA 硬件上的深度定制能力。
- **通用 cross-attention 抽象**，为后续更多模型的接入降低了适配成本。

### 5. 对项目发展的整体影响

基于 README 中 "Easy, fast, and cheap omni-modality model serving" 的定位，这些提交在三个维度上推动项目前进：**广度**（新增 T2A、更多模型示例）、**速度**（多处算法与硬件级优化）、**可用性**（全双工服务、跨平台支持）。华为与 AMD 贡献者活跃度高，说明多厂商共建生态已初具规模，这对项目长期竞争力和生态扩展是积极信号。

## 详细提交记录

### [dfdae25](https://github.com/vllm-project/vllm-omni/commit/dfdae25d67896d4982eb445a3f77353e8e44653c)

- **作者**: y-null
- **时间**: 2026-10-17T17:49:25Z
- **提交信息**: [Hardware][Ascend][Perf] Run the CAM++ speaker embedding on the NPU instead of CPU onnxruntime (#9026)

Signed-off-by: y-null <y-null@users.noreply.github.com>
Co-authored-by: y-null <y-null@users.noreply.github.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [04c347c](https://github.com/vllm-project/vllm-omni/commit/04c347c993a2b6a4eb5098a1dec87e0771045ef9)

- **作者**: Stochastic
- **时间**: 2026-10-17T17:48:57Z
- **提交信息**: [perf][sched] O(N) chunk queue partition: remove O(N²) queue.remove-in-loop (#9025)

Signed-off-by: Asthenia0412 <Asthenia0412@users.noreply.github.com>
Co-authored-by: Asthenia0412 <asthenia0412@users.noreply.github.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [37c78bd](https://github.com/vllm-project/vllm-omni/commit/37c78bd6d4788fb8010d73e88670311aa3089647)

- **作者**: BeatSeat
- **时间**: 2026-10-17T17:24:14Z
- **提交信息**: [Perf][PersonaPlex] Batched execution, CUDA graphs, and memory optimization (Stage 0, Depformer, Stage 1) (#8441)

Signed-off-by: BeatSeat <wendavid552@gmail.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [a091098](https://github.com/vllm-project/vllm-omni/commit/a09109802595efd47b957f35487828ef9035f296)

- **作者**: hurukawa
- **时间**: 2026-10-17T15:47:44Z
- **提交信息**: [Feature] Add Text-to-audio one-stage pipline for LTX 2.5 (#6489)

Signed-off-by: nagisa <1434936049@qq.com>
Signed-off-by: nagisa-kun <1434936049@qq.com>

### [73e6560](https://github.com/vllm-project/vllm-omni/commit/73e6560360d96cd3db8ff5dcbcec4b0c3b4de316)

- **作者**: amy-why-3459
- **时间**: 2026-10-17T15:45:02Z
- **提交信息**: [Perf][MiniCPM-o] Fuse the NPU CFM DiT body (#8908)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [cd53b96](https://github.com/vllm-project/vllm-omni/commit/cd53b96883625676fab0af25b599a474eb660cef)

- **作者**: haic0
- **时间**: 2026-10-17T15:40:41Z
- **提交信息**: [CI/Build][ROCm] Add Qwen2.5-Omni documentation examples to MI300 nightly (#9000)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>
Signed-off-by: andyluo7 <andy.luo@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: andyluo7 <andy.luo@amd.com>

### [8468d73](https://github.com/vllm-project/vllm-omni/commit/8468d73c4bf54c4fd0ae43356819823a83a86201)

- **作者**: QianCyrus
- **时间**: 2026-10-17T14:40:15Z
- **提交信息**: [Core][Duplex] Add session-aware replica placement and multi-frontend full-duplex serving (#8913)

Signed-off-by: QianCyrus <101633534+QianCyrus@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Fallenpetal <2205151451@qq.com>

### [b164fea](https://github.com/vllm-project/vllm-omni/commit/b164fea797531c1fa10f8b87829632cad006b9fc)

- **作者**: amy-why-3459
- **时间**: 2026-10-17T08:58:35Z
- **提交信息**: [Perf][Qwen-Image-2.1] Reuse repeated conditioning and shared modulation (#8729)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [69d298a](https://github.com/vllm-project/vllm-omni/commit/69d298af462e7552a3708613d683f1a58aa1b193)

- **作者**: tsinghua-code
- **时间**: 2026-10-17T08:57:11Z
- **提交信息**: [Core] Introduce a generic cross-attention abstraction with LingBot integration (#8859)

Signed-off-by: tsinghua-code <zr-liu25@mails.tsinghua.edu.cn>

### [7201e78](https://github.com/vllm-project/vllm-omni/commit/7201e7820b9c7febfafd586d48254bd375e486cc)

- **作者**: R0CKSTAR
- **时间**: 2026-10-17T08:06:46Z
- **提交信息**: [Perf] MAGI-2: pin the attention head layout in the output projection (#8627)

Signed-off-by: Xiaodong Ye <xiaodong.ye@mthreads.com>

---
