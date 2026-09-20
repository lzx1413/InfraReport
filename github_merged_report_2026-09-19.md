# GitHub Stars 合并报告 - 2026-09-19

**合并日期**: 2026-09-20
**监控日期**: 2026-09-19
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


**报告日期**: 2026-09-20
**监控日期**: 2026-09-19
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2214
- **最后更新**: 2026-09-19T10:58:04Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-09-20
**监控日期**: 2026-09-19
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2830
- **最后更新**: 2026-09-18T21:15:32Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-09-20
**监控日期**: 2026-09-19
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2253
- **最后更新**: 2026-09-19T18:15:55Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-09-20
**监控日期**: 2026-09-19
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6453
- **最后更新**: 2026-09-19T23:35:34Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: feih-nv

## AI分析总结

## 1. 主要更新类型

- **功能新增/架构统一**：核心是让 CUTLASS 统一 runner 消费与 TRT-LLM / CuTe-DSL / Cake 相同的 `MoEActivationPack`。
- **重构（接口对齐）**：不修改 kernel 和 `core.py`，仅调整激活量化与配置层，属于接口层面的重构。
- **测试增强**：新增混合候选（mixed-candidate）测试，覆盖多后端共享同一激活包。
- **文档更新**：设计文档移除旧的 singleton-candidate 指引，改为“每个 MMA pair 一个激活包”的描述。

## 2. 关键变更点及与项目方向的关系

- **统一激活包**：同一 `MoEActivationPack` 可服务多个 MMA 候选（如 `TrtllmFp4Config()` 与 `CutlassNvfp4Config()` 混用），消除了此前各后端各自准备激活的割裂。
- **NVFP4 量化格式变更**：从 BF16 内核内量化改为 packed `uint8 [M, H/2]` + 线性 E4M3 `[M, H/16]` scale，并要求 `hidden_size % 64 == 0`。
- **MXFP8/MXFP4×MXFP8**：默认线性 `[M, H/32]` scale，可选 swizzled 1-D `input_sf`（仅 CUTLASS MXFP8 支持）。
- **配置拒绝逻辑**：CUTLASS runner 拒绝 `per_token_scale=True` 及携带该字段的 pack。

这与 FlashInfer 作为“高性能 GPU 推理内核库”的整体方向一致：通过统一 MoE 激活接口，减少后端碎片化，提升多后端组合的可用性。

## 3. 对项目的影响和潜在意义

- **降低集成成本**：用户可在同一激活包上混合不同量化后端，简化 MoE 推理部署。
- **提升一致性**：TRT-LLM、CuTe-DSL、CUTLASS 共享量化语义，减少因后端差异导致的精度/行为偏差。
- **精度基准修正**：NVFP4 参考实现现模拟 GEMM2 输入的 NVFP4 重量化，误差减半，修复了 VR200 CI 上超出 0.3 容差的问题。
- **潜在约束**：NVFP4 对 `hidden_size` 的 64 对齐要求，可能限制部分模型配置。

## 4. 值得关注的技术点

- **共享 `prepare.py` 助手**：`CutlassNvfp4Config.prepare_activations` 直接复用 `TrtllmFp4Config` 的实现，体现“同一 pack 一行”的设计。
- **设备能力降级处理**：测试中候选若在测试设备上不支持（如 SM107 上的 CuTe-DSL W4A8），则被丢弃而非报错，提升测试鲁棒性。
- **swizzled scale 的排他性**：仅 CUTLASS MXFP8 接受，其他后端在 `check_support` 中拒绝，避免误用。
- **per_token_scale 的显式拒绝**：明确边界，防止不支持的量化路径静默通过。

## 5. 基于 README 背景的项目发展影响

FlashInfer 定位为“面向推理的高性能 GPU 内核”，强调多后端与多量化方案的支持。本次提交通过统一 MoE 激活包，强化了“一次准备、多后端消费”的能力，直接服务于 MoE 推理这一大模型关键场景。它使项目在保持内核高性能的同时，提升了跨后端组合的工程可用性，符合其作为推理基础设施库的演进方向——从“各后端独立”走向“接口统一、后端可插拔”。长期看，这有助于降低用户在不同量化方案间切换的成本，并推动更多混合精度 MoE 部署落地。

## 详细提交记录

### [0a761d1](https://github.com/flashinfer-ai/flashinfer/commit/0a761d12ae3ee6867278f864b26bdfd6cb4fd100)

- **作者**: feih-nv
- **时间**: 2026-09-19T23:06:11Z
- **提交信息**: feat(moe): CUTLASS unified runners consume the TRT-LLM canonical activation packs (#5230)

<!-- .github/pull_request_template.md -->

## 📌 Description

Unified CUTLASS runners now consume the same `MoEActivationPack` as
TRT-LLM / CuTe-DSL / Cake for each MMA pair, so mixed candidate sets
like `(TrtllmFp4Config(), CutlassNvfp4Config())` work on one pack. No
kernel / `core.py` changes.

- **NVFP4**: packed `uint8 [M, H/2]` + linear E4M3 `[M, H/16]` scale
(was BF16, in-kernel quant). `hidden_size % 64 == 0` required (kernel
reads the linear scale with a 64-padded row stride);
`prepare_cutlass_nvfp4_weights` rejects other H at load time.
- **MXFP8 / MXFP4×MXFP8**: linear `[M, H/32]` scale by default;
`QuantConfig(swizzled_scale_factors=True)` selects the flat swizzled 1-D
`input_sf` (CUTLASS MXFP8 runners only; CUTLASS NVFP4, TRT-LLM and
CuTe-DSL reject it in `check_support`).
`Cutlass*Mxfp8*Config.prepare_activations(x, quant=config.quant)` reads
the layout from the same `QuantConfig` the layer declares.
- `Cutlass*Config.prepare_activations` produce the canonical packs via
the shared `prepare.py` helpers
(`CutlassNvfp4Config.prepare_activations` is
`TrtllmFp4Config.prepare_activations`); `MoEActivationPack` docs one row
per pair; design doc drops #4914's singleton-candidate guidance and
describes the shared pack in an undated "One activation pack per MMA
pair" bullet instead of a changelog section; `unified_moe` benchmark
quantizes for CUTLASS NVFP4.
- New mixed-candidate tests run one pack through TRT-LLM + CuTe-DSL +
CUTLASS (NVFP4, MXFP4×MXFP8) and TRT-LLM + CUTLASS (MXFP8); candidates
that decline the pair on the test device (CuTe-DSL W4A8 on SM107) are
dropped, not failed. The NVFP4 reference now models the kernels'
GEMM2-input NVFP4 requantization, which halves its error against every
backend (VR200 CI had crossed the unchanged 0.3 tolerance by one
element).
- CUTLASS runners reject `QuantConfig(per_token_scale=True)` and a pack
carrying `per_token_scale`; the flat ABI has no such input and packing
silently dropped it (pre-existing, surfaced in review).

TODO: `activation_prequantized` knob for a CUTLASS BF16-in-kernel path,
if a framework needs it.

## 🔍 Related Issues

- Follow-up to #4610 / #4914 (unified CUTLASS runners) and #5061
(three-axis `QuantConfig`); reverts #4914's "choose one singleton
candidate set" guidance.

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

On SM100 (B200):
- `tests/moe/test_unified_moe_cutlass.py` — all pass, including new
mixed-candidate tests that build one `MoELayer` over TRT-LLM + CuTe-DSL
+ CUTLASS (NVFP4, MXFP4×MXFP8) and TRT-LLM + CUTLASS (MXFP8) on a single
pack.
- `tests/moe/test_unified_moe_fuzz.py -k cutlass` — CUTLASS contract
handlers moved onto the canonical packs.
- `tests/moe/test_unified_moe.py -k "cutlass or swizzled or Backend"` —
pass.
- `benchmarks/flashinfer_benchmark.py --routine unified_moe
--quant-variant nvfp4 --backends cutlass --refcheck` — pass.

## Reviewer Notes

- User-visible changes:
- `CutlassNvfp4Config` takes the pre-quantized NVFP4 pack, not BF16
(b12x / cuTile still take BF16).
- `CutlassNvfp4Config.prepare_weights` rejects `hidden_size % 64 != 0`
at load time; on `main` such shapes ran via in-kernel quantization.
- `CutlassNvfp4Config.prepare_activations` is an alias of
`TrtllmFp4Config.prepare_activations` (same default, optional `quant=`);
`CutlassMxfp8Config` / `CutlassMxfp8Mxfp4Config.prepare_activations`
take `quant=` (the layer's `MoEConfig.quant`) instead of a
`swizzled_scale_factors` bool.
- CUTLASS runners reject `QuantConfig(per_token_scale=True)` instead of
ignoring it.
- `_DEFAULT_BACKEND` unchanged.

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-09-20
**监控日期**: 2026-09-19
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4478
- **最后更新**: 2026-09-19T23:05:54Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-09-20
**监控日期**: 2026-09-19
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34548
- **最后更新**: 2026-09-19T19:37:50Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-09-20
**监控日期**: 2026-09-19
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


**报告日期**: 2026-09-20
**监控日期**: 2026-09-19
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13140
- **最后更新**: 2026-09-19T22:52:19Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-09-20
**监控日期**: 2026-09-19
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 36177
- **最后更新**: 2026-09-19T23:00:45Z

## 提交统计

- **昨日提交总数**: 17
- **提交者数量**: 12
- **主要提交者**: kk, Benjamin Truong, amd-danli103

## AI分析总结

# SGLang 昨日提交分析总结

## 1. 主要更新类型

- **性能优化为主**：MoE 内核、调度器、KV 缓存、logprob 计算等多处深度优化。
- **功能新增**：MegaMoE 接入 Qwen MoE、HiCache 主机池自动伸缩。
- **Bug 修复**：GLM-5.2 分离式 PP MTP、AMD HIP 后端、mHC 上下文泄漏、CI 测试桩等。
- **重构与清理**：去重内核测试、diffusion fixtures 与 benchmark 辅助代码。

## 2. 关键变更点与项目方向

- **MegaMoE 接入 Qwen MoE（MXFP4/NVFP4）**：将 DeepGEMM 的 MegaMoE 内核与 Qwen MoE 块打通，延续项目对低精度（FP4）MoE 推理的深度支持。
- **调度器统计完整 prefill burst 及其 token 数**：增强调度可观测性，服务于大规模推理的吞吐与延迟调优。
- **HiCache 主机池自动适配可用内存**：降低部署门槛，提升异构硬件下的缓存利用率。
- **DSV4/DSV4.1 系列优化**：索引器 MQA logits 分块、mHC 与元数据开销削减、融合 wo_a 量化，持续打磨 DeepSeek 系列模型推理效率。
- **ROCm/AMD 专项修复与优化**：kv_splits 按索引流选择、HiCache JIT 拷贝轮次加宽、K-only 主机池启用，体现对 AMD 平台的持续投入。

## 3. 对项目的影响与潜在意义

- 强化 SGLang 作为**高性能 LLM 推理引擎**的定位，尤其在 MoE 与低精度量化场景。
- 调度与缓存优化直接提升**大模型服务吞吐与显存/内存效率**，利好生产部署。
- AMD/ROCm 与 NVIDIA 双平台并进，扩大硬件生态覆盖。
- CI 与测试清理提升**工程健壮性与可维护性**，降低回归风险。

## 4. 值得关注的技术点

- **MXFP4/NVFP4 专家 + DeepGEMM MegaMoE** 的融合路径，代表 FP4 推理前沿。
- **CUDA-graph-pool 死区复用** 服务 input-logprob 临时张量，是显存精细化管理范例。
- **mHC 上下文隔离** 避免污染非 V4 编译 MoE 前向，涉及编译期与运行期边界。
- **索引器 MQA logits 按 query 行分块**，在显存预算下平衡并行度与开销。

## 5. 结合 README 的项目发展意义

README 显示 SGLang 聚焦**高吞吐、低延迟的 LLM 与多模态服务**，并强调与主流模型（Qwen、DeepSeek、GLM 等）及多硬件后端兼容。本批提交正是这一方向的延续：一方面通过 FP4 MoE、HiCache、调度统计等提升核心推理性能；另一方面通过 AMD/ROCm 修复与 CI 加固保障跨平台稳定性。整体看，项目正从“可用”向“生产级高效、多硬件、多模型统一服务”稳步演进。

## 详细提交记录

### [9cc7da2](https://github.com/sgl-project/sglang/commit/9cc7da2ab0b305f7aecd45f7b0854c7e20535640)

- **作者**: YAMY
- **时间**: 2026-09-19T23:00:38Z
- **提交信息**: [MegaMoE] Wire Qwen MoE blocks to DeepGEMM MegaMoE (MXFP4 and NVFP4 experts) (#38080)

### [3a64faa](https://github.com/sgl-project/sglang/commit/3a64faa1f22a86abd37a759c84267d929e820d5b)

- **作者**: Po-Han Huang (NVIDIA)
- **时间**: 2026-09-19T20:55:07Z
- **提交信息**: Fix disagg PP MTP for GLM-5.2 (#39378)

Co-authored-by: Julien Lin <jullin@nvidia.com>
Co-authored-by: YAMY1234 <74099316+YAMY1234@users.noreply.github.com>
Co-authored-by: Yangmin Li <yangminl@nvidia.com>

### [8139a17](https://github.com/sgl-project/sglang/commit/8139a1740e06264867d871ab5cd82bca194b7b35)

- **作者**: metamergebot
- **时间**: 2026-09-19T19:56:15Z
- **提交信息**: [Scheduler] Count complete prefill bursts and their tokens (#40006)

Co-authored-by: pranjalssh <pranjalssh@fb.com>
Co-authored-by: Jialin Ouyang <Jialin.Ouyang@gmail.com>
Co-authored-by: Jialin Ouyang <jialino@meta.com>
Co-authored-by: Lianmin Zheng <lianminzheng@gmail.com>

### [7a6c652](https://github.com/sgl-project/sglang/commit/7a6c652c778723378556de1003beec2fd92a131b)

- **作者**: Zhiqiang Xie
- **时间**: 2026-09-19T19:50:43Z
- **提交信息**: [HiCache] Auto-size the host pool to fit available host memory (#40135)

### [2305242](https://github.com/sgl-project/sglang/commit/2305242f514da95eba3c411de0517c4d79ffff94)

- **作者**: amd-danli103
- **时间**: 2026-09-19T19:13:49Z
- **提交信息**: [AMD][DSV4] fix: skip compressed-KV metadata on the draft worker in the HIP radix backend (#40205)

### [9e5a62a](https://github.com/sgl-project/sglang/commit/9e5a62a767433b66a0e608276ca520d4e53e765b)

- **作者**: metamergebot
- **时间**: 2026-09-19T19:03:52Z
- **提交信息**: [Logprob] Serve input-logprob temporaries from CUDA-graph-pool dead space (#40038)

Co-authored-by: cctry <csycfl@gmail.com>

### [c5326d2](https://github.com/sgl-project/sglang/commit/c5326d28a348dfba14e908cb055ea4c8ec2a92fa)

- **作者**: kk
- **时间**: 2026-09-19T18:53:54Z
- **提交信息**: [AMD] dsv4: pick kv_splits per index stream, not by occupancy alone (#39968)

Co-authored-by: wunhuang <wunhuang@amd.com>

### [7b67a96](https://github.com/sgl-project/sglang/commit/7b67a966403e3e959aea6262b72b75a274339f85)

- **作者**: Junpan Wu
- **时间**: 2026-09-19T18:53:20Z
- **提交信息**: [DSV4] Chunk the indexer MQA logits by query rows under a free-memory budget (#39095)

Signed-off-by: Shiki Wu <shikiw@nvidia.com>
Co-authored-by: Baizhou Zhang <sobereddiezhang@gmail.com>
Co-authored-by: Yuwei An <ayw.sirius19@gmail.com>

### [993d1fc](https://github.com/sgl-project/sglang/commit/993d1fccbaafe3e79d91567d2fc1d665cc94fa50)

- **作者**: Zhang, Jiejing
- **时间**: 2026-09-19T15:58:10Z
- **提交信息**: [ROCm] Widen the HiCache JIT copy rounds and enable the K-only host pool (#37152)

Co-authored-by: Xiaobo Chen <xiaobche@smci355-ccs-aus-n05-33.prov.aus.ccs.cpe.ice.amd.com>
Co-authored-by: HAI <hixiao@gmail.com>

### [76f9213](https://github.com/sgl-project/sglang/commit/76f9213a411018547f4fd6a75f36feaa4d6bed58)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-09-19T13:41:51Z
- **提交信息**: [Fix] Keep mHC context out of non-V4 compiled MoE forwards (#40353)

### [9e2298e](https://github.com/sgl-project/sglang/commit/9e2298e913b32548d7381977159d676871424ffb)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-09-19T13:07:06Z
- **提交信息**: [CI] Propagate full-run fast-fail policy to reusable workflows (#40349)

### [83e29d6](https://github.com/sgl-project/sglang/commit/83e29d6c5aed7ca30d088d443607619aee17405e)

- **作者**: Benjamin Truong
- **时间**: 2026-09-19T12:34:25Z
- **提交信息**: [perf] Optimize w4a8 MoE for glm5.2 on H200 (#38220)

Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

### [7fac84b](https://github.com/sgl-project/sglang/commit/7fac84b6391b56b4469e0c29fd1ae0a3c0d871c6)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-09-19T11:51:21Z
- **提交信息**: [DSV4.1] Reduce mHC, metadata and small-batch router overhead (#39704)

### [d1acbe0](https://github.com/sgl-project/sglang/commit/d1acbe07467e7b82a61ae31b8ba0cd1788c4dcb9)

- **作者**: DarkSharpness
- **时间**: 2026-09-19T11:46:53Z
- **提交信息**: [DSV4.1] Big fused wo_a quant (#39957)

Co-authored-by: BBuf <1182563586@qq.com>

### [cb22f24](https://github.com/sgl-project/sglang/commit/cb22f2451e8efc8dc1f298fb50b6c41d3106e881)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-09-19T11:45:38Z
- **提交信息**: [Cleanup] Deduplicate kernel tests, diffusion fixtures and benchmark helpers (#40265)

### [0b0d2c2](https://github.com/sgl-project/sglang/commit/0b0d2c257a8ecd7c9f23cd4144e18b31dc729143)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-09-19T10:16:05Z
- **提交信息**: [Fix] Repair CI fixtures and ROCm speculative tree device checks (#40325)

### [567d592](https://github.com/sgl-project/sglang/commit/567d5925fe896a7b70043271f5621d6fe6e650d4)

- **作者**: Cheng Wan
- **时间**: 2026-09-19T07:43:56Z
- **提交信息**: Fix mxfp4 padding test stubbing an accessor the module no longer imports (#40308)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-09-20
**监控日期**: 2026-09-19
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1282
- **最后更新**: 2026-09-18T01:53:39Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-09-20
**监控日期**: 2026-09-19
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 92187
- **最后更新**: 2026-09-19T23:53:53Z

## 提交统计

- **昨日提交总数**: 13
- **提交者数量**: 12
- **主要提交者**: Ryan Rock, David Cheung, Wentao Ye

## AI分析总结

# vLLM 昨日提交分析（13 条）

## 1. 主要更新类型分布

- **Bug 修复（4 条）**：MoE reprocess 测试 mock 修复、ragged decode 批次走 padded 路径、MiMo-V2.5 fused FP8 qkv_proj 分片修复、DSA offset candidate 缓冲区避免运行时 JIT。
- **性能优化（3 条）**：GLM-5 稀疏 indexer decode workspace 显存优化、sm_120 批不变持久化 matmul 调优配置、ROCm AITER GDN decode 快路径。
- **功能新增（2 条）**：Model Runner V2 支持自定义 logits processors、ModelOpt MXFP8 加载预处理权重。
- **重构（1 条）**：processor 中改用动态 MM cache。
- **测试/文档/CI（3 条）**：新增 `get_unhashed_block_ids_all_groups` 测试、Triton 指针对齐 JIT 特化文档、AMD CI 升级 torchao。

## 2. 关键变更点与项目方向

- **显存与性能持续压榨**：GLM-5 稀疏 indexer 单次节省 3072 MiB 显存，sm_120 针对 RTX 50/Pro 6000 提供专用调优，ROCm 侧启用 AITER 快路径——延续 vLLM “easy, fast, cheap” 的核心理念，覆盖 NVIDIA 新架构与 AMD 生态。
- **新模型/新硬件适配**：MiMo-V2.5、GLM-5、MXFP8 量化等，说明项目在快速跟进前沿模型与量化格式。
- **Model Runner V2 演进**：支持自定义 logits processors，是架构升级的重要一步，为后续可扩展性铺路。
- **重构与测试补强**：动态 MM cache、补充单测，体现工程成熟度提升。

## 3. 对项目的影响与潜在意义

- 显存节省直接提升单卡可服务模型规模与并发吞吐，对低成本部署意义显著。
- 修复 ragged decode 与 MoE 测试，保障 CI 稳定性与推理正确性，避免回归。
- ROCm 与 sm_120 优化扩大硬件覆盖面，增强跨平台竞争力。
- ModelOpt MXFP8 预处理权重加载，降低量化部署门槛。

## 4. 值得关注的技术点

- **稀疏注意力 indexer 的 workspace 尺寸化**：显存精细管理思路可复用到其他稀疏算子。
- **批不变（batch-invariant）持久化 matmul**：保证不同 batch 下数值一致，对可复现性与正确性关键。
- **DSA 避免运行时 JIT**：减少首 token 延迟抖动，提升服务稳定性。
- **Triton 指针对齐 JIT 特化文档**：揭示 kernel 性能调优的底层机制。

## 5. 结合 README 的项目发展影响

vLLM 定位为“人人可用、快速、廉价”的 LLM 服务引擎。本批提交从三个维度支撑该目标：**性能**（显存节省、硬件调优）、**兼容性**（新模型、AMD/NVIDIA 新卡、量化格式）、**可靠性**（Bug 修复与测试补强）。整体看，项目正从“支持更多模型”向“在更多硬件上更高效、更稳定地服务”深化，符合其成为通用高性能推理引擎的长期方向。

## 详细提交记录

### [674b6d9](https://github.com/vllm-project/vllm/commit/674b6d95d6d0bd63b44cae0abe2bf304328c73e9)

- **作者**: vllm-agent
- **时间**: 2026-09-19T21:42:21Z
- **提交信息**: [CI][Bugfix] Fix MoE reprocess test mock after #57405's kernel refactor (#57641)

Signed-off-by: kimi-no-na-wa <kimi-no-na-wa@users.noreply.github.com>
Signed-off-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>
Co-authored-by: kimi-no-na-wa <kimi-no-na-wa@users.noreply.github.com>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>

### [36fa72d](https://github.com/vllm-project/vllm/commit/36fa72d2d0d2f86c7c83e1e99c9012b7bd26463b)

- **作者**: Wentao Ye
- **时间**: 2026-09-19T20:57:01Z
- **提交信息**: [GLM5.3 Perf] Size the GLM-5 sparse indexer decode workspace, 3072 MiB GPU memory saved (#57701)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [133b71e](https://github.com/vllm-project/vllm/commit/133b71e0beec3c7bcaae5b0839a03e7e88d20bc7)

- **作者**: Pavel Zakharov
- **时间**: 2026-09-19T20:14:29Z
- **提交信息**: [Bugfix] Take padded path for ragged decode batches in sparse_attn_indexer (#52500)

Signed-off-by: pavelzak <pavel.zakharov@gmail.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: Jee Jee Li <pandaleefree@gmail.com>

### [5302d1f](https://github.com/vllm-project/vllm/commit/5302d1fe40e6969b854e0ab288d34825653767c6)

- **作者**: David Cheung
- **时间**: 2026-09-19T17:46:49Z
- **提交信息**: [Model Runner V2] Support custom logits processors (#56497)

Signed-off-by: David Cheung <d7cheung@gmail.com>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>

### [751f680](https://github.com/vllm-project/vllm/commit/751f6807d9cb3de50c27a5f27188c4fb04fe0e2b)

- **作者**: Cyrus Leung
- **时间**: 2026-09-19T15:38:00Z
- **提交信息**: [Refactor] Use dynamic MM cache in processor (#57674)

Signed-off-by: DarkLight1337 <tlleungac@connect.ust.hk>

### [41c4a3e](https://github.com/vllm-project/vllm/commit/41c4a3ed4e45792739bd8a5bbcd01269b06eae2c)

- **作者**: Lio Einaudi
- **时间**: 2026-09-19T13:30:55Z
- **提交信息**: [Kernel][Perf] Add sm_120 (RTX PRO 6000 / RTX 50) tuned configs for batch-invariant persistent matmul (#57456)

Signed-off-by: LioEinaudi <zhao3024667639@gmail.com>

### [fbe8a15](https://github.com/vllm-project/vllm/commit/fbe8a157fbdd4b2f813ae6395397232de97d5c5d)

- **作者**: Mikko Tukiainen
- **时间**: 2026-09-19T13:05:04Z
- **提交信息**: [ROCm][Perf] Enable the AITER GDN decode fast path for flat qkvz layouts (#53623)

Signed-off-by: Mikko Tukiainen <Mikko.Tukiainen@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: TJian <tunjian.tan@embeddedllm.com>

### [211e252](https://github.com/vllm-project/vllm/commit/211e252d0b4f8429f9b15fc52bdfed07782c7f70)

- **作者**: vllmellm
- **时间**: 2026-09-19T13:05:00Z
- **提交信息**: [Bugfix][Model] Fix MiMo-V2.5 fused fp8 qkv_proj sharding (pre-shard count is num_key_value_heads; MTP path too) (#57508)

Signed-off-by: vllmellm <vllm.ellm@embeddedllm.com>

### [4cc15f2](https://github.com/vllm-project/vllm/commit/4cc15f2121b3421478f3186aac38de901b4a44ef)

- **作者**: siyu
- **时间**: 2026-09-19T09:16:39Z
- **提交信息**:  [Quantization] Let ModelOpt MXFP8 layers load pre-processed weights  Purpose (#57316)

Signed-off-by: liusy58 <mg21330037@smail.nju.edu.cn>
Signed-off-by: Isotr0py <2037008807@qq.com>
Co-authored-by: Isotr0py <2037008807@qq.com>

### [a5a3047](https://github.com/vllm-project/vllm/commit/a5a30471ff2bb7f0824f2da10e358af98d304472)

- **作者**: Aditya Ganesh Kumar
- **时间**: 2026-09-19T09:13:54Z
- **提交信息**: [Tests] Cover get_unhashed_block_ids_all_groups (#55928)

Signed-off-by: Aditya Ganesh Kumar <adty910@gmail.com>

### [c3b4844](https://github.com/vllm-project/vllm/commit/c3b48446349569512749db7f6e2164aa8a33437d)

- **作者**: Woosuk Kwon
- **时间**: 2026-09-19T07:53:42Z
- **提交信息**: [Docs] Explain pointer-alignment JIT specialization in Triton skill (#57669)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>

### [3853733](https://github.com/vllm-project/vllm/commit/38537331d3e8b37e480f1bbc174f78888e6c5252)

- **作者**: Woosuk Kwon
- **时间**: 2026-09-19T07:27:11Z
- **提交信息**: [Bugfix][DSA] Avoid runtime JIT for offset candidate end buffers (#57667)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>

### [59e6682](https://github.com/vllm-project/vllm/commit/59e6682c21595b3f71c4a569318d1a1ac328add3)

- **作者**: Ryan Rock
- **时间**: 2026-09-19T07:13:16Z
- **提交信息**: [CI][AMD] Bump torchao to v18 for Python 3.14 (#53009)

Signed-off-by: Ryan Rock <ryan.rock@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-09-20
**监控日期**: 2026-09-19
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 6910
- **最后更新**: 2026-09-19T23:02:55Z

## 提交统计

- **昨日提交总数**: 10
- **提交者数量**: 10
- **主要提交者**: chethanuk, Inesh Reddy Chappidi, TaffyOfficial

## AI分析总结

# vllm-omni 昨日提交分析（共10条）

## 1. 主要更新类型
- **Bug修复为主**：约6条（#7525、#7298、#6826、#7579、#7826、#7628），覆盖测试、分布式、音频、量化、缓存等。
- **重构**：3条（#5172、#6654、#7326），涉及配置校验、前缀缓存架构、分布式拓扑规划。
- **功能新增**：1条（#4083，新增 Anima 模型支持）。

## 2. 关键变更点与项目方向
- **模型生态扩展**：新增 circlestone-labs/Anima，延续项目“omni-modality 多模态模型服务”的定位。
- **架构级重构**：将 omni 前缀缓存拆分为 Manager/Controller（#6654），并在 plan 阶段解析分布式 layerwise 拓扑（#7326），说明项目正从“能跑”走向“可扩展、可维护”的工程化阶段。
- **配置健壮性**：拒绝未知 diffusion 配置字段（#5172），减少静默错误，提升用户配置体验。
- **多模态细节修复**：HunyuanImage3 离线测试重定向、HiggsAudio v2 参考音频缓存盐、Qwen-Image AutoRound W4A16 CPU offload，均针对具体模型链路。

## 3. 对项目的影响与潜在意义
- 修复类提交提升了**测试稳定性与推理正确性**，尤其分布式副本统计（#7298）和单调时钟超时（#7628）直接影响多副本服务的可靠性。
- 前缀缓存重构是**核心性能路径**的架构调整，为后续缓存策略优化和并发扩展打基础。
- 配置严格化与拓扑规划重构，降低了**大规模部署的隐性风险**，契合“fast、cheap serving”的目标。

## 4. 值得关注的技术点
- **前缀缓存 Manager/Controller 分离**：可能引入更清晰的职责边界，便于独立扩展与测试。
- **分布式 layerwise 拓扑在 plan 阶段解析**：将拓扑决策前移，利于资源调度与并行策略优化。
- **AutoRound W4A16 在 offload 时保持 CPU**：量化+卸载组合场景的典型坑，修复具代表性。
- **缓存盐（cache salt）纳入参考音频**：多模态缓存键设计的关键细节，避免音频串扰。

## 5. 结合项目背景的发展影响
vllm-omni 定位为“人人可用的全模态模型服务”，强调易用、快速、低成本。本批提交一方面通过模型新增与多模型 Bug 修复**拓宽可用模型面**；另一方面通过前缀缓存、分布式拓扑、配置校验等重构**夯实底层服务能力**。整体呈现“广度扩展 + 深度加固”并行的节奏，有助于项目从实验性多模态支持走向生产级稳定服务。

## 详细提交记录

### [573ec4c](https://github.com/vllm-project/vllm-omni/commit/573ec4cdace9dceafff8ee9f6aa11b207a832938)

- **作者**: chethanuk
- **时间**: 2026-09-19T18:16:13Z
- **提交信息**: fix(e2e): re-point HunyuanImage3 offline test to text_to_image.py (#7525)

Signed-off-by: ChethanUK <chethanuk@outlook.com>
Signed-off-by: Gao Han <hgaoaf@connect.ust.hk>
Co-authored-by: Gao Han <hgaoaf@connect.ust.hk>

### [fa506e0](https://github.com/vllm-project/vllm-omni/commit/fa506e0fe80365c90d75701e44b4308ee8eacf2a)

- **作者**: leegangtoe
- **时间**: 2026-09-19T17:07:14Z
- **提交信息**: [Bugfix] Register statistics for dynamically added replicas (#7298)

Signed-off-by: leegangtoe <leegangtoe@gmail.com>

### [51c715c](https://github.com/vllm-project/vllm-omni/commit/51c715c7ef87c23bde02cb274a3741f3d8301857)

- **作者**: Inesh Reddy Chappidi
- **时间**: 2026-09-19T17:04:58Z
- **提交信息**: [Bugfix][Test] Assert stable-audio CPU offload savings on max_memory_allocated (#6826)

Signed-off-by: Inesh Reddy <ineshreddy249@gmail.com>
Signed-off-by: Inesh Reddy Chappidi <ineshreddy249@gmail.com>

### [23d8c83](https://github.com/vllm-project/vllm-omni/commit/23d8c83dab27037332205b376d4986dec158b366)

- **作者**: NumberWan
- **时间**: 2026-09-19T16:34:11Z
- **提交信息**: [Bugfix][Qwen-Image] Keep AutoRound W4A16 on CPU when offloading; Fixes #7555 (#7579)

Signed-off-by: NumberWan <wantszkin2003@gmail.com>

### [f9f53f2](https://github.com/vllm-project/vllm-omni/commit/f9f53f2bd8ddf7c7990b167d448108daa50f992a)

- **作者**: boatman
- **时间**: 2026-09-19T16:19:14Z
- **提交信息**: [Bugfix]Include Reference Audio Cache Salt for HiggsAudio v2 (#7826)

Signed-off-by: boatman <109857087+sphinxkkkbc@users.noreply.github.com>

### [415005b](https://github.com/vllm-project/vllm-omni/commit/415005be22568f29c02c1e419a786dfebe747954)

- **作者**: akshatvishu
- **时间**: 2026-09-19T16:16:38Z
- **提交信息**: [Model] Add circlestone-labs/Anima (#4083)

Signed-off-by: akshatvishu <akshatnayak197@gmail.com>

### [698f716](https://github.com/vllm-project/vllm-omni/commit/698f7160125d3071b8c0eef69b1b03fa8dfba766)

- **作者**: TaffyOfficial
- **时间**: 2026-09-19T15:37:34Z
- **提交信息**: [Refactor] Reject unknown diffusion config fields (#5172)

Signed-off-by: TaffyOfficial <2324465096@qq.com>
Signed-off-by: zuiho <2324465096@qq.com>
Signed-off-by: Gao Han <hgaoaf@connect.ust.hk>
Co-authored-by: TaffyOfficial <2324465096@qq.com>
Co-authored-by: Gao Han <hgaoaf@connect.ust.hk>

### [f90c267](https://github.com/vllm-project/vllm-omni/commit/f90c267ffb61c79e42f0165476909b995caedd83)

- **作者**: psv666
- **时间**: 2026-09-19T13:25:14Z
- **提交信息**: [Bugfix] Use monotonic clocks for test server startup timeouts (#7628)

Signed-off-by: psv666 <2693925048@qq.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [470ec60](https://github.com/vllm-project/vllm-omni/commit/470ec60848fa98e030298706cceff88ae8f691a8)

- **作者**: Zheng Wengang
- **时间**: 2026-09-19T13:23:59Z
- **提交信息**: [Core] Refactor omni prefix cache into Manager/Controller (#6654)

Signed-off-by: ZhengWG <zwg0606@gmail.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [ea84055](https://github.com/vllm-project/vllm-omni/commit/ea84055507971c4a7f31d4efdba1488f50c264ae)

- **作者**: Anjie Hou
- **时间**: 2026-09-19T11:05:18Z
- **提交信息**: [Refactor][Diffusion] Resolve distributed layerwise topology in the plan (#7326)

Signed-off-by: specture724 <specture724@gmail.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

---
