# GitHub Stars 合并报告 - 2026-07-17

**合并日期**: 2026-07-18
**监控日期**: 2026-07-17
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


**报告日期**: 2026-07-18
**监控日期**: 2026-07-17
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2093
- **最后更新**: 2026-07-17T21:27:57Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: 鐘天楽, Bin Jia

## AI分析总结

根据提供的提交记录和项目背景，以下是昨日更新的要点总结：

---

### 1. 主要更新类型
- **功能新增 (feat)**：暴露检查点早停设置（#926）
- **基础设施/杂项 (chore)**：在 CUDA 13 镜像中安装 OpenSSH 服务器（#937）
- **文档更新**：随功能新增更新了配置、分布式、训练器等相关文档

### 2. 关键变更点与项目方向的关系
- **安装 OpenSSH 服务器**：为 Docker 镜像增加 SSH 访问能力，方便用户远程调试、执行命令或进行分布式节点间的通信（SSH 常用于分布式训练中节点握手和文件传输）。这增强了项目的**部署灵活性和易用性**，契合 VeOmni 作为**分布式训练框架**对容器化环境的支持需求。
- **暴露检查点早停设置**：允许用户在训练配置中自定义早停条件（如验证损失不再下降时提前停止并保存检查点）。VeOmni 的核心是通过“食谱库”提供可组合、可配置的训练方案，该提交**提升了食谱的可定制性**，使用户能更精细地控制训练流程，避免资源浪费，符合“扩展任意模态模型训练”的目标。

### 3. 对项目的影响与潜在意义
- **提升实用性与鲁棒性**：SSH 安装降低了用户通过容器进行开发/调试的门槛；早停功能则针对大规模训练场景（尤其是多模态大模型），显著节省算力和时间。
- **完善“食谱”生态**：早停作为训练策略中的关键组件，其配置暴露使 VeOmni 的 recipe zoo 更贴近实际生产需求，用户可轻松复用并调整早停规则。
- **文档同步更新**：保持了项目文档与实际功能的同步，提高用户上手体验。

### 4. 值得关注的技术点
- Docker 镜像中集成 SSH 服务器时，需注意安全实践（如密钥认证、端口映射、避免暴露默认密码）。
- 检查点早停的实现可能依赖于分布式训练框架的内部状态（如全局步数、梯度聚合后的验证指标）；暴露的配置项可能包括 `early_stop_patience`、`save_best_only` 等参数，需关注其与现有检查点保存逻辑的交互。

### 5. 对项目发展的影响（结合 README 背景）
- VeOmni 强调“以模型为中心的分布式食谱集”，致力于让任意模态训练更易扩展。早停功能的配置暴露，允许用户根据具体模型和数据动态调整训练终止策略，**增强了食谱的适应性和自动化程度**。
- SSH 支持优化了容器使用体验，推动项目向更成熟的**开箱即用**平台演进，吸引更多开发者进行二次开发或贡献食谱。
- 两个更新虽小，但分别作用于**底层基础设施**和**训练流程控制**，体现了项目在“易用性”和“可配置性”上的持续打磨，有助于降低多模态大模型训练的技术门槛。

## 详细提交记录

### [110900b](https://github.com/ByteDance-Seed/VeOmni/commit/110900b3d44dc3b4ebbda995e397b051205907a7)

- **作者**: Bin Jia
- **时间**: 2026-07-17T10:28:08Z
- **提交信息**: [docker] chore: install openssh server in CUDA 13 image (#937)

### [e2c9742](https://github.com/ByteDance-Seed/VeOmni/commit/e2c97423f4cb0cccbc823b0952738d22f97baed8)

- **作者**: 鐘天楽
- **时间**: 2026-07-17T07:56:52Z
- **提交信息**: [config, dist, trainer, docs] feat: expose checkpoint early-stop setting (#926)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-07-18
**监控日期**: 2026-07-17
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2505
- **最后更新**: 2026-07-17T18:27:46Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 4
- **主要提交者**: Bilang ZHANG, helloyongyang, Zicheng Weng

## AI分析总结

根据您提供的仓库背景（LightX2V 是一个轻量视频生成推理框架）以及昨日提交记录，以下是分析总结：

---

### 1. 主要更新类型
- **功能新增**：添加 SwanLab 训练监控支持
- **性能优化**：优化 Wan VAE 编码器的分布式推理、FLF2V 预热机制
- **功能更新**：FLF2V 版本更新、后处理流程更新

### 2. 关键变更点及其与项目方向的关系
| 提交 | 变更内容 | 与项目目标（轻量视频生成推理）的关系 |
|------|----------|--------------------------------------|
| `33e3f0a` | 新增 SwanLab 训练监控（通过 yaml 配置激活） | 提升训练可观测性，便于用户调试和实验跟踪，符合“易用性”方向 |
| `d44cd84` | 优化 Wan VAE 编码器分布式推理 | 核心推理性能改进，直接提升视频生成速度与资源效率，符合“轻量高效”目标 |
| `9056086` | FLF2V 预热机制与版本更新 | 预热可减少推理冷启动延迟，更新可能带来模型效果或兼容性提升，对长期稳定部署有价值 |
| `fea7781` | 更新后处理流程 | 视频生成后处理的优化或 bug 修复，直接影响输出质量与流程完整性 |

### 3. 对项目的影响与潜在意义
- **监控与可调试性**：SwanLab 集成降低了训练监控门槛，特别对研究者和开发者友好，有助于快速定位训练问题。
- **推理效率**：分布式 VAE 编码器优化和 FLF2V 预热机制，可显著缩短端到端推理时间，尤其是在多卡或批处理场景下。
- **质量与稳定性**：后处理更新可能修复已知输出瑕疵，FLF2V 更新增加模型鲁棒性，为用户提供更可靠的视频生成体验。

### 4. 值得关注的技术点
- **SwanLab 集成方式**：通过 yaml 中 `swanlab` 键配置，支持 `api_key`，保持与现有 LightX2V 配置风格一致，且 `rank_zero_only` 多卡兼容。
- **分布式 VAE 编码器优化**：具体优化细节可能在代码中涉及通信或计算图改进，值得深入查看。
- **FLF2V 预热**：实现方式（如预设张量或逐步激活）可能对显存占用和首帧延迟有影响。

### 5. 结合项目背景，这些提交如何影响项目发展
- **强化实用工具链**：添加 SwanLab 监控、优化后处理，使 LightX2V 从“纯推理框架”向“训练+推理完整方案”演进，吸引更多用户。
- **性能竞争力提升**：分布式编码器优化和预热机制是视频生成框架的关键痛点解决，可与其他轻量框架（如 DiffSynth-Engine）形成差异化。
- **社区友好性与开放性**：积极接受外部贡献（提交中包含合作者），说明项目维护活跃，有助于吸引更多开发者共建。

## 详细提交记录

### [33e3f0a](https://github.com/ModelTC/LightX2V/commit/33e3f0ab8e4418c028d8cc30c69164affc79591c)

- **作者**: Zicheng Weng
- **时间**: 2026-07-17T18:27:42Z
- **提交信息**: Add SwanLab training monitor (#1256)

add swanlab key in yaml to activate monitor

```
logging:
    rank_zero_only: true
    train_log_every_iters: 10
    infer_log_every_steps: 10
    swanlab:
        enable: true
        project: xxx
        name: xxx
        api_key: your_api_key
```

<img width="1723" height="683" alt="image"
src="https://github.com/user-attachments/assets/afe8911b-967b-491a-ac8a-83fcbb35c688"
/>

---------

Co-authored-by: wengzicheng03 <wengzicheng03@kuaishou.com>
Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>

### [d44cd84](https://github.com/ModelTC/LightX2V/commit/d44cd848fe966a08f5ad6fda9ceee60757ef0a8f)

- **作者**: helloyongyang
- **时间**: 2026-07-17T18:15:17Z
- **提交信息**: optimize wan vae encoder dist infer

### [9056086](https://github.com/ModelTC/LightX2V/commit/90560863ed0ea7848b9068573097904b08738439)

- **作者**: Bilang ZHANG
- **时间**: 2026-07-17T10:10:38Z
- **提交信息**: flf2v warmup and update (#1264)

### [fea7781](https://github.com/ModelTC/LightX2V/commit/fea7781538c3ad5a43ed693e0fd4992a7149280f)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-07-17T09:03:07Z
- **提交信息**: update post process (#1263)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-07-18
**监控日期**: 2026-07-17
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2174
- **最后更新**: 2026-07-17T11:00:40Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-07-18
**监控日期**: 2026-07-17
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5974
- **最后更新**: 2026-07-17T23:07:45Z

## 提交统计

- **昨日提交总数**: 7
- **提交者数量**: 7
- **主要提交者**: Julien Debache, Samuel Nordmann, ameynaik-hub

## AI分析总结

以下是基于`flashinfer-ai/flashinfer`仓库昨日提交记录

## 详细提交记录

### [91054b9](https://github.com/flashinfer-ai/flashinfer/commit/91054b9e4b38f057fded08eee84b7a7fe68d5a7c)

- **作者**: yichengj
- **时间**: 2026-07-17T23:07:41Z
- **提交信息**: perf(jit): drop dead SM12x gencode from SM10x-serving modules (#3947)

## 📌 Description

Resolves cross-cutting item 10 of the SM121 support audit (#3170):
several SM10x-serving
JIT module generators include major version 12 in
`supported_major_versions`, so wheel
builds whose arch list contains a 12.x entry compile their kernels for
SM12x too. That
SM12x machine code can never run: on a compute capability 12.x device,
dispatch always
selects the dedicated sm120 module (cutlass fused-moe, groupwise gemm,
cutlass
fp4/fp8/bf16 gemm) or the sm100 variant (mamba
`selective_state_update`), and on SM10x
devices the CUDA loader picks the matching sm_100a/sm_103a code from the
fatbin.

Measured in the published v0.6.9 cu130 aarch64 jit-cache wheel
(per-module
readelf/cuobjdump accounting), this dead code is **1,046 MB installed,
52% of all SM12x
bytes** in the wheel:

| module | dead SM12x bytes |
|---|---|
| `fused_moe_103` | 430 MB |
| `fused_moe_100` | 409 MB |
| `gemm_sm100` | 48 MB |
| `fp8_gemm_cutlass` | 8 MB |
| `fp4_gemm_cutlass` | 5 MB |
| `selective_state_update` base/sm90 variants (100 modules) | ~147 MB |

Fixes:

- Remove `12` from `supported_major_versions` at the nine dead sites:
`gen_cutlass_fused_moe_sm100_module`,
`gen_cutlass_fused_moe_sm103_module`
  (`flashinfer/jit/fused_moe.py`); `gen_gemm_sm100_module`,
`gen_gemm_sm100_module_cutlass_fp4`,
`gen_gemm_sm103_module_cutlass_fp4`,
`gen_gemm_sm100_module_cutlass_fp8`,
`gen_gemm_sm100_module_cutlass_bf16`
  (`flashinfer/jit/gemm/core.py`); `gen_selective_state_update_module`,
`gen_selective_state_update_sm90_module`
(`flashinfer/jit/mamba/selective_state_update.py`).

This matters for the release pipeline right now: the cu130 wheels sit
just under GitHub's
2 GiB release-asset cap (aarch64 at 2.117 GB, x86_64 at 2.133 GB, cap
2.147 GB), so any
module growth breaks the next upload. This change shrinks the aarch64
wheel to roughly
1.88 GB zipped (x86_64 similar).

## 🔍 Related Issues

#3170 (cross-cutting item 10).

## 🧪 Tests

- A dispatch audit shows that CC 12.x never reaches the nine changed
generator sites.
- The change was verified at runtime on both SM121 (DGX Spark, GB10) and
SM120
  (RTX 5080). Starting from an empty JIT cache, the test
suites for all six affected op families (mamba selective state update,
bmm_fp8,
mm_fp4, mm_bf16, groupwise-scaled fp8 GEMM, and cutlass fused MoE) pass
on both
machines, and the cache afterwards contains none of the nine modules
this PR edits.
  This confirms that SM12x dispatch never loads them.
- `pre-commit run` on the changed files is clean.

## Reviewer Notes

- The dead verdicts depend on today's dispatch gates
(`get_cutlass_fused_moe_module`'s
backend strings, `is_sm12x_supported` branches preceding
`is_sm100a_supported`, the
bmm_fp8 heuristic preferring `cutlass_sm12x`, and the mamba
`_get_module` ordering).
If a future change routes SM12x to one of these modules, its generator
needs 12 back.
- The mamba base/sm90 variants also embed SM9x/SM10x code that the same
dispatch logic
never loads (base only serves SM8x, sm90 only SM9x). Not touched here to
keep this PR
  scoped to the SM12x audit; a follow-up could prune those the same way.
- No runtime behavior changes on any device: no dispatch path is
modified, only the set
  of arch targets each module is compiled for.

🤖 Generated with [Claude Code](https://claude.com/claude-code)











<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved CUDA architecture compatibility for fused MoE, GEMM, and
selective state update operations.
* Prevented unsupported CUDA 12 compilation targets for selected GPU
kernels, while preserving CUDA 12 support where applicable.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [97f3b03](https://github.com/flashinfer-ai/flashinfer/commit/97f3b035a1f2bfaa94b5f636b169d8fd35bcf2b7)

- **作者**: Samuel Nordmann
- **时间**: 2026-07-17T22:43:03Z
- **提交信息**: perf(moe): optimize one-sided EP4 NVFP4 dispatch (#3846)

## Summary

Optimize one-sided MoE dispatch by:

- constructing routing metadata cooperatively across a warp instead of
using a
  serial thread-0 loop;
- retaining one compact destination per rank when `ep_size == 4` and
  `top_k > 4`;
- using a 128-thread CTA for that compact path when every payload is at
most
  1,024 bytes per token.

The compact path reduces destination state from `top_k` entries to at
most
four and no longer depends on an exact model payload fingerprint. Other
EP
sizes and `top_k <= 4` retain the generic path. There is no API change.

The 128-thread choice was measured against 64 and 256 threads on two
GB200
nodes. Compared with 64 threads, 128 was effectively neutral at 4-64
tokens/rank, 0.9-2.9% faster at 512 tokens/rank, and 2.5-10.0% faster at
8,192
tokens/rank.

## Performance

GB200, EP4, top-k22, H2048 NVFP4, CUDA graphs. Values average the
medians from two independent opposite-order runs.

| Tokens/rank | Dispatch baseline → candidate | Reduction | Dispatch +
combine baseline → candidate | Reduction |
|---:|---:|---:|---:|---:|
| 4 | 19.68 → 13.79 us | 29.9% | 31.78 → 25.83 us | 18.7% |
| 64 | 22.15 → 15.52 us | 29.9% | 35.59 → 28.95 us | 18.7% |
| 512 | 46.90 → 18.21 us | 61.2% | 67.77 → 38.71 us | 42.9% |
| 8192 | 456.43 → 53.04 us | 88.4% | 599.90 → 192.65 us | 67.9% |

End-to-end Nemotron Ultra NVFP4 was measured with vLLM on one GB200
node,
`TP=1`, `DP=4`, `EP=4`, concurrency 16, and `ISL/OSL=50000/2048`.
Four balanced ABBA/BAAB allocations covered 3,072 requests.

| Metric | Baseline | Candidate | Geometric-mean change |
|---|---:|---:|---:|
| Aggregate output throughput | 532.75 tok/s | 562.09 tok/s | +5.5% |
| Mean TPOT | 23.12 ms | 23.06 ms | -0.3% |
| Mean TTFT | 13.16 s | 10.96 s | -16.7% |

## Validation

- all supported top-k values: 200 generic-path changing-payload graph
replays each;
- exact packed-NVFP4 target: 1,000 replays in vLLM payload order and 200
in
  the alternate FlashInfer order;
- nonmatching top-k22 payload: 200 replays through the generic fallback;
- four-rank GB200 CUDA-graph validation for compact EP4 `top_k` 6, 8,
10,
16, and 22 with packed H2048 payloads, plus a wide-BF16 case that
retains
  the configured CTA size (Lyris job `2301707`, commit `8a5a6f93`);
- local and GitHub `pre-commit`.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

## Summary by CodeRabbit

* **New Features**
* Added a compact EP4 dispatch mode for MOE AlltoAll routing, improving
how repeated destinations are handled.
* Updated dispatch launch behavior to better match the payload size and
expert routing layout.

* **Tests**
* Added a new test covering compact EP4 dispatch to validate token
routing and dispatched outputs across ranks.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [17bd9be](https://github.com/flashinfer-ai/flashinfer/commit/17bd9be0de3c2360a596043e50c7b12893da7257)

- **作者**: sychen52
- **时间**: 2026-07-17T21:26:39Z
- **提交信息**: fix(benchmark): don't fail non-trtllm mm_fp4 backends on unaligned n (#4033)

<!-- .github/pull_request_template.md -->

## 📌 Description

- nvfp4_quantize(do_shuffle=True) requires n % 128 == 0, but its output
is only consumed by the trtllm backend
- prepare the shuffled weight/scale tensors only when trtllm is
requested
- on shuffle failure, drop only the trtllm backend with the standard
unsupported-configuration message instead of failing the whole test case
- return the result list instead of None when no backend passes
validation, so the harness reports the skip instead of "'NoneType' is
not iterable"


## 🔍 Related Issues

<!-- Link any related issues here -->

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

- [ ] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved FP4 benchmark handling when the optional TensorRT-LLM backend
is unavailable or fails validation.
  * Avoided unnecessary FP4 weight preparation for unselected backends.
* Ensured benchmark routines consistently return empty results when no
valid backends remain.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: Shiyang Chen <shiychen@nvidia.com>

### [37ce036](https://github.com/flashinfer-ai/flashinfer/commit/37ce0366fd324c6b026f190aba7123be8ca3eb95)

- **作者**: ameynaik-hub
- **时间**: 2026-07-17T20:52:31Z
- **提交信息**: Ameyn/gdn wy perf followup (#3908)

## 📌 Stacked on #3720

This branch builds on #3720's head (`00a655e`); the diff will show its
commits until it merges. **Review only the 5 commits listed below.**
Once #3720 lands, the diff collapses to just these changes (one rebase
needed only if #3720 is squash-merged).

## What

Performance and correctness follow-ups to the WY output-only GDN decode
kernel, driven by Nsight Compute analysis on B200. Two files:
`flashinfer/gdn_kernels/gdn_decode_bf16_wy_output_only.py`,
`benchmarks/bench_gdn_decode.py`.

### Performance
- **`49a7ccf` Raise launch-bounds cap 4→8.** With `min_blocks_per_mp`
capped at 4, the compiler used 73 regs/thread, limiting occupancy to 6
CTAs/SM (37.5%). Requesting 8 fits 64 regs/thread with no spills → 7
CTAs/SM (43.75%). Adds `GDN_WY_MBP` env override for tuning experiments.
- **`39693d1` SMEM-staged coalesced output epilogue.** The
MMA-fragment-direct 4-byte stores wasted half of every 32-byte sector
(NCU: 23% of all L2 sector traffic). The output tile now stages through
`sH`'s SMEM (dead at that point — zero extra usage) and flushes with
consecutive-lane 16-byte stores at 100% sector utilization. Excessive
sectors: 23% → 5%.
- **`6d34642` Enable native-short-T + native-a/b by default for
T∈{4,8}.** The kernel reads the real `[B,T,…]` tensors (loads only the T
valid rows), removing 4 of 5 host staging copies per call. Previously
gated off due to an accuracy signal that traced to the bf16-cache bug
fixed in `856f21f`, not this path. `SGLANG_GDN_WY_NATIVE_T=0` /
`SGLANG_GDN_WY_NATIVE_AB=0` restore staging.

### Benchmarking
- **`45e6956` Time the wy_output_only head-to-head with CUPTI + cold
L2** — the same `bench_gpu_time(enable_cupti=True, cold_l2_cache=True)`
methodology as every other version in the file

## Benchmark results

```bash
python benchmarks/bench_gdn_decode.py --version bf16_wy_output_only \
  --num-q-heads 16 --num-k-heads 16 --num-v-heads 64 --head-size 128 \
  --seq-len 4 8 16 --batch-size 1 2 4 8 16 32 64 128 256 \
  --warmup 10 --iters 1000
```

B200 (SM100) · CUPTI per-kernel GPU time · L2 flushed before every
iteration · median of 1000 iters · bf16, HV=64, H=HK=16, head 128. "old"
= PR #3720 head (`00a655e`), "new" = this PR, measured identically; the
`bf16_state` reference-kernel column reproduced to <0.1% between the two
runs (measurement control).

**WY output-only kernel time, old → new µs (Δ):**

| B | T=4 | T=8 | T=16 |
|---:|---:|---:|---:|
| 1 | 5.28 → 5.12 (−3.0%) | 5.18 → 5.02 (−3.1%) | 5.60 → 5.44 (−2.9%) |
| 2 | 5.92 → 5.73 (−3.2%) | 5.79 → 5.60 (−3.3%) | 6.18 → 6.14 (−0.6%) |
| 4 | 6.98 → 6.43 (−7.9%) | 7.01 → 6.62 (−5.6%) | 7.55 → 7.42 (−1.7%) |
| 8 | 8.35 → 7.87 (−5.7%) | 8.26 → 7.97 (−3.5%) | 9.18 → 8.96 (−2.4%) |
| 16 | 12.77 → 10.53 (**−17.5%**) | 12.77 → 11.33 (−11.3%) | 14.08 →
12.96 (−8.0%) |
| 32 | 21.31 → 19.07 (−10.5%) | 21.25 → 20.29 (−4.5%) | 23.62 → 22.85
(−3.3%) |
| 64 | 37.76 → 35.20 (−6.8%) | 37.73 → 35.68 (−5.4%) | 41.95 → 40.18
(−4.2%) |
| 128 | 65.97 → 61.57 (−6.7%) | 66.88 → 62.78 (−6.1%) | 76.13 → 70.47
(−7.4%) |
| 256 | 121.76 → 112.99 (−7.2%) | 123.74 → 114.66 (−7.3%) | 143.81 →
130.72 (**−9.1%**) |



## Checklist

- [x] pre-commit installed, hooks installed, `pre-commit run
--all-files` passes (incl. mypy, ruff)
- [x] Tests pass on SM100
- [x] AI-assisted (Claude Code): NCU analysis, implementation, and
validation


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Performance**
* Improved BF16 decode output handling with more efficient data
movement, potentially reducing overhead for supported workloads.
* Tuned execution behavior for better performance across varying tensor
and layout configurations.

* **Reliability**
* Improved compatibility when runtime dimensions and layouts differ by
preventing inappropriate cached kernel reuse.
  * Updated default execution settings for native decoding paths.

* **Benchmarks**
* Refined kernel timing methodology for more consistent performance
measurements.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>

### [42f2a79](https://github.com/flashinfer-ai/flashinfer/commit/42f2a79bf766afaf01b4830e5629e524e084bccb)

- **作者**: nvamyt
- **时间**: 2026-07-17T18:35:42Z
- **提交信息**: test(comm): add additional comm tests to multi-node CI (#3968)

The checkpoint test was added by PR #3950 but never wired into any CI
test script. Add it to task_test_multi_node_comm_kernels.sh so it runs
on GB300/GB200 multi-node jobs.

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->
Add test_trtllm_allreduce_checkpoint.py to
task_test_multi_node_comm_kernels.sh
## 🔍 Related Issues

<!-- Link any related issues here -->
https://github.com/flashinfer-ai/flashinfer/issues/3966
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

* **Tests**
* Expanded multi-node communication kernel test coverage to include
additional all-reduce and all-to-all scenarios.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Sonnet 4.6 <noreply@anthropic.com>

### [825cae8](https://github.com/flashinfer-ai/flashinfer/commit/825cae8ae8a2d9e31c89fa10326381c93de91f15)

- **作者**: Julien Debache
- **时间**: 2026-07-17T17:58:13Z
- **提交信息**: Autotuner mem leak follow up 2 (#3970)

### [17228c6](https://github.com/flashinfer-ai/flashinfer/commit/17228c6f9eae0c5bb9498d8ee600a7f3face114e)

- **作者**: Blake Ledden
- **时间**: 2026-07-17T10:36:40Z
- **提交信息**: feat: enable fmha_v2 HMMA attention for SM120 standard shapes (#3016)

## Summary

Enables the existing TRT-LLM fmha_v2 HMMA flash attention kernels for
SM120 (RTX 5090, DGX Spark) with standard head dimensions (64/128/256).
These kernels use Ampere-compatible HMMA tensor core instructions
(`sm_mma=80`) which SM120 supports natively.

The fmha_v2 SM120 kernel infrastructure already existed for DeepSeek MLA
shapes (192x128) but standard attention kernels (bf16/fp16) were not
enumerated in the JIT generation path. This PR adds them and wires
fmha_v2 into `BatchPrefillWithRaggedKVCacheWrapper` as an automatic
backend for SM12x MHA at sequence lengths >= 256.

## Changes

- `flashinfer/jit/attention/fmha_v2/generate_kernels.py`: Add
`enumerate_hmma_flash_kernels(specs, sm=120, dtype="bf16")` and `fp16`
for standard shapes
- `flashinfer/utils.py`: Add `_should_use_fmha_v2_sm120()` helper
- `flashinfer/prefill.py`: Wire fmha_v2 into BatchPrefill plan/run with
conditional selection

## Backend selection logic

```
SM12x + MHA + seqlen >= 256 + bf16/fp16 + no custom mask → fmha_v2
SM12x + GQA or seqlen < 256 → fa2 (fallback)
```

## SM121a (DGX Spark) validation

**Correctness** (14/14 configs, all vs f32 reference):

| Config | Error |
|--------|-------|
| B=1 S=64 H=4 D=64 bf16 causal | 0.007 |
| B=2 S=128 H=4 D=64 bf16 causal | 0.007 |
| B=1 S=64 H=8 D=128 bf16 causal | 0.008 |
| B=1 S=256 H=4 D=128 bf16 noncausal | 0.001 |
| B=1 S=128 H=4 D=128 fp16 causal | 0.003 |

**Performance** (CUDA event timing, bf16 causal):

| Config | fmha_v2 | FA2 | ratio |
|--------|---------|-----|-------|
| B=2 S=512 H=4 D=64 | 0.050ms | 0.073ms | **0.69x** |
| B=2 S=512 H=4 D=128 | 0.037ms | 0.041ms | **0.91x** |
| B=1 S=1024 H=4 D=128 | 0.047ms | 0.053ms | **0.88x** |
| B=1 S=128 H=4 D=64 | 0.020ms | 0.010ms | 2.07x (FA2 wins, below
threshold) |

fmha_v2 is 10-31% faster than FA2 at S>=512, but slower at small
sequences due to CTA launch overhead. The S>=256 threshold avoids the
regression region.

## Related

- Addresses Issue #2555 (Issue 1: SM120 kernel generation, Issue 2:
backend routing)
- Complements PR #2598 (CuTe DSL backend — different kernel system,
independent)

Contributed by Second Nature Computing (https://joinsecondnature.com)

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Expanded SM120 GPU support with optimized flash-attention kernels for
bfloat16 and float16.
* Automatic selection of the optimized prefill backend for compatible
SM120 workloads (>=256 sequence length and matching Q/KV layout).
* New prefill execution path that uses packed Q/KV inputs and cached
sequence/index buffers for faster runs.
* Note: the optimized prefill path does not support returning LSEs
(NotImplemented).
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Blake Ledden <blake@secondnaturecomputing.com>
Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-07-18
**监控日期**: 2026-07-17
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3848
- **最后更新**: 2026-07-17T13:56:52Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: William Lin

## AI分析总结

### 昨日更新要点分析

**提交记录：**  
- `32cd603` Revert docs trusted-branch-only workflow (#1618)  

#### 1. 主要更新类型
- **配置回滚 / 工作流维护**（属于基础设施调整）

#### 2. 关键变更点及与项目方向的关系
- **变更内容**：撤销了之前对文档构建工作流设置的“仅信任特定分支”（trusted-branch-only）限制。  
- **项目方向关联**：FastVideo 项目强调文档的重要性（README 中提供完整文档入口和快速开始指南），本次回滚意味着文档的自动构建与部署不再局限于受保护分支，而是放开到更多分支或 PR 中。这有助于降低社区贡献的门槛，使文档更新更加敏捷，符合项目对外开放协作、快速迭代的整体方向。

#### 3. 对项目的影响和潜在意义
- **影响**：恢复为更宽松的文档工作流配置，任何分支或合并请求的文档变更都可能触发自动构建与发布（需确认具体配置）。  
- **潜在意义**：  
  - 提升贡献者体验：无需等待合并到特定分支即可预览文档效果，减少等待时间。  
  - 降低维护成本：避免因分支策略过严导致文档更新滞后或遗漏。  
  - 促进社区参与：鼓励更多用户通过文档 PR 提出改进建议，加速项目生态建设。

#### 4. 值得关注的技术点
- **CI/CD 工作流中的分支过滤机制**：`trusted-branch-only` 通常指仅在 `main` 或 `master` 等核心分支上运行工作流。回滚此配置可能改用 `push`、`pull_request` 等更通用的触发器，或取消 `if` 条件判断。  
- **文档部署的安全性权衡**：放开分支限制可能带来误部署或安全风险，但本次回滚表明项目方更倾向于便利性而非严格控制，未来可能通过其他机制（如手动批准）来保障质量。

#### 5. 基于项目背景的发展影响
- FastVideo 作为一个开源视频处理/生成工具，其文档是用户理解和使用的关键入口。本次提交表明项目团队在优化开发流程，追求**更开放的协作模式**。  
- 回滚操作本身也是快速响应社区反馈或内部测试的结果，体现了项目维护的灵活性与务实态度。长远看，这有助于加快文档更新速度，与项目强调的“快速”（FastVideo 名称）理念相呼应。

## 详细提交记录

### [32cd603](https://github.com/hao-ai-lab/FastVideo/commit/32cd6035156405d6a61e398d35bd90347de3ba8a)

- **作者**: William Lin
- **时间**: 2026-07-17T07:22:56Z
- **提交信息**: Revert docs trusted-branch-only workflow (#1618)

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-07-18
**监控日期**: 2026-07-17
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34078
- **最后更新**: 2026-07-17T23:18:43Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 4
- **主要提交者**: Sayak Paul, yzhautouskay, David El Malih

## AI分析总结

根据提供的 `huggingface/diffusers` 仓库提交记录和 README 上下文，以下是昨日更新的要点总结：

---

### 1. 主要更新类型
- **文档更新**：`agents doc` 指导、`scheduling_k_dpm_2_discrete.py` 注释改进
- **功能新增**：Cosmos3 蒸馏支持（专用 modular pipeline + blocks）
- **测试重构**：大规模 Pipeline 测试重写（使用 mixin、清理废弃属性）
- **Bug 修复**：ModelOpt 预量化加载修复
- **测试增强**：`not_params` 机制加入 `ModularPipelineTesterMixin`

---

### 2. 关键变更点及与项目方向的关系
- **文档指导 checkpoint 变体设计**（#14208）：阐明何时应创建新的 blockset（而非用 `ConfigSpec` 加 if 分支），强化了项目的 modular 架构原则 —— 不同 checkpoint 变体（如蒸馏版）应作为独立的 pipeline 组装，而非通过配置标志污染标准 pipeline。这与 README 中 “modular pipelines” 的设计理念完全一致。
- **测试框架增强**（#14207）：`not_params` 使测试能够断言某个规范参数（如 `negative_prompt`）**必须缺失**，直接支持了蒸馏类模型输入接口的差异化验证。体现了项目对 pipeline 输入契约精确性的追求。
- **Cosmos3 蒸馏支持**（#14177）：新增独立 modular pipeline，展示了如何遵循上一提交的文档原则（检查点变体作为独立的 blockset），同时使用 `ModularPipelineTesterMixin` 进行测试，形成完整的实践闭环。
- **测试基础设施重构**（#14113）：全面优化测试结构（mixin、缓存、量化级别测试），降低维护成本，为后续新 pipeline 的快速集成提供稳定底座。
- **量化加载修复**（#14188）：修复 ModelOpt 预量化模型加载，保证 NVIDIA 优化路径的可用性，属于实用 bugfix。

---

### 3. 对项目的影响和潜在意义
- **提升设计一致性**：通过文档 + 测试工具（`not_params`）双重约束，避免开发者将标准 pipeline 的“配置标志思维”带入 modular 架构，减少技术债务。
- **加速新模型支持**：Cosmos3 蒸馏的完整实现 + 测试框架重构，降低了后续添加新变体的门槛。
- **提高可靠性**：预量化加载修复 + 更严格的签名测试，减少生产环境中的意外行为。
- **强化社区贡献指南**：`agents doc` 中明确的 blockset 决策树和反模式说明，降低了贡献者的认知负荷。

---

### 4. 值得关注的技术点
- **blockset vs ConfigSpec 决策原则**：
  - 输入、组件、块结构改变 → 新建 blockset
  - 仅值改变 → 可用 ConfigSpec
  - 用 `flux2-klein` 作为参考案例
- **`not_params` 测试机制**：允许 pipeline 声明其故意省略的规范参数，测试自动验证这些参数不在 `__call__` 中暴露，是 modular 管线的契约测试利器。
- **蒸馏模型输入差异处理**：例如 guidance-distilled 管道无 `negative_prompt`，需通过不同 blockset 自然实现，而非运行时条件判断。

---

### 5. 对项目发展的影响（结合 README 背景）
- **巩固 modular 方法论**：项目目标之一是实现灵活、可组合的 pipeline。本次更新直接解决了“标准 pipeline 移植到 modular 时易犯的错误”，使得 modular 架构的推广更有底气。
- **扩展模型支持面**：Cosmos3 蒸馏是

## 详细提交记录

### [5abc8c6](https://github.com/huggingface/diffusers/commit/5abc8c6773dedd360dc85e83ed4042c7feb3f1ef)

- **作者**: YiYi Xu
- **时间**: 2026-07-17T22:34:32Z
- **提交信息**: [agents doc] notes on when to create new blocksets for checkpoint variant (#14208)

* modular.md: document checkpoint variants as separate blocks assemblies

Contributors keep handling checkpoint variants (distilled/turbo) with a
ConfigSpec flag and an if-branch inside a shared block — the standard-pipeline
mindset ported into modular. The doc never said what to do instead: nothing
routed on 'behavior differs per checkpoint', and flux2-klein was only cited
as a flatness example, not as the variant pattern it embodies.

Adds:
- a per-checkpoint branch in the block types decision tree
- 'Key pattern: Checkpoint variants' — separate assembly when the variant
  changes the contract (inputs/components/blocks), ConfigSpec only when it
  changes a value; flux2-klein as reference; the config-flag anti-pattern
- gotcha #9 for the if-components.config.<variant_flag> smell

Co-Authored-By: Claude Fable 5 <noreply@anthropic.com>

* Clarify when the map fn resolves the variant (standard model_index repos)

Co-Authored-By: Claude Fable 5 <noreply@anthropic.com>

* Sharpen variant rule: inputs are the hard line (repo can override components/config, never inputs)

Co-Authored-By: Claude Fable 5 <noreply@anthropic.com>

* Reframe checkpoint variants around the advantage, not the prohibition

The config-flag branch is what standard pipelines are forced into; modular's
pitch is that the loaded pipeline describes exactly its checkpoint. Lead with
the payoff (clean per-variant contract, automatic routing, input-surface
expressiveness) and present the flag branch as tolerable-but-lossy rather
than forbidden.

Co-Authored-By: Claude Fable 5 <noreply@anthropic.com>

* Simplify checkpoint-variants section: different checkpoint -> own blockset unless literally the same

Co-Authored-By: Claude Fable 5 <noreply@anthropic.com>

* Add growth rule: one workflow at a time, new blocks over edits, generalize only by removing branches/duplicates

Co-Authored-By: Claude Fable 5 <noreply@anthropic.com>

* Address review: standardize on 'blockset', reword decision tree, link flux2 growth example

Co-Authored-By: Claude Fable 5 <noreply@anthropic.com>

---------

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [f6a3517](https://github.com/huggingface/diffusers/commit/f6a3517673e32b4134cd4eb62bd13a20934385eb)

- **作者**: YiYi Xu
- **时间**: 2026-07-17T18:40:00Z
- **提交信息**: Add not_params to ModularPipelineTesterMixin (#14207)

Pipelines sometimes deliberately drop a canonical param — e.g. guidance-distilled
pipelines don't accept negative_prompt. Test classes can now declare these in
not_params and test_pipeline_call_signature asserts they are absent from the
pipeline's inputs, so reintroducing one by accident fails the test.

Adopted in the flux2-klein test classes (negative_prompt).

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [8eac6ad](https://github.com/huggingface/diffusers/commit/8eac6ad1c402ecdc268e47d379eb84fec6d69710)

- **作者**: yzhautouskay
- **时间**: 2026-07-17T18:35:41Z
- **提交信息**: Cosmos3 Distilled support (#14177)

* Cosmos3 distilled support (dedicated modular pipeline + blocks)

* Address review comments

* Refactor unit test to use ModularPipelineTesterMixin

* Docs fix

* Tests refactor

* Pass generator to SDE scheduler  for reproducibility

* Apply suggestion from @yiyixuxu

* Distilled text encoder step bugfix

---------

Co-authored-by: YiYi Xu <yixu310@gmail.com>

### [2f2a74f](https://github.com/huggingface/diffusers/commit/2f2a74fef07c8f2c618d897589506e946762d92f)

- **作者**: David El Malih
- **时间**: 2026-07-17T17:23:53Z
- **提交信息**: docs: improve docstring scheduling_k_dpm_2_discrete.py (#14212)

Improve docstring scheduling k dpm 2 discrete

### [cff933c](https://github.com/huggingface/diffusers/commit/cff933cc6d1529e79886598faccf42fce916150d)

- **作者**: Sayak Paul
- **时间**: 2026-07-17T15:15:15Z
- **提交信息**: [tests] Pipeline test refactor (#14113)

* up

* up

* quantization level refactors.

* style

* up

* up

* use mixins and remove stale attributes

* fixture for the deprecated pipelines

* remove qkv

* remove lergacy for attention processor.

* use pytorch tensors exclusively.

* rejig dodgy test.

* improve how base pipeline output fixture is used.

* rename params.

* up

* use pipeline load api for ip adapter.

* move to flux specific.

* redesign config for caching

* remove eval.

* up

* up

* add a todo note on check_qkv_fusion_matches_attn_procs_length

* nan test in layerwise casting

* proper skipping

* skip properly.

* up

* up

### [48fadcc](https://github.com/huggingface/diffusers/commit/48fadcc9460efa0e51886ae3b382b8cdd590379a)

- **作者**: yzhautouskay
- **时间**: 2026-07-17T13:18:05Z
- **提交信息**: [Quantization] Fix ModelOpt pre-quantized loading  (#14188)

* Fix ModelOpt pre-quantized loading

* Add regression catching failure before the fix

---------

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-07-18
**监控日期**: 2026-07-17
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 424
- **最后更新**: 2026-07-10T06:55:40Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-07-18
**监控日期**: 2026-07-17
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12712
- **最后更新**: 2026-07-17T21:55:45Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-07-18
**监控日期**: 2026-07-17
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 30417
- **最后更新**: 2026-07-17T22:58:42Z

## 提交统计

- **昨日提交总数**: 24
- **提交者数量**: 19
- **主要提交者**: Bingxu Chen, fanxingran, Xiaoyu Zhang

## AI分析总结

分析生成失败

## 详细提交记录

### [0ad0ff2](https://github.com/sgl-project/sglang/commit/0ad0ff2e9ee4d52d699175b0a744543a1fed8a6a)

- **作者**: sglang-bot
- **时间**: 2026-07-17T22:58:36Z
- **提交信息**: chore: bump sglang-kernel version to 0.4.5 (#31618)

Co-authored-by: sglang-bot <sglang-bot@users.noreply.github.com>

### [e2d2e8d](https://github.com/sgl-project/sglang/commit/e2d2e8d07ebfa019af5834b81933bd31ef6f4c4f)

- **作者**: Qiaolin Yu
- **时间**: 2026-07-17T22:18:01Z
- **提交信息**: [spec decoding] fix multi_layer_eagle rotate_input_ids kernel registration (#31614)

### [ec6a316](https://github.com/sgl-project/sglang/commit/ec6a3163b7ac2f0071cc2e92988f92513a2f4757)

- **作者**: Sam (Kesen Li)
- **时间**: 2026-07-17T21:49:43Z
- **提交信息**: [Feature] Add FP4 KV Cache Design and support SM120 GPUs (#21601)

### [7fc3fb9](https://github.com/sgl-project/sglang/commit/7fc3fb9657a527d5523b86304350296cf486a557)

- **作者**: Brayden Zhong
- **时间**: 2026-07-17T21:34:29Z
- **提交信息**: Remove deprecated Mamba flags from doc, wrong FP8 GEMM docstrings and change Nemotron image to 0.5.15 (#31094)

Co-authored-by: Brayden Zhong <brayden@radixark.ai>

### [c00206c](https://github.com/sgl-project/sglang/commit/c00206c68c81551ce79c7c9b76c53f63a28b55ff)

- **作者**: sglang-bot
- **时间**: 2026-07-17T21:00:55Z
- **提交信息**: chore: bump sgl-kernel version to 0.4.5 (#31496)

### [ae3f626](https://github.com/sgl-project/sglang/commit/ae3f62613a257dc5eb7e83ba6d2468a8d2984c58)

- **作者**: Douglas Yang
- **时间**: 2026-07-17T20:24:46Z
- **提交信息**: docs(cookbook): fix stale/pruned Docker image tags (#31508)

Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [2c856ab](https://github.com/sgl-project/sglang/commit/2c856abbe3c0f3e2811bf9f7648c4bf6bec4f884)

- **作者**: Liangsheng Yin
- **时间**: 2026-07-17T20:19:03Z
- **提交信息**: [Fix] Enable chunked input-logprob processing by default to cap peak memory (#31498)

### [d389039](https://github.com/sgl-project/sglang/commit/d38903933744088895eef03170ecc76b11eff4b4)

- **作者**: Andy Ye
- **时间**: 2026-07-17T19:00:23Z
- **提交信息**: [diffusion] Opt in Qwen and Wan multi-output conditioning expansion (#31233)

### [fec6131](https://github.com/sgl-project/sglang/commit/fec613184480bd6fc5bfc9967bfb24a6125f684c)

- **作者**: fanxingran
- **时间**: 2026-07-17T17:22:14Z
- **提交信息**: [AMD] Disable DSA fused top-k v2 on ROCm for GLM-5.x / DeepSeek-V3.2 (#30506)

Co-authored-by: kk <43161300+kkHuang-amd@users.noreply.github.com>

### [2db21da](https://github.com/sgl-project/sglang/commit/2db21daf8dbe04d109d36423fe69819b2e14937f)

- **作者**: Muhammad Safiullah Memon
- **时间**: 2026-07-17T17:21:50Z
- **提交信息**: Fix Heartbeat Checker in KV Manager Disaggregation (#31584)

Co-authored-by: Muhammad Safiullah <muhammadsafiullah136@gmail.com>

### [2c64b77](https://github.com/sgl-project/sglang/commit/2c64b7782e0352fd5928060caafa51bda2e1dcf3)

- **作者**: Zhaoyi Li
- **时间**: 2026-07-17T17:08:04Z
- **提交信息**: [AMD][PD] Fix early-send cached-prefix KV racing the prefill forward on mori (#31368)

Co-authored-by: Michael <13900043+michaelzhang-ai@users.noreply.github.com>

### [53229e8](https://github.com/sgl-project/sglang/commit/53229e88da96edd5e3bd61e2067007ea0f29bf18)

- **作者**: Bingxu Chen
- **时间**: 2026-07-17T16:03:44Z
- **提交信息**: [AMD] Fix stale imports in test_fused_fp8_kv_write.py (#31515)

### [c546afc](https://github.com/sgl-project/sglang/commit/c546afc14712b686ba5c26db5afa8c5db778706f)

- **作者**: Michael
- **时间**: 2026-07-17T16:01:46Z
- **提交信息**: [AMD] Register 2 CPU/triton unit + kernel tests for AMD 1-GPU PR CI (#31379)

### [5e7eed4](https://github.com/sgl-project/sglang/commit/5e7eed4c008c73f2f02c6a0a06d63d6f249a78b3)

- **作者**: NOOB
- **时间**: 2026-07-17T15:24:00Z
- **提交信息**: [MLX] Honor --max-running-requests in the model runner stub (#30547)

Co-authored-by: R0CKSTAR <yeahdongcn@gmail.com>

### [85ac56c](https://github.com/sgl-project/sglang/commit/85ac56c82308b8f0e86b3aa8542b61af0de666aa)

- **作者**: Mick
- **时间**: 2026-07-17T11:39:38Z
- **提交信息**: docs: simplify diffusion new model guide (#30109)

### [681c223](https://github.com/sgl-project/sglang/commit/681c223570810bc9a6dd85b9cc12ea6a3ff689bc)

- **作者**: Mick
- **时间**: 2026-07-17T11:15:04Z
- **提交信息**: refactor: wrap split backends once on full-attention backends (#31439)

### [24a8944](https://github.com/sgl-project/sglang/commit/24a8944e151f04093cd48f7e9dce77fb5f03b209)

- **作者**: Mick
- **时间**: 2026-07-17T11:13:54Z
- **提交信息**: fix: enable Kimi multimodal breakable prefill cuda graph replay (#31391)

### [132ade5](https://github.com/sgl-project/sglang/commit/132ade55cd65c3679a60adec563c8e6ca81238c5)

- **作者**: DarkSharpness
- **时间**: 2026-07-17T10:37:22Z
- **提交信息**: [Kernel] Rewrite JIT custom all-reduce (v2) with a decoupled kernel/storage design (#31049)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: root <root@GPUC5A6.maas>

### [eaeb779](https://github.com/sgl-project/sglang/commit/eaeb779ea4b1011a14a55fe0cdb6a96bb3520466)

- **作者**: Baizhou Zhang
- **时间**: 2026-07-17T09:25:50Z
- **提交信息**: [Doc] Update GLM5.2 Cookbook with LayerSplit usage (#31577)

### [19f4859](https://github.com/sgl-project/sglang/commit/19f4859b30843f2df3a9c0db1859f10591c2a8ec)

- **作者**: Liangsheng Yin
- **时间**: 2026-07-17T09:11:41Z
- **提交信息**: [CI] Exclude current process memory from GPU idle check (#31571)

### [8f765bc](https://github.com/sgl-project/sglang/commit/8f765bc1c9542c4ff1c3b62ad16fbfe8882a5587)

- **作者**: zijiexia
- **时间**: 2026-07-17T08:07:09Z
- **提交信息**: [Docs] Inkling cookbook: mark B300/GB300 recipes verified, tune B300 MTP mem fractions (#31550)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [d67aa05](https://github.com/sgl-project/sglang/commit/d67aa0569727fb02d5b31644f45d361181dd6921)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-07-17T07:50:12Z
- **提交信息**: Bump FlashInfer to 0.6.15 and revert regressions (#31502)

Co-authored-by: Brayden Zhong <b8zhong@uwaterloo.ca>

### [e835512](https://github.com/sgl-project/sglang/commit/e835512303830bc3f10c83ec4d77c155c7b62ca0)

- **作者**: Baizhou Zhang
- **时间**: 2026-07-17T07:29:14Z
- **提交信息**: Add nightly test for GLM5.2 LayerSplit (#31512)

### [619609a](https://github.com/sgl-project/sglang/commit/619609aa5a2c4859cee79e9dd16a15cf1ff4c98a)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-07-17T07:06:26Z
- **提交信息**: [Kernel] Simplify sglang.kernels tests to idiomatic pytest style (RFC #29630) (#31546)

Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-07-18
**监控日期**: 2026-07-17
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1231
- **最后更新**: 2026-07-16T13:17:10Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-07-18
**监控日期**: 2026-07-17
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 86527
- **最后更新**: 2026-07-17T23:19:36Z

## 提交统计

- **昨日提交总数**: 28
- **提交者数量**: 24
- **主要提交者**: Chang Guo, JooHo Lee, passtoor-agi

## AI分析总结

### vllm-project/vllm 昨日更新总结

#### 1. 主要更新类型
- **Bug 修复**（约 7 项）：涉及 `prompt_logprobs`、GLM4V 视频 profilin、工具解析中保留空格、`data_parallel_size` 恢复、KV offloading 最后块释放、Transformer 后端 `weight_loader` 属性错误、FlashAttention MLA 预填兼容性、Qwen3-Omni 音频视频混合输入等。
- **性能优化**（约 4 项）：包括 dsv4 路由专用 kernel（2.94% E2E TPOT 提升）、CuTe-DSL 实现的 FlashInfer MXFP4 量化、ROCm gfx950 稀疏解码占用改善、beam-search 使用 `itertools.chain` 代替 `sum` 扁平化。
- **功能新增**（约 4 项）：支持 TranslateGemma-12b-it 模型、每 KV-cache 组可选不同 attention 后端、KV offload 新增层局部性事件、状态化训练器发送新抽象（RL 前置工作）。
- **重构与清理**：移除 DeepSeek 死代码。
- **硬件/平台支持扩展**：XPU（Intel）多项改进（bump 内核版本、支持 HND 布局、强制 flash attn）、AMD profiler 配置扩展、Helion B200 禁用 warp specialization 等。
- **CI/文档**：macOS wheel 注释上下文修复、非默认 wheel 构建门控、文档链接路径保留。

#### 2. 关键变更点与项目方向的关系
| 变更点 | 与项目方向

## 详细提交记录

### [fae5430](https://github.com/vllm-project/vllm/commit/fae543015cd49dfb4db3afb3a2e96d2eccb3e1db)

- **作者**: Wang Xingda
- **时间**: 2026-07-17T22:09:14Z
- **提交信息**: [Frontend]Flatten beam-search beams with itertools.chain instead of sum (#48829)

Signed-off-by: Wang Xingda <wangxingda1993@126.com>
Co-authored-by: 王兴达 <wangxingda@360itdeMacBook-Pro.local>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [c9be3a8](https://github.com/vllm-project/vllm/commit/c9be3a8aa1f01f7efdc99dd9439451617ef54a00)

- **作者**: Shangdi Yu
- **时间**: 2026-07-17T21:39:09Z
- **提交信息**: [Kernel][Helion] Disable warp specialization in rms_norm_per_block_quant B200 configs (#48797)

Signed-off-by: Shangdi Yu <shangdiy@meta.com>
Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [41ea2dd](https://github.com/vllm-project/vllm/commit/41ea2dd44a3a20c46ebeb985de0022c7673fb953)

- **作者**: aoshen02
- **时间**: 2026-07-17T20:58:59Z
- **提交信息**: [Bugfix][V1/V2] Fix prompt_logprobs to respect logprobs_mode (#47680)

Signed-off-by: Wojciech Wais <wojciech.wais@gmail.com>
Signed-off-by: Federico Kamelhar <209537060+fede-kamel@users.noreply.github.com>
Signed-off-by: Allen Shen <aoshen@inferact.ai>
Co-authored-by: Wojciech Wais <wojciech.wais@gmail.com>
Co-authored-by: Federico Kamelhar <209537060+fede-kamel@users.noreply.github.com>

### [088c0be](https://github.com/vllm-project/vllm/commit/088c0be2684fda35b18645bb36f0944a5c5fc941)

- **作者**: Kevin H. Luu
- **时间**: 2026-07-17T20:44:48Z
- **提交信息**: [CI] Fix macOS wheel release annotation context (#48771)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Codex <codex@openai.com>

### [fcd2255](https://github.com/vllm-project/vllm/commit/fcd2255d16bd3c62493bae5dee769ce998098f21)

- **作者**: devalshahamd
- **时间**: 2026-07-17T20:38:59Z
- **提交信息**: [Hardware][GPU] Profiler config additional to increase it scope and annotation details (#37524)

Signed-off-by: devalshahamd <deval.shah@amd.com>
Signed-off-by: Deval Shah <devashah@amd.com>
Signed-off-by: Deval Shah <deval.shah@amd.com>
Co-authored-by: Deval Shah <devashah@amd.com>

### [b5433b6](https://github.com/vllm-project/vllm/commit/b5433b6f5079feb32f9f278cf4ae23bd87375148)

- **作者**: Wentao Ye
- **时间**: 2026-07-17T20:35:06Z
- **提交信息**: [Perf] Optimize dsv4 routing using specialized kernel, 2.94% E2E TPOT improvement (#48660)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [cc25f02](https://github.com/vllm-project/vllm/commit/cc25f028b76844024fddd0b4ca18d4ca169b32be)

- **作者**: Michael Goin
- **时间**: 2026-07-17T20:30:02Z
- **提交信息**: [Loader] Improve InstantTensor loading (#46868)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [c4cd2bd](https://github.com/vllm-project/vllm/commit/c4cd2bd5440bca29039e5b6f33b695a95721bd3e)

- **作者**: limeward
- **时间**: 2026-07-17T19:35:04Z
- **提交信息**: [Bugfix] MoRIIO toy P/D proxy: fix DP-rank index aliasing + harden for high-concurrency bursts (#46115)

Signed-off-by: Edwin Lim <edwin.lim@mangoboost.io>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: QinPR <1905873179@qq.com>
Co-authored-by: Peiran Qin <66068739+QinPR@users.noreply.github.com>

### [5784507](https://github.com/vllm-project/vllm/commit/5784507da458656ef8248119590822445d4c67f2)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-07-17T19:19:02Z
- **提交信息**: [Attention] Allow selecting a different attention backend per KV-cache group (#48012)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>
Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>

### [bf578e1](https://github.com/vllm-project/vllm/commit/bf578e1abdffc2d25232783ff59a3132279e6bdd)

- **作者**: labAxiaoming
- **时间**: 2026-07-17T17:44:45Z
- **提交信息**: [Bugfix][GLM4V] Fix video dummy profiling and memory usage (#48729)

Signed-off-by: xiaoming <1259730330@qq.com>

### [efed8a1](https://github.com/vllm-project/vllm/commit/efed8a1e8345de2b4398a48243301d6a5b1a361e)

- **作者**: Fangzhou Ai
- **时间**: 2026-07-17T17:24:59Z
- **提交信息**: [ROCm][Perf][DSV4] Improve sparse decode reduction occupancy on gfx950 (#48788)

Signed-off-by: fai <fangzhouai@gmail.com>

### [11d2915](https://github.com/vllm-project/vllm/commit/11d291511a35bfa2a9ecb8fd21ee1c48b3a78d6b)

- **作者**: mosya415
- **时间**: 2026-07-17T16:45:41Z
- **提交信息**: [Bugfix][Tool Parser] Preserve whitespace in parameter values (MiniMax M2, Qwen3, MiniCPM5 XML) (#48846)

Signed-off-by: mosya415 <263250241+mosya415@users.noreply.github.com>
Signed-off-by: Ben Browning <56071+bbrowning@users.noreply.github.com>
Co-authored-by: mosya415 <263250241+mosya415@users.noreply.github.com>
Co-authored-by: Ben Browning <56071+bbrowning@users.noreply.github.com>

### [877dae9](https://github.com/vllm-project/vllm/commit/877dae9c684cd8cb2f66eed33f1c3261c6792c10)

- **作者**: Wentao Ye
- **时间**: 2026-07-17T14:57:13Z
- **提交信息**: [Refactor] Remove deepseek dead code (#48780)

Signed-off-by: yewentao256 <zhyanwentao@126.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [c4dd6d7](https://github.com/vllm-project/vllm/commit/c4dd6d78fd6485e103d71ba815b0a530e5c49439)

- **作者**: passtoor-agi
- **时间**: 2026-07-17T14:27:50Z
- **提交信息**: Fix: Restore data_parallel_size > 1 for use_sequence_parallel_moe (#48849)

Signed-off-by: passtoor-agi <305788622+passtoor-agi@users.noreply.github.com>

### [ce2aecc](https://github.com/vllm-project/vllm/commit/ce2aecc4dc42151d63f65d51c675edf28d40d671)

- **作者**: JooHo Lee
- **时间**: 2026-07-17T13:53:48Z
- **提交信息**: [Performance] Use CuTe-DSL for FlashInfer MXFP4 quantization (#48417)

Signed-off-by: BWAAEEEK <jooho414@gmail.com>

### [f38f3d1](https://github.com/vllm-project/vllm/commit/f38f3d11fb7b180c4d66f4af82cf770f335391cc)

- **作者**: AlexHuang
- **时间**: 2026-07-17T13:50:49Z
- **提交信息**: [Bugfix][KV Offloading] Offload last block at request finish and prevent reuse race (#48596)

Signed-off-by: Alex <alex.tech.lab@outlook.com>
Co-authored-by: Or Ozeri <oro@il.ibm.com>

### [d4b4562](https://github.com/vllm-project/vllm/commit/d4b45629172dfb792b44bd142982563a8c8bba9d)

- **作者**: Artur Fierka
- **时间**: 2026-07-17T12:43:23Z
- **提交信息**: [XPU] Bump vllm_xpu_kernels to v0.1.11.1 (#48942)

Signed-off-by: Artur Fierka <artur.fierka@intel.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [7b31925](https://github.com/vllm-project/vllm/commit/7b3192523e194e20077017ed104caff37c1ad691)

- **作者**: Yejing Lai
- **时间**: 2026-07-17T11:43:44Z
- **提交信息**: [Bugfix]Fix transformer backend failed: AttributeError: 'Parameter' object has no attribute 'weight_loader' (#48699)

Signed-off-by: Lai, Yejing <yejing.lai@intel.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [4c6e2e4](https://github.com/vllm-project/vllm/commit/4c6e2e4b308c15fc2bcdf10e278f2591c9cec0dc)

- **作者**: Yejing Lai
- **时间**: 2026-07-17T11:19:05Z
- **提交信息**: [XPU][UT]fix _POSSIBLE_KERNELS error on XPU (#47516)

Signed-off-by: Lai, Yejing <yejing.lai@intel.com>

### [8502958](https://github.com/vllm-project/vllm/commit/850295881041754184717804104fcaadd2b2129e)

- **作者**: liuzhenwei
- **时间**: 2026-07-17T10:54:34Z
- **提交信息**: [XPU] support HND layout (#47975)

Signed-off-by: zhenwei-intel <zhenwei.liu@intel.com>

### [ce4bdcb](https://github.com/vllm-project/vllm/commit/ce4bdcbda4f3c2da67b2fe241e80937ccdcc1fc6)

- **作者**: Julien Denize
- **时间**: 2026-07-17T10:07:00Z
- **提交信息**: [Bugfix] Enable FlashAttention MLA prefill for Mistral Small 4 head dims (#48855)

Signed-off-by: juliendenize <julien.denize@mistral.ai>
Co-authored-by: Nicolò Lucchesi <nlucches@redhat.com>

### [d5b1ec2](https://github.com/vllm-project/vllm/commit/d5b1ec268431f394efd6bad0f1b2adec657c31af)

- **作者**: liuzhenwei
- **时间**: 2026-07-17T09:44:18Z
- **提交信息**: [XPU] allow forcing flash attn for mm_prefix (#48828)

Signed-off-by: zhenwei-intel <zhenwei.liu@intel.com>

### [867ff69](https://github.com/vllm-project/vllm/commit/867ff69733dd32467a18fed288592373225d8db1)

- **作者**: Kevin H. Luu
- **时间**: 2026-07-17T09:16:44Z
- **提交信息**: [CI] Gate non-default release wheel builds (#48772)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [109b736](https://github.com/vllm-project/vllm/commit/109b736b8681dff6e2f547d89362afc3a9c77c00)

- **作者**: Sage
- **时间**: 2026-07-17T08:56:45Z
- **提交信息**: [docs] preserve page path in stable-docs announcement link (#48839)

Signed-off-by: Sage Ahrac <sagiahrak@gmail.com>

### [69d4f5e](https://github.com/vllm-project/vllm/commit/69d4f5ef6323a44621b10e0f269c2775db510cc5)

- **作者**: wendadawen
- **时间**: 2026-07-17T08:31:16Z
- **提交信息**: [Bugfix][Multimodal] Fix Qwen3-Omni use_audio_in_video with mixed image/video inputs (#46213)

Signed-off-by: wendadawen <wendadawen@qq.com>
Signed-off-by: Tianyu Guo <guoty9@mail2.sysu.edu.cn>
Co-authored-by: Tianyu Guo <guoty9@mail2.sysu.edu.cn>

### [426d48b](https://github.com/vllm-project/vllm/commit/426d48bfa149582664d48f89df21ec9beae5c37b)

- **作者**: Chang Guo
- **时间**: 2026-07-17T07:31:52Z
- **提交信息**: [KV Offload] Add optional tier locality to FS/OBJ KV events (#48281)

Signed-off-by: Change72 <changg@nvidia.com>
Co-authored-by: Codex <codex@openai.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [26c909e](https://github.com/vllm-project/vllm/commit/26c909ed74a6298952d0c3191fbfdf2b513d9e1d)

- **作者**: Zhang Jian
- **时间**: 2026-07-17T07:17:59Z
- **提交信息**: [Model] Support TranslateGemma-12b-it (#41599)

Signed-off-by: Zhang Jian <jianmusings@gmail.com>
Co-authored-by: Tyler Michael Smith <tlrmchlsmth@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>

### [fb1d8cc](https://github.com/vllm-project/vllm/commit/fb1d8ccaf5bc46935031ef074950eaa8232cd15e)

- **作者**: Aaron Hao
- **时间**: 2026-07-17T07:11:06Z
- **提交信息**: [rl] Stateful Trainer Send: New Abstractions [1/N]  (#48042)

Signed-off-by: haoaaron <ahao@anyscale.com>
Signed-off-by: Aaron Hao <ahao@anyscale.com>
Co-authored-by: Sumanth R Hegde <39546518+SumanthRH@users.noreply.github.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-07-18
**监控日期**: 2026-07-17
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 5609
- **最后更新**: 2026-07-17T18:49:31Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: bastefaniak, Weiming Liao

## AI分析总结

根据提供的提交记录和项目背景（vllm-omni：面向所有人的易、快、便宜的通用多模态模型服务），昨日更新要点总结如下：

---

### 1. 主要更新类型
- **Bug修复**：修复调度器RNG处理问题（提交 `d09f549`）
- **CI/测试增强**：为NPU（Ascend）添加夜间性能测试（提交 `7aa5c9a`）

---

### 2. 关键变更点及与项目方向的关系
| 变更点 | 与项目方向的关系 |
|--------|----------------|
| **修复FlowMatchEulerDiscreteScheduler的RNG处理**（对应diffusers 0.39.0） | 确保即将推出的**Cosmos3蒸馏模型**能正确运行，扩展项目对前沿多模态模型（NVIDIA Cosmos系列，可能涉及视频/图像生成）的支持 |
| **为NPU添加Qwen3-TTS夜间性能测试**（在A3硬件上） | 强化项目对**多硬件（NPU）** 和**多模态（文本转语音TTS）** 的覆盖，符合“服务于每个人”和“多模态模型服务”的宗旨 |

---

### 3. 对项目的影响和潜在意义
- **兼容性与稳定性**：修复RNG处理避免随机性偏差，保障Cosmos3等未来模型推理正确性，减少用户集成时的意外问题。
- **硬件生态扩展**：NPU性能测试常态化（夜间运行）可及时发现NPU上的回归，提升对国产/非GPU硬件的支持质量，吸引更多硬件平台用户。
- **模型覆盖广度**：Qwen3-TTS作为语音模型，Cosmos3作为生成模型，表明项目正从纯文本/视觉向多模态（语音+图像+视频）全面演进。

---

### 4. 值得关注的技术点
- **调度器RNG处理细节**：`FlowMatchEulerDiscreteScheduler` 在diffusers 0.39.0中的随机数生成方式变更，需确保分布式/多卡场景下的一致性（常见于多模态大模型推理）。
- **NPU测试框架**：在A3硬件上运行Qwen3-TTS，推测使用华为Ascend NPU，涉及自定义算子或图编译优化，测试结果可反映NPU上TTS模型的吞吐与延迟特性。

---

### 5. 结合项目背景，这些提交如何影响项目发展
- **加速前沿模型接入**：通过修复调度器，扫清Cosmos3蒸馏模型集成障碍，紧跟NVIDIA最新多模态开源模型趋势。
- **强化“便宜”与“易用”**：NPU通常比GPU成本低，针对NPU的CI测试确保用户能在更经济的硬件上使用TTS服务，降低使用门槛。
- **完善多模态服务矩阵**：从仅支持视觉/文本到涵盖语音（TTS）、生成（Cosmos3），逐步实现README中“omni-modality”的承诺，增强项目竞争力。

## 详细提交记录

### [d09f549](https://github.com/vllm-project/vllm-omni/commit/d09f549e862c58ca87c195d4050e77b20a126a38)

- **作者**: bastefaniak
- **时间**: 2026-07-17T18:38:04Z
- **提交信息**: [bugfix] Use FlowMatchEulerDiscreteScheduler from diffusers 0.39.0 with correct RNG handling for upcoming Cosmos3 distilled models (#5176)

Signed-off-by: Bartosz Stefaniak <bstefaniak@nvidia.com>

### [7aa5c9a](https://github.com/vllm-project/vllm-omni/commit/7aa5c9a0901b7b9254052c4d342d0c3fa447eb95)

- **作者**: Weiming Liao
- **时间**: 2026-07-17T09:32:48Z
- **提交信息**: [CI][NPU]:  Add nightly performance test for NPU - Qwen3-TTS on A3 (#5158)

Signed-off-by: Weiming Liao <liaowm5@gmail.com>
Co-authored-by: wangyu <53896905+yenuo26@users.noreply.github.com>

---
