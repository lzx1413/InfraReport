# GitHub Stars 合并报告 - 2026-11-16

**合并日期**: 2026-11-17
**监控日期**: 2026-11-16
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


**报告日期**: 2026-11-17
**监控日期**: 2026-11-16
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2295
- **最后更新**: 2026-11-16T17:43:30Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 5
- **主要提交者**: Yusen Gao, NancyFyong, BeatSeat

## AI分析总结

<tool_call><function=bash><parameter=command>gh api repos/ByteDance-Seed/VeOmni/commits/e42d6f8 --jq '{message: .commit.message, files: [.files[] | {filename: .filename, additions: .additions, deletions: .deletions}]}' 2>&1 | head -60</parameter><parameter=description>查看提交e42d6f8详情</parameter></function></tool_call><tool_call><function=bash><parameter=command>gh api repos/ByteDance-Seed/VeOmni/commits/5da1a47 --jq '{message: .commit.message, files: [.files[] | {filename: .filename, additions: .additions, deletions: .deletions}]}' 2>&1 | head -60</parameter><parameter=description>查看提交5da1a47详情</parameter></function></tool_call>

## 详细提交记录

### [e42d6f8](https://github.com/ByteDance-Seed/VeOmni/commit/e42d6f893109874c7dcb65f775cee64787080036)

- **作者**: Coach257
- **时间**: 2026-11-16T12:33:46Z
- **提交信息**: [model, omni] refactor: skip the embedding tie when a module has no output head (#1471)

Co-authored-by: Cursor <cursoragent@cursor.com>

### [baaa62c](https://github.com/ByteDance-Seed/VeOmni/commit/baaa62c6f3076d0d96ade137d09f3271fe5d66a5)

- **作者**: NancyFyong
- **时间**: 2026-11-16T10:16:49Z
- **提交信息**: [model] feat: add MiniMax-H3-Image inference support (#1444)

### [ce0b39b](https://github.com/ByteDance-Seed/VeOmni/commit/ce0b39ba01cbfd543cfb82d19213d2a38638b4e9)

- **作者**: zpl1n
- **时间**: 2026-11-16T09:44:03Z
- **提交信息**: [docker, ci] feat: build CANN 9.2.1 A2 and A3 images (#1427)

### [f1fea3a](https://github.com/ByteDance-Seed/VeOmni/commit/f1fea3ace53484e7a4c74b9360dc57b5605f4260)

- **作者**: Yusen Gao
- **时间**: 2026-11-16T09:29:58Z
- **提交信息**: [ci] test: run the optional torchao tests in the GPU unit job (#1468)

### [38a2d0b](https://github.com/ByteDance-Seed/VeOmni/commit/38a2d0ba1c82b5dc80b6be493e518cefe2724e38)

- **作者**: Coach257
- **时间**: 2026-11-16T08:54:40Z
- **提交信息**: [omni, model, config, docs] feat: support Qwen3-MoE in SeedOmni (#1451)

### [5da1a47](https://github.com/ByteDance-Seed/VeOmni/commit/5da1a4795aa39d01fe6a8bd028d7a571a16a7677)

- **作者**: BeatSeat
- **时间**: 2026-11-16T08:36:59Z
- **提交信息**: [model, ops, docs] feat: add torchao_nvfp4 QAT op rows for linear and swiglu_mlp (#1426)

Co-authored-by: Yusen Gao <amenomorikou@gmail.com>

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-11-17
**监控日期**: 2026-11-16
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 3010
- **最后更新**: 2026-11-16T17:03:05Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 3
- **主要提交者**: Watebear, Bilang ZHANG, Yang Yong (雍洋)

## AI分析总结

# LightX2V 昨日提交分析

## 1. 主要更新类型

本次更新以**重构**、**功能新增**和**性能优化**为主，涵盖 4 个提交，未涉及文档更新或 Bug 修复。其中重构占比最高，体现了项目进入深度优化阶段。

## 2. 关键变更点及与项目方向的关系

- **LightX2V 全面重构（#1673）**：作为核心提交，对推理框架进行整体结构调整，为后续功能扩展奠定架构基础。
- **FSDP 分片加载机制（#1711）**：新增通用的 rank-local sharded 加载能力，针对分布式训练/推理中的模型权重加载效率进行改进。
- **H3 因果流式推理优化（#1721）**：对 H3 模型的因果流式推理做性能优化，直接服务于项目"轻量视频生成推理"的核心目标。
- **完整 Ulysses 序列并行（#1720）**：补全 Ulysses SP（序列并行）支持，增强长序列视频生成场景下的并行计算能力。

这些变更与项目"Light Video Generation"的定位高度一致——通过架构重构提升可维护性，通过并行与分片技术降低显存与时间开销。

## 3. 对项目的影响和潜在意义

- **架构层面**：重构 + FSDP 分片加载 + Ulysses SP 三者配合，说明项目正从"单机可跑"迈向"大规模分布式高效推理"的阶段。
- **性能层面**：H3 流式推理优化直接改善用户体验（更低延迟），符合"Light"（轻量）的品牌承诺。
- **生态层面**：Ulysses SP 和 FSDP 都是 PyTorch 生态的主流并行方案，降低了用户接入门槛，增强了社区兼容性。

## 4. 值得关注的技术点

- **Ulysses 序列并行的"完整"（full）实现**：暗示此前可能只有部分支持，完整版意味着对 head 划分、注意力计算的全链路适配，是长视频生成的关键瓶颈突破。
- **FSDP rank-local sharded loading**：rank-local 设计可避免聚合加载时的 IO 瓶颈，对超大模型推理尤为关键。
- **H3 因果流式推理**："因果流式"意味着支持逐帧生成，是实时/低延迟视频生成的核心路径。
- **大规模 PR 编号（#1720、#1721、#1711）**：反映出社区活跃度高，项目处于快速迭代期。

## 5. 结合项目背景对发展的影响

README 明确项目定位是**轻量视频生成推理框架**。本批提交通过一次大规模重构统一架构，再以三项具体优化（分片加载、流式推理、序列并行）分别解决**内存、延迟、序列长度**三大视频推理核心难题。这使 LightX2V 从功能性框架向生产级推理引擎演进，同时文档/许可证体系已就绪，为后续稳定版本发布和社区推广提供了坚实基础。整体而言，这批提交显著强化了项目在高效视频生成推理领域的技术壁垒与实用价值。

## 详细提交记录

### [395e2ac](https://github.com/ModelTC/LightX2V/commit/395e2ac49f215a5962a6ba7c42a4d9e6a9d109c0)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-11-16T15:02:33Z
- **提交信息**: LightX2V Refactor (#1673)

### [2ebdc54](https://github.com/ModelTC/LightX2V/commit/2ebdc54f7b4d8316186ff7c2be6b2ed7989a09b3)

- **作者**: Watebear
- **时间**: 2026-11-16T08:06:14Z
- **提交信息**: feat(fsdp): add generic rank-local sharded loading (#1711)

### [6a49844](https://github.com/ModelTC/LightX2V/commit/6a4984448dc58fb3c515850c131e02672bb6adae)

- **作者**: Bilang ZHANG
- **时间**: 2026-11-16T07:26:34Z
- **提交信息**: perf: optimize H3 causal streaming inference (#1721)

### [d9d7faf](https://github.com/ModelTC/LightX2V/commit/d9d7faf94caf3d6c64d8cb259abceb4fa4e636ed)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-11-16T06:10:40Z
- **提交信息**: Add full ulysses sp (#1720)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-11-17
**监控日期**: 2026-11-16
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2335
- **最后更新**: 2026-11-13T06:03:52Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-11-17
**监控日期**: 2026-11-16
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6942
- **最后更新**: 2026-11-17T02:47:18Z

## 提交统计

- **昨日提交总数**: 36
- **提交者数量**: 25
- **主要提交者**: Lee Nau, Edwin Mascarenhas, garry569

## AI分析总结

# FlashInfer 昨日提交总结

## 一、主要更新

昨日提交以 **Bug 修复**（主导）与**性能优化**为主线，辅以功能新增、测试与生态同步：

- **数值与并发正确性修复**：涵盖 NaN 泄漏、数据竞争、越界与对齐问题。
- **性能调优**：GEMM 自动调优、量化路由、MoE 路由与融合、NVFP4/MLA 解码、SM120 FP8 稀疏 prefill 融合。
- **功能新增**：DeepSeek-V4.1 解码索引与 NVFP4 KV 缓存、QSA 稀疏分页注意力 API 转正、batch-invariant FP8 MoE 后端、MNNVL 多节点量化融合、SM100 门控激活融合。
- **测试与文档**：cuDNN 回归矩阵系统性补齐、测试套件提速 3–20 倍、上游 TRT-LLM 补丁同步。

## 二、关键变更

**正确性加固**：small-bh prefill 隔离序列末尾非有限值防止 NaN 泄漏；SegmentGEMM 保持整数段长度精度；Triton GEMM 尾声保持 FP32 直至写回；split-KV 归约将 mbarrier acquire 提升至 `.cluster` scope 修正跨 CTA 竞争；GEMM 内核修复 TMEM 释放时序、tcgen05 fence 缺失与 PDL bias 读取未等待等问题；同步上游 SFC store 越界、amax 极值 NaN、Lamport clear 尺寸错误等补丁；块级量化启动器零尺寸输入提前返回并包裹 `TLLM_CUDA_CHECK`，消除被后续调用"顶替"报告的隐蔽错误。

**性能调优**：cute-dsl MXFP8 GEMM 自动调优采样增至 16 次（约 5% 加速）；量化路由按总行数判断（1.5~2 倍加速）；MoE routing/finalize 内核重写与 SwiGLU 指令精简；SM12x MoE 引入 token-major gather 与 SplitK2；NVFP4 解码与 SM90 MLA 滑窗解码深度调优；SM100 masked grouped GEMM 融合门控激活；SM120 上将 Q RoPE、稀疏 MLA、逆输出 RoPE 与 FP8 输出量化合并为单一内核，借助 CuTe 编译时特化分离 K/V 与 QK/softmax/PV 角色，减少启动次数与中间读写。

**生态与 API**：DeepSeek-V4.1 DSA 索引与 NVFP4 块稀疏注意力；QSA 稀疏注意力以 SASS 级验证零行为变化后转正；batch-invariant MoE 支持确定性推理；NVLink 双边通信补入确定性空 rank 场景测试，填补仅靠 CPU mock 的缺口；CTA barrier 修复有意限定 SM103，体现架构感知权衡。

## 三、项目影响

多为静默错误类型（NaN 泄漏、段错位、数据竞争），不修复会导致难以察觉的推理输出错误，合入后显著提升内核可靠性。性能调优覆盖 H100 到 Blackwell/Rubin（SM90/100/107/12x）全栈硬件，巩固 MoE、MLA 与新量化格式的吞吐优势，直接惠及 vLLM/SGLang 等下游框架。API 转正、上游同步与 CI 提速降低维护成本，配合多 cuDNN 版本交叉验证与 CUDA 图回放校验，标志项目进入"可靠性与性能并重"的成熟运营阶段，为更大规模采用奠定信任基础。

## 四、技术关注点

1. **PTX memory scope 配对**：`st.async` 的 `.cluster` release 与 `.cta` acquire 不构成同步，是易踩陷阱。
2. **mbarrier phase 语义**：phaseParity 仅看当前或前一 phase，"等待 phase 1"可能立即返回。
3. **FP32 累加器降精度时机**：附带 16 例覆盖溢出/抵消/下溢的回归测试。
4. **测试范式**：输出投毒回放、FP64 边界行校验、`late_store` 延迟注入触发竞态、空 rank 确定性路由可复现失败、SASS 逐条匹配。
5. **文档化隐式契约**：SM100 FP8 scale 截断为 2^floor(log2(x)) 仅文档说明，体现性能与安全的权衡。
6. **自动调优保守设计**：autotuner 缓存键版本化与 SplitK 自动策略守卫。

这些工作共同支撑 FlashInfer 向"更可靠、更快、API 更稳定"的生产级推理内核库演进。

## 详细提交记录

### [45e0842](https://github.com/flashinfer-ai/flashinfer/commit/45e0842d4a48b5849422e2f55b04af5e8b7a7163)

- **作者**: Ka-Hyun Nam
- **时间**: 2026-11-16T23:40:26Z
- **提交信息**: fix(kda): isolate non-finite V past the sequence end in small-bh prefill (#9286)

## Summary

`recurrent_kda` prefill with `backend="small-bh"` (also chosen by
`backend="auto"` for BF16 state when `2 * num_sequences * heads <= SM
count`) let a non-finite V value in one packed sequence reach the output
and final state of the sequence before it.

Kernel 2 loads V by TMA at the packed sequence offset, so the rows of
the last tile past a sequence's end hold the next sequence's tokens.
They fed `P = Mkk @ (V - dV)` unmasked, and `Mkk * NaN` is NaN even
where the `Mkk` entry is zero. This is the small-bh counterpart of the
leak #8599 fixed in the chain prefill kernel; it was split out of that
review (#8443 is the report).

The fix zeroes the `V - dV` rows at or past the sequence end in the
consumer warpgroup when `cu_seqlens` is given, using the MMA's own
coordinate partition so it needs no shared-memory write, barrier or
extra pipeline stage. The fixed-length path is unchanged.

## Test

New `tests/kda/test_kda_small_bh_padding.py` packs two to four
sequences, poisons the last sequence's V with NaN or Inf, and compares
every earlier sequence's output and final state with a run on the clean
prefix. Cases: `(37, 40)`, `(3, 5, 7, 9)`, `(100, 17, 130)` and an
aligned `(64, 64)` control.

| Arch | Base | This PR |
|---|---|---|
| B100 (SM100) | 6 failed, 2 passed | 8 passed |
| B300 (SM103) | 6 failed (the aligned control passes) | no failures |

On B100 the whole of `tests/kda/test_recurrent_kda_prefill.py`,
`tests/kda/test_recurrent_kda.py` and the new file passes (412 passed, 6
skipped).

## Performance

B200, CUPTI timing with a cold L2, `backend="small-bh"`, 12 heads,
D=128, BF16 state, median of 50 iterations, three alternating base/head
rounds:

| B x L | base (ms) | this PR (ms) | delta |
|---|---|---|---|
| 1 x 1000 | 0.0382 | 0.0382 | +0.0% |
| 1 x 4096 | 0.1182 | 0.1186 | +0.3% |
| 4 x 1000 | 0.0502 | 0.0503 | +0.2% |
| 4 x 4000 | 0.1616 | 0.1615 | -0.1% |
| 4 x 4096 | 0.1636 | 0.1635 | -0.1% |
| 4 x 16000 | 0.5956 | 0.5979 | +0.4% |
| 4 x 16384 | 0.6099 | 0.6119 | +0.3% |

Related: #8443, #8599


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved handling of variable-length sequences in the small-batch
processing path. Unused entries in a partially filled sequence tile no
longer interfere with results for earlier sequences.
* Added coverage for cases where unused entries contain invalid values,
including NaNs and infinities, and verified that earlier outputs and
final states remain consistent.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Sonnet 5.5 <noreply@anthropic.com>

### [05de7b2](https://github.com/flashinfer-ai/flashinfer/commit/05de7b2484909afa0fd2825774bacb5561f21622)

- **作者**: nulllt2
- **时间**: 2026-11-16T23:09:25Z
- **提交信息**: fix(gemm): keep SegmentGEMM lengths as integers (#9097)

<!-- .github/pull_request_template.md -->

## 📌 Description

SegmentGEMM uses segment lengths to decide which rows share a weight
matrix. Copying these lengths with `.to(x)` also converts them to
FP16/BF16, which can change values such as 259 to 260 and put rows in
the wrong segment.

Move the lengths to `x.device` without changing their integer dtype. Add
tests for rounding boundaries and explicit `seg_indptr` for both
backends.

## 🔍 Related Issues

Fixes #9096.

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
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: Targeted metadata and grouped-GEMM tests cover this change.

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/cpu/gemm/test_segment_gemm_lengths.py
tests/gemm/test_group_gemm.py`

Validation:

```sh
CUDA_VISIBLE_DEVICES=0 CUDA_HOME=/usr/local/cuda PATH=/usr/local/cuda/bin:$PATH .venv/bin/python -m pytest tests/cpu/gemm/test_segment_gemm_lengths.py -v
```

- Standard pytest: **20 passed in 12.07s**, using the real package
imports, API decorators, and root conftest. The tests check actual
wrapper metadata and intercept backend argument preparation before a
GEMM launch.
- Earlier metadata baseline: **6 failed / 14 passed**; fixed: **20
passed**.
- Earlier CUDA metadata probe: **12 passed**, covering CPU/CUDA length
tensors and both backend selectors on RTX 4090.
- Actual SM80 CUTLASS execution: **12 passed in 93.52s**, through
`SegmentGEMMWrapper.run` on RTX 4090 (SM89), PyTorch 2.12.0+cu130.
Covered FP16 `[2049, 1]`, BF16 `[257, 1]` / `[259, 1]`, CPU/CUDA integer
length tensors and derived/explicit segment pointers. Every output row
matched the exact reference; SM90 execution remains untested locally.
- `pre-commit run --all-files`: **passed**, including mypy, Ruff,
formatting and the scope-validator self-test. Hooks are installed; `git
diff --check` passed, and the sweep left no source changes.
- The all-tests checkbox remains unchecked because the full
supported-hardware matrix has not run. Public CI reports `CI skipped —
pending authorization`; this account has pull access only, so public CI
is not represented as passing.

<details>
<summary>Reproduce the additional CUDA output check</summary>

Save the following as `/tmp/flashinfer_segment_gemm_cuda_probe.py` in an
environment with an editable FlashInfer install and the required
submodules:

```python
import pytest
import torch
from flashinfer.gemm import SegmentGEMMWrapper

@pytest.mark.parametrize('dtype,lengths', [(torch.float16, [2049, 1]), (torch.bfloat16, [257, 1]), (torch.bfloat16, [259, 1])])
@pytest.mark.parametrize('lengths_device', ['cpu', 'cuda'])
@pytest.mark.parametrize('explicit_indptr', [False, True])
def test_exact_segment_boundaries(dtype, lengths, lengths_device, explicit_indptr):
    x = torch.ones((sum(lengths), 128), dtype=dtype, device='cuda')
    weights = torch.stack([torch.eye(128), 2 * torch.eye(128)]).to(device='cuda', dtype=dtype)
    seg_lens = torch.tensor(lengths, dtype=torch.int64, device=lengths_device)
    indptr = torch.tensor([0, lengths[0], sum(lengths)], dtype=torch.int64, device='cuda')
    wrapper = SegmentGEMMWrapper(torch.empty(32 * 1024 * 1024, dtype=torch.int8, device='cuda'), backend='sm80')
    out = wrapper.run(x, weights, len(lengths), weight_column_major=False, seg_lens=seg_lens, seg_indptr=indptr if explicit_indptr else None)
    expected = torch.cat([torch.ones_like(x[:lengths[0]]), 2 * torch.ones_like(x[lengths[0]:])])
    torch.testing.assert_close(out, expected, rtol=0, atol=0)
```

```sh
CUDA_VISIBLE_DEVICES=0 CUDA_HOME=/usr/local/cuda PATH=$PWD/.venv/bin:/usr/local/cuda/bin:$PATH FLASHINFER_CUDA_ARCH_LIST=8.9 MAX_JOBS=2 .venv/bin/python -m pytest /tmp/flashinfer_segment_gemm_cuda_probe.py -v -x -o cache_dir=/tmp/nulllt2-flashinfer-pytest-cache
```

</details>

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

The checked-in CPU regressions check the exact segment pointers passed
to both backends and stop before a GEMM launch. The additional local
CUDA probe above executes the real SM80 CUTLASS backend and verifies
every output row. The change preserves integer lengths on the
destination device and does not change the public API signature.

AI assistance: OpenAI Codex assisted with implementation, self-review,
environment setup, and local test execution.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Fixed segment metadata preparation to use the input’s device, helping
ensure segment boundaries are computed correctly for FP16 and BF16
inputs.

* **Tests**
* Added CPU-only regression coverage for implicit and explicit segment
pointers, checking expected boundaries for rounding-sensitive segment
lengths across supported GPU architectures. The tests also verify
pointer device and batch size without launching a GPU kernel.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: litian <18374328@buaa.edu.cn>

### [75662c9](https://github.com/flashinfer-ai/flashinfer/commit/75662c98c7e870b99ef6c416f816229d5308cf7b)

- **作者**: Gabriel Wu
- **时间**: 2026-11-16T23:03:56Z
- **提交信息**: feat(sm120_dsa_indexer): DeepSeek-V4.1 decode in the paged form: strided page caches and candidate blocks (#8740)

<!-- .github/pull_request_template.md -->

## 📌 Description

This PR makes the paged (decode) form of the SM120 DSA indexer (#7085)
serve DeepSeek-V4.1's indexer layers in vLLM:

1. **Strided page caches (fix):** vLLM's DeepSeek-V4.1 indexer cache is
a view at an offset inside per-block buffers. The paged form raised on
it at the first decode.
2. **Candidate source rows** (`candidate_out`): layer 20 publishes each
row's top candidate blocks.
3. **Candidate consumer rows** (`candidate_blocks`): layers 24-36 rank
each row only within those blocks.

### Strided page caches

The paged form takes a cache whose page `p` starts at byte `p *
k.stride(0) * k.element_size()` and holds `k.shape[1]` key rows followed
by their scales. Its wrapper viewed that cache as `[num_pages,
page_stride]` bytes, which also requires a full page stride of storage
after the last page's start. When the page stride is larger than a page,
the storage can end with the last page's bytes. This happens with padded
pages, or with pages inside larger blocks. Then `torch.as_strided`
raises, for example:

```
RuntimeError: setStorage: sizes [11846, 212256], strides [212256, 1], storage offset 101376, and itemsize 1 requiring a storage size of 2514485952 are out of bounds for storage of size 2514384576
```

The wrapper now:

- **Views only the bytes the kernel reads:** each page's `page_rows *
(row + 4)` bytes, at the page stride. The kernel is unchanged.
- **Rejects pages whose bytes are not contiguous.** The kernel receives
only the page stride, so such a cache was previously read wrongly
without an error.

### Candidate blocks

DeepSeek-V4.1 uses two-level index selection on its uncompressed indexer
layers:

- **Source layer (layer 20):** ranks its own top-k and also publishes,
for each decode row, the 2048 blocks of 8 keys with the highest block
scores. A block's score is the largest score among its visible keys, and
the row's newest block always ranks first.
- **Consumer layers (24-36):** rank each decode row only within the
blocks published for it. `top_k` is 512.

On SM120, vLLM serves both from DeepGEMM's `fp8_paged_mqa_logits`, which
scores the row's whole context into a `[rows, max_model_len]` fp32
matrix:

- **Source:** a block-score kernel, `torch.topk` or DeepSelect over the
block scores, and `persistent_topk` for the row's own top-k.
- **Consumer:** a Triton kernel masks the scores outside the candidates,
then `persistent_topk` runs.

The consumer's work grows with the context, although no consumer row can
select from more than 16K keys.

This PR covers both roles in the paged form of
`dsa_indexer_det_topk(..., backend="sm120")` (#7085). There are three
new keyword arguments:

- **`candidate_out`** (source rows): int32 `[B * next_n, C]` with `C <=
4096`. It also receives each row's top `min(C, blocks)` blocks, in no
particular order, `-1` padded. The newest block and any NaN block rank
first, and ties go to the larger block id. The row's own top-k is
returned as before.
- **`candidate_blocks`** (consumer rows): int32 `[B * next_n, C]` of
request-local block ids. Any order, duplicates, `-1` padding and blocks
past the row are allowed, so a source layer's output passes unchanged.
`C * candidate_block_size` must be at most 16384. Each row then ranks
only the visible keys of its listed blocks: its ids and scores are the
plain form's over those keys.
- **`candidate_block_size`:** a power of two from 8 to `min(page_rows,
128)`, and 8 or 16 with `candidate_out`. It is 8 for DeepSeek-V4.1.

`candidate_out` and `candidate_blocks` are mutually exclusive.

### Source rows
- **Scan and token top-k:** the decode logits scan and the row's own
top-k selection run as before.
- **Block scores (scan epilogue):** the scan also writes each block's
score, pinning the newest block and any NaN block to `+inf`. After the
quad reduction, each lane of a warp's 8 row groups holds the scores of
keys `16·warp + g` and `+8` of the tile. So a block of 8 keys takes
three `shfl_xor` across `g`, and a block of 16 is the pair; this is why
`candidate_out` takes blocks of 8 or 16 keys. The epilogue is a separate
scan instantiation (`kBlk`), so the plain scan's code is unchanged. No
extra launch or logits re-read is needed.
- **Block selection:** the existing selection kernel then ranks these
block rows like key rows, with `top_k = C`, so its ids are block ids. A
block row longer than one selection CTA (over 16K blocks, about 128K
keys) needs a histogram. The scan counts it beside the long key rows'
histogram, in a separate long-row state.

### Consumer rows
- **Preparation:** a small kernel (one CTA per row) builds a bitmap of
each row's listed visible blocks. It compacts the bitmap into an
ascending list of distinct blocks and writes the length of the *virtual
row* those blocks form. Only the newest block can be partial, and it is
last, so the virtual row is contiguous.
- **Scan:** the decode logits scan reads the listed blocks back to back
as that row. A dedicated producer branch issues one TMA box per block,
from one lane per box. A box's scales are only 32 bytes, too small for a
tensor copy's 128-byte destination alignment, so they come by
`cp.async.bulk` on the same barrier. The math warps are unchanged.
- **Selection:** a virtual row has at most 16K keys, so it always fits
the single-CTA selection. An epilogue maps the selected positions back
to key ids. The blocks ascend, so positions sort like key ids and ties
still go to the larger key id.
- **Rows of a request:** they have different lists, so consumer calls
use one-row units.

### Both modes
- **CUDA graphs:** every launch is fixed by `C`, the block size and the
batch shape, and nothing synchronizes with the host. A captured graph
replays for any lists and lengths.
- **Dense paths:** untouched. The new producer branch, the selection
epilogue and the extra launches run only when the new arguments are
given.

### Performance

**Setup:**
- **GPU:** RTX PRO 6000 Blackwell Server Edition (SM120, 188 SMs). The
kernels are JIT-built by CUDA 13.3.
- **Shape:** DeepSeek-V4.1's indexer, 32 heads × 128, `top_k` 512, FP8
keys, 64-key pages, `C` = 2048 blocks of 8 keys. Each request has one
row at context `L`.
- **Graphs:** each pipeline is captured in a CUDA graph with
`max_model_len` = 131072, as vLLM captures it.
- **Timing:** CUPTI kernel spans (first kernel's start to last kernel's
end), with L2 flushed before each call. Each figure is the interquartile
mean of 50 replays.
- **Equivalence:** before timing, both pipelines' token and block index
sets were checked equal on every row.

**Source layer.** The baseline is DeepGEMM `fp8_paged_mqa_logits`, then
vLLM's `select_candidate_blocks` (fp32 block scores), then
`persistent_topk`.

| B | L | Baseline (us) | This PR (us) | Speedup | Same rows, plain form
(us) |
|---|---|---|---|---|---|
| 1 | 8K | 89.7 | 9.4 | 9.51x | 7.8 |
| 1 | 32K | 87.5 | 17.8 | 4.92x | 13.1 |
| 1 | 128K | 103.5 | 30.0 | 3.45x | 21.3 |
| 8 | 8K | 97.8 | 15.1 | 6.47x | 13.0 |
| 8 | 32K | 112.6 | 39.2 | 2.87x | 34.0 |
| 8 | 128K | 192.1 | 114.6 | 1.68x | 104.2 |
| 32 | 8K | 113.3 | 31.9 | 3.56x | 30.2 |
| 32 | 32K | 182.4 | 108.4 | 1.68x | 102.9 |
| 32 | 128K | 513.2 | 398.9 | 1.29x | 382.1 |

Every cell measured is faster: B 1/8/32 at 8K-128K, and `next_n` 2,
which is 1.73x-6.25x. Against the plain form, a source row adds the
block selection's launch and the block-score stores, 2-17 us here. The
plain form's own times are unchanged by this PR.

**Consumer layers.** The baseline is DeepGEMM `fp8_paged_mqa_logits`,
then vLLM's `apply_candidate_mask`, then `persistent_topk`. For rows
with at most 2048 blocks, the lists hold every block; longer rows list
the newest block and random others.

| B | L | Baseline (us) | This PR (us) | Speedup | Same rows, plain form
(us) |
|---|---|---|---|---|---|
| 1 | 8K | 16.8 | 12.5 | 1.35x | 7.8 |
| 1 | 32K | 27.9 | 14.8 | 1.89x | 12.9 |
| 1 | 128K | 40.0 | 15.2 | 2.63x | 21.4 |
| 8 | 8K | 25.4 | 18.5 | 1.37x | 13.1 |
| 8 | 32K | 51.0 | 27.3 | 1.86x | 34.1 |
| 8 | 128K | 126.0 | 27.6 | 4.57x | 103.6 |
| 32 | 8K | 56.4 | 37.7 | 1.50x | 30.1 |
| 32 | 32K | 136.7 | 66.3 | 2.06x | 104.9 |
| 32 | 128K | 452.8 | 66.6 | 6.79x | 383.6 |

- **More cells:** at 16K and 64K, and with `next_n` 2, the consumer is
1.22x-3.44x faster. With MXFP4 keys it is 1.22x-5.21x faster.
- **Past 16K keys:** consumer rows stay flat as the context grows.
- **Below 16K keys:** a row that lists all its blocks is slower than the
same row in the plain form (last column). Two costs cause this: the
preparation kernel, and 16 small loads per 128-key tile instead of one
or two. Merging runs of contiguous blocks into larger boxes would close
the gap. It is left for a follow-up and noted under Limitations in the
README.

## 🔍 Related Issues

- **Tracking issue:** #7084.
- **Builds on:** the paged form added in #7085.
- **Earlier scope:** this PR first held only the strided-page-cache fix.
The DeepSeek-V4.1 candidate-block support was folded in so the paged
form's DeepSeek-V4.1 changes are reviewed together.
- **Related, not a duplicate:** #5118 adds DeepSeek-V4.1 MXFP4 candidate
*scoring* (logits only) for SM100, leaving block selection and top-k to
the caller. This PR fuses both roles with the exact top-k on SM120,
inside the existing `dsa_indexer_det_topk` API.

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
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).

Suggested CI test targets:
`tests/experimental/test_sm120_dsa_indexer.py`

**Strided page caches:**
- **`test_paged_strided_pages`:** two layouts, each with its storage
ending at the last page's bytes and the bytes between pages poisoned.
One has a gap after each page (padded pages); the other has pages at an
offset inside larger blocks.
- **`test_paged_validation`:** adds a cache whose rows are strided apart
within a page.
- All nine of these cases fail without the fix.

**Candidate blocks.** The new tests in
`tests/experimental/test_sm120_dsa_indexer.py` check against an exact
FP64 reference.

**Source rows:**
- **`test_paged_candidate_source`:** FP8 and MXFP4, both head counts,
`next_n` 1 and 2, block sizes 8 and 16. The rows have 0 blocks, fewer
than `C` blocks (all published), more than `C`, and more than 16K blocks
(140K keys). Both the row's own top-k and its blocks are checked.
- **`test_paged_candidate_source_cuda_graph`:** one capture replayed
over new lengths and queries, including block rows over 16K blocks,
whose state persists across replays.
- **`test_paged_candidate_source_validation`:** includes rejected block
sizes (4 and 32).

**Consumer rows:**
- **`test_paged_candidates`:** FP8 and MXFP4, both head counts, `next_n`
1 and 2. The rows have 0 keys, a few keys, about 16384 keys, and up to
100K keys. Block sizes are 8, 16 and 64, with page sizes 32, 64 and 128.
The lists have duplicates, `-1` padding and blocks past the row, in
shuffled order.
- **`test_paged_candidates_all_blocks`:** a row listing all its blocks
returns the plain form's ids and scores.
- **`test_paged_candidates_cuda_graph`:** one capture replayed over new
lists, lengths and queries.
- **`test_paged_candidates_small_partition`:** `next_n` 16 on an 8-SM
green context. With fewer CTAs than a request's rows, each row must
still read its own request's block-table row.
- **`test_paged_candidates_validation`.**

**Non-finite scores:**
- **`test_paged_nonfinite_scores`:** NaN or +inf scores, injected
through a key's scale, in several blocks, with C = 1/2/5, on short rows
and on rows of more than 16K blocks.
- **Checks:** exactly C blocks are published, the larger +inf blocks
first, and every token id is in range and unique.
- **What it guards:** the selection's top-bin bound. Before the review
fix, the +inf bin's upper bound was +inf itself. With at least `top_k`
scores at +inf, a one-CTA row dropped those keys and a long row wrote
past its output. A NaN score could also leave ids out of range.
  - **NaN handling:** NaN scores now rank last, as -inf.

All 258 tests in the file pass on an RTX PRO 6000 Blackwell (SM120).
Each checked mechanism has a test that fails without it:

| Change to the code | Failing tests |
|---|---|
| Newest-block pin removed | 14 of 15 source tests |
| Long block-row histogram skipped | The long source rows |
| Consumer selection epilogue disabled | 18 of the first 21 consumer
tests |
| Block-table row computed from the collapsed split | The
small-partition test hits an illegal memory access |

## 🔬 Experimental Track

- [x] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.
Tracking issue: #7084
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
tests/experimental/test_sm120_dsa_indexer.py
```

## Reviewer Notes

- **Non-finite scores:** the selection change is in `rowsel_bin_lo`
(`decode_select_row.cuh`), and the store of NaN scores as -inf is in the
scan. Finite scores rank exactly as before.
- **Commits, in review order:** the two `fix` commits are the
strided-page-cache change. A merge of `main` follows, so the branch
moved forward without rewriting history. Then come the consumer rows,
the source rows, and the review fixes (non-finite scores, input checks).
- **Core change:** the keyword arguments and their docstring in
`flashinfer/dsa_indexer.py`, plus a check that the ragged form rejects
them.
- **Where to look in the kernels:**
- `produce_candidates` in `decode_scan.cuh`: box addressing, and the
window of 64 boxes held by the lanes.
- The selection epilogue in `decode_select_row.cuh`: it relies on
`__syncthreads()` to make the selection's global writes visible within
the CTA.
- The `kBlk` epilogue in `decode_scan.cuh`: the shuffle mapping of the
fragment's row groups to blocks, and the block rows' histogram. It
reuses the long key rows' 16-bit shared counts and their flush, against
a separate state.
- **Launch order:** the block selection reads the block counts, written
by the scan, before its `griddepcontrol.wait`. This is safe because the
token selection never triggers its dependents early, so the block
selection launches only after the scan has finished.
- **Block-score precision:** block scores come from the fp32 logits.
vLLM may keep bf16 logits for its block top-k, so near-tied blocks can
be ordered differently.
- **Scratch:**
- Source rows allocate their block scores `[rows, blocks]` and block
counts per call. The scan writes them, so nothing re-reads the logits.
- Consumer rows allocate their sorted lists and virtual lengths per
call.
  - Under CUDA graph capture, this memory comes from the graph's pool.
- Long block rows reuse the long-row state mechanism, in a separate
per-device buffer. Like the key rows' state, it must be allocated by one
call outside capture.

AI assistance: this change, its tests and the benchmark were written
with Claude Code and reviewed by me.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Paged decode can restrict key selection to specified candidate blocks
or return the highest-scoring blocks alongside the usual key results.
* Candidate options support configurable block sizes, validate candidate
lists and output capacity, and are available only for paged decode.
* **Bug Fixes**
* Paged caches with padded or offset page storage are read without
including gaps between pages.
* Invalid page layouts lacking contiguous data for keys and scales are
rejected.
* Candidate ranking handles NaN and positive-infinity scores
consistently.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Zihua Wu <13583761+lucifer1004@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [e1d9657](https://github.com/flashinfer-ai/flashinfer/commit/e1d965712d28bbe125b6911f2e8e46fb3be667f3)

- **作者**: nulllt2
- **时间**: 2026-11-16T22:43:25Z
- **提交信息**: fix(triton): keep GEMM epilogues in FP32 until the output store (#9095)

<!-- .github/pull_request_template.md -->

## 📌 Description

The pointer-based Triton GEMMs cast their FP32 accumulator to the output
dtype before applying `alpha` and `beta`. With 128x128 FP16 inputs
filled with 32 and `alpha=1/128`, this overflows the intermediate result
and returns `inf` instead of 1024.

Keep the accumulator in FP32 through the epilogue and let the final
store convert it to the output dtype. Add a focused 16-case regression
covering both pointer kernels, FP16/BF16, finite controls, scaling
overflow, beta cancellation and scaling underflow against an FP32
`torch.addmm` reference.

## 🔍 Related Issues

Fixes #9094.

Related: #4724 / #4725 address reading uninitialized C when beta is
zero. This change initializes C in every test and leaves that separate
fix to #4725.

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

`pre-commit run --all-files`: **passed**, including mypy, Ruff,
formatting and the scope-validator self-test. Hooks are installed; `git
diff --check` passed, and the sweep left no source changes.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: Targeted tests cover the two modified kernels; full-scope CI is
not requested.

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/gemm/test_sm_constraint_gemm_epilogue.py
tests/gemm/test_sm_constraint_gemm.py`

Local GPU results: RTX 4090 (SM89), driver 590.48.01, PyTorch
2.12.0+cu130, Triton 3.7.0, Python 3.11.7.

```sh
CUDA_VISIBLE_DEVICES=1 CUDA_HOME=/usr/local/cuda PATH=/usr/local/cuda/bin:$PATH .venv/bin/python -m pytest tests/gemm/test_sm_constraint_gemm_epilogue.py -v
```

- Standard pytest: **16 passed in 19.56s**, no skips, with the normal
package imports and root conftest. The previous missing-`tvm_ffi`
collection blocker is resolved; this run does not use a namespace
bootstrap or mock kernel implementations.
- Earlier baseline `fdd17baec` reproduction: **6 failed, 10 passed** in
the regression suite.
- Hopper/Blackwell hardware, the existing full GEMM matrix and the
complete project suite were not validated locally. The all-tests
checkbox remains unchecked because the full supported-hardware matrix
has not run. Public CI currently reports `CI skipped — pending
authorization`; this account has pull access only, so public CI is not
represented as passing.

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

The descriptor-based GEMM already applies the epilogue to the FP32
accumulator. This patch brings the pointer-based kernels into alignment
with that ordering.

FP16/BF16 outputs can change rounding because the intermediate
conversion is removed. The regression uses powers of two and an FP32
reference so expected results are exactly representable. This is a
correctness change; no performance improvement is claimed.

Self-review followed `.claude/skills/self-review/SKILL.md` and
`docs/code_review_guidance.md`: checked dtype promotion, final-store
conversion, initialized test buffers, architecture guards, and scope of
the complete diff. The indexing, masks, launch configurations and API
signatures are unchanged.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* GEMM operations now apply scaling and combine results at full
precision before converting to half-precision or bfloat16 output. This
improves numerical accuracy in cases involving large or small values and
cancellation, while preserving the expected output format.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->
AI assistance: OpenAI Codex assisted with implementation, self-review,
environment setup, and local test execution.

---------

Co-authored-by: litian <18374328@buaa.edu.cn>

### [baa2875](https://github.com/flashinfer-ai/flashinfer/commit/baa2875ef59fcc5406598fcfe1ce4d5d2fe5ffc8)

- **作者**: Bastian Hagedorn
- **时间**: 2026-11-16T22:09:07Z
- **提交信息**: fix(prims_ts): acquire at cluster scope before reducing the split-KV partials in the decode correction (#9224)

## 📌 Description


`flashinfer/attention/prims_ts/kernels/fmha_decode/fmha_decode_resources/tmem_corr.py`
implements the cluster split-KV reduction of the Prim-TS FMHA decode
kernel (`cluster_shape = [splits_kv, 1, 1]` when
`use_cluster_smem_reduction` is set). The peer CTAs publish their
partial-O vectors and (max, sum) pairs into the owner CTA's shared
memory with `st.async.shared::cluster.mbarrier::complete_tx::bytes`
(`_cluster_store_async_vec4_i32`, `_cluster_store_async_vec2_f32`),
crediting the owner's transaction mbarrier. The owner waits in
`_cluster_wait_transaction_barrier` with
`prims.mbarrier_try_wait_parity(mbarrier, 0, ...)`, publishes lane 0's
wait to the correction group with a named barrier, and
`_reduce_cluster_partial_segment` then loads the peer-written stats and
partials.

`prims.mbarrier_try_wait_parity` without a `scope` argument emits
`mbarrier.try_wait.parity` at the default `.cta` scope. The completing
operation is a release at `.cluster` scope performed by a **peer CTA's
thread** (PTX ISA, `st.async`: the complete-tx operation on the mbarrier
has `.release` semantics at `.cluster` scope). Under the PTX memory
model a release and an acquire synchronize only if each specifies a
scope that includes the thread executing the other. A `.cta`-scope
acquire does not include a thread of another CTA, so the reduction's
reads of the partials have no happens-before edge to the peers' stores.
The named barrier that follows is CTA scope and does not widen the
acquire. (TMA loads into this CTA are different: there the async proxy
acts for the issuing thread, which is in the waiting CTA, and
`.acquire.cta` suffices.)

**Change**: `scope=prims.MBarrierScope.CLUSTER` on both try-waits in
`_cluster_wait_transaction_barrier` (the probe with `time_limit=0` and
lane 0's polling loop), the same spelling the split-K mailbox fixes in
#8853 and #8856 use. Nothing else changes; configurations without the
cluster reduction are not affected.

No wrong result has been observed, and none is expected on current
parts: payload and complete-tx travel together on the DSMEM path. The
ISA does not promise that ordering, which is why #7443, #8853 and #8856
made the same change for the split-K mailboxes. Cost: one
`.acquire.cluster` wait per owner CTA and reduction.

**Update (second commit, 4eb8efd)**: a try-wait with `.acquire.cluster`
makes ptxas invalidate L1 after every attempt, since a cluster-scope
acquire also has to cover global memory. The data this wait protects is
only the owner CTA's shared memory, so the wait is now
`.relaxed.cluster` (`order=prims.MemOrder.RELAXED`) and the acquire is
`fence.acquire.sync_restrict::shared::cluster.cluster`
(`prims.fence_sync_restrict(prims.MemOrder.ACQUIRE)`), executed once
before the existing correction-group barrier. The restricted fence
orders the distributed-SMEM reads and costs no SASS instruction. This is
the acquire pattern of the PTX memory model (a strong read that observes
the release, then an acquire fence), and it is the ISA's own example for
acquiring local shared memory through the generic proxy. Both primitives
are already used elsewhere in `prims_ts` (`fence_sync_restrict(RELEASE)`
and the cluster-scope `order=` argument in the MLA decode 2-CTA loader).

## 🔍 Related Issues

#7443, #8853, #8856 (the same cluster-scope acquire on peer-completed
mailbox barriers in the split-K GEMMs). The vendored copy of this file
in TensorRT-LLM is updated by NVIDIA/TensorRT-LLM#21852, which pins this
change.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues. (ruff check + format and codespell on the
changed file; mypy not run.)

## 🧪 Tests

- [ ] Tests have been added or updated as needed. (Not applicable:
memory-model conformance, no observable failure to test for.)
- [ ] All tests are passing (`unittest`, etc.). (Not yet run on CI. The
change is limited to the `scope` keyword of two existing
`prims.mbarrier_try_wait_parity` calls.)
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).

Suggested CI test targets:
`tests/attention/test_prims_ts_decode_backend.py`

## Reviewer Notes

The change is confined to `_cluster_wait_transaction_barrier`:
`scope=prims.MBarrierScope.CLUSTER` and `order=prims.MemOrder.RELAXED`
on the two existing try-waits, one
`prims.fence_sync_restrict(prims.MemOrder.ACQUIRE)` before the existing
named barrier, and the comment. The wait lowers to
`mbarrier.try_wait.parity.relaxed.cluster`, the fence to
`fence.acquire.sync_restrict::shared::cluster.cluster`; the peers'
`st.async` complete-tx is the matching cluster-scope release.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved synchronization during attention decoding, supporting more
reliable execution when work is coordinated across processing units.
Decoding now waits for required work to be ready before proceeding,
helping avoid inconsistent results. The change improves execution
reliability without altering the available functionality or changing how
users interact with attention decoding.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Bastian Hagedorn <bhagedorn@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [8295ab8](https://github.com/flashinfer-ai/flashinfer/commit/8295ab85af523ff2b1cf9f757c2ab614db4f5709)

- **作者**: Perkz Zheng
- **时间**: 2026-11-16T22:08:48Z
- **提交信息**: feat(prims-ts): NVFP4 KV cache for QToken-KvBlock-Sparse-Attention (#9375)

<!-- .github/pull_request_template.md -->

## 📌 Description

Adds NVFP4 K/V storage to D256 Prims-TS QToken block-sparse attention.
Q's dtype selects the MMA precision: BF16 Q uses BF16 operands, while
FP8 Q uses E4M3-rounded operands; output is BF16.

- Supports interleaved payload/scale rows and separate
`kv_scale_factors`, including strided HND views, with fixed or packed
(`qo_indptr`) queries.
- Treats NVFP4 as an ordinary transform-KV storage dtype. The shared
sparse policy selects the TMEM-transformed Swaps recipe or the QToken
Keeps transform, which converts each raw D256 stage into FP8 or exact
BF16 SMEM K/V rings; the Keeps loader supports separate scales and
non-flat caches.
- The QToken Keeps transform is limited to the QToken sparse route;
dense decode keeps the Keeps SMEM converters from #9315, and their
shared warp roles, register grants and rings key off one
`uses_decode_kv_converter` predicate. On the QToken route the TMEM
transform keeps its slice loops rolled (instruction cache) and separate
scale tensors may be strided HND views; other routes keep fully unrolled
loops and compact, folded scale rows, which the D512 V-scale swizzle
needs.
- Shares membership-layout and prefetch decisions between planning and
workspace sizing. QToken prologue work overlaps metadata generation
while preserving the dependent reads' synchronization.
- Metadata kernels release the attention grid after their last output
store instead of at entry (the attention dependency wait is unchanged),
and the map kernel overlaps its page-table and position loads. Releasing
at entry left attention CTAs resident through the whole metadata grid,
which slowed their later TMA issue and output stores under a cold L2 by
about 5 us on single-wave shapes.

GB300 (SM103), BF16 Q, D256, 128K KV tokens, page size 16, 512 selected
4-token blocks with 70% adjacent-query overlap. Deterministic synthetic
inputs; BF16 K/V holds the exact dequantized NVFP4 values. Cold-L2 CUDA
graphs with PDL; GPU span from metadata start through the split
reduction, mean of two processes, in us:

| Hq/Hkv, batch, query tokens | NVFP4 K/V, interleaved rows | NVFP4 K/V,
separate scales | BF16 K/V |
|---|---:|---:|---:|
| 16/1, 1, 5 | 25.0 | 25.3 | 24.7 |
| 16/1, 32, 4 | 29.6 | 30.1 | 38.9 |
| 16/1, 64, 4 | 40.3 | 41.7 | 57.9 |
| 16/1, 64, 5 | 60.0 | 66.9 | 71.8 |
| 32/8, 1, 4 | 24.3 | 24.2 | 24.8 |
| 64/16, 32, 5 | 222.6 | 233.6 | 412.3 |

Every query row checked in these runs passed the FP32 reference (maximum
row relative L2 0.0033, limit 0.01).

Dense NVFP4 decode stays within about 1% of main or faster (FP8 Q, CUDA
graph, best of 10, in us):

| Shape | main | this PR |
|---|---:|---:|
| D256, batch 64, 64K KV, 1 query token | 402 | 398 |
| D256, batch 64, 64K KV, 6 query tokens | 478 | 461 |
| D512 32/4 heads, batch 32, 32K KV, 6 query tokens, page 64 | 539 | 546
|
| D512 16/2 heads, 5 query tokens, page 32 | 285 | 288 |

## 🔍 Related Issues

Builds on #9222.

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
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust):
`tests/attention/test_attention_ts_q_token_kv_block_sparse_metadata.py
tests/attention/test_attention_ts_decode.py`

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

- On GB300 (SM103), CuTe DSL 4.8.1 / CUDA 13.4:
`test_attention_ts_q_token_kv_block_sparse_metadata.py` 254 passed;
`test_attention_ts_decode.py` 1206 passed, 96 skipped (rebased on main
after #9315). `pre-commit` passed on the changed files (`--all-files`
not run). SM100/SM107 untested.
- Storage-layout and recipe selection add no new batch-size or
sequence-length specialization.
- The prologue change in `decode_gen_kernel` applies only to the QToken
route with metadata-produced lengths; every other route compiles the
same Q-tile check and PDL acquire as before.
- Moving the metadata PDL release changes launch timing only; attention
still acquires the metadata grid before its first dependent read.
- Not in this PR: general paged decode at q_len >= 5 with 8 Q heads per
KV head (remaining #6979 item), which is H128/H512; follow-up.



<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added support for packed NVFP4 K/V caches in D256 QToken-KV
block-sparse attention with BF16 or FP8 queries and BF16 output.
* Supports scales stored alongside packed values or in separate
scale-factor tensors, including supported strided HND layouts.
* Selects a compatible attention execution path based on query type and
workload shape.
* **Bug Fixes**
* Improved coordination so attention waits until sparse metadata has
been written before using it.
* Improved handling of NVFP4 scale fragments and cache layouts across
supported configurations.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Perkz Zheng <67892460+PerkzZheng@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [bf2d4af](https://github.com/flashinfer-ai/flashinfer/commit/bf2d4af5b6326eace002f4549a2bb74fca4bf643)

- **作者**: Ka-Hyun Nam
- **时间**: 2026-11-16T21:52:47Z
- **提交信息**: fix(quantization): route batched NVFP4 quantize on SM107 by total rows (#9471)

<!-- .github/pull_request_template.md -->

## 📌 Description

`useTmaQuantization` on SM107 tests only the per-batch row count `m`
(since #9292), so `fp4_batched_quantize` with `m = 1024` and `b >= 2`
stays on the vectorized kernel, which is slower than the TMA kernel
there. Before #9292 the 32 MiB byte rule routed these inputs to TMA, so
`nvfp4_batched_quantize` B4 M1024 K4096 BF16 regressed from about 9 us
to about 15 us on Vera Rubin.

The fix compares `b * m` against the same thresholds (2048 for the 128x4
swizzled layout, 3072 otherwise). Single-batch inputs route exactly as
before, and other architectures are untouched.

Measured with CUPTI, cold L2, BF16, 128x4 layout, on a Vera Rubin NVL4
node (SM107, 212 SMs). The outputs of the two kernels are bitwise equal
on every shape.

| b, m, k | before (us) | after (us) |
|---|---|---|
| 4, 1024, 4096 | 15.01 | 9.31 |
| 8, 1024, 4096 | 26.96 | 14.91 |
| 16, 1024, 4096 | 49.34 | 23.63 |
| 2, 1024, 4096 | 9.10 | 7.30 |
| 4, 1024, 3072 | 11.92 | 8.05 |
| 4, 1024, 7168 | 18.46 | 13.55 |
| 2, 1024, 7168 | 10.85 | 10.05 |
| 1, 1024, 4096 | 6.14 | 6.18 (stays vectorized, TMA is 6.85) |

A GR100 bring-up board (216 SMs) shows the same ordering; there the
TMA-related tests in `tests/utils/test_fp4_quantize.py` pass (1584
passed).

## 🔍 Related Issues

Follow-up to #9292.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

The hooks ran on the commit's changed files and passed.

## 🧪 Tests

- [ ] Tests have been added or updated as needed. The existing batched
parity test `test_nvfp4_batched_quantize_fp8_tma_matches_non_tma`
already reaches the TMA kernel on SM107 only through the batch count
after this change, so no shape was added.
- [x] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
      Reason:

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/utils/test_fp4_quantize.py`

## Reviewer Notes

Not verified: Vera Rubin NVL72 itself, FP8 batched input timings, and
#9292's single-batch sweep re-run on this branch (single-batch routing
is unchanged by construction).

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* Batched quantization now selects its processing path based on the
total number of rows across batches, rather than the row count in each
batch. This may affect performance for workloads with rows spread across
multiple batches. Existing eligibility conditions and layout-specific
thresholds remain unchanged.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Sonnet 5.5 <noreply@anthropic.com>

### [d73bd1d](https://github.com/flashinfer-ai/flashinfer/commit/d73bd1d3cad8fd7921d3a03f21ddcd1df8ad398f)

- **作者**: Edwin Mascarenhas
- **时间**: 2026-11-16T21:04:02Z
- **提交信息**: perf(gemm): For autotuning cute-dsl mm_mxfp8 GEMMs move from 1 to 16 launches per sample (#8836)

## 📌 Description

The AutoTuner times mm_mxfp8(backend="cute-dsl") and
mm_mxfp8(backend="cutedsl_low_latency") with one launch per sample. For
low latency GEMM shapes and decode GEMMs with small M, running just one
launch per autotune sample has a margin of error in picking the fastest
kernel.

Use the cold launch chain flashinfer-ai#6360 introduced for BF16, with
16 back-to-back launches instead of 1 with rotating buffers for weights
and scales.

## 🔍 Related Issues


[flashinfer-ai#6360](https://github.com/flashinfer-ai/flashinfer/pull/6360)

## Performance 

`benchmarks/flashinfer_benchmark.py --testlist`, cases `--routine
mm_mxfp8 --m M --n N --k K --backends cute-dsl --out_dtype bfloat16
--refcheck --autotune` (tuned at each M, then timed with the tuned pick
under CUDA graph with cold L2):
- shapes: 46 N x K, the dense MXFP8 projections of MiniMax-M3 / M3.1
(23) and DeepSeek-V4.1-Flash (23) at TP1-TP8;
- M: 1, 2, 4, 8, 16, 32, 64, 128, 256 (414 cases per GPU);
- trees: main `0df3b6743` vs this PR, each on two GPUs of one node, tree
order swapped between the GPUs;
- hardware: B300 and B200, driver 580.159.03, torch 2.14.0+cu130,
nvidia-cutlass-dsl 4.8.0.

Every case passed `--refcheck`. Speedup is main time / PR time on the
same GPU, as the geometric mean over the two GPUs.

| GPU | median speedup | geomean | > 5% faster | > 5% slower (on both
GPUs) | best / worst |
|---|---|---|---|---|---|
| B300 | 1.037x | 1.054x | 174 / 414 | 10 (1) | 1.42x / 0.83x |
| B200 | 1.050x | 1.073x | 207 / 414 | 0 | 1.50x / 0.96x |

Median speedup per M:

| M | 1 | 2 | 4 | 8 | 16 | 32 | 64 | 128 | 256 |
|---|---|---|---|---|---|---|---|---|---|
| B300 | 1.022 | 1.022 | 1.036 | 1.014 | 1.066 | 1.056 | 1.032 | 1.040 |
1.053 |
| B200 | 1.029 | 1.033 | 1.059 | 1.035 | 1.092 | 1.098 | 1.044 | 1.065 |
1.063 |

The tuner also becomes repeatable. The two GPUs' tuned times differ by
more than 5% on 137 -> 11 cases (B300) and 116 -> 14 cases (B200), with
the median difference going from 1.8-1.9% to 0.4%.

This benchmark times each launch after an L2 flush, with no kernel
before it. Serving runs the GEMM right after the activation quant, with
PDL, so the next section repeats the comparison in that order.

### The same 414 cases but benchmarking Quant + GEMM rather than back to
back GEMM

Every cute-dsl tactic was timed in vLLM's order: the cute-dsl activation
quant, then `mm_mxfp8` with the tactic forced, PDL on, the weights
rotating through copies totalling more than 2x L2. The quant's own time
(20% of the pair, median) is subtracted, so the numbers are the GEMM's.
Each tuner ran 3 times from a cleared cache with tune M = 256, which
fills every bucket up to 256. Regret is how far the tuner's pick lands
from the fastest tactic, as the mean over the 3 tunings. Speedup is the
GEMM time of main's pick over the GEMM time of this PR's pick.

| | B300 main | B300 this PR | B200 main | B200 this PR |
|---|---|---|---|---|
| regret: median / p90 | 4.8% / 15.1% | **0.3% / 6.0%** | 6.5% / 18.7% |
**0.3% / 4.6%** |
| cases > 5% off the fastest tactic | 199 / 414 | **52** | 246 / 414 |
**34** |
| speedup over main: median / geomean | | **1.028x / 1.048x** | |
**1.046x / 1.062x** |
| > 5% faster / > 5% slower than main | | **151 / 10** | | **199 / 2** |
| best/worst case | | **1.34x/0.904x** | | **1.37x/0.925x** |

Median regret falls at every M, on both GPUs and for both models. With
32 launches the regret median is 0.1% on both GPUs; the speedup over
main is 1.052x (B300) and 1.064x (B200) geomean, with 8 and 1 cases > 5%
slower. On 8 of these shapes, 8 launches left 2-3% median regret.

All 10 of the isolated benchmark's > 5% slower cases are within 5% of
main or faster in serving order. The 0.83x case (`5120 x 1024`, M = 128)
is 1.09x faster there. The 12 cases that are > 5% slower in serving
order (10 on B300, 2 on B200) are listed under Reviewer Notes.


### `backend="cutedsl_low_latency"` in serving order

The same serving-order method, with the low-latency backend's tactics:
44 of the 46 shapes (5120 x 288 and 5120 x 576 have K not divisible by
128, which this backend requires) at M = 1, 2, 4, 8, its limit, so 176
cases per GPU. Each tuner ran 3 times with tune M = 8. GEMM time, quant
subtracted:

| | B300 main | B300 this PR | B200 main | B200 this PR |
|---|---|---|---|---|
| regret: median / p90 | 4.0% / 13.7% | **2.4% / 8.3%** | 7.0% / 18.6% |
**2.1% / 5.5%** |
| cases > 5% off the fastest tactic | 77 / 176 | **39** | 107 / 176 |
**22** |
| speedup over main: median / geomean | | **1.013x / 1.024x** | |
**1.043x / 1.062x** |
| > 5% faster / > 5% slower than main | | **42 / 6** | | **79 / 0** |
| best/worst case | | **1.19x/0.933x** | | **1.40x/0.953x** |

The six B300 losses are 7% or less: MiniMax-M3
`shared_expert.gate_up_proj` 1536 x 6144 (TP4) at M = 1, 4 and 8,
`qkv_proj` 1280 x 6144 (TP8) at M = 1, DeepSeek-V4.1-Flash
`context_wkv_proj` 1536 x 5120 (TP1) at M = 2 and
`shared_experts.down_proj` 5120 x 2304 (TP1) at M = 1. 32 launches gave
about the same result as 16. Tuning time per shape was unchanged (B300
median 13.2 s on main, 13.5 s with this PR; B200 16.5 s and 16.2 s).
## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

> The repository's ruff hooks (format and lint) pass on the two changed
files.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).

Suggested CI test targets: `tests/autotuner/test_autotuner_core.py
tests/gemm/test_mm_mxfp8.py`

`test_cold_chain_profiling_policy_labels` now expects `cold-chain:16`
for the MXFP8 cute-dsl config. On B300 and B200 with this commit:
`tests/autotuner/test_autotuner_core.py` 163 passed, and `pytest
tests/gemm/test_mm_mxfp8.py -k "cute_dsl or cutedsl_low_latency"` 39
passed and 14 skipped (the skips need SM107).

## 🔬 Experimental Track

N/A

## Reviewer Notes

- **Why 16** Rough ballpark since the BF16 used 8, Used MXFP8 with 16
launches. Tested 32 and the gains were very minor.
- **Potential follow-up: adaptive chain length.** Choose N per shape and
bucket so that one sample lasts at least ~100 µs (capped at 32): many
launches for microsecond kernels, few for large prefill GEMMs, where a
fixed 16 mostly adds graph-capture host time. Simulating that rule from
the same tuner traces matched the 32-launch regret.
- **Cases slower than main in serving order.** Twelve of the 828 cases
lose more than 5% of GEMM time. On B300 they are DeepSeek-V4.1-Flash
`attn.wo_b` 5120 x 2048 (TP4) at M = 8 (0.91x) and 16 (0.95x);
`shared_experts.down_proj` 5120 x 2304 (TP1) at M = 1-8 (0.93-0.95x);
`attn.wq_b` 32768 x 1280 (TP1) at M = 256 (0.94x);
`shared_experts.gate_up_proj` 2304 x 5120 (TP2) at M = 1 (0.95x);
MiniMax-M3 `o_proj` 6144 x 2048 (TP4) at M = 8 (0.90x); and
`shared_expert.down_proj` 6144 x 1536 (TP2) at M = 16 (0.93x). On B200
they are DeepSeek-V4.1-Flash `attn.wo_b` 5120 x 4096 (TP2) at M = 8
(0.93x) and `attn.wq_b` 32768 x 1280 at M = 256 (0.95x). All but one
pick the same tactic in all 3 tunings, so they are systematic, not
noise.
- **Where those losses come from.** In 8 of the 12 (for example 5120 x
2304 at M = 1-8) the pick is the fastest tactic, or within 2.5% of it,
when the GEMM runs back to back, but another tactic wins when the
activation quant runs first. The tuner's chain runs the GEMM after
itself, so a longer chain cannot fix this. In the other 4 (5120 x 2048
at M = 8 and 16, 6144 x 2048 at M = 8, 6144 x 1536 at M = 16) the pick
is also 5-10% off in a long back-to-back run, so the tuner's short cold
chain ranks those tactics differently from steady state. Tuning with the
real preceding kernel would be a larger AutoTuner change.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* Updated MXFP8 matrix multiplication performance measurements to use
consecutive launches and account for additional input data.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [802d030](https://github.com/flashinfer-ai/flashinfer/commit/802d030bfdfacc1be5e445426239050a51bc375e)

- **作者**: Lee Nau
- **时间**: 2026-11-16T21:00:39Z
- **提交信息**: fix(gemm): order the TMEM hand-offs of the TGV BF16 GEMM (#9337)

<!-- .github/pull_request_template.md -->

## 📌 Description

Fixes the TMEM hand-off in the CuTe-DSL TGV BF16 GEMM
(`flashinfer/gemm/kernels/tgv_gemm_cute_ext.py`, the `tgv` / `cute_ext`
backend of `mm_bf16` / `bmm_bf16`). These are the same two defects #7443
fixed in the cluster split-K kernel.

1. **TMEM can be freed before the epilogue reads it.** `bar_tmem_alloc`
has 160 arrivals per phase (32 MMA + 128 epilogue).
- Phase 0 means "TMEM allocated"; phase 1 means "epilogue done with
TMEM".
- The MMA warp makes its phase-1 arrival and then waits on parity 1, but
it never waits for phase 0 first.
- If two or more epilogue warps have not yet made their phase-0 arrival,
the MMA warp's arrival counts toward phase 0 instead. The parity-1 wait
then returns at once, because `phaseParity` refers to the current or the
immediately preceding phase. `tcgen05.dealloc` therefore runs while the
epilogue may still be reading TMEM.
   - Fix: the MMA warp now waits for phase 0 before it arrives.
2. **tcgen05 fences.** Every mbarrier hand-off of tcgen05 work now has
`tcgen05.fence::before_thread_sync` before the arrival and
`tcgen05.fence::after_thread_sync` after the wait. This follows the PTX
ISA's canonical tcgen05 synchronization patterns. The six sites are:
   - alloc → epilogue
   - TMA → MMA
   - MMA → epilogue
   - epilogue → dealloc (one site on each side)

It reuses `_tcgen05_fence` from `dense_bf16_gemm_sm100_splitk.py`
(#7443).

Tiles, MMA order and rounding are unchanged. Outputs are bitwise
identical to main for every tactic (see below).

compute-sanitizer synccheck flags defect 1 on main. On the 2-CTA tactic,
every architecture tested reports `Barrier error detected. Missing
wait.` from thread 64, which is the MMA warp, followed by a launch
failure. With this PR it reports 0 errors. The shipped kernel still
returns correct results without injected delays, for two reasons:
- each CTA requests the full per-CTA SMEM, so no other CTA shares its SM
and nothing can reuse the freed TMEM columns;
- the epilogue's first arrival normally lands long before the MMA warp
finishes its mainloop.

## 🔍 Related Issues

- Same defects and fix as #7443 (issue #6786) in the split-K BF16 GEMM.
- Reported by @dhiraj113 in review of #9146.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

- [ ] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/gemm/test_mm_bf16.py
tests/gemm/test_tgv_gemm.py`

No new unit test: the race needs an injected delay to change results, so
a deterministic test can't catch it. The validation below was run on
three architectures. Each machine used the `flashinfer-ci` image (cu130
on GB200 and B300A, cu134 on R100), nvidia-cutlass-dsl 4.8.0, and main
24630ce24 with this patch.

| | GB200 (SM100) | B300A (SM103) | R100 (SM107) |
|---|---|---|---|
| `test_tgv_gemm.py` + `test_mm_bf16.py` | 189 passed | 188 passed, 1
skipped | 189 passed |
| Repro, main (wrong launches out of 20) | 1-CTA 0, 2-CTA 4 | 1-CTA 20,
2-CTA 1 | 1-CTA 20, 2-CTA 3 |
| Repro, this PR | 0 / 0 | 0 / 0 | 0 / 0 |
| synccheck, 2-CTA tactic 16, main | 64 errors + launch failure | 256
errors + launch failure | 96 errors + launch failure |
| synccheck, this PR (1-CTA and 2-CTA) | 0 | 0 | 0 |
| Bitwise identical to main | 124/124 cases, 29 tactics | 124/124 cases,
29 tactics | 196/196 cases, 47 tactics |

**Repro.** The method is the same as #6786. The test runs copies of the
kernel with two test-only edits, neither of which touches the
synchronization:
- epilogue warps 2–3 sleep for 100 µs before their phase-0
`bar_tmem_alloc` arrival;
- the launch requests half the SMEM capacity, so CTAs share an SM.

The 1-CTA case uses tactic 0, or tactic 1 on SM107; the 2-CTA case uses
tactic 16. Shape: M=64, N=16384, K=2048, with PDL on. With either edit
alone, every variant is 0/20. **Bitwise:** for every valid tactic, the
output was compared at four shapes (M,N,K: 1,2048,1024 / 8,4096,4096 /
37,7168,2048 / 128,2112,7168), plus a bias case for tactics 1 and 16,
and checked against an fp32 reference. **synccheck:** 25 launches of
tactics 0/1 and 16.

**Perf.** Each measurement is a CUDA-graph replay of 20 back-to-back PDL
launches. All variants run in one process, interleaved ABBA, and the
table gives the median over rounds in µs per GEMM. "Fix only" is defect
1 alone.
- **GB200 and B300A:** every delta is within ±0.6% (6 rounds, tactics 1
and 16, 6 shapes).
- **R100:** 12 rounds, and the deltas reproduced the 6-round run to
within 0.4%.
  - Fix only: within ±0.3%, except −0.97% at one point.
  - With the fences, the 2-CTA tactics are neutral (−0.6% to +0.3%).
- The 1-CTA tactics move up to 3% faster at large K; the one slowdown is
+1.0%, at tactic 1, M,N,K=64,1024,6144.

<details><summary>Per-shape times (µs per GEMM)</summary>

GB200, CUDA 13.0, driver 580.159.04:

| tactic | M,N,K | main | fix only | this PR |
|---|---|---|---|---|
| 1 (64,8,8) | 1,2112,7168 | 13.718 | 13.719 (+0.00%) | 13.718 (+0.00%)
|
| 1 | 8,2112,7168 | 13.732 | 13.731 (-0.00%) | 13.819 (+0.63%) |
| 1 | 1,7168,2048 | 5.631 | 5.633 (+0.05%) | 5.636 (+0.09%) |
| 1 | 32,7168,2048 | 16.399 | 16.399 (-0.00%) | 16.439 (+0.25%) |
| 1 | 16,4096,4096 | 8.872 | 8.905 (+0.37%) | 8.907 (+0.39%) |
| 1 | 64,1024,6144 | 12.195 | 12.195 (-0.00%) | 12.194 (-0.00%) |
| 16 (64,16,6,2-CTA) | 1,2112,7168 | 10.128 | 10.135 (+0.07%) | 10.134
(+0.06%) |
| 16 | 8,2112,7168 | 10.151 | 10.201 (+0.49%) | 10.148 (-0.04%) |
| 16 | 1,7168,2048 | 4.904 | 4.919 (+0.30%) | 4.909 (+0.10%) |
| 16 | 32,7168,2048 | 9.219 | 9.225 (+0.06%) | 9.221 (+0.02%) |
| 16 | 16,4096,4096 | 6.699 | 6.672 (-0.39%) | 6.664 (-0.52%) |
| 16 | 64,1024,6144 | 9.018 | 9.018 (+0.00%) | 9.018 (+0.00%) |

B300A, CUDA 13.0, driver 595.84.01:

| tactic | M,N,K | main | fix only | this PR |
|---|---|---|---|---|
| 1 (64,8,8) | 1,2112,7168 | 8.340 | 8.340 (-0.00%) | 8.334 (-0.07%) |
| 1 | 8,2112,7168 | 8.369 | 8.372 (+0.04%) | 8.398 (+0.34%) |
| 1 | 1,7168,2048 | 7.046 | 7.046 (+0.00%) | 7.060 (+0.20%) |
| 1 | 32,7168,2048 | 23.392 | 23.393 (+0.00%) | 23.439 (+0.20%) |
| 1 | 16,4096,4096 | 11.068 | 11.067 (-0.01%) | 11.074 (+0.06%) |
| 1 | 64,1024,6144 | 15.103 | 15.102 (-0.00%) | 15.118 (+0.10%) |
| 16 (64,16,6,2-CTA) | 1,2112,7168 | 6.062 | 6.073 (+0.19%) | 6.056
(-0.10%) |
| 16 | 8,2112,7168 | 6.101 | 6.111 (+0.16%) | 6.085 (-0.26%) |
| 16 | 1,7168,2048 | 6.372 | 6.380 (+0.13%) | 6.375 (+0.06%) |
| 16 | 32,7168,2048 | 11.982 | 11.984 (+0.01%) | 11.979 (-0.02%) |
| 16 | 16,4096,4096 | 5.022 | 5.022 (+0.00%) | 5.022 (-0.00%) |
| 16 | 64,1024,6144 | 6.755 | 6.755 (+0.01%) | 6.751 (-0.06%) |

R100, CUDA 13.4, driver 620.62 (12 rounds):

| tactic | M,N,K | main | fix only | this PR |
|---|---|---|---|---|
| 1 (64,8,8) | 1,2112,7168 | 6.048 | 6.043 (-0.08%) | 5.880 (-2.78%) |
| 1 | 8,2112,7168 | 6.049 | 6.046 (-0.04%) | 5.899 (-2.47%) |
| 1 | 1,7168,2048 | 2.962 | 2.964 (+0.04%) | 2.934 (-0.98%) |
| 1 | 32,7168,2048 | 8.075 | 8.075 (-0.00%) | 8.029 (-0.56%) |
| 1 | 16,4096,4096 | 5.524 | 5.527 (+0.04%) | 5.554 (+0.54%) |
| 1 | 64,1024,6144 | 7.440 | 7.437 (-0.03%) | 7.515 (+1.01%) |
| 16 (64,16,6,2-CTA) | 1,2112,7168 | 5.074 | 5.076 (+0.04%) | 5.081
(+0.14%) |
| 16 | 8,2112,7168 | 5.058 | 5.054 (-0.08%) | 5.055 (-0.07%) |
| 16 | 1,7168,2048 | 3.366 | 3.360 (-0.18%) | 3.353 (-0.39%) |
| 16 | 32,7168,2048 | 4.963 | 4.970 (+0.13%) | 4.975 (+0.23%) |
| 16 | 16,4096,4096 | 3.496 | 3.501 (+0.14%) | 3.501 (+0.14%) |
| 16 | 64,1024,6144 | 4.542 | 4.535 (-0.14%) | 4.544 (+0.04%) |
| 30 (64,16,16) | 1,2112,7168 | 6.113 | 6.108 (-0.09%) | 5.930 (-3.00%)
|
| 30 | 8,2112,7168 | 6.118 | 6.109 (-0.16%) | 5.919 (-3.25%) |
| 30 | 1,7168,2048 | 4.443 | 4.430 (-0.29%) | 4.375 (-1.53%) |
| 30 | 32,7168,2048 | 5.746 | 5.739 (-0.13%) | 5.692 (-0.95%) |
| 30 | 16,4096,4096 | 3.989 | 3.989 (+0.01%) | 3.888 (-2.52%) |
| 30 | 64,1024,6144 | 5.342 | 5.343 (+0.03%) | 5.191 (-2.82%) |
| 40 (64,32,16,2-CTA) | 1,2112,7168 | 5.384 | 5.387 (+0.06%) | 5.390
(+0.11%) |
| 40 | 8,2112,7168 | 5.426 | 5.431 (+0.08%) | 5.431 (+0.09%) |
| 40 | 1,7168,2048 | 4.089 | 4.049 (-0.97%) | 4.066 (-0.56%) |
| 40 | 32,7168,2048 | 2.962 | 2.957 (-0.16%) | 2.965 (+0.12%) |
| 40 | 16,4096,4096 | 3.722 | 3.729 (+0.18%) | 3.731 (+0.26%) |
| 40 | 64,1024,6144 | 4.831 | 4.843 (+0.25%) | 4.840 (+0.19%) |

</details>

## Reviewer Notes

- Not addressed here: the 2-CTA path has no cross-CTA handshake before
the `cta_group::2` dealloc; CUTLASS and `TmemAllocator.free` pair the
two CTAs with an mbarrier. Whether that handshake is needed depends on
the dealloc's collective semantics, so it is left for a separate change.
- SGLang vendors this kernel with the same handshake and would need the
same fix.
- AI-assisted (Claude Code); validated on GB200, B300A and R100 as
above.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Updated synchronization during GEMM operations, including matrix
calculations and data transfers. This improves coordination between
execution stages and memory access, helping ensure these operations
proceed in the correct order. No new user-facing features or changes to
public interfaces are included in this update.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [7cbe547](https://github.com/flashinfer-ai/flashinfer/commit/7cbe547cbb2eeab8c1c5ccf44bf247ac7ab4d8ed)

- **作者**: ADonkey
- **时间**: 2026-11-16T20:58:51Z
- **提交信息**: fix(gemm): handle unaligned N in b12x FP4 and MXFP8 stores (#7182)

<!-- .github/pull_request_template.md -->

## 📌 Description

b12x MXFP8 and FP4 used a TMA output descriptor even when compact
FP16/BF16 rows had a stride that was not divisible by 16 bytes. For
example, M=2, N=129, K=384 produces misplaced output rows and changes
output canaries. Even M=1 can change canaries while the logical output
appears correct.

Use predicated global stores for those rows, retaining the existing
shared-memory epilogue and its tile barriers. Aligned outputs keep TMA
stores. Include the resolved store mode in the kernel cache key so
aligned and tail-N calls cannot reuse the wrong specialization.

For MXFP8 on RTX 5090 / CUDA 13.0, aligned-output kernel latency changes
by -0.3% to +0.3% across eight shapes (M=1/17/128/512, N/K=128/384 or
4096/4096). Timings use cold L2, CUDA Graphs and CUPTI, with three
rounds of 30 samples per baseline–candidate–baseline boot.

## 🔍 Related Issues

Fixes the b12x unaligned-N output bug reported by @Raymondlol in
https://github.com/flashinfer-ai/flashinfer/pull/5943#issuecomment-5959561467.
This is independent of that PR's new cute-dsl backend and #5191's
partial-K support.

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
- [ ] All tests are passing (`unittest`, etc.).

On RTX 5090, PyTorch 2.12.1+cu130 / CuTe DSL 4.7.1:

- `.venv/bin/python -m pytest tests/gemm/test_mm_mxfp8_sm120.py -q
--full`: 356 passed.
- `.venv/bin/python -m pytest tests/gemm/test_mm_fp4.py -q -k b12x`: 15
passed on 2026-10-30. All six added NVFP4/MXFP4 tail-N cases fail on
`9550df8` and pass with the FP4 runner fix. They cover FP16/BF16 output,
guards, aligned/tail-N cache reuse, autotuning and CUDA Graph replay.
- Memcheck and synccheck on those six FP4 cases: zero errors. The tests
restrict autotuning to the tested M; the initial unrestricted run hit
allocation failures while profiling unrelated default M buckets.
- The 356-case SM120 MXFP8 file and pre-commit on
`flashinfer/gemm/gemm_base.py` and `tests/gemm/test_mm_fp4.py` also pass
on the updated head.
- Memcheck, synccheck and racecheck on the 122 alignment / tactic tests:
all pass; zero sanitizer errors and zero racecheck hazards.
- 2,400 persistent-tile stress executions across both output types,
prefetch modes and K=128/384: zero wrong outputs.
- CUDA Graph replay, every advertised tactic, autotune, alternating
aligned/unaligned cache use, nonuniform block scales, output canaries
and delayed PDL producers pass.
- `pre-commit run --files benchmarks/bench_mxfp8_output_alignment.py
flashinfer/gemm/gemm_mm_mxfp8_cute_dsl.py
flashinfer/gemm/kernels/dense_blockscaled_gemm_sm120_b12x.py
tests/gemm/test_mm_mxfp8_sm120.py` and `git diff --check` pass.
`--all-files` was not run.
- Benchmark: `benchmarks/bench_mxfp8_output_alignment.py --output
results.jsonl`; add `--tail` for corrected tail-N shapes.

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

Only SM120 was tested on hardware. The non-TMA path requires
split_k_slices=1, matching both runners' tactics. The FP4 runner now
resolves the same store mode before its cache lookup and passes it to
the shared kernel; aligned FP4 outputs still use TMA. Tail-N timings are
absolute latencies; incorrect baseline output is not used to claim a
speedup.

This change was developed with AI assistance.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved MXFP8 matrix multiplication for output widths that do not
align with the preferred store size. Results are now written safely
across irregular output shapes while preserving existing behavior for
aligned shapes.
* Improved FP4 matrix multiplication output handling for aligned and
unaligned widths across supported backends and output types.

* **Tests**
* Added coverage for varied output types, dimensions, execution paths,
autotuning, and CUDA graph replay to help ensure reliable results across
supported configurations.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [c21661c](https://github.com/flashinfer-ai/flashinfer/commit/c21661ccc80038031ecec3936a1e7579b6308996)

- **作者**: Samuel Nordmann
- **时间**: 2026-11-16T20:52:27Z
- **提交信息**: feat(comm): support MNNVL packed group FP8 fusion (#3850)

<!-- .github/pull_request_template.md -->

## 📌 Description

Extends the packed per-token-group FP8 fusion patterns from #3059 to the
MNNVL backend:

- `kARResidualRMSNormPerTokenGroupFP8PackedQuant` (pattern 8)
- `kARResidualRMSNormOutPerTokenGroupFP8PackedQuant` (pattern 9)

Both one-shot and two-shot paths produce E4M3 activations and packed
UE8M0 scales in the existing DeepGEMM-compatible layout. They share
scale computation and packing with TRT. The normalized values are
rounded to the input dtype before quantization, so the norm-out variant
can be checked byte-for-byte against quantization of its materialized
output.

MNNVL requires each CTA to own whole quantization groups. Unsupported
partitions fail before launch. Full-warp CTAs use a deterministic
shuffle mask; partial warps and groups smaller than a vector use shared
memory. Python validates buffer shape, dtype, strides, alignment, and
device before dispatch.

The multi-node runner retains both group-FP8 coverage and upstream's
renamed one-sided Sentinel test. Distributed tests select the
launcher-local GPU before NCCL initialization and pass it explicitly as
`device_id`; deriving the device from global rank caused CUDA-device
mismatches when ranks did not fill each node. The test-helper import
follows upstream's new `tests.comm.test_helpers` location. MXFP8 retains
internal quantization ID 4; packed group FP8 uses ID 5. Public pattern
IDs and output layouts are unchanged.

## 🔍 Related Issues

Related: #2434, #2364. Extends the TRT packed-group fusion introduced in
#3059 to MNNVL.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

All hooks pass on the nine PR files, including mypy, Ruff, and
clang-format; Python compilation, shell syntax, and diff-whitespace
checks pass. The whole-repository `--all-files` box remains unchecked
because validation is scoped to this PR.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: Targeted communication tests cover this change; full-scope CI is
not requested.

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust):
`tests/comm/test_trtllm_mnnvl_allreduce_group_fp8_quant.py
tests/comm/test_trtllm_allreduce_fusion_group_fp8_quant.py
tests/comm/test_trtllm_mnnvl_allreduce_mxfp8.py`

Author GPU validation on `b1da467ca61e6ce44cf1110747e265c96415c79f`
passed on four GB200s (Lyris job 3471580, node lyris0024, driver
580.196, CUDA 13.1, Torch 2.11.0a0+eb65b36914.nv26.02):

- **105/105 MNNVL group-FP8 tests per rank**, including FP16/BF16/FP32,
exact bytes/exponents, padding, partial warps, small groups, wide rows,
invalid inputs, and PDL CUDA Graph replay.
- **4/4 TRT group-FP8 regression tests**.
- **2/2 selected four-rank MNNVL MXFP8 tests**; four other
parameterizations deselected.
- Slurm `COMPLETED`, exit `0:0`, elapsed 5m58s.

Reproduction after setting up FlashInfer and MPI:

```bash
mpirun -np 4 python -m pytest -q tests/comm/test_trtllm_mnnvl_allreduce_group_fp8_quant.py -x -s
python -m pytest -q tests/comm/test_trtllm_allreduce_fusion_group_fp8_quant.py -x -s
python -m pytest -q tests/comm/test_trtllm_mnnvl_allreduce_mxfp8.py -k '4' -x -s
```

Current head `0065f2496a0ecc786d0cd21751b03d2f2a6ff263` includes
upstream `a2e3d1e7075edf57c87248c63f206c3a3b87a185` (2026-11-16). The
current CUDA 13.4 CI container uses PyTorch NCCL device inference based
on global rank when neither `device_id` nor `LOCAL_RANK` is supplied;
the shared helper now accepts explicit binding. Eight new host
regressions cover Slurm/torchrun, sparse node placement, full nodes, and
a single visible GPU. Isolated execution of the actual helper/test AST
with mocked CUDA calls passes all eight; the old initialization sequence
and omission of explicit NCCL binding each fail all eight.
**Current-head two-node Rubin validation passed: 113/113 tests per
rank**, including all 82 GPU correctness/graph cases, 23 invalid-input
cases, and eight launcher regressions. Rhea job 58570 completed with
exit `0:0` in 2m26s on rhea0199–0200 (same NVLink block nvlblk12). One
rank per node with four visible GPUs exercises the sparse placement that
exposed the bug. NCCL logs confirm both ranks use CUDA device 0.

Runtime: NVIDIA VR NVL72 (SM 10.7), driver 620.70.06, CUDA 13.4.59,
Torch 2.15.0.dev20260923+cu134, NCCL 2.30.7+cuda13.3; repo CI image
`flashinfer/flashinfer-ci-cu134:20261106-54b9f685`. Source kernels were
compiled without an installed `flashinfer_jit_cache` package.
Reproduction uses `srun --mpi=none -N2 -n2 --ntasks-per-node=1` with
`MASTER_ADDR` set to the first node, followed by `python -m pytest -q
tests/comm/test_trtllm_mnnvl_allreduce_group_fp8_quant.py -x -s` inside
the CI container.

The [November 5 public CI
run](https://github.com/flashinfer-ai/flashinfer/actions/runs/41944346238)
passed on previous head `630f0504e`, including H100 targeted tests and
six AOT import jobs. The [internal CI
report](https://github.com/flashinfer-ai/flashinfer/pull/3850#issuecomment-6676776073)
reported 82 PR-related Rubin multi-node failures (`Expected tensor on
cuda:0 but found tensor on cuda:1`). The launcher-local-device fix
addresses that defect. Other reported failures were classified by CI as
pre-existing MXFP8 failures or infrastructure/incomplete runs; they are
not claimed fixed here.

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

Review focus: exact CTA partitioning, packed-scale padding,
shared-memory synchronization, and the shared TRT helper extraction. The
upstream cluster-barrier fix is retained. No unresolved inline review
threads remain.

GitHub reports the current head as mergeable and approved. New-head
pre-commit passed; API/documentation and docs-build checks are still
running. Fresh authorized public/internal CI is still required on the
pushed fix; the [new public
summary](https://github.com/flashinfer-ai/flashinfer/actions/runs/43866983043/job/133297996433)
skipped GPU execution pending authorization. Suggested targeted rerun:
`tests/comm`.

Earlier July evidence includes 8×GB200/two-node correctness. Multi-node
validation and comparative performance were not rerun for the October
updates.

<details>
<summary>Historical performance — July 2026, not remeasured on this
head</summary>

These measurements predate the current upstream integration and
validation fixes; they have not been remeasured on the current head.



4xGB200, BF16 input, group size 128, CUDA Graphs, cold-L2 rotation,
CUDA-event timing. Values are arithmetic means of two independent run
medians; each run contains 100 iterations and reports max-rank latency.
Across the best strategy for each measured shape, fusion is
`2.33x-5.98x` faster than the exact unfused FlashInfer AR+RMSNorm plus
Torch quantization/scale-packing composition.

| Shape | Strategy | Fused | Unfused | Speedup |
| --- | --- | ---: | ---: | ---: |
| `1x4096` | one-shot | `6.338 us` | `34.272 us` | `5.408x` |
| `16x4096` | one-shot | `6.546 us` | `39.111 us` | `5.975x` |
| `128x4096` | two-shot | `9.207 us` | `43.405 us` | `4.715x` |
| `1024x4096` | two-shot | `32.826 us` | `94.907 us` | `2.891x` |
| `1024x8192` | two-shot | `64.501 us` | `150.007 us` | `2.326x` |

A same-node ABBA comparison against the pre-review kernel measured
`-0.97%` to `+0.51%` latency deltas across all 18 shape/strategy pairs,
i.e. no measurable regression from the review hardening.

</details>

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added support for packed per-token-group FP8 quantization in allreduce
fusion paths.
  * Introduced a new group size option for FP8 quantization workflows.
* Expanded benchmarking and CUDA Graph replay coverage for the new
quantization mode.

* **Bug Fixes**
* Improved validation for tensor shapes, scale storage, and padding
requirements.
* Added stricter checks for distributed execution and runtime
configuration handling.

* **Tests**
* Added distributed correctness tests for normal execution and graph
replay.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [779b3d7](https://github.com/flashinfer-ai/flashinfer/commit/779b3d70c1e42172f761027f75631efddcf04e34)

- **作者**: Jimmy Zhou
- **时间**: 2026-11-16T20:37:24Z
- **提交信息**: chore: add @jimmyzho to autotuner CODEOWNERS (#9539)

Add myself as a code owner for the autotuner paths
(`flashinfer/autotuner/`, `tests/autotuner/`, `tests/cpu/autotuner/`) so
I get review requests for autotuner changes.

CODEOWNERS-only change; no code touched.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Chores**
* Updated ownership assignments for Autotuner areas. This internal
maintenance change does not affect app functionality or the end-user
experience.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [b947d70](https://github.com/flashinfer-ai/flashinfer/commit/b947d70fabd85e2498f7811444afe2a0bf480848)

- **作者**: Louis Sugy
- **时间**: 2026-11-16T20:32:37Z
- **提交信息**: perf(moe): prims-TS epilogue optimizations (#9404)

## 📌 Description

This PR optimizes the SwiGLU clamp and block-scaled quantization:

- `_clamp_f32_trt`: from 4 to 2 instructions using `max.NaN.f32` and
`min.NaN.f32`
 - `_clamp_upper_f32_trt`: from 2 to 1 instruction
- SF floor: remove unnecessary `max`: the SF value is either 0 or >=
2^-9, and 0 special case is already handled.

The PR also adds `--profile` and `--host-input-gen` in the batched GEMM
runner, and tests for the special case of zero scales.

## 🔍 Related Issues

N/A

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

## Reviewer Notes

N/A


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added a profiling mode that launches a Batched GEMM workload once
without correctness checks or timing.
* Added an option to generate inputs on the host for profiling,
validation, and benchmarking.
* Documented how to launch the profiler without correctness checks,
timing, or stream capture.
* Profiling must be run separately from benchmarking and validation-only
mode.
* **Bug Fixes**
  * Improved NaN and subnormal handling in activation calculations.
  * Corrected SwiGLU beta handling and NVFP4 scale conversion.
* **Tests**
  * Added coverage for zero-input and host-generated input cases.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [9f29ff4](https://github.com/flashinfer-ai/flashinfer/commit/9f29ff4883e481c119e1d1ba61e8112db5433034)

- **作者**: Zixin Huang
- **时间**: 2026-11-16T20:31:38Z
- **提交信息**: docs(gemm): state that DeepGEMM grouped FP8 GEMMs need power-of-two scales on SM100 (#8889)

## Impact
**`group_deepgemm_fp8_nt_groupwise` and
`batch_deepgemm_fp8_nt_groupwise` silently apply float32 block scales
that are not powers of two up to 2x too small on SM100 / SM103 /
SM107.** The docstrings describe `a_scale` / `b_scale` as plain
`torch.float32` per-token / per-block scales, so a caller using the
common recipe `scale = amax / 448` gets wrong output with no error.

## Problem
On these architectures the DeepGEMM kernels consume UE8M0 scales.
`get_col_major_tma_aligned_packed_tensor` (`flashinfer/deep_gemm.py`)
converts each float32 scale with `x.view(torch.int) >> 23`, keeping only
the exponent, i.e. `2 ** floor(log2(scale))`. The tests and the
docstring examples only ever pass power-of-two scales, because
`per_token_cast_to_fp8` / `per_block_cast_to_fp8` in
`flashinfer.testing.utils` round them up with `2 ** ceil(log2(...))`, so
the requirement never shows up there.

## Fix
Documentation only:
- Both docstrings state that on SM100 / SM103 / SM107 the scales must be
powers of two, what happens otherwise, and how to produce them.
- The examples import `per_token_cast_to_fp8` / `per_block_cast_to_fp8`
from `flashinfer.testing.utils`, where they are defined;
`flashinfer.utils` does not export them.

Validating the scales at call time would need a device-to-host
synchronization on every call, which breaks CUDA graph capture, so this
PR only documents the contract.

## Test
No behaviour change. `ruff check` / `ruff format --check` pass on the
changed file.

cc @cyx-6 @jimmyzho

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Documentation**
* Clarified that on SM100, SM103, and SM107, FP8 scales are rounded down
to the nearest power of two when converted to UE8M0. Non-power-of-two
scales may consequently be applied at up to half their specified value.
* Recommended using power-of-two scales for both inputs. The
batch-operation documentation also notes that this requirement applies
to the Cake backend’s block-scaled routes.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [6761139](https://github.com/flashinfer-ai/flashinfer/commit/6761139f6115954dbb96cdb110977910f4e64c60)

- **作者**: Sam
- **时间**: 2026-11-16T20:10:22Z
- **提交信息**: fix(gemm): read the mm_bf16 CuTe-DSL warp split-K bias after the PDL wait (#7591)

<!-- .github/pull_request_template.md -->

## 📌 Description

In the warp split-K kernel behind `mm_bf16(backend="cute-dsl",
pdl=True)`, only the activation loader warps call `griddepcontrol.wait`.
The compute warps read the bias without waiting, so a bias the previous
kernel is still writing can be read stale.

The compute warps now wait before the bias read when the kernel has a
bias. The weight loads stay ahead of the wait: weights are static
parameters, as in the PDL contract of #6799.

## 🔍 Related Issues

Follow-up to #7288 (raised in its review). Same class of fix as #6322
and #7188.

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

`test_mm_bf16_cute_dsl_warp_splitk_pdl_waits_for_bias` uses `late_store`
from `tests/test_helpers/pdl.py` (added on main by #6322). It triggers
the dependent launch, then writes the first 32 bits of the bias late;
the test compares the output bitwise against a normal run. It calls the
warp split-K kernel directly so the backend selector cannot route around
it.

| B200 (SM100) | Before | After |
|---|---|---|
| `test_mm_bf16_cute_dsl_warp_splitk_pdl_waits_for_bias` | failed |
passed |

Also run on B200 with this PR: `tests/gemm/test_mm_bf16.py -k
"warp_splitk_pdl_waits or cute"`, 11 passed.

### Performance

There is no measurable change: the compute warps cannot start their K
loop before the activation tiles arrive, and the activation loaders
already wait. B200, `pdl=True`, default tactic, 32 back-to-back launches
captured in a CUDA graph and timed with CUDA events, median µs per GEMM.
"Cold" cycles through distinct weights totalling over 4x the L2 size, as
consecutive decoder layers do; "hot" reuses one weight. With bias:

| m × n × k | cold before | cold after | hot before | hot after |
|---|---|---|---|---|
| 1 × 768 × 7168 | 4.16 | 4.17 | 4.14 | 4.16 |
| 8 × 768 × 7168 | 4.35 | 4.35 | 4.33 | 4.35 |
| 16 × 2304 × 1536 | 2.81 | 2.82 | 2.56 | 2.59 |
| 8 × 4096 × 4096 | 5.99 | 5.97 | 4.54 | 4.54 |
| 32 × 1024 × 7168 | 5.35 | 5.37 | 5.16 | 5.18 |
| 1 × 1024 × 128 | 1.70 | 1.72 | 1.35 | 1.35 |

Without bias the kernel is unchanged, and before and after agree within
0.05 µs. Each configuration was run twice, interleaved; the table shows
the first run, and the two runs agree within 0.04 µs.

<details>
<summary>Benchmark script</summary>

```python
import torch
from flashinfer.gemm.kernels.dense_bf16_gemm_warp_splitk import default_tactic, run_warp_splitk_dense

CHAIN, REPEAT = 32, 50
L2_BYTES = torch.cuda.get_device_properties(0).L2_cache_size
for m, n, k in [(1, 768, 7168), (8, 768, 7168), (16, 2304, 1536), (8, 4096, 4096), (32, 1024, 7168), (1, 1024, 128)]:
    for has_bias in (False, True):
        sets = max(CHAIN, -(-4 * L2_BYTES // (n * k * 2)))
        a = torch.randn((m, k), device="cuda", dtype=torch.bfloat16)
        bs = [torch.randn((n, k), device="cuda", dtype=torch.bfloat16) for _ in range(sets)]
        biases = [torch.randn((n,), device="cuda", dtype=torch.bfloat16) if has_bias else None for _ in range(sets)]
        out = torch.empty((m, n), device="cuda", dtype=torch.bfloat16)
        tactic = default_tactic(m, n, k)
        for mode in ("cold", "hot"):
            stream = torch.cuda.Stream()
            with torch.cuda.stream(stream):
                for i in range(3):
                    run_warp_splitk_dense(a, bs[i].T, out, True, tactic, biases[i])
            torch.cuda.synchronize()
            graphs = []
            for g in range(sets // CHAIN if mode == "cold" else 1):
                graph = torch.cuda.CUDAGraph()
                with torch.cuda.graph(graph, stream=stream):
                    for i in range(CHAIN):
                        j = g * CHAIN + i if mode == "cold" else 0
                        run_warp_splitk_dense(a, bs[j].T, out, True, tactic, biases[j])
                graphs.append(graph)
            for graph in graphs * 3:
                graph.replay()
            times = []
            for r in range(REPEAT):
                start, end = torch.cuda.Event(enable_timing=True), torch.cuda.Event(enable_timing=True)
                start.record()
                graphs[r % len(graphs)].replay()
                end.record()
                end.synchronize()
                times.append(start.elapsed_time(end) * 1000 / CHAIN)
            times.sort()
            print(f"{mode} m={m} n={n} k={k} bias={int(has_bias)} median={times[len(times) // 2]:.2f} us")
```

</details>

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

- The review on #7288 pointed at the bias. If biases are meant to be
static parameters like the weights in #6799, this wait is not needed and
the PR can be closed; I added it because, unlike the weights, a bias is
a plausible output of a preceding kernel.
- The weight loads are left ahead of the wait on purpose, following
#6799. The MXFP8 sibling kernel (`dense_mxfp8_gemm_warp_splitk.py`)
waits before its weight loads; that is outside this PR.
- SM103 and SM107 run the same kernel but were not tested; I have no
such GPUs.
- `tests/test_helpers/pdl.py`: main's `late_store` (#6322) takes a float
and stores it as `c_float`. This PR widens it to take an `int | float`
and store its 32 bits in `dst`'s dtype, so the test can write a raw word
of the bf16 bias. Existing callers pass a Python float for a float32
tensor and get the same bits.



<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Tests**
* Added coverage for BF16 GEMM with bias on supported hardware, checking
that output remains consistent when bias data changes between runs. This
helps verify the reliability of the bias-wait path.
* **Documentation**
* Clarified comments describing weight-loading and bias-access
assumptions for the warp Split-K kernel.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: almightychang (Sam, Joochul Chang) <almightychang@icloud.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [eec9e79](https://github.com/flashinfer-ai/flashinfer/commit/eec9e7921c471b4e38d80b8352bc39dfb19bc282)

- **作者**: ranx2026
- **时间**: 2026-11-16T20:07:37Z
- **提交信息**: trtllm-gen: raise on cubin load failure, skip unloadable cubins on Windows (#6436)

**What this fixes**. On native Windows arm64 the FP4 MoE path crashed
inside the CUDA driver at the first launch (issue #5322): the trtllm-gen
launcher dropped the result of cuModuleLoadData and launched an
uninitialised handle when the Windows driver rejected a Linux-assembled
cubin.

**Changes** (the narrowed version by @aleozlx, cherry-picked as is).
Every trtllm-gen cubin is load-checked before use. The default tactic is
chosen lazily: the first shape-valid config whose cubin loads. A shape
with no loadable cubin raises a RuntimeError that names the cubin
instead of crashing. A failed cubin download or checksum hands the
native side empty bytes, and the checked driver load then fails like on
any bad cubin; the loader convention (always a buffer) is unchanged. No
environment switch; nothing changes where every cubin loads.

**Verification.** Windows arm64, GB300 whose driver rejects part of the
cubin set: the FP4 MoE call ends in the named RuntimeError, no crash;
with a Windows-assembled cubin set it completes. Eleven trtllm-gen MoE
test files: no node lost against the previous head. Linux GB300 and
B200: the four trtllm-gen MoE test files are unchanged node for node,
and the three workspace-size nodes that failed in CI round one pass.

**Review notes.** The earlier revision's Windows-only skip list and its
environment switch are gone. CLAUDE.md no longer documents a switch.
Follow-up, separate PR: re-assembly of the rejected cubins on Windows so
the call succeeds without a hand-built set.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Batched GEMM operations now select configurations with kernels that
load successfully and report an error when no usable configuration is
available.
* FP4 block-scale MoE operations can try alternative tile sizes during
default-tactic launches when the selected tile is unavailable.
* Kernel loading failures are handled more consistently, and
unsuccessful loads no longer return stale data.
* MoE tactic selection now uses the device associated with the input
tensors, improving correctness when multiple devices are in use.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Alex Yang <aleyang@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [2192f05](https://github.com/flashinfer-ai/flashinfer/commit/2192f0509d674d22ac8118c8813d9c0d6d91bdc5)

- **作者**: Bo Li
- **时间**: 2026-11-16T20:07:10Z
- **提交信息**: perf(fused_moe): faster routing and finalize for precomputed top-k (#8495)

## 📌 Description

Faster routing and finalize kernels of the fused MoE
(`csrc/fused_moe/trtllm_backend`) for precomputed top-k ids, the path
the expert-parallel split layer takes: the MoE receives each token's
expert ids and weights from the dispatch. The trtllm-gen and Prims-TS
MoE backends share these kernels.

| Commit | Change |
|---|---|
| finalize, one warp per token | `finalizeKernelWarpPerToken` for
128-bit aligned rows and top_k <= 32: after the PDL wait, lanes read the
permuted indices and weights and keep several loads per local expert in
flight; small batches split rows across `blockIdx.y`. Large batches ran
many short waves at about half the HBM bandwidth. |
| full-width cluster routing | Precomputed top-k ids only need the
histogram, offsets and permutation, which spread over all threads, so
the 1024-thread single-cluster variant replaces the 256/512-thread ones
sized for the score-to-top-k path. |
| cooperative routing above 4096 tokens | The cooperative kernel, which
spreads the histogram and permutation over all SMs, now takes
precomputed batches above 4096 tokens. |
| single-CTA permutation, 17..512 tokens | The shared permutation is
templated on its CTA count; one 1024-thread CTA runs it with plain
shared memory and `__syncthreads`, without the cluster barriers and
distributed-shared-memory reads (routing kernel about 5.8 -> 3.5-4 us at
32..512 tokens). |
| single-CTA permutation, 9..16 tokens | The dyn-block kernel grows with
the batch; the single-CTA kernel is faster from nine tokens on. |
| 4-CTA cluster, 257..3072 tokens | Half as many remote histogram reads
and CTAs per cluster barrier as the 8-CTA cluster. |

MoE compute stage, DeepSeek-V4.1-Flash experts (hidden 5120, 384
experts, top-6, inter 2304, MXFP4 x MXFP8), EP8 on B300 (us). Each
commit message has its own before/after numbers. The finalize change:

| T per rank | Prims-TS before | after | trtllm-gen before | after |
|---:|---:|---:|---:|---:|
| 8 | 42.3 | 41.0 | 46.3 | 45.9 |
| 512 | 198.7 | 192.0 | 201.5 | 197.2 |
| 1024 | 242.2 | 230.3 | 242.9 | 232.4 |
| 4096 | 761.6 | 712.6 | 732.1 | 672.2 |

and, for small batches, the single-CTA permutation at T = 4/8/16:
Prims-TS 28.4/36.2/54.0 -> 26.4/34.0/51.8 us, trtllm-gen 31.6/43.0/65.1
-> 29.3/40.4/62.6 us.

## 🔍 Related Issues

Layer 1 of the stack
https://github.com/flashinfer-ai/flashinfer/stack/8499 (four PRs); the
layers above build on it:
1. #8495 **this PR**: routing and finalize for precomputed top-k
2. #8496 Prims-TS weight cache policy per expert
3. #8497 Prims-TS MXFP4 x MXFP8 MoE GEMMs
4. #8498 split layer: finalize the experts into the combine input

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

Validated on 8 B300s at the top of the stack (#8498, 7564ad77d) against
plain `main` (4d0c28d83, which includes #7585); no failure that `main`
does not also have. `pre-commit run --from-ref main` passes. The
performance numbers above were measured on an earlier `main` (5f79e6f26)
and have not been re-measured after the rebase.

- `tests/moe/test_trtllm_gen_fused_moe.py`: 784 passed, 4519 skipped, 28
xfailed, as on `main`.
- `tests/moe/test_trtllm_gen_routed_fused_moe.py` 375 passed;
`test_trtllm_gen_routing.py` 690 passed, 24 skipped;
`test_trtllm_gen_fused_moe_routing_renormalize_{bf16,fp4,fp8}.py` 16 /
20 / 112 passed; `test_trtllm_gen_per_token_moe.py`,
`test_trtllm_gen_moe_workspace.py`,
`test_trtllm_gen_moe_autotune_tactics.py` and
`test_trtllm_fp4_routed_moe_routing_metadata.py` pass.
- The routing tests cover 1, 7, 8, 32, 64 and 1024 tokens. An additional
check outside the test suite compared precomputed top-k routing with
logits routing at 1, 8, 9, 12, 16, 17, 64, 256, 257, 512, 513, 2048,
3072, 3073, 4096, 4097 and 8192 tokens, MXFP4 x MXFP8 and NVFP4, packed
and unpacked ids: 102 of 102 match.
- `tests/moe/test_unified_moe_prims_ts.py` (Prims-TS calls the same
kernels): 39 passed, 1 xfailed.

After the review fix, rerun at the stack top 45cae150a: this PR adds
e7066ac4f, which keeps every lane of `finalizeKernelWarpPerToken` in the
loop that holds its full-mask shuffles (with top-k 22 or 32 at hidden
size 128 or 1152, every row came out wrong before it, as a check outside
the suite showed; all rows match a float reference after it).
`tests/moe/test_trtllm_gen_fused_moe.py` passes in every part it was
split into; `test_trtllm_gen_routed_fused_moe.py` 375 passed;
`test_trtllm_gen_fused_moe_routing_renormalize_{bf16,fp4,fp8}.py` 16 /
20 / 112 passed; `test_trtllm_gen_per_token_moe.py` 50 passed;
`test_trtllm_fp4_routed_moe_routing_metadata.py` 95 passed.

Rebased onto main at 1bdba8725. #8610 moved the PDL wait of
`finalizeKernelVecLoad` and `finalizeKernelSmallBatch` before their
reads of the routing outputs; 1f4040f17 does the same for
`finalizeKernelWarpPerToken`, so every finalize kernel reads what
another kernel wrote only after the wait. The reads no longer overlap
the GEMM before the finalize: on the EP8 shape above, the finalize
kernel takes 0.1 to 0.8 us longer at T = 8..4096 per rank (trtllm-gen:
7.16 -> 7.95 us at T = 8, 14.57 -> 14.66 us at 512, 97.39 -> 97.62 us at
4096). At T = 8 that is more than the 0.4 us the finalize change saves
for trtllm-gen in the table above. The other commits are unchanged. At
1f4040f17: `tests/moe/test_trtllm_gen_routing.py` 690 passed, 24
skipped; `test_trtllm_gen_routed_fused_moe.py` 375 passed;
`test_trtllm_gen_fused_moe_routing_renormalize_bf16.py` 16 passed;
`test_trtllm_gen_per_token_moe.py` 50 passed;
`test_trtllm_gen_fused_moe.py::test_deepseekv3_routing -k Relu2` 6
passed; `test_trtllm_fp4_routed_moe_routing_metadata.py` 95 passed;
`test_trtllm_gen_moe_pdl_ordering.py` (from #8610) 1 passed;
`tests/cpu/moe` 217 passed. At the stack top (#8498, eac484dc8):
`tests/moe/test_trtllm_gen_fused_moe.py` passes in every part it was
split into;
`test_trtllm_gen_fused_moe_routing_renormalize_{bf16,fp4,fp8}.py` 16 /
20 / 112 passed; `test_trtllm_gen_moe_autotune_tactics.py` 95 passed;
`test_trtllm_gen_moe_workspace.py` 186 passed;
`test_trtllm_gen_moe_pdl_ordering.py` 1 passed; the check outside the
suite that compares precomputed top-k routing with logits routing: 102
of 102 match.

Rebased onto main at 88077bda8, with two new commits. The first CI run
did not compile the routing kernels for SM80 and SM89: the single-CTA
permutation instantiates the shared `routingPermutation` for every
architecture of the routing module, and the CUDA headers declare the
cluster barrier intrinsics and `cluster_group` only for SM90+, which
nvcc looks up even in the branches that `if constexpr` discards.
b47c71dc4 compiles the cluster statements only on SM90+; the code for
SM90+ is unchanged, and the host still launches the single-CTA kernel
only on SM90+. The `moe_utils` module now builds for sm_80, sm_89,
sm_90a, sm_100a, sm_103a and sm_120f; before b47c71dc4, sm_80 failed
with the errors of the CI run. 952ef731f launches only the
warp-per-token finalize slices that hold steps: with FP16, hidden size
8192 and 300 tokens, 8 steps went to 7 slices of 2, and the last three
got none. The other commits are unchanged. At 952ef731f:
`tests/moe/test_trtllm_gen_routing.py` 690 passed, 24 skipped;
`test_trtllm_gen_routed_fused_moe.py` 375 passed;
`test_trtllm_gen_fused_moe_routing_renormalize_bf16.py` 16 passed;
`test_trtllm_gen_per_token_moe.py` 50 passed;
`test_trtllm_gen_fused_moe.py::test_deepseekv3_routing -k Relu2` 6
passed; `test_trtllm_fp4_routed_moe_routing_metadata.py` 95 passed;
`test_trtllm_gen_moe_pdl_ordering.py` 1 passed; `tests/cpu/moe` 217
passed. At the stack top (#8498, 39aa95d58):
`tests/moe/test_trtllm_gen_fused_moe.py` passes in every part it was
split into;
`test_trtllm_gen_fused_moe_routing_renormalize_{bf16,fp4,fp8}.py` 16 /
20 / 112 passed; `test_trtllm_gen_moe_autotune_tactics.py` 95 passed;
`test_trtllm_gen_moe_workspace.py` 186 passed; the check outside the
suite that compares precomputed top-k routing with logits routing: 102
of 102 match.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance Improvements**
* Improved mixture-of-experts routing performance for small and medium
token batches on supported GPUs.
* Expanded routing coverage across batch sizes and workloads, while
preserving existing routing behavior for workloads that use other paths.
* Improved aggregation of routed expert outputs for eligible workloads
by distributing work across output slices. These improvements apply only
to supported configurations and do not change available routing or
output features.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Bo Li <22713281+bobboli@users.noreply.github.com>

### [943b09d](https://github.com/flashinfer-ai/flashinfer/commit/943b09d1bdb12023c1738a276810c80339701d16)

- **作者**: feih-nv
- **时间**: 2026-11-16T20:04:30Z
- **提交信息**: fix(moe): guard the CuTe-DSL act-fusion SFC store at the N boundary; align offset Rubin pointers (#9383)

<!-- .github/pull_request_template.md -->

## 📌 Description

Two fixes to the CuTe-DSL MoE kernels, from upstream TensorRT-LLM
commits FlashInfer's copies predate.

- **SM100 act-fusion kernel wrote scale factors past the N boundary**
([NVIDIA/TensorRT-LLM#21401](https://github.com/NVIDIA/TensorRT-LLM/pull/21401),
act-fusion part). In
`blackwell/blockscaled_contiguous_gather_grouped_gemm_act_fusion.py` the
SFC store at the end of the epilogue ran for every subtile; scale blocks
past the last column land in the next 128 rows' scale factors (the
`TODO: Need to think about predicate on it` comment marked the spot).
The store is now guarded on the N boundary, for both the vectorized and
the MXFP8 scalar-byte path.
- **`_Pointer.__add__` kept the base alignment**
([NVIDIA/TensorRT-LLM#19184](https://github.com/NVIDIA/TensorRT-LLM/pull/19184)
for the Blackwell utils,
[NVIDIA/TensorRT-LLM#19183](https://github.com/NVIDIA/TensorRT-LLM/pull/19183)
for the Rubin copy). `_Pointer` had no `__add__`, so an offset pointer
inherited the base's `assumed_align` and could claim 16-byte alignment
for a misaligned address. The override computes `gcd(offset bytes, base
alignment)`. It is added to `common/kernel_utils.py`, which every launch
path (Blackwell, Hopper and Rubin kernels) builds its pointers through,
and to `rubin/utils.py` for parity with upstream; the Rubin copy has no
caller today.

## 🔍 Related Issues


[NVIDIA/TensorRT-LLM#21401](https://github.com/NVIDIA/TensorRT-LLM/pull/21401),
[NVIDIA/TensorRT-LLM#19183](https://github.com/NVIDIA/TensorRT-LLM/pull/19183).

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

New: `test_numerical_accuracy_ragged_sf_n` (w4a4, intermediate sizes 768
and 1152, Swiglu and Relu2), where the act-fusion epilogue's last N
subtile row is partial. It is an accuracy check at those shapes, not a
regression test for the guard: with the guard removed it still passes
and `compute-sanitizer --tool memcheck` reports no error, because the
extra scale-factor stores land inside the padded SF buffer (the next 128
rows' SFs, which are then overwritten in order). A shape that makes the
aliasing observable was not found in this test harness. The mxfp8
scalar-byte path already runs at intermediate size 128 in this class.
`tests/moe/test_cute_dsl_fused_moe.py` on B200 (CUDA 13.0 CI container):
819 passed, 22 skipped, at FlashInfer `e3ebb9e7dd` + this commit. The
`__add__` override has no caller in the current kernels (pointers are
built once per launch and not offset), so it changes no behavior today;
the Blackwell lane re-ran after it was added to
`common/kernel_utils.py`.

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

Perf, local B200 (CUDA 13.0 CI container,
`benchmarks/flashinfer_benchmark.py --routine
cute_dsl_fp4_block_scale_moe`, CUDA-event timing, 50 iterations),
upstream/main `ae58183fa` vs this branch; the SFC guard sits in GEMM1's
act-fusion epilogue, so these are the shapes it runs on, two with an
intermediate size that is not a multiple of the SF tile:

| tokens | hidden | intermediate | experts | top_k | main (ms) | this PR
(ms) |
|---|---|---|---|---|---|---|
| 256 | 1024 | 512 | 256 | 2 | 0.060 | 0.060 |
| 256 | 2048 | 768 | 32 | 2 | 0.035 | 0.035 |
| 1024 | 2048 | 768 | 32 | 2 | 0.038 | 0.038 |
| 1024 | 2048 | 1152 | 32 | 2 | 0.046 | 0.046 |
| 1024 | 7168 | 2048 | 256 | 8 | 1.163 (std 0.025) | 1.121 (std 0.263) |

No measurable difference; the last row's gap is within its noise.


Whether a FlashInfer caller can hit the SFC overrun depends on `n % (128
* sf_vec_size)`; the guard is cheap either way.

### [bc11503](https://github.com/flashinfer-ai/flashinfer/commit/bc115037eab0b4ff6c1471f7a13a396f25fde721)

- **作者**: feih-nv
- **时间**: 2026-11-16T20:04:07Z
- **提交信息**: fix(moe): four upstream fixes to the CUTLASS MoE / GEMM sources (#9380)

<!-- .github/pull_request_template.md -->

## 📌 Description

Four fixes to the TRT-LLM CUTLASS MoE / GEMM sources under
`csrc/nv_internal`, from upstream TensorRT-LLM commits FlashInfer's
copies predate, plus one FlashInfer-side fix in the same quantization
kernel.

- ~~PDL wait without a memory clobber (NVIDIA/TensorRT-LLM#9695, header
part)~~ dropped at review (`2419e49d6`): the header it changed,
`cutlass_extensions/arch/grid_dependency_control.h`, is included by
nothing in this tree. The MoE kernels (and TRT-LLM's own pingpong GEMM)
take `cutlass/arch/grid_dependency_control.h` from the CUTLASS
submodule, which is bare at pin `b46b16d0` and already carries the
clobber on CUTLASS main; the fix arrives with the submodule bump, not
here.
- **NaN from `448 / amax`**
([NVIDIA/TensorRT-LLM#11256](https://github.com/NVIDIA/TensorRT-LLM/pull/11256)).
The 1x128 and 128x128 block-scale quantization kernels in
`fp8_blockscale_gemm_kernel.cuh` guarded only `amax == 0`; a tiny
nonzero amax gave an inf scale and NaN output. `amax` is clamped to
`1e-10` first.
- **`util_convert_type` returned a dangling fragment**
([NVIDIA/TensorRT-LLM#20017](https://github.com/NVIDIA/TensorRT-LLM/pull/20017)).
`moe_cute_util.cuh` built the result tensor over a stack
`cutlass::Array` that goes out of scope on return; it now copies into a
tensor that owns its storage, with a static assert that the input is
contiguous.
- **SM120 / SM121 launch check**
([NVIDIA/TensorRT-LLM#12704](https://github.com/NVIDIA/TensorRT-LLM/pull/12704),
launcher part). Consumer Blackwell has 99 KiB of shared memory per
block; both TMA warp-specialized launchers now check the kernel's
`SharedStorage` against `cudaDevAttrMaxSharedMemoryPerBlockOptin` before
launching, so an oversized tile fails with a message instead of a launch
error. Upstream's heuristic-level filter (keep only
`CtaShape128x128x64B`) is not taken: FlashInfer's SM120 list already
drops the `...x64B` tiles for FP8 activations, so the filter left W4A8
with no tactic on RTX PRO 6000 / Spark (first push of this PR), and the
`128x128x128B` tile it relies on fits there.
- **`scale_128x128_kernel` reduced its amax over the wrong rows**
(FlashInfer-side, found in review). The reduction loop bounded the
column check with the row index `i` instead of the inner index `j` (the
write loop already used `j`): `scales_idx_x * 128 + i * 32 + lane_id >=
dim_x` breaks out of the reduction at row `i >= (dim_x - scales_idx_x *
128) / 32`, so for any `dim_x` below about 4200 every 128x128 block's
amax came from its first rows only and the remaining rows saturate at
448. Upstream still has `i`; FlashInfer's 2025-10 import carried it over
and this fix is FlashInfer-first. Only the internal BF16-weight
quantization path (`weight_scale=None`) is affected, and that kernel now
reads all 128 rows of a block for the amax where it read the first few;
its write loop already read the whole block, so the kernel is at most
about 2x its old (wrong) cost on that path only. The amax floor is
applied in fp32 so a half instantiation would not flush `1e-10` to 0.

No kernel arithmetic changes except the amax clamp and the reduction
bound above.

## 🔍 Related Issues


[NVIDIA/TensorRT-LLM#9695](https://github.com/NVIDIA/TensorRT-LLM/pull/9695),
[NVIDIA/TensorRT-LLM#11256](https://github.com/NVIDIA/TensorRT-LLM/pull/11256),
[NVIDIA/TensorRT-LLM#20017](https://github.com/NVIDIA/TensorRT-LLM/pull/20017),
[NVIDIA/TensorRT-LLM#12704](https://github.com/NVIDIA/TensorRT-LLM/pull/12704)
(launcher part).
[NVIDIA/TensorRT-LLM#11561](https://github.com/NVIDIA/TensorRT-LLM/pull/11561)
is not needed: FlashInfer gates the SM120 TMA warp-specialized path on
`isValidSM120MOESpecialisation`, so pure-int weight-only configs never
reach the SM120 list.

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

New: `test_fp8_blockscale_gemm_weight_amax_covers_whole_block` (SM90a):
weight blocks whose rows 0-3 are tiny and whose other rows sit near the
FP8 maximum, against the BF16 reference; a reduction that stops after
the first rows saturates the block. It runs in the GitLab H100 job (the
file is SM90-only and skips on B200). For the upstream fixes no new
tests: the SM120 / SM121 launch check needs consumer Blackwell hardware,
the dangling fragment is undefined behavior that happens to work today,
and the NaN needs an amax below `1e-10`. Run on B200 (CUDA 13.0 CI
container): `tests/gemm/test_fp8_blockscale_gemm.py` and
`tests/moe/test_trtllm_cutlass_fused_moe.py -k "test_moe[ or
test_moe_fp8_block_scaling or test_moe_w4a8[ or test_moe_fp8[ or
test_moe_nvfp4["`: 56 passed, 86 skipped (SM90-only and Hopper-only
variants), at FlashInfer `e3ebb9e7dd` + this commit.

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

Reviewers with SM120 / SM121 hardware:
`tests/moe/test_trtllm_cutlass_fused_moe.py` covers the launch check;
the GitLab lane runs it on RTX PRO 6000 and Spark.

### [f0b61e9](https://github.com/flashinfer-ai/flashinfer/commit/f0b61e9ba40eeaebfe3573a8f948f88600c63453)

- **作者**: feih-nv
- **时间**: 2026-11-16T20:03:43Z
- **提交信息**: fix(comm): Lamport clear size in 16-bit units shared by every writer; fence the Helix sender before refilling shared memory (#9379)

<!-- .github/pull_request_template.md -->

## 📌 Description

Two fixes to the TRT-LLM-derived communication kernels, from upstream
TensorRT-LLM commits FlashInfer's copies predate.

- **Lamport clear size kept in elements of the writer's dtype**
([NVIDIA/TensorRT-LLM#21283](https://github.com/NVIDIA/TensorRT-LLM/pull/21283)).
`LamportComm` in `trtllm_allreduce_fusion.cuh` and
`trtllm_moe_allreduce_fusion.cuh` recorded `params.size * NRanks`
elements for the next kernel to clear, and that kernel divided by its
own `VEC_SIZE`. Every Lamport kernel on a workspace shares the slot. The
Python wrapper refuses a call whose dtype disagrees with the workspace's
`use_fp32_lamport`, so the mismatch needs a lower-level call that
bypasses that check on a workspace created with `use_fp32_lamport=True`:
a bf16 kernel following an fp32 one then cleared half the bytes and read
stale data, and the reverse over-cleared. Within one dtype the old count
was right; the fix makes the slot's unit independent of the writer. The
slot now counts 16-bit units and readers round up to whole 16-byte
stores. Upstream switched the slot to bytes; FlashInfer cannot, because
the cake kernels on the same workspace
(`csrc/cake_trtllm_moe_allreduce_union/`,
`csrc/cake_moe_finalize_allreduce_fusion/`, 36 generated files) write
bf16 / fp16 element counts and read `clear_size / 8`. Two-byte units
keep bf16 / fp16 bitwise as before, stay compatible with cake, and still
fix fp32. The workspace layout is unchanged (`kernel_flag_ptr[4]`,
initialized to 0); its docstring now names the unit (`5da38d8bc`).
- **Lamport clear stores wrote the clearing kernel's own `-0`**
(FlashInfer-side, found in review). A bf16 / fp16 kernel cleared with
`0x8000` pairs, which an fp32 kernel two calls later reads as
`0x80008000`, not fp32 `-0`, and takes as arrived data. The clear now
writes the fp32 `-0` pattern (`0x80000000` per word) whatever the dtype:
fp32 readers see `-0`, bf16 / fp16 readers (trtllm and cake both test
each 16-bit half) see `0x8000` in the high half. Remaining gap, not
touched here: the cake kernels still clear with bf16 `-0` pairs, so cake
followed by an fp32 trtllm kernel on one workspace is still unsafe; no
caller does that today.
- **Helix all-to-all sender refill ordering**
([NVIDIA/TensorRT-LLM#20939](https://github.com/NVIDIA/TensorRT-LLM/pull/20939),
fence part). In `helixAllToAll.cu` the sender's `protoPack` stores and
the register S2G loads go through the generic proxy, and the next
iteration refills the same shared memory with `cp.async.bulk` (async
proxy) without a fence between them. A `fence.proxy.async.shared::cta`
before the `__syncwarp` orders them, matching the receiver side that
#5172 already fenced.

## 🔍 Related Issues


[NVIDIA/TensorRT-LLM#21283](https://github.com/NVIDIA/TensorRT-LLM/pull/21283),
[NVIDIA/TensorRT-LLM#20939](https://github.com/NVIDIA/TensorRT-LLM/pull/20939).

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

The existing multi-rank tests
(`tests/comm/test_trtllm_allreduce_fusion*.py`,
`test_trtllm_moe_allreduce_fusion*.py`, `test_dcp_alltoall.py`) cover
the touched kernels; they need 2+ GPUs, which the development node does
not have, so this PR relies on the GitLab multi-GPU lane. Local: the
`trtllm_comm` and DCP all-to-all JIT modules build on the branch (CUDA
13.0 CI container). `trtllm_comm`, `dcp_alltoall` and
`dcp_alltoall_generated` built on B200 in the CUDA 13.0 CI container.

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

Upstream also moved the clear size to a 64-bit slot in a new workspace
word; FlashInfer keeps the existing `int` slot because `clear_size <=
lamport_comm_size`, which the Python side caps at `MAX_COMM_SIZE`. The
bf16-after-fp32 case needs a workspace used with both dtypes, and the
cake interplay a workspace alternating `backend="trtllm"` / `"cake"`
with different inputs; no existing test does either, and same-input A/B
runs pass even when stale data is read. A mixed-dtype / mixed-backend
case would be the regression test if reviewers want one. The GitLab lane
for the latest push includes `test_cake_moe_allreduce_union.py` and
`test_cake_moe_finalize_allreduce.py`.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved synchronization for data transfers on supported GPUs, helping
ensure copied data is available in the correct order.
* Standardized temporary-buffer clearing across data types, with sizes
rounded to the required alignment.
* **Documentation**
  * Clarified how temporary-buffer clear sizes are measured.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [1658f0b](https://github.com/flashinfer-ai/flashinfer/commit/1658f0bf02b65fe9a71862286f6da546d0fce890)

- **作者**: S.J. Lee
- **时间**: 2026-11-16T19:39:13Z
- **提交信息**: feat(sparse): graduate qsa_sparse_paged_attention to a stable API (#9474)

<!-- .github/pull_request_template.md -->

## 📌 Description

This graduates `flashinfer.sparse.qsa_sparse_paged_attention` and its
default kernel (SM80 through SM90, NVFP4, FP8 and BF16 KV caches) from
the experimental track to a stable API, as planned in the tracking issue
#6803. The signature and the supported targets stay as they are. The
backend moves out of `flashinfer/experimental/qsa_nvfp4/` into the
regular layout:

- kernel: `include/flashinfer/attention/qsa_sparse_paged.cuh`
- launcher and TVM-FFI exports: `csrc/qsa_sparse_paged.cu` and
`csrc/qsa_sparse_paged_jit_binding.cu`
- JIT generator: `flashinfer/jit/qsa_sparse_paged.py`
- Python backend: `flashinfer/sparse.py` (the former
`experimental/qsa_nvfp4/backend.py` with renamed helpers)

Only names and file locations change. The sm_80 and sm_90a SASS of all
14 kernels matches the experimental build instruction for instruction.

The rest of the change is what a stable API needs:

- `flashinfer/aot.py` builds the module when the target list has an 8.x
or 9.x arch, so the jit-cache carries it. Release wheels drop
experimental kernel sources, so with a PyPI wheel the API fails today on
its first JIT build; the moved sources are not experimental and ship in
the wheel.
- The entry point is a `@flashinfer_api` with one trace definition per
cache format in `flashinfer/trace/templates/qsa.py`
(`qsa_sparse_paged_attention_nvfp4`, `_fp8`, `_bf16`; the formats run
different kernels), an example in `tests/trace/example.py` and its
reference JSON.
- `flashinfer.qsa_sparse_paged_attention` is exported, and
`docs/api/sparse.rst` documents it. The docstring now also carries the
contract the removed README held: the GQA group limit, which entries are
skipped, zero rows, and the BF16 rounding before the gate.
- The tests move to
`tests/attention/test_qsa_sparse_paged_attention.py`.
- The experimental package, its README and
`examples/experimental/qsa_nvfp4.py` are removed. vLLM calls
`flashinfer.sparse.qsa_sparse_paged_attention`, so no caller imports the
removed module.

The Cake backend in `flashinfer/experimental/cake_qsa_nvfp4/` stays
experimental, and its code does not change; its README and package
comment now describe the opt-in below. With the entry point no longer an
`@flashinfer_experimental_api`, the routing follows the policy for
experimental backends behind a stable API:

- `backend="cake"` works as before and emits the experimental warning
once.
- `backend="auto"` with an NVFP4 cache on a Cake target (10.0, 10.3,
10.7, 12.0) now needs `FLASHINFER_ALLOW_EXPERIMENTAL_AUTO_BACKENDS=1`
and raises a `RuntimeError` without it. vLLM's integration
([vllm-project/vllm#64199](https://github.com/vllm-project/vllm/pull/64199),
still open) calls with the default backend, so on these targets it needs
the variable or `backend="cake"`. Release wheels do not ship Cake's
sources, so this route did not run from a PyPI wheel before either.
- Routing for FP8 and BF16 caches and for 8.x and 9.0 targets does not
change.

## 🔍 Related Issues

Tracking issue: #6803

The open PR #8440 edits `flashinfer/experimental/qsa_nvfp4/jit.py`,
which this PR removes, so whichever of the two lands second needs a
rebase.

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
`tests/attention/test_qsa_sparse_paged_attention.py
tests/experimental/test_cake_qsa_nvfp4_api.py
tests/trace/test_fi_trace_template_consistency.py`

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

- On sm_80, `tests/attention/test_qsa_sparse_paged_attention.py` passes
(46 tests), `tests/experimental/test_cake_qsa_nvfp4_api.py` passes with
one skip (the auto-to-Cake case needs a Cake target), and the trace
example writes the committed JSON.
- The SASS check compiled main and this branch for sm_80 and sm_90a: 14
kernels and 20,816 instructions, no difference.
- AOT: a target list of `8.0 8.6 8.9 9.0a` builds the module for sm_80,
sm_86, sm_89 and sm_90a, `8.6` alone builds it, and `10.0a 12.0a` leaves
it out.
- The CPU trace tests cover the three definitions, and a CPU trace of
each cache format gives three distinct names.
- `test_auto_cake_route_requires_the_experimental_opt_in` now also
asserts the warning on the explicit and the opted-in route.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added a public sparse paged-attention API for Qwen QSA, supporting
NVFP4, FP8, and BF16 KV caches.
* Added trace support for sparse paged attention across the supported
cache formats.
* Added experimental Cake backend routing for NVFP4 on supported GPUs.
Automatic selection requires
`FLASHINFER_ALLOW_EXPERIMENTAL_AUTO_BACKENDS=1`; explicitly selecting
Cake displays a warning.
* **Documentation**
* Documented the API, supported cache formats, and backend-selection
behavior.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: lesj0610 <lesj0610@gmail.com>

### [d494bfe](https://github.com/flashinfer-ai/flashinfer/commit/d494bfeb61f283c42c39332c785d8c3b582accfd)

- **作者**: S.J. Lee
- **时间**: 2026-11-16T18:37:13Z
- **提交信息**: fix(attention): skip the kv length copy fa2 paged prefill never reads (#9397)

<!-- .github/pull_request_template.md -->

## 📌 Description

`BatchPrefillWithPagedKVCacheWrapper.plan()` copies the per-request kv
lengths it builds on the host into `_kv_lens_buffer` with
`non_blocking=True`. fa2 never reads that buffer; its kernels derive the
lengths from `paged_kv_indptr` and `paged_kv_last_page_len`. Unless the
caller passes `seq_lens` as a pinned int32 CPU tensor, `plan()` builds
the host lengths in pageable memory, and a `non_blocking` copy from
pageable memory can be silently synchronous. So on fa2 the copy is
wasted work that can also sync the stream. vLLM runs its CI with a sync
check (`VLLM_GPU_SYNC_CHECK=error`) that flags such copies, and it
currently exempts the `plan()` of
`BatchPrefillWithCausalBidirectionalRangesWrapper`, which only runs fa2
and takes no `seq_lens`.

This skips the copy when the plan resolves to fa2. The one fa2 plan that
still needs it is on a `backend="auto"` CUDA graph wrapper that captured
cuDNN in an earlier plan: the retained cuDNN graph keeps reading the
buffer, and the refresh later in `plan()` counts on this copy for the kv
lengths. That case still stages them, keyed on the same retained
Q-length buffer the refresh checks. Other backends, fa3 included, keep
the copy as before; I only changed and tested fa2.

The new `test_batch_prefill_fa2_plan_skips_kv_lens_buffer` fills the
buffer with a sentinel and plans on fa2 three ways: eagerly, with a CUDA
graph wrapper, and with a CUDA graph wrapper holding a cuDNN Q-length
buffer, as a retained capture leaves it. The first two must leave the
buffer untouched and the last must stage the lengths. Without this
change the first two fail, and skipping the copy on every fa2 plan fails
the last. On SM80 the new test passes, and so do these:
`tests/attention/test_bidirectional_ranges_attention.py` (79 passed),
`test_batch_prefill_with_paged_kv_cache` (351 passed, 65 skipped), and
`test_auto_backend_upgrade.py`, `test_cudnn_wrapper_regressions.py`,
`test_prefill_uniform_q_len_plan.py` together with the paged plan tests
next to the new one (214 passed, 155 skipped).
`test_paged_auto_fallback_refreshes_retained_capture` covers a real
retained cuDNN capture but only runs on SM10x, so I couldn't run it.

## 🔍 Related Issues

Replaces #9370, which forwarded `seq_lens` through the ranges wrapper
and only changed where the unused copy came from.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
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
reviewers may adjust): `tests/attention/test_batch_prefill_kernels.py
tests/attention/test_bidirectional_ranges_attention.py
tests/attention/test_cudnn_wrapper_regressions.py`

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

* **Bug Fixes**
* Improved paged KV-cache planning for FA2 by avoiding unnecessary
KV-length staging. Other backends and CUDA-graph plans that require KV
lengths continue to handle them as expected.
* Added coverage for ordinary and CUDA-graph planning scenarios to
verify the expected KV-length behavior.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: lesj0610 <lesj0610@gmail.com>

### [f25a0c2](https://github.com/flashinfer-ai/flashinfer/commit/f25a0c25a0cc07871b871341ac49e52a05532b9d)

- **作者**: Brian K. Ryu
- **时间**: 2026-11-16T17:56:20Z
- **提交信息**: feat(batch_invariant): batch-invariant fp8 per-tensor unified `MoELayer` (`BatchInvariantFp8PerTensorConfig`) (#9406)

<!-- .github/pull_request_template.md -->

## 📌 Description
The second MoE backend of the batch-invariant mode. Adds
`BatchInvariantFp8PerTensorConfig()` as a backend candidate of the
unified `MoELayer` for the quantization pair `(FP8PerTensor,
FP8PerTensor)`:

```python
from flashinfer.fused_moe import (BackendOptions, BatchInvariantFp8PerTensorConfig, ExpertConfig, MoEActivationPack, MoEConfig,
                                  MoELayer, MoEWeightPack, QuantConfig, QuantFormat, RoutingConfig, SwiGLU)
from flashinfer.fused_moe.api import RoutingInputMode, RoutingMethodType

cfg = MoEConfig(routing=RoutingConfig(num_experts=E, top_k=k, method=RoutingMethodType.Renormalize),
                quant=QuantConfig(weight=QuantFormat.FP8PerTensor, activation=QuantFormat.FP8PerTensor),
                experts=ExpertConfig(intermediate_size=I), activation=SwiGLU(),
                backend=BackendOptions((BatchInvariantFp8PerTensorConfig(),)))
layer = MoELayer(cfg)
weights = MoEWeightPack()
weights.prepare_for("batch_invariant_fp8_per_tensor", BatchInvariantFp8PerTensorConfig.prepare_weights(
    w1, w2, hidden_states_scale_global=m_x, intermediate_scale_global=m_inter, num_local_experts=E, hidden_size=H,
    intermediate_size=I, activation=SwiGLU()))
xq, _ = BatchInvariantFp8PerTensorConfig.prepare_activations(x, hidden_states_scale_global=m_x)
out = layer(MoEActivationPack(xq, None, routing_input_mode=RoutingInputMode.FromLogits, routing_logits=logits), weights)
```

The scales follow FlashInfer's per-tensor convention where
`hidden_states_scale_global` and `intermediate_scale_global` are the
calibrated E4M3 multipliers (`q = x * s`); the experts are quantized at
preparation with one `448 / amax` multiplier per expert and GEMM (the
bytes of `prepare_trtllm_fp8_per_tensor_weights`'s cast); the
activations are e4m3 `[T, H]` with no scale tensor in the pack. The
backend takes the three routing input modes (from logits through the
shared route kernels: `Default`, `Renormalize`, `RenormalizeNaive`,
`Sigmoid`, `SigmoidRenorm`, `TopK`, `TopKSigmoid`, `Llama4` top-1 and
`DeepSeekV3` with or without its expert groups; pre-routed ids and
weights under any `RoutingConfig`), every typed activation of the layer
(gated on the (gate, up) pair: `SwiGLU` with any `alpha` / `beta` /
`limit`, `SwiGLUStep`, `GeGLU`, `GeGLUTanh`, `SiTU`, `PowLU`; ungated:
`ReLU2`, `Identity`, `GELU`, `ReLU`, `SiLU`), on SM100 / SM103 / SM107.
It refuses, with the mode's error and no fallback, `do_finalize=False`
(the slot-order combine is part of the class) and expert-parallel shards
(`local_expert_offset` / `local_num_experts`: the class's EP form is not
part of this backend).

### Performance
The batch-invariant backend (`BatchInvariantFp8PerTensorConfig`,
labelled **batch-invariant** below) through the unified `MoELayer`
against the fastest existing FlashInfer fp8 per-tensor backend of each
regime -- TRTLLM-Gen (`TrtllmFp8PerTensorConfig`), CUTLASS fp8
per-tensor on both parts, prims-TS on SM100 only (it refuses SM107) --
on the same bf16 source weights and the same calibrated multipliers, in
two operator forms and two modes:
* **form A** = pre-routed (`PackedPrecomputed` ids and weights from one
common routing; the permutation, the two grouped GEMMs and the combine
as each backend implements them),
* **form B** = from logits (the routing inside the op: ours, TRTLLM-Gen,
prims-TS);
Two tuning modes:
* **untuned** = each backend's default pick, 
* **autotuned** = each tuned at the exact batch size through
FlashInfer's autotuner.
Five representative models (Qwen3-30B, Qwen3-235B, Mixtral 8x7B,
DeepSeek-V3, Nemotron-3 30B) x T in {1, 4, 16, 64, 256, 1024, 4096,
16384} on Rubin (the full grid); the B200's reduced grid chosen for
performance measurements.

Every batch-invariant cell's output was bit-checked against the class's
default pick. Ratio = the best existing backend's time / the
batch-invariant time per regime geomean (> 1: batch-invariant faster),
the backend named with the cell count.

| part | regime | form A (pre-routed) untuned | form A (pre-routed)
autotuned | form B (from logits) untuned | form B (from logits)
autotuned |
|---|---|---|---|---|---|
| Rubin NVL4 (SM107, 212 SMs) | decode (T <= 16) | 0.97 (TRTLLM-Gen, 15)
| 0.97 (TRTLLM-Gen, 15) | 0.81 (TRTLLM-Gen, 15) | 0.82 (TRTLLM-Gen, 15)
|
| Rubin NVL4 (SM107, 212 SMs) | mid (64 .. 1024) | 1.18 (TRTLLM-Gen, 15)
| 1.00 (TRTLLM-Gen, 15) | 1.12 (TRTLLM-Gen, 15) | 0.94 (TRTLLM-Gen, 15)
|
| Rubin NVL4 (SM107, 212 SMs) | prefill (>= 4096) | 1.40 (TRTLLM-Gen,
10) | 1.13 (TRTLLM-Gen, 10) | 1.37 (TRTLLM-Gen, 10) | 1.10 (TRTLLM-Gen,
10) |
| Rubin NVL4 (SM107, 212 SMs) | all | 1.14 (TRTLLM-Gen, 40) | 1.02
(TRTLLM-Gen, 40) | 1.04 (TRTLLM-Gen, 40) | 0.93 (TRTLLM-Gen, 40) |
| B200 (SM100, 148 SMs) | decode (T <= 16) | 0.96 (TRTLLM-Gen, 15) |
0.96 (TRTLLM-Gen, 9) | 0.86 (TRTLLM-Gen, 9) | 0.86 (TRTLLM-Gen, 9) |
| B200 (SM100, 148 SMs) | mid (64 .. 1024) | 1.09 (TRTLLM-Gen, 15) |
0.96 (prims-TS, 9) | 1.12 (TRTLLM-Gen, 9) | 0.93 (TRTLLM-Gen, 9) |
| B200 (SM100, 148 SMs) | prefill (>= 4096) | 0.96 (prims-TS, 10) | 0.91
(prims-TS, 6) | 1.02 (prims-TS, 6) | 0.88 (prims-TS, 6) |
| B200 (SM100, 148 SMs) | all | 1.06 (TRTLLM-Gen, 40) | 0.95 (prims-TS,
24) | 1.05 (TRTLLM-Gen, 24) | 0.89 (prims-TS, 24) |

**Reading.** 
* On Rubin, prefill and middle regimes are at or above the bar vs.
TRTLLM-Gen, the only supported backend. Decode regime loses by up to 19%
on Rubin.
* On B200, loses by around 10-20% to the better of TRTLLM-Gen and Prims
TS in each case.

Fusion opportunities are remained for future exploration which may close
the performance gap a bit further

**Attribution.** The kernels of this backend took optimization ideas
from FlashInfer's other MoE backends, each adopted as a placement of the
class's dataflow (the same bits, placed as those kernels place theirs):
the swapped-AB decode records as ranked members of the dispatcher's
space follow Prims-TS (the open counterpart of TRTLLM-Gen's MoE GEMMs:
its swap-AB low-latency templates and its tile-N ladder from the rows
per expert) and TRTLLM-Gen's fp8 per-tensor decode tactics; the fused
activation and e4m3 requantisation at the static per-tensor multiplier
in GEMM1's epilogue follows Prims-TS's fused activation and TRTLLM-Gen's
fp8 per-tensor contract, whose surface this backend mirrors; the PDL
wait / trigger placement and the launch's tile bound on the persistent
grid follow Prims-TS and TRTLLM-Gen.

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

## 🔍 Related Issues

<!-- Link any related issues here -->
#9009

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

* **New Features**
* Added opt-in batch-invariant per-tensor FP8 support for MoE on
supported hardware, including weight preparation, activation
quantization, routing, and output combination.
* Added grouped and swapped FP8 execution, automatic tactic selection,
and optional intermediate outputs.
* **Bug Fixes**
* Improved NaN handling in reference calculations and support for
zero-row grouped GEMM operations.
* **Documentation**
* Expanded guidance on supported activations, hardware, and execution
constraints, including finalization and expert-parallel limitations.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [b5b0461](https://github.com/flashinfer-ai/flashinfer/commit/b5b0461413aae3415c84fc35cb09d2e6effee98b)

- **作者**: Jonathan Dierksen
- **时间**: 2026-11-16T17:17:58Z
- **提交信息**: test: cut full-suite pytest collection time (#9424)

<!-- .github/pull_request_template.md -->

## 📌 Description

The sharding runner collects all of `tests/` (~208k nodes) once before
it plans batches. On Lustre-backed GPU nodes that one pass is slow, and
most of the time went to work that a collection-only run doesn't need.
This PR removes five such costs. The set of collected node IDs is
unchanged.

**Measured**: one 8× H100 node, `flashinfer-ci-cu129:20261106` image,
tree on Lustre. Each cold copy was made on another host, so the compute
node starts with an empty `__pycache__` and page cache, as a fresh CI
checkout does. Collection used the runner's flags.

| Full `tests/` collection (208,537 nodes) | Before | After |
|---|---|---|
| Cold (fresh copy, empty JIT cache), two runs each | 562.9s / 562.5s |
93.0s / 92.7s |
| Warm (`__pycache__` and JIT cache populated) | 85.8s | 40–47s |

The cold "after" runs predate change 3. The warm figure includes it.

**Measured in internal CI**: the plan jobs of a full-suite run of this
PR, compared with recent full-suite runs of the regular matrix. Each
value is the time from the runner's `state=collecting` line to its
`Collected nodes:` line, so Slurm queueing and environment setup are
excluded. Each column is a single run.

| Plan job | This PR (209k nodes) | release-v0.7.5 (208k) |
release-v0.7.4 (201k) | Earlier PR full run (206k) |
|---|---|---|---|---|
| H100 cu129 / cu130 | **57s / 57s** | 1428s / 1210s | 1403s / 1219s | —
|
| B200, 3 CUDA versions | **64–65s** | 216–231s | 211–230s | 213–248s |
| GB200, 3 CUDA versions | **62–65s** | 299–311s | 299–311s | 292–334s |
| GB300, 3 CUDA versions | **63–65s** | 294–312s | 288–303s | 295–324s |
| VR NVL72 cu134 | **47s** | 195s | 189s | 191s |

Nightly runs collect the `--full` matrix (about 515k nodes) and
currently spend 207–383s per Blackwell plan job and 21–25 minutes per
H100 plan job.

**Changes**

1. **`tests/mamba/conftest.py`**: return early from the
`checkpointing_ssu` JIT prewarm under `--collect-only`. With an empty
JIT cache, the planning pass compiled 57 kernels (about 410s) even
though it runs no tests. `tests/attention/conftest.py` already skips its
prebuild for `--collect-only`. The hook now also runs `trylast`, so it
counts only the nodes a batch will run, after `-k`/`-m` and the sharding
plugin's `--flashinfer-node-file` have deselected the rest. Before, any
batch of `test_checkpointing_ssu.py`, even a single test, counted the
whole file and prewarmed.
2. **`scripts/test_sharding/runner.py`**: collect with `--assert=plain`.
Collection runs no asserts, and rewriting every test module cost about
44s cold (137s vs 93s). Worker batches still rewrite the files they
execute.
3. **`scripts/test_sharding/pytest_plugin.py`**: resolve each source
file once. `pytest_collection_modifyitems` called `Path.resolve()` twice
per item, about 417k calls, which took about 41s on Lustre. This hook's
time went from 38.9s to 8.2s, and the `--flashinfer-collection-json`
output is byte-identical.
4. **`tests/moe/test_b12x_fused_moe.py`**: borrower discovery parsed all
384 files under `flashinfer/fused_moe` (~0.5M lines) at import to find
the four that contain `_dense_cls`. It now checks for that substring
before parsing (about 6s saved).
5. **`tests/infra/test_helpers/parametrize.py`**:
`pairwise_product_cases` rebuilt each candidate's pair set on every
greedy step. It now builds each set once (about 2s saved across 62
calls). It scans candidates in the same order with the same
tie-breaking, so it selects the same regular cases.

**Out of scope** (noted for follow-ups):
- Each batch's pytest process costs about 6s before its first test on an
8-GPU node. `torch.cuda.init()` is about 2.5s of that, triggered during
collection by `torch.cuda` calls in conftest hooks and module-level
`skipif`s.
- Importing `tests/comm/test_allreduce_unified_api.py` initializes MPI.
Under a plain `srun` with a PMIx environment, MPICH aborts the pytest
process (exit 16, no output) partway through collection.

## 🔍 Related Issues

None.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues. (Ran on the changed files.)

## 🧪 Tests

- [ ] Tests have been added or updated as needed. (No new tests:
behavior is unchanged, and the node-ID comparison below is the check.)
- [x] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).

Suggested CI test targets: `tests/test_sharding
tests/moe/test_b12x_fused_moe.py tests/mamba`

**Validation**
- Full `tests/` collection before and after (x86 + RTX 3090, CI image):
all 208,747 node IDs are byte-identical, which covers the
`pairwise_product_cases` change.
- The runner's collection JSON on the H100 node is byte-identical before
and after the plugin change.
- `tests/test_sharding/`: 315 passed. `test_pytest_plugin.py` and
`test_runner_cli.py` were rerun on the H100 node after change 3 (79
passed).
- `tests/moe/test_b12x_fused_moe.py -k borrow`: 5 passed.
- `pytest --collect-only tests/mamba/` no longer logs `Building JIT
module`.

## Reviewer Notes

- `--assert=plain` affects only the runner's collection subprocess.
Worker batches keep normal assertion rewriting.
- With a cold JIT cache, the `checkpointing_ssu` prewarm (57 modules,
about 410s on an 8× H100 node) now runs in the first worker batch of
`test_checkpointing_ssu.py` with at least 8 selected nodes, rather than
in the planning pass. That stays well inside the default 2-hour unit
timeout. Concurrent batches of the file take the per-module build lock,
so they wait for a module rather than compile it twice. CI jobs usually
start from a seeded compile cache, so the cold case should be rare.
- The CI table above covers the aarch64 (GB200/GB300) plan jobs as well
as x86.

Developed with AI assistance (Claude Code). I reviewed and validated the
changes.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Tests**
* Improved test collection and sharding workflows, including more
efficient path handling and support for collect-only runs without
triggering prewarm.
  * Streamlined test-case generation and source-file scanning.
* Collection now uses plain assertions; worker test execution behavior
remains unchanged.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [cee7f82](https://github.com/flashinfer-ai/flashinfer/commit/cee7f82735737a173757cd97b46164d9e168ca1a)

- **作者**: garry569
- **时间**: 2026-11-16T15:55:08Z
- **提交信息**: feat(gemm): fuse gated activation into masked grouped GEMM epilogue (#7850)

## 📌 Description

Adds an optional gated-activation (SwiGLU) epilogue to the SM100/SM103
CuTe DSL masked grouped GEMM (`grouped_gemm_nt_masked`), so MoE GEMM1
can write the activated `(m, n/2, l)` tensor directly instead of a
full-width `(m, n, l)` gate/up tensor followed by a separate activation
kernel.

New optional arguments (all default to the current behavior; the default
kernel is unchanged):

| Argument | Meaning |
|---|---|
| `activation_type=ActivationType.Swiglu` | Enable the fused epilogue.
Other activation types raise `NotImplementedError`. |
| `swiglu_alpha`, `swiglu_beta`, `swiglu_limit` | Same scalars and
validation (`validate_cute_dsl_moe_swiglu_config`) as the existing CuTe
DSL fused MoE. |
| `alpha_up` | Optional `float32 (l,)` scale for the up projection when
gate and up weights have different global scales. Defaults to `alpha`. |
| `a_per_token_scale` | Optional `float32 (l, m)` per-row scale of `A`,
applied before the activation (per-token activation quantization). |

Each output element is

```
gate = min(alpha    * s * acc_gate, limit)
up   = clamp(alpha_up * s * acc_up, -limit, limit)
out  = gate * sigmoid(swiglu_alpha * gate) * (up + swiglu_beta)
```

With the defaults (`1.0, 0.0, FLT_MAX`) this is plain SiLU-and-mul; with
`(1.702, 1.0, 7.0)` it matches the existing `swigluoai` semantics.

Weight layout: `B`/`SFB` rows are interleaved in 64-row blocks with the
up projection first (`[up_0:64, gate_0:64, up_64:128, ...]`), the same
granularity as the existing blockscaled act-fusion kernel, so each
epilogue subtile holds matching gate/up columns.

Constraints (checked on the host, unsupported combinations raise):
`mma_tiler_mn` `(128, 128)` or `(128, 256)`, `n` a multiple of
`mma_tiler_mn[1]`, no combine fusion / `is_swap_ab` / `dst_signals`;
SM107 rejects the new arguments explicitly.

## 🔍 Related Issues

Follow-up: #7851 adds NVFP4 output quantization in the same epilogue
(stacked on this PR), so GEMM1 can produce the GEMM2 input directly.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] `ruff format` / `ruff check` (0.12.8) and `mypy` (1.17.1) pass on
the changed files.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing.

New `tests/gemm/test_grouped_gemm_masked_fused_epilogue.py` (B300 /
SM103, CUDA 13, cutlass-dsl 4.8.1):

- 64 cases against a PyTorch reference: `l`, `m`, `n`, `k`, both tilers,
default and clamped SwiGLU, shared / separate up alpha, with / without
per-token scale, partial `masked_m`.
- Invalid-argument tests (unsupported activation, swap-AB, 2-CTA tiler,
FP8 output, negative limit, wrong per-token scale shape, `alpha_up`
without activation, full-width output).
- Regression: `tests/gemm/test_cute_dsl_blockscaled_gemm.py` 258 passed,
128 xfailed (pre-existing `l=1` xfails).

Suggested CI test targets:
`tests/gemm/test_grouped_gemm_masked_fused_epilogue.py
tests/gemm/test_cute_dsl_blockscaled_gemm.py`

## 📊 Benchmark

B300 (SM103), single GPU, CUDA graph, median of 10 replays x 20
iterations. MoE GEMM1 decode shape: 16 local experts, `k = 6144`, `n = 2
x 3072`, NVFP4 inputs, capacity `8 x T` rows per expert, `T/4` valid
rows per expert. Happy to add the benchmark script under `benchmarks/`
if useful.

| tokens/rank | rows/expert | GEMM1 only, full-width BF16 | GEMM1 +
fused SwiGLU, BF16 | GEMM1 +
`silu_and_mul_scaled_nvfp4_experts_quantize` | fused SwiGLU +
`scaled_fp4_grouped_quantize` | speedup |
|---:|---:|---:|---:|---:|---:|---:|
| 32 | 8 | 64.2 us | 62.4 us | 68.6 us | 66.1 us | 3.6% |
| 128 | 32 | 64.2 us | 62.6 us | 69.4 us | 67.0 us | 3.5% |
| 256 | 64 | 64.1 us | 62.5 us | 70.3 us | 67.5 us | 4.0% |
| 512 | 128 | 63.9 us | 62.8 us | 73.0 us | 69.2 us | 5.2% |

- The fused epilogue is not slower than the plain full-width GEMM (it
writes half the output), so the activation becomes free.
- In a GEMM1 -> NVFP4 GEMM2 pipeline the remaining cost is the separate
quantization; #7851 fuses that as well.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added optional fused SwiGLU activation to masked grouped GEMM on
supported Blackwell GPUs.
* Added configurable SwiGLU parameters, separate up-projection scaling,
and per-token input scaling.
* SwiGLU produces output with half the usual column width and requires
interleaved up/gate projection data.
* **Compatibility**
* SwiGLU supports specific tile sizes and cannot be combined with
combine fusion or swapped operands.
* Unsupported activation and scaling combinations are rejected; the new
options are unavailable on Rubin GPUs.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: garry569 <324435785+garry569@users.noreply.github.com>

### [cd2d2c8](https://github.com/flashinfer-ai/flashinfer/commit/cd2d2c8e264fc56b9be30565cb150521dda4bdfb)

- **作者**: CarstyYou
- **时间**: 2026-11-16T13:56:42Z
- **提交信息**: feat(moe): optimize SM12x gather and add low-parallelism SplitK FC1 (#9312)

<!-- .github/pull_request_template.md -->

## 📌 Description

Improve the existing SM12x FP8 and MXFP8×MXFP4 MoE paths, and add a
guarded SplitK2 FC1 implementation for low M/N parallelism.

This reuses `cutedsl_fused_moe_sm12x`: the PR includes the
gather/short-K and FP8 improvements, SplitK integration, and a
test-fixture compatibility fix, rebased onto `upstream/main` at
`71945d4fa`.

| Area | Changes |
| --- | --- |
| FC1 inputs | Token-major activation/SF gather through `token_map`,
including BM8, instead of replicating inputs across routed slots. |
| Short-K paths | Existing branch improvements to FC2 ping-pong
scheduling and FP8 data movement. |
| MXFP8×MXFP4 FC1 | Paired BN32/BK128/S2 SplitK2 kernel plus a separate
reduce–activation–BF16–Q1 kernel, with private per-call scratch. |
| Dispatch | `split_k=None` uses conservative metadata/parallelism
guards; `1` retains the existing path and `2` forces SplitK.
Explicit/tuned tactics and PDL take precedence over automatic selection.
|
| DSL compatibility | Keep Boolean storage conversion local to each
staged copy call, avoiding cached i8 values escaping between regions
with DSL 4.8. |

The unified runner's PDL default is unchanged: automatic SplitK is
eligible only when PDL is disabled and all guards pass. NVFP4 is not
modified.

**Ready for review:** fresh revision-matched before/after
whole-local-MoE measurements are reported below, separately for MXFP8 x
MXFP4 and FP8 x FP8.

## 📊 Performance results (revision-matched)

| Terminology | Meaning |
| --- | --- |
| Local-MoE | Single-rank Mixture-of-Experts expert layer |
| PDL | Programmatic Dependent Launch, controlled by `enable_pdl` |
| FC1 / FC2 | First / second expert projections |
| Act / Q1 | Gated activation / runtime quantization of its intermediate
output |
| MAD | Median absolute deviation of batch medians |
| TP / PP | Tensor parallelism / pipeline parallelism |

| Decision summary | Scope |
| --- | --- |
| MXFP8 x MXFP4, 8192 tokens: 13.57% lower latency | Complete local-MoE,
default dispatch and PDL request |
| FP8 x FP8, 8192 tokens: 11.12% lower latency | Separate
precision/activation pair; not a cross-precision ranking |
| All seven registered pairs cleared their 2.00% detection threshold |
Observations for the listed synthetic cases, not a general
model-performance claim |

| Setup / protocol | Value |
| --- | --- |
| Compared revisions | PR head `8650e0ce9` against its upstream rebase
baseline `71945d4fa`, not moving latest main |
| Hardware / software | RTX PRO 6000 Blackwell Server Edition, SM120 /
188 streaming multiprocessors; CUDA 13.0, Torch 2.11.0+cu130, CUTLASS
DSL 4.8.0 |
| Workload | Single-rank synthetic local MoE (Mixture of Experts):
hidden=3584, local intermediate=384, experts=896, top-k=16, seed=42; not
a full model or request |
| Activation | MXFP8 x MXFP4: SiTU(4,25); FP8 x FP8: SwiGLU without
clamp |
| Timed boundary | Complete public MoELayer CUDA Graph replay: route
metadata, runtime activation quantization, FC1/Act/Q1, required clears,
FC2/finalize. Prepared weights, top-k input generation, just-in-time
compilation and graph capture excluded |
| Sampling / cache | 20 graph warmups per arm; 12 alternating AB/BA
rounds with 10 replays per arm, plus two A/A rounds. Each arm batch has
three context warmups then a 256 MiB flush and synchronization outside
the CUDA Event window; not every replay is cold-cache |
| Aggregation / detector | Median of batch medians; detector=max(2%,
each arm's relative 2 MAD, A/A relative differences). All samples
retained; this is not a confidence interval |
| Clock admission | Requested graphics-clock lock 2257 MHz; sampled
`clocks.sm` must be within 2235±15 MHz and span at most 15 MHz per pair.
Memory clock 12481 MHz; permitted reason bits 0x404 may vary. Not a
max-boost or unthrottled claim |
| 16K capacity | Both revisions use
`ExecutionConfig.tune_max_num_tokens=16384` for the 16K case; all
smaller cases retain the 8192 default. No tactic was forced |

### MXFP8 x MXFP4 - whole local-MoE latency

| Tokens | PDL | Baseline (us) | PR (us) | Latency reduction | Result |
| ---: | --- | ---: | ---: | ---: | --- |
| 8192 | default | 3699.392 | 3197.488 | 13.57% | faster |
| 1 | false | 51.512 | 44.864 | 12.91% | faster |
| 1 | default | 49.232 | 46.648 | 5.25% | faster |
| 4096 | default | 2263.360 | 2048.328 | 9.50% | faster |
| 16384 | default | 6152.856 | 5917.776 | 3.82% | faster |

### FP8 x FP8 - whole local-MoE latency

| Tokens | PDL | Baseline (us) | PR (us) | Latency reduction | Result |
| ---: | --- | ---: | ---: | ---: | --- |
| 8192 | default | 4302.512 | 3824.112 | 11.12% | faster |
| 1 | default | 73.640 | 62.504 | 15.12% | faster |

Latency reduction is `(baseline - PR) / baseline`; the PDL column is the
public `enable_pdl` request, where `default` means `None` (observed as
enabled in both arms) and `false` means explicitly disabled.

| Supported observation / limitation | Boundary |
| --- | --- |
| Each row measures the complete PR bundle, including all selected
launches and workspace traffic | Do not attribute the whole-row delta to
gather, FC2, or SplitK alone, or combine independently paired rows into
a cumulative gain |
| Only MXFP8 x MXFP4 T=1 with PDL disabled actually selected automatic
SplitK | Its complete boundary includes both SplitK and reduce-Act-Q1
launches plus scratch traffic; default-PDL rows did not select SplitK |
| Each arm passed eager/graph numerical checks and post-timing checks,
with matching prepared-input bytes and admitted actual CuTe native
images | Large-token independent Torch references sampled four tokens;
T=1 used the full token, and full arm outputs were compared before/after
timing. This is not full-project CI or a new sanitizer qualification |
| No row is a full model, distributed TP/PP execution, or a B12x/W4A16
comparison | Do not extrapolate to unmeasured shapes, phases or
individual optimization mechanisms |

<details>
<summary>Exact-revision evidence provenance</summary>

These are fresh before/after measurements of this PR, not the archived
pre-port stage comparisons. Tables were generated by
`summarize_fi_revision.py` from complete paired raw records; each
primary includes source/input/native/dispatch identity, numerical
checks, all replay samples and telemetry, with the exact inputs and
selected images retained in the development archive.

| Case | Primary observations SHA256 |
| --- | --- |
| `mx8192_default` |
`16704becad59bf960aff4360bc86aa4bb2d67339219be77df415873f0d69e572` |
| `fp88192_default` |
`455a61a97800343a349f6ae01dc545896542436b7a5e798e986573492d146d57` |
| `mx1_no_pdl` |
`741884950fe99df469bde00a6c56c3032ca0e7152e696794ce3bfcfe74167a62` |
| `mx1_default` |
`176edfab2a650d6f651aeb057150d78056c502efeae56df006cfcd2ce2cd3256` |
| `fp81_default` |
`54f4e982ae824e87a7b4edabc9e97d2f8456efa62dea2d7f53e956df2b851a0e` |
| `mx4096_default` |
`11da69ff21109f5d30d7944485c28cc5b3d05fe47fc1f583b163a29dfda8b5a0` |
| `mx16384_default` |
`a244cf0967cb7d1a81744bcb223a0e08b5535d5c3a10042a0451569ffccd0e03` |

</details>

## 🔍 Related Issues

Follow-up to #4720. Separate from the NVFP4 work in #6510.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

Changed-file checks passed with `pre-commit run --files` on all 22
PR-modified files after rebase, and again on the final fixture fix.
Whole-tree `--all-files` and hook installation were not performed in
this cycle; their boxes above remain unchecked.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: targeted SM12x MoE test files cover the affected paths;
full-project CI is not requested.

Latest local validation used an RTX PRO 6000 Blackwell Server Edition
(SM120), CUDA 13.0, Torch 2.11.0+cu130 and CUTLASS DSL 4.8.0, with the
actual rebased FlashInfer implementation (no candidate substitution).
The validated source content is committed at `8650e0ce9`.

| Latest validation | Result |
| --- | --- |
| `tests/moe/test_cute_dsl_sm12x_fp8.py` | 45 passed |
| `tests/moe/test_cute_dsl_sm12x_mxfp8_mxfp4.py` | 114 passed |
| `tests/moe/test_sm12x_fp8_q0_route.py` | 34 passed |
| `tests/moe/test_sm12x_mxfp8_q0_route.py` | 25 passed |
| `tests/moe/test_unified_moe_sm12x_fp8.py` | 12 passed |
| `tests/moe/test_unified_moe_sm12x_mxfp8_mxfp4.py` | 18 passed |
| Combined targeted files | 248 passed, 0 failures/errors/skips |
| Generated SplitK/reduce native | Four activation variants; LOCAL=0 and
no LDL/STL instructions. SplitK has a 16-byte reserved-unused frame, not
zero stack usage. |

Coverage includes FP8/MX internal operations, Q0 and unified runners,
independent SplitK partial references, BF16/Q1 and scale outputs,
activation parameters, empty/padded routing, caller-owned outputs,
automatic/forced/tuned dispatch, and eager/CUDA Graph execution.
Upstream byte-scale poison and uint8/int32 cache-transition tests are
preserved: the legacy routed fixture returns a byte view, while the
gather reference explicitly retains its packed Int32 view. No kernel,
tolerance or assertion was changed for that fixture correction.

Equivalent test targets:

```bash
MOE_AUTOTUNE=0 pytest -q -x \
  tests/moe/test_cute_dsl_sm12x_fp8.py \
  tests/moe/test_cute_dsl_sm12x_mxfp8_mxfp4.py \
  tests/moe/test_sm12x_fp8_q0_route.py \
  tests/moe/test_sm12x_mxfp8_q0_route.py \
  tests/moe/test_unified_moe_sm12x_fp8.py \
  tests/moe/test_unified_moe_sm12x_mxfp8_mxfp4.py
```

All six listed files were freshly rerun after the rebase and fixture
correction. The full project suite and a new sanitizer run are not
claimed here; the full-suite checkbox remains unchecked. Fresh
performance measurements are reported above.

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/moe/test_cute_dsl_sm12x_fp8.py
tests/moe/test_cute_dsl_sm12x_mxfp8_mxfp4.py
tests/moe/test_sm12x_fp8_q0_route.py
tests/moe/test_sm12x_mxfp8_q0_route.py
tests/moe/test_unified_moe_sm12x_fp8.py
tests/moe/test_unified_moe_sm12x_mxfp8_mxfp4.py`

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

Please focus on source/output ownership across SplitK and reduction, the
token-major gather ABI, dispatch precedence, and preservation of PDL
behavior. The two kernel launches remain separate and use the same
stream; writable scratch is private to each invocation.

This PR is ready for review. The performance tables above compare this
exact revision with its upstream rebase baseline; they are fixed-case
whole-local-MoE observations, not full-model or isolated-optimization
claims.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added token-only routing and token-map gathering for SM12x FP8 and
MXFP8×MXFP4 MoE workflows, preserving quantized outputs and scales in
token order.
* Added optional Split-K execution for MXFP8×MXFP4 FC1, with automatic
selection for eligible workloads.
* Added ping-pong scheduling for MXFP8×MXFP4 FC2 finalization and
asynchronous copying for selected FP8 FC2 configurations.

* **Bug Fixes**
  * Improved support for strided inputs and singleton scale tensors.
  * Added validation for token maps and gather configurations.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [a2e3d1e](https://github.com/flashinfer-ai/flashinfer/commit/a2e3d1e7075edf57c87248c63f206c3a3b87a185)

- **作者**: Yang Xu
- **时间**: 2026-11-16T09:50:32Z
- **提交信息**: test: cover cuDNN D256 paged auto boundaries and replay (#9523)

<!-- .github/pull_request_template.md -->

## 📌 Description

Extend the existing SM100 paged-auto test harness with 36 D256 cases (18
boundary shapes, causal and noncausal). Cover the 16 Mi work floor,
query and KV limits, Q128 classification in mixed batches, batch limits,
GQA ratios, MHA rejection, and CPU/device metadata admission.

Every case checks actual public-wrapper dispatch, full FA2 O/LSE results
and independent FP64 boundary rows, then changes Q/K/V, poisons output
storage and checks CUDA-graph replay. Existing D128 cases use the same
helper. No production dispatch or kernel changes.

## 🔍 Related Issues

Extends the D128 regression from #9520 and complements the retained-plan
D256 regression in `test_cudnn_paged_gqa_auto.py`.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`. (Existing
worktree hook configuration.)
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.
Required changed-file hooks passed; no unrelated whole-tree formatting.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All targeted tests are passing.

SM100, actual PyTorch 2.11.0+cu130 and CUDA 13.4 compiler: full
maintained file **66 passed on cuDNN 9.24.0.43**; D256 control **36
passed on actual cuDNN 9.27.0.42**. Production paged-auto/prefill
sources are unchanged between the pinned runtime snapshot and this PR
base. Changed-file hooks and `git diff --check` passed.
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
      Reason: Not required; only the named test file changes.

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust):
`tests/attention/test_cudnn_paged_auto_boundaries.py`

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

AI-assisted implementation and validation using Codex. This is SM100
coverage; an H100 CI skip does not establish numerical qualification.
The FP64 oracle samples boundary rows, while FA2 checks every O/LSE
element. These direct API tests do not claim full serving E2E
acceptance.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Tests**
* Expanded validation of paged attention boundary conditions for D128
and D256, covering query and KV lengths, workload, head ratios, batch
sizes, and mixed requests.
* Added coverage for CPU and CUDA metadata and checks that run when the
relevant cuDNN mode is supported.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [7855d94](https://github.com/flashinfer-ai/flashinfer/commit/7855d941e6e6013e7462c9de928704a3c36ec71f)

- **作者**: Yang Xu
- **时间**: 2026-11-16T09:38:14Z
- **提交信息**: test: compare both cuDNN packed-query layouts to reference (#9522)

<!-- .github/pull_request_template.md -->

## 📌 Description

On A100 with cuDNN 9.24, the packed-query regression can fail its 1e-3
comparison between layouts even though both results satisfy the existing
reference check. Fixed-address direct FE executions also vary by one
BF16 step on 9.24 and 9.27; the same controls are stable on the tested
9.28 preview. This is consistent with the backend repeatability
limitation reported in NVIDIA/cudnn-frontend#1412.

Compare **both** packed and contiguous results to FA2 with the existing
O/LSE reference budgets, replacing the tighter cross-run output
comparison. Previously only the first result was compared to FA2. Keep
the existing cross-layout LSE assertion and both graph-cache population
orders. No production code changes.

## 🔍 Related Issues

Related: https://github.com/NVIDIA/cudnn-frontend/issues/1412. This test
change does not fix or close the backend determinism issue.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`. (Existing
shared worktree hook configuration.)
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.
Required changed-file hooks passed manually and at commit; no unrelated
whole-tree formatting.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All targeted tests are passing: 8 packed-query combinations on
A100, actual PyTorch 2.11.0+cu130 / cuDNN 9.24.0.43.

The original pairwise assertion failed in 5/16 saved-input trials; both
outputs passed an independent FP64 O/LSE reference every time. A private
negative control restores the incorrect packed-Q batch stride and the
maintained test fails (96/128 LSE elements differ). Changed-file
pre-commit and `git diff --check` passed.
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
      Reason: Not required; one test changes.

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/attention/test_cudnn_decode.py`

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

AI-assisted implementation and validation using Codex. Reference
tolerances are unchanged; the tighter pairwise output assertion is
deliberately removed. Both layouts now receive the same independent
numerical check. Passing this stride test does not establish backend
determinism.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Tests**
* Updated coverage to check packed and contiguous query layouts
independently against the reference implementation.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [44a0b33](https://github.com/flashinfer-ai/flashinfer/commit/44a0b33dfefbd33473cc36f9443275a6eb067bbe)

- **作者**: Perkz Zheng
- **时间**: 2026-11-16T09:10:33Z
- **提交信息**: perf(prims_ts): optimize NVFP4 decode conversion and scheduling (#9315)

## 📌 Description

Improve FP8-Q/NVFP4-KV decode with wide Swaps tiles, grouped Keeps
conversion,
and work-based split selection. D128/D256 Keeps converts K/V into FP8
SMEM;
D512 Swaps uses staged conversion and swizzled V scales. On native
SM107,
D256 Keeps retains packed rows in registers and releases raw SMEM before
conversion so loads can overlap conversion.

Conversion paths share row-scale and FP8-store helpers. Tasks stay in
the flat
module and use the standard TaskManager with one-CTA resource budgets.
Swaps correction uses one early identity check; Q48 fragment coverage
follows
query geometry. Explicit zero conversion depth selects the automatic
depth;
unsafe converter warp counts and undersized padded statistics storage
are
rejected. Wide direct-output tiles publish requested LSE, including
graph replay
and padded query rows. Existing output tolerances and explicit nonzero
conversion depths are
preserved.

The expanded full-grid split scoring and grouped-Keeps automatic
eligibility
are limited to NVFP4. Homogeneous FP8 retains the base dispatch scope,
including
the existing D128 FP16/BF16-output fixed multi-token, no-sinks grouping
gate.
Explicit supported configurations are unchanged.

This PR includes the wide-tile changes previously proposed in #7409 and
is
rebased directly onto main (`cfa0318a13`).

### Performance

Rubin SM107 and GB300, CUDA 13.4, CuTe DSL 4.8.1. Hq16/Hkv2, D256,
page128,
KV65536, FP8 Q/NVFP4 KV, BF16 output; Q1 dense and Q6 causal. Public
auto
dispatch including reduction, seeded inputs, CUDA graphs (best of ten
replays,
20 calls/replay, no L2 flush). Times are microseconds; the comparator is
main
`cfa0318a13` on the same GPU. The PR column was measured at
`e294aa18b3`;
the resource/LSE follow-up preserves default-path outputs bit-for-bit
and
changes matched Rubin timings by less than 0.1%.

| GPU | B | Q | Main µs | PR µs | Main / PR |
| --- | ---: | ---: | ---: | ---: | ---: |
| Rubin | 64 | 1 | 1924.96 | 316.32 | 6.09x |
| Rubin | 128 | 1 | 4440.33 | 629.44 | 7.05x |
| Rubin | 64 | 6 | 5648.03 | 321.80 | 17.55x |
| Rubin | 128 | 6 | 6922.52 | 638.00 | 10.85x |
| GB300 | 64 | 1 | 401.24 | 400.52 | 1.00x |
| GB300 | 128 | 1 | 824.83 | 770.44 | 1.07x |
| GB300 | 64 | 6 | 986.39 | 480.43 | 2.05x |
| GB300 | 128 | 6 | 1946.00 | 906.77 | 2.15x |

### #6979 B200 verification

For the remaining D512/GQA8/Q5–Q6 cases in
[#6979's
update](https://github.com/flashinfer-ai/flashinfer/issues/6979#issuecomment-6356261073),
all 32 measured configurations select Q64 and one **Q CTA** per KV head.
KV splits process disjoint KV ranges and are counted separately. The
cohort
covers heads 32/4 and 16/2, B8/B32, KV8K/KV32K, and page32/page64.

B200 (148 SMs), CUDA 13.4, DSL 4.8.1; FP8 Q/NVFP4 KV, FP16 output,
causal
HND, uniform planned KV lengths, scale 1/sqrt(512). TRT FP8 uses the
exact
logical K/V dequantized from the NVFP4 inputs. Median of 50 CUPTI
CUDA-graph
samples after 10 warmups, with L2 flushed before each sample; attention
and
reduction are included. Kernel source is `cf896fa52a`; the subsequent
change
only adds regression coverage. Representative B32/KV32K/Q6 results in
µs:

| TP | Page | Base `cfa0318a13` NVFP4 | PR NVFP4 | TRT FP8 |
| ---: | ---: | ---: | ---: | ---: |
| 1 | 32 | 1551.49 | 564.37 | 677.94 |
| 1 | 64 | 1153.22 | 528.53 | 675.94 |
| 2 | 32 | 718.59 | 300.05 | 339.79 |
| 2 | 64 | 594.35 | 282.53 | 336.59 |

Across the 29 strict-reference-passing Q5/Q6 cases, PR/TRT latency is
0.77–1.10x; matched passing base/PR speedups are 1.22–2.76x. NCU reports
zero local and shared spilling requests in three representative Q64
profiles
(direct and separate reduction, large and small grids), and in the
Q4/Q32
control. Q64 launches use 96 registers/thread and 640 threads/CTA.

The full D512 cohort including Q1/Q4 controls passes 61/64 strict FP16
comparisons on the PR and 60/64 on the base. The reference checks the
first
two requests per case; all outputs are checked for finiteness. The three
PR
failures also fail on the base at the same worst-error coordinates: TP2
B8/KV32K/page64/Q6, TP1 B32/KV8K/page32/Q6, and TP1 B32/KV8K/page64/Q5.
They are excluded from qualified timing claims, and no tolerance was
changed.
The new maintained D512/Q64/page64 Q5/Q6 cases exercise V-scale
swizzling,
partial/aligned output bands, LSE and graph replay; all 26 focused cases
pass
on B200.

Scope limits remain: the small cold-cache cases can be about 10% slower
than
TRT FP8. Q64 covers up to eight query tokens at GQA8; the Q9 control
still
uses two Q CTAs (526.30 µs versus TRT FP8 413.81 µs). H128 page32/page64
controls pass on both base and PR with identical query-grouping
policies,
confirming that the earlier page-size gate was already fixed upstream.

## 🔍 Related Issues

Related: #9311, #7409, #6979. SM107 staging ideas informed by #8322.
This changes the
Prims backend; it does not optimize TRT NVFP4 or claim to resolve every
#9311 shape.

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

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/attention/test_attention_ts_decode.py`

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

- Homogeneous FP8 dispatch scope is restored to the base. A B200
comparison
matches 1,806 supported FP8 configurations and 18 rejections; all 192
NVFP4
controls retain the previous PR choices. The scoped fix passes 225
maintained
decode checks and changed-file hooks. Six matched FP8 timings differ
from
  base `cfa0318a13` by less than 0.6%.
- Reviewed and cleaned with AI assistance. No new public tuning controls
or
  exact-batch compilation fields are introduced.
- The resource/LSE follow-up passes 187 maintained decode/statistics
checks on
Rubin. Its focused regression cohort has 24 cases: nine failed before
the
fixes and all pass afterward, including Q48/Q64/Q128 LSE reference
comparisons
and graph replay after clearing output buffers to NaN. Changed-file
hooks pass.
A fresh GB300 run of this follow-up was not completed because its
allocation
remained queued; the previous head's GB300 qualification is recorded
below.
- The preceding optimization head passed 170 maintained checks on each
GPU,
12 graph-replay boundary cohorts per GPU (48 request-level comparisons),
neighboring D128/D512 cases, and final-head smoke tests. Rubin also
passed
  page64 coverage and tensor-aware racecheck with zero hazards.
- On Rubin, correction ordering was compared in four interleaved
early/late rounds:
40 reference checks pass with bit-identical outputs. Early skipping
lowers
latency by up to 8%; the consolidated helper reproduces the winning
timings
and matches all ten saved outputs bit-for-bit on Rubin. The resource/LSE
follow-up additionally passes four interleaved before/after timing
rounds
(16 reference checks) with bit-identical default-path outputs. Targeted
attention CI is requested for the updated head; the full repository
suite
  has not been run locally.
- Removing the two-CTA residency policy has a tradeoff in forced Swaps
profiles: Rubin D256/Q48, B64/B128, KV65536, Hq16/Hkv2, page128, FP8 Q,
NVFP4 KV, BF16 output, five splits, raw/transformed ring depths 4/2
changes
from 914.48/1743.24 µs in the prior two-CTA control to 990.10/1893.79 µs
  with one CTA (8–9% slower). Default D256 Keeps timings are preserved.
- On Rubin, a separate strict FP16-output synthetic probe (B64/Q1,
Hq32/Hkv4, D256,
page64, KV8192) fails its tolerance on both base `cfa0318a13` and this
PR.
  Its numerical cause remains unresolved; no tolerance was relaxed. This
limitation is separate from the passing maintained suite and BF16
timings.
- D128 Keeps versus Swaps depends on query grouping and work per CTA;
the
capability table is not a performance ranking. Swaps also supplies D512
  coverage. D512 V-scale swizzling requires complete 1024-byte atoms and
  smaller page fragments retain the unswizzled path.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Expanded attention decode support for FP8 queries with NVFP4 key/value
caches, including BF16 output and head dimension 512 in supported
configurations.
* Added support for wider grouped-query configurations, additional paged
decode setups, and larger runtime page windows.
* **Performance**
* Improved decode performance for supported NVFP4 and large
grouped-query workloads, including on newer GPU architectures.
* Improved handling of selected large-query and split-reduction
workloads.
* **Documentation**
* Expanded guidance on supported decode configurations and scheduling
behavior.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Perkz Zheng <67892460+PerkzZheng@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [f5f03a9](https://github.com/flashinfer-ai/flashinfer/commit/f5f03a96e238f8ca4b583bc6c38162fc0c7fe842)

- **作者**: Yang Xu
- **时间**: 2026-11-16T09:08:28Z
- **提交信息**: test(attention): cover cuDNN paged auto boundaries and replay (#9520)

<!-- .github/pull_request_template.md -->

## 📌 Description

Add 30 numerical regression cases for the existing SM100 BF16 D128 paged
`backend="auto"` domain. The tests exercise real default dispatch at
work floors, short-query and mixed-batch boundaries, CPU/device length
metadata, 16K square prefill, and 32K KV prefixes. Causal cases inside
the domain must select cuDNN; outside-domain and noncausal controls must
retain FA2.

Every case uses packed projection Q views and shuffled KV pages. Full
output/LSE comparisons against FA2 are supplemented by independent FP64
checks at request and tile boundaries. CUDA graph replay changes Q/K/V
and poisons the output buffers before rechecking. Production dispatch is
unchanged.

Developed with AI assistance.

## 🔍 Related Issues

Release qualification follow-up to #9516; complements the D256
retained-capture coverage with D128 automatic-admission boundaries.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] Used the existing pre-commit installation.
- [x] Commit hooks ran on the new file.
- [x] `pre-commit run --files
tests/attention/test_cudnn_paged_auto_boundaries.py` passed.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added.
- [x] All 30 cases passed on SM100 with PyTorch 2.11.0+cu130 and actual
cuDNN 9.24.0.43; all 30 also passed with actual cuDNN 9.27.0.42. CUDA
compiler 13.4.

The independent FP64 oracle samples boundary rows; the FA2 comparison
checks every output and LSE element. These are consumer API tests, not
vLLM/SGLang serving E2E results.
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust):
`tests/attention/test_cudnn_paged_auto_boundaries.py`

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

No dispatch helpers or capability queries are mocked. Unsupported
architectures/runtimes skip explicitly. The exact current admission
assertions are intentional: changes to this domain should update the
corresponding coverage. CPU metadata and device metadata take their
normal public paths.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Tests**
* Added coverage for cuDNN selection at paged-auto workload boundaries
on supported Blackwell devices, including captured execution and output
comparisons against reference results.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [9930ccc](https://github.com/flashinfer-ai/flashinfer/commit/9930cccbc9198ae8b220274dc420996f473ffd58)

- **作者**: Yang Xu
- **时间**: 2026-11-16T09:03:50Z
- **提交信息**: test: cover cuDNN empty-request prefill across graph replay (#9519)

<!-- .github/pull_request_template.md -->

## 📌 Description

Empty requests can move to a different batch position while a CUDA graph
keeps the same query capacity. Add a 32-case cuDNN prefill regression
that updates device lengths and token offsets on replay, changes Q,
poisons outputs, and checks live O and LSE against an independent FP64
reference.

Coverage spans FP16/BF16, ragged/paged KV, MHA/GQA,
single-token/multi-token queries, and packed/padded LSE. On cuDNN <9.27,
the single-token GQA packed-LSE cases verify the existing actionable
rejection; the corresponding padded-LSE cases execute. On 9.27 those
packed cases execute too. No production behavior or tolerance changes.

Validation: actual PyTorch 2.11.0+cu130 with cuDNN 9.24.0.43: 32 passed
on SM100 (28 numerical eager/replay cases and 4 expected rejections);
the equivalent pre-commit probe also passed all 32 on H100 and L40S.
Actual cuDNN 9.27.0.42 on H100: all 32 numerical eager/replay cases
passed. Configured pre-commit and `git diff --check` passed. These are
direct FlashInfer API checks, not full vLLM/SGLang serving validation.

## 🔍 Related Issues

Related implementation: #7438 and #9351. No issue is closed by this
test-only change.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`. (Not
installed in the isolated worktree; invoked manually.)
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.
Changed-file hooks were run and passed; no unrelated whole-tree
formatting was requested.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All targeted tests are passing (local results above; focused CI:
H100 59 passed, CPU 10971 passed / 20 skipped, all AOT import and
provider lint jobs passed).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
      Reason: Not required: only the named regression-test file changes.

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust):
`tests/attention/test_cudnn_prefill_lse_layout.py`

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

AI-assisted implementation and validation using Codex. Existing cuDNN
<9.27 packed single-token GQA rejections remain explicit; numerical
coverage is not claimed for those four cases on 9.24.

### [b6f4e8d](https://github.com/flashinfer-ai/flashinfer/commit/b6f4e8db816364c873429f206d7a4816c0315912)

- **作者**: DylanChen-NV
- **时间**: 2026-11-16T08:19:06Z
- **提交信息**: [Perf] Optimize SM90 DOTS3 MLA sliding-window decode (#9511)

<!-- .github/pull_request_template.md -->
<!-- Suggested title: [Perf] Optimize SM90 DOTS3 MLA sliding-window
decode -->

## 📌 Description

This PR further optimizes [the SM90 DOTS3 MLA+sliding-window backend
merged in #6823](https://github.com/flashinfer-ai/flashinfer/pull/6823).
It improves the existing
`flashinfer.mla.batch_decode_with_kv_cache_mla_swa` implementation
without changing its public signature, workspace-size API, or precision
contract.

### Changes

- Derive each CTA's physical-page range from its query token's causal
window, rather than the request-wide union. W513 then needs at most nine
pages per CTA, including `s_q=4`.
- Fuse the FP32 split combine into a bounded cooperative grid for
M8-S3/S5/S9 and the new M16-S4 tactic when the complete grid fits the
queried device capacity. Keep the separate FP32 combine for
larger/unsupported cooperative launches; no spin counters or workspace
initialization are introduced.
- Improve M16 pipelines with six lookahead slices, register-resident
softmax row state, terminal-page cleanup/softmax overlap, and per-WG DSM
ready/ACK synchronization.
- Improve M32 softmax with half-warp row ownership and vectorized
loads/stores. Reuse the dead RoPE KV slice for scores, cache PV
rescaling factors, and add two lookahead slices to M32-S1.
- Extend the autotuner from six to seven qualified tactics, select
M16-S4 for the two 512-query-head-row shapes, and version its cache key.
Update the tactic documentation and tests.

The existing contract remains BF16 Q/KV/output, local Hq=64, Dq=1088,
Dv=1024, Page64, `window_left=512` (513 tokens including the current
token), local B in {1,2,4,8,16}, and `s_q` in {1,4}. Scores, PV
accumulators, and all split-reduction payloads/calculations remain FP32.
This does not introduce BF16 partial reduction.

### Performance

GPU: **NVIDIA H100 80GB HBM3, 132 SMs**; local Hq=64, Hkv=1, Dq=1088,
Dv=1024, W513/Page64, BF16 input/output and FP32 partial/reduction.
Measurements use the same GPU/process/inputs, preallocated
workspace/output, complete-op latency including split combine, and 12
balanced/interleaved rounds × 300 warm CUDA Graph replays.

**Fallback** is the original SGLang Triton MLA+SWA op,
`forward_dense_kvlora_swa_torch_fallback`, pinned at SGLang commit
`0dcac68751189e6d3417daafad52393bff01b0c9`. It is not a previous
FlashInfer release or the standalone benchmark's PyTorch reference.

**Latency reduction = (fallback latency − this PR's latency) / fallback
latency × 100%.** Across all 20 cases, latency is **21.7%–53.8% lower**
than fallback. The geometric-mean speedup is **1.542×**, corresponding
to **35.1% lower latency**; this aggregate is not an arithmetic average
of the row percentages.

B below is the **local, per-device batch size**. For attention-DP8, the
corresponding global batch is 8 × B; these are attention-op
measurements, not eight-device end-to-end throughput results. The tables
use the qualified optimized kernel's archived paired measurements before
publication-only formatting/comment/documentation cleanup; the Release
rebuild was checked separately under Tests.

#### s_q = 1

| Local B | KV length | Tactic | Fallback (µs) | This PR (µs) | Speedup
|
|---:|---:|---|---:|---:|---:|
| 1 | 4096 | M8-S9 | 19.249 | 9.268 | 2.08× |
| 1 | 4127 | M8-S9 | 19.281 | 8.902 | 2.17× |
| 2 | 4096 | M8-S5 | 20.043 | 11.451 | 1.75× |
| 2 | 4127 | M8-S5 | 19.922 | 11.768 | 1.69× |
| 4 | 4096 | M8-S3 | 22.618 | 15.081 | 1.50× |
| 4 | 4127 | M8-S3 | 22.647 | 15.020 | 1.51× |
| 8 | 4096 | M16-S4 | 25.654 | 17.173 | 1.49× |
| 8 | 4127 | M16-S4 | 25.774 | 17.872 | 1.44× |
| 16 | 4096 | M16-S2 | 38.477 | 21.899 | 1.76× |
| 16 | 4127 | M16-S2 | 38.572 | 22.986 | 1.68× |

#### s_q = 4

| Local B | KV length | Tactic | Fallback (µs) | This PR (µs) | Speedup
|
|---:|---:|---|---:|---:|---:|
| 1 | 4096 | M8-S3 | 21.051 | 14.463 | 1.46× |
| 1 | 4127 | M8-S3 | 21.144 | 14.334 | 1.48× |
| 2 | 4096 | M16-S4 | 22.551 | 15.662 | 1.44× |
| 2 | 4127 | M16-S4 | 22.511 | 16.185 | 1.39× |
| 4 | 4096 | M16-S2 | 26.385 | 20.020 | 1.32× |
| 4 | 4127 | M16-S2 | 26.497 | 20.757 | 1.28× |
| 8 | 4096 | M32-S2 | 36.692 | 26.318 | 1.39× |
| 8 | 4127 | M32-S2 | 36.620 | 27.424 | 1.34× |
| 16 | 4096 | M32-S1 | 62.248 | 41.366 | 1.50× |
| 16 | 4127 | M32-S1 | 62.292 | 42.018 | 1.48× |

To measure the current FlashInfer op and run its FP64 reference check:

```bash
FLASHINFER_CUDA_ARCH_LIST=9.0a FLASHINFER_JIT_DEBUG=0 python benchmarks/bench_mla_swa_sm90.py \
    --batch-sizes 1 2 4 8 16 --q-lens 1 4 --kv-len 4096 \
    --rounds 12 --replays 300 --refcheck --output results/mla_swa_4096.json
# Repeat with --kv-len 4127 and a different output filename.
```

This standalone command requires no SGLang installation or model
weights. Its `pytorch_reference_us` field is a gather/mask reference,
**not** the Triton fallback in the tables. The fallback comparison was
collected with the paired development harness
(`optimization_archive/iterations/20261029_table_driven_optimization/benchmark.py`
in the development archive), using the pinned SGLang fallback; that
harness is not part of this FlashInfer PR.

## 🔍 Related Issues

Follow-up to https://github.com/flashinfer-ai/flashinfer/pull/6823.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

Before the November 15 rebase, changed-file checks passed with the
repository's hooks: clang-format 19.1.1, Ruff, mypy, and the standard
file checks. Hooks were run with `pre-commit run --files <changed
files>`; the whole-repository checkbox above is intentionally not
claimed. These are historical results, not a fresh hook run against the
rebased head.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: Not requested; changes are confined to the SM90 MLA+SWA backend.

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/attention/test_mla_swa_sm90.py
tests/trace/test_mla_swa.py`

Targeted validation command:

```bash
FLASHINFER_CUDA_ARCH_LIST=9.0a FLASHINFER_JIT_DEBUG=0 pytest -q \
    tests/attention/test_mla_swa_sm90.py tests/trace/test_mla_swa.py
```

Historical GPU validation of the pre-rebase publication commit
`df6d7e550f04ea79775a3123bbd20169594504a8`, on H100 80GB HBM3 with
PyTorch 2.14.1+cu130 / CUDA 13.0:

- Release JIT compilation and loading passed; all 26 compiled source
identities matched that publication commit. The build has `-DNDEBUG` and
no `--device-debug`.
- **219 targeted tests passed**, covering all seven tactics and the
trace API. The existing FP64 accuracy thresholds are unchanged.
- All 20 default-dispatch benchmark cases passed independent FP64 checks
and produced bitwise-identical BF16 outputs to the sealed M18 module.
- Same-job publication-vs-M18 replay comparison: geometric-mean latency
change **+0.09%**. Nineteen of 20 rows differed by at most 0.23%;
`(B=16, s_q=4, KV=4127)` measured +2.15%. These publication checks are
separate from the fallback comparison above; no new speedup is claimed
from formatting or rebasing.

The all-tests checkbox remains open pending PR CI: the full repository
suite and full default AOT matrix were not rerun locally. Release
validation explicitly used `FLASHINFER_JIT_DEBUG=0`.

### November 15, 2026 rebase verification

- Rebased `dots3_swa_perf` onto upstream `main` at
`67d996c0a454cf975e91fd97dcce457b4a54b202`; the new head is
`1c0d86e2322eb2d8ac7a63c0adabdda2072498e5`.
- The rebase was conflict-free. `git range-diff` reports an identical
patch, and SHA-256 checks confirm that all 24 files changed by this PR
are byte-for-byte identical to the previously validated publication
tree. The CUTLASS and CCCL submodule revisions are unchanged as well.
- `git diff --check` and Python AST parsing of the three modified Python
files passed after rebasing.
- GPU tests, performance measurements, and pre-commit hooks were **not
rerun after this rebase**. The performance tables and 219-test result
above remain archived pre-rebase evidence, not fresh validation of the
updated dependency tree. Please run targeted CI on the final head:

```text
@flashinfer-bot run tests/attention/test_mla_swa_sm90.py tests/trace/test_mla_swa.py
```

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

- Please focus on cooperative-grid admission/fallback, the dead-RoPE
score alias lifetime, and the M16 per-WG DSM ready/ACK publication and
buffer-lifetime protocol.
- Cooperative fusion is not assumed to be legal based only on a
particular H100's SM count. Admission queries cooperative-launch support
and actual kernel occupancy; non-fitting grids retain the two-kernel
FP32 path.
- Masked NaN/Inf cache slots must remain safe, the KV cache must not be
modified, and the existing independent FP64 accuracy thresholds are
unchanged. Tests cover all seven tactics, short/empty inputs, graph
replay, non-default streams, and both fused/separate Global FP32 shapes.
- The public API and workspace capacity are unchanged; tactic selection
and the minimum opt-in shared-memory requirement are updated. No SM120
backend or SGLang code is changed.
- The reported speedups are attention-op measurements on H100 HBM3, not
model end-to-end speedups or a claim about other GPUs. No
clean-sanitizer or full default AOT-build result is claimed for this
follow-up.
- Development and release preparation were AI-assisted; validation
provenance and the remaining post-rebase CI requirement are stated
above.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added an additional SM90 attention tactic, expanding the available
options from six to seven.
* Added cooperative execution for eligible workloads, with existing
execution paths used when cooperative execution is unavailable.
* Updated default tactic selection and tuning to include the new option.
* **Bug Fixes**
* Updated SM90 shared-memory requirements and improved coverage for
correctness across tactics and context lengths.
* **Documentation**
  * Updated SM90 requirements, tactic options, and execution behavior.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [e8d1b85](https://github.com/flashinfer-ai/flashinfer/commit/e8d1b85de8591f85f69e3eb2129b73b3e2765d24)

- **作者**: Yang Xu
- **时间**: 2026-11-16T06:44:00Z
- **提交信息**: test(attention): restore cuDNN FP8 replay and independent numerics coverage (#9516)

<!-- .github/pull_request_template.md -->

## 📌 Description

Restore cuDNN attention coverage on the supported 9.24 runtime. The FP8
paged-prefill matrix was unconditionally xfailed, and its `return_lse`
and graph-capture parameters did not affect execution. Exercise output
and LSE against a Torch reference over the actual quantized/scaled
inputs, then verify changed-input and scale-only graph replays. Preserve
the historical xfail below 9.24.

Also replace the ragged wrapper's auto-backend reference, which can
select cuDNN too, with independent Torch numerics. Repair two legacy-FE
test doubles to hide native capability flags instead of changing a
version string that the implementation no longer checks. Production
dispatch and kernels are unchanged.

## 🔍 Related Issues

Found during cuDNN 9.24 multi-architecture attention qualification.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [x] Ran `pre-commit run --files` for the three changed test files; all
hooks passed.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] Changed-test validation: **605 passed, 288 skipped** on SM100 /
actual cuDNN 9.24.0.43 / CUDA 13.4. The skips are existing invalid `Sq >
Sk` parameter combinations. This runs both complete prefill/LSE files
and the two repaired legacy-capability cases.
- Earlier FP8 validation on a second SM100 device: 288 passed, 144
invalid-shape skips. The independent ragged reference also passed on
SM90 and SM89.
- Negative controls: corrupting cuDNN O leaves the old auto-reference
test green but makes both new reference cases fail; corrupting LSE or
suppressing graph replay leaves the old FP8 test green with its xfail
disabled but fails the new test. Fault injection is private validation,
not shipped code.
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/attention/test_cudnn_prefill.py
tests/attention/test_cudnn_prefill_lse_layout.py
tests/attention/test_cudnn_ragged_shape_override.py`

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

AI-assisted implementation and validation using Codex. This is test
hardening, with no performance claim. Older cuDNN and untested
architectures are not inferred qualified from the local results.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Tests**
* Expanded attention test coverage to compare cuDNN results and optional
log-sum-exp values with independent reference calculations, including
causal masking and packed layouts.
* Added CUDA Graph replay checks after changing inputs and scale values.
* Improved compatibility checks for bounded ragged inputs with older
frontends.
* Updated Blackwell test expectations to account for cuDNN version
differences.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [84d2ef1](https://github.com/flashinfer-ai/flashinfer/commit/84d2ef14cbf2d290cb4d41e5c865976c6af52caf)

- **作者**: Cindy Zhang
- **时间**: 2026-11-16T02:41:12Z
- **提交信息**: test: cover empty ranks in NVLink two-sided communication (#9491)

Extend the existing multi-rank dispatch/combine reference test with a
deterministic empty rank that serves peer experts. Check output shape
and reuse the existing numerical and workspace reuse checks for top-k 4
and 8.

Validation: Ruff lint/format, isolated parameter collection, and CPU
routing/numerical and reshape mutation checks passed. Real NVLink/MNNVL
multi-GPU execution remains pending.

AI-assisted implementation and review.

## 📌 Description
Extend test_dispatch_combine_matches_local_reference with deterministic
multi-GPU empty-rank coverage for the NVLink two-sided backend,
following #8821.

### Coverage gap
#8821 fixed a reshape error when local_num_tokens == 0 and added CPU
regression coverage with mocked communication.

The existing multi-GPU reference test samples token counts with
randint(1, max_tokens_per_rank + 1), which excludes empty ranks. In
addition to the CPU regression, a real multi-GPU case is needed to
verify that an empty rank still serves peer tokens and completes
dispatch/combine correctly.

### Changes
• Add an empty-rank scenario only for nvlink_two_sided, with top-k 4 and
8.
• Set rank 0’s local token count to zero while keeping peers non-empty.
  • Route peer tokens deterministically to rank 0’s experts.
• Check output shape and reuse the existing numerical-reference checks.
• Reuse the existing two-round loop to verify workspace and
communication-state reuse.

The original non-empty cases are preserved. No separate test function or
duplicate harness is added.

## 🔍 Related Issues
Regression coverage for #8821.

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
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets:
tests/moe_ep/test_moe_ep_communication_multirank.py

  torchrun --nproc_per_node=2 -m pytest \
    tests/moe_ep/test_moe_ep_communication_multirank.py \
    -k 'test_dispatch_combine_matches_local_reference and empty-rank' -v


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
Only the existing multi-rank test is modified.

### [cf8e7ab](https://github.com/flashinfer-ai/flashinfer/commit/cf8e7abbef38acc1cea864afb44239258814097a)

- **作者**: feih-nv
- **时间**: 2026-11-16T02:40:48Z
- **提交信息**: fix(quantization): zero-row launches return early and the launches are checked (fp4_quantize, mxfp8_quantize) (#9377)

<!-- .github/pull_request_template.md -->

## 📌 Description

Launcher fixes for the TRT-LLM block-scale quantization kernels
(`fp4_quantize`, `mxfp8_quantize`), from upstream TensorRT-LLM: the
launcher hunks of
[NVIDIA/TensorRT-LLM#19727](https://github.com/NVIDIA/TensorRT-LLM/pull/19727)
and
[NVIDIA/TensorRT-LLM#19988](https://github.com/NVIDIA/TensorRT-LLM/pull/19988).
The kernels themselves are main's. The CTA barrier before the PDL
trigger (NVIDIA/TensorRT-LLM#14668) was split out at review into #9445,
gated to SM103, because it guards one consumer (CUTLASS's SM103
block-scaled GEMM, NVIDIA/cutlass#3279) and costs every other
architecture.

- **Zero-sized inputs return early and launches are checked.**
`invokeFP4Quantization` and `invokeMxFP8Quantization` launched a
zero-sized grid for `m == 0`, which fails with `cudaErrorInvalidValue`
that the next CUDA call reports (`fp4_quantize(torch.empty(0, 64))`
followed by any kernel raised `CUDA error: invalid argument` on main;
the Python `mxfp8_quantize` entry already guards this since #8576). The
launchers return before configuring the launch when `b`, `m` or `n` is
0, and the three `cudaLaunchKernelEx` calls are wrapped in
`TLLM_CUDA_CHECK`.

Output is unchanged for non-empty inputs.

## 🔍 Related Issues


[NVIDIA/TensorRT-LLM#19727](https://github.com/NVIDIA/TensorRT-LLM/pull/19727),
[NVIDIA/TensorRT-LLM#19988](https://github.com/NVIDIA/TensorRT-LLM/pull/19988).

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

New: `test_fp4_quantize_zero_rows` (both scale-factor sizes, both
layouts); it fails on main with `CUDA error: invalid argument` and
passes here. `mxfp8_quantize` already returns before the launch for zero
rows on the Python side (#8576, covered by `test_mxfp8_quantize_empty`),
so no new test for it; the launcher's early return and launch check stay
for the other C++ callers. `SHAPES` gains `(8, 4800)`: 600 column
threads, so the 512-thread block finishes the row in a second pass of 88
threads and the scale-factor shuffle runs in a partially active warp; it
is checked against the PyTorch reference like the other shapes and also
exercises #9445's masks on SM103.

Run on B200 (CUDA 13.0 CI container): `tests/utils/test_fp4_quantize.py
-k "test_fp4_quantization or test_scale_swizzling or
test_e2m1_dequantization or zero_rows"` and
`tests/utils/test_fp8_quantize.py -k "test_mxfp8_quantize_torch or
zero_rows"`: 502 passed, 168 skipped (CuTe-DSL / CPU variants), at
FlashInfer `e3ebb9e7dd` + this commit.

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

Kernel code is untouched; no perf effect. Review on the earlier revision
measured its barrier at +14-19% on `fp4_quantize` and the partial mask
at +14-15% on MXFP8 (B200); both now live in #9445 behind an SM103 gate.

### [516f361](https://github.com/flashinfer-ai/flashinfer/commit/516f361b9994f84ec9b2eb673dc5c23cbf76ed5c)

- **作者**: Guangyun Han
- **时间**: 2026-11-16T01:48:24Z
- **提交信息**: feat(mla): fuse FP8 SM120 sparse prefill (#8747)

Fuses
- Q RoPE
- sparse MLA
- inverse output RoPE 
- and FP8 output quantization
for FP8-cache SM120 prefill. Mega is not proper name in this context, we
inherit the name from related project.

CuTe separates K loading, V loading, QK and softmax/PV roles, with
compile-time fused/unfused specialization.

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-11-17
**监控日期**: 2026-11-16
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4822
- **最后更新**: 2026-11-16T14:54:32Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-11-17
**监控日期**: 2026-11-16
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34927
- **最后更新**: 2026-11-17T02:29:20Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Sayak Paul

## AI分析总结

## huggingface/diffusers 昨日提交分析

### 1. 主要更新类型
**Bug 修复**：修复扩散模型中 Gemma 掩码（mask）调用与 Transformers 库的兼容性问题。

### 2. 关键变更点及与项目方向的关系
- 该提交针对的是模型集成层面的掩码调用逻辑错误，确保 diffusion Gemma 在配合 `transformers` 库时能正确传递和使用 attention mask。
- Diffusers 项目的核心目标是提供统一、灵活的扩散模型框架，支持多种架构与下游生态的无缝对接。此次修复直接服务于这一目标——保证与 HuggingFace Transformers 生态的**互操作性**，避免因接口差异导致的功能异常。
- 项目 README 明确其为 Apache 2.0 许可的 HuggingFace 官方项目，强调开放协作，此类小而精确的修复有助于维持代码库的高质量与跨库兼容。

### 3. 对项目的影响和潜在意义
- **短期**：解决用户在使用 Gemma 相关扩散配置时可能遇到的掩码维度或类型不匹配报错，提升开箱即用的体验。
- **长期**：随 Transformers 库持续演进，Diffusers 必须紧跟上游接口变化。此次修复体现了项目对生态同步的维护投入，有助于巩固两大库之间的稳定契约，降低集成风险。
- 这也是 PR 编号已达 #15306 的成熟社区，反映项目仍处于活跃迭代阶段。

### 4. 值得关注的技术点
- **掩码（mask）在扩散模型中的作用**：attention mask 影响去噪过程中的注意力计算，错误的掩码调用可能导致生成质量下降甚至崩溃，因此此类"小修复"实际影响不小。
- **跨库兼容性维护模式**：Diffusers 与 Transformers 之间存在隐式 API 依赖，需要持续的回归测试。值得关注后续是否补充了相应的集成测试用例。
- 提交信息规范（带 PR 链接），便于回溯问题来源。

### 5. 结合项目背景对发展的影响
基于 README 描述的项目定位——一个专业、规范（明确许可声明、版权归 HuggingFace）的扩散模型库——此类针对性 Bug 修复虽不引入新功能，但持续打磨**兼容性与稳定性**，正是开源框架走向成熟、被广泛信赖的关键路径。它与项目吸引用户、扩展支持模型架构的整体战略方向一致：只有底层集成稳固，用户才能专注于实验与创新。总体而言，这是一次以质量为导向的维护性提交，对项目发展起到支撑性而非驱动性作用。

## 详细提交记录

### [1dabc29](https://github.com/huggingface/diffusers/commit/1dabc292d8413638cf0666cca6d7a6c2c765befa)

- **作者**: Sayak Paul
- **时间**: 2026-11-16T09:16:03Z
- **提交信息**: fix diffusion gemma mask call for transformers. (#15306)

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-11-17
**监控日期**: 2026-11-16
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 431
- **最后更新**: 2026-11-12T08:10:11Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-11-17
**监控日期**: 2026-11-16
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13375
- **最后更新**: 2026-11-17T03:11:46Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Hong Zhang

## AI分析总结

## 昨日提交分析（第 1/1 批）

### 1. 主要更新类型
**Bug 修复**。该提交修复了 MiniMax-H3-Image 模型训练时未正确使用数据集 captions（图片描述文本）的问题，并移除了相关测试文件。

### 2. 关键变更点及其与项目整体方向的关系
- **修复训练数据流断裂**：训练管道在微调 MiniMax-H3-Image 时忽略了数据集中的 captions 字段，这意味着模型在没有文本条件引导的情况下进行训练，严重偏离了文生图/图生图任务的核心机制——文本与图像的对齐学习。
- **与项目方向的关联**：DiffSynth-Studio 的核心目标是提供一个统一、易用的扩散模型合成与微调框架，支持多种模型架构的低门槛训练。该修复直接关系到框架"正确训练支持的模型"这一基本承诺，确保用户使用 MiniMax-H3-Image 微调时能得到符合预期的结果，而非静默产生有缺陷的输出。
- **移除测试**：附带删除了测试代码，可能意味着相关测试为临时验证用例，或与修复方式调整后不再适用，属于清理性操作。

### 3. 对项目的影响和潜在意义
- **对用户的直接影响**：此前使用 MiniMax-H3-Image 进行微调的用户，其训练成果可能因缺少文本条件而显著劣于预期——表现为生成图像与 prompt 语义关联性差。修复后，用户重新训练可获得正常质量的模型。
- **项目信誉层面**：这类"静默失效"型 bug（不报错但结果错误）对开源框架的信任度伤害最大，及早修复避免了用户反复排查浪费时间，也减少了 issue 区的负面反馈。
- **潜在风险提示**：同一逻辑问题可能存在于其他模型的训练适配代码中，建议项目维护者系统性审查各模型训练入口的 caption 传参链路，防止类似 bug 复发。

### 4. 值得关注的技术点
- **数据集字段的管道透传**：训练脚本中 dataset → dataloader → loss 计算的字段传递链路是此类 bug 的高发区，尤其是当框架为多模型设计、每个模型有独立训练适配器时，字段命名不统一（caption/text/prompt）容易导致遗漏。
- **静默失败模式**：bug 未通过异常暴露，说明代码在缺失 caption 时有默认值兜底（如空字符串），这种防御性设计反而掩盖了逻辑错误。更好的做法是在训练配置校验阶段对必填字段缺失显式报错。
- **与 Style 的合作提交（Co-authored-by）**：表明该修复来自社区贡献者，反映出 DiffSynth-Studio 具有健康的外部贡献吸收机制。

### 5. 对项目发展的影响
结合 README 所述，DiffSynth-Studio 定位于一个支持多模型扩散合成与微调的工作室级工具包（已上架 PyPI、获 Trendshift 推荐）。本次提交虽小，但属于**关键基础设施的正确性维护**：一个支持多模型的训练框架，其价值高度依赖于"每个被声称支持的模型都能正确训练"。修复 MiniMax-H3-Image 的 caption 问题意味着该模型的微调功能从不可用状态恢复为可用，直接扩大了框架的有效支持范围。这类维护性修复累积起来，是项目从"功能堆砌"走向"生产可用"的必要过程，有助于增强社区对框架稳定性的信心，进而促进更多用户采用和贡献，形成良性发展循环。后续若能建立跨模型的训练正确性回归测试，将大幅提升此类问题的拦截效率。

## 详细提交记录

### [c05b58d](https://github.com/modelscope/DiffSynth-Studio/commit/c05b58d6a78cc9d2c1908b9a10c9941a59b9bcdf)

- **作者**: Hong Zhang
- **时间**: 2026-11-16T10:00:38Z
- **提交信息**: Fix MiniMax-H3-Image training not using dataset captions

* Fix MiniMax-H3-Image training not using dataset captions

* remove tests

---------

Co-authored-by: Style <Lbbb200434@outlook.com>

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-11-17
**监控日期**: 2026-11-16
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 38963
- **最后更新**: 2026-11-17T04:03:53Z

## 提交统计

- **昨日提交总数**: 74
- **提交者数量**: 46
- **主要提交者**: Haishuo.Kong, DarkSharpness, jiaqiang-dot-liu

## AI分析总结

# SGLang 昨日提交（共 74 条）综合分析

## 1. 主要更新类型
- **Bug 修复（约 30+ 条，占比最高）**：覆盖扩散模型、量化、多模态、PD 分离（disaggregation）、采样与调度等核心链路。
- **性能优化（约 13 条）**：集中在 AMD、NVIDIA、NPU 三大后端的 kernel 与调度调优。
- **功能新增（约 10 条）**：新模型支持、HiCache 数据面、调度策略、`--language-model-only` 等。
- **文档与 CI（约 17 条）**：diffusion 文档、cookbook、benchmark、Rust/NPU CI 缓存与基线配置。
- **重构（2 条）**：gateway 演进——先迁移用户至 sgl-router，再删除 sgl-model-gateway 旧源码。

## 2. 关键变更与项目方向
- **多硬件后端持续深耕**：AMD（gfx1250 all-reduce、GDN aiter 后端、mono-kernel 固定）、NVIDIA（KDA 扩展至 SM90、DeepGEMM 权重本地化、Blackwell/Rubin 混合 GDN+QSA+MoE 优化）、NPU（W4A8 分片、INT8 LightningIndexer、多流 draft、精度基线 OBS 对齐）全面推进，巩固跨平台推理引擎定位。
- **扩散模型生态走向成熟**：约 15 条提交涉及 ltx2、Anima、MOSS-Image、qwen-image-layered、H3 FP8 attention、端到端 profiling；配套文档密集补充动态 LoRA、Z-Image 输出尺寸对齐、cookbook 修正，说明该模块已从开发期进入易用性打磨与推广期。
- **PD 分离与大规模 serving 成熟化**：MegaMoE EP token 计数、attn_dp_size 校验、prefill delayer 同步、DeepSeek-v4.1 prefill CP 等修复，指向生产级 disaggregated serving 的稳定性打磨。
- **HiCache 生态成型**：新增后端数据面、凭据脱敏安全修复、write-back 用法 cookbook，缓存子系统趋于完整。

## 3. 对项目的影响与潜在意义
- gateway 两步重构统一到 sgl-router，降低路由层历史包袱与运维心智成本。
- 大量硬件 Perf 调优叠加 nightly benchmark（AgentX、MXFP4 等），性能回归监控体系增强，利于发布质量把控。
- 凭据脱敏、reasoning_tokens 用量统计修正等提升企业采用可信度；tqdm 多进程锁修复与对称工作区按注册顺序 finalize 消除了并发场景下的死锁与资源生命周期缺陷。
- `--language-model-only` 支持跳过多模态组件单独部署语言模型，降低显存与启动开销，利好轻量推理部署。
- 文档修正降低新用户上手扩散模型的门槛。

## 4. 值得关注的技术点
- **调度新策略**：fixed-batch bounded LPM policy 可能改变延迟/吞吐权衡。
- **megakernel-binding 视图抽象**：将混合模型的状态、缓存池、预填图、草稿步统一暴露，是 kernel 层与调度层解耦的关键设计，或成为自定义算子扩展接口。
- **混合 GDN + QSA + MoE 组合优化**：涉及投机解码 draft-step 与 MoE 路由协同，是吞吐提升前沿方向。
- **MoE 数值一致性**：swiglu_limit 在 CuTe DSL MoE runner 中生效。
- **回滚信号**：Blackwell/Rubin serving 优化被 Revert，提示激进融合优化仍有稳定性风险。
- 语法/采样 handoff 修复与 GLM 系列参数解析直接关系 tool-call 输出正确性，是 agentic 场景关键能力。
- 大量提交带 Claude/Cursor 协作署名，AI 辅助开发与合并流程已深度融入该仓库，其代码审查与质量管控机制值得留意。

## 5. 整体影响
SGLang 正处于**从"LLM 快速推理引擎"向"全模态、跨硬件、生产级推理平台"演进**的阶段：以密集修复加固 PD 分离与量化链路正确性，以 diffusion 与新模型（lfm3 Omni、Qwen3.5、kimi-k3、GLM-4.7、Gemma4）支撑生态广度，以硬件专项优化与 benchmark CI 守住"Fast" 承诺。短期风险来自大改动回滚，长期看 HiCache、router 统一与跨后端 kernel 沉淀将构成竞争壁垒。扩散模型与最新 NVIDIA 架构优化是最值得关注的两个增长点，项目已进入功能广度与工程质量并重的巩固期。

## 详细提交记录

### [01f9bbb](https://github.com/sgl-project/sglang/commit/01f9bbb0db847bc517b91ae92275fd15e71797e2)

- **作者**: jacky.cheng
- **时间**: 2026-11-16T23:48:11Z
- **提交信息**: [Chore] [AMD] mono-kernel: Pin sgl-amd-mono at a04ceab for Qwen3.5 FP8 (#50813)

### [da52ee2](https://github.com/sgl-project/sglang/commit/da52ee2cbf0b5ee083b97e015c5e528876c52f7f)

- **作者**: Tri Dao
- **时间**: 2026-11-16T23:46:21Z
- **提交信息**: [Fix] kimi-k3: Pass the EP-wide token count to MegaMoE under attention DP (#50838)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [ae3f39c](https://github.com/sgl-project/sglang/commit/ae3f39c3e9a1cee35b42706a9178c930d38dec1d)

- **作者**: Richard Wang
- **时间**: 2026-11-16T23:42:38Z
- **提交信息**: [Chore] codeowners: Update CODEOWNERS (#50865)

### [da05bde](https://github.com/sgl-project/sglang/commit/da05bdedc3cead4fb7331b21c0b3651cec1c25f0)

- **作者**: Yihao Wang
- **时间**: 2026-11-16T23:23:25Z
- **提交信息**: [Chore] diffusion: Fix stale comments and docstrings in serving, apps and CI scripts (#49838)

Signed-off-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [5dfa6c8](https://github.com/sgl-project/sglang/commit/5dfa6c8ab6ad2118ccb3a1f593ae917b4cfa2a30)

- **作者**: Sidhartha Reddy Potu
- **时间**: 2026-11-16T22:15:06Z
- **提交信息**: [Fix] muse-glimmer: Fix vision embedding order (#50855)

### [f6de13a](https://github.com/sgl-project/sglang/commit/f6de13a0c26697382a1bb7969e24ea59f089365e)

- **作者**: Khoa Pham
- **时间**: 2026-11-16T21:11:34Z
- **提交信息**: [Fix] dcp: Plan DCP attention metadata for GLM-4.7-Flash prefix hits (#50849)

### [f75136c](https://github.com/sgl-project/sglang/commit/f75136c949fd2b44533be4e8179ba586c782c1b6)

- **作者**: Nan Jiang
- **时间**: 2026-11-16T21:03:20Z
- **提交信息**: [Fix] moe: Apply the model's swiglu_limit in the CuTe DSL MoE runner (#50019)

Co-authored-by: Byron Hsu <byronhsu1230@gmail.com>

### [045c9fb](https://github.com/sgl-project/sglang/commit/045c9fbb6e58155086205ec004153b0a0a78d324)

- **作者**: Tri Dao
- **时间**: 2026-11-16T20:54:13Z
- **提交信息**: [Fix] mamba: Allow extra_buffer_lazy on a PD prefill worker (#50840)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [c2a7d10](https://github.com/sgl-project/sglang/commit/c2a7d10c5675007679b3c343847005698687daa8)

- **作者**: INBreezefall
- **时间**: 2026-11-16T20:19:30Z
- **提交信息**: [Fix] [NPU] quantization: Shard W4A8 MoE scale_bias by MoE TP rank (#40880)

Co-authored-by: inbreeze <majj8@chinatelecom.cn>
Co-authored-by: ronnie_zheng <zl19940307@163.com>
Co-authored-by: Артем Савкин <58187114+OrangeRedeng@users.noreply.github.com>

### [424fa3c](https://github.com/sgl-project/sglang/commit/424fa3c8b733030e719cc2cb94f4d9d0e4b10564)

- **作者**: Murthy L
- **时间**: 2026-11-16T18:10:44Z
- **提交信息**: [Fix] [XPU] diffusion: Copy flash-attention inputs under torch.compile (#46877)

Signed-off-by: Murthy L <murthy.l@intel.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [e6d9ff4](https://github.com/sgl-project/sglang/commit/e6d9ff4670a7f397f6c88ab8edff26125bdbc1a2)

- **作者**: Miles TsungWei Chin
- **时间**: 2026-11-16T17:43:33Z
- **提交信息**: [Fix] rust-server: Refuse return_hidden_states above the server's mode (#50555)

### [ddc8a02](https://github.com/sgl-project/sglang/commit/ddc8a02a384e554891d95b7959ec47c15ff0ab0d)

- **作者**: Michael
- **时间**: 2026-11-16T17:22:28Z
- **提交信息**: [CI] [AMD] nightly-benchmark: Run InferenceX's AgentX MiniMax-M3.1-Flash DSpark curve on MI35x (#50489)

### [48e3558](https://github.com/sgl-project/sglang/commit/48e35583bd0ebf251637d5b670a615145ce85564)

- **作者**: Xinyuan Tong
- **时间**: 2026-11-16T14:13:29Z
- **提交信息**: [Fix] parser: Fix reasoning/tool-call grammar handoff and GLM-4.5 argument parsing (#45803)

Co-authored-by: 文贤 <luoyuan.luo@antgroup.com>
Co-authored-by: 得泽 <zhangkaihong.zkh@antgroup.com>

### [c712459](https://github.com/sgl-project/sglang/commit/c712459e7f8233302fdf0bdd5d4ddcd22aa4b2ab)

- **作者**: Haishuo.Kong
- **时间**: 2026-11-16T13:43:05Z
- **提交信息**: [Fix] http_server: Hold the HTTP port across the model load (#49823)

### [bb0d416](https://github.com/sgl-project/sglang/commit/bb0d416adb42bc0127dd7d3ec18d38a4e3d08a50)

- **作者**: zilong
- **时间**: 2026-11-16T13:42:45Z
- **提交信息**: [Perf] qwen3-next: Use fused_sigmoid_mul for the attention output gate (#50696)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [bfdcfe1](https://github.com/sgl-project/sglang/commit/bfdcfe18d94b914051516f7eb4b8c104039a35f1)

- **作者**: Han-Yin Chang
- **时间**: 2026-11-16T13:42:30Z
- **提交信息**: [Fix] diffusion/ltx2: Repeat prompt rows when one request asks for several videos (#50529)

Signed-off-by: Han-Yin Chang <nick20350@gmail.com>
Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

### [4ea50be](https://github.com/sgl-project/sglang/commit/4ea50be84156987358b7f263b5d59bb0e89e49ba)

- **作者**: BESzbing
- **时间**: 2026-11-16T13:42:21Z
- **提交信息**: [Fix] quantization: Pad the Marlin N tile for compressed-tensors WNA16 (#48794)

### [e0cf330](https://github.com/sgl-project/sglang/commit/e0cf330b24e9d892e753a520ece201943694d1ff)

- **作者**: Po-Han Huang (NVIDIA)
- **时间**: 2026-11-16T13:22:40Z
- **提交信息**: [Doc] cookbook: Refresh SemiAnalysis AgentX launches to InferenceX main 8ab57a81 (#50766)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [47361c5](https://github.com/sgl-project/sglang/commit/47361c57be9fcc23f11b9804633bfcfe9342f98e)

- **作者**: Piotr Mazurek
- **时间**: 2026-11-16T11:33:14Z
- **提交信息**: [Feat] lfm3: Add text, vision, audio and Omni support (#46858)

Co-authored-by: Xinyuan Tong <115166877+JustinTong0323@users.noreply.github.com>
Co-authored-by: Xinyuan Tong <xinyuantong.cs@gmail.com>

### [d130d85](https://github.com/sgl-project/sglang/commit/d130d857543ba25794229a67e7f81064f23df22d)

- **作者**: Bowen Wang
- **时间**: 2026-11-16T11:12:41Z
- **提交信息**: [Fix] multimodal: Return the selected processor from LlavaMultimodalProcessor (#45868)

Co-authored-by: Xinyuan Tong <xinyuantong.cs@gmail.com>

### [8cb94fc](https://github.com/sgl-project/sglang/commit/8cb94fcc3f097a5b547dca352131a0b6a05d9ca7)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-16T09:44:52Z
- **提交信息**: [Fix] sampling: Parse the UOCR page-guard lookahead inside its error handling (#49760)

### [4138420](https://github.com/sgl-project/sglang/commit/41384200061f5aea317d402e878750cbf144e7b7)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-16T09:42:02Z
- **提交信息**: [Fix] security: Redact the HiCache storage credentials from server info, dumps, logs and gRPC (#49761)

### [5c51b46](https://github.com/sgl-project/sglang/commit/5c51b4690001b7e0530ae7f212b072f584b6db02)

- **作者**: Ke Bao
- **时间**: 2026-11-16T09:36:00Z
- **提交信息**: [Chore] inkling: Bump tml-renderers to 0.4.1 (#50522)

Co-authored-by: Xinyuan Tong <115166877+JustinTong0323@users.noreply.github.com>
Co-authored-by: Aurick Qiao <aurickq@users.noreply.github.com>
Co-authored-by: Xinyuan Tong <xinyuantong.cs@gmail.com>

### [8854900](https://github.com/sgl-project/sglang/commit/885490015cadf0ece168cc06c41e37dce0171a73)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-16T09:26:19Z
- **提交信息**: [Misc] router: NPU router artifact name and a multi-node KV events warning (#50751)

### [cf1ab1b](https://github.com/sgl-project/sglang/commit/cf1ab1bd65baaa80f0a476d973f29642d24cbf50)

- **作者**: Wenkai Du
- **时间**: 2026-11-16T09:20:30Z
- **提交信息**: [Perf] [AMD] custom-all-reduce: Add hier_ring_simple, a ring all-reduce over partition pairs on gfx1250 (#50660)

Co-authored-by: Cursor <cursoragent@cursor.com>

### [074aeaf](https://github.com/sgl-project/sglang/commit/074aeaf67499d06cc61300971fae90bcf4297670)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-16T09:07:19Z
- **提交信息**: [CI] pr_title: Allow the Misc type (#50755)

### [88151fa](https://github.com/sgl-project/sglang/commit/88151fa62c6129f56a80b2127a0f770be3de6f83)

- **作者**: konst42r
- **时间**: 2026-11-16T08:52:51Z
- **提交信息**: [Perf] [NPU] dsa: Add INT8 LightningIndexer to accelerate indexing on A2/A3 (#42224)

Co-authored-by: Артем Савкин <58187114+OrangeRedeng@users.noreply.github.com>
Co-authored-by: TamirBaydasov <mr.jeijy@gmail.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [59963c6](https://github.com/sgl-project/sglang/commit/59963c664fcf11717dcac10d20f37bbfc98817d6)

- **作者**: Mick
- **时间**: 2026-11-16T08:49:19Z
- **提交信息**: [Doc] diffusion: update the README logo (#50669)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>

### [37bc19e](https://github.com/sgl-project/sglang/commit/37bc19e86ea88a4f8fe03c781a18c3a7692eb713)

- **作者**: Mick
- **时间**: 2026-11-16T08:48:02Z
- **提交信息**: [Perf] diffusion: enable H3 Image FP8 attention on DGX Spark (#49599)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [d03e40c](https://github.com/sgl-project/sglang/commit/d03e40c6a2ae22076aeb7f6e852ece60454fac7b)

- **作者**: Mick
- **时间**: 2026-11-16T08:47:34Z
- **提交信息**: [Doc] diffusion: Correct Wan video requests and document padding tradeoffs (#48503)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [3237f87](https://github.com/sgl-project/sglang/commit/3237f87e0519a754c1ed981c04202ed4c16b5a71)

- **作者**: Mick
- **时间**: 2026-11-16T08:47:01Z
- **提交信息**: [Perf] diffusion: Hash large conditioning-cache keys in parallel chunks (#46100)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [2588d80](https://github.com/sgl-project/sglang/commit/2588d80d062ec80cad7a1eb02b56882e53ace995)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-16T08:35:32Z
- **提交信息**: [Refactor] gateway: Delete sgl-model-gateway and its leftovers (#50732)

### [b947a61](https://github.com/sgl-project/sglang/commit/b947a615f62bbb31e3b5e5165674930eef0cef33)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-16T07:55:09Z
- **提交信息**: [Refactor] gateway: Keep sgl-model-gateway as source only and move every user to sgl-router (#50671)

### [ed3aa8c](https://github.com/sgl-project/sglang/commit/ed3aa8c3226eb18ca4a4d071778a0929066245cc)

- **作者**: Ankith Averineni
- **时间**: 2026-11-16T07:31:19Z
- **提交信息**: [Perf] [AMD] dsv4: Retune sparse paged-prefill launch config for gfx1250 (#41382)

### [1315562](https://github.com/sgl-project/sglang/commit/1315562f8e4797d598cb09e0a7bc610cbf979ae3)

- **作者**: Артем Савкин
- **时间**: 2026-11-16T07:29:39Z
- **提交信息**: [Fix] [NPU] CI: Update NPU failure analyzer coverage (#44736)

### [ecc5cb2](https://github.com/sgl-project/sglang/commit/ecc5cb25a66ac11eab4ed81b531eaf532f79d5fd)

- **作者**: Ho-Ren (Jack) Chuang
- **时间**: 2026-11-16T07:12:47Z
- **提交信息**: [Perf] [NVIDIA] KDA: Extend the CuTe DSL MTP verify kernel to SM90 (#44612)

Co-authored-by: Han Han <hanhan7630@outlook.com>
Co-authored-by: Xinyuan Tong <xinyuantong.cs@gmail.com>

### [50fbc8a](https://github.com/sgl-project/sglang/commit/50fbc8af48f870370f53f8ecb22ef941319417a7)

- **作者**: BingjiaWang
- **时间**: 2026-11-16T07:05:51Z
- **提交信息**: [Feat] [NVIDIA] deepseek-v4.1: Support prefill CP with BCG in PD serving (2/N) (#40333)

Co-authored-by: SYChen123 <csy512356@ant-intl.com>

### [56a2e45](https://github.com/sgl-project/sglang/commit/56a2e457e6fa29d56b3c7c66ea25e3d9eef4a699)

- **作者**: BaoYunkai
- **时间**: 2026-11-16T07:05:28Z
- **提交信息**: [Perf] [AMD] gdn: Add an aiter backend for linear-chain target verify (#48118)

### [a75b6bf](https://github.com/sgl-project/sglang/commit/a75b6bffe90e991da67f3e819d3619a26629b9f5)

- **作者**: jiaqiang-dot-liu
- **时间**: 2026-11-16T07:05:05Z
- **提交信息**: [Doc] [AMD] cookbook: Add the Qwen3.5 MI300X FP8 agentic recipe (#50402)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [d9bf131](https://github.com/sgl-project/sglang/commit/d9bf131d8b9b07bd85fbba9b1f80b8644310e60a)

- **作者**: Guangda Liu
- **时间**: 2026-11-16T06:59:04Z
- **提交信息**: [Feat] hisparse: Add the HiCache backend data plane (#49473)

### [baaa201](https://github.com/sgl-project/sglang/commit/baaa201a146e484cb281ba4c402acbba1e07ae7e)

- **作者**: lihaoming45
- **时间**: 2026-11-16T06:22:02Z
- **提交信息**: [Feat] [NPU] DSpark: Support multi-stream execution in draft layers (#49294)

### [b41e00c](https://github.com/sgl-project/sglang/commit/b41e00c09dcd94b42749d44c69ccec611d90454d)

- **作者**: Cheng Xin
- **时间**: 2026-11-16T06:11:07Z
- **提交信息**: [Test] [NPU] llada2-mini: Run FDFO performance case with 32 prompts at 6K/3K (#50105)

### [24feb92](https://github.com/sgl-project/sglang/commit/24feb92de0678b33b9de4f42b908e015df11d6a3)

- **作者**: yz-wqf
- **时间**: 2026-11-16T05:37:20Z
- **提交信息**: [Perf] [NVIDIA] mega_moe: Allow DeepGEMM weight localization on SM 10.0 and 10.3 (#50608)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [4fed7f2](https://github.com/sgl-project/sglang/commit/4fed7f29c77046be313e4e6dfa2ac805f5ff1342)

- **作者**: Kunal
- **时间**: 2026-11-16T05:19:36Z
- **提交信息**: [Fix] disaggregation: Release multimodal features when PD prefill finishes a request (#44576)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [4d4d35e](https://github.com/sgl-project/sglang/commit/4d4d35ea3a61b3bea97d41309b4d92ffbd1a3813)

- **作者**: Mick
- **时间**: 2026-11-16T05:11:36Z
- **提交信息**: [CI] diffusion: Isolate editable install cache locks per runner (#49697)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [861f851](https://github.com/sgl-project/sglang/commit/861f8514a754e43a60396f5521de9fd8c8e6ed61)

- **作者**: Mick
- **时间**: 2026-11-16T05:07:11Z
- **提交信息**: [Doc] diffusion: Clarify H100 baseline calibration limits (#49998)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [c5b97de](https://github.com/sgl-project/sglang/commit/c5b97de00c3278f5f337514ed54bb7d19cdb4fb7)

- **作者**: Mick
- **时间**: 2026-11-16T05:06:05Z
- **提交信息**: [Feat] diffusion: Add end-to-end serving profiling (#50658)

Co-authored-by: zhyajie <yajizhan@amd.com>
Co-authored-by: ronnie_zheng <zl19940307@163.com>
Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [862c793](https://github.com/sgl-project/sglang/commit/862c793da1ba2f11d596eecf39b4d2d23f790349)

- **作者**: Mick
- **时间**: 2026-11-16T05:05:24Z
- **提交信息**: [Doc] diffusion: update adoption wall (#50668)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [f76ac26](https://github.com/sgl-project/sglang/commit/f76ac26543deb2149c2da9173b59b3adce16df0f)

- **作者**: Wenzhi Feng
- **时间**: 2026-11-16T04:27:48Z
- **提交信息**: [Feat] scheduler: add fixed-batch bounded LPM policy (#48409)

### [5a31013](https://github.com/sgl-project/sglang/commit/5a31013d6b305dd356500d3fbe9ba2434733d7b8)

- **作者**: Aravind.S
- **时间**: 2026-11-16T04:27:27Z
- **提交信息**: [Fix] quantization: Determine Qwen3.5 GDN dense vs. GPTQ init from checkpoint precision and dynamic exclusions (#38854) (#39741)

Signed-off-by: aravindsundaresan <aravindsharma20@gmail.com>

### [a365e8e](https://github.com/sgl-project/sglang/commit/a365e8e59b874e0b35e1763e3d87ef40de620019)

- **作者**: Han-Yin Chang
- **时间**: 2026-11-16T04:27:05Z
- **提交信息**: [Fix] diffusion: Align Anima request sizes to the 16-pixel patch grid (#50599)

Signed-off-by: Han-Yin Chang <nick20350@gmail.com>

### [a985f1d](https://github.com/sgl-project/sglang/commit/a985f1d8a68f87127ef45f0cc5fba89ad6e578f4)

- **作者**: Han-Yin Chang
- **时间**: 2026-11-16T04:26:49Z
- **提交信息**: [Fix] diffusion: Align MOSS-Image request sizes to the 16-pixel patch grid (#50598)

Signed-off-by: Han-Yin Chang <nick20350@gmail.com>

### [ea3ff74](https://github.com/sgl-project/sglang/commit/ea3ff7414dba7266bc16418b6d26b5c47f8a1d0b)

- **作者**: Han-Yin Chang
- **时间**: 2026-11-16T04:26:32Z
- **提交信息**: [Fix] diffusion/qwen-image-layered: Keep the input image's alpha channel (#50589)

Signed-off-by: Han-Yin Chang <nick20350@gmail.com>

### [4888890](https://github.com/sgl-project/sglang/commit/488889009d07a31b9b209e79693ea09b4c9b9c5b)

- **作者**: xiaofei-zheng
- **时间**: 2026-11-16T04:26:15Z
- **提交信息**: [Doc] [AMD] cookbook: Run the GLM-5.3 MI355X AgentX TP4 command with write-back HiCache (#50678)

### [ad1d2ca](https://github.com/sgl-project/sglang/commit/ad1d2cab7b28ee2d3b170c10ce65a974587076cb)

- **作者**: DarkSharpness
- **时间**: 2026-11-16T04:25:55Z
- **提交信息**: [Fix] tp-qknorm: Stride push phases by kNumGPU slots (#50645)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [b40c565](https://github.com/sgl-project/sglang/commit/b40c565be9fa769d5c980f8f43467820d8a6b64f)

- **作者**: weireweire
- **时间**: 2026-11-16T04:24:00Z
- **提交信息**: [Fix] disaggregation: Read attn_dp_size in the prefill_complete validator (#50520)

Co-authored-by: weireweire <20922698+weireweire@users.noreply.github.com>

### [3981de0](https://github.com/sgl-project/sglang/commit/3981de0825d577fd47c11b3a1645b35e6a3f8618)

- **作者**: Khoa Pham
- **时间**: 2026-11-16T04:17:01Z
- **提交信息**: Revert "[Perf] [NVIDIA] runtime: Blackwell/Rubin serving optimizations for hybrid GDN + QSA + MoE models (#50156)" (#50703)

### [e73b150](https://github.com/sgl-project/sglang/commit/e73b150870115790dca9478ddda5698e5de886f7)

- **作者**: Ke Bao
- **时间**: 2026-11-16T04:16:42Z
- **提交信息**: [Fix] usage: Report reasoning_tokens as 0 when the model does not think (#50576)

Co-authored-by: Xinyuan Tong <xinyuantong.cs@gmail.com>

### [552e169](https://github.com/sgl-project/sglang/commit/552e16968b5a9db4ccd5e47f8006235fa2527026)

- **作者**: Yuxuan Zhang
- **时间**: 2026-11-16T03:00:46Z
- **提交信息**: [Fix] scheduler: Join the prefill delayer all-gather on DP ranks that defer prefill (#50146)

Co-authored-by: Shangming Cai <csmthu@gmail.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [55ceff1](https://github.com/sgl-project/sglang/commit/55ceff111496fbf58eda1d2a1606c510f936266b)

- **作者**: Michael
- **时间**: 2026-11-16T02:52:47Z
- **提交信息**: [CI] [AMD] nightly: Run minimax-m3.1 MXFP4 only on its cron's ROCm image (#50492)

### [c926f4a](https://github.com/sgl-project/sglang/commit/c926f4acb10c80bcf6693f8ea7a1582cd98fe89a)

- **作者**: Mick
- **时间**: 2026-11-16T02:45:15Z
- **提交信息**: [Doc] diffusion: Document multiple dynamic LoRA adapters (#49997)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [c63d7e3](https://github.com/sgl-project/sglang/commit/c63d7e3d73f769f97e74eb25d6f23f931b7f6041)

- **作者**: Yihao Wang
- **时间**: 2026-11-16T02:43:42Z
- **提交信息**: [Doc] diffusion: Fix cookbook commands, model IDs and catalog entries (#49671)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [19f4a42](https://github.com/sgl-project/sglang/commit/19f4a42f90476c9e443f8627b5d0f98043e52fe9)

- **作者**: Mick
- **时间**: 2026-11-16T02:39:17Z
- **提交信息**: [Fix] diffusion: Keep tqdm off its multiprocessing lock in scheduler workers (#50663)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Sonnet 5.5 <noreply@anthropic.com>

### [ab0a701](https://github.com/sgl-project/sglang/commit/ab0a701fbc0907497c66abae78cb63f9880f4ac2)

- **作者**: metamergebot
- **时间**: 2026-11-16T02:22:33Z
- **提交信息**: [Fix] custom-ar-v2: Finalize symmetric workspaces in registration order (#50572)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: ZYHowell <ZYHowell@users.noreply.github.com>

### [41ceffe](https://github.com/sgl-project/sglang/commit/41ceffe676ba889b601316af1585e34bbbaaeb67)

- **作者**: Phạm Phú Lợi
- **时间**: 2026-11-16T02:16:06Z
- **提交信息**: [Feat] gemma4: Support --language-model-only (#49511)

Signed-off-by: Phạm Phú Lợi <127595669+phphlio1@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Po-Han Huang <pohanh@nvidia.com>

### [2605373](https://github.com/sgl-project/sglang/commit/2605373abbdbb7d3441b7513be58d801c927f04c)

- **作者**: Youduo Liu
- **时间**: 2026-11-16T02:09:17Z
- **提交信息**: [Doc] [NPU] cookbook: add A3 deployment scenarios to GLM-5.1 (#45655)

### [2f7dd85](https://github.com/sgl-project/sglang/commit/2f7dd856a0346fdb9a474e4362fcc0f3cdb67e1a)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-16T01:40:30Z
- **提交信息**: [CI] rust: Cache the Rust Ext cargo target dir and narrow the sgl-router cache key (#50659)

### [775db05](https://github.com/sgl-project/sglang/commit/775db052b618bf1d34a747f86c79fcfd311b65ca)

- **作者**: YAMY
- **时间**: 2026-11-16T01:35:22Z
- **提交信息**: [Perf] [NVIDIA] runtime: Blackwell/Rubin serving optimizations for hybrid GDN + QSA + MoE models (#50156)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [406667c](https://github.com/sgl-project/sglang/commit/406667c45fe5c08ff8bde73109c4e0359a183ca3)

- **作者**: shun8686
- **时间**: 2026-11-16T01:33:31Z
- **提交信息**: [CI] NPU: Align precision baseline OBS paths (#50027)

### [0b28a39](https://github.com/sgl-project/sglang/commit/0b28a39a2b5ce363930447161f58ba9cd04c9c15)

- **作者**: YAMY
- **时间**: 2026-11-16T01:21:58Z
- **提交信息**: [Feat] [NVIDIA] megakernel-binding: state, pool, prefill-graph and draft-step views for hybrid models (#50157)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [da614ba](https://github.com/sgl-project/sglang/commit/da614bad49dad9c0cbae5b3c0be04581c1f16a9e)

- **作者**: YAMY
- **时间**: 2026-11-16T01:02:03Z
- **提交信息**: [CI] megakernel: Select sgl-nvidia-mega's e2e tests from its per-model list (#50641)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [023b1d7](https://github.com/sgl-project/sglang/commit/023b1d7dcb138d18deef9ac2d16aba75461915bc)

- **作者**: Mick
- **时间**: 2026-11-16T00:36:09Z
- **提交信息**: [Doc] diffusion: Center the logo wall and update MOSS branding (#50662)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [0b098e1](https://github.com/sgl-project/sglang/commit/0b098e1279bcf030408100f95ffbe44ad0a51f2a)

- **作者**: Mick
- **时间**: 2026-11-16T00:17:33Z
- **提交信息**: [Doc] diffusion: Document Z-Image output size alignment (#50254)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [33726c2](https://github.com/sgl-project/sglang/commit/33726c21249bb90ec3df083513fdb8134490860a)

- **作者**: Mick
- **时间**: 2026-11-16T00:13:42Z
- **提交信息**: [Doc] diffusion: Add adoption and integrations logo wall (#50556)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-11-17
**监控日期**: 2026-11-16
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for 100+ DiTs.
- **语言**: Python
- **星标数**: 1308
- **最后更新**: 2026-11-15T22:07:40Z

## 提交统计

- **昨日提交总数**: 5
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

## 提交分析总结

### 1. 主要更新类型
本次提交以**重构和文档更新**为主，核心是将 FP8/FP4 量化 GEMM 统一迁移到 CUTLASS collective 框架，辅以相关文档补充和 README 清理。

### 2. 关键变更点及其与项目方向的关系

- **FP8 GEMM 全面重构**：将 per-row/per-tensor/per-block 三种 FP8 量化 GEMM 模式统一迁移到 CUTLASS SM120 collectives，并统一了 `fp8_quantize_gemm` 命名、自动 padding/depad 机制，直接强化了 README 中提到的**量化（Quantization）**核心能力。
- **FP4 GEMM 收敛**：移除手写 FP4 GEMM 和 `use_ws`，升级 CUTLASS 子模块至 v4.8.1，统一使用 collective 入口 `fp4_gemm_cutlass_2x/1x`，减少了自维护代码量。
- **SVDQ 可行性分析**：新增 CUTLASS collective 可行性参考文档，为后续 SVDQ（与 #1283 相关）量化方案做技术铺垫。
- **README 整理**：移除 emoji、常规更新，属于项目呈现层的清理工作。

### 3. 对项目的影响和潜在意义

- **代码统一性显著提升**：FP4/FP8 两条量化路径全部收敛到 CUTLASS collective 单一框架，降低了双轨维护成本，未来新增量化格式（如 SVDQ）可以复用同一套基础设施。
- **测试覆盖充分**：191 个 FP8 测试 + 315 个 FP4 测试通过，并做了 FLUX FP4/FP8 编译对比验证，重构风险可控。
- **性能可移植性增强**：依赖官方 CUTLASS 库而非手写 kernel，能更好地跟随 NVIDIA 新架构（SM120）的优化，对推理引擎的持续性能演进有利。

### 4. 值得关注的技术点

- **自动 padding/depad 机制**：为不支持的形状自动补齐/去补，使 CUTLASS collective 的形状限制对上层透明，这是工程上的重要抽象。
- **EVT 与 scale-layout 契约文档化**：明确了量化、事件（EVT）和 scale 布局的接口约定，有利于多人协作和后续扩展。
- **CUTLASS 子模块版本管理**：升级到 v4.8.1 并成为唯一依赖路径，需关注后续 CUTLASS 版本兼容性。
- **SVDQ 可行性分析先行**：采用"文档论证 → 实施"的模式，与 #1283 关联，预示下一步可能落地 SVDQ 量化。

### 5. 对项目发展的整体影响

cache-dit 作为面向 DiT 的 PyTorch 原生推理引擎，其核心竞争力在于 **Cache、并行、量化和 CPU Offload** 四大能力。本批提交通过统一量化 GEMM 底层实现，夯实了"量化"这一支柱的技术基础——用成熟的 CUTLASS collective 替代手写 kernel，既提升了代码质量和可维护性，又为后续 SVDQ 等新量化方案铺平了道路。配合文档中对量化契约的明确，项目正从"功能堆叠"阶段走向"架构收敛与规范化"阶段，有利于吸引社区贡献者和保障长期演进。README 的轻量清理则体现了项目对外呈现的持续打磨。总体而言，这是一组高质量的架构性重构提交，对项目的技术债清理和未来扩展具有积极意义。

## 详细提交记录

### [7773cda](https://github.com/vipshop/cache-dit/commit/7773cda304251e87a36d9532442420daa28b6f1a)

- **作者**: DefTruth
- **时间**: 2026-11-16T10:15:40Z
- **提交信息**: Remove emojis from video entries in README

### [ee38814](https://github.com/vipshop/cache-dit/commit/ee388144a92be59d9eba1045ca5fea850523c0cd)

- **作者**: DefTruth
- **时间**: 2026-11-16T10:15:15Z
- **提交信息**: Update README.md

### [e1d50f7](https://github.com/vipshop/cache-dit/commit/e1d50f7c8dfb7c76d3a5095a476211b5ee1c8b90)

- **作者**: DefTruth
- **时间**: 2026-11-16T09:47:37Z
- **提交信息**: docs(svdq): add CUTLASS collective feasibility analysis (#1331)

Add and register the SVDQ CuTe FP4 CUTLASS collective feasibility reference. Related to #1283.

### [eced015](https://github.com/vipshop/cache-dit/commit/eced0158b25e597aa629e6ce6551397359d65afe)

- **作者**: DefTruth
- **时间**: 2026-11-16T08:47:56Z
- **提交信息**: refactor(fp8): use CUTLASS collectives for all GEMM modes

- migrate per-row/per-tensor/per-block FP8 GEMM to CUTLASS SM120 collectives
- add automatic padding/depad and unify fp8_quantize_gemm naming
- document quantization, EVT and scale-layout contracts
- validate with 191 tests and FLUX FP4/FP8 compile comparisons

### [3448773](https://github.com/vipshop/cache-dit/commit/344877336ef0bf4e79c4812050cd662fe07573d9)

- **作者**: DefTruth
- **时间**: 2026-11-16T06:48:36Z
- **提交信息**: refactor(fp4): use CUTLASS 4.8.1 collective only

- upgrade CUTLASS submodule to v4.8.1
- remove hand-written FP4 GEMM and use_ws
- rename collective entry points to fp4_gemm_cutlass_2x/1x
- add automatic padding/depad for unsupported shapes
- document quantization, collective and EVT contracts
- 315 tests passed

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-11-17
**监控日期**: 2026-11-16
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 97065
- **最后更新**: 2026-11-17T04:29:47Z

## 提交统计

- **昨日提交总数**: 113
- **提交者数量**: 84
- **主要提交者**: PerryZhang01, Yosef W. Alemneh, Santhanam

## AI分析总结

# vLLM 昨日提交分析（113 个提交）

## 一、主要更新类型

- **性能优化占比最高**：内核融合持续推进，涵盖 GELU+NVFP4 融合、MXFP4 旋转融合、RMSNorm 融合（含 Qwen4Exp MTP drafter 单 Triton 发射）、FP8 量化融合与 group 量化 value-only reduction、Qwen3.5 FP8 动态量化并入 Gemma add-RMSNorm。投机解码路径去冗余、GDN 去除预填充拷贝、Mamba mid-block resume 预填充由 3 次前向压缩为 1 次，MoE a2a 通信默认启用。
- **功能新增**：新模型支持（DeepSeek-V4.1 扩展至 SM80/SM90、LFM3-Omni、Step5 PrimTS 注意力、DSpine 投机解码、EAGLE-3/DSpark 辅助隐藏状态）；Rust 前端补齐 --hf-token、abort_requests、tokens-only 端点、优先级头、--kv-sharing-fast-prefill、features 透传等 CLI/API 能力；序列并行与流水线并行组合支持；KV offload 度量与 mmap 路径。
- **Bug 修复**：分布式/NCCL 流顺序、投机解码、KV 卸载、Mooncake 连接器与后端接口抽象、注意力后端校验、多模态预处理（LLaVA-OneVision、Llama 4、ERNIE-4.5-VL、GLM）、安全（压缩包解压大小检查）。
- **重构与 CI/文档**：Worker 平台初始化钩子暴露、KV offload 命名规范、ROCm/XPU CI 大量维护、DockerHub 镜像别名、GPU 活动采样。

## 二、关键变更与项目方向

- **Rust 前端快速收敛**：约三分之一提交围绕与 Python 入口的行为对齐——logprobs 空格、透明图合成、缓存键命名、错误码 400/500，加速 Rust 网关替代 Python 入口，为低开销生产接入铺路。
- **多硬件均衡深化**：ROCm（gfx942/gfx950/RDNA4 MI350/MI355）、XPU、Blackwell/Rubin、NVIDIA 多架构同步投入，含 int4 lm_head 量化、Mamba2 SSD kernel，呼应"普惠 serving"目标。
- **大规模模型扩展性**：Qwen3-Next/Qwen3.5/DeepSeek-V2/V3/V3.2 的 SP+PP 组合，直接服务长上下文与大 MoE 高吞吐部署。
- **KV 分层与 P/D 分离**：KV Offload、Mooncake、对称内存 rendezvous 修复、AuxOutput 路由专家，强化 disaggregated serving 生产可靠性。
- **量化与在线量化**：NVFP4、FP8、MX 系列贯穿稠密层、MoE 与投机解码；NVFP4 在线权重量化与量化模块直接重载，指向动态部署。

## 三、影响与潜在意义

DeepSeek-V4.1 扩展至 SM80/SM90 并配套元数据惰性导入，扩大最新模型硬件覆盖；内核融合与量化优化带来端到端延迟/吞吐收益，尤其在 NVFP4 与 FP8 decode 路径；KV Offload 与 Mooncake 修复降低 disaggregated 架构故障恢复成本；SP+PP 与投机解码提升旗舰模型吞吐上限；torch.load 前校验降低供应链攻击面；镜像别名与多厂商 CI 修复改善分发、开发体验与非 NVIDIA 平台发布节奏。

## 四、值得关注的技术点

**batch-invariance（批量不变性）** 作为横切主题贯穿 MXFP8 内核选择守卫、H100 配置、collective 分片归约与文档，确定性推理正成为一等公民；**一致性工程** 在 Rust 与 Python 的缓存键、图像合成、logprobs 上逐项对齐，是跨实现一致性的良好实践；**AI 辅助开发** 深度融入，多数提交由 Claude/Codex/Cursor 等智能体共同署名，反映人机协作已成为项目标准工作流。

## 五、对项目发展的综合影响

这些提交表明 vLLM 同时推进 **Rust 前端成熟化、新硬件与新模型并行扩展、内核级性能深挖** 三条主线，从"快速迭代"转向"性能精雕 + 多硬件均衡 + 生产可靠性"并重的成熟期。Rust 前端降低接入成本，SP+PP 与内核融合提升速度，多硬件适配摊薄部署成本，共同兑现 README 中 "easy, fast, and cheap" 的承诺。可预见下一阶段 Rust 前端进入功能冻结与生产验证期，SP+PP 与投机解码的组合优化将成为旗舰模型服务的默认路径，而多后端将从"能跑"走向优化成熟，进一步巩固 vLLM 作为通用 LLM serving 底座的地位。

## 详细提交记录

### [b409a4f](https://github.com/vllm-project/vllm/commit/b409a4f0d787fdddb75ec2e8ddb6dfcfd36235b7)

- **作者**: Xinyu Chen
- **时间**: 2026-11-16T23:51:31Z
- **提交信息**: [XPU] Include oneAPI compiler build date in collect_env (#67172)

Signed-off-by: Xinyu Chen <xinyu1.chen@intel.com>
Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [ea8f314](https://github.com/vllm-project/vllm/commit/ea8f3140ef7a15a04e8e0f0f208ab3c7285ae264)

- **作者**: Kevin H. Luu
- **时间**: 2026-11-16T23:38:48Z
- **提交信息**: [CI/Build] Mirror release and nightly images to the vllm/vllm, vllm/vllm-rocm and vllm/vllm-xpu DockerHub aliases (#65107)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [cd154c6](https://github.com/vllm-project/vllm/commit/cd154c622a7f817c25ac10ee60d00f7f1c25fb8e)

- **作者**: Hanjun Cho
- **时间**: 2026-11-16T23:21:19Z
- **提交信息**: [Perf][Kernel] Fuse GELU + NVFP4 quant for BERT-style FFNs (#65578)

Signed-off-by: Hanjun Cho <gkswns0531@gmail.com>
Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Thien Tran <gau.nernst@yahoo.com.sg>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [68e4786](https://github.com/vllm-project/vllm/commit/68e478651a20e3d23bf939912c38883d511ac3ee)

- **作者**: afriedri
- **时间**: 2026-11-16T22:44:20Z
- **提交信息**: [ROCm][CI] Skip wvSplitKQ fp8 skinny GEMM test where the kernel is not built (#68025)

Signed-off-by: Andy Friedrich <andy.friedrich@amd.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [fdc3364](https://github.com/vllm-project/vllm/commit/fdc3364c9543de38e8900360ea1fd6df9c1ec557)

- **作者**: Sheral Kumar
- **时间**: 2026-11-16T22:08:26Z
- **提交信息**: [ROCm][CI] Retarget 8 MI300 1 GPU jobs to the mi300_dpx queue (#67993)

Signed-off-by: Sheral Kumar <shekumar@amd.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [bf39457](https://github.com/vllm-project/vllm/commit/bf39457294ccd246e92aa7243d46db79aa054a06)

- **作者**: Chenyu Zhang
- **时间**: 2026-11-16T21:39:34Z
- **提交信息**: [Spec Decode][MRV2] Pass NewRequestData to speculator add_request; add shutdown hook (#64306)

Signed-off-by: Chenyu Zhang <chenyzhang@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [94de867](https://github.com/vllm-project/vllm/commit/94de867077ce4bbcdcfc9413002a9b2feb2640d2)

- **作者**: Andreas Karatzas
- **时间**: 2026-11-16T21:05:05Z
- **提交信息**: [CI][ROCm] Keep HIP uninitialized in the GPU memory wait (#67821)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [78aa0f1](https://github.com/vllm-project/vllm/commit/78aa0f15f7f8d4a4b550503b07069188a6bef10f)

- **作者**: Misha Goin
- **时间**: 2026-11-16T20:53:26Z
- **提交信息**: [Quant] LUT-B: fit per-channel block32 weight scales (#67267)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [fa6c77f](https://github.com/vllm-project/vllm/commit/fa6c77f5954ef22e705cd82456cc731ba67d0ae9)

- **作者**: Thang Nguyen
- **时间**: 2026-11-16T20:40:39Z
- **提交信息**: [Bugfix][DSv4.1] Import the SM80/SM90 metadata builders lazily (#68005)

Signed-off-by: Thang Nguyen <thangnguyenvn647@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [35890ee](https://github.com/vllm-project/vllm/commit/35890eeba058ab5f571f9b7838b31d60e0e73ccd)

- **作者**: Santhanam
- **时间**: 2026-11-16T20:39:24Z
- **提交信息**: [Perf] Use value-only reduction for FP8 group quantization (#59564)

### [f5dd110](https://github.com/vllm-project/vllm/commit/f5dd1105023485bc1e28eeb23c561f4ae593465f)

- **作者**: keneoneth
- **时间**: 2026-11-16T20:07:25Z
- **提交信息**: [ROCm][Kernel] Extend skinny gemm N=5 to N=8 cases on GFX12 (RDNA4) using  SWMMAC optimization (#45559)

Signed-off-by: keneoneth <keneoneth18@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Douglas Lehr <91553416+dllehr-amd@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [2deea9a](https://github.com/vllm-project/vllm/commit/2deea9af98f5d26334fa98cde44df2db4a09ba72)

- **作者**: Tony Lin
- **时间**: 2026-11-16T20:05:35Z
- **提交信息**: [XPU][batch invariant] Optimize batch-invariant collectives with sharded reductions (#67182)

Signed-off-by: Tony Lin <tony.lin@intel.com>
Co-authored-by: Flora Feng <4florafeng@gmail.com>

### [8070069](https://github.com/vllm-project/vllm/commit/8070069e849111f3238bb70f88b28d66838f252b)

- **作者**: Helen Zhao
- **时间**: 2026-11-16T20:04:36Z
- **提交信息**: [Spec Decode] Add DSpine support (#67094)

Signed-off-by: shanjiaz <zsjwpianpian@gmail.com>
Signed-off-by: Tomas Ruiz <tomas.ruiz.te@gmail.com>
Co-authored-by: Codex <codex@openai.com>
Co-authored-by: Tomas Ruiz <tomas.ruiz.te@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Codex <noreply@openai.com>

### [4dd655d](https://github.com/vllm-project/vllm/commit/4dd655ddb5a8ef097c1e6626f770a638e53ee3c4)

- **作者**: Wei Zhao
- **时间**: 2026-11-16T20:04:10Z
- **提交信息**: [CI][Test] Share the narrow dummy FP8 fixture with the NVFP4 fusion test (#67809)

Signed-off-by: wzhao18 <wzhao18.sz@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [233171e](https://github.com/vllm-project/vllm/commit/233171ed5c8f7b363076c782dbc510bc309cdccd)

- **作者**: Josh R
- **时间**: 2026-11-16T20:02:56Z
- **提交信息**: [ROCm][Perf] Use tuned AITER Triton `gemm_a8w8` for per-tensor FP8 decode GEMMs on gfx950 (#65711)

Signed-off-by: amd-jrosas <joshua.rosas@amd.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [348b4bf](https://github.com/vllm-project/vllm/commit/348b4bf89680af55b5cf9dbeb63684e4b2cedc97)

- **作者**: Mickaël Seznec
- **时间**: 2026-11-16T20:02:11Z
- **提交信息**: [Bugfix][Distributed] Guard cross-node symmetric-memory rendezvous (#59208)

Signed-off-by: Mickael Seznec <mickael@mistral.ai>
Co-authored-by: Wei Zhao <51183510+wzhao18@users.noreply.github.com>

### [5b4659e](https://github.com/vllm-project/vllm/commit/5b4659e755f4dace97cf89f7ccfa793368f16f0b)

- **作者**: Samu Tamminen
- **时间**: 2026-11-16T20:00:29Z
- **提交信息**: [ROCm][Kimi-K3] Enable encoder graph capture for Kimi-K3 Vision Tower (#63086)

Signed-off-by: Samu Tamminen <samu.tamminen@amd.com>
Co-authored-by: Claude Code <noreply@anthropic.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [b4369a2](https://github.com/vllm-project/vllm/commit/b4369a29cdff5a34901bc0da7ca7cb7920c735fc)

- **作者**: 최재영
- **时间**: 2026-11-16T19:59:14Z
- **提交信息**: [Bugfix][MiniMax-M3] Drop the stale config read from the FlashInfer indexer builder (#67215)

Signed-off-by: 최재영 <144660874+Jaeyeong-CHOI@users.noreply.github.com>
Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>

### [7c1a90d](https://github.com/vllm-project/vllm/commit/7c1a90d0913813051ab4205f75d5ce922122e50c)

- **作者**: bnellnm
- **时间**: 2026-11-16T19:58:59Z
- **提交信息**: [MoE] Disable expanded DeepEP v2 dispatch in all execution modes (#66653)

Signed-off-by: Tyler Michael Smith <tlrmchlsmth@gmail.com>
Signed-off-by: Bill Nell <bnell@redhat.com>
Signed-off-by: bnellnm <49004751+bnellnm@users.noreply.github.com>
Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Tyler Michael Smith <tlrmchlsmth@gmail.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Misha Goin <mgoin64@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [9b0ae78](https://github.com/vllm-project/vllm/commit/9b0ae78af60195e7df280a7b8e0e0f44efdd3edb)

- **作者**: xaguilar-amd
- **时间**: 2026-11-16T19:57:37Z
- **提交信息**: [ROCm][Bugfix] Port Mistral Large 4 AMD indexer cache to get_kv_cache_config (#67984)

Signed-off-by: Xavier Aguilar <xavier.aguilarfruto@amd.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [96ad207](https://github.com/vllm-project/vllm/commit/96ad207c2cb02c01005c1eb96db16ccba70a36bd)

- **作者**: Jon Belof
- **时间**: 2026-11-16T19:57:13Z
- **提交信息**: [Perf][MoE] OCP MX emulation: dequantize only the routed experts (#64406)

Signed-off-by: Jon Belof <jonathan.belof@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Eugene Kuznetsov <eugene.kuznetsov@amd.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [0c8dae9](https://github.com/vllm-project/vllm/commit/0c8dae983ac1c5dafae62ae7779be2e89d8cbbcc)

- **作者**: Mikko Tukiainen
- **时间**: 2026-11-16T19:56:44Z
- **提交信息**: [ROCm][Quantization][Perf] Fuse the block Hadamard input rotation into AITER's MXFP4 activation quant (#63272)

Signed-off-by: Mikko Tukiainen <Mikko.Tukiainen@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [2f5dc1d](https://github.com/vllm-project/vllm/commit/2f5dc1d729437fc00b91213773e03bf683027757)

- **作者**: Bandham Manikanta
- **时间**: 2026-11-16T19:43:06Z
- **提交信息**: [CI][Test] Prevent NVSHMEM IB transport setup hang in DBO GSM8K tests (#67852)

Signed-off-by: Manikanta Bandham <bandhammanikanta@gmail.com>
Co-authored-by: Wei Zhao <51183510+wzhao18@users.noreply.github.com>

### [5358288](https://github.com/vllm-project/vllm/commit/535828851cb9404f280422de973fdd062d71a966)

- **作者**: Isaac Thompson
- **时间**: 2026-11-16T19:18:51Z
- **提交信息**: [Doc] Correct the batch-invariance comment on Hopper/Blackwell split-k (#67179)

Signed-off-by: imthomp <it238@byu.edu>

### [17fcc9d](https://github.com/vllm-project/vllm/commit/17fcc9da8d44befffc3b39f5685e3b76f6866249)

- **作者**: JunjieChen
- **时间**: 2026-11-16T19:17:29Z
- **提交信息**: [KV Connector][Mooncake] Fail pulls from a lost prefill worker (#65575)

Signed-off-by: CJJ1008 <843515223@qq.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [33ca7f4](https://github.com/vllm-project/vllm/commit/33ca7f415b23346a8601ac6dc46297dafcfd9f64)

- **作者**: Itay Etelis
- **时间**: 2026-11-16T19:10:35Z
- **提交信息**: [KV Offload] Set the CPU tier up in the background under async_init (#66583)

Signed-off-by: Itay Etelis <92247226+Etelis@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [fbbaa32](https://github.com/vllm-project/vllm/commit/fbbaa328f54ae4512f0d1a8bfadb08b6eaab75bb)

- **作者**: Isaac Thompson
- **时间**: 2026-11-16T19:02:13Z
- **提交信息**: [Kernel][Perf] Add H100 BF16 batch-invariant matmul configs for gpt-oss (#65931)

Signed-off-by: imthomp <it238@byu.edu>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [7f4a9a3](https://github.com/vllm-project/vllm/commit/7f4a9a3cc671f1385f476d234d4399e6af98525c)

- **作者**: Hongxia Yang
- **时间**: 2026-11-16T18:51:14Z
- **提交信息**: [Config] Make --monokernel and decode_backend=latency_specialized one switch (#67315)

Signed-off-by: Hongxia Yang <hongxia.yang@amd.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [3e2d13b](https://github.com/vllm-project/vllm/commit/3e2d13bc217462541434b122f3089679c931ad22)

- **作者**: Flora Feng
- **时间**: 2026-11-16T18:40:49Z
- **提交信息**: [Bugfix] Select only batch-invariant MXFP8 linear kernels under VLLM_BATCH_INVARIANT (#67806)

Signed-off-by: Flora Feng <4florafeng@gmail.com>

### [a712bf9](https://github.com/vllm-project/vllm/commit/a712bf9ef3d8a66e3225770c7287039376151233)

- **作者**: James E T Smith
- **时间**: 2026-11-16T18:40:22Z
- **提交信息**: [Recipe][ROCm] ripple-65b on mi350x and mi355x (#67055)

Signed-off-by: jamesETsmith <james.smith9113@gmail.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Hongxia Yang <62075498+hongxiayang@users.noreply.github.com>

### [b401405](https://github.com/vllm-project/vllm/commit/b401405452eab3f4b9d85421aa719116b1532cf1)

- **作者**: Pham Binh
- **时间**: 2026-11-16T18:32:27Z
- **提交信息**: [Bugfix][ROCm] Fix ROCM_AITER_FA context loss on out-of-order batches (#59098)

Signed-off-by: Pham Binh <194774975+phambinhfin@users.noreply.github.com>
Co-authored-by: Pham Binh <194774975+phambinhfin@users.noreply.github.com>
Co-authored-by: Qiang Li <qiang.li2@amd.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Douglas Lehr <91553416+dllehr-amd@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Simon Danielsson <70206058+simondanielsson@users.noreply.github.com>

### [31a8415](https://github.com/vllm-project/vllm/commit/31a841584007d44a862c75fdb67e5fad3b11c088)

- **作者**: Andreas Karatzas
- **时间**: 2026-11-16T18:25:59Z
- **提交信息**: [ROCm][CI] Dump child process stacks when an AMD CI test times out (#67605)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [cfe0fb6](https://github.com/vllm-project/vllm/commit/cfe0fb6b951c842f6740f84a43a1a148bd4090f2)

- **作者**: Andreas Karatzas
- **时间**: 2026-11-16T18:25:18Z
- **提交信息**: [ROCm][CI] Re-enable VLLM_GPU_SYNC_CHECK=error in the ROCm test image (#64176)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [d48c4df](https://github.com/vllm-project/vllm/commit/d48c4dfce391142a168faaa7668b5255d2ebc194)

- **作者**: Andreas Karatzas
- **时间**: 2026-11-16T18:24:58Z
- **提交信息**: [ROCm][Model] Run Qwen3.5 on the eager breakable-graph model on MI355X (#66320)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [ce88d40](https://github.com/vllm-project/vllm/commit/ce88d407a76b487a0ad358fd34c2e2aa5107faec)

- **作者**: Andreas Karatzas
- **时间**: 2026-11-16T18:22:55Z
- **提交信息**: [ROCm][CI] Make /ci rocm cache a cache-only CI build that also copies the runtime (#66032)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [352dbd1](https://github.com/vllm-project/vllm/commit/352dbd1db9f543ecc10ce9f4d8257ba28bda5129)

- **作者**: Yaoyao Ding
- **时间**: 2026-11-16T17:54:00Z
- **提交信息**: [Model][DSv4.1] DeepSeek-V4.1 on A100 (SM80) and H100 (SM90) (#66497)

Signed-off-by: Yaoyao Ding <yaoyaod@nvidia.com>
Signed-off-by: Misha Goin <mgoin64@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Misha Goin <mgoin64@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [b89d893](https://github.com/vllm-project/vllm/commit/b89d8935b63e1fe63785f179721d4ca400bcdbed)

- **作者**: Kevin H. Luu
- **时间**: 2026-11-16T17:18:54Z
- **提交信息**: [CI][Test] Compare logprobs in the Machete bf16 repeat-run test (#67917)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [d27d74a](https://github.com/vllm-project/vllm/commit/d27d74a591e677e38b77be1704228f84313a7114)

- **作者**: yeshihai
- **时间**: 2026-11-16T17:09:06Z
- **提交信息**: [Bugfix][Distributed] Fall back to torch.distributed when pynccl is disabled (#67882)

Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [f418f61](https://github.com/vllm-project/vllm/commit/f418f616efd13022c21825120424f41048dcaba4)

- **作者**: Paul Pak
- **时间**: 2026-11-16T16:59:40Z
- **提交信息**: [Model] Add LFM3-Omni (#65829)

Signed-off-by: paulpak58 <52512091+paulpak58@users.noreply.github.com>

### [732bafd](https://github.com/vllm-project/vllm/commit/732bafd23f9a5afd4cfb67aa638bc2d9ec16bf28)

- **作者**: Chinmay Shrivastava
- **时间**: 2026-11-16T16:43:17Z
- **提交信息**: [MRV2][Spec Decode] Cap dummy-run requests by their draft slots (#67571)

Signed-off-by: JonSnow1807 <JonSnow1807@users.noreply.github.com>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: JonSnow1807 <JonSnow1807@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [a4c6f3b](https://github.com/vllm-project/vllm/commit/a4c6f3b747f0925ce54e4fdb467d36fe62139597)

- **作者**: Perkz Zheng
- **时间**: 2026-11-16T16:42:58Z
- **提交信息**: [Model] Add opt-in PrimTS attention for Step5 on Blackwell (#62550)

Signed-off-by: Perkz Zheng <67892460+PerkzZheng@users.noreply.github.com>
Signed-off-by: <>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Claude Sonnet 5.5 <noreply@anthropic.com>
Co-authored-by: Perkz Zheng <perkzz@oci-jhb-slurm-1-vscode-01.cm.cluster>
Co-authored-by: Jee Jee Li <pandaleefree@gmail.com>

### [9a6032d](https://github.com/vllm-project/vllm/commit/9a6032dbeebd8d78addcc8573119edfaf9daf3d9)

- **作者**: devshah-cohere
- **时间**: 2026-11-16T16:07:17Z
- **提交信息**: [Rust Frontend] Support --tokens-only (#67708)

Signed-off-by: Dev Shah <dev.shah@cohere.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [87c9334](https://github.com/vllm-project/vllm/commit/87c9334782e4c85a521aea6d1937ebd923ac3bd1)

- **作者**: Stary
- **时间**: 2026-11-16T16:05:48Z
- **提交信息**: [Bugfix][Mooncake] Make early prefill abort cleanup idempotent (#65672)

Signed-off-by: staryxchen <staryxchen@tencent.com>

### [9e341f4](https://github.com/vllm-project/vllm/commit/9e341f4c66b9c77f2fba78d2e5df68569bbdc688)

- **作者**: Bugen Zhao
- **时间**: 2026-11-16T16:04:36Z
- **提交信息**: [Rust Frontend] Serve /inference/v1/abort_requests (#67893)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: weihantu <das41086@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [02fe81c](https://github.com/vllm-project/vllm/commit/02fe81c8aeaf23932d66c8274895002325221e0b)

- **作者**: Stefano Castagnetta
- **时间**: 2026-11-16T15:55:55Z
- **提交信息**: [Quantization] Online weight-only NVFP4 for dense linear layers (#67006)

Signed-off-by: Stefano Castagnetta <scastagnetta@nvidia.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [c5993c0](https://github.com/vllm-project/vllm/commit/c5993c0471bdebe6e8be2596d483ca9deee71c83)

- **作者**: bogdan-petkovic
- **时间**: 2026-11-16T15:40:01Z
- **提交信息**: [ROCm][CI] Widen the bound of test_quark_online_rotation_wikitext (#67938)

Signed-off-by: bogdan-petkovic <bpetkovi@amd.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [52fae19](https://github.com/vllm-project/vllm/commit/52fae19fb648cea2d0fdfbf1e9cdcfedacc3c4ca)

- **作者**: Jakub Zakrzewski
- **时间**: 2026-11-16T15:08:28Z
- **提交信息**: [Perf] Add opt-in FlashInfer multimodal encoder autotuning (#65901)

Signed-off-by: Jakub Zakrzewski <jzakrzewski@nvidia.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [d454b3d](https://github.com/vllm-project/vllm/commit/d454b3d42707e6eac6a472f3780b028c2c737050)

- **作者**: AlexHuang
- **时间**: 2026-11-16T14:48:28Z
- **提交信息**: [Bugfix][KV Offload] Avoid false flushes for shared Full Attention prefixes (#67486)

Signed-off-by: Alex <alex.tech.lab@outlook.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [dcc3e3c](https://github.com/vllm-project/vllm/commit/dcc3e3ced8bb551595a9446f05d275d75aa0b52f)

- **作者**: mushroomcarbon
- **时间**: 2026-11-16T14:47:24Z
- **提交信息**: [KV Offload] Explain EFAULT from a full /dev/shm in _madvise_populate_write (#62058)

Signed-off-by: Andrew Goh <andrew.goh@zillion.network>
Co-authored-by: Itay Etelis <92247226+Etelis@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [6606dde](https://github.com/vllm-project/vllm/commit/6606dde694bbd936d50f9055384622b0a956a9e1)

- **作者**: Yannick Schnider
- **时间**: 2026-11-16T14:46:37Z
- **提交信息**: [Bugfix][Model] Gemma4/Gemma3n: allocate the PLE cache on the input device (#62659)

Signed-off-by: Yannick Schnider <Yannick.Schnider1@ibm.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [a4910b4](https://github.com/vllm-project/vllm/commit/a4910b41280ae228bcc74ebc9d21144e09ef63ef)

- **作者**: Aaron Hao
- **时间**: 2026-11-16T13:53:22Z
- **提交信息**: [Model Loader] Direct reload of online-quantized modules (#65802)

Signed-off-by: Aaron Hao <hao-aaron@users.noreply.github.com>
Signed-off-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: Aaron Hao <hao-aaron@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: aoshen02 <aoshen@inferact.ai>

### [902364d](https://github.com/vllm-project/vllm/commit/902364d152ff5cc204addd049c217e3bd68cc2fe)

- **作者**: Aaron Hao
- **时间**: 2026-11-16T13:18:40Z
- **提交信息**: [RL][Model Loader] Load FP8 indexer wk and MLA projections independently, as FP8 or BF16, in any scale layout (#66118)

Signed-off-by: aoshen02 <aoshen@inferact.ai>
Signed-off-by: Aaron Hao <hao-aaron@users.noreply.github.com>
Co-authored-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Aaron Hao <hao-aaron@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [4fdc79d](https://github.com/vllm-project/vllm/commit/4fdc79d89d9788838740092c3557845d376b259f)

- **作者**: lishuoshuo-amd
- **时间**: 2026-11-16T12:59:10Z
- **提交信息**: [ROCm][DSv4.1][Perf] Always use the unfolded layer-0 mHC entry on gfx942 (#67853)

Signed-off-by: lishuoshuo-amd <shuoli@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Shanshan Shen <467638484@qq.com>

### [013741d](https://github.com/vllm-project/vllm/commit/013741d38900d454fb7bb7c0ee02cf61e91d5904)

- **作者**: Jared Wen
- **时间**: 2026-11-16T12:55:28Z
- **提交信息**: [Perf][KDA] Export Triton KDA prefill checkpoints via a per-sequence buffer (#67866)

Signed-off-by: Jared Wen <jaredwen@inferact.ai>
Co-authored-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [919025c](https://github.com/vllm-project/vllm/commit/919025c814832aed3a1fea323b00a9e321039d34)

- **作者**: Yuhan Zhou
- **时间**: 2026-11-16T12:40:04Z
- **提交信息**: [Perf][KV Connector][MooncakeConnector] Submit Mooncake transfer descriptors with array API (#67656)

Signed-off-by: Yuhan Zhou <zhouyuhan_@outlook.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [b1bbd26](https://github.com/vllm-project/vllm/commit/b1bbd26fe3b9ee9a37110b4f6fd16bc8aa105c38)

- **作者**: siyu
- **时间**: 2026-11-16T12:29:38Z
- **提交信息**: [Fast Start] Support compressed-tensors CUTLASS FP8 weight-cache restarts (#63673)

Signed-off-by: liusy58 <liusy58@smail.nju.edu.cn>
Signed-off-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: liusy58 <liusy58@smail.nju.edu.cn>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>

### [9986df4](https://github.com/vllm-project/vllm/commit/9986df412141231516b80c023a799136522c3d47)

- **作者**: Yizhou Wang
- **时间**: 2026-11-16T11:20:53Z
- **提交信息**: [XPU][UT] Enable v1/attention tests on XPU (#65788)

Signed-off-by: Yizhou Wang <yizhou.wang@intel.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [0db6f1b](https://github.com/vllm-project/vllm/commit/0db6f1ba55c8b85e19ed3f3abd6edef007432959)

- **作者**: Kevin H. Luu
- **时间**: 2026-11-16T10:59:59Z
- **提交信息**: [CI] Sample GPU activity on Kubernetes jobs (L4, B200, H100) (#67910)

Signed-off-by: Kevin Luu <51931015+khluu@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [bb94a48](https://github.com/vllm-project/vllm/commit/bb94a485b28a493a7691155be4c23a083b643688)

- **作者**: Bugen Zhao
- **时间**: 2026-11-16T10:23:47Z
- **提交信息**: [Rust Frontend] Honor X-Vllm-Priority on generate and reject unparsable request headers (#67399)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [d07b7db](https://github.com/vllm-project/vllm/commit/d07b7db9785564549d163937b5d5d9c04c76d626)

- **作者**: PerryZhang01
- **时间**: 2026-11-16T09:47:35Z
- **提交信息**: [CI] Fix SPLADE late-interaction reset test after ec_connector.reset() (#66846) (#67888)

Signed-off-by: PerryZhang01 <Perry.Zhang@amd.com>

### [cf0a516](https://github.com/vllm-project/vllm/commit/cf0a516f95cf2ad6f63c11980123d288790b7f4f)

- **作者**: Artem Perevedentsev
- **时间**: 2026-11-16T09:37:27Z
- **提交信息**: [MoE] enable all2all fi_one_sided by default only for Blackwell and Rubin (#54268)

Signed-off-by: Artem Perevedentsev <aperevedents@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [c2d7d74](https://github.com/vllm-project/vllm/commit/c2d7d74774a8550cb6f6a19931fcaebbe0f9f0d1)

- **作者**: Bugen Zhao
- **时间**: 2026-11-16T09:36:41Z
- **提交信息**: [Rust Frontend] Accept features together with content_parts on /generate (#67400)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [cab3f26](https://github.com/vllm-project/vllm/commit/cab3f26ab24e5442387dead34a4aa627ae661664)

- **作者**: Reid
- **时间**: 2026-11-16T09:12:17Z
- **提交信息**: [Bugfix][Rust Frontend] Preserve SentencePiece leading spaces in logprobs (#63773)

Signed-off-by: reidliu41 <reid201711@gmail.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [aea5035](https://github.com/vllm-project/vllm/commit/aea503524a19d920d70f67b7b63ae960ef58b26d)

- **作者**: Ronald
- **时间**: 2026-11-16T09:12:06Z
- **提交信息**: [Refactor][Worker] Expose platform initialization hooks (#65565)

Signed-off-by: Ronald1995 <ronaldautomobile@163.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [614f529](https://github.com/vllm-project/vllm/commit/614f5297c5f4c4fef17a4c8beb2aa34b9d87fb94)

- **作者**: Bugen Zhao
- **时间**: 2026-11-16T09:11:24Z
- **提交信息**: [Rust Frontend] Fix tests that fail when sharing one test process (#67729)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [ab6696a](https://github.com/vllm-project/vllm/commit/ab6696a5f0781422abbb9467af1c259c873afa8a)

- **作者**: Bugen Zhao
- **时间**: 2026-11-16T09:10:29Z
- **提交信息**: [Rust Frontend] Support --kv-sharing-fast-prefill (#67872)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [13329cc](https://github.com/vllm-project/vllm/commit/13329cca5ca75daa9cbb83446e695cdd97cae427)

- **作者**: xiangdong
- **时间**: 2026-11-16T09:10:21Z
- **提交信息**: [XPU][CI]Disable BMG Rust Frontend Core Correctness due to random accuracy issue (#67867)

Signed-off-by: zengxian <xiangdong.zeng@intel.com>

### [e501342](https://github.com/vllm-project/vllm/commit/e501342f3f7d6931ff5b7103f5c30f4e14d5731f)

- **作者**: PerryZhang01
- **时间**: 2026-11-16T09:05:36Z
- **提交信息**: [ROCm][CI] Keep the CI kernel recorder out of the Python 3.14 smoke venv (#67694)

Signed-off-by: PerryZhang01 <Perry.Zhang@amd.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [c418202](https://github.com/vllm-project/vllm/commit/c4182020b39aa30fe985cc38404a43f077f7d052)

- **作者**: Aaron Deng
- **时间**: 2026-11-16T08:35:55Z
- **提交信息**: [Bugfix][Attention] Reject TORCH_SDPA for decoder attention (#64965)

Signed-off-by: Aaron Deng <84045863+aarongdeng@users.noreply.github.com>
Co-authored-by: ChatGPT <noreply@openai.com>

### [0cf8b0f](https://github.com/vllm-project/vllm/commit/0cf8b0f8bab1ed6465401949bdb82d87179ea8d0)

- **作者**: Aaron Hao
- **时间**: 2026-11-16T08:34:16Z
- **提交信息**: [Test][Model Loader] Direct weight reload equals a cold start, bitwise (#65347)

Signed-off-by: Aaron Hao <hao-aaron@users.noreply.github.com>
Co-authored-by: Aaron Hao <hao-aaron@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [657f971](https://github.com/vllm-project/vllm/commit/657f971b8533125d3d5528f2e9886f85e3671449)

- **作者**: Bugen Zhao
- **时间**: 2026-11-16T08:33:14Z
- **提交信息**: [Rust Frontend] Support --hf-token (#67871)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [eda28e4](https://github.com/vllm-project/vllm/commit/eda28e41fa4bb968af7dd8d816af5bcaa9356d5f)

- **作者**: Bugen Zhao
- **时间**: 2026-11-16T08:32:07Z
- **提交信息**: [Rust Frontend] Support --default-mm-loras (#67873)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [25063c7](https://github.com/vllm-project/vllm/commit/25063c7c36cd133c2be6b19cb7079eccbaaa50b2)

- **作者**: Bugen Zhao
- **时间**: 2026-11-16T08:31:18Z
- **提交信息**: [Rust Frontend] Domain-tag multimodal cache keys like Python (#67870)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [53526b1](https://github.com/vllm-project/vllm/commit/53526b1253b21d2fcc11fa1516a4f939caf40283)

- **作者**: Tianyao Wu
- **时间**: 2026-11-16T08:30:23Z
- **提交信息**: [Bugfix][Rust Frontend] Composite transparent images over white like Python (#63912)

Signed-off-by: Tianyao Wu <rayroy31@gmail.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [d17f8ab](https://github.com/vllm-project/vllm/commit/d17f8abb9193577c6d385dd7036b58bbfe356d80)

- **作者**: Bugen Zhao
- **时间**: 2026-11-16T08:29:29Z
- **提交信息**: [Rust Frontend] Return 500 for engine errors on non-streaming generate (#67869)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [6a0fc61](https://github.com/vllm-project/vllm/commit/6a0fc612870e8de4f9afdb12a6ef096042edb3c5)

- **作者**: Tianyao Wu
- **时间**: 2026-11-16T08:27:17Z
- **提交信息**: [Bugfix][Rust Frontend] Return 400 for media the request got wrong (#63749)

Signed-off-by: Tianyao Wu <rayroy31@gmail.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [5b6139a](https://github.com/vllm-project/vllm/commit/5b6139aec58d4773c1a54581bcd23534ff373c33)

- **作者**: TJian
- **时间**: 2026-11-16T08:24:30Z
- **提交信息**: [Bugfix][ROCm][MoRIIO] Slice WRITE heads by each layer's head count (#62474)

Signed-off-by: tjtanaa <tunjian.tan@embeddedllm.com>
Signed-off-by: kliuae <kuanfu.liu@embeddedllm.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: kliuae <kuanfu.liu@embeddedllm.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [9448aba](https://github.com/vllm-project/vllm/commit/9448aba2c8847cfa4df6167293d0e1918db693d2)

- **作者**: waizuichougou
- **时间**: 2026-11-16T08:04:44Z
- **提交信息**: [Bugfix][KV Offload] Report transferred bytes in tiering metrics (#67788)

Signed-off-by: waizuichougou <2082431897@qq.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [543cb51](https://github.com/vllm-project/vllm/commit/543cb51c071db93cfd5647e694da55de952921ca)

- **作者**: Yifei Wang
- **时间**: 2026-11-16T07:45:33Z
- **提交信息**: [Bugfix][MRV2] Apply EVS-recomputed M-RoPE positions on every PP stage (#66632)

Signed-off-by: Yifei Wang <yifei.w@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [77d5b1a](https://github.com/vllm-project/vllm/commit/77d5b1a6a47b2f9cbbbceecedc1a147d4a5878b1)

- **作者**: chuncaohenli
- **时间**: 2026-11-16T07:40:11Z
- **提交信息**: [Bugfix][Multimodal] Fix LLaVA-OneVision embeddings for unequal video frame counts (#67744)

Signed-off-by: chuncaohenli <604265882@qq.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [e0af2d6](https://github.com/vllm-project/vllm/commit/e0af2d6a77b2cba2877d5aaeb1ac5a3aee676bc8)

- **作者**: Lucas Martins
- **时间**: 2026-11-16T07:10:23Z
- **提交信息**: [Rust Frontend] Pass pulled object storage model dir to the Rust frontend (#61788)

Signed-off-by: Lucas-Fernandes-Martins <lucasfmartins16@gmail.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>

### [d5bc1e4](https://github.com/vllm-project/vllm/commit/d5bc1e4d53730ad7ee26f608e4be4fda1d593d58)

- **作者**: Aaron Hao
- **时间**: 2026-11-16T07:05:02Z
- **提交信息**: [Bugfix][Distributed] Order packed NCCL loads after the caller stream (#65487)

Signed-off-by: Aaron Hao <hao-aaron@users.noreply.github.com>
Signed-off-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: Aaron Hao <hao-aaron@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: aoshen02 <aoshen@inferact.ai>

### [0d9d953](https://github.com/vllm-project/vllm/commit/0d9d953d68ceccd2738c8229dd82ae39f2ef5d56)

- **作者**: Artur Fierka
- **时间**: 2026-11-16T06:06:13Z
- **提交信息**: [Kernel][XPU] Mamba2 SSD: tensor-descriptor path for _chunk_scan_fwd_kernel and _chunk_state_fwd_kernel (#60801)

Signed-off-by: Marceli Fylcek <marceli.fylcek@intel.com>
Signed-off-by: Artur Fierka <artur.fierka@intel.com>
Co-authored-by: Marceli Fylcek <marceli.fylcek@intel.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [60bd6dd](https://github.com/vllm-project/vllm/commit/60bd6dd2edd175a1c55fd3488f871e4c3d2ef27d)

- **作者**: Isotr0py
- **时间**: 2026-11-16T05:35:29Z
- **提交信息**: [Fast Start] Add weights mirror support for daemon2daemon (#64641)

Signed-off-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: liusy58 <mg21330037@smail.nju.edu.cn>
Co-authored-by: Xun Sun <UNIDY2002@outlook.com>
Co-authored-by: Kimi Code <noreply@moonshot.cn>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [7c86910](https://github.com/vllm-project/vllm/commit/7c869102912b9f89bd7c99688e771c1273b8aeb5)

- **作者**: Yuxuan Zhang
- **时间**: 2026-11-16T05:31:34Z
- **提交信息**: [Multimodal] Require Rust preprocessing for GLM-5.3-Flash (#67237)

Signed-off-by: Yuxuan Zhang <Yuxuan.Zhang2@liverpool.ac.uk>
Signed-off-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>

### [1077638](https://github.com/vllm-project/vllm/commit/1077638523987ce80e468b1017dc9fb054b735fc)

- **作者**: Yifei Wang
- **时间**: 2026-11-16T05:30:24Z
- **提交信息**: [Model] Support sequence parallelism with pipeline parallelism for Qwen3-Next, Qwen3.5 and DeepSeek-V2/V3 (#66866)

Signed-off-by: Yifei Wang <yifei.w@inferact.ai>
Co-authored-by: AceCoder0 <104333925+AceCoder0@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [b6dfb95](https://github.com/vllm-project/vllm/commit/b6dfb9543ebc44f9d4ae56ef34370dac98f39a53)

- **作者**: Xin Li
- **时间**: 2026-11-16T05:30:11Z
- **提交信息**: [Perf][MiniMax-M3.1] MiniMax-M3.1-Flash Specialized Decode: CuTe DSL Optimized GB300 (up to 1.45x) (#66324)

Signed-off-by: Xin Li <xinli@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [2cddb0d](https://github.com/vllm-project/vllm/commit/2cddb0dcda54c3ffcb8d7bf5b9be589b1d124b65)

- **作者**: Yifei Wang
- **时间**: 2026-11-16T05:29:53Z
- **提交信息**: [DeepSeek-V3.2] Support sequence parallelism with pipeline parallelism (#65947)

Signed-off-by: Yifei Wang <yifei.w@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [dab9fb7](https://github.com/vllm-project/vllm/commit/dab9fb74c3f630f0eab698b4b3a186a0ab63659b)

- **作者**: SyaOtiLan
- **时间**: 2026-11-16T05:24:17Z
- **提交信息**: [CI] Align CPU offload latency-test prefixes with cache blocks (#67761)

Signed-off-by: SyaOtiLan <954239196@qq.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [b93d6e4](https://github.com/vllm-project/vllm/commit/b93d6e4c177b74ebb122682ccbf5fba97f44cf02)

- **作者**: omerpaz95
- **时间**: 2026-11-16T05:09:51Z
- **提交信息**: [KV Offload] Add mmap_path to SharedOffloadRegion (#67258)

Signed-off-by: omerpaz95 <omerpaz95@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [81e20e9](https://github.com/vllm-project/vllm/commit/81e20e92e880418e15999473fd292f1aa07e5e30)

- **作者**: Yiliu Dong
- **时间**: 2026-11-16T05:09:22Z
- **提交信息**: [Perf][Hy4] Enable sink-aware ShardQ prefill (#67490)

Signed-off-by: Yiliu Dong <91178480+qianlihuang@users.noreply.github.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [fe5be25](https://github.com/vllm-project/vllm/commit/fe5be25a65747c4dced8449ce5c4520b69b10052)

- **作者**: Lantao Jin
- **时间**: 2026-11-16T05:05:36Z
- **提交信息**: [CI][ROCm] Fix the DSv4.1 sparse MLA forward_mqa test after #66842 (#67845)

Signed-off-by: Lantao Jin <ltjin@amazon.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [3f893fb](https://github.com/vllm-project/vllm/commit/3f893fbbcb56c85280773d927915ce9b8b849af3)

- **作者**: Amir Friedman
- **时间**: 2026-11-16T05:02:38Z
- **提交信息**: [KV Offload] Rename the filtered group index to config_group_idx (#65197)

Signed-off-by: Amir Friedman <Amir.Friedman1@ibm.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Or Ozeri <oro@il.ibm.com>

### [92b5279](https://github.com/vllm-project/vllm/commit/92b52792da4f68d8cd81037749c8a46e822d4ce2)

- **作者**: Thien Tran
- **时间**: 2026-11-16T04:46:11Z
- **提交信息**: [Perf][GDN] Drop the prefill copies of the fused spec-decode path (#67733)

Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [b733542](https://github.com/vllm-project/vllm/commit/b733542059641fa0d91727bb448ac425c1e947c2)

- **作者**: Thien Tran
- **时间**: 2026-11-16T04:45:51Z
- **提交信息**: [Perf][Qwen4Exp] Fuse the MTP drafter's pre-FC Gemma RMSNorms into one Triton launch (#67725)

Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [c02ebf1](https://github.com/vllm-project/vllm/commit/c02ebf136ed70dd6d9cc7b8858d27f8660f418de)

- **作者**: Yan Ma
- **时间**: 2026-11-16T04:07:34Z
- **提交信息**: [XPU] quick fix for lora test workspace (#67824)

Signed-off-by: Yan Ma <yan.ma@intel.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [777288d](https://github.com/vllm-project/vllm/commit/777288d2eb129baacda26d446d18b31d6e518ba1)

- **作者**: Yibo Liu
- **时间**: 2026-11-16T04:01:42Z
- **提交信息**: [Bugfix][Multimodal] Llama 4: honor per-request max_patches (#67813)

Signed-off-by: Yibo Liu <yibol9768@gmail.com>

### [4d6df3f](https://github.com/vllm-project/vllm/commit/4d6df3fad69f7f80b78309855a6396881b23ad88)

- **作者**: Yosef W. Alemneh
- **时间**: 2026-11-16T03:56:51Z
- **提交信息**: [Model] Add EAGLE-3 / DSpark support (aux hidden states) for Lfm3ForCausalLM (#66323)

Signed-off-by: Yosef W. Alemneh <37704356+rasyosef@users.noreply.github.com>

### [2f70c32](https://github.com/vllm-project/vllm/commit/2f70c32d07af8063b632cb67fa160b3fd19ea90b)

- **作者**: Subhash Polisetti
- **时间**: 2026-11-16T03:50:08Z
- **提交信息**: [Bugfix][Multimodal] Profile ERNIE-4.5-VL with the largest admitted video (#66937)

Signed-off-by: subhash polisetti <subhashr161347@gmail.com>

### [d1911f7](https://github.com/vllm-project/vllm/commit/d1911f711c07a9c4ceb05c993166b00ed4866497)

- **作者**: Leizhen Zhang
- **时间**: 2026-11-16T03:48:31Z
- **提交信息**: [Bugfix][Security] Check the uncompressed size of embedding archives before torch.load (#67316)

Signed-off-by: LeizhenZhang <zhangleizhen645@gmail.com>

### [5b028fb](https://github.com/vllm-project/vllm/commit/5b028fb8369dff6e5e8ba06d911d9ec98210fb51)

- **作者**: Wei Zhao
- **时间**: 2026-11-16T03:43:43Z
- **提交信息**: [Perf][Mamba] Optimize prefill splits for mid-block resume (3 forward passes to 1) (#66938)

Signed-off-by: wzhao18 <wzhao18.sz@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [7a558a7](https://github.com/vllm-project/vllm/commit/7a558a78654fe95efb59a98ad7bc89b77071a7a5)

- **作者**: Thien Tran
- **时间**: 2026-11-16T03:41:17Z
- **提交信息**: [Perf][Qwen4Exp] Drop the defensive zero fill from the QSA output path (#67728)

Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [bde6bff](https://github.com/vllm-project/vllm/commit/bde6bff65560fafed4af81e2a599b3dac326a080)

- **作者**: Artur Fierka
- **时间**: 2026-11-16T03:39:12Z
- **提交信息**: [Bugfix][XPU] Apply attn_sink in the DeepSeek-V4 sparse MLA Triton kernel (#64252)

Signed-off-by: Artur Fierka <artur.fierka@intel.com>
Co-authored-by: Claude Sonnet 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [b99384c](https://github.com/vllm-project/vllm/commit/b99384c624074d6d94d1407d46fda3ca001691d9)

- **作者**: Hen in UI
- **时间**: 2026-11-16T03:35:13Z
- **提交信息**: [Bugfix] Reject bad_words on generate servers without a tokenizer (#67408)

Signed-off-by: paul <paulqwer.cs13@nycu.edu.tw>
Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>

### [0067b98](https://github.com/vllm-project/vllm/commit/0067b98f7e62c774ea4acd300eea743aed832aaf)

- **作者**: GuorongYe
- **时间**: 2026-11-16T03:20:09Z
- **提交信息**: [Bugfix][EPD] Clear ECMooncakeConnector local cache on reset_encoder_cache (#66846)

Signed-off-by: grYe99 <guorongye99@gmail.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [3494bb0](https://github.com/vllm-project/vllm/commit/3494bb04178506d66d62c1e522dd97b73f7555f4)

- **作者**: lishuoshuo-amd
- **时间**: 2026-11-16T03:00:29Z
- **提交信息**: [ROCm][Docs] Add DeepSeek-V4.1-Flash MI300X AgentX preset (#67586)

Signed-off-by: lishuoshuo-amd <shuoli@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Shanshan Shen <467638484@qq.com>

### [193d81a](https://github.com/vllm-project/vllm/commit/193d81ab898f797586e318b0344afd9aa2cc2ea7)

- **作者**: xiao-vllm_amd
- **时间**: 2026-11-16T02:49:08Z
- **提交信息**: [ROCm][Quantization] Add load-time int4 lm_head quantization for RDNA… (#62708)

Signed-off-by: riceharvest <myappleiddarimaan@gmail.com>
Signed-off-by: Xiao Yu <xiao.yu.dc@outlook.com>
Co-authored-by: riceharvest <myappleiddarimaan@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [12e8576](https://github.com/vllm-project/vllm/commit/12e8576f6f41012e2a56ddcc5a4516bf8b6edac9)

- **作者**: Lantao Jin
- **时间**: 2026-11-16T02:42:24Z
- **提交信息**: [Perf][Qwen3.5] Fuse dynamic per-token FP8 input quant into the Gemma add-RMSNorm (#67393)

Signed-off-by: Lantao Jin <ltjin@amazon.com>
Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Thien Tran <gau.nernst@yahoo.com.sg>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [8888387](https://github.com/vllm-project/vllm/commit/88883873ed60cdef7f710bd56855c0bf9e86d08d)

- **作者**: Andreas Karatzas
- **时间**: 2026-11-16T02:37:36Z
- **提交信息**: [ROCm][Bugfix] Run the Canary WER correctness test in fp32 (#67606)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [3b1f19c](https://github.com/vllm-project/vllm/commit/3b1f19c1e35f49ed147c38cc49604eef5092eb9b)

- **作者**: azaidy
- **时间**: 2026-11-16T02:30:06Z
- **提交信息**: [ROCm][Muse Spark] DSpark draft layers as one persistent FlyDSL launch (--monokernel) (#65985)

Signed-off-by: Aliasger Zaidy <aliasger.zaidy@amd.com>
Signed-off-by: Matt <156021403+mawong-amd@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Matt <156021403+mawong-amd@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Fangzhou Ai <31551580+Fangzhou-Ai@users.noreply.github.com>

### [b6ed9b6](https://github.com/vllm-project/vllm/commit/b6ed9b6b915099b9a57b99cb39c5793134ee2ac8)

- **作者**: faresobeid
- **时间**: 2026-11-16T02:25:35Z
- **提交信息**: [Feature][AuxOutput] Support routed experts with P/D disaggregation (#62056)

Signed-off-by: Ao Shen <aoshen524@gmail.com>
Co-authored-by: Ao Shen <aoshen524@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: aoshen02 <aoshen@inferact.ai>

### [20b15bb](https://github.com/vllm-project/vllm/commit/20b15bbf5bf550e390d322ce49b6a9d8b3ae3cbf)

- **作者**: CAICAIIs
- **时间**: 2026-11-16T02:00:48Z
- **提交信息**: [Mooncake] Route KV transfers through a backend interface (#64363)

Signed-off-by: CAICAIIs <3360776475@qq.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [1bf414e](https://github.com/vllm-project/vllm/commit/1bf414e97acf7563297726531f702cdbea6b2921)

- **作者**: seungrokj
- **时间**: 2026-11-16T00:39:59Z
- **提交信息**: [Recipe] Kimi-K3.1-Pro: MI355X kimi-k31-5c14fe8 image and SP prefill, align with InferenceX#5089 (#67817)

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-11-17
**监控日期**: 2026-11-16
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7802
- **最后更新**: 2026-11-17T03:34:24Z

## 提交统计

- **昨日提交总数**: 43
- **提交者数量**: 29
- **主要提交者**: y-null, dongbo910220, Jianan Wu

## AI分析总结

## vllm-omni 昨日提交分析（第1/1批，共43条）

### 1. 主要更新类型分布
- **Bug修复**：约15条，占比最大，集中在多模态模型的运行时边界问题。
- **CI/构建**：约13条，重点是ROCm/AMD、Ascend（华为昇腾）夜间任务提升为阻塞门禁。
- **模型功能新增/集成**：约8条，新增Haru-4B全双工对话、Qwen3-Omni投机解码等。
- **性能优化**：约6条，涉及Diffusion IPC、KV缓存、编译优化等。
- **文档与清理**：少量文档更新，以及移除过时模型支持（Kokoro-82M等）。

### 2. 关键变更点与项目方向的关系
- **全双工（duplex）会话体系是核心主线**：多条提交围绕Qwen3-Omni双工会话展开——可替换的双工历史策略（#9960）、通过真实调度器钉定双工上下文边界（RFC #7389 W6，#8784）、双工轮次合并时保留相机帧（#10289）、MiniCPM-o双工分段边界重置采样器等。这直接服务于README中"easy, fast, cheap omni-modality serving"的目标，即让语音+视觉实时交互服务更稳定。
- **多硬件生态（ROCm/Ascend）门禁硬化**：大量ROCm夜间任务从非阻塞提升为阻塞、加入weekly parity和Cosmos3 burn-in测试，Ascend侧恢复MiniCPM-o图执行、优化Qwen3-TTS codec推理。说明项目正把AMD和昇腾从"实验性支持"推向"生产级质量保证"。
- **Model Runner V2 架构迁移**：Breeze-TTS-2 stage 0、MOSS-TTS-Nano、MiniMax-H3 encoder stage等逐步切换到V2运行时，体现底层执行框架的统一化重构。

### 3. 对项目的影响和潜在意义
- CI门禁收紧将减少夜间回归泄漏，提升发布可靠性，但也会增加合并门槛和CI成本（尤其AMD镜像发布已做并行化优化）。
- 双工会话的调度级修复意味着实时语音交互延迟和上下文一致性将改善，是面向"对话式omni服务"场景的关键打磨。
- 移除Kokoro-82M、JoyAI-Image-Edit等旧模型，表明项目在做支持矩阵的收敛，聚焦高价值模型。

### 4. 值得关注的技术点
- **投机解码进入omni领域**：Qwen3-Omni Thinker的DFlash投机解码Phase 1（#9595），将LLM侧的加速技术引入多模态思考链。
- **Mooncake KV/HS缓存接入双工会话**（#10321）：跨请求/跨会话的KV共享，对长时双工对话降本很关键。
- **分布式测试的TCP rendezvous竞态修复**（#10479）和OmniServer端口占用重试（#10176）：都是大规模CI下的典型并发陷阱。
- **diffusion IPC中bf16 SHM张量按原始位传输**（#9487）：进程间共享显存零拷贝的细节优化。
- **Sana-WM编译版camera-prep叶节点优化**（#8738）：opt-in方式引入torch.compile局部优化，风险可控。

### 5. 对项目发展的整体影响
结合README"让每个人都能轻松、快速、廉价地部署全模态模型"的定位，这批提交显示出项目正从"功能铺开"阶段进入"质量与性能收敛"阶段：一方面通过阻塞式CI和weekly parity夯实AMD/昇腾双硬件底座，另一方面沿双工会话、Model Runner V2、KV缓存复用三条技术线深化实时多模态服务能力。长线看，这将降低多硬件部署的隐性成本，加快omni模型从实验室走向生产环境的速度。

## 详细提交记录

### [24e5472](https://github.com/vllm-project/vllm-omni/commit/24e54728490e4ded447f0a6d0eda538dedf75bb8)

- **作者**: hac17
- **时间**: 2026-11-16T22:51:53Z
- **提交信息**: [CI/Build][ROCm] Promote three NIGHTLY full-model jobs to blocking (#10337)

Signed-off-by: hac17 <29197483+hacZ17@users.noreply.github.com>
Signed-off-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>
Co-authored-by: hac17 <29197483+hacZ17@users.noreply.github.com>
Co-authored-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>

### [cc5bc79](https://github.com/vllm-project/vllm-omni/commit/cc5bc79bfb918a044c8946af0963a27a2da106cd)

- **作者**: hac17
- **时间**: 2026-11-16T22:12:08Z
- **提交信息**: [CI/Build][ROCm] Promote NIGHTLY collective and offloader jobs to blocking (#10336)

Signed-off-by: hac17 <29197483+hacZ17@users.noreply.github.com>
Signed-off-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>
Co-authored-by: hac17 <29197483+hacZ17@users.noreply.github.com>
Co-authored-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>

### [6f16dbb](https://github.com/vllm-project/vllm-omni/commit/6f16dbb759baa45eabca38d917b00e0901fbe211)

- **作者**: hac17
- **时间**: 2026-11-16T20:34:25Z
- **提交信息**: [CI/Build] Avoid TCP rendezvous races in GLM-Image CPU tests (#10479)

Signed-off-by: hac17 <29197483+hacZ17@users.noreply.github.com>
Signed-off-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>
Co-authored-by: hac17 <29197483+hacZ17@users.noreply.github.com>
Co-authored-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>

### [8164ed7](https://github.com/vllm-project/vllm-omni/commit/8164ed75bb6fbe2a51728ebb7470169fe5e8e579)

- **作者**: lm10-arg
- **时间**: 2026-11-16T20:24:04Z
- **提交信息**: [Bugfix] Preserve CosyVoice3 DSpark capture contract (#10485)

Signed-off-by: apex-mochen <2756823972@qq.com>
Signed-off-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>
Co-authored-by: apex-mochen <2756823972@qq.com>
Co-authored-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>

### [174d221](https://github.com/vllm-project/vllm-omni/commit/174d2216c007b7d84069373a278cf25c789a0e02)

- **作者**: dongbo910220
- **时间**: 2026-11-16T19:56:55Z
- **提交信息**: [Bugfix] Validate VoxCPM2 reference audio before resolution (#10357)

Signed-off-by: dongbo910220 <1275604947@qq.com>

### [ca0129d](https://github.com/vllm-project/vllm-omni/commit/ca0129db859b8c3763fd43444a7da90fb63fff0c)

- **作者**: wangqiankun13
- **时间**: 2026-11-16T19:07:50Z
- **提交信息**: [Bugfix][Qwen-Image-Edit] Initialize the text encoder on CPU (#10451)

Signed-off-by: wangqiankun13 <wangqiankun13@huawei.com>

### [7fa9bbf](https://github.com/vllm-project/vllm-omni/commit/7fa9bbf24892d55e87a453408ecbbfd7a9a949d9)

- **作者**: alex7092
- **时间**: 2026-11-16T17:53:31Z
- **提交信息**: [Bugfix][Diffusion] Use the diffusers guidance_scale default for SDXL when omitted (#10462)

Signed-off-by: 刘星 <15105576+alex7092@users.noreply.github.com>

### [ec1c4c1](https://github.com/vllm-project/vllm-omni/commit/ec1c4c131df1e21cc37ae968296472ce43748a0f)

- **作者**: searlion
- **时间**: 2026-11-16T17:45:39Z
- **提交信息**: [Bugfix][Breeze-TTS-2] Run Breeze stage 0 on Model Runner V2 (#10399)

Signed-off-by: Lewis Won <lewis.won@gmail.com>

### [d64649c](https://github.com/vllm-project/vllm-omni/commit/d64649c41a3a2dce6da3cd97ae48b754def4eb25)

- **作者**: klin
- **时间**: 2026-11-16T16:01:43Z
- **提交信息**: [Bugfix][Wan2.2] Handle the None decode result on non-decoding pipeline-parallel stages (#10404)

Signed-off-by: Lin, KuanTing <Kuanting.Lin@amd.com>

### [4e7c184](https://github.com/vllm-project/vllm-omni/commit/4e7c184bd86265fb3240143ba8f67df66220489a)

- **作者**: Ziang Tang
- **时间**: 2026-11-16T15:51:50Z
- **提交信息**: [Core] Support Qwen3-Omni duplex sessions with Mooncake KV/HS caching (#10321)

Signed-off-by: Ziang Tang <ztang2370@gmail.com>
Signed-off-by: psv666 <150513104+psv666@users.noreply.github.com>
Co-authored-by: psv666 <150513104+psv666@users.noreply.github.com>

### [62bad9a](https://github.com/vllm-project/vllm-omni/commit/62bad9add15d867d261a083dfc4d26e70d45d931)

- **作者**: lm10-arg
- **时间**: 2026-11-16T15:44:06Z
- **提交信息**: [CI/Build] Parallelize bounded AMD image publication (#10436)

Signed-off-by: lm10-arg <linluo@icloud.com>

### [a9b61f8](https://github.com/vllm-project/vllm-omni/commit/a9b61f816ab4b3e820f222f7e82bfaafc784dc46)

- **作者**: Dong1017
- **时间**: 2026-11-16T15:01:34Z
- **提交信息**: [Perf][Sana-WM] Add opt-in compiled camera-prep leaf optimization (#8738)

Signed-off-by: GUOGUO <xwdong1998@163.com>

### [f5c3a32](https://github.com/vllm-project/vllm-omni/commit/f5c3a32d543c9f53024bafec15948fdd85083133)

- **作者**: Dong1017
- **时间**: 2026-11-16T14:28:23Z
- **提交信息**: [Doc] Record Ref2VA RainFusion points for 86 GB 950PR (#9955)

Signed-off-by: Dong1017 <xwdong1998@163.com>
Signed-off-by: GUOGUO <xwdong1998@163.com>

### [64d674c](https://github.com/vllm-project/vllm-omni/commit/64d674cb034dc0014d68752b10cb604431791d1e)

- **作者**: lm10-arg
- **时间**: 2026-11-16T13:28:27Z
- **提交信息**: [CI/Build][ROCm] Promote nightly weekly-parity owners (#10457)

Signed-off-by: lm10-arg <lm10-arg@users.noreply.github.com>
Co-authored-by: lm10-arg <lm10-arg@users.noreply.github.com>

### [8de23dc](https://github.com/vllm-project/vllm-omni/commit/8de23dc3036aa0fc9c590242ad359e2a3ae78330)

- **作者**: BruceLoveDecimal
- **时间**: 2026-11-16T13:24:42Z
- **提交信息**: [Perf][LingBot World] Add WorldKV memory retrieval (#9945)

Signed-off-by: BruceLoveDecimal <liuqihao970610@gmail.com>

### [74b163d](https://github.com/vllm-project/vllm-omni/commit/74b163d971206885000180b2d99f75243f5039a8)

- **作者**: Dong1017
- **时间**: 2026-11-16T13:24:26Z
- **提交信息**: [MiniMax-H3] Select model runner v2 for the encoder stage (#10074)

Signed-off-by: GUOGUO <xwdong1998@163.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [7726d4d](https://github.com/vllm-project/vllm-omni/commit/7726d4d9ca67cf48db02ec5f424450d4b78ddd17)

- **作者**: psv666
- **时间**: 2026-11-16T13:11:02Z
- **提交信息**: [CI/Build] Fix Qwen duplex history policy coverage (#10455)

Signed-off-by: psv666 <2693925048@qq.com>
Co-authored-by: wangyu <53896905+yenuo26@users.noreply.github.com>

### [7ba1234](https://github.com/vllm-project/vllm-omni/commit/7ba123462e657d2936d0df6e11c603f7e07d6549)

- **作者**: wangyu
- **时间**: 2026-11-16T12:43:09Z
- **提交信息**: [Bugfix] Remove hardcoded environment inventory count test (#10456)

Signed-off-by: wangyu <410167048@qq.com>

### [86df898](https://github.com/vllm-project/vllm-omni/commit/86df898490c28a93d6e18f39d49ccecf3986ee67)

- **作者**: BeatSeat
- **时间**: 2026-11-16T11:59:08Z
- **提交信息**: [Model] Run MOSS-TTS-Nano on Model Runner V2 (#9905)

Signed-off-by: BeatSeat <wendavid552@gmail.com>

### [f4b5a8a](https://github.com/vllm-project/vllm-omni/commit/f4b5a8a07b9b0fe505c589cdbb85a5abd558e918)

- **作者**: y-null
- **时间**: 2026-11-16T10:21:30Z
- **提交信息**: [Bugfix][Ascend] Restore MiniCPM-o MRv2 FULL graphs and two-card Nightly (#10435)

Signed-off-by: y-null <213026468+y-null@users.noreply.github.com>
Co-authored-by: y-null <213026468+y-null@users.noreply.github.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [84a8917](https://github.com/vllm-project/vllm-omni/commit/84a89177e6574b7141c3beb5b4b0583a5799a549)

- **作者**: Sheng GAO
- **时间**: 2026-11-16T09:54:07Z
- **提交信息**: [Bugfix] Retry OmniServer start on EADDRINUSE (#10176)

Signed-off-by: Sheng GAO <sheng.gao.dev@gmail.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: wangyu <53896905+yenuo26@users.noreply.github.com>

### [704c158](https://github.com/vllm-project/vllm-omni/commit/704c158f747f60708a3771b34f0f4c5d19d8d4bd)

- **作者**: lm10-arg
- **时间**: 2026-11-16T08:29:12Z
- **提交信息**: [CI/Build][ROCm] Promote final AMD weekly parity jobs (#10438)

Signed-off-by: lm10-arg <lm10-arg@users.noreply.github.com>
Signed-off-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>
Co-authored-by: lm10-arg <lm10-arg@users.noreply.github.com>
Co-authored-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>

### [c71efee](https://github.com/vllm-project/vllm-omni/commit/c71efee1041c32821aac1a1bc3af1d7e0fcfd7f2)

- **作者**: Yuanbing Zhu
- **时间**: 2026-11-16T07:52:55Z
- **提交信息**: [Model] Move ABot-World live camera control onto the stepwise interaction path (#10207)

Signed-off-by: zyuanbing <zhuyuanbing1021@icloud.com>
Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>

### [28d865c](https://github.com/vllm-project/vllm-omni/commit/28d865cff00c3c7c857f95b726093aad85c82cce)

- **作者**: NATURE
- **时间**: 2026-11-16T07:07:13Z
- **提交信息**: [CI/Build] Add JoyAI long-session lifecycle acceptance tests (#10386)

Signed-off-by: natureofnature <wzliu@connect.hku.hk>

### [0cf28f8](https://github.com/vllm-project/vllm-omni/commit/0cf28f81d294163ebfd30ed5de9f6442033c9952)

- **作者**: amy-why-3459
- **时间**: 2026-11-16T07:02:15Z
- **提交信息**: [Hardware][Ascend] Enable MiniMax-H3-Image VAE graph execution by default (#10184)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [0b65149](https://github.com/vllm-project/vllm-omni/commit/0b651491c2c1dd78cdf3f755befc0743af649444)

- **作者**: psv666
- **时间**: 2026-11-16T06:56:03Z
- **提交信息**: [Model] Add replaceable Qwen3-Omni duplex history policies (#9960)

Signed-off-by: psv666 <2693925048@qq.com>

### [acd3496](https://github.com/vllm-project/vllm-omni/commit/acd34967f2710ebc6ee77382937db42a716188a8)

- **作者**: amy-why-3459
- **时间**: 2026-11-16T06:34:50Z
- **提交信息**: [Hardware][Ascend] Optimize Qwen3-TTS codec and predictor inference (#9068)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>
Signed-off-by: Codex benchmark <benchmark@local.invalid>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>
Co-authored-by: Codex benchmark <benchmark@local.invalid>

### [3ae914a](https://github.com/vllm-project/vllm-omni/commit/3ae914a3a3817342aa2f0341291b4b53577e607a)

- **作者**: Y. Fisher
- **时间**: 2026-11-16T06:31:50Z
- **提交信息**: [Hardware][Ascend] Reuse LingBot paged attention lengths and block conditions (#10427)

Signed-off-by: fishermanykx <yukexiong1@huawei.com>

### [bc84941](https://github.com/vllm-project/vllm-omni/commit/bc849410d6614857c8172df7ff6e8931061e2944)

- **作者**: wangyu
- **时间**: 2026-11-16T06:11:09Z
- **提交信息**: [Model] Remove Kokoro-82M and JoyAI-Image-Edit support (#10393)

Signed-off-by: wangyu <410167048@qq.com>

### [fc308a7](https://github.com/vllm-project/vllm-omni/commit/fc308a7f4e971b79c5e05838d49935e51e284438)

- **作者**: NATURE
- **时间**: 2026-11-16T04:30:26Z
- **提交信息**: [Bugfix] Preserve committed camera frames when coalescing duplex turns (#10289)

Signed-off-by: natureofnature <wzliu@connect.hku.hk>

### [595f97a](https://github.com/vllm-project/vllm-omni/commit/595f97afd645115a2715a0f4d5259b1ecd012b32)

- **作者**: MaciejBalaNV
- **时间**: 2026-11-16T04:22:30Z
- **提交信息**: [Perf] diffusion IPC: ship bf16 SHM tensors as raw bits and copy host… (#9487)

Signed-off-by: Sebastian Rogawski <srogawski@nvidia.com>
Signed-off-by: Maciej Bala <mbala@nvidia.com>
Signed-off-by: princepride <wangzhipeng628@gmail.com>
Co-authored-by: Sebastian Rogawski <srogawski@nvidia.com>
Co-authored-by: princepride <wangzhipeng628@gmail.com>

### [abd0e5d](https://github.com/vllm-project/vllm-omni/commit/abd0e5db77d7e60d99a45acb63aefb84b3c99688)

- **作者**: WeiQing Chen
- **时间**: 2026-11-16T04:01:50Z
- **提交信息**: [Doc] Update vLLM-Omni WeChat QR code (#10423)

Signed-off-by: David Chen <530634352@qq.com>

### [0ac1fd4](https://github.com/vllm-project/vllm-omni/commit/0ac1fd4f379a3d35cb17a45893466660ee8ad54c)

- **作者**: Fenwick
- **时间**: 2026-11-16T03:38:05Z
- **提交信息**: [Core] Add Qwen3-Omni Thinker DFlash support Phase 1 Thinker-only speculative decoding (#9595)

Signed-off-by: yudeng <2272776615@qq.com>
Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>
Co-authored-by: yudeng <2272776615@qq.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [2e06bde](https://github.com/vllm-project/vllm-omni/commit/2e06bde643712bf66d173ed8fd56b70bd87a29a0)

- **作者**: amy-why-3459
- **时间**: 2026-11-16T03:30:51Z
- **提交信息**: [Model] MiniCPM-o 4.5 Seed-TTS runtime and deployment optimizations (#10331)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [d0d2b38](https://github.com/vllm-project/vllm-omni/commit/d0d2b38ff041f71b06066be0b3fe30318c46cc96)

- **作者**: Ziang Tang
- **时间**: 2026-11-16T03:25:48Z
- **提交信息**: [Core] Pin the duplex context boundary through the real scheduler (RFC #7389 W6) (#8784)

Signed-off-by: Ziang Tang <ztang2370@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [9ab4fab](https://github.com/vllm-project/vllm-omni/commit/9ab4fabc74f271074d77485560a3599649cc9853)

- **作者**: Jianan Wu
- **时间**: 2026-11-16T03:23:35Z
- **提交信息**: [Bugfix] Support up to 10 reference images in Qwen-Image 2.1 (#9770)

Signed-off-by: Jianan Wu <114214927+Nankago@users.noreply.github.com>

### [9f3d1bb](https://github.com/vllm-project/vllm-omni/commit/9f3d1bbc5e565b7ba22add867bd8ec98acbe71c5)

- **作者**: wtz2333
- **时间**: 2026-11-16T02:57:37Z
- **提交信息**: [Perf][Hy-Nomas] Parallelize PixelUMM decode windows (#9961)

Signed-off-by: wtz2333 <2955110911@qq.com>

### [8f6c007](https://github.com/vllm-project/vllm-omni/commit/8f6c00733081d9bbfb50810621de048da3fc540d)

- **作者**: Yueqian Lin
- **时间**: 2026-11-16T02:16:28Z
- **提交信息**: [Model] Add Haru-4B full-duplex spoken dialogue model (#10301)

Signed-off-by: Yueqian Lin <linyueqian@outlook.com>

### [7873c0b](https://github.com/vllm-project/vllm-omni/commit/7873c0b35c54cb7211bc16075b7cdff503026d76)

- **作者**: heyew
- **时间**: 2026-11-16T01:41:11Z
- **提交信息**: [Bugfix] Reset MiniCPM-o NPU host sampler at duplex segment boundaries (#10319)

Signed-off-by: heyew <2025190973@qq.com>

### [9afb731](https://github.com/vllm-project/vllm-omni/commit/9afb7315a55fb2fe9ef5ad5f305f0e93356757e0)

- **作者**: lm10-arg
- **时间**: 2026-11-16T01:33:46Z
- **提交信息**: [CI/Build][ROCm] Add Cosmos3 weekly generation-mode burn-in (#10416)

Add a nonblocking AMD weekly owner for both portable Cosmos3 image and video generation nodes with exact result and cleanup guards.

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Signed-off-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>

### [7fe3922](https://github.com/vllm-project/vllm-omni/commit/7fe3922435e586d7252e05089b3ec2c5f6fa4c6b)

- **作者**: Yukim1
- **时间**: 2026-11-16T01:16:10Z
- **提交信息**: [CI/Build][Ascend] Fix Fast Ulysses NPU Ready (#10248)

Signed-off-by: zwhzzz0821 <zwhzzz0821@users.noreply.github.com>
Co-authored-by: zwhzzz0821 <zwhzzz0821@users.noreply.github.com>
Co-authored-by: dengyunyang <584797741@qq.com>

### [549e63f](https://github.com/vllm-project/vllm-omni/commit/549e63f86a12aab93f3a844fa406c5381022a100)

- **作者**: Zeng Chuang
- **时间**: 2026-11-16T01:13:50Z
- **提交信息**: [Bugfix] Load MOSS-TTS checkpoint processors without AutoProcessor (#10377)

Signed-off-by: zengchuang <zengchuang3@huawei.com>
Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>

### [ebb350a](https://github.com/vllm-project/vllm-omni/commit/ebb350ad088be5b726a728cdf2e26ceaa8b3a11f)

- **作者**: Laceprndpm
- **时间**: 2026-11-16T00:02:24Z
- **提交信息**: [Bugfix] Enable Cache-DiT for SenseNova-U1 (#8248)

Signed-off-by: Laceprndpm <laceprndpm.64@gmail.com>
Signed-off-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>
Co-authored-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>

---
