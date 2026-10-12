# GitHub Stars 合并报告 - 2026-10-11

**合并日期**: 2026-10-12
**监控日期**: 2026-10-11
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


**报告日期**: 2026-10-12
**监控日期**: 2026-10-11
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2236
- **最后更新**: 2026-10-11T14:36:13Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-10-12
**监控日期**: 2026-10-11
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2897
- **最后更新**: 2026-10-11T19:48:43Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 2
- **主要提交者**: Yang Yong (雍洋), Chengtao Lv

## AI分析总结

## LightX2V 仓库昨日提交分析

### 1. 主要更新类型

本次 3 个提交涉及两种类型：**功能新增**（2个）和**性能/资源优化**（1个）。核心主题是为 LightX2V 框架新增对 Qwen-Image-2.1-Turbo 模型的支持，并降低实时视频生成的内存开销。

---

### 2. 关键变更点及与项目方向的关系

- **Qwen-Image-2.1-Turbo 模型支持（#1601, #1602）**：这是本次最重要的更新。先在通用平台上支持了该模型，随后紧接着适配了 MacBook MPS（Apple Silicon Metal Performance Shaders）后端。这表明项目在积极扩展支持的模型矩阵，同时重视跨平台覆盖（尤其是 Apple Silicon 用户群）。

- **realtimewam 内存优化（#1600）**：针对实时视频生成工作流中的内存占用进行降低。这直接呼应了项目名称 "LightX2V" 中的 "Light" 定位——让视频生成推理尽可能轻量化。

---

### 3. 对项目的影响和潜在意义

- **模型生态扩展**：持续接入新的图像/视频生成模型（如 Qwen 系列），增强了框架的实用性和社区吸引力。
- **硬件可及性提升**：MPS 支持意味着普通 Mac 用户（无需 NVIDIA GPU）也能使用 LightX2V 进行推理，大幅降低了使用门槛。
- **资源效率改善**：realtimewam 的内存优化使得在消费级硬件上运行实时视频生成更加可行，这对 "轻量推理框架" 的品牌定位至关重要。

---

### 4. 值得关注的技术点

- **多后端适配策略**：先上通用实现、再补 MPS 后端，这种渐进式平台适配模式表明项目具有良好的架构抽象，模型实现与后端计算解耦。
- **Qwen-Image-2.1-Turbo 的 "Turbo" 特性**：推测涉及蒸馏或量化加速技术，LightX2V 框架需要针对此类加速模型优化推理管线。
- **realtimewam 的内存优化**：实时视频生成通常对显存/内存极其敏感，降低内存开销可能涉及 KV cache 管理、张量生命周期优化或 offload 策略等手段。

---

### 5. 对项目发展方向的影响

结合 README 中 "Light Video Generation Inference Framework" 的定位，这组提交清晰地体现了项目的两大发展主线：

1. **广度**：不断扩展支持的模型种类（Qwen-Image-2.1-Turbo），使框架成为更多视频/图像生成模型的统一轻量推理入口。
2. **深度**：在硬件适配（MPS）和资源效率（内存优化）上持续打磨，确保 "Light" 名副其实。

两者共同指向一个目标：**让视频生成推理在尽可能多的硬件上、以尽可能低的资源消耗运行**，这对于推动视频生成技术从研究走向普惠应用具有重要意义。

## 详细提交记录

### [370878c](https://github.com/ModelTC/LightX2V/commit/370878c09dec0227f1a52fdfbfab73bd0bf7ba1a)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-10-11T19:48:38Z
- **提交信息**: Support qwen-image-2.1-turbo for macbook mps (#1602)

### [9f47d67](https://github.com/ModelTC/LightX2V/commit/9f47d6773f8c74b72f8be95cd5a855dc3286a193)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-10-11T19:21:53Z
- **提交信息**: Support Qwen-Image-2.1-Turbo (#1601)

### [7bd01b7](https://github.com/ModelTC/LightX2V/commit/7bd01b7d5d04bf99cdd9ca9082f20c184c66d991)

- **作者**: Chengtao Lv
- **时间**: 2026-10-11T13:51:54Z
- **提交信息**: reduce memory usage of realtimewam (#1600)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-10-12
**监控日期**: 2026-10-11
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2290
- **最后更新**: 2026-10-11T05:25:53Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-10-12
**监控日期**: 2026-10-11
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6590
- **最后更新**: 2026-10-11T21:45:45Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 2
- **主要提交者**: eigen, Cindy Zhang

## AI分析总结

# FlashInfer 昨日提交分析（共6笔）

## 1. 主要更新类型
- **性能优化（4笔，绝对主力）**：均为"Cake"系列GPU内核的调优与再导出，覆盖MLP、投影GEMM、MQA logits、Mamba2 SSD等场景。
- **CI修复（1笔）**：增强Nightly发布流水线的包一致性校验。
- **代码同步/杂项（1笔）**：MoE内核从上游Cake主分支重新渲染导出。

## 2. 关键变更点与项目方向的关系
- FlashInfer的核心定位是"高性能GPU推理内核库"，这批提交几乎全部服务于该目标，且高度集中在**SM100（B200）/SM103（GB300）新一代Blackwell架构**上：
  - **#6314**：MiniMax-H3 MLP的FC2 BF16收尾（epilogue）从8个warp减到4个，CTA从320线程缩到192，指令数降约13%，且输出**逐位相同**。
  - **#6335**：Kimi-K3 FP8投影GEMM第9轮调优，通过严格A/B测量冻结调度表（split-K、K=128/192 GEMM单元、TMA存储收尾等）。
  - **#6318**：DeepGEMM MQA logits引入按架构选择内核程序的机制（catalog v8）和"静态优先窗口"策略，小批量时避免动态调度的固定开销。
  - **#6330**：Mamba2 SSD第5轮优化，采用四槽环形收尾、TMA细粒度存储等，同时严格保证逐位一致。
- **#6283**：修复Nightly测试可能"静默回退到旧cubin缓存"的问题，确保测试真正覆盖当次构建产物——保障性能优化验证的可信度。
- **#6320**：MoE内核同步到上游Cake主分支的修复（INFO_VALID守卫等），属于常规的再生成导出。

## 3. 对项目的影响和潜在意义
- **持续压榨新硬件性能**：多个内核在生产形状上获得0.3%~16%不等的提升，强化了FlashInfer在B200/GB300推理场景的竞争力。
- **可复现的调优方法论**：#6335体现了"同GPU配对A/B、多次采样、≥2%增益门槛"的严格流程，调度表仅在两轮无新收益后冻结，增强了性能数据的可信度。
- **CI加固**：#6283防止了Nightly测试假阳性，让每日性能回归验证更加可靠，对一个以内核性能为核心的项目至关重要。

## 4. 值得关注的技术点
- **"逐位一致"作为硬约束**：性能改动绝不改变数值结果，便于安全替换，这对推理精度敏感场景是重要卖点。
- **按架构/形状分发**：catalog机制支持同一算子在SM100/SM103选择不同内核程序，甚至静态/动态调度按批量×上下文长度窗口切换。
- **warp级收尾优化**：MLP和SSD都通过减少spin-warp、TMA slab细分来隐藏存储延迟，是Blackwell上典型的细粒度调优手法。

## 5. 对项目发展的意义
结合README定位，这批提交表明FlashInfer正处于**Blackwell架构内核打磨的密集期**，且已形成"Cake上游生成→FlashInfer导出→逐位验证+严格A/B"的成熟工作流。配合CI加固，项目在保持数值正确性的前提下稳步提升新一代GPU推理性能，巩固其作为高性能推理内核库的领先地位。

## 详细提交记录

### [eec6ef1](https://github.com/flashinfer-ai/flashinfer/commit/eec6ef14082ca383fd11d108f79ebf2985516bea)

- **作者**: eigen
- **时间**: 2026-10-11T21:45:38Z
- **提交信息**: perf(cake_diffusion): MiniMax-H3 full MLP FC2 BF16 epilogue with 4 warps, bit-identical re-export (SM100 / SM103) (#6314)

## Summary

Re-export of the Cake MiniMax-H3 MLP kernel sources
(`csrc/cake_minimax_h3_mlp_sm100a.cu`,
`csrc/cake_minimax_h3_mlp_sm103a.cu`) for the BF16 / MXFP8 / NVFP4
operators `flashinfer.diffusion_ops.minimax_h3_mlp{,_mxfp8,_nvfp4}`
(follow-up to #6176). Python bindings, JIT spec and tests are unchanged.

- **FC2 BF16 epilogue 8 -> 4 warps.** The FC2 BF16 kernel drains its
256-column accumulator with 4 epilogue warps (two 128-column drains, the
full row drained before the epilogue-done arrive, split-K hand-off
counter re-armed after the stores). The CTA shrinks from 320 to 192
threads; the host-side thread constant follows. Executed warp
instructions drop ~13 % (spin warps 8 -> 4); the in-trace FC2 kernel
time is 0.3-0.4 % lower on B200 / B300 at the production shapes.
- **Bit-identical output.** Operator output, FC1 activations and the FC2
output compared as integer views against the previous kernel at M = 1 /
127 / 128 / 129 / 255 / 256 / 257 (P = 8), M = 4824 (P = 8) and the
production tiers on both architectures; identical tail-split decisions.
No tolerance, rounding point or precision change.
- **Norm/AdaLN kernels** spell their launch bound through the
generator's `THREADS` define (`__launch_bounds__(THREADS)` under
`#define THREADS 128`); same value, device code otherwise unchanged.
MXFP8 / NVFP4 GEMM kernels are unchanged.

## Validation

- JIT smoke of the three operators with `use_fast_math=False`,
stage-wise bit-exact against the Cake reference at M = 4824 / P 8, M =
257 / P 1 and M = 1 / P 8, on B200 (sm_100a) and B300 (sm_103a).
- `tests/diffusion_ops/test_minimax_h3_mlp.py`: 26 passed on B300; the
B200 run is in progress and will be noted here.
- `compute-sanitizer synccheck` clean for all three operators at M = 1
and the unaligned tail M = 257 on both architectures; `racecheck` clean
for the BF16 operator at M = 257 (the MXFP8 / NVFP4 operators hit a
sanitizer-internal error in the same reference path on the previous
sources as well).

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Performance**
* Updated BF16 model processing for supported hardware, including how
output values are accumulated and combined with gating and residual
inputs.
* Adjusted kernel execution settings for BF16 and quantized operations.
These changes do not alter public interfaces.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [23dc1d5](https://github.com/flashinfer-ai/flashinfer/commit/23dc1d5957558a04d03d5bc0003a09c0035ed776)

- **作者**: eigen
- **时间**: 2026-10-11T21:37:02Z
- **提交信息**: perf(cake_kimi_k3_fp8_projection): round 9 — cluster split-K re-association cells, K=128 / 192-wide GEMM cells, fused-shape re-tune, quant_done barrier (SM100a, SM103a) (#6335)

## Summary

Round 9 of the Cake `kimi_k3_fp8_projection` generated-program export
(FP8 block-scaled projection GEMMs of the Kimi-K3 KDA / MLA families —
22 families, 352 contract rows per GPU: 198 perf rows = 22 (N, K)
families × M in {1, 8, 64, 256, 512, 1024, 2048, 4096, 16384} and 154
correctness rows at M 3 / 129 / 513 / 1000 / 1023 / 1025 / 4097 with
strided views — on SM100 + SM103). It builds on the round-8 package on
FlashInfer main (`1f28b952d`, #6217) and changes the dispatch tables,
the kernel instances they select, the host mirror's reading of two new
table keys, and one kernel-side barrier (`quant_done`, below).

- **Dispatch-table convergence, exact.** Every runtime-selectable lever
was re-measured on every open contract row of both GPUs under paired
same-GPU A/B (shared-weight harness, A/A and no-op-twin controls, 3
alternating rounds × 1000 cold-L2 graph-replay samples), confirmed alone
on the node (quiet + two shared runs, controls within 1 %, gain >= 2 %),
and adopted per cell; the table was frozen only after two consecutive
clean full passes per GPU found no further gate-compliant win. Adoptions
per architecture (cells): SM103 — four cluster split-K cells (`1,28,256`
/ `1,28,512` / `1,28,1024` / `5,28,512`: csplit 6 / 8 / 6 / 3) plus
`5,28,256` csplit 3; the fused-shape re-tune of `1,28,2048` (STAGES 2,
XB_STAGES 2, QLANES 8, XBH 1) and the fused 6-knob form on `1,28,1024`;
23 GEMM cells from the K6 pass (gemm_bk 128 / gemm_pf / gemm_bn 192 per
cell) plus the two-stage / four-slot TMA-store epilogue (new keys
`gemm_stages 2` / `gemm_ts_slots 4`, also a K6-pass arm) on the 4
short-K cells `12,1,16384` / `24,2,16384` / `96,1,16384` / `96,1,4096`;
stream-K fix-up (`gemm_skf 1`) on `17,28,16384`, `96,28,4096`,
`386,28,1024` (`17,28,16384` later also gemm_bn 192 + gemm_bk 128 on top
of the fix-up); further K8-pass cells (`17,28,4096` gemm_bk 128,
`192,2,1024` gemm_bn 192 + gemm_bk 128, `24,2,16384` gemm_bk 128 on top
of the two-stage epilogue, `384,28,1024` gemm_bk 128, `12,1,4096`
gemm_bn 192 + gemm_bk 128, `24,2,4096` gemm_bn 192 + gemm_bk 128,
`386,28,2048` gemm_bk 128, `5,28,512` acc_bufs 2 + quant_units 2 +
epi_groups 2) — 41 cells with a new or changed lever in total. SM100 —
the same four cluster split-K cells (csplit 6 / 8 / 6 / 3) plus
`5,28,256` csplit 3; the two fused forms on `1,28,2048` / `1,28,1024` (+
epi_groups 2); 19 K6 GEMM cells (gemm_bk 128 / gemm_pf / gemm_bn 192)
plus the two-stage / four-slot TMA-store epilogue (`gemm_stages 2` /
`gemm_ts_slots 4`) on the 3 short-K cells `12,1,16384` / `96,1,16384` /
`96,1,4096`; `56,48,4096` gemm_sk 0 + gemm_skf 1; `96,28,4096` gemm_skf
1; `56,6,16384` / `56,6,4096` / `192,2,4096` / `192,2,16384` /
`56,48,2048` gemm_bk 128 and `96,1,4096` gemm_bk 128 on top of the
two-stage epilogue, `96,1,512` gemm_bn 192 + gemm_bk 128; `5,28,512`
epi_groups 2 — 36 cells with a new or changed lever in total.
- **Measured gains (R8-3 shared-run ratios, record / new):** cluster
split-K cells SM103 1.198 / 1.144 / 1.040 / 1.131 on `1,28,512` /
`1,28,1024` / `1,28,256` / `5,28,512` and 1.064–1.090 on `5,28,256`;
SM100 1.090 / 1.036 / 1.038 / 1.164 on the same four cells and
1.072–1.094 on `5,28,256`; `1,28,2048` fused re-tune 1.153–1.164 (SM103,
17.44 -> 14.24 us) and 1.156–1.161 (SM100, 17.6 -> 15.168 us); GEMM
cells 1.016–1.121 per cell (for example `96,1,16384` 1.121 / 1.119
(two-stage / four-slot epilogue), `96,1,512` 1.098, `12,1,4096`
1.076–1.092; the last two cells `56,48,2048` 131.74 -> 122.72 us and
`386,28,2048` 409.1 -> 401.632 us).
- **Kernel change (one):** a thread-executed `quant_done` named barrier
(15) in the fused + aliased cluster-exchange decode instances (the
quantization warps arrive after their last stage, the epilogue waits
after `mainloop_done`), gated on `fused && cs_alias`. The barrier adds
no arithmetic: the identity check shows the 69/69 + 68/68 dispatched
cubins unchanged and the fused + aliased instances differing only by the
barrier (+2 CUDA lines), the sealed parity finds every
non-re-association contract row bit-identical to the round-8 package,
and `compute-sanitizer --tool racecheck` now reports 0 hazards on these
instances on both GPUs (the aliased exchange had 46 WAW hazard groups
under racecheck before; SASS-to-op mapping had shown them ordered in
hardware by the MMA commit, which racecheck cannot see).
- **Host mirror:** `decode_table.py` grammar gains `gemm_stages` (2 | 3)
and `gemm_ts_slots` (1 | 4) on GEMM-route cells (symbol tokens `_s<n>` /
`_ts<n>`; kernel-key order
`gemm_tstore[_n192][_k128][_s<n>][_ts<n>][_sk|_skf<n>|_sks<n>][_pf<depth>]`),
`route_plan` prefers the tokened stems with the untokened fallback at
the same geometry; the mirror still refuses any table field it does not
read. Templates formatted with the repo's pinned ruff 0.12.8 (line
wrapping only).
- **Export protocol:** the exporter now samples the SM clock from a
spawned process during every timing window (200 ms samples) and starts a
shape's window only after 5 consecutive samples within 1 % (30 s cap; an
unstable precondition is recorded, never a gate); the measurement
identity carries the SM count and the NVML maximum clock; validity gates
unchanged (`source_over_export >= 0.94` median-based,
`directional_disagreement <= 0.08`, `endpoint_drift <= 0.02`; 3
counterbalanced groups × 2000 samples per arm, 8 captured graph
instances per arm, cold L2, CUPTI).
- **Package:** SM103 sealed export: 217 files, 9,526,590 bytes, combined
package hash `4c52de1353a947b8` (186 files under
`csrc/cake_kimi_k3_fp8_projection/`, 23 shared
`csrc/cake_device_helpers/`, 8 other files: the package Python modules,
README / docs, the test file, and `csrc/.clang-format` +
`csrc/README.md`; counts from the per-file hash lines of the parity
log). SM100 sealed export: the same 217 files, 9,526,590 bytes, combined
package hash `4c52de1353a947b8` — the file set and every per-file hash
are identical on both GPUs. The delivery patch against `1f28b952d`
touches 40 paths: 22 added, 6 modified (`README.md`, `cake_backend.py`,
`cake_jit.py`, `decode_table.py`,
`csrc/cake_kimi_k3_fp8_projection/cake_kimi_k3_fp8_projection_device_common.cuh`,
`tests/experimental/test_cake_kimi_k3_fp8_projection.py`) and 12 renamed
content-hashed program sources; 92 registry hashes over 184 `.cu` files,
0 unreferenced, 0 paths outside the owned directories.

## Exactness and parity

- Two kinds of adopted levers. **Bit-exact** levers (TMA-store / operand
hand-off / prefetch / pipeline depth / quantization width / TMEM
accumulator sets / epilogue groups / fused forms) leave every output
bit-identical to the round-8 package. **Re-association** levers (the
cluster split-K partition `csplit` and the stream-K fix-up `gemm_skf`)
change only the order in which exact FP32 partial sums are added; they
ship only where an exactness packet shows, on every touched row, that
each output element is bit-identical to the round-8 output or differs by
exactly 1 BF16 ulp (or, for a handful of tiny-magnitude outputs, by less
than one FP32 rounding unit of the exact dot product's magnitude scale,
2^-24 × Σ|a_k b_k|), that max |err| vs the FP64-accumulated dequantized
reference did not grow by more than 1 BF16 ulp at that element's
magnitude with the row's mean |err| within 1e-3 relative, and that eager
and CUDA-graph replay are bit-identical. UE8M0 block-FP8 recipe, FP32
accumulation of every product and BF16 output rounding are unchanged; no
approximate algorithm, no reduced-precision partials, no atomics.
- Rows that are no longer bit-identical to the round-8 package
(re-association cells): SM100 `1,28,256` (csplit 4 -> 6), `1,28,512` (4
-> 8), `1,28,1024` (4 -> 6), `5,28,512` (-> 3), `5,28,256` (2 -> 3),
`56,48,4096` (stream-K -> fix-up), `96,28,4096` (fix-up); SM103
`1,28,256` (4 -> 6), `1,28,512` (-> 8), `1,28,1024` (-> 6), `5,28,512`
(-> 3), `5,28,256` (2 -> 3), `17,28,16384`, `386,28,1024`, `96,28,4096`
(fix-up). Example packet (SM100 `96,28,4096`, `tp1:q_proj:4096`): 619 of
the row's elements differ from the round-8 output, 592 by exactly 1 BF16
ulp and 27 within the FP32-rounding bound; max |err| vs the FP64
reference 0.03122 -> 0.03122 (unchanged); mean |err| relative change
−2.2e-9; eager == graph replay. SM100 `5,28,256`: 17 elements differ per
row (14 at 1 ulp, 3 within the bound).
- **Bitwise checks on all 704 contract rows (352 per GPU)** — two
comparisons: (a) exported program vs Cake source, 353/353 receipts per
GPU; (b) round-9 output vs the round-8 package, 318 identical / 34
listed re-association rows per GPU. SM103 352/352 — 318 rows
bit-identical to the round-8 package, 34 rows differ and every one of
them is a listed re-association row (the 20 perf rows of the 8 SM103
cells above plus 14 of their correctness-shape variants); Cake source vs
exported program bitwise-identical on 353/353 receipts; delivered SM103
package 217 files, combined hash `4c52de1353a947b8`. On SM103 the 34
differing rows are a subset of the exporter's 54-row re-association
label list; the other 20 labelled rows are bit-identical (a changed
re-association form does not always change the BF16 output). SM100
352/352 — the same split: 318 rows bit-identical to the round-8 package,
34 rows differ and every one of them is a listed re-association row (the
18 perf rows of the 7 SM100 cells above plus 16 of their
correctness-shape variants); Cake source vs exported program
bitwise-identical on 353/353 receipts (the first run and the re-measured
row); the 34 differing rows are a subset of the exporter's 53-row
re-association label list, the other 19 labelled rows bit-identical;
combined package hash `4c52de1353a947b8` identical on both GPUs. 704
rows checked, 0 unlisted differences.

## Validation

- Sealed export receipts on this exact render (paired same-GPU
source-vs-export CUPTI timing, protocol above, plus bitwise parity and
zero-budget correctness on every row): SM103 353/353 receipts passed
(198 perf + 154 correctness + 1 coverage), 0 gate failures, 0
exceptions, 0 unstable-precondition rows, Cake<->FI bitwise ok 353/353;
source_over_export over the 353 rows min 0.9515, p05 0.995, geomean
1.0003 (gate 0.94, median-based); measured SM clock median 2070 MHz on
329 rows and 1537–2047 MHz on 24 rows (14 perf + 10 correctness) with M
>= 1000 of the fused_qkvg / in_proj_qkvgfab / o_proj / q_proj families;
`TARGET_REVISION` = FlashInfer `1f28b952d`. SM100 (first sealed run):
353 receipts, 352 passed, 1 validity refusal — `tp1_fused_qkvg_m16384`
failed the `endpoint_drift` gate (measured SM clock median 1402 MHz,
p10–p90 1380–1432 MHz, window spread 0.4808; export 3975.079 us,
source_over_export 1.0082; the Cake<->FI bitwise check passed on that
row; the row's receipt of record is the passing re-measure below, whose
correctness and bitwise checks are attested) — 0 exceptions, 0
unstable-precondition rows, Cake<->FI bitwise ok 353/353;
source_over_export over the 353 rows min 0.9404, p05 0.992, geomean
0.9997 (gate 0.94, median-based); measured SM clock median 1965 MHz on
314 rows and 1395–1958 MHz on 39 rows (25 perf + 14 correctness, all M
>= 512 of the fused_qkv_a / fused_qkvg / in_proj_qkvgfab / o_proj / q_b
/ q_proj families); `TARGET_REVISION` = FlashInfer `1f28b952d`. The
protocol re-measures an environment-validity refusal once:
`tp1_fused_qkvg_m16384` was re-measured once under that rule and passed
every gate (source_over_export 0.9998, directional_disagreement 0.0005,
endpoint_drift 0.0030 against the 0.02 gate; measured SM clock median
1372 MHz, p10–p90 1282–1425 MHz, window spread 0.6375 — the same
sustained-power operating point as the first measurement's 1402 MHz;
export 3971.485 us; Cake<->FI bitwise identical before and after; the
dispatched kernels `gemm_tstore` + `quant:u4` are the round-8 forms).
The SM100 receipt set of record is the composition first run + that
re-measure: 353/353 passed, 0 gate failures, 0 exceptions, 0
unstable-precondition rows, Cake<->FI bitwise ok 353/353;
source_over_export over the 353 rows min 0.9404, p05 0.992, geomean
0.9996; the re-association label list of the re-measure round is
identical to the first run's (53 rows).
- `tests/experimental/test_cake_kimi_k3_fp8_projection.py` on this
render: 74 passed on GB300 and 74 passed on B200 inside the seed
deliveries (before the first sealed measurement); on the sealed
deliveries: SM103 green (rc 0 inside the sealed export); SM100 green on
the first sealed run's delivery (rc 0) and again in the re-measure round
(rc 0). `ruff format --check` + `ruff check` (repo config, ruff 0.12.8):
"All checks passed!" on the 3 templates and the 4 delivered Python files
— in the seed deliveries on both GPUs and on the final sealed delivery
(one package, identical on both GPUs).
- Paired same-GPU no-regression check vs the round-8 kernel of record on
both GPUs (198 timed rows, 44-row shards × 3 alternating rounds, A,B,A,B
per-kernel isolation of every row below 0.98): SM103 geomean 1.0221 (198
rows, lowest shard reading 0.9620), SM100 geomean 1.0180 (198 rows,
lowest 0.9450). The 3 + 3 rows that read below 0.98 in the sharded runs
were re-measured alone: on SM103 `tp8:kv_b:256`, `tp1:f_b:512`,
`tp8:kv_b:1024` (identical kernels and identical table cells in both
renders) timed 5.76 / 9.28 / 8.93 us for record and new in all four A/B
probes each (ratio 1.000; timer-quantum artefact of three shards sharing
one node); on SM100 `tp8:kv_b:256` and `tp8:kv_b:512` likewise 5.95 and
6.69 us ×4 (1.000), and the 1.1-ms `tp1:o_proj:16384` row (same kernel,
no explicit table cell in either render) read 1101.68 / 1126.46 /
1112.89 / 1107.84 us A,B,A,B = 0.991 by medians, inside that row's own
0.982–1.018 A/A spread. After attribution: 0 rows below 0.98 on either
GPU, geomean above 1.00 on both.
- Versus the fastest FP8 chain that produced a timing in the measurement
container (FI CUTLASS groupwise, FI TRT-LLM groupwise, cuTile groupwise,
FI DeepGEMM grouped; DeepGEMM ue8m0 on GB300) on FlashInfer main
`1f28b952d`, CUDA-graph replay, CUPTI kernel time, one process per peer,
measurement container `nvcr.io/nvidia/sglang:26.07-py3`: SM103 — 198/198
perf rows timed, geomean 2.2648 vs the fastest chain that produced a
timing on each row, minimum 1.040 (`tp1_in_proj_qkvgfab_m1` vs FI
TRT-LLM groupwise), 0 rows below 1.00×. Per peer: FI CUTLASS groupwise
198/198 rows (geomean 2.489, min 1.081); FI TRT-LLM groupwise 180/198
(geomean 3.578, min 1.040; the 18 `f_b` rows refuse with `ValueError:
a.shape[1] must be >= 256 in TRTLLM`); cuTile groupwise 72/198 (geomean
2.251, min 1.167; the other configurations fail with
`TileCompilerExecutionError: Return code 5`, as in round 8); FI DeepGEMM
grouped 0/198 (`ValueError: cubin not registered:
kernel.fp8_m_grouped_gemm.<id>` on every row); DeepGEMM ue8m0 0/198
(`RuntimeError: interpreter INTERNAL ASSERT FAILED at
".../torch/include/c10/core/impl/PyObjectSlot.h":30, please report a bug
to PyTorch. cannot access PyObject for Tensor - no interpreter set` on
every row) — the two DeepGEMM chains are unmeasurable in this container,
unchanged from round 8. SM100 — 198/198 perf rows timed, geomean 2.2513
vs the fastest chain that produced a timing on each row, minimum 1.024
(`tp1_in_proj_qkvgfab_m8` vs FI TRT-LLM groupwise), 0 rows below 1.00×.
Per peer: FI CUTLASS groupwise 198/198 rows (geomean 2.472, min 1.067);
FI TRT-LLM groupwise 180/198 (geomean 3.537, min 1.024; the same 18
`f_b` rows refuse with `ValueError: a.shape[1] must be >= 256 in
TRTLLM`); cuTile groupwise 72/198 (geomean 2.197, min 1.170; 12 families
× M in {1, 8, 64, 256, 4096, 16384}, the other configurations fail with
`TileCompilerExecutionError: Return code 5`); FI DeepGEMM grouped 0/198
(`ValueError: cubin not registered: kernel.fp8_m_grouped_gemm.<id>` on
every row); the DeepGEMM ue8m0 chain is not a peer on SM100. Both GPUs:
every perf row above 1.00× the fastest complete chain (minimum 1.040
SM103 / 1.024 SM100).
- `compute-sanitizer` synccheck + racecheck on every kernel instance new
since the round-8 package: 0 errors / 0 hazards on every adoption tip's
touched rows on both GPUs (46 rows SM103 / 40 rows SM100 at the first
combined tip, every later cell re-run); final render: synccheck +
racecheck 0 errors on the rows of the last adopted cells on both GPUs.
- Roofline fraction (per-row floor = max(bytes / 8 TB/s, FLOPs / 4500
TFLOPS) + the measured launch ramp, 3.680 us GB300 / 4.064 us B200; and
the same floor with the compute term scaled to the SM clock measured
during the row): SM103 geomean fraction 1.665 (round-8 receipts, same
ramp) -> 1.626 nominal / 1.666 clock-normalized over the 198 perf rows
(the measured clock, 2070 MHz on most rows, is above the 1807 MHz
implied by the 4500 TFLOPS peak, so the clock-normalized floor is the
tighter one); 4 rows within 1.10× of the clock-normalized floor
(`tp8_f_b_m1` 1.071, `tp8_f_b_m8` 1.070, `tp1_fused_qkvg_m16384` 1.092,
`tp1_in_proj_qkvgfab_m16384` 1.092). SM100 geomean fraction 1.688
(round-8 receipts, same ramp) -> 1.665 nominal / 1.650 clock-normalized
over the 198 perf rows (rows measured at 1965 MHz sit above the 1856 MHz
implied by the 4500 TFLOPS peak for 148 SMs and get the tighter
clock-normalized floor; the large-M rows measured below it under
sustained power, down to 1372 MHz, get a looser one, so the net
clock-normalized geomean lands slightly below nominal); 5 rows within
1.10× of the clock-normalized floor (`tp8_f_b_m1` 1.002, `tp8_f_b_m8`
1.032, `tp8_f_b_m64` 1.042, `tp8_kv_b_m1` 1.089, `tp8_kv_b_m8` 1.094);
the two M=16384 fused rows that are within 1.10× on SM103 read 1.143 /
1.179 on SM100 (measured at 1372 / 1402 MHz).
- Host launcher per-call path unchanged in this round.

## Checklist

- [x] ruff 0.12.8 `format --check` + `check` clean on the 3 templates
and the 4 delivered Python files (seed deliveries on both GPUs and the
final sealed delivery: "All checks passed!")
- [x] `tests/experimental/test_cake_kimi_k3_fp8_projection.py` green on
SM100 and SM103 on the delivered package (SM103: rc 0 in the sealed
export; SM100: rc 0 in the first sealed run and rc 0 in the re-measure
round)
- [x] Sealed export receipt summaries + 704-row bitwise parity reported
in this description (SM103 353 receipts + parity PASS; SM100 353
receipts of the composed set — first run + one re-measure — + parity
PASS; the per-row tables and the evidence manifest are kept with the
Cake-side delivery record)
- [ ] `/bot run` + `run-ci` label cycled after every push (first cycle
started at PR creation; results are recorded in the PR thread as they
land)
- [x] Tracker #4254 bullet after #6217 (`- #6335`, added at PR creation)

🤖 Generated with [Claude Code](https://claude.com/claude-code)

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [adae683](https://github.com/flashinfer-ai/flashinfer/commit/adae6837f1962a5790162be0ee45e014659cbbf8)

- **作者**: eigen
- **时间**: 2026-10-11T21:28:04Z
- **提交信息**: perf(cake_deepgemm): per-architecture 64-head FP8 dense texts, static-preferred windows and two new paged geometries (SM100a, SM103a) (#6318)

## Summary

Re-export of the `deepgemm_dense_mqa` family (dense 32-head and 64-head
FP8 / FP4 MQA logits, paged FP8 MQA logits) from the producer tip of the
convergence round against the stock DeepGEMM kernels (`fp8_mqa_logits` /
`fp8_paged_mqa_logits`, sgl-deep-gemm 0.2.0). Catalog schema
`dense_mqa.v7` -> `dense_mqa.v8`.

### `deepgemm_dense_mqa`

1. **64-head FP8 dense logits -- production text chosen per
architecture.** On SM100a the accumulator is a two-stage TMEM ring (the
next row's MMA fills the second stage while the math roles drain the
first); on SM103a the MMA and math roles wait on the producer's
source-side barriers. The one-split short-KV text is shared. The catalog
therefore binds a stage's program per architecture (`stages = [[stage,
{arch: program}], ...]`); `dense_mqa.stage_program(stage, arch)` /
`program_names(route, arch=...)` resolve the device's program, the
catalog checker requires every delivered (program, architecture) pair to
be routed, and only the device's programs are built. Routing, admission
(`dense_admission`: every 64-head route admitted on both architectures)
and the `:short` rule are unchanged.
2. **Paged FP8 MQA logits -- static-preferred windows.** New policy key
`policy.paged.dynamic_scheduler.static_windows[arch][static_route] =
[[max_batch, max_context_len], ...]` (`null` = unbounded). Inside a
window the static program serves a batch the dynamic-scheduler route
would otherwise take: at these sizes the request set is a handful of
chunks and the dynamic program's fixed costs (persistent grid, claim
chain, pool locate) exceed its balance gain. `paged_route_name(...,
batch=, max_context_len=, arch=)` applies the rule; without
`max_context_len` / `arch` it keeps the pre-v8 batch rule. Windows (both
architectures unless noted): 64 heads x page 64 x next_n 1 -- (1,
163840), (4, 41216), (16, 30208), (64, 3072 on SM100a / 6912 on SM103a);
next_n 2 -- (1, 131072), (4, 125696), (16, 10752), (64, 3840).
3. **Two new paged geometries.** 32 heads x page 64 x next_n 2 and 64
heads x page 32 x next_n 2, each with a static and a dynamic-scheduler
program (`paged:fp8:h32:p64:n2[:dyn]`, `paged:fp8:h64:p32:n2[:dyn]`);
the 32-head page-64 and 64-head page-32 next_n 1 routes are unchanged.
4. **Paged admission tables** rewritten from the measured tables on both
architectures (`(max_batch, max_context_len)` rules, `null` = unbounded,
admitted when some rule holds. SM100a: 64 heads x page 64 x next_n 1
static (16, null), (512, 170496), (null, 32768) and dynamic (128, null),
(256, 170240), (null, 32768); next_n 2 static (16, null), (64, 32768),
(512, 42752), (null, 8192), dynamic unbounded; the page-32 / 32-head
next_n 1 routes keep (16, null), (null, 32768) static and (128, null),
(null, 32768) dynamic. SM103a: 64 heads x page 64 x next_n 1 static (64,
null), (128, 32768), (512, 170496), (null, 8192) and dynamic (128,
null), (256, 170240), (null, 32768); next_n 2 static (16, null), (64,
32768), (512, 170496), (null, 8192), dynamic unbounded; the page-32 /
32-head next_n 1 routes keep (64, null), (128, 32768), (null, 8192)
static and (128, null), (null, 32768) dynamic. The two new next_n 2
geometries are delivered and validated by the export but admitted only
where a table clears: the 32-head page-64 dynamic route on SM103a at
batch <= 152 and context <= 32768; every other new route is withheld
(empty rule list) until its table clears).

Provenance: generated from the producer tip `37d2cbee7` against
FlashInfer `9df2bfe23`; 34 programs (28 before: 8 new single-text
programs, 2 removed -- the previous shared 64-head full / partial
production texts) (the 26 unchanged programs keep byte-identical sources
and their compiled `.text` is byte-identical to the previous export on
both architectures).

## Test plan

- Export protocol on both architectures (bitwise source / export parity
per shape, identical per-call kernel count, paired CUPTI timing of the
FlashInfer plan against the production launcher): 92 / 92 shapes per
architecture (70 dense + 22 paged) pass -- every shape validates against
the dequantised reference, source / export logits are bitwise identical
and the per-call launch count matches; the FlashInfer plan's paired time
against the production launcher (source / export) is 0.95-1.11 (geomean
1.018) on SM100a and 0.91-1.11 (geomean 1.017) on SM103a; the frozen
protocol lock is byte-identical across the two architectures.
- `tests/experimental/test_dense_mqa_admission.py`,
`tests/experimental/test_dense_mqa_generated.py`,
`tests/experimental/test_paged_mqa_generated.py`,
`tests/experimental/test_cake_dsa_indexer.py` on both architectures:
admission 27, dense 63, paged 16, DSA indexer 164 passed on each
architecture.
- Paired CUPTI acceptance tables at the producer tip (9 ABBA sessions
per row with an identical-text control per arm, pinned DeepGEMM 0.2.0
baseline): dense 64-head family 54 rows per architecture -- SM100a 52 /
54 rows clear their paired floor (geomean 1.053, min 1.014, no row below
1.00), SM103a 52 / 54 (geomean 1.064, min 1.012); the two rows outside
on each architecture are the 32-head coverage shapes that the catalog
routes to the stock kernel; paged family 256 rows per architecture --
SM103a 249 / 256 rows clear under the paired rule (geomean 1.237, min
1.014, no row below 1.00; 4 rows served by the stock kernel count as
1.00, 3 rows read above 1.00 inside their noise floor), SM100a 237 / 256
(geomean 1.240, min 0.989; 10 rows served by the stock kernel count as
1.00, 7 rows read above 1.00 inside their noise floor -- one of them
clears on a second-GPU confirmation -- and the 2 rows at batch 256 x
128k context with next_n 2 read below 1.00 (0.991 / 0.989 on the table,
0.990 / 0.997 on the second-GPU confirmation); the large-batch
128k-context rows on SM100a -- next_n 2 at batch 256, next_n 4 at batch
256 / 512 and at batch = SM count -- are not converged).

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Paged MQA route selection now accounts for the target architecture and
maximum context length, choosing static routes within configured windows
and dynamic routes otherwise.
* Expanded paged FP8 route coverage for additional head counts, page
sizes, and KV configurations, including more architecture-specific
options.
* Dense MQA plans now select stage programs supported by the chosen
architecture, with clearer feedback when a program is unavailable.
* Program listings can now be filtered by architecture, while unfiltered
listings include programs across architectures.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [36fd768](https://github.com/flashinfer-ai/flashinfer/commit/36fd76859292ac2ac5aebd0892fc64715569b9da)

- **作者**: eigen
- **时间**: 2026-10-11T21:18:41Z
- **提交信息**: perf(cake_ssd_combined): exact-scan epilogue ring + calibrated schedule-variant rule (SM100 / SM103) (#6330)

## Summary
Fifth performance round of the Cake Mamba2 SSD combined prefill
(`flashinfer.mamba.SSDCombined(backend="cake")` and its Cake-only
functional wrapper `flashinfer.mamba.ssd_combined_fwd`), SM100 (B200)
and SM103 (GB300). Exact arithmetic is preserved: every kernel change is
a schedule / data-movement / issue-order change that is bitwise
identical to the previous release on the 9-shape bitwise set (partial
chunks, D per head and per head x dim, packed varlen, three state
dtypes), the 3 multi-work-item shapes and the 5 sub-chunk shapes on both
archs; no FTZ / rounding / accumulation-order change; the two host rules
below are calibrated from measurements only.

- **Exact scan — epilogue ring (six regenerated device sources
`exact_<state>_<mode>`)**: the epilogue warps store each 128-row output
stage as four per-warp 32-row TMA slabs with per-warp bulk-group waits
(the `out_map` TMA box shrinks from 128 to 32 rows); the output stage
runs through a four-slot ring whose z-gate loads for the next group are
issued inside the current group's body, ahead of that group's arithmetic
and stores; the D row is staged in shared memory once per work item; the
next work item's initial state is prefetched into L2 during the current
item's last chunk (no registers); and the kernel's control region moves
to the tail of dynamic shared memory (231,808 B instead of 232,448 B).
Kernel-level scan time vs the previous release (CUPTI kernel-only, cold
L2, two separately compiled copies per arm, all-pairs verdict, 3
interleaved rounds, noise floor ≤ 0.35 %): SM103 improves v1x128 /
v8x128 / v64x128 / v1x1024 / v4x2048 / b1x1024 / b4x1024 / b1x32768z /
v2p96_160z (b1x32768z 0.842, v2p96_160z 0.954), v2x64z stays inside the
band (1.003–1.004) and v8x64z is 1.022–1.023 slower; SM100 improves
v1x128 / v8x128 / v64x128 / v1x1024 / v4x2048 / b1x1024 / b1x32768z /
v2x64z / v2p96_160z (b1x32768z 0.854, v2p96_160z 0.961), b4x1024 stays
inside the band (0.998) and v8x64z is 1.006–1.008 slower. Single-copy
readings of the same programs on the multi-item and sub-chunk geometries
(SM103 / SM100, new/previous): v8x128z 0.917 / 0.915, v8x128 0.928 /
0.934, v64x128 0.911 / 0.926, v64x64 0.988 / 0.981, v8x64 0.993 / 0.991,
v64x64z 1.002 / 1.002, v8x64z 1.011 / 1.005.

- **Schedule-variant rule + `_noring` programs**: the one geometry where
the ring loses — packed varlen with z, sequences of exactly 64 tokens
(two one-chunk work items per 128-token chunk) at ≥ 2 sequences x 128
heads — and the batch-2 no-z 25–90-token batched cell run the previous
schedule, exported through the same front door as six
`exact_<state>_<mode>_noring` programs (the same kernel built with
`epilogue_ring=False`; bitwise identical to the previous release on 17
shapes on both archs; 232,448 B SMEM; its device code differs from the
previous release only in that the output stage goes out as four 32-row
slabs through the family's shared `out_map` box — scan time 0.999–1.003
/ 0.999–1.005 of the previous release on 11 calibration cells, SM103 /
SM100). `_exact_scan_variant` decides from host-known quantities only
(mode, has_z, nheads, state dtype, sequence count, total tokens, batch,
seqlen; no per-sequence lengths and no device synchronisation, so
prepared / captured shapes keep their program): varlen → `_noring` iff
has_z and num_sequences x nheads ≥ {bf16, f16: 2 x 128; f32: 4 x 128}
and 63 x num_sequences < total_tokens < 65 x num_sequences; batched →
`_noring` iff not has_z and batch == 2 and 25 < seqlen < 90; otherwise
the ring program. The windows were calibrated at kernel level on 84 + 28
+ 27 cells per arch (ring / previous scan-kernel ratio, 3 interleaved
rounds: uniform 63- and 65-token sequences win on both archs, uniform 64
and the pair-sum-128 mixtures lose; batch-2 no-z 50–75-token calls lose
or tie on at least one arch (+0.0…+0.8 %, at or just beyond the band),
25 and 90 win; batch 1 / 3 / 4 / 8 and every z batched cell win) and the
varlen item threshold at FI level on the 64-token window (1–4 sequences
x 64 tokens x {bf16, f32} state, z + initial states, 5 interleaved
rounds: the bf16 2 x 64 cell loses 1.011–1.018 on SM103 in four gates
(two 3-round 93-row gates, the 5-round focus run and the 5-round window
gate) and ties on SM100 at 0.997–1.001; the f32 2 x 64 and 3 x 64 cells
win or tie on both archs, 0.974–1.003). The only benchmark row whose
program changes under the final threshold is the 2-sequence x 64-token
bf16-state Nemotron-H row; it reads 1.000 vs the previous release on
both archs afterwards (5 interleaved rounds), with the f32 twin at 1.010
/ 1.018 and the two control rows inside their bands.

- **Chunk-parallel program**: device sources unchanged (re-exported with
new content identities only). `_CHUNK_PARALLEL_COST_MODEL_US` re-fitted
against the delivered exact-scan program (24 (batch, nheads, nchunks)
cells x 3 interleaved rounds per arch, forced chunk-parallel vs forced
exact scan, CUPTI main-kernel medians, cold L2, least squares in the
unchanged model form, 1.05 selection margin): SM100 serial 4.69 → 4.99
µs + 2.594..2.809 → 2.556..2.758 µs per chunk, chunk-parallel 25.2 →
25.0 µs + 0.0493 → 0.0491 µs per tile; SM103 4.33 → 4.72 + 2.395..2.51 →
2.345..2.432, 24.3 → 24.1 + 0.0432 → 0.0429 (no constant moves by more
than 9 %). No routing decision changes on the 24 calibration cells or on
the 93 benchmark rows on either arch; the Cake code generator's copy
carries the same constants. The worst absolute fit error is 20.7 %
(SM103) / 22.1 % (SM100), against 19.8 % / 19.5 % for the previous fit,
on the shortest 8-head cells (1 x 8 heads x 4 chunks 20.7 / 22.1 %, 1 x
8 x 8 19.0 / 14.7 %, SM103 / SM100) where the fixed chunk-parallel term
over-predicts the chunk-parallel time; the three cells where the rule
and the measurement disagree (1 x 8 heads x 8 chunks, 1 x 16 x 8, 4 x 8
x 16) are the previous release's disagreements plus 1 x 16 x 8 on SM103
(SM100 already listed it), all inside the fitted margin or on the
exact-scan side of it.

- **Measured and not shipped** (every variant bitwise-exact where it had
to be; each rejected by paired A/B on time on both archs, except where a
measured register spill or a loss on one arch's production rows ended
the form first): a single-pass chained chunk-parallel scan
(ticket-ordered segments, L2 release/acquire flags, f32 state hand-off,
no grid barrier) is 1.12–1.77x slower on 7 of 8 chunk-parallel shapes; a
two-chunk Horner aggregation of the phase-2 recurrence reproduces the
current program's fp64 per-token outlier / worst-ulp / max-abs metrics
on all 37 compared tensors (the gate's formal verdict is FAIL for the
current program and the candidate alike, on an inherited ≤-CuTe
worst-ulp clause on one cancellation-dominated row per arch) but is
1.09–1.19x slower on every chunk-parallel benchmark row on SM103 and
slower on all 8 kernel-level shapes on both archs; a family of twelve
phase-2 prefetch / double-buffer / pairing forms ends slower on the
chunk-parallel rows or spills registers; in-CTA fusion of the segment
preprocess into the scan (typed round-to-nearest scalar ops, bitwise
with the two-kernel path on every set) is slower on 7 of 8 kernel shapes
and on 11–12 of 14 benchmark rows; six pre_inter / pre_intra
re-schedulings, a TMEM-quadrant warp-role rebalance, a fully-masked
column-block skip, a per-item state prefetch into registers, a wider
persistent-grid balancing rule and a driver-API cubin-launcher flag were
rejected the same way; porting the slab store into the chunk-parallel
epilogue loses 0.7–2.6 % on the 1024-token shapes on both archs and is
not shipped.

## Measurements
Paired interleaved CUPTI call-span timing (`bench_gpu_time`, cold L2:
the GPU span of one call from its first to its last kernel, including
the inter-kernel launch gap; the incumbent, CuTe and stock Triton arms
are measured over the same span of their own calls), new and incumbent
arms in separate processes on the same device with no other work on the
node, 3 interleaved rounds per arch (5 on the focused re-gates), stock
Triton reference in its own process. Incumbent = the previous release of
this backend (FlashInfer main at the start of this work); CuTe = the
CuTe-DSL SSD kernels in this repo; new/incumbent is accepted when ≥ 1.00
− the row's A/A band (per-row twin / round-to-round band). Rows per
arch: 93 = 50 fixed benchmark rows (this backend's correctness_* /
perf_* shape set, 'contract rows' below), 34 Nemotron-H-geometry rows
(17 bf16-state, 17 f32-state, incl. unaligned lengths and packed
mixtures), 7 sub-chunk rows (< 128 tokens) and the 2 chunk-parallel
cells added in the previous release (1 x 2048 x 32 heads, 4 x 2048 x 8
heads). The SM100 gate runs the seven chunk-parallel-routed rows first
in each process (see the row-order note below the table); the row order
is otherwise the shape-set order. Ratios in the tables are incumbent (or
CuTe / stock Triton) time divided by new time: > 1 means the new program
is faster. Kernel-level ratios quoted in prose ("scan kernel", the
Summary's per-shape numbers) are new time divided by previous-release
time: < 1 means faster.

| arch | class | rows | incumbent measured | new/incumbent min (row) |
new/incumbent geomean | rows in A/A band | vs CuTe min / geomean (rows)
| vs stock Triton min / geomean (rows) |
|---|---|---|---|---|---|---|---|---|
| SM100 (B200) | contract rows (correctness_* / perf_*) | 50 | 50 |
0.995 (perf_batched_1x4) | 1.024 | 2 | 2.092 / 3.198 (50) | 2.935 /
11.985 (50) |
| SM100 (B200) | Nemotron-H rows, bf16 state | 17 | 17 | 1.000
(nem_v64_64_bfloat16) | 1.077 | 0 | 2.172 / 3.028 (14) | 4.004 / 8.299
(17) |
| SM100 (B200) | Nemotron-H rows, f32 state | 17 | 17 | 1.000
(nem_v8x64_float32) | 1.086 | 1 | - / - (0) | 3.818 / 8.243 (17) |
| SM100 (B200) | sub-chunk rows (< 128 tokens) | 7 | 7 | 0.996
(short_batched_2x50) | 1.016 | 1 | - / - (0) | 21.632 / 26.426 (6) |
| SM100 (B200) | chunk-parallel cells | 2 | 2 | 1.001 (cp_b1h32c16) |
1.003 | 0 | 2.887 / 2.958 (2) | 8.446 / 8.446 (1) |
| SM100 (B200) | all rows | 93 | 93 | 0.995 (perf_batched_1x4) | 1.043 |
4 | 2.092 / 3.154 (66) | 2.935 / 10.950 (91) |
| SM103 (GB300) | contract rows (correctness_* / perf_*) | 50 | 50 |
0.991 (perf_batched_1x4) | 1.026 | 3 | 2.349 / 3.598 (50) | 3.247 /
12.442 (50) |
| SM103 (GB300) | Nemotron-H rows, bf16 state | 17 | 17 | 0.998
(nem_v8x64_bfloat16) | 1.076 | 2 | 2.391 / 3.611 (14) | 8.442 / 13.964
(17) |
| SM103 (GB300) | Nemotron-H rows, f32 state | 17 | 17 | 1.000
(nem_v8x64_float32) | 1.083 | 0 | - / - (0) | 5.433 / 9.743 (17) |
| SM103 (GB300) | sub-chunk rows (< 128 tokens) | 7 | 7 | 0.987
(short_batched_2x50) | 1.021 | 2 | - / - (0) | 23.090 / 26.388 (6) |
| SM103 (GB300) | chunk-parallel cells | 2 | 2 | 0.999 (cp_b4h8c16) |
1.002 | 1 | 3.181 / 3.264 (2) | 9.874 / 9.874 (1) |
| SM103 (GB300) | all rows | 93 | 93 | 0.987 (short_batched_2x50) |
1.044 | 8 | 2.349 / 3.590 (66) | 3.247 / 12.730 (91) |

SM100: 4 rows inside the A/A band (nem_v8x64_float32 1.000 with band
0.005; perf_batched_1x4 0.995 with band 0.007; perf_batched_4x64 0.999
with band 0.005; short_batched_2x50 0.996 with band 0.005), 0 below it,
0 without an incumbent measurement.
SM103: 8 rows inside the A/A band (cp_b4h8c16 0.999 with band 0.010;
nem_v64_64_bfloat16 0.999 with band 0.013; nem_v8x64_bfloat16 0.998 with
band 0.005; perf_batched_1x256 0.999 with band 0.005; perf_batched_1x4
0.991 with band 0.025; perf_batched_4x64 0.997 with band 0.005;
short_batched_2x50 0.987 with band 0.026; short_varlen_64_60 0.998 with
band 0.019), 0 below it, 0 without an incumbent measurement.
Band convention: the per-row band is the same run's twin-copy /
round-to-round A/A band. Checked on the raw ratios against the per-row
bands pre-registered at the start of this work, 92 of 93 rows on each
arch also clear that stricter reading; the two exceptions are SM100
perf_batched_1x4 (0.9948 against 0.9950 under its 0.005 pre-registered
band; its same-run band is 0.007) and SM103 short_batched_2x50 (0.987
against 0.988 under its 0.012 pre-registered band), whose scan and
preprocess kernels read 1.000 in the final gate and in both 5-round
re-tests that include the row (1.002 and 0.998).

Earlier readings on the same device programs (disclosed; not the
acceptance tables): the first 93-row gates of the delivered launcher
configuration, run before the item-threshold revision and in the
shape-set order on both archs, read SM103 FAIL=2 and SM100 FAIL=7.
SM103: nem_v64_64_bfloat16 0.987 — the 2 x 64-token bf16-state cell that
the state-dtype-aware threshold now routes to `_noring`; it reads 0.999
(scan kernel 1.000) in the final gate above and 1.000 in a 5-round
re-gate; short_batched_2x50 0.987 — the two 5-round re-tests read 1.002
and 0.998; the 3-round final gate reads 0.987 again, inside that run's
own 0.026 A/A band (0.010 in the first gate), with the scan kernel at
1.000–1.003 and the preprocess kernel at 1.000 in every run — the
residual sits on the host / launch-gap side of a 19 µs call, not in the
kernels. SM100: the seven chunk-parallel-routed rows (cp_b1h32c16,
cp_b4h8c16, perf_batched_1x16 / 1x64 / 1x256 / 4x16 / 4x64) read
0.971–0.995 in three gates where they ran after the exact-scan rows of
their process (all seven rows below their band in two of them, five in
the third), and 0.999–1.005 (93 rows, the table above) / 0.998–1.001
(11-row gate) when they run first; the chunk-parallel device program is
byte-identical in both arms (the six generated sources are pure renames,
0 insertions / 0 deletions) and SM103 shows no such effect, so the
difference is the process history of the measurement (allocator /
placement vs thermal not separated), not the delivered programs.

Saturated rows and the 1 x 32768 row (chunk-parallel selected):

| arch | row | new Cake µs | incumbent µs | CuTe µs | stock Triton µs |
new/incumbent | A/A band |
|---|---|---|---|---|---|---|---|
| SM100 | perf_batched_256x16 | 658.4 | 661.3 | 1506.4 | 4326.2 | 1.004
| 0.044 |
| SM100 | perf_varlen_128x32 | 733.5 | 766.3 | 1672.1 | 6451.0 | 1.045 |
0.005 |
| SM100 | perf_batched_1x256 | 136.0 | 136.1 | 1697.7 | 431.2 | 1.000 |
0.005 |
| SM103 | perf_batched_256x16 | 581.0 | 595.6 | 1436.5 | 3978.9 | 1.025
| 0.005 |
| SM103 | perf_varlen_128x32 | 675.6 | 715.6 | 1591.5 | 5885.1 | 1.059 |
0.005 |
| SM103 | perf_batched_1x256 | 129.1 | 128.9 | 1626.3 | 426.9 | 0.999 |
0.005 |

The per-row gains concentrate where this round's changes act: the
many-item one-chunk Nemotron-H rows (scan kernel 0.86–0.92 of the
previous release on both archs: next-item initial-state prefetch plus
the slab store), the saturated rows (perf_batched_256x16 /
perf_varlen_128x32 scan kernel 0.974 / 0.942 on SM103 and 0.995 / 0.956
on SM100) and the one-wave rows (perf_batched_1x1 / 16x1 scan kernel
0.963 / 0.965 on SM103 and 0.954 / 0.964 on SM100); the
chunk-parallel-routed rows run the unchanged chunk-parallel program in
both arms and read 0.999–1.005 on SM100 (run first in each process; scan
kernel 0.993–1.001) and 0.997–1.030 on SM103 (scan kernel 0.973–1.004).

Roofline on the delivered programs (bounds from the SKU peak rates at
the device-reported SM count and clock; scan-kernel medians from the
paired gate's per-kernel split): the saturated rows run at 58.5 % / 65.5
% on SM100 and 63.8 % / 74.6 % on SM103 (perf_varlen_128x32 /
perf_batched_256x16, scan kernel) of their 415 µs HBM bound while
issuing 0.98x of the compulsory DRAM bytes (ncu DRAM read + write bytes
against the unique tensor bytes of the call), so the remaining gap is
dependency latency, not traffic: the per-tile period of the busiest role
decomposes into instruction-attributed dependency latencies (issue,
exposed shared-memory / MUFU / TMEM-load / ALU hops, tcgen05 issue and
MMA) for 53–61 % of the period and into SMSP issue contention between
the co-scheduled consumer roles for another 26–33 %, the critical loop
being the B/C loader's C@B^T issue → cb_full → pre_intra path
(co-critical with pre_inter's publish → prescale → INTER1 → update loop
on the varlen row); the single-chunk chain of an 8-CTA calibration cell
measures 4653 / 4779 cycles per tile (SM103 / SM100) for the batched
cell, and the packed-varlen row's chain carries a further 919 / 998
cycles (the varlen term derived from the 8-head varlen rows); the
saturated rows sit at 86–93 % of their own chain times their 224 tiles
per SM (perf_batched_256x16 90.4 / 86.0 %, perf_varlen_128x32 92.6 /
92.8 %, SM103 / SM100). The 1 x 32768 x 8 chunk-parallel row's scan
kernel is at 19.7 % / 21.0 % (SM100 / SM103) of its 25.7 µs HBM bound;
it issues 2.28–2.31x the compulsory DRAM bytes (the S/H workspace round
trip of its three-phase structure) and its phase-2 recurrence step takes
258 / 257 cycles against a 93-cycle issue floor — the single-pass and
look-back restructurings that would remove the round trip or shorten the
chain were built and measured, and lose (Summary). The unsaturated
multi-chunk row perf_batched_16x16 is at 51.6 % / 54.7 % (SM100 / SM103)
of its 26 µs HBM bound and at 85.1 % / 83.0 % of its chain floor of 16
chunks x the calibration chain plus the measured fixed term. One-wave
rows (8–128 tiles) stay latency-bound at 1–19 % of a sub-2 µs bound: the
fixed per-call term of the 1 x 128 row splits into launch 1.8–1.9 µs,
first-chunk fill 3.7–4.0 µs (prologue, metadata → first TMA, TMA
landing, C@B^T, prescale → INTER1 — the first chunk's own dependency
chain) and drain 1.5–1.6 µs of epilogue compute plus 0.5–0.6 µs of store
completion; the slab store adopted here is the drain-side lever, and no
fill-side candidate survived its A/B. By class on the final gates (scan
kernel, SM103 / SM100; % of the SKU bound, then % of the
calibration-chain floor): saturated 22 rows 30.5–74.6 / 27.9–67.7 % of
bound and 49.4–94.5 / 49.3–93.2 % of floor; non-saturated multi-chunk 33
rows 2.3–54.7 / 2.3–51.6 % and 57.8–473.9 / 59.3–478.9 % (above 100 %
are the four chunk-parallel-routed perf_batched rows 1x16 / 1x64 / 1x256
/ 4x64, whose program beats the serial exact-scan chain, and the two 1 x
2048 varlen Nemotron-H rows at 100–102 %); one-chunk 29 rows 1.4–49.2 /
1.4–45.3 % and 34.0–77.8 / 35.5–87.3 %; the 5 chunk-parallel-routed
contract rows against their own three-phase floor 7.8–22.4 / 7.2–21.0 %
and 42.6–61.2 / 40.1–57.6 %; sub-chunk 7 rows 2.5–20.4 / 2.5–20.9 % and
54.9–83.2 / 56.6–89.9 % (the five chunk-parallel-routed perf_batched
rows appear in both the multi-chunk class, against the serial chain, and
the chunk-parallel class, against their own floor; the two cp_* cells
have no floor row).

## Validation

- Bitwise sets vs the previous release on SM100 and SM103: the six ring
programs are identical on the 9-shape set, the 3 multi-work-item shapes
and the 5 sub-chunk shapes (17 / 17 per arch); the six `_noring`
programs are identical on the same 17 shapes; the chunk-parallel device
sources are unchanged. 20 repeated launches of 7 z / packed-varlen /
multi-work-item shapes produce one output hash per shape, equal to the
previous release, for the ring programs and for the `_noring` programs
on both archs.
- FI-path bitwise dump comparison of the previous release against this
head through the FlashInfer front door (the 50 contract shapes + 7
sub-chunk shapes, plus the 17-shape kernel-level sets), same Cake tree
and GPU, both archs: PASS — SM100 and SM103 each 57/57 identical on the
front-door set and 17/17 identical on the kernel-level sets (outputs and
final states `torch.equal`, 0 arm errors).

- `pytest tests/mamba/test_cake_ssd_combined.py
tests/mamba/test_cake_ssd_combined_capture.py` on this exact FI head
(re-run after the formatting-only commit): SM100 (B200) 435 passed, 2
skipped; SM103 (GB300) 435 passed, 2 skipped. The parent commit (same
device sources and loader, item threshold not yet state-dtype aware)
passed 426 / 2 on both archs; the 9 added tests are 9 new state-dtype
cells of `_VARIANT_CASES` (33 → 42 cases: kernel-level calibration cells
plus the FI-level 64-token-window cells);
`test_source_exact_scan_variant_programs` and the shipped-sources count
test (19 device files = 6 ring + 6 `_noring` + 6 chunk-parallel + 1
preprocess) were already part of the parent commit's 426.
- The shipped device sources and host templates are byte-identical to
the Cake export of the delivered Cake revision (identity re-run on both
SM100 and SM103 hosts after the last Cake commit); the FI loader tables
and the Cake export profiles name the same module identities.
- compute-sanitizer, run as separate bounded commands per tool:
`synccheck` 0 errors on both archs for the ring programs (registered
exact-scan launcher, 4 benchmark shapes: batched, packed varlen with a
non-aligned boundary and z, int64 seq_idx, 1 x 32768) and for the
`_noring` programs (direct driver, 4 z / f32 / packed / multi shapes).
`racecheck` reports the same population of records on the previous
release and on the delivered programs (hazard-mode counts, previous
release vs `_noring`, on the 2 x 1024 z shape: GB300 195872 vs 195875,
B200 195867 vs 195864; in analysis mode on SM103 the ring programs show
the same single site class at shifted offsets — 30 records vs 35 for the
previous release and 36 for `_noring`, per kernel 6 / 11 / 13 vs 6 / 12
/ 17 and 6 / 11 / 19; 0 records on one-chunk shapes): every record is a
write-after-read pair on the two-stage delta / cumsum staging ring whose
ordering goes reads → `bar.sync` → elected `mbarrier.arrive` (release) →
loader `try_wait.parity` (acquire) → stores, a happens-before chain
through mbarriers that racecheck does not follow; this PR adds no record
class or kind and no site outside that staging ring. (The Cake
repository's registered racecheck gate had reported 0 because its worker
exits without a device synchronize, so the tool never emitted its
analysis; the same registered function with a synchronize before exit
shows the same 12 records on the previous release — a tool follow-up,
not a kernel change.)
- The Cake repository's GPU test slice for this kernel (`-k mamba_ssd`,
78 tests) passes on both archs on the tree carrying the delivered device
programs and on the tree merged forward onto Cake main at the
merge-forward check (the later main delta is documentation-only; merges
cleanly, no GPU re-run required); its two benchmark-regression checks
pass on both archs (exact_scan 0.0443 / 0.0483 ms and chunk_parallel
0.1706 / 0.1602 ms GPU time, SM100 / SM103, measured on the same tree).
- sglang route tests (GB200, inside the sglang Nemotron-H test
environment, FlashInfer at the commit that introduced the item threshold
— this head minus the formatting-only commit — and, in the first run, at
the commit before it): CPU 47 passed and GPU 42 passed in both
environments.
- Nemotron-H-8B-Reasoning-128K BF16 TP1 end-to-end (sglang, GB200,
FlashInfer at the commit before the item-threshold revision — identical
device sources and loader except the item-threshold constant): both arms
(stock vs Cake SSD prefill) NaN-free on short prompts (1–127 tokens),
prefix-hit extend (P = 128–1024) and GSM8K-200 (0 non-finite logprobs
beyond sglang's conventional position-0 None; 0 nan/inf server-log
lines; 0 exceptions); GSM8K accuracy 0.885 in both arms; per-question
flips 3 each way (118 / 200 identical answers, 76 same verdict with
different text); the cross-arm probe table (short prompts, prefix-hit
extends, 8 fixed prompts 7/8 same text, 1024-token input probe) is
value-for-value identical to the two previous rounds' runs, as expected
for bitwise schedule changes. Re-run at this exact head: GSM8K 0.890
(stock) / 0.885 (Cake SSD prefill); 0 nan/inf server-log lines and 0
exceptions in both arms; route line `Cake kernel selected` 1 / fallback
0; per-question flips 4 stock-correct / Cake-wrong and 3 Cake-correct /
stock-wrong (127 / 200 identical answers); the cross-arm probe table is
value-for-value identical to the first run. The stock arm moved 0.885 →
0.890 between the two runs (sglang batching nondeterminism on its Triton
path) while the Cake arm read 0.885 in both.

## Launch contract and resources

The exact-scan ring programs request 231,808 B of dynamic shared memory
per CTA (the kernel's control region moved from the prefix to the tail
of the allocation; 640 B below the previous 232,448 B), the `_noring`
programs and the chunk-parallel programs keep 232,448 B (the standard
opt-in ceiling of SM100 / SM103) — `_EXACT_SMEM_BYTES` /
`_EXACT_NORING_SMEM_BYTES` / `_CHUNKPAR_SMEM_BYTES` in the loader,
`SMEM_TOTAL` in the generated sources. The exact-scan host template's
`out_map` TMA box is 64 x 1 x 32 x 1 (was 128 rows): the ring programs
store per-warp 32-row slabs and the `_noring` programs store their
128-row stage as four slabs from warp 0's elected thread. Everything
else in the previous release's contract is unchanged: 512 threads per
CTA with the same per-role register budgets (`setmaxnreg` 24 / 112 / 168
/ 208; 128 registers, 0 spills, 0 stack, 11 named barriers measured on
the ring programs), a full `cta_group::1` TMEM allocation (one CTA per
SM), the same persistent grid-size rule, an ordinary non-cooperative
launch with no cluster dimensions, the chunk-parallel family's software
grid barrier, `FLASHINFER_CAKE_SSD_CHUNK_PARALLEL=never` to disable that
family, and the prepared / captured submission API
(`CakeSSDCombined.prepare` / replay): the schedule variant is chosen
when the workspace is materialized, so a prepared or captured call keeps
its program. 19 device sources ship (6 ring, 6 `_noring`, 6
chunk-parallel, 1 preprocess) with the two host templates.

## CI
`@flashinfer-bot run tests/mamba/test_cake_ssd_combined.py
tests/mamba/test_cake_ssd_combined_capture.py`
`/bot run`

---

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [65c38d2](https://github.com/flashinfer-ai/flashinfer/commit/65c38d2a502493bfb01b9cc3af4be8dc13f0f1a8)

- **作者**: Cindy Zhang
- **时间**: 2026-10-11T09:38:48Z
- **提交信息**: fix(ci): validate nightly kernel packages (#6283)

<!-- .github/pull_request_template.md -->

## 📌 Description

This PR adds an explicit package-consistency check to the Nightly
Release test workflow.

Nightly installs the newly built `flashinfer-python`,
`flashinfer-cubin`, and JIT-cache wheels before running package tests.
If an incompatible `flashinfer-cubin` wheel is installed, FlashInfer may
ignore it and fall back to the shared cubin cache. This could
allow Nightly tests to pass without exercising the cubins produced by
the current workflow.

The new validation runs after package installation and before
`show-config` and package tests. It verifies that
  - `flashinfer-python` and `flashinfer-cubin` versions match exactly.
- `flashinfer-jit-cache` matches the Python package version, allowing
its CUDA local-version suffix.
  - Installed JIT-cache providers match the JIT-cache shim version.
- The selected `FLASHINFER_CUBIN_DIR` is the directory provided by the
installed `flashinfer-cubin` wheel, rather than a fallback cache.

The validator is read-only. It does not download artifacts, modify
installed packages, or remove existing caches. A mismatch causes the
Nightly test job to fail before package tests begin.

  Regression tests cover:

  - A valid, matching package set.
  - A stale `flashinfer-cubin` version.
  - Selection of a fallback cubin cache.
  - A mismatched JIT-cache shim.
  - A mismatched JIT-cache provider.


## 🔍 Related Issues

- Related to #5886
- Follow-up to #5892
- Fix #6281

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
Please focus on whether the validation should remain a separate script
or be implemented directly in the Nightly test entry point, and whether
the package-version checks are appropriately strict for Nightly builds.

The selected cubin-directory assertion is intentionally strict: Nightly
package tests should exercise the flashinfer-cubin wheel built by the
current workflow and must not silently pass using an existing fallback
cache.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

## Summary

* **Bug Fixes**
* Nightly package tests now check that required FlashInfer packages are
installed and that package versions and the selected cubin directory are
consistent.
* The tests report mismatches between the Python package, cubin package,
JIT cache, and JIT-cache providers.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [ddff5f6](https://github.com/flashinfer-ai/flashinfer/commit/ddff5f686d065e8d140092e6ff6e277d34786943)

- **作者**: eigen
- **时间**: 2026-10-11T07:11:15Z
- **提交信息**: chore(cake_fused_moe): re-render the Kimi-K3 MXFP4 SiTU MoE export (cake, cake_cute) from the merged Cake main revision (#6320)

## Summary

Follow-up to #6154 (merged as `34bb66e4d0b`): re-renders the two
Cake-exported Kimi-K3 W4A8 MXFP4 SiTU routed-MoE backends
(`flashinfer/fused_moe/cake_mxfp4_situ_moe/` for `backend="cake"` and
`cake_cute_mxfp4_situ_moe/` for `backend="cake_cute"`) from the Cake
revision that landed the mixed192 chain on the Cake main branch,
`9316cbf49bd21548735f2d9720f2375b883a5c69`, by the exporter's single
render command, so both manifests pin a main-branch producer revision
(previously the candidate-branch revision `70198066696`). Export +
evidence only: no FlashInfer runtime code outside the two generated
packages changes, `.pre-commit-config.yaml` is untouched.

What changes in the generated sources versus the merged `70198066696`
export (every module paired on (role, route.form), file names and
identity namespaces normalised):

- All 107 cake + 95 cake_cute host bindings are identical modulo the
hash-derived module name / shim namespace; the 202 arg plans, launch
descriptors, compile flags and TMA ABIs are unchanged; PDL
`griddepcontrol` placement is identical in all 202 modules.
- `cake_cute`: 65 device sources identical. The 30 swap-AB forms
(`gemm1_swapab_situ` x10, `gemm2_swapab_finalize` x14,
`gemm2_swapab_partial` x6) wrap their first-/next-record metadata loads
(`meta_alpha`; also `cur_tok` / `cur_scale` in the n8 / n16 / n32 GEMM2
forms) in `if info[3] != 0` (the record's `INFO_VALID` flag, Cake main's
A-K kernel pattern that reached the candidate when main was merged). The
guarded statements are unchanged; for valid records the loaded values
and the compute are the same, for records with `INFO_VALID == 0` the
loads are skipped.
- `cake`: the same 30 forms carry the same guard. In addition all 107
device sources differ only by Cake main's CUDA emitter cleanups:
`__launch_bounds__(N)` -> `__launch_bounds__(THREADS)` with `THREADS`
defined to the same N (107/107 checked), literal shared-memory offsets
-> the pre-existing `SMEM_*_OFF` macros whose values equal the previous
literals (107/107 checked), blank lines.

Module file names and identity namespaces (content hash,
`cake_host_shim_<hash>`) move because the identity hash covers these
sources and Cake's IR repr gained fields. The guarded kernels are the
ones re-validated on the merged tree before this render (see Evidence):
acceptance 91/91 rows per backend, paired CUPTI 51/51 rows >= 1.0 per
backend, GPU e2e and sanitizer gates.

## Evidence (B300, sm_103a)

- Render identity: `verify --flashinfer --revision 9316cbf49bd` clean (0
differences) after `ship-apply`; 202 launcher modules verified (107 cake
+ 95 cake_cute); plan parity 3168 token counts per backend. This render
is byte-identical to the cand-r14 candidate render (404/404 files) and
source-identical modulo hash to the cand-r9 / cand-r11 candidate renders
(202/202 modules paired, 0 differ) on which the merged-tree
re-validation below ran. The diff against the merged `70198066696`
export is exactly the Summary above (manifest-paired, hash-normalised
comparison over all 202 module pairs).
- Merged-tree re-validation of these kernels on isolated B300 nodes
(cand-r9 `f869c7a22d9`, same sources modulo hash): contract acceptance
91/91 rows correct per backend (0 failed, 0 N/A, baseline 0 failed);
paired graph-replay CUPTI 51/51 rows >= 1.0x trtllm-gen per backend,
geomean 1.2491 (cake) / 1.2432 (cake_cute), within 1 percent of the
`70198066696` receipts on 50/51 and 51/51 rows; CUDA-graph capture +
replay T = 1..16 and 2-stream concurrency gates 12/12 records passed on
three candidate revisions; compute-sanitizer synccheck + memcheck on the
11 registered gemm2 swap-AB launchers 22/22 clean summaries on three
candidate revisions. A full 54-launcher synccheck + memcheck sweep on
`9316cbf49bd` is running and will be reported in a comment.
- FlashInfer host tests: 58 passed / 0 failed, both packages (58
skipped: rows that need sm_103a and the package kernels, plus the
`split_two_stage` / `hybrid` rows that run as GPU chain tests);
FlashInfer GPU tests (both packages, incl. the executable-path
gate-oracle rows of every chain): 98 passed / 0 failed in 367 s (52 rows
per package; 9 skipped per package: 6 reference-wrapper comparisons
because the installed FlashInfer does not expose the hand-written MXFP4
wrapper, 3 `split_two_stage` / `hybrid` rows that execute as GPU chain
tests at this revision) on one B300.
- Cake-side gates on the pinned revision: full `kimi_k3_mxfp4_situ` GPU
e2e slice 59 passed / 0 failed (B300, step `0ecc2e1c`); analysis-layer +
family unit set 201 passed / 0 failed; the row-group dense GEMM2 form's
e2e slice 2 passed / 0 failed (both routes agree with the reference in
the same error class) and its compute-sanitizer synccheck + memcheck
both `ERROR SUMMARY: 0 errors`.
- Contract `eval_contract_kimi_k3_mxfp4_situ_cute_dsl_moe` v29 is
ratified at `9316cbf49bd` on the Cake side with the receipts above (the
`70198066696` receipts of #6154 plus the merged-tree re-runs); the
timing tables are not re-measured on this render by the rule fixed
before the results were read (sources identical modulo hash to the
re-validated candidate).
- Tracker: #4254.

## Test plan

- [x] `verify` render identity on the shipped tree
- [x] `pytest tests/moe/test_cake_mxfp4_situ_moe*.py` (host + GPU) on
B300
- [ ] CI (`/bot run`)

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

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-10-12
**监控日期**: 2026-10-11
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4586
- **最后更新**: 2026-10-11T16:38:50Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-10-12
**监控日期**: 2026-10-11
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34702
- **最后更新**: 2026-10-11T22:27:26Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Lucas Ruan

## AI分析总结

## 仓库提交分析：huggingface/diffusers（单批记录）

> 说明：本次分析仅基于所提供的 1 条提交记录及 README 背景摘要，无法交叉验证具体代码变更内容，以下判断以提交标题语义与项目定位为依据。

### 1. 主要更新类型
- **Bug 修复为主，兼具结构性整理**：提交标题 "Fix Anima text encoder exports and standalone core denoising" 中的 "Fix" 明确指向缺陷修复。
- 修复对象分为两部分：**文本编码器的导出（exports）问题**，以及**核心去噪逻辑的独立可用性（standalone core denoising）**。
- 后者带有一定**重构/解耦**性质，即把去噪主流程从对特定模型或管线的隐式依赖中剥离出来。

### 2. 关键变更点与项目方向的关系
- diffusers 的核心定位是提供统一、模块化的扩散模型构建块（scheduler、unet/transformer、text encoder、pipeline）。**文本编码器导出修复**直接服务于组件化原则——确保任意模型组件都能被正确序列化、共享与跨框架复用，这与 HuggingFace 生态强调的"可移植、可分享"理念一致。
- **Standalone core denoising** 意味着去噪步骤可脱离完整 pipeline 独立调用，契合项目持续推动的"低层级 API 暴露"路线：让用户能自定义循环、插入控制（如 ControlNet、Guidance）、做研究实验，而不必复制粘贴 pipeline 源码。
- "Anima" 指向某一具体模型/社区实现，反映项目对第三方模型适配与社区贡献的持续接纳（PR 编号 #14943 也印证了这是社区驱动的修复）。

### 3. 对项目的影响和潜在意义
- **直接收益**：修复导出问题能消除用户在保存/加载该模型文本编码器时遇到的运行时错误或权重错配，降低使用门槛。
- **间接收益**：核心去噪逻辑解耦后，便于后续新增调度器、采样技巧或新架构时复用同一路径，减少重复代码与回归风险。
- **风险面**：涉及"核心"去噪路径的改动若测试覆盖不足，可能影响依赖该内部实现的多条 pipeline，因此通常需要较完整的回归测试与版本说明。

### 4. 值得关注的技术点
- **导出语义**：需关注是 `save_pretrained`/`from_pretrained` 的 state_dict 键名不一致、配置类注册缺失，还是序列化时对象引用未正确解包——这类问题在新增模型适配中最常见。
- **Standalone 化的边界**：观察是否引入了新的公共函数/类（如独立的去噪步骤接口），这决定了它是一次性修补还是可扩展 API 的起点。
- **兼容性策略**：修复是否保留旧调用路径的回退，对下游第三方库（如 ComfyUI、InvokeAI 等常复用 diffusers 内部实现的项目）影响较大。

### 5. 结合 README 背景对项目发展的影响
- README 体现项目遵循 Apache 2.0、由 HuggingFace 团队维护、强调开源协作与合规分发。上述提交正体现了这一运作模式：**社区通过 PR 报告并修复特定模型适配问题，维护者合入后使生态覆盖面扩大**。
- 从发展脉络看，这类提交累积的效果是：扩散模型组件的**标准化程度**不断提高（每个模型都能正确导出），同时**底层与高层 API 的分层**日益清晰（core denoising 可独立使用）。这两点共同支撑 diffusers 成为研究原型到生产部署之间的稳定中间层。
- 长期而言，这种"修小洞、松耦合"的维护节奏虽不如新功能显眼，却是项目保持向后兼容、吸引第三方贡献、避免代码腐化的关键，对一个已被大量下游依赖的基础库而言，其价值往往高于单次功能新增。

**小结**：该提交是一次针对特定模型适配与核心去噪解耦的维护性修复，体现了 diffusers 持续强化组件标准化与 API 分层的长期方向。

## 详细提交记录

### [e1a6c67](https://github.com/huggingface/diffusers/commit/e1a6c67dc724e7c1a5ae8eb0c1964c9f47325217)

- **作者**: Lucas Ruan
- **时间**: 2026-10-11T21:41:19Z
- **提交信息**: Fix Anima text encoder exports and standalone core denoising (#14943)

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-10-12
**监控日期**: 2026-10-11
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


**报告日期**: 2026-10-12
**监控日期**: 2026-10-11
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13220
- **最后更新**: 2026-10-12T01:00:37Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-10-12
**监控日期**: 2026-10-11
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 37003
- **最后更新**: 2026-10-12T01:06:21Z

## 提交统计

- **昨日提交总数**: 24
- **提交者数量**: 10
- **主要提交者**: FeiHong Guo, Ziyi Xu, Shuwen Wang

## AI分析总结

# SGLang 昨日提交分析（共 24 条）

## 1. 主要更新类型

- **功能新增/重构**：DSpark 投机解码子系统的大规模重构（占 7 条提交，近 30%）；KV Events 事件系统增强；扩散模型（Diffusion）多项功能
- **Bug 修复**：约 7 条，涵盖 DP 路由、HiCache、VLM 资源泄漏、KV 事件回放、NIXL 数据拷贝等
- **性能优化**：采样器排序优化、MLA/Mamba 主机池共享初始化、扩散模型视频编码路径优化
- **配置/兼容性**：默认 Flash Attention 版本选择、FP8 量化支持

## 2. 关键变更点及与项目方向的关系

**DSpark 投机解码子系统（最大主题）**：新增 `MarkovSampleStep` 统一算子接口，将 Markov 草稿步骤的加法和 token 选择合并为单个操作；所有 Markov 头统一通过单一步骤接口执行；草稿 TP 同步合并至 `dspark-draft`；支持 `SGLANG_SIMULATE_ACC_LEN` 内联接受逻辑；新增贪心草稿（argmax 一次性接受）模式。这一系列重构使投机解码路径更加模块化和高效，直接服务于项目"快速推理"的核心目标。

**KV Events 事件系统**：发布 LoRA 适配器名称和命名空间化块哈希，修复回放时缺失事件主题的问题，提升了 KV 缓存事件追踪的完整性和可观测性。

**统一 Radix 树与 Mamba 集成**：惰性 Mamba 检查点失效修复、Mamba 主机池从设备缓冲区信息构建，强化了对混合架构模型的支持。

**调度器增强**：DP 转换后的解码批次保持为运行批次、混合步骤中 KV 池不足时回退解码行、健康检查不干扰用户请求路由——这些均提升了多副本推理的调度稳定性。

## 3. 对项目的影响和潜在意义

- **投机解码性能飞跃**：DSpark 的重构将 Markov 采样从多步骤分散逻辑合并为统一算子和统一图尾执行，减少了图间开销和同步开销，可能显著提升投机解码的接受率和吞吐量
- **多模态/扩散模型生态扩展**：Pi0.5 FP8 量化、LTX 视频编码优化、VSA-H3 选择修复，表明 SGLang 正加速向视觉-语言-动作（VLA）和扩散模型推理场景覆盖
- **生产可靠性提升**：HiCache 存储工作线程异常存活、DP 健康检查隔离、VMM 租约清理修复等，增强了长时间运行的服务稳定性

## 4. 值得关注的技术点

- **`MarkovSampleStep` 的算子化设计**：将草稿采样的数学运算封装为单个 CUDA 算子，减少 kernel launch 开销
- **`SGLANG_DSPARK_USE_GREEDY_DRAFT`**：支持 argmax 草稿作为 one-hot 接受，在确定性场景下简化投机路径
- **`SGLANG_DSPARK_FOLDED_SAMPLING` 的删除**：说明 Markov 采样已原生集成到草稿图尾，不再需要折叠优化——架构简化
- **DeepSeek-V4.1 `hc_mix` 统计 kernel 调整为 `num_stages=1`**：流水线深度调整，暗示内存压力与性能的权衡
- **扩散模型中 Claude Opus 5.5 参与协作**：反映了 AI 辅助开发在复杂推理系统中的实际应用

## 5. 对项目发展的影响

SGLang 以"LLM 和多模态模型的快速推理"为定位，本次提交集中体现了三条发展主线：（1）通过 DSpark 投机解码架构持续压低端到端延迟；（2）通过 KV Events 和统一 Radix 树强化异构推理后端（NIXL、Mamba、LoRA）的统一管理能力；（3）通过扩散模型和 VLM 修复加速多模态推理生态布局。这些变更共同强化了 SGLang 作为统一、高性能推理引擎的竞争力，特别是在投机解码和多模态扩展这两个推理效率的关键前沿上。

## 详细提交记录

### [e607293](https://github.com/sgl-project/sglang/commit/e6072935bfa1036d4e20e8ed042ce1ff09872f57)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-11T22:33:24Z
- **提交信息**: [DSpark] Apply `SGLANG_SIMULATE_ACC_LEN` inside the accept instead of switching paths (#43623)

### [a65b776](https://github.com/sgl-project/sglang/commit/a65b776963d3e9139a82ac38fced030d0bbb6acf)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-11T22:18:59Z
- **提交信息**: [DSpark] Add `SGLANG_DSPARK_USE_GREEDY_DRAFT`, an argmax draft accepted as one-hot (#43670)

### [3cc23b3](https://github.com/sgl-project/sglang/commit/3cc23b3b86c2f1583a316a8466c853e89aced06f)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-11T22:17:47Z
- **提交信息**: [DSpark] Merge the draft TP sync sites into `dspark-draft` (#43669)

### [00ba90f](https://github.com/sgl-project/sglang/commit/00ba90fd1a5023bad829ae0263b15f4e2eedc6ba)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-11T22:15:59Z
- **提交信息**: [DSpark] Run the same markov block in the draft graph tail; drop `SGLANG_DSPARK_FOLDED_SAMPLING` (#43668)

### [48abbdb](https://github.com/sgl-project/sglang/commit/48abbdb845e1872813fc978f10be77a8b817831c)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-11T22:13:02Z
- **提交信息**: [DSpark] Draft the eager markov block through `MarkovSampleStep` (#43622)

### [467209e](https://github.com/sgl-project/sglang/commit/467209e838926c398bdde45fe1fffde0ded1684f)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-11T22:10:58Z
- **提交信息**: [DSpark] Add `MarkovSampleStep`, one op for a markov draft step's add and token pick (#43621)

### [9943cf8](https://github.com/sgl-project/sglang/commit/9943cf8eeffc625bb50df88a913d97cab901190e)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-11T22:07:51Z
- **提交信息**: [DSpark] Run every markov head through one step interface (#43620)

### [d62b9c2](https://github.com/sgl-project/sglang/commit/d62b9c2480f3b4b2ff16344c90e6a73e4b1d09fa)

- **作者**: Banruo Liu
- **时间**: 2026-10-11T15:23:30Z
- **提交信息**: [KV Events] Publish LoRA adapter names and namespaced block hashes (#42455)

Signed-off-by: Banruo Liu <lichangxinlivingshade@gmail.com>
Co-authored-by: Shangming Cai <csmthu@gmail.com>

### [97bfa5c](https://github.com/sgl-project/sglang/commit/97bfa5cc53fa38053374cb3d662c9fdb0008c925)

- **作者**: Mick
- **时间**: 2026-10-11T15:05:25Z
- **提交信息**: [diffusion] fix: select VSA-H3 for FastH3 when no transformer backend is given (#43690)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [46a97e5](https://github.com/sgl-project/sglang/commit/46a97e55400d871ba05537f21ed603321801da2d)

- **作者**: Ke Bao
- **时间**: 2026-10-11T14:39:14Z
- **提交信息**: Preserve serialized page dtype in NIXL copy fallback (#43593)

### [b0a75c8](https://github.com/sgl-project/sglang/commit/b0a75c819612e96657bc82e8f4befea99ccefe83)

- **作者**: Ke Bao
- **时间**: 2026-10-11T14:36:29Z
- **提交信息**: Share MLA host capacity initialization (#43595)

### [c938b6e](https://github.com/sgl-project/sglang/commit/c938b6e454903cd740ba59d6af96527fa9a3e045)

- **作者**: Ke Bao
- **时间**: 2026-10-11T14:35:52Z
- **提交信息**: Build Mamba host pools from device buffer infos (#43596)

### [ef3e5c8](https://github.com/sgl-project/sglang/commit/ef3e5c83c5255690abe2bafb08a128beaed1edc6)

- **作者**: Shuwen Wang
- **时间**: 2026-10-11T14:26:56Z
- **提交信息**: [HiCache] Keep storage workers alive on backend exceptions (#43550)

### [11bfd86](https://github.com/sgl-project/sglang/commit/11bfd868ac36c0d5c7089c3f1a65ed575feb5540)

- **作者**: Mick
- **时间**: 2026-10-11T13:15:49Z
- **提交信息**: [diffusion] perf: encode LTX video/audio through the shared bounded MP4 path (#43656)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [0923bcd](https://github.com/sgl-project/sglang/commit/0923bcd258b41aa9a5a6b4ee10cfa5229f71cfc0)

- **作者**: Shuwen Wang
- **时间**: 2026-10-11T13:12:51Z
- **提交信息**: [Unified Radix] Invalidate lazy Mamba checkpoints before in-place tracking (#43567)

### [cf88ed4](https://github.com/sgl-project/sglang/commit/cf88ed4352c74e34d960171859ef2242157e734d)

- **作者**: FeiHong Guo
- **时间**: 2026-10-11T13:08:55Z
- **提交信息**: [BugFix][DP] Prevent health checks from perturbing user request routing (#35721)

Signed-off-by: Phoenix3334 <Phoenix3334@users.noreply.github.com>

### [d26b6a5](https://github.com/sgl-project/sglang/commit/d26b6a5a9c4752e2ad0309df66eaca2f33816d68)

- **作者**: Shuwen Wang
- **时间**: 2026-10-11T12:57:42Z
- **提交信息**: fix: default Inkling to fa4 on Hopper (#35292)

### [586d98c](https://github.com/sgl-project/sglang/commit/586d98cc156145e28a575ce9225545f761435160)

- **作者**: trebladev
- **时间**: 2026-10-11T12:55:59Z
- **提交信息**: [Diffusion] Add ModelOpt FP8 checkpoint quantization for Pi0.5 (#43062)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [04f7405](https://github.com/sgl-project/sglang/commit/04f740580c69f2d00aee1df950773a041984c30f)

- **作者**: Mick
- **时间**: 2026-10-11T11:13:39Z
- **提交信息**: [VLM] fix: repair multimodal VMM lease cleanup and source-stream ordering (#43475)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [efd14cf](https://github.com/sgl-project/sglang/commit/efd14cfb66a316cd1e028d179947a4dcedd5ef41)

- **作者**: Ziyi Xu
- **时间**: 2026-10-11T11:03:19Z
- **提交信息**: [DeepSeek-V4.1] Use num_stages=1 for the hc_mix stats partial kernel (#43070)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Yuan Luo <4908075+yuan-luo@users.noreply.github.com>

### [53295c6](https://github.com/sgl-project/sglang/commit/53295c697255a5e8ddb263f98ab7e047e2700ad2)

- **作者**: Sage
- **时间**: 2026-10-11T09:25:43Z
- **提交信息**: [kvevents] fix missing topics in replayed kv events (#43386)

Signed-off-by: Sage Ahrac <sagiahrak@gmail.com>

### [0a21a3b](https://github.com/sgl-project/sglang/commit/0a21a3b79839d6c85b84811f5d859252ac416234)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-11T08:23:51Z
- **提交信息**: [Scheduler] Keep a DP-converted decode batch as the running batch (#43283)

### [4165222](https://github.com/sgl-project/sglang/commit/41652225d0e52cbbad63ffd7f052ac19806b027a)

- **作者**: jiaqiang-dot-liu
- **时间**: 2026-10-11T08:00:59Z
- **提交信息**: [Sampler] Sort only the max(top_k) leading columns in the torch sampler (#43346)

### [dab108b](https://github.com/sgl-project/sglang/commit/dab108b9f386b5b991ee070c7e4784f35df03f93)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-11T07:18:27Z
- **提交信息**: [Scheduler] Hold back decode rows on a mixed step when they do not fit the KV pool (#43290)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-10-12
**监控日期**: 2026-10-11
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1290
- **最后更新**: 2026-10-10T08:39:17Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-10-12
**监控日期**: 2026-10-11
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 93585
- **最后更新**: 2026-10-12T01:09:04Z

## 提交统计

- **昨日提交总数**: 15
- **提交者数量**: 11
- **主要提交者**: tc-mb, debanshd, Jared Wen

## AI分析总结

## vLLM 昨日提交分析（共15条）

### 1. 主要更新类型
- **Bug修复**（7条）：占主导，涵盖注意力机制、缓存管理、前端、安全等领域
- **性能优化**（2条）：TP分片优化、GPU内存回收
- **安全加固**（2条）：ZMQ资源耗尽修复、CORS限制
- **模型支持**（1条）：新增 MiniCPM-V 4.7
- **工程改进**（3条）：MRV2 CI切换、RL通信器释放、前端提示优化

### 2. 关键变更点与项目方向的关系
- **混合架构（Hybrid）深度优化**：MRV2 相关修复（FlashInfer注意力、ReplaySSM预热、CI迁移）表明 vLLM 正在积极推广 MRV2（多记录版本2）后端架构，逐步淘汰 MRV1。
- **Mamba/SSM 状态空间模型持续完善**：GLM-5.3-Flash 的 SSM 缓存 dtype 修复与长上下文索引器 TP 分片，说明 vLLM 在混合 Transformer+Mamba 模型上的投入不断加深。
- **投机解码（EAGLE）与分布式推理修复**：Mooncake EAGLE 滑动窗口边界、RL 权重传输通信器释放，对应 vLLM 在 RL 训练-推理协同和高性能投机解码上的方向。
- **安全收紧**：ZMQ P2P peer session 不受控增长和默认 CORS 过宽的修复，体现项目对生产环境安全性的重视，符合其"人人可用的LLM服务"的定位。

### 3. 对项目的影响和潜在意义
- **稳定性提升**：内存管理类修复（权重加载时回收缓存、Fast Start 快照时机）直接减少 OOM 和启动失败，改善用户体验。
- **功能正确性**：离线 chat template 被正确应用、前端 priority 参数打通 `LLM.chat()`，让 API 层行为符合用户预期。
- **生态扩展**：MiniCPM-V 4.7 的加入延续了 vLLM 快速跟进主流开源模型的传统。
- **协作信号**：多条提交有 Claude/Codex/Kimi 等 AI 助手的联合署名，反映 AI 辅助开发已深度嵌入 vLLM 的工程流程。

### 4. 值得关注的技术点
- **ZMQ socket 耗尽修复**（#51504）：限制 P2P peer session 数量，防止恶意或异常 peer 导致资源耗尽，是分布式推理栈中的重要防御性修复。
- **长上下文索引器跨 TP 分片**（#54951）：对 GLM-5.3-Flash 这类长上下文模型，避免单卡行数瓶颈，显著改善预填充吞吐。
- **RL 权重传输通信器无停机释放**（#61060）：对 RLHF/vLLM 组合工作流，消除权重同步期间的推理中断。
- **GPU 内存回收与外部权重加载时序**（#60966、#57516）：改善 Fast Start 等动态权重加载场景的内存压力。

### 5. 对项目发展的影响
结合 README "Easy, fast, and cheap LLM serving for everyone" 的目标，本批提交整体呈现"**稳内核、拓前沿**"的态势：安全与内存修复降低了使用门槛（Easy），TP 分片与通信器优化提升吞吐（Fast），模型支持与混合架构完善则巩固了 vLLM 在多样化模型生态中的核心地位（cheap/efficient）。MRV2 的加速推广预示后端架构将进入新阶段，安全加固则为更大规模的生产部署铺路。

## 详细提交记录

### [3fe917a](https://github.com/vllm-project/vllm/commit/3fe917abb13160d60bea5330399f5c09ca282348)

- **作者**: Nick Hill
- **时间**: 2026-10-11T23:04:41Z
- **提交信息**: [Bugfix][MRV2] Fix FlashInfer attention and ReplaySSM warmups on MRV2 (#61013)

Signed-off-by: Nick Hill <nickhill123@gmail.com>

### [f26d9f4](https://github.com/vllm-project/vllm/commit/f26d9f432ced7b1087d02d29bffed2249df1a18e)

- **作者**: Jared Wen
- **时间**: 2026-10-11T17:55:00Z
- **提交信息**: [Bugfix][GLM-5.3-Flash] Honor `--mamba-ssm-cache-dtype` for the KDA recurrent state (#59147)

Signed-off-by: Jared Wen <jaredwen@inferact.ai>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [c059bee](https://github.com/vllm-project/vllm/commit/c059bee812842fb76c2b045e240c02f37c0d498d)

- **作者**: Nick Hill
- **时间**: 2026-10-11T16:57:07Z
- **提交信息**: [MRV2] Switch CI tests still running on MRV1 unnecessarily (#61014)

Signed-off-by: Nick Hill <nickhill123@gmail.com>

### [b99fdbe](https://github.com/vllm-project/vllm/commit/b99fdbe1f896abd7f4b133685a37397c3427f7d5)

- **作者**: Ting SUN
- **时间**: 2026-10-11T16:27:21Z
- **提交信息**: [Bugfix] Respect the configured offline chat template (#61061)

Signed-off-by: Ting Sun <suntcrick@gmail.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>

### [93d2cab](https://github.com/vllm-project/vllm/commit/93d2cab35e8ae66bbaa1dea1c077986d5a79eb80)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-10-11T15:39:11Z
- **提交信息**: [Security] Fix P2P ZMQ socket exhaustion via unbounded peer sessions (#51504)

Signed-off-by: jperezde <jperezde@redhat.com>
Signed-off-by: Juan Pérez de Algaba <jperezde@redhat.com>
Co-authored-by: Robert Shaw <114415538+robertgshaw2-redhat@users.noreply.github.com>
Co-authored-by: Itay Etelis <92247226+Etelis@users.noreply.github.com>

### [239a3fa](https://github.com/vllm-project/vllm/commit/239a3fa3a8ffc6508e867452c115ea7bcee2304b)

- **作者**: aoshen02
- **时间**: 2026-10-11T15:30:56Z
- **提交信息**: [Sleep] Retain draft-private weights with existing parameter selector (#61046)

Signed-off-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: Codex <noreply@openai.com>

### [3e8e136](https://github.com/vllm-project/vllm/commit/3e8e1364ff41330fb667b2d76d6645176d61fdd0)

- **作者**: Zheng Cai
- **时间**: 2026-10-11T14:43:37Z
- **提交信息**: [Perf][GLM-5.3-Flash] Shard long-context indexer prefill rows across TP (#54951)

Signed-off-by: Zheng Cai <8370601+zigzagcai@users.noreply.github.com>
Signed-off-by: Zheng Cai <caizheng1993@gmail.com>
Signed-off-by: Codex <noreply@openai.com>
Co-authored-by: root <root@rjob-fb29567b88fec0a9-88c9a4c797eb2ec1-0.caizheng.ailab-sys.svc.pjlab.local>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: zigzagcai <zigzagcai@users.noreply.github.com>
Co-authored-by: Claude Code <noreply@anthropic.com>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>

### [bd5bbce](https://github.com/vllm-project/vllm/commit/bd5bbce6e45e09dbd07ac3e8c394626c059078f7)

- **作者**: aoshen02
- **时间**: 2026-10-11T13:15:14Z
- **提交信息**: [RL] Release weight-transfer communicators without stopping inference (#61060)

Signed-off-by: aoshen02 <aoshen@inferact.ai>
Signed-off-by: fh3 <a@b>

### [c85616e](https://github.com/vllm-project/vllm/commit/c85616efc6f0eaa50ca1f1a09c32368aedffd3d8)

- **作者**: tc-mb
- **时间**: 2026-10-11T10:21:10Z
- **提交信息**: [Model] Support MiniCPM-V 4.7 (#58674)

Signed-off-by: tc-mb <tianchi_cai@icloud.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>

### [f425a21](https://github.com/vllm-project/vllm/commit/f425a212081181e3d6ad2ca92daa74ba0f9e83a4)

- **作者**: Subhash Polisetti
- **时间**: 2026-10-11T10:03:33Z
- **提交信息**: [Bugfix][Frontend] Support scalar priority and wire priority into LLM.chat() (#57243)

Signed-off-by: subhash polisetti <subhashr161347@gmail.com>

### [2339bd3](https://github.com/vllm-project/vllm/commit/2339bd39d661965b821bfbe652db8f536e0b3dcd)

- **作者**: Stu Cao
- **时间**: 2026-10-11T09:15:18Z
- **提交信息**: [Bugfix][Mooncake] Use the EAGLE replay boundary when retaining sliding-window tails (#61012)

Signed-off-by: Stu Cao <stu@primeintellect.ai>
Signed-off-by: Yifan Qiao <yifanqiao@inferact.ai>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: Yifan Qiao <yifanqiao@inferact.ai>
Co-authored-by: Codex <noreply@openai.com>

### [1789f09](https://github.com/vllm-project/vllm/commit/1789f095881d14966d7d4d9a2647748bf32dd834)

- **作者**: aoshen02
- **时间**: 2026-10-11T08:58:07Z
- **提交信息**: [Frontend] Explain disabled scale-out endpoints with opt-in hints (#61042)

Signed-off-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [fcae5c9](https://github.com/vllm-project/vllm/commit/fcae5c98870ff2c20659731dce7ba3a3ff0d48aa)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-10-11T08:26:02Z
- **提交信息**: [Security] Restrict default CORS origins (#61009)

Signed-off-by: Juan Pérez de Algaba <jperezde@redhat.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>

### [26a488a](https://github.com/vllm-project/vllm/commit/26a488ad93d12c658449a19dea2eb78f1be38f83)

- **作者**: Xun Sun
- **时间**: 2026-10-11T07:10:04Z
- **提交信息**: [Fast Start][Bugfix] Snapshot GPU memory after external weights are ready (#60966)

### [ef42b43](https://github.com/vllm-project/vllm/commit/ef42b4385f8512567703692a5bfbb9c0edc59c89)

- **作者**: debanshd
- **时间**: 2026-10-11T07:03:06Z
- **提交信息**: [Bugfix] Reclaim cached GPU memory during weight loading (#57516)

Signed-off-by: Debanshu Das <debanshu@google.com>
Signed-off-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: Kimi Code <noreply@moonshot.cn>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-10-12
**监控日期**: 2026-10-11
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7125
- **最后更新**: 2026-10-12T00:49:40Z

## 提交统计

- **昨日提交总数**: 11
- **提交者数量**: 10
- **主要提交者**: BeatSeat, Laceprndpm, Kuatova Kamila

## AI分析总结

# vllm-omni 昨日提交分析总结

## 1. 主要更新类型

- **模型支持新增与适配（4项）**：MiniMax H3 时间线引导条件、Cosmos3 视频输出优化、Wan 2.2 VAE 编码优化、MiniCPM-o 4.5 适配
- **Bug 修复（5项）**：涵盖桥接客户端错误处理、CUDA 图显存预留、a2a JIT 构建、CLI 配置冲突、引擎空闲前的请求最终化
- **性能优化与重构（2项）**：TTS/全双工路径死代码清理、性能指标可配置

整体呈现"新模型支持为主、稳定性修复并重"的提交分布，无文档类更新。

## 2. 关键变更点与项目方向的关系

项目 README 定位为"人人可用的 omni-modality 模型serving"，强调易用、快速、低成本。昨日提交高度契合这一定位：

- **扩展 omni 模型生态**：MiniMax H3、Cosmos3、Wan 2.2、MiniCPM-o 4.5 均为多模态/omni 模型，表明项目在积极覆盖主流 omni 模型谱系，直接强化"omni-modality serving"的核心能力。其中 MiniCPM-o 4.5 涉及"全双工 MRv2"统一支持，说明项目在语音-视觉全双工交互场景上的架构演进。
- **降低serving成本与提升吞吐**：Cosmos3 视频输出传输开销优化、Wan 2.2 VAE 编码优化、Omni KV 缓存的 CUDA 图显存预留，均指向"fast and cheap"的目标——通过减少数据搬运、编码开销和显存浪费来提升吞吐并降低成本。
- **提升系统健壮性（易用性）**：桥接客户端错误只失败请求而非整个 orchestrator、修复 CLI 与 deploy-config 的配置冲突、引擎空闲前正确 finalize 请求，这些修复降低了运维复杂度和故障半径，呼应"Easy"的承诺。

## 3. 对项目的影响和潜在意义

- **短期**：新增 4 个模型适配直接扩大可用模型覆盖面，吸引使用这些模型的用户；5 项 bugfix 修复了显存、构建、配置等实际部署中的痛点，提升线上稳定性。
- **中期**：全双工 MRv2 统一支持（#8536）可能是一次重要的架构整合，为后续全双工 omni 模型（语音交互、实时对话类）提供统一框架，减少逐模型适配的碎片化成本。
- **潜在风险**：CUDA 图显存预留（#7632）和 a2a JIT 构建修复（#7599）涉及底层显存与编译逻辑，若测试不充分可能引入回归，建议关注相关 CI 与回归测试覆盖情况。

## 4. 值得关注的技术点

- **全双工 MRv2 与 MiniCPM-o 4.5 适配**：全双工（full-duplex）指模型可在听取的同时持续输出，是实时语音 omni 场景的关键能力；MRv2 疑似一种多模态表示或路由版本，统一支持意味着抽象层的提升。
- **Omni KV 缓存与 CUDA 图显存预留**：omni 模型多模态注意力 KV 缓存 + CUDA Graph 的显存协同管理是 serving 层的高难度问题，此修复说明项目已进入显存精细化管理阶段。
- **Wan 2.2 VAE 编码优化**：VAE 编码是视频/图像扩散模型的瓶颈，优化后可显著提升视频生成类 omni 模型的首帧延迟与吞吐。
- **性能指标可配置**（#8554）：允许关闭 per-request stage metrics，为高并发场景减少监控开销，体现生产环境成熟度的提升。

## 5. 对项目发展的影响（结合 README 背景）

README 强调"Easy, fast, and cheap omni-modality model serving for everyone"。昨日提交从三个维度支撑了这一愿景：**广度上**通过 MiniMax H3、Cosmos3、Wan 2.2、MiniCPM-o 4.5 扩展模型生态；**速度与成本上**通过 VAE 编码、视频传输、KV 缓存显存优化降低单请求开销；**易用与稳定上**通过 orchestrator 容错、CLI 配置修复、请求生命周期修复降低使用门槛。其中全双工 MRv2 的统一支持尤其值得关注，它可能成为项目在实时语音 omni serving 领域的差异化架构基础，长期有利于项目在 vLLM 生态中确立 omni 场景的专精地位。

综上，昨日的提交组合显示出项目正处于"生态扩张 + 生产级稳定性加固"并行推进的阶段，与其"人人可用的 omni serving"愿景高度一致。

## 详细提交记录

### [198c210](https://github.com/vllm-project/vllm-omni/commit/198c2105930bd1bac0b0966ffd0997cdd84d4790)

- **作者**: shykoe
- **时间**: 2026-10-11T15:33:51Z
- **提交信息**: [Model] MiniMax H3 timeline guide conditioning (#8460)

Signed-off-by: shykoe <shykoe@gmail.com>
Signed-off-by: princepride <wangzhipeng628@gmail.com>
Co-authored-by: princepride <wangzhipeng628@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [47776fd](https://github.com/vllm-project/vllm-omni/commit/47776fd350f55f21e016d58167129476497cb3e5)

- **作者**: Rahul Steiger
- **时间**: 2026-10-11T14:32:43Z
- **提交信息**: [Model] Cosmos3: Reduce video output transfer overhead (#5712)

Signed-off-by: Rahul Steiger <rsteiger@nvidia.com>
Signed-off-by: Rahul Steiger <rsteiger@aws-cmh-slurm-1-vscode-04.cm.cluster>
Co-authored-by: Copilot Autofix powered by AI <175728472+Copilot@users.noreply.github.com>
Co-authored-by: Rahul Steiger <rsteiger@aws-cmh-slurm-1-vscode-04.cm.cluster>

### [5b95f27](https://github.com/vllm-project/vllm-omni/commit/5b95f2791f062fcaa2091e033eab0006b6360db2)

- **作者**: Kuatova Kamila
- **时间**: 2026-10-11T13:35:16Z
- **提交信息**: [Bugfix] Fail the request, not the orchestrator, on a bridge client error (#8605)

Signed-off-by: Kamila Kuatova <kuatova_kamila@list.ru>
Signed-off-by: princepride <wangzhipeng628@gmail.com>
Co-authored-by: princepride <wangzhipeng628@gmail.com>

### [6bacbf2](https://github.com/vllm-project/vllm-omni/commit/6bacbf2742021b17a299b8b57e19a04e7ef44036)

- **作者**: MaciejBalaNV
- **时间**: 2026-10-11T13:31:37Z
- **提交信息**: [optimization] Added Wan 2.2 VAE encode optimizations (#8067)

Signed-off-by: Maciej Bala <mbala@nvidia.com>
Signed-off-by: MaciejBalaNV <mbala@nvidia.com>

### [2fe2977](https://github.com/vllm-project/vllm-omni/commit/2fe2977e9970b2e76ea50744940cb778217a980c)

- **作者**: Yueqian Lin
- **时间**: 2026-10-11T12:38:51Z
- **提交信息**: [Misc] Remove dead and duplicate code in TTS and full-duplex paths (#8751)

Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: Sy03 <1370724210@qq.com>

### [213a1c8](https://github.com/vllm-project/vllm-omni/commit/213a1c835ed595d6a51d4f918e3920f4159dd7ed)

- **作者**: BeatSeat
- **时间**: 2026-10-11T10:40:44Z
- **提交信息**: [Core][Model] Unified Full-Duplex MRv2 Support and MiniCPM-o 4.5 Adaptation (#8536)

Signed-off-by: BeatSeat <wendavid552@gmail.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [5217267](https://github.com/vllm-project/vllm-omni/commit/5217267cfc1cc625e12eae79ef8dda6cf32d9a03)

- **作者**: DanaerLee
- **时间**: 2026-10-11T10:03:11Z
- **提交信息**: [Bugfix] Reserve CUDA graph memory when sizing Omni KV caches (#7632)

Signed-off-by: MrlixiangWE <mrdanaer@gmail.com>
Co-authored-by: zijianc2 <157244773+zijianc2@users.noreply.github.com>
Co-authored-by: amy-why-3459 <221522807+amy-why-3459@users.noreply.github.com>

### [bdc01f8](https://github.com/vllm-project/vllm-omni/commit/bdc01f866e12c5b4d7e0523b161b4dd87f77bf8f)

- **作者**: Lele
- **时间**: 2026-10-11T09:13:32Z
- **提交信息**: [Bugfix] Preserve CUDA toolkit header precedence in a2a JIT builds (#7599)

Signed-off-by: 武垚乐 <wuyaole@mininglamp.com>
Co-authored-by: 武垚乐 <wuyaole@mininglamp.com>

### [46dedaf](https://github.com/vllm-project/vllm-omni/commit/46dedafbb7deee11c9ea89f3e77663515c554f64)

- **作者**: MaciejBalaNV
- **时间**: 2026-10-11T08:49:57Z
- **提交信息**: [bugfix] Fix CLI flags that modify model_config when using --deploy-config (#8289)

Signed-off-by: Maciej Bala <mbala@nvidia.com>

### [096988d](https://github.com/vllm-project/vllm-omni/commit/096988d30cd017bf833033bc06ef3ebc48077d09)

- **作者**: Alessio Netti
- **时间**: 2026-10-11T07:08:04Z
- **提交信息**: [Perf] Allow disabling per-request stage metrics (#8554)

Signed-off-by: Alessio Netti <26897207+AlessioNetti@users.noreply.github.com>

### [9ea7ee4](https://github.com/vllm-project/vllm-omni/commit/9ea7ee4f265b8022500d613f26e8de1c7ecb90b5)

- **作者**: Laceprndpm
- **时间**: 2026-10-11T07:07:57Z
- **提交信息**: [Bugfix] Finalize step requests before engine idle (#8719)

Signed-off-by: Laceprndpm <laceprndpm.64@gmail.com>

---
