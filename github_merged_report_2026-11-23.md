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
- **主要提交者**: Coach257, Kaiyu Shi

## AI分析总结

## 1. 主要更新类型

本次批次包含两项**功能新增**，分别属于算子（ops）与模型（model）层，同时伴随少量文档（docs）更新。整体属于能力扩展而非修复或重构。

## 2. 关键变更点及与项目方向的关系

- **[9f533f4] 配置驱动的按站点选择 op 行**：允许从同一个配置字段为不同站点（site，如不同硬件/集群环境）挑选不同的算子实现，涉及 ops、model、docs 三个模块，并由 AI 辅助工具（Cursor）协作完成。
- **[df1accc] 原生 NPU 跨卡/分块交叉熵**：为昇腾 NPU 硬件补齐原生的 chunk cross entropy 算子。

这两项变更直接呼应 README 中 "Model-Centric Distributed Recipe Zoo" 的核心定位——VeOmni 的目标是用统一配方扩展**任意模态**训练，而"任意硬件适配"是配方能否落地的前提。配置化的 op 选择机制让同一份训练配方能在多站点异构环境中复用；NPU 原生算子则填补了国产硬件后端的关键缺口。

## 3. 对项目的影响和潜在意义

- **可移植性提升**：用户无需为不同环境维护多套配置，降低了跨集群、跨硬件迁移的门槛，符合"recipe zoo"一处编写、多处运行的愿景。
- **硬件生态扩展**：原生 NPU 交叉熵通常意味着避免 host-device 往返、采用融合 kernel，在训练稳定性与吞吐上优于外挂实现，使项目对国内大规模训练场景更具吸引力。
- **协作模式信号**：出现 Cursor 联署提交，说明项目已引入 AI 辅助开发流程，后续变更节奏可能加快，但需关注 review 质量。

## 4. 值得关注的技术点

- 配置字段如何在保持**向后兼容**的前提下同时表达"默认行"与"按站点覆盖行"，其 schema 设计值得跟进。
- NPU chunk cross entropy 的**数值精度与显存分块策略**，以及与 Flash-Attention 类算子的配合是否会影响长序列训练。
- 该配置机制是否会被推广到更多算子维度（如通信、优化器），是判断其为局部补丁还是架构级抽象的关键。

## 5. 对项目发展的整体影响

结合 README，VeOmni 强调以模型为中心的分布式配方复用。本次提交从**硬件抽象层**和**算子完备性**两个方向夯实了这一基础：前者让配方可跨站点分发，后者让配方在 NPU 上真正跑得动、跑得快。二者共同推动项目从"研究性框架"向"可工程化落地的多模态训练底座"演进。后续若能配套自动化测试覆盖多站点配置与 NPU 算子数值一致性，将显著增强社区采用信心，也会让文档中承诺的跨硬件能力更具说服力。

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

## LightX2V 昨日提交分析

### 1. 主要更新类型
**功能增强** — 扩展 H3 因果音频历史长度从原有设置到 9 个 chunk。

### 2. 关键变更点与项目方向的关系

- 该提交属于**音频-视频联合生成**（Audio-Video Co-generation）能力的增强，将因果音频模型（H3）的音频历史上下文窗口扩大至 9 个 chunk。
- LightX2V 作为轻量级视频生成推理框架，持续优化音视频生成质量与一致性。此变更直接提升音频生成的**长时序连贯性**，与项目"轻量高效生成高质量音视频"的核心目标一致。
- H3 是项目中采用的因果音频建模方案，增大历史窗口意味着在推理时能利用更长的音频上下文，减少音频片段间的不连续感。

### 3. 对项目的影响和潜在意义

- **音频质量提升**：更长的因果历史使模型能感知更完整的音频结构，降低长视频场景中音频的断裂感和节奏漂移问题。
- **推理开销权衡**：历史 chunk 从较小值增至 9，会增加 KV cache 的显存占用和计算量，对轻量化推理框架而言需要在质量与效率间取得平衡，这体现了项目在"轻量"与"效果"间的持续调优。
- **为长视频音视频生成铺路**：支持更长音频上下文是生成更长、更连贯视频的基础能力之一。

### 4. 值得关注的技术点

- **因果（Causal）音频建模**：采用单向注意力机制，意味着推理时可增量式处理音频流，适合流式/自回归生成场景，保持了推理效率。
- **Chunk 化处理策略**：以 chunk 为单位管理音频历史，是平衡显存占用与上下文长度的工程化方案，9 个 chunk 的选择可能经过 benchmark 验证。
- **配置可调性**：此类参数扩展通常伴随配置项开放，便于不同硬件条件下灵活调整。

### 5. 对项目发展的意义

LightX2V 定位为轻量高效的视频生成推理框架，README 中强调其推理性能与文档支持。此提交表明项目在**音视频协同生成**这一方向上持续深耕——不仅关注视觉质量，也在同步提升音频生成的一致性和完整性。对于一个以"Light"为名的框架来说，在有限的计算预算下扩展音频上下文，反映了团队对**推理效率优化与生成质量**的精细化管理。这类底层能力增强将为后续更复杂的音视频生成任务（如长视频配音、对话视频生成）奠定基础，推动项目从纯视频生成向**多模态内容生成**平台演进。

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
- **星标数**: 6995
- **最后更新**: 2026-11-24T04:05:20Z

## 提交统计

- **昨日提交总数**: 20
- **提交者数量**: 12
- **主要提交者**: Brandon Zhang, Jimmy Zhou, Cindy Zhang

## AI分析总结

# FlashInfer 昨日（20 个提交）提交分析

## 一、主要更新类型
以**测试维护与修复**为主（约 9 条），其次是**性能优化**（5 条）、**功能新增**（4 条）、**基准测试扩展**（2 条）与 **CI 调整**（1 条，临时禁用 H100 任务）。

## 二、关键变更及与项目方向的关系
- **新 GEMM 后端**：SM107（Rubin）专用 MXFP8 小 M GEMM，因该硬件无原生 warp 级 fp8 MMA，用 `cvt.rn.scaled` 将操作数转 bf16 并折叠块缩放后以 bf16 MMA 累加，仅在 34 个实测优势形状上启用；快速 TF32 router GEMM 用 CuTe DSL 低 M split-K 配合 PDL，在 CUDA graph 内连续调用场景显著优于 cuBLAS，填补 fp32 输入 GEMM 空白。两条均以严格 allowlist 路由保证不劣化现有路径。
- **基准测试扩展**：统一基准的 MoE 例程从 11 增至 14、`unified_moe` 配对从 34 增至 59，杂项例程从 39 增至 57，使 Frost、Prims-TS、CuTe-DSL 等新后端可被量化评估。
- **测试健壮性**：拆分超时的解码测试、修复采样器间歇性失败与架构断言（SM 10.7 共享内存容量变更）、CUPTI 无记录误报、`scale_out` 越界写、参考实现舍入顺序与内核不一致等；MoE all-reduce、Cake、b12x FP4 等测试真正接入 CI。这些均属测试自身缺陷而非内核回归，暴露出测试未在多 GPU/内部 CI 跑通的问题。
- **微优化**：NVFP4 per-token 量化跳过 scale 零填充，省去每次调用的 kernel launch，量化延迟降低约 25–30%；Prims-TS softmax 将可见 K 范围每 work tile 只算一次，覆盖 FMHA 与 MLA 多路径；MLA 融合原生 NVFP4 SM120 稀疏 prefill，相比分离内核提速 1.3–1.5×。
- **功能新增**：`trace_apply` 支持列出已安装内核包并释放被 CUDA graph 冻结的包绑定。
- **精度与解码优化**（来自 TensorRT-LLM 移植）：MoE finalize 全归约融合 kernel 改为 fp32 累加、Lamport 写出时单次舍入，与 trtllm-gen 对齐；MLA 批量解码 Cake 后端新增 FP8 page-64 split reducer，将单查询行 128 个头分摊到最多 128 个 CTA（原 16 个），按 batch×q_len、KV split 数与共享内存条件选择路径，输出与 LSE 位级一致。

## 三、对项目的影响和潜在意义
新增 GEMM 后端直接提升 Rubin 与 MoE router 场景吞吐；量化省 launch 与 softmax 边界缓存是推理热路径微优化，对 LLM 服务吞吐有实际意义；MoE 精度修复属正确性收益，风险低。基准覆盖扩大使性能回归可被及时发现。多 GPU CI 补齐后，通信内核改动的回归将被提前拦截；参考实现与内核舍入对齐使数值测试真正有判别力。临时禁用 H100 任务（关联事故 #9893）表明存在待排查的环境问题，短期降低该硬件覆盖。多条提交标注为 v0.7.6 cherry-pick 候选，说明团队正为发布收尾做稳定化。MLA 优化针对 B200/GB300 小 batch 解码：相对旧 Cake 版本 geomean 加速约 1.148×（B200）/1.145×（GB300），峰值近 1.59×，但相对最快非 Cake 后端仍约 0.92×/0.89×，`backend="auto"` 仍自动择优。

## 四、值得关注的技术点
1. SWIZZLED_128×4 布局 buffer 尺寸线性计算与 `round_up` 差异导致 43KB 越界写，且因落在 PyTorch 内存池内侥幸通过——典型潜伏内存安全问题。
2. 数值测试采用"恰好可表示输入 + FP32 独立参考 + 零容差"策略，消除容差掩盖，值得借鉴。
3. 每 tile 一次的边界缓存 packed 成 32-bit word 存 SMEM/task cache；作者记录 D256 路径反例（ptxas 寄存器拷贝导致回退 3–8%），体现精细性能剖析功底。
4. fp32 累加单次舍入与 CTA 粒度 split-KV 自适应并行度，是混合精度与 GPU 资源调度的典型实践。
5. AI 辅助开发（多条 Codex/OpenAI 提交）在 PR 中明确标注，流程透明。
6. 测试改为按设备能力推导参数（ring depth、共享内存预算）而非硬编码，是跨架构测试的正确范式。

## 五、结合 README 项目背景的发展影响
FlashInfer 定位为高性能 GPU 推理 kernel 库，本日提交沿四条主线推进：**硬件代际扩张**（SM107/Rubin 与 GB300 专用 kernel、架构适配测试）、**性能基础设施**（统一基准大幅扩大量化所有后端）、**发布质量**（清理 CI 与测试债务为 v0.7.6 铺路）、**与 TensorRT-LLM 生态的代码同步**（融合通信算子与 MLA 后端移植）。这些工作共同强化项目在多后端、多硬件推理加速上的竞争力，并通过 allowlist 与严格测试确保新增优化不破坏既有稳定性。总体体现了项目从功能广度扩张向覆盖度、可度量性与发布稳定性并重的成熟化演进。

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

## 提交分析总结（hao-ai-lab/FastVideo，昨日第 1/1 批）

### 1. 主要更新类型
- **Bug修复**：针对流式（Streaming）会话生命周期管理的缺陷修复，同时可能伴随少量文档/行为对齐性质的调整。

### 2. 关键变更点及与项目方向的关系
- 修复内容聚焦于流式会话的**终止条件**：会话现在严格按照文档约定的 `segment_cap`（分段上限）、`session_timeout`（会话超时）以及 **error frames（错误帧）** 来正确结束，而不是此前可能存在提前、延迟或遗漏终止的情况。
- 与项目整体方向的关系：FastVideo 是一个围绕高效视频生成/推理的服务化框架，README 中链接了 Uniserve、Dreamverse Harness 等周边生态，说明项目正朝着**可部署、可服务化、生产可用**的方向发展。流式接口是实时视频服务的核心通道，其会话管理的正确性直接关系到服务能力的可靠性。此修复表明团队在推进功能的同时，正系统性地加固流式服务的健壮性，使代码行为与对外文档保持一致。

### 3. 对项目的影响和潜在影响
- **直接收益**：消除流式会话可能无法按预期终止的隐患，减少服务器端资源泄漏（如长期占用的连接/显存）、僵尸会话堆积等问题。
- **稳定性提升**：超时与错误帧路径的规范化处理，使异常场景下的行为可预测，有利于大规模并发服务下的故障隔离。
- **潜在意义**：为下游依赖该流式接口的集成方（Cookbook 示例、Harness 等）提供了更可靠的基础，降低集成调试成本，也是发布稳定版本前必要的质量收敛。

### 4. 值得关注的技术点
- **三重终止条件的协同语义**：`segment_cap`、`session_timeout`、error frame 三者之间的优先级与竞态处理——当多个条件同时触发时如何保证会话恰好终止一次（exactly-once termination），是流式状态机设计的经典难点。
- **错误帧机制**：通过在协议层注入 error frame 来通知客户端终止，而非直接断开连接，体现了对客户端体验和协议完整性的考量。
- **行为与文档对齐**：修复以"documented"行为为基准，说明项目有较严格的接口契约意识，这类修复通常涉及回归测试的补充。

### 5. 结合项目背景对项目发展的影响
- README 显示 FastVideo 生态正在扩展（Documentation、Cookbook、Uniserve、Harness 等多入口），项目从"研究代码"向"工程化平台"演进。流式服务是这类平台对外暴露的关键 API，其可靠性直接影响用户对整个生态的信任度。
- 此类小而精准的 bugfix 表明项目已进入**成熟期维护阶段**：在持续迭代新功能之外，团队开始投入精力修复边界问题、对齐文档承诺，这是开源项目从功能堆叠走向生产就绪的典型信号。对潜在采用者而言，这类提交比新功能更能体现项目的工程严谨性和长期维护意愿。

**总结**：本次提交是一次针对流式会话终止逻辑的高质量 bugfix，它强化了 FastVideo 服务化路线中的可靠性基础，体现了项目在向生产级视频服务平台演进过程中对协议契约和资源管理的重视。

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
- **最后更新**: 2026-11-23T19:26:24Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Sara Han

## AI分析总结

## huggingface/diffusers 昨日提交分析（第 1/1 批）

### 1. 主要更新类型

- **重构（命名规范化）**：这是一次模块命名层面的重构提交，核心操作是将 `P-H3-Image` 相关模块统一更名为 `P-Image-OSS`。
- **文档更新与弃用标注**：同时对模块别名进行了文档澄清，并对旧命名实施了弃用（deprecated）标记。

### 2. 关键变更点及其与项目整体方向的关系

- **涉及范围广**：变更覆盖了 autoencoder（自动编码器）、condition embedder（条件嵌入器）、modular pipeline（模块化流水线）、文档及测试，是一次贯穿模型组件、管线架构和配套资源的全链路重命名。
- **兼容性策略**：旧的 `p_h3_image` 模块作为废弃别名保留，体现了 Diffusers 项目一贯重视的向下游用户和平滑迁移体验的工程原则。
- **与项目方向的关联**：Diffusers 致力于提供统一、清晰、模块化的扩散模型生态。统一命名有助于减少社区认知负担，避免同一模型因多个内部代号造成混乱，这与项目 README 中体现的"开放、规范、易用"理念一致。

### 3. 对项目的影响和潜在意义

- **用户体验层面**：对新用户而言，`P-Image-OSS` 更直观地表明其开源属性（OSS），降低了学习门槛；对老用户，别名机制确保既有代码不会立刻失效，降低了破坏性变更风险。
- **维护层面**：统一命名有助于后续 CI、文档搜索、示例代码和社区讨论中的一致性，减少维护成本和"同物异名"导致的碎片化问题。
- **发布层面**：这类命名整理通常出现在模型正式开源发布或进入主分支的前后节点，暗示该 P-Image 模型正在逐步走向对外可用状态。

### 4. 值得关注的技术点

- **别名与弃用机制的设计**：项目采用了"保留旧模块 + deprecated 别名"的过渡方案，而不是直接删除，是大型开源库做 breaking change 的典型范式，值得其他 ML 框架借鉴。
- **合并冲突处理**：提交信息提到"fix: fix mismatch after merging"，说明该重命名发生在功能分支与主干同步的过程中，需注意此类大规模重命名在多人协作下可能引入的隐患。
- **AI 协作痕迹**：提交者署名包含 Claude Opus 5.5，反映出 HuggingFace 团队在代码协作中已实际引入 AI 辅助开发，这是一个行业趋势信号。
- **测试覆盖**：重命名同步更新了测试，说明团队对模块命名变更的回归验证较为严谨。

### 5. 基于 README 背景对项目发展的影响

Diffusers 作为 HuggingFace 扩散模型生态的核心库，其 README 强调了 Apache 2.0 许可和社区驱动的开放协作模式。本次提交通过规范化命名、保留兼容层、同步文档与测试，体现了项目在"功能丰富"与"工程规范"之间的平衡取向：

- **长期意义**：这类重构虽不带来新的模型能力，但为后续模型接入和社区贡献铺平了道路，是健康开源项目"先理顺、再扩展"的典型做法。
- **社区信号**：P-Image-OSS 的命名调整和弃用标注，暗示相关模型资产正在从内部代号向公开发布过渡，社区可以关注其后续在模型 Hub 中的正式上线与示例发布。

综上，这次提交是一次以命名统一和兼容性保障为核心的工程重构，虽然表面上是"改名"，实则对 Diffusers 的生态一致性、用户迁移体验以及该模型的开源发布节奏都具有实质性的推动作用。

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

## DiffSynth-Studio 昨日提交分析（第1/1批）

### 1. 主要更新类型
本次提交以**功能新增**为主，辅以文档更新和少量修复。核心是两项重大特性：**统一序列并行（Unified Sequence Parallel）**和**KV-Cache压缩**的全面支持，以及超分辨率模型DetailScale-SR的接入。

### 2. 关键变更点及与项目方向的关系
- **序列并行（#1851）**：这是本批最重量级的更新，一次性覆盖了22+个pipeline（含13个简单pipeline、9个更多pipeline、KV-Cache模型、H3-Image等），支持双流并行、padding、集合通信与上下文管理。这与项目"高效推理与部署"的核心方向高度一致——通过并行化降低大规模视频/图像生成模型的显存和延迟瓶颈。
- **KV-Cache压缩（#1844）**：支持KV-Cache压缩并扩展到Wan-Animate-2，属于推理效率优化的关键路径，直接服务于自回归/流式生成场景的长序列推理。
- **DetailScale-SR（#1845）**：新增超分辨率模型支持，丰富了项目的图像处理能力矩阵。
- **文档与示例更新（#1846, #1847, #1852, #1848）**：同步补充并行文档、脚本、示例，保证新功能的可用性和可发现性。

### 3. 对项目的影响和潜在意义
- **可扩展性大幅提升**：序列并行的统一框架使用户无需为每个模型单独定制并行策略，降低了分布式推理的使用门槛。
- **推理效率显著提升**：KV-Cache压缩与并行化的组合，使DiffSynth-Studio在大规模视频生成模型（Wan系列等）上具备更强的生产级部署能力。
- **生态完善**：持续的文档和示例更新降低了新用户上手成本，有利于社区贡献者扩展新pipeline。

### 4. 值得关注的技术点
- **序列并行的通用化设计**：通过collective/context抽象、sp hook/backend/state三层机制实现跨pipeline的统一并行接口，架构思路值得借鉴。
- **双流（double stream）并行支持**：适配了DiT类双流架构，体现了对主流模型结构的深度适配。
- **对多种模型的兼容性打磨**：包括对LTX2.5、Wan2.2-5B、ERNIE等模型的专项修复，以及对某些模型的guard保护，反映了并行功能已达到较高的成熟度。
- **KV-Cache与并行的协同**：KV-Cache模型同时获得序列并行支持，说明两者在架构层面是打通的。

### 5. 对项目发展方向的影响
DiffSynth-Studio作为ModelScope旗下的高效扩散模型合成/推理框架，README明确其定位是面向多模态生成模型的高效训练与推理。本批提交表明项目正从"功能覆盖"阶段转向**"高性能工程化"阶段**——通过序列并行和KV-Cache压缩两大引擎，将推理效率和可扩展性推向生产级水平，同时保持对广泛模型生态的兼容，这将巩固其作为国内主流扩散模型推理框架的竞争地位。

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
- **星标数**: 38998
- **最后更新**: 2026-11-24T05:00:03Z

## 提交统计

- **昨日提交总数**: 25
- **提交者数量**: 20
- **主要提交者**: maocheng23, sherdavincl9, qiuhongchen

## AI分析总结

## sgl-project/sglang 昨日提交分析（共25条）

### 1. 主要更新类型分布

- **CI/CD 与基础设施**：约7条，占比最高，涉及Lark通知、slash命令处理、AMD/NPU/Intel多平台CI测试策略
- **Bug修复**：约10条，覆盖调度器、linker、MoE路由、硬件特定问题（qknorm、hicache、CPU量化）
- **性能优化**：4条，集中在AMD QSA解码、linker KV预取、Triton确定性解码
- **功能新增**：2条，kernel_plugins的DFLASH worker绑定、NPU DSA-TAIL的PD传输与解码回退
- **重构与文档**：各1条，运行时核心死代码清理、cookbook新增Ling-3.2-air模型

### 2. 关键变更与项目方向的关系

- **多硬件生态扩展**是核心主题：AMD gfx950上的AITER融合稀疏解码、ROCm MQA日志加速、NPU的MemFabric大页flag移除与DSA-TAIL支持、Intel XPU容器共享与Arc Pro B70扩散性能基线，均体现项目向多后端推理扩展的战略
- **CI可靠性建设**反映项目在快速增长中对工程规范的重视：移除不稳定的runner健康卡片、统一handler从默认分支运行、AMD上迁移73个CUDA per-PR测试、NPU失败时收集pod日志
- **调度器与linker的正确性修复**（如finished prefill请求释放时序、prefetch KV与session绑定、slot位置解析提前到forward fence）直接关系推理服务的稳定性和性能一致性

### 3. 对项目的影响和潜在意义

- 多平台CI矩阵的完善将降低硬件特定回归风险，提升社区贡献的合并信心
- MoE路由softcap权重有限化修复了大logits下的数值稳定性问题，对大规模MoE模型部署至关重要
- 运行时核心重构（1/4）预示后续将有系统性的代码质量提升
- NPU DSA-TAIL的PD传输能力强化了分离式推理架构在华为硬件上的可用性

### 4. 值得关注的技术点

- **DFLASH worker轮次绑定**（#52495）：kernel_plugins允许worker声明自身轮次阶段，支持运行时组合式调度，是推理引擎内核插件架构的重要演进
- **linker的slot解析优化**（#49463）：将KV slot位置解析提前到forward fence之前，减少了同步等待
- **确定性Triton解码块分配**（#47410）：固定解码块数量以保证大split预算下的确定性行为
- **draft megakernel降级机制**（#52438）：不满足条件时优雅降级而非拒绝服务，提升了兼容性

### 5. 对项目发展的整体影响

这些提交共同强化了SGLang作为多硬件、高性能LLM推理框架的工程基础。README定位的"Fast inference for LLMs and multimodal models"在本次提交中得到多维度支撑：AMD/NPU/Intel三线并进的性能优化直接兑现了"Fast"承诺；调度器、linker、MoE的正确性修复保障了推理服务的生产可靠性；而CI基础设施和运行时重构则为后续更复杂的特性开发奠定了可维护性基础。项目正从单一GPU优化走向全栈硬件适配与工程规范化并重的成熟阶段。

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

# `vipshop/cache-dit` 昨日提交分析

## 1. 主要更新类型

本次提交批次以 **功能新增** 为主，辅以 **文档完善** 和少量 **API 重构**。核心围绕 SVDQ（奇异值分解量化）量化能力的大幅扩展，没有涉及 Bug 修复。

## 2. 关键变更点与项目方向的关系

- **新增打包权重格式（W1A4/W2A4/W3A4）**：支持 1/2/3-bit 权重搭配 4-bit 激活值的混合精度推理，直接服务于 README 中"Quantization"这一核心定位。
- **新增 W4A8 融合内核（#1388）**：在 4-bit 权重、8-bit 激活的场景下提供融合算子，提升量化推理效率。
- **FP8 检查点序列化与统一算子命名（#1386）**：实现 FP8 权重的完整保存/加载回环，为后续 FP8 推理铺路。
- **默认启用三阶段编码（three-stage codec）并新增 rank256 支持**：W1/W2 权重默认走三阶段量化管线，量化 API 统一收敛，提升了默认体验。
- **支持 per-2 内部分组量化**：更细粒度的量化分组策略，优化精度与压缩率的平衡。

## 3. 对项目的影响和潜在意义

- **显著降低 DiT 推理显存占用**：W1A4 等极低比特格式可将权重压缩至 1/8~1/4，配合 CPU Offload 能力，使大模型在消费级 GPU 上可部署。
- **量化生态趋于完善**：从 FP8 到 4-bit、3-bit、2-bit、1-bit 形成完整梯度，用户可根据硬件和精度需求灵活选择。
- **API 收敛降低使用门槛**：统一量化 API 和三阶段默认化，减少用户手动调参成本。
- **大量文档和 Gallery 更新**：内存账目、数学原理、编译示例等配套完善，增强可复现性。

## 4. 值得关注的技术点

- **三阶段量化编码**（three-stage codec）：将 SVD 分解、量化、打包拆分为三个阶段，是本次打包格式的底层架构。
- **W1A4 的实验性 rank 阈值**：极低比特量化中 SVD 分解的秩选择对精度影响巨大，文档化阈值有助于工程落地。
- **打包 A4 的内存账目精确到权重和激活分开统计**：对显存敏感的推理场景至关重要。
- **FP8 检查点回环测试**：保证量化状态在训练/推理间的无损迁移。
- **融合内核设计（W4A8）**：减少量化反量化开销，是实际吞吐提升的关键。

## 5. 对项目发展的影响

cache-dit 的 README 定位是"Cache + Parallelism + Quantization + CPU Offload 的 DiT 推理引擎"。本次提交批次将 **Quantization** 能力推向了极致——覆盖 1~8 bit 全谱段、支持打包格式和融合内核、统一 API 并完善文档。这使得项目从"能跑量化推理"进化为"提供工业级量化推理方案"，与 Cache 和 Offload 能力协同后，有望将 DiT 推理的部署门槛进一步降低，吸引更多追求极致效率的用户。三阶段编码的架构设计也为未来更激进的压缩策略留下了扩展空间。总体而言，这批提交是项目在量化方向上的一次里程碑式推进。

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
- **星标数**: 97436
- **最后更新**: 2026-11-24T04:56:49Z

## 提交统计

- **昨日提交总数**: 68
- **提交者数量**: 51
- **主要提交者**: Haobin Guo, Nicolò Lucchesi, wangxiyuan

## AI分析总结

# vLLM 昨日提交综合分析（68 个提交）

## 一、主要更新类型
Bug 修复占比最高（约 45%），覆盖内核、量化、KV 缓存、Tracing、模型加载及 XPU/EPLB 等路径；性能优化集中在 MLA、AWQ、MoE 等内核层面；CI 与基础设施涉及 ROCm、XPU、CPU 镜像和测试流水线加固；此外还有量化新格式、投机解码、流水线并行（PP）等功能新增，以及文档、代码所有者等治理变更。

## 二、关键变更与项目方向
- **量化生态扩张与收敛**：MXFP8 进入 FlashInfer CuteDSL 专家内核（服务 DeepEP 低延迟）、nvfp4 在线量化、XPU 新增 modelopt_mxfp8 格式，同时正式弃用 TorchAO，体现"cheap serving"下对低比特推理的聚焦与后端栈精简。
- **多硬件支持深化**：ROCm（缓存基镜像、int8 精度修复、sliding-window 前缀预填充优化）、XPU（CI 扩展、滑窗层尊重用户 block size、依赖补充）提交密集，跨硬件可移植性是核心战略。
- **分布式与长上下文**：KV Connector 系列修复（HF3FS 流水线并行 rank 推导、MLA 内核行拆分、逐阶段 KV 元数据暴露）、Mooncake、KV Offload 修复，支撑 disaggregated serving。
- **性能优化**：TRITON_MLA 融合调度（1.7x 内核收益）、GLM-5.3-Flash 融合 all-reduce（8.7% E2E 吞吐）、Gemma3n CUDA graph 修复、Qwen4Exp FP8 PLE 表跨 NVLink/RDMA 共享，直接兑现 "fast and cheap" 承诺。
- **新模型与投机解码**：HY4 Flash / DFly 多项改进（NVFP4 目标方案、DecodeBenchConnector、CUDA 平台检查）、Qwen GDN 复用于 OLMo、DeepSeek V4 修复，反映对前沿模型的快速跟进。

## 三、对项目的影响与潜在意义
大量并发、竞态、精度类修复（MLA LSE 竞态、ROCm logit 漂移、异步 EPLB 关闭顺序、prompt logprobs 填充）显著降低生产环境风险，提升多硬件平台可用性。内核与融合优化提升同等硬件的服务能力，跨节点 FP8 表共享减少重复加载开销，对大规模 MoE 部署有实际收益。LoRA 私有 worker 本地张量适配器加载扩展了多租户与动态适配能力。PP 与 KV Connector 演进为弹性 disaggregated serving 铺路。测试选择器、gcc 重试、deep_gemm 覆盖规则等 CI 调整保障集成可靠性，支撑高频合入节奏。

## 四、值得关注的技术点
- **AI 协作开发常态化**：大量提交含 Claude、Codex、Copilot、vllm-agent 等 Co-authored-by，AI 已深度参与开发流程。
- **CuTe DSL 成为内核新基座**：FlashInfer CuteDSL、CuTe DSL A2A reduce（DCP 稀疏 MLA，Kimi K3.1）显示 NVIDIA 主导的 DSL 路线正渗透核心内核。
- **Grace EGM + NVLink 分片（Engram）**：面向 Grace 平台的新型内存层级利用。
- **deep_gemm 后端强制覆盖**：允许命令行覆盖模型默认配置，体现后端选择的灵活性。

## 五、整体影响
昨日变更展现 vLLM 高速迭代的典型样态：以 Bug 修复保稳定、以内核优化兑现性能、以 ROCm/XPU 投入扩大硬件覆盖、以量化与投机解码降低成本、以 KV Connector/PP 支撑 disaggregated serving 演进。这与 README 中 "Easy, fast, and cheap LLM serving for everyone" 的目标高度一致——项目正从"能跑"走向"跨硬件、高可靠、极致性价比"的生产级服务平台，并通过治理提交与文档完善维持社区健康度。

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
- **星标数**: 7928
- **最后更新**: 2026-11-24T03:28:57Z

## 提交统计

- **昨日提交总数**: 31
- **提交者数量**: 23
- **主要提交者**: Shiang Zhang, Wallbreazzz, Tianyao Wu

## AI分析总结

## 一、主要更新类型

本批 31 个提交以 **CI/构建与硬件验证**（约 11 条，以 ROCm 为主）、**性能优化**（扩散模型与语音推理）、**Bug 修复**（量化、双工、TTS）、**新模型/硬件支持**、**文档与测试补充**为主。整体呈现"验证覆盖扩张 + 多模态性能推进"的格局。

## 二、关键变更点与项目方向的关系

- **CI/ROCm 扩展是最大主题**：为 Wan、Qwen VAE、扩散流水线并行、Qwen3-TTS、Qwen-Image 等持续将 parity 测试加入 NIGHTLY/周度覆盖，对应 README 中"cheap、fast 的 omni 模型服务"目标——通过 AMD 硬件上的持续回归保障推理正确性与可移植性。
- **多模态/扩散性能优化密集**：MOSS 长 codec 跨请求批处理、FlashInfer cute-dsl attention（前缀 K/V 切片、SM10x 默认启用 MiniMax-H3）、FLUX/LongCat 等共享 MergedRowParallelLinear 并行、Qwen3-Omni MTP 图性能恢复等，直接提升吞吐与延迟。
- **语音双工与会话能力完善**：MiniCPM-o 4.5 输入时钟会话、JoyAI ASR 全异步 chunk 流式、Qwen3-Omni DFlash 与可恢复语音（MRv2）、双工 fence 修复，强化实时语音交互这一 omni 核心场景。
- **多硬件生态推进**：Ascend（Fused RoPE、Qwen-Image-2.1 FP16）、MUSA 环境诊断、AMD LTX 覆盖，延续项目跨后端适配的开放性。

## 三、对项目的影响和潜在意义

1. **验证成本与信心提升**：ROcm nightly 矩阵扩张意味着非 NVIDIA 路径回归更早暴露问题，降低发布风险。
2. **服务性能瓶颈缓解**：注意力/并行层与批处理优化将直接改善扩散生成与长音频推理成本，贴合"cheap"承诺。
3. **稳定性增强**：fp8 ignored_layers 匹配模式、duplex fence、TTS 字段校验等修复减少生产环境边缘故障。
4. **开发体验改善**：CPU 单测开销削减、单元测试补充、请求生命周期文档与微信二维码更新提升社区可维护性。

## 四、值得关注的技术点

- **FlashInfer cute-dsl 注意力**在扩散 K/V 前缀切片场景的落地与 MiniMax-H3 默认策略；
- **共享 MergedRowParallelLinear** 对 attention+MLP 的张量并行融合（多扩散模型复用）；
- **MOSS 跨请求长 codec 批处理**与异步 chunk 流式的组合对 ASR 双工延迟的影响；
- **DLO packed MXFP4 AllGather**、fp8 层忽略匹配模式等量化细节；
- **CUA 协作痕迹**（Claude Fable/Opus 等 co-author）出现在模型支持与双工修复中，值得关注质量把关方式。

## 五、结合 README 背景对项目发展的意义

README 定位是"人人可用的易、快、省 omni 模态模型服务"。本批提交表明项目正沿三条主线推进：**其一**，以 ROCm/Ascend/MUSA 为代表的后端中立验证体系日臻完善，使"easy"扩展到更多硬件；**其二**，通过注意力融合、并行共享、批处理等手段兑现"fast 与 cheap"；**其三**，语音双工、会话时钟、扩散并行等 omni 特有能力持续完善，夯实核心差异化场景。短期内项目可信度与覆盖度将显著提升，但 nightly/周度矩阵膨胀也预示未来需关注 CI 时长与维护成本的平衡。综上，这些提交使 vllm-omni 在多后端正确性保障、推理性能与实时语音体验三方面同步演进，整体朝着稳定、可扩展的 omni 服务平台稳步发展。

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
