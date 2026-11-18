# GitHub Stars 合并报告 - 2026-11-17

**合并日期**: 2026-11-18
**监控日期**: 2026-11-17
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


**报告日期**: 2026-11-18
**监控日期**: 2026-11-17
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2297
- **最后更新**: 2026-11-18T00:28:15Z

## 提交统计

- **昨日提交总数**: 7
- **提交者数量**: 6
- **主要提交者**: zhangxin.zzzzz, zpl1n, 帅喆

## AI分析总结

## VeOmni 昨日提交分析总结

### 1. 主要更新类型
- **功能新增**（3项）：序列并行优化跳过、NPU上下文并行、冻结特定模型参数
- **性能优化**（2项）：MoE SwiGLU反向融合、gated_mlp重构
- **文档更新**（2项）：Ascend指南简化、缺失功能文档补全

### 2. 关键变更点与项目方向的关系
- **分布式训练优化**：`conversation_list`上跳过inter-module SP all-gather（#1455）直接针对README强调的"Model-Centric Distributed Recipe"目标，减少通信开销
- **硬件生态扩展**：deepseek_v4上下文并行支持NPU（#1404）、Ascend文档简化（#1474）表明项目持续拓展国产AI加速芯片生态
- **性能工程深化**：MoE SwiGLU反向融合（#1467）和gated_mlp重构（#1462）聚焦核心算子级优化，提升大规模模型训练效率
- **训练稳定性**：冻结Qwen4-Exp PLE embedding表（#1354）针对特定模型架构的训练稳定性控制

### 3. 对项目的影响和潜在意义
- 通信优化和算子融合将直接降低多模态大模型分布式训练的成本和延迟
- NPU支持增强使项目更适合国内部署场景，降低对NVIDIA生态的依赖
- 文档完善提升项目可用性，有利于社区采用和贡献
- 整体上强化了"Any Modality"多模态训练框架的工程成熟度

### 4. 值得关注的技术点
- **跳过SP all-gather的条件机制**：在conversation_list场景下智能判断何时可跳过通信，是分布式效率优化的精细实践
- **MoE SwiGLU反向融合**：将多个反向传播操作融合为单一kernel，对MoE架构训练性能影响显著
- **gated_mlp行级归入MLP模块**：API/架构层面的重构，可能影响下游代码接口
- **Cursor Co-author标记**：#1455由AI辅助工具协作完成，反映字节内部AI编程工作流的应用

### 5. 对项目发展的综合影响
这批提交体现了VeOmni在**"分布式配方"**和**"性能优化"**两条主线上的持续迭代。结合README中"Scaling Any Modality Model Training"的定位，通信优化（SP跳过）、算子融合（MoE SwiGLU）、国产硬件支持（NPU）三管齐下，正在将论文中的分布式训练方法论转化为可大规模落地的工程实践。文档补齐和重构则为后续更复杂的多模态训练场景奠定基础，推动项目从研究原型向生产级框架演进。

## 详细提交记录

### [35e3bb7](https://github.com/ByteDance-Seed/VeOmni/commit/35e3bb741de398a5aa07d356cf8d9ba0015de190)

- **作者**: zpl1n
- **时间**: 2026-11-17T14:11:59Z
- **提交信息**: [docs] fix: simplify Ascend guides and supported tags (#1474)

### [4c1592e](https://github.com/ByteDance-Seed/VeOmni/commit/4c1592e81b849d9b54cfe7431719d17c0372b647)

- **作者**: Coach257
- **时间**: 2026-11-17T13:37:53Z
- **提交信息**: [ops, model] refactor: give the gated_mlp rows the MLP module (#1462)

### [5978a70](https://github.com/ByteDance-Seed/VeOmni/commit/5978a7040d44d41593ceb8a11bb9353beadf435e)

- **作者**: sunrise-bx
- **时间**: 2026-11-17T09:40:32Z
- **提交信息**: [docs] chore: Complete the Missing Feature Documentation (#1299)

### [dc39d4e](https://github.com/ByteDance-Seed/VeOmni/commit/dc39d4e6609a17d20b36cd80418559eaaed5853f)

- **作者**: Coach257
- **时间**: 2026-11-17T08:02:47Z
- **提交信息**: [omni, dist, parallel] feat: support skipping inter-module SP all-gather on conversation_list (#1455)

Co-authored-by: Cursor <cursoragent@cursor.com>

### [6761cdf](https://github.com/ByteDance-Seed/VeOmni/commit/6761cdfe7a23e49bc40ead870c6f82cb36e57237)

- **作者**: zhangxin.zzzzz
- **时间**: 2026-11-17T07:37:48Z
- **提交信息**: [ops, perf] refactor: fuse merged MoE SwiGLU backward (#1467)

### [ee61066](https://github.com/ByteDance-Seed/VeOmni/commit/ee6106699412f08348c44337c639ae58e0ae5344)

- **作者**: 帅喆
- **时间**: 2026-11-17T06:50:42Z
- **提交信息**: [model, ci] feat: allow deepseek_v4 context parallelism on NPU (#1404)

### [adfa928](https://github.com/ByteDance-Seed/VeOmni/commit/adfa9285bfe5596593fdfade570c9c8ce7bf36ac)

- **作者**: zhouyang
- **时间**: 2026-11-17T06:08:17Z
- **提交信息**: [model, optim] feat: freeze Qwen4-Exp PLE embedding tables (#1354)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-11-18
**监控日期**: 2026-11-17
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 3011
- **最后更新**: 2026-11-17T15:07:26Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Yang Yong (雍洋), Bilang ZHANG

## AI分析总结

## 提交分析总结（ModelTC/LightX2V）

### 1. 主要更新类型
- **功能新增**：配置系统增强（request_defaults 支持）
- **性能优化**：H3 因果推理路径的执行效率提升
- 本次批次无 Bug 修复或文档变更，属于"能力扩展 + 效率打磨"的组合。

### 2. 关键变更点及与项目方向的关系
- **request_defaults 进入配置体系**：为用户配置提供统一的默认值来源，减少重复字段书写，使多任务/多模型的配置管理更集中。这与 LightX2V 作为"推理框架"的定位一致——框架不仅要跑得快，还要让配置和部署足够轻量、可维护。
- **H3 因果推理优化**：针对特定架构（H3 类模型）的因果（causal）推理做性能压榨，直接服务项目核心目标——**轻量视频生成推理**。视频生成推理的瓶颈往往在长序列注意力与去噪循环，因果化/结构化推理是降本增效的关键抓手。

### 3. 对项目的影响与潜在意义
- 配置层面的默认值机制降低了新用户与新模型接入的门槛，有利于社区贡献者以更少样板代码提交配置，间接扩大生态。
- H3 优化可能带来显存占用或吞吐的可见改善，提升 LightX2V 在端侧/低资源场景的竞争力。
- 两者结合体现维护策略：在扩展功能面的同时持续回收性能债务，符合轻量推理框架的长期演进节奏。

### 4. 值得关注的技术点
- request_defaults 的作用域与优先级设计（用户配置 vs 模型默认 vs 框架默认的覆盖顺序），值得后续关注是否有文档与示例同步。
- H3 因果推理优化的具体手段（KV 缓存复用、算子融合、批处理调度等）可作为其他架构优化的模板，观察是否会在后续提交中推广到更多模型。
- 两提交分别对应 PR #1725、#1724，说明项目以 PR 驱动、拆分粒度清晰的协作模式推进。

### 5. 基于 README 背景对项目发展的影响
README 明确 LightX2V 的目标是**轻量视频生成推理框架**，配套双语文档与 Apache 2.0 许可，走的是开放、国际化路线。本次提交从"配置易用性"和"推理性能"两个维度同时推进：配置默认值让框架更易被集成与二次开发，H3 优化则持续兑现"Light"（轻量）这一品牌承诺。二者共同强化了项目在易用性与效率上的双重护城河，有助于吸引更多模型接入与工业落地。总体而言，这批提交是框架走向成熟期的典型增量演进，短期提升用户体验与运行效率，长期为多模型、多场景的规模化部署奠定基础。

## 详细提交记录

### [211495f](https://github.com/ModelTC/LightX2V/commit/211495fe504bfa0238c832fa1a501487486fb334)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-11-17T14:32:46Z
- **提交信息**: Support request_defaults in configs (#1725)

### [2ba2139](https://github.com/ModelTC/LightX2V/commit/2ba2139dcfa9fd5a725e5507b7a071331b835b76)

- **作者**: Bilang ZHANG
- **时间**: 2026-11-17T12:17:45Z
- **提交信息**: perf: optimize H3 causal inference (#1724)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-11-18
**监控日期**: 2026-11-17
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


**报告日期**: 2026-11-18
**监控日期**: 2026-11-17
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6954
- **最后更新**: 2026-11-18T02:39:09Z

## 提交统计

- **昨日提交总数**: 37
- **提交者数量**: 25
- **主要提交者**: Po-Han Huang (NVIDIA), Brian K. Ryu, Adrian Stanescu

## AI分析总结

# FlashInfer 昨日提交总结（37 个提交）

## 主要更新
昨日更新以性能优化（约 10 项）与 Bug 修复（约 12 项）为主，辅以功能新增（约 8 项）和 CI/基础设施（3 项），无大规模重构。脉络清晰：战略瘦身回归推理本源、低精度算子补齐、生产级加固。覆盖 GEMM、MoE、注意力、采样、GDN、autotuner 与分布式通信等核心模块。

## 关键变更
- **移除 CAKE 训练内核（#9326）**：删除约 4870 个文件（约 211MB），涉及 31 个训练后端包、公共模块、测试、基准与文档，内核迁移至 cuDNN Frontend 与 radixark/miles-ext-kernels，消除 v0.7.3 引入训练代码造成的方向偏移。
- **性能优化**：Cake GDP 静态解码程序在 H100/B200/GB300 提速 1.6~1.8x geomean；Sage FP8 块稀疏注意力双缓冲与 tile 重叠在 B200 提速约 7%；SM90 MoE 后端消除冗余映射；批量不变注意力在位级约束下提升 prefill 性能；split-K 调优峰值内存从 1595 MiB 降至 361 MiB（-77%）。
- **正确性修复**：PTX 内存模型同步顺序、PDL `griddepcontrol.wait` 前的输入读取时序、split-K wave 归一化、MoE 路由整数溢出与 EP 索引错误、GDN 尾块 NaN/Inf 跨请求污染、GEMM 维度延迟失败，以及 TGV GEMM 的 TMEM 释放竞态（#8787，`tcgen05.dealloc` 早于 epilogue 的 `tcgen05.ld`）。
- **功能新增**：批不变 MXFP8×MXFP4 GEMM（#9366，`flashinfer.mm_mxfp8_mxfp4`）、NVFP4 epilogue 量化的 masked grouped GEMM、CUDA 图安全的 NVFP4→FP8 token-sparse 转换、SM120/107 MegaMoE（W4A8 nosync）内核、batch-invariant 采样的 `log_softmax(out_dtype=)` 与 `sampling_from_logits(temperature=)` API、destination-major DCP 输入。
- **生态与 CI**：autotuner 支持有状态进程组适配 vLLM 弹性 EP、修复 `torch.compile` 回归（SGLang 暴露）、sccache 种子工作流降低冷构建开销、Windows arm64 构建与分片运行器系统性移植。

## 项目影响
- **定位回归、维护减负**：训练代码移除大幅缩减仓库体积，降低认知成本，强化"推理专家"的社区形象。
- **生产可靠性提升**：EP/CP 边缘路径、PDL 时序、多请求隔离与 TMEM 竞态修复降低 vLLM/SGLang 崩溃风险。
- **长序列吞吐改善**：MoE 激活持久化核（#9329）在 32–128 token 区间提速 1.3×–2.5×，在 256–2048 token 上下文行区间提速 3.2×–13.2×，对长上下文推理有直接生产价值。
- **能力扩展**：NVFP4/MXFP4 与 SM100+/SM120 适配巩固 Blackwell 生态；采样 API 向 verl、Megatron-Core 等 RL 训练延伸，项目从纯推理库向训练-推理协同基础设施演进。
- **破坏性变更**：DCP 输入轴布局改变，调用方需迁移。

## 技术关注点
- **批不变性的严格契约**：输出比特仅依赖输入值、块缩放因子、权重形状与架构，不受批量、行位置、分发配置或 SM 数量影响；SM100/103 要求 K 为 128 倍数、SM107 要求 32 倍数，不满足时抛出 `BatchInvariantUnsupportedError` 而非静默回退。
- **PTX 级同步修复**：mbarrier parity 语义分析（parity 1 指向紧邻前一相位）以及输出位相同、只能靠生成 PTX 静态测试验证的修复，是排查 GPU 竞态的典范；`0 * NaN = NaN` 陷阱最终在加载阶段用张量映射裁剪。
- **持久化核 + 设备端工作分配**：MoE 激活从每列块一 block 改为每 SM 最多 8 个 block，由设备端依据路由结果动态划分，是解决 expert parallelism 下无效计算的经典手法。
- **工程纪律**：位级一致性约束下的可复现调优、Job Object 替代 `taskkill /T` 解决 Windows 后代进程追踪、Layered 校验将约束上移至 Python 前置改善 API 可用性。

## 整体趋势
项目正处于功能扩张转向生产级加固的阶段：在多架构（SM90/100/103/120）× 多场景（prefill/decode/MTP）× 多精度（FP8/FP4/bf16）纵深覆盖的同时，通过战略收缩、正确性修复与跨平台基建夯实可靠性，持续巩固其作为主流推理框架底层内核的竞争力。

## 详细提交记录

### [97f4577](https://github.com/flashinfer-ai/flashinfer/commit/97f4577f8eb2166037c37424387cbddc0ebcd0d0)

- **作者**: Martín el Cheikh
- **时间**: 2026-11-17T23:41:07Z
- **提交信息**: fix(gemm): normalize base_waves by CTA slots in mm_bf16_fp4 split-K gate (#7746)

## 📌 Description

In `CuteDslBf16Fp4Runner.get_valid_tactics` (#4038),
`split_reduces_makespan` gates split-K tactics (`splits in (2, 4, 8)`)
so they are only offered to the autotuner when splitting shortens the
grid's last wave by at least 25%:

```python
slots = sm_count * cfg[6]
base_waves = -(-tiles // sm_count)
split_waves = (-(-tiles * splits // slots)) / splits
return split_waves <= 0.75 * base_waves
```

When `cfg[6] == 2` (`occupancy = 2`), `slots = 2 * sm_count`. Because
`base_waves` divided by `sm_count` (1 CTA/SM) while `split_waves`
divided by `slots` (2 CTAs/SM), the ratio `split_waves / base_waves`
converged to `0.50 <= 0.75` for arbitrarily large `m_opt`.

As a result:
- `occupancy=2` split-K tactics (`splits = 2, 4, 8`) bypassed the 25%
wave-tail guard on all multi-wave prefill buckets (`m_opt = 256..8192`).
- Profiling `splits = 8` on large prefill buckets allocated a persistent
global buffer (`mm_bf16_fp4_split_k_partial` of size `k_splits * m * n *
4` bytes, e.g. `768 MiB` at `M=2048, N=12288` and `3..4 GiB` at
`M=8192`), inflating peak VRAM during `autotune()` and exposing
multi-wave shapes to warm-L2 over-ranking.

This PR normalizes `base_waves` by `slots` (`base_waves = -(-tiles //
slots)`) so unsplit and split wave counts are compared at the same CTA
occupancy:
- Underfilled decode grids (`tiles <= sm_count`, where `ceil(tiles /
sm_count) == ceil(tiles / slots) == 1`, such as `m=1, n=2048, k=7168`
and `m=1, n=4096, k=4096`) keep the exact same `occ=1` and `occ=2`
split-K candidates as before.
- Multi-wave prefill buckets (`base_waves >= 4`, `tiles > 3 * slots`)
properly reject split-K across all occupancy levels.

Measured on RTX 5090 (`SM 12.0`, 170 SMs) with `autotune()` on `M=2048,
K=4096, N=12288`:
- Peak allocated memory drops from **1595.00 MiB** to **361.00 MiB**
(-77.4%).
- Peak reserved memory drops from **3720.00 MiB** to **1008.00 MiB**
(-72.9%).
- Autotune wall time for the shape drops from **19.38 s** to **14.80 s**
(-23.6%).

## 🔍 Related Issues

Follow-up to #4038.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

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

  Suggested CI test targets: `tests/gemm/test_mm_bf16_fp4.py`

New tests:
- Added `test_cute_dsl_autotune_split_k_makespan_gate` in
`tests/gemm/test_mm_bf16_fp4.py` verifying that underfilled decode grids
offer both `occ=1` and `occ=2` split-K tactics (including `m=1, n=4096,
k=4096` on 84 SMs where `splits=2` fits in one wave only at `occ=2`),
while multi-wave prefill buckets (`m_opt in (256, 2048, 8192)`) reject
split-K across 48/84/170/188-SM parts.
- Full `tests/gemm/test_mm_bf16_fp4.py` suite passes on RTX 5090 (SM
12.0).

## Reviewer Notes

- Also resolves one of the factors behind the `occ=2` split-K
over-ranking on `m=1, n=4096, k=512` on 48-SM parts (DGX Spark) noted in
#4038: at `64` tiles on `48` SMs (`slots = 96` at `occ=2`), `base_waves`
is `1` wave of 96 slots rather than `2`, so `occ=2, splits=2` (`128`
tiles spilling into 2 waves of 96 slots) is no longer admitted as a
makespan reduction.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Corrected workload estimates used to select execution strategies for
supported GPU matrix multiplications. Split-work choices now better
account for GPU occupancy across different grid sizes, including
underfilled decode workloads. This can change which execution strategy
is selected for some workloads; public interfaces remain unchanged.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: martin el cheikh <martinelcheikh@gmail.com>

### [2b6e1a4](https://github.com/flashinfer-ai/flashinfer/commit/2b6e1a42943d67e13f019da797fae132f9c73e26)

- **作者**: Xu
- **时间**: 2026-11-17T23:40:21Z
- **提交信息**: fix(gemm): narrow the masked grouped GEMM arm to SM100/SM103/SM107 (#9252)

## 📌 Description

`grouped_gemm_nt_masked` picks its kernel with `elif major >= 10`
(`flashinfer/gemm/kernels/grouped_gemm_masked_wrapper.py:259`, main @
`3bb1e9c9`) and hands
the tensors to the Blackwell cute-dsl kernel. That kernel disagrees with
the arm two layers
inside itself:

```python
# gemm/kernels/grouped_gemm_masked_blackwell.py:659-661, in the class constructor
supported_sm_versions = ["sm_100", "sm_103", "sm_107"]
assert sm_version in supported_sm_versions, (
    f"{supported_sm_versions} are the only supported SM versions for cute-dsl backend, "
    f"but encountered {sm_version}"
)
```

and the value it checks is one this wrapper builds from the device it is
running on:
`sm_version=f"sm_{major}{minor}"`
(`grouped_gemm_masked_blackwell.py:3734`).

So on SM120/SM121 the wrapper's `major >= 10` says yes, the kernel's own
triple says no, and
the user gets a bare `AssertionError` from inside a kernel class
constructor — naming
neither the API that was called nor the device that was rejected.
Nothing was ever runnable
there: the kernel imports `from cutlass.cute.nvgpu import cpasync,
tcgen05` (`:42`) and its
docstring describes `tcgen05.mma` plus TMEM traffic (`:529-540`), the
datacenter-Blackwell
instruction path. FlashInfer's own SM120 block-scaled GEMM is built the
other way —
`gemm/kernels/dense_blockscaled_gemm_sm120_b12x.py` takes its MMA atom
from the warp-level
path (`from cutlass.cute.nvgpu.warp.mma import Field as WarpField`,
`:48`) and its only
`nvgpu` import besides that is `cpasync` (`:47`); it never imports
`tcgen05`. So widening the
arm is not the fix here; refusing at the entry is.

The change is one line of routing plus the tail message:

```python
elif (major, minor) in ((10, 0), (10, 3)):      # was: elif major >= 10:
```

SM107 is not in that tuple because it already has its own arm above it
(`:192`), and SM110
already has its own refusal at `:189`, which this PR leaves untouched.

The triple `(10, 0)`, `(10, 3)`, `(10, 7)` is not invented here. It is
what the wrapper's own
documentation promises in three places — "supporting both Blackwell
(SM100/SM103) and Rubin
(SM107)" (`:20-21`), the kernel map (`:30-31`: `SM100/SM103 (Blackwell):
grouped_gemm_masked_blackwell.py`, `SM107 (Rubin):
grouped_gemm_masked_rubin.py`), and the
public docstring "Masked, batched, block-scaled GEMM on Blackwell
(SM100/SM103) and Rubin
(SM107)" (`:68`, `:71`) — and it is what the existing suite already
skips on:

```python
# tests/utils/test_fp8_quantize.py:1341
pytest.skip("grouped_gemm_nt_masked MXFP8 requires SM100/SM103/SM107")
```

so after this PR the entry, the kernel and the suite state the same
rule. (The same file's
MXFP8-quant helper at `:72` still uses `major >= 10`, because
`mxfp8_quantize` itself really
is "SM100 or newer" — that difference is about the quantize API, not
about this kernel, and
this PR does not touch it.)

The tail raise used to read "only supported on SM100+
(Blackwell/Rubin)". `SM100+` is the
wording that made the over-wide arm look intentional, and it is also the
message SM80/SM90
callers get, so it now names the triple and the reason:

```
ValueError: Masked grouped GEMM is only supported on SM100, SM103 and SM107 (the cute-dsl
kernels import tcgen05/TMEM from cutlass.cute.nvgpu, which this file builds for SM100-family
targets only), got SM120
```

Devices whose result changes: SM120/SM121 (assert inside a constructor →
refusal at the
entry) and SM80/SM90/anything else in the tail (same refusal, different
sentence). SM100,
SM103, SM107 and SM110 are routed exactly as before, which is what the
containment cases in
the new test pin.

## 🔍 Related Issues

- #3170 — DGX Spark (SM121) Current Support Audit (`arch: sm12x`, `op:
gemm`). It records the
useful rule that SM120 and SM121 are architecturally the same for
FlashInfer's purposes and
that hardcoded `sm_120` checks are over-restricting; this PR is not that
class of bug. Here
the kernel genuinely cannot run on 12.x (no `tcgen05`/TMEM path), so the
correct change is
the entry refusal, and the audit is where actual SM12x masked-GEMM
coverage should be
  tracked.
- #6354 (closed) — same file family, about *rejected candidates printing
`[DSL ERROR]` text
that looks like a failure. Same underlying complaint from the other
side: an architecture
judgment made deep inside a kernel surfaces as something that does not
read like a
  supported-range statement.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

On the second box: this machine carries a mandatory org-level
`core.hooksPath` (credential
scan), so `pre-commit install` refuses to write into `.git/hooks`; the
hooks were therefore
invoked explicitly. On the third: I ran them scoped to the two paths
this PR touches rather
than across the tree, because `--all-files` would spend the whole check
on files this PR does
not change —

```
pre-commit run --files flashinfer/gemm/kernels/grouped_gemm_masked_wrapper.py tests/gemm/test_grouped_gemm_masked_arch_gate.py
```

and every applicable hook passed — `mypy`, `ruff check`, `ruff format`,
fix end of files,
mixed line ending, trim trailing whitespace, Tabs remover, CRLF
end-lines remover, check for
added large files, check for case conflicts, check for merge conflicts —
while `clang-format`,
`fix requirements.txt`, `ruff check (SM12x import order)` and the
experimental test scope
selftest were skipped for having no files to check.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: n/a — one routing arm and one message in one wrapper, plus a new
test file.

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust):
  `tests/gemm/test_grouped_gemm_masked_arch_gate.py`

The new file stubs `get_compute_capability` and `get_num_sm`, and
injects stub modules for
both kernels through `sys.modules`, so it needs no GPU (the tensors it
passes are CPU zeros —
the wrapper only forwards them to whichever kernel the branch selects)
and it never imports a
real cute-dsl kernel.

- 4 refusal cases — `(12, 0)`, `(12, 1)`, `(11, 1)`, `(9, 0)` — assert
the new `ValueError`.
These are the cases that are red on main: today `(12, 0)`/`(12,
1)`/`(11, 1)` sail into the
  Blackwell arm and `(9, 0)` reaches the old tail sentence.
- 1 case pins SM110's pre-existing refusal (`(11, 0)` → "SM110 is not
supported for cute-dsl")
  so this PR cannot silently take it over.
- 2 cases assert `(10, 0)`/`(10, 3)` still reach the Blackwell kernel,
and check that the
resolved `sm_count` is passed on — i.e. that narrowing the arm did not
break the devices it
  is meant to keep.
- 1 case asserts `(10, 7)` still reaches the Rubin kernel.

The two files in this pair are independent: this one is 8 cases, #9251's
is 10 cases and
reads `10 passed` against a patched tree on both SM120 and SM90 (`5
failed, 5 passed`
unpatched). Full readings for this file are the A/B/C table in Reviewer
Notes.

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

**Focus on one line**: `elif major >= 10:` → `elif (major, minor) in
((10, 0), (10, 3)):`.
Everything else in the product diff is the tail message and a comment
recording where the
triple comes from.

**Measurements.** All three arms ran on 8× RTX PRO 5000 (SM120) against
the image's own
flashinfer 0.7.1, with the wrapper patched in a shadow copy of the
installed package. The
patched file is dereferenced out of the symlink tree before writing, so
site-packages was
never modified: `md5sum -c` read back `OK` immediately after patching
and again at the end.
The serving engine in that container was not touched (9 sglang processes
at the end).

| arm | what differs | result |
|---|---|---|
| A | unpatched wheel | `4 failed, 4 passed` — the 4 refusals red, the 4
containment cases green |
| B | wrapper patched (`(10, 0)`/`(10, 3)` arm + tail message) | `8
passed` |
| C | B, plus `cutlass.utils.rubin_helpers` made unfindable | `8 passed`
|

Arm C is the answer to the review point on the SM107 case. The old
version of that case did
`from flashinfer.gemm.kernels import grouped_gemm_masked_rubin`, and the
rubin kernel module
pulls `import cutlass.utils.rubin_helpers` at its own line 23 — so on a
DSL below the repo's
4.8 floor the case errored before it could check anything. Under C the
old file reads
`5 failed, 3 passed` with `ModuleNotFoundError` on that case, while the
injected-stub version
still reads `8 passed`. C also exercises the repo's own gate for this:
`cute_dsl/availability.py:86` probes
`find_spec("cutlass.utils.rubin_helpers")` and
`gemm/kernels/__init__.py:50` skips the rubin kernel when it returns
`None`, which is exactly
what the simulation produces (`availability: False`, `rubin kernel in
sys.modules: False`).
The stub is the same mechanism the Blackwell case already used, so the
file now depends on
neither a GPU nor any particular CUTLASS DSL version.

The earlier revision of this PR also ran the pair on an H20 (SM90);
those readings were taken
against the previous shape of these two test files and are superseded by
the table above.

**Limits, stated plainly.**
- Capability is stubbed in these cases, so they prove the branch
decision, not that any
kernel runs. We have SM120 and SM90 hardware; SM103/SM107 coverage here
is the containment
  assertion that the route is unchanged, not a run on those devices.
- Refusing SM120/SM121 is a *diagnosis* fix, not SM12x support: a 12.x
caller still cannot run
masked grouped GEMM after this PR, and getting it to run means an SM12x
kernel — the shape
of that work is what `gemm/kernels/dense_blockscaled_gemm_sm120_b12x.py`
already shows for
the dense case, consumed from
`tests/gemm/test_cute_dsl_blockscaled_gemm.py` for the grouped
  one. That is #3170's scope, not this PR's.
- One adjacent sentence this PR makes stale, deliberately left alone:
`tests/utils/test_fp8_quantize.py:69-70` justifies its `major >= 10`
helper with "(the
grouped wrapper raises for `major < 10`)". That parenthetical describes
the pre-patch arm.
The helper itself stays correct — it gates `mxfp8_quantize` /
`mxfp8_grouped_quantize`, which
really are SM100-or-newer, and none of its skip decisions change — so I
kept the diff to the
one line of routing. Say the word and I will reword that clause in the
same PR.
- The shadow-tree patch is the same minimal edit applied to the wheel's
own wrapper file, not
  a whole-file swap from main.
- `major == 10 and minor not in (0, 3, 7)` now falls to the tail raise
instead of into the
Blackwell kernel. No such device is known; if one appears, the message
names the accepted
  triple rather than asserting two layers down.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Corrected architecture selection for grouped masked matrix
multiplication. SM100 and SM103 use the Blackwell path, while SM107 uses
the Rubin path.
* Unsupported architectures now receive an error that identifies the
supported architectures and reports the detected architecture. Other
hardware generations are no longer incorrectly routed through the
Blackwell path.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [6445777](https://github.com/flashinfer-ai/flashinfer/commit/64457773858724f24c4f2c028ab486be38d50954)

- **作者**: Itay Alroy
- **时间**: 2026-11-17T23:22:57Z
- **提交信息**: fix(autotuner): support stateless process groups (#9472)

get_backend() fails for stateless process groups, which vLLM uses for
Elastic EP and fault tolerance. This prevents FlashInfer
autotuning with these groups (see
https://github.com/vllm-project/vllm/pull/65307 for more info)

Select the collective device from the group's supported devices instead
of relying on PyTorch's global registry.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Distributed autotuning now selects the appropriate device for
collective operations based on the process group configuration,
improving reliability across supported distributed setups. This helps
avoid device mismatches during tuning and profiling.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Itay Alroy <ialroy@nvidia.com>
Co-authored-by: Alex Yang <aleyang@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [edcb2c8](https://github.com/flashinfer-ai/flashinfer/commit/edcb2c869f5b080ff396885ff88a8f9d7a27c680)

- **作者**: Dongha
- **时间**: 2026-11-17T23:22:52Z
- **提交信息**: feat(comm): destination-major DCP inputs and token masks (#6483)

## 📌 Description

The NCCL fused DCP operation from #4929 expects the destination axis
after the head axis. Contiguous attention outputs grouped by destination
therefore need a layout copy before calling it.

This PR changes `decode_cp_a2a_lse_reduce` to accept contiguous
destination-major inputs:

- Accept `partial_o` `[batch, cp_size, heads, head_dim]` (FP16/BF16) and
`partial_lse` `[batch, cp_size, heads]` (FP32), returning `[batch,
heads, head_dim]`. `cp_size` is the context-parallel group size; its
axis contains slices destined for the CP ranks. The operation does not
shard the `heads` axis. Arbitrary matching leading dimensions remain
supported as `[..., cp_size, heads, head_dim]` and `[..., cp_size,
heads]`.
- Add optional keyword-only `mask`: contiguous CUDA bool `[batch]`,
supported for 4-D `partial_o` and 3-D `partial_lse`. A `False` entry
sends zero partial output and `-inf` LSE without reading those inputs,
while participating in collective synchronization. Nonfinite LSE
contributes no weight and its partial output is not read; if every shard
contributes no weight, the output is zero.
- Retain the synchronization change: each block snapshots the
device-side epoch, and block 0 advances it after the receive-side grid
synchronization. This removes the initial grid synchronization while
preserving system-scope fences and release/acquire flags.
- Update the existing tests, trace template/example and benchmark for
the new input contract.

This replaces the previous strided-input proposal with fixed contiguous
addressing. **It changes the input-axis contract from #4929**; callers
must migrate. Compatible contiguous producer tensors can be viewed in
destination-major order without a copy. Independently strided LSE and
padded O storage still require contiguous preparation. Downstream
vLLM/SGLang adapters are separate from this PR.

The commits remain split into layout/mask support, synchronization, and
tests.

### Performance

8×H100, DCP=8, BF16, 16 total heads, D=512, base-2 LSE. The table
measures the SGLang adapter's hot-cache CUDA graph combine path.

| Batch | Before barrier change (µs) | This PR (µs) | Latency reduction
|
|---:|---:|---:|---:|
| 1 | 12.915 | 11.906 | 7.81% |
| 4 | 16.423 | 15.330 | 6.65% |
| 16 | 18.026 | 16.820 | 6.69% |
| 64 | 20.803 | 19.714 | 5.23% |

## 🔍 Related Issues

- Extends the NCCL-based implementation in #4929.
- Related feature request: #4575.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

Git hooks are installed. `pre-commit run --all-files` passed on HEAD
`143d0e8a5` in an isolated worktree without modifying files; scoped
checks and `git diff --check` also passed.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] 8×H100, DCP=8: 47 tests passed per rank, zero skips.

```sh
python -m torch.distributed.run --standalone --nproc-per-node=8 \
  -m pytest tests/comm/test_dcp_lse_reduce.py -q -s -ra -x
```

## Reviewer Notes

- Review independent O/LSE strides, masked payloads and epoch reuse.
Each workspace requires one ordered CUDA stream and a supported NCCL LSA
domain.
- Performance isolates synchronization with identical mask/stride
support. Earlier downstream model accuracy failures and
allocator/teardown warnings remain unresolved.

cc @kwen2501 

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

- **New Features**
- Added an optional batch mask to distributed LSE reduction. Masked rows
contribute zero output, and rows with no valid contributions return
zero.
  - Added support for batched, destination-major input layouts.
- **Bug Fixes**
  - Non-finite LSE values are now excluded from output reduction.
  - Improved workspace reuse across changing inputs and shapes.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Dongha Yoon <dyoon@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [8c21ca5](https://github.com/flashinfer-ai/flashinfer/commit/8c21ca5e42d2b19e14bb03658c6b2c15adc7a1b9)

- **作者**: akhilg-nv
- **时间**: 2026-11-17T23:11:03Z
- **提交信息**: fix(gemm): order the stage release, output stores and loader exit of the warp split-K BF16 GEMM (#8081)

[by Claude Code]

<!-- .github/pull_request_template.md -->

## 📌 Description

Fixes three synchronization orderings that the PTX memory model does not
guarantee in `CpAsyncWarpSplitKKernel`
(`flashinfer/gemm/kernels/dense_bf16_gemm_warp_splitk.py`, the warp
split-K runner of `mm_bf16(backend="cute-dsl")`); details in #8080.
Tiles, K slices, MMA order, reduction order and rounding are unchanged,
so outputs are bitwise identical to main.

1. **Output stores under PDL.** Only the activation-loader warps
executed `griddepcontrol.wait`; the warp that stores the output was
ordered after the prerequisite grids only through the loaders'
asynchronous `cp.async.mbarrier.arrive`. With `use_pdl`, the storing
warp now executes `griddepcontrol.wait` before its stores. The
prerequisite grids have already completed by then (the stores depend on
activation tiles that the loaders read after their own wait), so it
never waits on a running grid.
2. **Stage reuse.** One elected lane per compute warp arrived on a
stage's empty barrier (count 4), but `mbarrier.try_wait` orders only the
arriving threads' prior accesses, so the other lanes' `ldmatrix` reads
were not ordered before the loaders' next `cp.async` into the stage.
Every compute lane now arrives (count 4 x 32).
3. **Loader exit.** Loader threads exited with `cp.async` copies in
flight, which the PTX ISA does not define. Each loader path now ends
with `cp.async.wait_all` (on the activation-loader path after
`launch_dependents`, so the dependent launch is not delayed).

New test `tests/gemm/test_mm_bf16_warp_splitk_sync.py` compiles the
kernel on the host for sm_100a and sm_103a (no GPU needed) and checks
the three orderings in the generated PTX, as
`tests/moe/test_b12x_w4a16_grid_barrier.py` does for its barrier. These
orderings change no result, so a replay test cannot tell the two kernels
apart.

The fix was validated on Vera Rubin NVL72 (SM107) on v0.7.2 (the same
three hunks: #6833 changed only `autotune_tactics` in this file) and
re-validated on B300 (SM103) on main e7ee9232e.

### Performance (kernel microbenchmark)

In situ: a CUDA graph of [predecessor -> GEMM -> successor] layers with
distinct weights in every layer (about 512 MiB of weights per graph; the
cap of 78 layers gives 146 MiB at 160 x 6144 and 468 MiB at 6144 x 512),
`pdl=True`, FlashInfer RMSNorm or SiLU-and-mul before and after the GEMM
(a BMM before 6144 x 4096). Each run pairs this PR's kernel against
main's kernel, loaded as separate modules, with a second copy of main's
kernel as an A/A control: 21 repeats x 10 replays per arm, arm order
rotated every repeat. Per call = (PR - main) / (the GEMM's marginal
in-graph time).

**B300, the default tactic** (what `mm_bf16(backend="cute-dsl")` runs
without autotuning), 16 decode shapes, 4-5 runs per shape:

| N x K | M | tactic (output, token, k tile, stages, B loaders) | main
(us per layer) | PR - main (us) | per call |
|---|---|---|---|---|---|
| 6144 x 4096 | 1 / 4 / 5 | (16, 8, 256, 9, 2) | 14.7 / 15.3 / 15.3 |
-0.12 to -0.01 | -1.2% to -0.1% |
| 6144 x 4096 | 20 | (16, 32, 256, 4, 2) | 19.8 | -0.13 to -0.09 | -0.9%
to -0.6% |
| 2624 x 6144 | 1 / 4 / 5 | (32, 8, 256, 11, 2) | 9.9 / 10.6 / 10.6 |
-0.19 to +0.01 | -3.0% to +0.2% |
| 2624 x 6144 | 20 | (32, 32, 256, 6, 2) | 13.0 | +0.00 to +0.06 | +0.0%
to +0.7% |
| 6144 x 512 | 1 / 4 / 5 | (16, 8, 128, 4, 1) | 6.1 / 6.6 / 6.6 | +0.01
to +0.03 | +0.2% to +0.9% |
| 160 x 6144 | 5 | (16, 8, 256, 16, 2) | 7.1 | -0.20 | -5.1% to -4.9% |
| 1024 x 6144 | 1 / 4 / 5 | (16, 8, 256, 16, 2) | 6.9 / 7.7 / 7.8 |
-0.28 to -0.23 | -6.2% to -5.1% |
| **1024 x 6144** | **20** | **(16, 16, 256, 13, 2)** | 8.5 | **+0.40 to
+0.43** | **+7.9% to +8.4%** |

**B300 at SM107's default tactics** (`default_tactic` depends on the SM
count; these are the tactics it picks on Vera Rubin NVL72 for the same
shapes. On B300 all of them except (32, 8, 128, 4, 1) fall outside the
autotune space, so they were passed explicitly), 5 runs: M <= 5 with
token tile 8 is 2.7% to 4.8% faster per call at 6144 x 4096 and 2624 x
6144; slower in every run are 2624 x 6144 M=20 at (16, 32, 256, 9, 2)
(+3.8% to +4.6%), 6144 x 4096 M=20 at (32, 32, 256, 6, 2) (+2.2% to
+2.5%) and 6144 x 512 at (32, 8, 128, 4, 1) (+1.9% to +3.1%).

**Vera Rubin NVL72 (SM107)**, v0.7.2 with the same three hunks, the 16
shapes at SM107's default tactics, 2 runs: -4.5% to +0.9% per call in
the first run and -4.4% to +1.4% in the second; 15 of 16 shapes stay at
or below +0.9% in both, and 1024 x 6144 M=20 measured +0.1% and +1.4%.

Attribution (B300, single-fix variants of the kernel, same bench, one
run): the speedups at token tile 8 come mostly from `cp.async.wait_all`
(also seen on SM107; the mechanism is not established). Where the fix
costs most, the per-lane empty-barrier arrive is most of it: +0.36 us of
the +0.41 us at 1024 x 6144 M=20 (16, 16, 256, 13, 2), and +0.56 us of
+0.61 us at 2624 x 6144 M=20 (16, 32, 256, 9, 2). In the sm_103a SASS
that arrive is a `SYNCS.ARRIVE.TRANS64.A1T0` executed by every lane; on
SM107 it lowered to a single warp-uniform `USYNCS.ARRIVE.TRANS64.ACT0`.
At 6144 x 4096 M=20 (32, 32, 256, 6, 2) the cost comes mostly from items
1 and 3 instead. See the Reviewer Notes for a cheaper form of item 2.

## 🔍 Related Issues

Fixes #8080

Related: #7591 (open) makes the compute warps wait before the bias read
when the kernel has a bias. It edits nearby lines of the same file; the
two changes merge without conflict. With both, a kernel with a bias
waits twice in the storing warp, and the second wait returns without
waiting on any grid.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues. (Run on the two changed files with
`pre-commit run --files`; every hook passed.)

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
reviewers may adjust): `tests/gemm/test_mm_bf16_warp_splitk_sync.py
tests/gemm/test_mm_bf16.py tests/gemm/test_mm_mxfp8.py`

On B300 (CUDA 13.0, torch 2.14.1+cu130, nvidia-cutlass-dsl 4.8.0), this
branch and main side by side:
- `tests/gemm/test_mm_bf16_warp_splitk_sync.py` (new): 6 passed; on
main, 6 failed. With one fix removed or partly removed (6 variants, run
on a host without a GPU), only that fix's check fails, for sm_100a and
sm_103a.
- `tests/gemm/test_mm_bf16.py -k cute-dsl` (PDL on, off and `None`,
bias, autotune): 7 passed, the same as main.
- `tests/gemm/test_mm_mxfp8.py`, its CuTe-DSL low-M, PDL-producer, PDL
CUDA-graph, scale-encoding and stale-tactic cases (the MXFP8 kernel
imports this file's helpers): 23 passed, the same as main.
- Element-wise against an FP32 matmul of the same BF16 inputs, 19 shapes
x PDL on / off (the 16 decode shapes above at SM107's default tactics
plus the three warp split-K shapes of `test_mm_bf16.py` at the default
tactic), poisoned outputs, two input sets, tolerance |out - ref| <= 2^-7
|ref| + 2^-9 rms(ref) set before the runs: 38/38 pass (worst error 0.44
of the bound). The output is bitwise equal to main's in 38/38, and in
every benchmark run above, at both tactic sets. The checker flags 76/76
injected errors (shifted weight row, dropped last K tile, 2% scale, one
unwritten row).
- PDL chain (CUDA graph: a producer that triggers its dependents first
and writes its output late -> GEMM -> a consumer that waits, buffers
poisoned before each replay): 0 wrong outputs in 1,900 replays. A
consumer without `griddepcontrol.wait` reads poison at all 19 `pdl=True`
shapes, so the test can see a missing wait.
- compute-sanitizer memcheck, initcheck and synccheck on 4
instantiations and one chain: no device errors (memcheck also lists 7
`cuGetProcAddress` probes that fail while the Python driver bindings
import).
- Generated PTX of 11 instantiations x PDL on / off, from the runtime
JIT build on sm_103a and the host build on sm_100a / sm_103a (the two
sm_103a builds are identical apart from comments, debug lines and symbol
names): with PDL, a second `griddepcontrol.wait` after the split-K
reduction barrier and before the first `st.global`; in the 8 stage-reuse
instantiations, no `elect.sync` and an empty-barrier count of 128;
`cp.async.wait_all` on both loader paths. The same checks report the
three items as not fixed on main.

On Vera Rubin NVL72 (SM107), v0.7.2 with the same three hunks:
element-wise at the 16 decode shapes, PDL on and off (32/32), bitwise
equal to v0.7.2, PDL chain (0 wrong in 1,600 replays), memcheck /
initcheck / synccheck with no errors in FlashInfer kernels, and the same
PTX checks.

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

- **A cheaper form of item 2 on SM103, if that matters more than strict
compliance.** Keep the elected arrive (count 4) and add
`cute.arch.sync_warp()` before it. In one B300 run at the default tactic
it measured -7.0% to +0.8% per call over the 16 shapes, against -6.2% to
+7.9% for the per-lane arrive in the same run: 1024 x 6144 M=20 at (16,
16, 256, 13, 2) went from +0.40 us to +0.00 us, and 2624 x 6144 M=20 at
(16, 32, 256, 9, 2) from +0.50 us to +0.06 us. It is not faster
everywhere: at 6144 x 4096 M=20 with the default (16, 32, 256, 4, 2) it
measured +0.06 us where the per-lane arrive measured -0.13 us, and at
6144 x 4096 M <= 5 with (32, 8, 256, 11, 2) it measured -0.18 to -0.21
us against -0.30 to -0.36 us. We used the per-lane arrive because the
memory-consistency chapter of the PTX ISA does not list `bar.warp.sync`
among the operations that establish ordering between threads, so with
`__syncwarp()` the other lanes' reads are ordered before the elected
lane's release only under a reading of the `bar.warp.sync` description
("also guarantee memory ordering among threads participating in
barrier"). It is a two-line change either way.
- The new test inspects PTX instead of running the kernel; it needs
`nvidia-cutlass-dsl` with `cutlass.experimental` and no GPU, and writes
the PTX into a pytest temporary directory.
- `_cp_async_wait_all` is inline PTX, like the file's existing
`_cp_async_16_with_policy`.
- The MXFP8 sibling, `dense_mxfp8_gemm_warp_splitk.py`, has the same
three patterns (see #8080); this PR does not change it.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

- **Bug Fixes**
- Improved synchronization in warp split-K BF16 matrix multiplication,
helping ensure results are written only after required computation and
data transfers are complete.
- Improved coordination when producing output across dependent GPU work.
- **Tests**
- Added coverage for BF16 matrix multiplication synchronization and
data-transfer behavior across supported GPU architectures.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [85c65fb](https://github.com/flashinfer-ai/flashinfer/commit/85c65fb3969bd3195d4d571e377ebf0615ea3276)

- **作者**: feih-nv
- **时间**: 2026-11-17T23:08:39Z
- **提交信息**: fix(common): CUDA_LAUNCH_BLOCKING is read on the first call; fmtstr ends its va_list copies (#9521)

## 📌 Description

Two fixes in the TRT-LLM common support code under `csrc/nv_internal/`,
from upstream TensorRT-LLM:

- **`isCudaLaunchBlocking` never read `CUDA_LAUNCH_BLOCKING`**
([NVIDIA/TensorRT-LLM#11261](https://github.com/NVIDIA/TensorRT-LLM/pull/11261),
commit
[100bfdc51](https://github.com/NVIDIA/TensorRT-LLM/commit/100bfdc5168444ddbad189767e9ae47cc0600c2b)).
The nv_internal copy (`tensorrt_llm/common/cudaUtils.h`) read the
variable only when `firstCall` was already false, which never happens,
so `sync_check_cuda_error` never synchronized in release builds and the
variable had no effect (41 call sites). The condition is `if
(firstCall)`, as in FlashInfer's other copy
`include/flashinfer/trtllm/common/cudaUtils.h`. Upstream fixed it by
rewriting `doCheckError` around a static lambda; FlashInfer keeps the
optional-based structure the two copies share, so this is the
one-character version of that fix.
- **`fmtstr` leaked its `va_list` copies**
([NVIDIA/TensorRT-LLM#6758](https://github.com/NVIDIA/TensorRT-LLM/pull/6758),
commit
[22d59a6f6](https://github.com/NVIDIA/TensorRT-LLM/commit/22d59a6f61ab6df0b7b17488a20c714a7f2c66e5)).
`fmtstr_` `va_copy`'d the arguments for the sizing `vsnprintf` and never
`va_end`'d the copy; `fmtstr` skipped `va_end` when `fmtstr_` threw. The
copy is ended right after the sizing call and `fmtstr` holds its list in
a `va_list_guard` (RAII), as upstream does.

Both are the trtllm_common items of the kernel-sync triage of
2026-11-12; merged by hand (the family has no GPU contract).

## 🔍 Related Issues


[NVIDIA/TensorRT-LLM#11261](https://github.com/NVIDIA/TensorRT-LLM/pull/11261),
[NVIDIA/TensorRT-LLM#6758](https://github.com/NVIDIA/TensorRT-LLM/pull/6758).

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

No new test: neither change is observable from Python (a synchronization
that now happens, a `va_list` that is now ended). B200, CUDA 13.0 CI
container, at `b6f4e8db8` + this branch:
`tests/utils/test_fp4_quantize.py::test_fp4_quantize_zero_rows` and
`tests/utils/test_fp8_quantize.py -k "zero_rows or empty"` (the modules
that compile `cudaUtils.h` and `stringUtils.cpp`): 16 passed; the same
with `CUDA_LAUNCH_BLOCKING=1`: 4 passed.

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

With `CUDA_LAUNCH_BLOCKING=1` every `sync_check_cuda_error` in the
TRT-LLM kernels now synchronizes, as it always did in debug builds and
as the `include/flashinfer/trtllm/common/` copy already did; without the
variable nothing changes.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* CUDA launch-blocking settings are now checked on the first call. An
unset setting remains unset, and only the value `"1"` is treated as
enabled.
* Message formatting now reliably releases its argument-list resources,
including when formatting encounters an error.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [789b0a2](https://github.com/flashinfer-ai/flashinfer/commit/789b0a2b4ff2d8e9dda02a76e8cddd17798749e4)

- **作者**: feih-nv
- **时间**: 2026-11-17T23:08:24Z
- **提交信息**: fix(moe): pad an empty EP rank's FP8 block-scale grouped GEMM input with one zero row (#9514)

## 📌 Description

With expert parallelism and no all-to-all, an EP rank that received no
tokens ran the DeepSeek FP8 block-scale grouped GEMMs on zero rows.
`expandInputRowsKernelLauncher` is followed by
`padEmptyFp8BlockScaleMoeInput`, which copies the expert offsets into a
separate `gemm_expert_first_token_offset` workspace array and, when the
rank is empty, zero-fills one row and assigns it to the last local
expert; both GEMMs read the GEMM offsets while the routing metadata is
untouched, so the finalizer discards the row. The padding runs only for
`use_deepseek_fp8_block_scale && ep_size > 1 && !enable_alltoall`, and
only when the call has tokens (`num_rows > 0`): with no tokens the
permuted buffer is zero-sized and there is nothing to pad. That guard is
FlashInfer's; upstream has no `num_rows == 0` handling on this path
either.

Port of the CUTLASS MoE part of
[NVIDIA/TensorRT-LLM#16603](https://github.com/NVIDIA/TensorRT-LLM/pull/16603)
(commit
[d010c6297](https://github.com/NVIDIA/TensorRT-LLM/commit/d010c62971b82c3b1c82dbc4904a55fe1a14b9d1));
the same upstream commit's MNNVL topology check is TRT-LLM Python and
not ported. The merge onto FlashInfer `286c22a6a` was done by the
kernel-sync controller; the `num_rows > 0` guard was added at review.

## 🔍 Related Issues


[NVIDIA/TensorRT-LLM#16603](https://github.com/NVIDIA/TensorRT-LLM/pull/16603).

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

No new test: the path needs EP > 1 with an empty rank, outside the
single-GPU matrix. On one GB200 node (CUDA 13.0 CI container, aarch64)
at FlashInfer `286c22a6a` + this commit, run by the kernel-sync
controller: `tests/moe/test_trtllm_cutlass_fused_moe.py::test_moe`,
`::test_moe_nvfp4`, `::test_moe_mxfp8_mxfp4`,
`::test_moe_unfused_finalize`,
`::test_moe_deterministic_mode_selects_unfused_finalize`: 66 passed.

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

One extra `(num_experts_per_node + 1) * 8` bytes of workspace for the
FP8 block-scale path. The padding kernel is a single 256-thread block
launched once per call on the EP path above (one offset copy plus, on an
empty rank, one zero row): a few microseconds of launch latency per MoE
call. Not measured: the CUTLASS DeepSeek FP8 block-scale path is
SM90-only and no H100 was at hand.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Fixed processing of empty expert batches in DeepSeek FP8 block-scale
MoE when using multi-rank execution with all-gather/reduce-scatter
communication. Inputs are now handled correctly when an expert receives
no tokens, while routing information remains unchanged. This improves
reliability for affected workloads without changing behavior in other
execution paths.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [950ae31](https://github.com/flashinfer-ai/flashinfer/commit/950ae31a711caa2bf1c9ad851b8de7a17b5c29e6)

- **作者**: feih-nv
- **时间**: 2026-11-17T23:08:07Z
- **提交信息**: fix(moe): Llama4 routing warp kernel lays out CTAs and padding from the local experts only (#9513)

## 📌 Description

`routingIndicesWarpKernel` in `trtllm_fused_moe_routing_llama4.cu` (the
path for fewer than 4 tokens) counted every expert's tokens when laying
out CTAs and padded rows and wrote global expert indices into
`mPtrCtaIdxXyToBatchIdx`. With expert parallelism the GEMMs then saw
CTAs for remote experts and batch indices outside this rank's weight
tensors. The kernel now maps local experts to local indices, gives CTAs
and padding only to them, and keeps a `-1` permutation index for remote
tokens, as the block-level path already did.

Port of
[NVIDIA/TensorRT-LLM#19251](https://github.com/NVIDIA/TensorRT-LLM/pull/19251)
(commit
[ec5ff4f99](https://github.com/NVIDIA/TensorRT-LLM/commit/ec5ff4f997ab6b7d6a7506cf173c2225a435f055)).
The merge onto FlashInfer `286c22a6a` was done by the kernel-sync
controller; no hand edits.

## 🔍 Related Issues


[NVIDIA/TensorRT-LLM#19251](https://github.com/NVIDIA/TensorRT-LLM/pull/19251).

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

No new test: the defect needs EP > 1 with fewer than 4 tokens, which the
routing tests do not parameterize. On one GB200 node (CUDA 13.0 CI
container, aarch64) at FlashInfer `286c22a6a` + this commit, run by the
kernel-sync controller: `tests/moe/test_trtllm_gen_routing.py -k
test_deepseekv3_routing`: 144 passed.

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

Routing-metadata only; the Llama4 warp path with a single rank is
unchanged in behavior.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Corrected expert routing so only local experts contribute work and
padded rows. Tokens routed to non-local experts now retain an invalid
permutation index, rather than receiving reserved tiles and CTA
metadata.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [cca2b64](https://github.com/flashinfer-ai/flashinfer/commit/cca2b640f0edab3d838e8c934bf2236da256a693)

- **作者**: feih-nv
- **时间**: 2026-11-17T23:07:50Z
- **提交信息**: fix(moe): index the trtllm-gen MoE permute and finalize kernels with int64 (#9512)

## 📌 Description

`permuteKernel`, `finalizeKernel` and `finalizeDeepSeekKernel` in
`trtllm_fused_moe_dev_kernel.cu` computed `tokenIdx * hiddenDim` and
`permutedIdx * hiddenDimPadded` in 32-bit `int`, which overflows for
large token counts (the DeepSeek FP8 shapes upstream hit). The row index
is widened to `int64_t` before the multiply, as upstream did.

Where it matters in FlashInfer:
- `permute::run` has no caller here; its change keeps the file aligned
with upstream.
- `finalize::run` picks `finalizeKernel` only for small grids (under
1184 blocks) or an unaligned hidden size; aligned large shapes use the
FlashInfer-only `finalizeKernelVecLoad`, mid topK the FlashInfer-only
`finalizeKernelSmallBatch`. Their `permutedIdx` loads were already
64-bit; their `tokenIdx * hiddenDim` store offsets were not (overflow at
about 300k tokens with H=7168) and are widened here as well, beyond the
upstream diff.
- The activation kernels already used `int64_t`, so the upstream hunks
there have no counterpart.

Port of
[NVIDIA/TensorRT-LLM#15887](https://github.com/NVIDIA/TensorRT-LLM/pull/15887)
(commit
[60ff8b784](https://github.com/NVIDIA/TensorRT-LLM/commit/60ff8b7843d694641d46ec2b51560a1dc1590019)).
The merge onto FlashInfer `286c22a6a` was done by the kernel-sync
controller; the VecLoad / SmallBatch casts were added at review.

## 🔍 Related Issues


[NVIDIA/TensorRT-LLM#15887](https://github.com/NVIDIA/TensorRT-LLM/pull/15887).

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

No new test: the overflow needs more rows than the test matrix
allocates. On one GB200 node (CUDA 13.0 CI container, aarch64) at
FlashInfer `286c22a6a` + this commit, run by the kernel-sync controller:
`tests/moe/test_trtllm_gen_routing.py -k test_deepseekv3_routing`: 144
passed.

Perf, B200 (CUDA 13.0 CI container), `benchmarks/flashinfer_benchmark.py
--routine trtllm_fp4_block_scale_moe` with the DeepSeek-V3 shape (hidden
7168, intermediate 2048, 256 experts, top-k 8, NVFP4, deepseek_v3
routing, shuffled weights), 300 iterations, median ms. Base is
`e3ebb9e7d`; the branch was run twice, bracketing the base run.

| tokens | base | branch | branch (2nd run) |
|---:|---:|---:|---:|
| 8 | 0.252 | 0.243 | 0.244 |
| 32 | 0.625 | 0.634 | 0.667 |
| 256 | 1.353 | 1.364 | 1.421 |
| 2048 | 2.446 | 2.393 | 2.436 |

Within run-to-run noise (std 0.1-0.7 ms at 32-256 tokens on this shared
node); the finalize kernel is a small part of the end-to-end time.

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

Index arithmetic only; the compiled kernels differ by the 64-bit
multiplies.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved handling of large tensor offsets during permutation and
finalization, helping prevent incorrect memory addressing in these
operations.
* Tensor indexing and output calculations remain unchanged, while
large-offset cases are handled more reliably. This can help preserve
correct results when processing tensors whose dimensions or token counts
produce offsets beyond the previous range.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [22b3158](https://github.com/flashinfer-ai/flashinfer/commit/22b3158b4201559f8780ba6682e8a1e68ee678dc)

- **作者**: feih-nv
- **时间**: 2026-11-17T23:07:14Z
- **提交信息**: fix(moe): size the CUTLASS MoE autotuner workspace for the FINALIZE fusion on SM >= 90 (#9507)

## 📌 Description

`MoeGemmRunner::getWorkspaceSize` counted the FINALIZE epilogue fusion's
workspace only for `sm_ == 90`, while the fusion is enabled on every SM
>= 90 (`use_fused_finalize` default), so on Blackwell the autotuner
workspace could be sized without it. One line: `sm_ == 90` -> `sm_ >=
90` in `moe_gemm_template_dispatch.h`.

Port of
[NVIDIA/TensorRT-LLM#18675](https://github.com/NVIDIA/TensorRT-LLM/pull/18675)
(commit
[c295dd9fc](https://github.com/NVIDIA/TensorRT-LLM/commit/c295dd9fca143a3fdd2769617699fdd4d4a93eb5)).
The merge onto FlashInfer `286c22a6a` was done by the kernel-sync
controller (its first port); the conflict was FlashInfer's local
formatting of the same lines.

## 🔍 Related Issues


[NVIDIA/TensorRT-LLM#18675](https://github.com/NVIDIA/TensorRT-LLM/pull/18675).

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

No new test: the change is the workspace bound the existing
fused-finalize paths exercise. On one GB200 node (CUDA 13.0 CI
container, aarch64), at `286c22a6a` + this commit:
`tests/moe/test_trtllm_cutlass_fused_moe.py::test_moe`,
`::test_moe_nvfp4`, `::test_moe_mxfp8_mxfp4`,
`::test_moe_unfused_finalize`,
`::test_moe_deterministic_mode_selects_unfused_finalize`: 66 passed in
17m31s including the JIT builds.

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

No kernel change, so no perf effect; the workspace grows by the FINALIZE
fusion's share on SM100/SM103, which SM90 already paid.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Updated workspace sizing for fused MoE operations on GPU architectures
with compute capability 9.0 and later.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [5793d81](https://github.com/flashinfer-ai/flashinfer/commit/5793d8104c13cdbd15b8c9fb2e39008125e0d4b3)

- **作者**: Jonathan Dierksen
- **时间**: 2026-11-17T22:34:58Z
- **提交信息**: test: guard POSIX-only calls for native Windows (#9461)

<!-- .github/pull_request_template.md -->

## 📌 Description

Native Windows arm64 runs hit six test cases that call POSIX-only
facilities without a guard. This makes them pass, or skip cleanly, on
Windows; Linux behavior is unchanged.

- `tests/jit/test_prims_ts_mla_prebuild.py`,
`tests/cpu/gemm/test_mxfp8_precompile.py`: `os.sched_getaffinity` is
patched with `raising=False`. Both functions under test already fall
back to `os.cpu_count()` when it is missing, and the patched value still
takes precedence.
- `flashinfer/mla/cake_dsv4.py` `_shared_library`: reads
`RTLD_NOLOAD`/`RTLD_NOW` through `getattr(os, ..., 0)`. On POSIX the
flags and probe order are the same as before. On Windows, ctypes ignores
`mode`, so both attempts are plain loads instead of an `AttributeError`.
Its unit test checks no-load semantics, which Windows does not have, so
it is skipped there.
-
`tests/cpu/trace_apply/test_packages.py::test_root_and_bundle_special_file_safety_checks_remain`:
skipped when `os.mkfifo` is absent.
- `tests/cpu/infra/test_build_jit_cache_wheel.py`: the stand-in
interpreter used to be a `#!/bin/bash` script, which Windows cannot
execute (WinError 193). Its logic is now a small Python script behind a
launcher named like an interpreter: `sh` on POSIX, `.cmd` on Windows.
`scripts/build_jit_cache_wheel.py` is unchanged.

This is the small, independent part of the Windows test cleanup. The
pytest sharding-runner port is in a separate PR. The Windows build port
itself is #8431.

## 🔍 Related Issues

Related: #8431 (Windows build port, open). Same skip style as #9288.

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
reviewers may adjust): `tests/jit/test_prims_ts_mla_prebuild.py
tests/cpu/mla tests/cpu/trace_apply tests/cpu/infra tests/cpu/gemm`

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

Validation (Linux, GB10, `flashinfer-ci-cu132` container): the five
touched test files ran on `main` and on this branch, giving `1541
passed` both times. `pre-commit run --files <changed>` is clean.

**Native Windows was not verified**: no arm64 Windows host was
reachable. Windows reasoning: `.cmd` launched through
`subprocess.run([...])`, `sys.exit(msg)` writes to stderr (which the
retry classifier reads), and the log path is embedded with `repr()`.

Left alone on purpose: the other Windows failures in `test_packages.py`
come from a separate sealed-package verifier issue. The `fifo` parameter
of the bundle-source replacement test (also `os.mkfifo`) is not changed
here either.

AI assistance: changes drafted and validated with Claude Code. I
reviewed them.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved shared-library loading compatibility on Windows while
preserving the existing loading behavior on POSIX systems.

* **Tests**
* Updated platform-specific test handling so CPU-affinity, build-retry,
and special-file checks can run or skip appropriately across supported
operating systems.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [f3f46d3](https://github.com/flashinfer-ai/flashinfer/commit/f3f46d3ba64988ea6b570ef4d6d64ffdd8d4e558)

- **作者**: Jonathan Dierksen
- **时间**: 2026-11-17T22:34:38Z
- **提交信息**: ci: add a Windows arm64 wheel and JIT-cache build driver (#9462)

<!-- .github/pull_request_template.md -->

## 📌 Description

Draft. This adds a driver that builds the Windows arm64 wheels and
JIT-cache packages (GB300 and RTX PRO 6000 DGX Stations), which are
built by hand today. The release tooling builds wheels only through
Linux bash (`scripts/jit_cache_build_common.sh` and its callers, run in
a manylinux container). WSL2 keeps using the Linux wheels.

`scripts/build_windows_arm64_wheels.py` is a Python port of that flow.
It runs under a native win-arm64 interpreter and has no dependency
outside the standard library. It builds three kinds of wheel:

- **python**: the `flashinfer-python` wheel. The sdist still comes from
the Linux job.
- **provider**: one `flashinfer-jit-cache-sm*` wheel per
`--provider-arch`.
- **shim**: the metadata-only `flashinfer-jit-cache` wheel.

The wheels and a `build-summary.json` go to `--output-dir`. A future
Windows CI lane can call it directly:

```
python scripts/build_windows_arm64_wheels.py --cuda-label cu134 --provider-arch 10.3a --provider-arch 12.0f --output-dir wheelhouse
```

Only the `cu134` label is accepted. The [CUDA 13.4 release
notes](https://docs.nvidia.com/cuda/archive/13.4.1/cuda-toolkit-release-notes/index.html)
(13.4.1 is the GA release) list Windows on Arm as new: §2.3.1 says "CUDA
13.4 adds support for Windows on Arm on RTX Spark devices", and NVCC,
cudart, NVRTC and cuobjdump list `arm64 (Windows)`. The [13.0
notes](https://docs.nvidia.com/cuda/archive/13.0.0/cuda-toolkit-release-notes/index.html)
have no `arm64 (Windows)` component. So `cu129` and `cu130` cannot
produce win_arm64 wheels, and the driver refuses them before running
anything. `cu134` uses the nightly PyTorch index, so the driver sets
`PIP_PRE`.

Supporting changes:
- `jit_cache_provider_validation.validate_provider` takes a
`library_name` callable. It defaults to `<module>.so`, so the Linux
behaviour does not change. The Windows driver passes `module.dll`, which
is the layout `jit_env.jit_library_name` uses in the build port.
- `verify_jit_cache_provider_artifact.py --library-layout windows` uses
that layout.
- `validate_shim` now also rejects a shim that carries a `.dll`.
- One paragraph in `docs/development/jit_and_build.md`.

### Design: each bash step and its Windows equivalent

| Linux (bash) | Windows driver |
| --- | --- |
| manylinux image, `uname -m` | `sysconfig.get_platform() ==
"win-arm64"` (the interpreter decides the wheel tag, so an emulated x64
Python is refused) |
| compiler preinstalled in the image | `cl.exe`/`link.exe` already on
PATH are used as they are. Otherwise vswhere finds a VS install with
`VC.Tools.ARM64`, and the environment of `vcvarsall.bat arm64` is
loaded. The build port does not locate MSVC itself. |
| `validate_jit_cache_cuda_toolchain` | `validate_cuda_toolchain` (same
`release X.Y` parse) |
| `compute_jit_cache_parallelism` (`free`, `nproc`) |
`compute_parallelism`, with memory from `GlobalMemoryStatusEx`. The same
clamps; a test checks both against each other on Linux. |
| `setup_jit_cache_python_build` | `python_build_environment`:
pip>=26.2.1 bootstrap without constraints, reuse or install torch for
the matrix CUDA, a `torch==<ver>` file in
`PIP_CONSTRAINT`/`PIP_BUILD_CONSTRAINT`, the PyTorch index in
`PIP_EXTRA_INDEX_URL`, `PIP_PRE` for nightly. The caller's environment
is never mutated, so no cleanup trap is needed. |
| `setup_sccache` (musl tarball) | **Skipped** (see open questions) |
| `run_with_output_watchdog.py` | Not used: it reads `/proc` |
| `build_jit_cache_wheel.py` | Reused unchanged for python and provider
builds |
| `build_jit_cache_shim_wheel.sh` | `build_shim`: a throwaway venv and
`python -m build --wheel --no-isolation` |
| `verify_jit_cache_provider_artifact.py` | `validate_provider` with the
module.dll layout, plus the cuobjdump inventory when `cuobjdump.exe` is
under `CUDA_HOME`/`CUDA_PATH` |
| `pip install` + entry-point check | Read from the wheel (METADATA,
manifest, entry_points.txt), so a persistent runner's interpreter does
not collect provider packages |
| `cp dist/*.whl $OUTPUT_DIR` | Copied after each build (the next build
cleans `dist/`), plus `build-summary.json` |

The Linux-only variables `FLASHINFER_JIT_CACHE_PROVIDER_PLATFORM_TAG`
and `FLASHINFER_{NVCC,CXX}_LAUNCHER` are removed from the build
environment. The provider backend rejects a platform-tag override
outside glibc. `FLASHINFER_LOCAL_VERSION` is withheld from the
`flashinfer-python` build, as in the release job, because
`build_backend.py` would add `+cuXXX` to the version.

**How wheel tags are verified.** Provider and shim wheels must be
`cp39-abi3-win_arm64`; the backends inherit that tag from the
interpreter. `flashinfer-python` must be `any` or `win_arm64`, and never
a Linux tag. The filename check runs before the content validators,
which repeat the platform-tag check.

### Open questions

1. **sccache.** Both sccache builds the Linux flow uses ship a
Windows-on-Arm binary:
- upstream mozilla/sccache `v0.18.0`:
`sccache-v0.18.0-aarch64-pc-windows-msvc.zip`, sha256
`205d613fa74a9a0525e41a5ace77b1c71907d5bd4a5e668bad79111776829290`
- rapidsai/sccache `v0.18.0-rapids.8` (the fork pinned in
`jit_cache_build_common.sh`):
`sccache-v0.18.0-rapids.8-aarch64-pc-windows-msvc.zip`, sha256
`2a64e9664068fac009507104a7100f88c43d581a453ba82ed7666b78bc88313b`. The
latest fork release, `v0.18.0-rapids.16`, ships the same asset.

The driver still skips sccache, because the Windows ninja rules in #8431
call `cl.exe` and `nvcc` without `$cxx_launcher`/`$nvcc_launcher`, so
installing either binary would have no effect. Once the rules honour the
launchers, try the rapids fork for nvcc first: it caches the dependency
list, so a hit skips nvcc's preprocessing. Two things then need checking
on Windows arm64. On Linux the fork leaves host C++ uncached because it
fails on `g++ -MMD`; how it handles `cl.exe /showIncludes` is unknown.
It is also unconfirmed that it handles `nvcc -ccbin cl`.
2. **Provider architectures for Windows.** `ci/cuda-versions.json` has
only `x86_64_`/`aarch64_provider_architectures`, so `--provider-arch` is
explicit for now. A `win_arm64_provider_architectures` entry, probably
`10.3a` and `12.0f`, should come with the CI lane and needs
`validate_cuda_versions.py` support.
3. **torch for win_arm64 + CUDA.** If
`download.pytorch.org/whl/nightly/cu134` has no win_arm64 CUDA wheel,
the driver stops and asks for a preinstalled one; it does not fall back
to the CPU wheel.
4. **cuobjdump on DLLs.** `inspect_cuda_architectures` writes each
module to a temporary `.so` name before running `cuobjdump`. I have not
confirmed that the Windows `cuobjdump.exe` reads a PE DLL saved under
that name.
5. **Device scope of CUDA 13.4 Windows on Arm.** The release notes name
only RTX Spark devices, with a Windows driver of 616.41 or later. The
[13.4 blog
post](https://developer.nvidia.com/blog/cuda-toolkit-13-4-adds-windows-on-arm-support-and-greater-control-over-shared-gpus/)
names the N1X laptop ecosystem. Neither mentions the GB300 or RTX PRO
6000 DGX Stations this driver is for, although #8431 reports test runs
on both. Before release wheels go out for them, confirm that they are
supported Windows-on-Arm targets for 13.4, and which provider
architectures (likely `10.3a` and `12.0f`) that implies.
6. **flashinfer-python build path.** This build uses the non-isolated
`build_jit_cache_wheel.py`, like the provider builds. The Linux release
job uses an isolated `python -m build`.

### Base and dependency

This branch is based on **`main`**, not on #8431. The driver only
orchestrates: it imports nothing from `flashinfer`, and the tests mock
every subprocess. Real provider builds on Windows still need #8431,
which adds MSVC host support and the `module.dll` naming.

### Follow-up (not in this PR)

Once the Windows CI lane exists, add a
`build-flashinfer-jit-cache-provider-win-arm64` job to
`release-build.yml`. It would run on the Windows arm64 runner, use
`actions/setup-python` with an arm64 interpreter, run this driver per
provider architecture plus one shim, and upload
`build/wheelhouse-win_arm64`. `verify_jit_cache_provider_release.py` and
`update_whl_index.py` then need to accept the `win_arm64` tag in the
release set. The test here shows that `update_whl_index` already parses
the filenames.

This PR was written with AI assistance (Claude Code). A person has
reviewed the design but has not run it on Windows hardware (see Tests).

## 🔍 Related Issues

- Depends on #8431 (Windows arm64 build port, MSVC host) for real
provider builds.
- Follows #9288 (skips the bash-sourcing release tests on Windows). The
new tests are the Windows-runnable counterpart.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues. (`pre-commit run --files` on the changed
files)

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).

Suggested CI test targets:
`tests/cpu/infra/test_build_windows_arm64_wheels.py
tests/cpu/infra/test_jit_cache_release.py
tests/cpu/infra/test_jit_cache_providers.py`

`tests/cpu/infra/test_build_windows_arm64_wheels.py` has 41 cases. They
need no GPU, CUDA toolkit or MSVC: a fake runner records every command
and writes minimal wheels where a build would. They cover the host
check, MSVC discovery (vswhere and the vcvarsall batch file, with `=C:`
lines skipped), the nvcc check, parallelism, the pip-constraint
environment (preinstalled, nightly install, and missing torch),
wheel-tag checks, the module.dll and `.so` validator paths, wheel-index
parsing, refusal of `cu129`/`cu130`, and an end-to-end `cu134` run of
python + 2 providers + shim with environment assertions. Seven parity
cases run the bash `compute_jit_cache_parallelism` with stubbed
`free`/`nproc` and compare the results. Those are skipped on Windows;
everything else runs there.

Local results (macOS, Python 3.14, CPU torch): the new file and
`test_jit_cache_release.py`, `test_build_jit_cache_wheel.py` and
`test_jit_cache_providers.py` gave 137 passed, 1 skipped. After the
final vcvarsall fix I reran the three files suggested above: 130 passed.
After restricting the driver to `cu134`, the new file gives 41 passed.

**Native Windows not verified:** no Windows arm64 host was reachable, so
the driver has not run on real hardware.

## Reviewer Notes

- The `validate_provider` signature gained a keyword argument with a
default; Linux callers are unchanged.
- vcvarsall runs through a temporary `.bat` written with CRLF. Passing a
quoted path through `subprocess` would backslash-escape the quotes, and
`cmd.exe` does not accept that.
- Provider builds run without the output watchdog on Windows, so a hung
nvcc is bounded only by the CI job timeout.

🤖 Generated with [Claude Code](https://claude.com/claude-code)




<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added support for building and validating package wheels on native
Windows ARM64 systems, including provider and shim builds.
* Added Windows-specific provider library validation for build
artifacts.
* **Documentation**
* Added guidance on Windows ARM64 builds, including supported CUDA
configuration and required build tools.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [dc99c09](https://github.com/flashinfer-ai/flashinfer/commit/dc99c09c60f33291e6753cbc3ee97026217b7be8)

- **作者**: Jonathan Dierksen
- **时间**: 2026-11-17T22:33:51Z
- **提交信息**: ci: seed the PR AOT sccache after merges to main (#9465)

<!-- .github/pull_request_template.md -->

## 📌 Description

Adds `.github/workflows/aot-cache-seed.yml`, which fills the PR AOT
lanes' sccache S3 cache right after merges to `main`.

**Why.** Pull requests from forks get no AWS credentials, so their `AOT
Build Import` lanes read the cache but never write it. Until now only
two kinds of runs wrote it: scheduled PR Test runs on `main`, and pull
requests from branches in this repository. After a merge that changes a
widely included header, every fork PR paid a cold AOT build until one of
those happened to run. Measured on the PR Test runs after #9031
(rapidsai sccache fork) landed:

| | x64 lanes | arm64 lanes |
|---|---|---|
| Warm cache (median) | 13–14 min | 16–19 min |
| Cold, after a broad header change (#4312 changed
`include/flashinfer/utils.cuh`) | 103–113 min | 125–214 min |

- **Gaps between cache writes:** the 3×/day scheduled runs started 5–7.5
h after their cron times.
- **Example:** on 11-12, fork PRs saw 17.7% cache hits from 17:50Z until
a same-repo PR started rebuilding the cache at about 18:50Z.
- **Cost:** in the 40 h after the rollout settled, 25 fork PR runs hit a
cold cache. That was about 143 extra runner-hours, or 85 a day.
- **Rollout window:** right after #9031 merged, PRs were cold for about
11 h. That was the stale `-rapids` prefix waiting for the first
scheduled run.

**What the seed does**
- **Trigger:** runs on pushes to `main` that can change an AOT compile
input:
  - `include/`, `csrc/`, `3rdparty/`
  - C/C++/CUDA sources and Jinja templates anywhere
- `flashinfer/jit/`, `flashinfer/aot.py`,
`flashinfer/compilation_context.py`, and `flashinfer/**/*jit*.py`
- `flashinfer-jit-cache/`, `ci/docker-tags.yml`,
`ci/cuda-versions.json`, and the two AOT scripts

It can also be started with `workflow_dispatch`. It only runs in
`flashinfer-ai/flashinfer`.
- **Same lanes:** it builds the same lanes as the PR AOT matrix
(x64/arm64 × each runtime CUDA version with a published image). It uses
the same image, runner pool and script
(`task_test_jit_cache_package_build_import.sh`), so it writes the
`cuda<ver>-<arch>-rapids` prefixes the PR lanes read.
- **Credentials:** it runs with the sccache credentials and fails if
they are missing, rather than doing a read-only build that seeds
nothing.
- **Concurrency:** a single `aot-cache-seed` group with
`cancel-in-progress: false`, so one seed runs and only the newest waits.
- This answers why #6968 removed the per-merge PR Test runs: 90% of them
were cancelled, and their work was lost.
- Here nothing is lost. sccache uploads each object as soon as it
compiles, so PRs started while a seed is still running already benefit.
On 11-12, fork PR hit rates went 18% → 51% → 100% while a cache-writing
run was still compiling.
- **`fail-fast: false`:** lanes write different prefixes, so one failing
lane doesn't stop the others.
- **No lint:** the seed sets the new `AOT_SKIP_SPEC_LINT=1` switch,
which skips the provider spec lint. The merged code already passed it on
its PR, and a lint failure would leave the cache cold until the next
merge. PR lanes are unchanged.
- **No other tests or reporting:** a seed builds and imports the
provider wheels and nothing else, and opens no issue on failure. The
scheduled PR Test run already reports AOT build breakage on `main`.

**Expected cost:** roughly 40–65 CPU runner-hours a day. Most seeds are
warm runs of 13–19 min per lane, plus a few cold ones after broad header
changes. This is an estimate: in the last 7 days, merges touching
`include/`, `csrc/` or `3rdparty/` came a median 60 min apart. On the
savings side, cold fork PRs currently cost about 85 extra runner-hours a
day, and a cold PR waits 1.5–3.5 h for AOT instead of 15–20 min. Both
figures come from 2 days of data with one broad header change, so the
seed's own runtimes should be checked after it lands.

**What it does not fix:** PRs that start during the 2–3.5 h after a
broad header change are still partly cold. The seed shortens that
stretch by starting as soon as the change merges, instead of waiting for
the next writer.

## 🔍 Related Issues

- Follow-up to #9031 (rapidsai sccache fork for the PR AOT lane).
- Context: #6968 (scheduled runs replaced the per-merge PR Test runs on
`main`).
- The spec-lint lock-timeout flake from the same investigation is
already fixed by #9441.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues. (Ran on the changed files; all pass.)

## 🧪 Tests

- [x] Tests have been added or updated as needed.
(`tests/cpu/infra/test_aot_cache_seed_workflow.py`)
- [x] All tests are passing (`unittest`, etc.). (20 passed; see Reviewer
Notes for how.)
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/cpu/infra/test_aot_cache_seed_workflow.py
tests/cpu/jit/test_jit_spec_gencode_lint.py`

## 🔬 Experimental Track

- [ ] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.
Tracking issue: #

## Reviewer Notes

- **The workflow itself can't run on this PR.** It triggers only on
`push` to `main`. The first real seed is the first matching merge after
this lands. To check it, look for `sccache mode: read-write` and the
`sccache-stats-seed-*` artifacts. After a header change, later fork PRs'
AOT hit rates should go up.
- **New tests:** they check the triggers, that seeds never cancel, which
paths start a seed and which don't (through a GitHub path-filter
translator), that the lanes match the PR matrix, the credentials, and
the lint switch (run as a bash fragment).
- **How I ran them:** in an isolated copy with only pytest and PyYAML,
because my local machine has no torch and `tests/conftest.py` imports
it. The CI CPU lane runs them normally.
- **Existing test:**
`test_aot_script_lints_specs_before_building_and_inspects_wheels_after`
still holds, since the lint call is still before the build.
- **actionlint:** it reports only the custom runner labels (`cpu`,
`on-demand`) and SC2046 in the `Cleanup` step copied from `pr-test.yml`.
`pr-test.yml` gets the same warnings.
- **Path filter:** this is a judgment call. A false positive costs one
warm run (13–19 min per lane). A missed path means fork PRs stay cold
until the next scheduled run.

AI-assisted (Claude Code): the analysis of PR Test and nightly runs, the
workflow, the tests and this description.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* AOT build caches are seeded after qualifying updates to the main
branch, with support for multiple CUDA versions and processor
architectures.
* Cache seeding can also be started manually. Fork pull requests can
read the cache without cloud credentials.
* Cache-seeding runs are serialized, allowing an active run to finish
while the newest pending run waits.
* **Documentation**
* Added guidance on cache access, eligible cache writers, seeding
schedules, and approximate build times.
* **Build Improvements**
* Provider-spec lint can be skipped during cache-seeding builds; it
continues to run by default.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [127fb6d](https://github.com/flashinfer-ai/flashinfer/commit/127fb6dfd8bb7f70a01dcc34fcda1566a3a98a64)

- **作者**: Jonathan Dierksen
- **时间**: 2026-11-17T22:33:02Z
- **提交信息**: Port sharding runner process control to native Windows (#9466)

<!-- .github/pull_request_template.md -->

## 📌 Description

Ports the pytest sharding runner's worker process control to native
Windows. Previously every worker died at `os.killpg` (AttributeError),
and `signal.SIGKILL` does not exist on Windows. This is groundwork for
running the same sharding runner in a Windows CI lane.

`scripts/test_sharding/processes.py` now handles both starting and
ending a process group:

- **`start_process_group(command, **popen_kwargs)`** replaces the two
`subprocess.Popen(..., start_new_session=True)` call sites (collection
in `runner.py`, batches in `workers.py`).
  - POSIX: unchanged (`start_new_session=True`).
- Windows: starts the child with `CREATE_NEW_PROCESS_GROUP` and assigns
it to its own **Job Object** (ctypes, kernel32). The job keeps tracking
descendants even after the leader exits, which `taskkill /T` cannot do
because it walks parent PIDs.
- **`terminate_process_group(process, grace_seconds)`** keeps its
contract and return values.
  - POSIX: unchanged. `killpg(SIGTERM)` → grace → `killpg(SIGKILL)`.
- Windows: sends `CTRL_BREAK_EVENT` to the console process group, polls
the job's `ActiveProcesses` during the grace period, then calls
`TerminateJobObject` (exit code 137, so a forced kill never reads as
pytest's 0/1). If the job cannot be created or assigned,
`start_process_group` kills the leader and raises, so the runner never
launches a worker it could not clean up. A `taskkill /T` fallback would
miss descendants after the leader exits.
- **`GRACEFUL_TERMINATION` / `FORCED_TERMINATION`** define the reported
`termination_signal` strings (for example `signal=` in `PYTEST KILLED`
lines): `SIGTERM`/`SIGKILL` on POSIX,
`CTRL_BREAK_EVENT`/`TerminateJobObject` on Windows.

`__shell-settings` now prints test paths with `as_posix()`, because
`task_run_unit_tests.sh` word-splits that line and backslashes would not
survive it. The output is unchanged on POSIX.

Test changes (platform-aware rather than skipped wherever possible):

- `test_processes.py`: uses `start_process_group`, has the test child
ignore `SIGBREAK` on Windows (`SIGTERM` on POSIX), and asserts
`FORCED_TERMINATION`.
- `test_runner_cli.py`:
  - expects `signal={FORCED_TERMINATION}`.
- compares help defaults as rendered `Path`s (the runner has no `/tmp`
default of its own; argparse renders the env-provided `Path` with native
separators).
- reads child stdout with a thread, since `select()` on a pipe is
socket-only on Windows.
- uses a `subprocess.call` prefix wrapper, because on Windows `os.execv`
spawns a new process and exits.
- uses `portalocker` instead of `fcntl` on Windows in the GPU-sharing
suite (`fcntl` is unchanged on POSIX).
  - skips the `tests/comm` conftest case on Windows.
- `test_workers.py`: skips
`test_inherited_stdout_cannot_block_batch_completion` on Windows. On
POSIX the test makes a descendant escape the group with `setsid`. Inside
a Job Object without breakaway rights no descendant can escape, so the
scenario cannot occur.

## 🔍 Related Issues

Windows-on-Arm bring-up (native Windows CI lane for the sharding
runner).

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.
(`pre-commit run --files <changed files>`: clean. `mypy` also passes for
`processes.py` with both `--platform win32` and the default platform.)

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/test_sharding`

Validation:

- **Linux** (`flashinfer-ci-cu129` container, CPU only): `pytest
tests/test_sharding tests/cpu` on the base commit and on this branch
gives 10603 passed and the same 42 failures on both. Those 42 are
pre-existing failures in `test_shell_entrypoint`,
`test_bot_run_workflow`, `tests/cpu/prims_ts` and `tests/cpu/infra`
caused by the container environment, and none are in the files this PR
touches. All of `test_processes.py`, `test_workers.py` and
`test_runner_cli.py` pass.
- **Native Windows** (Windows Server 2022 **x64**, Python 3.12, CPU
torch). `test_processes.py`, `test_workers.py` and `test_runner_cli.py`:
  - base: 31 failed.
- this branch: **86 passed, 4 skipped** (3 × comm conftest, 1 × escaped
descendant). The new test covers a launch where Job Object assignment
fails.
  - Not yet run on arm64 Windows.
- **macOS**: same `tests/test_sharding` failure set before and after
(all pre-existing and macOS-specific: bash 3, missing GNU tools).

## Reviewer Notes

- **Assignment race.** The child runs for a moment before it is assigned
to the job. Python and pytest start up long before they spawn
descendants, so nothing escapes in practice. A fully race-free version
needs `CREATE_SUSPENDED` plus a resume through an undocumented `ntdll`
call; I chose not to do that.
- **No console.** If the runner has no console, `CTRL_BREAK_EVENT`
cannot be delivered. The group still gets the grace period, then
`TerminateJobObject`.
- **`KILL_ON_JOB_CLOSE` is not set.** This matches POSIX, where workers
outlive a dead runner. It could be added later if orphaned GPU processes
become a problem on the Windows lane.
- **Command prefixes.** On Windows a `PYTEST_COMMAND_PREFIX` wrapper
must not `os.execv`, because the wrapper exits and the real pytest is
cleaned up as residual group work.
- **Known Windows gaps outside this PR.** Both are non-fatal
background-thread tracebacks today:
  - `resource_monitor.py` calls `os.getloadavg`.
- `workers._descendant_pids` reads `/proc`, so RSS telemetry is missing
on Windows.
- Separately, `test_bot_run_workflow.py` fails to collect on Windows
with a `UnicodeDecodeError`, because it reads files with the locale
encoding.

This change was developed with AI assistance (Claude Code). I reviewed
and validated it as described above.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved test process cleanup on Windows and POSIX, including when a
process exits before its child processes.
* Fixed cleanup when Windows process setup fails, ensuring the started
process is terminated.
* Standardized test-path formatting for shell-based test runs across
platforms.
* Updated test-runner checks to support platform-specific process
behavior.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [dd4d0f4](https://github.com/flashinfer-ai/flashinfer/commit/dd4d0f4654e4cab027116bb18cb0f344737e7dcd)

- **作者**: losewayy
- **时间**: 2026-11-17T22:18:10Z
- **提交信息**: fix(autotuner): retune when cached winners lack runner coverage (#9144)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

Tuning an explicit backend can cache a single-runner winner that a later
`auto` tune reuses before profiling newly eligible runners.

During multi-runner tuning, reuse the first eligible cached winner only
if its record covers every current candidate. Save coverage after a
complete comparison so a later tune can retry an incomplete one. Give
the SM107 low-M CuTe-DSL runner a distinct cache identity from the
regular runner.

## 🔍 Related Issues

<!-- Link any related issues here -->

Fixes #9029. Related to #9020.

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
reviewers may adjust): `tests/autotuner/test_autotuner_core.py
tests/autotuner/test_autotune_cache_v2.py
tests/cpu/autotuner/test_autotuner_configs.py
tests/cpu/autotuner/test_autotuner_distributed.py
tests/gemm/test_mm_mxfp8.py`

The candidate-expansion regression failed on the original code because
the expanded call made zero profiling calls. It passes with the fix.
Local validation included 410 targeted tests for autotuning, cache
reload and GEMM behavior, plus 36 CPU distributed tests including Gloo
cache-hit agreement. The pre-commit hooks were installed and run in an
isolated validation checkout.

On an RTX 5070 Ti Laptop GPU (SM120), tuning `mm_mxfp8` with
`backend="cutlass"` and then `backend="auto"` at `(M, N, K) = (128, 256,
256)` profiled b12x, CUTLASS and cuDNN. Repeated tuning and inference
reused the result. The `K=160` single-candidate control reused the
CUTLASS winner. The SM107 scenario from #9020 was exercised with
simulated device capability and fake runners.

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

Runner coverage is optional metadata in the existing JSON and managed v2
cache formats. Older entries remain usable for inference and compatible
single-runner tuning. A multi-runner tune refreshes a winner whose
record lacks coverage. The distinct SM107 low-M identity can cause an
initial cache miss for that runner.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Cached tuning results are reused only when they cover the available
runner candidates, so changed candidate sets can produce an updated
selection.
* Incomplete tuning attempts can fall back to the best measured option
and be retried later.
* Distributed tuning uses a fallback when runners disagree on the final
selection or validation is incomplete.
* Low-M MXFP8 tuning is kept distinct from regular CuTe-DSL tuning to
prevent cache results from being shared incorrectly.
* **Documentation**
* Updated autotuning guidance on cache reuse, candidate coverage,
measurement retries, and audit records.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [7ba4018](https://github.com/flashinfer-ai/flashinfer/commit/7ba4018ce5f0d89e80dc0efd211359a85098f450)

- **作者**: Po-Han Huang (NVIDIA)
- **时间**: 2026-11-17T22:12:12Z
- **提交信息**: fix(utils): keep _get_stream_cache_buf traceable under torch.compile(dynamic=True) (#9354)

[by Claude Code]

<!-- .github/pull_request_template.md -->

## 📌 Description

#8696 changed `_get_stream_cache_buf` to key its per-stream scratch
buffers with `torch._C._cuda_getCurrentRawStream(index)`. That saves
building a `Stream` object on every eager call. Under
`torch.compile(dynamic=True)`, however, Dynamo can trace the device
index as a symbolic int, and the raw binding rejects it during
fake-tensor propagation:

```
torch._dynamo.exc.TorchRuntimeError: RuntimeError when making fake tensor call
  Explanation: Dynamo failed to run FX node with fake tensors: call_function
  <built-in function _cuda_getCurrentRawStream>(*(s62,), **{}): got RuntimeError('invalid argument to getCurrentStream')
```

So any compiled function that reaches the helper no longer compiles. In
0.7.3 these compiled fine, because the helper used
`torch.cuda.current_stream(device).cuda_stream`. Callers that reach the
helper include:
- `top_k`, `top_k_page_table_transform`, `top_k_ragged_transform`,
`top_k_renorm_probs` and `top_k_mask_logits` (through
`_get_row_states_buffer`);
- the `mm_*` / `bmm_*` / groupwise GEMM workspaces;
- cuDNN grouped GEMM.

The regression surfaced when SGLang bumped to FlashInfer 0.7.4
(sgl-project/sglang#49771). SGLang's UNO speculative sampling wraps
`flashinfer.top_k` in `torch.compile(dynamic=True)`, and its unit test
started failing with the error above.

This PR uses the traceable
`torch.cuda.current_stream(device).cuda_stream`, the pre-#8696 spelling
with the same handle, only while Dynamo is tracing
(`torch.compiler.is_dynamo_compiling()`). Eager calls keep the raw
binding. The guard costs about 32 ns per call (measured standalone on an
L40S host), and it does not import `torch._dynamo` (see #3290).

The compiled code still keys buffers by the stream it actually runs on.
The new test runs a compiled `top_k` on two side streams and checks that
each gets its own cached `row_states`, so the per-stream isolation from
#3618 still holds under `torch.compile`.

## 🔍 Related Issues

- Follow-up to #8696 (and #8221).
- Surfaced in sgl-project/sglang#49771.

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

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/utils/test_topk.py
tests/autotuner/test_autotuner_bmm_fp8.py`

The new test is
`tests/utils/test_topk.py::test_multi_cta_top_k_under_torch_compile_keeps_row_states_per_stream`.
It traces `flashinfer.top_k` with `torch.compile(dynamic=True,
backend="eager")` on two side streams and checks the results and the
per-stream `row_states` buffers.

Setup: L40S (SM89), torch 2.14.1+cu130. I ran against the
`flashinfer-python==0.7.4` wheel with this patch applied, because
`_get_stream_cache_buf` on `main` is identical to 0.7.4's.
- Without the fix, the new test fails with the `invalid argument to
getCurrentStream` error above.
- With the fix, the new test and the 11 existing `row_states`
stream/graph tests in `tests/utils/test_topk.py` pass (12 passed).
- With the fix, SGLang's unmodified `test_speculative_sampling.py`
passes 11/11 (it fails without it).

I also checked compiled `top_k` against eager on several shapes,
including two side streams.

## Reviewer Notes

- Several other modules also call `torch._C._cuda_getCurrentRawStream`
directly:
  - `cake_fmha.py`
  - `cudnn/utils.py`
  - `comm/tp_moe_finalize_rmsnorm.py`
  - a few `cake_*` backends

They are separate code paths and not part of this regression, so this PR
leaves them alone. If they can be reached from a
`torch.compile(dynamic=True)` region, they may need the same guard.
- `fullgraph=True` was never possible through `top_k`: its FFI kernel
call is opaque to Dynamo. This PR restores the `fullgraph=False`
behavior that 0.7.3 had.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved scratch-buffer caching during compiled CUDA operations,
including proper separation across CUDA streams.

* **Tests**
* Added regression coverage for compiled top-k operations across
multiple streams.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [9e2600a](https://github.com/flashinfer-ai/flashinfer/commit/9e2600a88ca2bac9802bd65cbeaa05053b6fb24e)

- **作者**: garry569
- **时间**: 2026-11-17T22:08:05Z
- **提交信息**: feat(gemm): quantize masked grouped GEMM output to NVFP4 in the epilogue (#7851)

> **Depends on #7850** (fused gated activation). This branch is stacked
on it, so the diff includes that commit; please review only the last two
commits. I will rebase onto `main` once #7850 is merged.

## 📌 Description

Lets the SM100/SM103 CuTe DSL masked grouped GEMM quantize its output to
NVFP4 in the epilogue, so the result (e.g. MoE GEMM1 activations) feeds
the next masked GEMM directly without a BF16 round trip through global
memory and a separate quantization kernel.

New output mode, enabled by `c_dtype="float4_e2m1fn"` (SM100/SM103
only):

| Argument | Meaning |
|---|---|
| `out` | `uint8` (or `float4_e2m1fn_x2`) `(m, n_out/2, l)`, two E2M1
values per byte, written through the TMA store. |
| `out_scale` | E4M3 block scales (`sf_vec_size=16`) in the same
swizzled layout as `SFA`: logical `(32, 4, rm, 4, rk, l)`, physical `(l,
rm, rk, 32, 4, 4)`, `rk = n_out/64`. Accepts a dense buffer or the 6-D
view returned by the NVFP4 quantizers. |
| `global_scale` | `float32 (l,)` per-batch global scale, same as
`a_global_sf` of `scaled_fp4_grouped_quantize`. |

Numerics: the epilogue rounds to BF16 first and then applies the default
(fast-math) recipe of `scaled_fp4_grouped_quantize`, so values and
scales are **bitwise identical** to "BF16 output +
`scaled_fp4_grouped_quantize`". The epilogue only implements that
recipe, so it raises `ValueError` when `FLASHINFER_NVFP4_4OVER6`,
`FLASHINFER_DISABLE_FP4_QUANT_FAST_MATH` or its `TRTLLM_` alias is set,
instead of silently diverging from the standalone quantizer.

Works with and without the fused gated activation; with it, `n_out =
n/2`.

Constraints (checked on the host): `mma_tiler_mn[0] == 128`, `n` a
multiple of `mma_tiler_mn[1]`, `n_out` a multiple of 64, no combine
fusion / `is_swap_ab`; SM107 rejects the new arguments explicitly.

## 🔍 Related Issues

Depends on #7850.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] `ruff format` / `ruff check` (0.12.8) and `mypy` (1.17.1) pass on
the changed files.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing.

`tests/gemm/test_grouped_gemm_masked_fused_epilogue.py`, 99 passed on
B300 / SM103 (CUDA 13, cutlass-dsl 4.8.1); new in this PR:

- 16 bitwise cases against `scaled_fp4_grouped_quantize` (both tilers,
with / without gated activation, partial `masked_m`; values and
unswizzled scales compared with `torch.equal`).
- CUDA graph capture / replay with `masked_m` changed between replays.
- Invalid-argument tests (missing / misshaped `out_scale`, wrong
`global_scale`, wrong `out` shape, 2-CTA tiler, swap-AB, non-FP4
`c_dtype` with scales) and one test per recipe environment variable.

Suggested CI test targets:
`tests/gemm/test_grouped_gemm_masked_fused_epilogue.py
tests/gemm/test_cute_dsl_blockscaled_gemm.py`

## 📊 Benchmark

B300 (SM103), single GPU, CUDA graph, median of 10 replays x 20
iterations. MoE GEMM1 decode shape: 16 local experts, `k = 6144`, `n = 2
x 3072`, NVFP4 inputs, capacity `8 x T` rows per expert, `T/4` valid
rows per expert. Happy to add the benchmark script under `benchmarks/`
if useful.

| tokens/rank | rows/expert | A: GEMM1 (BF16, full width) +
`silu_and_mul_scaled_nvfp4_experts_quantize` | B: GEMM1 + fused SwiGLU
(BF16) + `scaled_fp4_grouped_quantize` | C: GEMM1 + fused SwiGLU + NVFP4
output (this PR) | C vs A | C vs B |
|---:|---:|---:|---:|---:|---:|---:|
| 32 | 8 | 68.6 us | 66.1 us | 61.2 us | 10.8% | 7.4% |
| 128 | 32 | 69.4 us | 67.0 us | 61.3 us | 11.7% | 8.6% |
| 256 | 64 | 70.3 us | 67.5 us | 61.2 us | 12.9% | 9.2% |
| 512 | 128 | 73.0 us | 69.2 us | 61.2 us | 16.2% | 11.6% |

C stays at the cost of the GEMM alone; the gain grows with tokens
because the removed kernels scale with rows.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added NVFP4 output quantization for masked grouped GEMM on supported
Blackwell GPUs, with configurable scale tensors and fused
gated-activation support.
  * Added a benchmark for fused SwiGLU with NVFP4 output.
* **Bug Fixes**
* Added validation for required output buffers and scales, supported
layouts and shapes, and incompatible quantization settings.
  * NVFP4 output quantization is not supported on Rubin GPUs.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: garry569 <324435785+garry569@users.noreply.github.com>

### [97aa2c2](https://github.com/flashinfer-ai/flashinfer/commit/97aa2c236ab370a799de783f11ea81c8ce8c161d)

- **作者**: amitz-nv
- **时间**: 2026-11-17T21:44:52Z
- **提交信息**: feat(sdsa): convert NVFP4 KV tokens to FP8 for token-sparse attention, once per key (#9527)

## 📌 Description

Token-sparse attention over an NVFP4 KV cache needs each query row's
selected tokens as FP8 E4M3 rows in a workspace of one-token pages, the
input of the trtllm-gen token-sparse FMHA
(`trtllm_batch_decode_with_kv_cache(..., sparse_top_k=top_k,
uses_shared_paged_kv_idx=False)`). This PR adds two CUDA-graph-safe
conversion paths that start from the selected **key positions** and
write both the FP8 rows and the K/V index lists the FMHA reads. The
persistent cache stays packed NVFP4; only selected tokens are converted.

Rows that belong to the same request select mostly the same keys: the 1
+ k verify tokens of a speculative-decode request, or the tokens of a
prefill chunk (at 200K context, a 3K-token chunk reuses each selected
key about 30 times). Converting per row repeats that work; this PR
converts each selected key once per request.

**New APIs** (`flashinfer.sdsa.token_sparse`, also exported from
`flashinfer.token_sparse`):

- `gather_nvfp4_kv_cache_by_position`: per query row, positions → cache
slots (through the request's block table) → FP8 rows, in one launch with
16-byte loads and stores. It also writes each attention request's K/V
index lists and count, as `token_sparse_kv_indices` does for slots.
Suited to few rows (e.g. batch size 1).
- `compact_nvfp4_kv_cache`: rows grouped by request convert each
selected key once into the group's region of the workspace; each row's
lists point into that region entry for entry, and dead entries point at
a single zero row.
- **Union groups** number their keys with a per-group key bitmap (mark,
prefix-number, remap). The bitmap is persistent and every call leaves it
zeroed, so no memset is needed under CUDA graphs.
- **Dense groups** (chunks whose rows select more keys in all than the
context holds) convert every key below the last selected one, key `p` to
region row `p`.
- `compact_nvfp4_scratch_numel` and `compact_nvfp4_bitmap_numel` size
the workspaces.
- Launches can cover different group ranges (`group_base`) over shared
positions and output tables: rows of other ranges are skipped; padding
rows (`row_groups` -1) point at the zero row.
- The conversion grid is groups × the largest region's tiles. When that
would exceed 1024 programs per SM, a grid of 256 programs per SM loops
over each group's own tiles instead, so groups with small regions do not
launch idle programs (on GB300, one long dense prefill group next to 50
short union groups: 378 → 97 µs, same outputs bit for bit). Decode
batches (e.g. 128 requests × 6 rows) stay below the threshold: there the
full grid is as fast or faster.

**Behavior:**

- Both paths write the same FP8 bits for a given token, and entry `j` of
a row's lists holds the same key as entry `j` of its positions, so
token-sparse attention over either result computes on the same values in
the same order. During development the outputs were checked bit for bit
against a per-row slot gather (#9321's kernel).
- **Scaling:** an FP8 row holds the decoded NVFP4 values (E2M1 × E4M3
block scale) divided by six, excluding the global scales. Callers
multiply BMM1's K scale and BMM2's V scale by six. This keeps NVFP4's
full normalized range representable in FP8 without saturation. E2M1
pairs are decoded with Blackwell's `cvt.rn.f16x2.e2m1x2`; every E2M1
value is exact in FP16.
- **Layout:** K/V are uint8 HND pages (two E2M1 values per byte) with
FP8 E4M3 block-scale pages. K scales are linear. V scales use TRT-LLM's
four-token swizzle by default; `v_sf_swizzled=False` reads linear V
scales as written by `nvfp4_quantize_append_paged_kv_cache`.
- **Stale entries:** both paths take optional authoritative row lengths,
for lists whose entries past the count may be stale.
- **Graph safety:** all launches are graph safe, with no host
synchronization. The conversion grid puts tiles on axis 0, so regions of
more than 65,535 tiles work.
- **Validation:** every index tensor is checked (contiguous 1-D, dtype,
size, the cache's device), as `token_sparse_kv_indices` does, along with
a non-empty block table and the launch parameters.
- **Requirements:** a Blackwell GPU (compute capability 10.x, 11.x or
12.x); validated on SM103 (GB300). `head_dim` must be a power of two, 64
or more (other values raise `ValueError` before any launch). Other GPUs
raise `NotImplementedError`. `cvt.rn.f16x2.e2m1x2` needs an
arch-specific (`sm_XXXa`) or family (`sm_XXXf`) compile target, which
Triton uses for Blackwell.
- **Tracing:** both APIs have `fi_trace` templates
(`flashinfer/trace/templates/sdsa.py`, recording `v_sf_swizzled` too),
with examples in `tests/trace/example.py` and reference JSONs in
`tests/trace/fi_trace_out`.
- **Docs:** `docs/api/sparse.rst` (token-sparse section).

**Performance:** per attention layer on GB300, head_dim 256, top_k 2048,
200K context, 16 tokens per program; CUDA-graph replays with L2 flushed
before each, median of 30. Baseline: `token_sparse_kv_indices` + #9321's
per-row slot gather, one launch for all rows. Every result below matched
the baseline bit for bit (counts and the FP8 bytes of every live entry).

| case | per-row gather | this PR |
|---|---|---|
| decode, 1 request × 3 verify rows | 19.6 µs | 9.4 µs
(`gather_nvfp4_kv_cache_by_position`) |
| decode, 128 requests × 3 verify rows | 794 µs | 94 µs
(`compact_nvfp4_kv_cache`, union) |
| decode, 128 requests × 6 verify rows | 1574 µs | 133 µs
(`compact_nvfp4_kv_cache`, union) |
| prefill, one 2816-row chunk | 5695 µs | 56 µs
(`compact_nvfp4_kv_cache`, dense) |

End to end, in a vLLM serving benchmark of an NVFP4-KV token-sparse
model (TP4, 64 concurrent long-context sessions, same node), switching
from the per-row gather to an earlier revision of these paths raised
throughput by 22% (824.7 → 1008.9 output tok/s/GPU).

## 🔍 Related Issues

Supersedes #9321 (per-row NVFP4 KV gather): this PR covers that use case
with the position-based path and adds the once-per-request compaction.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

The hooks pass on the changed files (`pre-commit run --files ...`); the
full repository was not checked.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).

New `tests/sdsa/test_token_sparse_nvfp4.py` (263 cases) checks both
paths bit for bit (FP8 bit patterns, so −0.0 and +0.0 differ) against an
independent torch decode reference. It covers:

- swizzled and linear V scales, head dims 128 and 256, page sizes 64 and
16;
- top-k 512 and 2048, one or two attention requests per row;
- every byte (two E2M1 codes) under every finite E4M3 block scale, both
signs;
- random block scales across E4M3's normal and subnormal range, with
scale pages strided differently from data pages;
- stale entries past each row's count, with authoritative lengths, and
`max_keys` below the context;
- union and mixed dense / union groups, in one launch, split across two
group ranges, with a padding row, or with the conversion grid capped to
one or three looping programs per group; `max_capacity` below a union's
size, tile-aligned or not;
- a launch with no groups (padding rows still point at the zero row,
which is zeroed);
- rejected malformed inputs;
- dead entries addressing the zero row;
- the bitmap left zeroed, also across a CUDA-graph replay.

Both APIs also have `fi_trace` examples in `tests/trace/example.py`,
with reference JSONs in `tests/trace/fi_trace_out`. The NVFP4 tests skip
on non-Blackwell GPUs.

Validated on **NVIDIA GB300**, at the PR head:

- `tests/sdsa/test_token_sparse.py
tests/sdsa/test_token_sparse_nvfp4.py`: **284 passed**;
- with `tests/trace/test_fi_trace_template_consistency.py
tests/trace/test_fi_trace.py`: **1627 passed, 2 skipped**;
- the example calls regenerate the committed reference JSONs exactly.

The full test suite was not run. `pre-commit run --files <changed
files>` passes.

Suggested CI test targets: `tests/sdsa/test_token_sparse.py
tests/sdsa/test_token_sparse_nvfp4.py
tests/trace/test_fi_trace_template_consistency.py`

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added APIs to gather selected NVFP4 KV-cache tokens into an FP8
attention workspace or compact each group’s selected tokens into a
shared region.
* Added helpers for sizing the scratch and bitmap buffers required for
compaction.
* Added support for optional row lengths, grouped processing, and
key/value index lists.
* **Documentation**
  * Documented the new NVFP4 token-sparse conversion options and APIs.
* **Tests**
* Added coverage for conversion, gathering, compaction, input
validation, and CUDA graph replay.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [40a779e](https://github.com/flashinfer-ai/flashinfer/commit/40a779ed3665676d19e930f4e663123f708c7fa1)

- **作者**: Zhaowei Gu
- **时间**: 2026-11-17T21:41:01Z
- **提交信息**: fix(gemm): reject K not divisible by 256 for trtllm gemm_fp8_nt_groupwise (#6881)

<!-- .github/pull_request_template.md -->

## 📌 Description

`gemm_fp8_nt_groupwise(..., backend="trtllm")` accepts any K >= 256 in
`_trtllm_gemm_fp8_nt_groupwise_requirement`. For K = 384 or 640 it
passes Python validation and then fails in C++ with `Check failed:
(gemm.isValidConfig(config, gemmData)) is false: unsupported tactic id
in run`.

`select_kernel_fp8` in `csrc/trtllm_gemm_runner.cu` can only pick
`t128x{8,16,32}x128u2` block-scaled (`dsFp8`) kernels. These are
TileK=128 with `UnrollLoop2xForMma`, which needs K to be a multiple of 2
* TileK = 256. The issue derives this from the cubin pin's
`GemmOptions.h` and confirms it on Rubin (and GB300 campaign logs).

This PR implements the first ask of #6149: fail early with a clear
error.
- `_trtllm_gemm_fp8_nt_groupwise_requirement` now raises
`ValueError("a.shape[1] must be a multiple of 256 in TRTLLM, got <K>;
use backend='cutlass' for this K")` when K % 256 != 0. Inputs with K <
256 still get the existing message. An explicit `backend="trtllm"` call
is now rejected by `@backend_requirement` before any kernel/JIT work.
- The trtllm skip in `test_fp8_groupwise_gemm` changes from `k < 256` to
`k % 256 != 0`, to match. The K list there is `[128, 256, 512, 4096,
8192]`, so the set of tests that run is unchanged.
- A CPU-only test calls the requirement directly, following
`test_mm_mxfp8.py::test_trtllm_raises_for_linear_b_descale`. K = 256 and
512 are accepted; K = 384 and 640 must raise.
- A GPU test calls the public `gemm_fp8_nt_groupwise(...,
backend="trtllm")` at (M, N, K) = (64, 7168, 384) and expects the
`ValueError`, so the `@backend_requirement` wiring is covered too.
- `benchmarks/routines/gemm.py` drops trtllm when `k % 256 != 0` (was `k
< 256`), to match. That routine's compute-capability table does not list
trtllm yet, so for now the table drops it first.

Out of scope (the other two asks in the issue, both need GPU and cubin
work):
- making `selectHeuristic` validate the FP8 choice and fall back only to
`dsFp8` configs;
- shipping a non-`u2` `dsFp8` kernel so that K % 256 == 128 can be
supported. Once one exists, this check should be relaxed.

Validated on CPU only. The trtllm kernel path itself was not exercised
(no GPU here):

```
$ python -m pytest -v tests/gemm/test_groupwise_scaled_gemm_fp8.py -k test_fp8_groupwise_gemm_trtllm_k_requirement -p no:cacheprovider
# this branch
tests/gemm/test_groupwise_scaled_gemm_fp8.py::test_fp8_groupwise_gemm_trtllm_k_requirement[256-True] PASSED [ 25%]
tests/gemm/test_groupwise_scaled_gemm_fp8.py::test_fp8_groupwise_gemm_trtllm_k_requirement[384-False] PASSED [ 50%]
tests/gemm/test_groupwise_scaled_gemm_fp8.py::test_fp8_groupwise_gemm_trtllm_k_requirement[512-True] PASSED [ 75%]
tests/gemm/test_groupwise_scaled_gemm_fp8.py::test_fp8_groupwise_gemm_trtllm_k_requirement[640-False] PASSED [100%]
====================== 4 passed, 4085 deselected in 0.91s ======================

$ python -m pytest -q tests/gemm/test_groupwise_scaled_gemm_fp8.py -k test_fp8_groupwise_gemm_trtllm_k_requirement -p no:cacheprovider
# same test against main's gemm_base.py
E           Failed: DID NOT RAISE ValueError
E           Failed: DID NOT RAISE ValueError
FAILED tests/gemm/test_groupwise_scaled_gemm_fp8.py::test_fp8_groupwise_gemm_trtllm_k_requirement[384-False]
FAILED tests/gemm/test_groupwise_scaled_gemm_fp8.py::test_fp8_groupwise_gemm_trtllm_k_requirement[640-False]
2 failed, 2 passed, 4085 deselected in 0.96s
```

## 🔍 Related Issues

#6149 (this addresses ask 1; asks 2 and 3 remain open)

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

- `pre-commit run --files` on the three changed files passes. The
full-repo run and the GPU test suite were not run here.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

- **Bug Fixes**
- TensorRT-LLM groupwise FP8 GEMM now validates that the contraction
dimension is at least 256 and divisible by 256. Unsupported dimensions
raise a clear error; use the CUTLASS backend for dimensions that are not
divisible by 256.

- **Tests**
- Expanded coverage for supported and unsupported contraction
dimensions, including checks for the validation error.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Zhaowei Gu <83746079+zw-g@users.noreply.github.com>

### [b856fee](https://github.com/flashinfer-ai/flashinfer/commit/b856feeec5aa1ef132d7811382de99b8890b0c65)

- **作者**: Zhaowei Gu
- **时间**: 2026-11-17T21:30:46Z
- **提交信息**: fix(gemm): reject K not divisible by 128 for cute-dsl mm_bf16 at M <= 32 (#8033)

<!-- .github/pull_request_template.md -->

## 📌 Description

`mm_bf16(..., backend="cute-dsl")` with M <= 32 and a K that is not a
multiple of 128 (K=320 in #7966) fails with a message from inside the
split-K tactic validation that blames the wrong condition:

```
K=320 with CTA_K=128 does not divide evenly across split_k=1
```

`_cute_dsl_mm_bf16_requirement` never checks K for M <= 32. It calls
`default_tactic()` from `dense_bf16_gemm_sm100_splitk.py`, whose
`validate_tactic` folds `k % _CTA_K` and the split-K divisibility into
one condition with one message. None of the three low-M kernels can
serve such a K: cluster split-K needs K % 128 == 0, warp split-K needs a
positive multiple of 128, and direct needs K % 256 == 0.

This PR checks K in the requirement, before the kernel module is
imported, and raises a `ValueError` that names the real condition:

```
The CuTeDSL low-M backend requires K to be a positive multiple of 128 for M <= 32, got K=320.
```

- The set of accepted shapes does not change: every K the new check
rejects (K <= 0 or K % 128 != 0) was already rejected by
`validate_tactic`. Only the place and the wording change.
- `backend="auto"` is unaffected. It already skipped cute-dsl for these
shapes, because `suitable_auto_backends` catches the requirement's
`ValueError`, and it still does.
- The `mm_bf16` docstring now states the K limit for M <= 32.
- New CPU-only test
`tests/cpu/gemm/test_mm_bf16_cute_dsl_requirement.py`
(`@pytest.mark.cpu_only`). It calls the public `mm_bf16` with an SM100
device, `is_sm100a_supported` and `is_cute_dsl_available` monkeypatched,
for (M, K) = (1, 320), (32, 320), (8, 0), (8, 192), and checks that
`backend="auto"` still accepts M=33, K=320 (K is not checked above M =
32).

`validate_tactic` in `dense_bf16_gemm_sm100_splitk.py` now reports `K
must be a positive multiple of CTA_K=128, got <K>` on its own, so a
`skip_check=True` call at K=320 also gets the real reason. The `does not
divide evenly across split_k=...` message stays for the split-K case.

Validated on a CPU-only machine (no GPU, no cutlass / cuda-python), so
the kernels were not run.

```
$ python -m pytest -v -p no:cacheprovider tests/cpu/gemm/test_mm_bf16_cute_dsl_requirement.py
# this branch
tests/cpu/gemm/test_mm_bf16_cute_dsl_requirement.py::test_low_m_rejects_k_not_divisible_by_128[1-320] PASSED
tests/cpu/gemm/test_mm_bf16_cute_dsl_requirement.py::test_low_m_rejects_k_not_divisible_by_128[32-320] PASSED
tests/cpu/gemm/test_mm_bf16_cute_dsl_requirement.py::test_low_m_rejects_k_not_divisible_by_128[8-0] PASSED
tests/cpu/gemm/test_mm_bf16_cute_dsl_requirement.py::test_low_m_rejects_k_not_divisible_by_128[8-192] PASSED
tests/cpu/gemm/test_mm_bf16_cute_dsl_requirement.py::test_m_above_32_accepts_k_not_divisible_by_128 PASSED
5 passed in 0.28s
```

On main the same test fails. On a CPU-only machine main's requirement
first stops at the kernel-module import (`ModuleNotFoundError: No module
named 'cuda'`, 4 failed, 1 passed). With the tactic-selection code of
`dense_bf16_gemm_sm100_splitk.py` (everything above `__all__`) loaded
without its cutlass / cuda-python imports, and the SM100 shared-memory
size stubbed, main's requirement produces the message from the issue:

```
# main's gemm_base.py
E     Actual message: 'K=320 with CTA_K=128 does not divide evenly across split_k=1'
E     Actual message: 'K=320 with CTA_K=128 does not divide evenly across split_k=1'
E     Actual message: 'K=0 with CTA_K=128 does not divide evenly across split_k=1'
E     Actual message: 'K=192 with CTA_K=128 does not divide evenly across split_k=1'
4 failed, 1 passed in 0.30s
```

`pre-commit run --files` on the changed files passes, including mypy,
ruff check and ruff format.

## 🔍 Related Issues

Fixes #7966

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
reviewers may adjust):
`tests/cpu/gemm/test_mm_bf16_cute_dsl_requirement.py
tests/gemm/test_mm_bf16.py`

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

- Rejecting, rather than routing such K to cuBLASLt inside
`backend="cute-dsl"`, follows the issue's first ask and the scope of
this backend (low-M kernels for M <= 32). `auto` already picks another
backend for these shapes.
- The literal 128 follows the existing `a.shape[1] % 128` checks in
`gemm_base.py`. Importing `_CTA_K` would load the cutlass-dependent
kernel module.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Invalid `mm_bf16` inputs with M ≤ 32 now raise a clear error when K is
nonpositive or not divisible by 128.
* Split-K operations now distinguish invalid K values from valid K
values that cannot be evenly partitioned, providing the appropriate
validation error.
* **Documentation**
  * Clarified the K requirement for `mm_bf16` when M ≤ 32.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Zhaowei Gu <83746079+zw-g@users.noreply.github.com>

### [a854f7c](https://github.com/flashinfer-ai/flashinfer/commit/a854f7c56fb1b823b2a2e6dbebb1732c3b8c02a1)

- **作者**: Sam
- **时间**: 2026-11-17T21:29:24Z
- **提交信息**: fix: read PDL-produced inputs after griddepcontrol.wait in cluster top-k, mm_fp4 and mm_bf16_fp4 CuTe-DSL kernels (#7288)

<!-- .github/pull_request_template.md -->

## 📌 Description

Some Blackwell kernels read inputs from the previous kernel before
`griddepcontrol.wait`. With PDL on, they can read stale values.

- `fast_topk_clusters_exact` (`pdl=True`): the three kernels wait only
inside `fast_topk_cuda_v4`, which runs when `seq_len > TopK`. The
copy-through path for shorter rows reads `logits`, `seq_lens`,
`page_table` and `offsets` without waiting. The wait moves to the kernel
entry.
- `mm_fp4` CuTe-DSL dense kernels (SM100, SM100 split-K, SM103, SM120
b12x): `alpha[0]` is read at kernel entry, before the existing wait. It
is now read right after the wait.
- `mm_fp4` `cutedsl_low_latency`: only the B DMA warp waits. The
epilogue reads the bias after a barrier that warp arrives on once it has
waited, but it read `mScale[0]` without that barrier. The scale now goes
through the same barrier.
- `mm_bf16_fp4` CuTe-DSL (SM100 W4A16): only the activation TMA warp
waits. The epilogue read `alpha[group_idx]` as soon as the scheduler
published the tile, before the accumulator was ready, so the first tile
of each CTA could use a stale alpha. It now reads alpha after the
accumulator wait. The SM12x W4A16 kernels already read alpha after a
wait.

## 🔍 Related Issues

Follow-up to #6322 and #7188.

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

The new tests use `late_store` from #7188 (same file). It triggers the
dependent launch, then writes one input late; each test compares the
output bitwise against a normal run.

| B200 (SM100) | Before | After |
|---|---|---|
| `test_topk_clusters_pdl_waits_before_reading` (exact, page_table,
ragged) | 3 failed | 3 passed |
| `test_mm_fp4_pdl_waits_for_alpha` (cute-dsl, cutedsl_low_latency) | 2
failed | 2 passed |
| `test_mm_bf16_fp4_pdl_waits_for_alpha` (cute-dsl) | failed | passed |

| RTX 5080 (SM120) | Before | After |
|---|---|---|
| `test_mm_fp4_pdl_waits_for_alpha` (b12x) | failed | passed |

Also run on B200 with this PR: `test_mm_fp4` for the CuTe-DSL backends,
`test_mm_fp4_per_token_alpha*` and `test_topk_clusters_exact_*`, 403
passed.
For the W4A16 change, `tests/gemm/test_mm_bf16_fp4.py -k "pdl_waits or
cute-dsl"` on B200: 117 passed.

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

- The SM103 kernel gets the same change as SM100 but was not run; I have
no SM103 GPU.
- The `cutlass` backend of `mm_fp4` has the same issue inside CUTLASS
(the epilogue loads `alpha_ptr` before the wait). That fix is
NVIDIA/cutlass#3786; the test case can be added with the submodule bump.
- #6322 also adds `tests/test_helpers/pdl.py`; whichever PR lands second
takes the #7188 version.
- `/bot run tests/utils/test_topk.py tests/gemm/test_mm_fp4.py
tests/gemm/test_mm_bf16_fp4.py`


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved reliability of GEMM operations with programmatic dependent
launch (PDL) enabled. Output scaling, bias, and alpha values are now
handled in the correct synchronization order across supported variants,
helping produce consistent results.
* Improved correctness of exact, page-table, and ragged cluster top-k
operations when PDL is enabled, including cases where rows contain fewer
elements than the requested top-k.
* Added regression coverage for GEMM and cluster top-k results when
inputs or scaling values are updated during PDL execution.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: almightychang (Sam, Joochul Chang) <almightychang@icloud.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [6206e83](https://github.com/flashinfer-ai/flashinfer/commit/6206e833a0880b3516e27fc26e784be2fbeded19)

- **作者**: eigen
- **时间**: 2026-11-17T21:26:06Z
- **提交信息**: perf(cake_sage_block_sparse_attention): overlapped tile epilogue for mid-sparsity rows and faster tail split on SM100/SM103 (#9605)

The Sage FP8 block-sparse attention kernels use FP8 E4M3 Q/K/V with
per-token Q scales, per-16-token K scales and per-channel V scales, and
select KV blocks block-sparsely. Rows with 6 to 23 selected KV blocks
per row on sm_100a, and 16 to 23 on sm_103a, now run a build that hands
each tile's output merge and store to a separate warpgroup, so this work
overlaps the next tile. That build is used only when the call has at
least twice as many tiles as SMs, and other rows keep their route. On
sm_103a, that build now rescales the output in four 16-column parts, so
it compiles without spilling registers. The attention builds now store
the output in whole 32-byte sectors, and in the tail-split build (the
2-CTA split of the partial last wave) the two CTAs of a split tile now
fold the tile in halves at the same time instead of one CTA folding all
of it. Outputs are unchanged.

Compared with the previous Cake version of this kernel (current
FlashInfer main), the combined-API speedup under CUDA graph is 0.994x to
1.069x on B200 and 0.993x to 1.062x on GB300 across all 15 measured
rows. The largest gains are on the sel 6 rows: B1/H32/Hkv8/S4096 sel 6
at 1.069x on B200 and 1.062x on GB300, and B8/H32/Hkv32/S4096 sel 6 at
1.048x on B200 and 1.049x on GB300. No row counts as slower, which would
need the median paired ratio to exceed 1 by more than the run-to-run
noise and this PR to be slower in at least 14 of 16 rounds. The cells
below 1.000 on B200 are B8/H32/Hkv32/S4096 sel 58 (0.994 combined API)
and B1/H2/Hkv2/S4096 sel 58 (0.998 combined API). On GB300 they are
B1/H40/Hkv40/S32768 sel 256 (0.993 combined API) and B1/H2/Hkv2/S4096
sel 58 (0.998 combined API, 0.991 quantize + attention). All of these
cells are within noise except the 0.991 cell, whose median paired ratio
(1.009) is just above its noise (0.007) with this PR slower in 13 of 16
rounds; it measured 0.996 in a rerun on a second GB300.

Latencies are medians over 16 paired rounds of CUDA graph replay.
Speedup is main latency divided by this PR's latency, so a value above 1
means this PR is faster. `sel` is the number of KV blocks selected per
row. Head dim is 128, and B, H, Hkv and S are batch, query heads, KV
heads and sequence length.

**NVIDIA B200 (sm_100a, 148 SMs), CUDA 13.3 (torch
2.13.0a0+9186a08b2c.nv26.07)**

| shape | sel | main, combined API, graph (µs) | this PR (µs) | speedup
| main, quantize + attention, graph (µs) | this PR (µs) | speedup |
|---|---:|---:|---:|---:|---:|---:|---:|
| B8/H32/Hkv32/S4096 | 6 | 484.98 | 462.96 | 1.048 | 485.14 | 463.18 |
1.047 |
| B8/H32/Hkv32/S4096 | 32 | 1198.83 | 1176.29 | 1.019 | 1190.09 |
1184.45 | 1.005 |
| B8/H32/Hkv32/S4096 | 58 | 1919.15 | 1930.66 | 0.994 | 1927.91 |
1909.15 | 1.010 |
| B1/H8/Hkv8/S4096 | 6 | 23.79 | 22.78 | 1.044 | 23.76 | 22.80 | 1.042 |
| B1/H8/Hkv8/S4096 | 32 | 48.61 | 47.23 | 1.029 | 48.67 | 47.25 | 1.030
|
| B1/H8/Hkv8/S4096 | 58 | 69.78 | 68.62 | 1.017 | 69.77 | 68.65 | 1.016
|
| B1/H40/Hkv40/S32768 | 51 | 2268.81 | 2201.19 | 1.031 | 2256.13 |
2206.95 | 1.022 |
| B1/H40/Hkv40/S32768 | 128 | 5029.30 | 4981.15 | 1.010 | 5032.90 |
5031.29 | 1.000 |
| B1/H40/Hkv40/S32768 | 256 | 9485.97 | 9447.73 | 1.004 | 9496.70 |
9433.63 | 1.007 |
| B2/H24/Hkv24/S16384 | 32 | 889.69 | 871.48 | 1.021 | 890.33 | 872.58 |
1.020 |
| B1/H2/Hkv2/S4096 | 6 | 12.22 | 12.19 | 1.002 | 12.27 | 12.17 | 1.008 |
| B1/H2/Hkv2/S4096 | 58 | 25.14 | 25.18 | 0.998 | 25.25 | 25.17 | 1.003
|
| B1/H4/Hkv4/S4096 | 6 | 15.67 | 15.49 | 1.012 | 15.75 | 15.51 | 1.015 |
| B1/H4/Hkv4/S4096 | 58 | 41.26 | 41.27 | 1.000 | 41.35 | 41.25 | 1.002
|
| B1/H32/Hkv8/S4096 | 6 | 55.66 | 52.09 | 1.069 | 55.67 | 52.11 | 1.068
|

**NVIDIA GB300 (sm_103a, 152 SMs), CUDA 13.3 (torch
2.13.0a0+9186a08b2c.nv26.07)**

| shape | sel | main, combined API, graph (µs) | this PR (µs) | speedup
| main, quantize + attention, graph (µs) | this PR (µs) | speedup |
|---|---:|---:|---:|---:|---:|---:|---:|
| B8/H32/Hkv32/S4096 | 6 | 450.66 | 429.63 | 1.049 | 450.48 | 429.66 |
1.048 |
| B8/H32/Hkv32/S4096 | 32 | 954.14 | 940.24 | 1.015 | 954.25 | 940.03 |
1.015 |
| B8/H32/Hkv32/S4096 | 58 | 1436.54 | 1427.36 | 1.006 | 1436.89 |
1427.88 | 1.006 |
| B1/H8/Hkv8/S4096 | 6 | 22.02 | 21.45 | 1.027 | 22.05 | 21.45 | 1.028 |
| B1/H8/Hkv8/S4096 | 32 | 40.14 | 38.42 | 1.045 | 40.06 | 38.40 | 1.043
|
| B1/H8/Hkv8/S4096 | 58 | 55.71 | 54.14 | 1.029 | 55.71 | 54.14 | 1.029
|
| B1/H40/Hkv40/S32768 | 51 | 1675.66 | 1645.58 | 1.018 | 1677.05 |
1645.76 | 1.019 |
| B1/H40/Hkv40/S32768 | 128 | 3587.88 | 3550.00 | 1.011 | 3532.70 |
3514.30 | 1.005 |
| B1/H40/Hkv40/S32768 | 256 | 6664.62 | 6712.06 | 0.993 | 6716.30 |
6717.01 | 1.000 |
| B2/H24/Hkv24/S16384 | 32 | 720.41 | 701.83 | 1.026 | 720.50 | 701.79 |
1.027 |
| B1/H2/Hkv2/S4096 | 6 | 11.60 | 11.55 | 1.004 | 11.54 | 11.53 | 1.001 |
| B1/H2/Hkv2/S4096 | 58 | 20.78 | 20.82 | 0.998 | 20.67 | 20.86 | 0.991
|
| B1/H4/Hkv4/S4096 | 6 | 14.84 | 14.62 | 1.015 | 14.76 | 14.66 | 1.007 |
| B1/H4/Hkv4/S4096 | 58 | 33.44 | 33.29 | 1.005 | 33.37 | 33.30 | 1.002
|
| B1/H32/Hkv8/S4096 | 6 | 50.29 | 47.34 | 1.062 | 50.28 | 47.30 | 1.063
|

The same FP8 attention also runs on pre-quantized E4M3 inputs
(`bsa_attn_sm100_sage_fwd_cake`) or behind the fused BF16 quantizer
(`sage_fp8_quantize_sm100`, `bsa_attn_sm100_sage_quantize_fwd_cake`) on
sm_100a and sm_103a, and the family's INT8-QK / FP8-PV variant
(`bsa_attn_sm120_blk64_sage_fwd_cake`) ships for SM120.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added a block-sparse attention route for supported SM100 and SM103
workloads, with optional PDL execution.
* Expanded block-sparse attention support on these architectures with
additional kernel implementations.
* **Performance**
  * Improved attention output processing with vectorized writes.
* **Bug Fixes**
* Improved output handling for buffers that are not aligned to 32 bytes,
while preserving data outside the output view.
* Expanded coverage for routed execution across tile counts and
selection sizes.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [c66d201](https://github.com/flashinfer-ai/flashinfer/commit/c66d2015008d1e8d9089c5653dfaab06e25dec45)

- **作者**: Akaash Parthasarathy
- **时间**: 2026-11-17T19:52:33Z
- **提交信息**: feat(moe_ep): refresh SM107 MegaMoE sources and adapter (#9426)

<!-- .github/pull_request_template.md -->

## 📌 Description

Update the Rubin standard and GenPhase MegaMoE sources to `70a6878d`,
with retained fixes recorded in the export manifest.

- **Standard workspace:** Allocate the native temporary buffer
separately and retain it across CUDA graph replay.
- **Epilogue controls:** Expose `use_tanh_sigmoid` and
`epilogue_warpgroups`. Two warpgroups require standard inference with
BF16 bulk combine and `epi_warps` token return.
- **GenPhase:** Update gather, communication and tail handling, fix
padded Gather4 row IDs and cluster-exit synchronization, and admit NVFP4
N64 tiles through explicit knobs.
- **Communication lifetime:** Alternate GenPhase LL inboxes, clear stale
history at tag rollover and complete FC1-row bulk stores before
publishing READY counters. Validate multi-stage dispatch scale groups
and match token-back copies to their allocated staging chunks.
- **Reduction:** Use the shared reducer, with self-validating BF16
combine for GenPhase top-k up to 31 and static reduction for larger
top-k, including shared fusion.
- **Shared experts:** Expose a replicated MXFP8 shared FFN in standard
and GenPhase, including weight preparation, input staging and addition
to the routed output.
- **Deduplicated combine:** Expose owner-side reduction before
rank-major return in standard inference, with early routing weights and
BF16 bulk combine.
- **Adapter correctness:** Retain shared weights through pooled
workspaces, captured replay and tuning/winner installation; include the
shared term in the sampled correctness reference. Accept typed or raw
E8M0 shared-input scales and preserve dedup settings in direct tuning
sweeps. Keep default Mega/split numerical contracts compatible.
- **Numerical compatibility:** Preserve main's batch-invariant paths,
initialize FC1 scale padding, apply split-CTA routing weights at the
selected stage and support 16-byte routed outputs with 128-bit
deduplicated stores.
- **Cache identity:** Include optional feature settings in workspace and
tuning keys, and distinguish native builds with different communication
settings.
- **Package and documentation:** Keep package-local imports and lazy
entry points, export shared helpers under `src/common/`, include the
manifest in wheels and document the export procedure.
- **Benchmark controls:** Add SiTU parameters, activation clamping,
routing-weight placement and the new epilogue options to the Rubin
benchmark.

Shared fusion and dedup are opt-in and do not implement the
batch-invariant contract. Decode/die-aware scheduling controls are not
exposed through the adapter. Backend defaults and the automatic search
grid are unchanged.

### Performance

The tables were collected at refresh revision `7e8ac619e`, before the
communication-lifetime fixes and optional adapter wiring in this update.
Shared fusion and dedup are disabled in these measurements.

Compare against FlashInfer `119cf05be`, whose vendored Rubin sources
match the original PR base `c07ac287f`. The GenPhase baseline also
includes the cluster-exit fix. Each pair uses the same Rubin GPUs,
inputs, software and timing settings. The tables measure individual
layers.

Each value is the median of three process repetitions, using the slowest
rank's median over 50 samples after 20 warmups. Measurements use CUDA
graphs, with L2 flushed outside each timed interval. Negative changes
mean lower latency.

The 3584/3072 shape uses 896 experts, top-k 16 and SiTU (beta 4, linear
beta 25). The 5120/2304 and 7168/3072 shapes use 384 experts, top-k 6
and SwiGLU clamped at 10. The 8192/2048 shape uses 512 experts, top-k 10
and unclamped SwiGLU. Format lists weights/activations, with one name
when both match. Input and combine are BF16 throughout.

#### Standard

EP4, complete forward including BF16 input staging and finalization.
Routing weights are applied late with separate reduction, except the
8192/2048 row, which uses early weights and in-kernel atomic reduction.

Both revisions are tuned independently over the 32 production
candidates, the default and 12 wider-tile one-stage FC2 variants. The
refresh also tests tanh sigmoid and two epilogue warpgroups where
supported. These are manual tuning results. The automatic search is
unchanged.

| H / I | Format (W/A) | Live / capacity | Routing | Tuned main (µs) |
Tuned refresh (µs) | Change | Default main (µs) | Default refresh (µs) |
Change |
|---|---|---:|---|---:|---:|---:|---:|---:|---:|
| 3584 / 3072 | MXFP4/MXFP8 | 128 / 128 | balanced | 338.69 | 338.96 |
+0.08% | 710.72 | 705.79 | -0.69% |
| 3584 / 3072 | MXFP4/MXFP8 | 2048 / 2048 | balanced | 467.68 | 450.22 |
-3.73% | 1547.58 | 1491.01 | -3.66% |
| 3584 / 3072 | MXFP4/MXFP8 | 8192 / 8192 | balanced | 1820.46 | 1756.66
| -3.51% | 4952.83 | 4586.82 | -7.39% |
| 3584 / 3072 | NVFP4 | 128 / 128 | balanced | 353.04 | 353.23 | +0.05%
| 571.55 | 564.61 | -1.21% |
| 3584 / 3072 | NVFP4 | 2048 / 2048 | balanced | 429.14 | 427.09 |
-0.48% | 1398.62 | 1289.78 | -7.78% |
| 3584 / 3072 | NVFP4 | 8192 / 8192 | balanced | 1179.86 | 1104.21 |
-6.41% | 4508.85 | 4216.05 | -6.49% |
| 5120 / 2304 | MXFP4 | 128 / 128 | balanced | 180.16 | 178.66 | -0.83%
| 205.34 | 205.26 | -0.04% |
| 5120 / 2304 | MXFP4/MXFP8 | 512 / 512 | power-law | 201.97 | 199.68 |
-1.13% | 263.58 | 263.20 | -0.15% |
| 5120 / 2304 | MXFP8 E4M3 | 128 / 128 | balanced | 302.50 | 301.74 |
-0.25% | 333.30 | 333.49 | +0.06% |
| 5120 / 2304 | MXFP8 E5M2 | 128 / 128 | balanced | 302.08 | 301.65 |
-0.14% | 333.20 | 333.36 | +0.05% |
| 7168 / 3072 | NVFP4 | 512 / 512 | balanced | 316.66 | 317.01 | +0.11%
| 347.90 | 349.01 | +0.32% |
| 8192 / 2048 | NVFP4 | 32 / 64 | balanced | 304.72 | 303.50 | -0.40% |
377.89 | 374.61 | -0.87% |

#### GenPhase

EP4 and EP8, kernel execution with inputs already staged, including
reset and reduction. "Early / atomic" applies routing weights before FC2
and reduces in the kernel. "Late / separate" applies weights after FC2
and uses a separate BF16 reducer. Each row uses the same weighting and
reduction on both revisions.

Tuned values reuse the earlier shortlist comparison, with a separate
configuration selected for each revision. This is not a full-grid or
automatic-tuner result. Default and tuned runs use separate allocations,
with the same GPUs for each before/after pair. Standard timings include
input staging; GenPhase timings exclude it, so the tables cannot be used
to choose between variants.

| EP | H / I | Format (W/A) | Live / capacity | Routing; weights /
reduction | Tuned main (µs) | Tuned refresh (µs) | Change | Default main
(µs) | Default refresh (µs) | Change |
|---:|---|---|---:|---|---:|---:|---:|---:|---:|---:|
| 4 | 3584 / 3072 | MXFP4/MXFP8 | 128 / 128 | balanced; late / separate
| 513.20 | 319.87 | -37.67% | 973.62 | 555.33 | -42.96% |
| 4 | 5120 / 2304 | MXFP4/MXFP8 | 512 / 512 | power-law; early / atomic
| 244.64 | 183.78 | -24.88% | 362.77 | 230.94 | -36.34% |
| 4 | 7168 / 3072 | MXFP4/MXFP8 | 512 / 512 | balanced; early / atomic |
354.54 | 286.02 | -19.33% | 456.54 | 386.32 | -15.38% |
| 4 | 8192 / 2048 | NVFP4 | 32 / 64 | balanced; late / separate | 385.54
| 278.06 | -27.88% | 574.34 | 351.15 | -38.86% |
| 8 | 3584 / 3072 | MXFP4/MXFP8 | 128 / 128 | balanced; early / atomic |
281.70 | 177.94 | -36.83% | 467.14 | 302.78 | -35.18% |
| 8 | 3584 / 3072 | NVFP4 | 128 / 128 | balanced; early / atomic |
349.07 | 182.02 | -47.86% | 440.43 | 276.86 | -37.14% |
| 8 | 5120 / 2304 | MXFP4/MXFP8 | 512 / 512 | power-law; early / atomic
| 206.77 | 137.92 | -33.30% | 243.34 | 180.53 | -25.81% |
| 8 | 7168 / 3072 | MXFP4/MXFP8 | 512 / 512 | balanced; early / atomic |
189.33 | 171.55 | -9.39% | 243.15 | 228.35 | -6.09% |
| 8 | 8192 / 2048 | NVFP4 | 32 / 64 | balanced; early / atomic | 227.49
| 159.07 | -30.07% | 324.18 | 195.18 | -39.79% |

## 🔍 Related Issues

None.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks on the changed files with `pre-commit run
--files ...` and fixed any reported issues.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] Affected host tests and GPU qualification pass.
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: targeted MoE EP package, adapter and Rubin GPU coverage is
sufficient.

846 host tests, 11 portable CUDA staging tests, whole-tree mypy and
changed-file pre-commit checks pass. The host checks include the
two-rank allocation-failure and retry test. A four-GPU Rubin run also
passes 16 cases per rank for typed/raw shared scales, shared GenPhase
top-k 31/32/33 and multi-stage communication, with captured input/route
changes and numerical-reference checks. Public-layer GPU qualification
covers 55 feature cases at EP4/EP8, plus four partial-empty-rank cases
at EP8. The final EP8 run also passes 12 graph/epoch checks and four
lifecycle checks on every rank. Repeated exports reproduce all 69 native
files; installed-wheel imports and actual native constructors pass.
These runs establish correctness, not shared-expert or dedup speedups.

Suggested CI targets: `tests/moe_ep/test_provider_package.py
tests/moe_ep/test_sm107_block_scaled_contracts.py
tests/moe_ep/test_sm107_shared_expert.py
tests/moe_ep/test_sm107_native_communication.py
tests/moe_ep/test_sm107_runtime_options.py
tests/moe_ep/test_sm107_tuning.py
tests/moe_ep/test_sm107_tuning_protocol.py
tests/moe_ep/test_sm107_variant_selection.py
tests/moe_ep/test_sm107_genphase_kernel.py
tests/moe_ep/test_sm107_routing_graph_multirank.py
tests/moe_ep/test_moe_ep_sm107_block_scaled_mega_multirank.py
tests/moe_ep/test_megamoe_quantized_tiles_batch_invariant.py
tests/moe_ep/test_megamoe_numerical_variants.py
tests/cpu/test_sm107_benchmark.py tests/moe_ep/test_ep_selection.py
tests/moe_ep/test_sm107_torch_staging.py`

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

### [98f7877](https://github.com/flashinfer-ai/flashinfer/commit/98f7877d03e2f347ebe23fd40e343e0e3881db99)

- **作者**: Lee Nau
- **时间**: 2026-11-17T19:20:53Z
- **提交信息**: docs(gemm): correct the TGV epilogue's TMEM-load fence comment (#9545)

## 📌 Description

Comment-only change in `flashinfer/gemm/kernels/tgv_gemm_cute_ext.py`.

The comment above the epilogue's `fence_view_async_tmem_load()` said
that this fence makes the `tcgen05.ld` result visible to both the
`rAcc.load()` that follows and the MMA warp's `dealloc_tmem`. Since
#9337, the `tcgen05.fence::before_thread_sync` on the next line orders
the retired load before the dealloc. `fence_view_async_tmem_load()`
(`tcgen05.wait::ld`) only makes the loaded registers safe to read. The
new comment says which fence does what.

No code change: the generated kernel is identical.

## 🔍 Related Issues

Follow-up to #9337, from review notes on #9337 and #8787. #8787 does not
touch these lines, so the two PRs merge cleanly in either order.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

- [ ] Tests have been added or updated as needed. (Not applicable: the
change is to a comment only.)
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).

  Suggested CI test targets: none; the change is to a comment only.

## Reviewer Notes

Draft until #8787 merges, so this lands after the last functional TGV
change. AI-assisted (Claude Code).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Documentation**
* Clarified how asynchronous memory loads and synchronization relate to
data availability and memory deallocation. No executable behavior
changed.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [74cb235](https://github.com/flashinfer-ai/flashinfer/commit/74cb235c8be6d16adfb2b892f0d68f717fa2417a)

- **作者**: Vincent
- **时间**: 2026-11-17T19:04:14Z
- **提交信息**: perf(batch_invariant): prefill placements of the batch-invariant attention class (#9301)

## 📌 Description

Placements of the batch-invariant attention class of #8590 that speed up
prefill. The class is unchanged: the three fingerprints
(`attn-bf16-d64/128/256-...`) are the same literals, no term, spec or
Lean file changes, and every test of
`tests/attention/test_batch_invariant_attention.py` passes bit for bit
against the same references as before (R3: every placement computes the
same bits).

**Planner**

- **Split rule** (`plan.py`). The `"auto"` unit kind split every
multi-chunk Q tile whenever the fused unit count was below twice the SM
count. That rule fits decode units (a few live rows per unit) but not
prefill tiles: a split 128-row unit writes its 128 x D fp32 partial rows
and the fixup kernel folds them again, which costs more than the balance
the split buys on a part-filled machine. Units wider than
`INKERNEL_MAX_ROWS` now split under `"auto"` only when the fused units
would occupy under a quarter of the SMs (`WIDE_SPLIT_SM_FRACTION`);
narrow units keep the previous rule.
- **Snake unit order over the launch grid** (`plan.py`, `engine.py`).
The persistent CTAs walk units `u = bidx, bidx + grid, ...`; with the
longest-first order alone CTA 0 took the longest unit of every wave and
finished last. The waves now alternate direction (`snake_order`), with
the wave width taken from the launch grid, so the CTA that takes a
wave's longest unit takes the next wave's shortest; the paired
placement's pair table takes the same order. The order of units reaches
no value (every unit restarts its state).

**Kernel blocks**

- **One P store** (`blocks/softmax.py`). One
`St32x32bOp(Repetition(p_words))` writes the softmax warpgroup's packed
bf16 pairs from a single register block; the same values reach the same
TMEM columns in the same order.
- **Streamed exponentials** (`blocks/softmax.py`). The exponentials,
their bf16 words and the rowsum tree are emitted as one stream in key
order (the canonical adjacent pairwise tree, each level as soon as both
operands exist), so the P words take the registers of the scores they
came from. With two softmax warpgroups each loads only its key slice and
exchanges its slice maximum through shared memory (`fmax` is exact and
order-free); one warpgroup stays the default.
- **Correction warpgroup** (`blocks/correction.py`). With the merged
state in TMEM (D <= 128) a fused unit's last chunk is folded into it and
the accumulator stage is released before the output rows are normalised,
so the next unit's first PV does not wait for the epilogue. The rescale
issues the TMEM loads of several pieces before the first multiply
instead of one load round trip per piece, and the merge / normalisation
use the packed `f32x2` forms of the same per-element operations.
- **Whole-tile K / V ring slots at D = 256** (`blocks/kernel.py`,
`mma.py`, `operands.py`). Two whole-tile slots replace four half-tile
slots, so QK^T is one instruction per K-step; each slot's load is issued
a tile ahead of its use.

**Speedups over `main`** (same shapes, median of repeated graph replays,
ratio of the old time to the new time, geomean over a 36-shape prefill
grid and a 66 to 72-shape decode grid per head dim):

| | prefill D=64 | prefill D=128 | prefill D=256 | decode (all D) |
|---|---|---|---|---|
| GB200 | 1.22x | 1.32x | 1.30x | 1.00x |
| GB300 | 1.24x | 1.39x | 1.26x | 1.00x |

By regime, single-request prefill gains most (1x1K: 1.7x to 2.2x, 1x4K:
1.5x to 1.9x, 1x8K: 1.10x to 1.24x, 1x32K: 1.03x to 1.18x); many-request
prefill gains 1.01x to 1.12x; decode is within noise at every batch
size.

## 🔍 Related Issues

Follows #8590; tracked in #9009.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

- [x] Tests have been added or updated as needed: two device-free tests
pin the planner rules (`test_planner_unit_kind_rules`: the `"auto"` unit
kind for decode-sized and wide tiles; `test_planner_snake_order`: a
permutation of the longest-first list in alternating waves of the launch
grid). The existing bitwise suite covers the kernel placements (every
configuration, unit kind and softmax warpgroup count against the same
references).
- [x] All tests are passing:
`tests/attention/test_batch_invariant_attention.py` 96 / 96 on SM100
(GB200) and SM103 (GB300) on this branch merged with `main`; the
fingerprint pins unchanged; `tests/batch_invariant/test_lean.py`
device-free part 2 / 2.
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Improvements**
* Batch-invariant attention now processes key slices and combines
partial results more efficiently across supported execution layouts.
* Work planning now adapts tile splitting and processing order to
workload size and available compute resources.
* Attention output handling has been refined for different accumulator
placements and single- or multi-chunk workloads.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [306b1d9](https://github.com/flashinfer-ai/flashinfer/commit/306b1d9d1f68e18a5df99f33fcd00f5fc503de73)

- **作者**: seongyun.kim
- **时间**: 2026-11-17T18:08:02Z
- **提交信息**: test: cover large-vocab chain correction across scan chunks (#7572)

## 📌 Description

The chain speculative sampling distribution tests use `vocab=4`, leaving
the
scan carry across vocabulary chunks uncovered. Add a forced-rejection
case
with `vocab=32001` and equal residual mass at tokens 1, 31800 and 32000.
The last two support tokens share the final partial chunk, so its
interior
mass cannot be replaced by the last-valid-index fallback without
changing
the expected distribution.

Both deterministic modes check the correction distribution, output
support,
padding, and accepted/emitted counters. CPU controls cover balanced
mass,
complete endpoint collapse, and the interior tail mass moving to token
32000. The
new GPU cases share the existing chain distribution family's alpha
budget.

This is test-only; it changes no kernel or public API.

## 🔍 Related Issues

Follow-up to the non-blocking large-vocabulary suggestion in #6870:
https://github.com/flashinfer-ai/flashinfer/pull/6870

Part of the sampling validation work under #3605.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

All applicable hooks passed with `pre-commit run --files
tests/utils/test_sampling_fuzz.py`.
The repository-wide hook suite was not rerun.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

Validated revision: **`420be684107e3449b132d5749e47e661f20c96a5`**
(tree `f0a075d4dcfb88efcbf6e96c3249fb30f7ce0937`), based on previous
head
`f4c120d65a5cf431b2e0a790477e88428745ade5`.

### Current revision — Hyperstack Linux CPU validation passed

The candidate changes only `tests/utils/test_sampling_fuzz.py`: equal
mass
at 1/31800/32000, shared expected probabilities, a balanced CPU control,
and
a negative control for histogram mass `(1/3, 0, 2/3)`. Existing endpoint
negative controls and the separate `@_GPU_ONLY` decorators remain.
The GPU family has the same 12 regular + 2 large-vocabulary comparisons;
`alpha_per = 1e-5 / 14`. Deterministic CPU controls add no randomized
GPU
comparisons. The nominal asymptotic significance contract is unchanged.

On a GPU-free Hyperstack Linux CPU VM, the exact candidate commit/tree
was
verified before execution and the tracked source stayed unchanged
afterward.
Only this test file and its changed-file checks were run:

```bash
python -m pytest -q --confcutdir=tests/utils tests/utils/test_sampling_fuzz.py
# 72 passed, 414 CUDA skips, zero failures
pre-commit run --files tests/utils/test_sampling_fuzz.py
# All applicable hooks passed
git diff HEAD^ HEAD --check
# Passed; tracked source unchanged
```

The CPU tests accepted the balanced `(85,85,86)` histogram and rejected
the
`(85,0,171)` tail-fallback histogram, while retaining both
endpoint-collapse
negative controls. These four tests call the actual statistical gate.
Analytical Pearson values for the two constructed histograms are
chi-square
0.0078125/p≈0.9961 and 171.3359375/p≈6.24e-38, respectively. The
histograms
are constructed controls, not samples obtained by running GPU mutants.

Actual GPU detection of either kernel mutation is unverified for this
revision. The reviewer offered scoped CI after this update on
`tests/utils/test_sampling_fuzz.py`.

### Historical evidence — retained on its original revisions

- Integrated head `f4c120d65a` passed our normal Linux CPU run:
  70 passed and 414 CUDA skips, with changed-file pre-commit passing.
- In [YangXu1990uiuc's earlier
review](https://github.com/flashinfer-ai/flashinfer/pull/7572#pullrequestreview-5838562775),
`pytest tests/utils/test_sampling_fuzz.py -k chain` passed 29 cases on
each
  of A100, L40S, H100 NVL and B200 after resolving main `8e0a8afd6`.
  These are independent reviewer results.
- Our original head `f7ff79f69d` passed the two selected
large-vocabulary
  GPU cases on H100 NVL (CC 9.0, driver 580.173.02, CUDA 12.9,
  Python 3.11.13, torch 2.8.0+cu129).

These results used the earlier two-token oracle and do not validate this
three-token revision or establish sensitivity to the carry defects.
[kahyunnam's B200
review](https://github.com/flashinfer-ai/flashinfer/pull/7572#discussion_r4527956221)
found that both carry mutants passed the previous oracle. The original
cross-chunk sensitivity claim was therefore too strong.

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

The 256-row case uses about 98 MB of probability tensors. The
distributions
are deliberately sparse. The interior final-chunk support token is
intended
to distinguish correct carry from last-index fallback; actual GPU
mutation
detection remains pending scoped validation.
No performance benchmark or speedup claim is included. The change is
AI-assisted.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Tests**
* Added large-vocabulary speculative-sampling checks in deterministic
and nondeterministic modes, covering output padding, counters, supported
tokens, and distribution fit.
* Added CPU checks to reject collapsed endpoint mass or a missing
interior-tail carry, and to accept balanced counts across three tokens.
  * Updated significance thresholds to account for the additional cases.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: seongyun.kim <197560810+seongyun1104@users.noreply.github.com>

### [778f57e](https://github.com/flashinfer-ai/flashinfer/commit/778f57e4d73a73a439ad9cb88daabb5e14cbf816)

- **作者**: eigen
- **时间**: 2026-11-17T17:08:18Z
- **提交信息**: perf(cake_gdp): static decode programs for 2, 3, 5, 6, 7 and 16 tokens (#9613)

Cake Gated DeltaProduct (GDP) has four decode routes, `decode_nh1` to
`decode_nh4`, one for each number of Householder updates per token (n =
1, 2, 3 and 4). All four use head sizes K = 128 and V = 64, an FP32
recurrent state and fused q/k L2 normalization. Each route serves decode
and MTP verification on SM90, SM100 and SM103. A call launches the
static-token-count program for its token count T if one exists and that
program's band admits the call's batch x heads on the device's SM count.
Otherwise it launches the route's runtime-token-count program, which
handles any T up to 16. SM90 also has chunked varlen prefill programs.

This PR adds n = 3 static-token-count programs for T = 2, 3, 5, 6 and 7,
and for T = 16, on SM90, SM100 and SM103. Each architecture gets a
lane-owns-rows `l8r4` program for each of these six token counts. T = 5,
6, 7 and 16 also get an `l8r2` program. The `l8r2` program runs while
batch x heads fits in two CTAs per SM (one CTA per SM for the SM90 T =
16 program), and `l8r4` runs above that. Before this PR, these calls ran
the n = 3 runtime-token-count program, which is the previous Cake
version on FlashInfer main and the baseline below.

The tables cover 96 shapes per GPU: heads 80, 24, 20, 10 x batch 1, 16,
64, 256 x T 2, 3, 5, 6, 7, 16. Speedup is previous / this PR, using
median kernel time with both sides on the same GPU and CUDA 13.4:

- H100: geomean 1.5909x, min 1.1269x, max 2.7798x
- B200: geomean 1.6860x, min 1.3045x, max 3.0204x
- GB300: geomean 1.7573x, min 1.3750x, max 3.1563x

The other Cake GDP variants (the n = 1, 2 and 4 routes, the n = 3
programs for T = 1, 4 and 8, and the SM90 chunked varlen prefill
programs) are unchanged; the family ships on `sm_90a`, `sm_100a` and
`sm_103a`.

<details>
<summary>NVIDIA H100 80GB HBM3, SM90 (sm_90a, 132 SMs), CUDA 13.4:
median kernel time in microseconds</summary>

| T | heads | batch | previous Cake (us) | this PR (us) | speedup |
|---:|---:|---:|---:|---:|---:|
| 2 | 80 | 1 | 8.22 | 5.22 | 1.58x |
| 2 | 80 | 16 | 43.36 | 31.54 | 1.37x |
| 2 | 80 | 64 | 145.82 | 118.42 | 1.23x |
| 2 | 80 | 256 | 548.06 | 468.72 | 1.17x |
| 2 | 24 | 1 | 7.58 | 4.80 | 1.58x |
| 2 | 24 | 16 | 13.92 | 12.35 | 1.13x |
| 2 | 24 | 64 | 47.81 | 37.54 | 1.27x |
| 2 | 24 | 256 | 173.49 | 141.95 | 1.22x |
| 2 | 20 | 1 | 7.52 | 4.74 | 1.59x |
| 2 | 20 | 16 | 12.57 | 11.01 | 1.14x |
| 2 | 20 | 64 | 42.98 | 31.04 | 1.38x |
| 2 | 20 | 256 | 145.25 | 118.59 | 1.22x |
| 2 | 10 | 1 | 7.39 | 4.54 | 1.63x |
| 2 | 10 | 16 | 9.63 | 7.42 | 1.30x |
| 2 | 10 | 64 | 25.22 | 20.00 | 1.26x |
| 2 | 10 | 256 | 76.67 | 60.37 | 1.27x |
| 3 | 80 | 1 | 11.04 | 6.14 | 1.80x |
| 3 | 80 | 16 | 53.50 | 35.71 | 1.50x |
| 3 | 80 | 64 | 182.50 | 124.61 | 1.46x |
| 3 | 80 | 256 | 702.44 | 481.85 | 1.46x |
| 3 | 24 | 1 | 10.24 | 5.50 | 1.86x |
| 3 | 24 | 16 | 17.15 | 13.92 | 1.23x |
| 3 | 24 | 64 | 57.57 | 41.76 | 1.38x |
| 3 | 24 | 256 | 215.07 | 148.35 | 1.45x |
| 3 | 20 | 1 | 10.37 | 5.54 | 1.87x |
| 3 | 20 | 16 | 16.03 | 12.61 | 1.27x |
| 3 | 20 | 64 | 52.22 | 35.49 | 1.47x |
| 3 | 20 | 256 | 180.91 | 124.45 | 1.45x |
| 3 | 10 | 1 | 9.89 | 5.38 | 1.84x |
| 3 | 10 | 16 | 12.29 | 8.67 | 1.42x |
| 3 | 10 | 64 | 31.68 | 22.94 | 1.38x |
| 3 | 10 | 256 | 92.51 | 65.28 | 1.42x |
| 5 | 80 | 1 | 15.23 | 7.10 | 2.14x |
| 5 | 80 | 16 | 70.18 | 48.35 | 1.45x |
| 5 | 80 | 64 | 240.74 | 151.84 | 1.59x |
| 5 | 80 | 256 | 914.11 | 553.85 | 1.65x |
| 5 | 24 | 1 | 14.62 | 6.46 | 2.26x |
| 5 | 24 | 16 | 22.75 | 17.60 | 1.29x |
| 5 | 24 | 64 | 74.56 | 55.74 | 1.34x |
| 5 | 24 | 256 | 281.69 | 178.27 | 1.58x |
| 5 | 20 | 1 | 14.46 | 6.46 | 2.24x |
| 5 | 20 | 16 | 21.73 | 15.94 | 1.36x |
| 5 | 20 | 64 | 69.18 | 48.16 | 1.44x |
| 5 | 20 | 256 | 237.73 | 151.90 | 1.56x |
| 5 | 10 | 1 | 14.18 | 6.40 | 2.21x |
| 5 | 10 | 16 | 16.22 | 10.62 | 1.53x |
| 5 | 10 | 64 | 42.85 | 29.86 | 1.44x |
| 5 | 10 | 256 | 120.74 | 81.54 | 1.48x |
| 6 | 80 | 1 | 16.99 | 7.81 | 2.18x |
| 6 | 80 | 16 | 78.10 | 53.10 | 1.47x |
| 6 | 80 | 64 | 265.92 | 165.39 | 1.61x |
| 6 | 80 | 256 | 1020.23 | 604.19 | 1.69x |
| 6 | 24 | 1 | 16.10 | 7.13 | 2.26x |
| 6 | 24 | 16 | 25.18 | 19.30 | 1.31x |
| 6 | 24 | 64 | 82.22 | 59.63 | 1.38x |
| 6 | 24 | 256 | 314.32 | 194.43 | 1.62x |
| 6 | 20 | 1 | 16.00 | 7.10 | 2.25x |
| 6 | 20 | 16 | 24.03 | 17.54 | 1.37x |
| 6 | 20 | 64 | 76.80 | 52.80 | 1.45x |
| 6 | 20 | 256 | 263.01 | 165.60 | 1.59x |
| 6 | 10 | 1 | 15.74 | 7.07 | 2.23x |
| 6 | 10 | 16 | 18.11 | 11.93 | 1.52x |
| 6 | 10 | 64 | 47.87 | 33.47 | 1.43x |
| 6 | 10 | 256 | 133.50 | 89.98 | 1.48x |
| 7 | 80 | 1 | 19.58 | 8.54 | 2.29x |
| 7 | 80 | 16 | 87.09 | 56.19 | 1.55x |
| 7 | 80 | 64 | 298.00 | 181.90 | 1.64x |
| 7 | 80 | 256 | 1134.83 | 675.32 | 1.68x |
| 7 | 24 | 1 | 18.91 | 7.84 | 2.41x |
| 7 | 24 | 16 | 28.42 | 20.70 | 1.37x |
| 7 | 24 | 64 | 91.94 | 64.11 | 1.43x |
| 7 | 24 | 256 | 348.88 | 215.20 | 1.62x |
| 7 | 20 | 1 | 18.66 | 7.78 | 2.40x |
| 7 | 20 | 16 | 27.39 | 19.30 | 1.42x |
| 7 | 20 | 64 | 86.22 | 55.97 | 1.54x |
| 7 | 20 | 256 | 293.81 | 181.76 | 1.62x |
| 7 | 10 | 1 | 18.37 | 7.77 | 2.36x |
| 7 | 10 | 16 | 20.51 | 13.09 | 1.57x |
| 7 | 10 | 64 | 53.81 | 35.57 | 1.51x |
| 7 | 10 | 256 | 149.04 | 97.98 | 1.52x |
| 16 | 80 | 1 | 38.50 | 14.37 | 2.68x |
| 16 | 80 | 16 | 164.38 | 101.66 | 1.62x |
| 16 | 80 | 64 | 553.56 | 359.58 | 1.54x |
| 16 | 80 | 256 | 2156.42 | 1381.10 | 1.56x |
| 16 | 24 | 1 | 37.06 | 13.41 | 2.76x |
| 16 | 24 | 16 | 53.66 | 35.65 | 1.51x |
| 16 | 24 | 64 | 168.97 | 118.97 | 1.42x |
| 16 | 24 | 256 | 657.18 | 429.71 | 1.53x |
| 16 | 20 | 1 | 37.18 | 13.38 | 2.78x |
| 16 | 20 | 16 | 52.54 | 34.66 | 1.52x |
| 16 | 20 | 64 | 163.01 | 101.76 | 1.60x |
| 16 | 20 | 256 | 548.22 | 359.65 | 1.52x |
| 16 | 10 | 1 | 36.43 | 13.41 | 2.72x |
| 16 | 10 | 16 | 38.91 | 25.50 | 1.53x |
| 16 | 10 | 64 | 103.58 | 63.81 | 1.62x |
| 16 | 10 | 256 | 275.33 | 190.51 | 1.45x |

</details>

<details>
<summary>NVIDIA B200, SM100 (sm_100a, 148 SMs), CUDA 13.4: median kernel
time in microseconds</summary>

| T | heads | batch | previous Cake (us) | this PR (us) | speedup |
|---:|---:|---:|---:|---:|---:|
| 2 | 80 | 1 | 7.792 | 5.185 | 1.50x |
| 2 | 80 | 16 | 27.999 | 19.392 | 1.44x |
| 2 | 80 | 64 | 87.071 | 61.758 | 1.41x |
| 2 | 80 | 256 | 324.795 | 229.533 | 1.42x |
| 2 | 24 | 1 | 7.648 | 5.088 | 1.50x |
| 2 | 24 | 16 | 11.104 | 8.512 | 1.30x |
| 2 | 24 | 64 | 30.559 | 22.272 | 1.37x |
| 2 | 24 | 256 | 102.943 | 72.991 | 1.41x |
| 2 | 20 | 1 | 7.664 | 5.024 | 1.53x |
| 2 | 20 | 16 | 10.880 | 8.224 | 1.32x |
| 2 | 20 | 64 | 27.936 | 19.360 | 1.44x |
| 2 | 20 | 256 | 87.424 | 61.712 | 1.42x |
| 2 | 10 | 1 | 7.488 | 5.088 | 1.47x |
| 2 | 10 | 16 | 8.673 | 6.368 | 1.36x |
| 2 | 10 | 64 | 18.495 | 12.736 | 1.45x |
| 2 | 10 | 256 | 46.591 | 33.376 | 1.40x |
| 3 | 80 | 1 | 10.816 | 5.856 | 1.85x |
| 3 | 80 | 16 | 36.383 | 22.368 | 1.63x |
| 3 | 80 | 64 | 113.695 | 72.287 | 1.57x |
| 3 | 80 | 256 | 422.729 | 268.236 | 1.58x |
| 3 | 24 | 1 | 10.624 | 5.632 | 1.89x |
| 3 | 24 | 16 | 14.768 | 9.951 | 1.48x |
| 3 | 24 | 64 | 39.104 | 26.016 | 1.50x |
| 3 | 24 | 256 | 134.558 | 85.439 | 1.57x |
| 3 | 20 | 1 | 10.464 | 5.648 | 1.85x |
| 3 | 20 | 16 | 14.432 | 9.664 | 1.49x |
| 3 | 20 | 64 | 36.224 | 22.463 | 1.61x |
| 3 | 20 | 256 | 113.246 | 72.415 | 1.56x |
| 3 | 10 | 1 | 10.240 | 5.536 | 1.85x |
| 3 | 10 | 16 | 11.488 | 7.328 | 1.57x |
| 3 | 10 | 64 | 23.712 | 14.528 | 1.63x |
| 3 | 10 | 256 | 60.576 | 39.519 | 1.53x |
| 5 | 80 | 1 | 15.040 | 7.072 | 2.13x |
| 5 | 80 | 16 | 50.495 | 30.768 | 1.64x |
| 5 | 80 | 64 | 158.510 | 102.815 | 1.54x |
| 5 | 80 | 256 | 599.991 | 385.610 | 1.56x |
| 5 | 24 | 1 | 14.816 | 6.752 | 2.19x |
| 5 | 24 | 16 | 20.575 | 13.280 | 1.55x |
| 5 | 24 | 64 | 55.087 | 35.999 | 1.53x |
| 5 | 24 | 256 | 189.565 | 121.790 | 1.56x |
| 5 | 20 | 1 | 14.736 | 6.688 | 2.20x |
| 5 | 20 | 16 | 20.256 | 12.896 | 1.57x |
| 5 | 20 | 64 | 50.143 | 30.784 | 1.63x |
| 5 | 20 | 256 | 159.422 | 102.814 | 1.55x |
| 5 | 10 | 1 | 14.688 | 6.752 | 2.18x |
| 5 | 10 | 16 | 16.160 | 9.760 | 1.66x |
| 5 | 10 | 64 | 32.640 | 19.328 | 1.69x |
| 5 | 10 | 256 | 84.287 | 55.551 | 1.52x |
| 6 | 80 | 1 | 17.056 | 7.424 | 2.30x |
| 6 | 80 | 16 | 56.047 | 35.839 | 1.56x |
| 6 | 80 | 64 | 177.453 | 119.134 | 1.49x |
| 6 | 80 | 256 | 668.358 | 446.521 | 1.50x |
| 6 | 24 | 1 | 16.576 | 7.136 | 2.32x |
| 6 | 24 | 16 | 22.975 | 15.136 | 1.52x |
| 6 | 24 | 64 | 61.727 | 42.048 | 1.47x |
| 6 | 24 | 256 | 212.124 | 141.086 | 1.50x |
| 6 | 20 | 1 | 16.448 | 7.200 | 2.28x |
| 6 | 20 | 16 | 22.528 | 14.815 | 1.52x |
| 6 | 20 | 64 | 56.256 | 35.872 | 1.57x |
| 6 | 20 | 256 | 177.629 | 119.230 | 1.49x |
| 6 | 10 | 1 | 15.936 | 7.088 | 2.25x |
| 6 | 10 | 16 | 17.439 | 10.528 | 1.66x |
| 6 | 10 | 64 | 36.736 | 22.560 | 1.63x |
| 6 | 10 | 256 | 94.718 | 64.544 | 1.47x |
| 7 | 80 | 1 | 19.647 | 8.032 | 2.45x |
| 7 | 80 | 16 | 64.927 | 39.104 | 1.66x |
| 7 | 80 | 64 | 206.109 | 131.070 | 1.57x |
| 7 | 80 | 256 | 779.620 | 492.376 | 1.58x |
| 7 | 24 | 1 | 19.072 | 7.712 | 2.47x |
| 7 | 24 | 16 | 26.527 | 16.447 | 1.61x |
| 7 | 24 | 64 | 70.782 | 46.047 | 1.54x |
| 7 | 24 | 256 | 244.364 | 155.518 | 1.57x |
| 7 | 20 | 1 | 19.264 | 7.712 | 2.50x |
| 7 | 20 | 16 | 25.823 | 16.032 | 1.61x |
| 7 | 20 | 64 | 64.383 | 39.263 | 1.64x |
| 7 | 20 | 256 | 204.782 | 131.358 | 1.56x |
| 7 | 10 | 1 | 18.879 | 7.712 | 2.45x |
| 7 | 10 | 16 | 20.064 | 11.616 | 1.73x |
| 7 | 10 | 64 | 41.920 | 24.512 | 1.71x |
| 7 | 10 | 256 | 108.574 | 71.070 | 1.53x |
| 16 | 80 | 1 | 39.263 | 13.088 | 3.00x |
| 16 | 80 | 16 | 127.646 | 75.614 | 1.69x |
| 16 | 80 | 64 | 410.507 | 266.332 | 1.54x |
| 16 | 80 | 256 | 1558.986 | 1016.929 | 1.53x |
| 16 | 24 | 1 | 38.368 | 12.703 | 3.02x |
| 16 | 24 | 16 | 51.935 | 29.632 | 1.75x |
| 16 | 24 | 64 | 141.678 | 90.079 | 1.57x |
| 16 | 24 | 256 | 486.105 | 316.715 | 1.53x |
| 16 | 20 | 1 | 38.367 | 12.736 | 3.01x |
| 16 | 20 | 16 | 51.231 | 29.312 | 1.75x |
| 16 | 20 | 64 | 127.710 | 75.743 | 1.69x |
| 16 | 20 | 256 | 409.466 | 266.620 | 1.54x |
| 16 | 10 | 1 | 37.728 | 12.640 | 2.98x |
| 16 | 10 | 16 | 39.167 | 20.991 | 1.87x |
| 16 | 10 | 64 | 82.591 | 45.552 | 1.81x |
| 16 | 10 | 256 | 215.085 | 141.406 | 1.52x |

</details>

<details>
<summary>NVIDIA GB300, SM103 (sm_103a, 152 SMs), CUDA 13.4: median
kernel time in microseconds</summary>

| T | heads | batch | previous Cake (us) | this PR (us) | speedup |
|---:|---:|---:|---:|---:|---:|
| 2 | 80 | 1 | 8.000 | 4.992 | 1.60x |
| 2 | 80 | 16 | 26.528 | 18.080 | 1.47x |
| 2 | 80 | 64 | 83.040 | 56.640 | 1.47x |
| 2 | 80 | 256 | 310.352 | 214.880 | 1.44x |
| 2 | 24 | 1 | 7.808 | 4.768 | 1.64x |
| 2 | 24 | 16 | 11.264 | 8.192 | 1.38x |
| 2 | 24 | 64 | 28.768 | 20.768 | 1.39x |
| 2 | 24 | 256 | 98.111 | 67.376 | 1.46x |
| 2 | 20 | 1 | 7.776 | 4.736 | 1.64x |
| 2 | 20 | 16 | 11.168 | 7.824 | 1.43x |
| 2 | 20 | 64 | 26.656 | 18.048 | 1.48x |
| 2 | 20 | 256 | 83.424 | 57.056 | 1.46x |
| 2 | 10 | 1 | 7.424 | 4.416 | 1.68x |
| 2 | 10 | 16 | 8.736 | 6.240 | 1.40x |
| 2 | 10 | 64 | 17.408 | 12.032 | 1.45x |
| 2 | 10 | 256 | 44.512 | 30.112 | 1.48x |
| 3 | 80 | 1 | 10.928 | 5.568 | 1.96x |
| 3 | 80 | 16 | 34.720 | 20.640 | 1.68x |
| 3 | 80 | 64 | 108.799 | 65.440 | 1.66x |
| 3 | 80 | 256 | 410.144 | 245.376 | 1.67x |
| 3 | 24 | 1 | 10.496 | 5.344 | 1.96x |
| 3 | 24 | 16 | 14.432 | 9.376 | 1.54x |
| 3 | 24 | 64 | 37.152 | 23.568 | 1.58x |
| 3 | 24 | 256 | 128.576 | 77.472 | 1.66x |
| 3 | 20 | 1 | 10.528 | 5.344 | 1.97x |
| 3 | 20 | 16 | 14.304 | 9.184 | 1.56x |
| 3 | 20 | 64 | 34.560 | 20.672 | 1.67x |
| 3 | 20 | 256 | 108.864 | 65.504 | 1.66x |
| 3 | 10 | 1 | 10.464 | 5.344 | 1.96x |
| 3 | 10 | 16 | 11.456 | 7.008 | 1.63x |
| 3 | 10 | 64 | 22.656 | 13.440 | 1.69x |
| 3 | 10 | 256 | 58.015 | 35.264 | 1.65x |
| 5 | 80 | 1 | 15.200 | 6.688 | 2.27x |
| 5 | 80 | 16 | 48.096 | 28.352 | 1.70x |
| 5 | 80 | 64 | 151.136 | 92.944 | 1.63x |
| 5 | 80 | 256 | 573.472 | 353.007 | 1.62x |
| 5 | 24 | 1 | 14.432 | 6.400 | 2.25x |
| 5 | 24 | 16 | 19.936 | 12.417 | 1.61x |
| 5 | 24 | 64 | 52.128 | 32.736 | 1.59x |
| 5 | 24 | 256 | 180.704 | 110.784 | 1.63x |
| 5 | 20 | 1 | 14.448 | 6.368 | 2.27x |
| 5 | 20 | 16 | 19.680 | 12.224 | 1.61x |
| 5 | 20 | 64 | 48.000 | 28.352 | 1.69x |
| 5 | 20 | 256 | 150.880 | 92.992 | 1.62x |
| 5 | 10 | 1 | 14.272 | 6.176 | 2.31x |
| 5 | 10 | 16 | 15.424 | 9.072 | 1.70x |
| 5 | 10 | 64 | 31.328 | 17.920 | 1.75x |
| 5 | 10 | 256 | 80.512 | 49.120 | 1.64x |
| 6 | 80 | 1 | 16.593 | 7.200 | 2.30x |
| 6 | 80 | 16 | 53.504 | 31.936 | 1.68x |
| 6 | 80 | 64 | 168.447 | 104.960 | 1.60x |
| 6 | 80 | 256 | 638.799 | 398.064 | 1.60x |
| 6 | 24 | 1 | 16.544 | 6.976 | 2.37x |
| 6 | 24 | 16 | 22.240 | 13.984 | 1.59x |
| 6 | 24 | 64 | 58.176 | 37.376 | 1.56x |
| 6 | 24 | 256 | 201.632 | 124.768 | 1.62x |
| 6 | 20 | 1 | 16.320 | 6.944 | 2.35x |
| 6 | 20 | 16 | 21.920 | 13.696 | 1.60x |
| 6 | 20 | 64 | 53.120 | 31.936 | 1.66x |
| 6 | 20 | 256 | 167.872 | 105.248 | 1.59x |
| 6 | 10 | 1 | 15.712 | 6.720 | 2.34x |
| 6 | 10 | 16 | 17.056 | 10.304 | 1.66x |
| 6 | 10 | 64 | 34.656 | 20.288 | 1.71x |
| 6 | 10 | 256 | 89.856 | 55.712 | 1.61x |
| 7 | 80 | 1 | 19.392 | 7.712 | 2.51x |
| 7 | 80 | 16 | 61.152 | 36.383 | 1.68x |
| 7 | 80 | 64 | 193.376 | 120.944 | 1.60x |
| 7 | 80 | 256 | 738.943 | 460.672 | 1.60x |
| 7 | 24 | 1 | 19.040 | 7.424 | 2.56x |
| 7 | 24 | 16 | 25.312 | 15.488 | 1.63x |
| 7 | 24 | 64 | 66.880 | 42.784 | 1.56x |
| 7 | 24 | 256 | 232.513 | 143.840 | 1.62x |
| 7 | 20 | 1 | 18.816 | 7.456 | 2.52x |
| 7 | 20 | 16 | 25.056 | 15.200 | 1.65x |
| 7 | 20 | 64 | 61.312 | 36.448 | 1.68x |
| 7 | 20 | 256 | 192.992 | 120.993 | 1.60x |
| 7 | 10 | 1 | 18.528 | 7.296 | 2.54x |
| 7 | 10 | 16 | 19.520 | 11.136 | 1.75x |
| 7 | 10 | 64 | 40.032 | 22.912 | 1.75x |
| 7 | 10 | 256 | 103.295 | 63.809 | 1.62x |
| 16 | 80 | 1 | 37.920 | 12.096 | 3.13x |
| 16 | 80 | 16 | 121.664 | 69.408 | 1.75x |
| 16 | 80 | 64 | 381.087 | 241.760 | 1.58x |
| 16 | 80 | 256 | 1466.736 | 936.031 | 1.57x |
| 16 | 24 | 1 | 37.472 | 11.872 | 3.16x |
| 16 | 24 | 16 | 49.568 | 27.328 | 1.81x |
| 16 | 24 | 64 | 134.624 | 82.656 | 1.63x |
| 16 | 24 | 256 | 463.872 | 289.344 | 1.60x |
| 16 | 20 | 1 | 36.960 | 12.000 | 3.08x |
| 16 | 20 | 16 | 49.152 | 27.200 | 1.81x |
| 16 | 20 | 64 | 121.312 | 69.376 | 1.75x |
| 16 | 20 | 256 | 379.727 | 241.983 | 1.57x |
| 16 | 10 | 1 | 36.449 | 11.680 | 3.12x |
| 16 | 10 | 16 | 37.952 | 19.552 | 1.94x |
| 16 | 10 | 64 | 78.528 | 41.792 | 1.88x |
| 16 | 10 | 256 | 204.800 | 125.072 | 1.64x |

</details>


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

- **New Features**
- Expanded Cake GDP decode support with precompiled kernels for
additional token counts, including 3, 5, 6, and 7, across supported GPU
architectures.
- Added support for selecting static-token-count kernels across the
supported range of 2–16.
- Extended prefill kernel options for additional state and gating
configurations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery H <averyh@nvidia.com>

### [82866b5](https://github.com/flashinfer-ai/flashinfer/commit/82866b5b0075530c906e7ea06a4a7d429950c106)

- **作者**: Mr Knight
- **时间**: 2026-11-17T08:50:00Z
- **提交信息**: feat(moe_ep): SM120 MXFP4 x MXFP8 nosync MegaMoE kernel as a small-batch option of MoEEpLayer (#8806)

<!-- .github/pull_request_template.md -->

## 📌 Description

Adds a small-batch option to `flashinfer.moe_ep.MoEEpLayer` for SM120
(RTX PRO 6000 class): `nosync=NosyncOptions()`. The layer is built
exactly as configured (the cake or cutedsl SM120 MXFP4 MegaMoE backend,
unchanged), and next to it a new W4A8 (MXFP4 weights, MXFP8 activations)
MegaMoE kernel, `sm120_mxfp4_mxfp8_bf16_nosync`. Calls of at most
`max_tokens_per_rank` tokens per rank (default 128, i.e. decode) run the
new kernel; every larger call runs the configured backend, bit for bit
as without the option. The kernel does single-host expert parallelism
(1–8 ranks) over PCIe peer-to-peer, or over the NIC (NCCL GIN) for pairs
whose PCIe peer path is slow. `flashinfer.megamoe` is unchanged.

Design notes (kernel phases, transports, host-topology caveats, limits):
[`docs/design_docs/moe_ep_sm120_nosync.md`](https://github.com/YijiaZhao/flashinfer/blob/feat/megamoe-sm120-mxfp4/docs/design_docs/moe_ep_sm120_nosync.md)
in this PR. Full report with design, per-phase timing and vLLM serving
results:
[SM120_MEGAMOE_RESULTS.md](https://github.com/YijiaZhao/megamoe_basedondeepgemm/blob/main/docs/SM120_MEGAMOE_RESULTS.md).

**API:** the existing call, plus one argument:

```python
from flashinfer.moe_ep import MegaConfig, MoEEpLayer, MoEEpTensors, NosyncOptions, PrequantizedMoEWeights
from flashinfer.moe_ep import Sm120_Mxfp4_Mxfp8_Bf16_Cake_MegaMoeConfig

layer = MoEEpLayer(
    bootstrap=bootstrap,                     # EP group
    fleet_params=FleetParams(num_experts=E, max_tokens_per_rank=1024, token_hidden_size=H),
    weights=PrequantizedMoEWeights(w13=..., w2=..., w13_scale=..., w2_scale=...),  # E2M1 + UE8M0 per 32
    backend=MegaConfig(                      # whatever the deployment uses today, unchanged
        megakernel=Sm120_Mxfp4_Mxfp8_Bf16_Cake_MegaMoeConfig(intermediate_size=I, top_k=k),
        quantize_input=True, preprocess_weights=True,
    ),
    nosync=NosyncOptions(),                  # the new option: calls of <= 128 tokens per rank run the nosync kernel
)
y = layer(MoEEpTensors(hidden_states=x_bf16, topk_ids=ids_int64, topk_weights=w_fp32))
```

`layer.forward`, `stage_inputs` / `compute_staged` (CUDA graphs) and
`warmup` behave as on the configured layer; other attributes come from
it. Every rank must take the same kernel for a call, so the layer
decides on a rank-uniform bound: `compile_tokens_per_rank` of
`stage_inputs` when given, the call's own (padded) token count during
CUDA graph capture, and otherwise the largest token count of any rank
(one all-reduce). Where the kernel cannot run (not compute capability
12.0, weights that are not MXFP4, cake with its in-kernel shared expert,
an unsupported geometry) the option warns and every call runs the
configured backend.

**Weights:** the nosync kernel reads the FP4 weights in the layout the
cake and cutedsl backends already hold (row-major, gate/up rows
interleaved 8 + 8, low nibble first), so with either of them it uses
their packed tensors and only adds its UE8M0 scales (1/16 of the FP4
bytes). The option needs pre-quantized MXFP4 weights
(`PrequantizedMoEWeights`), which today only the cake and cutedsl
backends take on SM120; with a layer fed BF16 weights (e.g.
`SplitConfig` with the `fused_moe` kernel, which rejects pre-quantized
weights) it warns and stays off. The FP4 tensors are shared only when
the configured backend's `kernel_name` is cake or cutedsl; another MXFP4
backend would get a packed copy (its size is logged).

Inputs, weights and staging are the same as cake's: BF16 activations
quantized to MXFP8 (E4M3, UE8M0 per 32) by `stage_inputs` (or
pre-quantized with `quantize_input=False`), the same
`PrequantizedMoEWeights` layout, `topk_ids` int64 with -1 for a masked
route. Ranks may stage different token counts in the same call,
including none.

One persistent kernel per call:

- top-k routes are exchanged through the symmetric buffer;
- each staged MXFP8 token is pushed with 16-byte P2P stores straight
into the owning rank's expert pool;
- FC1 + SwiGLU + FC2 run on the block-scaled `mma.sync ...
kind::mxf8f6f4.block_scale` (E2M1 × E4M3) with swap-AB; each lane loads
16 contiguous bytes of a weight row per K128 and a 4×4 lane transpose
turns them into MMA fragments (K is permuted within each 32-element
scale block, identically for both operands), and the gate/up interleave
keeps SwiGLU in registers; with 8-token work items the P2P build
double-buffers the weight loop (the next step's weights and scales load
while this step's MMAs run);
- the BF16 expert outputs are pushed back to the source rank and
combined with the routing weights.

Synchronization is what the name `nosync` refers to: there is no
cross-rank barrier. Each producer writes an epoch-tagged flag into the
consumer's memory after its data (`st.release.sys`), and the consumer
polls its own memory (`ld.acquire.sys`); over GIN the consumer counts
signals per source instead. No remote atomics and no host-side sync.
Spins time out (30 s) into an error word instead of hanging
(`protocol_error(workspace)`).

**Options** (`NosyncOptions`): `max_tokens_per_rank` (1–128, default
128, the same on every rank), `transport`, `tokens_per_item`, and
`top_k` / `swiglu_limit`, which default to the configured backend's when
it is cake or cutedsl. The kernel is also a plain `moe_ep` MegaMoE
backend (`Sm120_Mxfp4_Mxfp8_Bf16_Nosync_MegaMoeConfig`) for deployments
that only run decode.

**Transport: the same as the configured cake layer.** By default
(`transport=None`) the nosync kernel reaches each pair of ranks the way
the configured cake backend does: it takes the per-pair table cake
resolved from its `transport_table` (`all_gin`, `lsa_where_reachable`,
`all_lsa`, `auto`, `tuned` or an explicit table) and uses P2P stores
where cake uses LSA and NCCL GIN puts where cake uses GIN. One setting,
cake's `transport_table`, decides the data path of both kernels. With
another configured backend the nosync kernel uses P2P.

- **LSA** (load/store access): the kernel reads and writes the peer
GPU's buffer directly, over NVLink or PCIe P2P. A pair is **LSA
reachable** when NCCL can map the peer's window into this GPU's address
space (`ncclGetPeerDevicePointer`); NCCL decides that from the topology
and its settings, e.g. the NICs `NCCL_IB_HCA` allows.
- **GIN** (GPU-initiated networking, NCCL Device API): the kernel posts
RDMA puts through a NIC into the peer's window, and the receiver counts
signals. Any pair the network connects can use it.
- cake's tables: `all_gin` (its default) puts every remote pair on GIN,
`lsa_where_reachable` puts the LSA-reachable pairs on LSA and the rest
on GIN, `all_lsa` puts every pair on LSA (rejected if a pair is not
reachable), `auto` / `tuned` choose a table by a setup probe / an
offline tuner.

An explicit `transport` overrides cake's table: `"p2p"` (every pair P2P,
torch symmetric memory), `"auto"` (P2P where NCCL maps the pair, GIN
elsewhere), `"nic"` (GIN for every other rank), or a per-pair table in
cake's encoding (0 self, 1 P2P, 2 GIN).

Over GIN a token is sent once per rank, with one slot table per call
(the rank's pool slots → the source's tokens), and the partials come
back one put per run of finished rows of an FC2 tile; the receiver
counts GIN signals per source instead of polling flags. The NIC path is
a separate JIT module per GIN backend (proxy / GDAKI / GPI) plus a
host-only session module (`ncclMemAlloc`, `ncclCommWindowRegister`,
`ncclDevCommCreate`); the P2P module has no NCCL dependency. Needs NCCL
2.30.7 with the Device API.

`tokens_per_item` (work-item width): a work item multiplies 8 tokens of
one expert per weight load, or 16 once the experts average at least 3
routed rows each (`tokens * top_k / local experts`): the best of 8 / 16
/ 24 / 32 in a cold-L2 sweep on RTX 6000D (three shapes below, EP4 /
EP8, 16–128 tokens per rank; 16 matches 8 below 3 rows and is up to 12%
faster above, 24 and 32 are 0–6% slower than 16). Against the previous
default (24 from 7 rows, else 8) on RTX 6000D, same routes: unchanged up
to 16 tokens per rank, 0–5% faster from 32, e.g. DSV4-Flash EP8 at 32
tokens 408.3 → 394.0 µs, GLM-5.3-Flash EP4 at 64 tokens 868.9 → 835.2
µs, DSV4.1-Flash EP4 at 128 tokens 1604.5 → 1550.8 µs; one point is 1%
slower (DSV4.1-Flash EP8 at 128 tokens, 917.1 → 927.1 µs). For the best
performance on another GPU or model, sweep `tokens_per_item=8|16|24|32`
per token count with `bench_megamoe_mxfp4_sm120.py --tokens-per-item`;
without it the 8 / 16 default applies.

Limits of the nosync kernel: compute capability 12.0, `hidden % 256 ==
0` and `hidden <= 7936`, `intermediate_size % 256 == 0`, top-k ≤ 8, ≤
256 local experts, ≤ 8 ranks, at most 128 tokens per rank (see *Token
range* below). Outside them the option is off and the configured backend
runs every call.

### Performance: with vs without this PR

FlashInfer's existing SM120 MXFP4 × MXFP8 MegaMoE backends in
`flashinfer.moe_ep` are the "without" baseline, all three run through
the same `MoEEpLayer` path:

- **cutedsl:** `Sm120_Mxfp4_Mxfp8_Bf16_Cutedsl_MegaMoeConfig` (#4632)
- **cake:** `Sm120_Mxfp4_Mxfp8_Bf16_Cake_MegaMoeConfig` (#6346)
- **DeepEP + CUTLASS:** the unfused path: DeepEP v2 dispatch over NCCL,
FlashInfer's CUTLASS grouped MoE (`cutlass_fused_moe`, MXFP8 × MXFP4) on
the local experts, DeepEP combine (setup under *Backend settings*)

Setup:

- **RTX 6000D host:** 8× NVIDIA RTX 6000D (sm_120, 156 SMs, 84 GB GDDR7
each; clocks not locked, max boost 2430 MHz), no NVLink: ranks talk over
PCIe P2P. Driver 580.95.05, CUDA 13, image
`toklin/vllm-sm120:e10ecb6bd-v41`.
- **RTX PRO 6000 host:** 8× RTX PRO 6000 Blackwell Server Edition (188
SMs, 96 GB), 2× Xeon Platinum 8480+, PCIe switches with one dual-port
ConnectX-7 per GPU pair, one of its two 400 GbE ports up (4 ports up in
all, every rank using its own pair's NIC; no `NCCL_IB_HCA`), plus a 25
GbE management NIC, driver 615.71.10, image `vllm/vllm-openai:v0.32.0`.
Stock cutedsl from `main` runs on it (188 SMs avoid the grid-size
ambiguity in Reviewer Notes).
- **RTX 6000D interconnect:** 2× AMD EPYC 9575F; Broadcom PEX890xx PCIe
Gen5 switches, each GPU pair sharing one switch (`PIX`) with two
ConnectX-8 400 Gb/s RoCE NICs, pairs within a socket at `NODE`, across
sockets at `SYS`. EP4 uses GPUs 0–3 (one socket); EP8 uses all eight
across the two sockets. Four of the eight ConnectX-8 ports are up (one
per card), each on its own subnet with no route between them, so every
run pins NCCL to one NIC (`NCCL_IB_HCA==mlx5_0`); with that one NIC NCCL
maps every GPU pair for load/store. This PR and cutedsl move data
GPU-to-GPU over PCIe P2P; cake can also go through the NICs (see backend
settings).
- **Shapes:** listed above the tables.
- **Routing:** random top-k. All three backends replay **identical
routes** (`--save-routing` / `--load-routing`). This PR's column is
`MoEEpLayer(backend=<cake config>, nosync=NosyncOptions())` (every point
is ≤ 128 tokens per rank, so the nosync kernel runs); cutedsl and cake
(code unchanged by this PR) were measured earlier on the same hosts,
routes and `MoEEpLayer` path.
- **Buffer:** `max_tokens_per_rank = 128`, default work-item width,
default transport: this PR uses the table of the cake column it is
compared with. RTX 6000D: every pair P2P (`all_lsa` at EP4,
`lsa_where_reachable` at EP8, both all-LSA with one NIC). RTX PRO 6000:
every pair P2P at EP4; at EP8 one column per cake table (see that
table).
- **Which commit and host:** every RTX 6000D number is the PR head
(`3ffd6c87`, rebased on `main`) on the host described above, all four
backends from that one tree in two rounds (order reversed in the second,
every run started with all GPUs idle) on identical seeded routes; each
cell is the median of the two rounds, DeepEP + CUTLASS the better of 4
and 8 SMs. The cake column of the RTX 6000D EP8 table was measured again
the same way (two rounds, same routes) with `lsa_where_reachable`, the
fastest cake table on this host (see *Backend settings*); this PR's
column there re-measured within 1.5% of the numbers shown (default
transport, `79719f6a`). The RTX PRO 6000 tables are the same tree
measured the same way on the RTX PRO 6000 host.
- **Timing:** each call is captured in a CUDA graph. Each round takes
the max over ranks, and the table reports the median over rounds. For
every backend the BF16 inputs are staged (and quantized) once by
`MoEEpLayer.stage_inputs` and the timed call is
`MoEEpLayer.compute_staged`.
- **L2:** cold, as in #6343: a 512 MB write flushes L2 before each call,
so the weights come from DRAM as in a decode step that walks every
layer.

**What is measured:** the standalone MoE kernel, one MoE layer (routed
experts only) per timed call. FC1 is the gate + up weight [2I, H] and
FC2 the down weight [H, I] of one expert. Not timed: the router and
top-k selection, input staging and quantisation, attention and shared
experts.

- **Input:** x [T, H] in BF16, quantized to MXFP8 (E4M3, one UE8M0 scale
per 32 channels) by `stage_inputs` outside the timed call (all three
backends), plus `topk_ids` [T, k] (int64) and `topk_weights` [T, k]
(FP32).
- **Weights:** MXFP4 (E2M1, one UE8M0 scale per 32 values along K). FC1
rows are the I gate rows then the I up rows.
- **Per (token, expert):** g, u = FC1 · x → h = SiLU(min(g, 10)) ·
clamp(u, −10, 10) (clamped SwiGLU, limit 10 in all three backends) → h
quantized to MXFP8 → o = FC2 · h. y[t] = Σ over the token's k routes of
topk_weight · o, in BF16.

Backends: this PR's backend (one persistent kernel), cutedsl (two
kernels, K1 and K2, running concurrently), cake (one persistent kernel)
and DeepEP + CUTLASS (dispatch kernel, grouped GEMM, combine kernel).
EP4 runs on GPUs 0–3 (one CPU socket), EP8 on all eight (two sockets).

Model shapes (x = input per rank, FC1 = gate + up weight [2I, H] and FC2
= down weight [H, I] of one expert, T = tokens per rank): DSV4-Flash: x
[T, 4096], FC1 [4096, 4096], FC2 [4096, 2048], 256 experts, top-6;
DSV4.1-Flash: x [T, 5120], FC1 [4608, 5120], FC2 [5120, 2304], 384
experts, top-6; GLM-5.3-Flash: x [T, 4096], FC1 [4096, 4096], FC2 [4096,
2048], 288 experts, top-8.

µs per MoE layer, lower is better; speedup = the fastest of the other
backends ÷ this PR.

**RTX 6000D, EP4** (8× RTX 6000D, driver 580.95.05; NICs: 4 of 8
ConnectX-8 400 GbE ports up; code `3ffd6c87`):

| model | tokens / rank | this PR | cutedsl | cake | DeepEP + CUTLASS |
speedup |
|---|---:|---:|---:|---:|---:|---:|
| DSV4-Flash | 1 | **125.7** | 204.4 | 295.8 | 286.9 | 1.63× |
| DSV4-Flash | 2 | **178.4** | 273.2 | 348.9 | 366.4 | 1.53× |
| DSV4-Flash | 8 | **448.3** | 562.1 | 668.5 | 742.1 | 1.25× |
| DSV4-Flash | 16 | **569.9** | 686.5 | 811.6 | 893.8 | 1.20× |
| DSV4-Flash | 32 | **696.8** | 799.9 | 938.1 | 1062.5 | 1.15× |
| DSV4-Flash | 64 | **723.7** | 845.6 | 955.2 | 1207.7 | 1.17× |
| DSV4-Flash | 128 | **776.0** | 981.9 | 965.4 | 1363.7 | 1.24× |
| DSV4.1-Flash | 1 | **155.4** | 233.1 | 331.3 | 325.4 | 1.50× |
| DSV4.1-Flash | 2 | **286.3** | 381.5 | 482.2 | 506.6 | 1.33× |
| DSV4.1-Flash | 8 | **621.7** | 730.7 | 855.3 | 928.2 | 1.18× |
| DSV4.1-Flash | 16 | **1002.4** | 1099.3 | 1258.7 | 1451.0 | 1.10× |
| DSV4.1-Flash | 32 | **1348.3** | 1443.8 | 1622.8 | 2098.3 | 1.07× |
| DSV4.1-Flash | 64 | **1517.2** | 1613.8 | 1773.5 | 2772.6 | 1.06× |
| DSV4.1-Flash | 128 | **1553.1** | 1929.3 | 1800.0 | 2715.5 | 1.16× |
| GLM-5.3-Flash | 1 | **154.3** | 234.9 | 341.1 | 353.0 | 1.52× |
| GLM-5.3-Flash | 2 | **225.4** | 318.8 | 426.6 | 442.6 | 1.41× |
| GLM-5.3-Flash | 8 | **557.2** | 663.0 | 811.8 | 876.2 | 1.19× |
| GLM-5.3-Flash | 16 | **664.2** | 773.8 | 935.0 | 1014.2 | 1.16× |
| GLM-5.3-Flash | 32 | **824.5** | 901.3 | 1073.8 | 1182.0 | 1.09× |
| GLM-5.3-Flash | 64 | **838.0** | 933.8 | 1086.9 | 1295.6 | 1.11× |
| GLM-5.3-Flash | 128 | **895.7** | 1088.9 | 1090.2 | 1493.5 | 1.22× |

**RTX 6000D, EP8** (8× RTX 6000D, driver 580.95.05; NICs: 4 of 8
ConnectX-8 400 GbE ports up; code `3ffd6c87`; the cake column is
`transport_table="lsa_where_reachable"`, measured with `79719f6a` (cake
code unchanged), see *Backend settings*):

| model | tokens / rank | this PR | cutedsl | cake `lsa_where_reachable`
| DeepEP + CUTLASS | speedup |
|---|---:|---:|---:|---:|---:|---:|
| DSV4-Flash | 1 | **142.8** | 242.4 | 315.1 | 429.9 | 1.70× |
| DSV4-Flash | 2 | **200.3** | 314.5 | 378.6 | 563.0 | 1.57× |
| DSV4-Flash | 8 | **309.8** | 464.4 | 511.4 | 709.0 | 1.50× |
| DSV4-Flash | 16 | **379.1** | 544.2 | 584.4 | 831.5 | 1.44× |
| DSV4-Flash | 32 | **397.9** | 549.8 | 602.5 | 970.7 | 1.38× |
| DSV4-Flash | 64 | **432.0** | 585.1 | 604.1 | 1272.7 | 1.35× |
| DSV4-Flash | 128 | **544.3** | 675.0 | 655.2 | 1771.4 | 1.20× |
| DSV4.1-Flash | 1 | **215.8** | 332.5 | 405.1 | 521.0 | 1.54× |
| DSV4.1-Flash | 2 | **339.6** | 476.0 | 557.7 | 676.6 | 1.40× |
| DSV4.1-Flash | 8 | **561.0** | 736.0 | 800.5 | 1014.5 | 1.31× |
| DSV4.1-Flash | 16 | **691.3** | 901.6 | 943.1 | 1238.0 | 1.30× |
| DSV4.1-Flash | 32 | **779.6** | 983.0 | 1013.8 | 1464.4 | 1.26× |
| DSV4.1-Flash | 64 | **813.8** | 1035.0 | 1027.3 | 1809.3 | 1.26× |
| DSV4.1-Flash | 128 | **929.1** | 1135.2 | 1088.3 | 2415.8 | 1.17× |
| GLM-5.3-Flash | 1 | **174.1** | 279.7 | 379.6 | 512.0 | 1.61× |
| GLM-5.3-Flash | 2 | **220.6** | 336.8 | 433.4 | 578.8 | 1.53× |
| GLM-5.3-Flash | 8 | **383.8** | 539.1 | 620.1 | 794.3 | 1.40× |
| GLM-5.3-Flash | 16 | **436.9** | 595.0 | 660.2 | 917.0 | 1.36× |
| GLM-5.3-Flash | 32 | **454.6** | 610.2 | 670.5 | 1072.1 | 1.34× |
| GLM-5.3-Flash | 64 | **508.4** | 681.3 | 695.9 | 1421.8 | 1.34× |
| GLM-5.3-Flash | 128 | **689.0** | 810.5 | 744.0 | 2021.7 | 1.08× |

**RTX PRO 6000, EP4** (8× RTX PRO 6000, driver 615.71.10; NICs: 4 of 8
ConnectX-7 400 GbE ports up; code `3ffd6c87`):

| model | tokens / rank | this PR | cutedsl | cake | DeepEP + CUTLASS |
speedup |
|---|---:|---:|---:|---:|---:|---:|
| DSV4-Flash | 1 | **124.9** | 203.1 | 301.4 | 280.1 | 1.63× |
| DSV4-Flash | 2 | **153.6** | 243.7 | 330.8 | 350.2 | 1.59× |
| DSV4-Flash | 8 | **389.1** | 485.9 | 606.2 | 645.0 | 1.25× |
| DSV4-Flash | 16 | **528.4** | 633.1 | 768.0 | 823.3 | 1.20× |
| DSV4-Flash | 32 | **599.7** | 693.0 | 839.7 | 908.1 | 1.16× |
| DSV4-Flash | 64 | **643.4** | 745.2 | 874.0 | 1001.3 | 1.16× |
| DSV4-Flash | 128 | **700.4** | 812.0 | 878.6 | 1091.6 | 1.16× |
| DSV4.1-Flash | 1 | **154.6** | 235.5 | 343.8 | 320.5 | 1.52× |
| DSV4.1-Flash | 2 | **233.5** | 321.6 | 428.0 | 432.1 | 1.38× |
| DSV4.1-Flash | 8 | **559.1** | 661.7 | 785.4 | 837.6 | 1.18× |
| DSV4.1-Flash | 16 | **856.4** | 957.0 | 1114.1 | 1209.3 | 1.12× |
| DSV4.1-Flash | 32 | **1156.4** | 1257.0 | 1431.6 | 1482.6 | 1.09× |
| DSV4.1-Flash | 64 | **1347.6** | 1433.7 | 1587.8 | 1733.3 | 1.06× |
| DSV4.1-Flash | 128 | **1384.4** | 1626.7 | 1607.2 | 1838.9 | 1.16× |
| GLM-5.3-Flash | 1 | **152.4** | 235.1 | 347.8 | 297.3 | 1.54× |
| GLM-5.3-Flash | 2 | **232.3** | 307.7 | 438.6 | 431.4 | 1.32× |
| GLM-5.3-Flash | 8 | **470.9** | 562.2 | 716.8 | 714.8 | 1.19× |
| GLM-5.3-Flash | 16 | **657.4** | 761.3 | 917.5 | 932.3 | 1.16× |
| GLM-5.3-Flash | 32 | **727.0** | 810.2 | 974.8 | 1018.8 | 1.11× |
| GLM-5.3-Flash | 64 | **744.5** | 827.2 | 985.1 | 1103.8 | 1.11× |
| GLM-5.3-Flash | 128 | **822.6** | 907.6 | 991.2 | 1212.5 | 1.10× |

**RTX PRO 6000, EP8 across two CPU sockets, same data path** (8× RTX PRO
6000, driver 615.71.10, clocks not locked; NICs: one dual-port
ConnectX-7 per GPU pair, one 400 GbE port up on each, 4 ports in all;
code `b28ac4c5`). This PR runs with the default transport, so each "this
PR" column takes the table of the cake column next to it and both
kernels send each pair the same way: with `all_gin` every remote pair
over GIN, with `lsa_where_reachable` P2P within a socket and GIN across
(NCCL does not map the cross-socket pairs here). Speedup = cake ÷ this
PR on the same table. Medians of two rounds; cutedsl and DeepEP +
CUTLASS are the earlier measurement on this host (`3ffd6c87`, same
routes):

| model | tokens / rank | this PR (`all_gin`) | cake `all_gin` | speedup
| this PR (`lsa_where_reachable`) | cake `lsa_where_reachable` | speedup
| cutedsl (P2P only) | DeepEP + CUTLASS |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| DSV4-Flash | 1 | **208.2** | 299.9 | 1.44× | **172.6** | 298.6 | 1.73×
| 186.7 | 303.1 |
| DSV4-Flash | 2 | **274.4** | 368.6 | 1.34× | **237.6** | 364.0 | 1.53×
| 270.9 | 405.5 |
| DSV4-Flash | 8 | **409.5** | 519.9 | 1.27× | **371.0** | 518.0 | 1.40×
| 929.1 | 567.3 |
| DSV4-Flash | 16 | **437.2** | 554.0 | 1.27× | **405.5** | 549.9 |
1.36× | 2248.5 | 612.4 |
| DSV4-Flash | 32 | **460.8** | 577.9 | 1.25× | **435.7** | 578.5 |
1.33× | 4590.4 | 673.8 |
| DSV4-Flash | 64 | **530.9** | 593.1 | 1.12× | **495.6** | 581.1 |
1.17× | 8944.6 | 799.0 |
| DSV4-Flash | 128 | 704.5 | **661.5** | 0.94× | 703.5 | **640.0** |
0.91× | 9039.4 | 961.5 |
| DSV4.1-Flash | 1 | **246.3** | 367.8 | 1.49× | **214.3** | 366.6 |
1.71× | 260.1 | 368.6 |
| DSV4.1-Flash | 2 | **300.9** | 404.8 | 1.35× | **263.7** | 400.9 |
1.52× | 335.9 | 453.0 |
| DSV4.1-Flash | 8 | **596.0** | 747.5 | 1.25× | **565.2** | 745.5 |
1.32× | 871.2 | 819.2 |
| DSV4.1-Flash | 16 | **721.9** | 884.7 | 1.23× | **692.2** | 880.6 |
1.27× | 2625.2 | 971.1 |
| DSV4.1-Flash | 32 | **778.5** | 946.2 | 1.22× | **753.7** | 935.9 |
1.24× | 6902.9 | 1088.1 |
| DSV4.1-Flash | 64 | **831.5** | 963.6 | 1.16× | **800.0** | 952.3 |
1.19× | 11927.0 | 1214.8 |
| DSV4.1-Flash | 128 | **1008.7** | 1049.7 | 1.04× | **1002.0** | 1033.2
| 1.03× | 11376.3 | 1395.5 |
| GLM-5.3-Flash | 1 | **232.4** | 360.4 | 1.55× | **196.6** | 358.4 |
1.82× | 219.7 | 317.1 |
| GLM-5.3-Flash | 2 | **294.9** | 434.2 | 1.47× | **270.3** | 431.5 |
1.60× | 315.1 | 468.8 |
| GLM-5.3-Flash | 8 | **432.5** | 589.8 | 1.36× | **403.8** | 586.8 |
1.45× | 1029.8 | 623.6 |
| GLM-5.3-Flash | 16 | **473.1** | 633.1 | 1.34× | **445.9** | 626.7 |
1.41× | 3288.1 | 675.8 |
| GLM-5.3-Flash | 32 | **515.6** | 651.3 | 1.26× | **477.2** | 658.0 |
1.38× | 5710.6 | 759.8 |
| GLM-5.3-Flash | 64 | **591.7** | 684.0 | 1.16× | **587.1** | 675.8 |
1.15× | 11860.3 | 866.6 |
| GLM-5.3-Flash | 128 | 882.7 | **753.5** | 0.85× | **884.0** | 1199.9 |
1.36× | 12237.1 | 1089.5 |

### Token range: why at most 128 tokens per rank

The kernel is built for decode-size batches. In an earlier
DeepSeek-V4-Flash sweep on RTX 6000D with the three backends on
identical routes, it was faster up to 128 tokens per rank, 0–10% slower
than the faster existing backend at 256 (cold L2), and clearly slower at
512 (e.g. EP4 at 512 tokens per rank with cold L2: 1691 µs vs cake 1054
µs). So the option caps `max_tokens_per_rank` at 128, and every larger
call (prefill, large decode batches) runs the configured backend. A
deployment can lower the bound per shape (e.g. 64 for DSV4-Flash and
GLM-5.3-Flash at EP8 on RTX PRO 6000, the two points below 1×). cutedsl
ran with `{"k2_warps": 12, "k2_tail_reclaim": false}` up to 64 tokens
per rank and `{"k2_tail_reclaim": false}` above, because the dual-group
K2 mapping requires a (64, 16, 128) tile there.

**Same data path for every backend.** On the RTX 6000D host this PR,
cake and cutedsl all move data GPU-to-GPU over PCIe P2P (this PR and
cake through the same per-pair table, cutedsl has no other path; DeepEP
+ CUTLASS goes through one NIC, see *Backend settings*), and this PR is
the fastest at every point: 1.06–1.63× at EP4 and 1.08–1.70× at EP8 over
the fastest other backend. On the RTX PRO 6000 host at EP8 this PR and
cake are compared on the same table, both `all_gin` and
`lsa_where_reachable`: this PR is faster at every point up to 64 tokens
per rank, and at 128 it is slower for DSV4-Flash on both tables (0.94×,
0.91×) and for GLM-5.3-Flash on `all_gin` (0.85×). cutedsl has no NIC
path, so there it stays on the slow cross-socket P2P.

### RTX PRO 6000, EP8 across sockets

**EP8 across sockets on the RTX PRO 6000 host.** On this host (2× Xeon
Platinum 8480+) GPU-to-GPU PCIe traffic between the two sockets runs at
about 5 GB/s, and NCCL does not map those pairs for load/store, so
`lsa_where_reachable` sends ranks 0–3 ↔ 4–7 over the NICs and keeps P2P
within a socket, while `all_gin` sends every remote pair over the NICs.
With P2P only, this PR and cutedsl took 4–12 ms per layer from 16 tokens
per rank. At 128 tokens per rank the rows and partials over the NIC
dominate: each GPU pair shares one 400 GbE port on this host. The RTX
6000D host's cross-socket P2P is fast, and there every pair stays P2P
(tables above).

Backend settings:

- **cutedsl:** NVSHMEM 3.7.0 (`NVSHMEM_HEAP_KIND=VIDMEM`,
`NVSHMEM_REMOTE_TRANSPORT=none`) with knobs `{"k2_warps": 12,
"k2_tail_reclaim": false}`. The default dual-N8 tail reclaim hangs at
small buckets on this GPU. It also needed a local fix to run at all; see
Reviewer Notes.
- **cake:** NCCL 2.30.7. On RTX PRO 6000 EP8 both `all_gin` and
`lsa_where_reachable` were measured (all NICs; `all_lsa` is rejected
there: NCCL does not map the cross-socket pairs). On RTX 6000D every run
pins one NIC, `NCCL_IB_HCA==mlx5_0`. This is a property of that host's
network, not of a transport table: its four NIC ports sit on different
subnets and RoCE between them times out, so with every NIC allowed,
registering any NCCL window fails (`ncclCommWindowRegister: unhandled
system error`, measured for cake `all_gin` and `lsa_where_reachable`
alike). With `mlx5_0` pinned every cake table runs, and NCCL maps every
pair for load/store, so `lsa_where_reachable` is all-LSA there
(`all_lsa` gives the same times within 0.3%). EP4 uses `all_lsa`, EP8
`lsa_where_reachable`: the fastest cake table on this host. `all_gin`
sends every rank through the one NIC and is slower from 16 tokens per
rank on, e.g. EP8 DSV4-Flash at 128 tokens per rank 1275.7 µs vs 655.2
µs.
- **DeepEP + CUTLASS:** DeepEP 2.0.0 (`ElasticBuffer`, built on the NCCL
2.30.7 Device API) as shipped in both images, `do_cpu_sync=False`
(CUDA-graph capturable, no cached layout), FP8 dispatch of the MXFP8
tokens with their UE8M0 scales packed 4 per int32, padding rows of the
max-size receive buffer masked, then `cutlass_fused_moe` (MXFP8 × MXFP4,
clamped SwiGLU with limit 10, routing weight in the finalize) on the
local experts and DeepEP combine. Quantizing the inputs to MXFP8 is
outside the timed call, as for the other backends. On these PCIe hosts
DeepEP's scale-up (NVLink-domain) barrier needs peer atomics across PCIe
switches and times out, so it runs with `NCCL_P2P_DISABLE=1
NCCL_SHM_DISABLE=1`: every rank is its own scale-up domain and all
traffic goes over the NICs through NCCL GIN. Best of 4 and 8 DeepEP SMs
per point (fewer SMs were faster; 16 and 32 were slower still). On RTX
6000D all ranks share one NIC (`NCCL_IB_HCA==mlx5_0`, as for cake),
which penalizes DeepEP there, most at EP8; on RTX PRO 6000 each rank
uses its own NICs. Its output matches the same `cutlass_fused_moe` on
all tokens without DeepEP to 1.7e-3 relative L2.

Reproduce:

```bash
B="python benchmarks/bench_megamoe_mxfp4_sm120.py --ep 4 --shape flash --capacity 128 --tokens 1 2 8 16 32 64 128"
C="--cold-l2 --repeats 1 --rounds 20"
$B --backend nosync   --save-routing /tmp/rt $C      # cake + NosyncOptions() (follows cake's --transport); --ep 8, --shape flash41 / glm53flash
$B --backend cutedsl --load-routing /tmp/rt $C --knobs '{"k2_warps":12,"k2_tail_reclaim":false}'   # 128 tokens: '{"k2_tail_reclaim":false}'
$B --backend cake    --load-routing /tmp/rt $C      # EP8: --transport lsa_where_reachable (RTX 6000D: NCCL_IB_HCA==mlx5_0)
```

### Numerics

The kernel quantizes the clamped SwiGLU output to MXFP8 per 32 channels
and applies the routing weight after FC2 (in the combine).

- **Against a reference with the same recipe:** relative L2 between 0
and 1.5e-4.
- **Against cake on identical weights and inputs:** 4–5% relative L2 (up
to ~7% at one token). cake applies the routing weight before quantizing
the SwiGLU output (it matches that recipe to 0.8%); the difference is
that rounding. Against a reference that keeps the intermediate
unquantized, both backends are within 2.5–3.6% (cake slightly closer);
against a fully unquantized reference, 5.5–6%.
- **Calls above the bound** run the configured backend and are
bit-identical to it.

## 🔍 Related Issues

A third SM120 MXFP4 × MXFP8 MegaMoE backend next to #4632 (cutedsl) and
#6346 (cake), which are the baselines above; the kernel design follows
#6343 (`flashinfer.megamoe`, SM90).

Full report:
[SM120_MEGAMOE_RESULTS.md](https://github.com/YijiaZhao/megamoe_basedondeepgemm/blob/main/docs/SM120_MEGAMOE_RESULTS.md).
It covers:

- the kernel design;
- the per-phase breakdown from in-kernel timestamps (routing exchange,
dispatch, FC1, FC2, combine);
- end-to-end vLLM serving of DeepSeek-V4-Flash on RTX 6000D (AgentX
trace, PD with DP4/EP4 decode);
- correctness and reproduction steps.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues. (Run on the files in this PR; all hooks
pass.)

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).

Suggested CI test targets:
`tests/moe_ep/test_moe_ep_sm120_w4a8_nosync_mega.py`

`tests/moe_ep/test_moe_ep_sm120_w4a8_nosync_mega.py` builds
`MoEEpLayer(backend=<cake or cutedsl config>,
nosync=NosyncOptions(...))` next to the same layer without the option,
on the same weights, and covers:

- the switch: calls above the bound bit-identical to the configured
layer, calls at or below it on the nosync kernel, with even and uneven
token counts across ranks (one rank staging none), at the default bound
and at 16;
- cutedsl as the configured backend (opt-in with
`FLASHINFER_TEST_SM120_CUTEDSL=1`: it needs NVSHMEM);
- EP 2/4/8 with random, hot-expert, empty and invalid (out-of-range /
repeated id) routing;
- the DSV4-Flash, DSV4.1-Flash and GLM-5.3-Flash shapes at EP4 and EP8;
- every forced work-item width (`tokens_per_item` 8 / 16 / 24 / 32);
- pre-quantized inputs (`quantize_input=False`) giving the same bits as
BF16 inputs;
- agreement with cake on identical weights and inputs;
- `transport="nic"` at EP 2/4/8 with every routing, `transport="auto"`
at EP8 with uneven rows, and the default (`None`) following cake's
`all_gin` and `lsa_where_reachable` tables at EP8 (opt-in with
`FLASHINFER_TEST_MEGAMOE_SM120_NIC=1`: they need a GIN-capable network);
- deterministic workspace reuse, CUDA graph replay (staging and the
kernel choice included), and `protocol_error() == 0`.

How correctness is checked: all data is random. Expert weights are
random E2M1 codes (all 16 values, both signs) with random UE8M0 scales
per 32; activations are `torch.randn` BF16; routes are random top-k with
signed random weights and every third token's last slot masked, plus the
hot / empty / invalid cases above. The reference is computed in FP32 in
PyTorch with the same recipe (MXFP8 inputs, dequantized MXFP4 weights,
SwiGLU clamped at 10, MXFP8 intermediate, routing weight after FC2),
all-reduced over ranks. Pass criteria: relative L2 below 5e-3 against it
(measured 0 to 1.5e-4), all-masked tokens exactly zero, calls above the
bound bit-identical to the configured layer, the nosync kernel reading
the configured backend's FP4 tensors (same pointer), and repeated calls,
pre-quantized inputs and CUDA graph replay bit-identical to the first
call. `warmup()` followed by capturing a small call with no eager call
before it (the order vLLM uses) was also checked: replay matches the
reference exactly.

Result on the current commit (`1207505f`), with
`FLASHINFER_TEST_MEGAMOE_SM120_NIC=1`: 32 passed, 2 skipped (the cutedsl
tests) on 8× RTX 6000D (`NCCL_IB_HCA==mlx5_0`) and on 8× RTX PRO 6000
(cutedsl not enabled there for this run);
`tests/moe_ep/test_ep_selection*.py` (the `MoEEpLayer` factory, which
the rebase merged with `AutoConfig`): 54 passed, 26 skipped on both.
Before the rebase: 34 passed on 8× RTX PRO 6000 with every opt-in
enabled. The tests skip when fewer than 2 SM120 GPUs are present.

## Reviewer Notes

- **Transport default:** `NosyncOptions.transport=None` reads the table
of the configured cake layer's default workspace at `warmup()` or the
first eager call (collectively; the default workspace can still be
configured with `create_workspace` after construction), so one setting
(cake's `transport_table`) decides how both kernels reach each pair; a
P2P cell that NCCL does not map for load/store raises.

- **NIC transport:** `auto` derives the GIN pairs from NCCL's load/store
reachability (`ncclGetPeerDevicePointer`), and the buffer checks the
per-pair choice is symmetric across ranks. The GIN path is built per
backend (`NCCL_GIN_*_ENABLE`) with the device code in nvcc's device pass
only, since NCCL's device headers do not compile in the host pass. GIN
uses 4 contexts (CTAs spread their puts over them; 4 beat 1 by 1.4× at
128 tokens and 16 added signal-poll cost at small batches).

- **cutedsl does not run on RTX 6000D on `main`** (it does on the 188-SM
RTX PRO 6000). `NativeGreenContextGraph.capture` fails with `Failed to
identify both CuTeDSL K1/K2 graph nodes: rebound=(3, 0)`. On this 156-SM
part the 104/52 K1/K2 split launches K2 at 2 CTAs/SM, which is also 104
CTAs, so the grid-size match assigns both nodes to K1. For the baseline
above I disambiguated by capture order (K1 is launched first). That
change is not part of this PR; happy to send it separately.
- **cake hangs on extremely skewed routing:** with every token routed to
the same six experts (all on rank 0), cake alone (no option) hangs at 96
and 128 tokens per rank (EP4, capacity 128); random routing at 128 is
fine. The hot-expert test therefore compares with cake only up to 64
tokens per rank (the nosync kernel is checked against the reference at
every size). Not touched by this PR.
- The workspace holds `max_tokens_per_rank` rows per (local expert,
source rank). At the DSV4-Flash shape with capacity 128 and EP4 the
whole buffer is about 200 MB per rank. It is pooled across layers with
the same geometry, like the other backends' workspaces.
- The kernel source stays in `include/flashinfer/megamoe/` and
`csrc/megamoe/` (JIT generators in `flashinfer/jit/megamoe.py`) next to
the SM90 MegaMoE it is modeled on; the kernel's Python side lives in
`flashinfer/moe_ep/backends/mega/kernel/sm120/mxfp4_mxfp8_bf16_nosync/`,
and the option in `flashinfer/moe_ep/modes/nosync_layer.py`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [5a99423](https://github.com/flashinfer-ai/flashinfer/commit/5a99423646ed9877ec4d9001621d8d2de18f6ae8)

- **作者**: NVJiangShao
- **时间**: 2026-11-17T07:14:18Z
- **提交信息**: perf(moe): optimize SM90 mixed-input CUTLASS MoE backend for TP-dominant workloads (#9493)

<!-- .github/pull_request_template.md -->

## 📌 Description

Avoid redundant C tensor-map maintenance and move prebuilt-D descriptor
acquisition to the producer in the SM90 mixed-input MoE kernels. The
source-disabled epilogue preserves the existing D buffering/stage
geometry; producer/consumer barriers retain the descriptor visibility
handoff.

The optimizations are enabled for supported H100 SXM and H20 paths;
other configurations retain their existing implementation.

### Synthetic TPEP benchmarks

The main figures use **balanced per-expert M as a controlled
benchmark**, not production routing traces. Counts are spread as evenly
as integers permit. Coverage is **108 workloads per GPU**: three paths ×
four TP/EP pairs (`1/8`, `2/4`, `4/2`, `8/1`) × nine batch sizes (`8`
through `2048`), or 36 workloads per GPU/path. Skewed M is kept as a
separate, collapsed sensitivity check below and is **not pooled into the
main averages**.

These are archived development measurements from **2026-11-11, against
baseline `2d134f98d`**. The full matrix has not been rerun on the
current PR revision; final-code acceptance results are shown separately
below. The workload is synthetic and the timing excludes communication,
so these are not production inference speedups.

- Columns are TP/EP pairs; H100 and ordinary H20 are adjacent rows.
Orange squares show FC1, blue circles FC2, and black diamonds their
combined time; each stage includes its adjacent builder + GEMM.
- The y-axis is `100 × (baseline latency / candidate latency − 1)`:
higher is better; negative values are regressions. This is speedup gain,
not latency reduction. Matching balanced/skewed figures use the same
y-scale.
- NCU `gpu__time_duration.sum`, application replay, cache-control
`none`, clock-control `none`; 20 warmups, 10 calls with the first two
discarded, two reversed-order rounds. Combined time is summed within
each call before taking the median. Routing, quantization, finalization,
host time and communication are excluded.
- Each version independently uses native autotune, so the comparison
includes tactic reselection. Each GPU is compared with its own baseline,
not with the other GPU's absolute speed.
- **H20 Humming is unchanged** and shown as a baseline reference, not a
new candidate or A/A measurement.

#### INT4 × FP8

![Balanced M: INT4 × FP8, synthetic TPEP benchmark on H100 and
H20](https://raw.githubusercontent.com/StudyingShao/flashinfer/cd21d6e516528c6030c11e3b3327cabf391b0367/flashinfer-pr9493-int4-fp8-tpep-h100-h20-20261115.png)

#### MXFP4 × BF16

![Balanced M: MXFP4 × BF16, synthetic TPEP benchmark on H100 and
H20](https://raw.githubusercontent.com/StudyingShao/flashinfer/cd21d6e516528c6030c11e3b3327cabf391b0367/flashinfer-pr9493-mxfp4-bf16-tpep-h100-h20-20261115.png)

#### MXFP4 × FP8 (Humming)

![Balanced M: MXFP4 × FP8 (Humming), synthetic TPEP benchmark on H100
and
H20](https://raw.githubusercontent.com/StudyingShao/flashinfer/cd21d6e516528c6030c11e3b3327cabf391b0367/flashinfer-pr9493-mxfp4-fp8-humming-premma-tpep-h100-h20-20261115.png)

#### Balanced-M summary

All values below summarize only the main figures: 36 balanced-M
workloads per GPU/path, and nine batches per TP/EP cell. Geometric means
weight each workload equally. Regressions are retained.

| GPU | Path | FC1 GM | FC2 GM | FC1+FC2 GM | Per-case total range |
Total <1× |
| --- | --- | ---: | ---: | ---: | ---: | ---: |
| H100 | INT4 × FP8 | 1.0143× | 1.1036× | 1.0531× | 1.0091–1.1233× |
0/36 |
| H100 | MXFP4 × BF16 | 1.0397× | 1.1063× | 1.0684× | 1.0245–1.1351× |
0/36 |
| H100 | MXFP4 × FP8 (Humming) | 1.0111× | 1.0235× | 1.0148× |
0.9784–1.0800× | 6/36 |
| H20 | INT4 × FP8 | 1.0000× | 1.0313× | 1.0145× | 0.9491–1.0474× | 5/36
|
| H20 | MXFP4 × BF16 | 1.0015× | 1.0429× | 1.0183× | 0.9936–1.1894× |
1/36 |
| H20 | MXFP4 × FP8 (Humming) | 1.0000× ref. | 1.0000× ref. | 1.0000×
ref. | reference | — |

| GPU | Path | TP1/EP8 | TP2/EP4 | TP4/EP2 | TP8/EP1 |
| --- | --- | ---: | ---: | ---: | ---: |
| H100 | INT4 × FP8 | 1.0267× | 1.0240× | 1.0535× | 1.1105× |
| H100 | MXFP4 × BF16 | 1.0368× | 1.0470× | 1.0806× | 1.1107× |
| H100 | MXFP4 × FP8 (Humming) | 1.0217× | 1.0258× | 1.0086× | 1.0031× |
| H20 | INT4 × FP8 | 0.9987× | 1.0039× | 1.0188× | 1.0368× |
| H20 | MXFP4 × BF16 | 1.0044× | 1.0064× | 1.0368× | 1.0260× |
| H20 | MXFP4 × FP8 (Humming) | 1.0000× ref. | 1.0000× ref. | 1.0000×
ref. | 1.0000× ref. |

[Statistics separated by M
distribution](https://raw.githubusercontent.com/StudyingShao/flashinfer/cd21d6e516528c6030c11e3b3327cabf391b0367/flashinfer-pr9493-summary-by-m-distribution-20261115.json)
· [All measured points and absolute times, including the sensitivity
cases](https://raw.githubusercontent.com/StudyingShao/flashinfer/cd21d6e516528c6030c11e3b3327cabf391b0367/flashinfer-pr9493-selected-policy-tpep-h100-h20-20261115.csv)
· [Exact routing
fixtures](https://raw.githubusercontent.com/StudyingShao/flashinfer/cd21d6e516528c6030c11e3b3327cabf391b0367/flashinfer-pr9493-tpep-routing-fixtures-20261115.json)

<details>
<summary>Skewed-M sensitivity check — synthetic workloads</summary>

This additional 108-workload-per-GPU grid uses deterministic nonuniform
per-expert M at the same routed-row budget. It is also synthetic, not a
sampled production distribution. It checks how the measured gains and
regressions change with expert-load imbalance; it does not establish
real-serving performance. These results remain separate from the main
summary.

![Skewed M sensitivity: INT4 × FP8, synthetic TPEP workload on H100 and
H20](https://raw.githubusercontent.com/StudyingShao/flashinfer/cd21d6e516528c6030c11e3b3327cabf391b0367/flashinfer-pr9493-int4-fp8-tpep-h100-h20-skewed-m-20261115.png)

![Skewed M sensitivity: MXFP4 × BF16, synthetic TPEP workload on H100
and
H20](https://raw.githubusercontent.com/StudyingShao/flashinfer/cd21d6e516528c6030c11e3b3327cabf391b0367/flashinfer-pr9493-mxfp4-bf16-tpep-h100-h20-skewed-m-20261115.png)

![Skewed M sensitivity: MXFP4 × FP8 (Humming), synthetic TPEP workload
on H100 and
H20](https://raw.githubusercontent.com/StudyingShao/flashinfer/cd21d6e516528c6030c11e3b3327cabf391b0367/flashinfer-pr9493-mxfp4-fp8-humming-premma-tpep-h100-h20-skewed-m-20261115.png)

Skewed-M-only summary (36 workloads per GPU/path):

| GPU | Path | FC1 GM | FC2 GM | FC1+FC2 GM | Per-case total range |
Total <1× |
| --- | --- | ---: | ---: | ---: | ---: | ---: |
| H100 | INT4 × FP8 | 1.0165× | 1.1062× | 1.0557× | 1.0095–1.1412× |
0/36 |
| H100 | MXFP4 × BF16 | 1.0354× | 1.1072× | 1.0658× | 1.0216–1.1265× |
0/36 |
| H100 | MXFP4 × FP8 (Humming) | 1.0227× | 1.0302× | 1.0251× |
0.9888–1.1632× | 8/36 |
| H20 | INT4 × FP8 | 1.0001× | 1.0377× | 1.0160× | 0.9955–1.0402× | 3/36
|
| H20 | MXFP4 × BF16 | 1.0007× | 1.0327× | 1.0136× | 0.9990–1.0418× |
2/36 |
| H20 | MXFP4 × FP8 (Humming) | 1.0000× ref. | 1.0000× ref. | 1.0000×
ref. | reference | — |

</details>

### Separate final-code acceptance sample


Example synthetic balanced TP8/EP1 local shard: batch 32, 384 local
experts, top-k 6, hidden 7168, intermediate 384. Expert row counts are
one for experts 0–191 and zero for the remaining experts. FC1 has
N=768/K=7168; FC2 has N=7168/K=384. TP/EP describe local shard sizes;
this benchmark includes no distributed communication.

| GPU | Path | Baseline (µs) | Candidate (µs) | Speedup |
| --- | --- | ---: | ---: | ---: |
| H100 SXM 80GB HBM3 | MXFP4 × BF16 | 452.640 | 403.296 | 1.122× |
| H20 (ordinary H20) | MXFP4 × BF16 | 683.408 | 657.728 | 1.039× |

Times are NCU `gpu__time_duration.sum`: sum the adjacent
descriptor-builder + GEMM kernels for FC1 and FC2 within each call, then
take the median. These are kernel times, excluding
routing/quantization/finalization kernels, compilation, host overhead
and communication. Each arm selected its own tactics with native
autotune; no fixed tactics or schedule filtering. Protocol: 20 warmups,
10 measured calls with the first two discarded, two reversed-order
rounds, application replay, `clock-control=none`, `cache-control=none`.

The cleaned implementation separately passed 12 fixtures per GPU (four
per path). The two absolute-time rows above belong to that final-code
acceptance run, not the full historical sweep plotted above; they are
not mixed into its curves or statistics.

**Measurement provenance:** GPU measurements used baseline
`2d134f98d88351c499e09259d32cf3b9b82a34b4` and the final optimization
candidate. This PR is rebased onto
`9c50996794564e1e3b2a4b0683e9aa2bcc528df8`; its CUDA kernel
implementations are unchanged from the measured candidate; the follow-up
host-compiler eligibility fix affects JIT selection only. Upstream
autotuning has changed in the meantime, so these are historical
measurements, not a rerun of the full matrix on the new base.

<details>
<summary>Minimal BF16 workload reproducer and NCU commands</summary>

Save the following as `sm90_moe_repro.py` and run it in separately
installed baseline/candidate checkouts, with separate build workspaces
and autotune cache files. Its BF16 shapes, tensor seed recipe and
routing are extracted from the measured harness; native autotune should
be run afresh for each revision. The snippet is extracted from the
measured input recipe and is provided for reproduction; it was
syntax-checked during PR preparation, not newly run on a GPU.

```python
"""Minimal public-API reproduction of the balanced TP8/EP1 BF16 workload."""

import argparse
import hashlib
import subprocess

import torch
from flashinfer import autotune
from flashinfer import fused_moe as moe
from flashinfer.jit.fused_moe import gen_cutlass_fused_moe_sm90_module

parser = argparse.ArgumentParser()
parser.add_argument("--cache", required=True)
parser.add_argument("--tune", action="store_true")
args = parser.parse_args()
device = torch.device("cuda")
batch, hidden, inter, experts, topk = 32, 7168, 384, 384, 6

# Compile/tune first in the same checkout and workspace. Measurement refuses
# a missing or stale module instead of starting a compiler under NCU.
spec = gen_cutlass_fused_moe_sm90_module()
print("Selected module:", spec.name)
if not args.tune:
    assert spec.jit_library_path.is_file(), "Run --tune first"
    dry_run = subprocess.check_output(
        ["ninja", "-n", "-C", str(spec.jit_library_path.parent)], text=True
    )
    assert "no work to do" in dry_run, dry_run


def generator(*parts):
    digest = hashlib.sha256(repr((20261107,) + parts).encode()).digest()
    seed = int.from_bytes(digest[:8], "little") & ((1 << 63) - 1)
    return torch.Generator(device=device).manual_seed(seed)


g = generator("mxfp4_bf16", "weights", experts, hidden, inter)


def raw(shape, low=0, high=256):
    return torch.randint(low, high, shape, generator=g, device=device, dtype=torch.uint8)


w1 = raw((experts, 2 * inter, hidden // 2))
w2 = raw((experts, hidden, inter // 2))
s1 = raw((experts, 2 * inter, hidden // 32), 118, 123)
s2 = raw((experts, hidden, inter // 32), 118, 123)
w1 = moe.interleave_moe_weights_for_sm90_mixed_gemm(w1, "fp4")
w2 = moe.interleave_moe_weights_for_sm90_mixed_gemm(w2, "fp4")
scales = [
    moe.interleave_moe_scales_for_sm90_mixed_gemm(s).view(torch.int32)
    for s in (s1, s2)
]
g = generator("mxfp4_bf16", "activations", batch, hidden, topk)
x = torch.randn(batch, hidden, generator=g, device=device, dtype=torch.bfloat16)
routes = torch.arange(batch * topk, device=device, dtype=torch.int32).reshape(batch, topk)
weights = torch.rand(batch, topk, generator=g, device=device, dtype=torch.float32) + 0.5
weights /= weights.sum(dim=1, keepdim=True)
output = torch.empty_like(x)
workspace = torch.empty(
    moe.cutlass_fused_moe_workspace_size(
        batch, hidden, inter, experts, topk,
        x_dtype=x.dtype, weight_dtype=w1.dtype, output_dtype=output.dtype,
        use_w4_group_scaling=True, use_fused_finalize=True, device=device,
        use_packed_weights=False, use_wfp4afp8_humming=False,
    ),
    dtype=torch.uint8,
    device=device,
)


def run():
    moe.cutlass_fused_moe(
        x, routes, weights, w1, w2, torch.bfloat16,
        quant_scales=scales, use_w4_group_scaling=True,
        use_packed_weights=False, use_wfp4afp8_humming=False,
        output=output, workspace_buffer=workspace,
    )


with autotune(args.tune, cache=args.cache, tuning_buckets=(batch,)):
    if args.tune:
        run()
    else:
        for _ in range(20):
            run()
        torch.cuda.synchronize()
        with torch.cuda.nvtx.range("NATIVE_MEASURE"):
            for _ in range(10):
                run()
        torch.cuda.synchronize()
```

```bash
# In each checkout, before profiling (compilation/autotuning happens here):
export FLASHINFER_CUDA_ARCH_LIST=9.0a
export FLASHINFER_WORKSPACE_BASE=/path/to/this-revision-workspace
python sm90_moe_repro.py --cache /path/to/this-revision-tactics.json --tune

# Collect all kernels in the measured range, preserving builder/GEMM adjacency.
ncu --clock-control none --cache-control none --replay-mode application \
  --app-replay-mode strict --target-processes all --kernel-name-base demangled \
  --nvtx --nvtx-include 'NATIVE_MEASURE/' \
  --metrics gpu__time_duration.sum --page raw --csv --print-units base \
  --log-file timings.csv \
  python sm90_moe_repro.py --cache /path/to/this-revision-tactics.json
```

Check the printed module name: on H100, baseline should use
`fused_moe_90` and the candidate `fused_moe_90_h100_prebuilt_d`; on H20
both use `fused_moe_90_h20_prebuilt_d`.

Select each call's two descriptor-builders and two grouped-GEMMs from
the capture, sum them per call, discard the first two calls, and compare
baseline/candidate medians in reversed-order rounds. Do not sum every
kernel in the range or use Python wall-clock time as the kernel latency.

</details>

## 🔍 Related Issues

None.

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

All applicable changed-file hooks passed with `pre-commit run --files
<the nine changed paths>`: clang-format, Ruff, mypy and the standard
file checks. Hooks were invoked explicitly; an all-repository run was
not performed.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: targeted SM90 mixed-input MoE and CPU dispatch/AOT coverage is
proposed.

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/moe/test_trtllm_cutlass_fused_moe.py
tests/cpu/jit/test_cutlass_fused_moe_sm90_prebuilt_d.py
tests/cpu/jit/test_cutlass_fused_moe_aot.py
tests/cpu/jit/test_fused_moe_host_compile_flags.py`

Current rebased tree:

- 69 CPU dispatch/AOT/host-compiler tests passed with real PyTorch,
Python 3.12 and no GPU; JIT compilation/loading was explicitly
prohibited.
- 35 additional upstream AOT/gencode compatibility tests passed
(including one initially skipped for missing PyYAML, then run
successfully after installing that dependency).
- Changed-file pre-commit checks passed. The AOT `gen_all_modules` logic
is unchanged by the upstream refactor; the GPU test import was updated
by upstream to the relocated, byte-identical quantization helper.

Prior final-kernel validation, retained as historical evidence:

- H100/H20/generic modules each compiled, loaded in a fresh process and
passed the relevant numerical smoke test.
- H100 and ordinary H20 each passed the two K-boundary cases plus
Humming smoke; generic passed its independent strict numerical check.
- Both GPUs passed 12 independently autotuned fixtures with
original-implementation same-tactic reference checks and two NCU rounds.
- CUDA Graph replay passed with changing expert counts and independent
numerical references.

No new GPU compilation/performance matrix was run after rebasing; the
full CI checkbox is left unchecked. The optional extra generic
subprocess test is omitted to avoid another full cold-cache CI module
build; generic dispatch/AOT selection remains covered on CPU.

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

Please focus on descriptor visibility/barrier handoff, retention of the
D epilogue storage layout when source maintenance is disabled, and
device-independent generic AOT registration.

The H100-specific module may require a first-use JIT build when only
generic AOT artifacts are installed. There are no experiment switches or
per-tactic routing tables in the patch. The measurements above are
archived GPU results with the stated scope.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* Improved grouped MoE execution on supported H100 and H20
configurations, with optimized paths selected based on device and
workload.
* H20 post-MMA workloads with smaller K dimensions can use an optimized
path; other workloads retain the compatible fallback.
* **Compatibility**
* AOT builds continue to include the generic module, with
device-specific variants selected at JIT time.
* Unsupported devices and configurations continue to use the generic
execution path.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [f003191](https://github.com/flashinfer-ai/flashinfer/commit/f0031919bdc5692d2fd1b18bae129db19d817c9e)

- **作者**: Adrian Stanescu
- **时间**: 2026-11-17T06:47:31Z
- **提交信息**: fix(gdn): isolate non-finite next-sequence rows in SM12x tail chunk (#9373)

<!-- .github/pull_request_template.md -->

## 📌 Description

In a packed (`cu_seqlens`) call, the SM12x GDN prefill kernel loads the
last chunk of a sequence as a full 64-row TMA tile from the packed q/k/v
tensors. When the sequence length B is not a multiple of 64, rows B..63
of that tile are the next sequence's first tokens. For the last
sequence, they are the rows after `cu_seqlens[-1]`, when the tensors
have more rows than the packed tokens. The kernel masks those rows by
selection in KK, QK, alpha and beta. Two products mask them by a
multiply by zero, so `0 * NaN = NaN` (and `0 * Inf = NaN`) reaches the
output and the state:

- `NewV = (V - SK) @ T^T`: `T` is zero in the columns from B on, but a
non-finite value in V or in `SK = S @ K^T` still gives NaN. `NewV` then
carries it into `O2` and into the state.
- `KV += NewV @ K`: `kv_decay_v` multiplies the `NewV` columns from B on
by zero, but a non-finite value in a K row from B on still gives NaN in
every state entry.

So a NaN or Inf in the k or v of the next sequence's first token makes
the first sequence's last output rows and its whole final state
non-finite. A NaN in q, g or beta does not (the Q tail only reaches rows
that are masked or not stored, and g and beta load as 1 and 0 past the
end). One request with non-finite activations can corrupt an unrelated
request in the same batch. A non-finite k or v row after
`cu_seqlens[-1]` corrupts the last sequence in the same way.

This PR has three commits. The first commit selected zeros in registers,
in the math warps. The review found that it slows multi-sequence
prefill. The second commit replaces the selects: it clips the K and V
loads with tail tensor maps, as the review suggested. The third commit
changes the test as the review asked. The net change against `main`:

- For the last block of every sequence whose length is not a multiple of
64 (the last sequence too), the load warp copies the base K and V tensor
maps into two per-SM slots of a new workspace
(`gdn_prefill_load_tensormaps`, 2 x 128 bytes per SM). It sets global
dimension 1 (the token) to the sequence end, releases and acquires the
two tensor maps, and loads the K and V tiles of that block through them.
This is the method of the O store's tail tensor map
(`CollectiveStoreTma`).
- TMA writes zeros into the rows after the sequence end and still
delivers the full tile, so the expected transaction count does not
change. With the K and V rows from B on zero, `SK` and `V - SK` are zero
there, and the K operand of the state update is zero there. This cuts
both paths.
- The load loop keeps main's structure. The tensor maps are written in
the iteration of the tail block. With two or more blocks, this happens
while the math warps work on the earlier blocks. With one block, it
comes before the only load. Blocks of sequences whose length is a
multiple of 64 do no tensor-map work. `%smid` is read once per work
item.
- Q keeps the base tensor map. Its rows from B on reach only masked QK
entries and O rows past the sequence end.
- `compute_loop_body` and `run_math_role` are main's source again. The
math warps run main's code.
- The two slots per SM rely on one CTA per SM, as the O tail slot does.

Rows before B are not touched. Finite inputs give bit-identical results
to `main`.

The new test `test_sm12x_next_sequence_nan_stays_out_of_partial_tail`
packs `[100, 128]` and `[36, 128]` tokens, with and without state
checkpoints (every 64 tokens). It writes a NaN or an Inf into the second
sequence's first row of q, k, v, g or beta (40 cases). It compares the
first sequence's output and final state bit for bit with the unpoisoned
run, in all cases. With checkpoints, it also compares the checkpoints
bit for bit, and the checkpoint buffer starts filled with NaN, so a
checkpoint that the kernel does not write fails the test. (The first
version checked the checkpointed calls for finiteness only. That check
could not fail: a partial final block stores no checkpoint.)

## 🔍 Related Issues

Part of #9372. This PR fixes the reported SM120 non-CP case. The
left-padding (`prefix_lens`), SM90 and context-parallel variants listed
there remain open, so #9372 stays open after this PR. The SM120
context-parallel kernel, which `use_cp="auto"` picks for small batches,
still has the same leak (by reading; not probed).

Related to #8443 (the same class of bug in MLA and KDA), #8599 (the KDA
fix, merged) and #9286 (another KDA fix, open).

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

I ran `uvx pre-commit run --all-files` on a clean checkout of the first
commit. All hooks passed, and the working tree stayed clean. For the
update, I ran `uvx pre-commit run --files` on its two changed files
(`flashinfer/gdn_kernels/delta_rule_dsl/delta_rule_sm120.py` and
`tests/gdn/test_prefill_delta_rule.py`). Every hook passed or was
skipped because no file matched (ruff check, ruff format and mypy
passed), and the working tree stayed clean. I did not run `--all-files`
on the update. I did not install the git hooks.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.). RTX PRO 6000 Blackwell
Server Edition (SM120), CUDA 13.0, torch 2.14.1+cu130: the new test
passes (40 passed), and the whole `tests/gdn/test_prefill_delta_rule.py`
with the new test passes (2818 passed, 0 failed, 882 skipped). With the
update's kernel, these files also pass, each with the same per-test
outcomes as on `main`: `tests/gdn/test_paged_state.py` (111 passed, 0
failed, 9 skipped), `tests/gdn/test_prefill_state_indices.py` (114
passed, 0 failed, 84 skipped), `tests/gdn/test_prefill_cp_delta_rule.py`
(250 passed, 0 failed, 1 skipped),
`tests/gdn/test_delta_rule_dsl_disk_cache.py` (10 passed) and
`tests/gdn/test_prefill_qk_normalization.py` (170 passed).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/gdn/test_prefill_delta_rule.py
tests/gdn/test_paged_state.py tests/gdn/test_prefill_state_indices.py`

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

Setup: RTX PRO 6000 Blackwell Server Edition (SM120, 188 SMs), driver
595.91.07, torch 2.14.1+cu130 (CUDA 13.0), nvidia-cutlass-dsl 4.8.1,
cupti-python 13.5.0. The timing below is from the branch rebased onto
`main` at 9c5099679, so it uses the read flush that #9374 introduced for
cold-L2 timing. The kernel binaries of `main` and of this PR are
byte-identical on 9c5099679 and on the original base 36186cb4d; no
commit between the two changes `flashinfer/gdn_kernels/`.

### Correction to the first version

The first version of this text said that the selects "run in the last
chunk of each sequence and in nothing else". That was wrong. The kernel
uses the final-block variant of the loop body for the first block too,
so the selects ran in the first and in the last chunk of every sequence.
It also said "Performance: not measured". The slowdown that the review
measured reproduces. The first version against `main` (8 rounds,
medians): fp16 with an initial state, +7.78% at 8x1024, +4.77% at
8x2048, +1.31% at `[1000, 300, 2048, 70, 700]` and +4.57% at 256x33;
bf16 without an initial state, +11.70%, +7.92%, +3.55% and +1.15%.

With the write flush that the timer used before #9374, the same binaries
in the same run give +10.34%, +6.12%, +4.64% and +4.88% (fp16) and
+15.21%, +9.22%, +4.94% and +0.23% (bf16). `main` itself reads 1.0% to
5.3% longer with the write flush. So two builds must be timed with the
same flush.

### Correctness of the update

- Reproducer (`[100, 128]`, a NaN in the second sequence's first token):
finite output and final state, exit 0.
- Leak probe, 408 cases (NaN, +Inf or -Inf in one k or v row; fp16 and
bf16; with and without an initial state and checkpoints; six packs): on
`main`, 288 cases leak. With this PR, 0.
- Rows after the last sequence, 240 cases (non-finite k or v rows after
`cu_seqlens[-1]`): `main` leaks in all of them. With this PR, 0, and 0
elements differ in bits from the unpoisoned run.
- Finite inputs are bit-identical to `main`: 0 differing elements in 136
tensors (output, final state and checkpoints; fp16 and bf16; seven
packs), and in 112 more with `prefix_lens` and state indices.
- New test: 40 passed. On `main`, its 16 k and v cases fail and the 24
others pass. The whole `tests/gdn/test_prefill_delta_rule.py` with it:
2818 passed, 0 failed, 882 skipped.
- `test_paged_state.py`, `test_prefill_state_indices.py`,
`test_prefill_cp_delta_rule.py`, `test_delta_rule_dsl_disk_cache.py` and
`test_prefill_qk_normalization.py`: the same per-test outcomes as on
`main`.
- compute-sanitizer memcheck: 0 errors on the reproducer and on one
unaligned call. I do not know whether memcheck checks TMA loads, so this
is not proof that the tail tensor maps stay in bounds.

The first three items, the 136 tensors and the test file ran on the
rebased branch. The 112 tensors, the other test files and
compute-sanitizer ran on the original base, with the same kernel
binaries.

### Performance

Method: `flashinfer.testing.bench_gpu_time(enable_cupti=True,
cold_l2_cache=True)`, 100 timed calls per shape and round, one process
per build and round in random order, all kernels compiled before timing.
`main` is measured twice per round ("main vs main"). Each Δ is the
median over rounds of (this PR / main - 1), with a bootstrap 95% CI over
rounds. Call: `use_cp=False`, head size 128, 16 q/k and 48 v heads.
Clocks were not locked; pairing by round absorbs clock changes inside a
run.

This PR against `main`, 12 rounds:

| Shape | dtype, h0 | main (µs) | this PR (µs) | Δ median | 95% CI |
main vs main 95% CI |
| --- | --- | --- | --- | --- | --- | --- |
| 8x1024 | fp16, yes | 312.6 | 308.5 | -1.26% | [-1.91%, -0.91%] |
[-0.04%, +0.03%] |
| 8x2048 | fp16, yes | 564.0 | 560.2 | -0.72% | [-1.05%, -0.50%] |
[-0.00%, +0.09%] |
| [1000, 300, 2048, 70, 700] | fp16, yes | 183.6 | 181.5 | -1.11% |
[-1.34%, -0.97%] | [-0.02%, +0.31%] |
| 256x33 | fp16, yes | 1286.7 | 1283.9 | -0.19% | [-0.27%, -0.14%] |
[-0.01%, +0.02%] |
| 8x1024 | bf16, no | 278.8 | 279.5 | +0.51% | [-0.17%, +0.92%] |
[-0.01%, +0.23%] |
| 8x2048 | bf16, no | 529.8 | 530.6 | +0.20% | [-0.06%, +0.48%] |
[-0.10%, +0.11%] |
| [1000, 300, 2048, 70, 700] | bf16, no | 170.2 | 170.6 | +0.16% |
[+0.04%, +0.34%] | [-0.14%, +0.27%] |
| 256x33 | bf16, no | 737.7 | 742.2 | +0.61% | [+0.49%, +0.72%] |
[-0.01%, +0.02%] |

- The eight 1024x8 rows with the head configs of `bench_gdn_prefill.py`
(fp16, an initial state): -1.51% to -0.44%.
- My acceptance set has 20 rows: these eight, the nine rows with the
head configs of `bench_gdn_prefill.py` (1024x8 and 8192x8), 8x8192,
1x65536 and 3x128. The upper end of the CI is at or below +0.5% on 16 of
them and at or below +1.0% on 19. The one above +1.0% is 1x65536, whose
main-vs-main interval is wide too ([-0.01%, +3.32%]).
- The fp16 rows are faster than `main` because ptxas schedules the fp16
math code differently (see "Compiler output"). I do not claim that as an
effect of this change.
- Aligned shapes in bf16: a 20-round run shows no difference (8x1024
-0.13% [-0.58%, +0.09%], 8x2048 -0.04% [-0.14%, +0.05%]).
- Unaligned tails cost time in bf16 when every sequence of the batch is
unaligned (20 rounds): 8x1000 +1.46% [+1.10%, +1.77%], 8x2000 +0.52%
[+0.34%, +0.80%], 8x520 +0.64% [+0.48%, +0.73%]. In fp16, 8x1000 shows
no cost (+0.17% [-0.04%, +0.23%]). A control build that writes the tail
tensor maps and loads through them, but does not cut the extent, costs
the same (+1.55% at 8x1000 bf16). So the cost is the tensor-map setup,
not the clipping.
- One-block sequences without an initial state cost +0.36% to +0.76%
(256x33 and 256x63).
- The review's script, unmodified (`bench_gdn_prefill.py --use-cupti`,
two runs per build): the first version is +0.96% to +8.49% on its eight
1024x8 rows; this PR is never above `main` by more than one printed step
(1 µs).
- I tried two variants and kept neither: one shared setup of the O, K
and V tail tensor maps in the load warp (larger and slower), and the
tail tensor maps written once before the block loop (faster at some
unaligned shapes, slower in fp16 without an initial state).

### Compiler output

SASS of the timed cubins, `main` against this PR:

- bf16 without an initial state: the middle loop is main's (2213
instructions in the same order), up to a renaming of 7 uniform
registers.
- fp16: the math PTX is main's up to register names and one parameter
index, but ptxas schedules it differently. With an initial state, the
middle loop has 2190 instructions against main's 2203. Without one, it
has 2190 against 2189, with one more local store and load per trip; that
shows no cost (8x1024 fp16 without an initial state: -1.14% [-1.41%,
-0.90%], 20 rounds). So I cannot claim identical math SASS in fp16.
- Size against `main`: +896 bytes (fp16 with an initial state), +1,536
bytes (bf16 without one) and +1,024 bytes (fp16 without one). The first
version added 16,640 and 21,632 bytes in the first two. Registers and
stack frame are main's.
- Load and store warps: no local memory; the highest register is R21 of
the 24 they may use. A block of an aligned sequence runs 16 more
load-warp instructions than on `main` and none of the tensor-map work. A
tail block runs 59 more, with a GPU-scope fence and two tensor-map
acquires.

### Limits and follow-ups

- `prefix_lens` (left padding) has the same problem in the other
direction, and this PR does not fix it. With `cu_seqlens = [0, 100,
200]` and `prefix_lens = [0, 30]`, a NaN in k or v at the first
sequence's last row makes the second sequence's output, final state and
checkpoints non-finite, on `main` and with this PR alike.
- The SM120 context-parallel kernels are unchanged (their 45 cubins are
byte-identical to main's), and I did not probe them. By reading, they
and the SM90 kernels load an unbounded tail tile in the same way, so
they probably leak the same way. SM90 needs a load-time clip as here: a
register select does not fit its WGMMA state update.
- The test skips itself on GPUs that are not SM12x.

Claude Code used.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Fixed an issue where NaN or infinite values at the start of one
sequence could affect results for the preceding sequence when processing
a partial final block. The preceding sequence’s outputs and final state
now match results from processing without those invalid values. When
checkpointing is enabled, its checkpoints also match.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [0b39fb7](https://github.com/flashinfer-ai/flashinfer/commit/0b39fb763987a6d94b793734c240a4a4e98394df)

- **作者**: Akaash Parthasarathy
- **时间**: 2026-11-17T06:10:25Z
- **提交信息**: test(moe_ep): expect retuning after workspace capacity changes (#9540)

<!-- .github/pull_request_template.md -->

## 📌 Description

The multirank test still expects cached knobs to be reused when
workspace capacity grows. Update it to expect a fresh search and check
that the old cache entries remain available for replay.

## 🔍 Related Issues

#8477

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
`tests/moe_ep/test_sm107_variant_selection_multirank.py`

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

AI-assisted implementation.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Tests**
* Expanded multi-rank coverage to verify tuning behavior when capacity
increases, including retuning and preservation of existing protocol
records.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [f50ab18](https://github.com/flashinfer-ai/flashinfer/commit/f50ab181f2804b470a94e6d5ef083d1ab9d16341)

- **作者**: eigen
- **时间**: 2026-11-17T03:37:22Z
- **提交信息**: perf(cake_sage_block_sparse_attention): double-buffered S and tail split for many-block rows on SM100/SM103 (#9536)

The Sage FP8 block-sparse attention kernels use FP8 E4M3 Q/K/V with
per-token Q scales, per-16-token K scales and per-channel V scales, and
select KV blocks block-sparsely. This PR changes how rows with many
selected KV blocks are routed. Rows at or above a threshold of selected
KV blocks per row now run a double-buffered score (S) attention build.
On a partial last wave, they run a 2-CTA cluster tail split. The
double-buffered build starts at 24 selected blocks per row on both
architectures. The tail split starts at 24 on sm_100a and at 32 on
sm_103a.

Compared with the previous Cake version of this kernel (current
FlashInfer main), combined-API latency under CUDA graph improves by
1.023x to 1.120x on B200 and 1.020x to 1.108x on GB300 for the measured
rows with 32 or more selected blocks. The sel 6 rows are below both
thresholds, so they take the unchanged route.

Latencies are medians over 16 paired rounds of CUDA graph replay.
Speedup is main latency divided by this PR's latency, so a value above 1
means this PR is faster. `sel` is the number of KV blocks selected per
row. Head dim is 128, and B, H, Hkv and S are batch, query heads, KV
heads and sequence length.

**NVIDIA B200 (sm_100a, 148 SMs), CUDA 13.3 (torch
2.13.0a0+9186a08b2c.nv26.07)**

| shape | sel | main, combined API, graph (µs) | this PR (µs) | speedup
| main, quantize + attention, graph (µs) | this PR (µs) | speedup |
|---|---:|---:|---:|---:|---:|---:|---:|
| B8/H32/Hkv32/S4096 | 6 | 483.96 | 484.14 | 1.000 | 483.89 | 484.44 |
0.999 |
| B8/H32/Hkv32/S4096 | 32 | 1204.68 | 1177.18 | 1.023 | 1208.85 |
1184.55 | 1.021 |
| B8/H32/Hkv32/S4096 | 58 | 1978.91 | 1868.03 | 1.059 | 1954.31 |
1872.95 | 1.043 |
| B1/H8/Hkv8/S4096 | 6 | 23.77 | 23.68 | 1.004 | 23.78 | 23.70 | 1.003 |
| B1/H8/Hkv8/S4096 | 32 | 51.14 | 48.32 | 1.058 | 51.22 | 48.30 | 1.060
|
| B1/H8/Hkv8/S4096 | 58 | 77.74 | 69.38 | 1.120 | 77.76 | 69.35 | 1.121
|
| B1/H40/Hkv40/S32768 | 51 | 2320.97 | 2201.87 | 1.054 | 2290.51 |
2188.21 | 1.047 |
| B1/H40/Hkv40/S32768 | 128 | 5184.32 | 4938.97 | 1.050 | 5243.49 |
4957.08 | 1.058 |
| B1/H40/Hkv40/S32768 | 256 | 9948.53 | 9366.54 | 1.062 | 9885.50 |
9365.74 | 1.055 |
| B2/H24/Hkv24/S16384 | 32 | 912.39 | 886.53 | 1.029 | 914.95 | 882.21 |
1.037 |
| B1/H2/Hkv2/S4096 | 6 | 12.40 | 12.38 | 1.002 | 12.38 | 12.38 | 1.000 |
| B1/H2/Hkv2/S4096 | 58 | 26.45 | 25.13 | 1.053 | 26.50 | 25.14 | 1.054
|
| B1/H4/Hkv4/S4096 | 6 | 15.74 | 15.63 | 1.007 | 15.82 | 15.75 | 1.004 |
| B1/H4/Hkv4/S4096 | 58 | 43.54 | 41.14 | 1.058 | 43.49 | 41.06 | 1.059
|
| B1/H32/Hkv8/S4096 | 6 | 55.38 | 55.46 | 0.999 | 55.38 | 55.46 | 0.999
|

**NVIDIA GB300 (sm_103a, 152 SMs), CUDA 13.3 (torch
2.13.0a0+9186a08b2c.nv26.07)**

| shape | sel | main, combined API, graph (µs) | this PR (µs) | speedup
| main, quantize + attention, graph (µs) | this PR (µs) | speedup |
|---|---:|---:|---:|---:|---:|---:|---:|
| B8/H32/Hkv32/S4096 | 6 | 450.84 | 450.74 | 1.000 | 450.91 | 450.78 |
1.000 |
| B8/H32/Hkv32/S4096 | 32 | 976.13 | 954.47 | 1.023 | 976.13 | 954.22 |
1.023 |
| B8/H32/Hkv32/S4096 | 58 | 1511.90 | 1436.46 | 1.053 | 1511.85 |
1436.46 | 1.052 |
| B1/H8/Hkv8/S4096 | 6 | 22.22 | 22.24 | 0.999 | 22.24 | 22.29 | 0.998 |
| B1/H8/Hkv8/S4096 | 32 | 41.98 | 40.20 | 1.044 | 41.86 | 40.21 | 1.041
|
| B1/H8/Hkv8/S4096 | 58 | 61.68 | 55.68 | 1.108 | 61.73 | 55.68 | 1.109
|
| B1/H40/Hkv40/S32768 | 51 | 1767.17 | 1677.47 | 1.053 | 1766.55 |
1677.25 | 1.053 |
| B1/H40/Hkv40/S32768 | 128 | 3685.70 | 3505.49 | 1.051 | 3662.33 |
3470.51 | 1.055 |
| B1/H40/Hkv40/S32768 | 256 | 6981.09 | 6611.78 | 1.056 | 6982.86 |
6625.99 | 1.054 |
| B2/H24/Hkv24/S16384 | 32 | 736.77 | 722.29 | 1.020 | 736.89 | 722.82 |
1.019 |
| B1/H2/Hkv2/S4096 | 6 | 11.58 | 11.60 | 0.998 | 11.58 | 11.55 | 1.003 |
| B1/H2/Hkv2/S4096 | 58 | 21.59 | 20.81 | 1.037 | 21.61 | 20.82 | 1.038
|
| B1/H4/Hkv4/S4096 | 6 | 14.82 | 14.88 | 0.996 | 14.85 | 14.82 | 1.002 |
| B1/H4/Hkv4/S4096 | 58 | 34.91 | 33.42 | 1.045 | 35.00 | 33.51 | 1.044
|
| B1/H32/Hkv8/S4096 | 6 | 50.29 | 50.23 | 1.001 | 50.35 | 50.30 | 1.001
|

Rows below the thresholds keep their existing route. The same FP8
attention also runs on pre-quantized E4M3 inputs
(`bsa_attn_sm100_sage_fwd_cake`) or behind the fused BF16 quantizer
(`sage_fp8_quantize_sm100`, `bsa_attn_sm100_sage_quantize_fwd_cake`) on
sm_100a and sm_103a, and the family's INT8-QK / FP8-PV variant
(`bsa_attn_sm120_blk64_sage_fwd_cake`) ships for SM120.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added architecture-specific routing for block-sparse attention,
including a tail-split option for qualifying workloads.
* Added support for additional attention builds on SM100 and SM103 GPUs.
* **Improvements**
* Routing decisions are cached outside CUDA Graph capture; capture does
not populate the cache.
* Split execution may sum softmax values in a different order, with
results checked against the unsplit path within defined tolerances.
* **Tests**
* Added coverage for routing choices, split results, PDL settings, and
CUDA Graph replay.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [2666509](https://github.com/flashinfer-ai/flashinfer/commit/26665099a6437e8f861832d41de1e9699a4f1bf3)

- **作者**: Brian K. Ryu
- **时间**: 2026-11-17T02:14:28Z
- **提交信息**: feat(batch_invariant): the training-forward surface of the sampling classes -- `log_softmax(out_dtype=)`, `sampling_from_logits(temperature=, return_logprob=)` (#9535)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

The RL trainers re-score a rollout's tokens with a forward pass whose
log-softmax must give the inference engine's bits. The batch-invariant
class `lse.row` (#8999) and the draw over it (#9365) give them that
dataflow; this PR adds the four pieces the trainers' integration needs,
with no new kernel and no change to the existing outputs:

1. **`flashinfer.sampling.log_softmax(logits, temperature,
out_dtype=)`** -- the log-softmax row in the input's 16-bit dtype,
converted once from the class's fp32 row (`cvt.rn`), bit for bit
`log_softmax(logits, temperature).to(logits.dtype)` without the fp32
round trip: the shape of `aten::_log_softmax` on 16-bit inputs that
verl's and Megatron-Core's batch-invariant modes override
(`half_to_float=False`). A different member of the class with its own
receipt (`fingerprint("log_softmax", N=, dtype=, temperature=,
out_dtype=)`); `out_dtype=None` / `torch.float32` is the fp32 row as
before, any other dtype raises `BatchInvariantUnsupportedError`.
2. **`flashinfer.sampling.sampling_from_logits(...,
batch_invariant=True, temperature=, return_logprob=)`** -- the
temperaturethe class takes (`None`, a positive scalar or one per row,
inside the chain as `softmax` / `log_probs` apply it; the receipt gains
the optional `temperature` dimension), and the drawn token's natural
log-probability under the full distribution at that temperature returned
from the same launch as `(samples, logp)`: bit for bit
`log_probs(logits, samples, temperature)` (the value a trainer
re-scoring the token computes), never renormalised over a filtered
support. Both keywords are refused with `ValueError` on the default path
(the operator's kernel takes neither).
3. **The definition contract** in `flashinfer/batch_invariant/README.md`
("The training forward"): what the entries compute, what two callers
must pass to agree bit for bit, the adapter the frameworks own, the
vocabulary-parallel form, where it plugs in, and that nothing is stored.
4. **Caller-owned output buffers** on every entry under the flag --
`softmax(..., out=)`, `log_softmax(..., out=)`, `log_probs(..., out=,
lse_out=)`, `sampling_from_probs(..., out=)`, `sampling_from_logits(...,
out=, logprob_out=)` -- written in place and returned as given, so a
step allocates nothing: CUDA graphs captured on the caller's buffers
replay into them, and a framework's persistent token / log-probability /
chunk buffers take the kernels' stores directly. A buffer must have the
output dtype and shape, be contiguous and (the row outputs) 16-byte
aligned; one that does not fit is refused with `ValueError`, never
copied. Without the buffers the entries allocate as the operator's own
kernels do. The validity mask is formed only when `return_valid` asks
for it (it was a cast kernel on every call).

The Lean model gains the converted element (`Sampling.specLogpCvt`,
`logp_cvt_equiv` / `logp_cvt_bits_equal`: every placement's converted
output equals the spec's) and the generated conformance cases print it
(`lseout ... logp0c`).

## 🔍 Related Issues

<!-- Link any related issues here -->

* Tracker: #9009
* Previous PRs:
  * #8999
  * #9365

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

* **New Features**
* Batch-invariant sampling APIs accept caller-provided output buffers
for probabilities, log-probabilities, samples, and related outputs.
* Log-softmax supports selecting an output dtype, including converted
16-bit results.
* Logits-based sampling supports temperature scaling and optional
log-probability results in batch-invariant mode.
* Documentation covers training-forward integration and output-buffer
requirements.
* **Bug Fixes**
* Invalid output buffers and unsupported option combinations are
rejected with clear errors.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [a0b040e](https://github.com/flashinfer-ai/flashinfer/commit/a0b040ea9d490530a5020fc182adc4c7b95e2389)

- **作者**: Alex Yang
- **时间**: 2026-11-17T01:31:30Z
- **提交信息**: refactor!: remove the CAKE training kernels from FlashInfer (#9326)

<!-- .github/pull_request_template.md -->

## 📌 Description

FlashInfer is an inference library, but v0.7.3 shipped the first CAKE
**training** kernels. This PR removes them from FlashInfer. The kernels
move to cuDNN Frontend (NVIDIA/cudnn-frontend);
[`radixark/miles-ext-kernels`](https://github.com/radixark/miles-ext-kernels)
already vendors all 13 families.

**Removed (4,870 files, about 211 MB of mostly generated sources):**

| Area | What |
| --- | --- |
| Backends | all 31 packages under `flashinfer/experimental/cake/`
(`cake_<op>_<det\|nondet>_train[_kcp]`), so the `cake/` namespace
package is gone |
| Public modules | the 31 facades
`flashinfer.cake_<op>_<det\|nondet>_train[_kcp]` plus
`flashinfer/_cake_lm_head_train_knobs.py`, and their entries in
`flashinfer/__init__.py` (lazy exports plus the eager causal-conv1d and
mHC imports) |
| Ops | causal_conv1d (+kcp), dense_gemm, dsa_indexer,
dsa_sparse_attention, gated_act_mxfp8, gdn (+kcp), gqa, kda (+kcp),
lm_head, mhc, mhc_head, moe_grouped_gemm, rmsnorm, rmsnorm_silu_gate |
| Tests | ~240 training test files (`tests/experimental`, `tests/norm`,
`tests/mhc`, `tests/cpu`, `tests/test_cake_causal_conv1d_*`) and their
training-only helpers |
| Benchmarks | 28 `bench_cake_*_train*.py`,
`cake_causal_conv1d_baselines.py`,
`diag_cake_dsa_indexer_det_train_sampling.py` |
| Docs | 19 `docs/api/cake_*_train*.rst`,
`docs/training_backend_{names,migration}.md`, and the training sections
of `norm.rst`, `mamba.rst`, `mhc.rst`, `quantization.rst`,
`grouped_mm.rst` |
| Config | 11 `FLASHINFER_CAKE_DSA_*` / `FLASHINFER_CAKE_LM_HEAD_LOSS_*`
rows in `docs/development/environment_variables.md`, `pyproject.toml`
package-data, `scripts/check_cake_build_manifests.py` rows (17 packages
remain, 0 findings), `.pre-commit-config.yaml` excludes,
`.github/labeler.yml` globs, the `cake_gated_act_mxfp8_det_train` trace
template and its registry entry |

**Shared inference paths touched (please review):**

- `flashinfer.grouped_mm.grouped_mm_bf16(backend="cake")` is removed.
The experimental opt-in ran the deterministic *forward* programs of
`cake_moe_grouped_gemm_det_train`. `backend="cudnn"` (the default) is
unchanged. No in-tree test or benchmark used the Cake route.
- `flashinfer.dsa_indexer.dsa_indexer_det_topk(backend="cake")` still
raises `ValueError`; the message now says the training form was removed
rather than naming the deleted module.
- `tests/cake/test_helpers/cake_package.py` is kept (inference Cake
suites use it); only its training rows are dropped.

**No forwarding.** FlashInfer will not expose training kernels, either
directly or by calling cuDNN. This PR deletes them; the kernels are
added to cuDNN Frontend separately.

## 🔍 Related Issues

- Training-family naming and renames: #8928 (made obsolete by this PR)
- cuDNN Frontend already hosts an opt-in `kda_cake` engine for the older
KDA C16 training route: NVIDIA/cudnn-frontend#912

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues. (Hooks ran on the commit's changed files
and passed; `scripts/check_cake_build_manifests.py`: 17 packages, 0
findings.)

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.). GPU results will be
added below.
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/grouped_mm/ tests/norm/ tests/mhc/
tests/mamba/ tests/cpu/ tests/trace/
tests/experimental/test_sm120_dsa_indexer.py
tests/experimental/test_cake_stepfun_moe.py
tests/experimental/test_mok_bf16_api.py
tests/attention/test_cake_fused_qk_rope_append.py`

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

- The cuDNN Frontend counterparts covering all 13 training families have
merged, so this removal no longer waits on them.
- This is a breaking API removal for anyone importing
`flashinfer.cake_*_train*` from 0.7.3 / 0.7.4rc builds. It needs a
release-note line.
- Nearly all of the diff is generated `csrc/` under the deleted
packages. The hand-edited files are `flashinfer/__init__.py`,
`flashinfer/grouped_mm/{__init__,core}.py`, `flashinfer/dsa_indexer.py`,
`pyproject.toml`, `build_backend.py` (comment only),
`scripts/check_cake_build_manifests.py`, `.pre-commit-config.yaml`,
`.github/labeler.yml`, `docs/development/environment_variables.md`,
`benchmarks/README.md`, `flashinfer/experimental/README.md`,
`docs/index.rst`, the five `docs/api/*.rst`,
`tests/cake/test_helpers/cake_package.py`,
`tests/cpu/infra/test_build_backend_slim_wheel.py` and
`tests/trace/template_registry.py`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [57effe0](https://github.com/flashinfer-ai/flashinfer/commit/57effe034ded2501c675381ffbd78e44e9057d50)

- **作者**: Brian K. Ryu
- **时间**: 2026-11-17T00:16:01Z
- **提交信息**: feat(batch_invariant): `mm_mxfp8_mxfp4`, the MXFP8-activation x MXFP4-weight GEMM (#9366)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

A batch-invariant dense GEMM of MXFP8 activations against MXFP4 weights.
`flashinfer.mm_mxfp8_mxfp4(a, b, a_descale, b_descale, alpha=None,
out_dtype=torch.bfloat16, out=None, *, batch_invariant=False,
enable_pdl=None)` (also `flashinfer.gemm.mm_mxfp8_mxfp4`) computes `out
= cvt_rn(mul_rn(sum_k dequant(a) dequant(b), alpha))` with the mode's
guarantee: an output row's bits depend on the input values, their block
scales, `alpha`, the weight shape and the architecture alone -- not on
the batch size, the row's position, the configuration the dispatcher
picks, the chunk count's implementation or the SM count.

As a new API, **both values of `batch_invariant` will run the class
today; future PRs may change the behavior of `batch_invariant=False`.
`True` is the guarantee and keeps it.

**Contract.** `a` `(M, K)` `float8_e4m3fn` row-major (`mxfp8_quantize`'s
output); `b` `(K / 2, N)` as the transpose of a row-major `(N, K / 2)`
packed e2m1 weight (uint8 or `float4_e2m1fn_x2`, `mxfp4_quantize`'s
output; the instruction takes K-major operands only); the scales as the
quantizers' 128x4 swizzled uint8 buffers; `alpha` a 1-element fp32
tensor or None (1.0); bf16 / fp16 output (fp32 on the direct entry); `N`
a multiple of 8; **`K` a multiple of 128 on SM100 / SM103** (the TMA's
unpacking format for the 8-bit operand container reads 128-element runs
of the e2m1 rows; smaller K faults in the TMA, so it raises) and of 32
on SM107. Everything else raises `BatchInvariantUnsupportedError`;
nothing falls back.

### Performance

We profile the untuned and autotuned performance of
`flashinfer.mm_mxfp8_mxfp4`. Cold L2, CUDA-graph replay, 14 weight
shapes x 12 token counts = 168 points per part, the tuned pass at 84 of
them.

As a new API, performance comparisons require proxy APIs. References on
the same bf16 source quantized for:
**TGV** = FlashInfer's TGV low-latency block-scaled kernel on its
`A{e4m3} x B{e2m1}` path (the only other single-problem dense entry that
takes the pair; M <= 8 only). The pair's other entries are grouped:
`group_gemm_mxfp8_mxfp4_nt_groupwise` and the MoE backends.
* **batch-invariant MXFP8** -- expected to be slower due to larger
weight bits
* **batch-invariant MXFP4** -- expected to be faster due to smaller
activation bits and w4a4 tensor core operations

Heuristic "regret" is also quantified as well by computing the untuned
pick's time over the best candidate's.

#### Summary (geometric means of reference time / batch-invariant time
over the cells where the reference runs; > 1 = batch-invariant faster;
untuned / autotuner-equivalent)

Ratios are geomeans of ref time / `mm_mxfp8_mxfp4` time. > 1.0 means
`mm_mxfp8_mxfp4` is faster. The regret column value of >1.0 shows
geomean heuristic regret (1.02x means 2% regret by geomean)

**Rubin NVL4 (SM107, 212 SMs)**, `gemm.mxfp4w8a.kfold64` /
`kchunk64[C]`:

| regime | vs TGV (M <= 8) | vs batch-invariant MXFP8 | vs
batch-invariant MXFP4 | untuned regret, geomean (max) |
|---|---|---|---|---|
| decode M <= 16 | 1.66 / 1.70 (28 / 14 cells) | 1.34 / 1.35 | 1.02 /
1.04 | 1.016 (1.050) |
| mid 32 - 512 | - | 1.16 / 1.20 | 0.87 / 0.91 | 1.015 (1.049) |
| prefill >= 1024 | - | 1.08 / 1.11 | 0.70 / 0.74 | 1.018 (1.141) |
| all | 1.66 / 1.70 | 1.17 / 1.22 (168 / 84 cells) | 0.83 / 0.89 | 1.016
(1.141) |

**B200 (SM100, 148 SMs)**, `gemm.mxfp4w8a.kfold` / `kchunk[C]`:

| regime | vs TGV (M <= 8) | vs batch-invariant MXFP8 | vs
batch-invariant MXFP4 | untuned regret, geomean (max) |
|---|---|---|---|---|
| decode M <= 16 | 1.33 / 1.37 (28 / 14 cells) | 1.24 / 1.27 | 0.88 /
0.90 | 1.026 (1.077) |
| mid 32 - 512 | - | 1.13 / 1.17 | 0.80 / 0.84 | 1.026 (1.108) |
| prefill >= 1024 | - | 1.08 / 1.11 | 0.63 / 0.68 | 1.025 (1.217) |
| all | 1.33 / 1.37 | 1.14 / 1.18 | 0.74 / 0.80 | 1.026 (1.217) |

Reading: the class beats the TGV kernel at decode on both parts, is
faster than the batch-invariant MXFP8 class in every regimeand sits
below the batch-invariant MXFP4 class everywhere but Rubin's decode
regime, the expected position of an 8-bit-activation format.

#### Default picks of the shipped block-scaled classes

The dispatcher's cost model is shared by every block-scaled class, and
this PR corrects one pricing in it: an in-cluster split record
(`cluster_k > 1`) launches `cluster_k` CTAs per output tile and folds
its partners' fp32 partials through distributed shared memory at the
end, which the model priced as one CTA with a fraction of the K steps
and no fold.

The correction impacts the untuned picks of `mm_mxfp8` and `mm_fp4`. The
spaces are unchanged, the autotuner can still reach every record, and
every dispatched record is a member of its space (device-free tests,
regenerated Lean membership cases). Measured old pick time over new pick
time at the changed points, every point bit-identical:

| class | B200 (SM100): geomean / worst | Rubin (SM107): geomean / worst
|
|---|---|---|
| MXFP8 (`mm_mxfp8`) | 1.51 / 1.17 (review, 52 of 60 sampled points
changed) | 1.53 / 1.18 (26 of 154 grid points changed, all timed) |
| NVFP4 (`mm_fp4`) | 1.43 / 1.13 | 1.56 / 1.25 (42 of 154 changed, all
timed) |
| MXFP4 (`mm_fp4`, `use_nvfp4=False`) | 1.48 / 1.05 | 1.62 / 1.23 (36 of
154 changed, all timed) |

On Rubin every changed point of the campaign grid sees speedup with no
regression.

## 🔍 Related Issues

<!-- Link any related issues here -->

#9009

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

`tests/gemm/test_batch_invariant_mm_mxfp8_mxfp4.py
tests/gemm/test_batch_invariant_mm_mxfp8.py
tests/gemm/test_batch_invariant_mm_fp4.py tests/batch_invariant/`
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
* Added `mm_mxfp8_mxfp4` for matrix multiplication with MXFP8
activations and packed MXFP4 weights, including configurable output
dtype, optional scalar scaling, and dependent-launch support.
* Added batch-invariant execution with architecture-specific support and
automatic chunking on compatible GPUs.
* **Documentation**
* Documented supported inputs, hardware requirements, and
batch-invariance behavior.
* **Tests**
* Added coverage for correctness, determinism, graph replay, input
validation, and supported execution configurations.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [dcdd363](https://github.com/flashinfer-ai/flashinfer/commit/dcdd363e0d6596704779600b61932836cfb486ff)

- **作者**: Bastian Hagedorn
- **时间**: 2026-11-17T00:14:57Z
- **提交信息**: fix(gemm,moe): order the TMEM release after the epilogue's tcgen05.ld in the TGV, low-latency blockscaled and frost GEMMs (#8787)

## 📌 Description

`flashinfer/gemm/kernels/tgv_gemm_cute_ext.py` releases TMEM through
`bar_tmem_alloc` (160 arrivals = 32 MMA + 128 EPILOG), which is used for
two rounds: round 0 publishes the TMEM allocation, round 1 says the
epilogue has read the accumulator. The MMA warp makes its round-0
arrival after `alloc_tmem`, runs the K-loop, makes its round-1 arrival,
waits with `mbarrier_wait(bar_tmem_alloc, 1)` and deallocates. It never
waits for round 0.

If two or more EPILOG warps have not yet made their first arrival when
the MMA warp arrives the second time, that arrival counts toward round
0, round 0 stays open, and the parity-1 wait returns immediately: parity
1 then names the barrier's "immediately preceding phase", which is
complete by definition (PTX ISA, [`mbarrier.test_wait` /
`mbarrier.try_wait`](https://docs.nvidia.com/cuda/parallel-thread-execution/#parallel-synchronization-and-communication-instructions-mbarrier-test-wait-try-wait)).
`tcgen05.dealloc` then runs before the epilogue's `tcgen05.ld`.

This is the same defect that #6786 reported and #7443 fixed in
`dense_bf16_gemm_sm100_splitk.py`; the TGV kernel still has the original
sequence. Its window is shorter than the split-K kernel's: in the 2-CTA
tactics the non-leader CTA's MMA warp skips the K-loop (`if
is_leader:`), so its two arrivals are back to back and the race is
against the EPILOG warps' first few instructions.

**Change**

1. `mbarrier_wait(bar_tmem_alloc, 0)` before the MMA warp's release
arrival. In the leader and in the 1-CTA tactics this wait is already
satisfied by the time the K-loop ends; in the non-leader CTA it waits
for the EPILOG warps' first arrival.
2. 2-CTA only: a 32-count `bar_tmem_dealloc` mbarrier on which the two
MMA warps rendezvous (arrive on the peer's word, wait on ours) before
`tcgen05.dealloc.cta_group::2`. The PTX ISA section on `tcgen05.alloc` /
`tcgen05.dealloc` / `tcgen05.relinquish_alloc_permit`
([link](https://docs.nvidia.com/cuda/parallel-thread-execution/#tcgen05-instructions-tcgen05-alloc-dealloc-relinquish-alloc-permit);
section numbers move between ISA versions, the anchor does not)
describes that instruction as one collective operation of the CTA pair
and requires that the "issuing warp and peer CTA warp must synchronize
Tensor Memory accesses before attempting to collectively deallocate";
`cutlass.utils.TmemAllocator.free` does the same handshake. The comment
that said the 2-CTA dealloc is "per-CTA, no cross-CTA handshake" is
replaced. This part is ISA conformance rather than a fix for an observed
failure; happy to drop it if the minimal change is preferred.

**How it was reproduced (B200, CUDA 13.0)**

The shipped launch requests the full shared-memory capacity, so no other
CTA is co-resident and the freed columns are not reallocated before the
CTA exits; the race is latent there and the output stays correct. It
becomes visible with two perturbations: hold EPILOG warps 6 and 7 of the
non-leader CTA back before their first arrival (a `nanosleep` loop), and
launch with a shared-memory request close to the tactic's footprint so
two GEMM CTAs share an SM (the next cluster's `tcgen05.alloc` takes the
freed columns and its first MMA overwrites them).

Tactic 16 (2-CTA 64x16x128, 6 stages), 4096 CTAs, 50 launches each,
output checked against an fp32 reference:

| EPILOG stall | unfixed: launches with wrong tiles | wrong tiles (rank
0 / rank 1) | fixed |
|---|---|---|---|
| 100 µs | 50/50 | 0 / 12246 | 0/50 |
| 10 µs | 18/50 | 0 / 7072 | 0/50 |
| none | 0/200 | 0 / 0 | 0/200 |

The 1-CTA tactics have the same bug with the K-loop-long window: with
the stall applied in every CTA, 20/20 launches wrong before the fix,
0/20 after. All wrong elements were in the non-leader CTA's tile (rank
1) in the 2-CTA runs. The standalone script that patches the stall in
and runs this comparison can be attached if useful.

Performance was not measured for this PR; the added wait is satisfied
before it is reached in the leader and in every 1-CTA tactic, and the
handshake is one cross-CTA mbarrier arrive/wait per CTA.

## 🔍 Related Issues

#6786, #7443 (same race in `dense_bf16_gemm_sm100_splitk.py`). The
SGLang copy of this kernel
(`python/sglang/kernels/ops/gemm/cutedsl_bf16_gemm.py`) has the
identical `mma_warp` and gets the same change in
sgl-project/sglang#48616.

Two more kernels in this repo release TMEM with the same arrive,
parity-1 wait, dealloc sequence in their 1-CTA `mma_warp` and no phase-0
wait: `flashinfer/fused_moe/backends/frost_low_latency/gemm.py` and
`flashinfer/gemm/kernels/cute_dsl/low_latency_blockscaled_gemm.py`
(barrier `tmem_alloc_result_bar`, 32 MMA + 128 epilogue (+ 128 SFB)
arrivals). There the MMA warp runs the K-loop between its two arrivals,
so the window is as long as the K-loop rather than a few instructions,
but the defect is the same. Commit 37f76106 adds the one-line phase-0
wait to both; being 1-CTA they need no peer handshake. Both patched
files were compile-checked (NVFP4 split-K 2 configuration of the
low-latency GEMM; the frost routed GEMM through a standalone wrapper of
its `prepare` + `device_body`), not run on hardware:
`tests/gemm/test_low_latency_blockscaled_gemm.py` and
`tests/moe/test_frost_low_latency_*.py` should be in the CI run.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

- [ ] Tests have been added or updated as needed. (No new test: the race
needs an injected stall and a trimmed shared-memory request to become
observable; the existing TGV tests pass before and after.)
- [ ] All tests are passing (`unittest`, etc.). (Not run on CI yet;
draft.)
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).

Suggested CI test targets: `tests/gemm/test_tgv_gemm.py
tests/gemm/test_mm_bf16.py tests/gemm/test_bmm_bf16.py
tests/gemm/test_low_latency_blockscaled_gemm.py
tests/moe/test_frost_low_latency_grouped_block_fp8.py
tests/moe/test_frost_low_latency_nvfp4.py`

## Reviewer Notes

The one-line phase-0 wait is the bug fix (TGV, low-latency blockscaled
GEMM, frost routed GEMM); the 2-CTA handshake in the TGV kernel is
optional ISA conformance. Reviewers who want to see the race: the stall
must hit two of the four EPILOG warps of the rank-1 CTA before their
first `bar_tmem_alloc` arrival, and something must reallocate the freed
TMEM columns during the CTA's lifetime, which the shipped full-capacity
shared-memory request prevents.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved synchronization during low-latency GEMM operations that use
tensor memory, including memory release and deallocation. Two-CTA
execution now coordinates both participating CTAs, while single-CTA
execution retains its existing behavior. Barrier sequencing is also more
consistent across affected GEMM paths, helping prevent synchronization
issues in supported configurations.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [d4afbc1](https://github.com/flashinfer-ai/flashinfer/commit/d4afbc1004fcf43196e51fcf9f41b02de2e7cd43)

- **作者**: Dhiraj Reddy (cuDNN/FlashInfer)
- **时间**: 2026-11-17T00:10:36Z
- **提交信息**: perf(moe): one persistent DeepSeek FP8 activation kernel for the trtllm-gen MoE (#9329)

## 📌 Description

### Summary

The trtllm-gen fused MoE runs a separate activation kernel between its
two expert GEMMs when the model uses DeepSeek FP8 block scaling: SwiGLU
plus re-quantization of GEMM1's output to e4m3 with one scale per 128
columns. The existing kernel, `activationDeepSeekKernel`, launches one
block per column block of every (token, top-k slot) pair, packing 2 or 4
tokens into a block at larger token counts, and its time grows with
tokens × top-k even though, under expert parallelism, most of those
slots belong to other GPUs. This PR replaces it, for the fused MoE, with
one persistent kernel that launches at most 8 blocks per SM and decides
on the device, from the live row count that routing produced, how to
split the work. For finite inputs the kernel writes exactly the same
bytes as the old one, and both kernels drop a NaN from GEMM1 alike (see
Correctness).

Measured inside the fused MoE call on two exclusively allocated cluster
nodes, a B300 (sm_103) node and a Vera Rubin (sm_107) tray (tables
below; speedups are before / after; 1 to 128 tokens are the headline
range, 256 tokens and above are context rows): with PDL off, so that the
profiler reports the kernel's own time, the activation is 1.2x faster at
1 token (no local pair on this rank, so the kernel exits on an empty
list), 0.88x to 0.95x at 2 and 4 tokens and at 8 tokens on the sm_107
tray (0.1 to 0.3 us slower; its one-round-trip schedule pays off only
when the launch overlaps GEMM1), 1.00x to 1.09x otherwise at 8 and 16
tokens, 1.3x to 2.5x faster at 32 to 128 tokens, and 3.2x to 13.2x in
the context rows from 256 to 2048 tokens. With PDL on, the production
launch mode, the whole fused MoE call at EP8 is 1.00x to 1.06x at 1 to
16 tokens, inside the 1 to 2 % control drift except on the B300 at 4 and
8 tokens (1.04x and 1.03x), 1.02x to 1.04x faster at 32 to 128 tokens
and 1.05x to 1.40x in the context rows from 256 to 2048 tokens. End to
end in vLLM 0.32.0 on 8x B300 (GLM-5.3, TP8 attention + EP8 MoE, two
baseline / patched pairs, each on one exclusive node, section below),
the decode step is 1.5 % shorter at 128 and 144 concurrent requests (2.4
% at 256, a context row), inside the pairs' drift at 64 requests and
below, and a 16K-token prefill chunk is 8.3 % shorter; held at the
baseline's interactivity instead, the patched build carries fewer than
16 more requests at 128 and at 256 by the measured points (about 5 and
2.4 % more by interpolation between them); per MoE layer the
activation's exclusive time falls from 6.0 to 1.9 us at 64 requests and
from 823 to 38 us in the prefill chunk. The old kernel stays for the one
caller that does not provide the row map (the standalone activation op).

### What changes

- `csrc/fused_moe/trtllm_backend/trtllm_fused_moe_dev_kernel.cu`: the
new kernel `activationDeepSeekKernelPersistent128` and its host side;
`activation::run()` selects it whenever
`persistentActivationSupported()` holds (row map and bound present,
128-wide scale blocks, whole blocks per row, 16-byte aligned buffers,
and the tile → expert map when the per-expert SwiGLU controls are set),
else the old kernel as before.
- `include/flashinfer/trtllm/fused_moe/DevKernel.h`,
`csrc/trtllm_fused_moe_runner.cu`: `activation::Data` carries the
permuted row → token map and the padded-row bound, set by the runner
from its workspace.
- `csrc/trtllm_batched_gemm_runner.cu`: with PDL on, a check that a
kernel the interface launches with the PDL attribute (one with any
grid-dependency wait or fine-grained-consumer flag) waits on its primary
and cannot trigger its dependent launch or exit before that wait, the
property the glue kernels' pre-wait reads rely on. It holds for all 8350
kernels of the pinned manifest.
- `tests/moe/test_trtllm_gen_moe_activation_persistent.py` (new): the
fused MoE launches the persistent kernel, and only it, at 1, 8, 64 and
1024 tokens with all experts local and with a quarter local, PDL on and
off; PDL on and PDL off produce identical bytes at 1, 8, 64 and 512
tokens, with and without per-expert SwiGLU controls; under expert
parallelism (a quarter of the experts local, where the kernel walks the
permuted rows and resolves each row's expert through the tile map) the
output matches the dequantized reference at 8, 32 and 64 tokens, with
and without per-expert controls (at 8 tokens the padded row count is at
most the pair count, so the kernel takes the rows list at or just inside
its boundary; at 32 and 64 tokens it takes it with margin, the padded
rows being about half the pairs at the default tiles); a rank with no
(token, slot) pair at all gets an empty work list and an all-zero,
PDL-independent output.
- `tests/moe/test_trtllm_gen_fused_moe.py`: the DeepSeek FP8
SwiGLU-controls test also checks distinct per-expert values against the
reference, with neighbouring experts far apart so that a lookup off by
one GEMM tile would fail the comparison.

No Python API change; `activation::Data` gains two fields with defaults,
so other callers of `activation::run()` are unaffected.

### How the kernel works

A *piece* is one 128-column scale block of one permuted row. 32 lanes of
a warp own a piece when there are few pieces (4 bytes per lane, 5
xor-shuffles for the block maximum) and 8 lanes when there are many (16
bytes per lane); no shared memory, no block barrier. Every block strides
over a work list, and the kernel picks the list on the device: the
permuted rows (skipping padding rows) when the live padded row count P
is at most the number of (token, slot) pairs, else the pairs (skipping
pairs routed to other GPUs). Neither padding nor remote pairs cost a
data load. The list entry of a piece is fetched two pieces ahead and its
data one piece ahead, so each piece costs one memory round trip.

P, the two index tables and the tile → expert map are routing outputs,
and the kernel reads them before its PDL wait: GEMM1, the kernel it
depends on, waits on routing in every CTA before it triggers or exits,
and `griddepcontrol.wait` returns only when routing has completed with
its writes visible, so those tables are final whenever this kernel runs.
GEMM1's output is read only after the wait. The per-expert SwiGLU
controls (alpha, beta, clamp) are looked up once per piece instead of
once per element.

### Correctness

- Bit-identical to `activationDeepSeekKernel` on every live row and
scale in a standalone harness: 150 configurations with the 128-wide
scale block in the prototype's final revision (GLM and Qwen shapes, 8-
and 64-row GEMM tiles, EP8 and EP1, 1 to 2048 tokens, with and without
per-expert controls), plus 48 with the 32-wide block that is not
compiled here; padding rows are left untouched, as the old kernel leaves
them.
- Inside the fused MoE, the `main` build and this branch produce
bit-identical outputs (the final output and the GEMM2 rows of every
local pair) in all 11 cases of a module-level comparison on an sm_107
board: the GLM-5.3 shape on EP8 rank 3 at 1, 7, 49, 50, 64, 256, 2048
tokens; the GLM-5.3 shape on EP8 rank 0 at 7, 256 tokens; a shape with
five scale blocks per row (intermediate 640) on EP8 rank 1 at 7, 256
tokens.
- Module tests: the new test file (40 cases) passes on sm_100 and sm_107
boards; the DeepSeek FP8 SwiGLU-controls test, the Prims-TS (the
explicit unified-MoE backend described in `docs/api/fused_moe.rst`)
block-scale test and the renormalize-FP8 routing file pass; the new test
skips on other architectures.
- Numerics are the old kernel's operation for operation. The block
maximum is reduced with `fmaxf`, as the old kernel's 2- and 4-token
instantiations do; its 1-token instantiation reduces with
`cuda::maximum<>`, which the vendored CCCL implements as `fmax` for
float (a hardware `redux.sync.max` on the sm_100a / sm_100f builds), so
all three reductions drop a NaN alike and no difference is expected for
a NaN input either; the bitwise comparisons used finite inputs.

### Performance

Problem: `trtllm_fp8_block_scale_moe` as vLLM calls it for GLM-5.3 at
EP8: hidden 6144, intermediate 2048, 256 experts, top-k 8, DeepSeekV3
routing with bias, one rank's 32 local experts (`local_expert_offset`
96) so one in eight (token, slot) pairs is local, CUDA graph replay;
routing logits are drawn on the device with a fixed seed, and the draw
differs between the two environments from 512 tokens up, hence the
different local-pair counts there. 1 to 128 tokens are the decode range
and the headline; 256 to 2048 tokens are context rows (beyond the
headline range, not the prefill phase).

**Reproducible benchmark.** The repository benchmark, baseline (`main`
at the merge base) and this branch alternating three times on the
exclusively allocated sm_107 tray, whole call by CUDA events. Two of its
limits shape the configuration: its reference routing needs `topk_group
× n_group ≥ top_k`, so DeepSeek-V3's grouping (8 groups of 32 experts, 4
chosen) stands in for GLM's single group, and it allocates weights for
every expert, so all 256 experts are local here (every (token, slot)
pair is local, the EP1 case; the EP8 case follows in the tables below).

```
python benchmarks/flashinfer_benchmark.py --routine trtllm_fp8_block_scale_moe --num_tokens <T> \
  --hidden_size 6144 --intermediate_size 2048 --num_experts 256 --top_k 8 --n_group 8 --topk_group 4 \
  --routed_scaling_factor 2.5 --routing_method deepseek_v3 --use_routing_bias \
  --use_cuda_events --num_iters 30 --dry_run_iters 10 [--enable_pdl]
```

| tokens | before, us | after, us | speedup (before / after) |
|---|---|---|---|
| 1 | 48.8 | 48.0 | 1.02x |
| 2 | 68.2 | 67.5 | 1.01x |
| 4 | 111.4 | 109.9 | 1.01x |
| 8 | 179.9 | 178.4 | 1.01x |
| 16 | 300.9 | 299.6 | 1.00x |
| 32 | 469.1 | 466.2 | 1.01x |
| 64 | 630.1 | 625.0 | 1.01x |
| 128 | 715.9 | 707.6 | 1.01x |
| 256 (context) | 863.8 | 848.7 | 1.02x |
| 512 (context) | 1286.9 | 1258.2 | 1.02x |
| 1024 (context) | 1375.9 | 1318.8 | 1.04x |
| 2048 (context) | 1497.4 | 1383.0 | 1.08x |

<sup>Rubin (sm_107), 212 SMs, exclusively allocated Vera Rubin NVL72
tray of a cluster, PDL on, whole fused MoE call by CUDA events, all 256
experts local, CUDA graph replay; 3 + 3 records, base and new
alternating, median of 30 timed iterations per record.</sup>

| tokens | before, us | after, us | speedup (before / after) |
|---|---|---|---|
| 1 | 52.5 | 52.5 | 1.00x |
| 2 | 71.3 | 71.8 | 0.99x |
| 4 | 113.5 | 113.5 | 1.00x |
| 8 | 182.2 | 182.0 | 1.00x |
| 16 | 303.3 | 303.1 | 1.00x |
| 32 | 471.4 | 469.5 | 1.00x |
| 64 | 633.3 | 628.6 | 1.01x |
| 128 | 718.3 | 710.6 | 1.01x |
| 256 (context) | 865.4 | 851.0 | 1.02x |
| 512 (context) | 1287.9 | 1259.1 | 1.02x |
| 1024 (context) | 1379.4 | 1323.0 | 1.04x |
| 2048 (context) | 1500.2 | 1386.0 | 1.08x |

<sup>Rubin (sm_107), 212 SMs, exclusively allocated Vera Rubin NVL72
tray of a cluster, PDL off, whole fused MoE call by CUDA events, all 256
experts local, CUDA graph replay; 3 + 3 records, base and new
alternating, median of 30 timed iterations per record.</sup>

**Kernel-own time.** The activation kernel's own time inside the EP8
call, from the torch profiler, with PDL off so that the profiler span is
the kernel's own (under PDL a kernel's span includes its wait for its
primary); baseline and new alternating three times in one session on
each node. The EP8 tables come from a standalone script outside the tree
that issues vLLM's `trtllm_fp8_block_scale_moe` call for one EP8 rank
(random logits with a fixed seed, CUDA graph replay, 30 iterations per
size); the repository benchmark above is the in-tree reproduction:

| tokens | local pairs | before, us | after, us | speedup (before /
after) |
|---|---|---|---|---|
| 1 | 0 | 1.73 | 1.47 | 1.17x |
| 2 | 1 | 2.08 | 2.37 | 0.88x |
| 4 | 3 | 2.24 | 2.50 | 0.90x |
| 8 | 6 | 2.78 | 2.62 | 1.06x |
| 16 | 10 | 3.17 | 2.91 | 1.09x |
| 32 | 28 | 4.42 | 3.06 | 1.45x |
| 64 | 61 | 6.86 | 3.46 | 1.99x |
| 128 | 118 | 9.42 | 3.84 | 2.45x |
| 256 (context) | 273 | 16.00 | 4.19 | 3.82x |
| 512 (context) | 528 | 28.11 | 4.66 | 6.04x |
| 1024 (context) | 1068 | 54.18 | 5.87 | 9.23x |
| 2048 (context) | 1983 | 103.39 | 7.84 | 13.19x |

<sup>B300 (sm_103), 148 SMs, exclusively allocated cluster node, PDL
off, kernel-own time, EP8 rank 3, base and new alternating; 3 + 3
records, medians over 30 iterations per record.</sup>

| tokens | local pairs | before, us | after, us | speedup (before /
after) |
|---|---|---|---|---|
| 1 | 0 | 1.57 | 1.31 | 1.20x |
| 2 | 1 | 1.98 | 2.11 | 0.94x |
| 4 | 3 | 2.08 | 2.34 | 0.89x |
| 8 | 6 | 2.53 | 2.66 | 0.95x |
| 16 | 10 | 2.62 | 2.62 | 1.00x |
| 32 | 28 | 4.16 | 3.17 | 1.31x |
| 64 | 61 | 5.25 | 3.18 | 1.65x |
| 128 | 118 | 7.68 | 3.46 | 2.22x |
| 256 (context) | 273 | 12.38 | 3.87 | 3.20x |
| 512 (context) | 494 | 21.76 | 4.22 | 5.15x |
| 1024 (context) | 1029 | 40.45 | 4.96 | 8.15x |
| 2048 (context) | 2070 | 77.14 | 6.14 | 12.55x |

<sup>Rubin (sm_107), 212 SMs, exclusively allocated Vera Rubin NVL72
tray of a cluster, PDL off, kernel-own time, EP8 rank 3, base and new
alternating; 3 + 3 records, medians over 30 iterations per record.</sup>

**Whole call with PDL on**, the production launch mode, by CUDA events,
baseline and new alternating three times:

| tokens | local pairs | before, us | after, us | speedup (before /
after) |
|---|---|---|---|---|
| 1 | 0 | 22.7 | 21.4 | 1.06x |
| 2 | 1 | 35.8 | 35.8 | 1.00x |
| 4 | 3 | 43.9 | 42.1 | 1.04x |
| 8 | 6 | 66.5 | 64.6 | 1.03x |
| 16 | 10 | 92.5 | 91.1 | 1.01x |
| 32 | 28 | 134.0 | 130.0 | 1.03x |
| 64 | 61 | 187.6 | 183.3 | 1.02x |
| 128 | 118 | 218.1 | 210.6 | 1.04x |
| 256 (context) | 273 | 236.5 | 224.2 | 1.05x |
| 512 (context) | 528 | 259.1 | 234.5 | 1.11x |
| 1024 (context) | 1068 | 291.8 | 242.5 | 1.20x |
| 2048 (context) | 1983 | 385.0 | 287.7 | 1.34x |

<sup>B300 (sm_103), 148 SMs, exclusively allocated cluster node, PDL on,
whole fused MoE call by CUDA events, EP8 rank 3, base and new
alternating; 3 + 3 records, medians over 30 iterations per record.</sup>

| tokens | local pairs | before, us | after, us | speedup (before /
after) |
|---|---|---|---|---|
| 1 | 0 | 24.8 | 24.8 | 1.00x |
| 2 | 1 | 32.9 | 32.5 | 1.01x |
| 4 | 3 | 35.7 | 35.1 | 1.02x |
| 8 | 6 | 42.6 | 42.2 | 1.01x |
| 16 | 10 | 56.7 | 55.7 | 1.02x |
| 32 | 28 | 79.6 | 78.1 | 1.02x |
| 64 | 61 | 113.2 | 110.8 | 1.02x |
| 128 | 118 | 122.6 | 117.7 | 1.04x |
| 256 (context) | 273 | 133.1 | 124.4 | 1.07x |
| 512 (context) | 494 | 160.8 | 143.1 | 1.12x |
| 1024 (context) | 1029 | 175.7 | 138.6 | 1.27x |
| 2048 (context) | 2070 | 250.9 | 179.4 | 1.40x |

<sup>Rubin (sm_107), 212 SMs, exclusively allocated Vera Rubin NVL72
tray of a cluster, PDL on, whole fused MoE call by CUDA events, EP8 rank
3, base and new alternating; 3 + 3 records, medians over 30 iterations
per record.</sup>

The two expert GEMMs plus routing, which this PR does not touch, agree
between the two sides within 2 % from 4 tokens up on both nodes and,
with PDL on, move 8 to 10 % at 2 tokens (a short call whose spans hold
the PDL waits, so a small absolute drift reads large; with PDL off the
2-token control moves under 1 %); the call-time spread across the three
repetitions is 0.1 to 0.4 % in the median on both nodes and reaches 14 %
(sm_107 tray) and 19 % (B300) only in the 1-token cell, the shortest
call.

### End to end: GLM-5.3 in vLLM 0.32.0 on 8x B300 (two same-node
baseline / patched pairs; step times measured, percentages derived from
the tables)

**Setup.** Two pairs, each on one exclusively allocated 8x B300 node of
the same cluster (a different node per pair), the baseline arm first and
the patched arm right after it on the same node, so that node-to-node
differences cancel within a pair (driver 580 with the CUDA 13.2
forward-compatibility user-mode driver, CUDA toolkit 13.2), TP8
(tensor-parallel) attention + EP8 (expert-parallel) MoE, vLLM 0.32.0's
own release build with the FlashInfer release it pins (0.7.0.post1). The
three source files of this PR (the kernel file, `DevKernel.h`, the fused
MoE runner) were ported onto that release and copied into the patched
arm's Python environment, which JIT-builds the module from them; the
port differs from this PR only where the release lacks the feature (it
has no 32-wide scale block, so the kernel's block-width check is
dropped) and leaves out the new check in the batched GEMM runner (the
release pins an older trtllm-gen export; the check does not affect
timing). The baseline arm is the same environment with the released
files. The activation the patched arm replaces,
`activationDeepSeekKernel`, performs the same operations for the
128-wide scale block in the release and on `main` (`main`'s version adds
the 32-wide branch of #8666, which this configuration never takes), so
the gains below are gains against `main`'s kernel; the finalize kernels
are the release's in both arms (the scalar `finalizeKernel` up to 32
requests, `finalizeKernelVecLoad` from 64). Both arms run with
FlashInfer's autotuner off
(`--kernel-config.enable_flashinfer_autotune=false`), so every GEMM uses
the library's default tactic in both arms, each arm compiling FlashInfer
into its own cache directory; the traces show identical kernel names in
both arms apart from the activation (27 profiled windows per arm in each
pair, none differing) and `activationDeepSeekKernelPersistent128` in
every window of the patched arms. The cells, driven by `vllm bench
serve` (`--kv-cache-dtype fp8_e4m3`): decode at 1, 2, 4, 8, 16, 32, 64,
72, 128 and 144 concurrent requests (8K-token random prompts decoded
greedily to a fixed output length per cell; at TP8 + EP8 every rank's
MoE call sees that many tokens per layer), 256 and 272 as context rows,
beyond the headline range of 1 to 128 requests (288 would exceed our
capture script's rule of 85 % of the KV cache at this prompt length),
one 16K-token prefill chunk of a 32K prompt, and serving at 256
concurrent requests on ShareGPT with sampling (indicative). 72, 144 and
272 are the next measured points above 64, 128 and 256: they let the
fixed-interactivity question, how many requests the patched build
carries at the baseline's step, be read from measured steps. The step is
the trace step period, the mean over the 8 ranks of the time between
forward steps inside a profiled window (two windows per cell and arm,
one for the prefill chunk); the unprofiled client step is the client's
median time between output tokens in a second run of the same cell
without the profiler. The GEMM column is the drift control: the two
expert GEMMs run identical cubins in both arms, so their movement is the
pair's noise. The two pairs' step changes agree within 1.1 points in the
decode and context cells from 128 requests up (the indicative serving
cell apart, see below) and within 2.4 points below, apart from the
64-request cell (4.1 points; see below). The tables give signed changes
rather than before / after ratios, so that gains and losses read in one
column.

Step time, vLLM, same-node pairs: both arms of a pair on one exclusive
8x B300 node, baseline first; a cell's step is the trace step period
(mean over the arm's profiled windows, a window whose GPU idle exceeds
15 % of the period left out), mean over 2 pairs, the per-pair changes in
parentheses; the unprofiled client step is the client's median time
between output tokens in a second run of the cell without the profiler.
The activation + finalize column is traced spans (under programmatic
dependent launch a span also holds the kernel's wait for its
predecessor, equal in both arms); exclusive times are in the per-layer
table. The GEMM column is the same-node drift control: GEMM1 + GEMM2
spans per step, identical cubins in both arms.

| concurrent requests (decode rows: = tokens per rank per MoE call) |
baseline step, ms | patched step, ms | change, % (per pair) | unprofiled
client step, baseline -> patched ms (change, %) | activation + finalize
per step, baseline -> patched ms (change, % of the baseline step) |
GEMM1 + GEMM2 per step, baseline -> patched ms (change, %) |
|---|---|---|---|---|---|---|
| 1 | 9.178 | 9.163 | -0.16 (-0.14, -0.19) | 8.957 -> 8.909 (-0.53) |
0.741 -> 0.742 (+0.01) | 1.678 -> 1.694 (+0.98) |
| 2 | 10.226 | 10.230 | +0.04 (-0.12, +0.20) | 9.969 -> 9.975 (+0.06) |
0.868 -> 0.871 (+0.03) | 2.124 -> 2.151 (+1.27) |
| 4 | 11.273 | 11.217 | -0.50 (-1.53, +0.54) | 11.059 -> 11.096 (+0.33)
| 0.945 -> 0.945 (-0.00) | 2.689 -> 2.701 (+0.44) |
| 8 | 12.574 | 12.495 | -0.62 (-0.18, -1.07) | 12.430 -> 12.267 (-1.31)
| 1.021 -> 0.994 (-0.22) | 3.780 -> 3.714 (-1.75) |
| 16 | 14.567 | 14.375 | -1.32 (-1.52, -1.13) | 14.380 -> 14.237 (-1.00)
| 1.070 -> 1.016 (-0.37) | 4.876 -> 4.789 (-1.80) |
| 32 | 17.261 | 17.197 | -0.37 (-1.55, +0.80) | 17.236 -> 16.956 (-1.62)
| 1.140 -> 1.006 (-0.78) | 6.677 -> 6.799 (+1.82) |
| 64 | 20.858 | 21.122 | +1.27 (-0.78, +3.34) | 20.773 -> 20.820 (+0.23)
| 1.431 -> 1.127 (-1.46) | 8.953 -> 9.154 (+2.24) |
| 72 | 21.556 | 21.419 | -0.64 (+0.18, -1.44) | 21.466 -> 21.160 (-1.42)
| 1.522 -> 1.239 (-1.31) | 9.152 -> 9.236 (+0.92) |
| 128 | 25.105 | 24.735 | -1.47 (-1.06, -1.88) | 24.823 -> 24.487
(-1.35) | 1.684 -> 1.246 (-1.74) | 11.290 -> 11.291 (+0.01) |
| 144 | 26.065 | 25.672 | -1.50 (-0.95, -2.05) | 25.621 -> 25.370
(-0.98) | 1.810 -> 1.360 (-1.72) | 11.533 -> 11.645 (+0.97) |
| 256 (context) | 32.496 | 31.707 | -2.43 (-2.04, -2.81) | 31.899 ->
31.076 (-2.58) | 2.284 -> 1.439 (-2.60) | 13.027 -> 13.386 (+2.75) |
| 272 (context) | 34.416 | 33.744 | -1.95 (-1.91, -2.00) | 34.184 ->
33.502 (-2.00) | 2.398 -> 1.644 (-2.19) | 13.558 -> 13.707 (+1.10) |
| one 16K prefill chunk of a 32K prompt | 745.901 | 683.996 | -8.30
(-8.36, -8.24) | - | 70.523 -> 11.629 (-7.90) | 95.539 -> 95.563 (+0.02)
|
| serving, 256 concurrent ShareGPT requests (indicative) | 70.790 |
76.004 | +7.37 (+2.69, +12.28) | - | 3.393 -> 1.647 (-2.47) | 15.431 ->
15.501 (+0.45) |

Fixed interactivity, measured: the baseline's step at a reference
concurrency against the patched arm's step at that concurrency and at
the next measured points above it. "Requests at the baseline's latency"
is the largest measured patched concurrency whose step does not exceed
the baseline's reference step (per-pair values in parentheses); the
tokens-per-second column is (requests / step) of the patched arm at that
concurrency against (requests / step) of the baseline at the reference:
the same requests at a shorter step, a measured lower bound of the gain
at the baseline's latency, not a separate reading. The crossing is a
linear interpolation between the two measured patched points that
bracket the baseline step (both ends measured; none when the largest
measured point is still below the baseline step).

| reference | baseline step at the reference, ms | patched step at the
reference and above, ms (concurrency) | requests at the baseline's
latency, measured (per pair) | tokens per second at that concurrency
(lower bound at the baseline's latency) | crossing between measured
points |
|---|---|---|---|---|---|
| 64 requests | 20.858 | 21.122 (64), 21.419 (72) | none (pair 1: 64,
pair 2: none) | - | - |
| 128 requests | 25.105 | 24.735 (128), 25.672 (144) | 128 (pair 1: 128,
pair 2: 128) | +1.5 % (128 requests at 24.735 ms vs 128 at 25.105 ms) |
134 requests (+4.9 % vs 128) |
| 256 requests | 32.496 | 31.707 (256), 33.744 (272) | 256 (pair 1: 256,
pair 2: 256) | +2.5 % (256 requests at 31.707 ms vs 256 at 32.496 ms) |
262 requests (+2.4 % vs 256) |

Per MoE layer, vLLM, from the rank-0 traces, mean over the arm's windows
of 2 pairs (windows left out of the step period left out here too; block
= GEMM1 start to finalize end; exclusive = end minus the later of the
kernel's own start and the previous kernel's end, so a gap between two
kernels is in the block but in neither kernel).

| concurrent requests | windows (baseline / patched) | MoE expert block
per layer, baseline -> patched us (change) | activation, exclusive us |
finalize, exclusive us | GEMM1 + GEMM2, exclusive us (same cubins;
change, %) |
|---|---|---|---|---|---|
| 1 | 4 / 4 | 22.98 -> 22.67 (-0.31) | 1.76 -> 1.67 (-0.09) | 1.87 ->
1.94 (+0.07) | 19.30 -> 19.00 (-1.55) |
| 2 | 4 / 4 | 28.84 -> 28.49 (-0.35) | 1.99 -> 1.92 (-0.08) | 1.94 ->
2.02 (+0.08) | 24.79 -> 24.42 (-1.49) |
| 4 | 4 / 4 | 36.98 -> 36.70 (-0.27) | 2.21 -> 2.00 (-0.21) | 2.12 ->
2.24 (+0.12) | 32.55 -> 32.34 (-0.65) |
| 8 | 4 / 4 | 51.29 -> 50.23 (-1.06) | 2.40 -> 1.84 (-0.57) | 2.33 ->
2.46 (+0.13) | 46.42 -> 45.79 (-1.37) |
| 16 | 4 / 4 | 67.74 -> 65.22 (-2.51) | 2.56 -> 1.78 (-0.78) | 2.60 ->
2.65 (+0.05) | 61.54 -> 59.77 (-2.89) |
| 32 | 4 / 4 | 94.55 -> 93.75 (-0.80) | 3.77 -> 1.88 (-1.89) | 2.85 ->
2.86 (+0.01) | 87.92 -> 89.00 (+1.23) |
| 64 | 4 / 4 | 128.19 -> 127.88 (-0.31) | 6.05 -> 1.87 (-4.18) | 4.73 ->
4.75 (+0.01) | 117.40 -> 121.25 (+3.28) |
| 72 | 4 / 4 | 130.88 -> 129.65 (-1.23) | 6.08 -> 2.28 (-3.80) | 4.95 ->
4.97 (+0.02) | 119.84 -> 122.40 (+2.13) |
| 128 | 4 / 4 | 162.09 -> 157.24 (-4.85) | 8.79 -> 2.87 (-5.91) | 5.36
-> 5.35 (-0.00) | 147.93 -> 148.99 (+0.72) |
| 144 | 4 / 4 | 166.71 -> 161.42 (-5.29) | 9.58 -> 3.57 (-6.01) | 5.55
-> 5.54 (-0.02) | 151.56 -> 152.30 (+0.49) |
| 256 (context) | 4 / 4 | 192.90 -> 186.19 (-6.71) | 15.08 -> 3.84
(-11.25) | 6.34 -> 6.32 (-0.02) | 171.35 -> 175.91 (+2.66) |
| 272 (context) | 4 / 4 | 200.76 -> 192.40 (-8.36) | 15.74 -> 5.66
(-10.08) | 6.58 -> 6.61 (+0.03) | 178.40 -> 180.09 (+0.95) |
| one 16K prefill chunk of a 32K prompt | 2 / 2 | 2213.59 -> 1428.47
(-785.12) | 823.38 -> 38.15 (-785.23) | 116.86 -> 116.72 (-0.14) |
1273.16 -> 1273.29 (+0.01) |
| serving, 256 concurrent ShareGPT requests (indicative) | 4 / 4 |
240.50 -> 218.14 (-22.36) | 29.21 -> 5.70 (-23.52) | 7.73 -> 7.81
(+0.08) | 203.50 -> 204.49 (+0.49) |

Planned cells without a measurement, left out of every table above: 288
(context) (not measured in any arm of any pair)

**What it says, at fixed concurrency.** The decode step is 1.5 % shorter
at 128 and at 144 requests (the pairs between −1.0 and −2.1 %; the
unprofiled client step −1.0 to −1.4 %) and, in the context rows, 2.4 %
shorter at 256 (the two pairs −2.0 and −2.8 %; the client step −2.6 %)
and 2.0 % at 272, so from 128 requests up each user's tokens arrive 1.5
to 2.4 % sooner and the server emits as many percent more tokens per
second; at 256 the control GEMMs read 2.8 % longer per step in both
pairs (1.1 % of the step), opposite to the step change, so the drift
there works against the gain, not for it. At 16 requests the step reads
1.5 and 1.1 % shorter, but the control GEMMs read 2.2 and 1.4 % shorter
in the same cell (the activation's own saving is 0.4 % of the step), so
this is inside the drift too; at 1 to 8 requests the mean change is
within ±0.7 % (single pairs within ±1.6 %), where the activation is 1.8
to 2.4 us of a 23 to 51 us expert block. At 32, 64 and 72 requests the
two pairs disagree in sign (−1.6 / +0.8 % at 32, −0.8 / +3.3 % at 64,
+0.2 / −1.4 % at 72): in the pair whose step reads longer the control
GEMMs, identical cubins in both arms, read 3 to 5 % longer per step (4
to 6 % per layer; one of the four 64-request windows of the patched arms
ran 1.3 ms long), so the step in those cells is inside the pairs' drift,
while the activation's own saving is 1.9 us per layer at 32 and 4.2 us
at 64 (0.8 and 1.5 % of the step) and the unprofiled client step reads
−1.6 % at 32, +0.2 % at 64 and −1.4 % at 72. Read exclusively per MoE
layer, the activation goes from 6.0 to 1.9 us at 64 requests, 8.8 to 2.9
us at 128, 15.1 to 3.8 us at 256 and 823 to 38 us in the 16K prefill
chunk, whose step is 8.3 % shorter (−8.4 and −8.2 %), so the time to
first token of long prompts falls accordingly; the finalize is unchanged
within 0.15 us. The serving cell's step is not a reading: its two
profiled windows per arm differ by 13 to 21 ms with the request mix of
the moment, while its MoE expert block per layer is 22 us shorter.

**At fixed interactivity, measured.** The second table reads the
concurrency the patched build carries at the baseline's step from
measured points, not from the step curve's slope. At 128 requests (39.8
tokens per second per user in the baseline) the patched arm serves 128
requests 1.5 % faster and 144 requests 2.3 % slower than the baseline
serves 128, so the concurrency it carries at the baseline's
interactivity lies between 128 and 144: fewer than 16 more requests
(12.5 %), about 134 (+4.9 %) by linear interpolation between the two
measured patched points. In the context rows, at 256 requests (30.8
tokens per second per user) the patched arm serves 256 requests 2.4 %
faster and 272 requests 3.8 % slower than the baseline serves 256:
between 256 and 272, fewer than 16 more requests (6 %), about 262 (+2.4
%) by interpolation. At 64 requests the patched step is below the
baseline's in one pair (−0.8 %) and above it in the other (+3.3 %, the
pair whose second patched window ran 1.3 ms long), +1.3 % on the mean,
so no gain at fixed interactivity is read there. The table's "tokens per
second at that concurrency" column is the same requests at the shorter
step, a measured lower bound of the gain at the baseline's latency, not
a separate reading. SGLang and the configuration without expert
parallelism follow in the same protocol.

### Scope

- The 32-wide scale block reaches `activation::run()` only through the
standalone activation op (Prims-TS), which builds `activation::Data`
without the row map and whose primary is not a trtllm-gen GEMM; it keeps
the old kernel. The kernel template handles 32-wide blocks and is
instantiated for 128 only.
- The old kernel remains for callers without the row map.

## 🔍 Related Issues

Follows up on #8721 (row-parallel activation and finalize), which is
open and changes the same `activation::run()` path, the same
`activation::Data` fields and the activation selection test. This PR
supersedes its activation part: once this lands, the row-parallel
activation kernel and its 64-token selection rule are not needed, and
#8721 will be rebased onto this branch keeping only its finalize part.

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
`tests/moe/test_trtllm_gen_moe_activation_persistent.py
tests/moe/test_trtllm_gen_fused_moe.py
tests/moe/test_trtllm_gen_fused_moe_routing_renormalize_fp8.py
tests/moe/test_prims_ts_fp8_block_scale_moe.py`

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

- **Where to look first.** The PDL argument in the comment block above
`activationDeepSeekKernelPersistent128`: the kernel reads routing
outputs before `cudaGridDependencySynchronize()`, which is sound only
because GEMM1 waits before it triggers or exits. The new
`FLASHINFER_CHECK` in `csrc/trtllm_batched_gemm_runner.cu` turns that
assumption into a per-launch check on the selected cubin's options.
- **Scope of the check.** It runs for both expert GEMMs (GEMM1 and
GEMM2) on every launch with PDL on, not only for GEMM1, whose property
the activation needs. It is vacuous for a kernel with no grid-dependency
wait and no fine-grained-consumer flag, which `BatchedGemmInterface`
launches in plain stream order. Every kernel of the pinned manifest
waits, and passes.
- **Known cost.** With PDL off the kernel's own time at 2 and 4 tokens,
and at 8 tokens on the sm_107 tray, is 0.1 to 0.3 us above the old
kernel's (the device-side list and lane decision costs one extra memory
round trip when nothing overlaps it). The fused MoE launches the
activation with PDL on, where the whole call is unchanged within noise
or faster (1.00x to 1.04x) at those sizes.
- **Tuning constants.** The fine/coarse crossover (8192 pieces) and the
8 blocks per SM come from measurements on a 148-SM board and were
applied unchanged on the 148-SM B300 node and the 212-SM Rubin tray of
the tables; they were not re-tuned on either.
- **Coverage of the rows list with per-expert controls.** The shared
reference harness (`run_moe_test`) runs with all experts local, where
the kernel takes the pairs list; the new test file therefore carries its
own expert-parallel reference check (the reference computes every expert
and gives the remote ones a routing weight of zero), with and without
SwiGLU controls, next to the standalone harness and the PDL-on/off
bitwise test.
- **Not instantiated.** The kernel template handles the 32-wide scale
block of #8666 but only the 128-wide instantiation is compiled, because
the only caller with 32-wide blocks is the standalone activation op,
which has no row map and keeps the old kernel.
- **Test placement.** The new test reads kernel names from the profiler
(`tests/cake/test_helpers/cake_profiler.py`) because the output tests
cannot distinguish two kernels that write identical bytes.
- **Evidence outside the tree.** The standalone harness behind the
bitwise and kernel-level comparisons and the EP8 timing script behind
the module tables are not part of this PR; the in-tree evidence is the
module-level bitwise comparison, the tests above and the repository
benchmark.
- **End-to-end serving numbers.** Two same-node vLLM pairs on 8x B300
(baseline, then patched, on one exclusive node, twice) are in the
End-to-end section above, with the fixed-interactivity reading taken
from measured points at 72, 144 and 272 requests; the SGLang pair and
the configuration without expert parallelism follow in the same protocol
and will be added here.

AI-assisted.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* Added a persistent activation path for eligible DeepSeek FP8
workloads, with processing adapted to token and expert layouts.

* **Bug Fixes**
* Improved handling of per-expert activation settings and remote-only
routing, including cases with no locally processed tokens.

* **Testing**
* Expanded coverage across token counts, expert layouts, and PDL
settings, including comparisons with reference outputs.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-11-18
**监控日期**: 2026-11-17
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4825
- **最后更新**: 2026-11-17T15:02:25Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-11-18
**监控日期**: 2026-11-17
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34936
- **最后更新**: 2026-11-18T02:00:47Z

## 提交统计

- **昨日提交总数**: 5
- **提交者数量**: 5
- **主要提交者**: Sylvan Liu, yzhautouskay, Sayak Paul

## AI分析总结

# huggingface/diffusers 近期提交分析

## 1. 主要更新类型

本次批次以 **Bug修复与稳定性增强** 为主，兼顾 **功能演进（新缓存机制）**、**硬件兼容性优化** 与 **测试覆盖补充**，属于典型的维护期迭代。

## 2. 关键变更点与项目方向的关系

- **兼容性修复**：移除 Kolors 管线中 `apply_rotary_pos_emb` 上的 `@torch.jit.script`，解决 PyTorch nightly 弃用该装饰器导致的导入失败；另修复 Cosmos3 辅助 FP8 导出 scale 的告警并改用上游共享测试。这体现了 diffusers 作为"多模型、多后端统一分发库"对生态链上游变动的快速响应能力。
- **性能与硬件适配**：在 ROCm gfx1100 上，当跨步 K/V 超出缓存阈值时先复制再调用原生 SDPA，并明确说明低于阈值或未列出架构不复制的原因——针对 AMD GPU 上注意力算子的已知限制做精细化回退策略。
- **缓存架构演进**：为 PAB 与 FasterCache 引入统一的 `cache_context`，并将旧的 `current_timestep_callback` 走弃用路径而非直接删除，同时把相关用例下沉到 cache tester。这与 README 中"提供可组合、可扩展的去噪管线与组件"的目标一致，标志着缓存加速从分散回调走向标准化上下文接口。
- **测试基建**：补充 `BaseOutput` 的不可变性、字段校验与张量检查测试，并按评审采用 `assert_equal` 统一断言，强化输出容器这一公共基类的契约保障。

## 3. 对项目的影响与潜在意义

短期内消除了 Kolors/Cosmos 用户在 nightly 环境下的安装与告警问题；中期看，`cache_context` 的引入为未来更多加速方案（如其他缓存/蒸馏策略）提供了可插拔的统一挂载点，降低新增缓存实现的集成成本；ROCm 修复则扩大了 AMD 平台的可用性，利好跨硬件生态。

## 4. 值得关注的技术点

- **弃用而非删除** 的兼容策略，以及 "preserve deprecated functionality" 与 fix-copies 的提交说明，显示团队在大规模重构中注重向后兼容与文档同步。
- **阈值驱动的条件复制** 设计：只在必要时付出拷贝开销，并对不复制的情形给出可追溯的注释，是性能优化中"最小侵入"的范例。
- 测试向共享基类和统一断言迁移，反映项目在提升测试一致性与可维护性。

## 5. 对项目发展的总体意义

这些提交共同强化了 diffusers 作为生产级扩散模型基础设施的三根支柱：**跨 PyTorch 版本与跨硬件的鲁棒性**、**加速组件的可扩展抽象**、**公共输出与测试契约的可靠性**。在保持新特性（如新缓存机制）迭代的同时严格维护兼容与文档，有助于稳固其在研究与工业部署两端的社区信任，推动项目向更稳定、更易扩展的方向持续演进。

## 详细提交记录

### [e84bda1](https://github.com/huggingface/diffusers/commit/e84bda1c0005da3f48cc4c899635438cb0aa13c1)

- **作者**: klin
- **时间**: 2026-11-17T18:34:19Z
- **提交信息**: [Kolors] Remove @torch.jit.script from apply_rotary_pos_emb (#15316)

[Kolors] remove @torch.jit.script from apply_rotary_pos_emb

torch.jit.script was removed from PyTorch nightly; the decorator made
importing the Kolors pipelines fail.

Signed-off-by: Lin, KuanTing <Kuanting.Lin@amd.com>

### [03f2edc](https://github.com/huggingface/diffusers/commit/03f2edc7ca655870186ff220b691db20def0a42b)

- **作者**: yzhautouskay
- **时间**: 2026-11-17T18:33:47Z
- **提交信息**: Fix: filter Cosmos3 warnings for auxiliary FP8 export scales (#15107)

* Fix Cosmos3 warnings for auxiliary FP8 export scales

* Update Cosmos3 tests to use upstream shared test

### [d9586a3](https://github.com/huggingface/diffusers/commit/d9586a3dc62cce5091bdb7cff981d725f4a6dfe5)

- **作者**: Sayak Paul
- **时间**: 2026-11-17T13:09:16Z
- **提交信息**: feat: implement cache_context for pab and fastercache. (#14900)

* feat: implement cache_context for pab and fastercache.

* deprecate current_timestep_callback instead of removing.

* preserve deprecated functionality.

* up

* propagate to existing tests.

* fix-copies

* move to cache testers.

* pass timestep to cache_context in remaining modular blocks and update cache docs.

### [a4f3082](https://github.com/huggingface/diffusers/commit/a4f3082873d199e352b37329f48ecfd6c4cbf869)

- **作者**: Sylvan Liu
- **时间**: 2026-11-17T12:13:10Z
- **提交信息**: [ROCm] Copy strided K/V before native SDPA on gfx1100 when they exceed the cache (#15291)

* Copy strided K/V before native SDPA on ROCm gfx1100 when they exceed the cache

* Explain why K/V below the threshold or on unlisted architectures are not copied

---------

Co-authored-by: Dhruv Nair <dhruv.nair@gmail.com>

### [865e421](https://github.com/huggingface/diffusers/commit/865e42151a86e911fd141b4e1504f87272c60ea8)

- **作者**: udayraj1238
- **时间**: 2026-11-17T04:38:30Z
- **提交信息**: tests(utils): test BaseOutput immutability, field validation, and tensor checking (#15312)

* tests(utils): test BaseOutput immutability, field validation, and tensor checking

* test(outputs): adopt assert_equal, remove MultiFieldOutput and test_is_tensor per review

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-11-18
**监控日期**: 2026-11-17
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


**报告日期**: 2026-11-18
**监控日期**: 2026-11-17
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13379
- **最后更新**: 2026-11-18T02:26:35Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 2
- **主要提交者**: Hong Zhang, Zhongjie Duan

## AI分析总结

# DiffSynth-Studio 近期提交分析

## 1. 主要更新类型
- **功能新增**：支持 H3 图像训练适配器（training adapter）及最小像素数（min_pixels）配置。
- **Bug 修复**：修复 h3-image-pruned 模型在使用 gc（垃圾回收）时的问题。
- **版本发布**：将版本号更新至 2.2.3，标志着上述变更打包为正式发行版。

## 2. 关键变更点及与项目整体方向的关系
DiffSynth-Studio 是一个面向图像/视频生成模型的统一推理与训练框架，核心价值在于覆盖从低分辨率到高分辨率、从轻量到大规模的多种生成模型（如 H3 系列）。本次提交围绕 **H3 图像模型的训练支持**展开：

- 引入 H3 图像训练适配器，使用户不仅能推理，还能在 H3 图像模型上进行微调训练，补全了"训练—推理"闭环。
- 增加 min_pixels/max_pixels 约束（并保证 max ≥ min），这是扩散模型常见的分辨率控制手段，有助于在不同显存条件下灵活控制生成分辨率，与项目一贯追求的"可扩展、可定制"目标一致。
- 修复 pruned（裁剪版）H3 模型配合 gc 时的异常，确保轻量化部署路径的稳定性。

## 3. 对项目的影响和潜在意义
- **提升 H3 模型的生态完整性**：训练适配器让社区可以基于 H3 做领域微调，增强用户黏性与模型复用性。
- **增强资源适配能力**：像素数控制机制使低显存环境也能参与训练/生成，扩大了受众面。
- **稳定性与发布节奏**：紧随功能合并后即发布 2.2.3，说明团队采用"快速迭代、小步发布"的维护策略，有利于降低升级风险。
- 轻量版模型（pruned）的修复意味着项目对移动端/边缘部署场景的持续关注。

## 4. 值得关注的技术点
- **训练适配器设计模式**：adapter 作为可插拔模块，避免了对主干代码的侵入式修改，值得借鉴其模块化思路。
- **像素数边界校验**（max ≥ min pixels）：体现了对输入参数做防御性校验的良好工程习惯。
- **gc 与 pruned 模型的交互问题**：暗示模型裁剪后可能涉及共享权重或内存释放顺序问题，此类 bug 在量化/裁剪部署中具有普遍参考价值。
- 提交粒度较细、每个 PR 附带清晰的变更说明，协作规范度较高。

## 5. 基于项目背景对发展的影响
结合 README，DiffSynth-Studio 定位为一站式生成模型工作台，本次提交进一步强化了其两大支柱：

- **多模型支持广度**：H3 系列作为重要组成部分，其训练能力的补齐使框架在"全栈支持"叙事上更有说服力，有利于在与同类框架（如 ComfyUI 生态）竞争时形成差异化。
- **版本化交付**：2.2.3 的发布便于下游用户和第三方项目锁定兼容接口，促进生态集成。

总体而言，这批提交属于**功能性增强为主的迭代**，在修复关键部署问题的同时扩展了训练能力，推动项目向"推理与训练并重、轻量与旗舰兼顾"的方向稳步演进。

## 详细提交记录

### [9dde6d1](https://github.com/modelscope/DiffSynth-Studio/commit/9dde6d179fb49f835e8e746b08c2998a2877e5c7)

- **作者**: Zhongjie Duan
- **时间**: 2026-11-17T12:30:23Z
- **提交信息**: update version to 2.2.3 (#1835)

### [9285155](https://github.com/modelscope/DiffSynth-Studio/commit/9285155970e01cd6a0f46f79097c9c12b86e0559)

- **作者**: Hong Zhang
- **时间**: 2026-11-17T11:26:33Z
- **提交信息**: fix h3-image-pruned using gc (#1832)

* support min_pixels & h3-image-training-adapter

* max >= min pixels

* fix h3-image-pruned using gc

### [77fcaf6](https://github.com/modelscope/DiffSynth-Studio/commit/77fcaf62c6c6140c49f5e7f19c1b055165d76e81)

- **作者**: Hong Zhang
- **时间**: 2026-11-17T04:37:19Z
- **提交信息**: support H3 image training adapter (#1827)

* support min_pixels & h3-image-training-adapter

* max >= min pixels

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-11-18
**监控日期**: 2026-11-17
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 38995
- **最后更新**: 2026-11-18T03:38:06Z

## 提交统计

- **昨日提交总数**: 99
- **提交者数量**: 65
- **主要提交者**: Siliang Chen, heziiop, Mick

## AI分析总结

# SGLang 昨日提交总结

## 主要更新

昨日 99 个提交以**功能新增**（约 32 条）、**性能优化**（约 24 条）和 **Bug 修复**（约 32 条）为主，其余为 CI/测试治理、重构与文档更新，整体呈现多硬件平台并行推进、高频活跃的开发状态。

## 关键变更

- **多硬件生态扩张**：AMD 覆盖 gfx942/950/1250，含 AITER 内核、融合 AR+RMSNorm+FP8、custom-all-reduce 重调、HiCache DCP、ModelOpt FP8 等，从"可用"转向"高性能"；NPU/Ascend 持续投入 MindIE 量化注意力、npu graph、可中断 prefill 图、FP8 KV DSA decode 上下文并行与 GLM-5.3-Flash 支持；Intel、MUSA、NVIDIA（DeepGEMM fp8、Hopper indexer）同步推进。
- **投机解码深化**：DFLASH 每请求滑窗草稿 KV 环、置信度调度 compact verify、DSPARK 草稿加速、MTP 状态恢复，持续压低解码延迟。
- **新模型与新架构 Day-0 支持**：Kimi-K3/K3.1、Qwen3.8 Flash Next KV 分片、MiniMax-H3、Ideogram 4、GLM-5.3-Flash、Inkling 2 全套算子栈（FA4 相对偏置 decode、MoE 路由/量化/分组 GEMM、all-reduce 算子）批量交付，验证算子开发流程的标准化。
- **PD 分离与调度打磨**：PD decode 首 token 与首输出合并流式、SPF 共享前缀去重、encoder-replay 行预留、retraction 重引导补测，服务大规模分离式部署。
- **稳定性与内存治理**：GC 冻结堆/空闲冻结与 CUDA graph 捕获交互优化、disaggregation 传输队列轮询、safe_pickle 反序列化安全修复、64 位 token 偏移溢出修复。
- **扩散模型线**：rank-local TP 检查点加载、FLUX.3 像素对齐、Sana VAE、cosmos3 优化，作为并行产品线持续演进。
- **工程化提效**：CI 套件命名统一与非 NV/AMD 硬件门控、Docker 镜像瘦身、依赖治理（ml-dtypes 限 <0.6）、Lamport 逻辑时钟统一重构。

## 项目影响

内存与 GC 系列修复降低长时运行 OOM 风险，提升生产可用性；AMD/NPU/MUSA 补齐增强国产与非 NV 硬件竞争力，扩大部署覆盖面；调度与流式修复改善长上下文场景吞吐与首 token 延迟；CI 治理与安全修复保障长期可维护性与服务端安全。

## 技术关注点

DFLASH 全滑窗 MHA 草稿的 per-request KV ring 设计、GPU heap 冻结与 CUDA graph 捕获的精细显存管理、Engram 表 group_shards 复制换免通信的权衡、Triton 稀疏 MLA 64 位偏移修复、NPU 可中断 prefill 图、Beam search trie head 共享上下文注意力。

## 项目发展方向

结合 README 的"快速推理 LLM 与多模态模型"使命，本日提交在性能内核、新模型覆盖、多后端适配、分离式调度、稳定性治理五个维度同步推进，共同推动 SGLang 向硬件覆盖更广、生产更成熟的高性能推理框架演进。

## 详细提交记录

### [ecd3d75](https://github.com/sgl-project/sglang/commit/ecd3d75a2a790cdb3acba0ecdb4786ff4d4ab25d)

- **作者**: Kaya Emre Arikan
- **时间**: 2026-11-17T23:33:41Z
- **提交信息**: [Fix] diffusion/security: Use safe_pickle_loads for DiffusionServer inbound requests (#49290) (#49290)

### [5830ea8](https://github.com/sgl-project/sglang/commit/5830ea82054517d396573e509ac305e4ed04c83e)

- **作者**: Siliang Chen
- **时间**: 2026-11-17T23:19:10Z
- **提交信息**: [Perf] [AMD] mhc: Enable AITER mHC kernels on gfx942 (#50196)

Co-authored-by: Cursor <cursoragent@cursor.com>

### [7aaebb1](https://github.com/sgl-project/sglang/commit/7aaebb1cf068184fb3b4f86b4ed69a1848a441c9)

- **作者**: shyeh25
- **时间**: 2026-11-17T22:35:53Z
- **提交信息**: [Feat] spec/dflash: Per-request draft KV ring for all-sliding-window MHA drafts (trtllm_mha, fa4) (#50740)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Po-Han Huang <pohanh@nvidia.com>

### [372b350](https://github.com/sgl-project/sglang/commit/372b35034dbf3855044eb9a52a7fa7477c39cc1b)

- **作者**: Yuxuan Zhang
- **时间**: 2026-11-17T21:43:53Z
- **提交信息**: [Fix] disaggregation: Poll the decode transfer queue while retracted requests wait (#50712)

Co-authored-by: Junda Chen <32371474+GindaChen@users.noreply.github.com>
Co-authored-by: Yi Sun <98612013+Boreas618@users.noreply.github.com>
Co-authored-by: Junda Su <90978028+Davids048@users.noreply.github.com>
Co-authored-by: Minshen Zhang <26690162+alexzms@users.noreply.github.com>
Co-authored-by: Shangming Cai <csmthu@gmail.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [1280ff5](https://github.com/sgl-project/sglang/commit/1280ff574b669b4b9f2bda05f5d282dafdcb720e)

- **作者**: Shunkangz
- **时间**: 2026-11-17T21:43:31Z
- **提交信息**: [Feat] CP: Prefill context parallelism for Kimi K3 (#38344)

### [9d9b45d](https://github.com/sgl-project/sglang/commit/9d9b45d413c5185637b88f8ab10ada34ca3fd4ab)

- **作者**: Yihao Wang
- **时间**: 2026-11-17T21:39:24Z
- **提交信息**: [Feat] diffusion: Enable rank-local TP checkpoint loading for MiniMax-H3 (#38766)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [85360aa](https://github.com/sgl-project/sglang/commit/85360aaab8a85f083e7fdd013ba811ba6ecc57d3)

- **作者**: Michael
- **时间**: 2026-11-17T21:33:31Z
- **提交信息**: [Fix] [AMD] monokernels: Keep a draft's forward when it does not meet the spec's hf_config (#50748)

### [4b9f904](https://github.com/sgl-project/sglang/commit/4b9f9043faee0eb8824c47aaaaeee8f29c5af35e)

- **作者**: Jian Chen
- **时间**: 2026-11-17T21:24:29Z
- **提交信息**: [Feat] spec: confidence-scheduled compact verify for DFLASH (#46190)

Co-authored-by: Jian Chen <jic188@ucsd.edu>
Co-authored-by: Qiaolin-Yu <liin1211@outlook.com>

### [1aa45c6](https://github.com/sgl-project/sglang/commit/1aa45c661758b2ff99dc8c57ec849175ab4625ed)

- **作者**: Nan Jiang
- **时间**: 2026-11-17T19:45:00Z
- **提交信息**: [Perf] tokenizer: Return output sampling masks as flat arrays on request (#50126)

### [5cefe8d](https://github.com/sgl-project/sglang/commit/5cefe8de82e1b8b53150306d69e20862848ce4b9)

- **作者**: inkcherry
- **时间**: 2026-11-17T19:40:54Z
- **提交信息**: [Feat] [AMD] moe: Run AITER MegaMoEGfx1250 with the mori dispatch (#48097)

Co-authored-by: Duyi-Wang <duyi.wang@amd.com>

### [b43c4c0](https://github.com/sgl-project/sglang/commit/b43c4c00a64811c05f937724c47ec18f92efd4bb)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-17T19:11:23Z
- **提交信息**: [CI] tests: Register the qknorm rope AMD tests under the renamed JIT stage and cap ml-dtypes on AMD (#51044)

### [31e55a5](https://github.com/sgl-project/sglang/commit/31e55a5120529fb584e6553c3498cfbe93a2cd8a)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-17T18:48:29Z
- **提交信息**: [CI] suites: Unify CI suite and command names, skip instead of fail without run-ci, and share one finish-job check (#50874)

### [9c1b3ec](https://github.com/sgl-project/sglang/commit/9c1b3eceb8d573ab77a9c606cecddc75ef67bf9b)

- **作者**: Vedant V Jhaveri
- **时间**: 2026-11-17T18:45:49Z
- **提交信息**: [Feat] beam-search: Add trie head and shared-context attention (#44349)

### [aa3ccef](https://github.com/sgl-project/sglang/commit/aa3ccefd38c6459aead8fd56dce3047c4f905120)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-17T18:34:03Z
- **提交信息**: [Fix] gc: Warn on frozen garbage instead of reporting a leak (#50983)

### [90121c6](https://github.com/sgl-project/sglang/commit/90121c62a803876a445e95678c2ae88dcac1d0e4)

- **作者**: lishuoshuo-amd
- **时间**: 2026-11-17T18:12:48Z
- **提交信息**: [Fix] mem_cache: Insert the prompt end in the same checkpoint as an SWA branch point (#50059)

### [ba9c86b](https://github.com/sgl-project/sglang/commit/ba9c86bb7eee016a3d5943f4dfe3d8daf0ad7e0a)

- **作者**: Zhenqiang Xu
- **时间**: 2026-11-17T17:04:52Z
- **提交信息**: [Feat] [NPU] diffusion: Integrate MindIE-SD quantized attention into Ascend FA (#46029)

Co-authored-by: zqxu <xuzhenqiang3@huawei.com>
Co-authored-by: Артем Савкин <58187114+OrangeRedeng@users.noreply.github.com>

### [db12772](https://github.com/sgl-project/sglang/commit/db12772f0cb7b7341f3902d7d7cae0bd280c2cc2)

- **作者**: Shuwen Wang
- **时间**: 2026-11-17T16:38:04Z
- **提交信息**: [Fix] unified_cache: Restore Inkling MTP draft state in the direct external linker (#47293)

### [b2cc023](https://github.com/sgl-project/sglang/commit/b2cc023f23e14e6482490238968e018573847d0c)

- **作者**: Zhangheng
- **时间**: 2026-11-17T13:53:57Z
- **提交信息**: [Chore] mem_cache: Add UMBP code owners (#51021)

### [703e763](https://github.com/sgl-project/sglang/commit/703e763d5f3af75ea3587275d79155c28d3c5d4f)

- **作者**: fengshaoyi-amd
- **时间**: 2026-11-17T11:19:50Z
- **提交信息**: [Perf] [AMD] qwen3: Fuse prefill QK-norm + RoPE on ROCm with the JIT qknorm_rope kernel (#47052)

Co-authored-by: BBuf <35585791+BBuf@users.noreply.github.com>

### [39af8b1](https://github.com/sgl-project/sglang/commit/39af8b1211791c9e6936afad499b01f36ecc4b9c)

- **作者**: Lee Nau
- **时间**: 2026-11-17T11:08:18Z
- **提交信息**: [Doc] cookbook: Use the nemotron_3 reasoning parser for Nemotron 3 Nano Omni (#50815)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [513e44c](https://github.com/sgl-project/sglang/commit/513e44c89c2e9982516762bea71d7015660467f3)

- **作者**: shun8686
- **时间**: 2026-11-17T10:51:09Z
- **提交信息**: [CI] [NPU] test: Optimized the multi-node e2e test method (#50969)

Co-authored-by: sglang-npu-bot <sglangnpu@163.com>

### [c02b04f](https://github.com/sgl-project/sglang/commit/c02b04fb50bf5a57ba528d1bfe7d109d16d4c690)

- **作者**: Baizhou Zhang
- **时间**: 2026-11-17T10:11:04Z
- **提交信息**: [Fix] disaggregation: Set aux-exchange and deferred-ACK fields on the KV-shard CP-TP test manager (#50995)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [4469f9f](https://github.com/sgl-project/sglang/commit/4469f9fc7fa0a7efd0758e44f288e1af8ad1c0a7)

- **作者**: dorado269
- **时间**: 2026-11-17T10:03:38Z
- **提交信息**: [Fix] [AMD] mla: Bound absorb-BMM wave budget (follow-up to #46918) (#49732)

Signed-off-by: yihou <yihou@amd.com>
Co-authored-by: 璒瑜 <liudengpan.ldp@alibaba-inc.com>
Co-authored-by: Kevin Mi <mikevin920@yahoo.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [b8555f9](https://github.com/sgl-project/sglang/commit/b8555f91bbb83f4d3117b5161317760e0055c7a5)

- **作者**: Baizhou Zhang
- **时间**: 2026-11-17T09:58:48Z
- **提交信息**: [CI] docker: Drop sgl-fa3 from the CUDA 13.4 image (#50994)

### [eade493](https://github.com/sgl-project/sglang/commit/eade493029f0caf6f3e6616be2497dbc7d7bac8c)

- **作者**: jiaqiang-dot-liu
- **时间**: 2026-11-17T09:50:02Z
- **提交信息**: [Perf] [AMD] gemm: K-start rotation and a flat partial sum for the BF16 row-major small-M GEMM (#50686)

Co-authored-by: jiaqiang-dot-liu <295720280+jiaqiang-dot-liu@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [9fd8b7f](https://github.com/sgl-project/sglang/commit/9fd8b7fef22505895eb43282faf6962d73afbc75)

- **作者**: Chen Cheng
- **时间**: 2026-11-17T09:48:35Z
- **提交信息**: [Perf] [NVIDIA] dsv4: Score the V4.1 prefill indexer with DeepGEMM fp8 MQA logits on Hopper (#50719)

### [b2fc126](https://github.com/sgl-project/sglang/commit/b2fc1268302b0083b59e377d1491864567e897c6)

- **作者**: DarkSharpness
- **时间**: 2026-11-17T09:42:39Z
- **提交信息**: [Test] kernels: Remove input-rejection cases that only test generic argument checking (#50824)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [9158db2](https://github.com/sgl-project/sglang/commit/9158db2b97d9b4aef2ae2adba4ccb0eef2b6f843)

- **作者**: inkcherry
- **时间**: 2026-11-17T09:24:11Z
- **提交信息**: [Perf] [AMD] dspark: Speed up the DSPARK draft step (#48095)

Co-authored-by: Duyi-Wang <duyi.wang@amd.com>

### [8241f8e](https://github.com/sgl-project/sglang/commit/8241f8e6f6667920fdde3207365bbd2222fdc37f)

- **作者**: Han-Yin Chang
- **时间**: 2026-11-17T09:11:35Z
- **提交信息**: [Fix] diffusion: Align Ideogram 4 request sizes to the 16-pixel patch grid (#50640)

Signed-off-by: Han-Yin Chang <nick20350@gmail.com>

### [c67db7c](https://github.com/sgl-project/sglang/commit/c67db7c76280986ee936af4b3a1019397b0c285e)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-17T08:59:44Z
- **提交信息**: [Fix] cuda-graph: Free the old decode graphs before a recapture (#50982)

### [7e2d9b8](https://github.com/sgl-project/sglang/commit/7e2d9b85a3941ef87ee36e737340ba3e080c9696)

- **作者**: inkcherry
- **时间**: 2026-11-17T08:58:32Z
- **提交信息**: [Fix] [AMD] dsv4: Fix the mHC weight orientation across layer boundaries (#48065)

Co-authored-by: Duyi-Wang <duyi.wang@amd.com>

### [d1e7987](https://github.com/sgl-project/sglang/commit/d1e7987757f7ea5c29d7d53402daf30d9a7b85fe)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-17T08:55:42Z
- **提交信息**: [Fix] gc: Keep the heap frozen after a CUDA graph capture (#50981)

### [cc70547](https://github.com/sgl-project/sglang/commit/cc7054723b25488962b80d1572099531a8567748)

- **作者**: heziiop
- **时间**: 2026-11-17T08:54:07Z
- **提交信息**: [Fix] [NPU] distributed: Avoid NVML queries in multimem initialization (#50744)

### [f549aa8](https://github.com/sgl-project/sglang/commit/f549aa8b7b921f7540583b814becd5f0c8175d31)

- **作者**: sushil Dubey
- **时间**: 2026-11-17T08:52:58Z
- **提交信息**: [Perf] [AMD] qwen3_5: use strided GDN prefill projection views on HIP (#41683)

Co-authored-by: Sushil Dubey <susdubey@amd.com>
Co-authored-by: jacky.cheng <yichiche@amd.com>

### [09185be](https://github.com/sgl-project/sglang/commit/09185be8f9d1368a0d628c681ca50c84d847d38f)

- **作者**: Shunkangz
- **时间**: 2026-11-17T08:52:54Z
- **提交信息**: [Feat] KVShard: Enable KV cache sharding for Qwen3.8 Flash Next (#44447)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [47dbe17](https://github.com/sgl-project/sglang/commit/47dbe1702cd13164857bb834ea8332dd6392465a)

- **作者**: 黄孝君
- **时间**: 2026-11-17T08:49:25Z
- **提交信息**: [CI] npu: Update SGLANG_KERNEL_NPU_TAG to 2026.11.0.post6 (#50884)

### [4e07dc8](https://github.com/sgl-project/sglang/commit/4e07dc8aa1e5b563d9aa113bd453c1ff548e4467)

- **作者**: yuchengliu1
- **时间**: 2026-11-17T08:46:46Z
- **提交信息**: [Feat] benchmark: add rerank benchmark client (#47854)

Co-authored-by: Ma Mingfei <mingfei.ma@intel.com>

### [8d07d63](https://github.com/sgl-project/sglang/commit/8d07d63f3798ccf41990f0d1e9e2720afa1908d2)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-17T08:45:46Z
- **提交信息**: [Fix] gc: Collect before freezing the heap (#50980)

### [87f393c](https://github.com/sgl-project/sglang/commit/87f393c249290d53fc18d96c81df02f7311796f4)

- **作者**: inkcherry
- **时间**: 2026-11-17T08:44:57Z
- **提交信息**: [Perf] [AMD] dsv4: aiter sparse prefill, fp8 wo_a and mxfp8_128 GEMM (#48064)

Co-authored-by: kawhil-amd <kawhil-amd@users.noreply.github.com>
Co-authored-by: Duyi-Wang <duyi.wang@amd.com>
Co-authored-by: HAI <hixiao@gmail.com>

### [ced0383](https://github.com/sgl-project/sglang/commit/ced03834827d6a33847c99b5aee927e46d3bef57)

- **作者**: wl55721
- **时间**: 2026-11-17T08:38:19Z
- **提交信息**: [Feat] [NPU] layernorm-sp: Support sequence parallel on NPU (#41496)

### [cb08ff1](https://github.com/sgl-project/sglang/commit/cb08ff1b9da13522cc037d6b94de2e2eb1abdcb2)

- **作者**: ming_wang
- **时间**: 2026-11-17T08:36:19Z
- **提交信息**: [Feat] [NPU] hicache: back hugepage host pools with the mmap allocator (#50676)

### [3400b40](https://github.com/sgl-project/sglang/commit/3400b40b343e390db91cf565868d7953ca34cf7d)

- **作者**: Артем Савкин
- **时间**: 2026-11-17T08:35:58Z
- **提交信息**: [Perf] [NPU] MiniMax-H3: optimize RMSNorm and SwiGLU (#49353)

### [5dd0c10](https://github.com/sgl-project/sglang/commit/5dd0c10e33b4f6bd473a4a06f9cb25c3cc8bcde0)

- **作者**: ZY Y
- **时间**: 2026-11-17T08:25:36Z
- **提交信息**: [Test] [NPU] deepseek-v4: Enable DSPARK on PD prefill and add off-CP / off-DSPARK testcases (#50925)

### [fbdad02](https://github.com/sgl-project/sglang/commit/fbdad0224aabf53faa923b238a719e771b3095c8)

- **作者**: Arseniy Mironov
- **时间**: 2026-11-17T08:17:19Z
- **提交信息**: [Fix] [NPU] diffusion: MiniMax-H3 crashes with mxfp8 quantization or ref2va configuration (#50117)

Co-authored-by: Артем Савкин <58187114+OrangeRedeng@users.noreply.github.com>

### [ba93265](https://github.com/sgl-project/sglang/commit/ba9326548741a155ba92b1b20f12cfbaf1a1a613)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-17T08:16:45Z
- **提交信息**: [CI] hardware: Gate non-NV/AMD hardware CI behind `run-ci-<hw>-extra` labels (#50872)

### [435ee28](https://github.com/sgl-project/sglang/commit/435ee288edbda6d4522ff2bae2fe33f82a3fd1ea)

- **作者**: Chunyuan WU
- **时间**: 2026-11-17T08:11:24Z
- **提交信息**: [Perf] [Intel] dp: Routes all_gather_into_tensor and reduce_scatter_tensor to shm kernels (#41521)

### [9eb23a3](https://github.com/sgl-project/sglang/commit/9eb23a3e63d6da37ccb418558904c336f762ac39)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-17T08:10:00Z
- **提交信息**: [Feat] gc: Add idle freeze and checks for heap growth and frozen garbage (#50883)

### [4009bc1](https://github.com/sgl-project/sglang/commit/4009bc1be59f0d6be9d0a1be1b23894c09524d0e)

- **作者**: Michael
- **时间**: 2026-11-17T08:08:35Z
- **提交信息**: [CI] [AMD] nightly-benchmark: Run InferenceX's AgentX Muse Spark Open MXFP4 DFlash2 curve on MI35x (#50747)

### [2e07b70](https://github.com/sgl-project/sglang/commit/2e07b70e50b46e14f6f444e82f9feb67793e8cdf)

- **作者**: Mick
- **时间**: 2026-11-17T07:59:21Z
- **提交信息**: [Doc] diffusion: update logo (#50960)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>

### [e55e2ee](https://github.com/sgl-project/sglang/commit/e55e2eeb1f49dc3d48f260ff44d7d172f6521aeb)

- **作者**: guanam
- **时间**: 2026-11-17T07:49:44Z
- **提交信息**: [Feat] [NPU] graph: Compile decode graphs with npugraph_ex and optional static kernels (#49999)

### [22df117](https://github.com/sgl-project/sglang/commit/22df117a991cd418aa05448362f7976df86ea5f6)

- **作者**: wzrd
- **时间**: 2026-11-17T07:37:19Z
- **提交信息**: [Test] [NPU] rl: Add P0 RLHF lifecycle coverage (#49289)

Signed-off-by: wzrd <floatlibai@gmail.com>

### [b5a4fca](https://github.com/sgl-project/sglang/commit/b5a4fca3a6c81908af00e9ea3a82a973ac373f94)

- **作者**: kangwangamd
- **时间**: 2026-11-17T07:33:34Z
- **提交信息**: [Chore] [AMD] aiter: Bump the gfx942/gfx950 pin to 581579ab5 (#50759)

Co-authored-by: Wang, KangLin (Colin) <kanglin.wang@amd.com>

### [6321f71](https://github.com/sgl-project/sglang/commit/6321f714ddd9c5da511b0cfefa0ebabc4277cf36)

- **作者**: sglang-bot
- **时间**: 2026-11-17T07:32:56Z
- **提交信息**: [Feat] kimi_k3: Merge the rest of the Kimi-K3.1 Day-0 branch (#48414)

Co-authored-by: sglang-bot <232288953+sglang-bot@users.noreply.github.com>
Co-authored-by: Yuhao Yang <47235274+yhyang201@users.noreply.github.com>
Co-authored-by: Khoa Pham <khoa.pham@radixark.ai>
Co-authored-by: Baizhou Zhang <sobereddiezhang@gmail.com>
Co-authored-by: Shuwen Wang <47200617+alphabetc1@users.noreply.github.com>
Co-authored-by: Po-Han Huang <53919306+nvpohanh@users.noreply.github.com>
Co-authored-by: StarDuster <7328584+StarDuster@users.noreply.github.com>
Co-authored-by: Yuwei An <ayw.sirius19@gmail.com>
Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>
Co-authored-by: Chunan Zeng <zcnrex@gmail.com>
Co-authored-by: Mao Cheng <35615230+maocheng23@users.noreply.github.com>
Co-authored-by: Ziyi Xu <76582120+DarkSharpness@users.noreply.github.com>
Co-authored-by: Nitin Sai Bommi <227267412+nbommi19@users.noreply.github.com>
Co-authored-by: Kurt Shuster <kurt@thinkingmachines.ai>
Co-authored-by: akhilg-nv <165961486+akhilg-nv@users.noreply.github.com>
Co-authored-by: hnyls2002 <lsyincs@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Po-Han Huang <pohanh@nvidia.com>
Co-authored-by: Liangsheng Yin <hnyls2002@gmail.com>

### [f74df0c](https://github.com/sgl-project/sglang/commit/f74df0c3d688ca21e3a4eafd62f908a59dcbc610)

- **作者**: Yuxuan Zhang
- **时间**: 2026-11-17T07:27:26Z
- **提交信息**: [Fix] scheduler: Wait for the launched forward before writing weights (#50717)

Co-authored-by: Junda Chen <32371474+GindaChen@users.noreply.github.com>
Co-authored-by: Yi Sun <98612013+Boreas618@users.noreply.github.com>
Co-authored-by: Junda Su <90978028+Davids048@users.noreply.github.com>
Co-authored-by: Minshen Zhang <26690162+alexzms@users.noreply.github.com>

### [d766b73](https://github.com/sgl-project/sglang/commit/d766b7327e1bcac165be15664e0c9c8b7f60326c)

- **作者**: LI MOU
- **时间**: 2026-11-17T07:21:40Z
- **提交信息**: [Doc] [AMD] dsv41: Add MI355X DP attention agentic recipes for concurrency 128 and 256 (#50677)

Co-authored-by: LI MOU <lxglbk@gmail.com>

### [8e737da](https://github.com/sgl-project/sglang/commit/8e737da037ddf967d9b1bab778f48fb35275d7ee)

- **作者**: Yihao Wang
- **时间**: 2026-11-17T07:08:10Z
- **提交信息**: [Refactor] diffusion: Remove dead code in entrypoints, managers and server args (#49840)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [2d8e368](https://github.com/sgl-project/sglang/commit/2d8e3681dc47961e1fccd3b2a07755512af8dea6)

- **作者**: Mick
- **时间**: 2026-11-17T07:05:34Z
- **提交信息**: [Doc] diffusion: Show the logo on the docs and cookbook landing pages (#50867)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>

### [56d5f6c](https://github.com/sgl-project/sglang/commit/56d5f6cb71aca814939e3b62d47fe1b1f53702e9)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-17T07:01:35Z
- **提交信息**: [Fix] gemma4: Feed the AR fusion test's DeepGEMM UE8M0 weight scales on Blackwell (#50941)

### [eef4271](https://github.com/sgl-project/sglang/commit/eef42710c4507a506bba4a16d473e10c120e3f7c)

- **作者**: 钱瑞源
- **时间**: 2026-11-17T06:09:25Z
- **提交信息**: [Feat] [NPU] Qwen3.8-Flash-Next: Support graph replay, MTP, and Triton kernels (#37570)

### [ddb0129](https://github.com/sgl-project/sglang/commit/ddb012983188bdafd5ab5c2b41ee8ba151590bcd)

- **作者**: Michael
- **时间**: 2026-11-17T06:09:07Z
- **提交信息**: [CI] [AMD] deepseek-r1: Align the MI35x MXFP4 TP4 MTP GSM8K gate with the non-MTP test (#49384)

### [b743e77](https://github.com/sgl-project/sglang/commit/b743e776abcb5ac0dd8b001f98148ae71da9ce5b)

- **作者**: Xuanyi Li
- **时间**: 2026-11-17T05:58:48Z
- **提交信息**: [Fix] kda: Align unfused safe-gate diagonal normalization anchor (#48745)

### [d8a6e5a](https://github.com/sgl-project/sglang/commit/d8a6e5a9deddfc92d1b0d21aeb7bed743f0a3e4e)

- **作者**: yz-wqf
- **时间**: 2026-11-17T05:58:31Z
- **提交信息**: [Fix] [NVIDIA] mega_moe: Stop DeepGEMM's MLOPart helper before every KV cache sizing (#50771)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [837d1cf](https://github.com/sgl-project/sglang/commit/837d1cf76e8be89608bef613a3a5de0e3d16d658)

- **作者**: Po-Han Huang (NVIDIA)
- **时间**: 2026-11-17T05:58:16Z
- **提交信息**: [Perf] tokenizer_manager: Poll client disconnects once per wait timeout, not per streamed chunk (#50741)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [471ae1b](https://github.com/sgl-project/sglang/commit/471ae1b32c44d630d23a984597280e9516866513)

- **作者**: Ke Bao
- **时间**: 2026-11-17T05:42:47Z
- **提交信息**: [Feat] fa4: Add the relative-bias decode kernel for Inkling 2 (#50523)

Co-authored-by: Chunan Zeng <zcnrex@gmail.com>
Co-authored-by: Cheng Wan <54331508+ch-wan@users.noreply.github.com>
Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>

### [41419ca](https://github.com/sgl-project/sglang/commit/41419ca900076988dc9332f4cb7896ffbbb3aa2e)

- **作者**: Ke Bao
- **时间**: 2026-11-17T05:42:18Z
- **提交信息**: [Feat] inkling2: Add MoE routing, quantization and grouped GEMM kernels (#50525)

Co-authored-by: Chunan Zeng <zcnrex@gmail.com>
Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>

### [bb477b2](https://github.com/sgl-project/sglang/commit/bb477b230b373dbc42971dbbc58b231270496c89)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-17T05:25:59Z
- **提交信息**: [CI] deps: Cap ml-dtypes below 0.6 with the lmms_eval install (#50940)

### [6795aed](https://github.com/sgl-project/sglang/commit/6795aed9755ece703d226063155fcf8ef7c5f150)

- **作者**: weireweire
- **时间**: 2026-11-17T05:23:17Z
- **提交信息**: [Perf] disaggregation: Stream a PD decode request's first token with its first decode output (#50895)

Co-authored-by: weireweire <20922698+weireweire@users.noreply.github.com>

### [a27a59c](https://github.com/sgl-project/sglang/commit/a27a59c2e73be3c44d479d9c15e168ff029c97b8)

- **作者**: weireweire
- **时间**: 2026-11-17T05:22:50Z
- **提交信息**: [Perf] dsv41: Share Engram tables across servers with replication group_shards (#50471)

Signed-off-by: weireweire <20922698+weireweire@users.noreply.github.com>
Co-authored-by: weireweire <20922698+weireweire@users.noreply.github.com>
Co-authored-by: Po-Han Huang <pohanh@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [a0d169e](https://github.com/sgl-project/sglang/commit/a0d169e8d0836600c409a721fec36545591845d9)

- **作者**: DarkSharpness
- **时间**: 2026-11-17T05:17:32Z
- **提交信息**: [Refactor] comm: Route the remaining inline Lamport markers through LamportTrait (#50764)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [04f3bb4](https://github.com/sgl-project/sglang/commit/04f3bb4678b2256a21aaed98ac5e513853fd44b8)

- **作者**: jiaqiang-dot-liu
- **时间**: 2026-11-17T05:17:17Z
- **提交信息**: [Perf] [AMD] moe: Run the Qwen3.5 small-M fused router on gfx942 (#50504)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [3da953f](https://github.com/sgl-project/sglang/commit/3da953fab51434a1835e42791a10877208300c15)

- **作者**: jiaqiang-dot-liu
- **时间**: 2026-11-17T05:16:59Z
- **提交信息**: [Perf] [AMD] qwen3.5: Route the 512-expert softmax router through aiter topk_gating on gfx942 (#50503)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [7fb3ccb](https://github.com/sgl-project/sglang/commit/7fb3ccb5d205831d0d5f03f597b7dbdc2446d68d)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-17T05:05:03Z
- **提交信息**: [Fix] hisparse: Give the plain pool fake in the retraction test the allocator's state field (#50937)

### [83c2c71](https://github.com/sgl-project/sglang/commit/83c2c71774108e4dfa2bbabe9ec2695fbeda1af6)

- **作者**: Shash Bhaskar
- **时间**: 2026-11-17T04:55:55Z
- **提交信息**: [CI] wait-for-jobs: Retry transient GitHub API errors (#42806)

Co-authored-by: shashb27 <shashb27@users.noreply.github.com>

### [5b35f1b](https://github.com/sgl-project/sglang/commit/5b35f1badbd6e546e372ce61f9e41378b60003ed)

- **作者**: qiuhongchen
- **时间**: 2026-11-17T04:45:47Z
- **提交信息**: [Feat] [NPU] glm5: Support GLM-5.3-Flash on Ascend A3/A5 (#43305)

Signed-off-by: IceShip <chenqiuhong45@gmail.com>
Co-authored-by: stellaxcpeng <xp009228@gmail.com>
Co-authored-by: Even Zhou <even.y.zhou@outlook.com>

### [d08d159](https://github.com/sgl-project/sglang/commit/d08d15985b731db38824d7297b37cf1265e030b1)

- **作者**: R0CKSTAR
- **时间**: 2026-11-17T04:06:03Z
- **提交信息**: [Fix] [MUSA] sgl-kernel: Restore the MUSA AOT wheel build (#50486)

### [f534dba](https://github.com/sgl-project/sglang/commit/f534dbaeb2d07c67951d905c628d2888e1ca1673)

- **作者**: qiye
- **时间**: 2026-11-17T02:39:52Z
- **提交信息**: [Test] hisparse: Cover the PD decode retraction rebootstrap path (#40732)

Signed-off-by: Jianliang Qi <jianliang5669@gmail.com>
Co-authored-by: huangtingwei <huangtingwei9988@gmail.com>

### [0e8c255](https://github.com/sgl-project/sglang/commit/0e8c25511701f7303e8d9a29c2d4d5a35a5ab7cc)

- **作者**: akhilg-nv
- **时间**: 2026-11-17T02:05:46Z
- **提交信息**: [Fix] scheduler: Dedupe shared prefixes in shortest-first order under SPF (#46022)

### [0bf51f9](https://github.com/sgl-project/sglang/commit/0bf51f9d0b49c0f1e6e4e0e08ff770cc88f7a50b)

- **作者**: Tri Dao
- **时间**: 2026-11-17T01:55:27Z
- **提交信息**: [Fix] kimi-k3: Handle idle attention-DP ranks and match the KDA checkpoint dtype (#50839)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: kpham-sgl <khoa.pham@radixark.ai>

### [4aef4d6](https://github.com/sgl-project/sglang/commit/4aef4d60e35631faddbf63bfbe3b8e1a62eb0483)

- **作者**: hanwlax
- **时间**: 2026-11-17T01:54:19Z
- **提交信息**: [Fix] [NPU] kda: Fix Ascend prefill crash due to missing kernel flag (#50725)

### [9e14a21](https://github.com/sgl-project/sglang/commit/9e14a219404c8c8425fe4669b0fa23c275dd81ed)

- **作者**: qyb233
- **时间**: 2026-11-17T01:52:08Z
- **提交信息**: [Feat] [NPU] attention: Support FP8 KV for DSA decode context parallelism (#50097)

### [988b043](https://github.com/sgl-project/sglang/commit/988b043982c5270cfbf4d6a17bc9df245dd0f039)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-17T01:50:29Z
- **提交信息**: [Feat] gc: Log GC passes and long-GC warnings in every server process (#50882)

### [9bf6da2](https://github.com/sgl-project/sglang/commit/9bf6da221410faef571d6e952a2b4bbb36383e5a)

- **作者**: akhilg-nv
- **时间**: 2026-11-17T01:48:35Z
- **提交信息**: [Fix] scheduler: Reserve encoder-replay rows in the shortest-prefill-first chunk reservation (#46063)

### [00db5b7](https://github.com/sgl-project/sglang/commit/00db5b72e3adf268c30f7f68aad4c70acce40313)

- **作者**: amote-i
- **时间**: 2026-11-17T01:46:14Z
- **提交信息**: [Fix] multimodal: Match CUDA tensors by device type for cuda-only gpu_tensors_blake3 kernel (#50470)

### [2a71304](https://github.com/sgl-project/sglang/commit/2a71304ac55fd8398834be2fad157403a7dcdc3d)

- **作者**: Rio
- **时间**: 2026-11-17T01:33:16Z
- **提交信息**: [Feat] [NPU] prefill: breakable prefill graph for DSV4 and ascend_ops MoE (#49481)

Co-authored-by: kyrotiko <yy417168602@gmail.com>

### [70b34f3](https://github.com/sgl-project/sglang/commit/70b34f322a911f5534a683e7f84a1c4a6939d660)

- **作者**: Ke Bao
- **时间**: 2026-11-17T01:27:31Z
- **提交信息**: [Feat] inkling2: Add dense-path kernels (#50524)

Co-authored-by: Chunan Zeng <zcnrex@gmail.com>
Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>

### [98c45e1](https://github.com/sgl-project/sglang/commit/98c45e11c4f401d823ae0a1d1bb40aed3bdf3c5f)

- **作者**: Ke Bao
- **时间**: 2026-11-17T01:26:53Z
- **提交信息**: [Feat] inkling2: Add all-reduce and exchange kernels (#50526)

Co-authored-by: Chunan Zeng <zcnrex@gmail.com>
Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>

### [e4d84dc](https://github.com/sgl-project/sglang/commit/e4d84dca71553b9f36909ac9f77164861d46c8cd)

- **作者**: Clint
- **时间**: 2026-11-17T01:15:14Z
- **提交信息**: [Fix] [AMD] dsa: Use 64-bit token offsets in the Triton sparse MLA kernels (#50870)

Co-authored-by: clintg6 <7388379+clintg6@users.noreply.github.com>

### [6c9a193](https://github.com/sgl-project/sglang/commit/6c9a1938d033d532e66cb41a95e9047819296ee4)

- **作者**: jiaqiang-dot-liu
- **时间**: 2026-11-17T00:58:05Z
- **提交信息**: [Perf] [AMD] distributed: Run the fused AR + RMSNorm + per-group FP8 quant on gfx942 (#49884)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [04af670](https://github.com/sgl-project/sglang/commit/04af670a31bafbd6f25c5e69c745885d2bd595aa)

- **作者**: Zheng Gong
- **时间**: 2026-11-17T00:57:54Z
- **提交信息**: [Perf] [AMD] deepseek-v4.1: Build the low-ratio extend slot gather once per forward, without a host sync (#50512)

Signed-off-by: Zheng Gong <zgong@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [2123631](https://github.com/sgl-project/sglang/commit/2123631e0eb051f788b63ff22a982c078346da71)

- **作者**: Han-Yin Chang
- **时间**: 2026-11-17T00:57:48Z
- **提交信息**: [Fix] diffusion: Align FLUX.3 request sizes to the 16-pixel latent grid (#50638)

Signed-off-by: Han-Yin Chang <nick20350@gmail.com>

### [3797ca3](https://github.com/sgl-project/sglang/commit/3797ca3b1cdb123e6be460b3ccf8571281b68490)

- **作者**: Emma Yang
- **时间**: 2026-11-17T00:57:34Z
- **提交信息**: [Fix] diffusion/sana: Honor --vae-tiling in the AutoencoderDC VAE (#34514)

Co-authored-by: mickqian <mickqian@users.noreply.github.com>
Co-authored-by: Mick <mickjagger19@icloud.com>
Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

### [b097614](https://github.com/sgl-project/sglang/commit/b097614b25466be3bd2fd509dc70e836918846c3)

- **作者**: Eric.Chin.AMD
- **时间**: 2026-11-17T00:55:33Z
- **提交信息**: [Feat] [AMD] hicache: Enable HiCache for DSA DCP with a packed MTP draft (#45205)

Co-authored-by: Thomas Wang <thomawan@amd.com>

### [2adf75f](https://github.com/sgl-project/sglang/commit/2adf75fec6240ab02bfb54908b45a5c74578a062)

- **作者**: Hubert Lu
- **时间**: 2026-11-17T00:45:47Z
- **提交信息**: [Perf] [AMD] custom-all-reduce: Drop the gfx1250 2shot_push clamp and retune carv2 (#50656)

### [d79c53c](https://github.com/sgl-project/sglang/commit/d79c53ca37274fbd860339f2b055d9c26b52c688)

- **作者**: Mick
- **时间**: 2026-11-17T00:20:38Z
- **提交信息**: [Doc] diffusion: Include action generation across public entry points (#50868)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [25c1c43](https://github.com/sgl-project/sglang/commit/25c1c439424d0d781d409c462e944cf6197b250c)

- **作者**: Pinjie Xu
- **时间**: 2026-11-17T00:13:17Z
- **提交信息**: [Perf] diffusion/cosmos3: opt sm120 gemm performance on bimanual (#50765)

### [68aeb0d](https://github.com/sgl-project/sglang/commit/68aeb0dc0a0bee696976376f5f5f33214b70f9d9)

- **作者**: Yichi Zhang
- **时间**: 2026-11-17T00:12:10Z
- **提交信息**: [Feat] cli: Edit the whole Guide command in your editor (#50733)

### [1a86ab4](https://github.com/sgl-project/sglang/commit/1a86ab49e71576c9a1069d47f5c82b2185344d18)

- **作者**: Lee Nau
- **时间**: 2026-11-17T00:10:32Z
- **提交信息**: [CI] openai_server: Sample greedily in the streaming tool-call args test (#50825)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [0596e4d](https://github.com/sgl-project/sglang/commit/0596e4d77582f80c6a02ba3fe5a876f088c78761)

- **作者**: Xinyu Jiang
- **时间**: 2026-11-17T00:06:46Z
- **提交信息**: [Fix] [AMD] inkling: Initialize Inkling safely on ROCm (#41928)

Co-authored-by: Jiajun Li <guapisolo@gmail.com>
Co-authored-by: Zhiyao Jiang <jessicajiang324@gmail.com>
Co-authored-by: HAI <hixiao@gmail.com>

### [4fb2069](https://github.com/sgl-project/sglang/commit/4fb20694be146bdf300059406affcce7fe804159)

- **作者**: Xinyu Jiang
- **时间**: 2026-11-17T00:03:02Z
- **提交信息**: [Fix] [AMD] modelopt: Support ModelOpt FP8 Nemotron models on gfx950 (#48089)

Co-authored-by: Zhiyao Jiang <jessicajiang324@gmail.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-11-18
**监控日期**: 2026-11-17
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for 100+ DiTs.
- **语言**: Python
- **星标数**: 1308
- **最后更新**: 2026-11-15T22:07:40Z

## 提交统计

- **昨日提交总数**: 7
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

# vipshop/cache-dit 昨日提交分析（批次 1/1，7 条提交）

## 1. 主要更新类型
- **性能优化**（4 条）：SVDQ（SVD 量化）CuTe 融合 MLP/SwiGLU 链路、NVFP4 运行时的 GEMM/epilogue 优化、fc2 路径特化。
- **功能新增**（1 条）：新 SVD-Cache 校准器（calibrator）及统一的校准器 CLI 选型机制。
- **Bug 修复**（1 条）：PSNR 指标计算中 uint8 溢出导致的严重虚高。
- **文档/工程化**（1 条为主，含多次补充）：新增缓存算法集成的 agent skill，覆盖论文评估、落地路径与验收门禁。

## 2. 关键变更点与项目方向的关系
项目目标是做 **PyTorch 原生的 DiT 推理引擎，核心能力 = Cache + 并行 + 量化 + CPU offload**。本批提交正好对应两大主线：

- **量化主线（svdq）**：从 #1332 引入 CuTe 上的融合 MLP/SwiGLU，到 #1343 优化融合链路（量化存储向量化配对、D epilogue 的 B 操作数加载流水化、融合 GEMM 拆分并做 `kFuseDown` 特化），再到 #1344 给 fc2 增加几何门控的纯 G2R 大 K 行主序路径。三条提交层层递进，把 full-M fc2 推到原生实现的 0.948x/0.965x（M=4096/8192），并用强制 TMA 基准保留对照。
- **缓存主线（cache）**：#1338 先建立缓存算法的三轴分解框架（skip 时机/粒度/替换算子）与五个验收门禁；#1340 据此落地 SVD-Cache（token×channel 低秩拆分、在线拟合、推理期冻结，提供 ema/taylor 两个预测器），同时统一 `--calibrator` 接口并保留旧别名；#1342 记录其"**实现成功但收益为负**"的结论。
- **正确性**：#1335 修复 PSNR 的 uint8 回绕（虚高 5–21 dB），#1338 进一步澄清 PSNR 的 float[0,1] 输入仍会虚高 48.13 dB，形成"修 bug → 更新说明"的闭环。

## 3. 对项目的影响与潜在意义
- **性能**：量化融合链路逼近原生速度，直接提升 DiT 推理吞吐，是引擎核心卖点之一。
- **工程可扩展性**：新增的 cache-integration skill 使未来引入新缓存论文时无需重新推导项目架构，显著降低新算法评估与落地成本——这对快速跟进前沿缓存研究的团队价值很大。
- **决策资产**：SVD-Cache 的"负结果 + 可复用读数 + 生产推荐（taylorseer/dmd）"被文档化，避免团队重复试错，体现了务实的工程取舍文化。
- **指标可信度**：PSNR 修复保证了此前和后续所有质量验收数据的有效性，对 #1340 等带实测表格的变更尤其关键。

## 4. 值得关注的技术点
- **CuTe/DSL 层的细粒度特化**：几何门控的 G2R 路径、`kFuseDown` 分派、producer 侧 SwiGLU 双族实现，以及为保留性能基线而留的 forced-TMA benchmark，展示出对硬件执行模型的深入控制。
- **calibrator 统一抽象**：`--calibrator {taylorseer,dmd,foca,svd}` + `--calibrator-params` 的设计，四个开关互斥、冲突即失败，是典型的 CLI 收敛重构。
- **在线拟合 SVD**：SVD-Cache 不依赖离线 artifact，每次推理期冻结，降低部署复杂度。
- **系统化验证方式**：单批提交合计通过 234+203+197+65 项回归/单元测试，并统一 7x3 基准 + FLUX/Qwen eager/compile e2e，测试覆盖相当扎实。

## 5. 基于 README 背景对项目发展的判断
README 表明 cache-dit 是"**带缓存、并行、量化、CPU offload 的 PyTorch 原生 DiT 推理引擎**"。本批提交同时强化了其中两根支柱——**Cache 与 Quantization**——并补齐了**衡量缓存/质量的指标正确性**：

- 量化侧已从"能跑"进入"逼近原生"的收敛期，剩余 gap 集中在 #1336 追踪的 full-M 下游 GEMM，说明性能工作进入了长尾优化阶段。
- 缓存侧则完成了从"散点实现"到"框架化评估 + 统一接口"的升级，SVD-Cache 的负结果说明团队在用可量化的方式筛选缓存方案，而非盲目堆功能。
- 整体上，项目正从功能构建转向**性能对标原生、接口收敛、知识沉淀（skill 化）与结论可追溯**的成熟工程阶段，这与其作为对外发布的 PyTorch 推理引擎的定位一致。

## 详细提交记录

### [519cd1d](https://github.com/vipshop/cache-dit/commit/519cd1d33ab3412361410bfe0b7b767a43e669d9)

- **作者**: DefTruth
- **时间**: 2026-11-17T12:33:06Z
- **提交信息**: perf(svdq): close the full-M fc2 CuTe gap (#1344)

Add a geometry-gated pure-G2R large-K row-major-D fc2 path, preserve a forced-TMA benchmark baseline, and cover dispatch, numerical parity, and malformed-pack boundaries.

Full-M fc2 reaches 0.948x/0.965x of native at M=4096/8192. Validated by 234 regression tests, unified 7x3 benchmarks, and FLUX eager/compile e2e; all PR checks pass.

### [abae49d](https://github.com/vipshop/cache-dit/commit/abae49dd5b33fb05da1e7c6d855f1769f3794aa2)

- **作者**: DefTruth
- **时间**: 2026-11-17T10:11:31Z
- **提交信息**: perf(svdq): optimize the CuTe fused MLP chain (#1343)

Vectorize and pair fused quantization stores, pipeline the D epilogue's B-operand loads, and split fused GEMM instances into fused.cu with kFuseDown specialization.

Validated by 203 SVDQ tests and FLUX eager/compile e2e. The remaining full-M downstream GEMM gap is tracked in #1336.

### [69260e7](https://github.com/vipshop/cache-dit/commit/69260e7277bfa058fb6e3ac91d8410fbe3ff0a4b)

- **作者**: DefTruth
- **时间**: 2026-11-17T09:45:45Z
- **提交信息**: docs(skill): record the SVD-Cache outcome in the cache-integration skill (#1342)

Follow-up to #1340, which shipped the SVDCalibrator but could not carry these
notes (they were written in the wrong checkout).

- SKILL.md judgement table: SVD-Cache moves from "priority highest, not
  implemented" to "v1 implemented, negative result"; the row now carries the
  two operating points, the reason EMA cannot win and where the loss comes from.
- references/landscape.md: §2.3 gets the measured basis ranks and the two
  predictors; new §4.4 adds the full same-harness table (rdt 0.12 and
  rdt 0.6 + mcc 6), the three reusable readings, and the production
  recommendation (taylorseer / dmd).

### [30f8aae](https://github.com/vipshop/cache-dit/commit/30f8aaef52f61ddd6f95306943f2225e22164fca)

- **作者**: DefTruth
- **时间**: 2026-11-17T09:39:13Z
- **提交信息**: feat(cache): add SVD-Cache calibrator and unify the calibrator CLI (#1340)

- New SVDCalibrator: token x channel low-rank split of the cached block
  tensor, basis fitted online (no offline artifact), frozen per inference.
  Two predictors: "ema" (paper smoothing) and "taylor" (SVD + Taylor).
- Unify calibrator selection: --calibrator {taylorseer,dmd,foca,svd} plus
  --calibrator-params "k=v,k=v"; legacy --taylorseer/--dmd/--foca kept as
  aliases, conflicting selections now fail.
- load_configs: enable_svd/svd_* keys, four calibrator switches mutually
  exclusive.
- Docs, example yaml and tests: CACHE_API section with the measured table,
  sync of the stale --help blocks, 65 unit tests (incl. batched CFG input,
  bit-exact no-cache regression, pipeline-level calibrator assertions).

### [fe1641f](https://github.com/vipshop/cache-dit/commit/fe1641f9bcb32fe03ba1f4718aaec5f752793ebc)

- **作者**: DefTruth
- **时间**: 2026-11-17T06:46:06Z
- **提交信息**: docs(skill): add cache-algorithm integration skill (#1338)

* docs(skill): add cache-integration skill for cache paper triage

Add .agents/skills/cache-dit-cache-integration so a new feature-caching paper can be triaged and landed without re-deriving cache-dit's cache architecture each time.

- SKILL.md: three-layer split (skip timing / skip granularity / replacement operator), five gates, red flags, the judged cases (HiCache, MagCache, SVD-Cache, DiCache), landing options and the acceptance gate.

- references/landscape.md: current cache surface (DBCache / DBPrune / TaylorSeer / DMD / FoCa), four paper skeletons, dimension-by-dimension comparison and the same-harness baseline table.

- references/extension-points.md: file map, four landing options with concrete edit lists, CP/TP/quant/offload/compile interactions, minimal test matrix and known pitfalls.

- references/paper-triage.md: one-hour triage flow, 12 checkpoints, decision tree and the single conclusion template.

- docs/developer_guide/AGENTS.md: register the skill in the index table and add two example prompts.

* docs(skill): tighten the PSNR caveat after the #1335 metrics fix

The peak stays 255 in calculate_psnr; #1335 only fixed the uint8 wraparound. Feeding float[0, 1] still inflates by 48.13 dB, so say exactly that instead of blaming the whole function.

### [3a43504](https://github.com/vipshop/cache-dit/commit/3a43504b07ea110096944483b005251949a3f4c9)

- **作者**: DefTruth
- **时间**: 2026-11-17T06:27:12Z
- **提交信息**: feat(svdq): fused MLP and SwiGLU on the CuTe NVFP4 runtime (#1332)

Fused epilogue for the CuTe W4A4 GEMM (qout/oscales + both D layouts + write_dense), producer-side SwiGLU on both producer families, and row_major as a first-class fused path.

Verified with 197 SVDQ tests and FLUX/Qwen e2e. The remaining chain-level performance gap is tracked separately in #1336.

### [da397cc](https://github.com/vipshop/cache-dit/commit/da397ccacab8a9d927c4b8b18e11017975fc164f)

- **作者**: DefTruth
- **时间**: 2026-11-17T04:12:27Z
- **提交信息**: fix(metrics): cast PSNR inputs to float64 to avoid uint8 wraparound (#1335)

calculate_psnr subtracted the uint8 arrays returned by cv2.imread directly, so
negative residuals wrapped modulo 256 and the MSE came out far too small. PSNR
therefore inflated by 5-21 dB depending on how different the two images are
(28.00 dB reported vs 6.69 dB true on one pair from the acceptance run).

Cast both inputs to float64 before the residual; the peak stays 255 for uint8
semantics. Adds tests/metrics/test_metrics_psnr.py, which fails on the previous
implementation (4 of 5 cases) and passes after the fix.

Co-authored-by: DefTruth <def_truth@163.com>

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-11-18
**监控日期**: 2026-11-17
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 97121
- **最后更新**: 2026-11-18T03:38:20Z

## 提交统计

- **昨日提交总数**: 91
- **提交者数量**: 66
- **主要提交者**: Thien Tran, Yiliu Dong, DimensionSTP

## AI分析总结

# vLLM 昨日提交分析（91 条）

## 1. 主要更新类型

- **Bug 修复**：占比最高（约 35 条），覆盖调度、注意力后端、投机解码、多模态、LoRA、量化、NIXL 通信及内核数值稳定性。
- **性能优化**：约 26 条，集中在注意力内核、MoE、投机解码、流水线并行与 ROCm/GPU 后端。
- **多硬件平台与 CI**：Intel XPU、AMD ROCm、Arm 主机的测试维护、镜像与跳过策略。
- **模型与配方新增**：NemotronLabsDiffusion 三模式推理、Base Labs mammoth/elephant 双向掩码模型、MiniCPM-OCR、Kimi-K3.1-Pro 多轮与 B300 分离式预设、DSpark/DFlash 调优。
- **功能与安全**：watermarking 密钥管理、CV-CUDA GPU 图像预处理、2 条明确的安全加固。
- **文档与重构**：量化表格自动生成、Routed Experts 调优指南、Ask AI 组件、死代码清理。

## 2. 关键变更点及与项目方向的关系

- **核心稳定性**：修复 FA3 MLA split-KV 超出 CUDA graph 尺寸导致的 OOM、prefix replay 不遵守 `prefill_schedule_interval`、spec decode D2H 拷贝改用设备无关流、top-k NaN、RMSNorm 维度约束等，直接保障长序列与高吞吐场景的调度正确性。
- **投机解码深化**：DSpark/DFlash 滑窗草稿 KV 仅保留尾部、CAKE 上运行 DSpark 草稿块、滑窗 Triton split-K 解码，服务"快速廉价"目标。
- **多后端异构生态**：ROCm gfx942/gfx1151 大量修复、XPU 包索引与 LoRA 测试维护、NVIDIA SM90/100/107 与 L4 FP8 配方，体现非 NVIDIA 硬件的一等公民战略。
- **分布式可靠性**：NIXL 连接丢失重握手、DCP 配置检查、Copy-engine PP 支持 TP>1 与多节点 NVLink。
- **安全加固**：错误信息限制非法模型名、视频帧计入请求预算防滥用，增强多租户部署健壮性。

## 3. 对项目的影响和潜在意义

- 高频内核与内存修复（CoW OOM、cuMem guard、Mooncake 主机内存释放、CPU KV 排除出 core dump）提升生产稳定性，降低用户踩坑成本。
- **量化能力扩展**：NVFP4 MoE 在线量化支持 CPU offload、FP8 KV cache，为显存受限环境提供新的低成本路径。
- **配方体系快速迭代**：B300/GB300 开箱即用预设、nightly 依赖刷新，降低前沿模型复现门槛；文档自动生成与 Ask AI 组件契合"for everyone"定位。
- **AI 辅助开发常态化**：多数提交以 Claude、Codex、Copilot 为共同作者，AI 结对已深度融入开发流程，加快迭代与社区贡献吞吐。

## 4. 值得关注的技术点

- **稀疏 MLA prefill 路由**在 metadata builder 中一次性决策，减少运行时开销。
- **FlashInfer warp split-K GEMM** 引入 SM107 低延迟表，展示新架构内核适配节奏。
- **注意力块大小协商机制**：仅当所有后端偏好一致时才采用，体现多后端抽象精细化。
- **Transformers 后端**首次可服务 Llama，为统一抽象铺路。
- **EPLB 窄状态暴露给树外设备**，为第三方硬件集成提供扩展点。
- **CV-CUDA GPU 端图像/视频缩放**将多模态预处理卸载到 GPU；beam search 对极端 `length_penalty` 做数值防御。

## 5. 对项目发展的影响

这批提交呈现"稳底盘、拓边界"的双重主线：一方面通过大量内核、通信、调度与内存修复夯实 serving 稳定性，项目正从功能扩张期转向大规模生产级打磨期；另一方面在投机解码、稀疏注意力、扩散模型及 ROCm RDNA、SM100/107、B300 等新硬件上持续扩张能力边界。结合 README 愿景，"fast"由 ROCm/CuTe/Triton 内核与 FP8 KV cache 强化，"cheap"通过 NVFP4 offload 与多硬件支持降低成本，"easy"体现在新配方、配置扩展与 CI 稳定性上。多平台 CI 的密集维护印证其生态多元化战略，AI 协作开发与自动化文档的成熟将进一步巩固 vLLM 在 LLM 推理服务领域的领先地位。

## 详细提交记录

### [952dc48](https://github.com/vllm-project/vllm/commit/952dc48bcf64c5f071086d59507c55de5a8f6951)

- **作者**: Andreas Karatzas
- **时间**: 2026-11-17T23:43:30Z
- **提交信息**: [ROCm][Bugfix] Keep a guard granule after each sleep-mode cuMem reservation (#68090)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [ba5477f](https://github.com/vllm-project/vllm/commit/ba5477f3df9f3fe058db69b3f2ef4954d0a31e89)

- **作者**: Wentao Ye
- **时间**: 2026-11-17T23:29:33Z
- **提交信息**: [Refactor] Remove multiple dead code in models (#68010)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [7725438](https://github.com/vllm-project/vllm/commit/7725438cc4c1f8d8266d18fc2517602c9655fc4d)

- **作者**: Aarushi Jain
- **时间**: 2026-11-17T23:08:18Z
- **提交信息**: [CI][ROCm] Skip the memory-settle stability wait when the GPU is idle (#66670)

Signed-off-by: aarushjain29 <aarushi.jain2@amd.com>
Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [7a1d281](https://github.com/vllm-project/vllm/commit/7a1d2818b63ed86d3c17bae533206b20d37906db)

- **作者**: Andreas Karatzas
- **时间**: 2026-11-17T23:02:54Z
- **提交信息**: [Bugfix][Multimodal] Skip the Omni audio-in-video host read without audio and video (#68099)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [935f87d](https://github.com/vllm-project/vllm/commit/935f87de846980dc16c54ac1996595fc12eb3f9e)

- **作者**: mispa-ms
- **时间**: 2026-11-17T21:49:25Z
- **提交信息**: [Recipe] Kimi-K3.1-Pro: B300 PD preset serves the released DSpark draft, align with InferenceX#5108 (#68093)

Signed-off-by: Mi Sun Park <misunp@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [c8cd8b0](https://github.com/vllm-project/vllm/commit/c8cd8b06fe89d5d0cc034031728882d88f2edb57)

- **作者**: Bo Pang
- **时间**: 2026-11-17T21:42:54Z
- **提交信息**: [Attention] Decide the sparse MLA prefill route once in the metadata builder (#67338)

Signed-off-by: Bo Pang <bopang314@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [5a7fcd3](https://github.com/vllm-project/vllm/commit/5a7fcd38f99e052be89beff15ae58e25b53ab6d4)

- **作者**: Yiliu Dong
- **时间**: 2026-11-17T21:07:27Z
- **提交信息**: [Perf][Hy4] Sequence parallelism for iHC (#67659)

Signed-off-by: Yiliu Dong <91178480+qianlihuang@users.noreply.github.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [1580561](https://github.com/vllm-project/vllm/commit/1580561b6eade24f2724a3805ae616dfe6801aca)

- **作者**: Harry Mellor
- **时间**: 2026-11-17T20:44:48Z
- **提交信息**: [CI] Remove CODEOWNERS entries for users without write access (#68148)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [21d9da4](https://github.com/vllm-project/vllm/commit/21d9da46b30b9f6f83afbd076924595946ee34eb)

- **作者**: mispa-ms
- **时间**: 2026-11-17T20:36:02Z
- **提交信息**: [Recipe] Kimi-K3.1-Pro: document the GB300 DEP lanes' frontend session affinity and weight load format, align with InferenceX#5069 (#68220)

Signed-off-by: Mi Sun Park <misunp@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [645f0b9](https://github.com/vllm-project/vllm/commit/645f0b9f491607dbf932e4a15c061938bf1d56dd)

- **作者**: ArkVex
- **时间**: 2026-11-17T20:12:39Z
- **提交信息**: [Frontend] Support output logprobs for gpt-oss in the Responses API (#64027)

Signed-off-by: ArkVex <dev@mysola.world>
Co-authored-by: Flora Feng <4florafeng@gmail.com>

### [61dc78b](https://github.com/vllm-project/vllm/commit/61dc78bc9ecc2531ea6ea6125f42789f722321ad)

- **作者**: Nick Hill
- **时间**: 2026-11-17T19:58:36Z
- **提交信息**: [Bugfix][NIXL] Re-handshake a pull peer whose connection NIXL reports lost (#68047)

Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Yongye Zhu <zyy1102000@gmail.com>
Co-authored-by: Maroon Ayoub <mayoub@redhat.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [3aeca63](https://github.com/vllm-project/vllm/commit/3aeca630d8c3ca0aa28858cb87c65b6a97714a80)

- **作者**: Sajad Norouzi
- **时间**: 2026-11-17T19:46:41Z
- **提交信息**: [Model] Add NemotronLabsDiffusion support with tri-mode inference (#58387)

Signed-off-by: Alex Steiner <asteiner@nvidia.com>
Signed-off-by: "Alex Steiner" <asteiner@nvidia.com>
Signed-off-by: Lucas Wilkinson <lwilkins@redhat.com>
Signed-off-by: pst2154 <6865592+pst2154@users.noreply.github.com>
Co-authored-by: Alex Steiner <asteiner@nvidia.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: pst2154 <6865592+pst2154@users.noreply.github.com>
Co-authored-by: Lucas Wilkinson <LucasWilkinson@users.noreply.github.com>

### [46cff21](https://github.com/vllm-project/vllm/commit/46cff217653ea0f08c96cd47102356070e51362d)

- **作者**: Misha Goin
- **时间**: 2026-11-17T19:33:28Z
- **提交信息**: [Docs] Generate quantization method, scheme, and linear backend tables (#65215)

Signed-off-by: Misha Goin <mgoin64@gmail.com>
Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: DeepSeek V4.1 Flash <noreply@deepseek.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [db8e465](https://github.com/vllm-project/vllm/commit/db8e4658ed0f322710804738f03de9318abeb8fc)

- **作者**: mispa-ms
- **时间**: 2026-11-17T18:45:57Z
- **提交信息**: [Recipe] Kimi-K3.1-Pro: serve the preview DSpark draft in the GB300 AgentX presets, align with InferenceX#5069 (#68213)

Signed-off-by: Mi Sun Park <misunp@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [08191fe](https://github.com/vllm-project/vllm/commit/08191feb2dd6f75e167cfc32cbef9b683d9ba523)

- **作者**: DimensionSTP
- **时间**: 2026-11-17T18:30:39Z
- **提交信息**: [Bugfix][NIXL] Apply DCP config checks to NixlPullConnector (#60255)

Signed-off-by: DimensionSTP <65501090+DimensionSTP@users.noreply.github.com>
Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>
Co-authored-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [8c9e6f9](https://github.com/vllm-project/vllm/commit/8c9e6f919ec6b921d61be9771187bf901bb3d19a)

- **作者**: Dao007forever
- **时间**: 2026-11-17T18:08:50Z
- **提交信息**: [Core][Spec Decode] Back only the tail of DFlash/DSpark sliding-window drafter KV (#64109)

Signed-off-by: Dao Le <Dao007forever@gmail.com>
Signed-off-by: Dao Le <daole@inferact.ai>
Signed-off-by: Yifan Qiao <yifanqiao@inferact.ai>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: Yifan Qiao <yifanqiao@inferact.ai>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [905a81d](https://github.com/vllm-project/vllm/commit/905a81dd83d057bccbb66396805e244880d15cd4)

- **作者**: mispa-ms
- **时间**: 2026-11-17T18:04:51Z
- **提交信息**: [Recipe] Kimi-K3.1-Pro: update GB300 AgentX presets, align with InferenceX#5069 (#67719)

Signed-off-by: Mi Sun Park <misunp@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [f538463](https://github.com/vllm-project/vllm/commit/f538463a2e233e23925fd259e2a3acc4e99d95f2)

- **作者**: Sahithi Chigurupati
- **时间**: 2026-11-17T17:35:46Z
- **提交信息**: [Perf][GLM-5.3] Add FlashInfer warp split-K GEMMs to the SM107 low-latency table and fix q_b's M=1 fallback (#65706)

Signed-off-by: Sahithi Chigurupati <chigurupati.sahithi@gmail.com>
Signed-off-by: LopezCastroRoberto <rocastro@redhat.com>
Co-authored-by: Roberto L. Castro <38211239+LopezCastroRoberto@users.noreply.github.com>
Co-authored-by: LopezCastroRoberto <rocastro@redhat.com>

### [748f1ab](https://github.com/vllm-project/vllm/commit/748f1ab353d77900e1b55961b331d4cc1cd72edc)

- **作者**: Luca Motz
- **时间**: 2026-11-17T17:02:46Z
- **提交信息**: [Bugfix][Kernel] Key sign-set NaN scores above +inf in the top-k kernels (#66839)

Signed-off-by: Luca Motz <luca.motz@icloud.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [b1a26ea](https://github.com/vllm-project/vllm/commit/b1a26ea58f1474aa6a7c6455e5685a5efb7dfe8e)

- **作者**: Markus Hartikainen
- **时间**: 2026-11-17T17:01:56Z
- **提交信息**: [ROCm][Perf][DSv4.1] Mono decode at tensor parallel size 8 on gfx942 (#67540)

Signed-off-by: Markus Hartikainen <markus.hartikainen@amd.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [0108707](https://github.com/vllm-project/vllm/commit/0108707434cd40ccc764d37c3590e5ac2032c971)

- **作者**: Harry Mellor
- **时间**: 2026-11-17T17:01:37Z
- **提交信息**: [Transformers backend] Serve Llama with the Transformers modeling backend (#66547)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [b3a483b](https://github.com/vllm-project/vllm/commit/b3a483bc56749b476cb5012f20a37eb5fbc6481a)

- **作者**: simon-veitner-redhat
- **时间**: 2026-11-17T16:38:07Z
- **提交信息**: [Model] Serve Base Labs mammoth-1 / elephant-1 with their trained block-bidirectional mask (#63114)

Signed-off-by: Simon Veitner <sveitner@redhat.com>
Signed-off-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: Lucas Wilkinson <LucasWilkinson@users.noreply.github.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [d92a765](https://github.com/vllm-project/vllm/commit/d92a765211e4b898c2b0c605926a02f4bee5b3de)

- **作者**: Nick Hill
- **时间**: 2026-11-17T16:35:04Z
- **提交信息**: [Perf][PP] Copy-engine PP transport: TP > 1, PCP > 1 and multi-node NVLink (#66677)

Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [f39d833](https://github.com/vllm-project/vllm/commit/f39d83306ea62d4ad8919995f378d8ca4aed8b57)

- **作者**: keneoneth
- **时间**: 2026-11-17T16:26:59Z
- **提交信息**: [ROCm] Restore gfx1151 paged-MQA fused path (#56328)

Signed-off-by: keneoneth <keneoneth18@gmail.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: Douglas Lehr <91553416+dllehr-amd@users.noreply.github.com>

### [c978033](https://github.com/vllm-project/vllm/commit/c9780337c79107341010e11244a7c95507835375)

- **作者**: Raghu-dev-pixel
- **时间**: 2026-11-17T16:04:27Z
- **提交信息**: [Misc] Log unsupported FlashAttention version as a one-time warning (#63592)

Signed-off-by: Raghu Mysore Shantharam <raghums534@gmail.com>

### [b7e43db](https://github.com/vllm-project/vllm/commit/b7e43db256a69b8c2917e5ef4cf8073a086187eb)

- **作者**: S.J. Lee
- **时间**: 2026-11-17T15:42:12Z
- **提交信息**: [Model Loader] Find safetensors shards listed in a subdirectory (#64739)

Signed-off-by: lesj0610 <lesj0610@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [77d76a8](https://github.com/vllm-project/vllm/commit/77d76a89bf808fdf79287d7662b823a1be52a78e)

- **作者**: Uros Markovic
- **时间**: 2026-11-17T15:36:40Z
- **提交信息**: [Perf][Attention] Split only the sliding window into Triton split-K decode segments (#61646)

Signed-off-by: Uros Markovic <umarkovi@amd.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Douglas Lehr <91553416+dllehr-amd@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [571b75a](https://github.com/vllm-project/vllm/commit/571b75ab8d7dfb827257c807ba9f2a313d586ba0)

- **作者**: Stephan Toivonen
- **时间**: 2026-11-17T15:35:32Z
- **提交信息**: [ROCm][RDNA][Perf] W4A16: fused scale/zero-point carrier for Triton prefill (#64375)

Signed-off-by: Stephan Toivonen <Stephan.Toivonen@amd.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [c7d2760](https://github.com/vllm-project/vllm/commit/c7d27607f4a0ac0d26cd188559c69c612e4eef30)

- **作者**: Misha Goin
- **时间**: 2026-11-17T15:35:22Z
- **提交信息**: [Doc] Remove stale install_deepgemm.sh references (#68011)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [89e860d](https://github.com/vllm-project/vllm/commit/89e860de0073bb9b5ed6af2a42817e2edb99b606)

- **作者**: Jyun-An Chen
- **时间**: 2026-11-17T15:15:58Z
- **提交信息**: [Misc] Remove --log-config-file and indexer_tp_shard_min_rows past their removal version (#67679)

Signed-off-by: ColtenOuO <jun930436@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [891a2d7](https://github.com/vllm-project/vllm/commit/891a2d787efbdf470ec59cc9b882709b6aed637e)

- **作者**: Harry Mellor
- **时间**: 2026-11-17T15:15:51Z
- **提交信息**: [CI] Only use trust_remote_code for checkpoints that need it (#67964)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [2497008](https://github.com/vllm-project/vllm/commit/24970086663a0bdddd2433acb9e28e9aac4018c9)

- **作者**: aoshen02
- **时间**: 2026-11-17T14:48:06Z
- **提交信息**: [Doc] Sleep mode: free a KV connector's host memory with Mooncake standalone-store (#68175)

Signed-off-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [8562b2c](https://github.com/vllm-project/vllm/commit/8562b2cb2ac6715b40b9066eab7e4e35e6600a79)

- **作者**: Misha Goin
- **时间**: 2026-11-17T14:42:54Z
- **提交信息**: [Build] Bump humming-kernels to 0.1.20 (#68007)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [2d4457d](https://github.com/vllm-project/vllm/commit/2d4457d33306aaef297071f0c43ba6420fc9b4d2)

- **作者**: Misha Goin
- **时间**: 2026-11-17T14:36:05Z
- **提交信息**: [Kernel] Bump DeepGEMM for SM90 paged-MQA metadata and mHC prenorm fixes (#68017)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [377c4d7](https://github.com/vllm-project/vllm/commit/377c4d7e5b814a7aad4f26ade5ff256ca0d08793)

- **作者**: Shijie Lyu
- **时间**: 2026-11-17T14:21:27Z
- **提交信息**: [Perf][MoE] Add NVIDIA L4 FP8 fused MoE config for Qwen3-30B-A3B (#66711)

Signed-off-by: Shijie Lyu <lshjhf@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>

### [88456c7](https://github.com/vllm-project/vllm/commit/88456c78cedb8a7c5c32f6d33013ff41f299e2e9)

- **作者**: Sidhartha Reddy Potu
- **时间**: 2026-11-17T14:19:16Z
- **提交信息**: [Bugfix] Muse Glimmer: fix vision embedding order (#68021)

Signed-off-by: sid-rp <sidrp@meta.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Jee Jee Li <pandaleefree@gmail.com>

### [441cf52](https://github.com/vllm-project/vllm/commit/441cf52085427fd4d4559447813faef9a5624bd3)

- **作者**: zexplorerhj
- **时间**: 2026-11-17T14:18:15Z
- **提交信息**: [Bugfix][Model] Fix Ling VL MTP quantization config (#68087)

Signed-off-by: zexplorerhj <zhjoneson@163.com>
Co-authored-by: ghphotoframe <854746559@qq.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [0edebb6](https://github.com/vllm-project/vllm/commit/0edebb6625f803d8b749c436578b2a8b4e5615af)

- **作者**: aoshen02
- **时间**: 2026-11-17T14:13:58Z
- **提交信息**: [Doc] Routed experts: row storage, replica affinity, sizing and cache resets (#68174)

Signed-off-by: Ao Shen <aoshen524@gmail.com>
Co-authored-by: Ao Shen <aoshen524@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [8392490](https://github.com/vllm-project/vllm/commit/8392490d24f11f78c074e5c696bbf43bb4b71cea)

- **作者**: Sherif Waly
- **时间**: 2026-11-17T14:12:58Z
- **提交信息**: [Bugfix][Kimi-K3] Capture all mixed CUDA graphs with RecoverSSM (#67903)

Signed-off-by: Sherif Waly <sherif.waly@mistral.ai>
Co-authored-by: Nicolò Lucchesi <nicolo.lucchesi@mistral.ai>

### [dd4aadb](https://github.com/vllm-project/vllm/commit/dd4aadb5b20f5f1c520bca89a8dda2a429c954f7)

- **作者**: Lê Duy Khang
- **时间**: 2026-11-17T13:50:39Z
- **提交信息**: [Bugfix] Report reasoning_tokens in /inference/v1/generate derender usage (#65383)

Signed-off-by: Khang Le Duy <ldkhang1201@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [adadaad](https://github.com/vllm-project/vllm/commit/adadaad8b185568d1e91cf6ed92ee687469ee819)

- **作者**: Jiangyun Zhu
- **时间**: 2026-11-17T13:39:10Z
- **提交信息**: [Kimi K3][Specialized decode] Run causal DSpark draft blocks on CAKE (TP / DEP) (#67588)

Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: wzhao18 <weizha@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [ff8be57](https://github.com/vllm-project/vllm/commit/ff8be5722fd05273a16de10eb5aa992a16ce74b3)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-11-17T13:35:05Z
- **提交信息**: [KV Offload] Leave CPU KV offload buffers out of core dumps (#67960)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [4d7f225](https://github.com/vllm-project/vllm/commit/4d7f225e4e8209879ef14175be6ba263da7c900c)

- **作者**: michael-gpu
- **时间**: 2026-11-17T13:34:52Z
- **提交信息**: [Bugfix] Bound CoW block-copy transient to avoid OOM near the memory limit (#61051)

Signed-off-by: michael-gpu <18089103+michael-gpu@users.noreply.github.com>
Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: opencode <noreply@opencode.ai>
Co-authored-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: Thien Tran <26946864+gau-nernst@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [5d83998](https://github.com/vllm-project/vllm/commit/5d83998e927f3081c804932e6586bd7312a424e8)

- **作者**: Harry Mellor
- **时间**: 2026-11-17T13:13:16Z
- **提交信息**: [Docs] Add add-cli-arg agent skill and drop arg_utils.py code owner (#68144)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [7697182](https://github.com/vllm-project/vllm/commit/7697182102ea94c947e796f1eed35aa44ae37179)

- **作者**: Harshal Janjani
- **时间**: 2026-11-17T13:00:38Z
- **提交信息**: fix: Only fuse RMSNorms that normalize over the last dim (#67989)

Signed-off-by: Harshal Janjani <harshaljanjani@gmail.com>

### [26acafd](https://github.com/vllm-project/vllm/commit/26acafd3a5aab86d76f44a42787f2d53cf6c5a8b)

- **作者**: Chauncey
- **时间**: 2026-11-17T11:49:22Z
- **提交信息**: [Bugfix] Avoid read-only NumPy warnings in DeepSeek-V4.1/v41 image prepro (#67896)

Signed-off-by: chaunceyjiang <chaunceyjiang@gmail.com>
Signed-off-by: Chauncey <chaunceyjiang@gmail.com>
Co-authored-by: cjackal <44624812+cjackal@users.noreply.github.com>

### [c84273b](https://github.com/vllm-project/vllm/commit/c84273be384d7faaeadfb36caced2f9d5a112f7f)

- **作者**: Jared Wen
- **时间**: 2026-11-17T11:04:49Z
- **提交信息**: [Perf][KDA] Export Triton prefill checkpoints for Bailing V3 (#68106)

Signed-off-by: Jared Wen <jaredwen@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [4bd291d](https://github.com/vllm-project/vllm/commit/4bd291dc3c3771af5a81a4b822c29391d5bf2ae7)

- **作者**: Roy Wang
- **时间**: 2026-11-17T10:38:40Z
- **提交信息**: [Docs] Add Ask AI widget (#68102)

Signed-off-by: esmeetu <jasonailu87@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [91fc1e1](https://github.com/vllm-project/vllm/commit/91fc1e1cc57ccf81bf16adeededec7045c155125)

- **作者**: Hung Hoang (黄兴）
- **时间**: 2026-11-17T10:32:35Z
- **提交信息**: [Bugfix][Multimodal] Size the ERNIE-4.5-VL image budget from the processor's pixel limits (#68122)

Signed-off-by: hungh <hungh@nvidia.com>
Co-authored-by: Cursor Agent <cursoragent@cursor.com>

### [48e1b88](https://github.com/vllm-project/vllm/commit/48e1b883050c40187e76e82877627c3423fecbeb)

- **作者**: Jee Jee Li
- **时间**: 2026-11-17T10:15:41Z
- **提交信息**: [Bugfix][LoRA] Reject reusing the same lora_int_id for  a different adapter (#67970)

Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>

### [01fb22e](https://github.com/vllm-project/vllm/commit/01fb22eed6b5ae67f7b97bc19dc637bd413851c7)

- **作者**: stefankoncarevic
- **时间**: 2026-11-17T10:07:55Z
- **提交信息**: [ROCm][Bugfix] Null stale block-table entries after the KV cache sizing shrink (#67966)

Signed-off-by: Stefan Koncarevic <Stefan.Koncarevic@amd.com>
Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [ac796f3](https://github.com/vllm-project/vllm/commit/ac796f363e4e55dc92f8339b2ff772958c3de8ff)

- **作者**: Arijit Desai
- **时间**: 2026-11-17T10:07:33Z
- **提交信息**: [CPU] Keep user-set KMP_BLOCKTIME and KMP_TPAUSE in CPU workers (#67726)

Signed-off-by: ardecode <desaiarijit@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [82d1643](https://github.com/vllm-project/vllm/commit/82d1643db4da6a15dba1a4128f163a3f3b3ced7c)

- **作者**: 최재영
- **时间**: 2026-11-17T10:07:22Z
- **提交信息**: [Bugfix][Multimodal] Use the request's max_slice_nums for MiniCPM-V/O image placeholders (#68096)

Signed-off-by: 최재영 <144660874+Jaeyeong-CHOI@users.noreply.github.com>
Co-authored-by: OpenAI Codex (GPT-6 Astra) <noreply@openai.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [990372c](https://github.com/vllm-project/vllm/commit/990372cacb2528cb46817514c7d0faf896bed329)

- **作者**: 최재영
- **时间**: 2026-11-17T10:02:55Z
- **提交信息**: [Bugfix][Multimodal] Don't forward image crop kwargs to the InternVL video processor (#68076)

Signed-off-by: 최재영 <144660874+Jaeyeong-CHOI@users.noreply.github.com>
Co-authored-by: OpenAI Codex (GPT-6 Astra) <noreply@openai.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [f91a777](https://github.com/vllm-project/vllm/commit/f91a7779cad81443345f326386a996e6488b27e2)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-11-17T09:28:13Z
- **提交信息**: [Misc] Update ML4 recipe (#68126)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [a8183ab](https://github.com/vllm-project/vllm/commit/a8183ab9cf79f2474d58f2e363c7ed60cebf3ba9)

- **作者**: Kevin H. Luu
- **时间**: 2026-11-17T09:21:24Z
- **提交信息**: [CI] Fix three CI-config failures: L4 Preload and N-Gram timeouts, ROCm refresh retry (#67918)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [c2d218e](https://github.com/vllm-project/vllm/commit/c2d218ee3057ea6aff8bbca6d64ff9654165cdd1)

- **作者**: Thien Tran
- **时间**: 2026-11-17T08:59:23Z
- **提交信息**: [Perf][Qwen4Exp] QSA top-k: default to FlashInfer gvr_2 on SM100 (#67741)

Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [3487d03](https://github.com/vllm-project/vllm/commit/3487d039b6dd245e55673ba07f2924a2d57a0ed7)

- **作者**: Andreas Karatzas
- **时间**: 2026-11-17T08:55:09Z
- **提交信息**: [ROCm][Bugfix] Route OCP MX emulation MoE experts without a host sync (#68050)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [bf5567a](https://github.com/vllm-project/vllm/commit/bf5567a306ac0e5fdfd02a051b4d45692ac42188)

- **作者**: Roy Wang
- **时间**: 2026-11-17T08:30:26Z
- **提交信息**: [Recipe] Make the DeepSeek-V4.1-Flash and Kimi-K3 AgentX presets opt-in (#68109)

Signed-off-by: esmeetu <jasonailu87@gmail.com>
Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>

### [96b0d14](https://github.com/vllm-project/vllm/commit/96b0d1466d6b84f4079bcce5782cd680e40a693a)

- **作者**: Roy Wang
- **时间**: 2026-11-17T08:28:48Z
- **提交信息**: [Recipe] Refresh nightly requirements after v0.34.0 (#68110)

Signed-off-by: esmeetu <jasonailu87@gmail.com>
Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>

### [5b9b189](https://github.com/vllm-project/vllm/commit/5b9b189d8b3e024d1d6108a22a2cdf08233cd1cf)

- **作者**: Vadim Gimpelson
- **时间**: 2026-11-17T08:26:49Z
- **提交信息**: [Bugfix] Fix OOM from unused FA3 MLA split-KV buffer on decode batches above CUDA graph sizes (#67489)

Signed-off-by: Vadim Gimpelson <vadim.gimpelson@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [73cdfa0](https://github.com/vllm-project/vllm/commit/73cdfa01e5bcb478544db6a25092064b801b479c)

- **作者**: Kevin H. Luu
- **时间**: 2026-11-17T08:24:47Z
- **提交信息**: [CI] Prune old images on Arm CPU test hosts under disk pressure (#67640)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [f35d1e2](https://github.com/vllm-project/vllm/commit/f35d1e215068a38667161f56c94087a2bf77e8d4)

- **作者**: Kevin H. Luu
- **时间**: 2026-11-17T08:23:32Z
- **提交信息**: [XPU][Bugfix] Freeze the startup heap in XPUWorker.init_device (#67639)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [059fb66](https://github.com/vllm-project/vllm/commit/059fb66bdc0e25d086ff517f5a9c5e72825c13dd)

- **作者**: sebfelix
- **时间**: 2026-11-17T08:16:22Z
- **提交信息**: [Misc] Watermarking: read the key from a file (#64550)

Signed-off-by: Sebastian Felix <sebastianf369@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [c26c9bf](https://github.com/vllm-project/vllm/commit/c26c9bfeb7ee2c804fe55b425afd049809814582)

- **作者**: kliuae
- **时间**: 2026-11-17T07:32:40Z
- **提交信息**: [ROCm][Perf] Muse Spark Open Shard residual stream across TP (#63085)

Signed-off-by: kliuae <kuanfu.liu@embeddedllm.com>
Co-authored-by: Claude Opus <noreply@anthropic.com>
Co-authored-by: TJian <tunjian.tan@embeddedllm.com>

### [8bdc685](https://github.com/vllm-project/vllm/commit/8bdc68536b8fdd1f5f4bbf551354b38a239a6bb9)

- **作者**: Chauncey
- **时间**: 2026-11-17T07:23:29Z
- **提交信息**: [Core][Bugfix] Honor prefill_schedule_interval for prefix replay (#67879)

Signed-off-by: chaunceyjiang <chaunceyjiang@gmail.com>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [ae7048c](https://github.com/vllm-project/vllm/commit/ae7048c068d0382fc476d3afa64f6f1c63b38662)

- **作者**: linitra24
- **时间**: 2026-11-17T07:19:49Z
- **提交信息**: [CI][ROCm] Honor spawn in GPU memory waits (#68068)

Signed-off-by: linitra24 <renshuang.zhou@daocloud.io>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [3d836e1](https://github.com/vllm-project/vllm/commit/3d836e13ea80247f0f7a2a4133a63e32d379fa0f)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-11-17T07:14:08Z
- **提交信息**: [Security] Bound invalid model names in error messages (#67765)

Signed-off-by: Juan Pérez de Algaba <jperezde@redhat.com>
Co-authored-by: Codex <noreply@openai.com>

### [20d8574](https://github.com/vllm-project/vllm/commit/20d8574efbca8d3e22ab1bc497c71f31ad2a7153)

- **作者**: Matthew Bonanni
- **时间**: 2026-11-17T06:54:51Z
- **提交信息**: [Bugfix][HiSparse] Read the hot cache as flat rows in FlashMLA FP8 decode (#68014)

Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [cb55df8](https://github.com/vllm-project/vllm/commit/cb55df89d5fb27fdfca8c1edf10ac6ce07d4c09b)

- **作者**: Jade Zheng
- **时间**: 2026-11-17T06:54:44Z
- **提交信息**: [Core][spec_decode] Use device-generic streams and events in the D2H copy path (#67724)

Signed-off-by: Zheng Shoujian <zheng.shoujian@outlook.com>
Signed-off-by: jianzs <jianzs@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: jianzs <jianzs@users.noreply.github.com>

### [9e6c6b0](https://github.com/vllm-project/vllm/commit/9e6c6b007ae698bd8604620b17d5720a89169da8)

- **作者**: Leizhen Zhang
- **时间**: 2026-11-17T06:50:03Z
- **提交信息**: [Bugfix][Security] Charge sampled video frames to the request budget before decoding (#67314)

Signed-off-by: LeizhenZhang <zhangleizhen645@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [592699a](https://github.com/vllm-project/vllm/commit/592699add6b92023d7dcbce8ce788fd0dd8ba483)

- **作者**: Caldalis
- **时间**: 2026-11-17T06:47:59Z
- **提交信息**: [Recipe] Add MiniCPM-OCR 1.0 (#68078)

Signed-off-by: Caldalis <zyk_computer@163.com>
Co-authored-by: Claude Code <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [2440ffc](https://github.com/vllm-project/vllm/commit/2440ffc3870cdd6329bdf7ec0f780e05a2f01eb0)

- **作者**: Dariusz Kreft
- **时间**: 2026-11-17T06:14:11Z
- **提交信息**: [Bugfix][Attention] Use a block size only when every backend prefers it (#60892)

Signed-off-by: Dariusz Kreft <dkreft@habana.ai>
Signed-off-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [8ca7663](https://github.com/vllm-project/vllm/commit/8ca766326652caf4b8e50d1b9118d8a22f6adc73)

- **作者**: Josh Schell
- **时间**: 2026-11-17T05:57:04Z
- **提交信息**: [ROCm][CI] Install the AITER nightly's own requirements in the test image (#67986)

Signed-off-by: josh schell <josh.schell@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [ca04fba](https://github.com/vllm-project/vllm/commit/ca04fba3211d9a86d589a59b490eff3a8344aaa5)

- **作者**: Serge Panev
- **时间**: 2026-11-17T04:52:51Z
- **提交信息**: [Quantization] Support CPU offloading with online NVFP4 MoE quantization (#67136)

Signed-off-by: Serge Panev <spanev@nvidia.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Thien Tran <gau.nernst@yahoo.com.sg>

### [fe5d74d](https://github.com/vllm-project/vllm/commit/fe5d74dbfe08957fe7156c5ee09325eaf7f3e161)

- **作者**: liuzhenwei
- **时间**: 2026-11-17T04:39:31Z
- **提交信息**: [XPU][CI] Skip redundant LoRA TP4 tests on XPU (#67243)

Signed-off-by: zhenwei-intel <zhenwei.liu@intel.com>
Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [19fc89f](https://github.com/vllm-project/vllm/commit/19fc89f3d67f4f74c7a71336d21968dbebd8f6b1)

- **作者**: Yan Ma
- **时间**: 2026-11-17T04:38:15Z
- **提交信息**: [XPU] Skip test_one_sided_all2all_default_follows_dispatch_format (#68052)

Signed-off-by: Yan Ma <yan.ma@intel.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [237d474](https://github.com/vllm-project/vllm/commit/237d474518904323d7102d2d81227bc4098537c4)

- **作者**: Yan Ma
- **时间**: 2026-11-17T04:38:03Z
- **提交信息**: [XPU] Update test_inactive_default_mm_lora (#67188)

Signed-off-by: Yan Ma <yan.ma@intel.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [ccbff4e](https://github.com/vllm-project/vllm/commit/ccbff4ea102f986df1316f7608d984cd551aef1c)

- **作者**: Oliver Holworthy
- **时间**: 2026-11-17T04:34:32Z
- **提交信息**: [Bugfix] Extend --chat-template-content-format to cross-encoder scoring (#67058)

Signed-off-by: Oliver Holworthy <1216955+oliverholworthy@users.noreply.github.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [444a9f5](https://github.com/vllm-project/vllm/commit/444a9f5b39ea25e9b1e864cb4802589d518994a5)

- **作者**: Brandon Pelfrey
- **时间**: 2026-11-17T03:35:18Z
- **提交信息**: [MM] Nemotron VL: resize images and video frames on the GPU with CV-CUDA (#65941)

Signed-off-by: Brandon Pelfrey <bpelfrey@nvidia.com>
Co-authored-by: David Lesage <dlesage@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [61c3895](https://github.com/vllm-project/vllm/commit/61c3895fc937b4ffc2a59abe188959de1e459c8a)

- **作者**: Ziyang Ma
- **时间**: 2026-11-17T03:23:01Z
- **提交信息**: [XPU] Avoid unrelated package lookups on the XPU kernel index (#67877)

Signed-off-by: RyanMa29 <ziyang.ma@intel.com>

### [9929e84](https://github.com/vllm-project/vllm/commit/9929e84fd5b4a480263ed852e3c87e6d9d06c432)

- **作者**: Vinayak Gokhale
- **时间**: 2026-11-17T02:40:09Z
- **提交信息**: [ROCm] Fuse output proj to MoE topk and sort for M3.1 decode (#67072)

Signed-off-by: Vinayak Gokhale <vinayak.gokhale@amd.com>
Co-authored-by: Micah Williamson <micah.williamson@amd.com>

### [b5a2d20](https://github.com/vllm-project/vllm/commit/b5a2d209b47a700aa5e56270e0225a626f3cc0bb)

- **作者**: Lucas Liao
- **时间**: 2026-11-17T02:25:26Z
- **提交信息**: [Bugfix][ROCm][KV Connector] MoRIIO: fix port collision with TP > 1 and DP > 1 (#64574)

Signed-off-by: Lucas Liao <lliao@gimletlabs.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Codex <noreply@openai.com>

### [c4183d9](https://github.com/vllm-project/vllm/commit/c4183d9a81e627f439821ceef587df32dffda10e)

- **作者**: Oliver Yu
- **时间**: 2026-11-17T02:18:17Z
- **提交信息**: [ROCm][Perf][Qwen4Exp] Tune sparse GQA prefill profile on gfx942 and gfx950 (#62590)

Signed-off-by: Oliver Yu <tc3oliver@gmail.com>
Co-authored-by: Rony Leppänen <rony.leppanen@amd.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [0fcefcb](https://github.com/vllm-project/vllm/commit/0fcefcbcd177ba8fc7e5c41ba4ef050173e86b32)

- **作者**: freyfwt
- **时间**: 2026-11-17T02:05:52Z
- **提交信息**: [EPLB] Expose narrow state overrides for out-of-tree devices (#49700)

Signed-off-by: freyfwt <freytian1996@gmail.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [29c6cfc](https://github.com/vllm-project/vllm/commit/29c6cfc457aef4040370af43b948d8ed1ab61297)

- **作者**: Anjie Hou
- **时间**: 2026-11-17T02:02:23Z
- **提交信息**: [Perf][GDN] Export Triton prefill checkpoints via per-sequence buffers (#65186)

Signed-off-by: specture724 <specture724@gmail.com>
Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Codex <noreply@openai.com>

### [f3f0a01](https://github.com/vllm-project/vllm/commit/f3f0a014240e1e0a778728f90469cba8d15ed1bb)

- **作者**: mispa-ms
- **时间**: 2026-11-17T01:07:56Z
- **提交信息**: [Recipe] Kimi-K3.1-Pro: add the B300 AgentX disaggregated preset, align with InferenceX#5068 (#67722)

Signed-off-by: Mi Sun Park <misunp@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [3ea7fcd](https://github.com/vllm-project/vllm/commit/3ea7fcdc98380289bb496de0ffff24a2746c9c77)

- **作者**: Jee Jee Li
- **时间**: 2026-11-17T00:48:39Z
- **提交信息**: [Perf][Muse Spark] FP8 KV cache for the specialized decode (#67067)

Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [ba8412c](https://github.com/vllm-project/vllm/commit/ba8412c8a1db271809e488df3f05d33f06c43330)

- **作者**: qizixi
- **时间**: 2026-11-17T00:28:50Z
- **提交信息**: [Recipe] Kimi-K3.1-Pro: serve the Inferact/Kimi-K3.1-Pro-DSpark draft and fix the B300 baseline (#67807)

### [dbcaf2d](https://github.com/vllm-project/vllm/commit/dbcaf2dfb203b3a381b5ed1a2251b04506def979)

- **作者**: Chauncey
- **时间**: 2026-11-17T00:11:32Z
- **提交信息**: [Perf][DSV4.1] Accelerate candidate prefill and decode with CuTe (#65656)

Signed-off-by: chaunceyjiang <chaunceyjiang@gmail.com>
Co-authored-by: yeshihai <71063616+yeshihai@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [b75e225](https://github.com/vllm-project/vllm/commit/b75e225229f6c4cb460fd4da48c45cde8edca42e)

- **作者**: Kevin H. Luu
- **时间**: 2026-11-17T00:06:35Z
- **提交信息**: [Bugfix][Frontend] Don't crash beam search on an extreme length_penalty (#59506)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-11-18
**监控日期**: 2026-11-17
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7818
- **最后更新**: 2026-11-18T03:23:24Z

## 提交统计

- **昨日提交总数**: 36
- **提交者数量**: 27
- **主要提交者**: PanMing, Linze Shi, psv666

## AI分析总结

# vllm-omni 昨日提交分析总结

## 1. 主要更新类型

- **Bug修复为主**（约18条，占一半）：涉及dtype配置、资源泄漏、CUDA graph恢复、tokenizer兼容性等
- **CI/构建增强**（约10条）：ROCm任务提升为阻塞级、性能回归门禁、测试加速
- **功能新增**（约5条）：duplex副本跨节点支持、Heun采样器、实时视频输出、异步chunk
- **模型支持优化**（约3条）：MOSS-TTS基线、YuE2延迟优化、JoyAI-VL异步处理

## 2. 关键变更点与项目方向的关系

项目定位是"人人可用的多模态模型服务"（easy, fast, cheap），本次提交高度契合该方向：

- **Duplex流水线架构推进**：支持跨stage运行时和节点的duplex副本、duplex工具调用增强，直接服务于实时全双工语音交互场景
- **延迟/吞吐优化**：YuE2自动ABC+配对CFG、FlashInfer注意力选择、CUDA graph恢复，对应"fast and cheap"目标
- **多模态广度扩展**：TTS（Qwen3、IndexTTS、Voxtral、MOSS）、Diffusion视频（MiniMax H3、LTX）、多模态payload保留，体现"omni-modality"愿景
- **前端体验**：Fish Speech无缝音频流播放、CORS文档、token预算截断报告，降低使用门槛

## 3. 对项目的影响和潜在意义

- **稳定性显著提升**：大量bug修复集中在资源释放（codec模块、connector关闭、视频元数据过期）、配置正确性（设备布局检查、bfloat16硬编码），可减少生产环境的内存泄漏与崩溃
- **CI质量门禁加强**：10%性能回归强制检查、ROCm任务转为blocking、可靠性测试与故障库对齐，有助于保障多硬件（NVIDIA/ROCm）生态的质量
- **实时交互能力成熟化**：duplex相关多项变更落地，意味着项目正从"能跑"走向"生产级实时服务"

## 4. 值得关注的技术点

- **FlashInfer fa2替代cute-dsl**（SM12x自动注意力）：涉及硬件代际适配，值得关注性能回归情况
- **CHUNK_READY实时视频输出**：Diffusion请求路径的流式输出机制，对实时视频服务有示范意义
- **SM75兼容修复**（VoxtralTTS的bfloat16硬编码）：展示了对旧GPU的持续支持，降低部署门槛
- **多处借助AI协作（Claude/Cursor）**：反映社区采用AI辅助开发的趋势
- **多签名/联合署名密集**：社区协作活跃，华为、NUS、UST等多方参与

## 5. 对项目发展的影响

结合README的项目目标，这批提交显示出项目正处于**从功能扩展转向工程成熟**的阶段：基础设施（CI门禁、跨节点duplex、并发资源管理）的加固为承载更大规模的omni模态服务奠定基础；同时通过降低使用门槛的前端改进和对多种硬件/旧GPU的支持，持续践行"easy and cheap"的承诺。短期内建议关注性能基线强制执行后是否引发功能回滚，以及duplex架构演进对API兼容性的影响。

## 详细提交记录

### [a2dc592](https://github.com/vllm-project/vllm-omni/commit/a2dc592dc3625bd362380f6617edb38208096c86)

- **作者**: Harish Natarajan
- **时间**: 2026-11-17T23:16:23Z
- **提交信息**: [BugFix] Respect user specified dtype in Qwen3 TTS (#8284)

Signed-off-by: N-Harish <harishnatarajan24@gmail.com>

### [db70c77](https://github.com/vllm-project/vllm-omni/commit/db70c774d40eb0d760e0a36d555136395237b9d1)

- **作者**: Optance
- **时间**: 2026-11-17T22:33:23Z
- **提交信息**: [Frontend] Fish Speech demo: gapless AudioWorklet streaming playback (#4836)

Signed-off-by: nagelanping <xiao.yi.ming@foxmail.com>
Signed-off-by: Optance <xiao.yi.ming@foxmail.com>

### [005588d](https://github.com/vllm-project/vllm-omni/commit/005588d4a3942236af94006965a12ac63d69585b)

- **作者**: Linze Shi
- **时间**: 2026-11-17T21:06:49Z
- **提交信息**: [CI/Build] Increase duplex resume test synchronization timeout (#10480)

Signed-off-by: Linze-Shi <linzeshi0@gmail.com>

### [8a23872](https://github.com/vllm-project/vllm-omni/commit/8a23872d81ed69aa07684de19fc0bc424aba734f)

- **作者**: lm10-arg
- **时间**: 2026-11-17T20:41:38Z
- **提交信息**: [Bugfix] Close Omni connectors during runner shutdown (#10559)

Signed-off-by: lm10-arg <lm10-arg@users.noreply.github.com>
Signed-off-by: Andy Luo <43718156+andyluo7@users.noreply.github.com>
Co-authored-by: lm10-arg <lm10-arg@users.noreply.github.com>
Co-authored-by: Andy Luo <43718156+andyluo7@users.noreply.github.com>

### [33c8cc3](https://github.com/vllm-project/vllm-omni/commit/33c8cc3d3cccebf380f39876ec282c2a030c5881)

- **作者**: Linze Shi
- **时间**: 2026-11-17T20:17:41Z
- **提交信息**: [Frontend] Document and test browser CORS options (#10389)

Signed-off-by: Linze-Shi <linzeshi0@gmail.com>

### [73bdc4b](https://github.com/vllm-project/vllm-omni/commit/73bdc4b856ed4335b6272d7195d021011f673990)

- **作者**: hac17
- **时间**: 2026-11-17T20:16:31Z
- **提交信息**: [CI/Build][ROCm] Promote NIGHTLY tiny diffusion 2-GPU to blocking (#10519)

Signed-off-by: hac17 <29197483+hacZ17@users.noreply.github.com>
Co-authored-by: hac17 <29197483+hacZ17@users.noreply.github.com>
Co-authored-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>

### [ecc1578](https://github.com/vllm-project/vllm-omni/commit/ecc15781d909cbaba5abdecf5d562845c3975ca6)

- **作者**: He Yingxu
- **时间**: 2026-11-17T19:24:55Z
- **提交信息**: [Frontend] Report token-budget truncation for Qwen3-TTS, Breeze-TTS-2 and Drama 3 (#10556)

Signed-off-by: He Yingxu <28558142+YingxuH@users.noreply.github.com>
Co-authored-by: He Yingxu <28558142+YingxuH@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [7a92afd](https://github.com/vllm-project/vllm-omni/commit/7a92afde03efea84583d716221107899d7ffbd12)

- **作者**: Regina Huang
- **时间**: 2026-11-17T18:19:45Z
- **提交信息**: [Benchmark] Add MOSS-TTS-Realtime RTX 5060 Ti 16GB baseline (#10312)

Signed-off-by: regina <huang.rong@northeastern.edu>
Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: Yueqian Lin <linyueqian@outlook.com>

### [e63fe77](https://github.com/vllm-project/vllm-omni/commit/e63fe779286d82c7a28856b873113958d3592281)

- **作者**: chickeyton
- **时间**: 2026-11-17T16:48:43Z
- **提交信息**: [Core] Support duplex replicas across stage runtimes and nodes (#10422)

Signed-off-by: chickeyton <ngton2014@gmail.com>
Co-authored-by: pluviofold <45517337+xiaoyu-xyz@users.noreply.github.com>

### [a15e6eb](https://github.com/vllm-project/vllm-omni/commit/a15e6eb0a8aef5663141803952c28adb547a97da)

- **作者**: Hang Zhengyang
- **时间**: 2026-11-17T16:38:59Z
- **提交信息**: [Bugfix][Hardware][NVIDIA] Use FlashInfer fa2, not cute-dsl, for auto attention on SM12x (#10426)

Signed-off-by: Hang Zhengyang <hang.zhengyang1010@gmail.com>

### [ce3dddd](https://github.com/vllm-project/vllm-omni/commit/ce3ddddaa43cc80e32b206d20797bb7ec864ae20)

- **作者**: BeatSeat
- **时间**: 2026-11-17T16:35:35Z
- **提交信息**: [Model] Run MOSS-TTS-Realtime on Model Runner V2 (#9906)

Signed-off-by: BeatSeat <wendavid552@gmail.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [436c9fd](https://github.com/vllm-project/vllm-omni/commit/436c9fd50186a7d36e2b6943ff59c164336d4b7f)

- **作者**: hac17
- **时间**: 2026-11-17T16:33:57Z
- **提交信息**: [CI/Build][ROCm] Promote three NIGHTLY model-validation jobs to blocking (#10481)

Signed-off-by: hac17 <29197483+hacZ17@users.noreply.github.com>
Signed-off-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>
Co-authored-by: hac17 <29197483+hacZ17@users.noreply.github.com>
Co-authored-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>

### [61d3b07](https://github.com/vllm-project/vllm-omni/commit/61d3b07830750e38ccab3b69ee5e40e819852d06)

- **作者**: lm10-arg
- **时间**: 2026-11-17T16:14:49Z
- **提交信息**: [CI/Build][ROCm] Recognize quoted HIP OOM evidence (#10514)

Signed-off-by: lm10-arg <lm10-arg@users.noreply.github.com>
Co-authored-by: lm10-arg <lm10-arg@users.noreply.github.com>

### [8ab979f](https://github.com/vllm-project/vllm-omni/commit/8ab979fd79e6178ffdfe6ae9eb813df344c6ae85)

- **作者**: ZacheryAU
- **时间**: 2026-11-17T15:13:11Z
- **提交信息**: [Model] Implement full async_chunk for JoyAI-VL-Interaction (#10281)

Co-authored-by: Gao Han <hgaoaf@connect.ust.hk>

### [1c35357](https://github.com/vllm-project/vllm-omni/commit/1c3535743d171568bdb4a32423f1749a66ab4ee3)

- **作者**: wangyu
- **时间**: 2026-11-17T14:55:26Z
- **提交信息**: [CI/Build] Reduce repeated setup in Simple Test CPU coverage (#10469)

Signed-off-by: wangyu <410167048@qq.com>

### [7aa155a](https://github.com/vllm-project/vllm-omni/commit/7aa155ac21c68c944e5ffecde3a37215a643533d)

- **作者**: PanMing
- **时间**: 2026-11-17T13:51:26Z
- **提交信息**: [Bugfix] Add Chinese punctuation normalization for IndexTTS-2 (#5590)

Signed-off-by: panming <1925642328@qq.com>
Signed-off-by: xiny-spec <yxin98660@gmail.com>
Signed-off-by: Gao Han <hgaoaf@connect.ust.hk>
Co-authored-by: panming <1925642328@qq.com>
Co-authored-by: Gao Han <hgaoaf@connect.ust.hk>

### [ec46a81](https://github.com/vllm-project/vllm-omni/commit/ec46a81c9fb2254e24b4f7148ec55bf82b02b99a)

- **作者**: RK
- **时间**: 2026-11-17T13:31:09Z
- **提交信息**: [Bugfix] Exclude incomplete Higgs Audio v3 frames before codec decoding (#7942)

Signed-off-by: rk <rk@316.com>
Co-authored-by: rk <rk@316.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [800abb6](https://github.com/vllm-project/vllm-omni/commit/800abb6590e3033a1651750cd8ab33292c3fb9aa)

- **作者**: psv666
- **时间**: 2026-11-17T12:56:41Z
- **提交信息**: [Bugfix] Preserve multimodal payloads across stage-0 replicas (#10539)

Signed-off-by: psv666 <2693925048@qq.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [57046d7](https://github.com/vllm-project/vllm-omni/commit/57046d7f111c4bcde6cdcda305009169aa430433)

- **作者**: Gao Han
- **时间**: 2026-11-17T12:07:25Z
- **提交信息**: [Bugfix] Expire video job metadata with stored artifacts (#10535)

Signed-off-by: Gao Han <hgaoaf@connect.ust.hk>

### [c861579](https://github.com/vllm-project/vllm-omni/commit/c86157914e5aab089bf5022f0463ea7963972384)

- **作者**: Regina Huang
- **时间**: 2026-11-17T11:39:05Z
- **提交信息**: [Bugfix] Release unused MOSS-TTS codec modules (#10345)

Signed-off-by: regina <huang.rong@northeastern.edu>

### [76dc41d](https://github.com/vllm-project/vllm-omni/commit/76dc41d6de3f8973f6b26d1d09893973b9e1d7f8)

- **作者**: WeiQing Chen
- **时间**: 2026-11-17T10:25:04Z
- **提交信息**: [Bugfix][MiniMax-H3] Skip FastH3 checkpoint gate check when a host-weight plan owns the DiT (#10498)

Signed-off-by: WeiQing Chen <40507679+david6666666@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [fd872e0](https://github.com/vllm-project/vllm-omni/commit/fd872e0c463d1658a5d3aec262f254f88212669f)

- **作者**: Wenbo Ji　嵇文博
- **时间**: 2026-11-17T10:12:49Z
- **提交信息**: [Bugfix][Config] Check strategy device layout after stage overrides are merged (#9586)

Signed-off-by: Wenbo Ji <36562829+fusheng-ji@users.noreply.github.com>

### [0face29](https://github.com/vllm-project/vllm-omni/commit/0face299bd564c767d1814f35999507cdc96fb06)

- **作者**: Chen-Yo Sun
- **时间**: 2026-11-17T10:11:17Z
- **提交信息**: [Bugfix][VoxtralTTS] Tokenizer & LM has hardcoded torch.bfloat16 component, crashing on fp16-only GPUs (T4/sm75) (#9324)

Signed-off-by: Chen-Yo Sun <chenyo.sun@mistral.ai>

### [1d10a42](https://github.com/vllm-project/vllm-omni/commit/1d10a42442df2c9d92b0e18d9886ca29af74f05a)

- **作者**: Zhou Taichang
- **时间**: 2026-11-17T09:36:20Z
- **提交信息**: [CI/Build] Add LingBot World accuracy and performance CI (#9009)

Signed-off-by: tzhouam <tzhouam@connect.ust.hk>
Signed-off-by: Zhou Taichang <tzhouam@connect.ust.hk>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [320cf50](https://github.com/vllm-project/vllm-omni/commit/320cf50cfd30c463d5ed598d5cd08fc7eb2e37a1)

- **作者**: chickeyton
- **时间**: 2026-11-17T09:33:49Z
- **提交信息**: [Core] Duplex tool-call enhancement (#9909)

Signed-off-by: chickeyton <ngton2014@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [711e8ef](https://github.com/vllm-project/vllm-omni/commit/711e8ef32f08c6fc05b443767e5883a2ba0089da)

- **作者**: Dong1017
- **时间**: 2026-11-17T09:10:03Z
- **提交信息**: [CI/Build] Re-import DFX diffusion runner without a stale package attribute (#10523)

Signed-off-by: Dong1017 <55723162+Dong1017@users.noreply.github.com>

### [b1d6e27](https://github.com/vllm-project/vllm-omni/commit/b1d6e270e466f220fff2f48e59263c3551bfa0e6)

- **作者**: Hniii98
- **时间**: 2026-11-17T08:47:28Z
- **提交信息**: [Bugfix][Step-Audio2] Align example prompts with the upstream message format (#10191)

Signed-off-by: Hniii98 <752608928@qq.com>

### [6492091](https://github.com/vllm-project/vllm-omni/commit/6492091b4cdf64d8212e29238521177608ffdf57)

- **作者**: nodeeeeee
- **时间**: 2026-11-17T07:23:20Z
- **提交信息**: [Feature][Diffusion] Add the Heun sampler for MiniMax H3 (#10400)

Signed-off-by: nodeeeeee <zhangkai.nodeee@gmail.com>
Co-authored-by: Zhengyuan Su (苏政渊) <su.zhengyuan@u.nus.edu>

### [3eda479](https://github.com/vllm-project/vllm-omni/commit/3eda479586179b7502f7ad6e60f877f302e15558)

- **作者**: amy-why-3459
- **时间**: 2026-11-17T06:24:17Z
- **提交信息**: [Bugfix] Restore Qwen3-TTS MRv2 FULL graph replay (#10503)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [21f364d](https://github.com/vllm-project/vllm-omni/commit/21f364da9372108316df3572723be1495a9053c0)

- **作者**: psv666
- **时间**: 2026-11-17T05:50:36Z
- **提交信息**: [Bugfix] Restore Qwen3-Omni Talker FULL CUDA graphs (#10499)

Signed-off-by: psv666 <2693925048@qq.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [53092ab](https://github.com/vllm-project/vllm-omni/commit/53092ab49348b33b5e04071b4a47dd27a180e4cc)

- **作者**: Sheng GAO
- **时间**: 2026-11-17T05:23:03Z
- **提交信息**: [Diffusion] Add request-path CHUNK_READY realtime video output (#10049)

Signed-off-by: Sheng GAO <sheng.gao.dev@gmail.com>
Signed-off-by: sheng <sheng.gao.dev@gmail.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [e58c990](https://github.com/vllm-project/vllm-omni/commit/e58c990da9ac75721e1f0ee9b42b632d5cc86bd6)

- **作者**: lm10-arg
- **时间**: 2026-11-17T04:04:07Z
- **提交信息**: [CI/Build][Bugfix] Resolve LTX-2.5 Gemma4 RoPE config (#10467)

Signed-off-by: lm10-arg <lm10-arg@users.noreply.github.com>
Co-authored-by: lm10-arg <lm10-arg@users.noreply.github.com>

### [0781f0f](https://github.com/vllm-project/vllm-omni/commit/0781f0f9a9c644cd25844917fe95b16801c47b61)

- **作者**: wangyu
- **时间**: 2026-11-17T01:23:15Z
- **提交信息**: [CI/Build] Enforce 10% performance baseline regression checks (#10395)

Signed-off-by: wangyu <410167048@qq.com>

### [9e0084a](https://github.com/vllm-project/vllm-omni/commit/9e0084a13ee4f9592d926047f46fcfa87f42b19b)

- **作者**: wangyu
- **时间**: 2026-11-17T01:22:39Z
- **提交信息**: [CI/Build] Align model reliability tests with the fault-mode library (#10402)

Signed-off-by: wangyu <410167048@qq.com>
Signed-off-by: [Your Name] <your.email@example.com>

### [8dd0a9d](https://github.com/vllm-project/vllm-omni/commit/8dd0a9daa32bed4ff79cc1bb9cd8e8ff30dd60ff)

- **作者**: searlion
- **时间**: 2026-11-17T00:44:52Z
- **提交信息**: [Bugfix] Reject blank Qwen3-TTS text before it reaches the Talker (#10380)

Signed-off-by: Lewis Won <lewis.won@gmail.com>

### [72c183d](https://github.com/vllm-project/vllm-omni/commit/72c183d1619591a2fb581d79c5fa53d353daeab2)

- **作者**: Zhongqi Luo
- **时间**: 2026-11-17T00:38:54Z
- **提交信息**: [Model] Improve YuE2 latency and throughput with automatic ABC and paired CFG (#9098)

Signed-off-by: Zhongqi LUO <lzq@qiyin.ink>

---
