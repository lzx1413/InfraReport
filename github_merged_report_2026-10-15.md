# GitHub Stars 合并报告 - 2026-10-15

**合并日期**: 2026-10-16
**监控日期**: 2026-10-15
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


**报告日期**: 2026-10-16
**监控日期**: 2026-10-15
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2245
- **最后更新**: 2026-10-15T13:06:34Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 4
- **主要提交者**: YLlllllllllll, Coach257, ChibiQuest

## AI分析总结

# VeOmni 仓库昨日提交分析

## 1. 主要更新类型

以**功能新增**为主导，辅以关键**Bug修复**与**流程重构**。六条提交中四条为功能新增（离线缓存工作流、HF权重加载、MoE流式加载、NPU内核），一条为硬件适配修复（昇腾GDR修复），一条为并行策略扩展。其中第一条提交标记为 **BREAKING**，意味着对既有训练流水线存在破坏性接口变更。

## 2. 关键变更点及与项目方向的关系

- **两阶段离线缓存工作流（#1279，BREAKING）**：将数据准备与训练解耦为离线缓存阶段，重构了 trainer、data、ckpt、dist 多个模块。这直接服务于 VeOmni "扩展任意模态模型训练"的核心目标——多模态数据加载往往是训练瓶颈，离线缓存可显著提升大规模训练吞吐，代价是接口不兼容。
- **SeedOmni 兼容上游 HF checkpoint（#1300）**：打通与 HuggingFace 生态的互操作，降低用户使用门槛，利于社区采纳。
- **EP 下流式加载 DeepSeek-V4 逐专家权重（#1293）**：针对超大 MoE 模型（DeepSeek-V4），在专家并行（Expert Parallel）场景下按专家分片流式加载，避免整模型驻留内存，是 MoE 规模化训练的关键基础设施。
- **Ulysses 序列并行支持 + QSA TileLang GPU 内核（#1197）**：扩展 Qwen3.8 Flash Next 的长上下文训练能力，同时引入 TileLang GPU 算子实现。
- **DeepSeek-V4 NPU 内核与昇腾 GDR 修复（#1218、#970）**：持续加深对昇腾（Ascend）NPU 后端的算子覆盖与正确性修复。

## 3. 对项目的影响和潜在意义

短期内，BREAKING 变更会要求存量用户迁移训练配置，但离线缓存与流式权重加载将把 VeOmni 的有效训练规模上限推向新的量级。生态层面，HF checkpoint 兼容与国产硬件双路优化并行，使 VeOmni 同时具备"接入开源生态"和"自主硬件落地"两条腿。值得注意的是，多条提交由 Cursor AI 协作完成（Co-authored-by: Cursor），反映出该团队已将 AI 编程代理深度纳入分布式系统开发流程，这对需要大量繁琐内核适配的工作尤其高效。

## 4. 值得关注的技术点

- **训练任务抽象（training_task）**：离线缓存工作流以 training_task 为组织单元，可能形成一套可复现、可组合的"分布式配方"描述范式，与项目名中 "Recipe Zoo" 的定位高度一致。
- **EP 逐专家流式加载**：是 MoE 训练中 checkpoint 管理的进阶实践，值得后续关注其与断点续训、专家负载均衡的配合。
- **TileLang 与昇腾 GDR**：体现"一套配方多硬件后端"的算子抽象路线；GDR（GPU Direct RDMA 或相关直连通路）填充 lane 掩码问题属于性能与正确性交叉的底层细节，修复价值高。

## 5. 对项目整体发展的影响

结合 README 中 "Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo" 的定位，这批提交清晰勾勒出 VeOmni 当前的发展重心：一是**规模上限**——通过离线缓存、MoE 流式加载、序列并行三路并进，支撑千亿级多模态模型训练；二是**硬件广度**——GPU（TileLang）与昇腾 NPU 内核持续补齐，符合国产算力适配的战略方向；三是**易用性与生态**——HF 权重兼容降低迁移成本。总体而言，VeOmni 正从"多模态训练配方集合"演进为"覆盖数据、并行、算子、硬件的全栈训练平台"，BREAKING 重构虽带来短期迁移成本，但为长期可扩展性奠定了架构基础，值得多模态大模型训练团队重点关注其离线缓存工作流的后续文档与最佳实践。

## 详细提交记录

### [8f31dda](https://github.com/ByteDance-Seed/VeOmni/commit/8f31dda82fa309be0e856df5983502883d94789b)

- **作者**: Coach257
- **时间**: 2026-10-15T13:06:27Z
- **提交信息**: [BREAKING][omni, trainer, data, ckpt, dist] feat: add a two-stage offline-cache workflow via training_task (#1279)

### [a794543](https://github.com/ByteDance-Seed/VeOmni/commit/a794543171e4df2ddfb47510118939b94fd8be67)

- **作者**: Coach257
- **时间**: 2026-10-15T11:29:19Z
- **提交信息**: [model, omni, ckpt] feat: load SeedOmni models from upstream HF checkpoints (#1300)

### [87bca73](https://github.com/ByteDance-Seed/VeOmni/commit/87bca73bd2ca7e029644b7de7be1668dcec59228)

- **作者**: Coach257
- **时间**: 2026-10-15T10:03:12Z
- **提交信息**: [model] feat: stream per-expert DeepSeek-V4 checkpoints under EP (#1293)

### [8143e5b](https://github.com/ByteDance-Seed/VeOmni/commit/8143e5b0f3202245a95a0aef549baf57096e884d)

- **作者**: YLlllllllllll
- **时间**: 2026-10-15T09:18:02Z
- **提交信息**: [ops, ci] fix: mask padded GDR dot lanes on Ascend (#970)

Co-authored-by: Cursor <cursoragent@cursor.com>

### [4cc1f55](https://github.com/ByteDance-Seed/VeOmni/commit/4cc1f55ee959116a5ce2de11148fb5e9908869a8)

- **作者**: 顾立辉
- **时间**: 2026-10-15T09:02:31Z
- **提交信息**: [parallel, ops] feat: Support Ulysses Sp for Qwen3.8 Flash Next  & QSA TileLang GPU (#1197)

Co-authored-by: shizhelun <shizhelun@bytedance.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [76f3207](https://github.com/ByteDance-Seed/VeOmni/commit/76f32077f42ac496c2dccfb2a35a97c337e1385a)

- **作者**: ChibiQuest
- **时间**: 2026-10-15T07:32:26Z
- **提交信息**: [model] feat: add deepseek-v4 NPU kernels (#1218)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-10-16
**监控日期**: 2026-10-15
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2913
- **最后更新**: 2026-10-15T14:03:00Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 1
- **主要提交者**: Bilang ZHANG

## AI分析总结

## 昨日提交分析：ModelTC/LightX2V

### 1. 主要更新类型
- **代码重构**：简化配置与脚本
- **文档更新**：刷新双语README

昨日共两个提交，无新增功能或Bug修复，属于项目维护和优化阶段的常规工作。

### 2. 关键变更点及与项目方向的关系
- **[cc94291] 简化 Wan2.2 和 Qwen Image 的配置与脚本**：该提交对两个重要视频/图像生成模型的配置文件和运行脚本进行了简化重构。Wan2.2 是当前主流的视频生成模型，Qwen Image 则涉及图像生成方向。这一变更与 LightX2V "轻量级视频生成推理框架"的核心定位高度一致——通过减少配置复杂度，降低用户的使用门槛，使框架真正做到"Light"。
- **[0753950] 刷新双语README**：对中英文文档进行同步更新，保证国内外用户获得一致的信息，体现了项目国际化发展的战略方向。

### 3. 对项目的影响和潜在意义
- 配置和脚本的简化直接改善了**开发者体验**（DX），使新用户能够更快上手 Wan2.2 和 Qwen Image 模型的推理部署。
- 减少配置冗余也有助于**降低维护成本**，避免多份相似配置之间的不一致问题。
- README 的双语更新提升了项目的**可发现性和专业形象**，对吸引更多社区贡献者和使用者有积极作用。

### 4. 值得关注的技术点
- **Wan2.2 和 Qwen Image 的统一化**：简化配置意味着项目团队可能将两个模型的接口或参数体系进行了标准化抽象，这种模式化的设计思路如果推广到更多模型，将显著提升框架的可扩展性。
- **配置与脚本的精简策略**：在视频生成这类计算密集型场景中，配置项的精简不仅仅是"删代码"，更可能是将默认值合理化或将可变参数收敛到必要范围内，体现了团队对模型运行流程的深入理解。

### 5. 基于项目背景的发展影响
LightX2V 定位为轻量级视频生成推理框架，核心竞争力在于**高效、易用、广泛模型支持**。昨日的两个提交虽然体量不大，但精准对准了"易用性"和"社区建设"两个关键方向：重构提交让框架在模型支持层面更加简洁统一，文档提交则确保了中英文社区的信息透明。这类持续性的小步优化是开源项目走向成熟的重要标志，也为后续版本中引入更多视频生成模型（如更多版本的Wan系列或新一代模型）奠定了良好的基础设施基础。总体而言，项目正处于稳步打磨核心体验的阶段，值得关注其在模型覆盖广度上的下一步动向。

## 详细提交记录

### [cc94291](https://github.com/ModelTC/LightX2V/commit/cc9429192971815afff8368f74bd10adcc6fed48)

- **作者**: Bilang ZHANG
- **时间**: 2026-10-15T10:49:33Z
- **提交信息**: refactor: simplify Wan2.2 and Qwen Image configs and scripts (#1616)

### [0753950](https://github.com/ModelTC/LightX2V/commit/07539504958440635dd95235a6466b5f0cae6027)

- **作者**: Bilang ZHANG
- **时间**: 2026-10-15T08:02:04Z
- **提交信息**: docs: refresh bilingual READMEs (#1615)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-10-16
**监控日期**: 2026-10-15
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2301
- **最后更新**: 2026-10-15T07:56:39Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-10-16
**监控日期**: 2026-10-15
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6626
- **最后更新**: 2026-10-15T23:38:14Z

## 提交统计

- **昨日提交总数**: 12
- **提交者数量**: 5
- **主要提交者**: Anerudhan Gopal, eigen, Yanqin Zhai

## AI分析总结

# FlashInfer 昨日提交合并分析（共 12 个提交）

## 一、主要更新概览

昨日提交集中在四个方面：**Blackwell 平台性能优化**（占比最高）、**MoE 推理与训练内核迭代**、**架构重构与功能扩展**、**工程基础设施改进**。CAKE 生成式内核包是本轮迭代的绝对主线，横跨 SM100 (B200)、SM103 (GB300)、SM120 (RTX 5090/PRO 6000) 等多个 SKU。

## 二、关键变更

**后端智能调度**：优化 `auto` 后端选择策略，按 head/序列长度分区扩展 cuDNN 适用范围，在 10% 测量裕度内优先选 cuDNN——GB200 上 64K 长序列 FP32 调用从约 1950µs 降至 562µs，约 3.5× 加速，是本轮最亮眼的单项提升。

**MoE 全面提速**：多条路径同步推进。W8A8 融合内核按 (M,K) 形状在三种流水线变体间动态分发；NVFP4 路由 MoE 引入自路由 up 内核与 K-256 W2 面板布局；MNNVL all-to-all 融合量化 combine 并以 16 字节向量化合并两次 kernel launch；训练侧 Cake MoK 完成多轮不平衡感知通信拆分优化（B200 MXFP8、GB300 EP8 可选拆分）。

**架构重构**：MoE 引擎将硬编码的 cuDNN Frost 注册表替换为紧凑内核目录与四 dtype 共享模板，设备参数解析推迟到准备阶段，修复 BF16 自动调优缓存复用问题，并支持可复用 FP4 scale 缓冲区，为多精度内核扩展扫清障碍。

**其他**：kimi_k3 FP8 projection 完成第 11 轮 GEMM 调度导出并修复 TMA-store epilogue 竞态；DSv4 稀疏 MLA FP8 通过指令重排实现前导重叠；SM120 新增分页 MQA logits indexer（较 DeepGEMM 加速 1.20–1.23×）；AllReduce 新增静态 FP8 输出量化融合；topk_varlen 测试改用 `parametrize_product`，用例从 129 例精简至 113 例。

## 三、项目影响

1. **硬件覆盖持续扩张**：从数据中心 B200/GB300 到消费级 RTX 5090，巩固"全栈 GPU 推理内核库"定位。
2. **生成式内核平台加速核心化**：CAKE 通过自动化导出与系统化测量收敛到接近手工调优的性能，正转化为差异化竞争力。
3. **训练方向深入**：MoE 训练、通信拆分等内容显示项目向训练/推理混合场景延伸。
4. **架构可维护性提升**：MoE 引擎重构消除硬编码注册表，降低长期维护成本。
5. **默认保守、可选激进**的 opt-in 策略降低下游集成风险，利于生态采用。

## 四、值得关注的技术点

- **精度零容忍文化**：多个 PR 强调 bit-exact 对比与 ulp 级精度分析，指令大规模重排下数值完全不变。
- **底层竞态修复**：精准定位 TMA staging slot 在 bulk store 完成前被覆写的根因。
- **形状驱动分发**：按形状选择流水线深度与 CTA 布局，配合 `cp.async.bulk.wait_group.read 0` 异步 epilogue 减少流水线气泡。
- **融合量化**：将 MX/NVFP4 块量化与 AllReduce 静态 FP8 输出融入上游内核，避免中间张量往返。
- **API 向后兼容**：新增能力均以可选参数加默认值方式扩展。

总体而言，这批提交巩固了 FlashInfer 在 Blackwell 世代各 SKU 上的性能前沿地位，并加速生成式内核方法论从实验组件向核心资产的转化。

## 详细提交记录

### [36b9ac0](https://github.com/flashinfer-ai/flashinfer/commit/36b9ac0b9cd40a159ccee96036eed39e71103661)

- **作者**: Adrian
- **时间**: 2026-10-15T23:38:09Z
- **提交信息**: test: use parametrize_product for topk_varlen (#6383)

<!-- .github/pull_request_template.md -->

## 📌 Description

Adopt `parametrize_product` in `tests/topk_varlen/test_topk_varlen.py`
using deterministic pairwise regular cases and preserving the original
parameter assignments under `pytest --full`. Preserve coupled
configurations, test bodies, and other markers.

Collection for this file: **129 original/full cases → 113 regular
cases**.

Some test functions does not reduce the test node count by converting to
use `@parametrize_product` and `pairwise_product_cases`. But keep in
this way for future expansion of the parametrization.

## 🔍 Related Issues

Follows the regular/full parameterization approach in #5313 and #5413.

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

- Regular collection passed: 113 cases.
- Full collection passed: 129 cases; all six converted files together
retain the original 1,606 full cases.
- Parameter-matrix equivalence, pairwise coverage, unique IDs, Python
compilation, and diff checks passed.
- Pre-commit hooks passed for the changed files.
- A GPU test execution attempt stopped with `RuntimeError: No CUDA GPUs
are available`; GPU correctness must be validated in CI.

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

Converted functions:
- `test_basic_decode`
- `test_return_values`
- `test_next_n`
- `test_compress_ratio`
- `test_radix_cutlass_return_values`
- `test_radix_cutlass_next_n`
- `test_radix_cutlass_compress_ratio`
- `test_radix_basic`
- `test_radix_next_n`

Full parameter assignments were checked against the original decorators,
including grouped axes. Regular subsets retain every axis value and
every pair of axis values. Test bodies and other decorators are
unchanged. Source-defined configuration/backend inventories remain
unchanged; metadata checks used symbolic representatives for those
inventories. GPU runtime was not benchmarked.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Tests**
* Updated test case combinations across several variable-length top-k
scenarios to use a shared pairwise parameterization strategy. Declared
test values remain unchanged.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [deca0e2](https://github.com/flashinfer-ai/flashinfer/commit/deca0e2959d521fe37efffdb6074cd357e836042)

- **作者**: Anerudhan Gopal
- **时间**: 2026-10-15T23:08:06Z
- **提交信息**: perf(kda): prefer cuDNN within measured prefill latency margin (#6506)

<!-- .github/pull_request_template.md -->

## 📌 Description

`auto` restricts cuDNN to a small GB200 region and returns to slower
native kernels at 32K/64K. Wide FP32 calls also miss the persistent
backend.

Use coarse head/length regions on SM100/SM103, favoring cuDNN when its
GPU time is within 10% of the fastest valid measured backend, with an
explicit exception for GB300 wide-head BF16 calls. Retain native
math/layout checks, explicit backend overrides, and
state-pool/checkpoint handling. A supplied native workspace no longer
blocks cuDNN; cuDNN manages its own scratch, and native fallback uses
the supplied workspace.

- Local heads: few 1–16; moderate 17–64; wide 65–96.
- Sequence length: short 1K–<4K; medium 4K–<8K; long 8K–64K. K = 1024.
- FP32 wide-head calls use persistent. BF16 wide-head calls use cuDNN on
both GB200 and GB300. GB300 accepts the measured 14–15% GPU overhead
against Cake.
- Few-head FP32 calls switch to cuDNN at 4K; BF16 switches at 4K for up
to 8 heads and 8K for 9–16 heads.
- Moderate-head BF16 calls keep small-bh. Moderate-head FP32 calls use
persistent below 4K and cuDNN above it, except the GB300 8K–<16K bucket.

The first-run data covers 96 valid bounded-gate cases at H=8/12/64/96
and T=1K/4K/8K/16K/32K/64K. The measured `c29969ef` policy selected
cuDNN in 53 cases; the largest measured cuDNN overhead against the
fastest valid backend is 8.04%. The 10% limit is an offline tuning
target; GB300 wide-head BF16 is now an explicit exception.

Measured baseline → `c29969ef` auto GPU timings, in µs/call (BF16
activations, D128, one packed sequence):

| GPU | Heads | State | Tokens | Baseline auto | PR auto | PR backend |
|---|---:|---|---:|---:|---:|---|
| GB200 | 8 | FP32 | 65536 | 1950.70 | 561.97 | cudnn |
| GB300 | 8 | FP32 | 65536 | 1940.20 | 561.01 | cudnn |
| GB200 | 64 | FP32 | 4096 | 207.10 | 200.48 | cudnn |
| GB300 | 64 | FP32 | 4096 | 203.78 | 195.91 | cudnn |
| GB200 | 96 | BF16 | 8192 | 450.85 | 445.78 | cudnn |
| GB300 | 96 | BF16 | 8192 | 457.43 | 395.72 | cake |
| GB200 | 96 | FP32 | 8192 | 452.29 | 358.67 | cute-dsl-persistent |
| GB300 | 96 | FP32 | 8192 | 458.95 | 355.27 | cute-dsl-persistent |

Paired same-node runs compare the requested baseline `fd14b3056d0c` with
PR commit `c29969ef04cb`. The comparison includes intervening
main-branch changes. Each run uses 5 warmups, 30 samples, reused inputs,
state reset outside timing, and no L2 flush. GPU time is the median
summed eager CUPTI kernel duration.

| GPU | Valid paired cases | CPU speedup | GPU speedup | Graph speedup |
|---|---:|---:|---:|---:|
| GB200 | 90 | 0.887× | 1.117× | 1.190× |
| GB300 | 90 | 0.881× | 1.183× | 1.203× |

Speedup is the geometric mean of baseline/PR ratios; below 1 means
slower. CPU launch time increases by about 13% on GB200 and 14% on
GB300. This policy prioritizes GPU time.

The `c29969ef` runs selected cuDNN in 53 bounded-gate sequence cases.
The largest GPU penalty against the fastest valid explicit backend is
**9.05% on GB200** and **7.80% on GB300**; no cuDNN choice exceeds 10%.
All 53 choices also use cuDNN during graph capture with a supplied
native workspace.

[Full results, raw data, tests, and GPU
chart](https://gitlab-master.nvidia.com/agopal/flashinfer_kda_bench/-/blob/main/results/2026-10-15_c29969ef04cb_feat-kda-cudnn-auto-policy/RESULTS.md)
(NVIDIA access).

The public-call comparison can also be reproduced with the existing
benchmark, which reports host/wall and graph timing rather than summed
eager CUPTI time:

```bash
python benchmarks/bench_cudnn_linear_attention.py --family kda --lengths 65536 --heads 8 --state-dtype fp32 --backends auto,cudnn,cute-dsl --output kda-h8-t64k.json
python benchmarks/bench_cudnn_linear_attention.py --family kda --lengths 8192 --heads 96 --state-dtype fp32 --backends auto,cudnn,cute-dsl-persistent --output kda-h96-t8k.json
```

## 🔍 Related Issues

Extends the cuDNN KDA policy from #6187. Independent of the native
launch optimization in #6297.

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
- [x] All targeted tests are passing (`unittest`, etc.).

- Latest GB300 wide-head BF16 policy change: `pytest
tests/kda/test_cudnn_auto_dispatch.py -q` — **113 passed, 26 skipped**.
Local cuDNN frontend 1.29.0 does not meet the GPU tests’ 1.31
requirement. Changed-file pre-commit checks passed.
- Earlier policy: **133 passed** on a local SM100 GPU (148 SMs), PyTorch
2.13.0+cu130, CuTe DSL 4.7.0, cuDNN frontend 1.31.0.
- Covers both architecture policies on the host, real backend dispatch,
output and final-state checks, CUDA Graph replay, persistent alignment
and SM-count guards, optional runtime fallback, and explicit backend
overrides.
- Changed-file pre-commit checks passed, including mypy, Ruff
lint/format, whitespace and conflict checks. The full repository suite
and `pre-commit --all-files` were not run.
- Measured commit `c29969ef` passed **133 tests on GB200 and 133 on
GB300**, including cuDNN capture with a supplied native workspace and
native fallback capture. Lyris jobs 3353636/3353637 completed all 1,728
PR rows plus 216 paired baseline-auto rows. Statuses match the first-run
matrix; known Kimi-Linear failures remain visible. Cluster runtime:
PyTorch 2.13.0+cu132, CuTe DSL 4.7.1, cuDNN frontend 1.31.0.
- The earlier CI run failed in three SM107 MoE staging tests because the
fixture lacked `kernel`. Cherry-picked the test-only fix from #6509
(`38ae833e6`) as `91b36d76`; KDA code and benchmark results are
unchanged.
- `pytest tests/moe_ep/test_sm107_block_scaled_contracts.py
tests/moe_ep/test_sm107_torch_staging.py -q`: **128 passed** on the
local SM100 GPU, including all three previously failing CUDA capture
cases. Changed-file pre-commit checks passed.
- [Full GitHub
CI](https://github.com/flashinfer-ai/flashinfer/actions/runs/38679413398)
was restarted with `run-ci` on `91b36d76`; results are pending.

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

- GB300 BF16 state with 65–96 heads now selects cuDNN for 1K–64K tokens.
Cake remains the native fallback. Historical auto timing tables above
describe `c29969ef` before this change; explicit cuDNN measurements show
14–15% overhead against Cake. FP32 selection is unchanged.

- PTX stays explicit: its state-value bound is narrower than native auto
semantics. For GB300 moderate-head FP32 at 8K–<16K, choose persistent
because cuDNN was 16.4% slower than PTX at 8K. Persistent itself was
10.1% slower than PTX at that point.
- Auto persistent selection is restricted to one sequence with H no
greater than the SM count, so no inter-CTA handoffs or split-grid
concurrency restriction is introduced.
- Auto-selected cuDNN leaves a supplied native `prefill_workspace`
unused and owns its capture scratch. Native fallback retains the
supplied workspace. Tests cover cuDNN selection and native fallback
during capture; warm with the same arguments and stream before capture.
- No kernel math, public signature, decode dispatch, or experimental
backend was changed.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Automatic prefill selection now covers eligible single-sequence
workloads on SM100/SM103 with 128-dimensional heads, up to 96 heads, and
sequence lengths from 1K to 64K tokens. Selection accounts for state
type, head count, device, and cuDNN availability.
* If cuDNN is unavailable or declines an eligible workload, selection
can use a persistent native backend when its eligibility checks pass;
otherwise, it uses another applicable native backend.

* **Documentation**
* Clarified backend eligibility and fallback behavior, and how workspace
handling differs between cuDNN and native calls.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yang Xu <yanxu@nvidia.com>

### [09d482e](https://github.com/flashinfer-ai/flashinfer/commit/09d482e1abbd833094c597c083fa8553040c09ba)

- **作者**: eigen
- **时间**: 2026-10-15T22:46:24Z
- **提交信息**: perf(cake_mok): optimizations, B200 MXFP8 imbalance split, opt-in GB300 EP8 split (SM100a, SM103a; stacked on #6439) (#6543)

## Summary

This PR optimizes the kernels of the Cake MoK MegaMoE training step in
`flashinfer/experimental/cake_mok_bf16` (#6053). It covers forward,
recompute and backward, with BF16 and MXFP8 routed experts, on SM100a
and SM103a. Precision, correctness and the recipe do not change. The
MXFP8 recipe, FP32 accumulation and compiler flags stay as they are, and
a precision comparison against the #6439 package reads equal on all 216
rows.

The adapter has one default-behaviour change: a B200 MXFP8 row in the
imbalance split table. It also gains an opt-in fixed communication split
per device, with one GB300 MXFP8 EP8 row. See "Default behaviour" below.

#6439 merged into `main` as `af8c006ba389` on 2026-10-15. This PR is
rebased onto that `main`, so its diff against `main` now holds only this
round's commits. The rebase changed no file content: the diff against
the base is byte-identical to the one at the previous head
`ce45f719f676` (index lines aside), and `main`'s MoK files equal #6439's
head `5d89d7df1d45`.

- Head: `6ba93463939ea1e56d622d6fe5a7cc38f362ed96` (rebased; previous
head `ce45f719f676d5ad73277c9cca1cd41790d40006` had the same content)
- Base: `main` at `af8c006ba389` (the squash merge of #6439; on the MoK
files it equals #6439 head `5d89d7df1d45`)

## What changed

Commits on top of `main` (`af8c006ba389`), grouped by kind and oldest
first within each group (in the branch, `758e5a6e4` sits between
`3b994bbb5` and `0fc9f788f`).

**Kernel changes (generated sources).** None of them changes the
arithmetic. Operands, the single BF16 → E4M3 rounding, the block scales
and FP32 accumulation all stay the same.

- `27ef0656a`: paired 32-bit shared-memory loads in the MXFP8 transposed
quantizer pass of the dispatch.
- Each thread takes a row pair. Byte permutes split the words into the
bf16x2 pairs that the block quantizer consumes.
- Before, each element went through a 16-bit load, a widen to f32 and a
repack.
- `046293bcd`: the same paired transposed pass for `d_gate` / `d_up` in
the MXFP8 SwiGLU backward. `93a5d4319` builds on it.
- `031561cb7`: the BF16 kernel family is regenerated with the current
generator. BF16 device logic does not change.
- The host shims move to the form the MXFP8 families already use.
Launches go through `cudaLaunchKernelExC` with the same grid, block,
shared memory and stream. TMA box checks go through a `box_dim[]` array.
An encoder device check is added.
- The device sources gain `__launch_bounds__` / `LAUNCH_MIN_BLOCKS` and
named `SMEM_*_OFF` offsets.
- `275756e69`: the decoded task is carried across scheduler iterations.
- Before, compute CTAs decoded the next task at the bottom of an
iteration, to decide whether a cluster sync was needed, and again at the
top of the next iteration.
- Now each task is decoded once and kept as a loop variable. This
applies to the BF16 and MXFP8 backward and to the MXFP8 forward and
recompute.
- `93a5d4319`: a single runtime stage body in the MXFP8 SwiGLU backward.
- The two-stage loop was unrolled at generation time. It is now emitted
once. A runtime stage index selects the barrier slot, the phase bit and
the buffer offsets.
  - Every shared-memory access hits the same byte as before.
- `dbfb10676`: routed outputs that a later task of the same kernel
re-reads now stay L2-resident.
- The TMA stores of these outputs no longer carry the `evict_first`
hint. They are the routed GEMM outputs consumed by the SwiGLU or the
combine, in forward, recompute and backward.
- Write-once outputs, saved E4M3 tensors and weight gradients keep
`evict_first`. This is a cache-policy change only.
- `69dab37bf`: pipelined dispatch in the MXFP8 backward.
- The communication CTAs re-dispatch the next macrobatch's replayed `x`
and score-scaled `dy` with the double-buffered stream dispatch. The pull
of the next half overlaps the quantization and stores of the current
half.
- Before, this was two serial loops. Tasks, order and stores are the
same. The BF16 backward is unchanged.
- `45c64391d`: the single runtime stage body is applied to the three
stages of the MXFP8 SwiGLU forward epilogue.
- The quantizer gains a destination word offset, which is 0 for every
other caller.
  - As a result, the dispatch and backward sources change in text only.
- `3b994bbb5`: a deferred wait in the MXFP8 SwiGLU backward.
- The wait for the transposed store's shared-memory read used to come
right after the commit. It now comes just before that staging buffer is
next written.
- For a non-final stage, that point is the next stage's first barrier.
For the last stage, it is the task's final barrier.
- `0fc9f788f`: task decode without runtime integer division.
- Launch-invariant divisors become fast-divmod kernel parameters
(divisor, multiplier, shift). The host precomputes them in
`cake_mok_bf16/_kernels.py`. This applies to the BF16 and MXFP8 forward,
recompute and backward kernels.
- The launch constants of the backward decode are computed once per
launch.
  - The MXFP8 forward and recompute decode each task once.

**Adapter changes (`flashinfer/mok.py`, host only).**

- `758e5a6e4`: a B200 MXFP8 row in the imbalance split.
- `IMBALANCE_COMM_SMS` gains B200 MXFP8 → (44, 36), next to the existing
B200 BF16 row.
- The threshold becomes per precision: `IMBALANCE_THRESHOLDS` (BF16 4.0,
MXFP8 2.7), `resolve_imbalance_threshold` and
`imbalance_threshold="auto"`.
  - This changes default behaviour on B200 MXFP8. See below.
- `57c5df748`: an opt-in fixed communication split per device and EP
group size.
- Pass `fwd_num_comm_sms="auto"` and `bwd_num_comm_sms="auto"` together
(both or neither). They resolve through `resolve_comm_sms(precision,
ep_size, device)` and `COMM_SMS`, keyed by (compute capability, SM
count, precision, EP size).
- There is one row: GB300 MXFP8 EP8 → (44, 36). Everywhere else,
`"auto"` gives the factory split (40, 40).
- `ff9caca40`: fixes the SM count of the GB300 row.
- torch reports `multi_processor_count=152` for GB300 (sm_103). The row
was keyed on 160, so it never resolved. It is now keyed on 152.
- A test checks that a 160-SM key falls back to the factory split. The
README now says "GB300 (152 SMs)".
- `5f8798378`: shortens a test comment for `ruff format`.
- `3c3b4b1bb`: keeps `IMBALANCE_THRESHOLD` (the #6439 name) bound to the
BF16 threshold, so callers written against #6439 keep working.
- `a17fecc62`: swaps the operands of the new alias assertion in
`test_mok_bf16.py` (ruff `SIM300`). Test file only.
- `6ba934639`: `ruff format` of `_kernels.py` (two wrapped lines and one
blank line; whitespace only). This is what the `pre-commit` check asked
for on the first push.

**Regenerated sources.**

- Against `main` (`af8c006ba389`), the PR touches 118 files (+77169 /
−69404), the same as before the rebase.
- Most of the diff is regenerated kernel sources under
`flashinfer/experimental/cake_mok_bf16/`, with their `sources.json`
entries.
- The hand-written files are `flashinfer/mok.py`,
`cake_mok_bf16/workspace.py`, `cake_mok_bf16/_kernels.py` (the
fast-divmod carriers), `tests/experimental/test_mok_bf16.py` and the
README.
- The sm_107a sources are regenerated by the same generator. See "Not
covered".

## Default behaviour

- **There is one default change: B200 MXFP8 under imbalanced routing.**
- `imbalance_comm_sms="auto"` has been the default since #6439. With
this PR it also resolves on B200 MXFP8 (compute capability (10, 0), 148
SMs), to (44, 36), at the MXFP8 threshold 2.7.
- A step switches to (44, 36) when its hottest rank's routed load
reaches 2.7× the mean. Balanced steps never switch.
- Because the row now exists, the per-step load observation from #6439
also runs on B200 MXFP8.
  - The B200 BF16 row and the BF16 threshold (4.0) are unchanged.
- This row was measured on B200 EP8 (ABAB × 2) before it was added: four
of the imbalanced / skewed MXFP8 rows got faster (imbal, ckpt_imbal,
raggedimbal, skew4), ckpt_raggedimbal stayed in band, skew8 was
drift-gated and not read, and no row got slower. The re-validation below
runs with this default active on every B200 MXFP8 row.
- **No other device, precision or EP size has a default change.**
- GB200 (compute capability (10, 0), 152 SMs), GB300 and SM107a have no
imbalance row.
- `fwd_num_comm_sms` / `bwd_num_comm_sms` still default to the factory
split (40, 40) on every device.
- **The GB300 EP8 row is opt-in.** It applies only when the caller
passes `"auto"` for both counts. It was measured against a fixed 40 / 32
split (the split our benchmark harness uses), not against the factory
(40, 40), so it is not the default. The numbers are in the `COMM_SMS`
comment in `flashinfer/mok.py`.
- **API.**
  - The #6053 API is unchanged.
- This PR adds only optional values and helpers: `"auto"` for
`fwd_num_comm_sms` / `bwd_num_comm_sms`, `COMM_SMS`, `resolve_comm_sms`,
`IMBALANCE_THRESHOLDS` and `resolve_imbalance_threshold`.
- `imbalance_threshold` now defaults to `"auto"`. For BF16 this gives
the #6439 value, and `IMBALANCE_THRESHOLD` still names it.
- **Numerics.**
- The MXFP8 recipe is unchanged: E4M3 data, E8M0 scales, 32-element
blocks along K and the MoK scale layout.
  - Accumulation is FP32.
- Compiler flags are unchanged. The generated kernels build with the
per-kernel flags recorded in `sources.json`. These include
`--use_fast_math`, as on #6439, and this PR does not change them.
  - Repeated runs are bitwise identical.

## Correctness and tests

FlashInfer tests on cluster GPUs:

| Tree | Device | `test_mok_bf16.py` | `test_mok_bf16_tolerance.py` |
`test_mok_mxfp8.py` |
|---|---|---|---|---|
| `ff9caca40` | 1 × B200 (sm_100a) | 44 passed | 10 passed | 25 passed |
| `57c5df748` | 1 × B200 (sm_100a) | 43 passed | 10 passed | 25 passed |

The head `6ba934639` differs from `ff9caca40` by a test-file comment,
the `IMBALANCE_THRESHOLD` alias, the operand order of its assertion and
whitespace in `_kernels.py` (host and test files only; the kernel
sources and `sources.json` are byte-identical). At `3c3b4b1bb` the three
test files passed on 1 × B200 (44 / 10 / 25 passed) and `ruff check`
reported exactly one finding, `SIM300` on the new assertion, which
`a17fecc62` fixes. At `a17fecc62` on 1 × B200 (sm_100a):
`test_mok_bf16.py` 44 passed (454.8 s), `test_mok_bf16_tolerance.py` 10
passed, `test_mok_mxfp8.py` 25 passed; `ruff format --check` and `ruff
check` (pinned ruff 0.12.8) pass on `flashinfer/mok.py` and
`tests/experimental/test_mok_bf16.py`. At the head `6ba934639` on 1 ×
B200 (sm_100a): `test_mok_bf16.py` 44 passed (416.40 s),
`test_mok_bf16_tolerance.py` 10 passed, `test_mok_mxfp8.py` 25 passed;
`ruff format --check` and `ruff check` (pinned ruff 0.12.8) pass on all
four changed Python files (`flashinfer/mok.py`,
`tests/experimental/test_mok_bf16.py`,
`flashinfer/experimental/cake_mok_bf16/_kernels.py`,
`flashinfer/experimental/cake_mok_bf16/workspace.py`).

Generator-side gates on the exported package:

- **Precision:** a toy-problem comparison against the #6439 package
covers 216 rows. Every row equals the baseline (ratio 1.0).
- **Reproducibility:** regenerating the package from a fresh clone of
the generator reproduces it byte-for-byte.
- **End-to-end and unit suites:**
- sm_100a: end-to-end suite (`-k mok`) 20 passed; unit suite 50 passed /
2 skipped.
- sm_103a: end-to-end suite 20 passed; unit suite 50 passed; rendered
sources compare 48/48 exact.
- **compute-sanitizer:** `synccheck` and `memcheck` on four EP4 toy
cases (BF16, MXFP8, each with uniform and 4× skewed routing) report 0
errors. On B200 they ran on the L8b export that `0fc9f788f` commits
(same kernel sources and `sources.json` as this head). On GB300 they ran
on the frozen stack (4/4).

Bot run: `@flashinfer-bot run tests/experimental/test_mok_bf16.py
tests/experimental/test_mok_bf16_tolerance.py
tests/experimental/test_mok_mxfp8.py`. The first request (16:52Z, at
pre-rebase head `54e3d0563`) started run 38772713195, which the
`ce45f719f` push cancelled after its H100 targeted unit test had passed.
The run was re-requested at 17:25Z on `ce45f719f` (comment 6198134564);
flashinfer-bot acknowledged it and ran PR Test run 38777329177
(https://github.com/flashinfer-ai/flashinfer/actions/runs/38777329177),
which completed with conclusion success: Targeted Unittest (H100), all
six AOT Build Import jobs (x64 / arm64 × cu129 / cu130 / cu134) and Test
Results Summary passed; the `ci/test-scope-1` check for the three MoK
test files reads pass. After #6439 merged, the branch was rebased onto
`main` (`af8c006ba389`) with no content change (head `6ba934639`) and
the run was requested again at 21:17Z (comment
https://github.com/flashinfer-ai/flashinfer/pull/6543#issuecomment-6202464622);
flashinfer-bot ran PR Test run 38808739963
(https://github.com/flashinfer-ai/flashinfer/actions/runs/38808739963)
on `6ba934639`, which completed with conclusion success: Permission
Check, Setup, Targeted Unittest (H100) and all six AOT Build Import jobs
passed.

## Performance

**Protocol.**

- A is the #6439 tree at `28df319b5`. `5d89d7df1d45` changed only the
adapter afterwards (the `histc` load count and the SM-keyed imbalance
table); its kernels are identical to `28df319b5`. B is this PR. The B200
rows are the same as in #6439's tables; the GB300 EP8 two-node set (10
rows) is new in this round.
- Each row runs A, B, A, B on the same GPUs, which gives two rounds.
Each row is read on the two-round mean of (B − A) / A:
  - faster: both rounds negative and mean ≤ −0.6 %;
  - slower: both rounds positive and mean ≥ +0.6 %;
  - band: everything else (±0.6 pp).
- An in-process MoK #17 arm is the drift control. A row is not read if
its MoK #17 time moves by more than 1.2 % between A and B; it is then
re-measured.

**B200 EP8** (one node, 8 × B200)

| Row set | Rows | Result |
|---|---|---|
| Core set | 9 | 4 faster (the four MXFP8 defaults rows: ckpt −3.4 %,
ckpt_mb393216 −3.6 %, full −3.4 %, full_mb393216 −3.2 %), 5 band, 0
slower |
| BF16 routing variants | 8 | 3 faster (ckpt_imbal −0.65 %, full_imbal
−0.71 %, full_skew2 −0.61 %), 5 band, 0 slower |
| MXFP8 routing variants | 9 | 9 faster (−2.2 … −7.8 %), 0 slower.
`full_imbal` was re-measured on a fresh lease after a drift-gated round:
−6.39 % (−6.36 / −6.43). |
| Skew-8 pair (BF16, MXFP8) | 2 | MXFP8: faster (−8.48 %, −8.43 /
−8.52). BF16: band (−0.22 %, +0.18 / −0.61; re-measured on a fresh lease
after a drift-gated first run). |
| All rows | 28 | 17 faster, 11 band, 0 slower. Geometric mean −2.56 %.
MXFP8 rows −2.2 … −8.5 %. |

**B200 EP4**

| Row set | Rows | Result |
|---|---|---|
| Core set | 9 | 4 faster (−3.8 … −4.3 %), 5 band, 0 slower |
| BF16 routing variants | 8 | 2 faster, 6 band, 0 slower |
| Skew-8 pair (BF16, MXFP8) | 2 | BF16: band (+0.34 %). MXFP8: faster
(−6.63 %, re-measured after a drift-gated first run). |
| MXFP8 routing variants | 9 | 9 faster (−3.6 … −6.4 %), 0 slower |

Band rows with one round above +0.6 %:

| Row | Round 1 | Round 2 |
|---|---|---|
| B200 EP4 `bf16_full_cap2` | +0.75 % | +0.15 % |
| B200 EP4 `bf16_full_skew4` | +0.27 % | +0.63 % |
| B200 EP4 `bf16_full_skew8` | −0.53 % | +1.20 % |
| B200 EP8 `bf16_full_skew4` | −0.53 % | +1.65 % |

Band rows with one round below −0.6 % (the verdict stays band because
the two-round mean is above −0.6 % or the two rounds differ in sign):
B200 EP4 `bf16_full_ragged` (−0.51 / −0.65); B200 EP8
`bf16_ckpt_mb393216` (−0.68 / −0.35), `bf16_full_raggedimbal` (+0.26 /
−0.63), `bf16_full_skew8` (+0.18 / −0.61).

**GB300 EP4**

| Row set | Rows | Result |
|---|---|---|
| All rows | 28 | 15 faster, 13 band, 0 slower. Geometric mean −2.99 %.
MXFP8 rows −4.5 … −6.9 %. |

**GB300 EP8** (two nodes)

| Tree | Rows | Result |
|---|---|---|
| `57c5df748`: kernel changes only (the GB300 row was keyed on 160 SMs
and did not resolve) | 10 | 5 faster (MXFP8, −3.8 … −7.7 %), 5 band, 0
slower |
| With the 152-SM fix, `"auto"` resolving to (44, 36) | 10 | 5 faster
(all MXFP8: defaults −3.83 %, ckpt −4.02 %, imbal −8.53 %, skew4 −10.35
%, skew8 −11.01 %), 5 band (all BF16), 0 slower |

**Memory.** On every row measured so far, B's context and peak memory
equal A's (0.01 GiB resolution).

**Distance to a hardware lower bound.**

- The ratio is B's step time divided by a per-row lower bound.
- The bound is the slowest rank's maximum of MMA, HBM and NVLink time at
measured achievable peaks. Every row is MMA-bound.

| Configuration | Rows covered | Geometric mean of step time / bound |
|---|---|---|
| B200 EP8 | 28 | 1.71 |
| B200 EP4 | 28 | 1.73 |
| GB300 EP4 | 28 | 1.66 |
| GB300 EP8 (two nodes) | 10 | 1.68 |

Design doc and tactics for this round: Cake docs MR
https://gitlab-master.nvidia.com/averyh/r94494673bb0150eeffa896f7/-/merge_requests/1481
(branch `averyh/cake-1105-r4-docs` @ `3105bba3ea86`; this is the branch
rebased onto `mok-bf16-rubin-weave` after docs MR !1424 merged, with the
same content as `ddd0f21db18f`, which merges into
`mok-bf16-rubin-weave`; that branch reaches `main` through Cake MR
!1155).

## Validation status

- All 94 performance rows are measured: B200 EP8 28, B200 EP4 28, GB300
EP4 28, GB300 EP8 (two nodes) 10. No row is slower by the two-round
mean. Memory (context and peak) is equal to the baseline in every cell.
- The tests and gates listed above ran at the commits named next to
them. Commit hashes in this description are those of the rebased branch;
the pre-rebase heads were `54e3d0563` (v5) and `ce45f719f` (v6), with
identical file content. The B200 result quoted for `a17fecc62` was
measured at its pre-rebase twin `54e3d0563`, and the v6 head result
(tests + ruff on all four changed Python files) at `ce45f719f`. The same
B200 test chain was re-run on the rebased head `6ba934639` (NSC lease
2268227, 1 × B200, 2026-10-15 21:52Z): `test_mok_bf16.py` 44 passed,
`test_mok_bf16_tolerance.py` 10 passed, `test_mok_mxfp8.py` 25 passed;
`ruff format --check` and `ruff check` (0.12.8) pass on the four changed
Python files.
- `@flashinfer-bot` run on this PR: The first request (16:52Z, at
pre-rebase head `54e3d0563`) started run 38772713195, which the
`ce45f719f` push cancelled after its H100 targeted unit test had passed.
The run was re-requested at 17:25Z on `ce45f719f` (comment 6198134564);
flashinfer-bot acknowledged it and ran PR Test run 38777329177
(https://github.com/flashinfer-ai/flashinfer/actions/runs/38777329177),
which completed with conclusion success: Targeted Unittest (H100), all
six AOT Build Import jobs (x64 / arm64 × cu129 / cu130 / cu134) and Test
Results Summary passed; the `ci/test-scope-1` check for the three MoK
test files reads pass. After #6439 merged, the branch was rebased onto
`main` (`af8c006ba389`) with no content change (head `6ba934639`) and
the run was requested again at 21:17Z (comment
https://github.com/flashinfer-ai/flashinfer/pull/6543#issuecomment-6202464622);
flashinfer-bot ran PR Test run 38808739963
(https://github.com/flashinfer-ai/flashinfer/actions/runs/38808739963)
on `6ba934639`, which completed with conclusion success: Permission
Check, Setup, Targeted Unittest (H100) and all six AOT Build Import jobs
passed.
- Not measured: VR200 (sm_107a) rows. That node was unreachable during
this round.

## Not covered

- **SM107a:** the sm_107a sources in this PR are regenerated by the same
generator. We had no SM107a hardware this round, so they were not
measured or tested.
- **GB200:** we did not measure GB200. Neither split table has a GB200
row, so on GB200 only the kernel changes apply.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added automatic imbalance-threshold selection by precision: 4.0 for
BF16 and 2.7 for MXFP8.
* Added automatic fixed communication-split selection using measured
device and group-size settings, with a fallback when no matching setting
is available.
* Added B200 MXFP8 measurements and documented supported GB300 MXFP8 EP8
measurements.
* **Performance**
* Optimized task and column indexing across forward, recompute, and
backward operations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [73437da](https://github.com/flashinfer-ai/flashinfer/commit/73437da87c5d80b1f4903e513f526c310a3133ca)

- **作者**: eigen
- **时间**: 2026-10-15T21:39:03Z
- **提交信息**: perf(cake_kimi_k3_fp8_projection): round 11 — static / grid-stride GEMM schedules, PDL-after-weights loader, 19 table adoptions (SM100a, SM103a) (#6552)

## Summary

This is round 11 of the Cake `kimi_k3_fp8_projection` generated-program
export: the FP8 block-scaled projection GEMMs of the Kimi-K3 KDA / MLA
families, on SM100 (B200) and SM103 (GB300).

The contract has not changed:
- 352 rows per GPU.
- 198 perf rows: 22 (N, K) families × M in {1, 8, 64, 256, 512, 1024,
2048, 4096, 16384}.
- 154 correctness rows: M 3 / 129 / 513 / 1000 / 1023 / 1025 / 4097,
with strided views.

The round builds on the round-10 package on FlashInfer main `ea5f7409`
(#6433). That package is the "record" for every comparison below.

What this PR adds:
- Three GEMM schedule forms.
- A fix to the TMA-store epilogue of the GEMM producer. The epilogue
could rewrite a staging slot before the bulk store that last read it had
completed. This was the root cause of the wrong output that round 10
found for the 192-wide tile with the two-stage / four-slot TMA store.
Details are under Exactness.
- 19 dispatch-table adoption entries: 9 on SM103 and 10 on SM100. That
is 25 cell adoptions per GPU (24 distinct cells on SM103, 22 on SM100; a
few cells were adopted in more than one step). The two newest entries
adopt the 192-wide tile on `12,1,16384`, one on each GPU. The kernel fix
made them possible.
- The host-mirror keys that select the new forms.
- A fix to the exported host's launch arguments for the grid-stride
form. The FlashInfer target test found this defect before the sealed
export of the delivered package: every delivered seed and full result
was measured on the final tip, which contains the fix. One earlier seed
export on a superseded tip (7 rows, none of them a `_gs` cell) ran
before the diagnosis and is not part of the delivered results.

Every adopted cell is bit-exact against the record except one Tier A′
cell on SM100 (`56,48,1024`).

- **New GEMM schedule forms.** All three are Weave programs and all are
Tier A: the per-element MMA order and the epilogue are the record's.
- **PDL wait after the weights, `_pdlb`.** The table key is `gemm_pdlb`.
The exporter token is `_pdlb`, the last stem token before `_pf<D>`.
- Problem: in the record GEMM, the load role runs `griddepcontrol.wait`
before its first TMA box. The first-stage weight boxes (B / SFB) do not
depend on the quantization kernel, but they still wait for it.
- Change: `_pdlb` issues B / SFB first, runs one predicated
`griddepcontrol.wait`, and then issues A / SFA. Later ring iterations
issue B then A with no wait. This is the order the decode kernel already
uses.
- Scope of the change: only the issue order of two independent TMA loads
and the position of one wait. The render census shows every record
program unchanged, and each `_pdlb` twin differs only in load-role
lines.
- Timing: the export protocol measures the per-replay GPU span, from the
first kernel's start to the last kernel's end, so PDL overlap shows up
in its timings.
- Result: screened on the 76 (SM103) / 77 (SM100) GEMM-route rows, with
one adoption.
- **Static one-tile schedule `_st`.** The table key is `gemm_static`.
The instances are `gemm_tstore_n192_k128_st` and
`gemm_rstaged_n192_k128_st`.
- Problem: when the tile count T is at most the resident pair count P
(74 on SM100, 76 on SM103), every pair owns exactly one tile. The record
still allocates the CLC work ring, traces `clc_response` /
`clc_try_cancel`, and polls for a tile that never comes.
- Change: `_st` drops that scheduling code. It is admissible only when T
≤ P. A table cell that asks for `gemm_static` on a launch with T > P is
refused by both hosts (ValueError), never routed around; only Cake's A/B
env knob `LOOM_KIMI_GEMM_STATIC` is a no-op (off) there.
- **Static grid-stride schedule `_gs`.** The table key is `gemm_gs`; an
example instance is `gemm_tstore_k128_gs`.
- Schedule: pair p takes tiles p, p + P′, p + 2P′, …. The grid is 2 ·
min(T, P′), and there is no work ring.
- Correctness of the mapping: (p, i) → p + iP′ is a bijection onto [0,
T). A CPU unit test checks this for every contract (T, P′).
- The host asserts P′ ≤ `cuOccupancyMaxActiveClusters` and raises if it
does not hold. It never falls back.
- Trade-off: `_gs` gives up CLC's dynamic rebalancing of per-tile
jitter. In exchange, the loader can issue tile i+1's first stage without
waiting for a CLC response.
    - `_st` is `_gs` with one tile per pair.
- **Existing forms combined in new ways and now dispatched:**
- `gemm_tstore_n192_k128_skf_pf1` on SM100 (`56,48,1024`,
tp1:o_proj:1024; new to the sm_100a plan at C22 — render census +1
instance, export keys 81 → 82). That cell's intermediate
`gemm_tstore_n192_k128_skf` form (C17 to C22) is no longer dispatched
there, and the plain `gemm_tstore_n192_k128_skf` program is not new on
SM100: it was already the record program of `5,28,16384`
(tp1/tp8:kv_a:16384).
- `gemm_tstore_n192_s2_ts4` on SM103 `96,1,512`, SM103 `12,1,16384` and
SM100 `12,1,16384` (kernel-symbol order `tstore_s2_ts4_n192`), with the
fixed TMA-store epilogue. See the kernel fix under Exactness.
  - The 384-wide pair tile on four more M = 16384 cells.
- The decode `qwarps 16` instance
`decode_t64_p2_fused_w16_r2_xh_q8_cs4_xp`.
- The decode `pw 2` instances, for example `decode_t16_p4_pw2` on SM100.
- **Dispatch-table convergence (strict two-clean-pass rule, both
GPUs).**
- The runtime-catalog pass (every runtime-selectable lever, decode and
GEMM) was re-run on the adoption trees between build units: passes 1 and
2 on the 77 runtime-catalog rows; pass 3 on 120 SM103 / 118 SM100 rows
(the catalog plus coverage additions); pass 4 on every row still open at
C18, 125 SM103 / 134 SM100. The tail passes 6-9 covered every
non-class-A row: 191 on SM103 and 194 on SM100 (38 / 37 of them lie
outside the catalog and borrow the nearest same-module arm list).
- Screen settings: 3 rounds × 1000 cold-L2 CUDA-graph replays, node
alone, 4 GPUs, bar 1.015.
  - Every hit was confirmed by one of two protocols:
- **R8-3**, for rows above 20 us: node alone; quiet single arm ≥ 1.0;
two shared runs, each ≥ 1.015; the A/A arm and the `WAIT_TICKS=0` no-op
twin within [0.99, 1.01]; bit-exact.
- **S5 v2**, for rows below 20 us: interleaved, 3 × 1000; every round ≥
1.015; A/A in band; bit-exact.
- If a hit lands on a (row, arm) whose program is unchanged since an
earlier confirm verdict, that verdict is reused.
  - Pass history:
    - Full passes 1–4 each ended in adoptions.
- Pass 5 was a targeted closure pass of 12 rows / 61 arms and does not
count.
- Full passes 6 and 7 were clean on both GPUs. Pass 6 covered 191 rows /
2085 arms on SM103 and 194 rows / 2125 arms on SM100; pass 7 covered 191
rows / 1911 arms on SM103 and 194 rows / 1958 arms on SM100 (arm counts
include the `WAIT_TICKS=0` twin; pass 7 reused the pre-augment pass-6
spec, so it omitted the 174 / 167 route-coverage donor arms added for
pass 6). They no longer count. The `12,1,16384` adoption that followed
the kernel fix reset the count.
- Full passes 8 and 9 used pass 7's screen spec unchanged. Pass 8 ran on
the adoption commit. Pass 9 ran on a later commit with the same exported
program set.
- Passes 8 and 9 were clean on both GPUs: 191 rows on SM103 and 194 rows
on SM100, 3 × 1000 cold-L2 graph-replay samples per arm, node alone.
Every hit ≥ 1.015 was either carried by a prior node-alone verdict or
re-measured node alone and found below the bar:
- Pass 8, SM103: 8 hits. 6 were carried. S5 v2 confirms on 3 rows all
failed.
- Pass 8, SM100: 38 hits. 30 were carried. 4 R8-3 candidates and 3 S5 v2
rows were re-measured, and none passed.
- Pass 9, SM103: 8 hits. 5 were carried. S5 v2 confirms on 3 rows all
failed.
- Pass 9, SM100: 41 hits. 33 were carried. 2 R8-3 candidates and 2 S5 v2
rows were re-measured, and none passed.
- Screen readings of 1.03–1.05, mostly on `PW=1` arms, fell to
0.995–1.017 in the interleaved S5 v2 confirms of passes 3 and 4 (node
alone, like the screens), every row below the 1.015 bar in at least one
round. The highest single rounds were 1.01668 on tp1:f_b:512 `GEMM_PF=2`
and 1.01587 on tp8:o_proj:64 `PW=1`, both in the pass-4 confirm; the
recorded verdict ratios (minimum round) were 0.9946–1.0119. Passes 3, 4,
6 and 7 showed the same pattern.
- Convergence is met on both GPUs: two consecutive clean full passes
under the round-11 catalog.
- Final state, measured against the round-10 sealed floors (class A = ≤
1.10× the clock-normalized floor):
- SM103: class A 7, all applicable levers closed on 191 rows (by
same-GPU measurement or an evidenced bound), open 0.
    - SM100: class A 4, closed 194, open 0.
- The SM100 pass-7 screen was noisy: its own controls read
0.9548–1.0427. It was resolved only on node-alone evidence. 30 hit pairs
reused prior verdicts on unchanged cells, and 9 pairs were confirmed
again with controls in band. Nothing was adopted from it.
  -   - Three confirm flips are recorded as flips:
    - SM103 `56,48,16384`: the first confirm had out-of-band controls.
- SM103 `96,1,1024` stages 2 / slots 4: it failed S5 v2 in round 10 and
in pass 1, then passed in pass 2.
- SM103 `56,48,2048` `gemm_bk 128`: the first R8-3 read 1.0162 / 1.0118
/ 1.0121, both shared rounds below the 1.015 bar, so it was not adopted;
the R8-3 re-confirm about 15 minutes later on another node (step
6280ab29 submitted 06:52:03Z vs step 4ae5004a 06:36:34Z; its verdict
landed 06:56:31Z, 10 minutes after the first at 06:46:36Z) read 1.0184 /
1.0204 / 1.0197 and was adopted. This is the "one R8-3 re-confirm at
1.020" in the grid-stride group below.
    - SM103 `56,48,16384`: the first confirm had out-of-band controls.
- SM103 `96,1,1024` stages 2 / slots 4: it failed S5 v2 in round 10 and
in pass 1, then passed in pass 2.
- **Dispatch-table adoptions, SM103 (GB300).** How to read the numbers:
- Ratios are production / candidate at the adoption tip, paired on the
same GPU; > 1 means faster.
- A triple is the three confirm readings: quiet, shared 1, shared 2 for
R8-3; rounds 1–3 for S5 v2.
  - us values are confirm-run candidate medians.

  Adoptions:
- **PDL order:** `50,28,1024` `gemm_pdlb 1` (tp8:in_proj_qkvgfab:1024):
42.624 → 39.088 us. R8-3 1.0213 / 1.0237 / 1.0238, controls
0.9992–1.0024.
- **Grid-stride, first group.** The confirms for this group were S5 v2
PASS on four cells, with the `_gs` arm paired against a same-form
control without `_gs`, plus one R8-3 re-confirm at 1.020.
    - `96,1,2048` `gemm_gs 1` + `gemm_bk 128` (tp1:f_b:2048): 15.84 us.
    - `12,1,4096` `gemm_gs 1` (tp8:f_b:4096): 9.088 us.
- `24,2,2048` `gemm_gs 1` + `gemm_bk 128` (tp8:kv_b:2048): 10.464 us.
    - `24,2,1024` `gemm_gs 1` + `gemm_bk 128` (tp8:kv_b:1024): 8.8 us.
    - `56,48,2048` `gemm_bk 128` (tp1:o_proj:2048): 112.144 us.
  - **Grid-stride, later adoptions (S5 v2 PASS):**
- `12,1,2048` `gemm_bn 192` + `gemm_bk 128` + `gemm_gs 1`
(tp8:f_b:2048): 8.96 → 7.84 us.
- `18,6,2048` `gemm_bk 128` + `gemm_gs 1` + `quant_units 2`
(tp8:q_b:2048): 14.56 → 13.632 us.
  - **192-wide tile:**
- `56,48,512` `gemm_bn 192` (tp1:o_proj:512): R8-3 1.083 / 1.091 /
1.092.
    - `56,6,512` `gemm_bn 192` (tp8:o_proj:512): S5 v2 1.070 × 3.
- `56,48,1024` `gemm_bn 192`, dropping the cell's stale `gemm_sk`
(tp1:o_proj:1024): 1.023 / 1.018 / 1.020.
- `96,1,512` `gemm_bn 192` + `gemm_stages 2` + `gemm_ts_slots 4`
(tp1:f_b:512): 9.66 → 9.056 us. S5 v2 1.028 / 1.032 / 1.028, A/A 1.0 ×
3. Confirmed again on the fixed program, node alone: S5 v2 1.03014 /
1.03559 / 1.03203, A/A 1.0 × 3, bit-exact.
- `12,1,16384` `gemm_bn 192` (tp8:f_b:16384), after the kernel fix, Tier
A: 16.512 → 16.256 us. S5 v2 1.01575 / 1.01772 / 1.01575, A/A 1.0 /
1.00194 / 0.99994, bit-exact.
  - **R8-3 on three cells,** two of them WIN2 (both shared runs ≥ 1.02):
    - `56,48,1024` `gemm_pf 1`, on top of the 192-wide tile (59.712 us).
    - `96,28,2048` `gemm_bk 128` (tp1:q_proj:2048): 106.752 us.
- `12,28,4096` `gemm_bn 192` + `gemm_bk 128` (tp8:q_proj:4096): 47.648
us.
  - **K-tile and stage / slot:**
- `384,28,2048` `gemm_bk 128` (tp1:fused_qkvg:2048): 406.944 → 399.713
us. R8-3 1.0161 / 1.0186 / 1.0176.
- `50,28,16384` `gemm_bk 128` (tp8:in_proj_qkvgfab:16384): 476.608 →
466.353 us. R8-3 1.0238 / 1.0218 / 1.0222.
- `96,1,1024` `gemm_stages 2` + `gemm_ts_slots 4` (tp1:f_b:1024): 11.328
us. S5 v2 1.0226 / 1.0198 / 1.0226; this is the flip noted above.
  - **M = 16384:**
    - `144,6,16384` `gemm_gm 64` (tp1:q_b:16384): 1.026 / 1.025 / 1.026.
- New cell `96,28,16384` `gemm_bn 384` (tp1:q_proj:16384): 803.792 us,
1.019 / 1.017 / 1.018. SM100 gets an explicit record twin of this cell.
- `56,48,16384` `gemm_bn 384` (tp1:o_proj:16384): 870.176 us. The R8-3
re-confirm read 1.036 / 1.033 / 1.035. The first confirm (shared 1.036 /
1.025) was voided because its controls were out of band (1.0126 /
0.987).
  - **Decode:**
- `384,28,1` persistent CTA count 128 (tp1:fused_qkvg:1): 1.025 / 1.025
/ 1.024.
- `1,28,2048` `qwarps 16` (tp1 / tp8 b_proj:2048 and f_a:2048): S5 v2
1.0405 × 3, A/A 1.0.
- `192,2,64` `pw 2` (tp1:kv_b:64): 8.256 us. S5 v2 1.0233 / 1.0194 /
1.0194.
- **Dispatch-table adoptions, SM100 (B200).** The numbers read the same
way as for SM103.
  - **Static one-tile:**
- `12,1,2048` `gemm_static 1` (tp8:f_b:2048): 8.256 → 7.936 us. S5 v2
1.04032 × 3, A/A 0.99614 × 3.
- `50,28,512` `gemm_static 1` (tp8:in_proj_qkvgfab:512): 28.096 → 27.616
us. R8-3 1.008 / 1.0174 / 1.0174.
- **Grid-stride and K-tile, one adoption entry.** Its confirms, which
also cover the Tier A′ cell below: R8-3 on 5 cells, shared 1.017–1.068;
S5 v2 on 6 cells, 1.025–1.076, A/A in band.
- `17,28,2048` `gemm_bk 128` + `gemm_gs 1` (tp1 / tp8 fused_qkv_a:2048):
35.488 us.
    - `56,6,2048` `gemm_gs 1` (tp8:o_proj:2048): 26.592 us.
    - `96,1,2048` `gemm_bk 128` + `gemm_gs 1` (tp1:f_b:2048): 16.096 us.
    - `12,1,4096` `gemm_gs 1` (tp8:f_b:4096): 9.408 us.
- `24,2,1024` / `24,2,2048` / `24,2,4096` `gemm_bk 128` + `gemm_gs 1`
(tp8:kv_b): 9.056 / 10.72 / 14.848 us.
- `56,6,512` `gemm_bk 128` + `gemm_gs 1` (tp8:o_proj:512): 13.344 us.
    - `192,2,2048` `gemm_bk 128` (tp1:kv_b:2048): 32.416 us.
    - `50,28,2048` `gemm_bk 128` (tp8:in_proj_qkvgfab:2048): 74.272 us.
- **Grid-stride, later:** `192,2,512` `gemm_bk 128` + `gemm_gs 1`
(tp1:kv_b:512): 14.496 us. S5 v2 1.020 / 1.018 / 1.018.
  - **192-wide tile with the stream-K fix-up kept (Tier A′):**
- `56,48,1024` `gemm_bn 192` becomes `gemm_tstore_n192_k128_skf`
(tp1:o_proj:1024): 74.85 → 70.11 us. The screen read 1.068 and was not
bit-exact; the rule-5 packet passed.
- Then `gemm_pf 1`, giving `gemm_tstore_n192_k128_skf_pf1`: 70.112 →
68.816 us. R8-3 1.0195 / 1.0188 / 1.0181, controls 0.9991–0.9995,
bit-exact against the Tier A′ program.
- **192-wide tile on the two-stage / four-slot TMA-store cell, after the
kernel fix (Tier A):**
- `12,1,16384` `gemm_bn 192` on the cell's two-stage / four-slot TMA
store (tp8:f_b:16384), giving `gemm_tstore_n192_s2_ts4`: 17.952 → 17.536
us. S5 v2 1.02372 / 1.02367 / 1.02372, A/A 1.0 × 3, bit-exact.
    - This adds `gemm_tstore_n192_s2_ts4` to the SM100 plan.
  - **384-wide tile on the power-capped pair:**
- `384,28,16384` `gemm_bn 384` (tp1:fused_qkvg:16384): 4201.232 us. R8-3
1.021 / 1.028 / 1.024.
- `386,28,16384` `gemm_bn 384` (tp1:in_proj_qkvgfab:16384): 4252.191 us.
R8-3 1.013 / 1.020 / 1.020.
- These rows run at 1170 MHz under the power cap. In the clock-traced
screen the gain is a clock gain: time ratio 1.0210 at clock ratio 1.0188
(fused_qkvg) and 1.0278 at 1.0385 (in_proj_qkvgfab).
  - **K-tile, prefetch and stage / slot:**
- `17,28,16384` `gemm_bn 192` + `gemm_bk 128` (tp1:fused_qkv_a:16384):
R8-3 1.0153 / 1.0168 / 1.0169.
- `18,6,4096` `gemm_pf 1` (tp8:q_b:4096): R8-3 1.009 / 1.0167 / 1.0167.
`gemm_bk 128` was added later (20.768 us).
- `96,1,1024` `gemm_stages 2` + `gemm_ts_slots 4` (tp1:f_b:1024): S5 v2
1.01795 / 1.02043 / 1.02051. `gemm_bk 128` was added later (11.744 us).
- Confirms of the two later `gemm_bk 128` additions: R8-3 1.0168 /
1.0185 / 1.0185 and S5 v2 1.061 / 1.063 / 1.060.
  - **Decode:**
- `1,28,2048` `qwarps 16`: 15.168 us. S5 v2 1.036–1.042 in every round.
- `18,6,64` `pw 2` (tp8:q_b:64): 7.14 → 6.72 us. S5 v2 1.02336 / 1.02336
/ 1.02351, then 1.02381 × 3 when confirmed again. `pw 1` failed at
1.01389 / 1.01415.
- **Measured but not shipped.** Each of these was measured on the same
GPU, and none is dispatched:
- **Fused quantization inside the GEMM producer (`_fq2`, TMA-staged).**
On tp1:kv_a:4096 the best variant took 49.312 us against the 34.304 us
two-launch chain on SM103, and 54.048 us against 37.376 us on SM100.
That is about 0.8 us of quantizer time per 128-K block. Every arm was
bit-exact.
  - **`_st` on the kv_a:4096 rows:** 1.0023–1.0087.
- **Exact part-split accumulator ring `_a3h`:** best 1.0004 on SM100 and
1.0028 on SM103.
- **Decode X-side multicast:** best 1.0087 on SM103 and 0.9671 on SM100.
- **`cta_group::2` pair weight stream for M = 64:** 0.90–0.91 on SM100.
  - **Register-staged `_gs`:** no hit on 8 / 8 rows.
- **`gemm_bk 128` on top of the 192-wide tile at `12,1,16384`.** It
passed on SM100 (1.0239 / 1.02385 / 1.02574), but it adds a program for
the same gain, so it was not adopted. It failed on SM103 (1.0098 /
1.01176 / 1.01176).
- **In-CTA quantizer program `_qp`.** It read 5.2–5.8 % faster than the
earlier `qwarps 8` production. Against the adopted `qwarps 16`
production it failed all 12 confirm verdicts on each GPU (3 arms × the
four `1,28,2048` rows, every round below 1.015), so it was not merged.
- **Decode store-cadence and mid-M decode levers:** closed by bound or
by measurement.
- **Host mirror (`cake_backend.py`):**
- Reads the new keys `gemm_pdlb`, `gemm_static` and `gemm_gs`, plus the
decode key `pw`. The round-10 `DecodeConfig` had no `pw`.
- Carries the 192-wide admissibility rule `gemm_n192_admissible`, the
same rule as Cake. The 192-wide pair tile is now admitted on the N =
7168 cells, where the storage-fit guard used to fall back to 256.
- 192-wide cells that have a prefetch or stream-K key no longer list the
plain `gemm_tstore_n192`. Mirror / plan parity is empty on both GPUs.
- Launches `_gs` plans on a grid of CTA_GROUP × P′, with P′ taken from
the stage arguments (see the host defect under Validation).
  - Templates are formatted with FlashInfer's pinned ruff 0.12.8.
- **Exporter and receipts:**
  - `TARGET_REVISION` is FlashInfer `ea5f7409`.
- The exporter's delivery check refuses undeclared constant-only kernel
clones. It now accepts the raster-group twin (`GROUP_M` 32 vs 64), which
is declared in `SCHEDULE_CONSTANTS`. This twin changes only the tile
raster order, not the per-element MMA order.
- Measurement semantics are the same as round 9: SM-clock trace with a
clock-stability precondition, 3 counterbalanced groups × 2000 samples, 8
graph instances, cold L2, CUPTI, node alone, 4 GPUs.
- **Package:** the delivered package manifest and delivery patch against
`ea5f7409`: FI delivery patch (protocol r9, generated from the sealed
export on both GPUs; FlashInfer HEAD
ea5f740951ac45f8a73aed036e28a5a9c7e57838 = TARGET_REVISION): both GPUs
produce the SAME patch, fi_delivery_cpu.patch sha256
a6bd5e0d91ba356f81b4853d29b56f084b7a01e4af4da9a7f73d96e4a258615a,
1393200 bytes, 39 files, status_entries=46, outside_owned_paths=0,
registry_hashes=107, cu_files=214, unreferenced=0; combined package hash
cf6a209c47071753 (248 files, 11034424 bytes) identical on B300 and B200,
i.e. the exported program set is byte-identical across the two export
runs.

## Exactness and parity

- **Two exactness classes, as in rounds 9 and 10.**
- **Bit-exact (Tier A)** levers leave every output bit-identical to the
record. On every cell except the one below, the tile-shape, raster,
static-tile, grid-stride, PDL-order, prefetch, stage / slot,
quantization-width, decode-grid, `qwarps` and `pw` keys do not
re-associate any FP32 partial sum.
- **Re-association (Tier A′)** levers ship only under the rule-5
exactness-equivalence gate, with the refined 5(a). On every touched row:
- each output element is bit-identical to the record's, or off by
exactly 1 BF16 ulp, or, for near-zero outputs, off by at most 2^-24 ×
Σ_k |a_k b_k|;
    - max |err| vs the FP64 reference is at most the record's + 1 ulp;
    - mean |err| is within 1e-3 relative;
    - the reduction is deterministic and fixed-order;
    - eager output equals graph replay;
    - NaN / Inf and padding are unchanged;
    - a per-row packet is published.
  - At equal gain, Tier A wins over Tier A′.
  - The contract itself is unchanged.
- **The one Tier A′ cell of this round: SM100 `56,48,1024`
(tp1:o_proj:1024).**
- The 192-wide tile keeps the cell's stream-K fix-up
(`gemm_tstore_n192_k128_skf`). The fix-up partition follows the tile
grid, so the order in which exact FP32 partial sums are added changes
even though the stream-K token does not.
- Rule-5 packet: PASS on the 5 touched rows. 4 rows are bit-identical; 1
row has near-zero elements judged under the refined rule 5(a).
- The later `gemm_pf 1` on the same cell is bit-exact against that
program.
- **Rows expected to differ from the record.** These lists come from the
static derivation over the table diff (registry v3, derived again before
parity):
- **SM100:** 3 rows, all in cell `56,48,1024`: `tp1_o_proj_m1000_corr`,
`tp1_o_proj_m1024` and `tp1_o_proj_m513_corr`.
- **SM103:** 2 rows in cell `96,28,2048` (`gemm_bk` 256 → 128 under the
cell's stream-K fix-up): `tp1_q_proj_m1025_corr` and `tp1_q_proj_m2048`.
The conservative static rule lists them, but the cell's paired confirm
was bit-exact, so they are listed and expected bit-identical. The sealed
parity decides. Listed rows that turn out equal are reported as
listed-but-equal.
- **Static-derivation correction (disclosure).**
- The first version of the static rule (v2) treated every tile-shape key
as exact. It listed a row only when the row's re-association token
changed.
- On SM100 it therefore listed only the two register-staged rows of
`56,48,1024`. It predicted the perf row `tp1_o_proj_m1024` would be
bit-identical, even though that row's confirm was not bit-exact and the
row shipped under the rule-5 packet.
- v3 adds the rule "a tile-geometry change (`bn` / `bk` / `gm`) under an
unchanged re-association token is Tier A′", with new self-test cases.
This rule also adds the SM103 perf row `tp1_q_proj_m2048`.
- **Bitwise checks on all 704 contract rows (352 per GPU).** Two checks
run on every row:
  - (a) exported program vs Cake source, on every receipt;
- (b) this package's output vs the round-10 package. Every differing row
must be a listed Tier A′ row, and the result is cross-checked against
the output digests.

  Results:
- SM103: SM103: 352 / 352 rows bit-identical to the round-10 package
(differ 0, errors 0); the 2 statically listed rows of cell 96,28,2048
are listed-but-equal, so no rule-5 packet is needed. Digest audit:
SM103: output-hash audit of all 354 receipts (353 hashed rows, 0
inconsistent) labels 0 rows as differing; the 2 statically listed rows
are confirmed equal.
- SM100: B200 parity (protocol r9, step 68f54501, 17:24-17:51Z; record
package = the round-10 delivered FlashInfer package at ea5f7409, new =
the FIN tip 12 package): record-vs-new bitwise parity sm_100a total 352,
equal 351, differ 1 (tp1_o_proj_m1024), record_error 0, new_error 0,
launcher_differ 0, repeat_differ 0, missing 0; PARITY_TIERAP differ=1
tierap_listed=1 unlisted_differ=0 other_nonequal=0 -> the single
differing row is the statically listed Tier A' row of cell 56,48,1024
(packet acc7795e PASS); the other two listed rows
(tp1_o_proj_m1000_corr, tp1_o_proj_m513_corr) are listed-but-equal;
PARITY_HASH_DONE record rows=352 errors=0, new rows=352 errors=0
(results/r9-parity/r11f/{record,new}_sm_100a.json); delivered package
PKGHASH_COMBINED cf6a209c47071753 files=248 bytes=11034424, identical to
the SM103 package hash. Digest audit: B200 rows audit on the merged
sealed view r11f-merged-sm_100a (step 90b5ecc7, 0 GPU, 17:54Z; the
refused FULL receipt of tp1_f_b_m1000_corr superseded by the passed Q7
receipt): EXPORT_ROWS sm_100a receipts=353 passed=353 gate_fail=0
exception=0 unstable=0 no_trace=0 bitwise_ok=353 forms_changed=49
tierap=3 sm_counts=[148] median_mhz=1365-1965; TIERAP_AUDIT sm_100a
rows=353 hash_rows=353 hash_labelled=1 form_labelled=0 both=0
form_only=0 hash_only=1 form_unverified=0 published=3 listed=3
source=hash:353,form:0 hash_source=receipt receipt_hash_rows=353
receipt_hash_inconsistent=0 (registry tierap_registry_r11.v3): exactly
one row carries a differing hash (tp1_o_proj_m1024, the published Tier
A' row of cell 56,48,1024), the other two listed rows are
listed-but-equal; TIERAP_R11 CONFIRM rows=1 cells ['56,48,1024'] tokens
cs4/skf; ROWSAUDIT_DONE rc=0 derive=0.
- **Kernel fix: TMA-store staging-slot wait.** This is the root cause of
the wrong output that round 10 found for the 192-wide tile with the
two-stage / four-slot TMA store.
- Symptom: round 10 measured wrong output on SM100 `12,1,16384`: 23,537
elements differ (23,490 by more than 1 BF16 ulp), max abs error vs FP64
1.387 (record 0.0039). The same race explains every not-bit-exact
reading of a 192-wide arm on a two-stage / four-slot cell in this
round's passes 1, 6 and 7.
- Cause: the TMA-store epilogue of the GEMM producer (`stage_and_store`)
waits for pending bulk stores before it rewrites a staging slot. It
waited only until `GEMM_TS_SLOTS - 1` (= 3) stores were pending. A
192-wide tile drains 3 chunks per epilogue group; a 256-wide tile drains
4. With 4 slots and a 192-wide tile, the asynchronous bulk store of the
previous tile's chunk could still be reading a slot while the next tile
wrote the same slot. This is a write-after-read race.
- Fix: the wait bound is now `min(GEMM_TS_SLOTS, GEMM_EPI_COLS //
TS_COLS) - 1`, that is, min(slots, chunks per drain) - 1 pending stores.
It is 3 for the 256-wide tile (unchanged), 2 for the 192-wide four-slot
form and 0 for single-slot forms. The fix only adds waiting.
- Programs changed: the render census at the fix shows exactly one
differing program, `gemm_tstore_n192_s2_ts4` on SM103. Every other
program is identical on both GPUs.
- Why the sanitizers did not find it: `compute-sanitizer` racecheck
cannot observe reads by the asynchronous proxy. The earlier synccheck +
racecheck runs on this instance were therefore clean.
- Validation: bit-exact re-measurement on both GPUs (the two
`12,1,16384` adoptions and the `96,1,512` re-confirm) and the sealed
parity. A Cake CPU render test also checks the rendered wait depth. It
asserts that the program's only `cp.async.bulk.wait_group.read`
immediate equals the slot period minus one (2 / 3 / 0), and that the
CTA-retire drain is a `cp.async.bulk.wait_group 0`.
- Sealed parity of the rows served by `gemm_tstore_n192_s2_ts4`: C24
(ec37e0da) fixed the write-after-read race in stage_and_store (TMA-store
epilogue): before reusing a staging slot the code waited only until
GEMM_TS_SLOTS - 1 = 3 bulk stores were pending, although a 192-wide tile
drains 3 chunks per epilogue group, so with four slots the next tile
could overwrite a chunk still being read by the previous tile's
asynchronous TMA store; the bound is now min(GEMM_TS_SLOTS,
GEMM_EPI_COLS // TS_COLS) - 1 (BN 256: 3 unchanged; BN 192 four-slot
form: 2; single-slot forms: 0). racecheck cannot observe async-proxy
reads, so the fix was confirmed by bit-exact re-measurement on both GPUs
(t7fixb). Sealed r11f parity of the gemm_tstore_n192_s2_ts4 rows against
the round-10 record: sm_100a tp8_f_b_m16384 (adoption #18) is bitwise
equal (the only differing sm_100a row is the Tier A' tp1_o_proj_m1024);
on sm_103a every row is bitwise equal (352/352), including
tp8_f_b_m16384 (adoption #19) and the 96,1,512 row of adoption #12.
- Shipped cells affected: one. SM103 `96,1,512` (tp1:f_b:512) shipped
`gemm_tstore_n192_s2_ts4` before the fix. Its original S5 v2 confirm was
bit-exact. It was confirmed again on the fixed program, node alone: S5
v2 1.03014 / 1.03559 / 1.03203, A/A 1.0 × 3, bit-exact. The adoption is
kept.
- The 192-wide arms on the other two-stage / four-slot cells
(tp1:f_b:1024 / 4096 / 16384 and tp8:kv_b:16384) keep their earlier
measured-not-adopted verdicts. The fix only adds waiting, so those
verdicts stand.
- **Now shipped: the 192-wide tile on the SM100 two-stage / four-slot
TMA-store cell `12,1,16384` (tp8:f_b:16384).**
- Before the fix, the exactness gate excluded it. On SM100 it read
1.02935 / 1.02757 / 1.02935 in its pass-1 confirm and 1.02768 / 1.02589
/ 1.02773 in its pass-6 confirm (screen 1.0294 and 1.0330), but it was
not bit-exact. The pass-1 SM103 confirm of the same arm (1.01587 /
1.01386 / 1.01584) was not bit-exact either. The staging-slot race above
explains these readings.
- On the fixed program, re-measured node alone with S5 v2, it is
bit-exact and passes on both GPUs. It ships as a Tier A adoption on
SM100 and SM103 (see the adoption lists above).
- Round 10 stated that no shipped instance combined the 192-wide tile
with the stage / slot tokens. That statement does not hold for this
package. `gemm_tstore_n192_s2_ts4` ships on SM103 `96,1,512`
(tp1:f_b:512), on SM103 `12,1,16384` (tp8:f_b:16384) and on SM100
`12,1,16384` (tp8:f_b:16384).

## Validation

- **Sealed export receipts on the final tip.** The exported programs
come from Cake commit `f41a34357f61a1738766ef532d19e5b7c3cc7831`. The
receipts use the protocol above with `TARGET_REVISION` = FlashInfer
`ea5f7409`.
- Program set: compared with the last Cake commit before the kernel fix,
the exported program set is bit-identical except for two entries.
`gemm_tstore_n192_s2_ts4` changed with the fix on SM103, the only plan
that had it. The same instance was then added to the SM100 plan by the
`12,1,16384` adoption.
- SM103 (GB300): 354 receipts, 354 passed (gate_fail 0, exception 0,
unstable 0, no_trace 0), bitwise_ok 354, TARGET_REVISION check ok
against ea5f7409; target test 81 passed on the delivered package; 152
SMs, median SM clock 1590-2070 MHz across rows.
- SM100 (B200): 353 receipts: 352 passed in the first sealed run plus
one correctness row re-measured once under the round-10 single
re-measure rule (see below), bitwise_ok 353, TARGET_REVISION check ok
against ea5f7409; target test 81 passed on the delivered package; 148
SMs, median SM clock 1365-1965 MHz across rows.
- Single re-measure under the round-8 Q7 rule, if any: one SM100
correctness row (tp1 f_b M=1000) was refused by a timing-consistency
gate of the first sealed run (its drift and directional gates passed and
the output was bitwise equal) and was re-measured once under the
round-10 single re-measure rule: 15.424 us, 1.0104 vs the record, every
gate passed, bitwise equal; the composed sealed root (first run +
re-measure, the later run supersedes the refused receipt) is the SM100
package of record, as in round 10.
- **`tests/experimental/test_cake_kimi_k3_fp8_projection.py` on the
final tip.** Pre-measurement seed (export rc, FI target tests, FI ruff
rc, target HEAD and `TARGET_REVISION` check):
- SM103: export rc 0 (707 shapes, clock-stability precondition ok),
target test 81 passed, ruff 0.12.8 format + check clean, TARGET_REVISION
check ok.
- SM100: export rc 0 (707 shapes, clock-stability precondition ok),
target test 81 passed, ruff 0.12.8 format + check clean, TARGET_REVISION
check ok (two earlier attempts failed only on a shared-filesystem file
quota while writing logs; no kernel or test failure).
- **New expectations in the test module:**
- Expected GEMM program keys are composed with `_g64` / `_cs<S>` / `_st`
/ `_gs` / `_pdlb`, the same way Cake's `route_plan` composes them.
  - 5 new GPU rows.
  - The CPU test `test_sk_bindings_carry_no_split_scalars`.
  - The `_gs` launch grid.
  - The updated plan pin for the `12,1,16384` adoption.
- **Seed failures on earlier tips of this round, all fixed before the
sealed export of the delivered package.** None of these fixes changed
kernel source:
  1. Three problems on the first tip:
- The exporter refused the `GROUP_M` raster twin of SM103 `144,6,16384`
as an undeclared constant clone. The twin is now declared.
- The pinned ruff asked to reformat two templates. The fix is a
format-only patch generated with the same ruff.
- Six FI package tests failed against the stale round-10 backend left in
the FlashInfer tree. They did not recur once a round-11 package was
delivered.
2. The GPU case expected `gemm_rstaged_n192_k128` where the plan
correctly selects `gemm_rstaged_n192_k128_pdlb`. The numerics passed.
3. The new `_gs` GPU rows exposed the host defect described in the next
bullet.
4. The new CPU test's 1 MiB workspace fixture was smaller than the
stream-K class's 1,574,912-byte partial area. The fixture is now
GEMM_SK_FLAG_BYTES + 8 × GEMM_SK_TILE_BYTES.
5. The GPU case asserted the per-tile grid (1024) for `_gs` plans, but
their launcher grid is CTA_GROUP × P′ (152 on SM103, 148 on SM100).
Every numeric case passed (80 passed on each GPU).
- **Host defect found before the sealed export (disclosure).**
- Symptom: the FI target test's new `_gs` GPU rows (SM103 tp8:f_b:2048
and tp1:f_b:2048) returned an output that was never written (all NaN).
  - Cause:
- `prepare_kimi_k3_fp8_projection` applies the call-bound tensors over
the per-stage arguments (`kwargs = dict(fixed); kwargs.update(bound)`).
- The binding side, `_sk_launch_kwargs`, returned `sk_pairs = sk_rem =
sk_ksplit = sk_dp = 0` for every GEMM form without a stream-K hand-off
area.
- The `_gs` programs carry their launched pair count P′ in `sk_pairs`,
and the stage side (`_sk_scalar_kwargs`) set it correctly. The zero
binding overrode that value.
- The kernel then computed `gs_n = (T - p + sk_pairs - 1) // sk_pairs`
with a zero divisor and ran no tile.
  - Affected: every `_gs` cell through the prepare / one-shot API.
- SM103: `12,1,2048`, `96,1,2048`, `12,1,4096`, `24,2,2048`,
`24,2,1024`, `18,6,2048`.
- SM100: `17,28,2048`, `56,6,2048`, `96,1,2048`, `12,1,4096`,
`24,2,1024`, `24,2,2048`, `24,2,4096`, `56,6,512`, `192,2,512`.
- Not affected: the Cake launcher, the FI `KimiK3Fp8ProjectionLauncher`
template path, and every non-`_gs` program.
- The defect had been latent since the `_gs` adoptions, because no FI
GPU test had a `_gs` row before this round.
  - Fix (exports only):
- `_sk_launch_kwargs` now returns only the two hand-off tensors, so the
split scalars have a single source (`_sk_scalar_kwargs` in
`_stage_kwargs`).
- `test_sk_bindings_carry_no_split_scalars` asserts that bindings and
scalars are disjoint on the plain, `_gs`, `_skf` and stream-K plan
classes.
- The sealed export and the 704-row parity are both measured on the
fixed host.
- **Ruff.** FlashInfer's pinned ruff 0.12.8 (`ruff format --check` +
`ruff check`, run inside the FlashInfer tree):
- The FI-pinned ruff set-diff on the final tip reports pre-existing
findings only (140 / 140).
  - FI ruff rc in the final-tip seeds: see the seed results above.
- **GPU gates on the final tip.** Cake `pytest -m gpu -k kimi_k3_fp8`
and the kimi bench-regression passed on both GPUs:
  - SM103: 34 passed; bench-regression ALL PASS (floor 2199 TFLOPS).
  - SM100: pytest rc 0; bench-regression ALL PASS (floor 2275 TFLOPS).

The selection now has 34 tests. It gained an end-to-end row for
`gemm_tstore_n192_s2_ts4`. The gates passed on every delivery tip and
every adoption tip of this round they ran on, with one exception. On one
intermediate delivery tip the SM100 gate failed on that new row (1
failed, 33 passed). The row used the strided-output path, whose register
epilogue is incompatible with the row's TMA-store slot pin. The next tip
runs the row with `strided_out: 0`. Before any adoption, the first build
commit of the PDL-order GEMM form also failed its SM103 gate on a Python
`NameError` at trace time (a closure default evaluated at definition
time); the next commit fixed it, and the form was adopted only after its
gates passed on both GPUs. The row used the strided-output path, whose
register epilogue is incompatible with the row's TMA-store slot pin. The
next tip runs the row with `strided_out: 0`.
- **0-GPU chain on the final tip:**
  - FlashInfer-mirror CPU test: 24 passed (57 skipped).
- Exporter CPU set: 177 passed, including the new wait-depth render
test. On one intermediate tip, the first version of that test asserted
one wait per epilogue chunk and failed. The chunk loop renders once, so
the final version asserts the single immediate.
- Render census: IDENTICAL against the previous tip on both
architectures (0 new programs).
- **Cake exporter and bench-harness CPU suites** (`loom/tests/infra`,
`loom/tests/export`, `-m "not gpu"`): loom/tests/infra on the final tip
827 failed / 11506 passed / 59 errors vs the round-10 record 827 / 11476
/ 60, identical failed set (782 unique ids); the one record-only error
is a collection error of a test file that no longer exists on the final
tip; loom/tests/export 8 failed / 373 passed / 6 errors vs 8 / 292 / 6,
identical failed and error sets; no regression.
- **Rebase.** The Cake-side squash is rebased onto the then-current Cake
main. Its base-move checks (preview merge, 0-GPU chain and render census
on the rebased tree) are reported in the Cake merge request.
- **Sanitizers.** `compute-sanitizer` synccheck + racecheck (never
memcheck) ran with 0 errors on every new instance, and on at least one
touched row of every adoption except the first T7 adoption (commits
`0d362298` + `e4f89c90`: `gemm_bk 128` on the sm_103a cells 384,28,2048
/ 50,28,16384, rows tp1:fused_qkvg:2048 and tp8:in_proj_qkvgfab:16384;
decode-table-only commits that re-use the existing 128-K programs
`kimi_k3_fp8_proj_gemm_tstore_k128` and, for the 16384 row,
`kimi_k3_fp8_proj_gemm_rstaged_k128`). That adoption carried the GPU
gates on both GPUs (GB300 `81aa3df4`, B200 `9865e91a`) but no row
sanitizer step. Two adoptions sanitized a subset of their touched rows:
C9 `2d56c042` (GB300 `ed061ace`, 5 of 6 rows; the decode cell 384,28,1
`grid 128`, row tp1:fused_qkvg:1, had none) and C17 `6f3dbb1f` (B200
`40813ace`, one row per new `_gs` program: tp1:fused_qkv_a:2048 for
`gemm_tstore_k128_gs` and tp8:kv_b:1024 for `gemm_tstore_n192_k128_gs`;
its other 10 rows had none). This includes:
  - the `_gs` instances;
- `gemm_tstore_n192_s2_ts4`: before the fix, again after it at
tp1:f_b:512, and at the new `12,1,16384` plan entry (tp8:f_b:16384) on
both GPUs;
- the new named sanitizer entry for that instance,
`kimi_k3_fp8_projection_gemm_n192_ts4_sanitizer`, on both GPUs;
  - `gemm_tstore_n192_k128_skf_pf1`;
  - `decode_t64_p2_fused_w16_r2_xh_q8_cs4_xp`;
  - `decode_t16_p4_pw2`.

Racecheck cannot observe asynchronous-proxy reads, so these runs alone
do not validate the kernel fix (see Exactness). The commits after the
adoption add no new program, so no further sanitizer run was needed.
- **Static analysis (Cake).**
- On `_gs`, the analyzer reports `missing_proxy_fence`. This was traced
to a coverage gap in the analyzer for cross-tile bulk-group completion
edges:
- A probe added a `_gs`-guarded `fence.proxy.async.shared::cta`. It
cleared only the findings outside the warp that issues `bulk_wait` and
the `tma_store`, so a kernel-side fence does not fully clear the
finding.
- The finding is recorded as an expected error class. No kernel change
was made.
- The composed `gemm_tstore_n192_s2_ts4` now has its own end-to-end
registry row and analysis entry. The analysis passes on both
architectures on the final tip.
- **Eager = graph-replay bit-identity** on every adopted instance at the
final tip: all 352 contract rows per GPU replay bit-identically (eager
twice + CUDA-graph replay) at the final tip: SM100 352 / 352 rows, 112
program instances, 0 failures; SM103 352 / 352 rows, 112 program
instances, 0 failures.
- **A3: paired same-GPU no-regression check against the round-10 kernels
of record.** This uses the same script as round 10, pointed at the
round-10 record. Acceptance: no row below 0.98 after attribution, and
geomean ≥ 1.00.
- SM103: 198 perf rows A/B against the round-10 kernels on the same
node: geomean 1.0049, minimum 0.9925 (tp8 o_proj M=64), no row below
0.98 (per-shard geomeans 1.0028 / 1.0014 / 1.0015 / 1.0097 / 1.0132).
- SM100: B200 A3 (A/B vs the round-10 record on the same node, 5 shards
+ combine): combined rows=198 geomean=1.0034 min=0.9459 (tp8:kv_b:512),
4 rows read below 0.98 in the shards (tp8:kv_b:512 0.9459, tp8:q_b:1024
0.9777, tp1:fused_qkv_a:256 0.9780, tp1:fused_qkvg:2048 0.9739); all
four were re-measured with the round-10 per-kernel probe protocol
(record, new, record, new; one process per arm; same GPU): identical
kernels and equal per-kernel times in both arms (6.59 x4 us;
9.82/9.82/9.85/9.82 us; 14.08 x4 us; 457.77/455.58/458.70/452.89 us with
the new arm faster in both pairs); the programs of these four rows are
byte-identical to the record's, so the shard readings are measurement
noise; 0 rows below 0.98 after attribution; raw shard numbers and probe
logs kept verbatim.
- **A2: comparison with the fastest complete FlashInfer / DeepGEMM FP8
chain on every perf row.** Acceptance: every perf row > 1.00×.
- SM103: 198 perf rows, all measured: geomean 2.2567x the fastest
complete FP8 chain, minimum 1.0411x, no row below 1.00x. Per peer:
cutlass groupwise 198 rows (geomean 2.477, min 1.084); trtllm groupwise
180 rows (geomean 3.557, min 1.041; 18 rows refused by the peer:
'ValueError: a.shape[1] must be >= 256 in TRTLLM'); cuTile groupwise 72
rows (geomean 2.234, min 1.175; partial as in round 10: 42 shapes per
shard unsupported by the kernel, one autotune config fails with
'TileCompilerExecutionError: Return code 5'); DeepGEMM grouped and
deepgemm_ue8m0 unmeasurable on every row in the SM103 sglang 26.07
container ('ValueError: cubin not registered:
kernel.fp8_m_grouped_gemm.<hash>' and 'RuntimeError: interpreter
INTERNAL ASSERT FAILED at torch/include/c10/core/impl/PyObjectSlot.h:30
... cannot access PyObject for Tensor'), identical to round 10.
- SM100: B200 A2 (graph mode, 3 shards + combine): combined rows=198
measured=198 geomean vs the fastest complete FlashInfer/DeepGEMM chain
2.2480, min 0.9856 on ONE row, tp1:in_proj_qkvgfab:8 (x0.986 vs
flashinfer_trtllm_groupwise: 75.55 us vs 74.46 us in that shard process;
the same kernel read 72.70 us in the sibling process, sealed receipt
71.456 us, record-vs-new A/B 1.0000, cell unchanged in this round). Per
the round-10 single-row re-measure rule (disclosed) the row was
re-measured three times against the same peer on the same GPU, twice
alone in fresh processes and once by re-running the whole 66-row shard:
x1.031 (71.90 vs 74.11 us), x1.030 (71.97 vs 74.14 us), x1.041 (71.55 vs
74.46 us) -> measurement outlier; the row is above 1.00x after
re-measure and the original shard artifacts are kept verbatim next to
the probes. Per peer: flashinfer_cutlass_groupwise n198 gm 2.474 min
1.072; flashinfer_trtllm_groupwise n180 gm 3.522 min 0.986 (18 rows
refused by the peer: 'ValueError: a.shape[1] must be >= 256 in TRTLLM');
flashinfer_cutile_groupwise n72 gm 2.196 min 1.160 (partial as in round
10: 24 of 66 rows per shard measured, 42 shapes per shard marked
correctness FAIL for the cuTile output, one autotune config fails with
'TileCompilerExecutionError: Return code 5');
flashinfer_deepgemm_grouped1 unmeasurable on every row (198/198),
verbatim: 'ValueError: cubin not registered:
kernel.fp8_m_grouped_gemm.<hash>' (5 distinct hashes); deepgemm_ue8m0 is
a B300-only arm of the chain and was not run on B200 (as in round 10).
- **Roofline fraction.**
- Method: the round-10 floor definition, clock-normalized with f_nominal
= 4.5e15 / (SM count × 16384), which is 1807.0 MHz on 152 SMs and 1855.8
MHz on 148 SMs. Class A means ≤ 1.10× the clock-normalized floor.
- Launch ramp, re-measured at the start of this round: 3.904 us on SM103
and 4.000 us on SM100 (round 10: 3.872 / 4.096).
  - Calibration readings from this round:
- HBM read / copy: 7015 / 6432 GB/s on SM103 and 7049 / 6135 GB/s on
SM100.
- Sustained dense FP8 16384² × 7168: 3704 TFLOPS at 1695 MHz = 87.8 %
per clock on SM103; 2988 TFLOPS at 1395 MHz = 88.3 % per clock on SM100
(power cap 97 %).
- Before (the round-10 receipts as scored in round 10; geomean nominal /
clock-normalized / attainable):
    - SM103: 1.595 / 1.636 / 1.501, class A 7.
    - SM100: 1.673 / 1.655 / 1.466, class A 4.
- Before, re-scored with this round's ramp and calibration: SM100 1.692
/ 1.674 / 1.499, 3 rows within 1.10x (tp8 f_b M=1/8/64; tp8 kv_b M=8
reads 1.11 with the round-11 ramp); SM103 1.589 / 1.630 / 1.478, 7 rows
within 1.10x.
  - After:
- SM103: 198 perf rows with clock trace: geomean fraction of the floor
nominal 1.580 / clock-normalized 1.622 / attainable 1.471 (round-10
record rescored with the same ramp: 1.589 / 1.630 / 1.478); 6 rows
within 1.10x of the clock-normalized floor. One unchanged row (tp1
fused_qkvg M=16384) reads 1.098 on the record receipt and 1.101 on this
receipt (3183 us at 1605 MHz vs 3253 us at 1567 MHz); its remaining
lever is measured before publication.
- SM100: B200 floors on the sealed receipts (floor_r11_r11f_sm_100a.md
43868 B sha256 b0c048897e8aa4e5; ramp 4.000 us; f_nominal = 4.5e15 /
(148 x 16384)): 198 perf rows, 198 measured with clock trace, f_measured
1965 MHz on every M bucket except 1959 MHz at M=16384; geomean floor
fraction before 1.655 -> nominal 1.684 / clock-normalized 1.667 /
attainable 1.493; class A (clock) 3: tp8_f_b_m1 (1.03), tp8_f_b_m8
(1.05), tp8_f_b_m64 (1.06). tp8_kv_b_m8 (class A on the round-10 receipt
at 1.09) reads 1.16 on the new receipt (4.864 us vs floor 4.20 us;
record-vs-new A/B 0.9998, program unchanged, bitwise equal) -> treated
as open and closed by direct measurement of its remaining lever (T5 form
B, XMC=2/4/8: 0.85 / 0.82 / 0.81, all bit-exact, not adopted).
- Before and after come from two sealed sessions, each at its own
clocks, so they are not a paired A/B. The paired verdict is A3.
- **Host launcher per-call cost (W4 bench) on the final tip:**
- SM103: host-launcher bench exit 0 (400 calls x 7 rounds): all 5 rows
bit-exact (eager, graph replay, launcher plan equal); the chain is
faster than the per-kernel launcher on every sample (-7.10 to -4.30 us);
no regression.
- SM100: B200 W4 host-launcher bench (1 GPU, 400 calls x 7 rounds, 5
rows tp8:q_b:1 / tp8:q_b:64 / tp8:o_proj:1 / tp8:q_proj:256 /
tp8:fused_qkv_a:1024): all rows bit-exact and graph-replay bit-exact;
the pre-chain reference launcher is bit-exact with an equal plan on 4
rows. Tooling disclosure: on tp8:q_b:64 (plan quant:u1 +
decode:t16_p4_pw2) both reference launcher texts (the round-7 text at
ea5f7409 and the pre-chain round-8 template) predate the table knob 'pw'
and name a program the new sm_100a package does not build
(NotImplementedError), so the bench skips both reference arms on that
row and records it; the first two runs crashed there before the skip
existed. A limitation of the reference arms, not of the delivered
launcher; the B300 rows carry no pw cell. Host cost vs the round-10
bench (median us, new vs round 10): same-output launcher 4.58 vs 4.63,
6.11 vs 6.01, 4.66 vs 4.68, 6.25 vs 6.41, 6.53 vs 6.50; round-7 launcher
4.82 vs 4.81, n/a, 4.90 vs 4.90, 6.62 vs 6.68, 6.84 vs 7.03; one-shot
launch 9.49 vs 9.70, 12.38 vs 12.49, 9.72 vs 9.97, 12.56 vs 12.71, 12.85
vs 13.09 -> no regression.

## Checklist

- [x] ruff 0.12.8 `format --check` + `check` clean on the templates and
the delivered Python files. Final tip: the FI-pinned ruff set-diff
reports pre-existing findings only (140 / 140); the seed ruff results
are under Validation.
- [x] `tests/experimental/test_cake_kimi_k3_fp8_projection.py` green on
SM100 and SM103 on the delivered package. The final-tip seed results are
under Validation.
- [x] Sealed export receipt summaries and 704-row bitwise parity
reported in this description. The SM103 and SM100 receipts and the
352-row parity per GPU are above; the per-row tables and the evidence
manifest are kept with the Cake-side delivery record.
- [x] `gemm_tstore_n192_s2_ts4` (SM103 `96,1,512`, SM103 `12,1,16384`,
SM100 `12,1,16384`): root cause of the round-10 wrong output established
and fixed (TMA-store staging-slot wait), and sealed parity of its rows
reported (see Exactness above).
- [x] `/bot run` + `run-ci` label cycled after every push (added at PR
creation: `/bot run`, `@flashinfer-bot run
tests/experimental/test_cake_kimi_k3_fp8_projection.py`, label `run-ci`;
repeated after each later push).
- [x] Tracker #4254 bullet after #6433 (`- #6552`, added at PR
creation).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [f0f5ae8](https://github.com/flashinfer-ai/flashinfer/commit/f0f5ae8f019516e8c4ccf01fcbf826aab953d1f8)

- **作者**: eigen
- **时间**: 2026-10-15T21:37:34Z
- **提交信息**: perf(cake_sparse_mla): FP8 prologue levers: h64 source-exact prologue overlap, low-head prefill index staging, h8/h16 setup order (SM100/SM103) (#6550)

## Summary

`backend="cake"` DSv4 sparse-MLA (SM100 / SM103) release: the Cake
`cake_dsv4` programs re-exported from Cake `dbc4b83bcb6`
(Cake main after the merge of the three lever changes below and of two
export-engine fixes: one keeps this family's units per-architecture, one
lets the source-preparation capture accept the runtime's launch keyword;
the program sources are those of the lever merges) on top of upstream
main `fd14b3056d0`, which already carries
this family's previous release (#6220) and the later NVFP4 decode update
(#6357). Two commits: sm_103a, then sm_100a.

Kernel changes in this release (three FP8 programs; the other programs
of the family are re-exported from the same tree
and carry no intended kernel change):

- `fp8_h64_source_exact` (class
`fp8_h64_source_exact_q64_kv128_v512_persistent_keeps`, 3 export rows):
prologue overlap
on the CLC-persistent producer. The first work item's pair-0 index page
`cp.async` and its Q expect-tx + four Q TMA
boxes move between the mbarrier publication and the TMEM allocation, so
their latency overlaps the allocation and the
post-allocation CTA sync. The role bodies skip only that first issue;
every wait, arrive, expect-tx, barrier count,
byte, mask and MMA stays. Ordering only, no arithmetic change (the
lowering emits one CTA-wide publication barrier in
place of the former warp-level one and one additional, idempotent
`griddepcontrol.wait` on the warp that issues the
moved boxes; the authored mbarriers and their arrival counts are
unchanged).
- `fp8_lowhead_prefill` (class `fp8_lowhead_prefill`, target row
hardening-000070; the same program serves 15
`fp8_lowhead_decode` rows): the first sparse-index pass of each of the
four load warps for the CTA's first work item
(the pass `index_pass == load_warp_rank`) moves into kernel setup, stays
in registers across the mbarrier init, both
CTA syncs and the TMEM allocation, and is stored to shared memory right
before the index loop, which then starts at
`load_warp_rank + 4` for that item only (every later pass of that item
and every later item loads as before); the
first item's Q TMA is issued before the TMEM allocation. Same loads,
values, masks, smem bytes and offsets; order
  only; output bit-identical.
- `fp8_h8_h16_source_exact` (class `fp8_h16_source_exact`, 11 export
rows): the TMEM allocation moves from warp 0 to
warp 8 (the MMA role's warp, idle before role dispatch), and the 52
serial lane-0 `mbarrier.init` calls become
lane-indexed batches at the same addresses and with the same counts.
Decorator-level change
(+3 lines in one file: one import and two decorator knobs); numerics
bit-identical by construction.

Sparse-validity semantics and the host contract
(`flashinfer/mla/cake_dsv4.py`, `flashinfer/mla/_core.py`) are
unchanged. No tolerance, dispatcher, grid, workspace or ABI change.

## What changed
- `csrc/cake_dsv4/`: the family's units regenerated from Cake
`dbc4b83bcb6`. Per-architecture `*_kernel.cu` /
`*_binding.cu` units are content-hashed (kernel symbol and host-shim
namespace hashed over the export identity, as in
the previous releases), so a unit whose rendered kernel changed appears
as one retired file plus one new file (three
per architecture in this release: the lever programs); the upstream
NVFP4 units and headers under `common/` are
untouched. Nine further `*_kernel.cu` units per architecture, whose
rendered kernel is unchanged, are refreshed in
place under their existing names (+9 lines each, nothing removed): each
gains the translation-unit-local
`__device__ __forceinline__ int make_warp_uniform(int)` fallback that
the exporter now emits beside the shared header's
content-addressed `uint32_t make_warp_uniform(uint32_t)` helper. The two
form a legal overload pair; every call site
passes an `int`, so the call binds to the `int` overload as an exact
match and the `shfl.sync.idx.b32` result is
bit-identical. Every unit was JIT-built and passed the correctness gate
in this export (197/197 rows per architecture).
- Shared headers
`csrc/cake_dsv4/<arch>/cake_dsv4_{device,host}_common.cuh` and the
content-addressed device helpers
under `csrc/cake_device_helpers/`: regenerated from the same tree and
checked against the base before the push (every
base line must be present; helper files may only be added). In this
release the two device headers differ from the
base only in line order (`git diff` against the base: sm_103a +2/-2,
sm_100a +1/-1; include lines that changed
position, nothing added or removed; the provenance tool's `reordered`
count below is positional, counting the base
lines that fall out of order in an in-order walk of the base: for
sm_103a the 20 base lines the two includes were
moved past, not the two includes themselves; for sm_100a the one moved
include itself), the host headers are
  byte-identical, and no device helper is added or changed:
sm_103a device header +0 lines (112 -> 112), 0 removed, 20 reordered;
sm_103a host header identical to the base (52 lines); sm_100a device
header +0 lines (112 -> 112), 0 removed, 1 reordered; sm_100a host
header identical to the base (52 lines); device helpers: base 69 files,
0 added, none removed or changed.
- `flashinfer/jit/cake_dsv4.py`: the `_ARCH_REGISTRATIONS` entries of
the exported programs are replaced; the upstream
NVFP4 DSv4 decode registrations are preserved verbatim. Loader audit
against the base: sm_103a: 27 program entries replaced (0 added, 0
removed), 0 upstream NVFP4 entries touched (NVFP4 record diff 0 lines),
all 34 `min_cuda_version` stamps unchanged, summary passed_count
196/197; sm_100a: 27 program entries replaced (0 added, 0 removed), 0
upstream NVFP4 entries touched (NVFP4 record diff 0 lines), all 34
`min_cuda_version` stamps unchanged, summary passed_count 197/197.
- Export protocol unchanged (197 shapes per architecture; correctness +
source/export timing parity gates;
rows that fail only a timing gate are re-measured in place from the
closed prior; the documented sm_100a
measurement-gate exception - at most the two `bf16_h64_prefill`
hardening rows 000016 / 000036 failing only
`directional_disagreement` with correct output after the in-place
re-measure - is accepted when it occurs, the gate
itself is unchanged and every occurrence is recorded in the sm_100a
summary). For this release the project owner
also accepted one sm_103a row as a documented exception: the
`bf16_h64_compressed` hardening row 000046 (~10 us;
neither of its two units is a lever unit: its main unit is unchanged and
its reduce unit is one of the nine refreshed
in place) fails only a source/export timing gate with correct output,
once in the full run and once after the
in-place re-measure; both measurements are in the sm_103a line below and
the row stays recorded in the sm_103a
summary. In the full runs one further row per architecture (sm_103a
hardening-000002 of `bf16_h64_prefill`, sm_100a
hardening-000031 of `bf16_h128_topk128x_row_first`; correct output both)
failed only a timing gate and passed the
in-place re-measure. sm_103a: 196/197 shapes passed (correctness
197/197); the bf16_h64_compressed hardening row 000046 (~10 us; not one
of the three lever units) fails only a source/export timing gate with
correct output: directional_disagreement in the full run (source
0.009536 ms / export 0.009376 ms); source_over_export after the in-place
single-worker re-measure (source 0.009504 ms / export 0.010112 ms); the
project owner accepted this one row for this release as a documented
exception, the gate itself is unchanged and the row stays recorded in
the sm_103a summary. sm_100a:
197/197 shapes passed (correctness 197/197). Release commit:
`3d8b4291bdf0` (sm_103a `a820647ba12e`, sm_100a `3d8b4291bdf0`), two
commits on upstream main
  `fd14b3056d0`.

## Measured (paired CUPTI ABBA on the lever trees: legs A1 B1 B2 A2
after a discarded warm leg, kernel-sum medians, shard-level
identical-text control arm within +-0.5 % in the same step, per-row
control values quoted where they matter; ratios < 1 = faster)
- `fp8_h64_source_exact` (3 rows): GB300 (sm_103a) geomean B/A 0.9830
(-1.70 %; rows 0.9894 / 0.9805 / 0.9790; control
1.0030). B200 (sm_100a) 0.9872 (-1.28 %; rows 0.9841 / 0.9878 / 0.9897;
control 1.0000). No row > 1.01 on either
architecture. Launch-history regime check (export-protocol replica,
production-regime B/A): 0.9927 GB300 / 0.9930
  B200, PASS on both.
- `fp8_lowhead_prefill` (target row hardening-000070): GB300 0.9690
(-3.1 %; shard control 1.0001; worst other row
1.0045). B200 0.9807 (-1.9 %; shard control 1.0009); hardening-000072
read 1.0101 in the forward arm order (per-row
cap 1.01) with the identical-text control at 1.0101 / 1.0121 on the same
row; the same-order in-place re-measure
repeated it (target 0.9794), and the reversed-order re-measure read the
target at 0.9778 and that row at 0.9860
(arm-order artefact; no row > 1.01). The record rates the sm_100a leg
adoptable under that reversed-order reading and
left the choice between it and the earlier same-order rule (under which
the repeated > 1.01 reading would have
rejected the sm_100a leg as measured) to the merge owner; the project
owner merged the change for both architectures.
  Regime check 4/4 PASS on both architectures.
- `fp8_h8_h16_source_exact` (11 rows): GB300 0.9664 (-3.36 %; rows
0.9635..0.9701, 11/11 <= 0.99, 0 > 1.01; control
0.9996). B200: not measured on the lever tree before adoption. The
project owner adopted the change on both
architectures with the sm_100a performance unmeasured (decision of
2026-10-12; bit-identity by construction is
architecture-independent); a delivery-time paired ABBA of the exported
programs (rows served by the three changed
units, 30 rows per architecture; B = the lever-merge tree `b60866bd8de`,
whose rendered program units are identical
to this release tree's, A = the previous export tree `d6b11c4cec9`) is
run for this release; see the next bullet.
- Delivery paired ABBA of the exported programs (rows served by the
three changed units, 30 rows per architecture; B = the
lever-merge tree `b60866bd8de`, whose rendered program units are
identical to this release tree's (checked per
architecture before the export), A = the previous export tree
`d6b11c4cec9`; same protocol): sm_103a 30/30 rows PASS (geometric mean
B2/A2 = 0.9844 with B = the lever-merge tree and A = the previous export
tree, so < 1 is faster; 14 rows <= 0.99, 0 rows > 1.01, max row 1.0067;
identical-text control 1.0001, max control deviation 0.0045 <= 0.005; 1
row whose A/A spread exceeded 0.0049 was repeated in place and passed;
per program: fp8_h8_h16_source_exact 0.9663 over 11 rows,
fp8_lowhead_prefill 0.9943 over 16 rows, fp8_h64_source_exact 0.9985
over 3 rows); sm_100a 29/30 rows PASS (geometric mean B2/A2 = 0.9843,
same convention; 17 rows <= 0.99; identical-text control 1.0000, max
control deviation 0.0049 <= 0.005; per program: fp8_h8_h16_source_exact
0.9652 over 11 rows, fp8_h64_source_exact 0.9890 over 3 rows,
fp8_lowhead_prefill 0.9968 over 16 rows) and 1 row SLOWER: the 8 us
fp8_lowhead_decode hardening row served by the fp8_lowhead_prefill unit
read 1.0198 in the first run (8.10 -> 8.26 us); the in-place repeat in
the same arm order read 1.0195 (the recorded value) and the repeat with
the arm order reversed 1.0198, with the control at 1.0000 on that row;
the same row is 0.976 on sm_103a. The other 15 rows of that program are
<= 1.01 on sm_100a (all PASS; max 1.0049).

## Gates (per change, on its lever tree, before adoption)
- `fp8_h64_source_exact`, both architectures: render diff against main
limited to its unit; check_rows on all mutation
axes 839/839 plus 213 CPU rule tests; checksel 15/15 on the class rows;
compute-sanitizer synccheck
(hardening-000067 on sm_103a; hardening-000067 and prefill-style-000087
on sm_100a) and memcheck (hardening-000067,
re-run under a 10800 s cap) with `ERROR SUMMARY: 0 errors`; SASS of the
changed unit +4.3 % (sm_103a) / +4.0 %
  (sm_100a) instructions, 128 registers, no local memory.
- `fp8_lowhead_prefill`, both architectures: render diff limited to its
unit; e2e GPU slice 1 passed; check_rows
839/839 plus 241 CPU tests; checksel 47/47; synccheck (hardening-000070,
decode-000006, decode-000054) and memcheck
(hardening-000070, decode-000006) with 0 errors; SASS +3.38 % (sm_103a)
/ +3.32 % (sm_100a) instructions,
  REG 128/128, LOCAL 0/0.
- `fp8_h8_h16_source_exact`, sm_103a: render diff limited to its unit;
checksel 55/55 with the sorted max_abs tables
identical to the base tree; check_rows 839/839 plus 201 CPU tests;
synccheck (hardening-000098, decode-000068,
decode-000055) 0 errors; racecheck 0 hazards; no memcheck (the owner's
sanitizer policy for this round); SASS -1.53 %
instructions, REG 128 / LOCAL 0 unchanged. sm_100a: render diff 30/29/1
(only its unit), render identity bounded to
the mbarrier-init and TMEM-allocation blocks at widths 192 / 256 / 260,
py_compile, and the ptxas spill judge equal
to the base (regs 96, spill 0); no GPU gate, no sanitizer run and no
ABBA on B200.
- Release: loader audit as above; FlashInfer's pinned ruff (v0.12.8,
FlashInfer's own `[tool.ruff]` settings) on the
  released loader: clean (gated before the push).
- Fresh-clone FlashInfer DSv4 tests at the release commit: sm_103a: 521
passed, 4 skipped, 0 failed (161 s; fresh clone at `3d8b4291bdf0` on a
GB300 node) / sm_100a: 521 passed, 4 skipped, 0 failed (218 s; fresh
clone at `3d8b4291bdf0` on a B200 node).

## Changed files
```
    sm_103a commit a820647ba12e (base -> sm_103a; renames = retired unit -> new unit of the same program):
     csrc/cake_dsv4/sm_103a/cake_dsv4_06cdf778054cc6c67dc5_kernel.cu                                                 |   9 ++++++
     csrc/cake_dsv4/sm_103a/cake_dsv4_3b4ec80fd59f1a59eb0d_kernel.cu                                                 |   9 ++++++
     csrc/cake_dsv4/sm_103a/cake_dsv4_6a34a835c2b39424c20c_kernel.cu                                                 |   9 ++++++
     csrc/cake_dsv4/sm_103a/{cake_dsv4_e875bc1d8a3b3ff27030_binding.cu => cake_dsv4_70a0b1ae882054e5c302_binding.cu} |  16 +++++-----
     csrc/cake_dsv4/sm_103a/{cake_dsv4_e875bc1d8a3b3ff27030_kernel.cu => cake_dsv4_70a0b1ae882054e5c302_kernel.cu}   | 129 +++++++++++++++++++++++++++--------------------------------------------------
     csrc/cake_dsv4/sm_103a/{cake_dsv4_8543cb10ca15edd3a26b_binding.cu => cake_dsv4_7682c095a61495bc66df_binding.cu} |  16 +++++-----
     csrc/cake_dsv4/sm_103a/{cake_dsv4_8543cb10ca15edd3a26b_kernel.cu => cake_dsv4_7682c095a61495bc66df_kernel.cu}   | 166 ++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++----------------------------------
     csrc/cake_dsv4/sm_103a/cake_dsv4_8b60cfd54a78d36864f4_kernel.cu                                                 |   9 ++++++
     csrc/cake_dsv4/sm_103a/cake_dsv4_8c2cf89e71be1ebbd233_kernel.cu                                                 |   9 ++++++
     csrc/cake_dsv4/sm_103a/cake_dsv4_9c1ead828285aaa7f400_kernel.cu                                                 |   9 ++++++
     csrc/cake_dsv4/sm_103a/cake_dsv4_a8b112bf2abd1a8ed848_kernel.cu                                                 |   9 ++++++
     csrc/cake_dsv4/sm_103a/cake_dsv4_aa6dd9bfdbb2d261b462_kernel.cu                                                 |   9 ++++++
     csrc/cake_dsv4/sm_103a/cake_dsv4_device_common.cuh                                                              |   4 +--
     csrc/cake_dsv4/sm_103a/cake_dsv4_e900f8c37ff1f0974a39_kernel.cu                                                 |   9 ++++++
     csrc/cake_dsv4/sm_103a/{cake_dsv4_3b2807f9cb6acd058bdf_binding.cu => cake_dsv4_fc0b78470851912fb4c6_binding.cu} |  16 +++++-----
     csrc/cake_dsv4/sm_103a/{cake_dsv4_3b2807f9cb6acd058bdf_kernel.cu => cake_dsv4_fc0b78470851912fb4c6_kernel.cu}   |  81 +++++++++++++++++++++++++++++++++++++++++--------
     flashinfer/jit/cake_dsv4.py                                                                                     |  66 ++++++++++++++++++++--------------------
     17 files changed, 363 insertions(+), 212 deletions(-)
    
    sm_100a commit 3d8b4291bdf0 (sm_103a commit -> sm_100a):
     csrc/cake_dsv4/sm_100a/cake_dsv4_1b4dfa2ab26fc784f640_kernel.cu                                                 |   9 ++++++
     csrc/cake_dsv4/sm_100a/cake_dsv4_2b24cab15b398c9b420a_kernel.cu                                                 |   9 ++++++
     csrc/cake_dsv4/sm_100a/cake_dsv4_3af1afa1871d27324303_kernel.cu                                                 |   9 ++++++
     csrc/cake_dsv4/sm_100a/cake_dsv4_71e0baa44c61b948d82c_kernel.cu                                                 |   9 ++++++
     csrc/cake_dsv4/sm_100a/cake_dsv4_860a0ac41a77c1305873_kernel.cu                                                 |   9 ++++++
     csrc/cake_dsv4/sm_100a/cake_dsv4_8a33d6688c16c25820e9_kernel.cu                                                 |   9 ++++++
     csrc/cake_dsv4/sm_100a/{cake_dsv4_820670a92a2bf9dfb2b0_binding.cu => cake_dsv4_b4379be324141d01636c_binding.cu} |  16 +++++-----
     csrc/cake_dsv4/sm_100a/{cake_dsv4_820670a92a2bf9dfb2b0_kernel.cu => cake_dsv4_b4379be324141d01636c_kernel.cu}   |  81 +++++++++++++++++++++++++++++++++++++++++--------
     csrc/cake_dsv4/sm_100a/{cake_dsv4_f98ac384c6e4f7fb86e4_binding.cu => cake_dsv4_cd52094425e6b8d7102c_binding.cu} |  16 +++++-----
     csrc/cake_dsv4/sm_100a/{cake_dsv4_f98ac384c6e4f7fb86e4_kernel.cu => cake_dsv4_cd52094425e6b8d7102c_kernel.cu}   | 129 +++++++++++++++++++++++++++--------------------------------------------------
     csrc/cake_dsv4/sm_100a/cake_dsv4_device_common.cuh                                                              |   2 +-
     csrc/cake_dsv4/sm_100a/cake_dsv4_e1c7ffd7ad7de34b2096_kernel.cu                                                 |   9 ++++++
     csrc/cake_dsv4/sm_100a/cake_dsv4_efb864796f11291dc52c_kernel.cu                                                 |   9 ++++++
     csrc/cake_dsv4/sm_100a/cake_dsv4_fc73aade5a5f4f85a9e8_kernel.cu                                                 |   9 ++++++
     csrc/cake_dsv4/sm_100a/{cake_dsv4_d7c58d0212deccbcaf48_binding.cu => cake_dsv4_fcaeb5ddd771372bdb3d_binding.cu} |  16 +++++-----
     csrc/cake_dsv4/sm_100a/{cake_dsv4_d7c58d0212deccbcaf48_kernel.cu => cake_dsv4_fcaeb5ddd771372bdb3d_kernel.cu}   | 166 ++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++----------------------------------
     flashinfer/jit/cake_dsv4.py                                                                                     |  66 ++++++++++++++++++++--------------------
     17 files changed, 362 insertions(+), 211 deletions(-)
```

## Tests
- `tests/mla/test_cake_dsv4.py`,
`tests/mla/test_cake_dsv4_hardening.py`: unchanged; run on a fresh clone
at the
  release commit on both architectures (results above).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [52b0de0](https://github.com/flashinfer-ai/flashinfer/commit/52b0de0b815419fbc890a0d049a243f01b4e231a)

- **作者**: eigen
- **时间**: 2026-10-15T21:29:50Z
- **提交信息**: feat(cake_comm): MNNVL MoE all-to-all cake backend: fused quantized combine, vectorized BF16 combine, fused sanitize (regenerated sm100/sm103 bundles) (#6545)

## 📌 Description

This PR updates the kernels behind `backend="cake"` in the MNNVL MoE
all-to-all, which dispatches and combines MoE tokens across ranks over
NVLink and multi-node NVLink. The default backend, `backend="trtllm"`
(TRT-LLM MNNVL MoeAlltoAll), is unchanged, and the new kernels and
routes run only when `backend="cake"` is selected. The trtllm tests are
unaffected. With the default left as `trtllm`, the test files pass on
this branch's host routing commit (the head before the whitespace-only
formatting commit) on both architectures (188 passed / 1 skipped
single-process, 25 passed under `mpirun -n 4`; see Tests).

The kernel generator produces the cake backend kernels, which are
checked in as device bundles under `csrc/generated/`. The cake launcher
in `moeAlltoAllFusedKernels.cu` declares, preloads and launches them.
This branch is the pinned revision `ceb589ce` (FlashInfer 0.7.2) plus
three commits:
- "mnnvl a2a: regenerate the cake backend bundles (sm100/sm103, 33
kernels)"
- "mnnvl a2a: route the fused quantized combine, BF16 vector combine and
fused sanitize (backend=cake)"
- "mnnvl a2a: clang-format moeAlltoAllFusedKernels.cu (pre-commit)"

### Kernel changes

1. **Block quantization fused into the per-TOP_K combine.** MX/NVFP4
block quantization now runs inside the combine kernel
(`combine_quantized_top_k_{1,2,4,6,8,10,12,14,16,18,22}`). The quantized
combine takes one launch instead of a combine followed by a quantize,
and no BF16/FP16 carrier tensor is written. The carrier rounding is
reproduced in registers, so the quantized values and scale bytes match
the two-kernel path byte for byte on all tested cases (see Precision).
2. **16-byte vectorized BF16 combine for TOP_K 1, 2 and 4.**
`combine_bf16_vector_top_k_{1,2,4}` replace the generic combine's scalar
2-byte loads for these TOP_K values. They keep the same pinned FP32
reduction tree for every output element.
3. **Sanitize pass fused into the dispatch kernel's last-arriving CTA.**
The dispatch kernel gains two trailing arguments,
`sanitize_payload_index` and `invalid_expert_id`, which let the
last-arriving CTA run the sanitize fill. On the cake project's host this
removes the separate sanitize launch (two-rank dispatch path: 3 launches
to 2). In this PR the FlashInfer launcher passes `-1, 0` for the two new
arguments and keeps its separate sanitize launch, so the fused fill is
not enabled on the FlashInfer path (see Host routing).

Each change was measured with paired A/B runs on the cake project's own
launch path, against the kernel set without that change. "How to read
the row-level columns" below explains what that path measures.

| change | rows that exercise it | B200 (sm_100a) | GB300 (sm_103a) |
|---|---|---|---|
| vectorized BF16 combine | mpi2 combine rows with TOP_K 1/2 | rows
+25..+34 %; combine kernel x2.5-3 | rows +11..+23 % (inside the mpi2
noise band); combine kernel 26.9-31.8 us -> 6.5-6.9 us (x4.1-4.8) |
| fused sanitize | mpi2 dispatch rows | rows +8..+56 % (inside the mpi2
noise band, 51-97 %); production-kernel time +57..+169 % beyond its band
(20-48 %) on six of the eight dispatch rows, since the separate sanitize
launch and its handshake are gone | rows inside the mpi2 noise band;
max-over-ranks kernel time 146-164 us -> 80-92 us (+75..+98 %) on every
dispatch row |
| fused quantized combine (10 interleaved pairs) | the six quantized
logical_simulation rows, which run a simulation-kernel fusion that drops
the quantize launch but still writes the carrier; the carrier-less
production kernel itself has no timing row (see below) | +1.26..+3.20 %,
no loss attributable to the change | +1.40..+2.60 % (kernel level
+1.42..+2.65 %), 0 losses |

None of the mpi2 or mpi8 rows produces a quantized combine output. The
production fused quantized kernel is therefore covered by byte-parity
tests (see Precision) but has no timing row.

### Regenerated device bundles

`csrc/generated/mnnvl_moe_alltoall_sm100.cu` and
`csrc/generated/mnnvl_moe_alltoall_sm103.cu` hold 33 kernels each and
have identical content: 335221 bytes, sha256
`c634bc0cd4671a942df36dadb2023f8b8e0360a23b9e2e4101239727d95fd571`. They
use the same file form as the pinned bundles (SPDX header, `#include
<stdint.h>`, `FLASHINFER_INF`). The kernel text is byte-identical to the
build that was benchmarked below.

### Host routing (second commit, 5 files)

-
`csrc/nv_internal/tensorrt_llm/kernels/communicationKernels/moeAlltoAllFusedKernels.cu`:
- Declares the new kernel symbols (`combine_bf16_vector_top_k_{1,2,4}`,
`combine_quantized_top_k_{1,2,4,6,8,10,12,14,16,18,22}`) and the two new
dispatch arguments.
- Selects routes in `moe_a2a_dispatch_launch`,
`moe_a2a_prepare_combine_launch` and `moe_a2a_combine_launch`.
- BF16 vector combine: used when TOP_K is 1, 2 or 4, the payload is BF16
and `elements_per_token % 8 == 0`. Grid `max(local_num_tokens, 1)`, 256
threads.
- Fused quantized combine: used when `quant_mode != NONE`,
`local_num_tokens > 0`, `elements_per_token % 32 == 0` and no BF16
carrier variant (vector, top-k 6, top-k 8) applies. 256 threads, no
dynamic shared memory, grid `max(local_num_tokens, 1)`.
- Dispatch: `moe_a2a_dispatch_launch` passes `-1, 0` for
`sanitize_payload_index` / `invalid_expert_id` and keeps the separate
sanitize launch. The fused in-kernel fill is not enabled on the
FlashInfer path.
- `csrc/trtllm_moe_alltoall.cu` (`moeA2ACombineIntoOp`): when the
combine fuses quantization (`moe_a2a_combine_fuses_quantization()`),
skips the separate quantize launch and the temporary carrier. The trtllm
side returns false, so the default path is unchanged.
- `moeAlltoAllKernels.cu` (+4) and `moeAlltoAllKernels.h` (+4): the
header declares `moe_a2a_combine_fuses_quantization()` and the trtllm
translation unit defines it to return false, so the default path is
unchanged.
- `tests/comm/test_mnnvl_moe_alltoall_fused_adapter.py`: adds
exact-boundary tests for the BF16 vector routes and the stage grid.

The third commit only changes whitespace in
`moeAlltoAllFusedKernels.cu`: clang-format v19.1.1 reflowed the macro
continuation lines and the `FLASHINFER_CHECK` argument wrapping, and the
file is token-identical before and after (662 lines).

### Precision

- **Tolerances are unchanged:**
  - dispatch, integer and scale bytes: bit-exact
  - BF16/FP16: atol = rtol = 1e-2
  - FP8: 0.1 / 0.1
  - FP4 (dequantized): 1.0 / 0.1
- **Pinned numerics are kept:** TOP_K reduction tree, FP32 accumulation
order, `rcp.approx`, and the E8M0 / E4M3 / E2M1 conversion boundaries.
- **Fused quantized combine:** quantized values and scale bytes are
bitwise identical to the two-kernel path (combine, then quantize).
- Fused-vs-two-kernel byte-parity tests passed on both architectures: 16
fusion tests (`torch.equal` on quantized values and scale bytes: 10
production cases and 6 simulation rows). The 121-row simulation
correctness run also passed; it is a tolerance check, not a byte
comparison.
- An extended set also passed on both architectures. It has 25 tests
covering all 11 exported TOP_K values, 9 quantization x layout pairs,
PDL, low-precision mode and FP16 edge carriers. It adds an 80-row
simulation `torch.equal` comparison and launcher fused cases with 0 byte
mismatches.
- **BF16 vector combine:** BF16/FP16 combine outputs are bitwise
identical to the kernels at the pinned revision by construction, because
the per-element reduction tree is the same.
- **Fused sanitize:** dispatch output is bitwise identical to the
previous kernels by construction (integer and byte outputs unchanged);
the harness's exact-byte dispatch checks in the correctness view below
pass on both architectures.
- **Correctness view:** before timing, every benchmark cell first runs
the full correctness view of its own partition at the tolerances above.
Over the four partitions that is 159 rows per architecture:
logical_simulation 126, mpi2 16, mpi8 5, single_gpu_real 12.
- Over the cells paired with cake at the pinned revision (5 rounds x 2
runs x 4 partitions, all ranks), correctness passed in 120/120 rank
reports per architecture, with 0 failed and 0 missing.

### Measurement method

- **Rows:** 40 per architecture from the cake project's benchmark
harness for this operator, in four partitions:
  - single_gpu_real: 2 rows, one GPU
  - logical_simulation: 17 rows, multi-rank traffic simulated on one GPU
  - mpi2: 16 rows on 2 ranks (8 dispatch, 8 combine)
  - mpi8: 5 rows on 8 ranks
- **Timer:** CUPTI activity tracing (GPU time) with cold L2 and no host
timers. Each row's latency is the max over ranks of the per-rank CUPTI
medians.
- **Pairing:** the candidate arm and one baseline arm alternate in the
same process on the same GPUs. Each run is 5 paired rounds per arm per
partition. A row's speedup is the median of the per-round ratios, so it
can differ from the quotient of the displayed times.
- **Runs:** two independent runs per architecture on whole-node
allocations with the other GPUs idle. Each B200 run continued across
consecutive allocations; every hand-off happened between benchmark
cells, and no row was re-measured.
- **Topologies:**
  - B200 (sm_100a): 1 node x 8 GPUs, intra-node NVLink
- GB300 (sm_103a): 2 nodes x 4 GPUs, cross-node MNNVL in an NVL72 domain
- **SM clock** (NVML, sampled every 50 ms during one benchmark call):
  - B200: 1965 MHz (max 1965; 416 samples, min = median = max)
  - GB300: 2070 MHz (max 2070; 389 samples, min = median = max)
- **Pass criteria per run:** every row is faster than trtllm, and every
row is at least as fast as cake at the pinned revision or within the
row's A/A noise band (the spread measured when the same kernels run in
both arms). No row needed the band.
- **GB300 re-measurement:** two run 1 mpi2 cells against cake at the
pinned revision (rounds 1 and 3) overlapped for about two minutes during
a hand-off between two serial benchmark chains on the same allocation.
Both were re-measured serially on the idle allocation, and the originals
were archived before aggregation.

#### How to read the row-level columns

- **trtllm default** and **cake at pinned revision ceb589ce** are
FlashInfer at the pin, called through the harness with
`backend="trtllm"` and `backend="cake"`. The times shown are the run 1
medians.
- **this PR** is the harness's candidate arm: the kernel text of this
PR's bundles, launched by the cake project's own host. That host uses
CUDA graphs on the multi-rank rows and on multi-launch simulation rows.
  - On mpi2 and mpi8 rows, it runs the production kernels exported here.
- On logical_simulation rows, it runs the cake project's single-GPU
simulation kernels, which are not part of the bundles. Those rows also
include cake-side host changes that are not in this PR: graph replay of
multi-launch simulated rows, and lane-parallel token routing in the
simulated dispatch.
- This column is not a measurement of FlashInfer's `backend="cake"` path
with this PR applied; such end-to-end timings were not taken. The
FlashInfer tests listed below run this PR's bundles through the adapter
for correctness.
- **Row-level speedups include launch-path and harness differences, not
only kernel speed.** Before the changes in this PR, on the GB300 mpi8
rows (span numbers from `basic_bf16`):
- The `backend="cake"` arm ran the same kernels as the cake host but
measured 717.0 us of GPU span against 395.6 us. The difference came from
eager launches with about 46 us of inter-kernel gaps, plus extra full
passes over the payload in the harness's baseline route.
- At the production-kernel level, across the five GB300 mpi8 rows,
trtllm's kernels took 1.07-1.21x the time of the cake kernels on the
cake host.
- The same cake kernels behind FlashInfer's adapter took 1.20-1.31x the
time they took on the cake host. This was attributed to the adapter's
launch count and workspace layout.
- The production-kernel and kernel-level columns below count production
kernels only, so they are the evidence for kernel speed.

### Floor model and kernel-level column

Each row's floor is the larger of a byte floor and a launch + handshake
floor. All inputs were measured on the same clusters and GPU models as
the runs below:
- **Byte floor:**
- mpi2 and mpi8 rows: NVLink push time at the row's deduplicated
per-peer dispatch bytes, plus NVLink pull time at its per-peer combine
bytes (both from measured probe curves), plus local bytes / HBM copy
bandwidth (B200 3444 GB/s, GB300 3533 GB/s).
- single_gpu_real and logical_simulation rows: all bytes / HBM copy
bandwidth, plus launches x empty-kernel launch time.
- **Launch + handshake floor:** production launches x empty-kernel
launch time (B200 1.25 us, GB300 1.26 us), plus handshakes x the
measured two-rank system-scope ping-pong round trip (B200 intra-node
5.84 us; GB300 intra-node 3.52 us, cross-node 4.16 us). This term binds
only on the eight mpi2 dispatch rows per architecture (B200 8.34 us,
GB300 6.05 us). Every other row keeps its byte floor.

**Production kernels (us)** in the per-row tables = production-kernel
CUPTI time of the cake kernels, taken on rank 0 with 20 samples per row
from the rounds of both runs. **Kernel-level % of measured floor** =
floor / production kernels. Rows at or above 90 % count as at bound:

| | single_gpu_real | logical_simulation | mpi2 | mpi8 | total |
|---|---|---|---|---|---|
| B200 | 1/2 | 0/17 | 3/16 | 0/5 | 4/40 |
| GB300 | 1/2 | 0/17 | 5/16 | 2/5 | 8/40 |

Values above 100 % mean the kernel beat a probe-based component of the
floor. Examples are the launch-bound t10 row (2.0 us GB300 / 2.1 us B200
against a 2.5 us floor) and the pull-latency floor below 1 MB per peer.

Rows below 90 % (B200 36/40, GB300 32/40) each have a gap statement:
- **mpi8:** the gap (production kernels minus floor) is B200 29.4-43.7
us on all five rows and GB300 20.1-35.2 us on `fp8`, `nvfp4` and
`validate_bf16`. It splits into:
- handshake kernels (prepare_dispatch, stage and publish: flag protocol,
generation advance and the readiness wait including inter-rank skew,
with their launches): B200 6.9-13.6 us, GB300 9.7-26.4 us
- bytes excess (dispatch and combine time above their byte-floor
components): B200 23.2-32.3 us, GB300 15.0-17.5 us
- residual (gap minus the columns above): B200 -2.1 to -0.6 us, GB300
-6.8 to -0.5 us. A negative residual means a transfer kernel ran faster
than its probe-based byte-floor component, so the two columns above add
up to more than the gap.

A separate per-kernel attribution of the GB300 mpi8 rows, taken on one
checkpoint round of an earlier kernel set rather than the rounds above,
found `dispatch` at 96 % and `combine` at about 97 % of their byte
floors on the BF16 rows. In that attribution the distance to the row
floor is the `publish_combine` readiness wait (6.8-46.7 us across the
five rows), which is inter-rank skew built up in the harness phase
between dispatch and combine.

For `validate_bf16`, that attribution puts the transport part at 83 %
(GB300) / 84 % (B200, from rounds measured before the changes in this
PR) of its floor. The final kernel-level values in the per-row tables
are 86.3 % (GB300) / 83.5 % (B200). The 3.1-3.4 ms of harness validation
kernels inside the timed region count as their own measured floor.
- **mpi2:** latency rows on 22-552 KB transfers. Their gaps (GB300
3.8-7.9 us, B200 3.1-17.6 us) are attributed to the flag round trip and
the skew between the two ranks. In the gap tables the dispatch rows book
this gap as dispatch time above its byte-floor component (the kernel's
in-kernel wait for the peer; `dominant` = bytes), and the combine rows
book it under the handshake kernels (`dominant` = handshake).
- **logical_simulation:** time is spent in the simulation kernel's
serial per-rank emulation while moving < 2 MB, not in transfer or
launch.
- **single_gpu_real t902:** the local copy runs below the asymptotic HBM
bandwidth at a payload-sized working set.

### Summary

The pass criteria held on every row in both runs on both architectures:
40/40 rows faster than trtllm, and 40/40 rows at least as fast as cake
at the pinned revision, with no row using the noise band.

The tightest row on both architectures is mpi8
`hard_documented_validate_bf16_w8_t1024_v7168_e256_k8` (run 1 / run 2):

| | vs trtllm | vs pinned cake |
|---|---|---|
| B200 | 1.0198 / 1.0178 | 1.0275 / 1.0284 |
| GB300 | 1.0354 / 1.0309 | 1.0403 / 1.0421 |

Per-partition geomean of the row speedups (run 1 / run 2):

| partition (rows) | B200 vs trtllm | B200 vs pinned cake | GB300 vs
trtllm | GB300 vs pinned cake |
|---|---|---|---|---|
| single_gpu_real (2) | 7.4477 / 7.3229 | 7.0075 / 6.9395 | 9.0101 /
9.1151 | 9.3137 / 9.2842 |
| logical_simulation (17) | 4.6146 / 4.5749 | 4.6957 / 4.6779 | 6.0510 /
6.1319 | 6.0653 / 6.1330 |
| mpi2 (16) | 2.3731 / 2.6122 | 2.5631 / 2.5006 | 3.0868 / 2.8338 |
2.9247 / 2.7155 |
| mpi8 (5) | 1.3837 / 1.3809 | 1.4333 / 1.4375 | 1.4007 / 1.3819 |
1.4536 / 1.4471 |

### Per-row results: B200 (sm_100a)

| partition | row | trtllm default (us, run 1) | cake at pinned revision
ceb589ce (us, run 1) | this PR (us, run 1 / run 2) | speedup vs trtllm
(run 1 / run 2) | speedup vs pinned cake (run 1 / run 2) | production
kernels (us) | floor (us) | kernel-level % of measured floor |
|---|---|---|---|---|---|---|---|---|---|
| mpi8 | `hard_documented_basic_bf16_w8_t1024_v7168_e256_k8` | 675.5 |
710.5 | 404.9 / 409.9 | 1.670 / 1.657 | 1.755 / 1.757 | 250.5 | 220.6 |
88.1 |
| mpi8 | `hard_documented_fp8_w8_t1024_v7168_e256_k8` | 854.5 | 890.7 |
572.2 / 578.4 | 1.487 / 1.477 | 1.546 / 1.545 | 200.1 | 169.3 | 84.6 |
| mpi8 | `hard_documented_nvfp4_w8_t1024_v7168_e256_k8` | 1769.6 |
1807.2 | 1455.0 / 1473.3 | 1.209 / 1.211 | 1.239 / 1.241 | 182.1 | 147.0
| 80.7 |
| mpi8 | `hard_documented_per_phase_bf16_w8_t1024_v7168_e256_k8` | 685.1
| 715.2 | 407.9 / 416.3 | 1.656 / 1.665 | 1.751 / 1.772 | 250.0 | 220.6
| 88.2 |
| mpi8 | `hard_documented_validate_bf16_w8_t1024_v7168_e256_k8` | 3747.2
| 3720.8 | 3671.5 / 3686.9 | 1.020 / 1.018 | 1.027 / 1.028 | 264.3 |
220.6 | 83.5 |
| mpi2 | `source_mpi2_combine_random_k1_plain` | 289.7 | 299.0 | 70.5 /
69.1 | 3.919 / 4.139 | 4.246 / 4.299 | 28.4 | 25.2 | 88.7 |
| mpi2 | `source_mpi2_combine_random_k2_lora` | 323.3 | 346.8 | 81.9 /
82.0 | 3.828 / 4.022 | 4.084 / 4.188 | 29.5 | 27.6 | 93.4 |
| mpi2 | `source_mpi2_combine_random_k2_plain` | 299.8 | 303.7 | 74.4 /
74.9 | 3.925 / 3.905 | 4.123 / 4.032 | 27.0 | 27.6 | 102.3 |
| mpi2 | `source_mpi2_combine_random_k8_plain` | 291.6 | 297.4 | 94.3 /
96.5 | 2.974 / 2.971 | 3.028 / 3.128 | 31.0 | 30.0 | 96.8 |
| mpi2 | `source_mpi2_combine_uniform_k1_plain` | 275.3 | 289.4 | 70.1 /
69.4 | 3.791 / 3.962 | 4.194 / 4.261 | 27.0 | 23.9 | 88.5 |
| mpi2 | `source_mpi2_combine_uniform_k2_plain` | 300.3 | 308.5 | 72.3 /
73.1 | 3.985 / 4.127 | 4.315 / 4.404 | 27.7 | 24.2 | 87.3 |
| mpi2 | `source_mpi2_combine_uniform_k8_lora` | 329.9 | 325.4 | 90.4 /
87.7 | 3.465 / 3.871 | 3.720 / 3.653 | 30.6 | 25.6 | 83.7 |
| mpi2 | `source_mpi2_combine_uniform_k8_plain` | 287.5 | 292.7 | 82.3 /
84.7 | 3.431 / 3.504 | 3.364 / 3.441 | 30.0 | 25.6 | 85.4 |
| mpi2 | `source_mpi2_dispatch_random_k1_plain` | 92.2 | 78.9 | 72.7 /
49.7 | 1.248 / 1.892 | 2.123 / 1.732 | 13.9 | 8.3 | 59.9 |
| mpi2 | `source_mpi2_dispatch_random_k2_plain` | 98.1 | 78.5 | 43.5 /
68.3 | 2.089 / 1.565 | 1.528 / 1.939 | 16.0 | 8.3 | 52.0 |
| mpi2 | `source_mpi2_dispatch_random_k8_lora` | 90.8 | 79.9 | 34.9 /
57.4 | 2.313 / 1.659 | 1.498 / 1.851 | 21.6 | 8.3 | 38.6 |
| mpi2 | `source_mpi2_dispatch_random_k8_plain` | 81.5 | 63.6 | 52.1 /
30.9 | 1.682 / 1.989 | 1.428 / 1.208 | 16.8 | 8.3 | 49.5 |
| mpi2 | `source_mpi2_dispatch_uniform_k1_plain` | 99.6 | 79.0 | 62.6 /
42.4 | 1.161 / 1.731 | 1.842 / 1.346 | 14.2 | 8.3 | 58.6 |
| mpi2 | `source_mpi2_dispatch_uniform_k2_plain` | 79.9 | 65.9 | 59.2 /
64.6 | 1.405 / 1.526 | 1.480 / 1.823 | 14.6 | 8.3 | 57.3 |
| mpi2 | `source_mpi2_dispatch_uniform_k8_lora` | 108.4 | 74.1 | 63.1 /
61.9 | 1.179 / 1.786 | 1.389 / 1.563 | 21.7 | 8.3 | 38.4 |
| mpi2 | `source_mpi2_dispatch_uniform_k8_plain` | 92.5 | 85.2 | 54.4 /
41.4 | 1.649 / 2.380 | 2.693 / 1.515 | 25.9 | 8.3 | 32.2 |
| logical_simulation | `current_compact_ep4_t4_v256_e64_k8` | 209.9 |
213.0 | 22.6 / 23.5 | 9.311 / 8.913 | 8.811 / 8.808 | 23.9 | 5.0 | 21.0
|
| logical_simulation | `current_eplb_w4_t16_v16_e32` | 203.7 | 204.7 |
30.9 / 30.9 | 6.608 / 6.586 | 6.604 / 6.757 | 30.9 | 5.0 | 16.1 |
| logical_simulation | `current_fp8_combine_w8_t16_v7168_k8_workspace` |
2172.4 | 2225.2 | 989.8 / 994.2 | 2.210 / 2.177 | 2.230 / 2.233 | 994.4
| 26.2 | 2.6 |
| logical_simulation | `current_nondiv_w4_t16_v32_e6` | 132.6 | 132.2 |
7.0 / 6.9 | 19.149 / 19.139 | 19.170 / 17.430 | 6.9 | 5.0 | 71.9 |
| logical_simulation | `current_rankmask_w4_t16_v32_dead2` | 306.7 |
318.9 | 62.7 / 62.9 | 4.878 / 4.866 | 5.066 / 5.106 | 62.8 | 10.0 | 15.9
|
| logical_simulation |
`focused_combine_w4_t16_v2880_k4_mxfp8_layout_8x4` | 1279.2 | 1334.2 |
419.5 / 413.3 | 3.058 / 3.106 | 3.184 / 3.234 | 414.8 | 10.7 | 2.6 |
| logical_simulation |
`focused_combine_w8_t16_v4096_k10_mxfp4_layout_128x4` | 2346.6 | 2460.3
| 666.2 / 663.5 | 3.526 / 3.543 | 3.696 / 3.742 | 663.8 | 24.0 | 3.6 |
| logical_simulation |
`focused_combine_w8_t16_v4096_k16_nvfp4_layout_128x4` | 2312.5 | 2461.7
| 783.0 / 784.8 | 2.954 / 2.939 | 3.135 / 3.137 | 784.7 | 24.7 | 3.1 |
| logical_simulation |
`focused_combine_w8_t16_v4096_k22_mxfp4_layout_128x4` | 2356.4 | 2490.0
| 929.0 / 936.5 | 2.536 / 2.531 | 2.679 / 2.657 | 930.8 | 25.0 | 2.7 |
| logical_simulation |
`focused_combine_w8_t16_v4096_k8_mxfp4_layout_128x4` | 2341.0 | 2425.0 |
572.7 / 579.6 | 4.100 / 4.039 | 4.221 / 4.183 | 579.8 | 23.5 | 4.1 |
| logical_simulation |
`focused_combine_w8_t16_v5120_k6_mxfp4_layout_128x4` | 2331.7 | 2419.5 |
645.6 / 656.6 | 3.632 / 3.546 | 3.762 / 3.680 | 654.5 | 23.9 | 3.7 |
| logical_simulation |
`focused_combine_w8_t16_v7168_k8_none_linear_pdl0` | 2180.5 | 2219.7 |
994.3 / 999.0 | 2.181 / 2.205 | 2.220 / 2.230 | 996.8 | 26.2 | 2.6 |
| logical_simulation | `focused_larger_payloads_w8_t16_v2048_p5` | 519.7
| 524.6 | 106.5 / 107.8 | 4.904 / 4.839 | 4.861 / 4.867 | 107.6 | 11.5 |
10.7 |
| logical_simulation | `focused_larger_payloads_w8_t16_v2048_p6` | 575.5
| 580.1 | 106.8 / 107.0 | 5.426 / 5.311 | 5.353 / 5.473 | 107.0 | 11.8 |
11.0 |
| logical_simulation |
`focused_lora_combine_1_w4_t16_v4096_k2_workspace` | 1342.0 | 1367.2 |
548.5 / 547.8 | 2.444 / 2.450 | 2.494 / 2.495 | 549.9 | 10.7 | 1.9 |
| logical_simulation | `focused_sanitize_w2_t64` | 123.2 | 124.2 | 16.3
/ 16.5 | 7.611 / 7.426 | 7.898 / 7.757 | 15.8 | 2.5 | 15.8 |
| logical_simulation | `focused_simulated_dispatch_w2_t5_v8` | 93.6 |
93.3 | 7.9 / 8.0 | 11.831 / 11.711 | 11.663 / 11.656 | 8.0 | 2.5 | 31.2
|
| single_gpu_real | `focused_object_roundtrip_t10_v8_e8_k2` | 71.4 |
75.3 | 2.1 / 2.1 | 34.969 / 33.830 | 37.143 / 36.524 | 2.1 | 2.5 | 121.0
|
| single_gpu_real |
`focused_object_roundtrip_t902_v7168_e256_k8_payload_external_output_provided`
| 169.6 | 141.3 | 106.9 / 107.0 | 1.586 / 1.585 | 1.322 / 1.318 | 107.0
| 88.8 | 83.0 |

### Per-row results: GB300 (sm_103a)

| partition | row | trtllm default (us, run 1) | cake at pinned revision
ceb589ce (us, run 1) | this PR (us, run 1 / run 2) | speedup vs trtllm
(run 1 / run 2) | speedup vs pinned cake (run 1 / run 2) | production
kernels (us) | floor (us) | kernel-level % of measured floor |
|---|---|---|---|---|---|---|---|---|---|
| mpi8 | `hard_documented_basic_bf16_w8_t1024_v7168_e256_k8` | 676.0 |
722.6 | 410.0 / 416.0 | 1.670 / 1.623 | 1.763 / 1.743 | 237.9 | 222.7 |
93.6 |
| mpi8 | `hard_documented_fp8_w8_t1024_v7168_e256_k8` | 838.4 | 885.9 |
568.7 / 564.8 | 1.489 / 1.479 | 1.561 / 1.557 | 191.0 | 170.9 | 89.5 |
| mpi8 | `hard_documented_nvfp4_w8_t1024_v7168_e256_k8` | 1764.1 |
1801.4 | 1413.5 / 1414.8 | 1.245 / 1.245 | 1.289 / 1.268 | 179.3 | 148.0
| 82.5 |
| mpi8 | `hard_documented_per_phase_bf16_w8_t1024_v7168_e256_k8` | 686.0
| 723.6 | 410.5 / 418.0 | 1.683 / 1.635 | 1.759 / 1.770 | 235.9 | 222.7
| 94.4 |
| mpi8 | `hard_documented_validate_bf16_w8_t1024_v7168_e256_k8` | 3576.0
| 3580.4 | 3467.6 / 3457.0 | 1.035 / 1.031 | 1.040 / 1.042 | 257.9 |
222.7 | 86.3 |
| mpi2 | `source_mpi2_combine_random_k1_plain` | 451.7 | 453.5 | 89.1 /
100.5 | 4.995 / 4.540 | 4.657 / 5.074 | 22.6 | 21.3 | 93.9 |
| mpi2 | `source_mpi2_combine_random_k2_lora` | 493.2 | 510.1 | 96.4 /
92.3 | 5.047 / 5.445 | 4.747 / 4.913 | 24.0 | 23.5 | 98.0 |
| mpi2 | `source_mpi2_combine_random_k2_plain` | 442.7 | 468.2 | 90.0 /
93.5 | 4.630 / 4.767 | 5.386 / 4.445 | 23.3 | 23.5 | 100.7 |
| mpi2 | `source_mpi2_combine_random_k8_plain` | 447.0 | 464.2 | 101.4 /
104.2 | 4.401 / 4.148 | 4.273 / 4.179 | 27.5 | 25.8 | 93.7 |
| mpi2 | `source_mpi2_combine_uniform_k1_plain` | 440.1 | 451.0 | 93.0 /
88.6 | 4.475 / 4.983 | 4.485 / 4.447 | 21.8 | 19.8 | 90.9 |
| mpi2 | `source_mpi2_combine_uniform_k2_plain` | 441.4 | 454.4 | 83.3 /
92.4 | 5.241 / 4.797 | 4.702 / 4.643 | 24.1 | 20.3 | 84.0 |
| mpi2 | `source_mpi2_combine_uniform_k8_lora` | 498.7 | 501.6 | 102.1 /
98.9 | 4.724 / 5.128 | 4.508 / 4.637 | 26.1 | 21.7 | 82.9 |
| mpi2 | `source_mpi2_combine_uniform_k8_plain` | 441.9 | 454.5 | 98.4 /
96.6 | 4.478 / 4.685 | 4.477 / 4.270 | 25.8 | 21.7 | 83.8 |
| mpi2 | `source_mpi2_dispatch_random_k1_plain` | 163.2 | 167.8 | 76.5 /
99.9 | 2.092 / 1.656 | 1.985 / 1.638 | 10.7 | 6.0 | 56.3 |
| mpi2 | `source_mpi2_dispatch_random_k2_plain` | 164.4 | 168.2 | 80.4 /
102.0 | 1.967 / 1.680 | 1.706 / 1.602 | 11.4 | 6.0 | 53.2 |
| mpi2 | `source_mpi2_dispatch_random_k8_lora` | 175.1 | 179.7 | 88.6 /
107.0 | 1.918 / 1.760 | 1.962 / 1.611 | 13.9 | 6.0 | 43.6 |
| mpi2 | `source_mpi2_dispatch_random_k8_plain` | 162.0 | 169.8 | 66.0 /
107.1 | 2.382 / 1.641 | 1.752 / 1.646 | 13.0 | 6.0 | 46.4 |
| mpi2 | `source_mpi2_dispatch_uniform_k1_plain` | 163.4 | 164.7 | 77.9
/ 103.6 | 2.068 / 1.645 | 1.874 / 1.629 | 10.4 | 6.0 | 58.0 |
| mpi2 | `source_mpi2_dispatch_uniform_k2_plain` | 163.5 | 168.0 | 77.0
/ 105.9 | 1.985 / 1.645 | 1.701 / 1.536 | 10.8 | 6.0 | 56.1 |
| mpi2 | `source_mpi2_dispatch_uniform_k8_lora` | 180.9 | 182.5 | 94.6 /
107.8 | 1.880 / 1.739 | 1.939 / 1.630 | 13.8 | 6.0 | 44.0 |
| mpi2 | `source_mpi2_dispatch_uniform_k8_plain` | 163.1 | 161.1 | 88.4
/ 106.0 | 1.837 / 1.630 | 1.840 / 1.628 | 12.8 | 6.0 | 47.4 |
| logical_simulation | `current_compact_ep4_t4_v256_e64_k8` | 346.6 |
342.4 | 24.4 / 23.3 | 14.047 / 15.010 | 13.523 / 14.991 | 23.6 | 5.1 |
21.5 |
| logical_simulation | `current_eplb_w4_t16_v16_e32` | 349.2 | 339.5 |
51.2 / 51.6 | 6.773 / 6.860 | 6.599 / 6.712 | 51.3 | 5.1 | 9.9 |
| logical_simulation | `current_fp8_combine_w8_t16_v7168_k8_workspace` |
3340.5 | 3346.7 | 1225.2 / 1221.4 | 2.704 / 2.758 | 2.721 / 2.736 |
1224.8 | 26.3 | 2.1 |
| logical_simulation | `current_nondiv_w4_t16_v32_e6` | 219.7 | 211.0 |
7.9 / 7.4 | 27.706 / 29.991 | 27.190 / 27.564 | 7.8 | 5.1 | 64.6 |
| logical_simulation | `current_rankmask_w4_t16_v32_dead2` | 481.7 |
483.4 | 98.4 / 98.5 | 4.845 / 4.944 | 4.851 / 4.996 | 98.5 | 10.1 | 10.3
|
| logical_simulation |
`focused_combine_w4_t16_v2880_k4_mxfp8_layout_8x4` | 1924.9 | 1961.8 |
511.9 / 514.8 | 3.743 / 3.756 | 3.820 / 3.824 | 513.9 | 10.8 | 2.1 |
| logical_simulation |
`focused_combine_w8_t16_v4096_k10_mxfp4_layout_128x4` | 3641.0 | 3750.6
| 789.2 / 788.2 | 4.568 / 4.664 | 4.684 / 4.818 | 788.7 | 24.1 | 3.1 |
| logical_simulation |
`focused_combine_w8_t16_v4096_k16_nvfp4_layout_128x4` | 3545.4 | 3666.5
| 940.4 / 935.0 | 3.740 / 3.815 | 3.864 / 3.958 | 940.3 | 24.8 | 2.6 |
| logical_simulation |
`focused_combine_w8_t16_v4096_k22_mxfp4_layout_128x4` | 3645.2 | 3741.6
| 1087.2 / 1083.5 | 3.351 / 3.366 | 3.432 / 3.461 | 1087.2 | 25.1 | 2.3
|
| logical_simulation |
`focused_combine_w8_t16_v4096_k8_mxfp4_layout_128x4` | 3652.8 | 3685.5 |
709.7 / 707.2 | 5.127 / 5.172 | 5.149 / 5.258 | 708.7 | 23.7 | 3.3 |
| logical_simulation |
`focused_combine_w8_t16_v5120_k6_mxfp4_layout_128x4` | 3649.7 | 3705.2 |
828.8 / 827.9 | 4.350 / 4.460 | 4.444 / 4.503 | 828.6 | 24.1 | 2.9 |
| logical_simulation |
`focused_combine_w8_t16_v7168_k8_none_linear_pdl0` | 3331.5 | 3366.4 |
1223.5 / 1225.2 | 2.708 / 2.734 | 2.739 / 2.759 | 1224.6 | 26.3 | 2.1 |
| logical_simulation | `focused_larger_payloads_w8_t16_v2048_p5` | 851.7
| 852.4 | 105.8 / 103.6 | 8.050 / 8.159 | 8.113 / 8.173 | 104.5 | 11.6 |
11.1 |
| logical_simulation | `focused_larger_payloads_w8_t16_v2048_p6` | 947.4
| 940.1 | 108.8 / 109.3 | 8.668 / 8.709 | 8.665 / 8.583 | 109.1 | 11.9 |
10.9 |
| logical_simulation |
`focused_lora_combine_1_w4_t16_v4096_k2_workspace` | 1987.9 | 1992.7 |
657.8 / 654.1 | 3.017 / 3.030 | 3.010 / 3.081 | 655.3 | 10.8 | 1.7 |
| logical_simulation | `focused_sanitize_w2_t64` | 208.2 | 205.4 | 18.8
/ 17.6 | 11.049 / 11.848 | 10.837 / 11.275 | 18.0 | 2.5 | 14.1 |
| logical_simulation | `focused_simulated_dispatch_w2_t5_v8` | 152.0 |
151.9 | 8.1 / 9.4 | 18.791 / 16.068 | 18.631 / 16.139 | 8.8 | 2.5 | 28.8
|
| single_gpu_real | `focused_object_roundtrip_t10_v8_e8_k2` | 127.3 |
129.8 | 2.0 / 2.0 | 63.516 / 65.098 | 66.097 / 65.787 | 2.0 | 2.5 |
127.5 |
| single_gpu_real |
`focused_object_roundtrip_t902_v7168_e256_k8_payload_external_output_provided`
| 130.8 | 134.4 | 102.4 / 102.5 | 1.278 / 1.276 | 1.312 / 1.310 | 102.5
| 86.7 | 84.6 |

## 🔍 Related Issues

- Builds on #4784, which added the `backend="cake"` kernels.
- Upstream host changes #5336, #5532 and #6376 (all in the pin) were
checked for parity with the cake path; see Reviewer Notes.

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

`pre-commit` was not run in the environment that produced this PR, so
the three boxes above are left unchecked. The repository's `pre-commit`
CI check passes on the current head. It failed on the first push because
clang-format reformatted `moeAlltoAllFusedKernels.cu`, and the third
commit applies that formatting.

`ruff check` and `ruff format --check` on the host change are clean.
They ran on an earlier revision of this branch with the same host commit
content. The branch was later rebuilt on the pin, and that rebuild
changed only the two generated `.cu` bundles.

## 🧪 Tests

- [x] Tests have been added or updated as needed:
`tests/comm/test_mnnvl_moe_alltoall_fused_adapter.py` adds
exact-boundary tests for the BF16 vector routes and the stage grid.
- [x] All tests are passing (`unittest`, etc.): the three MNNVL
all-to-all test files below pass on both architectures, with the default
backend flipped to `cake` and with the unmodified default.

Setup: pin `ceb589ce` + regenerated bundles + host change (the branch
before the whitespace-only formatting commit), JIT-compiled, 4 GPUs of
one node per architecture. For the cake runs, a local pytest plugin (not
part of this PR) flips the public API's default backend to `"cake"`. It
does not touch explicit `backend=` arguments, kernels or tolerances.
Three test files:
- `tests/comm/test_trtllm_moe_alltoall.py` and
`tests/comm/test_mnnvl_moe_alltoall_fused_adapter.py` (single-process).
- `tests/comm/test_mnnvl_moe_alltoall.py`, run under `mpirun -n 4`.

| run | B200 (sm_100a) | GB300 (sm_103a) |
|---|---|---|
| default flipped to `cake`, single-process files | 187 passed / 1
skipped / 1 deselected | 187 passed / 1 skipped / 1 deselected |
| default flipped to `cake`, `mpirun -n 4` `test_mnnvl_moe_alltoall.py`
| 25 passed | 25 passed |
| unmodified default (`trtllm`), single-process files | 188 passed / 1
skipped | 188 passed / 1 skipped |
| unmodified default (`trtllm`), `mpirun -n 4`
`test_mnnvl_moe_alltoall.py` | 25 passed | 25 passed |

The one deselected test,
`tests/comm/test_mnnvl_moe_alltoall_fused_adapter.py::test_workspace_initialization_rendezvous_is_ordered_and_cached_per_backend`,
asserts the trtllm default's workspace identity. It is deselected only
in the flipped-default run and passes in the unmodified run. On CPU, the
adapter tests give 25 passed / 1 skipped.

The same kernel text was also checked with compute-sanitizer in the cake
project:
- **Per-kernel (single GPU):** synccheck, memcheck and racecheck on the
four production entry points (combine, dispatch, prepare_dispatch,
sanitize) report 0 errors and 0 racecheck hazards on both architectures.
- **Multi-rank:** 2-rank, 4-rank and 8-rank targets, each under
synccheck, memcheck and racecheck (nine cells per architecture),
launched per rank through the cake project's native multi-rank launcher.
Completed cells, all clean:
- B200 (sm_100a), all nine cells: the six 2-rank and 4-rank cells pass
in one sealed run (6/6). Each 8-rank cell (synccheck, memcheck,
racecheck) has a sealed stand-alone receipt with status pass and 0
errors (racecheck: 0 hazards). An earlier run of the same three cells
was also clean.
- GB300 (sm_103a), eight of nine cells in one session: the 2-rank and
4-rank cells under all three tools, and the 8-rank synccheck and
memcheck cells, each reporting 0 errors (racecheck: 0 hazards). The
8-rank racecheck cell started after the memcheck cell finished; its
result is below.
- **B200 nine-cell matrix receipt:** combining the nine B200 cells into
one aggregated receipt (the form GB300 produces in one session) needed a
final run of the three 8-rank cells. The first two attempts failed on
bookkeeping grounds (manifest identity, then manifest location), not on
any sanitizer finding, and every rank output in them showed 0 errors
(racecheck: 0 hazards).

Results of the final runs:

B200 8-rank synccheck, memcheck and racecheck cells, run with the sealed
manifest:

B200 (sm_100a): the three 8-rank cells (synccheck, memcheck, racecheck)
were re-run once more in the sealed form the aggregator requires and
passed again: 0 errors each (racecheck 0 hazards).

B200 aggregated matrix receipt for the nine cells:

B200 (sm_100a): the nine cells are now also sealed in one aggregated
receipt, 9/9 passing, every cell 0 errors (racecheck 0 hazards).

GB300 8-rank racecheck cell and the GB300 matrix receipt:

GB300 (sm_103a): all nine cells (2-rank, 4-rank and 8-rank, each under
synccheck, memcheck and racecheck) passed in one sealed run, 9/9, every
cell 0 errors (racecheck 0 hazards).

Bot test commands were posted as PR comments after each of the two
pushes (the initial push and the clang-format commit): `/bot run` and
`@flashinfer-bot run tests/comm/test_trtllm_moe_alltoall.py
tests/comm/test_mnnvl_moe_alltoall.py
tests/comm/test_mnnvl_moe_alltoall_fused_adapter.py`.

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

- **Generated code:** the two bundles come from the kernel generator and
are identical for sm100 and sm103. The hand-written part to review is
the host routing commit.
- **Formatting commit:** the third commit only applies clang-format
whitespace changes to `moeAlltoAllFusedKernels.cu` for the `pre-commit`
check, so the file is token-identical to its version in the host routing
commit.
- **Default path:** `backend="trtllm"` is unchanged. Its test counts are
listed under Tests.
- **Fused sanitize on the FlashInfer path:** `moe_a2a_dispatch_launch`
passes `-1, 0` for `sanitize_payload_index` / `invalid_expert_id` and
keeps FlashInfer's separate sanitize launch, so the in-kernel sanitize
fill stays off on the FlashInfer path. The 3 -> 2 launch saving and the
timing effects quoted for this change were measured on the cake host's
launch path.
- **Coverage gaps:**
- No benchmark row uses the TOP_K = 4 BF16 vector combine. In the cake
project it is covered only by the CPU ABI/parity tests (export and
pytest); no benchmark or GPU parity run there exercises it.
- The production fused quantized combine has no timing row. Its
byte-level evidence is the cake-side fused-vs-two-kernel comparison (see
Precision). No FlashInfer-side byte comparison against the two-kernel
path has been run.
- **Not in this PR:** for an in-workspace combine, FlashInfer's
`backend="cake"` adapter launches stage (1 CTA) + publish + combine,
which is 3 launches against 2 on the cake host. That extra launch costs
about one launch (1.3-4 us) per in-workspace combine, ≤ 1.7 % of an mpi8
row. Removing it changes the adapter rather than the generated kernels,
so it is left as a possible follow-up for the maintainers to decide.
- **Upstream host parity:** #5336 (recv-view cache) and #6376 (fixed
combine region) are shared Python changes that reach `backend="cake"`
without any kernel or launcher change. #5532 adds only a
constructor-time `@deprecated`. None of them leaves a kernel or launcher
gap on the cake path.
- **Upstream main:** when this branch was prepared, main had 7 commits
past the pin, and none of them touched the files in this PR. Main has
moved since then.
- **Not every row is at the floor:** B200 has 4/40 rows at or above 90 %
of the floor and GB300 has 8/40. The rows below 90 % are listed with
their gap statements above.

CI state of this PR:

CI state when this description was last updated (19:50Z UTC): 19 checks,
skipped 2, success 17; pre-commit success; no failing check.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [042162c](https://github.com/flashinfer-ai/flashinfer/commit/042162c8ed2237d4a82404f82032652e25b5c735)

- **作者**: eigen
- **时间**: 2026-10-15T21:28:12Z
- **提交信息**: perf(cake_deepgemm): SM120 paged MQA-logits indexer: batch-aware Q-atom programs, DeepGEMM block-table cache, num_heads metadata kwarg (#6530)

## Summary

> **Speedup over DeepGEMM (geomean of the 216 shapes per device, kernel
time, measured with `max_context_hint`): RTX 5090 1.23×, RTX PRO 6000
1.20×.** Ratios below are Cake / DeepGEMM time (0.8151 and 0.8354); r2
without the hint measured 1.21× / 1.19×. Best shapes reach 2.5× (32-head
`next_n` 5 at batch 256); 199 of 216 shapes are faster on the RTX 5090
and 203 of 216 on the RTX PRO 6000; the slower shapes (12 / 10) are
DeepGEMM-identical schedules within +2.2 %.

This PR updates the SM120a paged FP8 MQA logits package, the
DeepSeek-V3.2 / V4.1-Flash decode lightning indexer. It replaces all of
the generated programs from #6180, #6199 and #6219.

A larger Q atom scores more tokens in each pass over the KV cache. Small
batches still need DeepGEMM's 2-token atoms to balance work across SMs,
unless their contexts are long. So each call now picks its atom.

- **Batch-aware Q-atom variants.** Each call picks a Q-atom program from
the head count, `next_n` and batch class.
- **`num_heads` keyword.** `get_paged_mqa_logits_metadata` gains a
keyword-only `num_heads`. It is needed only for `next_n` 5/6 at batch >
8, and at batch 2..8 when `max_context_hint` is at least 16384.
- **`bt_batch`.** The TMA warp loads 32 block-table entries at once and
shuffles out each tile's page index, as DeepGEMM does.
- **`max_context_hint` keyword (round R3).** This is an optional upper
bound on the batch's context lengths. From 16384 KV tokens up, batches
2..8 use the large-batch Q-atom rule. If you omit it, the selection
stays as before.

Logits stay bitwise-identical to DeepGEMM, with and without the hint.
With the hint, the geomean kernel time versus DeepGEMM is 0.8151 on the
RTX 5090 and 0.8354 on the RTX PRO 6000. The r2 matrices, which had no
hint, gave 0.8277 and 0.8413.

## Round R3: optional `max_context_hint`

**Why.** In r2 the atom choice depended on the batch only, because the
context lengths are on the device when the program is picked. As a
result, the batch-8 rows at 16K and 64K KV tokens fell back to
DeepGEMM's 2-token atoms. For `next_n` 3/4, those rows lost 10 to 28 %
against the round before r2. For example, `h32p128n3` at batch 8 × 64K
on the RTX 5090 went from 0.7185 to 0.9903 of DeepGEMM's time.

**What it does.** `max_context_hint` is an upper bound, in KV tokens, on
the batch's context lengths. The caller knows it on the host, for
example as the maximum of the framework's `seq_lens_cpu`. It only
affects the Q-atom choice at batch 2..8. When the hint is at least
16384, those batches use the large-batch selection:

- `next_n` 3 and 4: native `a3` / `a4` atoms, for 32 and 64 heads.
- `next_n` 5 and 6 with 32 heads: native `a5` / `a6` atoms.
- `next_n` 5 and 6 with 64 heads: the reference 2-token atoms stay,
because the native atom exceeds the 256-row TMA Q box.

The hint does not change `next_n` 1/2, batch 1 or batches above 8.
Omitting it (`None`, the default) keeps the r2 batch-only selection. The
hint adds no program or route. Every variant it selects already ships
for larger batches.

**API.** `max_context_hint=None` is a keyword-only argument on
`get_paged_mqa_logits_metadata`, `fp8_paged_mqa_logits` and
`prepare_sm120_paged_mqa_logits`, with the same meaning on each. The
plan classes and the host helpers `atom_variant`, `next_n_atoms`,
`route_name` and `route_available` also accept it. A hint must be at
least 1. `prepare_sm120_paged_mqa_logits` stores it as
`plan.max_context_hint`. The positional `max_context_len`, which is the
logits row width, is never used for the selection.

**Catalog.** `policy.atom_rule` gains `long_context_min_kv` (16384) and
`selection_long`. `selection_long` differs from `selection` only in the
batch 2..8 class.

**Tests.** The new `test_sm120_paged_mqa_logits_long_context_hint` runs
5 cases at an average context of 16384 with a hint of 65536. Host-side
checks cover:

- `selection_long` against `selection` for each batch class
- the hint boundary (16383, 16384, `None`)
- the head-count rule
- `route_available` with the hint

**A/B.** The A/B covers 24 rows: {`h32p128`, `h32p64`, `h64p64`} ×
`next_n` 3..6 × batch 8 × {16K, 64K}. Both arms (hint and no hint) were
paired against DeepGEMM in the same step, using CUPTI with a cold L2.
Logits were bitwise-identical in both arms.

| device | paired rows | hint faster by > 0.5 % | hint slower by > 0.5 %
| within 0.5 % | geomean hint / no hint | largest gain (Cake/DG, no hint
to hint) |
|---|---|---:|---:|---:|---:|---|
| RTX PRO 6000 | 23/24 | 17 | 0 | 6 | 0.9384 | `h32p64n5`, 8 × 64K:
0.9710 to 0.7458 |
| RTX 5090 | 18/24 | 15 | 1 | 2 | 0.9107 | `h32p128n5`, 8 × 64K: 0.9766
to 0.6416 |

- On the PRO 6000, one row is missing because the no-hint arm hit a
clock-gate error.
- On the RTX 5090, six 64K rows fell below the 2500 MHz clock gate in
both arms.
- The one row where the hint was slower is `h32p64n6` at 8 × 16K on the
RTX 5090, which went from 0.9045 to 0.9111.

The threshold stays at 16384. At 16K, no row got worse on the PRO 6000,
and only that one row got worse on the RTX 5090, by 0.7 %.

## What is delivered

| group | location |
|---|---|
| public API | `flashinfer/sm120_paged_mqa_logits.py` |
| runtime, catalog, README |
`flashinfer/experimental/deepgemm_sm120_paged_mqa_logits/` |
| generated CUDA and bindings |
`csrc/experimental/deepgemm_sm120_paged_mqa_logits/generated/` |
| test | `tests/experimental/test_sm120_paged_mqa_logits.py` |
| benchmark | `benchmarks/bench_sm120_paged_mqa_logits.py` |

There are 31 kernels: one shared scheduler and 30 logits programs across
18 geometries. Each logits route has one prepared-sequence binding,
which submits the scheduler and the logits kernel as one FFI call. R3
adds no kernel program or route.

At the r2 head `d9d8e1ff`, the delivery had 81 files (3,460,912 bytes).
Compared with the base, 10 tracked files were modified and 60 files were
new. Every program has a new content-hash name, so 36 generated files
from the earlier deliveries were orphaned. This PR removes them. The R3
commit changes 5 files (+619 / -78): the public API module, the runtime,
the catalog, the package README and the test. No generated CUDA file
changes.

The package README documents the atom table, the metadata API, the
long-context hint and the per-program DeepGEMM comparison. Its measured
table is the hinted table shown below.

## API change

```python
get_paged_mqa_logits_metadata(
    context_lens, page_kv, num_sms, indices=None, *, num_heads=None, max_context_hint=None, out=None
)
fp8_paged_mqa_logits(
    q, kv_cache, weights, context_lens, block_table, schedule_meta, max_context_len,
    clean_logits=False, indices=None, *, page_kv=None, max_context_hint=None
)
```

- The schedule's item count is the Q-atom count for `(num_heads, next_n,
batch)`. At batch 2..8 it also depends on the hint.
- `batch` and `next_n` come from `context_lens.shape`.
- `num_heads` is needed only for `next_n` 5 and 6 at batch > 8, and,
with a hint of at least 16384, also at batch 2..8. These are the only
cases where the two shipped head counts select different schedules.
- If `num_heads` is missing at batch > 8, a `ValueError` names it.
- Everywhere else, the DeepGEMM call without `num_heads` is exact.
- `indices` must still be `None`, because DeepGEMM's variable-length
branch is not ported.

The metadata call and the logits call of one decode step should receive
the same hint, just as they receive the same `num_heads`. The schedule
buffer is DeepGEMM-identical and carries no atom count, so a mismatch
cannot be detected from the buffer. For that reason, the logits entries
rebuild the schedule under their own `(context_lens, num_heads,
max_context_hint)` before the program reads it.

The runtime helpers `next_n_atoms`, `atom_variant`, `route_name` and
`route_available` follow the same rule. The catalog key
`policy.next_n_atoms` is removed without an alias, and
`policy.atom_rule` replaces it.

## Correctness

- Logits are bitwise-identical to DeepGEMM `yyihuang/DeepGEMM@79a4ef3b`
on every validated row of both devices, with and without the hint.
- **Without the hint (r2 matrices):** 216 acceptance rows per device (18
programs × 12 (batch, context) points). Schedule metadata matches both
DeepGEMM's metadata and the Python mirror on every row. No NaN or Inf
appeared.
- **With the hint (R3 matrices):** the hint is set to each row's maximum
context length. The same 216 rows per device give 432 rows in total.
Schedule metadata matches the Python mirror on every row.

The delivered test runs every shipped `(heads, page_kv, next_n, atom)`
program at a small and a large batch. It compares the logits with a
dequantized PyTorch reference and the schedule with an independent
mirror. It also covers the write extent, padded block strides, CUDA
Graph replay and the `num_heads` rule. R3 adds the hint test described
above.

## Performance

Kernel times come from Loom's CUPTI paired-group timer
(`bench_gpu_time_paired_groups`: cold L2, at least 3 independent ABBA
groups per row). DeepGEMM `79a4ef3b` ran on the same device and clocks.
Each program has 12 (batch, average context) rows: (1, 16K), (8, 4K),
(8, 16K), (8, 64K), (32, 16K), (32, 64K), (64, 4K), (64, 16K), (128,
16K), (128, 64K), (256, 4K) and (256, 16K).

Every row below was measured with `max_context_hint` set to that row's
maximum context length. The RTX 5090 matrix ran on a different node from
the r2 matrix. A first RTX 5090 run on another node hit 41/216
clock-gate errors because the GPU throttled below the 2500 MHz gate.
That run was not used, and the re-run had 0 errors.

| program | RTX 5090 Cake/DG | RTX 5090 speedup | RTX 5090 faster / tie
/ slower | RTX PRO 6000 Cake/DG | RTX PRO 6000 speedup | RTX PRO 6000
faster / tie / slower |
|---|---:|---:|---:|---:|---:|---:|
| `h32p128n1` | 0.996 | 1.00× | 10 / 1 / 1 | 0.997 | 1.00× | 10 / 0 / 2
|
| `h32p128n2` | 0.991 | 1.01× | 11 / 1 / 0 | 0.995 | 1.01× | 11 / 1 / 0
|
| `h32p128n3` | 0.703 | 1.42× | 12 / 0 / 0 | 0.769 | 1.30× | 12 / 0 / 0
|
| `h32p128n4` | 0.724 | 1.38× | 11 / 0 / 1 | 0.773 | 1.29× | 12 / 0 / 0
|
| `h32p128n5` | 0.614 | 1.63× | 12 / 0 / 0 | 0.702 | 1.42× | 12 / 0 / 0
|
| `h32p128n6` | 0.675 | 1.48× | 12 / 0 / 0 | 0.699 | 1.43× | 12 / 0 / 0
|
| `h32p64n1` | 0.997 | 1.00× | 9 / 0 / 3 | 0.998 | 1.00× | 11 / 1 / 0 |
| `h32p64n2` | 0.992 | 1.01× | 9 / 1 / 2 | 0.994 | 1.01× | 12 / 0 / 0 |
| `h32p64n3` | 0.711 | 1.41× | 12 / 0 / 0 | 0.770 | 1.30× | 12 / 0 / 0 |
| `h32p64n4` | 0.740 | 1.35× | 11 / 0 / 1 | 0.779 | 1.28× | 12 / 0 / 0 |
| `h32p64n5` | 0.626 | 1.60× | 12 / 0 / 0 | 0.680 | 1.47× | 12 / 0 / 0 |
| `h32p64n6` | 0.664 | 1.51× | 12 / 0 / 0 | 0.691 | 1.45× | 12 / 0 / 0 |
| `h64p64n1` | 0.988 | 1.01× | 12 / 0 / 0 | 0.994 | 1.01× | 11 / 0 / 1 |
| `h64p64n2` | 0.992 | 1.01× | 11 / 0 / 1 | 0.996 | 1.00× | 9 / 0 / 3 |
| `h64p64n3` | 0.739 | 1.35× | 12 / 0 / 0 | 0.757 | 1.32× | 12 / 0 / 0 |
| `h64p64n4` | 0.922 | 1.08× | 9 / 2 / 1 | 0.795 | 1.26× | 11 / 0 / 1 |
| `h64p64n5` | 0.885 | 1.13× | 12 / 0 / 0 | 0.888 | 1.13× | 12 / 0 / 0 |
| `h64p64n6` | 0.948 | 1.05× | 10 / 0 / 2 | 0.920 | 1.09× | 8 / 1 / 3 |
| **all 18 programs** | 0.815 | 1.23× | 199 / 5 / 12 | 0.835 | 1.20× |
203 / 3 / 10 |

Each ratio is a geomean over that program's 12 rows. Below 1 means Cake
is faster. `faster` needs a bootstrap 95 % CI upper bound ≤ 1, and `tie`
means within 0.5 % with a CI that contains 1.

R3 targets the batch-8 rows at 16K and 64K average context. Some of the
rows that moved (Cake/DG):

| device | program | batch × avg context | r2, no hint | R3, with hint |
|---|---|---|---:|---:|
| RTX 5090 | `h32p128n3` | 8 × 64K | 0.9903 | 0.7225 |
| RTX 5090 | `h64p64n3` | 8 × 16K | 0.9664 | 0.8099 |
| RTX PRO 6000 | `h32p64n5` | 8 × 64K | 0.9699 | 0.7456 |
| RTX PRO 6000 | `h64p64n4` | 8 × 64K | 0.9996 | 0.9281 |

Without the hint, these rows run the r2 programs and keep the r2
numbers.

- **32-head rows at 8 × 16K:** most moved from 0.92..0.97 to 0.86..0.91
on the RTX 5090. On the PRO 6000 they moved from 0.95..1.00 to
0.90..0.98.
- **One hinted row got slower than in r2:** `h32p64n4` at 8 × 16K on the
RTX 5090, from 0.9516 to 0.9671.
- **Unchanged:** on the PRO 6000, `h64p64n3` at 8 × 16K stayed at 0.958.
The 64-head `next_n` 5/6 rows are unchanged because the rule keeps their
reference atoms.

Against the r2 matrices, the PRO 6000 has 3 fixed rows and none
regressed. The RTX 5090 has 5 fixed rows and 5 regressed:

- Four of the regressed rows run the same schedule as DeepGEMM and are
within the noise range: `h32p64n2` at 1 × 16K, `h32p128n2` at 8 × 4K,
`h64p64n2` at 64 × 16K and `h64p64n4` at 1 × 16K.
- The fifth is the hinted tie described below.

All 22 slower rows use DeepGEMM-identical schedules:

- 12 on the RTX 5090, slower by +0.05 % to +2.2 %.
- 10 on the RTX PRO 6000, slower by +0.04 % to +2.1 %.

Short kernels are noisy between runs.

On the RTX 5090, one hinted row is a tie: `h64p64n4` at batch 8 × 16K
runs the `a4` program at 1.0000 (95 % CI [0.9989, 1.0011]). In r2,
without the hint, this row ran the reference program at 0.9921.

Before `bt_batch` became the default in r2, the matrices had 38 slower
rows on the RTX 5090 and 35 on the RTX PRO 6000.

## Validation

Everything below ran on an RTX PRO 6000 Blackwell Server Edition (188
SMs) and a GeForce RTX 5090 (170 SMs).

At the R3 head `be3a46a6ad6a23367f29fbab2a06f0ad7356ccbc`:

- `tools/export-generated-programs protocol` and `run` ran on both
devices from the Cake producer `19a428fd`. The protocol lock sha256 is
`c673430a9aecffc1…` (54 shapes, 54 resolved routes, 31 declared
templates).
- `run` completed the full denominator (54/54), and all gates passed
(54/54) on both devices (360 s on the RTX PRO 6000, 356 s on the RTX
5090).
- The 81 delivered files were byte-identical on both devices (identical
delivered manifests).
- `audit-export-slop` ran on the delivered paths.
- `pytest tests/experimental/test_sm120_paged_mqa_logits.py`: 42 passed
on both devices (37 in r2; the long-context hint test adds 5 cases).
- `python benchmarks/bench_sm120_paged_mqa_logits.py` ran on both
devices.
- `pre-commit run --files <delivered files>`: every hook passed and left
the delivered bytes unchanged on both devices.
- The R3 commit `be3a46a6` changes 5 files (+619 / -78):
`flashinfer/sm120_paged_mqa_logits.py`, the runtime
`sm120_paged_mqa.py`, the catalog `sm120_paged_mqa_catalog.json`, the
package README and the test. No generated CUDA file changes, so the 31
kernels are those of the r2 head.

At the r2 head `d9d8e1ff`:

- `tools/export-generated-programs protocol` and `run` ran on both
devices. The protocol lock sha256 is `fc9464f7…` (42 resolved routes).
- `run` completed the full denominator (42/42), and all gates passed
(42/42).
- The 81 delivered files were byte-identical on both devices.
- `audit-export-slop` found 0 identical-body, 0 arch-copy and 0
unreferenced lines.
- The audit's 7232 constant-clone lines are the per-shape SMEM
constants, as in earlier deliveries. The 31 kernels have 31 distinct
bodies.
- `pytest tests/experimental/test_sm120_paged_mqa_logits.py`: 37 passed
on both devices.
- `python benchmarks/bench_sm120_paged_mqa_logits.py` ran on both
devices.
- `pre-commit run --files <delivered files>`: every hook passed and left
the delivered bytes unchanged.
- The generated CUDA passed the repository's clang-format hook
unchanged. There is no new third-party dependency.

## Notes for reviewers

- Route names follow `sm120:fp8:h<H>:p<P>:n<N>:a<A>`, where `a<A>` is
the Q-atom size in tokens.
- For example, `sm120:fp8:h32:p128:n5:a5` is the native atom, and
`...:n5:a2` is DeepGEMM's 2-token split of the same geometry.
- Every route shares the scheduler, which also has its own route,
`sm120:metadata`.
- The atom rule is catalog data in `policy.atom_rule`, with
`batch_class_min = [1, 2, 9, 128]`, `long_context_min_kv = 16384` and a
`selection_long` table for the hinted batch 2..8 class. The runtime
evaluates it without the producer.

| `next_n` | heads | B = 1 | B = 2..8 | B = 2..8, hint ≥ 16384 | B =
9..127 | B ≥ 128 |
|---|---|---|---|---|---|---|
| 1 | 32, 64 | `a1` | `a1` | `a1` | `a1` | `a1` |
| 2 | 32, 64 | `a2` | `a2` | `a2` | `a2` | `a2` |
| 3 | 32, 64 | `a3` | `a2` | `a3` | `a3` | `a3` |
| 4 | 32, 64 | `a2` | `a2` | `a4` | `a4` | `a4` |
| 5, 6 | 32 | `a2` | `a2` | `a5` / `a6` | `a5` / `a6` | `a5` / `a6` |
| 5, 6 | 64 | `a2` | `a2` | `a2` | `a2` | `a3` |

- A 64-head 5- or 6-token atom does not fit the 256-row TMA Q box. So
those geometries use two 3-token atoms from batch 128 up, and keep
2-token atoms at batch 2..8 even with the hint.
- Store semantics follow DeepGEMM's `clean_logits=False`. Cells beyond a
token's context length are unspecified, so consumers must mask by
context length.
- `bt_batch` targets a gap that ncu showed on the RTX PRO 6000. On `h64
p64 n1` at batch 128 × 16K, Cake issued 43.5k global loads and DeepGEMM
9.3k. SM active cycles were equal (433.8k vs 432.0k).
- Two other levers were tested and not adopted: removing the release
fence, and DeepGEMM's `try_wait` suspend hint. Both were neutral.
- This PR does not depend on #6233.

## Producer provenance

- Cake R3 commits, stacked on the r2 delivery
`33492f24eb0501830b91833e22d1b697b24c9f2a`:
  - `fa6a05ea` (feature)
  - `02a3e0a35a740232e8a9d7e0df07de2536230356` (review fixes)
- `19a428fd14061b16f8a69017cae7b1a44678889f` (README measured table; the
producer revision of this delivery)
- `fd4b20c996c9bdc53795c6982a0d949b05d63570` (Cake-side NOTES only; no
delivered file changes)
- The R3 producer generates the same default programs as the r2 delivery
(CPU identity check, 18/18). The r2 programs match the measured tree
`32a558c2d9c77c214a03e48618bbb9cfd5a202ba` (18/18).
- DeepGEMM baseline: `yyihuang/DeepGEMM@79a4ef3b`.
- Base: FlashInfer main `fd14b3056d0c1aa72c80fc9c35c8493f38c5a9a5`
(2026-10-14), which includes #6180, #6199 and #6219.
- PR head: `be3a46a6ad6a23367f29fbab2a06f0ad7356ccbc`, one commit on the
r2 head `d9d8e1ffee1f1525572b438518aaa3ae44ddeaef`.
- Producer gates on `02a3e0a3`, on both devices:
  - e2e GPU tests: 15 passed
  - e2e CPU tests: 45 passed
- compute-sanitizer synccheck and memcheck: 0 errors across 8 benchmarks
  - Cake bench-regression: 8/8
  - exporter: ruff clean, import smoke test OK

  The r2 delivery head `33492f24` passed the same GPU gates.
- The RTX 5090 bench-regression uses per-device floors for the h64
`next_n` 5/6 rows. On the r2 measured tree `32a558c2`, those rows
reached 316 / 376 TFLOPS on the RTX 5090, below the PRO 6000 floors of
356 / 423. So the r2 delivery head added RTX 5090 floors of 284 / 338
TFLOPS.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [af8c006](https://github.com/flashinfer-ai/flashinfer/commit/af8c006ba389efb9202230f9f3306af6424568be)

- **作者**: eigen
- **时间**: 2026-10-15T21:11:52Z
- **提交信息**: perf(cake_mok): imbalance-aware comm split, earlier backward replay dispatch and an atomics-free load count (SM100a, SM103a, SM107a) (#6439)

## Summary

Part of the generated-kernel progress tracker #4254 (training-kernel
tracker #4642). Follow-up to #6053 (the `cake_mok_bf16`
MoE-training package on main): four performance changes (a fifth commit
is formatting and doc wording only); no existing signature changes — the
public API only grows by optional parameters with defaults
(`create_mok_bf16_workspace(precision, imbalance_comm_sms,
imbalance_threshold)`; `MoKConfig.imbalance_comm_sms` /
`imbalance_threshold`), the helpers `resolve_imbalance_comm_sms`,
`count_routed_load` and `select_comm_split`, the constants
`IMBALANCE_COMM_SMS`, `IMBALANCE_THRESHOLD` and `MOK_PRECISIONS`, and
the `CAKE_MOK_COMM_SPLIT_LOG` switch; the new default
`imbalance_comm_sms="auto"` enables the 24 / 28 split on B200 BF16 only
above the threshold. Supersedes #6240 (closed): its two performance
changes (the imbalance-aware communication split and the re-exported
backward kernels) are re-based here onto the #6053 package layout; the
feature content of #6240 (context-only recompute, GLM-5.3-Flash layouts,
clamped SwiGLU, native MXFP8 routed experts) is already on main through
#6053 and is not part of this PR.

1. `7e4f02475` — **imbalance-aware communication split** (adapter only,
kernels unchanged). `MoKConfig.imbalance_comm_sms:
(fwd, bwd) | None` and `imbalance_threshold` (default raised to 4 in
(4)). `build_schedule` counts the gathered expert IDs per owning rank on
device and
copies the counts into pinned host memory behind a CUDA event (no host
synchronization; identical on every rank; skipped during
graph capture). While the hottest rank's load is at least
`imbalance_threshold` × the mean load the launches use the imbalance
split; balanced steps are unchanged.
`create_mok_bf16_workspace(precision="bf16", imbalance_comm_sms="auto",
imbalance_threshold=4.0)`: `"auto"` resolves the measured row of the
device generation (B200 BF16: 24 / 28; none elsewhere, so
the fixed split stays in force), `None` keeps the fixed split, a pair
sets it. `CAKE_MOK_COMM_SPLIT_LOG=1` prints split changes.
   Three host-only tests in `tests/experimental/test_mok_bf16.py`.
2. `edd4f7ff7` — **re-exported backward kernel sources** (12 device + 12
binding files; `sources.json` updated with their 24 sha256 entries;
every other file byte-identical): the backward
communication program re-dispatches the replayed `x` of the next
macrobatch before the score-scaled `dy` (BF16, MXFP8 and their
clamped / FP32-wgrad variants, sm_100a/sm_103a and sm_107a). The replay
GEMMs wait only on `x`, so the compute CTAs leave the
replay gate earlier. Same quantization, scale layout, counters and
thresholds; no numerical change by construction (only the
order in which the communication CTAs process the two chunk kinds
differs). Rendered by the current generator, so the files also
carry its codegen-level changes (shared-memory offsets through
`SMEM_*_OFF` macros, `LAUNCH_MIN_BLOCKS` in `__launch_bounds__`, TMA box
checks
against a hoisted `box_dim[]` array) and a CUDA ≥ 13.1 guard with an
exact bit-widen + `cvt.rn.satfinite.e4m3x2.f32` fallback around
`cvt.rn.satfinite.e4m3x2.bf16x2`, so the MXFP8 backward sources also
compile under CUDA 13.0.
3. `1fab8e62f` — **the load observation of (1) without atomics**. The
first version counted the gathered ids with `scatter_add_` into
`ep_size + 1` bins (one global atomic per id on a handful of addresses;
padding ids all land in the extra bin, and on the capacity-2 row most
gathered ids are padding), which cost 0.3–0.5 % of a step on the
balanced B200 EP8 BF16 default rows and 2.4 % on the B200 EP8 capacity-2
row
(main + commit 1 against main, two rounds on one node).
`count_routed_load()` compares the owning rank
of every id against the rank range and reduces (floor-divide, `arange`,
broadcast compare, sum): a few small elementwise / reduction kernels, no
atomics, no host synchronization (`torch.bincount` sizes its
output from `max()` on the host, so it was not used). Same counts, same
decision, pinned host buffers now int64. Host-only test.

4. `9368b0664` — **switch to the imbalance split only from 4× the mean
load** (`IMBALANCE_THRESHOLD` 1.5 → 4.0; docstrings, README
and host-only tests follow; the parameter keeps its meaning). On this
package's backward programs the 24 / 28 split pays only under
heavy imbalance (B200 EP8 complete training steps, two rounds each on
its own node, step time against the fixed 20 / 24): hottest rank at 5.6×
/ 7.4× the mean routed
load −1.0 / −1.7 % and −1.2 / −1.3 %; at 3.0× (one rank's experts at
twice the routing probability) +0.4 / +0.7 % (full step),
+0.8 / +0.5 % (checkpoint step) and −0.1 … +1.6 % with ragged source
rows (8 cells, 7 slower): no gain: every cell lies within or just above
the
0.1 – 1.0 % spread measured between arms that executed the same 20 / 24
split and the same kernels. The threshold sits between the measured 3.0×
and 5.6×;
the crossover in between is not measured, and with 4 ranks the ratio
reaches 4 only when one rank carries every routed row. `28df319b5` on
top is formatting and doc
wording only (ruff-format of the test file; "no gain at 3×" instead of
"faster"); the runtime code of the PR head equals `9368b0664`.

### Measurements (complete training step, cake vs the #6053 package of
main `e44067b1f` and vs the references MoK #17 and DeepEP, two paired
A/B rounds per row)

Every row is the complete training step (forward + backward, or forward
+ recompute + backward for `ckpt`), CUDA-event timed, slowest rank per
iteration, median of three counterbalanced groups, two A/B rounds (main
then PR per round; for the B200 variant / default rows each round ran on
a
separately allocated node, the B200 EP8 BF16 skew8 row and the GB300
rows ran both rounds back-to-back on one node); `main` = the #6053
package of `e44067b1f` in the same process protocol; MoK #17 = the
reference implementation (mixture-of-kittens PR 17) in the same process;
DeepEP = DeepEP HybridEP dispatch / combine with torch grouped GEMMs on
the BF16 rows (no DeepEP arm on the MXFP8 rows, shown as n/a; omitted on
EP8 BF16 skew 8, where its backward runs out of memory). The B200 BF16
rows
(the only rows whose code path commits 3 and 4 change: the observation
and the threshold act only where `imbalance_comm_sms` resolves, i.e.
B200 BF16) were re-measured at `9368b0664` (commit 4; the runtime code
of the PR head `28df319b5`); the MXFP8 rows and the GB300 rows were
measured at `edd4f7ff7` (commits 1 + 2) and are unchanged by commits 3
and 4 (the observation is skipped there).

**B200 EP8 BF16 variants** (measured at `9368b0664`, the runtime code of
the PR head `28df319b5`; two rounds on two leases, mean over rounds,
per-round PR-vs-main in parentheses)

| row | main ms | PR ms | PR vs main % | PR vs MoK #17 % | PR vs DeepEP
% | peak mem PR/main |
|---|---|---|---|---|---|---|
| `glm52_ep8_bf16_ckpt_imbal` | 105.09 | 100.69 | -4.18 (-4.57 / -3.80)
| -12.80 | -46.84 | 1.000 |
| `glm52_ep8_bf16_ckpt_ragged` | 25.16 | 25.26 | +0.41 (+0.80 / +0.02) |
-9.24 | -46.44 | 1.000 |
| `glm52_ep8_bf16_ckpt_raggedimbal` | 60.32 | 60.84 | +0.87 (+1.21 /
+0.53) | -8.98 | -47.01 | 1.000 |
| `glm52_ep8_bf16_full_imbal` | 92.24 | 89.10 | -3.41 (-3.86 / -2.97) |
-12.41 | -36.68 | 1.000 |
| `glm52_ep8_bf16_full_ragged` | 20.91 | 21.00 | +0.46 (+0.73 / +0.20) |
-8.55 | -42.38 | 1.000 |
| `glm52_ep8_bf16_full_raggedimbal` | 49.64 | 49.79 | +0.30 (-0.36 /
+0.95) | -9.34 | -41.44 | 1.000 |
| `glm52_ep8_bf16_full_skew2` | 93.21 | 89.27 | -4.22 (-4.20 / -4.24) |
-12.51 | -36.66 | 1.000 |
| `glm52_ep8_bf16_full_skew4` | 192.86 | 175.94 | -8.76 (-8.38 / -9.14)
| -15.89 | -33.83 | 1.000 |

**B200 EP8 BF16 skew8 (no DeepEP arm: the reference OOMs in its backward
at EP8 skew 8)** (measured at `9368b0664`, the runtime code of the PR
head `28df319b5`; two rounds back-to-back on one lease, mean over
rounds, per-round PR-vs-main in parentheses)

| row | main ms | PR ms | PR vs main % | PR vs MoK #17 % | PR vs DeepEP
% | peak mem PR/main |
|---|---|---|---|---|---|---|
| `glm52_ep8_bf16_full_skew8` | 255.86 | 231.91 | -9.36 (-9.90 / -8.81)
| -15.63 | n/a | 1.000 |

**B200 EP8 BF16 defaults** (measured at `9368b0664`, the runtime code of
the PR head `28df319b5`; two rounds on two leases, mean over rounds,
per-round PR-vs-main in parentheses)

| row | main ms | PR ms | PR vs main % | PR vs MoK #17 % | PR vs DeepEP
% | peak mem PR/main |
|---|---|---|---|---|---|---|
| `glm52_ep8_bf16_ckpt` | 37.54 | 37.58 | +0.11 (+0.12 / +0.10) | -9.64
| -46.54 | 1.000 |
| `glm52_ep8_bf16_ckpt_mb393216` | 37.56 | 37.53 | -0.09 (+0.40 / -0.59)
| -9.83 | -46.31 | 1.000 |
| `glm52_ep8_bf16_full_cap2` | 31.13 | 31.19 | +0.20 (-0.11 / +0.51) |
-9.46 | -42.19 | 1.000 |
| `glm52_ep8_bf16_full` | 31.00 | 31.13 | +0.41 (+0.53 / +0.30) | -9.07
| -41.76 | 1.000 |
| `glm52_ep8_bf16_full_mb393216` | 30.91 | 31.02 | +0.36 (+0.60 / +0.12)
| -9.41 | -41.93 | 1.000 |

**B200 EP4 BF16 variants** (measured at `9368b0664`, the runtime code of
the PR head `28df319b5`; two rounds on two leases, mean over rounds,
per-round PR-vs-main in parentheses)

| row | main ms | PR ms | PR vs main % | PR vs MoK #17 % | PR vs DeepEP
% | peak mem PR/main |
|---|---|---|---|---|---|---|
| `glm52_ep4_bf16_ckpt_imbal` | 82.33 | 80.60 | -2.10 (-2.28 / -1.91) |
-14.50 | -43.99 | 1.000 |
| `glm52_ep4_bf16_ckpt_ragged` | 26.02 | 26.07 | +0.18 (-0.19 / +0.56) |
-11.79 | -43.28 | 1.000 |
| `glm52_ep4_bf16_ckpt_raggedimbal` | 48.87 | 48.79 | -0.18 (-0.31 /
-0.06) | -12.33 | -45.39 | 1.000 |
| `glm52_ep4_bf16_full_imbal` | 70.99 | 69.60 | -1.97 (-2.73 / -1.20) |
-13.62 | -34.85 | 1.000 |
| `glm52_ep4_bf16_full_ragged` | 21.44 | 21.50 | +0.32 (+0.33 / +0.31) |
-12.01 | -39.20 | 1.000 |
| `glm52_ep4_bf16_full_raggedimbal` | 40.27 | 40.28 | +0.03 (+0.15 /
-0.08) | -12.32 | -39.80 | 1.000 |
| `glm52_ep4_bf16_full_skew2` | 71.21 | 69.44 | -2.48 (-2.09 / -2.87) |
-13.87 | -34.87 | 1.000 |
| `glm52_ep4_bf16_full_skew4` | 110.78 | 104.96 | -5.25 (-5.05 / -5.45)
| -15.19 | -32.89 | 1.000 |
| `glm52_ep4_bf16_full_skew8` | 128.59 | 120.82 | -6.05 (-6.40 / -5.69)
| -14.64 | -30.59 | 1.000 |

**B200 EP4 BF16 defaults** (measured at `9368b0664`, the runtime code of
the PR head `28df319b5`; two rounds on two leases, mean over rounds,
per-round PR-vs-main in parentheses)

| row | main ms | PR ms | PR vs main % | PR vs MoK #17 % | PR vs DeepEP
% | peak mem PR/main |
|---|---|---|---|---|---|---|
| `glm52_ep4_bf16_ckpt` | 38.63 | 38.70 | +0.19 (+0.77 / -0.39) | -11.34
| -43.15 | 1.000 |
| `glm52_ep4_bf16_ckpt_mb393216` | 38.73 | 38.79 | +0.14 (+0.19 / +0.09)
| -11.10 | -43.25 | 1.000 |
| `glm52_ep4_bf16_full_cap2` | 31.96 | 31.98 | +0.07 (-0.06 / +0.19) |
-11.34 | -38.99 | 1.000 |
| `glm52_ep4_bf16_full` | 31.78 | 31.91 | +0.39 (+0.28 / +0.51) | -11.06
| -38.28 | 1.000 |
| `glm52_ep4_bf16_full_mb393216` | 31.93 | 31.93 | +0.01 (-0.41 / +0.42)
| -10.97 | -38.26 | 1.000 |

**B200 EP8 MXFP8 variants** (measured at `edd4f7ff7`, commits 1 + 2;
commits 3 and 4 do not touch this path; two rounds on two leases, mean
over rounds, per-round PR-vs-main in parentheses)

| row | main ms | PR ms | PR vs main % | PR vs MoK #17 % | PR vs DeepEP
% | peak mem PR/main |
|---|---|---|---|---|---|---|
| `glm52_ep8_mxfp8_ckpt_imbal` | 78.67 | 74.36 | -5.48 (-5.77 / -5.19) |
-9.74 | n/a | 1.000 |
| `glm52_ep8_mxfp8_ckpt_ragged` | 20.09 | 20.08 | -0.02 (+0.03 / -0.07)
| -3.21 | n/a | 1.000 |
| `glm52_ep8_mxfp8_ckpt_raggedimbal` | 45.12 | 45.10 | -0.04 (+0.26 /
-0.35) | -5.70 | n/a | 1.000 |
| `glm52_ep8_mxfp8_full_cap2` | 23.36 | 23.31 | -0.22 (-0.06 / -0.37) |
-6.13 | n/a | 1.000 |
| `glm52_ep8_mxfp8_full_imbal` | 69.60 | 65.09 | -6.48 (-6.31 / -6.65) |
-10.96 | n/a | 1.000 |
| `glm52_ep8_mxfp8_full_ragged` | 16.47 | 16.47 | +0.00 (+0.32 / -0.32)
| -2.83 | n/a | 1.000 |
| `glm52_ep8_mxfp8_full_raggedimbal` | 36.27 | 36.32 | +0.14 (+0.04 /
+0.23) | -7.84 | n/a | 1.000 |
| `glm52_ep8_mxfp8_full_skew2` | 70.10 | 65.37 | -6.75 (-6.89 / -6.61) |
-10.14 | n/a | 1.000 |
| `glm52_ep8_mxfp8_full_skew4` | 146.67 | 129.75 | -11.53 (-12.06 /
-11.01) | -14.99 | n/a | 1.000 |
| `glm52_ep8_mxfp8_full_skew8` | 197.94 | 173.66 | -12.27 (-12.79 /
-11.75) | -15.54 | n/a | 1.000 |

**B200 EP8 MXFP8 defaults** (measured at `edd4f7ff7`, commits 1 + 2;
commits 3 and 4 do not touch this path; two rounds on two leases, mean
over rounds, per-round PR-vs-main in parentheses)

| row | main ms | PR ms | PR vs main % | PR vs MoK #17 % | PR vs DeepEP
% | peak mem PR/main |
|---|---|---|---|---|---|---|
| `glm52_ep8_mxfp8_ckpt` | 28.68 | 28.75 | +0.22 (+0.37 / +0.07) | -5.41
| n/a | 1.000 |
| `glm52_ep8_mxfp8_ckpt_mb393216` | 28.73 | 28.72 | -0.05 (-0.20 /
+0.10) | -5.39 | n/a | 1.000 |
| `glm52_ep8_mxfp8_full` | 23.34 | 23.34 | -0.00 (+0.11 / -0.11) | -5.82
| n/a | 1.000 |
| `glm52_ep8_mxfp8_full_mb393216` | 23.35 | 23.29 | -0.25 (-0.19 /
-0.30) | -6.03 | n/a | 1.000 |

**B200 EP4 MXFP8 variants** (measured at `edd4f7ff7`, commits 1 + 2;
commits 3 and 4 do not touch this path; two rounds on two leases, mean
over rounds, per-round PR-vs-main in parentheses)

| row | main ms | PR ms | PR vs main % | PR vs MoK #17 % | PR vs DeepEP
% | peak mem PR/main |
|---|---|---|---|---|---|---|
| `glm52_ep4_mxfp8_ckpt_imbal` | 64.01 | 61.85 | -3.37 (-3.26 / -3.48) |
-9.20 | n/a | 1.000 |
| `glm52_ep4_mxfp8_ckpt_ragged` | 21.30 | 21.32 | +0.06 (-0.01 / +0.14)
| -4.73 | n/a | 1.000 |
| `glm52_ep4_mxfp8_ckpt_raggedimbal` | 37.74 | 37.77 | +0.08 (+0.38 /
-0.22) | -6.90 | n/a | 1.000 |
| `glm52_ep4_mxfp8_full_cap2` | 24.45 | 24.49 | +0.18 (-0.19 / +0.56) |
-6.46 | n/a | 1.000 |
| `glm52_ep4_mxfp8_full_imbal` | 54.51 | 52.57 | -3.56 (-3.45 / -3.66) |
-10.70 | n/a | 1.000 |
| `glm52_ep4_mxfp8_full_ragged` | 17.54 | 17.51 | -0.17 (-0.20 / -0.13)
| -4.97 | n/a | 1.000 |
| `glm52_ep4_mxfp8_full_raggedimbal` | 30.56 | 30.55 | -0.03 (+0.13 /
-0.20) | -8.38 | n/a | 1.000 |
| `glm52_ep4_mxfp8_full_skew2` | 54.51 | 52.40 | -3.87 (-3.82 / -3.91) |
-11.49 | n/a | 1.000 |
| `glm52_ep4_mxfp8_full_skew4` | 86.33 | 78.78 | -8.74 (-8.75 / -8.73) |
-14.15 | n/a | 1.000 |
| `glm52_ep4_mxfp8_full_skew8` | 99.65 | 89.94 | -9.74 (-10.32 / -9.16)
| -14.55 | n/a | 1.000 |

**B200 EP4 MXFP8 defaults** (measured at `edd4f7ff7`, commits 1 + 2;
commits 3 and 4 do not touch this path; two rounds on two leases, mean
over rounds, per-round PR-vs-main in parentheses)

| row | main ms | PR ms | PR vs main % | PR vs MoK #17 % | PR vs DeepEP
% | peak mem PR/main |
|---|---|---|---|---|---|---|
| `glm52_ep4_mxfp8_ckpt` | 29.54 | 29.57 | +0.09 (-0.20 / +0.38) | -6.03
| n/a | 1.000 |
| `glm52_ep4_mxfp8_ckpt_mb393216` | 29.52 | 29.52 | +0.01 (+0.28 /
-0.26) | -6.06 | n/a | 1.000 |
| `glm52_ep4_mxfp8_full` | 24.06 | 24.05 | -0.07 (-0.27 / +0.14) | -6.54
| n/a | 1.000 |
| `glm52_ep4_mxfp8_full_mb393216` | 24.03 | 24.07 | +0.13 (+0.19 /
+0.08) | -6.36 | n/a | 1.000 |

**GB300 EP4, BF16 and MXFP8** (measured at `edd4f7ff7`, commits 1 + 2;
the load observation is off on GB300 because `imbalance_comm_sms="auto"`
resolves to `None` there; two rounds back-to-back on one lease, mean
over rounds, per-round PR-vs-main in parentheses)

| row | main ms | PR ms | PR vs main % | PR vs MoK #17 % | PR vs DeepEP
% | peak mem PR/main |
|---|---|---|---|---|---|---|
| `glm52_ep4_bf16_ckpt` | 30.23 | 30.22 | -0.04 (+0.08 / -0.15) | -11.20
| -48.61 | 1.000 |
| `glm52_ep4_bf16_ckpt_imbal` | 66.24 | 65.10 | -1.72 (-1.56 / -1.89) |
-13.02 | -47.21 | 1.000 |
| `glm52_ep4_bf16_ckpt_mb393216` | 30.15 | 30.22 | +0.22 (+0.59 / -0.15)
| -11.42 | -48.63 | 1.000 |
| `glm52_ep4_bf16_ckpt_ragged` | 21.04 | 21.02 | -0.12 (-0.25 / +0.01) |
-10.83 | -48.50 | 1.000 |
| `glm52_ep4_bf16_ckpt_raggedimbal` | 39.59 | 39.57 | -0.06 (-0.33 /
+0.22) | -11.22 | -49.18 | 1.000 |
| `glm52_ep4_bf16_full_cap2` | 25.02 | 24.98 | -0.18 (-0.11 / -0.25) |
-11.32 | -44.55 | 1.000 |
| `glm52_ep4_bf16_full` | 24.94 | 24.91 | -0.14 (-0.16 / -0.12) | -11.08
| -44.02 | 1.000 |
| `glm52_ep4_bf16_full_imbal` | 56.80 | 55.99 | -1.42 (-1.74 / -1.10) |
-13.30 | -38.86 | 1.000 |
| `glm52_ep4_bf16_full_mb393216` | 24.94 | 24.95 | +0.04 (+0.19 / -0.11)
| -10.77 | -43.94 | 1.000 |
| `glm52_ep4_bf16_full_ragged` | 17.42 | 17.43 | +0.06 (+0.10 / +0.01) |
-11.02 | -44.48 | 1.000 |
| `glm52_ep4_bf16_full_raggedimbal` | 32.57 | 32.61 | +0.12 (+0.54 /
-0.30) | -10.89 | -44.10 | 1.000 |
| `glm52_ep4_bf16_full_skew2` | 56.65 | 55.78 | -1.53 (-1.29 / -1.76) |
-13.54 | -39.13 | 1.000 |
| `glm52_ep4_bf16_full_skew4` | 87.44 | 84.32 | -3.57 (-3.26 / -3.87) |
-15.55 | -35.90 | 1.000 |
| `glm52_ep4_bf16_full_skew8` | 97.67 | 93.31 | -4.47 (-4.63 / -4.31) |
-16.24 | -35.50 | 1.000 |
| `glm52_ep4_mxfp8_ckpt` | 23.70 | 23.71 | +0.03 (+0.07 / -0.01) | -6.83
| n/a | 1.000 |
| `glm52_ep4_mxfp8_ckpt_imbal` | 51.97 | 50.45 | -2.93 (-2.87 / -2.99) |
-10.02 | n/a | 1.000 |
| `glm52_ep4_mxfp8_ckpt_mb393216` | 23.71 | 23.72 | +0.03 (-0.04 /
+0.10) | -6.91 | n/a | 1.000 |
| `glm52_ep4_mxfp8_ckpt_ragged` | 17.19 | 17.21 | +0.12 (+0.18 / +0.06)
| -4.55 | n/a | 1.000 |
| `glm52_ep4_mxfp8_ckpt_raggedimbal` | 30.98 | 30.98 | -0.02 (+0.33 /
-0.37) | -7.37 | n/a | 1.000 |
| `glm52_ep4_mxfp8_full_cap2` | 19.58 | 19.58 | -0.05 (-0.14 / +0.04) |
-7.49 | n/a | 1.000 |
| `glm52_ep4_mxfp8_full` | 19.41 | 19.42 | +0.04 (+0.01 / +0.07) | -7.01
| n/a | 1.000 |
| `glm52_ep4_mxfp8_full_imbal` | 44.66 | 43.00 | -3.71 (-3.76 / -3.66) |
-11.10 | n/a | 1.000 |
| `glm52_ep4_mxfp8_full_mb393216` | 19.45 | 19.43 | -0.08 (-0.18 /
+0.02) | -7.11 | n/a | 1.000 |
| `glm52_ep4_mxfp8_full_ragged` | 14.19 | 14.21 | +0.14 (+0.06 / +0.22)
| -4.75 | n/a | 1.000 |
| `glm52_ep4_mxfp8_full_raggedimbal` | 25.11 | 25.11 | -0.03 (+0.22 /
-0.28) | -8.38 | n/a | 1.000 |
| `glm52_ep4_mxfp8_full_skew2` | 44.68 | 42.98 | -3.80 (-3.72 / -3.87) |
-11.17 | n/a | 1.000 |
| `glm52_ep4_mxfp8_full_skew4` | 71.11 | 64.31 | -9.57 (-9.85 / -9.30) |
-16.59 | n/a | 1.000 |
| `glm52_ep4_mxfp8_full_skew8` | 80.23 | 71.61 | -10.74 (-10.58 /
-10.91) | -17.64 | n/a | 1.000 |

**VR200 EP4, BF16 and MXFP8** (measured at `28df319b5` against main
`e44067b1f`; the load observation is off on VR200 because
`imbalance_comm_sms="auto"` resolves to `None` there, so the PR arm
differs from main only by the re-exported backward kernels; two rounds
back-to-back on one lease (one 4 × VR200 node), mean over rounds,
per-round PR-vs-main in parentheses; `_nomok` rows run without the MoK
#17 arm because the MoK Rubin port does not support them (— in that
column); the DeepEP reference is BF16-only, so the MXFP8 rows show n/a)

| row | main ms | PR ms | PR vs main % | PR vs MoK #17 % | PR vs DeepEP
% | peak mem PR/main |
|---|---|---|---|---|---|---|
| `glm52_ep4_bf16_ckpt_imbal_nomok` | 41.41 | 39.99 | -3.44 (-3.58 /
-3.29) | — | -59.56 | 1.000 |
| `glm52_ep4_bf16_ckpt_mb393216_nomok` | 19.58 | 19.63 | +0.24 (+1.28 /
-0.79) | — | -59.81 | 1.000 |
| `glm52_ep4_bf16_ckpt_nomok` | 19.54 | 19.60 | +0.33 (+0.56 / +0.10) |
— | -59.81 | 1.000 |
| `glm52_ep4_bf16_ckpt_ragged_nomok` | 13.64 | 13.66 | +0.13 (+0.20 /
+0.06) | — | -59.93 | 1.000 |
| `glm52_ep4_bf16_ckpt_raggedimbal_nomok` | 24.42 | 24.44 | +0.12 (-0.06
/ +0.30) | — | -60.95 | 1.000 |
| `glm52_ep4_bf16_full_cap2_nomok` | 16.27 | 16.28 | +0.06 (-0.15 /
+0.27) | — | -55.97 | 1.000 |
| `glm52_ep4_bf16_full` | 16.30 | 16.28 | -0.13 (-0.17 / -0.09) | -75.26
| -55.42 | 1.000 |
| `glm52_ep4_bf16_full_imbal` | 35.81 | 34.70 | -3.09 (-3.10 / -3.08) |
-77.29 | -51.43 | 1.000 |
| `glm52_ep4_bf16_full_mb393216` | 16.33 | 16.26 | -0.39 (-0.51 / -0.27)
| -75.28 | -55.47 | 1.000 |
| `glm52_ep4_bf16_full_ragged_nomok` | 11.31 | 11.29 | -0.14 (-0.11 /
-0.17) | — | -56.52 | 1.000 |
| `glm52_ep4_bf16_full_raggedimbal_nomok` | 20.05 | 20.13 | +0.44 (+0.29
/ +0.59) | — | -56.37 | 1.000 |
| `glm52_ep4_bf16_full_skew2` | 35.82 | 34.65 | -3.28 (-2.94 / -3.62) |
-77.32 | -51.48 | 1.000 |
| `glm52_ep4_bf16_full_skew4` | 57.29 | 52.29 | -8.73 (-8.65 / -8.81) |
-76.96 | -48.84 | 1.000 |
| `glm52_ep4_bf16_full_skew8` | 64.65 | 58.25 | -9.90 (-9.98 / -9.82) |
-76.87 | -48.40 | 1.000 |
| `glm52_ep4_mxfp8_ckpt` | 13.94 | 13.95 | +0.10 (+0.13 / +0.07) |
-30.66 | n/a | 1.000 |
| `glm52_ep4_mxfp8_ckpt_imbal` | 29.89 | 28.82 | -3.58 (-3.60 / -3.56) |
-37.16 | n/a | 1.000 |
| `glm52_ep4_mxfp8_ckpt_mb393216` | 13.94 | 13.95 | +0.12 (+0.21 /
+0.04) | -30.60 | n/a | 1.000 |
| `glm52_ep4_mxfp8_ckpt_ragged_nomok` | 10.21 | 10.22 | +0.03 (-0.00 /
+0.07) | — | n/a | 1.000 |
| `glm52_ep4_mxfp8_ckpt_raggedimbal_nomok` | 17.28 | 17.30 | +0.07
(-0.00 / +0.14) | — | n/a | 1.000 |
| `glm52_ep4_mxfp8_full_cap2_nomok` | 11.31 | 11.32 | +0.09 (+0.14 /
+0.04) | — | n/a | 1.000 |
| `glm52_ep4_mxfp8_full` | 11.19 | 11.19 | +0.01 (-0.04 / +0.07) |
-30.90 | n/a | 1.000 |
| `glm52_ep4_mxfp8_full_imbal` | 25.29 | 24.24 | -4.15 (-4.12 / -4.17) |
-38.00 | n/a | 1.000 |
| `glm52_ep4_mxfp8_full_mb393216` | 11.19 | 11.20 | +0.08 (+0.00 /
+0.16) | -30.83 | n/a | 1.000 |
| `glm52_ep4_mxfp8_full_ragged_nomok` | 8.29 | 8.30 | +0.15 (+0.12 /
+0.17) | — | n/a | 1.000 |
| `glm52_ep4_mxfp8_full_raggedimbal_nomok` | 13.78 | 13.78 | +0.05
(+0.06 / +0.05) | — | n/a | 1.000 |
| `glm52_ep4_mxfp8_full_skew2` | 25.29 | 24.25 | -4.12 (-4.14 / -4.09) |
-37.98 | n/a | 1.000 |
| `glm52_ep4_mxfp8_full_skew4` | 39.74 | 36.06 | -9.27 (-9.24 / -9.30) |
-43.06 | n/a | 1.000 |
| `glm52_ep4_mxfp8_full_skew8` | 44.62 | 39.96 | -10.43 (-10.42 /
-10.44) | -44.04 | n/a | 1.000 |

Ragged + imbalanced rows: at `1fab8e62f` the EP8 rows were +2.5 % (full)
/ +0.8 % (checkpoint) and the EP4 checkpoint row +0.7 %
slower than main's package; of the remaining 25 rows measured there (all
BF16) only the EP4 full `mb393216` row (+0.70 %: +0.75 / +0.64) and the
EP4 full `cap2` row (+0.60 %: +0.63 / +0.58) also sat at or above the
+0.6 % band on the two-round mean, and the imbalanced and skewed rows
were
0.9–9.5 % faster. A five-arm diagnostic on one B200 node (main /
`1fab8e62f` / switch disabled / observing but never switching /
`edd4f7ff7`;
two rounds over the EP8 full and checkpoint ragged + imbalanced rows and
the uniform imbalanced row) attributed the EP8 slowdown to the 24 / 28
decision itself: the observation costs nothing
(observing-but-never-switching vs switch-disabled −0.7…+1.0 % per round
with both signs, within the
~1 % spread of code-identical arms), the re-exported kernels are neutral
on those rows (switch disabled vs main −0.4 / +0.6 % and +0.5 / −0.3 %),
and selecting 24 / 28 at a 3.0× routed load ratio cost +0.6…+1.6 % on
the EP8 ragged rows in that run (−0.1…+0.7 % when repeated on two other
nodes: 8 cells, 7 slower). Commit (4) moves the threshold so these rows
(and the uniform
imbalanced rows at 3.0×, where the switch also cost +0.4…+0.8 %) keep
the fixed split; the B200 BF16 tables above are measured at `9368b0664`
(the PR head `28df319b5` differs only by formatting and doc wording),
the MXFP8 and GB300 tables at `edd4f7ff7`, as labelled. Re-validation at
`9368b0664` leaves one row above the band: EP8 checkpoint ragged +
imbalanced +0.87 % (+1.21 / +0.53; its round-1 pair was re-measured once
as a
single paired run after the first round-1 main arm died in a shared
JIT-cache relink), still −9.0 % against MoK #17; the row does not switch
at
the new threshold, and the same code measured against main in six paired
rounds across the diagnostics averages +0.26 % with a ~1.5 pp spread.

Memory: peak and retained context identical to main's package at 0.01
GiB.

### Tests

Trees: the B200 column ran at `9368b0664` (runtime code of the PR head
`28df319b5`; the EP8 toy at `edd4f7ff7`); the GB300 column ran at
`edd4f7ff7` (commits 1 + 2), with `test_mok_bf16.py` / `_tolerance.py` /
`test_mok_mxfp8.py`, the EP4 torchrun tests and the BF16 + MXFP8 toys
repeated at `1fab8e62f`; the VR200 column ran at `edd4f7ff7`. Commits 3
and 4 change only the adapter's observation and threshold, which are
inactive on GB300 and VR200; the VR200 pair rows were re-measured at the
final head `28df319b5` (table above); GB300 is not re-measured because
the only code that changed after `edd4f7ff7` is the adapter observation,
which does not run there.

| test | B200 (sm_100a) | VR200 (sm_107a, at `edd4f7ff7`) | GB300
(sm_103a) |
|---|---|---|---|
| `tests/experimental/test_mok_bf16.py` (1 GPU) | 33 passed | 32 passed
| 32 passed (at `edd4f7ff7`); 33 passed (at `1fab8e62f`, which adds one
host-only test) |
| `tests/experimental/test_mok_bf16_tolerance.py` (1 GPU) | 10 passed |
10 passed (at `28df319b5`) | 10 passed (at `edd4f7ff7` and `1fab8e62f`)
|
| `tests/experimental/test_mok_mxfp8.py` (1 GPU) | 25 passed | 25 passed
| 25 passed (at `edd4f7ff7` and `1fab8e62f`) |
| torchrun EP4: `test_mok_bf16_distributed`, `_capacity`,
`test_mok_training_distributed` | 1 passed each | 1 passed each | 1
passed each (at `edd4f7ff7` and `1fab8e62f`) |
| torchrun EP4: `test_mok_bf16_unequal` | 1 passed | **1 failed —
pre-existing on main `e44067b1f` with the identical mismatch counts
(routed wgrad 587/685/802 of 262144, identical in all four runs); not
introduced here** | **1 failed — pre-existing on main `e44067b1f` with
the identical mismatch counts (routed wgrad 648/788/795 of 262144); not
introduced here** |
| `examples/mok_bf16_toy.py` EP4 BF16 (three CUDA-graph replays bitwise
equal) | 64/64 PASS (EP8: 128/128 at `edd4f7ff7`) | 64/64 PASS | 64/64
PASS (at `edd4f7ff7` and `1fab8e62f`) |
| toy arms MXFP8 / skew / clamped SwiGLU / GLM layout (EP4) | 7 arms
64/64 PASS | 4 MXFP8 arms + 3 BF16 arms, 64/64 PASS | 7 arms 64/64 PASS
(at `edd4f7ff7`; `ep4_bf16` + `ep4_mxfp8` repeated at `1fab8e62f`) |
| FP32-oracle fairness vs the reference (6 arms, mean ≤ 1.02×, max ≤
1.5×) | PASS (max ratio ≤ 1.000001, mean ≤ 1.00002) | — (not run) | PASS
at `edd4f7ff7` (max ratio ≤ 1.000001, mean ≤ 1.00001) |
| compute-sanitizer synccheck + memcheck (EP4 toy, BF16 and MXFP8) | 0
errors (BF16); 0 errors (MXFP8) | 0 errors (BF16); 0 errors (MXFP8) | 0
errors (BF16); 0 errors (MXFP8) (at `edd4f7ff7`) |
| pre-commit on the diff vs `e44067b1f` (at `28df319b5`) | all hooks
passed | | |


CI: the `pre-commit` check passes on the PR head `28df319b5` (all hooks;
clang-format has no files in scope because the exported
`flashinfer/experimental/cake_mok_bf16/csrc/` is excluded by
`.pre-commit-config.yaml`); the label-triggered run (`@flashinfer-bot
run
tests/experimental/test_mok_bf16.py
tests/experimental/test_mok_bf16_tolerance.py
tests/experimental/test_mok_mxfp8.py`, run 38491681098 on
`28df319b5`) passed: AOT build import on x64 / arm64 × cu129 / cu130 /
cu134 (6/6) and the targeted unit tests on H100 (`ci/test-scope-1`; the
SM100a-only kernel cases skip there, `test_mok_bf16_tolerance.py`
10/10). The automatic `PR Test` run stops at its authorization step
(`Report
unauthorized PR status`), as for every PR push; tests run only in the
label-triggered run. The GPU tests listed above ran on B200 (sm_100a)
and
GB300 (sm_103a); on VR200 (sm_107a) every row except the FP32-oracle
fairness check ran, at `edd4f7ff7`, and `test_mok_bf16_tolerance.py` at
`28df319b5`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added automatic communication-SM split selection for imbalanced routed
workloads, with configurable thresholds and optional split-change
logging. Existing fixed splits remain available, and automatic presets
are limited to supported device and precision combinations.
* Added BF16 and MXFP8 precision options when creating a MoK workspace.
* **Bug Fixes**
* Corrected backward communication to route input activations and
weighted gradients separately.
* **Documentation**
* Clarified CUDA version requirements: MXFP8 forward and recompute
require CUDA 13.1 or newer; backward supports CUDA 13.0.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [e43f75d](https://github.com/flashinfer-ai/flashinfer/commit/e43f75d4db39943ad4151e0f653efeba79cec3c1)

- **作者**: Yanqin Zhai
- **时间**: 2026-10-15T18:04:25Z
- **提交信息**: refactor-moe-engine-to-avoid-hardcoded-registry-table (#6503)

<!-- .github/pull_request_template.md -->

## 📌 Description

Replace the hardcoded cuDNN Frost registry with compact kernel catalogs
and shared templates across all four dtypes. Resolve device parameters
during preparation, fix BF16 autotune cache reuse, and support reusable
FP4 scale buffers.

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
* cuDNN Frost supports broader shape coverage with bounded tactic search
across supported data types, including eligible MXFP8 and NVFP4
backends.
* cuDNN Frost can run routing preparation, FC1, and FC2 as separate
stages.
* FP4 block-scale interleaving can write into a caller-provided output
tensor.
* Frost manifests support expanded catalog formats and remain compatible
with earlier versions.

* **Documentation**
* Expanded Frost guidance on supported shapes, search behavior, and
artifact catalogs.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [4c40d8b](https://github.com/flashinfer-ai/flashinfer/commit/4c40d8bbc7bf8420eff3bde6abc50722c5a70a36)

- **作者**: eigen
- **时间**: 2026-10-15T17:59:57Z
- **提交信息**: perf(cake_alpha_moe): dispatch the W8A8 fused MoE kernel by (M, K) across three pipeline variants (#6512)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

## 📌 Description

Speed up the SM100a / SM103a **AlphaMoE W8A8** fused expert compute
`alphamoe_fp8_block_scale_aligned_moe` (PR #4287 lineage;
`csrc/alphamoe_sm100.cu`) on **NVIDIA B200 (sm_100a)** and **NVIDIA
GB300 (sm_103a)** without changing its arithmetic. The merged kernel is
one fused up-SwiGLU-requantize-down megakernel with fixed 3-stage UP /
DOWN TMA rings and a synchronous epilogue. This head keeps the kernel
identity, signature, FP8 quantization recipe (E4M3, absmax / 448,
128-wide activation groups, 128 × 128 weight blocks), per-k-block MMA
products, FP32 accumulation order and BF16 bulk reduce-add, and changes
only **pipeline depth, epilogue wait placement and CTAs per SM**,
selected by the host from `(M, K)`:

| Host rule | Kernel namespace | Generator module of record | UP / DOWN
ring stages | CTAs / SM | Dynamic shared memory (B) | Registers / stack
/ local (sm_103a; sm_100a) |
|---|---|---|---:|---:|---:|---|
| `M > 8` | `w8a8_l2` |
`alpha_moe_w8a8_up_down_fp32acc_lw02l_cta2_up2_down2_async_v1` | 2 / 2 +
asynchronous epilogue | 2 (`__launch_bounds__(192, 2)`) | 104,576 | 84 /
0 / 0; 85 / 0 / 0 (+ 1024 B static shared) |
| `M <= 8` and `K >= 4096` | `w8a8_i2` |
`alpha_moe_w8a8_up_down_fp32acc_lw02i_up5_down3_async_v1` | 5 / 3 +
asynchronous epilogue | 1 | 222,336 | 84 / 0 / 0; 85 / 0 / 0 (+ 1024 B
static shared) |
| `M <= 8` and `K < 4096` | `w8a8_j2` |
`alpha_moe_w8a8_up_down_fp32acc_lw02j_stages4_async_v1` | 4 / 4 +
asynchronous epilogue | 1 | 204,928 | 84 / 0 / 0; 85 / 0 / 0 (+ 1024 B
static shared) |

"Asynchronous epilogue" = the per-output-block
`cp.async.bulk.wait_group.read 0` (shared-memory reuse only) inside the
output loop plus one `wait_group 0` after the loop, instead of a full
completion wait per output block; the global reduce-add round trip
leaves each of the serial per-CTA output chains. The three kernels are
generated from one source family (the FP32-accumulating base of the
merged kernel); each is captured to a cubin and composed into
`csrc/alphamoe_sm100.cu` under its own namespace; the host selects by
`(M, K)` and sets the per-kernel dynamic shared-memory attribute.

No public API change: flashinfer/fused_moe/alphamoe_sm100.py on the PR
head f364cacd is byte-identical to the pin (sha256 b5c5994b228bc4c7...);
the (M, K) dispatch to the i2 / j2 / l2 kernel variants is internal to
csrc/alphamoe_sm100.cu

### Final W8A8 kernel performance (v1, 2026-10-14)

Measured CUDA: this head `f364cacdb8de97f1ad616b758a3cfb3cc6fb2d23`,
`csrc/alphamoe_sm100.cu` sha256
`d1988ef3cd802e47e21366bcd91f1410b2befb9e9bbad32c20eeb0b02fd56dd3`.
Merged-`main` reference: `2d5b283d3ca2676c83fbfd746622b5c00c046044`,
`csrc/alphamoe_sm100.cu` sha256
`237a9b44549fa82fb3f7833ee51df76dd08d0927fc22674bc62c77c2182429b1`
(separate JIT build, same flags / ABI).

Arms: **S** = Stock = the **fastest valid library arm per row** among
(i) the stock SGLang Triton fused-MoE sequence (5 kernels = the PR #4287
protocol: Triton 3.6.0 `fused_moe_kernel` GEMM1 -> sgl-kernel
`act_and_mul_kernel` (SwiGLU) -> sgl-kernel
`per_token_quant_fp8_cta_kernel` (intermediate FP8 quantization) ->
Triton `fused_moe_kernel` GEMM2 -> Triton combine; sglang
0.5.14+nv26.7.59534057; SGLang pin
`5569b14d26ffd94a8326889eca15a153e8f1b68b`, sgl-kernel `0.4.4`; the
checkout used on each part is listed under Baselines) and (ii)
`trtllm_fp8_block_scale_routed_moe` (DeepSeek-FP8 128 × 128 block
scales) where it supports the row's geometry, measured as two variants:
`stock_trtllm` = natural MajorK expert weights
(`use_shuffled_weight=False`) and `stock_trtllm_shuffled` = the same
call with `use_shuffled_weight=True` and the expert weights pre-shuffled
per expert (`shuffle_matrix_a(w.view(uint8), 64)`; scales unchanged; the
shuffle is an untimed weight-layout conversion). The fastest valid arm
is chosen independently in each run, so the S arm can differ between run
1 and run 2 of the same row; the arm chosen per row and run and the
reason an arm is unsupported are listed under each table. **M** = the
merged-`main` AlphaMoE W8A8 kernel. **C** = this PR (the kernel the host
selects for the row). **T** = twin of C (second copy, independent output
buffers; A/A noise floor). Ratios > 1 favor C.

Same FP8 codes / scales, FP32 route weights and logical expert weights
for every arm; BF16 output. Timed interval = sum of correlated GPU
kernel durations (strict CUPTI activity tracing, cold L2 before every
sample; CPU gaps excluded). Input quantization, route alignment,
weight-layout conversion, allocation, JIT, warm-up and per-sample output
resets are untimed. S keeps its own intermediate rounding; C / M / T
share theirs.

Protocol (per architecture): **two independent runs on two different
whole-node allocations** (whole node held: 4 GPUs per node on GB300, 8
on B200; 1 used, the remaining GPUs verified idle with no other compute
processes before the run); same container and toolchain for all arms
inside a run. Each run has two lanes, run back to back on the same GPU:
lane C = this PR's tree (C, its own S arms, T) and lane M = the
merged-`main` tree (M, its own S arms and an M twin). Per arm and round:
5 warm-ups, 30 samples (median); within a lane the arm order alternates
every round (odd rounds: the lane's kernel (C in lane C, M in lane M),
`stock_sgl`, `stock_trtllm`, `stock_trtllm_shuffled`, its A/A twin (T);
even rounds reversed; arms unsupported on a row are skipped); **6
rounds** per lane and row (>= 5). Row durations = medians of the round
medians. **S / C** = median of the within-round S / C ratios of lane C.
**M / C** = ratio of the two lanes' row medians; M and C were not timed
in the same rounds, so the per-round M / C column in the round tables
below pairs round *i* of each lane by index only and its median can
differ slightly from the headline M / C (e.g. GB300 A8 run 1: 1.1633
headline vs 1.1642 median of the per-round column). Samples recorded:
23,040 in total (both parts, both runs, both lanes, every timed arm).

Fixtures: N = 2I = 256; weight scale blocks 128 × 128; activation groups
128; routing balancedness 0.8. **A8 / A128**: M = 8 / 128, K = 7168, E =
257, top-k = 9, one shared expert, routed scale 2.5, seeds 28101 /
28102. **Q8 / Q128**: M = 8 / 128, K = 2048, E = 512, top-k = 10, no
shared expert, routed scale 1.0, seeds 28103 / 28104. Q uses the
Qwen3-Next geometry; fixtures are deterministic performance inputs, not
real-request correctness.

S configuration (SGLang Triton arm, A rows): `{BLOCK_SIZE_M: 64,
BLOCK_SIZE_N: 128, BLOCK_SIZE_K: 128, GROUP_SIZE_M: 32, num_warps: 4,
num_stages: 3} (config_source default_fp8_w8a8_blockwise == PR #4287
stock dict, fused_moe_triton_config.py get_default_config; down_config
None; config_matches_pr4287 True; try_get_optimal_moe_config raised
ValueError "config namespace 'exec' not published" so the
runtime-context lookup fell back to the block-wise fp8 default)`; Q
rows: not a Triton config: the Q rows' Stock arm is
`trtllm_fp8_block_scale_routed_moe` (`stock_trtllm` /
`stock_trtllm_shuffled`); the A rows use the SGLang Triton fused-MoE
(`stock_sgl`). Kernels per sample: A rows S = 5 (the SGLang sequence
listed above; protocol definition, not a recorded count), C = 1, M = 1;
Q rows S = `trtllm_fp8_block_scale_routed_moe` (its per-sample launch
count was not recorded in the acceptance bench and is not stated here),
C = 1, M = 1. The C count is the recorded CUPTI activity count (1 on
every row and run); M is the single fused kernel
`kernel_alpha_moe_w8a8_up_down`.

**Hardware floor** per row = max(byte floor, FLOP floor) at the measured
HBM read plateau (GB300 7202.5 GB/s, B200 7166.3 GB/s): bytes = W1 + W2
of the touched experts (1 B / element + FP32 128 × 128 block scales) +
activations in / out -- GB300: the fixture routing was not counted, so
the expert count is the analytic upper bound (every expert a routed pair
could reach, plus the shared expert, capped at E) = 65 / 257 / 80 / 512
for A8 / A128 / Q8 / Q128, i.e. all experts on A128 and Q128; the GB300
floors are therefore upper bounds and their floor shares slightly high;
B200: experts counted from the fixture's routing (59 / 253 / 72 / 469
for A8 / A128 / Q8 / Q128); FLOPs = 6 · M · k · K · I at the measured
`tcgen05` FP8 stream rate × SM count × busy clock. "Floor share" = floor
/ C; reporting only.

#### NVIDIA GB300 (sm_103a)

| Case | Kernel (C) | S arm r1 / r2 | S (us) r1 / r2 | M (us) r1 / r2 |
C (us) r1 / r2 | S / C r1 / r2 | M / C r1 / r2 | Floor (us) | Floor
share r1 / r2 | Twin dev. r1 / r2 | FI order-aware gate r1 / r2 (fixed
FP8 tolerance pass fraction recorded, not gated); exact-order oracle
(see Precision / contract-oracle note) |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---|
| A8 | `kernel_alpha_moe_w8a8_up_down_w8a8_i2` | stock_sgl / stock_sgl |
110.83 / 109.15 | 72.08 / 71.26 | 61.96 / 61.60 | **1.7916 / 1.7715** |
1.1633 / 1.1568 | 24.87 | 40.1 % / 40.4 % | 0.41 % / 0.39 % | PASS /
PASS (order-aware bound pass in both runs; max abs diff vs FI reference
0.25 / 0.25; fixed FP8 tolerance pass fraction, recorded not gated:
1.000000 / 1.000000); not run on this row in the acceptance bench
(exact-order oracle recorded separately as a diagnostic) |
| A128 | `kernel_alpha_moe_w8a8_up_down_w8a8_l2` | stock_sgl / stock_sgl
| 354.60 / 354.38 | 201.25 / 202.27 | 149.78 / 149.90 | **2.3675 /
2.3649** | 1.3436 / 1.3494 | 98.63 | 65.8 % / 65.8 % | 0.43 % / 0.51 % |
PASS / PASS (order-aware bound pass in both runs; max abs diff vs FI
reference 0.5 / 0.5; fixed FP8 tolerance pass fraction, recorded not
gated: 0.999997 / 0.999998); not run on this row in the acceptance bench
(exact-order oracle recorded separately as a diagnostic) |
| Q8 | `kernel_alpha_moe_w8a8_up_down_w8a8_j2` | stock_trtllm_shuffled /
stock_trtllm_shuffled | 33.08 / 32.52 | 25.34 / 25.75 | 22.78 / 22.97 |
**1.4515 / 1.4170** | 1.1128 / 1.1212 | 8.74 | 38.4 % / 38.1 % | 0.56 %
/ 0.14 % | PASS / PASS (order-aware bound pass in both runs; max abs
diff vs FI reference 0.03125 / 0.03125; fixed FP8 tolerance pass
fraction, recorded not gated: 1.000000 / 1.000000); not run on this row
in the acceptance bench (exact-order oracle recorded separately as a
diagnostic) |
| Q128 | `kernel_alpha_moe_w8a8_up_down_w8a8_l2` | stock_trtllm /
stock_trtllm | 109.89 / 109.78 | 105.62 / 105.69 | 85.23 / 85.38 |
**1.2910 / 1.2854** | 1.2392 / 1.2379 | 56.03 | 65.7 % / 65.6 % | 0.38 %
/ 0.55 % | PASS / PASS (order-aware bound pass in both runs; max abs
diff vs FI reference 0.03125 / 0.0625; fixed FP8 tolerance pass
fraction, recorded not gated: 1.000000 / 1.000000); not run on this row
in the acceptance bench (exact-order oracle recorded separately as a
diagnostic) |

Stock arm status per row (GB300) -- SGLang Triton (`stock_sgl`): A8,
A128: ready in both runs; S arm on this row = `stock_sgl` in both runs;
Q8, Q128: ready in both runs. `trtllm_fp8_block_scale_routed_moe`
(`stock_trtllm` unshuffled / `stock_trtllm_shuffled`): A8, A128:
unsupported: num_experts=257 % 4 != 0 --
csrc/trtllm_fused_moe_kernel_launcher.cu:4090-4091 'Routing kernel
expects that num_experts must be divisible by 4'; the shared expert can
only be a routed id because the routed wrapper passes
num_fused_shared_experts=0 (flashinfer/fused_moe/core.py:6343) (both
variants `stock_trtllm` / `stock_trtllm_shuffled`) in both runs; Q8:
ready (both variants `stock_trtllm` / `stock_trtllm_shuffled`) in both
runs; S arm on this row = `stock_trtllm_shuffled` in both runs; Q128:
ready (both variants `stock_trtllm` / `stock_trtllm_shuffled`) in both
runs; S arm on this row = `stock_trtllm` in both runs.
GB300: **4/4 rows with S / C > 1 in both runs**; geomean(M / C) =
**1.2116 / 1.2132**. Twin deviation of C (largest single-round deviation
between C and T): run 1 max 0.56 % on `w8a8_Q8` (the other 3 rows <=
0.43 %; on that row the main lane's twin 0.63 %); run 2 max 0.55 % on
`w8a8_Q128` (the other 3 rows <= 0.51 %; on that row the main lane's
twin 0.58 %). Rows below 1 vs S in either run: none. Rows below 1 vs M
in either run: none. Rows failing the row gate or the non-regression
rule: none.

<details><summary>GB300: every paired round (run 1, run 2)</summary>

| row | round | S us | M us | C us | T us | S/C | M/C |
|---|---:|---:|---:|---:|---:|---:|---:|
| A8 | 1 | 107.39 | 71.84 | 61.98 | 62.00 | 1.7326 | 1.1590 |
| A8 | 2 | 107.97 | 71.81 | 62.06 | 62.21 | 1.7396 | 1.1570 |
| A8 | 3 | 113.55 | 72.25 | 61.94 | 61.97 | 1.8334 | 1.1666 |
| A8 | 4 | 111.81 | 72.19 | 62.11 | 62.03 | 1.8001 | 1.1623 |
| A8 | 5 | 110.35 | 72.37 | 61.89 | 61.92 | 1.7831 | 1.1693 |
| A8 | 6 | 111.31 | 71.97 | 61.71 | 61.97 | 1.8037 | 1.1662 |
| A128 | 1 | 354.69 | 201.28 | 150.45 | 149.81 | 2.3575 | 1.3379 |
| A128 | 2 | 354.62 | 200.90 | 149.73 | 150.16 | 2.3685 | 1.3418 |
| A128 | 3 | 354.83 | 201.33 | 149.78 | 150.26 | 2.3691 | 1.3442 |
| A128 | 4 | 354.58 | 201.54 | 149.90 | 149.42 | 2.3654 | 1.3444 |
| A128 | 5 | 354.50 | 201.22 | 149.79 | 149.89 | 2.3666 | 1.3433 |
| A128 | 6 | 354.53 | 200.94 | 149.55 | 149.58 | 2.3706 | 1.3437 |
| Q8 | 1 | 33.07 | 25.44 | 22.85 | 22.72 | 1.4474 | 1.1134 |
| Q8 | 2 | 33.02 | 25.36 | 22.78 | 22.72 | 1.4495 | 1.1131 |
| Q8 | 3 | 33.09 | 25.28 | 22.69 | 22.70 | 1.4584 | 1.1142 |
| Q8 | 4 | 32.98 | 25.31 | 22.75 | 22.72 | 1.4494 | 1.1125 |
| Q8 | 5 | 33.17 | 25.33 | 22.77 | 22.78 | 1.4568 | 1.1124 |
| Q8 | 6 | 33.12 | 25.42 | 22.78 | 22.85 | 1.4536 | 1.1158 |
| Q128 | 1 | 109.78 | 105.84 | 85.38 | 85.26 | 1.2858 | 1.2397 |
| Q128 | 2 | 110.13 | 105.55 | 85.22 | 85.17 | 1.2923 | 1.2387 |
| Q128 | 3 | 109.97 | 105.94 | 85.25 | 84.96 | 1.2900 | 1.2427 |
| Q128 | 4 | 109.81 | 105.68 | 84.99 | 85.31 | 1.2920 | 1.2434 |
| Q128 | 5 | 109.66 | 105.43 | 85.33 | 85.02 | 1.2852 | 1.2355 |
| Q128 | 6 | 110.08 | 105.55 | 85.12 | 85.15 | 1.2932 | 1.2400 |

| row | round | S us | M us | C us | T us | S/C | M/C |
|---|---:|---:|---:|---:|---:|---:|---:|
| A8 | 1 | 104.21 | 71.41 | 61.76 | 61.52 | 1.6873 | 1.1562 |
| A8 | 2 | 107.76 | 71.25 | 61.54 | 61.58 | 1.7512 | 1.1578 |
| A8 | 3 | 108.90 | 71.25 | 61.52 | 61.41 | 1.7701 | 1.1581 |
| A8 | 4 | 109.41 | 71.28 | 61.71 | 61.58 | 1.7729 | 1.1550 |
| A8 | 5 | 111.91 | 71.01 | 61.66 | 61.42 | 1.8148 | 1.1515 |
| A8 | 6 | 110.82 | 71.26 | 61.50 | 61.62 | 1.8018 | 1.1587 |
| A128 | 1 | 354.30 | 202.29 | 149.33 | 150.10 | 2.3727 | 1.3547 |
| A128 | 2 | 354.53 | 202.19 | 149.63 | 149.60 | 2.3693 | 1.3513 |
| A128 | 3 | 354.27 | 202.26 | 150.02 | 149.54 | 2.3616 | 1.3482 |
| A128 | 4 | 354.24 | 202.35 | 150.21 | 150.29 | 2.3583 | 1.3471 |
| A128 | 5 | 354.45 | 202.30 | 150.02 | 149.74 | 2.3627 | 1.3485 |
| A128 | 6 | 354.54 | 202.22 | 149.78 | 149.68 | 2.3672 | 1.3502 |
| Q8 | 1 | 32.45 | 25.70 | 22.91 | 22.93 | 1.4162 | 1.1216 |
| Q8 | 2 | 32.46 | 25.78 | 22.96 | 22.96 | 1.4139 | 1.1226 |
| Q8 | 3 | 32.58 | 25.73 | 22.98 | 22.98 | 1.4178 | 1.1198 |
| Q8 | 4 | 32.83 | 25.65 | 23.02 | 22.99 | 1.4260 | 1.1140 |
| Q8 | 5 | 32.38 | 25.78 | 22.91 | 22.91 | 1.4134 | 1.1250 |
| Q8 | 6 | 32.85 | 25.86 | 22.98 | 22.94 | 1.4297 | 1.1254 |
| Q128 | 1 | 109.83 | 105.70 | 85.46 | 85.14 | 1.2852 | 1.2368 |
| Q128 | 2 | 110.05 | 105.79 | 84.85 | 85.31 | 1.2970 | 1.2468 |
| Q128 | 3 | 110.13 | 105.26 | 85.36 | 85.19 | 1.2902 | 1.2332 |
| Q128 | 4 | 109.55 | 105.68 | 85.22 | 85.42 | 1.2856 | 1.2401 |
| Q128 | 5 | 109.73 | 105.54 | 85.39 | 85.58 | 1.2850 | 1.2359 |
| Q128 | 6 | 109.47 | 105.79 | 85.49 | 85.23 | 1.2806 | 1.2375 |

</details>

#### NVIDIA B200 (sm_100a)

| Case | Kernel (C) | S arm r1 / r2 | S (us) r1 / r2 | M (us) r1 / r2 |
C (us) r1 / r2 | S / C r1 / r2 | M / C r1 / r2 | Floor (us) | Floor
share r1 / r2 | Twin dev. r1 / r2 | FI order-aware gate r1 / r2 (fixed
FP8 tolerance pass fraction recorded, not gated); exact-order oracle
(see Precision / contract-oracle note) |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---|
| A8 | `kernel_alpha_moe_w8a8_up_down_w8a8_i2` | stock_sgl / stock_sgl |
139.30 / 139.77 | 75.27 / 75.67 | 64.64 / 64.46 | **2.1552 / 2.1682** |
1.1645 / 1.1740 | 22.69 | 35.1 % / 35.2 % | 0.35 % / 0.60 % | PASS /
PASS (order-aware bound pass in both runs; max abs diff vs FI reference
0.5 / 0.5; fixed FP8 tolerance pass fraction, recorded not gated:
1.000000 / 1.000000); not run on this row in the acceptance bench
(exact-order oracle recorded separately as a diagnostic) |
| A128 | `kernel_alpha_moe_w8a8_up_down_w8a8_l2` | stock_sgl / stock_sgl
| 378.43 / 378.70 | 212.30 / 212.17 | 156.46 / 156.68 | **2.4183 /
2.4180** | 1.3569 / 1.3542 | 97.59 | 62.4 % / 62.3 % | 0.32 % / 0.36 % |
PASS / PASS (order-aware bound pass in both runs; max abs diff vs FI
reference 0.5 / 0.5; fixed FP8 tolerance pass fraction, recorded not
gated: 0.999998 / 0.999997); not run on this row in the acceptance bench
(exact-order oracle recorded separately as a diagnostic) |
| Q8 | `kernel_alpha_moe_w8a8_up_down_w8a8_j2` | stock_trtllm /
stock_trtllm_shuffled | 38.60 / 38.85 | 26.85 / 26.91 | 23.59 / 23.62 |
**1.6356 / 1.6433** | 1.1380 / 1.1395 | 7.91 | 33.5 % / 33.5 % | 0.34 %
/ 0.27 % | PASS / PASS (order-aware bound pass in both runs; max abs
diff vs FI reference 0.03125 / 0.03125; fixed FP8 tolerance pass
fraction, recorded not gated: 1.000000 / 1.000000); not run on this row
in the acceptance bench (exact-order oracle recorded separately as a
diagnostic) |
| Q128 | `kernel_alpha_moe_w8a8_up_down_w8a8_l2` | stock_trtllm /
stock_trtllm_shuffled | 115.91 / 115.84 | 109.85 / 109.75 | 89.05 /
89.18 | **1.3018 / 1.2990** | 1.2336 / 1.2306 | 51.59 | 57.9 % / 57.9 %
| 0.43 % / 0.30 % | PASS / PASS (order-aware bound pass in both runs;
max abs diff vs FI reference 0.07812 / 0.04688; fixed FP8 tolerance pass
fraction, recorded not gated: 1.000000 / 1.000000); not run on this row
in the acceptance bench (exact-order oracle recorded separately as a
diagnostic) |

Stock arm status per row (B200) -- SGLang Triton (`stock_sgl`): A8,
A128: ready in both runs; S arm on this row = `stock_sgl` in both runs;
Q8, Q128: ready in both runs. `trtllm_fp8_block_scale_routed_moe`
(`stock_trtllm` unshuffled / `stock_trtllm_shuffled`): A8, A128:
unsupported: num_experts=257 % 4 != 0 --
csrc/trtllm_fused_moe_kernel_launcher.cu:4090-4091 'Routing kernel
expects that num_experts must be divisible by 4'; the shared expert can
only be a routed id because the routed wrapper passes
num_fused_shared_experts=0 (flashinfer/fused_moe/core.py:6343) (both
variants `stock_trtllm` / `stock_trtllm_shuffled`) in both runs; Q8,
Q128: ready (both variants `stock_trtllm` / `stock_trtllm_shuffled`) in
both runs; S arm on this row = `stock_trtllm` in run 1,
`stock_trtllm_shuffled` in run 2.
B200: **4/4 rows with S / C > 1 in both runs**; geomean(M / C) =
**1.2204 / 1.2219**. Twin deviation of C (largest single-round deviation
between C and T): run 1 max 0.43 % on `w8a8_Q128` (the other 3 rows <=
0.35 %; on that row the main lane's twin 0.28 %); run 2 max 0.60 % on
`w8a8_A8` (the other 3 rows <= 0.36 %; on that row the main lane's twin
0.65 %). Rows below 1 vs S in either run: none. Rows below 1 vs M in
either run: none. Rows failing the row gate or the non-regression rule:
none.

<details><summary>B200: every paired round (run 1, run 2)</summary>

| row | round | S us | M us | C us | T us | S/C | M/C |
|---|---:|---:|---:|---:|---:|---:|---:|
| A8 | 1 | 139.17 | 75.39 | 64.61 | 64.75 | 2.1540 | 1.1669 |
| A8 | 2 | 139.10 | 75.09 | 64.46 | 64.61 | 2.1579 | 1.1648 |
| A8 | 3 | 139.04 | 75.34 | 64.59 | 64.43 | 2.1526 | 1.1665 |
| A8 | 4 | 139.42 | 74.94 | 64.67 | 64.50 | 2.1559 | 1.1588 |
| A8 | 5 | 139.52 | 75.38 | 64.67 | 64.45 | 2.1573 | 1.1655 |
| A8 | 6 | 139.50 | 75.20 | 64.75 | 64.70 | 2.1544 | 1.1613 |
| A128 | 1 | 378.40 | 212.10 | 156.62 | 156.37 | 2.4160 | 1.3542 |
| A128 | 2 | 378.72 | 212.27 | 156.43 | 156.45 | 2.4210 | 1.3570 |
| A128 | 3 | 378.53 | 212.41 | 156.34 | 156.70 | 2.4212 | 1.3587 |
| A128 | 4 | 378.46 | 211.73 | 156.48 | 156.48 | 2.4186 | 1.3531 |
| A128 | 5 | 378.16 | 212.35 | 156.40 | 156.42 | 2.4179 | 1.3577 |
| A128 | 6 | 378.09 | 212.32 | 156.85 | 156.35 | 2.4106 | 1.3537 |
| Q8 | 1 | 38.61 | 26.88 | 23.60 | 23.52 | 1.6359 | 1.1390 |
| Q8 | 2 | 38.67 | 26.75 | 23.65 | 23.60 | 1.6353 | 1.1313 |
| Q8 | 3 | 38.40 | 26.98 | 23.58 | 23.60 | 1.6283 | 1.1439 |
| Q8 | 4 | 38.73 | 26.82 | 23.58 | 23.58 | 1.6424 | 1.1370 |
| Q8 | 5 | 38.59 | 26.82 | 23.58 | 23.60 | 1.6364 | 1.1370 |
| Q8 | 6 | 38.51 | 26.93 | 23.60 | 23.57 | 1.6319 | 1.1410 |
| Q128 | 1 | 115.76 | 109.66 | 88.99 | 88.99 | 1.3008 | 1.2323 |
| Q128 | 2 | 116.06 | 110.14 | 88.85 | 89.10 | 1.3063 | 1.2397 |
| Q128 | 3 | 116.22 | 109.86 | 89.10 | 89.02 | 1.3044 | 1.2329 |
| Q128 | 4 | 115.84 | 109.74 | 88.93 | 89.12 | 1.3026 | 1.2341 |
| Q128 | 5 | 115.98 | 109.84 | 89.15 | 89.04 | 1.3010 | 1.2320 |
| Q128 | 6 | 115.82 | 109.94 | 89.46 | 89.07 | 1.2948 | 1.2289 |

| row | round | S us | M us | C us | T us | S/C | M/C |
|---|---:|---:|---:|---:|---:|---:|---:|
| A8 | 1 | 139.73 | 75.68 | 64.46 | 64.24 | 2.1675 | 1.1740 |
| A8 | 2 | 139.77 | 75.70 | 64.45 | 64.53 | 2.1688 | 1.1745 |
| A8 | 3 | 139.52 | 75.66 | 64.35 | 64.74 | 2.1681 | 1.1758 |
| A8 | 4 | 139.77 | 75.86 | 64.46 | 64.77 | 2.1683 | 1.1767 |
| A8 | 5 | 139.85 | 75.55 | 64.40 | 64.64 | 2.1717 | 1.1732 |
| A8 | 6 | 140.00 | 75.57 | 64.62 | 64.75 | 2.1664 | 1.1693 |
| A128 | 1 | 379.05 | 212.16 | 156.64 | 156.35 | 2.4199 | 1.3544 |
| A128 | 2 | 378.65 | 212.45 | 156.72 | 156.38 | 2.4161 | 1.3556 |
| A128 | 3 | 378.91 | 211.50 | 157.07 | 156.51 | 2.4123 | 1.3465 |
| A128 | 4 | 378.70 | 212.45 | 156.41 | 156.93 | 2.4211 | 1.3582 |
| A128 | 5 | 378.41 | 212.11 | 156.90 | 156.35 | 2.4119 | 1.3519 |
| A128 | 6 | 378.70 | 212.18 | 156.45 | 156.54 | 2.4206 | 1.3562 |
| Q8 | 1 | 38.86 | 26.91 | 23.62 | 23.62 | 1.6457 | 1.1395 |
| Q8 | 2 | 38.85 | 26.86 | 23.62 | 23.63 | 1.6450 | 1.1375 |
| Q8 | 3 | 39.37 | 26.91 | 23.65 | 23.58 | 1.6650 | 1.1380 |
| Q8 | 4 | 38.58 | 26.75 | 23.62 | 23.60 | 1.6334 | 1.1328 |
| Q8 | 5 | 38.69 | 27.02 | 23.62 | 23.65 | 1.6382 | 1.1443 |
| Q8 | 6 | 38.85 | 26.91 | 23.66 | 23.62 | 1.6416 | 1.1372 |
| Q128 | 1 | 115.76 | 109.79 | 89.46 | 89.23 | 1.2940 | 1.2273 |
| Q128 | 2 | 115.95 | 109.71 | 89.25 | 88.98 | 1.2992 | 1.2293 |
| Q128 | 3 | 115.79 | 109.86 | 89.15 | 89.10 | 1.2988 | 1.2322 |
| Q128 | 4 | 115.58 | 109.55 | 89.15 | 88.99 | 1.2965 | 1.2288 |
| Q128 | 5 | 116.08 | 109.62 | 89.22 | 89.26 | 1.3011 | 1.2287 |
| Q128 | 6 | 115.89 | 110.09 | 89.01 | 88.98 | 1.3020 | 1.2369 |

</details>

<details>
<summary>Measurement identity per run</summary>

| Arch / run | GPU (name, UUID) | Driver | Median busy SM clock (MHz) |
Container image (sha256 of the image file) | S sources | M source | C
source |
|---|---|---|---:|---|---|---|---|
| GB300 run 1 | NVIDIA GB300, `6a3d023a-4572-1145-8cf5-48627a71f3fc` |
580.159.03 | 2070 |
`ff910f2f900c58f8cfd9837ba7d4f98a6d755e62048f335e5c57fbdf5f6c1c00` |
SGLang `5569b14d26ffd94a8326889eca15a153e8f1b68b`, sgl-kernel `0.4.4`;
trtllm-gen cubins `35cb99413a3ebce2e87a03fc04196e528e22c8d5` | csrc
`237a9b44549fa82fb3f7833ee51df76dd08d0927fc22674bc62c77c2182429b1` @
`2d5b283d3ca2676c83fbfd746622b5c00c046044` | csrc
`d1988ef3cd802e47e21366bcd91f1410b2befb9e9bbad32c20eeb0b02fd56dd3` @
`f364cacdb8de97f1ad616b758a3cfb3cc6fb2d23` |
| GB300 run 2 | NVIDIA GB300, `3a31c974-a4f8-ab10-29e9-6463c45f0cdd` |
580.159.03 | 2070 | same | same | same | same |
| B200 run 1 | NVIDIA B200, `65cb3b9c-09e7-9429-187f-aef74634c32e` |
580.82.07 | 1965 |
`eb6812256b15ac860d43d371296f4a8f8810aac1b53cf7cf0e8c985f7ad16075` |
SGLang `684fea8af3b11a5b51ec9966c02959a32ad3421c`, sgl-kernel `0.4.4`;
trtllm-gen cubins `35cb99413a3ebce2e87a03fc04196e528e22c8d5` | same |
same |
| B200 run 2 | NVIDIA B200, `c502242e-3548-1a43-d781-9b437291017e` |
580.82.07 | 1965 | same | same | same | same |

Default (boost) clocks, no clock lock; FP32 references computed with
TF32 disabled (`TORCH_ALLOW_TF32_CUBLAS_OVERRIDE` unset) in every arm
and test.
</details>

### Numerics (v1, 2026-10-14)

- **Unchanged arithmetic.** The per-k-block FP8 MMA products, the
consumer's FP32 accumulation order (`panel += partial * scale` in FP32),
the SwiGLU / requantization (E4M3, absmax / 448, 128-wide groups) and
the final BF16 bulk reduce-add are the merged kernel's. The three
kernels differ from it only in ring depth, epilogue wait placement and
CTAs per SM. No fast-math change, no tolerance change, no
quantization-recipe change.
- **Why "bitwise vs `main`" is not the gate for this kernel.** The
merged kernel's cross-CTA output reduction (`cp.reduce.async.bulk.add`
into BF16) is order-nondeterministic by construction, and this PR's
kernels use that reduce-add unchanged, so no two runs of either kernel
are guaranteed bit-identical (the `tests/moe/test_alphamoe_sm100.py`
reference encodes this as the legal async-order bound). Measured on this
PR's kernel: its in-process twin **T** (a second copy of the same kernel
on independent output buffers, same inputs) is bit-identical to **C** in
0 of 16 cells (4 rows x 2 parts x 2 runs), with max |diff| 0.5 on the A
rows / 0.0625 on the Q rows (output max |value| 61.5 / 5.438). No
separate twin-vs-twin figure was recorded for the merged kernel. The
acceptance gate is therefore the independent order-aware reference
below, applied to every row on both parts, in every run; the un-widened
fixed tolerance against the same reference is recorded alongside it.
- **FI order-aware reference -- the gate**
(`tests/moe/test_alphamoe_sm100.py` criterion: independent FP32
reference with the legal BF16 async-order bound `max(atol + rtol*|ref|,
2 * |BF16 contribution mass| * 2^-7)`; contributions per element = top-k
x (N / 256): 9 on the A8 / A128 rows, 10 on the Q8 / Q128 rows): PASS on
4/4 rows x 2 parts x 2 runs (largest max |diff| vs the FI reference 0.5,
reached on `w8a8_A8` on B200 in both runs; `w8a8_A128` on both parts in
both runs; every other cell <= 0.25).
- Fixed elementwise FP8 tolerance vs the FlashInfer test's independent
FP32 reference (single fixed order, `atol + rtol * |reference|`, atol =
rtol = 0.1; no order-aware widening) -- **recorded, not gated**: pass
fraction 1.000000 in every cell of `w8a8_A8`, `w8a8_Q8`, `w8a8_Q128`;
below 1.0 on `w8a8_A128`: GB300 run 1 0.999997 (3 of 917,504 elements),
GB300 run 2 0.999998 (2 of 917,504 elements), B200 run 1 0.999998 (2 of
917,504 elements), B200 run 2 0.999997 (3 of 917,504 elements)
(cancellation cases near zero are what the order-aware bound exists for;
a kernel whose cross-CTA BF16 reduce-add order is nondeterministic is
not held to this single-reference per-element tolerance, see the note
below).
- **Exact-order contract oracle** (the CAKE team's internal W8A8
evaluation contract
`design_doc/active/eval_contract_alpha_moe_w8a8_up_down.yaml`, not part
of this repository): see "Precision / contract-oracle note" directly
below -- it states the gate for this PR and reports the oracle outcome
for every arm, including the finding that the oracle's reference
revision, not the kernel, explains the failing shapes.
- Real-model (Qwen3-Next-80B-A3B FP8) end-to-end accuracy is **not
re-run** for this head: the numerics class is unchanged from the merged
kernel validated in #4287 (1259 / 1314 GSM8K, delta 0 vs stock Triton
experts); the kernel-level gates above are the acceptance evidence.

### Precision / contract-oracle note

**Gate for this PR.** W8A8 precision is accepted on one gate, applied to
every row on both parts in both acceptance runs: the FlashInfer
order-aware reference of `tests/moe/test_alphamoe_sm100.py` (independent
FP32 reference; FP8 tolerance atol = rtol = 0.1, widened per element by
the legal BF16 async-reduce-order bound `max(atol + rtol*|ref|, 2 *
|BF16 contribution mass| * 2^-7)`, i.e. every output element is finite
and within that bound of the reference): PASS on 4/4 rows x 2 parts x 2
runs (largest max |diff| vs the FI reference 0.5, reached on `w8a8_A8`
on B200 in both runs; `w8a8_A128` on both parts in both runs; every
other cell <= 0.25). This is the criterion the merged kernel (#4287) was
accepted under; this PR does not change the arithmetic, so the same
criterion applies. **Recorded, not gated:** the fraction of output
elements inside the un-widened per-element FP8 tolerance (atol + rtol *
|reference|, atol = rtol = 0.1) against the same FlashInfer FP32
reference -- pass fraction 1.000000 in every cell of `w8a8_A8`,
`w8a8_Q8`, `w8a8_Q128`; below 1.0 on `w8a8_A128`: GB300 run 1 0.999997
(3 of 917,504 elements), GB300 run 2 0.999998 (2 of 917,504 elements),
B200 run 1 0.999998 (2 of 917,504 elements), B200 run 2 0.999997 (3 of
917,504 elements). The misses are cancellation cases near zero, which
the order-aware bound exists for; a kernel whose cross-CTA BF16
reduce-add order is nondeterministic is not held to the un-widened
tolerance, and the CAKE team's contract records this field as recorded,
not gated.

**Recorded diagnostic, not a gate.** The CAKE team also keeps an
exact-source-order BF16 contract oracle in its internal W8A8 evaluation
contract `design_doc/active/eval_contract_alpha_moe_w8a8_up_down.yaml`
(not part of this repository; revision v3-2026-07-28: an independent
reference that enumerates the legal BF16 accumulation orders, FP8
tolerance atol = rtol = 0.1). It was run on 6 contract shapes against
four arms: the merged `main` kernel, this PR's kernels, the
FP32-accumulating generator base both are produced from, and a variant
that rounds every 128-wide partial sum to BF16. The first three arms
fail the same 3 shapes (M = 8 / E = 257 / K = 7168 / top-9; M = 32 / E =
512 / K = 2048 / top-8; M = 128 / E = 257 / K = 7168 / top-9 (block_m
16)) with near-identical maximum deviations (1.203125 / 0.2578125 /
1.65625 on merged `main`; 1.19921875 / 0.2578125 / 1.65625 on this PR's
kernels and on the generator base (fp32acc module)) and pass the three K
<= 512 shapes (M = 8 / K = 256 smoke, N = 512 width, M = 17 / K = 512
tail); the BF16-partial variant passes all 6 shapes, max |diff| 0.0. The
oracle's reference therefore encodes BF16-rounded partial accumulation,
not the FP32 accumulation of the merged kernel; the mismatch is a
property of that reference revision, not a regression introduced here
(merged `main` vs this PR under the same fixtures: bitwise on 1/6
(smoke); 0.0078125 (1-ulp-class async-order noise) on the two other
small shapes; 0.25 / 0.09375 / 0.5 on the three failing shapes). Oracle
outcome per arm, recorded verbatim: merged `main`: PASS 3/6; this PR's
kernels: PASS 3/6; generator base (fp32acc module): PASS 3/6;
BF16-partial reference module: PASS 6/6. Provenance: the oracle run was
executed on the GB300 part on the immediate predecessor build of this
head (same device code: the host-side `csrc/alphamoe_sm100.cu` differs
only in comments and dispatch formatting, 38 lines; each kernel's SASS
equals the same captured cubin on both parts, 0 differing lines, so the
results carry over by identity); a paired A/B of the two builds on B200
(2 paired rounds, all four rows) agreed within the twin control on every
row (time ratios 0.9996-1.0072). That internal contract now states the
single order-aware gate given above, records the un-widened fixed
tolerance as recorded, not gated, and records its exact-order clause as
a diagnostic; the oracle outcome is reported here so that the precision
statement above is complete.

### Validation on this head

The FlashInfer tests, the CUDA 12.9 build and the native SASS gate on
both parts ran on this head
(`f364cacdb8de97f1ad616b758a3cfb3cc6fb2d23`); the compute-sanitizer runs
and the contract-oracle run were recorded on the immediate predecessor
build of this head (same device code: the host-side
`csrc/alphamoe_sm100.cu` differs only in comments and dispatch
formatting, 38 lines; each kernel's SASS equals the same captured cubin
on both parts, 0 differing lines, so the results carry over by
identity).

- `tests/moe/test_alphamoe_sm100.py`: 9 passed on GB300 and B200 (incl.
`test_alphamoe_sm100_matches_reference` on every parametrized geometry,
which now exercises all three kernels through the `(M, K)` dispatch).
- Native gate: the built library's SASS for each of `w8a8_i2` /
`w8a8_j2` / `w8a8_l2` equals its captured cubin on both parts, 0
differing lines (GB300 / sm_103a: 2210 / 2210 / 2194 lines; B200 /
sm_100a: 2226 / 2226 / 2210 lines); register / stack / local usage per
kernel: 84 / 0 / 0 on GB300 (sm_103a), 85 / 0 / 0 with 1024 B static
shared memory on B200 (sm_100a); no spills on either part. The GB300
per-kernel line counts were recorded on single-kernel builds of the same
device code; on this head each kernel's SASS equals its captured cubin
and the predecessor build's, 0 differing lines on both parts.
- compute-sanitizer **memcheck / synccheck / racecheck** -- run on the
SASS-identical predecessor build named above -- on all four rows (A8 ->
`kernel_alpha_moe_w8a8_up_down_w8a8_i2`, A128 ->
`kernel_alpha_moe_w8a8_up_down_w8a8_l2`, Q8 ->
`kernel_alpha_moe_w8a8_up_down_w8a8_j2`, Q128 ->
`kernel_alpha_moe_w8a8_up_down_w8a8_l2`) on both parts: **0 errors / 0
errors / 0 hazards** (compute-sanitizer 2026.3 on the sm_103a part;
compute-sanitizer 2026.3.0.0 build 38637409 from the cuda_sanitizer_api
13.4.57 archive on the sm_100a part). Evidence method:
`--dump-kernel-launches` records one launch per instrumented kernel; the
verdict counts error *records* and requires an unfiltered launch record
naming each of the three kernels (1 instrumented launch of the expected
kernel per row and tool on both parts: A8 -> i2, Q8 -> j2, A128 / Q128
-> l2 (12/12)); a positive control (deliberately broken throw-away
fixture kernels under the same kernel filter) was reported by all three
tools on the sm_103a part in the same environment as its gate runs; no
separate positive control was run on the sm_100a part, whose
instrumentation evidence is the included launch records above (one
launch of the expected kernel per row and tool, 12 of 12).
- **CUDA 12.9 build**: the package built from this head and passed `9`
tests in the FlashInfer CI image
`docker.io/flashinfer/flashinfer-ci-cu129:20260930-b1420f1` (digest
`sha256:38eea3ca97eb5a35ab02d45fe8bb4c25762371f88afbb478d319c680b8cf43b5
(index; linux/arm64
sha256:74ae1561b99ee93f51b9ffe6a8a8798f9d6491620bc0db7064711c51cce17235,
linux/amd64
sha256:fc00b288930d6e77ddae908646527c26469f4a330db59d646e4c2f807e0e6b0e)`,
torch `2.13.0+cu129`, nvcc `12.9.41 (Build
cuda_12.9.r12.9/compiler.35813241_0)`, arch list `10.3a` on GB300 /
`10.0a` on B200. The arch-list deviation from the FlashInfer CI
configuration: `FLASHINFER_CUDA_ARCH_LIST` was set explicitly to the
node's architecture, whereas FlashInfer CI leaves it unset and lets the
JIT target the visible GPU (the same target on these nodes)).
- Pre-commit on the changed file (`csrc/alphamoe_sm100.cu`): all
applicable hooks passed, including clang-format (this csrc unit is in
clang-format scope; only the NVFP4 AlphaMoE unit is excluded); ruff /
mypy had no files to check on this csrc-only diff; no hook modified the
file.
- Convergence status against the hardware floor (reporting only): GB300
not converged: neither at bound nor levers exhausted; rows below 90 % of
the floor (worse run): `w8a8_A8` (40.1 %), `w8a8_A128` (65.8 %),
`w8a8_Q8` (38.1 %), `w8a8_Q128` (65.6 %); B200 not converged: neither at
bound nor levers exhausted; rows below 90 % of the floor (worse run):
`w8a8_A8` (35.1 %), `w8a8_A128` (62.3 %), `w8a8_Q8` (33.5 %),
`w8a8_Q128` (57.9 %).

### Public contract (unchanged from #4287)

- FP8 E4M3 activations `[M, K]` with FP32 per-token group-128 scales;
FP8 weights with FP32 128 × 128 block scales; gate/up rows use the
provided eight-row interleave (`alphamoe_interleave_gated_weights`).
- `K % 128 == 0`; combined gate/up width `N % 256 == 0`; `block_m >= 8`
and divisible by eight. An omitted output is zero-allocated; a supplied
BF16 output is an initial accumulator; the cross-CTA BF16 reduce-add
order is nondeterministic.
- JIT targets exact SM100a / SM103a only (SM100a needs CUDA >= 12.8,
SM103a CUDA >= 12.9). The `(M, K)` kernel choice is internal to the
binding; callers see one API.

### Baselines and their source PRs

| baseline | origin | files | used for |
|---|---|---|---|
| SGLang Triton fused-MoE sequence (5 kernels) | sgl-project/sglang
`main` @ `5569b14d26ffd94a8326889eca15a153e8f1b68b` (2026-10-13;
sgl-kernel `0.4.4`); checkout used by the Stock arm per part -- GB300:
the pin; B200: `684fea8af3b11a5b51ec9966c02959a32ad3421c` = pin + 7
commits (descendant), files differing vs the pin: layers/moe +
layers/quantization 0; sgl-kernel 0; python/sglang/srt/layers 3
(attention/dsa only (attention/dsa/dsa_indexer.py,
attention/dsa/utils.py, attention/dsa_backend.py)); whole tree 30 |
`python/sglang/srt/layers/moe/fused_moe_triton/...` | S arm where it is
the fastest valid arm |
| `trtllm_fp8_block_scale_routed_moe` (trtllm-gen FP8 block-scale fused
MoE, cubin artifacts `35cb99413a3ebce2e87a03fc04196e528e22c8d5`) |
flashinfer-ai/flashinfer `main` @
`2d5b283d3ca2676c83fbfd746622b5c00c046044` |
`flashinfer/fused_moe/core.py`, `csrc/trtllm_fused_moe_*.cu` | S arm
where supported and fastest; unsupported rows recorded with the
library's reason |
| merged AlphaMoE W8A8 kernel (PR #4287) | flashinfer-ai/flashinfer
`main` @ `2d5b283d3ca2676c83fbfd746622b5c00c046044`
(`csrc/alphamoe_sm100.cu` sha256
`237a9b44549fa82fb3f7833ee51df76dd08d0927fc22674bc62c77c2182429b1`) |
`csrc/alphamoe_sm100.cu`, `flashinfer/fused_moe/alphamoe_sm100.py` | M
arm (non-regression reference) |

## 🔍 Related Issues

Follow-up to #4287 (W8A8 expert compute). No API change.

## 🚀 Pull Request Checklist

- [x] I have read the [contributing
guidelines](https://github.com/flashinfer-ai/flashinfer/blob/main/CONTRIBUTING.md)
- [x] Pre-commit hooks pass on the changed files
- [x] Tests: `tests/moe/test_alphamoe_sm100.py` (9 cases)
- [x] Documentation: unchanged

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- cake-shared-references:start -->
## References

The shared reference corpus for CAKE kernel development includes the
following projects, documentation, and existing CAKE work:

- **GPU programming and instructions:** [NVIDIA CUDA Programming
Guide](https://docs.nvidia.com/cuda/cuda-programming-guide/index.html),
[NVIDIA PTX
ISA](https://docs.nvidia.com/cuda/parallel-thread-execution/), and
gau-nernst's [tcgen05 tutorial](https://gau-nernst.github.io/tcgen05/)
and [CUDA kernel examples](https://github.com/gau-nernst/learn-cuda).
- **Kernel programming libraries and compilers:** [NVIDIA CUTLASS /
CuTe](https://github.com/NVIDIA/cutlass),
[Triton](https://github.com/triton-lang/triton),
[TileLang](https://github.com/tile-ai/tilelang), [NVIDIA cuTile
Python](https://github.com/NVIDIA/cutile-python), and
[ThunderKittens](https://github.com/HazyResearch/ThunderKittens)
([ThunderKittens 2.0
techniques](https://hazyresearch.stanford.edu/blog/2026-02-19-tk-2)).
- **Attention and inference:** [FlashAttention (including Hopper and
CuTe implementations)](https://github.com/Dao-AILab/flash-attention),
[FlashInfer, including its TRT-LLM kernel
integration](https://github.com/flashinfer-ai/flashinfer), [Flash Linear
Attention](https://github.com/fla-org/flash-linear-attention),
[SageAttention](https://github.com/thu-ml/SageAttention),
[FlashAttention-FP4](https://github.com/hao-ai-lab/flash-attention-fp4),
and [FastVideo](https://github.com/hao-ai-lab/FastVideo).
- **GEMM and MoE:** [DeepGEMM](https://github.com/deepseek-ai/DeepGEMM),
[SonicMoE](https://github.com/Dao-AILab/sonic-moe),
[Alpha-MoE](https://github.com/Aleph-Alpha/Alpha-MoE), and [Mixture of
Kittens](https://github.com/cursor/mixture-of-kittens).
- **Clustering and nearest-neighbor kernels:** [Flash
K-Means](https://github.com/svg-project/flash-kmeans) and
[FlashLib](https://github.com/FlashML-org/flashlib).
- **Existing CAKE implementations and PRs:** [CAKE-generated kernel
progress tracker and PR index
(#4254)](https://github.com/flashinfer-ai/flashinfer/issues/4254).

These are corpus-level references. PR-specific implementation details,
changes, and benchmark references are documented above.
<!-- cake-shared-references:end -->

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [4f4a5ac](https://github.com/flashinfer-ai/flashinfer/commit/4f4a5ace75b5dce056d4ffa0f544072f600d7cc5)

- **作者**: eigen
- **时间**: 2026-10-15T17:59:34Z
- **提交信息**: perf(cake_alpha_moe): faster NVFP4 routed-MoE routes on sm_100a/sm_103a (self-routing up kernels, K-256 W2 panels, per-CC dispatch) (#6511)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

## 📌 Description

Speed up the SM100a / SM103a **AlphaMoE NVFP4** routed-MoE operator (PR
#4340 / #5930 lineage) on the representative decode, batched and
large-batch shapes of both Blackwell parts, **NVIDIA B200 (sm_100a)**
and **NVIDIA GB300 (sm_103a)**, without changing the quantization
recipe, tolerances, compile flags or precision class: the GLM-geometry
rows are bitwise identical to the Stock operator
`trtllm_fp4_block_scale_routed_moe` on 30 of the 32 (row, part, run)
cells (8 rows x 2 parts x 2 runs); the exceptions are `glm_decode_m8` on
B200 run 1 and run 2 (max abs diff vs Stock 0.125 in each) -- there this
PR is bitwise identical to the merged-`main` kernel, and both differ
from Stock on the same 3 of 49,152 elements by 1 BF16 ulp, within the
FP4 tolerance: the merged kernel's own class, not introduced here (see
Numerics); the H = 7168 / I = 128 rows stay within 2 BF16 ulp of Stock,
measured as the max abs diff in units of the BF16 ulp at the output's
maximum magnitude (`source_decode_m8` 0.25 ulp on GB300 / 0.0001221 ulp
on B200, `source_batch_m128` 1 / 1 ulp; the same per-element deviation
class as the merged-`main` kernels, see Numerics). Every row below is
measured against **two arms**: Stock, and the **merged `main` kernels**
(`2d5b283d3ca2676c83fbfd746622b5c00c046044`,
`csrc/alphamoe_nvfp4_sm100.cu` sha256
`5545845bd6841864e26d5a5cd86825eaaf41af5b72e21960181970d75d0c9d35`) so
that the PR is also shown to be a non-regression of the current library
on every row.

The host route selector keeps its `(M, N, K, block_m, prepared-weight
inputs)` shape; this head adds a device compute-capability dimension to
it (one route may pick a different kernel on CC 10.0 and CC 10.3).
For the M = 128 and M = 512 GLM shapes the head also adds routes whose
up kernel builds the expert-major token plan itself (routes 19 and 18
below), so the separate alignment launch of those chains disappears; the
kernels after the up kernel in each chain are unchanged.

### What changed, kernel by kernel

Every kernel below is generated from a named **generator module of
record**, captured to a cubin, composed into
`csrc/alphamoe_nvfp4_sm100.cu` as a new kernel namespace, and gated by a
kernel-by-kernel SASS comparison of the built library against the
merged-`main` library (only the planned additions / removals and the
one-line #6222 barrier fix in `moe_align_block_size_kernel` differ; see
"Validation on this head").

| Routes | Shapes affected | Kernel namespace in this PR (replaces) |
Generator module of record | Change | Precision class |
|---|---|---|---|---|---|
| 12 (M = 512 GLM), 10 (M = 128 GLM), 9 (M = 8 GLM) | `glm_batch_m512`,
`glm_batch_m128`, `glm_decode_m8` | `nvfp4_u1_c358nb_down` (replaces
`nvfp4_s14_c358n_down`), `nvfp4_u1_c360b_down` (replaces
`nvfp4_s12_c360_down`), `nvfp4_u1_c407b_down` (replaces
`nvfp4_s11_c407_down`) | `alpha_moe_candidate358n_runtime_n_down_v1`,
`alpha_moe_nvfp4_candidate360_preparedw2_evictfirst_down_v1`,
`alpha_moe_nvfp4_candidate407_fitz_down_v1` | The three BM8 down kernels
used named barriers 14 / 15; the hardware caps resident CTAs per SM by
the highest named-barrier id in use, so the kernels were capped at 2
CTAs/SM (ncu `launch__occupancy_limit_barriers` = 2; the driver also
sized the shared-memory carveout to that occupancy) although their
dynamic shared memory (49,152 / 38,912 B) allows 4 / 5 CTAs/SM. With ids
1 / 2 the barrier limit rises to 10 CTAs/SM and shared memory becomes
the binding limit (ncu on GB300: 4 CTAs/SM for `c358nb`, 5 for `c360b`;
warps active 16.9 % -> 30.6 % / 31.5 %). The generator change is the two
named-barrier ids (14 / 15 -> 1 / 2); the three kernels are re-emitted
from the current generator with the same dynamic shared memory,
shared-memory layout, thread count, launch bounds and MMA issue order
(registers 61 / 40 / 44 for `c358nb` / `c360b` / `c407b`; the shipped
`c360` used 48). | bitwise vs the merged-`main` kernels on
`glm_batch_m512` / `glm_batch_m128` / `glm_decode_m8` (output dump
compares, both parts, both runs) and vs Stock on those rows, except B200
`glm_decode_m8`, which inherits the route-9 chain class described in the
CC 10.0 row (bitwise vs merged `main`; 3 of 49,152 elements, 1 BF16 ulp
vs Stock) |
| 17 (new; = route 12 with the K-256 prepared W2 panels; reused as the
down kernel of the M = 512 chain below) | `glm_batch_m512` |
`nvfp4_u1_c358nd_down` (added) |
`alpha_moe_candidate358nd_k256panels_down_v1` | The route-12 down kernel
streams W2 as the 16 KB K-256 panels already produced by
`prepare_nvfp4_w2_data_k256` / `prepare_nvfp4_w2_scales_k256` (one TMA
pair per stage instead of two 8 KB K-128 boxes plus a scalar scale
gather). Not chosen by the host route selector on its own (the M = 512
GLM call with the K-256 sidecars, the route-16 inputs, takes the chain
in the rows below, which reuses this kernel as its down kernel); route
17 itself is reachable only by passing the route id explicitly to the
complete-routed op. Without the sidecars route 12 is unchanged. MMA
issue order unchanged (K-256 panel ascending, K-64 sub-MMAs ascending).
| bitwise vs route 12 and vs Stock |
| 9 (M = 8 GLM) on CC 10.0 only | `glm_decode_m8` on B200 |
`nvfp4_u1_c416t_up` (added; CC 10.3 keeps `nvfp4_s11_c416s_up`) |
`alpha_moe_nvfp4_candidate416t_s4_dual_up_v1` | The route-9 up kernel at
2 CTAs/SM (UP ring 3 stages, 108,800 B dynamic shared memory, low
barrier ids) is selected on sm_100a by a compute-capability check in the
host selector; sm_103a keeps the shipped kernel (it measured slower
there). The grid doubles accordingly. | B200: bitwise vs the
merged-`main` kernel (0 of 49,152 elements differ in both runs; gate of
record for this row); vs Stock: max abs diff vs Stock 0.125 (0.125 BF16
ulp at the output's maximum magnitude) (both runs), within the FP4
tolerance (atol 1.0 / rtol 0.1); both this PR and the merged-`main`
kernel differ from Stock on the same 3 of 49,152 elements (1 ordinal
BF16 ulp each; max abs diff 0.125 at an output maximum magnitude of 166)
-- inherited from the shipped route-9 chain, not introduced here (same
MMA / accumulation order as `c416s`); GB300 keeps `c416s` and is bitwise
vs Stock (see the B200 per-row table and Numerics) |
| 16 (large-batch, small-row band: `M * top_k < E * 128`) |
`glm_decode_m1000`, `glm_prefill_m2048` | `nvfp4_u1_c500ag_up` (replaces
`nvfp4_s13_c500ab_up`) |
`alpha_moe_nvfp4_c500ag_token_tile_gather_xsf_up_v1` | The token-tile up
kernel's consumer warp 0 gathers the 16 activation scale-factor words of
its rows directly from `hidden_states_scale` (live rows only; padded
rows get a zero word and no load; the next work item's row ids are
prefetched), so the separate x-scale-factor panel kernel (`c505d`) is no
longer launched for this band. The large band (`c500y`) still uses the
panel. Register count unchanged (168 / 0 stack / 0 local), dynamic
shared memory unchanged (222,208 B). | bitwise vs route 16 on `main` and
vs Stock (route-16 vs general-path test passes at M = 1000, the `c500ag`
band, and at M = 4096, the unchanged `c500y` band) |
| 8 (`moe_align_block_size_kernel`) | the 2..7-token small-alignment
path (route 8) of the H = 6144 / I = 512 GLM geometry; none of the
benchmark rows below | same kernel, one added `__syncthreads()` | n/a
(existing alignment kernel) | Adopts the one-line fix from
flashinfer-ai/flashinfer#6222 by @builtin-pb (Bo Peng, commit
`4d03fd19092e33080a92b8c67b1c57d320461dec`): the `prefix[]`
shared-memory writes were not ordered before the per-thread binary
search over `prefix[mid]` (a shared-memory read-after-write race that
can hand a whole block the wrong expert id). Credit to the original
author; the change is applied verbatim on top of this PR's base. |
correctness fix; no numeric change on the race-free path |
| 18 (new; = the route-17 chain with the alignment launch folded into
the up kernel) | `glm_batch_m512` | `nvfp4_u1_c340sr_up` (added; the
route-17 down kernel and the finalize kernel are reused unchanged) |
`alpha_moe_nvfp4_candidate340sr_selfroute_up_v1.py` | The route-17 chain
launched a separate alignment kernel (expert-major sort of the routed
pairs, prefix sums, token table) before the up kernel. Route 18 does
that work inside the up kernel: a static expert-major CTA map gives each
expert's first 32 routed pairs a first-owner CTA and the remainder
sibling slots, so every CTA finds its rows without waiting for a
published plan, and the plan the kernel does publish is kept canonical
so the down and finalize kernels stay byte-identical to route 17. Per
kernel on GB300 (route-18 vs route-17 A/B, same down and finalize
kernels): up kernel +3.79 us vs the route-17 up kernel, alignment launch
of 6.21 us removed, net -2.51 us on the row. On B200 (acceptance run 2,
route-18 chain vs the `main` route-12 chain): up kernel +5.26 us vs the
route-12 up kernel, alignment launch of 6.42 us removed, net -1.16 us
from the fold-in; the row's -8.37 us vs `main` also includes the down
kernel change (`c358n` -> `c358nd`, K-256 prepared W2 panels, -5.74 us)
and a shorter finalize (same kernel, -1.04 us). Selected for M = 512
exactly (the plan phases read the route ids as aligned 4-vectors,
`num_pairs % 4 == 0`); other token counts keep their routes. Registers
94 / 0 stack / 0 local; dynamic shared memory 90,368 B. | bitwise vs
route 17, the merged-`main` route-12 chain and Stock (acceptance
output-dump compares, see Numerics);
`tests/moe/test_alphamoe_nvfp4_selfroute.py` checks route 18 bitwise
against the prepared route-12 path on this head, incl. a skewed-routing
case: several experts with more than 32 routed pairs, so the
sibling-slot path is covered by the public tests |
| 19 (new; = the route-10 chain with the alignment launch folded into
the up kernel) | `glm_batch_m128` | `nvfp4_u1_c336sr_up` (added; the
route-10 down kernel is reused unchanged) |
`alpha_moe_nvfp4_candidate336sr_selfroute_up_v1.py` | The route-10 chain
launched the same separate alignment kernel before its up kernel. Route
19 applies the self-routing construction of route 18 to the M = 128 GLM
chain: the up kernel builds the expert-major token plan itself and
publishes the canonical plan, so the down kernel is unchanged and the
alignment launch disappears. Per kernel on GB300 (route-19 vs route-10
A/B, same down and finalize kernels): up kernel +1.06 us vs the route-10
up kernel, alignment launch of 4.19 us removed, net -2.83 us on the row.
On B200 (acceptance run 2, route-19 chain vs the `main` route-10 chain):
up kernel +1.02 us vs the route-10 up kernel, alignment launch of 3.81
us removed, net -2.79 us from the fold-in; the row's -2.84 us vs `main`
also includes the barrier-id down kernel change (`c360` -> `c360b`,
-0.21 us) and finalize (+0.03 us). Selected for the M = 128 GLM
geometry; other token counts keep their routes. Registers 80 / 0 stack /
0 local; dynamic shared memory 90,368 B. | bitwise vs route 10
(`tests/moe/test_alphamoe_nvfp4_selfroute.py`: prepared route-10 path on
this head, accumulate on and off) and vs the merged-`main` route-10
chain and Stock (acceptance output-dump compares) |
| 9 (extended to H = 7168, I = 128, M = 8) | `source_decode_m8` | host
selector only: for the N = 256, K = 7168, E = 256, top-k 8, block_m 8
geometry at M = 8, when the caller passes all route-9 prepared inputs,
the routed entry takes route 9 (deterministic finalize) instead of the
generic fp32-atomic path; M in {1, 4, 16, 128} keep the generic route |
existing route-9 kernels (runtime-generic in N / K) | The M = 8 / I =
128 row leaves the general split-K route (torch fill + align-seed + up +
down + copy, 5 launches) for the route-9 chain (up + down + finalize). |
GB300: <= 2 BF16 ulp vs Stock at the output's maximum magnitude (max abs
diff 0.5 = 0.25 ulp (both runs)); B200: <= 2 BF16 ulp vs Stock at the
output's maximum magnitude (max abs diff 0.0002441 = 0.0001221 ulp (both
runs)) (same convention as the Numerics section; deterministic finalize
instead of fp32 atomics, same deviation class as the merged `main`
kernels on this row) |

### Public API

No public API change: the host route selector keeps its (M, N, K,
block_m, prepared inputs) shape and adds a device compute-capability
dimension; the K-256 prepared W2 panels pass through the existing routed
and deferred entry points; no public API, helper, keyword or default
changes

### GPU performance (NVIDIA GB300 sm_103a and NVIDIA B200 sm_100a)

Boundary: complete routed operator, prequantized activations + route ids
/ weights in, BF16 out, for every arm. **Stock** =
`trtllm_fp4_block_scale_routed_moe` (shuffled weights, PDL, permutation
+ both GEMMs + intermediate quantization + finalization; autotuned once,
untimed). **main** = the merged-`main` AlphaMoE kernels at
`2d5b283d3ca2676c83fbfd746622b5c00c046044` (route alignment + kernels +
finalize). **This PR** = the same call on this head. Metric = sum of
correlated GPU kernel durations from strict CUPTI activity tracing with
a cold L2 before every sample. Per arm and round: 5 warm-up invocations,
then 30 samples (median). Each judged kernel runs in its own lane of
four arms whose order alternates every round (odd rounds: this PR,
Stock, this-PR A/A twin, Stock twin; even rounds reversed); **6 paired
rounds** (>= 5) per row. The this-PR lane and the main lane ran back to
back on the same GPU within the same allocation, each with its own Stock
arm and its own A/A twin. GPU sum (us) per arm = median over rounds of
the per-round sample medians. Speedup vs Stock = median over rounds of
the within-round ratio Stock / this PR (from this PR's lane). Speedup vs
main = main GPU sum / this PR GPU sum, i.e. the ratio of the two lanes'
round medians, not a within-round ratio; > 1 favors this PR.

Each architecture was measured in **two independent runs on two
different whole-node allocations** (whole node held: 4 GPUs per node on
GB300, 8 on B200; one GPU used, the remaining GPUs verified idle with no
other compute processes before the run), same container image and
toolchain for all arms inside a run. An **A/A twin** (a second copy of
this PR's kernels on independent output buffers, same inputs) ran in
every round of this PR's lane; the main lane carried its own twin of the
main kernels. The twin deviation quoted per run is the largest
single-round deviation between this PR's two copies; a row's reported
time is the median over rounds, so one disturbed round does not move it.
Both runs are shown; a row passes only if it is above 1x vs Stock in
both.

Fixtures: deterministic routed inputs with unit expert global scales,
balancedness 0.8; seeds 28104 / 28105 (H = 7168 rows) and 28110..28113
(GLM rows); large-batch rows use the same generator at M = 1000 / 2048 /
4096 / 8192. Measured on a build of this PR's content on `main`
`2d5b283d3ca2676c83fbfd746622b5c00c046044` whose
`csrc/alphamoe_nvfp4_sm100.cu` (sha256
`52fb6b7b3fce0352246a8d74a84ad40de0c75c8ac515a3cd09323140613548b6`)
differs from this head's file (sha256
`3385a5fa1784da5b20a58f21571d6bcf3290ec27545e2679aed10408c1831b93`) only
by two unreferenced preprocessor lines (an unused `#define` / `#undef`
pair, removed) and by a formatter pass on the Python host / test files
(AST-identical); all 93 device kernels of the two builds are SASS- and
resource-usage-identical on both parts (93/93 on GB300 and on B200); the
FlashInfer tests and the CUDA 12.9 CI-like run were executed on this
head itself. No timing re-run was made on this head.

**Hardware floor** per row: the 3 M <= 8 rows (`source_decode_m8`,
`glm_decode_m1`, `glm_decode_m8`) use the itemised latency floor = the
part's eager launch span (GB300 1.55 us, B200 1.63 us; applied per
launch analytically, not micro-benchmarked per launch item) x the number
of launches in the chain (5 / 2 / 3) + the row's byte floor (GB300 12.27
/ 5.90 / 42.03 us, B200 12.98 / 5.93 / 40.76 us); every other row uses
max(byte floor, FLOP floor), at the measured HBM read plateau of the
part (GB300 7202.5 GB/s, B200 7166.3 GB/s; bytes = W1 + W2 of the
experts actually touched by the fixture's top-k routing, plus E4M3 block
scales, plus activations in / out; FLOPs = 6 · M · k · H · I at the
measured `tcgen05` stream rate × SM count × busy clock). "Floor share" =
floor / this PR's time; it is a reporting column, not a pass criterion.

#### NVIDIA GB300 (sm_103a) — six-shape rows

| Shape | Route | Stock GPU sum (us) r1 / r2 | main GPU sum (us) r1 / r2
| This PR GPU sum (us) r1 / r2 | Speedup vs Stock r1 / r2 | Speedup vs
main r1 / r2 | Floor (us) | Floor share r1 / r2 | max abs diff vs Stock
|
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| M=8, H=7168, I=128, E=256, top-k=8, BM=8 | 9 | 40.01 / 40.52 | 38.77 /
38.72 | 31.38 / 31.34 | **1.2736x / 1.2915x** | 1.2353x / 1.2353x |
20.03 | 63.8 % / 63.9 % | 0.5 |
| M=128, H=7168, I=128, E=256, top-k=8, BM=16 | aligned entry (no route
id; single fused up_down kernel) | 116.47 / 116.60 | 102.06 / 101.99 |
102.02 / 101.90 | **1.1398x / 1.1444x** | 1.0003x / 1.0009x | 54.93 |
53.8 % / 53.9 % | 2 |
| M=1, H=6144, I=512, E=256, top-k=8, BM=8 | 1 | 24.86 / 24.35 | 19.58 /
19.65 | 19.58 / 19.67 | **1.2696x / 1.2380x** | 0.9996x / 0.9988x | 9.00
| 46.0 % / 45.8 % | 0 |
| M=8, H=6144, I=512, E=256, top-k=8, BM=8 | 9 | 73.77 / 73.74 | 74.22 /
73.95 | 71.90 / 71.68 | **1.0267x / 1.0285x** | 1.0322x / 1.0317x |
46.68 | 64.9 % / 65.1 % | 0 |
| M=128, H=6144, I=512, E=256, top-k=8, BM=8 | 19 | 224.09 / 224.34 |
231.76 / 231.54 | 215.03 / 215.21 | **1.0432x / 1.0432x** | 1.0778x /
1.0759x | 183.06 | 85.1 % / 85.1 % | 0 |
| M=512, H=6144, I=512, E=256, top-k=8, BM=8 | 18 | 242.10 / 242.06 |
262.89 / 262.82 | 233.95 / 234.03 | **1.0348x / 1.0341x** | 1.1237x /
1.1230x | 189.80 | 81.1 % / 81.1 % | 0 |

**Large batches (same metric, PDL-enabled Stock):**

| Shape | Route | Stock GPU sum (us) r1 / r2 | main GPU sum (us) r1 / r2
| This PR GPU sum (us) r1 / r2 | Speedup vs Stock r1 / r2 | Speedup vs
main r1 / r2 | Floor (us) | Floor share r1 / r2 | max abs diff vs Stock
|
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| M=1000, H=6144, I=512, E=256, top-k=8, BM=8 | 16 | 260.86 / 260.66 |
257.14 / 257.04 | 251.61 / 251.70 | **1.0371x / 1.0353x** | 1.0220x /
1.0212x | 190.87 | 75.9 % / 75.8 % | 0 |
| M=2048, H=6144, I=512, E=256, top-k=8, BM=8 | 16 | 303.73 / 303.19 |
286.94 / 286.72 | 282.79 / 282.63 | **1.0741x / 1.0726x** | 1.0146x /
1.0145x | 193.17 | 68.3 % / 68.3 % | 0 |
| M=4096, H=6144, I=512, E=256, top-k=8, BM=8 | 16 | 391.00 / 391.28 |
380.23 / 379.27 | 380.06 / 379.29 | **1.0285x / 1.0313x** | 1.0004x /
1.0000x | 197.67 | 52.0 % / 52.1 % | 0 |
| M=8192, H=6144, I=512, E=256, top-k=8, BM=8 | 16 | 618.97 / 619.18 |
576.23 / 576.53 | 576.77 / 576.65 | **1.0736x / 1.0740x** | 0.9991x /
0.9998x | 250.28 | 43.4 % / 43.4 % | 0 |

GB300: **10/10 rows above 1x vs Stock in both runs**; geomean(main /
this PR) over the 10 rows = **1.0481 / 1.0477**. A/A twin deviation of
this PR's copy: run 1 max 0.65 % on `glm_decode_m1` (the other 9 rows <=
0.61 %; on that row Stock's own twin deviated 0.85 % and the main lane's
twin 0.57 %); run 2 max 0.84 % on `source_batch_m128` (the other 9 rows
<= 0.41 %; on that row Stock's own twin deviated 0.41 % and the main
lane's twin 0.98 %). Tightest row vs Stock: `glm_decode_m8`, per-round
ratios run 1 1.0280, 1.0273, 1.0288, 1.0245, 1.0260, 1.0241; run 2
1.0255, 1.0312, 1.0274, 1.0234, 1.0297, 1.0295. Rows below 1x vs Stock
in either run: none. Rows below 1x vs main in either run (a shortfall
inside the row's own twin envelope passes the non-regression rule):
`glm_decode_m1` (0.9996 / 0.9988; shortfall 0.04 / 0.12 %; twin
deviation 0.65 / 0.41 %, envelope 0.65 % -> non-regression pass);
`glm_prefill_m4096` (1.0004 / 1.0000; shortfall 0.00 / 0.00 %; twin
deviation 0.11 / 0.16 %, envelope 0.16 % -> non-regression pass);
`glm_prefill_m8192` (0.9991 / 0.9998; shortfall 0.09 / 0.02 %; twin
deviation 0.16 / 0.19 %, envelope 0.19 % -> non-regression pass). Rows
failing the row gate or the non-regression rule: none.

#### NVIDIA B200 (sm_100a) — six-shape rows

| Shape | Route | Stock GPU sum (us) r1 / r2 | main GPU sum (us) r1 / r2
| This PR GPU sum (us) r1 / r2 | Speedup vs Stock r1 / r2 | Speedup vs
main r1 / r2 | Floor (us) | Floor share r1 / r2 | max abs diff vs Stock
|
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| M=8, H=7168, I=128, E=256, top-k=8, BM=8 | 9 | 43.75 / 43.74 | 40.44 /
40.48 | 36.42 / 36.43 | **1.2014x / 1.2010x** | 1.1103x / 1.1111x |
21.14 | 58.0 % / 58.0 % | 0.0002441 |
| M=128, H=7168, I=128, E=256, top-k=8, BM=16 | aligned entry (no route
id; single fused up_down kernel) | 120.46 / 120.62 | 107.62 / 107.98 |
107.95 / 108.05 | **1.1152x / 1.1170x** | 0.9970x / 0.9994x | 54.99 |
50.9 % / 50.9 % | 2 |
| M=1, H=6144, I=512, E=256, top-k=8, BM=8 | 1 | 25.11 / 25.14 | 20.57 /
20.66 | 20.53 / 20.58 | **1.2233x / 1.2226x** | 1.0020x / 1.0039x | 9.19
| 44.8 % / 44.7 % | 0 |
| M=8, H=6144, I=512, E=256, top-k=8, BM=8 | 9 | 73.91 / 73.50 | 78.02 /
78.14 | 72.91 / 72.88 | **1.0144x / 1.0091x** | 1.0700x / 1.0721x |
45.65 | 62.6 % / 62.6 % | 0.125 |
| M=128, H=6144, I=512, E=256, top-k=8, BM=8 | 19 | 228.86 / 228.78 |
228.82 / 228.78 | 225.91 / 225.94 | **1.0129x / 1.0126x** | 1.0129x /
1.0125x | 187.69 | 83.1 % / 83.1 % | 0 |
| M=512, H=6144, I=512, E=256, top-k=8, BM=8 | 18 | 245.07 / 245.25 |
252.60 / 253.06 | 244.26 / 244.69 | **1.0033x / 1.0022x** | 1.0341x /
1.0342x | 190.76 | 78.1 % / 78.0 % | 0 |

**Large batches (same metric, PDL-enabled Stock):**

| Shape | Route | Stock GPU sum (us) r1 / r2 | main GPU sum (us) r1 / r2
| This PR GPU sum (us) r1 / r2 | Speedup vs Stock r1 / r2 | Speedup vs
main r1 / r2 | Floor (us) | Floor share r1 / r2 | max abs diff vs Stock
|
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| M=1000, H=6144, I=512, E=256, top-k=8, BM=8 | 16 | 266.43 / 266.26 |
267.05 / 267.85 | 260.93 / 261.29 | **1.0207x / 1.0191x** | 1.0235x /
1.0251x | 191.84 | 73.5 % / 73.4 % | 0 |
| M=2048, H=6144, I=512, E=256, top-k=8, BM=8 | 16 | 309.54 / 308.24 |
301.36 / 301.92 | 295.79 / 295.21 | **1.0473x / 1.0443x** | 1.0188x /
1.0227x | 194.15 | 65.6 % / 65.8 % | 0 |
| M=4096, H=6144, I=512, E=256, top-k=8, BM=8 | 16 | 412.09 / 414.16 |
397.15 / 398.93 | 397.21 / 399.27 | **1.0376x / 1.0377x** | 0.9999x /
0.9991x | 198.67 | 50.0 % / 49.8 % | 0 |
| M=8192, H=6144, I=512, E=256, top-k=8, BM=8 | 16 | 682.35 / 693.41 |
651.13 / 657.88 | 651.27 / 657.93 | **1.0479x / 1.0539x** | 0.9998x /
0.9999x | 270.77 | 41.6 % / 41.2 % | 0 |

B200: **10/10 rows above 1x vs Stock in both runs**; geomean(main / this
PR) over the 10 rows = **1.0262 / 1.0274**. A/A twin deviation of this
PR's copy: run 1 max 0.92 % on `glm_decode_m1` (the other 9 rows <= 0.57
%; on that row Stock's own twin deviated 1.33 % and the main lane's twin
0.46 %); run 2 max 32.76 % on `glm_prefill_m4096` (the other 9 rows <=
0.92 %; on that row Stock's own twin deviated 36.60 % and the main
lane's twin 0.07 %). Tightest row vs Stock: `glm_batch_m512`, per-round
ratios run 1 1.0041, 1.0026, 1.0042, 1.0031, 1.0035, 1.0012; run 2
1.0028, 1.0013, 1.0020, 1.0038, 0.9998, 1.0024. Rows below 1x vs Stock
in either run: none. Rows below 1x vs main in either run (a shortfall
inside the row's own twin envelope passes the non-regression rule):
`source_batch_m128` (0.9970 / 0.9994; shortfall 0.30 / 0.06 %; twin
deviation 0.48 / 0.49 %, envelope 0.49 % -> non-regression pass);
`glm_prefill_m4096` (0.9999 / 0.9991; shortfall 0.01 / 0.09 %; twin
deviation 0.09 / 32.76 %, envelope 32.76 % -> non-regression pass);
`glm_prefill_m8192` (0.9998 / 0.9999; shortfall 0.02 / 0.01 %; twin
deviation 0.09 / 0.09 %, envelope 0.09 % -> non-regression pass). Rows
failing the row gate or the non-regression rule: none.

<details>
<summary>Measurement identity per run (GPU, driver, clocks, container,
arm sources)</summary>

| Arch / run | GPU (name, UUID) | Driver | Median busy SM clock during
the measured samples (MHz) | Container image (sha256 of the image file)
| Stock arm | main arm | This PR arm |
|---|---|---|---:|---|---|---|---|
| GB300 run 1 | NVIDIA GB300, `6a3d023a-4572-1145-8cf5-48627a71f3fc` |
580.159.03 | 2070 |
`ff910f2f900c58f8cfd9837ba7d4f98a6d755e62048f335e5c57fbdf5f6c1c00` |
trtllm-gen cubins `35cb99413a3ebce2e87a03fc04196e528e22c8d5` on `main`
`2d5b283d3ca2676c83fbfd746622b5c00c046044` | csrc
`5545845bd6841864e26d5a5cd86825eaaf41af5b72e21960181970d75d0c9d35` |
measured build csrc
`52fb6b7b3fce0352246a8d74a84ad40de0c75c8ac515a3cd09323140613548b6`; this
head's csrc
`3385a5fa1784da5b20a58f21571d6bcf3290ec27545e2679aed10408c1831b93`
(differs only by two unreferenced preprocessor lines (an unused
`#define` / `#undef` pair, removed) and by a formatter pass on the
Python host / test files (AST-identical); all 93 device kernels of the
two builds are SASS- and resource-usage-identical on both parts (93/93
on GB300 and on B200)) |
| GB300 run 2 | NVIDIA GB300, `3a31c974-a4f8-ab10-29e9-6463c45f0cdd` |
580.159.03 | 2070 | same | same | same | same |
| B200 run 1 | NVIDIA B200, `65cb3b9c-09e7-9429-187f-aef74634c32e` |
580.82.07 | 1965 |
`eb6812256b15ac860d43d371296f4a8f8810aac1b53cf7cf0e8c985f7ad16075` |
same | same | same |
| B200 run 2 | NVIDIA B200, `c502242e-3548-1a43-d781-9b437291017e` |
580.82.07 | 1965 | same | same | same | same |

Power / clock state: default (boost) clocks, no clock lock, power cap as
shipped (1400.00 W GB300 / 1000.00 W B200); the busy clock column is the
median of the per-sample SM clock readings taken after each measured
iteration.
</details>

### Numerics

- **GLM-geometry rows (H = 6144, I = 512; M = 1 / 8 / 128 / 512 / 1000 /
2048 / 4096 / 8192)**: output bitwise identical to Stock on 30 of the 32
(row, part, run) cells (8 rows x 2 parts x 2 runs); the exceptions are
`glm_decode_m8` on B200 run 1 and run 2 (max abs diff vs Stock 0.125 in
each). On that row (route 9) this PR's output is bitwise identical to
the merged-`main` kernel's output (0 of 49,152 elements differ), and
both differ from Stock on the same 3 of 49,152 elements, each by one
adjacent BF16 value (max |diff| 0.125, i.e. 0.125 BF16 ulp at the
output's maximum magnitude 166; 1 ordinal ulp per element) -- a
difference inherited from the merged-`main` kernel, within the FP4
tolerance (atol 1.0 / rtol 0.1). On GB300 this row is bitwise identical
to Stock in both runs. Every other GLM cell is bitwise identical to
Stock on both parts in both runs.
- **H = 7168 / I = 128 rows (M = 8 / 128)**: max |diff| vs Stock, run 1
/ run 2: `source_decode_m8` 0.5 / 0.5 (GB300) and 0.0002441 / 0.0002441
(B200); `source_batch_m128` 2 / 2 (GB300) and 2 / 2 (B200) -- i.e. <= 2
BF16 ulp measured at the output's maximum magnitude (max |diff| in units
of the BF16 ulp at |out|max: `source_decode_m8` 0.25 ulp on GB300 /
0.0001221 ulp on B200, `source_batch_m128` 1 / 1 ulp). Per element the
picture is the same as for the merged-`main` kernels: `source_decode_m8`
differs from Stock by at most 1 ordinal BF16 ulp (4 elements on GB300 /
2 on B200 of 57,344); `source_batch_m128` (served by the unchanged
aligned entry) has about 265k elements at 1 ordinal ulp, about 36k at 2
and 50,614 (GB300) / 49,807 (B200) near-zero cancellation elements above
2 ordinal ulp of 917,504 -- a histogram identical to the merged-`main`
kernels' own histogram vs Stock, because the general route's fp32 atomic
accumulation has no fixed order. This PR does not change that class; vs
the merged-`main` kernels this head differs by at most 4 (GB300) / 6
(B200) ordinal ulp on 35-41 elements.
- Every row is finite and within the FP4 tolerance (atol 1.0, rtol 0.1)
vs Stock in both runs. The 10 rows above on both parts, with these
tolerances, are the scope of the CAKE team's internal NVFP4 package
evaluation contract `eval_contract_alpha_moe_nvfp4_package.yaml` (not
part of this repository); its validation on this head: PASS (GB300) (a
static Stage-0 check of the contract file against the harness: schema
with the 10 rows, harness import and forbidden-import checks; not a GPU
run). The contract file is still marked draft pending ratification after
acceptance; only the stricter promotion profile, which requires a
ratified contract, reports that. Route-equivalence tests on this head:
`test_alphamoe_nvfp4_token_tile_route_matches_general[m1000]` checks the
small-row band of route 16 (the new `c500ag` up kernel) bitwise against
the general path and `[m4096]` covers the unchanged large band (`c500y`)
the same way; `tests/moe/test_alphamoe_nvfp4_selfroute.py` checks route
18 (M = 512) bitwise against the prepared route-12 path and route 19 (M
= 128) bitwise against the prepared route-10 path (accumulate on and
off, on the library fixture and on a skewed routing with more than 32
pairs for several experts); route 17 = route 12 = Stock bitwise comes
from the route-17 A/B dump compare, and the acceptance dump compares
hold routes 18 and 19 bitwise to the recorded merged-`main` chains and
to Stock. The source M = 8 route-9 selector
(`tests/moe/test_alphamoe_nvfp4_source_route.py`) is checked against the
generic path (<= 2 BF16 ulp at the generic output's maximum magnitude),
within the FP4 tolerance of the torch oracle, and bitwise deterministic
across calls; it is not bitwise against the generic path, whose
fp32-atomic accumulation order is run-to-run nondeterministic.
- **Route 18 (M = 512)**: output bitwise identical to the recorded
route-12 chain of merged `main`, to route 17 and to Stock on both parts
(`glm_batch_m512` output dumps were compared element by element against
the recorded route-12 chain (the merged-`main` kernels) and against
Stock in both acceptance runs on GB300 and on B200: 0 of 3,145,728
elements differ in every compare; the earlier route-18 A/B measurements
on both parts showed the same bitwise result);
`tests/moe/test_alphamoe_nvfp4_selfroute.py` checks route 18 bitwise
against the prepared route-12 path (this head's route-12 chain, whose
down kernel differs from merged `main` only by the barrier ids) on the
library fixture and on a skewed-routing fixture (several experts with
more than 32 routed pairs), because the in-kernel plan has a separate
code path for an expert's pairs beyond the first 32.
- **Route 19 (M = 128)**: output bitwise identical to the recorded
route-10 chain of merged `main` and to Stock on both parts
(`glm_batch_m128` output dumps were compared element by element against
the recorded route-10 chain (the merged-`main` kernels) and against
Stock in both acceptance runs on GB300 and on B200: 0 of 786,432
elements differ in every compare; the earlier route-19 A/B measurements
on both parts showed the same bitwise result);
`tests/moe/test_alphamoe_nvfp4_selfroute.py` checks route 19 bitwise
against the prepared route-10 path on the library fixture and on the
skewed-routing fixture (accumulate on and off).
- On these two rows the only further change is where the expert-major
token plan is built: inside the up kernel instead of a separate
alignment launch. The plan the up kernel publishes is the canonical one
the alignment launch produced, so the kernels after it are
byte-identical.
- Nothing in the arithmetic of any kernel changed: same NVFP4 / E4M3
block-scale recipe, same MMA shapes and K order, same compile flags, and
every replaced kernel keeps the accumulation and finalize order of the
kernel it replaces. The changes are barrier ids (the BM8 down kernels)
and one added `__syncthreads()` (`moe_align_block_size_kernel`, #6222),
pipeline depth and per-compute-capability kernel selection (the route-9
up kernel), how W2 is streamed (K-256 panels, route 17), where the
expert-major token plan is built (inside the up kernel for the M = 128
and M = 512 GLM chains), and where the activation scale factors are read
from (route 16).
- Exception (source-row route change) -- one row changes its summation:
the M = 8 / H = 7168 / I = 128 source row moves from the generic split-K
path (fp32 atomic accumulation, no fixed order, not run-to-run
deterministic) to the existing route-9 chain (BF16 per-route partials +
fixed-order finalize). On this row the output is therefore not bitwise
identical to the merged-`main` path (GB300: about 38 % of the 57,344
outputs differ, max abs diff vs `main` 1 (= 0.5 BF16 ulp at the output's
maximum magnitude); B200: about 38 % of the 57,344 outputs differ, max
abs diff vs `main` 2 (= 1 BF16 ulp at the output's maximum magnitude)).
Vs Stock it stays in the bound it already had: GB300 <= 2 BF16 ulp vs
Stock at the output's maximum magnitude (max abs diff 0.5 = 0.25 ulp
(both runs)); B200 <= 2 BF16 ulp vs Stock at the output's maximum
magnitude (max abs diff 0.0002441 = 0.0001221 ulp (both runs)); FP4
tolerance met, and two consecutive calls are bitwise identical
(`tests/moe/test_alphamoe_nvfp4_source_route.py` asserts route
selection, <= 2 BF16 ulp vs the generic path, FP4 tolerance vs the torch
oracle, and determinism; it does not assert bitwise equality with the
generic path because that path is itself nondeterministic).

### Validation on this head

- Native gate: PASS on GB300 and B200 — 30 package tests passed on each
part (`tests/moe/test_alphamoe_nvfp4_sm100.py`: 20, unchanged,
`tests/moe/test_alphamoe_nvfp4_selfroute.py`,
`tests/moe/test_alphamoe_nvfp4_source_route.py`: 4 + 6, new); the built
library's SASS compared kernel by kernel against the merged-`main`
library: 84 of 85 common kernels bit-identical (0 register-renaming-only
differences); the one differing common kernel is
`moe_align_block_size_kernel` (BAR.SYNC 9 -> 10, the PR #6222 fix, by
design); 8 added / 4 removed exactly as planned
(kernel_alpha_moe_nvfp4_up_token_tile_c500ag_nvfp4_u1_c500ag_up,
kernel_alpha_moe_nvfp4_up_workspace_prepacked_w1_c340sr_selfroute_nvfp4_u1_c340sr_up,
kernel_alpha_moe_nvfp4_up_workspace_prepacked_w1_m128_c336sr_selfroute_nvfp4_u1_c336sr_up,
kernel_alpha_moe_nvfp4_down_workspace_c358nd_k256panels_nvfp4_u1_c358nd_down,
kernel_alpha_moe_nvfp4_down_workspace_c358_preparedw2_evictfirst_nvfp4_u1_c358nb_down,
kernel_alpha_moe_nvfp4_down_c360_preparedw2_evictfirst_nvfp4_u1_c360b_down,
kernel_alpha_moe_nvfp4_down_workspace_m8_bf16_routes_persistent_v7fitz_nvfp4_u1_c407b_down,
kernel_alpha_moe_nvfp4_up_workspace_singleton_n8_prepacked_w1_nsplit64_preparedw1_inkernel_align_maskrank_nvfp4_u1_c416t_up
/
kernel_alpha_moe_nvfp4_down_c360_preparedw2_evictfirst_nvfp4_s12_c360_down,
kernel_alpha_moe_nvfp4_down_workspace_c358_preparedw2_evictfirst_nvfp4_s14_c358n_down,
kernel_alpha_moe_nvfp4_down_workspace_m8_bf16_routes_persistent_v7fitz_nvfp4_s11_c407_down,
kernel_alpha_moe_nvfp4_up_token_tile_c500ab_nvfp4_s13_c500ab_up); every
added kernel's SASS equals its captured cubin.
- compute-sanitizer **memcheck / synccheck / racecheck** on every
changed route reached by the measured rows, at representative token
counts (rows M = 512 / 1000 / 2048 / 128 / 8 (routes 18, 16, 16, 19, 9),
run on the measured build, whose device code is identical to this head
(93/93 kernels, SASS and resource usage); the source M = 8 route-9 row
was covered by an earlier sanitizer run on a build whose route-9 kernels
(`c416s` on GB300 / `c416t` on B200, `c407b`, `c402r9ns`) are
SASS-identical to this head (31 included launches, 0 errors / 0
hazards)) on both parts: **0 errors / 0 errors / 0 hazards**
(compute-sanitizer 2026.3.0.0: build 38855100 on the sm_103a part, build
38637409 from the cuda_sanitizer_api 13.4.57 archive on the sm_100a
part). Each run used `--dump-kernel-launches`, so the log carries one
launch record per instrumented kernel; the verdict counts error
*records*, and requires at least one unfiltered launch record naming
each kernel of the sanitized routes (26 included launches per tool on
each part: c500ag 6, c340sr 3, c336sr 3, c358nd 3, c360b 3 (the route-19
down kernel), c407b 3, route-9 up 3 (c416s on GB300 / c416t on B200),
c402r9ns finalize 2 (= 26); 0 error / hazard records) — a clean summary
line alone is not accepted as evidence.
- The route-12 down kernel `c358nb` (barrier-id change only; selected
for M = 512 only when the caller passes no K-256 sidecars) is not
launched by the sanitized rows and has no sanitizer launch record; it is
exercised by the prepared route-12 reference path of
`tests/moe/test_alphamoe_nvfp4_selfroute.py`.
- **CUDA 12.9 build** (the CI configuration that failed on an earlier
head of #4340): the package built from this head and passed `30` tests
in the FlashInfer CI image
`docker.io/flashinfer/flashinfer-ci-cu129:20260930-b1420f1` (digest
`sha256:38eea3ca97eb5a35ab02d45fe8bb4c25762371f88afbb478d319c680b8cf43b5
(index; linux/arm64
sha256:74ae1561b99ee93f51b9ffe6a8a8798f9d6491620bc0db7064711c51cce17235,
linux/amd64
sha256:fc00b288930d6e77ddae908646527c26469f4a330db59d646e4c2f807e0e6b0e)`,
torch `2.13.0+cu129`, nvcc `12.9.41 (Build
cuda_12.9.r12.9/compiler.35813241_0)`, arch list `10.3a` on GB300 /
`10.0a` on B200. The arch-list deviation from the FlashInfer CI
configuration (one of the five recorded): `FLASHINFER_CUDA_ARCH_LIST`
was set explicitly to the node's architecture, whereas FlashInfer CI
leaves it unset and lets the JIT target the visible GPU (the same target
on these nodes)). compute-sanitizer was not run inside the CUDA 12.9
build; that run deviates from the FlashInfer CI configuration in five
recorded ways (node-local tree copy, pytest flags, pinned arch list, no
memcheck, sqsh container runtime instead of docker). Sanitizer coverage
for this head is the compute-sanitizer 2026.3 gates in the previous
bullet (memcheck / synccheck / racecheck, 26 included launches per tool
on each part, 0 error / hazard records).
- Pre-commit hooks (ruff check + format, mypy, clang-format with the
AlphaMoE csrc units excluded): clean.
- Convergence status against the hardware floor (reporting only): GB300
not converged: neither at bound nor levers exhausted; rows below 90 % of
the floor (worse run): `source_decode_m8` (63.8 %), `source_batch_m128`
(53.8 %), `glm_decode_m1` (45.8 %), `glm_decode_m8` (64.9 %),
`glm_batch_m128` (85.1 %), `glm_batch_m512` (81.1 %), `glm_decode_m1000`
(75.8 %), `glm_prefill_m2048` (68.3 %), `glm_prefill_m4096` (52.0 %),
`glm_prefill_m8192` (43.4 %); B200 not converged: neither at bound nor
levers exhausted; rows below 90 % of the floor (worse run):
`source_decode_m8` (58.0 %), `source_batch_m128` (50.9 %),
`glm_decode_m1` (44.7 %), `glm_decode_m8` (62.6 %), `glm_batch_m128`
(83.1 %), `glm_batch_m512` (78.0 %), `glm_decode_m1000` (73.4 %),
`glm_prefill_m2048` (65.6 %), `glm_prefill_m4096` (49.8 %),
`glm_prefill_m8192` (41.2 %).

### Baselines and their source PRs

| baseline | origin | files | used for |
|---|---|---|---|
| `trtllm_fp4_block_scale_routed_moe` (trtllm-gen NVFP4 fused MoE, cubin
artifacts `35cb99413a3ebce2e87a03fc04196e528e22c8d5`) |
flashinfer-ai/flashinfer `main` @
`2d5b283d3ca2676c83fbfd746622b5c00c046044` (2026-10-13) |
`flashinfer/fused_moe/core.py`, `csrc/trtllm_fused_moe_runner.cu`,
`csrc/trtllm_fused_moe_kernel_launcher.cu`,
`csrc/trtllm_fused_moe_routing_binding.cu` | Stock arm, all rows, both
parts |
| merged AlphaMoE NVFP4 package (PR #4340 head `19056357` + #5930) |
flashinfer-ai/flashinfer `main` @
`2d5b283d3ca2676c83fbfd746622b5c00c046044`
(`csrc/alphamoe_nvfp4_sm100.cu` sha256
`5545845bd6841864e26d5a5cd86825eaaf41af5b72e21960181970d75d0c9d35`) |
`csrc/alphamoe_nvfp4_sm100.cu`,
`flashinfer/fused_moe/alphamoe_nvfp4_sm100.py` | main arm
(non-regression reference), all rows, both parts |
| `moe_align_block_size_kernel` barrier fix |
flashinfer-ai/flashinfer#6222 by @builtin-pb (Bo Peng), commit
`4d03fd19092e33080a92b8c67b1c57d320461dec` |
`csrc/alphamoe_nvfp4_sm100.cu` | adopted verbatim in this PR (see "What
changed") |

## 🔍 Related Issues

Includes the fix proposed in #6222 (credit: @builtin-pb).

## 🚀 Pull Request Checklist

- [x] I have read the [contributing
guidelines](https://github.com/flashinfer-ai/flashinfer/blob/main/CONTRIBUTING.md)
- [x] Pre-commit hooks pass on the changed files
- [x] Tests added: `tests/moe/test_alphamoe_nvfp4_selfroute.py` (4
cases, new: routes 18 (M = 512) and 19 (M = 128) equal the prepared
route-12 / route-10 paths bit for bit in both accumulate forms, on the
library fixture and on a skewed routing with more than 32 pairs per
expert) and `tests/moe/test_alphamoe_nvfp4_source_route.py` (6 cases,
new: 2 seeds at source M = 8 -- route 9 is selected, the output is
finite and within the FP4 tolerance (atol 1.0 / rtol 0.1) of the torch
oracle, at most 2 BF16 ulp from the generic path, and deterministic run
to run; plus M = 1 / 4 / 16 / 128 keep the generic route). The existing
`tests/moe/test_alphamoe_nvfp4_sm100.py` (20 cases) is unchanged and
passes -- 30 cases in total on GB300 and B200
- [x] Documentation: unchanged

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- cake-shared-references:start -->
## References

The shared reference corpus for CAKE kernel development includes the
following projects, documentation, and existing CAKE work:

- **GPU programming and instructions:** [NVIDIA CUDA Programming
Guide](https://docs.nvidia.com/cuda/cuda-programming-guide/index.html),
[NVIDIA PTX
ISA](https://docs.nvidia.com/cuda/parallel-thread-execution/), and
gau-nernst's [tcgen05 tutorial](https://gau-nernst.github.io/tcgen05/)
and [CUDA kernel examples](https://github.com/gau-nernst/learn-cuda).
- **Kernel programming libraries and compilers:** [NVIDIA CUTLASS /
CuTe](https://github.com/NVIDIA/cutlass),
[Triton](https://github.com/triton-lang/triton),
[TileLang](https://github.com/tile-ai/tilelang), [NVIDIA cuTile
Python](https://github.com/NVIDIA/cutile-python), and
[ThunderKittens](https://github.com/HazyResearch/ThunderKittens)
([ThunderKittens 2.0
techniques](https://hazyresearch.stanford.edu/blog/2026-02-19-tk-2)).
- **Attention and inference:** [FlashAttention (including Hopper and
CuTe implementations)](https://github.com/Dao-AILab/flash-attention),
[FlashInfer, including its TRT-LLM kernel
integration](https://github.com/flashinfer-ai/flashinfer), [Flash Linear
Attention](https://github.com/fla-org/flash-linear-attention),
[SageAttention](https://github.com/thu-ml/SageAttention),
[FlashAttention-FP4](https://github.com/hao-ai-lab/flash-attention-fp4),
and [FastVideo](https://github.com/hao-ai-lab/FastVideo).
- **GEMM and MoE:** [DeepGEMM](https://github.com/deepseek-ai/DeepGEMM),
[SonicMoE](https://github.com/Dao-AILab/sonic-moe),
[Alpha-MoE](https://github.com/Aleph-Alpha/Alpha-MoE), and [Mixture of
Kittens](https://github.com/cursor/mixture-of-kittens).
- **Clustering and nearest-neighbor kernels:** [Flash
K-Means](https://github.com/svg-project/flash-kmeans) and
[FlashLib](https://github.com/FlashML-org/flashlib).
- **Existing CAKE implementations and PRs:** [CAKE-generated kernel
progress tracker and PR index
(#4254)](https://github.com/flashinfer-ai/flashinfer/issues/4254).

These are corpus-level references. PR-specific implementation details,
changes, and benchmark references are documented above.
<!-- cake-shared-references:end -->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added optimized NVFP4 MoE execution for selected workloads, including
a small-token configuration and two larger-token configurations.
* The optimized paths are used only when the required input data and
alignment conditions are met; otherwise, execution falls back to the
general path.
* Added validation for output accuracy and repeatability across
supported configurations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Bo Peng <builtin.pb@gmail.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [7b2438e](https://github.com/flashinfer-ai/flashinfer/commit/7b2438ec309a9b1b244dbef8a1260073e59a913a)

- **作者**: Benjamin Chislett
- **时间**: 2026-10-15T16:49:55Z
- **提交信息**: feat(allreduce): Add support for Static FP8 Output Quant in CUTEDSL MNNVL AR (#5533)

## 📌 Description

This PR adds support for FP8 output quant fusion in CUTEDSL MNNVL AR,
significantly improving performance when the subsequent op is a static
FP8 quant op.

## 🔍 Related Issues

https://github.com/flashinfer-ai/flashinfer/issues/2364 -- this PR only
adds static FP8, not dynamic FP8

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

Apologies for slop. Most of the implementation is codex-generated. I'm
not too familiar with FI, but the code looks good enough to my eye.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added static E4M3 FP8 normalized-output support for supported
all-reduce fusion patterns in the reference MNNVL CuTe DSL backend.
* FP8 outputs use a supplied scale and can optionally include a BF16
copy of the normalized result. Communication and residual outputs remain
BF16.
* Scale values can be updated between CUDA Graph replays; per-token
scale estimation is not supported.
* **Documentation**
* Clarified output dtype options, scale requirements, pattern behavior,
and BF16 output requirements.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Benjamin Chislett <bchislett@nvidia.com>
Co-authored-by: Vincent Tombari <Vinnie6167@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-10-16
**监控日期**: 2026-10-15
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4610
- **最后更新**: 2026-10-15T15:14:43Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 1
- **主要提交者**: William Lin

## AI分析总结

## FastVideo 昨日提交分析

### 1. 主要更新类型
本次提交以**项目维护与社区治理**为主，涉及 CI 流程调整、文档/页面新增以及开发工具链清理，属于非核心功能层面的工程改进。

---

### 2. 关键变更点及与项目方向的关系

- **停止自动标记 stale (#1964)**：移除了自动将 issue 和 PR 标记为 "stale" 的 CI 机制。这说明项目管理团队意识到自动关闭流程可能误伤有价值的讨论，尤其是 FastVideo 作为一个活跃的开源视频生成项目，社区贡献量较大，人工审核优于机械清理。

- **新增公开联系页面 (#1959)**：为项目添加了公开的联系方式页面，强化了社区沟通渠道。这与 README 中展示的多渠道文档体系（Documentation、Cookbook、Quick Start、Dev Meeting）一脉相承，体现了项目对用户友好性和社区透明度的持续投入。

- **移除过时的 Agent 技能 (#1963)**：清理了 "add-model" 和 "decompose-pipeline-pr" 两个 agent 技能。这暗示项目可能在重新审视其 AI 辅助开发流程，移除不再适用或维护成本过高的自动化工具。

---

### 3. 对项目的影响和潜在意义

- **社区健康度提升**：取消 stale 自动标记避免了误关活跃讨论，有助于留住贡献者，降低社区参与门槛。这对于一个增长中的开源项目至关重要。

- **沟通渠道完善**：公开联系页为商业合作、学术合作和用户反馈提供了正式入口，有助于项目生态扩展。

- **工具链瘦身**：移除 agent 技能减少了维护负担，也暗示项目在开发自动化方面进行了反思或方向调整，可能后续会有更完善的工具替代。

---

### 4. 值得关注的技术点

- 这批提交虽然体量小，但反映了项目在**"从快速开发转向精细化运营"**的阶段过渡。FastVideo 此前以快速迭代核心推理加速能力著称，现在开始关注社区管理和开发者体验。
- Agent 技能的移除值得关注其 commit 内容中的具体原因——如果是与主流 CI/CD 工具链冲突或与新的开发规范不一致，则可能预示后续会有新的自动化方案落地。

---

### 5. 对项目发展的综合影响

基于 README 可知，FastVideo 是一个面向视频生成模型推理加速的框架，拥有完整的文档体系、Cookbook 教程和周度开发会议，社区活跃度较高。本次三笔提交虽然不涉及核心推理性能或模型支持，但它们体现了项目在**基础设施和社区治理上的成熟化**：减少自动化误伤、优化沟通渠道、清理冗余工具。这些"隐性投资"对于吸引更多高质量贡献者、维持长期社区活力具有重要意义。整体来看，项目正从"功能驱动"阶段自然过渡到"生态与社区并重"的健康发展阶段。

## 详细提交记录

### [ba371e3](https://github.com/hao-ai-lab/FastVideo/commit/ba371e33ed080e51f1884ae166baf7c4447a66fe)

- **作者**: William Lin
- **时间**: 2026-10-15T08:05:48Z
- **提交信息**: [ci] Stop automatically marking issues and PRs stale (#1964)

### [06c8c5f](https://github.com/hao-ai-lab/FastVideo/commit/06c8c5f4b898d07c10a0e53deb6475f571685a79)

- **作者**: William Lin
- **时间**: 2026-10-15T07:26:44Z
- **提交信息**: [docs] Add public contact page (#1959)

### [c535797](https://github.com/hao-ai-lab/FastVideo/commit/c535797e3d1f502f9b13470618ac970ee40061aa)

- **作者**: William Lin
- **时间**: 2026-10-15T07:10:49Z
- **提交信息**: [skill] Remove the add-model and decompose-pipeline-pr agent skills (#1963)

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-10-16
**监控日期**: 2026-10-15
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34728
- **最后更新**: 2026-10-15T20:06:27Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 3
- **主要提交者**: Akshan Krithick, Jingya HUANG, Sayak Paul

## AI分析总结

# huggingface/diffusers 昨日提交分析

## 1. 主要更新类型
- **功能新增**：Qwen-Image-2.1 模块化流水线（含 Turbo 变体）及张量并行（TP）支持
- **重构**：移除 Qwen Image 中冗余的 Neuron RoPE 路径，简化设备适配逻辑
- **CI/基础设施**：大量 GitHub Actions 依赖版本升级（涉及 17 个组件）

## 2. 关键变更点及与项目方向的关系

- **模块化流水线扩展**：为 Qwen-Image-2.1 新增模块化流水线，并拆分出 Turbo 块集、从文本编码器中移除 guider，延续了 diffusers 推行的"模块化、可组合"架构方向，让用户能更灵活地组装和定制生成流程。

- **张量并行（TP）支持**：在 Qwen-Image-2.1 上实现张量并行计划，已在 Neuron 上验证。这反映了项目对**多设备、大规模推理部署**的持续投入，尤其是在 AWS Neuron（Trainium/Inferentia）等非 NVIDIA 加速器上的可移植性。

- **Neuron RoPE 简化**：Neuron 现已原生支持复数张量，因此删除了 `apply_rotary_emb_qwen_neuron`、`ROPE_PER_DEVICE` 等特殊分支，所有设备统一使用默认复数 RoPE。这是典型的**"硬件成熟后消除软件兼容层"**重构，降低了维护成本。

- **CI 生态升级**：actions/checkout 升至 v7、upload-artifact 升至 v7、download-artifact 升至 v8、labeler 升至 v7 等，确保构建、测试、文档生成和 PyPI 发布流水线的安全性与稳定性。

## 3. 对项目的影响和潜在意义

- **模型覆盖更广**：Qwen-Image-2.1 成为 diffusers 中功能完整的模型家族成员（模块化流水线 + TP + Turbo），有助于吸引更多来自阿里生态的用户。
- **硬件泛化能力增强**：TP 支持在 Neuron 上验证，意味着该模型可在 AWS 芯片上高效推理，强化了 diffusers 作为跨硬件推理框架的定位。
- **维护负担降低**：合并 Neuron 特殊 RoPE 路径后，后续模型维护和代码审查更简单，减少潜在 bug 面。
- **工程质量提升**：CI 依赖大版本升级带来安全性补丁和新功能，降低供应链风险。

## 4. 值得关注的技术点

- **模块化流水线设计模式**：通过测试文件中区分标准版和 Turbo 版流水线，体现了如何优雅处理同一模型的不同推理变体。
- **`torch.accelerator.device_count()` 的使用**：TP 实现中采用 PyTorch 抽象层获取设备数，而非硬编码 CUDA API，提升了跨后端兼容性。
- **RoPE 统一化**：硬件原生支持复数运算后，软件层特殊处理可安全移除——这个模式会随其他硬件成熟而重复出现。
- **TensorParallelNeuronTesterMixin**：专门为 Neuron 环境抽象的 TP 测试混入类，为后续其他模型的 TP 测试提供了可复用的范式。

## 5. 对项目发展的整体影响

结合 README 中体现的 Apache 2.0 开源定位和 HuggingFace 生态整合目标，这批提交呈现出三个清晰信号：一是持续深耕**模块化架构**，使 pipeline 组件化程度更高、用户定制空间更大；二是积极拥抱**多硬件生态**，从 NVIDIA 扩展到 Neuron/TPU，契合行业端侧和专用芯片多样化趋势；三是通过及时的基础设施维护保持工程健康度。这些工作共同支撑 diffusers 从单纯的"模型实现库"向"生产级推理框架"演进。

## 详细提交记录

### [7ecb1e1](https://github.com/huggingface/diffusers/commit/7ecb1e1b4fe500be7fb7381a7bb79a24d7fa3941)

- **作者**: Sayak Paul
- **时间**: 2026-10-15T16:30:50Z
- **提交信息**: Flux3 image (#15046)

* Bump the actions group with 17 updates (#12)

Bumps the actions group with 17 updates:

| Package | From | To |
| --- | --- | --- |
| [actions/checkout](https://github.com/actions/checkout) | `6` | `7` |
| [actions/upload-artifact](https://github.com/actions/upload-artifact) | `4.6.2` | `7.0.1` |
| [docker/setup-buildx-action](https://github.com/docker/setup-buildx-action) | `3.12.0` | `4.2.0` |
| [docker/login-action](https://github.com/docker/login-action) | `3.7.0` | `4.6.0` |
| [docker/build-push-action](https://github.com/docker/build-push-action) | `6.19.2` | `7.3.0` |
| [huggingface/doc-builder/.github/workflows/build_main_documentation.yml](https://github.com/huggingface/doc-builder) | `e60a538eea9817ab312196d0d233604b01697265` | `af49b8dc3859c3d80c7220c8c0ba146431132e49` |
| [actions/setup-python](https://github.com/actions/setup-python) | `5.6.0` | `7.0.0` |
| [huggingface/doc-builder/.github/workflows/build_pr_documentation.yml](https://github.com/huggingface/doc-builder) | `e60a538eea9817ab312196d0d233604b01697265` | `af49b8dc3859c3d80c7220c8c0ba146431132e49` |
| [anthropics/claude-code-action](https://github.com/anthropics/claude-code-action) | `1.0.155` | `1.0.193` |
| [huggingface/security-workflows/.github/workflows/codeql-reusable.yml](https://github.com/huggingface/security-workflows) | `1.1.0` | `1.2.0` |
| [actions/download-artifact](https://github.com/actions/download-artifact) | `4.3.0` | `8.0.1` |
| [actions/labeler](https://github.com/actions/labeler) | `5.0.0` | `7.0.0` |
| [pypa/gh-action-pypi-publish](https://github.com/pypa/gh-action-pypi-publish) | `1.13.0` | `1.14.2` |
| [huggingface/tailscale-action](https://github.com/huggingface/tailscale-action) | `7d53c9737e53934c30290b5524d1c9b4a7c98c8a` | `07d36e4c3b68707bd3fe070dbb96f03f993a6efd` |
| [trufflesecurity/trufflehog](https://github.com/trufflesecurity/trufflehog) | `3.94.2` | `3.97.0` |
| [crate-ci/typos](https://github.com/crate-ci/typos) | `1.42.1` | `1.49.0` |
| [huggingface/doc-builder/.github/workflows/upload_pr_documentation.yml](https://github.com/huggingface/doc-builder) | `9ad2de8582b56c017cb530c1165116d40433f1c6` | `af49b8dc3859c3d80c7220c8c0ba146431132e49` |


Updates `actions/checkout` from 6 to 7
- [Release notes](https://github.com/actions/checkout/releases)
- [Commits](https://github.com/actions/checkout/compare/v6...v7)

Updates `actions/upload-artifact` from 4.6.2 to 7.0.1
- [Release notes](https://github.com/actions/upload-artifact/releases)
- [Commits](https://github.com/actions/upload-artifact/compare/v4.6.2...v7.0.1)

Updates `docker/setup-buildx-action` from 3.12.0 to 4.2.0
- [Release notes](https://github.com/docker/setup-buildx-action/releases)
- [Commits](https://github.com/docker/setup-buildx-action/compare/8d2750c68a42422c14e847fe6c8ac0403b4cbd6f...bb05f3f5519dd87d3ba754cc423b652a5edd6d2c)

Updates `docker/login-action` from 3.7.0 to 4.6.0
- [Release notes](https://github.com/docker/login-action/releases)
- [Commits](https://github.com/docker/login-action/compare/c94ce9fb468520275223c153574b00df6fe4bcc9...dbcb813823bdd20940b903addbd779551569679f)

Updates `docker/build-push-action` from 6.19.2 to 7.3.0
- [Release notes](https://github.com/docker/build-push-action/releases)
- [Commits](https://github.com/docker/build-push-action/compare/10e90e3645eae34f1e60eeb005ba3a3d33f178e8...53b7df96c91f9c12dcc8a07bcb9ccacbed38856a)

Updates `huggingface/doc-builder/.github/workflows/build_main_documentation.yml` from e60a538eea9817ab312196d0d233604b01697265 to af49b8dc3859c3d80c7220c8c0ba146431132e49
- [Release notes](https://github.com/huggingface/doc-builder/releases)
- [Commits](https://github.com/huggingface/doc-builder/compare/e60a538eea9817ab312196d0d233604b01697265...af49b8dc3859c3d80c7220c8c0ba146431132e49)

Updates `actions/setup-python` from 5.6.0 to 7.0.0
- [Release notes](https://github.com/actions/setup-python/releases)
- [Commits](https://github.com/actions/setup-python/compare/v5.6.0...v7)

Updates `huggingface/doc-builder/.github/workflows/build_pr_documentation.yml` from e60a538eea9817ab312196d0d233604b01697265 to af49b8dc3859c3d80c7220c8c0ba146431132e49
- [Release notes](https://github.com/huggingface/doc-builder/releases)
- [Commits](https://github.com/huggingface/doc-builder/compare/e60a538eea9817ab312196d0d233604b01697265...af49b8dc3859c3d80c7220c8c0ba146431132e49)

Updates `anthropics/claude-code-action` from 1.0.155 to 1.0.193
- [Release notes](https://github.com/anthropics/claude-code-action/releases)
- [Commits](https://github.com/anthropics/claude-code-action/compare/80b31826338489861333dc17217865dfe8085cdc...9d7150bc8a3dae8149739a88019d192b579ad90c)

Updates `huggingface/security-workflows/.github/workflows/codeql-reusable.yml` from 1.1.0 to 1.2.0
- [Release notes](https://github.com/huggingface/security-workflows/releases)
- [Commits](https://github.com/huggingface/security-workflows/compare/dc6ca34688e6876c2dd18750719b44d177586c17...e0d40aaf3c566a5e820787840453f45f909e337f)

Updates `actions/download-artifact` from 4.3.0 to 8.0.1
- [Release notes](https://github.com/actions/download-artifact/releases)
- [Commits](https://github.com/actions/download-artifact/compare/v4.3.0...3e5f45b2cfb9172054b4087a40e8e0b5a5461e7c)

Updates `actions/labeler` from 5.0.0 to 7.0.0
- [Release notes](https://github.com/actions/labeler/releases)
- [Commits](https://github.com/actions/labeler/compare/8558fd74291d67161a8a78ce36a881fa63b766a9...bf12e9b00b37c5c0ca2b87b79b2daf7891dbda13)

Updates `pypa/gh-action-pypi-publish` from 1.13.0 to 1.14.2
- [Release notes](https://github.com/pypa/gh-action-pypi-publish/releases)
- [Commits](https://github.com/pypa/gh-action-pypi-publish/compare/ed0c53931b1dc9bd32cbe73a98c7f6766f8a527e...dc37677b2e1c63e2034f94d8a5b11f265b73ba33)

Updates `huggingface/tailscale-action` from 7d53c9737e53934c30290b5524d1c9b4a7c98c8a to 07d36e4c3b68707bd3fe070dbb96f03f993a6efd
- [Release notes](https://github.com/huggingface/tailscale-action/releases)
- [Commits](https://github.com/huggingface/tailscale-action/compare/7d53c9737e53934c30290b5524d1c9b4a7c98c8a...07d36e4c3b68707bd3fe070dbb96f03f993a6efd)

Updates `trufflesecurity/trufflehog` from 3.94.2 to 3.97.0
- [Release notes](https://github.com/trufflesecurity/trufflehog/releases)
- [Commits](https://github.com/trufflesecurity/trufflehog/compare/6bd2d14f7a4bc1e569fa3550efa7ec632a4fa67b...bcfcf73aaf4759d4dadc2783177c245a02792318)

Updates `crate-ci/typos` from 1.42.1 to 1.49.0
- [Release notes](https://github.com/crate-ci/typos/releases)
- [Changelog](https://github.com/crate-ci/typos/blob/master/CHANGELOG.md)
- [Commits](https://github.com/crate-ci/typos/compare/65120634e79d8374d1aa2f27e54baa0c364fff5a...8a48f81b6c64dcfea44b3633223084c4be58ac5f)

Updates `huggingface/doc-builder/.github/workflows/upload_pr_documentation.yml` from 9ad2de8582b56c017cb530c1165116d40433f1c6 to af49b8dc3859c3d80c7220c8c0ba146431132e49
- [Release notes](https://github.com/huggingface/doc-builder/releases)
- [Commits](https://github.com/huggingface/doc-builder/compare/9ad2de8582b56c017cb530c1165116d40433f1c6...af49b8dc3859c3d80c7220c8c0ba146431132e49)

---
updated-dependencies:
- dependency-name: actions/checkout
  dependency-version: '7'
  dependency-type: direct:production
  update-type: version-update:semver-major
  dependency-group: actions
- dependency-name: actions/upload-artifact
  dependency-version: 7.0.1
  dependency-type: direct:production
  update-type: version-update:semver-major
  dependency-group: actions
- dependency-name: docker/setup-buildx-action
  dependency-version: 4.2.0
  dependency-type: direct:production
  update-type: version-update:semver-major
  dependency-group: actions
- dependency-name: docker/login-action
  dependency-version: 4.6.0
  dependency-type: direct:production
  update-type: version-update:semver-major
  dependency-group: actions
- dependency-name: docker/build-push-action
  dependency-version: 7.3.0
  dependency-type: direct:production
  update-type: version-update:semver-major
  dependency-group: actions
- dependency-name: huggingface/doc-builder/.github/workflows/build_main_documentation.yml
  dependency-version: af49b8dc3859c3d80c7220c8c0ba146431132e49
  dependency-type: direct:production
  dependency-group: actions
- dependency-name: actions/setup-python
  dependency-version: 7.0.0
  dependency-type: direct:production
  update-type: version-update:semver-major
  dependency-group: actions
- dependency-name: huggingface/doc-builder/.github/workflows/build_pr_documentation.yml
  dependency-version: af49b8dc3859c3d80c7220c8c0ba146431132e49
  dependency-type: direct:production
  dependency-group: actions
- dependency-name: anthropics/claude-code-action
  dependency-version: 1.0.193
  dependency-type: direct:production
  update-type: version-update:semver-patch
  dependency-group: actions
- dependency-name: huggingface/security-workflows/.github/workflows/codeql-reusable.yml
  dependency-version: 1.2.0
  dependency-type: direct:production
  update-type: version-update:semver-minor
  dependency-group: actions
- dependency-name: actions/download-artifact
  dependency-version: 8.0.1
  dependency-type: direct:production
  update-type: version-update:semver-major
  dependency-group: actions
- dependency-name: actions/labeler
  dependency-version: 7.0.0
  dependency-type: direct:production
  update-type: version-update:semver-major
  dependency-group: actions
- dependency-name: pypa/gh-action-pypi-publish
  dependency-version: 1.14.2
  dependency-type: direct:production
  update-type: version-update:semver-minor
  dependency-group: actions
- dependency-name: huggingface/tailscale-action
  dependency-version: 07d36e4c3b68707bd3fe070dbb96f03f993a6efd
  dependency-type: direct:production
  dependency-group: actions
- dependency-name: trufflesecurity/trufflehog
  dependency-version: 3.97.0
  dependency-type: direct:production
  update-type: version-update:semver-minor
  dependency-group: actions
- dependency-name: crate-ci/typos
  dependency-version: 1.49.0
  dependency-type: direct:production
  update-type: version-update:semver-minor
  dependency-group: actions
- dependency-name: huggingface/doc-builder/.github/workflows/upload_pr_documentation.yml
  dependency-version: af49b8dc3859c3d80c7220c8c0ba146431132e49
  dependency-type: direct:production
  dependency-group: actions
...

Signed-off-by: dependabot[bot] <support@github.com>
Co-authored-by: dependabot[bot] <49699333+dependabot[bot]@users.noreply.github.com>

* Scope GITHUB_TOKEN permissions per job (#16)

A job with no `permissions:` block inherits whatever the repository
hands out. Each block added here grants what that job's own steps
need and nothing more.

Co-authored-by: hf-security-analysis[bot] <265538906+hf-security-analysis[bot]@users.noreply.github.com>

* Pin GitHub Actions to commit SHAs (#17)

A tag is mutable: whoever controls the action's repository can move
`v4` to different code, and the next run picks it up with no diff to
review. Pinning to the commit SHA freezes the code that runs today.

Co-authored-by: hf-security-analysis[bot] <265538906+hf-security-analysis[bot]@users.noreply.github.com>

* Bump doc-builder workflow pin (#22)

* Bump doc-builder pin to 9fc8a41 in build_documentation.yml

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

* Bump doc-builder pin to 9fc8a41 in build_pr_documentation.yml

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

* Bump doc-builder pin to 9fc8a41 in upload_pr_documentation.yml

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

---------

Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>

* Add FLUX.3 image: Flux3Transformer2DModel and modular text-to-image / image-to-image pipeline

Adds the FLUX.3 image transformer, the modular pipeline (text-to-image and image-to-image with one
prompt per call and one or more reference images), Flux3ImageProcessor, the converter for BFL's
model package, tests and docs. Verified against BFL's reference on the real checkpoint
(integration-notes/parity_bf16.py, temporary folder).

Co-Authored-By: Claude Fable 5.1 <noreply@anthropic.com>

* integration-notes: ship the knight example image with the doc examples

Co-Authored-By: Claude Fable 5.1 <noreply@anthropic.com>

* integration-notes: drop the tokenizer config workaround (not needed with transformers 5.x)

Co-Authored-By: Claude Fable 5.1 <noreply@anthropic.com>

* Address review: rename the mode channel dict and the final norm, name the reference workflow
image_conditioned, document the guidance scale

Co-Authored-By: Claude Fable 5.1 <noreply@anthropic.com>

* Add the step-distilled FLUX.3 image model (flow map)

- transformer: `flow_map` config and `target_timestep_embedder`; forward takes
  `target_timestep` (the timestep each step jumps to), added to the modulation
  of every mode and the final layer
- convert script: map `ref_time_in.*` and read `flow_map` from the package config
- modular: dedicated `Flux3Distilled*` blocks (text encoder, text input, text
  RoPE inputs, denoiser) with no guider and no negative prompt, 16 steps by
  default; `Flux3DistilledAutoBlocks` and `Flux3DistilledModularPipeline`
- tests for the flow-map transformer path and the distilled modular pipeline
- docs: step-distilled section and autodoc entries

Co-Authored-By: Claude Fable 5.1 <noreply@anthropic.com>

* Add the step-distilled examples script

Same four cases as flux3_examples.py, run against the distilled Hub repo.

Co-Authored-By: Claude Fable 5.1 <noreply@anthropic.com>

* feat: add a single file support in Flux3 image. (#32)

* Warn about the denoiser input fields that are not passed to the transformer

Co-Authored-By: Claude Fable 5.1 <noreply@anthropic.com>

* Document reproducible generation with user-provided latents

Co-Authored-By: Claude Fable 5.1 <noreply@anthropic.com>

* Run the QK norm and RoPE in fp32 with a single cast back, matching the BFL implementation

Co-Authored-By: Claude Fable 5.1 <noreply@anthropic.com>

* parity script: run against the Hub repos and print the imported diffusers source

Co-Authored-By: Claude Fable 5.1 <noreply@anthropic.com>

* Wrap a forward docstring line for the doc-builder style check

Co-Authored-By: Claude Fable 5.1 <noreply@anthropic.com>

* support lora loading (including ostris) in flux3 image pipeline. (#25)

* feat: support loading and performing inference with single-file formatted FP8 and NVFP4 checkpoints (#24)

* feat: support loading siungle file format checkpoints including quants.

* remove updates.patch

* remove fluff.

* feat: add a single file support in Flux3 image.

* bfl prefix

* version guard.

* prpoagate changes.

* add tests

* doc mods and remove integration notes

* remove script for quant

---------

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

* add LoRA training for Flux 3 image small

* tests: clarify FLUX3_TINY_REPO comment

The tiny repo is uploaded to hf-internal-testing and the env var is a
local-dev escape hatch, not a pre-PR TODO.

* examples/flux3: drop unused args and dead class

Remove the text-encoder weight-decay arg from both trainers (neither
trains the text encoder) and, from the img2img trainer, the
prior-preservation leftovers (--class_data_dir, --sample_batch_size,
PromptDataset) that it never uses.

* bump yarn example rank to 32 in flux3 small readme

* Document <ref_image_n> references and layout prompts for FLUX.3

Matches the prompt grammar in BFL's reference inference code (bfl-hf-flux3-confidential#3): references are addressed as <ref_image_n> in the order passed to image, and regions can be placed with a trailing JSON list of id / bbox / desc (from / src_bbox / tgt_bbox when editing).

* examples/flux3: set klein model id, document ref image prompts, clean leftover refs

* point flux3 image docs at the klein release model ids

* fix: TestFlux3DistilledModularPipelineWorkflow::test_workflow_defaults test (#35)

* fix checkpoint ids in the flux3 docs. (#38)

* [docs] update pipe loading with vae fp32 dtype (#39)

* update pipe loading with vae fp32 dtype

* updating `load_componenets`

* use actual ckpts. (#42)

* flux3 klein example: rename from "small" and fix caption dropout for long prompts (#41)

* examples/flux3: rename small trainer, tests and readme files to klein

* examples/flux3: fix caption dropout shape mismatch for prompts longer than the pad window

* examples/flux3: add caption dropout to the i2i trainer

* examples/flux3: complete the klein rename (test class names, example output dirs)

* examples/flux3: guard against train_batch_size>1 with variable-length captions

* update flux3.md (#43)

* examples/flux3: support train_batch_size>1 and prior preservation with variable-length captions (#44)

* doc

* autodocstrings.

---------

Signed-off-by: dependabot[bot] <support@github.com>
Co-authored-by: dependabot[bot] <49699333+dependabot[bot]@users.noreply.github.com>
Co-authored-by: hf-security-analysis[bot] <265538906+hf-security-analysis[bot]@users.noreply.github.com>
Co-authored-by: Pauline Bailly-Masson <155966238+paulinebm@users.noreply.github.com>
Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>
Co-authored-by: yiyixuxu <yixu310@gmail.com>
Co-authored-by: linoytsaban <linoy.tsaban@gmail.com>
Co-authored-by: apolinário <joaopaulo.passos@gmail.com>
Co-authored-by: Linoy Tsaban <57615435+linoytsaban@users.noreply.github.com>
Co-authored-by: Aritra Roy Gosthipaty <aritra.born2fly@gmail.com>
Co-authored-by: Yumeng Li <109459218+YumengLi007@users.noreply.github.com>

### [62cde2b](https://github.com/huggingface/diffusers/commit/62cde2b0115d57492d2f5ecefab54994797df2e3)

- **作者**: Akshan Krithick
- **时间**: 2026-10-15T12:22:16Z
- **提交信息**: add modular pipeline for qwen-image 2.1 (#14976)

* add modular pipeline for qwen-image 2.1

* split out a turbo blockset and drop the guider from the text encoders

* Update tests/modular_pipelines/qwenimage21/test_modular_pipeline_qwenimage21_turbo.py

* Update tests/modular_pipelines/qwenimage21/test_modular_pipeline_qwenimage21.py

---------

Co-authored-by: Dhruv Nair <dhruv.nair@gmail.com>

### [4113984](https://github.com/huggingface/diffusers/commit/4113984327a4c96c57df4eceb6ccb02fafb527d3)

- **作者**: Jingya HUANG
- **时间**: 2026-10-15T12:04:32Z
- **提交信息**: refactor: drop the Neuron RoPE path in Qwen Image (#15042)

Neuron now runs complex tensors natively, so Qwen Image uses the
default complex RoPE on every device. This removes
`apply_rotary_emb_qwen_neuron`, `ROPE_PER_DEVICE` and the
`torch.angle` branch in `_get_device_freqs`, added in #13718.

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

### [ee84919](https://github.com/huggingface/diffusers/commit/ee849197ce45360e4f13b5c6bf6bf2e8e0b0ee78)

- **作者**: Jingya HUANG
- **时间**: 2026-10-15T11:37:50Z
- **提交信息**: [core] Tensor parallelism for Qwen-Image-2.1 (#14865)

* feat: qwen image 21 tp plan

* test: vallidated on neuron

* fix: lru_cache_unless_export leak

* fix: use complex RoPE on TPU for Qwen Image 2.1

TorchTPU reports TPU tensors as "tpu" and supports complex dtypes, so
only Neuron needs the angle-based RoPE path.

Co-Authored-By: Claude Opus 5.5 <noreply@anthropic.com>

* refactor: inline the Neuron device check for Qwen Image 2.1 RoPE

* review: cache Qwen Image 2.1 RoPE device freqs with lru_cache

* review: drop redundant torch.device

* fix: use torch.accelerator.device_count() when resolving the parallel device

* refactor: drop the Neuron branch in Qwen Image 2.1 block ids

* restore: neuron  repeat_interleave lowering error fix

* review: add TensorParallelNeuronTesterMixin for Neuron TP tests

* review: revert Qwen Image 2.1 RoPE freqs cache to a per-instance dict

* review: drop the Neuron RoPE path in Qwen Image 2.1

Neuron now runs complex tensors natively, so Qwen Image 2.1 uses the
default complex RoPE on every device. This removes
`apply_rotary_emb_qwen_neuron`, `ROPE_PER_DEVICE` and the per-device
freqs cache, and keeps `self.freqs = [freq.to(device) ...]` as on main.

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-10-16
**监控日期**: 2026-10-15
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


**报告日期**: 2026-10-16
**监控日期**: 2026-10-15
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13252
- **最后更新**: 2026-10-15T17:30:35Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Hong Zhang

## AI分析总结

# DiffSynth-Studio 仓库昨日提交分析

## 1. 主要更新类型
**功能新增** - 为训练流程中的量化选项添加 JSON 格式支持，提升配置灵活性。

## 2. 关键变更点及其与项目整体方向的关系

- **量化选项配置增强**：此次提交通过引入 JSON 格式，使用户能够以更结构化、标准化的方式定义量化参数，这与 DiffSynth-Studio 作为专业扩散模型工具的定位高度契合
- **提升用户配置体验**：JSON 格式相比硬编码方式更易于理解和维护，降低了使用门槛
- **训练工作流优化**：支持多种配置格式反映了项目对工程化实践的重视，与开源社区的配置管理最佳实践保持一致

## 3. 对项目的影响和潜在意义

**直接影响**：
- 训练脚本的配置灵活性显著提升
- 便于在不同实验场景中快速调整量化参数
- 提高了实验的可复现性

**长期意义**：
- 为后续支持更复杂的量化策略奠定基础
- 增强项目的可扩展性和社区贡献便利性
- 改善了项目在生产环境中的适用性

## 4. 值得关注的技术点

- **JSON 格式化配置**：实现了量化参数的声明式配置，便于版本控制和参数搜索
- **训练与推理的协同**：量化选项不仅影响模型存储大小，还直接关系到推理性能，这一改进对完整的模型生命周期都有意义
- **向后兼容性**：此类改动通常需要保持原有配置方式的兼容，体现了对稳定性的考量

## 5. 基于项目背景的影响分析

DiffSynth-Studio 作为扩散模型领域的综合工具平台，致力于提供从训练到部署的完整解决方案。此次提交虽然看似只是一个配置格式的改进，但实际上反映了项目的几个重要发展方向：

- **工程化成熟度提升**：支持 JSON 配置表明项目正从研究原型向生产级工具演进
- **用户体验优化**：标准化配置方式降低了学习成本，有利于吸引更多用户和贡献者
- **量化技术整合**：量化是模型部署的关键环节，此项改进强化了项目在推理优化方面的能力

总体而言，这个提交虽然规模较小，但体现了 DiffSynth-Studio 在持续完善用户体验和工程实践方面的努力，对项目向成熟、易用的方向发展具有积极意义。

## 详细提交记录

### [4a2d8af](https://github.com/modelscope/DiffSynth-Studio/commit/4a2d8af77849b20702b2639338f6fe4512f2f93e)

- **作者**: Hong Zhang
- **时间**: 2026-10-15T09:40:03Z
- **提交信息**: add json format for quant_options in training (#1757)

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-10-16
**监控日期**: 2026-10-15
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 37180
- **最后更新**: 2026-10-16T00:21:50Z

## 提交统计

- **昨日提交总数**: 41
- **提交者数量**: 33
- **主要提交者**: Tong Chen, Michael, Xinyuan Tong

## AI分析总结

## sgl-project/sglang 昨日提交分析

### 1. 主要更新类型

- **性能优化（最多）**：约 12 条，集中在推理内核融合、调度与通信优化
- **新功能**：约 12 条，涵盖多硬件平台支持、rust-server 增强、扩散模型支持
- **Bug 修复**：约 10 条，涉及 MoE 路由、流水线并行、DSA 选择器等
- **文档/Cookbook**：约 6 条，主要是模型部署配方扩充
- **重构**：5 条，DeepSeek-v4、调度器、流水线边界重构

### 2. 关键变更点

**多硬件生态持续扩展（AMD/NVIDIA/NPU/AWS）**
- AMD 方面：monokernel 插件统一运行时开关、ROCm 10.1 for gfx1250 发布、AITER 修复与 pin 更新、diffusion BF16 attention 与 MXFP4 编译启用、gfx1250 上未量化线性层路由到 aiter tgemm
- NVIDIA 方面：Blackwell 上 NVIDIA Confidential Computing 的 overlap 调度修复、FlashInfer 默认 tactic 纳入启动调优
- AWS 方面：新增基于已发布镜像构建的 EFA 镜像变体，强化云上高性能网络支持
- NPU：文档更新至 CANN 9.1.0

**DeepSeek-v4 专项优化**
- 请求窗口 KV 拷贝融合、稀疏 prefill 免主机同步的压缩长度构建、显式阶段边界与行传输重构，形成一条完整的 DSv4 优化主线，对应项目在超大 MoE 模型上的核心竞争力。

**推理架构与调度**
- MoE EP 映射保留负路由哨兵修复、PP 输出按 rank 奇偶排序解决跨节点 hang、HiCache 新增 tail-only SWA 备份与 page_unified 主机 KV 布局、调度器 prefill 预算检查前移、MiMo 验证 RoPE 与 KV 写入融合。

**rust-server 增强**
- 支持 x-override-* 请求头、健康检查端点附加元数据头、sgl-router 修复 rustls 安全漏洞（RUSTSEC-2026-0346..0349）并修复 dp-aware 下的 disagg_prefill 透传。

**扩散模型与 Cookbook**
- 新增 FLUX.3 image 与 MOSS-Image 扩散模型支持，配套大量 cookbook（muse spark、Jais 3、Nemotron 3.5 Super VL、FLUX.3 prompt upsampler 等），体现项目向多模态/图像生成推理扩展的方向。

### 3. 对项目的影响

- **正确性提升**：修复了 MoE 路由、DSA top-k 溢出、kimi-k3 流水线图、PP 跨节点 hang 等关键 bug，增强生产可靠性。
- **性能天花板**：多处 kernel 级融合（KV 写入、RoPE、稀疏 prefill）和免同步设计，持续压低推理延迟。
- **生态广度**：AMD/NPU/AWS 镜像与文档齐进，降低多平台部署门槛；CI 改进（stage 等待预算、AMD 缓存优化）保障大规模合并的效率。
- **安全与工程化**：rustls 漏洞修复、版本 bump（sgl-kernel 0.4.10）体现规范的发布流程。

### 4. 值得关注的技术点

- **免主机同步的稀疏 prefill 压缩长度构建**：消除 GPU-CPU 同步点，对大 batch 推理吞吐意义显著。
- **PP 输出按 rank 奇偶排序**：以通信顺序规避跨节点 hang，是流水线并行的典型并发陷阱案例。
- **HiCache page_unified 主机 KV 布局 + 统一 L3 key**：为分层缓存（HBM-DRAM-SSD）提供统一抽象，是长上下文与高并发场景的基础设施。
- **多个提交由 Claude/Cursor 等 AI 工具协同署名**：体现 AI 辅助开发在高性能推理内核领域的深入应用。

### 5. 对项目发展方向的影响

结合 README"LLM 与多模态模型的快速推理"定位，这批提交清晰地强化了三条主线：一是在 DeepSeek-v4 等前沿 MoE 模型上保持极致性能领先；二是通过 AMD/NPU/AWS/NVIDIA 全栈支持兑现"广泛硬件可用"的承诺，尤其 gfx1250 与 ROCm 10.1 是 ROCm 侧的重要里程碑；三是借助扩散模型（FLUX.3、MOSS-Image）和 cookbook 生态，把推理框架从纯 LLM 推理扩展到图像生成等多模态场景，扩大用户基础。整体来看，项目正从"单一推理引擎"演化为"多硬件、多模态、生产就绪"的统一推理平台。

## 详细提交记录

### [4cca7fc](https://github.com/sgl-project/sglang/commit/4cca7fcd3e644f22a61c7a6e6b57bb89b568d62a)

- **作者**: Khoa Pham
- **时间**: 2026-10-15T22:50:51Z
- **提交信息**: chore: bump sgl-kernel version to 0.4.10 (#44590)

### [ec7ab9d](https://github.com/sgl-project/sglang/commit/ec7ab9d0c21ae8e1d146379f5c148df9edae2176)

- **作者**: Kevin Mi
- **时间**: 2026-10-15T22:50:25Z
- **提交信息**: [Feat] [AMD] monokernels: one runtime switch for vendor monokernel plugins (#44353)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: wunhuang <wunhuang@amd.com>

### [0b1a735](https://github.com/sgl-project/sglang/commit/0b1a73599a23aa2d9a6ff5487c32ea1f31c85748)

- **作者**: metamergebot
- **时间**: 2026-10-15T22:50:04Z
- **提交信息**: [Feat] rust-server: Apply the x-override-* request headers (#44312)

Co-authored-by: metamergebot <metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [4e0609e](https://github.com/sgl-project/sglang/commit/4e0609ea277d09393d752fcb79181e3416d94c56)

- **作者**: William Hu
- **时间**: 2026-10-15T22:05:08Z
- **提交信息**: [Fix] moe: Preserve negative routing sentinel in EP mapping (#40498)

### [91f6ef2](https://github.com/sgl-project/sglang/commit/91f6ef23223d8415724b1bbfab415bb5977fca0c)

- **作者**: Yuwei An
- **时间**: 2026-10-15T21:11:51Z
- **提交信息**: [DSv4.1] Fuse request-window KV copies (#44555)

### [877be29](https://github.com/sgl-project/sglang/commit/877be2974aa151a984e52822c028276c2b1e9303)

- **作者**: Xinyuan Tong
- **时间**: 2026-10-15T20:34:49Z
- **提交信息**: [CI] pr-test: Let stage wait jobs reach their max-wait budget (#44410)

### [aa5c7e8](https://github.com/sgl-project/sglang/commit/aa5c7e887c7e1ef1cba10176710ce709882ef594)

- **作者**: snadampal
- **时间**: 2026-10-15T20:19:22Z
- **提交信息**: [Feat] docker: Add AWS EFA image variants built on published images (#41006)

Signed-off-by: Sunita Nadampalli <nadampal@amazon.com>

### [bc76a6b](https://github.com/sgl-project/sglang/commit/bc76a6b8193c2a7fce321c87ed893286019e68a6)

- **作者**: Ziyi Xu
- **时间**: 2026-10-15T19:45:56Z
- **提交信息**: [DSv4] Sparse prefill: build compressed lengths without a host sync (#44557)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [8721108](https://github.com/sgl-project/sglang/commit/87211088c98ae4f5b60625eebcce007db36aa6af)

- **作者**: elvischenv
- **时间**: 2026-10-15T19:09:09Z
- **提交信息**: perf: fix overlap scheduling for NVIDIA Confidential Computing(CC) on Blackwell (#36810)

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: Po-Han Huang <pohanh@nvidia.com>
Co-authored-by: Po-Han Huang (NVIDIA) <53919306+nvpohanh@users.noreply.github.com>

### [02a43ee](https://github.com/sgl-project/sglang/commit/02a43eeef6ffe4d614d00720f1a35d668ec8a6ff)

- **作者**: metamergebot
- **时间**: 2026-10-15T19:04:23Z
- **提交信息**: [Feat] rust-server: Attach configured metadata headers to a healthy /health_generate (#44315)

Co-authored-by: fei-xx <fei-xx@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [173e0f2](https://github.com/sgl-project/sglang/commit/173e0f2e9b29225384dcda89e858671851652d80)

- **作者**: metamergebot
- **时间**: 2026-10-15T19:02:59Z
- **提交信息**: [Feat] hicache: Add opt-in tail-only SWA backups in buffer mode (#44173)

Co-authored-by: metamergebot <metamergebot@users.noreply.github.com>
Co-authored-by: xiezhq-hermann <xiezhq-hermann@users.noreply.github.com>

### [bba535e](https://github.com/sgl-project/sglang/commit/bba535ebb4d176c6bf8361619e0c29fa263642fe)

- **作者**: Michael
- **时间**: 2026-10-15T18:18:41Z
- **提交信息**: [Fix] [AMD] docker: Repair the AITER build step after the 2bb549102 pin bump (#44534)

### [c5a5bf0](https://github.com/sgl-project/sglang/commit/c5a5bf0d0bd3ff2d5d08bda41aa9273feea98584)

- **作者**: Tong Chen
- **时间**: 2026-10-15T17:46:37Z
- **提交信息**: [Fix] pp: Order output send/recv by rank parity to fix cross-node hang (#44453)

Co-authored-by: chuixue <chuixue@minimaxi.com>
Co-authored-by: Shangming Cai <csmthu@gmail.com>

### [c7fb57d](https://github.com/sgl-project/sglang/commit/c7fb57d990416dd86c64e698bdb7bab58d68ca2d)

- **作者**: Shangming Cai
- **时间**: 2026-10-15T17:28:57Z
- **提交信息**: [Fix] sgl-router: Bump rustls to 0.23.46 for RUSTSEC-2026-0346..0349 (#44509)

### [a8aaf95](https://github.com/sgl-project/sglang/commit/a8aaf95b58e0a460dec547b8cc48b427e126f9c9)

- **作者**: Baizhou Zhang
- **时间**: 2026-10-15T17:20:38Z
- **提交信息**: [Cookbook] Add cookbook for muse spark open (#44527)

Co-authored-by: thomawan <thomawan@amd.com>
Co-authored-by: HAI <hixiao@gmail.com>
Co-authored-by: jianan-gu <jianan.gu@intel.com>
Co-authored-by: Thomas Wang <1am9trash@gmail.com>
Co-authored-by: zijie <zijie.chen@amd.com>
Co-authored-by: Alex Nails <alex.nails@radixark.ai>

### [5ef8319](https://github.com/sgl-project/sglang/commit/5ef8319f16290d054295c1499bf82e712a9474c7)

- **作者**: Aleksi Vesanto
- **时间**: 2026-10-15T16:40:41Z
- **提交信息**: [Perf] [AMD] attention: Enable diffusion BF16 attention and MXFP4 compilation (#27702)

Co-authored-by: jacky.cheng <yichiche@amd.com>

### [5b12ec1](https://github.com/sgl-project/sglang/commit/5b12ec163c00a852d606b6dd521ebef8d2dbdabf)

- **作者**: Yihao Wang
- **时间**: 2026-10-15T15:56:54Z
- **提交信息**: [Doc] cookbook: Expand the FLUX.3 Image Klein model description (#44515)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [05cbe24](https://github.com/sgl-project/sglang/commit/05cbe241be8b5003ee8928211608d04748b3ccbc)

- **作者**: Jimmy Shong
- **时间**: 2026-10-15T15:39:14Z
- **提交信息**: [Doc] cookbook: Add Nemotron 3.5 Super VL (#44510)

Co-authored-by: Jimmy Shong <jimmy.shong@mac.attlocal.net>

### [28b98e5](https://github.com/sgl-project/sglang/commit/28b98e5d139fb53b2c4c4eb57a5334025590da2d)

- **作者**: Yihao Wang
- **时间**: 2026-10-15T15:38:33Z
- **提交信息**: [Doc] cookbook: Add the FLUX.3 prompt upsampler section (#44512)

Co-authored-by: Sandro Cavallari <scavallari@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [e87e32b](https://github.com/sgl-project/sglang/commit/e87e32b31160dcb0dad8371258d2084e92a272cd)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-10-15T14:59:54Z
- **提交信息**: [Feat] [AMD] docker: Release ROCm 10.1 for gfx1250 in parallel with ROCm 10.0 (#42699)

### [a577073](https://github.com/sgl-project/sglang/commit/a57707377f3c4a3329f026d11909846d36f717bf)

- **作者**: AMD-yanfeiwang
- **时间**: 2026-10-15T14:42:33Z
- **提交信息**: [Fix] sgl-router: Send disagg_prefill_dp_rank to decode under --dp-aware (#44072)

Co-authored-by: Shangming Cai <csmthu@gmail.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [c4870d9](https://github.com/sgl-project/sglang/commit/c4870d98cfefa80f5cbf83de2ff6a6745032f86c)

- **作者**: qiaonan02
- **时间**: 2026-10-15T13:53:31Z
- **提交信息**: [Fix] glm5_next: Correct num_experts_per_tok default to 8 (#44093)

### [09b7383](https://github.com/sgl-project/sglang/commit/09b7383624c11a60e50af75ab40f65d4d4a99939)

- **作者**: Yihao Wang
- **时间**: 2026-10-15T13:50:59Z
- **提交信息**: [diffusion] model: support FLUX.3 image (#44418)

Co-authored-by: Dom Brown <3886319+DomBrown@users.noreply.github.com>
Co-authored-by: niehen6174 <1639206518@qq.com>
Co-authored-by: Mick Qian <mickqian@radixark.ai>
Co-authored-by: Nikita Korobov <14355239+nekorobov@users.noreply.github.com>
Co-authored-by: Daniel Campora <961215+dcampora@users.noreply.github.com>
Co-authored-by: Richard Wang <11150595+rwang5203@users.noreply.github.com>
Co-authored-by: BBuf <1182563586@qq.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [6fe5596](https://github.com/sgl-project/sglang/commit/6fe5596ebb1bdc17fa55104e9f87a3cfd77566b0)

- **作者**: elvischenv
- **时间**: 2026-10-15T13:50:09Z
- **提交信息**: Support EPLB for Nemotron-H (#43685)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [c5bf3aa](https://github.com/sgl-project/sglang/commit/c5bf3aafbc229e887eb6a6f01045b8f90a7dee13)

- **作者**: ormandj
- **时间**: 2026-10-15T13:44:58Z
- **提交信息**: Fix overflow in legacy and v1 DSA top-k selectors (#37625)

Co-authored-by: Benjamin Oldenburg <benjamin.oldenburg@ordis.co.th>

### [2f5407d](https://github.com/sgl-project/sglang/commit/2f5407da286bebd645440b5fe2293bd6e4fbfcc5)

- **作者**: jiaqiang-dot-liu
- **时间**: 2026-10-15T13:22:46Z
- **提交信息**: [Fix] [AMD] qwen3: Fix KV cache write in the fused QK-norm + mRoPE decode path (#44266)

Co-authored-by: Cursor <cursoragent@cursor.com>

### [2092160](https://github.com/sgl-project/sglang/commit/2092160d426d6a92c35b7281e87390512c3f8a2f)

- **作者**: sogalin_codegen
- **时间**: 2026-10-15T13:08:44Z
- **提交信息**: [AMD][Diffusion] Route unquantized linears through aiter tgemm on gfx1250 (#41988)

### [abf9282](https://github.com/sgl-project/sglang/commit/abf92826ee54076d368ec90175a239365c49a14e)

- **作者**: amote-i
- **时间**: 2026-10-15T12:22:54Z
- **提交信息**: [NPU] [DOC] update NPU best practices and model deployment docs to CANN 9.1.0 (#44432)

### [23c2a02](https://github.com/sgl-project/sglang/commit/23c2a026db0f5d5405f005e8c882492a26fdd851)

- **作者**: Zhang Yiyang (SII)
- **时间**: 2026-10-15T11:23:56Z
- **提交信息**: [diffusion] model: support MOSS-Image (#44325)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [f7ad434](https://github.com/sgl-project/sglang/commit/f7ad4345b86d147a1c3095a3cebabca9a33ebaa1)

- **作者**: Cheng Wan
- **时间**: 2026-10-15T09:05:28Z
- **提交信息**: [Refactor] deepseek-v4: Use explicit stage boundaries and row transport (#43607)

### [3a835cf](https://github.com/sgl-project/sglang/commit/3a835cf417d5b50ac9ef0e57dee8ffad5c7c4217)

- **作者**: Cheng Wan
- **时间**: 2026-10-15T09:04:46Z
- **提交信息**: [Refactor] inkling: Use short-convolution stage boundaries (#43606)

### [e1f9fce](https://github.com/sgl-project/sglang/commit/e1f9fce7b33d293233c4a2eefd6e43608c562ba7)

- **作者**: Cheng Wan
- **时间**: 2026-10-15T09:04:02Z
- **提交信息**: [Refactor] layer-boundary: Bind residual completion to producer updates (#43605)

### [d59c344](https://github.com/sgl-project/sglang/commit/d59c3448b085173aeebee9b60e400b7e3854db93)

- **作者**: Cheng Wan
- **时间**: 2026-10-15T09:03:27Z
- **提交信息**: [Fix] kimi-k3: Preserve pipeline graph bank inputs and bound chunk profiling (#43604)

### [71a17db](https://github.com/sgl-project/sglang/commit/71a17dbc24acdac99231b166aea57763d925b89f)

- **作者**: Eddie Zhou
- **时间**: 2026-10-15T08:21:46Z
- **提交信息**: [AMD][CI] setup: Skip redundant pip-cache chown walk and MORI rebuild (#42148)

### [93dbe88](https://github.com/sgl-project/sglang/commit/93dbe88183df35a36da5618642fd6f4bc37d283a)

- **作者**: leonardHONG
- **时间**: 2026-10-15T08:15:24Z
- **提交信息**: Fuse MiMo verification RoPE and KV cache writes (#43106)

Co-authored-by: lianghougong <lianghouhong@xiaohongshu.com>
Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

### [2870357](https://github.com/sgl-project/sglang/commit/28703575f9ba9b598891bd757bd9e264e0b442a4)

- **作者**: kangwangamd
- **时间**: 2026-10-15T08:10:41Z
- **提交信息**: [AMD] Update ROCm AITER pin to 2bb549102 (#44379)

### [8f853b0](https://github.com/sgl-project/sglang/commit/8f853b0041c11a641dfc126e09ea6836e725ec53)

- **作者**: GeorgeSherif
- **时间**: 2026-10-15T08:09:44Z
- **提交信息**: [Doc] cookbook: Add Jais 3 deployment recipes (#42766)

Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

### [86f4ede](https://github.com/sgl-project/sglang/commit/86f4ede4fbc3543ea431bb7caccd7069dde7430b)

- **作者**: xiaofei-zheng
- **时间**: 2026-10-15T07:52:48Z
- **提交信息**: [Fix] dsa: Make the fused top-k exact on an overflowing threshold bin (#37941)

Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: DarkSharpness <2040703891@qq.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [9ea5472](https://github.com/sgl-project/sglang/commit/9ea5472833296e97724f12df716936576d34ddbb)

- **作者**: Shunkangz
- **时间**: 2026-10-15T07:46:13Z
- **提交信息**: [HiCache] Add the page_unified host KV layout and the unified L3 key (#39727)

Co-authored-by: huangtingwei <141888744+huangtingwei9988@users.noreply.github.com>
Co-authored-by: Zhangheng <hzh0425@apache.org>

### [33618d4](https://github.com/sgl-project/sglang/commit/33618d4f00cb5c0b3c2182bca2561737325dfd2a)

- **作者**: Lee Nau
- **时间**: 2026-10-15T07:30:45Z
- **提交信息**: [Feat] runtime: Include FlashInfer’s default tactic in startup tuning. (#43927)

Co-authored-by: Po-Han Huang <pohanh@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [a776851](https://github.com/sgl-project/sglang/commit/a776851c97253bf6bb43e9de9dc543cd22d8de73)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-15T07:16:56Z
- **提交信息**: [Refactor] scheduler: Check the prefill budget at the admission loop head; drop a redundant PD gate (#44420)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-10-16
**监控日期**: 2026-10-15
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1291
- **最后更新**: 2026-10-15T10:44:48Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

## cache-dit 昨日提交分析（2025年7月3日）

### 1. 主要更新类型
- **纯文档更新**：昨日仅提交了 2 条记录，全部为 README 文档的同步和格式修正，不涉及任何功能代码变更。

### 2. 关键变更点及与项目方向的关系
- **社区集成列表同步**（`cdacd40`）：将 README 中的 Community Integration 部分与主文档保持一致，确保外部用户能看到最新的第三方集成信息（如 DiffSynth Studio、Diffusers 原生支持等）。
- **格式修正**（`a57c826`）：对 README.md 中的排版问题进行修复，提升文档的渲染效果和阅读体验。

这些变更虽然细微，但直接服务于项目的**社区生态建设**目标——cache-dit 作为面向 DiT 推理加速的开源引擎，依赖社区集成（如与 ComfyUI、Diffusers、DiffSynth Studio 等生态的对接）来扩大用户基础。

### 3. 对项目的影响和潜在意义
- **低技术影响，高传播价值**：这类文档更新不会改变项目的功能或性能，但对于**降低新用户上手门槛**、提升项目在 GitHub/PyPI 上的展示质量有直接作用。
- **反映项目处于成熟维护阶段**：昨日没有功能性提交，仅做文档打磨，说明项目当前可能正处于功能迭代的间隙期，或者是维护者在为下一波功能更新做准备。
- **社区信任建设**：及时同步社区集成列表有助于展示项目生态的活跃度，增强潜在用户和贡献者的信心。

### 4. 值得关注的技术点
- 昨日提交中没有直接的技术变更，因此暂无值得关注的技术细节。
- 但可以从 README 结构推断出项目当前的**生态布局**：项目已集成了 DiffSynth Studio、Diffusers 原生支持和 ComfyUI 等多个生态入口，说明团队在持续拓展**跨框架兼容性**，这是推理引擎类项目的核心竞争力之一。
- 项目采用 `#` 号关联 Issue/PR（如 `#1121`），说明贡献流程较为规范，可能有活跃的外部贡献者参与。

### 5. 对项目发展的整体影响
cache-dit 的目标是构建一个**PyTorch 原生的 DiT 推理引擎**，涵盖缓存（Cache）、并行（Parallelism）、量化（Quantization）和 CPU Offload 等核心能力。昨日的文档更新虽然体量极小，但体现了一个开源项目在**功能开发之外的持续运营**——保持文档与社区生态同步，是项目走向成熟、吸引更广泛用户群体的重要基础工作。这类"小步快跑"式的文档维护通常预示着项目有活跃的维护节奏，后续可能很快会有新的功能性提交到来。

## 详细提交记录

### [cdacd40](https://github.com/vipshop/cache-dit/commit/cdacd4064c6efb8c8da824528dbd5db759b92472)

- **作者**: DefTruth
- **时间**: 2026-10-15T10:44:43Z
- **提交信息**: docs: sync Community Integration lists with README (#1121)

### [a57c826](https://github.com/vipshop/cache-dit/commit/a57c826d3527736a0d1f1b0243d47568c350eb5f)

- **作者**: DefTruth
- **时间**: 2026-10-15T07:22:14Z
- **提交信息**: Fix formatting issues in README.md

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-10-16
**监控日期**: 2026-10-15
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 93870
- **最后更新**: 2026-10-16T00:26:45Z

## 提交统计

- **昨日提交总数**: 69
- **提交者数量**: 54
- **主要提交者**: Wen Zhou, Laith Sakka, Yongye Zhu

## AI分析总结

# vLLM 昨日提交综合分析（69 条）

## 一、主要更新类型

昨日提交以**性能优化**（约 20 条）和 **Bug 修复**（约 21 条）为主体，辅以 **AMD/ROCm 硬件支持**（约 13 条）、**CI/测试工程化**（约 11 条）以及少量新模型与功能接入（如 AliceAI、Decision 3.0 全系列、UMBP 连接器等）。

## 二、关键变更及与项目方向的关系

**投机解码持续深挖。** 量化草稿模型 lm_head、修复随机采样复用 bug、优化调度预算、GLM5.3 草稿元数据原地更新（带来 1.7% 吞吐提升），体现了 vLLM 对推理吞吐极致优化的核心追求。

**MoE 体系加速整合。** DeepGEMM MegaMoE 统一特性矩阵并支持 NVFP4，FlashInfer/TRT-LLM MXFP8 形状感知 padding，跳过冗余转置拷贝——与 DeepSeek-V4 系列模型的密集落地紧密呼应。

**AMD/ROCm 生态大力投入。** AITITER 内核接入（KDA decode、topk_gating、MegaMoE fixed-slot dispatch）、gfx1250 优化、W4A16 MoE hash 路由，以及 ZenTorch 升级启用 float16，显示 vLLM 正积极扩展非 NVIDIA 硬件覆盖面。

**KV 缓存与分布式基础设施加固。** CPU offload 共享内存分片、NIXL KV connector 改进（NVFP4 限制、MLA KV 区域注册）、CPU all-reduce 低延迟元数据同步；修复 KV offload 中 `mark_miss()` 可能翻转 pending/in-flight 异步探针状态的竞态条件，并拒绝 float16/bfloat16 KV cache dtype 不匹配配置，防止半精度混用导致的静默推理错误。这是对异步 KV 缓存状态机的深度加固，对长上下文和显存受限场景意义重大。

**易用性与工具调用改进。** 为布尔型 CLI 参数统一 `--enable-x`/`--disable-x` 风格，让 `--tool-strict-level` 未设置时回退到解析器默认值，直接呼应 "Easy, fast, and cheap LLM serving for everyone" 的定位，改善 OpenAI 兼容 API 的 tool calling 体验。

**CI 成本与可靠性。** 4×B200 测试改为夜间运行以节省资源；DeepSeek-V4.1-Flash-NVFP4 评测固定到特定模型 revision，避免模型侧变动导致 CI 结果漂移；Intel XPU 侧跳过不适用的 MoE 权重量化测试。这些调整使主分支反馈信号更稳定，有助于加速 PR 合并。

## 三、值得关注的技术点

- **滑窗注意力块表跳过空头**与 **mamba 对齐内核融合（7→1，6 倍加速）**：典型的小内核优化带来大收益。
- **Humming DeviceInfo 在 torch.compile 下可追踪**：对编译路径可观测性有长期价值。
- **生产稳定性关键修复**：流式输出会话僵尸进程清理、spec decode 停止截断 token 计数错误、KV offload 异步竞态——均直接影响生产环境可靠性。
- **多处 legacy 清理**（如 Ray driver-node GPU pin 遗留代码删除），表明代码库正向更简洁的执行器架构收敛。
- **AI 辅助开发痕迹明显**：大量提交署名 Claude/Codex/Cursor，反映 AI pair programming 已深度融入 vLLM 开发流程。

## 四、对项目整体发展的影响

结合 README 中普惠、高效、低成本的愿景，本日提交在三条主线上强化了项目定位：**性能**（投机解码与内核级优化）、**广度**（AMD/Intel 硬件与新模型接入）、**生产可靠性**（流式会话、KV 缓存、调度修复）。

投机解码与 MoE 已成最活跃的演进方向，DeepSeek-V4 全系列的密集适配说明 vLLM 正紧跟前沿模型结构快速迭代；NVFP4/MXFP4 量化的推进直接服务于降低成本。KV 缓存管理是 vLLM 高吞吐推理的核心差异化能力，其稳定性决定用户能否信任长上下文和显存卸载等高级特性。CI 策略优化为后续更大规模的功能开发铺平了持续集成道路。总体而言，这批提交体现了项目从快速功能扩张向**生产级可靠性**过渡的成熟化趋势。

## 详细提交记录

### [19b0efc](https://github.com/vllm-project/vllm/commit/19b0efce308acf2db6c8740dae7bdbfcdcce21cb)

- **作者**: Juntian Liu
- **时间**: 2026-10-15T23:14:51Z
- **提交信息**: [Perf][Core] Skip the null head of sliding-window block tables (#61724)

Signed-off-by: Juntian Liu <Juntianl777@gmail.com>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [4a89316](https://github.com/vllm-project/vllm/commit/4a89316efaf329d690ae6c5e2d7fd9cb078be44c)

- **作者**: Woosuk Kwon
- **时间**: 2026-10-15T23:00:18Z
- **提交信息**: [Core] Drop the Ray driver-node GPU pin left over from the legacy executor (#61713)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [3f1e572](https://github.com/vllm-project/vllm/commit/3f1e57225abec635b2ec1b513271ac385267bad3)

- **作者**: Omar Muhammad
- **时间**: 2026-10-15T22:54:24Z
- **提交信息**: [ROCm][Perf][Kimi-K3] Use AITER Gluon KDA kernels for decode and spec decode (#57392)

Signed-off-by: omuhamma <omar.muhammad@amd.com>
Signed-off-by: Nicholas Susanto <nicholas.susanto@amd.com>
Co-authored-by: Nicholas Susanto <nicholas.susanto@amd.com>
Co-authored-by: Simon Danielsson <70206058+simondanielsson@users.noreply.github.com>

### [de7d706](https://github.com/vllm-project/vllm/commit/de7d70676d9a39353aab4796a6987d345c597991)

- **作者**: Nick Hill
- **时间**: 2026-10-15T22:29:13Z
- **提交信息**: [Perf] Low-latency CPU all-reduce for DP metadata syncs (#61767)

Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: hjjq <50634613+hjjq@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [784d1ff](https://github.com/vllm-project/vllm/commit/784d1fff0c491b9add10ecd732de8f707a7e7dbe)

- **作者**: Stefano Castagnetta
- **时间**: 2026-10-15T22:06:40Z
- **提交信息**: [MRV2][Spec Decode] Quantized draft lm_head for drafters that share the target head (#59973)

Signed-off-by: Stefano Castagnetta <scastagnetta@nvidia.com>
Co-authored-by: Kevin H. Luu <khluu000@gmail.com>

### [d92a4f2](https://github.com/vllm-project/vllm/commit/d92a4f25f270a4c9e3a4ceb5c0fad0035e200936)

- **作者**: Shern Shiou Tan
- **时间**: 2026-10-15T22:06:06Z
- **提交信息**: [watermarking] Add DFlash support to dual-key gumbel-max watermarking (#59554)

Signed-off-by: Shern Shiou Tan <shernshiou@gmail.com>
Signed-off-by: Simon Veitner <sveitner@redhat.com>
Signed-off-by: Raphael Rialland <raphael.rialland@mistral.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Simon Veitner <sveitner@redhat.com>
Co-authored-by: Raphael Rialland <raphael.rialland@mistral.ai>
Co-authored-by: Lucas Wilkinson <LucasWilkinson@users.noreply.github.com>

### [e711723](https://github.com/vllm-project/vllm/commit/e711723352670e811b0e904300d771471e28930d)

- **作者**: Juan Villamizar
- **时间**: 2026-10-15T21:51:57Z
- **提交信息**: [ROCm] gfx1250 optimizations and model enablement (#58800)

Signed-off-by: jpvillam <juan.villamizar@amd.com>
Signed-off-by: Jaden Mathias <jaden.mathias@amd.com>
Signed-off-by: Juan Villamizar <jpvillam@amd.com>
Signed-off-by: jpvillam <jpvillam@amd.com>
Signed-off-by: Omar Muhammad <omar.muhammad@amd.com>
Signed-off-by: Daniel <danichan@amd.com>
Signed-off-by: Juan Villamizar <100237675+jpvillam-amd@users.noreply.github.com>
Co-authored-by: Jaden Mathias <jaden.mathias@amd.com>
Co-authored-by: jpvillam <jpvillam@amd.com>
Co-authored-by: Omar Muhammad <omar.muhammad@amd.com>
Co-authored-by: Daniel <danichan@amd.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: Daniel Chan <Daniel.Chan@amd.com>

### [9b99ccb](https://github.com/vllm-project/vllm/commit/9b99ccb56bc90d9f6524f0861af274ea2af02f70)

- **作者**: Thang Nguyen
- **时间**: 2026-10-15T21:48:19Z
- **提交信息**: [CI] Shard the AMD mirrors of the DP, RayExecutorV2 and batch invariance steps automatically (#61861)

Signed-off-by: Thang Nguyen <thangnguyenvn647@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [9edcc7f](https://github.com/vllm-project/vllm/commit/9edcc7fa7ec858e13d4dc10ed968b741e2c95d6a)

- **作者**: DimensionSTP
- **时间**: 2026-10-15T21:46:38Z
- **提交信息**: [Bugfix][Spec Decode] Avoid reusing random draws across block verification rounds (#61161)

Signed-off-by: DimensionSTP <65501090+DimensionSTP@users.noreply.github.com>
Co-authored-by: Kevin H. Luu <khluu000@gmail.com>

### [0c25849](https://github.com/vllm-project/vllm/commit/0c2584929202353a1b2e33934611125c604b7eed)

- **作者**: Mikko Tukiainen
- **时间**: 2026-10-15T21:11:33Z
- **提交信息**: [ROCm][Perf][Bugfix] Probe the preshuffled FP4 GEMM config by logical K (#59406)

Signed-off-by: Mikko Tukiainen <Mikko.Tukiainen@amd.com>

### [f8460ef](https://github.com/vllm-project/vllm/commit/f8460ef23659afd69046a81529ec2295e4c3f686)

- **作者**: Juntian Liu
- **时间**: 2026-10-15T20:58:25Z
- **提交信息**: [Kernel][DSv4.1] Bump FlashMLA to the 2026.09.30 release and its interleaved V4.1 KV cache (#61371)

Signed-off-by: juntianl <juntianl@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Kimi Code <noreply@moonshot.ai>
Co-authored-by: Yifan Qiao <yifanqiao@inferact.ai>

### [33212db](https://github.com/vllm-project/vllm/commit/33212db2c2daa3bb0692864b1b8c93eb1c8e545d)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-10-15T20:57:37Z
- **提交信息**: [KV Connector][NIXL] Reject NVFP4 KV cache with heterogeneous TP head split (#61865)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Kevin H. Luu <khluu000@gmail.com>

### [c414bf0](https://github.com/vllm-project/vllm/commit/c414bf029537f61d30d9782cdc9ee30698d97b20)

- **作者**: Thang Nguyen
- **时间**: 2026-10-15T20:57:35Z
- **提交信息**: [CI] Shard four AMD mirrors automatically (#61817)

Signed-off-by: Thang Nguyen <thangnguyenvn647@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [54d9b1c](https://github.com/vllm-project/vllm/commit/54d9b1cb487c2a2f12506942820f0ae443807093)

- **作者**: Wentao Ye
- **时间**: 2026-10-15T20:20:12Z
- **提交信息**: [GLM5.3 Perf] Inplace update draft decode metadata, 1.7% E2E Throughput Improvement (#61873)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [ee8c479](https://github.com/vllm-project/vllm/commit/ee8c47961b927320400f2684029945761bdb72aa)

- **作者**: SeongJun Lee
- **时间**: 2026-10-15T20:19:09Z
- **提交信息**: [CI] Use an ungated model as the attention test config default (#61732)

Signed-off-by: lesj0610 <lesj0610@gmail.com>
Co-authored-by: Wei Zhao <51183510+wzhao18@users.noreply.github.com>

### [21f4b6d](https://github.com/vllm-project/vllm/commit/21f4b6dc84d73d53818af8cdb6e4dfde4577d6cd)

- **作者**: Itay Etelis
- **时间**: 2026-10-15T20:17:40Z
- **提交信息**: [KV Offload] Split the CPU offload region across shm files (#59546)

Signed-off-by: Itay Etelis <92247226+Etelis@users.noreply.github.com>
Co-authored-by: Robert Shaw <114415538+robertgshaw2-redhat@users.noreply.github.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Kevin H. Luu <khluu000@gmail.com>

### [1653287](https://github.com/vllm-project/vllm/commit/16532876e7d370c6cf24037445a256d7b1a2a66e)

- **作者**: Thang Nguyen
- **时间**: 2026-10-15T20:13:51Z
- **提交信息**: [CI] Shard four more AMD mirrors automatically (#61860)

Signed-off-by: Thang Nguyen <thangnguyenvn647@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [d12ea8e](https://github.com/vllm-project/vllm/commit/d12ea8e309d71a79d2001255f500e9642cfe87ef)

- **作者**: Kevin
- **时间**: 2026-10-15T19:54:21Z
- **提交信息**: [Bugfix][MRV2] Keep input_ids on later PP stages for raw-token models (#61016)

Signed-off-by: booth-algo <kevinlauofficial01@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Kevin H. Luu <khluu000@gmail.com>

### [d486219](https://github.com/vllm-project/vllm/commit/d486219fc2f27a981d6eda53eb2b95bfde1a1d63)

- **作者**: David Cheung
- **时间**: 2026-10-15T19:50:06Z
- **提交信息**: [Bugfix][Core] Uncount stop-trimmed spec tokens from num_computed_tokens (#58668)

Signed-off-by: David Cheung <d7cheung@gmail.com>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>

### [49f944b](https://github.com/vllm-project/vllm/commit/49f944be3e9fa12cbff5f30ea5ed8e1efa534e20)

- **作者**: Itay Etelis
- **时间**: 2026-10-15T19:33:03Z
- **提交信息**: [Perf][HiSparse] Reuse pinned host pool after graph profiling (#61668)

Signed-off-by: Itay Etelis <92247226+Etelis@users.noreply.github.com>
Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [105605b](https://github.com/vllm-project/vllm/commit/105605b8e9982af14351cd8260b21acda7ab5869)

- **作者**: Rohan Potdar
- **时间**: 2026-10-15T19:10:12Z
- **提交信息**: [ROCm] Support DeepSeek-V4 hash routing in AITER Triton W4A16 MoE (#60282)

Signed-off-by: Rohan Potdar <rohan.potdar@amd.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [82b9cca](https://github.com/vllm-project/vllm/commit/82b9ccaa798eeec73f40ea7766d4044cfeaaff32)

- **作者**: Thien Tran
- **时间**: 2026-10-15T19:09:07Z
- **提交信息**: [Perf][MoE] Skip the TRTLLM fp8-block activation-scale transpose copy (#61773)

Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>

### [4d58fa2](https://github.com/vllm-project/vllm/commit/4d58fa254a869a5d9d0aab250ab125503d3cef26)

- **作者**: Yongye Zhu
- **时间**: 2026-10-15T19:02:01Z
- **提交信息**: [MoE] Unify DeepGEMM MegaMoE experts behind one feature-matrix layer; add NVFP4 (#61538)

Signed-off-by: Yongye Zhu <zyy1102000@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: Kevin H. Luu <khluu000@gmail.com>

### [4d9a8d6](https://github.com/vllm-project/vllm/commit/4d9a8d6a417afad932b368471e498ca75a03b942)

- **作者**: Misha Goin
- **时间**: 2026-10-15T18:12:21Z
- **提交信息**: [Bugfix] Make Humming DeviceInfo lookups traceable under torch.compile (#61858)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [47fd76e](https://github.com/vllm-project/vllm/commit/47fd76e4cee3293dfb9a99852182de9963cbe403)

- **作者**: Mikko Tukiainen
- **时间**: 2026-10-15T17:53:18Z
- **提交信息**: [ROCm][Perf] Route softmax MoE top-k, including fused shared-expert sigmoid, through AITER topk_gating (#56226)

Signed-off-by: Mikko Tukiainen <Mikko.Tukiainen@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [4f49b55](https://github.com/vllm-project/vllm/commit/4f49b55c1f753183cec09f0a32f5e3a84467e1ec)

- **作者**: Jhao-Ting Chen
- **时间**: 2026-10-15T17:44:11Z
- **提交信息**: [MoE] Shape-based padding for FlashInfer TRT-LLM MXFP8 experts (gated and non-gated) (#61293)

Signed-off-by: Jhao-Ting Chen <jhaotingc@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Robert Shaw <114415538+robertgshaw2-redhat@users.noreply.github.com>

### [7cd7982](https://github.com/vllm-project/vllm/commit/7cd7982dfda0d29c68f73c54cd343b674b290a47)

- **作者**: qizixi
- **时间**: 2026-10-15T17:23:58Z
- **提交信息**: [Spec Decode] Don't reserve DFlash/DSpark draft slots in the scheduler token budget (#59468)

Signed-off-by: zixi-qi <zixi@inferact.ai>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [338dab0](https://github.com/vllm-project/vllm/commit/338dab077c187e1bd421c4624af1169f95f60e06)

- **作者**: bzsuni
- **时间**: 2026-10-15T16:49:57Z
- **提交信息**: [Bugfix] Fix Apertus streaming scientific notation (#61812)

Signed-off-by: bzsuni <bingzhe.sun@daocloud.io>
Co-authored-by: Flora Feng <4florafeng@gmail.com>

### [957d512](https://github.com/vllm-project/vllm/commit/957d512e96d515241ab01624ca33e1e2989e8988)

- **作者**: David Cheung
- **时间**: 2026-10-15T16:38:28Z
- **提交信息**: [Bugfix][Frontend] Preserve streaming chunk boundaries in RequestOutputCollector (#58941)

Signed-off-by: David Cheung <d7cheung@gmail.com>
Co-authored-by: Benedikt Falk <bfalk@nvidia.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>

### [a9e90b9](https://github.com/vllm-project/vllm/commit/a9e90b9d1df255643fd0e600c8be182052bb6a75)

- **作者**: Jovan
- **时间**: 2026-10-15T16:37:08Z
- **提交信息**: [Bugfix][Frontend] Reject Cohere REQUIRED tool choice without tools (#61825)

Signed-off-by: Kevin <jia__kuan@163.com>

### [d6f0b7a](https://github.com/vllm-project/vllm/commit/d6f0b7a4166b325b4dda6512e2e06dcb581923ba)

- **作者**: Oxana Korzh
- **时间**: 2026-10-15T16:08:14Z
- **提交信息**: [CI] Skip exited descendants when finding the worker in the FT e2e test (#61648)

Signed-off-by: Oxana Korzh <okorzh@amd.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [ed3050a](https://github.com/vllm-project/vllm/commit/ed3050add4abd770b118ad6fa337bdde0ba2ae08)

- **作者**: fululi12
- **时间**: 2026-10-15T16:03:13Z
- **提交信息**: [Core] Apply prefill_schedule_interval outside data parallelism (#54627)

Signed-off-by: lifulu <fululi12@amd.com>
Signed-off-by: lifulu <lifulu@users.noreply.github.com>
Co-authored-by: Cursor Agent <cursoragent@cursor.com>
Co-authored-by: lifulu <lifulu@users.noreply.github.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [c825e1d](https://github.com/vllm-project/vllm/commit/c825e1d235896694ca50160286440859ed46d7d3)

- **作者**: fululi12
- **时间**: 2026-10-15T16:02:53Z
- **提交信息**: [Perf] Fuse the mamba align block-table gather into one Triton kernel, 7 kernels -> 1, 6x speedup on all shapes for this kernel (#58737)

Signed-off-by: lifulu <fululi12@amd.com>
Signed-off-by: lifulu <lifulu@users.noreply.github.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: lifulu <lifulu@users.noreply.github.com>

### [a97d19d](https://github.com/vllm-project/vllm/commit/a97d19d7924a337dd0a89b71e7bcf1fdae3f9e18)

- **作者**: CharlesWu
- **时间**: 2026-10-15T15:12:39Z
- **提交信息**: [UMBP][1/10] Add shared connector, runtime contracts, and request lifecycle (#61789)

Signed-off-by: CharlesWu <Charles.Wu@amd.com>
Co-authored-by: Yichao Zhu <Yichao.Zhu@amd.com>

### [3dcfaeb](https://github.com/vllm-project/vllm/commit/3dcfaeb4e8f6b90276c5b5f376010783ac24406c)

- **作者**: Yin Li
- **时间**: 2026-10-15T15:04:04Z
- **提交信息**: [Frontend] Apply each endpoint's top_logprobs cut in derender (#59518)

Signed-off-by: Yin Li <kevinli.ai.work@gmail.com>
Co-authored-by: Yin Li <kevinli.ai.work@gmail.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>

### [011fa68](https://github.com/vllm-project/vllm/commit/011fa68ca90c4b8745ac0376a4a44ec9cf2e8b23)

- **作者**: Matthias Gehre
- **时间**: 2026-10-15T14:26:32Z
- **提交信息**: [ROCm][Perf] Pad fp16/bf16 GEMM weight row stride for L2 cache (#55090)

Signed-off-by: Matthias Gehre <matthias.gehre@amd.com>

### [d12d546](https://github.com/vllm-project/vllm/commit/d12d5460a58b5127fd70baec43da3ce4ed280ea8)

- **作者**: Ronald
- **时间**: 2026-10-15T14:02:06Z
- **提交信息**: [Bugfix][MoE] Keep routing rows during DeepSeek V4.1 decoder replay (#61643)

Signed-off-by: Ronald1995 <ronaldautomobile@163.com>
Co-authored-by: aoshen02 <aoshen@inferact.ai>

### [24f632c](https://github.com/vllm-project/vllm/commit/24f632ca7e0dcdd66a23fd2d3063ba1819a099ec)

- **作者**: Zheng Cai
- **时间**: 2026-10-15T13:54:14Z
- **提交信息**: [Bugfix] Engage indexer TP row sharding on total rows, not per-rank rows (#61647)

Signed-off-by: Zheng Cai <caizheng1993@gmail.com>
Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: Claude Opus 4.7 <noreply@anthropic.com>
Co-authored-by: zjy0516 <riverclouds.zhu@qq.com>

### [6942584](https://github.com/vllm-project/vllm/commit/69425846f8085942b5f4c1ab8a4ae40687650258)

- **作者**: mosafariuk
- **时间**: 2026-10-15T13:52:05Z
- **提交信息**: [Bugfix][CPU] Report the real cause when the worker outgrows its memory reservation (#59472)

Signed-off-by: Mo <mosafariuk@gmail.com>

### [b7b20b1](https://github.com/vllm-project/vllm/commit/b7b20b1b8f8014e216da573351d2652b3963ada6)

- **作者**: Kevin H. Luu
- **时间**: 2026-10-15T13:51:34Z
- **提交信息**: [Bugfix][Frontend] Leave the final stop token out of chat derender text (#61757)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>

### [71536bd](https://github.com/vllm-project/vllm/commit/71536bd5f8a21faf4ea0ee52be0da690dd23940f)

- **作者**: littlecircle0730
- **时间**: 2026-10-15T13:38:52Z
- **提交信息**: [MM][CG] Support ViT full CUDA graph for DeepSeek-VL2 (#46005)

Signed-off-by: littlecircle0730 <littlecircle0730@gmail.com>
Signed-off-by: littlecircle0730 <43994952+littlecircle0730@users.noreply.github.com>
Co-authored-by: Shanshan Shen <467638484@qq.com>

### [0951fc1](https://github.com/vllm-project/vllm/commit/0951fc183cc7a86b54be45320dd42679c7065995)

- **作者**: Tuukka Sarvi
- **时间**: 2026-10-15T13:38:39Z
- **提交信息**: [ROCm][DSv4.1] Disambiguate ROCm attention class names (#58689)

Signed-off-by: Tuukka Sarvi <tuukka.sarvi@amd.com>
Co-authored-by: Shanshan Shen <467638484@qq.com>
Co-authored-by: Kevin H. Luu <khluu000@gmail.com>

### [1463501](https://github.com/vllm-project/vllm/commit/146350155321de06d178f50a5d5fff7afaad0128)

- **作者**: David Cheung
- **时间**: 2026-10-15T13:32:19Z
- **提交信息**: [Bugfix] Terminate streaming sessions on ABORT/ERROR and prevent zombie sessions (#58942)

Signed-off-by: David Cheung <d7cheung@gmail.com>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Benedikt Falk <bfalk@nvidia.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>

### [766c837](https://github.com/vllm-project/vllm/commit/766c837bd535160dd52f8c3cc61f8a1782c847d4)

- **作者**: Xunzhuo
- **时间**: 2026-10-15T13:29:24Z
- **提交信息**: [Model] Support every Decision 3.0 size (d3-flash, d3-mini, d3-nano, d3-lite, d3-edge) (#61778)

Signed-off-by: Xunzhuo Liu <xunzhuo.liu@amd.com>

### [9cede34](https://github.com/vllm-project/vllm/commit/9cede34a674c392092134e34218b127d6bbb3679)

- **作者**: Laith Sakka
- **时间**: 2026-10-15T12:59:22Z
- **提交信息**: [Bugfix] Create cuBLAS handles before memory profiling to avoid OOM (#61044)

Signed-off-by: Laith Sakka <lsakka@meta.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>

### [252be28](https://github.com/vllm-project/vllm/commit/252be28c1823b3297ade5ba74a97fdcce41a60fb)

- **作者**: Martin Hickey
- **时间**: 2026-10-15T12:41:46Z
- **提交信息**: [Frontend] Replace return_mm_kwargs with an mm_payload enum on render requests (#61427)

Signed-off-by: Martin Hickey <martin.hickey@ie.ibm.com>

### [c6b772c](https://github.com/vllm-project/vllm/commit/c6b772cf6be783b1a0dbf6046570e17c3bc85ec6)

- **作者**: Martin Hickey
- **时间**: 2026-10-15T12:34:15Z
- **提交信息**: [Bugfix][Frontend] Emit kv/ec transfer params at the top level of render output (#61241)

Signed-off-by: Martin Hickey <martin.hickey@ie.ibm.com>

### [e8e1e96](https://github.com/vllm-project/vllm/commit/e8e1e96196725f097eae2394cbc458b1f5a679b8)

- **作者**: Micah Williamson
- **时间**: 2026-10-15T11:10:59Z
- **提交信息**: [ROCm][DSv4] AITER MegaMoE Fixed-Slot Dispatch For DeepSeek-V4 (#61262)

Signed-off-by: Micah Williamson <micah.williamson@amd.com>

### [8b27d27](https://github.com/vllm-project/vllm/commit/8b27d274025e8dd1db3ca0405ac893492f8e7683)

- **作者**: Divyansh Lalotra
- **时间**: 2026-10-15T11:07:23Z
- **提交信息**: [Bugfix][KV Offload] Always attempt NIXL agent removal during peer teardown (#60279)

Signed-off-by: nej1gotnochill <divyanshlalotra2@gmail.com>
Co-authored-by: Codebuff <noreply@codebuff.com>
Co-authored-by: Kevin H. Luu <khluu000@gmail.com>

### [81e42c9](https://github.com/vllm-project/vllm/commit/81e42c99876d5e08a3ea70f5194ebf590c2e6b3c)

- **作者**: Talor Abramovich
- **时间**: 2026-10-15T11:07:19Z
- **提交信息**: [Feature][Frontend] Control the log level of request JSON body using env var (#60630)

Signed-off-by: talora <talora@nvidia.com>

### [365aaa7](https://github.com/vllm-project/vllm/commit/365aaa77bd2e714200b50854115af062e2d09f63)

- **作者**: jimmy-adams
- **时间**: 2026-10-15T10:51:57Z
- **提交信息**: [Bugfix][DSv4] Remap Quark MTP layer_quant_config onto draft prefixes (#56054)

Signed-off-by: jimmy-adams <41593649+jimmy-adams@users.noreply.github.com>

### [e10c10a](https://github.com/vllm-project/vllm/commit/e10c10a6445e56f8302e9594d8d8e279fcfaf776)

- **作者**: Wen Zhou
- **时间**: 2026-10-15T10:47:41Z
- **提交信息**: [Core] Add PROMOTION_LATENCY histogram metric for tiering offload (#53910)

Signed-off-by: Wen Zhou <wenzhou@redhat.com>
Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: Kevin H. Luu <khluu000@gmail.com>
Co-authored-by: Or Ozeri <oro@il.ibm.com>

### [6fe7401](https://github.com/vllm-project/vllm/commit/6fe7401fac6e708dd9bbffd61c0fdae00c14a7df)

- **作者**: Pei Li
- **时间**: 2026-10-15T10:35:54Z
- **提交信息**: [Perf] Read VLLM_COMPUTE_NANS_IN_LOGITS once per IterationStats (#61710)

Signed-off-by: Pei Li <peili@nvidia.com>
Co-authored-by: Kevin H. Luu <khluu000@gmail.com>

### [716c522](https://github.com/vllm-project/vllm/commit/716c5225aefa7aae0628d88a6d58adddbca7c22c)

- **作者**: Timofey
- **时间**: 2026-10-15T10:15:03Z
- **提交信息**: [Model] Add AliceAI support (#57963)

Signed-off-by: timka <timka.byzov@yandex.ru>
Co-authored-by: Codex <noreply@openai.com>

### [7020600](https://github.com/vllm-project/vllm/commit/7020600b1db32f239611b037f07e0dc5268e5b4f)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-10-15T09:18:15Z
- **提交信息**: [KV Connector][NIXL] Register packed MLA KV rows as a single region (#61074)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>
Signed-off-by: Yifan Qiao <yifanqiao@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Yifan Qiao <yifanqiao@inferact.ai>
Co-authored-by: Codex <noreply@openai.com>

### [80dd705](https://github.com/vllm-project/vllm/commit/80dd705c1d422d04fcbd65d061dfedbf738ff573)

- **作者**: Flora Feng
- **时间**: 2026-10-15T09:12:02Z
- **提交信息**: [Frontend] Make finish_reason and Responses item status truthful (#59324)

Signed-off-by: Flora Feng <4florafeng@gmail.com>
Signed-off-by: sfeng33 <4florafeng@gmail.com>
Co-authored-by: Chauncey <chaunceyjiang@gmail.com>

### [427915b](https://github.com/vllm-project/vllm/commit/427915bed2c8abc3cd05112b30d00fd2bc672d4b)

- **作者**: Denis Khachyan
- **时间**: 2026-10-15T09:11:51Z
- **提交信息**: [Build][CPU] Install Run:ai Model Streamer in vllm-openai-cpu image (#61382)

Signed-off-by: Denis Khachyan <khachyanda@gmail.com>
Co-authored-by: Claude Code <noreply@anthropic.com>

### [7f730b4](https://github.com/vllm-project/vllm/commit/7f730b4cea9a66520a9200265928ebe016b48a39)

- **作者**: Kevin H. Luu
- **时间**: 2026-10-15T08:32:43Z
- **提交信息**: [CI] Run 4xH100 steps nightly only (#61782)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [0f0bc4d](https://github.com/vllm-project/vllm/commit/0f0bc4dbb1177d3391dfb6f3dbd336f226315106)

- **作者**: wang.yuqi
- **时间**: 2026-10-15T08:26:22Z
- **提交信息**: [Test] Split the chat_utils tests. (#61765)

Signed-off-by: wang.yuqi <yuqi.wang@daocloud.io>

### [b965ee5](https://github.com/vllm-project/vllm/commit/b965ee564d1897fdaeddaeceecc316aa15a45312)

- **作者**: Harry Mellor
- **时间**: 2026-10-15T08:08:08Z
- **提交信息**: [Chore] Use upstream Transformers DeepseekV4Config (#61392)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Kevin H. Luu <khluu000@gmail.com>

### [1c4c319](https://github.com/vllm-project/vllm/commit/1c4c31979212a134b096c2ea5d58a4523feb5d33)

- **作者**: Misha Goin
- **时间**: 2026-10-15T08:08:02Z
- **提交信息**: [Frontend] Advertise `--enable-x`/`--disable-x` for boolean CLI flags (#61479)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [48f17b7](https://github.com/vllm-project/vllm/commit/48f17b77bba9430ffedc3297186a2c9d932d94c7)

- **作者**: Akshat Anand
- **时间**: 2026-10-15T08:06:59Z
- **提交信息**: [Bugfix] Reject mismatched float16/bfloat16 KV cache dtype (#60885)

Signed-off-by: cipheraxat <cipheraxat@users.noreply.github.com>
Co-authored-by: cipheraxat <cipheraxat@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [fc8e08a](https://github.com/vllm-project/vllm/commit/fc8e08a2a607968226376c53a30cfa6337578f79)

- **作者**: Sohom chakraborty
- **时间**: 2026-10-15T07:57:46Z
- **提交信息**: [Bugfix][KV Offload] Do not let mark_miss() flip a pending or in-flight async lookup probe (#59096)

Signed-off-by: Sohom Chakraborty <16609933+sohom-cs@users.noreply.github.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Kevin H. Luu <khluu000@gmail.com>

### [8fa5ae8](https://github.com/vllm-project/vllm/commit/8fa5ae844a7a8a08df54be4b044858194bea0b71)

- **作者**: Bugen Zhao
- **时间**: 2026-10-15T07:48:38Z
- **提交信息**: [Frontend] Let an unset `--tool-strict-level` fall back to the tool parser's default (#61328)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [91ed285](https://github.com/vllm-project/vllm/commit/91ed2859c7345dc160956781b4662dbf99870005)

- **作者**: Ganesh R
- **时间**: 2026-10-15T07:23:50Z
- **提交信息**: [CPU][Zen] Update zentorch to 2.14.0.1 & enable float16 on Venice and later (#61411)

Signed-off-by: Ganesh R <ganesh.r@amd.com>
Co-authored-by: Kevin H. Luu <khluu000@gmail.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>

### [85c94c1](https://github.com/vllm-project/vllm/commit/85c94c170638a41841ca7f856234de4df5e8cd8d)

- **作者**: Chaojun Zhang
- **时间**: 2026-10-15T07:23:45Z
- **提交信息**: [Tests][XPU] Skip modelopt_fp4 online MoE re-quantization test on XPU (#61723)

Signed-off-by: Chaojun Zhang <chaojun.zhang@intel.com>
Co-authored-by: Kevin H. Luu <khluu000@gmail.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>

### [8f111b2](https://github.com/vllm-project/vllm/commit/8f111b22ee433b0295043361a5cee0b0945eef34)

- **作者**: Kevin H. Luu
- **时间**: 2026-10-15T07:08:48Z
- **提交信息**: [CI] Run 4xB200 steps nightly only (#61541)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [32feecd](https://github.com/vllm-project/vllm/commit/32feecd91f4c2feb8506d21703e20e2de1e1628c)

- **作者**: Kevin H. Luu
- **时间**: 2026-10-15T07:05:18Z
- **提交信息**: [CI] Pin DeepSeek-V4.1-Flash-NVFP4 eval to its FP8-Engram revision (#61763)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [ab59367](https://github.com/vllm-project/vllm/commit/ab593678b5ae3f55d50e4526895fad165194c0d8)

- **作者**: Chaojun Zhang
- **时间**: 2026-10-15T07:03:34Z
- **提交信息**: [CI][XPU] Ignore test_reload.py on Intel CI (#61740)

Signed-off-by: Chaojun Zhang <chaojun.zhang@intel.com>
Co-authored-by: Kevin H. Luu <khluu000@gmail.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-10-16
**监控日期**: 2026-10-15
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7196
- **最后更新**: 2026-10-16T00:28:21Z

## 提交统计

- **昨日提交总数**: 29
- **提交者数量**: 25
- **主要提交者**: amy-why-3459, Chendi.Xue, boatman

## AI分析总结

## vllm-omni 昨日提交分析

### 1. 主要更新类型
- **功能新增（约 9 条）**：包括 server VAD、前端独立运行、VibeVoice-1.5B 离线支持、VoxCPM2 MRV2、播放背压等核心/模型能力。
- **Bug 修复（约 7 条）**：涉及引擎配置保留、流水线元数据、语音 token 加载、CUDA graph 内存预留等。
- **性能优化（约 3 条）**：扩散流背压、MoE 路由融合、VAE 缓存清理等。
- **CI/构建（约 5 条）**：ROCm/AMD 冒烟测试、CI 工作流优化、夜间性能测试等。
- **硬件支持（约 4 条）**：ROCm、XPU MXFP8/MXFP4、Ascend 910B。
- **文档/工具（约 2 条）**：CI 反馈闭环、精度结果标准化。

### 2. 关键变更点与项目方向的关系
该项目目标是"简单、快速、低成本的全模态模型服务"。本次提交集中在：

- **全模态服务能力完善**：Qwen3-Omni 双工会话支持（#8974）、talker MTP CUDA graph 内存预留（#8854）、MiniCPM-o 流式条件修复（#8970）——直接强化 omni 模型的实时对话链路。
- **TTS 实时性深化**：VAD 支持、流式文本提交、per-segment rho 指标、per-concurrency 首音频延迟报告——从不同层面打磨 TTS 的实时体验和可观测性。
- **多模态架构解耦**：前端独立运行与 Stage ID 校验（#8626）、AR 与扩散后端配置传播（#8092）、异步 chunk 原子调度（#7438）——为模块化部署和多后端组合奠定基础。
- **多硬件生态扩展**：ROCm（MI300 冒烟测试、AMD 周度可靠性套件）、Intel XPU（MXFP8/MXFP4 直调 vLLM kernel）、华为昇腾 4 卡实时基准——呼应"为所有人服务"的跨硬件承诺。

### 3. 对项目的影响和潜在意义
- **稳定性显著提升**：多处流式/内存类 bug 修复（如 KV cache 尺寸预留、流式条件序列保留）减少生产环境的 OOM 与输出错乱风险。
- **可观测性增强**：rho 指标、首音频延迟基准、精度结果标准化，为性能调优和回归监控提供数据基础。
- **CI 效率改善**：取消被取代的 PR 工作流、CodeQL 定时化，缓解队列压力，加快迭代节奏。
- **部署灵活性提升**：前端独立运行 + 阶段 ID 校验使用户可以只部署部分组件，降低资源门槛。

### 4. 值得关注的技术点
- **VoxCPM2 MRV2（#8743）**：混合 CUDA graph + 增量 VAE 解码，是 TTS 流式生成性能的关键突破方向。
- **扩散流播放背压（#8721）**：在生成侧与播放侧之间引入流控，是实时多模态系统中较少见但重要的工程实践。
- **异步 chunk 原子调度（#7438）**：解决流式调度中的竞争条件，对实时语音链路的正确性至关重要。
- **XPU 直调 vLLM MXFP kernel（#7173）**：复用上游 kernel 而非自研，降低异构硬件适配的维护成本。

### 5. 对项目整体发展的影响
从 README 看，vllm-omni 定位为面向所有人的全模态模型服务框架。这批提交表明项目正处于**从"能跑"到"跑好"的成熟期**：一方面持续扩展模型覆盖面（VibeVoice、HunyuanImage3、MAGI-2 等）和硬件平台（AMD、Intel、Ascend），另一方面大力投入实时链路（VAD、流式提交、背压、CUDA graph）的稳定性与性能。多硬件和多模型的并行推进，加上 CI 与可观测性基础设施的完善，为项目走向生产可用的全模态服务打下了坚实基础。

## 详细提交记录

### [6c1555a](https://github.com/vllm-project/vllm-omni/commit/6c1555aa199f7e7135ca700f59d790d8cf0025e7)

- **作者**: haic0
- **时间**: 2026-10-15T22:39:14Z
- **提交信息**: [CI/Build][ROCm] Add MiniMax-H3 MI300 nightly smoke (#8942)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>
Signed-off-by: andyluo7 <andy.luo@amd.com>
Co-authored-by: GPT-5.6 Sol <cursoragent@cursor.com>
Co-authored-by: andyluo7 <andy.luo@amd.com>

### [96274a0](https://github.com/vllm-project/vllm-omni/commit/96274a06f3a3e36c899bc4b74eb8d4d9a492e5ae)

- **作者**: haic0
- **时间**: 2026-10-15T19:58:11Z
- **提交信息**: [Bugfix][ROCm] Skip MAGI-2 fused routing tie tests off NVIDIA CUDA (#8996)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>
Signed-off-by: andyluo7 <andy.luo@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: andyluo7 <andy.luo@amd.com>

### [e27caf8](https://github.com/vllm-project/vllm-omni/commit/e27caf843c573b39f41e30cf4f2e56f09f5f2900)

- **作者**: Nick Cao
- **时间**: 2026-10-15T19:16:48Z
- **提交信息**: [Feature] Add server VAD support to turn-based /v1/realtime (#8600)

Signed-off-by: Nick Cao <ncao@redhat.com>
Co-authored-by: Codex <noreply@openai.com>

### [7812588](https://github.com/vllm-project/vllm-omni/commit/781258807459c24c27cd685ec61d572d8be0dfb1)

- **作者**: Alex Brooks
- **时间**: 2026-10-15T18:43:26Z
- **提交信息**: [Frontend / Core] Support Running Frontend Only & Validate Stage IDs (#8626)

Signed-off-by: Alex Brooks <albrooks@redhat.com>

### [730632e](https://github.com/vllm-project/vllm-omni/commit/730632e64282f1d04d628116a00efd1066e2e904)

- **作者**: leo
- **时间**: 2026-10-15T16:42:27Z
- **提交信息**: [Frontend] Add M1 streaming text commitment for Qwen3-TTS (#6515)

Signed-off-by: liuyao0322 <yaoliu548926@gmail.com>
Signed-off-by: liuyao <yaoliu548926@gmail.com>

### [010015b](https://github.com/vllm-project/vllm-omni/commit/010015bae2f9b2fec991188675360c3776ea3386)

- **作者**: CAICAII
- **时间**: 2026-10-15T16:34:31Z
- **提交信息**: [Core][TTS] Add per-segment rho instrumentation to the Qwen3-TTS ramp path (#6496) (#7201)

Signed-off-by: CAICAIIs <3360776475@qq.com>

### [fa2d0c3](https://github.com/vllm-project/vllm-omni/commit/fa2d0c3d3bfdc456baa5fafbf2d55624e1dbaf9b)

- **作者**: easonyu
- **时间**: 2026-10-15T16:29:05Z
- **提交信息**: [Benchmark] [TTS] Report per-concurrency first-audio latency in the TTS benchmark (#6577)

Signed-off-by: VLa1111 <vyu112@foxmail.com>
Signed-off-by: vla11 <vyu112@foxmail.com>
Co-authored-by: Claude Code <noreply@anthropic.com>

### [d93f97d](https://github.com/vllm-project/vllm-omni/commit/d93f97dc36d17153f9a9849cc3b94d163e92a3b6)

- **作者**: wangyu
- **时间**: 2026-10-15T14:30:04Z
- **提交信息**: [CI/Build] Cancel superseded PR workflows and schedule CodeQL to reduce workflow queue time (#8922)

Signed-off-by: wangyu <410167048@qq.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [c64509f](https://github.com/vllm-project/vllm-omni/commit/c64509fd76ecb5f965795c9255867854b0fe268c)

- **作者**: Liuchenbing-2026
- **时间**: 2026-10-15T14:17:26Z
- **提交信息**: [Bugfix] Preserve typed engine configs during legacy stage projection (#8976)

Copy dataclass fields without flattening upstream config objects. Preserve disabled fault tolerance for typed defaults and retain native opt-in for raw dictionaries.

Signed-off-by: liuchenbing <chenliumail@163.com>

### [415d76b](https://github.com/vllm-project/vllm-omni/commit/415d76b466a736e638b02eaa1096efb97cc4a05e)

- **作者**: Nick Cao
- **时间**: 2026-10-15T14:12:40Z
- **提交信息**: [BugFix][HunyuanImage3] Fix pipeline metadata (#8432)

Signed-off-by: Nick Cao <ncao@redhat.com>
Co-authored-by: Codex <noreply@openai.com>

### [b7eb54b](https://github.com/vllm-project/vllm-omni/commit/b7eb54b93e1730b06100e71f9f9f8fac2fc44c56)

- **作者**: Sy03
- **时间**: 2026-10-15T14:11:47Z
- **提交信息**: [Bugfix][Frontend] Share the runtime voice registry across API processes (#8424)

Signed-off-by: Sy03 <1370724210@qq.com>

### [f936a5b](https://github.com/vllm-project/vllm-omni/commit/f936a5b83c1444e437bc35fa007fbed13a4d7ccf)

- **作者**: wangqiankun13
- **时间**: 2026-10-15T14:07:30Z
- **提交信息**: [CI] Add nightly performance test for Qwen-Image-2.1 (#8923)

Signed-off-by: wangqiankun13 <wangqiankun13@huawei.com>
Co-authored-by: dengyunyang <584797741@qq.com>

### [620adcd](https://github.com/vllm-project/vllm-omni/commit/620adcd38a960ad0a96e2ae5c7ad6f1914cd93d2)

- **作者**: Tianyao Wu
- **时间**: 2026-10-15T13:53:29Z
- **提交信息**: [Bugfix] Load the speech usage tokenizer once and honor trust_remote_code (#8413)

Signed-off-by: Tianyao Wu <rayroy31@gmail.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [2c3976d](https://github.com/vllm-project/vllm-omni/commit/2c3976d00b8e2a0be5ec6018a1b2b74afa308774)

- **作者**: boatman
- **时间**: 2026-10-15T13:44:19Z
- **提交信息**: [Core] Add VoxCPM2 MRV2 support with mixed CUDA graphs and incremental VAE decoding (#8743)

Signed-off-by: boatman <109857087+sphinxkkkbc@users.noreply.github.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [5a0d8d6](https://github.com/vllm-project/vllm-omni/commit/5a0d8d6dea81bae953af60ad3eb33daa401996a0)

- **作者**: youhengfei
- **时间**: 2026-10-15T13:05:53Z
- **提交信息**: [Model] Add eager offline VibeVoice-1.5B support (#8909)

Signed-off-by: YouHengfei <474029121@qq.com>

### [328e9c6](https://github.com/vllm-project/vllm-omni/commit/328e9c67a920331e8dafc187beabf7d2a6cbdf0a)

- **作者**: wtz2333
- **时间**: 2026-10-15T11:49:27Z
- **提交信息**: [Core] Add playback backpressure for diffusion streams (#8721)

Signed-off-by: wtz2333 <2955110911@qq.com>
Co-authored-by: Claude Code <noreply@anthropic.com>

### [fa3a069](https://github.com/vllm-project/vllm-omni/commit/fa3a0691f436785bf67fc7e72c0d2598ab779981)

- **作者**: wangyu
- **时间**: 2026-10-15T11:38:23Z
- **提交信息**: [Misc] Standardize Omni accuracy result files for the accuracy dashboard (#8924)

Signed-off-by: wangyu <410167048@qq.com>

### [70d5f17](https://github.com/vllm-project/vllm-omni/commit/70d5f173bc7ea6ccc2b9ae266a862db32b22a751)

- **作者**: amy-why-3459
- **时间**: 2026-10-15T11:28:15Z
- **提交信息**: [Model][Qwen3-Omni] Serve duplex sessions on Model Runner V2 (#8974)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [813a23a](https://github.com/vllm-project/vllm-omni/commit/813a23a9fbef115069034ba8ddea3d223addf762)

- **作者**: DanaerLee
- **时间**: 2026-10-15T11:11:24Z
- **提交信息**: [Bugfix] Reserve talker MTP and auxiliary CUDA graph memory when sizing Omni KV caches (#8854)

Signed-off-by: MrlixiangWE <mrdanaer@gmail.com>
Co-authored-by: amy-why-3459 <221522807+amy-why-3459@users.noreply.github.com>
Co-authored-by: zijianc2 <157244773+zijianc2@users.noreply.github.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [9a18812](https://github.com/vllm-project/vllm-omni/commit/9a188123cba838af7fe0bcabc0eebb3b520e9748)

- **作者**: dengyunyang
- **时间**: 2026-10-15T09:52:45Z
- **提交信息**: [Diffusion][CI] diffusion ci skill && qwen_image21 acc ci (#8726)

Signed-off-by: dengyunyang <584797741@qq.com>
Co-authored-by: wangyu <53896905+yenuo26@users.noreply.github.com>

### [11600ba](https://github.com/vllm-project/vllm-omni/commit/11600ba498691fc353a7e0f10fd5e9e2485af60a)

- **作者**: Chendi.Xue
- **时间**: 2026-10-15T09:17:55Z
- **提交信息**: [XPU] update the way integrate xpu mxfp8/mxfp4 by direct invoking vllm mxfp4/mxfp8 kernel (#7173)

Signed-off-by: Chendi Xue <chendi.xue@intel.com>

### [7e9161e](https://github.com/vllm-project/vllm-omni/commit/7e9161e8a5600a879c70e397ba99a7e04b42d9de)

- **作者**: MinhaoLi0318
- **时间**: 2026-10-15T09:16:56Z
- **提交信息**: [Perf][Qwen-Image-2.1] Drop dead VAE feature-cache clones for single-frame images (#8680)

Signed-off-by: MinhaoLi0318 <lminhao039@gmail.com>

### [9d58852](https://github.com/vllm-project/vllm-omni/commit/9d5885230ca3396b4a2964bcb04abcad5a8b01c1)

- **作者**: weitian_wang
- **时间**: 2026-10-15T09:16:27Z
- **提交信息**: [Diffusion][MAGI-2] Fuse multi-head MoE route construction (#7175)

Signed-off-by: Weitian Wang <wangweitian@hotmail.com>
Signed-off-by: weitian_wang <wangweitian@hotmail.com>

### [dd35793](https://github.com/vllm-project/vllm-omni/commit/dd3579356059a178902416e4ac5e8e684fb4cd39)

- **作者**: Dong1017
- **时间**: 2026-10-15T08:40:26Z
- **提交信息**: [Hardware][Ascend] Enable LingBot-World realtime benchmark on 4x Ascend 910B1 (#8112)

Signed-off-by: GUOGUO <xwdong1998@163.com>
Signed-off-by: Dong1017 <55723162+Dong1017@users.noreply.github.com>

### [ad70db4](https://github.com/vllm-project/vllm-omni/commit/ad70db47810ddf471e6d7d07cc02fe078b2ee5f2)

- **作者**: dongteng
- **时间**: 2026-10-15T08:25:25Z
- **提交信息**: [Bugfix][Core] Schedule async chunks atomically (#7438)

Signed-off-by: zhangjunming <835915585@qq.com>
Signed-off-by: zh <835915585@qq.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [b8aaa07](https://github.com/vllm-project/vllm-omni/commit/b8aaa071165c9620810e7f1e10c5b9ffeb1b3c4e)

- **作者**: yezhi0312
- **时间**: 2026-10-15T08:21:13Z
- **提交信息**: [Bugfix] Preserve MiniCPM-o 4.5 streaming condition sequence in Talker output (#8970)

Signed-off-by: yezhi0312 <liuyue199903@icloud.com>
Co-authored-by: yezhi0312 <liuyue199903@icloud.com>

### [daa0309](https://github.com/vllm-project/vllm-omni/commit/daa030919cc48365567c5e11add139e7284a8873)

- **作者**: haic0
- **时间**: 2026-10-15T07:46:54Z
- **提交信息**: [CI/Build][ROCm] Add the AMD weekly reliability suite (#8945)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>
Signed-off-by: andyluo7 <andy.luo@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: andyluo7 <andy.luo@amd.com>

### [4bb1c41](https://github.com/vllm-project/vllm-omni/commit/4bb1c411beec125cb2797217b2a3fce08f74440c)

- **作者**: · Wu Kui
- **时间**: 2026-10-15T07:41:45Z
- **提交信息**: [Core] Add AR and diffusion backend config propagation (#8092)

Signed-off-by: wu kui <wukui1030660585@163.com>
Signed-off-by: shunwendongan <MacBook@MacBook-Air-6.local>
Co-authored-by: shunwendongan <MacBook@MacBook-Air-6.local>

### [a08fabe](https://github.com/vllm-project/vllm-omni/commit/a08fabee6fc0ff534cacc7b5787c2fc0fe6cba85)

- **作者**: Hongsheng Liu
- **时间**: 2026-10-15T07:37:18Z
- **提交信息**: [Doc] Close the CI failure feedback and repair evidence loop (#8969)

Signed-off-by: Hongsheng Liu <liuhongsheng4@huawei.com>
Co-authored-by: Codex <noreply@openai.com>

---
