# GitHub Stars 合并报告 - 2026-09-30

**合并日期**: 2026-10-01
**监控日期**: 2026-09-30
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


**报告日期**: 2026-10-01
**监控日期**: 2026-09-30
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2230
- **最后更新**: 2026-09-30T08:21:01Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-10-01
**监控日期**: 2026-09-30
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2869
- **最后更新**: 2026-09-30T16:37:44Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-10-01
**监控日期**: 2026-09-30
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2275
- **最后更新**: 2026-09-30T14:42:54Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-10-01
**监控日期**: 2026-09-30
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6525
- **最后更新**: 2026-10-01T01:09:04Z

## 提交统计

- **昨日提交总数**: 18
- **提交者数量**: 12
- **主要提交者**: Chunan Zeng, bhsueh_NV, Ligeng Zhu

## AI分析总结

# FlashInfer 昨日提交综合分析

## 一、主要更新类型
昨日共 18 个提交，以**性能优化、功能新增、Bug 修复**为主：CAKE 团队的内核优化迭代与新前沿算子移植（约 11 个）、架构门槛放宽与新后端引入（约 4 个）、下游框架兼容性修复与 CI/日志改进（约 3 个）。

## 二、关键变更点
1. **Rubin（SM107）架构支持放宽**：CuTe packed KDA、随机舍入 `cvt.rs`、Mamba2 SSD、fused gated MXFP8 量化移除了静态架构白名单，可在 Rubin 上原生运行；MLA decode 利用 SM107 的 327KB 共享内存将 K/V 加载流水线加深至 4/4 阶，修复了此前隐藏的 ~4x 软件回退代价。
2. **CAKE 团队持续优化循环**：Kimi-K3 LatentMoE、NVFP4 GEMM、radix sampling、multi-LoRA BGMV MoE 等采用"杠杆账本"式迭代，每个 PR 仅采纳一个 A/B 验证过的变换并保持位级一致；BGMV MoE 扩展至 SM90/100/103 三个目标。
3. **新算子与新后端**：`flashinfer.recurrent_kda(..., backend="ptx")` 引入 Kimi Delta Attention 的 PTX 前端，B300 上相对基线实现 2.918x 加速；新增 8-bit Sage attention、SM100/103 原生 DSA 稀疏注意力训练内核、KDA CuTe 实现，SM90 MLA 自动回退 FA2。
4. **MoE 路由关键修复**：修复 TRT-LLM 路由中 `permuted_idx_to_token_idx` 未使用填充行未初始化的问题——TMA gather 会为被屏蔽的填充行加载激活值，导致延迟依赖工作区历史内容。修复方式是在路由生产者中直接写入 `-1` 填充索引，零额外开销，覆盖 block、dynamic-block、cluster、cooperative、histogram/offsets 五种路由路径；同时修复了 SM12x MoE 对 -1 expert id 的跳过、SM89 CUTLASS MoE 缺失的 ENABLE_FP4 编译守卫。
5. **基础设施**：SM107 GEMM 候选拒绝日志降级到 DEBUG、CI stage benchmarks 脚本修复、nightly 包测试补全 benchmarks 目录。

## 三、项目影响
- **Rubin 生态就绪**：多个算子从静默回退变为原生支持，为 Rubin 平台部署扫清障碍。
- **性能确定性保障**：MoE 填充索引修复消除了 GB300 上 NVFP4 TMA gather 策略的非确定性延迟，使 SLA 严格的生产环境性能更可预测；测试结果在 8192 tokens、896 experts、top-k 16 场景下验证了显著延迟改善。
- **技术纵深扩大**：KDA/DSA 训练内核的引入使 FlashInfer 从纯推理内核向训练场景延伸，算子覆盖（线性注意力、MoE、量化注意力、采样）与现代 LLM 服务场景高度契合。
- **下游生态兼容**：MoE 的 vLLM padding 语义兼容、MLA 自动后端回退、路由文档更新，体现对 vLLM、TensorRT-LLM 等框架互操作性的重视。

## 四、技术关注点
- **架构自适应设计**：共享内存预算按 SM107 容量精确调整；`cvt.rs` 需 CUDA 13.4 ptxas 支持且 sm_110a/120a 仍拒绝 `.rs`，体现跨工具链版本的兼容性细节。
- **CUDA Graph 友好**：DSA、KDA 实现强调一次性参数绑定、后续无分配启动；MoE 修复复用现有 tile 元数据写入机制，避免修复引入新开销。
- **数值与测试纪律**：bit-identical 输出、A/A 控制、冷 LCUPTI 计时、CUDA Graph replay + CUDA events + 中位数统计等严谨方法论贯穿始终；INT8 分数 FP32 累积、未路由 token 精确零行等细节保证数值正确。
- **JIT 基础设施**：KDA PTX 后端缓存含汇编器与源码标识、原子发布、包外写入，为未来 JIT 扩展奠定基础。

## 五、整体展望
FlashInfer 正从 Blackwell 优化库演进为**多架构（Hopper→Blackwell→Rubin）、多算子形态（CUTLASS/CuTe DSL/PTX）的统一高性能推理层**。这批提交显示项目在新硬件快速适配、前沿模型算子深度支持、严格基准驱动的持续微调三线并进，同时以生产级的确定性质量追求巩固其在 LLM 服务生态中的内核层竞争优势。

## 详细提交记录

### [b6deaf7](https://github.com/flashinfer-ai/flashinfer/commit/b6deaf768214556d79a28fbfa5b18e9906dd4437)

- **作者**: Vincent
- **时间**: 2026-09-30T23:43:57Z
- **提交信息**: feat(kda,mamba): enable CuTe packed KDA decode, cvt.rs stochastic rounding and Mamba2 SSD on SM107 (Rubin) (#5396)

## What

Enables three linear-attention / SSM paths on SM107 (Rubin) that were
held back by static architecture allowlists. One commit per path; each
is independent. (The Cake packed KDA T=1, Cake GDN and frozen
FlashKDA/Cake decode enablements that were here moved to the dedicated
Cake PR #5467.)

| path | gate(s) removed | GR100 (cc 10.7) result |
|---|---|---|
| Experimental CuTe packed KDA | two exact-(10,0) pins: `_check_b200` in
the kernel module and the fast-path mode selector in `recurrent_kda.py`
(whose `None` silently sent calls down the generic path) |
`tests/kda/test_packed_kda_decode_cute.py`: 1 passed / 41 skipped → **42
passed** |
| Hardware `cvt.rs` stochastic rounding (Mamba checkpointing SSU, Philox
SR) | `is_cvt_rs_supported()` + the `FLASHINFER_MAMBA_HAS_CVT_RS` guard
(`__CUDA_ARCH_FEAT_SM107_ALL`) |
`tests/mamba/test_checkpointing_ssu.py`: 234 passed / 62 skipped → **292
passed / 4 skipped** |
| CuTe DSL Mamba2 SSD (`SSDCombined`) | an explicit `(major, minor) ==
(10, 7)` carve-out on top of the SM100-family check |
`tests/mamba/test_chunk_scan_combined.py`: 25 skipped → **24 passed / 1
xfailed** |

## Why these are safe

- **CuTe packed KDA**: the kernel has no architecture pins (no
`blackwell_helpers`, tcgen05, `GPUArch` or `"sm_100"` strings); the two
exact-(10,0) checks also excluded SM103. The batch-size config ladder
stays B200-tuned.
- **`cvt.rs`**: `cvt.rs.{f16x2,bf16x2,satfinite.e4m3x4}.f32` assemble
for `sm_107a` with the CUDA 13.4 ptxas (`sm_110a`/`sm_120a` still reject
`.rs`, as the guard's comment requires checking). Besides the skips, the
old guard made Rubin silently compile the ~12-instruction software
fallback that the code's own comment measured at ~4× the cost — so this
is also a perf fix.
- **Mamba2 SSD**: the carve-out comment said only "not yet supported by
this kernel"; the kernel's ingredients (tcgen05 1/2-CTA MMA,
`blackwell_helpers`, sm_100 SMEM budget) are the same ones the TGV
cute_ext GEMM (#5333) runs with on Rubin under CuTe DSL ≥ 4.8.0.dev0.

## Caveats

- **The two `tests/mamba` results (cvt.rs, Mamba2) were measured with
the directory's Triton conftest probe forced open.** That probe
blanket-skips all of `tests/mamba` on Rubin today and is fixed by #5308;
until #5308 lands these tests keep skipping in CI regardless of this PR.
- Tuning inherited from Blackwell on SM107: the CuTe packed KDA batch
ladder stays B200-tuned. Functionally validated; not Rubin-tuned.
- Validated on x86_64 only (GR100, driver 620.05); the Rubin CI nodes
are arm64. Not included: Cake FlashKDA **prefill** (sealed per-arch
generated registry) and the frozen Cake SSD path (per-arch artifacts) —
raised with the Cake owner.

## Validation

Image `flashinfer-ci:cu134-nightly-py3.67144516-whl-amd64` with the CI
job's `nvidia-cutlass-dsl[cu13]==4.8.0.dev0` override, against an
`upstream/main` baseline on the same tree/image — numbers in the table
above; **zero new failures**.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Expanded KDA decoding support to GPUs with compute capabilities 10.0,
10.3, and 10.7 (Rubin).
* Mamba SSD operations now accept compute-capability major versions 10
and 11, including SM107 (Rubin).
  * Hardware stochastic rounding support now includes SM107 GPUs.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Vincent Tombari <Vinnie6167@users.noreply.github.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [45d35e4](https://github.com/flashinfer-ai/flashinfer/commit/45d35e4e7509c400c83f46eea5cc6d3e078052ea)

- **作者**: eigen
- **时间**: 2026-09-30T21:57:51Z
- **提交信息**: perf(cake_kimi_k3_latent_moe): round 10 -- final-item staged TMA store for the 256-wide prefill tail GEMM instances (SM100a/SM103a) (#5734)

Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

## Summary

Round 10 of the Kimi-K3 Stable LatentMoE front / tail projections in
`flashinfer/experimental/kimi_k3_latent_moe` (#5721, #5671, #5647,
#5584, #5575, tracker #4254): a paired lever ledger on B200 and B300
(A/B in interleaved CUDA-graph groups, cold-L2 CUPTI timing, an A/A
control per row, two independent processes per GPU for the single-wave
rows) adopts one exact transformation of the prefill tail GEMM and
nothing else. The decode programs, the front GEMM and the tail norm are
unchanged from #5721 and regenerated from the same registry keys. Public
API, tensor shapes / dtypes / strides and the weight layout (`[N, K]`
bf16, no load-time packing) are unchanged; every program still binds its
tensor maps by value. Numerics are exact: the same fp32 accumulators and
the same round-to-nearest bf16 conversion, so `out` is bit-identical to
the #5721 programs on every row.

- **Final-item staged TMA store (every 256-wide tail GEMM instance).** A
persistent CTA's epilogue used to write each 128 x 256 output tile with
32-B scattered stores from all 32 lanes of its eight epilogue warps. Now
the CTA's *last* item (its last stream-K segment) packs its bf16 rows
into the memory of the drained TMA ring (32 KiB, free because the item's
last `mainloop_done` phase followed the last `tcgen05.commit`),
publishes the eight 32 x 64 slabs to the async proxy and lets one
elected lane per warp issue one `cp.async.bulk.tensor` store per slab;
every earlier item keeps the direct stores (staging them too loses to
shared-memory port contention with the next item's mainloop -- measured
in the round's earlier batches on both GPUs). The epilogue learns that
an item is its last by consuming the work-ring response before the
item's stores instead of after them (same response, same order). No
extra shared memory, the 7-deep ring stays. Paired on the same tree
(B200 / B300, vs the #5721 programs): `tail_tp8_m256` **+3.0 / +2.9 %**,
`tail_tp8_m1024` **+2.8 / +2.9 %**, `tail_tp8_m2048` +1.0 / +0.6 %,
`tail_tp8_m4096` +1.0 / +1.0 %, `tail_tp8_m8192` +0.4 / +0.5 %,
`tail_tp8_m16384` +0.3 / +0.2 %; `tail_tp1_m256` +0.8 / +0.6 %,
`tail_tp1_m512` +0.8 / +0.7 %, `tail_tp1_m1024` +0.3 / +0.4 %,
`tail_tp1_m2048` +0.4 / +0.6 %, `tail_tp1_m4096` +0.4 / +0.3 %,
`tail_tp1_m8192` / `m16384` neutral (A/A controls within +-0.5 %). The
128-wide TP8 T=512 instance keeps the direct stores: with one 64-column
pass per warp the slab's fixed cost exceeds the exposed store it
replaces (0.987 / 0.989).

Host planner (`cake_backend.py`): `tail_gemm_config` now returns
`(num_stages, block_n, final_ts)` and the staged-store instances carry
the new key suffix `t1`
(`tail_gemm:tp<1|8>e<0|1>f<0|1>[s<stages>][n<block_n>][t1]`; the
128-wide instance keeps `tail_gemm:tp8e0f0s9n128`); the tail GEMM
binding passes the bf16 tensor map of `out` (`out_map`, bound by value
from the same tensor) beside the `out` pointer -- the generated argument
plan of a `t1` program lists it, the 128-wide program's does not. Plan
fields, the decode / front / norm keys, the package-internal fp32
partial workspaces and the arrival counters are those of #5721;
`cake_jit.py` (the regenerated module records), the generated sources,
`cake_backend.py` and the tests change.

## Evidence (Cake export protocol, producer `0f753f42986`, target
`da5189d61`)

Every row runs the source (Cake production launcher) and the exported
programs in counterbalanced CUDA-graph groups; correctness = both arms
against the FP32/BF16 torch reference, bitwise source == export.

| arch | GPU | rows sealed | clock-unqualified (disclosed) | correct
(bitwise source == export) | source/export | steps |
|---|---|---|---|---|---|---|
| sm_100a | B200 | 50 / 60 | 9 clock-unqualified + `front_tp1_m1024`
(first: endpoint-drift gate, ratio 0.9989, correct, bitwise; retry:
endpoint-drift gate, ratio 0.9988, correct, bitwise) | 52 / 52 | 0.9560
- 1.0778 | 84d2d00be3a00bc0308e8754 (protocol) +
d90e503918c200c043ce3d74 (export) + c3cad116c80cd8301f843495 (retry + FI
tests) |
| sm_103a | B300 | 51 / 60 | 9 clock-unqualified | 51 / 51 | 0.9577 -
1.0632 | 1b989f49f47e4b269545b2b9 (export) + cd8cf06bc801255d0ca98004
(retry + FI tests) |

Clock-unqualified rows: the sustained dense tcgen05 GEMM rows run at the
power cap and the interleaved timing session sampled the loaded SM clock
below 0.85 x max on both bounded attempts (sampled / max MHz): sm_100a:
`front_tp1_m2048` (1605/1965 MHz first, 1537/1965 MHz retry),
`front_tp1_m4096` (1485/1965 MHz first, 1312/1965 MHz retry),
`front_tp1_m8192` (1432/1965 MHz first, 1432/1965 MHz retry),
`front_tp1_m16384` (1320/1965 MHz first, 1657/1965 MHz retry),
`front_tp8_m8192` (1477/1965 MHz first, 1462/1965 MHz retry),
`front_tp8_m16384` (1387/1965 MHz first, 1395/1965 MHz retry),
`tail_tp1_m4096` (1575/1965 MHz first, 1560/1965 MHz retry),
`tail_tp1_m8192` (1402/1965 MHz first, 1417/1965 MHz retry),
`tail_tp1_m16384` (1342/1965 MHz first, 1357/1965 MHz retry); sm_103a:
`front_tp1_m2048` (1537/2032 MHz first, 1515/2032 MHz retry),
`front_tp1_m4096` (1320/2032 MHz first, 1417/2032 MHz retry),
`front_tp1_m8192` (1282/2032 MHz first, 1290/2032 MHz retry),
`front_tp1_m16384` (1237/2032 MHz first, 1237/2032 MHz retry),
`front_tp8_m8192` (1680/2032 MHz first, 1425/2032 MHz retry),
`front_tp8_m16384` (1282/2032 MHz first, 1290/2032 MHz retry),
`tail_tp1_m4096` (1425/2032 MHz first, 1425/2032 MHz retry),
`tail_tp1_m8192` (1312/2032 MHz first, 1725/2032 MHz retry),
`tail_tp1_m16384` (1252/2032 MHz first, 1245/2032 MHz retry). They are
disclosed per the protocol (no ratio gate loosened); their paired
speedups vs the stock chain are in the contract table below.

<details><summary>sm_100a per-row receipts</summary>

| row (B200, sm_100a) | route | source | export | source / export |
correctness (both arms) | bitwise src == exp | verdict |
|---|---|---|---:|---:|---|---|---|
| front_tp1_m1 | decode | 49.76 us | 49.76 us | 1.0000 | pass | yes |
sealed |
| front_tp1_m2 | decode | 49.98 us | 50.08 us | 0.9981 | pass | yes |
sealed |
| front_tp1_m4 | decode | 50.27 us | 50.14 us | 1.0026 | pass | yes |
sealed |
| front_tp1_m8 | decode | 50.27 us | 50.08 us | 1.0038 | pass | yes |
sealed |
| front_tp1_m16 | decode | 50.56 us | 50.69 us | 0.9975 | pass | yes |
sealed |
| front_tp1_m32 | decode | 51.33 us | 51.17 us | 1.0031 | pass | yes |
sealed |
| front_tp1_m64 | decode | 53.57 us | 53.66 us | 0.9982 | pass | yes |
sealed |
| front_tp1_m128 | decode | 59.71 us | 59.65 us | 1.0011 | pass | yes |
sealed |
| front_tp1_m256 | prefill | 52.13 us | 52.24 us | 0.9978 | pass | yes |
sealed |
| front_tp1_m512 | prefill | 85.47 us | 85.02 us | 1.0053 | pass | yes |
sealed |
| front_tp1_m1024 | prefill | — | — | — | — | — | disclosed: first:
endpoint-drift gate, ratio 0.9989, correct, bitwise; retry:
endpoint-drift gate, ratio 0.9988, correct, bitwise |
| front_tp1_m2048 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1605/1965 MHz first, 1537/1965 MHz retry) |
| front_tp1_m4096 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1485/1965 MHz first, 1312/1965 MHz retry) |
| front_tp1_m8192 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1432/1965 MHz first, 1432/1965 MHz retry) |
| front_tp1_m16384 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1320/1965 MHz first, 1657/1965 MHz retry) |
| front_tp8_m1 | decode | 21.60 us | 21.70 us | 0.9956 | pass | yes |
sealed |
| front_tp8_m2 | decode | 21.89 us | 21.92 us | 0.9985 | pass | yes |
sealed |
| front_tp8_m4 | decode | 21.79 us | 21.82 us | 0.9985 | pass | yes |
sealed |
| front_tp8_m8 | decode | 21.86 us | 21.95 us | 0.9957 | pass | yes |
sealed |
| front_tp8_m16 | decode | 22.08 us | 22.08 us | 1.0000 | pass | yes |
sealed |
| front_tp8_m32 | decode | 23.46 us | 23.42 us | 1.0014 | pass | yes |
sealed |
| front_tp8_m64 | decode | 25.70 us | 25.63 us | 1.0025 | pass | yes |
sealed |
| front_tp8_m128 | decode | 31.30 us | 31.39 us | 0.9969 | pass | yes |
sealed |
| front_tp8_m256 | prefill | 30.78 us | 30.88 us | 0.9969 | pass | yes |
sealed |
| front_tp8_m512 | prefill | 46.11 us | 46.21 us | 0.9979 | pass | yes |
sealed |
| front_tp8_m1024 | prefill | 68.45 us | 68.32 us | 1.0019 | pass | yes
| sealed |
| front_tp8_m2048 | prefill | 118.08 us | 118.21 us | 0.9989 | pass |
yes | sealed |
| front_tp8_m4096 | prefill | 235.33 us | 235.50 us | 0.9993 | pass |
yes | sealed |
| front_tp8_m8192 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1477/1965 MHz first, 1462/1965 MHz retry) |
| front_tp8_m16384 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1387/1965 MHz first, 1395/1965 MHz retry) |
| tail_tp1_m1 | decode | 31.55 us | 31.49 us | 1.0020 | pass | yes |
sealed |
| tail_tp1_m2 | decode | 31.58 us | 31.52 us | 1.0020 | pass | yes |
sealed |
| tail_tp1_m4 | decode | 31.68 us | 31.68 us | 1.0000 | pass | yes |
sealed |
| tail_tp1_m8 | decode | 31.81 us | 31.90 us | 0.9970 | pass | yes |
sealed |
| tail_tp1_m16 | decode | 33.76 us | 33.92 us | 0.9953 | pass | yes |
sealed |
| tail_tp1_m32 | decode | 34.34 us | 34.43 us | 0.9972 | pass | yes |
sealed |
| tail_tp1_m64 | decode | 36.48 us | 36.51 us | 0.9991 | pass | yes |
sealed |
| tail_tp1_m128 | decode | 43.01 us | 39.90 us | 1.0778 | pass | yes |
sealed |
| tail_tp1_m256 | prefill | 42.91 us | 42.85 us | 1.0015 | pass | yes |
sealed |
| tail_tp1_m512 | prefill | 56.73 us | 56.70 us | 1.0006 | pass | yes |
sealed |
| tail_tp1_m1024 | prefill | 101.17 us | 101.34 us | 0.9983 | pass | yes
| sealed |
| tail_tp1_m2048 | prefill | 201.82 us | 201.60 us | 1.0011 | pass | yes
| sealed (retry) |
| tail_tp1_m4096 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1575/1965 MHz first, 1560/1965 MHz retry) |
| tail_tp1_m8192 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1402/1965 MHz first, 1417/1965 MHz retry) |
| tail_tp1_m16384 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1342/1965 MHz first, 1357/1965 MHz retry) |
| tail_tp8_m1 | decode | 8.03 us | 8.03 us | 0.9999 | pass | yes |
sealed |
| tail_tp8_m2 | decode | 8.03 us | 8.00 us | 1.0040 | pass | yes |
sealed |
| tail_tp8_m4 | decode | 8.13 us | 8.13 us | 1.0000 | pass | yes |
sealed |
| tail_tp8_m8 | tail_decode_sm_100a | 8.29 us | 8.26 us | 1.0039 | pass
| yes | sealed |
| tail_tp8_m16 | tail_decode_sm_100a | 9.73 us | 10.18 us | 0.9560 |
pass | yes | sealed |
| tail_tp8_m32 | tail_decode_sm_100a | 10.78 us | 10.85 us | 0.9941 |
pass | yes | sealed |
| tail_tp8_m64 | tail_decode_sm_100a | 12.10 us | 12.10 us | 1.0001 |
pass | yes | sealed |
| tail_tp8_m128 | tail_decode_sm_100a | 14.62 us | 14.69 us | 0.9956 |
pass | yes | sealed |
| tail_tp8_m256 | tail_prefill_sm_100a | 15.78 us | 15.68 us | 1.0061 |
pass | yes | sealed |
| tail_tp8_m512 | tail_prefill_sm_100a | 18.75 us | 18.81 us | 0.9967 |
pass | yes | sealed |
| tail_tp8_m1024 | tail_prefill_sm_100a | 26.34 us | 26.30 us | 1.0012 |
pass | yes | sealed |
| tail_tp8_m2048 | tail_prefill_sm_100a | 40.02 us | 40.00 us | 1.0004 |
pass | yes | sealed |
| tail_tp8_m4096 | tail_prefill_sm_100a | 66.02 us | 66.14 us | 0.9980 |
pass | yes | sealed |
| tail_tp8_m8192 | tail_prefill_sm_100a | 116.38 us | 116.19 us | 1.0017
| pass | yes | sealed |
| tail_tp8_m16384 | tail_prefill_sm_100a | 227.01 us | 227.09 us |
0.9996 | pass | yes | sealed |

</details>

<details><summary>sm_103a per-row receipts</summary>

| row (B300, sm_103a) | route | source | export | source / export |
correctness (both arms) | bitwise src == exp | verdict |
|---|---|---|---:|---:|---|---|---|
| front_tp1_m1 | decode | 50.02 us | 50.30 us | 0.9943 | pass | yes |
sealed |
| front_tp1_m2 | decode | 50.11 us | 50.27 us | 0.9968 | pass | yes |
sealed |
| front_tp1_m4 | decode | 50.40 us | 50.47 us | 0.9987 | pass | yes |
sealed |
| front_tp1_m8 | decode | 50.24 us | 50.50 us | 0.9949 | pass | yes |
sealed |
| front_tp1_m16 | decode | 50.78 us | 50.88 us | 0.9981 | pass | yes |
sealed |
| front_tp1_m32 | decode | 51.52 us | 51.59 us | 0.9987 | pass | yes |
sealed |
| front_tp1_m64 | decode | 53.89 us | 53.95 us | 0.9988 | pass | yes |
sealed |
| front_tp1_m128 | decode | 59.17 us | 59.39 us | 0.9962 | pass | yes |
sealed |
| front_tp1_m256 | prefill | 52.10 us | 52.32 us | 0.9957 | pass | yes |
sealed |
| front_tp1_m512 | prefill | 80.87 us | 80.83 us | 1.0004 | pass | yes |
sealed |
| front_tp1_m1024 | prefill | 152.61 us | 153.03 us | 0.9973 | pass |
yes | sealed |
| front_tp1_m2048 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1537/2032 MHz first, 1515/2032 MHz retry) |
| front_tp1_m4096 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1320/2032 MHz first, 1417/2032 MHz retry) |
| front_tp1_m8192 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1282/2032 MHz first, 1290/2032 MHz retry) |
| front_tp1_m16384 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1237/2032 MHz first, 1237/2032 MHz retry) |
| front_tp8_m1 | decode | 21.66 us | 21.73 us | 0.9971 | pass | yes |
sealed |
| front_tp8_m2 | decode | 21.82 us | 21.95 us | 0.9941 | pass | yes |
sealed |
| front_tp8_m4 | decode | 21.70 us | 21.82 us | 0.9942 | pass | yes |
sealed |
| front_tp8_m8 | decode | 21.82 us | 21.95 us | 0.9942 | pass | yes |
sealed |
| front_tp8_m16 | decode | 22.21 us | 22.21 us | 1.0000 | pass | yes |
sealed |
| front_tp8_m32 | decode | 23.33 us | 23.36 us | 0.9986 | pass | yes |
sealed |
| front_tp8_m64 | decode | 25.60 us | 25.70 us | 0.9962 | pass | yes |
sealed |
| front_tp8_m128 | decode | 31.59 us | 31.55 us | 1.0010 | pass | yes |
sealed |
| front_tp8_m256 | prefill | 29.76 us | 29.82 us | 0.9978 | pass | yes |
sealed |
| front_tp8_m512 | prefill | 43.60 us | 43.95 us | 0.9920 | pass | yes |
sealed |
| front_tp8_m1024 | prefill | 65.47 us | 64.83 us | 1.0099 | pass | yes
| sealed |
| front_tp8_m2048 | prefill | 111.78 us | 112.16 us | 0.9966 | pass |
yes | sealed |
| front_tp8_m4096 | prefill | 221.19 us | 221.28 us | 0.9996 | pass |
yes | sealed |
| front_tp8_m8192 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1680/2032 MHz first, 1425/2032 MHz retry) |
| front_tp8_m16384 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1282/2032 MHz first, 1290/2032 MHz retry) |
| tail_tp1_m1 | decode | 31.94 us | 31.74 us | 1.0060 | pass | yes |
sealed |
| tail_tp1_m2 | decode | 31.94 us | 31.78 us | 1.0050 | pass | yes |
sealed |
| tail_tp1_m4 | decode | 32.03 us | 32.00 us | 1.0010 | pass | yes |
sealed |
| tail_tp1_m8 | decode | 32.16 us | 32.16 us | 1.0000 | pass | yes |
sealed |
| tail_tp1_m16 | decode | 33.70 us | 33.86 us | 0.9953 | pass | yes |
sealed |
| tail_tp1_m32 | decode | 34.46 us | 34.53 us | 0.9981 | pass | yes |
sealed |
| tail_tp1_m64 | decode | 36.61 us | 36.61 us | 1.0000 | pass | yes |
sealed |
| tail_tp1_m128 | decode | 42.56 us | 40.03 us | 1.0632 | pass | yes |
sealed |
| tail_tp1_m256 | prefill | 42.62 us | 42.72 us | 0.9978 | pass | yes |
sealed |
| tail_tp1_m512 | prefill | 53.89 us | 53.92 us | 0.9994 | pass | yes |
sealed |
| tail_tp1_m1024 | prefill | 96.48 us | 96.90 us | 0.9957 | pass | yes |
sealed |
| tail_tp1_m2048 | prefill | 185.06 us | 185.27 us | 0.9989 | pass | yes
| sealed |
| tail_tp1_m4096 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1425/2032 MHz first, 1425/2032 MHz retry) |
| tail_tp1_m8192 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1312/2032 MHz first, 1725/2032 MHz retry) |
| tail_tp1_m16384 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1252/2032 MHz first, 1245/2032 MHz retry) |
| tail_tp8_m1 | decode | 7.87 us | 7.90 us | 0.9960 | pass | yes |
sealed |
| tail_tp8_m2 | decode | 8.00 us | 7.97 us | 1.0040 | pass | yes |
sealed |
| tail_tp8_m4 | decode | 7.94 us | 7.97 us | 0.9960 | pass | yes |
sealed |
| tail_tp8_m8 | tail_decode_sm_103a | 8.10 us | 8.10 us | 1.0000 | pass
| yes | sealed |
| tail_tp8_m16 | tail_decode_sm_103a | 9.41 us | 9.82 us | 0.9577 | pass
| yes | sealed |
| tail_tp8_m32 | tail_decode_sm_103a | 10.69 us | 11.10 us | 0.9625 |
pass | yes | sealed |
| tail_tp8_m64 | tail_decode_sm_103a | 11.81 us | 12.32 us | 0.9585 |
pass | yes | sealed |
| tail_tp8_m128 | tail_decode_sm_103a | 14.37 us | 14.40 us | 0.9978 |
pass | yes | sealed |
| tail_tp8_m256 | tail_prefill_sm_103a | 14.88 us | 14.78 us | 1.0065 |
pass | yes | sealed |
| tail_tp8_m512 | tail_prefill_sm_103a | 17.79 us | 17.92 us | 0.9929 |
pass | yes | sealed |
| tail_tp8_m1024 | tail_prefill_sm_103a | 24.32 us | 24.54 us | 0.9909 |
pass | yes | sealed |
| tail_tp8_m2048 | tail_prefill_sm_103a | 37.76 us | 38.11 us | 0.9908 |
pass | yes | sealed |
| tail_tp8_m4096 | tail_prefill_sm_103a | 62.27 us | 62.66 us | 0.9939 |
pass | yes | sealed |
| tail_tp8_m8192 | tail_prefill_sm_103a | 110.88 us | 110.88 us | 1.0000
| pass | yes | sealed |
| tail_tp8_m16384 | tail_prefill_sm_103a | 210.15 us | 210.05 us |
1.0005 | pass | yes | sealed |

</details>

### Measured speedups (Cake contract, paired cold-L2 CUPTI graph timing
vs the fastest stock chain of each row)

Kernel arm = the exported programs of this PR (CUDA-graph form, three
alternating groups, cold-L2 CUPTI timing, correctness of both arms
against the torch reference, graph == eager); denominator = the fastest
stock chain of the row (see Baselines). **B200: 60 / 60 rows > 1.00, min
1.029 (`tail_tp1_m16384`), geomean 1.614. B300: 60 / 60 rows > 1.00, min
1.048 (`tail_tp1_m16384`), geomean 1.624.**

| row | B200: exported program / fastest stock chain us = speedup |
B300: same |
|---|---|---|
| `front_tp1_m1` | 49.85 / 88.06 = 1.766 | 50.40 / 85.60 = 1.698 |
| `front_tp1_m2` | 50.05 / 87.84 = 1.755 | 50.50 / 85.86 = 1.700 |
| `front_tp1_m4` | 50.56 / 88.70 = 1.754 | 51.10 / 87.39 = 1.710 |
| `front_tp1_m8` | 49.92 / 87.42 = 1.751 | 50.37 / 86.50 = 1.717 |
| `front_tp1_m16` | 50.27 / 89.18 = 1.774 | 50.78 / 88.61 = 1.745 |
| `front_tp1_m32` | 51.14 / 90.59 = 1.772 | 51.52 / 90.08 = 1.748 |
| `front_tp1_m64` | 54.27 / 90.78 = 1.673 | 54.56 / 90.53 = 1.659 |
| `front_tp1_m128` | 58.69 / 94.91 = 1.617 | 58.94 / 94.59 = 1.605 |
| `front_tp1_m256` | 52.29 / 115.71 = 2.213 | 52.51 / 114.37 = 2.178 |
| `front_tp1_m512` | 85.38 / 165.34 = 1.937 | 80.61 / 159.49 = 1.979 |
| `front_tp1_m1024` | 166.64 / 289.84 = 1.739 | 152.00 / 266.18 = 1.751
|
| `front_tp1_m2048` | 315.58 / 595.91 = 1.888 | 289.89 / 558.89 = 1.928
|
| `front_tp1_m4096` | 665.27 / 1195.01 = 1.796 | 614.63 / 1168.55 =
1.901 |
| `front_tp1_m8192` | 1324.92 / 2370.06 = 1.789 | 1241.32 / 2318.98 =
1.868 |
| `front_tp1_m16384` | 2576.49 / 4727.88 = 1.835 | 2436.47 / 4587.45 =
1.883 |
| `front_tp8_m1` | 21.73 / 58.21 = 2.679 | 21.76 / 56.54 = 2.598 |
| `front_tp8_m2` | 21.92 / 58.11 = 2.651 | 21.95 / 56.38 = 2.569 |
| `front_tp8_m4` | 21.86 / 57.85 = 2.647 | 21.70 / 55.84 = 2.574 |
| `front_tp8_m8` | 21.86 / 57.28 = 2.621 | 21.79 / 55.46 = 2.545 |
| `front_tp8_m16` | 22.21 / 57.76 = 2.601 | 22.21 / 56.48 = 2.543 |
| `front_tp8_m32` | 23.49 / 61.86 = 2.634 | 23.55 / 60.64 = 2.575 |
| `front_tp8_m64` | 25.66 / 60.93 = 2.374 | 25.66 / 59.78 = 2.329 |
| `front_tp8_m128` | 31.68 / 63.46 = 2.003 | 31.84 / 62.46 = 1.962 |
| `front_tp8_m256` | 30.78 / 73.18 = 2.377 | 29.86 / 71.33 = 2.389 |
| `front_tp8_m512` | 46.18 / 79.33 = 1.718 | 43.84 / 77.31 = 1.764 |
| `front_tp8_m1024` | 68.61 / 106.94 = 1.559 | 64.87 / 102.94 = 1.587 |
| `front_tp8_m2048` | 118.37 / 172.57 = 1.458 | 111.71 / 163.23 = 1.461
|
| `front_tp8_m4096` | 241.10 / 324.70 = 1.347 | 222.05 / 306.08 = 1.378
|
| `front_tp8_m8192` | 488.30 / 649.51 = 1.330 | 460.28 / 636.07 = 1.382
|
| `front_tp8_m16384` | 991.51 / 1324.85 = 1.336 | 871.85 / 1252.93 =
1.437 |
| `tail_tp1_m1` | 31.36 / 39.78 = 1.268 | 31.71 / 39.11 = 1.233 |
| `tail_tp1_m2` | 31.45 / 39.49 = 1.255 | 31.65 / 39.78 = 1.257 |
| `tail_tp1_m4` | 31.65 / 40.26 = 1.272 | 31.78 / 40.51 = 1.275 |
| `tail_tp1_m8` | 31.74 / 40.06 = 1.262 | 31.94 / 40.54 = 1.270 |
| `tail_tp1_m16` | 33.92 / 39.23 = 1.157 | 33.83 / 39.52 = 1.168 |
| `tail_tp1_m32` | 34.43 / 39.68 = 1.152 | 34.59 / 39.84 = 1.152 |
| `tail_tp1_m64` | 36.48 / 40.42 = 1.108 | 36.70 / 41.02 = 1.118 |
| `tail_tp1_m128` | 40.03 / 45.09 = 1.126 | 40.13 / 45.03 = 1.122 |
| `tail_tp1_m256` | 42.88 / 49.41 = 1.152 | 42.72 / 49.41 = 1.157 |
| `tail_tp1_m512` | 56.32 / 71.84 = 1.276 | 53.86 / 68.64 = 1.274 |
| `tail_tp1_m1024` | 101.47 / 122.85 = 1.211 | 96.90 / 115.49 = 1.192 |
| `tail_tp1_m2048` | 205.82 / 217.31 = 1.056 | 191.91 / 202.15 = 1.053 |
| `tail_tp1_m4096` | 421.95 / 436.64 = 1.035 | 393.29 / 415.69 = 1.057 |
| `tail_tp1_m8192` | 841.40 / 885.22 = 1.052 | 806.11 / 873.68 = 1.084 |
| `tail_tp1_m16384` | 1694.77 / 1743.58 = 1.029 | 1644.86 / 1723.75 =
1.048 |
| `tail_tp8_m1` | 8.10 / 16.19 = 2.000 (2.000) | 7.94 / 15.90 = 2.004
(1.996) |
| `tail_tp8_m2` | 8.06 / 17.15 = 2.127 (2.127) | 7.90 / 16.80 = 2.126
(2.126) |
| `tail_tp8_m4` | 8.10 / 17.31 = 2.138 (2.138) | 7.94 / 17.15 = 2.161
(2.161) |
| `tail_tp8_m8` | 8.22 / 16.64 = 2.023 (2.023) | 8.10 / 16.51 = 2.040
(2.043) |
| `tail_tp8_m16` | 10.59 / 18.11 = 1.710 (1.710) | 9.22 / 17.95 = 1.948
(1.941) |
| `tail_tp8_m32` | 10.91 / 17.73 = 1.625 (1.625) | 10.69 / 17.54 = 1.641
(1.641) |
| `tail_tp8_m64` | 12.22 / 19.33 = 1.581 (1.581) | 12.16 / 19.17 = 1.576
(1.576) |
| `tail_tp8_m128` | 14.59 / 20.16 = 1.382 | 14.40 / 19.87 = 1.380 |
| `tail_tp8_m256` | 15.55 / 22.43 = 1.442 | 14.72 / 21.70 = 1.474 |
| `tail_tp8_m512` | 18.88 / 27.58 = 1.461 | 17.76 / 26.94 = 1.517 |
| `tail_tp8_m1024` | 26.11 / 36.61 = 1.402 | 24.29 / 35.39 = 1.457 |
| `tail_tp8_m2048` | 39.81 / 51.04 = 1.282 | 37.38 / 49.47 = 1.324 |
| `tail_tp8_m4096` | 65.82 / 95.97 = 1.458 | 62.46 / 91.94 = 1.472 |
| `tail_tp8_m8192` | 119.74 / 184.90 = 1.544 | 110.95 / 175.62 = 1.583 |
| `tail_tp8_m16384` | 245.63 / 357.53 = 1.456 | 221.76 / 338.18 = 1.525
|

Values in parentheses: the same row in the additional independent
process(es) of the short-row re-measurement (tail TP8 T <= 32 at 300 ms
per arm, T = 64 at 250 ms per arm; the default window of these rows
exceeds the protocol's sample cap, so they are timed only in these
dedicated processes).

### Baselines and their source PRs

- **Stock chain (Cake contract denominator, per row the fastest of):**
torch / cuBLAS `torch.mm` / `torch.addmm` (FP32-upcast or
`out_dtype=float32` router GEMM, BF16 latent / shared GEMMs, `addmm` for
the tail sum) and every FlashInfer `mm_bf16` backend that computes the
product (`auto`, `cudnn`, `cublaslt`, `tgv`, `tinygemm`, `cutlass`,
`cute-dsl`), `flashinfer.rmsnorm` for the tail norm, torch `silu` /
`mul` / `topk` for the elementwise steps; same chain and same shapes as
#5575 / #5584 / #5647 / #5671 / #5721.
- **Previous rounds of this operator (the programs this PR replaces):**
#5721 (82e8eb141, 2026-09-30), #5671 (3a3fb9aa5, 2026-09-29), #5647
(443347d3e, 2026-09-28), #5584 (1eb503cd3, 2026-09-27), #5575 (initial
package); the exported-program contract of #5721 is the per-row
comparison baseline (no row may regress by more than 2 % against it
without a same-node attribution).
- **Operator semantics reference:** `nvidia/Kimi-K3-NVFP4`
`modeling_kimi_linear.py` (`KimiSparseMoeBlock`, `KimiMLP`,
`KimiRMSNorm`, `SituAndMul`, `KimiMoEGate`); serving layout from vLLM
`models/kimi_k3/nvidia/{model.py, latent_moe_runner.py,
low_latency_gemm.py}` and SGLang `srt/models/kimi_k3.py`.
- **Test oracle:** the torch reference in
`tests/experimental/test_cake_kimi_k3_latent_moe.py` (transcribed from
the Cake reference module).
- **Merge-base:** upstream `main` aafe22ff6 (#5444, 2026-09-30); no
upstream change to the package between #5721 and this branch.

## Test

```
pytest tests/experimental/test_cake_kimi_k3_latent_moe.py
```

`pytest tests/experimental/test_cake_kimi_k3_latent_moe.py`: **40
passed, 24 warnings in 14.18s (B200) / 40 passed, 24 warnings in 8.29s
(B300)** on B200 (sm_100a) and on B300 (sm_103a), run on the delivered
tree in the export clone of each GPU (plan / route tests incl. the new
`t1` keys + GPU correctness for both stages x TP {1, 8} x the row set,
bit-identical re-launch and CUDA-graph replay, `y` byte-exact).
Producer-side gates on the same kernel tree: poisoned pre-check of the
new store path (9 rows x NaN / +huge / -huge fills of the output, the
latent workspace and the stream-K slots; output bitwise vs the
direct-store path), e2e GPU + no-GPU test slices (only the pre-existing
exempt tp12 analysis pair fails, as on main), unit tests,
compute-sanitizer synccheck + memcheck 0 errors (registered witnesses +
a split-row supplement), bench-regression rc 0, four 62-row contract
passes per GPU (62 / 62 correct, 53 / 53 gated rows faster than the
stock chain in every pass) and the seven sub-15 us rows in two
independent processes per GPU.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Performance**
* Optimized final output writes for eligible Kimi K3 latent MoE
workloads using staged tensor-memory transfers. The 128-wide TP8,
512-token configuration retains direct stores.
* **Compatibility**
* Updated generated kernel variants and launch paths to support the
optimized output handling across supported configurations.
* **Tests**
* Added coverage for the updated tail GEMM configuration and route
selection.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <yyihuang@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [6fd8900](https://github.com/flashinfer-ai/flashinfer/commit/6fd8900473dd29f6441a36a54e8fcb09797ec82a)

- **作者**: eigen
- **时间**: 2026-09-30T21:49:08Z
- **提交信息**: perf(cake_mm_fp4): tactic rules and regenerated programs for the per-token NVFP4 route (#5744)

<!-- .github/pull_request_template.md -->

## 📌 Description

Tactic-rule and program update of the experimental `backend="cake"`
per-token NVFP4 route (#5697): six measured levers on the host tactic
rules and the generated programs, no public API, default or
backend-semantics change, no approximation, outputs bitwise identical to
the merged route on every measured row (quantizer: identical programs or
a store-policy-only change; GEMM: `torch.equal` against the merged route
on every A/B row of both GPUs, including the split-K 3 rows whose K
partition differs from the merged split-K 2).

1. **Wave-cost tile width for multi-wave 2-CTA rows**
(`_two_cta_tile_n`): on rows with more 256-token x tile_n units than CTA
pairs, tile_n is re-picked in {128, 192, 256} by ceil(units / pairs) x
the measured per-tile wave cost {0.575, 0.787, 1.0}, switching only for
a modelled gain >= 1.5 %. Changes 8192x8192 and 28672x8192 M = 2048 to
192 on both GPUs, plus 16384x7168 / 18432x7168 M = 2048 and 8192x28672 M
= 257 / 512 on the 148-SM part: +1.0..+2.8 %.
2. **Grouped raster only for multi-wave grids** (`raster_group` 8 / 16
iff units > pairs): the 8-tile group costs 1-2 % when every tile of the
grid runs concurrently; single-wave 2-CTA rows (7168x1536 M = 130-2048,
7168x2112 M = 2048, 8192x8192 and 28672x8192 M = 257 / 512, ...) now run
ungrouped: +1..+2 %.
3. **Split-K 2 for the narrow token tiles at K >= 16384** (`n8_sk2` /
`n32_sk2` cluster programs) when 2 x n_tiles <= SMs and (K == 16384 or
the 32-token tile): 16384x7168 M = 1-32, 18432x7168 and 28672x8192 M =
17 / 32: +0.4..+3.4 %.
4. **Split-K 3 from cluster co-residency** (`n8_sk3`): the split-K
launch is `weight tiles x token tiles` clusters that must all be
co-resident; the driver's `cuOccupancyMaxActiveClusters` for the split-K
program (`CLUSTER_CAPACITY_BY_SM_COUNT`, 148 / 152 SMs, re-checked at
prepare time) predicts every measured verdict. 8 < M <= 32 rows on the
8-wide token tile take three K slices when the cluster grid fits; on the
grid that is 7168x1536 M = 17 (3 x 12 clusters of 3): +5.8..+6.6 % on
both GPUs. Every deeper split that does not fit was measured and loses
6-70 %.
5. **Evict-last stores for the quantizer outputs of the >= 512-row CTA
configurations**: the quantizer streams its input once and writes 5/16
of it; with the default policy the read stream's evictions force the
fresh outputs back to HBM inside the kernel (Nsight: 17.1 MB of
in-kernel DRAM writes on 16384x8192, 7.7 MB with the hint). Marking the
output stores `L2::evict_last` keeps them for the dependent GEMM:
+3..+12 % on every M = 2048 / 8192 row of both GPUs (reset-flush cold-L2
bench; rotating-output-buffer control excludes residue), M = 512
+0..+2.7 %. Scoped to the CTA configurations the `>= 512 rows` branch
picks per K (registry keys disjoint from the small-row programs), so the
M < 512 programs are byte-identical to #5697. One measured residual: the
8192x28672 M = 512 quantizer -> GEMM chain on GB300 is 0.3-0.5 % slower
(the same row is +1.8..+2.0 % on B200; all other M = 512 chains gain);
kept, documented in the design doc.
6. **No L2 promotion on one-wave 128-wide rows** (the one-token-tile
branch loses its SM-count condition): when one wave of 128-wide weight
tiles streams the operand exactly once (7168x18432 M = 128, 144 tiles),
the 256 B TMA promotion is pure overhead; the L2-off descriptors are
ahead of the promoted default in seven paired comparisons on both build
arms on B200 (+0.35..+0.9 %, export arm vs the merged default 1.0055
fp16 / 1.0037 bf16), the same 0.1 us the GB300 rule measured. Kernel
source unchanged (host descriptor attribute only). Changes one row on
B200.

Regenerated programs: the `sk2` / `sk3` cluster GEMM programs, the
192-wide 2-CTA programs, the L2-off `m128` programs on sm_100a and the
large-row quantizer programs (both arches); every other generated source
is byte-identical to #5697 (drift diff in the evidence: 60 / 66
unchanged kernel sources per arch, 17 quantizer sources changed by the
one store-policy line, all non-kernel module files unchanged; the module
names differ because the exporter hashes its own version). Rows whose
candidate program differs from #5697 are marked `*` in the tables;
unmarked rows launch the same source built twice on the two arms and
measure the instrument (ties).

## Baselines and their source PRs

- #5697 (merged; `flashinfer/experimental/cake_nvfp4_per_token`): the
`backend="cake"` per-token route this PR updates. **Progress baseline**
(arm A of the progress tables): its generated programs and tactic rules,
unmodified, in the same process as this PR's programs.
- #5609 `97b3bd80` (merged): CuTe-DSL per-token kernel optimisations;
`backend="cute-dsl"` with the untuned default tactic is the **threshold
baseline** of the threshold tables.
- #5504 `7d967939` (merged): per-token alpha `mm_fp4` + `out_scale` fold
in per-token `nvfp4_quantize` (the API both routes implement).

## Methodology

Container `sglang:26.07-py3`, single tenant, cold L2 (persisting lines
reset before each flush), CUPTI kernel spans, 100 iterations per timing,
6 paired rounds per row with the arm order alternated (base, cand, cand,
base). Statistics per row: min over rounds, median of round medians,
geometric mean; the acceptance statistic is the min-of-round-medians
ratio for the GEMM and fused tables and the median of round medians for
the quantizer. Shapes: (K, N) in {(7168,2112), (7168,1536),
(16384,7168), (7168,18432), (18432,7168), (8192,8192), (8192,28672),
(28672,8192)} x M in {1, 8, 17, 32, 128, 130, 257, 512, 2048, 8192},
128x4 SF, bf16 and fp16 outputs; quantizer over the same M x K grid with
and without the `out_scale` fold. Progress tables: both arms are
nvcc-built generated programs loaded in one process (unchanged rows
launch byte-identical sources). Fused table: quantizer + GEMM chain
replayed from a CUDA graph (PDL edges included), eager spans as
auxiliary. Roofline share per row against measured peaks (dense FP4
microbenchmark, HBM copy bandwidth, launch floor), not data-sheet
numbers.

## Results

Cell format: `acceptance(median/geomean)` for the GEMM and fused tables
(acceptance = min-of-round-medians ratio, median = ratio of the medians
of the round medians, geomean = ratio of the geometric means) and
`acceptance(min/geomean)` for the quantizer (acceptance = median of the
round ratios, min = min-of-round-medians ratio). `*` after the tactic =
the candidate program differs from #5697 on that row; unmarked rows run
byte-identical programs on both arms (ties: the residual is the
instrument's, see the design doc for the A/A control). `roof` = share of
the measured peak (`c` compute, `h` HBM) and, for rows under 6 launch
floors, the row time in launch floors (`Nf`). Full per-row JSON (round
medians, per-kernel spans, bitwise flags) and the complete A/B record
including every negative result are kept in the Cake team's design
notes.

### Speedup summary

Geometric means over all rows of each table (acceptance statistic per
row, 6-12 alternating rounds x 100 iterations, cold L2, CUPTI spans):

| table | GPU | vs #5697 (merged cake route) | vs cute-dsl per-token
(untuned default) |
|---|---|---|---|
| GEMM per-token | B200 | bf16 1.0050 / fp16 1.0051 (min 0.9950 /
0.9954) | bf16 1.0549 / fp16 1.0548 (min 1.0028 / 1.0018) |
| GEMM per-token | GB300 | bf16 1.0047 / fp16 1.0045 (min 0.9970 /
0.9981) | bf16 1.0509 / fp16 1.0508 (min 0.9996 / 1.0021) |
| Fused quantize + GEMM chain | B200 | bf16 1.0096 / fp16 1.0099 (min
0.9950) | bf16 1.0885 (min 1.0047) |
| Fused quantize + GEMM chain | GB300 | bf16 1.0074 / fp16 1.0077 (min
0.9863 / 0.9909) | bf16 1.0904 (min 1.0024) |
| Quantize kernel | B200 | bf16 1.0156 (min 0.9996) / fp16 1.0088 | bf16
1.1258 (min 1.0175) / fp16 1.1150 |
| Quantize kernel | GB300 | bf16 1.0143 (min 0.9958) / fp16 1.0047 |
bf16 1.1233 (min 1.0090) / fp16 1.1115 |

- vs the cute-dsl baseline every row of every table on both GPUs is >
1.00 except GB300 GEMM bf16 7168x18432 M = 8192 at 0.9996 (12 rounds;
both routes at 90-91 % of the measured dense-FP4 peak, 14 tactic
variants all lose - a hardware-limit tie).
- vs #5697 the gains sit on the rows whose program changed (marked `*`
below): quantizer M = 2048 / 8192 rows +3..+12 % (evict-last output
stores), 7168x1536 M = 17 +5.6..+6.6 % (three-slice cluster split-K),
multi-wave 2-CTA rows +1..+2.8 % (192-wide tiles, ungrouped raster), K
>= 16384 narrow rows +0.4..+3.4 % (split-K 2). About half of the rows
run byte-identical programs on both arms and read 0.995-1.00: ties of
the instrument (the GB300 fused-chain minima 0.986-0.991 on M = 1 / 8
chains reproduce in an A/A run of the #5697 package against itself). The
lever-6 row on B200 is a one-CUPTI-tick tie against the promoted program
(GEMM 0.9982, fused 0.9950).
- Where the rows stand against the measured hardware: large-M
compute-bound GEMM rows at 82-93 % of the measured dense-FP4 peak (both
GPUs); one-wave weight-streaming rows (M = 128 class) at 55-80 % of the
measured HBM bandwidth (pipeline fill and tail of a single wave, not
bandwidth); M <= 32 rows at 2-6 launch floors (14-25 % of HBM bandwidth
for the GEMM, 12-35 % for the quantizer) - latency-bound, where the
remaining headroom would need a fused single-kernel quantize + GEMM or
deeper PDL overlap, both outside this PR's no-API-change scope; large-M
quantizer rows at 93-95 % of HBM bandwidth.

### GB300 (sm_103a, 152 SMs)

<details>
<summary>GB300 tables: quantizer, GEMM, fused chain (click to
expand)</summary>

#### GEMM per-token — vs #5697: bf16 rows 80, geomean 1.0047, min
0.9970, rows <= 1.00: 40; fp16 rows 80, geomean 1.0045, min 0.9981, rows
<= 1.00: 43. vs cute-dsl: bf16 rows 80, geomean 1.0509, min 0.9996, rows
<= 1.00: 1; fp16 rows 80, geomean 1.0508, min 1.0021, rows <= 1.00: 0

|K|N|M|tactic|vs #5697 bf16|vs #5697 fp16|vs cute-dsl bf16|vs cute-dsl
fp16|roof (share of measured peak; Nf = N x launch floor)|
|---|---|---|---|---|---|---|---|---|

|7168|2112|1|n8sk4|1.000(1.000/1.000)|1.000(1.000/0.999)|1.022(1.028/1.025)|1.022(1.028/1.025)|22%h
4.6f|

|7168|2112|8|n8sk4|1.000(1.000/1.000)|1.000(1.000/0.999)|1.022(1.022/1.021)|1.016(1.022/1.021)|22%h
4.6f|

|7168|2112|17|n8sk2|1.000(1.000/1.000)|1.000(1.005/1.001)|1.031(1.036/1.033)|1.031(1.036/1.033)|24%h
4.3f|

|7168|2112|32|n8sk2|1.000(1.000/0.999)|1.005(1.000/1.001)|1.031(1.031/1.031)|1.036(1.031/1.031)|21%h
5.1f|

|7168|2112|128|2xm64|1.000(1.000/1.000)|1.000(1.000/1.000)|1.049(1.049/1.048)|1.049(1.049/1.050)|18%h|

|7168|2112|130|2xm64|1.000(1.004/1.000)|1.000(1.000/1.000)|1.041(1.040/1.042)|1.045(1.040/1.041)|20%h
5.6f|

|7168|2112|257|2xm64|1.004(1.004/1.001)|1.000(1.000/1.000)|1.044(1.044/1.046)|1.044(1.048/1.047)|22%h
5.8f|

|7168|2112|512|2xm64|1.000(1.000/0.998)|1.000(1.000/1.000)|1.047(1.047/1.046)|1.039(1.047/1.044)|23%h|

|7168|2112|2048*|2xm256|1.012(1.010/1.011)|1.010(1.010/1.010)|1.037(1.040/1.039)|1.035(1.040/1.038)|60%c|

|7168|2112|8192|2xm192g8|0.999(1.001/1.000)|1.002(1.000/0.999)|1.025(1.025/1.025)|1.025(1.025/1.024)|74%c|

|7168|1536|1|n8sk4|1.000(1.000/1.000)|1.000(1.000/1.001)|1.024(1.024/1.023)|1.024(1.024/1.025)|17%h
4.4f|

|7168|1536|8|n8sk4|1.000(1.000/1.000)|1.000(1.000/1.000)|1.024(1.029/1.025)|1.024(1.024/1.023)|17%h
4.4f|

|7168|1536|17*|n8sk3|1.064(1.064/1.065)|1.058(1.064/1.063)|1.082(1.088/1.085)|1.082(1.082/1.082)|18%h
4.1f|

|7168|1536|32|n8sk2|1.000(0.995/0.999)|1.000(1.005/1.001)|1.022(1.027/1.025)|1.022(1.027/1.025)|16%h
4.7f|

|7168|1536|128|2xm64|1.000(1.000/1.000)|1.000(1.000/1.000)|1.055(1.055/1.056)|1.060(1.059/1.058)|14%h|

|7168|1536|130|2xm64|1.017(1.017/1.018)|1.017(1.017/1.016)|1.042(1.047/1.044)|1.038(1.042/1.043)|15%h
5.6f|

|7168|1536|257|2xm64|1.021(1.017/1.018)|1.021(1.017/1.018)|1.046(1.042/1.044)|1.042(1.046/1.044)|17%h
5.7f|

|7168|1536|512|2xm64|1.021(1.017/1.018)|1.017(1.017/1.018)|1.046(1.046/1.047)|1.046(1.046/1.045)|19%h|

|7168|1536|2048*|2xm192|1.012(1.012/1.012)|1.015(1.012/1.026)|1.050(1.050/1.051)|1.050(1.053/1.054)|53%c|

|7168|1536|8192|2xm256g8|1.000(1.000/1.000)|1.000(1.000/1.000)|1.056(1.057/1.057)|1.056(1.056/1.057)|70%c|

|16384|7168|1*|n8sk2|1.004(1.004/1.008)|1.004(1.006/1.006)|1.126(1.125/1.126)|1.128(1.125/1.126)|66%h|

|16384|7168|8*|n8sk2|1.004(1.004/1.004)|1.004(1.004/1.005)|1.134(1.131/1.133)|1.132(1.132/1.131)|67%h|

|16384|7168|17*|n32sk2|1.031(1.029/1.029)|1.031(1.029/1.030)|1.155(1.153/1.152)|1.151(1.155/1.154)|65%h|

|16384|7168|32*|n32sk2|1.033(1.035/1.034)|1.027(1.027/1.028)|1.143(1.145/1.145)|1.150(1.150/1.149)|64%h|

|16384|7168|128|m64|0.998(1.000/0.999)|1.002(1.000/1.001)|1.020(1.020/1.021)|1.020(1.022/1.021)|59%h|

|16384|7168|130|2xm128|1.000(1.000/1.000)|1.002(1.002/1.001)|1.048(1.050/1.049)|1.048(1.050/1.050)|57%h|

|16384|7168|257|2xm192|0.998(1.000/0.999)|1.000(1.000/0.999)|1.035(1.038/1.037)|1.034(1.035/1.035)|51%h|

|16384|7168|512|2xm192|1.001(1.000/1.000)|0.999(1.001/1.000)|1.044(1.043/1.043)|1.040(1.040/1.040)|68%c|

|16384|7168|2048|2xm256g8|1.004(1.001/1.002)|1.000(1.000/0.999)|1.020(1.019/1.019)|1.021(1.019/1.019)|89%c|

|16384|7168|8192|2xm256g16clc|1.000(0.997/0.999)|0.999(0.998/1.000)|1.108(1.110/1.109)|1.110(1.106/1.108)|93%c|

|7168|18432|1|n8s3|1.000(0.998/0.999)|1.000(1.000/1.001)|1.039(1.039/1.039)|1.043(1.041/1.040)|70%h|

|7168|18432|8|n8s3|1.002(1.000/0.999)|1.002(1.000/1.001)|1.043(1.043/1.043)|1.045(1.045/1.045)|70%h|

|7168|18432|17|n32s3|1.000(1.000/1.000)|1.000(1.000/1.001)|1.022(1.024/1.023)|1.026(1.026/1.027)|71%h|

|7168|18432|32|n32s3|0.998(1.000/1.000)|1.000(1.000/1.001)|1.020(1.022/1.021)|1.020(1.022/1.020)|71%h|

|7168|18432|128|m128l2n|1.002(1.000/1.001)|0.998(1.002/1.000)|1.006(1.006/1.004)|1.004(1.006/1.004)|70%h|

|7168|18432|130|2xm256|1.000(1.000/1.000)|0.998(1.000/1.000)|1.027(1.027/1.027)|1.025(1.025/1.025)|67%h|

|7168|18432|257|2xm256|1.001(1.000/1.000)|1.000(1.001/1.000)|1.042(1.041/1.041)|1.040(1.040/1.040)|53%h|

|7168|18432|512|2xm256|0.997(1.000/1.000)|0.999(1.000/0.999)|1.035(1.033/1.034)|1.035(1.035/1.034)|66%c|

|7168|18432|2048|2xm256|1.001(1.000/1.000)|0.999(1.001/0.999)|1.015(1.015/1.015)|1.015(1.012/1.012)|83%c|

|7168|18432|8192|2xm256clc|1.002(1.001/1.000)|0.999(0.999/0.994)|1.000(0.999/1.000)|1.002(1.000/1.001)|91%c|

|18432|7168|1|n8|1.004(1.000/1.000)|1.000(1.000/1.001)|1.123(1.122/1.122)|1.122(1.122/1.122)|67%h|

|18432|7168|8|n8|0.998(0.998/0.999)|1.000(1.000/1.000)|1.124(1.122/1.123)|1.124(1.124/1.124)|67%h|

|18432|7168|17*|n32sk2|1.024(1.022/1.023)|1.026(1.024/1.026)|1.158(1.156/1.156)|1.152(1.154/1.154)|65%h|

|18432|7168|32*|n32sk2|1.026(1.024/1.025)|1.026(1.024/1.026)|1.152(1.151/1.153)|1.154(1.151/1.152)|65%h|

|18432|7168|128|m64|1.002(1.000/1.000)|1.000(1.002/1.001)|1.026(1.025/1.025)|1.026(1.024/1.025)|61%h|

|18432|7168|130|2xm128|1.000(1.000/1.000)|0.998(1.000/0.999)|1.052(1.052/1.053)|1.052(1.052/1.052)|58%h|

|18432|7168|257|2xm192|1.001(0.999/1.000)|1.001(1.000/1.000)|1.042(1.042/1.041)|1.039(1.040/1.041)|52%h|

|18432|7168|512|2xm192|1.000(1.000/1.000)|0.999(1.001/1.000)|1.045(1.044/1.044)|1.044(1.046/1.045)|70%c|

|18432|7168|2048|2xm256g8|0.999(1.000/0.999)|0.999(1.000/1.000)|1.016(1.015/1.015)|1.018(1.017/1.018)|89%c|

|18432|7168|8192|2xm256g16clc|1.000(1.003/1.003)|1.001(1.000/0.999)|1.109(1.112/1.110)|1.112(1.112/1.110)|93%c|

|8192|8192|1|n8|1.000(1.000/1.001)|1.000(1.000/1.000)|1.009(1.012/1.010)|1.012(1.009/1.010)|55%h|

|8192|8192|8|n8|1.000(1.000/0.999)|1.003(1.000/1.000)|1.019(1.015/1.018)|1.019(1.019/1.017)|55%h|

|8192|8192|17|n32|1.003(1.000/1.000)|1.003(0.997/0.996)|1.015(1.018/1.017)|1.015(1.015/1.015)|55%h|

|8192|8192|32|n32|0.997(1.000/1.000)|1.000(1.000/0.998)|1.015(1.015/1.014)|1.015(1.015/1.014)|54%h|

|8192|8192|128|m64|1.000(1.000/0.999)|1.000(1.000/1.000)|1.014(1.014/1.014)|1.017(1.014/1.014)|53%h|

|8192|8192|130|2xm128|1.000(1.000/1.000)|1.000(0.997/1.000)|1.049(1.048/1.050)|1.051(1.051/1.052)|52%h|

|8192|8192|257|2xm256|1.008(1.011/1.009)|1.008(1.008/1.009)|1.036(1.038/1.038)|1.038(1.038/1.038)|43%h|

|8192|8192|512|2xm256|1.008(1.010/1.009)|1.008(1.008/1.009)|1.040(1.037/1.037)|1.037(1.037/1.037)|55%c|

|8192|8192|2048*|2xm192|1.020(1.020/1.020)|1.023(1.020/1.021)|1.053(1.051/1.052)|1.052(1.052/1.051)|76%c|

|8192|8192|8192|2xm256g16clc|1.003(0.999/1.000)|1.003(0.999/1.000)|1.003(1.002/1.003)|1.005(1.002/1.003)|89%c|

|8192|28672|1|n8|1.001(0.999/1.000)|1.000(1.000/1.000)|1.007(1.006/1.006)|1.007(1.006/1.010)|80%h|

|8192|28672|8|n8|1.001(1.000/1.001)|1.000(1.000/1.000)|1.009(1.012/1.010)|1.008(1.008/1.008)|80%h|

|8192|28672|17|n32|1.000(1.000/1.000)|1.000(1.000/0.999)|1.017(1.015/1.016)|1.014(1.014/1.014)|80%h|

|8192|28672|32|n32|0.999(1.000/0.999)|1.000(1.000/1.000)|1.014(1.015/1.015)|1.008(1.008/1.008)|80%h|

|8192|28672|128|m192|1.002(1.001/1.001)|1.000(1.000/1.000)|1.003(0.998/0.998)|1.011(1.008/1.009)|77%h|

|8192|28672|130|2xm192|0.999(0.999/0.999)|1.000(1.000/1.000)|1.018(1.020/1.019)|1.016(1.019/1.018)|76%h|

|8192|28672|257|2xm256|1.000(0.999/1.000)|1.001(0.999/1.000)|1.035(1.034/1.034)|1.034(1.034/1.034)|59%h|

|8192|28672|512|2xm256|0.998(0.999/0.999)|0.999(1.000/1.000)|1.035(1.035/1.035)|1.034(1.033/1.033)|75%c|

|8192|28672|2048|2xm256clc|0.999(0.999/1.000)|1.001(1.000/1.000)|1.011(1.010/1.011)|1.010(1.011/1.011)|90%c|

|8192|28672|8192|2xm256clc|1.000(1.001/1.000)|1.000(1.001/1.001)|1.006(1.005/1.005)|1.008(1.007/1.007)|93%c|

|28672|8192|1|n8|1.001(1.001/1.001)|1.000(0.999/0.999)|1.195(1.195/1.196)|1.189(1.188/1.188)|78%h|

|28672|8192|8|n8|1.000(0.997/0.999)|1.001(1.000/1.000)|1.188(1.184/1.185)|1.186(1.187/1.186)|78%h|

|28672|8192|17*|n32sk2|1.009(1.006/1.006)|1.007(1.005/1.006)|1.195(1.195/1.195)|1.196(1.195/1.195)|76%h|

|28672|8192|32*|n32sk2|1.012(1.011/1.011)|1.014(1.012/1.013)|1.195(1.194/1.194)|1.195(1.193/1.194)|76%h|

|28672|8192|128|m64|1.000(1.000/1.001)|1.002(0.999/1.000)|1.020(1.019/1.020)|1.022(1.019/1.020)|71%h|

|28672|8192|130|2xm128|1.001(1.001/1.001)|1.000(1.000/1.000)|1.037(1.037/1.037)|1.036(1.036/1.036)|69%h|

|28672|8192|257|2xm256|1.002(1.003/1.003)|1.006(1.004/1.005)|1.032(1.033/1.033)|1.033(1.032/1.044)|53%h|

|28672|8192|512|2xm256|1.006(1.004/1.004)|1.004(1.003/1.004)|1.042(1.040/1.041)|1.039(1.039/1.039)|72%c|

|28672|8192|2048*|2xm192|1.024(1.022/1.022)|1.021(1.024/1.023)|1.026(1.027/1.027)|1.030(1.028/1.028)|82%c|

|28672|8192|8192|2xm256g8clc|1.002(1.003/1.001)|1.001(1.000/1.001)|1.100(1.100/1.101)|1.098(1.101/1.104)|91%c|

#### Fused quantize + GEMM chain (CUDA-graph replay, PDL edge included)
— vs #5697: bf16 rows 80, geomean 1.0074, min 0.9863, rows <= 1.00: 28;
fp16 rows 80, geomean 1.0077, min 0.9909, rows <= 1.00: 27. vs cute-dsl
(bf16): rows 80, geomean 1.0904, min 1.0024, rows <= 1.00: 0

|K|N|M|GEMM tactic|vs #5697 bf16|vs #5697 fp16|vs cute-dsl bf16|
|---|---|---|---|---|---|---|

|7168|2112|1|n8sk4|0.987(0.975/0.983)|0.996(0.979/0.986)|1.099(1.092/1.098)|

|7168|2112|8|n8sk4|1.013(0.987/1.000)|1.013(0.983/1.000)|1.140(1.119/1.136)|

|7168|2112|17|n8sk2|0.996(0.988/0.999)|1.000(0.992/1.001)|1.128(1.138/1.145)|

|7168|2112|32|n8sk2|1.012(1.004/1.008)|1.016(1.008/1.009)|1.138(1.146/1.142)|

|7168|2112|128|2xm64|1.000(0.990/0.995)|1.000(0.990/0.995)|1.116(1.129/1.129)|

|7168|2112|130|2xm64|1.000(0.994/0.998)|1.003(0.994/0.998)|1.123(1.114/1.109)|

|7168|2112|257|2xm64|0.997(1.015/1.005)|1.003(1.015/1.008)|1.108(1.129/1.122)|

|7168|2112|512*|2xm64|1.015(1.009/1.012)|1.015(1.009/1.011)|1.137(1.126/1.131)|

|7168|2112|2048*|2xm256|1.020(1.012/1.014)|1.019(1.014/1.016)|1.223(1.216/1.217)|

|7168|2112|8192*|2xm192g8|1.040(1.040/1.040)|1.038(1.040/1.040)|1.051(1.059/1.057)|

|7168|1536|1|n8sk4|0.986(0.973/0.982)|0.991(0.978/0.987)|1.073(1.099/1.101)|

|7168|1536|8|n8sk4|1.009(1.032/1.018)|1.009(1.023/1.020)|1.140(1.138/1.139)|

|7168|1536|17*|n8sk3|1.040(1.035/1.039)|1.036(1.035/1.036)|1.145(1.146/1.151)|

|7168|1536|32|n8sk2|1.004(1.008/1.006)|1.004(1.004/1.005)|1.104(1.102/1.105)|

|7168|1536|128|2xm64|1.003(0.990/0.995)|0.997(1.000/0.998)|1.103(1.113/1.109)|

|7168|1536|130|2xm64|1.031(1.034/1.033)|1.034(1.037/1.033)|1.099(1.105/1.094)|

|7168|1536|257|2xm64|1.003(1.016/1.011)|1.003(1.016/1.011)|1.070(1.091/1.081)|

|7168|1536|512*|2xm64|1.015(1.006/1.007)|1.018(1.003/1.007)|1.114(1.101/1.100)|

|7168|1536|2048*|2xm192|1.021(0.973/0.979)|1.025(0.975/0.992)|1.231(1.223/1.227)|

|7168|1536|8192*|2xm256g8|1.054(1.057/1.055)|1.057(1.055/1.055)|1.099(1.101/1.099)|

|16384|7168|1*|n8sk2|1.011(1.019/1.020)|1.013(1.021/1.021)|1.133(1.134/1.133)|

|16384|7168|8*|n8sk2|1.011(1.011/1.017)|1.011(1.008/1.015)|1.133(1.130/1.133)|

|16384|7168|17*|n32sk2|1.031(1.033/1.034)|1.027(1.035/1.034)|1.156(1.161/1.160)|

|16384|7168|32*|n32sk2|1.037(1.033/1.036)|1.037(1.033/1.036)|1.155(1.156/1.154)|

|16384|7168|128|m64|0.995(0.990/0.992)|0.997(0.993/0.994)|1.066(1.068/1.067)|

|16384|7168|130|2xm128|1.000(0.995/0.997)|1.000(0.997/0.998)|1.077(1.089/1.084)|

|16384|7168|257|2xm192|1.001(1.008/1.006)|1.001(1.008/1.005)|1.068(1.071/1.071)|

|16384|7168|512*|2xm192|1.006(1.004/1.005)|1.004(1.005/1.004)|1.118(1.119/1.120)|

|16384|7168|2048*|2xm256g8|1.009(1.010/1.010)|1.008(1.010/1.009)|1.085(1.086/1.085)|

|16384|7168|8192*|2xm256g16clc|1.012(1.012/1.012)|1.011(1.010/1.011)|1.147(1.149/1.149)|

|7168|18432|1|n8s3|1.000(0.989/0.994)|0.996(0.991/0.993)|1.055(1.056/1.058)|

|7168|18432|8|n8s3|0.996(0.989/0.994)|0.998(0.989/0.993)|1.057(1.070/1.066)|

|7168|18432|17|n32s3|1.004(1.000/1.002)|1.002(0.995/1.000)|1.046(1.043/1.045)|

|7168|18432|32|n32s3|1.000(1.000/1.000)|1.004(0.998/1.000)|1.038(1.029/1.034)|

|7168|18432|128|m128l2n|1.000(0.998/0.998)|1.000(0.998/0.997)|1.028(1.029/1.027)|

|7168|18432|130|2xm256|1.000(1.003/1.003)|1.000(1.003/1.003)|1.053(1.052/1.052)|

|7168|18432|257|2xm256|1.004(1.004/1.003)|1.004(1.005/0.997)|1.069(1.070/1.069)|

|7168|18432|512*|2xm256|1.000(1.001/1.001)|1.002(1.000/1.001)|1.072(1.068/1.069)|

|7168|18432|2048*|2xm256|1.006(1.004/1.004)|1.002(1.004/1.004)|1.047(1.046/1.046)|

|7168|18432|8192*|2xm256clc|1.003(1.007/1.006)|1.004(1.007/1.006)|1.016(1.013/1.014)|

|18432|7168|1|n8|1.008(0.961/0.975)|1.005(0.960/0.974)|1.121(1.077/1.083)|

|18432|7168|8|n8|1.002(1.040/1.029)|1.000(1.042/1.029)|1.130(1.121/1.115)|

|18432|7168|17*|n32sk2|1.033(1.041/1.041)|1.028(1.043/1.041)|1.156(1.146/1.148)|

|18432|7168|32*|n32sk2|1.038(1.043/1.041)|1.038(1.042/1.040)|1.159(1.164/1.159)|

|18432|7168|128|m64|1.000(1.003/1.001)|1.002(1.005/1.002)|1.059(1.067/1.065)|

|18432|7168|130|2xm128|0.996(0.996/0.997)|0.996(0.996/0.997)|1.058(1.065/1.065)|

|18432|7168|257|2xm192|1.000(0.998/0.998)|0.999(0.996/1.005)|1.062(1.059/1.061)|

|18432|7168|512*|2xm192|1.006(1.009/1.007)|1.006(1.008/1.007)|1.118(1.121/1.119)|

|18432|7168|2048*|2xm256g8|1.002(1.003/1.010)|1.000(1.006/1.003)|1.085(1.087/1.086)|

|18432|7168|8192*|2xm256g16clc|1.006(1.006/1.006)|1.005(1.006/1.006)|1.098(1.101/1.097)|

|8192|8192|1|n8|1.000(0.989/0.994)|0.997(0.995/0.996)|1.057(1.056/1.057)|

|8192|8192|8|n8|0.997(0.997/0.998)|0.995(0.989/0.990)|1.057(1.051/1.053)|

|8192|8192|17|n32|1.016(1.013/1.012)|1.016(1.010/1.011)|1.090(1.095/1.092)|

|8192|8192|32|n32|0.997(0.990/0.992)|1.000(0.992/0.994)|1.070(1.062/1.065)|

|8192|8192|128|m64|1.000(0.995/0.997)|1.000(0.993/0.997)|1.054(1.051/1.053)|

|8192|8192|130|2xm128|1.002(0.995/1.000)|1.005(0.995/0.999)|1.092(1.084/1.089)|

|8192|8192|257|2xm256|1.009(1.015/1.012)|1.011(1.011/1.017)|1.083(1.084/1.082)|

|8192|8192|512*|2xm256|1.016(1.010/1.014)|1.016(1.012/1.016)|1.091(1.088/1.089)|

|8192|8192|2048*|2xm192|1.018(1.020/1.019)|1.023(1.022/1.022)|1.085(1.078/1.079)|

|8192|8192|8192*|2xm256g16clc|1.017(1.016/1.016)|1.015(1.013/1.013)|1.016(1.014/1.014)|

|8192|28672|1|n8|1.000(1.001/1.001)|1.000(1.001/1.000)|1.007(1.011/1.009)|

|8192|28672|8|n8|1.001(1.005/1.003)|1.004(1.006/1.005)|1.012(1.015/1.014)|

|8192|28672|17|n32|0.999(0.996/0.997)|0.995(0.995/0.996)|1.008(1.005/1.006)|

|8192|28672|32|n32|0.999(0.996/0.999)|0.999(0.998/0.998)|1.002(1.002/1.004)|

|8192|28672|128|m192|1.002(1.001/1.001)|1.002(1.002/1.002)|1.030(1.028/1.030)|

|8192|28672|130|2xm192|1.001(1.001/1.000)|1.003(1.001/1.000)|1.039(1.041/1.043)|

|8192|28672|257|2xm256|0.998(0.998/0.997)|1.000(0.996/0.997)|1.064(1.062/1.062)|

|8192|28672|512*|2xm256|0.997(0.996/0.997)|0.997(0.996/0.997)|1.065(1.064/1.065)|

|8192|28672|2048*|2xm256clc|0.997(0.996/0.991)|0.996(0.999/0.999)|1.027(1.027/1.027)|

|8192|28672|8192*|2xm256clc|1.004(1.004/1.004)|1.004(1.006/1.006)|1.012(1.012/1.012)|

|28672|8192|1|n8|1.001(0.990/0.994)|0.999(0.991/0.994)|1.192(1.189/1.190)|

|28672|8192|8|n8|1.000(1.010/1.007)|1.000(1.007/1.007)|1.192(1.194/1.194)|

|28672|8192|17*|n32sk2|1.016(1.017/1.015)|1.012(1.016/1.013)|1.200(1.201/1.200)|

|28672|8192|32*|n32sk2|1.006(1.008/1.008)|1.009(1.012/1.010)|1.201(1.199/1.199)|

|28672|8192|128|m64|1.003(1.001/1.002)|0.998(1.001/1.000)|1.062(1.062/1.063)|

|28672|8192|130|2xm128|1.003(1.005/1.003)|1.005(1.004/1.004)|1.083(1.084/1.084)|

|28672|8192|257|2xm256|1.001(1.001/1.001)|1.002(1.000/1.001)|1.076(1.074/1.076)|

|28672|8192|512*|2xm256|1.007(1.007/1.016)|1.007(1.009/1.009)|1.095(1.093/1.093)|

|28672|8192|2048*|2xm192|1.024(1.023/1.024)|1.024(1.024/1.024)|1.058(1.061/1.061)|

|28672|8192|8192*|2xm256g8clc|1.004(1.004/1.004)|1.010(1.004/1.005)|1.100(1.102/1.102)|

#### Quantize kernel (fold = out_scale folded into the per-token scale)
— vs #5697: bf16 rows 100, geomean 1.0143, min 0.9958, rows <= 1.00: 74;
fp16 (8 registered rows) rows 8, geomean 1.0047, min 1.0000, rows <=
1.00: 7. vs cute-dsl: bf16 rows 100, geomean 1.1233, min 1.0090, rows <=
1.00: 0; fp16 rows 8, geomean 1.1115, min 1.0647, rows <= 1.00: 0

|K|M|fold|vs #5697 bf16|vs cute-dsl bf16|roof|
|---|---|---|---|---|---|
|7168|1|0|1.000(1.000/1.003)|1.215(1.215/1.213)|LB 2.1f|
|7168|1|1|1.000(1.000/1.000)|1.192(1.192/1.191)|LB 2.1f|
|7168|8|0|1.000(1.000/0.998)|1.169(1.169/1.158)|LB 2.1f|
|7168|8|1|1.000(1.000/1.000)|1.111(1.111/1.111)|LB 1.9f|
|7168|17|0|1.000(1.000/0.998)|1.100(1.100/1.098)|LB 2.1f|
|7168|17|1|1.000(1.000/1.001)|1.143(1.143/1.155)|LB 2.1f|
|7168|32|0|1.000(1.000/1.005)|1.112(1.112/1.103)|LB 2.1f|
|7168|32|1|1.000(1.000/1.002)|1.086(1.086/1.086)|LB 2.1f|
|7168|128|0|1.000(1.000/0.998)|1.091(1.091/1.086)|12%h 2.3f|
|7168|128|1|1.000(1.000/1.001)|1.102(1.102/1.098)|12%h 2.3f|
|7168|130|0|1.000(1.000/1.000)|1.101(1.101/1.102)|12%h 2.3f|
|7168|130|1|1.000(1.000/1.002)|1.100(1.100/1.101)|12%h 2.3f|
|7168|257|0|1.000(1.000/0.999)|1.056(1.056/1.056)|20%h 2.8f|
|7168|257|1|1.000(1.000/1.001)|1.065(1.065/1.066)|20%h 2.7f|
|7168|512*|0|1.000(1.000/1.002)|1.073(1.073/1.070)|31%h 3.6f|
|7168|512*|1|1.000(1.000/1.001)|1.072(1.072/1.076)|32%h 3.5f|
|7168|2048*|0|1.041(1.041/1.045)|1.321(1.321/1.323)|60%h|
|7168|2048*|1|1.029(1.029/1.030)|1.287(1.287/1.288)|61%h|
|7168|8192*|0|1.091(1.091/1.091)|1.157(1.157/1.158)|84%h|
|7168|8192*|1|1.114(1.114/1.114)|1.171(1.171/1.172)|84%h|
|8192|1|0|1.000(1.000/1.001)|1.181(1.181/1.179)|LB 2.0f|
|8192|1|1|1.000(1.000/0.998)|1.195(1.195/1.198)|LB 2.0f|
|8192|8|0|1.000(1.000/1.000)|1.084(1.084/1.092)|LB 2.1f|
|8192|8|1|1.000(1.000/0.999)|1.096(1.096/1.101)|LB 2.1f|
|8192|17|0|1.000(1.000/1.000)|1.072(1.072/1.078)|LB 2.1f|
|8192|17|1|1.000(1.000/1.001)|1.085(1.085/1.083)|LB 2.1f|
|8192|32|0|1.000(1.000/0.999)|1.072(1.072/1.062)|LB 2.1f|
|8192|32|1|1.000(1.000/0.998)|1.072(1.072/1.074)|LB 2.1f|
|8192|128|0|1.000(1.000/1.001)|1.065(1.065/1.067)|13%h 2.4f|
|8192|128|1|1.000(1.000/0.998)|1.076(1.076/1.077)|14%h 2.4f|
|8192|130|0|1.000(1.000/1.002)|1.074(1.074/1.072)|13%h 2.4f|
|8192|130|1|1.000(1.000/1.001)|1.074(1.074/1.080)|13%h 2.4f|
|8192|257|0|1.000(1.000/0.998)|1.043(1.043/1.045)|22%h 3.0f|
|8192|257|1|1.000(1.000/1.000)|1.053(1.053/1.051)|22%h 2.9f|
|8192|512*|0|1.013(1.013/1.012)|1.060(1.060/1.064)|34%h 3.8f|
|8192|512*|1|1.000(1.000/0.995)|1.039(1.039/1.040)|33%h 3.8f|
|8192|2048*|0|1.035(1.035/1.032)|1.200(1.200/1.201)|62%h|
|8192|2048*|1|1.029(1.029/1.030)|1.158(1.158/1.161)|63%h|
|8192|8192*|0|1.113(1.113/1.113)|1.164(1.164/1.164)|87%h|
|8192|8192*|1|1.123(1.123/1.123)|1.176(1.176/1.174)|85%h|
|16384|1|0|1.000(1.000/1.002)|1.174(1.174/1.171)|LB 2.4f|
|16384|1|1|1.000(1.000/1.000)|1.113(1.113/1.113)|LB 2.5f|
|16384|8|0|1.000(1.000/1.000)|1.132(1.132/1.128)|LB 2.4f|
|16384|8|1|1.000(1.000/0.999)|1.140(1.140/1.133)|LB 2.4f|
|16384|17|0|1.000(1.000/0.999)|1.085(1.085/1.085)|LB 2.4f|
|16384|17|1|1.000(1.000/1.003)|1.095(1.095/1.089)|LB 2.4f|
|16384|32|0|1.000(1.000/0.998)|1.071(1.071/1.067)|LB 2.5f|
|16384|32|1|1.000(1.000/1.001)|1.082(1.082/1.084)|LB 2.5f|
|16384|128|0|1.000(1.000/0.999)|1.043(1.043/1.045)|21%h 3.1f|
|16384|128|1|1.000(1.000/1.001)|1.050(1.050/1.048)|21%h 3.0f|
|16384|130|0|1.000(1.000/1.001)|1.058(1.058/1.052)|21%h 3.1f|
|16384|130|1|1.000(1.000/1.001)|1.040(1.040/1.036)|21%h 3.0f|
|16384|257|0|1.000(1.000/0.999)|1.044(1.044/1.044)|31%h 4.2f|
|16384|257|1|1.000(1.000/1.000)|1.019(1.019/1.021)|31%h 4.1f|
|16384|512*|0|1.009(1.009/1.009)|1.140(1.140/1.139)|45%h 5.6f|
|16384|512*|1|1.005(1.005/1.003)|1.165(1.165/1.168)|44%h 5.7f|
|16384|2048*|0|1.075(1.075/1.073)|1.427(1.427/1.426)|72%h|
|16384|2048*|1|1.077(1.077/1.075)|1.374(1.374/1.374)|72%h|
|16384|8192*|0|1.081(1.081/1.081)|1.317(1.317/1.317)|90%h|
|16384|8192*|1|1.074(1.074/1.074)|1.325(1.325/1.325)|90%h|
|18432|1|0|1.000(1.000/1.000)|1.147(1.147/1.147)|LB 2.5f|
|18432|1|1|1.000(1.000/1.002)|1.141(1.141/1.145)|LB 2.5f|
|18432|8|0|1.000(1.000/0.999)|1.113(1.113/1.116)|LB 2.4f|
|18432|8|1|1.000(1.000/1.000)|1.122(1.122/1.122)|LB 2.5f|
|18432|17|0|1.000(1.000/0.999)|1.092(1.092/1.093)|LB 2.5f|
|18432|17|1|1.000(1.000/0.997)|1.099(1.099/1.093)|LB 2.5f|
|18432|32|0|1.000(1.000/1.001)|1.069(1.069/1.071)|LB 2.6f|
|18432|32|1|1.000(1.000/1.002)|1.088(1.088/1.087)|LB 2.7f|
|18432|128|0|1.000(1.000/1.000)|1.032(1.032/1.032)|23%h 3.2f|
|18432|128|1|1.000(1.000/1.002)|1.039(1.039/1.043)|22%h 3.2f|
|18432|130|0|1.000(1.000/1.001)|1.039(1.039/1.039)|23%h 3.2f|
|18432|130|1|1.000(1.000/0.999)|1.031(1.031/1.034)|22%h 3.3f|
|18432|257|0|1.000(1.000/1.000)|1.023(1.023/1.023)|33%h 4.4f|
|18432|257|1|1.000(1.000/1.000)|1.017(1.017/1.017)|32%h 4.4f|
|18432|512*|0|1.000(1.000/1.002)|1.181(1.181/1.183)|48%h|
|18432|512*|1|0.996(0.996/0.994)|1.214(1.214/1.213)|48%h|
|18432|2048*|0|1.090(1.090/1.092)|1.429(1.429/1.428)|75%h|
|18432|2048*|1|1.055(1.055/1.055)|1.402(1.402/1.401)|74%h|
|18432|8192*|0|1.067(1.067/1.066)|1.080(1.080/1.080)|92%h|
|18432|8192*|1|1.050(1.050/1.051)|1.067(1.067/1.067)|91%h|
|28672|1|0|1.000(1.000/1.001)|1.187(1.187/1.191)|LB 2.7f|
|28672|1|1|1.000(1.000/1.003)|1.196(1.196/1.197)|LB 2.8f|
|28672|8|0|1.000(1.000/1.000)|1.156(1.156/1.163)|LB 2.8f|
|28672|8|1|1.000(1.000/1.007)|1.188(1.188/1.179)|LB 2.8f|
|28672|17|0|1.000(1.000/1.001)|1.107(1.107/1.113)|LB 2.9f|
|28672|17|1|1.000(1.000/1.001)|1.158(1.158/1.154)|LB 2.9f|
|28672|32|0|1.000(1.000/1.000)|1.093(1.093/1.092)|LB 3.0f|
|28672|32|1|1.000(1.000/0.999)|1.118(1.118/1.118)|LB 3.1f|
|28672|128|0|1.007(1.007/1.002)|1.045(1.045/1.043)|29%h 3.9f|
|28672|128|1|1.000(1.000/1.000)|1.071(1.071/1.070)|29%h 3.9f|
|28672|130|0|1.000(1.000/1.000)|1.063(1.063/1.065)|26%h 4.3f|
|28672|130|1|1.000(1.000/0.999)|1.085(1.085/1.085)|28%h 4.1f|
|28672|257|0|1.000(1.000/1.000)|1.009(1.009/1.011)|40%h 5.6f|
|28672|257|1|1.000(1.000/1.000)|1.061(1.061/1.060)|41%h 5.5f|
|28672|512*|0|1.015(1.015/1.013)|1.102(1.102/1.104)|53%h|
|28672|512*|1|1.018(1.018/1.016)|1.124(1.124/1.127)|53%h|
|28672|2048*|0|1.092(1.092/1.091)|1.266(1.266/1.267)|79%h|
|28672|2048*|1|1.094(1.094/1.093)|1.323(1.323/1.323)|79%h|
|28672|8192*|0|1.044(1.044/1.044)|1.112(1.112/1.112)|93%h|
|28672|8192*|1|1.043(1.043/1.043)|1.109(1.109/1.110)|93%h|

fp16 activations (the registered fp16 quantizer rows):

|K|M|fold|vs #5697 fp16|vs cute-dsl fp16|
|---|---|---|---|---|
|7168|8|0|1.000(1.000/0.999)|1.127(1.127/1.123)|
|7168|17|0|1.000(1.000/1.000)|1.087(1.087/1.082)|
|7168|32|0|1.000(1.000/1.006)|1.087(1.087/1.087)|
|7168|128|0|1.000(1.000/1.002)|1.103(1.103/1.103)|
|7168|130|0|1.000(1.000/1.003)|1.090(1.090/1.097)|
|7168|257|0|1.000(1.000/0.999)|1.065(1.065/1.068)|
|7168|512*|0|1.000(1.000/1.006)|1.065(1.065/1.064)|
|7168|2048*|0|1.038(1.038/1.036)|1.281(1.281/1.281)|

</details>

### B200 (sm_100a, 148 SMs)

<details>
<summary>B200 tables: quantizer, GEMM, fused chain (click to
expand)</summary>

#### GEMM per-token — vs #5697: bf16 rows 80, geomean 1.0050, min
0.9950, rows <= 1.00: 42; fp16 rows 80, geomean 1.0051, min 0.9954, rows
<= 1.00: 40. vs cute-dsl: bf16 rows 80, geomean 1.0549, min 1.0028, rows
<= 1.00: 0; fp16 rows 80, geomean 1.0548, min 1.0018, rows <= 1.00: 0

|K|N|M|tactic|vs #5697 bf16|vs #5697 fp16|vs cute-dsl bf16|vs cute-dsl
fp16|roof (share of measured peak; Nf = N x launch floor)|
|---|---|---|---|---|---|---|---|---|

|7168|2112|1|n8sk4|1.000(1.000/1.000)|1.000(1.000/1.000)|1.021(1.026/1.027)|1.016(1.026/1.028)|23%h
4.0f|

|7168|2112|8|n8sk4|1.000(1.000/1.001)|1.000(1.000/1.000)|1.021(1.026/1.024)|1.026(1.026/1.025)|23%h
4.0f|

|7168|2112|17|n8sk2|1.000(1.000/0.999)|1.000(1.000/1.000)|1.025(1.020/1.023)|1.025(1.030/1.027)|22%h
4.2f|

|7168|2112|32|n8sk2|1.000(1.000/1.001)|1.000(1.000/0.999)|1.049(1.044/1.045)|1.044(1.044/1.046)|21%h
4.4f|

|7168|2112|128|2xm64|1.004(1.000/1.000)|1.000(1.000/1.000)|1.047(1.047/1.044)|1.043(1.047/1.044)|18%h
5.5f|

|7168|2112|130|2xm64|1.000(1.000/0.999)|1.000(1.000/1.000)|1.047(1.047/1.044)|1.043(1.047/1.045)|19%h
5.5f|

|7168|2112|257|2xm64|1.000(1.000/1.000)|1.000(1.000/1.000)|1.042(1.046/1.044)|1.042(1.042/1.042)|20%h
5.6f|

|7168|2112|512|2xm64|1.000(1.000/1.000)|1.000(1.000/1.000)|1.041(1.045/1.044)|1.041(1.044/1.044)|24%c
5.9f|

|7168|2112|2048*|2xm256|1.011(1.009/1.009)|1.009(1.009/1.010)|1.041(1.041/1.041)|1.041(1.041/1.040)|58%c|

|7168|2112|8192|2xm192g8|1.001(1.001/1.001)|1.000(0.999/1.000)|1.050(1.050/1.050)|1.049(1.049/1.049)|76%c|

|7168|1536|1|n8sk4|1.000(1.006/1.001)|1.005(1.000/1.000)|1.017(1.017/1.017)|1.017(1.017/1.016)|17%h
3.9f|

|7168|1536|8|n8sk4|1.000(1.000/0.999)|1.000(1.000/1.000)|1.017(1.017/1.016)|1.011(1.012/1.011)|17%h
3.9f|

|7168|1536|17*|n8sk3|1.056(1.056/1.055)|1.066(1.060/1.061)|1.090(1.084/1.087)|1.085(1.084/1.086)|17%h
4.0f|

|7168|1536|32|n8sk2|1.000(1.000/1.000)|1.005(1.000/1.001)|1.032(1.032/1.030)|1.032(1.032/1.032)|16%h
4.2f|

|7168|1536|128|2xm64|1.000(1.000/1.001)|1.000(1.000/1.001)|1.053(1.053/1.053)|1.053(1.053/1.052)|14%h
5.4f|

|7168|1536|130|2xm64|1.020(1.020/1.019)|1.020(1.020/1.019)|1.045(1.040/1.042)|1.045(1.044/1.043)|14%h
5.4f|

|7168|1536|257|2xm64|1.020(1.016/1.018)|1.016(1.020/1.017)|1.036(1.040/1.040)|1.040(1.044/1.041)|16%h
5.4f|

|7168|1536|512|2xm64|1.015(1.019/1.018)|1.019(1.019/1.019)|1.039(1.039/1.039)|1.039(1.039/1.040)|19%h
5.6f|

|7168|1536|2048*|2xm192|1.013(1.013/1.012)|1.013(1.013/1.013)|1.045(1.048/1.046)|1.048(1.048/1.048)|52%c|

|7168|1536|8192|2xm256g8|1.000(1.001/1.001)|1.001(1.000/1.000)|1.073(1.074/1.074)|1.074(1.075/1.075)|71%c|

|16384|7168|1*|n8sk2|1.013(1.012/1.012)|1.013(1.015/1.013)|1.113(1.113/1.112)|1.116(1.115/1.114)|68%h|

|16384|7168|8*|n8sk2|1.010(1.008/1.010)|1.008(1.013/1.012)|1.120(1.119/1.119)|1.120(1.117/1.118)|68%h|

|16384|7168|17*|n32sk2|1.022(1.020/1.024)|1.020(1.020/1.022)|1.145(1.145/1.147)|1.143(1.145/1.144)|66%h|

|16384|7168|32*|n32sk2|1.022(1.022/1.022)|1.024(1.024/1.024)|1.141(1.140/1.141)|1.143(1.140/1.141)|66%h|

|16384|7168|128|m64|0.998(1.002/1.001)|1.000(1.000/1.000)|1.018(1.018/1.018)|1.018(1.018/1.017)|59%h|

|16384|7168|130|2xm128|0.998(0.998/0.999)|1.002(1.000/1.001)|1.048(1.049/1.049)|1.048(1.049/1.048)|57%h|

|16384|7168|257|2xm256|1.006(1.006/1.006)|1.004(1.006/1.005)|1.040(1.041/1.041)|1.041(1.042/1.042)|43%h|

|16384|7168|512|2xm256|1.005(1.006/1.005)|1.007(1.005/1.006)|1.041(1.043/1.043)|1.041(1.041/1.041)|61%c|

|16384|7168|2048*|2xm192|1.028(1.027/1.028)|1.027(1.027/1.027)|1.057(1.057/1.057)|1.057(1.056/1.057)|74%c|

|16384|7168|8192|2xm256g16clc|0.996(0.999/1.002)|0.998(0.983/1.002)|1.124(1.107/1.100)|1.133(1.134/1.127)|89%c|

|7168|18432|1|n8s3|0.998(1.000/1.000)|1.000(1.000/1.000)|1.033(1.031/1.031)|1.031(1.031/1.031)|72%h|

|7168|18432|8|n8s3|0.998(1.000/0.999)|0.998(1.000/0.999)|1.031(1.033/1.032)|1.035(1.035/1.034)|72%h|

|7168|18432|17|n32s3|1.002(1.000/1.002)|1.000(1.000/1.001)|1.012(1.012/1.010)|1.014(1.015/1.014)|72%h|

|7168|18432|32|n32s3|1.000(0.998/0.999)|1.000(0.998/0.999)|1.015(1.010/1.012)|1.014(1.012/1.012)|72%h|

|7168|18432|128*|m128l2n|0.998(0.998/0.998)|0.998(1.000/1.000)|1.006(1.007/1.007)|1.002(1.002/1.001)|72%h|

|7168|18432|130|2xm256|1.000(0.998/0.999)|0.998(1.000/1.000)|1.029(1.031/1.030)|1.031(1.032/1.031)|67%h|

|7168|18432|257|2xm256|1.001(1.000/1.000)|1.000(0.999/1.000)|1.039(1.038/1.039)|1.037(1.038/1.038)|51%h|

|7168|18432|512|2xm256|1.000(1.000/1.000)|0.999(0.999/1.000)|1.037(1.037/1.037)|1.038(1.038/1.037)|68%c|

|7168|18432|2048|2xm256|1.000(1.000/1.000)|1.001(1.000/1.000)|1.033(1.032/1.032)|1.032(1.031/1.031)|86%c|

|7168|18432|8192|2xm256clc|0.995(1.009/1.015)|1.000(1.019/1.002)|1.043(1.047/1.048)|1.039(1.039/1.037)|89%c|

|18432|7168|1|n8|1.000(1.000/1.000)|1.000(1.002/1.000)|1.148(1.148/1.149)|1.150(1.148/1.149)|68%h|

|18432|7168|8|n8|1.000(1.002/1.000)|1.000(1.000/0.999)|1.152(1.150/1.151)|1.150(1.150/1.151)|68%h|

|18432|7168|17*|n32sk2|1.009(1.011/1.012)|1.009(1.007/1.011)|1.149(1.149/1.150)|1.149(1.149/1.150)|65%h|

|18432|7168|32*|n32sk2|1.009(1.011/1.010)|1.009(1.009/1.008)|1.141(1.141/1.142)|1.145(1.146/1.146)|65%h|

|18432|7168|128|m64|1.000(0.998/0.999)|1.000(1.000/1.000)|1.023(1.024/1.023)|1.023(1.023/1.022)|61%h|

|18432|7168|130|2xm128|1.000(1.000/1.000)|1.000(1.000/1.000)|1.057(1.056/1.056)|1.054(1.056/1.056)|58%h|

|18432|7168|257|2xm256|1.006(1.004/1.005)|1.007(1.006/1.006)|1.045(1.047/1.046)|1.046(1.046/1.046)|44%h|

|18432|7168|512|2xm256|1.005(1.004/1.007)|1.005(1.004/1.005)|1.049(1.048/1.049)|1.048(1.047/1.048)|62%c|

|18432|7168|2048*|2xm192|1.027(1.026/1.026)|1.025(1.026/1.026)|1.056(1.053/1.053)|1.053(1.057/1.057)|75%c|

|18432|7168|8192|2xm256g16clc|0.999(0.990/0.980)|0.998(0.997/0.999)|1.125(1.132/1.133)|1.127(1.133/1.121)|88%c|

|8192|8192|1|n8|1.000(1.000/1.000)|1.003(1.000/0.999)|1.012(1.012/1.011)|1.003(1.006/1.004)|57%h|

|8192|8192|8|n8|0.997(1.000/0.999)|1.000(1.000/1.000)|1.012(1.012/1.013)|1.012(1.009/1.010)|57%h|

|8192|8192|17|n32|1.000(1.000/1.001)|0.997(1.000/1.001)|1.012(1.012/1.013)|1.015(1.015/1.015)|57%h|

|8192|8192|32|n32|1.000(1.003/1.001)|1.000(1.000/1.001)|1.006(1.006/1.006)|1.006(1.003/1.004)|56%h|

|8192|8192|128|m64|1.000(1.000/1.001)|1.003(1.000/1.000)|1.003(1.003/1.004)|1.006(1.005/1.005)|55%h|

|8192|8192|130|2xm128|1.000(1.000/1.000)|1.000(1.000/1.000)|1.044(1.047/1.046)|1.047(1.044/1.045)|52%h|

|8192|8192|257|2xm256|1.008(1.008/1.008)|1.010(1.008/1.008)|1.047(1.049/1.049)|1.049(1.049/1.049)|42%h|

|8192|8192|512|2xm256|1.010(1.009/1.009)|1.008(1.010/1.008)|1.046(1.048/1.048)|1.046(1.046/1.046)|56%c|

|8192|8192|2048*|2xm192|1.021(1.021/1.021)|1.021(1.021/1.021)|1.059(1.058/1.059)|1.058(1.058/1.058)|77%c|

|8192|8192|8192|2xm256g16clc|1.000(1.001/1.008)|1.004(1.001/1.005)|1.040(1.042/1.038)|1.040(1.037/1.036)|90%c|

|8192|28672|1|n8|1.000(1.000/1.000)|1.000(1.000/1.000)|1.006(1.006/1.006)|1.008(1.008/1.008)|83%h|

|8192|28672|8|n8|1.000(0.999/0.999)|1.000(1.000/1.000)|1.010(1.010/1.010)|1.009(1.010/1.010)|83%h|

|8192|28672|17|n32|1.003(1.000/1.009)|1.000(0.999/1.001)|1.009(1.009/1.018)|1.009(1.007/1.010)|83%h|

|8192|28672|32|n32|1.000(1.001/1.001)|1.000(1.000/1.000)|1.010(1.011/1.011)|1.005(1.004/1.004)|84%h|

|8192|28672|128|m128|0.999(1.000/1.000)|1.000(1.000/1.001)|1.019(1.020/1.020)|1.017(1.020/1.020)|78%h|

|8192|28672|130|2xm256|1.000(1.000/1.000)|1.000(1.000/1.000)|1.019(1.019/1.018)|1.019(1.019/1.019)|70%h|

|8192|28672|257*|2xm192|1.021(1.021/1.020)|1.021(1.019/1.018)|1.056(1.057/1.057)|1.057(1.056/1.056)|48%h|

|8192|28672|512*|2xm192|1.021(1.021/1.021)|1.021(1.021/1.020)|1.062(1.062/1.062)|1.062(1.062/1.062)|65%c|

|8192|28672|2048|2xm256clc|0.999(0.998/0.998)|1.001(1.005/0.999)|1.044(1.046/1.045)|1.044(1.043/1.042)|86%c|

|8192|28672|8192|2xm256clc|0.998(1.000/1.008)|0.997(1.003/1.001)|1.015(1.040/1.024)|1.019(1.033/1.027)|85%c|

|28672|8192|1|n8|1.000(1.000/1.000)|1.000(1.000/1.000)|1.189(1.190/1.189)|1.190(1.192/1.192)|81%h|

|28672|8192|8|n8|1.001(0.999/1.000)|1.000(1.001/1.001)|1.190(1.192/1.192)|1.192(1.189/1.190)|81%h|

|28672|8192|17*|n32sk2|1.001(1.001/1.003)|1.002(1.002/1.013)|1.182(1.181/1.184)|1.184(1.184/1.186)|78%h|

|28672|8192|32*|n32sk2|1.006(1.005/1.005)|0.999(1.002/1.002)|1.180(1.182/1.181)|1.176(1.179/1.179)|78%h|

|28672|8192|128|m64|0.999(1.000/1.000)|0.999(1.001/1.000)|1.014(1.016/1.016)|1.013(1.015/1.015)|73%h|

|28672|8192|130|2xm128|1.000(1.000/1.000)|0.999(0.999/0.999)|1.043(1.044/1.044)|1.043(1.043/1.043)|70%h|

|28672|8192|257|2xm256|1.004(1.004/1.003)|1.004(1.003/1.003)|1.048(1.048/1.048)|1.046(1.048/1.047)|52%h|

|28672|8192|512|2xm256|1.004(1.004/1.004)|1.004(1.003/1.004)|1.059(1.058/1.058)|1.057(1.056/1.057)|75%c|

|28672|8192|2048*|2xm192|1.025(1.024/1.015)|1.023(1.024/1.021)|1.054(1.053/1.052)|1.053(1.054/1.058)|85%c|

|28672|8192|8192|2xm256g8clc|1.002(1.002/1.025)|0.995(0.998/0.995)|1.086(1.099/1.100)|1.096(1.078/1.075)|85%c|

#### Fused quantize + GEMM chain (CUDA-graph replay, PDL edge included)
— vs #5697: bf16 rows 80, geomean 1.0096, min 0.9950, rows <= 1.00: 25;
fp16 rows 80, geomean 1.0099, min 0.9950, rows <= 1.00: 25. vs cute-dsl
(bf16): rows 80, geomean 1.0885, min 1.0047, rows <= 1.00: 0

|K|N|M|GEMM tactic|vs #5697 bf16|vs #5697 fp16|vs cute-dsl bf16|
|---|---|---|---|---|---|---|

|7168|2112|1|n8sk4|1.013(1.026/1.018)|1.017(1.026/1.018)|1.115(1.166/1.152)|

|7168|2112|8|n8sk4|1.000(1.004/1.002)|0.996(1.000/0.999)|1.140(1.174/1.164)|

|7168|2112|17|n8sk2|1.000(1.012/1.002)|0.996(1.004/1.001)|1.151(1.173/1.163)|

|7168|2112|32|n8sk2|1.004(1.004/1.003)|1.000(1.008/1.003)|1.135(1.138/1.139)|

|7168|2112|128|2xm64|1.003(0.997/0.999)|1.000(0.997/0.997)|1.131(1.138/1.132)|

|7168|2112|130|2xm64|1.003(1.016/1.010)|1.006(1.016/1.010)|1.134(1.151/1.145)|

|7168|2112|257|2xm64|1.003(0.997/0.995)|1.000(0.997/0.996)|1.121(1.125/1.121)|

|7168|2112|512*|2xm64|1.022(1.027/1.026)|1.022(1.027/1.027)|1.126(1.149/1.145)|

|7168|2112|2048*|2xm256|1.026(1.010/1.013)|1.019(1.013/1.014)|1.231(1.203/1.206)|

|7168|2112|8192*|2xm192g8|1.047(1.044/1.045)|1.046(1.044/1.045)|1.057(1.056/1.057)|

|7168|1536|1|n8sk4|0.996(0.987/0.996)|1.000(0.991/0.999)|1.120(1.108/1.120)|

|7168|1536|8|n8sk4|0.996(0.978/0.986)|0.995(0.978/0.988)|1.088(1.090/1.088)|

|7168|1536|17*|n8sk3|1.035(1.034/1.035)|1.035(1.030/1.033)|1.167(1.149/1.159)|

|7168|1536|32|n8sk2|1.000(1.004/1.006)|1.008(0.996/1.002)|1.102(1.097/1.102)|

|7168|1536|128|2xm64|1.000(0.987/0.994)|0.997(0.987/0.994)|1.087(1.079/1.084)|

|7168|1536|130|2xm64|1.016(1.006/1.009)|1.016(1.010/1.008)|1.090(1.076/1.079)|

|7168|1536|257|2xm64|1.012(1.000/1.010)|1.012(1.000/1.011)|1.077(1.073/1.079)|

|7168|1536|512*|2xm64|1.045(1.045/1.044)|1.045(1.048/1.045)|1.119(1.121/1.121)|

|7168|1536|2048*|2xm192|1.031(1.027/1.028)|1.026(1.032/1.030)|1.194(1.204/1.200)|

|7168|1536|8192*|2xm256g8|1.047(1.046/1.046)|1.043(1.044/1.044)|1.090(1.089/1.089)|

|16384|7168|1*|n8sk2|1.011(1.014/1.018)|1.007(1.014/1.018)|1.104(1.106/1.107)|

|16384|7168|8*|n8sk2|1.009(1.015/1.020)|1.009(1.011/1.019)|1.107(1.115/1.111)|

|16384|7168|17*|n32sk2|1.029(1.021/1.025)|1.027(1.025/1.026)|1.144(1.138/1.140)|

|16384|7168|32*|n32sk2|1.034(1.046/1.040)|1.032(1.044/1.040)|1.146(1.154/1.149)|

|16384|7168|128|m64|1.006(1.006/1.004)|1.008(1.008/1.006)|1.040(1.047/1.043)|

|16384|7168|130|2xm128|0.998(0.999/0.998)|1.002(0.999/0.999)|1.077(1.093/1.088)|

|16384|7168|257|2xm256|1.010(1.006/1.007)|1.012(1.005/1.007)|1.037(1.037/1.037)|

|16384|7168|512*|2xm256|1.011(1.010/1.009)|1.018(1.009/1.009)|1.085(1.073/1.074)|

|16384|7168|2048*|2xm192|1.035(1.035/1.035)|1.037(1.036/1.036)|1.112(1.112/1.112)|

|16384|7168|8192*|2xm256g16clc|1.001(0.991/1.001)|1.007(1.007/1.014)|1.152(1.148/1.155)|

|7168|18432|1|n8s3|1.000(1.004/1.001)|0.998(1.002/1.002)|1.079(1.089/1.083)|

|7168|18432|8|n8s3|0.998(1.005/1.003)|1.000(1.004/1.004)|1.073(1.095/1.086)|

|7168|18432|17|n32s3|1.000(1.000/1.000)|1.000(1.000/1.001)|1.050(1.049/1.050)|

|7168|18432|32|n32s3|1.009(1.003/1.007)|1.005(1.005/1.006)|1.053(1.062/1.060)|

|7168|18432|128*|m128l2n|0.995(1.000/0.998)|0.995(0.998/0.998)|1.043(1.058/1.055)|

|7168|18432|130|2xm256|1.002(0.997/1.000)|1.002(0.995/1.000)|1.047(1.044/1.047)|

|7168|18432|257|2xm256|0.999(0.996/0.997)|0.998(0.994/0.997)|1.053(1.054/1.053)|

|7168|18432|512*|2xm256|1.006(1.011/1.009)|1.007(1.011/1.009)|1.061(1.065/1.065)|

|7168|18432|2048*|2xm256|1.006(1.005/1.006)|1.008(1.006/1.006)|1.048(1.047/1.047)|

|7168|18432|8192*|2xm256clc|0.999(1.012/1.015)|1.007(1.008/1.011)|1.029(1.068/1.060)|

|18432|7168|1|n8|1.003(1.000/0.997)|1.003(1.002/0.998)|1.108(1.070/1.077)|

|18432|7168|8|n8|1.005(1.035/1.026)|1.002(1.035/1.026)|1.115(1.114/1.112)|

|18432|7168|17*|n32sk2|1.030(1.043/1.037)|1.029(1.046/1.038)|1.158(1.161/1.155)|

|18432|7168|32*|n32sk2|1.025(1.019/1.023)|1.027(1.020/1.025)|1.143(1.139/1.141)|

|18432|7168|128|m64|0.997(0.993/0.994)|1.000(0.994/0.995)|1.052(1.053/1.053)|

|18432|7168|130|2xm128|1.001(1.000/1.001)|1.001(1.009/1.006)|1.075(1.078/1.076)|

|18432|7168|257|2xm256|1.003(1.007/1.005)|1.006(1.007/1.006)|1.047(1.050/1.050)|

|18432|7168|512*|2xm256|1.012(1.010/1.009)|1.010(1.010/1.010)|1.099(1.096/1.098)|

|18432|7168|2048*|2xm192|1.036(1.039/1.038)|1.037(1.038/1.038)|1.113(1.116/1.114)|

|18432|7168|8192*|2xm256g16clc|1.004(1.007/1.007)|1.012(0.999/0.999)|1.111(1.101/1.087)|

|8192|8192|1|n8|1.005(1.005/1.004)|1.005(1.005/1.008)|1.057(1.059/1.057)|

|8192|8192|8|n8|1.005(1.010/1.009)|1.008(1.010/1.008)|1.046(1.067/1.060)|

|8192|8192|17|n32|0.998(0.990/0.992)|1.000(0.990/0.985)|1.045(1.045/1.044)|

|8192|8192|32|n32|1.013(1.015/1.011)|1.013(1.010/1.009)|1.055(1.050/1.051)|

|8192|8192|128|m64|0.995(1.000/0.996)|0.995(1.000/0.997)|1.052(1.054/1.051)|

|8192|8192|130|2xm128|1.004(1.002/1.005)|1.002(1.004/1.004)|1.075(1.079/1.080)|

|8192|8192|257|2xm256|1.008(1.000/1.004)|1.008(0.998/1.002)|1.062(1.063/1.062)|

|8192|8192|512*|2xm256|1.022(1.021/1.022)|1.022(1.022/1.023)|1.077(1.064/1.070)|

|8192|8192|2048*|2xm192|1.030(1.029/1.033)|1.027(1.027/1.027)|1.084(1.084/1.084)|

|8192|8192|8192*|2xm256g16clc|1.016(1.014/1.011)|1.016(1.018/1.015)|1.020(1.018/1.018)|

|8192|28672|1|n8|0.999(0.994/0.997)|1.000(0.994/0.996)|1.046(1.041/1.041)|

|8192|28672|8|n8|0.999(0.994/0.996)|0.999(0.994/0.995)|1.038(1.036/1.036)|

|8192|28672|17|n32|0.999(0.999/0.999)|0.999(0.999/0.998)|1.005(1.014/1.011)|

|8192|28672|32|n32|1.006(1.007/1.006)|1.002(1.008/1.005)|1.030(1.035/1.034)|

|8192|28672|128|m128|1.000(0.998/0.999)|0.999(0.996/0.998)|1.008(1.005/1.007)|

|8192|28672|130|2xm256|1.005(1.005/1.005)|1.006(1.006/1.005)|1.040(1.040/1.041)|

|8192|28672|257*|2xm192|1.020(1.019/1.019)|1.022(1.020/1.020)|1.067(1.066/1.067)|

|8192|28672|512*|2xm192|1.018(1.019/1.019)|1.020(1.020/1.019)|1.063(1.062/1.063)|

|8192|28672|2048*|2xm256clc|1.000(1.005/1.004)|1.002(1.001/1.001)|1.040(1.043/1.042)|

|8192|28672|8192*|2xm256clc|0.998(1.003/1.006)|1.003(1.003/1.019)|1.019(1.031/1.027)|

|28672|8192|1|n8|1.000(1.027/1.018)|1.000(1.028/1.019)|1.175(1.177/1.170)|

|28672|8192|8|n8|0.999(0.970/0.980)|0.999(0.972/0.982)|1.200(1.163/1.170)|

|28672|8192|17*|n32sk2|1.007(1.003/1.005)|1.014(1.014/1.014)|1.193(1.186/1.188)|

|28672|8192|32*|n32sk2|1.012(1.017/1.019)|1.014(1.026/1.025)|1.185(1.182/1.184)|

|28672|8192|128|m64|0.996(0.994/0.996)|0.996(0.997/0.997)|1.051(1.054/1.053)|

|28672|8192|130|2xm128|0.999(0.998/0.998)|0.999(0.998/0.999)|1.065(1.068/1.066)|

|28672|8192|257|2xm256|1.007(1.021/1.016)|1.008(1.024/1.017)|1.073(1.075/1.074)|

|28672|8192|512*|2xm256|1.002(1.008/1.006)|1.005(1.011/1.010)|1.104(1.103/1.099)|

|28672|8192|2048*|2xm192|1.032(1.033/1.035)|1.037(1.034/1.033)|1.069(1.070/1.068)|

|28672|8192|8192*|2xm256g8clc|1.007(1.009/1.024)|0.996(1.003/1.004)|1.083(1.094/1.092)|

#### Quantize kernel (fold = out_scale folded into the per-token scale)
— vs #5697: bf16 rows 100, geomean 1.0156, min 0.9996, rows <= 1.00: 65;
fp16 (8 registered rows) rows 8, geomean 1.0088, min 1.0000, rows <=
1.00: 6. vs cute-dsl: bf16 rows 100, geomean 1.1258, min 1.0175, rows <=
1.00: 0; fp16 rows 8, geomean 1.1150, min 1.0629, rows <= 1.00: 0

|K|M|fold|vs #5697 bf16|vs cute-dsl bf16|roof|
|---|---|---|---|---|---|
|7168|1|0|1.000(1.000/0.999)|1.217(1.217/1.211)|LB 1.8f|
|7168|1|1|1.000(1.000/1.001)|1.181(1.181/1.175)|LB 1.8f|
|7168|8|0|1.000(1.000/1.002)|1.165(1.165/1.163)|LB 1.8f|
|7168|8|1|1.000(1.000/0.998)|1.095(1.095/1.098)|LB 1.7f|
|7168|17|0|1.000(1.000/0.998)|1.108(1.108/1.105)|LB 1.8f|
|7168|17|1|1.000(1.000/0.999)|1.139(1.139/1.139)|LB 1.8f|
|7168|32|0|1.012(1.012/1.005)|1.120(1.120/1.112)|LB 1.8f|
|7168|32|1|1.000(1.000/0.999)|1.107(1.107/1.105)|LB 1.8f|
|7168|128|0|1.000(1.000/0.998)|1.099(1.099/1.099)|13%h 2.0f|
|7168|128|1|1.000(1.000/0.998)|1.097(1.097/1.094)|13%h 2.0f|
|7168|130|0|1.000(1.000/0.997)|1.097(1.097/1.099)|13%h 2.0f|
|7168|130|1|1.000(1.000/1.002)|1.097(1.097/1.097)|13%h 2.0f|
|7168|257|0|1.000(1.000/1.000)|1.062(1.062/1.066)|20%h 2.5f|
|7168|257|1|1.000(1.000/1.001)|1.071(1.071/1.072)|21%h 2.4f|
|7168|512*|0|1.000(1.000/1.002)|1.062(1.062/1.063)|32%h 3.2f|
|7168|512*|1|1.000(1.000/1.001)|1.076(1.076/1.078)|32%h 3.2f|
|7168|2048*|0|1.050(1.050/1.050)|1.279(1.279/1.282)|64%h|
|7168|2048*|1|1.039(1.039/1.041)|1.343(1.343/1.343)|62%h|
|7168|8192*|0|1.091(1.091/1.091)|1.153(1.153/1.153)|86%h|
|7168|8192*|1|1.122(1.122/1.122)|1.183(1.183/1.182)|86%h|
|8192|1|0|1.000(1.000/1.001)|1.186(1.186/1.190)|LB 1.8f|
|8192|1|1|1.012(1.012/1.005)|1.200(1.200/1.202)|LB 1.8f|
|8192|8|0|1.000(1.000/1.000)|1.083(1.083/1.080)|LB 1.8f|
|8192|8|1|1.000(1.000/1.001)|1.070(1.070/1.072)|LB 1.8f|
|8192|17|0|1.000(1.000/1.001)|1.082(1.082/1.083)|LB 1.8f|
|8192|17|1|1.000(1.000/1.001)|1.070(1.070/1.069)|LB 1.9f|
|8192|32|0|1.000(1.000/0.998)|1.093(1.093/1.091)|LB 1.9f|
|8192|32|1|1.000(1.000/1.000)|1.057(1.057/1.064)|LB 1.9f|
|8192|128|0|1.000(1.000/1.001)|1.074(1.074/1.076)|14%h 2.1f|
|8192|128|1|1.000(1.000/1.002)|1.073(1.073/1.076)|14%h 2.1f|
|8192|130|0|1.000(1.000/1.001)|1.113(1.113/1.112)|14%h 2.1f|
|8192|130|1|1.000(1.000/1.003)|1.071(1.071/1.070)|14%h 2.1f|
|8192|257|0|1.000(1.000/1.002)|1.050(1.050/1.054)|22%h 2.6f|
|8192|257|1|1.000(1.000/1.000)|1.042(1.042/1.044)|22%h 2.6f|
|8192|512*|0|1.006(1.006/1.005)|1.058(1.058/1.055)|34%h 3.4f|
|8192|512*|1|1.000(1.000/0.999)|1.045(1.045/1.042)|34%h 3.4f|
|8192|2048*|0|1.043(1.043/1.047)|1.186(1.186/1.189)|64%h|
|8192|2048*|1|1.037(1.037/1.039)|1.192(1.192/1.191)|62%h|
|8192|8192*|0|1.117(1.117/1.118)|1.146(1.146/1.146)|87%h|
|8192|8192*|1|1.099(1.099/1.100)|1.142(1.142/1.143)|88%h|
|16384|1|0|1.000(1.000/1.000)|1.165(1.165/1.168)|LB 2.1f|
|16384|1|1|1.000(1.000/1.001)|1.109(1.109/1.114)|LB 2.2f|
|16384|8|0|1.000(1.000/1.001)|1.093(1.093/1.091)|LB 2.1f|
|16384|8|1|1.000(1.000/1.003)|1.082(1.082/1.087)|LB 2.1f|
|16384|17|0|1.000(1.000/1.000)|1.081(1.081/1.080)|LB 2.1f|
|16384|17|1|1.000(1.000/0.998)|1.071(1.071/1.069)|LB 2.1f|
|16384|32|0|1.000(1.000/1.004)|1.038(1.038/1.036)|LB 2.2f|
|16384|32|1|1.000(1.000/1.000)|1.079(1.079/1.080)|LB 2.2f|
|16384|128|0|1.000(1.000/1.001)|1.040(1.040/1.041)|21%h 2.7f|
|16384|128|1|1.000(1.000/1.001)|1.032(1.032/1.033)|21%h 2.7f|
|16384|130|0|1.000(1.000/1.001)|1.069(1.069/1.069)|20%h 2.9f|
|16384|130|1|1.000(1.000/0.999)|1.047(1.047/1.045)|20%h 2.9f|
|16384|257|0|1.000(1.000/1.000)|1.042(1.042/1.041)|32%h 3.6f|
|16384|257|1|1.000(1.000/1.000)|1.025(1.025/1.023)|31%h 3.7f|
|16384|512*|0|1.000(1.000/1.001)|1.185(1.185/1.185)|46%h 4.9f|
|16384|512*|1|1.000(1.000/1.002)|1.183(1.183/1.184)|46%h 5.0f|
|16384|2048*|0|1.070(1.070/1.071)|1.469(1.469/1.469)|75%h|
|16384|2048*|1|1.089(1.089/1.087)|1.436(1.436/1.439)|76%h|
|16384|8192*|0|1.079(1.079/1.080)|1.342(1.342/1.343)|93%h|
|16384|8192*|1|1.074(1.074/1.074)|1.339(1.339/1.338)|93%h|
|18432|1|0|1.000(1.000/1.002)|1.137(1.137/1.138)|LB 2.1f|
|18432|1|1|1.000(1.000/1.000)|1.152(1.152/1.145)|LB 2.3f|
|18432|8|0|1.000(1.000/1.001)|1.130(1.130/1.125)|LB 2.2f|
|18432|8|1|1.000(1.000/0.999)|1.096(1.096/1.092)|LB 2.2f|
|18432|17|0|1.000(1.000/1.000)|1.097(1.097/1.097)|LB 2.2f|
|18432|17|1|1.000(1.000/0.999)|1.104(1.104/1.101)|LB 2.3f|
|18432|32|0|1.000(1.000/1.000)|1.065(1.065/1.068)|LB 2.3f|
|18432|32|1|1.000(1.000/1.002)|1.104(1.104/1.106)|LB 2.3f|
|18432|128|0|1.000(1.000/1.000)|1.046(1.046/1.046)|23%h 2.8f|
|18432|128|1|1.000(1.000/0.999)|1.053(1.053/1.052)|22%h 2.9f|
|18432|130|0|1.000(1.000/1.002)|1.043(1.043/1.043)|21%h 3.1f|
|18432|130|1|1.000(1.000/1.000)|1.037(1.037/1.040)|22%h 3.0f|
|18432|257|0|1.000(1.000/1.000)|1.034(1.034/1.032)|34%h 3.8f|
|18432|257|1|1.000(1.000/1.001)|1.027(1.027/1.024)|33%h 3.9f|
|18432|512*|0|1.004(1.004/1.002)|1.195(1.195/1.193)|49%h 5.3f|
|18432|512*|1|1.000(1.000/1.003)|1.241(1.241/1.237)|49%h 5.3f|
|18432|2048*|0|1.119(1.119/1.119)|1.484(1.484/1.484)|76%h|
|18432|2048*|1|1.086(1.086/1.087)|1.477(1.477/1.479)|76%h|
|18432|8192*|0|1.058(1.058/1.058)|1.077(1.077/1.078)|93%h|
|18432|8192*|1|1.063(1.063/1.063)|1.060(1.060/1.060)|93%h|
|28672|1|0|1.000(1.000/1.002)|1.172(1.172/1.174)|LB 2.4f|
|28672|1|1|1.000(1.000/0.996)|1.198(1.198/1.194)|LB 2.5f|
|28672|8|0|1.000(1.000/0.998)|1.140(1.140/1.143)|LB 2.5f|
|28672|8|1|1.008(1.008/1.001)|1.164(1.164/1.163)|LB 2.5f|
|28672|17|0|1.000(1.000/1.000)|1.127(1.127/1.124)|LB 2.6f|
|28672|17|1|1.000(1.000/0.999)|1.132(1.132/1.134)|LB 2.6f|
|28672|32|0|1.000(1.000/1.001)|1.097(1.097/1.097)|LB 2.7f|
|28672|32|1|1.000(1.000/1.001)|1.128(1.128/1.124)|LB 2.7f|
|28672|128|0|1.000(1.000/0.999)|1.044(1.044/1.048)|29%h 3.5f|
|28672|128|1|1.000(1.000/1.001)|1.068(1.068/1.068)|29%h 3.5f|
|28672|130|0|1.000(1.000/1.000)|1.052(1.052/1.054)|26%h 3.9f|
|28672|130|1|1.000(1.000/0.999)|1.067(1.067/1.067)|28%h 3.7f|
|28672|257|0|1.000(1.000/1.000)|1.018(1.018/1.017)|41%h 4.9f|
|28672|257|1|1.000(1.000/1.000)|1.062(1.062/1.061)|41%h 4.9f|
|28672|512*|0|1.027(1.027/1.026)|1.119(1.119/1.118)|54%h|
|28672|512*|1|1.017(1.017/1.015)|1.158(1.158/1.157)|53%h|
|28672|2048*|0|1.079(1.079/1.079)|1.313(1.313/1.313)|81%h|
|28672|2048*|1|1.115(1.115/1.115)|1.320(1.320/1.320)|81%h|
|28672|8192*|0|1.046(1.046/1.046)|1.111(1.111/1.111)|95%h|
|28672|8192*|1|1.042(1.042/1.043)|1.117(1.117/1.117)|95%h|

fp16 activations (the registered fp16 quantizer rows):

|K|M|fold|vs #5697 fp16|vs cute-dsl fp16|
|---|---|---|---|---|
|7168|8|0|1.000(1.000/0.999)|1.096(1.096/1.096)|
|7168|17|0|1.000(1.000/1.000)|1.084(1.084/1.087)|
|7168|32|0|1.000(1.000/0.999)|1.108(1.108/1.108)|
|7168|128|0|1.000(1.000/1.000)|1.111(1.111/1.104)|
|7168|130|0|1.000(1.000/0.999)|1.063(1.063/1.061)|
|7168|257|0|1.000(1.000/1.001)|1.072(1.072/1.075)|
|7168|512*|0|1.007(1.007/1.006)|1.063(1.063/1.066)|
|7168|2048*|0|1.065(1.065/1.067)|1.347(1.347/1.347)|

</details>

Rows that read below 1.00 vs #5697 at 6 rounds were re-measured at 12
rounds and carry the 12-round statistics. Every remaining row <= 1.00 vs
#5697 runs a byte-identical program on both arms (the fused-graph
instrument's residual on M = 1 / 8 chains is 0.986-0.995 and reproduces
to the tick in an A/A run of the #5697 package against itself), with one
exception: the lever-6 row 7168x18432 M = 128 on B200 runs the L2-off
program against the promoted one (kernel source byte-identical, host
descriptor attribute only) and reads GEMM 0.9982 / 0.9982 and fused
0.9950 / 0.9950 (0.99498 bf16) min-of-round-medians at 12 rounds,
medians 0.9982 / 1.0000 and 1.0000 / 0.9984 - one 32 ns CUPTI tick on a
17.4 / 19.4 us row, i.e. a tie; the same process reads the row at 1.0055
/ 1.0018 (GEMM) and 1.0433 / 1.0444 (fused) against the cute-dsl
baseline, where the promoted default had read 0.9927 (fp16) in the
6-round export. vs the cute-dsl baseline every row is > 1.00 except
GB300 GEMM bf16 7168x18432 M = 8192 (0.9996 at 12 rounds; both routes
run at 90-91 % of the measured 8269 TFLOPS, 14 tactic variants all
lose).

## Gates

- FlashInfer tests on this head (dc8a4854), sglang:26.07-py3, on both
GPUs: `test_cake_mm_fp4` 26 passed, `test_cake_nvfp4_quantize` 30
passed, `test_fp4_quantize` 10565 passed, `test_mm_fp4` 136 passed / 12
skipped, `test_cute_dsl_cache` 63 passed (incl. graph replay) - sm_103a
(GB300) step 0465493c, sm_100a (B200) step ce20d5d5. The first run on
the regenerate commit caught two pre-existing `test_cake_mm_fp4`
assertions that pinned the old 148-SM L2-promotion behaviour of the
lever-6 row; they now state the rule (rule commit 749e8d6d).
- compute-sanitizer 13.3 on B200, `--tool memcheck` and `--tool
synccheck` over every regenerated program (quantizer M in {1, 17, 130,
257, 512, 2048, 8192} x K in {7168, 8192, 16384, 18432, 28672}, fold /
no fold, fp16 rows; every GEMM tactic key incl. `sk2` / `sk3` / 192-wide
2-CTA) and the prepared quantizer -> GEMM chain under CUDA-graph replay:
`ERROR SUMMARY: 0 errors` for both tools (~145 launches each,
compute-sanitizer 13.3.75, step ce20d5d5 on this head; the GB300
containers have no sanitizer route, the same programs are exercised
there by the 272-row export receipts and the FlashInfer tests).
- Bitwise: every quantizer row identical to #5697 (`not_bitwise = 0`
over all 272 export rows and every A/B row); every GEMM A/B row
`torch.equal` to the #5697 output on both GPUs (`not_bitwise = 0`; the
tolerance check against the FP32 reference reports 0 violations on every
row).
- pre-commit (ruff, ruff-format, clang-format, codespell) clean on the
head on both test nodes (`PRECOMMIT_DIFF_BYTES=0`); publication guard
clean; codegen drift vs #5697 as described above (17 quantizer sources
per arch changed by one line, two new sm_100a L2-off `m128` programs
whose kernel source is byte-identical to the promoted ones, all other
generated sources byte-identical).

## 🔍 Related Issues

Tracker #4254 (NVFP4 Per-Token Quantize + GEMM). Follow-up to #5697.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [0ca06f1](https://github.com/flashinfer-ai/flashinfer/commit/0ca06f1c0f5e955ba9242cdb642145c4fd054b97)

- **作者**: Vincent
- **时间**: 2026-09-30T21:43:52Z
- **提交信息**: feat(quant): enable fused gated MXFP8 quantization (SwiGLU + MXFP8) on SM107 (Rubin) (#5392)

## What

Enables the fused gated MXFP8 quantization kernel —
`silu_and_mul_mxfp8_quantize` and its backward (SwiGLU + MXFP8
rowwise/colwise quantization) — on SM107 (Rubin). One commit.

| gate | change |
|---|---|
| `flashinfer/gated_act_mxfp8.py` `(major, minor) not in ((10, 0), (10,
3))` | add `(10, 7)` |
| `csrc/gated_act_mxfp8/gated_act_mxfp8.cu` `TVM_FFI_ICHECK(major == 10
&& (minor == 0 \|\| minor == 3))` | add `minor == 7` |
| `tests/utils/test_gated_act_mxfp8.py` `_supported()` | add `(10, 7)` |

The `_sm103`-specific backward variants stay selected by `minor == 3`
only; SM107 takes the SM100-tuned generic backward kernels, which is
functionally correct. Whether Rubin wants its own selection rule is a
perf follow-up.

## Why it is safe

The kernels use TMA bulk copies, mbarriers (CTA and cluster scope) and
packed `bf16x2`/`f32x2` math — nothing Blackwell-exclusive, no
tcgen05/TMEM, no `__CUDA_ARCH__` branches. The JIT module
(`flashinfer/jit/gated_act_mxfp8.py`) compiles with
`supported_major_versions=[10]` and `map_sm107_to_100f=False`, i.e. it
**already emits native `sm_107a` code** on a Rubin build; only the three
checks above kept the op from being called.

## Validation

GR100 (cc 10.7, driver 620.05), image
`flashinfer-ci:cu134-nightly-py3.67144516-whl-amd64` with the CI job's
`nvidia-cutlass-dsl[cu13]==4.8.0.dev0` override, against an
`upstream/main` baseline on the same tree/image:

```
tests/utils/test_gated_act_mxfp8.py   1 passed / 15 skipped  ->  15 passed / 1 skipped
```

The remaining skip is
`test_gated_act_mxfp8_sm103_backward_both_special_values`, which is
SM103-only by design. Zero new failures. Validated on x86_64 only; the
Rubin CI nodes are arm64.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added support for gated activation with MXFP8 on SM107 GPUs, alongside
SM100 and SM103.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Vincent Tombari <Vinnie6167@users.noreply.github.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [06cd11d](https://github.com/flashinfer-ai/flashinfer/commit/06cd11d14c1964f99d11ffc7d85ca4252745e119)

- **作者**: eigen
- **时间**: 2026-09-30T21:20:38Z
- **提交信息**: feat(cake_sampling): round-6 radix sampling bundle: coarse-sample stage-1 twins, row-span filter arm and small-k dispatch re-fit (#5731)

## Summary

Round 6 of the cake exact radix top-k / top-p sampling route
(`flashinfer.cake_sampling`): the frozen bundle is refreshed with two
kernel-level levers and every output stays **bit-identical** to the
round-5 bundle (exact top-k set, exact top-p cut, same Philox sample,
same tie-breaking; no approximation of any kind).

* **Coarse-sample stage-1 twins** (`_cs`, `launch_flags` bit 4). Every
streaming stage-1 variant ships a second build whose sampled first pass
histograms every 8th entry of the row instead of every 4th (lower-bucket
margin, sampled-mass cap and filter-arm density factor scaled to the
rate). The exact passes are unchanged. The host takes the twin for
launches whose largest top-k fits the two-warp fused tail (`top_k_max <=
64`); larger top-k launches keep the default build, which is
byte-identical to round 5 (a k ~ 1000 row's candidate list sits at the
gather capacity, where the coarser estimate sends 3-12 % of the rows
down the slower path).
* **Row-span filter arm** (`launch_flags` bit 5). A streaming variant's
filter pass chooses its float-threshold arm from the expected candidate
density of the whole row instead of one CTA's span (the round-5 test
compared the cluster-wide sampled mass with a single CTA's span, CLUSTER
x too strict for multi-CTA rows). Both arms build identical candidate
segments. The host sets the bit for cluster >= 8 streams whose largest
top-k exceeds the two-warp tail on compute capability 9.0 / 10.0 / 10.3;
Rubin measures neutral and keeps the round-5 test.

* **Small-k dispatch re-fit** (host only, `_STAGE1_COST_BY_SM_COUNT` 148
/ 212). Policy-aware stage-1 sweeps of every frozen variant
(coarse-sample twins at k <= 64) on B200, GB300 and R200 showed the
round-5 tables 3-4.5 % off the measured best at V = 151936 B <= 8 (148:
the (8,16) stream where (8,32) wins) and at V = 128256 / 151936 B <= 16
(212: cluster-8 streams where (4,32) wins). The re-fit is constrained so
that no k > 64 pick changes and no cell's pick gets slower (worst regret
4.5 -> 2.8 % on 148, 4.1 -> 1.7 % on 212; 132 unchanged, its 3.7 %
residual is a batch-dependent ept-32 cost the chunk-linear model does
not express). Pinned picks in the tests follow;
`docs/api/cake_sampling.rst` describes the re-fit and carries the
round-6 per-cell tables.

Bundle: 46 kernels (28 stage-1 builds: 12 defaults, 8 whole-CTA-tail
twins, 8 coarse-sample twins; 18 stage-2/3 forms), four source parts
under the mirror's 5 MiB limit, manifest `source_sha256`
`b9772a6551fb5338…`. Manifest stage-1 entries carry `coarse_sample`; the
JIT validates it (stream only, exclusive with `fused_block_tail`, a twin
requires its default build); the binding gains
`Stage1Variant.coarse_sample`, `kFlagCoarseSample` (build selection,
never forwarded to the kernel) and `kFlagRowSpanDiet` (forwarded;
rejected on register-resident variants). sm_120 / sm_121 keep the
`top_k_first` fallback semantics and the host API is unchanged.

## Performance (stage-1 paired A/B vs the round-5 kernels, same run,
cold L2, CUPTI medians, all bit-exact)

Coarse sample, k = 50 (ratio new / round 5):

| cell | B200 | GB300 | H100 | R200 |
|---|---|---|---|---|
| V 262144 B 128 cluster 1 | 0.931 | 0.911 | 0.911 | 0.910 |
| V 262144 B 64 cluster 2 | 0.935 | 0.955 | 0.925 | 0.922 |
| V 262144 B 32 cluster 4 | 1.000 | 0.977 | 0.983 | 0.961 |
| V 262144 B 8 cluster 8 | 0.982 | 0.986 | 0.987 | 0.991 |

Row-span filter arm, k = 1000 (bit 5 set vs clear):

| cell | B200 | GB300 | H100 | R200 (not enabled) |
|---|---|---|---|---|
| V 262144 B 16 cluster 8 | 0.969 | 0.970 | 0.963 | 0.998 |
| V 262144 B 8 cluster 8 | 0.978 | 0.977 | 0.963 | 1.007 |
| V 262144 B 1 cluster 8 | 0.983 | 0.980 | 0.951 | 1.011 |

End-to-end speedup summary (same run, CUPTI medians, eager + CUDA graph,
192 cells per GPU; full per-cell tables in
`docs/api/cake_sampling.rst`):

| GPU | vs `top_k_first`, all 192 cells (min / median / max) | vs
round-5 bundle, k <= 64 (median / max; B >= 32 median) | vs round-5
bundle, k = 1000 (median) | cells slower than `top_k_first` |
|---|---|---|---|---|
| B200 (sm_100a) | 1.63x / 3.97x / 8.62x | 1.020x / 1.101x; 1.027x |
1.000x | 0 of 192 |
| GB300 (sm_103a) | 1.67x / 4.17x / 14.56x | 1.016x / 1.102x; 1.026x |
1.001x | 0 of 192 |
| H100 (sm_90a) | 1.67x / 3.47x / 8.88x | 1.007x / 1.100x; 1.051x |
1.038x | 0 of 192 |
| R200 (sm_107a) | 1.58x / 3.69x / 7.26x | 1.022x / 1.103x; 1.048x |
1.000x | 0 of 192 |

End-to-end 192-cell matrix (fi-base = round-5 bundle vs this bundle,
eager + CUDA graph, k in {10, 50, 1000}, B in {1..128}, V in {32768,
128256, 151936, 262144}) on B200 / GB300 / H100 / R200: every cell
faster than `top_k_first` (B200 1.63-8.62x, GB300 1.67-14.56x, H100
1.67-8.88x, R200 1.58-7.26x); k <= 64 vs the round-5 bundle median 1.02x
on B200 / GB300 (B >= 32: up to 1.10x from the coarse sample; V = 151936
B <= 8: 2-4 % from the re-fit), 1.01x on H100 (B >= 32 median 1.05x),
1.02x on R200 (B >= 32 median 1.05x; V = 128256 / 151936 B <= 16: 2-5 %
from the re-fit); k = 1000 median 1.00x on Blackwell and 1.04x on H100
(graph rows 1.03-1.09x from the row-span diet). Every cell slower in
both matrix orders was re-measured in independent processes: none
regresses on B200 / H100; one GB300 cell (V = 128256, B = 64, k = 1000,
eager) stays +0.9 % (28.8 -> 29.1 us) with a byte- and time-identical
stage 1 (the difference is in the stage-2/3 launch queued behind the
(2,32) stream; CUDA graph +0.2 %). On R200 the both-order k = 1000 graph
rows (V = 262144, B = 1 / 2) are neutral in independent processes.

## Tests

* `tests/utils/test_cake_sampling.py`: new
`test_coarse_sample_build_matches_default_build` and
`test_row_span_diet_flag_matches_default_build` (bitwise slab / count /
samples / renorm with the flag set vs clear for every streaming variant,
k in {10/50, 64, per-row, 1000, 200}, four vocabularies; rejection of
the bits on register-resident variants; host policy on `choose_stage1`
picks).
* `tests/utils/test_cake_sampling.py` +
`tests/utils/test_cake_sampling_upstream.py`: 252 passed / 18 skipped on
B200, GB300, H100 and R200 (this bundle, the round-6 dispatch tables);
sm_120 on a real RTX PRO 6000 Blackwell (dlcluster, this bundle
@757bee91, 46 kernels): 250 passed / 20 skipped (the top_k_first route
is unchanged there; the streaming variants are not dispatch candidates
on 99 KB devices).
* compute-sanitizer synccheck + memcheck (every frozen stage-1 variant x
fused / two-launch / whole-CTA tail, both sample builds, bit 5 on the
two-launch streams): `ERROR SUMMARY: 0 errors` for synccheck and
memcheck on B200 and R200 (336 launches each in the repro harness, plus
the two `bench-regression` cells).
* sglang e2e parity on B200 (Qwen GSM8K 8-shot, n = 1319, temperature
0.7, k = 50, p = 0.9): cake route 0.697 vs `top_k_first` 0.702 / 0.705
(two seeds) vs joint 0.688 / 0.711; greedy 0.941 (k = 1 route 0.955 vs
0.94); k = 1000 `top_k_first` 0.704 vs joint 0.694 -- all inside the
seed-to-seed spread (2.4 points). Next-token histograms (4096 samples x
6 prompts, k in {10, 50}): 0 samples outside the exact support for every
arm; max TV vs the exact masked distribution cake 0.095 / 0.071 vs
`top_k_first` 0.104 / 0.075.

## Source PRs

This bundle builds on the previously merged cake sampling PRs: #5439,
#5482, #5585, #5607, #5636, #5684.

## Related

Cake design doc `design_doc/active/CAKE_536_RADIX_SAMPLING_PIPELINE.md`
§ "Round 6 (CAKE-776)" (lever ledger, roofline, convergence statement);
Linear CAKE-776.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added coarse sampling for supported streaming workloads with smaller
top-k values, using a 1/8 first-pass sample.
* Added a row-span filtering option for eligible larger top-k workloads
on Hopper, B200, and GB300 GPUs. Both options preserve results.

* **Performance**
  * Updated dispatch tuning for selected GPU configurations.

* **Documentation**
* Updated performance measurements and documented the sampling and
filtering options.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [5ce4ef8](https://github.com/flashinfer-ai/flashinfer/commit/5ce4ef801f3606ff38779ca9f88a344779f21c82)

- **作者**: Chunan Zeng
- **时间**: 2026-09-30T20:12:08Z
- **提交信息**: perf(mla): deepen FP8 and FP16/BF16 decode load pipelines on SM107 (#5703)

## 📌 Description

The monolithic CuTe DSL FP8 MLA decode kernel (the default path of
`trtllm_batch_decode_with_kv_cache_mla(backend="cute-dsl")` for FP8 KV)
keeps 3 K and 2 V load stages. That is about 224 KB of shared memory per
CTA, right at the default 227 KB limit.

sm_107 allows 327 KB per CTA: CuTe DSL >= 4.8 lists 327 KB for `sm_107`
and launches the kernel with the oversized shared memory mode. That is
enough for 4 K and 4 V stages (~324 KB). Deeper V buffering keeps more
KV bytes in flight where decode is HBM bound.

This PR selects FP8 4/4 K/V load stages when the resolved launch
architecture is `sm_107` or `sm_107a`. Other targets retain 3/2,
including SM100/SM103 and the `sm_100f` fallback used by older CuTe DSLs
without native SM107 support. The resolved architecture is passed to the
kernel, included in its compilation cache key, and explicitly supplied
to `cute.compile`.

The shared FP16/BF16 kernel also uses 8 rather than 7 KV load stages for
multi-token queries on native SM107. Single-token queries retain 15
stages, and other architectures retain their existing 15/7 selection.
This change only deepens KV buffering; QK tiling, TMEM allocation, and
softmax math are unchanged.

Per-CTA shared memory of the split-KV kernel (2-CTA, FP8): K 36 KB/stage
(latent 32 + rope 4), V 32 KB/stage, Q 36 KB, P 16 KB. The launched
split kernel goes from 232448 B to 334848 B of dynamic shared memory
(kineto trace).

## Validation

### FP16/BF16 multi-token KV staging

SM107 on nv-slurm (`vr-r38-cn02`), CuTe DSL 4.8.0.dev0, H=12, Q=8,
batch=16, KV length=max_seq_len=131072, page size=64, latent/RoPE
dimensions=512/64, PDL enabled, fixed sequence lengths. Compared the
updated PR with the same source using the previous 7-stage setting.
Timed the full monolithic decode plus split-KV reduction using CUDA
events over five-call CUDA graphs; 5 shuffled rounds x 30 replays,
median us/call. BF16 output for both input dtypes.

| Input/KV dtype | 7 stages (us) | 8 stages (us) | Latency change |
|---|---:|---:|---:|
| BF16 | 298.11 | 283.08 | -5.0% |
| FP16 | 295.49 | 280.32 | -5.1% |

Both are bit-identical to the 7-stage baseline and pass an FP32
causal-attention reference check (maximum absolute error < 0.001). This
performance result covers the stated shape; it does not establish a
speedup across all multi-token workloads.

Reproduction artifacts: nv-slurm
`/home/sgl-chunan-zeng/mla5703-bf16/{bench.py,source.tgz,run.sbatch}`,
benchmark job 1124. `bench.py` compiles baseline and updated variants
from the same source and alternates their measurement order.

### FP8 K/V staging

sm_107, CuTe DSL 4.8.0.dev0, public
`trtllm_batch_decode_with_kv_cache_mla(backend="cute-dsl")`, FP8 KV,
page size 64, `max_seq_len` 1M (CUDA-graph case), cold KV with distinct
pages per request, CUDA-graph us/call, mean of 2 rounds, this PR vs its
parent:

| KV length | batch | change | example |
|---|---|---|---|
| 64k / 128k | 4-32 | -9% to -16% | B16 H12 q_len 8, 128k: 149.9 ->
125.5 us |
| 64k / 128k | 64 | -1% to -5% | |
| 64k / 128k | 1 | -0.5% to -2% | |
| 8k | 64 | -4% to -6% | |
| 8k | 1 | 0 to +0.5% | |
| 8k | 4-32 | +0.7% to +4.2% | B16 H12 q_len 8, 8k: 21.5 -> 22.4 us |

Shapes: H12 with q_len 1 and 8, H128 with q_len 1. Output is
bit-identical to the parent on all 36 shapes: the stage count only
changes pipelining.

<details>
<summary>Per-shape results, this PR vs main (36 shapes)</summary>

**Method.** Each shape is timed as one CUDA graph of 32 calls rotating
over 4 input sets (4 separate KV pools, each request on its own pages,
so KV reads come from HBM). us/call is the median of the last 6 of 7
graph replays, then the median of 3 such measurements; the table
averages 2 rounds that alternate main and this PR in separate processes.
`seq_lens` are uniform per batch. For reference, a device-to-device
`torch` copy on this GPU reaches ~13.1 TB/s (read + write) at 1.2 GB.

| H | q_len | batch | KV | main (us) | this PR (us) | change | round 1 /
round 2 | KV read TB/s (main -> PR) |
|---:|---:|---:|---:|---:|---:|---:|---|---:|
| 12 | 1 | 1 | 8k | 8.65 | 8.65 | +0.0% | +0.0% / +0.0% | 0.5 -> 0.5 |
| 12 | 1 | 4 | 8k | 10.49 | 10.65 | +1.5% | +1.8% / +1.2% | 1.8 -> 1.8 |
| 12 | 1 | 16 | 8k | 15.93 | 16.04 | +0.7% | +0.6% / +0.8% | 4.7 -> 4.7
|
| 12 | 1 | 64 | 8k | 39.92 | 37.55 | -5.9% | -5.9% / -6.0% | 7.6 -> 8.0
|
| 12 | 1 | 1 | 64k | 16.38 | 16.26 | -0.8% | -0.9% / -0.7% | 2.3 -> 2.3
|
| 12 | 1 | 4 | 64k | 23.43 | 23.29 | -0.6% | -0.6% / -0.6% | 6.4 -> 6.5
|
| 12 | 1 | 16 | 64k | 67.11 | 57.72 | -14.0% | -13.8% / -14.2% | 9.0 ->
10.5 |
| 12 | 1 | 64 | 64k | 277.78 | 274.03 | -1.3% | -0.6% / -2.1% | 8.7 ->
8.8 |
| 12 | 1 | 1 | 128k | 24.41 | 23.95 | -1.9% | -1.9% / -1.8% | 3.1 -> 3.2
|
| 12 | 1 | 4 | 128k | 40.39 | 36.00 | -10.9% | -10.9% / -10.8% | 7.5 ->
8.4 |
| 12 | 1 | 16 | 128k | 126.18 | 114.00 | -9.5% | -3.7% / -15.2% | 9.6 ->
10.6 |
| 12 | 1 | 64 | 128k | 557.60 | 553.11 | -0.8% | -0.9% / -0.7% | 8.7 ->
8.7 |
| 12 | 8 | 1 | 8k | 9.93 | 9.98 | +0.5% | +0.5% / +0.5% | 0.5 -> 0.5 |
| 12 | 8 | 4 | 8k | 13.11 | 13.34 | +1.8% | +2.1% / +1.5% | 1.4 -> 1.4 |
| 12 | 8 | 16 | 8k | 21.50 | 22.39 | +4.2% | +4.6% / +3.7% | 3.5 -> 3.4
|
| 12 | 8 | 32 | 8k | 37.59 | 38.89 | +3.5% | +0.3% / +6.7% | 4.0 -> 3.9
|
| 12 | 8 | 64 | 8k | 41.99 | 40.16 | -4.4% | -4.3% / -4.4% | 7.2 -> 7.5
|
| 12 | 8 | 1 | 64k | 18.07 | 17.98 | -0.5% | -0.4% / -0.6% | 2.1 -> 2.1
|
| 12 | 8 | 4 | 64k | 29.26 | 28.46 | -2.7% | -2.9% / -2.6% | 5.2 -> 5.3
|
| 12 | 8 | 16 | 64k | 77.09 | 65.78 | -14.7% | -14.2% / -15.1% | 7.8 ->
9.2 |
| 12 | 8 | 32 | 64k | 151.18 | 130.32 | -13.8% | -14.5% / -13.1% | 8.0
-> 9.3 |
| 12 | 8 | 64 | 64k | 301.02 | 291.99 | -3.0% | -3.2% / -2.8% | 8.0 ->
8.3 |
| 12 | 8 | 1 | 128k | 26.38 | 25.87 | -2.0% | -1.9% / -2.0% | 2.9 -> 2.9
|
| 12 | 8 | 4 | 128k | 45.33 | 41.02 | -9.5% | -9.4% / -9.7% | 6.7 -> 7.4
|
| 12 | 8 | 16 | 128k | 149.85 | 125.50 | -16.2% | -16.5% / -16.0% | 8.1
-> 9.6 |
| 12 | 8 | 32 | 128k | 301.69 | 270.22 | -10.4% | -10.6% / -10.2% | 8.0
-> 8.9 |
| 12 | 8 | 64 | 128k | 596.95 | 588.33 | -1.4% | -1.6% / -1.3% | 8.1 ->
8.2 |
| 128 | 1 | 1 | 8k | 10.11 | 10.14 | +0.2% | +0.4% / +0.1% | 0.5 -> 0.5
|
| 128 | 1 | 16 | 8k | 24.17 | 24.61 | +1.8% | +1.5% / +2.2% | 3.1 -> 3.1
|
| 128 | 1 | 64 | 8k | 42.30 | 40.25 | -4.8% | -4.6% / -5.1% | 7.1 -> 7.5
|
| 128 | 1 | 1 | 64k | 18.27 | 18.13 | -0.7% | -0.5% / -0.9% | 2.1 -> 2.1
|
| 128 | 1 | 16 | 64k | 79.68 | 67.90 | -14.8% | -14.7% / -14.8% | 7.6 ->
8.9 |
| 128 | 1 | 64 | 64k | 311.33 | 297.24 | -4.5% | -4.4% / -4.7% | 7.8 ->
8.1 |
| 128 | 1 | 1 | 128k | 26.52 | 26.05 | -1.8% | -1.7% / -1.8% | 2.8 ->
2.9 |
| 128 | 1 | 16 | 128k | 153.33 | 132.67 | -13.5% | -10.7% / -16.3% | 7.9
-> 9.1 |
| 128 | 1 | 64 | 128k | 615.06 | 602.52 | -2.0% | -1.8% / -2.3% | 7.9 ->
8.0 |

</details>

Stage sweep at 64k/128k (20 shapes, mean / worst change vs 3/2):

| K/V stages | smem (KB) | mean | worst |
|---|---|---|---|
| 2/3 | ~220 | +3.9% | +20.3% |
| 2/4 | ~252 | -2.0% | +12.8% |
| 3/3 | ~256 | -7.5% | +1.2% |
| 3/4 | ~288 | -7.5% | +1.6% |
| 3/5 | ~320 | -8.7% | +0.4% |
| 4/4 | ~324 | -8.7% | -0.6% |

4/4 is the only split that is never slower than 3/2. More K stages with
2 V stages are slower (4/2 up to +12%, 5/2 up to +27%). 2/3, the only
deeper-V split that fits the default 227 KB limit, is slower at B1 and
B64, so sm_100/sm_103 are left unchanged.

<details>
<summary>Per-shape stage sweep, 64k/128k (20 shapes; change vs
3/2)</summary>

Same inputs and CUDA-graph timing (median of 7 replays). Variants are
compiled from the same source with only `load_k_stage` / `load_v_stage`
changed, and timed interleaved in one process in shuffled order, 3
measurements each (median), mean of 2 rounds. Outputs of every variant
are bit-identical to 3/2.

| H | q_len | batch | KV | 3/2 (us) | 2/3 | 2/4 | 2/5 | 3/3 | 3/4 | 3/5
| 4/4 |
|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 12 | 1 | 1 | 64k | 15.91 | +9.8% | +5.5% | +0.0% | -0.2% | -0.4% |
-0.7% | -0.6% |
| 12 | 1 | 4 | 64k | 23.05 | +5.4% | +2.8% | -0.4% | -1.0% | -0.8% |
-1.7% | -0.7% |
| 12 | 1 | 16 | 64k | 72.80 | -1.8% | -9.3% | -13.9% | -11.4% | -14.1% |
-15.9% | -17.5% |
| 12 | 1 | 64 | 64k | 278.65 | +20.3% | +12.8% | +0.8% | +1.2% | +1.6% |
-3.6% | -5.4% |
| 12 | 1 | 1 | 128k | 24.11 | +14.1% | +7.9% | +0.2% | -0.5% | -0.9% |
-1.5% | -1.6% |
| 12 | 1 | 4 | 128k | 39.93 | -0.4% | -4.6% | -8.1% | -8.2% | -8.6% |
-9.8% | -10.0% |
| 12 | 1 | 16 | 128k | 150.84 | -7.6% | -11.4% | -17.1% | -19.4% |
-17.7% | -20.6% | -20.5% |
| 12 | 1 | 64 | 128k | 581.51 | +13.6% | +4.7% | +0.2% | -1.1% | -2.2% |
-3.8% | -3.6% |
| 12 | 8 | 1 | 64k | 17.11 | +10.4% | +5.6% | +0.8% | +0.3% | +0.1% |
+0.4% | -0.6% |
| 12 | 8 | 4 | 64k | 28.24 | +0.4% | -1.1% | -3.8% | -3.4% | -2.2% |
-2.6% | -2.2% |
| 12 | 8 | 16 | 64k | 81.15 | -5.7% | -10.2% | -13.8% | -11.9% | -9.7% |
-15.6% | -15.4% |
| 12 | 8 | 32 | 64k | 164.97 | -1.5% | -10.0% | -14.8% | -15.5% | -15.2%
| -14.4% | -16.8% |
| 12 | 8 | 64 | 64k | 300.26 | +11.8% | +9.4% | +1.2% | +0.6% | -0.7% |
-4.2% | -3.1% |
| 12 | 8 | 1 | 128k | 25.38 | +14.5% | +7.4% | +0.8% | -0.2% | -0.3% |
-0.2% | -2.0% |
| 12 | 8 | 4 | 128k | 44.87 | -3.4% | -5.0% | -8.4% | -10.1% | -9.8% |
-11.0% | -10.4% |
| 12 | 8 | 16 | 128k | 162.97 | +0.2% | -13.8% | -19.5% | -15.9% |
-17.3% | -15.7% | -13.8% |
| 12 | 8 | 32 | 128k | 342.37 | -8.0% | -13.8% | -23.3% | -23.4% |
-19.8% | -20.4% | -18.7% |
| 12 | 8 | 64 | 128k | 620.50 | +11.4% | +2.9% | -2.0% | -1.5% | -2.0% |
-2.5% | -1.3% |
| 128 | 1 | 16 | 64k | 84.41 | -1.6% | -6.5% | -9.2% | -9.7% | -12.4% |
-12.8% | -11.5% |
| 128 | 1 | 16 | 128k | 173.09 | -4.3% | -13.1% | -18.8% | -17.7% |
-17.6% | -17.4% | -18.2% |

A separate earlier run adds 4/2, 5/2 and 4/3 (18 shapes; 3/3..4/4 are
repeated there, so the two runs can be compared):

| H | q_len | batch | KV | 3/2 (us) | 4/2 | 5/2 | 4/3 | 3/3 | 3/4 | 3/5
| 4/4 |
|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 12 | 1 | 4 | 64k | 23.09 | +8.2% | +13.9% | -2.0% | -1.2% | -1.0% |
-2.0% | -0.4% |
| 12 | 1 | 16 | 64k | 73.57 | +10.6% | +18.3% | -7.4% | -13.3% | -14.9%
| -17.1% | -18.4% |
| 12 | 1 | 64 | 64k | 279.00 | +11.3% | +17.4% | -2.6% | +1.4% | +0.2% |
-1.8% | -1.5% |
| 12 | 1 | 4 | 128k | 39.93 | +12.0% | +18.6% | +0.0% | -7.7% | -8.3% |
-9.2% | -9.4% |
| 12 | 1 | 16 | 128k | 148.67 | +10.9% | +16.5% | -10.2% | -17.9% |
-16.9% | -19.4% | -19.5% |
| 12 | 1 | 64 | 128k | 578.93 | +8.2% | +12.3% | -1.0% | -2.0% | -1.3% |
-2.8% | +0.6% |
| 12 | 8 | 1 | 64k | 17.11 | -0.2% | -0.1% | -0.4% | +0.2% | +0.3% |
+0.4% | -0.6% |
| 12 | 8 | 4 | 64k | 28.19 | +6.2% | +7.3% | -0.4% | -1.9% | -0.4% |
-1.0% | -0.5% |
| 12 | 8 | 16 | 64k | 79.50 | +11.8% | +17.8% | -4.0% | -12.2% | -12.1%
| -8.3% | -8.0% |
| 12 | 8 | 32 | 64k | 168.12 | +2.3% | +12.9% | -13.9% | -17.8% | -16.5%
| -20.6% | -17.9% |
| 12 | 8 | 64 | 64k | 297.72 | +10.3% | +18.9% | -2.2% | -3.3% | +0.4% |
-0.4% | -1.2% |
| 12 | 8 | 1 | 128k | 25.44 | -1.8% | -1.8% | -1.9% | -0.4% | -0.5% |
-0.3% | -2.1% |
| 12 | 8 | 4 | 128k | 44.74 | +7.4% | +12.9% | -2.8% | -7.0% | -8.2% |
-10.6% | -10.1% |
| 12 | 8 | 16 | 128k | 165.00 | +5.6% | +11.3% | -13.8% | -18.0% |
-19.7% | -16.1% | -19.8% |
| 12 | 8 | 32 | 128k | 336.52 | +1.5% | +12.9% | -4.5% | -20.4% | -27.1%
| -17.4% | -25.4% |
| 12 | 8 | 64 | 128k | 627.18 | +6.9% | +9.2% | -2.9% | -3.5% | -2.9% |
-4.6% | -2.8% |
| 128 | 1 | 16 | 64k | 84.07 | +8.7% | +14.5% | -3.6% | -6.0% | -13.6% |
-16.8% | -9.6% |
| 128 | 1 | 16 | 128k | 157.95 | +12.5% | +26.7% | +0.4% | -15.8% |
-12.1% | -15.2% | -7.0% |

</details>

The 8k regression at batch 4-32 remains (at most ~1.3 us/call). The
stage count is compile-time, and CUDA-graph callers pass the maximum
context as `max_seq_len`, so it cannot be gated on the runtime KV
length.

## 🔍 Related Issues

<!-- Link any related issues here -->

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

- [x] Added FP16/BF16 architecture-stage regression coverage and
extended the architecture-separated compilation-cache test to FP16,
BF16, and FP8.
- [x] SM107 job 1125: **268 passed, 466 deselected**, covering
monolithic FP16/BF16 decode, packed and variable query layouts,
CUDA-graph replay, DCP, architecture-stage selection, and compile-cache
separation.
- [x] All pre-commit hooks passed for the three files changed by the
FP16/BF16 update, including mypy and Ruff.
- [x] `tests/attention/test_cute_dsl_mla_decode.py` and
`tests/attention/test_cute_dsl_mla_dcp.py`, FP8 selection: 99 passed on
sm_107, before and after.
- [x] `ruff check` / `ruff format` clean on the changed file.

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

The FP16/BF16 stage increase applies only to multi-token queries
compiled for native SM107. SM100/SM103 and family-fallback targets
retain existing staging. The FP8 short-context tradeoff is documented
above; the added FP16/BF16 performance measurement covers
H12/Q8/B16/128K.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Improvements**
* MLA decoding now compiles kernels using settings matched to the GPU
architecture, with compiled kernels cached separately for each
architecture.
* FP8 decoding uses architecture-specific load configurations on newer
GPUs. FP16 decoding uses architecture-specific pipeline configurations,
including for multi-query decoding.
* Existing configurations remain in use on other architectures and for
single-query FP16 decoding.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Chunan Zeng <zcnrex@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [6811376](https://github.com/flashinfer-ai/flashinfer/commit/6811376a2610921d20046d61299a2bd1fb904876)

- **作者**: Ligeng Zhu
- **时间**: 2026-09-30T19:53:22Z
- **提交信息**: feat(kda): kda-for-kda CAKE PTX impl (#5665)

<!-- .github/pull_request_template.md -->

## 📌 Description

Adds `flashinfer.recurrent_kda(..., backend="ptx")` for **Kimi Delta
Attention** prefill on B300. The backend imports the four retained
static PTX programs and TVM FFI shims from
[`kda-cake-ptxver/`](https://github.com/humanfia/kda-for-kda-release/tree/e4fcf0efaea6b6ac4d76ec1a0c137dc04532c925/kda-cake-ptxver),
with byte-preserving source hashes and the original MIT license.

- Exact Q/K L2 normalization, K3 gate and beta sigmoid, and FP32 V-first
recurrent state. The host scheduler retains exact state handoffs and
removes approximate split planning and expected-norm substitution.
- Explicit `backend="ptx"`; default dispatch is unchanged. Supports
contiguous BF16 B=1, H64/H96, D128; at least 32 total tokens; fixed and
packed sequences with individual lengths 1–16384. FP32 initial state
must be finite with absolute values <=4096. Other contracts are rejected
explicitly.
- Caller-owned output, in-place state updates, stream-bound workspaces,
per-plan TMA descriptors, and warmed CUDA Graph capture/replay. Handoff
flags are cleared on every launch. Packed offsets remain fixed during
graph replay.
- PTX ISA 9.2 is assembled with ptxas >=13.2 and embedded as cubins. The
cache includes assembler and source identity, uses atomic publication,
and writes outside the installed package. The backend honors
`FLASHINFER_DISABLE_JIT` and is JIT-only. Install the optional `ptx`
extra or supply a compatible toolkit.

**Operator:** Kimi Delta Attention  
**Baseline:**
[MoonshotAI/FlashKDA](https://github.com/MoonshotAI/FlashKDA/tree/7afb9f454f160a6c4bbc0999beca0a8c40a38934)
(`7afb9f4`, raw fused CUTLASS forward)
**Shapes:** INT21's six workloads, each with 8192 total tokens and D128;
H96/H64, with `[8192]`, `[1300, 547, 2048, 963, 271, 3063]`, or `[1024]
* 8` sequence lengths.
**Speedup:** **2.918x measured geometric mean on B300**. The original
reported result for this contribution is **2.94x**; the fresh public-API
measurements below are reported separately.

| Workload | FlashKDA (ms) | PTX public API (ms) | Speedup |
|---|---:|---:|---:|
| h96-fixed | 0.999366 | 0.360258 | 2.774x |
| h96-mixed_varlen | 0.876597 | 0.273425 | 3.206x |
| h96-uniform_varlen | 0.713828 | 0.268177 | 2.662x |
| h64-fixed | 0.905798 | 0.322306 | 2.810x |
| h64-mixed_varlen | 0.656980 | 0.188321 | 3.489x |
| h64-uniform_varlen | 0.482691 | 0.181634 | 2.657x |
| **Geometric mean speedup** | | | **2.918x** |

Validated commit: `040dfd95389b74e0a08598c488e4b80c5a5a1807`.

Measurements: NVIDIA B300 SXM6 AC, SM103 / 148 SMs, driver 595.58.03;
torch 2.12.1+cu130, CUDA toolkit/ptxas 13.2, TVM FFI 0.1.14.post1, FLA
0.5.2, CUPTI Python 13.0.1. Both arms update FP32 state in place and are
captured once. Timing uses cold-L2 CUPTI GPU activity spans, three
trials of 30 iterations after three warmups, alternating
candidate/baseline order; medians within and across trials. States
evolve during timing and reset before each trial. Allocation,
compilation, planning, capture, state reset, and CPU overhead are
outside timing. These are captured GPU-call results, not eager
wall-clock or whole-model throughput.

Both outputs of both arms pass the INT21 accuracy gate against FLA's
independent Triton reference: relative L2 <=0.03, and elementwise error
<=max(0.5 * reference RMS, 0.05 * absolute reference).

```bash
# Build the pinned baseline in place with CUDA >=13.2 for SM103a.
git clone --recursive https://github.com/MoonshotAI/FlashKDA.git /tmp/FlashKDA
git -C /tmp/FlashKDA checkout 7afb9f454f160a6c4bbc0999beca0a8c40a38934
git -C /tmp/FlashKDA submodule update --init --recursive
(cd /tmp/FlashKDA && FLASH_KDA_CUDA_ARCHS=103a python setup.py build_ext --inplace)

# From the FlashInfer checkout, in the environment containing FlashInfer,
# fla-core==0.5.2, cupti-python==13.0.1, and the PTX dependencies:
python benchmarks/bench_recurrent_kda_ptx.py \
    --flash-kda-source-dir /tmp/FlashKDA --output ptx-results.json
```

The benchmark emits absolute/trial latencies, accuracy checks, routes,
baseline revision and extension hash, assembler version, PTX manifest
hash, and public adapter hash. Frozen payload manifest:
`e9bc1b3480505ef8d22a43c26254fb57f6768859e30043918f9b0b9f1c4f4552`.

## 🔍 Related Issues

Related KDA integration work: #4845, #4675, #4445.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] The repository's installed pre-commit hook passes on this commit.
- [x] I have run `pre-commit run` on every changed file and fixed
reported issues. The full unrelated repository was not reformatted.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] The targeted B300 suite passes: **44 passed**.

```bash
pytest tests/kda/test_recurrent_kda_ptx.py -q
```

Coverage includes FP64 recurrence comparisons, all six INT21 shapes,
small/zero Q/K norms, weak decay, non-aligned sequence tails, optional
initial/final state, output ownership, in-place state updates,
non-default streams, changing graph inputs, eager/capture/replay
ordering, offset mutation, and invalid-contract rejection. Also checked:
28/28 source/imported exact schedule row comparisons, 12/12 frozen
payload hashes, editable installation with the MIT license, and the
JIT-disable guard. Hardware qualification is B300 only.

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

The retained `.ptx`, `.cc`, and argument metadata are unchanged; the
integration and host scheduling changes are in
`flashinfer/kda_prefill_ptx.py` and `flashinfer/kda_kernels/ptx/`. The
source revision and individual file hashes are in
`csrc/kda/ptx/manifest.json`. This adds an explicit prefill backend
alongside the existing Cake/CuTe backends; it does not extend decode,
state-pool, checkpoint, or speculative contracts.

AI-assisted implementation and local B300 validation.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added an opt-in PTX backend for recurrent KDA prefill on supported
SM103a GPUs, with documented input, sequence-length, and state
requirements.
* Added prepared-launch support and CUDA Graph capture and replay with a
warmed, caller-provided workspace.
* Added a benchmark comparing PTX prefill performance with FlashKDA
across supported workloads.
* **Documentation**
* Added guidance on backend setup, supported workloads, graph usage, and
benchmarking.
* **Bug Fixes**
* Unsupported options and invalid inputs for the PTX backend now produce
clear errors.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Ligeng Zhu <7783214+Lyken17@users.noreply.github.com>
Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [1026e73](https://github.com/flashinfer-ai/flashinfer/commit/1026e73a15de260db258df26820ed45e0d9a7b97)

- **作者**: eigen
- **时间**: 2026-09-30T19:50:46Z
- **提交信息**: feat(cake_bgmv_moe): SM90/SM100/SM103 support and cake_bgmv_moe naming for the deterministic multi-LoRA BGMV MoE backend (#5727)

Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

## Description

Follow-up to #4821 (deterministic prepared multi-LoRA BGMV MoE backend).
Two changes:

**1. SM90, SM100 and SM103 support.** The generated shrink/expand
programs use `cp.async`, warp shuffles and FMA only, so one source body
now builds one module per data-center target:

| target | devices | nvcc flags | module URI |
|---|---|---|---|
| `sm90a` | H100 / H200 (CC 9.0) | `sm90a_nvcc_flags` |
`cake_bgmv_moe_<dtype>_h<hidden>_sm90a` |
| `sm100a` | B200 / GB200 (CC 10.0) | `sm100a_nvcc_flags` |
`cake_bgmv_moe_<dtype>_h<hidden>_sm100a` |
| `sm103a` | B300 / GB300 (CC 10.3) | `sm103a_nvcc_flags` |
`cake_bgmv_moe_<dtype>_h<hidden>_sm103a` |

`prepare_bgmv_moe` routes by `torch.cuda.get_device_capability()`; every
other capability (including 12.x) still fails closed. The binding checks
that the device matches the compiled target
(`CAKE_BGMV_MOE_CC_MAJOR/MINOR`) instead of hard-coding 10.0. AOT
registers each target when its exact capability is requested. The
schedule selector keeps one table for all three targets: a per-shape
sweep of the three expand schedules (`token_owned_t64` / `token_owned` /
`token_owned_dual_col`, BF16, CUPTI cold-L2, two interleaved rounds)
over the 14 serving shapes puts them within **1.2 %** of each other on
B200 (worst chosen-vs-best 1.012 at h2688 t256) and within **3.5 %** on
H100 (worst 1.035 at h2688 t1024, where `token_owned_dual_col` trails
`token_owned` by ~3 %). The shared table is kept; no per-target selector
was introduced for that gap (see the docstring of
`select_cake_bgmv_moe_schedule`).

**2. Cake naming.**

| before | after |
|---|---|
|
`csrc/blackwell_bgmv_moe/sm100a/blackwell_bgmv_moe_{bf16,f16}_h{2688,3072}_sm100a.cu`
| `csrc/cake_bgmv_moe/cake_bgmv_moe_{bf16,f16}_h{2688,3072}.cu` |
| `csrc/blackwell_bgmv_moe/sm100a/blackwell_bgmv_moe_binding.cuh` |
`csrc/cake_bgmv_moe/cake_bgmv_moe_binding.cuh` |
| `flashinfer/jit/blackwell_bgmv_moe.py` |
`flashinfer/jit/cake_bgmv_moe.py` |
| `tests/moe/test_blackwell_bgmv_moe.py`,
`tests/jit/test_blackwell_bgmv_moe_jit.py` |
`tests/moe/test_cake_bgmv_moe.py`, `tests/jit/test_cake_bgmv_moe_jit.py`
|
| `benchmarks/bench_blackwell_bgmv_moe.py` |
`benchmarks/bench_cake_bgmv_moe.py` |
| `BGMVMoEBlackwellPlan` | `BGMVMoECakePlan` (`BGMVMoEBlackwellPlan`
kept as an alias) |
| `prepare_bgmv_moe(..., backend="blackwell")` | `backend="cake"`
(default; `"blackwell"` accepted as a compatible alias) |

Kernel symbols and the generated bodies are unchanged apart from the
header comment, so SM100 numerics and behaviour are identical to #4821
(bitwise-reproducible replays, one owner per output token, no output
atomics).

## Baselines and their source PRs

The performance tables compare the prepared pipeline against the
portable `bgmv_moe_shrink` + `bgmv_moe_expand` path at two revisions, on
the same GPU, interleaved, CUPTI cold-L2, boundary = zero `shrink_out` +
zero `y_accum` + shrink + expand:

| arm | revision | source PRs | files |
|---|---|---|---|
| `portable_pre` | `60f0bc0f960f` (parent of #3535) | #3249 (merged
2026-05-29, `17763e2088`) original kernels; #3746 E2E wiring |
`csrc/bgmv_moe/`, `flashinfer/fused_moe/bgmv_moe.py` |
| `portable_post` (**baseline**) | `main` @ `2b8f80cd4eec` (2026-09-30)
| #3535 (merged 2026-09-29, `7d4d764fe2`) direct decode shrink kernel;
#3542 (merged 2026-09-29, `c3f7334d43`) coalesced 128-bit expand kernel
| same |
| `cake` | this branch | #4821 (merged 2026-08-30, `231f70828d`) + this
PR | `csrc/cake_bgmv_moe/`, `flashinfer/jit/cake_bgmv_moe.py` |

Merge-base of this branch with `main`: `2b8f80cd4eec`. `git log
2b8f80cd4eec..origin/main -- csrc/bgmv_moe
flashinfer/fused_moe/bgmv_moe.py flashinfer/jit/bgmv_moe.py` is empty at
publication time (no later upstream change touched the baseline path).

## Performance

Measurement: one process per arm, arms interleaved on the same GPU (uuid
recorded per set), `flashinfer.testing.bench_gpu_time_with_cupti` with
`cold_l2_cache=True`, CUPTI-fallback warnings treated as errors, median
of two interleaved rounds. Every row of every arm is checked against a
pair-loop torch reference at atol=rtol=1e-2 and replayed three times for
bitwise stability. With top-k = 2 the portable atomic expand is also
bitwise stable (two fp32 addends onto zero commute exactly); the
deterministic-ownership advantage of this backend appears only at top-k
≥ 3.

Where this backend is slower: with **expert-sorted pair order** (S4, not
the layout `bgmv_moe_gemm1/2_lora_delta` produce — those build pairs as
`arange(T).repeat_interleave(top_k)`), the current general routing path
scans all pairs per CTA and is far slower than the portable path at ≥
1024 tokens (numbers below). A token→pair index prologue for that path
is a follow-up; the fast path covers the layout used by FlashInfer's E2E
LoRA integration, its tests and both benchmarks.

### H100 (sm_90) — NVIDIA H100 80GB HBM3 (CC (9, 0), 132 SMs)

Serving shapes (S1, BF16, rank 32, 128 experts, top-k 2, 8 LoRAs). Times
are CUPTI cold-L2 medians (µs) of the full zero + shrink + expand
boundary; `pre` = portable path before #3535/#3542, `post` = portable
path on `main` (baseline), `cake` = this PR.

| hidden | tokens | pre µs | post µs | cake µs | post vs pre | cake vs
post | cake bitwise ×3 | post bitwise ×3 |
|---:|---:|---:|---:|---:|---:|---:|---|---|
| 2688 | 1 | 41.18 | 24.16 | 16.77 | 1.70× | **1.44×** | True | True |
| 2688 | 4 | 58.46 | 24.96 | 19.65 | 2.34× | **1.27×** | True | True |
| 2688 | 8 | 59.87 | 25.98 | 20.86 | 2.30× | **1.25×** | True | True |
| 2688 | 32 | 38.59 | 37.70 | 18.05 | 1.02× | **2.09×** | True | True |
| 2688 | 256 | 110.37 | 90.94 | 67.10 | 1.21× | **1.36×** | True | True
|
| 2688 | 512 | 183.78 | 139.61 | 101.15 | 1.32× | **1.38×** | True |
True |
| 2688 | 1024 | 335.15 | 234.65 | 167.33 | 1.43× | **1.40×** | True |
True |
| 3072 | 1 | 31.93 | 22.91 | 16.64 | 1.39× | **1.38×** | True | True |
| 3072 | 4 | 42.21 | 24.06 | 19.55 | 1.75× | **1.23×** | True | True |
| 3072 | 8 | 43.87 | 25.15 | 20.80 | 1.74× | **1.21×** | True | True |
| 3072 | 32 | 35.58 | 34.56 | 19.10 | 1.03× | **1.81×** | True | True |
| 3072 | 256 | 113.54 | 90.18 | 72.48 | 1.26× | **1.24×** | True | True
|
| 3072 | 512 | 185.25 | 133.92 | 113.47 | 1.38× | **1.18×** | True |
True |
| 3072 | 1024 | 333.02 | 217.50 | 186.94 | 1.53× | **1.16×** | True |
True |

S1 cake vs post: geomean **1.366×**, min 1.163×, max 2.089×, n=14; every
row passes atol=rtol=1e-2 against the pair-loop reference.

- **S2** #3535 shapes (shrink decode claim): 5 rows; post vs pre geomean
1.75× (min 1.25×, max 2.60×); cake vs post geomean 1.22× (min 1.22×, max
1.22×, n=1; cake covers hidden 2688/3072 × rank 32 only)
- **S3** #3542 sweep (rank × hidden × tokens, BF16): 84 rows; post vs
pre geomean 1.60× (min 1.15×, max 2.62×); cake vs post geomean 1.32×
(min 1.19×, max 1.52×, n=6; cake covers hidden 2688/3072 × rank 32 only)
- **S4** expert-sorted pair order (arbitrary routing): 4 rows; post vs
pre geomean 1.46× (min 1.06×, max 1.83×); cake vs post geomean 0.11×
(min 0.01×, max 1.59×, n=4; cake covers hidden 2688/3072 × rank 32 only)
cake's general routing path scans all pairs per CTA when pairs are not
contiguous per token; per-row:
  - hidden 2688, tokens 1024: post 226.5 µs, cake 2421.2 µs (0.094×)
  - hidden 3072, tokens 32: post 33.6 µs, cake 21.2 µs (1.589×)
  - hidden 3072, tokens 1024: post 199.6 µs, cake 2662.4 µs (0.075×)
  - hidden 3072, tokens 4096: post 651.7 µs, cake 52728.7 µs (0.012×)

### B200 (sm_100) — NVIDIA B200 (CC (10, 0), 148 SMs)

Serving shapes (S1, BF16, rank 32, 128 experts, top-k 2, 8 LoRAs). Times
are CUPTI cold-L2 medians (µs) of the full zero + shrink + expand
boundary; `pre` = portable path before #3535/#3542, `post` = portable
path on `main` (baseline), `cake` = this PR.

| hidden | tokens | pre µs | post µs | cake µs | post vs pre | cake vs
post | cake bitwise ×3 | post bitwise ×3 |
|---:|---:|---:|---:|---:|---:|---:|---|---|
| 2688 | 1 | 40.61 | 22.53 | 16.80 | 1.80× | **1.34×** | True | True |
| 2688 | 4 | 58.66 | 23.62 | 19.52 | 2.48× | **1.21×** | True | True |
| 2688 | 8 | 56.74 | 24.77 | 19.81 | 2.29× | **1.25×** | True | True |
| 2688 | 32 | 36.10 | 32.51 | 13.15 | 1.11× | **2.47×** | True | True |
| 2688 | 256 | 98.08 | 72.42 | 42.08 | 1.35× | **1.72×** | True | True |
| 2688 | 512 | 165.06 | 110.34 | 66.66 | 1.50× | **1.66×** | True | True
|
| 2688 | 1024 | 306.14 | 189.28 | 115.74 | 1.62× | **1.64×** | True |
True |
| 3072 | 1 | 31.23 | 21.66 | 16.38 | 1.44× | **1.32×** | True | True |
| 3072 | 4 | 41.66 | 22.78 | 19.01 | 1.83× | **1.20×** | True | True |
| 3072 | 8 | 40.99 | 23.87 | 19.46 | 1.72× | **1.23×** | True | True |
| 3072 | 32 | 32.29 | 28.58 | 13.44 | 1.13× | **2.13×** | True | True |
| 3072 | 256 | 94.11 | 63.36 | 45.79 | 1.49× | **1.38×** | True | True |
| 3072 | 512 | 159.87 | 93.70 | 70.53 | 1.71× | **1.33×** | True | True
|
| 3072 | 1024 | 293.41 | 158.11 | 124.45 | 1.86× | **1.27×** | True |
True |

S1 cake vs post: geomean **1.473×**, min 1.199×, max 2.472×, n=14; every
row passes atol=rtol=1e-2 against the pair-loop reference.

- **S2** #3535 shapes (shrink decode claim): 5 rows; post vs pre geomean
1.80× (min 1.39×, max 2.45×); cake vs post geomean 1.22× (min 1.22×, max
1.22×, n=1; cake covers hidden 2688/3072 × rank 32 only)
- **S3** #3542 sweep (rank × hidden × tokens, BF16): 84 rows; post vs
pre geomean 1.76× (min 1.16×, max 2.65×); cake vs post geomean 1.40×
(min 1.17×, max 1.67×, n=6; cake covers hidden 2688/3072 × rank 32 only)
- **S4** expert-sorted pair order (arbitrary routing): 4 rows; post vs
pre geomean 1.62× (min 1.15×, max 2.01×); cake vs post geomean 0.10×
(min 0.01×, max 1.63×, n=4; cake covers hidden 2688/3072 × rank 32 only)
cake's general routing path scans all pairs per CTA when pairs are not
contiguous per token; per-row:
  - hidden 2688, tokens 1024: post 187.1 µs, cake 2197.6 µs (0.085×)
  - hidden 3072, tokens 32: post 28.1 µs, cake 17.2 µs (1.627×)
  - hidden 3072, tokens 1024: post 156.4 µs, cake 2417.5 µs (0.065×)
  - hidden 3072, tokens 4096: post 545.0 µs, cake 48751.5 µs (0.011×)

### GB300 (sm_103) — NVIDIA GB300 (CC (10, 3), 152 SMs)

Serving shapes (S1, BF16, rank 32, 128 experts, top-k 2, 8 LoRAs). Times
are CUPTI cold-L2 medians (µs) of the full zero + shrink + expand
boundary; `pre` = portable path before #3535/#3542, `post` = portable
path on `main` (baseline), `cake` = this PR.

| hidden | tokens | pre µs | post µs | cake µs | post vs pre | cake vs
post | cake bitwise ×3 | post bitwise ×3 |
|---:|---:|---:|---:|---:|---:|---:|---|---|
| 2688 | 1 | 40.99 | 26.91 | 16.19 | 1.52× | **1.66×** | True | True |
| 2688 | 4 | 58.24 | 27.68 | 18.21 | 2.10× | **1.52×** | True | True |
| 2688 | 8 | 57.70 | 29.06 | 19.04 | 1.99× | **1.53×** | True | True |
| 2688 | 32 | 36.83 | 33.98 | 12.67 | 1.08× | **2.68×** | True | True |
| 2688 | 256 | 94.30 | 71.78 | 41.02 | 1.31× | **1.75×** | True | True |
| 2688 | 512 | 155.71 | 106.88 | 63.01 | 1.46× | **1.70×** | True | True
|
| 2688 | 1024 | 285.22 | 178.82 | 107.65 | 1.60× | **1.66×** | True |
True |
| 3072 | 1 | 33.95 | 26.99 | 15.94 | 1.26× | **1.69×** | True | True |
| 3072 | 4 | 42.62 | 25.79 | 17.76 | 1.65× | **1.45×** | True | True |
| 3072 | 8 | 43.46 | 26.34 | 18.34 | 1.65× | **1.44×** | True | True |
| 3072 | 32 | 34.18 | 30.56 | 12.77 | 1.12× | **2.39×** | True | True |
| 3072 | 256 | 91.33 | 63.90 | 43.07 | 1.43× | **1.48×** | True | True |
| 3072 | 512 | 151.81 | 90.40 | 67.04 | 1.68× | **1.35×** | True | True
|
| 3072 | 1024 | 274.43 | 149.57 | 115.94 | 1.83× | **1.29×** | True |
True |

S1 cake vs post: geomean **1.650×**, min 1.290×, max 2.682×, n=14; every
row passes atol=rtol=1e-2 against the pair-loop reference.

- **S2** #3535 shapes (shrink decode claim): 5 rows; post vs pre geomean
1.53× (min 1.16×, max 2.15×); cake vs post geomean 1.59× (min 1.59×, max
1.59×, n=1; cake covers hidden 2688/3072 × rank 32 only)
- **S3** #3542 sweep (rank × hidden × tokens, BF16): 84 rows; post vs
pre geomean 1.72× (min 1.17×, max 2.64×); cake vs post geomean 1.47×
(min 1.18×, max 1.69×, n=6; cake covers hidden 2688/3072 × rank 32 only)
- **S4** expert-sorted pair order (arbitrary routing): 4 rows; post vs
pre geomean 1.60× (min 1.12×, max 2.00×); cake vs post geomean 0.10×
(min 0.01×, max 1.84×, n=4; cake covers hidden 2688/3072 × rank 32 only)
cake's general routing path scans all pairs per CTA when pairs are not
contiguous per token; per-row:
  - hidden 2688, tokens 1024: post 176.0 µs, cake 2029.4 µs (0.087×)
  - hidden 3072, tokens 32: post 30.4 µs, cake 16.6 µs (1.836×)
  - hidden 3072, tokens 1024: post 149.0 µs, cake 2240.1 µs (0.067×)
  - hidden 3072, tokens 4096: post 509.6 µs, cake 45070.4 µs (0.011×)



## Tests

Validated at `0275ac2e7` on H100 (tests, benchmark, pre-commit). B200
and GB300 were validated at `a7200d15`, which differs from `0275ac2e7`
only by the `select_cake_bgmv_moe_schedule` docstring (`git diff
a7200d15 0275ac2e7`: one file, 6+/2- comment lines). The A/B `cake` arm
below ran from `56e7709e` (GB300), `56e7709e`/`249c538` (B200) and
`a7200d15` (H100); over `56e7709e..HEAD` the sources under
`csrc/cake_bgmv_moe/` differ only in header comments and clang-format
line breaks (identical after stripping comments and whitespace), so
every measured kernel is the head's kernel.

- H100 (CC 9.0, cw-dfw): `tests/jit/test_cake_bgmv_moe_jit.py` 64 passed
(CPU), `tests/moe/test_cake_bgmv_moe.py` 31 passed (GPU, incl. bitwise
replay ×7, outer CUDA-Graph capture, non-default stream, arbitrary route
order, `-1` LoRA skip, invalid-pair padding)
- B200 (CC 10.0, NSC): `tests/jit/test_cake_bgmv_moe_jit.py` 64 passed
(CPU), `tests/moe/test_cake_bgmv_moe.py` 31 passed (GPU, incl. bitwise
replay ×7, outer CUDA-Graph capture, non-default stream, arbitrary route
order, `-1` LoRA skip, invalid-pair padding)
- GB300 (CC 10.3, OCI): `tests/jit/test_cake_bgmv_moe_jit.py` 64 passed
(CPU), `tests/moe/test_cake_bgmv_moe.py` 31 passed (GPU, incl. bitwise
replay ×7, outer CUDA-Graph capture, non-default stream, arbitrary route
order, `-1` LoRA skip, invalid-pair padding)
- `benchmarks/bench_cake_bgmv_moe.py --repeat-time-ms 500` on H100
(NVIDIA H100 80GB HBM3): geomean **1.377×** vs the portable path on
`main`, min 1.156×, max 2.046× over 14 shapes
- `benchmarks/bench_cake_bgmv_moe.py --repeat-time-ms 500` on B200
(NVIDIA B200): geomean **1.446×** vs the portable path on `main`, min
1.184×, max 2.385× over 14 shapes
- `benchmarks/bench_cake_bgmv_moe.py --repeat-time-ms 500` on GB300
(NVIDIA GB300): geomean **1.656×** vs the portable path on `main`, min
1.302×, max 2.715× over 14 shapes
- pre-commit on the changed files (clang-format, mypy, ruff): all hooks
passed
- Existing `tests/moe/test_bgmv_moe.py` (portable path) is untouched by
this PR.

## Reviewer notes

- `csrc/cake_bgmv_moe/*.cu` are the #4821 bodies moved with `git mv`
(rename-only diff plus one header comment line).
- The per-target module split keeps a mismatched cubin from ever
running: an `sm103a` module on a 10.0 or 9.0 device (or any other
mismatch) raises at `configure()`.
- No H200 route was available for this round; the H100 numbers below are
compared against the H200 numbers quoted in #3535/#3542 only
qualitatively (same SM count and SM90 ISA, higher HBM bandwidth on
H200).
- `BGMVMoEBlackwellPlan` and `backend="blackwell"` remain
importable/accepted so existing callers of #4821 keep working; the
Literal widening is a compatible public-API change.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [849f423](https://github.com/flashinfer-ai/flashinfer/commit/849f42360c1691b27e4ae2c9fe4a392bdb778f17)

- **作者**: FlashInfer Bot
- **时间**: 2026-09-30T19:28:38Z
- **提交信息**: Update Docker CI tags to 20260930-b1420f1 (#4673)

This PR updates the Docker CI image tags to the latest version:
`20260930-b1420f1`

The image list is generated from `ci/cuda-versions.json`.

Auto-generated by [release-ci-docker
workflow](https://github.com/flashinfer-ai/flashinfer/actions/runs/36655164686)

Co-authored-by: Anerudhan <916946+Anerudhan@users.noreply.github.com>

### [4ccd86d](https://github.com/flashinfer-ai/flashinfer/commit/4ccd86d935a548374ec3da2367e43017aa19ab67)

- **作者**: yufeiwu-nv
- **时间**: 2026-09-30T18:23:08Z
- **提交信息**: fix: log expected SM107 GEMM candidate rejections at debug level (#5689)

<!-- .github/pull_request_template.md -->

## 📌 Description

SM107 dense and masked grouped GEMM candidate checks print `[DSL ERROR]
CantImplementError` for every unsupported autotuning candidate, even
though they catch the exception and return `False`. Large candidate
sweeps therefore flood stdout with expected rejections.

Use a module logger at DEBUG level in both checks. Candidate eligibility
and exception propagation stay the same; rejection reasons remain
available when debug logging is enabled.

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

## 🧪 Tests

- Repository pre-commit hooks on both changed files passed, including
mypy and Ruff.
- Temporary CPU checks executed the actual candidate-check method bodies
with dependency stubs: accepted candidates still return `True`; 10,000
rejected candidates per method return `False` without
stdout/default-level logs; DEBUG retains the reason; unrelated
`RuntimeError` exceptions propagate.
- `git diff --check` passed. No GPU execution was performed; this
changes host-side logging only.


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

The module loggers follow the existing GEMM logging convention. Enable
Python DEBUG logging for
`flashinfer.gemm.kernels.dense_blockscaled_gemm_sm107` or
`flashinfer.gemm.kernels.grouped_gemm_masked_rubin` to inspect rejection
reasons. No kernel computation or candidate-validity condition is
changed.

Validation scripts were kept outside the repository; no test files were
added. Pre-commit was run on the changed files, not the entire
repository.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **Improvements**
- Unsupported computation options in dense and grouped GEMM operations
no longer print error messages to the console when skipped. Details are
recorded at debug level instead, and unsupported options continue to be
rejected. This keeps routine console output quieter without changing
which computation options are supported or how supported operations
behave.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [104283d](https://github.com/flashinfer-ai/flashinfer/commit/104283d1a23c4eb7da20b038ee2a497afc86b06a)

- **作者**: Mingyang Wang
- **时间**: 2026-09-30T17:40:21Z
- **提交信息**: feat(mla): fall back to FA2 for unsupported SM90 auto requests (#5712)

<!-- .github/pull_request_template.md -->

## 📌 Description

Allow SM90 automatic MLA planning to try FA2 when FA3 rejects a request
as unsupported. For example, a request with `head_dim_ckv=384` now
reaches the existing FA2 backend instead of failing at FA3 preflight.

Keep FA3 first on supported Hopper toolchains, preserve the selected
backend during CUDA graph replanning, and propagate invalid-input,
compiler and runtime errors. Architecture dispatch now lives in
`_auto_policy.py`, with explicit SM80/SM90 ordering and the existing
SM100 policy.

## 🔍 Related Issues

Follow-up to #5463.

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

Scoped changed-file pre-commit checks passed, including mypy and Ruff.
The full-repository `--all-files` command was not run.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

Targeted validation on the current patch:

- `test_mla_auto_backend.py -k "cpu or sm90"`: 85 passed, including
native H100 eager/graph fallback and replay checks.
- SM100 policy, metadata and volume regression subset: 140 passed.
- `test_mla_auto_backend_warning.py`: 5 passed.
- L40S: eight numerical auto/FA2 probes across FP16/BF16 and eager/graph
execution passed.

Native B100 tests were not rerun on this revision because hardware was
occupied; the full test suite was not run.

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

This change improves supported-request fallback; it makes no speedup
claim. The earlier H100 campaign found no confirmed regressions but
retained 59 inconclusive comparisons. Existing FA3 CKV256 numerical
failures remain a separate issue. Benchmark tooling is maintained
separately and is not included in this PR.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **Improvements**
- Automatic MLA planning selects backend candidates by device
architecture: supported SM90a devices try FA3 before FA2; SM80 and other
architectures use FA2; SM100 retains workload-ranked selection.
- On eager SM90 replans, a typed FA3 rejection can fall back to FA2.
CUDA-graph replans retain the previously prepared backend.
  - Blackwell fallback warnings report FA2.
- **Breaking Changes**
  - Removed the public utility for selecting an MLA backend directly.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [9e9ec38](https://github.com/flashinfer-ai/flashinfer/commit/9e9ec38922a25a30a331b0abdedf7af8fc559a5a)

- **作者**: Jonathan Dierksen
- **时间**: 2026-09-30T16:27:48Z
- **提交信息**: ci: stage benchmarks for nightly package tests (#5698)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

Nightly package tests run from an isolated temporary directory to
exercise the installed FlashInfer distribution. That directory copied
`tests/` and `pytest.ini`, but omitted benchmark scripts loaded by tests
through sibling paths. `tests/moe_ep/test_sm107_tuning.py` consequently
raised `FileNotFoundError` for `bench_moe_ep_sm107_block_scaled_mega.py`
in the [September 29 cu129 and cu130 shard-1
jobs](https://github.com/flashinfer-ai/flashinfer/actions/runs/36526449378).

Copy `benchmarks/` into the isolated test directory. The directory still
excludes the source `flashinfer/` package, preserving the
installed-package test contract.

## 🔍 Related Issues

<!-- Link any related issues here -->

- [IKL-524](https://nvidia.atlassian.net/browse/IKL-524)

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [ ] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

Ran `pre-commit run --files scripts/task_test_nightly_build.sh`; all
applicable hooks passed.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [ ] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

Validated `bash -n scripts/task_test_nightly_build.sh`, `git diff
--check`, and a local staging copy that places benchmark fixtures beside
`tests/` without copying source `flashinfer/`. Package tests were not
run locally because this environment lacks `pytest`; the affected GPU
nightly lane remains to be run.

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

The same nightly jobs also fail `test_sm107_qualification.py` because
its subprocess tests inherit `PYTEST_ADDOPTS=--full`. That failure is
independent of the missing benchmark and remains outside this focused
change.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Tests**
* Nightly package tests now include benchmark fixtures in the isolated
test run.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [1c84d0e](https://github.com/flashinfer-ai/flashinfer/commit/1c84d0eae49bd956f8fcc51d741acc18179a21e2)

- **作者**: Yuhang He
- **时间**: 2026-09-30T16:04:21Z
- **提交信息**: feat(prims-ts): 8-bit Q/K/V sage attention for the PrimTS block sparse decode kernels (#5123)

<!-- .github/pull_request_template.md -->

## 📌 Description

Adds Sage attention (8-bit Q/K/V with per-block dequantization scales in
the TensorRT-LLM `sageQuant` layout) to the PrimTS `fmha_decode` kernels
for contiguous K/V, in dense mode and in block-sparse mode with exact
and proxy routes. The contiguous block-sparse wrapper also gains a dense
mode.

### New features

- **Sage attention** through `BlockSparseTSWrapper` and
`block_sparse_attention`:
- FP8 E4M3 or INT8 Q/K (INT8 on SM100 only), E4M3 V, BF16 or FP16
output.
- `SageAttentionConfig` fixes the recipe at plan time: `q_block_size`,
`k_block_size` (1, 4, 16, 32, 64, 128, 256), `k_summary_block_size` for
proxy summaries, and `v_mean`.
- `SageAttentionParams` carries each run's scale tensors: `q_scale`,
`k_scale`, `v_scale`, optional `v_mean`, and `k_summary_scale` for proxy
plans.
- Q64/KV256 and Q128/KV128 profiles, static and persistent scheduling,
causal masks, token masks, BSR and bitmask routes, proxy routes.
- **Dense mode** for contiguous K/V: `plan(use_block_sparse=False)` and
`block_sparse_attention(use_block_sparse=False)` run dense attention
over the whole sequence, for 16-bit and Sage recipes, with matching
trace templates.

### Changes by area

- **API** (`block_sparse.py`, `sage.py`, `_block_sparse/`): new
`plan`/`run` arguments, scale-tensor validation, and one contiguous
adapter whose routing and scale slots are optional. `plan` takes
`k_data_type`/`v_data_type` with `kv_data_type` as the alias for both,
as in `BatchDecodeTSWrapper.plan`.
- **Kernel** (`kernels/fmha_decode/`): scales enter the softmax before
the row max and the exponential; P is E4M3 with the static 448 scale; V
scales apply per channel in the epilogue. The K and V scales are
task-scheduling resources (`SageKScalesResource`,
`SageVScalesResource`). INT8 scores accumulate onto an FP32 bias, so the
softmax reads them without conversion. Byte-wide KV256 tiles use a
four-stage K/V ring and split the output tail between lane groups.
Softmax and correction improvements that do not depend on the element
width apply to the 16-bit kernels too.
- **Config** (`fmha_decode_config.py`): the Sage recipe rules next to
the mixed-precision rules of #4414, a check of every schedule's complete
SMEM layout against the SM100-family per-CTA capacity, and INT8 Q/K
limited to SM100.
- **Docs**: a Sage section in the PrimTS README.
- **Tests**: `tests/attention/test_attention_ts_sage.py` (an end-to-end
reference matrix plus rejection tests) and dense-mode tests in
`test_attention_ts_block_sparse.py`.

### Behavior change

Block-sparse proxy routes take `v_summary` as the per-block **mean** of
V, not the sum, for 16-bit plans as well. The block's token mass enters
the softmax logit. Producers of `v_summary` (the TensorRT-LLM SOL
predictor) must emit means.

### Limitations

- `head_dim=128` and contiguous K/V; the paged block-sparse APIs do not
support Sage.
- No split-KV, sliding window or attention sinks with Sage.
- Scales are assumed finite and positive; the kernel does not check
them.

### Performance

B200, D=128, CUDA Graph replay minimum of the kernel, paired A/B over
three interleaved legs, same plan and launch heuristic on both sides.
Random 8-bit inputs and scales; default recipe `(q, k, v) = (1, 16,
per-channel)`.

**Sage vs BF16** (time ratio, lower is faster)

| Case | BF16 | FP8 Sage | ratio | INT8 Sage | ratio |
| --- | ---: | ---: | ---: | ---: | ---: |
| Dense S=10800 H=40 | 2072 us | 1832 us | 0.88 | 1864 us | 0.89 |
| Dense S=4096 H=8 | 66.8 us | 68.7 us | 1.03 | 69.0 us | 1.04 |
| Block-sparse exact S=4096 H=8, density 0.25 | 38.1 us | 35.9 us | 0.95
| 36.1 us | 0.95 |
| Block-sparse exact S=4096 H=8 Hkv=4 (Q128/KV128), density 0.25 | 38.2
us | 40.1 us | 1.05 | | |
| Block-sparse exact S=15360 H=40, density 0.125 | 688 us | 554 us |
0.81 | 565 us | 0.82 |
| Block-sparse exact S=75600 H=40, density 0.10 | 11263 us | 8874 us |
0.79 | 8602 us | 0.76 |
| Block-sparse exact S=10800 H=40, density 0.175 | 470 us | 386 us |
0.82 | 394 us | 0.84 |
| Block-sparse proxy S=10800 H=40, density 0.175 | 544 us | 467 us |
0.86 | 475 us | 0.87 |

**Small K blocks** (time relative to `k_block_size=16` of the same
recipe)

| Case | `k_block_size=4` | `k_block_size=1` |
| --- | ---: | ---: |
| FP8 block-sparse exact S=10800 H=40 | 1.07 | 1.18 |
| FP8 block-sparse proxy S=10800 H=40 | 1.05 | 1.16 |
| INT8 block-sparse exact S=10800 H=40 | 1.10 | 1.26 |
| INT8 block-sparse proxy S=10800 H=40 | 1.11 | 1.28 |
| FP8 dense S=10800 H=40 | 1.06 | 1.2 |
| FP8 block-sparse exact Q128/KV128 S=4096 | | 1.09 |

**16-bit kernels vs `main`** (BF16, same plan)

| Case | ratio |
| --- | ---: |
| Block-sparse exact S=10800 H=40, density 0.175 | 0.94 |
| Block-sparse proxy S=10800 H=40, density 0.175 | 0.91 |
| Block-sparse exact S=4096 H=8, density 0.25 | 0.94 |
| Block-sparse exact S=4096 H=8 Hkv=4 (Q128/KV128) | 0.99 |
| Block-sparse exact S=15360 H=40, density 0.125 | 0.94 |

## 🔍 Related Issues

Follows #5002 (PrimTS block-sparse attention optimizations). Follow-ups
outside this PR: the TensorRT-LLM SOL predictor must emit V means; trace
capture of the Sage scale tensors.

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

On B200 at the tip of this branch:

- `tests/attention/test_attention_ts_sage.py`: 28 passed
- `tests/attention/test_attention_ts_block_sparse.py`: 235 passed, 1
skipped
- `tests/attention/test_attention_ts_decode.py`: 665 passed
- `tests/trace/test_fi_trace_template_consistency.py`: 821 passed, 1
skipped

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

- The `v_summary` mean contract is the one result change for existing
callers; please weigh in if a sum-compatible mode is wanted instead.
- The 16-bit kernels are not byte-identical to `main`, because the
shared softmax and correction changes apply to them; the last table
gives their effect.
- The branch builds on #4414: the Sage recipes use its
`qk_dtype`/`pv_dtype` names, and `_dtype_bytes` counts INT8 and packed
NVFP4 as one byte. FP8-Q profiles stream P under the same rule as the
16-bit ones, and the shared softmax path also reaches the FP8 and
mixed-precision paged decode kernels. Paired B200 A/B against `main` on
paged decode (B=4, KV=8192, D=128, page 64, one query token): FP8
Hq=128/Hkv=1 (Q128/KV128, streamed P) 0.99; with Hq=32/Hkv=4, FP8 1.00,
BF16 1.00, BF16 Q + FP8 K/V 1.00, BF16 Q + NVFP4 K/V 1.01, FP8 Q + NVFP4
K/V 1.00.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added dense contiguous attention to the block-sparse planning and
execution APIs, including trace support.
* Added Sage attention with configurable quantization scales and
optional V means for dense and block-sparse workloads.
* Added support for separate V dtypes and INT8 Q/K in Sage attention on
supported hardware.
  * Exported Sage configuration and runtime parameter types.
* **Bug Fixes**
* Proxy-route V summaries now use block means, with represented block
mass applied consistently.
* Improved validation for unsupported dense-plan inputs, dtype
combinations, device support, and shared-memory limits.
* **Documentation**
* Updated attention guides to describe dense execution, Sage APIs, and
proxy-summary requirements.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [2dce1db](https://github.com/flashinfer-ai/flashinfer/commit/2dce1db15d3104ad155f6e64874deaecda15d8fe)

- **作者**: Sam Mausberg
- **时间**: 2026-09-30T14:48:26Z
- **提交信息**: fix(moe): skip unrouted (-1) expert ids in the SM12x b12x fused MoE (#5451)

<!-- .github/pull_request_template.md -->

## Description

vLLM writes -1 into the CUDA-graph padding rows of `topk_ids`
(`VLLM_MOE_SKIP_PADDING`). The b12x kernels indexed their per-expert
routing state with that id: the dynamic kernels' histogram,
`expert_write_rows` and `expert_tile_base` lookups, the static kernel's
virtual-expert allocator, and the micro kernels' weight reads. On SM120
that is an illegal memory access, or silent corruption when the write
lands in mapped memory. This is the crash in #5446; jschmied traced it
to the histogram in #3170.

A negative id now marks an unrouted pair: it takes no packed row and no
compact expert, its scale lookup is skipped, and the finalizers ignore
its slot, so a token whose slots are all negative produces an exact-zero
row. In detail:

- The Triton compaction pre-pass gives unrouted pairs compact id -1 and
leaves them out of `active_expert_count`.
- The static kernel's routing loop and finalizer, and both dynamic
kernels' histogram, producers and packing stores, skip negative ids. The
gated kernel keeps its shared-quant fast path by giving unrouted slots
the first routed slot's scale; their stores are skipped on `phys_row`.
- The single-token MMA micro and the direct-micro kernels keep their
dense pair-to-expert layout and instead read expert 0 with a zero
routing weight.
- The W4A16 top-k sum takes `topk_ids` and skips the FC2 rows the route
packer already dropped, instead of zeroing the whole buffer.

The docstrings of `b12x_fused_moe` and `B12xMoEWrapper.run` state the
contract. Ids >= `num_experts` are still caller errors.

## Related Issues

Fixes #5446. Root cause analysis by jschmied in #3170.

## Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

RTX 5070 Ti (SM120, 70 SMs), CUDA 13.2, torch 2.14.0+cu130,
nvidia-cutlass-dsl 4.8.0. CI has not run.

New `TestUnroutedPairs` (35 cases) in
`tests/moe/test_b12x_fused_moe.py`: the compaction pre-pass; tail, all
and mixed masking through forced `direct_micro`, `micro`, `static` and
`dynamic` backends, with the dynamic path covered on both the gated
kernel (N=512) and the generic kernel (silu at N=640, relu2);
single-token micro for silu, relu2 and relu2 with a shared input scale;
MXFP4 at 64 and 512 tokens; W4A16 at 4 and 64 tokens; `B12xMoEWrapper`
under CUDA-graph replay at 4, 64 and 512 tokens. Each case runs an
unmasked call first so the cached workspace is dirty, then asserts exact
zeros for fully unrouted tokens and reference accuracy for the rest. On
unpatched main the class hits an illegal memory access.

| run | result |
| --- | --- |
| `tests/moe/test_b12x_fused_moe.py -k TestUnroutedPairs` | 35 passed |
| `tests/moe/test_b12x_fused_moe.py -k "not 1024-2048"` (largest shapes
deselected for VRAM) | 226 passed, 1 skipped |
| `test_b12x_moe_kernel_cache.py`, `test_b12x_w4a16_route_pack.py`,
`test_unified_moe_b12x.py` | 192 passed |

The report's shape (E=512, K=2560, N=640, top_k=10, NVFP4) with the last
quarter of the tokens padded and with every slot padded: on main, 8
tokens (micro) returns denormal garbage (2.8e-39) in the padded rows and
64 tokens (static) raises an illegal memory access; with this PR, 8, 64,
128, 512 and 4096 tokens finish with exact zeros in the padded rows.
Valid routing at those sizes ran clean on both.

Valid-id wall time at that shape, CUDA events, warm cache, minimum of 40
iterations, three alternating rounds (us):

| tokens | path | main | this PR |
| ---: | --- | --- | --- |
| 64 | static | 1506 / 2967 / 1566 | 1528 / 1521 / 1510 |
| 4096 | dynamic | 3705 / 3896 / 3908 | 3931 / 3918 / 3917 |

The spread between rounds is the shared WSL2 GPU, not the change.

## Experimental Track

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

Most of the diff is re-indentation from wrapping existing loop bodies in
`if expert_id >= 0`; `git diff -w` shows about 90 changed lines in
`gated.py` and 40 in `generic.py`. The two places worth a close look are
the `route_gs` handling in `gated.py` and the single-token micro /
direct-micro substitution (expert 0 with weight 0.0 rather than a tile
skip, which would need matching producer and consumer pipeline changes;
it only applies at m <= 8).

Developed with Claude Fable 5.1.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Corrected Mixture-of-Experts processing for unrouted slots marked with
negative expert IDs in b12x.
* Unrouted slots no longer affect routing, packing, quantization, or
output accumulation.
  * Tokens with no routed experts now produce zero-valued output rows.
* Improved handling across dynamic, static, quantized, and CUDA-graph
execution paths.

* **Tests**
* Added coverage for fully unrouted and partially routed tokens across
supported b12x configurations.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Alex Yang <aleyang@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [b161fd6](https://github.com/flashinfer-ai/flashinfer/commit/b161fd6b5910ca1414fe37104b2d079de6a10780)

- **作者**: x41lakazam
- **时间**: 2026-09-30T14:23:09Z
- **提交信息**: fix(moe): guard Humming MXFP4xFP8 runner behind ENABLE_FP4 (#5086)

### Description

`make_humming_runner` in
`csrc/fused_moe/cutlass_backend/flashinfer_cutlass_fused_moe_binding.cu`
references `kernels::Fp4Type` unconditionally. That type only exists in
FP4-enabled builds, so any
CUTLASS fused-MoE module compiled without `-DENABLE_FP4` fails to
compile.

`gen_cutlass_fused_moe_sm89_module` (`flashinfer/jit/fused_moe.py:133`)
sets only `-DENABLE_BF16`,
`-DENABLE_FP8`, `-DENABLE_FP8_BLOCK_SCALE` and
`-DUSING_OSS_CUTLASS_MOE_GEMM` — no `-DENABLE_FP4`.
So SM89 builds of this module are broken on `main` today.

The Humming path is SM90-only at every call site, so a non-FP4 build can
never legitimately reach
it. This guards the lambda body with `#ifdef ENABLE_FP4` and fails with
a clear runtime message
otherwise, so SM89 compiles again without changing behaviour on
FP4-enabled builds.

**Reproduction:** run anything that triggers the SM89 CUTLASS fused-MoE
module on an
sm89 device (e.g. an L4), such as
`tests/moe/test_trtllm_cutlass_fused_moe.py`; the JIT build fails
in `flashinfer_cutlass_fused_moe_binding.cu` on `kernels::Fp4Type`.

Found while building the SM89 module on an L4 host.

## 🔍 Related Issues

<!-- none -->

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

No new tests: this is a build-time fix with no behavioural change on
FP4-enabled builds. It is
verified by the SM89 module compiling again — on an L4, `tests/moe/`
cases that JIT
`fused_moe_89` build and run, where previously the build aborted.

## Notes for reviewers

The `#else` branch uses `TVM_FFI_ICHECK(false)` rather than `#error`, so
a non-FP4 build still
links; the failure only surfaces if something actually calls the Humming
path, which no SM89 call
site does.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Enabled SM90 Humming-style MXFP4×FP8 execution with FP16 or BF16
activations when activation and output data types match.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: Alex Yang <aleyang@nvidia.com>

### [fdb08a8](https://github.com/flashinfer-ai/flashinfer/commit/fdb08a897cb807111bceada956e961da18bfc1dd)

- **作者**: eigen
- **时间**: 2026-09-30T10:48:05Z
- **提交信息**: feat(cake_dsa): add native 64-query-head DSA sparse-attention kernels for SM100/SM103 (#5657) (#5704)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

<!-- Title: feat(cake_dsa): native 64-query-head DSA sparse-attention
training kernels (fwd + bwd) for SM100/SM103 -->

## Summary

Experimental API + Cake backend for the native 64-query-head DeepSeek
Sparse Attention training kernels
(top-k sparse MLA with absorbed queries) on SM100 (B200 / GB200;
acceptance architecture) and SM103
(GB300; same sources, measured with the same protocol). Addresses #5657
(GLM-5.2: 64 heads, 512 latent + 64 rope query/key
dimensions, 512 value dimensions, top-k 2048, BF16 inputs, FP32
accumulation).

- `flashinfer/dsa_sparse_attention.py`: `dsa_sparse_attention(q_latent,
q_rope, kv_latent, k_rope, indices,
topk_length=None, softmax_scale=None, return_lse=False,
key_passes=None)` (global key indices, `-1` / `>= S` invalid
anywhere in the row, any positive top-k) and
`dsa_sparse_attention_varlen(..., gather_kv_indices,
cu_seqlens_q, cu_seqlens_k, max_seqlen_q, max_seqlen_k, ...)`
(per-document indices offset on device).
Both are `@flashinfer_experimental_api`, differentiable
(`torch.autograd.Function` saving `out`,
`o_lo`, `lse`), and accept views of packed `[T, 64, 576]` / `[S, 576]`
tensors.
- `flashinfer/experimental/cake_dsa_train/`: generated programs (one
record per architecture: forward,
backward preprocess, backward main in its single-pass and key-range-pass
form with the per-pass key
compaction, cast), host backend (validation, workspace layout,
key-range-pass planning, argument-plan
binding, allocation-free CUDA-graph-capturable runner), autograd
wrapper. The eager entry points validate
and bind once per input binding (`(data_ptr, shape, stride, dtype)` of
every input plus the scale) and
launch later calls from the remembered argument plans with fresh outputs
(`cake_backend.BINDING_CACHE`;
no caller tensor pinned; `FLASHINFER_CAKE_DSA_TRAIN_BINDING_CACHE=0`
disables it). TMA descriptors of
the pointer-ABI programs live in a caller-owned workspace region
refreshed on the launch stream (no
  per-pointer host copies, no descriptor-slot limit, graph-capturable).
- `tests/experimental/test_cake_dsa_train.py`: host-layer tests and
device tests against a chunked FP64
reference (iid, masked rows, out-of-range and non-multiple-of-64 top-k,
varlen multi-document with q/kv
length mismatch, peaked attention, forward / dQ determinism, dKV
run-to-run spread, autograd parity,
natural-layout FP32 dK/dV in the `dkv_fp32` mode, binding-cache hit
paths, key-range passes: forced
three-pass small shape with masking and the whole-row policy case
through the public entry).
The forward output is held to 1.05x the numerics floor of a BF16-P
kernel emulated in FP64 on the same
inputs (`reference_fp64(...)["out_emu"]`), so the tolerance follows the
shape instead of a fixed constant.
- `benchmarks/bench_cake_dsa_train.py`: the 18 representative training
rows and the accuracy cases, with
the optional FlashMLA + cuDNN and FA sparse-MLA baselines, plus the
host-microseconds mode.

Kernel snapshot: the generated programs of this PR are exported from
Cake revision `5c2ab2357f6` (exporter adapter and frozen protocol lock
at `671ad221fb6`). The key-range-pass stages (`bwd_compact`,
`bwd_main_pass`) and the record's `key_pass_policy` are exported from
Cake revision `42071e0ef61` (the whole-row key-range-pass policy on the
same kernel programs; exporter adapter `a36c8a6da19`, re-frozen protocol
lock `d338f5a74ee`: 44 shapes, six templates); the forward, backward
preprocess, backward main and cast sources are byte-identical to the
first export.

## Kernels (one training step)

- **Forward**: one CTA per query token gathers its top-k keys once
through TMA gather, computes S, the
online softmax and O with tcgen05 MMAs in tensor memory, and writes
`out` (BF16), the natural-log `lse`
  (FP32) and the BF16 output residual `o_lo = bf16(fp32(O) - bf16(O))`.
- **Backward preprocess**: `delta = rowsum(dO * (O + O_lo))` in FP32,
one (token, head) row per warp
  (exact-delta method of the FA sparse-MLA backward).
- **Backward main**: one CTA per query token, 20 warps in gather /
compute / reduce / MMA / load / metadata
roles. Q, dO and the gathered K/V tiles stream through shared memory; S
and dP are recomputed from the
BF16 Q and K per 64-key tile, P and dS are formed in registers, dQ and
dQ_rope accumulate in tensor memory
over all tiles of the token (written once per row: bitwise
deterministic), and the per-token dK/dV and
dK_rope contributions are scattered with vectorized FP32
`red.global.add.v4` / `.v2` into an FP32
accumulator kept in an internal permuted layout that suits the
reduction's register tiling.
- **Backward main, key-range passes** (DRAM regime; see the section
below): when the FP32 dK/dV accumulators
outgrow the L2, the host runs the main stage in P passes over disjoint
key ranges -- per pass a compaction
kernel (one warp per token) lists the row's keys inside the range and
the pass form of the main kernel
consumes that list, carrying the token's FP32 dQ / dQ_rope partial
between passes -- so that each pass's
accumulator slice stays L2-resident; the single-pass kernel runs
unchanged everywhere else.
- **Cast**: un-permutes the FP32 accumulators into the natural `[S,
512]` / `[S, 64]` BF16 gradients (or
natural-layout FP32 gradients when the caller asks for `dkv_fp32=True`);
the permuted accumulator never
  crosses the API boundary (registry field `dkv_acc_layout`).

## Numerics

BF16 operands into the tensor cores (Q, K, V, P, dS), FP32 accumulation;
the backward recomputes S from
the BF16 Q and K and forms `delta` from the saved BF16 output residual.
`dq` is computed once per row
(bitwise deterministic); `dkv` is accumulated in FP32 with atomics then
cast to BF16 (run-to-run spread
reported below). Fully masked rows give `out = 0`, `lse = -inf`, `dq =
0`. No precision was traded for speed.

## Performance (B200)

Arm A = FlashMLA sparse forward + cuDNN frontend DSA backward; arm B =
FA sparse-MLA kernels (PR 2914,
`gather_bwd_recompute_p=True`, `gather_bwd_token_chunk=4096`). Same node
and GPU, sequential arms,
bit-identical seeded inputs, three alternating rounds (A, B, this PR per
round), medians of 20 steps (13 at
128k). Forward / backward columns are the CUPTI kernel-time sums of the
components (torch.profiler); the step
column is the CUDA-event wall time of the whole training step including
the wrappers (for this PR: the source
implementation's forward and backward entry points, `topk_length`
derived inside, cost included; the
generated programs in this PR launch the same kernels -- the export run
validated them bitwise against the
source on five rows with step-time ratios 0.9992-1.0002). Ratios > 1
mean this PR is faster. Loaded SM
clocks 1657-1965 MHz (driver default, recorded per arm and row); rows
marked `*` had > 3 % clock spread
between arms and are reported as measured, not corrected (packed_N1:
this PR at 1665 MHz vs 1702 / 1732 for
A / B; packed_N4: 1657 vs 1717 / 1702; packed_N8: 1732 vs 1770 / 1695;
packed_N32: 1800 vs 1845 / 1770;
skewed8: 1710 vs 1770 / 1702).

| row | T | S | docs | fwd ms (this PR / A / B) | bwd ms (this PR / A /
B) | step ms (this PR / A / B) | A / this PR (fwd, bwd, step) | B / this
PR (fwd, bwd, step) |
|---|---:|---:|---:|---|---|---|---|---|
| doc_4096 | 4096 | 4096 | 1 | 0.916 / 1.185 / 1.175 | 3.805 / 4.185 /
5.220 | 4.785 / 5.364 / 6.552 | 1.294, 1.100, 1.121 | 1.283, 1.372,
1.369 |
| doc_8192 | 8192 | 8192 | 1 | 2.037 / 2.365 / 2.301 | 8.624 / 9.293 /
10.986 | 11.027 / 11.828 / 13.733 | 1.161, 1.078, 1.073 | 1.130, 1.274,
1.245 |
| doc_16384 | 16384 | 16384 | 1 | 4.310 / 4.727 / 4.589 | 18.988 /
20.079 / 23.606 | 23.692 / 25.090 / 28.573 | 1.097, 1.057, 1.059 |
1.065, 1.243, 1.206 |
| doc_32768 | 32768 | 32768 | 1 | 8.851 / 9.511 / 9.232 | 40.729 /
42.310 / 50.889 | 50.267 / 52.963 / 59.056 | 1.075, 1.039, 1.054 |
1.043, 1.249, 1.175 |
| doc_65536 | 65536 | 65536 | 1 | 19.116 / 23.316 / 19.450 | 90.334 /
94.305 / 111.0 | 109.1 / 117.9 / 129.5 | 1.220, 1.044, 1.081 | 1.017,
1.229, 1.188 |
| doc_131072 | 131072 | 131072 | 1 | 42.094 / 51.553 / 44.006 | 205.5 /
212.8 / 255.9 | 246.3 / 262.8 / 300.5 | 1.225, 1.035, 1.067 | 1.045,
1.245, 1.220 |
| cptail_4k_65536 | 4096 | 65536 | 1 | 1.205 / 1.276 / 1.243 | 6.189 /
6.591 / 7.742 | 7.623 / 7.958 / 9.236 | 1.059, 1.065, 1.044 | 1.031,
1.251, 1.212 |
| cptail_4k_131072 | 4096 | 131072 | 1 | 1.367 / 1.407 / 1.380 | 7.353 /
7.880 / 8.904 | 8.846 / 9.365 / 10.514 | 1.029, 1.072, 1.059 | 1.010,
1.211, 1.189 |
| packed_N1 * | 32768 | 262144 | 1 | 11.956 / 11.934 / 12.032 | 62.431 /
64.965 / 78.474 | 74.225 / 76.347 / 89.283 | 0.998, 1.041, 1.029 |
1.006, 1.257, 1.203 |
| packed_N2 | 32768 | 262144 | 2 | 10.866 / 11.033 / 10.984 | 59.759 /
61.866 / 73.631 | 70.270 / 72.726 / 84.223 | 1.015, 1.035, 1.035 |
1.011, 1.232, 1.199 |
| packed_N4 * | 32768 | 262144 | 4 | 9.710 / 10.158 / 9.864 | 50.725 /
53.780 / 64.642 | 60.698 / 64.575 / 74.502 | 1.046, 1.060, 1.064 |
1.016, 1.274, 1.227 |
| packed_N8 * | 32768 | 262144 | 8 | 9.128 / 9.684 / 9.223 | 44.481 /
46.461 / 52.377 | 53.959 / 57.179 / 62.626 | 1.061, 1.045, 1.060 |
1.010, 1.178, 1.161 |
| packed_N16 | 32768 | 262144 | 16 | 9.151 / 9.676 / 9.188 | 42.138 /
44.814 / 50.356 | 51.698 / 54.720 / 59.675 | 1.057, 1.064, 1.058 |
1.004, 1.195, 1.154 |
| packed_N32 * | 32768 | 262144 | 32 | 9.108 / 9.792 / 9.211 | 42.797 /
44.550 / 50.364 | 51.660 / 54.461 / 59.784 | 1.075, 1.041, 1.054 |
1.011, 1.177, 1.157 |
| skewed8 (1:1:2:2:4:4:8:10) * | 32768 | 262144 | 8 | 9.505 / 10.016 /
9.747 | 48.277 / 51.399 / 60.091 | 58.677 / 61.737 / 69.839 | 1.054,
1.065, 1.052 | 1.025, 1.245, 1.190 |
| spread_32k_65536 | 32768 | 65536 | 1 | 9.434 / 9.882 / 9.586 | 47.480
/ 50.454 / 59.462 | 57.425 / 60.781 / 69.039 | 1.047, 1.063, 1.058 |
1.016, 1.252, 1.202 |
| spread_32k_131072 | 32768 | 131072 | 1 | 10.708 / 10.874 / 10.800 |
58.606 / 60.446 / 72.992 | 69.562 / 71.375 / 83.725 | 1.015, 1.031,
1.026 | 1.009, 1.245, 1.204 |
| spread_32k_196608 | 32768 | 196608 | 1 | 11.629 / 11.477 / 11.463 |
60.937 / 63.838 / 76.532 | 72.922 / 74.618 / 87.830 | 0.987, 1.048,
1.023 | 0.986, 1.256, 1.204 |

Training step: this PR is faster than A on 18 / 18 rows (A / this PR
1.023-1.121) and than B on 18 / 18
(1.154-1.369); backward kernel time vs cuDNN 1.031-1.100 on every row.
Forward alone is not a win everywhere:
by CUDA-event time this PR's forward trails FlashMLA on packed_N1
(0.987; kernel-only 0.998), packed_N2
(0.999; kernel-only 1.015) and spread_32k_196608 (0.973; kernel-only
0.987), and trails B's forward on
packed_N1 (0.981; kernel-only 1.006), spread_32k_65536 (0.995;
kernel-only 1.016) and spread_32k_196608
(0.984; kernel-only 0.986). On these large-S rows the forward of all
three arms is bound by the top-k gather
(2048 x 1152 B per token) and their kernel times are within 1.5 % of
each other; the event ratios additionally
contain each arm's host wrapper (this PR's forward wrapper --
validation, binding, `topk_length`
derivation -- costs more than FlashMLA's thin extension call).

Component attribution at doc_65536 (CUPTI kernel time, B200): forward
19.1 ms = 18.6 ms attention kernel +
the wrapper's `topk_length` derivation kernels (A FlashMLA forward 23.3
ms, B 19.5 ms); backward 90.3 ms =
preprocess 1.7 + main 88.7 + cast 0.05 ms (A cuDNN backward 94.3 ms, B
111.0 ms).

SM103 (GB300, 152 SMs, one GPU, same protocol, loaded clock 2070 MHz on
every arm and row, no clock flags):
this PR's step is faster than A on 18 / 18 rows (A / this PR
1.022-1.125) and than B on 18 / 18
(1.144-1.350); peak memory <= B on every row. At doc_65536: this PR
15.46 / 72.76 / 88.22 ms forward / backward
/ step (kernel-only 15.53 / 72.92) vs A 20.40 / 78.87 / 99.27 and B
15.98 / 90.57 / 106.56 (A / this PR step
1.125, B / this PR 1.208). Six forward rows trail FlashMLA there (event
/ kernel-only): cptail_4k_65536
0.969 / 1.039, cptail_4k_131072 0.938 / 0.998, packed_N1 0.979 / 0.979,
packed_N2 0.976 / 0.977,
spread_32k_131072 0.973 / 0.973, spread_32k_196608 0.979 / 0.978; the
other twelve are 1.04-1.32. On the two
cptail rows the kernel-only forward is at parity or ahead and the event
deficit is host time on the Grace
CPU (~95 us per forward call for this PR's and B's Python wrappers vs
~15 us for FlashMLA's extension); on the
four 32k-token rows the forward kernel itself is 2-3 % slower than
FlashMLA's. Accuracy on
SM103 matches SM100 to the printed digits; the only difference is a
query-side elementwise check
(atol = rtol = 1e-2 against the BF16-rounded reference) that flags 4 of
134 M `dq_latent` and 1 of 16.8 M
`dq_rope` elements at |diff| = 0.015625 on the iid 4k case -- the same
counts appear for B and 5 + 2 for A on
that GPU, and none for any of the three on B200; recorded, not gated.

### Memory

Peak memory above the inputs and saved activations at doc_65536 (B200):
this PR 12.59 GiB peak / 8.02 GiB
saved (`out`, `o_lo`, `lse`); B 13.69 GiB peak / 8.02 GiB saved; A 17.74
/ 8.60 GiB. Across the 18 rows this
PR's peak is 0.44-0.95 x B's and its saved set equals B's (gate: <= 1.05
x B). The backward's
scratch is `delta` (T x 64 x 4 B), the FP32 accumulators (S x 576 x 4 B)
and the descriptor workspace (< 1 KiB),
owned per binding by the cache (bounded: 32 bindings / 512 MiB) or by
the caller of the prepared runner; a
backward that takes the key-range passes adds `T x (147,456 + 4 x topk +
4)` B of pass scratch (608 MiB at
T 4096, top-k 2048; none of the rows in the table above except the two
CP-tail rows).

### Host path

B200, doc_4096, `benchmarks/bench_cake_dsa_train.py --host-us` (binding
cache off / on alternating in one
process, medians of 3 rounds x 20 calls, GPU asynchronous; measured on
the committed generated programs of the
freeze revision): `cake_backend.forward` 86.6 -> 21.5 us per call,
`cake_backend.backward` 154.6 -> 41.1 us,
public `dsa_sparse_attention` forward (autograd `Function.apply`) 104.7
-> 33.0 us; results bitwise equal
(`out`, `lse`, `dq_*`; `dkv_*` within the `red.global` run-to-run
spread, rel-L2 <= 7.5e-5) and kernel-only
time unchanged (fwd 1.10 / 1.04 ms, bwd 4.00 / 3.88 ms). The public
autograd backward
(`torch.autograd.grad`) costs 627 / 486 us per call and the autograd
step 941 / 628 us: `Function.backward`
runs on PyTorch's autograd device thread, whose two thread handoffs (~30
us each with an idle GPU, ~170 us
each while kernels are queued) and 3-4x slower Python execution add
several hundred microseconds that are
not in this package (a trivial `Function` with the same saved tensors
shows the same cost; no synchronization
anywhere). In a GPU-bound step this hides behind the 4-5 ms of backward
kernels at 4k tokens; host-bound loops
should use the eager entry points or the CUDA-graph runner.

## Accuracy (relative L2 vs a chunked FP64 reference of the same BF16
inputs)

Same harness, same seeded inputs for the three arms (B200); gate = 1.05
x B measured on the same case. Baseline A accuracy was measured in the
initial baseline round on the same node, container and seeded inputs;
baseline versions unchanged since.

| case | metric | this PR | B (FA PR 2914) | A (FlashMLA fwd + cuDNN
bwd) |
|---|---|---|---|---|
| iid 4k x 4k, top-k 2048 | out / dq_latent / dq_rope / dkv_latent /
dk_rope | 0.201 % / 0.215 % / 0.236 % / 0.232 % / 0.237 % | 0.196 % /
0.215 % / 0.236 % / 0.232 % / 0.238 % | 0.201 % / 0.220 % / 0.242 % /
0.234 % / 0.243 % |
| iid 4k x 4k with `topk_length` (valid-first slots) | out / dq_latent /
dkv_latent | 0.195 % / 0.230 % / 0.233 % | 0.191 % / 0.230 % / 0.233 % |
|
| peaked, self-weight 0.53 / 0.99 (4k x 4k) | dq_latent | 0.235 % /
0.238 % | 0.235 % / 0.238 % | 0.447 % / 9.60 % |
| peaked 32k x 256k (self-weight 0.99) | dq_latent row p99 (gate 0.4 %)
| 0.341 % | 0.318 % | 66.1 % |
| all cases | lse max-abs | <= 9.6e-6 | <= 9.9e-6 | <= 9.6e-6 |

The peaked cases are the failure mode of #5657: a query whose own key
carries almost all of the softmax mass
needs the exact `delta`; this PR and B stay at the BF16 floor there, the
cuDNN backward does not. The dq row
p99 of the 4k peaked 0.99 case is 0.43 % for this PR and 0.40 % for B
(the contract gates row p99 on the
32k x 256k case only; recorded as a diagnostic elsewhere).

Determinism: forward and dq bitwise across runs in every case; dkv is
accumulated with FP32 atomics, run-to-run
rel-L2 2.4e-6 to 3.4e-5 (B and A: same behaviour). compute-sanitizer
synccheck and memcheck on the backward
launches (preprocess, main, cast; doc_4096 row): `ERROR SUMMARY: 0
errors` for both tools at the kernel
snapshot above. Tests:
`pytest tests/experimental/test_cake_dsa_train.py` (44 tests; varlen
multi-document, q/kv length mismatch,
`-1` and out-of-range indices, top-k not a multiple of 2048 or of the
key block, fully masked rows, peaked
attention, `dkv_fp32` natural layout, binding-cache hits, key-range
passes; 128k rows in the benchmark).

## Key-range passes for the DRAM regime (backward)

With many keys the FP32 dK/dV accumulators (2304 B per key) outgrow the
L2 and the `red.global.add` scatter of the
backward main stage runs at DRAM speed. The backend now registers the
two-stage key-range-pass form of that stage
(`bwd_compact` + `bwd_main_pass`) next to the single-pass `bwd_main`,
and the host selects it by the policy carried in
the registry record (`key_pass_policy`):

* **Trigger**: `P = ceil(S * 2304 B / 100 MiB)` passes over disjoint key
ranges when `P > 1` **and** the whole row fits
the pass workspace budget (640 MiB: `T <= 4224` tokens at top-k 2048;
passes run over the whole row, no token
chunking). Otherwise the single-pass stage runs unchanged. At top-k 2048
that is `T <= 4224` and `S >= 45,512`
(two passes at `S = 65,536`, three at `131,072`); 4k x 4k rows and
32k-token rows stay single-pass, so of the 22
export rows only `cptail_4k_65536` (P = 2) and `cptail_4k_131072` (P =
3) change. Kernel sequence per backward:
`bwd_delta`, then per pass `bwd_compact` (one warp per token: the row's
keys inside the pass range, in slot order,
under the same validity rules) + `bwd_main_pass` (the main kernel over
that list, carrying the token's FP32 dQ /
  dQ_rope partial between passes), then `bwd_cast`.
* **Workspace**: the passes add `T * (147,456 + 4 * topk + 4)` B
(`dq_partial`, `key_scratch`, `pass_counts`) to the
caller-owned workspace -- 608 MiB at `T = 4096`, top-k 2048;
`dsa_train_workspace_size` includes them (nothing
  without passes). No launch allocates.
* **Determinism / numerics**: dQ is still written once per row from the
carried FP32 partial -- bitwise deterministic
run to run and across the validating and remembered-binding paths; its
partial sums are re-associated, so it differs
from the single pass in the last FP32 places (well inside the BF16
output and the accuracy gates). The dK/dV
reductions are the same `red.global.add` per key in another order
(run-to-run spread unchanged).
* **Override**: `key_passes=` on `dsa_sparse_attention(_varlen)`,
`cake_backend.backward` and `prepare_dsa_train`
(`None` = policy, `1` = single pass, `n` = that many passes); part of
the binding-cache key.
* **Binding cache**: a remembered binding owns no problem-sized scratch
-- `delta`, the FP32 dK/dV accumulators (one
zeroed span) and the key-range-pass regions come from the caching
allocator on every call like the outputs, and the
binding keeps only the descriptor workspace and a materialized
`topk_length` (kilobytes). The cache is LRU with
capacity 256 (`FLASHINFER_CAKE_DSA_TRAIN_BINDING_CACHE_CAPACITY`), so a
model whose layers cycle through up to that
many forward / backward bindings per step binds each once. Host path on
B200 with a remembered binding (two runs,
one of them on a fresh clone): 22-26 us per `forward` and 56-61 / 74-77
/ 87-93 us per `backward` call at `doc_4096` /
`cptail_4k_65536` / `cptail_4k_131072` (60 / 60 cache hits; the
validating path costs 174-183 / 232-244 / 250-265 us).
* **Tests** (+6 in this section, 57 total with the review follow-ups
below): policy rule and planner (override validation), workspace
regions, fake-record binding of
the pass stages, a forced three-pass small shape (T 256 x S 65,536) with
`-1` / out-of-range / `topk_length`
masking against the FP64 reference with bitwise dQ across runs, and the
whole-row policy case 4096 x 65,536 (two
  passes) through the public entry against the canonical gates.
* **Export**: both arms of the generated-program export follow the same
policy (the exporter verifies the record's
policy against the kernel snapshot's launcher and freezes the per-row
pass count); protocol lock 44 shapes / 6
templates; the CP-tail rows pass correctness with source/export bitwise
`dq` parity and the same kernel count per
step on both arms; the forward, `bwd_delta`, `bwd_main` and `bwd_cast`
generated sources are unchanged.
  Baselines and their versions are unchanged.

## Review follow-ups

* `indices` (and `k_rope`) views that start inside a larger storage are
passed to the kernels as the storage base plus
the element offset, like strided views, so the kernels' alignment test
for their 8-wide index tile loads sees the true
alignment; before, a contiguous view at an odd element offset raised
`CUDA error: misaligned address` (reproduced on
B200 at offsets 1 and 13). Tests: alias / rebind units, forward +
backward through the public entry with views at
offsets 1 / 8 / 13 (bitwise equal to the plain-tensor call), a forced
two-pass case at top-k 256.
* `S == 0` is rejected; `T == 0` returns empty outputs and zero
gradients from the eager entries and the autograd
  function without binding or launching; the explicit runner rejects it.
* Binding cache redesign as above (per-call scratch, LRU, capacity 256);
the kernel sequence per cached call is
  unchanged.
* README reflow (the workspace formula stays on one line) and the
benchmark's `--steps-128k` threshold (`< 2**34`, so
  the 128k row takes it).
* Not changed: the generated `run` bindings' pointer-extent /
`q_rope`-width checks -- those belong in the generator's
host contract and will arrive with regenerated sources; every public
entry validates shapes, dtypes and extents
  before binding.

## Baselines and their sources

- **A: FlashMLA sparse forward** -- deepseek-ai/FlashMLA `main` @
`ba89a3466e9470ad08ab39738d4e7bb66989e1e7`,
`flash_mla.flash_mla_sparse_fwd(q, kv.unsqueeze(1),
indices.unsqueeze(1), sm_scale, d_v=512)` (native
  head-64 SM100 kernel), built for sm_100a.
- **A: cuDNN frontend DSA backward** -- NVIDIA/cudnn-frontend 1.30.0
(`cudnn.DSA.sparse_attention_backward_wrapper`)
  with the cuDNN 9.24 runtime; valid-first indices + `topk_length`.
- **B: FA sparse-MLA kernels** -- Dao-AILab/flash-attention PR #2914
head `c9e2e5eb4c32ee06d659e25a7bc964e07e687e8f`
(branch `sparse-mla-64h-native`), CuTe DSL (`nvidia-cutlass-dsl`) 4.7.1,
quack 0.6.5,
`flash_attn_varlen_func(..., gather_kv_indices=..., pack_gqa=True,
gather_bwd_recompute_p=True,
  gather_bwd_token_chunk=4096, return_lse=True)`.
- Environment: NVIDIA 26.07 containers (PyTorch 2.13.0a0+nv26.07, CUDA
13.3, cuDNN 9.24.0); B200 (SM100,
148 SMs) at the driver's default clocks with the loaded SM clock
recorded per arm and row; GB300 (SM103,
  152 SMs, aarch64 host) for the SM103 paragraph.
- Reference oracle: chunked FP64 reference following the FA PR #2914
sparse-MLA test protocol
  (`tests/test_helpers/cake_dsa_train_reference.py`).
- Measured on the same node and GPU, sequentially, bit-identical seeded
inputs.

Provenance: this branch is rebased on upstream `main` at dfd17d64d
(merge-base); the added files are new
(`flashinfer/dsa_sparse_attention.py`,
`flashinfer/experimental/cake_dsa_train/`,
`tests/experimental/test_cake_dsa_train.py`,
`benchmarks/bench_cake_dsa_train.py`), so no upstream commit after the
merge-base touches them. The baselines are external projects pinned by
commit / release as listed above (not upstream FlashInfer kernels), and
none of them changed between the baseline round and the freeze
measurements.

## Experimental track

- Owner: Cake team (NVIDIA). Tracking issue: #5657. Graduation plan:
finalize the API contract and move the
backend to its stable home once the API has been consumed by a
training-framework integration; target
  four weeks.
- JIT-only (no AOT registration); not part of automatic backend
selection, autotuning or trace-apply.
- Tests live under `tests/experimental/` and run in the experimental
lane.

## Checklist

- [x] Pre-commit (pinned hook versions) run on every added file; the
generated sources are byte-exact exporter
output and are excluded from clang-format by the directory-scoped
`.clang-format`.
- [x] Tests pass on B200 (`pytest
tests/experimental/test_cake_dsa_train.py`: 44 passed), also on a fresh
clone
      with cold JIT caches (re-run after the key-range-pass export).
- [x] Tables above filled from the paired A / B / this-PR measurements
(three rounds) on B200 and GB300.
- [x] Experimental track: tracking issue #5657.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

- **New Features**
- Added experimental sparse attention APIs for fixed-length and packed
variable-length inputs, with forward and backward support on select
NVIDIA GPUs.
- Added options for per-query top-k lengths, log-sum-exp output,
configurable key-range passes, and higher-precision key/value gradients.
- Added a benchmark for training performance and memory use, with
optional accuracy comparisons and host-latency measurements.
- **Documentation**
- Added guidance on supported inputs, outputs, gradients, and training
backend behavior.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [f558e9f](https://github.com/flashinfer-ai/flashinfer/commit/f558e9fd4e56807b6d12f147591efd44901d1d23)

- **作者**: Ligeng Zhu
- **时间**: 2026-09-30T08:34:44Z
- **提交信息**: feat(kda): kda for kda cutedsl impl (#5612)

<!-- .github/pull_request_template.md -->

## 📌 Description

Adds `backend="cute-dsl-persistent"` to `flashinfer.recurrent_kda` for
**Kimi Delta Attention** prefill. This ports the MIT-licensed CuTe
implementation from
[humanfia/kda-for-kda-release](https://github.com/humanfia/kda-for-kda-release/tree/b642859a00544f2599e7bb7edce686f637759a73/cute)
into FlashInfer's public API, JIT cache and workspace lifecycle.

The persistent M128/BT32 kernel fuses Q/K L2 normalization, the bounded
K3 gate, beta sigmoid, preparation, triangular solves and recurrence.
Five preparation stages overlap with the recurrence; split chains
exchange complete FP32 state. The imported device-kernel body is
preserved, with integration changes in scheduling and launch code.

- Explicit SM100/SM103 backend for contiguous BF16 inputs, D128 and H
divisible by eight, with FP32 value-first state. Fixed batches and
nonempty packed sequences are supported.
- Preserves the public in-place state-update contract, optional
final-state return and caller-provided output. Per-workspace scheduling
and handoff scratch support the current CUDA stream and warmed CUDA
Graph capture.
- Retains the exact INT21 schedules, uses complete-chain scheduling for
other shapes, and clears handoff flags on every invocation. No
approximate warmup split is used.
- Adds independent FP64 recurrence tests, FLA workload checks,
capture/stream/error-contract tests, documentation, a reproducible
benchmark, and MIT attribution packaged in the wheel.

Reported speedup: **2.88x** over MoonshotAI/FlashKDA on B300 (INT21
workloads).

## 🔍 Related Issues

Integration references: #4445, #4675 and #4845. This adds an explicit
CuTe backend alongside the existing KDA implementations.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

Ran all pre-commit hooks on the 11 changed files; all passed, including
mypy, Ruff and formatting. The all-files checkbox is left unchecked
because validation was scoped to this change.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

Validated on B300:

```text
pytest tests/kda/test_recurrent_kda_persistent.py -q
32 passed

# Rerun after adding the small-norm case and refining the FP64 normalization oracle:
pytest tests/kda/test_recurrent_kda_persistent.py -k 'not int21' -q
27 passed, 6 deselected

pytest tests/kda/test_recurrent_kda_prefill.py -k 'public_api_uses_phase or public_backend_requires or public_backend_option or auto_backend_selects_small_bh_at_half or auto_backend_uses_logical or auto_backend_falls_through' -q
7 passed, 277 deselected
```

All 33 cases in the final new test file have been validated across these
runs. The new tests cover fixed and packed layouts, partial chunks and
one-token packed segments, optional state, custom scale, FP32 in-place
updates, all six INT21 workloads, changed activation/state values across
graph replays, nondefault streams, inference-mode offset mutation, weak
decay/zero and small norms, alignment/alias checks and capture warmup
requirements. The full repository suite was not run.

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

- `backend="auto"`, existing backends and defaults retain their current
behavior. The new backend is opt-in; the public signature only gains an
accepted backend value.
- State pools/indices, checkpoints, frozen-state mode, GQA, unbounded
gates, speculative decode and strided activations are rejected
explicitly.
- One explicit workspace is bound to one stream and one captured call.
Capture requires warming the exact buffers and scalar arguments; offsets
remain fixed across graph replay. In eager mode, packed offsets are read
on the host before selecting/building the schedule.
- Architecture guards allow SM100/SM103; this PR was tested and
benchmarked on B300 (SM103). B200 validation is still pending. INT21
split schedules are selected only for their exact shapes on 148-SM
devices; other shapes use whole-chain scheduling.
- Numerical tests deliberately distinguish short FP64 comparisons (1%
relative L2 plus elementwise tolerances) from the documented
INT21/weak-decay accuracy contract. Long weak-decay state can exceed a
0.01 elementwise tolerance because of BF16 operand rounding.
- Split-grid schedules assume full-grid residency; overlapping
independent split-grid launches on separate CUDA streams is unsupported
and documented. Stream tests cover nondefault-stream execution and
sequential graph/eager interleaving.
- The imported device body retains its tuning switches and inline PTX.
Please focus review on the exact state handoff synchronization,
tensor/alignment guards and workspace/capture ownership. Self-review
fixed state alignment and int32-index bounds and removed shared mutable
handoff scratch from the source host path.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **New Features**
- Added an experimental persistent backend for recurrent KDA prefill on
supported NVIDIA hardware, with fixed-length and packed variable-length
sequence support and optional initial and final recurrent states.
- Added CUDA Graph capture and replay when workspace and outputs are
prepared in advance and replay inputs remain consistent.
- **Documentation**
- Documented backend requirements, supported options, graph replay
constraints, and benchmark usage.
- **Benchmarks**
- Added correctness and timing comparisons with FlashKDA across six
workloads.
- **Licensing**
- Added license and attribution information for the persistent KDA
kernels.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Ligeng Zhu <7783214+Lyken17@users.noreply.github.com>
Co-authored-by: Dongyun Zou <songb@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: DongyunZou <dongyunzou03@gmail.com>

### [aafe22f](https://github.com/flashinfer-ai/flashinfer/commit/aafe22ff614bddd2b117d14906ce5a6c20af6f49)

- **作者**: bhsueh_NV
- **时间**: 2026-09-30T07:49:55Z
- **提交信息**: fix(moe): initialize TRTLLM routing padding for TMA gathers (#5444)

<!-- .github/pull_request_template.md -->

## 📌 Description

Initialize unused rows in active TRT-LLM MoE expert tiles to `-1` during
routing.

Routing currently leaves these entries in `permuted_idx_to_token_idx`
uninitialized. If they contain valid-looking token IDs, FC1 TMA gathers
can load activations for padded rows even though the GEMM masks their
outputs. This makes latency depend on the previous contents of the
routing workspace.

This PR writes the padding indices in the existing routing producers,
alongside each tile's metadata. It suppresses those activation loads
without a separate initialization kernel. Live mappings and allocation
slack are preserved, including the tiles reserved for non-local experts
by Llama4's warp routing path.

The changes cover block, dynamic-block, cluster, cooperative, and
histogram/offsets routing paths. The routing documentation now states
that unused entries within the actual padded count are `-1`.

### Performance

Compared main `5871b667` with this fix on an NVIDIA GB300, using
FlashInfer built from source, PyTorch `2.14.0+cu130`, and CUDA 13.0.

The synthetic NVFP4 reproducer uses 8,192 tokens, 896 experts, top-k 16,
hidden size 3,584, intermediate size 192, and SiTU activation. The input
includes 2,038 zero-valued token rows. The TMA case explicitly selects
tactic `(192, 2)`, which main advertises as valid for this shape. The
default tactic uses LDGSTS and does not reproduce the padding-content
slowdown.

Timing covers one MoE operation—routing, GEMMs, and finalize—using CUDA
events and CUDA graph replay, without NSYS. Each value is the median of
10 block averages, with 30 replays per block. Both versions start with
zero-filled routing-map padding. Diagnostic initialization is outside
the timed region; the writes added by this PR are inside it. Runs were
sequential on the same GPU.

| Tactic | PDL | Main | This PR | Latency change |
| --- | --- | ---: | ---: | ---: |
| TMA `(192, 2)` | ON | 1.791010 ms | 0.811724 ms | 54.68% lower |
| TMA `(192, 2)` | OFF | 1.787529 ms | 0.810462 ms | 54.66% lower |
| Default LDGSTS | ON | 0.576547 ms | 0.578629 ms | 0.36% higher |
| Default LDGSTS | OFF | 0.572997 ms | 0.575420 ms | 0.42% higher |

With the fix, the TMA case takes approximately the same time whether the
diagnostic initializes padding to `0` or `-1`. Each run also verifies
valid live mappings and bitwise-equal outputs across the initialization
conditions. These are operator-level measurements, not full-model E2E
results; the default LDGSTS tactic remains faster for this shape.

## 🔍 Related Issues

Related to
[#5349](https://github.com/flashinfer-ai/flashinfer/issues/5349).

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

The targeted GPU tests below passed on GB300 with the environment listed
above. The full CI matrix is pending.

| Validation | Result |
| --- | --- |
| `tests/moe/test_trtllm_gen_routing.py --full` | 690 passed, 24 skipped
|
| NVFP4 cases in `test_trtllm_gen_routed_fused_moe_format_parity --full`
| 6 passed, 12 non-NVFP4 cases deselected |
| `pre-commit run --all-files` | Passed |

All 22 new padding cases passed. They poison the routing map before
eager calls and CUDA graph replays, change routing patterns on fixed
buffers, and check live mappings, active-tile padding, untouched
allocation slack, and buffer canaries. Coverage includes PDL ON/OFF,
expert-parallel shards, Llama4 warp routing, fully aligned tiles, empty
local routing, and offset buffer views.

The 24 skips are existing cases whose tie-free logits construction
requires float32 beyond 256 experts. None of the new padding cases were
skipped. A poisoned-padding regression case was also verified to fail on
unmodified main.

```bash
pytest tests/moe/test_trtllm_gen_routing.py --full -q
pytest tests/moe/test_trtllm_gen_routed_fused_moe.py::test_trtllm_gen_routed_fused_moe_format_parity -k NvFP4xNvFP4 --full -q
pre-commit run --all-files
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

Please check the padding ownership boundaries, particularly the tiles
reserved for non-local experts in Llama4's warp path. Padding writes
occur before the existing PDL completion triggers.

AI-assisted implementation and validation.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved Mixture-of-Experts routing reliability by safely marking
unused entries in active tiles, preventing padded activations from being
gathered.
* Improved routing support for configurations with local and remote
experts, including custom expert placement and strides.
* Preserved allocation slack and buffer safeguards across eager
execution and CUDA Graph replay.

* **Tests**
* Added comprehensive coverage for tile padding, expert sharding,
routing permutations, and changing routing patterns.

* **Documentation**
  * Clarified routing-buffer padding behavior and expectations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Bo Hsueh <11360707+byshiue@users.noreply.github.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-10-01
**监控日期**: 2026-09-30
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4528
- **最后更新**: 2026-09-30T17:27:42Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Junda Su

## AI分析总结

## 提交分析总结：[9edc8ad] Move test-suite environment access into the registry and allowlists (#1898)

### 1. 主要更新类型
**基础设施重构**（归属 `misc` 类别），非功能新增或性能优化，属于测试工程化与安全治理层面的内部改进。

### 2. 关键变更点及与项目方向的关系
- **核心变更**：将测试套件中分散的环境变量访问逻辑，统一收敛到一个"registry（注册表）"机制中，并通过显式的 **allowlists（允许列表）** 控制哪些环境变量可以被读取/暴露。
- **与项目方向的关系**：FastVideo 作为高效的视频生成/推理框架，对外提供 Quick Start、Cookbook 等面向用户的文档。这种基础设施收口属于"练内功"——它本身不会改变模型推理性能或功能特性，但直接影响 CI 测试的稳定性与安全性，从而保障每次代码合入（如本 PR 关联的 #1898）的可靠性。

### 3. 对项目的影响和潜在意义
- **可维护性提升**：测试代码不再各自散读 `os.environ`，避免出现"隐式依赖"导致的脆弱测试，后续新增测试环境配置时只需在 registry 中登记一次。
- **安全与隔离**：allowlists 机制减少了环境变量泄露（如 CI 密钥、内部地址）到日志或错误报告中的风险，符合开源项目对 CI 日志安全的要求。
- **CI 成本与稳定性**：对一个拥有快速合入节奏的活跃仓库（有 weekly dev meeting、Cookbook 持续更新）而言，测试层的统一治理能降低"flaky test"（不稳定测试）造成的维护成本。

### 4. 值得关注的技术点
- **Registry 模式**：将环境访问声明式集中管理，是一种典型的"配置即数据"设计，可复用于其他需要类似管控的场景。
- **Allowlist 而非 Blocklist**：采用默认拒绝、显式放行的策略，这是安全工程中的推荐做法。
- **PR 号 #1898** 表明这可能源于某个实际遇到的测试问题（如环境变量在不同 runner 上不一致），是"治标也治本"的工程实践。

### 5. 结合项目背景对项目发展的影响
FastVideo 的 README 显示项目定位为易用、快速、文档完善的视频生成工具（Documentation / Cookbook / Quick Start / Slack 社区）。此类提交虽然对终端用户"无感"，但对开源项目的健康发展至关重要：它让贡献者在提交代码时拥有更可预期、更安全的测试环境，降低了外部参与贡献的门槛——而这正是项目文档化、社区化策略（Slack、开发会议）能否持续生效的底层支撑。因此，本次提交虽被标记为 `misc`，实际是为项目后续的功能迭代和规模化协作铺路的基础设施投资。

（完）

## 详细提交记录

### [9edc8ad](https://github.com/hao-ai-lab/FastVideo/commit/9edc8adf5f6f8e76072297af86d5b05324b54630)

- **作者**: Junda Su
- **时间**: 2026-09-30T07:15:39Z
- **提交信息**: [misc] Move test-suite environment access into the registry and allowlists (#1898)

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-10-01
**监控日期**: 2026-09-30
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34638
- **最后更新**: 2026-09-30T23:15:14Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 3
- **主要提交者**: yzhautouskay, Dhruv Nair, Steven Liu

## AI分析总结

# huggingface/diffusers 昨日提交分析

## 1. 主要更新类型

本次共 3 条提交，整体属于**代码质量与稳定性维护**为主的一次迭代，辅以针对特定模型的 **Bug 修复**：

- **类型注解补全**（#14874）：为 modular pipelines 补充返回类型注解。
- **Bug 修复**（#14897）：修复 Cosmos3 Transfer 在 control CFG 下 SeaCache 产生的伪影问题。
- **重构/清理**（#14838）：移除已废弃的代码路径。

## 2. 关键变更点及与项目方向的关系

- **Modular Pipelines 的类型安全强化**：#14874 通过添加 return type 注解和 return block，并配套测试验证其正确性，直接服务于 diffusers 正在推进的**模块化 pipeline 架构**。这一架构是项目的核心演进方向，让用户能以组合方式构建和复用扩散模型管线。类型注解与校验测试能确保模块化接口的一致性和可预测性，降低开发者使用门槛。
- **针对 Cosmos 系列模型的专项修复**：#14897 解决了 Cosmos3 Transfer 模型在使用控制信号 CFG（Control Guidance Scale）时，SeaCache（一种缓存/调度机制）引入的图像伪影问题。这反映出项目正在快速扩展对前沿模型（如 Cosmos 系列）的支持，并及时跟进其质量缺陷。提交中还对 SeaCache 指示器的使用指引进行了澄清，并对测试进行了重构，说明维护者重视文档与可维护性。
- **技术债清理**：#14838 移除废弃代码路径，与 #14874 中"跳过废弃内容"的处理呼应，表明项目正处于**统一精简、聚焦当前架构**的阶段。

## 3. 对项目的影响和潜在意义

- 类型注解与校验测试的加入，将提升 modular pipelines 的**健壮性和开发体验**，使接口变更更容易被工具链发现，有助于社区贡献者参与。
- Cosmos3 伪影修复直接提升**输出质量**，对实际使用 Cosmos Transfer 的用户有立竿见影的效果。
- 废弃代码的移除减小代码库体积与维护成本，但也意味着依赖旧接口的下游项目可能需要适配升级。

## 4. 值得关注的技术点

- **Return block + 类型注解 + 测试验证**的组合做法：不仅标注类型，还用测试实际校验返回结构，这是防止类型注解与实现脱节的有效手段。
- **SeaCache 与 Control CFG 的交互**：控制信号的 CFG 与缓存机制之间的相互影响是扩散模型工程中的典型难题，该修复提示这类缓存优化策略需谨慎对待条件生成场景。
- 提交中出现 Sayak Paul 的联合署名，体现项目核心维护者对前沿模型支持的高度参与。

## 5. 对项目整体发展的意义

diffusers 的 README 主要是许可证头，但项目背景明确：它是 HuggingFace 生态中开源扩散模型库，目标是提供统一、模块化的推理与训练接口。本次提交体现项目当前三大主线的推进——**模块化 pipeline 架构成熟化**（类型注解）、**前沿模型持续支持与质量打磨**（Cosmos3 修复）、**技术债清理以支撑长期演进**（移除废弃代码）。这些看似零散的改动，共同指向一个方向：让 diffusers 从"支持很多模型"的库，演进为"接口规范、质量可靠、易于扩展"的平台，为扩散模型的标准化和社区生态奠定基础。

## 详细提交记录

### [c60830e](https://github.com/huggingface/diffusers/commit/c60830ee365d520ab52b110dda562dd26f7b4d7f)

- **作者**: Steven Liu
- **时间**: 2026-09-30T15:59:23Z
- **提交信息**: [fix] Add return types (#14874)

* add return types

* add return blocks

* style

* modular pipelines

* add a test to validate

* feedback - skip deprecated stuff

### [78405ec](https://github.com/huggingface/diffusers/commit/78405ec9a1c1637c4027136658c96b7e85f915e5)

- **作者**: yzhautouskay
- **时间**: 2026-09-30T15:53:20Z
- **提交信息**: [Cosmos3] Fix Transfer SeaCache artifacts with control CFG (#14897)

* Fix Cosmos 3 Transfer SeaCache indicators

* Clarify SeaCache indicator guidance; tests refactor

---------

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

### [a12c38a](https://github.com/huggingface/diffusers/commit/a12c38a6893efbfacc6fedc3fd79878fd63c30fa)

- **作者**: Dhruv Nair
- **时间**: 2026-09-30T12:08:01Z
- **提交信息**: Remove deprecated code paths  (#14838)

update

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-10-01
**监控日期**: 2026-09-30
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


**报告日期**: 2026-10-01
**监控日期**: 2026-09-30
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13200
- **最后更新**: 2026-09-30T22:47:29Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Zhongjie Duan

## AI分析总结

# DiffSynth-Studio 昨日提交分析

## 1. 主要更新类型
**代码重构 / 代码质量优化**。此次提交的核心是简化了 LoRA 位置表达式的写法，不涉及新功能、Bug 修复或文档更新。

## 2. 关键变更点及其与项目整体方向的关系

- **变更内容**：简化了 LoRA（Low-Rank Adaptation）在模型中的位置/层表达方式。通常这类变更意味着将原来冗长的层路径字符串（如 `"unet.down_blocks.0.attentions.0"`）替换为更简洁的索引或通配符写法，或者提取了公共辅助函数来定位 LoRA 层。
- **与项目方向的关联**：DiffSynth-Studio 是一个面向扩散模型的统一合成/训练/推理框架，支持多种模型架构和 LoRA 微调。LoRA 位置表达的简化直接提升了**配置的可读性**和**扩展性**——当项目持续接入更多模型架构（如不同版本的 UNet、DiT、视频模型）时，简洁的位置抽象能显著降低维护成本，也降低用户配置 LoRA 微调时出错的概率。

## 3. 对项目的影响和潜在意义

- **用户体验提升**：用户在编写训练配置时，LoRA 层选择更直观，减少因路径写错导致的静默失败（LoRA 未挂载到正确层）。
- **维护性增强**：为后续在更多架构上支持 LoRA 打下了基础，降低了"每加一个模型就要维护一套层路径"的负担。
- **潜在风险**：若此重构未保留向后兼容（即旧的位置表达式不再被接受），则可能对现有用户的旧配置造成破坏性影响。PR 编号 #1714 暗示这是一次经过社区 review 的协作提交，通常会有兼容性考量。

## 4. 值得关注的技术点

- **LoRA 层定位机制的抽象化**：在多架构统一框架中，如何优雅地映射 LoRA 位置到不同模型的内部层路径，是一个值得深入研究的设计问题。
- **配置 DSL 的演进**：位置表达式本质上是项目配置语言的一部分，其简化趋势反映了项目在工程成熟度上的进步——从"能跑"到"好用"。
- **与社区 PR 流程的结合**：通过 GitHub PR 合并（#1714），体现了该项目对社区贡献的开放态度，这对开源框架的生态建设至关重要。

## 5. 基于项目背景的影响评估

DiffSynth-Studio 作为 ModelScope 生态下的扩散模型统一工具库，其核心价值在于**降低扩散模型的使用门槛**，让研究者和工程师能够通过统一接口完成训练、微调和推理。此次 LoRA 位置表达简化虽然从提交信息上看是一个较小的改动，但它代表了项目在**工程质量打磨**阶段的持续推进：

- 对于用户：降低了 LoRA 微调的配置门槛，使更多初学者能顺利上手。
- 对于项目：强化了"统一框架"这一核心卖点——只有内部抽象足够简洁，才能支撑持续扩展的模型生态。
- 对于社区：这是一个典型的"让代码更优雅"的重构提交，有助于吸引更多高质量贡献者参与。

总体而言，此次提交虽然规模不大，但与项目"统一、简洁、可扩展"的整体方向高度一致，是项目走向成熟的一个积极信号。

## 详细提交记录

### [974cfa3](https://github.com/modelscope/DiffSynth-Studio/commit/974cfa37f27ac55eba3b6d10efa21f876900572d)

- **作者**: Zhongjie Duan
- **时间**: 2026-09-30T08:07:00Z
- **提交信息**: Simplify the LoRA position expression (#1714)

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-10-01
**监控日期**: 2026-09-30
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 36678
- **最后更新**: 2026-10-01T01:17:48Z

## 提交统计

- **昨日提交总数**: 54
- **提交者数量**: 28
- **主要提交者**: Yuan Luo, Sage, Zhaoyi Li

## AI分析总结

# SGLang 昨日提交分析

## 一、主要更新类型

本次提交批次覆盖多种类型，大致分布为：**重构（约10次）** > **Bug修复（约18次）** > **功能新增（约12次）** > **性能优化/后端增强（约8次）** > **测试与文档/CI维护（约6次）**。整体呈现"架构重构 + 多硬件适配 + 推理功能扩展"并行推进的格局。

## 二、关键变更点及与项目方向的关系

**1. 核心架构重构与技术债清理**
- 调度器内部状态读写职责下放（#41950），移除大量无人读取的模型放置属性与参数，精简 ModelRunner 只保留 TP/PP group（#41811–#41817 系列）。
- 引入 `make_pp_layers` 等抽象，让模型层不再手工传递流水线并行位置信息，职责边界更清晰。
- **意义**：这些提交服务于 SGLang 高并发 LLM 推理的核心目标——减少配置传递链路中的混乱状态，降低多专家（MoE）+ 张量/流水线并行组合的维护成本。

**2. 多硬件/多后端持续扩展**
- AMD：gfx950 支持 DeepSeek-V4.1（#41308）、DSA indexer 按架构选波长（#41687）、flashinfer/TRT-LLM DSA 门控到 CUDA。
- NPU：dSA 模型的解码上下文并行（#37787）、Kimi-K3 PD 分离部署文档。
- SM100（B200/GB200）启用 ptx_kda prefill 后端，并修复 NaN 问题（#41445、#41572）。
- **意义**：SGLang 正从单一 NVIDIA 生态走向跨硬件推理平台，这对大规模集群部署是关键竞争力。

**3. 推理功能与性能相关**
- 投机解码持续增强：Qwen3.5 EAGLE3 流式重叠修复（#41154）、PP × 投机解码下混合循环状态提交修复（#40001）、top-p mask capture 引入 DFlash/DSpark（#34201）。
- PD 分离（prefill-decode disaggregation）多个修复：Mamba COW 槽释放、HiCache 前缀匹配钳位、queue_time 统计修正。
- HiCache：buffer 模式存储命中归属修正（#41758）。
- MiMo-V2 无 TorchCodec 可用、Responses/Kimi K3 inline instructions 保留等模型适配修复。
- **意义**：投机解码与 PD 分离是 SGLang 高吞吐推理的两大引擎，本批次修复直接提升长上下文与多模态场景的稳定性。

**4. Rust 渲染器与基建演进**
- Rust 侧新增 `sglang-processor` 库（#41896），提取 runtime.v1 protobuf 共享绑定（#41726）。
- 依赖升级：transformers 5.17.0、FlashInfer 0.7.0.post1。
- Router 续篇提交（8/13–11/13）：跨发现突发的舰队级共享获取、未见证 graft 时向舰队询问、bootstrapped 副本正确性证明。
- **意义**：Rust 组件正成为处理多模态输入（图像/视频）的轻量路径；Router 系列体现对大规模多副本路由正确性的系统性建设。

## 三、对项目的影响

- **架构层**：重构批次显著降低了 MoE + DP/TP/PP 并行配置的复杂度，为后续更激进的性能优化打下地基。
- **生态层**：AMD/NPU/多模型适配的密集提交说明 SGLang 正被更多生产环境采用，跨厂商支持是其开源影响力扩张的核心抓手。
- **稳定性层**：PD 分离与投机解码的修复直接利好长上下文、低延迟场景，是"Fast inference"承诺的兑现。

## 四、值得关注的技术点

- `--attn-dp-size` 替代 `--enable-dp-attention`：参数命名更精确地指向"按注意力层做数据并行"，API 演进值得升级时留意。
- top-p mask capture（投机解码 + RL）：将采样约束显式传入草稿模型，是投机解码质量提升的重要方向。
- 调度器状态职责下放 + 单元测试精简：提示测试策略从"重复断言内部状态"转向更高层的行为验证。
- Router 系列提交使用了大量 AI 协助（Claude 等）并标注"×/13"序号，是人机协作开发架构组件的典型案例。
- Rust 渲染器独立成库 `sglang-processor`，可能未来会作为独立分发组件发布。

## 五、对项目发展的整体判断

结合 README——SGLang 致力于 LLM 与多模态模型的快速推理——本批次提交恰好覆盖了三根支柱：**推理速度**（投机解码、KDA 后端、性能修复）、**系统稳定性**（PD 分离与调度器修复）、**平台广度**（AMD/NPU/多模型/Rust 渲染器）。大量重构表明项目正在消化早期快速迭代积累的技术债，为下一阶段的大规模生产部署和跨硬件推广做准备。项目正处于"功能覆盖向工程成熟度"的转型期，这与开源推理框架的发展规律一致。

## 详细提交记录

### [63321e3](https://github.com/sgl-project/sglang/commit/63321e3693599a1718644c425be92c519effac46)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-30T23:40:57Z
- **提交信息**: [Scheduler] Move internal-state readback and updates into a collaborator (#41950)

### [517cfa2](https://github.com/sgl-project/sglang/commit/517cfa218cfee933ed79d9878ca1ee36f85c1dc0)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-30T23:30:18Z
- **提交信息**: [Test] Prune redundant scheduler unit tests (#41952)

### [488869c](https://github.com/sgl-project/sglang/commit/488869c2d0f3321299488bcf221934df40b06454)

- **作者**: Jan Bernlöhr
- **时间**: 2026-09-30T22:28:16Z
- **提交信息**: [Fix] Keep MiMo-V2 processor available without TorchCodec (#41667)

Co-authored-by: jbernloehr <janbernloehr@users.noreply.github.com>

### [826f15b](https://github.com/sgl-project/sglang/commit/826f15bf9c8be2bd358c389724e9681f73c9d841)

- **作者**: James Liu
- **时间**: 2026-09-30T22:20:52Z
- **提交信息**: [Fix] Preserve inline instructions for Responses and Kimi K3 Messages (#40077)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: hnyls2002 <lsyincs@gmail.com>
Co-authored-by: Liangsheng Yin <hnyls2002@gmail.com>

### [8e4bcc5](https://github.com/sgl-project/sglang/commit/8e4bcc5ca9042396f632d49a05052197d6a7ff4d)

- **作者**: Sage
- **时间**: 2026-09-30T22:09:35Z
- **提交信息**: [rust-renderer] `sglang-processor` lib (#41896)

Signed-off-by: Sage Ahrac <sagiahrak@gmail.com>

### [f050ab1](https://github.com/sgl-project/sglang/commit/f050ab194ab5b1c6d792be06925658826c56bbd4)

- **作者**: Doğaç Eldenk
- **时间**: 2026-09-30T21:41:46Z
- **提交信息**: fix(spec): enable Qwen3.5 EAGLE3 capture and streaming overlap (#41154)

Co-authored-by: Yuhao Wang <59914901+jin-chuan@users.noreply.github.com>
Co-authored-by: Liangsheng Yin <95566987+hnyls2002@users.noreply.github.com>

### [a9c97c9](https://github.com/sgl-project/sglang/commit/a9c97c9f6973c03e778d1fe1e63a6b9f58a55012)

- **作者**: Cheng Wan
- **时间**: 2026-09-30T20:34:18Z
- **提交信息**: [Feature] Add --attn-dp-size and deprecate --enable-dp-attention (#41818)

### [201c4b9](https://github.com/sgl-project/sglang/commit/201c4b9b2a1e5a222bfedf97566ade0eef24d86c)

- **作者**: Jason Mancuso
- **时间**: 2026-09-30T20:32:26Z
- **提交信息**: [RL, Spec] Introduce top-p mask capture for spec and add DFlash/DSpark impl (#34201)

Co-authored-by: hnyls2002 <lsyincs@gmail.com>

### [986cb82](https://github.com/sgl-project/sglang/commit/986cb8268b8bfdc1f937251249943eb5507adbfa)

- **作者**: Cheng Wan
- **时间**: 2026-09-30T20:28:50Z
- **提交信息**: [Refactor] Enter draft TP scopes by attention ownership and drop ModelRunner.tp_group (#41817)

### [e7f6a99](https://github.com/sgl-project/sglang/commit/e7f6a99313633778188cf37d3d7d9f004c55a6e3)

- **作者**: Cheng Wan
- **时间**: 2026-09-30T20:28:34Z
- **提交信息**: [Refactor] Add make_pp_layers so models stop handing their PP position down (#41816)

### [00659ac](https://github.com/sgl-project/sglang/commit/00659ac0998b4243a2ceab4580f30711ab6e5bcb)

- **作者**: Cheng Wan
- **时间**: 2026-09-30T20:28:17Z
- **提交信息**: [Refactor] Stop passing models' layers the placement they already read (#41815)

### [c7fa37a](https://github.com/sgl-project/sglang/commit/c7fa37a5ca8898d45bd2a92272a35fee6c213c73)

- **作者**: Cheng Wan
- **时间**: 2026-09-30T20:27:58Z
- **提交信息**: [Refactor] Let FusedMoE's weight-loading helpers read the layer's MoE-TP rank (#41814)

### [499e86d](https://github.com/sgl-project/sglang/commit/499e86db983df6417fc1a5d8bcadc9e7d6edd5e4)

- **作者**: Cheng Wan
- **时间**: 2026-09-30T20:27:31Z
- **提交信息**: [Refactor] Keep only the TP and PP groups on the model runner (#41813)

### [a09aedf](https://github.com/sgl-project/sglang/commit/a09aedf1ca5ebe62c9f9ad646c4819afc95d65b6)

- **作者**: Cheng Wan
- **时间**: 2026-09-30T20:27:11Z
- **提交信息**: [Refactor] Drop model placement attributes and parameters nothing reads (#41812)

### [b0cc246](https://github.com/sgl-project/sglang/commit/b0cc246ff8cb990e247d8dae3f4b49d3a11738f6)

- **作者**: Cheng Wan
- **时间**: 2026-09-30T20:26:51Z
- **提交信息**: [Refactor] Drop placement values nothing reads (#41811)

### [4f3ee94](https://github.com/sgl-project/sglang/commit/4f3ee94d2572b09af97e9dbd031de0030bf99352)

- **作者**: Cheng Wan
- **时间**: 2026-09-30T20:26:32Z
- **提交信息**: [Fix] Make the Solar model constructible and runnable (#41810)

### [a659e64](https://github.com/sgl-project/sglang/commit/a659e6461f8684cb8aff0a7cfd065c2f4bd988e3)

- **作者**: Cheng Wan
- **时间**: 2026-09-30T20:26:12Z
- **提交信息**: [Fix] Size the prefill delayer's gather buffer to its TP group (#41809)

### [ecc0f0d](https://github.com/sgl-project/sglang/commit/ecc0f0dec2171b7cf9693b362f83b1b2b177cb0c)

- **作者**: Cheng Wan
- **时间**: 2026-09-30T20:25:54Z
- **提交信息**: [Fix] Pass the draft's attention ownership to DFLASH's eager LiLiCorr scope (#41808)

### [e289989](https://github.com/sgl-project/sglang/commit/e2899899331f77f78ecded9435de245aad7d1e4b)

- **作者**: Cheng Wan
- **时间**: 2026-09-30T20:25:38Z
- **提交信息**: [Fix] Shard MoE WNA16 and Quark INT4-FP8 weights by the MoE placement (#41807)

### [3f20738](https://github.com/sgl-project/sglang/commit/3f207388465683d2ed873631983a68eff8b48078)

- **作者**: Cheng Wan
- **时间**: 2026-09-30T20:25:19Z
- **提交信息**: [Fix] State the configured MoE-DP width in the weight-cache fingerprint (#41806)

### [e27b6e0](https://github.com/sgl-project/sglang/commit/e27b6e0971c7fefe74f5d61d0e16e0636da5a2d6)

- **作者**: Cheng Wan
- **时间**: 2026-09-30T20:25:03Z
- **提交信息**: [Fix] Read TensorCast's WORLD placement under its current names (#41805)

### [4407a21](https://github.com/sgl-project/sglang/commit/4407a21f3c390b4c34c367ac8a7eddaa45138f56)

- **作者**: YAMY
- **时间**: 2026-09-30T20:05:39Z
- **提交信息**: [Spec][PP] Fix hybrid recurrent-state commit and micro-batch pairing under PP x speculative decoding (#40001)

### [547286b](https://github.com/sgl-project/sglang/commit/547286bb5abbabe85e69c6c4d3d84a93f5954993)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-09-30T19:52:02Z
- **提交信息**: [Deps] Bump transformers to 5.17.0 (#39012)

Co-authored-by: Mohammad Angkad <mohammad.angkad@radixark.ai>
Co-authored-by: Xinyuan Tong <xinyuantong.cs@gmail.com>

### [036a3b3](https://github.com/sgl-project/sglang/commit/036a3b3e14af76a03a5520c8e07111786ac002b6)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-09-30T19:50:42Z
- **提交信息**: [Test] Lower the SM120 NVFP4 KV GSM8K threshold to 0.60 (#41799)

Co-authored-by: Mohammad Angkad <mohammad.angkad@radixark.ai>

### [eae8089](https://github.com/sgl-project/sglang/commit/eae808903ff571d9e00e65cea8ef03ba9a1b309f)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-09-30T19:42:19Z
- **提交信息**: [Deps] Bump FlashInfer to 0.7.0.post1 (#40709)

Co-authored-by: Mohammad Angkad <mohammad.angkad@radixark.ai>

### [4dfc0ac](https://github.com/sgl-project/sglang/commit/4dfc0ac131274e6fc4599345d33863e949e52947)

- **作者**: Jan Bernlöhr
- **时间**: 2026-09-30T19:05:41Z
- **提交信息**: [BugFix] Pass token-major Q/K tensors from Gemma-3 to RadixAttention (#37984)

Co-authored-by: Po-Han Huang (NVIDIA) <53919306+nvpohanh@users.noreply.github.com>
Co-authored-by: Po-Han Huang <pohanh@nvidia.com>

### [3a39844](https://github.com/sgl-project/sglang/commit/3a398442bfccac64a4e681093f1a1aec6a7d4cd1)

- **作者**: Kevin Mi
- **时间**: 2026-09-30T18:47:14Z
- **提交信息**: dsv4.1-amd: serve DeepSeek-V4.1 on gfx950 (#41308)

Co-authored-by: Kevin Mi <kevin.mi@radixark.ai>

### [9f9f9e7](https://github.com/sgl-project/sglang/commit/9f9f9e702a48a96b902a5cf580514dbec9acd6d9)

- **作者**: metamergebot
- **时间**: 2026-09-30T18:46:30Z
- **提交信息**: [HiCache] Attribute buffer-mode storage hits against the joint device match (#41758)

Co-authored-by: merrymercy <merrymercy@users.noreply.github.com>
Co-authored-by: xiezhq-hermann <xiezhq-hermann@users.noreply.github.com>

### [d26ec46](https://github.com/sgl-project/sglang/commit/d26ec4690d10d4c69890280b313d0409c8265feb)

- **作者**: zijiexia
- **时间**: 2026-09-30T17:51:36Z
- **提交信息**: docs: remove unreliable DeepWiki badge (#41851)

### [aec4b79](https://github.com/sgl-project/sglang/commit/aec4b799e61af971701d960e19d9d3062a6eb5ee)

- **作者**: Shuwen Wang
- **时间**: 2026-09-30T17:50:44Z
- **提交信息**: [PD][Mamba] fix: free the COW mamba slot of decode requests dropped before preallocation (#41451)

Co-authored-by: Shangming Cai <csmthu@gmail.com>

### [21ed9fb](https://github.com/sgl-project/sglang/commit/21ed9fbf441801c30c45504f30bcf54c54b26f40)

- **作者**: jain-ria
- **时间**: 2026-09-30T17:13:08Z
- **提交信息**: [Rust] Extract shared runtime.v1 protobuf bindings (#41726)

Signed-off-by: jain-ria <riajain@NVIDIA.com>

### [28c5e7f](https://github.com/sgl-project/sglang/commit/28c5e7f5cbac8bb1a4e645579dbf56d83f442cbc)

- **作者**: Sohom chakraborty
- **时间**: 2026-09-30T15:17:03Z
- **提交信息**: [Fix] Stop PD-decode queue_time from counting decode time before a retraction (#41380)

Signed-off-by: Sohom Chakraborty <sohomchakraborty.iitkgp@gmail.com>
Co-authored-by: Shuwen Wang <47200617+alphabetc1@users.noreply.github.com>

### [bd66ce3](https://github.com/sgl-project/sglang/commit/bd66ce343e4f6e2f2b75d7e820fe4d0718a8d824)

- **作者**: Mick
- **时间**: 2026-09-30T11:52:20Z
- **提交信息**: [diffusion] nightly: measure every framework with one client end-to-end methodology (#41689)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [4b3f63e](https://github.com/sgl-project/sglang/commit/4b3f63ec7090f588cc7c7b852031fdce7560c35a)

- **作者**: Kangyan-Zhou
- **时间**: 2026-09-30T11:19:26Z
- **提交信息**: [Router] Prove a bootstrapped replica answers like the one it copied (11/13) (#40697)

Co-authored-by: Kangyan Zhou <kangyan.zhou@radixark.ai>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [4c93012](https://github.com/sgl-project/sglang/commit/4c930125c7a4f055376db43337cfbb8c75700e13)

- **作者**: Kangyan-Zhou
- **时间**: 2026-09-30T10:59:21Z
- **提交信息**: [Router] Ask the fleet when a graft's splice goes unwitnessed (10/13) (#40696)

Co-authored-by: Kangyan Zhou <kangyan.zhou@radixark.ai>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [53225fa](https://github.com/sgl-project/sglang/commit/53225fadf40428149315d43f53b6df80d12957e0)

- **作者**: Cheng Wan
- **时间**: 2026-09-30T10:27:51Z
- **提交信息**: [Fix] Stop the namespace census at the leaf a read names (#41838)

### [f850047](https://github.com/sgl-project/sglang/commit/f8500474c94d06845e099f8865593dd2d03e8480)

- **作者**: Kangyan-Zhou
- **时间**: 2026-09-30T10:07:51Z
- **提交信息**: [Router] Share one fleet-wide fetch across a discovery burst (9/13) (#40695)

Co-authored-by: Kangyan Zhou <kangyan.zhou@radixark.ai>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [47dcde7](https://github.com/sgl-project/sglang/commit/47dcde70f40e7ceba59be1b1dc83a81b574c2b6e)

- **作者**: jacky.cheng
- **时间**: 2026-09-30T09:44:19Z
- **提交信息**: [Docs] Add MI355X FP8 agentic recipe to the Qwen3.5 cookbook (#41849)

### [57c8125](https://github.com/sgl-project/sglang/commit/57c81258d493a08953407ceabf2cf73b1307ff8b)

- **作者**: Yuan Luo
- **时间**: 2026-09-30T09:24:51Z
- **提交信息**: [KDA] Enable the ptx_kda prefill backend on SM100 (B200 / GB200) (#41445)

Co-authored-by: luoyuan.luo <luoyuan.luo@antgroup.com>

### [c029618](https://github.com/sgl-project/sglang/commit/c0296186b75ef2ff7a376b16161bb8b2f09f1de6)

- **作者**: Yuan Luo
- **时间**: 2026-09-30T09:23:54Z
- **提交信息**: [KDA] Fix ptx_kda prefill NaN without a gate lower bound and workspace growth (#41572)

Co-authored-by: luoyuan.luo <luoyuan.luo@antgroup.com>

### [8055ccd](https://github.com/sgl-project/sglang/commit/8055ccd2cd36964541b36b817e40f5a758e31746)

- **作者**: paulzhang-tm
- **时间**: 2026-09-30T09:19:02Z
- **提交信息**: [Linear Attention] Expose GDN/KDA prefill hooks and auxiliary cache accounting (#40227)

Co-authored-by: Ke Bao <ispobaoke@gmail.com>

### [9b7464c](https://github.com/sgl-project/sglang/commit/9b7464c8dd1c1c43d28c426232f2be9fd35c87a8)

- **作者**: EdwardXuy
- **时间**: 2026-09-30T09:17:39Z
- **提交信息**: ci: temporarily disable A5 (950) nightly job during power maintenance (#41856)

Co-authored-by: EdwardXuy <EdwardXuy@users.noreply.github.com>

### [e9b0d0c](https://github.com/sgl-project/sglang/commit/e9b0d0c0a3cc033a653501231b2de6af9ffec7db)

- **作者**: jiaryang
- **时间**: 2026-09-30T09:10:02Z
- **提交信息**: [AMD] Gate flashinfer and TRT-LLM DSA paths on CUDA (#40911)

### [d7cce54](https://github.com/sgl-project/sglang/commit/d7cce548859c9a088fcebf5d5f95c4269ab44146)

- **作者**: Michael
- **时间**: 2026-09-30T09:01:15Z
- **提交信息**: [AMD] Resolve QSA packed-varlen decode to aiter on HIP (#41513)

### [964c45c](https://github.com/sgl-project/sglang/commit/964c45cf31e838d85c048fe8c03fa51a588881a1)

- **作者**: amote-i
- **时间**: 2026-09-30T08:42:46Z
- **提交信息**: [NPU] [DOC]: add Kimi-K3 NPU PD disaggregation recipes (#41717)

### [4d4d3f2](https://github.com/sgl-project/sglang/commit/4d4d3f2e5ce7a6bb4ae09e342c9f750648aec711)

- **作者**: Kangyan-Zhou
- **时间**: 2026-09-30T08:34:12Z
- **提交信息**: [Router] Sweep the fleet for a peer snapshot and hand it to the pump (8/13) (#40694)

Co-authored-by: Kangyan Zhou <kangyan.zhou@radixark.ai>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [45c8ddd](https://github.com/sgl-project/sglang/commit/45c8ddddd3defbb760a221881b82911e67de3f11)

- **作者**: Mick
- **时间**: 2026-09-30T08:26:39Z
- **提交信息**: [diffusion] feat: check the final MP4 in-process instead of spawning ffprobe (#41825)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [0931a72](https://github.com/sgl-project/sglang/commit/0931a72eb2265b136b9d664448c4a79b34d988bd)

- **作者**: WenhaoZhang
- **时间**: 2026-09-30T08:23:56Z
- **提交信息**: [diffusion] feat: support MiniMax H3 RL  (#34365)

### [b87a241](https://github.com/sgl-project/sglang/commit/b87a241a6f977c2de475b1f7029d23c0b50adf09)

- **作者**: Michael
- **时间**: 2026-09-30T07:54:36Z
- **提交信息**: [AMD] Add Qwen3.8-Flash-Next-FP8 nightly validation (#36901)

### [682f4ef](https://github.com/sgl-project/sglang/commit/682f4ef32f46fd718fdc698c93e69a6b3a79f8f5)

- **作者**: jiaryang
- **时间**: 2026-09-30T07:47:04Z
- **提交信息**: [ROCm] Select DSA indexer top-k wave size by arch (wave32 on gfx1250) (#41687)

Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Thomas Wang <thomawan@amd.com>

### [51cae5f](https://github.com/sgl-project/sglang/commit/51cae5f303ec3c0c8fe20976c274fda8fc5bb1fe)

- **作者**: Shuwen Wang
- **时间**: 2026-09-30T07:26:15Z
- **提交信息**: [HiCache][PD] fix: clamp the decode restore to the prefix promised to prefill (#41450)

### [ec00066](https://github.com/sgl-project/sglang/commit/ec0006673abe8c2a89162d428ef9b68b67393797)

- **作者**: heziiop
- **时间**: 2026-09-30T07:22:16Z
- **提交信息**: [NPU] Add decode context parallel support for dsa models (#37787)

Co-authored-by: sglang-npu-bot <sglangnpu@163.com>

### [8c75ad9](https://github.com/sgl-project/sglang/commit/8c75ad9e62c8a994cd386f2357d1a9d7c1fcd0ac)

- **作者**: Shangming Cai
- **时间**: 2026-09-30T07:16:54Z
- **提交信息**: chore: bump mooncake version to 0.3.13.post1 (#41678)

### [3b537e9](https://github.com/sgl-project/sglang/commit/3b537e96e2e676583f72d0c86558570bc7723282)

- **作者**: Zhaoyi Li
- **时间**: 2026-09-30T07:02:42Z
- **提交信息**: [AMD][DI][CI] Leave the GLM-5.2 MTP decode room to load its Triton kernels (#41135)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-10-01
**监控日期**: 2026-09-30
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1287
- **最后更新**: 2026-09-29T13:34:55Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-10-01
**监控日期**: 2026-09-30
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 93008
- **最后更新**: 2026-10-01T01:06:32Z

## 提交统计

- **昨日提交总数**: 66
- **提交者数量**: 50
- **主要提交者**: Benjamin Chislett, stefankoncarevic, Matthew Bonanni

## AI分析总结

# vLLM 昨日提交合并总结（66 项提交）

## 一、主要更新类型

昨日 66 项提交以**性能优化**为绝对主导（ROCm、量化、CPU 平台合计约 20 项），其次为 **Bug 修复**（约 20 项，覆盖 Mamba/SSM、HiSparse、多模态、安全）与 **CI/测试维护**（约 15 项，集中于 ROCm、XPU、POWER10 平台）。另有少量**功能新增**（Rust 前端、PP+PCP、水印）、**模型支持扩展**（DeepSeek V4/V4.1、GLM 系列、MiniMax-M3）、**安全加固**与**重构**。

## 二、关键变更点

- **多硬件生态持续扩张**：ROCm（AMD）、XPU（Intel）、POWER10/PowerPC（IBM）、CPU aarch64（ARM）同步推进，与项目"人人可用"的普惠目标高度契合。
- **最新模型快速跟进**：DeepSeek V4/V4.1 在 ROCm 上引入共享 prefill chunk plan 与 FP4（a4w4）MoE 激活量化；GLM4V/GLM5Next 实现多模态归一化设备侧执行；MiniMax-M3 的 EAGLE3 投机解码与 Triton indexer 调优；另有 GLM-5.3-Flash、MiMo-V2.6 等。
- **推理性能深度优化**：AITER MoE/MLA 内核融合、KV-cache 写入优化、STRIDE-aware decode、CPU 向量化 Sampler Kernel、W4A16 量化在 POWER10 启用、NVFP4 CuTe-DSL 后端。
- **架构与工程质量**：共享 prefill chunk plan 减少多后端实现分叉；Mypy 类型清理、CODEOWNERS 更新、docs build gate 重启；聊天模板 DoS 修复、多模态缓存句柄认证、多项 Dependabot 依赖升级。

## 三、项目影响

- **降低部署成本**：多硬件与低精度量化投入使 vLLM 可服务更广泛用户，强化普惠定位。
- **加速生产级推理**：投机解码、MoE 融合等优化显著提升吞吐、降低延迟；FP4 虽为 opt-in，但为默认启用铺路。
- **模型可用周期缩短**：新模型从发布到生产可用的适配速度成为竞争力关键。
- **工程质量提升**：类型检查、安全修复与 CI 稳定性为高速迭代奠基。
- **生态主导地位**：AMD、IBM、Intel、Red Hat、Mistral 等多方参与，印证 vLLM 作为 LLM 推理事实标准的地位。

## 四、值得关注的技术点

- **AITER 深度集成**：AMD 生态推理内核加速成熟。
- **Rust 前端演进**：shutdown RPC 与 XGrammar 语法回放，暗示更高性能 API 路径。
- **PP>1 与投机解码协同**：EAGLE3 状态同步是大规模分布式推理的重要突破。
- **Mamba/HiSparse 密集修复**：新代码路径仍处快速成熟期。
- **设备侧多模态归一化**：减少 CPU-GPU 数据搬运，精细控制通信开销。
- **AI 协作开发**：Cursor、Claude 等签名反映开源开发流程的演进趋势。

## 五、综合评估

整体呈现**横向拓宽（多硬件/多模型/多量化格式）与纵向加深（性能/安全/工程质量）并进**的态势。项目正从以 NVIDIA CUDA 为核心走向全平台可部署的通用推理引擎，通过投机解码、MoE 优化与低精度量化持续压低单位推理成本，与 LLM 推理从"可用"向"可经济地规模化部署"过渡的行业趋势一致，巩固其开源推理引擎的领先地位。

## 详细提交记录

### [26ce58b](https://github.com/vllm-project/vllm/commit/26ce58b48cb7335abba9d0e2a8a522c58795402a)

- **作者**: Aarushi Jain
- **时间**: 2026-09-30T23:58:07Z
- **提交信息**: [ROCm][CI] Sync two AMD test groups between test-amd.yaml and test_areas (#59499)

Signed-off-by: aarushjain29 <aarushi.jain2@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [8fb16ea](https://github.com/vllm-project/vllm/commit/8fb16ea5a66f0ef362e728f0ff025f2845927fd5)

- **作者**: Benjamin Chislett
- **时间**: 2026-09-30T21:47:28Z
- **提交信息**: [Docs] Add PR checklist skill for coding agents (#57084)

Signed-off-by: Benjamin Chislett <bchislett@nvidia.com>
Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>

### [deb148e](https://github.com/vllm-project/vllm/commit/deb148e730225c64427f8ccf1f313cb4b33325b0)

- **作者**: Andrii Skliar
- **时间**: 2026-09-30T21:41:17Z
- **提交信息**: [Mamba] Add FlashInfer ReplaySSM support for MTP (#52928)

Signed-off-by: Andrii Skliar <askliar@nvidia.com>
Co-authored-by: Andrii Skliar <askliar@nvidia.com>

### [7e583e6](https://github.com/vllm-project/vllm/commit/7e583e615c20ee4ff0cd82aac592c7d6310aa7c3)

- **作者**: kliuae
- **时间**: 2026-09-30T21:26:54Z
- **提交信息**: [Bugfix][Core] Fix mamba prefill checkpoint block reservation and prompt-end eviction in align mode (#59175)

Signed-off-by: kliuae <kuanfu.liu@embeddedllm.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>

### [42f0c17](https://github.com/vllm-project/vllm/commit/42f0c17ea755a70656f92d278ba086e31fc72086)

- **作者**: Venky
- **时间**: 2026-09-30T21:14:24Z
- **提交信息**: [Bugfix][PP][Spec Decode] MiniMax-M3 EAGLE3 aux-state relay at PP > 1 and per-stage FlashInfer autotune (#57197)

Signed-off-by: venkywonka <23023424+venkywonka@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [73c7cae](https://github.com/vllm-project/vllm/commit/73c7cae4d746f64c22677348d1cc120eea6f7439)

- **作者**: Yueh-Ting (eop) Chen
- **时间**: 2026-09-30T20:50:01Z
- **提交信息**: [Bugfix][HiSparse] Stop the host pool feeding device KV cache residency metrics (#58725)

Signed-off-by: Yueh-Ting Chen <yueh.ting.chen@gmail.com>
Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [51048b1](https://github.com/vllm-project/vllm/commit/51048b13ce4229b85b980b582fda07c0aad81415)

- **作者**: Nils Matteson
- **时间**: 2026-09-30T20:31:21Z
- **提交信息**: [Docs] Clarify snapshot runtime image support (#59127)

Signed-off-by: Nils Matteson <nilsmatteson@icloud.com>

### [3eb6cec](https://github.com/vllm-project/vllm/commit/3eb6cec22ad9bb098393021b956feaa97081fc85)

- **作者**: Matthew Bonanni
- **时间**: 2026-09-30T19:43:09Z
- **提交信息**: [Bugfix][HiSparse] Adopt GPU prefix copies after the hit's allocation (#59282)

Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [84f738f](https://github.com/vllm-project/vllm/commit/84f738f1878ff2ab7664f1a4464b7f9f3cdb063d)

- **作者**: Venky
- **时间**: 2026-09-30T19:33:23Z
- **提交信息**: [Perf][MiniMax-M3] Triton indexer: decode grid retune + SM12.0 split-K (#56151)

Signed-off-by: venkywonka <23023424+venkywonka@users.noreply.github.com>
Signed-off-by: Zijing Liu <liuzijing2014@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: Zijing Liu <liuzijing2014@gmail.com>
Co-authored-by: Kyle Liang <199154931+kyleliang-nv@users.noreply.github.com>

### [b56b54b](https://github.com/vllm-project/vllm/commit/b56b54bc54073223d8acc04368fb004859df882e)

- **作者**: djramic
- **时间**: 2026-09-30T19:27:21Z
- **提交信息**: [ROCm][CI] Relax simple-nemotron-h-8b GSM8K threshold on ROCm (#59477)

Signed-off-by: Djordje Ramic <djoramic@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [a21a3f2](https://github.com/vllm-project/vllm/commit/a21a3f2ec76a02fada576b7e581a56307fb3e78f)

- **作者**: Matthew Bonanni
- **时间**: 2026-09-30T19:04:47Z
- **提交信息**: [CI] Add supports_multimodal_inputs to test_executor_replace's mock config (#59476)

Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [aba01ef](https://github.com/vllm-project/vllm/commit/aba01ef1f73d5bf24952c8f7d61febc509bbfefc)

- **作者**: Chaojun Zhang
- **时间**: 2026-09-30T18:23:02Z
- **提交信息**: [XPU][CI] Skip test_core_engine_actor_manager.py on Intel CI (#59338)

Signed-off-by: Chaojun Zhang <chaojun.zhang@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [ed3f6d1](https://github.com/vllm-project/vllm/commit/ed3f6d1a56272a966bd9e514cb262c0ce3ee6822)

- **作者**: Aarushi Jain
- **时间**: 2026-09-30T17:51:20Z
- **提交信息**: [ROCm][CI] Remove duplicate MI355 DPX jobs (#59256)

Signed-off-by: aarushjain29 <aarushi.jain2@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [b33e1cb](https://github.com/vllm-project/vllm/commit/b33e1cb172609343166ee485bf97c0a6f11587cf)

- **作者**: Aarushi Jain
- **时间**: 2026-09-30T17:44:40Z
- **提交信息**: [ROCm]Transpose compressed-tensors MoE weights on device (#59253)

Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [8f24ab3](https://github.com/vllm-project/vllm/commit/8f24ab30a36d62386bb0d30d2aa1c689806604af)

- **作者**: Rita Brugarolas
- **时间**: 2026-09-30T17:20:05Z
- **提交信息**: [ROCm][Kimi-K3][Perf] Fuse MLA decode KV-cache write and Q-prep via AITER (#57640)

Signed-off-by: Rita Brugarolas Brufau <rita.brugarolasbrufau@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [d2fb35f](https://github.com/vllm-project/vllm/commit/d2fb35f66e6ce9fbd0e32c6129b130ad90c1754c)

- **作者**: stefankoncarevic
- **时间**: 2026-09-30T16:24:08Z
- **提交信息**: [CI][ROCm] Drop the duplicate OAI Triton MoE run from FP8 MoE Kernels (#59237)

Signed-off-by: Stefan Koncarevic <Stefan.Koncarevic@amd.com>

### [8873ac8](https://github.com/vllm-project/vllm/commit/8873ac83bbd279aaf1aeacca4050e0baa8e56da2)

- **作者**: Thien Tran
- **时间**: 2026-09-30T16:23:40Z
- **提交信息**: [Docs] Add @gau-nernst to CODEOWNERS and committers (#59369)

Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [0f8b398](https://github.com/vllm-project/vllm/commit/0f8b398158f01fb3ea0e81b5adc93338fdf3db9c)

- **作者**: Raphaël Rialland
- **时间**: 2026-09-30T16:22:10Z
- **提交信息**: [watermarking] add context deduplication support to speculative decoding (#56807)

Signed-off-by: Raphael Rialland <raphael.rialland@mistral.ai>
Signed-off-by: Simon Veitner <sveitner@redhat.com>
Co-authored-by: Simon Veitner <sveitner@redhat.com>
Co-authored-by: Lucas Wilkinson <LucasWilkinson@users.noreply.github.com>

### [73a5831](https://github.com/vllm-project/vllm/commit/73a5831127a9d2b87102da8a6e7c96b6f7f64fcd)

- **作者**: Yoni Gozlan
- **时间**: 2026-09-30T16:21:02Z
- **提交信息**: [Frontend] Port chat_parsing core from Transformers (#58602)

Signed-off-by: Yoni Gozlan <yonigozlan@users.noreply.github.com>
Co-authored-by: Yoni Gozlan <yonigozlan@users.noreply.github.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [42a3dd5](https://github.com/vllm-project/vllm/commit/42a3dd5fec6f1ee9c7f84af7700fdf544aa4ca9c)

- **作者**: rasmith
- **时间**: 2026-09-30T16:15:03Z
- **提交信息**: [ROcm][BugFix][The Rock] Update The Rock dockerfile to most recent Triton 3.8 (#59287)

Signed-off-by: Randall Smith <Randall.Smith@amd.com>

### [ff1b87c](https://github.com/vllm-project/vllm/commit/ff1b87cca25690fef6bd12667fd0d26690d949af)

- **作者**: Yueh-Ting (eop) Chen
- **时间**: 2026-09-30T16:14:51Z
- **提交信息**: [Bugfix][HiSparse] Preserve host prefix publication after request completion (#59007)

Signed-off-by: Yueh-Ting Chen <yueh.ting.chen@gmail.com>
Co-authored-by: Matthew Bonanni <mbonanni@redhat.com>

### [279012f](https://github.com/vllm-project/vllm/commit/279012f94dac8a569c557b0fe86420099470650d)

- **作者**: Wei Zhao
- **时间**: 2026-09-30T16:12:12Z
- **提交信息**: [Docs] Add @wzhao18 to NVIDIA integration and kv offloading code owners (#59456)

Signed-off-by: wzhao18 <wzhao18.sz@gmail.com>
Co-authored-by: Codex <codex@openai.com>

### [c32513b](https://github.com/vllm-project/vllm/commit/c32513b99d29b3c6efee38df752a696bc2696c2f)

- **作者**: Eldar Kurtić
- **时间**: 2026-09-30T16:08:31Z
- **提交信息**: Add support for unquantized ngram in CT format (#59431)

### [c4df37d](https://github.com/vllm-project/vllm/commit/c4df37dfcc7f72ca41cd43801a468526ecf99a2b)

- **作者**: rasmith
- **时间**: 2026-09-30T15:51:40Z
- **提交信息**: [ROCm][BugFix][The Rock] Fix mori build for the rock (#59372)

Signed-off-by: Randall Smith <Randall.Smith@amd.com>
Co-authored-by: Misha Goin <mgoin64@gmail.com>

### [cff08b4](https://github.com/vllm-project/vllm/commit/cff08b461e086523cee8bba5bd3c66d302625134)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-09-30T15:32:00Z
- **提交信息**: [Security] Fix chat template resource-exhaustion DoS (GHSA-4hhp-h66f-… (#50300)

Signed-off-by: jperezde <jperezde@redhat.com>
Signed-off-by: Juan Pérez de Algaba <jperezde@redhat.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [fc2c801](https://github.com/vllm-project/vllm/commit/fc2c801ad93bcd8d7cd863645ee3ac8533cc85be)

- **作者**: Harry Mellor
- **时间**: 2026-09-30T15:18:50Z
- **提交信息**: Disable mypy `arg-type` and `assignment` checks in tests (#59428)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [17e9295](https://github.com/vllm-project/vllm/commit/17e9295dd565d0a2c2fe7404ecd27705aafbf354)

- **作者**: Yida Weng
- **时间**: 2026-09-30T15:09:11Z
- **提交信息**: [BugFix][Multimodal] Pick worst-case DeepSeek-V4 VL dummy image size (#59271) (#59373)

Signed-off-by: Yida Weng <84164537+YidaWeng@users.noreply.github.com>
Co-authored-by: Grok <grok@x.ai>

### [4e1182a](https://github.com/vllm-project/vllm/commit/4e1182a3a609a5165afd6de99b1269099b5d5999)

- **作者**: Sergey Shlyapnikov
- **时间**: 2026-09-30T15:08:21Z
- **提交信息**: [ROCm][MoE] Pad the AITER MoE intermediate size at allocation time, and round the expert-group count to a kernel that exists (#55368)

Signed-off-by: Sergei Shliapnikov <sergei.shliapnikov@amd.com>

### [2df122e](https://github.com/vllm-project/vllm/commit/2df122e65e87dc12870ce5f0180b49f012e7a53b)

- **作者**: Simon Danielsson
- **时间**: 2026-09-30T14:45:00Z
- **提交信息**: [ROCm][Perf][GLM-5.3-Flash] "Fit kpool top-k indices to AITER" with a single Triton kernel (#58008)

Signed-off-by: simondanielsson <simon.danielsson99@hotmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [643bbef](https://github.com/vllm-project/vllm/commit/643bbef55c37edb5c3fd341aae1e20e026d0e730)

- **作者**: aoshen02
- **时间**: 2026-09-30T14:29:12Z
- **提交信息**: [Refactor] Share workspace and model runner init between GPU and XPU workers (#59200)

Signed-off-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [eef8b15](https://github.com/vllm-project/vllm/commit/eef8b15d7c34019880b5ad8c811f60652aa4a6a7)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-09-30T14:26:16Z
- **提交信息**: [Security] Bump pyjwt and rand for remaining GHSAs (#59427)

Signed-off-by: Juan Pérez de Algaba <jperezde@redhat.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [98b45c1](https://github.com/vllm-project/vllm/commit/98b45c1a94db509e75fa9ef268cf5d2ae71875b7)

- **作者**: Qiu Chunshuo
- **时间**: 2026-09-30T14:21:56Z
- **提交信息**: [Feat] Support PP with PCP in GPU Model Runner V2 (#59139)

Signed-off-by: QiuChunshuo <qiuchunshuo@huawei.com>
Co-authored-by: Lucas Wilkinson <LucasWilkinson@users.noreply.github.com>

### [2e52a55](https://github.com/vllm-project/vllm/commit/2e52a558f04307b3f6f842e937e35aac079121c1)

- **作者**: Giulio De Pasquale
- **时间**: 2026-09-30T14:04:28Z
- **提交信息**: [Bugfix][Core] Schedule encoder-only prompts larger than one step (#59029)

Signed-off-by: Giulio De Pasquale <git@depasquale.giugl.io>
Co-authored-by: Isotr0py <2037008807@qq.com>

### [02a3c6d](https://github.com/vllm-project/vllm/commit/02a3c6dfc56c8776179a2e1c4fe01df270188f71)

- **作者**: Chaojun Zhang
- **时间**: 2026-09-30T13:50:40Z
- **提交信息**: [Test] Skip IPC weight-transfer test on XPU platforms (#59379)

Signed-off-by: Chaojun Zhang <chaojun.zhang@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [677e3f5](https://github.com/vllm-project/vllm/commit/677e3f5d5040db80087fd5693cd3434d1adcde83)

- **作者**: Cyrus Leung
- **时间**: 2026-09-30T13:45:28Z
- **提交信息**: [CI/Build] Fix pre-commit (#59426)

### [5463fe4](https://github.com/vllm-project/vllm/commit/5463fe4962785cdc3383477bf3af6533e7647dfd)

- **作者**: Varun Sundar Rabindranath
- **时间**: 2026-09-30T13:11:03Z
- **提交信息**: [KV-Offloading][TP] : Expand replicated_layout detection to multi-group MLA  (#57652)

### [f28a508](https://github.com/vllm-project/vllm/commit/f28a5081629377c36cd219a35070555b72279109)

- **作者**: JulienDarve
- **时间**: 2026-09-30T12:49:25Z
- **提交信息**: [Feature][Rust Frontend] Add Shutdown control RPC (#59316)

Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Signed-off-by: Julien Darve <jdarve@NVIDIA.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>

### [b22494c](https://github.com/vllm-project/vllm/commit/b22494cc0cb4bd9db4a62fb107d92429a4a3249d)

- **作者**: Harry Mellor
- **时间**: 2026-09-30T12:41:53Z
- **提交信息**: [Docs] Reinstate docs build gate for PRs (#59411)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [effdea9](https://github.com/vllm-project/vllm/commit/effdea9a5303f02759ba243ee624bf0a9b2576b0)

- **作者**: Jakub Zakrzewski
- **时间**: 2026-09-30T12:27:12Z
- **提交信息**: [MM][Mistral] Add compile support for Pixtral vision encoders (#57168)

Signed-off-by: Jakub Zakrzewski <jzakrzewski@nvidia.com>
Co-authored-by: Nicolò Lucchesi <nicolo.lucchesi@mistral.ai>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [93dd80f](https://github.com/vllm-project/vllm/commit/93dd80f63639453591e68891614729fb0bd44855)

- **作者**: almayne
- **时间**: 2026-09-30T12:23:42Z
- **提交信息**: [CPU] Conv1d optimised kernel for aarch64 (#54093)

Signed-off-by: Anna Mayne <anna.mayne@arm.com>
Co-authored-by: Li, Jiang <jiang1.li@intel.com>

### [df5668e](https://github.com/vllm-project/vllm/commit/df5668e5c935990cd9595bad2c3559b821092a5b)

- **作者**: Michał Ganczarenko
- **时间**: 2026-09-30T12:19:33Z
- **提交信息**: [XPU] Dispatch nn.LayerNorm to fused SYCL kernel via CustomOp (#57172)

Signed-off-by: Michal Ganczarenko <michal.ganczarenko@intel.com>
Co-authored-by: Claude Sonnet 5 <noreply@anthropic.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [a4c4bb4](https://github.com/vllm-project/vllm/commit/a4c4bb418e051e57b4a87084d757d5710cc66129)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-09-30T12:16:31Z
- **提交信息**: [Security] Bump remaining Dependabot packages (excl. ignored) (#59315)

Signed-off-by: Juan Pérez de Algaba <jperezde@redhat.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [3d5625c](https://github.com/vllm-project/vllm/commit/3d5625cc3c2474994107047d7a6ecb8e4008f9b0)

- **作者**: Clinton Thomas
- **时间**: 2026-09-30T12:16:26Z
- **提交信息**: [Security] Authenticate shared-memory multimodal cache handles (#59357)

Signed-off-by: Clinton Thomas <1033162+KernelClint@users.noreply.github.com>
Co-authored-by: Lucas Bourtoule <35483370+dhalf@users.noreply.github.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>

### [72e7874](https://github.com/vllm-project/vllm/commit/72e7874fa669617fd20c716e08cb486032f542c1)

- **作者**: Rukhaiya2004
- **时间**: 2026-09-30T11:44:48Z
- **提交信息**: [Hardware][Power] Enable W4A16 (AWQ & GPTQ) quantization on POWER10 using VSX (#59149)

Signed-off-by: Rukhaiya <bibirukhaiya123@gmail.com>
Co-authored-by: Li, Jiang <jiang1.li@intel.com>

### [863475e](https://github.com/vllm-project/vllm/commit/863475eb9cd78ae6a4a22f1b90df7fe85e0af438)

- **作者**: yuvalluria
- **时间**: 2026-09-30T11:13:23Z
- **提交信息**: docs: add gemma-2, SmolLM2, Qwen2.5-Coder, Llama-3.2-1B to batch invariance tested models (#54441)

Signed-off-by: Yuval Luria <yluria@redhat.com>
Co-authored-by: Claude Sonnet 4.6 <noreply@anthropic.com>

### [5a4351a](https://github.com/vllm-project/vllm/commit/5a4351ab096268944bf29a9b804800066309baa9)

- **作者**: Jakub Zakrzewski
- **时间**: 2026-09-30T11:08:24Z
- **提交信息**: [MM] Keep device input normalization fused when encoder compilation is enabled (#59195)

Signed-off-by: Jakub Zakrzewski <jzakrzewski@nvidia.com>
Co-authored-by: Codex <codex@openai.com>

### [5225f1b](https://github.com/vllm-project/vllm/commit/5225f1bacb907e3d7ec76e7f356c598468d229ec)

- **作者**: Taimys
- **时间**: 2026-09-30T11:06:07Z
- **提交信息**: [MyPy][3/N] Fix MyPy errors in test groups (part 3) (#55939)

Signed-off-by: Taimys <ffy2281693949@gmail.com>
Signed-off-by: Luyi Xiao <81631911+luyixiao95@users.noreply.github.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Luyi Xiao <81631911+luyixiao95@users.noreply.github.com>
Co-authored-by: Taimys <ffy2281693949@gmail.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [c4fa6f3](https://github.com/vllm-project/vllm/commit/c4fa6f36a7ba6fc9bb46c5934dc1e6ed88c00862)

- **作者**: apex-mochen
- **时间**: 2026-09-30T10:54:32Z
- **提交信息**: [Tests][Multimodal] Cover scoped processor kwargs precedence (#59399)

Signed-off-by: apex-mochen <2756823972@qq.com>

### [0103a9b](https://github.com/vllm-project/vllm/commit/0103a9b96fde27d26a464bf2c30b4d977b2a134f)

- **作者**: Matej Sirovatka
- **时间**: 2026-09-30T10:42:03Z
- **提交信息**: [Quantization] Add per-token NVFP4 CuTe-DSL MoE backend (#50030)

Signed-off-by: aoshen02 <aoshen@inferact.ai>
Signed-off-by: S1ro1 <matej.sirovatka@gmail.com>
Co-authored-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: aoshen02 <aoshen02@users.noreply.github.com>

### [d5ee309](https://github.com/vllm-project/vllm/commit/d5ee309314c78a52a0e154cb15d53e34844d623f)

- **作者**: Francesco Fusco
- **时间**: 2026-09-30T10:34:31Z
- **提交信息**: [UX] Tag torch.compile log lines with the component being compiled (#48133)

Signed-off-by: Francesco Fusco <ffu@zurich.ibm.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Luka Govedič <ProExpertProg@users.noreply.github.com>

### [d71f662](https://github.com/vllm-project/vllm/commit/d71f6626061af38dad1c3f27830366cf7f279fe4)

- **作者**: Akash kaothalkar
- **时间**: 2026-09-30T09:59:02Z
- **提交信息**: [Bugfix][Model][CPU] Fix Mamba2 quantized in_proj weight and scale loading for TP >1 (#58083)

Signed-off-by: Akash kaothalkar <akash.kaothalkar@ibm.com>
Co-authored-by: Akash kaothalkar <akash.kaothalkar@ibm.com>
Co-authored-by: Antigravity <antigravity@google.com>
Co-authored-by: Li, Jiang <jiang1.li@intel.com>

### [91dab0e](https://github.com/vllm-project/vllm/commit/91dab0eb7f42efd8580086935a7c0768a594f575)

- **作者**: Mathew Odden
- **时间**: 2026-09-30T09:43:16Z
- **提交信息**: [ROCm][Perf] Allocate the pinned PLE prefetch buffer lazily (#58797)

Signed-off-by: Mathew Odden <modden@redhat.com>
Co-authored-by: opencode+glm-5.3+vllm <opencode+glm-5.3+vllm@example.com>

### [5031991](https://github.com/vllm-project/vllm/commit/50319916a3c72ec1358f9e29c7c282d316d86f78)

- **作者**: djramic
- **时间**: 2026-09-30T09:42:25Z
- **提交信息**: [ROCm][CI] Move Basic Models (Other) to MI355 (#59400)

Signed-off-by: Djordje Ramic <djoramic@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [16d4ac4](https://github.com/vllm-project/vllm/commit/16d4ac4ba3a0a7d0b6a5eb11e203cd171a2d64a1)

- **作者**: yhcheong (vllmellm)
- **时间**: 2026-09-30T09:23:00Z
- **提交信息**: [ROCm][MoE] Support MiMo-V2.6 MXFP4 on gfx942 (#58262)

Signed-off-by: vllmellm <vllm.ellm@embeddedllm.com>

### [749192f](https://github.com/vllm-project/vllm/commit/749192ff41f4fddd6e5d3c4ef1eb5851175e8fc2)

- **作者**: aoshen02
- **时间**: 2026-09-30T09:20:32Z
- **提交信息**: [CI] Skip the IPC weight-checker test on non-CUDA platforms (#59398)

Signed-off-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [713ec07](https://github.com/vllm-project/vllm/commit/713ec07655a3d39daeeff0fd2fcb9dd251c73979)

- **作者**: Ronald
- **时间**: 2026-09-30T09:19:43Z
- **提交信息**: [Frontend][RL] Track HTTP weight operation outcomes and concurrency (#55781)

Signed-off-by: Ronald1995 <ronaldautomobile@163.com>
Signed-off-by: aoshen02 <aoshen02@users.noreply.github.com>
Co-authored-by: aoshen02 <aoshen02@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: aoshen02 <aoshen@inferact.ai>

### [ae66f9a](https://github.com/vllm-project/vllm/commit/ae66f9a97c6db39bb7225d7b0569acf6d2fdc300)

- **作者**: Akash kaothalkar
- **时间**: 2026-09-30T09:14:17Z
- **提交信息**: [Hardware][PowerPC] Prioritize bfloat16 for auto dtype on PowerPC (#58528)

Signed-off-by: Akash kaothalkar <akash.kaothalkar@ibm.com>
Co-authored-by: Akash kaothalkar <akash.kaothalkar@ibm.com>
Co-authored-by: Antigravity <antigravity@google.com>
Co-authored-by: Li, Jiang <jiang1.li@intel.com>

### [fb91712](https://github.com/vllm-project/vllm/commit/fb91712b38a68bb751526ad53552b91226290edd)

- **作者**: Avishek Goswami
- **时间**: 2026-09-30T08:57:21Z
- **提交信息**: [Model] Make the BERT/RoBERTa embedding class a class attribute (#59348)

Signed-off-by: Avishek Goswami <avishek.goswami@ibm.com>
Signed-off-by: Avishek Goswami <86944690+GOavi101@users.noreply.github.com>
Co-authored-by: Avishek Goswami <avishek.goswami@ibm.com>

### [3627a6a](https://github.com/vllm-project/vllm/commit/3627a6a124896edbc9f802e7c7e120633007e29d)

- **作者**: Simon Danielsson
- **时间**: 2026-09-30T08:16:29Z
- **提交信息**: [ROCm][Perf][GLM-5.3-Flash] Stride-aware decode KDA (#57979)

Signed-off-by: simondanielsson <simon.danielsson99@hotmail.com>

### [b819848](https://github.com/vllm-project/vllm/commit/b81984879ab28d0f7c22d21c688689613510ef92)

- **作者**: Alexandra Sidorova
- **时间**: 2026-09-30T08:03:37Z
- **提交信息**: [K2 Horizon] fold partial-RoPE permutation into q/k (and norm) weights (#55335)

Signed-off-by: Alexandra Sidorova <asidorov@amd.com>

### [0a30bc3](https://github.com/vllm-project/vllm/commit/0a30bc3f9ac3cc1a9339e115377a99d32252aed0)

- **作者**: cjackal
- **时间**: 2026-09-30T07:44:46Z
- **提交信息**: [Model] Extend device-side mm normalization to GLM4V/GLM5Next (#55389)

Signed-off-by: cjackal <44624812+cjackal@users.noreply.github.com>

### [8ee4069](https://github.com/vllm-project/vllm/commit/8ee40690331c25f19ecad49696dd54930fcab696)

- **作者**: Zheng Gong
- **时间**: 2026-09-30T07:31:51Z
- **提交信息**: [ROCm][DSv4.1][Perf] Use the shared prefill chunk plan in the ROCm sparse prefill (#58539)

Signed-off-by: Zheng Gong <zgong@amd.com>

### [87228cf](https://github.com/vllm-project/vllm/commit/87228cff01d7a56988e572c9a689444728f26568)

- **作者**: Bugen Zhao
- **时间**: 2026-09-30T07:29:01Z
- **提交信息**: [Rust Frontend] Replay roundtrip output grammars through XGrammar (#59143)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [fcd317c](https://github.com/vllm-project/vllm/commit/fcd317cf33b5113768a8ba1570f5211627f6fd63)

- **作者**: Zheng Gong
- **时间**: 2026-09-30T07:26:57Z
- **提交信息**: [ROCm][DSv4][Perf] Use the shared prefill chunk plan in the ROCm sparse prefill (#58405)

Signed-off-by: Zheng Gong <zgong@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [583637f](https://github.com/vllm-project/vllm/commit/583637f126a5f5193952a81ca9e0630ae9fc9986)

- **作者**: Rehan Khan
- **时间**: 2026-09-30T07:16:28Z
- **提交信息**: [CPU][Perf] Add vectorized Sampler Kernel (#53913)

Signed-off-by: Rehan Khan <Rehan.Khan7@ibm.com>
Co-authored-by: Li, Jiang <jiang1.li@intel.com>

### [77e8b02](https://github.com/vllm-project/vllm/commit/77e8b02c8d69f25867227fb9883797996fbfcd7b)

- **作者**: Fangzhou Ai
- **时间**: 2026-09-30T07:07:44Z
- **提交信息**: [ROCm][Perf] Add opt-in a4w4 (FP4 activation) MoE for DeepSeek V4.1 on AITER (#58819)

Signed-off-by: fai <fangzhouai@gmail.com>
Signed-off-by: Fangzhou Ai <31551580+Fangzhou-Ai@users.noreply.github.com>
Co-authored-by: Cursor Agent (Claude Sonnet 5) <cursoragent@cursor.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-10-01
**监控日期**: 2026-09-30
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7159
- **最后更新**: 2026-10-01T01:02:43Z

## 提交统计

- **昨日提交总数**: 7
- **提交者数量**: 7
- **主要提交者**: psv666, Sy03, amy-why-3459

## AI分析总结

## vllm-omni 昨日提交分析总结（第 1/1 批，共 7 条）

### 1. 主要更新类型

- **Bug 修复**：3 条（VoxCPM2 NPU 导入循环、Qwen3-Omni 音频输入回归、Helios KV cache 地址复用）
- **功能增强/性能优化**：1 条（Higgs Audio v3 MRV2 流式推理与 mixed-prefill 捕获边界）
- **数值稳定性优化**：1 条（Cosmos3 扩散采样状态 FP32）
- **CI/构建维护**：2 条（性能基线刷新、TTS 任务调度优化）

整体以稳定性与平台兼容性修复为主，辅以流式能力增强与 CI 健康度维护。

### 2. 关键变更点与项目方向的关系

项目定位是"让所有人轻松、快速、低成本地部署多模态（omni-modality）模型"。本次提交高度贴合这一方向：

- **多模型覆盖推进**：同时涉及 Cosmos3（扩散模型）、VoxCPM2、Higgs Audio v3、Qwen3-Omni、Helios 等多种音频/语音/多模态模型的修复与增强，说明项目正快速扩展对主流 omni 模型的支持面。
- **多硬件平台适配**：VoxCPM2 的 NPU（华为昇腾）补丁延迟加载修复，以及来自多个硬件厂商/研究机构的贡献者（NVIDIA、华为、高校），体现项目积极构建跨平台（GPU/NPU）部署能力。
- **流式与端到端体验**：Higgs Audio MRV2 流式使能直接服务"omni 模型服务"的核心场景——低延迟语音交互。
- **性能可观测性**：刷新 perf 基线与修复 `mean_e2el_ms` 端到端指标回归，说明项目已进入注重性能回归监控的成熟工程阶段。

### 3. 对项目的影响与潜在意义

- **稳定性提升**：三个 Bugfix 修复了可能导致崩溃（导入循环、KV cache 地址复用导致数据污染）和指标劣化的问题，降低用户生产环境风险。
- **数值可靠性**：Cosmos3 扩散采样状态保持 FP32 避免混合精度下的累积误差，对生成质量敏感的扩散模型尤为重要。
- **CI 可持续性**：拆分超长 TTS 任务至 nightly，缓解 CI 时长压力，保证主干反馈速度——这是多模型测试矩阵庞大项目的常见痛点。
- **性能防回归**：端到端指标修复 + 基线刷新，形成"发现问题—修复—建立基线"的闭环。

### 4. 值得关注的技术点

- **NPU 补丁延迟加载模式**：将平台特定补丁推迟到运行时而非模块导入时，是规避循环依赖的优雅解法，可为其他平台适配提供范式。
- **Mixed-prefill 捕获边界修复**：涉及 CUDA graph 捕获在混合 prefill 场景下的边界条件，属于推理引擎底层细节。
- **KV cache 地址复用防护**：跨注意力 KV cache 的地址安全性问题，是缓存复用机制的隐蔽隐患，修复价值高。
- **扩散模型精度策略**：在 FP16/BF16 混合精度推理中显式保留 FP32 采样状态。

### 5. 对项目发展的整体影响

结合 README "Easy, fast, and cheap omni-modality model serving for everyone" 的愿景，本批提交显示项目处于**从功能铺开转向工程加固**的阶段：一方面持续扩展支持的模型与硬件矩阵（NVIDIA、华为 NPU），另一方面通过指标回归修复、CI 任务重组、数值稳定性处理来夯实生产可用性。跨厂商贡献者的密集出现，也预示项目正朝着多模态推理服务的社区标准演进，为其"低成本、普适"的目标提供了扎实的工程质量基础。

## 详细提交记录

### [27a6321](https://github.com/vllm-project/vllm-omni/commit/27a6321a6311870fe68c2c9c13b694f2612ff779)

- **作者**: yzhautouskay
- **时间**: 2026-09-30T18:35:51Z
- **提交信息**: [Model][Cosmos3] Keep diffusion sampling state in FP32 (#7592)

Signed-off-by: Yuliya Zhautouskaya <yzhautouskay@nvidia.com>

### [4af28f3](https://github.com/vllm-project/vllm-omni/commit/4af28f33bd9c07e7e4fc862ac6ccb72834512995)

- **作者**: amy-why-3459
- **时间**: 2026-09-30T12:25:36Z
- **提交信息**: [Bugfix] Defer VoxCPM2 NPU patch to avoid platform import cycle (#8330)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [56763cd](https://github.com/vllm-project/vllm-omni/commit/56763cd6c383233f5ea2fab86f945401fd2f002a)

- **作者**: Sy03
- **时间**: 2026-09-30T11:32:27Z
- **提交信息**: [Model] Enable Higgs Audio v3 MRV2 streaming and fix mixed-prefill capture bounds (#8226)

Signed-off-by: Sy03 <1370724210@qq.com>

### [b44b2f9](https://github.com/vllm-project/vllm-omni/commit/b44b2f981c8029ae8c75010d70180fa915689162)

- **作者**: psv666
- **时间**: 2026-09-30T10:07:55Z
- **提交信息**: [Bugfix] Fix Qwen3-Omni audio-input mean_e2el_ms regression (#8306)

Signed-off-by: psv666 <2693925048@qq.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [c524e1a](https://github.com/vllm-project/vllm-omni/commit/c524e1a87967bd78d901b2fe3dae4446589c9ee8)

- **作者**: Alicia
- **时间**: 2026-09-30T09:24:25Z
- **提交信息**: [CI/Build] Refresh targeted perf baselines (#6538)

Signed-off-by: Alicia <115451386+congw729@users.noreply.github.com>

### [d0f0736](https://github.com/vllm-project/vllm-omni/commit/d0f073686afc4e740373ef709df6e2de26cd6698)

- **作者**: wangyu
- **时间**: 2026-09-30T09:08:24Z
- **提交信息**: [CI/Build] Split long weekly TTS jobs and route slow full-model cases to nightly (#8239)

Signed-off-by: wangyu <410167048@qq.com>
Co-authored-by: Alicia <115451386+congw729@users.noreply.github.com>

### [004a571](https://github.com/vllm-project/vllm-omni/commit/004a5711dc1495e38fd12c4deae0438f680f68fa)

- **作者**: Yan Cao
- **时间**: 2026-09-30T08:44:51Z
- **提交信息**: [Bugfix][Helios] Guard cross-attn KV cache against address reuse (#8064)

Signed-off-by: yancaocn <yancaochn@163.com>
Co-authored-by: yancaocn <yancaochn@163.com>
Co-authored-by: Zhou Taichang <tzhouam@connect.ust.hk>

---
