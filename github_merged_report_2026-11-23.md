# GitHub Stars 合并报告 - 2026-11-23

**合并日期**: 2026-11-24
**监控日期**: 2026-11-23
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


**报告日期**: 2026-11-24
**监控日期**: 2026-11-23
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2302
- **最后更新**: 2026-11-24T01:01:50Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Kaiyu Shi, Coach257

## AI分析总结

# VeOmni 昨日提交分析

## 1. 主要更新类型
- **功能新增**：两条提交均属功能增强，分别涉及分布式算子配置灵活性和NPU硬件支持。
- **平台适配**：无核心Bug修复，重心在提升框架的多硬件、多配置能力。

## 2. 关键变更点及与项目方向的关系
- **统一配置字段控制算子行选择**：允许在一个配置字段中按站点（site）选择不同的算子实现行。这直接服务于VeOmni"以模型为中心的分布式配方库（Recipe Zoo）"理念，使不同硬件/环境的分布式策略可通过单一配置灵活切换，降低配置复杂度。
- **新增原生NPU分块交叉熵**：为华为昇腾NPU提供原生（native）的分块（chunked）交叉熵算子，解决大词表场景下的显存瓶颈。这扩展了VeOmni对异构硬件生态的覆盖，呼应项目"Any Modality + Scale"的目标。

## 3. 对项目的影响和潜在意义
- **提升可移植性与运维效率**：站点级算子选择使同一训练配方能在多种硬件上快速适配，减少人工维护多套配置的成本。
- **增强大模型训练能力**：分块交叉熵在NPU上的落地，使VeOmni在国产硬件上支持更长序列、更大词表的训练，扩大适用场景。
- **生态竞争力**：NPU支持对国内AI训练场景意义重大，有助于吸引昇腾用户群体。

## 4. 值得关注的技术点
- **配置驱动的算子选择机制**：体现了"配置即代码"的设计模式，值得关注其与Recipe Zoo的集成方式。
- **分块交叉熵的NPU原生实现**：分块策略可显著降低峰值显存，NPU原生版本通常涉及Ascend C算子编程，实现难度较高。
- **跨站点配置粒度**：引入"site"概念，暗示VeOmni正在向多节点异构集群场景演进。

## 5. 基于README背景的影响
VeOmni定位为"Scaling Any Modality Model Training"的框架，核心竞争力在于**跨模态、跨硬件的高效分布式训练**。这两条提交分别从**配置灵活性**和**硬件生态广度**两个维度强化了这一定位：前者让不同环境下的分布式配方更易复用，后者补齐了NPU算子短板。两者共同推动项目向"开箱即用、硬件无关"的目标迈进，对多模态大模型训练的规模化部署具有积极意义。

## 详细提交记录

### [9f533f4](https://github.com/ByteDance-Seed/VeOmni/commit/9f533f4613e8b3470fcc6b9b409c539e2391e6c1)

- **作者**: Coach257
- **时间**: 2026-11-23T02:36:47Z
- **提交信息**: [ops, model, docs] feat: choose different op rows per site from one config field (#1472)

Co-authored-by: Cursor <cursoragent@cursor.com>

### [df1accc](https://github.com/ByteDance-Seed/VeOmni/commit/df1accc562aabfbed71c0acf90fe296ce5f063bc)

- **作者**: Kaiyu Shi
- **时间**: 2026-11-23T02:10:08Z
- **提交信息**: [ops] feat: add native NPU chunk cross entropy (#1418)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-11-24
**监控日期**: 2026-11-23
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 3020
- **最后更新**: 2026-11-23T14:17:13Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Bilang ZHANG

## AI分析总结

## 1. 主要更新类型

- **功能增强**（feat）：属于对既有音频条件生成能力的扩展，而非全新模块或 Bug 修复。
- 提交信息中的 PR 编号 #1749 表明这是社区/内部协作的特性迭代。

## 2. 关键变更点及与项目方向的关系

- 核心变更是将 **H3（第三档历史窗口/配置）的因果音频历史长度从原有长度扩展到 9 个 chunk**。
- 这一改动直接服务于 LightX2V 的核心目标——**轻量化的视频生成推理**：音频与视频的同步生成需要模型回看足够长的音频上下文，才能保证长时段的节奏一致性与口型/音画对齐。
- 与 README 中"Light Video Generation Inference Framework"的定位一致：在不引入重型多模态大模型的前提下，通过**增大因果历史窗口**这种可控的计算开销，换取更长时序的一致性。

## 3. 对项目的影响和潜在意义

- **更长的音频记忆**意味着在长视频生成时，后续帧的音频条件能参考更多先前信息，减少音画漂移、节奏突变等问题。
- 扩展到 9 个 chunk 属于**显存/延迟与质量的权衡**：推理时的注意力范围增大，可能带来少量延迟或显存上升，但换来更稳定的时间一致性。
- 该变更暗示项目正在从"能跑通音视频生成"向"**长时序、高质量生成**"演进，符合推理框架持续打磨用户体验的方向。
- 作为轻量框架，这类改动也体现了团队对**参数化历史长度**（如 H1/H2/H3 档位）的设计思路，让用户可按硬件条件选择历史深度。

## 4. 值得关注的技术点

- **因果（causal）音频历史**：采用单向历史而非全局注意力，是控制复杂度的关键，扩展到 9 chunk 后需关注推理显存与 KV 缓存策略。
- **分块（chunk）粒度的时间管理**：chunk 的具体时长决定了 9 个 chunk 对应的音频时长，直接影响可用上下文长度。
- 需要确认该改动是否附带**模型权重或配置默认值的更新**，以及是否对旧配置保持向后兼容。
- 性能回归测试：扩展历史窗口后是否在 benchmark 中保持了轻量框架应有的吞吐优势，值得关注后续提交。

## 5. 对项目整体发展的影响

结合 README，LightX2V 的价值主张是"轻量 + 快速"的视频生成推理。本次提交表明项目在**不牺牲轻量定位的前提下，持续补齐音视频同步生成的短板**——这是音视频联合生成能否实用化的决定性因素之一。

从发展路径看，这类提交标志着项目正从基础设施搭建阶段，进入**生成质量与长时序一致性精耕**的阶段。历史窗口可配置化（H1/H2/H3）也为未来更多模态条件（如文本、深度）的条件注入提供了可复用的框架范式。总体而言，这是一次面向实际生成效果的稳步推进，有助于提升 LightX2V 在轻量音视频生成领域的竞争力。

（注：以上分析基于提交信息与 README 推断，具体实现细节需查看 #1749 的实际 diff。）

## 详细提交记录

### [e574493](https://github.com/ModelTC/LightX2V/commit/e574493231fc019abe70f6e7727902ea45e59474)

- **作者**: Bilang ZHANG
- **时间**: 2026-11-23T11:17:26Z
- **提交信息**: feat: extend H3 causal audio history to 9 chunks (#1749)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-11-24
**监控日期**: 2026-11-23
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2341
- **最后更新**: 2026-11-23T11:59:24Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-11-24
**监控日期**: 2026-11-23
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6996
- **最后更新**: 2026-11-24T05:56:05Z

## 提交统计

- **昨日提交总数**: 20
- **提交者数量**: 12
- **主要提交者**: Lee Nau, Brandon Zhang, Eran Geva

## AI分析总结

# flashinfer-ai/flashinfer 昨日提交综合分析（共 20 个提交）

## 一、主要更新类型

昨日提交大致分为四条主线：
- **测试与 CI 加固**（约 8–9 条）：CI 作业调整、测试文件拆分、测试收集漏洞修复、断言与跳过逻辑修复、数值精度验证改造。
- **性能优化**（约 5 条）：MXFP8 特化 GEMM、TF32 router GEMM、量化内核去冗余 fill、softmax masking 统一、MLA decode/prefill 加速。
- **Benchmark 覆盖扩展**（2 条）：MoE 与杂项内核基准例程大幅扩充。
- **功能新增与集成**（约 4 条）：trace_apply 包管理、NVFP4 MLA 融合、b12x tail-N 覆盖等。

## 二、关键变更及与项目方向的关系

**测试与 CI 是本日核心主题。** 多个提交暴露了 CI 长期未真正运行部分测试的问题：MoE all-reduce 测试未列入多 GPU 脚本、Cake 测试因 `norecursedirs` 从不被收集、autotuner 测试因新增 `pool` 参数集体失败；同时临时禁用 H100 测试作业以响应硬件事故，GB200/GB300 上耗时 110+ 分钟的混合精度 decode 测试被拆分为独立文件以规避 2 小时 CI 预算上限。另有架构自适应修复：共享内存预算改为从设备能力推导，解决 SM10.7 变化导致的误报；profiler（CUPTI）偶发无记录导致的误失败也已修复。这些修复直接服务于"内核正确性必须由真实执行的回归测试保证"这一目标，多个提交正是在恢复 main 分支绿灯。

**数值精度修复严谨。** MoE finalize 融合 kernel 将 bf16/fp16 逐项舍入求和改为 fp32 累加、仅在 Lamport 写回时舍入一次，与 TensorRT-LLM 非延迟路径对齐（上游 #16778 的移植）；MoE all-reduce 测试修复了 scale_out 越界写（每次约 43KB）与参考实现舍入顺序不一致的问题；另有提交用可精确表示的输入与 FP32 独立参考替代余弦相似度检查，实现零容差验证。

**性能优化贴合真实推理负载。** SM107（Rubin）上新增 decode 尺寸 MXFP8 形状特化 warp 级 MMA 内核（34 个白名单形状，须同时胜过两条 stock 基线才启用）；新增 fp32 输入/TF32 MMA 的 fast router GEMM，规避 cuBLAS split-K + reduce 低效路径；vLLM MiniMax MoE 量化省去每次一个 fill kernel；Prims-TS softmax 统一可见 K 范围缓存策略；NVFP4 稀疏 MLA prefill 移植到 CuTe C++ 并融合 mega kernel（最高 1.5× 加速）；Blackwell 上 DeepSeek MLA decode 的 Cake 后端新增 FP8 page-64 split reducer，128 个头分散到最多 128 个 CTA，小 batch decode 取得约 1.145–1.148× geomean 加速（最高 1.59×）。

**Benchmark 体系补全。** MoE 例程 11→14、unified_moe 34→59 对、杂项例程 39→57，覆盖 TRT-LLM Gen、Prims-TS、CuTe-DSL、Frost 等多后端及量化模式，为所有公开内核提供性能度量基础。

**集成与生态。** 新增 `installed_packages()` 与 `release_packages(allow_frozen=True)`，面向自行管理内核包的推理引擎，解决 CUDA Graph 捕获绑定无法释放的生命周期难题。

## 三、项目影响与潜在意义

- **发布质量**：多条修复标注为 v0.7.6 cherry-pick 候选，团队正在收敛发布分支，注重 release 候选的 CI 健康度；修复测试收集漏洞后，多 GPU 通信内核、Cake 实验内核、autotuner 纳入真实回归，降低"合并即破坏 main"的风险。
- **性能竞争力**：MXFP8、TF32 router、MLA 各路径优化针对 SM100/103/107 与 B200/GB300 新一代硬件的推理热点（decode 与 MoE 路由），强化新架构上的性能领先。
- **可回归性**：benchmark 覆盖扩大使后续内核改动更易被性能回归检测到，是长期质量保障的基建投入。

## 四、值得关注的技术点

- **SM107 无原生 fp8 warp MMA** 的处理：通过 `cvt.rn.scaled` 将操作数一次性转 bf16（block-scale 乘法折叠进转换），再用 bf16 HMMA fp32 累加，结合 DSMEM `st.async` 做 cluster 路径 split-K 归约。
- **越界写在 PyTorch 内存池中"侥幸通过"** 的案例，说明仅凭测试通过不足以证明内存安全。
- **CUDA Graph 状态管理**：用不同哨兵值检测 graph replay 的陈旧输出；被 graph 捕获的绑定无法释放的生命周期问题。
- **缓存一次 vs 逐 tile 重建**的权衡：D256 LDTM 因寄存器压力反而回退 3–8%，体现内核优化需实测。
- **渐进式 kernel 族管理**：新 reducer 作为第 24 个 device program 加入，按 shape 条件路由，展示大型 kernel 族的按需分发架构。
- **agent 辅助开发**：多个 PR 标注由 Codex/OpenAI 辅助完成，反映项目已采用 AI 辅助开发流程。

## 五、整体影响

结合 README 定位（面向推理的高性能 GPU 内核库），昨日提交呈现"性能前沿推进 + 工程质量加固"并重的节奏：功能层面在新一代硬件上持续落地新内核与新后端；工程层面通过 benchmark 全覆盖、测试拆分与架构自适应修复、CI 事故响应，构建可持续的性能回归与发布质量体系。项目正同步推进**质量基建**、**性能深水区**（逐微秒优化）、**生态适配**（vLLM、Blackwell SM120/107、NVFP4、多 GPU CI）三条主线，体现从"功能合并"转向"工程成熟度"与"真实负载优化"并重的发展阶段，为 v0.7.6 及后续版本的稳定交付奠定基础，巩固其在 MoE 与 DeepSeek MLA 等主流架构支持上的深度，以及在推理框架生态中的核心地位。

## 详细提交记录

### [abb297e](https://github.com/flashinfer-ai/flashinfer/commit/abb297ea0f179af74a6aaac1c16225a604ad302a)

- **作者**: Adrian
- **时间**: 2026-11-23T22:29:27Z
- **提交信息**: ci: temporarily disable H100 test jobs (#9908)

<!-- .github/pull_request_template.md -->

## 📌 Description

Temporarily disable H100 jobs in PR Test by setting `RUN_H100=false`.
This stops both full-suite and targeted H100 matrix entries for pull
requests, scheduled runs, and manual dispatches. The change is limited
to one line.

Prepared with Codex assistance.

## 🔍 Related Issues

Related incident: #9893.

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
reviewers may adjust): None (workflow-only scheduling switch).

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

Validation: changed-file pre-commit hooks passed (`PYENV_VERSION=pt
pre-commit run --files .github/workflows/pr-test.yml`), as did YAML
parsing, matrix-gate inspection, shell syntax validation, and `git diff
--check`. No GPU tests or CI runs were triggered.

Existing PR-only summary wording is retained to keep the diff minimal;
H100 scheduling is disabled for all event types.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Chores**
* H100 jobs are no longer included in the test matrix for pull requests,
scheduled runs, or manual runs.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [8faa120](https://github.com/flashinfer-ai/flashinfer/commit/8faa12077da39325a3ef8151ffc9954f6949001c)

- **作者**: Jimmy Zhou
- **时间**: 2026-11-23T22:27:21Z
- **提交信息**: bench(moe): cover TRT-LLM Gen, Prims-TS, CuTe-DSL and Frost MoE (#7622)

## 📌 Description

**Problem.** The unified benchmark script
(`benchmarks/flashinfer_benchmark.py`) covers the TRT-LLM Gen MoE
kernels only through their logits-routed FP4 / FP8 entry points, and
most MoE backends the library offers have no benchmark line:

- TRT-LLM Gen BF16 and MXINT4 fused MoE.
- The `*_routed_moe` entry points, which take routing computed earlier
(precomputed top-k ids and weights) instead of router logits.
- Prims-TS MoE (the CUTLASS-primitive, task-scheduled GEMMs) behind the
flat TRT-LLM signatures.
- In the layer API (`MoELayer`, benchmarked by `unified_moe`): most
quantized pairs of the trtllm, cute_dsl, prims_ts, cuDNN Frost and Frost
low-latency backends. `main` has the BF16 pairs and DeepSeek FP8 for
trtllm / prims_ts.
- The standalone routing kernels (`trtllm_gen_routing`,
`fused_topk_deepseek`, `alphamoe_fused_router`, `hash_topk`).
- Model features: MXFP8 and per-channel FP8, gpt-oss SwiGLU parameters
and GEMM biases, fused shared experts, padded hidden / intermediate
sizes, and half of the routing methods (`--routing_method` offered 5 of
the library's 10).

**What this PR adds.** MoE routines go from 11 to 14, and `unified_moe`
goes from 34 to 59 (quant mode, backend) pairs. Only files under
`benchmarks/` change.

- New routines: `trtllm_bf16_moe`, `trtllm_mxint4_block_scale_moe`,
`moe_routing`.
- On the `trtllm_*` routines: `--backends trtllm prims-ts`;
`--routing_input precomputed` (the routed APIs); `--fp8_quant_type
mxfp8`; `--fp8_scale_granularity per_channel`; all 10 routing methods;
`--swiglu_alpha/--swiglu_beta/--swiglu_limit`; `--gemm_bias` (FP4);
`--num_fused_shared_experts`;
`--valid_hidden_size/--valid_intermediate_size`; expert-parallel local
weights; `--autotune` on the FP8 routines.
- `alphamoe_nvfp4_aligned_moe --alphamoe_routing routed`.
- `unified_moe`: 25 new pairs across `trtllm`, `cute_dsl`, `prims_ts`,
`cudnn_frost` and `frost_low_latency`; the new quant mode
`mxint4_w4a16`; the PowLU activation. The new pairs build weights
through each config's own `prepare_*` from one shared set of BF16
weights. Pairs that already exist on `main` keep their code path.
- The three existing flat TRT-LLM routines now share one setup / bind /
time / report path with the two new ones, so each (format, backend,
routing input) combination is one table row instead of a hand-written
call site.

**Behaviour a testlist author should know.**

- A backend that rejects a configuration is reported with `[ERROR]` and
skipped; the other backends on the line still produce rows. The line
fails only if no backend ran.
- A mode flag on a routine that does not read it (for example
`--gemm_bias` outside `trtllm_fp4_block_scale_moe`, or `--backends` on
`cutlass_fused_moe`) is an error, so a row can never carry a mode that
did not run.
- `trtllm_mxint4_block_scale_moe` accepts only SwiGLU: its entry point
has no activation argument.
- `moe_routing` with `deepseek_v3` needs `--n_group` and `--topk_group`.
The `alphamoe` routing backend runs only when named in `--backends`.
- `--refcheck` on the `trtllm_*` routines: `trtllm_bf16_moe`,
`trtllm_mxint4_block_scale_moe` and `--fp8_quant_type mxfp8` are
compared with a BF16 torch reference. The other modes use synthetic
scales, so they compare a precomputed-routing call with its
logits-routed twin and each later backend with the first; a line with
neither prints a warning. `unified_moe` and `moe_routing` check against
a torch reference as before.

**Per-architecture table rows added**
(`routine_cc_to_supported_backends`).

| routine | SM100 / SM103 | SM107 |
|---|---|---|
| trtllm_fp4 / fp8_block / fp8_per_tensor | + prims-ts | + prims-ts |
| trtllm_bf16_moe (new) | trtllm, prims-ts | trtllm, prims-ts |
| trtllm_mxint4_block_scale_moe (new) | trtllm | trtllm |
| moe_routing (new) | trtllm, dsv3, alphamoe (when named), hash |
trtllm, dsv3, hash |
| cutlass_fused_moe | + 8.9 / 9.0 / 11.0 rows (library guard only, no
test hardware) | — |

`unified_moe` itself needs no rows: it filters each backend by the
config's `supported(arch)` and then by a real launch.

**Changes that move existing numbers** (the perf dashboard reads this
script; these series will step):

- NVFP4 activation scales. `trtllm_fp4_block_scale_moe --fp4_mode nvfp4`
quantized activations with *swizzled* scale factors while telling the
kernel they were linear, and when the token count was not a multiple of
128 it passed all-ones scales. It now quantizes in the linear layout the
kernel reads, at every token count.
- Timed cast. `trtllm_fp8_block_scale_moe` timed a BF16→FP8 activation
cast inside the measured region. The cast now happens before timing, so
small-token latencies drop slightly.
- `--autotune` on the FP8 routines. It used to be ignored there; it now
tunes, and the row's backend label becomes `trtllm_autotune`. An
existing FP8 line that carries `--autotune` starts a new series.
- Expert-parallel lines (`--local_num_experts` below `--num_experts`).
Weights are built for the local experts only, and TFLOPS / bandwidth
count only the (token, expert) pairs that land in the local shard.
- `unified_moe --quant_variant deepseek_fp8` bandwidth. Its rows were
accounted with the MXFP4 byte model; they now use the FP8 block-scale
model, which changes `tb_per_sec`, `weight_dtype` and `fp4_mode` on
those rows.

**New CSV columns** (appended after the existing MoE columns):
`routing_input`, `num_fused_shared_experts`, `valid_hidden_size`,
`valid_intermediate_size`, `swiglu_alpha`, `swiglu_beta`, `gemm_bias`.
The CSV writer back-fills empty columns from the parsed arguments, so
existing flat MoE rows now carry `routing_input=logits`,
`num_fused_shared_experts=0`, `gemm_bias=False` and `None` for the rest.
None of these is in the dashboard's problem key today. A testlist line
that differs from an existing one only by one of these flags needs the
column added to the key first (with those values as defaults), or the
two series merge.

**Still not covered.** CUTLASS SM90-only configs (W4A8, Humming), SM12x
FP8 configs, b12x MXFP4, `alphamoe_fp8_block_scale_aligned_moe`,
`mono_moe`. Expert-parallel layers and all-to-all are out of scope here,
as are the Cake MoE paths beyond the `cake_stepfun` pair `main` already
has.

## 🔍 Related Issues

One of five independent sibling PRs that extend
`flashinfer_benchmark.py`, each a single change off `main`:

- attention — #7620
- GEMM — #7621
- MoE (this PR)
- linear attention / SSM / comm — #7623
- norm / activation / quant / RoPE / sampling — #7624

All five edit `benchmarks/routines/flashinfer_benchmark_utils.py` and
`benchmarks/README.md`, each in its own family block, so whichever
merges later needs a trivial rebase.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

- [ ] Tests have been added or updated as needed. No unit tests: this is
a benchmark-only change.
- [x] All tests are passing (`unittest`, etc.). Validation was a
pipeclean, below.

**Pipeclean of the original change.** Every MoE example testlist (kept
outside this repo) was run once with all five families merged on top of
`main`, one case per distinct routine / backend / dtype combination:

| | lists, rc=0 | cases | CSV rows | notes |
|---|---|---|---|---|
| B200 (SM100) | 8 / 8 | 71 | 74 | |
| B300 (SM103) | 7 / 8 | 40 | 44 | the run's allocation ended before
`moe_unified_backends`; it passed on B300 in the MoE-only run |
| SM107 | 8 / 8 | 71 | 46 | AlphaMoE list gives 0 rows by design
(SM100/SM103 only) |

**After the merge with `main` and the review fixes** (MoE lists only,
same 71 cases, with `main`'s backend and mode names):

| | cases | CSV rows | errors |
|---|---|---|---|
| B200 (SM100) | 71 | 75 | 1: the `alphamoe` router's runtime compile
cannot find the CCCL headers in the test container |
| SM107 | 71 | 61 | 1 CuTe-DSL GeGLU-tanh line (not built for SM107); 3
AlphaMoE lines and 11 `unified_moe` lines have no backend on SM107 in
this container (Prims-TS layer path is SM100/SM103; Frost needs the
newer DSL) |

SM107 gains rows over the first pipeclean because Prims-TS behind the
flat `trtllm_*` routines and standalone `trtllm` routing now run there.
A further 34 targeted lines (one per review fix: every refcheck path,
each rejection, one failing backend keeping the other's row) pass on
both machines. B300 was not re-run.

The Frost list was run separately, because cuDNN Frost and Frost
low-latency need a released `nvidia-cutlass-dsl` ≥ 4.8.1 and the test
container has a 4.8.0 pre-release. Keep that list out of CI until the
image is updated.

## Reviewer Notes

- Some backends are listed by a config's `supported(arch)` but rejected
by its runner's `check_support()` for specific modes (TRT-LLM W4A16 on
SM103, CuTe-DSL W4A8 / MXFP8 and GeGLU-tanh on SM107, Prims-TS MXFP8
with ReLU2). `unified_moe` reports those as unsupported lines, not
failures; this is the library's intended two-stage check.
- Within one `unified_moe` quant mode, backends do not all time the same
boundary. The new pairs receive activations quantized before timing;
three existing backends (`cutlass` FP8 per-tensor and MXFP4-W4A8,
`cudnn` FP8 per-tensor) deliberately time the BF16→quantized conversion
and report the pre-quantized time in `prequantized_median_time`. Compare
across backends on that column in the `fp8` and `mxfp4_w4a8` modes.
- `main`'s early guards on the flat FP8 routines (FP8 block: SwiGLU
only; FP8 per-tensor: gated only) are replaced by passing the activation
to the library, which validates it.
- Timings from the pipeclean are not quoted: the machines were shared.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Expanded MoE benchmarks with standalone routing tests, additional
backend choices, and broader support for quantization formats,
activations, and model configurations.
* Added options for routing inputs, shared experts, padded dimensions,
and activation parameters, with validation for options that do not apply
to a selected benchmark.
* Added support for additional unified MoE quantization and activation
variants.
* **Documentation**
* Updated the benchmark guide with expanded format, routing, backend,
option, and autotuning coverage.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [da36a35](https://github.com/flashinfer-ai/flashinfer/commit/da36a352b4df879880a1ded6364e2252b61c1b93)

- **作者**: Jimmy Zhou
- **时间**: 2026-11-23T22:27:09Z
- **提交信息**: bench(misc): cover norm, activation, quant, RoPE and sampling APIs (#7624)

## 📌 Description

**Problem.** The unified benchmark script
(`benchmarks/flashinfer_benchmark.py`) had 39 routines for
normalization, activation, quantization, RoPE and sampling. The library
has since gained many public kernels in this family that no benchmark
line measured:

- Norms: layernorm, FP8 block-quant fused add-RMSNorm, mHC, and the
three gated-residual norms.
- Activations and fused activation + quantization: gated activations
(`act_and_mul`), SwiGLU fused with NVFP4 or MXFP8 quantization for MoE
expert inputs.
- Quantization: grouped NVFP4 / MXFP8, per-token-group 8-bit, NVFP4
KV-cache quantize / dequantize, bit packing.
- Modes of existing routines: forced top-k algorithms, per-request
sampling parameters given as tensors, deterministic sampling, NVFP4
per-token and alternative scale layouts, in-place and MLA RoPE.
- Two existing routines (`fused_rmsnorm_silu`, `fused_dit_layernorm`)
had no row in the per-architecture backend table
(`routine_cc_to_supported_backends`).

**What this PR adds.** Routines go from 39 to 57. Only files under
`benchmarks/` change.

- New norm routines: `fused_add_rmsnorm_fp8_block_quant`, `layernorm`,
`act_and_mul` (silu / gelu / gelu_tanh), `mhc` (3 modes),
`gated_residual_rmsnorm`, `gated_residual_next_rmsnorm`,
`rmsnorm_sigmoid_gate`. The gated-residual norms are pinned to the
CuTe-DSL kernels, because the library's `auto` prefers Cake (out of
scope).
- New quantization routines: `scaled_fp4_grouped_quantize`,
`mxfp8_grouped_quantize` (cuda, cutile), `per_token_group_quant_8bit`,
`silu_and_mul_nvfp4_quantize`,
`silu_and_mul_scaled_nvfp4_experts_quantize`,
`silu_and_mul_mxfp8_experts_quantize`, `nvfp4_kv_quantize`,
`nvfp4_kv_dequantize`, `nvfp4_kv_dequantize_paged`, `packbits`,
`segment_packbits`.
- Top-k: forced algorithms `radix`, `clusters`, `cub` as backends, plus
`--sorted`, `--tie_break`, `--deterministic`, `--dsa_graph_safe`.
- Sampling: `--param_mode tensor` (per-request parameters),
`--deterministic`, `--input_distribution`.
- Quantization modes: NVFP4 per-token, 4over6, FP8 input, 8×4 and linear
scale layouts (with a bitwise cute-dsl vs cuda refcheck); MXFP4 cute-dsl
on SM107.
- RoPE: `--inplace` (the five `*_inplace` APIs), `--mla_kv`,
`rope_quantize_fp8` cutile.
- Quantized outputs for `fused_rmsnorm_silu`, `fused_dit_layernorm`,
`fused_qk_rmsnorm_rope`.

**Per-architecture table rows added.** Every 10.0, 10.3 and 10.7 entry
is backed by a timed result line on B200, B300 or SM107 hardware. Rows
for 9.0, 12.x and below 10.0 rest on library guards.

| routine | SM100 / SM103 | SM107 |
|---|---|---|
| new norm routines (7) | cuda or cute-dsl, one row each | same |
| fused_rmsnorm_silu, fused_dit_layernorm | cuda (had no row) | cuda |
| new quant routines, except below | cuda or cute-dsl, one row each |
same |
| mxfp8_grouped_quantize (new) | cuda, cutile | cuda |
| per_token_group_quant_8bit (new) | cutile | — |
| mxfp4_quantize | unchanged | + cute-dsl |
| rope_quantize_fp8 | + cutile | unchanged |
| top_k, top_k_page_table_transform, top_k_ragged_transform | + radix,
clusters, cub | same |

Totals: +31 entries on 10.0, +31 on 10.3, +29 on 10.7, none removed.
cuTile is not listed on 10.7: the tile compiler in the test container
does not accept SM107.

**CSV rows of existing lines stay the same.** The CSV writer back-fills
every empty column from the parsed arguments, so a new flag would write
its default into rows that never used it. A new shared helper
(`blank_unused_mode_columns` in `flashinfer_benchmark_utils.py`) leaves
each new mode column empty on rows that do not use it. Two deliberate
changes remain. `sf_layout` now reads `linear` for `mxfp8_quantize
--no_sf_swizzled_layout` rows (it used to repeat the default). And
`resolved_backend` (an existing column) now says `cute-dsl` instead of
being empty on norm rows that run the CuTe-DSL kernel. These norm APIs
have no `backend=` argument and can fall back to CUDA kernels silently,
so the column records which path actually ran.

**New CSV columns** (appended, blank where unused): norm `act_type`,
`mhc_mode`, `num_splits`, `norm_variant`; quantization
`per_token_activation`, `nvfp4_4over6`, `use_4over6`,
`nvfp4_4over6_err_mode`, `nvfp4_4over6_err_use_fast_math`,
`nvfp4_4over6_e4m3_max`, `disable_quant_fast_math`, `masked_m`,
`column_major_scales`, `scale_tma_aligned`, `scale_ue8m0`, `bitorder`;
RoPE `inplace`, `mla_kv`; sampling `param_mode`, `deterministic`,
`input_distribution`, `sorted`, `tie_break`, `dsa_graph_safe`.

**Still not covered.** `nvfp4_quantize_paged_kv_cache` (one-shot cache
conversion), `mxfp4_dequantize`, `LogitsPipe` (it compiles to sampling
kernels that are already timed). Out of scope: Cake kernels (including
`silu_and_mul_mxfp8_quantize`, whose only implementation is Cake), the
experimental `prepare_mega_mhc`, model-specific diffusion fusions,
host-side helpers and weight-preparation shuffles.

## 🔍 Related Issues

- #7507 corrects docstrings found wrong here:
`scaled_fp4_grouped_quantize` needs a global scale of shape `[B]`, not
`[1]`. The routine passes `[B]`.

One of five independent sibling PRs that extend
`flashinfer_benchmark.py`, each a single change off `main`:

- attention — #7620
- GEMM — #7621
- MoE — #7622
- linear attention / SSM / comm — #7623
- norm / activation / quant / RoPE / sampling (this PR)

All five edit `benchmarks/routines/flashinfer_benchmark_utils.py` and
`benchmarks/README.md`, each in its own family block, so whichever
merges later needs a trivial rebase.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

- [ ] Tests have been added or updated as needed. No unit tests: this is
a benchmark-only change.
- [x] All tests are passing (`unittest`, etc.). Validation was a
pipeclean, below.

**Pipeclean.** Every example testlist for this family (kept outside this
repo) was run once with all five families merged on top of `main`, one
case per distinct routine / backend / dtype combination:

| | lists, rc=0 | cases | CSV rows | notes |
|---|---|---|---|---|
| B200 (SM100) | 15 / 15 | 121 | 135 | |
| B300 (SM103) | 12 / 15 | 98 | 99 | the run's allocation ended before 3
lists (layernorm, quantization backends, RoPE variants); all 3 passed on
B300 in the family-only run |
| SM107 | 15 / 15 | 121 | 128 | 5 cutile-only grouped-quant lines print
"No backends to test" (no cutile on 10.7) |

The B200 and SM107 runs were repeated after rebasing all five branches
onto today's `main` (the merge now includes #7486): same lists, same
case and CSV-row counts on every list.

**After merging `main` and the review fixes** (a0cd61b29): the
`batch_invariant` backends from #9368 and the MXFP8 padding check from
#9429 are kept alongside the new routines. The 15 lists were re-run on
SM100 and SM107: every list exits 0 with the same case and CSV-row
counts as in the table. A mode flag passed to a routine that ignores it
is now a parser error instead of a misleading CSV column.

**Existing lines.** The 58 distinct lines of the existing norm,
quantization, RoPE and sampling CI lists were run on SM107 with `main`'s
harness and with this one: 59 CSV rows each, none missing, and the only
column differences are the two changes described above.

## Reviewer Notes

- `sampling.softmax` dispatches internally to a Blackwell softmax kernel
with no backend choice; the routine times whatever the library
dispatches.
- Timings from the pipeclean are not quoted: the machines were shared.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added benchmark coverage for normalization, activation, quantization,
sampling, and RoPE operations.
* Added options for quantized outputs, quantization layouts and modes,
in-place RoPE, and top-k backend selection.
* Expanded NVFP4 quantization and KV-cache benchmarks, including paged
operations and MLA-shaped inputs.
* Added configurable sampling inputs, execution modes, and page-table
transformations.
* Benchmark results include additional backend and comparison details,
with unused mode fields left blank.
* **Bug Fixes**
* Improved output comparisons and reference checks across supported
formats and backends.
* **Documentation**
* Updated benchmark documentation with the new routines, modes, and
options.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [94edd32](https://github.com/flashinfer-ai/flashinfer/commit/94edd32d8d13f91657bca4ca2db6bdbd4a7ac526)

- **作者**: Jimmy Zhou
- **时间**: 2026-11-23T21:56:41Z
- **提交信息**: test(prims-ts): move the mixed-precision decode grid into its own file (#9897)

## 📌 Description

CI runs each test file under one 2-hour budget.
`tests/attention/test_attention_ts_decode.py` now takes 110–120 minutes
on GB200 and GB300. When a run is a little slower than usual, the runner
kills the file at 2 hours and marks every case in it as not run, even
with 0 failures so far (#9877).

About half of that time is one parametrized test,
`test_attention_ts_decode_mixed_precision`. It grew from about 30 to
about 60 minutes when the 512 head-dim cases were added (#5720). The
cases added since v0.7.5 brought the whole file to the edge of the
budget. No existing test got slower, so this is not a kernel slowdown.

This PR moves that grid into
`tests/attention/test_attention_ts_decode_mixed_precision.py`, so each
file gets its own budget, about an hour each.

- The test body becomes `run_mixed_precision_decode_case` in the
original file.
`test_attention_ts_decode_nvfp4_small_page_scale_fragments` still calls
it.
- No test case is added, removed or changed. Same parameters, same ids,
and only the file path in the node ids changes.
- The prims-ts README test command lists the new file.

## 🔍 Related Issues

Fixes #9877.

## 🧪 Tests

- `ruff check` and `ruff format` pass; pre-commit passes.
- Scoped CI on both files.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Tests**
* Expanded mixed-precision decode validation across batch sizes, KV
sequence lengths, query lengths, head dimensions, page sizes, and
supported data type combinations.
* Reused a shared test helper for selected decode cases, including NVFP4
small-page scale-fragment checks. The expanded tests run when CUTLASS
4.7.0 or newer is available and omit unsupported combinations.
* **Documentation**
* Updated validation instructions to include the mixed-precision decode
test module alongside the existing decode tests.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: jimmzhou <jimmzhou@nvidia.com>
Co-authored-by: mingyangw <35635157+saltyminty@users.noreply.github.com>

### [ff73235](https://github.com/flashinfer-ai/flashinfer/commit/ff73235a98cbb2e41331a8b3508301583b33d456)

- **作者**: Jimmy Zhou
- **时间**: 2026-11-23T21:45:01Z
- **提交信息**: test(batch_invariant): skip the MoE graph-capture fill check when the profiler records nothing (#9844)

## 📌 Description

`test_routing_constants_are_read_from_the_cache_under_graph_capture`
fails intermittently on GB300 with `AssertionError: []`.

**Problem.** The test replays a CUDA graph under `torch.profiler` and
counts the fill kernels in the trace. In the failing runs the trace
holds no CUDA events at all: the list it prints is empty. The graph
replay itself has already run and matched the eager output a few lines
earlier. So the empty list means the profiler (CUPTI) recorded nothing,
not that the MoE path launched too few fills.

**Fix (test only).** When the profiler returns no CUDA events, skip the
fill count instead of failing. When the trace has events, the check is
unchanged: exactly one fill, for the constant first met inside the
capture.

## 🔍 Related Issues

The test came from #9406.

## 🚀 Pull Request Checklist

- [x] Pre-commit hooks pass.
- [ ] Scoped CI on this file.

## Reviewer Notes

Cherry-pick candidate for v0.7.6, where this test fails intermittently
on GB300.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Tests**
* Updated CUDA-graph replay test handling so output equality is still
verified when profiling records no CUDA activity. When CUDA events are
recorded, the test continues to check for exactly one fill event.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [87786a1](https://github.com/flashinfer-ai/flashinfer/commit/87786a1d57aa19e83349b1de766e3cb0919fe928)

- **作者**: Jimmy Zhou
- **时间**: 2026-11-23T21:40:42Z
- **提交信息**: test(prims-ts): derive the over-capacity KV256 ring depth from the device (#9843)

## 📌 Description

`test_kv256_explicit_ring_depth_beyond_smem_capacity_is_rejected` fails
with `DID NOT RAISE` on SM 10.7 since #9315. The test is wrong, not the
library.

**Problem.** The test hardcodes a K/V ring of 6 tiles (`kv_stages=6`).
It expects that ring to pass the static pipeline check and then overflow
shared memory when the schedule is built. That held while the schedule
builder used the 227 KiB SM 10.0/10.3 limit on every arch. #9315 gave
native SM 10.7 builds their real 327 KiB (CUTLASS DSL's own table
agrees). The 6-stage layout needs about 232.5 KiB, so on SM 10.7 it fits
and the builder correctly accepts it.

**Fix (test only).**
- The test derives the deepest ring the static Q + K/V budget admits,
instead of hardcoding 6.
- On native SM 10.7 it skips. There, every ring the static check allows
also fits in shared memory, so the over-capacity error cannot be reached
for this config.
- SM 10.0/10.3 still expect the `shared-memory capacity` error.

No library change.

## 🔍 Related Issues

Introduced by #9315 (SM 10.7 shared-memory capacity). The test came from
#5123.

## 🚀 Pull Request Checklist

- [x] Pre-commit hooks pass.
- [x] Checked on CPU with the CuTe DSL compile target forced to each
arch. Before the fix: `sm_100a` and `sm_103a` pass, `sm_107a` fails with
`DID NOT RAISE`. After: `sm_100a` and `sm_103a` pass, `sm_107a` skips.

## Reviewer Notes

Cherry-pick candidate for v0.7.6; this test fails on SM 10.7 in the
release candidate.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Tests**
* Updated validation of KV256 ring depth to account for available shared
memory and Q pipeline usage.
  * Adjusted schedule-capacity checks for SM107.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [e2d163f](https://github.com/flashinfer-ai/flashinfer/commit/e2d163fb3d46dfe251feba5b6652a08871f4a0b8)

- **作者**: Brandon Zhang
- **时间**: 2026-11-23T20:48:26Z
- **提交信息**: feat(gemm): "specialized" backend for mm_mxfp8 — agent-generated SM107 small-M MXFP8 kernel (#9588)

## What

Adds an agent-generated, shape-specialized warp-level MMA kernel for
decode-size
MXFP8 (E4M3 data + UE8M0 block-32 scales, 1D swizzled 128x4 layout) NT
GEMM on
SM107 (Rubin), exposed as a new `"specialized"` backend of `mm_mxfp8`
behind a
strict `(M, N, K)` allowlist of 34 measured LLM-serving shapes (M 1-32,
N 768-6144, K 384-6144) shipped as package data
(`flashinfer/mm_mxfp8_specialized_sm107_workloads.json`). The allowlist
holds
exactly the shapes where the kernel beats the strongest stock
configuration
with margin on **both** measured stock arms — the latest FlashInfer
release and
current `main`'s autotuned backend ranking — so the stock path keeps
every
shape where it is already competitive.

SM107 has no native warp-level fp8 MMA (ptxas expands `mma...e4m3` into
F2FP
unpacks + HMMA), so the kernel converts operands to bf16 once using the
fused
scaled up-conversion (`cvt.rn.scaled::n2::ue8m0.bf16x2.e4m3x2`) — the
power-of-two block-scale multiply folds into the conversion — and
accumulates
with `mma.m16n8k16.bf16` in fp32. The wide B operand drives the mma
16-row axis
so the streamed operand is the wide one; one 16-byte lane load covers
four mma
fragments with one scale decode. Per-shape-family launch routes (m/n
tile,
warp k-split, 64/128-element k units, thread-block cluster width,
dequant form)
are compile-time specialized, with split-K folded through shared memory
and,
on cluster routes, reduced via DSMEM `st.async`. A rare-case
exact-dequant
helper preserves bit-accurate results when a tiny UE8M0 scale (< 2^-124)
would
lose low E4M3 bits in the bf16 conversion.

## Files

- `csrc/mm_mxfp8_smallm_sm107.cu` — kernel + TVM-FFI binding (single
translation unit).
- `flashinfer/jit/gemm/mxfp8_smallm_sm107.py` — JIT spec (`sm_107a`
gencode only; `-lcuda` for `cuStreamGetGreenCtx`).
- `flashinfer/gemm/mxfp8_smallm_sm107.py` — the specialized-backend
dispatcher: guards, explicit-refusal semantics, stats.
- `flashinfer/mm_mxfp8_specialized_sm107_workloads.json` — the
dispatch-surface allowlist (package data; added to `pyproject.toml`).
- `flashinfer/gemm/gemm_base.py` — `"specialized"` added to `mm_mxfp8`'s
backends (`MM_MXFP8_BACKENDS`) and the dispatch hook.
- `docs/api/gemm.rst` — backend + kill-switch documentation.
- `tests/gemm/test_mm_mxfp8_smallm_sm107.py` — tests.

## Value provenance

- **Captured structure:** the 34 allowlisted `(M, N, K)` shapes (and the
per-shape weights used in the weighted evaluation) were captured from
real
  LLM serving traces on SM107.
- **Synthetic values:** the tensor *values* used in validation are
seeded
synthetic data — bf16 Gaussians quantized by a pure-PyTorch reference MX
quantizer (E4M3 data, UE8M0 block-32 scales, 1D swizzled 128x4 layout) —
not captured activations or weights. Correctness is additionally guarded
by
an exact-dequant path in the kernel for scale/value combinations where
the
  bf16 conversion would lose E4M3 bits.

## Dispatch (the specialized-backend pattern)

`mm_mxfp8` declares `MM_MXFP8_BACKENDS = ("auto", "specialized",
"cutlass",
"cute-dsl", "cutedsl_low_latency", "trtllm", "cudnn", "b12x")`.

- The specialized backend is a **default auto candidate and a
first-class
autotune candidate**: when the call matches the allowlist surface
exactly
  (compute capability 10.7, bf16 `out_dtype` into a contiguous `out`,
  `use_8x4_sf_layout=False`, fp8 e4m3 inputs, contiguous row-major A /
  column-major B, 1D swizzled 128x4 scales of the expected padded size,
  `(M, N, K)` in the allowlist, JIT module loadable), the auto heuristic
ranks `"specialized"` first — untuned `backend="auto"` therefore runs
the
  kernel there — and the autotuner races it as itself (a `TunableRunner`
with a single fixed tactic) against the stock SM107 candidates, caching
whichever wins per bucket. Every other call keeps the stock ranking: the
runner advertises no tactic off its guards, so profiling skips shapes
the
  kernel cannot serve, and bucketed cache entries recorded on an
  allowlisted shape fall back safely off it
  (`supports_inputs`/`is_tactic_compatible`).
- **An explicitly selected backend is never silently swapped and never
falls back**: explicit `"cute-dsl"` (or any other backend) never
receives
  this kernel; explicit `backend="specialized"` that cannot serve a call
  raises `NotImplementedError` with the refusal reason (recorded in the
  dispatch stats) — only `backend="auto"` routes around a refusal.
- Guard order: GPU-free checks (kill switch, dtypes, geometry,
contiguity,
allowlist) → scale-layout guards → device guards. A JIT build failure is
  logged once; `auto` falls through to the stock path, explicit
  `backend="specialized"` raises.
- `fallback_reasons` and per-backend dispatch counters are recorded
  (`flashinfer.gemm.mxfp8_smallm_sm107._mm_mxfp8_specialized_stats()`).

The allowlist is exact membership, never a range: on shapes outside it
the
kernel measured slower than the stock path, and its generic fallback
route is
not guaranteed CUDA-graph-capture safe, so near-miss shapes must not be
added
without re-measuring (the autotuner cannot admit an off-allowlist shape
either — the runner's tactic list is empty there by construction).
Inside the allowlist every launch is a fixed,
compile-time route and is capture-safe; the kernel allocates nothing,
mutates
no device state, creates no streams, and is bitwise deterministic for
fixed
inputs.

**Kill-switch:** `FLASHINFER_SPECIALIZED_KERNEL_DISABLE=1` (read at call
time)
disables the kernel: `backend="auto"` keeps the stock path, explicit
`backend="specialized"` raises; documented in `docs/api/gemm.rst`.

## Performance

Validated on NVIDIA Rubin (SM107) silicon, per shape under CUDA-graph
timing, across the captured serving shape set, against two stock arms:
the
FlashInfer 0.7.4 release and current `main` with its autotuned SM107
backend
ranking. The specialized backend is auto-selected only on the shapes
where it
beat both arms with margin. The branch itself is based on current
`main`.
On the 34-shape allowlist the specialized kernel measures a **1.4621×
weighted
geomean vs the FlashInfer 0.7.4 release** and **1.4324× vs current
`main`'s
autotuned SM107 backend ranking** (1.3563× / 1.2792× over all 43
captured
shapes; every allowlisted shape clears ≥1.03× against both arms).
Against the
study-era pin (0.7.2.post1) the same kernel measured 1.358× weighted. A
separate A/B against the best non-FlashInfer path at this contract
(`torch._scaled_mm` MX / cuBLASLt) measures 2.45× weighted, with the
competitor winning zero of the 43 shapes.

## Testing

`tests/gemm/test_mm_mxfp8_smallm_sm107.py` (GPU tests skip unless the
device is
SM107):

- `backend="auto"` on allowlisted shapes runs the specialized kernel and
  matches a bf16 reference and the stock backend on identical quantized
  operands,
- GPU-free candidacy tests: the auto heuristic ranks `"specialized"`
first
  exactly when the eligibility probe passes (and excludes it otherwise),
  the `TunableRunner` candidate declines ineligible inputs (empty tactic
  list, `supports_inputs` False), and the `out=None` eligibility probe
  behaves,
- explicit `backend="cute-dsl"` on an allowlisted shape never receives
the
  specialized kernel,
- explicit `backend="specialized"` on the allowlist runs the kernel; off
the
  allowlist it raises `NotImplementedError` with the refusal reason
  recorded in the dispatch stats,
- `backend="auto"` off the allowlist produces the stock path's exact
results,
- the kill switch keeps the stock path under `auto`, makes explicit
  `backend="specialized"` raise, and the kernel returns once lifted,
- a non-bf16 `out_dtype` keeps the stock path,
- a CPU swizzle -> unswizzle -> dequant roundtrip over the padded
scale-layout
classes (scale columns padded to a multiple of 4, rows to a multiple of
128),
- CPU-side allowlist and scale-padding invariants (run on any machine).

`ruff check` / `ruff format` clean; `pytest --collect-only` clean.

This kernel and its integration were generated and validated with AI
assistance.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## CI

- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- not needed: targeted change behind an allowlist/new surface
-->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/gemm/test_mm_mxfp8_smallm_sm107.py
tests/gemm/test_mm_mxfp8.py tests/gemm/test_mm_mxfp8_sm120.py
tests/gemm/test_batch_invariant_mm_mxfp8.py`




### Consolidated validation follow-up (8dfadfcac90d)

Consolidated native validation and checked launches with dispatch-state
isolation and CPU negative-path coverage. The exact candidate passed 68
tests on two Rubin GPUs, zero skips, with the CUDA 13 CuTe DSL runtime.
A separate ARM AOT provider was exercised with JIT disabled. Earlier
human AOT/launch/shape requests remain addressed; additional validation
is author-side evidence, not a new human requirement.

Changed-file pre-commit checks passed. Implemented and validated with
Codex assistance; GPT-6.2 Astra on NVIDIA Inference Hub supplied
additional source review. CI must still pass on this commit.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added a specialized MXFP8 GEMM backend for supported small-M workloads
on SM107a. Automatic selection uses it only for measured, eligible
shapes; other shapes retain existing routing.
* You can select the specialized backend explicitly. Unsupported calls
raise an error rather than falling back.
* Setting `FLASHINFER_SPECIALIZED_KERNEL_DISABLE=1` keeps automatic
selection on the existing path and makes explicit specialized selection
raise an error.
* **Documentation**
* Updated GEMM backend guidance to describe automatic and explicit
selection, including behavior for unsupported calls and when the
specialized backend is disabled.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

<!-- codex-consolidated-validation -->
## Follow-up validation

Fixed the operand-placement P1 in [review
6000025580](https://github.com/flashinfer-ai/flashinfer/pull/9588#pullrequestreview-6000025580)
at 27e44ba396bc5742dc8f1da41bbe8205be3cff5f.

The public validator now rejects CPU or different-GPU activations,
weights, scales and output before backend selection. The specialized
native entry independently checks CUDA residency and co-location before
shape access, device queries or pointer use. Valid operands on a
non-current CUDA device remain supported.

Validation on my Rubin SM107 allocation using the official cu134 image:
**101 passed, zero skipped**, across the specialized suite, new
operand-placement tests and dispatch tests; the public batch-invariant
bypass test also passed. This includes every native argument on CPU and
on another GPU, a valid call after each refusal, and the existing
non-current-device success case. The separate full CPU suite passed
**11,440 tests**, with 19 skips and one expected failure. Changed-file
hooks pass.

Kernel arithmetic and the eligible workload set are unchanged. These are
independent validation results; official CI is requested for this
published head.

Implemented and reviewed with Codex and NVIDIA-hosted GPT-6.2 Astra.

### [e4f8d55](https://github.com/flashinfer-ai/flashinfer/commit/e4f8d55957c2452193da9b6e4711d067fa540190)

- **作者**: Wookje Han
- **时间**: 2026-11-23T20:48:07Z
- **提交信息**: feat(gemm): add fast tf32 router gemm (#9694)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->
Adds fast router gemm with fp32 inputs, TF32 MMAs, fp32 accumulation and
fp32 output. FlashInfer has no fp32-input GEMM today. At low M, cuBLAS's
TF32 path runs a split-K GEMM plus a separate reduce kernel which is not
effcient.

Backends:
- `"cute-dsl"`: new low-M kernel,
`flashinfer/gemm/kernels/dense_tf32_gemm_sm100_splitk.py`, for SM100,
SM103 and SM107.
- `"cublas"`: `torch.matmul`; requires
`torch.backends.cuda.matmul.allow_tf32` (it does not change it).
- `"auto"`: CuTe DSL first while its output tiles fit in half the SMs,
cuBLAS first above that. Under autotuning it picks the faster per M
bucket.

## Tests

- `tests/gemm/test_mm_tf32.py` (smoke set):
  - every backend with PDL and with autotune
  - one explicit tactic per kernel variant
  - PDL read-after-write with `late_store`
  - rejections
- checked against an fp64 reference and against `torch.matmul` under
TF32, with bitwise repeatability
- `tests/gemm/test_mm_tf32_cute_dsl_splitk_sync.py`: 500 CUDA-graph
replays plus eager PDL launches queued behind a sleep, at split
2/4/8/16, with NaN-poisoned outputs, compared bitwise against the first
result.
- `tests/gemm/test_unified_gemm_fuzz.py`: new `mm_tf32` adapter, quant
mode `tf32`.
- `tests/trace/test_mm_tf32_reference_correctness.py`.
- Results: SM107 and SM103 (GB300) pass 43/43 on the three files above.
The fuzzer passes 204/204 (SM107) and 225/225 (SM103) on mm_tf32
configs.

## Performance

Shapes are MoE router logits GEMMs with fp32 weights. A CUDA graph holds
60 back-to-back calls, each on its own weight and activation (cold
weight); median µs per call. *default* is the heuristic tactic,
*autotuned* the AutoTuner's pick. With PDL each call loads its weight
while the previous call finishes; cuBLAS has no PDL launch.

**N=256, K=8192 (Muse Spark), SM107**

| M | cuBLAS | default | autotuned | default + PDL | autotuned + PDL |
|---|---|---|---|---|---|
| 1 | 5.12 | 3.61 | 3.61 | 2.62 | 2.62 |
| 2 | 5.20 | 3.62 | 3.62 | 2.63 | 2.64 |
| 4 | 5.35 | 3.62 | 3.63 | 2.66 | 2.66 |
| 8 | 4.64 | 3.64 | 3.64 | 2.68 | 2.68 |
| 16 | 4.70 | 3.66 | 3.66 | 3.03 | 2.63 |
| 32 | 4.54 | 3.73 | 3.73 | 3.14 | 2.91 |
| 64 | 4.78 | 3.88 | 3.87 | 3.31 | 3.51 |
| 128 | 5.09 | 4.45 | 4.46 | 3.90 | 3.91 |
| 256 | 5.97 | 5.50 | 5.50 | 4.71 | 4.71 |
| 512 | 6.89 | 7.44 | 7.45 | 6.43 | 6.43 |

**N=256, K=8192 (Muse Spark), SM103**

| M | cuBLAS | default | autotuned | default + PDL | autotuned + PDL |
|---|---|---|---|---|---|
| 1 | 5.80 | 4.61 | 4.54 | 3.20 | 3.20 |
| 2 | 5.70 | 4.61 | 4.54 | 3.20 | 3.20 |
| 4 | 5.60 | 4.64 | 4.58 | 3.21 | 3.21 |
| 8 | 5.75 | 4.64 | 4.61 | 3.24 | 3.24 |
| 16 | 6.06 | 4.68 | 4.68 | 3.35 | 3.34 |
| 32 | 6.16 | 4.87 | 4.90 | 3.63 | 3.74 |
| 64 | 6.51 | 5.41 | 5.41 | 4.42 | 4.31 |
| 128 | 6.53 | 6.57 | 6.28 | 5.69 | 5.45 |
| 256 | 8.86 | 7.63 | 7.63 | 6.92 | 6.93 |
| 512 | 9.79 | 10.27 | 9.34 | 9.77 | 8.74 |

**N=160, K=5120 (GLM-4.5/4.6), SM107**

| M | cuBLAS | default | autotuned | default + PDL | autotuned + PDL |
|---|---|---|---|---|---|
| 1 | 4.86 | 3.16 | 3.16 | 2.20 | 2.21 |
| 2 | 3.81 | 3.16 | 3.20 | 2.21 | 2.21 |
| 4 | 4.07 | 3.17 | 3.20 | 2.22 | 2.21 |
| 8 | 4.05 | 3.18 | 3.17 | 2.23 | 2.23 |
| 16 | 4.11 | 3.15 | 3.15 | 2.38 | 2.28 |
| 32 | 3.99 | 3.20 | 3.20 | 2.41 | 2.42 |
| 64 | 4.20 | 3.32 | 3.33 | 2.58 | 2.61 |
| 128 | 4.35 | 4.02 | 3.81 | 3.35 | 3.10 |
| 256 | 4.91 | 4.85 | 4.42 | 4.23 | 3.75 |
| 512 | 5.41 | 5.74 | 5.74 | 4.83 | 5.30 |

**N=160, K=5120 (GLM-4.5/4.6), SM103**

| M | cuBLAS | default | autotuned | default + PDL | autotuned + PDL |
|---|---|---|---|---|---|
| 1 | 5.29 | 3.73 | 3.73 | 2.51 | 2.52 |
| 2 | 5.25 | 3.74 | 3.67 | 2.52 | 2.53 |
| 4 | 5.39 | 3.74 | 3.69 | 2.54 | 2.54 |
| 8 | 5.43 | 3.75 | 3.71 | 2.54 | 2.55 |
| 16 | 5.63 | 3.75 | 3.79 | 2.64 | 2.63 |
| 32 | 5.71 | 3.84 | 3.84 | 2.76 | 2.77 |
| 64 | 5.73 | 4.05 | 4.03 | 3.20 | 3.23 |
| 128 | 5.91 | 4.69 | 4.70 | 3.88 | 3.88 |
| 256 | 6.40 | 5.42 | 5.42 | 4.57 | 4.56 |
| 512 | 8.39 | 7.63 | 7.05 | 6.83 | 6.30 |

**N=128, K=4096 (GLM-4.5-Air), SM107**

| M | cuBLAS | default | autotuned | default + PDL | autotuned + PDL |
|---|---|---|---|---|---|
| 1 | 3.81 | 3.02 | 3.03 | 2.10 | 2.10 |
| 2 | 3.92 | 3.02 | 3.02 | 2.11 | 2.11 |
| 4 | 3.95 | 3.03 | 3.03 | 2.14 | 2.14 |
| 8 | 3.98 | 3.04 | 3.05 | 2.17 | 2.17 |
| 16 | 3.99 | 3.05 | 3.07 | 2.25 | 2.31 |
| 32 | 3.70 | 3.09 | 3.09 | 2.31 | 2.31 |
| 64 | 3.90 | 3.21 | 3.20 | 2.48 | 2.49 |
| 128 | 4.04 | 3.23 | 3.24 | 2.55 | 2.57 |
| 256 | 4.28 | 3.75 | 3.76 | 3.07 | 3.08 |
| 512 | 4.89 | 4.76 | 4.29 | 4.19 | 3.56 |

**N=128, K=4096 (GLM-4.5-Air), SM103**

| M | cuBLAS | default | autotuned | default + PDL | autotuned + PDL |
|---|---|---|---|---|---|
| 1 | 4.11 | 3.26 | 3.30 | 2.30 | 2.29 |
| 2 | 4.84 | 3.25 | 3.26 | 2.31 | 2.31 |
| 4 | 5.00 | 3.30 | 3.30 | 2.32 | 2.38 |
| 8 | 5.10 | 3.32 | 3.34 | 2.35 | 2.36 |
| 16 | 5.11 | 3.44 | 3.44 | 2.38 | 2.45 |
| 32 | 5.15 | 3.55 | 3.54 | 2.51 | 2.53 |
| 64 | 5.18 | 3.80 | 3.79 | 2.81 | 2.81 |
| 128 | 5.31 | 4.42 | 4.42 | 3.48 | 3.36 |
| 256 | 5.80 | 4.93 | 4.95 | 4.15 | 3.99 |
| 512 | 10.30 | 5.59 | 5.59 | 4.81 | 4.80 |

Against cuBLAS TF32:
- **SM107:** 1.2–1.5× faster up to M = 64 without PDL, 1.4–2.2× with PDL
(1.1–1.6× at M = 128–512); PDL saves 12–30% per call.
- **SM103:** 1.2–1.5× faster up to M = 64 without PDL, 1.5–2.2× with PDL
(1.1–2.1× at M = 128–512); PDL saves 5–33% per call.

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
* Added `mm_tf32` for FP32 matrix multiplication using TF32, with CuTe
DSL, cuBLAS, and automatic backend selection.
* Added autotuning, performance benchmarking, and execution tracing for
TF32 matrix multiplication.

* **Documentation**
* Documented the operation, supported benchmark routines, and input
requirements. cuBLAS use requires TF32 to be enabled.

* **Tests**
* Added coverage for numerical accuracy, backend selection, autotuning,
repeatability, and input validation.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [ec72105](https://github.com/flashinfer-ai/flashinfer/commit/ec7210591017ef90487b2c028d57759cb0b87426)

- **作者**: Cindy Zhang
- **时间**: 2026-11-23T18:53:55Z
- **提交信息**: fix(tests): locate MoE EP provider resources in nightly installs (#9847)

Resolve provider manifests and pinned reducer sources from the installed
distribution when tests run outside the checkout. Add a CPU regression
test for the isolated nightly layout while retaining missing-resource
failures.

Developed with assistance from OpenAI Codex.

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->
Fix two MoE EP integrity tests that fail when nightly package tests run
outside the source checkout.

Nightly stages tests and benchmarks in a temporary directory without
copying the `flashinfer/` source tree. Both tests previously resolved
provider files relative to the staged tests, causing `FileNotFoundError`
for `export_manifest.json` and `topk_reduce.py` across CUDA 12.9, 13.0,
and 13.4 shard 1 jobs.
- Resolve provider resources through `flashinfer-python` distribution
metadata when the source tree is absent.
- Preserve manifest coverage and SHA-256 checks, including failures for
missing package data.
- Add a CPU regression test that exercises both integrity checks in an
isolated layout without importing FlashInfer or requiring CUDA.

## 🔍 Related Issues

<!-- Link any related issues here -->
Observed in Nightly Release run: 
  https://github.com/flashinfer-ai/flashinfer/actions/runs/44877470908
- Introduced by #9426, which added the two integrity tests with paths
relative to the source checkout.
- #9740 subsequently updated those paths during the kernel
reorganization; the same failure was already present before that PR.


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
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

  Suggested CI test targets:
`tests/moe_ep/test_provider_package.py
tests/cpu/moe_ep/test_provider_package_isolation.py`


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
The CPU regression test stages real vendored files with distribution
metadata to reproduce the installed layout. It does not build or install
the release artifact; full nightly shard 1 validation remains pending.

### [57e5a38](https://github.com/flashinfer-ai/flashinfer/commit/57e5a38b76fe8e683fc540415c4c8c4a30bd6547)

- **作者**: feih-nv
- **时间**: 2026-11-23T18:53:02Z
- **提交信息**: test(comm): fix scale_out size and the reference in the finalize all-reduce test; run the MoE all-reduce tests in multi-GPU CI (#9861)

## 📌 Description

`tests/comm/test_trtllm_moe_allreduce_fusion_finalize.py` had two
defects, and neither showed up because CI never ran the file. Found
while qualifying #9749 on 4-GPU nodes.

**1. `scale_out` was under-allocated (out-of-bounds write on every
call).**
- The test allocated the linear size, `token_num * hidden_dim / 16`
elements: 14 KB at 16 x 7168.
- `trtllm_moe_finalize_allreduce_fusion` writes scale factors in
SWIZZLED_128x4, as its docstring says: `round_up(token_num, 128) *
round_up(hidden_dim // 16, 4)` bytes, 57 KB here. So each call wrote
about 43 KB past the buffer.
- The writes landed inside PyTorch's memory pool, so the unmodified test
still passed. With a different allocation layout the 2-rank cases fail
with `CUDA error: an illegal memory access`.
- Fix: size the buffer with `comm.compute_fp4_swizzled_layout_sf_size`,
as `test_trtllm_moe_allreduce_fusion.py` already does for its swizzled
cases.

**2. The reference rounded differently from the kernel (`[dtype1-4]`,
bf16 with 4 ranks, fails on main).**
- The reference summed the top-k terms in bf16 / fp16. The kernel rounds
in a different order, and since #9749 it accumulates in fp32 and rounds
once.
- Where the terms cancel, the two per-rank values differ by about 0.08;
four ranks multiply that past `atol = 0.2`. `Mismatched elements: 9 /
114688` on main before #9749, 6 after it. fp16 and the 2-rank cases stay
within tolerance.
- Fix: the reference accumulates in fp32 and rounds once per rank, like
the kernel.

**3. Why CI did not catch either.**
`scripts/infra/task_test_multi_gpu_comm_kernels.sh` listed neither this
file nor `test_trtllm_moe_allreduce_fusion.py`, so the multi-GPU job
logged `No multi-GPU files overlap TEST_PATH=...; skipping.`, and in the
single-GPU shards every case skips for lack of GPUs. Both files spawn
their own workers, so they are added to `SPAWN_MANAGED_TEST_FILES`.

## 🔍 Related Issues

Follow-up to #9749.

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
`tests/comm/test_trtllm_moe_allreduce_fusion_finalize.py
tests/comm/test_trtllm_moe_allreduce_fusion.py`

Both test files on a 4-GPU GB300 node (SM103, CUDA 13.0 CI container),
run by hand through the kernel-sync controller because CI did not run
them:

| test file | main (with #9749) | this PR |
|---|---|---|
| finalize (4 cases) | 3/4, `[dtype1-4]` fails | 4/4 |
| reduction (4 cases) | 4/4 | 4/4 |

How each defect was reproduced before the fix:
- Tolerance: unmodified main fails `[dtype1-4]` every time on 4-GPU
nodes (GB200 at `21e077fc80` and `c032cb58be`, GB300 at `c032cb58be`),
and replaying the kernel's and the reference's arithmetic with the
test's seeded inputs gives the same 9 elements.
- Out-of-bounds write: silent with the unmodified test. Variants
alternated in one GB300 allocation: the original file passes, the fp32
reference with the old `scale_out` size faults on both 2-rank cases, the
same file with the buffer sized for the swizzled layout passes.

A GB200 run of this branch is queued; result to follow in a comment.
With the script change, the multi-GPU CI job should now run both files
on this PR.

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

- The tolerance (`rtol = atol = 0.2`) is unchanged; with the fp32
reference it could be tightened, left for a separate change.
- The CI script change is one line and separable if you prefer it in its
own PR. Without it this PR's CI does not execute the test it fixes.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Tests**
* Updated validation for FP4 all-reduce fusion to account for swizzled
output sizing and fp32 accumulation before conversion.
* Added both FP4 all-reduce fusion test cases to the spawn-managed
multi-GPU communication test group, where they run under plain pytest
rather than MPI.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [07e46a8](https://github.com/flashinfer-ai/flashinfer/commit/07e46a81a7282c4fe518bc26715e2047ab57c3ac)

- **作者**: Cindy Zhang
- **时间**: 2026-11-23T18:11:28Z
- **提交信息**: test: strengthen b12x tail-N numerical and tactic coverage (#9871)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->
 Strengthen b12x tail-N regression coverage for NVFP4, MXFP4, and MXFP8.
• Replace the FP4 row-alignment test’s cosine-only check with exactly
representable inputs and an independent FP32 matmul reference. Validate
eager output and CUDA Graph replay with zero tolerance after casting the
reference to the output dtype.
• Validate every advertised FP4 tactic against the same reference and
check output-buffer guards.
• Extend the existing unified GEMM fuzzer with explicit b12x coverage on
SM120/121, using legal K dimensions and aligned/ unaligned N.

Preserves the existing six FP4 regression cases and the default
2,000-case fuzz budget. No production code changes.

## 🔍 Related Issues

<!-- Link any related issues here -->
Follow-up test improvements for #7182.
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
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets: tests/gemm/test_mm_fp4.py
tests/gemm/test_unified_gemm_fuzz.py

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
Zero tolerance is specific to the bounded, lossless inputs used by this
regression at K=256; it is not a general FP4 accuracy threshold.
Existing random-input tests remain in placeAll-tactic validation runs
only on the tail-N pass. The aligned → tail → aligned sequence continues
to exercise compiled-kernel cache reuse across output-store modes.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Tests**
* Strengthened matrix multiplication checks with exact reference
comparisons, including output and surrounding memory checks for aligned
and unaligned dimensions.
* Expanded validation of supported execution tactics and randomized
configurations across supported hardware and data formats, including
additional output shapes.
* Updated CUDA version requirements in tests to reflect the supported
minimums for NVFP4 and MXFP4.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [8b17e7b](https://github.com/flashinfer-ai/flashinfer/commit/8b17e7b0bfeb5c5fabe6daa2e4f26df4d006c824)

- **作者**: Cindy Zhang
- **时间**: 2026-11-23T18:10:56Z
- **提交信息**: test(prims-ts): cover inactive sink outputs and graph replay (#9865)

Check inactive output rows exactly while preserving the existing
numerical tolerance for active rows in uniform-Q and packed-Q persistent
decode. Replay one CUDA graph across active, inactive, and active
KV-length states, using distinct sentinels to detect stale output and
unintended writes.

Validation: 2 GPU tests passed on SM100 with CUDA 13.0 and CUTLASS DSL
4.8.0 in flashinfer-ci-cu130:20261106-54b9f685. Both assertion
sensitivity probes and changed-file pre-commit checks passed.

AI-assisted test changes and review with Codex.

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->
Strengthen the existing persistent decode regression for attention
sinks:

- Check inactive output rows exactly (`rtol=0`, `atol=0`). The previous
numerical tolerance could miss unintended writes such as 8 → 8.0625.
- Capture one CUDA graph and replay it with requests transitioning from
active → inactive → active. Use distinct output sentinels on each replay
to detect stale results and unintended writes.
- Preserve the independent FP32 reference checks for active rows and the
existing uniform-Q / packed-Q parameterization.

The existing eager execution also serves as capture warmup, and the
active-row mask is constructed once.

## 🔍 Related Issues

<!-- Link any related issues here -->
Follow-up test coverage for #9693.
## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [] I have run the hooks manually with `pre-commit run --all-files` and
fixed any reported issues.

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
reviewers may adjust): `tests/...`
`tests/attention/test_attention_ts_decode.py`
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

* **Tests**
* Expanded coverage for inactive-request handling during eager execution
and graph replay, including mixed and all-active request states.
* Added checks that inactive rows retain their sentinel values across
replay.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: cindyz <cindyz@nvidia.com>

### [72ea00b](https://github.com/flashinfer-ai/flashinfer/commit/72ea00b18cd13a00b7e04e9deff11ab53f46fbfd)

- **作者**: Lee Nau
- **时间**: 2026-11-23T18:08:46Z
- **提交信息**: test(autotuner): let the simulated CUDA in test_cupti_distributed accept a graph pool (#9894)

<!-- .github/pull_request_template.md -->

## 📌 Description

`main` fails
`tests/autotuner/test_cupti_distributed.py::test_cupti_fallback_is_collective[graph]`
since #9554 was merged.

#9554 made every profiling capture call `torch.cuda.graph(graph,
pool=profile_graph_pool())`. This test runs the real profiler against
simulated CUDA and CUPTI calls, so two things broke:

- Its fake `capture(graph)` took no `pool` argument. On a GPU runner
every rank fails with `capture() got an unexpected keyword argument
'pool'`, and rank 0 then times out in `monitoredBarrier`.
- `profile_graph_pool()` reached the real `torch.cuda.current_device()`
and `torch.cuda.graph_pool_handle()`. These are the only CUDA calls in
the test that weren't simulated. Without CUDA they fail one step
earlier.

This PR makes the fake `capture` accept `pool=`, and simulates
`current_device` and `graph_pool_handle` along with the other
`torch.cuda` calls the test already patches. No library code changes.

#9554's CI ran only its new
`tests/autotuner/test_profile_graph_pool.py`, so this wasn't caught
there. It currently fails targeted CI for any PR whose targets include
`tests/autotuner`, for example #9892.

## 🔍 Related Issues

Follow-up to #9554. No issue was filed.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

The hooks pass on the changed file (`pre-commit run --files ...`); the
full repository was not run.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
      Reason: a one-file test fix; targeted autotuner tests cover it.

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/autotuner`

"All tests are passing" stays unchecked until upstream CI has run.

**Local validation** (macOS arm64, Python 3.12.12, PyTorch 2.14.1 CPU,
pytest 9.2.0). The test runs real Gloo processes against the production
autotuner, loaded through a CPU import harness that stubs the native
modules:

- **`main` (`560d7e296`):** 1 failed, 1 passed. `[graph]` fails on ranks
1 and 2 inside `profile_graph_pool()` at `torch.cuda.current_device()`,
and rank 0 times out in `monitoredBarrier`.
- **This PR:** 2 passed.

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

AI-assisted: drafted and validated with Claude Code.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Tests**
* Updated CUDA test mocks to support graph capture pools and provide
device and graph-pool information.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [d6ab9eb](https://github.com/flashinfer-ai/flashinfer/commit/d6ab9eb1a43dd913fcdeb1caf69441aa6e3cefdd)

- **作者**: Eran Geva
- **时间**: 2026-11-23T17:26:40Z
- **提交信息**: perf(quantization): skip the scale zero fill in the per-token NVFP4 quant (linear layout) (#8815)

<!-- .github/pull_request_template.md -->

## 📌 Description

### Overview

`nvfp4_quant_and_per_token_scale_sm100` (the per-token NVFP4
quantization behind `nvfp4_quantize(..., per_token_activation=True)`)
allocates its scale tensor with `new_zeros`. That adds a fill kernel
launch before every quantization.

In the linear scale layout without a row permutation, the kernel writes
every scale byte: one per 16 values of each row, `[m, k / 16]` in total.
This PR allocates that tensor with `new_empty` in that case. The
swizzled layouts, which have padding that consumers read as zeros, and
the permuted path keep the zero fill.

vLLM uses this quantization for the MoE input of MiniMax-M3.1 (per-token
NVFP4 activations, linear layout). There the fill sits on the critical
path between the router and the quantization, once per layer.

### Claims

- **Bitwise unchanged.** The new test runs the quantization on scale
buffers prefilled with 0xAB and 0xFF and compares against a zero-filled
buffer. It covers fp16 and bf16, m from 1 to 512, k of 64, 3072 and
6144, and an all-zero block. The wrapper's output is also compared.
- **Faster:** one launch fewer per call. On GB300, CUDA-graph timed back
to back at k = 6144:

  | rows | before | after |
  |---|---|---|
  | 8 | 2.79 µs | 2.07 µs |
  | 64 | 2.88 µs | 2.16 µs |
  | 256 | 3.29 µs | 2.37 µs |

- **End to end:** see Validation.

### Validation

- `pytest tests/utils/test_fp4_quantize.py -k need_no_zero_fill`. On
GB300 against FlashInfer 0.7.2, which has the same Python wrapper and
kernel as `main`, the equivalent standalone check ran 576 comparisons
with 0 mismatches.
- **Serving:** MiniMax-M3.1 Flash on GB300 (driver 580.178.04), the
InferenceX recipe (TP4, DSpark K=7, NVFP4 KV, MoE input quantized per
token to NVFP4), with FlashInfer 0.7.2 patched with this change. Base
and change runs were alternated on one node, with nsys. "MoE head" is
the median per-layer span from the end of the all-reduce to the start of
the first MoE GEMM, which contains the router, the fill and the
quantization:

  | concurrency | MoE head per layer | per step (60 layers) |
  |---|---|---|
  | 1 | 8.00 → 6.66 µs | −80 µs (≈ 1.2% of the step) |
  | 8 | 14.94 → 14.69 µs | −15 µs |
  | 32 | 18.26 → 18.34 µs | no change |

At larger batches the fill overlaps with the router GEMM, so removing it
shows no gain there.

Rebased onto `main` 8baa822f8; the per-token quant kernel
(`csrc/nv_internal/tensorrt_llm/thop/fp4Quantize.cpp`) is unchanged
there since the version measured above.

## 🔍 Related Issues

None.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues. (Run on the changed files; all hooks
pass.)

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.). (The new test passed
against FlashInfer 0.7.2 on GB300; not yet run on a `main` build.)
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).

  Suggested CI test targets: `tests/utils/test_fp4_quantize.py`

## Reviewer Notes

AI assistance: the change, test and description were written with Claude
Code (Claude Opus 5.5). The submitter reviews every line before marking
it ready.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* Supported linear-scale per-token FP4 quantization avoids
zero-initializing its scale buffer, reducing setup work. Quantized
outputs and scale values remain consistent regardless of the buffer’s
initial contents across tested row counts and widths. Swizzled layouts
and cases with row-permutation mappings retain zero-initialized scale
buffers and their existing behavior.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Eran Geva <19514940+MrGeva@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [560d7e2](https://github.com/flashinfer-ai/flashinfer/commit/560d7e296484ce898d1ff508a02916f51ad2287d)

- **作者**: akshaver
- **时间**: 2026-11-23T08:16:51Z
- **提交信息**: feat(trace_apply): list packages and allow update of packages (#9476)

## 📌 Description

Two small additions for an inference engine that manages sealed kernel
packages
itself: it can ask which packages are installed, and it can release one
that a
CUDA graph has used.

**`installed_packages()`: which packages are installed**

An engine that routes its own call sites has to pair each Definition
with the
callable of the package FlashInfer actually installed. FlashInfer can
keep track of this
at no extra cost, allowing any caller to determine which kernel packages
are available.

**`release_packages(allow_frozen=True)`: release a package a CUDA graph
has used**

Prior to this PR, a setup-bearing binding could never be released:
captured graphs replay
against its state's addresses, so it was kept for the life of the
process.

With this change, a frozen kernel package binding can be torn down (see
`SetupBoundCallable.release()` and
`release_packages()`).

## 🔍 Related Issues

Follow-up to #8866 (sealed kernel packages) and #9408 (setup staleness).

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] Ran the hooks on the changed files: ruff check, ruff format, mypy
pass.

## 🧪 Tests

- [x] Test added: a capture-frozen binding refuses release without the
flag,
releases with it (teardown ran), and a fresh package for the same
Definition
  binds and serves afterwards.
- [x] Test added: `installed_packages()` lists the package that loaded
and not
one refused at load, returns the callable FlashInfer serves, keeps a
frozen
  package after a plain release, is empty after
`release_packages(allow_frozen=True)`, and gives a forked child a
binding of
  its own. It fails without the function.
- [x] Test added: a frozen binding released by its own
`release(allow_frozen=True)` leaves the registry: `setup_stats()` no
longer
lists it, `installed_packages()` returns a fresh binding that serves,
and a
plain `release_packages()` then empties the list. It fails without the
fix.
- [x] All tests pass locally: `tests/cpu/trace_apply/`, 166 passed, with
this
  branch's `trace_apply` laid over the 0.7.5 wheel on a GPU-less host.
- [x] Full-scope CI not required — contained to trace_apply.

  Suggested CI test targets: `tests/cpu/trace_apply/`

## 🔬 Experimental Track

Not experimental; section intentionally left unapplied.

## Reviewer Notes

The contract sentence that matters: with `allow_frozen`, the caller
guarantees
every graph that captured a call through the binding has been destroyed.
The
flag exists because only the engine knows that, never FlashInfer.

`installed_packages()` gets each callable through `import_entry`. In the
process that loaded the package it returns the same object
`load_packages`
did. In a forked child its first call imports the package there, because
the
parent's binding refuses by process id.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Frozen package bindings retained during CUDA graph capture can now be
released with an explicit opt-in, either individually or package-wide.
By default, captured bindings remain installed.
* Destroy any CUDA graphs that use a binding before opting in to release
it. After an individual binding is released, importing its entry again
creates a fresh binding.
* You can now list installed packages that have not been released, along
with their associated callables.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Code <noreply@anthropic.com>

### [ec47a9d](https://github.com/flashinfer-ai/flashinfer/commit/ec47a9d9d04fb9c909e6f446a983e39dfd2f7d69)

- **作者**: eigen
- **时间**: 2026-11-23T06:11:05Z
- **提交信息**: fix: make Cake tests pass on every internal-CI GPU lane (#9836)

Cake kernels were merged into FlashInfer without running internal CI.
The nightly internal CI never collects `tests/experimental` because it
is in `norecursedirs`, so the Cake tests had never run there. This PR
names every Cake test file explicitly in `/bot run`. It runs them on
B200, GB200, GB300 and VR NVL72 with the cu129 (torch 2.13), cu130
(torch 2.14.1) and cu134 (torch 2.15 nightly) images, plus the H100, RTX
PRO 6000, Spark and CPU lanes. It also fixes the failures found in
FlashInfer code. A compute-sanitizer cache-guard failure is fixed in the
internal CI scripts instead. An occasional port collision (`EADDRINUSE`)
in the shared multi-process test helper passed on retry. The first
commit (96ad8f0de) is empty and only carries the `/bot run` requests, so
it disappears on squash merge.

## Fixes

**d664ce455: fix(tests): make Cake tests pass on every internal-CI GPU
lane**

Product fix:
- `flashinfer/moe_ep/core/bf16_stage.py`: an empty strided view is
reported as contiguous but has a non-unit inner stride, which DLPack
rejects. Empty planes now get a unit inner stride. Before this fix, the
zero-token rank raised an error in fused staging.

Test fixes:
- `kimi_k3_latent_moe`: `GreenContext` in torch 2.13 has no constructor,
so the test uses `GreenContext.create()`.
- `kimi_k3_attn_res`: on sm_100a with 152 SMs (GB200) there is no `_clc`
route for the (4096, 6) cell, so the test checks the static program
there.
- `minimax_h3_varlen_attention`: the tail-first shapes assumed 74
clusters (B200). The shape now comes from the device grid (76 on GB200).
- `mega_native_topk_reduce_multirank`: the test selects the legacy NVFP4
kernel, which is the one the legacy tuner tunes. A forward failure is
now shared across ranks, so an error on one rank fails the test instead
of hanging the other ranks.
- Six Cake comm tests: pass `device_id` to `init_process_group` so that
backends that do not infer the device bind the right GPU.
- `generated_mega_moe`: graph edges are read through the driver's
`cuGraphGetEdges_v2`. cuda-bindings 13.0 to 13.2 (cu130 image) return
edge data from a freed buffer, so the edge types were random. This is
fixed upstream in cuda-bindings 13.3.0.
- `cake_vsa_sm90`: skip the FP8 GQA queue test on non-SM90 GPUs, as its
sibling tests already do.
- `stepfun_moe`: use the shared `cake_profiler` capture. It retries and
skips when a profiler session loses its CUDA records.

**8a6ae91fa: fix(nvfp4_attention): require CUDA 13.0 for the SM100/SM103
quantizer** (product fix)
- On sm_100a and sm_103a, ptxas 12.9 miscompiles the E2M1 decode
`cvt.rn.f16x2.e2m1x2` of bytes 2 and 3 of a `mov.b32`-packed register.
It emits `F2FP.F16.E2M1.UNPACK_B Rd, RZ.B2/RZ.B3`, which decodes the
zero register. With CUDA 12.9, NVFP4 attention ran and silently returned
wrong values. ptxas 13.0 compiles it correctly.
- `min_cuda` is now 13.0 in both quantizer `build.json` entries, so the
JIT refuses older toolkits. The package tests skip below this floor.
- A SASS sweep of every sm_100a/sm_103a FlashInfer unit that decodes
E2M1 found no other affected kernel.

**a4ac89010: fix(cake_mok_bf16): use a blocking barrier when creating
the workspace** (product fix)
- With the default nccl2 backend in torch 2.15 nightly, every rank hung
in `dist.barrier(async_op=True, device_ids=...).block_current_stream()`.
`blockCurrentStream` enqueues a spin kernel that only a future callback
releases. The nccl2 barrier is host-blocking, and its `getFuture()`
synchronizes the current stream first, so each waits on the other.
- The hang reproduces in pure torch. The legacy NCCL backend does not
hang.
- A blocking `dist.barrier` keeps the same setup semantics: one host
wait per workspace.

**c680b32d1: fix(kimi_k3_latent_moe): refuse an oversized cooperative
launch under capture** (product fix)
- If a cooperative route is captured on a green context with fewer SMs
than its grid needs, the capture must fail.
- Driver 580.x (CUDA 13.0, B200/GB200 lanes) refuses the eager launch
but records it under stream capture. The result is a graph that cannot
run. Driver 620 (CUDA 13.5, GB300) and the CUDA 13.4 forward-compat
driver in the cu134 image refuse at capture.
- Under capture only, the launch now compares the SM count of the
capture stream's context (`cuStreamGetCtx` + `cuCtxGetDevResource`) with
its minimum and refuses before launching. The eager path is unchanged.

**7d585a05f: fix(moe_ep): disable NVSHMEM NVLS for the two-node BF16
rank-major test** (test launcher and docs)
- On two VR NVL72 nodes, NVSHMEM's default NVLS setup runs out of
internal teams (`No more teams available (max = 128)`), so every rank
fails during initialization. The ranks share one NVLink domain and use
the direct peer-memory path.
- With `NNODES` above 1, `tests/moe_ep/run_tests.sh bf16-rank-major` now
exports `NVSHMEM_DISABLE_NVLS=1` and `NVSHMEM_REMOTE_TRANSPORT=none`
unless they are set. The test docstring and its design doc describe the
settings for direct `torchrun` launches.

## Validation

All runs are internal CI via `/bot run`:
- Pipeline 84475161 at head c680b32d ran 15 files:
`test_cake_kimi_k3_latent_moe`, the six `test_mok_bf16*` files, the six
Cake comm tests, `test_mega_native_topk_reduce_multirank` and
`test_bf16_stage`. They passed on B200, GB200 and GB300 with cu129,
cu130 and cu134, and on VR NVL72 with cu134. All lanes were green,
including the multi-GPU and multi-node jobs, H100, RTX PRO 6000, Spark
and CPU.
- Pipeline 84442815 at 8a6ae91f ran the other touched files:
`kimi_k3_attn_res`, `minimax_h3_varlen_attention`, `stepfun_moe`,
`stepfun_moe_api`, `cake_vsa_sm90`, `generated_mega_moe`,
`nvfp4_attention` and `nvfp4_attention_api`. They passed on every lane,
and later commits do not touch them.
- On a separate B200 node, the full `kimi_k3_latent_moe` file gives 267
passed / 28 skipped on each image (3 tests failed before the fix). The
4-rank `mok_bf16` tests pass under both NCCL backends.
- `test_moe_ep_bf16_rank_major_cuda_multirank` on sm_107a ran on two VR
NVL72 nodes in one NVLink domain (8 ranks), with the cu134 CI image and
with a CUDA 13.5 image. With `NVSHMEM_DISABLE_NVLS=1` and
`NVSHMEM_REMOTE_TRANSPORT=none` exported, every rank reports 52 passed;
without them, NVSHMEM initialization fails on every rank. The updated
`run_tests.sh` target was not itself rerun on two nodes; it exports the
same two settings.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved reliability of distributed GPU operations through more
dependable setup synchronization and improved handling of empty tensor
inputs.
* CUDA Graph captures now avoid cooperative launches when available
device resources are insufficient.
* **Compatibility**
* NVFP4 attention libraries for certain GPU architectures now require
CUDA 13.0 or later. Tests now skip when the installed CUDA toolkit does
not meet the required version.
* **Documentation**
  * Clarified environment requirements for multi-node BF16 tests.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [7b1f440](https://github.com/flashinfer-ai/flashinfer/commit/7b1f4400b1129066705fb5c5524225cfce422f10)

- **作者**: Perkz Zheng
- **时间**: 2026-11-23T06:10:15Z
- **提交信息**: perf(prims-ts): compute each work tile's visible K range once for softmax masking (#9846)

<!-- .github/pull_request_template.md -->

## 📌 Description

Every Prims-TS softmax now chooses between its masked and unmasked path
the same way. It computes the work tile's visible K range once (in the
task cache, SMEM or the work tile), then makes one comparison per K
tile. Before this PR, several paths rebuilt their bounds on every tile,
reloaded request metadata from GMEM, or masked every tile.

- **Shared helpers** (`kernels/mask.py`):
- `unmasked_kv_tile_range` / `kv_tile_in_range` (plus a packed one-word
form) build and test the range.
- `kv_tile_needs_right_mask` / `kv_tile_is_fully_visible` are the
key-space forms, for bounds already live in the loop.
- **FMHA context:**
- Variable-window, sliding-window and head-paired varlen LOOP masks
cache a per-warp tile range in SMEM, packed into one 32-bit word. They
used to mask every tile.
- Query-paired causal and packed dense-K use the shared right-bound
test.
  - TAIL masks are unchanged.
- **FMHA decode:**
- Grouped per-row causal and sliding-window CTAs cache their visible K
interval (end, plus begin for a window) in the task cache.
- The FP8 Q128 streamed Swaps path compared every score on every tile;
it now masks only boundary tiles, in one pass per Q32 band.
- **MLA decode:**
- When the rows of one tile see different prefixes, the tile caches its
first row's K prefix once. This covers causal MTP and packed-Q
(`qo_indptr`), in both 1CTA and 2CTA, and context-parallel causal in
2CTA, which previously masked every tile. Per-row bounds load only on
masked tiles.
- The 1CTA dense test drops a `seq_len % tile` term that masked every
tile of an unaligned request.

The D256 LDTM.STAT context softmax is the one deliberate exception to
"cache once". Every loop-carried form of its causal bound regressed
3–8%, because ptxas copied the 128-register S tile on every tile. So
that bound is rebuilt each tile from values already in registers. That
compiles to main's instruction count. The reason is recorded in the code
and in the commit message.

**Performance** (B300, `253986e2d` vs this branch at `ba0560642`,
outputs bitwise identical in every case). These come from the new
[mask-tile A/B
suite](https://github.com/PerkzZheng/flashinfer-prims-ts-validation/blob/main/docs/mask_tiles.md):
33 cases, 5 interleaved rounds, median paired ratio, geomean −2.98%.

| Case | main µs | PR µs | Δ |
| --- | ---: | ---: | ---: |
| context, sliding window 1024, S=8K | 135.2 | 108.0 | −20.1% |
| context, sliding window 4000, S=8K | 351.1 | 267.6 | −23.7% |
| context, variable window 2048, S=4K | 211.9 | 179.0 | −15.6% |
| context, packed sliding window 2048, S_kv > S_q | 591.1 | 459.8 |
−22.2% |
| MLA H128, context parallel 8×64, packed-Q causal | 120.2 | 118.1 |
−2.1% |
| MLA H128, context parallel 8×64, causal MTP (SQ4) | 141.5 | 139.7 |
−1.2% |
| context, paged shifted causal D256 (4 shapes) | — | — | −0.21% …
+0.02% |
| worst case of the 33 (MLA H16 packed-Q causal) | 54.7 | 55.2 | +0.9% |

Measured separately on the same GPU, interleaved against main:
- FP8 Q128 streamed Swaps path, forced: −3.3% / −4.5%.
- `flashinfer_benchmark.py` MLA matrix, 70 cases: geomean −0.14%. The 11
cases above +0.5% were re-run for 8 rounds; all are ≤ +0.9%.
- D256 shifted-causal paged context, 6 shapes × 5 rounds: −0.9% … +0.2%.

## 🔍 Related Issues

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
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/attention/test_attention_ts_context.py
tests/attention/test_attention_ts_decode.py
tests/attention/test_attention_ts_mla_decode.py
tests/attention/test_attention_ts_mla_cp.py
tests/attention/test_attention_ts_sparse_mla.py
tests/attention/test_attention_ts_block_sparse.py
tests/attention/test_attention_ts_features.py`

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

- **Validation.** On B300 (SM103), on `ba0560642` (decode, MLA and the
other kernel files are byte-identical to the tested `fd4f258c6` for the
suites run there):

  | Suite | Result |
  | --- | --- |
  | context | 401/401 |
  | decode | 1211 passed, 96 skipped |
  | MLA decode | 199/199 |
  | MLA context parallel | 7/7 |
  | sparse MLA | 210/210 |
  | block-sparse | 241 passed, 1 skipped |
  | features | 21/21 |

  New tests:
- one exhaustive host test: the plain and packed tile ranges (the packed
word read back as a signed 32-bit register) select exactly the tiles the
per-tile visibility test accepts, and bounds past 16 bits only shrink
the range;
- a GPU test that forces the FP8 Q128 streamed Swaps path, which no
existing test reached.
- **Lint.** pre-commit does not run on my machine. I ran ruff check,
ruff format and `git diff --check` on the changed files instead.
- **Overlap with #9475.** That PR also changes the multi-token Swaps
decode mask in `fmha_decode_resources/tmem_s.py`. Whichever lands second
will need a rebase there.
- **Review fixes.** The packed LOOP range now clamps both bounds to
65535 and decodes the upper field unsigned (`289b7fb04`). Before, bounds
of 65536+ tiles wrapped into the other field, and the fixed sliding
window's open right bound decoded as −1, so every LOOP tile of a fixed
window was masked; the window rows above are that fix. `caf889d48`
removes paths this PR had duplicated (a LOOP-only right mask, a second
causal mask helper, per-call-site decode dispatch, two MLA prefix
predicates); the non-LDTM query-paired causal mask is main's helper
again, since rebuilding it on the LOOP causal-end helpers cost 1.6–1.9%
on D256.
- **Rebase onto #9641.** The MLA commit was rebased onto the
context-parallel bounds refactor. Rank-local causal prefixes, like
global ones, never decrease along the flat query rows, so the first
row's prefix bounds every row in the tile.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved attention masking for variable-length, causal,
sliding-window, and packed-key configurations, including cases where
query rows have different visible key ranges.
* Fully visible key tiles can now skip unnecessary masking across
supported attention paths.
* **Tests**
* Added coverage for FP8 causal decode with ragged key lengths and
expanded checks for visible-tile ranges.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Perkz Zheng <67892460+PerkzZheng@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [637f9c5](https://github.com/flashinfer-ai/flashinfer/commit/637f9c5309093704b9500495068627761f6ebc97)

- **作者**: Guangyun Han
- **时间**: 2026-11-23T02:01:29Z
- **提交信息**: feat(mla): fuse native NVFP4 SM120 sparse prefill (#9356)

## 📌 Description

Extend the sparse MLA mega API to native NVFP4 caches and port native
prefill to CuTe C++ operations and CUTLASS barriers. IO warps gather KV
and transpose/requantize V; math warps execute QK, online softmax and
PV. Non-RoPE features use block-scaled FP4 with a BF16 RoPE tail. Fused
and unfused specializations share the prefill implementation. NVFP4 mega
execution requires a prefill plan; decode plans are explicitly rejected
here and supported separately in #9439. Ordinary NVFP4 decode is
unchanged.

### Built-in prefill benchmark

RTX PRO 6000 Blackwell Server Edition, CUDA 13.4, SM120. Baseline: FP8
parent `5272e33c5b7ca3765f26c38714b3bf4db0ee47c9`; PR:
`0548948996795c46e082f52ea93d3a09f62ff7c9`. Warm-L2 CUDA Graph replay;
100 ms warmup / 500 ms measurement. GPU runs are serialized. Both
original builtin shapes: B=1, Q=128, H=128, D=512, KV=8192, page=64, no
secondary cache. Values are microseconds. Attention-only and
complete-pipeline comparisons are separate; the complete baseline
includes Q RoPE, original native NVFP4 attention, inverse output RoPE
and FP8 quantization, timed as one sequence. Only benchmark/transform
helpers are backported to the parent.

| Selected KV | Parent attention | PR non-mega attention | Parent / PR
attention | Parent separate kernels | PR mega | Parent separate / mega |
|---:|---:|---:|---:|---:|---:|---:|
| 128 | 46.65 | 39.89 | 1.170× | 65.49 | 43.18 | 1.517× |
| 512 | 144.65 | 119.86 | 1.207× | 163.49 | 124.99 | 1.308× |

### [83a5b03](https://github.com/flashinfer-ai/flashinfer/commit/83a5b03c44b8310e0f7f029235a33bf8403d8624)

- **作者**: feih-nv
- **时间**: 2026-11-23T01:52:12Z
- **提交信息**: fix(comm): fp32 accumulation in the deferred MoE finalize all-reduce (#9749)

## 📌 Description

`moefinalize_allreduce_fusion_kernel_oneshot_lamport` summed the top-k
weighted expert outputs and the shared expert in T (bf16 / fp16),
rounding after every term. It now accumulates in fp32 and rounds once
for the Lamport store, as the trtllm-gen MoE finalize kernels
(`csrc/fused_moe/trtllm_backend/trtllm_fused_moe_dev_kernel.cu`) do when
the finalize is not deferred. The sibling
`moereduction_allreduce_fusion_kernel_oneshot_lamport` in the same
header still rounds per term and is not changed here. Port of
NVIDIA/TensorRT-LLM#16778 (2801e9478), where the per-term rounding
showed up as lower routed-output accuracy.

## 🔍 Related Issues

NVIDIA/TensorRT-LLM#16778.

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

- [ ] Tests have been added or updated as needed. (None: the existing
finalize test covers the kernel; see below.)
- [ ] All tests are passing (`unittest`, etc.). (7/8 on 4-GPU nodes; the
one failure is on main too, see below.)
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust):
`tests/comm/test_trtllm_moe_allreduce_fusion_finalize.py
tests/comm/test_trtllm_moe_allreduce_fusion.py`

`tests/comm/test_trtllm_moe_allreduce_fusion_finalize.py` and
`tests/comm/test_trtllm_moe_allreduce_fusion.py` on 4-GPU nodes (CUDA
13.0 CI container), this branch vs unmodified main `c032cb58be`:

| GPU | main | this PR |
|---|---|---|
| GB200 (SM100) | 7/8 | 7/8 |
| GB300 (SM103) | 7/8 | 7/8 |

The one failure on both sides is
`test_trtllm_moe_finalize_allreduce_fusion[dtype1-4]` (bf16, 4 ranks), a
pre-existing tolerance failure: a few elements whose value is near zero
differ from the test's bf16 reference by more than `atol=0.2` once four
ranks are summed. Replaying the arithmetic with the test's seeded inputs
gives 9 such elements of 114,688 on main and 6 with this PR; the other
seven cases have none.

Found while investigating that case, not fixed here: the test allocates
`scale_out` at the linear size (`token_num * hidden_dim / 16` elements,
14 KB) while the kernel writes SWIZZLED_128x4 as the API documents (up
to 57 KB), so every call writes out of bounds inside PyTorch's pool. A
follow-up test PR sizes the buffer and switches the reference to fp32
accumulation, which makes the bf16 4-rank case pass with this kernel.

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

Kernel-only change in
`include/flashinfer/comm/trtllm_moe_allreduce_fusion.cuh`; the test is
unchanged.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved numerical precision when combining routed and shared expert
outputs in MoE results.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [6046d47](https://github.com/flashinfer-ai/flashinfer/commit/6046d47f2907e7abb89c7061e63c2f7766c00446)

- **作者**: eigen
- **时间**: 2026-11-23T01:29:10Z
- **提交信息**: perf(mla): Cake FP8 page-64 decode merges the splits of one or two query rows over up to 128 CTAs per row (#9858)

The Cake backend of `trtllm_batch_decode_with_kv_cache_mla` runs
DeepSeek MLA decode on Blackwell. The family now has 24 device programs:
the 23 shipped before, which this PR does not change, plus one new
program, the head build of the FP8 page-64 split reducer. This PR
delivers the split-KV route for an FP8 KV cache with page size 64.
Before this PR, that route's split reducer kept at most 16 CTAs busy per
query row. The new head build spreads one query row's 128 heads over up
to 128 CTAs (min(128, SMs / rows)). It writes the same output and LSE
bits as the existing reducer. The head build runs for one or two query
rows (batch × q_len ≤ 2) when the request has at least 8 KV splits per
query row and a CTA's partial rows fit in its shared-memory stage.
Otherwise, the existing reducer runs as before. Split counts do not
change. The PR changes 32 shapes on B200 and 32 on GB300 (batch × q_len
of 1×1, 1×2 or 2×1; max KV length 1856 to 262144). On these shapes, the
geomean speedup against the previous Cake version (FlashInfer main
1b4d210d) is 1.148x on B200 (min 1.001x, max 1.591x) and 1.145x on GB300
(min 1.025x, max 1.571x). Against the fastest non-Cake backend, the
geomean is 0.924x on B200 (min 0.799x, max 1.033x) and 0.890x on GB300
(min 0.756x, max 1.067x). `backend="auto"` keeps choosing the fastest
tuned backend for each shape.

The kernel's other Cake programs serve BF16 page-32/64 decode (including
the split-KV route with up to 64 splits), FP8 page 32, the FP8 page-64
producers and the existing reducer, and a generic tail for other shapes,
and the family ships on sm_100a (B200) and sm_103a (GB300).

**Table: explicit `backend="cake"` on every shape this PR changes.**
GPUs: NVIDIA B200 (sm_100a, 148 SMs) and NVIDIA GB300 (sm_103a, 152
SMs). Software: CUDA 13.5 JIT (nvcc 13.5) and torch 2.14.1+cu130. Every
row uses an FP8 KV cache with page size 64. "KV length" is the maximum
KV length (max_seq_len). The lengths are uniform or varied. "Splits" is
the number of planned KV splits, which this PR does not change.
"Previous Cake" is FlashInfer main 1b4d210d. "Fastest non-Cake" is the
faster of tuned trtllm-gen and cute-dsl, measured on the same GPU in the
same rounds, with the faster backend in parentheses. Timing is the CUPTI
kernel span over CUDA-graph replay, with L2 flushed before every
iteration. Each value is the median of the per-round medians over 6
rounds. Speedup = baseline / this PR; >1 means this PR is faster.

| GPU | batch | q_len | KV length | lengths | splits | previous Cake
(us) | fastest non-Cake (us) | this PR (us) | speedup vs previous Cake |
speedup vs fastest non-Cake |
|---|---|---|---|---|---|---|---|---|---|---|
| B200 | 1 | 1 | 1856 | uniform | 8 | 11.216 | 11.569 (cute-dsl) |
11.200 | 1.001x | 1.033x |
| B200 | 1 | 1 | 2048 | uniform | 8 | 11.216 | 10.591 (cute-dsl) |
11.104 | 1.010x | 0.954x |
| B200 | 1 | 1 | 2304 | varied | 9 | 11.504 | 11.152 (cute-dsl) | 11.136
| 1.033x | 1.001x |
| B200 | 1 | 1 | 2560 | uniform | 10 | 11.951 | 11.504 (cute-dsl) |
11.392 | 1.049x | 1.010x |
| B200 | 1 | 1 | 3072 | varied | 12 | 12.240 | 11.424 (cute-dsl) |
11.600 | 1.055x | 0.985x |
| B200 | 1 | 1 | 4096 | uniform | 16 | 13.216 | 11.408 (cute-dsl) |
11.984 | 1.103x | 0.952x |
| B200 | 1 | 1 | 4096 | varied | 16 | 13.104 | 11.568 (cute-dsl) |
11.712 | 1.119x | 0.988x |
| B200 | 1 | 1 | 16384 | uniform | 64 | 26.049 | 14.768 (cute-dsl) |
16.944 | 1.537x | 0.872x |
| B200 | 1 | 1 | 32768 | uniform | 74 | 31.248 | 17.392 (cute-dsl) |
20.176 | 1.549x | 0.862x |
| B200 | 1 | 1 | 32768 | varied | 74 | 30.112 | 15.681 (cute-dsl) |
18.927 | 1.591x | 0.828x |
| B200 | 1 | 1 | 65536 | uniform | 74 | 34.544 | 20.416 (cute-dsl) |
23.456 | 1.473x | 0.870x |
| B200 | 1 | 1 | 131072 | uniform | 74 | 41.072 | 28.128 (cute-dsl) |
29.808 | 1.378x | 0.944x |
| B200 | 1 | 1 | 131072 | varied | 74 | 37.280 | 24.128 (cute-dsl) |
25.936 | 1.437x | 0.930x |
| B200 | 1 | 1 | 262144 | uniform | 74 | 54.560 | 40.192 (cute-dsl) |
42.816 | 1.274x | 0.939x |
| B200 | 1 | 2 | 3904 | uniform | 16 | 14.079 | 12.848 (cute-dsl) |
13.504 | 1.043x | 0.951x |
| B200 | 1 | 2 | 4096 | uniform | 16 | 14.272 | 12.656 (cute-dsl) |
13.664 | 1.044x | 0.926x |
| B200 | 1 | 2 | 4096 | varied | 16 | 14.048 | 12.528 (cute-dsl) |
13.489 | 1.041x | 0.929x |
| B200 | 1 | 2 | 16384 | uniform | 37 | 21.808 | 15.744 (cute-dsl) |
19.280 | 1.131x | 0.817x |
| B200 | 1 | 2 | 32768 | uniform | 37 | 24.623 | 20.608 (cute-dsl) |
21.968 | 1.121x | 0.938x |
| B200 | 1 | 2 | 32768 | varied | 37 | 22.784 | 18.144 (cute-dsl) |
20.209 | 1.127x | 0.898x |
| B200 | 1 | 2 | 65536 | uniform | 37 | 30.399 | 26.640 (cute-dsl) |
27.744 | 1.096x | 0.960x |
| B200 | 1 | 2 | 131072 | uniform | 37 | 41.488 | 38.239 (cute-dsl) |
38.832 | 1.068x | 0.985x |
| B200 | 1 | 2 | 131072 | varied | 37 | 34.320 | 30.784 (cute-dsl) |
31.712 | 1.082x | 0.971x |
| B200 | 2 | 1 | 3904 | varied | 16 | 13.984 | 12.176 (cute-dsl) |
13.312 | 1.050x | 0.915x |
| B200 | 2 | 1 | 4096 | uniform | 16 | 14.352 | 12.704 (cute-dsl) |
13.760 | 1.043x | 0.923x |
| B200 | 2 | 1 | 4096 | varied | 16 | 14.144 | 12.032 (cute-dsl) |
13.392 | 1.056x | 0.898x |
| B200 | 2 | 1 | 16384 | uniform | 37 | 22.816 | 16.175 (cute-dsl) |
20.256 | 1.126x | 0.799x |
| B200 | 2 | 1 | 32768 | uniform | 37 | 25.968 | 21.169 (cute-dsl) |
23.328 | 1.113x | 0.907x |
| B200 | 2 | 1 | 32768 | varied | 37 | 25.344 | 19.808 (cute-dsl) |
22.608 | 1.121x | 0.876x |
| B200 | 2 | 1 | 65536 | uniform | 37 | 32.495 | 27.488 (cute-dsl) |
29.887 | 1.087x | 0.920x |
| B200 | 2 | 1 | 131072 | uniform | 37 | 45.312 | 39.343 (cute-dsl) |
42.544 | 1.065x | 0.925x |
| B200 | 2 | 1 | 131072 | varied | 37 | 37.855 | 32.320 (cute-dsl) |
35.136 | 1.077x | 0.920x |
| GB300 | 1 | 1 | 1856 | uniform | 8 | 10.720 | 11.008 (cute-dsl) |
10.320 | 1.039x | 1.067x |
| GB300 | 1 | 1 | 2048 | uniform | 8 | 10.592 | 10.240 (cute-dsl) |
10.336 | 1.025x | 0.991x |
| GB300 | 1 | 1 | 2304 | varied | 9 | 10.992 | 10.480 (cute-dsl) |
10.464 | 1.050x | 1.002x |
| GB300 | 1 | 1 | 2560 | uniform | 10 | 11.248 | 11.232 (cute-dsl) |
10.704 | 1.051x | 1.049x |
| GB300 | 1 | 1 | 3072 | varied | 12 | 11.456 | 10.688 (cute-dsl) |
10.640 | 1.077x | 1.005x |
| GB300 | 1 | 1 | 4096 | uniform | 16 | 12.144 | 10.672 (cute-dsl) |
11.136 | 1.091x | 0.958x |
| GB300 | 1 | 1 | 4096 | varied | 16 | 12.144 | 10.624 (cute-dsl) |
11.040 | 1.100x | 0.962x |
| GB300 | 1 | 1 | 16384 | uniform | 64 | 24.592 | 13.616 (cute-dsl) |
15.968 | 1.540x | 0.853x |
| GB300 | 1 | 1 | 32768 | uniform | 76 | 30.048 | 15.792 (cute-dsl) |
19.632 | 1.531x | 0.804x |
| GB300 | 1 | 1 | 32768 | varied | 76 | 28.800 | 14.480 (cute-dsl) |
18.336 | 1.571x | 0.790x |
| GB300 | 1 | 1 | 65536 | uniform | 76 | 33.168 | 18.624 (cute-dsl) |
22.640 | 1.465x | 0.823x |
| GB300 | 1 | 1 | 131072 | uniform | 76 | 39.872 | 25.200 (cute-dsl) |
29.008 | 1.375x | 0.869x |
| GB300 | 1 | 1 | 131072 | varied | 76 | 37.024 | 22.504 (cute-dsl) |
26.304 | 1.408x | 0.856x |
| GB300 | 1 | 1 | 262144 | uniform | 76 | 51.872 | 36.608 (cute-dsl) |
41.264 | 1.257x | 0.887x |
| GB300 | 1 | 2 | 3904 | uniform | 16 | 13.296 | 12.240 (cute-dsl) |
12.640 | 1.052x | 0.968x |
| GB300 | 1 | 2 | 4096 | uniform | 16 | 13.184 | 11.808 (cute-dsl) |
12.704 | 1.038x | 0.929x |
| GB300 | 1 | 2 | 4096 | varied | 16 | 13.120 | 11.840 (cute-dsl) |
12.640 | 1.038x | 0.937x |
| GB300 | 1 | 2 | 16384 | uniform | 38 | 21.040 | 14.224 (cute-dsl) |
18.672 | 1.127x | 0.762x |
| GB300 | 1 | 2 | 32768 | uniform | 38 | 23.520 | 18.192 (cute-dsl) |
21.344 | 1.102x | 0.852x |
| GB300 | 1 | 2 | 32768 | varied | 38 | 21.856 | 16.000 (cute-dsl) |
19.568 | 1.117x | 0.818x |
| GB300 | 1 | 2 | 65536 | uniform | 38 | 29.247 | 23.264 (cute-dsl) |
26.832 | 1.090x | 0.867x |
| GB300 | 1 | 2 | 131072 | uniform | 38 | 38.528 | 31.984 (cute-dsl) |
36.032 | 1.069x | 0.888x |
| GB300 | 1 | 2 | 131072 | varied | 38 | 33.904 | 28.016 (cute-dsl) |
31.408 | 1.079x | 0.892x |
| GB300 | 2 | 1 | 3904 | varied | 16 | 13.168 | 11.600 (cute-dsl) |
12.480 | 1.055x | 0.929x |
| GB300 | 2 | 1 | 4096 | uniform | 16 | 13.360 | 11.760 (cute-dsl) |
12.912 | 1.035x | 0.911x |
| GB300 | 2 | 1 | 4096 | varied | 16 | 13.168 | 11.552 (cute-dsl) |
12.640 | 1.042x | 0.914x |
| GB300 | 2 | 1 | 16384 | uniform | 38 | 21.872 | 14.784 (cute-dsl) |
19.552 | 1.119x | 0.756x |
| GB300 | 2 | 1 | 32768 | uniform | 38 | 25.120 | 19.168 (cute-dsl) |
22.800 | 1.102x | 0.841x |
| GB300 | 2 | 1 | 32768 | varied | 38 | 25.136 | 18.672 (cute-dsl) |
22.608 | 1.112x | 0.826x |
| GB300 | 2 | 1 | 65536 | uniform | 38 | 31.616 | 24.416 (cute-dsl) |
29.056 | 1.088x | 0.840x |
| GB300 | 2 | 1 | 131072 | uniform | 38 | 43.456 | 35.648 (cute-dsl) |
40.992 | 1.060x | 0.870x |
| GB300 | 2 | 1 | 131072 | varied | 38 | 38.224 | 31.016 (cute-dsl) |
35.696 | 1.071x | 0.869x |


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added an additional reducer option for FP8 page-64 MLA workloads on
supported GPU architectures. The app selects it when the query-row,
split-count, and resource limits are met; other workloads continue to
use the existing reducer.
* **Bug Fixes**
* Improved consistency of normalized outputs and log-sum-exp values when
combining split results, including cases with empty splits.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-11-24
**监控日期**: 2026-11-23
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4852
- **最后更新**: 2026-11-24T03:53:35Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Keith

## AI分析总结

## 提交分析总结（hao-ai-lab/FastVideo，2025-11-19 第 1/1 批）

### 1. 主要更新类型
- **Bug 修复**：核心是修复流式（Streaming）会话的终止逻辑问题，属于稳定性与协议正确性层面的修复。

### 2. 关键变更点及与项目方向的关系
- 修复了流式会话未按文档约定终止的问题，确保会话能正确应用三个终止条件：
  - `segment_cap`（分段数量上限）
  - `session_timeout`（会话超时）
  - `error frames`（错误帧触发终止）
- 这意味着此前流式接口的实际行为与文档承诺存在偏差（如会话可能挂起、不释放资源、或异常状态不返回），本次修复使实现与文档对齐。
- FastVideo 作为视频生成/推理框架，其对外 API（文档、Cookbook、Uniserve 等集成生态）的可靠性是项目核心竞争力之一，流式会话是长耗时视频生成任务的关键交互模式。

### 3. 对项目的影响和潜在意义
- **稳定性提升**：避免流式会话泄漏（不超时、不封顶导致资源占用），降低服务端长连接堆积风险。
- **API 契约可信度**：实现与文档一致，增强开发者信任，利好 Cookbook 示例与第三方集成（Uniserve、Dreamverse Harness）。
- **生产可用性**：错误帧正确终止意味着客户端能及时感知失败并重试，对在线视频生成服务尤为重要。

### 4. 值得关注的技术点
- 三个终止条件（数量、时间、错误）需协同触发且互斥优先级需明确，是典型的流式状态机设计问题。
- 协同作者来自社区（Co-authored-by 标注），体现项目采用 PR 合并（#2072）的协作流程，修复来自实际使用反馈的可能性较高。
- 关注后续是否有配套的测试用例覆盖这三条终止路径，以及是否涉及协议版本兼容问题。

### 5. 结合项目背景对发展的影响
- 从 README 看，FastVideo 正构建以文档、Cookbook 和周边生态（Uniserve、Dreamverse Harness）为核心的服务化体系，**流式会话的正确终止是服务化/在线推理路线的基础工程**。
- 此类修复虽小，但直接关系到长耗时视频任务的用户体验与服务器资源效率，属于"让框架从能跑"走向"能在生产稳定跑"的关键一步，为后续更复杂的流式功能（如增量生成、多轮会话）奠定可靠性基础。
- 建议持续关注该仓库在流式接口、会话管理和错误处理上的后续提交，以判断其服务化战略的推进节奏。

## 详细提交记录

### [a7eb340](https://github.com/hao-ai-lab/FastVideo/commit/a7eb3401de33d61530c09bcdb6ced12de322b719)

- **作者**: Keith
- **时间**: 2026-11-23T05:10:50Z
- **提交信息**: [bugfix] Streaming: end sessions with the documented segment_cap, session_timeout and error frames (#2072)

Co-authored-by: Aryan Kumar <156166681+aryan5v@users.noreply.github.com>

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-11-24
**监控日期**: 2026-11-23
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34968
- **最后更新**: 2026-11-24T06:00:41Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Sara Han

## AI分析总结

### 1. 主要更新类型
- **重构与代码整理**：将模块从 `P-H3-Image` 重命名为 `P-Image-OSS`，并移动相关组件（如自编码器、条件嵌入器、模块化流水线、文档和测试）到新命名空间。
- **文档更新**：对重命名相关的文档说明进行了补充和澄清。
- **弃用机制引入**：保留旧的 `p_h3_image` 模块作为弃用别名，以确保向后兼容。

### 2. 关键变更点及其与项目整体方向的关系
- **命名规范化**：此变更旨在提升代码库的命名一致性和可读性，符合 diffusers 项目持续优化模块化架构的方向。重命名使组件名称更简洁直观，有助于降低开发者理解成本。
- **模块化流水线整合**：移动 `autoencoder`、`condition embedder` 和 `modular pipeline` 等核心组件，体现了项目对扩散模型流水线灵活性的重视，为未来功能扩展（如新模型集成）预留空间。
- **兼容性保留**：通过弃用别名而非直接删除，维护了现有用户和下游代码的稳定性，符合开源项目渐进式演进的实践。

### 3. 对项目的影响和潜在意义
- **提升可维护性**：清晰的命名和模块划分将减少代码冗余和潜在冲突，加速后续功能开发与调试。
- **促进社区协作**：规范化的命名约定使新贡献者更容易定位和修改代码，可能提高开源参与度。
- **降低迁移风险**：弃用策略允许用户平滑过渡到新命名，避免因突然破坏性变更导致的应用中断。

### 4. 值得关注的技术点
- **弃用别名实现**：旧模块被保留为别名，这需要精细的导入机制处理（如 `__init__.py` 中的条件导入），确保旧代码在运行时仍能访问新组件，但会在日志或文档中标记弃用警告。
- **文档与测试同步更新**：重命名涉及文档路径和测试用例的同步调整，展示了项目对代码-文档一致性的严格要求。
- **合并冲突处理**：提交记录中提到“fix: fix mismatch after merging”，暗示此变更可能在多人协作环境中进行，反映了项目对复杂合并场景的应对能力。

### 5. 基于README背景的项目发展影响
- README 摘要表明 diffusers 是一个专注于扩散模型的开源库，其核心目标是为研究者和开发者提供高效、灵活的工具。此次重命名提交直接服务于这一目标：通过模块化重构和命名优化，增强库的架构清晰度，从而支持更高效的实验迭代和模型部署。
- 长期来看，这种代码级清理有助于建立更稳定的 API 和组件生态，为未来引入新扩散架构（如文本到图像、视频生成等）奠定基础，同时强化项目作为扩散模型领域标杆工具的可持续性。

## 详细提交记录

### [2e09bbc](https://github.com/huggingface/diffusers/commit/2e09bbcf1c4930381a3f043e8fe7bb9f8bdafb43)

- **作者**: Sara Han
- **时间**: 2026-11-23T18:00:12Z
- **提交信息**: fix : Rename to P-Image-OSS (#15362)

* Rename P-H3-Image to P-Image-OSS

Move the autoencoder, condition embedder, modular pipeline,
docs and tests to the p_image_oss name. Keep the old
p_h3_image modules as deprecated aliases.

Co-Authored-By: Claude Opus 5.5 <noreply@anthropic.com>

* fix: small clarification in doc about the aliases

* fix: deprecate the old naming

* fix: fix missmatch after merging

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: YiYi Xu <yixu310@gmail.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-11-24
**监控日期**: 2026-11-23
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


**报告日期**: 2026-11-24
**监控日期**: 2026-11-23
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13438
- **最后更新**: 2026-11-24T01:34:02Z

## 提交统计

- **昨日提交总数**: 7
- **提交者数量**: 1
- **主要提交者**: Zhongjie Duan

## AI分析总结

## modelscope/DiffSynth-Studio 昨日提交分析

### 1. 主要更新类型

- **功能新增（核心）**：支持统一序列并行（Unified Sequence Parallel）、KV-Cache 压缩、DetailScale-SR 超分辨率
- **文档更新**：README、文档、示例脚本的多处补充与修正
- **Bug 修复**：少量拼写错误和序列并行相关的设备/逻辑修复

### 2. 关键变更点及其与项目整体方向的关系

- **序列并行（#1851）** 是本次最重要的提交，涉及 hook、后端、状态管理、双流并行、padding 等底层机制，覆盖 22 个以上 pipeline（含 kvcache 模型、H3-Image 等），并提供并行启动脚本和文档。这与项目「统一扩散框架」的方向高度一致——将并行加速能力从单个模型推广到整个模型族，降低大规模推理的门槛。
- **KV-Cache 压缩（#1844、#1846）** 针对视频生成等自回归/逐帧扩散流程，压缩缓存以降低显存占用，后续还扩展到了 Wan-Animate-2。这回应了扩散视频模型在长序列、高分辨率下显存瓶颈的核心痛点。
- **DetailScale-SR（#1845）** 新增超分辨率能力，丰富了模型生态。
- 文档类提交（README、docs、typo）说明项目在快速迭代的同时注重可维护性和用户引导。

### 3. 对项目的影响和潜在意义

- 序列并行使用户能在多卡上高效运行原本单卡难以承载的大模型 pipeline，显著提升可用性和推理规模。
- KV-Cache 压缩直接降低显存需求，使消费级硬件也能运行长视频生成任务，扩大用户群体。
- 两者结合体现了项目在**性能与可扩展性**上的战略投入，从「支持更多模型」转向「让现有模型跑得更快、更省」。

### 4. 值得关注的技术点

- 序列并行采用统一抽象（collective、context、state、hook），而非逐模型定制，设计上具备良好的可扩展性。
- 双流并行（double stream sp）和 kvcache 模型的并行支持说明框架已深入到 DiT 双流架构和注意力缓存等复杂场景。
- 从提交信息看，序列并行经历了 13→9→更多 pipeline 的渐进式适配过程，体现了务实的工程推进方式。
- 并行脚本与文档同步提交，说明 PR 已经过验证（"verified sp hook"）。

### 5. 基于项目背景对项目发展的影响

DiffSynth-Studio 作为统一扩散推理框架，此前重点在于模型覆盖广度（视频、图像、超分等）。这批提交标志着项目进入**深度优化阶段**：通过序列并行和缓存压缩解决规模化推理的工程瓶颈，使框架在保持模型多样性的同时具备生产级的性能表现。这将增强其与竞品（如 ComfyUI 生态）的差异化优势，吸引更多需要大规模推理的研究者和开发者，推动项目从研究工具向高性能推理平台演进。

## 详细提交记录

### [259d186](https://github.com/modelscope/DiffSynth-Studio/commit/259d1864903a7d469975584294d233bdb4aba6ae)

- **作者**: Zhongjie Duan
- **时间**: 2026-11-23T07:38:17Z
- **提交信息**: update README (#1852)

### [e33e16c](https://github.com/modelscope/DiffSynth-Studio/commit/e33e16cfd38fc9d22b753303ed2b16d086ceb586)

- **作者**: Zhongjie Duan
- **时间**: 2026-11-23T07:30:43Z
- **提交信息**: Support Unified Sequence Parallel (#1851)

* collective and context

* refine config

* verified sp hook, backend, state

* support padding

* support double stream sp

* support sp for 13 simple pipeline

* support 9 more pipeline

* support kvcache models

* support h3-image

* fix sp device

* guard boogu and ideogram4

* add sp_parallel scripts

* fix sp bug for ltx2.5, wan2.2-5B, ernie

* add scripts in docs

* add docs for parallel

* update README

---------

Co-authored-by: mi804 <1576993271@qq.com>

### [ee5fab2](https://github.com/modelscope/DiffSynth-Studio/commit/ee5fab2387c9ae012edb771dcfad6c6a6aceda3b)

- **作者**: Zhongjie Duan
- **时间**: 2026-11-23T06:14:14Z
- **提交信息**: fix typo (#1848)

### [87ae016](https://github.com/modelscope/DiffSynth-Studio/commit/87ae01654426887ebb139923820df41dc6592c77)

- **作者**: Zhongjie Duan
- **时间**: 2026-11-23T05:10:22Z
- **提交信息**: update docs (#1847)

### [e0fd432](https://github.com/modelscope/DiffSynth-Studio/commit/e0fd43262d92ebc162a5433ef91dc23200f1342d)

- **作者**: Zhongjie Duan
- **时间**: 2026-11-23T03:32:23Z
- **提交信息**: update kv-cache-compression examples (#1846)

### [eb8ce72](https://github.com/modelscope/DiffSynth-Studio/commit/eb8ce72835e6e3fb0554a5b3fca0bd46948262f2)

- **作者**: Zhongjie Duan
- **时间**: 2026-11-23T02:59:18Z
- **提交信息**: support DetailScale-SR (#1845)

### [3075eb6](https://github.com/modelscope/DiffSynth-Studio/commit/3075eb67ae18b68c756e95bb93419292f7abed49)

- **作者**: Zhongjie Duan
- **时间**: 2026-11-23T02:37:39Z
- **提交信息**: Support KV-Cache Compression (#1844)

* support KV-Cache Compression

* update docs

* support KV-Cache Compression for Wan-Animate-2

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-11-24
**监控日期**: 2026-11-23
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 39000
- **最后更新**: 2026-11-24T06:07:25Z

## 提交统计

- **昨日提交总数**: 25
- **提交者数量**: 20
- **主要提交者**: Aarne Talman, ashwini rathi, em-dreyer

## AI分析总结

## SGLang 昨日提交分析（共25条）

### 1. 主要更新类型
- **性能优化**：占比最高，涵盖AMD/ROCm解码内核、调度器预填充释放、Triton确定性解码块启动等
- **Bug修复**：MoE路由权重、量化精度、HiCache内存标志、NPU测试等
- **CI/基础设施**：AMD、NPU、Intel XPU多后端测试矩阵扩容与稳定性修复
- **文档与重构**：cookbook新增模型、运行时核心死代码清理

### 2. 关键变更与项目方向的关系
- **多硬件后端持续深化**：AMD（gfx950稀疏解码、QSA MQA logits加速）、NPU（DSA-TAIL的PD传输与解码回退、MemFabric修复）、Intel XPU（容器共享、Arc Pro B70基线）均有大量投入，体现SGLang"跨平台高性能推理"的核心定位
- **调度与缓存链路优化**：scheduler在观察者延迟响应前释放已完成的prefill请求、linker在forward栅栏前解析槽位位置、prefetch KV绑定请求会话——这些直接服务于低延迟与长上下文推理
- **内核插件体系成熟化**：DFLASH worker轮次阶段绑定、draft megakernel规格降级拒绝，说明kernel_plugins机制在扩展
- **安全与稳定性**：sgl-router升级url依赖修复RUSTSEC漏洞、MoE路由softcap防止大logits溢出

### 3. 影响与潜在意义
- 硬件覆盖扩展降低了各后端（AMD/NPU/XPU）的部署门槛，有助于生态采纳
- 调度器与linker的修复提升了长会话/缓存场景下的正确性与吞吐
- CI矩阵扩容（73个CUDA测试迁移到AMD）增强回归保障，但增加维护成本

### 4. 值得关注的技术点
- **[Perf] AMD FlyDSL稀疏解码与padded Q分组步进launch**：针对gfx950的QSA深度优化
- **[Fix] scheduler在observers延迟前释放prefill**：避免请求滞留导致的延迟放大
- **[Feat] DFLASH worker绑定自身轮次阶段**：运行时可组合轮次的灵活设计
- **[Fix] MoE softcap路由权重有限性**：数值稳定性细节
- 多条提交由Claude系列模型协同生成，体现AI辅助开发流程的常态化

### 5. 对项目发展的意义
结合README中"Fast inference for LLMs and multimodal models"的目标，本批提交表明项目正处于**多后端性能打磨与生产可靠性加固**阶段：一手在AMD/NPU/XPU上推进解码与缓存的极限性能，一手通过CI扩容和调度修复夯实稳定性。这巩固了SGLang作为跨平台推理引擎的竞争壁垒，为更大规模的模型（如Ling-3.2、GLM-5.3、Qwen3.8）落地提供了支撑，整体推动项目向生产就绪、硬件无关的高性能推理平台演进。

## 详细提交记录

### [95c4492](https://github.com/sgl-project/sglang/commit/95c449215fba542c7c8d485be087358413fc5922)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-23T23:47:19Z
- **提交信息**: [CI] ci-lark-notify: Remove the runner-health card (#52687)

### [be6c4c7](https://github.com/sgl-project/sglang/commit/be6c4c7bd9cd40860560a260d19f0fffb639030b)

- **作者**: Shangming Cai
- **时间**: 2026-11-23T23:07:32Z
- **提交信息**: [Fix] sgl-router: Bump url to 2.5.9 for RUSTSEC-2026-0592 (#52663)

### [bb81caa](https://github.com/sgl-project/sglang/commit/bb81caa2b1efa1db61a37e2c6422b9b3ed21f050)

- **作者**: em-dreyer
- **时间**: 2026-11-23T22:38:40Z
- **提交信息**: [CI] slash-command-handler: always run the handler from the default branch (#52651)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [e1dbd0e](https://github.com/sgl-project/sglang/commit/e1dbd0ed451a642f664b07f797c64e26c5d792aa)

- **作者**: maocheng23
- **时间**: 2026-11-23T22:10:07Z
- **提交信息**: [Fix] scheduler: Release finished prefill requests before observers defer responses (#52510)

Co-authored-by: canghua <canghua.wjp@alibaba-inc.com>

### [1f71385](https://github.com/sgl-project/sglang/commit/1f713857aa37c065bf2168f7570a7058d43396a1)

- **作者**: Yuwei An
- **时间**: 2026-11-23T21:45:03Z
- **提交信息**: [Feat] kernel_plugins: Bind the DFLASH worker's own round phases for a runtime that composes its round (#52495)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [563813c](https://github.com/sgl-project/sglang/commit/563813c0d60282fa848382fec600b40d28ddec98)

- **作者**: Xinyuan Tong
- **时间**: 2026-11-23T15:51:16Z
- **提交信息**: [Doc] cookbook: Add Ling-3.2-air (#52598)

### [ac02437](https://github.com/sgl-project/sglang/commit/ac0243723b0dcba177f8792979daaa2f8d6ee6ea)

- **作者**: Denji-kk
- **时间**: 2026-11-23T14:35:43Z
- **提交信息**: [Perf] linker: Resolve slot locations before the forward fence (#49463)

Co-authored-by: Shuwen Wang <47200617+alphabetc1@users.noreply.github.com>
Co-authored-by: alphabetc1 <2508695655@qq.com>

### [576e00a](https://github.com/sgl-project/sglang/commit/576e00a5afe7f52052a7437ae6ea5917e9f62c79)

- **作者**: Denji-kk
- **时间**: 2026-11-23T14:33:25Z
- **提交信息**: [Fix] linker: Cover published prefetch KV with its request's session (#49467)

Co-authored-by: alphabetc1 <2508695655@qq.com>
Co-authored-by: Shuwen Wang <47200617+alphabetc1@users.noreply.github.com>

### [ac0380c](https://github.com/sgl-project/sglang/commit/ac0380c7faf9cece3ca32ffe75815af7c585acea)

- **作者**: Nikolai
- **时间**: 2026-11-23T13:44:52Z
- **提交信息**: [Perf] [AMD] Qwen3.8: Serve QSA decode with AITER's fused FlyDSL sparse decode on gfx950 (#45196)

Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Thomas Wang <thomawan@amd.com>

### [6332091](https://github.com/sgl-project/sglang/commit/63320913035252b0bcf10e54650394a87460ceec)

- **作者**: Christian Gilli
- **时间**: 2026-11-23T13:16:09Z
- **提交信息**: [Perf] [AMD] qsa: Faster decode MQA logits on ROCm (padded Q, group-strided launch) (#48649)

Co-authored-by: Nikolai <nprotaso@amd.com>

### [b119180](https://github.com/sgl-project/sglang/commit/b119180763ec4f102e13643ea6270112415ccf0b)

- **作者**: ankitgala007
- **时间**: 2026-11-23T13:15:39Z
- **提交信息**: [Fix] moe/router: Keep softcapped router weights finite for large logits (#51138)

Co-authored-by: Ankit Gala <204639277+ankitgala007@users.noreply.github.com>

### [6a4e10a](https://github.com/sgl-project/sglang/commit/6a4e10a0ee643dfbe5f59a98b60293bc11fc1bdd)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-11-23T12:41:14Z
- **提交信息**: [Refactor] srt: Fix silent failures and prune dead code in the runtime core (1/4) (#50803)

Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>

### [0a8693f](https://github.com/sgl-project/sglang/commit/0a8693fbe3a2e46ccc06470a461a2b85865672fd)

- **作者**: pllimax
- **时间**: 2026-11-23T11:34:56Z
- **提交信息**: [Fix] [NPU] tests: drop pin_memory expandable segments and fix parallel-config mock (#52545)

### [38ae340](https://github.com/sgl-project/sglang/commit/38ae340221b4b65859c68e85d9e8ffb6b9c6f167)

- **作者**: Bingxu Chen
- **时间**: 2026-11-23T09:47:30Z
- **提交信息**: [CI] [AMD] ci: Run 73 more CUDA per-PR tests on AMD in their CUDA tiers (#51523)

Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Michael <13900043+michaelzhang-ai@users.noreply.github.com>

### [9bfccac](https://github.com/sgl-project/sglang/commit/9bfccac06d0a6833a28ae78e837a2c6bc098bccb)

- **作者**: Bingxu Chen
- **时间**: 2026-11-23T09:47:12Z
- **提交信息**: [CI] [AMD] ci: Follow #48617 on AMD, drop the nondeterministic job, and lint AMD nightly flags (#51514)

Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Michael <13900043+michaelzhang-ai@users.noreply.github.com>

### [2be81e0](https://github.com/sgl-project/sglang/commit/2be81e0ddc572fea3229960b2d9dd7c864cde883)

- **作者**: shun8686
- **时间**: 2026-11-23T07:38:33Z
- **提交信息**: [CI] [NPU] test: Collect pod logs on failure and add L3 Mooncake HiCache to the GLM-5.3 PCP GPQA case (#52484)

### [7f0ba83](https://github.com/sgl-project/sglang/commit/7f0ba83a7cf1e7c0d8f9d92b5b5c1bd39d3714b9)

- **作者**: Bingxu Chen
- **时间**: 2026-11-23T07:35:33Z
- **提交信息**: [Fix] [AMD] qknorm: Fall back from fused QK norm on ROCm when norm weights differ in dtype (#52234)

Co-authored-by: bingxche <195740905+bingxche@users.noreply.github.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [2544c9a](https://github.com/sgl-project/sglang/commit/2544c9ac34be4447bdffa612c37015a3f8da9e84)

- **作者**: Yuwei An
- **时间**: 2026-11-23T04:42:35Z
- **提交信息**: [Fix] kernel_plugins: Let a draft megakernel spec this server does not meet decline instead of refusing the server (#52438)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [42abbd7](https://github.com/sgl-project/sglang/commit/42abbd7e2cc191a052cbdaa736753639ac026bf0)

- **作者**: Shuwen Wang
- **时间**: 2026-11-23T03:03:14Z
- **提交信息**: [Fix] cookbook: Render AgentX linker options with --unified-cache-external-linker-config (#52373)

### [b40fc17](https://github.com/sgl-project/sglang/commit/b40fc179614059a645501a752b6f9d2fdc5d4f6b)

- **作者**: sherdavincl9
- **时间**: 2026-11-23T02:47:54Z
- **提交信息**: [Fix] [NPU] hicache: Drop the MemFabric giant-page flag for AICPU (#51747)

### [3f28f31](https://github.com/sgl-project/sglang/commit/3f28f31039d4910b7c010b630e1bc8d3e83755f0)

- **作者**: ashwini rathi
- **时间**: 2026-11-23T02:31:16Z
- **提交信息**: [CI] [Intel] ci/xpu: Use per-job container names so XPU runners can share a host (#51238)

### [57cd75b](https://github.com/sgl-project/sglang/commit/57cd75b8e9e28783a6e63f6efe72d79eaf255099)

- **作者**: ashwini rathi
- **时间**: 2026-11-23T02:25:14Z
- **提交信息**: [CI] [Intel] ci/xpu: Add an Arc Pro B70 diffusion perf baseline and pick it per device (#52069)

### [7c21d8c](https://github.com/sgl-project/sglang/commit/7c21d8c7017884f613089f3e69b225534e75a6cb)

- **作者**: Ziru
- **时间**: 2026-11-23T01:50:03Z
- **提交信息**: [Fix] [CPU] Fix: Qwen3.5-35B-A3B-GPTQ-Int4 quantization rule failure and accuracy degradation (#46559)

Co-authored-by: Niu Ziru <niuziru@gnr799217.jf.intel.com>
Co-authored-by: Niu Ziru <niuziru@a4bf018d3341.jf.intel.com>

### [61915e5](https://github.com/sgl-project/sglang/commit/61915e54eeb06a88805c551d4412f8a59d997311)

- **作者**: qiuhongchen
- **时间**: 2026-11-23T00:49:53Z
- **提交信息**: [Feat] [NPU] DSA-TAIL: Support PD-transfer and decode-retraction (#50968)

### [e2d88a6](https://github.com/sgl-project/sglang/commit/e2d88a64f05dec87a23980a52215eb1491b44421)

- **作者**: Aarne Talman
- **时间**: 2026-11-23T00:39:36Z
- **提交信息**: [Perf] deterministic: Launch a fixed number of Triton decode blocks for large split budgets (#47410)

Co-authored-by: Xinyi Song <xinyisong0111@gmail.com>
Co-authored-by: HAI <hixiao@gmail.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-11-24
**监控日期**: 2026-11-23
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1307
- **最后更新**: 2026-11-23T12:26:00Z

## 提交统计

- **昨日提交总数**: 14
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

## cache-dit 仓库昨日提交分析

### 1. 主要更新类型

**功能新增（为主）**：新增 SVDQ（Singular Value Decomposition Quantization）量化体系下的多种混合精度权重格式（W1A4/W2A4/W3A4）；新增 FP8 检查点序列化支持；新增 Fused W4A8 内核。同时伴随大量**文档更新**，用于量化数学原理、内存账目和对比结果说明。

---

### 2. 关键变更点及与项目方向的关系

- **SVDQ 量化体系全面落地**：从底层算子（Fused W4A8 内核）、中间表示（统一量化 API、统一算子命名）、权重格式（Packed W1A4/W2A4/W3A4）、到上层序列化（FP8 checkpoint）打通了完整链路，直接服务于 README 中"Quantization"这一核心目标。
- **Packed A4 特化优化**：支持 per-2 inner groups 的 packed A4 内存布局，并配套编译（compile）优化 gallery，表明项目在推理性能与显存压缩上的持续深耕。
- **文档体系同步建设**：围绕量化格式、内存账目（weight/activation）、三阶段（three-stage）编解码、实验阈值等做了系统化文档补充，降低了用户理解复杂量化方案的门槛。
- **实验结果可视化**：通过 gallery 展示 W2A4 r32/r64 三阶段结果、W1/W2 默认 rank256 等配置，形成"格式→编译→效果"的闭环展示。

---

### 3. 对项目的影响和潜在意义

- 显著扩展了量化压缩的精度-效率组合空间（从 4bit 到 8bit 的全范围），为用户提供了更多可选的推理加速配置。
- FP8 checkpoint 支持打通了从训练/导出到推理部署的存取流程，对实际工程落地至关重要。
- 统一量化 API 和算子命名的重构为后续扩展新格式（如 W4A4 等）预留了良好架构。
- 三阶段编解码（three-stage codec）的引入表明项目在压缩精度损失方面做出了系统性改进，有望在同等显存下提升重建质量。

---

### 4. 值得关注的技术点

- **SVDQ + Packed 量化组合**：将 SVD 分解与 A4 打包布局结合，是较前沿的权重压缩策略，尤其 per-2 inner group 的设计需要在 kernel 层面精细调度。
- **三阶段编解码（Three-stage codec）**：W1/W2 默认启用 three-stage 并支持 rank256，意味着在极低比特场景下对压缩质量做了层次化处理，值得关注其数学原理。
- **Fused W4A8 内核**：将 4bit 权重和 8bit 激活的 GEMM 融合为单一内核，是推理引擎中常见的性能优化手段，直接影响吞吐。
- **编译优化（Compile）**：gallery 资产中出现 compile 优化，暗示项目在利用 torch.compile 或自定义 codegen 加速量化路径。

---

### 5. 基于 README 的项目发展评估

cache-dit 定位为"PyTorch 原生的 DiT 推理引擎，覆盖 Cache/并行/量化/CPU Offload"。这批提交集中火力在**量化**这一支柱上，使其从早期的简单量化扩展为具备多种混合精度格式、统一 API、编译优化和实验结果的成熟模块。这不仅增强了 DiT 推理的实际部署能力（更小的显存占用、更快的推理速度），也为项目在量化领域的持续演进打下了坚实基础，是项目走向工程化、生产化的重要一步。

## 详细提交记录

### [6708c1f](https://github.com/vipshop/cache-dit/commit/6708c1f44c3da351a0c8bf46dd6b2dd68d6fc504)

- **作者**: DefTruth
- **时间**: 2026-11-23T13:27:57Z
- **提交信息**: Merge pull request #1390 from vipshop/dev

feat(svdq): add packed W1A4/W2A4/W3A4 weight formats

### [f3e6cc0](https://github.com/vipshop/cache-dit/commit/f3e6cc049a1c31bf123adff03413b378d1c963cc)

- **作者**: DefTruth
- **时间**: 2026-11-23T13:07:25Z
- **提交信息**: Document W1A4 experimental rank threshold

### [bb4f5a5](https://github.com/vipshop/cache-dit/commit/bb4f5a53c162e99d734beb98e222bdb123d0b047)

- **作者**: DefTruth
- **时间**: 2026-11-23T13:05:43Z
- **提交信息**: Document packed A4 weight and activation memory accounting

### [e464ef5](https://github.com/vipshop/cache-dit/commit/e464ef50626667ba414f9bba711b8d20c78fe8fe)

- **作者**: DefTruth
- **时间**: 2026-11-23T13:02:55Z
- **提交信息**: Match packed A4 table to gallery configurations

### [086a1a1](https://github.com/vipshop/cache-dit/commit/086a1a1631f26f551b6b1ff173fd6b5003871c5a)

- **作者**: DefTruth
- **时间**: 2026-11-23T13:01:11Z
- **提交信息**: Support packed A4 per-2 inner groups and update gallery

### [d074458](https://github.com/vipshop/cache-dit/commit/d074458a2ff6ab785aa3685162dbd4d35e7b4ba7)

- **作者**: DefTruth
- **时间**: 2026-11-23T12:31:09Z
- **提交信息**: Show W2A4 r32/r64 three-stage results

### [77dc0c4](https://github.com/vipshop/cache-dit/commit/77dc0c462800c5d9e6e15257ea13398e7c409ce2)

- **作者**: DefTruth
- **时间**: 2026-11-23T12:24:02Z
- **提交信息**: Document packed three-stage codec in wNa4

### [247a4fd](https://github.com/vipshop/cache-dit/commit/247a4fd8f6e00f86afc2266aa63d2945875215ba)

- **作者**: DefTruth
- **时间**: 2026-11-23T12:17:59Z
- **提交信息**: Refine packed A4 gallery and document weight memory

### [7be2509](https://github.com/vipshop/cache-dit/commit/7be2509cb24549bddc81208e65b130ec513687c9)

- **作者**: DefTruth
- **时间**: 2026-11-23T12:16:37Z
- **提交信息**: Add packed A4 compile gallery asset

### [f76ff02](https://github.com/vipshop/cache-dit/commit/f76ff02093e7f70f1bee06780cbb1a1654314053)

- **作者**: DefTruth
- **时间**: 2026-11-23T12:16:26Z
- **提交信息**: Document packed A4 math and compile gallery

### [b5d2a38](https://github.com/vipshop/cache-dit/commit/b5d2a38d3536c6a64a5357a5f9f31e5fb9ed3647)

- **作者**: DefTruth
- **时间**: 2026-11-23T12:13:18Z
- **提交信息**: Default packed W1/W2 to three-stage and add rank256

### [312b3ef](https://github.com/vipshop/cache-dit/commit/312b3efa7e371a3678f71f11b73efe480720ec16)

- **作者**: DefTruth
- **时间**: 2026-11-23T09:47:19Z
- **提交信息**: Add packed SVDQ W1A4-W3A4 and unify quantization APIs

### [a87c58f](https://github.com/vipshop/cache-dit/commit/a87c58f77528b63a3f805637ae647777cb4d24ec)

- **作者**: DefTruth
- **时间**: 2026-11-23T05:38:43Z
- **提交信息**: feat(svdq): add fused W4A8 kernels (#1388)

Refs #1387

### [91be9e9](https://github.com/vipshop/cache-dit/commit/91be9e917c5bd361d227810f1e106a27660a95b4)

- **作者**: DefTruth
- **时间**: 2026-11-23T02:54:28Z
- **提交信息**: feat(svdq): add FP8 checkpoint serialization and unified operator naming (#1386)

Adds FP8 checkpoint round-trip support, prefixes SVDQ pybind exports, and records the per-block design plan.

Closes #1385.

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-11-24
**监控日期**: 2026-11-23
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 97441
- **最后更新**: 2026-11-24T06:04:47Z

## 提交统计

- **昨日提交总数**: 68
- **提交者数量**: 51
- **主要提交者**: wenjinhust, yhcheong (vllmellm), rishabh

## AI分析总结

## vLLM 昨日 68 个提交合并分析

### 一、主要更新类型分布
- **Bug 修复占比最高**，约一半，覆盖 Kernel、量化、KV Cache/Connector、模型加载、滑动窗口 XPU 兼容、异步 EPLB 关闭顺序、HY4 Flash CUDA 平台检查等。
- **基础设施与 CI** 约 8 条，涉及 CPU/XPU/ROCm 镜像缓存、测试选择器与运行器迁移、XPU 依赖补齐、Recipe 镜像更新。
- **性能优化** 约 6 条，集中在 Kernel 层（AWQ、TRITON_MLA、滑窗前缀预填充、融合算子）与 DeepGemm 线性后端覆盖。
- **功能新增** 约 9 条，含 MXFP8 FlashInfer、DCP 稀疏 MLA、Engram Grace EGM、XPU 量化格式、LoRA 私有 worker 本地张量适配器加载。
- 另有文档 5 条、重构 4 条、治理 3 条、弃用 1 条（TorchAO 后端）。

### 二、关键变更与项目方向
- **强化多硬件生态**：ROCm 精度修复与 MI325X/MI355X 方案、XPU 量化与 CI 扩展，系统性保障非 NVIDIA 硬件一致性，呼应"everyone"的跨平台定位。
- **深挖推理性能**：GLM-5.3-Flash 融合 all-reduce+mHC+RMSNorm 实现 8.7% E2E 吞吐提升，TRITON_MLA 内核级最高 1.7× 收益，直接服务"fast and cheap"目标。
- **MoE 与量化体系收敛**：MXFP8、nvfp4_per_token、moe_wna16 路由专家处理完善，同时弃用 TorchAO、ERNIE 4.5 迁移 Transformers 后端，量化栈趋向标准化，降低长期维护负担。
- **分布式与长上下文**：KV Connector、MLA、DeepEP、MoE 内核持续打磨；Pipeline 并行下 KV/输入 ID 与 embedding 构建的修复减少多机部署踩坑。

### 三、值得关注的技术点
- **MoE CuteDSL MXFP8 + DeepEP 低延迟**：面向 Hopper/Blackwell 的专家并行加速。
- **FP8 PLE 表跨 NVLink/RDMA 共享**：量化表在高速互联上的通信优化，是内核与分布式通信交叉的典型方向，减少多卡重复传输。
- **异步 EPLB 关闭顺序修复**：避免专家并行负载均衡资源泄漏或崩溃，对 MoE 稳定性关键。
- **稀疏 MLA DCP（CuTe DSL A2A reduce）**：支持 Kimi K3.1，显示社区对前沿模型的快速跟进。
- **Engram Grace EGM 支撑 NVLink peer shards**：CPU-GPU 内存分层的新尝试。
- **LoRA 私有 worker 本地适配器加载**：增强多租户与动态 LoRA 场景的隔离性与加载效率。
- **DeepGemm 后端显式覆盖**：`--linear-backend deep_gemm` 提供更细的内核调优粒度。
- **Mamba/SSD 内核预热、Gemma3n CUDA Graph 尺寸修复**：边缘与混合架构稳定性保障。

### 四、影响与潜在意义
高频 CI 修复降低维护成本、提升合并速度与贡献体验；治理与 CodeOwner 更新（新增 pooling committer、EPD owner）表明项目在规模化协同。XPU/ROCm 平台检查补强提升企业级部署信心，Qwen4Exp、Inkling 2 Mini 等 Recipe 更新体现新模型跟进速度。

### 五、整体评价
这批提交显示 vLLM 正从"功能扩张"转向"**深度优化 + 多硬件成熟度 + 工程治理**"：一方面以 Kernel 与融合算子压榨吞吐成本，另一方面以大量修复与 CI 加固保障生产可用性。对照其"Easy, fast, cheap"愿景，跨平台修复降低了使用门槛，内核与分布式共享优化了性能，LoRA 与量化收敛减少了内存与计算开销。整体属项目成熟期的稳定化与精细化优化，持续巩固 vLLM 作为主流 LLM 推理引擎的工程可靠性与硬件覆盖广度，为更大规模的分布式与异构硬件场景奠定基础。

## 详细提交记录

### [1fd30e4](https://github.com/vllm-project/vllm/commit/1fd30e4f6e8fd621ac68cf44fb36bfe710646a69)

- **作者**: Kevin H. Luu
- **时间**: 2026-11-23T23:30:43Z
- **提交信息**: [CI] Don't treat a finished build left blocked by the test picker as running (#69497)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [6e628b6](https://github.com/vllm-project/vllm/commit/6e628b66ab60519d0ced0dd58c2c50d573e41758)

- **作者**: Srijan Keshri
- **时间**: 2026-11-23T23:21:38Z
- **提交信息**: [Bugfix][Kernel] Validate decode top-k runtime width (#60961)

Signed-off-by: Srijan Keshri <212402043+arcusbuilds@users.noreply.github.com>
Signed-off-by: Srijan Keshri <srijankeshri007@gmail.com>
Signed-off-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>

### [ab6ce7d](https://github.com/vllm-project/vllm/commit/ab6ce7d23086042756e5434dbf861b7a2d3ce2b9)

- **作者**: Haobin Guo
- **时间**: 2026-11-23T23:16:14Z
- **提交信息**: [MoE][Kernel] Support MXFP8 in FlashInfer CuteDSL batched experts for DeepEP low-latency (#66456)

Signed-off-by: Haobin Guo <haobing@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Pavani Majety <pmajety@nvidia.com>

### [4e630bf](https://github.com/vllm-project/vllm/commit/4e630bfc663ccaa63b94a9a54ff69eb015435d3a)

- **作者**: Andreas Karatzas
- **时间**: 2026-11-23T23:10:33Z
- **提交信息**: [ROCm][CI] Cache a PR's ROCm base image automatically before merge (#69056)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Rohan Potdar <66227218+Rohan138@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [5a215c2](https://github.com/vllm-project/vllm/commit/5a215c27fd761158ba3120415eafe04a2ee5841a)

- **作者**: callum thickett
- **时间**: 2026-11-23T22:48:00Z
- **提交信息**: [Perf][Kernel] AWQ: vectorize the output store in dequantize_weights (#63590)

Signed-off-by: Callum Thickett <callum.thickett@lendable.co.uk>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [6cbea92](https://github.com/vllm-project/vllm/commit/6cbea92cb2f17d49e0a35e52313413a0f45dbd46)

- **作者**: searlion
- **时间**: 2026-11-23T22:34:54Z
- **提交信息**: [Bugfix] Fix oversized piecewise CUDA graphs for Gemma3n cross-decoder (#68944)

Signed-off-by: Lewis Won <lewis.won@gmail.com>
Co-authored-by: Lucas Wilkinson <LucasWilkinson@users.noreply.github.com>

### [4172f61](https://github.com/vllm-project/vllm/commit/4172f6178d47b6753b52ec4d7f47b144cdd1bf82)

- **作者**: Kevin H. Luu
- **时间**: 2026-11-23T22:20:20Z
- **提交信息**: [CI] Retry gcc-15 downloads from the Launchpad PPA in the CPU image (#69416)

Signed-off-by: Kevin Luu <51931015+khluu@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [6905d65](https://github.com/vllm-project/vllm/commit/6905d656c5df78effe0a3d5432cb3bb0f811f444)

- **作者**: Anjie Hou
- **时间**: 2026-11-23T22:17:03Z
- **提交信息**: [Feature][GDN] Reuse Qwen GDN for OLMo Hybrid prefill checkpoints (#68368)

Signed-off-by: specture724 <specture724@gmail.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [a289c72](https://github.com/vllm-project/vllm/commit/a289c722dd59a0e74bf77e005a7077676c320f5c)

- **作者**: Wentao Ye
- **时间**: 2026-11-23T21:59:18Z
- **提交信息**: [Perf][GLM-5.3-Flash] Enable fused all-reduce + mHC + RMSNorm on Hopper, 8.7%E2E Throughput Improvement (#69001)

Signed-off-by: yewentao256 <zhyanwentao@126.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [74808b1](https://github.com/vllm-project/vllm/commit/74808b14bcc3f28a6202517490d86c7acf666c54)

- **作者**: Wentao Ye
- **时间**: 2026-11-23T21:35:26Z
- **提交信息**: [Bugfix][Kernel] Restrict `TRITON_ATTN` tensor-descriptor path to XPU (#68521)

Signed-off-by: yewentao256 <zhyanwentao@126.com>
Signed-off-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>
Co-authored-by: cinnamonica02 <96633571+cinnamonica02@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [8d5e012](https://github.com/vllm-project/vllm/commit/8d5e012ab97fb267da35b23941538f8a523b7fc2)

- **作者**: Artur Fierka
- **时间**: 2026-11-23T21:12:27Z
- **提交信息**: [Bugfix][Mamba] Warm up the SSD kernels on a prefill-sized sequence (#60800)

Signed-off-by: Artur Fierka <artur.fierka@intel.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [4043b93](https://github.com/vllm-project/vllm/commit/4043b93faf62485f5f77ec8f81ce99ab9d995061)

- **作者**: Taneem Ibrahim
- **时间**: 2026-11-23T20:50:43Z
- **提交信息**: [Governance] Add Taneem Ibrahim as a pooling committer (#69437)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [a998a20](https://github.com/vllm-project/vllm/commit/a998a20ef98e1f788954470ffd0c635207e7157a)

- **作者**: Yifei Wang
- **时间**: 2026-11-23T20:49:50Z
- **提交信息**: [Bugfix][KV Connector] Fix HF3FS storage rank derivation with pipeline parallelism (#67301)

Signed-off-by: Yifei Wang <yifei.w@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [a688cea](https://github.com/vllm-project/vllm/commit/a688ceac3979f7a9097e6d949db9bf91a5a42fde)

- **作者**: Akshat Anand
- **时间**: 2026-11-23T20:25:55Z
- **提交信息**: [Bugfix][Tracing] Collect request stats when OTLP tracing is enabled (#68674)

Signed-off-by: cipheraxat <cipheraxat@users.noreply.github.com>

### [bfe3d7e](https://github.com/vllm-project/vllm/commit/bfe3d7e879344289915ad4c0b5d01c219fbefbae)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-11-23T20:05:24Z
- **提交信息**: [Bugfix] Only inject `cohere_format` default chat-template kwarg in Cohere tokenizer mode (#69468)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [71985a9](https://github.com/vllm-project/vllm/commit/71985a9633253fb77385fe4104ab194c18dc1e0d)

- **作者**: Taneem Ibrahim
- **时间**: 2026-11-23T20:04:36Z
- **提交信息**: [Docs] Fix HY4 Flash IndexPool API reference warnings (#69472)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [822bbd5](https://github.com/vllm-project/vllm/commit/822bbd577ba38dd90c00c7f7449c8d10cc754ff9)

- **作者**: Ganto12
- **时间**: 2026-11-23T20:02:40Z
- **提交信息**: [Bugfix][DSv4.1] Keep MXFP8 linear weights in FP8 on SM90 at TP1 (#69446)

Signed-off-by: Ganto12 <20272171+Ganto12@users.noreply.github.com>

### [0f06eb7](https://github.com/vllm-project/vllm/commit/0f06eb7e4eee59fa43824b64f900c5c16306bb4d)

- **作者**: rasmith
- **时间**: 2026-11-23T19:49:53Z
- **提交信息**: [ROCm][Bugfix] Fix precision loss in asymmetric int8 linear layers on ROCm (#69085)

Signed-off-by: Randall Smith <Randall.Smith@amd.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [0fcd102](https://github.com/vllm-project/vllm/commit/0fcd102378d9a501ab7abac7625deebe8200b43a)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-11-23T19:48:13Z
- **提交信息**: [Bugfix][Mooncake] Stop reloading from the store after a failed load (#67957)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [4623da9](https://github.com/vllm-project/vllm/commit/4623da99ff85b0f52d9493cfafe2d1f58ede67e4)

- **作者**: ZacharyZcR
- **时间**: 2026-11-23T19:32:09Z
- **提交信息**: [Bugfix][DeepSeek V4] Keep input IDs on later pipeline stages (#55520)

### [5cfdcab](https://github.com/vllm-project/vllm/commit/5cfdcabb24c6196f0c75ef6bd8a5f787e38a3216)

- **作者**: Nils Matteson
- **时间**: 2026-11-23T18:15:05Z
- **提交信息**: [Benchmark] Time real server starts in vllm bench startup (--serve-cmd) (#69076)

Signed-off-by: Nils Matteson <nils@inferact.ai>

### [51bb4b5](https://github.com/vllm-project/vllm/commit/51bb4b5844395a39bfd2051a6a149cf69d7aa88b)

- **作者**: Alex Steiner
- **时间**: 2026-11-23T17:32:03Z
- **提交信息**: [Bugfix] Honor DecisionLimits.labeled in /v1/decisions (#68037)

Signed-off-by: pst2154 <6865592+pst2154@users.noreply.github.com>
Signed-off-by: vanshil shah <49670736+vanshilshah97@users.noreply.github.com>
Co-authored-by: pst2154 <6865592+pst2154@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vanshil shah <49670736+vanshilshah97@users.noreply.github.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: Lucas Wilkinson <LucasWilkinson@users.noreply.github.com>

### [4f0ecff](https://github.com/vllm-project/vllm/commit/4f0ecfff6be6f4d28ba91ad4d44b43b4100d4f2d)

- **作者**: stefankoncarevic
- **时间**: 2026-11-23T17:24:47Z
- **提交信息**: [Bugfix][MLA] Fix race in in-place LSE merge of chunked context (#69433)

Signed-off-by: Stefan Koncarevic <Stefan.Koncarevic@amd.com>

### [5eca5e9](https://github.com/vllm-project/vllm/commit/5eca5e982bff3f04d446dcb83ec5277f93577f4c)

- **作者**: Arpit Rawat
- **时间**: 2026-11-23T17:21:28Z
- **提交信息**: [Perf][Kernel] Coalesce K_Buffer loads and co-schedule head blocks TRITON_MLA (upto 1.7x gain at kernel level) (#69029)

Signed-off-by: Arpit Rawat <arpitrawat0404@gmail.com>

### [e4ac61a](https://github.com/vllm-project/vllm/commit/e4ac61ae44d140df4daa4cb975a198aff002581e)

- **作者**: Jee Jee Li
- **时间**: 2026-11-23T17:13:02Z
- **提交信息**: [Model][PERF] HY4 Flash Improvement (#68770)

Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>

### [4a107a2](https://github.com/vllm-project/vllm/commit/4a107a282047eef22b1aac8b72e5969f5c40f0cc)

- **作者**: Devanshi Jain
- **时间**: 2026-11-23T17:01:50Z
- **提交信息**: [Deprecation][Quantization] Deprecate the TorchAO backend (#69066)

Signed-off-by: Devanshi Jain <devanshijain@meta.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>

### [1d9f805](https://github.com/vllm-project/vllm/commit/1d9f8058bf8b3354214b0f4a4dafdac25bfb4be1)

- **作者**: Misha Goin
- **时间**: 2026-11-23T16:24:47Z
- **提交信息**: [Spec Decode][HY4] Allow DFly on any compressed-tensors target scheme (NVFP4) (#69274)

### [e83d82a](https://github.com/vllm-project/vllm/commit/e83d82a46b50a27534584a8bf4c6dd2d2cb9eeb5)

- **作者**: Pham Binh
- **时间**: 2026-11-23T15:38:17Z
- **提交信息**: [ROCm][Perf] Skip masked-out context tiles for sliding-window models in Triton prefix-prefill (#63867)

Signed-off-by: Pham Binh <194774975+phambinhfin@users.noreply.github.com>
Co-authored-by: Pham Binh <194774975+phambinhfin@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [187c473](https://github.com/vllm-project/vllm/commit/187c473dbe8aa2b3fc4213d5b79a70c588902ba5)

- **作者**: Ronald
- **时间**: 2026-11-23T15:33:10Z
- **提交信息**: [Refactor][SleepMode] Expose CuMemBackend allocator hook (#69412)

Signed-off-by: Ronald1995 <ronaldautomobile@163.com>
Co-authored-by: aoshen02 <aoshen@inferact.ai>

### [75d8770](https://github.com/vllm-project/vllm/commit/75d8770263d6907de1f28a7fdaf485e20a039d6d)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-11-23T15:28:32Z
- **提交信息**: [Bugfix][KVConnector] Split MLA kernel rows larger than the NIXL block into dense pages (#59586)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Aaron Pham <contact@aarnphm.xyz>

### [6aeedab](https://github.com/vllm-project/vllm/commit/6aeedab553dd85d6bc3f9f4deb3bb264bce0cb7c)

- **作者**: claris
- **时间**: 2026-11-23T15:01:05Z
- **提交信息**: [Bugfix][Model] Normalize the legacy Qwen3-ASR text config alias (#69226)

Signed-off-by: claris <80609948+pk954061458@users.noreply.github.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Codex <codex@openai.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [abad4cc](https://github.com/vllm-project/vllm/commit/abad4cc48213a20bdc335379520fc66b26e6181d)

- **作者**: yhcheong (vllmellm)
- **时间**: 2026-11-23T14:26:34Z
- **提交信息**: [Bugfix][Quantization] Keep checkpoint-excluded routed experts unquantized under moe_wna16 (#67413)

Signed-off-by: vllmellm <vllm.ellm@embeddedllm.com>

### [afb35f8](https://github.com/vllm-project/vllm/commit/afb35f85e7e25720a9acb656d0b20b20d33ffcd0)

- **作者**: Roman Baron
- **时间**: 2026-11-23T13:51:49Z
- **提交信息**: [Core][Model Loader] Add sleep/wake/reload lifecycle hooks to model loader (#57011)

Signed-off-by: Roman Baron <romanb@nvidia.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: aoshen02 <aoshen@inferact.ai>

### [ee1d07c](https://github.com/vllm-project/vllm/commit/ee1d07c7b2c30dc0eb686bdb00a8ce94f4e4c071)

- **作者**: Tony Lin
- **时间**: 2026-11-23T13:32:30Z
- **提交信息**: [CI] Use test runner for sampling and LoRA tests (#68884)

Signed-off-by: Tony Lin <tony.lin@intel.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [d9bfe86](https://github.com/vllm-project/vllm/commit/d9bfe86b9fe1156642ac45aadef965159dd1d7f1)

- **作者**: 李绍飞
- **时间**: 2026-11-23T13:14:31Z
- **提交信息**: [Model] Migrate ERNIE 4.5 to Transformers backend (#69087)

Signed-off-by: 李绍飞 <73046195+Remarkable911@users.noreply.github.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [4a1620a](https://github.com/vllm-project/vllm/commit/4a1620a09aba0cd771a186b81e973707c0ecbb07)

- **作者**: rishabh
- **时间**: 2026-11-23T12:53:53Z
- **提交信息**: [Bugfix] Respect root_path in elastic EP scaling middleware (#69285)

Signed-off-by: Rishabh <rishabhsaiv@gmail.com>

### [ab94934](https://github.com/vllm-project/vllm/commit/ab94934e6ca2db6e41e9e6d8eeefb740488ed0ee)

- **作者**: Tony Lin
- **时间**: 2026-11-23T12:50:17Z
- **提交信息**: [CI][Bugfix] Precompute Gemma3n sparsity quantiles before inference (#69140)

Signed-off-by: Tony Lin <tony.lin@intel.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [cc093c3](https://github.com/vllm-project/vllm/commit/cc093c3c62461796acb2307130dbfbcad03a2995)

- **作者**: Yiliu Dong
- **时间**: 2026-11-23T12:49:58Z
- **提交信息**: [HY4 Flash][Spec Decode] Allow DecodeBenchConnector and synthetic DFly acceptance (#68651)

Signed-off-by: Yiliu Dong <91178480+qianlihuang@users.noreply.github.com>

### [9e46474](https://github.com/vllm-project/vllm/commit/9e46474a7f5cde978bf012fca845aa757f8d084f)

- **作者**: matti-palomaki-amd
- **时间**: 2026-11-23T11:48:04Z
- **提交信息**: [Docs][ROCm] Add Step-5-Preview recipe for MI325X and MI355X (#67443)

Signed-off-by: Matti Palomäki <matti.palomaki@amd.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Shanshan Shen <467638484@qq.com>

### [c865edc](https://github.com/vllm-project/vllm/commit/c865edc19b67a8951d2c40af210c335e64e4f58f)

- **作者**: wangxiyuan
- **时间**: 2026-11-23T11:34:40Z
- **提交信息**: [Governance] Update codeowner for wangxiyuan (#69397)

Signed-off-by: wangxiyuan <wangxiyuan1007@gmail.com>

### [0cd1964](https://github.com/vllm-project/vllm/commit/0cd1964ad27b0736c59565568c91ce63eac79f78)

- **作者**: Tianyu Guo
- **时间**: 2026-11-23T11:25:30Z
- **提交信息**: [Bugfix] Fix ROCm OCR preemption logit drift with DeepEncoder GEMM (#69108)

Signed-off-by: Tianyu Guo <guoty9@mail2.sysu.edu.cn>
Signed-off-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>

### [179ebd9](https://github.com/vllm-project/vllm/commit/179ebd9896cff5fddc27f622649ff4c99ed5c733)

- **作者**: Tianyu Guo
- **时间**: 2026-11-23T10:20:31Z
- **提交信息**: [Governance] Add Tianyu Guo as an EPD code owner (#69376)

Signed-off-by: Tianyu Guo <guoty9@mail2.sysu.edu.cn>

### [7c1ad10](https://github.com/vllm-project/vllm/commit/7c1ad1014ee9b4b0361e9a11e8b895f6b108b5cf)

- **作者**: ankitgala007
- **时间**: 2026-11-23T10:16:56Z
- **提交信息**: [Bugfix] Pad prompt logprobs of completions aborted mid-prefill (#68605)

Signed-off-by: Ankit Gala <204639277+ankitgala007@users.noreply.github.com>
Co-authored-by: Ankit Gala <204639277+ankitgala007@users.noreply.github.com>

### [da8a505](https://github.com/vllm-project/vllm/commit/da8a505684e6a7388d5ada84bcca6a13a65765f6)

- **作者**: herotai214
- **时间**: 2026-11-23T10:13:22Z
- **提交信息**: [Core][EPD] Keep metadata-only items out of the receiver cache (#66930)

Signed-off-by: herotai214 <herotai214@gmail.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [f2f1fb7](https://github.com/vllm-project/vllm/commit/f2f1fb71ddc4a38148619e285d9b617e338375fc)

- **作者**: Devanshi Jain
- **时间**: 2026-11-23T09:27:04Z
- **提交信息**: [Bugfix][Quantization] torchao: apply each fused shard's AWQ act_pre_scale (#69002)

### [b26e084](https://github.com/vllm-project/vllm/commit/b26e0840134ea4b4c87c34bd5a0e0aa61397c638)

- **作者**: Jiangyun Zhu
- **时间**: 2026-11-23T09:05:49Z
- **提交信息**: [Attention][DCP] Sparse MLA DCP: CuTe DSL A2A reduce and DCP ShardQ (Kimi K3.1 6/6) (#66027)

Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>
Signed-off-by: Mi Sun Park <misunp@nvidia.com>
Signed-off-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: Roger Wang <hey@rogerw.io>
Co-authored-by: wangzhengtao <wangzhengtao@msh.team>
Co-authored-by: wanglinian <wanglinian@stu.pku.edu.cn>
Co-authored-by: Kimi <kimi@moonshot.cn>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Bowen Wang <abmfy@icloud.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: qizixi <22851944+zixi-qi@users.noreply.github.com>
Co-authored-by: Thien Tran <gau.nernst@yahoo.com.sg>
Co-authored-by: Jiahan Chang (Cyrus) <173873397+jiahanc@users.noreply.github.com>
Co-authored-by: Perkz Zheng <67892460+PerkzZheng@users.noreply.github.com>
Co-authored-by: Wei Zhao <51183510+wzhao18@users.noreply.github.com>
Co-authored-by: Wei Zhao <weizha@nvidia.com>
Co-authored-by: Yifan Qiao <yifanqiao@inferact.ai>
Co-authored-by: Jared Wen <jaredwen@inferact.ai>
Co-authored-by: billishyahao <bill.he@amd.com>
Co-authored-by: Yichao Zhu <Yichao.Zhu@amd.com>
Co-authored-by: hyukjlee <hyukjlee@amd.com>
Co-authored-by: seungrokj <seungrok.jung@amd.com>
Co-authored-by: Hexiang Wang <56632993+whx-sjtu@users.noreply.github.com>
Co-authored-by: seungrokj <144636725+seungrokj@users.noreply.github.com>
Co-authored-by: inferact-agent-v[bot] <326714608+inferact-agent-v[bot]@users.noreply.github.com>
Co-authored-by: v <v@inferact.ai>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Hongxia Yang <hongxia.yang@amd.com>
Co-authored-by: Hongxia Yang <62075498+hongxiayang@users.noreply.github.com>
Co-authored-by: Jiayi Yan <1195343015@qq.com>
Co-authored-by: 1195343015 <1195343015@users.noreply.github.com>
Co-authored-by: mispa-ms <81828223+mispa-ms@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>

### [d6d1616](https://github.com/vllm-project/vllm/commit/d6d1616c1c6f925d8823ffaf5e65e61e42d3b1b6)

- **作者**: wenjinhust
- **时间**: 2026-11-23T08:45:16Z
- **提交信息**: [Bugfix] call sys._current_frames() to dump callstack (#68924)

Signed-off-by: wenjinhust <wenjin.sh@huawei.com>

### [ad227db](https://github.com/vllm-project/vllm/commit/ad227db3ceb2880e7775e3683ff9805c2dfa662b)

- **作者**: Hexiang Wang
- **时间**: 2026-11-23T08:12:25Z
- **提交信息**: [Recipe][ROCm] MiniMax-M3.1-Flash MI355X AgentX PD disaggregation over Mooncake (#67857)

Signed-off-by: whx-sjtu <xiaowang990929@gmail.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Shanshan Shen <467638484@qq.com>

### [dddd8b7](https://github.com/vllm-project/vllm/commit/dddd8b7dd3e70176e6db382e979eecd041af5d30)

- **作者**: Yunxiao Ning
- **时间**: 2026-11-23T07:55:24Z
- **提交信息**: [Engram] Back NVLink peer shards with Grace EGM (#68685)

Signed-off-by: Juntian Liu <Juntianl777@gmail.com>
Signed-off-by: yunzhi <ningyunxiao.nyx@antgroup.com>
Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: Juntian Liu <Juntianl777@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: v <v@inferact.ai>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: zjy0516 <riverclouds.zhu@qq.com>

### [18af054](https://github.com/vllm-project/vllm/commit/18af054a09aba40e3ecbb70fb93eeb49f726e0fb)

- **作者**: nvision
- **时间**: 2026-11-23T07:52:13Z
- **提交信息**: [Bugfix][KV Offload] Store the chunk containing a partial-tail CPU hit (#69048)

Signed-off-by: nvisional <211501492+nvisional@users.noreply.github.com>
Co-authored-by: nvisional <211501492+nvisional@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [418af60](https://github.com/vllm-project/vllm/commit/418af607309d819bf091229bcc3d8ca8e5ce007f)

- **作者**: xiangdong
- **时间**: 2026-11-23T06:53:48Z
- **提交信息**: [XPU][CI] Expand more entrypoints in Intel GPU CI (#68354)

Signed-off-by: zengxian <xiangdong.zeng@intel.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [88952d2](https://github.com/vllm-project/vllm/commit/88952d22dcb3e1b616051ac4f427eddc37d93004)

- **作者**: liuzhenwei
- **时间**: 2026-11-23T06:26:53Z
- **提交信息**: [XPU][CI] revert skipped cases v1/worker (#68618)

Signed-off-by: zhenwei-intel <zhenwei.liu@intel.com>
Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [eff4de9](https://github.com/vllm-project/vllm/commit/eff4de9be3c901c6ad12cb651de64e4b10ced219)

- **作者**: aoshen02
- **时间**: 2026-11-23T05:55:49Z
- **提交信息**: [Doc] Highlight HTTP-only (no vLLM import) weight updates in training docs (#69333)

Signed-off-by: aoshen524 <aoshen524@gmail.com>
Co-authored-by: aoshen524 <aoshen524@gmail.com>

### [a3309b3](https://github.com/vllm-project/vllm/commit/a3309b31387df003abad5affe544fa7f7d80e735)

- **作者**: Yifei Wang
- **时间**: 2026-11-23T05:40:11Z
- **提交信息**: [Model][PP] Build input embeddings, final norms and LM heads only on the pipeline stages that use them (#67349)

Signed-off-by: Yifei Wang <yifei.w@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [8399da3](https://github.com/vllm-project/vllm/commit/8399da37800dfa13d19e116cb2c838aa33538320)

- **作者**: Yifei Wang
- **时间**: 2026-11-23T04:47:41Z
- **提交信息**: [Core][PP][KV Connector] Expose per-stage KV cache metadata to connectors (#67998)

Signed-off-by: Yifei Wang <yifei.w@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [cbfb900](https://github.com/vllm-project/vllm/commit/cbfb900a7c326861e59551960e9a88584a01224c)

- **作者**: Yan Ma
- **时间**: 2026-11-23T04:22:09Z
- **提交信息**: [XPU] add modelopt_mxfp8 quantization format (#68858)

Signed-off-by: Yan Ma <yan.ma@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [306f47f](https://github.com/vllm-project/vllm/commit/306f47fcfb2bbbfb3b4f43dff6eb4de8992e31bf)

- **作者**: Serge Panev
- **时间**: 2026-11-23T04:03:50Z
- **提交信息**: [Model] Quantize Muse Spark BF16 routed experts with online nvfp4_per_token (#64552)

Signed-off-by: Serge Panev <spanev@nvidia.com>
Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>
Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Thien Tran <gau.nernst@yahoo.com.sg>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Jee Jee Li <jeejeelee@inferact.ai>

### [e3347e7](https://github.com/vllm-project/vllm/commit/e3347e7d088d18b24fdae5378140e545f8454915)

- **作者**: Xinyu Chen
- **时间**: 2026-11-23T03:57:39Z
- **提交信息**: [XPU][Doc] Add vllm-xpu-kernels find-links to wheel install commands (#68626)

Signed-off-by: Xinyu Chen <xinyu1.chen@intel.com>
Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [ed40b63](https://github.com/vllm-project/vllm/commit/ed40b63ee9d55cb7b96af5cbadeb4e6b24a249a7)

- **作者**: Devanshi Jain
- **时间**: 2026-11-23T03:13:15Z
- **提交信息**: [Bugfix][Benchmark] Keep bench serve warmups and ready check out of the prefix cache (#66701)

Signed-off-by: Devanshi Jain <devanshijain@meta.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [19cc9ed](https://github.com/vllm-project/vllm/commit/19cc9ed6f6ff3c22a7c03204a88e7356bf83888f)

- **作者**: aoshen02
- **时间**: 2026-11-23T03:11:40Z
- **提交信息**: [Doc] Fix relative example links in docs/training/weight_updates/engines (#69300)

Signed-off-by: aoshen524 <aoshen524@gmail.com>
Co-authored-by: aoshen524 <aoshen524@gmail.com>

### [2b55f82](https://github.com/vllm-project/vllm/commit/2b55f82b085a765e4c813691d505563b397b4173)

- **作者**: Chaojun Zhang
- **时间**: 2026-11-23T02:40:48Z
- **提交信息**: [Bugfix][XPU] Honor user block size for sliding-window layers on XPU (#68108)

Signed-off-by: Chaojun Zhang <chaojun.zhang@intel.com>
Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>

### [842f74f](https://github.com/vllm-project/vllm/commit/842f74fa8dff2c6792bd68b021c92d8fbf2b93bc)

- **作者**: Yunxiao Ning
- **时间**: 2026-11-23T02:34:07Z
- **提交信息**: [Qwen4Exp] Share FP8 PLE tables over NVLink and RDMA (#68684)

Signed-off-by: Juntian Liu <Juntianl777@gmail.com>
Signed-off-by: yunzhi <ningyunxiao.nyx@antgroup.com>
Co-authored-by: Juntian Liu <Juntianl777@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: v <v@inferact.ai>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: Codex <codex@openai.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [1acec5c](https://github.com/vllm-project/vllm/commit/1acec5c00970441b344b846c9a0e1b5cb27fde0b)

- **作者**: Tony Lin
- **时间**: 2026-11-23T02:19:53Z
- **提交信息**: [BUG] Fix async EPLB worker shutdown ordering (#67589)

Signed-off-by: Tony Lin <tony.lin@intel.com>
Co-authored-by: Shengqi Chen <harry-chen@outlook.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [83710f0](https://github.com/vllm-project/vllm/commit/83710f05617ed75febedeafeca64e22d3f0c80dd)

- **作者**: Tony Lin
- **时间**: 2026-11-23T02:17:31Z
- **提交信息**: [Bugfix] Restore HY4 Flash CUDA platform checks (#69193)

Signed-off-by: Tony Lin <tony.lin@intel.com>
Co-authored-by: Jee Jee Li <pandaleefree@gmail.com>

### [f17a0e4](https://github.com/vllm-project/vllm/commit/f17a0e40d4151b51b9720cacae8e847702da8b7b)

- **作者**: Jee Jee Li
- **时间**: 2026-11-23T02:15:08Z
- **提交信息**: [LoRA] Add private worker-local tensor adapter loading (#69229)

Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>
Co-authored-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: rankYu <70557386+rank-Yu@users.noreply.github.com>

### [d39baa1](https://github.com/vllm-project/vllm/commit/d39baa181a42e310d6823f5b909b052e69ddabda)

- **作者**: Chaojun Zhang
- **时间**: 2026-11-23T02:00:09Z
- **提交信息**: [XPU][CI] Add genai_perf to XPU test requirements  (#63660)

Signed-off-by: Chaojun Zhang <chaojun.zhang@intel.com>

### [3146a9d](https://github.com/vllm-project/vllm/commit/3146a9df41403b8fc30234259444d205974982dd)

- **作者**: June
- **时间**: 2026-11-23T01:13:53Z
- **提交信息**: [Kernel] Let --linear-backend deep_gemm override the DeepGemm model a… (#64872)

Signed-off-by: Jun Zhu <zhujun981661@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [edccd1e](https://github.com/vllm-project/vllm/commit/edccd1e39ede897504babb9a50aa8bba26089bbb)

- **作者**: Woosuk Kwon
- **时间**: 2026-11-23T00:29:43Z
- **提交信息**: [Recipe] Inkling 2 Mini: use the nightly image (#69296)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-11-24
**监控日期**: 2026-11-23
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7929
- **最后更新**: 2026-11-24T05:14:24Z

## 提交统计

- **昨日提交总数**: 31
- **提交者数量**: 23
- **主要提交者**: Wallbreazzz, William R, Hongsheng Liu

## AI分析总结

## vllm-omni 昨日提交分析（共 31 条）

### 1. 主要更新类型
- **CI/构建与测试覆盖**：占比最高（约 10 条），集中于 ROCm/NIGHTLY 流水线扩展
- **性能优化**：约 7 条，涉及扩散模型、语音、量化等
- **模型/功能新增**：约 8 条，覆盖多个新模型与硬件后端
- **Bug 修复**：约 5 条
- **文档更新**：2 条

### 2. 关键变更点与项目方向的关系
- **ROCm/AMD 生态全面扩容**：为 Wan、Qwen VAE、扩散流水线并行、TTS CustomVoice、LTX、Qwen-Image 等在 NIGHTLY 与周级测试中新增 parity/覆盖，直接支撑 README 中"人人可用的全模态模型服务"的多硬件普惠目标。
- **全模态能力深化**：MiniCPM-o 4.5 输入时钟会话、Qwen3-Omni DFlash 与可恢复语音（Model Runner V2）、JoyAI ASR 全异步流、YuE2 与 Duplex 修复，强化语音/双工/视频链路的完整度。
- **扩散模型（图像/视频）提速**：FlashInfer cute-dsl attention、共享 MergedRowParallelLinear（FLUX.1/2、Klein、LongCat）、MiniMax-H3 FlashGen 原生 LoRA、MoSS 长 codec 跨请求批处理，直指"fast and cheap"的性能承诺。
- **多硬件后端**：华为 Ascend（Qwen-Image-2.1 FP16、融合 RoPE）、Intel（MXFP4 AllGather）、摩尔线程（fp8 ignored_layers）、MUSA 诊断，体现异构算力中立性。

### 3. 影响与潜在意义
- CI 密集投入表明项目正从功能迭代转向**生产级质量门禁**，ROCm parity 测试可降低 AMD 回归风险，利好多平台部署信心。
- 性能与流式修复减少尾延迟与内存抖动，提升长会话、双工场景的用户体验，扩大可用模型规模。

### 4. 值得关注的技术点
- **RNG 无漂移的 Qwen3-Omni MTP 图性能恢复**：兼顾吞吐与可复现性，是推理引擎少见的精细权衡。
- **"append fence 永不落后于已接受 fence"** 的双工修复：属并发正确性根因级修复。
- **输入时钟会话与可恢复语音**：为断线重连、长时交互奠定架构基础。
- **CI 中出现 Claude 协助签署**：反映 AI 辅助开发已常态化。

### 5. 对项目发展的总体影响
这批提交呈现"**三条腿走路**"格局：以 ROCm/周级 CI 巩固跨平台可靠性，以扩散与语音性能优化兑现"快与省"，以多模型、多硬件接入扩展"全模态"覆盖面。整体上项目正从能力铺设期迈入**成熟度与生态并重**的阶段，为其全模态推理服务的商业化与社区采纳打下坚实基础。

## 详细提交记录

### [28c34bd](https://github.com/vllm-project/vllm-omni/commit/28c34bdd24627f119e8c75cab6f937da0343e512)

- **作者**: hac17
- **时间**: 2026-11-23T23:02:38Z
- **提交信息**: [CI/Build][ROCm] Add Wan and Qwen VAE patch-decode parity to NIGHTLY (#11043)

Signed-off-by: hac17 <29197483+hacZ17@users.noreply.github.com>
Co-authored-by: hac17 <29197483+hacZ17@users.noreply.github.com>

### [9d75fbd](https://github.com/vllm-project/vllm-omni/commit/9d75fbd48bd02e8acea0a80a17647268b01bef63)

- **作者**: hac17
- **时间**: 2026-11-23T23:01:41Z
- **提交信息**: [CI/Build][ROCm] Add two-GPU diffusion pipeline-parallel parity to NIGHTLY (#11042)

Signed-off-by: hac17 <29197483+hacZ17@users.noreply.github.com>
Co-authored-by: hac17 <29197483+hacZ17@users.noreply.github.com>

### [6ab215d](https://github.com/vllm-project/vllm-omni/commit/6ab215dd0695b9b006e79a8e8739f9db4aebe565)

- **作者**: hac17
- **时间**: 2026-11-23T23:00:42Z
- **提交信息**: [CI/Build][ROCm] Add Qwen3-TTS CustomVoice expansion to NIGHTLY (#11041)

Signed-off-by: hac17 <29197483+hacZ17@users.noreply.github.com>
Co-authored-by: hac17 <29197483+hacZ17@users.noreply.github.com>

### [5973723](https://github.com/vllm-project/vllm-omni/commit/597372343ff4299d296f9802a60f7831886d4aac)

- **作者**: Wallbreazzz
- **时间**: 2026-11-23T21:09:24Z
- **提交信息**: [Performance] Batch MOSS long codec inputs across requests (#10616)

Signed-off-by: Wallbreazzz <110282866+Wallbreazzz@users.noreply.github.com>

### [0c2161e](https://github.com/vllm-project/vllm-omni/commit/0c2161e7694222493d202ae2465821c2bb204546)

- **作者**: hac17
- **时间**: 2026-11-23T20:12:50Z
- **提交信息**: [CI/Build][ROCm] Add Qwen-Image text-to-image documentation to NIGHTLY (#11037)

Signed-off-by: hac17 <29197483+hacZ17@users.noreply.github.com>
Co-authored-by: hac17 <29197483+hacZ17@users.noreply.github.com>

### [c54de9f](https://github.com/vllm-project/vllm-omni/commit/c54de9f4a088ab1cd2e3726fe211e64b5f212099)

- **作者**: hac17
- **时间**: 2026-11-23T20:12:05Z
- **提交信息**: [CI/Build][ROCm] Add Wan VAE spatial-shard decode parity to NIGHTLY (#11036)

Signed-off-by: hac17 <29197483+hacZ17@users.noreply.github.com>
Co-authored-by: hac17 <29197483+hacZ17@users.noreply.github.com>

### [da497e7](https://github.com/vllm-project/vllm-omni/commit/da497e7b15b2b4a268fa527fa8a9c6ee93955d30)

- **作者**: hac17
- **时间**: 2026-11-23T20:10:57Z
- **提交信息**: [CI/Build][ROCm] Promote tiny 4-GPU diffusion and Daily-Omni accuracy in NIGHTLY (#11035)

Signed-off-by: hac17 <29197483+hacZ17@users.noreply.github.com>
Co-authored-by: hac17 <29197483+hacZ17@users.noreply.github.com>

### [14a8e63](https://github.com/vllm-project/vllm-omni/commit/14a8e6399b30f9c8aad8010342df112aea1f9488)

- **作者**: lm10-arg
- **时间**: 2026-11-23T19:31:27Z
- **提交信息**: [CI/Build][ROCm] Promote Wan2.1 VACE weekly coverage (#11039)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>

### [9cc0ee4](https://github.com/vllm-project/vllm-omni/commit/9cc0ee4524e4c80a3574e8d42197f999974516e4)

- **作者**: Tianyao Wu
- **时间**: 2026-11-23T19:25:52Z
- **提交信息**: [Bugfix][YuE2] Reject speech request fields the adapter does not use (#8457)

Signed-off-by: Tianyao Wu <rayroy31@gmail.com>

### [7d0f18e](https://github.com/vllm-project/vllm-omni/commit/7d0f18e7f2c957c8e7e73aa8b31e329e5ea9cc19)

- **作者**: Yinhong Liu
- **时间**: 2026-11-23T18:55:56Z
- **提交信息**: [Model] Support input-clocked sessions for MiniCPM-o 4.5 (#10788)

Signed-off-by: williamLyh <williamliuyinhong@gmail.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [5d6f661](https://github.com/vllm-project/vllm-omni/commit/5d6f661ac784fd6496e8d28e5c42da7f57b32691)

- **作者**: BKtensor
- **时间**: 2026-11-23T18:21:18Z
- **提交信息**: [Bugfix] Duplex: append fence never falls behind the accepted fence (#11032)

Signed-off-by: Jie Jin <jiejin@adventists.ai>
Co-authored-by: Jie Jin <jiejin@adventists.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [d0a4c9e](https://github.com/vllm-project/vllm-omni/commit/d0a4c9e6b4fffb5051878492c11abaf10904b046)

- **作者**: William R
- **时间**: 2026-11-23T17:41:04Z
- **提交信息**: [Test] Add unit tests for chat template, voice stem and final stage helpers (#10213)

Signed-off-by: william ren <wrenuw@amazon.com>

### [2280fd6](https://github.com/vllm-project/vllm-omni/commit/2280fd690cb7b6d890f6b3b2f89cb0148f3ee14d)

- **作者**: lm10-arg
- **时间**: 2026-11-23T17:11:21Z
- **提交信息**: [Bugfix] Restore Qwen3-Omni MTP graph performance without RNG drift (#11031)

### [964e65d](https://github.com/vllm-project/vllm-omni/commit/964e65d5d4ddb68e1fcfd6143d8cf29be6e683af)

- **作者**: Chendi.Xue
- **时间**: 2026-11-23T15:14:19Z
- **提交信息**: [Diffusion][TP] Shared MergedRowParallelLinear for parallel attention + MLP blocks (FLUX.1, FLUX.2, Klein, LongCat-Image) (#9316)

Signed-off-by: Chendi Xue <chendi.xue@intel.com>
Co-authored-by: Thanaji Rao Thakkalapelli <thanaji.rao.thakkalapelli@intel.com>
Co-authored-by: QianCyrus <101633534+QianCyrus@users.noreply.github.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [aec6f25](https://github.com/vllm-project/vllm-omni/commit/aec6f251756da5cea9879435b38b2a365ffb7071)

- **作者**: YeFeng24
- **时间**: 2026-11-23T14:43:00Z
- **提交信息**: [Hardware][Ascend][Diffusion] Qwen-Image-2.1: serve in FP16 on Ascend 300IDUO (#10997)

Signed-off-by: YeFeng24 <yefeng24@huawei.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [d0606f0](https://github.com/vllm-project/vllm-omni/commit/d0606f02fc0118c2621a3d07dfe290372a12a7b2)

- **作者**: psv666
- **时间**: 2026-11-23T13:27:28Z
- **提交信息**: [CI/Build] Run Qwen3-Omni duplex tool tests on Model Runner V2 (#11022)

Signed-off-by: psv666 <2693925048@qq.com>

### [4ce8e7b](https://github.com/vllm-project/vllm-omni/commit/4ce8e7b5bb7e819945a17fe731c6989f450e8084)

- **作者**: Oliver7th
- **时间**: 2026-11-23T11:53:26Z
- **提交信息**: [Hardware][Ascend] Enable fused RoPE for Cosmos3 Nano and Super (#9950)

Signed-off-by: Oliver7th <1105319308@qq.com>

### [e56a099](https://github.com/vllm-project/vllm-omni/commit/e56a099fdfbc063161a2fb38ac03705d77a5b631)

- **作者**: Shiang Zhang
- **时间**: 2026-11-23T11:28:24Z
- **提交信息**: [Model] Add opt-in MiniMax-H3 reference isolation (#9689)

Signed-off-by: zhang-s-a <1120187718@qq.com>
Co-authored-by: dengyunyang <584797741@qq.com>

### [3427710](https://github.com/vllm-project/vllm-omni/commit/3427710b1f7ea82d5933df6ba56624a67a7642a3)

- **作者**: Hongsheng Liu
- **时间**: 2026-11-23T11:21:33Z
- **提交信息**: [Doc] Trace the request lifecycle across engine orchestration and stage runtime (#10928)

Signed-off-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [2ad9929](https://github.com/vllm-project/vllm-omni/commit/2ad9929d30411a8e2ac6db2cd2fb96a2b7feff01)

- **作者**: CYJiang
- **时间**: 2026-11-23T10:06:34Z
- **提交信息**: [Hardware][MUSA] Add MUSA diagnostics to collect_env (#9329)

Signed-off-by: CYJiang <googs1025@gmail.com>

### [f79cc5a](https://github.com/vllm-project/vllm-omni/commit/f79cc5a05aa2d43fb54b54bd70bcd17d38d8d51d)

- **作者**: y-null
- **时间**: 2026-11-23T10:04:34Z
- **提交信息**: [Core] Support Qwen3-Omni DFlash and resumable speech on MRv2 (#10443)

Signed-off-by: y-null <y_null@qq.com>
Signed-off-by: y_null <y_null@qq.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [50b6216](https://github.com/vllm-project/vllm-omni/commit/50b621630278873e7773877246d84e51227326b1)

- **作者**: SYLAR
- **时间**: 2026-11-23T09:40:39Z
- **提交信息**: [Perf][Diffusion] FlashInfer cute-dsl attention: K/V prefix slicing, dense Q/K/V, MiniMax-H3 default on SM10x (#10856)

Signed-off-by: SYLAR <125541396+lishunyang12@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [9b75387](https://github.com/vllm-project/vllm-omni/commit/9b753874d73fb40204418a457d22d802b731d19f)

- **作者**: 汪志鹏
- **时间**: 2026-11-23T07:29:26Z
- **提交信息**: [Model][MiniMax-H3] FastH3 Omni: timeline guides and ControlNet (#10958)

Signed-off-by: princepride <wangzhipeng628@gmail.com>

### [1f4cb36](https://github.com/vllm-project/vllm-omni/commit/1f4cb36f36027853e8cee721c6b71f94f1930581)

- **作者**: wangyu
- **时间**: 2026-11-23T07:20:44Z
- **提交信息**: [CI/Build] Reduce CPU unit test setup and parsing overhead (#10688)

Signed-off-by: wangyu <410167048@qq.com>
Signed-off-by: [Your Name] <your.email@example.com>

### [7441c4b](https://github.com/vllm-project/vllm-omni/commit/7441c4b74a1ac9862ada159909182d31d9385ea0)

- **作者**: R0CKSTAR
- **时间**: 2026-11-23T06:34:51Z
- **提交信息**: [Bugfix][Quantization] fp8: honour ignored_layers match mode (#10908)

Signed-off-by: Xiaodong Ye <xiaodong.ye@mthreads.com>

### [085d7db](https://github.com/vllm-project/vllm-omni/commit/085d7dba33eca00f44753f8c4a5e11bd7c669f38)

- **作者**: wuli666
- **时间**: 2026-11-23T05:32:17Z
- **提交信息**: [Model] Enable full async_chunk streaming on JoyAI ASR duplex profile (#10871)

Signed-off-by: wuli666 <421774554@qq.com>

### [3232f85](https://github.com/vllm-project/vllm-omni/commit/3232f854c7c79fc0525e832481ca66d1824aa55a)

- **作者**: lm10-arg
- **时间**: 2026-11-23T05:04:13Z
- **提交信息**: [Hardware][AMD] Enable LTX weekly coverage on ROCm (#10990)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>

### [099874a](https://github.com/vllm-project/vllm-omni/commit/099874a7a7ef28619176cef8d7ae36cc94a4d6b2)

- **作者**: Zhang Ziyu
- **时间**: 2026-11-23T04:38:34Z
- **提交信息**: Support MiniMax-H3 FlashGen native LoRA for FL2VA and Ref2VA (#10596)

Signed-off-by: zhangziyu <448424548@qq.com>
Signed-off-by: z00899456 <zhangziyu24@huawei.com>
Signed-off-by: princepride <wangzhipeng628@gmail.com>
Co-authored-by: z00899456 <zhangziyu24@huawei.com>
Co-authored-by: princepride <wangzhipeng628@gmail.com>

### [efcd8f2](https://github.com/vllm-project/vllm-omni/commit/efcd8f29954b20ff2ab8374ed49673c5df709406)

- **作者**: lm10-arg
- **时间**: 2026-11-23T02:28:42Z
- **提交信息**: [CI/Build][ROCm] Add LongCat, Boogu, Flux, and Krea2 weekly coverage (#10972)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>

### [4495def](https://github.com/vllm-project/vllm-omni/commit/4495defbc66350899f02abb3f90a4acc60a2b6c4)

- **作者**: Yi Liu
- **时间**: 2026-11-23T02:19:54Z
- **提交信息**: [Bugfix][DLO] Support packed MXFP4 in AllGather (#10586)

Signed-off-by: yiliu30 <yi4.liu@intel.com>
Co-authored-by: WeiQing Chen <40507679+david6666666@users.noreply.github.com>

### [d43ccfa](https://github.com/vllm-project/vllm-omni/commit/d43ccfac95effb191457895f74e93237ad7a66c6)

- **作者**: WeiQing Chen
- **时间**: 2026-11-23T01:24:34Z
- **提交信息**: [Doc] Update vLLM-Omni WeChat QR code (#10974)

Signed-off-by: David Chen <530634352@qq.com>

---
