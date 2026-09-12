# GitHub Stars 合并报告 - 2026-09-11

**合并日期**: 2026-09-12
**监控日期**: 2026-09-11
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


**报告日期**: 2026-09-12
**监控日期**: 2026-09-11
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2205
- **最后更新**: 2026-09-11T20:28:35Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Bin Jia

## AI分析总结

# VeOmni 昨日提交分析（第 1/1 批）

## 1. 主要更新类型
本次提交属于**依赖升级 + 破坏性变更（BREAKING CHANGE）**，涉及模型、算子（ops）及杂项模块。核心动作是将 `transformers` 库升级至 5.16.1，并明确标记为不兼容变更，说明升级可能引入 API 或行为差异，需要下游适配。

## 2. 关键变更点与项目方向的关系
- **关键点**：`transformers` 版本跃迁至 5.16.1，且被标记为 BREAKING，意味着模型加载、配置解析、tokenizer 或算子接口可能发生不兼容调整。
- **与项目方向的关系**：VeOmni 定位为“任意模态模型训练”的分布式配方库（Recipe Zoo），高度依赖 HuggingFace 生态的模型与工具链。紧跟 `transformers` 主版本，有助于保持对最新模型架构（多模态、任意模态）的兼容性，符合其“Scaling Any Modality Model Training”的核心目标。

## 3. 对项目的影响与潜在意义
- **短期影响**：现有用户升级后可能遇到模型加载失败、配置字段变更或算子行为差异，需要按迁移说明调整代码或锁定旧版本。
- **长期意义**：主动对齐上游最新版本，可减少未来技术债，确保 VeOmni 能第一时间支持新发布的模态模型，巩固其作为“分布式训练配方集合”的前瞻性。
- **生态意义**：BREAKING 标记体现了对语义化版本与用户预期的尊重，有助于维护社区信任。

## 4. 值得关注的技术点
- `transformers` 5.x 相比 4.x 在模型注册、注意力实现、多模态处理器上的潜在重构。
- 升级是否同步调整了 VeOmni 自身的 ops 层封装，以适配新版本算子接口。
- 是否更新了依赖约束文件（如 `pyproject.toml` / `requirements`）及 CI 测试矩阵。
- 对分布式训练配方（recipe）中模型并行、FSDP/TP 等策略是否产生连带影响。

## 5. 基于 README 背景的项目发展影响
VeOmni 强调“Model-Centric Distributed Recipe Zoo”，即围绕模型组织分布式训练配方。`transformers` 是其模型接入的关键上游。此次升级：
- **正面**：使配方库能覆盖更多基于新版 `transformers` 的模型，扩展“任意模态”支持范围。
- **风险**：若迁移不彻底，可能导致部分既有配方失效，影响用户复现论文结果。
- **战略**：体现项目在快速演进的 AI 生态中保持同步的意愿，是维持竞争力的必要维护动作，但需配套迁移文档与回归测试，以降低破坏性升级带来的使用门槛。

**总结**：这是一次以依赖升级为核心的破坏性维护提交，短期带来适配成本，长期利于项目紧跟上游、扩展多模态模型支持，是 VeOmni 保持生态同步性的关键一步。

## 详细提交记录

### [b8a3edc](https://github.com/ByteDance-Seed/VeOmni/commit/b8a3edcc01dba6026c785fa087a9ca1a59c9c9e2)

- **作者**: Bin Jia
- **时间**: 2026-09-11T13:00:22Z
- **提交信息**: [BREAKING][model, ops, misc] chore: upgrade transformers to 5.16.1 (#1171)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-09-12
**监控日期**: 2026-09-11
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2804
- **最后更新**: 2026-09-11T12:06:18Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Yang Yong (雍洋)

## AI分析总结

## 提交分析总结

**1. 主要更新类型**
本次提交属于**代码修复/重构类**更新，具体为修正模块导入路径（import 语句），涉及 `cache_minimax_h3_adaln` 相关模块。从提交信息看，这是一次小范围的依赖引用修正，而非功能新增或性能优化。

**2. 关键变更点及与项目方向的关系**
- 变更核心是更新 `cache_minimax_h3_adaln` 的 import 路径，属于内部模块引用调整。
- 结合 LightX2V 作为“轻量视频生成推理框架”的定位，该项目持续集成多种视频生成模型（如 MiniMax、Hunyuan 等系列）及其缓存/加速机制。`adaln`（自适应层归一化）与 `cache` 通常关联于 DiT 类视频生成模型的推理加速策略。
- 此次修正表明项目正在维护或扩展对 MiniMax H3 相关模型缓存机制的支持，与框架“多模型、高效推理”的整体方向一致。

**3. 对项目的影响和潜在意义**
- 修复导入错误可避免运行时 `ImportError`，保证相关推理流程（尤其是启用缓存优化的 MiniMax 路径）能正常加载。
- 属于维护性修复，对框架整体功能无破坏性影响，但能提升代码健壮性和可用性。
- 若此前该 import 已失效，则此提交恢复了对应模块的可用性，对使用该模型缓存的用户有直接价值。

**4. 值得关注的技术点**
- `cache_minimax_h3_adaln` 命名暗示了针对 MiniMax H3 模型的缓存与 AdaLN 结合优化，可能涉及推理时的 KV Cache 或特征缓存复用。
- 在视频生成推理框架中，缓存机制是降低显存占用、提升生成速度的关键手段，此类模块的维护反映了项目对推理效率的持续投入。
- import 路径的调整也可能意味着模块目录结构发生了重构，值得留意后续是否有相关文档或配置同步更新。

**5. 基于 README 背景的项目发展影响**
LightX2V 定位为轻量级视频生成推理框架，强调高效推理与多模型支持。本次提交虽小，但体现了项目在快速迭代中持续维护各模型适配路径的工程实践。它保障了 MiniMax H3 相关缓存优化功能的可用性，间接支撑框架“轻量、高效”的核心目标。对于依赖该模型进行视频生成的用户而言，此类修复是框架稳定性的重要保障，也为后续功能扩展奠定了基础。

## 详细提交记录

### [9bf4d39](https://github.com/ModelTC/LightX2V/commit/9bf4d39ac048a0d922b9a2139da9ed795f78f4e8)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-09-11T12:04:39Z
- **提交信息**: update cache_minimax_h3_adaln import (#1514)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-09-12
**监控日期**: 2026-09-11
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2245
- **最后更新**: 2026-09-11T19:23:33Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-09-12
**监控日期**: 2026-09-11
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6379
- **最后更新**: 2026-09-12T00:04:24Z

## 提交统计

- **昨日提交总数**: 19
- **提交者数量**: 12
- **主要提交者**: eigen, Alex, baonudesifeizhai

## AI分析总结

# FlashInfer 昨日提交总结

## 一、主要更新类型

昨日共 19 个提交，以**功能新增**与**Bug 修复**为主，辅以构建配置调整：

- **功能新增**：SM100a/SM103a 支持、SM120 稀疏 MLA 行步长、CuTe-DSL MXFP8 支持 fp32 输入、Blackwell MNNVL MoE all-to-all 后端、cuTile 系列 GEMM 内核、融合 KDA 解码后端 `cake`。
- **重大特性**：新增 CUTLASS Primitives + 任务调度（PrimsTS）Blackwell MoE 后端。
- **Bug 修复**：采样 softmax 归一化、分布式通信同步、MoE autotuner 布局断言、稀疏 MLA tile 选择、cuDNN 依赖回滚、Humming MXFP4 FP8 scale 溢出、per-token NVFP4 fast-math INF scale、bmm_fp8 cublasLt handle 误用、GDN 磁盘缓存往返测试。
- **构建/流程**：CODEOWNERS 全局审批人、nvidia-cudnn-frontend 版本下限提升。

## 二、关键变更点与项目方向

- **数值正确性优先**：`__fmul_rn` 修复低温采样概率 >1 问题，直接影响投机解码 token 接受逻辑；MoE 量化中针对极小 amax 与全零行导致的 Inf/NaN 污染进行防护，属生产级关键修复。
- **分布式健壮性**：`TorchDistBackend.Split()` 改为同步集合操作，对齐 MPI 语义，消除 rank 提前退出导致的 socket 断裂窗口。
- **量化布局统一化**：修复 MoE autotuner 对 mxfp8 扁平 scale 布局的假设，为 MXFP8 增加 fp32 输入，逐步收敛量化接口约定。
- **新硬件与新后端**：SM100a、SM120 稀疏 MLA、SM103a BF16 pre-attention、Blackwell MNNVL、PrimsTS MoE、cuTile GEMM、Cake 解码后端，均采用显式 opt-in，默认行为不变，体现渐进式演进策略。

## 三、对项目的影响与潜在意义

- PrimsTS 引入独立于 TRT-LLM Gen 的 MoE 后端，降低对单一上游依赖；MoE autotuner 修复解除 TRT-LLM 使用 FlashInfer 后端的阻塞。
- 稀疏 MLA 行宽从 656B 压缩到 528B，KV 存储下降 19.5%，对长上下文推理有直接收益。
- Cake 后端在 B200/B300 上相对 CuTe DSL 取得约 1.02–1.05x 稳定加速，1315/1315 用例全部更快，具备量产性能优势。
- bmm_fp8 修复解决 vLLM 在 Blackwell 上 autotune/profiling 路径失败，强化下游兼容性。
- cuDNN 版本下限回滚，说明依赖升级需更谨慎验证。

## 四、值得关注的技术点

- `__fmul_rn` 阻止编译器 FMA 融合，是浮点确定性控制的典型案例。
- gloo pair 握手非对称性导致 `new_group()` 不隐含同步，属分布式调试隐蔽陷阱。
- 稀疏 MLA 中恰好为 2 的幂次头数（1/2/4）反而失败，属边界条件盲区。
- FP8 scale 下溢防护用 `448 / max(row_amax, 448/FLT_MAX)` 保证结果有限。
- cublasHandle_t 与 cublasLtHandle_t 不可混用，类型重解释在特定路径才暴露。
- cuTile 作为 cuBLAS/CUTLASS 之外第三条路线，masked_bmm 达 1.22×，单 GEMM 仍落后，定位为补充。
- `auto` 调度引入隐式行为变化，新后端接入会波及既有测试与缓存语义，需加强跨 PR 集成验证。

## 五、项目发展意义

FlashInfer 定位为高性能 GPU 推理内核库。昨日提交延续三条主线：**正确性加固**（采样、通信、tile 选择、量化边界）、**量化生态扩展**（mxfp8/fp32、布局兼容）、**Blackwell 架构覆盖**（SM100a/SM103a/SM120/PrimsTS/Cake/cuTile）。横向扩展新架构与新后端以保持性能领先，纵向修复量化数值边界以保障推理正确性，二者共同巩固其作为 vLLM/SGLang/TRT-LLM 底层推理基础设施的可靠性，尤其在 MoE 与稀疏 MLA 等前沿场景中保持竞争力。项目正从单一内核实现走向**多后端自动调度 + 架构特化**的成熟阶段。

## 详细提交记录

### [eea399b](https://github.com/flashinfer-ai/flashinfer/commit/eea399b74fe3cb74f942f21eecfed6c0d46561c4)

- **作者**: Alex
- **时间**: 2026-09-11T23:52:20Z
- **提交信息**: fix(sampling): preserve softmax normalization at low temperatures (#5088)

<!-- .github/pull_request_template.md -->

## 📌 Description

Fix incorrect softmax normalization at low temperatures. On GB300 with
`temperature=0.001`, a row containing one logit of `42` and all others
`-20` can produce a probability of `1.0013437` instead of `1.0`. In
speculative decoding, this can incorrectly reject a valid token and
leave an empty rejection distribution.

Use `__fmul_rn` at all four temperature-scaling sites to round the
multiplication consistently across softmax passes, rather than allowing
it to fuse with a subsequent subtraction.

Add regression coverage for scalar and per-row temperatures across fused
and split-vocabulary execution paths.

## 🔍 Related Issues

No linked issue. This reproduces serially and is separate from the
multi-stream workspace race in #4692.

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

Changed-file hooks passed:
```bash
pre-commit run --files include/flashinfer/sampling.cuh tests/utils/test_sampling.py
```
Repository-wide hooks have not been run locally.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

Validated on GB300 (SM103):
- All six new regression cases passed against the corrected installed
GPU module, covering three shapes with scalar and per-row temperatures.
- The original split-vocabulary kernel fails normalization; the
corrected kernel passes.
- Four captured speculative-decoding failures replay correctly with the
corrected probabilities.
- Additional checks passed at temperatures `1e-5`, `0.001`, `0.01`,
`1.0`, and `2.0`.

The full upstream suite and cross-architecture validation have not been
completed.

**Minimal reproduction**
```python
import torch
import flashinfer

logits = torch.full((5, 129280), -20.0, device="cuda")
logits[:, 123] = 42.0
probs = flashinfer.sampling.softmax(logits, temperature=0.001)
# Before: probs[:, 123] == 1.0013437
# After:  probs[:, 123] == 1.0
```

**Performance:** Maximum measured softmax-kernel overhead was **0.23%
(under 0.05 µs)** on GB300 across batch sizes 5–276 at temperatures
`0.001` and `1.0`, using FP32 logits, vocabulary size 129280, and CUDA
graphs (median of three alternating before/after runs).

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

When testing header changes, rebuild the sampling module: an installed
prebuilt JIT cache can otherwise load the old binary.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Improved softmax numerical stability at very low temperatures,
preventing probability mass from being incorrectly lost and ensuring
dominant logits produce near one-hot results.
* Applied consistently across supported online softmax execution paths.

* **Tests**
* Added coverage for low-temperature softmax normalization with both
scalar and per-row temperature inputs.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [93a2377](https://github.com/flashinfer-ai/flashinfer/commit/93a2377d807724fea466b14989784feaa1acb530)

- **作者**: Alex Yang
- **时间**: 2026-09-11T23:49:11Z
- **提交信息**: fix(comm): make TorchDistBackend.Split() synchronizing, like MPI_Comm_split (#4206)

<!-- .github/pull_request_template.md -->

## 📌 Description

`TorchDistBackend.Split()` returns without synchronizing the ranks,
which leaves a window where one rank can walk away while a peer is still
building the sub-group. Two facts combine:

1. **`new_group()` does not synchronize ranks.** Its post-init store
barrier only runs when `TORCH_DIST_INIT_BARRIER=1`, and that env var
defaults to `0` (`_is_barrier_after_init` in torch's
`distributed_c10d.py`). A rank returns from
`new_subgroups_by_enumeration()` as soon as *its own* side of the
rendezvous is done.
2. **The gloo pair handshake is asymmetric.** Per
`gloo/transport/tcp/pair.cc`: "one side takes a passive role and the
other side takes an active role" — the active side connects, writes a
sequence number and returns; the passive side must still accept and
*read* it.

So `Split()` can return on one rank while a peer is still inside the
mesh. If that rank then tears its process groups down or exits, the peer
is left holding a socket that just closed.

**Fix:** barrier on the **parent** group before returning. `Split()`
becomes collective *and* synchronizing, matching `MPI_Comm_split` — and
`MPIBackend.Split` — semantics: no rank leaves until every peer has
finished its sub-group rendezvous. `Split()` runs once at setup, so the
cost is irrelevant.

## 🔍 Related Issues

Related to #4193 — but this PR **does not claim to fix it**, and
deliberately uses no closing keyword. See Reviewer Notes. The
instrumentation half of the original #4195 was split out into #4205 so
it can land independently of this one.

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

`tests/comm/test_comm_backend.py`: 9 passed, 1 skipped (mpi4py not
installed). The fake-`dist` unit test now asserts that `Split()`
barriers on the parent group, so a regression is caught without needing
real processes.

## Reviewer Notes

**I could not reproduce the CI failure in 242 runs against the unfixed
code, and I want that stated up front rather than buried.** On
Linux/x86_64 with CPU-only gloo (the **tcp** transport, same as CI):

| scenario | runs | failures |
|---|---|---|
| pytest, idle host | 60 | 0 |
| pytest, 6-way concurrent, pinned to 2 CPUs | 72 | 0 |
| hard-exit stress, sub-groups of 2 / 4 / 8 ranks | 90 | 0 |
| hard-exit stress, 16 ranks timesharing 1 CPU | 20 | 0 |

The "hard-exit stress" harness was written specifically to trigger the
window described above — every rank calls `os._exit(0)` the instant
`Split()` returns, no `destroy_process_group()`, with the sub-group
enlarged so the rendezvous has more pairs and a wider spread between
first and last rank to finish. It is green. That is evidence *against*
the specific causal story, not for it.

By the rule of three, 0 failures in 242 runs puts the 95% upper bound on
the per-run failure rate at ~1.2%, and 1% is already in mild tension
with the data. **A green CI run on this PR is therefore not evidence
that anything was fixed** — at p ≈ 1% a single run passes with ~99%
probability even with the bug fully present, and catching it with 95%
confidence would take roughly 300 runs. Please don't read a green
pipeline as validation.

So: treat this as closing a synchronization gap that is **provable from
the torch and gloo sources**, not as a fix for #4193. That issue should
stay open with its `infra` label; infrastructure is not exonerated, and
the runners on this repo demonstrably kill jobs mid-run.

On the change itself: the barrier is on the parent group, which every
rank reaches because `Split()` is already collective on it (it opens
with an `allgather`). So it cannot deadlock — including when splitting
an existing sub-group — and it adds no device requirement beyond what
that `allgather` already imposes.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved communicator splitting to synchronize all processes before
returning the new subgroup.
* Ensures split operations behave consistently with MPI-style
communication semantics.

* **Tests**
* Added coverage verifying synchronization occurs on the parent
communicator during subgroup creation.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [10f7e14](https://github.com/flashinfer-ai/flashinfer/commit/10f7e1474a83333c734940bb9198327a62ff7a11)

- **作者**: Alex Yang
- **时间**: 2026-09-11T23:48:59Z
- **提交信息**: fix(moe): accept mxfp8's flat linear activation-scale layout in the MoE autotuner (#4943)

<!-- .github/pull_request_template.md -->

## 📌 Description

The MoE autotuner asserted that `hidden_states_scale`'s dim 0 is the
token count. That is false for the linear MXFP8 layout — the buffer is
flat, holding `num_tokens * (hidden_size / sf_block_size)` elements — so
any caller passing it aborted before a single kernel ran:

```
AssertionError: hidden_states_scale shape (96,) does not match expected layout (num_tokens=1, ...)
  flashinfer/fused_moe/core.py:2042  _make_tuning_config
  flashinfer/fused_moe/core.py:2035  _dynamic_dim
```

This blocked TensorRT-LLM from using the FlashInfer MoE backend for
GPT-OSS entirely, reproduced on a B200 with TRT-LLM 1.3.0rc25.

## Root cause: a non-uniform scale-layout convention

The library has no single convention for how a quantizer returns block
scales:

| producer | activation scale |
|---|---|
| `mxfp8_quantize(..., is_sf_swizzled_layout=False)` | **flat 1-D**,
`num_tokens * hidden_size // 32` |
| `nvfp4_quantize` / `fp4_quantize` | 2-D (or a swizzled buffer) |

So **the flat linear layout is currently mxfp8-specific** — that is the
state of the tree today, not a designed contract. Consumers have each
grown their own assumption about which one they get, and the ones
written against the FP4 shape break when handed the mxfp8 one.

This is not the first time it has bitten. #3455 raised exactly this
question and named it in the same terms: *"`nvfp4_quantize` returns a 2D
scale, `mxfp8_quantize` returns a 1D-flat scale"* — there it broke the
cuDNN `bmm_mxfp8` descale; here it breaks the MoE autotuner.

**Backward compatibility / why the consumer is fixed, not the
producer.** #3455's fix (landed as #3489) is the precedent: it
recomputed the correct 3-D descriptor *from* the flat buffer, and was
explicitly *"pure shape/stride metadata — no data movement, **no
quantizer change**"*. This PR follows the same shape one layer over:
`ConstraintSpec` derives the extent the autotuner needs from the flat
buffer, rather than changing `mxfp8_quantize` or requiring callers to
reshape. Changing the producer to return 2-D would be the breaking
option — it would invalidate every current caller, including the cuDNN
path that now depends on flat, and the in-repo MoE tests that reshape it
themselves.

The producer cannot simply be changed to match, and the reason is on the
record in #3457: *"We can't just flip the shape (vLLM/SGLang reshape the
1D buffer themselves)"* — external consumers depend on the current flat
form.

**#3457 is the structural fix for this class and is already in flight**
(open, not yet on `main`): it adds an opt-in `rank_preserving` flag so
the scale's rank mirrors the input — 2-D → 2-D `[M_pad, K_pad]` matching
nvfp4, 3-D → per-batch-padded — with a migration path before any default
changes.

This PR is complementary, not a competing approach:

- #3457's default is **today's flat behavior**, so the MoE autotuner
keeps receiving flat scales even after it lands. This fix is required
either way.
- The code here already handles the 2-D layout, so if the default is
ever flipped, both forms work and nothing here needs revisiting.

The change is therefore a pure relaxation: what worked before still
works, and a layout that previously crashed now runs.

**The C++ was never the problem.** `args->hidden_states_scale` is a bare
`void*` (`include/flashinfer/trtllm/fused_moe/runner.h:316`),
`FP4BlockScaleLauncher::check_moe()` only tests `has_value()`, and the
FFI derives the SF vector size from `numel()` alone
(`csrc/trtllm_fused_moe_kernel_launcher.cu:4218-4221`). Flat and
`[num_tokens, K]` are byte-identical to it, so the assertion — not the
kernel — was wrong. FlashInfer's own `mxfp8_quantize(...,
is_sf_swizzled_layout=False)` returns this flat layout; every in-repo
caller happens to reshape to `[num_tokens, -1]` first, which is why CI
never caught it.

**Why not simply `return 0` for the flat tensor.** That would have been
worse than the crash. The autotuner writes a bucket's token count
*verbatim* into a dynamic dim (`AutoTuner._create_tensor_like`), so
profiling bucket `B` would build a `(B,)` scale while the kernel indexes
`B * sf_per_token` elements — a silent out-of-bounds device read.
Instead this uses `ConstraintSpec`, the mechanism already used for the
swizzled MXFP8 activation scale in `runners.py`, to derive the extent as
`hidden_states.shape[0] * sf_per_token`.

Only the linear layout is accepted: the implied SF vector size must be
16 (NvFp4) or 32 (Mx*), matching what the C++ accepts downstream. A
padded 128x4-swizzled buffer implies some other vector size, so it is
rejected early with an actionable message rather than silently
mis-sized. **DeepSeekFp8, whose 2-D layout the C++ genuinely requires,
is untouched.**

## 🔍 Related Issues

Found while validating #2482 (issue #2372), but independent of it — this
is a pre-existing bug on `main`, introduced by #4106 (distribution-aware
autotuning), confirmed via `git log -L
2015,2050:flashinfer/fused_moe/core.py`.

**Prior art, same root cause, different consumer.** #3455 (closed) hit
the identical asymmetry from the GEMM side — its description names it
directly: *"`nvfp4_quantize` returns a 2D scale, `mxfp8_quantize`
returns a 1D-flat scale"*. There the flat buffer broke the cuDNN
`bmm_mxfp8` override-shape descale; here it breaks the MoE autotuner's
`_dynamic_dim`.

- #3455's substantive fix **already landed** via #3489
(`_calculate_block_scale_dims`, on `main` at `gemm_base.py:3823`), so
the GEMM path is fine. Nothing that landed touches `fused_moe/core.py`,
which is why this bug is still live — the assertion reproduces on
current `main`.
- #3455's *second* commit — rejecting non-swizzled scales via a numel
check — was **deliberately dropped**, and #3882 handled the concern
differently. That decision constrains this PR too; see Reviewer Notes.

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

`tests/moe/test_moe_autotune_flat_act_scale.py` is **CPU-only** (the JIT
module is mocked), so unlike the SM100-gated MoE tests it actually
executes in public CI. It covers acceptance of the flat layout and — the
important one — that profiling scales the extent by `sf_per_token`
rather than collapsing it to the bucket size.

Validated on a B200 (SM100):

- 8/8 new unit tests pass; they fail on unmodified `main` with the
`AssertionError` above.
- GPT-OSS-20b through TensorRT-LLM's FlashInfer MoE backend scores
20/20, identical to the native trtllm backend.
- TensorRT-LLM's own
`TestGPTOSS::test_w4_1gpu[v2_kv_cache-True-True-trtllm-auto]` (GSM8K on
gpt-oss-120b) passes end to end: evaluated accuracy 89.92 against their
reference threshold of 85.0.

## Reviewer Notes

- The fix is verifiable entirely in this repo's CI — no TensorRT-LLM
needed.
- **The `sf_per_token` check is a malformed-input guard, not a layout
discriminator.** #3455 measured that linear and 128x4-swizzled 1-D
scales have identical `numel` whenever `(b·m) % 128 == 0`, i.e. they are
indistinguishable at the API boundary — which is why a numel-based guard
was dropped there. This PR does not repeat that claim (`dd5fda2e`
corrects an earlier comment of mine that did). The ambiguity is harmless
*here* for a reason specific to this use: `sf_per_token` only ever
**sizes a profiling buffer** and never interprets data. When the numels
coincide the derived value equals the linear one and the buffer is
correct; when they do not, the swizzled buffer is strictly larger, so
the check either fires or the buffer is over-sized — safe either way.
- If a future consumer genuinely needs to tell linear from swizzled
apart, that wants an explicit layout tag rather than a third attempt to
infer it from shape.
- The subtle part is the `ConstraintSpec` choice, not the relaxed
assertion. `test_flat_act_scale_profiles_scale_with_sf_per_token` is the
test that guards the silent-OOB failure mode; it is the one worth
reading closely.
- `pre-commit run --all-files` passes clean on the whole repo, with no
hook rewrites.
- AI-assisted: investigation, fix and adversarial verification by Claude
Opus.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **New Features**
- Added support for flat, one-dimensional activation scale buffers in
FP4 MoE workflows.
- Added an explicit activation scale layout option for FP4 MoE
operations.
- Linear scale-factor layouts no longer require token-count alignment
restrictions.

- **Bug Fixes**
- Improved autotuning and validation for sizing and profiling flat
activation scales.
- Added clearer validation for unsupported layouts and malformed scale
buffers.

- **Deprecation**
- Omitting the activation scale layout infers the linear layout and
emits a deprecation warning.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [561f5af](https://github.com/flashinfer-ai/flashinfer/commit/561f5af703654f4b770186a848c1b46d6a7ac512)

- **作者**: eigen
- **时间**: 2026-09-11T23:48:26Z
- **提交信息**: feat(cake_diffusion): add SM100a support to MiniMax-H3 BF16 pre-attention (#5137)

Add SM100a support to the MiniMax-H3 BF16 pre-attention implementation
merged in #4690, while retaining SM103a support. The runtime accepts
compute capability 10.0 or 10.3, and the cached JIT module contains both
native targets with the existing precise-math flags. CUDA 12.9 remains
the minimum.

### Measured speedup vs baseline

These CUPTI/cold-L2 measurements compare the exported fused operator
with the segmented BF16 baseline, including input RMSNorm, indexed
AdaLN, three BF16 projections, Q/K RMSNorm, partial NeoX RoPE, packing,
and the final D2D copy. Speedup is **baseline latency / exported
latency**; host setup and weight packing are outside timing.

| GPU | Scope | Baseline (ms) | Exported fused operator (ms) | Speedup
vs baseline |
|---|---|---:|---:|---:|
| B200 / SM100 | Primary M4824/P8 | 2.905457 | 2.332705 | **1.245531×**
|
| GB300 / SM103 | Primary M4824/P8 | 2.641840 | 2.129152 | **1.240794×**
|
| B200 / SM100 | All 24 production centers: geometric mean | 11.276954 |
10.747696 | **1.049244×** |
| GB300 / SM103 | All 24 production centers: geometric mean | 10.168333
| 9.892297 | **1.027904×** |

All 24 centers are included: SM100 has 17 faster / 7 slower shapes;
SM103 has 13 faster / 11 slower shapes. Minimum speedups are 0.910050×
and 0.886623× respectively. Full per-shape baseline/source/export
timings, source/export parity, hardware provenance and measurement
durations remain below.

The public API, output layout, BF16 round points, and authored kernel
schedule are preserved. Regenerated CUDA uses updated warp/lane lowering
and a CTA barrier-wait suspend hint. Current SM103 correctness and
performance measurements below cover this generated code; previous
performance results are not reused as new evidence.

### Correctness and integration validation

All completed public full-suite runs execute 67 tests, including the
complete 44-shape inventory, at BF16 atol=rtol=0.01. Exact public source
and every setup/call/teardown phase were checked.

| GPU / CUDA | Passed / skipped | JUnit tests (s) | Validation payload
(s) | Separate source staging (s) | Physical turnaround (s) |
|---|---:|---:|---:|---:|---:|
| B200 / 12.9 | 67 / 0 | 12.259 | 256.949 | 57.872 | 448.904 |
| B200 / 13.0 | 67 / 0 | 6.956 | 191.337 | reused validated staging |
589.914 |
| GB300 / 12.9 | 67 / 0 | 33.155 | 100.490 | included in payload |
299.490 |
| GB300 / 13.0 | 67 / 0 | 34.350 | 90.880 | included in payload |
263.450 |

Both B200 runs used Python 3.10.21 and driver 580.82.07 on the same GPU.
CUDA 12.9 used NVCC 12.9.41, PyTorch 2.13.0+cu129 and image
`flashinfer/flashinfer-ci-cu129@sha256:b0181ed5707140c87a06834ca07676f20e1c212c2c63e58712a8cf6dfdf312c6`;
CUDA 13.0 used NVCC 13.0.88, PyTorch 2.13.0+cu130 and image
`flashinfer/flashinfer-ci-cu130@sha256:0b9fd0713b0b92e36ad8fe4654f702710724e851ce30d91c07dde2f81dcad415`.
Their pytest subprocesses took 17.223 and 10.596 seconds. CUDA 13.0
physical turnaround includes time queued behind the comparative
benchmark. The GB300 public runs used NVCC 12.9.41 and 13.0.88 with
corresponding PyTorch 2.13.0 builds. These are suite and orchestration
durations, not kernel timing.

Source, exported implementation, and explicit segmented baseline each
passed all 44 shapes on both GPUs with no failed or skipped shapes and
atol=rtol=0.01; source/export outputs matched on every row.

| Source/export correctness | Rows per arm | Correctness subprocess (s)
| Setup/validation payload (s) | Physical turnaround (s) |
|---|---:|---:|---:|---:|
| SM100 | 44 / 44 / 44 | 52.835 | 655.402 | 887.620 |
| SM103 | 44 / 44 / 44 | 41.000 | 49.630 | 212.790 |

Generated-export checks passed: 39 tests, zero skips; both native
targets compiled with NVRTC; canonical freeze/replay and Python
lint/format checks passed. The check payload took 38.30 seconds, with
864.30 seconds of physical turnaround. Exact-head CPU/API validation
also passed 17 tests, collecting all 67 tests and 44 shapes; its 50 GPU
skips are superseded by the hardware runs above.

Current-head [PR Test
CI](https://github.com/flashinfer-ai/flashinfer/actions/runs/34595426448)
passed all 14 jobs: seven JIT test jobs, four AOT Build Import jobs
across x64/arm64 and CUDA 12.9/13.0, plus Permission Check, Setup, and
Test Results Summary. Each JIT/AOT job ran its test step successfully.
Workflow turnaround was 3h 33m 19s. This CI matrix itself does not
execute SM100. Current-head pre-commit and documentation checks also
passed.

### Registered regression and bounded sanitizers

| Gate | SM100 | SM103 |
|---|---|---|
| Registered GPU e2e | PASS: one pytest case, eight shapes; 3.481 s
testcase / 9.193 s JUnit suite | PASS: one pytest case, eight shapes;
3.479 s JUnit |
| Registered CUPTI benchmark | PASS: 2.3245 ms against 2.55728 ms
ceiling; 30.989 s subprocess | PASS: 2.1529 ms against 3.1000 ms
ceiling; 28.20 s subprocess |
| NVIDIA synccheck | PASS: 0 errors, 0 warnings; one command, 10
launches, 15.459 s | PASS: 0 errors, 0 warnings, 10 launches, 13.53 s |
| NVIDIA racecheck | PASS: 0 errors, 0 warnings; 10 launch positions
checked across 10 commands, 16.185–16.676 s each | PASS: 0 errors, 0
warnings, 10 launches, 18.52 s |

The registered SM100 e2e retry passed after private pytest 9.1.1
dependency setup. Its one case invokes the unchanged eight-shape
registration, spanning all P routes, the active center, tails, and small
rows; zero failures or skips. Testcase time was 3.481 seconds, JUnit
suite time 9.193 seconds, pytest subprocess 10.993 seconds, dependency
setup/test payload 21.688 seconds, and physical turnaround 102.832
seconds.

SM100 synccheck uses one command covering the full ten-launch worker.
SM100 racecheck uses ten separate commands. Every racecheck command
executes the unchanged registered worker: the same ten candidate calls,
in the same order, over M128/P8 and M129/P8, each with valid inputs
followed by AdaLN index sentinels -1, 9, -2147483648, and 2147483647.

Command `i` retains the candidate kernel-name filter and adds
`--launch-skip i --launch-count 1` for `i=0..9`. NVIDIA documents that
these counters advance only for launches matching the kernel filters.
[Compute Sanitizer command-line
options](https://docs.nvidia.com/compute-sanitizer/ComputeSanitizer/index.html).
The batch therefore executes **100 candidate calls in total and
instruments 10**, covering each of the ten required launch positions
once. Each command preserves the 19-second TERM timeout plus one-second
kill grace; registry preparation and report processing occur outside
that cap.

All ten racecheck commands completed with zero errors and zero warnings.
Their combined command time was 163.657 seconds; the batch used 228.708
seconds payload and 301.177 seconds physical turnaround. The completed
SM103 registered e2e/benchmark batch used 76.09 seconds payload and
149.65 seconds physical turnaround; its separate successful sanitizer
batch used 43.44 seconds payload and 115.40 seconds physical turnaround.

The initial registered batch used 79.026 seconds payload and 687.239
seconds physical turnaround, including its queue behind other
validation. Its e2e command stopped before testing because pytest was
missing, and its unsplit racecheck command reached the 19-second cutoff.
Those incomplete results are superseded by the successful e2e retry and
the complete racecheck coverage across ten bounded commands above. The
successful initial benchmark and synccheck results are retained.

The initial registered SM100 CUPTI measurement was 2.3248 ms (30.482 s
subprocess). It established the existing 110% latency ceiling at 2.55728
ms. The subsequent registered check passed at 2.3245 ms with
`backend_actual=cupti`; the CLI displays the ceiling rounded to 2.5573
ms. Confirmation took 30.989 seconds for the benchmark subprocess,
32.407 seconds for the payload, and 115.041 seconds of physical
turnaround. This confirms the newly established ceiling and is not an
improvement claim against a preexisting SM100 baseline.

### Measured hardware and software

Each architecture's source/export comparison used one visible GPU. GPU
identity came from the measured process, and both arms used the same
device.

| Field | SM100 | SM103 |
|---|---|---|
| GPU | NVIDIA B200 | NVIDIA GB300 |
| Host | `nsc-svg-slurm-1-gpu-62` | `nvl72d232-T18` |
| GPU UUID | `GPU-9a6fd126-b31c-8fd5-5694-dac2b52e7e60` |
`GPU-ec223e3c-a093-cba2-b83d-7eb979f080ed` |
| Compute capability / CPU | 10.0 / x86_64 | 10.3 / aarch64 |
| Driver | 580.82.07 | 580.159.03 |
| Framework CUDA / NVCC | 13.3 / 13.3.33 | 13.3 / 13.3.33 |
| Python / PyTorch | 3.12.3 / 2.13.0a0+8145d630e8.nv26.06 | 3.12.3 /
2.13.0a0+8145d630e8.nv26.06 |
| CUPTI Python | 13.0.1 | 13.0.1 |
| Container reference | `nvcr.io/nvidia/pytorch:26.06-py3` |
`nvcr.io/nvidia/pytorch:26.06-py3` |
| Public generated-source revision |
`f617403f534c0bf9f2a2076c81fa94a6fa18e594` |
`f617403f534c0bf9f2a2076c81fa94a6fa18e594` |

The recorded compiler identity is NVCC; separate NVRTC/ptxas versions
and the benchmark container digest were not retained in these summaries.
Both runs used the recorded clock policy with no imposed minimum SM
frequency and no steady-state-clock requirement. BF16 reduced-precision
matmul reduction and TF32 framework flags were enabled for the
reference. The measurements establish current behavior on each GPU;
cross-GPU latency differences are not an optimization claim.

### Comparative CUPTI/cold-L2 evidence

These are whole-operator GPU timings: the fused source/export kernel
versus the explicit segmented reference chain. They are not serving
latency. Hidden width is 5376, with 56 heads of dimension 128 and
partial 96-channel split-half NeoX RoPE. Inputs and outputs are BF16;
output is caller-owned and destination-major. The baseline includes
input RMSNorm, indexed AdaLN, three separate BF16 projections, Q/K
RMSNorm, RoPE, packing and the final D2D copy. Host setup and weight
packing are outside timing.

All 24 production centers use shared inputs and interleaved
forward/reverse baseline/source/export ordering. The independent
export-parity comparison uses three adjacent closed ABBA/BAAB groups on
the same GPU and process, one CUPTI session per reportable group. Warmup
is 100 ms and measurement is 500 ms with cold L2; the recorded GPU
activity scope includes kernels and D2D copies. Baseline comparison and
export parity are separate experiments. No production row is excluded;
the other 20 shapes are correctness-only.

Geometric-mean latencies and ratios use the same complete row set and
unrounded per-row measurements. `ΔB−S` and `ΔB−E` mean baseline minus
source/export latency; a positive delta saves time. B/S and B/E below
use the three-arm group.

| Architecture | Rows | Baseline geomean ms | Source geomean ms | Export
geomean ms | B/S geomean | B/E geomean | Minimum B/E | Export faster /
slower |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| SM100 | 24 | 11.276954 | 10.717868 | 10.747696 | 1.052164× | 1.049244×
| 0.910050× | 17 / 7 |
| SM103 | 24 | 10.168333 | 9.853035 | 9.892297 | 1.032000× | 1.027904× |
0.886623× | 13 / 11 |

At the primary M4824/P8 center, SM100 baseline/source/export are
**2.905457 / 2.319617 / 2.332705 ms**, giving **1.245531×**
baseline/export speedup. SM103 is **2.641840 / 2.122128 / 2.129152 ms**,
giving **1.240794×**. The worst B/E shape on both GPUs is M48768/P1:
**0.910050×** on SM100 and **0.886623×** on SM103. These slower shapes
remain visible in the full tables.

<details>
<summary>SM100: all 24 production-center measurements
(milliseconds)</summary>

| M | P | Baseline ms | Source ms | Export ms | ΔB−S ms | ΔB−E ms | B/S
| B/E | S/E paired |
|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 33472 | 1 | 17.535125 | 18.877477 | 18.789269 | -1.342351 | -1.254144
| 0.928891× | 0.933252× | 1.004919× |
| 16736 | 2 | 9.646046 | 9.304622 | 9.401678 | +0.341424 | +0.244368 |
1.036694× | 1.025992× | 0.990011× |
| 8368 | 4 | 4.917423 | 4.222208 | 4.205136 | +0.695215 | +0.712288 |
1.164657× | 1.169385× | 1.004856× |
| 4184 | 8 | 2.545408 | 2.086225 | 2.090576 | +0.459184 | +0.454832 |
1.220103× | 1.217563× | 0.996370× |
| 38592 | 1 | 20.184677 | 21.747893 | 21.671413 | -1.563216 | -1.486736
| 0.928121× | 0.931396× | 1.003495× |
| 19296 | 2 | 11.135155 | 10.839668 | 10.956019 | +0.295488 | +0.179137
| 1.027260× | 1.016351× | 0.989551× |
| 9648 | 4 | 5.648274 | 5.069185 | 5.039362 | +0.579089 | +0.608912 |
1.114237× | 1.120831× | 1.004044× |
| 4824 | 8 | 2.905457 | 2.319617 | 2.332705 | +0.585840 | +0.572752 |
1.252559× | 1.245531× | 0.996150× |
| 48768 | 1 | 25.563467 | 27.638379 | 28.090187 | -2.074912 | -2.526720
| 0.924926× | 0.910050× | 0.983925× |
| 24384 | 2 | 14.080998 | 13.812662 | 13.743669 | +0.268337 | +0.337329
| 1.019427× | 1.024544× | 1.005030× |
| 12192 | 4 | 7.088963 | 6.496595 | 6.474147 | +0.592368 | +0.614816 |
1.091181× | 1.094965× | 1.004360× |
| 6096 | 8 | 3.621010 | 2.980338 | 3.002945 | +0.640672 | +0.618065 |
1.214966× | 1.205820× | 0.992756× |
| 58944 | 1 | 31.273039 | 33.236783 | 33.119104 | -1.963744 | -1.846065
| 0.940917× | 0.944260× | 1.004196× |
| 29472 | 2 | 16.972664 | 16.762648 | 16.662199 | +0.210016 | +0.310465
| 1.012529× | 1.018633× | 1.006652× |
| 14736 | 4 | 8.519892 | 8.040532 | 8.006403 | +0.479361 | +0.513489 |
1.059618× | 1.064135× | 1.005031× |
| 7368 | 8 | 4.319714 | 3.717106 | 3.696130 | +0.602608 | +0.623585 |
1.162118× | 1.168713× | 1.003843× |
| 74240 | 1 | 39.172706 | 41.917043 | 42.614900 | -2.744338 | -3.442194
| 0.934529× | 0.919226× | 0.983804× |
| 37120 | 2 | 21.354713 | 21.067401 | 21.411657 | +0.287312 | -0.056944
| 1.013638× | 0.997341× | 0.984040× |
| 18560 | 4 | 10.722389 | 10.516453 | 10.665989 | +0.205936 | +0.056400
| 1.019582× | 1.005288× | 0.985339× |
| 9280 | 8 | 5.419939 | 4.747906 | 4.732499 | +0.672033 | +0.687441 |
1.141543× | 1.145260× | 1.004780× |
| 109952 | 1 | 64.599660 | 62.539851 | 63.501707 | +2.059809 | +1.097953
| 1.032936× | 1.017290× | 0.983548× |
| 54976 | 2 | 31.963918 | 31.152366 | 31.020350 | +0.811552 | +0.943568
| 1.026051× | 1.030418× | 1.004349× |
| 27488 | 4 | 15.835446 | 15.677047 | 15.837270 | +0.158399 | -0.001824
| 1.010104× | 0.999885× | 0.990130× |
| 13744 | 8 | 7.984419 | 7.426659 | 7.393219 | +0.557760 | +0.591200 |
1.075102× | 1.079965× | 1.004789× |

</details>

<details>
<summary>SM103: all 24 production-center measurements
(milliseconds)</summary>

`ΔB−S` and `ΔB−E` are baseline minus source/export latency; positive
values save time. B/S and B/E use the three-arm measurement group. S/E
paired comes from the independent three-group parity experiment.

| M | P | Baseline ms | Source ms | Export ms | ΔB−S ms | ΔB−E ms | B/S
| B/E | S/E paired |
|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 33472 | 1 | 15.818704 | 17.377280 | 17.359104 | -1.558576 | -1.540400
| 0.910310× | 0.911263× | 1.001078× |
| 16736 | 2 | 8.755232 | 8.563264 | 8.618576 | +0.191968 | +0.136656 |
1.022418× | 1.015856× | 0.993659× |
| 8368 | 4 | 4.485312 | 3.866032 | 3.860384 | +0.619280 | +0.624928 |
1.160185× | 1.161882× | 1.000949× |
| 4184 | 8 | 2.357600 | 1.947616 | 1.951536 | +0.409984 | +0.406064 |
1.210506× | 1.208074× | 0.997560× |
| 38592 | 1 | 18.184224 | 20.010400 | 19.991696 | -1.826176 | -1.807472
| 0.908739× | 0.909589× | 1.000738× |
| 19296 | 2 | 10.044096 | 10.017408 | 10.095744 | +0.026688 | -0.051648
| 1.002664× | 0.994884× | 0.992396× |
| 9648 | 4 | 5.109200 | 4.495184 | 4.488960 | +0.614016 | +0.620240 |
1.136594× | 1.138170× | 1.001152× |
| 4824 | 8 | 2.641840 | 2.122128 | 2.129152 | +0.519712 | +0.512688 |
1.244901× | 1.240794× | 0.996380× |
| 48768 | 1 | 22.944111 | 25.455952 | 25.878096 | -2.511841 | -2.933985
| 0.901326× | 0.886623× | 0.983811× |
| 24384 | 2 | 12.684752 | 12.652752 | 12.632144 | +0.032000 | +0.052608
| 1.002529× | 1.004165× | 1.001458× |
| 12192 | 4 | 6.429568 | 5.999984 | 5.992000 | +0.429584 | +0.437568 |
1.071598× | 1.073025× | 1.001535× |
| 6096 | 8 | 3.291536 | 2.787984 | 2.801648 | +0.503552 | +0.489888 |
1.180615× | 1.174857× | 0.996001× |
| 58944 | 1 | 27.779600 | 30.587968 | 30.568928 | -2.808368 | -2.789328
| 0.908187× | 0.908753× | 1.000538× |
| 29472 | 2 | 15.266752 | 15.482512 | 15.449472 | -0.215760 | -0.182720
| 0.986064× | 0.988173× | 1.002299× |
| 14736 | 4 | 7.731024 | 7.348640 | 7.340048 | +0.382384 | +0.390976 |
1.052035× | 1.053266× | 1.001659× |
| 7368 | 8 | 3.942400 | 3.475168 | 3.472256 | +0.467232 | +0.470144 |
1.134449× | 1.135400× | 1.001207× |
| 74240 | 1 | 34.880720 | 38.677264 | 39.311344 | -3.796544 | -4.430624
| 0.901840× | 0.887294× | 0.983831× |
| 37120 | 2 | 19.246944 | 19.438160 | 19.754640 | -0.191216 | -0.507696
| 0.990163× | 0.974300× | 0.983844× |
| 18560 | 4 | 9.660528 | 9.637408 | 9.770336 | +0.023120 | -0.109808 |
1.002399× | 0.988761× | 0.986275× |
| 9280 | 8 | 4.926128 | 4.369984 | 4.365456 | +0.556144 | +0.560672 |
1.127265× | 1.128434× | 1.001213× |
| 109952 | 1 | 55.166416 | 57.228320 | 58.174464 | -2.061904 | -3.008048
| 0.963971× | 0.948293× | 0.983680× |
| 54976 | 2 | 28.518991 | 28.473712 | 28.437648 | +0.045279 | +0.081343
| 1.001590× | 1.002860× | 1.001077× |
| 27488 | 4 | 14.329072 | 14.395680 | 14.509088 | -0.066608 | -0.180016
| 0.995373× | 0.987593× | 0.992220× |
| 13744 | 8 | 7.210127 | 6.759776 | 6.753519 | +0.450352 | +0.456608 |
1.066622× | 1.067610× | 1.001550× |

</details>

### Separate exported-artifact parity

The loaded generated entrypoint is
`kernel_minimax_h3_bf16_pre_attention_destination_major_005f_v1`, from
the public dual-target implementation at
`f617403f534c0bf9f2a2076c81fa94a6fa18e594`. All 24 source/export pairs
on each GPU have matching activity signatures and pass the existing
export/source band [1/1.03, 1.03].

These source/export absolute latencies come from the separate paired
experiment. S/E means source divided by export. Source-first and
export-first ratios preserve the two ordering directions. The
source/export drift columns are the per-arm median endpoint drifts
across the three closed groups, as percentages. PASS is the immediate
existing-band result; it does not compare against the segmented
baseline.

| Architecture | Rows | Paired source geomean ms | Paired export geomean
ms | Paired S/E geomean | Existing-band passes | Exclusions |
|---|---:|---:|---:|---:|---:|---|
| SM100 | 24 | 10.707443 | 10.736484 | 0.997295× | 24 / 24 | none |
| SM103 | 24 | 9.853649 | 9.892576 | 0.996065× | 24 / 24 | none |

<details>
<summary>SM100: separate source/export parity, all 24 centers</summary>

| M | P | Source ms | Export ms | S/E | Source-first S/E | Export-first
S/E | Source drift % | Export drift % | Verdict |
|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| 33472 | 1 | 18.873262 | 18.780880 | 1.004919× | 1.004824× | 1.004766×
| 0.041125 | 0.031444 | PASS |
| 16736 | 2 | 9.303708 | 9.397581 | 0.990011× | 0.989991× | 0.990112× |
0.007212 | 0.006811 | PASS |
| 8368 | 4 | 4.214767 | 4.194399 | 1.004856× | 1.005117× | 1.005134× |
0.014431 | 0.043468 | PASS |
| 4184 | 8 | 2.081856 | 2.089440 | 0.996370× | 0.996423× | 0.996523× |
0.046120 | 0.021391 | PASS |
| 38592 | 1 | 21.746804 | 21.671059 | 1.003495× | 1.003694× | 1.003635×
| 0.074798 | 0.017567 | PASS |
| 19296 | 2 | 10.833588 | 10.947987 | 0.989551× | 0.989548× | 0.989552×
| 0.012993 | 0.011246 | PASS |
| 9648 | 4 | 5.061506 | 5.041121 | 1.004044× | 1.004040× | 1.003912× |
0.012666 | 0.017135 | PASS |
| 4824 | 8 | 2.318161 | 2.327122 | 0.996150× | 0.996343× | 0.995886× |
0.044174 | 0.054995 | PASS |
| 48768 | 1 | 27.626795 | 28.078138 | 0.983925× | 0.983907× | 0.983903×
| 0.023112 | 0.009059 | PASS |
| 24384 | 2 | 13.811077 | 13.741958 | 1.005030× | 1.005194× | 1.005060×
| 0.021537 | 0.003027 | PASS |
| 12192 | 4 | 6.498499 | 6.470291 | 1.004360× | 1.004425× | 1.004461× |
0.072416 | 0.086091 | PASS |
| 6096 | 8 | 2.973346 | 2.995041 | 0.992756× | 0.992829× | 0.992716× |
0.061359 | 0.019236 | PASS |
| 58944 | 1 | 33.204736 | 33.065984 | 1.004196× | 1.004283× | 1.004043×
| 0.017918 | 0.013845 | PASS |
| 29472 | 2 | 16.762040 | 16.651272 | 1.006652× | 1.006520× | 1.006474×
| 0.027091 | 0.032467 | PASS |
| 14736 | 4 | 8.038324 | 7.998084 | 1.005031× | 1.005123× | 1.004959× |
0.040012 | 0.032999 | PASS |
| 7368 | 8 | 3.710962 | 3.696754 | 1.003843× | 1.003940× | 1.003614× |
0.015534 | 0.039401 | PASS |
| 74240 | 1 | 41.903542 | 42.593366 | 0.983804× | 0.983744× | 0.983872×
| 0.013591 | 0.011193 | PASS |
| 37120 | 2 | 21.061498 | 21.403082 | 0.984040× | 0.983922× | 0.984085×
| 0.012160 | 0.009564 | PASS |
| 18560 | 4 | 10.511173 | 10.667573 | 0.985339× | 0.985292× | 0.985326×
| 0.009732 | 0.016520 | PASS |
| 9280 | 8 | 4.748562 | 4.725970 | 1.004780× | 1.004755× | 1.004647× |
0.014152 | 0.006750 | PASS |
| 109952 | 1 | 62.023280 | 63.060734 | 0.983548× | 0.983541× | 0.983587×
| 0.005677 | 0.012382 | PASS |
| 54976 | 2 | 31.122685 | 30.987933 | 1.004349× | 1.004307× | 1.004322×
| 0.029101 | 0.022406 | PASS |
| 27488 | 4 | 15.674999 | 15.831255 | 0.990130× | 0.990127× | 0.990108×
| 0.006842 | 0.030516 | PASS |
| 13744 | 8 | 7.422531 | 7.387156 | 1.004789× | 1.004964× | 1.004628× |
0.040090 | 0.063712 | PASS |

</details>

<details>
<summary>SM103: separate source/export parity, all 24 centers</summary>

| M | P | Source ms | Export ms | S/E | Source-first S/E | Export-first
S/E | Source drift % | Export drift % | Verdict |
|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| 33472 | 1 | 17.376209 | 17.357489 | 1.001078× | 1.000995× | 1.001071×
| 0.011416 | 0.051611 | PASS |
| 16736 | 2 | 8.562864 | 8.617504 | 0.993659× | 0.993653× | 0.993648× |
0.015130 | 0.010775 | PASS |
| 8368 | 4 | 3.864400 | 3.860736 | 1.000949× | 1.001019× | 1.001310× |
0.024026 | 0.089113 | PASS |
| 4184 | 8 | 1.949088 | 1.953856 | 0.997560× | 0.997491× | 0.997459× |
0.284396 | 0.269769 | PASS |
| 38592 | 1 | 20.010368 | 19.995617 | 1.000738× | 1.000728× | 1.000671×
| 0.019670 | 0.006321 | PASS |
| 19296 | 2 | 10.018336 | 10.095104 | 0.992396× | 0.992344× | 0.992400×
| 0.013413 | 0.029794 | PASS |
| 9648 | 4 | 4.493200 | 4.488032 | 1.001152× | 1.001096× | 1.001610× |
0.046269 | 0.020671 | PASS |
| 4824 | 8 | 2.122752 | 2.130464 | 0.996380× | 0.996368× | 0.996430× |
0.194113 | 0.100534 | PASS |
| 48768 | 1 | 25.457328 | 25.876239 | 0.983811× | 0.983860× | 0.983780×
| 0.001259 | 0.035485 | PASS |
| 24384 | 2 | 12.652912 | 12.634495 | 1.001458× | 1.001461× | 1.001370×
| 0.017831 | 0.012410 | PASS |
| 12192 | 4 | 6.001072 | 5.991872 | 1.001535× | 1.001482× | 1.001402× |
0.012265 | 0.018159 | PASS |
| 6096 | 8 | 2.789792 | 2.800992 | 0.996001× | 0.996086× | 0.995970× |
0.016058 | 0.034264 | PASS |
| 58944 | 1 | 30.586655 | 30.570223 | 1.000538× | 1.000631× | 1.000617×
| 0.004813 | 0.008165 | PASS |
| 29472 | 2 | 15.483904 | 15.448384 | 1.002299× | 1.002145× | 1.002292×
| 0.020043 | 0.054873 | PASS |
| 14736 | 4 | 7.351120 | 7.338944 | 1.001659× | 1.001574× | 1.001657× |
0.040060 | 0.010465 | PASS |
| 7368 | 8 | 3.476048 | 3.471856 | 1.001207× | 1.001357× | 1.001326× |
0.004602 | 0.019360 | PASS |
| 74240 | 1 | 38.675904 | 39.311536 | 0.983831× | 0.983874× | 0.983850×
| 0.005626 | 0.005456 | PASS |
| 37120 | 2 | 19.436992 | 19.756176 | 0.983844× | 0.983829× | 0.983899×
| 0.007820 | 0.009070 | PASS |
| 18560 | 4 | 9.634976 | 9.769056 | 0.986275× | 0.986231× | 0.986373× |
0.014447 | 0.029648 | PASS |
| 9280 | 8 | 4.370864 | 4.365568 | 1.001213× | 1.001507× | 1.001195× |
0.006224 | 0.016124 | PASS |
| 109952 | 1 | 57.227008 | 58.176447 | 0.983680× | 0.983634× | 0.983686×
| 0.003243 | 0.014135 | PASS |
| 54976 | 2 | 28.471041 | 28.440416 | 1.001077× | 1.001058× | 1.001062×
| 0.013261 | 0.029371 | PASS |
| 27488 | 4 | 14.395824 | 14.508704 | 0.992220× | 0.992210× | 0.992254×
| 0.011559 | 0.012138 | PASS |
| 13744 | 8 | 6.760096 | 6.749632 | 1.001550× | 1.001571× | 1.001419× |
0.026962 | 0.069687 | PASS |

</details>

| Benchmark duration | SM100 (s) | SM103 (s) |
|---|---:|---:|
| Measured GPU samples | 147.082 | 144.837 |
| Benchmark payload | 299.892 | 303.365 |
| End-to-end physical turnaround | 372.353 | 376.583 |

Cache flushing, preparation, and orchestration account for the
difference between measured GPU time, payload time, and physical
turnaround.

### Complete existing shape denominator

The existing 44-row inventory is preserved: 24 production centers
measured for performance on both GPUs, eight aligned neighbors, eight
tail neighbors, and four smoke shapes. Every row passed
source/export/reference correctness at BF16 atol=rtol=0.01 on both
architectures. The table gives every M/P coordinate; head count, head
dimension, dtype, layout, and operator semantics are as defined above.

<details>
<summary>All 44 shapes and their coverage</summary>

| Shape | M | P | Coverage |
|---|---:|---:|---|
| center_p1_4s_m33472 | 33472 | 1 | correctness + performance |
| center_p2_4s_m16736 | 16736 | 2 | correctness + performance |
| center_p4_4s_m8368 | 8368 | 4 | correctness + performance |
| center_p8_4s_m4184 | 4184 | 8 | correctness + performance |
| center_p1_5s_m38592 | 38592 | 1 | correctness + performance |
| center_p2_5s_m19296 | 19296 | 2 | correctness + performance |
| center_p4_5s_m9648 | 9648 | 4 | correctness + performance |
| center_p8_5s_m4824 | 4824 | 8 | correctness + performance |
| center_p1_6s_m48768 | 48768 | 1 | correctness + performance |
| center_p2_6s_m24384 | 24384 | 2 | correctness + performance |
| center_p4_6s_m12192 | 12192 | 4 | correctness + performance |
| center_p8_6s_m6096 | 6096 | 8 | correctness + performance |
| center_p1_8s_m58944 | 58944 | 1 | correctness + performance |
| center_p2_8s_m29472 | 29472 | 2 | correctness + performance |
| center_p4_8s_m14736 | 14736 | 4 | correctness + performance |
| center_p8_8s_m7368 | 7368 | 8 | correctness + performance |
| center_p1_10s_m74240 | 74240 | 1 | correctness + performance |
| center_p2_10s_m37120 | 37120 | 2 | correctness + performance |
| center_p4_10s_m18560 | 18560 | 4 | correctness + performance |
| center_p8_10s_m9280 | 9280 | 8 | correctness + performance |
| center_p1_15s_m109952 | 109952 | 1 | correctness + performance |
| center_p2_15s_m54976 | 54976 | 2 | correctness + performance |
| center_p4_15s_m27488 | 27488 | 4 | correctness + performance |
| center_p8_15s_m13744 | 13744 | 8 | correctness + performance |
| aligned_p1_5s_minus64_m38528 | 38528 | 1 | correctness |
| aligned_p1_5s_plus64_m38656 | 38656 | 1 | correctness |
| aligned_p2_5s_minus32_m19264 | 19264 | 2 | correctness |
| aligned_p2_5s_plus32_m19328 | 19328 | 2 | correctness |
| aligned_p4_5s_minus16_m9632 | 9632 | 4 | correctness |
| aligned_p4_5s_plus16_m9664 | 9664 | 4 | correctness |
| aligned_p8_5s_minus8_m4816 | 4816 | 8 | correctness |
| aligned_p8_5s_plus8_m4832 | 4832 | 8 | correctness |
| tail_p1_5s_minus1_m38591 | 38591 | 1 | correctness |
| tail_p1_5s_plus1_m38593 | 38593 | 1 | correctness |
| tail_p2_5s_minus1_m19295 | 19295 | 2 | correctness |
| tail_p2_5s_plus1_m19297 | 19297 | 2 | correctness |
| tail_p4_5s_minus1_m9647 | 9647 | 4 | correctness |
| tail_p4_5s_plus1_m9649 | 9649 | 4 | correctness |
| tail_p8_5s_minus1_m4823 | 4823 | 8 | correctness |
| tail_p8_5s_plus1_m4825 | 4825 | 8 | correctness |
| smoke_p8_m1 | 1 | 8 | correctness |
| smoke_p8_m127 | 127 | 8 | correctness |
| smoke_p8_m128 | 128 | 8 | correctness |
| smoke_p8_m129 | 129 | 8 | correctness |

</details>

### Reproduction

```bash
FLASHINFER_RUN_FULL_MINIMAX_H3_TESTS=1 python -m pytest tests/diffusion_ops/test_minimax_h3_bf16_pre_attention.py
```


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
  * Added support for CUDA compute capabilities 10.0 and 10.3.
  * Enabled JIT compilation for both SM100a and SM103a architectures.
  * Improved barrier synchronization behavior for supported hardware.

* **Bug Fixes**
  * Expanded runtime compatibility and validation for Blackwell GPUs.
* Updated correctness checks, CUDA graph capture, and invalid-index
handling across supported architectures.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [f1e3f17](https://github.com/flashinfer-ai/flashinfer/commit/f1e3f1739db625de8b432afb2633f0f54dcb4e87)

- **作者**: Alex Yang
- **时间**: 2026-09-11T23:34:33Z
- **提交信息**: Revert "build: raise the nvidia-cudnn-frontend floor to 1.28.0" (#5159)

Reverts flashinfer-ai/flashinfer#5131

### [915e7c4](https://github.com/flashinfer-ai/flashinfer/commit/915e7c49aececa5ba4fdf60ac0f4038ca1455fc1)

- **作者**: Gabriel Wu
- **时间**: 2026-09-11T22:11:20Z
- **提交信息**: feat(sm120): runtime KV row stride + canonical 528B GLM53_NOPE rows + NaN-safe masked gathers in sparse MLA (#5075)

## 📌 Description

Three changes to the SM120 sparse-MLA cache handling, motivated by the
compact-row discussion in flashinfer-ai/flashinfer#5022. This is an
alternative design for the same goals. It also carries follow-up fixes
from community review: cache-view validation hardening and the GLM NoPE
eight-head decode instantiation from ormandj's branch
(lucifer1004/flashinfer#3, retaining the #5022 implementation), and the
calibration-cache invalidation reported by qsang-nv.

**Runtime gmem row stride ("stride is data, not format").** GLM53_NOPE's
packed
payload is 528B/token (512 FP8 values + 4 inline FP32 scales); the 656B
row came
from inheriting vLLM's fp8_ds_mla ABI, whose trailing 128B are RoPE
bytes the
NoPE model never uses. Instead of adding a second layout selected by
shape
sniffing, this PR makes the payload canonical (`bytes_per_token = 528`)
and takes
the gmem row advance as a runtime stride everywhere:

- decode already honored `stride_kv_row`; prefill now derives the
advance from
`stride_kv_block / page_block_size` (no new kernel parameter), and
swapAB
  decouples its smem row stride (528B payload) from the gmem advance.
- A legacy 656B pool (vLLM fp8_ds_mla) and a compact 528B pool are the
same
kernel with a different stride; the payload prefix is identical, so
existing
callers keep working unchanged. Per-token KV storage drops 19.5% for
callers
  that switch to 528B rows.
- Binding validation: inline-scale models accept padded rows (advance >=
width
>= payload, 16B-aligned, blocks contiguous); footer-scale models keep
the
packed-rows requirement. Flat 2D caches must be packed at 528B for
GLM53_NOPE
  (a flat block carries no stride to infer); GLM53_NOPE has no released
  downstream, so this is the last moment the canonical width can flip.
- The cpb calibration store bumps to schema v2 for the flip: a pre-PR
cache
entry persists `bytes_per_chunk = 41984` for glm53_nope and would
silently
overstate the L2 footprint in the cpb guard by ~24%, potentially
excluding
valid candidates. Stale files count as absent and recalibrate on the
next
tuning-mode pass (review feedback from qsang-nv on this PR), and a stale
  file's mtime is remembered so repeated lookups no longer reread it.

**Cache-view validation hardening** (carried from ormandj's review
branch,
lucifer1004/flashinfer#3):

- Flat 2D caches derived the block advance from the dim-1 *size* instead
of
  the real `stride(0)`, so a view with gaps between pages read the wrong
page. The physical block stride is now honored (and must be >= the
packed
  block width).
- Cache origins and block strides must be 16B-aligned (cp.async.bulk);
footer-scale 3D/4D views must keep token rows packed (previously only
the
  row *width* was checked, not the stride).
- GLM53_NOPE H=8 decode now has a dedicated instantiation: the runtime-H
  fallback strides split-K scratch by the 16-head tile while the public
allocator reserves only 8 rows for H=8 (the #5022 eight-head fix,
carried).
H=16 joins the dedicated grid for symmetry with DSV3_2/GLM_NSA — it was
  already correct via runtime-H (its scratch stride equals the true head
  count there), this just drops the runtime loop bounds.



**Universal NaN-safe masked gathers.** Masked (-1) candidates were
clamped to
mutable cache slot 0 in seven places (prefill MG/SG gather + scale
gather,
swapAB gather, decode-v32, decode-dsv4, and the two NVFP4 kernels from
flashinfer-ai/flashinfer#4955). A NaN in that slot leaks into valid
outputs through `0 * NaN` in the value MMA (and `0 * inf` from a
poisoned
0xFF footer scale on footer-scale models). All seven now gather a shared
zero-initialized row (`sparse_mla_zero_row`), which is mbar-compatible
and adds
no synchronization. The NVFP4 case is narrower but real: the masked
scale
load there is explicitly zeroed, which covers the E2M1 NoPE values, but
the
128B BF16 rope tail rides the same clamped pointer with no scale in its
path
(review feedback from qsang-nv on this PR). The property now holds
unconditionally for every model type — no opt-in and no contract version
to
negotiate. This is a live bug on main for every family, not only the new
one:
this PR's seven poison tests each fail against a build without the fix
(glm53_nope, dsv4 decode, dsv4 prefill, dsv3_2 prefill verified on main
fb961281; nvfp4 verified against the pre-fix kernels, which are main's).

**Unconditional topk bounds in prefill index staging.** The prefill
`load_idx`
lambdas (MG, MG dual-cache, swapAB) bounded lanes by `actual_ni * BI`
but not by
`topk_len`, so lanes in the last partial tile read caller padding.
Callers that
leave stale values there (instead of -1) would gather wild gmem
addresses —
the new `bounds_stale_padding` tests crash a main build with a CUDA
illegal
memory access on both the MG and the swapAB route. Lanes past `topk_len`
now
stage -1 for every model type. The math side normalizes the same way
before
forming gmem addresses from the raw index row: the QK rope operand loads
(SG/MG/producer-consumer) are real loads, and DSV4's XV rope MMA reads
rope
straight from gmem, so stale positive padding past `topk_len` could form
a
wild address there as well (review feedback from coderabbit on this PR;
the
initial stale-padding test only covered rope-free GLM53_NOPE).

**ScaleSpec extraction (layout groundwork).** Each model's scale
configuration
(numeric format, group size, inline-vs-footer placement) is now a
composed
`ScaleSpec` row in `model/scale_spec.cuh` instead of hand-spelled
constants per
`KVCacheTraits` specialization, with the conversion helpers shared
through
`ScaleConvert`. Consumers keep reading the forwarded members
(`QUANT_TILE`/`NUM_SCALES`/`SCALE_FORMAT`/`SCALE_INLINE`/...) unchanged,
and
static asserts pin every derived constant to its pre-refactor value. A
future
DSv4-MXFP8 (group-32 UE8M0) or GLM53-NVFP4 cache becomes one traits row
plus
its dispatch entry, not another parallel traits/kernel copy; combined
with the
runtime row stride, the container side needs no kernel change at all.

Relation to flashinfer-ai/flashinfer#5022: same goals (compact rows,
masked-read correction); different
mechanism — one canonical layout + runtime stride instead of dual
layouts +
`shape[-1] == 528` sniffing +
`compact_bytes_per_token`/`glm53_nope_contract_version`
advertisement fields. flashinfer-ai/flashinfer#5022 constexpr-gates its
masked-read and bounds fixes
to GLM53_NOPE; this PR applies them to every family, and the on-main
reproduction above shows the hazards are not glm53-specific. If this PR
lands,
it is intended to supersede #5022's compact-row and masked-read changes;
the
8-head decode instantiation from #5022 is now carried here (via
ormandj's
branch, with its regression coverage).

## 🧪 Tests

RTX PRO 6000 (SM120):

```bash
python -m pytest -q tests/attention/test_sparse_mla_sm120.py \
  tests/attention/test_sparse_mla_sm120_dispatch.py \
  tests/attention/test_sparse_mla_sm120_cpb_model.py \
  tests/attention/test_sparse_mla_nvfp4_sm120.py \
  tests/attention/test_sparse_mla_nvfp4_sm120_plan.py
# 782 passed
```

Performance (RTX PRO 6000; paired same-session A/B vs upstream main
fb961281, per-arm forced JIT rebuilds, isolated autotune caches,
CUDA-graph
replay timing for the runner suite plus direct-binding timing with
explicit
cpb for the DRAM-pool rows):

- Decode (dsv4/dsv3_2/glm53_nope, T=1..64, single and dual cache): flat
within ±1% on dsv3_2 and glm53_nope; dsv4 dual-cache decode carries
+2-3%
at small T, cleanly attributable to the zero-row select in the issue
loop
(a probe with main's clamp instead matches main exactly). At 11-16us per
  call this is ~0.3us of added predication in the latency-bound regime.
- Prefill: dsv3_2/glm_nsa MG+swapAB flat across a 57-row matrix
(0.986-1.013x); dsv4 MG prefill (H=128, topk=1024) on the pre-review
build
was +0.7% at T=128 and +2.4% at T=2048 (3855us vs main's 3761-3776us).
An
  earlier revision spilled 8B to stack in the DSV4 MG
instantiation and lost +4.6% there; restructuring the zero-row selects
to
clamp-first form removed the spill (register/stack usage is now
identical
to main). The residual resists micro-optimization: five formulations of
the
  bounds/zero-row predication — including a fused per-lane limit that is
  strictly fewer instructions per tile than main's original guard — all
measure identically (+2.2-2.5%). On this shape the IO warps sit exactly
at
a per-tile issue edge where a handful of added instructions cost the
full
delta and the cost saturates: spreading the bulk gather from 64 to 128
IO
threads (3870us vs 3855us), staging fully resolved row pointers and
footer
  scale values a tile ahead so the issue point is a bare cp.async.bulk
  (3880us, +2.6% at T=128), address-clamped unconditional index loads
(3862-3866us), and a full-tile fast branch whose executed loop body
differs
from main only by the three zero-row selects (3855-3864us) all measure
the
  same; only a loop body with zero added instructions — no protection at
all — recovers main's 3761-3776us. NCU stall attribution puts the delta
  on long-scoreboard (gmem dependency) cycles in the gather/index path:
+0.19 cycles per issued instruction on +0.7% more issued instructions,
with
barrier, MIO, and short-scoreboard stalls unchanged. Static
compute/MMA/LSU
SASS opcode counts are identical to main. Two closing controls (separate
event-timed harness, same GPU): (a) adding a single always-true per-lane
select to main's staging loop reproduces nearly the whole delta by
itself
(3895us vs main's 3795us; the PR adds only ~10-25us on top of that), so
the loop has no slack for any added instruction — this is not specific
to
  the protection logic; (b) the +2.2-2.5% is a property of the 10MB
  L2-resident pool used above, not of production shapes: with a 4.9GB
DRAM-resident pool the same change costs +0.4% (3940us vs 3924us),
because
  the longer per-tile gather latency restores the slack the L2-resident
microbenchmark lacks. The math-side topk_len normalization added during
  review shifted the same equilibrium the other way — the final build
measures 3808-3815us at T=2048 (+1.3% vs main) and 250.9-251.1us at
T=128
(-0.9%, i.e. slightly faster than main) — consistent with the reading
that
small instruction changes anywhere in this kernel move this L2-resident
  shape by ~1% in either direction.
- GLM53_NOPE 528B rows are time-neutral on the measured shapes: at the
production decode shape (T=64, H=64, topk=2176, 640MiB pool, cpb=16)
both
row widths run ~220us at a ~415 GB/s unique-byte rate — not
DRAM-byte-bound
  on this GPU. The 528B row's benefit is the -19.5% KV footprint and the
  layout compatibility, not local kernel time.

New tests:

- `test_sparse_mla_sm120_glm53_nope_compact_rows`: 656B pool vs packed
528B vs
a 528B slice of the 656B pool (row stride 656) are bitwise-identical
across
  decode, prefill-MG, and prefill-swapAB shapes.
-
`test_sparse_mla_sm120_{glm53_nope,decode_dsv4}_masked_rows_ignore_poisoned_slot_zero`:
slot 0 poisoned with NaN values and scales; masked candidates keep
outputs
  finite and on-reference (inline and footer gather paths).
- `test_sparse_mla_sm120_prefill_glm53_nope_bounds_stale_padding`:
garbage
(huge positive) indices past `topk_length` are never gathered (MG +
swapAB).
-
`test_sparse_mla_sm120_prefill_{dsv3_2,dsv4,dots3_swa}_bounds_stale_padding`:
the same stale-padding discipline for rope models — SG, MG, MG
dual-cache,
and the BI=32 producer-consumer route — covering the math-side rope
address
formation. Each crashes the pre-fix build of this PR with an illegal
memory
  access and passes after.

Carried from ormandj's branch (lucifer1004/flashinfer#3):

- `test_sparse_mla_sm120_footer_flat_block_stride` /
`test_glm53_decode_flat_block_stride`: flat 2D caches with aligned gaps
between pages decode bit-identically to packed pages (the size-vs-stride
  regression).
- `test_sparse_mla_sm120_cache_alignment_rejected`,
  `test_sparse_mla_sm120_{decode,prefill}_footer_row_gap_rejected`,
`test_sparse_mla_sm120_inline_scale_rejects_padded_block_stride`: the
new
binding rejections (misaligned origin/block stride, footer row padding,
  inter-block gaps).
- `test_glm53_eight_head_decode_preserves_scratch_guards`: the H=8
scratch
  ABI, with guard regions.
- `test_glm53_compact_rows_match_padded_rows`,
  `test_glm53_masked_cache_rows_ignore_poisoned_slot_zero`,
`test_glm53_canonical_payload_is_scoped_to_model`: #5022's compact-row
and
  masked-row regression coverage on the canonical-payload design.
- `test_legacy_glm_layout_calibration_is_invalidated` /
`test_stale_schema_is_read_once_until_file_changes`: schema-v1 caches
are
  retired and a stale file is not reparsed until it changes.

Updated tests:

- `test_sparse_mla_sm120_inline_scale_prefill_accepts_padded_rows` (was
`..._rejects_padded_rows`): padded-row inline caches now work in
prefill;
the inter-block-gap rejection test keeps its semantics with the new
message.
- `test_sparse_mla_sm120_envelope_consistency`: 2D fixtures pack
GLM53_NOPE at
  its 528B payload.

pre-commit (clang-format, ruff, mypy) passes on the changed files.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

- **New Features**
- Added support for GLM-5.3 NoPE sparse MLA KV caches with compact
528-byte payloads and padded rows.
  - Added runtime row-stride handling for inline-scale KV caches.
- Masked or out-of-range KV entries now use safe zero values instead of
reading cache slot 0.

- **Bug Fixes**
- Prevented stale padding and invalid cache indices from producing
unintended memory reads or non-finite attention results.
- Improved support for padded KV rows across prefill, decode, and
dual-cache workflows.

- **Tests**
- Added coverage for compact rows, padded layouts, masked entries, and
multiple sparse MLA model variants.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: lucifer1004 <13583761+lucifer1004@users.noreply.github.com>
Co-authored-by: David Orman <ormandj@corenode.com>

### [83ce2da](https://github.com/flashinfer-ai/flashinfer/commit/83ce2dab1fca9f81480991915ad95f08d9a0038c)

- **作者**: Brian K. Ryu
- **时间**: 2026-09-11T21:01:24Z
- **提交信息**: feat(quantization): support fp32 input in the CuTe-DSL mxfp8_quantize kernel (#5112)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

Adds fp32 input support to the CuTe-DSL MXFP8 quantizer (requested in
#4930 for SGLang). fp32 pairs convert through the same saturating
`cvt.rn.satfinite.e4m3x2.f32` PTX the fp16/bf16 paths already use
internally, so numerics are identical by construction. fp32 uses 256-bit
loads (`ld.global.v8.u32`, sm_100+) to match the 16-bit paths'
load-instruction count. The fp16/bf16 code paths are untouched
(const-expr branches; verified bit-exact). The `cuda` backend
intentionally keeps its existing fp32 rejection.

Also enables fp32 in the benchmarks: `flashinfer_benchmark.py --routine
mxfp8_quantize --input_dtype float32` (cuda backend auto-dropped with an
INFO) and `bench_mxfp8_quantize_backend_comparison.py --bandwidth
--dtype float32` (dtype-aware TB/s accounting).

Performance heatmap collected with
`bench_mxfp8_quantize_backend_comparison.py --bandwidth --dtype float32`
on a B200 (peak DRAM BW 8TB/s)

<img width="1646" height="1481"
alt="fp32bw_v8_bandwidth_swizzled_128x4_float32"
src="https://github.com/user-attachments/assets/a18c2c73-e1ea-4cd1-bf68-3778eec87b1e"
/>


## 🔍 Related Issues

<!-- Link any related issues here -->

Closes #4930

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

- **New Features**
- MXFP8 quantization now supports `float32` input when using the
CuTe-DSL backend.
- Benchmark tools now accept `float32` as an input dtype and support
bandwidth measurements for it.
- Quantization handles contiguous views with non-standard alignment more
reliably.

- **Bug Fixes**
- Prevented unsupported `float32` configurations from selecting the CUDA
backend.

- **Documentation**
  - Clarified backend-specific dtype support for MXFP8 quantization.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [73810ba](https://github.com/flashinfer-ai/flashinfer/commit/73810ba3c26426378cb19e95581686f426625632)

- **作者**: Jimmy Zhou
- **时间**: 2026-09-11T20:44:49Z
- **提交信息**: fix[mla]: add Q8 floor for tile selection in trtllm-gen sparse mla kernels (#5106)

## 📌 Description

`trtllm_batch_decode_mla` on the sparse path fails kernel lookup before
launch when a tensor-parallel split leaves fewer than 8 Q heads per rank
*and* that count is a power of two. Reported on v0.6.18 / SM107 with
GLM-5.2 under SGLang disaggregated decode at TEP16 — 64 Q heads over 16
ranks leaves `numHeadsQPerKv = 4`:

```
Missing TRTLLM-GEN kernel (decode): qkvLayout=2, maskType=0, kernelType=2,
tileScheduler=0, multiCtasKvMode=1, headDimPerCtaV=512, headDimQk=576,
headDimV=512, tileSizeQ=4, tileSizeKv=128, numTokensPerPage=1, ...
sparseMlaType=1, ...
```

**Cause.** `selectSparseMlaGenerationKernel` sets the base tile to the
head group itself (`tileSizeQ = numHeadsQPerKv`), and only the *halving*
branch checks the Q8 floor (`halfTileSizeQ >= 8`). The helper that
exists to rescue undersized groups, `getPaddedMlaTileSizeQ`,
early-returns `0` for **every** power of two — so groups of 1, 2 and 4
skip padding entirely and hash to a kernel that does not exist.

**This is not a cubin coverage gap.** Q8 is the smallest MLA tile that
ships: the trtllm-gen generator configures `tileSizeQList = [8, 16, 32]`
for the static-token-sparse H576x512 group, 8 is the minimum across
every kernel family in that manifest, and no revision of it has ever
contained a tile below 8. No cubin publish can resolve this — the
selector has to clamp.

**Why it went unnoticed.** Two independent reasons:

- Groups of 5, 6 and 7 already work: they are not powers of two, so they
take the padding path and round up to 8. Sub-8 head counts are in fact
already covered —
`test_trtllm_batch_decode_sparse_mla_generic_non_power_of_two_heads[3-...]`
and `..._non_power_of_two_heads[...-6-...]` both pass today. The matrix
simply never lands on a power of two below 8.
- Dense MLA already works at these head counts: the non-sparse branch
has its own `numHeadsQPerKv <= 8 ? 8 : 16` clamp. Only the sparse path
is affected.

**Fix.** Extend the existing padding helper to also pad power-of-two
groups below 8, rather than adding a second clamp at the call site, so
one place continues to own the floor. Padding a Q8 tile that serves
fewer than 8 real heads is the mechanism already in production for
5/6/7-head groups: the launcher sizes the grid from `min(numHeadsQPerKv,
kernelMeta.mStepQ)` — the real head count, not the tile — so launch
geometry stays correct.

**Blast radius.** Evaluating the selector both ways across SM counts
{148, 208, 212} × batch {1, 2, 8, 32, 128} × topK {128, 512, 2048} ×
seqLenKv {1024, 8192, 131072}: only `numHeadsQPerKv` ∈ {1, 2, 4}
changes, all to Q8, on the sparse path only. The dense path is identical
at every head count. Everything ≥ 8 is untouched.

## 🔍 Related Issues

Reported internally against v0.6.18 (SM107 / GLM-5.2 / SGLang
disaggregated decode, TEP16).

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
- [x] All tests are passing (`unittest`, etc.).

`test_trtllm_batch_decode_sparse_mla_small_power_of_two_heads` adds the
missing corner: heads {1, 2, 4} × {bf16, fp8_e4m3} × topk {128, 2048},
placed next to the existing `..._power_of_two_heads` test which only
covers 16.

Validated on SM107 (GR100) in `flashinfer-ci:rubin-latest-py312-amd64`
carrying v0.6.18, the version the failure was reported against. The
selector logic is byte-identical between this base and 0.6.18.

| | new cases | `-k "heads or sparse"` |
|---|---|---|
| before | 12 failed | 12 failed, 1385 passed |
| after | 12 passed | **1397 passed, 0 failed** |

Fixed by this change: 12. Broken by this change: 0.

## 🔬 Experimental Track

<!-- Only for PRs submitted under the experimental policy
(CONTRIBUTING.md → "Experimental APIs and Backends").
     Leave this section untouched for normal PRs. -->

- [ ] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.
Tracking issue: #

## Reviewer Notes

The functional change is one condition; the other six lines correct two
existing comments that the change makes factually false (the helper's
doc comment and the call-site comment). No new explanatory prose was
added.

Worth a second look: the claim that an oversized tile is safe. It rests
on `computeCtaAndClusterConfig` deriving `numHeadsPerCta =
min(params.mNumHeadsQPerKv, kernelMeta.mStepQ)`, so the grid follows the
real head count rather than the tile — and every shipped Q8 sparse MLA
record has `stepQ = 8` with `mGroupsHeadsQ = true`.

One caveat this PR does not address: a Q8 tile serving 4 real heads
leaves half the Q tile idle. This makes wide-TEP sparse MLA *work*;
whether it is the right performance point for TEP16 versus TEP8 has not
been measured here.

### [c05407c](https://github.com/flashinfer-ai/flashinfer/commit/c05407ceffb7d9ce111a73553a8e37ad752adb62)

- **作者**: Nikita Korobov
- **时间**: 2026-09-11T17:27:39Z
- **提交信息**: Add CUTLASS Primitives and Task Scheduling Blackwell MoE kernels (#4361)

## 📌 Description

This PR adds an experimental PrimsTS MoE backend for Blackwell GPUs
under `flashinfer.fused_moe` and `flashinfer.prims_ts`. The kernels are
ported from TRT-LLM Gen and built from CUTLASS primitives plus the
task-scheduled (TS) scheduler. PrimsTS executes the FC1 and FC2 expert
GEMMs while reusing the TRT-LLM Gen routing and finalization flow.

The new `prims_ts_*` entry points are modeled after the corresponding
`trtllm_*` APIs, with backend-specific arguments and support
restrictions documented and validated before launch. Existing TRT-LLM
Gen APIs remain available and continue to use the native implementation.

### Supported configurations

- BF16 MoE: logits-based and routed APIs with BF16 activations and
weights.
- FP8 per-tensor MoE: E4M3 activations and weights with per-tensor
scalar scales.
- FP8 block-scale MoE: logits-based and routed APIs with DeepSeek FP8
and MXFP8 scale layouts.
- FP4 block-scale MoE: logits-based and routed APIs for NVFP4 × NVFP4,
MXFP4 × MXFP8, and MXFP4 × BF16.
- Batched/grouped FC1 and FC2 GEMMs with FP32 accumulation, supported
fused gated activations, bias, clamp, and fused quantization epilogues.
- Static hardware-grid and dynamic persistent CLC scheduling, PDL where
supported, autotuning, custom/fake ops, trace definitions, and
validation helpers.

### Current limitations

MXINT4 × BF16 is not supported. Other remaining gaps include selected
LoRA, fused shared-expert, routing replay/policy, activation, and DSMEM
split-K combinations. Accuracy qualification currently targets
SM100a/B200; SM103a/B300 is architecture-gated but has not completed
signoff qualification.

### Benchmark

B200, E/local-E=128, top-k=4, H=I=3072, SwiGLU

| Quant mode | Routing | Tokens | TRT default (ms) | TRT tuned (ms) |
Prims default (ms) | Prims tuned (ms) | Tuned Prims / TRT |
|---|---|---:|---:|---:|---:|---:|---:|
| BF16 | logits | 1 | 0.056480 | 0.056000 | 0.059120 | 0.058080 | 1.037x
|
| BF16 | logits | 32 | 0.617152 | 0.615536 | 0.629471 | 0.616959 |
1.002x |
| BF16 | logits | 128 | 0.987232 | 0.984191 | 0.998287 | 0.985871 |
1.002x |
| BF16 | logits | 512 | 1.367231 | 1.030591 | 1.501358 | 1.034463 |
1.004x |
| Fp8-Per-Tensor | logits | 1 | 0.036400 | 0.036304 | 0.039552 |
0.037536 | 1.034x |
| Fp8-Per-Tensor | logits | 32 | 0.353199 | 0.353264 | 0.370976 |
0.354448 | 1.003x |
| Fp8-Per-Tensor | logits | 128 | 0.517103 | 0.516880 | 0.539456 |
0.518624 | 1.003x |
| Fp8-Per-Tensor | logits | 512 | 0.638703 | 0.546576 | 0.915023 |
0.547472 | 1.002x |
| Fp8-Block | logits | 1 | 0.046415 | 0.045952 | 0.047456 | 0.045808 |
0.997x |
| Fp8-Block | logits | 32 | 0.074432 | 0.057904 | 0.133855 | 0.054576 |
0.943x |
| Fp8-Block | logits | 128 | 0.199392 | 0.088592 | 0.328543 | 0.079072 |
0.893x |
| Fp8-Block | logits | 512 | 0.694366 | 0.189536 | 1.093375 | 0.179423 |
0.947x |
| NvFP4xNvFP4 | precomputed | 1 | 0.024976 | 0.025008 | 0.028448 |
0.028448 | 1.138x |
| NvFP4xNvFP4 | precomputed | 32 | 0.191377 | 0.191584 | 0.219792 |
0.195217 | 1.019x |
| NvFP4xNvFP4 | precomputed | 128 | 0.309536 | 0.309392 | 0.348336 |
0.312592 | 1.010x |
| NvFP4xNvFP4 | precomputed | 512 | 0.368256 | 0.319840 | 0.499232 |
0.324416 | 1.014x |
| MxFP4xBf16 | precomputed | 1 | 0.032417 | 0.032624 | 0.205680 |
0.186992 | 5.732x |
| MxFP4xBf16 | precomputed | 32 | 0.232608 | 0.229984 | 2.195889 |
2.184864 | 9.500x |
| MxFP4xBf16 | precomputed | 128 | 0.392384 | 0.379632 | 3.775120 |
3.652624 | 9.621x |
| MxFP4xBf16 | precomputed | 512 | 0.814144 | 0.416896 | 8.844993 |
3.688272 | 8.847x |
| MxFP4xMxFP8 | precomputed | 1 | 0.026880 | 0.027264 | 0.033504 |
0.030304 | 1.112x |
| MxFP4xMxFP8 | precomputed | 32 | 0.185503 | 0.185344 | 0.281199 |
0.187632 | 1.012x |
| MxFP4xMxFP8 | precomputed | 128 | 0.300767 | 0.300864 | 0.456000 |
0.302623 | 1.006x |
| MxFP4xMxFP8 | precomputed | 512 | 0.479248 | 0.318720 | 0.964047 |
0.322560 | 1.012x |

MxFP4xBf16 performance difference will be addressed in the future PRs.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] `pre-commit` is available in the development environment.
- [x] The local Git hook has been installed with `pre-commit install`.
- [x] `pre-commit run --all-files` passes on the current branch.

## 🧪 Tests

- [x] Added standalone PrimsTS batched-GEMM correctness,
schedule-validation, metadata, and no-hang coverage.
- [x] Added MoE backend integration and routed-input parity coverage.
- [x] Added trace examples and regenerated `tests/trace/fi_trace_out/`
definitions.
- [x] Added focused regressions for reusable routed FFI tensors and
autotuner cache-key compatibility.
- [x] Reduced the shared MoE integration matrix so PrimsTS coverage no
longer multiplies the full TRT-LLM test grid.
- [ ] Complete SM100/SM103 GPU CI signoff.

## Reviewer Notes

The PrimsTS backend shares TRT-LLM Gen routing/finalization semantics
but substitutes task-scheduled batched GEMMs for FC1/FC2. Unsupported
shape, dtype, layout, scale, routing, and activation combinations are
rejected before launch.

### Remaining follow-ups

- [x] **Performance qualification before merge:** benchmark
representative supported configurations against TRT-LLM Gen on
B200/SM100a, publish the environment/shapes and median latency, and
verify or revise the intended “on par” claim. SM103a/B300 results belong
with its separate signoff.
- [ ] **Persistent kernel cache after merge:** move the current
process-local PrimsTS compiled-GEMM cache to FlashInfer's persistent
CuTe-DSL cache lifecycle with architecture/version/source/config
invalidation and cold/warm-process tests. Track this in a linked issue
with an owner; it is not a known correctness blocker.

Review focus: kernel correctness on CUDA 12.9/13.x, representative
end-to-end backend coverage, and sustainable CI collection/runtime.

---------

Signed-off-by: qgai <qgai@nvidia.com>
Co-authored-by: qgai <qgai@nvidia.com>
Co-authored-by: Justus Henneberg <jhenneberg@nvidia.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: Alex Yang <aleyang@nvidia.com>
Co-authored-by: Brian K. Ryu <bryu@nvidia.com>
Co-authored-by: Jingfan Sun <jingfans@nvidia.com>
Co-authored-by: Dimitrios Bariamis <dbari@users.noreply.github.com>
Co-authored-by: feih <feih@nvidia.com>
Co-authored-by: Dimitrios Bariamis <12195802+dbari@users.noreply.github.com>
Co-authored-by: Ka-Hyun Nam <69875166+kahyunnam@users.noreply.github.com>

### [6268039](https://github.com/flashinfer-ai/flashinfer/commit/6268039d4261679765aaccabc92d3d257fc92891)

- **作者**: Brian K. Ryu
- **时间**: 2026-09-11T17:21:49Z
- **提交信息**: chore: add codebase-wise  approvers to every CODEOWNERS rule (#5146)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

Adds codebase-wise approvers (@aleozlx @yzh119 @Jingfan-Sun
@YangXu1990uiuc @bkryu) to every CODEOWNERS rule so any one of them can
approve any PR.

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

- **Chores**
- Updated code review ownership and approval routing across project
components.
- Added additional reviewers to relevant areas and clarified
repository-wide approval coverage.
- No end-user functionality, performance, or interface changes are
included in this update.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [65146a5](https://github.com/flashinfer-ai/flashinfer/commit/65146a59c89f0b6351618d87fc0fe7a519b04fdd)

- **作者**: Void
- **时间**: 2026-09-11T17:05:13Z
- **提交信息**: fix(moe): avoid FP8 scale overflow in the Humming MXFP4 path (#5024)

## 📌 Description

The Humming MXFP4 x FP8 fused-MoE path dynamically quantizes each routed
activation row to FP8 E4M3 at two points:

1. when the input rows are expanded for GEMM1; and
2. after the fused activation, before GEMM2.

For a row with maximum absolute value `row_amax`, both sites previously
used:

```text
quant_scale = row_amax > 0 ? 448 / row_amax : 1
```

This expression is not finite for every positive FP32 input. If
`0 < row_amax < 448 / FLT_MAX` (approximately `1.317e-36`), the quotient
overflows to infinity. Scaling the row by that value can then produce
Inf/NaN
FP8 inputs (`0 * Inf` is NaN), and a single routed expert can
contaminate the
complete top-k-combined MoE output row.

This edge case was exposed by the Humming MXFP4 representation. Weight
preprocessing decomposes each expert's MXFP4 E8M0 block exponents into
encoded
block-local offsets and a common FP32 expert residual scale. Runtime
folds that
residual into the activation dequantization scale. In Qwen3.5-397B, an
effectively dormant expert produced a real post-activation row with an
amax of
about `6.3e-38`, which enters the overflowing branch above.

This PR derives the smallest safe denominator from FP32 limits and
applies the
same helper at both dynamic-quantization sites:

```text
min_amax = 448 / FLT_MAX
quant_scale = 448 / max(row_amax, min_amax)
```

The result is finite and at most `FLT_MAX`. Rows in the ordinary range
retain
the original calculation exactly, and zero rows retain the previous
scale of
one. For signals too small to survive the FP8/FP32 representation after
all
scales are applied, the route may still round to zero; the purpose of
this
minimal fix is to prevent such a negligible route from becoming
non-finite and
poisoning the token.

The issue and fix are specific to the dynamic FP8 activation-scaling
code used
by this Humming MXFP4 fused-MoE path. They are not an inherent
limitation of the
MXFP4 format.

### Qwen3.5-397B model-level impact

We found the overflow while evaluating Qwen3.5-397B-A17B with MXFP4
expert
weights and FP8 activations on 8 x H200. The following runs used the
same 1,314
GSM8K examples, 5-shot prompts, completion API, and greedy decoding:

| Configuration | Correct | Accuracy |
|---|---:|---:|
| BF16 | 1264 / 1314 | 96.1948% |
| Official FP8 checkpoint | 1247 / 1314 | 94.9011% |
| Calibrated WINT4 x FP8 | 1251 / 1314 | 95.2055% |
| MXFP4 x FP8, overflowing path | 1155 / 1314 | 87.8995% |
| MXFP4 x FP8, this PR (`a70bda3c`) | 1245 / 1314 | 94.7489% |

The fix recovered 90 answers, or 6.8493 percentage points. The corrected
MXFP4 result is within two answers of the FP8 checkpoint and six answers
of the
calibrated WINT4 x FP8 checkpoint.

The failure was localized to a routed expert in layer 5. Its gate/up and
down
projection weights had RMS values around `1e-20`, producing a
post-SwiGLU row
around `1e-38`. The old quotient generated 4,096 non-finite values and
poisoned
one complete hidden row. Replaying the saved layer input with the
finite-scale
guard removed all 4,096 non-finite values. Against an independently
computed
finite reference, the corrected local-MoE output had 1.455% relative
RMSE and
0.999894 cosine similarity.

This PR:

- adds one shared finite-scale helper for dynamic FP8 row quantization;
- uses it for both the GEMM1 input and post-activation GEMM2 input
paths; and
- adds Hopper regressions for tiny nonzero rows at both sites.

## 🔍 Related Issues

N/A

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] Changed Python file passes `ruff check --no-cache`.
- [x] Changed Python file passes `ruff format --check`.
- [x] Changed CUDA ranges pass the repository's clang-format 19.1.1
formatter.
- [x] `git diff --check` passes.

## 🧪 Tests

- [x] H200: `test_moe_fp8_mxfp4_humming_tiny_amax_stays_finite` — 2/2
  parameterized cases passed (`input` and `post_activation`).
- [x] H200: existing
`test_moe_fp8_mxfp4_humming_prescale_hopper_correctness[False-small]` —
  passed.
- [x] H200, 8 GPUs: full Qwen3.5-397B GSM8K run — 1245/1314
  (94.7489%), with all 1,314 evaluation requests returning HTTP 200.

The regression constructs tiny nonzero rows at each online FP8
quantization
site and asserts that the fused-MoE output remains finite. Before this
fix, the
input-stage case was confirmed to produce an all-NaN output row.

## 🔬 Experimental Track

Not applicable; this PR does not add or change an experimental
API/backend.

## Reviewer Notes

This is intentionally a minimal common-path change. It adds a single
`fmaxf`
before the existing division and does not introduce residual-dependent
scale
selection or exact-division/FMA instructions. The threshold is derived
directly
from `FP8_E4M3_MAX / FLT_MAX`, rather than chosen empirically.

### [01f19ab](https://github.com/flashinfer-ai/flashinfer/commit/01f19ab957319d3c84dcb214a10263ab471e1e75)

- **作者**: Anerudhan Gopal
- **时间**: 2026-09-11T16:58:54Z
- **提交信息**: build: raise the nvidia-cudnn-frontend floor to 1.28.0 (#5131)

## Summary

Raises the `nvidia-cudnn-frontend` floor from `>=1.25.0` to `>=1.28.0`.
One line, no code changes.

## Motivation

The declared floor is below what shipped code already requires, so an
environment can satisfy `requirements.txt` and still silently lose a
cuDNN path.

`flashinfer/cudnn/prefill.py:44-56` gates its FP8 / mixed-dtype prefill
on frontend `(1, 27)`:

```python
if mixed or (dtype in (torch.float8_e4m3fn, torch.float8_e5m2)):
    min_backend, min_frontend = 92500, (1, 27)
elif dtype in (torch.float16, torch.bfloat16):
    min_backend, min_frontend = 92400, (1, 25)
...
major, minor = map(int, cudnn.__version__.split(".")[:2])
return (major, minor) >= min_frontend
```

while `requirements.txt` asks only for `>=1.25.0`.

On a resolved 1.25 or 1.26, `_cudnn_supports_direct_seqlens` returns
`False` and the token-unit direct path is skipped — **no error and no
warning**, just a quieter fallback. That check is deliberately a
package-version compare rather than a feature probe, as its own comment
explains:

> this is a pure version compare against the runtime backend and the FE
package version (the practical proxy for the FE's compiled-against
cuDNN). The FE exposes no compiled/effective-version query, so a
feature-probe with NOT_SUPPORTED fallback is left as a follow-up.

Since the frontend offers no capability query, the declared floor is the
only place that information can live — which makes the current
understatement load-bearing rather than cosmetic.

## Why 1.28 and not 1.27

To be precise: the **strictly demonstrated** in-tree requirement today
is **1.27**. This picks 1.28.0 because it is the current release on
PyPI, so the floor costs nothing to satisfy and avoids a second bump
shortly after. Newer frontend APIs (the DSA indexer / top-K family) also
live there, but nothing in this PR depends on them.

Happy to retarget this at `>=1.27.0` instead if maintainers prefer the
floor to track only what is provably required.

## Compatibility

- `1.28.0` is the latest `nvidia-cudnn-frontend` release on PyPI, so the
floor is satisfiable today.
- No behaviour change for anyone already resolving 1.28.
- Anyone previously resolving 1.25–1.27 now gets the FP8 prefill path
they were silently missing.

## Test plan

No code touched. Verified locally that a clean environment resolving
`nvidia-cudnn-frontend==1.28.0` imports FlashInfer and reports the
expected versions:

```
torch 2.11.0+cu128   cuda 12.8
cudnn FE 1.28.0      backend 91900
```

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Chores**
* Updated the minimum supported version of the NVIDIA cuDNN frontend
dependency.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [7c51384](https://github.com/flashinfer-ai/flashinfer/commit/7c51384819f9e78e22a703391fd871dc15ab2630)

- **作者**: baonudesifeizhai
- **时间**: 2026-09-11T16:22:12Z
- **提交信息**: Fix bmm_fp8 cublasLt handle usage in autotuned cublas runner  #26381 (#2808)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

## 🔍 Related Issues
 https://github.com/vllm-project/vllm/issues/26381
Root cause:
torch.cuda.current_blas_handle() returns cublasHandle_t, but bmm_fp8
reinterpreted it as cublasLtHandle_t before calling cublasLt APIs. This
can fail in autotune/profiling paths on Blackwell.
<!-- Link any related issues here -->
on vllm side 
before: https://paste.ubuntu.com/p/npS2tkZY2c/
after : https://paste.ubuntu.com/p/c6Ys69PqvR/

and :  
```
 CUDA_VISIBLE_DEVICES=4,5,6,7 \
VLLM_DISABLE_COMPILE_CACHE=1 \
TORCHINDUCTOR_FORCE_DISABLE_CACHES=1 \
python examples/basic/offline_inference/generate.py \
  --model redhatai/meta-Llama-3.1-8B-FP8 \
  --tensor-parallel-size 4 \
  --kv-cache-dtype fp8 \
  --trust-remote-code \
  --max-model-len 4096 \
  --max-tokens 32 \
  --temperature 0
```
:https://paste.ubuntu.com/p/rPYcXQSwPC/


<img width="1115" height="510" alt="image"
src="https://github.com/user-attachments/assets/ee05e9d9-fa6a-4ea4-bd89-082df63828a7"
/>

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

## Refactor

* Simplified FP8 batch matrix multiplication interfaces by removing the
need to provide an external cuBLAS handle.
* Improved FP8 GEMM execution by automatically managing and reusing
cuBLAS resources for each GPU device.
* Updated FP8 algorithm selection and execution workflows to use this
internal resource management consistently.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [80342ae](https://github.com/flashinfer-ai/flashinfer/commit/80342aea9a81a69b81729bc4a025587ba35a7461)

- **作者**: Xuanteng Huang
- **时间**: 2026-09-11T11:36:55Z
- **提交信息**: fix(moe): Fix per-token quantization `fast-math` INF scale when activation contains all-zero row (#5031)

<!-- .github/pull_request_template.md -->

## 📌 Description

This PR aims to fix a potential bug in per-token NVFP4 quantization
kernel in the `fast-math` path. If the input tensor has a all-zero row,
current non `fast-math` path generates 0 scale:

https://github.com/flashinfer-ai/flashinfer/blob/8bc3b578027791336c6ae87db5c9d76f82cef8bc/csrc/nv_internal/tensorrt_llm/kernels/quantization.cuh#L793-L802

But the `fast-math` path will produce INF scale, which ultimately leads
to NaN activation. As ReLU2 happens to produce zero rows, this bug
causes the accuracy regression in Nemotron-3 series models.

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

- **Bug Fixes**
- Improved FP4 quantization stability for zero-scale inputs, preventing
invalid results such as NaN or infinity.
- Ensured zero-valued inputs produce valid zero outputs in routed
mixture-of-experts processing.

- **Tests**
- Added coverage for zero-valued input rows and verified numerical
stability and expected zero results.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Xuanteng Huang <xuantengh@nvidia.com>

### [604da4f](https://github.com/flashinfer-ai/flashinfer/commit/604da4ff96cba980b7edf11ffb5e3c4d8c3c0fb8)

- **作者**: eigen
- **时间**: 2026-09-11T11:30:45Z
- **提交信息**: feat(cake_diffusion): add SM103a BF16 pre-attention (#4690)

<!-- .github/pull_request_template.md -->

## 📌 Description

- Add an SM103a-only fused BF16 pre-attention operator for the
highest-priority MiniMax-H3 workload in #4532.
- Support the native tensor-map alignment supplied by CUDA 12.9 and CUDA
13.0 while retaining the native by-value launch ABI.
- Keep the established public API and route it explicitly to the Cake
implementation.
- Fuse input RMSNorm, indexed AdaLN, BF16 QKV projection, per-head Q/K
RMSNorm, partial 3-D split-half NeoX RoPE, and destination-major
packing.
- Preserve the native checkpoint weight layout `[21504, 5376]` and write
directly to caller-owned `[P, M, 56 // P, 3, 128]` output for `P in {1,
2, 4, 8}`.
- Expose a direct kernel entry for compute capability 10.3 with CUDA
12.9+ and precise-math compilation flags. This entry does not perform
automatic hybrid dispatch, and the following collective remains outside
the operator.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.). Fresh GPU CI for this
update is pending.

### Validation

The compatibility update retains the kernel arithmetic, precise-math
flags, and full 44-shape correctness contract. All 38 exporter tests and
17 target CPU tests pass, and the generated integration reproduces
identically. Target Ruff 0.12.8 lint and formatting checks pass. Fresh
CUDA 12.9 and CUDA 13.0 validation on GB300 is pending; the recorded GPU
results below describe the previously measured revision
`f23b30f1dcd88675b40b1a2e2869c2a6d2a1341a`.

- NVIDIA GB300 / compute capability 10.3.
- BF16 correctness passed all 44 contract shapes at `atol=rtol=1e-2`.
The 24 production centers cover `P in {1,2,4,8}` with
`M={33472,38592,48768,58944,74240,109952}/P`; the edge set adds aligned
neighbors, plus/minus-one tails around the 5-second center, and `P=8, M
in {1,127,128,129}` smoke shapes.
- Invalid AdaLN table indices `{-1, 9, INT_MIN, INT_MAX}` produce zero
output rows. CUDA graph replay was checked after explicitly clearing the
captured output buffer, and tracing was checked for multiple runtime
parallelism/head bindings.
- The source distribution and wheel contain the required CUDA source and
headers. An isolated wheel installation resolved the packaged paths and
passed a real JIT compile and launch on GB300.
- The registered benchmark regression passed at `2.1377 ms` against its
`3.1000 ms` limit, with CUPTI as the actual backend.
- Candidate-only Compute Sanitizer runs passed both `synccheck` and
`memcheck` with final `ERROR SUMMARY: 0 errors`, including valid tail
shapes and mixed invalid AdaLN indices.

## Performance

In the recorded 2026-08-28 measurements at
`f23b30f1dcd88675b40b1a2e2869c2a6d2a1341a` on **NVIDIA GB300 / SM103a**,
the fused operator achieved **1.189003x geometric-mean speedup across
all 24 production-center shapes**, with improvements on every measured
shape. At the primary `P=8, M=4824` shape, latency is **3.007044 →
2.079651 ms (1.445937x)**.

These are the recorded 2026-08-28 measurements. The measured CUDA source
and Python integration files match PR commit
`f23b30f1dcd88675b40b1a2e2869c2a6d2a1341a` byte for byte.

Timings use `bench_gpu_time(enable_cupti=True, cold_l2_cache=True,
dry_run_iters=10, repeat_iters=100)` with CUPTI as the actual backend.
JIT compilation, tensor creation, and output allocation are outside the
timing boundary. The complete segmented baseline includes input RMSNorm,
indexed AdaLN, three BF16 projections, Q/K RMSNorm, partial 3-D
split-half NeoX RoPE, destination-major packing, and the final
device-to-device copy to the caller-owned output.

| Shape group | Shapes | Geometric-mean speedup |
| --- | ---: | ---: |
| `P=1` | 6 | 1.063690x |
| `P=2` | 6 | 1.148392x |
| `P=4` | 6 | 1.220319x |
| `P=8` | 6 | 1.340763x |
| **All production centers** | **24** | **1.189003x** |

The sum of the 24 baseline latencies is **391.703544 ms**, versus
**352.150005 ms** for the fused kernel: **39.553539 ms** less total
latency. Their ratio is **1.112320x**; this is a separate aggregate from
the geometric mean above. The `3.1000 ms` benchmark regression limit in
Validation is a threshold, not the measured comparison baseline.

All 24 measured shapes are listed below. Speedup is baseline latency
divided by fused latency; reduction is baseline minus fused latency.

| Duration | P | M | Baseline (ms) | Fused (ms) | Reduction (ms) |
Speedup |
| --- | ---: | ---: | ---: | ---: | ---: | ---: |
| 4s | 1 | 33472 | 18.782824 | 17.286614 | 1.496210 | 1.086553x |
| 4s | 2 | 16736 | 10.036461 | 8.570956 | 1.465505 | 1.170985x |
| 4s | 4 | 8368 | 5.098999 | 3.847141 | 1.251858 | 1.325400x |
| 4s | 8 | 4184 | 2.678692 | 1.897108 | 0.781584 | 1.411987x |
| 5s | 1 | 38592 | 21.473754 | 19.915034 | 1.558720 | 1.078269x |
| 5s | 2 | 19296 | 11.457663 | 10.046237 | 1.411426 | 1.140493x |
| 5s | 4 | 9648 | 5.805928 | 4.506037 | 1.299891 | 1.288478x |
| 5s | 8 | 4824 | 3.007044 | 2.079651 | 0.927393 | 1.445937x |
| 6s | 1 | 48768 | 27.349780 | 25.774386 | 1.575394 | 1.061122x |
| 6s | 2 | 24384 | 14.556563 | 12.577808 | 1.978755 | 1.157321x |
| 6s | 4 | 12192 | 7.369658 | 5.978710 | 1.390948 | 1.232650x |
| 6s | 8 | 6096 | 3.775348 | 2.767284 | 1.008064 | 1.364279x |
| 8s | 1 | 58944 | 33.080459 | 30.446152 | 2.634307 | 1.086523x |
| 8s | 2 | 29472 | 17.579319 | 15.377988 | 2.201331 | 1.143148x |
| 8s | 4 | 14736 | 8.866027 | 7.316154 | 1.549873 | 1.211843x |
| 8s | 8 | 7368 | 4.520454 | 3.426820 | 1.093634 | 1.319140x |
| 10s | 1 | 74240 | 41.599636 | 39.161390 | 2.438246 | 1.062261x |
| 10s | 2 | 37120 | 22.125386 | 19.679768 | 2.445618 | 1.124271x |
| 10s | 4 | 18560 | 11.054317 | 9.713275 | 1.341042 | 1.138063x |
| 10s | 8 | 9280 | 5.607911 | 4.354997 | 1.252914 | 1.287696x |
| 15s | 1 | 109952 | 58.456101 | 57.909877 | 0.546224 | 1.009432x |
| 15s | 2 | 54976 | 32.723207 | 28.339041 | 4.384166 | 1.154704x |
| 15s | 4 | 27488 | 16.430436 | 14.443889 | 1.986547 | 1.137535x |
| 15s | 8 | 13744 | 8.267577 | 6.733688 | 1.533889 | 1.227793x |

## 🔍 Related Issues

Addresses the fused BF16 pre-attention focus in
https://github.com/flashinfer-ai/flashinfer/issues/4532 without
including the downstream collective.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [ ] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

The complete pre-commit checks will run in CI for the updated commit.

## Reviewer Notes

The compatibility fix preserves native by-value tensor-map passing and
precise-math compilation. The public function signature and custom-op
schema remain unchanged; the implementation is selected through
`backend="cake"`.

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [ac7bce1](https://github.com/flashinfer-ai/flashinfer/commit/ac7bce13ea0ff76392fd17aa696b096e191d0825)

- **作者**: eigen
- **时间**: 2026-09-11T09:20:05Z
- **提交信息**: feat(cake_comm): add opt-in Blackwell MNNVL MoE all-to-all backend (#4784)

## 📌 Description

Add an **explicitly opt-in** generated Blackwell backend for MNNVL MoE
all-to-all.

**TensorRT-LLM remains the default on every architecture, including B200
and GB300.** Existing callers do not automatically switch backend based
on their GPU. Select Cake explicitly on every participating rank:

```python
from flashinfer.comm import MoeAlltoAll

# Existing/default behavior:
collective = MoeAlltoAll(mapping, max_num_tokens, top_k, num_experts,
                        hidden_size=hidden_size)  # backend="trtllm"

# Explicit opt-in on compute capability 10.0 or 10.3:
collective = MoeAlltoAll(mapping, max_num_tokens, top_k, num_experts,
                        hidden_size=hidden_size, backend="cake")
```

The functional `moe_a2a_*` entry points also default to
`backend="trtllm"`. An opt-in caller must use `backend="cake"`
consistently for workspace sizing, initialization, dispatch, combine,
and sanitization. Unsupported Cake architectures and invalid backend
names raise an error rather than silently falling back. Backend-specific
workspace caches and distinct custom-op names keep the two
implementations isolated when they coexist in one process.

The default backend's dispatch copy also checks source and destination
alignment when choosing its vector width. Mixed payloads can leave a
receive plane only 8-byte aligned even when its row size is divisible by
16; this correction avoids a misaligned wide store without changing the
workspace layout or padding requirements.

Existing SGLang callers that do not pass the new argument keep the
default backend. This PR does not add a SGLang command-line option or
enable Cake in SGLang automatically.

### Performance results

The previously reported **real eight-rank communication measurements**
are summarized below. Speedup is baseline time divided by
generated-backend time; lower latency is better.

| GPU | Input format | Baseline (ms) | Generated backend (ms) | Speedup
|
| --- | --- | ---: | ---: | ---: |
| B200 | BF16 | 0.680267 | 0.442816 | **1.5362×** |
| B200 | FP8 | 0.851167 | 0.615376 | **1.3832×** |
| B200 | NVFP4 | 1.829577 | 1.547981 | **1.1819×** |
| GB300 | BF16 | 0.766562 | 0.462081 | **1.6589×** |
| GB300 | FP8 | 0.9220185 | 0.6196015 | **1.4881×** |
| GB300 | NVFP4 | 1.937989 | 1.469315 | **1.3190×** |

Configuration: B200 **1 node × 8 GPUs**; GB300 **2 nodes × 4 GPUs**.
Each case uses 1,024 tokens/rank, hidden size 7,168, 256 experts, top-k
8, PDL enabled, and workspace-resident combine payloads. These are
CUPTI-timed **dispatch-plus-combine** microbenchmarks with no-op expert
computation, not full MoE or SGLang serving measurements. Baseline:
FlashInfer 0.6.16 at `8da13a29c85f7e5b1c81878d933f84ae9fc4afa9`. The
generated-backend values come from the archived standalone-kernel
harness used for the original results. Each row has one recorded
baseline/candidate pair; no statistical significance is claimed.

These are **historical results**, not a remeasurement of the current PR
head after the opt-in change or upstream merge. The explicit selector
preserves TRT-LLM as the default; obtaining these generated-backend
paths now requires `backend="cake"`.

### Full historical results and scope

The table below is **historical microbenchmark evidence**, not a new
benchmark of this opt-in change, a guarantee for every shape, or an
end-to-end SGLang speedup. Each architecture's 40 rows mix two
world-size-one cases, 17 simulated multi-rank cases, and 21 real
multi-rank cases. In particular, the largest ratios are small
world-size-one object-roundtrip measurements, not distributed serving
results. Later kernel changes and this selector change require their own
measurements; the historical table should not be read as a uniform
measurement of the current PR head.

<details>
<summary>Historical shape-level measurements (original reported
values)</summary>

| Shape | B200 speedup | GB300 speedup |
| --- | ---: | ---: |
| `focused_object_roundtrip_t10_v8_e8_k2` | 58.8761× | 120.4431× |
| `focused_simulated_dispatch_w2_t5_v8` | 9.9510× | 20.4237× |
| `focused_larger_payloads_w8_t16_v2048_p5` | 4.4606× | 10.6631× |
| `focused_larger_payloads_w8_t16_v2048_p6` | 4.9037× | 11.3582× |
| `focused_sanitize_w2_t64` | 1.7007× | 2.8413× |
| `focused_combine_w4_t16_v2880_k4_mxfp8_layout_8x4` | 3.3312× | 4.8058×
|
| `focused_combine_w8_t16_v5120_k6_mxfp4_layout_128x4` | 3.7305× |
5.6235× |
| `focused_combine_w8_t16_v4096_k8_mxfp4_layout_128x4` | 4.1624× |
7.5814× |
| `focused_combine_w8_t16_v4096_k10_mxfp4_layout_128x4` | 3.7399× |
5.8680× |
| `focused_combine_w8_t16_v4096_k16_nvfp4_layout_128x4` | 2.7558× |
5.4735× |
| `focused_combine_w8_t16_v4096_k22_mxfp4_layout_128x4` | 2.5597× |
4.2554× |
| `focused_lora_combine_1_w4_t16_v4096_k2_workspace` | 2.3941× | 4.6425×
|
| `hard_documented_basic_bf16_w8_t1024_v7168_e256_k8` | 1.5362× |
1.6589× |
| `hard_documented_fp8_w8_t1024_v7168_e256_k8` | 1.3832× | 1.4881× |
| `hard_documented_nvfp4_w8_t1024_v7168_e256_k8` | 1.1819× | 1.3190× |
| `hard_documented_validate_bf16_w8_t1024_v7168_e256_k8` | 1.0120× |
1.0378× |
| `hard_documented_per_phase_bf16_w8_t1024_v7168_e256_k8` | 1.4718× |
1.6840× |
|
`focused_object_roundtrip_t902_v7168_e256_k8_payload_external_output_provided`
| 1.2590× | 2.0700× |
| `focused_combine_w8_t16_v7168_k8_none_linear_pdl0` | 2.1746× | 3.6459×
|
| `current_nondiv_w4_t16_v32_e6` | 9.6345× | 23.7619× |
| `current_rankmask_w4_t16_v32_dead2` | 4.5735× | 6.3148× |
| `current_eplb_w4_t16_v16_e32` | 6.3290× | 9.4849× |
| `current_compact_ep4_t4_v256_e64_k8` | 8.5566× | 17.6389× |
| `current_fp8_combine_w8_t16_v7168_k8_workspace` | 2.1925× | 3.6832× |
| `source_mpi2_dispatch_random_k1_plain` | 8.4738× | 1.9820× |
| `source_mpi2_dispatch_uniform_k1_plain` | 8.2569× | 8.4916× |
| `source_mpi2_dispatch_random_k2_plain` | 7.9072× | 3.1515× |
| `source_mpi2_dispatch_uniform_k2_plain` | 8.4794× | 2.5603× |
| `source_mpi2_dispatch_random_k8_plain` | 7.0850× | 5.7582× |
| `source_mpi2_dispatch_uniform_k8_plain` | 6.9662× | 3.1348× |
| `source_mpi2_dispatch_random_k8_lora` | 7.7793× | 2.7036× |
| `source_mpi2_dispatch_uniform_k8_lora` | 8.0279× | 2.2788× |
| `source_mpi2_combine_random_k1_plain` | 6.4270× | 6.8773× |
| `source_mpi2_combine_uniform_k1_plain` | 6.5419× | 6.8569× |
| `source_mpi2_combine_random_k2_plain` | 5.8795× | 6.2871× |
| `source_mpi2_combine_uniform_k2_plain` | 6.2487× | 6.1478× |
| `source_mpi2_combine_random_k8_plain` | 6.1003× | 6.8304× |
| `source_mpi2_combine_uniform_k8_plain` | 7.0231× | 8.7408× |
| `source_mpi2_combine_random_k2_lora` | 6.2823× | 5.8514× |
| `source_mpi2_combine_uniform_k8_lora` | 7.3852× | 8.0432× |

</details>

## 🔍 Related Issues

https://github.com/flashinfer-ai/flashinfer/issues/4254

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [ ] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

### Latest two-GPU regression

Validated commit `d3bdcc09570e63f598cfc3983c7713e078899703` on one
x86_64 host with **two NVIDIA B200 GPUs**, NV18 connectivity, and
bidirectional CUDA peer access. Environment: NVIDIA PyTorch 26.08
container, PyTorch `2.14.0a0+4fdf77b940.nv26.08`, CUDA 13.4.

- The unchanged native MPI2 test **passed on both ranks, with zero
skips**. Each rank reported `1 passed` in **199.72 seconds**, including
first-use compilation. The enclosing successful managed step took
**264.8 seconds** end to end. The complete sequence from the first
submitted attempt, including container setup, diagnosis and retries,
took **87.2 minutes**; these are validation turnaround times, not kernel
benchmark timings.
- The **24 interface tests passed in 3.80 seconds** on parent commit
`7a1df219dc8cb752dd6d19c061cd2f72a15e302b`. Those completed results are
retained separately; the only subsequent code change is the NVLink
discovery fix below, exercised by the native run.
- NVLink discovery now increments its available-link count only after a
successful state query. On this platform, querying a nonexistent link
can report a P2P capability before its state query raises
`NotSupported`; counting it first caused a false unsupported-device
result. Both GPUs now report **18 valid / 18 active links**. Valid
inactive links still fail the all-links-up requirement. No hardware
check, test assertion, or skip condition was disabled.

This is **same-node communication/backend integration correctness**,
including the full TRT-LLM → Cake → TRT-LLM lifecycle. It is not a new
performance result, multi-node FABRIC/IMEX validation, or SGLang serving
run. TensorRT-LLM remains the default; Cake remains explicit opt-in.
GitHub CI is evaluated separately on the new commit.

### Earlier targeted validation

Targeted validation at `e37c1a37a6ae87a4bf8ad6e89890c9b1155068b2` on two
NVIDIA B200 GPUs (CUDA 13.0, PyTorch `2.13.0+cu130`):

- Interface tests: **24 passed in 1.49 seconds**; the native MPI2 case
was deselected for this invocation.
- Native MPI2 public-API test: **passed on both ranks in 7.80–7.81
seconds**, with no skips. It runs TRT-LLM → Cake → TRT-LLM in one
process and checks mixed-width payload alignment, non-divisible expert
placement, EPLB, quantized combine outputs, external outputs, separate
backend workspaces, and final single-active-rank rounds for both
backends.
- Ruff 0.12.8 checks passed; the changed Python files were
Ruff-formatted and the changed CUDA section was checked with
clang-format 19.1.1.

Reproduction:

```bash
pytest -q tests/comm/test_mnnvl_moe_alltoall_fused_adapter.py -k 'not public_mpi2'
mpirun --oversubscribe --bind-to none -np 2 python -m pytest -q -rA \
  tests/comm/test_mnnvl_moe_alltoall_fused_adapter.py -k public_mpi2
```

The successful native-validation step took **197.6 seconds end to end**,
including environment startup and checks; its pytest runtime was **7.81
seconds**. The validation sequence including setup, repairs, and retries
took about **39 minutes**. These are validation turnaround times, not
kernel timings. This is communication-layer correctness validation, not
a new SGLang serving run.

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

Please review the explicit backend boundary and coexistence behavior. No
environment variable, architecture-triggered default switch, or silent
Cake fallback is introduced.

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [43550a8](https://github.com/flashinfer-ai/flashinfer/commit/43550a80857ea385f081b9cb1d019b137a96539d)

- **作者**: yifeis-nv
- **时间**: 2026-09-11T09:16:06Z
- **提交信息**: feat(gemm): cuTile alpha-beta / masked-bmm / ragged-bmm / block-scaled FP8 GEMM (#4020)

## 📌 Description

Adds five cuTile GEMM kernels (public `cuda.tile` API), registered as
`backend="cutile"` on existing `flashinfer.gemm` ops — defaults
unchanged.

**Why FlashInfer wants this:** `gemm_fp8_nt_groupwise` gains a
CUDA-graph-safe block-scaled FP8 path that beats cutlass on aligned MoE
segments; `masked_bmm` / `ragged_bmm` / `gemm_alpha_beta` fill
batched/ragged GEMM gaps in the public API.

**Added:** `gemm_alpha_beta`, `masked_bmm`, `ragged_bmm`,
`ragged_block_scaled_bmm`, `gemm_fp8_nt_groupwise` (single + grouped +
aligned-segment TMA fast path via `segment_alignment`).

### FP8 / bmm perf — B300 / sm103, FP8 vs cutlass; bmm vs cutlass bf16

| op · shape | cuTile | native | ratio |
|---|---|---|---|
| gemm_fp8_nt_groupwise single · 4096³ | 1535 TF | 1863 TF (cutlass) |
0.82× |
| gemm_fp8_nt_groupwise single · 2048³ / 2560³ | — | cutlass | 0.85× /
0.84× |
| group_gemm_fp8 **aligned-TMA** · m1024·g8 | — | cutlass | **1.03×** |
| group_gemm_fp8 **aligned-TMA** · m512·g4 / m128·g4 | — | cutlass |
0.66× / 0.60× |
| group_gemm_fp8 arbitrary (gather) · m1024·g8 | 524 TF | cutlass |
0.29× |
| masked_bmm (bmm_bf16) · 8×1024³ | 737 TF | 625 TF (cutlass) | 1.22× |

`gemm_fp8` single's ~0.82× is a cuTile-vs-cutlass FP8-MMA gap (shared by
the persistent bf16 GEMM); aligned callers get the TMA fast path
(`segment_alignment=128`). Arbitrary (non-aligned) segments use the
gather path.

### Dense bf16 GEMM benchmark

`benchmarks/bench_mm_bf16_backend_comparison.py` (canonical
`--providers`/`--csv`, inline correctness verify, `bench_gpu_time`
kernel self-time, speedup-vs-CUTLASS table + heatmap): cuTile `mm_bf16`
vs **CUTLASS** (SOTA) / cuDNN / torch, over square {1024…8192}³ plus
weight-fixed m-sweeps at (n,k) = (4096,4096) and (8192,8192).

On **B200 (sm100)**, cuTile ÷ each backend (>1 = cuTile faster) —
**geomean 1.34× vs CUTLASS, 1.15× vs cuDNN, 0.86× vs torch/cuBLAS**:

| m · n · k | cuTile TFLOP/s | ÷ cutlass | ÷ cudnn | ÷ torch |
|---|---|---|---|---|
| 1024³ | 161 | 1.17× | 3.90× | 0.77× |
| 2048³ | 671 | 1.24× | 1.96× | 0.80× |
| 8192³ | 1415 | **3.07×** | 1.20× | 1.20× |
| 16 · 4096 · 4096 | 25 | 1.00× | 1.05× | 1.00× |
| 512 · 4096 · 4096 | 620 | 1.66× | 1.07× | 1.07× |
| 4096 · 4096 · 4096 | 1219 | 1.56× | 0.81× | 0.81× |
| 64 · 8192 · 8192 | 204 | 0.90× | 1.12× | 0.85× |
| 2048 · 8192 · 8192 | 1285 | 1.63× | 0.80× | 0.80× |

cuTile clearly beats FlashInfer's CUTLASS and cuDNN backends, with the
lead growing with problem size (up to ~3× at 8192³); it trails only on
tiny-M (16/64-row) shapes. Against vendor cuBLAS/torch it trades the
lead by shape — winning the large square GEMMs (8192³: 1.20×) and the
512-row weight-fixed shapes, behind on the rest.

`cuBLASLt` / `TGV` / `TinyGEMM` report **N/A with a reason** in the
sweep — these are benchmark-image build limits, not B200 unsupport: TGV
needs `nvidia-cutlass-dsl` with CuTe-Experimental (the bundled 4.4.2 is
rejected), cuBLASLt's JIT source `mm_bf16_cublaslt.cu` is absent from
the image, and TinyGEMM's JIT build fails on a missing symbol.

## 🔍 Related Issues

Part of a 3-way split of the cuTile migration (attention / quantization
/ GEMM), replacing #3959. Sibling PRs: #4018 (attention), #4019
(quantization).

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

Measured on B300 / sm103:
- group_gemm_fp8 `-k cutile`: 144 passed / 144 skipped
- ragged_block_scaled_bmm: 2 passed — bit-identical to native
`group_gemm_fp8_nt_groupwise` (trtllm)
- ragged_bmm: 9 passed / 6 skipped · gemm_alpha_beta: 16 passed (incl.
the `beta==0` NaN-C regression) · masked_bmm: 8 passed
- CUDA-graph capture + replay: bit-exact vs eager

## Reviewer Notes

Carries the shared `cached_replace_hints` helper in
`flashinfer/cutile/cutile_common.py` (also in the quantization PR,
#4019) — whichever merges second drops the duplicate hunk on rebase.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added new cuTile GEMM entry points: `masked_bmm`, `ragged_bmm`,
`ragged_block_scaled_bmm`, and `gemm_alpha_beta`.
* Added `segment_alignment` support to grouped FP8 GEMM on the cuTile
backend.
* **Performance**
* Improved grouped FP8 execution by moving from per-group launches to a
single fused persistent on-device kernel.
* Added LRU memoization for hinted cuTile kernels to reduce repeated
recompiles.
* **Bug Fixes**
* Ensures `beta=0` ignores existing output values to prevent NaN/invalid
propagation.
* **Tests**
* Added new cuTile correctness coverage for the new GEMM entry points
and alignment behavior.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [c9f0f0d](https://github.com/flashinfer-ai/flashinfer/commit/c9f0f0d90a22b1734733297ec09f0f44d21927cf)

- **作者**: eigen
- **时间**: 2026-09-11T07:19:17Z
- **提交信息**: feat(cake_kda): add fused decode backend for B200 and B300 (#4967)

<!-- .github/pull_request_template.md -->

## 📌 Description

Adds a generated fused KDA decode backend for SM100a/B200 and
SM103a/B300.
Callers select `backend="cake"` or `backend="auto"` with a host-known
state-index
mode; the default remains `backend="cute-dsl"`. The implementation
supports
FP32/BF16 recurrent state, nullable and repeated indices with sequential
updates, padded strides, signed 64-bit slot offsets, caller-owned output
and
CUDA Graph capture.

The 46 checked-in CUDA translation units have unique kernel symbols and
separate JIT identities for each target. Positive-unique FP32 dispatch
now
uses two-resident-CTA wide kernels, a vectorized producer variant for
the
short partial-wave band, and the existing high-work schedules for sparse
later waves. Two compact-async wide-offset variants also apply the
measured
occupancy flag on both architectures (80 registers and three resident
blocks,
without spills).

### Current performance versus CuTe DSL

The latest performance measurements use revision
`7f5616d0361abdf3fa3f2a84fff7dc230bad2534`. Current head
`0203598e3bc21ddc00ecfe185c00732fa5715ca7` removes the one-time
migration
verifier and its legacy benchmark inheritance option. CUDA sources,
JIT/runtime
code, correctness tests and GPU timing functions are unchanged. Fresh
benchmarks
and same-revision checkpoint resume remain available.
Speedup is paired CuTe DSL latency divided by candidate latency.

| GPU / inventory | Candidate GM (µs) | CuTe DSL GM (µs) | Speedup |
Minimum | Faster rows |
| --- | ---: | ---: | ---: | ---: | ---: |
| B200 / 1,315-case composite | 76.743111 | 78.589476 | 1.024068495x |
1.001795332x | 1315/1315 |
| B200 / official 21-case subset | 17.112648 | 17.951588 | 1.049057741x
| 1.007284660x | 21/21 |
| B300 / official 21-case composite | 16.754023 | 17.597753 |
1.050359822x | 1.010097845x | 21/21 |

The B200 composite combines 187 remeasured affected cases with 1,128
unchanged
cases. B300 combines 11 remeasured cases with 10 unchanged cases.
Unchanged
cases retain their measurement identities; the composites are not full
reruns.
B200 uses cold-L2 CUPTI/CUDA-Graph ABBA against the public CuTe DSL
fallback;
B300 uses its official paired benchmark protocol. Assess export overhead
with
the direct source/export comparison below.

### Current source/export performance

All 46 variants on each architecture pass canonical qualification
(92/92).
Source and export are paired in the same measurement environment.
Geometric
means (GM) include all 46 variants on each architecture.

| GPU | Source GM (µs) | Export GM (µs) | Source / export | Export
faster / tied / slower |
| --- | ---: | ---: | ---: | ---: |
| B200 | 13.056910 | 13.017657 | 1.003015360x | 22 / 5 / 19 |
| B300 | 12.765178 | 12.711863 | 1.004194117x | 32 / 6 / 8 |

Export GM latency is 0.301% lower on B200 and 0.418% lower on B300. Some
individual exports are slower. The largest measured latency increases
are:

| GPU | Variant | Source (µs) | Export (µs) | Export latency increase |
| --- | --- | ---: | ---: | ---: |
| B200 | `pr_eval_h32_f32` | 7.584 | 7.808 | +2.954% |
| B300 | `compact_async_pr_eval_h96_f32` | 11.745 | 12.032 | +2.444% |

Qualification requires `source/export >= 0.97`; passing does not mean
zero
slowdown for every variant. Minimum ratios are 0.971311475x on B200 and
0.976146941x on B300. All variants pass correctness, output/state, graph
replay, zero-allocation, activity and source/artifact identity checks.

Timing uses three counterbalanced groups, 10-ms warmup and 30-ms
measurement
per arm, fixed CUDA Graph history and cold-L2 CUPTI. Directional
disagreement
and endpoint drift each have a 0.02 limit; observed maxima are
0.001295442/0.004203447 on B200 and 0.006066082/0.006088898 on B300.
Four variants use explicit retained-factory bindings; 42 use production
dispatch.

The final canonical batches cover seven B200 variants and six B300
variants.
Exporter runtime / physical turnaround is 714.5 / 860.993270 s on B200
and
604.5 / 714.739445 s on B300, separate from the kernel latencies above.

## 🔍 Related Issues

Related to #4254.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] Current-head pre-commit
[34539855184](https://github.com/flashinfer-ai/flashinfer/actions/runs/34539855184).

## 🧪 Tests

The runtime qualification below applies to unchanged kernel/runtime/test
files
from the measured revision named above.

- [x] Selector tests: 60 passed, 27 deselected; 9.39 s pytest runtime,
  26.974036 s physical turnaround.
- [x] Canonical source/export validation: 46/46 on B200 and 46/46 on
B300,
  including correctness, state, graph replay and all timing gates.
- [x] Separate BF16 synccheck and racecheck: zero errors/hazards.
- [x] Cleanup inspection: Python syntax and diff whitespace checks pass;
  the removed verifier has no remaining in-repository references.
- [ ] Current-head documentation build
[34539855087](https://github.com/flashinfer-ai/flashinfer/actions/runs/34539855087).
- [x] Current-head public API/documentation check
[34539855039](https://github.com/flashinfer-ai/flashinfer/actions/runs/34539855039).
- [ ] Current-head PR Test
[34540071846](https://github.com/flashinfer-ai/flashinfer/actions/runs/34540071846),
triggered through `run-ci`; pending.
- [x] Current-head review approval.

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

Review target-specific JIT identities, FP32 occupancy/dispatch
boundaries,
host-known index modes, sequential repeated-index updates, offset width
and
fallback behavior. The baseline and source/export tables report
different
comparisons; individual export slowdowns are shown explicitly.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **New Features**
- Added an optional Cake backend for fused KDA decoding on supported
NVIDIA architectures, with explicit and automatic backend selection.
- Added state-index modes for unique, nullable, and repeated state
usage.
- Added optimized fused decode paths supporting BF16/F32 data, wide slot
offsets, repeated states, and multiple head configurations.
- Added strict B200/B300 benchmarking with correctness checks,
checkpointing, and performance comparisons.

- **Tests**
- Added comprehensive dispatch, correctness, architecture, layout, and
CUDA graph coverage.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [82090ee](https://github.com/flashinfer-ai/flashinfer/commit/82090eedd5b47012f28aca19353e92ca25ad49ed)

- **作者**: Brian K. Ryu
- **时间**: 2026-09-11T07:01:36Z
- **提交信息**: fix(test): pin the GDN disk-cache round-trip test to the flashinfer backend (#5104)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

`tests/gdn/test_cute_dsl_kernel_cache.py::test_nontranspose_disk_cache_round_trip`
fails deterministically on SM100/SM103 (B200, GB200, GB300) with
`AssertionError: expected one exported artifact, got []`.

Root cause is a cross-PR dispatch interaction, not a disk-cache bug: the
test (added in #4912, merged Sept 8) calls `gated_delta_rule_decode`
with the default `backend="auto"` and asserts the CuTe-DSL nontranspose
kernel exports one artifact. #4581 (merged Sept 9 — the day the failures
began) added the Cake GDN backend, which `auto` now tries *first* on
SM100/103; it handles the test's BF16 decode and returns, so the
CuTe-DSL kernel under test never compiles and nothing is exported. This
also explains the arch fingerprint: the test fails on B200/GB200/GB300
(Cake-eligible) and passes on H100 (SM90, where Cake falls through to
the CuTe-DSL kernel). Each PR was green alone; composed they are red.

Fix: pin both `gated_delta_rule_decode` calls in the test to
`backend="flashinfer"` (the dispatcher's explicit Cake bypass), so the
test exercises the backend whose cache it verifies — robust to future
`auto`-dispatch changes.

## 🔍 Related Issues

<!-- Link any related issues here -->

Fixes #5091. Interaction between #4912 and #4581.

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

* **Tests**
* Updated kernel cache round-trip coverage to explicitly use the
FlashInfer backend for both decode operations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-09-12
**监控日期**: 2026-09-11
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4376
- **最后更新**: 2026-09-12T00:03:30Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-09-12
**监控日期**: 2026-09-11
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34497
- **最后更新**: 2026-09-11T17:51:42Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Nianze Wu, Steven Liu

## AI分析总结

# diffusers 昨日提交分析（共 2 条）

## 1. 主要更新类型
- **重构/工程规范**：将库内非交互式消息统一改由 logger 输出（#14682）。
- **文档更新**：改进文档导航结构（#14537）。
- 整体属于“内部质量 + 文档体验”类维护性提交，而非模型功能新增。

## 2. 关键变更点及与项目方向的关系
- **日志统一化**：把原先散落的 print/提示信息改为标准 logging 通道，并移除专门的日志回归测试。这契合 diffusers 作为被广泛集成的库的定位——库代码不应直接向 stdout 打印，以免污染下游应用（如 WebUI、训练脚本）的输出。
- **文档导航重构**：调整目录排列、增加交叉链接与标题，降低新用户查找 pipeline、scheduler、训练指南等内容的门槛，呼应项目“易用、可扩展”的定位。

## 3. 对项目的影响与潜在意义
- 日志规范化提升了库的可嵌入性与可维护性，便于用户按级别过滤信息，也利于未来统一调试与告警。
- 文档导航优化直接改善上手体验，对扩散模型生态中大量非专业用户尤为重要，有助于降低使用与贡献门槛。
- 两者均不改变 API 行为，属于低风险、长期收益型改动。

## 4. 值得关注的技术点
- 移除“专用日志回归测试”意味着团队可能认为日志行为已由通用测试或约定覆盖，需关注后续是否引入统一日志规范。
- 文档侧强调交叉链接与标题层级，反映项目在文档信息架构上的持续投入，可能与后续教程/API 重组相关。

## 5. 结合 README 背景看项目发展
README 显示 diffusers 定位为“扩散模型的最先进工具箱”，强调模块化与易用性。本次提交虽小，却从两方面支撑该目标：一是让库更“安静、专业”，适合作为依赖被集成；二是让文档更“可导航”，帮助用户快速找到 pipeline 与调度器。这类工程与文档打磨，是项目从“能用”走向“好用、可规模化维护”的必要积累，为后续功能扩展奠定稳定基础。

## 详细提交记录

### [c419dac](https://github.com/huggingface/diffusers/commit/c419dac0152186060246c93a095bc1bfaea342b3)

- **作者**: Nianze Wu
- **时间**: 2026-09-11T17:51:16Z
- **提交信息**: Route non-interactive library messages through loggers (#14682)

* fix: route library messages through loggers

* test: remove dedicated logging regressions

### [b27b69c](https://github.com/huggingface/diffusers/commit/b27b69c1d6dbe7ca45194970ce11ef555c895ef2)

- **作者**: Steven Liu
- **时间**: 2026-09-11T15:35:50Z
- **提交信息**: [docs] Improve navigation (#14537)

* docs

* rearrange

* cross links

* titles

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-09-12
**监控日期**: 2026-09-11
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 432
- **最后更新**: 2026-08-31T08:28:31Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-09-12
**监控日期**: 2026-09-11
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13088
- **最后更新**: 2026-09-11T11:47:45Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Hong Zhang, Zhongjie Duan

## AI分析总结

# DiffSynth-Studio 昨日提交分析（第 1/1 批）

## 1. 主要更新类型
- **功能新增为主**：两个提交均为新模型支持（YuE2、LTX-2.5），属于核心能力扩展。
- **附带重构与文档更新**：LTX-2.5 提交包含管线合并、模块扁平化、训练脚本与文档重写。
- **Bug 修复与性能优化**：修复 VRAM 管理、CPU offload 下的模块引用问题，并调整训练策略（ZeRO-2 → ZeRO-3 兼容性处理）。

## 2. 关键变更点及与项目方向的关系
- **LTX-2.5 统一进 LTX2AudioVideoPipeline**：放弃独立 `ltx25_audio_video.py`，体现项目"统一管线、多模型复用"的设计取向。
- **DiffVAE 扁平化**：将 VAE 拆为单一 decode 接口并支持自动 tiling，降低模块耦合，便于显存优化与复用。
- **新增 BF16/INT8 变体、低显存示例**：延续项目对消费级硬件友好、量化推理支持的定位。
- **补充训练脚本与文档**：从"仅推理"向"推理+训练"闭环扩展，符合 DiffSynth 作为全流程扩散工具箱的定位。

## 3. 对项目的影响与潜在意义
- 扩展了音视频生成模型矩阵（YuE2 偏音频，LTX-2.5 覆盖 T2AV/I2AV/A2V/T2A/Retake 等多任务），增强多模态覆盖度。
- 统一管线与扁平化 VAE 降低了后续接入新模型的边际成本，利于生态扩张。
- INT8 与低显存支持扩大了可用用户群，提升工程实用性。

## 4. 值得关注的技术点
- **tokenwise AV 跨注意力 scale/shift** 与 keyframes 绝对位置嵌入，是音视频联合建模的关键改动。
- **stage1 蒸馏 ancestral schedule** 与 auto_duration 单次调用，简化推理流程。
- **ZeRO-3 与 Gemma4 文本编码器不兼容**：因模型在 `deepspeed.zero.Init` 内构造，改用 ZeRO-2 + CPU offload，是分布式训练的实用经验。
- **VRAM 包装模块的别名引用修复**：通过 owner 解析，确保 CPU offload 下走包装路径，属易错细节。

## 5. 基于 README 背景的项目发展影响
README 显示 DiffSynth-Studio 定位为面向 ModelScope 的扩散模型全流程工具（推理、训练、量化、显存优化）。本次提交正是该定位的典型落地：一方面持续扩充前沿模型支持（YuE2、LTX-2.5），保持与社区模型迭代同步；另一方面通过统一管线、扁平化模块、INT8 与低显存示例，强化"易用+可训练+省显存"的核心竞争力。整体看，这批提交巩固了项目作为多模态扩散模型一站式平台的地位，并为后续模型接入提供了更清晰的工程范式。

## 详细提交记录

### [32ef37e](https://github.com/modelscope/DiffSynth-Studio/commit/32ef37e4fc38400f9fe14b1affd335dad9cdf50d)

- **作者**: Zhongjie Duan
- **时间**: 2026-09-11T09:15:33Z
- **提交信息**: support YuE2 (#1686)

### [a98c6d4](https://github.com/modelscope/DiffSynth-Studio/commit/a98c6d4b46083033406726c71384f368077a0007)

- **作者**: Hong Zhang
- **时间**: 2026-09-11T07:53:55Z
- **提交信息**: Support LTX-2.5 (#1683)

* feat: add LTX-2.5 inference pipeline

* Support LTX-2.5: unified pipeline, flat DiffVAE, INT8 variants and inference examples

- Merge LTX-2.5 into LTX2AudioVideoPipeline (drop separate ltx25_audio_video.py)
- Register ltx25 DiT / Gemma4 text encoder / feature extractor + connectors / video VAE (DiffVAE + ConvVAE) / audio VAE / vocoder / duration head, BF16 and INT8 ConvRot variants
- Flatten DiffVAE into diffsynth/models/ltx25_diffusion_video_vae.py with a single decode interface and auto tiling
- Add keyframes abs pos embedding and tokenwise AV cross-attention scale/shift to ltx2_dit
- Add stage1 distilled ancestral schedule unit, audio-only (T2A) and A2V freeze support, auto_duration in one pipe call
- VRAM management maps for new modules; low-VRAM and standard inference examples for T2AV/I2AV/A2V/T2A/Retake/IC-LoRA/INT8

* Fix LTX-2.5 VRAM management, add training scripts and docs

- Resolve aliased/preprocessor module references through the owner in ltx2_dit so VRAM-wrapped modules are used under CPU offload
- Move STFT/mel buffers and DiffVAE raw parameters (scale_shift_table, fused QKV) to the input device/dtype at the use site
- Read functional projection weights through the VRAM wrapper computation path; reduce the DiffVAE module map to leaf-level entries since the decoder calls block methods directly
- Treat missing generate_video input param as True so training caches video positions (T2A keeps generate_video=False)
- Add LTX-2.5 T2AV split training scripts (LoRA/full/debug), validate scripts and a series-local zero3 accelerate config
- Rewrite LTX-2.5 docs for the unified pipeline, training and unsupported features; add README news and model table rows
- Drop the PR leftover LTX-2.5-Keyframe-Interpolation low-VRAM script (keyframes are covered by I2AV)

* Use ZeRO-2 with CPU offload for LTX-2.5 full training

ZeRO-3 is incompatible with the Gemma4 text encoder: DiffSynth constructs models inside
deepspeed.zero.Init, where transformers' _init_weights indexes weight[padding_idx] on an
empty sharded embedding and raises IndexError. Replace the series-local zero3 config with
the ZeRO-2 + CPU optimizer/param offload config used by the LTX-2.3 full scripts.

* Remove decorative separator comment in ltx2_audio_vae

* Fix LTX-2.5 A2V fidelity and two-stage refinement

- Return the original input audio (resampled and trimmed) when the audio modality is
  fully frozen, matching the upstream A2V pipeline which skips the VAE/vocoder round
  trip to preserve fidelity (mel corr vs input 0.928 -> 0.998)
- Run the second stage without classifier-free guidance, as upstream uses a simple
  denoiser there; the stage-1 cfg scale previously leaked into stage 2
- Align the stage-2 distilled LoRA strength default with upstream (1.0 instead of 0.8),
  which removes residual dithering in dev two-stage outputs

* Remove dead code from the LTX-2.5 DiffVAE module

Drop unreferenced helpers, tiling constructors and the NATTEN attention fallback that
the portable eager path never selects. Verified bit-identical outputs (max abs pixel
diff 0) for the distilled T2AV and I2AV keyframe examples before/after.

* Point LTX-2.3 examples at the current spatial upscaler checkpoint

The Lightricks/LTX-2.3 repo no longer ships ltx-2.3-spatial-upscaler-x2-1.0.safetensors;
the registered ltx2_latent_upsampler hash matches the x2-1.1 file, so update the example
scripts, docs and the registration example comment accordingly.

* Skip video decoder validation during training caching stages

The decoder selector validated the loaded decoder component at unit execution time, which
breaks split training for LTX-2/2.3 repackaged checkpoints whose stage 1 loads only the VAE
encoder. Caching stages never decode, so skip the validation when the scheduler is in
training mode; inference behavior is unchanged.

* Strip docstrings from the LTX-2.5 DiffVAE module

Remove 192 docstring blocks (~1000 lines) from the portable DiffVAE implementation; the
module keeps its inline WHY comments. Distilled T2AV output remains bit-identical
(max abs pixel diff 0) to the pre-change baseline. File size 6391 -> 5036 lines.

* Refine the LTX-2.5 example matrix and default negative prompt

The dev weights are the general-purpose checkpoint, so they now cover the full feature
set: OneStage/TwoStage T2AV and I2AV examples are added in both the standard and the
low-VRAM directories. The distilled and INT8 checkpoints keep a single T2AV example each,
so the distilled I2AV scripts are removed; IC-LoRA stays a distilled exception because
upstream runs both of its stages on the distilled weights. Docs and README list the
resulting ten-row matrix.

LTX-2.5 also ships a longer default negative prompt than LTX-2.3: upstream prefixes the
shared tag list with has_subtitles, has_blurbox, transition from black, transition to
black and speech_ending_short. Add an "LTX-2.5" entry to pipe.default_negative_prompt and
switch every 2.5 example, low-VRAM example and validation script to it (the T2A scripts
previously used the placeholder "noise").

* Reformat the LTX-2.5 Gemma config literal

LTX25_GEMMA_CONFIG was a raw pprint dump with single quotes and hanging indentation.
Restyle it to match the other text encoder configs (double quotes, four-space indent, one
key per line, inline leaf dicts) and collapse the 48-entry layer_types list into its
repeating five-sliding-plus-one-full pattern. Formatting only: the resolved
Gemma4UnifiedConfig.to_dict() is byte-identical to the previous one.

* Restore upstream preprocessor init timing and stage-2 LoRA default

Moving _init_preprocessors into __init__ made the argument preprocessors capture the
plain modules before VRAM management replaces them with wrappers, so under CPU offload
the preprocessors called stale modules whose weights never onload. PR #1602 built the
preprocessors at the start of every forward, after wrapping; restore that timing and
drop the OwnerModuleProxy workaround it had made unnecessary.

Also restore the upstream stage2_lora_strength default of 0.8, which the LTX-2/2.3
two-stage examples rely on, and pass 1.0 explicitly in the LTX-2.5 two-stage examples
whose distilled stage-2 LoRA needs full strength.

* verified dit clean

* Restore upstream VRAM maps and VAE code, merge the 2.5 tokenizer into the TE file

The VRAM module maps and the audio/video VAE modules carried changes that only existed
to support our own earlier fine-grained map experiment: PerChannelStatistics, Snake and
sibling vocoder entries, the LTX2AudioEncoder entry, the LTXModel block-level entry and
the use-site STFT/mel casts. With the maps back to the upstream layout the vocoder and
audio encoder fall back to the whole-model wrap exactly as LTX-2.3 runs today, so those
code changes are reverted too, together with the string-to-Enum coercions in the video
VAE whose only consumers were string extra_kwargs we added for the 2.5 entries. The only
remaining map delta is the LTX-2.5 DiffusionVideoDecoder entry, whose flat class path and
leaf-level wrapping the 2.5 decoder requires.

LTX25GemmaTokenizer moves verbatim into ltx25_text_encoder.py, mirroring how the LTX-2.3
tokenizer lives inside its TE file, and the 2.5 registry entries are regrouped by model
hash with concrete dev-file example comments.

* Unify LTX-2.5 model loading with the shared registry and a Repackage checkpoint

Register the LTX-2.5 components under the same model names as LTX-2/2.3 so
from_pretrained fetches every version through one shared path; only the tokenizer
construction stays version-specific. The text encoder post modules are the single
component whose weights are scattered across two upstream files (feature extractor in
the TE checkpoint, connectors in the transformer checkpoint), so they are packed into
DiffSynth-Studio/LTX-2.5-Repackage/text_encoder_post_modules.safetensors in target key
layout, needing no state dict converter, and the packed Gemma4 tokenizer assets are
unpacked into an HF-style tokenizer directory so tokenizer_config works like LTX-2.3.

Pipeline cleanups along the way: the video decoder is selected by availability
(conv decoder first, diffusion decoder as fallback), gemma_path and load_duration_head
are gone, and the upstream section comments, import layout and upsampler fetch position
are restored.

* Drop the unused Gemma3 processor and unify tokenizer construction

The Gemma3Processor was assigned but never read anywhere in the repository, so remove
it together with its attribute and imports. Tokenizer construction collapses to picking
the version-specific class and instantiating it with tokenizer_path, which is now the
parameter name for LTX25GemmaTokenizer as well.

* Simplify video decoding and auto duration handling

The decoder selector unit is gone: the pipeline keeps a single video_vae_decoder
attribute, filled with the ConvVAE decoder when loaded and the DiffVAE decoder otherwise,
and __call__ passes the tiling and seed arguments straight to decode(). Both decoders
accept **kwargs so the uniform argument set needs no branching; the DiffVAE decoder takes
seed/rand_device and builds its sampling generator internally, offset by 42 from the
denoise seed, and tiles automatically when tiled is set, matching the official pipeline
default. Auto duration validation moves into the AutoDuration unit, which now declares
onload_model_names and clamps the requested bounds into (0, 20] instead of raising.

* Keep NoiseInitializer in upstream shape and rename generate_video to audio_only

NoiseInitializer goes back to the upstream process_stage/process structure; the only
additions are the generate-video guard and a build_video_keyframes_mask helper that
returns the LTX-2.5 first-frame marker (None for other versions), so the mask is rebuilt
at every stage resolution automatically. The token-layout noise, unpatchify bridges and
ancestral transforms are gone: noise is drawn in the 5D latent layout like LTX-2.3.

The generate_video flag is renamed to audio_only with inverted polarity, which removes
the None-normalization trick: the unit runner passes None for missing keys, and a falsy
value now correctly means "generate video" during training caching stages.

* Give DiffVAE decode explicit tile sizes with a min-tile fallback

The decode path accepts tile_size_in_pixels / tile_size_in_frames (overlaps stay
halo-derived, since DiffVAE ramps need complementary masks) and validates them; any
invalid configuration falls back to the automatic tiling instead of raising. The automatic
path now returns the minimum legal tile (spatial floor 512 px, temporal 80 frames), which
keeps the decode peak around 7 GB at 1024x1536x121 instead of the recommender's
spare-VRAM-hungry choice (~68 GB measured). Inference examples pass tile_size_in_frames=80
and carry a comment pointing at the conv vae decoder as the low-VRAM alternative.

* Add AncestralFlowMatchScheduler and revert non-essential pipeline deviations

- Move the rectified-flow ancestral Euler step into AncestralFlowMatchScheduler
  (flow_match.py base classes stay byte-identical to upstream); installed in
  __call__ for LTX-2.5 distilled runs, stage 2 restores the base scheduler.
- Revert base_pipeline.py to upstream: drop the dead generate_noise generator
  parameter and handle disabled-modality predictions with a 0 placeholder at the
  model_fn_ltx2 return site instead of a CFG None guard.
- Remove LTX-2.5 special-casing from denoise_stage (timestep dtype/sigmas switch,
  cfg_scale read, timestep_scale), the PipelineChecker raises, and cosmetic
  reformats; denoise_stage and PipelineChecker now match upstream exactly.
- Point LTX25TextEncoder.forward at the inner hidden-states pass so both text
  encoder generations share one call site in the prompt embedder unit.
- Run LTX-2.5 one-stage examples at half resolution, matching LTX-2/2.3.
- Ignore *.mp4 and *.wav test outputs.

* Inherit LTX25TextEncoder from Gemma4UnifiedForConditionalGeneration

- Drop the wrapper layout: the class now inherits the transformers model, the
  config literal lives in __init__ (no deepcopy, no module-level constant), and
  the forward override is gone since the inherited forward returns hidden states.
- Delete reset_non_persistent_buffers: rope values match transformers' own init
  bit-for-bit and the embed_scale difference cancels in RMSNorm, verified by
  end-to-end bit-identical encodings with and without it.
- Update the state dict converter key prefixes for the inherited layout
  (model.language_model.*, model.embed_vision.*, model.embed_audio.*, lm_head).

* Mark appended reference tokens as non-keyframes in the keyframes mask

Upstream extends the keyframes mask with zeros for given-content conditioning
(keyframe_cond.py:86, reference_video_cond.py:102-104: "Reference tokens are
never keyframes"); we concatenated ones, which added the learned keyframe
embedding to tokens that must not receive it. Verified against the target
library with per-channel probes (appended tokens stay unmarked, first latent
frame stays marked unconditionally).

* Decode frozen retake audio through the audio VAE like upstream

The audio_fully_frozen shortcut returned the resampled input waveform and
skipped the audio decoder when the retake mask was all-zero; upstream always
decodes the (frozen) audio latent (retake.py:326). Restore the unconditional
decode path and drop the now-unused resample_waveform import.

* Revert .gitignore to the upstream version

The *.mp4 / *.wav ignore rules were local-only convenience for test outputs and
must not ship in the integration branch.

* Merge LTX-2.5 docs into the LTX-2 page and keep position precision per generation

- Treat LTX-2.5 as a version update: fold its content into docs/{zh,en}/Model_Details/LTX-2.md,
  delete the standalone LTX-2.5 pages, point README news/links at the merged page and drop the
  duplicated doc link entry.
- Keep video positions in fp32 for LTX-2.5 and cast them to the model dtype only for LTX-2/2.3;
  bf16 time coordinates made the 2.5 outputs flicker while fp32 breaks the older generations.
- Drop the dead ff_bias plumbing from LTX2TextEncoder and the redundant prose comments in the
  LTX-2.5 example scripts.

* revert gitignore

* refactor ltx vram

* final check

* Drop redundant cfg_scale from LTX-2.5 examples to use the pipeline default

The LTX2AudioVideoPipeline defaults cfg_scale to 3.0. Remove the explicit
cfg_scale=3.0 from the LTX-2.5 inference and validate scripts (no behavior
change) and remove cfg_scale=4.0 from the T2AV validate scripts so they also
fall back to 3.0. Keep cfg_scale=1.0 in the distilled / INT8-ConvRot /
IC-LoRA-Pixel-Spatial-Upscaler scripts, where CFG is intentionally disabled.

* Point LTX-2.5 T2AV training at its own dataset instead of LTX-2.3's

The LTX-2.5 T2AV split-training scripts downloaded and read from
ltx2/LTX-2.3-T2AV-splited. Give LTX-2.5 a dedicated example dataset
(ltx2/LTX-2.5-T2AV-splited), matching the I2AV scripts, so each model
version references its own dataset.

---------

Co-authored-by: DiffSynth-Studio Bot <noreply@github.com>

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-09-12
**监控日期**: 2026-09-11
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 35828
- **最后更新**: 2026-09-12T00:16:35Z

## 提交统计

- **昨日提交总数**: 34
- **提交者数量**: 28
- **主要提交者**: zijiexia, AMD-yanfeiwang, Shangming Cai

## AI分析总结

## 一、主要更新类型

本批34条提交以**Bug修复**和**AMD/NPU硬件适配**为主，辅以性能优化、CI调整与文档更新。功能新增集中在LoRA、缓存路由与推理解析器；重构涉及注意力图变体与PD失败通知机制。

## 二、关键变更点与项目方向

- **会话与稳定性修复**：修复被拒请求后的会话空闲超时、NCCL图缓冲注册导致的纯DP解码挂起、paged sparse-decode gather的内存安全（零填充、int64偏移、FP8反量化），直接提升长时服务可靠性。
- **AMD生态深化**：AITER shuffled block FP8权重校验、GLM-5.2 MXFP4的Triton DSA后端、DCP支持、SWA KV池解析、统一KV外部链接器等，显示SGLang正系统性补齐ROCm/MI350X/MI355X能力。
- **NPU与国产硬件**：Ascend Memcache Hicache L3存储后端、GLM-5.2 FP8显存优化、Docker工作目录调整，延续多硬件后端战略。
- **PD分离架构**：跨后端共享prefill→decode失败通知、nixl TransferInfo字段读取、路由元数据经/v1/responses传播，强化解耦推理的健壮性。
- **Diffusion与解析器**：SANA-WM卷积后处理、Hopper LTX BF16舍入保持、Granite 4.2推理解析器、GLM-5.3模板自动识别，扩展多模态与模型覆盖。

## 三、影响与潜在意义

修复类提交直接降低生产环境挂起与内存越界风险；AMD/NPU适配扩大可部署硬件面，契合项目“高性能多后端推理引擎”定位。PD失败通知共享与缓存亲和路由提升大规模分布式部署的容错与命中率。CI裁剪与暂停表明团队在测试成本与稳定性间做权衡。

## 四、值得关注的技术点

- paged sparse-decode的零填充scratch与int64偏移是内存安全的关键细节。
- 禁用TP LM-head all-to-all的NCCL图缓冲注册，揭示图捕获与通信库的深层冲突。
- LoRA在MoE全量/可断prefill CUDA图中的支持，涉及图捕获与适配器动态性的平衡。
- 桶路由保留全局缓存亲和，是缓存感知调度的新思路。

## 五、对项目发展的意义

结合README中SGLang作为高吞吐LLM服务引擎的定位，本批提交体现三条主线：**稳定性加固**（会话、内存、通信）、**硬件广度扩张**（AMD/NPU/ROCm）、**架构演进**（PD分离、统一缓存、图捕获）。这些工作共同支撑其在多硬件、大规模分布式场景下的生产可用性，巩固其作为主流推理框架的竞争力。

## 详细提交记录

### [7d9c57d](https://github.com/sgl-project/sglang/commit/7d9c57da6e3cbd7b5670c178ec453081f3022899)

- **作者**: Byron Hsu
- **时间**: 2026-09-11T23:59:43Z
- **提交信息**: [Session] Fix session idle timeout after rejected requests (#39035)

Co-authored-by: Byron Hsu <byron+per@periodiclabs.ai>
Co-authored-by: Manik Singhal <3400497+Manikvsin@users.noreply.github.com>

### [5f3606c](https://github.com/sgl-project/sglang/commit/5f3606c7b2aec653fcfdbe3465379e700c4a5492)

- **作者**: Kevin Mi
- **时间**: 2026-09-11T23:10:44Z
- **提交信息**: [Cookbook][AMD] Kimi-K3 MI350X/MI355X: pin a ROCm image with the DSPARK graph-capture fix, add measured cell numbers (#39029)

### [6671cfc](https://github.com/sgl-project/sglang/commit/6671cfc77520fb2d07893b992e6ab67db607e75c)

- **作者**: Xinyu Kang
- **时间**: 2026-09-11T22:49:56Z
- **提交信息**: [AMD] Fix weight checking for AITER-shuffled block FP8 weights (#34330)

### [f963d7a](https://github.com/sgl-project/sglang/commit/f963d7a27ccea2c1dd9adaa54b33bffb04e4f975)

- **作者**: YAMY
- **时间**: 2026-09-11T22:47:25Z
- **提交信息**: fix(qsa): make the paged sparse-decode gather memory-safe (zero-fill scratch, int64 offsets, dequant FP8 on gather) (#38851)

### [ec30f19](https://github.com/sgl-project/sglang/commit/ec30f19e4ad3059ed3b05188c1de539959e3df83)

- **作者**: Yanbin Jiang
- **时间**: 2026-09-11T21:40:02Z
- **提交信息**: [LoRA] Support MoE in full and breakable prefill CUDA graphs (#38578)

### [45715e7](https://github.com/sgl-project/sglang/commit/45715e7f20629d1813ff8f543a23bb437128db2e)

- **作者**: Hanming Lu
- **时间**: 2026-09-11T20:10:48Z
- **提交信息**: [Fix] Disable NCCL graph buffer registration for the TP LM-head all-to-all (pure-DP decode hang under request bursts) (#38936)

### [a338a9a](https://github.com/sgl-project/sglang/commit/a338a9a01c217e2d612608bc0700d7aee9fe2b23)

- **作者**: Bingxu Chen
- **时间**: 2026-09-11T19:25:20Z
- **提交信息**: [AMD][CI] Skip failing Wave test and relax multi-LoRA output check (#38585)

### [df64249](https://github.com/sgl-project/sglang/commit/df6424967ab850cc53bf0321904a11a0cce099b2)

- **作者**: zijiexia
- **时间**: 2026-09-11T18:58:30Z
- **提交信息**: [docs] Add the NVIDIA NVFP4 export to the Qwen3.8-27B cookbook (#38611)

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>
Co-authored-by: Jiminator <jimmysh341@gmail.com>
Co-authored-by: Jimmy Shong <69131491+Jiminator@users.noreply.github.com>

### [d7c284b](https://github.com/sgl-project/sglang/commit/d7c284b894e9569c25c2ce0b940dc7113f5c0d30)

- **作者**: Zhang, Jiejing
- **时间**: 2026-09-11T18:48:50Z
- **提交信息**: [AMD] Use the triton DSA backend for GLM-5.2 MXFP4 on MI355X (#39106)

### [833bce9](https://github.com/sgl-project/sglang/commit/833bce9df57fb1dd110a810b9759f1f0d7425884)

- **作者**: billishyahao
- **时间**: 2026-09-11T17:35:51Z
- **提交信息**: [AMD][DCP 1/N] add dcp support for aiter backend (#34432)

Co-authored-by: HAI <hixiao@gmail.com>

### [f69d6fc](https://github.com/sgl-project/sglang/commit/f69d6fc28a9fb5c02498e1b33824f0e5c2dac387)

- **作者**: Jeremy Zhang
- **时间**: 2026-09-11T17:33:38Z
- **提交信息**: [OpenAI] Propagate PD routing metadata through /v1/responses (#35503)

### [ddf02a4](https://github.com/sgl-project/sglang/commit/ddf02a4f5851edc02c9d5387ba4dedf3240e3bee)

- **作者**: Vignesh Sethuraman
- **时间**: 2026-09-11T17:13:48Z
- **提交信息**: [AMD] aiter: resolve SWA KV pool for draft workers + guard paged decode (#38756)

### [4309c7c](https://github.com/sgl-project/sglang/commit/4309c7ce19dc42fb42cc9e7d883691c8dd8bda10)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-09-11T15:31:42Z
- **提交信息**: Fix stale DSV4 indexer metadata names in the TopK v2 dispatch test (#39101)

Co-authored-by: Mohammad Angkad <mohammad.angkad@radixark.ai>

### [d6b5dca](https://github.com/sgl-project/sglang/commit/d6b5dca90cdc18ae0f521a8d6a2376ed68dacc82)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-09-11T15:30:17Z
- **提交信息**: [Diffusion] Optimize SANA-WM convolution post-processing and streaming GDN (#38529)

### [2c10f87](https://github.com/sgl-project/sglang/commit/2c10f87991f7406c79c909a893764fd20184f888)

- **作者**: Shangming Cai
- **时间**: 2026-09-11T15:20:02Z
- **提交信息**: [PD] Read nixl TransferInfo.is_dummy as a field in unit tests (#39100)

### [2a46cf2](https://github.com/sgl-project/sglang/commit/2a46cf2ca0fe284a4ca7cc5b0c35cf0a6ecafe43)

- **作者**: jambow0320
- **时间**: 2026-09-11T15:16:17Z
- **提交信息**: [PD] Share the prefill->decode failure notification across backends (#36612)

Co-authored-by: inkcherry <mingzhi.liu@amd.com>
Co-authored-by: Shangming Cai <csmthu@gmail.com>

### [e016de4](https://github.com/sgl-project/sglang/commit/e016de462c7288d7d7659117948e51a43780570c)

- **作者**: Mick
- **时间**: 2026-09-11T15:07:37Z
- **提交信息**: [diffusion] CI: expose nightly server telemetry coverage (#38782)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [7f09fbc](https://github.com/sgl-project/sglang/commit/7f09fbcd2526a7d953dcda5a9714952b43a97408)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-09-11T15:02:54Z
- **提交信息**: [Diffusion] Preserve BF16 rounding in Hopper LTX QKNorm and RoPE fusion (#38533)

### [dd67a42](https://github.com/sgl-project/sglang/commit/dd67a426346c434ce019f9a98e3902ce5c1ee49e)

- **作者**: Mick
- **时间**: 2026-09-11T14:45:21Z
- **提交信息**: [diffusion] UX: quiet request-path cache diagnostics (#38783)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [593c7a9](https://github.com/sgl-project/sglang/commit/593c7a900d217ab4869d79782234f32a46b4c7bb)

- **作者**: Yousaf
- **时间**: 2026-09-11T14:18:35Z
- **提交信息**: Add granite_thinking_parser reasoning parser for Granite 4.2 (#38693)

Signed-off-by: Yousaf Shah <yousaf.shah@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Xinyuan Tong <xinyuantong.cs@gmail.com>
Co-authored-by: Xinyuan Tong <115166877+JustinTong0323@users.noreply.github.com>

### [335f6aa](https://github.com/sgl-project/sglang/commit/335f6aab27a40e8db13919908caa120ae0cb7b43)

- **作者**: weireweire
- **时间**: 2026-09-11T14:17:36Z
- **提交信息**: [DSV4] Support raw-index output in TopK v2 (#33672)

Co-authored-by: weireweire <20922698+weireweire@users.noreply.github.com>
Co-authored-by: Brayden Zhong <b8zhong@uwaterloo.ca>
Co-authored-by: Po-Han Huang (NVIDIA) <53919306+nvpohanh@users.noreply.github.com>

### [ab9750f](https://github.com/sgl-project/sglang/commit/ab9750fb355edaa792b351fd3183a3141d9a6bd7)

- **作者**: Mick
- **时间**: 2026-09-11T14:04:40Z
- **提交信息**: [diffusion] optimization: pin layerwise host stores in place at their exact size (#39021)

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [e8a36d3](https://github.com/sgl-project/sglang/commit/e8a36d339cb40be84f90afb29a2cb825a6d07f40)

- **作者**: Xinyuan Tong
- **时间**: 2026-09-11T13:02:44Z
- **提交信息**: Auto-detect GLM-5.3 chat templates as glm45/glm47 parsers (#38297)

### [358c163](https://github.com/sgl-project/sglang/commit/358c163250ad3b1f62939b01ce1314a0a31a0365)

- **作者**: Mick
- **时间**: 2026-09-11T11:34:09Z
- **提交信息**: [diffusion] fix: recover ipc jit initialization after interrupted builds (#39034)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [165d8dd](https://github.com/sgl-project/sglang/commit/165d8dd17736fa4938f2e73018f26835cd6e0778)

- **作者**: James
- **时间**: 2026-09-11T10:54:00Z
- **提交信息**: [NPU][Hicache] Add Ascend Memcache Hicache L3 storage backend (#38827)

### [747734d](https://github.com/sgl-project/sglang/commit/747734dce44cabaa2cfc80000d8f03eb160e2ed3)

- **作者**: Liwansi
- **时间**: 2026-09-11T10:48:45Z
- **提交信息**: [NPU]glm5.2 fp8 memory opt (#38807)

### [a4ff563](https://github.com/sgl-project/sglang/commit/a4ff5634b82546679704c42c984d7f950203922e)

- **作者**: Shangming Cai
- **时间**: 2026-09-11T10:04:57Z
- **提交信息**: [CI] Add CI permissions for PP contributor stepinto (#39077)

### [8e7deb3](https://github.com/sgl-project/sglang/commit/8e7deb329edbd7bb4b3ca1c706eece44c425246e)

- **作者**: Vincent Gao
- **时间**: 2026-09-11T09:41:27Z
- **提交信息**: [Router] Preserve global cache affinity with bucket routing (#38814)

Signed-off-by: Vincent Gao <vincentbo@linux.alibaba.com>

### [822e73c](https://github.com/sgl-project/sglang/commit/822e73ccddc0297e9901042d4aab7fcccc11f1a6)

- **作者**: Niko Ma
- **时间**: 2026-09-11T08:49:29Z
- **提交信息**: [Unified Cache][AMD] Support DeepSeek-V4 unified KV in direct external linkers (#38269)

Co-authored-by: amd-danli103 <danli103@amd.com>
Co-authored-by: Duyi-Wang <duyi.wang@amd.com>
Co-authored-by: TianDi101 <tiandi920722@gmail.com>

### [0bae676](https://github.com/sgl-project/sglang/commit/0bae67648a9b04562f7d13b00c88c4c4cb0cdd8b)

- **作者**: Jensen
- **时间**: 2026-09-11T08:30:07Z
- **提交信息**: [NPU] Change npu.Dockerfile working directory to /sgl-workspace (#38968)

### [ad5af53](https://github.com/sgl-project/sglang/commit/ad5af539cd39e9af10ef318d3f8a50f5d6f9c153)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-09-11T08:04:16Z
- **提交信息**: [CI] Trim DSV4 trtllm B200 tests (#39013)

Co-authored-by: Mohammad Angkad <mohammad.angkad@radixark.ai>

### [17fa5ad](https://github.com/sgl-project/sglang/commit/17fa5ad3276aec39f7626abcf7bbdf3dcff8297f)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-11T07:45:58Z
- **提交信息**: [Refactor] Generalize attention graph variants in the decode runner (#38993)

### [f618022](https://github.com/sgl-project/sglang/commit/f618022b73f813daa6f25e615b0269c82c66a941)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-09-11T07:19:24Z
- **提交信息**: [AMD][CI] Temporarily pause MI355X disaggregated nightly (#39044)

Co-authored-by: Chen <bingxche@amd.com>

### [69aa46b](https://github.com/sgl-project/sglang/commit/69aa46b2fa6f099e92c345eae1c0c9a42b5d66b4)

- **作者**: AMD-yanfeiwang
- **时间**: 2026-09-11T07:12:24Z
- **提交信息**: [ROCm] Raise HiCache JIT block quota for mapped-host throughput (#39036)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-09-12
**监控日期**: 2026-09-11
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1275
- **最后更新**: 2026-09-10T02:30:25Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-09-12
**监控日期**: 2026-09-11
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 91525
- **最后更新**: 2026-09-11T23:53:31Z

## 提交统计

- **昨日提交总数**: 43
- **提交者数量**: 37
- **主要提交者**: Matt, JinYan Su, Micah Williamson

## AI分析总结

# vLLM 昨日提交分析（共 43 条）

## 1. 主要更新类型分布

- **Bug 修复**：约 18 条，占比最高，覆盖 KV Connector、MLA、YaRN、CUDA Graph、多模态视频解析、DP padding、Mamba 状态管理等。
- **性能优化**：约 6 条，包括 Kimi FP8 MLA cache 插入（小 batch 下 4~6x 提升）、MoE align kernel 协作写入、Arm CPU LM Head 加速、ROCm indexer gather 冷编译优化。
- **新模型/功能支持**：DeepSeek-V4.1-Flash、DeepSeek V4 Vision（ROCm）、MTP 投机解码在流水并行下支持、KDA bf16 checkpoint。
- **CI/构建/平台**：ROCm 超时与镜像、XPU 测试、Rust 前端 vllm-proto 发布 crates.io、tpu-inference 升级。
- **文档与弃用**：API key 认证范围澄清、Triton skill 链接、0.29 弃用项清理。

## 2. 关键变更点与项目方向

- **多硬件后端持续扩展**：ROCm、XPU、TPU、Arm CPU 均有针对性修复与优化，体现 vLLM “跨平台统一服务”的核心定位。
- **新模型快速跟进**：DeepSeek-V4.1-Flash、V4 Vision、Kimi-K3、GLM-OCR、Qwen3-VL 等前沿模型同步支持，强化其作为主流推理引擎的地位。
- **Rust 前端与 gRPC 成熟化**：错误透传、proto 发布、DeepSeek 工具调用对齐，表明 vLLM 正推进生产级服务接口。
- **投机解码与并行策略深化**：MTP + 流水并行、breakable cudagraph 作用域收敛，指向大规模部署场景。

## 3. 对项目的影响与意义

- 大量 Bugfix 集中在 **KV 缓存、注意力元数据、CUDA Graph 捕获**等核心路径，直接提升长上下文与高并发场景的稳定性。
- 性能优化聚焦 **小 batch 与 MoE 场景**，契合实际线上推理的低延迟需求。
- 弃用清理与 httpx 迁移表明项目在**技术债治理与依赖现代化**上稳步推进。
- 一次 revert（Kimi-K3 DCP 流水并行修复）显示对回归风险的谨慎态度。

## 4. 值得关注的技术点

- **FP8 MLA cache 分组插入**：小 batch 下 kernel 级 4~6x 提升，对 Kimi 类长上下文模型意义重大。
- **MTP 投机解码支持流水并行**：扩展了投机解码的适用拓扑。
- **NVDEC GPU 视频解码**：多模态 EPD 架构下降低视频 IO 开销。
- **Prometheus 直方图桶统一模块**：可观测性配置集中化，便于运维调优。
- **YaRN 与 Transformers 对齐**：避免 max_model_len 重复缩放，修复长上下文外推一致性。

## 5. 结合 README 的项目发展视角

README 强调 “Easy, fast, and cheap LLM serving for everyone”。本批提交从三个维度呼应这一目标：**fast**——Kimi/MoE/Arm 多项性能优化；**easy**——Rust 前端错误透传、文档澄清、弃用清理降低使用门槛；**for everyone**——ROCm/XPU/TPU/Arm 多平台覆盖与新模型快速接入。整体看，vLLM 正从“支持多模型”向“多硬件、多并行策略、生产级接口全面成熟”演进，Bugfix 密度高也反映其用户规模扩大后对稳定性的迫切需求。

## 详细提交记录

### [9d88ceb](https://github.com/vllm-project/vllm/commit/9d88ceb02694c6e3df182ec3c87201284f50e2c6)

- **作者**: Wei Zhao
- **时间**: 2026-09-11T23:53:24Z
- **提交信息**: [KDA] Update flashKDA to support bf16 checkpoint state (#56485)

Signed-off-by: wzhao18 <wzhao18.sz@gmail.com>

### [988d9b6](https://github.com/vllm-project/vllm/commit/988d9b6777d077f843cd2164a222ac8535d36ed2)

- **作者**: Alec
- **时间**: 2026-09-11T22:31:55Z
- **提交信息**: [Rust Frontend][gRPC] Surface engine generation errors (#56405)

Signed-off-by: Alec Flowers <aflowers@nvidia.com>
Co-authored-by: Codex <noreply@openai.com>

### [bbaa1b9](https://github.com/vllm-project/vllm/commit/bbaa1b93402dbc3c9741b2d81f8f2ebac74ba339)

- **作者**: Micah Williamson
- **时间**: 2026-09-11T22:11:59Z
- **提交信息**: [ROCm][CI] Extend timeout for `Basic Models (other)` (#56522)

Signed-off-by: Micah Williamson <micah.williamson@amd.com>

### [2d75e58](https://github.com/vllm-project/vllm/commit/2d75e586fcaf88231f7a75f482dc8bfb5ad9da10)

- **作者**: amd-xavierwang
- **时间**: 2026-09-11T21:34:17Z
- **提交信息**: [ROCm][Kernel][DSV4] Remove tl.constexpr to avoid cold-compile churn in indexer gather kernel (#56153)

Signed-off-by: xawang <xawang@amd.com>

### [9dcf6bf](https://github.com/vllm-project/vllm/commit/9dcf6bf344caa7793bae0b45a7896d3f8e03a01a)

- **作者**: Giancarlo Delfin
- **时间**: 2026-09-11T21:33:53Z
- **提交信息**: [BugFix] Fix DP token padding in dflash attention metadata (#56181)

Signed-off-by: Giancarlo Delfin <gdelfin@inferact.ai>

### [c1b69aa](https://github.com/vllm-project/vllm/commit/c1b69aa0d49b88016b5b2156ae61649c2c2df282)

- **作者**: mevince
- **时间**: 2026-09-11T20:12:59Z
- **提交信息**: [Bugfix][KV Connector] Only enforce disk block alignment for O_DIRECT (#55424)

Signed-off-by: Vincent <vincexxchan@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [cc5dd0a](https://github.com/vllm-project/vllm/commit/cc5dd0a857cde0ec224c63fee40276269e32f278)

- **作者**: Nick Hill
- **时间**: 2026-09-11T19:55:34Z
- **提交信息**: [MRV1] Scope breakable cudagraphs to the piecewise path only (#56312)

Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [dffb863](https://github.com/vllm-project/vllm/commit/dffb863c97c16f392207625d6bccf7e12bfe10ee)

- **作者**: Lyle Lai
- **时间**: 2026-09-11T19:32:47Z
- **提交信息**: Upgrade tpu-inference to v0.29.0 (#56388)

Signed-off-by: Lyle Lai <lyle.lai@cienet.com>

### [0c1e89c](https://github.com/vllm-project/vllm/commit/0c1e89ceb92b95e02b5a7aa07781340aacfcf011)

- **作者**: chengchengpei
- **时间**: 2026-09-11T19:07:30Z
- **提交信息**: [Bugfix][Kimi-K3] Fix KDA projection overlap on Hopper (#55426)

Signed-off-by: Chengcheng Pei <5881383+chengchengpei@users.noreply.github.com>
Co-authored-by: Chengcheng Pei <5881383+chengchengpei@users.noreply.github.com>
Co-authored-by: Tyler Michael Smith <tlrmchlsmth@gmail.com>

### [00e5cda](https://github.com/vllm-project/vllm/commit/00e5cda926ffdf35fb96027979e6692d77ea27bd)

- **作者**: Misha Goin
- **时间**: 2026-09-11T19:05:41Z
- **提交信息**: [Agents] Link Triton skill to JIT kernel warmup guide (#56499)

Signed-off-by: mgoin <mgoin64@gmail.com>

### [8a7f98c](https://github.com/vllm-project/vllm/commit/8a7f98c8c3ae409df6130995e364393ead5dbc24)

- **作者**: Misha Goin
- **时间**: 2026-09-11T19:05:22Z
- **提交信息**: [Kernel][MoE] Optimize batched_moe_align_block_size with cooperative writes (#53280)

Signed-off-by: mgoin <mgoin64@gmail.com>

### [dc07f16](https://github.com/vllm-project/vllm/commit/dc07f1638f73814b95776832b85df1cc92850416)

- **作者**: Andy Lo
- **时间**: 2026-09-11T18:02:13Z
- **提交信息**: [Bugfix][MLA] Read sparse model settings from text config (#56160)

Signed-off-by: Andy Lo <andy@mistral.ai>

### [6fe67cb](https://github.com/vllm-project/vllm/commit/6fe67cbbf3e43da89bebf6ab0eeaca4ba6c75663)

- **作者**: Chris Eastwood
- **时间**: 2026-09-11T17:55:21Z
- **提交信息**: [Spec][V2] Support MTP speculative decoding under pipeline parallelism (#46994)

Signed-off-by: Chris Eastwood <chris.eastwood@pwn4g3.dev>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [9a35c08](https://github.com/vllm-project/vllm/commit/9a35c081e80a94828af6f611525102bb70e3c67f)

- **作者**: Sören Dréano
- **时间**: 2026-09-11T16:54:35Z
- **提交信息**: [Docs] Correct API key authentication scope (/inference does NOT bypass the API key) (#56269)

Signed-off-by: Sören Dréano <gailenstorm@gmail.com>

### [9dd969d](https://github.com/vllm-project/vllm/commit/9dd969da096e37256ee37e24f6a4689d860f39ce)

- **作者**: Andreas Karatzas
- **时间**: 2026-09-11T16:17:30Z
- **提交信息**: [Model][ROCm] Enable DeepSeek V4 Vision (#55107)

Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>
Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [127143e](https://github.com/vllm-project/vllm/commit/127143e27f2ba15e3b0ee6f4d73eaeaa60097bc2)

- **作者**: Shanshan Shen
- **时间**: 2026-09-11T16:17:26Z
- **提交信息**: Revert "[Rocm][Kimi-k3] Fix pipeline_parallel support for the kimik3 DCP mode  (#53664)" (#56429)

Signed-off-by: Shanshan Shen <87969357+shen-shanshan@users.noreply.github.com>

### [b873398](https://github.com/vllm-project/vllm/commit/b87339888d29329c42c42573e34cc2beebdcc48b)

- **作者**: Lucain
- **时间**: 2026-09-11T15:29:31Z
- **提交信息**: [httpx migration] Import httpx from huggingface_hub (#56460)

Signed-off-by: Lucain Pouget <lucain@huggingface.co>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [5fe77ae](https://github.com/vllm-project/vllm/commit/5fe77aecfc7687c1f3cc49862022ce34d45d1784)

- **作者**: Wentao Ye
- **时间**: 2026-09-11T15:17:02Z
- **提交信息**: [Deprecation] Deprecate items scheduled for 0.29 (#55353)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [1e1060f](https://github.com/vllm-project/vllm/commit/1e1060f9988fa188fd243c093610889594ba18fd)

- **作者**: Wentao Ye
- **时间**: 2026-09-11T15:16:57Z
- **提交信息**: [Kimi Perf] Group fp8 mla cahche insertion, 4~6x kernel level performance improvement for small batch (#55356)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [22258a2](https://github.com/vllm-project/vllm/commit/22258a26bc090bccf5473cf681bbe9bac41bd035)

- **作者**: Isotr0py
- **时间**: 2026-09-11T14:20:11Z
- **提交信息**: [Multimodal] Use GPU NVDEC for EPD encoder-only instance video media IO (#53675)

Signed-off-by: Isotr0py <Isotr0py@outlook.com>

### [5392fbc](https://github.com/vllm-project/vllm/commit/5392fbca2a45d0224f5653e01885d271518d2dfd)

- **作者**: djramic
- **时间**: 2026-09-11T14:14:16Z
- **提交信息**: [ROCm][Docker] Pin AINIC apt repo to snapshot 1.117.5-a-77 (#56459)

Signed-off-by: Djordje Ramic <djoramic@amd.com>

### [d5a9d0f](https://github.com/vllm-project/vllm/commit/d5a9d0f59bbbbb55ac347e6126d01b1456dbd94f)

- **作者**: Guy Stone
- **时间**: 2026-09-11T14:12:36Z
- **提交信息**: [Metrics] Consolidate Prometheus histogram bucket defaults into a single module (#48866)

Signed-off-by: Guy Stone <guys@spotify.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [c191787](https://github.com/vllm-project/vllm/commit/c191787a6861868069bc4f6ed6f842af541de23a)

- **作者**: Harry Mellor
- **时间**: 2026-09-11T13:01:38Z
- **提交信息**: [Bugfix] Align vLLM YaRN with Transformers and stop re-scaling max_model_len (#56446)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [a5b714e](https://github.com/vllm-project/vllm/commit/a5b714eee4ef09c286368c53df28443b7ac4cf4a)

- **作者**: labAxiaoming
- **时间**: 2026-09-11T12:58:15Z
- **提交信息**: [Bugfix] Fix Qwen3-VL and Cosmos3-Edge text architectures for CPU and pipeline parallelism (#53699)

Signed-off-by: xiaoming <1259730330@qq.com>

### [912dfb3](https://github.com/vllm-project/vllm/commit/912dfb37581b98c0b6eaeca5758d1e1462b7feac)

- **作者**: 김재억
- **时间**: 2026-09-11T12:52:45Z
- **提交信息**: [Bugfix][Scoring] Warn when serving original Qwen3 reranker without chat template (#56017)

Signed-off-by: 김재억 <gadian88@gmail.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [89dbb26](https://github.com/vllm-project/vllm/commit/89dbb2644552d6e473a7e97da0ce8f0aa8e32c9d)

- **作者**: Yuxuan Zhang
- **时间**: 2026-09-11T12:31:10Z
- **提交信息**: [Bugfix] Fix GLM-OCR MTP position masking during CUDA graph capture (#56447)

Signed-off-by: zRzRzRzRzRzRzR <Yuxuan.Zhang2@liverpool.ac.uk>

### [295ac4e](https://github.com/vllm-project/vllm/commit/295ac4e52e8a35772b2a63c028f6510e221a65cf)

- **作者**: waizuichougou
- **时间**: 2026-09-11T12:16:05Z
- **提交信息**: [Bugfix][Multimodal] Parse decoded video frame lists as a single video (#55326)

Signed-off-by: waizuichougou <2082431897@qq.com>
Signed-off-by: waizuichougou <105572299+waizuichougou@users.noreply.github.com>
Co-authored-by: Isotr0py <2037008807@qq.com>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [7ef4d9b](https://github.com/vllm-project/vllm/commit/7ef4d9bfed6311e3b78a40abb4a8bb6a2fc741b0)

- **作者**: Nicole LiHui 🥜
- **时间**: 2026-09-11T12:07:04Z
- **提交信息**: [Bugfix][Responses] Fix browser.find action type (#55305)

Signed-off-by: nicole-lihui <nicole.li@daocloud.io>
Co-authored-by: Chauncey <chaunceyjiang@gmail.com>

### [b4da4d1](https://github.com/vllm-project/vllm/commit/b4da4d17ae0c1fb44f7358585f04fdba7e4e1c91)

- **作者**: Matt
- **时间**: 2026-09-11T11:44:57Z
- **提交信息**: [ROCm][Bugfix] Fix AITER preshuffled FP8 block-scale kernel (#56433)

Signed-off-by: Matthew Wong <Matthew.Wong2@amd.com>

### [a2bc2ff](https://github.com/vllm-project/vllm/commit/a2bc2ffb2c8bf46759c4bbeb88e2f4dc32968762)

- **作者**: shaohuaxi
- **时间**: 2026-09-11T10:26:44Z
- **提交信息**: [Bugfix][Pooling] Restore token limits for offline Jina scoring (#56415)

Signed-off-by: 子华 <huaxi.shx@alibaba-inc.com>
Co-authored-by: Codex <noreply@openai.com>

### [79c137c](https://github.com/vllm-project/vllm/commit/79c137c6ada6bf9384e14feb260e10d91bf58c0b)

- **作者**: JinYan Su
- **时间**: 2026-09-11T10:19:55Z
- **提交信息**: [Bugfix][Rust Frontend][Renderer] Align DeepSeek tool-call arguments with deepseek-recipe (#56260)

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Codex <noreply@openai.com>
Signed-off-by: JinYan Su <751080330@qq.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>

### [8c1d1c2](https://github.com/vllm-project/vllm/commit/8c1d1c2974ee42757ee2e93cc898932edfd9d265)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-09-11T09:35:56Z
- **提交信息**: [Misc] Log FlashInfer allreduce workspace init failure as error (#55127)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [eb7e894](https://github.com/vllm-project/vllm/commit/eb7e89443287cc8ec95b8e6fb993bacbd310f9c3)

- **作者**: Andreas Karatzas
- **时间**: 2026-09-11T09:24:28Z
- **提交信息**: [ROCm][CI] Add HY-V4 generation coverage (#55667)

Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>

### [e77daef](https://github.com/vllm-project/vllm/commit/e77daef89e18e08321ae7b8b24827eedd5fe8673)

- **作者**: Yongye Zhu
- **时间**: 2026-09-11T09:11:19Z
- **提交信息**: [Model] Support DeepSeek-V4.1-Flash (#56214)

Signed-off-by: Yongye Zhu <zyy1102000@gmail.com>
Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>
Signed-off-by: andyluo7 <andy.luo@amd.com>
Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: Jee Jee Li <jeejeelee@inferact.ai>
Co-authored-by: andyluo7 <andy.luo@amd.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [e6821ce](https://github.com/vllm-project/vllm/commit/e6821ceac91f4d61c7a8603f6de21d9c8935effb)

- **作者**: Tony Lin
- **时间**: 2026-09-11T08:58:27Z
- **提交信息**: [XPU][CI] Add decord to test requirements (#56355)

Signed-off-by: Tony Lin <tony.lin@intel.com>

### [1cf6555](https://github.com/vllm-project/vllm/commit/1cf6555214446cfb98c42ff5d07baab784925c1b)

- **作者**: Kevin H. Luu
- **时间**: 2026-09-11T08:57:47Z
- **提交信息**: [Bugfix] Pin EPLB and MLA host-to-device transfer buffers (#56138)

Signed-off-by: khluu <khluu000@gmail.com>
Signed-off-by: Kevin H. Luu <khluu000@gmail.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [d0dfe58](https://github.com/vllm-project/vllm/commit/d0dfe587d5b20609af4de8e8d968713116b80eb6)

- **作者**: Andreas Karatzas
- **时间**: 2026-09-11T08:56:05Z
- **提交信息**: [Bugfix] Fall back to full decode graphs for noncompiled models (#55095)

Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>
Signed-off-by: Lucas Wilkinson <lwilkins@redhat.com>
Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: Lucas Wilkinson <lwilkins@redhat.com>

### [9dcab80](https://github.com/vllm-project/vllm/commit/9dcab802154d89d25de22332c458168673afab89)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-09-11T08:53:04Z
- **提交信息**: [Bugfix][Bench] Fix bench mm-processor crash in shared request sampling (#56300)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [69db1c2](https://github.com/vllm-project/vllm/commit/69db1c26b4fe4474ab4c9df1c9701efac8bedde1)

- **作者**: JulienDarve
- **时间**: 2026-09-11T08:28:52Z
- **提交信息**: [CI/Build][Rust Frontend] Publish vllm-proto on crates.io (#56365)

Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Signed-off-by: Julien Darve <jdarve@NVIDIA.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>

### [e3f755b](https://github.com/vllm-project/vllm/commit/e3f755b732316df4db8437dcb973b9fa28bfd656)

- **作者**: Fadi Arafeh
- **时间**: 2026-09-11T08:21:14Z
- **提交信息**: [CPU] Speedup LM Head on Arm CPUs (#55352)

Signed-off-by: Fadi Arafeh <fadi.arafeh@arm.com>
Co-authored-by: Li, Jiang <jiang1.li@intel.com>

### [6376c60](https://github.com/vllm-project/vllm/commit/6376c601ede7c8ff25d2bd89dbaa46297a45db10)

- **作者**: pmanczak
- **时间**: 2026-09-11T07:59:13Z
- **提交信息**: [XPU][Tests] Enable test_per_token_group_quant_int8 on XPU (#55681)

Signed-off-by: pmanczak <pawel.manczak@intel.com>

### [fadfe1c](https://github.com/vllm-project/vllm/commit/fadfe1c7d4df4c29b3dbc159ed790238a885b084)

- **作者**: lucamotz
- **时间**: 2026-09-11T07:50:47Z
- **提交信息**: [Bugfix][Core] Retire Mamba states across null gaps (#55450)

Signed-off-by: Luca Motz <luca.motz@icloud.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>

### [a9271c7](https://github.com/vllm-project/vllm/commit/a9271c750f6eb07ad7e4c52b9dffa65ff2ee336a)

- **作者**: Micah Williamson
- **时间**: 2026-09-11T07:30:39Z
- **提交信息**: [ROCm][CI] Accept `base-v2-preview` images during content hash lookup for ROCm base images (#56356)

Signed-off-by: Micah Williamson <micah.williamson@amd.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-09-12
**监控日期**: 2026-09-11
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 6767
- **最后更新**: 2026-09-11T22:59:54Z

## 提交统计

- **昨日提交总数**: 14
- **提交者数量**: 12
- **主要提交者**: Guangjian Dong, GXIN, wtz2333

## AI分析总结

# vllm-omni 昨日提交分析（14 条）

## 1. 主要更新类型分布

- **模型新增/扩展（4 条）**：Tencent AuK 语音生成与编辑、LingBot World Ulysses 序列并行、HunyuanImage-3.0 示例迁移、MiniCPM-o 4.5 修复。
- **Bug 修复（5 条）**：CFGP 与蒸馏 Cosmos3 冲突报错、OpenAI realtime API 遗留事件名、FLUX.2 Klein 多图编辑元数据、MiniCPM-o embed_multimodal、ERNIE-Image AdaLN 广播。
- **性能优化（4 条）**：MiniMax-H3 Q/K RMSNorm-RoPE 单次启动、GLM-Image 消除标量同步、HSDP 启动优化与 LoRA delta 加速、ERNIE-Image 延迟广播。
- **基础设施/CI（2 条）**：XPU 与 ROCm 镜像对齐 vLLM v0.29.0。
- **可观测性（1 条）**：TTS Speech API 流式指标。

## 2. 关键变更点与项目方向

项目定位是"全模态模型服务"，昨日提交高度契合这一方向：**语音（AuK、TTS 指标）、图像（FLUX.2、ERNIE-Image、GLM-Image、HunyuanImage）、视频/世界模型（LingBot World）、多模态 LLM（MiniCPM-o）** 全面覆盖，说明社区正快速扩充 omni-modality 模型矩阵。同时 XPU/ROCm 镜像对齐 vLLM 0.29.0，体现与上游 vLLM 主线的同步策略，保障多硬件后端一致性。

## 3. 对项目的影响与潜在意义

- **模型生态扩张**：AuK 与 LingBot World 的加入填补了语音编辑与世界模型序列并行的空白，增强"omni"叙事完整性。
- **稳定性提升**：多个 Bugfix 集中在边界场景（蒸馏模型、多图元数据、遗留 API 命名），减少用户踩坑，提升生产可用性。
- **性能红利**：内核融合与去同步化优化直接降低扩散/生成模型的延迟，符合"fast and cheap"的 README 承诺。
- **硬件覆盖**：XPU、ROCm 同步上游，巩固多平台部署能力。

## 4. 值得关注的技术点

- **Kernel 融合**：MiniMax-H3 将 Q/K RMSNorm-RoPE 合并为单次 launch，是典型的算子级优化范式。
- **消除标量同步**：GLM-Image 与 ERNIE-Image 的改动针对 GPU-CPU 同步瓶颈，对扩散推理吞吐影响显著。
- **HSDP + LoRA 优化**：Rank-0 共享权重加载与加速 LoRA delta 计算，是分布式训练/微调场景的关键提速。
- **显式错误提示**：CFGP 与蒸馏 Cosmos3 冲突时主动报错，体现"fail fast"的工程哲学。
- **流式指标**：TTS Speech API 指标为可观测性打基础，利于线上监控与调优。

## 5. 结合 README 的项目发展意义

README 强调"Easy, fast, and cheap omni-modality model serving for everyone"。昨日提交从三个维度推进该目标：**广度**（新增语音、世界模型、图像模型）、**速度**（内核融合、去同步、HSDP 优化）、**易用性**（Bugfix、显式报错、示例迁移、流式指标）。整体看，项目正处于"模型矩阵快速扩张 + 性能持续打磨 + 多硬件对齐"的良性发展阶段，社区贡献活跃（NVIDIA、Intel、AMD、字节、腾讯等），生态健康度良好。

## 详细提交记录

### [13b85c5](https://github.com/vllm-project/vllm-omni/commit/13b85c562248831a7c5f527cc08531dc72c0fbad)

- **作者**: MaciejBalaNV
- **时间**: 2026-09-11T22:59:49Z
- **提交信息**: [Bugfix] Add explicit error when using CFGP with distilled Cosmos3 models (#7427)

Signed-off-by: Maciej Bala <mbala@nvidia.com>

### [6fcab74](https://github.com/vllm-project/vllm-omni/commit/6fcab74aa9b048ab16b2a3815484649ec1ea32f6)

- **作者**: Joshna-Medisetty
- **时间**: 2026-09-11T20:54:28Z
- **提交信息**: [XPU][Docker] Align XPU image and CI with vLLM v0.29.0 (#7441)

Signed-off-by: Joshna-Medisetty <joshna.medisetty@intel.com>

### [c111f3a](https://github.com/vllm-project/vllm-omni/commit/c111f3a2d6048848cd239b9cbce37cd55001d57c)

- **作者**: Yueqian Lin
- **时间**: 2026-09-11T20:09:58Z
- **提交信息**: [Model] Add Tencent AuK speech generation and editing (encoder + diffusion pipeline) (#7385)

Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: Sy03 <1370724210@qq.com>

### [d349338](https://github.com/vllm-project/vllm-omni/commit/d3493384cfc6c4b9ba1fc4e534e91fe588ecb4f1)

- **作者**: Nick Cao
- **时间**: 2026-09-11T14:28:55Z
- **提交信息**: [BugFix] Fix leftovers of the legacy OpenAI realtime API event names (#7426)

Signed-off-by: Nick Cao <ncao@redhat.com>
Co-authored-by: Codex <noreply@openai.com>

### [78e1a0a](https://github.com/vllm-project/vllm-omni/commit/78e1a0ae5ce6bec260043a085df2d35d42ce1d03)

- **作者**: Qi Jia
- **时间**: 2026-09-11T14:18:07Z
- **提交信息**: [Bugfix][Model] Fix FLUX.2 Klein multi-image edit metadata (#7430)

Signed-off-by: QI JIA <qi.jia@shengshu.ai>
Co-authored-by: QI JIA <qi.jia@shengshu.ai>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [33fff21](https://github.com/vllm-project/vllm-omni/commit/33fff2155e0bf9bc8688f7ffb92ef508efdf6954)

- **作者**: GXIN
- **时间**: 2026-09-11T13:22:15Z
- **提交信息**: [Feature][TTS] Add Speech API streaming metrics (#6853)

Signed-off-by: XIN GAO <1037396230@qq.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [02aaa34](https://github.com/vllm-project/vllm-omni/commit/02aaa34059478280eb3e6a5ee05a9484f0fa23c4)

- **作者**: wtz2333
- **时间**: 2026-09-11T10:37:12Z
- **提交信息**: [Model] Add LingBot World Ulysses sequence parallelism (#6841)

Signed-off-by: wtz2333 <2955110911@qq.com>
Co-authored-by: Zhou Taichang <tzhouam@connect.ust.hk>

### [de9a133](https://github.com/vllm-project/vllm-omni/commit/de9a133d48cbcb35c7165c772524be20e0fd1bdd)

- **作者**: Guangjian Dong
- **时间**: 2026-09-11T10:05:12Z
- **提交信息**: [Bugfix] Add embed_multimodal to MiniCPM-o 4.5 omni LLM class (#7384)

Signed-off-by: Guangjian <hiro20833@gmail.com>

### [dff8f8f](https://github.com/vllm-project/vllm-omni/commit/dff8f8f4cfe9ba6e6eaeeac455f8aee66f95c4ae)

- **作者**: andyluo7
- **时间**: 2026-09-11T09:41:45Z
- **提交信息**: [CI][ROCm] Align AMD image with vLLM 0.29 (#7395)

Signed-off-by: andyluo7 <andy.luo@amd.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [43b8de9](https://github.com/vllm-project/vllm-omni/commit/43b8de9b0ecdeb78ec3585222db02164a087103a)

- **作者**: hyw
- **时间**: 2026-09-11T09:18:12Z
- **提交信息**: [Kernel][MiniMax-H3] Run Q/K RMSNorm-RoPE in one launch (#7167)

Signed-off-by: hyw <yuweih205@gmail.com>

### [f62d4ad](https://github.com/vllm-project/vllm-omni/commit/f62d4ad4a794bd0706340d8dcc9d92e67672af1c)

- **作者**: hyw
- **时间**: 2026-09-11T09:15:32Z
- **提交信息**: [Model][ERNIE-Image] Delay AdaLN modulation broadcast (#7171)

Signed-off-by: hyw <yuweih205@gmail.com>

### [3f7c217](https://github.com/vllm-project/vllm-omni/commit/3f7c2174574f14a9767c022b01834fa2c52420df)

- **作者**: hyw
- **时间**: 2026-09-11T09:09:26Z
- **提交信息**: [Model] Avoid scalar synchronizations in GLM-Image preparation (#7172)

Signed-off-by: hyw <yuweih205@gmail.com>

### [a7ab91f](https://github.com/vllm-project/vllm-omni/commit/a7ab91fb85b1bb513d34f0a19c3289c55a38b013)

- **作者**: SuyanLi
- **时间**: 2026-09-11T08:47:25Z
- **提交信息**: [Example] Migrate HunyuanImage-3.0 to model_extras + shared task examples (#5559)

Signed-off-by: suyanli220 <suyanli220@gmail.com>
Signed-off-by: suyan.li <suyan.li@bytedance.com>
Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>
Co-authored-by: suyan.li <suyan.li@bytedance.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [96360cc](https://github.com/vllm-project/vllm-omni/commit/96360ccb00d0c4c415eaec4369c827e7396e910a)

- **作者**: Samit
- **时间**: 2026-09-11T08:28:42Z
- **提交信息**: [Perf][Diffusion] Optimize HSDP startup via Rank-0 shared weight loading and accelerated LoRA delta computation (#7005)

Signed-off-by: samithuang <285365963@qq.com>

---
