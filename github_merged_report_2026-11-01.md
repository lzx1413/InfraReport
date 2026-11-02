# GitHub Stars 合并报告 - 2026-11-01

**合并日期**: 2026-11-02
**监控日期**: 2026-11-01
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


**报告日期**: 2026-11-02
**监控日期**: 2026-11-01
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2272
- **最后更新**: 2026-11-01T19:42:29Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-11-02
**监控日期**: 2026-11-01
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2982
- **最后更新**: 2026-11-01T17:01:13Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-11-02
**监控日期**: 2026-11-01
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2322
- **最后更新**: 2026-11-01T16:59:21Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-11-02
**监控日期**: 2026-11-01
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6829
- **最后更新**: 2026-11-02T01:26:02Z

## 提交统计

- **昨日提交总数**: 58
- **提交者数量**: 1
- **主要提交者**: eigen

## AI分析总结

# FlashInfer 昨日提交分析总结

## 一、主要更新类型

昨日共 58 个提交，以性能优化为绝对主体（约 40 条），另有功能新增（约 8 条）、正确性/健壮性修复（约 6 条）及少量重构与文档维护。所有提交围绕自研 "Cake" 高性能内核体系展开，覆盖注意力（FMHA、MLA、稀疏注意力、AttnRes）、线性注意力与状态空间模型（GDN、Mamba2 SSD、mHC）、MoE、采样、RMSNorm/SiLU 融合算子、causal conv1d 及投影 GEMM 等全链路算子，焦点集中在 B200/GB300/R200 多代 Blackwell/Rubin 硬件的深度调优。

## 二、关键变更

**1. 跨架构调度与极致性能打磨。** 针对 Hopper sm_90a、Blackwell sm_100a/sm_103a 与 Rubin sm_107a 差异化调优：统一引入 `cp.async.bulk.prefetch` 配合 L2 evict-first 预读范式；Blackwell 上采用 CLC 动态分发与 token-queue 持久化程序替代静态跨步调度；tailpipe 变体与寄存器环形缓冲广泛用于隐藏访存延迟。MQA logits 在 B200/GB300 上引入四阶段 TMEM 环形缓冲程序变体，按 K 长度分桶路由，最高约 5.5% 加速。单点加速多在 1.003–1.18x，FMHA 短 KV 最高 1.284x，SM107 回退修复最高达 3.01x。

**2. 训练/自动微分生态补齐。** KDA、KCP、RMSNorm、GDN、dense GEMM、采样等内核新增或完善非确定性反向传播路径（dx 位级可复现），换取 1–4% 提升；新增确定性训练后端与确定性 causal conv1d backward 专用行组程序；causal conv1d、rmsnorm_silu_gate 在 `deterministic=False` 时换用更快的 dweight flush 策略与精确配对加法指令。引入可选 `keep_logits` 模式省去每 chunk 的 logits 重算 GEMM（耗时降至 0.75–0.84 倍，以峰值内存换速度）。补齐 `cake_gdn_train_kcp` 最后一个非确定性上下文并行变体，该系列四个变体全部上线；新增 KCP 反向 "lean" 局部工作区，节省约 17–23% 工作区内存，作为 opt-in 选项。

**3. 调度表驱动的架构适配。** 多数提交仅增加或重路由既有 record，以调度数据驱动硬件适配；按行数/token 数/通道数划分内核变体，选择 balanced chunk、persistent kernel 等策略；针对 sm_107a、sm_103a、sm_100a 分别重规划扫描表、bin-mix 条件调度与索引预取，其中一项修复了 backward 在全 SM 占用下阻塞不完成的调度问题，显著改善多流并发可预测性。

**4. 正确性与健壮性修复。** 修复 Blackwell softmax 指数单次舍入精度问题（约 1.4% 性能代价）；修复 Mamba2 SSD 组合预填充在 batch>1 时的越界写入，改为启动前 `ValueError` 快速失败；修复 `cake_lm_head_det_loss` 在选择性激活检查点下的反向失败；修复 SM107 上 BF16 误入 CP 自动波段导致的 51–433ms 延迟陷阱；移除 mega_mhc 的 64 tokens/SM 启动上限；用带溢出检查的宿主端算术重建 TMA 描述符（SASS 字节级不变）。

**5. host 端启动开销削减。** KDA/KCP 预填充合并索引收集与 launch 记录构建、tvm-ffi stream 上下文粒度优化、静态参数与模块缓存——设备程序不变即可获益，对 CUDA Graph 场景尤为重要。

## 三、项目影响

- **推理性能持续领先**：多点优化累积对端到端延迟贡献可观，巩固对 `torch.compile`、trtllm-gen 等竞品的优势。
- **向训练推理一体化演进**：非确定性/确定性双后端、SAC 兼容修复、训练后端补齐系统性拓展训练场景；非确定性 KCP 变体比最强非 Cake 实现快 3.7–5.2×，确立上下文并行训练竞争优势。
- **新硬件与新模型前瞻布局**：SM107 从缺记录到全覆盖；服务 MiniMax-M3、Kimi K3、Gated DeltaNet 等前沿模型结构。
- **成熟期精耕**：多数提速 1–10% 属边际但系统性的优化，逐 PR 小步迭代，项目进入微优化阶段；严格遵循位级一致、A/A 噪声基线与统计检验纪律，工程可靠性持续提升。

## 四、值得关注的技术点

- **程序变体管理复杂度**：mega_mhc 已有 43 个变体、cake_sampling 达 153 个符号，变体爆炸治理是长期工程挑战。
- **CLC 动态调度与 TMEM 四阶段环形缓冲**：token 按 CTA 动态分配到 SM、利用 Blackwell 张量内存结构化双缓冲隐藏累加延迟，代表硬件特性驱动的微架构创新。
- **内存-速度权衡显式化**：`keep_logits` 与 `local_arena="lean"` 均为 opt-in 设计，体现良好的 API 演进习惯。
- **CP 波段的架构敏感性**：同一调度策略在不同 SM 代际表现天差地别，凸显硬件感知调度的必要性。

整体而言，FlashInfer 正以 Cake 内核族为主线，在 B200/GB300/R200 三代硬件上建立系统性调优体系，稳步向覆盖训练—推理全链路的高性能算子库方向演进。

## 详细提交记录

### [c703cf1](https://github.com/flashinfer-ai/flashinfer/commit/c703cf1f1526140bd8e099606729b86bfd064621)

- **作者**: eigen
- **时间**: 2026-11-01T23:41:26Z
- **提交信息**: perf(cake_selective_state_update): L2 read-ahead builds of the lean P-split decode programs at their measured shapes on sm_100a (#8237)

`flashinfer.mamba.selective_state_update(..., backend="cake")` runs the
Mamba2 selective-state-update decode step under both the SGLang and the
canonical calling conventions. The kernel's variants are defined by
these dimensions: SSM state dtype (BF16 or FP32), input convention
(canonical FP32 dt / D / dt_bias with an int64 state-slot index, or raw
SGLang BF16 dt / D / dt_bias with an int32 slot index and padded
fused-projection rows), head dim 64 or 128 (state dim 128), single-token
decode or multi-token (speculative) decode with an intermediate-state
cache or a destination-slot table, and an optional fused z gate and dt
softplus. The baseline is the previous Cake version, which is FlashInfer
main after #8203. This PR changes routes only on sm_100a (B200, 148
SMs), and only for two single-token shapes. Both have 128 heads in 8
groups, state dim 128, BF16 state and canonical FP32 dt/D with an int64
slot index. The first is batch 257 at head dim 128
(fitest_stp_persistent), and the second is batch 320 at head dim 64
(fitest_stp_hd64_paired_rows_b320). Main already runs these shapes on
lean P-split programs: the head-dim-128 program for the first, and the
head-dim-64 paired-rows program for the second. This PR runs them on new
L2 read-ahead builds of those same programs.

In these builds, right after the producer issues its first stages, it
prefetches into L2 (`cp.async.bulk.prefetch.tensor`) the state tiles of
every further head of the CTA's work tile. On a split build, it
prefetches only the CTA's own P slice of those tiles. It then loads them
stage by stage after the previous head's writeback. The prefetch is only
a hint: every tile is still loaded, updated and stored by the same TMA
requests as in main. The new build option enters every paired-rows
program's identity, so 36 existing paired-rows programs get new names.
Apart from the embedded name, their source text and their sm_100a and
sm_103a machine code are unchanged. Two new programs are added, for
sm_100a only, and no other route changes on either GPU. Outputs and
states are bitwise identical to main's on all 122 shapes on each GPU.

On B200, both changed shapes run faster than main in every round of both
runs:
- fitest_stp_persistent: 1.003x (main 313.255 us, this PR 312.303 us)
- fitest_stp_hd64_paired_rows_b320: 1.002x (main 195.248 us, this PR
194.904 us)

The other 120 shapes keep main's program, some under its new name only,
and their speedups (0.995x to 1.006x) are run-to-run variation. A small
table shows the two changed shapes on 12 B200 GPUs across three nodes,
with two sessions per GPU. This PR is faster on every GPU in every
session: 1.0040x to 1.0048x on fitest_stp_persistent (1.25 to 1.50 us
saved) and 1.0016x to 1.0032x on fitest_stp_hd64_paired_rows_b320 (0.32
to 0.62 us saved). On GB300 (sm_103a), no program changes, though 58
shapes now use the new names. All 122 GB300 speedups (0.995x to 1.011x)
are run-to-run variation.

*NVIDIA B200 (sm_100a, 148 SMs), driver 580.82.07, CUDA 13.4; PyTorch
2.14.1+cu130; programs compiled with nvcc 13.4. Timer: CUPTI kernel time
with a cold L2; times are medians over 2 runs x 9 interleaved rounds
(us); speedup = main / this PR; the program column says whether this PR
routes the shape to a different program (`new`) or keeps main's program,
possibly under its new name (`same`).*

| case | batch | tokens | heads | groups | head dim | state dim | state
| inputs | options | main (us) | this PR (us) | speedup | program |
|---|---:|---:|---:|---:|---:|---:|---|---|---|---:|---:|---:|---|
| sample_stp_bf16 | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 37.728 | 37.712 | 1.000x | same |
| sample_stp_state_fp32 | 64 | 1 | 64 | 8 | 128 | 128 | FP32 | FP32
dt/D, int64 index | - | 76.144 | 76.096 | 1.001x | same |
| sample_stp_z | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D, int64
index | z gate | 38.368 | 38.368 | 1.000x | same |
| sample_stp_softplus | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | softplus | 37.664 | 37.712 | 0.999x | same |
| sample_stp_z_softplus | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32
dt/D, int64 index | z gate, softplus | 38.416 | 38.432 | 1.000x | same |
| sample_stp_ratio1 | 32 | 1 | 16 | 16 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 7.800 | 7.808 | 0.999x | same |
| sample_stp_ratio16 | 32 | 1 | 128 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 38.848 | 38.864 | 1.000x | same |
| sample_stp_b256 | 256 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 156.056 | 156.048 | 1.000x | same |
| sample_stp_b128 | 128 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 78.544 | 78.552 | 1.000x | same |
| sample_mtp1 | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D, int64
index | - | 37.696 | 37.720 | 0.999x | same |
| sample_mtp2 | 64 | 2 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D, int64
index | - | 39.496 | 39.560 | 0.998x | same |
| sweep_bfloat16_vertical_b1 | 1 | 6 | 64 | 8 | 64 | 128 | BF16 | FP32
dt/D, int64 index | softplus, state cache, no state write,
algorithm=vertical | 3.760 | 3.760 | 1.000x | same |
| sweep_bfloat16_horizontal_b1024 | 1024 | 6 | 64 | 8 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus, state cache, no state write,
algorithm=horizontal | 1173.380 | 1173.700 | 1.000x | same |
| dynamic_dump_b1_t1_prev0 | 1 | 1 | 16 | 1 | 64 | 128 | FP32 | FP32
dt/D, int64 index | softplus, dst slots, algorithm=simple | 2.816 |
2.816 | 1.000x | same |
| dynamic_dump_b1_t2_prev1 | 1 | 2 | 16 | 1 | 64 | 128 | FP32 | FP32
dt/D, int64 index | softplus, dst slots, algorithm=simple | 3.024 |
3.016 | 1.003x | same |
| dynamic_dump_b1_t4_prev2 | 1 | 4 | 16 | 1 | 64 | 128 | FP32 | FP32
dt/D, int64 index | softplus, dst slots, algorithm=simple | 3.168 |
3.168 | 1.000x | same |
| dynamic_dump_b1_t8_prev4 | 1 | 8 | 16 | 1 | 64 | 128 | FP32 | FP32
dt/D, int64 index | softplus, dst slots, algorithm=simple | 3.568 |
3.568 | 1.000x | same |
| dynamic_dump_b1_t8_prev8 | 1 | 8 | 16 | 1 | 64 | 128 | FP32 | FP32
dt/D, int64 index | softplus, dst slots, algorithm=simple | 3.568 |
3.568 | 1.000x | same |
| granite_ngram_t6_c4_legacy_adapted_graph_b1 | 1 | 6 | 64 | 1 | 64 |
128 | BF16 | FP32 dt/D, int64 index | softplus, state cache, no state
write, algorithm=vertical | 3.760 | 3.768 | 0.998x | same |
| granite_ngram_t6_c4_legacy_adapted_graph_b2 | 2 | 6 | 64 | 1 | 64 |
128 | BF16 | FP32 dt/D, int64 index | softplus, state cache, no state
write, algorithm=vertical | 4.752 | 4.752 | 1.000x | same |
| granite_ngram_t6_c4_legacy_adapted_graph_b3 | 3 | 6 | 64 | 1 | 64 |
128 | BF16 | FP32 dt/D, int64 index | softplus, state cache, no state
write, algorithm=vertical | 5.984 | 6.000 | 0.997x | same |
| granite_ngram_t6_c4_legacy_adapted_graph_b4 | 4 | 6 | 64 | 1 | 64 |
128 | BF16 | FP32 dt/D, int64 index | softplus, state cache, no state
write, algorithm=vertical | 6.656 | 6.656 | 1.000x | same |
| granite_ngram_t6_c4_sglang_raw_b1 | 1 | 6 | 64 | 1 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus, state cache, no state write | 3.960 |
3.952 | 1.002x | same |
| granite_ngram_t6_c4_sglang_raw_b2 | 2 | 6 | 64 | 1 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus, state cache, no state write | 4.992 |
4.976 | 1.003x | same |
| granite_ngram_t6_c4_sglang_raw_b3 | 3 | 6 | 64 | 1 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus, state cache, no state write | 6.144 |
6.144 | 1.000x | same |
| granite_ngram_t6_c4_sglang_raw_b4 | 4 | 6 | 64 | 1 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus, state cache, no state write | 6.944 |
6.944 | 1.000x | same |
| fitest_stp_ratio1 | 32 | 1 | 16 | 16 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 7.816 | 7.800 | 1.002x | same |
| fitest_stp_ratio8 | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 37.632 | 37.616 | 1.000x | same |
| fitest_stp_ratio8_sat | 128 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32
dt/D, int64 index | - | 78.544 | 78.584 | 0.999x | same |
| fitest_stp_ratio16 | 32 | 1 | 128 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 38.872 | 38.864 | 1.000x | same |
| fitest_stp_persistent | 257 | 1 | 128 | 8 | 128 | 128 | BF16 | FP32
dt/D, int64 index | - | 313.255 | 312.303 | 1.003x | new |
| fitest_stp_fp32 | 64 | 1 | 64 | 8 | 128 | 128 | FP32 | FP32 dt/D,
int64 index | - | 75.992 | 76.016 | 1.000x | same |
| fitest_mtp_short1 | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 37.688 | 37.680 | 1.000x | same |
| fitest_mtp_short2 | 64 | 2 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 39.544 | 39.560 | 1.000x | same |
| fitest_mtp_cache | 1 | 6 | 64 | 8 | 64 | 128 | BF16 | FP32 dt/D, int64
index | softplus, state cache, no state write, algorithm=vertical |
3.792 | 3.792 | 1.000x | same |
| fitest_mtp_horizontal | 32 | 6 | 64 | 8 | 64 | 128 | BF16 | FP32 dt/D,
int64 index | softplus, state cache, no state write,
algorithm=horizontal | 39.792 | 39.784 | 1.000x | same |
| fitest_dynamic0 | 1 | 1 | 16 | 1 | 64 | 128 | FP32 | FP32 dt/D, int64
index | softplus, dst slots, algorithm=simple | 2.800 | 2.784 | 1.006x |
same |
| fitest_dynamic0_b8 | 8 | 2 | 16 | 1 | 64 | 128 | FP32 | FP32 dt/D,
int64 index | softplus, dst slots, algorithm=simple | 4.176 | 4.160 |
1.004x | same |
| fitest_dynamic1 | 1 | 4 | 16 | 1 | 64 | 128 | FP32 | FP32 dt/D, int64
index | softplus, dst slots, algorithm=simple | 3.168 | 3.168 | 1.000x |
same |
| fitest_dynamic3 | 1 | 8 | 16 | 1 | 64 | 128 | FP32 | FP32 dt/D, int64
index | softplus, dst slots, algorithm=simple | 3.568 | 3.568 | 1.000x |
same |
| fitest_dynamic7 | 1 | 8 | 16 | 1 | 64 | 128 | FP32 | FP32 dt/D, int64
index | softplus, dst slots, algorithm=simple | 3.568 | 3.568 | 1.000x |
same |
| sweep_bfloat16_auto_b1 | 1 | 6 | 64 | 8 | 64 | 128 | BF16 | FP32 dt/D,
int64 index | softplus, state cache, no state write | 3.777 | 3.784 |
0.998x | same |
| dynamic_dump_b8_t2_prev1 | 8 | 2 | 16 | 1 | 64 | 128 | FP32 | FP32
dt/D, int64 index | softplus, dst slots, algorithm=simple | 4.176 |
4.160 | 1.004x | same |
| nemotron_h_tp1_hd64_sglang_raw_b1 | 1 | 1 | 128 | 8 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 3.128 | 3.136 | 0.997x | same |
| nemotron_h_tp1_hd64_canonical_b1 | 1 | 1 | 128 | 8 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 3.120 | 3.120 | 1.000x | same |
| nemotron_h_tp1_hd64_sglang_raw_b2 | 2 | 1 | 128 | 8 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 3.664 | 3.664 | 1.000x | same |
| nemotron_h_tp1_hd64_canonical_b2 | 2 | 1 | 128 | 8 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 3.672 | 3.672 | 1.000x | same |
| nemotron_h_tp1_hd64_sglang_raw_b4 | 4 | 1 | 128 | 8 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 4.896 | 4.896 | 1.000x | same |
| nemotron_h_tp1_hd64_canonical_b4 | 4 | 1 | 128 | 8 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 4.952 | 4.960 | 0.998x | same |
| nemotron_h_tp1_hd64_sglang_raw_b8 | 8 | 1 | 128 | 8 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 7.088 | 7.112 | 0.997x | same |
| nemotron_h_tp1_hd64_canonical_b8 | 8 | 1 | 128 | 8 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 6.992 | 6.992 | 1.000x | same |
| nemotron_h_tp1_hd64_sglang_raw_b16 | 16 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 10.312 | 10.320 | 0.999x |
same |
| nemotron_h_tp1_hd64_canonical_b16 | 16 | 1 | 128 | 8 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 10.544 | 10.528 | 1.002x | same |
| nemotron_h_tp1_hd64_sglang_raw_b32 | 32 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 19.072 | 19.080 | 1.000x |
same |
| nemotron_h_tp1_hd64_canonical_b32 | 32 | 1 | 128 | 8 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 19.048 | 19.056 | 1.000x | same |
| nemotron_h_tp1_hd64_sglang_raw_b64 | 64 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 39.256 | 39.240 | 1.000x |
same |
| nemotron_h_tp1_hd64_canonical_b64 | 64 | 1 | 128 | 8 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 39.240 | 39.256 | 1.000x | same |
| nemotron_h_tp1_hd64_sglang_raw_b128 | 128 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 78.520 | 78.496 | 1.000x |
same |
| nemotron_h_tp1_hd64_canonical_b128 | 128 | 1 | 128 | 8 | 64 | 128 |
BF16 | FP32 dt/D, int64 index | softplus | 78.616 | 78.608 | 1.000x |
same |
| nemotron_h_tp1_hd64_sglang_raw_b256 | 256 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 156.232 | 156.224 | 1.000x |
same |
| nemotron_h_tp1_hd64_canonical_b256 | 256 | 1 | 128 | 8 | 64 | 128 |
BF16 | FP32 dt/D, int64 index | softplus | 156.536 | 156.536 | 1.000x |
same |
| nemotron_h_tp1_hd64_sglang_raw_b6 | 6 | 1 | 128 | 8 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 6.064 | 6.064 | 1.000x | same |
| nemotron_h_tp1_hd64_sglang_raw_b12 | 12 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 8.816 | 8.816 | 1.000x | same
|
| nemotron_h_tp1_hd64_sglang_raw_b20 | 20 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 12.664 | 12.664 | 1.000x |
same |
| nemotron_h_tp1_hd64_sglang_raw_b24 | 24 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 14.800 | 14.800 | 1.000x |
same |
| nemotron_h_tp1_hd64_sglang_raw_b48 | 48 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 29.112 | 29.120 | 1.000x |
same |
| nemotron_h_tp1_hd64_fp32_sglang_raw_b1 | 1 | 1 | 128 | 8 | 64 | 128 |
FP32 | BF16 dt/D, int32 index | softplus | 3.704 | 3.704 | 1.000x | same
|
| nemotron_h_tp1_hd64_fp32_canonical_b1 | 1 | 1 | 128 | 8 | 64 | 128 |
FP32 | FP32 dt/D, int64 index | softplus | 3.448 | 3.456 | 0.998x | same
|
| nemotron_h_tp1_hd64_fp32_sglang_raw_b8 | 8 | 1 | 128 | 8 | 64 | 128 |
FP32 | BF16 dt/D, int32 index | softplus | 10.864 | 10.864 | 1.000x |
same |
| nemotron_h_tp1_hd64_fp32_canonical_b8 | 8 | 1 | 128 | 8 | 64 | 128 |
FP32 | FP32 dt/D, int64 index | softplus | 10.880 | 10.864 | 1.001x |
same |
| nemotron_h_tp1_hd64_fp32_sglang_raw_b64 | 64 | 1 | 128 | 8 | 64 | 128
| FP32 | BF16 dt/D, int32 index | softplus | 75.880 | 75.880 | 1.000x |
same |
| nemotron_h_tp1_hd64_fp32_canonical_b64 | 64 | 1 | 128 | 8 | 64 | 128 |
FP32 | FP32 dt/D, int64 index | softplus | 76.096 | 76.096 | 1.000x |
same |
| nemotron_h_tp1_hd64_fp32_sglang_raw_b256 | 256 | 1 | 128 | 8 | 64 |
128 | FP32 | BF16 dt/D, int32 index | softplus | 308.663 | 308.671 |
1.000x | same |
| nemotron_h_tp1_hd64_fp32_canonical_b256 | 256 | 1 | 128 | 8 | 64 | 128
| FP32 | FP32 dt/D, int64 index | softplus | 308.047 | 308.032 | 1.000x
| same |
| nemotron_h_tp1_hd64_fp32_sglang_raw_b2 | 2 | 1 | 128 | 8 | 64 | 128 |
FP32 | BF16 dt/D, int32 index | softplus | 4.712 | 4.704 | 1.002x | same
|
| nemotron_h_tp1_hd64_fp32_sglang_raw_b4 | 4 | 1 | 128 | 8 | 64 | 128 |
FP32 | BF16 dt/D, int32 index | softplus | 6.896 | 6.880 | 1.002x | same
|
| nemotron_h_tp1_hd64_fp32_sglang_raw_b16 | 16 | 1 | 128 | 8 | 64 | 128
| FP32 | BF16 dt/D, int32 index | softplus | 18.280 | 18.272 | 1.000x |
same |
| nemotron_h_tp1_hd64_fp32_sglang_raw_b32 | 32 | 1 | 128 | 8 | 64 | 128
| FP32 | BF16 dt/D, int32 index | softplus | 37.496 | 37.536 | 0.999x |
same |
| nemotron_h_tp2_hd64_sglang_raw_b1 | 1 | 1 | 64 | 4 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 2.928 | 2.936 | 0.997x | same |
| nemotron_h_tp2_hd64_canonical_b1 | 1 | 1 | 64 | 4 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 2.912 | 2.912 | 1.000x | same |
| nemotron_h_tp2_hd64_sglang_raw_b64 | 64 | 1 | 64 | 4 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 19.136 | 19.136 | 1.000x | same |
| nemotron_h_tp2_hd64_canonical_b64 | 64 | 1 | 64 | 4 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 19.032 | 19.040 | 1.000x | same |
| nemotron_h_tp2_hd64_sglang_raw_b256 | 256 | 1 | 64 | 4 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 78.448 | 78.432 | 1.000x |
same |
| nemotron_h_tp2_hd64_canonical_b256 | 256 | 1 | 64 | 4 | 64 | 128 |
BF16 | FP32 dt/D, int64 index | softplus | 78.288 | 78.304 | 1.000x |
same |
| nemotron_h_tp2_hd64_sglang_raw_b2 | 2 | 1 | 64 | 4 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 3.152 | 3.152 | 1.000x | same |
| nemotron_h_tp2_hd64_sglang_raw_b4 | 4 | 1 | 64 | 4 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 3.632 | 3.631 | 1.000x | same |
| nemotron_h_tp2_hd64_sglang_raw_b8 | 8 | 1 | 64 | 4 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 4.912 | 4.912 | 1.000x | same |
| nemotron_h_tp2_hd64_sglang_raw_b16 | 16 | 1 | 64 | 4 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 7.040 | 7.024 | 1.002x | same |
| nemotron_h_tp2_hd64_sglang_raw_b32 | 32 | 1 | 64 | 4 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 10.369 | 10.384 | 0.999x | same |
| nemotron_h_tp2_hd64_sglang_raw_b128 | 128 | 1 | 64 | 4 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 39.112 | 39.104 | 1.000x |
same |
| nemotron_h_tp4_hd64_sglang_raw_b1 | 1 | 1 | 32 | 2 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 2.688 | 2.680 | 1.003x | same |
| nemotron_h_tp4_hd64_canonical_b1 | 1 | 1 | 32 | 2 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 2.864 | 2.864 | 1.000x | same |
| nemotron_h_tp4_hd64_sglang_raw_b64 | 64 | 1 | 32 | 2 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 10.416 | 10.408 | 1.001x | same |
| nemotron_h_tp4_hd64_canonical_b64 | 64 | 1 | 32 | 2 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 10.464 | 10.448 | 1.002x | same |
| nemotron_h_tp4_hd64_sglang_raw_b256 | 256 | 1 | 32 | 2 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 39.152 | 39.128 | 1.001x |
same |
| nemotron_h_tp4_hd64_canonical_b256 | 256 | 1 | 32 | 2 | 64 | 128 |
BF16 | FP32 dt/D, int64 index | softplus | 39.248 | 39.264 | 1.000x |
same |
| nemotron_h_tp4_hd64_sglang_raw_b4 | 4 | 1 | 32 | 2 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 3.136 | 3.136 | 1.000x | same |
| nemotron_h_tp4_hd64_sglang_raw_b8 | 8 | 1 | 32 | 2 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 3.632 | 3.632 | 1.000x | same |
| nemotron_h_tp4_hd64_sglang_raw_b16 | 16 | 1 | 32 | 2 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 4.880 | 4.888 | 0.998x | same |
| nemotron_h_tp4_hd64_sglang_raw_b32 | 32 | 1 | 32 | 2 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 7.040 | 7.056 | 0.998x | same |
| nemotron_h_tp4_hd64_sglang_raw_b128 | 128 | 1 | 32 | 2 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 19.120 | 19.136 | 0.999x |
same |
| granite_h_small_hd64_sglang_raw_b1 | 1 | 1 | 128 | 1 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 3.088 | 3.088 | 1.000x | same |
| granite_h_small_hd64_canonical_b1 | 1 | 1 | 128 | 1 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 3.184 | 3.200 | 0.995x | same |
| granite_h_small_hd64_sglang_raw_b8 | 8 | 1 | 128 | 1 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 6.960 | 6.968 | 0.999x | same |
| granite_h_small_hd64_canonical_b8 | 8 | 1 | 128 | 1 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 6.976 | 6.976 | 1.000x | same |
| granite_h_small_hd64_sglang_raw_b64 | 64 | 1 | 128 | 1 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 39.024 | 39.040 | 1.000x |
same |
| granite_h_small_hd64_canonical_b64 | 64 | 1 | 128 | 1 | 64 | 128 |
BF16 | FP32 dt/D, int64 index | softplus | 39.184 | 39.208 | 0.999x |
same |
| granite_h_small_hd64_sglang_raw_b256 | 256 | 1 | 128 | 1 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 156.096 | 156.087 | 1.000x |
same |
| granite_h_small_hd64_canonical_b256 | 256 | 1 | 128 | 1 | 64 | 128 |
BF16 | FP32 dt/D, int64 index | softplus | 156.096 | 156.136 | 1.000x |
same |
| granite_h_tiny_hd64_sglang_raw_b1 | 1 | 1 | 48 | 1 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 2.800 | 2.800 | 1.000x | same |
| granite_h_tiny_hd64_canonical_b1 | 1 | 1 | 48 | 1 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 2.848 | 2.848 | 1.000x | same |
| granite_h_tiny_hd64_sglang_raw_b64 | 64 | 1 | 48 | 1 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 14.768 | 14.768 | 1.000x | same |
| granite_h_tiny_hd64_canonical_b64 | 64 | 1 | 48 | 1 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 14.736 | 14.720 | 1.001x | same |
| fitest_stp_hd64_rows_bf16 | 4 | 1 | 128 | 8 | 64 | 128 | BF16 | FP32
dt/D, int64 index | - | 4.928 | 4.928 | 1.000x | same |
| fitest_stp_hd64_paired_rows | 64 | 1 | 128 | 8 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | - | 39.152 | 39.128 | 1.001x | same |
| fitest_stp_hd64_paired_rows_b320 | 320 | 1 | 128 | 8 | 64 | 128 | BF16
| FP32 dt/D, int64 index | - | 195.248 | 194.904 | 1.002x | new |
| fitest_stp_hd64_fp32 | 64 | 1 | 128 | 8 | 64 | 128 | FP32 | FP32 dt/D,
int64 index | - | 76.000 | 75.976 | 1.000x | same |
| fitest_stp_hd64_odd_pairs | 8 | 1 | 24 | 8 | 64 | 128 | BF16 | FP32
dt/D, int64 index | - | 3.488 | 3.488 | 1.000x | same |
| fitest_stp_hd64_raw_rows | 2 | 1 | 128 | 8 | 64 | 128 | BF16 | BF16
dt/D, int32 index | softplus | 3.664 | 3.664 | 1.000x | same |
| fitest_stp_hd64_raw_paired | 64 | 1 | 128 | 8 | 64 | 128 | BF16 | BF16
dt/D, int32 index | softplus | 39.112 | 39.128 | 1.000x | same |
| fitest_stp_hd64_raw_fp32 | 8 | 1 | 128 | 8 | 64 | 128 | FP32 | BF16
dt/D, int32 index | softplus | 10.864 | 10.864 | 1.000x | same |
| fitest_stp_hd64_raw_paired_four_cta | 16 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 10.320 | 10.304 | 1.002x |
same |

*NVIDIA B200 (sm_100a, 148 SMs), CUDA 13.4, driver 580.82.07: the two
changed shapes on 12 B200 GPUs of three nodes (2, 8 and 2 GPUs), two
separate 9-round interleaved sessions per GPU. Times are each device's
medians over 9 rounds (us). Speedup = main / this PR. When the state
pool and output buffer were moved across 44 placements, the pooled
median also favored this PR on every device. Outputs and states are
bitwise identical to main's on every GPU.*

| node | device | case | main (us), run 1 / run 2 | this PR (us), run 1
/ run 2 | speedup, run 1 / run 2 |
|---|---:|---|---:|---:|---:|
| node A | 1 | fitest_stp_persistent | 312.224 / 312.192 | 310.816 /
310.848 | 1.0045x / 1.0043x |
| node A | 2 | fitest_stp_persistent | 312.128 / 312.144 | 310.688 /
310.800 | 1.0046x / 1.0043x |
| node B | 3 | fitest_stp_persistent | 312.126 / 312.159 | 310.687 /
310.703 | 1.0046x / 1.0047x |
| node B | 4 | fitest_stp_persistent | 312.094 / 312.111 | 310.735 /
310.815 | 1.0044x / 1.0042x |
| node B | 5 | fitest_stp_persistent | 312.126 / 312.158 | 310.798 /
310.798 | 1.0043x / 1.0044x |
| node B | 6 | fitest_stp_persistent | 312.207 / 312.223 | 310.751 /
310.719 | 1.0047x / 1.0048x |
| node B | 7 | fitest_stp_persistent | 312.175 / 312.143 | 310.750 /
310.751 | 1.0046x / 1.0045x |
| node B | 8 | fitest_stp_persistent | 312.142 / 312.127 | 310.719 /
310.655 | 1.0046x / 1.0047x |
| node B | 9 | fitest_stp_persistent | 312.191 / 312.191 | 310.831 /
310.752 | 1.0044x / 1.0046x |
| node B | 10 | fitest_stp_persistent | 312.159 / 312.175 | 310.671 /
310.719 | 1.0048x / 1.0047x |
| node C | 11 | fitest_stp_persistent | 313.471 / 313.472 | 312.192 /
312.224 | 1.0041x / 1.0040x |
| node C | 12 | fitest_stp_persistent | 313.374 / 313.422 | 312.126 /
312.142 | 1.0040x / 1.0041x |
| node A | 1 | fitest_stp_hd64_paired_rows_b320 | 194.513 / 194.496 |
193.984 / 194.048 | 1.0027x / 1.0023x |
| node A | 2 | fitest_stp_hd64_paired_rows_b320 | 194.512 / 194.497 |
194.000 / 194.096 | 1.0026x / 1.0021x |
| node B | 3 | fitest_stp_hd64_paired_rows_b320 | 194.495 / 194.495 |
193.952 / 193.984 | 1.0028x / 1.0026x |
| node B | 4 | fitest_stp_hd64_paired_rows_b320 | 194.559 / 194.480 |
193.936 / 193.968 | 1.0032x / 1.0026x |
| node B | 5 | fitest_stp_hd64_paired_rows_b320 | 194.479 / 194.527 |
194.015 / 193.951 | 1.0024x / 1.0030x |
| node B | 6 | fitest_stp_hd64_paired_rows_b320 | 194.495 / 194.495 |
194.047 / 194.047 | 1.0023x / 1.0023x |
| node B | 7 | fitest_stp_hd64_paired_rows_b320 | 194.495 / 194.496 |
193.983 / 193.984 | 1.0026x / 1.0026x |
| node B | 8 | fitest_stp_hd64_paired_rows_b320 | 194.495 / 194.543 |
193.999 / 193.983 | 1.0026x / 1.0029x |
| node B | 9 | fitest_stp_hd64_paired_rows_b320 | 194.480 / 194.480 |
194.031 / 194.016 | 1.0023x / 1.0024x |
| node B | 10 | fitest_stp_hd64_paired_rows_b320 | 194.432 / 194.495 |
193.984 / 194.111 | 1.0023x / 1.0020x |
| node C | 11 | fitest_stp_hd64_paired_rows_b320 | 195.232 / 195.217 |
194.912 / 194.816 | 1.0016x / 1.0021x |
| node C | 12 | fitest_stp_hd64_paired_rows_b320 | 195.231 / 195.199 |
194.847 / 194.799 | 1.0020x / 1.0021x |

*NVIDIA GB300 (sm_103a, 152 SMs), driver 580.159.03, CUDA 13.4; PyTorch
2.14.1+cu130; programs compiled with nvcc 13.4. Timer: CUPTI kernel time
with a cold L2; times are medians over 2 runs x 9 interleaved rounds
(us); speedup = main / this PR; the program column says whether this PR
routes the shape to a different program (`new`) or keeps main's program,
possibly under its new name (`same`).*

| case | batch | tokens | heads | groups | head dim | state dim | state
| inputs | options | main (us) | this PR (us) | speedup | program |
|---|---:|---:|---:|---:|---:|---:|---|---|---|---:|---:|---:|---|
| sample_stp_bf16 | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 37.376 | 37.367 | 1.000x | same |
| sample_stp_state_fp32 | 64 | 1 | 64 | 8 | 128 | 128 | FP32 | FP32
dt/D, int64 index | - | 73.896 | 73.888 | 1.000x | same |
| sample_stp_z | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D, int64
index | z gate | 37.328 | 37.376 | 0.999x | same |
| sample_stp_softplus | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | softplus | 37.376 | 37.368 | 1.000x | same |
| sample_stp_z_softplus | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32
dt/D, int64 index | z gate, softplus | 37.384 | 37.344 | 1.001x | same |
| sample_stp_ratio1 | 32 | 1 | 16 | 16 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 7.392 | 7.392 | 1.000x | same |
| sample_stp_ratio16 | 32 | 1 | 128 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 37.328 | 37.328 | 1.000x | same |
| sample_stp_b256 | 256 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 151.432 | 151.456 | 1.000x | same |
| sample_stp_b128 | 128 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 75.600 | 75.624 | 1.000x | same |
| sample_mtp1 | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D, int64
index | - | 36.280 | 36.304 | 0.999x | same |
| sample_mtp2 | 64 | 2 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D, int64
index | - | 38.056 | 38.072 | 1.000x | same |
| sweep_bfloat16_vertical_b1 | 1 | 6 | 64 | 8 | 64 | 128 | BF16 | FP32
dt/D, int64 index | softplus, state cache, no state write,
algorithm=vertical | 3.584 | 3.584 | 1.000x | same |
| sweep_bfloat16_horizontal_b1024 | 1024 | 6 | 64 | 8 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus, state cache, no state write,
algorithm=horizontal | 1115.984 | 1116.064 | 1.000x | same |
| dynamic_dump_b1_t1_prev0 | 1 | 1 | 16 | 1 | 64 | 128 | FP32 | FP32
dt/D, int64 index | softplus, dst slots, algorithm=simple | 2.728 |
2.720 | 1.003x | same |
| dynamic_dump_b1_t2_prev1 | 1 | 2 | 16 | 1 | 64 | 128 | FP32 | FP32
dt/D, int64 index | softplus, dst slots, algorithm=simple | 2.848 |
2.832 | 1.006x | same |
| dynamic_dump_b1_t4_prev2 | 1 | 4 | 16 | 1 | 64 | 128 | FP32 | FP32
dt/D, int64 index | softplus, dst slots, algorithm=simple | 3.072 |
3.072 | 1.000x | same |
| dynamic_dump_b1_t8_prev4 | 1 | 8 | 16 | 1 | 64 | 128 | FP32 | FP32
dt/D, int64 index | softplus, dst slots, algorithm=simple | 3.424 |
3.424 | 1.000x | same |
| dynamic_dump_b1_t8_prev8 | 1 | 8 | 16 | 1 | 64 | 128 | FP32 | FP32
dt/D, int64 index | softplus, dst slots, algorithm=simple | 3.456 |
3.440 | 1.005x | same |
| granite_ngram_t6_c4_legacy_adapted_graph_b1 | 1 | 6 | 64 | 1 | 64 |
128 | BF16 | FP32 dt/D, int64 index | softplus, state cache, no state
write, algorithm=vertical | 3.568 | 3.552 | 1.005x | same |
| granite_ngram_t6_c4_legacy_adapted_graph_b2 | 2 | 6 | 64 | 1 | 64 |
128 | BF16 | FP32 dt/D, int64 index | softplus, state cache, no state
write, algorithm=vertical | 4.624 | 4.624 | 1.000x | same |
| granite_ngram_t6_c4_legacy_adapted_graph_b3 | 3 | 6 | 64 | 1 | 64 |
128 | BF16 | FP32 dt/D, int64 index | softplus, state cache, no state
write, algorithm=vertical | 5.440 | 5.448 | 0.999x | same |
| granite_ngram_t6_c4_legacy_adapted_graph_b4 | 4 | 6 | 64 | 1 | 64 |
128 | BF16 | FP32 dt/D, int64 index | softplus, state cache, no state
write, algorithm=vertical | 6.456 | 6.448 | 1.001x | same |
| granite_ngram_t6_c4_sglang_raw_b1 | 1 | 6 | 64 | 1 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus, state cache, no state write | 3.824 |
3.824 | 1.000x | same |
| granite_ngram_t6_c4_sglang_raw_b2 | 2 | 6 | 64 | 1 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus, state cache, no state write | 4.776 |
4.776 | 1.000x | same |
| granite_ngram_t6_c4_sglang_raw_b3 | 3 | 6 | 64 | 1 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus, state cache, no state write | 5.688 |
5.680 | 1.001x | same |
| granite_ngram_t6_c4_sglang_raw_b4 | 4 | 6 | 64 | 1 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus, state cache, no state write | 6.656 |
6.656 | 1.000x | same |
| fitest_stp_ratio1 | 32 | 1 | 16 | 16 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 7.392 | 7.392 | 1.000x | same |
| fitest_stp_ratio8 | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 37.368 | 37.360 | 1.000x | same |
| fitest_stp_ratio8_sat | 128 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32
dt/D, int64 index | - | 75.552 | 75.632 | 0.999x | same |
| fitest_stp_ratio16 | 32 | 1 | 128 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 37.248 | 37.264 | 1.000x | same |
| fitest_stp_persistent | 257 | 1 | 128 | 8 | 128 | 128 | BF16 | FP32
dt/D, int64 index | - | 304.592 | 304.543 | 1.000x | same |
| fitest_stp_fp32 | 64 | 1 | 64 | 8 | 128 | 128 | FP32 | FP32 dt/D,
int64 index | - | 73.976 | 73.968 | 1.000x | same |
| fitest_mtp_short1 | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 36.328 | 36.312 | 1.000x | same |
| fitest_mtp_short2 | 64 | 2 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 38.128 | 38.112 | 1.000x | same |
| fitest_mtp_cache | 1 | 6 | 64 | 8 | 64 | 128 | BF16 | FP32 dt/D, int64
index | softplus, state cache, no state write, algorithm=vertical |
3.584 | 3.592 | 0.998x | same |
| fitest_mtp_horizontal | 32 | 6 | 64 | 8 | 64 | 128 | BF16 | FP32 dt/D,
int64 index | softplus, state cache, no state write,
algorithm=horizontal | 36.744 | 36.768 | 0.999x | same |
| fitest_dynamic0 | 1 | 1 | 16 | 1 | 64 | 128 | FP32 | FP32 dt/D, int64
index | softplus, dst slots, algorithm=simple | 2.736 | 2.720 | 1.006x |
same |
| fitest_dynamic0_b8 | 8 | 2 | 16 | 1 | 64 | 128 | FP32 | FP32 dt/D,
int64 index | softplus, dst slots, algorithm=simple | 3.824 | 3.824 |
1.000x | same |
| fitest_dynamic1 | 1 | 4 | 16 | 1 | 64 | 128 | FP32 | FP32 dt/D, int64
index | softplus, dst slots, algorithm=simple | 3.072 | 3.072 | 1.000x |
same |
| fitest_dynamic3 | 1 | 8 | 16 | 1 | 64 | 128 | FP32 | FP32 dt/D, int64
index | softplus, dst slots, algorithm=simple | 3.440 | 3.424 | 1.005x |
same |
| fitest_dynamic7 | 1 | 8 | 16 | 1 | 64 | 128 | FP32 | FP32 dt/D, int64
index | softplus, dst slots, algorithm=simple | 3.456 | 3.440 | 1.005x |
same |
| sweep_bfloat16_auto_b1 | 1 | 6 | 64 | 8 | 64 | 128 | BF16 | FP32 dt/D,
int64 index | softplus, state cache, no state write | 3.584 | 3.600 |
0.996x | same |
| dynamic_dump_b8_t2_prev1 | 8 | 2 | 16 | 1 | 64 | 128 | FP32 | FP32
dt/D, int64 index | softplus, dst slots, algorithm=simple | 3.824 |
3.824 | 1.000x | same |
| nemotron_h_tp1_hd64_sglang_raw_b1 | 1 | 1 | 128 | 8 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 2.976 | 2.992 | 0.995x | same |
| nemotron_h_tp1_hd64_canonical_b1 | 1 | 1 | 128 | 8 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 3.136 | 3.120 | 1.005x | same |
| nemotron_h_tp1_hd64_sglang_raw_b2 | 2 | 1 | 128 | 8 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 3.472 | 3.472 | 1.000x | same |
| nemotron_h_tp1_hd64_canonical_b2 | 2 | 1 | 128 | 8 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 3.504 | 3.504 | 1.000x | same |
| nemotron_h_tp1_hd64_sglang_raw_b4 | 4 | 1 | 128 | 8 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 4.704 | 4.704 | 1.000x | same |
| nemotron_h_tp1_hd64_canonical_b4 | 4 | 1 | 128 | 8 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 4.736 | 4.736 | 1.000x | same |
| nemotron_h_tp1_hd64_sglang_raw_b8 | 8 | 1 | 128 | 8 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 6.608 | 6.608 | 1.000x | same |
| nemotron_h_tp1_hd64_canonical_b8 | 8 | 1 | 128 | 8 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 6.592 | 6.576 | 1.002x | same |
| nemotron_h_tp1_hd64_sglang_raw_b16 | 16 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 9.904 | 9.904 | 1.000x | same
|
| nemotron_h_tp1_hd64_canonical_b16 | 16 | 1 | 128 | 8 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 10.016 | 10.000 | 1.002x | same |
| nemotron_h_tp1_hd64_sglang_raw_b32 | 32 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 18.408 | 18.400 | 1.000x |
same |
| nemotron_h_tp1_hd64_canonical_b32 | 32 | 1 | 128 | 8 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 18.128 | 18.120 | 1.000x | same |
| nemotron_h_tp1_hd64_sglang_raw_b64 | 64 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 37.512 | 37.520 | 1.000x |
same |
| nemotron_h_tp1_hd64_canonical_b64 | 64 | 1 | 128 | 8 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 37.512 | 37.512 | 1.000x | same |
| nemotron_h_tp1_hd64_sglang_raw_b128 | 128 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 75.696 | 75.704 | 1.000x |
same |
| nemotron_h_tp1_hd64_canonical_b128 | 128 | 1 | 128 | 8 | 64 | 128 |
BF16 | FP32 dt/D, int64 index | softplus | 75.832 | 75.824 | 1.000x |
same |
| nemotron_h_tp1_hd64_sglang_raw_b256 | 256 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 151.400 | 151.424 | 1.000x |
same |
| nemotron_h_tp1_hd64_canonical_b256 | 256 | 1 | 128 | 8 | 64 | 128 |
BF16 | FP32 dt/D, int64 index | softplus | 151.280 | 151.280 | 1.000x |
same |
| nemotron_h_tp1_hd64_sglang_raw_b6 | 6 | 1 | 128 | 8 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 5.792 | 5.792 | 1.000x | same |
| nemotron_h_tp1_hd64_sglang_raw_b12 | 12 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 8.384 | 8.384 | 1.000x | same
|
| nemotron_h_tp1_hd64_sglang_raw_b20 | 20 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 12.048 | 12.048 | 1.000x |
same |
| nemotron_h_tp1_hd64_sglang_raw_b24 | 24 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 14.032 | 14.032 | 1.000x |
same |
| nemotron_h_tp1_hd64_sglang_raw_b48 | 48 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 27.672 | 27.656 | 1.001x |
same |
| nemotron_h_tp1_hd64_fp32_sglang_raw_b1 | 1 | 1 | 128 | 8 | 64 | 128 |
FP32 | BF16 dt/D, int32 index | softplus | 3.504 | 3.504 | 1.000x | same
|
| nemotron_h_tp1_hd64_fp32_canonical_b1 | 1 | 1 | 128 | 8 | 64 | 128 |
FP32 | FP32 dt/D, int64 index | softplus | 3.304 | 3.296 | 1.002x | same
|
| nemotron_h_tp1_hd64_fp32_sglang_raw_b8 | 8 | 1 | 128 | 8 | 64 | 128 |
FP32 | BF16 dt/D, int32 index | softplus | 10.208 | 10.208 | 1.000x |
same |
| nemotron_h_tp1_hd64_fp32_canonical_b8 | 8 | 1 | 128 | 8 | 64 | 128 |
FP32 | FP32 dt/D, int64 index | softplus | 10.336 | 10.336 | 1.000x |
same |
| nemotron_h_tp1_hd64_fp32_sglang_raw_b64 | 64 | 1 | 128 | 8 | 64 | 128
| FP32 | BF16 dt/D, int32 index | softplus | 73.520 | 73.528 | 1.000x |
same |
| nemotron_h_tp1_hd64_fp32_canonical_b64 | 64 | 1 | 128 | 8 | 64 | 128 |
FP32 | FP32 dt/D, int64 index | softplus | 73.448 | 73.488 | 0.999x |
same |
| nemotron_h_tp1_hd64_fp32_sglang_raw_b256 | 256 | 1 | 128 | 8 | 64 |
128 | FP32 | BF16 dt/D, int32 index | softplus | 299.984 | 300.000 |
1.000x | same |
| nemotron_h_tp1_hd64_fp32_canonical_b256 | 256 | 1 | 128 | 8 | 64 | 128
| FP32 | FP32 dt/D, int64 index | softplus | 299.648 | 299.744 | 1.000x
| same |
| nemotron_h_tp1_hd64_fp32_sglang_raw_b2 | 2 | 1 | 128 | 8 | 64 | 128 |
FP32 | BF16 dt/D, int32 index | softplus | 4.464 | 4.464 | 1.000x | same
|
| nemotron_h_tp1_hd64_fp32_sglang_raw_b4 | 4 | 1 | 128 | 8 | 64 | 128 |
FP32 | BF16 dt/D, int32 index | softplus | 6.520 | 6.528 | 0.999x | same
|
| nemotron_h_tp1_hd64_fp32_sglang_raw_b16 | 16 | 1 | 128 | 8 | 64 | 128
| FP32 | BF16 dt/D, int32 index | softplus | 17.184 | 17.200 | 0.999x |
same |
| nemotron_h_tp1_hd64_fp32_sglang_raw_b32 | 32 | 1 | 128 | 8 | 64 | 128
| FP32 | BF16 dt/D, int32 index | softplus | 35.800 | 35.776 | 1.001x |
same |
| nemotron_h_tp2_hd64_sglang_raw_b1 | 1 | 1 | 64 | 4 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 2.832 | 2.800 | 1.011x | same |
| nemotron_h_tp2_hd64_canonical_b1 | 1 | 1 | 64 | 4 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 2.696 | 2.704 | 0.997x | same |
| nemotron_h_tp2_hd64_sglang_raw_b64 | 64 | 1 | 64 | 4 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 18.384 | 18.400 | 0.999x | same |
| nemotron_h_tp2_hd64_canonical_b64 | 64 | 1 | 64 | 4 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 18.056 | 18.064 | 1.000x | same |
| nemotron_h_tp2_hd64_sglang_raw_b256 | 256 | 1 | 64 | 4 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 75.664 | 75.656 | 1.000x |
same |
| nemotron_h_tp2_hd64_canonical_b256 | 256 | 1 | 64 | 4 | 64 | 128 |
BF16 | FP32 dt/D, int64 index | softplus | 75.752 | 75.728 | 1.000x |
same |
| nemotron_h_tp2_hd64_sglang_raw_b2 | 2 | 1 | 64 | 4 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 3.056 | 3.048 | 1.003x | same |
| nemotron_h_tp2_hd64_sglang_raw_b4 | 4 | 1 | 64 | 4 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 3.456 | 3.456 | 1.000x | same |
| nemotron_h_tp2_hd64_sglang_raw_b8 | 8 | 1 | 64 | 4 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 4.728 | 4.728 | 1.000x | same |
| nemotron_h_tp2_hd64_sglang_raw_b16 | 16 | 1 | 64 | 4 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 6.608 | 6.608 | 1.000x | same |
| nemotron_h_tp2_hd64_sglang_raw_b32 | 32 | 1 | 64 | 4 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 9.904 | 9.904 | 1.000x | same |
| nemotron_h_tp2_hd64_sglang_raw_b128 | 128 | 1 | 64 | 4 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 37.488 | 37.464 | 1.001x |
same |
| nemotron_h_tp4_hd64_sglang_raw_b1 | 1 | 1 | 32 | 2 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 2.520 | 2.528 | 0.997x | same |
| nemotron_h_tp4_hd64_canonical_b1 | 1 | 1 | 32 | 2 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 2.704 | 2.704 | 1.000x | same |
| nemotron_h_tp4_hd64_sglang_raw_b64 | 64 | 1 | 32 | 2 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 9.944 | 9.952 | 0.999x | same |
| nemotron_h_tp4_hd64_canonical_b64 | 64 | 1 | 32 | 2 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 9.968 | 9.968 | 1.000x | same |
| nemotron_h_tp4_hd64_sglang_raw_b256 | 256 | 1 | 32 | 2 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 37.472 | 37.472 | 1.000x |
same |
| nemotron_h_tp4_hd64_canonical_b256 | 256 | 1 | 32 | 2 | 64 | 128 |
BF16 | FP32 dt/D, int64 index | softplus | 37.624 | 37.616 | 1.000x |
same |
| nemotron_h_tp4_hd64_sglang_raw_b4 | 4 | 1 | 32 | 2 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 3.024 | 3.024 | 1.000x | same |
| nemotron_h_tp4_hd64_sglang_raw_b8 | 8 | 1 | 32 | 2 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 3.488 | 3.488 | 1.000x | same |
| nemotron_h_tp4_hd64_sglang_raw_b16 | 16 | 1 | 32 | 2 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 4.640 | 4.640 | 1.000x | same |
| nemotron_h_tp4_hd64_sglang_raw_b32 | 32 | 1 | 32 | 2 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 6.688 | 6.688 | 1.000x | same |
| nemotron_h_tp4_hd64_sglang_raw_b128 | 128 | 1 | 32 | 2 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 18.320 | 18.320 | 1.000x |
same |
| granite_h_small_hd64_sglang_raw_b1 | 1 | 1 | 128 | 1 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 2.984 | 2.992 | 0.997x | same |
| granite_h_small_hd64_canonical_b1 | 1 | 1 | 128 | 1 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 3.024 | 3.024 | 1.000x | same |
| granite_h_small_hd64_sglang_raw_b8 | 8 | 1 | 128 | 1 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 6.448 | 6.448 | 1.000x | same |
| granite_h_small_hd64_canonical_b8 | 8 | 1 | 128 | 1 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 6.480 | 6.480 | 1.000x | same |
| granite_h_small_hd64_sglang_raw_b64 | 64 | 1 | 128 | 1 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 37.472 | 37.480 | 1.000x |
same |
| granite_h_small_hd64_canonical_b64 | 64 | 1 | 128 | 1 | 64 | 128 |
BF16 | FP32 dt/D, int64 index | softplus | 37.488 | 37.504 | 1.000x |
same |
| granite_h_small_hd64_sglang_raw_b256 | 256 | 1 | 128 | 1 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 151.304 | 151.312 | 1.000x |
same |
| granite_h_small_hd64_canonical_b256 | 256 | 1 | 128 | 1 | 64 | 128 |
BF16 | FP32 dt/D, int64 index | softplus | 151.344 | 151.336 | 1.000x |
same |
| granite_h_tiny_hd64_sglang_raw_b1 | 1 | 1 | 48 | 1 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 2.656 | 2.648 | 1.003x | same |
| granite_h_tiny_hd64_canonical_b1 | 1 | 1 | 48 | 1 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 2.720 | 2.712 | 1.003x | same |
| granite_h_tiny_hd64_sglang_raw_b64 | 64 | 1 | 48 | 1 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 14.216 | 14.224 | 0.999x | same |
| granite_h_tiny_hd64_canonical_b64 | 64 | 1 | 48 | 1 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 14.096 | 14.112 | 0.999x | same |
| fitest_stp_hd64_rows_bf16 | 4 | 1 | 128 | 8 | 64 | 128 | BF16 | FP32
dt/D, int64 index | - | 4.736 | 4.736 | 1.000x | same |
| fitest_stp_hd64_paired_rows | 64 | 1 | 128 | 8 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | - | 37.512 | 37.488 | 1.001x | same |
| fitest_stp_hd64_paired_rows_b320 | 320 | 1 | 128 | 8 | 64 | 128 | BF16
| FP32 dt/D, int64 index | - | 189.312 | 189.344 | 1.000x | same |
| fitest_stp_hd64_fp32 | 64 | 1 | 128 | 8 | 64 | 128 | FP32 | FP32 dt/D,
int64 index | - | 73.376 | 73.416 | 0.999x | same |
| fitest_stp_hd64_odd_pairs | 8 | 1 | 24 | 8 | 64 | 128 | BF16 | FP32
dt/D, int64 index | - | 3.296 | 3.296 | 1.000x | same |
| fitest_stp_hd64_raw_rows | 2 | 1 | 128 | 8 | 64 | 128 | BF16 | BF16
dt/D, int32 index | softplus | 3.568 | 3.568 | 1.000x | same |
| fitest_stp_hd64_raw_paired | 64 | 1 | 128 | 8 | 64 | 128 | BF16 | BF16
dt/D, int32 index | softplus | 37.520 | 37.520 | 1.000x | same |
| fitest_stp_hd64_raw_fp32 | 8 | 1 | 128 | 8 | 64 | 128 | FP32 | BF16
dt/D, int32 index | softplus | 10.208 | 10.208 | 1.000x | same |
| fitest_stp_hd64_raw_paired_four_cta | 16 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 9.920 | 9.904 | 1.002x | same
|

Cake has no other variants of this kernel beyond the dimensions above,
and it ships the kernel only on sm_100a and sm_103a; this PR changes
routes only on sm_100a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added support for additional selective state update kernel variants,
including architecture- and shape-specific L2 read-ahead selection.
* Expanded test coverage to check variant selection and compare output
and state results against existing implementations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [6926590](https://github.com/flashinfer-ai/flashinfer/commit/69265901d35f5e9023c9ece8600d119a5f3f09c6)

- **作者**: eigen
- **时间**: 2026-11-01T23:32:48Z
- **提交信息**: fix(cake_softmax): round the Blackwell softmax exponent once (#8236)

`flashinfer.sampling.softmax` on Blackwell takes FP32 input in a
row-major `[rows, vocab]` layout. It can fuse a scalar or per-row
temperature and can launch with PDL. This PR updates it from the
previous Cake version, #7867, which is the current main.

The PR makes three changes:

- **Single-rounded exponent.** Each term is now computed as 2^(x · s(m)
− c(m)) with one FFMA, where the shift c(m) = m · s(m) is rounded once.
Before, it was computed as 2^((x − m) · log2(e)), which rounds the
exponent twice. On the measured shape sets with fresh seeds, against a
float64 reference, the maximum relative error drops from 1.0044e-6 to
7.93e-7 on B200 and from 1.0118e-6 to 7.79e-7 on GB300.
- **Balanced chunk for 6-tile chunks.** The 8-CTA shared-tile and
persistent programs now take the balanced chunk for a 6-tile whole-tile
chunk with a cut of at least 1/10. They use the same wave and trip
bounds as the other chunk tile counts. Tile, balanced chunk and cut are
defined as in #7867. Before this PR, B200 (sm_100a) kept whole tiles for
this class at every row count. GB300 (sm_103a) used the balanced chunk
only up to 79 rows (shared-tile) and 92 rows (persistent).
- **Persistent kernel on GB300.** On GB300 only, an 8-CTA chunk of 5 or
6 tiles whose per-CTA share exceeds 5 tiles now keeps the persistent
kernel from 296 to 443 rows (4 to 6 rows per shared-tile cluster). This
rule does not change any B200 route.

On the 41 listed shapes, the launches are unchanged and the
single-rounded exponent has a small cost: geometric mean 0.986×
(0.964×–1.011×) on GB300 and 0.984× (0.959×–1.003×) on B200 (Table A).
Shapes whose launch changes get faster:

- **GB300:** the 23 measured shapes whose chunk or kernel changes run at
1.015×–1.080×, geometric mean 1.039× (Table B1).
- **B200:** the 81 measured shapes whose chunk changes run at
0.998×–1.056×, geometric mean 1.034× (Table B2). The one row under
1.000×, 497 × 88320 at 0.998×, is at parity. On that shape, the balanced
chunk measures 1.001× against the same single-rounded exponent with
whole tiles.

**Table A.** The 41 listed shapes, whose launches this PR leaves
unchanged: latency in µs (median, cold L2) for main (the previous Cake
version, #7867) and this PR on GB300 (sm_103a) and B200 (sm_100a), CUDA
13.4 (nvcc 13.4.2), PyTorch 2.14.1. Speedup is the median of paired
interleaved ratios, so it can differ slightly from the ratio of the
medians shown.

| rows × vocab | temperature | GB300 main µs | GB300 this PR µs | GB300
speedup | B200 main µs | B200 this PR µs | B200 speedup |
|---|---|---:|---:|---:|---:|---:|---:|
| 1 × 32000 | none | 2.27 | 2.30 | 0.986× | 2.40 | 2.43 | 0.987× |
| 1 × 64000 | none | 2.66 | 2.69 | 0.988× | 2.78 | 2.82 | 0.988× |
| 1 × 128000 | none | 3.09 | 3.10 | 1.000× | 3.26 | 3.30 | 0.990× |
| 1 × 256000 | none | 4.06 | 4.10 | 0.992× | 4.42 | 4.45 | 0.995× |
| 4 × 32000 | none | 2.51 | 2.54 | 0.987× | 2.66 | 2.70 | 0.985× |
| 4 × 64000 | none | 2.72 | 2.75 | 0.988× | 2.91 | 2.98 | 0.984× |
| 4 × 128000 | none | 3.23 | 3.28 | 0.985× | 3.49 | 3.55 | 0.982× |
| 4 × 256000 | none | 4.43 | 4.50 | 0.986× | 4.80 | 4.83 | 0.993× |
| 8 × 32000 | none | 2.62 | 2.69 | 0.976× | 2.72 | 2.82 | 0.969× |
| 8 × 64000 | none | 3.04 | 3.14 | 0.971× | 3.23 | 3.31 | 0.972× |
| 8 × 128000 | none | 4.03 | 4.10 | 0.984× | 4.30 | 4.40 | 0.978× |
| 8 × 256000 | none | 5.78 | 5.98 | 0.965× | 6.67 | 6.91 | 0.963× |
| 16 × 32000 | none | 2.82 | 2.91 | 0.967× | 3.01 | 3.14 | 0.965× |
| 16 × 64000 | none | 3.55 | 3.65 | 0.978× | 3.79 | 3.89 | 0.975× |
| 16 × 128000 | none | 5.18 | 5.31 | 0.976× | 5.70 | 5.79 | 0.984× |
| 16 × 256000 | none | 9.12 | 9.01 | 1.011× | 9.66 | 9.66 | 1.000× |
| 32 × 32000 | none | 3.38 | 3.49 | 0.964× | 3.52 | 3.63 | 0.973× |
| 32 × 64000 | none | 4.64 | 4.77 | 0.973× | 5.10 | 5.22 | 0.976× |
| 32 × 128000 | none | 7.28 | 7.52 | 0.968× | 7.89 | 8.06 | 0.978× |
| 32 × 256000 | none | 12.94 | 12.94 | 0.999× | 13.49 | 13.50 | 1.000× |
| 64 × 32000 | none | 4.50 | 4.59 | 0.979× | 4.69 | 4.78 | 0.980× |
| 64 × 64000 | none | 6.99 | 7.14 | 0.980× | 7.17 | 7.33 | 0.978× |
| 64 × 128000 | none | 11.57 | 11.58 | 1.000× | 11.97 | 12.08 | 0.991× |
| 64 × 256000 | none | 20.43 | 20.48 | 0.998× | 20.94 | 21.23 | 0.986× |
| 128 × 32000 | none | 6.82 | 7.06 | 0.966× | 7.10 | 7.30 | 0.973× |
| 128 × 64000 | none | 11.04 | 11.30 | 0.977× | 11.31 | 11.68 | 0.968× |
| 128 × 128000 | none | 18.08 | 18.10 | 0.998× | 18.74 | 18.75 | 0.997×
|
| 128 × 256000 | none | 35.94 | 35.94 | 1.001× | 36.40 | 36.48 | 0.997×
|
| 256 × 32000 | none | 10.70 | 11.09 | 0.966× | 10.88 | 11.33 | 0.959× |
| 256 × 64000 | none | 18.40 | 18.82 | 0.980× | 18.93 | 19.33 | 0.980× |
| 256 × 128000 | none | 33.38 | 33.44 | 0.998× | 35.89 | 35.78 | 1.003×
|
| 256 × 256000 | none | 74.38 | 74.42 | 0.999× | 76.50 | 76.70 | 0.997×
|
| 512 × 32000 | none | 17.65 | 17.98 | 0.979× | 18.21 | 18.75 | 0.971× |
| 512 × 64000 | none | 35.42 | 35.73 | 0.991× | 36.06 | 36.58 | 0.987× |
| 512 × 128000 | none | 73.12 | 73.22 | 0.999× | 76.74 | 76.58 | 1.003×
|
| 512 × 256000 | none | 149.14 | 148.56 | 1.004× | 152.03 | 151.86 |
1.001× |
| 1024 × 32000 | none | 33.95 | 34.53 | 0.983× | 35.04 | 35.60 | 0.984×
|
| 1024 × 64000 | none | 72.08 | 72.21 | 0.998× | 72.69 | 73.14 | 0.993×
|
| 1024 × 128000 | none | 147.22 | 146.99 | 1.002× | 151.21 | 151.06 |
1.001× |
| 1024 × 256000 | none | 294.27 | 293.58 | 1.002× | 300.58 | 300.43 |
1.001× |
| 64 × 32000 | scalar T, PDL | 4.48 | 4.58 | 0.979× | 4.70 | 4.80 |
0.980× |
| geometric mean | | | | 0.986× | | | 0.984× |

**Table B1.** GB300 (sm_103a), the 23 measured shapes whose launch
(chunk or kernel) changes: latency in µs (median, cold L2) for main (the
previous Cake version, #7867) and this PR, CUDA 13.4 (nvcc 13.4.2),
PyTorch 2.14.1. Speedup is the median of paired interleaved ratios, so
it can differ slightly from the ratio of the medians shown.

| rows × vocab | temperature | main µs | this PR µs | speedup |
|---|---|---:|---:|---:|
| 93 × 81928 | none | 12.14 | 11.71 | 1.038× |
| 120 × 81928 | none | 14.13 | 13.73 | 1.028× |
| 150 × 81928 | none | 16.62 | 16.08 | 1.034× |
| 180 × 81928 | none | 17.98 | 17.26 | 1.041× |
| 180 × 81928 | scalar T | 17.95 | 17.23 | 1.041× |
| 296 × 81928 | none | 29.25 | 28.05 | 1.043× |
| 330 × 81928 | none | 31.95 | 30.62 | 1.044× |
| 370 × 81928 | none | 35.42 | 34.14 | 1.038× |
| 370 × 81928 | scalar T | 35.41 | 34.30 | 1.033× |
| 93 × 84000 | none | 12.16 | 11.74 | 1.035× |
| 180 × 84000 | none | 17.87 | 17.22 | 1.037× |
| 296 × 84000 | none | 29.66 | 27.94 | 1.060× |
| 370 × 84000 | none | 36.05 | 34.50 | 1.044× |
| 100 × 88320 | none | 12.37 | 11.98 | 1.032× |
| 180 × 88320 | none | 18.00 | 17.39 | 1.035× |
| 300 × 88320 | none | 30.98 | 28.66 | 1.080× |
| 370 × 88320 | none | 37.52 | 35.57 | 1.056× |
| 180 × 81928 | scalar T, PDL | 17.97 | 17.26 | 1.041× |
| 370 × 81928 | scalar T, PDL | 35.42 | 34.14 | 1.038× |
| 443 × 81928 | none | 41.62 | 41.02 | 1.015× |
| 443 × 88320 | none | 44.35 | 43.39 | 1.022× |
| 443 × 98304 | none | 48.94 | 47.36 | 1.034× |
| 403 × 81928 | none | 38.18 | 37.15 | 1.027× |
| geometric mean | | | | 1.039× |

**Table B2.** B200 (sm_100a), the 81 measured shapes whose chunk
changes: latency in µs (median, cold L2) for main (the previous Cake
version, #7867) and this PR, CUDA 13.4 (nvcc 13.4.2), PyTorch 2.14.1.
Speedup is the median of paired interleaved ratios, so it can differ
slightly from the ratio of the medians shown.

| rows × vocab | temperature | main µs | this PR µs | speedup |
|---|---|---:|---:|---:|
| 45 × 81928 | none | 8.21 | 7.78 | 1.053× |
| 45 × 81928 | scalar T | 8.18 | 7.78 | 1.053× |
| 79 × 81928 | none | 11.31 | 10.94 | 1.035× |
| 79 × 81928 | scalar T | 11.31 | 10.96 | 1.035× |
| 93 × 81928 | none | 12.24 | 11.78 | 1.038× |
| 93 × 81928 | scalar T | 12.21 | 11.79 | 1.035× |
| 128 × 81928 | none | 15.01 | 14.43 | 1.042× |
| 128 × 81928 | scalar T | 15.02 | 14.43 | 1.042× |
| 180 × 81928 | none | 19.33 | 18.75 | 1.030× |
| 180 × 81928 | scalar T | 19.34 | 18.69 | 1.036× |
| 231 × 81928 | none | 23.86 | 22.64 | 1.054× |
| 231 × 81928 | scalar T | 23.94 | 22.69 | 1.056× |
| 296 × 81928 | none | 30.91 | 29.95 | 1.032× |
| 296 × 81928 | scalar T | 30.96 | 30.00 | 1.032× |
| 370 × 81928 | none | 37.54 | 36.30 | 1.033× |
| 370 × 81928 | scalar T | 37.58 | 36.32 | 1.035× |
| 497 × 81928 | none | 48.99 | 47.57 | 1.030× |
| 497 × 81928 | scalar T | 48.91 | 47.52 | 1.029× |
| 45 × 82944 | none | 8.22 | 7.81 | 1.053× |
| 79 × 82944 | none | 11.33 | 10.96 | 1.035× |
| 93 × 82944 | none | 12.19 | 11.76 | 1.036× |
| 128 × 82944 | none | 14.99 | 14.32 | 1.045× |
| 180 × 82944 | none | 19.20 | 18.54 | 1.033× |
| 231 × 82944 | none | 23.78 | 22.58 | 1.053× |
| 296 × 82944 | none | 30.50 | 29.97 | 1.018× |
| 370 × 82944 | none | 36.98 | 36.61 | 1.010× |
| 497 × 82944 | none | 48.21 | 48.03 | 1.003× |
| 45 × 84000 | none | 8.24 | 7.87 | 1.049× |
| 79 × 84000 | none | 11.38 | 11.02 | 1.032× |
| 93 × 84000 | none | 12.21 | 11.86 | 1.030× |
| 128 × 84000 | none | 14.93 | 14.43 | 1.036× |
| 180 × 84000 | none | 19.23 | 18.67 | 1.033× |
| 231 × 84000 | none | 23.74 | 22.69 | 1.047× |
| 296 × 84000 | none | 31.06 | 30.11 | 1.031× |
| 370 × 84000 | none | 37.66 | 36.62 | 1.028× |
| 497 × 84000 | none | 49.10 | 48.37 | 1.014× |
| 45 × 84840 | none | 8.26 | 7.94 | 1.040× |
| 79 × 84840 | none | 11.44 | 11.12 | 1.030× |
| 93 × 84840 | none | 12.34 | 11.97 | 1.030× |
| 128 × 84840 | none | 15.10 | 14.62 | 1.033× |
| 180 × 84840 | none | 19.36 | 18.88 | 1.025× |
| 231 × 84840 | none | 23.95 | 22.96 | 1.043× |
| 296 × 84840 | none | 31.89 | 30.61 | 1.042× |
| 370 × 84840 | none | 38.70 | 37.12 | 1.042× |
| 497 × 84840 | none | 50.40 | 48.83 | 1.032× |
| 45 × 86016 | none | 8.32 | 8.00 | 1.042× |
| 79 × 86016 | none | 11.42 | 11.10 | 1.028× |
| 93 × 86016 | none | 12.22 | 11.87 | 1.030× |
| 128 × 86016 | none | 15.01 | 14.50 | 1.035× |
| 180 × 86016 | none | 19.36 | 18.83 | 1.028× |
| 231 × 86016 | none | 23.86 | 22.83 | 1.045× |
| 296 × 86016 | none | 31.52 | 30.42 | 1.036× |
| 370 × 86016 | none | 38.21 | 36.80 | 1.037× |
| 497 × 86016 | none | 49.70 | 48.93 | 1.016× |
| 45 × 87040 | none | 8.29 | 8.05 | 1.031× |
| 79 × 87040 | none | 11.41 | 11.04 | 1.032× |
| 93 × 87040 | none | 12.24 | 11.89 | 1.030× |
| 128 × 87040 | none | 15.06 | 14.54 | 1.036× |
| 180 × 87040 | none | 19.36 | 18.59 | 1.044× |
| 231 × 87040 | none | 23.89 | 22.93 | 1.042× |
| 296 × 87040 | none | 31.66 | 30.77 | 1.029× |
| 370 × 87040 | none | 38.37 | 37.36 | 1.027× |
| 497 × 87040 | none | 50.13 | 49.82 | 1.006× |
| 45 × 88320 | none | 8.34 | 8.14 | 1.024× |
| 79 × 88320 | none | 11.42 | 11.14 | 1.026× |
| 93 × 88320 | none | 12.33 | 11.98 | 1.027× |
| 128 × 88320 | none | 15.10 | 14.72 | 1.027× |
| 180 × 88320 | none | 19.38 | 18.99 | 1.022× |
| 231 × 88320 | none | 24.05 | 23.17 | 1.037× |
| 296 × 88320 | none | 31.86 | 31.33 | 1.017× |
| 370 × 88320 | none | 38.51 | 37.90 | 1.017× |
| 497 × 88320 | none | 50.56 | 50.66 | 0.998× |
| 45 × 81928 | scalar T, PDL | 8.19 | 7.79 | 1.053× |
| 79 × 81928 | scalar T, PDL | 11.33 | 10.96 | 1.034× |
| 93 × 81928 | scalar T, PDL | 12.29 | 11.82 | 1.039× |
| 128 × 81928 | scalar T, PDL | 14.99 | 14.40 | 1.042× |
| 180 × 81928 | scalar T, PDL | 19.31 | 18.72 | 1.033× |
| 231 × 81928 | scalar T, PDL | 23.87 | 22.62 | 1.054× |
| 296 × 81928 | scalar T, PDL | 30.91 | 29.95 | 1.031× |
| 370 × 81928 | scalar T, PDL | 37.54 | 36.26 | 1.035× |
| 497 × 81928 | scalar T, PDL | 49.01 | 47.57 | 1.029× |
| geometric mean | | | | 1.034× |

Cake ships this softmax with no temperature, a scalar temperature, or a
per-row temperature, each with or without PDL, for B200 (sm_100a) and
GB300 (sm_103a).

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [8a3dcba](https://github.com/flashinfer-ai/flashinfer/commit/8a3dcba6e7f49ba09be0e32655f28e9865529580)

- **作者**: eigen
- **时间**: 2026-11-01T23:23:48Z
- **提交信息**: perf(cake_rmsnorm_silu_gate): non-deterministic bulk-prefetch long backward on SM100/SM103 (#8235)

`cake_rmsnorm_silu_gate` computes `y = RMSNorm(x, w) * SiLU(z)` on BF16
rows of head dim 128. It has five variants: one forward, plus a
deterministic and a non-deterministic backward that each write the
weight gradient in BF16 or FP32.

This PR changes only the non-deterministic (`deterministic=False`)
backward, for both dw dtypes, on sm_100a and sm_103a. From 1280 rows (T
× H) per SM, that backward now runs a new long-input program. It
prefetches each row block's packed dy, x and z into L2 with one bulk
prefetch per tensor. It runs 5 CTAs per SM, a quarter more than an SM
holds at once. Below 1280 rows per SM the backward does not change. The
forward and sm_107a do not change either. dx and dz stay bitwise equal
to the deterministic backward, dw stays within the deterministic
backward's error bound, and the API is unchanged.

There is one table per GPU: B200 (sm_100a, 148 SMs) and GB300 (sm_103a,
152 SMs). Each table has one row per shape (H = 48 and H = 32) for `fwd`
(eager call), `bwd (CUDA graph)` and `ckpt 2×fwd+bwd (CUDA graph)`. Each
row gives absolute µs for:

- deterministic Cake
- the best non-Cake implementation, named per row
- the previous Cake version (FlashInfer main as of #8217)
- the new path

A ratio above 1 means the new path is faster. `(n.s.)` marks a ratio
that is not significant: for vs det, a ratio within the round spread;
for vs #8217, an A/B result that is not consistently faster across all
pairs and GPUs. vs non-Cake ratios carry no significance mark.

Rows marked **changed** are `bwd` and `ckpt` at and above 1280 rows per
SM. Rows noted `same code as #8217` run the same kernel program in both
A/B arms (only a kernel symbol name differs), so their ratio against
#8217 is noise and carries no claim. This includes every `fwd` row.
`(<1280)` marks a shape just below the cut. The first five bullets below
cover the changed rows only.

### Speedup

- `bwd (CUDA graph)` vs #8217: B200 1.008-1.058x, GB300 1.008-1.057x.
- `bwd (CUDA graph)` vs deterministic Cake: B200 1.109-1.200x, GB300
1.080-1.142x.
- `ckpt 2×fwd+bwd (CUDA graph)` vs #8217: B200 1.004-1.031x (30193x48,
32737x48 and 33000x48 n.s.), GB300 1.005-1.036x.
- `ckpt 2×fwd+bwd (CUDA graph)` vs deterministic Cake: B200
1.046-1.130x, GB300 1.038-1.127x.
- `ckpt 2×fwd+bwd (CUDA graph)` vs best non-Cake: B200 1.049-1.110x,
GB300 1.023-1.101x. The CUDA-graph backward has no non-Cake time because
no non-Cake backward could be captured in a CUDA graph.
- `fwd` runs the same code as #8217 in every row. Against #8217 it is
0.999-1.001x on B200 and 0.999-1.003x on GB300, all n.s. Some forward
rows have more A/B pairs with this PR slower than faster: 12 on B200 and
7 on GB300. The largest is GB300 33000x48: +0.112 µs on 185.554 µs,
slower in 20 of 24 pairs. None of these rows is beyond noise.
- Below 1x vs best non-Cake:
- The forward on B200 from 1x48 to 4097x48 (0.659-0.970x) and at
16384x32 (0.984x).
- The forward on GB300 at 1x48, 7x48, 129x48, 1031x48, 2048x48, 4054x48
and 16384x32 (0.764-0.995x).
  - The checkpointed step at 1x48 only (B200 0.676x, GB300 0.981x).

  Every ratio below 1x vs deterministic Cake or vs #8217 is n.s.

**NVIDIA B200 (sm_100a, 148 SMs), CUDA 13.4, PyTorch 2.14.1+cu130**

The columns come from two separate runs on this GPU type:

- **Baseline run** (BF16 dw, median of 10 round medians): det Cake, best
non-Cake, new, vs det and vs non-Cake.
- **A/B run against FlashInfer main** (median over 24 processes per arm,
interleaved in pairs): #8217, new (A/B) and vs #8217.

n/a means no non-Cake backward could be captured in a CUDA graph.

| T × H (rows/SM) | op | det Cake (µs) | best non-Cake (µs) | new (µs) |
vs det | vs non-Cake | #8217, A/B (µs) | new, A/B (µs) | vs #8217 | note
|
|---:|---|---:|---:|---:|---:|---:|---:|---:|---:|---|
| 1x48 (0) | fwd | 3.0 | 2.0 (torch.compile max-autotune) | 3.0 | 1.010x
(n.s.) | 0.659x | 2.976 | 2.976 | 1.000x (n.s.) | same code as #8217 |
| 1x48 (0) | bwd (CUDA graph) | 5.1 | n/a | 4.8 | 1.060x (n.s.) | n/a |
4.608 | 4.608 | 1.000x (n.s.) | same code as #8217 |
| 1x48 (0) | ckpt 2×fwd+bwd (CUDA graph) | 10.2 | 6.8 (torch.compile
max-autotune) | 10.0 | 1.019x (n.s.) | 0.676x | 9.976 | 9.976 | 1.000x
(n.s.) | same code as #8217 |
| 7x48 (2) | fwd | 3.0 | 2.2 (torch.compile max-autotune) | 3.0 | 1.000x
(n.s.) | 0.737x | 3.104 | 3.104 | 1.000x (n.s.) | same code as #8217 |
| 7x48 (2) | bwd (CUDA graph) | 5.2 | n/a | 4.4 | 1.202x | n/a | 4.352 |
4.352 | 1.000x (n.s.) | same code as #8217 |
| 7x48 (2) | ckpt 2×fwd+bwd (CUDA graph) | 10.4 | 10.5 (torch.compile
max-autotune) | 10.0 | 1.032x (n.s.) | 1.041x | 9.752 | 9.760 | 0.999x
(n.s.) | same code as #8217 |
| 129x48 (42) | fwd | 3.9 | 3.3 (torch.compile) | 3.9 | 0.984x (n.s.) |
0.846x | 3.936 | 3.936 | 1.000x (n.s.) | same code as #8217 |
| 129x48 (42) | bwd (CUDA graph) | 7.8 | n/a | 6.6 | 1.187x | n/a |
6.576 | 6.560 | 1.002x (n.s.) | same code as #8217 |
| 129x48 (42) | ckpt 2×fwd+bwd (CUDA graph) | 13.2 | 14.9 (torch.compile
max-autotune) | 12.3 | 1.074x | 1.213x | 12.368 | 12.360 | 1.001x (n.s.)
| same code as #8217 |
| 1031x48 (334) | fwd | 10.4 | 9.8 (torch.compile) | 10.4 | 1.000x
(n.s.) | 0.936x | 10.784 | 10.776 | 1.001x (n.s.) | same code as #8217 |
| 1031x48 (334) | bwd (CUDA graph) | 23.0 | n/a | 19.3 | 1.195x | n/a |
19.168 | 19.168 | 1.000x (n.s.) | same code as #8217 |
| 1031x48 (334) | ckpt 2×fwd+bwd (CUDA graph) | 38.8 | 52.8
(torch.compile) | 35.8 | 1.085x | 1.476x | 35.920 | 35.928 | 1.000x
(n.s.) | same code as #8217 |
| 2048x48 (664) | fwd | 18.0 | 17.1 (torch.compile max-autotune) | 18.1
| 0.996x (n.s.) | 0.945x | 17.984 | 17.984 | 1.000x (n.s.) | same code
as #8217 |
| 2048x48 (664) | bwd (CUDA graph) | 35.6 | n/a | 30.4 | 1.168x | n/a |
30.400 | 30.400 | 1.000x (n.s.) | same code as #8217 |
| 2048x48 (664) | ckpt 2×fwd+bwd (CUDA graph) | 65.8 | 67.4 (FLA) | 63.3
| 1.039x | 1.064x | 63.312 | 63.296 | 1.000x (n.s.) | same code as #8217
|
| 3946x48 (<1280) | fwd | 31.5 | 29.3 (torch.compile) | 30.3 | 1.038x |
0.966x | 30.104 | 30.127 | 0.999x (n.s.) | same code as #8217 |
| 3946x48 (<1280) | bwd (CUDA graph) | 61.9 | n/a | 52.5 | 1.178x | n/a
| 52.448 | 52.448 | 1.000x (n.s.) | same code as #8217 |
| 3946x48 (<1280) | ckpt 2×fwd+bwd (CUDA graph) | 119.4 | 115.0 (FLA) |
110.8 | 1.078x | 1.038x | 110.064 | 110.040 | 1.000x (n.s.) | same code
as #8217 |
| 3947x48 (1280) | fwd | 31.5 | 29.1 (torch.compile) | 30.4 | 1.035x |
0.957x | 30.223 | 30.223 | 1.000x (n.s.) | same code as #8217 |
| 3947x48 (1280) | bwd (CUDA graph) | 61.9 | n/a | 51.6 | 1.200x | n/a |
53.472 | 51.328 | 1.042x | **changed**: new long backward |
| 3947x48 (1280) | ckpt 2×fwd+bwd (CUDA graph) | 119.5 | 117.7 (FLA) |
109.5 | 1.092x | 1.075x | 111.096 | 108.479 | 1.024x | **changed**:
unchanged forwards + new long backward |
| 4053x48 (1314) | fwd | 32.3 | 30.4 (torch.compile max-autotune) | 31.3
| 1.031x | 0.970x | 30.944 | 30.960 | 0.999x (n.s.) | same code as #8217
|
| 4053x48 (1314) | bwd (CUDA graph) | 63.1 | n/a | 52.9 | 1.194x | n/a |
53.568 | 52.696 | 1.017x | **changed**: new long backward |
| 4053x48 (1314) | ckpt 2×fwd+bwd (CUDA graph) | 122.4 | 119.4 (FLA) |
112.5 | 1.087x | 1.061x | 112.680 | 111.528 | 1.010x | **changed**:
unchanged forwards + new long backward |
| 4054x48 (1315) | fwd | 32.3 | 30.0 (torch.compile) | 31.3 | 1.033x |
0.959x | 31.152 | 31.152 | 1.000x (n.s.) | same code as #8217 |
| 4054x48 (1315) | bwd (CUDA graph) | 63.3 | n/a | 52.8 | 1.198x | n/a |
53.624 | 52.744 | 1.017x | **changed**: new long backward |
| 4054x48 (1315) | ckpt 2×fwd+bwd (CUDA graph) | 122.4 | 119.4 (FLA) |
112.5 | 1.088x | 1.062x | 112.824 | 111.632 | 1.011x | **changed**:
unchanged forwards + new long backward |
| 4097x48 (1329) | fwd | 32.5 | 30.0 (torch.compile) | 31.7 | 1.025x |
0.945x | 31.408 | 31.409 | 1.000x (n.s.) | same code as #8217 |
| 4097x48 (1329) | bwd (CUDA graph) | 59.9 | n/a | 53.7 | 1.117x | n/a |
53.779 | 53.368 | 1.008x | **changed**: new long backward |
| 4097x48 (1329) | ckpt 2×fwd+bwd (CUDA graph) | 119.6 | 120.0 (FLA) |
114.3 | 1.046x | 1.049x | 113.816 | 113.328 | 1.004x | **changed**:
unchanged forwards + new long backward |
| 8192x48 (2657) | fwd | 60.2 | 54.4 (torch.compile max-autotune) | 54.4
| 1.108x | 1.000x | 54.272 | 54.280 | 1.000x (n.s.) | same code as #8217
|
| 8192x48 (2657) | bwd (CUDA graph) | 106.7 | n/a | 95.0 | 1.124x | n/a
| 98.855 | 94.608 | 1.045x | **changed**: new long backward |
| 8192x48 (2657) | ckpt 2×fwd+bwd (CUDA graph) | 220.8 | 219.3 (FLA) |
199.7 | 1.106x | 1.098x | 203.407 | 198.191 | 1.026x | **changed**:
unchanged forwards + new long backward |
| 16384x48 (5314) | fwd | 114.8 | 102.6 (torch.compile max-autotune) |
102.2 | 1.123x | 1.003x | 101.904 | 101.896 | 1.000x (n.s.) | same code
as #8217 |
| 16384x48 (5314) | bwd (CUDA graph) | 197.7 | n/a | 177.1 | 1.116x |
n/a | 185.412 | 176.031 | 1.053x | **changed**: new long backward |
| 16384x48 (5314) | ckpt 2×fwd+bwd (CUDA graph) | 419.9 | 416.0 (FLA) |
376.5 | 1.115x | 1.105x | 384.822 | 374.834 | 1.027x | **changed**:
unchanged forwards + new long backward |
| 30000x48 (9730) | fwd | 204.5 | 189.8 (torch.compile) | 180.0 | 1.136x
| 1.054x | 179.231 | 179.191 | 1.000x (n.s.) | same code as #8217 |
| 30000x48 (9730) | bwd (CUDA graph) | 350.8 | n/a | 312.9 | 1.121x |
n/a | 329.416 | 312.428 | 1.054x | **changed**: new long backward |
| 30000x48 (9730) | ckpt 2×fwd+bwd (CUDA graph) | 752.7 | 739.5 (FLA) |
666.4 | 1.130x | 1.110x | 693.007 | 676.166 | 1.025x | **changed**:
unchanged forwards + new long backward |
| 30193x48 (9792) | fwd | 205.5 | 199.6 (torch.compile) | 181.6 | 1.131x
| 1.099x | 180.992 | 180.951 | 1.000x (n.s.) | same code as #8217 |
| 30193x48 (9792) | bwd (CUDA graph) | 352.2 | n/a | 314.7 | 1.119x |
n/a | 331.096 | 314.043 | 1.054x | **changed**: new long backward |
| 30193x48 (9792) | ckpt 2×fwd+bwd (CUDA graph) | 755.1 | 745.1 (FLA) |
671.6 | 1.124x | 1.109x | 693.822 | 677.403 | 1.024x (n.s.) |
**changed**: unchanged forwards + new long backward |
| 32388x48 (10504) | fwd | 220.4 | 205.4 (torch.compile max-autotune) |
194.4 | 1.133x | 1.056x | 193.231 | 193.312 | 1.000x (n.s.) | same code
as #8217 |
| 32388x48 (10504) | bwd (CUDA graph) | 376.9 | n/a | 336.8 | 1.119x |
n/a | 355.035 | 335.455 | 1.058x | **changed**: new long backward |
| 32388x48 (10504) | ckpt 2×fwd+bwd (CUDA graph) | 808.3 | 787.5
(torch.compile max-autotune) | 717.2 | 1.127x | 1.098x | 753.726 |
731.373 | 1.031x | **changed**: unchanged forwards + new long backward |
| 32737x48 (10617) | fwd | 222.5 | 217.1 (torch.compile) | 196.3 |
1.134x | 1.106x | 195.391 | 195.383 | 1.000x (n.s.) | same code as #8217
|
| 32737x48 (10617) | bwd (CUDA graph) | 381.8 | n/a | 342.1 | 1.116x |
n/a | 358.951 | 340.824 | 1.053x | **changed**: new long backward |
| 32737x48 (10617) | ckpt 2×fwd+bwd (CUDA graph) | 818.2 | 805.1 (FLA) |
725.9 | 1.127x | 1.109x | 761.110 | 739.049 | 1.030x (n.s.) |
**changed**: unchanged forwards + new long backward |
| 33000x48 (10703) | fwd | 225.1 | 209.5 (torch.compile max-autotune) |
198.2 | 1.136x | 1.057x | 196.351 | 196.384 | 1.000x (n.s.) | same code
as #8217 |
| 33000x48 (10703) | bwd (CUDA graph) | 383.3 | n/a | 345.5 | 1.109x |
n/a | 360.728 | 344.744 | 1.046x | **changed**: new long backward |
| 33000x48 (10703) | ckpt 2×fwd+bwd (CUDA graph) | 824.1 | 797.9
(torch.compile max-autotune) | 732.8 | 1.125x | 1.089x | 767.335 |
744.126 | 1.031x (n.s.) | **changed**: unchanged forwards + new long
backward |
| 16384x32 (3542) | fwd | 78.8 | 69.8 (torch.compile max-autotune) |
70.9 | 1.111x | 0.984x | 70.864 | 70.864 | 1.000x (n.s.) | same code as
#8217 |
| 16384x32 (3542) | bwd (CUDA graph) | 137.2 | n/a | 120.6 | 1.138x |
n/a | 127.583 | 120.952 | 1.055x | **changed**: new long backward |
| 16384x32 (3542) | ckpt 2×fwd+bwd (CUDA graph) | 288.6 | 285.7 (FLA) |
258.2 | 1.118x | 1.106x | 264.615 | 257.480 | 1.028x | **changed**:
unchanged forwards + new long backward |
| 32737x32 (7078) | fwd | 150.6 | 140.3 (torch.compile max-autotune) |
133.1 | 1.131x | 1.054x | 133.148 | 133.088 | 1.000x (n.s.) | same code
as #8217 |
| 32737x32 (7078) | bwd (CUDA graph) | 259.0 | n/a | 230.7 | 1.123x |
n/a | 242.583 | 229.959 | 1.055x | **changed**: new long backward |
| 32737x32 (7078) | ckpt 2×fwd+bwd (CUDA graph) | 552.6 | 540.5
(torch.compile max-autotune) | 491.0 | 1.125x | 1.101x | 503.839 |
491.007 | 1.026x | **changed**: unchanged forwards + new long backward |

**NVIDIA GB300 (sm_103a, 152 SMs), CUDA 13.4, PyTorch 2.14.1+cu130**

The columns come from two separate runs on this GPU type:

- **Baseline run** (BF16 dw, median of 10 round medians): det Cake, best
non-Cake, new, vs det and vs non-Cake.
- **A/B run against FlashInfer main** (median over 24 processes per arm,
interleaved in pairs): #8217, new (A/B) and vs #8217.

n/a means no non-Cake backward could be captured in a CUDA graph.

| T × H (rows/SM) | op | det Cake (µs) | best non-Cake (µs) | new (µs) |
vs det | vs non-Cake | #8217, A/B (µs) | new, A/B (µs) | vs #8217 | note
|
|---:|---|---:|---:|---:|---:|---:|---:|---:|---:|---|
| 1x48 (0) | fwd | 2.9 | 2.8 (mamba_ssm) | 3.0 | 0.973x (n.s.) | 0.915x
| 3.008 | 3.000 | 1.003x (n.s.) | same code as #8217 |
| 1x48 (0) | bwd (CUDA graph) | 5.8 | n/a | 4.5 | 1.284x | n/a | 4.560 |
4.560 | 1.000x (n.s.) | same code as #8217 |
| 1x48 (0) | ckpt 2×fwd+bwd (CUDA graph) | 10.0 | 9.0 (torch.compile
max-autotune) | 9.2 | 1.089x (n.s.) | 0.981x | 9.848 | 9.848 | 1.000x
(n.s.) | same code as #8217 |
| 7x48 (2) | fwd | 2.8 | 2.2 (torch.compile) | 2.8 | 1.000x (n.s.) |
0.764x | 2.944 | 2.944 | 1.000x (n.s.) | same code as #8217 |
| 7x48 (2) | bwd (CUDA graph) | 5.8 | n/a | 4.3 | 1.357x | n/a | 4.256 |
4.256 | 1.000x (n.s.) | same code as #8217 |
| 7x48 (2) | ckpt 2×fwd+bwd (CUDA graph) | 9.8 | 9.4 (torch.compile) |
8.9 | 1.095x (n.s.) | 1.050x | 9.696 | 9.656 | 1.004x (n.s.) | same code
as #8217 |
| 129x48 (41) | fwd | 3.6 | 3.4 (FLA) | 3.6 | 1.000x (n.s.) | 0.930x |
3.776 | 3.776 | 1.000x (n.s.) | same code as #8217 |
| 129x48 (41) | bwd (CUDA graph) | 8.5 | n/a | 6.6 | 1.293x | n/a |
6.608 | 6.608 | 1.000x (n.s.) | same code as #8217 |
| 129x48 (41) | ckpt 2×fwd+bwd (CUDA graph) | 13.2 | 16.3 (FLA) | 11.6 |
1.140x | 1.409x | 11.808 | 11.808 | 1.000x (n.s.) | same code as #8217 |
| 1031x48 (326) | fwd | 10.0 | 10.0 (FLA) | 10.1 | 0.994x (n.s.) |
0.990x | 9.952 | 9.952 | 1.000x (n.s.) | same code as #8217 |
| 1031x48 (326) | bwd (CUDA graph) | 22.9 | n/a | 17.9 | 1.277x | n/a |
18.112 | 18.112 | 1.000x (n.s.) | same code as #8217 |
| 1031x48 (326) | ckpt 2×fwd+bwd (CUDA graph) | 37.0 | 43.5 (FLA) | 33.0
| 1.120x | 1.317x | 33.184 | 33.184 | 1.000x (n.s.) | same code as #8217
|
| 2048x48 (647) | fwd | 16.7 | 16.4 (FLA) | 16.8 | 0.992x (n.s.) |
0.977x | 17.072 | 17.072 | 1.000x (n.s.) | same code as #8217 |
| 2048x48 (647) | bwd (CUDA graph) | 34.5 | n/a | 28.4 | 1.214x | n/a |
28.352 | 28.352 | 1.000x (n.s.) | same code as #8217 |
| 2048x48 (647) | ckpt 2×fwd+bwd (CUDA graph) | 61.9 | 61.7 (FLA) | 58.4
| 1.061x | 1.058x | 58.720 | 58.720 | 1.000x (n.s.) | same code as #8217
|
| 3946x48 (1246) | fwd | 29.5 | 29.0 (torch.compile max-autotune) | 28.9
| 1.019x | 1.003x | 28.800 | 28.800 | 1.000x (n.s.) | same code as #8217
|
| 3946x48 (1246) | bwd (CUDA graph) | 59.3 | n/a | 51.8 | 1.145x | n/a |
51.712 | 51.712 | 1.000x (n.s.) | same code as #8217 |
| 3946x48 (1246) | ckpt 2×fwd+bwd (CUDA graph) | 113.1 | 108.1 (FLA) |
106.3 | 1.064x | 1.017x | 106.425 | 106.432 | 1.000x (n.s.) | same code
as #8217 |
| 3947x48 (1246) | fwd | 29.1 | 29.8 (FLA) | 28.4 | 1.025x | 1.051x |
28.544 | 28.544 | 1.000x (n.s.) | same code as #8217 |
| 3947x48 (1246) | bwd (CUDA graph) | 59.2 | n/a | 51.8 | 1.144x | n/a |
51.712 | 51.712 | 1.000x (n.s.) | same code as #8217 |
| 3947x48 (1246) | ckpt 2×fwd+bwd (CUDA graph) | 112.4 | 108.2 (FLA) |
106.0 | 1.061x | 1.021x | 105.972 | 105.985 | 1.000x (n.s.) | same code
as #8217 |
| 4053x48 (<1280) | fwd | 30.1 | 29.5 (torch.compile max-autotune) |
29.2 | 1.030x | 1.008x | 29.160 | 29.152 | 1.000x (n.s.) | same code as
#8217 |
| 4053x48 (<1280) | bwd (CUDA graph) | 60.2 | n/a | 53.0 | 1.137x | n/a
| 52.905 | 52.920 | 1.000x (n.s.) | same code as #8217 |
| 4053x48 (<1280) | ckpt 2×fwd+bwd (CUDA graph) | 115.5 | 110.0 (FLA) |
108.2 | 1.068x | 1.017x | 108.056 | 108.041 | 1.000x (n.s.) | same code
as #8217 |
| 4054x48 (1280) | fwd | 30.0 | 27.1 (torch.compile) | 28.8 | 1.042x |
0.943x | 29.088 | 29.088 | 1.000x (n.s.) | same code as #8217 |
| 4054x48 (1280) | bwd (CUDA graph) | 60.2 | n/a | 52.7 | 1.142x | n/a |
53.248 | 52.728 | 1.010x | **changed**: new long backward |
| 4054x48 (1280) | ckpt 2×fwd+bwd (CUDA graph) | 115.0 | 111.8 (FLA) |
107.3 | 1.072x | 1.042x | 108.393 | 107.797 | 1.006x | **changed**:
unchanged forwards + new long backward |
| 4097x48 (1294) | fwd | 30.5 | 30.1 (FLA) | 29.3 | 1.040x | 1.027x |
29.372 | 29.376 | 1.000x (n.s.) | same code as #8217 |
| 4097x48 (1294) | bwd (CUDA graph) | 57.2 | n/a | 53.0 | 1.080x | n/a |
53.312 | 52.896 | 1.008x | **changed**: new long backward |
| 4097x48 (1294) | ckpt 2×fwd+bwd (CUDA graph) | 112.7 | 111.1 (FLA) |
108.6 | 1.038x | 1.023x | 108.520 | 108.025 | 1.005x | **changed**:
unchanged forwards + new long backward |
| 8192x48 (2587) | fwd | 55.9 | 54.4 (FLA) | 51.6 | 1.084x | 1.055x |
52.120 | 52.128 | 1.000x (n.s.) | same code as #8217 |
| 8192x48 (2587) | bwd (CUDA graph) | 100.6 | n/a | 91.6 | 1.097x | n/a
| 94.464 | 91.697 | 1.030x | **changed**: new long backward |
| 8192x48 (2587) | ckpt 2×fwd+bwd (CUDA graph) | 206.6 | 201.5 (FLA) |
189.5 | 1.090x | 1.064x | 193.169 | 189.152 | 1.021x | **changed**:
unchanged forwards + new long backward |
| 16384x48 (5174) | fwd | 106.3 | 97.3 (torch.compile max-autotune) |
95.5 | 1.112x | 1.018x | 95.636 | 95.649 | 1.000x (n.s.) | same code as
#8217 |
| 16384x48 (5174) | bwd (CUDA graph) | 183.9 | n/a | 165.1 | 1.114x |
n/a | 175.257 | 165.769 | 1.057x | **changed**: new long backward |
| 16384x48 (5174) | ckpt 2×fwd+bwd (CUDA graph) | 390.2 | 383.0 (FLA) |
349.6 | 1.116x | 1.096x | 361.546 | 351.153 | 1.030x | **changed**:
unchanged forwards + new long backward |
| 30000x48 (9474) | fwd | 191.2 | 184.4 (FLA) | 169.3 | 1.129x | 1.089x
| 169.441 | 169.441 | 1.000x (n.s.) | same code as #8217 |
| 30000x48 (9474) | bwd (CUDA graph) | 325.8 | n/a | 291.0 | 1.119x |
n/a | 305.714 | 291.789 | 1.048x | **changed**: new long backward |
| 30000x48 (9474) | ckpt 2×fwd+bwd (CUDA graph) | 701.5 | 684.1 (FLA) |
623.3 | 1.125x | 1.098x | 641.029 | 623.685 | 1.028x | **changed**:
unchanged forwards + new long backward |
| 30193x48 (9535) | fwd | 191.2 | 178.2 (torch.compile max-autotune) |
170.2 | 1.124x | 1.047x | 169.988 | 169.981 | 1.000x (n.s.) | same code
as #8217 |
| 30193x48 (9535) | bwd (CUDA graph) | 329.1 | n/a | 293.0 | 1.123x |
n/a | 306.962 | 293.522 | 1.046x | **changed**: new long backward |
| 30193x48 (9535) | ckpt 2×fwd+bwd (CUDA graph) | 704.9 | 679.9
(torch.compile max-autotune) | 627.3 | 1.124x | 1.084x | 643.172 |
627.475 | 1.025x | **changed**: unchanged forwards + new long backward |
| 32388x48 (10228) | fwd | 205.5 | 190.9 (torch.compile max-autotune) |
181.8 | 1.130x | 1.050x | 181.793 | 181.873 | 1.000x (n.s.) | same code
as #8217 |
| 32388x48 (10228) | bwd (CUDA graph) | 351.1 | n/a | 312.5 | 1.124x |
n/a | 328.450 | 312.770 | 1.050x | **changed**: new long backward |
| 32388x48 (10228) | ckpt 2×fwd+bwd (CUDA graph) | 755.6 | 723.0
(torch.compile max-autotune) | 670.6 | 1.127x | 1.078x | 688.334 |
671.699 | 1.025x | **changed**: unchanged forwards + new long backward |
| 32737x48 (10338) | fwd | 206.7 | 192.5 (torch.compile max-autotune) |
183.3 | 1.127x | 1.050x | 184.226 | 184.010 | 1.001x (n.s.) | same code
as #8217 |
| 32737x48 (10338) | bwd (CUDA graph) | 353.7 | n/a | 316.3 | 1.118x |
n/a | 331.906 | 316.226 | 1.050x | **changed**: new long backward |
| 32737x48 (10338) | ckpt 2×fwd+bwd (CUDA graph) | 759.9 | 742.5 (FLA) |
677.4 | 1.122x | 1.096x | 694.519 | 677.641 | 1.025x | **changed**:
unchanged forwards + new long backward |
| 33000x48 (10421) | fwd | 208.3 | 193.6 (torch.compile max-autotune) |
185.4 | 1.124x | 1.045x | 185.554 | 185.697 | 0.999x (n.s.) | same code
as #8217 |
| 33000x48 (10421) | bwd (CUDA graph) | 357.6 | n/a | 318.6 | 1.122x |
n/a | 334.326 | 318.817 | 1.049x | **changed**: new long backward |
| 33000x48 (10421) | ckpt 2×fwd+bwd (CUDA graph) | 768.1 | 752.5 (FLA) |
683.4 | 1.124x | 1.101x | 700.845 | 683.644 | 1.025x | **changed**:
unchanged forwards + new long backward |
| 16384x32 (3449) | fwd | 73.0 | 66.5 (torch.compile max-autotune) |
66.8 | 1.093x | 0.995x | 66.176 | 66.208 | 1.000x (n.s.) | same code as
#8217 |
| 16384x32 (3449) | bwd (CUDA graph) | 128.3 | n/a | 115.3 | 1.113x |
n/a | 121.217 | 115.616 | 1.048x | **changed**: new long backward |
| 16384x32 (3449) | ckpt 2×fwd+bwd (CUDA graph) | 268.8 | 263.1 (FLA) |
243.5 | 1.104x | 1.081x | 252.297 | 243.441 | 1.036x | **changed**:
unchanged forwards + new long backward |
| 32737x32 (6892) | fwd | 140.8 | 131.3 (torch.compile max-autotune) |
125.6 | 1.121x | 1.045x | 125.345 | 125.057 | 1.002x (n.s.) | same code
as #8217 |
| 32737x32 (6892) | bwd (CUDA graph) | 243.0 | n/a | 216.6 | 1.122x |
n/a | 226.709 | 216.914 | 1.045x | **changed**: new long backward |
| 32737x32 (6892) | ckpt 2×fwd+bwd (CUDA graph) | 519.2 | 503.1 (FLA) |
462.8 | 1.122x | 1.087x | 472.451 | 461.351 | 1.024x | **changed**:
unchanged forwards + new long backward |

The kernel's other Cake variants, the forward and the deterministic
backward with BF16 or FP32 dw, cover sm_100a, sm_103a and sm_107a, as
does the non-deterministic backward changed here.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance Improvements**
* Improved RMSNorm/SiLU-gate training backward execution for large
workloads on SM100, SM103, and SM107 GPUs.
* Added architecture-specific backward paths for SM100 and SM103, with
separate workspace caching for different weight-gradient data types.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [d5438ad](https://github.com/flashinfer-ai/flashinfer/commit/d5438ad3c8eaaeb47dc475d6ac4013d448abacf5)

- **作者**: eigen
- **时间**: 2026-11-01T22:59:41Z
- **提交信息**: feat(cake_rmsnorm): opt-in non-deterministic weight gradient for the autograd RMSNorm (#8208)

This PR adds the `cake_rmsnorm_train` package
(`flashinfer.cake_rmsnorm_train`: `cake_rmsnorm`,
`cake_rmsnorm_train_forward`, `cake_rmsnorm_train_backward`,
`cake_rmsnorm_train_backward_workspace_bytes`,
`cake_rmsnorm_train_backward_workspace`, `CakeRMSNormFunction`). These
are the names the training RMSNorm used before the deterministic package
`cake_rmsnorm_det_train` took the `det` names. The package covers BF16
activations with BF16 or FP32 weight, forward and backward, across 8
shape families: hidden sizes 512, 1536, 2048, 4096, 5120 and 6144,
residual-add H 6144, and H 256 per-head views (query `[T, 24, 256]` with
strides (12288, 512, 1); key `[T, 4, 256]`). Every entry point takes
`deterministic`, which defaults to `True` and returns the deterministic
package's results. This PR delivers the opt-in non-deterministic
backward (`deterministic=False`) for all of these variants. In that mode
`dx` is bitwise reproducible and `dw` is not. The forward and
`deterministic=True` paths run the deterministic package's programs.

**Speedup tables pending:** the tables have one row per shape on B200,
GB300 and R200 with absolute latencies. They compare against the
deterministic Cake backward (`cake_rmsnorm_det_train`) and the fastest
measured non-Cake implementation, a static per-shape `torch.compile`.
They are being measured at this head and will be added before the PR
leaves draft.

The kernel's other Cake variants are the deterministic training RMSNorm
`cake_rmsnorm_det_train` and the SiLU-gated training RMSNorm in
deterministic (`cake_rmsnorm_silu_gate_det_train`) and non-deterministic
(`cake_rmsnorm_silu_gate_train`) forms, and like this package they all
ship on sm_100a (B200), sm_103a (GB300) and sm_107a (R200).

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [f89853d](https://github.com/flashinfer-ai/flashinfer/commit/f89853d9e82099844b072a06a2c66ded0731336d)

- **作者**: eigen
- **时间**: 2026-11-01T22:37:14Z
- **提交信息**: perf(cake_gdn): SM107 CP prefill T-precompute on named barrier 1 and a 3-CTA ring state fixup (up to 1.18x) (#8234)

The context-parallel (CP) GDN prefill path runs four Cake stages:
T-precompute, MN-precompute, CP prefill and the ring state fixup. This
PR changes two of them, on sm_107a only. The FP16 T-precompute program
`cake_gdn_cp_ce1c179ef0e27da84479` now synchronizes on named barrier 1
instead of 6. A new ring fixup route, `state_fixup_simt_row4_mb3`
(`cake_gdn_cp_036c38e9a01062ebb4fa`), runs 3 CTAs per SM instead of 2.
The CP plan selects it on sm_107a when two conditions hold. First, the
fixup grid (32 CTAs per sequence and head) must be more than 2 CTAs per
SM. Second, all sequences must have the same length (`total_tokens ==
num_seqs * max_seqlen`), so batches with more than one sequence must
pass `max_seqlen`. Otherwise the plan keeps `state_fixup_simt_row4`. The
baseline is the previous Cake version of these kernels on FlashInfer
main. Over the 47 FP16 shapes below, the geomean speedup is 1.111x (seed
17 1.1107, seed 29 1.1108), with a minimum of 1.024x and a maximum of
1.176x. The 3-CTA fixup is selected on 33 of the 47 shapes.

*NVIDIA VR200 (Rubin), sm_107a, 212 SMs, driver 620.43; CUDA 13.4 (nvcc
13.4.92), torch 2.14.1+cu130. FP16 I/O, FP32 initial and final state,
head dim 128, int32 `cu_seqlens`,
`chunk_gated_delta_rule(backend="cake_gdn", use_cp=True,
max_seqlen=max(seq_lens))`. Each time is the CUPTI GPU span of one call,
from its first kernel start to its last kernel end, with L2 flushed
before the call. Each arm reports the median over three interleaved
ABBA/BAAB/ABBA groups, seed 17. ratio = main / new, so a value above 1
means this PR is faster. The fixup column gives the route this PR
selects; main uses row4 on every shape.*

| seq | Hq/Hk/Hv | fixup | main µs | new µs | ratio |
|---|---|---|---:|---:|---:|
| 1x16384 | 2/2/8 | row4 | 106.26 | 100.99 | 1.0521 |
| 1x65536 | 16/16/16 | mb3 | 385.86 | 328.29 | 1.1754 |
| 1x32768 | 16/16/16 | mb3 | 227.52 | 196.93 | 1.1553 |
| 1x8192 | 16/16/16 | mb3 | 104.74 | 96.39 | 1.0867 |
| 1x4096 | 16/16/16 | mb3 | 78.62 | 72.42 | 1.0857 |
| 6144+2048 | 16/16/16 | row4 | 103.49 | 98.16 | 1.0543 |
| 2x4096 | 16/16/16 | mb3 | 102.91 | 93.49 | 1.1008 |
| 2048+6144 | 16/16/16 | row4 | 108.90 | 102.40 | 1.0634 |
| 1024+7168 | 16/16/16 | row4 | 112.58 | 105.31 | 1.0690 |
| 1x65536 | 2/2/8 | row4 | 225.89 | 201.79 | 1.1194 |
| 1x32768 | 2/2/8 | row4 | 151.33 | 139.68 | 1.0834 |
| 1x8192 | 2/2/8 | row4 | 81.19 | 77.47 | 1.0479 |
| 1x4096 | 2/2/8 | row4 | 62.37 | 60.29 | 1.0345 |
| 6144+2048 | 2/2/8 | row4 | 76.48 | 73.67 | 1.0382 |
| 2x4096 | 2/2/8 | mb3 | 78.56 | 71.97 | 1.0916 |
| 2048+6144 | 2/2/8 | row4 | 82.11 | 80.16 | 1.0244 |
| 1024+7168 | 2/2/8 | row4 | 84.55 | 81.38 | 1.0389 |
| 1x65536 | 4/4/16 | mb3 | 369.44 | 317.51 | 1.1636 |
| 1x32768 | 4/4/16 | mb3 | 221.51 | 192.23 | 1.1523 |
| 1x16384 | 4/4/16 | mb3 | 146.85 | 131.55 | 1.1163 |
| 1x8192 | 4/4/16 | mb3 | 103.49 | 95.30 | 1.0860 |
| 1x4096 | 4/4/16 | mb3 | 78.18 | 71.81 | 1.0887 |
| 6144+2048 | 4/4/16 | row4 | 102.16 | 96.67 | 1.0568 |
| 2x4096 | 4/4/16 | mb3 | 101.89 | 92.74 | 1.0987 |
| 2048+6144 | 4/4/16 | row4 | 107.14 | 100.64 | 1.0645 |
| 1024+7168 | 4/4/16 | row4 | 112.16 | 105.09 | 1.0673 |
| 1x65536 | 8/8/32 | mb3 | 693.64 | 597.45 | 1.1610 |
| 1x32768 | 8/8/32 | mb3 | 369.19 | 316.26 | 1.1674 |
| 1x16384 | 8/8/32 | mb3 | 220.93 | 190.18 | 1.1617 |
| 1x8192 | 8/8/32 | mb3 | 148.38 | 131.26 | 1.1304 |
| 1x4096 | 8/8/32 | mb3 | 102.24 | 92.39 | 1.1067 |
| 1x65536 | 16/16/32 | mb3 | 698.94 | 601.29 | 1.1624 |
| 1x32768 | 16/16/32 | mb3 | 372.04 | 318.08 | 1.1696 |
| 1x16384 | 16/16/32 | mb3 | 222.53 | 191.04 | 1.1648 |
| 1x8192 | 16/16/32 | mb3 | 149.76 | 131.78 | 1.1365 |
| 1x4096 | 16/16/32 | mb3 | 102.94 | 93.57 | 1.1002 |
| 1x65536 | 16/16/48 | mb3 | 998.46 | 862.20 | 1.1580 |
| 1x32768 | 16/16/48 | mb3 | 529.72 | 458.66 | 1.1549 |
| 1x16384 | 16/16/48 | mb3 | 295.88 | 258.72 | 1.1436 |
| 1x8192 | 16/16/48 | mb3 | 179.68 | 159.23 | 1.1284 |
| 1x4096 | 16/16/48 | mb3 | 121.19 | 109.98 | 1.1018 |
| 1x16384 | 16/16/16 | mb3 | 149.44 | 133.15 | 1.1223 |
| 1x65536 | 32/32/32 | mb3 | 720.23 | 613.96 | 1.1731 |
| 1x32768 | 32/32/32 | mb3 | 386.02 | 328.21 | 1.1761 |
| 1x16384 | 32/32/32 | mb3 | 228.16 | 195.46 | 1.1673 |
| 1x8192 | 32/32/32 | mb3 | 151.11 | 132.03 | 1.1445 |
| 1x4096 | 32/32/32 | mb3 | 103.49 | 94.02 | 1.1007 |

The CP family also ships BF16 forms of every stage, and sm_100a and
sm_103a add `_cu32` T-precompute forms and UTCMMA ring fixups while
sharing their T-precompute and SIMT fixup programs. This PR leaves every
sm_100a and sm_103a kernel unchanged, along with the BF16 T-precompute
on all architectures, and BF16 calls on sm_107a, which can also select
the new fixup route, were not measured.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* Improved state-fixup processing for certain equal-length sequence
workloads on supported SM107a GPUs. The optimized path is selected for
larger workloads, while other cases retain the existing path.
* **Compatibility**
* Added support for an additional state-fixup execution path on SM107a
GPUs, with fallback behavior when that path is unavailable.
* **Reliability**
* Updated GPU synchronization behavior in an existing state-processing
kernel.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [06c5bdc](https://github.com/flashinfer-ai/flashinfer/commit/06c5bdcda2a30bf95d3c88ff6733caa69a2a3a0f)

- **作者**: eigen
- **时间**: 2026-11-01T22:34:17Z
- **提交信息**: feat(cake_kda): with grad, add non-deterministic Cake KDA context-parallel (KCP) autograd backend (#8218)

Cake KDA (Kimi Delta Attention) chunked training for packed
variable-length sequences at head dim 128 has four variants:
deterministic and non-deterministic, each in a single-rank form and a
context-parallel (KCP) form. This PR adds the non-deterministic KCP
package, `flashinfer.experimental.cake_kda_train_kcp`, and its facade
`flashinfer.cake_kda_train_kcp`. Every facade entry (`chunk_kda_kcp`,
`chunk_kda_fwd_kcp`, `chunk_kda_bwd_kcp` and the workspace helpers)
takes `deterministic: bool = True`. `True` runs the deterministic KCP
package `flashinfer.experimental.cake_kda_det_train_kcp`, and `False`
runs this one. The package's own entries accept only
`deterministic=False`. Each rank runs the chunk stages of the
non-deterministic single-rank package from #8191
(`flashinfer.experimental.cake.cake_kda_train`) on its own shard. The
KCP state walks, merge and exchanges come from the deterministic
package. The PR also adds an opt-in lean local arena for the KCP
backward, set with `local_arena="lean"` and `lean_passes=2` on the
workspace. The tables below use the default arena. They compare this
package with two baselines on the same workload: the deterministic Cake
KCP package and the strongest non-Cake implementation,
flash-linear-attention (FLA).

Workload: one packed batch of 4 documents (42024, 57573, 73122 and 88673
tokens, T = 261392), split over the ranks of a `torch.distributed`
process group, at H = 4, 16 and 64. q, k and v are BF16 [T, H, 128],
with q and k L2-normalized. The gate g is FP32 [T, H, 128],
pre-activated, in (-5, 0). beta is BF16 [T, H]. The timed step is the
KCP KDA step alone, without the short convolution. On one node, the
context-parallel sizes are CP8, CP4 and CP2 on the 8-GPU B200 and B300
nodes, and CP4 and CP2 on the 4-GPU R200 node. Across nodes, NVIDIA
GB300 (`sm_103a`, 152 SMs, 4 GPUs per node) runs CP8 on 2 nodes and CP16
on 4 nodes of one NVL72 rack, with one process per GPU. NCCL carries
every collective over the rack's multi-node NVLink. CP16 uses T = 261376
(42021, 57569, 73118 and 88668 tokens), because FLA's zigzag partition
needs T to be a multiple of 2W = 32.

Token layouts, for W ranks: `contiguous` gives rank r part r of W equal
parts. `zigzag` (global) gives rank r parts r and 2W-1-r of 2W equal
parts. `zigzag_per_document` applies the zigzag split inside every
document. Ops: `fwd` is the forward with autograd recording. `bwd` is
the backward of a forward that runs untimed before it. `ckpt` is one
`torch.utils.checkpoint(use_reentrant=False)` step: forward, recompute
and backward, which is 2 x forward + backward.

Baselines: deterministic Cake is
`flashinfer.experimental.cake_kda_det_train_kcp` on this PR's base,
which is bitwise identical from run to run. It uses its own partition
and context, and so does the new package. The strongest non-Cake
implementation ("SOTA" in the tables) is FLA 0.6.0's context-parallel
KDA. It is `fla.ops.kda.chunk_kda` with
`cp_context=fla.ops.cp.build_cp_context(cu_seqlens, group, layout)`
(Triton) and `safe_gate=True`, which is FLA's path for gates bounded
below. It runs on the same pre-activated operands, with `scale=None` and
no in-kernel L2 norm, gate or beta sigmoid. FLA's `contiguous` and
`zigzag` layouts are equal-token partitions. Here they give every rank
the same tokens, in the same order, as the Cake shard. FLA has no
per-document zigzag layout, so the `zigzag_per_document` rows show
`unsupported` in the SOTA columns. We chose FLA because it is the
reference open-source KDA implementation and the only non-Cake KDA
training kernel with context parallelism that we know of. Speedup =
baseline latency / new latency, so a value above 1 means the new package
is faster.

Protocol: `benchmarks/bench_cake_kda_train_kcp.py` with arms `det nd
control fla_cp`, in eager execution. Timing uses CUDA events. Each
iteration runs after an L2 flush, a device synchronize and a barrier,
and counts the slowest rank. Per op, every arm gets one untimed call,
followed by 3 groups. In every group the arms run in the palindromic
order det, nd, control, fla_cp, fla_cp, control, nd, det, and every
visit takes 8 timed iterations. Each cell is the median over the groups
of each group's median. `control` is a second visit of the new package.
Its ratio to the new package measures the protocol's own noise, and the
acceptance band is 0.98-1.02. `drift` is the change of the new package's
median between its first and last group, with a limit of 2 %. A † after
the op marks a row where the drift or the control ratio is outside its
limit. Software: torch 2.14.1+cu130 (CUDA runtime 13.0), FLA 0.6.0, and
Cake kernels built with CUDA 13.4.

Against the deterministic Cake KCP package, the new package is at parity
on every architecture. No row of the 270 is below 0.98. The lowest is
B300 CP8 `contiguous` H16 `fwd` at 0.9801, and it is a † row. Parity is
expected for two reasons. The KCP state walks, merge and exchanges are
the deterministic package's. The rank-local chunk stages come from
#8191, and on one GPU that package is itself at parity with the
deterministic package (speedup vs det 0.989-1.018 in #8191). Against FLA
0.6.0's context-parallel KDA, the new package is faster on every row
that FLA supports. The SOTA ranges exclude the `zigzag_per_document`
rows, because FLA has no per-document zigzag layout.

| GPU / architecture | rows | speedup vs det | speedup vs det, geometric
mean | speedup vs SOTA | † rows |
|---|---|---|---|---|---|
| B200 (`sm_100a`) | 81 | 0.985-1.015 | 1.001 | 1.84-8.14x | 7 |
| B300 (`sm_103a`) | 81 | 0.980-1.052 | 1.000 | 1.87-8.34x | 3 |
| R200 (`sm_107a`) | 54 | 0.998-1.028 | 1.003 | 2.04-9.99x | 3 |
| GB300 (`sm_103a`, 2 and 4 nodes) | 54 | 0.987-1.032 | 1.003 |
1.79-4.10x | 11 |

### NVIDIA B200 (`sm_100a`, 148 SMs, 8 GPUs)

All B200 rows come from one 8-GPU node. A 4-GPU run of the CP4 and CP2
configurations on another node of the same partition, with the same
build, benchmark and protocol, gave speedup vs det 0.976-1.019 and
speedup vs SOTA 1.84-8.19x.

| GPU / architecture | workload (shape, dtype, layout) | op |
deterministic Cake (ms) | strongest non-Cake (ms) | new
non-deterministic Cake (ms) | speedup vs det | speedup vs SOTA |
|---|---|---|---|---|---|---|---|
| B200 `sm_100a` | CP8 contiguous, 4 docs, T=261392, H=4, BF16 packed |
fwd † | 0.953 | 5.414 | 0.940 | 1.0138 | 5.7591 |
| B200 `sm_100a` | CP8 contiguous, 4 docs, T=261392, H=4, BF16 packed |
bwd † | 1.778 | 7.497 | 1.773 | 1.0025 | 4.2279 |
| B200 `sm_100a` | CP8 contiguous, 4 docs, T=261392, H=4, BF16 packed |
ckpt † | 4.135 | 17.760 | 4.192 | 0.9863 | 4.2362 |
| B200 `sm_100a` | CP8 contiguous, 4 docs, T=261392, H=16, BF16 packed |
fwd | 1.602 | 6.618 | 1.605 | 0.9982 | 4.1234 |
| B200 `sm_100a` | CP8 contiguous, 4 docs, T=261392, H=16, BF16 packed |
bwd | 3.333 | 10.435 | 3.329 | 1.0010 | 3.1344 |
| B200 `sm_100a` | CP8 contiguous, 4 docs, T=261392, H=16, BF16 packed |
ckpt | 5.833 | 23.187 | 5.857 | 0.9960 | 3.9588 |
| B200 `sm_100a` | CP8 contiguous, 4 docs, T=261392, H=64, BF16 packed |
fwd | 4.693 | 11.962 | 4.705 | 0.9976 | 2.5426 |
| B200 `sm_100a` | CP8 contiguous, 4 docs, T=261392, H=64, BF16 packed |
bwd | 10.370 | 24.522 | 10.344 | 1.0025 | 2.3707 |
| B200 `sm_100a` | CP8 contiguous, 4 docs, T=261392, H=64, BF16 packed |
ckpt | 19.124 | 47.920 | 19.174 | 0.9974 | 2.4992 |
| B200 `sm_100a` | CP8 zigzag, 4 docs, T=261392, H=4, BF16 packed | fwd
† | 0.926 | 5.011 | 0.929 | 0.9966 | 5.3947 |
| B200 `sm_100a` | CP8 zigzag, 4 docs, T=261392, H=4, BF16 packed | bwd
| 1.902 | 6.365 | 1.877 | 1.0132 | 3.3907 |
| B200 `sm_100a` | CP8 zigzag, 4 docs, T=261392, H=4, BF16 packed | ckpt
| 4.369 | 16.107 | 4.362 | 1.0017 | 3.6928 |
| B200 `sm_100a` | CP8 zigzag, 4 docs, T=261392, H=16, BF16 packed | fwd
| 1.718 | 6.518 | 1.719 | 0.9993 | 3.7906 |
| B200 `sm_100a` | CP8 zigzag, 4 docs, T=261392, H=16, BF16 packed | bwd
| 3.408 | 9.732 | 3.401 | 1.0020 | 2.8614 |
| B200 `sm_100a` | CP8 zigzag, 4 docs, T=261392, H=16, BF16 packed |
ckpt | 5.971 | 22.121 | 5.972 | 0.9998 | 3.7043 |
| B200 `sm_100a` | CP8 zigzag, 4 docs, T=261392, H=64, BF16 packed | fwd
| 4.528 | 12.261 | 4.532 | 0.9991 | 2.7057 |
| B200 `sm_100a` | CP8 zigzag, 4 docs, T=261392, H=64, BF16 packed | bwd
| 10.125 | 24.765 | 10.060 | 1.0065 | 2.4618 |
| B200 `sm_100a` | CP8 zigzag, 4 docs, T=261392, H=64, BF16 packed |
ckpt | 18.823 | 48.698 | 18.630 | 1.0104 | 2.6140 |
| B200 `sm_100a` | CP8 zigzag per document, 4 docs, T=261392, H=4, BF16
packed | fwd | 0.917 | unsupported | 0.905 | 1.0133 | n/a |
| B200 `sm_100a` | CP8 zigzag per document, 4 docs, T=261392, H=4, BF16
packed | bwd | 1.668 | unsupported | 1.664 | 1.0023 | n/a |
| B200 `sm_100a` | CP8 zigzag per document, 4 docs, T=261392, H=4, BF16
packed | ckpt | 3.959 | unsupported | 3.920 | 1.0099 | n/a |
| B200 `sm_100a` | CP8 zigzag per document, 4 docs, T=261392, H=16, BF16
packed | fwd | 1.657 | unsupported | 1.659 | 0.9988 | n/a |
| B200 `sm_100a` | CP8 zigzag per document, 4 docs, T=261392, H=16, BF16
packed | bwd | 3.373 | unsupported | 3.365 | 1.0024 | n/a |
| B200 `sm_100a` | CP8 zigzag per document, 4 docs, T=261392, H=16, BF16
packed | ckpt | 5.842 | unsupported | 5.832 | 1.0017 | n/a |
| B200 `sm_100a` | CP8 zigzag per document, 4 docs, T=261392, H=64, BF16
packed | fwd | 4.595 | unsupported | 4.599 | 0.9992 | n/a |
| B200 `sm_100a` | CP8 zigzag per document, 4 docs, T=261392, H=64, BF16
packed | bwd | 10.444 | unsupported | 10.356 | 1.0085 | n/a |
| B200 `sm_100a` | CP8 zigzag per document, 4 docs, T=261392, H=64, BF16
packed | ckpt | 19.322 | unsupported | 19.386 | 0.9967 | n/a |
| B200 `sm_100a` | CP4 contiguous, 4 docs, T=261392, H=4, BF16 packed |
fwd | 1.116 | 6.655 | 1.119 | 0.9977 | 5.9498 |
| B200 `sm_100a` | CP4 contiguous, 4 docs, T=261392, H=4, BF16 packed |
bwd | 2.274 | 14.420 | 2.257 | 1.0075 | 6.3884 |
| B200 `sm_100a` | CP4 contiguous, 4 docs, T=261392, H=4, BF16 packed |
ckpt | 4.537 | 26.206 | 4.545 | 0.9982 | 5.7659 |
| B200 `sm_100a` | CP4 contiguous, 4 docs, T=261392, H=16, BF16 packed |
fwd | 2.464 | 8.849 | 2.468 | 0.9982 | 3.5854 |
| B200 `sm_100a` | CP4 contiguous, 4 docs, T=261392, H=16, BF16 packed |
bwd | 5.422 | 20.168 | 5.424 | 0.9996 | 3.7183 |
| B200 `sm_100a` | CP4 contiguous, 4 docs, T=261392, H=16, BF16 packed |
ckpt | 9.520 | 36.346 | 9.515 | 1.0005 | 3.8198 |
| B200 `sm_100a` | CP4 contiguous, 4 docs, T=261392, H=64, BF16 packed |
fwd | 8.455 | 17.477 | 8.439 | 1.0019 | 2.0709 |
| B200 `sm_100a` | CP4 contiguous, 4 docs, T=261392, H=64, BF16 packed |
bwd | 20.002 | 47.838 | 20.142 | 0.9931 | 2.3750 |
| B200 `sm_100a` | CP4 contiguous, 4 docs, T=261392, H=64, BF16 packed |
ckpt | 37.081 | 82.357 | 37.468 | 0.9897 | 2.1981 |
| B200 `sm_100a` | CP4 zigzag, 4 docs, T=261392, H=4, BF16 packed | fwd
| 1.137 | 9.243 | 1.136 | 1.0011 | 8.1352 |
| B200 `sm_100a` | CP4 zigzag, 4 docs, T=261392, H=4, BF16 packed | bwd
| 2.218 | 9.558 | 2.216 | 1.0009 | 4.3140 |
| B200 `sm_100a` | CP4 zigzag, 4 docs, T=261392, H=4, BF16 packed | ckpt
| 4.528 | 27.988 | 4.531 | 0.9993 | 6.1768 |
| B200 `sm_100a` | CP4 zigzag, 4 docs, T=261392, H=16, BF16 packed | fwd
| 2.741 | 11.782 | 2.747 | 0.9979 | 4.2895 |
| B200 `sm_100a` | CP4 zigzag, 4 docs, T=261392, H=16, BF16 packed | bwd
| 5.597 | 15.787 | 5.599 | 0.9996 | 2.8193 |
| B200 `sm_100a` | CP4 zigzag, 4 docs, T=261392, H=16, BF16 packed |
ckpt | 10.249 | 39.113 | 10.253 | 0.9996 | 3.8149 |
| B200 `sm_100a` | CP4 zigzag, 4 docs, T=261392, H=64, BF16 packed | fwd
| 8.689 | 23.201 | 8.679 | 1.0012 | 2.6732 |
| B200 `sm_100a` | CP4 zigzag, 4 docs, T=261392, H=64, BF16 packed | bwd
† | 20.026 | 43.555 | 20.221 | 0.9903 | 2.1539 |
| B200 `sm_100a` | CP4 zigzag, 4 docs, T=261392, H=64, BF16 packed |
ckpt † | 37.546 | 89.427 | 37.958 | 0.9892 | 2.3560 |
| B200 `sm_100a` | CP4 zigzag per document, 4 docs, T=261392, H=4, BF16
packed | fwd | 1.087 | unsupported | 1.085 | 1.0021 | n/a |
| B200 `sm_100a` | CP4 zigzag per document, 4 docs, T=261392, H=4, BF16
packed | bwd | 2.160 | unsupported | 2.152 | 1.0034 | n/a |
| B200 `sm_100a` | CP4 zigzag per document, 4 docs, T=261392, H=4, BF16
packed | ckpt | 4.399 | unsupported | 4.395 | 1.0009 | n/a |
| B200 `sm_100a` | CP4 zigzag per document, 4 docs, T=261392, H=16, BF16
packed | fwd | 2.614 | unsupported | 2.616 | 0.9992 | n/a |
| B200 `sm_100a` | CP4 zigzag per document, 4 docs, T=261392, H=16, BF16
packed | bwd | 5.557 | unsupported | 5.554 | 1.0005 | n/a |
| B200 `sm_100a` | CP4 zigzag per document, 4 docs, T=261392, H=16, BF16
packed | ckpt | 9.943 | unsupported | 9.943 | 1.0000 | n/a |
| B200 `sm_100a` | CP4 zigzag per document, 4 docs, T=261392, H=64, BF16
packed | fwd | 8.369 | unsupported | 8.371 | 0.9998 | n/a |
| B200 `sm_100a` | CP4 zigzag per document, 4 docs, T=261392, H=64, BF16
packed | bwd | 20.007 | unsupported | 20.156 | 0.9926 | n/a |
| B200 `sm_100a` | CP4 zigzag per document, 4 docs, T=261392, H=64, BF16
packed | ckpt | 37.343 | unsupported | 37.390 | 0.9987 | n/a |
| B200 `sm_100a` | CP2 contiguous, 4 docs, T=261392, H=4, BF16 packed |
fwd | 1.641 | 7.981 | 1.642 | 0.9995 | 4.8608 |
| B200 `sm_100a` | CP2 contiguous, 4 docs, T=261392, H=4, BF16 packed |
bwd | 3.332 | 14.932 | 3.324 | 1.0024 | 4.4922 |
| B200 `sm_100a` | CP2 contiguous, 4 docs, T=261392, H=4, BF16 packed |
ckpt † | 6.030 | 29.539 | 6.041 | 0.9982 | 4.8896 |
| B200 `sm_100a` | CP2 contiguous, 4 docs, T=261392, H=16, BF16 packed |
fwd | 4.366 | 11.918 | 4.373 | 0.9986 | 2.7256 |
| B200 `sm_100a` | CP2 contiguous, 4 docs, T=261392, H=16, BF16 packed |
bwd | 9.814 | 26.266 | 9.833 | 0.9981 | 2.6713 |
| B200 `sm_100a` | CP2 contiguous, 4 docs, T=261392, H=16, BF16 packed |
ckpt | 18.166 | 48.773 | 17.898 | 1.0150 | 2.7251 |
| B200 `sm_100a` | CP2 contiguous, 4 docs, T=261392, H=64, BF16 packed |
fwd | 16.023 | 29.325 | 15.950 | 1.0046 | 1.8386 |
| B200 `sm_100a` | CP2 contiguous, 4 docs, T=261392, H=64, BF16 packed |
bwd | 39.513 | 77.373 | 39.168 | 1.0088 | 1.9754 |
| B200 `sm_100a` | CP2 contiguous, 4 docs, T=261392, H=64, BF16 packed |
ckpt | 72.964 | 135.322 | 72.670 | 1.0040 | 1.8621 |
| B200 `sm_100a` | CP2 zigzag, 4 docs, T=261392, H=4, BF16 packed | fwd
| 1.650 | 9.830 | 1.653 | 0.9987 | 5.9481 |
| B200 `sm_100a` | CP2 zigzag, 4 docs, T=261392, H=4, BF16 packed | bwd
| 3.351 | 16.618 | 3.327 | 1.0072 | 4.9954 |
| B200 `sm_100a` | CP2 zigzag, 4 docs, T=261392, H=4, BF16 packed | ckpt
| 5.868 | 35.161 | 5.864 | 1.0006 | 5.9958 |
| B200 `sm_100a` | CP2 zigzag, 4 docs, T=261392, H=16, BF16 packed | fwd
| 4.648 | 14.481 | 4.651 | 0.9993 | 3.1133 |
| B200 `sm_100a` | CP2 zigzag, 4 docs, T=261392, H=16, BF16 packed | bwd
| 10.073 | 28.711 | 10.043 | 1.0029 | 2.8587 |
| B200 `sm_100a` | CP2 zigzag, 4 docs, T=261392, H=16, BF16 packed |
ckpt | 18.665 | 55.932 | 18.546 | 1.0064 | 3.0158 |
| B200 `sm_100a` | CP2 zigzag, 4 docs, T=261392, H=64, BF16 packed | fwd
| 16.281 | 33.376 | 16.144 | 1.0085 | 2.0673 |
| B200 `sm_100a` | CP2 zigzag, 4 docs, T=261392, H=64, BF16 packed | bwd
| 39.409 | 83.868 | 39.073 | 1.0086 | 2.1464 |
| B200 `sm_100a` | CP2 zigzag, 4 docs, T=261392, H=64, BF16 packed |
ckpt | 73.375 | 149.759 | 73.095 | 1.0038 | 2.0488 |
| B200 `sm_100a` | CP2 zigzag per document, 4 docs, T=261392, H=4, BF16
packed | fwd | 1.577 | unsupported | 1.573 | 1.0024 | n/a |
| B200 `sm_100a` | CP2 zigzag per document, 4 docs, T=261392, H=4, BF16
packed | bwd | 3.205 | unsupported | 3.199 | 1.0019 | n/a |
| B200 `sm_100a` | CP2 zigzag per document, 4 docs, T=261392, H=4, BF16
packed | ckpt | 5.602 | unsupported | 5.604 | 0.9997 | n/a |
| B200 `sm_100a` | CP2 zigzag per document, 4 docs, T=261392, H=16, BF16
packed | fwd | 4.553 | unsupported | 4.552 | 1.0003 | n/a |
| B200 `sm_100a` | CP2 zigzag per document, 4 docs, T=261392, H=16, BF16
packed | bwd | 10.068 | unsupported | 10.025 | 1.0043 | n/a |
| B200 `sm_100a` | CP2 zigzag per document, 4 docs, T=261392, H=16, BF16
packed | ckpt | 18.397 | unsupported | 18.671 | 0.9853 | n/a |
| B200 `sm_100a` | CP2 zigzag per document, 4 docs, T=261392, H=64, BF16
packed | fwd | 16.345 | unsupported | 16.524 | 0.9892 | n/a |
| B200 `sm_100a` | CP2 zigzag per document, 4 docs, T=261392, H=64, BF16
packed | bwd | 39.405 | unsupported | 39.190 | 1.0055 | n/a |
| B200 `sm_100a` | CP2 zigzag per document, 4 docs, T=261392, H=64, BF16
packed | ckpt | 73.715 | unsupported | 73.584 | 1.0018 | n/a |

### NVIDIA B300 (`sm_103a`, 148 SMs, 8 GPUs)

| GPU / architecture | workload (shape, dtype, layout) | op |
deterministic Cake (ms) | strongest non-Cake (ms) | new
non-deterministic Cake (ms) | speedup vs det | speedup vs SOTA |
|---|---|---|---|---|---|---|---|
| B300 `sm_103a` | CP8 contiguous, 4 docs, T=261392, H=4, BF16 packed |
fwd | 0.965 | 5.315 | 0.963 | 1.0021 | 5.5211 |
| B300 `sm_103a` | CP8 contiguous, 4 docs, T=261392, H=4, BF16 packed |
bwd † | 1.805 | 7.271 | 1.801 | 1.0022 | 4.0370 |
| B300 `sm_103a` | CP8 contiguous, 4 docs, T=261392, H=4, BF16 packed |
ckpt | 4.230 | 17.341 | 4.215 | 1.0037 | 4.1145 |
| B300 `sm_103a` | CP8 contiguous, 4 docs, T=261392, H=16, BF16 packed |
fwd † | 1.640 | 6.403 | 1.673 | 0.9801 | 3.8262 |
| B300 `sm_103a` | CP8 contiguous, 4 docs, T=261392, H=16, BF16 packed |
bwd | 3.188 | 10.082 | 3.186 | 1.0005 | 3.1644 |
| B300 `sm_103a` | CP8 contiguous, 4 docs, T=261392, H=16, BF16 packed |
ckpt | 5.713 | 22.426 | 5.707 | 1.0010 | 3.9295 |
| B300 `sm_103a` | CP8 contiguous, 4 docs, T=261392, H=64, BF16 packed |
fwd | 4.557 | 11.625 | 4.548 | 1.0020 | 2.5563 |
| B300 `sm_103a` | CP8 contiguous, 4 docs, T=261392, H=64, BF16 packed |
bwd | 9.609 | 23.410 | 9.614 | 0.9995 | 2.4350 |
| B300 `sm_103a` | CP8 contiguous, 4 docs, T=261392, H=64, BF16 packed |
ckpt | 17.851 | 46.195 | 17.860 | 0.9995 | 2.5865 |
| B300 `sm_103a` | CP8 zigzag, 4 docs, T=261392, H=4, BF16 packed | fwd
| 0.924 | 4.974 | 0.923 | 1.0013 | 5.3878 |
| B300 `sm_103a` | CP8 zigzag, 4 docs, T=261392, H=4, BF16 packed | bwd
| 1.687 | 6.226 | 1.691 | 0.9973 | 3.6811 |
| B300 `sm_103a` | CP8 zigzag, 4 docs, T=261392, H=4, BF16 packed | ckpt
| 4.018 | 15.859 | 4.077 | 0.9855 | 3.8898 |
| B300 `sm_103a` | CP8 zigzag, 4 docs, T=261392, H=16, BF16 packed | fwd
| 1.695 | 6.255 | 1.699 | 0.9979 | 3.6815 |
| B300 `sm_103a` | CP8 zigzag, 4 docs, T=261392, H=16, BF16 packed | bwd
| 3.258 | 9.486 | 3.253 | 1.0014 | 2.9158 |
| B300 `sm_103a` | CP8 zigzag, 4 docs, T=261392, H=16, BF16 packed |
ckpt | 5.807 | 21.469 | 5.824 | 0.9972 | 3.6867 |
| B300 `sm_103a` | CP8 zigzag, 4 docs, T=261392, H=64, BF16 packed | fwd
| 4.335 | 11.905 | 4.341 | 0.9986 | 2.7423 |
| B300 `sm_103a` | CP8 zigzag, 4 docs, T=261392, H=64, BF16 packed | bwd
| 9.414 | 23.672 | 9.415 | 0.9999 | 2.5144 |
| B300 `sm_103a` | CP8 zigzag, 4 docs, T=261392, H=64, BF16 packed |
ckpt | 17.265 | 46.899 | 17.273 | 0.9995 | 2.7151 |
| B300 `sm_103a` | CP8 zigzag per document, 4 docs, T=261392, H=4, BF16
packed | fwd | 0.968 | unsupported | 0.962 | 1.0065 | n/a |
| B300 `sm_103a` | CP8 zigzag per document, 4 docs, T=261392, H=4, BF16
packed | bwd | 1.777 | unsupported | 1.781 | 0.9978 | n/a |
| B300 `sm_103a` | CP8 zigzag per document, 4 docs, T=261392, H=4, BF16
packed | ckpt | 4.540 | unsupported | 4.315 | 1.0521 | n/a |
| B300 `sm_103a` | CP8 zigzag per document, 4 docs, T=261392, H=16, BF16
packed | fwd | 1.652 | unsupported | 1.650 | 1.0014 | n/a |
| B300 `sm_103a` | CP8 zigzag per document, 4 docs, T=261392, H=16, BF16
packed | bwd | 3.212 | unsupported | 3.215 | 0.9993 | n/a |
| B300 `sm_103a` | CP8 zigzag per document, 4 docs, T=261392, H=16, BF16
packed | ckpt | 5.743 | unsupported | 5.750 | 0.9989 | n/a |
| B300 `sm_103a` | CP8 zigzag per document, 4 docs, T=261392, H=64, BF16
packed | fwd | 4.437 | unsupported | 4.440 | 0.9994 | n/a |
| B300 `sm_103a` | CP8 zigzag per document, 4 docs, T=261392, H=64, BF16
packed | bwd | 9.578 | unsupported | 9.580 | 0.9997 | n/a |
| B300 `sm_103a` | CP8 zigzag per document, 4 docs, T=261392, H=64, BF16
packed | ckpt | 17.620 | unsupported | 17.621 | 1.0000 | n/a |
| B300 `sm_103a` | CP4 contiguous, 4 docs, T=261392, H=4, BF16 packed |
fwd | 1.094 | 6.469 | 1.097 | 0.9975 | 5.8982 |
| B300 `sm_103a` | CP4 contiguous, 4 docs, T=261392, H=4, BF16 packed |
bwd | 2.157 | 14.135 | 2.161 | 0.9981 | 6.5423 |
| B300 `sm_103a` | CP4 contiguous, 4 docs, T=261392, H=4, BF16 packed |
ckpt | 4.424 | 25.627 | 4.435 | 0.9974 | 5.7783 |
| B300 `sm_103a` | CP4 contiguous, 4 docs, T=261392, H=16, BF16 packed |
fwd | 2.426 | 8.357 | 2.426 | 1.0001 | 3.4445 |
| B300 `sm_103a` | CP4 contiguous, 4 docs, T=261392, H=16, BF16 packed |
bwd | 5.135 | 19.577 | 5.138 | 0.9996 | 3.8105 |
| B300 `sm_103a` | CP4 contiguous, 4 docs, T=261392, H=16, BF16 packed |
ckpt | 9.129 | 34.847 | 9.130 | 0.9999 | 3.8170 |
| B300 `sm_103a` | CP4 contiguous, 4 docs, T=261392, H=64, BF16 packed |
fwd | 8.095 | 17.009 | 8.098 | 0.9997 | 2.1005 |
| B300 `sm_103a` | CP4 contiguous, 4 docs, T=261392, H=64, BF16 packed |
bwd | 17.738 | 45.604 | 17.747 | 0.9995 | 2.5698 |
| B300 `sm_103a` | CP4 contiguous, 4 docs, T=261392, H=64, BF16 packed |
ckpt | 33.108 | 79.130 | 33.138 | 0.9991 | 2.3879 |
| B300 `sm_103a` | CP4 zigzag, 4 docs, T=261392, H=4, BF16 packed | fwd
| 1.107 | 9.257 | 1.110 | 0.9981 | 8.3432 |
| B300 `sm_103a` | CP4 zigzag, 4 docs, T=261392, H=4, BF16 packed | bwd
† | 2.125 | 9.250 | 2.128 | 0.9985 | 4.3465 |
| B300 `sm_103a` | CP4 zigzag, 4 docs, T=261392, H=4, BF16 packed | ckpt
| 4.456 | 28.043 | 4.451 | 1.0010 | 6.3006 |
| B300 `sm_103a` | CP4 zigzag, 4 docs, T=261392, H=16, BF16 packed | fwd
| 2.680 | 11.622 | 2.679 | 1.0002 | 4.3376 |
| B300 `sm_103a` | CP4 zigzag, 4 docs, T=261392, H=16, BF16 packed | bwd
| 5.283 | 15.201 | 5.284 | 0.9998 | 2.8771 |
| B300 `sm_103a` | CP4 zigzag, 4 docs, T=261392, H=16, BF16 packed |
ckpt | 9.782 | 38.180 | 9.770 | 1.0012 | 3.9079 |
| B300 `sm_103a` | CP4 zigzag, 4 docs, T=261392, H=64, BF16 packed | fwd
| 8.341 | 22.576 | 8.344 | 0.9997 | 2.7058 |
| B300 `sm_103a` | CP4 zigzag, 4 docs, T=261392, H=64, BF16 packed | bwd
| 17.895 | 41.595 | 17.900 | 0.9997 | 2.3237 |
| B300 `sm_103a` | CP4 zigzag, 4 docs, T=261392, H=64, BF16 packed |
ckpt | 33.583 | 86.139 | 33.577 | 1.0002 | 2.5654 |
| B300 `sm_103a` | CP4 zigzag per document, 4 docs, T=261392, H=4, BF16
packed | fwd | 1.060 | unsupported | 1.067 | 0.9932 | n/a |
| B300 `sm_103a` | CP4 zigzag per document, 4 docs, T=261392, H=4, BF16
packed | bwd | 2.046 | unsupported | 2.043 | 1.0014 | n/a |
| B300 `sm_103a` | CP4 zigzag per document, 4 docs, T=261392, H=4, BF16
packed | ckpt | 4.323 | unsupported | 4.302 | 1.0048 | n/a |
| B300 `sm_103a` | CP4 zigzag per document, 4 docs, T=261392, H=16, BF16
packed | fwd | 2.559 | unsupported | 2.564 | 0.9982 | n/a |
| B300 `sm_103a` | CP4 zigzag per document, 4 docs, T=261392, H=16, BF16
packed | bwd | 5.253 | unsupported | 5.260 | 0.9986 | n/a |
| B300 `sm_103a` | CP4 zigzag per document, 4 docs, T=261392, H=16, BF16
packed | ckpt | 9.500 | unsupported | 9.506 | 0.9994 | n/a |
| B300 `sm_103a` | CP4 zigzag per document, 4 docs, T=261392, H=64, BF16
packed | fwd | 7.998 | unsupported | 8.003 | 0.9994 | n/a |
| B300 `sm_103a` | CP4 zigzag per document, 4 docs, T=261392, H=64, BF16
packed | bwd | 17.769 | unsupported | 17.762 | 1.0004 | n/a |
| B300 `sm_103a` | CP4 zigzag per document, 4 docs, T=261392, H=64, BF16
packed | ckpt | 32.965 | unsupported | 32.984 | 0.9994 | n/a |
| B300 `sm_103a` | CP2 contiguous, 4 docs, T=261392, H=4, BF16 packed |
fwd | 1.608 | 7.777 | 1.608 | 1.0000 | 4.8368 |
| B300 `sm_103a` | CP2 contiguous, 4 docs, T=261392, H=4, BF16 packed |
bwd | 3.117 | 14.377 | 3.115 | 1.0008 | 4.6156 |
| B300 `sm_103a` | CP2 contiguous, 4 docs, T=261392, H=4, BF16 packed |
ckpt | 5.654 | 28.464 | 5.645 | 1.0016 | 5.0423 |
| B300 `sm_103a` | CP2 contiguous, 4 docs, T=261392, H=16, BF16 packed |
fwd | 4.253 | 11.365 | 4.265 | 0.9972 | 2.6646 |
| B300 `sm_103a` | CP2 contiguous, 4 docs, T=261392, H=16, BF16 packed |
bwd | 9.187 | 24.993 | 9.191 | 0.9996 | 2.7193 |
| B300 `sm_103a` | CP2 contiguous, 4 docs, T=261392, H=16, BF16 packed |
ckpt | 16.851 | 46.371 | 16.857 | 0.9996 | 2.7509 |
| B300 `sm_103a` | CP2 contiguous, 4 docs, T=261392, H=64, BF16 packed |
fwd | 15.261 | 28.548 | 15.261 | 1.0000 | 1.8706 |
| B300 `sm_103a` | CP2 contiguous, 4 docs, T=261392, H=64, BF16 packed |
bwd | 34.365 | 73.660 | 34.441 | 0.9978 | 2.1387 |
| B300 `sm_103a` | CP2 contiguous, 4 docs, T=261392, H=64, BF16 packed |
ckpt | 64.340 | 130.342 | 64.430 | 0.9986 | 2.0230 |
| B300 `sm_103a` | CP2 zigzag, 4 docs, T=261392, H=4, BF16 packed | fwd
| 1.599 | 9.592 | 1.605 | 0.9963 | 5.9779 |
| B300 `sm_103a` | CP2 zigzag, 4 docs, T=261392, H=4, BF16 packed | bwd
| 3.102 | 16.009 | 3.103 | 0.9995 | 5.1585 |
| B300 `sm_103a` | CP2 zigzag, 4 docs, T=261392, H=4, BF16 packed | ckpt
| 5.666 | 34.122 | 5.658 | 1.0015 | 6.0307 |
| B300 `sm_103a` | CP2 zigzag, 4 docs, T=261392, H=16, BF16 packed | fwd
| 4.495 | 13.665 | 4.501 | 0.9988 | 3.0360 |
| B300 `sm_103a` | CP2 zigzag, 4 docs, T=261392, H=16, BF16 packed | bwd
| 9.415 | 27.840 | 9.424 | 0.9990 | 2.9542 |
| B300 `sm_103a` | CP2 zigzag, 4 docs, T=261392, H=16, BF16 packed |
ckpt | 17.546 | 53.461 | 17.553 | 0.9996 | 3.0457 |
| B300 `sm_103a` | CP2 zigzag, 4 docs, T=261392, H=64, BF16 packed | fwd
| 15.441 | 32.523 | 15.440 | 1.0001 | 2.1064 |
| B300 `sm_103a` | CP2 zigzag, 4 docs, T=261392, H=64, BF16 packed | bwd
| 34.467 | 80.058 | 34.491 | 0.9993 | 2.3211 |
| B300 `sm_103a` | CP2 zigzag, 4 docs, T=261392, H=64, BF16 packed |
ckpt | 64.586 | 144.134 | 64.788 | 0.9969 | 2.2247 |
| B300 `sm_103a` | CP2 zigzag per document, 4 docs, T=261392, H=4, BF16
packed | fwd | 1.532 | unsupported | 1.534 | 0.9985 | n/a |
| B300 `sm_103a` | CP2 zigzag per document, 4 docs, T=261392, H=4, BF16
packed | bwd | 3.075 | unsupported | 3.074 | 1.0006 | n/a |
| B300 `sm_103a` | CP2 zigzag per document, 4 docs, T=261392, H=4, BF16
packed | ckpt | 5.478 | unsupported | 5.463 | 1.0028 | n/a |
| B300 `sm_103a` | CP2 zigzag per document, 4 docs, T=261392, H=16, BF16
packed | fwd | 4.406 | unsupported | 4.414 | 0.9983 | n/a |
| B300 `sm_103a` | CP2 zigzag per document, 4 docs, T=261392, H=16, BF16
packed | bwd | 9.377 | unsupported | 9.376 | 1.0002 | n/a |
| B300 `sm_103a` | CP2 zigzag per document, 4 docs, T=261392, H=16, BF16
packed | ckpt | 17.353 | unsupported | 17.364 | 0.9994 | n/a |
| B300 `sm_103a` | CP2 zigzag per document, 4 docs, T=261392, H=64, BF16
packed | fwd | 15.539 | unsupported | 15.549 | 0.9994 | n/a |
| B300 `sm_103a` | CP2 zigzag per document, 4 docs, T=261392, H=64, BF16
packed | bwd | 34.445 | unsupported | 34.464 | 0.9994 | n/a |
| B300 `sm_103a` | CP2 zigzag per document, 4 docs, T=261392, H=64, BF16
packed | ckpt | 64.845 | unsupported | 64.894 | 0.9993 | n/a |

### NVIDIA R200 (`sm_107a`, 212 SMs, 4 GPUs)

The H4 and H16 rows come from a second run of the same protocol, because
in the first run 7 of those 12 configurations had the drift or the
control ratio outside its limit. The H64 rows come from the first run.

| GPU / architecture | workload (shape, dtype, layout) | op |
deterministic Cake (ms) | strongest non-Cake (ms) | new
non-deterministic Cake (ms) | speedup vs det | speedup vs SOTA |
|---|---|---|---|---|---|---|---|
| R200 `sm_107a` | CP4 contiguous, 4 docs, T=261392, H=4, BF16 packed |
fwd | 0.747 | 5.431 | 0.745 | 1.0034 | 7.2912 |
| R200 `sm_107a` | CP4 contiguous, 4 docs, T=261392, H=4, BF16 packed |
bwd | 1.308 | 11.263 | 1.300 | 1.0068 | 8.6668 |
| R200 `sm_107a` | CP4 contiguous, 4 docs, T=261392, H=4, BF16 packed |
ckpt | 3.005 | 21.119 | 2.959 | 1.0155 | 7.1380 |
| R200 `sm_107a` | CP4 contiguous, 4 docs, T=261392, H=16, BF16 packed |
fwd † | 1.503 | 6.824 | 1.500 | 1.0022 | 4.5501 |
| R200 `sm_107a` | CP4 contiguous, 4 docs, T=261392, H=16, BF16 packed |
bwd | 2.988 | 15.024 | 2.980 | 1.0030 | 5.0424 |
| R200 `sm_107a` | CP4 contiguous, 4 docs, T=261392, H=16, BF16 packed |
ckpt | 5.598 | 27.340 | 5.601 | 0.9994 | 4.8811 |
| R200 `sm_107a` | CP4 contiguous, 4 docs, T=261392, H=64, BF16 packed |
fwd | 4.552 | 11.323 | 4.557 | 0.9989 | 2.4848 |
| R200 `sm_107a` | CP4 contiguous, 4 docs, T=261392, H=64, BF16 packed |
bwd | 10.593 | 28.342 | 10.561 | 1.0031 | 2.6837 |
| R200 `sm_107a` | CP4 contiguous, 4 docs, T=261392, H=64, BF16 packed |
ckpt | 18.929 | 49.521 | 18.907 | 1.0012 | 2.6192 |
| R200 `sm_107a` | CP4 zigzag, 4 docs, T=261392, H=4, BF16 packed | fwd
| 0.756 | 7.540 | 0.755 | 1.0018 | 9.9882 |
| R200 `sm_107a` | CP4 zigzag, 4 docs, T=261392, H=4, BF16 packed | bwd
† | 1.220 | 7.533 | 1.218 | 1.0019 | 6.1873 |
| R200 `sm_107a` | CP4 zigzag, 4 docs, T=261392, H=4, BF16 packed | ckpt
| 2.834 | 22.863 | 2.815 | 1.0069 | 8.1231 |
| R200 `sm_107a` | CP4 zigzag, 4 docs, T=261392, H=16, BF16 packed | fwd
| 1.596 | 8.775 | 1.598 | 0.9985 | 5.4915 |
| R200 `sm_107a` | CP4 zigzag, 4 docs, T=261392, H=16, BF16 packed | bwd
| 3.070 | 10.773 | 3.043 | 1.0086 | 3.5399 |
| R200 `sm_107a` | CP4 zigzag, 4 docs, T=261392, H=16, BF16 packed |
ckpt | 5.832 | 28.281 | 5.833 | 0.9998 | 4.8484 |
| R200 `sm_107a` | CP4 zigzag, 4 docs, T=261392, H=64, BF16 packed | fwd
| 4.955 | 14.322 | 4.954 | 1.0003 | 2.8911 |
| R200 `sm_107a` | CP4 zigzag, 4 docs, T=261392, H=64, BF16 packed | bwd
| 10.893 | 24.462 | 10.884 | 1.0008 | 2.2475 |
| R200 `sm_107a` | CP4 zigzag, 4 docs, T=261392, H=64, BF16 packed |
ckpt | 20.065 | 52.725 | 20.041 | 1.0012 | 2.6309 |
| R200 `sm_107a` | CP4 zigzag per document, 4 docs, T=261392, H=4, BF16
packed | fwd | 0.713 | unsupported | 0.708 | 1.0079 | n/a |
| R200 `sm_107a` | CP4 zigzag per document, 4 docs, T=261392, H=4, BF16
packed | bwd | 1.175 | unsupported | 1.168 | 1.0062 | n/a |
| R200 `sm_107a` | CP4 zigzag per document, 4 docs, T=261392, H=4, BF16
packed | ckpt | 2.764 | unsupported | 2.736 | 1.0101 | n/a |
| R200 `sm_107a` | CP4 zigzag per document, 4 docs, T=261392, H=16, BF16
packed | fwd | 1.567 | unsupported | 1.563 | 1.0024 | n/a |
| R200 `sm_107a` | CP4 zigzag per document, 4 docs, T=261392, H=16, BF16
packed | bwd | 3.049 | unsupported | 3.050 | 0.9996 | n/a |
| R200 `sm_107a` | CP4 zigzag per document, 4 docs, T=261392, H=16, BF16
packed | ckpt | 5.820 | unsupported | 5.804 | 1.0027 | n/a |
| R200 `sm_107a` | CP4 zigzag per document, 4 docs, T=261392, H=64, BF16
packed | fwd | 4.591 | unsupported | 4.588 | 1.0005 | n/a |
| R200 `sm_107a` | CP4 zigzag per document, 4 docs, T=261392, H=64, BF16
packed | bwd | 10.608 | unsupported | 10.596 | 1.0011 | n/a |
| R200 `sm_107a` | CP4 zigzag per document, 4 docs, T=261392, H=64, BF16
packed | ckpt | 19.095 | unsupported | 19.080 | 1.0008 | n/a |
| R200 `sm_107a` | CP2 contiguous, 4 docs, T=261392, H=4, BF16 packed |
fwd | 0.994 | 6.475 | 0.992 | 1.0018 | 6.5287 |
| R200 `sm_107a` | CP2 contiguous, 4 docs, T=261392, H=4, BF16 packed |
bwd | 1.855 | 11.208 | 1.848 | 1.0037 | 6.0635 |
| R200 `sm_107a` | CP2 contiguous, 4 docs, T=261392, H=4, BF16 packed |
ckpt | 3.465 | 23.139 | 3.456 | 1.0025 | 6.6954 |
| R200 `sm_107a` | CP2 contiguous, 4 docs, T=261392, H=16, BF16 packed |
fwd | 2.590 | 8.636 | 2.588 | 1.0006 | 3.3368 |
| R200 `sm_107a` | CP2 contiguous, 4 docs, T=261392, H=16, BF16 packed |
bwd | 5.425 | 17.372 | 5.417 | 1.0015 | 3.2071 |
| R200 `sm_107a` | CP2 contiguous, 4 docs, T=261392, H=16, BF16 packed |
ckpt | 10.206 | 33.422 | 10.206 | 1.0000 | 3.2749 |
| R200 `sm_107a` | CP2 contiguous, 4 docs, T=261392, H=64, BF16 packed |
fwd | 8.502 | 17.300 | 8.496 | 1.0006 | 2.0363 |
| R200 `sm_107a` | CP2 contiguous, 4 docs, T=261392, H=64, BF16 packed |
bwd | 19.949 | 42.913 | 19.920 | 1.0015 | 2.1543 |
| R200 `sm_107a` | CP2 contiguous, 4 docs, T=261392, H=64, BF16 packed |
ckpt | 36.229 | 75.970 | 36.161 | 1.0019 | 2.1009 |
| R200 `sm_107a` | CP2 zigzag, 4 docs, T=261392, H=4, BF16 packed | fwd
| 0.991 | 7.983 | 0.989 | 1.0025 | 8.0724 |
| R200 `sm_107a` | CP2 zigzag, 4 docs, T=261392, H=4, BF16 packed | bwd
| 1.844 | 12.922 | 1.835 | 1.0046 | 7.0407 |
| R200 `sm_107a` | CP2 zigzag, 4 docs, T=261392, H=4, BF16 packed | ckpt
| 3.464 | 28.302 | 3.470 | 0.9983 | 8.1571 |
| R200 `sm_107a` | CP2 zigzag, 4 docs, T=261392, H=16, BF16 packed | fwd
| 2.700 | 10.117 | 2.689 | 1.0041 | 3.7632 |
| R200 `sm_107a` | CP2 zigzag, 4 docs, T=261392, H=16, BF16 packed | bwd
| 5.659 | 18.998 | 5.507 | 1.0277 | 3.4499 |
| R200 `sm_107a` | CP2 zigzag, 4 docs, T=261392, H=16, BF16 packed |
ckpt | 10.514 | 37.740 | 10.505 | 1.0008 | 3.5925 |
| R200 `sm_107a` | CP2 zigzag, 4 docs, T=261392, H=64, BF16 packed | fwd
| 8.632 | 19.375 | 8.629 | 1.0003 | 2.2455 |
| R200 `sm_107a` | CP2 zigzag, 4 docs, T=261392, H=64, BF16 packed | bwd
| 20.068 | 45.893 | 20.045 | 1.0012 | 2.2896 |
| R200 `sm_107a` | CP2 zigzag, 4 docs, T=261392, H=64, BF16 packed |
ckpt | 36.421 | 83.746 | 36.390 | 1.0009 | 2.3013 |
| R200 `sm_107a` | CP2 zigzag per document, 4 docs, T=261392, H=4, BF16
packed | fwd | 0.954 | unsupported | 0.952 | 1.0020 | n/a |
| R200 `sm_107a` | CP2 zigzag per document, 4 docs, T=261392, H=4, BF16
packed | bwd | 1.739 | unsupported | 1.737 | 1.0014 | n/a |
| R200 `sm_107a` | CP2 zigzag per document, 4 docs, T=261392, H=4, BF16
packed | ckpt | 3.286 | unsupported | 3.270 | 1.0049 | n/a |
| R200 `sm_107a` | CP2 zigzag per document, 4 docs, T=261392, H=16, BF16
packed | fwd | 2.629 | unsupported | 2.632 | 0.9991 | n/a |
| R200 `sm_107a` | CP2 zigzag per document, 4 docs, T=261392, H=16, BF16
packed | bwd † | 5.501 | unsupported | 5.488 | 1.0022 | n/a |
| R200 `sm_107a` | CP2 zigzag per document, 4 docs, T=261392, H=16, BF16
packed | ckpt | 10.358 | unsupported | 10.365 | 0.9994 | n/a |
| R200 `sm_107a` | CP2 zigzag per document, 4 docs, T=261392, H=64, BF16
packed | fwd | 8.727 | unsupported | 8.724 | 1.0003 | n/a |
| R200 `sm_107a` | CP2 zigzag per document, 4 docs, T=261392, H=64, BF16
packed | bwd | 20.113 | unsupported | 20.068 | 1.0022 | n/a |
| R200 `sm_107a` | CP2 zigzag per document, 4 docs, T=261392, H=64, BF16
packed | ckpt | 36.833 | unsupported | 36.788 | 1.0012 | n/a |

### NVIDIA GB300 (`sm_103a`, 152 SMs, 2 and 4 nodes of one NVL72 rack)

A rerun of the configurations marked † did not bring them within the
limits, so the table keeps the first run. The CP8 `contiguous` H4 and
H16 rows ran while a test job used the rack's other two nodes.

| GPU / architecture | workload (shape, dtype, layout) | op |
deterministic Cake (ms) | strongest non-Cake (ms) | new
non-deterministic Cake (ms) | speedup vs det | speedup vs SOTA |
|---|---|---|---|---|---|---|---|
| GB300 `sm_103a` | CP16 contiguous, 4 docs, T=261376, H=4, BF16 packed
| fwd | 1.422 | 2.994 | 1.378 | 1.0315 | 2.1722 |
| GB300 `sm_103a` | CP16 contiguous, 4 docs, T=261376, H=4, BF16 packed
| bwd | 1.723 | 3.678 | 1.708 | 1.0084 | 2.1530 |
| GB300 `sm_103a` | CP16 contiguous, 4 docs, T=261376, H=4, BF16 packed
| ckpt | 4.944 | 8.965 | 4.994 | 0.9899 | 1.7949 |
| GB300 `sm_103a` | CP16 contiguous, 4 docs, T=261376, H=16, BF16 packed
| fwd | 1.439 | 3.471 | 1.424 | 1.0111 | 2.4381 |
| GB300 `sm_103a` | CP16 contiguous, 4 docs, T=261376, H=16, BF16 packed
| bwd | 2.107 | 5.080 | 2.093 | 1.0067 | 2.4270 |
| GB300 `sm_103a` | CP16 contiguous, 4 docs, T=261376, H=16, BF16 packed
| ckpt | 5.406 | 11.644 | 5.341 | 1.0121 | 2.1802 |
| GB300 `sm_103a` | CP16 contiguous, 4 docs, T=261376, H=64, BF16 packed
| fwd | 2.574 | 6.078 | 2.571 | 1.0014 | 2.3643 |
| GB300 `sm_103a` | CP16 contiguous, 4 docs, T=261376, H=64, BF16 packed
| bwd | 4.935 | 11.703 | 4.950 | 0.9970 | 2.3642 |
| GB300 `sm_103a` | CP16 contiguous, 4 docs, T=261376, H=64, BF16 packed
| ckpt | 9.156 | 23.554 | 9.185 | 0.9968 | 2.5643 |
| GB300 `sm_103a` | CP16 zigzag, 4 docs, T=261376, H=4, BF16 packed |
fwd | 1.298 | 3.043 | 1.315 | 0.9867 | 2.3139 |
| GB300 `sm_103a` | CP16 zigzag, 4 docs, T=261376, H=4, BF16 packed |
bwd | 1.677 | 3.272 | 1.642 | 1.0215 | 1.9929 |
| GB300 `sm_103a` | CP16 zigzag, 4 docs, T=261376, H=4, BF16 packed |
ckpt † | 4.973 | 9.036 | 4.886 | 1.0179 | 1.8493 |
| GB300 `sm_103a` | CP16 zigzag, 4 docs, T=261376, H=16, BF16 packed |
fwd † | 1.328 | 3.500 | 1.323 | 1.0043 | 2.6465 |
| GB300 `sm_103a` | CP16 zigzag, 4 docs, T=261376, H=16, BF16 packed |
bwd † | 2.051 | 4.750 | 2.035 | 1.0082 | 2.3343 |
| GB300 `sm_103a` | CP16 zigzag, 4 docs, T=261376, H=16, BF16 packed |
ckpt † | 5.146 | 11.523 | 5.099 | 1.0093 | 2.2601 |
| GB300 `sm_103a` | CP16 zigzag, 4 docs, T=261376, H=64, BF16 packed |
fwd | 2.468 | 6.772 | 2.467 | 1.0004 | 2.7451 |
| GB300 `sm_103a` | CP16 zigzag, 4 docs, T=261376, H=64, BF16 packed |
bwd | 4.874 | 12.300 | 4.882 | 0.9983 | 2.5194 |
| GB300 `sm_103a` | CP16 zigzag, 4 docs, T=261376, H=64, BF16 packed |
ckpt | 8.961 | 25.346 | 8.961 | 1.0000 | 2.8284 |
| GB300 `sm_103a` | CP16 zigzag per document, 4 docs, T=261376, H=4,
BF16 packed | fwd † | 1.295 | unsupported | 1.293 | 1.0020 | n/a |
| GB300 `sm_103a` | CP16 zigzag per document, 4 docs, T=261376, H=4,
BF16 packed | bwd | 1.627 | unsupported | 1.620 | 1.0044 | n/a |
| GB300 `sm_103a` | CP16 zigzag per document, 4 docs, T=261376, H=4,
BF16 packed | ckpt † | 4.727 | unsupported | 4.706 | 1.0045 | n/a |
| GB300 `sm_103a` | CP16 zigzag per document, 4 docs, T=261376, H=16,
BF16 packed | fwd | 1.344 | unsupported | 1.333 | 1.0077 | n/a |
| GB300 `sm_103a` | CP16 zigzag per document, 4 docs, T=261376, H=16,
BF16 packed | bwd | 2.068 | unsupported | 2.074 | 0.9973 | n/a |
| GB300 `sm_103a` | CP16 zigzag per document, 4 docs, T=261376, H=16,
BF16 packed | ckpt † | 5.093 | unsupported | 5.092 | 1.0002 | n/a |
| GB300 `sm_103a` | CP16 zigzag per document, 4 docs, T=261376, H=64,
BF16 packed | fwd | 2.636 | unsupported | 2.638 | 0.9990 | n/a |
| GB300 `sm_103a` | CP16 zigzag per document, 4 docs, T=261376, H=64,
BF16 packed | bwd | 5.136 | unsupported | 5.143 | 0.9985 | n/a |
| GB300 `sm_103a` | CP16 zigzag per document, 4 docs, T=261376, H=64,
BF16 packed | ckpt | 9.612 | unsupported | 9.604 | 1.0008 | n/a |
| GB300 `sm_103a` | CP8 contiguous, 4 docs, T=261392, H=4, BF16 packed |
fwd † | 1.296 | 5.307 | 1.293 | 1.0019 | 4.1037 |
| GB300 `sm_103a` | CP8 contiguous, 4 docs, T=261392, H=4, BF16 packed |
bwd † | 1.697 | 6.814 | 1.703 | 0.9960 | 3.9999 |
| GB300 `sm_103a` | CP8 contiguous, 4 docs, T=261392, H=4, BF16 packed |
ckpt | 4.709 | 16.958 | 4.688 | 1.0045 | 3.6174 |
| GB300 `sm_103a` | CP8 contiguous, 4 docs, T=261392, H=16, BF16 packed
| fwd | 1.677 | 6.384 | 1.669 | 1.0046 | 3.8248 |
| GB300 `sm_103a` | CP8 contiguous, 4 docs, T=261392, H=16, BF16 packed
| bwd | 2.920 | 9.696 | 2.919 | 1.0003 | 3.3220 |
| GB300 `sm_103a` | CP8 contiguous, 4 docs, T=261392, H=16, BF16 packed
| ckpt | 5.944 | 22.179 | 5.944 | 1.0000 | 3.7314 |
| GB300 `sm_103a` | CP8 contiguous, 4 docs, T=261392, H=64, BF16 packed
| fwd | 4.451 | 11.330 | 4.454 | 0.9993 | 2.5435 |
| GB300 `sm_103a` | CP8 contiguous, 4 docs, T=261392, H=64, BF16 packed
| bwd | 9.035 | 22.577 | 9.029 | 1.0006 | 2.5004 |
| GB300 `sm_103a` | CP8 contiguous, 4 docs, T=261392, H=64, BF16 packed
| ckpt | 17.075 | 44.916 | 17.079 | 0.9998 | 2.6299 |
| GB300 `sm_103a` | CP8 zigzag, 4 docs, T=261392, H=4, BF16 packed | fwd
| 1.301 | 4.982 | 1.304 | 0.9980 | 3.8206 |
| GB300 `sm_103a` | CP8 zigzag, 4 docs, T=261392, H=4, BF16 packed | bwd
| 1.740 | 5.792 | 1.724 | 1.0091 | 3.3591 |
| GB300 `sm_103a` | CP8 zigzag, 4 docs, T=261392, H=4, BF16 packed |
ckpt | 4.751 | 15.359 | 4.750 | 1.0003 | 3.2337 |
| GB300 `sm_103a` | CP8 zigzag, 4 docs, T=261392, H=16, BF16 packed |
fwd | 1.762 | 6.178 | 1.762 | 1.0001 | 3.5073 |
| GB300 `sm_103a` | CP8 zigzag, 4 docs, T=261392, H=16, BF16 packed |
bwd | 3.045 | 8.999 | 3.037 | 1.0025 | 2.9630 |
| GB300 `sm_103a` | CP8 zigzag, 4 docs, T=261392, H=16, BF16 packed |
ckpt | 6.056 | 20.866 | 6.019 | 1.0063 | 3.4669 |
| GB300 `sm_103a` | CP8 zigzag, 4 docs, T=261392, H=64, BF16 packed |
fwd | 4.320 | 11.752 | 4.313 | 1.0016 | 2.7247 |
| GB300 `sm_103a` | CP8 zigzag, 4 docs, T=261392, H=64, BF16 packed |
bwd | 8.874 | 22.949 | 8.870 | 1.0005 | 2.5874 |
| GB300 `sm_103a` | CP8 zigzag, 4 docs, T=261392, H=64, BF16 packed |
ckpt | 16.700 | 45.891 | 16.698 | 1.0002 | 2.7483 |
| GB300 `sm_103a` | CP8 zigzag per document, 4 docs, T=261392, H=4, BF16
packed | fwd | 1.304 | unsupported | 1.295 | 1.0069 | n/a |
| GB300 `sm_103a` | CP8 zigzag per document, 4 docs, T=261392, H=4, BF16
packed | bwd † | 1.686 | unsupported | 1.692 | 0.9966 | n/a |
| GB300 `sm_103a` | CP8 zigzag per document, 4 docs, T=261392, H=4, BF16
packed | ckpt † | 4.728 | unsupported | 4.707 | 1.0044 | n/a |
| GB300 `sm_103a` | CP8 zigzag per document, 4 docs, T=261392, H=16,
BF16 packed | fwd | 1.717 | unsupported | 1.712 | 1.0032 | n/a |
| GB300 `sm_103a` | CP8 zigzag per document, 4 docs, T=261392, H=16,
BF16 packed | bwd | 3.010 | unsupported | 3.002 | 1.0026 | n/a |
| GB300 `sm_103a` | CP8 zigzag per document, 4 docs, T=261392, H=16,
BF16 packed | ckpt | 5.997 | unsupported | 6.005 | 0.9987 | n/a |
| GB300 `sm_103a` | CP8 zigzag per document, 4 docs, T=261392, H=64,
BF16 packed | fwd | 4.374 | unsupported | 4.373 | 1.0002 | n/a |
| GB300 `sm_103a` | CP8 zigzag per document, 4 docs, T=261392, H=64,
BF16 packed | bwd | 9.099 | unsupported | 9.111 | 0.9987 | n/a |
| GB300 `sm_103a` | CP8 zigzag per document, 4 docs, T=261392, H=64,
BF16 packed | ckpt | 17.080 | unsupported | 17.089 | 0.9995 | n/a |

The other Cake KDA variants are the deterministic single-rank package
(`flashinfer.experimental.cake_kda_det_train`, facade
`flashinfer.cake_kda_det_train`) and its KCP form
(`flashinfer.experimental.cake_kda_det_train_kcp`, facade
`flashinfer.cake_kda_det_train_kcp`), both on main, plus the
non-deterministic single-rank package (#8191) and its
activation-checkpoint hand-off (#8209), and the family covers `sm_100a`,
`sm_103a` and `sm_107a`.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added an experimental context-parallel KDA training API with
selectable deterministic and non-deterministic execution, supporting
forward and backward operations.
* Added support for compatible GPU architectures, along with build-time
kernel loading and workspace configuration.
* Added a distributed benchmark for comparing execution modes and
reporting timing, memory, and numerical results.
* **Documentation**
* Added usage guidance, supported configurations, and operational limits
for the experimental API.
* **Tests**
* Added coverage for API routing, compatibility, workspace behavior,
uploads, and benchmark/build configuration.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [b8f0b05](https://github.com/flashinfer-ai/flashinfer/commit/b8f0b05137f75b9f8d6670beb70982681c1de4cc)

- **作者**: eigen
- **时间**: 2026-11-01T21:55:34Z
- **提交信息**: perf(cake_tinygemm2_wgmma): faster sm_90a packed and accumulator programs, wider routing windows (#8232)

The packed programs read the bias in the MMA warps only, so the producer warp
issues its first copies without a pending global load; the packed and
accumulator programs load the weights with an L2 evict-first hint. Outputs stay
bit-identical to csrc/tinygemm2.cu. The H100 routing windows are re-measured for
the new programs: 903 of 1008 measured shapes now take a generated program.

### [d2d59e4](https://github.com/flashinfer-ai/flashinfer/commit/d2d59e47d545dfe7a5c05888b7bcd4fdd5af132c)

- **作者**: eigen
- **时间**: 2026-11-01T21:35:52Z
- **提交信息**: perf(cake_comm): QkvNormRopeExchangeOverlap SM107 two- and four-rank plans publish one readiness word per destination (#8231)

### [f13c875](https://github.com/flashinfer-ai/flashinfer/commit/f13c875eb230c544e4bec392d8b7632e3fdf23bb)

- **作者**: eigen
- **时间**: 2026-11-01T21:28:38Z
- **提交信息**: perf(cake_megamoe_topk_reduce): admit sm_107a (R200) with its own token tiers (#8229)

`cake_megamoe_topk_reduce` sums the top-k BF16 expert partials of a
MegaMoE layer into the BF16 output. It accumulates in FP32 in fixed
route order and rounds once (RN), so the result is bitwise equal to the
ordered FP32 reference. It picks a CTA shape by token count T ("token
tiers"). Until now it was built only for sm_100a and sm_103a, with tiers
of 4 CTA shapes. This PR adds sm_107a (Rubin R200, compute capability
10.7) with its own tiers of 3 new CTA shapes: 256x2 for T <= 64, 256x4
for T <= 212 and 64x8 above that. The new shapes add each BF16 partial
directly into the FP32 sum and load partials with an L2 evict-first
hint. The sm_100a/sm_103a tiers are unchanged (same SASS). This kernel
had no earlier sm_107a version, so each row is compared against
FlashInfer's two existing CuTeDSL TopkReduce implementations that run on
sm_107a:
- the Rubin (sm107) CuTeDSL MegaMoE TopkReduce, called with no
scores/indices (pre-weighted partials)
- the vendored SM100 CuTeDSL TopkReduce

Speedup = baseline latency / new latency (>1 = faster).

**R200, 216 SMs (driver 615.71.10), sm_107a, CUDA 13.4.** BF16, CUPTI
kernel time, cold L2, median over 4 processes x 20 rounds.

| T | C | new (us) | Rubin CuTeDSL (us) | speedup vs Rubin | SM100
CuTeDSL (us) | speedup vs SM100 |
|---:|---:|---:|---:|---:|---:|---:|
| 1 | 256 | 1.888 | 1.972 | 1.04x | 1.914 | 1.01x |
| 8 | 256 | 1.914 | 2.006 | 1.05x | 1.936 | 1.01x |
| 64 | 256 | 2.246 | 2.286 | 1.02x | 2.268 | 1.01x |
| 128 | 256 | 2.652 | 2.702 | 1.02x | 2.688 | 1.01x |
| 256 | 256 | 3.505 | 3.546 | 1.01x | 3.664 | 1.05x |
| 4096 | 4096 | 23.716 | 24.328 | 1.03x | 28.544 | 1.20x |

**R200, 212 SMs (driver 620.62), sm_107a, CUDA 13.4.** BF16, CUPTI
kernel time, cold L2, median over 4 processes x 20 rounds.

| T | C | new (us) | Rubin CuTeDSL (us) | speedup vs Rubin | SM100
CuTeDSL (us) | speedup vs SM100 |
|---:|---:|---:|---:|---:|---:|---:|
| 1 | 256 | 1.864 | 1.948 | 1.05x | 1.884 | 1.01x |
| 8 | 256 | 1.896 | 1.975 | 1.04x | 1.912 | 1.01x |
| 64 | 256 | 2.265 | 2.323 | 1.03x | 2.284 | 1.01x |
| 128 | 256 | 2.572 | 2.620 | 1.02x | 2.613 | 1.02x |
| 256 | 256 | 3.264 | 3.298 | 1.01x | 3.484 | 1.07x |
| 4096 | 4096 | 18.996 | 19.272 | 1.01x | 24.962 | 1.31x |

The same reducer ships for sm_100a and sm_103a (unchanged here) and now
for sm_107a, and its Cake variants are this single
BF16-partials/FP32-accumulate reducer, selected by token tiers per
architecture.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added MegaMoE top-k reduction support for SM107a (Rubin) GPUs, with
architecture-specific performance tiers.
* Added automatic SM107a module generation for builds targeting that
architecture with CUDA 13.0 or later.

* **Tests**
* Expanded GPU coverage for SM107a and special numeric values, including
subnormals, signed zeros, infinities, and NaNs.

* **Benchmarks**
* Added a CuTeDSL reducer baseline for comparisons using the same
workload as the native reducer.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [6b3e429](https://github.com/flashinfer-ai/flashinfer/commit/6b3e429ed5b3525c12d1a31522ef842e35b32b93)

- **作者**: eigen
- **时间**: 2026-11-01T21:12:03Z
- **提交信息**: perf(cake_kda): with grad, checkpoint hand-off for the non-deterministic Cake KDA autograd backend (#8209)

### [f066acc](https://github.com/flashinfer-ai/flashinfer/commit/f066acc5b3c6750b6052e668887665181a39a560)

- **作者**: eigen
- **时间**: 2026-11-01T21:09:45Z
- **提交信息**: perf(cake_dsa_indexer_det): sm_103a CTA-pair l6 scan programs walk key tiles in descending order (#8224)

### [43ecb3f](https://github.com/flashinfer-ai/flashinfer/commit/43ecb3f677975bce419e23b88a20d1feea4883b6)

- **作者**: eigen
- **时间**: 2026-11-01T20:44:57Z
- **提交信息**: perf(cake_kda): build every record of a rebound BF16 KDA prefill launch before the first kernel (#8228)

The Cake chunked KDA (Kimi Delta Attention) prefill behind
`flashinfer.recurrent_kda(..., backend="cake")` has 85 modules: 51 with
BF16 inputs and 34 with TF32 inputs. They come in a fused single-kernel
form (M128, M64 value split, N16 chain) and a split form (map prefix,
carry scan, affine apply), with FP32 or BF16 state and optional
checkpoint rows. This PR reduces host-side launch work in that prefill.
It touches only the prepared BF16-input path with FP32 state
(`flashinfer.prepare_bf16_kda_prefill`). It adds no module or generated
program and changes no kernel. The target case is a cached plan reused
with new output, checkpoint-row or state-pool tensors. Every layer of a
serving forward does this. For split-form launches on long sequences,
the old code submitted the index gather kernel first. Only then did it
re-encode the main kernel's descriptors and rebuild its launch record.
The GPU sat idle between the two kernels. Now the launch re-encodes
every part and builds every record first, starting with the main
kernel's. Then it launches them back to back. A rebuilt record also
reuses the argument export of every tensor that did not move. Only moved
tensors are exported again. Kernels, their arguments and their stream
order are unchanged. Outputs are bit-identical to FlashInfer main on
every measured row and in both timing modes, including under caller
CUDA-graph capture. The tables compare against the previous Cake version
on FlashInfer main. They report median latency per call in microseconds,
with a cold L2. Each table has 56 rows: 12 or 16 heads, no gate lower
bound or -5, and 14 sequence-length shapes. TIE means no difference
beyond the measurement band. The first table shows the serving pattern,
where every call rebinds the cached plan to new buffers. On B200, the 20
split-form rows are 1.04x to 1.22x faster and the other 36 rows TIE. For
example, 12 heads, no gate bound, 8192 tokens drops from 258.85 to
221.44 us (1.17x). On GB300, 12 of 46 counted rows are faster and 34
TIE, with ratios from 1.00x to 1.23x. For example, 12 heads, no gate
bound, 16384 tokens drops from 430.82 to 366.85 us (1.17x). Ten more
GB300 split-form rows are marked † and not counted, because the
FlashInfer main timing varied beyond the measurement band. They still
show the head faster, but we do not claim them. The second table shows
repeated calls on the same buffers, which use the plan-cache fast path.
All 56 rows TIE on both GPUs because this PR does not change that path.

B200: NVIDIA B200, sm_100a, 148 SMs, driver 580.82.07. GB300: NVIDIA
GB300, sm_103a, 152 SMs, driver 580.159.03. CUDA 13.4 (nvcc), PyTorch
2.14.1+cu130.

**Serving pattern: every call rebinds the cached plan to new buffers
(alternating buffer sets)** (microseconds per call)

| heads | gate lower bound | sequence lengths | B200 main | B200 this PR
| speedup | GB300 main | GB300 this PR | speedup |
|---:|---|---|---:|---:|---:|---:|---:|---:|
| 12 | none | 8192 | 258.85 | 221.44 | 1.17x | 289.68 | 218.05 | 1.33x †
|
| 12 | none | 16384 | 418.72 | 381.77 | 1.10x | 430.82 | 366.85 | 1.17x
|
| 12 | none | 32768 | 726.85 | 689.17 | 1.05x | 753.71 | 673.78 | 1.12x
|
| 12 | none | 2x8192 | 411.33 | 374.21 | 1.10x | 425.90 | 361.06 | 1.18x
† |
| 12 | none | 3000+13384 | 437.70 | 399.14 | 1.10x | 452.16 | 387.07 |
1.17x |
| 12 | none | 4x4096 | 234.53 | 234.46 | 1.00x TIE | 219.07 | 219.30 |
1.00x TIE |
| 12 | none | 2x(8128+64) | 416.64 | 379.28 | 1.10x | 432.05 | 368.03 |
1.17x |
| 12 | none | 8x(1024+64) | 108.64 | 108.94 | 1.00x TIE | 101.22 |
101.57 | 1.00x TIE |
| 12 | none | BS4 x T64 | 16.06 | 16.03 | 1.00x TIE | 15.25 | 15.26 |
1.00x TIE |
| 12 | none | BS16 x T64 | 22.85 | 22.75 | 1.00x TIE | 21.44 | 21.47 |
1.00x TIE |
| 12 | none | BS64 x T64 | 58.88 | 58.91 | 1.00x TIE | 54.62 | 54.46 |
1.00x TIE |
| 12 | none | BS16 x T128 | 36.54 | 36.45 | 1.00x TIE | 33.95 | 33.95 |
1.00x TIE |
| 12 | none | BS16 x T256 | 56.96 | 57.02 | 1.00x TIE | 52.26 | 52.19 |
1.00x TIE |
| 12 | none | BS16 x T(17..255) | 37.18 | 37.15 | 1.00x TIE | 35.33 |
35.33 | 1.00x TIE |
| 16 | none | 8192 | 307.52 | 270.72 | 1.14x | 325.66 | 264.45 | 1.23x †
|
| 16 | none | 16384 | 504.77 | 467.68 | 1.08x | 509.02 | 446.24 | 1.14x
|
| 16 | none | 32768 | 920.06 | 880.78 | 1.04x | 909.95 | 840.21 | 1.08x
|
| 16 | none | 2x8192 | 527.12 | 489.33 | 1.08x | 533.22 | 470.35 | 1.13x
|
| 16 | none | 3000+13384 | 516.53 | 478.75 | 1.08x | 524.58 | 461.25 |
1.14x |
| 16 | none | 4x4096 | 264.64 | 264.77 | 1.00x TIE | 246.13 | 246.11 |
1.00x TIE |
| 16 | none | 2x(8128+64) | 533.22 | 496.19 | 1.07x | 534.62 | 472.94 |
1.13x |
| 16 | none | 8x(1024+64) | 112.74 | 112.67 | 1.00x TIE | 105.38 |
105.28 | 1.00x TIE |
| 16 | none | BS4 x T64 | 16.38 | 16.35 | 1.00x TIE | 15.52 | 15.52 |
1.00x TIE |
| 16 | none | BS16 x T64 | 25.86 | 25.86 | 1.00x TIE | 23.39 | 23.46 |
1.00x TIE |
| 16 | none | BS64 x T64 | 69.66 | 69.70 | 1.00x TIE | 65.18 | 65.09 |
1.00x TIE |
| 16 | none | BS16 x T128 | 39.46 | 39.46 | 1.00x TIE | 35.55 | 35.55 |
1.00x TIE |
| 16 | none | BS16 x T256 | 67.20 | 67.20 | 1.00x TIE | 59.36 | 59.39 |
1.00x TIE |
| 16 | none | BS16 x T(17..255) | 42.11 | 42.08 | 1.00x TIE | 37.47 |
37.44 | 1.00x TIE |
| 12 | -5 | 8192 | 199.20 | 163.58 | 1.22x | 304.58 | 163.49 | 1.86x † |
| 12 | -5 | 16384 | 301.20 | 266.62 | 1.13x | 315.06 | 253.89 | 1.24x †
|
| 12 | -5 | 32768 | 496.32 | 460.45 | 1.08x | 499.81 | 447.70 | 1.12x |
| 12 | -5 | 2x8192 | 282.72 | 282.75 | 1.00x TIE | 326.94 | 251.63 |
1.30x † |
| 12 | -5 | 3000+13384 | 315.86 | 278.69 | 1.13x | 329.47 | 266.88 |
1.23x |
| 12 | -5 | 4x4096 | 193.47 | 193.44 | 1.00x TIE | 180.64 | 180.74 |
1.00x TIE |
| 12 | -5 | 2x(8128+64) | 357.76 | 357.79 | 1.00x TIE | 315.97 | 256.85
| 1.23x † |
| 12 | -5 | 8x(1024+64) | 112.38 | 112.42 | 1.00x TIE | 103.20 | 103.23
| 1.00x TIE |
| 12 | -5 | BS4 x T64 | 11.14 | 11.14 | 1.00x TIE | 10.62 | 10.59 |
1.00x TIE |
| 12 | -5 | BS16 x T64 | 27.87 | 27.87 | 1.00x TIE | 25.79 | 25.89 |
1.00x TIE |
| 12 | -5 | BS64 x T64 | 68.10 | 68.09 | 1.00x TIE | 63.36 | 63.39 |
1.00x TIE |
| 12 | -5 | BS16 x T128 | 33.31 | 33.31 | 1.00x TIE | 31.33 | 31.33 |
1.00x TIE |
| 12 | -5 | BS16 x T256 | 48.03 | 48.06 | 1.00x TIE | 44.96 | 44.96 |
1.00x TIE |
| 12 | -5 | BS16 x T(17..255) | 31.10 | 31.07 | 1.00x TIE | 29.22 |
29.28 | 1.00x TIE |
| 16 | -5 | 8192 | 233.71 | 197.62 | 1.18x | 337.12 | 199.66 | 1.69x † |
| 16 | -5 | 16384 | 362.75 | 328.10 | 1.11x | 397.74 | 319.15 | 1.25x †
|
| 16 | -5 | 32768 | 623.66 | 589.52 | 1.06x | 643.07 | 567.74 | 1.13x |
| 16 | -5 | 2x8192 | 286.16 | 286.75 | 1.00x TIE | 271.31 | 271.52 |
1.00x TIE |
| 16 | -5 | 3000+13384 | 382.00 | 343.79 | 1.11x | 447.07 | 337.17 |
1.33x † |
| 16 | -5 | 4x4096 | 206.72 | 206.78 | 1.00x TIE | 183.36 | 183.36 |
1.00x TIE |
| 16 | -5 | 2x(8128+64) | 357.22 | 357.25 | 1.00x TIE | 341.31 | 341.34
| 1.00x TIE |
| 16 | -5 | 8x(1024+64) | 89.70 | 89.76 | 1.00x TIE | 76.03 | 76.03 |
1.00x TIE |
| 16 | -5 | BS4 x T64 | 11.58 | 11.58 | 1.00x TIE | 10.94 | 10.94 |
1.00x TIE |
| 16 | -5 | BS16 x T64 | 24.38 | 24.42 | 1.00x TIE | 23.33 | 23.28 |
1.00x TIE |
| 16 | -5 | BS64 x T64 | 67.97 | 67.90 | 1.00x TIE | 63.90 | 63.92 |
1.00x TIE |
| 16 | -5 | BS16 x T128 | 34.46 | 34.46 | 1.00x TIE | 32.16 | 32.19 |
1.00x TIE |
| 16 | -5 | BS16 x T256 | 49.47 | 49.50 | 1.00x TIE | 45.92 | 45.92 |
1.00x TIE |
| 16 | -5 | BS16 x T(17..255) | 36.58 | 36.61 | 1.00x TIE | 34.11 |
34.14 | 1.00x TIE |

- B200: speedup 1.00x .. 1.22x over 56 counted rows (20 faster, 36 TIE:
no difference beyond the measurement band)
- GB300: speedup 1.00x .. 1.23x over 46 counted rows (12 faster, 34 TIE:
no difference beyond the measurement band; 10 more rows † not counted:
the FI main timing varied beyond the measurement band)

**Repeated calls on the same buffers (plan-cache fast path)**
(microseconds per call)

| heads | gate lower bound | sequence lengths | B200 main | B200 this PR
| speedup | GB300 main | GB300 this PR | speedup |
|---:|---|---|---:|---:|---:|---:|---:|---:|
| 12 | none | 8192 | 218.53 | 218.32 | 1.00x TIE | 211.90 | 212.16 |
1.00x TIE |
| 12 | none | 16384 | 377.47 | 376.89 | 1.00x TIE | 359.52 | 359.94 |
1.00x TIE |
| 12 | none | 32768 | 687.63 | 688.02 | 1.00x TIE | 646.18 | 646.08 |
1.00x TIE |
| 12 | none | 2x8192 | 369.76 | 369.46 | 1.00x TIE | 354.30 | 354.30 |
1.00x TIE |
| 12 | none | 3000+13384 | 394.85 | 394.72 | 1.00x TIE | 378.82 | 378.83
| 1.00x TIE |
| 12 | none | 4x4096 | 233.18 | 233.15 | 1.00x TIE | 219.23 | 219.07 |
1.00x TIE |
| 12 | none | 2x(8128+64) | 376.45 | 375.86 | 1.00x TIE | 361.87 |
361.36 | 1.00x TIE |
| 12 | none | 8x(1024+64) | 110.56 | 110.61 | 1.00x TIE | 102.11 |
102.05 | 1.00x TIE |
| 12 | none | BS4 x T64 | 16.06 | 16.06 | 1.00x TIE | 15.30 | 15.30 |
1.00x TIE |
| 12 | none | BS16 x T64 | 22.69 | 22.62 | 1.00x TIE | 21.47 | 21.47 |
1.00x TIE |
| 12 | none | BS64 x T64 | 58.69 | 58.66 | 1.00x TIE | 54.38 | 54.46 |
1.00x TIE |
| 12 | none | BS16 x T128 | 36.35 | 36.22 | 1.00x TIE | 33.95 | 33.95 |
1.00x TIE |
| 12 | none | BS16 x T256 | 56.19 | 56.19 | 1.00x TIE | 52.35 | 52.42 |
1.00x TIE |
| 12 | none | BS16 x T(17..255) | 37.06 | 37.06 | 1.00x TIE | 35.07 |
35.04 | 1.00x TIE |
| 16 | none | 8192 | 267.84 | 268.16 | 1.00x TIE | 258.35 | 258.53 |
1.00x TIE |
| 16 | none | 16384 | 465.86 | 466.40 | 1.00x TIE | 440.26 | 440.35 |
1.00x TIE |
| 16 | none | 32768 | 878.99 | 880.10 | 1.00x TIE | 821.38 | 820.70 |
1.00x TIE |
| 16 | none | 2x8192 | 486.72 | 487.14 | 1.00x TIE | 462.30 | 462.72 |
1.00x TIE |
| 16 | none | 3000+13384 | 476.30 | 476.19 | 1.00x TIE | 452.77 | 452.77
| 1.00x TIE |
| 16 | none | 4x4096 | 264.19 | 264.21 | 1.00x TIE | 246.69 | 246.91 |
1.00x TIE |
| 16 | none | 2x(8128+64) | 493.66 | 494.05 | 1.00x TIE | 467.46 |
468.16 | 1.00x TIE |
| 16 | none | 8x(1024+64) | 112.51 | 112.48 | 1.00x TIE | 103.78 |
103.58 | 1.00x TIE |
| 16 | none | BS4 x T64 | 16.29 | 16.29 | 1.00x TIE | 15.55 | 15.55 |
1.00x TIE |
| 16 | none | BS16 x T64 | 25.63 | 25.66 | 1.00x TIE | 23.26 | 23.28 |
1.00x TIE |
| 16 | none | BS64 x T64 | 69.02 | 69.09 | 1.00x TIE | 65.25 | 65.25 |
1.00x TIE |
| 16 | none | BS16 x T128 | 39.10 | 39.10 | 1.00x TIE | 35.33 | 35.36 |
1.00x TIE |
| 16 | none | BS16 x T256 | 66.27 | 66.27 | 1.00x TIE | 59.26 | 59.39 |
1.00x TIE |
| 16 | none | BS16 x T(17..255) | 41.34 | 41.41 | 1.00x TIE | 37.34 |
37.34 | 1.00x TIE |
| 12 | -5 | 8192 | 159.42 | 159.55 | 1.00x TIE | 162.38 | 153.98 | 1.05x
TIE |
| 12 | -5 | 16384 | 260.11 | 260.64 | 1.00x TIE | 252.85 | 248.48 |
1.02x TIE |
| 12 | -5 | 32768 | 452.93 | 451.92 | 1.00x TIE | 435.23 | 430.74 |
1.01x TIE |
| 12 | -5 | 2x8192 | 283.10 | 283.01 | 1.00x TIE | 255.33 | 247.63 |
1.03x TIE |
| 12 | -5 | 3000+13384 | 273.34 | 273.28 | 1.00x TIE | 263.02 | 264.43 |
0.99x TIE |
| 12 | -5 | 4x4096 | 192.03 | 192.03 | 1.00x TIE | 179.36 | 179.33 |
1.00x TIE |
| 12 | -5 | 2x(8128+64) | 355.78 | 355.74 | 1.00x TIE | 256.99 | 253.28
| 1.01x TIE |
| 12 | -5 | 8x(1024+64) | 110.82 | 110.82 | 1.00x TIE | 103.07 | 103.10
| 1.00x TIE |
| 12 | -5 | BS4 x T64 | 11.17 | 11.17 | 1.00x TIE | 10.62 | 10.62 |
1.00x TIE |
| 12 | -5 | BS16 x T64 | 27.62 | 27.58 | 1.00x TIE | 25.92 | 25.92 |
1.00x TIE |
| 12 | -5 | BS64 x T64 | 67.62 | 67.58 | 1.00x TIE | 63.17 | 63.04 |
1.00x TIE |
| 12 | -5 | BS16 x T128 | 32.83 | 32.86 | 1.00x TIE | 31.71 | 31.71 |
1.00x TIE |
| 12 | -5 | BS16 x T256 | 47.49 | 47.49 | 1.00x TIE | 44.64 | 44.64 |
1.00x TIE |
| 12 | -5 | BS16 x T(17..255) | 30.69 | 30.66 | 1.00x TIE | 29.41 |
29.34 | 1.00x TIE |
| 16 | -5 | 8192 | 195.01 | 195.18 | 1.00x TIE | 187.25 | 188.80 | 0.99x
TIE |
| 16 | -5 | 16384 | 321.98 | 321.52 | 1.00x TIE | 307.92 | 308.61 |
1.00x TIE |
| 16 | -5 | 32768 | 578.69 | 579.50 | 1.00x TIE | 551.06 | 551.94 |
1.00x TIE |
| 16 | -5 | 2x8192 | 286.78 | 286.66 | 1.00x TIE | 275.98 | 275.46 |
1.00x TIE |
| 16 | -5 | 3000+13384 | 339.84 | 338.98 | 1.00x TIE | 319.76 | 320.90 |
1.00x TIE |
| 16 | -5 | 4x4096 | 205.44 | 205.47 | 1.00x TIE | 183.14 | 183.17 |
1.00x TIE |
| 16 | -5 | 2x(8128+64) | 357.25 | 357.28 | 1.00x TIE | 342.72 | 342.72
| 1.00x TIE |
| 16 | -5 | 8x(1024+64) | 89.06 | 89.06 | 1.00x TIE | 77.15 | 77.54 |
1.00x TIE |
| 16 | -5 | BS4 x T64 | 11.58 | 11.58 | 1.00x TIE | 10.88 | 10.88 |
1.00x TIE |
| 16 | -5 | BS16 x T64 | 24.29 | 24.32 | 1.00x TIE | 23.01 | 22.98 |
1.00x TIE |
| 16 | -5 | BS64 x T64 | 67.17 | 67.14 | 1.00x TIE | 63.39 | 63.50 |
1.00x TIE |
| 16 | -5 | BS16 x T128 | 34.11 | 34.11 | 1.00x TIE | 32.19 | 32.19 |
1.00x TIE |
| 16 | -5 | BS16 x T256 | 48.90 | 48.93 | 1.00x TIE | 45.79 | 45.86 |
1.00x TIE |
| 16 | -5 | BS16 x T(17..255) | 36.26 | 36.26 | 1.00x TIE | 33.54 |
33.54 | 1.00x TIE |

- B200: speedup 1.00x .. 1.00x over 56 counted rows (0 faster, 56 TIE:
no difference beyond the measurement band)
- GB300: speedup 0.99x .. 1.05x over 56 counted rows (0 faster, 56 TIE:
no difference beyond the measurement band)

The other Cake variants keep their behavior: the TF32-input modules, the
BF16-state forms and the fused single-kernel launches. The family ships
on sm_100a and sm_103a, and this PR changes the host launch order on
both.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved staged kernel launches so dependent operations use updated
tensor data, helping ensure results reflect the current inputs.
* **Performance**
* Reuses compatible tensor exports across launch stages, reducing
repeated preparation work.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery Huang <averyh@nvidia.com>

### [443ee13](https://github.com/flashinfer-ai/flashinfer/commit/443ee13db88a50cc54e76404cdc53893fdbb4171)

- **作者**: eigen
- **时间**: 2026-11-01T19:56:35Z
- **提交信息**: cake_gdn: run unshipped SM107 DV-split prefill keys on their full-DV records (up to 3.01x) (#8225)

`chunk_gated_delta_rule(backend="cake_gdn")` runs the Cake GDN non-CP
prefill. Cake is opt-in. `backend="auto"` never selects it, so default
users see no change. On SM 10.7 (R200, sm_107a), the resolver picks the
DV-split schedule whenever 2 * num_seqs * max(Hq, Hv) fits in the 212
active clusters. The limit is 148 clusters on sm_100a and 160 on
sm_103a. As a result, sm_107a sends some keys to DV-split that sm_100a
runs on full-DV. The non-gatepipe4 DV-split schedules ship no record for
FP16 I/O with FP32 initial and final state, ungated, where Hv/Hq and Hv
are both not powers of two (geometry key (-1, 0, -1)). These calls, for
example Hq2/Hv6 x 16 sequences, raised `CakeGDNUnsupportedError` on
sm_107a only. With this PR, if the DV-split schedule does not ship a
prefill key on sm_107a, the call runs the already-shipped full-DV record
for the same key. This applies only to calls with no checkpoints, packed
state, more than one chunk and no low-precision state. The change also
admits two groups that failed on every architecture before: the
smaller-num_seqs keys of the same contract, and the no-state Hq16/Hv64
single sequence with BF16 or FP16 I/O. The PR adds no kernel source and
no records. Keys that have a DV-split record are unchanged, and sm_100a
and sm_103a resolve exactly as before. Outputs match the reference
within the existing tolerances and are bitwise equal to the native
non-CP FlashInfer kernel.

| Shape | Cake (µs) | `backend="auto"` (µs) | Speedup |
|---|---:|---:|---:|
| Hq1/Hv3, 1 seq × 200 (FP16, initial+final state, ungated) | 18.54 |
39.20 | 2.11x |
| Hq1/Hv3, 35 seqs of 64-302 tokens | 22.81 | 29.20 | 1.28x |
| Hq2/Hv6, 16 × 128 | 17.24 | 22.34 | 1.30x |
| Hq2/Hv6, 1 × 1000 | 41.19 | 52.42 | 1.27x |
| Hq8/Hv24, seqs [500, 70] | 27.02 | 81.23 | 3.01x |
| Hq16/Hv48, seqs [256, 190] | 21.68 | 26.24 | 1.21x |
| Hq3/Hv9, 11 × 128 | 17.51 | 22.46 | 1.28x |
| Hq16/Hv64 BF16, no state, gated, 1 × 300 | 19.54 | 20.08 | 1.03x |
| Hq16/Hv64 FP16, no state, gated, 1 × 300 | 19.56 | 20.39 | 1.04x |
| Hq16/Hv64 FP16, no state, gated, 1 × 4096 | 139.42 | 132.19 | 0.95x |

Measured on NVIDIA VR200 (R200), sm_107a, 212 SMs, driver 620.43, with
the CUDA 13.4 toolchain (torch 2.14.1+cu130). Times are the median of
200 CUDA-graph replays with a cold L2. The p10-p90 spread is about ±0.2
µs per row. Speedup = `backend="auto"` / Cake, so a value above 1 means
Cake is faster. Rows 1-7 use FP16 I/O with FP32 initial and final state
and are ungated. Rows 8-10 have no state and are gated. Before this PR,
every row raised `CakeGDNUnsupportedError` with `backend="cake_gdn"`. On
the ungated rows, `backend="auto"` builds the unit g/beta tensors on
every call, and its times include that cost. On rows 1, 4 and 5, auto
selects its chunk-parallel kernel. The 4096-token no-state row is 5%
slower than auto. Cake is opt-in, so auto users are not affected.

This Cake GDN prefill also ships records for BF16 and FP16 I/O with FP32
or BF16 state, on both the DV-split and full-DV routes, for sm_100a,
sm_103a and sm_107a. This PR changes only how sm_107a resolves routes.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

- **New Features**
- On supported SM107 hardware, eligible prefill workloads can now use a
compatible full-DV schedule when no matching DV-split schedule is
available. This expands coverage for certain input geometries while
preserving existing DV-split routing where a matching schedule exists.
Unsupported geometries and configurations remain unsupported.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [91a3ea8](https://github.com/flashinfer-ai/flashinfer/commit/91a3ea848d37a0c70330dddf3ffbfa50345775f5)

- **作者**: eigen
- **时间**: 2026-11-01T19:42:02Z
- **提交信息**: perf(cake_fmha): faster B200 FP8 context split-KV launches with two splits (#8202)

### [5beccd5](https://github.com/flashinfer-ai/flashinfer/commit/5beccd527d3e6c7a5b3bcf0e33d1a69e6d6f11f5)

- **作者**: eigen
- **时间**: 2026-11-01T19:41:45Z
- **提交信息**: perf(cake_moe_grouped_gemm): finish the unordered k512 wgrad tail by whole rows and reduce it in lane pairs (#8198)

### [47879e4](https://github.com/flashinfer-ai/flashinfer/commit/47879e4bc79827368e433a0406a1cf40bd1ed386)

- **作者**: eigen
- **时间**: 2026-11-01T19:41:26Z
- **提交信息**: feat(cake_kda): with grad, add non-deterministic Cake KDA chunked autograd backend (#8191)

### [8f712aa](https://github.com/flashinfer-ai/flashinfer/commit/8f712aa5c56d555233042076d686ebfb2f9c1589)

- **作者**: eigen
- **时间**: 2026-11-01T19:02:34Z
- **提交信息**: perf(cake_deepgemm_mega_mhc): sm_107a raw launches at 129-384 and 833-1023 on tailpipe (#8223)

`flashinfer.mega_mhc` (`prepare_mega_mhc`) runs the fused
manifold-constrained hyper-connection (mHC) inference step. FlashInfer
main ships 43 per-arch programs for it:

- 14 hidden-5120 FP8-E4M3-output programs on sm_100a and sm_103a.
- For hidden 4096, five programs on each of sm_107a, sm_100a and
sm_103a: BF16 output, its tailpipe twin, its weight-staging tailpipe
twin, FP8 group-128 output and NVFP4 output.
- Four sm_107a-only tailpipe and weight-staging tailpipe forms of the
FP8 group-128 and NVFP4 variants.
- Three sm_107a-only FP8 group-128 UE8M0-scale-mode programs (plain,
tailpipe and weight-staging tailpipe).
- One sm_107a-only fast-division form of the plain FP8 group-128
program.
- Six sm_107a-only fast-chain forms: one each of the BF16-output
tailpipe program, the plain FP8 group-128 program (raw scale mode), the
plain FP8 group-128 program (UE8M0 scale mode), the FP8 group-128
weight-staging tailpipe program (raw scale mode), the FP8 group-128
UE8M0 tailpipe program and the NVFP4 tailpipe program.

This PR adds no program. It changes only sm_107a non-deterministic
routes, which now go to an existing program. The existing programs do
not change.

- **FP8 group-128 tailpipe program (existing).** Non-deterministic
raw-scale-mode launches of the plain regime at T = 129–384 and T =
833–1023 move to it. Before this PR, T = 129–192 and T = 833–1023 used
the plain FP8 group-128 program, and T = 193–384 used the fast-chain
form of the plain FP8 group-128 program. Main already uses the tailpipe
program for these launches in the deterministic mode at T = 16–47 and T
= 128–1024. It also uses it for non-deterministic launches at T =
385–832, where the host rule picks it.

Every other launch keeps the program main dispatches. No sm_100a or
sm_103a launch changes. The UE8M0 scale mode and the deterministic mode
do not change.

Each moved launch keeps its split count and its launch: 64 splits at T =
129–192, 32 splits at T = 193–384 and 13 splits at T = 833–1023. A tail
form reorders loads, not arithmetic, so outputs are bitwise identical to
main and batch invariance does not change.

The baseline is the previous Cake version of the kernel, which is what
FlashInfer main dispatches today. A is the program main dispatches, and
B is the program this PR dispatches. Speedup = A / B. Both sides run
through FlashInfer's loader on the same GPU, with the same inputs, in
one process. Both use programmatic dependent launch, as main already
does. The tables show medians. Each table lists the owner shapes first,
then the changed rows.

- FP8 group-128 tailpipe, raw scales, non-deterministic, T = 129–192 (64
splits): 1.033–1.039× on the 208-SM GPU and 1.033–1.056× on the 216-SM
GPU.
- FP8 group-128 tailpipe, raw scales, non-deterministic, T = 193–384 (32
splits): 1.020–1.034× on the 208-SM GPU and 1.026–1.033× on the 216-SM
GPU. The owner shape T = 256 is one of these changed rows: 1.033× on the
208-SM GPU.
- FP8 group-128 tailpipe, raw scales, non-deterministic, T = 833–1023
(13 splits): 1.044–1.075× on the 208-SM GPU and 1.039–1.079× on the
216-SM GPU.
- Rows that keep their program: 0.999–1.003× on the 208-SM GPU and
0.998–1.001× on the 216-SM GPU.

**FP8 group-128 output, raw scales, non-deterministic, hidden 4096.
NVIDIA R200 (sm_107a), 208 SMs, driver 615.71.10, CUDA 13.4 (nvcc
13.4.92), SM clock 2390–2413 MHz.**

| T (tokens) | Program dispatched by this PR | Splits | Previous, µs (A)
| This PR, µs (B) | Speedup (A / B) |
|---:|:--|---:|---:|---:|---:|
| 1 | FP8 group-128 | 64 | 9.224 | 9.216 | 1.001× |
| 4 | FP8 group-128 | 64 | 9.408 | 9.408 | 1.000× |
| 8 | FP8 group-128 | 64 | 9.407 | 9.408 | 1.000× |
| 16 | FP8 group-128 | 64 | 9.504 | 9.480 | 1.003× |
| 32 | FP8 group-128 | 64 | 9.536 | 9.536 | 1.000× |
| 64 | FP8 group-128 | 64 | 9.856 | 9.856 | 1.000× |
| 128 | FP8 group-128 | 64 | 10.432 | 10.432 | 1.000× |
| 256 | tailpipe | 32 | 12.032 | 11.648 | 1.033× |
| 512 | tailpipe | 22 | 13.968 | 13.983 | 0.999× |
| 1024 | FP8 group-128 | 13 | 19.840 | 19.856 | 0.999× |
| 2048 | tailpipe | 13 | 30.112 | 30.112 | 1.000× |
| 4096 | tailpipe (weight staged) | 16 | 57.856 | 57.856 | 1.000× |
| 8192 | tailpipe (weight staged) | 8 | 114.047 | 114.079 | 1.000× |
| 129 | tailpipe | 64 | 11.136 | 10.776 | 1.033× |
| 160 | tailpipe | 64 | 11.144 | 10.768 | 1.035× |
| 192 | tailpipe | 64 | 11.488 | 11.056 | 1.039× |
| 193 | tailpipe | 32 | 11.776 | 11.416 | 1.032× |
| 194 | tailpipe | 32 | 11.735 | 11.352 | 1.034× |
| 224 | tailpipe | 32 | 11.872 | 11.552 | 1.028× |
| 288 | tailpipe | 32 | 12.256 | 11.920 | 1.028× |
| 320 | tailpipe | 32 | 12.448 | 12.064 | 1.032× |
| 352 | tailpipe | 32 | 12.800 | 12.512 | 1.023× |
| 383 | tailpipe | 32 | 12.800 | 12.543 | 1.020× |
| 384 | tailpipe | 32 | 12.800 | 12.512 | 1.023× |
| 833 | tailpipe | 13 | 17.984 | 17.192 | 1.046× |
| 834 | tailpipe | 13 | 18.008 | 17.120 | 1.052× |
| 864 | tailpipe | 13 | 18.176 | 17.376 | 1.046× |
| 896 | tailpipe | 13 | 18.016 | 17.192 | 1.048× |
| 928 | tailpipe | 13 | 18.240 | 17.472 | 1.044× |
| 960 | tailpipe | 13 | 20.096 | 18.752 | 1.072× |
| 976 | tailpipe | 13 | 20.352 | 19.040 | 1.069× |
| 992 | tailpipe | 13 | 21.000 | 19.536 | 1.075× |
| 1008 | tailpipe | 13 | 21.088 | 19.624 | 1.075× |
| 1023 | tailpipe | 13 | 21.544 | 20.048 | 1.075× |

**FP8 group-128 output, raw scales, non-deterministic, hidden 4096.
NVIDIA R200 (sm_107a), 216 SMs, driver 615.71.10, CUDA 13.4 (nvcc
13.4.92), SM clock 2383–2412 MHz.**

| T (tokens) | Program dispatched by this PR | Splits | Previous, µs (A)
| This PR, µs (B) | Speedup (A / B) |
|---:|:--|---:|---:|---:|---:|
| 1 | FP8 group-128 | 64 | 9.272 | 9.280 | 0.999× |
| 4 | FP8 group-128 | 64 | 9.440 | 9.432 | 1.001× |
| 8 | FP8 group-128 | 64 | 9.568 | 9.560 | 1.001× |
| 16 | FP8 group-128 | 64 | 9.472 | 9.480 | 0.999× |
| 32 | FP8 group-128 | 64 | 9.544 | 9.537 | 1.001× |
| 64 | FP8 group-128 | 64 | 9.832 | 9.824 | 1.001× |
| 128 | FP8 group-128 | 64 | 10.376 | 10.384 | 0.999× |
| 256 | tailpipe | 32 | 12.032 | 11.680 | 1.030× |
| 512 | tailpipe | 22 | 13.864 | 13.888 | 0.998× |
| 1024 | FP8 group-128 | 13 | 19.392 | 19.400 | 1.000× |
| 2048 | tailpipe | 13 | 29.360 | 29.352 | 1.000× |
| 4096 | tailpipe (weight staged) | 16 | 56.064 | 56.056 | 1.000× |
| 8192 | tailpipe (weight staged) | 8 | 111.696 | 111.792 | 0.999× |
| 129 | tailpipe | 64 | 10.944 | 10.592 | 1.033× |
| 160 | tailpipe | 64 | 11.009 | 10.632 | 1.035× |
| 192 | tailpipe | 64 | 11.456 | 10.848 | 1.056× |
| 193 | tailpipe | 32 | 11.663 | 11.296 | 1.033× |
| 194 | tailpipe | 32 | 11.696 | 11.360 | 1.030× |
| 224 | tailpipe | 32 | 11.808 | 11.488 | 1.028× |
| 288 | tailpipe | 32 | 12.288 | 11.904 | 1.032× |
| 320 | tailpipe | 32 | 12.576 | 12.224 | 1.029× |
| 352 | tailpipe | 32 | 12.664 | 12.304 | 1.029× |
| 383 | tailpipe | 32 | 12.800 | 12.480 | 1.026× |
| 384 | tailpipe | 32 | 12.800 | 12.480 | 1.026× |
| 833 | tailpipe | 13 | 17.824 | 17.088 | 1.043× |
| 834 | tailpipe | 13 | 17.792 | 17.048 | 1.044× |
| 864 | tailpipe | 13 | 17.696 | 17.024 | 1.039× |
| 896 | tailpipe | 13 | 17.792 | 17.120 | 1.039× |
| 928 | tailpipe | 13 | 18.016 | 17.312 | 1.041× |
| 960 | tailpipe | 13 | 18.081 | 17.376 | 1.041× |
| 976 | tailpipe | 13 | 20.064 | 18.720 | 1.072× |
| 992 | tailpipe | 13 | 20.384 | 19.032 | 1.071× |
| 1008 | tailpipe | 13 | 20.984 | 19.520 | 1.075× |
| 1023 | tailpipe | 13 | 21.408 | 19.840 | 1.079× |

The kernel's other Cake variants (the BF16, NVFP4 and FP8 group-128
UE8M0 outputs, the deterministic and non-deterministic modes, and hidden
5120) are unchanged, and so is its arch coverage (sm_100a, sm_103a and
sm_107a).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* Expanded raw FP8 routing coverage for BF16 workloads across additional
token-count ranges and non-deterministic launches.
* Updated route selection so matching raw tailpipe routes take
precedence over fast-chain programs.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery Huang <averyh@nvidia.com>

### [27ccbb4](https://github.com/flashinfer-ai/flashinfer/commit/27ccbb48e2e53c9991b5078e37ef8ee1b2f08f76)

- **作者**: eigen
- **时间**: 2026-11-01T18:48:12Z
- **提交信息**: fix(cake_lm_head_det_loss): correct selective activation checkpointing of the det entries (#8222)

## Summary

Selective activation checkpointing (SAC) uses
`torch.utils.checkpoint(..., use_reentrant=False,
context_fn=create_selective_checkpoint_contexts(policy))`. A caching
dispatch mode records the operators of the checkpointed forward and
replays them by position in the recomputation, so both passes must run
the same operators. On main, the det entries of
`flashinfer.experimental.cake_lm_head_det_loss` did not. Their backward
failed with "... encountered during backward but not found in storage".
There were two causes:

- **The "auto" gradient placement.** The checkpointed forward of the
loss entry computed only the loss, but the recomputation ran the fused
forward. Every loss form failed under SAC.
- **State that only one pass forms or finds.** Bindings are keyed on
input addresses, and per-thread state is formed on first use. The
recomputation runs on the autograd engine's thread. A binding that one
pass finds and the other misses, or state formed in only one pass, adds
operators to that pass. This broke the log-probability entries (default,
budget and `keep_logits` forms) when their input was formed inside the
checkpointed region and the recomputation moved it. It also broke the
budget and `keep_logits` forms on the first use in a process or thread.

There was also a separate failure. A policy that saves every operator
(MUST_SAVE for all ops) saw the entries write in place to their own
buffers. The loss and log-probability entries failed, most of them with
torch's "Tensor cached during selective activation checkpoint has been
mutated" check. They now pass.

## Fix

Every det autograd Function covers loss, log-probability (default,
budget and `keep_logits`) and candidate support. While a SAC mode is
active, the forward of each one now runs again with all active torch
dispatch modes popped. The entry then runs only its own operators and
behaves as under a plain non-reentrant checkpoint. For the loss with
"auto" placement, the checkpointed forward computes only the loss, and
the recomputation forms the gradients once and hands them to the
backward. The loss entry now checks for the SAC mode even when it forms
no gradients.

State that belongs to no call is also formed outside active dispatch
modes. This is the process-wide constant cells and the calling thread's
valid-row constant and count cell. A first use inside a recomputation
therefore adds no operators.

Effects on other dispatch modes:

- While a det entry runs under SAC, every mode on the stack is popped,
not only the checkpoint's. This includes user modes such as
`FlopCounterMode`, which then do not see the entry's operators.
- A tracing mode (`FakeTensorMode`, a `torch.compile` trace) then gets
real launches on fake inputs and fails loudly rather than silently.
- Outside SAC, nothing changes.
- The private API `torch.utils._python_dispatch._disable_current_modes`
is looked up defensively. If it is missing, or the mode stack, the
dispatch-mode count or the SAC mode classes are missing, the entries
behave as on main.

Outputs are unchanged. The support entry already passed on main because
its bindings are not keyed on the input address; we wrap it for
uniformity. The README describes the behaviour under SAC.

Files: `README.md`, `cake_backend.py`, `cake_backend_opt_in.py`,
`cake_support.py`, `tests/experimental/test_cake_lm_head_loss.py` (5
files, +610/-30).

## Correctness

Each cell shows main → this PR. "Bitwise" means that loss, dHin and dW
match the uncheckpointed default step bit for bit.

| case | loss (all forms) | log-prob (default, budget, `keep_logits`) |
support |
|---|---|---|---|
| plain non-reentrant checkpoint | runs† → bitwise | runs† → bitwise | –
→ bitwise |
| SAC, PREFER_RECOMPUTE | fails with "auto", runs† with "forward" →
bitwise | runs† → bitwise | – → bitwise |
| SAC, MUST_SAVE mm | fails with "auto", runs† with "forward" → bitwise
| runs† → bitwise | – → bitwise |
| SAC, MUST_SAVE all ops | fails ("cached tensor mutated"; CE budget:
`aten.ge.Scalar`) → bitwise | fails ("cached tensor mutated") → bitwise
| bitwise → bitwise |
| X = mm(Hin, P) inside the region, plain step before each SAC step |
fails (`aten.view.dtype`, `aten.ge.Scalar`) → bitwise | default and
budget fail (`aten.view.default`); opt-in `keep_logits` fails 1 of 2;
backend keep entry passes → bitwise | bitwise → bitwise |
| same, with a user `TorchDispatchMode` around forward and backward |
fails → bitwise | as the row above → bitwise | bitwise → bitwise |
| non-reentrant checkpoint nested inside SAC | bitwise → bitwise |
bitwise → bitwise | bitwise → bitwise |
| fresh process, first call | – → bitwise | default/budget hold specs
and `keep_logits` fail → bitwise | – → bitwise |

† Main ran these rows in the A/B below. We did not compare them bitwise
on main.
– Not measured on main.

- The X-inside-region, user-mode, nested and MUST_SAVE-all cells for
main come from probes with 2 attempts per cell and "auto" placement.
"Fails" means both attempts failed unless the cell says otherwise. B200
and GB300 give the same pass/fail counts in every cell.
- The other loss forms (policy, CE fast, policy budget) fail on main in
the same way as CE and CE budget.
- This PR: 352/352 probe rows are bitwise on each GPU, across 10
entries. The probe covers the checkpoint, SAC PREFER_RECOMPUTE,
MUST_SAVE mm and MUST_SAVE all, the user-mode cases and the three hold
cases.
- Fresh-process first calls on this PR: 31/31 bitwise on each GPU,
including support and every hold spec.

## Tests

Environment: B200 (sm_100a) and GB300 (sm_103a), x86_64 / aarch64, torch
2.14.1+cu130, nvcc 13.4.92, Python 3.12.15.

| | B200 (sm_100a) | GB300 (sm_103a) |
|---|---|---|
| det GPU test files, this PR | 809 passed / 0 failed / 2 skipped | 810
passed / 0 failed / 1 skipped |
| det GPU test files, main | 744 passed / 0 failed / 2 skipped | 745
passed / 0 failed / 1 skipped |
| new tests on this PR | 65/65 pass | 65/65 pass |
| new tests on main (fails-before) | 39 fail / 26 pass | 39 fail / 26
pass |
| pre-commit 4.2.0 (changed files) | clean, 0 changes | clean, 0 changes
|

- The new tests are those selected by `-k "selective_checkpoint or
dispatch_mode or logprob_keep_step"`.
- The same tests skip on both sides.
- The new tests cover:
- the region-input test, with a plain step before each SAC step, with
and without a user mode, for the log-prob default, budget and both keep
entries
- a `selective_save_all` kind in the loss and log-prob device step tests
and in the keep step test
  - fresh-process first calls

## Cost

We traced the default uncheckpointed path line by line on B200 and
GB300:

- **Loss:** the forward and step (CE at T = 16231, policy at T = 32463)
execute exactly main's lines and calls.
- **Log-probability:** the forward and step (T = 1 and T = 128) execute
one more line and one more C call
(`torch._C._autograd._top_saved_tensors_default_hooks`). This is the
saved-tensor-hooks check that detects SAC. Main's log-probability
Function has no hooks check to reuse. The A/B cannot measure the cost:
the plain log-prob rows read 0.996-1.003.

**A/B method:**

- Main and this PR run in alternating order across processes. Each
process runs 2 interleaved in-process rounds of 3 steps per row.
- Each value is forward+backward wall time, taken as the median of the
per-round medians.
- There are 8 rounds for the log-prob budget, CE loss and CE loss budget
rows, and 4 for the log-prob and `keep_logits` rows.
- Shape: T = 12289, H = 6144, V = 154880, chunk 4096. The region is
`entry(mm(Hin, P), W)`.
- "SAC mm" means MUST_SAVE mm; "SAC rc" means PREFER_RECOMPUTE.

| entry | case / placement | B200 main (ms) | B200 PR (ms) | B200
PR/main | GB300 main (ms) | GB300 PR (ms) | GB300 PR/main |
|---|---|---|---|---|---|---|---|
| log-prob | ckpt / auto | 83.98 | 83.98 | 1.0000 | 66.32 | 66.47 |
1.0023 |
| log-prob | plain / auto | 67.77 | 67.52 | 0.9962 | 52.93 | 53.06 |
1.0024 |
| log-prob | SAC mm / auto | 83.41 | 83.61 | 1.0024 | 65.89 | 65.84 |
0.9993 |
| log-prob | SAC rc / auto | 84.20 | 84.32 | 1.0014 | 66.51 | 66.48 |
0.9995 |
| log-prob budget | ckpt / auto | 86.38 | 86.30 | 0.9991 | 68.01 | 67.93
| 0.9988 |
| log-prob budget | plain / auto | 69.36 | 69.43 | 1.0009 | 54.60 |
54.76 | 1.0030 |
| log-prob budget | SAC mm / auto | 85.43 | 85.36 | 0.9992 | 67.63 |
67.48 | 0.9977 |
| log-prob budget | SAC rc / auto | 86.30 | 85.94 | 0.9958 | 68.05 |
67.82 | 0.9966 |
| log-prob `keep_logits` | ckpt / auto | 70.00 | 70.26 | 1.0037 | 54.72
| 55.20 | 1.0089 |
| log-prob `keep_logits` | plain / auto | 53.06 | 53.17 | 1.0021 | 41.17
| 40.99 | 0.9958 |
| log-prob `keep_logits` | SAC mm / auto | 69.45 | 69.22 | 0.9966 |
54.53 | 54.50 | 0.9994 |
| log-prob `keep_logits` | SAC rc / auto | 70.08 | 70.00 | 0.9989 |
55.09 | 55.11 | 1.0003 |
| CE loss | ckpt / auto | 69.41 | 70.14 | 1.0105 | 54.70 | 54.54 |
0.9970 |
| CE loss | ckpt / forward | 99.45 | 99.33 | 0.9988 | 76.92 | 77.06 |
1.0018 |
| CE loss | plain / auto | 53.13 | 52.96 | 0.9967 | 41.48 | 41.21 |
0.9934 |
| CE loss | plain / forward | 53.09 | 53.07 | 0.9996 | 41.23 | 41.18 |
0.9988 |
| CE loss | SAC mm / auto | fails | 69.00 | - | fails | 53.84 | - |
| CE loss | SAC mm / forward | 98.83 | 99.07 | 1.0024 | 76.91 | 76.36 |
0.9929 |
| CE loss | SAC rc / auto | fails | 69.85 | - | fails | 54.55 | - |
| CE loss | SAC rc / forward | 99.24 | 99.61 | 1.0037 | 77.08 | 77.23 |
1.0020 |
| CE loss budget | ckpt / auto | 72.20 | 72.13 | 0.9991 | 56.18 | 56.30
| 1.0022 |
| CE loss budget | ckpt / forward | 105.80 | 105.92 | 1.0012 | 81.94 |
82.29 | 1.0042 |
| CE loss budget | plain / auto | 55.09 | 55.10 | 1.0002 | 42.46 | 42.76
| 1.0071 |
| CE loss budget | plain / forward | 55.20 | 55.33 | 1.0023 | 42.57 |
42.54 | 0.9992 |
| CE loss budget | SAC mm / auto | fails | 71.52 | - | fails | 55.43 | -
|
| CE loss budget | SAC mm / forward | 104.99 | 105.05 | 1.0006 | 81.04 |
81.24 | 1.0025 |
| CE loss budget | SAC rc / auto | fails | 72.48 | - | fails | 56.27 | -
|
| CE loss budget | SAC rc / forward | 105.86 | 105.83 | 0.9998 | 81.90 |
82.15 | 1.0030 |

- **Rows that main supports:** no regression. Every PR/main median is
0.993-1.011. Every per-round range includes 1.0 or lies within 1.1 % of
it.
- **Run-to-run variation:** independent runs move the same row by about
±1 %, with no consistent sign. For example, B200 CE loss ckpt / auto
reads 1.0105 here but 0.9997 and 1.0021 in two other runs. On these
paths the only code difference is one Python call per pass under
saved-tensor hooks.
- **SAC keeps the speedup of the "auto" gradient placement:**
- CE loss under SAC with "auto" placement runs as fast as a plain
checkpoint with "auto": on B200 69.00 / 69.85 ms (SAC mm / SAC rc) vs
70.14 ms, and on GB300 53.84 / 54.55 ms vs 54.54 ms.
- The forward placement, which main can run under SAC, takes 99.07 /
99.61 ms on B200 and 76.36 / 77.23 ms on GB300.

## Base and tested commits

- **Base and head:** the branch is one commit (`97ba5dbc`) on main
`9d2c3162`. Since then, main has only re-rendered generated kernel
sources and `build.json` of this package. This PR does not touch those
files, and it merges cleanly.
- **Runs on the head:** the test gates, pre-commit, the 352-row probe on
both GPUs, the B200 hold-case probe and the 8-round A/B rows on both
GPUs.
- **Runs on an earlier revision of this fix with the same library
code:**
  - the GB300 hold-case probe
  - the fresh-process runs on both GPUs
- the GB300 4-round A/B rows (log-prob and `keep_logits`); B200 ran
these rows on the head


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved compatibility with selective activation checkpointing across
loss, log-probability, and kept-logit operations, including gradient
handling and output consistency.
* Checkpointed operations now run without active dispatch modes in
supported cases. As a result, user-defined dispatch modes may not
observe those operations; tracing modes on fake inputs report an error.
* **Documentation**
  * Clarified checkpointing behavior and dispatch-mode limitations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [ea2d8c7](https://github.com/flashinfer-ai/flashinfer/commit/ea2d8c7004d6d723ad653acd23ca00248ce595f2)

- **作者**: eigen
- **时间**: 2026-11-01T18:39:20Z
- **提交信息**: perf(cake_mega_moe_v3): faster TP4 / TP8 T32 and TP4 EP4 / TP8 EP8 rank programs on sm_103a (#8220)

`flashinfer.experimental.mega_moe_v3` runs the Cake MegaMoE v3 prepared
pipeline for the 384-expert, top-6, hidden-5120 model with activation
clamp 10. A single kernel launch covers dispatch, FC1, clamped SwiGLU,
MXFP8 activation quantization, FC2 and weighted combine. The kernel has
four variants on main, and this PR updates one of them: the TP/EP rank
variant. It changes 5 of the variant's 32 programs. Each of them gets
one more operand ring stage. The five are TP4 EP1 and TP8 EP1 (384
experts) at 32 tokens, TP4 EP4 (96 local experts) at 32 and 1024 tokens,
and TP8 EP8 (48 local experts) at 32 tokens.

- At 32 tokens, the dispatch now folds its metadata and pulls token rows
through registers. The send region keeps only the destination-row word
and the folded expert row offsets. It shrinks from 20 KB to 2 KB at 384
experts, and to 1 KB at 96 and 48 local experts. The freed shared memory
takes a twelfth stage.
- TP4 EP4 at 1024 tokens gets an eleventh stage. The dispatch now pulls
each token row in two half-row trips, and the FC2 output staging stores
8 rows per group. This frees one stage of shared memory.
- TP4 EP1 and TP8 EP1 at 32 tokens keep their launch shape and host
binding. TP4 EP4 and TP8 EP8 at 32 tokens still share one host binding
(228480 B dynamic shared memory). TP4 EP4 at 1024 tokens now has its own
host binding.

The routes and the other 27 rank programs are unchanged. The baseline is
the previous Cake version on main, which is the rank variant as last
updated by #8192. The changed programs run faster by 1.005x for TP4 EP1,
1.007x for TP8 EP1, 1.006x for TP4 EP4 at 32 tokens, 1.007x for TP4 EP4
at 1024 tokens and 1.004x for TP8 EP8. That saves 0.32 to 1.87 µs per
call. All five are faster than the A/A noise band in both replicates.
The unchanged rows run 0.999x to 1.002x.

| Configuration | Tokens | previous a (us) | this PR a (us) | speedup a
| previous b (us) | this PR b (us) | speedup b |
|---|---:|---:|---:|---:|---:|---:|---:|
| TP4 EP1 | 1 | 13.90 | 13.91 | 1.000 | 13.90 | 13.89 | 1.001 |
| TP4 EP1 | 4 | 25.88 | 25.89 | 1.000 | 25.99 | 25.99 | 1.000 |
| TP4 EP1 | 16 | 81.14 | 81.16 | 1.000 | 81.18 | 81.15 | 1.000 |
| TP4 EP1 | 32 | 149.20 | 148.46 | 1.005 | 149.16 | 148.39 | 1.005 |
| TP4 EP1 | 128 | 294.18 | 294.11 | 1.000 | 294.08 | 294.08 | 1.000 |
| TP4 EP1 | 512 | 304.62 | 304.60 | 1.000 | 304.64 | 304.61 | 1.000 |
| TP4 EP1 | 1024 | 326.09 | 326.19 | 1.000 | 326.21 | 326.11 | 1.000 |
| TP4 EP1 | 4096 | 438.16 | 438.11 | 1.000 | 438.22 | 438.11 | 1.000 |
| TP8 EP1 | 1 | 12.17 | 12.17 | 1.000 | 12.21 | 12.19 | 1.001 |
| TP8 EP1 | 4 | 18.35 | 18.38 | 0.999 | 18.32 | 18.33 | 1.000 |
| TP8 EP1 | 16 | 52.75 | 52.71 | 1.001 | 52.73 | 52.72 | 1.000 |
| TP8 EP1 | 32 | 92.11 | 91.50 | 1.007 | 92.08 | 91.46 | 1.007 |
| TP8 EP1 | 128 | 180.04 | 180.04 | 1.000 | 180.00 | 180.00 | 1.000 |
| TP8 EP1 | 512 | 188.77 | 188.81 | 1.000 | 188.72 | 188.73 | 1.000 |
| TP8 EP1 | 1024 | 204.87 | 204.91 | 1.000 | 204.88 | 204.89 | 1.000 |
| TP8 EP1 | 4096 | 307.11 | 307.11 | 1.000 | 307.11 | 307.15 | 1.000 |
| TP4 EP4 | 1 | 14.47 | 14.46 | 1.001 | 14.48 | 14.49 | 0.999 |
| TP4 EP4 | 4 | 24.12 | 24.12 | 1.000 | 24.10 | 24.09 | 1.000 |
| TP4 EP4 | 16 | 72.87 | 72.84 | 1.000 | 72.81 | 72.85 | 0.999 |
| TP4 EP4 | 32 | 139.98 | 139.17 | 1.006 | 139.99 | 139.18 | 1.006 |
| TP4 EP4 | 128 | 269.25 | 269.25 | 1.000 | 269.25 | 269.22 | 1.000 |
| TP4 EP4 | 512 | 275.03 | 275.08 | 1.000 | 275.02 | 275.01 | 1.000 |
| TP4 EP4 | 1024 | 282.27 | 280.43 | 1.007 | 282.27 | 280.39 | 1.007 |
| TP4 EP4 | 4096 | 335.82 | 335.73 | 1.000 | 336.43 | 336.22 | 1.001 |
| TP8 EP8 | 1 | 13.06 | 13.06 | 1.000 | 13.07 | 13.06 | 1.001 |
| TP8 EP8 | 4 | 15.94 | 15.90 | 1.002 | 15.97 | 15.94 | 1.002 |
| TP8 EP8 | 16 | 39.44 | 39.45 | 1.000 | 39.43 | 39.38 | 1.001 |
| TP8 EP8 | 32 | 76.05 | 75.73 | 1.004 | 76.05 | 75.73 | 1.004 |
| TP8 EP8 | 128 | 140.18 | 140.13 | 1.000 | 140.15 | 140.07 | 1.001 |
| TP8 EP8 | 512 | 141.31 | 141.34 | 1.000 | 141.27 | 141.26 | 1.000 |
| TP8 EP8 | 1024 | 147.06 | 147.05 | 1.000 | 147.09 | 147.11 | 1.000 |
| TP8 EP8 | 4096 | 186.17 | 186.15 | 1.000 | 186.19 | 186.19 | 1.000 |

*NVIDIA GB300 (sm_103a, 152 SMs), CUDA 13.4, driver 580.159.03. Per-call
latency from CUDA-graph replays (20 calls per graph), median of 21
in-process rounds. The previous version and this PR ran in separate
processes, alternated over 6 rounds. Each value is the median of the 6
process medians. Speedup = previous / this PR. Columns a and b are two
independent replicates, each run alone on its own node. Each replicate
also timed the previous version against itself (an A/A control) to
measure its noise band. The widest band is 0.35 % in replicate a and
0.14 % in replicate b. One unchanged row reads slower than its band in
both replicates: TP8 EP1 at 4 tokens (18.35 to 18.38 µs in a, 18.32 to
18.33 µs in b). Its kernel, binding and catalog record are
byte-identical to main. The `trtllm_fp4_block_scale_routed_moe` baseline
timed in the same processes moved by a similar amount, so this reads as
process noise. 8 other unchanged rows read slower than their band in one
replicate only.*

The kernel's other three Cake variants (single-rank routed-FP4 pipeline,
single-rank routed-FP8 pipeline and grouped-GEMM routes) ship on sm_100a
and sm_103a, and the rank variant ships on sm_103a only.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Updates**
* Updated configuration metadata for several FP4 pipeline programs
targeting `sm_103a`.
* Adjusted the binding selection for one pipeline variant and revised
compile-time settings across multiple variants. These changes affect the
available build configurations; no new user-facing features are
included.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [de08be0](https://github.com/flashinfer-ai/flashinfer/commit/de08be0bb26b37146350497b93374cdf304cfcf2)

- **作者**: eigen
- **时间**: 2026-11-01T18:09:46Z
- **提交信息**: perf(cake_gdn_kcp): with grad, cut more eager host overhead in non-deterministic KCP (#8219)

This PR changes `flashinfer.experimental.cake_gdn_train_kcp`, the
non-deterministic context-parallel variant of Cake's Gated DeltaNet
(GDN) chunked training kernel with gradients. Callers reach it through
`flashinfer.cake_gdn_train_kcp(deterministic=False)`. It follows #8212
and cuts more of the package's eager host work. The change is host-side
only and has four parts:

1. Each plan now derives its launch state once and caches it in
`_Tables.memo`. That state covers the normalized pool tables of
`CallKcp.indexed` with their kernel addressing and device index tables,
the walk and merge-chain device tables, the zero block's index table,
the collectives' split lists and the pool sizes. Every device table
still comes from the plan's content cache, so each launch receives the
same tensors as before.
2. A call without `workspace=` now uses its context's ticket slots for
the current stream. Before, it made a zeroed allocation per call. There
is one zeroed set per context, device and stream. Under a CUDA stream
capture, the call gets fresh slots.
3. Such a call no longer sizes the forward exchange's pools for a
saved-context backward. It also no longer sizes the empty pools at P =
1. Backward peak memory can only go down.
4. `chunk_gdn_kcp` validates its keyword options once per keyword set.
The context's prepared-tables lookup is built once per key, and
per-launch pool slicing and record building are trimmed.

The exchanges cannot be packed: in each step's GDN all_to_all pair the
second exchange needs the first one's result, and the other 2 per-step
collectives belong to the causal-conv package.

Device programs, launch order, grids, streams, numerics, graph-replay
semantics and the public API are unchanged. In every timed run (eager
and graph replay, all ranks), outputs and every gradient are bitwise
equal to the previous package. Launch records are also equal.

Speedup is baseline latency / new latency, so values above 1 mean the
new package is faster. There are three baselines, and all of them ran in
the same process as the new package:

- **Deterministic Cake KCP:** the deterministic Cake KCP package from
main, called through its public entry.
- **Strongest non-Cake, per row:** the faster of FLA 0.6.0
context-parallel KCP and a head-parallel all-to-all around the cuDNN
frontend 1.32.1 FROST GDN engine. Both were qualified by comparison with
the new package. FROST head-CP does not apply to P2 at CP4, because 4
ranks divide neither 2 nor 6 heads. FLA KCP is the only non-Cake arm
there. FlashQLA has no sm_107a build.
- **Previous non-deterministic:** the package of #8212, now on main. It
cannot share the public entry with the new package in one process. It is
loaded as a renamed copy and called through an equivalent stand-in
entry, which skips the public entry's dispatch. A path-only control ran
this PR's code on the stand-in entry and on the public entry. It
measured 0.986-1.002 on forward+backward rows and 0.989-1.005 on
checkpointed rows. "vs previous" ratios are therefore conservative by up
to about 1 %. On the graph-replay rows, same-path code-only ratios
(previous vs this PR's code, both on the stand-in entry) are
0.995-1.002.

All arms ran on one exclusive R200 node (sm_107a, 212 SMs; CUDA 13.0
runtime, PyTorch 2.14.1+cu130; no power capping observed). S26, DET, P1
and P3 use CP2 (2 ranks). P2 uses CP4 (4 ranks). All rows use BF16
q/k/v, FP32 g/beta and head dim 128.

The protocol is the same as in #8212. Each of 5 groups runs the arms in
palindromic order 2 times. Each call is 12 timed iterations after 10
warm-up, with a 256 MiB L2 flush, sync and barrier before each
iteration. Latency is the median CUDA-event time of the slowest rank.
Speedup is the median of the per-group ratios [min, max]. Run 2 is a
separate process with the arm order reversed.

How to read the table:

- Backward = forward+backward − forward.
- "(medians)" marks a ratio of medians.
- (H, HV) = (query/key heads, value heads).
- S26 = (2, 6), 3 documents of 2049/3001/3142 tokens (8192).
- DET = (2, 6), 65536 tokens in 6 documents.
- P2 = (2, 6), 261987 tokens (3 documents), CP4.
- P1 = (16, 48), 241817 tokens.
- P3 = (16, 48), 259174 tokens.
- Layout C is contiguous; layout D is zigzag per document.

Four ratio cells are classed UNSTABLE, all in the vs-deterministic
column. Three are S26 run 1 cells: eager forward, eager forward+backward
and graph-replay checkpointed (deterministic arm drift 2.22 %). The
fourth is DET layout D run 2 eager forward. They are shown as measured.

Table: R200 (sm_107a, 212 SMs), CUDA 13.0 runtime, PyTorch 2.14.1+cu130,
CP2 (P2: CP4); latencies in ms (median CUDA-event time of the slowest
rank); speedup = median of the per-group ratios [min, max].

| GPU / architecture | workload (pack, (H, HV), S tokens, CP, layout);
timing mode; run | operation | deterministic Cake (ms) | strongest
non-Cake (ms, implementation) | previous non-deterministic Cake (ms) |
new non-deterministic Cake (ms) | speedup vs deterministic Cake |
speedup vs non-Cake SOTA | speedup vs previous non-deterministic Cake |
|---|---|---|---|---|---|---|---|---|---|
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, C; eager; run 1 |
forward | 0.805 | 3.235 (FLA KCP) | 0.724 | 0.546 | 1.474 [1.467, 1.479]
| 5.935 [5.909, 5.939] | 1.324 [1.323, 1.343] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, C; eager; run 1 |
backward (= forward+backward − forward) | 1.303 | 3.703 (FLA KCP) |
1.179 | 0.896 | 1.454 [1.430, 1.481] | 4.131 [4.131, 4.131] (medians) |
1.319 [1.301, 1.326] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, C; eager; run 1 |
forward+backward | 2.108 | 6.938 (FLA KCP) | 1.903 | 1.442 | 1.461
[1.446, 1.479] | 4.811 [4.811, 4.811] unpaired | 1.321 [1.312, 1.332] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, C; eager; run 1 |
checkpointed 2×forward+backward | 3.114 | 10.088 (FLA KCP) | 2.865 |
2.192 | 1.419 [1.412, 1.433] | 4.596 [4.568, 4.648] | 1.303 [1.300,
1.319] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, C; graph replay; run
1 | forward | 0.544 | n/a (no graph-replay arm) | 0.526 | 0.527 | 1.032
[1.029, 1.035] | n/a | 0.997 [0.995, 0.998] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, C; graph replay; run
1 | backward (= forward+backward − forward) | 0.854 | n/a (no
graph-replay arm) | 0.837 | 0.837 | 1.019 [1.018, 1.024] | n/a | 1.000
[0.998, 1.004] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, C; graph replay; run
1 | forward+backward | 1.398 | n/a (no graph-replay arm) | 1.363 | 1.364
| 1.025 [1.024, 1.026] | n/a | 0.999 [0.998, 1.000] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, C; graph replay; run
1 | checkpointed 2×forward+backward | 1.936 | n/a (no graph-replay arm)
| 1.895 | 1.899 | 1.020 [1.017, 1.022] | n/a | 0.998 [0.997, 0.999] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, C; eager; run 2
(reversed arm order) | forward | 0.792 | 3.235 (FLA KCP) | 0.718 | 0.545
| 1.453 [1.446, 1.456] | 5.941 [5.941, 5.941] unpaired | 1.318 [1.316,
1.320] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, C; eager; run 2
(reversed arm order) | backward (= forward+backward − forward) | 1.318 |
3.703 (FLA KCP) | 1.184 | 0.887 | 1.485 [1.471, 1.494] | 4.173 [4.173,
4.173] (medians) | 1.339 [1.323, 1.355] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, C; eager; run 2
(reversed arm order) | forward+backward | 2.110 | 6.938 (FLA KCP) |
1.902 | 1.432 | 1.474 [1.462, 1.479] | 4.853 [4.807, 4.857] | 1.331
[1.321, 1.341] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, C; eager; run 2
(reversed arm order) | checkpointed 2×forward+backward | 3.146 | 10.088
(FLA KCP) | 2.891 | 2.219 | 1.423 [1.405, 1.427] | 4.546 [4.546, 4.546]
unpaired | 1.307 [1.295, 1.311] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, C; graph replay; run
2 (reversed arm order) | forward | 0.541 | n/a (no graph-replay arm) |
0.526 | 0.526 | 1.029 [1.026, 1.029] | n/a | 0.999 [0.998, 0.999] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, C; graph replay; run
2 (reversed arm order) | backward (= forward+backward − forward) | 0.852
| n/a (no graph-replay arm) | 0.835 | 0.835 | 1.021 [1.019, 1.022] | n/a
| 1.000 [0.999, 1.003] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, C; graph replay; run
2 (reversed arm order) | forward+backward | 1.393 | n/a (no graph-replay
arm) | 1.361 | 1.361 | 1.023 [1.022, 1.025] | n/a | 1.000 [0.999, 1.002]
|
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, C; graph replay; run
2 (reversed arm order) | checkpointed 2×forward+backward | 1.931 | n/a
(no graph-replay arm) | 1.893 | 1.893 | 1.020 [1.018, 1.021] | n/a |
1.000 [0.999, 1.002] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, D; eager; run 1 |
forward | 0.889 | 3.235 (FLA KCP) | 0.628 | 0.625 | 1.421 [1.420, 1.427]
| 5.179 [5.179, 5.179] unpaired | 1.007 [1.005, 1.008] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, D; eager; run 1 |
backward (= forward+backward − forward) | 1.380 | 3.703 (FLA KCP) |
0.871 | 0.753 | 1.834 [1.814, 1.843] | 4.916 [4.916, 4.916] (medians) |
1.155 [1.152, 1.160] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, D; eager; run 1 |
forward+backward | 2.269 | 6.938 (FLA KCP) | 1.499 | 1.378 | 1.646
[1.639, 1.652] | 5.035 [5.035, 5.035] unpaired | 1.087 [1.087, 1.090] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, D; eager; run 1 |
checkpointed 2×forward+backward | 3.382 | 10.088 (FLA KCP) | 2.365 |
2.038 | 1.662 [1.650, 1.667] | 4.949 [4.949, 4.949] unpaired | 1.164
[1.157, 1.170] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, D; graph replay; run
1 | forward | 0.600 | n/a (no graph-replay arm) | 0.596 | 0.596 | 1.006
[1.005, 1.007] | n/a | 0.998 [0.996, 1.000] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, D; graph replay; run
1 | backward (= forward+backward − forward) | 0.810 | n/a (no
graph-replay arm) | 0.808 | 0.810 | 1.001 [1.000, 1.004] | n/a | 1.000
[0.995, 1.001] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, D; graph replay; run
1 | forward+backward | 1.411 | n/a (no graph-replay arm) | 1.404 | 1.406
| 1.003 [1.002, 1.004] | n/a | 0.999 [0.997, 0.999] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, D; graph replay; run
1 | checkpointed 2×forward+backward | 2.039 | n/a (no graph-replay arm)
| 2.031 | 2.032 | 1.004 [1.003, 1.004] | n/a | 0.999 [0.999, 1.000] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, D; eager; run 2
(reversed arm order) | forward | 0.885 | 3.235 (FLA KCP) | 0.625 | 0.621
| 1.428 [1.418, 1.458] UNSTABLE | 5.207 [5.207, 5.207] unpaired | 1.006
[1.005, 1.008] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, D; eager; run 2
(reversed arm order) | backward (= forward+backward − forward) | 1.377 |
3.703 (FLA KCP) | 0.873 | 0.755 | 1.821 [1.806, 1.830] | 4.904 [4.904,
4.904] (medians) | 1.155 [1.151, 1.159] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, D; eager; run 2
(reversed arm order) | forward+backward | 2.263 | 6.938 (FLA KCP) |
1.498 | 1.376 | 1.643 [1.640, 1.649] | 5.041 [5.041, 5.041] unpaired |
1.089 [1.085, 1.089] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, D; eager; run 2
(reversed arm order) | checkpointed 2×forward+backward | 3.371 | 10.088
(FLA KCP) | 2.366 | 2.034 | 1.656 [1.652, 1.671] | 4.960 [4.960, 4.960]
unpaired | 1.165 [1.161, 1.172] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, D; graph replay; run
2 (reversed arm order) | forward | 0.599 | n/a (no graph-replay arm) |
0.594 | 0.593 | 1.010 [1.009, 1.014] | n/a | 1.002 [1.000, 1.005] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, D; graph replay; run
2 (reversed arm order) | backward (= forward+backward − forward) | 0.809
| n/a (no graph-replay arm) | 0.809 | 0.808 | 1.003 [0.998, 1.004] | n/a
| 1.003 [0.998, 1.005] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, D; graph replay; run
2 (reversed arm order) | forward+backward | 1.408 | n/a (no graph-replay
arm) | 1.403 | 1.400 | 1.006 [1.004, 1.007] | n/a | 1.002 [1.000, 1.003]
|
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, D; graph replay; run
2 (reversed arm order) | checkpointed 2×forward+backward | 2.040 | n/a
(no graph-replay arm) | 2.026 | 2.026 | 1.007 [1.006, 1.008] | n/a |
1.000 [0.999, 1.001] |
| R200 sm_107a (212 SMs) | P1, (16, 48), 241817, CP2, C; eager; run 1 |
forward | 4.866 | 22.030 (FROST head-CP) | 4.805 | 4.793 | 1.015 [1.015,
1.015] | 4.596 [4.596, 4.596] unpaired | 1.003 [1.002, 1.003] |
| R200 sm_107a (212 SMs) | P1, (16, 48), 241817, CP2, C; eager; run 1 |
backward (= forward+backward − forward) | 8.539 | 32.014 (FROST head-CP)
| 8.543 | 8.546 | 0.999 [0.999, 1.000] | 3.746 [3.746, 3.746] (medians)
| 1.000 [0.999, 1.000] |
| R200 sm_107a (212 SMs) | P1, (16, 48), 241817, CP2, C; eager; run 1 |
forward+backward | 13.404 | 54.044 (FROST head-CP) | 13.348 | 13.340 |
1.005 [1.005, 1.005] | 4.051 [4.051, 4.051] unpaired | 1.001 [1.000,
1.001] |
| R200 sm_107a (212 SMs) | P1, (16, 48), 241817, CP2, C; eager; run 1 |
checkpointed 2×forward+backward | 15.063 | 70.615 (FROST head-CP) |
14.939 | 14.930 | 1.009 [1.009, 1.009] | 4.730 [4.730, 4.730] unpaired |
1.001 [1.000, 1.001] |
| R200 sm_107a (212 SMs) | P1, (16, 48), 241817, CP2, C; eager; run 2
(reversed arm order) | forward | 4.858 | 22.030 (FROST head-CP) | 4.791
| 4.781 | 1.016 [1.016, 1.017] | 4.608 [4.607, 4.610] | 1.002 [1.002,
1.003] |
| R200 sm_107a (212 SMs) | P1, (16, 48), 241817, CP2, C; eager; run 2
(reversed arm order) | backward (= forward+backward − forward) | 8.536 |
32.014 (FROST head-CP) | 8.534 | 8.539 | 1.000 [0.999, 1.000] | 3.749
[3.749, 3.749] (medians) | 0.999 [0.999, 1.000] |
| R200 sm_107a (212 SMs) | P1, (16, 48), 241817, CP2, C; eager; run 2
(reversed arm order) | forward+backward | 13.395 | 54.044 (FROST
head-CP) | 13.324 | 13.319 | 1.006 [1.005, 1.006] | 4.057 [4.056, 4.059]
| 1.000 [1.000, 1.001] |
| R200 sm_107a (212 SMs) | P1, (16, 48), 241817, CP2, C; eager; run 2
(reversed arm order) | checkpointed 2×forward+backward | 15.054 | 70.615
(FROST head-CP) | 14.920 | 14.908 | 1.010 [1.009, 1.010] | 4.737 [4.735,
4.738] | 1.001 [1.000, 1.001] |
| R200 sm_107a (212 SMs) | P2, (2, 6), 261987, CP4, C; eager; run 1 |
forward | 0.914 | 18.713 (FLA KCP) | 0.902 | 0.895 | 1.020 [1.020,
1.022] | 20.902 [20.902, 20.902] unpaired | 1.007 [1.007, 1.009] |
| R200 sm_107a (212 SMs) | P2, (2, 6), 261987, CP4, C; eager; run 1 |
backward (= forward+backward − forward) | 1.535 | 16.908 (FLA KCP) |
1.405 | 1.380 | 1.112 [1.107, 1.124] | 12.254 [12.254, 12.254] (medians)
| 1.016 [1.014, 1.023] |
| R200 sm_107a (212 SMs) | P2, (2, 6), 261987, CP4, C; eager; run 1 |
forward+backward | 2.448 | 35.621 (FLA KCP) | 2.307 | 2.275 | 1.076
[1.073, 1.084] | 15.659 [15.644, 15.729] | 1.012 [1.011, 1.017] |
| R200 sm_107a (212 SMs) | P2, (2, 6), 261987, CP4, C; eager; run 1 |
checkpointed 2×forward+backward | 3.413 | 54.507 (FLA KCP) | 3.179 |
2.816 | 1.212 [1.210, 1.213] | 19.346 [19.342, 19.377] | 1.129 [1.125,
1.134] |
| R200 sm_107a (212 SMs) | P2, (2, 6), 261987, CP4, C; graph replay; run
1 | forward | 0.892 | n/a (no graph-replay arm) | 0.879 | 0.882 | 1.012
[1.009, 1.014] | n/a | 0.997 [0.995, 0.999] |
| R200 sm_107a (212 SMs) | P2, (2, 6), 261987, CP4, C; graph replay; run
1 | backward (= forward+backward − forward) | 1.374 | n/a (no
graph-replay arm) | 1.374 | 1.375 | 1.000 [0.999, 1.001] | n/a | 1.000
[0.999, 1.001] |
| R200 sm_107a (212 SMs) | P2, (2, 6), 261987, CP4, C; graph replay; run
1 | forward+backward | 2.266 | n/a (no graph-replay arm) | 2.254 | 2.256
| 1.005 [1.004, 1.005] | n/a | 0.999 [0.999, 0.999] |
| R200 sm_107a (212 SMs) | P2, (2, 6), 261987, CP4, C; graph replay; run
1 | checkpointed 2×forward+backward | 3.172 | n/a (no graph-replay arm)
| 3.144 | 3.148 | 1.008 [1.007, 1.008] | n/a | 0.999 [0.998, 0.999] |
| R200 sm_107a (212 SMs) | P2, (2, 6), 261987, CP4, C; eager; run 2
(reversed arm order) | forward | 0.914 | 18.713 (FLA KCP) | 0.902 |
0.896 | 1.020 [1.019, 1.021] | 21.078 [20.856, 21.094] | 1.006 [1.006,
1.007] |
| R200 sm_107a (212 SMs) | P2, (2, 6), 261987, CP4, C; eager; run 2
(reversed arm order) | backward (= forward+backward − forward) | 1.529 |
16.908 (FLA KCP) | 1.400 | 1.378 | 1.109 [1.100, 1.116] | 12.268
[12.268, 12.268] (medians) | 1.014 [1.013, 1.022] |
| R200 sm_107a (212 SMs) | P2, (2, 6), 261987, CP4, C; eager; run 2
(reversed arm order) | forward+backward | 2.443 | 35.621 (FLA KCP) |
2.302 | 2.274 | 1.073 [1.068, 1.078] | 15.663 [15.663, 15.663] unpaired
| 1.011 [1.011, 1.016] |
| R200 sm_107a (212 SMs) | P2, (2, 6), 261987, CP4, C; eager; run 2
(reversed arm order) | checkpointed 2×forward+backward | 3.417 | 54.507
(FLA KCP) | 3.183 | 2.816 | 1.213 [1.210, 1.220] | 19.357 [19.357,
19.357] unpaired | 1.130 [1.128, 1.134] |
| R200 sm_107a (212 SMs) | P2, (2, 6), 261987, CP4, C; graph replay; run
2 (reversed arm order) | forward | 0.894 | n/a (no graph-replay arm) |
0.880 | 0.881 | 1.014 [1.011, 1.018] | n/a | 1.000 [0.996, 1.001] |
| R200 sm_107a (212 SMs) | P2, (2, 6), 261987, CP4, C; graph replay; run
2 (reversed arm order) | backward (= forward+backward − forward) | 1.373
| n/a (no graph-replay arm) | 1.371 | 1.374 | 1.000 [0.998, 1.002] | n/a
| 0.997 [0.997, 1.001] |
| R200 sm_107a (212 SMs) | P2, (2, 6), 261987, CP4, C; graph replay; run
2 (reversed arm order) | forward+backward | 2.267 | n/a (no graph-replay
arm) | 2.251 | 2.255 | 1.005 [1.005, 1.005] | n/a | 0.999 [0.998, 0.999]
|
| R200 sm_107a (212 SMs) | P2, (2, 6), 261987, CP4, C; graph replay; run
2 (reversed arm order) | checkpointed 2×forward+backward | 3.174 | n/a
(no graph-replay arm) | 3.143 | 3.146 | 1.009 [1.009, 1.009] | n/a |
0.999 [0.999, 1.000] |
| R200 sm_107a (212 SMs) | P3, (16, 48), 259174, CP2, C; eager; run 1 |
forward | 5.028 | 7.908 (FLA KCP) | 4.957 | 4.948 | 1.016 [1.016, 1.017]
| 1.598 [1.597, 1.599] | 1.002 [1.001, 1.003] |
| R200 sm_107a (212 SMs) | P3, (16, 48), 259174, CP2, C; eager; run 1 |
backward (= forward+backward − forward) | 9.084 | 51.429 (FROST head-CP
forward+backward − FLA KCP forward) | 9.081 | 9.081 | 1.000 [1.000,
1.001] | 5.664 [5.664, 5.664] (medians) | 1.000 [1.000, 1.001] |
| R200 sm_107a (212 SMs) | P3, (16, 48), 259174, CP2, C; eager; run 1 |
forward+backward | 14.112 | 59.337 (FROST head-CP) | 14.039 | 14.029 |
1.006 [1.006, 1.006] | 4.230 [4.230, 4.230] unpaired | 1.001 [1.000,
1.001] |
| R200 sm_107a (212 SMs) | P3, (16, 48), 259174, CP2, C; eager; run 1 |
checkpointed 2×forward+backward | 15.812 | 67.882 (FLA KCP) | 15.670 |
15.658 | 1.010 [1.009, 1.010] | 4.335 [4.335, 4.335] unpaired | 1.001
[1.000, 1.001] |
| R200 sm_107a (212 SMs) | P3, (16, 48), 259174, CP2, C; eager; run 2
(reversed arm order) | forward | 5.027 | 7.908 (FLA KCP) | 4.951 | 4.945
| 1.017 [1.016, 1.017] | 1.599 [1.599, 1.599] unpaired | 1.001 [1.000,
1.003] |
| R200 sm_107a (212 SMs) | P3, (16, 48), 259174, CP2, C; eager; run 2
(reversed arm order) | backward (= forward+backward − forward) | 9.086 |
51.429 (FROST head-CP forward+backward − FLA KCP forward) | 9.081 |
9.079 | 1.000 [1.000, 1.002] | 5.664 [5.664, 5.664] (medians) | 1.000
[0.999, 1.001] |
| R200 sm_107a (212 SMs) | P3, (16, 48), 259174, CP2, C; eager; run 2
(reversed arm order) | forward+backward | 14.113 | 59.337 (FROST
head-CP) | 14.032 | 14.024 | 1.006 [1.006, 1.007] | 4.231 [4.230, 4.232]
| 1.000 [1.000, 1.001] |
| R200 sm_107a (212 SMs) | P3, (16, 48), 259174, CP2, C; eager; run 2
(reversed arm order) | checkpointed 2×forward+backward | 15.826 | 67.882
(FLA KCP) | 15.666 | 15.660 | 1.011 [1.010, 1.011] | 4.335 [4.332,
4.336] | 1.000 [1.000, 1.001] |
| R200 sm_107a (212 SMs) | S26, (2, 6), 8192, CP2, C; eager; run 1 |
forward | 0.519 | 0.838 (FLA KCP) | 0.463 | 0.406 | 1.277 [1.271, 1.303]
UNSTABLE | 2.066 [2.052, 2.072] | 1.139 [1.136, 1.149] |
| R200 sm_107a (212 SMs) | S26, (2, 6), 8192, CP2, C; eager; run 1 |
backward (= forward+backward − forward) | 0.778 | 0.725 (FLA KCP) |
0.688 | 0.613 | 1.268 [1.262, 1.281] | 1.182 [1.182, 1.182] (medians) |
1.122 [1.118, 1.127] |
| R200 sm_107a (212 SMs) | S26, (2, 6), 8192, CP2, C; eager; run 1 |
forward+backward | 1.296 | 1.563 (FLA KCP) | 1.151 | 1.020 | 1.270
[1.268, 1.290] UNSTABLE | 1.533 [1.530, 1.541] | 1.130 [1.126, 1.133] |
| R200 sm_107a (212 SMs) | S26, (2, 6), 8192, CP2, C; eager; run 1 |
checkpointed 2×forward+backward | 2.186 | 2.547 (FLA KCP) | 1.991 |
1.809 | 1.207 [1.197, 1.217] | 1.403 [1.396, 1.412] | 1.096 [1.093,
1.107] |
| R200 sm_107a (212 SMs) | S26, (2, 6), 8192, CP2, C; graph replay; run
1 | forward | 0.306 | n/a (no graph-replay arm) | 0.298 | 0.299 | 1.025
[1.018, 1.026] | n/a | 0.998 [0.992, 1.000] |
| R200 sm_107a (212 SMs) | S26, (2, 6), 8192, CP2, C; graph replay; run
1 | backward (= forward+backward − forward) | 0.326 | n/a (no
graph-replay arm) | 0.325 | 0.325 | 1.002 [0.999, 1.012] | n/a | 0.998
[0.994, 1.005] |
| R200 sm_107a (212 SMs) | S26, (2, 6), 8192, CP2, C; graph replay; run
1 | forward+backward | 0.633 | n/a (no graph-replay arm) | 0.623 | 0.624
| 1.013 [1.012, 1.015] | n/a | 0.998 [0.997, 1.000] |
| R200 sm_107a (212 SMs) | S26, (2, 6), 8192, CP2, C; graph replay; run
1 | checkpointed 2×forward+backward | 1.014 | n/a (no graph-replay arm)
| 1.002 | 1.010 | 1.003 [0.952, 1.012] UNSTABLE | n/a | 0.993 [0.967,
0.995] |
| R200 sm_107a (212 SMs) | S26, (2, 6), 8192, CP2, C; eager; run 2
(reversed arm order) | forward | 0.518 | 0.838 (FLA KCP) | 0.462 | 0.407
| 1.272 [1.268, 1.282] | 2.061 [2.061, 2.061] unpaired | 1.137 [1.129,
1.140] |
| R200 sm_107a (212 SMs) | S26, (2, 6), 8192, CP2, C; eager; run 2
(reversed arm order) | backward (= forward+backward − forward) | 0.752 |
0.725 (FLA KCP) | 0.680 | 0.607 | 1.236 [1.228, 1.256] | 1.195 [1.195,
1.195] (medians) | 1.114 [1.110, 1.130] |
| R200 sm_107a (212 SMs) | S26, (2, 6), 8192, CP2, C; eager; run 2
(reversed arm order) | forward+backward | 1.270 | 1.563 (FLA KCP) |
1.142 | 1.014 | 1.250 [1.247, 1.262] | 1.543 [1.543, 1.543] unpaired |
1.123 [1.121, 1.133] |
| R200 sm_107a (212 SMs) | S26, (2, 6), 8192, CP2, C; eager; run 2
(reversed arm order) | checkpointed 2×forward+backward | 2.130 | 2.547
(FLA KCP) | 1.960 | 1.776 | 1.198 [1.194, 1.210] | 1.434 [1.434, 1.434]
unpaired | 1.105 [1.101, 1.113] |
| R200 sm_107a (212 SMs) | S26, (2, 6), 8192, CP2, C; graph replay; run
2 (reversed arm order) | forward | 0.305 | n/a (no graph-replay arm) |
0.298 | 0.299 | 1.019 [1.016, 1.022] | n/a | 0.994 [0.991, 0.997] |
| R200 sm_107a (212 SMs) | S26, (2, 6), 8192, CP2, C; graph replay; run
2 (reversed arm order) | backward (= forward+backward − forward) | 0.328
| n/a (no graph-replay arm) | 0.325 | 0.327 | 1.002 [1.002, 1.004] | n/a
| 0.995 [0.993, 0.999] |
| R200 sm_107a (212 SMs) | S26, (2, 6), 8192, CP2, C; graph replay; run
2 (reversed arm order) | forward+backward | 0.633 | n/a (no graph-replay
arm) | 0.623 | 0.626 | 1.010 [1.009, 1.012] | n/a | 0.995 [0.995, 0.996]
|
| R200 sm_107a (212 SMs) | S26, (2, 6), 8192, CP2, C; graph replay; run
2 (reversed arm order) | checkpointed 2×forward+backward | 0.995 | n/a
(no graph-replay arm) | 0.984 | 0.997 | 0.998 [0.992, 1.006] | n/a |
0.986 [0.982, 0.995] |

Reading:

- **Eager vs previous non-deterministic:** forward+backward is
1.123-1.130 on S26, 1.321-1.331 on DET C, 1.087-1.089 on DET D and
1.011-1.012 on P2 (CP4). Checkpointed steps are 1.096-1.105 (S26),
1.303-1.307 (DET C), 1.164-1.165 (DET D) and 1.129-1.130 (P2).
- **Eager vs deterministic Cake:** forward+backward is 1.250-1.270 on
S26, where the run 1 value of 1.270 is classed UNSTABLE. It is
1.461-1.474 on DET C, 1.643-1.646 on DET D and 1.073-1.076 on P2.
Checkpointed steps are 1.198-1.207 (S26), 1.419-1.423 (DET C),
1.656-1.662 (DET D) and 1.212-1.213 (P2).
- **Graph replay:** vs the previous package, the DET C, DET D and P2
graph cells are between 0.997 and 1.003. S26 graph cells are lower:
0.994-0.998 on forward, 0.995-0.998 on backward and forward+backward,
and 0.986-0.993 on checkpointed, the smallest cell. These ratios include
the entry-path difference. With both arms on the stand-in entry, the
same-path code-only ratios on the graph-replay rows are 0.995-1.002. Vs
deterministic Cake, graph cells are between 0.998 and 1.032.
- **(16, 48) rows:** P1 and P3 are GPU-bound and at parity with the
previous package, between 0.999 and 1.003 in every cell. Vs
deterministic Cake they are between 0.999 and 1.017.
- **Non-Cake:** the new package is faster than the strongest non-Cake
implementation in every eager cell. The smallest ratio is 1.182-1.195,
on S26 backward. On forward+backward it is 1.533-1.543 (S26),
4.811-4.853 (DET C), 5.035-5.041 (DET D), 15.659-15.663 (P2, vs FLA KCP
only), 4.051-4.057 (P1) and 4.230-4.231 (P3). There is no non-Cake
graph-replay arm.

B200 (sm_100a) and B300/GB300 (sm_103a) rows are pending; the change is
host-side only on every architecture.

The kernel's other Cake variants, all on main, are the deterministic
single-GPU `flashinfer.experimental.cake_gdn_det_train`, the
non-deterministic single-GPU
`flashinfer.experimental.cake.cake_gdn_train` (#8157) and the
deterministic context-parallel
`flashinfer.experimental.cake_gdn_det_train_kcp`; this PR tunes the
non-deterministic context-parallel package from #8172, previously tuned
in #8212, the two context-parallel variants share the entry
`flashinfer.cake_gdn_train_kcp(deterministic=...)`, and the family ships
on sm_100a, sm_103a and sm_107a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Improvements**
  * Repeated launch plans avoid redundant preparation.
* Per-call workspaces skip empty or unused buffers in applicable forward
and backward operations, reducing workspace requirements.
* Calls on separate CUDA streams use separate ticket state. During CUDA
graph capture, calls use fresh ticket state rather than sharing cached
state.
* Supported keyword options are validated, and repeated option sets can
reuse cached validation results.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [3b8d699](https://github.com/flashinfer-ai/flashinfer/commit/3b8d699eca76b63eea26792cfc549037f06f7049)

- **作者**: eigen
- **时间**: 2026-11-01T17:05:22Z
- **提交信息**: perf(cake_gdn): overlap the two compute warpgroups in the cross-rank state walk (#8215)

Cake's deterministic context-parallel GDN training kernel has one
data-type variant: BF16 q/k/v/out/dout and FP32 scalar log-decay g and
beta per token and value head, with dq/dk reduced in FP32 over the value
heads of each Q/K head and converted to the output type once. The
grouped Q/K head counts `(H_qk, HV)` are runtime parameters with
production shape (16, 48), and the kernel has three partition layouts:
contiguous, whole-buffer zigzag, and per-document zigzag + ragged. It
provides fused forward, backward from the saved set, checkpoint replay
(non-reentrant and reentrant), an optional causal-conv1d halo exchange,
and exact cross-rank state passing. This PR delivers the same variant
with one kernel change. The cross-rank state-transfer walk kernel
carries the forward state across rank boundaries in an 8-warp TF32 hi/lo
form. Its two compute warpgroups now run half a matrix multiply apart,
so one warpgroup's barrier wait overlaps the other warpgroup's
tensor-core work. Its shared-memory ring stage grows from 512 to 2048
bytes, and the kernel's dynamic shared memory grows from 198144 to
199680 bytes. All other kernels are unchanged and compile to identical
machine code. The PR also includes a README wording fix for the
workspace byte query default and test-only fixes for the distributed
test: an in-tree seeded inputs helper, and forward-only rows on a rank
that holds no tokens. The tables below compare against the previous
version of this package, PR #7761. Over 60 rows (5 packs x CP {2, 4, 8,
16} x 3 layouts), the gain is small, about 1 to 1.5 percent on average.
On GB300 the geometric-mean speedup is 1.011x forward and 1.010x
training step. Per-row values range from 0.90x to 1.03x forward and from
0.98x to 1.04x training step. Only one row is at 0.90x: P1, CP 16,
zigzag, forward. On GB200 the geometric-mean speedup is 1.015x forward
and 1.008x training step. Per-row values range from 0.99x to 1.05x
forward and from 0.99x to 1.02x training step. On both GPUs, peak memory
per rank is no higher than in the previous version on any row (within
0.5 MiB).

**NVIDIA GB300 (sm_103a, CUDA 13.4)** — context-parallel GDN layer,
`(H_qk, HV) = (16, 48)`, head dim 128, CP = 2, 4, 8, 16; latency per
call of the slowest rank (median over repeats); CP 2: median over 2
back-to-back session(s) on the same nodes; CP 4: median over 2
back-to-back session(s) on the same nodes; CP 8: median over 2
back-to-back session(s) on the same nodes; CP 16: median over 2
back-to-back session(s) on the same nodes. Forward = module forward;
training step = forward + checkpoint recompute + backward, communication
included. Baseline: the previous version of this package (#7761) on the
same layout.

| Pack (tokens / docs) | CP | Layout | Forward: this PR ms | previous ms
| Speedup | Training step: this PR ms | previous ms | Speedup |
|---|---:|---|---:|---:|---:|---:|---:|---:|
| P1 (241,817 tokens / 6 docs) | 2 | contiguous | 7.862 | 8.000 | 1.02x
| 23.775 | 24.085 | 1.01x |
| P1 (241,817 tokens / 6 docs) | 2 | zigzag | 7.838 | 7.990 | 1.02x |
23.906 | 24.211 | 1.01x |
| P1 (241,817 tokens / 6 docs) | 2 | per-document zigzag + ragged |
8.201 | 8.353 | 1.02x | 24.588 | 24.903 | 1.01x |
| P1 (241,817 tokens / 6 docs) | 4 | contiguous | 4.364 | 4.461 | 1.02x
| 13.000 | 13.181 | 1.01x |
| P1 (241,817 tokens / 6 docs) | 4 | zigzag | 4.298 | 4.379 | 1.02x |
12.806 | 12.961 | 1.01x |
| P1 (241,817 tokens / 6 docs) | 4 | per-document zigzag + ragged |
4.443 | 4.517 | 1.02x | 13.244 | 13.398 | 1.01x |
| P1 (241,817 tokens / 6 docs) | 8 | contiguous | 2.511 | 2.544 | 1.01x
| 7.896 | 7.854 | 0.99x |
| P1 (241,817 tokens / 6 docs) | 8 | zigzag | 2.654 | 2.710 | 1.02x |
7.535 | 7.693 | 1.02x |
| P1 (241,817 tokens / 6 docs) | 8 | per-document zigzag + ragged |
2.707 | 2.729 | 1.01x | 7.791 | 7.883 | 1.01x |
| P1 (241,817 tokens / 6 docs) | 16 | contiguous | 2.214 | 2.145 | 0.97x
| 6.921 | 6.963 | 1.01x |
| P1 (241,817 tokens / 6 docs) | 16 | zigzag | 1.956 | 1.762 | 0.90x |
5.891 | 5.807 | 0.99x |
| P1 (241,817 tokens / 6 docs) | 16 | per-document zigzag + ragged |
2.190 | 2.162 | 0.99x | 6.990 | 6.985 | 1.00x |
| P2 (261,987 / 3) | 2 | contiguous | 8.427 | 8.588 | 1.02x | 25.769 |
26.098 | 1.01x |
| P2 (261,987 / 3) | 2 | zigzag | 8.539 | 8.702 | 1.02x | 25.909 |
26.258 | 1.01x |
| P2 (261,987 / 3) | 2 | per-document zigzag + ragged | 8.560 | 8.734 |
1.02x | 26.293 | 26.640 | 1.01x |
| P2 (261,987 / 3) | 4 | contiguous | 4.409 | 4.490 | 1.02x | 13.133 |
13.267 | 1.01x |
| P2 (261,987 / 3) | 4 | zigzag | 4.651 | 4.735 | 1.02x | 13.905 |
14.000 | 1.01x |
| P2 (261,987 / 3) | 4 | per-document zigzag + ragged | 5.002 | 5.082 |
1.02x | 14.831 | 14.952 | 1.01x |
| P2 (261,987 / 3) | 8 | contiguous | 2.590 | 2.617 | 1.01x | 7.905 |
7.888 | 1.00x |
| P2 (261,987 / 3) | 8 | zigzag | 2.846 | 2.902 | 1.02x | 8.054 | 8.157
| 1.01x |
| P2 (261,987 / 3) | 8 | per-document zigzag + ragged | 2.796 | 2.837 |
1.01x | 8.032 | 8.126 | 1.01x |
| P2 (261,987 / 3) | 16 | contiguous | 2.190 | 2.179 | 0.99x | 6.977 |
6.959 | 1.00x |
| P2 (261,987 / 3) | 16 | zigzag | 1.815 | 1.831 | 1.01x | 6.026 | 6.020
| 1.00x |
| P2 (261,987 / 3) | 16 | per-document zigzag + ragged | 1.973 | 1.970 |
1.00x | 6.379 | 6.429 | 1.01x |
| P3 (259,174 / 2) | 2 | contiguous | 7.395 | 7.399 | 1.00x | 25.470 |
25.481 | 1.00x |
| P3 (259,174 / 2) | 2 | zigzag | 9.332 | 9.503 | 1.02x | 28.383 |
28.728 | 1.01x |
| P3 (259,174 / 2) | 2 | per-document zigzag + ragged | 8.262 | 8.431 |
1.02x | 25.329 | 25.678 | 1.01x |
| P3 (259,174 / 2) | 4 | contiguous | 4.376 | 4.456 | 1.02x | 13.224 |
13.395 | 1.01x |
| P3 (259,174 / 2) | 4 | zigzag | 4.383 | 4.462 | 1.02x | 13.236 |
13.394 | 1.01x |
| P3 (259,174 / 2) | 4 | per-document zigzag + ragged | 4.960 | 5.053 |
1.02x | 14.700 | 14.891 | 1.01x |
| P3 (259,174 / 2) | 8 | contiguous | 2.685 | 2.692 | 1.00x | 7.998 |
7.975 | 1.00x |
| P3 (259,174 / 2) | 8 | zigzag | 2.852 | 2.886 | 1.01x | 8.014 | 8.121
| 1.01x |
| P3 (259,174 / 2) | 8 | per-document zigzag + ragged | 2.873 | 2.891 |
1.01x | 8.138 | 8.255 | 1.01x |
| P3 (259,174 / 2) | 16 | contiguous | 2.278 | 2.274 | 1.00x | 6.993 |
6.977 | 1.00x |
| P3 (259,174 / 2) | 16 | zigzag | 1.835 | 1.832 | 1.00x | 5.975 | 5.913
| 0.99x |
| P3 (259,174 / 2) | 16 | per-document zigzag + ragged | 1.902 | 1.897 |
1.00x | 6.176 | 6.170 | 1.00x |
| P4 (254,976 / 1) | 2 | contiguous | 8.257 | 8.400 | 1.02x | 25.154 |
25.474 | 1.01x |
| P4 (254,976 / 1) | 2 | zigzag | 8.480 | 8.634 | 1.02x | 25.781 |
26.094 | 1.01x |
| P4 (254,976 / 1) | 2 | per-document zigzag + ragged | 8.527 | 8.685 |
1.02x | 25.898 | 26.210 | 1.01x |
| P4 (254,976 / 1) | 4 | contiguous | 4.281 | 4.369 | 1.02x | 12.739 |
13.287 | 1.04x |
| P4 (254,976 / 1) | 4 | zigzag | 4.327 | 4.411 | 1.02x | 12.846 |
13.414 | 1.04x |
| P4 (254,976 / 1) | 4 | per-document zigzag + ragged | 4.442 | 4.541 |
1.02x | 13.234 | 13.566 | 1.03x |
| P4 (254,976 / 1) | 8 | contiguous | 2.522 | 2.553 | 1.01x | 7.581 |
7.554 | 1.00x |
| P4 (254,976 / 1) | 8 | zigzag | 2.805 | 2.861 | 1.02x | 7.940 | 8.048
| 1.01x |
| P4 (254,976 / 1) | 8 | per-document zigzag + ragged | 2.862 | 2.920 |
1.02x | 8.200 | 8.324 | 1.02x |
| P4 (254,976 / 1) | 16 | contiguous | 2.189 | 2.262 | 1.03x | 6.944 |
6.904 | 0.99x |
| P4 (254,976 / 1) | 16 | zigzag | 1.828 | 1.876 | 1.03x | 5.989 | 5.986
| 1.00x |
| P4 (254,976 / 1) | 16 | per-document zigzag + ragged | 2.327 | 2.346 |
1.01x | 7.330 | 7.341 | 1.00x |
| P5 (249,856 / 4) | 2 | contiguous | 8.070 | 8.248 | 1.02x | 24.824 |
25.168 | 1.01x |
| P5 (249,856 / 4) | 2 | zigzag | 8.737 | 8.901 | 1.02x | 26.781 |
27.117 | 1.01x |
| P5 (249,856 / 4) | 2 | per-document zigzag + ragged | 8.304 | 8.473 |
1.02x | 25.257 | 25.595 | 1.01x |
| P5 (249,856 / 4) | 4 | contiguous | 4.236 | 4.313 | 1.02x | 12.805 |
12.963 | 1.01x |
| P5 (249,856 / 4) | 4 | zigzag | 4.346 | 4.431 | 1.02x | 13.004 |
13.162 | 1.01x |
| P5 (249,856 / 4) | 4 | per-document zigzag + ragged | 4.503 | 4.599 |
1.02x | 13.487 | 13.682 | 1.01x |
| P5 (249,856 / 4) | 8 | contiguous | 2.620 | 2.644 | 1.01x | 7.941 |
8.231 | 1.04x |
| P5 (249,856 / 4) | 8 | zigzag | 2.753 | 2.829 | 1.03x | 7.737 | 7.989
| 1.03x |
| P5 (249,856 / 4) | 8 | per-document zigzag + ragged | 2.657 | 2.734 |
1.03x | 7.680 | 7.883 | 1.03x |
| P5 (249,856 / 4) | 16 | contiguous | 2.195 | 2.177 | 0.99x | 6.936 |
6.968 | 1.00x |
| P5 (249,856 / 4) | 16 | zigzag | 1.801 | 1.796 | 1.00x | 5.893 | 5.797
| 0.98x |
| P5 (249,856 / 4) | 16 | per-document zigzag + ragged | 2.036 | 2.029 |
1.00x | 6.570 | 6.565 | 1.00x |

**NVIDIA GB200 (sm_100a, CUDA 13.4)** — context-parallel GDN layer,
`(H_qk, HV) = (16, 48)`, head dim 128, CP = 2, 4, 8, 16; latency per
call of the slowest rank (median over repeats); CP 2: median over 2
back-to-back session(s) on the same nodes; CP 4: median over 3
back-to-back session(s) on the same nodes; CP 8: median over 2
back-to-back session(s) on the same nodes; CP 16: median over 2
back-to-back session(s) on the same nodes. Forward = module forward;
training step = forward + checkpoint recompute + backward, communication
included. Baseline: the previous version of this package (#7761) on the
same layout.

| Pack (tokens / docs) | CP | Layout | Forward: this PR ms | previous ms
| Speedup | Training step: this PR ms | previous ms | Speedup |
|---|---:|---|---:|---:|---:|---:|---:|---:|
| P1 (241,817 tokens / 6 docs) | 2 | contiguous | 8.023 | 8.150 | 1.02x
| 24.241 | 24.537 | 1.01x |
| P1 (241,817 tokens / 6 docs) | 2 | zigzag | 7.986 | 8.137 | 1.02x |
24.354 | 24.660 | 1.01x |
| P1 (241,817 tokens / 6 docs) | 2 | per-document zigzag + ragged |
8.360 | 8.511 | 1.02x | 25.041 | 25.341 | 1.01x |
| P1 (241,817 tokens / 6 docs) | 4 | contiguous | 4.461 | 4.544 | 1.02x
| 13.306 | 13.469 | 1.01x |
| P1 (241,817 tokens / 6 docs) | 4 | zigzag | 4.364 | 4.443 | 1.02x |
13.023 | 13.173 | 1.01x |
| P1 (241,817 tokens / 6 docs) | 4 | per-document zigzag + ragged |
4.542 | 4.622 | 1.02x | 13.496 | 13.661 | 1.01x |
| P1 (241,817 tokens / 6 docs) | 8 | contiguous | 2.555 | 2.552 | 1.00x
| 7.880 | 7.885 | 1.00x |
| P1 (241,817 tokens / 6 docs) | 8 | zigzag | 2.671 | 2.727 | 1.02x |
7.658 | 7.789 | 1.02x |
| P1 (241,817 tokens / 6 docs) | 8 | per-document zigzag + ragged |
2.716 | 2.750 | 1.01x | 7.863 | 7.945 | 1.01x |
| P1 (241,817 tokens / 6 docs) | 16 | contiguous | 2.186 | 2.197 | 1.00x
| 6.911 | 6.874 | 0.99x |
| P1 (241,817 tokens / 6 docs) | 16 | zigzag | 1.767 | 1.777 | 1.01x |
5.769 | 5.746 | 1.00x |
| P1 (241,817 tokens / 6 docs) | 16 | per-document zigzag + ragged |
2.166 | 2.162 | 1.00x | 6.901 | 6.875 | 1.00x |
| P2 (261,987 / 3) | 2 | contiguous | 8.583 | 8.757 | 1.02x | 26.250 |
26.573 | 1.01x |
| P2 (261,987 / 3) | 2 | zigzag | 8.703 | 8.883 | 1.02x | 26.383 |
26.730 | 1.01x |
| P2 (261,987 / 3) | 2 | per-document zigzag + ragged | 8.732 | 8.911 |
1.02x | 26.803 | 27.144 | 1.01x |
| P2 (261,987 / 3) | 4 | contiguous | 4.514 | 4.572 | 1.01x | 13.370 |
13.545 | 1.01x |
| P2 (261,987 / 3) | 4 | zigzag | 4.753 | 4.829 | 1.02x | 14.144 |
14.288 | 1.01x |
| P2 (261,987 / 3) | 4 | per-document zigzag + ragged | 5.070 | 5.149 |
1.02x | 14.977 | 15.140 | 1.01x |
| P2 (261,987 / 3) | 8 | contiguous | 2.636 | 2.653 | 1.01x | 8.038 |
7.988 | 0.99x |
| P2 (261,987 / 3) | 8 | zigzag | 2.878 | 2.934 | 1.02x | 8.204 | 8.333
| 1.02x |
| P2 (261,987 / 3) | 8 | per-document zigzag + ragged | 2.825 | 2.875 |
1.02x | 8.174 | 8.270 | 1.01x |
| P2 (261,987 / 3) | 16 | contiguous | 2.192 | 2.196 | 1.00x | 6.984 |
6.972 | 1.00x |
| P2 (261,987 / 3) | 16 | zigzag | 1.815 | 1.849 | 1.02x | 5.971 | 5.963
| 1.00x |
| P2 (261,987 / 3) | 16 | per-document zigzag + ragged | 1.972 | 1.968 |
1.00x | 6.437 | 6.385 | 0.99x |
| P3 (259,174 / 2) | 2 | contiguous | 7.528 | 7.520 | 1.00x | 26.105 |
26.108 | 1.00x |
| P3 (259,174 / 2) | 2 | zigzag | 9.475 | 9.626 | 1.02x | 28.793 |
29.109 | 1.01x |
| P3 (259,174 / 2) | 2 | per-document zigzag + ragged | 8.423 | 8.580 |
1.02x | 25.830 | 26.159 | 1.01x |
| P3 (259,174 / 2) | 4 | contiguous | 4.458 | 4.542 | 1.02x | 13.458 |
13.623 | 1.01x |
| P3 (259,174 / 2) | 4 | zigzag | 4.482 | 4.549 | 1.01x | 13.475 |
13.625 | 1.01x |
| P3 (259,174 / 2) | 4 | per-document zigzag + ragged | 5.044 | 5.138 |
1.02x | 14.944 | 15.141 | 1.01x |
| P3 (259,174 / 2) | 8 | contiguous | 2.726 | 2.747 | 1.01x | 8.053 |
8.134 | 1.01x |
| P3 (259,174 / 2) | 8 | zigzag | 2.858 | 2.994 | 1.05x | 8.161 | 8.294
| 1.02x |
| P3 (259,174 / 2) | 8 | per-document zigzag + ragged | 2.859 | 2.993 |
1.05x | 8.261 | 8.388 | 1.02x |
| P3 (259,174 / 2) | 16 | contiguous | 2.195 | 2.244 | 1.02x | 6.852 |
6.945 | 1.01x |
| P3 (259,174 / 2) | 16 | zigzag | 1.807 | 1.846 | 1.02x | 5.889 | 5.846
| 0.99x |
| P3 (259,174 / 2) | 16 | per-document zigzag + ragged | 1.872 | 1.904 |
1.02x | 6.116 | 6.110 | 1.00x |
| P4 (254,976 / 1) | 2 | contiguous | 8.438 | 8.592 | 1.02x | 25.655 |
25.989 | 1.01x |
| P4 (254,976 / 1) | 2 | zigzag | 8.612 | 8.772 | 1.02x | 26.227 |
26.547 | 1.01x |
| P4 (254,976 / 1) | 2 | per-document zigzag + ragged | 8.668 | 8.826 |
1.02x | 26.292 | 26.607 | 1.01x |
| P4 (254,976 / 1) | 4 | contiguous | 4.360 | 4.434 | 1.02x | 13.026 |
13.158 | 1.01x |
| P4 (254,976 / 1) | 4 | zigzag | 4.405 | 4.478 | 1.02x | 13.111 |
13.271 | 1.01x |
| P4 (254,976 / 1) | 4 | per-document zigzag + ragged | 4.541 | 4.626 |
1.02x | 13.527 | 13.694 | 1.01x |
| P4 (254,976 / 1) | 8 | contiguous | 2.548 | 2.583 | 1.01x | 7.608 |
7.640 | 1.00x |
| P4 (254,976 / 1) | 8 | zigzag | 2.826 | 2.893 | 1.02x | 8.078 | 8.206
| 1.02x |
| P4 (254,976 / 1) | 8 | per-document zigzag + ragged | 2.890 | 2.943 |
1.02x | 8.342 | 8.455 | 1.01x |
| P4 (254,976 / 1) | 16 | contiguous | 2.164 | 2.172 | 1.00x | 6.815 |
6.837 | 1.00x |
| P4 (254,976 / 1) | 16 | zigzag | 1.828 | 1.869 | 1.02x | 5.883 | 5.826
| 0.99x |
| P4 (254,976 / 1) | 16 | per-document zigzag + ragged | 2.309 | 2.303 |
1.00x | 7.256 | 7.296 | 1.01x |
| P5 (249,856 / 4) | 2 | contiguous | 8.234 | 8.407 | 1.02x | 25.292 |
25.613 | 1.01x |
| P5 (249,856 / 4) | 2 | zigzag | 8.874 | 9.027 | 1.02x | 27.206 |
27.527 | 1.01x |
| P5 (249,856 / 4) | 2 | per-document zigzag + ragged | 8.447 | 8.637 |
1.02x | 25.705 | 26.067 | 1.01x |
| P5 (249,856 / 4) | 4 | contiguous | 4.315 | 4.391 | 1.02x | 13.040 |
13.192 | 1.01x |
| P5 (249,856 / 4) | 4 | zigzag | 4.417 | 4.497 | 1.02x | 13.217 |
13.376 | 1.01x |
| P5 (249,856 / 4) | 4 | per-document zigzag + ragged | 4.608 | 4.699 |
1.02x | 13.767 | 13.938 | 1.01x |
| P5 (249,856 / 4) | 8 | contiguous | 2.652 | 2.655 | 1.00x | 8.064 |
8.052 | 1.00x |
| P5 (249,856 / 4) | 8 | zigzag | 2.772 | 2.831 | 1.02x | 7.877 | 8.004
| 1.02x |
| P5 (249,856 / 4) | 8 | per-document zigzag + ragged | 2.679 | 2.727 |
1.02x | 7.779 | 7.871 | 1.01x |
| P5 (249,856 / 4) | 16 | contiguous | 2.209 | 2.195 | 0.99x | 6.964 |
6.935 | 1.00x |
| P5 (249,856 / 4) | 16 | zigzag | 1.798 | 1.808 | 1.01x | 5.810 | 5.814
| 1.00x |
| P5 (249,856 / 4) | 16 | per-document zigzag + ragged | 2.027 | 2.030 |
1.00x | 6.610 | 6.518 | 0.99x |

Cake also ships these separately: a non-deterministic variant of this
kernel (`flashinfer/experimental/cake_gdn_train_kcp`), single-GPU GDN
training packages without context parallelism
(`flashinfer/experimental/cake_gdn_det_train` deterministic and
`flashinfer/experimental/cake_gdn_train`), GDN inference kernels for
chunked prefill and decode, and the KDA deterministic context-parallel
training sibling `flashinfer/experimental/cake_kda_det_train_kcp`, which
covers the per-channel-gate form; this kernel ships on sm_100a, sm_103a
and sm_107a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Documentation**
* Clarified how the default workspace estimate relates to replay-form
tapes, and how enabling tape reuse changes the estimate by keeping
hand-off tensors outside the workspace.
* **Improvements**
* Updated the KCP training kernel’s shared-memory configuration and
execution pipeline. These changes may affect kernel performance; results
can vary by workload and hardware.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [70929a4](https://github.com/flashinfer-ai/flashinfer/commit/70929a45a12b4801f560b3ec11c875dd858ef4c9)

- **作者**: eigen
- **时间**: 2026-11-01T17:04:48Z
- **提交信息**: perf(cake_rmsnorm_silu_gate): non-deterministic mid-input forward on SM100/SM103 (#8217)

`cake_rmsnorm_silu_gate` computes `y = RMSNorm(x, w) * SiLU(z)` on BF16
rows of head dim 128 and has five variants: one forward, plus a
deterministic and a non-deterministic backward that each write the
weight gradient in BF16 or FP32. This PR changes only the
`deterministic=False` (non-deterministic) path as shipped by #8164 and
#8178. The API and the numerical contract stay the same: y, dx and dz
remain bitwise equal to the deterministic path, and dw stays within the
deterministic backward's error bound. On sm_100a and sm_103a, inputs
from 976 up to 2400 rows (T x H) per SM now run a mid-input forward. It
uses the long forward's kernel from #8178 on 128-thread CTAs of 16-row
blocks, with at most 6 CTAs per SM. It runs in the fewest whole waves
that give no CTA more than 2 blocks. y stays bitwise equal to the
deterministic forward. From 2400 rows per SM, the long forward of #8178
runs as before. Below 976 rows per SM, the forward is unchanged. sm_107a
is unchanged. There is one table per GPU: B200 (sm_100a, 148 SMs) and
GB300 (sm_103a, 152 SMs). Each table has one row per shape of the owner
list (H = 48 and H = 32) for `fwd` (eager call) and `ckpt 2×fwd+bwd
(CUDA graph)`. Each row gives absolute µs for deterministic Cake, the
best non-Cake (named per row: torch.compile or FLA), the previous Cake
(#8178) and the new path. A ratio above 1 means the new path is faster.
`(n.s.)` marks a ratio within the round spread. The changed rows are
those noted `fwd_mid (changed)` (forward) or `two fwd_mid forwards
(changed) + unchanged backward` (checkpointed step). Rows noted `same
code as #8178` run identical code, so their ratio against #8178 is
measurement noise and carries no claim. The ranges below cover the
changed rows only.

### Speedup

- `fwd` vs deterministic Cake: B200 1.010-1.042x, GB300 1.013-1.027x.
- `fwd` vs #8178: B200 1.016-1.041x, GB300 1.003-1.029x (GB300 4636×32
n.s.).
- `ckpt 2×fwd+bwd (CUDA graph)` vs deterministic Cake: B200
1.044-1.074x, GB300 1.032-1.061x.
- `ckpt 2×fwd+bwd (CUDA graph)` vs #8178: B200 1.007-1.023x (4514×32
n.s.), GB300 1.008-1.019x (4636×32 n.s.).
- vs best non-Cake: the forward alone is 0.927-0.984x on B200 and
0.931-1.011x on GB300. torch.compile or FLA is faster on the forward
alone in every changed B200 row and in 5 of the 10 changed GB300 rows.
The checkpointed step is 1.029-1.056x on B200 and 0.998-1.019x on GB300.

**NVIDIA B200 (sm_100a, 148 SMs), driver 580.82.07, CUDA 13.4, PyTorch
2.14.1+cu130**

| T × H (rows/SM) | op | det Cake (µs) | best non-Cake (µs) | previous
Cake, #8178 (µs) | new (µs) | vs det | vs non-Cake | vs #8178 | note |
|---:|---|---:|---:|---:|---:|---:|---:|---:|---|
| 1x48 (0) | fwd | 2.5 | 1.9 (torch.compile max-autotune) | 2.5 | 2.5 |
1.000x (n.s.) | 0.753x | 1.000x (n.s.) | same code as #8178 |
| 1x48 (0) | ckpt 2×fwd+bwd (CUDA graph) | 9.4 | 6.4 (torch.compile
max-autotune) | 8.8 | 9.0 | 1.054x (n.s.) | 0.709x | 0.979x (n.s.) |
same code as #8178 |
| 7x48 (2) | fwd | 3.0 | 2.4 (torch.compile) | 3.0 | 3.0 | 1.000x (n.s.)
| 0.800x | 1.000x (n.s.) | same code as #8178 |
| 7x48 (2) | ckpt 2×fwd+bwd (CUDA graph) | 9.3 | 9.1 (torch.compile
max-autotune) | 9.1 | 9.1 | 1.021x (n.s.) | 0.998x | 0.996x (n.s.) |
same code as #8178 |
| 129x48 (42) | fwd | 3.7 | 3.1 (torch.compile max-autotune) | 3.7 | 3.7
| 1.000x (n.s.) | 0.838x | 1.000x (n.s.) | same code as #8178 |
| 129x48 (42) | ckpt 2×fwd+bwd (CUDA graph) | 12.9 | 14.6 (torch.compile
max-autotune) | 12.0 | 12.0 | 1.069x | 1.210x | 0.997x (n.s.) | same
code as #8178 |
| 1031x48 (334) | fwd | 10.7 | 9.8 (torch.compile max-autotune) | 10.8 |
10.7 | 0.999x (n.s.) | 0.916x | 1.006x (n.s.) | same code as #8178 |
| 1031x48 (334) | ckpt 2×fwd+bwd (CUDA graph) | 39.0 | 50.8 (FLA) | 36.0
| 36.0 | 1.085x | 1.413x | 1.000x (n.s.) | same code as #8178 |
| 2048x48 (664) | fwd | 17.8 | 16.7 (torch.compile max-autotune) | 17.8
| 17.7 | 1.005x (n.s.) | 0.944x | 1.005x (n.s.) | same code as #8178 |
| 2048x48 (664) | ckpt 2×fwd+bwd (CUDA graph) | 65.7 | 66.2 (FLA) | 63.3
| 63.3 | 1.038x | 1.046x | 1.000x (n.s.) | same code as #8178 |
| 2600x48 (843) | fwd | 21.7 | 20.4 (torch.compile) | 21.8 | 21.8 |
0.997x (n.s.) | 0.935x | 0.999x (n.s.) | same code as #8178 |
| 2600x48 (843) | ckpt 2×fwd+bwd (CUDA graph) | 85.1 | 82.3 (FLA) | 79.0
| 79.0 | 1.077x | 1.042x | 1.000x (n.s.) | same code as #8178 |
| 3010x48 (976) | fwd | 24.6 | 23.4 (torch.compile) | 24.8 | 24.4 |
1.010x | 0.959x | 1.016x | fwd_mid (changed) |
| 3010x48 (976) | ckpt 2×fwd+bwd (CUDA graph) | 94.7 | 93.0 (FLA) | 89.3
| 88.7 | 1.068x | 1.048x | 1.007x | two fwd_mid forwards (changed) +
unchanged backward |
| 3200x48 (1038) | fwd | 26.4 | 23.9 (torch.compile) | 26.5 | 25.6 |
1.031x | 0.934x | 1.035x | fwd_mid (changed) |
| 3200x48 (1038) | ckpt 2×fwd+bwd (CUDA graph) | 98.1 | 97.9 (FLA) |
95.2 | 93.5 | 1.049x | 1.046x | 1.018x | two fwd_mid forwards (changed)
+ unchanged backward |
| 4097x48 (1329) | fwd | 32.4 | 30.8 (torch.compile max-autotune) | 32.4
| 31.5 | 1.030x | 0.981x | 1.031x | fwd_mid (changed) |
| 4097x48 (1329) | ckpt 2×fwd+bwd (CUDA graph) | 119.4 | 118.9 (FLA) |
116.6 | 114.4 | 1.044x | 1.039x | 1.019x | two fwd_mid forwards
(changed) + unchanged backward |
| 5000x48 (1622) | fwd | 38.7 | 35.7 (torch.compile max-autotune) | 38.6
| 37.7 | 1.025x | 0.947x | 1.023x | fwd_mid (changed) |
| 5000x48 (1622) | ckpt 2×fwd+bwd (CUDA graph) | 144.3 | 141.9 (FLA) |
139.4 | 137.6 | 1.049x | 1.031x | 1.013x | two fwd_mid forwards
(changed) + unchanged backward |
| 6000x48 (1946) | fwd | 45.3 | 42.9 (torch.compile) | 45.3 | 44.3 |
1.025x | 0.970x | 1.025x | fwd_mid (changed) |
| 6000x48 (1946) | ckpt 2×fwd+bwd (CUDA graph) | 168.1 | 165.4 (FLA) |
162.8 | 160.7 | 1.046x | 1.029x | 1.013x | two fwd_mid forwards
(changed) + unchanged backward |
| 7000x48 (2270) | fwd | 52.4 | 49.5 (torch.compile) | 52.3 | 50.3 |
1.042x | 0.984x | 1.041x | fwd_mid (changed) |
| 7000x48 (2270) | ckpt 2×fwd+bwd (CUDA graph) | 192.2 | 189.5 (FLA) |
187.3 | 183.2 | 1.049x | 1.035x | 1.023x | two fwd_mid forwards
(changed) + unchanged backward |
| 8192x48 (2657) | fwd | 60.2 | 53.7 (torch.compile max-autotune) | 54.7
| 54.6 | 1.102x | 0.983x | 1.002x | same code as #8178 |
| 8192x48 (2657) | ckpt 2×fwd+bwd (CUDA graph) | 220.6 | 217.9 (FLA) |
206.6 | 206.5 | 1.068x | 1.055x | 1.000x (n.s.) | same code as #8178 |
| 16384x48 (5314) | fwd | 113.4 | 101.4 (torch.compile max-autotune) |
101.7 | 101.9 | 1.113x | 0.996x | 0.998x | same code as #8178 |
| 16384x48 (5314) | ckpt 2×fwd+bwd (CUDA graph) | 414.3 | 412.1 (FLA) |
384.6 | 384.7 | 1.077x | 1.071x | 1.000x (n.s.) | same code as #8178 |
| 30000x48 (9730) | fwd | 202.1 | 189.0 (torch.compile max-autotune) |
179.2 | 179.3 | 1.127x | 1.054x | 0.999x (n.s.) | same code as #8178 |
| 30000x48 (9730) | ckpt 2×fwd+bwd (CUDA graph) | 744.1 | 733.9 (FLA) |
699.0 | 690.6 | 1.077x (n.s.) | 1.063x | 1.012x (n.s.) | same code as
#8178 |
| 30193x48 (9792) | fwd | 204.0 | 198.2 (torch.compile) | 180.5 | 180.9
| 1.128x | 1.095x | 0.998x (n.s.) | same code as #8178 |
| 30193x48 (9792) | ckpt 2×fwd+bwd (CUDA graph) | 748.1 | 737.8 (FLA) |
700.1 | 704.7 | 1.062x (n.s.) | 1.047x | 0.993x (n.s.) | same code as
#8178 |
| 32388x48 (10504) | fwd | 218.0 | 202.0 (torch.compile max-autotune) |
192.9 | 192.8 | 1.131x | 1.048x | 1.000x (n.s.) | same code as #8178 |
| 32388x48 (10504) | ckpt 2×fwd+bwd (CUDA graph) | 801.0 | 780.4
(torch.compile max-autotune) | 757.3 | 739.3 | 1.084x | 1.056x | 1.024x
(n.s.) | same code as #8178 |
| 32737x48 (10617) | fwd | 219.8 | 214.3 (FLA) | 194.4 | 194.3 | 1.131x
| 1.103x | 1.000x (n.s.) | same code as #8178 |
| 32737x48 (10617) | ckpt 2×fwd+bwd (CUDA graph) | 809.1 | 795.9 (FLA) |
755.0 | 766.4 | 1.056x (n.s.) | 1.038x | 0.985x (n.s.) | same code as
#8178 |
| 33000x48 (10703) | fwd | 221.7 | 206.1 (torch.compile max-autotune) |
196.0 | 196.1 | 1.130x | 1.051x | 1.000x (n.s.) | same code as #8178 |
| 33000x48 (10703) | ckpt 2×fwd+bwd (CUDA graph) | 815.1 | 794.0
(torch.compile max-autotune) | 765.2 | 758.8 | 1.074x | 1.046x | 1.008x
(n.s.) | same code as #8178 |
| 4000x32 (865) | fwd | 22.4 | 20.5 (torch.compile) | 22.3 | 22.6 |
0.992x (n.s.) | 0.908x | 0.989x | same code as #8178 |
| 4000x32 (865) | ckpt 2×fwd+bwd (CUDA graph) | 87.6 | 83.4 (FLA) | 80.9
| 80.9 | 1.084x | 1.032x | 1.000x (n.s.) | same code as #8178 |
| 4514x32 (976) | fwd | 24.9 | 22.9 (torch.compile) | 24.9 | 24.3 |
1.025x | 0.943x | 1.025x | fwd_mid (changed) |
| 4514x32 (976) | ckpt 2×fwd+bwd (CUDA graph) | 94.7 | 93.2 (FLA) | 89.0
| 88.2 | 1.073x | 1.056x | 1.009x (n.s.) | two fwd_mid forwards
(changed) + unchanged backward |
| 6000x32 (1297) | fwd | 31.6 | 29.4 (torch.compile max-autotune) | 31.6
| 30.5 | 1.038x | 0.966x | 1.037x | fwd_mid (changed) |
| 6000x32 (1297) | ckpt 2×fwd+bwd (CUDA graph) | 119.7 | 117.7 (FLA) |
113.6 | 111.5 | 1.074x | 1.056x | 1.019x | two fwd_mid forwards
(changed) + unchanged backward |
| 8192x32 (1771) | fwd | 41.6 | 37.3 (torch.compile max-autotune) | 41.7
| 40.3 | 1.033x | 0.927x | 1.036x | fwd_mid (changed) |
| 8192x32 (1771) | ckpt 2×fwd+bwd (CUDA graph) | 153.1 | 152.7 (FLA) |
148.6 | 146.1 | 1.048x | 1.045x | 1.017x | two fwd_mid forwards
(changed) + unchanged backward |
| 10000x32 (2162) | fwd | 49.4 | 46.7 (torch.compile max-autotune) |
49.4 | 48.0 | 1.031x | 0.974x | 1.029x | fwd_mid (changed) |
| 10000x32 (2162) | ckpt 2×fwd+bwd (CUDA graph) | 184.6 | 182.1 (FLA) |
178.1 | 175.1 | 1.054x | 1.040x | 1.017x | two fwd_mid forwards
(changed) + unchanged backward |
| 16384x32 (3542) | fwd | 78.1 | 69.2 (torch.compile max-autotune) |
70.3 | 70.3 | 1.112x | 0.984x | 1.001x | same code as #8178 |
| 16384x32 (3542) | ckpt 2×fwd+bwd (CUDA graph) | 285.8 | 283.5 (FLA) |
264.5 | 264.5 | 1.081x | 1.072x | 1.000x (n.s.) | same code as #8178 |
| 32737x32 (7078) | fwd | 149.5 | 139.8 (torch.compile max-autotune) |
133.0 | 132.7 | 1.126x | 1.053x | 1.002x | same code as #8178 |
| 32737x32 (7078) | ckpt 2×fwd+bwd (CUDA graph) | 549.0 | 537.1
(torch.compile max-autotune) | 503.4 | 503.3 | 1.091x | 1.067x | 1.000x
(n.s.) | same code as #8178 |

**NVIDIA GB300 (sm_103a, 152 SMs), driver 580.159.03, CUDA 13.4, PyTorch
2.14.1+cu130**

| T × H (rows/SM) | op | det Cake (µs) | best non-Cake (µs) | previous
Cake, #8178 (µs) | new (µs) | vs det | vs non-Cake | vs #8178 | note |
|---:|---|---:|---:|---:|---:|---:|---:|---:|---|
| 1x48 (0) | fwd | 2.5 | 2.3 (mamba_ssm) | 2.5 | 2.5 | 1.000x (n.s.) |
0.922x | 1.000x (n.s.) | same code as #8178 |
| 1x48 (0) | ckpt 2×fwd+bwd (CUDA graph) | 9.6 | 10.9 (torch.compile) |
8.9 | 8.9 | 1.078x (n.s.) | 1.233x | 1.002x (n.s.) | same code as #8178
|
| 7x48 (2) | fwd | 2.8 | 2.5 (mamba_ssm) | 2.8 | 2.8 | 1.000x (n.s.) |
0.888x | 1.000x (n.s.) | same code as #8178 |
| 7x48 (2) | ckpt 2×fwd+bwd (CUDA graph) | 9.8 | 12.9 (FLA) | 8.8 | 8.9
| 1.106x (n.s.) | 1.456x | 0.995x (n.s.) | same code as #8178 |
| 129x48 (41) | fwd | 3.7 | 3.4 (FLA) | 3.7 | 3.7 | 1.000x (n.s.) |
0.930x | 1.000x (n.s.) | same code as #8178 |
| 129x48 (41) | ckpt 2×fwd+bwd (CUDA graph) | 13.1 | 16.0 (torch.compile
max-autotune) | 11.6 | 11.6 | 1.125x | 1.382x | 1.003x (n.s.) | same
code as #8178 |
| 1031x48 (326) | fwd | 10.0 | 10.0 (FLA) | 9.9 | 9.9 | 1.002x (n.s.) |
1.008x | 0.998x (n.s.) | same code as #8178 |
| 1031x48 (326) | ckpt 2×fwd+bwd (CUDA graph) | 37.0 | 43.6 (FLA) | 33.2
| 33.2 | 1.115x | 1.314x | 1.000x (n.s.) | same code as #8178 |
| 2048x48 (647) | fwd | 16.9 | 16.3 (torch.compile max-autotune) | 16.7
| 16.7 | 1.012x (n.s.) | 0.977x | 1.004x (n.s.) | same code as #8178 |
| 2048x48 (647) | ckpt 2×fwd+bwd (CUDA graph) | 62.2 | 62.0 (FLA) | 58.6
| 58.6 | 1.061x | 1.057x | 0.999x (n.s.) | same code as #8178 |
| 2600x48 (821) | fwd | 20.3 | 20.1 (FLA) | 20.2 | 20.2 | 1.002x (n.s.)
| 0.995x | 1.000x (n.s.) | same code as #8178 |
| 2600x48 (821) | ckpt 2×fwd+bwd (CUDA graph) | 80.8 | 74.9 (FLA) | 74.4
| 74.4 | 1.086x | 1.007x | 1.001x (n.s.) | same code as #8178 |
| 3091x48 (976) | fwd | 23.8 | 23.6 (FLA) | 24.0 | 23.4 | 1.019x |
1.011x | 1.026x | fwd_mid (changed) |
| 3091x48 (976) | ckpt 2×fwd+bwd (CUDA graph) | 89.5 | 88.0 (FLA) | 87.4
| 86.7 | 1.032x | 1.015x | 1.008x | two fwd_mid forwards (changed) +
unchanged backward |
| 3200x48 (1011) | fwd | 24.4 | 24.3 (torch.compile max-autotune) | 24.7
| 24.1 | 1.013x | 1.008x | 1.024x | fwd_mid (changed) |
| 3200x48 (1011) | ckpt 2×fwd+bwd (CUDA graph) | 92.9 | 89.8 (FLA) |
90.6 | 89.5 | 1.037x | 1.003x | 1.012x | two fwd_mid forwards (changed)
+ unchanged backward |
| 4097x48 (1294) | fwd | 30.2 | 27.5 (torch.compile) | 30.0 | 29.4 |
1.027x | 0.937x | 1.021x | fwd_mid (changed) |
| 4097x48 (1294) | ckpt 2×fwd+bwd (CUDA graph) | 112.1 | 110.5 (FLA) |
110.1 | 108.4 | 1.035x | 1.019x | 1.016x | two fwd_mid forwards
(changed) + unchanged backward |
| 5000x48 (1579) | fwd | 36.2 | 33.1 (torch.compile) | 36.1 | 35.5 |
1.021x | 0.931x | 1.018x | fwd_mid (changed) |
| 5000x48 (1579) | ckpt 2×fwd+bwd (CUDA graph) | 136.3 | 130.6 (FLA) |
132.5 | 130.9 | 1.041x | 0.998x | 1.012x | two fwd_mid forwards
(changed) + unchanged backward |
| 6000x48 (1895) | fwd | 42.4 | 41.6 (FLA) | 42.5 | 41.3 | 1.026x |
1.007x | 1.029x | fwd_mid (changed) |
| 6000x48 (1895) | ckpt 2×fwd+bwd (CUDA graph) | 158.2 | 153.2 (FLA) |
153.8 | 151.2 | 1.046x | 1.013x | 1.017x | two fwd_mid forwards
(changed) + unchanged backward |
| 7000x48 (2211) | fwd | 48.4 | 47.5 (FLA) | 48.4 | 47.5 | 1.021x |
1.002x | 1.019x | fwd_mid (changed) |
| 7000x48 (2211) | ckpt 2×fwd+bwd (CUDA graph) | 180.2 | 175.4 (FLA) |
176.2 | 173.1 | 1.041x | 1.014x | 1.018x | two fwd_mid forwards
(changed) + unchanged backward |
| 8192x48 (2587) | fwd | 56.0 | 53.6 (torch.compile max-autotune) | 51.4
| 51.8 | 1.080x | 1.033x | 0.992x | same code as #8178 |
| 8192x48 (2587) | ckpt 2×fwd+bwd (CUDA graph) | 206.9 | 202.5 (FLA) |
193.3 | 193.4 | 1.070x | 1.047x | 0.999x (n.s.) | same code as #8178 |
| 16384x48 (5174) | fwd | 106.3 | 103.9 (FLA) | 96.0 | 96.1 | 1.107x |
1.082x | 0.999x (n.s.) | same code as #8178 |
| 16384x48 (5174) | ckpt 2×fwd+bwd (CUDA graph) | 390.4 | 383.5 (FLA) |
361.8 | 361.7 | 1.079x | 1.060x | 1.000x (n.s.) | same code as #8178 |
| 30000x48 (9474) | fwd | 191.2 | 177.4 (torch.compile max-autotune) |
169.0 | 169.2 | 1.130x | 1.048x | 0.999x | same code as #8178 |
| 30000x48 (9474) | ckpt 2×fwd+bwd (CUDA graph) | 702.8 | 685.7 (FLA) |
640.7 | 640.7 | 1.097x | 1.070x | 1.000x (n.s.) | same code as #8178 |
| 30193x48 (9535) | fwd | 191.5 | 177.8 (torch.compile max-autotune) |
170.2 | 170.0 | 1.126x | 1.046x | 1.001x | same code as #8178 |
| 30193x48 (9535) | ckpt 2×fwd+bwd (CUDA graph) | 704.8 | 679.0
(torch.compile max-autotune) | 643.1 | 643.2 | 1.096x | 1.056x | 1.000x
(n.s.) | same code as #8178 |
| 32388x48 (10228) | fwd | 204.3 | 190.2 (torch.compile max-autotune) |
182.0 | 181.4 | 1.126x | 1.049x | 1.003x | same code as #8178 |
| 32388x48 (10228) | ckpt 2×fwd+bwd (CUDA graph) | 753.7 | 721.5
(torch.compile max-autotune) | 687.0 | 686.9 | 1.097x | 1.050x | 1.000x
(n.s.) | same code as #8178 |
| 32737x48 (10338) | fwd | 206.3 | 192.4 (torch.compile max-autotune) |
184.2 | 182.8 | 1.129x | 1.053x | 1.008x | same code as #8178 |
| 32737x48 (10338) | ckpt 2×fwd+bwd (CUDA graph) | 760.3 | 742.5 (FLA) |
693.6 | 693.7 | 1.096x | 1.070x | 1.000x (n.s.) | same code as #8178 |
| 33000x48 (10421) | fwd | 210.0 | 195.5 (torch.compile max-autotune) |
185.6 | 185.4 | 1.133x | 1.054x | 1.001x | same code as #8178 |
| 33000x48 (10421) | ckpt 2×fwd+bwd (CUDA graph) | 769.8 | 752.4 (FLA) |
701.4 | 701.4 | 1.097x | 1.073x | 1.000x (n.s.) | same code as #8178 |
| 4000x32 (842) | fwd | 20.9 | 19.2 (torch.compile) | 21.0 | 20.9 |
1.002x (n.s.) | 0.919x | 1.008x (n.s.) | same code as #8178 |
| 4000x32 (842) | ckpt 2×fwd+bwd (CUDA graph) | 83.0 | 81.1 (FLA) | 76.7
| 77.0 | 1.077x | 1.053x | 0.997x (n.s.) | same code as #8178 |
| 4636x32 (976) | fwd | 23.8 | 23.4 (FLA) | 23.6 | 23.5 | 1.014x |
0.993x | 1.003x (n.s.) | fwd_mid (changed) |
| 4636x32 (976) | ckpt 2×fwd+bwd (CUDA graph) | 89.4 | 87.7 (FLA) | 87.1
| 86.4 | 1.035x | 1.016x | 1.008x (n.s.) | two fwd_mid forwards
(changed) + unchanged backward |
| 6000x32 (1263) | fwd | 29.6 | 27.7 (torch.compile max-autotune) | 29.7
| 28.9 | 1.024x | 0.959x | 1.028x | fwd_mid (changed) |
| 6000x32 (1263) | ckpt 2×fwd+bwd (CUDA graph) | 113.8 | 107.8 (FLA) |
108.7 | 107.2 | 1.061x | 1.005x | 1.014x | two fwd_mid forwards
(changed) + unchanged backward |
| 8192x32 (1725) | fwd | 38.7 | 35.6 (torch.compile max-autotune) | 38.8
| 38.1 | 1.015x | 0.933x | 1.017x | fwd_mid (changed) |
| 8192x32 (1725) | ckpt 2×fwd+bwd (CUDA graph) | 143.9 | 141.7 (FLA) |
141.1 | 139.4 | 1.032x | 1.016x | 1.012x | two fwd_mid forwards
(changed) + unchanged backward |
| 10000x32 (2105) | fwd | 46.5 | 45.8 (FLA) | 46.6 | 45.3 | 1.025x |
1.010x | 1.029x | fwd_mid (changed) |
| 10000x32 (2105) | ckpt 2×fwd+bwd (CUDA graph) | 174.5 | 169.0 (FLA) |
169.4 | 166.2 | 1.050x | 1.017x | 1.019x | two fwd_mid forwards
(changed) + unchanged backward |
| 16384x32 (3449) | fwd | 73.0 | 71.4 (FLA) | 65.7 | 65.9 | 1.108x |
1.084x | 0.997x | same code as #8178 |
| 16384x32 (3449) | ckpt 2×fwd+bwd (CUDA graph) | 268.6 | 262.7 (FLA) |
251.0 | 251.0 | 1.070x | 1.047x | 1.000x (n.s.) | same code as #8178 |
| 32737x32 (6892) | fwd | 139.8 | 135.8 (FLA) | 125.2 | 125.1 | 1.118x |
1.086x | 1.001x | same code as #8178 |
| 32737x32 (6892) | ckpt 2×fwd+bwd (CUDA graph) | 516.0 | 503.2 (FLA) |
472.2 | 472.1 | 1.093x | 1.066x | 1.000x (n.s.) | same code as #8178 |

Both modes cover sm_100a, sm_103a and sm_107a, and so do the other Cake
variants of this op (the default deterministic forward and backward, and
the FP32 weight-gradient output of both backward forms).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added a mid-sized workload route for SiLU-gated RMSNorm on SM100 and
SM103 GPUs, applying from 976 rows per SM up to the existing 2,400-row
threshold.
* The existing long-workload route remains in place from 2,400 rows per
SM. Both routes preserve the documented output bits.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [a887f33](https://github.com/flashinfer-ai/flashinfer/commit/a887f332af43d1115ff2a79334de8727e9919a17)

- **作者**: eigen
- **时间**: 2026-11-01T16:59:14Z
- **提交信息**: cake_gdn: route the remaining SM107 FP32-state head splits to the gate-streaming prefill body (up to 1.12x) (#8216)

`chunk_gated_delta_rule(backend="cake_gdn")` runs the Cake GDN non-CP
prefill with BF16 I/O and FP32 initial/final state. On SM 10.7 (R200,
sm_107a), its full-DV route has two bodies. One is the plain
`initial_sm107a_i64meta` body. The other is the faster
`initial_gatestream_full_sm107a_i64meta` body, which streams the gates.
FlashInfer already ships the gatestream_full body, but its sm_107a
records covered only three head splits: Hq16/Hv32, Hq8/Hv16 and Hq4/Hv8.
This PR adds the four missing sm_107a records, for Hq2/Hv4, Hq8/Hv32,
Hq4/Hv16 and Hq2/Hv8. Those shapes now select gatestream_full and no
longer fall back to the plain body. The PR adds no new kernel source,
and the selection rule is unchanged. "Previous" below is the plain-body
record those shapes used before this PR.

| shape (Hq/Hv, sequences) | s17 previous µs | s17 new µs | s17 speedup
| s29 previous µs | s29 new µs | s29 speedup | s17 auto µs | new vs auto
(s17) |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| 35b_tp8_hq2_hv4_64x256 (Hq2/Hv4) | 30.30 | 29.09 | 1.042 | 30.30 |
29.09 | 1.042 | 33.73 | 1.160 |
| 397b_tp2_hq8_hv32_16x512 (Hq8/Hv32) | 65.63 | 63.04 | 1.041 | 65.63 |
63.07 | 1.041 | 72.10 | 1.144 |
| 397b_tp2_hq8_hv32_32x512 (Hq8/Hv32) | 108.55 | 102.75 | 1.056 | 108.55
| 102.75 | 1.056 | 120.29 | 1.171 |
| 397b_tp2_hq8_hv32_64x256 (Hq8/Hv32) | 149.44 | 133.67 | 1.118 | 149.44
| 133.70 | 1.118 | 165.54 | 1.238 |
| 397b_tp4_hq4_hv16_16x512 (Hq4/Hv16) | 41.83 | 40.99 | 1.020 | 41.86 |
40.99 | 1.021 | 47.30 | 1.154 |
| 397b_tp4_hq4_hv16_32x512 (Hq4/Hv16) | 65.47 | 62.85 | 1.042 | 65.47 |
62.88 | 1.041 | 71.39 | 1.136 |
| 397b_tp4_hq4_hv16_64x256 (Hq4/Hv16) | 77.76 | 71.68 | 1.085 | 77.76 |
71.68 | 1.085 | 85.44 | 1.192 |
| 397b_tp8_hq2_hv8_32x512 (Hq2/Hv8) | 41.98 | 41.02 | 1.023 | 41.95 |
40.99 | 1.023 | 46.56 | 1.135 |
| 397b_tp8_hq2_hv8_64x256 (Hq2/Hv8) | 46.98 | 44.10 | 1.065 | 46.98 |
44.10 | 1.065 | 50.62 | 1.148 |

Rows are the 9 representative Qwen3.5-397B / Qwen3-Next-35B TP-split
shapes whose routing changes. Each label gives the model, TP degree,
head split and sequence pattern; for example, 64x256 means 64 sequences
of 256 tokens. Results are shown for seeds 17 (s17) and 29 (s29). "auto"
is `backend="auto"`. Measured on NVIDIA VR200 (R200), sm_107a, 212 SMs,
driver 620.43, with the CUDA 13.4 toolchain and CUDA runtime 13.0 (torch
2.14.1+cu130). Times are paired cold-L2 CUPTI GPU time, taking the
median of interleaved groups, with both columns run on the same node.
speedup = previous / new, so a value above 1 means faster. Every row is
checked against an FP32 reference.

Geomean speedup over the 9 rows and both seeds is 1.054 (min 1.020, max
1.118). The other 43 served representative rows in this geometry family
keep their records unchanged.

This kernel also has Cake records for BF16 state and FP32 state, on both
the dvsplit and full-DV routes, across sm_100a, sm_103a and sm_107a.
This PR changes only the sm_107a FP32-state full-DV records.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added support for additional SM107a prefill configurations with FP32
state, including varied query/value head sizes and final-state storage.
* **Tests**
* Added coverage for routing and output correctness across supported
head configurations and sequence lengths.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [de726d8](https://github.com/flashinfer-ai/flashinfer/commit/de726d8c4159d2719a789308232cff054c616a8f)

- **作者**: eigen
- **时间**: 2026-11-01T16:50:13Z
- **提交信息**: chore(cake_lm_head_det_loss): re-render the package from the merged Cake revision (#8214)

This PR re-renders `flashinfer.experimental.cake_lm_head_det_loss` from
the merged Cake revision. `build.json` now names that revision instead
of a pre-merge one. Twenty row-kernel sources each lose one unused line,
`#define NUM_MAIN_STAGES 1`, which no source refers to.

Performance is unchanged: every library built from `build.json` has SASS
identical to main's, 40 of 40 on sm_100a and 46 of 46 on sm_103a (CUDA
13.4.92), so there is no speedup to report.

The package has one data type (BF16) and covers the CE and policy
losses, the log-probability entry and the support-set log-probability
and KL entries; it ships on sm_100a and sm_103a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Chores**
  * Refreshed build metadata for existing GPU kernel variants.
* Simplified internal kernel configuration declarations. The changes do
not alter externally visible functionality, kernel interfaces, supported
architectures, build flags, or CUDA version.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [1feaf68](https://github.com/flashinfer-ai/flashinfer/commit/1feaf68dfbb861f0344a9cf61df8f68fc10df43b)

- **作者**: eigen
- **时间**: 2026-11-01T16:34:52Z
- **提交信息**: fix(cake_ssd_combined): refuse a seq_idx triple over more than one row (#8213)

`cake_ssd_combined` holds FlashInfer's Mamba2 SSD combined chunk-scan
prefill kernels. It has 56 programs in seven families: retained exact
scan (11), fused exact scan `exactfused` (11), two-kernel exact scan
`exactpre` (12), metadata-stage fused varlen `exactmeta` (5), one-launch
fused varlen `exactone` (5), chunk-parallel `chunkpar` (6) and
three-phase chunk-parallel `chunkpar3` (6). It also has 4 sm_107a-only
seq_idx check programs (`exactfused_{bf16,f32}_batched_{chk,zpfchk}`),
which #8132 added. This PR changes none of these programs. It changes
only a host-side input check in the runner, which runs before any
program launches. The packed-varlen `seq_idx` / `chunk_indices` /
`chunk_offsets` triple form describes one packed [1, total] token
stream. Before this PR, the runner accepted a call in that form with
batch > 1. It then ran every kernel with the geometry of one row. Rows
1..batch-1 were left unwritten, outputs were not repeatable, and on
sm_107a, partial-chunk stores could land past the end of `out`. The
runner now raises `ValueError` for the triple form with batch != 1
before any launch, as it already does for the cu_seqlens form. Batch-1
calls do not change: their outputs are bitwise identical, and every
architecture runs the same programs as before. As expected, speed does
not change compared with the previous Cake version (FlashInfer main
79f0637a4a9, which contains #8132). On each node, 0 shapes are faster,
93 are within band and 0 are slower. The geometric-mean speedup is
1.0000 on node 1 and 0.9999 on node 2.

**NVIDIA R200 (sm_107a, Rubin), CUDA 13.4.** Node 1 and Node 2 are two
different R200 nodes. Each value is the latency of one whole
`cake_ssd_combined` call with a cold L2, as the mean over 8 rounds of 4
input copies. On each node, both sides were measured on the same GPU,
interleaved. Speedup = main (79f0637a4a9) / this PR. A row counts as
faster or slower only if it falls outside its band. The band is the
largest of 0.5 %, the row's frozen noise band, and 2 standard errors.

| Shape | Node 1 main (µs) | Node 1 this PR (µs) | Node 1 speedup | Node
2 main (µs) | Node 2 this PR (µs) | Node 2 speedup |
|---|---:|---:|---:|---:|---:|---:|
| perf_varlen_1x1 | 7.216 | 7.218 | 0.9997 | 7.181 | 7.178 | 1.0003 |
| perf_varlen_4x1 | 7.399 | 7.395 | 1.0005 | 7.361 | 7.358 | 1.0004 |
| perf_varlen_8x1 | 7.727 | 7.725 | 1.0003 | 7.631 | 7.636 | 0.9994 |
| perf_varlen_32x1 | 11.932 | 11.932 | 1.0000 | 12.123 | 12.127 | 0.9997
|
| perf_varlen_64x1 | 16.107 | 16.114 | 0.9996 | 16.660 | 16.665 | 0.9997
|
| perf_varlen_128x1 | 24.272 | 24.280 | 0.9997 | 25.545 | 25.534 |
1.0004 |
| perf_varlen_256x1 | 41.367 | 41.371 | 0.9999 | 42.532 | 42.528 |
1.0001 |
| perf_varlen_4x8 | 20.716 | 20.719 | 0.9999 | 20.656 | 20.660 | 0.9998
|
| perf_varlen_8x8 | 21.065 | 21.066 | 0.9999 | 21.337 | 21.343 | 0.9997
|
| perf_varlen_16x8 | 24.100 | 24.099 | 1.0000 | 25.077 | 25.072 | 1.0002
|
| perf_varlen_32x8 | 38.695 | 38.701 | 0.9998 | 39.806 | 39.803 | 1.0001
|
| perf_varlen_64x8 | 60.405 | 60.405 | 1.0000 | 61.873 | 61.872 | 1.0000
|
| perf_varlen_32x32 | 99.939 | 99.961 | 0.9998 | 100.307 | 100.289 |
1.0002 |
| perf_varlen_64x32 | 179.356 | 179.362 | 1.0000 | 180.236 | 180.242 |
1.0000 |
| perf_varlen_128x32 | 347.430 | 347.427 | 1.0000 | 348.269 | 348.290 |
0.9999 |
| perf_batched_1x1 | 5.793 | 5.795 | 0.9997 | 5.761 | 5.762 | 0.9998 |
| perf_batched_1x4 | 10.701 | 10.701 | 1.0000 | 10.641 | 10.642 | 1.0000
|
| perf_batched_4x1 | 5.975 | 5.978 | 0.9995 | 5.940 | 5.942 | 0.9997 |
| perf_batched_4x4 | 10.884 | 10.885 | 1.0000 | 10.839 | 10.843 | 0.9996
|
| perf_batched_16x1 | 6.900 | 6.898 | 1.0003 | 6.917 | 6.921 | 0.9994 |
| perf_batched_16x4 | 12.403 | 12.404 | 0.9999 | 12.925 | 12.924 |
1.0001 |
| perf_batched_16x16 | 33.575 | 33.573 | 1.0001 | 34.831 | 34.824 |
1.0002 |
| perf_batched_64x1 | 12.499 | 12.497 | 1.0002 | 13.192 | 13.170 |
1.0017 |
| perf_batched_64x4 | 29.472 | 29.477 | 0.9998 | 31.303 | 31.314 |
0.9997 |
| perf_batched_64x16 | 87.515 | 87.518 | 1.0000 | 88.642 | 88.663 |
0.9998 |
| perf_batched_128x1 | 18.420 | 18.416 | 1.0002 | 19.426 | 19.432 |
0.9997 |
| perf_batched_128x4 | 48.451 | 48.459 | 0.9998 | 50.463 | 50.453 |
1.0002 |
| perf_batched_128x16 | 159.013 | 159.015 | 1.0000 | 159.972 | 159.969 |
1.0000 |
| perf_batched_256x1 | 32.038 | 32.038 | 1.0000 | 33.483 | 33.488 |
0.9998 |
| perf_batched_256x4 | 88.741 | 88.742 | 1.0000 | 90.841 | 90.828 |
1.0001 |
| perf_batched_256x16 | 307.807 | 307.794 | 1.0000 | 308.605 | 308.622 |
0.9999 |
| perf_batched_512x2 | 92.807 | 92.807 | 1.0000 | 94.159 | 94.155 |
1.0000 |
| correctness_base_b2_n1 | 5.876 | 5.878 | 0.9997 | 5.829 | 5.827 |
1.0003 |
| correctness_D_head_dim | 5.792 | 5.789 | 1.0005 | 5.764 | 5.765 |
0.9998 |
| correctness_no_D | 5.783 | 5.783 | 1.0000 | 5.741 | 5.742 | 0.9998 |
| correctness_initial_bf16 | 5.894 | 5.892 | 1.0003 | 5.858 | 5.857 |
1.0002 |
| correctness_varlen_single_256 | 7.477 | 7.475 | 1.0003 | 7.432 | 7.434
| 0.9997 |
| correctness_varlen_nonaligned_z | 10.539 | 10.538 | 1.0001 | 10.486 |
10.485 | 1.0001 |
| correctness_preallocated_output | 5.778 | 5.779 | 0.9998 | 5.738 |
5.739 | 0.9999 |
| correctness_no_final_states | 5.782 | 5.784 | 0.9996 | 5.739 | 5.740 |
0.9998 |
| correctness_seq_idx_int64 | 9.604 | 9.600 | 1.0004 | 9.502 | 9.504 |
0.9998 |
| correctness_fp16_state | 5.929 | 5.932 | 0.9995 | 5.886 | 5.889 |
0.9995 |
| correctness_z_b1_n1 | 6.564 | 6.562 | 1.0003 | 6.513 | 6.512 | 1.0001
|
| perf_nemotron_h_8b_c128_projection_batched_b1x1 | 8.073 | 8.073 |
1.0000 | 8.009 | 8.012 | 0.9996 |
| perf_nemotron_h_8b_c128_projection_varlen_4x1 | 19.491 | 19.486 |
1.0003 | 20.317 | 20.322 | 0.9998 |
| nem_v1x128_bfloat16 | 8.090 | 8.093 | 0.9996 | 8.025 | 8.026 | 0.9999
|
| nem_v4x128_bfloat16 | 19.525 | 19.540 | 0.9993 | 20.384 | 20.354 |
1.0015 |
| nem_v16x128_bfloat16 | 47.531 | 47.539 | 0.9998 | 49.468 | 49.444 |
1.0005 |
| nem_v64x128_bfloat16 | 172.002 | 172.003 | 1.0000 | 175.135 | 175.123
| 1.0001 |
| nem_v160x128_bfloat16 | 415.913 | 415.913 | 1.0000 | 421.375 | 421.372
| 1.0000 |
| nem_v64_64_bfloat16 | 14.024 | 14.019 | 1.0004 | 14.463 | 14.455 |
1.0006 |
| nem_v8x64_bfloat16 | 28.486 | 28.483 | 1.0001 | 29.396 | 29.394 |
1.0001 |
| nem_v1024_bfloat16 | 25.468 | 25.470 | 0.9999 | 25.524 | 25.510 |
1.0005 |
| nem_v1024x2_bfloat16 | 45.023 | 45.029 | 0.9999 | 45.958 | 45.935 |
1.0005 |
| nem_v2048_bfloat16 | 45.510 | 45.515 | 0.9999 | 44.461 | 44.449 |
1.0003 |
| nem_v128p896_bfloat16 | 29.328 | 29.401 | 0.9975 | 30.155 | 30.106 |
1.0016 |
| nem_v96p160_bfloat16 | 16.709 | 16.707 | 1.0001 | 16.895 | 16.892 |
1.0002 |
| nem_v1000_bfloat16 | 25.385 | 25.388 | 0.9999 | 25.422 | 25.430 |
0.9997 |
| nem_v1024p100_bfloat16 | 33.201 | 33.220 | 0.9994 | 33.154 | 33.265 |
0.9967 |
| nem_b1x1024_bfloat16 | 25.207 | 25.211 | 0.9998 | 25.373 | 25.371 |
1.0001 |
| nem_b1x2048_bfloat16 | 44.847 | 44.852 | 0.9999 | 44.111 | 44.099 |
1.0003 |
| nem_b1x1000_bfloat16 | 25.115 | 25.119 | 0.9998 | 25.294 | 25.294 |
1.0000 |
| nem_v1x128_float32 | 8.402 | 8.406 | 0.9995 | 8.376 | 8.375 | 1.0001 |
| nem_v4x128_float32 | 19.958 | 19.895 | 1.0032 | 20.769 | 20.849 |
0.9962 |
| nem_v16x128_float32 | 47.559 | 47.517 | 1.0009 | 48.836 | 48.890 |
0.9989 |
| nem_v64x128_float32 | 160.508 | 160.513 | 1.0000 | 163.174 | 163.184 |
0.9999 |
| nem_v160x128_float32 | 385.409 | 385.408 | 1.0000 | 390.392 | 390.391
| 1.0000 |
| nem_v64_64_float32 | 13.821 | 13.820 | 1.0000 | 14.257 | 14.256 |
1.0001 |
| nem_v8x64_float32 | 27.803 | 27.814 | 0.9996 | 28.538 | 28.543 |
0.9998 |
| nem_v1024_float32 | 25.501 | 25.502 | 1.0000 | 25.574 | 25.566 |
1.0003 |
| nem_v1024x2_float32 | 45.467 | 45.361 | 1.0023 | 46.509 | 46.564 |
0.9988 |
| nem_v2048_float32 | 45.723 | 45.727 | 0.9999 | 44.879 | 44.884 |
0.9999 |
| nem_v128p896_float32 | 29.808 | 29.797 | 1.0004 | 30.438 | 30.576 |
0.9955 |
| nem_v96p160_float32 | 16.897 | 16.901 | 0.9998 | 17.052 | 17.053 |
0.9999 |
| nem_v1000_float32 | 25.447 | 25.448 | 1.0000 | 25.526 | 25.525 |
1.0000 |
| nem_v1024p100_float32 | 33.595 | 33.641 | 0.9986 | 33.456 | 33.468 |
0.9996 |
| nem_b1x1024_float32 | 25.217 | 25.214 | 1.0001 | 25.413 | 25.420 |
0.9997 |
| nem_b1x2048_float32 | 45.196 | 45.193 | 1.0001 | 44.436 | 44.447 |
0.9997 |
| nem_b1x1000_float32 | 25.155 | 25.156 | 1.0000 | 25.355 | 25.368 |
0.9995 |
| short_varlen_1 | 5.607 | 5.605 | 1.0004 | 5.565 | 5.565 | 1.0001 |
| short_varlen_8 | 5.695 | 5.695 | 1.0000 | 5.661 | 5.662 | 0.9998 |
| short_varlen_8_f32 | 5.924 | 5.925 | 0.9998 | 5.897 | 5.896 | 1.0001 |
| short_varlen_127 | 6.951 | 6.950 | 1.0002 | 6.916 | 6.914 | 1.0003 |
| short_varlen_64_60 | 7.269 | 7.268 | 1.0002 | 7.209 | 7.210 | 0.9999 |
| short_batched_2x50 | 10.128 | 10.126 | 1.0002 | 10.175 | 10.176 |
0.9999 |
| short_batched_1x1 | 6.004 | 6.003 | 1.0002 | 5.952 | 5.951 | 1.0002 |
| perf_batched_1x16 | 20.154 | 20.139 | 1.0007 | 20.254 | 20.271 |
0.9992 |
| perf_batched_1x64 | 33.961 | 33.971 | 0.9997 | 34.505 | 34.491 |
1.0004 |
| perf_batched_1x256 | 68.567 | 68.592 | 0.9996 | 68.684 | 68.684 |
1.0000 |
| perf_batched_4x16 | 32.450 | 32.454 | 0.9999 | 32.581 | 32.588 |
0.9998 |
| perf_batched_4x64 | 65.831 | 65.833 | 1.0000 | 66.036 | 66.033 |
1.0000 |
| cp_b1h32c16 | 31.855 | 31.847 | 1.0002 | 32.042 | 32.046 | 0.9999 |
| cp_b4h8c16 | 32.752 | 32.738 | 1.0004 | 32.857 | 32.881 | 0.9993 |

The kernel ships on sm_100a (B200), sm_103a (B300/GB300) and sm_107a
(R200); the 4 seq_idx check programs from #8132 exist only on sm_107a,
and this PR leaves every program on all three architectures unchanged.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Packed variable-length inputs using sequence and chunk metadata now
require a batch size of 1. Larger batches return a clear error with
guidance to reshape the tokens into a single packed row.
  * Inputs using cumulative sequence lengths are unaffected.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [d3c37ca](https://github.com/flashinfer-ai/flashinfer/commit/d3c37ca08092733f8f4fc250f84b1e58cd3a9d4e)

- **作者**: eigen
- **时间**: 2026-11-01T16:31:21Z
- **提交信息**: perf(cake_gdn_kcp): with grad, lighter host path for the non-deterministic KCP package (#8212)

This PR changes `flashinfer.experimental.cake_gdn_train_kcp`, the
non-deterministic context-parallel variant of Cake's Gated DeltaNet
(GDN) chunked training kernel with gradients. Callers reach it through
`flashinfer.cake_gdn_train_kcp(deterministic=False)`. The change is
host-side only and has three parts:

1. The forward and backward bodies now enter one tvm-ffi stream context
per entry body. Before, they entered a context for every kernel launch.
A launch outside every scope still enters its own context, and so does a
launch after a stream switch inside a scope. Inside a CUDA graph
capture, the scope binds the capture stream.
2. The static launch arguments of each launch key (record, grid, test
flag, merge columns) are resolved once per context plan and kept with
the context's tables. Each launch still rebuilds its public values and
appends its launch record.
3. The public entry `flashinfer.cake_gdn_train_kcp` caches the two
package modules it routes to. Before, it re-imported the module on every
call. This also removes that per-call import from the
`deterministic=True` route, whose behavior is unchanged.

Device programs, launch order, grids, streams and workspace are
unchanged, and so are the checkpoint and graph-replay semantics. In
every timed run (eager and graph replay, both ranks), outputs and every
gradient are bitwise equal to main's non-deterministic package. Launch
records (programs and launch count per phase) are also equal.

Speedup is baseline latency / new latency, so values above 1 mean the
new package is faster. There are three baselines, and all of them ran in
the same process as the new package:

- **Deterministic Cake KCP:** the deterministic Cake KCP package from
main, called through its public entry.
- **Strongest non-Cake, per row:** the faster of FLA 0.6.0
context-parallel KCP (layout C) and a head-parallel all-to-all around
the cuDNN frontend 1.32.1 FROST GDN engine. Both were qualified by
comparison with the new package. FlashQLA has no sm_107a build, so these
two are the applicable candidates.
- **Previous non-deterministic:** main's non-deterministic KCP package.
It cannot share the public entry with the new package in one process, so
it is loaded as a renamed copy and called through an equivalent stand-in
entry. The stand-in skips the public entry's dispatch, so eager ratios
vs this package are conservative by up to about 1 % (a path-only control
with the new code on the stand-in entry measured 0.986-1.003 on
forward+backward).

All arms ran on one exclusive R200 node (sm_107a, 212 SMs; CUDA 13.0
runtime, PyTorch 2.14.1+cu130; no power capping observed). The setup was
CP2 (2 ranks, GPUs 0-1) with BF16 q/k/v, FP32 g/beta and head dim 128.

Protocol: 5 groups, each running the arms in palindromic order 2 times.
Each call is 12 timed iterations after 10 warm-up, with a 256 MiB L2
flush, device sync and barrier before every iteration. Latency is the
median CUDA-event time of the slowest rank, and speedup is the median of
the per-group ratios [min, max]. Two runs ran in separate processes, and
run 2 reverses the arm order. Eager uses default options. Graph replay
uses a caller-owned workspace with `graph="replay"`.

How to read the table:

- Backward = forward+backward − forward, per group.
- "(medians)" marks a ratio of medians.
- "unpaired" marks a non-Cake value measured with layout C for a
layout-D row.
- (H, HV) = (query/key heads, value heads).
- S26 = (2, 6), 3 documents of 2049/3001/3142 tokens (8192).
- DET = (2, 6), 65536 tokens in 6 documents.
- P1 = (16, 48), 241817 tokens.
- P3 = (16, 48), 259174 tokens.
- Layout C is contiguous; layout D is zigzag per document.

Five ratio cells are classed UNSTABLE because their group-to-group
spread is above the 1 % tolerance, all on S26 eager forward+backward
(two in run 1, three in run 2). They are shown as measured.

Table: R200 (sm_107a, 212 SMs), CUDA 13.0 runtime, PyTorch 2.14.1+cu130,
CP2; latencies in ms (median CUDA-event time of the slowest rank);
speedup = median of the per-group ratios [min, max].

| GPU / architecture | workload (pack, (H, HV), S tokens, CP, layout);
timing mode; run | operation | deterministic Cake (ms) | strongest
non-Cake (ms, implementation) | previous non-deterministic Cake (ms) |
new non-deterministic Cake (ms) | speedup vs deterministic Cake |
speedup vs non-Cake SOTA | speedup vs previous non-deterministic Cake |
|---|---|---|---|---|---|---|---|---|---|
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, C; eager; run 1 |
forward | 0.798 | 3.263 (FLA KCP) | 0.798 | 0.718 | 1.115 [1.099, 1.119]
| 4.538 [4.511, 4.590] | 1.113 [1.104, 1.115] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, C; eager; run 1 |
backward (= forward+backward − forward) | 1.321 | 3.711 (FLA KCP) |
1.327 | 1.213 | 1.094 [1.082, 1.103] | 3.060 [3.060, 3.060] (medians) |
1.096 [1.085, 1.106] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, C; eager; run 1 |
forward+backward | 2.118 | 6.974 (FLA KCP) | 2.125 | 1.930 | 1.102
[1.095, 1.103] | 3.616 [3.582, 3.649] | 1.101 [1.095, 1.110] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, C; eager; run 1 |
checkpointed 2×forward+backward | 3.147 | 10.154 (FLA KCP) | 3.158 |
2.888 | 1.089 [1.083, 1.095] | 3.505 [3.485, 3.535] | 1.090 [1.085,
1.098] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, C; graph replay; run
1 | forward | 0.543 | n/a (no graph-replay arm) | 0.524 | 0.526 | 1.033
[1.030, 1.034] | n/a | 0.997 [0.996, 1.001] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, C; graph replay; run
1 | backward (= forward+backward − forward) | 0.854 | n/a (no
graph-replay arm) | 0.831 | 0.833 | 1.026 [1.023, 1.028] | n/a | 0.998
[0.996, 0.998] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, C; graph replay; run
1 | forward+backward | 1.397 | n/a (no graph-replay arm) | 1.355 | 1.358
| 1.029 [1.027, 1.029] | n/a | 0.997 [0.997, 0.999] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, C; graph replay; run
1 | checkpointed 2×forward+backward | 1.934 | n/a (no graph-replay arm)
| 1.887 | 1.890 | 1.024 [1.022, 1.025] | n/a | 0.998 [0.997, 0.999] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, C; eager; run 2
(reversed arm order) | forward | 0.797 | 3.263 (FLA KCP) | 0.804 | 0.729
| 1.090 [1.083, 1.105] | 4.473 [4.473, 4.473] unpaired | 1.105 [1.097,
1.107] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, C; eager; run 2
(reversed arm order) | backward (= forward+backward − forward) | 1.327 |
3.711 (FLA KCP) | 1.326 | 1.204 | 1.099 [1.079, 1.104] | 3.082 [3.082,
3.082] (medians) | 1.096 [1.075, 1.105] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, C; eager; run 2
(reversed arm order) | forward+backward | 2.124 | 6.974 (FLA KCP) |
2.131 | 1.934 | 1.096 [1.083, 1.099] | 3.607 [3.607, 3.607] unpaired |
1.098 [1.086, 1.105] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, C; eager; run 2
(reversed arm order) | checkpointed 2×forward+backward | 3.154 | 10.154
(FLA KCP) | 3.179 | 2.922 | 1.078 [1.076, 1.082] | 3.474 [3.474, 3.474]
unpaired | 1.089 [1.083, 1.091] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, C; graph replay; run
2 (reversed arm order) | forward | 0.543 | n/a (no graph-replay arm) |
0.526 | 0.527 | 1.030 [1.028, 1.033] | n/a | 0.998 [0.997, 1.002] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, C; graph replay; run
2 (reversed arm order) | backward (= forward+backward − forward) | 0.851
| n/a (no graph-replay arm) | 0.835 | 0.834 | 1.020 [1.017, 1.022] | n/a
| 1.003 [0.999, 1.004] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, C; graph replay; run
2 (reversed arm order) | forward+backward | 1.393 | n/a (no graph-replay
arm) | 1.361 | 1.361 | 1.024 [1.023, 1.025] | n/a | 1.001 [1.000, 1.001]
|
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, C; graph replay; run
2 (reversed arm order) | checkpointed 2×forward+backward | 1.932 | n/a
(no graph-replay arm) | 1.895 | 1.893 | 1.020 [1.020, 1.021] | n/a |
1.001 [1.000, 1.001] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, D; eager; run 1 |
forward | 0.880 | 3.263 (FLA KCP) | 0.628 | 0.628 | 1.403 [1.397, 1.406]
| 5.194 [5.194, 5.194] unpaired | 0.999 [0.997, 1.002] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, D; eager; run 1 |
backward (= forward+backward − forward) | 1.397 | 3.711 (FLA KCP) |
0.997 | 0.868 | 1.616 [1.583, 1.624] | 4.273 [4.273, 4.273] (medians) |
1.149 [1.135, 1.160] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, D; eager; run 1 |
forward+backward | 2.277 | 6.974 (FLA KCP) | 1.625 | 1.497 | 1.526
[1.508, 1.531] | 4.660 [4.660, 4.660] unpaired | 1.086 [1.079, 1.092] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, D; eager; run 1 |
checkpointed 2×forward+backward | 3.392 | 10.154 (FLA KCP) | 2.601 |
2.401 | 1.415 [1.403, 1.422] | 4.229 [4.229, 4.229] unpaired | 1.082
[1.077, 1.090] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, D; graph replay; run
1 | forward | 0.596 | n/a (no graph-replay arm) | 0.589 | 0.589 | 1.011
[1.010, 1.014] | n/a | 1.000 [0.997, 1.000] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, D; graph replay; run
1 | backward (= forward+backward − forward) | 0.811 | n/a (no
graph-replay arm) | 0.809 | 0.808 | 1.004 [0.999, 1.006] | n/a | 1.001
[0.997, 1.004] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, D; graph replay; run
1 | forward+backward | 1.407 | n/a (no graph-replay arm) | 1.398 | 1.397
| 1.007 [1.006, 1.008] | n/a | 1.001 [0.998, 1.002] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, D; graph replay; run
1 | checkpointed 2×forward+backward | 2.036 | n/a (no graph-replay arm)
| 2.021 | 2.018 | 1.009 [1.008, 1.010] | n/a | 1.001 [1.001, 1.003] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, D; eager; run 2
(reversed arm order) | forward | 0.893 | 3.263 (FLA KCP) | 0.627 | 0.627
| 1.425 [1.420, 1.433] | 5.202 [5.202, 5.202] unpaired | 1.001 [0.999,
1.002] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, D; eager; run 2
(reversed arm order) | backward (= forward+backward − forward) | 1.408 |
3.711 (FLA KCP) | 1.021 | 0.886 | 1.581 [1.569, 1.608] | 4.187 [4.187,
4.187] (medians) | 1.148 [1.141, 1.164] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, D; eager; run 2
(reversed arm order) | forward+backward | 2.301 | 6.974 (FLA KCP) |
1.648 | 1.513 | 1.517 [1.513, 1.530] | 4.608 [4.608, 4.608] unpaired |
1.087 [1.084, 1.095] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, D; eager; run 2
(reversed arm order) | checkpointed 2×forward+backward | 3.415 | 10.154
(FLA KCP) | 2.597 | 2.381 | 1.431 [1.414, 1.448] | 4.264 [4.264, 4.264]
unpaired | 1.087 [1.077, 1.098] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, D; graph replay; run
2 (reversed arm order) | forward | 0.596 | n/a (no graph-replay arm) |
0.592 | 0.592 | 1.007 [1.006, 1.010] | n/a | 1.001 [0.999, 1.002] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, D; graph replay; run
2 (reversed arm order) | backward (= forward+backward − forward) | 0.810
| n/a (no graph-replay arm) | 0.812 | 0.812 | 0.997 [0.992, 1.001] | n/a
| 0.997 [0.995, 1.003] |
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, D; graph replay; run
2 (reversed arm order) | forward+backward | 1.406 | n/a (no graph-replay
arm) | 1.404 | 1.404 | 1.001 [1.000, 1.003] | n/a | 0.999 [0.998, 1.001]
|
| R200 sm_107a (212 SMs) | DET, (2, 6), 65536, CP2, D; graph replay; run
2 (reversed arm order) | checkpointed 2×forward+backward | 2.034 | n/a
(no graph-replay arm) | 2.029 | 2.028 | 1.004 [1.002, 1.004] | n/a |
1.001 [1.000, 1.002] |
| R200 sm_107a (212 SMs) | P1, (16, 48), 241817, CP2, C; eager; run 1 |
forward | 4.856 | 22.058 (FROST head-CP) | 4.795 | 4.794 | 1.013 [1.013,
1.013] | 4.601 [4.601, 4.601] unpaired | 1.000 [1.000, 1.000] |
| R200 sm_107a (212 SMs) | P1, (16, 48), 241817, CP2, C; eager; run 1 |
backward (= forward+backward − forward) | 8.545 | 32.074 (FROST head-CP)
| 8.542 | 8.549 | 1.000 [0.999, 1.000] | 3.752 [3.752, 3.752] (medians)
| 0.999 [0.999, 1.000] |
| R200 sm_107a (212 SMs) | P1, (16, 48), 241817, CP2, C; eager; run 1 |
forward+backward | 13.402 | 54.132 (FROST head-CP) | 13.336 | 13.344 |
1.004 [1.004, 1.005] | 4.057 [4.057, 4.057] unpaired | 0.999 [0.999,
1.000] |
| R200 sm_107a (212 SMs) | P1, (16, 48), 241817, CP2, C; eager; run 1 |
checkpointed 2×forward+backward | 15.075 | 70.721 (FROST head-CP) |
14.936 | 14.950 | 1.008 [1.008, 1.009] | 4.730 [4.730, 4.730] unpaired |
0.999 [0.998, 1.000] |
| R200 sm_107a (212 SMs) | P1, (16, 48), 241817, CP2, C; eager; run 2
(reversed arm order) | forward | 4.847 | 22.058 (FROST head-CP) | 4.781
| 4.783 | 1.013 [1.013, 1.014] | 4.611 [4.610, 4.615] | 0.999 [0.999,
1.000] |
| R200 sm_107a (212 SMs) | P1, (16, 48), 241817, CP2, C; eager; run 2
(reversed arm order) | backward (= forward+backward − forward) | 8.551 |
32.074 (FROST head-CP) | 8.549 | 8.554 | 1.000 [0.999, 1.001] | 3.750
[3.750, 3.750] (medians) | 0.999 [0.999, 1.001] |
| R200 sm_107a (212 SMs) | P1, (16, 48), 241817, CP2, C; eager; run 2
(reversed arm order) | forward+backward | 13.398 | 54.132 (FROST
head-CP) | 13.330 | 13.337 | 1.005 [1.004, 1.005] | 4.059 [4.058, 4.060]
| 0.999 [0.999, 1.000] |
| R200 sm_107a (212 SMs) | P1, (16, 48), 241817, CP2, C; eager; run 2
(reversed arm order) | checkpointed 2×forward+backward | 15.060 | 70.721
(FROST head-CP) | 14.926 | 14.930 | 1.009 [1.007, 1.009] | 4.737 [4.733,
4.740] | 1.000 [0.999, 1.001] |
| R200 sm_107a (212 SMs) | P3, (16, 48), 259174, CP2, C; eager; run 1 |
forward | 5.024 | 7.911 (FLA KCP) | 4.947 | 4.949 | 1.015 [1.014, 1.016]
| 1.599 [1.599, 1.599] unpaired | 1.000 [0.998, 1.000] |
| R200 sm_107a (212 SMs) | P3, (16, 48), 259174, CP2, C; eager; run 1 |
backward (= forward+backward − forward) | 9.085 | 51.819 (FROST head-CP
forward+backward − FLA KCP forward) | 9.075 | 9.073 | 1.002 [1.001,
1.002] | 5.711 [5.711, 5.711] (medians) | 1.000 [0.999, 1.002] |
| R200 sm_107a (212 SMs) | P3, (16, 48), 259174, CP2, C; eager; run 1 |
forward+backward | 14.109 | 59.730 (FROST head-CP) | 14.023 | 14.022 |
1.006 [1.006, 1.007] | 4.260 [4.260, 4.260] unpaired | 1.000 [1.000,
1.000] |
| R200 sm_107a (212 SMs) | P3, (16, 48), 259174, CP2, C; eager; run 1 |
checkpointed 2×forward+backward | 15.823 | 67.948 (FLA KCP) | 15.664 |
15.671 | 1.010 [1.009, 1.011] | 4.336 [4.336, 4.336] unpaired | 0.999
[0.999, 1.001] |
| R200 sm_107a (212 SMs) | P3, (16, 48), 259174, CP2, C; eager; run 2
(reversed arm order) | forward | 5.024 | 7.911 (FLA KCP) | 4.945 | 4.948
| 1.015 [1.015, 1.016] | 1.599 [1.598, 1.600] | 0.999 [0.998, 1.000] |
| R200 sm_107a (212 SMs) | P3, (16, 48), 259174, CP2, C; eager; run 2
(reversed arm order) | backward (= forward+backward − forward) | 9.079 |
51.819 (FROST head-CP forward+backward − FLA KCP forward) | 9.063 |
9.069 | 1.001 [1.000, 1.002] | 5.714 [5.714, 5.714] (medians) | 1.000
[0.997, 1.001] |
| R200 sm_107a (212 SMs) | P3, (16, 48), 259174, CP2, C; eager; run 2
(reversed arm order) | forward+backward | 14.103 | 59.730 (FROST
head-CP) | 14.007 | 14.017 | 1.006 [1.005, 1.007] | 4.261 [4.259, 4.263]
| 1.000 [0.998, 1.000] |
| R200 sm_107a (212 SMs) | P3, (16, 48), 259174, CP2, C; eager; run 2
(reversed arm order) | checkpointed 2×forward+backward | 15.815 | 67.948
(FLA KCP) | 15.651 | 15.660 | 1.010 [1.009, 1.010] | 4.339 [4.338,
4.339] | 0.999 [0.999, 1.000] |
| R200 sm_107a (212 SMs) | S26, (2, 6), 8192, CP2, C; eager; run 1 |
forward | 0.525 | 0.840 (FLA KCP) | 0.529 | 0.471 | 1.115 [1.098, 1.123]
| 1.785 [1.750, 1.799] | 1.122 [1.110, 1.128] |
| R200 sm_107a (212 SMs) | S26, (2, 6), 8192, CP2, C; eager; run 1 |
backward (= forward+backward − forward) | 0.780 | 0.736 (FLA KCP) |
0.772 | 0.706 | 1.109 [1.087, 1.126] | 1.042 [1.042, 1.042] (medians) |
1.088 [1.085, 1.121] |
| R200 sm_107a (212 SMs) | S26, (2, 6), 8192, CP2, C; eager; run 1 |
forward+backward | 1.305 | 1.576 (FLA KCP) | 1.301 | 1.177 | 1.110
[1.095, 1.121] UNSTABLE | 1.339 [1.339, 1.339] unpaired | 1.102 [1.097,
1.119] UNSTABLE |
| R200 sm_107a (212 SMs) | S26, (2, 6), 8192, CP2, C; eager; run 1 |
checkpointed 2×forward+backward | 2.223 | 2.557 (FLA KCP) | 2.240 |
2.062 | 1.079 [1.072, 1.086] | 1.236 [1.234, 1.256] | 1.087 [1.081,
1.093] |
| R200 sm_107a (212 SMs) | S26, (2, 6), 8192, CP2, C; graph replay; run
1 | forward | 0.306 | n/a (no graph-replay arm) | 0.298 | 0.299 | 1.023
[1.021, 1.024] | n/a | 0.996 [0.993, 0.997] |
| R200 sm_107a (212 SMs) | S26, (2, 6), 8192, CP2, C; graph replay; run
1 | backward (= forward+backward − forward) | 0.329 | n/a (no
graph-replay arm) | 0.329 | 0.326 | 1.007 [1.004, 1.013] | n/a | 1.006
[1.003, 1.010] |
| R200 sm_107a (212 SMs) | S26, (2, 6), 8192, CP2, C; graph replay; run
1 | forward+backward | 0.635 | n/a (no graph-replay arm) | 0.627 | 0.626
| 1.014 [1.013, 1.017] | n/a | 1.001 [1.000, 1.004] |
| R200 sm_107a (212 SMs) | S26, (2, 6), 8192, CP2, C; graph replay; run
1 | checkpointed 2×forward+backward | 1.018 | n/a (no graph-replay arm)
| 1.008 | 1.010 | 1.008 [1.006, 1.010] | n/a | 0.998 [0.994, 1.002] |
| R200 sm_107a (212 SMs) | S26, (2, 6), 8192, CP2, C; eager; run 2
(reversed arm order) | forward | 0.515 | 0.840 (FLA KCP) | 0.515 | 0.461
| 1.115 [1.106, 1.121] | 1.822 [1.822, 1.822] unpaired | 1.120 [1.111,
1.123] |
| R200 sm_107a (212 SMs) | S26, (2, 6), 8192, CP2, C; eager; run 2
(reversed arm order) | backward (= forward+backward − forward) | 0.763 |
0.736 (FLA KCP) | 0.755 | 0.688 | 1.106 [1.087, 1.135] | 1.070 [1.070,
1.070] (medians) | 1.096 [1.075, 1.121] |
| R200 sm_107a (212 SMs) | S26, (2, 6), 8192, CP2, C; eager; run 2
(reversed arm order) | forward+backward | 1.278 | 1.576 (FLA KCP) |
1.271 | 1.149 | 1.110 [1.098, 1.125] UNSTABLE | 1.376 [1.358, 1.376]
UNSTABLE | 1.102 [1.093, 1.118] UNSTABLE |
| R200 sm_107a (212 SMs) | S26, (2, 6), 8192, CP2, C; eager; run 2
(reversed arm order) | checkpointed 2×forward+backward | 2.140 | 2.557
(FLA KCP) | 2.144 | 1.973 | 1.083 [1.080, 1.089] | 1.296 [1.296, 1.296]
unpaired | 1.085 [1.081, 1.090] |
| R200 sm_107a (212 SMs) | S26, (2, 6), 8192, CP2, C; graph replay; run
2 (reversed arm order) | forward | 0.305 | n/a (no graph-replay arm) |
0.297 | 0.298 | 1.023 [1.020, 1.023] | n/a | 0.996 [0.994, 0.998] |
| R200 sm_107a (212 SMs) | S26, (2, 6), 8192, CP2, C; graph replay; run
2 (reversed arm order) | backward (= forward+backward − forward) | 0.327
| n/a (no graph-replay arm) | 0.326 | 0.327 | 0.999 [0.998, 1.001] | n/a
| 0.996 [0.995, 1.000] |
| R200 sm_107a (212 SMs) | S26, (2, 6), 8192, CP2, C; graph replay; run
2 (reversed arm order) | forward+backward | 0.631 | n/a (no graph-replay
arm) | 0.623 | 0.625 | 1.010 [1.008, 1.011] | n/a | 0.997 [0.995, 0.998]
|
| R200 sm_107a (212 SMs) | S26, (2, 6), 8192, CP2, C; graph replay; run
2 (reversed arm order) | checkpointed 2×forward+backward | 0.990 | n/a
(no graph-replay arm) | 0.980 | 0.985 | 1.008 [1.001, 1.011] | n/a |
0.995 [0.994, 0.998] |

Reading:

- **Eager, small heads:** S26, DET C and DET D are 8-10 % faster than
main's non-deterministic package on forward+backward and checkpointed
steps. Examples: S26 forward+backward 1.102 (classed UNSTABLE), S26
checkpointed 1.085-1.087, DET C forward+backward 1.098-1.101 and DET D
forward+backward 1.086-1.087. Single phases reach 1.149 (DET D
backward). On forward+backward these rows are also faster than
deterministic Cake: S26 1.110, DET C 1.096-1.102, DET D 1.517-1.526.
- **Graph replay:** graph replay runs none of the changed host code. It
is at parity with main's non-deterministic package, at 0.995-1.006 on
every graph cell. The smallest graph cell is S26 checkpointed: 0.998
[0.994, 1.002] in run 1 and 0.995 [0.994, 0.998] in run 2. Vs
deterministic Cake, graph cells are 0.997-1.033.
- **(16, 48) rows:** P1 and P3 are GPU-bound and at parity with main's
non-deterministic package (0.999-1.000). Vs deterministic Cake they are
1.000-1.015.
- **Non-Cake:** vs the strongest non-Cake implementation, the new
package is faster in every eager cell. The smallest ratio is 1.042-1.070
on S26 backward. On forward+backward it is 1.339-1.376 (S26),
3.607-3.616 (DET C), 4.608-4.660 (DET D), 4.057-4.059 (P1) and
4.260-4.261 (P3). There is no non-Cake graph-replay arm.

B200 (sm_100a) and B300/GB300 (sm_103a) rows are pending and will be
added when they are ready; the change is host-side only on every
architecture.

The kernel's other Cake variants, all on main, are the deterministic
single-GPU `flashinfer.experimental.cake_gdn_det_train`, the
non-deterministic single-GPU
`flashinfer.experimental.cake.cake_gdn_train` (#8157) and the
deterministic context-parallel
`flashinfer.experimental.cake_gdn_det_train_kcp`; this PR tunes the
non-deterministic context-parallel package from #8172, the two
context-parallel variants share the entry
`flashinfer.cake_gdn_train_kcp(deterministic=...)`, and the family ships
on sm_100a, sm_103a and sm_107a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* Repeated calls reuse package loading and launch setup, reducing
redundant work.
* Forward and backward operations reuse stream setup for launches on the
same stream, while stream changes remain supported.
* **Reliability**
* Reused launch settings preserve per-call launch records and results
across supported options, precision modes, and merge configurations.
* Stream handling is maintained across nested operations and restored
when scopes exit, including after errors.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [9b0f26b](https://github.com/flashinfer-ai/flashinfer/commit/9b0f26b7ed5f0beed26dcbbc687fa2da04c3b1f4)

- **作者**: eigen
- **时间**: 2026-11-01T16:04:47Z
- **提交信息**: perf(cake_trtllm_mla_blackwell): faster quarter-V BF16 and GB300 152-SM CLC decode programs (#8211)

`cake_trtllm_mla_blackwell` is the Cake MLA decode kernel family for
Blackwell. It supports these variants:

- **Data types:** BF16 or FP8 E4M3 query/KV (the same dtype for both),
with BF16 output.
- **Page sizes:** 32 and 64.
- **Dense MLA head geometries:** four, given as (qk_nope, kv_lora, rope,
heads): (128, 512, 64, 128), (128, 512, 64, 64), (64, 256, 64, 32) and
(512, 512, 64, 128).
- **Top-k sparse geometries:** also supported.

This PR changes two programs in the dense decode family:

- **BF16 value-quarter split decode** on sm_100a and sm_103a.
- **152-SM sm_103a CLC generic program**, which runs on GB300.

Every other program and device unit keeps its #7427 bytes.

The baseline is the previous Cake version of this kernel, which is what
FlashInfer main ships (#7427). On every measured shape, outputs are
bitwise identical to the baseline. No measured shape is slower:

- **B200:** faster on 8 of 10 shapes. The other 2 are within measurement
noise.
- **GB300:** faster on 11 of 22 shapes. The other 11 are within
measurement noise, meaning the ratio is 1.0000 or inside the measurement
band.

Per-call GPU latency on NVIDIA B200 (sm_100a, 148 SMs) and NVIDIA GB300
(sm_103a, 152 SMs) with CUDA 13.4. Each FlashInfer API call is replayed
in a CUDA graph with L2 flushed before each replay. Speedup = baseline /
this PR, shown as median [min, max] over 5 interleaved process groups.
Geometry is (qk_nope, kv_lora, rope, heads).

**Table 1: shapes timed for the value-quarter program, on B200 and
GB300**

| # | q/kv dtype | geometry | batch | q_len | kv_len | page | B200
baseline (us) | B200 this PR (us) | B200 speedup, median [min, max] |
B200 result | GB300 baseline (us) | GB300 this PR (us) | GB300 speedup,
median [min, max] | GB300 result |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | BF16 | (128, 512, 64, 128) | 1 | 8 | 1024 | 32 | 14.336 | 13.920 |
1.0299x [1.0299, 1.0299] | faster | 12.416 | 12.080 | 1.0278x [1.0265,
1.0278] | faster |
| 2 | BF16 | (128, 512, 64, 128) | 4 | 2 | random per request, max 1024
| 32 | 14.112 | 13.824 | 1.0208x [1.0197, 1.0208] | faster | 12.448 |
12.128 | 1.0264x [1.0264, 1.0264] | faster |
| 3 | BF16 | (128, 512, 64, 128) | 4 | 4 | random per request, max 1024
| 32 | 15.200 | 14.944 | 1.0171x [1.0161, 1.0182] | faster | 12.960 |
12.736 | 1.0176x [1.0176, 1.0176] | faster |
| 4 | BF16 | (128, 512, 64, 128) | 16 | 1 | 16 fixed lengths, max 874 |
32 | 14.400 | 14.336 | 1.0045x [1.0045, 1.0045] | faster | 12.800 |
12.528 | 1.0217x [1.0204, 1.0217] | faster |
| 5 | BF16 | (128, 512, 64, 128) | 1 | 1 | 256 | 64 | 7.232 | 7.200 |
1.0045x [1.0044, 1.0066] | faster | 6.720 | 6.688 | 1.0048x [1.0048,
1.0048] | faster |
| 6 | BF16 | (128, 512, 64, 128) | 4 | 1 | 256, 256, 256, 256 | 64 |
7.616 | 7.616 | 1.0000x [1.0000, 1.0000] | within noise | 6.944 | 6.944
| 1.0000x [1.0000, 1.0000] | within noise |
| 7 | BF16 | (512, 512, 64, 128) | 1 | 1 | 128 | 64 | 6.368 | 6.304 |
1.0102x [1.0102, 1.0102] | faster | 6.016 | 6.016 | 1.0000x [1.0000,
1.0000] | within noise |
| 8 | BF16 | (512, 512, 64, 128) | 1 | 1 | 512 | 64 | 9.280 | 9.280 |
1.0000x [0.9983, 1.0000] | within noise | 8.608 | 8.352 | 1.0307x
[1.0307, 1.0307] | faster |
| 9 | BF16 | (512, 512, 64, 128) | 4 | 1 | 128, 128, 128, 128 | 64 |
6.688 | 6.624 | 1.0097x [1.0097, 1.0097] | faster | 6.208 | 6.208 |
1.0000x [1.0000, 1.0000] | within noise |
| 10 | BF16 | (512, 512, 64, 128) | 4 | 1 | 512, 512, 512, 512 | 64 |
9.760 | 9.727 | 1.0033x [1.0033, 1.0034] | faster | 8.864 | 8.640 |
1.0259x [1.0259, 1.0259] | faster |

**Table 2: shapes timed for the 152-SM sm_103a CLC program, GB300 only**

The CLC program change applies only to 152-SM sm_103a parts, so these
shapes were measured on GB300 only. All shapes in this table use BF16,
geometry (128, 512, 64, 128) and page 32.

| # | batch | q_len | kv_len | GB300 baseline (us) | GB300 this PR (us)
| GB300 speedup, median [min, max] | result |
|---|---|---|---|---|---|---|---|
| 11 | 4 | 8 | random per request, max 1024 | 14.464 | 14.464 | 1.0000x
[1.0000, 1.0000] | within noise |
| 12 | 4 | 16 | random per request, max 1024 | 17.024 | 17.024 | 1.0000x
[1.0000, 1.0000] | within noise |
| 13 | 64 | 1 | random per request, max 1024 | 21.504 | 21.504 | 1.0000x
[1.0000, 1.0000] | within noise |
| 14 | 64 | 4 | random per request, max 1024 | 36.096 | 35.216 | 1.0250x
[1.0245, 1.0250] | faster |
| 15 | 64 | 8 | random per request, max 1024 | 59.152 | 58.400 | 1.0132x
[1.0126, 1.0132] | faster |
| 16 | 64 | 16 | random per request, max 1024 | 106.432 | 105.888 |
1.0051x [1.0051, 1.0056] | faster |
| 17 | 64 | 2 | random per request, max 8192 | 110.736 | 110.752 |
1.0000x [0.9999, 1.0000] | within noise |
| 18 | 512 | 16 | random per request, max 1024 | 945.256 | 946.992 |
0.9990x [0.9949, 1.0029] | within noise |
| 19 | 512 | 1 | random per request, max 4096 | 228.272 | 221.632 |
1.0299x [1.0292, 1.0306] | faster |
| 20 | 512 | 2 | random per request, max 4096 | 388.984 | 387.144 |
1.0046x [1.0041, 1.0052] | within noise |
| 21 | 768 | 8 | random per request, max 1024 | 732.160 | 737.000 |
0.9939x [0.9854, 1.0012] | within noise |
| 22 | 1024 | 4 | random per request, max 1024 | 496.896 | 496.432 |
1.0011x [0.9991, 1.0019] | within noise |

The other shapes from the #7427 list are not repeated here because they
run programs whose bytes this PR does not change:

- FP8 E4M3, batch 1, q_len 2, page 32
- FP8 E4M3, batch 1, q_len 16, page 64
- BF16, batch 1, q_len 4, page 32
- BF16, batch 1, q_len 1, page 64

This PR leaves the kernel's other Cake variants unchanged. These are the
BF16 and FP8 generic tail programs, the other specialized BF16 and FP8
programs, and the CLC programs used on sm_100a and on 148-SM sm_103a
parts. The family ships on sm_100a and sm_103a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Improvements**
* Updated MLA processing on supported Blackwell GPUs with revised data
loading, synchronization, and data handling. The changes affect how
these workloads are executed; no change to the available parameters or
launch behavior is indicated. No user-facing features or changes to the
way MLA workloads are invoked are included in this update.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [9d2c316](https://github.com/flashinfer-ai/flashinfer/commit/9d2c3162c553c8a2d5fb63b027e97336bacce2df)

- **作者**: eigen
- **时间**: 2026-11-01T15:34:57Z
- **提交信息**: perf(cake_msa_icp_indexer): sm_107a fused decode list scorer prefetches index-K before the PDL wait (#8210)

The MiniMax-M3 index-context-parallel (ICP) sparse-attention indexer
(`flashinfer.msa_ops` `msa_icp_*`, experimental backend
`cake_msa_icp_indexer`) has two decode chains. The default chain is
score plane + select publish. The fused chain is list scorer + list
publisher (`msa_icp_decode_score_publish`). Since #8177, the plan runs
the fused chain on sm_107a at page size 128 (TP2 and TP4) from 8
requests on.

This PR changes only sm_107a decode. At 64 and 32 local K rows per page
(P128 TP4 and TP2), the fused chain's list scorer now starts loading the
history index-K pages before the PDL wait. The score plane at those rows
has done this since #8177. The list output is still written after the
wait, and outputs are bit-identical. P256 runs the score plane, and its
code is unchanged. Speedup against the previous version in FlashInfer
main:

| World | Page | Cohort | Previous (ms) | New (ms) | Speedup |
|---|---|---|---:|---:|---:|
| TP4 | P128 | steady | 9.409 | 9.357 | 1.006x |
| TP4 | P128 | mixed | 9.831 | 9.778 | 1.005x |
| TP2 | P128 | steady | 14.442 | 14.340 | 1.007x |
| TP2 | P128 | mixed | 14.920 | 14.833 | 1.006x |
| TP4 | P256 | steady | 9.262 | 9.292 | 1.00x (parity) |
| TP4 | P256 | mixed | 9.642 | 9.650 | 1.00x (parity) |

*NVIDIA VR200 (sm_107a), 4 GPUs per node, CUDA 13.4. Workload:
MiniMax-M3 serving, 163840 input tokens, 8192 output tokens, 14
concurrent requests. Steady: the 14 requests decode together. Mixed: the
same, plus one request whose chunked prefill runs in mixed batches.
Values are the median GPU time of a decode step. n = 4 rounds, and each
round runs previous and new back to back on one node. Speedup = previous
/ new. The P256 layout runs the unchanged score plane. TP4 P256 steady
is bimodal per server launch (about 9.24 or 9.29 ms) for both packages,
so the P256 rows are parity within launch noise.*

End-to-end output throughput (tok/s), same runs. Ratio = new / previous.

| World | Page | Steady: previous -> new (ratio) | Mixed: previous ->
new (ratio) |
|---|---|---|---|
| TP4 | P128 | 2042.3 -> 2048.2 (1.002) | 1947.2 -> 1947.5 (1.000) |
| TP2 | P128 | 1486.8 -> 1491.8 (1.004) | 1472.4 -> 1476.9 (1.003) |
| TP4 | P256 | 2051.3 -> 2047.8 (0.999) | 1972.7 -> 1972.5 (1.000) |

The indexer ships the prefill path, the tagged and legacy receive rows,
and the P128/P256 x TP2/TP4 decode layouts on sm_100a (B200), sm_103a
(GB300) and sm_107a (VR200), and this PR changes only the sm_107a fused
decode chain, leaving sm_100a and sm_103a code unchanged.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* On supported compute capability 10.7 configurations, the fused scorer
can begin loading history pages before the preceding kernel completes,
matching the score-plane scorer’s behavior. The preceding kernel must
not write those pages and must either run without PDL or wait for its
predecessor before triggering dependent work.
* **Documentation**
* Clarified which scorer paths and page sizes support early history-page
loading across compute capabilities 10.0, 10.3, and 10.7.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [edb2273](https://github.com/flashinfer-ai/flashinfer/commit/edb2273a16edf04bfed0f8a2389d11a9f75951b4)

- **作者**: eigen
- **时间**: 2026-11-01T15:16:47Z
- **提交信息**: perf(cake_tinygemm2_wgmma): sm_90a wgmma programs for tinygemm_bf16, bit-identical to csrc/tinygemm2.cu (#8201)

On SM90, tinygemm_bf16 dispatches the shapes inside measured H100 windows to
generated wgmma programs (flashinfer.jit.cake_tinygemm2_wgmma: seven tiles,
with and without bias and PDL, 68 programs) whose outputs equal the reference
kernel's bit for bit; every other shape keeps csrc/tinygemm2.cu. Set
FLASHINFER_DISABLE_TINYGEMM2_WGMMA=1 to keep the reference everywhere.

### [44c7973](https://github.com/flashinfer-ai/flashinfer/commit/44c7973afbf45302ba9a393c9db74fb4abc63be6)

- **作者**: eigen
- **时间**: 2026-11-01T15:00:10Z
- **提交信息**: cake_gdn_cp: dedicated sm_107a ring state-fixup program (about 1.05x) (#8206)

The context-parallel GDN prefill state-fixup stage applies each CP
chunk's transfer to the incoming recurrent state. The host uses one
program for every input, selected under the key `state_fixup_simt_row4`.
Until now, sm_100a, sm_103a and sm_107a all used
`cake_gdn_cp_dc9fd29403170907f3a6`. This PR adds
`cake_gdn_cp_24af0c6f4359b2acf3c1` for SM 10.7 (R200, sm_107a) and sends
sm_107a to it. The new program launches 32 CTAs per sequence and head,
with four state rows per CTA, and prefetches the transfer through a
four-slot register ring. The speedups below compare it with the previous
Cake version of this kernel on sm_107a, which is `dc9fd294`.

NVIDIA VR200 (R200), sm_107a, 212 SMs, driver 620.62, SM clock 2424 MHz
max. CUDA 13.4 toolchain (nvcc 13.4), CUDA runtime 13.0 (torch
2.14.1+cu130). Times are the median of paired cold-L2 CUPTI GPU time,
run in interleaved ABBA groups. Speedup = previous latency / new
latency, so a value above 1 means the new program is faster. Every row
is output-checked against a reference.

| shape | s17 previous µs | s17 new µs | s17 speedup | s29 previous µs |
s29 new µs | s29 speedup |
|---|---:|---:|---:|---:|---:|---:|
| T=16384 H=8 chunk_len=1024 seq_lens=[16384] | 34.96 | 33.76 | 1.0355 |
34.91 | 33.73 | 1.0351 |
| T=65536 H=16 chunk_len=5120 seq_lens=[65536] | 56.48 | 54.08 | 1.0444
| 56.48 | 54.18 | 1.0425 |
| T=32768 H=16 chunk_len=2560 seq_lens=[32768] | 56.26 | 53.94 | 1.0430
| 56.31 | 54.00 | 1.0427 |
| T=8192 H=16 chunk_len=1024 seq_lens=[8192] | 35.86 | 33.98 | 1.0551 |
35.82 | 34.06 | 1.0517 |
| T=4096 H=16 chunk_len=512 seq_lens=[4096] | 35.68 | 34.18 | 1.0440 |
35.66 | 34.14 | 1.0445 |
| T=8192 H=16 chunk_len=1024 seq_lens=[6144, 2048] | 28.51 | 27.09 |
1.0526 | 28.54 | 27.14 | 1.0518 |
| T=8192 H=16 chunk_len=1024 seq_lens=[4096, 4096] | 29.46 | 27.81 |
1.0593 | 29.49 | 27.74 | 1.0629 |
| T=8192 H=16 chunk_len=1024 seq_lens=[2048, 6144] | 32.98 | 31.31 |
1.0531 | 32.99 | 31.28 | 1.0547 |
| T=8192 H=16 chunk_len=1024 seq_lens=[1024, 7168] | 34.75 | 33.25 |
1.0453 | 34.70 | 33.22 | 1.0448 |
| T=65536 H=8 chunk_len=2560 seq_lens=[65536] | 55.68 | 53.79 | 1.0351 |
55.71 | 53.76 | 1.0363 |
| T=32768 H=8 chunk_len=1536 seq_lens=[32768] | 47.46 | 45.79 | 1.0363 |
47.43 | 45.76 | 1.0364 |
| T=8192 H=8 chunk_len=512 seq_lens=[8192] | 34.99 | 33.82 | 1.0345 |
34.94 | 33.81 | 1.0336 |
| T=4096 H=8 chunk_len=512 seq_lens=[4096] | 18.72 | 18.10 | 1.0344 |
18.67 | 18.05 | 1.0345 |
| T=8192 H=8 chunk_len=512 seq_lens=[6144, 2048] | 27.73 | 26.43 |
1.0490 | 27.78 | 26.46 | 1.0495 |
| T=8192 H=8 chunk_len=512 seq_lens=[4096, 4096] | 35.81 | 34.34 |
1.0429 | 35.84 | 34.37 | 1.0429 |
| T=8192 H=8 chunk_len=512 seq_lens=[2048, 6144] | 35.87 | 34.16 |
1.0501 | 35.89 | 34.29 | 1.0467 |
| T=8192 H=8 chunk_len=512 seq_lens=[1024, 7168] | 35.82 | 34.37 |
1.0424 | 35.66 | 34.24 | 1.0416 |
| T=16384 H=16 chunk_len=1536 seq_lens=[16384] | 48.03 | 46.05 | 1.0431
| 48.03 | 45.98 | 1.0445 |
| T=65536 H=32 chunk_len=11264 seq_lens=[65536] | 42.03 | 39.94 | 1.0525
| 41.99 | 39.95 | 1.0509 |
| T=32768 H=32 chunk_len=5120 seq_lens=[32768] | 48.45 | 46.05 | 1.0521
| 48.38 | 46.08 | 1.0500 |
| T=16384 H=32 chunk_len=2560 seq_lens=[16384] | 48.42 | 46.03 | 1.0518
| 48.32 | 46.08 | 1.0486 |
| T=8192 H=32 chunk_len=1536 seq_lens=[8192] | 42.18 | 40.16 | 1.0502 |
42.18 | 40.16 | 1.0502 |
| T=4096 H=32 chunk_len=1024 seq_lens=[4096] | 29.41 | 27.76 | 1.0593 |
29.38 | 27.78 | 1.0576 |
| T=65536 H=48 chunk_len=16384 seq_lens=[65536] | 39.22 | 36.94 | 1.0615
| 39.17 | 36.91 | 1.0611 |
| T=32768 H=48 chunk_len=8192 seq_lens=[32768] | 39.34 | 37.03 | 1.0626
| 39.17 | 36.99 | 1.0588 |
| T=16384 H=48 chunk_len=4096 seq_lens=[16384] | 39.17 | 36.96 | 1.0597
| 39.22 | 36.93 | 1.0620 |
| T=8192 H=48 chunk_len=2048 seq_lens=[8192] | 39.23 | 36.91 | 1.0629 |
39.23 | 36.99 | 1.0605 |
| T=4096 H=48 chunk_len=1024 seq_lens=[4096] | 39.23 | 36.93 | 1.0624 |
39.18 | 36.96 | 1.0602 |
| T=385 H=2 chunk_len=128 seq_lens=[128, 128, 129] | 5.79 | 5.41 |
1.0710 | 5.82 | 5.38 | 1.0833 |

Geomean speedup over 29 shapes: seed 17 1.0498, seed 29 1.0496 (min
1.0336, max 1.0833).

This kernel family ships Cake variants for sm_100a, sm_103a and sm_107a.
sm_100a and sm_103a keep `dc9fd294`, and only sm_107a moves to
`24af0c6f`.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added CUDA support for state fixup on `sm_107a` GPUs, enabling state
updates across chunks and sequences.
* Sequences without chunks now retain their initial state in the output.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [1da0c4e](https://github.com/flashinfer-ai/flashinfer/commit/1da0c4e558d36fe0023fd5f729b87e6180465563)

- **作者**: eigen
- **时间**: 2026-11-01T14:58:59Z
- **提交信息**: perf(cake_kimi_k3_attn_res): route M 4096 to 8192 with K 6 to 8 on B200 and B300 to token-queue persistent programs (#8207)

This PR changes routes of the Cake AttnRes operator,
`flashinfer.experimental.cake_kimi_k3_attn_res`, which is exposed as
`flashinfer.kimi_k3_attn_res.prepare_kimi_k3_attn_res` and
`kimi_k3_attn_res`. One launch does residual add, an optional snapshot
write, K+1 candidate scoring, softmax, mix and output RMSNorm. It takes
BF16 inputs with hidden size 7168 and K in [0, 8]. It has one data type,
one layout and two fused forms: dense and snapshot write. This PR
changes routes of dense shapes only: 8 shapes on B200 and 9 on B300, at
both PDL modes.

- **Token-queue persistent programs (B200 and B300):** M 4096, 6144 and
8192 with K 6, 7 and 8 move to new token-queue builds of the persistent
programs they already ran: `persistent:k6_nc4_d2_f110000000000000_clc`,
`persistent:k7_nc4_d2_f110000000000000_clc` and
`persistent:k8_nc5_d2_f110000000000000_clc`. The one exception is M 8192
K 6 on B200, which does not change. A token-queue build launches one CTA
per token (grid M) and uses cluster launch control. Each running CTA
processes its own token and then the tokens of the CTAs it cancels, so
tokens are spread over the SMs dynamically instead of by a static stride
over 148 CTAs. The per-token work is the same as in the static build.
- **K 7 (B300):** M 4096 K 7 and M 6144 K 7 move from
`persistent:k7_nc4_d2_f111000000000000_fm` to the K 7 token-queue build.
- The backend adds the `_clc` key suffix, which plans grid M with grid
policy `clc_token_queue`. The registered-variant fallback never resolves
to a `_clc` program.
- GB300 (sm_103a, 152 SMs) routes do not change.

The program set goes from 184 programs (216 libraries: 101 sm_100a, 115
sm_103a) to 190 programs (222 libraries: 104 sm_100a, 118 sm_103a). Six
programs are added: the three token-queue builds for each architecture.
No program is removed, and the other 216 program/library pairs have SASS
identical to the previous version.

The baseline is the previous Cake version of this operator on current
main (PR #8171). All changed shapes are faster at both PDL modes: 2.1 %
to 3.2 % on B200 (ratios 1.0209 to 1.0319) and 2.5 % to 3.8 % on B300
(ratios 1.0248 to 1.0381). For shapes not in the tables below, see the
timings in PRs #6980, #7014, #7338, #7374, #7411, #7453, #7540, #7737,
#8120, #8143, #8155 and #8171.

NVIDIA B200 (sm_100a, 148 SMs), driver 580.82.07, CUDA 13.4, torch
2.14.1+cu130.

| Shape | Previous µs (PDL off) | New µs (PDL off) | Ratio | Previous µs
(PDL on) | New µs (PDL on) | Ratio |
|---|---|---|---|---|---|---|
| M 4096, K 6 (dense) | 94.257 | 92.320 | 1.0209 | 94.272 | 92.320 |
1.0213 |
| M 4096, K 7 (dense) | 105.440 | 102.592 | 1.0278 | 105.472 | 102.592 |
1.0281 |
| M 4096, K 8 (dense) | 114.528 | 111.488 | 1.0270 | 114.560 | 111.520 |
1.0273 |
| M 6144, K 6 (dense) | 137.632 | 134.400 | 1.0242 | 137.600 | 134.400 |
1.0240 |
| M 6144, K 7 (dense) | 152.160 | 147.472 | 1.0318 | 152.129 | 147.456 |
1.0319 |
| M 6144, K 8 (dense) | 164.095 | 160.032 | 1.0252 | 164.160 | 160.064 |
1.0257 |
| M 8192, K 7 (dense) | 197.920 | 192.032 | 1.0307 | 197.873 | 192.033 |
1.0303 |
| M 8192, K 8 (dense) | 213.632 | 208.256 | 1.0257 | 213.664 | 208.224 |
1.0260 |

NVIDIA B300 SXM6 AC (sm_103a, 148 SMs), driver 580.126.09, CUDA 13.4,
torch 2.14.1+cu130.

| Shape | Previous µs (PDL off) | New µs (PDL off) | Ratio | Previous µs
(PDL on) | New µs (PDL on) | Ratio |
|---|---|---|---|---|---|---|
| M 4096, K 6 (dense) | 97.121 | 94.176 | 1.0312 | 97.089 | 94.145 |
1.0313 |
| M 4096, K 7 (dense) | 106.945 | 104.353 | 1.0250 | 106.913 | 104.321 |
1.0248 |
| M 4096, K 8 (dense) | 117.121 | 112.993 | 1.0363 | 117.073 | 112.993 |
1.0360 |
| M 6144, K 6 (dense) | 141.073 | 135.970 | 1.0375 | 141.121 | 135.938 |
1.0381 |
| M 6144, K 7 (dense) | 153.954 | 149.281 | 1.0315 | 153.953 | 149.281 |
1.0311 |
| M 6144, K 8 (dense) | 167.553 | 161.601 | 1.0367 | 167.554 | 161.633 |
1.0366 |
| M 8192, K 6 (dense) | 183.666 | 177.345 | 1.0358 | 183.730 | 177.298 |
1.0364 |
| M 8192, K 7 (dense) | 202.178 | 195.298 | 1.0351 | 202.114 | 195.298 |
1.0351 |
| M 8192, K 8 (dense) | 218.322 | 210.977 | 1.0350 | 218.274 | 210.946 |
1.0347 |

Cake ships no other data types or layouts for this operator, since the
dense and snapshot-write forms are the whole family, and 190 programs
(222 libraries: 104 sm_100a, 118 sm_103a) cover B200 (sm_100a, 148 SMs),
B300 (sm_103a, 148 SMs) and GB300 (sm_103a, 152 SMs).

Co-authored-by: Avery Huang <averyh@nvidia.com>

### [db608d3](https://github.com/flashinfer-ai/flashinfer/commit/db608d3e061c16432a8c1a3e8b3ab4c8e061a323)

- **作者**: eigen
- **时间**: 2026-11-01T14:55:54Z
- **提交信息**: refactor(cake_nvfp4_svdquant): label registry records by kernel origin (#8204)

Replaces each record's `"module"` key, which held an internal generator
module path, with `"origin"`, the kernel's short name, in
`flashinfer/cake_nvfp4_svdquant_gemm_backend/cake_jit.py`.

- All 47 records now use one of nine short names, such as
`"2cta_persistent"`, `"tactic14_m64_bias"` or `"swapab_splitk"`. The
docstring now describes the new field and says that the program name
`cake_nvfp4_svdquant_gemm_<20 hex>` is a stable identifier fixed when
the program is first exported.
- Nothing reads this field at run time because the loader loads by
record name. Record names, build keywords, launch records, argument
plans, the route table, host plans, `build.json` and all CUDA sources
and bindings are unchanged.
- No compiled source changes, so performance should not change.
Supported targets are still sm_100a and sm_103a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Improvements**
* Program records now identify the originating kernel rather than its
module.
* Program-name documentation now describes identifiers as stable after
export and based on the kernel and build options.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [150eef8](https://github.com/flashinfer-ai/flashinfer/commit/150eef8ea280e99b9039babd3b0db9c1d120f3d4)

- **作者**: eigen
- **时间**: 2026-11-01T14:46:40Z
- **提交信息**: perf(cake_causal_conv1d_det_train): row-group backward program for 264 <= C < 512 on SM100 / SM103 (#8205)

`flashinfer.cake_causal_conv1d_det_train` is the deterministic packed
depthwise causal conv1d + SiLU for training. It has a forward pass and
these backward routes: `bwd`, `bwd_dt`, `bwd_bias`, `bwd_bias_bf16`,
`bwd_fp32g` and `bwd_bias_fp32g`. Each route is compiled separately for
each shape band and target arch. This PR adds one new backward program
for the plain `bwd` route on B200 (sm_100a) and GB300 (sm_103a). It
covers shapes with one channel tile and 264 <= C < 512 (C 264..504).
When the channel tile is not a multiple of 32 vectors, the program
copies whole rows in groups. It is selected only for that C class on the
plain `bwd` route. Every other shape and route runs the unchanged
program. dx and dw are bitwise identical to the previous program. The
baseline is the Cake package currently shipped on FlashInfer main.

Latency is the timed span in microseconds. Each value is the mean of two
copies of the same build, and ± is half the difference between those
copies. Speedup is the median paired baseline / new ratio. `backward`
times the backward alone, and `forward + backward` times both passes.

### B200 (sm_100a), CUDA 13.4

| S | C | timed | baseline us | new us | speedup (median paired ratio) |
|---|---|---|---|---|---|
| 250340 | 264 | forward + backward | 187.00 ± 0.02 | 169.89 ± 0.03 |
1.0998x |
| 250340 | 264 | backward | 127.63 ± 0.02 | 110.87 ± 0.00 | 1.1505x |
| 250340 | 336 | forward + backward | 189.61 ± 0.02 | 174.14 ± 0.07 |
1.0881x |
| 250340 | 336 | backward | 129.36 ± 0.02 | 113.10 ± 0.02 | 1.1422x |
| 250340 | 384 | forward + backward | 241.12 ± 0.02 | 229.67 ± 0.12 |
1.0487x |
| 250340 | 384 | backward | 166.13 ± 0.04 | 155.09 ± 0.02 | 1.0704x |
| 250340 | 448 | forward + backward | 268.61 ± 0.07 | 242.45 ± 0.04 |
1.1072x |
| 250340 | 448 | backward | 184.00 ± 0.00 | 158.11 ± 0.00 | 1.1630x |
| 250340 | 480 | forward + backward | 269.72 ± 0.03 | 243.91 ± 0.08 |
1.1064x |
| 250340 | 480 | backward | 185.04 ± 0.01 | 159.22 ± 0.03 | 1.1612x |
| 250340 | 504 | forward + backward | 282.37 ± 0.06 | 245.77 ± 0.14 |
1.1480x |
| 250340 | 504 | backward | 200.51 ± 0.10 | 160.05 ± 0.01 | 1.2518x |
| 262144 | 384 | forward + backward | 252.07 ± 0.02 | 239.38 ± 0.02 |
1.0538x |
| 262144 | 384 | backward | 174.21 ± 0.01 | 162.03 ± 0.03 | 1.0746x |
| 262144 | 480 | forward + backward | 279.24 ± 0.06 | 254.32 ± 0.04 |
1.0970x |
| 262144 | 480 | backward | 191.30 ± 0.02 | 165.65 ± 0.04 | 1.1540x |

### GB300 (sm_103a), CUDA 13.4

| S | C | timed | baseline us | new us | speedup (median paired ratio) |
|---|---|---|---|---|---|
| 250340 | 264 | forward + backward | 188.48 ± 0.16 | 173.39 ± 0.02 |
1.0862x |
| 250340 | 264 | backward | 115.94 ± 0.00 | 100.51 ± 0.01 | 1.1534x |
| 250340 | 336 | forward + backward | 189.34 ± 0.13 | 176.59 ± 0.20 |
1.0726x |
| 250340 | 336 | backward | 117.07 ± 0.02 | 102.89 ± 0.04 | 1.1378x |
| 250340 | 384 | forward + backward | 224.76 ± 0.04 | 211.46 ± 0.23 |
1.0615x |
| 250340 | 384 | backward | 153.60 ± 0.00 | 139.86 ± 0.00 | 1.0978x |
| 250340 | 448 | forward + backward | 239.48 ± 0.15 | 217.03 ± 0.02 |
1.1036x |
| 250340 | 448 | backward | 164.77 ± 0.00 | 142.85 ± 0.00 | 1.1536x |
| 250340 | 480 | forward + backward | 243.10 ± 0.07 | 220.85 ± 0.00 |
1.0997x |
| 250340 | 480 | backward | 165.57 ± 0.00 | 143.81 ± 0.03 | 1.1515x |
| 250340 | 504 | forward + backward | 251.54 ± 0.05 | 225.05 ± 0.01 |
1.1178x |
| 250340 | 504 | backward | 173.55 ± 0.00 | 144.41 ± 0.00 | 1.2011x |
| 262144 | 384 | forward + backward | 229.70 ± 0.08 | 216.27 ± 0.15 |
1.0615x |
| 262144 | 384 | backward | 159.28 ± 0.01 | 145.57 ± 0.00 | 1.0941x |
| 262144 | 480 | forward + backward | 252.16 ± 0.07 | 229.35 ± 0.01 |
1.0995x |
| 262144 | 480 | backward | 172.24 ± 0.02 | 149.66 ± 0.00 | 1.1509x |

The other measured shapes run the same program on both sides and measure
as ties in both timing modes. They are C 64, 128, 192 and 256 at S
250340, C 128 and 256 at S 262144, and the C 512 control at S 250340.
Their speedups are 0.9928x to 1.0004x on B200 and 0.9945x to 1.0017x on
GB300.

The kernel's other Cake variants are the context-parallel KCP package
(`flashinfer.cake_causal_conv1d_det_train_kcp`) and the opt-in
`bwd_grid_mult` backward split. The family ships on sm_100a, sm_103a and
sm_107a, and this PR leaves sm_107a (R200) unchanged.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added deterministic causal convolution training support for backward
passes with 264–511 channels on select newer NVIDIA GPU architectures.
* The new channel-range option produces results that match the existing
fallback bitwise, while retaining support for the existing channel
ranges and CUDA version.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [fe36017](https://github.com/flashinfer-ai/flashinfer/commit/fe36017904b4ca558e97464bc16b287bd68de6ad)

- **作者**: eigen
- **时间**: 2026-11-01T14:21:56Z
- **提交信息**: perf(cake_selective_state_update): the z-gated one-token ring at its measured batch on sm_103a (#8203)

`flashinfer.mamba.selective_state_update(..., backend="cake")` runs the
Mamba2 selective-state-update decode step under both the SGLang and the
canonical calling conventions. The kernel's variants are defined by
these dimensions: SSM state dtype (BF16 or FP32), input convention
(canonical FP32 dt / D / dt_bias with an int64 state-slot index, or raw
SGLang BF16 dt / D / dt_bias with an int32 slot index and padded
fused-projection rows), head dim 64 or 128 (state dim 128), single-token
decode or multi-token (speculative) decode with an intermediate-state
cache or a destination-slot table, and an optional fused z gate and dt
softplus. The baseline is the previous Cake version, which is FlashInfer
main after #7724. This PR makes one routing change, and it applies only
on sm_103a (GB300, 152 SMs). It covers single-token calls with the fused
z gate, 64 heads in 8 groups, head dim 128, state dim 128, BF16 state
and canonical FP32 dt/D with an int64 slot index, at batch 64. These
calls now run the z-gated one-token ring program that #7724 added for
sm_100a. On sm_103a, main runs these calls on its z-gated balanced lean
two-head program, but it already runs the one-token ring for the same
calls without z.

The ring program's source gains an sm_103a build. Like main's other
sm_103a rings, this build addresses the state tiles from the head's ring
base. The program keeps its name. No other program changes on either
GPU, and no program is renamed. On B200 (sm_100a), no route changes, and
the program's sm_100a machine code is identical to main's. Outputs and
states are bitwise identical to main's on all 122 shapes on each GPU.

On GB300, 2 of the 122 shapes change program, and both run faster than
main:
- sample_stp_z: 1.027x (main 38.608 us, this PR 37.600 us)
- sample_stp_z_softplus: 1.030x (main 38.728 us, this PR 37.608 us)

The other 120 shapes keep main's program, and their speedups (0.994x to
1.008x) are run-to-run variation. A small table shows the two z-gated
shapes on 12 GB300 GPUs across three nodes, with two sessions per GPU.
This PR is faster on every GPU in every session: 1.016x to 1.035x on
sample_stp_z and 1.032x to 1.051x on sample_stp_z_softplus. On B200, all
122 shapes keep main's program, and their speedups (0.994x to 1.004x)
are run-to-run variation.

*NVIDIA GB300 (sm_103a, 152 SMs), driver 580.159.03, CUDA 13.4; PyTorch
2.14.1+cu130; programs compiled with nvcc 13.4. Timer: CUPTI kernel time
with a cold L2; times are medians over 2 runs x 9 interleaved rounds
(us); speedup = main / this PR; the program column says whether this PR
routes the shape to a different program (`new`) or keeps main's
(`same`).*

| case | batch | tokens | heads | groups | head dim | state dim | state
| inputs | options | main (us) | this PR (us) | speedup | program |
|---|---:|---:|---:|---:|---:|---:|---|---|---|---:|---:|---:|---|
| sample_stp_bf16 | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 37.280 | 37.280 | 1.000x | same |
| sample_stp_state_fp32 | 64 | 1 | 64 | 8 | 128 | 128 | FP32 | FP32
dt/D, int64 index | - | 73.760 | 73.736 | 1.000x | same |
| sample_stp_z | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D, int64
index | z gate | 38.608 | 37.600 | 1.027x | new |
| sample_stp_softplus | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | softplus | 37.280 | 37.272 | 1.000x | same |
| sample_stp_z_softplus | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32
dt/D, int64 index | z gate, softplus | 38.728 | 37.608 | 1.030x | new |
| sample_stp_ratio1 | 32 | 1 | 16 | 16 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 7.544 | 7.544 | 1.000x | same |
| sample_stp_ratio16 | 32 | 1 | 128 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 37.240 | 37.224 | 1.000x | same |
| sample_stp_b256 | 256 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 151.008 | 150.992 | 1.000x | same |
| sample_stp_b128 | 128 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 75.504 | 75.496 | 1.000x | same |
| sample_mtp1 | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D, int64
index | - | 36.520 | 36.536 | 1.000x | same |
| sample_mtp2 | 64 | 2 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D, int64
index | - | 38.480 | 38.504 | 0.999x | same |
| sweep_bfloat16_vertical_b1 | 1 | 6 | 64 | 8 | 64 | 128 | BF16 | FP32
dt/D, int64 index | softplus, state cache, no state write,
algorithm=vertical | 3.584 | 3.584 | 1.000x | same |
| sweep_bfloat16_horizontal_b1024 | 1024 | 6 | 64 | 8 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus, state cache, no state write,
algorithm=horizontal | 1100.992 | 1100.936 | 1.000x | same |
| dynamic_dump_b1_t1_prev0 | 1 | 1 | 16 | 1 | 64 | 128 | FP32 | FP32
dt/D, int64 index | softplus, dst slots, algorithm=simple | 2.736 |
2.744 | 0.997x | same |
| dynamic_dump_b1_t2_prev1 | 1 | 2 | 16 | 1 | 64 | 128 | FP32 | FP32
dt/D, int64 index | softplus, dst slots, algorithm=simple | 2.864 |
2.880 | 0.994x | same |
| dynamic_dump_b1_t4_prev2 | 1 | 4 | 16 | 1 | 64 | 128 | FP32 | FP32
dt/D, int64 index | softplus, dst slots, algorithm=simple | 3.072 |
3.088 | 0.995x | same |
| dynamic_dump_b1_t8_prev4 | 1 | 8 | 16 | 1 | 64 | 128 | FP32 | FP32
dt/D, int64 index | softplus, dst slots, algorithm=simple | 3.440 |
3.440 | 1.000x | same |
| dynamic_dump_b1_t8_prev8 | 1 | 8 | 16 | 1 | 64 | 128 | FP32 | FP32
dt/D, int64 index | softplus, dst slots, algorithm=simple | 3.440 |
3.456 | 0.995x | same |
| granite_ngram_t6_c4_legacy_adapted_graph_b1 | 1 | 6 | 64 | 1 | 64 |
128 | BF16 | FP32 dt/D, int64 index | softplus, state cache, no state
write, algorithm=vertical | 3.592 | 3.608 | 0.996x | same |
| granite_ngram_t6_c4_legacy_adapted_graph_b2 | 2 | 6 | 64 | 1 | 64 |
128 | BF16 | FP32 dt/D, int64 index | softplus, state cache, no state
write, algorithm=vertical | 4.640 | 4.656 | 0.997x | same |
| granite_ngram_t6_c4_legacy_adapted_graph_b3 | 3 | 6 | 64 | 1 | 64 |
128 | BF16 | FP32 dt/D, int64 index | softplus, state cache, no state
write, algorithm=vertical | 5.584 | 5.584 | 1.000x | same |
| granite_ngram_t6_c4_legacy_adapted_graph_b4 | 4 | 6 | 64 | 1 | 64 |
128 | BF16 | FP32 dt/D, int64 index | softplus, state cache, no state
write, algorithm=vertical | 6.352 | 6.352 | 1.000x | same |
| granite_ngram_t6_c4_sglang_raw_b1 | 1 | 6 | 64 | 1 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus, state cache, no state write | 3.824 |
3.808 | 1.004x | same |
| granite_ngram_t6_c4_sglang_raw_b2 | 2 | 6 | 64 | 1 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus, state cache, no state write | 4.784 |
4.784 | 1.000x | same |
| granite_ngram_t6_c4_sglang_raw_b3 | 3 | 6 | 64 | 1 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus, state cache, no state write | 5.776 |
5.776 | 1.000x | same |
| granite_ngram_t6_c4_sglang_raw_b4 | 4 | 6 | 64 | 1 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus, state cache, no state write | 6.608 |
6.608 | 1.000x | same |
| fitest_stp_ratio1 | 32 | 1 | 16 | 16 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 7.544 | 7.528 | 1.002x | same |
| fitest_stp_ratio8 | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 37.256 | 37.264 | 1.000x | same |
| fitest_stp_ratio8_sat | 128 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32
dt/D, int64 index | - | 75.504 | 75.544 | 0.999x | same |
| fitest_stp_ratio16 | 32 | 1 | 128 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 37.152 | 37.152 | 1.000x | same |
| fitest_stp_persistent | 257 | 1 | 128 | 8 | 128 | 128 | BF16 | FP32
dt/D, int64 index | - | 303.568 | 303.528 | 1.000x | same |
| fitest_stp_fp32 | 64 | 1 | 64 | 8 | 128 | 128 | FP32 | FP32 dt/D,
int64 index | - | 73.824 | 73.760 | 1.001x | same |
| fitest_mtp_short1 | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 36.504 | 36.528 | 0.999x | same |
| fitest_mtp_short2 | 64 | 2 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 38.504 | 38.471 | 1.001x | same |
| fitest_mtp_cache | 1 | 6 | 64 | 8 | 64 | 128 | BF16 | FP32 dt/D, int64
index | softplus, state cache, no state write, algorithm=vertical |
3.608 | 3.600 | 1.002x | same |
| fitest_mtp_horizontal | 32 | 6 | 64 | 8 | 64 | 128 | BF16 | FP32 dt/D,
int64 index | softplus, state cache, no state write,
algorithm=horizontal | 36.608 | 36.616 | 1.000x | same |
| fitest_dynamic0 | 1 | 1 | 16 | 1 | 64 | 128 | FP32 | FP32 dt/D, int64
index | softplus, dst slots, algorithm=simple | 2.728 | 2.736 | 0.997x |
same |
| fitest_dynamic0_b8 | 8 | 2 | 16 | 1 | 64 | 128 | FP32 | FP32 dt/D,
int64 index | softplus, dst slots, algorithm=simple | 3.856 | 3.824 |
1.008x | same |
| fitest_dynamic1 | 1 | 4 | 16 | 1 | 64 | 128 | FP32 | FP32 dt/D, int64
index | softplus, dst slots, algorithm=simple | 3.072 | 3.072 | 1.000x |
same |
| fitest_dynamic3 | 1 | 8 | 16 | 1 | 64 | 128 | FP32 | FP32 dt/D, int64
index | softplus, dst slots, algorithm=simple | 3.440 | 3.440 | 1.000x |
same |
| fitest_dynamic7 | 1 | 8 | 16 | 1 | 64 | 128 | FP32 | FP32 dt/D, int64
index | softplus, dst slots, algorithm=simple | 3.464 | 3.456 | 1.002x |
same |
| sweep_bfloat16_auto_b1 | 1 | 6 | 64 | 8 | 64 | 128 | BF16 | FP32 dt/D,
int64 index | softplus, state cache, no state write | 3.600 | 3.600 |
1.000x | same |
| dynamic_dump_b8_t2_prev1 | 8 | 2 | 16 | 1 | 64 | 128 | FP32 | FP32
dt/D, int64 index | softplus, dst slots, algorithm=simple | 3.856 |
3.840 | 1.004x | same |
| nemotron_h_tp1_hd64_sglang_raw_b1 | 1 | 1 | 128 | 8 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 3.008 | 3.008 | 1.000x | same |
| nemotron_h_tp1_hd64_canonical_b1 | 1 | 1 | 128 | 8 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 3.136 | 3.128 | 1.003x | same |
| nemotron_h_tp1_hd64_sglang_raw_b2 | 2 | 1 | 128 | 8 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 3.512 | 3.520 | 0.998x | same |
| nemotron_h_tp1_hd64_canonical_b2 | 2 | 1 | 128 | 8 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 3.520 | 3.520 | 1.000x | same |
| nemotron_h_tp1_hd64_sglang_raw_b4 | 4 | 1 | 128 | 8 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 4.768 | 4.760 | 1.002x | same |
| nemotron_h_tp1_hd64_canonical_b4 | 4 | 1 | 128 | 8 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 4.800 | 4.800 | 1.000x | same |
| nemotron_h_tp1_hd64_sglang_raw_b8 | 8 | 1 | 128 | 8 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 6.640 | 6.640 | 1.000x | same |
| nemotron_h_tp1_hd64_canonical_b8 | 8 | 1 | 128 | 8 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 6.640 | 6.624 | 1.002x | same |
| nemotron_h_tp1_hd64_sglang_raw_b16 | 16 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 9.944 | 9.952 | 0.999x | same
|
| nemotron_h_tp1_hd64_canonical_b16 | 16 | 1 | 128 | 8 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 10.064 | 10.080 | 0.998x | same |
| nemotron_h_tp1_hd64_sglang_raw_b32 | 32 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 18.384 | 18.384 | 1.000x |
same |
| nemotron_h_tp1_hd64_canonical_b32 | 32 | 1 | 128 | 8 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 18.056 | 18.064 | 1.000x | same |
| nemotron_h_tp1_hd64_sglang_raw_b64 | 64 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 37.376 | 37.392 | 1.000x |
same |
| nemotron_h_tp1_hd64_canonical_b64 | 64 | 1 | 128 | 8 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 37.408 | 37.400 | 1.000x | same |
| nemotron_h_tp1_hd64_sglang_raw_b128 | 128 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 75.464 | 75.464 | 1.000x |
same |
| nemotron_h_tp1_hd64_canonical_b128 | 128 | 1 | 128 | 8 | 64 | 128 |
BF16 | FP32 dt/D, int64 index | softplus | 75.696 | 75.688 | 1.000x |
same |
| nemotron_h_tp1_hd64_sglang_raw_b256 | 256 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 150.928 | 150.944 | 1.000x |
same |
| nemotron_h_tp1_hd64_canonical_b256 | 256 | 1 | 128 | 8 | 64 | 128 |
BF16 | FP32 dt/D, int64 index | softplus | 150.768 | 150.768 | 1.000x |
same |
| nemotron_h_tp1_hd64_sglang_raw_b6 | 6 | 1 | 128 | 8 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 5.824 | 5.824 | 1.000x | same |
| nemotron_h_tp1_hd64_sglang_raw_b12 | 12 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 8.400 | 8.408 | 0.999x | same
|
| nemotron_h_tp1_hd64_sglang_raw_b20 | 20 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 12.176 | 12.152 | 1.002x |
same |
| nemotron_h_tp1_hd64_sglang_raw_b24 | 24 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 14.256 | 14.232 | 1.002x |
same |
| nemotron_h_tp1_hd64_sglang_raw_b48 | 48 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 27.600 | 27.616 | 0.999x |
same |
| nemotron_h_tp1_hd64_fp32_sglang_raw_b1 | 1 | 1 | 128 | 8 | 64 | 128 |
FP32 | BF16 dt/D, int32 index | softplus | 3.536 | 3.528 | 1.002x | same
|
| nemotron_h_tp1_hd64_fp32_canonical_b1 | 1 | 1 | 128 | 8 | 64 | 128 |
FP32 | FP32 dt/D, int64 index | softplus | 3.328 | 3.312 | 1.005x | same
|
| nemotron_h_tp1_hd64_fp32_sglang_raw_b8 | 8 | 1 | 128 | 8 | 64 | 128 |
FP32 | BF16 dt/D, int32 index | softplus | 10.304 | 10.304 | 1.000x |
same |
| nemotron_h_tp1_hd64_fp32_canonical_b8 | 8 | 1 | 128 | 8 | 64 | 128 |
FP32 | FP32 dt/D, int64 index | softplus | 10.304 | 10.304 | 1.000x |
same |
| nemotron_h_tp1_hd64_fp32_sglang_raw_b64 | 64 | 1 | 128 | 8 | 64 | 128
| FP32 | BF16 dt/D, int32 index | softplus | 73.232 | 73.248 | 1.000x |
same |
| nemotron_h_tp1_hd64_fp32_canonical_b64 | 64 | 1 | 128 | 8 | 64 | 128 |
FP32 | FP32 dt/D, int64 index | softplus | 73.336 | 73.392 | 0.999x |
same |
| nemotron_h_tp1_hd64_fp32_sglang_raw_b256 | 256 | 1 | 128 | 8 | 64 |
128 | FP32 | BF16 dt/D, int32 index | softplus | 298.864 | 298.856 |
1.000x | same |
| nemotron_h_tp1_hd64_fp32_canonical_b256 | 256 | 1 | 128 | 8 | 64 | 128
| FP32 | FP32 dt/D, int64 index | softplus | 298.752 | 298.744 | 1.000x
| same |
| nemotron_h_tp1_hd64_fp32_sglang_raw_b2 | 2 | 1 | 128 | 8 | 64 | 128 |
FP32 | BF16 dt/D, int32 index | softplus | 4.480 | 4.480 | 1.000x | same
|
| nemotron_h_tp1_hd64_fp32_sglang_raw_b4 | 4 | 1 | 128 | 8 | 64 | 128 |
FP32 | BF16 dt/D, int32 index | softplus | 6.544 | 6.544 | 1.000x | same
|
| nemotron_h_tp1_hd64_fp32_sglang_raw_b16 | 16 | 1 | 128 | 8 | 64 | 128
| FP32 | BF16 dt/D, int32 index | softplus | 17.248 | 17.240 | 1.000x |
same |
| nemotron_h_tp1_hd64_fp32_sglang_raw_b32 | 32 | 1 | 128 | 8 | 64 | 128
| FP32 | BF16 dt/D, int32 index | softplus | 35.672 | 35.680 | 1.000x |
same |
| nemotron_h_tp2_hd64_sglang_raw_b1 | 1 | 1 | 64 | 4 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 2.848 | 2.848 | 1.000x | same |
| nemotron_h_tp2_hd64_canonical_b1 | 1 | 1 | 64 | 4 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 2.704 | 2.704 | 1.000x | same |
| nemotron_h_tp2_hd64_sglang_raw_b64 | 64 | 1 | 64 | 4 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 18.384 | 18.384 | 1.000x | same |
| nemotron_h_tp2_hd64_canonical_b64 | 64 | 1 | 64 | 4 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 18.016 | 18.016 | 1.000x | same |
| nemotron_h_tp2_hd64_sglang_raw_b256 | 256 | 1 | 64 | 4 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 75.448 | 75.440 | 1.000x |
same |
| nemotron_h_tp2_hd64_canonical_b256 | 256 | 1 | 64 | 4 | 64 | 128 |
BF16 | FP32 dt/D, int64 index | softplus | 75.512 | 75.504 | 1.000x |
same |
| nemotron_h_tp2_hd64_sglang_raw_b2 | 2 | 1 | 64 | 4 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 3.072 | 3.072 | 1.000x | same |
| nemotron_h_tp2_hd64_sglang_raw_b4 | 4 | 1 | 64 | 4 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 3.480 | 3.488 | 0.998x | same |
| nemotron_h_tp2_hd64_sglang_raw_b8 | 8 | 1 | 64 | 4 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 4.752 | 4.752 | 1.000x | same |
| nemotron_h_tp2_hd64_sglang_raw_b16 | 16 | 1 | 64 | 4 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 6.624 | 6.624 | 1.000x | same |
| nemotron_h_tp2_hd64_sglang_raw_b32 | 32 | 1 | 64 | 4 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 9.936 | 9.936 | 1.000x | same |
| nemotron_h_tp2_hd64_sglang_raw_b128 | 128 | 1 | 64 | 4 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 37.344 | 37.344 | 1.000x |
same |
| nemotron_h_tp4_hd64_sglang_raw_b1 | 1 | 1 | 32 | 2 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 2.560 | 2.544 | 1.006x | same |
| nemotron_h_tp4_hd64_canonical_b1 | 1 | 1 | 32 | 2 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 2.608 | 2.624 | 0.994x | same |
| nemotron_h_tp4_hd64_sglang_raw_b64 | 64 | 1 | 32 | 2 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 9.968 | 9.960 | 1.001x | same |
| nemotron_h_tp4_hd64_canonical_b64 | 64 | 1 | 32 | 2 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 10.016 | 10.016 | 1.000x | same |
| nemotron_h_tp4_hd64_sglang_raw_b256 | 256 | 1 | 32 | 2 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 37.360 | 37.368 | 1.000x |
same |
| nemotron_h_tp4_hd64_canonical_b256 | 256 | 1 | 32 | 2 | 64 | 128 |
BF16 | FP32 dt/D, int64 index | softplus | 37.664 | 37.632 | 1.001x |
same |
| nemotron_h_tp4_hd64_sglang_raw_b4 | 4 | 1 | 32 | 2 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 3.072 | 3.064 | 1.003x | same |
| nemotron_h_tp4_hd64_sglang_raw_b8 | 8 | 1 | 32 | 2 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 3.520 | 3.512 | 1.002x | same |
| nemotron_h_tp4_hd64_sglang_raw_b16 | 16 | 1 | 32 | 2 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 4.720 | 4.720 | 1.000x | same |
| nemotron_h_tp4_hd64_sglang_raw_b32 | 32 | 1 | 32 | 2 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 6.672 | 6.672 | 1.000x | same |
| nemotron_h_tp4_hd64_sglang_raw_b128 | 128 | 1 | 32 | 2 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 18.288 | 18.288 | 1.000x |
same |
| granite_h_small_hd64_sglang_raw_b1 | 1 | 1 | 128 | 1 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 2.992 | 2.992 | 1.000x | same |
| granite_h_small_hd64_canonical_b1 | 1 | 1 | 128 | 1 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 3.088 | 3.088 | 1.000x | same |
| granite_h_small_hd64_sglang_raw_b8 | 8 | 1 | 128 | 1 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 6.496 | 6.496 | 1.000x | same |
| granite_h_small_hd64_canonical_b8 | 8 | 1 | 128 | 1 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 6.528 | 6.528 | 1.000x | same |
| granite_h_small_hd64_sglang_raw_b64 | 64 | 1 | 128 | 1 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 37.392 | 37.360 | 1.001x |
same |
| granite_h_small_hd64_canonical_b64 | 64 | 1 | 128 | 1 | 64 | 128 |
BF16 | FP32 dt/D, int64 index | softplus | 37.400 | 37.392 | 1.000x |
same |
| granite_h_small_hd64_sglang_raw_b256 | 256 | 1 | 128 | 1 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 150.832 | 150.864 | 1.000x |
same |
| granite_h_small_hd64_canonical_b256 | 256 | 1 | 128 | 1 | 64 | 128 |
BF16 | FP32 dt/D, int64 index | softplus | 150.856 | 150.872 | 1.000x |
same |
| granite_h_tiny_hd64_sglang_raw_b1 | 1 | 1 | 48 | 1 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 2.672 | 2.664 | 1.003x | same |
| granite_h_tiny_hd64_canonical_b1 | 1 | 1 | 48 | 1 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 2.736 | 2.736 | 1.000x | same |
| granite_h_tiny_hd64_sglang_raw_b64 | 64 | 1 | 48 | 1 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 14.144 | 14.152 | 0.999x | same |
| granite_h_tiny_hd64_canonical_b64 | 64 | 1 | 48 | 1 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 14.128 | 14.128 | 1.000x | same |
| fitest_stp_hd64_rows_bf16 | 4 | 1 | 128 | 8 | 64 | 128 | BF16 | FP32
dt/D, int64 index | - | 4.800 | 4.784 | 1.003x | same |
| fitest_stp_hd64_paired_rows | 64 | 1 | 128 | 8 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | - | 37.392 | 37.400 | 1.000x | same |
| fitest_stp_hd64_paired_rows_b320 | 320 | 1 | 128 | 8 | 64 | 128 | BF16
| FP32 dt/D, int64 index | - | 188.824 | 188.832 | 1.000x | same |
| fitest_stp_hd64_fp32 | 64 | 1 | 128 | 8 | 64 | 128 | FP32 | FP32 dt/D,
int64 index | - | 73.344 | 73.360 | 1.000x | same |
| fitest_stp_hd64_odd_pairs | 8 | 1 | 24 | 8 | 64 | 128 | BF16 | FP32
dt/D, int64 index | - | 3.328 | 3.328 | 1.000x | same |
| fitest_stp_hd64_raw_rows | 2 | 1 | 128 | 8 | 64 | 128 | BF16 | BF16
dt/D, int32 index | softplus | 3.600 | 3.600 | 1.000x | same |
| fitest_stp_hd64_raw_paired | 64 | 1 | 128 | 8 | 64 | 128 | BF16 | BF16
dt/D, int32 index | softplus | 37.368 | 37.360 | 1.000x | same |
| fitest_stp_hd64_raw_fp32 | 8 | 1 | 128 | 8 | 64 | 128 | FP32 | BF16
dt/D, int32 index | softplus | 10.288 | 10.304 | 0.998x | same |
| fitest_stp_hd64_raw_paired_four_cta | 16 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 9.944 | 9.952 | 0.999x | same
|

*NVIDIA GB300 (sm_103a, 152 SMs), CUDA 13.4, driver 580.159.03: the two
z-gated shapes on 12 GB300 GPUs of three nodes (4 per node), two
separate 9-round interleaved sessions per GPU. Times are medians over 9
rounds (us). Speedup = main / this PR. Outputs and states are bitwise
identical to main's on every GPU.*

| node | GPU | case | main (us), run 1 / run 2 | this PR (us), run 1 /
run 2 | speedup, run 1 / run 2 |
|---|---|---|---:|---:|---:|
| node A | 0 | sample_stp_z | 38.768 / 38.736 | 37.440 / 37.423 | 1.035x
/ 1.035x |
| node A | 0 | sample_stp_z_softplus | 39.040 / 39.056 | 37.392 / 37.408
| 1.044x / 1.044x |
| node A | 1 | sample_stp_z | 38.704 / 38.736 | 38.096 / 38.048 | 1.016x
/ 1.018x |
| node A | 1 | sample_stp_z_softplus | 39.104 / 39.168 | 37.536 / 37.599
| 1.042x / 1.042x |
| node A | 2 | sample_stp_z | 38.768 / 38.816 | 37.520 / 37.584 | 1.033x
/ 1.033x |
| node A | 2 | sample_stp_z_softplus | 39.184 / 39.184 | 37.344 / 37.280
| 1.049x / 1.051x |
| node A | 3 | sample_stp_z | 38.736 / 38.752 | 37.920 / 37.935 | 1.022x
/ 1.022x |
| node A | 3 | sample_stp_z_softplus | 39.264 / 39.280 | 37.408 / 37.392
| 1.050x / 1.050x |
| node B | 0 | sample_stp_z | 38.784 / 38.768 | 37.984 / 38.064 | 1.021x
/ 1.018x |
| node B | 0 | sample_stp_z_softplus | 39.088 / 39.072 | 37.824 / 37.808
| 1.033x / 1.033x |
| node B | 1 | sample_stp_z | 38.672 / 38.720 | 37.936 / 38.000 | 1.019x
/ 1.019x |
| node B | 1 | sample_stp_z_softplus | 38.928 / 38.944 | 37.664 / 37.727
| 1.034x / 1.032x |
| node B | 2 | sample_stp_z | 38.400 / 38.416 | 37.248 / 37.232 | 1.031x
/ 1.032x |
| node B | 2 | sample_stp_z_softplus | 38.672 / 38.736 | 37.088 / 37.088
| 1.043x / 1.044x |
| node B | 3 | sample_stp_z | 38.496 / 38.528 | 37.552 / 37.488 | 1.025x
/ 1.028x |
| node B | 3 | sample_stp_z_softplus | 38.720 / 38.720 | 37.136 / 37.152
| 1.043x / 1.042x |
| node C | 0 | sample_stp_z | 38.592 / 38.592 | 37.280 / 37.328 | 1.035x
/ 1.034x |
| node C | 0 | sample_stp_z_softplus | 38.912 / 39.024 | 37.152 / 37.152
| 1.047x / 1.050x |
| node C | 1 | sample_stp_z | 38.656 / 38.640 | 37.760 / 37.776 | 1.024x
/ 1.023x |
| node C | 1 | sample_stp_z_softplus | 38.896 / 38.912 | 37.248 / 37.264
| 1.044x / 1.044x |
| node C | 2 | sample_stp_z | 38.432 / 38.480 | 37.616 / 37.632 | 1.022x
/ 1.023x |
| node C | 2 | sample_stp_z_softplus | 38.704 / 38.736 | 37.216 / 37.280
| 1.040x / 1.039x |
| node C | 3 | sample_stp_z | 38.384 / 38.416 | 37.328 / 37.312 | 1.028x
/ 1.030x |
| node C | 3 | sample_stp_z_softplus | 38.688 / 38.640 | 37.136 / 37.136
| 1.042x / 1.040x |

*NVIDIA B200 (sm_100a, 148 SMs), driver 580.82.07, CUDA 13.4; PyTorch
2.14.1+cu130; programs compiled with nvcc 13.4. Timer: CUPTI kernel time
with a cold L2; times are medians over 2 runs x 9 interleaved rounds
(us); speedup = main / this PR; the program column says whether this PR
routes the shape to a different program (`new`) or keeps main's
(`same`).*

| case | batch | tokens | heads | groups | head dim | state dim | state
| inputs | options | main (us) | this PR (us) | speedup | program |
|---|---:|---:|---:|---:|---:|---:|---|---|---|---:|---:|---:|---|
| sample_stp_bf16 | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 37.640 | 37.656 | 1.000x | same |
| sample_stp_state_fp32 | 64 | 1 | 64 | 8 | 128 | 128 | FP32 | FP32
dt/D, int64 index | - | 75.816 | 75.816 | 1.000x | same |
| sample_stp_z | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D, int64
index | z gate | 38.328 | 38.336 | 1.000x | same |
| sample_stp_softplus | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | softplus | 37.680 | 37.608 | 1.002x | same |
| sample_stp_z_softplus | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32
dt/D, int64 index | z gate, softplus | 38.400 | 38.376 | 1.001x | same |
| sample_stp_ratio1 | 32 | 1 | 16 | 16 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 7.808 | 7.808 | 1.000x | same |
| sample_stp_ratio16 | 32 | 1 | 128 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 38.736 | 38.744 | 1.000x | same |
| sample_stp_b256 | 256 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 155.448 | 155.431 | 1.000x | same |
| sample_stp_b128 | 128 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 78.256 | 78.248 | 1.000x | same |
| sample_mtp1 | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D, int64
index | - | 37.808 | 37.840 | 0.999x | same |
| sample_mtp2 | 64 | 2 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D, int64
index | - | 39.376 | 39.440 | 0.998x | same |
| sweep_bfloat16_vertical_b1 | 1 | 6 | 64 | 8 | 64 | 128 | BF16 | FP32
dt/D, int64 index | softplus, state cache, no state write,
algorithm=vertical | 3.744 | 3.744 | 1.000x | same |
| sweep_bfloat16_horizontal_b1024 | 1024 | 6 | 64 | 8 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus, state cache, no state write,
algorithm=horizontal | 1192.579 | 1197.196 | 0.996x | same |
| dynamic_dump_b1_t1_prev0 | 1 | 1 | 16 | 1 | 64 | 128 | FP32 | FP32
dt/D, int64 index | softplus, dst slots, algorithm=simple | 2.800 |
2.808 | 0.997x | same |
| dynamic_dump_b1_t2_prev1 | 1 | 2 | 16 | 1 | 64 | 128 | FP32 | FP32
dt/D, int64 index | softplus, dst slots, algorithm=simple | 2.976 |
2.976 | 1.000x | same |
| dynamic_dump_b1_t4_prev2 | 1 | 4 | 16 | 1 | 64 | 128 | FP32 | FP32
dt/D, int64 index | softplus, dst slots, algorithm=simple | 3.120 |
3.128 | 0.997x | same |
| dynamic_dump_b1_t8_prev4 | 1 | 8 | 16 | 1 | 64 | 128 | FP32 | FP32
dt/D, int64 index | softplus, dst slots, algorithm=simple | 3.536 |
3.544 | 0.998x | same |
| dynamic_dump_b1_t8_prev8 | 1 | 8 | 16 | 1 | 64 | 128 | FP32 | FP32
dt/D, int64 index | softplus, dst slots, algorithm=simple | 3.552 |
3.553 | 1.000x | same |
| granite_ngram_t6_c4_legacy_adapted_graph_b1 | 1 | 6 | 64 | 1 | 64 |
128 | BF16 | FP32 dt/D, int64 index | softplus, state cache, no state
write, algorithm=vertical | 3.760 | 3.744 | 1.004x | same |
| granite_ngram_t6_c4_legacy_adapted_graph_b2 | 2 | 6 | 64 | 1 | 64 |
128 | BF16 | FP32 dt/D, int64 index | softplus, state cache, no state
write, algorithm=vertical | 4.760 | 4.752 | 1.002x | same |
| granite_ngram_t6_c4_legacy_adapted_graph_b3 | 3 | 6 | 64 | 1 | 64 |
128 | BF16 | FP32 dt/D, int64 index | softplus, state cache, no state
write, algorithm=vertical | 6.008 | 6.024 | 0.997x | same |
| granite_ngram_t6_c4_legacy_adapted_graph_b4 | 4 | 6 | 64 | 1 | 64 |
128 | BF16 | FP32 dt/D, int64 index | softplus, state cache, no state
write, algorithm=vertical | 6.688 | 6.688 | 1.000x | same |
| granite_ngram_t6_c4_sglang_raw_b1 | 1 | 6 | 64 | 1 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus, state cache, no state write | 3.936 |
3.944 | 0.998x | same |
| granite_ngram_t6_c4_sglang_raw_b2 | 2 | 6 | 64 | 1 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus, state cache, no state write | 4.992 |
4.992 | 1.000x | same |
| granite_ngram_t6_c4_sglang_raw_b3 | 3 | 6 | 64 | 1 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus, state cache, no state write | 6.176 |
6.176 | 1.000x | same |
| granite_ngram_t6_c4_sglang_raw_b4 | 4 | 6 | 64 | 1 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus, state cache, no state write | 6.960 |
6.960 | 1.000x | same |
| fitest_stp_ratio1 | 32 | 1 | 16 | 16 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 7.808 | 7.800 | 1.001x | same |
| fitest_stp_ratio8 | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 37.792 | 37.784 | 1.000x | same |
| fitest_stp_ratio8_sat | 128 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32
dt/D, int64 index | - | 78.248 | 78.256 | 1.000x | same |
| fitest_stp_ratio16 | 32 | 1 | 128 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 38.728 | 38.712 | 1.000x | same |
| fitest_stp_persistent | 257 | 1 | 128 | 8 | 128 | 128 | BF16 | FP32
dt/D, int64 index | - | 312.015 | 312.031 | 1.000x | same |
| fitest_stp_fp32 | 64 | 1 | 64 | 8 | 128 | 128 | FP32 | FP32 dt/D,
int64 index | - | 75.719 | 75.720 | 1.000x | same |
| fitest_mtp_short1 | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 37.816 | 37.824 | 1.000x | same |
| fitest_mtp_short2 | 64 | 2 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 39.367 | 39.384 | 1.000x | same |
| fitest_mtp_cache | 1 | 6 | 64 | 8 | 64 | 128 | BF16 | FP32 dt/D, int64
index | softplus, state cache, no state write, algorithm=vertical |
3.744 | 3.728 | 1.004x | same |
| fitest_mtp_horizontal | 32 | 6 | 64 | 8 | 64 | 128 | BF16 | FP32 dt/D,
int64 index | softplus, state cache, no state write,
algorithm=horizontal | 39.632 | 39.640 | 1.000x | same |
| fitest_dynamic0 | 1 | 1 | 16 | 1 | 64 | 128 | FP32 | FP32 dt/D, int64
index | softplus, dst slots, algorithm=simple | 2.800 | 2.808 | 0.997x |
same |
| fitest_dynamic0_b8 | 8 | 2 | 16 | 1 | 64 | 128 | FP32 | FP32 dt/D,
int64 index | softplus, dst slots, algorithm=simple | 4.160 | 4.176 |
0.996x | same |
| fitest_dynamic1 | 1 | 4 | 16 | 1 | 64 | 128 | FP32 | FP32 dt/D, int64
index | softplus, dst slots, algorithm=simple | 3.129 | 3.120 | 1.003x |
same |
| fitest_dynamic3 | 1 | 8 | 16 | 1 | 64 | 128 | FP32 | FP32 dt/D, int64
index | softplus, dst slots, algorithm=simple | 3.537 | 3.536 | 1.000x |
same |
| fitest_dynamic7 | 1 | 8 | 16 | 1 | 64 | 128 | FP32 | FP32 dt/D, int64
index | softplus, dst slots, algorithm=simple | 3.551 | 3.544 | 1.002x |
same |
| sweep_bfloat16_auto_b1 | 1 | 6 | 64 | 8 | 64 | 128 | BF16 | FP32 dt/D,
int64 index | softplus, state cache, no state write | 3.728 | 3.728 |
1.000x | same |
| dynamic_dump_b8_t2_prev1 | 8 | 2 | 16 | 1 | 64 | 128 | FP32 | FP32
dt/D, int64 index | softplus, dst slots, algorithm=simple | 4.160 |
4.175 | 0.996x | same |
| nemotron_h_tp1_hd64_sglang_raw_b1 | 1 | 1 | 128 | 8 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 3.104 | 3.104 | 1.000x | same |
| nemotron_h_tp1_hd64_canonical_b1 | 1 | 1 | 128 | 8 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 3.089 | 3.089 | 1.000x | same |
| nemotron_h_tp1_hd64_sglang_raw_b2 | 2 | 1 | 128 | 8 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 3.664 | 3.664 | 1.000x | same |
| nemotron_h_tp1_hd64_canonical_b2 | 2 | 1 | 128 | 8 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 3.672 | 3.680 | 0.998x | same |
| nemotron_h_tp1_hd64_sglang_raw_b4 | 4 | 1 | 128 | 8 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 4.896 | 4.896 | 1.000x | same |
| nemotron_h_tp1_hd64_canonical_b4 | 4 | 1 | 128 | 8 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 4.944 | 4.944 | 1.000x | same |
| nemotron_h_tp1_hd64_sglang_raw_b8 | 8 | 1 | 128 | 8 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 7.072 | 7.056 | 1.002x | same |
| nemotron_h_tp1_hd64_canonical_b8 | 8 | 1 | 128 | 8 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 6.992 | 6.984 | 1.001x | same |
| nemotron_h_tp1_hd64_sglang_raw_b16 | 16 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 10.304 | 10.320 | 0.998x |
same |
| nemotron_h_tp1_hd64_canonical_b16 | 16 | 1 | 128 | 8 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 10.480 | 10.504 | 0.998x | same |
| nemotron_h_tp1_hd64_sglang_raw_b32 | 32 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 19.056 | 19.056 | 1.000x |
same |
| nemotron_h_tp1_hd64_canonical_b32 | 32 | 1 | 128 | 8 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 19.056 | 19.056 | 1.000x | same |
| nemotron_h_tp1_hd64_sglang_raw_b64 | 64 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 38.976 | 38.984 | 1.000x |
same |
| nemotron_h_tp1_hd64_canonical_b64 | 64 | 1 | 128 | 8 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 39.071 | 39.064 | 1.000x | same |
| nemotron_h_tp1_hd64_sglang_raw_b128 | 128 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 78.224 | 78.240 | 1.000x |
same |
| nemotron_h_tp1_hd64_canonical_b128 | 128 | 1 | 128 | 8 | 64 | 128 |
BF16 | FP32 dt/D, int64 index | softplus | 78.288 | 78.280 | 1.000x |
same |
| nemotron_h_tp1_hd64_sglang_raw_b256 | 256 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 155.664 | 155.687 | 1.000x |
same |
| nemotron_h_tp1_hd64_canonical_b256 | 256 | 1 | 128 | 8 | 64 | 128 |
BF16 | FP32 dt/D, int64 index | softplus | 155.904 | 155.944 | 1.000x |
same |
| nemotron_h_tp1_hd64_sglang_raw_b6 | 6 | 1 | 128 | 8 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 6.032 | 6.032 | 1.000x | same |
| nemotron_h_tp1_hd64_sglang_raw_b12 | 12 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 8.800 | 8.816 | 0.998x | same
|
| nemotron_h_tp1_hd64_sglang_raw_b20 | 20 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 12.624 | 12.624 | 1.000x |
same |
| nemotron_h_tp1_hd64_sglang_raw_b24 | 24 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 14.768 | 14.768 | 1.000x |
same |
| nemotron_h_tp1_hd64_sglang_raw_b48 | 48 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 29.048 | 29.055 | 1.000x |
same |
| nemotron_h_tp1_hd64_fp32_sglang_raw_b1 | 1 | 1 | 128 | 8 | 64 | 128 |
FP32 | BF16 dt/D, int32 index | softplus | 3.648 | 3.640 | 1.002x | same
|
| nemotron_h_tp1_hd64_fp32_canonical_b1 | 1 | 1 | 128 | 8 | 64 | 128 |
FP32 | FP32 dt/D, int64 index | softplus | 3.472 | 3.472 | 1.000x | same
|
| nemotron_h_tp1_hd64_fp32_sglang_raw_b8 | 8 | 1 | 128 | 8 | 64 | 128 |
FP32 | BF16 dt/D, int32 index | softplus | 10.880 | 10.896 | 0.999x |
same |
| nemotron_h_tp1_hd64_fp32_canonical_b8 | 8 | 1 | 128 | 8 | 64 | 128 |
FP32 | FP32 dt/D, int64 index | softplus | 10.832 | 10.848 | 0.999x |
same |
| nemotron_h_tp1_hd64_fp32_sglang_raw_b64 | 64 | 1 | 128 | 8 | 64 | 128
| FP32 | BF16 dt/D, int32 index | softplus | 75.424 | 75.424 | 1.000x |
same |
| nemotron_h_tp1_hd64_fp32_canonical_b64 | 64 | 1 | 128 | 8 | 64 | 128 |
FP32 | FP32 dt/D, int64 index | softplus | 75.848 | 75.872 | 1.000x |
same |
| nemotron_h_tp1_hd64_fp32_sglang_raw_b256 | 256 | 1 | 128 | 8 | 64 |
128 | FP32 | BF16 dt/D, int32 index | softplus | 307.312 | 307.015 |
1.001x | same |
| nemotron_h_tp1_hd64_fp32_canonical_b256 | 256 | 1 | 128 | 8 | 64 | 128
| FP32 | FP32 dt/D, int64 index | softplus | 306.695 | 306.519 | 1.001x
| same |
| nemotron_h_tp1_hd64_fp32_sglang_raw_b2 | 2 | 1 | 128 | 8 | 64 | 128 |
FP32 | BF16 dt/D, int32 index | softplus | 4.704 | 4.704 | 1.000x | same
|
| nemotron_h_tp1_hd64_fp32_sglang_raw_b4 | 4 | 1 | 128 | 8 | 64 | 128 |
FP32 | BF16 dt/D, int32 index | softplus | 6.880 | 6.872 | 1.001x | same
|
| nemotron_h_tp1_hd64_fp32_sglang_raw_b16 | 16 | 1 | 128 | 8 | 64 | 128
| FP32 | BF16 dt/D, int32 index | softplus | 18.224 | 18.240 | 0.999x |
same |
| nemotron_h_tp1_hd64_fp32_sglang_raw_b32 | 32 | 1 | 128 | 8 | 64 | 128
| FP32 | BF16 dt/D, int32 index | softplus | 37.424 | 37.416 | 1.000x |
same |
| nemotron_h_tp2_hd64_sglang_raw_b1 | 1 | 1 | 64 | 4 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 2.913 | 2.928 | 0.995x | same |
| nemotron_h_tp2_hd64_canonical_b1 | 1 | 1 | 64 | 4 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 2.880 | 2.880 | 1.000x | same |
| nemotron_h_tp2_hd64_sglang_raw_b64 | 64 | 1 | 64 | 4 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 19.088 | 19.088 | 1.000x | same |
| nemotron_h_tp2_hd64_canonical_b64 | 64 | 1 | 64 | 4 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 19.024 | 19.016 | 1.000x | same |
| nemotron_h_tp2_hd64_sglang_raw_b256 | 256 | 1 | 64 | 4 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 78.168 | 78.160 | 1.000x |
same |
| nemotron_h_tp2_hd64_canonical_b256 | 256 | 1 | 64 | 4 | 64 | 128 |
BF16 | FP32 dt/D, int64 index | softplus | 78.016 | 77.992 | 1.000x |
same |
| nemotron_h_tp2_hd64_sglang_raw_b2 | 2 | 1 | 64 | 4 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 3.120 | 3.120 | 1.000x | same |
| nemotron_h_tp2_hd64_sglang_raw_b4 | 4 | 1 | 64 | 4 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 3.632 | 3.632 | 1.000x | same |
| nemotron_h_tp2_hd64_sglang_raw_b8 | 8 | 1 | 64 | 4 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 4.912 | 4.912 | 1.000x | same |
| nemotron_h_tp2_hd64_sglang_raw_b16 | 16 | 1 | 64 | 4 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 7.024 | 7.008 | 1.002x | same |
| nemotron_h_tp2_hd64_sglang_raw_b32 | 32 | 1 | 64 | 4 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 10.384 | 10.400 | 0.998x | same |
| nemotron_h_tp2_hd64_sglang_raw_b128 | 128 | 1 | 64 | 4 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 39.000 | 38.992 | 1.000x |
same |
| nemotron_h_tp4_hd64_sglang_raw_b1 | 1 | 1 | 32 | 2 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 2.640 | 2.656 | 0.994x | same |
| nemotron_h_tp4_hd64_canonical_b1 | 1 | 1 | 32 | 2 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 2.816 | 2.817 | 1.000x | same |
| nemotron_h_tp4_hd64_sglang_raw_b64 | 64 | 1 | 32 | 2 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 10.392 | 10.400 | 0.999x | same |
| nemotron_h_tp4_hd64_canonical_b64 | 64 | 1 | 32 | 2 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 10.432 | 10.440 | 0.999x | same |
| nemotron_h_tp4_hd64_sglang_raw_b256 | 256 | 1 | 32 | 2 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 38.944 | 38.944 | 1.000x |
same |
| nemotron_h_tp4_hd64_canonical_b256 | 256 | 1 | 32 | 2 | 64 | 128 |
BF16 | FP32 dt/D, int64 index | softplus | 39.128 | 39.120 | 1.000x |
same |
| nemotron_h_tp4_hd64_sglang_raw_b4 | 4 | 1 | 32 | 2 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 3.136 | 3.136 | 1.000x | same |
| nemotron_h_tp4_hd64_sglang_raw_b8 | 8 | 1 | 32 | 2 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 3.632 | 3.624 | 1.002x | same |
| nemotron_h_tp4_hd64_sglang_raw_b16 | 16 | 1 | 32 | 2 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 4.880 | 4.880 | 1.000x | same |
| nemotron_h_tp4_hd64_sglang_raw_b32 | 32 | 1 | 32 | 2 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 7.024 | 7.024 | 1.000x | same |
| nemotron_h_tp4_hd64_sglang_raw_b128 | 128 | 1 | 32 | 2 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 19.040 | 19.072 | 0.998x |
same |
| granite_h_small_hd64_sglang_raw_b1 | 1 | 1 | 128 | 1 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 3.024 | 3.040 | 0.995x | same |
| granite_h_small_hd64_canonical_b1 | 1 | 1 | 128 | 1 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 3.168 | 3.168 | 1.000x | same |
| granite_h_small_hd64_sglang_raw_b8 | 8 | 1 | 128 | 1 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 6.960 | 6.944 | 1.002x | same |
| granite_h_small_hd64_canonical_b8 | 8 | 1 | 128 | 1 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 6.968 | 6.960 | 1.001x | same |
| granite_h_small_hd64_sglang_raw_b64 | 64 | 1 | 128 | 1 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 38.960 | 38.944 | 1.000x |
same |
| granite_h_small_hd64_canonical_b64 | 64 | 1 | 128 | 1 | 64 | 128 |
BF16 | FP32 dt/D, int64 index | softplus | 39.064 | 39.063 | 1.000x |
same |
| granite_h_small_hd64_sglang_raw_b256 | 256 | 1 | 128 | 1 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 155.543 | 155.511 | 1.000x |
same |
| granite_h_small_hd64_canonical_b256 | 256 | 1 | 128 | 1 | 64 | 128 |
BF16 | FP32 dt/D, int64 index | softplus | 155.472 | 155.519 | 1.000x |
same |
| granite_h_tiny_hd64_sglang_raw_b1 | 1 | 1 | 48 | 1 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 2.752 | 2.760 | 0.997x | same |
| granite_h_tiny_hd64_canonical_b1 | 1 | 1 | 48 | 1 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 2.816 | 2.816 | 1.000x | same |
| granite_h_tiny_hd64_sglang_raw_b64 | 64 | 1 | 48 | 1 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 14.752 | 14.752 | 1.000x | same |
| granite_h_tiny_hd64_canonical_b64 | 64 | 1 | 48 | 1 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 14.736 | 14.736 | 1.000x | same |
| fitest_stp_hd64_rows_bf16 | 4 | 1 | 128 | 8 | 64 | 128 | BF16 | FP32
dt/D, int64 index | - | 4.944 | 4.944 | 1.000x | same |
| fitest_stp_hd64_paired_rows | 64 | 1 | 128 | 8 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | - | 39.008 | 39.008 | 1.000x | same |
| fitest_stp_hd64_paired_rows_b320 | 320 | 1 | 128 | 8 | 64 | 128 | BF16
| FP32 dt/D, int64 index | - | 194.495 | 194.503 | 1.000x | same |
| fitest_stp_hd64_fp32 | 64 | 1 | 128 | 8 | 64 | 128 | FP32 | FP32 dt/D,
int64 index | - | 75.696 | 75.704 | 1.000x | same |
| fitest_stp_hd64_odd_pairs | 8 | 1 | 24 | 8 | 64 | 128 | BF16 | FP32
dt/D, int64 index | - | 3.472 | 3.472 | 1.000x | same |
| fitest_stp_hd64_raw_rows | 2 | 1 | 128 | 8 | 64 | 128 | BF16 | BF16
dt/D, int32 index | softplus | 3.664 | 3.664 | 1.000x | same |
| fitest_stp_hd64_raw_paired | 64 | 1 | 128 | 8 | 64 | 128 | BF16 | BF16
dt/D, int32 index | softplus | 38.976 | 38.984 | 1.000x | same |
| fitest_stp_hd64_raw_fp32 | 8 | 1 | 128 | 8 | 64 | 128 | FP32 | BF16
dt/D, int32 index | softplus | 10.912 | 10.896 | 1.001x | same |
| fitest_stp_hd64_raw_paired_four_cta | 16 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 10.336 | 10.336 | 1.000x |
same |

Cake has no other variants of this kernel beyond the dimensions above,
and it ships the kernel only on sm_100a and sm_103a; this PR changes
routes only on sm_103a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added support for selective state updates on `sm_103a` GPUs, alongside
existing `sm_100a` support.
* **Improvements**
* Updated GPU-specific ring-buffer handling and selection for supported
hardware configurations. The state-update arithmetic remains unchanged.
* Adjusted hardware-specific routing so the z-gated one-token ring is
selected for the tested batch-64 configuration on both B200 and GB300.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [6dda7f6](https://github.com/flashinfer-ai/flashinfer/commit/6dda7f63f64876f74040de1649c0f2736119e5cd)

- **作者**: eigen
- **时间**: 2026-11-01T14:01:09Z
- **提交信息**: cake_gdn_cp: regenerate the SM107 T-precompute program with checked host descriptor arithmetic (#8200)

The context-parallel GDN prefill T-precompute kernel has four variants:
- `t_precompute`: FP16 I/O, int64 `cu_seqlens`
- `t_precompute_bf16`
- `t_precompute_cu32`: int32 `cu_seqlens`
- `t_precompute_bf16_cu32`

On SM 10.7 (R200), the FP16/int64 variant has a dedicated program,
`cake_gdn_cp_ce1c179ef0e27da84479`. This PR regenerates that program.
The kernel SASS is byte-identical to the version on main (1400
instructions, 80 registers). The change is in the host binding, which
now uses overflow-checked int64 arithmetic when setting up the TMA
descriptor and checks the TMA box against the extent on each axis, with
a clearer error message. The only change to the kernel source removes a
pre-SM100 fallback branch that this program never compiles.

The table compares this PR with the previous Cake version of this
program on main. Performance is unchanged within noise, at about 1.00x.

Geomean ratio: seed 17 0.9995, seed 29 0.9999.

*NVIDIA VR200 (R200), sm_107a, 212 SMs, driver 620.62; CUDA 13.4
toolchain (nvcc 13.4), CUDA runtime 13.0 (torch 2.14.1+cu130). Times are
paired cold-L2 CUPTI GPU times, median of 3 interleaved groups. ratio =
main latency / new latency, so > 1 means the new version is faster.*

| shape | s17 main us | s17 new us | s17 ratio | s29 main us | s29 new
us | s29 ratio |
|---|---:|---:|---:|---:|---:|---:|
| T=16384 Hk=2 Hsab=8 seq_lens=[16384] | 17.056 | 17.056 | 1.0000 |
17.056 | 17.056 | 1.0000 |
| T=65536 Hk=16 Hsab=16 seq_lens=[65536] | 120.178 | 120.114 | 1.0005 |
120.098 | 119.986 | 1.0009 |
| T=32768 Hk=16 Hsab=16 seq_lens=[32768] | 62.081 | 62.129 | 0.9992 |
62.145 | 62.033 | 1.0018 |
| T=8192 Hk=16 Hsab=16 seq_lens=[8192] | 18.081 | 18.064 | 1.0009 |
18.081 | 18.049 | 1.0018 |
| T=4096 Hk=16 Hsab=16 seq_lens=[4096] | 11.136 | 11.104 | 1.0029 |
11.168 | 11.136 | 1.0029 |
| T=8192 Hk=16 Hsab=16 seq_lens=[6144, 2048] | 18.320 | 18.304 | 1.0009
| 18.336 | 18.272 | 1.0035 |
| T=8192 Hk=16 Hsab=16 seq_lens=[4096, 4096] | 18.080 | 18.049 | 1.0017
| 18.081 | 18.017 | 1.0036 |
| T=8192 Hk=16 Hsab=16 seq_lens=[2048, 6144] | 19.136 | 19.120 | 1.0008
| 19.136 | 19.088 | 1.0025 |
| T=8192 Hk=16 Hsab=16 seq_lens=[1024, 7168] | 20.224 | 20.257 | 0.9984
| 20.224 | 20.257 | 0.9984 |
| T=65536 Hk=2 Hsab=8 seq_lens=[65536] | 59.313 | 59.185 | 1.0022 |
59.345 | 59.361 | 0.9997 |
| T=32768 Hk=2 Hsab=8 seq_lens=[32768] | 31.456 | 31.424 | 1.0010 |
31.456 | 31.392 | 1.0020 |
| T=8192 Hk=2 Hsab=8 seq_lens=[8192] | 10.576 | 10.544 | 1.0030 | 10.560
| 10.529 | 1.0029 |
| T=4096 Hk=2 Hsab=8 seq_lens=[4096] | 6.976 | 7.008 | 0.9954 | 6.993 |
7.008 | 0.9977 |
| T=8192 Hk=2 Hsab=8 seq_lens=[6144, 2048] | 10.560 | 10.529 | 1.0029 |
10.560 | 10.529 | 1.0029 |
| T=8192 Hk=2 Hsab=8 seq_lens=[4096, 4096] | 10.560 | 10.496 | 1.0061 |
10.576 | 10.592 | 0.9985 |
| T=8192 Hk=2 Hsab=8 seq_lens=[2048, 6144] | 10.000 | 10.016 | 0.9984 |
10.032 | 10.017 | 1.0016 |
| T=8192 Hk=2 Hsab=8 seq_lens=[1024, 7168] | 10.849 | 10.912 | 0.9942 |
10.880 | 10.912 | 0.9971 |
| T=65536 Hk=4 Hsab=16 seq_lens=[65536] | 114.018 | 113.954 | 1.0006 |
113.905 | 113.874 | 1.0003 |
| T=32768 Hk=4 Hsab=16 seq_lens=[32768] | 59.633 | 59.617 | 1.0003 |
59.617 | 59.681 | 0.9989 |
| T=16384 Hk=4 Hsab=16 seq_lens=[16384] | 31.585 | 31.536 | 1.0015 |
31.584 | 31.601 | 0.9995 |
| T=8192 Hk=4 Hsab=16 seq_lens=[8192] | 17.057 | 17.088 | 0.9982 |
17.088 | 17.088 | 1.0000 |
| T=4096 Hk=4 Hsab=16 seq_lens=[4096] | 10.656 | 10.624 | 1.0030 |
10.688 | 10.656 | 1.0030 |
| T=8192 Hk=4 Hsab=16 seq_lens=[6144, 2048] | 17.425 | 17.440 | 0.9991 |
17.409 | 17.440 | 0.9982 |
| T=8192 Hk=4 Hsab=16 seq_lens=[4096, 4096] | 17.072 | 17.072 | 1.0000 |
17.088 | 17.105 | 0.9991 |
| T=8192 Hk=4 Hsab=16 seq_lens=[2048, 6144] | 18.176 | 18.208 | 0.9982 |
18.176 | 18.209 | 0.9982 |
| T=8192 Hk=4 Hsab=16 seq_lens=[1024, 7168] | 19.264 | 19.328 | 0.9967 |
19.296 | 19.265 | 1.0016 |
| T=65536 Hk=8 Hsab=32 seq_lens=[65536] | 222.835 | 222.915 | 0.9996 |
222.788 | 222.851 | 0.9997 |
| T=32768 Hk=8 Hsab=32 seq_lens=[32768] | 114.370 | 114.481 | 0.9990 |
114.401 | 114.594 | 0.9983 |
| T=16384 Hk=8 Hsab=32 seq_lens=[16384] | 59.761 | 59.889 | 0.9979 |
59.777 | 60.001 | 0.9963 |
| T=8192 Hk=8 Hsab=32 seq_lens=[8192] | 31.744 | 31.776 | 0.9990 |
31.745 | 31.808 | 0.9980 |
| T=4096 Hk=8 Hsab=32 seq_lens=[4096] | 17.152 | 17.184 | 0.9981 |
17.152 | 17.153 | 0.9999 |
| T=65536 Hk=16 Hsab=32 seq_lens=[65536] | 225.155 | 225.188 | 0.9999 |
225.059 | 225.124 | 0.9997 |
| T=32768 Hk=16 Hsab=32 seq_lens=[32768] | 115.793 | 115.826 | 0.9997 |
115.745 | 115.842 | 0.9992 |
| T=16384 Hk=16 Hsab=32 seq_lens=[16384] | 60.801 | 60.865 | 0.9989 |
60.769 | 60.865 | 0.9984 |
| T=8192 Hk=16 Hsab=32 seq_lens=[8192] | 32.496 | 32.544 | 0.9985 |
32.512 | 32.513 | 1.0000 |
| T=4096 Hk=16 Hsab=32 seq_lens=[4096] | 17.472 | 17.536 | 0.9964 |
17.440 | 17.504 | 0.9963 |
| T=65536 Hk=16 Hsab=48 seq_lens=[65536] | 332.373 | 332.517 | 0.9996 |
332.453 | 332.437 | 1.0000 |
| T=32768 Hk=16 Hsab=48 seq_lens=[32768] | 169.139 | 169.138 | 1.0000 |
169.090 | 169.123 | 0.9998 |
| T=16384 Hk=16 Hsab=48 seq_lens=[16384] | 87.138 | 87.297 | 0.9982 |
87.217 | 87.138 | 1.0009 |
| T=8192 Hk=16 Hsab=48 seq_lens=[8192] | 45.984 | 46.017 | 0.9993 |
46.048 | 46.017 | 1.0007 |
| T=4096 Hk=16 Hsab=48 seq_lens=[4096] | 25.312 | 25.408 | 0.9962 |
25.344 | 25.408 | 0.9975 |
| T=16384 Hk=16 Hsab=16 seq_lens=[16384] | 33.217 | 33.280 | 0.9981 |
33.154 | 33.216 | 0.9981 |
| T=65536 Hk=32 Hsab=32 seq_lens=[65536] | 234.419 | 234.131 | 1.0012 |
234.163 | 234.291 | 0.9995 |
| T=32768 Hk=32 Hsab=32 seq_lens=[32768] | 120.594 | 120.706 | 0.9991 |
120.674 | 120.674 | 1.0000 |
| T=16384 Hk=32 Hsab=32 seq_lens=[16384] | 62.465 | 62.593 | 0.9979 |
62.497 | 62.625 | 0.9980 |
| T=8192 Hk=32 Hsab=32 seq_lens=[8192] | 33.456 | 33.456 | 1.0000 |
33.441 | 33.408 | 1.0010 |
| T=4096 Hk=32 Hsab=32 seq_lens=[4096] | 18.176 | 18.177 | 0.9999 |
18.176 | 18.208 | 0.9982 |
| T=193 Hk=2 Hsab=4 seq_lens=[64, 64, 65] | 3.744 | 3.776 | 0.9915 |
3.744 | 3.744 | 1.0000 |

This PR does not touch the kernel's other Cake variants: the BF16 and
int32-`cu_seqlens` variants, and the sm_100a / sm_103a programs
(`cake_gdn_cp_d5827d0f...` and the other variants listed above). The
kernel family ships on sm_100a, sm_103a and sm_107a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Descriptor dimensions and strides now use checked arithmetic,
preventing silent overflow during encoding.
* Invalid box extents are checked across all axes. Oversized boxes
remain allowed on axis 1; validation errors identify the axis, box size,
and extent, with guidance for handling tail tiles.
* Invalid multiplication, division, and remainder operations now raise
clear errors, including overflow and division by zero. Remainder by `-1`
returns zero.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [d548776](https://github.com/flashinfer-ai/flashinfer/commit/d548776a6170566b75e17712bc2cc7a146b6a4bf)

- **作者**: eigen
- **时间**: 2026-11-01T13:56:36Z
- **提交信息**: fix(cake_deepgemm_mega_mhc): one launch for hidden-4096 batches above 64 tokens/SM (#8199)

`flashinfer.mega_mhc` (`prepare_mega_mhc`) runs the fused
manifold-constrained hyper-connection (mHC) inference step. FlashInfer
main ships 43 per-arch programs for it:

- 14 hidden-5120 FP8-E4M3-output programs on sm_100a and sm_103a.
- For hidden 4096, five programs on each of sm_107a, sm_100a and
sm_103a: BF16 output, its tailpipe twin, its weight-staging tailpipe
twin, FP8 group-128 output and NVFP4 output.
- Four sm_107a-only tailpipe and weight-staging tailpipe forms of the
FP8 group-128 and NVFP4 variants.
- Three sm_107a-only FP8 group-128 UE8M0-scale-mode programs (plain,
tailpipe and weight-staging tailpipe).
- One sm_107a-only fast-division form of the plain FP8 group-128
program.
- Six sm_107a-only fast-chain forms: one each of the BF16-output
tailpipe program, the plain FP8 group-128 program (raw scale mode), the
plain FP8 group-128 program (UE8M0 scale mode), the FP8 group-128
weight-staging tailpipe program (raw scale mode), the FP8 group-128
UE8M0 tailpipe program and the NVFP4 tailpipe program.

This PR adds no program and changes no route. It removes a launch-time
check from the hidden-4096 program bindings. That check refused any
launch with more than 64 tokens per SM: the plan was created, then
`run()` raised `ValueError`. Callers with more tokens had to split the
batch into back-to-back calls under the limit. Now one call serves any T
in the documented range. Launches at or below the limit run
byte-identical compiled programs, so their outputs and timing do not
change. The baseline is the previous Cake version of the kernel, used
the only way it could serve these token counts: back-to-back calls over
chunks of at most 64 tokens per SM, each running the program the
dispatcher picks for it. Speedup = chunked / one launch. The speedup is
1.002x-1.065x on the 208-SM GPU and 1.007x-1.063x on the 216-SM GPU. For
BF16 output, the tables also compare one launch with FlashInfer's
non-fused sequence (`mhc_post`, FP32 matmul,
`mhc_pre_big_fuse_with_prenorm`, `rmsnorm`). That speedup is
6.686x-7.929x on the 208-SM GPU and 6.757x-8.052x on the 216-SM GPU.

Fused mHC inference step, hidden 4096, non-deterministic mode, on NVIDIA
R200 (208 SMs, sm_107a), driver 615.71.10, CUDA 13.4.92, PyTorch
2.14.1+cu130; SM clock 2406-2421 MHz during the measurement. One launch
over all tokens vs back-to-back launches over chunks of at most 13312
tokens (the only way to run more than 13312 tokens before this change;
each chunk takes the program the dispatcher picks for it) and vs the
FlashInfer non-fused sequence (mhc_post, FP32 matmul,
mhc_pre_big_fuse_with_prenorm, rmsnorm; BF16 output only). GPU kernel
time per call (sum over every kernel of the call, CUPTI), cold L2, 12
rounds x 64 calls with the arms interleaved; median of the round medians
[min, max], microseconds. Speedup = baseline / one launch; "(noise)" =
not beyond the run-to-run noise (ranges overlap or the difference is
within the repeat of the one-launch arm).

| tokens | output | one launch (us) | chunked launches (us) | speedup |
FlashInfer non-fused (us) | speedup | repeat of one launch (us) |
|---:|:--|--:|--:|--:|--:|--:|--:|
| 13313 | BF16 | 176.14 [176.03, 176.24] | 185.38 [185.14, 185.52] (2
calls) | 1.052x | 1374.95 [1374.62, 1375.59] | 7.806x | 175.89 [175.74,
176.00] |
| 13313 | FP8 (128-groups), UE8M0 scales | 182.19 [182.08, 182.38] |
192.43 [192.29, 192.62] (2 calls) | 1.056x | - | - | 181.69 [181.55,
181.82] |
| 13313 | FP8 (128-groups), scales not rounded to UE8M0 | 184.38
[184.24, 184.48] | 196.33 [196.00, 196.73] (2 calls) | 1.065x | - | - |
183.94 [183.79, 184.06] |
| 13313 | NVFP4 | 179.01 [178.69, 179.09] | 188.61 [188.45, 188.67] (2
calls) | 1.054x | - | - | 178.54 [178.43, 178.62] |
| 16384 | BF16 | 215.37 [215.23, 215.71] | 217.69 [217.39, 217.85] (2
calls) | 1.011x | 1607.49 [1606.88, 1607.77] | 7.464x | 215.82 [215.71,
215.97] |
| 16384 | FP8 (128-groups), UE8M0 scales | 223.17 [222.96, 223.33] |
227.08 [226.91, 227.45] (2 calls) | 1.017x | - | - | 223.04 [222.83,
223.17] |
| 16384 | FP8 (128-groups), scales not rounded to UE8M0 | 225.46
[225.28, 225.63] | 231.03 [230.73, 231.44] (2 calls) | 1.025x | - | - |
225.53 [225.41, 225.69] |
| 16384 | NVFP4 | 219.09 [218.97, 219.23] | 222.75 [222.54, 222.88] (2
calls) | 1.017x | - | - | 219.13 [218.97, 219.25] |
| 32768 | BF16 | 431.85 [431.52, 432.24] | 437.32 [436.99, 437.63] (3
calls) | 1.013x | 3424.10 [3423.67, 3424.93] | 7.929x | 431.68 [431.44,
432.14] |
| 32768 | FP8 (128-groups), UE8M0 scales | 447.32 [446.91, 447.42] |
454.24 [453.96, 454.35] (3 calls) | 1.015x | - | - | 447.73 [447.52,
447.90] |
| 32768 | FP8 (128-groups), scales not rounded to UE8M0 | 450.24
[449.90, 450.51] | 460.28 [460.01, 460.52] (3 calls) | 1.022x | - | - |
451.10 [450.59, 451.40] |
| 32768 | NVFP4 | 438.40 [438.11, 438.65] | 446.18 [446.04, 446.46] (3
calls) | 1.018x | - | - | 438.47 [438.03, 438.72] |
| 65536 | BF16 | 872.58 [871.35, 873.59] | 874.55 [874.27, 874.81] (5
calls) | 1.002x | 5834.46 [5834.04, 5834.78] | 6.686x | 871.79 [870.70,
872.57] |
| 65536 | FP8 (128-groups), UE8M0 scales | 903.45 [902.95, 904.17] |
905.50 [905.35, 905.87] (5 calls) | 1.002x | - | - | 902.79 [901.71,
903.24] |
| 65536 | FP8 (128-groups), scales not rounded to UE8M0 | 908.07
[907.66, 908.70] | 915.91 [915.51, 916.22] (5 calls) | 1.009x | - | - |
907.15 [906.52, 907.96] |
| 65536 | NVFP4 | 883.17 [882.41, 883.36] | 889.94 [889.70, 890.28] (5
calls) | 1.008x | - | - | 884.29 [883.67, 884.87] |

Fused mHC inference step, hidden 4096, non-deterministic mode, on NVIDIA
R200 (216 SMs, sm_107a), driver 615.71.10, CUDA 13.4.92, PyTorch
2.14.1+cu130; SM clock 2397-2419 MHz during the measurement. One launch
over all tokens vs back-to-back launches over chunks of at most 13824
tokens (the only way to run more than 13824 tokens before this change;
each chunk takes the program the dispatcher picks for it) and vs the
FlashInfer non-fused sequence (mhc_post, FP32 matmul,
mhc_pre_big_fuse_with_prenorm, rmsnorm; BF16 output only). GPU kernel
time per call (sum over every kernel of the call, CUPTI), cold L2, 12
rounds x 64 calls with the arms interleaved; median of the round medians
[min, max], microseconds. Speedup = baseline / one launch; "(noise)" =
not beyond the run-to-run noise (ranges overlap or the difference is
within the repeat of the one-launch arm).

| tokens | output | one launch (us) | chunked launches (us) | speedup |
FlashInfer non-fused (us) | speedup | repeat of one launch (us) |
|---:|:--|--:|--:|--:|--:|--:|--:|
| 13825 | BF16 | 176.10 [176.02, 176.14] | 185.48 [185.39, 185.73] (2
calls) | 1.053x | 1372.73 [1372.32, 1373.07] | 7.795x | 176.25 [176.08,
176.40] |
| 13825 | FP8 (128-groups), UE8M0 scales | 183.71 [183.57, 183.84] |
194.03 [193.74, 194.45] (2 calls) | 1.056x | - | - | 183.39 [183.31,
183.58] |
| 13825 | FP8 (128-groups), scales not rounded to UE8M0 | 186.36
[186.21, 186.46] | 198.14 [197.57, 198.26] (2 calls) | 1.063x | - | - |
185.82 [185.71, 185.98] |
| 13825 | NVFP4 | 180.43 [180.29, 180.51] | 190.50 [190.32, 190.83] (2
calls) | 1.056x | - | - | 180.39 [180.29, 180.45] |
| 16384 | BF16 | 208.07 [207.98, 208.19] | 212.28 [212.06, 212.37] (2
calls) | 1.020x | 1562.55 [1561.90, 1562.96] | 7.510x | 208.59 [208.46,
208.85] |
| 16384 | FP8 (128-groups), UE8M0 scales | 217.06 [216.96, 217.31] |
222.01 [221.94, 222.50] (2 calls) | 1.023x | - | - | 216.81 [216.67,
216.93] |
| 16384 | FP8 (128-groups), scales not rounded to UE8M0 | 219.50
[219.38, 219.62] | 225.92 [225.60, 226.27] (2 calls) | 1.029x | - | - |
219.15 [218.94, 219.30] |
| 16384 | NVFP4 | 212.93 [212.83, 213.06] | 218.18 [218.08, 218.32] (2
calls) | 1.025x | - | - | 212.90 [212.80, 212.99] |
| 32768 | BF16 | 414.77 [414.61, 414.99] | 421.88 [421.73, 422.08] (3
calls) | 1.017x | 3339.85 [3339.25, 3340.48] | 8.052x | 415.37 [415.25,
415.52] |
| 32768 | FP8 (128-groups), UE8M0 scales | 435.18 [435.04, 435.30] |
441.73 [441.63, 441.92] (3 calls) | 1.015x | - | - | 434.98 [434.59,
435.10] |
| 32768 | FP8 (128-groups), scales not rounded to UE8M0 | 438.82
[438.58, 439.01] | 449.57 [449.07, 449.92] (3 calls) | 1.024x | - | - |
438.98 [438.78, 439.18] |
| 32768 | NVFP4 | 426.49 [426.29, 426.74] | 434.63 [434.48, 434.88] (3
calls) | 1.019x | - | - | 426.55 [426.42, 426.78] |
| 65536 | BF16 | 837.89 [837.20, 838.38] | 845.45 [845.11, 845.60] (5
calls) | 1.009x | 5661.71 [5660.92, 5662.64] | 6.757x | 839.02 [838.45,
839.82] |
| 65536 | FP8 (128-groups), UE8M0 scales | 875.83 [875.27, 876.47] |
882.36 [882.02, 882.50] (5 calls) | 1.007x | - | - | 875.67 [875.46,
876.24] |
| 65536 | FP8 (128-groups), scales not rounded to UE8M0 | 881.28
[880.98, 881.63] | 893.03 [892.90, 893.25] (5 calls) | 1.013x | - | - |
881.67 [881.36, 882.10] |
| 65536 | NVFP4 | 856.20 [855.76, 856.39] | 866.32 [866.10, 866.50] (5
calls) | 1.012x | - | - | 857.27 [856.90, 857.75] |

The kernel's other Cake variants, the hidden-5120 programs and every
hidden-4096 launch at or below the limit keep their programs; the family
covers sm_100a, sm_103a and sm_107a, and the check is removed on all
three, though this PR reports timing only for sm_107a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Documentation**
* Clarified that kernel launches can use fewer CTAs than there are token
blocks, with blocks assigned across the launch grid.
* **Tests**
* Added coverage for BF16 and NVFP4 plans with hidden size 4096 when the
launch grid contains fewer CTAs than token blocks.
  * The tests also validate the plans’ outputs under this configuration.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery Huang <averyh@nvidia.com>

### [9b1376e](https://github.com/flashinfer-ai/flashinfer/commit/9b1376e9d7dfe0b3f529c0653946fcd1f6aface8)

- **作者**: eigen
- **时间**: 2026-11-01T13:50:35Z
- **提交信息**: perf(cake_lm_head_det_loss): opt-in kept logits for the log-probability backward (#8197)

## Summary

`chunked_lm_head_det_logprob` in
`flashinfer.experimental.cake_lm_head_det_loss` recomputes every chunk's
logits during the backward. That costs one logits GEMM per chunk, which
is about a quarter of a B200 step at T = 16231.

This PR adds an opt-in `memory_mode="keep_logits"`. With it, the forward
keeps each chunk's BF16 logits, which takes 2 * T_v * V bytes held until
the backward. The backward then forms dz from the kept logits with
`row_grad`, so it runs three GEMMs per chunk instead of four.

- **Bitwise identical:** logp, dX and dW match the default path bit for
bit.
- **Host-only:** the change uses the existing kernels and launch paths.
There is no change to device source, `build.json` or the JIT table.
- **Default path unchanged:** the kept form has its own entry points,
plan class, binding class, cache keys and memory report. We traced one
call on B200 and GB300, and the backend default path runs exactly main's
lines and calls. The opt-in entry adds one `try:` line.
- **Speed:** with `keep_logits`, a step takes 0.7514-0.8043x of main's
time and a checkpointed step 0.8119-0.8444x. This holds on B200 and
GB300 across all measured shapes. A forward under `no_grad` is
unchanged.
- **Cost:** peak memory includes the kept logits (25501 vs 8461 MiB at T
= 65031). That is why the mode is opt-in.

## What changes

- **`cake_backend.py`:**
- New eager entry points `chunked_lm_head_det_logprob_keep`,
`forward_logprob_keep` and `backward_logprob_keep`.
  - The kept form gets its own plan class, binding class and cache keys.
- New `kept_memory_report`. It adds `saved_logits_bytes` for kept plans
only. `memory_report` stays exactly as on main.
- **`cake_backend_opt_in.py`:**
  - `chunked_lm_head_det_logprob` accepts `memory_mode="keep_logits"`.
- `_resolve_memory_mode` is main's, and it still rejects `keep_logits`.
- The entry wraps main's fast-form test and call in a `try`/`except
ValueError`. The `except` sends `keep_logits` to the kept entry and
re-raises every other error.
- **`chunked_lm_head.py`:** docstring only.
- **README:** documents the mode, its memory use and its trade-offs.
- **`test_cake_lm_head_loss.py`:** new tests.

In total: 5 files, +1401/-25.

**Why the outputs are bitwise identical:** all logits forms on an
architecture share one mainloop. They produce BF16 from the same FP32
accumulator with the same RN conversion. `row_grad` on z is the
documented equivalent of the `gemm_logits_dz` arm.

## Semantics

- **When it keeps:** only when a backward can follow, meaning grad mode
is on and X or W requires grad.
- **When it falls back:** under `torch.no_grad`, `torch.inference_mode`,
with frozen inputs, or on the reference backend (at backend level), the
kept entry runs the default entry (the label-column forward).
- **Non-reentrant checkpoint:** the kept logits are saved with
`save_for_backward`, so a non-reentrant checkpoint drops them between
the forward and the backward. The checkpointed forward and the recompute
still allocate them, so the checkpointed step's peak includes them.
- **Retained graph:** a second backward through a retained graph
recomputes the logits.
- **Consumed views:** `backward_logprob_keep` marks the views it
consumed. A second call on them raises `ValueError` ("consumed by an
earlier backward").
- **Unsupported combinations:** at the public opt-in level,
`memory_mode="keep_logits"` with `num_valid_rows` raises `ValueError`,
and so does `keep_logits` with `backend="reference"`. The kept plan's
runner raises `NotImplementedError`; use the eager `*_keep` entry points
instead.
- **Cost on other opt-in calls:**
- A fast call runs one more traced line, the `try:`. On Python 3.11+
that is one NOP, with no added call.
  - A `"budget"` or `num_valid_rows` call adds one string comparison.
  - The backend default path adds nothing.

## Tests

Environment: B200 (sm_100a), GB300 (sm_103a), Python 3.12.15.

The table covers `test_cake_lm_head_loss.py`. Neither side has any
failures.

| platform | this PR | main | new tests run on main |
|---|---|---|---|
| CPU | 259 passed / 119 skipped | 257 passed / 117 skipped | 2 fail, 2
skip (device-only) |
| B200 | 376 passed / 2 skipped | 372 passed / 2 skipped | 4 fail |
| GB300 | 377 passed / 1 skipped | 373 passed / 1 skipped | 4 fail |

- The new tests fail on main because main has no keep entry points.
- The package's other test files give the same counts on both sides,
with no failures.
- pre-commit is clean on the head (all hooks pass, no changes).

The new tests cover:
- bitwise logp/dX/dW of the kept path against the default path,
including each input trainable alone
- the kept backward running no logits GEMM and one `row_grad` per chunk
- tensor lifetimes
- the error on reusing consumed views (`fr.logits`, tuple and list)
- that the default memory report has no `saved_logits_bytes` key

## Performance

**Method:**
- Paired, interleaved A/B of main and this PR in one process, on
exclusive nodes.
- A second main arm serves as an A/A control.
- 6 interleaved passes on B200 and 5 on GB300.
- A row counts as changed only if its 95% CI lies outside the A/A band.
- Shapes: H = 6144, V = 154880, chunk 4096.

**Results:**
- logp/dX/dW are bitwise equal to main on all 5 timed shapes on both
GPUs.
- `keep_logits` vs main: 20 rows faster, 10 equal, 0 slower on each GPU.
- The table shows calls after an idle gap equal to main's back-to-back
median. Every row was also timed with a fixed 2 ms gap before each call,
which gives the same verdict on every row. The summary ranges above
cover both.

| T | timed call | B200 main / keep (ms) | B200 keep/main [CI95] | GB300
main / keep (ms) | GB300 keep/main [CI95] | verdict |
|---|---|---|---|---|---|---|
| 2048 | step | 10.632 / 8.454 | 0.7977 [0.7887, 0.8056] | 8.803 / 7.063
| 0.8043 [0.7967, 0.8122] | faster |
| 2048 | checkpointed step | 13.419 / 11.227 | 0.8366 [0.8344, 0.8378] |
11.200 / 9.465 | 0.8444 [0.8433, 0.8510] | faster |
| 2048 | forward under no_grad | 2.594 / 2.599 | 1.0026 [0.9974, 1.0051]
| 2.285 / 2.330 | 1.0217 [1.0016, 1.0288] | equal |
| 8117 | step | 39.495 / 30.951 | 0.7834 [0.7684, 0.7870] | 31.350 /
24.800 | 0.7914 [0.7890, 0.7919] | faster |
| 8117 | checkpointed step | 49.082 / 40.891 | 0.8330 [0.8198, 0.8368] |
39.147 / 32.738 | 0.8357 [0.8348, 0.8377] | faster |
| 8117 | forward under no_grad | 9.642 / 9.642 | 0.9996 [0.9987, 1.0025]
| 7.736 / 7.737 | 0.9996 [0.9975, 1.0056] | equal |
| 16231 | step | 77.154 / 59.888 | 0.7745 [0.7643, 0.7947] | 61.771 /
47.734 | 0.7730 [0.7680, 0.7790] | faster |
| 16231 | checkpointed step | 96.449 / 79.933 | 0.8316 [0.8210, 0.8380]
| 78.028 / 63.722 | 0.8184 [0.8144, 0.8223] | faster |
| 16231 | forward under no_grad | 18.768 / 18.636 | 0.9977 [0.9858,
1.0125] | 14.729 / 14.727 | 0.9993 [0.9976, 1.0028] | equal |
| 32463 | step | 163.630 / 123.284 | 0.7514 [0.7319, 0.7875] | 128.803 /
98.528 | 0.7654 [0.7578, 0.7683] | faster |
| 32463 | checkpointed step | 205.070 / 167.185 | 0.8119 [0.8004,
0.8294] | 162.449 / 132.726 | 0.8170 [0.8128, 0.8185] | faster |
| 32463 | forward under no_grad | 37.216 / 36.910 | 0.9980 [0.9850,
1.0195] | 29.134 / 29.177 | 1.0006 [0.9996, 1.0020] | equal |
| 65031 | step | 338.281 / 264.081 | 0.7818 [0.7741, 0.7848] | 265.783 /
204.751 | 0.7707 [0.7682, 0.7715] | faster |
| 65031 | checkpointed step | 420.530 / 347.917 | 0.8288 [0.8212,
0.8346] | 333.066 / 273.272 | 0.8205 [0.8179, 0.8212] | faster |
| 65031 | forward under no_grad | 75.060 / 74.597 | 1.0025 [0.9834,
1.0165] | 59.605 / 59.682 | 1.0004 [0.9977, 1.0076] | equal |

**GB300 T = 2048 forward under `no_grad`:** the ratio's CI lies above 1
here, and also with the 2 ms gap. Under `no_grad`, the kept entry runs
the default entry, and the CI does not lie outside the A/A band, so the
rule counts the row as equal.

**Default path vs main:** equal on all 30 rows per GPU.
- Four single rows have a CI that excludes 1: 3 above and 1 below, out
of 60.
- The A/A control shows the same pattern: 4 of 30 rows on B200 and 2 of
30 on GB300 have a CI that excludes 1.
- The rule counts all of these rows as equal.

**Small calls, host time per call:** T = 1, 32 and 128; forward and
step; both call orders. The default path is equal to main in every cell.
Its order-combined end-to-end shift lies within the A/A shift of the
same run.

| GPU | default vs main, verdicts per order (end-to-end / submit) |
default vs main, combined end-to-end | A/A, combined end-to-end |
|---|---|---|---|
| B200 | equal 12/12 / equal 12/12 | +0.56 us [-2.41, +3.52] | -1.17 us
[-4.44, +2.10] |
| GB300 | equal 12/12 / equal 12/12 | +0.70 us [-0.18, +1.57] | +0.88 us
[+0.34, +1.42] |

**Small calls with `keep_logits`:** end-to-end time per call, keep minus
main, both call orders combined.

| T | timed call | B200 (us) [CI95] | GB300 (us) [CI95] |
|---|---|---|---|
| 1 | step | -375.03 [-377.20, -372.85] | -420.82 [-423.00, -418.65] |
| 32 | step | -348.82 [-353.76, -343.87] | -302.40 [-305.98, -298.82] |
| 128 | step | -404.89 [-411.88, -397.89] | -305.44 [-307.91, -302.98] |
| 1 | forward, grad on, no backward | +1.50 [-3.30, +6.30] | +10.88
[+9.86, +11.91] |
| 32 | forward, grad on, no backward | -1.96 [-3.06, -0.86] | -13.00
[-13.91, -12.08] |
| 128 | forward, grad on, no backward | -2.43 [-4.26, -0.60] | -7.21
[-8.83, -5.59] |

## Memory

Peak memory, in MiB above inputs. The values are identical in both arm
orders and on both GPUs.

| case | main | keep_logits |
|---|---|---|
| T = 65031, step and checkpointed-step peak | 8461 | 25501 |
| T = 65031, held after the checkpointed forward | 0 | 0 |
| T = 16231, peak | 7373 | 10718 |
| forward under no_grad, peak | equal | equal |

The kept logits are outside the chunk memory bound: they grow with T. A
non-reentrant checkpoint holds nothing after the forward. Its peak still
includes the kept logits, because the checkpointed forward and the
recompute allocate them.

## Trade-offs

- **Forward with grad on and no backward:** if a keep call has a
trainable input but its backward never runs, it still pays for the
full-logits forward. These numbers are per call with both call orders
combined, across three timing runs per GPU (the run above and two runs
of an earlier revision of this branch):
  - at T = 1, +0.4 to +1.6 us on B200 and +9.6 to +13.1 us on GB300
- at T = 32 and 128, -3.3 to +1.2 us on B200, and 5.4 to 13.0 us faster
on GB300
- **Memory held:** such a call holds the kept logits (2 * T_v * V bytes)
until its graph is freed.
- **Peak memory:** the peak includes the kept logits even under a
non-reentrant checkpoint (25501 vs 8461 MiB at T = 65031).
- **Unsupported combinations:** `keep_logits` does not support
`num_valid_rows` or the reference backend; both raise `ValueError`.

## Base and tested commits

- **Base:** the branch is one commit on main `98de6406`. Main has moved
since, but none of the later commits touch the files this PR changes,
and the branch merges cleanly.
- **Head:** `2bdb8766`. CPU tests and pre-commit ran on the head.
- **GPU timing and traces:** these ran on two earlier commits of this
branch. Neither differs from the head in executable code:
- **B200 timing and B200 line/call trace:** `30259247`. It differs from
the head by ruff-format whitespace and line wraps in 2 files, and by one
README number.
- **GB300 timing, GB300 line/call trace, and the B200 and GB300 test
runs:** `7e4c2fed`. It differs from the head only by one README number:
the GB300 figure "11.9" us was updated to "13.0" us.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added an opt-in `keep_logits` mode for log-probability computation. It
retains logits for the first backward pass, avoiding recomputation while
using additional memory.
* The mode applies when gradient recording is enabled and at least one
input requires gradients; later backward passes on a retained graph
recompute logits.
  * Results remain bitwise unchanged compared with the default mode.
* **Documentation**
* Clarified mode availability, memory use, and behavior when backward
computation is not applicable.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [cd0ae36](https://github.com/flashinfer-ai/flashinfer/commit/cd0ae364ef07560b1fa09df2d9a35777d7c1a73b)

- **作者**: eigen
- **时间**: 2026-11-01T13:50:07Z
- **提交信息**: fix(cake_rmsnorm_det): with grad, dw reproducibility per SM count; compensated backward below the measured SM counts (#8195)

### [7ec785b](https://github.com/flashinfer-ai/flashinfer/commit/7ec785bbf6cb8bae12eb1a038253eb753104e80f)

- **作者**: eigen
- **时间**: 2026-11-01T13:49:05Z
- **提交信息**: fix(cake_gdn): keep BF16 out of the SM107 Cake CP auto band and fail closed on long-sequence FP32-state rows (#8196)

## 📌 Description

On SM107a (R200, CC 10.7), `chunk_gated_delta_rule(...,
backend="cake_gdn", use_cp="auto")` sent BF16 I/O calls into the
automatic Cake CP band. #6323 added that band and qualified it with FP16
I/O only. With BF16 I/O, the SM107 CP program adds token-serial BF16
state-repair recurrences. As a result, calls in the band took 51–433 ms
on R200, while the default route takes 0.07–0.24 ms on the same rows.

Changes in `flashinfer/gdn_prefill.py`. They apply only to
`use_cp="auto"` on SM107a; `use_cp=False` and `use_cp=True` are
unchanged.

1. **CP auto band is FP16-only on SM107a**
(`_CAKE_GDN_CP_SM107A_IO_DTYPES`). BF16 calls no longer enter the band.
2. **Fail closed on two long-sequence bands.** The rule covers BF16 I/O
with FP32 `initial_state` and `output_final_state=True`. In the bands
below, `backend="cake_gdn"` raises `CakeGDNUnsupportedError` instead of
serving a slower kernel. Callers use the default backend there.
- Band A: longest sequence >= 8192 tokens and `num_seqs * num_heads` <=
32.
- Band B: longest sequence >= 4096 tokens and `num_seqs * num_heads` <=
8.

The longest sequence comes from the `max_seqlen` hint or
`cu_seqlens_cpu`. Otherwise it is ceil(total / num_seqs), computed by
the existing `_cake_gdn_cp_band_max_seqlen`.
3. **Tests and docs.** CPU dispatch tests were added at the end of the
SM107 band tests in `tests/gdn/test_cake_gdn_cp_backend.py`. They cover
the band rule, FP16 still entering CP, BF16 skipping CP, the fail-closed
bands, and shapes that stay on Cake. One paragraph was added to
`docs/api/gdn_prefill.rst`.

### Performance

**Setup**
- Hardware: R200 (CC 10.7, 212 SMs, driver 620.43, SM clock 2400–2424
MHz).
- Software: CUDA 13.4 container, torch 2.14.1+cu130.
- Before: main `be8cf032`. After: this PR's head, on main `3b6e31e5`.
- Workloads: Qwen3-Next / Qwen3.5 GDN prefill with BF16 I/O, FP32
initial and final state, and head dim 128.
- Six head geometries (HQ / HV): G1 8/16, G2 4/8, G3 2/4, G4 8/32, G5
4/16, G6 2/8.
- Eleven sequence patterns per geometry: 1x16384, 1x4096, 2x8192,
4x2048, 8x1024, 16x512, 32x512, 64x256, mixed16, 1x2048, 4x512. That
gives 66 rows.
- Timing: paired cold-L2 CUPTI GPU span, 3 ABBA groups, median, seeds 17
and 29.
- Correctness: output and final state are checked against an FP32
recurrence at atol = rtol = 1e-2, before and after timing.
- Baseline: `backend="auto"`. This is the CuTe-DSL route: CuTe CP on
long sequences and the Rubin chunked kernel otherwise. Speedup = auto
latency / cake_gdn latency.

**Summary (66 rows)**

| | Before (`be8cf032`) | After (this PR) |
|---|---|---|
| Served by cake_gdn | 66 | 52 |
| Faster than auto | 46 | 52 (both seeds) |
| In SM107 Cake CP band | 20, at 0.0003–0.0036x | 0 |
| Fail closed (`CakeGDNUnsupportedError`) | 0 | 14 |
| Speedup on winning rows, min / geomean / max | 1.031 / 1.316 / 5.11 |
seed 17: 1.0288 / 1.3738 / 5.1046<br>seed 29: 1.0290 / 1.3724 / 5.1292 |

The other 46 rows are unchanged: the after/before cake latency ratio is
0.994–1.009. There were 0 correctness failures after the change.

**The 20 rows that were in the CP band before**

Before, all 20 rows ran at 0.0003–0.0036x of auto. The table shows the
three per-row latencies that were recorded (seed 17).

| Pattern | Geometry | Before: cake_gdn µs | auto µs | After |
|---|---|---|---|---|
| 1x16384 | G1 | 432732.4 | 159.3 | fails closed (non-CP 0.34–0.98x) |
| 1x16384 | G2, G3, G4, G5, G6 | — | — | fails closed (non-CP
0.34–0.98x) |
| 2x8192 | G1, G2, G3, G5, G6 | — | — | fails closed (non-CP 0.34–0.98x)
|
| 1x4096 | G2, G3, G6 | — | — | fails closed (non-CP 0.34–0.98x) |
| 1x4096 | G1 | 103963.6 | 95.9 | Cake non-CP, 1.159x / 1.159x (seed 17
/ 29) |
| 1x4096 | G5 | — | — | Cake non-CP, 1.162x / 1.156x |
| 4x2048 | G2 | 51527.2 | 95.0 | Cake non-CP, 2.10–2.14x (range over
G2/G3/G6) |
| 4x2048 | G3, G6 | — | — | Cake non-CP, 2.10–2.14x (range over
G2/G3/G6) |
| 8x1024 | G3 | — | — | Cake non-CP, 3.658x / 3.662x |

## 🔍 Related Issues

- #6323: introduced the SM107 Cake CP band
- #6478: FP32-state prefill records
- #6754: SM107a prefill records
- Tracking: #6595

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

The pinned ruff 0.12.8 `format --check` and `check` pass on the two
changed Python files; the full hook set was not run.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/gdn/test_cake_gdn_cp_backend.py
tests/gdn/test_cake_gdn_prefill_gpu.py`

These were run on the same R200 node at the PR head. Every leg had 0
failures.

| Leg | File(s) | Passed | Skipped |
|---|---|---|---|
| CPU | the 3 `tests/gdn/test_cake_gdn_*` files | 455 | 213 |
| GPU | `test_cake_gdn_cp_backend.py` | 455 | 32 (SM100a/SM103a-only) |
| GPU | `test_cake_gdn_decode_gpu.py` | 92 | 2 |
| GPU | `test_cake_gdn_prefill_gpu.py` | 86 | 1 |
| 2 GPUs | 3 mixed-device cases | 3 | 0 |

The 20 new `test_sm107_*` cases pass.

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

- The fail-closed rule works per shape band, not per head geometry.
Every geometry also has rows where cake_gdn beats auto.
- The SM107 token-serial BF16 repair path in the CP program is
unchanged. BF16 calls with `use_cp="auto"` no longer reach it.
- This PR does not change any kernel source.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Behavior Changes**
* On SM107, automatic Cake GDN routing now reports an unsupported
configuration for BF16 inputs with FP32 initial and final state when
sequence length and parallelism fall within specified limits. Other
configurations, including explicit non-context-parallel routing,
continue to use the non-parallel backend.
* **Documentation**
* Updated the Cake GDN documentation to describe these unsupported
configurations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [19b209f](https://github.com/flashinfer-ai/flashinfer/commit/19b209f069765688c3d4db2e3101dc13069a4508)

- **作者**: eigen
- **时间**: 2026-11-01T13:48:22Z
- **提交信息**: perf(cake_gdn): with grad, split two-stream adjoint scan for sm_107a HV=3H; lighter host path (#8194)

### [79f0637](https://github.com/flashinfer-ai/flashinfer/commit/79f0637a4a98092d402bf05db281a78eaf8f59c2)

- **作者**: eigen
- **时间**: 2026-11-01T12:15:37Z
- **提交信息**: perf(cake_mega_moe_v3): faster TP4, TP8, TP4 EP4 and TP8 EP8 rank programs at 4096 tokens on sm_103a (#8192)

### [e302d38](https://github.com/flashinfer-ai/flashinfer/commit/e302d382bb6512bbc8a1fbf11f075811e953a55c)

- **作者**: eigen
- **时间**: 2026-11-01T11:42:35Z
- **提交信息**: feat(cake_dense_projection_gemm): non-deterministic split-K and stream-K autograd GEMMs (#8190)

### [3b6e31e](https://github.com/flashinfer-ai/flashinfer/commit/3b6e31e5565a2e539ade639507a5d363588fd0b7)

- **作者**: eigen
- **时间**: 2026-11-01T11:11:31Z
- **提交信息**: perf(cake_sampling): H100 L2-prefetch twins for top-k/top-p sampling at vocab 262144, batch 128 (#8182)

## Summary

`cake_sampling` is a fused sampler: top-k, then top-p over the
renormalized top-k, then a Philox sample, over contiguous float32
probability rows. At FlashInfer main `d29e16ae`, which holds the
previous Cake version from #7989, the kernel is made of 136 stage-1
builds and 15 stage-2/3 kernels, for 151 kernel symbols. This PR adds
two stage-1 builds. They are L2-prefetch twins of two cluster-1
speculative-sample streams: `kernel_cake_radix_topk_c1_e16s_sp_lb_pf`
and `kernel_cake_radix_topk_c1_e32s_sp_pf`. With them the family has 138
builds and 153 symbols. The PR also regenerates the kernel sources.

FlashInfer launches the twins only on H100 (132 SMs), and only at vocab
262144, batch 128 and top-k <= 64. In the shape list this covers 4 rows:
top-k 10 and 50, each in eager and CUDA graph. These rows run 1.034x to
1.038x faster than the previous Cake version. Every other row on every
GPU keeps the previous plan and runs the same SASS as the previous
version, so its "vs previous" ratio is run-to-run noise.

| GPU | arch | rows | rows changed by this PR | vs previous Cake,
changed rows | vs previous Cake, other rows | vs FlashInfer sampling,
all rows |
|---|---|---:|---:|---|---|---|
| H100 | sm_90a | 192 | 4 | 1.034x-1.038x | 0.997x-1.001x |
2.406x-9.686x |
| GB300 | sm_103a | 192 | 0 | - | 0.976x-1.017x | 2.322x-11.248x |
| R200 | sm_107a | 192 | 0 | - | 0.999x-1.002x | 2.110x-7.466x |
| RTX PRO 6000 | sm_120a | 144 | 0 | - | 0.999x-1.001x | 2.006x-6.047x |

Rows below 1.000x against the previous version stay in the tables:
- GB300: 6 rows. The lowest is top-k 1000, vocab 32768, batch 4, eager,
at 0.976x (16.336 µs vs 16.664 µs).
- H100: 4 rows, lowest 0.997x.
- R200: 1 row at 0.999x.
- RTX PRO 6000: 3 rows, lowest 0.999x.

None of these rows is one the twins change. All of them run the same
SASS as the previous version.

## Speedup

- **previous Cake**: `cake_sampling` at FlashInfer main `d29e16ae`
(#7989).
- **FlashInfer sampling**:
`flashinfer.sampling.top_k_top_p_sampling_from_probs(probs, k, top_p,
filter_apply_order="top_k_first", deterministic=True, seed, offset)` at
the same commit.
- Unmarked values use its default dispatch. That is the radix
composition when k <= 256, vocab >= 65536 and k < vocab, and otherwise
full-vocab `top_k_renorm_probs` followed by `top_p_sampling_from_probs`.
- `†` marks rows where the other composition, forced, was faster. Each
row shows the faster of the two.
- Why this is the comparison: it is FlashInfer's own deterministic
implementation of the same math with the same Philox seed and offset.
The `joint` order computes different math, and the non-deterministic
modes are not deterministic. Samplers outside FlashInfer were not
measured.
- **Latency**: GPU time of one sampling call, including all of its
kernels, with a cold L2. It is measured both as an eager call and as a
CUDA-graph replay. Each value is the median over 12 rounds.
- **Speedup**: baseline / this PR, taken as the median of the 12 paired
per-round ratios. It can therefore differ from the quotient of the
displayed latencies.

**H100 (sm_90a, 132 SMs)**

NVIDIA H100 80GB HBM3, sm_90a (compute capability 9.0), 132 SMs. CUDA
13.4 (nvcc V13.4.92) user space on driver 535.216.03 (forward
compatibility), PyTorch 2.14.1+cu130. This PR changes the top-k 10 and
50 rows at vocab 262144, batch 128.

| top-k | vocab | batch | eager: previous Cake µs | FlashInfer sampling
µs | this PR µs | vs previous | vs FlashInfer | graph: previous Cake µs
| FlashInfer sampling µs | this PR µs | vs previous | vs FlashInfer |
|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 10 | 32768 | 1 | 7.359 | 32.191 | 7.359 | 1.000x | 4.379x | 7.360 |
33.727 | 7.360 | 1.000x | 4.568x |
| 10 | 32768 | 2 | 7.456 | 35.008 | 7.456 | 1.000x | 4.693x | 7.488 |
36.648 | 7.488 | 1.000x | 4.894x |
| 10 | 32768 | 4 | 7.584 | 35.711 | 7.584 | 1.000x | 4.709x | 7.616 |
37.215 | 7.616 | 1.000x | 4.899x |
| 10 | 32768 | 8 | 7.808 | 39.792 | 7.808 | 1.000x | 5.098x | 7.839 |
41.407 | 7.839 | 1.000x | 5.286x |
| 10 | 32768 | 16 | 8.384 | 40.768 | 8.384 | 1.000x | 4.859x | 8.416 |
42.431 | 8.416 | 1.000x | 5.044x |
| 10 | 32768 | 32 | 10.048 | 45.039 | 10.048 | 1.000x | 4.481x | 10.080
| 45.839† | 10.080 | 1.000x | 4.534x |
| 10 | 32768 | 64 | 11.727 | 46.016 | 11.711 | 1.000x | 3.932x | 11.744
| 46.975† | 11.744 | 1.000x | 4.010x |
| 10 | 32768 | 128 | 15.168 | 51.592 | 15.200 | 1.000x | 3.394x | 15.104
| 50.560† | 15.104 | 1.000x | 3.347x |
| 10 | 128256 | 1 | 8.736 | 63.807† | 8.736 | 1.000x | 7.295x | 8.768 |
64.975† | 8.768 | 1.000x | 7.387x |
| 10 | 128256 | 2 | 8.992 | 68.863† | 8.992 | 1.000x | 7.653x | 9.024 |
65.135 | 9.024 | 1.000x | 7.228x |
| 10 | 128256 | 4 | 9.552 | 86.623† | 9.552 | 1.000x | 9.058x | 9.568 |
64.895 | 9.568 | 1.000x | 6.782x |
| 10 | 128256 | 8 | 10.336 | 87.055† | 10.352 | 1.000x | 8.403x | 10.383
| 65.463 | 10.368 | 1.000x | 6.308x |
| 10 | 128256 | 16 | 11.952 | 88.183† | 11.936 | 1.000x | 7.370x |
11.968 | 67.047 | 11.968 | 1.000x | 5.607x |
| 10 | 128256 | 32 | 15.712 | 93.535† | 15.711 | 1.000x | 5.959x |
15.743 | 71.711 | 15.743 | 1.000x | 4.567x |
| 10 | 128256 | 64 | 22.559 | 105.375 | 22.559 | 1.000x | 4.671x |
22.528 | 81.455 | 22.528 | 1.000x | 3.618x |
| 10 | 128256 | 128 | 36.383 | 106.399 | 36.368 | 1.000x | 2.924x |
36.367 | 99.455 | 36.375 | 1.000x | 2.735x |
| 10 | 151936 | 1 | 9.248 | 70.062† | 9.248 | 1.000x | 7.583x | 9.280 |
69.375 | 9.280 | 1.000x | 7.486x |
| 10 | 151936 | 2 | 9.600 | 82.927† | 9.600 | 1.000x | 8.631x | 9.632 |
69.639 | 9.648 | 1.000x | 7.213x |
| 10 | 151936 | 4 | 10.032 | 84.190† | 10.048 | 1.000x | 8.372x | 10.088
| 69.391 | 10.080 | 1.000x | 6.881x |
| 10 | 151936 | 8 | 10.816 | 86.854† | 10.800 | 1.000x | 8.048x | 10.816
| 70.239 | 10.816 | 1.000x | 6.489x |
| 10 | 151936 | 16 | 12.768 | 89.727† | 12.768 | 1.000x | 7.029x |
12.768 | 72.063 | 12.768 | 1.000x | 5.635x |
| 10 | 151936 | 32 | 17.504 | 102.623 | 17.504 | 1.000x | 5.858x |
17.535 | 78.239 | 17.520 | 1.000x | 4.464x |
| 10 | 151936 | 64 | 25.632 | 105.151 | 25.632 | 1.000x | 4.107x |
25.599 | 93.350 | 25.600 | 1.000x | 3.645x |
| 10 | 151936 | 128 | 41.247 | 115.199 | 41.247 | 1.000x | 2.797x |
41.248 | 109.486 | 41.279 | 1.001x | 2.654x |
| 10 | 262144 | 1 | 10.144 | 77.071† | 10.144 | 1.000x | 7.589x | 10.160
| 70.831 | 10.175 | 1.000x | 6.968x |
| 10 | 262144 | 2 | 10.560 | 98.222† | 10.560 | 1.000x | 9.298x | 10.592
| 71.391 | 10.592 | 1.000x | 6.740x |
| 10 | 262144 | 4 | 11.296 | 103.374 | 11.296 | 1.000x | 9.147x | 11.328
| 71.311 | 11.328 | 1.000x | 6.301x |
| 10 | 262144 | 8 | 12.496 | 98.839 | 12.511 | 1.000x | 7.900x | 12.512
| 71.711 | 12.511 | 1.000x | 5.743x |
| 10 | 262144 | 16 | 16.000 | 98.398 | 16.000 | 1.000x | 6.150x | 16.000
| 75.472 | 16.000 | 1.000x | 4.715x |
| 10 | 262144 | 32 | 24.335 | 131.662 | 24.351 | 1.000x | 5.438x |
24.352 | 126.974 | 24.360 | 1.000x | 5.213x |
| 10 | 262144 | 64 | 37.535 | 133.343 | 37.536 | 1.000x | 3.550x |
37.568 | 127.934 | 37.544 | 1.000x | 3.405x |
| 10 | 262144 | 128 | 62.671 | 156.622 | 60.567 | 1.034x | 2.592x |
62.575 | 151.022 | 60.688 | 1.034x | 2.489x |
| 50 | 32768 | 1 | 8.992 | 34.703 | 8.992 | 1.000x | 3.858x | 9.024 |
36.239 | 9.024 | 1.000x | 4.014x |
| 50 | 32768 | 2 | 9.056 | 35.600 | 9.056 | 1.000x | 3.928x | 9.088 |
37.103 | 9.088 | 1.000x | 4.090x |
| 50 | 32768 | 4 | 9.184 | 36.272 | 9.184 | 1.000x | 3.946x | 9.216 |
37.791 | 9.216 | 1.000x | 4.102x |
| 50 | 32768 | 8 | 9.408 | 41.087 | 9.408 | 1.000x | 4.371x | 9.408 |
42.623 | 9.408 | 1.000x | 4.527x |
| 50 | 32768 | 16 | 10.031 | 41.616 | 10.032 | 1.000x | 4.155x | 10.048
| 43.200 | 10.048 | 1.000x | 4.298x |
| 50 | 32768 | 32 | 10.880 | 44.032 | 10.864 | 1.000x | 4.060x | 10.912
| 45.648 | 10.912 | 1.000x | 4.177x |
| 50 | 32768 | 64 | 12.112 | 45.040 | 12.127 | 1.000x | 3.719x | 12.128
| 46.864 | 12.144 | 1.000x | 3.855x |
| 50 | 32768 | 128 | 15.552 | 53.024 | 15.552 | 1.000x | 3.409x | 15.488
| 54.479† | 15.488 | 1.000x | 3.512x |
| 50 | 128256 | 1 | 9.664 | 93.391† | 9.632 | 1.000x | 9.686x | 9.664 |
64.959 | 9.664 | 1.000x | 6.722x |
| 50 | 128256 | 2 | 9.984 | 93.711† | 9.984 | 1.000x | 9.370x | 10.016 |
65.296 | 10.015 | 1.000x | 6.522x |
| 50 | 128256 | 4 | 10.432 | 93.823† | 10.432 | 1.000x | 8.994x | 10.464
| 65.456 | 10.464 | 1.000x | 6.270x |
| 50 | 128256 | 8 | 11.200 | 94.815† | 11.200 | 1.000x | 8.457x | 11.216
| 66.991 | 11.200 | 1.000x | 5.959x |
| 50 | 128256 | 16 | 13.280 | 95.647† | 13.295 | 1.000x | 7.197x |
13.312 | 67.663 | 13.312 | 1.000x | 5.078x |
| 50 | 128256 | 32 | 16.831 | 100.911 | 16.831 | 1.000x | 5.984x |
16.832 | 75.447 | 16.832 | 1.000x | 4.482x |
| 50 | 128256 | 64 | 23.680 | 106.222 | 23.679 | 1.000x | 4.486x |
23.648 | 85.439 | 23.679 | 1.000x | 3.610x |
| 50 | 128256 | 128 | 36.896 | 111.351 | 36.911 | 1.000x | 3.014x |
36.896 | 103.799 | 36.895 | 1.000x | 2.810x |
| 50 | 151936 | 1 | 10.240 | 75.519† | 10.240 | 1.000x | 7.374x | 10.272
| 69.600 | 10.271 | 1.000x | 6.772x |
| 50 | 151936 | 2 | 10.656 | 81.631† | 10.655 | 1.000x | 7.667x | 10.688
| 70.240 | 10.687 | 1.000x | 6.578x |
| 50 | 151936 | 4 | 11.072 | 82.687† | 11.072 | 1.000x | 7.464x | 11.104
| 70.736 | 11.104 | 1.000x | 6.358x |
| 50 | 151936 | 8 | 11.872 | 86.607† | 11.873 | 1.000x | 7.297x | 11.904
| 72.272 | 11.904 | 1.000x | 6.081x |
| 50 | 151936 | 16 | 14.176 | 99.391† | 14.176 | 1.000x | 7.010x |
14.176 | 75.487 | 14.176 | 1.000x | 5.320x |
| 50 | 151936 | 32 | 19.136 | 100.910 | 19.136 | 1.000x | 5.274x |
19.136 | 81.856 | 19.151 | 1.000x | 4.277x |
| 50 | 151936 | 64 | 27.104 | 106.767 | 27.104 | 1.000x | 3.937x |
27.103 | 97.247 | 27.104 | 1.000x | 3.590x |
| 50 | 151936 | 128 | 41.968 | 159.294 | 41.975 | 1.000x | 3.797x |
42.016 | 153.926 | 42.031 | 0.999x | 3.663x |
| 50 | 262144 | 1 | 10.864 | 86.719† | 10.864 | 1.000x | 7.984x | 10.880
| 70.719 | 10.880 | 1.000x | 6.495x |
| 50 | 262144 | 2 | 11.280 | 99.359 | 11.280 | 1.000x | 8.820x | 11.296
| 71.712 | 11.296 | 1.000x | 6.349x |
| 50 | 262144 | 4 | 11.839 | 97.071 | 11.808 | 1.000x | 8.199x | 11.840
| 72.175 | 11.840 | 1.000x | 6.081x |
| 50 | 262144 | 8 | 13.728 | 100.719 | 13.728 | 1.000x | 7.337x | 13.760
| 73.200 | 13.759 | 1.000x | 5.324x |
| 50 | 262144 | 16 | 17.600 | 101.343 | 17.600 | 1.000x | 5.758x |
17.616 | 78.463 | 17.632 | 1.000x | 4.454x |
| 50 | 262144 | 32 | 25.408 | 135.550 | 25.407 | 1.000x | 5.364x |
25.439 | 130.302 | 25.439 | 1.000x | 5.125x |
| 50 | 262144 | 64 | 38.800 | 137.695 | 38.815 | 1.000x | 3.547x |
38.831 | 132.118 | 38.847 | 1.000x | 3.398x |
| 50 | 262144 | 128 | 62.880 | 160.398 | 60.815 | 1.038x | 2.640x |
62.991 | 155.102 | 60.703 | 1.038x | 2.548x |
| 1000 | 32768 | 1 | 14.624 | 35.136 | 14.624 | 1.000x | 2.406x | 14.559
| 36.672 | 14.575 | 1.000x | 2.522x |
| 1000 | 32768 | 2 | 14.815 | 36.032 | 14.800 | 1.000x | 2.432x | 14.752
| 37.632 | 14.752 | 1.000x | 2.555x |
| 1000 | 32768 | 4 | 14.879 | 36.096 | 14.879 | 1.000x | 2.430x | 14.800
| 37.663 | 14.800 | 1.000x | 2.551x |
| 1000 | 32768 | 8 | 14.960 | 36.352 | 14.976 | 1.000x | 2.435x | 14.880
| 37.935 | 14.880 | 1.000x | 2.548x |
| 1000 | 32768 | 16 | 15.712 | 38.239 | 15.712 | 1.000x | 2.436x |
15.648 | 39.887 | 15.648 | 1.000x | 2.545x |
| 1000 | 32768 | 32 | 17.248 | 46.464 | 17.264 | 1.000x | 2.693x |
17.152 | 48.160 | 17.183 | 1.000x | 2.802x |
| 1000 | 32768 | 64 | 18.784 | 48.015 | 18.767 | 1.000x | 2.557x |
18.655 | 49.663 | 18.656 | 1.000x | 2.666x |
| 1000 | 32768 | 128 | 20.895 | 56.416 | 20.880 | 1.001x | 2.701x |
20.928 | 58.175 | 20.912 | 1.000x | 2.784x |
| 1000 | 128256 | 1 | 14.832 | 67.806 | 14.832 | 1.000x | 4.568x |
14.880 | 68.863 | 14.864 | 1.000x | 4.633x |
| 1000 | 128256 | 2 | 15.312 | 71.967 | 15.616 | 1.000x | 4.603x |
15.328 | 70.879† | 15.328 | 1.000x | 4.615x |
| 1000 | 128256 | 4 | 15.904 | 72.463 | 15.712 | 1.000x | 4.602x |
15.824 | 71.663† | 15.808 | 0.999x | 4.524x |
| 1000 | 128256 | 8 | 16.576 | 74.895 | 16.608 | 1.000x | 4.511x |
16.688 | 73.935† | 16.624 | 1.000x | 4.436x |
| 1000 | 128256 | 16 | 20.239 | 96.031† | 20.240 | 1.000x | 4.752x |
20.176 | 78.400† | 20.144 | 1.000x | 3.894x |
| 1000 | 128256 | 32 | 24.192 | 103.391† | 24.160 | 1.001x | 4.279x |
24.128 | 95.295† | 24.096 | 1.000x | 3.952x |
| 1000 | 128256 | 64 | 30.816 | 111.407† | 30.775 | 1.000x | 3.626x |
30.944 | 105.319† | 30.880 | 1.000x | 3.410x |
| 1000 | 128256 | 128 | 46.416 | 130.207† | 46.303 | 1.000x | 2.800x |
46.400 | 124.143† | 46.383 | 1.000x | 2.674x |
| 1000 | 151936 | 1 | 16.128 | 76.303 | 16.136 | 1.000x | 4.725x |
16.207 | 75.167† | 16.144 | 1.000x | 4.643x |
| 1000 | 151936 | 2 | 16.431 | 80.831 | 16.592 | 1.000x | 4.867x |
16.399 | 75.279† | 16.528 | 1.000x | 4.548x |
| 1000 | 151936 | 4 | 16.816 | 97.855 | 16.816 | 1.000x | 5.815x |
16.832 | 76.431† | 16.848 | 1.000x | 4.537x |
| 1000 | 151936 | 8 | 17.568 | 99.263 | 17.599 | 1.000x | 5.631x |
17.599 | 78.511† | 17.599 | 1.000x | 4.460x |
| 1000 | 151936 | 16 | 21.584 | 97.071† | 21.568 | 1.000x | 4.501x |
21.439 | 83.199† | 21.424 | 1.000x | 3.882x |
| 1000 | 151936 | 32 | 26.944 | 102.351† | 26.944 | 1.000x | 3.799x |
26.880 | 93.390† | 26.880 | 1.000x | 3.476x |
| 1000 | 151936 | 64 | 34.224 | 122.638† | 34.272 | 0.997x | 3.563x |
34.288 | 116.447† | 34.272 | 1.000x | 3.396x |
| 1000 | 151936 | 128 | 51.712 | 138.815† | 51.712 | 1.001x | 2.687x |
51.615 | 132.366† | 51.568 | 0.999x | 2.569x |
| 1000 | 262144 | 1 | 16.560 | 93.007 | 16.544 | 1.000x | 5.625x |
16.319 | 75.599† | 16.303 | 1.000x | 4.633x |
| 1000 | 262144 | 2 | 17.024 | 98.943† | 17.024 | 1.000x | 5.678x |
17.087 | 75.935† | 17.072 | 1.000x | 4.443x |
| 1000 | 262144 | 4 | 17.600 | 97.887† | 17.631 | 1.000x | 5.572x |
17.648 | 77.279† | 17.696 | 1.000x | 4.367x |
| 1000 | 262144 | 8 | 19.104 | 105.422† | 19.088 | 1.000x | 5.542x |
19.040 | 79.119† | 19.055 | 1.000x | 4.158x |
| 1000 | 262144 | 16 | 24.527 | 108.942† | 24.544 | 1.000x | 4.447x |
24.448 | 86.015† | 24.448 | 1.000x | 3.517x |
| 1000 | 262144 | 32 | 36.256 | 147.486† | 36.288 | 1.000x | 4.052x |
36.288 | 141.886† | 36.288 | 1.000x | 3.906x |
| 1000 | 262144 | 64 | 46.208 | 158.462† | 46.207 | 1.001x | 3.422x |
46.272 | 152.270† | 46.208 | 1.000x | 3.292x |
| 1000 | 262144 | 128 | 71.775 | 182.110† | 71.647 | 1.000x | 2.536x |
71.519 | 175.805† | 71.583 | 1.000x | 2.456x |

**GB300 (sm_103a, 152 SMs)**

NVIDIA GB300, sm_103a (compute capability 10.3), 152 SMs. CUDA 13.4
(nvcc V13.4.92), driver 580.159.03, PyTorch 2.14.1+cu130.

| top-k | vocab | batch | eager: previous Cake µs | FlashInfer sampling
µs | this PR µs | vs previous | vs FlashInfer | graph: previous Cake µs
| FlashInfer sampling µs | this PR µs | vs previous | vs FlashInfer |
|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 10 | 32768 | 1 | 7.008 | 45.047 | 7.008 | 1.000x | 6.413x | 7.168 |
29.248 | 7.152 | 1.000x | 4.083x |
| 10 | 32768 | 2 | 7.104 | 46.975 | 7.104 | 1.000x | 6.592x | 7.360 |
31.600 | 7.360 | 1.000x | 4.301x |
| 10 | 32768 | 4 | 7.168 | 45.336 | 7.136 | 1.000x | 6.327x | 7.424 |
32.288 | 7.424 | 1.000x | 4.349x |
| 10 | 32768 | 8 | 7.296 | 51.472 | 7.296 | 1.000x | 6.972x | 7.520 |
35.744 | 7.520 | 1.000x | 4.752x |
| 10 | 32768 | 16 | 7.520 | 50.736 | 7.520 | 1.000x | 6.736x | 7.776 |
35.888 | 7.776 | 1.000x | 4.613x |
| 10 | 32768 | 32 | 8.096 | 55.696 | 8.096 | 1.000x | 6.879x | 8.384 |
40.256 | 8.368 | 1.000x | 4.813x |
| 10 | 32768 | 64 | 9.728 | 55.128 | 9.728 | 1.000x | 5.676x | 9.920 |
41.008 | 9.920 | 1.000x | 4.134x |
| 10 | 32768 | 128 | 10.752 | 56.240 | 10.752 | 1.000x | 5.238x | 10.944
| 41.920† | 10.944 | 1.000x | 3.830x |
| 10 | 128256 | 1 | 7.984 | 58.832† | 7.968 | 1.000x | 7.377x | 8.096 |
55.928† | 8.096 | 1.000x | 6.904x |
| 10 | 128256 | 2 | 8.064 | 63.023† | 8.064 | 1.000x | 7.803x | 8.288 |
60.208 | 8.288 | 1.000x | 7.284x |
| 10 | 128256 | 4 | 8.256 | 65.359† | 8.256 | 1.000x | 7.928x | 8.512 |
58.928 | 8.512 | 1.000x | 6.923x |
| 10 | 128256 | 8 | 8.608 | 72.976† | 8.608 | 1.000x | 8.478x | 8.864 |
59.472 | 8.864 | 1.000x | 6.695x |
| 10 | 128256 | 16 | 10.400 | 84.896† | 10.400 | 1.000x | 8.162x |
10.688 | 60.816 | 10.688 | 1.000x | 5.692x |
| 10 | 128256 | 32 | 11.568 | 85.584† | 11.552 | 1.000x | 7.389x |
11.840 | 61.728 | 11.840 | 1.000x | 5.222x |
| 10 | 128256 | 64 | 14.688 | 126.448† | 14.720 | 0.999x | 8.600x |
14.976 | 62.976 | 14.976 | 1.000x | 4.205x |
| 10 | 128256 | 128 | 20.736 | 172.911† | 20.720 | 1.000x | 8.341x |
20.975 | 67.023 | 20.976 | 1.000x | 3.193x |
| 10 | 151936 | 1 | 8.864 | 64.528† | 8.864 | 1.000x | 7.058x | 9.056 |
62.127† | 9.040 | 1.000x | 6.890x |
| 10 | 151936 | 2 | 8.864 | 77.888† | 8.864 | 1.000x | 8.767x | 9.088 |
65.216 | 9.088 | 1.000x | 7.181x |
| 10 | 151936 | 4 | 9.120 | 79.024† | 9.120 | 1.000x | 8.656x | 9.408 |
63.672 | 9.408 | 1.000x | 6.784x |
| 10 | 151936 | 8 | 9.568 | 79.159† | 9.568 | 1.000x | 8.288x | 9.824 |
64.240 | 9.824 | 1.000x | 6.547x |
| 10 | 151936 | 16 | 11.072 | 82.112† | 11.072 | 1.000x | 7.411x |
11.344 | 65.448 | 11.328 | 1.000x | 5.775x |
| 10 | 151936 | 32 | 12.184 | 89.328† | 12.176 | 1.000x | 7.340x |
12.448 | 68.864 | 12.448 | 1.000x | 5.532x |
| 10 | 151936 | 64 | 16.160 | 138.431† | 16.160 | 1.000x | 8.579x |
16.416 | 68.416 | 16.416 | 1.000x | 4.165x |
| 10 | 151936 | 128 | 24.288 | 200.392 | 24.288 | 1.000x | 8.251x |
24.544 | 74.535 | 24.512 | 1.000x | 3.037x |
| 10 | 262144 | 1 | 9.440 | 71.152† | 9.440 | 1.000x | 7.512x | 9.600 |
64.336 | 9.600 | 1.000x | 6.706x |
| 10 | 262144 | 2 | 9.536 | 101.104† | 9.536 | 1.000x | 10.604x | 9.696
| 65.856 | 9.728 | 1.000x | 6.768x |
| 10 | 262144 | 4 | 9.792 | 101.312† | 9.792 | 1.000x | 10.345x | 10.048
| 64.656 | 10.048 | 1.000x | 6.430x |
| 10 | 262144 | 8 | 10.496 | 105.360† | 10.496 | 1.000x | 10.028x |
10.752 | 66.080 | 10.752 | 1.000x | 6.146x |
| 10 | 262144 | 16 | 12.800 | 111.728† | 12.800 | 1.000x | 8.750x |
12.992 | 69.072 | 12.992 | 1.000x | 5.318x |
| 10 | 262144 | 32 | 14.800 | 157.600† | 14.800 | 1.000x | 10.654x |
15.072 | 112.384 | 15.040 | 1.000x | 7.465x |
| 10 | 262144 | 64 | 23.680 | 205.224 | 23.680 | 1.000x | 8.666x |
23.968 | 94.424 | 23.936 | 1.000x | 3.945x |
| 10 | 262144 | 128 | 35.424 | 198.416 | 35.456 | 1.000x | 5.596x |
35.648 | 114.575 | 35.648 | 0.999x | 3.214x |
| 50 | 32768 | 1 | 7.600 | 47.696 | 7.616 | 1.000x | 6.289x | 7.744 |
31.872 | 7.744 | 1.000x | 4.116x |
| 50 | 32768 | 2 | 7.680 | 47.736 | 7.680 | 1.000x | 6.203x | 7.936 |
32.416 | 7.936 | 1.000x | 4.087x |
| 50 | 32768 | 4 | 7.744 | 47.727 | 7.744 | 1.000x | 6.087x | 8.016 |
32.960 | 8.032 | 1.000x | 4.116x |
| 50 | 32768 | 8 | 7.968 | 51.168 | 7.968 | 1.000x | 6.422x | 8.192 |
37.152 | 8.192 | 1.000x | 4.539x |
| 50 | 32768 | 16 | 8.192 | 52.048 | 8.192 | 1.000x | 6.354x | 8.448 |
37.312 | 8.448 | 1.000x | 4.421x |
| 50 | 32768 | 32 | 8.736 | 53.936 | 8.736 | 1.000x | 6.172x | 8.960 |
41.279 | 8.960 | 1.000x | 4.600x |
| 50 | 32768 | 64 | 10.240 | 55.664 | 10.255 | 1.000x | 5.436x | 10.464
| 41.936 | 10.464 | 1.000x | 4.012x |
| 50 | 32768 | 128 | 11.296 | 55.464 | 11.296 | 1.000x | 4.910x | 11.520
| 43.008 | 11.520 | 1.000x | 3.735x |
| 50 | 128256 | 1 | 9.312 | 85.552† | 9.312 | 1.000x | 9.172x | 9.408 |
58.016 | 9.408 | 1.000x | 6.171x |
| 50 | 128256 | 2 | 9.440 | 85.856† | 9.440 | 1.000x | 9.095x | 9.664 |
60.495 | 9.680 | 1.000x | 6.257x |
| 50 | 128256 | 4 | 9.600 | 86.064† | 9.600 | 1.000x | 8.962x | 9.888 |
60.112 | 9.888 | 1.000x | 6.079x |
| 50 | 128256 | 8 | 10.032 | 86.688† | 10.032 | 1.000x | 8.638x | 10.288
| 61.520 | 10.287 | 1.000x | 5.982x |
| 50 | 128256 | 16 | 11.744 | 87.072† | 11.744 | 1.000x | 7.416x |
12.000 | 63.536 | 12.000 | 1.000x | 5.299x |
| 50 | 128256 | 32 | 13.024 | 87.600† | 13.024 | 1.000x | 6.722x |
13.312 | 64.592 | 13.312 | 1.000x | 4.848x |
| 50 | 128256 | 64 | 15.744 | 135.232† | 15.744 | 1.000x | 8.603x |
16.016 | 66.897 | 16.000 | 1.000x | 4.178x |
| 50 | 128256 | 128 | 21.536 | 180.112† | 21.552 | 1.000x | 8.357x |
21.760 | 71.360 | 21.776 | 1.000x | 3.273x |
| 50 | 151936 | 1 | 10.144 | 69.456† | 10.160 | 1.000x | 6.712x | 10.240
| 62.496 | 10.255 | 1.000x | 6.094x |
| 50 | 151936 | 2 | 10.176 | 104.056† | 10.176 | 1.000x | 10.218x |
10.336 | 66.672 | 10.320 | 1.000x | 6.456x |
| 50 | 151936 | 4 | 10.432 | 105.584† | 10.432 | 1.000x | 10.123x |
10.704 | 66.128 | 10.720 | 1.000x | 6.178x |
| 50 | 151936 | 8 | 10.944 | 105.856† | 10.928 | 1.000x | 9.683x |
11.168 | 67.311 | 11.168 | 1.000x | 6.023x |
| 50 | 151936 | 16 | 12.448 | 106.511† | 12.448 | 1.000x | 8.562x |
12.720 | 68.960 | 12.736 | 1.000x | 5.425x |
| 50 | 151936 | 32 | 13.536 | 106.992† | 13.536 | 1.000x | 7.897x |
13.824 | 72.384 | 13.824 | 1.000x | 5.236x |
| 50 | 151936 | 64 | 17.280 | 150.448† | 17.280 | 1.000x | 8.704x |
17.568 | 71.952 | 17.568 | 1.000x | 4.093x |
| 50 | 151936 | 128 | 24.896 | 192.800 | 24.912 | 1.000x | 7.734x |
25.104 | 79.856 | 25.120 | 0.999x | 3.179x |
| 50 | 262144 | 1 | 10.624 | 79.856† | 10.608 | 1.000x | 7.482x | 10.752
| 63.423 | 10.752 | 1.000x | 5.902x |
| 50 | 262144 | 2 | 10.784 | 98.048† | 10.784 | 1.000x | 9.071x | 11.008
| 65.600 | 11.008 | 1.000x | 5.961x |
| 50 | 262144 | 4 | 11.040 | 113.360† | 11.040 | 1.000x | 10.268x |
11.296 | 65.616 | 11.296 | 1.000x | 5.813x |
| 50 | 262144 | 8 | 11.864 | 132.527† | 11.872 | 1.000x | 11.171x |
12.096 | 68.207 | 12.096 | 1.000x | 5.637x |
| 50 | 262144 | 16 | 13.888 | 137.216† | 13.888 | 1.000x | 9.883x |
14.144 | 67.647 | 14.175 | 1.000x | 4.774x |
| 50 | 262144 | 32 | 16.064 | 180.624† | 16.032 | 1.000x | 11.248x |
16.352 | 114.912 | 16.336 | 1.000x | 7.029x |
| 50 | 262144 | 64 | 24.064 | 200.712 | 24.048 | 1.000x | 8.335x |
24.320 | 99.088 | 24.320 | 1.000x | 4.074x |
| 50 | 262144 | 128 | 35.808 | 209.984 | 35.808 | 1.000x | 5.862x |
36.047 | 118.992 | 36.064 | 1.000x | 3.299x |
| 1000 | 32768 | 1 | 15.424 | 45.328 | 15.376 | 1.013x | 2.941x | 13.888
| 32.367 | 13.872 | 1.000x | 2.343x |
| 1000 | 32768 | 2 | 16.176 | 47.248 | 15.776 | 1.008x | 2.946x | 13.968
| 32.944 | 13.968 | 1.000x | 2.363x |
| 1000 | 32768 | 4 | 16.336 | 47.432 | 16.664 | 0.976x | 2.866x | 14.192
| 32.911 | 14.192 | 1.000x | 2.322x |
| 1000 | 32768 | 8 | 16.608 | 47.184 | 16.352 | 1.017x | 2.917x | 14.176
| 33.008 | 14.176 | 1.000x | 2.333x |
| 1000 | 32768 | 16 | 16.808 | 51.984 | 16.928 | 1.011x | 3.110x |
14.448 | 37.472 | 14.448 | 1.000x | 2.594x |
| 1000 | 32768 | 32 | 16.432 | 53.448 | 16.208 | 1.004x | 3.261x |
15.584 | 40.000 | 15.584 | 1.000x | 2.566x |
| 1000 | 32768 | 64 | 16.384 | 54.208 | 16.352 | 1.002x | 3.208x |
16.544 | 40.800 | 16.544 | 1.000x | 2.464x |
| 1000 | 32768 | 128 | 17.696 | 54.208 | 17.712 | 1.000x | 3.050x |
18.128 | 42.688 | 18.128 | 1.000x | 2.362x |
| 1000 | 128256 | 1 | 15.040 | 59.688 | 15.040 | 1.000x | 3.976x |
15.232 | 59.999 | 15.240 | 1.000x | 3.933x |
| 1000 | 128256 | 2 | 15.104 | 66.344 | 15.104 | 1.000x | 4.389x |
15.376 | 66.416† | 15.376 | 1.000x | 4.323x |
| 1000 | 128256 | 4 | 15.168 | 70.512 | 15.168 | 1.000x | 4.640x |
15.472 | 66.368† | 15.488 | 1.000x | 4.280x |
| 1000 | 128256 | 8 | 15.744 | 71.256 | 15.744 | 1.000x | 4.516x |
16.032 | 67.552† | 16.032 | 1.000x | 4.215x |
| 1000 | 128256 | 16 | 18.880 | 96.200 | 18.880 | 1.000x | 5.097x |
19.136 | 72.672† | 19.104 | 1.000x | 3.807x |
| 1000 | 128256 | 32 | 20.304 | 94.736 | 20.096 | 1.000x | 4.719x |
20.608 | 82.927† | 20.608 | 1.000x | 4.058x |
| 1000 | 128256 | 64 | 22.960 | 137.007 | 22.960 | 1.000x | 5.978x |
23.440 | 83.456† | 23.408 | 1.000x | 3.587x |
| 1000 | 128256 | 128 | 32.464 | 184.320 | 32.432 | 1.000x | 5.699x |
32.848 | 90.080† | 32.848 | 1.000x | 2.753x |
| 1000 | 151936 | 1 | 16.320 | 67.264 | 16.320 | 1.000x | 4.117x |
16.448 | 66.752† | 16.448 | 1.000x | 4.058x |
| 1000 | 151936 | 2 | 16.608 | 73.880 | 16.608 | 1.000x | 4.447x |
16.928 | 71.152† | 16.928 | 1.000x | 4.205x |
| 1000 | 151936 | 4 | 16.832 | 93.056 | 16.832 | 1.000x | 5.529x |
17.152 | 70.688† | 17.152 | 1.000x | 4.123x |
| 1000 | 151936 | 8 | 17.328 | 90.096 | 17.328 | 1.000x | 5.199x |
17.600 | 72.303† | 17.616 | 1.000x | 4.113x |
| 1000 | 151936 | 16 | 19.816 | 110.752 | 19.792 | 1.000x | 5.595x |
20.015 | 76.975† | 20.000 | 1.000x | 3.858x |
| 1000 | 151936 | 32 | 20.736 | 115.008 | 20.720 | 1.000x | 5.551x |
21.280 | 83.391† | 21.280 | 1.000x | 3.921x |
| 1000 | 151936 | 64 | 25.152 | 157.480 | 25.152 | 1.000x | 6.280x |
25.648 | 87.136† | 25.672 | 1.000x | 3.397x |
| 1000 | 151936 | 128 | 32.096 | 206.679† | 32.096 | 1.000x | 6.443x |
32.303 | 96.703† | 32.320 | 1.000x | 2.992x |
| 1000 | 262144 | 1 | 16.832 | 82.400 | 16.768 | 1.000x | 4.896x |
16.928 | 67.024† | 16.912 | 1.000x | 3.951x |
| 1000 | 262144 | 2 | 16.864 | 145.007 | 16.864 | 1.000x | 8.582x |
17.088 | 70.560† | 17.088 | 1.000x | 4.128x |
| 1000 | 262144 | 4 | 17.648 | 145.136 | 17.664 | 1.000x | 8.202x |
17.984 | 70.696† | 17.976 | 1.000x | 3.939x |
| 1000 | 262144 | 8 | 18.320 | 140.992 | 18.336 | 1.000x | 7.691x |
18.560 | 72.864† | 18.560 | 1.000x | 3.928x |
| 1000 | 262144 | 16 | 22.400 | 141.344 | 22.416 | 1.000x | 6.306x |
22.640 | 77.584† | 22.640 | 1.000x | 3.425x |
| 1000 | 262144 | 32 | 23.728 | 196.463† | 23.728 | 1.000x | 8.353x |
24.112 | 126.255† | 24.128 | 1.000x | 5.229x |
| 1000 | 262144 | 64 | 31.056 | 204.969† | 31.056 | 1.000x | 6.546x |
31.792 | 114.609† | 31.776 | 1.000x | 3.611x |
| 1000 | 262144 | 128 | 46.528 | 206.376† | 46.528 | 0.999x | 4.436x |
46.688 | 138.016† | 46.848 | 0.997x | 2.961x |

**R200 (sm_107a, 212 SMs)**

R200 (reported as "NVIDIA Graphics Device"), sm_107a (compute capability
10.7), 212 SMs. CUDA 13.4 (nvcc V13.4.92), driver 620.62, PyTorch
2.14.1+cu130.

| top-k | vocab | batch | eager: previous Cake µs | FlashInfer sampling
µs | this PR µs | vs previous | vs FlashInfer | graph: previous Cake µs
| FlashInfer sampling µs | this PR µs | vs previous | vs FlashInfer |
|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 10 | 32768 | 1 | 7.920 | 23.281 | 7.920 | 1.000x | 2.939x | 7.776 |
24.656 | 7.776 | 1.000x | 3.188x |
| 10 | 32768 | 2 | 7.424 | 25.344 | 7.424 | 1.000x | 3.421x | 7.488 |
26.720 | 7.504 | 1.000x | 3.576x |
| 10 | 32768 | 4 | 7.504 | 26.913 | 7.488 | 1.000x | 3.595x | 7.584 |
27.968 | 7.584 | 1.000x | 3.707x |
| 10 | 32768 | 8 | 8.704 | 29.280 | 8.704 | 1.000x | 3.360x | 8.512 |
30.273 | 8.512 | 1.000x | 3.556x |
| 10 | 32768 | 16 | 8.896 | 29.504 | 8.896 | 1.000x | 3.317x | 8.801 |
30.561 | 8.800 | 1.000x | 3.486x |
| 10 | 32768 | 32 | 9.440 | 32.576 | 9.440 | 1.000x | 3.451x | 9.312 |
33.584 | 9.312 | 1.000x | 3.606x |
| 10 | 32768 | 64 | 9.665 | 32.864 | 9.664 | 1.000x | 3.401x | 9.632 |
33.920 | 9.632 | 1.000x | 3.531x |
| 10 | 32768 | 128 | 10.176 | 33.456 | 10.176 | 1.000x | 3.288x | 10.129
| 34.432 | 10.128 | 1.000x | 3.407x |
| 10 | 128256 | 1 | 8.064 | 49.568† | 8.064 | 1.000x | 6.144x | 8.113 |
50.240 | 8.096 | 1.000x | 6.223x |
| 10 | 128256 | 2 | 8.336 | 58.273† | 8.336 | 1.000x | 7.007x | 8.448 |
50.257 | 8.432 | 1.000x | 5.975x |
| 10 | 128256 | 4 | 8.384 | 60.112† | 8.384 | 1.000x | 7.195x | 8.448 |
51.056 | 8.448 | 1.000x | 6.038x |
| 10 | 128256 | 8 | 8.672 | 64.865 | 8.672 | 1.000x | 7.466x | 8.720 |
51.120 | 8.720 | 1.000x | 5.850x |
| 10 | 128256 | 16 | 9.504 | 64.449 | 9.504 | 1.000x | 6.794x | 9.536 |
51.873 | 9.504 | 1.000x | 5.468x |
| 10 | 128256 | 32 | 12.000 | 66.289 | 12.000 | 1.000x | 5.510x | 12.064
| 52.368 | 12.065 | 1.000x | 4.332x |
| 10 | 128256 | 64 | 13.377 | 65.617 | 13.377 | 1.000x | 4.900x | 13.472
| 53.689 | 13.472 | 1.000x | 3.988x |
| 10 | 128256 | 128 | 16.576 | 64.561 | 16.576 | 1.000x | 3.891x |
16.576 | 57.056 | 16.576 | 1.000x | 3.443x |
| 10 | 151936 | 1 | 8.800 | 54.769† | 8.800 | 1.000x | 6.231x | 8.832 |
54.881 | 8.832 | 1.000x | 6.236x |
| 10 | 151936 | 2 | 9.056 | 61.952† | 9.056 | 1.000x | 6.841x | 9.152 |
54.593 | 9.152 | 1.000x | 5.965x |
| 10 | 151936 | 4 | 9.280 | 63.569 | 9.280 | 1.000x | 6.850x | 9.329 |
55.105 | 9.329 | 1.000x | 5.955x |
| 10 | 151936 | 8 | 9.505 | 63.713 | 9.505 | 1.000x | 6.692x | 9.600 |
55.104 | 9.601 | 1.000x | 5.744x |
| 10 | 151936 | 16 | 10.208 | 63.361 | 10.176 | 1.000x | 6.216x | 10.336
| 56.001 | 10.336 | 1.000x | 5.450x |
| 10 | 151936 | 32 | 10.960 | 64.881 | 10.960 | 1.000x | 5.926x | 10.960
| 57.809 | 10.992 | 1.000x | 5.280x |
| 10 | 151936 | 64 | 13.744 | 66.193 | 13.744 | 1.000x | 4.799x | 13.856
| 58.241 | 13.856 | 1.000x | 4.208x |
| 10 | 151936 | 128 | 19.296 | 68.209 | 19.296 | 1.000x | 3.535x |
19.248 | 64.448 | 19.232 | 1.000x | 3.353x |
| 10 | 262144 | 1 | 9.089 | 64.160 | 9.088 | 1.000x | 7.076x | 9.136 |
55.473 | 9.136 | 1.000x | 6.086x |
| 10 | 262144 | 2 | 9.472 | 64.192 | 9.472 | 1.000x | 6.754x | 9.536 |
55.569 | 9.536 | 1.000x | 5.845x |
| 10 | 262144 | 4 | 9.712 | 63.184 | 9.712 | 1.000x | 6.495x | 9.792 |
55.681 | 9.792 | 1.000x | 5.704x |
| 10 | 262144 | 8 | 10.144 | 64.537 | 10.144 | 1.000x | 6.362x | 10.240
| 56.560 | 10.240 | 1.000x | 5.537x |
| 10 | 262144 | 16 | 11.264 | 63.361 | 11.256 | 1.000x | 5.633x | 11.360
| 57.505 | 11.360 | 1.000x | 5.064x |
| 10 | 262144 | 32 | 13.984 | 65.201 | 13.984 | 1.000x | 4.668x | 14.048
| 59.689 | 14.048 | 1.000x | 4.249x |
| 10 | 262144 | 64 | 17.985 | 83.185 | 18.000 | 1.000x | 4.637x | 18.048
| 80.321 | 18.032 | 1.000x | 4.458x |
| 10 | 262144 | 128 | 23.264 | 99.393 | 23.264 | 1.000x | 4.272x |
23.264 | 95.409 | 23.265 | 1.000x | 4.105x |
| 50 | 32768 | 1 | 8.400 | 25.441 | 8.416 | 1.000x | 3.029x | 8.256 |
26.800 | 8.241 | 1.000x | 3.243x |
| 50 | 32768 | 2 | 8.480 | 26.008 | 8.464 | 1.000x | 3.098x | 8.544 |
27.392 | 8.544 | 1.000x | 3.211x |
| 50 | 32768 | 4 | 8.576 | 27.616 | 8.576 | 1.000x | 3.222x | 8.640 |
28.592 | 8.640 | 1.000x | 3.312x |
| 50 | 32768 | 8 | 9.152 | 30.464 | 9.152 | 1.000x | 3.340x | 9.024 |
31.536 | 9.024 | 1.000x | 3.516x |
| 50 | 32768 | 16 | 9.568 | 33.808 | 9.568 | 1.000x | 3.535x | 9.552 |
34.864 | 9.536 | 1.000x | 3.671x |
| 50 | 32768 | 32 | 9.952 | 34.577 | 9.952 | 1.000x | 3.474x | 9.920 |
35.536 | 9.936 | 1.000x | 3.616x |
| 50 | 32768 | 64 | 10.176 | 34.849 | 10.145 | 1.002x | 3.433x | 10.096
| 35.761 | 10.097 | 1.000x | 3.549x |
| 50 | 32768 | 128 | 10.592 | 35.425 | 10.592 | 1.000x | 3.344x | 10.624
| 36.401 | 10.608 | 1.000x | 3.431x |
| 50 | 128256 | 1 | 9.088 | 64.433 | 9.088 | 1.000x | 7.120x | 9.056 |
50.385 | 9.056 | 1.000x | 5.575x |
| 50 | 128256 | 2 | 9.440 | 64.993 | 9.441 | 1.000x | 6.885x | 9.528 |
50.576 | 9.520 | 1.000x | 5.342x |
| 50 | 128256 | 4 | 9.568 | 62.625 | 9.552 | 1.000x | 6.551x | 9.664 |
51.809 | 9.664 | 1.000x | 5.442x |
| 50 | 128256 | 8 | 9.792 | 64.129 | 9.792 | 1.000x | 6.542x | 9.872 |
51.937 | 9.809 | 1.000x | 5.290x |
| 50 | 128256 | 16 | 10.400 | 63.617 | 10.368 | 1.000x | 6.136x | 10.480
| 54.688 | 10.480 | 1.000x | 5.239x |
| 50 | 128256 | 32 | 12.592 | 66.417 | 12.560 | 1.000x | 5.304x | 12.656
| 56.337 | 12.624 | 1.000x | 4.466x |
| 50 | 128256 | 64 | 14.032 | 65.377 | 14.017 | 1.000x | 4.654x | 14.065
| 57.312 | 14.080 | 1.000x | 4.073x |
| 50 | 128256 | 128 | 17.345 | 68.417 | 17.360 | 1.000x | 3.945x |
17.248 | 60.577 | 17.248 | 1.000x | 3.523x |
| 50 | 151936 | 1 | 9.649 | 59.344† | 9.664 | 1.000x | 6.138x | 9.665 |
54.744 | 9.680 | 1.000x | 5.671x |
| 50 | 151936 | 2 | 10.144 | 62.161 | 10.144 | 1.000x | 6.128x | 10.257
| 55.776 | 10.272 | 1.000x | 5.442x |
| 50 | 151936 | 4 | 10.145 | 63.489 | 10.145 | 1.000x | 6.249x | 10.272
| 55.968 | 10.272 | 1.000x | 5.466x |
| 50 | 151936 | 8 | 10.480 | 64.544 | 10.480 | 1.000x | 6.152x | 10.576
| 56.864 | 10.576 | 1.000x | 5.382x |
| 50 | 151936 | 16 | 11.280 | 65.249 | 11.280 | 1.000x | 5.793x | 11.360
| 59.553 | 11.376 | 1.000x | 5.277x |
| 50 | 151936 | 32 | 12.017 | 66.001 | 12.017 | 1.000x | 5.471x | 12.097
| 62.593 | 12.097 | 1.000x | 5.188x |
| 50 | 151936 | 64 | 14.720 | 66.097 | 14.720 | 1.000x | 4.495x | 14.832
| 61.713 | 14.817 | 1.000x | 4.168x |
| 50 | 151936 | 128 | 20.256 | 71.073 | 20.256 | 1.000x | 3.506x |
20.208 | 67.376 | 20.160 | 1.002x | 3.347x |
| 50 | 262144 | 1 | 10.305 | 63.056 | 10.305 | 1.000x | 6.081x | 10.368
| 55.728 | 10.368 | 1.000x | 5.385x |
| 50 | 262144 | 2 | 10.400 | 62.657 | 10.384 | 1.000x | 6.014x | 10.464
| 55.776 | 10.464 | 1.000x | 5.377x |
| 50 | 262144 | 4 | 10.752 | 63.600 | 10.752 | 1.000x | 5.897x | 10.849
| 56.480 | 10.864 | 1.000x | 5.213x |
| 50 | 262144 | 8 | 11.137 | 64.064 | 11.136 | 1.000x | 5.745x | 11.232
| 57.376 | 11.232 | 1.000x | 5.164x |
| 50 | 262144 | 16 | 11.953 | 64.737 | 11.952 | 1.000x | 5.424x | 11.968
| 60.224 | 11.968 | 1.000x | 5.034x |
| 50 | 262144 | 32 | 14.512 | 66.545 | 14.528 | 1.000x | 4.596x | 14.592
| 63.601 | 14.576 | 1.000x | 4.367x |
| 50 | 262144 | 64 | 18.480 | 87.249 | 18.496 | 1.000x | 4.735x | 18.560
| 84.433 | 18.560 | 1.000x | 4.563x |
| 50 | 262144 | 128 | 23.872 | 102.290 | 23.872 | 1.000x | 4.282x |
23.872 | 99.073 | 23.872 | 1.000x | 4.151x |
| 1000 | 32768 | 1 | 12.032 | 25.968 | 12.033 | 1.000x | 2.156x | 12.145
| 27.377 | 12.161 | 1.000x | 2.247x |
| 1000 | 32768 | 2 | 12.480 | 26.496 | 12.512 | 1.000x | 2.119x | 12.448
| 27.793 | 12.448 | 1.000x | 2.231x |
| 1000 | 32768 | 4 | 13.072 | 27.521 | 13.056 | 1.000x | 2.110x | 12.976
| 28.480 | 12.976 | 1.000x | 2.197x |
| 1000 | 32768 | 8 | 12.656 | 27.520 | 12.656 | 1.000x | 2.195x | 12.768
| 28.785 | 12.768 | 1.000x | 2.241x |
| 1000 | 32768 | 16 | 12.912 | 28.353 | 12.896 | 1.000x | 2.199x |
12.928 | 29.392 | 12.928 | 1.000x | 2.277x |
| 1000 | 32768 | 32 | 12.800 | 31.200 | 12.784 | 1.000x | 2.449x |
12.960 | 32.224 | 12.960 | 1.000x | 2.515x |
| 1000 | 32768 | 64 | 14.848 | 33.504 | 14.848 | 1.000x | 2.256x |
14.832 | 34.496 | 14.848 | 1.000x | 2.326x |
| 1000 | 32768 | 128 | 15.744 | 37.392 | 15.744 | 1.000x | 2.392x |
16.048 | 38.401 | 16.064 | 1.000x | 2.403x |
| 1000 | 128256 | 1 | 14.144 | 53.568 | 14.145 | 1.000x | 3.775x |
14.480 | 54.321 | 14.480 | 1.000x | 3.759x |
| 1000 | 128256 | 2 | 15.008 | 57.856 | 15.024 | 1.000x | 3.851x |
15.184 | 57.344† | 15.184 | 1.000x | 3.784x |
| 1000 | 128256 | 4 | 15.552 | 58.144 | 15.552 | 1.000x | 3.746x |
15.544 | 58.209† | 15.552 | 1.000x | 3.748x |
| 1000 | 128256 | 8 | 15.648 | 58.273 | 15.648 | 1.000x | 3.724x |
15.696 | 58.849† | 15.696 | 1.000x | 3.754x |
| 1000 | 128256 | 16 | 16.064 | 67.040† | 16.064 | 1.000x | 4.178x |
16.064 | 62.481† | 16.064 | 1.000x | 3.889x |
| 1000 | 128256 | 32 | 17.201 | 70.976 | 17.200 | 1.000x | 4.128x |
17.184 | 71.680 | 17.184 | 1.000x | 4.172x |
| 1000 | 128256 | 64 | 19.584 | 75.665† | 19.600 | 1.000x | 3.861x |
19.680 | 73.313† | 19.680 | 1.000x | 3.728x |
| 1000 | 128256 | 128 | 26.784 | 78.785† | 26.784 | 1.000x | 2.963x |
26.977 | 76.777† | 26.992 | 1.000x | 2.854x |
| 1000 | 151936 | 1 | 14.992 | 60.880 | 14.992 | 1.000x | 4.060x |
15.232 | 60.433† | 15.232 | 1.000x | 3.975x |
| 1000 | 151936 | 2 | 15.441 | 65.329† | 15.456 | 1.000x | 4.218x |
15.521 | 61.233† | 15.521 | 1.000x | 3.954x |
| 1000 | 151936 | 4 | 16.032 | 65.489† | 16.032 | 1.000x | 4.090x |
16.032 | 61.953† | 16.064 | 1.000x | 3.859x |
| 1000 | 151936 | 8 | 16.272 | 66.177† | 16.272 | 1.000x | 4.081x |
16.304 | 62.929† | 16.304 | 1.000x | 3.861x |
| 1000 | 151936 | 16 | 16.496 | 68.704† | 16.497 | 1.000x | 4.166x |
16.480 | 66.337† | 16.496 | 1.000x | 4.022x |
| 1000 | 151936 | 32 | 17.872 | 73.680† | 17.872 | 1.000x | 4.126x |
17.952 | 71.169† | 17.953 | 1.000x | 3.966x |
| 1000 | 151936 | 64 | 21.360 | 78.769† | 21.376 | 1.000x | 3.698x |
21.409 | 76.593† | 21.409 | 1.000x | 3.588x |
| 1000 | 151936 | 128 | 30.256 | 84.225† | 30.272 | 1.000x | 2.849x |
30.305 | 82.129† | 30.416 | 0.999x | 2.742x |
| 1000 | 262144 | 1 | 16.352 | 64.249† | 16.336 | 1.000x | 3.907x |
16.577 | 60.065† | 16.576 | 1.000x | 3.653x |
| 1000 | 262144 | 2 | 17.040 | 65.289† | 17.008 | 1.000x | 3.813x |
17.136 | 61.120† | 17.136 | 1.000x | 3.575x |
| 1000 | 262144 | 4 | 17.632 | 66.464† | 17.648 | 1.000x | 3.769x |
17.744 | 61.873† | 17.744 | 1.000x | 3.505x |
| 1000 | 262144 | 8 | 17.744 | 66.977† | 17.729 | 1.000x | 3.802x |
17.792 | 63.185† | 17.793 | 1.000x | 3.545x |
| 1000 | 262144 | 16 | 18.305 | 68.960† | 18.305 | 1.000x | 3.772x |
18.320 | 66.752† | 18.320 | 1.000x | 3.644x |
| 1000 | 262144 | 32 | 19.648 | 74.528† | 19.648 | 1.000x | 3.799x |
19.616 | 71.873† | 19.616 | 1.000x | 3.666x |
| 1000 | 262144 | 64 | 26.785 | 101.730† | 26.784 | 1.000x | 3.803x |
26.832 | 99.537† | 26.832 | 1.000x | 3.708x |
| 1000 | 262144 | 128 | 33.760 | 117.793† | 33.617 | 1.000x | 3.519x |
33.760 | 114.817† | 33.825 | 1.000x | 3.394x |

**RTX PRO 6000 (sm_120a, 188 SMs)**

NVIDIA RTX PRO 6000 Blackwell Server Edition, sm_120a (compute
capability 12.0), 188 SMs. CUDA 13.4 (nvcc V13.4.92), driver 595.84.01,
PyTorch 2.14.1+cu130. Vocab 262144 is not in this GPU's shape list.

| top-k | vocab | batch | eager: previous Cake µs | FlashInfer sampling
µs | this PR µs | vs previous | vs FlashInfer | graph: previous Cake µs
| FlashInfer sampling µs | this PR µs | vs previous | vs FlashInfer |
|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 10 | 32768 | 1 | 9.760 | 28.224 | 9.760 | 1.000x | 2.892x | 9.903 |
29.169 | 9.904 | 1.000x | 2.947x |
| 10 | 32768 | 2 | 9.969 | 30.800 | 9.968 | 1.000x | 3.093x | 10.144 |
31.776 | 10.144 | 1.000x | 3.134x |
| 10 | 32768 | 4 | 10.144 | 31.920 | 10.144 | 1.000x | 3.172x | 10.320 |
32.864 | 10.320 | 1.000x | 3.201x |
| 10 | 32768 | 8 | 10.592 | 35.840 | 10.592 | 1.000x | 3.382x | 10.752 |
36.736 | 10.752 | 1.000x | 3.421x |
| 10 | 32768 | 16 | 12.063 | 39.072 | 12.064 | 1.000x | 3.250x | 12.225
| 40.008 | 12.225 | 1.000x | 3.284x |
| 10 | 32768 | 32 | 15.536 | 42.400 | 15.553 | 1.000x | 2.724x | 15.712
| 43.712 | 15.712 | 1.000x | 2.788x |
| 10 | 32768 | 64 | 20.000 | 49.904 | 20.016 | 1.000x | 2.494x | 20.080
| 50.560 | 20.096 | 1.000x | 2.519x |
| 10 | 32768 | 128 | 35.184 | 78.032 | 35.200 | 1.000x | 2.216x | 35.264
| 73.808† | 35.248 | 1.000x | 2.094x |
| 10 | 128256 | 1 | 12.288 | 45.120† | 12.288 | 1.000x | 3.670x | 12.384
| 41.728 | 12.384 | 1.000x | 3.349x |
| 10 | 128256 | 2 | 13.056 | 49.792† | 13.040 | 1.000x | 3.829x | 13.184
| 41.824 | 13.184 | 1.000x | 3.167x |
| 10 | 128256 | 4 | 14.560 | 50.849† | 14.560 | 1.000x | 3.500x | 14.720
| 42.416 | 14.736 | 1.000x | 2.880x |
| 10 | 128256 | 8 | 17.953 | 54.464† | 17.976 | 0.999x | 3.031x | 18.113
| 44.672 | 18.128 | 1.000x | 2.462x |
| 10 | 128256 | 16 | 22.655 | 93.280† | 22.624 | 1.000x | 4.125x |
22.816 | 51.960 | 22.785 | 1.001x | 2.278x |
| 10 | 128256 | 32 | 28.081 | 97.841 | 28.096 | 1.000x | 3.457x | 28.224
| 77.641 | 28.208 | 1.001x | 2.758x |
| 10 | 128256 | 64 | 42.497 | 111.825 | 42.529 | 0.999x | 2.633x |
42.560 | 108.856 | 42.529 | 1.000x | 2.559x |
| 10 | 128256 | 128 | 70.576 | 163.713 | 70.560 | 1.000x | 2.321x |
70.737 | 161.217 | 70.768 | 1.000x | 2.282x |
| 10 | 151936 | 1 | 13.760 | 47.712† | 13.744 | 1.000x | 3.467x | 13.889
| 42.913 | 13.904 | 1.000x | 3.076x |
| 10 | 151936 | 2 | 14.368 | 58.592† | 14.368 | 1.000x | 4.076x | 14.529
| 43.040 | 14.544 | 1.000x | 2.963x |
| 10 | 151936 | 4 | 15.904 | 64.208† | 15.904 | 1.000x | 4.042x | 16.064
| 44.208 | 16.064 | 1.000x | 2.751x |
| 10 | 151936 | 8 | 20.096 | 76.641† | 20.064 | 1.000x | 3.820x | 20.224
| 47.104 | 20.241 | 1.000x | 2.322x |
| 10 | 151936 | 16 | 24.976 | 82.192† | 24.992 | 1.000x | 3.292x |
25.048 | 52.480 | 25.073 | 1.000x | 2.099x |
| 10 | 151936 | 32 | 31.576 | 101.032 | 31.568 | 1.000x | 3.189x |
31.664 | 82.081 | 31.648 | 1.000x | 2.594x |
| 10 | 151936 | 64 | 48.512 | 119.040 | 48.512 | 1.000x | 2.455x |
48.752 | 116.496 | 48.752 | 1.000x | 2.393x |
| 10 | 151936 | 128 | 79.521 | 176.689 | 79.552 | 1.000x | 2.222x |
79.544 | 173.921 | 79.552 | 1.000x | 2.187x |
| 50 | 32768 | 1 | 9.823 | 30.288 | 9.808 | 1.000x | 3.091x | 9.952 |
31.264 | 9.952 | 1.000x | 3.142x |
| 50 | 32768 | 2 | 10.016 | 31.104 | 10.016 | 1.000x | 3.112x | 10.224 |
32.120 | 10.209 | 1.000x | 3.164x |
| 50 | 32768 | 4 | 10.080 | 32.416 | 10.080 | 1.000x | 3.214x | 10.272 |
33.264 | 10.272 | 1.000x | 3.238x |
| 50 | 32768 | 8 | 10.640 | 36.736 | 10.640 | 1.000x | 3.454x | 10.784 |
37.641 | 10.784 | 1.000x | 3.492x |
| 50 | 32768 | 16 | 12.081 | 38.032 | 12.081 | 1.000x | 3.154x | 12.256
| 38.913 | 12.256 | 1.000x | 3.175x |
| 50 | 32768 | 32 | 15.568 | 41.344 | 15.568 | 1.000x | 2.655x | 15.760
| 42.648 | 15.744 | 1.000x | 2.712x |
| 50 | 32768 | 64 | 20.017 | 48.144 | 20.032 | 1.000x | 2.405x | 20.128
| 48.848 | 20.096 | 1.001x | 2.435x |
| 50 | 32768 | 128 | 35.264 | 76.720 | 35.264 | 1.000x | 2.176x | 35.304
| 75.704 | 35.312 | 1.000x | 2.144x |
| 50 | 128256 | 1 | 12.512 | 75.681† | 12.527 | 1.000x | 6.047x | 12.576
| 41.800 | 12.576 | 1.000x | 3.322x |
| 50 | 128256 | 2 | 13.216 | 76.049† | 13.216 | 1.000x | 5.755x | 13.376
| 41.840 | 13.376 | 1.000x | 3.125x |
| 50 | 128256 | 4 | 14.656 | 77.264† | 14.656 | 1.000x | 5.272x | 14.832
| 43.129 | 14.848 | 1.000x | 2.904x |
| 50 | 128256 | 8 | 18.081 | 79.904† | 18.096 | 1.000x | 4.420x | 18.256
| 45.984 | 18.271 | 1.000x | 2.516x |
| 50 | 128256 | 16 | 22.816 | 85.393† | 22.800 | 1.000x | 3.747x |
22.953 | 52.608 | 22.944 | 1.000x | 2.294x |
| 50 | 128256 | 32 | 28.448 | 99.344 | 28.448 | 1.000x | 3.494x | 28.568
| 81.048 | 28.576 | 1.000x | 2.838x |
| 50 | 128256 | 64 | 42.984 | 114.608 | 42.960 | 1.000x | 2.664x |
43.008 | 111.537 | 42.976 | 1.000x | 2.594x |
| 50 | 128256 | 128 | 70.897 | 166.129 | 70.880 | 1.000x | 2.345x |
71.073 | 163.905 | 71.072 | 1.000x | 2.307x |
| 50 | 151936 | 1 | 13.904 | 52.672† | 13.888 | 1.000x | 3.791x | 14.064
| 43.264 | 14.064 | 1.000x | 3.078x |
| 50 | 151936 | 2 | 14.560 | 57.553† | 14.560 | 1.000x | 3.954x | 14.720
| 43.504 | 14.720 | 1.000x | 2.952x |
| 50 | 151936 | 4 | 16.175 | 61.760† | 16.161 | 1.000x | 3.820x | 16.352
| 45.256 | 16.352 | 1.000x | 2.766x |
| 50 | 151936 | 8 | 20.320 | 65.312† | 20.320 | 1.000x | 3.213x | 20.480
| 48.640 | 20.480 | 1.000x | 2.373x |
| 50 | 151936 | 16 | 25.168 | 106.400 | 25.169 | 1.001x | 4.220x |
25.248 | 55.536 | 25.216 | 1.001x | 2.202x |
| 50 | 151936 | 32 | 31.760 | 93.969 | 31.728 | 1.000x | 2.963x | 31.848
| 85.920 | 31.857 | 1.000x | 2.704x |
| 50 | 151936 | 64 | 48.849 | 122.577 | 48.832 | 1.000x | 2.507x |
49.056 | 120.496 | 49.104 | 1.000x | 2.457x |
| 50 | 151936 | 128 | 79.873 | 180.377 | 79.873 | 1.000x | 2.257x |
79.904 | 177.633 | 79.904 | 1.000x | 2.224x |
| 1000 | 32768 | 1 | 13.696 | 30.656 | 13.696 | 1.000x | 2.233x | 13.760
| 31.520 | 13.760 | 1.000x | 2.290x |
| 1000 | 32768 | 2 | 13.888 | 31.376 | 13.888 | 1.000x | 2.260x | 14.001
| 32.384 | 14.016 | 1.000x | 2.311x |
| 1000 | 32768 | 4 | 14.048 | 31.952 | 14.048 | 1.000x | 2.280x | 14.144
| 32.944 | 14.145 | 1.000x | 2.333x |
| 1000 | 32768 | 8 | 14.368 | 32.192 | 14.384 | 1.000x | 2.236x | 14.465
| 33.088 | 14.473 | 1.000x | 2.286x |
| 1000 | 32768 | 16 | 15.808 | 37.296 | 15.808 | 1.000x | 2.361x |
15.937 | 38.144 | 15.936 | 1.000x | 2.393x |
| 1000 | 32768 | 32 | 19.201 | 44.512 | 19.201 | 1.000x | 2.318x |
19.416 | 45.824 | 19.424 | 1.000x | 2.360x |
| 1000 | 32768 | 64 | 24.160 | 54.912 | 24.160 | 1.000x | 2.275x |
24.480 | 55.552 | 24.464 | 1.000x | 2.283x |
| 1000 | 32768 | 128 | 38.352 | 83.113 | 38.392 | 1.000x | 2.165x |
38.552 | 82.200 | 38.544 | 1.000x | 2.135x |
| 1000 | 128256 | 1 | 15.760 | 48.576 | 15.760 | 1.000x | 3.081x |
15.872 | 46.208† | 15.873 | 1.000x | 2.907x |
| 1000 | 128256 | 2 | 16.208 | 52.401 | 16.209 | 1.000x | 3.235x |
16.384 | 47.344† | 16.384 | 1.000x | 2.891x |
| 1000 | 128256 | 4 | 18.144 | 53.760 | 18.112 | 1.001x | 2.967x |
18.336 | 48.800† | 18.336 | 1.000x | 2.666x |
| 1000 | 128256 | 8 | 21.303 | 57.184 | 21.312 | 1.000x | 2.685x |
21.504 | 51.536† | 21.488 | 1.000x | 2.397x |
| 1000 | 128256 | 16 | 26.032 | 82.656 | 26.016 | 1.000x | 3.179x |
26.272 | 59.296† | 26.281 | 1.000x | 2.255x |
| 1000 | 128256 | 32 | 42.672 | 98.656† | 42.688 | 1.000x | 2.319x |
42.897 | 90.977† | 42.896 | 1.000x | 2.120x |
| 1000 | 128256 | 64 | 48.448 | 125.856† | 48.465 | 1.000x | 2.596x |
48.513 | 122.545† | 48.513 | 1.000x | 2.529x |
| 1000 | 128256 | 128 | 76.513 | 178.785† | 76.528 | 1.000x | 2.340x |
76.840 | 177.105† | 76.832 | 1.000x | 2.306x |
| 1000 | 151936 | 1 | 17.104 | 53.328 | 17.088 | 1.000x | 3.120x |
17.248 | 47.328† | 17.248 | 1.000x | 2.752x |
| 1000 | 151936 | 2 | 17.888 | 57.024 | 17.888 | 1.000x | 3.187x |
18.096 | 48.448† | 18.111 | 1.000x | 2.678x |
| 1000 | 151936 | 4 | 19.552 | 75.009 | 19.529 | 1.001x | 3.841x |
19.727 | 50.593† | 19.729 | 1.000x | 2.564x |
| 1000 | 151936 | 8 | 23.472 | 78.688 | 23.504 | 1.000x | 3.349x |
23.680 | 53.456† | 23.680 | 1.000x | 2.259x |
| 1000 | 151936 | 16 | 28.336 | 84.176 | 28.337 | 1.000x | 2.970x |
28.368 | 61.697† | 28.320 | 1.000x | 2.179x |
| 1000 | 151936 | 32 | 47.616 | 103.025† | 47.632 | 1.000x | 2.166x |
47.648 | 95.424† | 47.617 | 1.000x | 2.006x |
| 1000 | 151936 | 64 | 53.632 | 132.369† | 53.617 | 1.000x | 2.472x |
54.064 | 130.945† | 54.112 | 0.999x | 2.422x |
| 1000 | 151936 | 128 | 85.312 | 192.113† | 85.328 | 1.000x | 2.255x |
85.329 | 189.840† | 85.344 | 1.000x | 2.225x |

**B200 (sm_100a, 148 SMs)**: this table is waiting on a measurement and
will be added to this description.

Cake ships no other data type, layout or fused form of `cake_sampling`:
float32 probabilities, contiguous rows, and top-k then top-p with a
Philox sample are the only ones. The family ships as one module with one
`-gencode` per FlashInfer target: sm_90a, sm_100a, sm_103a, sm_107a,
sm_110a, sm_120a, sm_120f and sm_121a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* Added an L2-prefetch option for selected sampling configurations,
which may improve performance without changing results.
* The option is used only when a matching build and supported launch
plan are available; otherwise, sampling continues with the existing
plan.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [19d71a0](https://github.com/flashinfer-ai/flashinfer/commit/19d71a01e91ea8b74345a15a0e6a69e78f00466c)

- **作者**: eigen
- **时间**: 2026-11-01T11:00:53Z
- **提交信息**: perf(cake_mhc): with grad, two-size column slab schedule at hidden 5120 / 7168 on sm_100a (#8189)

### [61eadc3](https://github.com/flashinfer-ai/flashinfer/commit/61eadc3805f23293de610238f2c96d7cf888503f)

- **作者**: eigen
- **时间**: 2026-11-01T10:54:35Z
- **提交信息**: perf(cake_rmsnorm_det): H 5120, per-head H 256 and FP32-weight autograd RMSNorm (SM100 / SM103 / SM107) (#8187)

`cake_rmsnorm_det_train` is Cake's deterministic training RMSNorm
(forward and backward). This PR adds the shapes requested in #7045:
- H = 5120 (`[T, 5120]`) with BF16 or FP32 weight.
- H = 256 with FP32 weight, as the per-head query view `[T, 24, 256]`
with strides (12288, 512, 1).
- H = 256 with FP32 weight, as the contiguous key `[T, 4, 256]`.

No earlier Cake version supports these shapes, so the baseline is the
fastest measured per-shape static `torch.compile`. Every backward row is
faster than that baseline: 1.001x to 2.426x on B200 and 1.020x to 2.389x
on GB300. Forward rows range from 0.966x to 1.532x on B200 and from
0.970x to 1.504x on GB300.

**NVIDIA B200 (148 SMs), sm_100a**; CUDA 13.4 (kernels built with nvcc
13.4), PyTorch 2.14.1+cu130, Triton 3.8.0. Latency = CUPTI kernel-active
time per call, cold L2, median of 4 x 20 calls per process.
torch.compile = fastest measured per-shape static compile (FP32 formula,
dynamic=False; minimum over every process of every formal session and
tc-only sweep of the row, each process with a fresh inductor / Triton
cache). Cake = fastest measured process of the delivered program over
every formal session of the row (the same statistic). Speedup =
torch.compile / Cake.

| Shape | T | Pass | torch.compile (us) | Cake (us) | Speedup |
|---|---:|---|---:|---:|---:|
| H 256 query: [T, 24, 256] view, strides (12288, 512, 1), FP32 weight
(rows = 24 T) | 256 | fwd | 3.232 | 3.168 | 1.020x |
| H 256 query: [T, 24, 256] view, strides (12288, 512, 1), FP32 weight
(rows = 24 T) | 1024 | fwd | 6.096 | 6.016 | 1.013x |
| H 256 query: [T, 24, 256] view, strides (12288, 512, 1), FP32 weight
(rows = 24 T) | 4096 | fwd | 17.664 | 17.664 | 1.000x |
| H 256 query: [T, 24, 256] view, strides (12288, 512, 1), FP32 weight
(rows = 24 T) | 14928 | fwd | 57.088 | 56.488 | 1.011x |
| H 256 query: [T, 24, 256] view, strides (12288, 512, 1), FP32 weight
(rows = 24 T) | 15288 | fwd | 58.535 | 57.848 | 1.012x |
| H 256 query: [T, 24, 256] view, strides (12288, 512, 1), FP32 weight
(rows = 24 T) | 15566 | fwd | 59.575 | 58.624 | 1.016x |
| H 256 query: [T, 24, 256] view, strides (12288, 512, 1), FP32 weight
(rows = 24 T) | 15590 | fwd | 59.423 | 58.776 | 1.011x |
| H 256 query: [T, 24, 256] view, strides (12288, 512, 1), FP32 weight
(rows = 24 T) | 16114 | fwd | 61.736 | 60.720 | 1.017x |
| H 256 query: [T, 24, 256] view, strides (12288, 512, 1), FP32 weight
(rows = 24 T) | 16132 | fwd | 61.728 | 60.880 | 1.014x |
| H 256 query: [T, 24, 256] view, strides (12288, 512, 1), FP32 weight
(rows = 24 T) | 16164 | fwd | 61.712 | 60.775 | 1.015x |
| H 256 query: [T, 24, 256] view, strides (12288, 512, 1), FP32 weight
(rows = 24 T) | 16263 | fwd | 61.912 | 61.000 | 1.015x |
| H 256 query: [T, 24, 256] view, strides (12288, 512, 1), FP32 weight
(rows = 24 T) | 32768 | fwd | 120.823 | 119.407 | 1.012x |
| H 256 query: [T, 24, 256] view, strides (12288, 512, 1), FP32 weight
(rows = 24 T) | 65536 | fwd | 238.622 | 235.606 | 1.013x |
| H 256 query: [T, 24, 256] view, strides (12288, 512, 1), FP32 weight
(rows = 24 T) | 256 | bwd | 14.087 | 9.863 | 1.428x |
| H 256 query: [T, 24, 256] view, strides (12288, 512, 1), FP32 weight
(rows = 24 T) | 1024 | bwd | 20.231 | 15.864 | 1.275x |
| H 256 query: [T, 24, 256] view, strides (12288, 512, 1), FP32 weight
(rows = 24 T) | 4096 | bwd | 39.552 | 37.432 | 1.057x |
| H 256 query: [T, 24, 256] view, strides (12288, 512, 1), FP32 weight
(rows = 24 T) | 14928 | bwd | 121.808 | 103.663 | 1.175x |
| H 256 query: [T, 24, 256] view, strides (12288, 512, 1), FP32 weight
(rows = 24 T) | 15288 | bwd | 121.440 | 105.871 | 1.147x |
| H 256 query: [T, 24, 256] view, strides (12288, 512, 1), FP32 weight
(rows = 24 T) | 15566 | bwd | 123.815 | 107.479 | 1.152x |
| H 256 query: [T, 24, 256] view, strides (12288, 512, 1), FP32 weight
(rows = 24 T) | 15590 | bwd | 120.463 | 107.440 | 1.121x |
| H 256 query: [T, 24, 256] view, strides (12288, 512, 1), FP32 weight
(rows = 24 T) | 16114 | bwd | 122.600 | 110.415 | 1.110x |
| H 256 query: [T, 24, 256] view, strides (12288, 512, 1), FP32 weight
(rows = 24 T) | 16132 | bwd | 124.287 | 110.799 | 1.122x |
| H 256 query: [T, 24, 256] view, strides (12288, 512, 1), FP32 weight
(rows = 24 T) | 16164 | bwd | 123.016 | 111.056 | 1.108x |
| H 256 query: [T, 24, 256] view, strides (12288, 512, 1), FP32 weight
(rows = 24 T) | 16263 | bwd | 123.672 | 111.479 | 1.109x |
| H 256 query: [T, 24, 256] view, strides (12288, 512, 1), FP32 weight
(rows = 24 T) | 32768 | bwd | 219.567 | 209.399 | 1.049x |
| H 256 query: [T, 24, 256] view, strides (12288, 512, 1), FP32 weight
(rows = 24 T) | 65536 | bwd | 402.477 | 402.069 | 1.001x |
| H 256 key: [T, 4, 256] contiguous, FP32 weight (rows = 4 T) | 256 |
fwd | 2.288 | 2.320 | 0.986x |
| H 256 key: [T, 4, 256] contiguous, FP32 weight (rows = 4 T) | 1024 |
fwd | 2.680 | 2.776 | 0.966x |
| H 256 key: [T, 4, 256] contiguous, FP32 weight (rows = 4 T) | 4096 |
fwd | 4.656 | 4.784 | 0.973x |
| H 256 key: [T, 4, 256] contiguous, FP32 weight (rows = 4 T) | 14928 |
fwd | 11.680 | 11.464 | 1.019x |
| H 256 key: [T, 4, 256] contiguous, FP32 weight (rows = 4 T) | 15288 |
fwd | 11.704 | 11.624 | 1.007x |
| H 256 key: [T, 4, 256] contiguous, FP32 weight (rows = 4 T) | 15566 |
fwd | 12.024 | 11.815 | 1.018x |
| H 256 key: [T, 4, 256] contiguous, FP32 weight (rows = 4 T) | 15590 |
fwd | 11.872 | 11.704 | 1.014x |
| H 256 key: [T, 4, 256] contiguous, FP32 weight (rows = 4 T) | 16114 |
fwd | 12.120 | 12.080 | 1.003x |
| H 256 key: [T, 4, 256] contiguous, FP32 weight (rows = 4 T) | 16132 |
fwd | 11.952 | 12.016 | 0.995x |
| H 256 key: [T, 4, 256] contiguous, FP32 weight (rows = 4 T) | 16164 |
fwd | 12.128 | 12.208 | 0.993x |
| H 256 key: [T, 4, 256] contiguous, FP32 weight (rows = 4 T) | 16263 |
fwd | 12.384 | 12.320 | 1.005x |
| H 256 key: [T, 4, 256] contiguous, FP32 weight (rows = 4 T) | 32768 |
fwd | 22.496 | 22.320 | 1.008x |
| H 256 key: [T, 4, 256] contiguous, FP32 weight (rows = 4 T) | 65536 |
fwd | 41.935 | 41.920 | 1.000x |
| H 256 key: [T, 4, 256] contiguous, FP32 weight (rows = 4 T) | 256 |
bwd | 12.856 | 6.008 | 2.140x |
| H 256 key: [T, 4, 256] contiguous, FP32 weight (rows = 4 T) | 1024 |
bwd | 13.568 | 8.128 | 1.669x |
| H 256 key: [T, 4, 256] contiguous, FP32 weight (rows = 4 T) | 4096 |
bwd | 17.208 | 13.304 | 1.293x |
| H 256 key: [T, 4, 256] contiguous, FP32 weight (rows = 4 T) | 14928 |
bwd | 28.800 | 24.824 | 1.160x |
| H 256 key: [T, 4, 256] contiguous, FP32 weight (rows = 4 T) | 15288 |
bwd | 29.200 | 24.840 | 1.176x |
| H 256 key: [T, 4, 256] contiguous, FP32 weight (rows = 4 T) | 15566 |
bwd | 29.488 | 25.416 | 1.160x |
| H 256 key: [T, 4, 256] contiguous, FP32 weight (rows = 4 T) | 15590 |
bwd | 29.504 | 25.416 | 1.161x |
| H 256 key: [T, 4, 256] contiguous, FP32 weight (rows = 4 T) | 16114 |
bwd | 29.944 | 25.768 | 1.162x |
| H 256 key: [T, 4, 256] contiguous, FP32 weight (rows = 4 T) | 16132 |
bwd | 29.896 | 25.871 | 1.156x |
| H 256 key: [T, 4, 256] contiguous, FP32 weight (rows = 4 T) | 16164 |
bwd | 29.840 | 25.864 | 1.154x |
| H 256 key: [T, 4, 256] contiguous, FP32 weight (rows = 4 T) | 16263 |
bwd | 30.175 | 26.224 | 1.151x |
| H 256 key: [T, 4, 256] contiguous, FP32 weight (rows = 4 T) | 32768 |
bwd | 48.616 | 46.232 | 1.052x |
| H 256 key: [T, 4, 256] contiguous, FP32 weight (rows = 4 T) | 65536 |
bwd | 86.072 | 79.560 | 1.082x |
| H 5120: [T, 5120], BF16 weight | 256 | fwd | 2.784 | 2.680 | 1.039x |
| H 5120: [T, 5120], BF16 weight | 1024 | fwd | 4.568 | 4.384 | 1.042x |
| H 5120: [T, 5120], BF16 weight | 4096 | fwd | 18.192 | 11.872 | 1.532x
|
| H 5120: [T, 5120], BF16 weight | 14928 | fwd | 48.952 | 46.912 |
1.043x |
| H 5120: [T, 5120], BF16 weight | 15288 | fwd | 49.967 | 47.672 |
1.048x |
| H 5120: [T, 5120], BF16 weight | 15566 | fwd | 50.904 | 48.504 |
1.049x |
| H 5120: [T, 5120], BF16 weight | 15590 | fwd | 50.928 | 48.560 |
1.049x |
| H 5120: [T, 5120], BF16 weight | 16114 | fwd | 52.408 | 50.368 |
1.041x |
| H 5120: [T, 5120], BF16 weight | 16132 | fwd | 52.423 | 50.264 |
1.043x |
| H 5120: [T, 5120], BF16 weight | 16164 | fwd | 52.575 | 50.608 |
1.039x |
| H 5120: [T, 5120], BF16 weight | 16263 | fwd | 52.815 | 50.695 |
1.042x |
| H 5120: [T, 5120], BF16 weight | 32768 | fwd | 110.975 | 100.103 |
1.109x |
| H 5120: [T, 5120], BF16 weight | 65536 | fwd | 215.990 | 197.367 |
1.094x |
| H 5120: [T, 5120], BF16 weight | 256 | bwd | 11.015 | 7.584 | 1.452x |
| H 5120: [T, 5120], BF16 weight | 1024 | bwd | 25.080 | 12.360 | 2.029x
|
| H 5120: [T, 5120], BF16 weight | 4096 | bwd | 64.623 | 27.112 | 2.384x
|
| H 5120: [T, 5120], BF16 weight | 14928 | bwd | 156.391 | 80.503 |
1.943x |
| H 5120: [T, 5120], BF16 weight | 15288 | bwd | 157.582 | 81.584 |
1.932x |
| H 5120: [T, 5120], BF16 weight | 15566 | bwd | 158.543 | 82.567 |
1.920x |
| H 5120: [T, 5120], BF16 weight | 15590 | bwd | 158.951 | 82.775 |
1.920x |
| H 5120: [T, 5120], BF16 weight | 16114 | bwd | 161.406 | 85.064 |
1.897x |
| H 5120: [T, 5120], BF16 weight | 16132 | bwd | 162.359 | 85.167 |
1.906x |
| H 5120: [T, 5120], BF16 weight | 16164 | bwd | 161.614 | 84.760 |
1.907x |
| H 5120: [T, 5120], BF16 weight | 16263 | bwd | 162.919 | 85.911 |
1.896x |
| H 5120: [T, 5120], BF16 weight | 32768 | bwd | 259.526 | 160.943 |
1.613x |
| H 5120: [T, 5120], BF16 weight | 65536 | bwd | 472.685 | 310.903 |
1.520x |
| H 5120: [T, 5120], FP32 weight | 256 | fwd | 2.944 | 2.688 | 1.095x |
| H 5120: [T, 5120], FP32 weight | 1024 | fwd | 4.640 | 4.544 | 1.021x |
| H 5120: [T, 5120], FP32 weight | 4096 | fwd | 18.280 | 12.712 | 1.438x
|
| H 5120: [T, 5120], FP32 weight | 14928 | fwd | 47.311 | 45.144 |
1.048x |
| H 5120: [T, 5120], FP32 weight | 15288 | fwd | 48.416 | 46.560 |
1.040x |
| H 5120: [T, 5120], FP32 weight | 15566 | fwd | 48.943 | 46.952 |
1.042x |
| H 5120: [T, 5120], FP32 weight | 15590 | fwd | 49.136 | 47.056 |
1.044x |
| H 5120: [T, 5120], FP32 weight | 16114 | fwd | 50.600 | 48.728 |
1.038x |
| H 5120: [T, 5120], FP32 weight | 16132 | fwd | 50.679 | 48.448 |
1.046x |
| H 5120: [T, 5120], FP32 weight | 16164 | fwd | 50.832 | 48.840 |
1.041x |
| H 5120: [T, 5120], FP32 weight | 16263 | fwd | 51.015 | 48.880 |
1.044x |
| H 5120: [T, 5120], FP32 weight | 32768 | fwd | 106.832 | 98.840 |
1.081x |
| H 5120: [T, 5120], FP32 weight | 65536 | fwd | 205.670 | 197.071 |
1.044x |
| H 5120: [T, 5120], FP32 weight | 256 | bwd | 11.176 | 7.624 | 1.466x |
| H 5120: [T, 5120], FP32 weight | 1024 | bwd | 26.248 | 12.656 | 2.074x
|
| H 5120: [T, 5120], FP32 weight | 4096 | bwd | 67.824 | 27.952 | 2.426x
|
| H 5120: [T, 5120], FP32 weight | 14928 | bwd | 184.669 | 80.991 |
2.280x |
| H 5120: [T, 5120], FP32 weight | 15288 | bwd | 184.877 | 82.104 |
2.252x |
| H 5120: [T, 5120], FP32 weight | 15566 | bwd | 187.501 | 82.928 |
2.261x |
| H 5120: [T, 5120], FP32 weight | 15590 | bwd | 186.606 | 83.407 |
2.237x |
| H 5120: [T, 5120], FP32 weight | 16114 | bwd | 189.966 | 85.327 |
2.226x |
| H 5120: [T, 5120], FP32 weight | 16132 | bwd | 189.838 | 85.487 |
2.221x |
| H 5120: [T, 5120], FP32 weight | 16164 | bwd | 190.407 | 85.439 |
2.229x |
| H 5120: [T, 5120], FP32 weight | 16263 | bwd | 190.485 | 86.095 |
2.213x |
| H 5120: [T, 5120], FP32 weight | 32768 | bwd | 294.692 | 162.447 |
1.814x |
| H 5120: [T, 5120], FP32 weight | 65536 | bwd | 543.749 | 313.845 |
1.733x |

**NVIDIA GB300 (152 SMs), sm_103a**; CUDA 13.4 (kernels built with nvcc
13.4), PyTorch 2.14.1+cu130, Triton 3.8.0. Latency = CUPTI kernel-active
time per call, cold L2, median of 4 x 20 calls per process.
torch.compile = fastest measured per-shape static compile (FP32 formula,
dynamic=False; minimum over every process of every formal session and
tc-only sweep of the row, each process with a fresh inductor / Triton
cache). Cake = fastest measured process of the delivered program over
every formal session of the row (the same statistic). Speedup =
torch.compile / Cake.

| Shape | T | Pass | torch.compile (us) | Cake (us) | Speedup |
|---|---:|---|---:|---:|---:|
| H 256 query: [T, 24, 256] view, strides (12288, 512, 1), FP32 weight
(rows = 24 T) | 256 | fwd | 3.040 | 3.040 | 1.000x |
| H 256 query: [T, 24, 256] view, strides (12288, 512, 1), FP32 weight
(rows = 24 T) | 1024 | fwd | 5.928 | 5.824 | 1.018x |
| H 256 query: [T, 24, 256] view, strides (12288, 512, 1), FP32 weight
(rows = 24 T) | 4096 | fwd | 16.984 | 16.856 | 1.008x |
| H 256 query: [T, 24, 256] view, strides (12288, 512, 1), FP32 weight
(rows = 24 T) | 14928 | fwd | 55.048 | 54.816 | 1.004x |
| H 256 query: [T, 24, 256] view, strides (12288, 512, 1), FP32 weight
(rows = 24 T) | 15288 | fwd | 56.288 | 55.920 | 1.007x |
| H 256 query: [T, 24, 256] view, strides (12288, 512, 1), FP32 weight
(rows = 24 T) | 15566 | fwd | 57.296 | 56.832 | 1.008x |
| H 256 query: [T, 24, 256] view, strides (12288, 512, 1), FP32 weight
(rows = 24 T) | 15590 | fwd | 57.208 | 56.896 | 1.005x |
| H 256 query: [T, 24, 256] view, strides (12288, 512, 1), FP32 weight
(rows = 24 T) | 16114 | fwd | 59.192 | 58.528 | 1.011x |
| H 256 query: [T, 24, 256] view, strides (12288, 512, 1), FP32 weight
(rows = 24 T) | 16132 | fwd | 59.088 | 58.576 | 1.009x |
| H 256 query: [T, 24, 256] view, strides (12288, 512, 1), FP32 weight
(rows = 24 T) | 16164 | fwd | 59.304 | 58.864 | 1.007x |
| H 256 query: [T, 24, 256] view, strides (12288, 512, 1), FP32 weight
(rows = 24 T) | 16263 | fwd | 59.799 | 59.120 | 1.011x |
| H 256 query: [T, 24, 256] view, strides (12288, 512, 1), FP32 weight
(rows = 24 T) | 32768 | fwd | 116.847 | 115.520 | 1.011x |
| H 256 query: [T, 24, 256] view, strides (12288, 512, 1), FP32 weight
(rows = 24 T) | 65536 | fwd | 230.617 | 227.120 | 1.015x |
| H 256 query: [T, 24, 256] view, strides (12288, 512, 1), FP32 weight
(rows = 24 T) | 256 | bwd | 13.624 | 9.208 | 1.480x |
| H 256 query: [T, 24, 256] view, strides (12288, 512, 1), FP32 weight
(rows = 24 T) | 1024 | bwd | 19.320 | 15.232 | 1.268x |
| H 256 query: [T, 24, 256] view, strides (12288, 512, 1), FP32 weight
(rows = 24 T) | 4096 | bwd | 39.297 | 32.432 | 1.212x |
| H 256 query: [T, 24, 256] view, strides (12288, 512, 1), FP32 weight
(rows = 24 T) | 14928 | bwd | 110.576 | 95.312 | 1.160x |
| H 256 query: [T, 24, 256] view, strides (12288, 512, 1), FP32 weight
(rows = 24 T) | 15288 | bwd | 115.048 | 97.399 | 1.181x |
| H 256 query: [T, 24, 256] view, strides (12288, 512, 1), FP32 weight
(rows = 24 T) | 15566 | bwd | 114.919 | 98.848 | 1.163x |
| H 256 query: [T, 24, 256] view, strides (12288, 512, 1), FP32 weight
(rows = 24 T) | 15590 | bwd | 116.863 | 99.128 | 1.179x |
| H 256 query: [T, 24, 256] view, strides (12288, 512, 1), FP32 weight
(rows = 24 T) | 16114 | bwd | 116.952 | 102.048 | 1.146x |
| H 256 query: [T, 24, 256] view, strides (12288, 512, 1), FP32 weight
(rows = 24 T) | 16132 | bwd | 116.192 | 101.992 | 1.139x |
| H 256 query: [T, 24, 256] view, strides (12288, 512, 1), FP32 weight
(rows = 24 T) | 16164 | bwd | 116.496 | 102.176 | 1.140x |
| H 256 query: [T, 24, 256] view, strides (12288, 512, 1), FP32 weight
(rows = 24 T) | 16263 | bwd | 116.079 | 102.727 | 1.130x |
| H 256 query: [T, 24, 256] view, strides (12288, 512, 1), FP32 weight
(rows = 24 T) | 32768 | bwd | 211.664 | 193.775 | 1.092x |
| H 256 query: [T, 24, 256] view, strides (12288, 512, 1), FP32 weight
(rows = 24 T) | 65536 | bwd | 380.920 | 373.447 | 1.020x |
| H 256 key: [T, 4, 256] contiguous, FP32 weight (rows = 4 T) | 256 |
fwd | 2.192 | 2.240 | 0.979x |
| H 256 key: [T, 4, 256] contiguous, FP32 weight (rows = 4 T) | 1024 |
fwd | 2.600 | 2.680 | 0.970x |
| H 256 key: [T, 4, 256] contiguous, FP32 weight (rows = 4 T) | 4096 |
fwd | 4.585 | 4.656 | 0.985x |
| H 256 key: [T, 4, 256] contiguous, FP32 weight (rows = 4 T) | 14928 |
fwd | 11.000 | 10.832 | 1.016x |
| H 256 key: [T, 4, 256] contiguous, FP32 weight (rows = 4 T) | 15288 |
fwd | 11.200 | 11.112 | 1.008x |
| H 256 key: [T, 4, 256] contiguous, FP32 weight (rows = 4 T) | 15566 |
fwd | 11.648 | 11.504 | 1.013x |
| H 256 key: [T, 4, 256] contiguous, FP32 weight (rows = 4 T) | 15590 |
fwd | 11.488 | 11.280 | 1.018x |
| H 256 key: [T, 4, 256] contiguous, FP32 weight (rows = 4 T) | 16114 |
fwd | 11.968 | 11.816 | 1.013x |
| H 256 key: [T, 4, 256] contiguous, FP32 weight (rows = 4 T) | 16132 |
fwd | 11.632 | 11.632 | 1.000x |
| H 256 key: [T, 4, 256] contiguous, FP32 weight (rows = 4 T) | 16164 |
fwd | 11.808 | 11.656 | 1.013x |
| H 256 key: [T, 4, 256] contiguous, FP32 weight (rows = 4 T) | 16263 |
fwd | 11.936 | 11.928 | 1.001x |
| H 256 key: [T, 4, 256] contiguous, FP32 weight (rows = 4 T) | 32768 |
fwd | 21.816 | 21.728 | 1.004x |
| H 256 key: [T, 4, 256] contiguous, FP32 weight (rows = 4 T) | 65536 |
fwd | 40.872 | 41.104 | 0.994x |
| H 256 key: [T, 4, 256] contiguous, FP32 weight (rows = 4 T) | 256 |
bwd | 12.720 | 5.800 | 2.193x |
| H 256 key: [T, 4, 256] contiguous, FP32 weight (rows = 4 T) | 1024 |
bwd | 13.488 | 8.000 | 1.686x |
| H 256 key: [T, 4, 256] contiguous, FP32 weight (rows = 4 T) | 4096 |
bwd | 16.536 | 13.064 | 1.266x |
| H 256 key: [T, 4, 256] contiguous, FP32 weight (rows = 4 T) | 14928 |
bwd | 27.696 | 23.944 | 1.157x |
| H 256 key: [T, 4, 256] contiguous, FP32 weight (rows = 4 T) | 15288 |
bwd | 27.920 | 24.040 | 1.161x |
| H 256 key: [T, 4, 256] contiguous, FP32 weight (rows = 4 T) | 15566 |
bwd | 28.232 | 24.104 | 1.171x |
| H 256 key: [T, 4, 256] contiguous, FP32 weight (rows = 4 T) | 15590 |
bwd | 28.312 | 24.336 | 1.163x |
| H 256 key: [T, 4, 256] contiguous, FP32 weight (rows = 4 T) | 16114 |
bwd | 28.673 | 24.872 | 1.153x |
| H 256 key: [T, 4, 256] contiguous, FP32 weight (rows = 4 T) | 16132 |
bwd | 28.880 | 24.696 | 1.169x |
| H 256 key: [T, 4, 256] contiguous, FP32 weight (rows = 4 T) | 16164 |
bwd | 28.880 | 24.792 | 1.165x |
| H 256 key: [T, 4, 256] contiguous, FP32 weight (rows = 4 T) | 16263 |
bwd | 29.024 | 24.960 | 1.163x |
| H 256 key: [T, 4, 256] contiguous, FP32 weight (rows = 4 T) | 32768 |
bwd | 48.504 | 40.032 | 1.212x |
| H 256 key: [T, 4, 256] contiguous, FP32 weight (rows = 4 T) | 65536 |
bwd | 81.583 | 73.393 | 1.112x |
| H 5120: [T, 5120], BF16 weight | 256 | fwd | 2.736 | 2.592 | 1.056x |
| H 5120: [T, 5120], BF16 weight | 1024 | fwd | 4.384 | 4.224 | 1.038x |
| H 5120: [T, 5120], BF16 weight | 4096 | fwd | 17.023 | 11.456 | 1.486x
|
| H 5120: [T, 5120], BF16 weight | 14928 | fwd | 46.639 | 44.481 |
1.049x |
| H 5120: [T, 5120], BF16 weight | 15288 | fwd | 47.800 | 45.816 |
1.043x |
| H 5120: [T, 5120], BF16 weight | 15566 | fwd | 48.600 | 46.560 |
1.044x |
| H 5120: [T, 5120], BF16 weight | 15590 | fwd | 48.584 | 46.335 |
1.049x |
| H 5120: [T, 5120], BF16 weight | 16114 | fwd | 50.112 | 48.024 |
1.043x |
| H 5120: [T, 5120], BF16 weight | 16132 | fwd | 50.408 | 48.272 |
1.044x |
| H 5120: [T, 5120], BF16 weight | 16164 | fwd | 50.448 | 48.399 |
1.042x |
| H 5120: [T, 5120], BF16 weight | 16263 | fwd | 50.504 | 48.872 |
1.033x |
| H 5120: [T, 5120], BF16 weight | 32768 | fwd | 104.895 | 95.815 |
1.095x |
| H 5120: [T, 5120], BF16 weight | 65536 | fwd | 204.175 | 190.520 |
1.072x |
| H 5120: [T, 5120], BF16 weight | 256 | bwd | 10.864 | 7.336 | 1.481x |
| H 5120: [T, 5120], BF16 weight | 1024 | bwd | 24.456 | 12.392 | 1.974x
|
| H 5120: [T, 5120], BF16 weight | 4096 | bwd | 61.376 | 26.848 | 2.286x
|
| H 5120: [T, 5120], BF16 weight | 14928 | bwd | 150.599 | 78.784 |
1.912x |
| H 5120: [T, 5120], BF16 weight | 15288 | bwd | 151.912 | 80.464 |
1.888x |
| H 5120: [T, 5120], BF16 weight | 15566 | bwd | 152.856 | 83.488 |
1.831x |
| H 5120: [T, 5120], BF16 weight | 15590 | bwd | 153.120 | 81.904 |
1.870x |
| H 5120: [T, 5120], BF16 weight | 16114 | bwd | 155.016 | 84.759 |
1.829x |
| H 5120: [T, 5120], BF16 weight | 16132 | bwd | 155.033 | 85.160 |
1.820x |
| H 5120: [T, 5120], BF16 weight | 16164 | bwd | 155.456 | 84.712 |
1.835x |
| H 5120: [T, 5120], BF16 weight | 16263 | bwd | 155.727 | 85.033 |
1.831x |
| H 5120: [T, 5120], BF16 weight | 32768 | bwd | 249.648 | 162.703 |
1.534x |
| H 5120: [T, 5120], BF16 weight | 65536 | bwd | 455.848 | 313.143 |
1.456x |
| H 5120: [T, 5120], FP32 weight | 256 | fwd | 3.376 | 2.616 | 1.291x |
| H 5120: [T, 5120], FP32 weight | 1024 | fwd | 4.512 | 4.328 | 1.043x |
| H 5120: [T, 5120], FP32 weight | 4096 | fwd | 17.432 | 11.592 | 1.504x
|
| H 5120: [T, 5120], FP32 weight | 14928 | fwd | 46.136 | 43.992 |
1.049x |
| H 5120: [T, 5120], FP32 weight | 15288 | fwd | 46.832 | 45.032 |
1.040x |
| H 5120: [T, 5120], FP32 weight | 15566 | fwd | 47.864 | 45.632 |
1.049x |
| H 5120: [T, 5120], FP32 weight | 15590 | fwd | 47.912 | 46.104 |
1.039x |
| H 5120: [T, 5120], FP32 weight | 16114 | fwd | 49.704 | 47.448 |
1.048x |
| H 5120: [T, 5120], FP32 weight | 16132 | fwd | 49.783 | 47.288 |
1.053x |
| H 5120: [T, 5120], FP32 weight | 16164 | fwd | 50.008 | 47.408 |
1.055x |
| H 5120: [T, 5120], FP32 weight | 16263 | fwd | 50.096 | 47.432 |
1.056x |
| H 5120: [T, 5120], FP32 weight | 32768 | fwd | 101.672 | 95.072 |
1.069x |
| H 5120: [T, 5120], FP32 weight | 65536 | fwd | 196.073 | 187.928 |
1.043x |
| H 5120: [T, 5120], FP32 weight | 256 | bwd | 10.896 | 7.352 | 1.482x |
| H 5120: [T, 5120], FP32 weight | 1024 | bwd | 25.600 | 12.320 | 2.078x
|
| H 5120: [T, 5120], FP32 weight | 4096 | bwd | 65.136 | 27.264 | 2.389x
|
| H 5120: [T, 5120], FP32 weight | 14928 | bwd | 174.248 | 79.072 |
2.204x |
| H 5120: [T, 5120], FP32 weight | 15288 | bwd | 175.487 | 80.544 |
2.179x |
| H 5120: [T, 5120], FP32 weight | 15566 | bwd | 176.391 | 83.416 |
2.115x |
| H 5120: [T, 5120], FP32 weight | 15590 | bwd | 176.176 | 81.568 |
2.160x |
| H 5120: [T, 5120], FP32 weight | 16114 | bwd | 177.382 | 84.600 |
2.097x |
| H 5120: [T, 5120], FP32 weight | 16132 | bwd | 177.632 | 85.432 |
2.079x |
| H 5120: [T, 5120], FP32 weight | 16164 | bwd | 177.736 | 84.984 |
2.091x |
| H 5120: [T, 5120], FP32 weight | 16263 | bwd | 178.104 | 85.280 |
2.088x |
| H 5120: [T, 5120], FP32 weight | 32768 | bwd | 278.736 | 162.432 |
1.716x |
| H 5120: [T, 5120], FP32 weight | 65536 | bwd | 511.993 | 312.256 |
1.640x |

**NVIDIA R200 (216 SMs), sm_107a**: rows will be added when the
measurement completes.

Besides these shapes, Cake ships this deterministic module for the
earlier hidden sizes from 512 to 6144, plus a non-deterministic training
RMSNorm. The deterministic family ships on sm_100a, sm_103a and sm_107a.

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [8826c9f](https://github.com/flashinfer-ai/flashinfer/commit/8826c9fa3be818b84aa1ba47dbdc29841b7c5f13)

- **作者**: eigen
- **时间**: 2026-11-01T10:27:10Z
- **提交信息**: perf(cake_fmha): faster FP8 paged context for short-KV and one-wave launches (#8184)

Cake paged context (prefill) attention in `flashinfer.cake_fmha` has
three variants by data type, all on a paged KV cache: BF16, FP8 (FP8
Q/K/V with FP8 output), and FP8 Q with NVFP4 KV. This PR changes only
the FP8 variant. On sm_103a (GB300), the one-stage programs used for
short KV used to read the first tile's sequence lengths and the first
entries of its K and V page-table rows one after another, after the
kernel setup. They now issue these reads at kernel entry, in parallel
with the setup, which shortens the chain of dependent reads before the
first K tile arrives. GB300 launches keep their programs. On sm_100a
(B200), launches that fit in one wave of CTAs (at most 64 tiles for the
programs that pack one or two query heads into a tile) and run one query
stage per tile now use new one-wave one-stage builds. One-wave launches
whose one-stage tiles also fit in one wave now run one query stage per
tile instead of two. Compared with the previous Cake version on
FlashInfer main, the largest gains are on B200 one-wave shapes. FP8,
B=2, q=256, kv=1500, heads 32/32, page 64 goes from 27.08 to 21.09 µs
(1.284x). FP8, B=1, q=200, kv=1024, heads 32/4, page 16 goes from
18.27–18.50 µs to 15.20–15.26 µs on three machines (1.200x to 1.215x).
On GB300, FP8, B=16, q=32, kv=128, heads 32/4, page 64 goes from 6.82 to
6.34 µs (1.076x), and FP8, B=1, q=32, kv=128, heads 32/4, page 64 goes
from 5.70–5.71 µs to 5.34 µs on three machines (1.060x to 1.066x).

Measured on NVIDIA B200 (sm_100a) and NVIDIA GB300 (sm_103a) with CUDA
13.0. "Previous" is the Cake version on FlashInfer main, and "this PR"
is the Cake programs in this branch. Each time is the median over 5
memory layouts of that layout's median of 6 rounds, with a cold L2. The
sweep rows marked † use 2 layouts instead of 5. Speedup is previous /
this PR: the median over layouts, with the minimum layout in
parentheses. trtllm-gen is the TensorRT-LLM generated kernel on the same
shape, shown for reference.

These are the 44 shapes tracked for this kernel, across all three
variants, measured on one B200 machine and two GB300 machines:

| Shape (paged KV, head dim 128) | B200 previous (µs) | B200 this PR
(µs) | B200 speedup | B200 trtllm-gen (µs) | GB300 previous (µs) | GB300
this PR (µs) | GB300 speedup | GB300 trtllm-gen (µs) |
|---|---:|---:|---|---:|---:|---:|---|---:|
| BF16, B=1, q=8192, kv=8192, heads 64/8, page 16 | 888.49 | 888.40 |
1.000x (min 0.998x) | 1060.40 | 611.50 | 610.90 | 1.000x (min 0.998x) |
670.68 |
| BF16, B=4, q=511, kv=2047, heads 10/2, page 32 | 34.78 | 34.85 |
1.000x (min 0.998x) | 37.82 | 27.07 | 27.07 | 1.000x (min 1.000x) |
30.34 |
| BF16, B=128, q=64, kv=2048, heads 32/4, page 16 | 232.25 | 232.25 |
1.000x (min 0.999x) | 990.30 | 171.94 | 172.08 | 0.999x (min 0.999x) |
717.95 |
| FP8, B=256, q=32, kv=1024, heads 32/4, page 64 | 109.79 | 109.74 |
1.001x (min 1.000x) | 774.13 | 82.78 | 82.75 | 1.000x (min 1.000x) |
513.73 |
| FP8 Q / NVFP4 KV, B=4, q=511, kv=2047, heads 32/4, page 16 | 57.66 |
57.63 | 1.000x (min 0.998x) | 61.68 | 51.27 | 51.27 | 1.000x (min
1.000x) | 52.03 |
| BF16, B=4, q=257, kv=1024, heads 10/2, page 1024 | 20.86 | 20.80 |
1.003x (min 0.996x) | 23.14 | 16.93 | 16.93 | 1.000x (min 1.000x) |
18.43 |
| FP8, B=256, q=64, kv=1024, heads 32/4, page 64 | 202.35 | 202.38 |
1.000x (min 0.999x) | 775.02 | 146.59 | 146.54 | 1.001x (min 0.999x) |
524.56 |
| FP8, B=128, q=128, kv=1024, heads 32/8, page 64 | 203.38 | 203.36 |
1.000x (min 1.000x) | 406.56 | 147.04 | 146.98 | 1.001x (min 0.999x) |
281.50 |
| FP8, B=256, q=32, kv=1024, heads 128/1, page 64 | 387.97 | 387.94 |
1.000x (min 1.000x) | 3074.55 | 267.47 | 267.49 | 1.000x (min 1.000x) |
1984.55 |
| FP8, B=16, q=256, kv=2048, heads 32/32, page 64 | 116.24 | 116.26 |
1.000x (min 0.999x) | 116.45 | 87.17 | 87.17 | 1.000x (min 1.000x) |
94.06 |
| FP8, B=256, q=32, kv=1024, heads 32/4, page 16 | 110.24 | 110.26 |
1.000x (min 1.000x) | 770.95 | 84.99 | 84.99 | 1.000x (min 1.000x) |
534.91 |
| FP8, B=256, q=32, kv=1024, heads 32/4, page 16, device scales | 110.69
| 110.62 | 1.001x (min 1.000x) | 792.66 | 84.70 | 84.67 | 1.000x (min
1.000x) | 568.67 |
| FP8, B=2, q=300, kv=1500, heads 32/4, page 16 | 25.34 | 25.38 | 1.000x
(min 0.999x) | 26.30 | 18.64 | 18.66 | 1.000x (min 0.999x) | 19.71 |
| FP8, B=256, q=32, kv=1024, heads 32/4, page 64, device scales | 110.10
| 110.06 | 1.000x (min 1.000x) | 780.18 | 82.91 | 82.91 | 1.000x (min
1.000x) | 551.39 |
| FP8 Q / NVFP4 KV, B=4, q=511, kv=2047, heads 32/4, page 16, device
scales | 57.74 | 57.73 | 1.000x (min 1.000x) | 76.56 | 51.23 | 51.25 |
1.000x (min 1.000x) | 87.26 |
| BF16, B=1, q=64, kv=16384, heads 32/4, page 16 | 195.71 | 195.68 |
1.000x (min 1.000x) | 215.36 | 157.76 | 157.76 | 1.000x (min 1.000x) |
191.55 |
| BF16, B=one wave of CTAs (18 on B200, 19 on GB300), q=64, kv=2048,
heads 32/4, page 16 | 36.78 | 36.80 | 1.000x (min 0.999x) | 133.10 |
32.70 | 32.70 | 1.000x (min 1.000x) | 107.90 |
| FP8, B=1, q=300, kv=1500, heads 32/4, page 16 | 24.78 | 24.80 | 1.000x
(min 0.999x) | 25.41 | 18.46 | 18.46 | 1.000x (min 1.000x) | 19.17 |
| FP8, B=2, q=300, kv=3000, heads 32/4, page 16 | 41.89 | 41.89 | 1.000x
(min 0.999x) | 45.09 | 31.04 | 31.04 | 1.000x (min 0.999x) | 33.38 |
| FP8, B=2, q=300, kv=6000, heads 32/4, page 16 | 71.46 | 71.44 | 1.000x
(min 0.999x) | 80.54 | 54.27 | 54.27 | 1.000x (min 1.000x) | 58.50 |
| FP8, B=2, q=128, kv=1500, heads 32/4, page 16 | 20.86 | 20.32 | 1.028x
(min 1.024x) | 24.45 | 15.81 | 15.81 | 1.000x (min 0.998x) | 18.78 |
| FP8, B=16, q=256, kv=4096, heads 32/32, page 64 | 205.79 | 205.78 |
1.000x (min 1.000x) | 218.16 | 156.99 | 156.99 | 1.000x (min 1.000x) |
169.34 |
| FP8, B=1, q=32, kv=16384, heads 32/4, page 64 | 44.58 | 44.58 | 1.000x
(min 1.000x) | 187.01 | 39.25 | 39.25 | 1.000x (min 1.000x) | 137.38 |
| FP8, B=1, q=32, kv=4096, heads 32/4, page 64 | 27.09 | 27.10 | 1.000x
(min 0.999x) | 51.42 | 23.65 | 23.65 | 1.000x (min 0.999x) | 37.89 |
| FP8, B=1, q=32, kv=8192, heads 32/4, page 64 | 33.28 | 33.28 | 1.000x
(min 1.000x) | 96.93 | 29.50 | 29.50 | 1.000x (min 1.000x) | 71.39 |
| FP8, B=1, q=32, kv=32768, heads 32/4, page 64 | 59.65 | 59.65 | 1.000x
(min 0.999x) | 366.78 | 53.09 | 53.09 | 1.000x (min 1.000x) | 274.94 |
| FP8, B=2, q=32, kv=16384, heads 32/4, page 64 | 48.22 | 48.22 | 1.000x
(min 0.999x) | 188.64 | 41.82 | 41.82 | 1.000x (min 1.000x) | 140.83 |
| FP8, B=4, q=32, kv=16384, heads 32/4, page 64 | 54.82 | 54.82 | 1.000x
(min 1.000x) | 191.65 | 48.88 | 48.90 | 1.000x (min 1.000x) | 142.91 |
| FP8, B=8, q=32, kv=8192, heads 32/4, page 64 | 47.74 | 47.74 | 1.000x
(min 0.999x) | 197.50 | 42.50 | 42.50 | 1.000x (min 1.000x) | 146.16 |
| FP8, B=1, q=128, kv=16384, heads 32/4, page 64 | 53.18 | 53.17 |
1.000x (min 1.000x) | 188.48 | 45.66 | 45.66 | 1.000x (min 1.000x) |
138.08 |
| FP8, B=1, q=512, kv=16384, heads 32/4, page 64 | 115.58 | 115.58 |
1.000x (min 0.999x) | 194.72 | 92.96 | 92.96 | 1.000x (min 1.000x) |
140.29 |
| FP8, B=2, q=300, kv=2000, heads 32/4, page 16 | 29.70 | 29.71 | 1.000x
(min 0.999x) | 32.70 | 22.86 | 22.85 | 1.000x (min 1.000x) | 24.51 |
| FP8, B=1, q=300, kv=3000, heads 32/4, page 16 | 31.04 | 31.04 | 1.000x
(min 1.000x) | 43.62 | 27.10 | 27.10 | 1.000x (min 1.000x) | 32.13 |
| FP8, B=16, q=256, kv=3072, heads 32/32, page 64 | 161.66 | 161.70 |
1.000x (min 0.999x) | 166.14 | 122.27 | 122.24 | 1.000x (min 0.999x) |
132.77 |
| FP8, B=1, q=32, kv=2048, heads 32/4, page 64 | 21.02 | 21.02 | 1.000x
(min 1.000x) | 28.32 | 18.78 | 18.77 | 1.000x (min 1.000x) | 21.22 |
| FP8, B=1, q=32, kv=12000, heads 32/4, page 64 | 39.84 | 39.84 | 1.000x
(min 1.000x) | 139.89 | 34.53 | 34.53 | 1.000x (min 1.000x) | 102.56 |
| FP8, B=3, q=32, kv=16384, heads 32/4, page 64 | 52.77 | 52.77 | 1.000x
(min 1.000x) | 189.70 | 47.20 | 47.20 | 1.000x (min 1.000x) | 140.67 |
| FP8, B=16, q=32, kv=16384, heads 32/4, page 64 | 121.98 | 121.92 |
1.001x (min 1.000x) | 761.92 | 102.11 | 102.11 | 1.000x (min 1.000x) |
541.92 |
| FP8, B=1, q=256, kv=16384, heads 32/4, page 64 | 70.19 | 70.17 |
1.000x (min 0.999x) | 193.22 | 58.24 | 58.22 | 1.000x (min 1.000x) |
139.34 |
| FP8, B=1, q=32, kv=16384, heads 32/8, page 64 | 45.09 | 45.12 | 1.000x
(min 0.999x) | 189.34 | 40.32 | 40.32 | 1.000x (min 0.999x) | 147.04 |
| FP8, B=1, q=32, kv=16384, heads 64/8, page 64 | 47.47 | 47.42 | 1.000x
(min 1.000x) | 188.51 | 41.66 | 41.66 | 1.000x (min 1.000x) | 139.39 |
| FP8, B=1, q=32, kv=16384, heads 16/2, page 64 | 43.50 | 43.52 | 1.000x
(min 0.999x) | 187.04 | 38.05 | 38.05 | 1.000x (min 1.000x) | 138.85 |
| FP8, B=1, q=32, kv=16384, heads 32/4, page 16 | 44.86 | 44.90 | 1.000x
(min 0.999x) | 189.85 | 39.94 | 39.94 | 1.000x (min 1.000x) | 144.93 |
| FP8, B=1, q=256, kv=8192, heads 32/32, page 64 | 47.33 | 47.33 |
1.000x (min 0.999x) | 103.94 | 41.79 | 41.79 | 1.000x (min 1.000x) |
81.22 |

These are the FP8 shapes this PR targets, plus FP8, B=16, q=256,
kv=2048, heads 32/32, page 64, a tracked shape whose program this PR
does not change. Each is measured on three machines of its GPU and
labelled in the machine column, with B200-2 measured twice:

| Shape (paged KV, head dim 128) | GPU | machine | previous (µs) | this
PR (µs) | speedup | trtllm-gen (µs) |
|---|---|---|---:|---:|---|---:|
| FP8, B=1, q=1, kv=16, heads 8/1, page 16 | B200 | B200-1 | 6.83 | 6.11
| 1.118x (min 1.118x) | 6.53 |
| FP8, B=1, q=1, kv=16, heads 8/1, page 16 | B200 | B200-2 | 7.18 | 6.48
| 1.109x (min 1.109x) | 6.56 |
| FP8, B=1, q=1, kv=16, heads 8/1, page 16 | B200 | B200-2 (rerun) |
7.18 | 6.48 | 1.109x (min 1.109x) | 6.56 |
| FP8, B=1, q=1, kv=16, heads 8/1, page 16 | B200 | B200-3 | 6.43 | 5.89
| 1.092x (min 1.089x) | 6.50 |
| FP8, B=1, q=200, kv=1024, heads 32/4, page 16 | B200 | B200-1 | 18.27
| 15.20 | 1.200x (min 1.198x) | 18.40 |
| FP8, B=1, q=200, kv=1024, heads 32/4, page 16 | B200 | B200-2 | 18.50
| 15.26 | 1.212x (min 1.211x) | 18.40 |
| FP8, B=1, q=200, kv=1024, heads 32/4, page 16 | B200 | B200-2 (rerun)
| 18.46 | 15.20 | 1.215x (min 1.214x) | 18.43 |
| FP8, B=1, q=200, kv=1024, heads 32/4, page 16 | B200 | B200-3 | 18.30
| 15.23 | 1.202x (min 1.202x) | 18.43 |
| FP8, B=1, q=300, kv=300, heads 32/4, page 16 | B200 | B200-1 | 10.58 |
8.86 | 1.194x (min 1.191x) | 10.05 |
| FP8, B=1, q=300, kv=300, heads 32/4, page 16 | B200 | B200-2 | 10.66 |
8.99 | 1.186x (min 1.184x) | 10.08 |
| FP8, B=1, q=300, kv=300, heads 32/4, page 16 | B200 | B200-2 (rerun) |
10.70 | 9.02 | 1.188x (min 1.186x) | 10.08 |
| FP8, B=1, q=300, kv=300, heads 32/4, page 16 | B200 | B200-3 | 10.56 |
8.83 | 1.196x (min 1.191x) | 10.05 |
| FP8, B=2, q=129, kv=100, heads 16/2, page 32 | B200 | B200-1 | 7.49 |
6.51 | 1.149x (min 1.142x) | 7.33 |
| FP8, B=2, q=129, kv=100, heads 16/2, page 32 | B200 | B200-2 | 7.65 |
6.46 | 1.180x (min 1.177x) | 7.36 |
| FP8, B=2, q=129, kv=100, heads 16/2, page 32 | B200 | B200-2 (rerun) |
7.65 | 6.46 | 1.183x (min 1.182x) | 7.36 |
| FP8, B=2, q=129, kv=100, heads 16/2, page 32 | B200 | B200-3 | 7.49 |
6.50 | 1.149x (min 1.142x) | 7.33 |
| FP8, B=3, q=1, kv=127, heads 32/4, page 16 | B200 | B200-1 | 6.82 |
6.18 | 1.104x (min 1.093x) | 7.10 |
| FP8, B=3, q=1, kv=127, heads 32/4, page 16 | B200 | B200-2 | 6.86 |
6.43 | 1.073x (min 1.067x) | 7.01 |
| FP8, B=3, q=1, kv=127, heads 32/4, page 16 | B200 | B200-2 (rerun) |
6.86 | 6.43 | 1.073x (min 1.067x) | 6.98 |
| FP8, B=3, q=1, kv=127, heads 32/4, page 16 | B200 | B200-3 | 6.69 |
6.22 | 1.072x (min 1.069x) | 7.04 |
| FP8, B=3, q=1, kv=129, heads 8/1, page 32 | B200 | B200-1 | 8.10 |
7.09 | 1.143x (min 1.138x) | 8.03 |
| FP8, B=3, q=1, kv=129, heads 8/1, page 32 | B200 | B200-2 | 8.64 |
7.62 | 1.135x (min 1.131x) | 8.06 |
| FP8, B=3, q=1, kv=129, heads 8/1, page 32 | B200 | B200-2 (rerun) |
8.64 | 7.62 | 1.134x (min 1.131x) | 8.03 |
| FP8, B=3, q=1, kv=129, heads 8/1, page 32 | B200 | B200-3 | 8.08 |
7.07 | 1.140x (min 1.137x) | 8.03 |
| FP8, B=16, q=256, kv=2048, heads 32/32, page 64 | B200 | B200-1 |
116.29 | 116.32 | 0.999x (min 0.998x) | 116.59 |
| FP8, B=16, q=256, kv=2048, heads 32/32, page 64 | B200 | B200-2 |
115.01 | 114.96 | 1.000x (min 0.999x) | 116.11 |
| FP8, B=16, q=256, kv=2048, heads 32/32, page 64 | B200 | B200-2
(rerun) | 115.68 | 115.68 | 1.000x (min 1.000x) | 115.74 |
| FP8, B=16, q=256, kv=2048, heads 32/32, page 64 | B200 | B200-3 |
115.92 | 115.94 | 1.000x (min 0.999x) | 116.61 |
| FP8, B=1, q=32, kv=128, heads 32/16, page 64 | GB300 | GB300-1 | 5.86
| 5.50 | 1.058x (min 1.058x) | 5.86 |
| FP8, B=1, q=32, kv=128, heads 32/16, page 64 | GB300 | GB300-2 | 5.84
| 5.50 | 1.058x (min 1.058x) | 5.86 |
| FP8, B=1, q=32, kv=128, heads 32/16, page 64 | GB300 | GB300-3 | 5.82
| 5.50 | 1.058x (min 1.058x) | 5.89 |
| FP8, B=1, q=32, kv=128, heads 32/4, page 16 | GB300 | GB300-1 | 5.76 |
5.50 | 1.041x (min 1.034x) | 5.68 |
| FP8, B=1, q=32, kv=128, heads 32/4, page 16 | GB300 | GB300-2 | 5.78 |
5.50 | 1.047x (min 1.040x) | 5.70 |
| FP8, B=1, q=32, kv=128, heads 32/4, page 16 | GB300 | GB300-3 | 5.74 |
5.50 | 1.041x (min 1.037x) | 5.70 |
| FP8, B=1, q=32, kv=128, heads 32/4, page 64 | GB300 | GB300-1 | 5.70 |
5.34 | 1.066x (min 1.060x) | 5.70 |
| FP8, B=1, q=32, kv=128, heads 32/4, page 64 | GB300 | GB300-2 | 5.71 |
5.34 | 1.066x (min 1.053x) | 5.70 |
| FP8, B=1, q=32, kv=128, heads 32/4, page 64 | GB300 | GB300-3 | 5.70 |
5.34 | 1.060x (min 1.060x) | 5.70 |
| FP8, B=1, q=32, kv=128, heads 32/8, page 64 | GB300 | GB300-1 | 5.79 |
5.47 | 1.058x (min 1.058x) | 5.79 |
| FP8, B=1, q=32, kv=128, heads 32/8, page 64 | GB300 | GB300-2 | 5.82 |
5.47 | 1.064x (min 1.058x) | 5.82 |
| FP8, B=1, q=32, kv=128, heads 32/8, page 64 | GB300 | GB300-3 | 5.82 |
5.47 | 1.064x (min 1.058x) | 5.82 |
| FP8, B=1, q=64, kv=128, heads 32/4, page 16 | GB300 | GB300-1 | 5.82 |
5.57 | 1.046x (min 1.040x) | 5.98 |
| FP8, B=1, q=64, kv=128, heads 32/4, page 16 | GB300 | GB300-2 | 5.86 |
5.57 | 1.046x (min 1.043x) | 5.98 |
| FP8, B=1, q=64, kv=128, heads 32/4, page 16 | GB300 | GB300-3 | 5.86 |
5.57 | 1.046x (min 1.046x) | 5.98 |

<details><summary>B200 long-KV: 39 FP8 shapes with kv of 2048 or more
that move to the new one-wave builds</summary>

Each shape was measured on one B200 machine. 38 are faster than the
previous version. One is unchanged within the run-to-run band: FP8,
B=16, q=4, kv=16384, heads 64/8, page 16, at 1.001x. The largest gain is
FP8, B=8, q=32, kv=2048, heads 64/8, page 16, from 26.82 to 26.35 µs
(1.019x).

| Shape (paged KV, head dim 128) | GPU | machine | previous (µs) | this
PR (µs) | speedup | trtllm-gen (µs) |
|---|---|---|---:|---:|---|---:|
| FP8, B=1, q=128, kv=2048, heads 64/8, page 16 | B200 | B200-3 | 24.93
| 24.74 | 1.006x (min 1.004x) | 29.70 |
| FP8, B=2, q=128, kv=2048, heads 32/4, page 16 | B200 | B200-3 | 25.12
| 24.93 | 1.006x (min 1.005x) | 30.66 |
| FP8, B=2, q=128, kv=2048, heads 32/8, page 16 | B200 | B200-3 | 25.25
| 25.09 | 1.006x (min 1.005x) | 31.07 |
| FP8, B=2, q=128, kv=2048, heads 32/16, page 16 | B200 | B200-2 | 25.50
| 25.12 | 1.014x (min 1.014x) | 31.36 |
| FP8, B=2, q=128, kv=2048, heads 32/32, page 16 | B200 | B200-3 | 25.92
| 25.60 | 1.012x (min 1.011x) | 32.10 |
| FP8, B=4, q=128, kv=2048, heads 16/2, page 16 | B200 | B200-3 | 25.09
| 24.75 | 1.014x (min 1.012x) | 30.62 |
| FP8, B=8, q=16, kv=2048, heads 64/8, page 16 | B200 | B200-3 | 26.53 |
26.14 | 1.016x (min 1.013x) | 105.66 |
| FP8, B=8, q=32, kv=2048, heads 64/8, page 16 | B200 | B200-2 | 26.82 |
26.35 | 1.019x (min 1.013x) | 108.77 |
| FP8, B=16, q=4, kv=2048, heads 32/8, page 16 | B200 | B200-2 | 28.90 |
28.64 | 1.009x (min 1.007x) | 106.34 |
| FP8, B=16, q=4, kv=2048, heads 64/8, page 16 | B200 | B200-3 | 28.99 |
28.67 | 1.010x (min 1.009x) | 180.29 |
| FP8, B=16, q=16, kv=2048, heads 32/4, page 16 | B200 | B200-2 | 26.40
| 26.08 | 1.012x (min 1.010x) | 108.19 |
| FP8, B=16, q=16, kv=2048, heads 32/8, page 16 | B200 | B200-3 | 29.22
| 28.86 | 1.011x (min 1.011x) | 108.35 |
| FP8, B=16, q=16, kv=2048, heads 64/8, page 16 | B200 | B200-2 | 29.15
| 28.80 | 1.012x (min 1.011x) | 185.54 |
| FP8, B=16, q=32, kv=2048, heads 32/4, page 16 | B200 | B200-3 | 26.74
| 26.32 | 1.016x (min 1.016x) | 108.48 |
| FP8, B=16, q=32, kv=2048, heads 32/8, page 16 | B200 | B200-3 | 29.34
| 28.96 | 1.013x (min 1.011x) | 109.54 |
| FP8, B=32, q=4, kv=2048, heads 32/4, page 16 | B200 | B200-3 | 29.18 |
28.90 | 1.010x (min 1.009x) | 181.15 |
| FP8, B=32, q=16, kv=2048, heads 16/2, page 16 | B200 | B200-3 | 26.50
| 26.14 | 1.013x (min 1.013x) | 108.35 |
| FP8, B=32, q=16, kv=2048, heads 32/4, page 16 | B200 | B200-2 | 29.28
| 28.94 | 1.011x (min 1.009x) | 187.22 |
| FP8, B=32, q=32, kv=2048, heads 16/2, page 16 | B200 | B200-2 | 26.90
| 26.50 | 1.014x (min 1.013x) | 109.89 |
| FP8, B=64, q=4, kv=2048, heads 16/2, page 16 | B200 | B200-2 | 28.90 |
28.66 | 1.008x (min 1.007x) | 184.62 |
| FP8, B=64, q=16, kv=2048, heads 16/2, page 16 | B200 | B200-3 | 29.54
| 29.17 | 1.012x (min 1.012x) | 186.91 |
| FP8, B=16, q=4, kv=4096, heads 32/8, page 16 | B200 | B200-2 | 50.91 |
50.72 | 1.004x (min 1.003x) | 200.80 |
| FP8, B=16, q=4, kv=4096, heads 64/8, page 16 | B200 | B200-3 | 51.23 |
50.98 | 1.005x (min 1.004x) | 343.79 |
| FP8, B=16, q=16, kv=4096, heads 32/8, page 16 | B200 | B200-3 | 51.30
| 51.01 | 1.005x (min 1.005x) | 204.06 |
| FP8, B=16, q=16, kv=4096, heads 64/8, page 16 | B200 | B200-2 | 51.17
| 50.83 | 1.007x (min 1.006x) | 352.03 |
| FP8, B=16, q=32, kv=4096, heads 32/8, page 16 | B200 | B200-3 | 51.49
| 51.18 | 1.006x (min 1.004x) | 206.34 |
| FP8, B=32, q=4, kv=4096, heads 32/4, page 16 | B200 | B200-3 | 51.42 |
51.17 | 1.005x (min 1.005x) | 344.43 |
| FP8, B=32, q=16, kv=4096, heads 32/4, page 16 | B200 | B200-2 | 51.25
| 50.91 | 1.006x (min 1.005x) | 358.22 |
| FP8, B=64, q=4, kv=4096, heads 16/2, page 16 | B200 | B200-3 | 51.54 |
51.27 | 1.005x (min 1.004x) | 350.11 |
| FP8, B=64, q=16, kv=4096, heads 16/2, page 16 | B200 | B200-3 | 51.74
| 51.39 | 1.007x (min 1.006x) | 357.01 |
| FP8, B=16, q=4, kv=16384, heads 32/8, page 16 | B200 | B200-2 | 167.31
| 167.09 | 1.001x (min 1.000x) | 757.68 |
| FP8, B=16, q=4, kv=16384, heads 64/8, page 16 | B200 | B200-2 | 167.12
| 166.98 | 1.001x (min 1.001x) | 1335.85 |
| FP8, B=16, q=16, kv=16384, heads 32/8, page 16 | B200 | B200-3 |
166.98 | 166.78 | 1.001x (min 1.001x) | 769.31 |
| FP8, B=16, q=16, kv=16384, heads 64/8, page 16 | B200 | B200-3 |
167.20 | 166.91 | 1.002x (min 1.001x) | 1376.26 |
| FP8, B=16, q=32, kv=16384, heads 32/8, page 16 | B200 | B200-2 |
167.46 | 167.23 | 1.002x (min 1.001x) | 791.23 |
| FP8, B=32, q=4, kv=16384, heads 32/4, page 16 | B200 | B200-2 | 167.36
| 167.20 | 1.001x (min 1.001x) | 1357.48 |
| FP8, B=32, q=16, kv=16384, heads 32/4, page 16 | B200 | B200-3 |
167.46 | 167.14 | 1.002x (min 1.002x) | 1414.39 |
| FP8, B=64, q=4, kv=16384, heads 16/2, page 16 | B200 | B200-3 | 167.22
| 167.03 | 1.001x (min 1.001x) | 1374.61 |
| FP8, B=64, q=16, kv=16384, heads 16/2, page 16 | B200 | B200-2 |
167.63 | 167.33 | 1.002x (min 1.002x) | 1448.39 |

</details>

<details><summary>FP8 sweep: 181 shapes that run a changed program (105
measured on B200, 87 on GB300)</summary>

**B200 (105 shapes).** The table lists two groups:
- The 24 sweep shapes whose launch moves to a different program,
measured over 5 layouts.
- 81 representative shapes of the moved launch classes, marked † and
measured over 2 layouts.

All 105 are faster than the previous version.

**GB300 (87 shapes).** The table lists the sweep shapes that run the
changed one-stage short-KV programs. 80 are faster than the previous
version. 7 are unchanged within the run-to-run band; the lowest is FP8,
B=16, q=32, kv=2048, heads 32/16, page 64, at 0.998x.

None is slower on either GPU. All other sweep shapes keep their previous
program on both GPUs and are not listed. '-' marks a GPU on which the
shape was not measured.

Shapes with more query tokens than keys (for example q=129, kv=100) time
a fully masked workload. The largest gain among them is FP8, B=1, q=129,
kv=100, heads 32/16, page 32, from 8.58 to 6.59 µs (1.301x).

| Shape (paged KV, head dim 128) | B200 previous (µs) | B200 this PR
(µs) | B200 speedup | B200 trtllm-gen (µs) | GB300 previous (µs) | GB300
this PR (µs) | GB300 speedup | GB300 trtllm-gen (µs) |
|---|---:|---:|---|---:|---:|---:|---|---:|
| FP8, B=1, q=32, kv=128, heads 32/4, page 64 | - | - | - | - | 5.82 |
5.44 | 1.071x (min 1.064x) | 5.82 |
| FP8, B=1, q=32, kv=128, heads 32/8, page 64 | - | - | - | - | 5.82 |
5.44 | 1.065x (min 1.058x) | 5.79 |
| FP8, B=1, q=32, kv=128, heads 32/16, page 64 | - | - | - | - | 5.86 |
5.54 | 1.055x (min 1.052x) | 5.86 |
| FP8, B=1, q=32, kv=256, heads 32/4, page 64 | - | - | - | - | 6.53 |
6.14 | 1.062x (min 1.062x) | 6.66 |
| FP8, B=1, q=32, kv=256, heads 32/8, page 64 | - | - | - | - | 6.82 |
6.40 | 1.065x (min 1.060x) | 6.78 |
| FP8, B=1, q=32, kv=256, heads 32/16, page 64 | - | - | - | - | 6.59 |
6.18 | 1.067x (min 1.059x) | 6.82 |
| FP8, B=1, q=32, kv=384, heads 32/4, page 64 | - | - | - | - | 7.23 |
6.85 | 1.056x (min 1.051x) | 7.58 |
| FP8, B=1, q=32, kv=384, heads 32/8, page 64 | - | - | - | - | 7.26 |
6.88 | 1.056x (min 1.056x) | 7.68 |
| FP8, B=1, q=32, kv=384, heads 32/16, page 64 | - | - | - | - | 7.18 |
6.78 | 1.057x (min 1.052x) | 7.74 |
| FP8, B=1, q=32, kv=384, heads 32/32, page 64 | - | - | - | - | 7.33 |
7.01 | 1.046x (min 1.045x) | 7.90 |
| FP8, B=1, q=32, kv=512, heads 32/4, page 64 | - | - | - | - | 7.90 |
7.55 | 1.047x (min 1.042x) | 8.54 |
| FP8, B=1, q=32, kv=512, heads 32/8, page 64 | - | - | - | - | 8.13 |
7.81 | 1.045x (min 1.039x) | 8.70 |
| FP8, B=1, q=32, kv=512, heads 32/16, page 64 | - | - | - | - | 8.03 |
7.74 | 1.041x (min 1.037x) | 8.93 |
| FP8, B=1, q=32, kv=512, heads 32/32, page 64 | - | - | - | - | 8.35 |
8.06 | 1.036x (min 1.036x) | 9.34 |
| FP8, B=1, q=32, kv=768, heads 32/4, page 64 | - | - | - | - | 9.50 |
9.34 | 1.015x (min 1.014x) | 10.62 |
| FP8, B=1, q=32, kv=768, heads 32/8, page 64 | - | - | - | - | 9.66 |
9.57 | 1.013x (min 1.007x) | 10.98 |
| FP8, B=1, q=32, kv=768, heads 32/16, page 64 | - | - | - | - | 9.60 |
9.47 | 1.017x (min 1.010x) | 11.26 |
| FP8, B=1, q=32, kv=768, heads 32/32, page 64 | - | - | - | - | 9.89 |
9.76 | 1.013x (min 1.010x) | 11.65 |
| FP8, B=1, q=32, kv=1024, heads 32/4, page 64 | - | - | - | - | 11.01 |
10.88 | 1.015x (min 1.006x) | 12.67 |
| FP8, B=1, q=32, kv=1024, heads 32/8, page 64 | - | - | - | - | 11.20 |
11.01 | 1.017x (min 1.014x) | 12.96 |
| FP8, B=1, q=32, kv=1024, heads 32/16, page 64 | - | - | - | - | 11.23
| 11.04 | 1.020x (min 1.009x) | 13.57 |
| FP8, B=1, q=32, kv=1024, heads 32/32, page 64 | - | - | - | - | 11.62
| 11.47 | 1.014x (min 1.010x) | 14.02 |
| FP8, B=2, q=32, kv=128, heads 32/4, page 64 | - | - | - | - | 5.70 |
5.47 | 1.047x (min 1.041x) | 5.98 |
| FP8, B=2, q=32, kv=128, heads 32/8, page 64 | - | - | - | - | 5.92 |
5.60 | 1.057x (min 1.051x) | 5.98 |
| FP8, B=2, q=32, kv=256, heads 32/4, page 64 | - | - | - | - | 6.56 |
6.18 | 1.062x (min 1.057x) | 6.82 |
| FP8, B=2, q=32, kv=256, heads 32/8, page 64 | - | - | - | - | 6.66 |
6.27 | 1.061x (min 1.061x) | 6.88 |
| FP8, B=2, q=32, kv=384, heads 32/4, page 64 | - | - | - | - | 7.22 |
6.94 | 1.037x (min 1.036x) | 7.74 |
| FP8, B=2, q=32, kv=384, heads 32/8, page 64 | - | - | - | - | 7.30 |
7.01 | 1.041x (min 1.036x) | 7.78 |
| FP8, B=2, q=32, kv=384, heads 32/16, page 64 | - | - | - | - | 7.36 |
7.07 | 1.041x (min 1.036x) | 8.10 |
| FP8, B=2, q=32, kv=384, heads 32/32, page 64 | - | - | - | - | 7.87 |
7.62 | 1.034x (min 1.029x) | 8.58 |
| FP8, B=2, q=32, kv=512, heads 32/4, page 64 | - | - | - | - | 8.00 |
7.71 | 1.041x (min 1.037x) | 8.74 |
| FP8, B=2, q=32, kv=512, heads 32/8, page 64 | - | - | - | - | 8.19 |
7.84 | 1.041x (min 1.041x) | 8.83 |
| FP8, B=2, q=32, kv=512, heads 32/16, page 64 | - | - | - | - | 8.29 |
8.00 | 1.032x (min 1.032x) | 9.31 |
| FP8, B=2, q=32, kv=512, heads 32/32, page 64 | - | - | - | - | 8.83 |
8.54 | 1.034x (min 1.030x) | 9.82 |
| FP8, B=2, q=32, kv=768, heads 32/4, page 64 | - | - | - | - | 9.60 |
9.44 | 1.017x (min 1.017x) | 10.88 |
| FP8, B=2, q=32, kv=768, heads 32/8, page 64 | - | - | - | - | 9.73 |
9.54 | 1.020x (min 1.017x) | 11.01 |
| FP8, B=2, q=32, kv=768, heads 32/16, page 64 | - | - | - | - | 9.92 |
9.76 | 1.018x (min 1.016x) | 11.74 |
| FP8, B=2, q=32, kv=768, heads 32/32, page 64 | - | - | - | - | 10.50 |
10.37 | 1.012x (min 1.009x) | 12.35 |
| FP8, B=2, q=32, kv=1024, heads 32/4, page 64 | - | - | - | - | 11.17 |
11.01 | 1.015x (min 1.014x) | 12.99 |
| FP8, B=2, q=32, kv=1024, heads 32/8, page 64 | - | - | - | - | 11.46 |
11.30 | 1.017x (min 1.014x) | 13.41 |
| FP8, B=2, q=32, kv=1024, heads 32/16, page 64 | - | - | - | - | 11.57
| 11.42 | 1.011x (min 1.011x) | 14.03 |
| FP8, B=2, q=32, kv=1024, heads 32/32, page 64 | - | - | - | - | 12.16
| 12.10 | 1.007x (min 1.005x) | 14.78 |
| FP8, B=2, q=32, kv=2048, heads 32/8, page 64 | - | - | - | - | 17.86 |
17.70 | 1.009x (min 1.009x) | 22.30 |
| FP8, B=2, q=32, kv=2048, heads 32/32, page 64 | - | - | - | - | 18.91
| 18.85 | 1.003x (min 1.002x) | 24.38 |
| FP8, B=16, q=32, kv=128, heads 32/4, page 64 | - | - | - | - | 6.82 |
6.34 | 1.076x (min 1.075x) | 13.34 |
| FP8, B=16, q=32, kv=256, heads 32/4, page 64 | - | - | - | - | 7.78 |
7.65 | 1.008x (min 1.008x) | 18.37 |
| FP8, B=16, q=32, kv=256, heads 32/8, page 64 | - | - | - | - | 8.19 |
8.03 | 1.020x (min 1.012x) | 18.51 |
| FP8, B=16, q=32, kv=256, heads 32/16, page 64 | - | - | - | - | 10.66
| 10.37 | 1.031x (min 1.028x) | 18.70 |
| FP8, B=16, q=32, kv=256, heads 32/32, page 64 | - | - | - | - | 15.23
| 14.91 | 1.021x (min 1.015x) | 18.94 |
| FP8, B=16, q=32, kv=384, heads 32/4, page 64 | - | - | - | - | 8.61 |
8.54 | 1.004x (min 1.000x) | 21.76 |
| FP8, B=16, q=32, kv=384, heads 32/8, page 64 | - | - | - | - | 8.96 |
8.85 | 1.011x (min 1.011x) | 21.60 |
| FP8, B=16, q=32, kv=384, heads 32/16, page 64 | - | - | - | - | 12.48
| 12.08 | 1.033x (min 1.021x) | 21.89 |
| FP8, B=16, q=32, kv=384, heads 32/32, page 64 | - | - | - | - | 19.26
| 18.94 | 1.018x (min 1.017x) | 22.69 |
| FP8, B=16, q=32, kv=512, heads 32/4, page 64 | - | - | - | - | 9.33 |
9.22 | 1.011x (min 1.009x) | 25.28 |
| FP8, B=16, q=32, kv=512, heads 32/8, page 64 | - | - | - | - | 9.86 |
9.76 | 1.013x (min 1.007x) | 25.47 |
| FP8, B=16, q=32, kv=512, heads 32/16, page 64 | - | - | - | - | 14.56
| 14.26 | 1.022x (min 1.018x) | 26.05 |
| FP8, B=16, q=32, kv=512, heads 32/32, page 64 | - | - | - | - | 23.65
| 23.17 | 1.021x (min 1.021x) | 28.06 |
| FP8, B=16, q=32, kv=768, heads 32/4, page 64 | - | - | - | - | 10.96 |
10.91 | 1.006x (min 1.004x) | 33.70 |
| FP8, B=16, q=32, kv=768, heads 32/8, page 64 | - | - | - | - | 11.97 |
11.84 | 1.011x (min 1.005x) | 34.27 |
| FP8, B=16, q=32, kv=768, heads 32/16, page 64 | - | - | - | - | 18.91
| 18.82 | 1.005x (min 1.002x) | 35.89 |
| FP8, B=16, q=32, kv=768, heads 32/32, page 64 | - | - | - | - | 32.26
| 32.06 | 1.006x (min 1.006x) | 39.41 |
| FP8, B=16, q=32, kv=1024, heads 32/4, page 64 | - | - | - | - | 12.66
| 12.61 | 1.004x (min 1.003x) | 42.14 |
| FP8, B=16, q=32, kv=1024, heads 32/8, page 64 | - | - | - | - | 14.02
| 13.95 | 1.007x (min 1.005x) | 43.20 |
| FP8, B=16, q=32, kv=1024, heads 32/16, page 64 | - | - | - | - | 23.42
| 23.34 | 1.003x (min 1.003x) | 46.27 |
| FP8, B=16, q=32, kv=1024, heads 32/32, page 64 | - | - | - | - | 40.46
| 40.38 | 1.002x (min 1.002x) | 49.73 |
| FP8, B=16, q=32, kv=2048, heads 32/4, page 64 | - | - | - | - | 20.03
| 19.97 | 1.003x (min 1.002x) | 77.54 |
| FP8, B=16, q=32, kv=2048, heads 32/8, page 64 | - | - | - | - | 23.25
| 23.14 | 1.004x (min 1.003x) | 80.48 |
| FP8, B=16, q=32, kv=2048, heads 32/16, page 64 | - | - | - | - | 40.61
| 40.66 | 0.998x (min 0.998x) | 84.82 |
| FP8, B=16, q=32, kv=2048, heads 32/32, page 64 | - | - | - | - | 69.55
| 69.57 | 1.000x (min 1.000x) | 89.44 |
| FP8, B=1, q=1, kv=16, heads 8/1, page 16 † | 6.61 | 6.01 | 1.100x (min
1.099x) | 6.59 | - | - | - | - |
| FP8, B=1, q=1, kv=129, heads 8/1, page 16 † | 8.53 | 7.53 | 1.133x
(min 1.130x) | 7.86 | - | - | - | - |
| FP8, B=1, q=1, kv=129, heads 8/1, page 64 † | 8.88 | 7.52 | 1.181x
(min 1.175x) | 7.84 | - | - | - | - |
| FP8, B=1, q=1, kv=129, heads 32/8, page 16 † | 9.05 | 7.22 | 1.254x
(min 1.250x) | 8.16 | - | - | - | - |
| FP8, B=1, q=1, kv=129, heads 32/8, page 64 † | 9.18 | 7.34 | 1.252x
(min 1.249x) | 8.08 | - | - | - | - |
| FP8, B=1, q=1, kv=129, heads 32/16, page 16 † | 9.28 | 7.34 | 1.264x
(min 1.263x) | 8.16 | - | - | - | - |
| FP8, B=1, q=1, kv=129, heads 32/16, page 64 † | 9.04 | 7.26 | 1.244x
(min 1.242x) | 7.98 | - | - | - | - |
| FP8, B=1, q=1, kv=129, heads 32/32, page 16 † | 9.39 | 7.41 | 1.268x
(min 1.264x) | 8.35 | - | - | - | - |
| FP8, B=1, q=1, kv=129, heads 32/32, page 64 † | 9.17 | 7.41 | 1.238x
(min 1.236x) | 8.13 | - | - | - | - |
| FP8, B=1, q=8, kv=256, heads 32/16, page 32 † | 9.17 | 7.65 | 1.199x
(min 1.197x) | 8.10 | - | - | - | - |
| FP8, B=1, q=16, kv=16, heads 8/1, page 16 † | 6.19 | 5.73 | 1.081x
(min 1.064x) | 6.60 | - | - | - | - |
| FP8, B=1, q=16, kv=127, heads 32/32, page 32 † | 6.88 | 6.52 | 1.055x
(min 1.052x) | 6.75 | - | - | - | - |
| FP8, B=1, q=17, kv=16, heads 8/1, page 16 † | 6.06 | 5.66 | 1.069x
(min 1.068x) | 6.59 | - | - | - | - |
| FP8, B=1, q=17, kv=256, heads 32/32, page 32 † | 9.25 | 7.78 | 1.189x
(min 1.189x) | 8.19 | - | - | - | - |
| FP8, B=1, q=31, kv=128, heads 32/8, page 32 † | 6.88 | 6.50 | 1.058x
(min 1.056x) | 6.82 | - | - | - | - |
| FP8, B=1, q=31, kv=129, heads 64/8, page 16 † | 8.06 | 7.61 | 1.060x
(min 1.055x) | 8.54 | - | - | - | - |
| FP8, B=1, q=32, kv=128, heads 32/4, page 16 | 6.62 | 6.40 | 1.035x
(min 1.020x) | 6.69 | 5.86 | 5.57 | 1.052x (min 1.052x) | 5.73 |
| FP8, B=1, q=33, kv=16, heads 8/1, page 16 † | 6.41 | 5.84 | 1.097x
(min 1.088x) | 6.70 | - | - | - | - |
| FP8, B=1, q=64, kv=128, heads 32/4, page 16 | 6.40 | 6.24 | 1.028x
(min 1.015x) | 6.82 | 6.02 | 5.73 | 1.050x (min 1.050x) | 6.14 |
| FP8, B=1, q=100, kv=100, heads 32/4, page 16 | 7.09 | 6.45 | 1.095x
(min 1.094x) | 7.31 | 5.98 | 5.73 | 1.045x (min 1.039x) | 6.30 |
| FP8, B=1, q=128, kv=127, heads 32/32, page 16 † | 7.20 | 6.67 | 1.079x
(min 1.077x) | 7.41 | - | - | - | - |
| FP8, B=1, q=128, kv=128, heads 32/4, page 16 | 6.59 | 6.35 | 1.040x
(min 1.038x) | 7.23 | 6.02 | 5.73 | 1.050x (min 1.044x) | 6.40 |
| FP8, B=1, q=128, kv=128, heads 64/8, page 16 | 6.88 | 6.56 | 1.049x
(min 1.044x) | 7.55 | 6.11 | 5.89 | 1.038x (min 1.033x) | 6.66 |
| FP8, B=1, q=128, kv=1500, heads 32/4, page 16 | 20.70 | 20.19 | 1.025x
(min 1.021x) | 23.58 | - | - | - | - |
| FP8, B=1, q=129, kv=100, heads 32/16, page 32 † | 8.58 | 6.59 | 1.301x
(min 1.296x) | 7.46 | - | - | - | - |
| FP8, B=1, q=129, kv=128, heads 32/8, page 16 † | 7.97 | 6.32 | 1.261x
(min 1.252x) | 7.30 | - | - | - | - |
| FP8, B=1, q=129, kv=128, heads 32/32, page 64 † | 7.82 | 6.50 | 1.203x
(min 1.202x) | 7.47 | - | - | - | - |
| FP8, B=1, q=129, kv=256, heads 32/32, page 16 † | 10.00 | 7.97 |
1.255x (min 1.250x) | 9.20 | - | - | - | - |
| FP8, B=1, q=200, kv=768, heads 64/8, page 16 † | 15.54 | 12.82 |
1.212x (min 1.212x) | 15.78 | - | - | - | - |
| FP8, B=1, q=200, kv=1024, heads 32/16, page 16 † | 19.60 | 15.58 |
1.258x (min 1.251x) | 18.86 | - | - | - | - |
| FP8, B=1, q=256, kv=1024, heads 32/8, page 16 † | 19.15 | 14.98 |
1.279x (min 1.274x) | 18.96 | - | - | - | - |
| FP8, B=1, q=256, kv=1024, heads 32/8, page 64 † | 18.74 | 14.67 |
1.277x (min 1.275x) | 18.75 | - | - | - | - |
| FP8, B=1, q=300, kv=384, heads 32/16, page 64 † | 11.54 | 9.42 |
1.224x (min 1.223x) | 11.63 | - | - | - | - |
| FP8, B=1, q=300, kv=384, heads 32/32, page 64 † | 11.76 | 9.88 |
1.190x (min 1.189x) | 11.76 | - | - | - | - |
| FP8, B=1, q=300, kv=512, heads 32/4, page 16 | 12.42 | 10.37 | 1.201x
(min 1.195x) | 12.93 | - | - | - | - |
| FP8, B=1, q=300, kv=768, heads 32/4, page 16 | 15.33 | 12.80 | 1.198x
(min 1.192x) | 16.03 | - | - | - | - |
| FP8, B=1, q=300, kv=1024, heads 32/4, page 16 | 18.50 | 15.33 | 1.207x
(min 1.204x) | 19.17 | - | - | - | - |
| FP8, B=1, q=300, kv=1024, heads 32/8, page 16 † | 19.33 | 15.28 |
1.265x (min 1.263x) | 19.30 | - | - | - | - |
| FP8, B=1, q=300, kv=1500, heads 32/32, page 16 | 26.43 | 21.23 |
1.245x (min 1.242x) | 25.79 | - | - | - | - |
| FP8, B=2, q=1, kv=100, heads 64/8, page 16 † | 6.80 | 6.38 | 1.067x
(min 1.063x) | 7.44 | - | - | - | - |
| FP8, B=2, q=1, kv=129, heads 32/32, page 16 † | 9.49 | 7.58 | 1.251x
(min 1.249x) | 8.77 | - | - | - | - |
| FP8, B=2, q=8, kv=256, heads 32/16, page 32 † | 9.26 | 7.78 | 1.191x
(min 1.189x) | 8.29 | - | - | - | - |
| FP8, B=2, q=16, kv=16, heads 32/4, page 16 † | 6.48 | 6.18 | 1.049x
(min 1.047x) | 6.91 | - | - | - | - |
| FP8, B=2, q=16, kv=129, heads 32/32, page 64 † | 9.87 | 7.90 | 1.249x
(min 1.241x) | 8.90 | - | - | - | - |
| FP8, B=2, q=17, kv=256, heads 32/32, page 32 † | 9.70 | 8.15 | 1.189x
(min 1.189x) | 8.69 | - | - | - | - |
| FP8, B=2, q=32, kv=127, heads 64/8, page 32 † | 7.06 | 6.46 | 1.092x
(min 1.089x) | 7.22 | - | - | - | - |
| FP8, B=2, q=32, kv=128, heads 32/4, page 16 | 6.66 | 6.40 | 1.040x
(min 1.030x) | 6.85 | 5.92 | 5.70 | 1.042x (min 1.039x) | 5.95 |
| FP8, B=2, q=64, kv=128, heads 32/4, page 16 | 6.59 | 6.30 | 1.043x
(min 1.030x) | 7.01 | 5.92 | 5.66 | 1.040x (min 1.034x) | 6.18 |
| FP8, B=2, q=65, kv=96, heads 32/16, page 16 † | 7.07 | 6.58 | 1.075x
(min 1.073x) | 7.28 | - | - | - | - |
| FP8, B=2, q=128, kv=100, heads 32/4, page 16 | 7.17 | 6.53 | 1.099x
(min 1.093x) | 7.62 | 6.11 | 5.92 | 1.032x (min 1.027x) | 6.62 |
| FP8, B=2, q=128, kv=128, heads 32/4, page 16 | 7.01 | 6.62 | 1.058x
(min 1.043x) | 7.62 | 6.10 | 5.94 | 1.030x (min 1.024x) | 6.72 |
| FP8, B=2, q=128, kv=128, heads 32/8, page 16 | 6.88 | 6.66 | 1.034x
(min 1.029x) | 7.52 | 6.18 | 6.00 | 1.029x (min 1.027x) | 6.66 |
| FP8, B=2, q=128, kv=256, heads 32/4, page 16 | 8.03 | 7.87 | 1.018x
(min 1.012x) | 8.93 | - | - | - | - |
| FP8, B=2, q=128, kv=512, heads 32/4, page 16 | 10.43 | 10.18 | 1.025x
(min 1.022x) | 12.00 | - | - | - | - |
| FP8, B=2, q=128, kv=768, heads 32/4, page 16 | 12.96 | 12.67 | 1.023x
(min 1.015x) | 15.10 | - | - | - | - |
| FP8, B=2, q=128, kv=1024, heads 32/4, page 16 | 15.36 | 15.14 | 1.014x
(min 1.011x) | 18.18 | - | - | - | - |
| FP8, B=2, q=128, kv=1500, heads 32/4, page 16 | 20.80 | 20.32 | 1.024x
(min 1.020x) | 24.42 | - | - | - | - |
| FP8, B=2, q=128, kv=1500, heads 32/4, page 64 | - | - | - | - | 14.85
| 14.72 | 1.007x (min 1.005x) | 18.18 |
| FP8, B=2, q=128, kv=1500, heads 32/32, page 16 | 21.34 | 20.72 |
1.030x (min 1.029x) | 25.60 | - | - | - | - |
| FP8, B=2, q=128, kv=2048, heads 32/4, page 16 | 25.09 | 24.80 | 1.012x
(min 1.010x) | 30.62 | - | - | - | - |
| FP8, B=2, q=129, kv=64, heads 32/16, page 64 † | 8.26 | 7.06 | 1.169x
(min 1.166x) | 7.68 | - | - | - | - |
| FP8, B=2, q=129, kv=96, heads 32/16, page 16 † | 8.64 | 7.30 | 1.184x
(min 1.184x) | 7.65 | - | - | - | - |
| FP8, B=2, q=129, kv=256, heads 8/1, page 16 † | 8.82 | 7.59 | 1.161x
(min 1.144x) | 8.76 | - | - | - | - |
| FP8, B=2, q=129, kv=256, heads 32/32, page 64 † | 10.08 | 8.42 |
1.197x (min 1.196x) | 9.74 | - | - | - | - |
| FP8, B=2, q=256, kv=1500, heads 32/16, page 64 † | 26.32 | 20.78 |
1.267x (min 1.262x) | 25.98 | - | - | - | - |
| FP8, B=2, q=256, kv=1500, heads 32/32, page 64 † | 27.08 | 21.09 |
1.284x (min 1.282x) | 26.46 | - | - | - | - |
| FP8, B=3, q=1, kv=129, heads 32/16, page 64 † | 9.33 | 7.50 | 1.243x
(min 1.238x) | 8.61 | - | - | - | - |
| FP8, B=3, q=8, kv=96, heads 16/2, page 32 † | 6.67 | 6.19 | 1.078x
(min 1.072x) | 6.75 | - | - | - | - |
| FP8, B=3, q=8, kv=129, heads 32/16, page 16 † | 9.79 | 7.73 | 1.267x
(min 1.264x) | 9.07 | - | - | - | - |
| FP8, B=3, q=96, kv=16, heads 64/8, page 32 † | 7.76 | 6.75 | 1.149x
(min 1.146x) | 11.33 | - | - | - | - |
| FP8, B=3, q=129, kv=96, heads 32/8, page 32 † | 8.75 | 6.88 | 1.272x
(min 1.270x) | 7.89 | - | - | - | - |
| FP8, B=3, q=129, kv=127, heads 16/2, page 16 † | 7.70 | 6.56 | 1.174x
(min 1.173x) | 7.55 | - | - | - | - |
| FP8, B=3, q=129, kv=128, heads 32/8, page 64 † | 8.14 | 6.85 | 1.189x
(min 1.187x) | 7.89 | - | - | - | - |
| FP8, B=3, q=129, kv=129, heads 32/8, page 32 † | 9.66 | 7.89 | 1.225x
(min 1.215x) | 9.78 | - | - | - | - |
| FP8, B=3, q=129, kv=129, heads 32/16, page 32 † | 10.00 | 8.75 |
1.143x (min 1.126x) | 9.98 | - | - | - | - |
| FP8, B=3, q=129, kv=129, heads 32/16, page 64 † | 9.79 | 8.46 | 1.157x
(min 1.150x) | 9.98 | - | - | - | - |
| FP8, B=4, q=1, kv=129, heads 32/16, page 16 † | 9.41 | 7.65 | 1.230x
(min 1.230x) | 9.26 | - | - | - | - |
| FP8, B=4, q=1, kv=256, heads 32/16, page 64 † | 9.09 | 7.66 | 1.186x
(min 1.185x) | 8.92 | - | - | - | - |
| FP8, B=4, q=8, kv=256, heads 32/16, page 32 † | 9.77 | 8.19 | 1.192x
(min 1.189x) | 9.02 | - | - | - | - |
| FP8, B=4, q=17, kv=256, heads 32/32, page 32 † | 10.54 | 9.14 | 1.153x
(min 1.153x) | 9.57 | - | - | - | - |
| FP8, B=4, q=17, kv=256, heads 32/32, page 64 † | 10.42 | 9.13 | 1.141x
(min 1.136x) | 9.58 | - | - | - | - |
| FP8, B=4, q=64, kv=128, heads 32/4, page 16 | - | - | - | - | 6.14 |
5.89 | 1.043x (min 1.043x) | 6.50 |
| FP8, B=4, q=128, kv=128, heads 32/4, page 16 | - | - | - | - | 6.62 |
6.22 | 1.065x (min 1.062x) | 7.07 |
| FP8, B=4, q=128, kv=128, heads 32/4, page 32 | - | - | - | - | 6.66 |
6.21 | 1.072x (min 1.069x) | 7.14 |
| FP8, B=4, q=129, kv=16, heads 8/1, page 16 † | 7.39 | 6.29 | 1.176x
(min 1.149x) | 7.46 | - | - | - | - |
| FP8, B=6, q=1, kv=129, heads 32/16, page 16 † | 9.54 | 8.13 | 1.173x
(min 1.169x) | 13.06 | - | - | - | - |
| FP8, B=6, q=1, kv=129, heads 64/8, page 64 † | 9.06 | 7.60 | 1.193x
(min 1.188x) | 17.94 | - | - | - | - |
| FP8, B=6, q=8, kv=129, heads 32/16, page 64 † | 10.11 | 8.64 | 1.170x
(min 1.167x) | 13.86 | - | - | - | - |
| FP8, B=6, q=17, kv=100, heads 64/8, page 32 † | 7.34 | 6.83 | 1.075x
(min 1.070x) | 13.23 | - | - | - | - |
| FP8, B=6, q=65, kv=96, heads 32/8, page 32 † | 8.80 | 7.11 | 1.237x
(min 1.234x) | 10.92 | - | - | - | - |
| FP8, B=6, q=96, kv=256, heads 32/8, page 32 † | 10.51 | 8.66 | 1.214x
(min 1.207x) | 14.38 | - | - | - | - |
| FP8, B=6, q=96, kv=256, heads 32/8, page 64 † | 10.27 | 8.63 | 1.190x
(min 1.189x) | 14.45 | - | - | - | - |
| FP8, B=6, q=128, kv=100, heads 8/1, page 32 † | 7.25 | 6.59 | 1.099x
(min 1.093x) | 7.60 | - | - | - | - |
| FP8, B=6, q=129, kv=128, heads 16/2, page 32 † | 7.74 | 6.80 | 1.139x
(min 1.138x) | 7.94 | - | - | - | - |
| FP8, B=6, q=129, kv=128, heads 16/2, page 64 † | 7.87 | 6.68 | 1.178x
(min 1.176x) | 7.90 | - | - | - | - |
| FP8, B=8, q=1, kv=129, heads 32/16, page 64 † | 10.14 | 8.66 | 1.171x
(min 1.169x) | 13.92 | - | - | - | - |
| FP8, B=8, q=8, kv=96, heads 32/4, page 16 † | 6.91 | 6.42 | 1.077x
(min 1.075x) | 10.11 | - | - | - | - |
| FP8, B=8, q=16, kv=384, heads 16/2, page 16 † | 9.14 | 8.84 | 1.033x
(min 1.031x) | 10.06 | - | - | - | - |
| FP8, B=8, q=32, kv=16, heads 8/1, page 16 † | 6.43 | 6.02 | 1.069x
(min 1.063x) | 6.94 | - | - | - | - |
| FP8, B=8, q=64, kv=128, heads 32/4, page 16 | - | - | - | - | 6.53 |
6.26 | 1.041x (min 1.041x) | 9.17 |
| FP8, B=8, q=128, kv=256, heads 8/1, page 32 † | 8.18 | 7.84 | 1.043x
(min 1.033x) | 9.08 | - | - | - | - |
| FP8, B=16, q=16, kv=512, heads 32/8, page 16 † | 11.93 | 11.57 |
1.031x (min 1.026x) | 34.46 | - | - | - | - |
| FP8, B=16, q=32, kv=128, heads 32/4, page 16 | 7.58 | 7.04 | 1.078x
(min 1.077x) | 16.35 | 6.53 | 6.40 | 1.020x (min 1.015x) | 13.60 |
| FP8, B=16, q=32, kv=256, heads 8/1, page 32 † | 8.10 | 7.79 | 1.039x
(min 1.037x) | 8.80 | - | - | - | - |
| FP8, B=16, q=129, kv=256, heads 8/1, page 32 † | 9.31 | 8.10 | 1.149x
(min 1.144x) | 9.97 | - | - | - | - |
| FP8, B=16, q=129, kv=256, heads 8/1, page 64 † | 9.90 | 8.17 | 1.212x
(min 1.207x) | 9.90 | - | - | - | - |
| FP8, B=64, q=8, kv=256, heads 8/1, page 16 † | 8.53 | 8.14 | 1.047x
(min 1.047x) | 21.58 | - | - | - | - |
| FP8, B=64, q=32, kv=256, heads 8/1, page 32 † | 9.23 | 8.62 | 1.071x
(min 1.067x) | 22.29 | - | - | - | - |
| FP8, B=128, q=16, kv=256, heads 8/1, page 32 † | 9.55 | 9.04 | 1.057x
(min 1.054x) | 35.90 | - | - | - | - |
| FP8, B=2, q=200, kv=1500, heads 32/4, page 16 | 24.67 | 20.10 | 1.226x
(min 1.224x) | 25.12 | - | - | - | - |
| FP8, B=4, q=128, kv=4096, heads 32/32, page 64 | - | - | - | - | 40.19
| 40.19 | 1.000x (min 0.999x) | 51.55 |
| FP8, B=16, q=128, kv=2048, heads 32/32, page 64 | - | - | - | - |
70.82 | 70.77 | 1.000x (min 1.000x) | 91.79 |

</details>

None of the 44 tracked shapes is slower than before on either GPU. On
B200 one of them is faster: FP8, B=2, q=128, kv=1500, heads 32/4, page
16, from 20.86 to 20.32 µs (1.028x). The other 43 are unchanged.

A shape counts as faster than trtllm-gen only if it is faster in every
round of every layout, with its smallest margin above that layout's
run-to-run band. Ratios below are trtllm-gen / this PR.

**GB300.** All 44 tracked shapes are faster than trtllm-gen in every
layout. Every GB300 target shape is faster than trtllm-gen on all three
machines. Among the targets, the smallest per-layout margin is 1.020x,
for FP8, B=1, q=32, kv=128, heads 32/4, page 16, on GB300-2. On all
three machines, the previous version of that shape had a median time
above trtllm-gen's.

**B200.** 43 of the 44 tracked shapes are faster than trtllm-gen. This
PR does not change the program of the remaining shape, FP8, B=16, q=256,
kv=2048, heads 32/32, page 64:
- It is within the run-to-run band of trtllm-gen on B200-1 (1.001x and
1.002x in two runs) and in the B200-2 rerun (1.001x).
- It is faster on B200-3 (1.005x) and in the first B200-2 run (1.010x).

One B200 target shape, FP8, B=1, q=1, kv=16, heads 8/1, page 16, is not
faster than trtllm-gen on every machine:
- It is faster on B200-1 (1.068x) and B200-3 (1.103x).
- It is within the run-to-run band on B200-2, in both runs (1.012x).
- This PR makes it 1.092x to 1.118x faster than before on all three
machines.

The other B200 targets, and every long-KV and sweep shape on both GPUs,
are faster than trtllm-gen.

This PR does not change the kernel's other Cake variants, BF16 and FP8 Q
with NVFP4 KV, and the kernel covers sm_100a (B200) and sm_103a (GB300).

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added optimized one-wave options for FP8 context attention on
supported GPUs, including runtime-sized workloads and several pack
sizes.
* Eligible short-context workloads can now use these options when
tile-count limits are met.

* **Bug Fixes**
* Invalid tensor layouts, dimensions, and launch parameters are checked
before execution, with errors reported for unsupported inputs.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [ce1232f](https://github.com/flashinfer-ai/flashinfer/commit/ce1232f9cc9259df85adba385c0f4a0ce6a719f7)

- **作者**: eigen
- **时间**: 2026-11-01T10:12:49Z
- **提交信息**: perf(cake_deepgemm_dense_mqa): serve fp8:qle2048:short on sm_103a for Q <= 136 up to K = 8448 with a four-stage TMEM ring bucket program (#8183)

This PR follows up #7607, #7643, #7741, #7779, #8113, #8124, #8142,
#8150, #8151, #8153 and #8173. FlashInfer's Cake DeepGEMM-form MQA
logits programs for Blackwell back `flashinfer.dense_mqa` and
`flashinfer.paged_mqa`. The variants are dense FP8 with 32 or 64 heads,
dense FP4 with 32 heads (including fused metadata + logits sequences),
and paged FP8. This PR changes dense FP8 with 32 heads, on sm_103a
(GB300) only. It adds one program,
`cake_deepgemm_dense_mqa_2abdc35ce7f99149bfb5`, as two generated units
(a kernel and a binding). Its kernel text is the same as
`cake_deepgemm_dense_mqa_4be5b4aaa1f52069837c`. It uses the 4-stage TMEM
accumulator ring that #8173 introduced on sm_100a. Each math warpgroup
therefore gets its own double buffer. On sm_103a, route
`fp8:qle2048:short` gains a stage bucket that runs the new program for
the `logits` stage. The bucket covers at most 136 queries and K up to
8448 keys. Calls on that route with more queries or longer K keep
`cake_deepgemm_dense_mqa_4be5b4aaa1f52069837c`. Every other call keeps
its program, and sm_100a is unchanged. The only other changes are the
catalog, the `dense_mqa.py` docstring, the README and the tests. Logits
are bitwise equal on every row of both tables (106/106 on each GPU). The
baseline is the previous version, FlashInfer d1e98753d8ee (#8173), for
the dense MQA paths. On GB300, 4 of the 106 rows run the updated
program. `Q 130, K 8192` FP8 goes from 9.44 to 9.34 µs (1.0103). `Q 130,
K 8448` FP8 goes from 9.76 to 9.60 µs (1.0167). `Q 132, K 2048` FP8 goes
from 6.46 to 6.16 µs (1.0518). `Q 132, K 8448` FP8 goes from 9.66 to
9.49 µs (1.0185). Each of these 4 rows is faster in all 3 sessions. The
other 102 rows run byte-identical programs in both versions. They read
0.9899–1.0112 (median 1.0000), which is measurement noise. On B200, no
row changes route. All 106 rows run byte-identical programs and read
0.9894–1.0108 (median 1.0000), which is also measurement noise.

**NVIDIA GB300** (sm_103a, 152 SMs), CUDA 13.4 (nvcc V13.4.92,
JIT-compiled), driver 580.167.08, torch 2.14.1+cu130. Previous version =
FlashInfer d1e98753d8ee (#8173 head; dense MQA paths). Timing is CUPTI
GPU time per call with a cold L2. µs is the median over the 3 sessions
of each session's median. Speedup is the median over the sessions of
previous / this (> 1 = faster). Rows that launch more than one kernel
per call report the sum of kernel times. The notation is the same as in
#7643. `Q q, K k` is q queries over k keys. `prefill Q q, prefix p,
causal` is q new queries attending causally over p cached keys plus
themselves (K = p + q). "2 sequences" and "2048-query chunks" mean the
same as in #7643. "updated" means the row now runs
`cake_deepgemm_dense_mqa_2abdc35ce7f99149bfb5` instead of
`cake_deepgemm_dense_mqa_4be5b4aaa1f52069837c`. "same program" means
every program on the row is byte-identical to the previous version.

| shape | dtype | heads | previous µs | this PR µs | speedup | program |
|---|---|---:|---:|---:|---:|---|
| prefill Q 37, prefix 4100, causal | FP8 | 32 | 5.36 | 5.34 | 1.0030 |
same program |
| prefill Q 1024, prefix 32779, causal | FP8 | 32 | 108.24 | 108.26 |
0.9998 | same program |
| prefill Q 1, prefix 0, causal | FP8 | 64 | 3.97 | 3.97 | 1.0000 | same
program |
| prefill Q 1, prefix 4100, causal | FP8 | 64 | 4.00 | 4.00 | 1.0000 |
same program |
| prefill Q 1, prefix 32779, causal | FP8 | 64 | 4.94 | 4.96 | 1.0000 |
same program |
| prefill Q 1, prefix 131077, causal | FP8 | 64 | 7.76 | 7.74 | 1.0010 |
same program |
| prefill Q 2, prefix 0, causal | FP8 | 64 | 3.92 | 3.94 | 0.9980 | same
program |
| prefill Q 2, prefix 4100, causal | FP8 | 64 | 4.58 | 4.58 | 1.0000 |
same program |
| prefill Q 3, prefix 0, causal | FP8 | 64 | 3.71 | 3.71 | 1.0000 | same
program |
| prefill Q 3, prefix 4100, causal | FP8 | 64 | 4.38 | 4.37 | 1.0000 |
same program |
| prefill Q 7, prefix 0, causal | FP8 | 64 | 3.81 | 3.81 | 1.0000 | same
program |
| prefill Q 7, prefix 4100, causal | FP8 | 64 | 4.42 | 4.40 | 1.0000 |
same program |
| prefill Q 8, prefix 0, causal | FP8 | 64 | 3.74 | 3.74 | 1.0000 | same
program |
| prefill Q 8, prefix 4100, causal | FP8 | 64 | 4.40 | 4.38 | 1.0036 |
same program |
| prefill Q 16, prefix 0, causal | FP8 | 64 | 3.74 | 3.71 | 1.0000 |
same program |
| prefill Q 16, prefix 4100, causal | FP8 | 64 | 4.42 | 4.42 | 1.0000 |
same program |
| prefill Q 37, prefix 0, causal | FP8 | 64 | 3.78 | 3.78 | 1.0000 |
same program |
| prefill Q 37, prefix 4100, causal | FP8 | 64 | 5.38 | 5.38 | 1.0000 |
same program |
| prefill Q 37, prefix 32779, causal | FP8 | 64 | 12.54 | 12.54 | 1.0000
| same program |
| prefill Q 37, prefix 131077, causal | FP8 | 64 | 33.95 | 33.97 |
1.0000 | same program |
| prefill Q 64, prefix 0, causal | FP8 | 64 | 3.81 | 3.81 | 1.0000 |
same program |
| prefill Q 64, prefix 4100, causal | FP8 | 64 | 6.08 | 6.06 | 1.0000 |
same program |
| prefill Q 128, prefix 0, causal | FP8 | 64 | 3.94 | 3.94 | 1.0000 |
same program |
| prefill Q 128, prefix 4100, causal | FP8 | 64 | 8.58 | 8.58 | 1.0000 |
same program |
| prefill Q 128, prefix 4100, causal, 2 sequences | FP8 | 64 | 7.49 |
7.49 | 1.0000 | same program |
| prefill Q 128, prefix 32779, causal | FP8 | 64 | 30.45 | 30.45 |
1.0000 | same program |
| prefill Q 128, prefix 131077, causal | FP8 | 64 | 103.23 | 103.23 |
1.0000 | same program |
| prefill Q 129, prefix 0, causal | FP8 | 64 | 3.90 | 3.90 | 1.0000 |
same program |
| prefill Q 129, prefix 4100, causal | FP8 | 64 | 8.67 | 8.66 | 1.0000 |
same program |
| prefill Q 1023, prefix 0, causal | FP8 | 64 | 9.49 | 9.49 | 1.0000 |
same program |
| prefill Q 1023, prefix 4100, causal | FP8 | 64 | 35.58 | 35.58 |
0.9996 | same program |
| prefill Q 1024, prefix 0, causal | FP8 | 64 | 9.57 | 9.57 | 1.0000 |
same program |
| prefill Q 1024, prefix 4100, causal | FP8 | 64 | 35.66 | 35.66 |
0.9996 | same program |
| prefill Q 1024, prefix 32779, causal | FP8 | 64 | 205.15 | 205.18 |
1.0002 | same program |
| prefill Q 1024, prefix 131077, causal | FP8 | 64 | 829.14 | 829.90 |
0.9995 | same program |
| prefill Q 4096, prefix 0, causal | FP8 | 64 | 61.44 | 61.45 | 0.9999 |
same program |
| prefill Q 4096, prefix 4100, causal | FP8 | 64 | 156.21 | 156.14 |
1.0004 | same program |
| prefill Q 4096, prefix 32779, causal | FP8 | 64 | 873.07 | 874.53 |
0.9998 | same program |
| prefill Q 4096, prefix 32779, causal, 2 sequences | FP8 | 64 | 577.05
| 577.34 | 1.0016 | same program |
| prefill Q 4096, prefix 32779, causal, 2048-query chunks | FP8 | 64 |
883.51 | 885.58 | 0.9899 | same program |
| prefill Q 4096, prefix 131077, causal | FP8 | 64 | 3523.18 | 3498.90 |
1.0055 | same program |
| prefill Q 4096, prefix 131077, causal, 2048-query chunks | FP8 | 64 |
3516.23 | 3521.30 | 0.9986 | same program |
| prefill Q 8192, prefix 0, causal | FP8 | 64 | 209.76 | 209.79 | 0.9979
| same program |
| prefill Q 8192, prefix 4100, causal | FP8 | 64 | 407.94 | 407.60 |
1.0011 | same program |
| prefill Q 8192, prefix 32779, causal | FP8 | 64 | 1886.91 | 1881.86 |
1.0027 | same program |
| prefill Q 8192, prefix 32779, causal, 2048-query chunks | FP8 | 64 |
1927.15 | 1926.59 | 1.0020 | same program |
| prefill Q 8192, prefix 131077, causal | FP8 | 64 | 7182.04 | 7183.40 |
0.9999 | same program |
| prefill Q 8192, prefix 131077, causal, 2048-query chunks | FP8 | 64 |
7231.66 | 7235.77 | 0.9990 | same program |
| prefill Q 16231, prefix 0, causal | FP8 | 64 | 828.77 | 830.10 |
0.9986 | same program |
| prefill Q 16231, prefix 4100, causal | FP8 | 64 | 1258.98 | 1248.80 |
1.0081 | same program |
| prefill Q 16231, prefix 32779, causal | FP8 | 64 | 4282.24 | 4258.38 |
1.0056 | same program |
| prefill Q 16231, prefix 32779, causal, 2048-query chunks | FP8 | 64 |
4341.92 | 4342.59 | 1.0000 | same program |
| prefill Q 16231, prefix 131077, causal | FP8 | 64 | 14670.75 |
14677.02 | 0.9996 | same program |
| prefill Q 16231, prefix 131077, causal, 2048-query chunks | FP8 | 64 |
14896.04 | 14881.23 | 1.0006 | same program |
| Q 1, K 4096 | FP8 | 32 | 3.84 | 3.82 | 1.0042 | same program |
| Q 1, K 32768 | FP8 | 32 | 4.64 | 4.64 | 1.0000 | same program |
| Q 1, K 131072 | FP8 | 32 | 7.46 | 7.44 | 1.0022 | same program |
| Q 1, K 1048576 | FP8 | 32 | 30.21 | 30.18 | 0.9995 | same program |
| Q 1, K 1048832 | FP8 | 32 | 30.03 | 30.05 | 0.9995 | same program |
| Q 3, K 8192 | FP8 | 32 | 4.72 | 4.72 | 1.0000 | same program |
| Q 3, K 1048832 | FP8 | 32 | 33.60 | 33.74 | 0.9991 | same program |
| Q 16, K 2048 | FP8 | 32 | 4.69 | 4.67 | 1.0000 | same program |
| Q 16, K 4096 | FP8 | 32 | 4.77 | 4.77 | 1.0000 | same program |
| Q 16, K 32768 | FP8 | 32 | 7.25 | 7.17 | 1.0112 | same program |
| Q 16, K 131072 | FP8 | 32 | 13.20 | 13.22 | 1.0000 | same program |
| Q 16, K 1048576 | FP8 | 32 | 59.18 | 59.22 | 0.9997 | same program |
| Q 16, K 1048832 | FP8 | 32 | 60.21 | 60.16 | 1.0008 | same program |
| Q 33, K 8192 | FP8 | 32 | 5.41 | 5.41 | 1.0000 | same program |
| Q 33, K 1048832 | FP8 | 32 | 179.76 | 180.17 | 0.9995 | same program |
| Q 37, K 4137 | FP8 | 32 | 5.31 | 5.31 | 1.0000 | same program |
| Q 128, K 2048 | FP8 | 32 | 5.89 | 5.87 | 1.0000 | same program |
| Q 128, K 4096 | FP8 | 32 | 7.01 | 7.01 | 1.0000 | same program |
| Q 128, K 32768 | FP8 | 32 | 18.18 | 18.19 | 1.0000 | same program |
| Q 128, K 131072 | FP8 | 32 | 53.58 | 53.58 | 1.0003 | same program |
| Q 128, K 131328 | FP8 | 32 | 55.08 | 55.07 | 1.0001 | same program |
| Q 130, K 8192 | FP8 | 32 | 9.44 | 9.34 | 1.0103 | updated |
| Q 130, K 8448 | FP8 | 32 | 9.76 | 9.60 | 1.0167 | updated |
| Q 130, K 65792 | FP8 | 32 | 32.45 | 32.43 | 1.0000 | same program |
| Q 132, K 2048 | FP8 | 32 | 6.46 | 6.16 | 1.0518 | updated |
| Q 132, K 8448 | FP8 | 32 | 9.66 | 9.49 | 1.0185 | updated |
| Q 132, K 65792 | FP8 | 32 | 32.40 | 32.42 | 1.0000 | same program |
| Q 1024, K 33803 | FP8 | 32 | 110.08 | 110.08 | 1.0000 | same program |
| Q 2052, K 2048 | FP8 | 32 | 20.80 | 20.77 | 0.9992 | same program |
| Q 2052, K 8448 | FP8 | 32 | 61.15 | 61.10 | 0.9997 | same program |
| Q 2053, K 2048 | FP8 | 32 | 21.25 | 21.22 | 1.0000 | same program |
| Q 2053, K 8448 | FP8 | 32 | 61.58 | 61.54 | 1.0000 | same program |
| Q 1, K 4096 | FP4 | 32 | 3.84 | 3.84 | 1.0000 | same program |
| Q 1, K 32768 | FP4 | 32 | 4.53 | 4.54 | 0.9965 | same program |
| Q 1, K 131072 | FP4 | 32 | 6.35 | 6.38 | 0.9950 | same program |
| Q 1, K 131328 | FP4 | 32 | 6.64 | 6.64 | 1.0000 | same program |
| Q 7, K 2048 | FP4 | 32 | 4.70 | 4.70 | 1.0000 | same program |
| Q 16, K 4096 | FP4 | 32 | 4.83 | 4.83 | 1.0000 | same program |
| Q 16, K 32768 | FP4 | 32 | 6.66 | 6.66 | 1.0000 | same program |
| Q 16, K 131072 | FP4 | 32 | 12.00 | 12.03 | 1.0000 | same program |
| Q 16, K 1048576 | FP4 | 32 | 54.24 | 54.29 | 1.0003 | same program |
| Q 16, K 1048832 | FP4 | 32 | 54.08 | 54.10 | 1.0003 | same program |
| Q 33, K 8192 | FP4 | 32 | 5.54 | 5.54 | 1.0000 | same program |
| Q 33, K 1048832 | FP4 | 32 | 118.35 | 118.29 | 1.0008 | same program |
| Q 128, K 4096 | FP4 | 32 | 6.40 | 6.40 | 1.0000 | same program |
| Q 128, K 32768 | FP4 | 32 | 17.06 | 17.04 | 1.0009 | same program |
| Q 128, K 131072 | FP4 | 32 | 52.72 | 52.72 | 1.0000 | same program |
| Q 130, K 65536 | FP4 | 32 | 30.48 | 30.50 | 0.9995 | same program |
| Q 130, K 65792 | FP4 | 32 | 30.67 | 30.67 | 1.0000 | same program |
| Q 1024, K 2048 | FP4 | 32 | 13.87 | 13.90 | 0.9977 | same program |
| Q 2052, K 2048 | FP4 | 32 | 21.49 | 21.78 | 0.9927 | same program |
| Q 2052, K 65792 | FP4 | 32 | 393.28 | 393.36 | 0.9998 | same program |

**NVIDIA B200** (sm_100a, 148 SMs), CUDA 13.4 (nvcc V13.4.92,
JIT-compiled), driver 580.82.07, torch 2.14.1+cu130. Previous version =
FlashInfer d1e98753d8ee (#8173 head; dense MQA paths). Timing, notation
and the labels are the same as in the GB300 table.

| shape | dtype | heads | previous µs | this PR µs | speedup | program |
|---|---|---:|---:|---:|---:|---|
| prefill Q 37, prefix 4100, causal | FP8 | 32 | 5.31 | 5.31 | 1.0000 |
same program |
| prefill Q 1024, prefix 32779, causal | FP8 | 32 | 136.58 | 136.99 |
0.9979 | same program |
| prefill Q 1, prefix 0, causal | FP8 | 64 | 4.10 | 4.10 | 1.0019 | same
program |
| prefill Q 1, prefix 4100, causal | FP8 | 64 | 4.14 | 4.14 | 1.0037 |
same program |
| prefill Q 1, prefix 32779, causal | FP8 | 64 | 5.15 | 5.15 | 1.0000 |
same program |
| prefill Q 1, prefix 131077, causal | FP8 | 64 | 8.06 | 8.06 | 1.0000 |
same program |
| prefill Q 2, prefix 0, causal | FP8 | 64 | 4.14 | 4.13 | 1.0001 | same
program |
| prefill Q 2, prefix 4100, causal | FP8 | 64 | 4.82 | 4.82 | 1.0000 |
same program |
| prefill Q 3, prefix 0, causal | FP8 | 64 | 3.90 | 3.90 | 1.0000 | same
program |
| prefill Q 3, prefix 4100, causal | FP8 | 64 | 4.59 | 4.61 | 1.0000 |
same program |
| prefill Q 7, prefix 0, causal | FP8 | 64 | 3.97 | 3.97 | 1.0000 | same
program |
| prefill Q 7, prefix 4100, causal | FP8 | 64 | 4.58 | 4.58 | 1.0000 |
same program |
| prefill Q 8, prefix 0, causal | FP8 | 64 | 3.92 | 3.92 | 1.0000 | same
program |
| prefill Q 8, prefix 4100, causal | FP8 | 64 | 4.58 | 4.58 | 0.9999 |
same program |
| prefill Q 16, prefix 0, causal | FP8 | 64 | 3.92 | 3.92 | 1.0000 |
same program |
| prefill Q 16, prefix 4100, causal | FP8 | 64 | 4.64 | 4.64 | 1.0000 |
same program |
| prefill Q 37, prefix 0, causal | FP8 | 64 | 3.94 | 3.94 | 1.0000 |
same program |
| prefill Q 37, prefix 4100, causal | FP8 | 64 | 5.73 | 5.72 | 1.0000 |
same program |
| prefill Q 37, prefix 32779, causal | FP8 | 64 | 14.43 | 14.43 | 1.0000
| same program |
| prefill Q 37, prefix 131077, causal | FP8 | 64 | 40.13 | 40.11 |
1.0002 | same program |
| prefill Q 64, prefix 0, causal | FP8 | 64 | 3.97 | 3.97 | 1.0000 |
same program |
| prefill Q 64, prefix 4100, causal | FP8 | 64 | 6.66 | 6.66 | 1.0000 |
same program |
| prefill Q 128, prefix 0, causal | FP8 | 64 | 4.13 | 4.13 | 1.0000 |
same program |
| prefill Q 128, prefix 4100, causal | FP8 | 64 | 9.33 | 9.33 | 0.9999 |
same program |
| prefill Q 128, prefix 4100, causal, 2 sequences | FP8 | 64 | 8.18 |
8.21 | 0.9962 | same program |
| prefill Q 128, prefix 32779, causal | FP8 | 64 | 34.69 | 34.69 |
1.0004 | same program |
| prefill Q 128, prefix 131077, causal | FP8 | 64 | 123.69 | 123.73 |
0.9983 | same program |
| prefill Q 129, prefix 0, causal | FP8 | 64 | 4.10 | 4.10 | 1.0000 |
same program |
| prefill Q 129, prefix 4100, causal | FP8 | 64 | 9.39 | 9.38 | 1.0017 |
same program |
| prefill Q 1023, prefix 0, causal | FP8 | 64 | 10.32 | 10.32 | 0.9986 |
same program |
| prefill Q 1023, prefix 4100, causal | FP8 | 64 | 40.29 | 40.29 |
1.0000 | same program |
| prefill Q 1024, prefix 0, causal | FP8 | 64 | 10.45 | 10.43 | 1.0015 |
same program |
| prefill Q 1024, prefix 4100, causal | FP8 | 64 | 40.26 | 40.20 |
1.0008 | same program |
| prefill Q 1024, prefix 32779, causal | FP8 | 64 | 262.83 | 263.16 |
0.9976 | same program |
| prefill Q 1024, prefix 131077, causal | FP8 | 64 | 1072.85 | 1065.02 |
1.0068 | same program |
| prefill Q 4096, prefix 0, causal | FP8 | 64 | 69.76 | 69.78 | 0.9995 |
same program |
| prefill Q 4096, prefix 4100, causal | FP8 | 64 | 201.04 | 199.29 |
1.0108 | same program |
| prefill Q 4096, prefix 32779, causal | FP8 | 64 | 1125.30 | 1127.52 |
0.9980 | same program |
| prefill Q 4096, prefix 32779, causal, 2 sequences | FP8 | 64 | 785.83
| 785.91 | 0.9987 | same program |
| prefill Q 4096, prefix 32779, causal, 2048-query chunks | FP8 | 64 |
1139.01 | 1135.94 | 0.9997 | same program |
| prefill Q 4096, prefix 131077, causal | FP8 | 64 | 4429.01 | 4428.03 |
1.0002 | same program |
| prefill Q 4096, prefix 131077, causal, 2048-query chunks | FP8 | 64 |
4433.93 | 4436.04 | 0.9996 | same program |
| prefill Q 8192, prefix 0, causal | FP8 | 64 | 278.40 | 278.34 | 0.9999
| same program |
| prefill Q 8192, prefix 4100, causal | FP8 | 64 | 547.06 | 548.11 |
0.9980 | same program |
| prefill Q 8192, prefix 32779, causal | FP8 | 64 | 2458.34 | 2476.15 |
0.9928 | same program |
| prefill Q 8192, prefix 32779, causal, 2048-query chunks | FP8 | 64 |
2456.06 | 2459.42 | 0.9986 | same program |
| prefill Q 8192, prefix 131077, causal | FP8 | 64 | 9078.41 | 9053.56 |
1.0027 | same program |
| prefill Q 8192, prefix 131077, causal, 2048-query chunks | FP8 | 64 |
9000.06 | 9001.70 | 1.0001 | same program |
| prefill Q 16231, prefix 0, causal | FP8 | 64 | 1087.56 | 1080.32 |
0.9991 | same program |
| prefill Q 16231, prefix 4100, causal | FP8 | 64 | 1634.37 | 1633.22 |
1.0006 | same program |
| prefill Q 16231, prefix 32779, causal | FP8 | 64 | 5400.08 | 5438.18 |
0.9983 | same program |
| prefill Q 16231, prefix 32779, causal, 2048-query chunks | FP8 | 64 |
5444.37 | 5444.43 | 1.0000 | same program |
| prefill Q 16231, prefix 131077, causal | FP8 | 64 | 18485.31 |
18486.67 | 0.9999 | same program |
| prefill Q 16231, prefix 131077, causal, 2048-query chunks | FP8 | 64 |
18534.71 | 18531.21 | 1.0000 | same program |
| Q 1, K 4096 | FP8 | 32 | 4.00 | 4.00 | 1.0000 | same program |
| Q 1, K 32768 | FP8 | 32 | 4.83 | 4.83 | 1.0000 | same program |
| Q 1, K 131072 | FP8 | 32 | 7.78 | 7.74 | 1.0000 | same program |
| Q 1, K 1048576 | FP8 | 32 | 31.01 | 31.07 | 0.9990 | same program |
| Q 1, K 1048832 | FP8 | 32 | 31.10 | 31.10 | 1.0008 | same program |
| Q 3, K 8192 | FP8 | 32 | 4.83 | 4.85 | 1.0000 | same program |
| Q 3, K 1048832 | FP8 | 32 | 34.72 | 34.85 | 0.9986 | same program |
| Q 16, K 2048 | FP8 | 32 | 4.59 | 4.59 | 0.9966 | same program |
| Q 16, K 4096 | FP8 | 32 | 4.69 | 4.67 | 1.0033 | same program |
| Q 16, K 32768 | FP8 | 32 | 7.71 | 7.68 | 1.0042 | same program |
| Q 16, K 131072 | FP8 | 32 | 14.82 | 14.82 | 1.0000 | same program |
| Q 16, K 1048576 | FP8 | 32 | 69.41 | 69.36 | 1.0007 | same program |
| Q 16, K 1048832 | FP8 | 32 | 70.54 | 70.50 | 1.0018 | same program |
| Q 33, K 8192 | FP8 | 32 | 5.57 | 5.57 | 1.0000 | same program |
| Q 33, K 1048832 | FP8 | 32 | 188.05 | 189.97 | 0.9894 | same program |
| Q 37, K 4137 | FP8 | 32 | 5.34 | 5.34 | 1.0000 | same program |
| Q 128, K 2048 | FP8 | 32 | 5.86 | 5.86 | 1.0001 | same program |
| Q 128, K 4096 | FP8 | 32 | 7.10 | 7.10 | 1.0000 | same program |
| Q 128, K 32768 | FP8 | 32 | 21.15 | 21.15 | 1.0007 | same program |
| Q 128, K 131072 | FP8 | 32 | 63.81 | 63.82 | 1.0000 | same program |
| Q 128, K 131328 | FP8 | 32 | 64.21 | 64.22 | 0.9998 | same program |
| Q 130, K 8192 | FP8 | 32 | 10.46 | 10.46 | 1.0000 | same program |
| Q 130, K 8448 | FP8 | 32 | 10.72 | 10.72 | 1.0000 | same program |
| Q 130, K 65792 | FP8 | 32 | 38.80 | 38.83 | 0.9975 | same program |
| Q 132, K 2048 | FP8 | 32 | 6.85 | 6.85 | 0.9999 | same program |
| Q 132, K 8448 | FP8 | 32 | 10.66 | 10.66 | 1.0000 | same program |
| Q 132, K 65792 | FP8 | 32 | 39.14 | 39.14 | 1.0004 | same program |
| Q 1024, K 33803 | FP8 | 32 | 138.56 | 138.24 | 1.0025 | same program |
| Q 2052, K 2048 | FP8 | 32 | 23.90 | 23.90 | 0.9993 | same program |
| Q 2052, K 8448 | FP8 | 32 | 69.88 | 69.84 | 1.0006 | same program |
| Q 2053, K 2048 | FP8 | 32 | 24.18 | 24.22 | 1.0000 | same program |
| Q 2053, K 8448 | FP8 | 32 | 70.75 | 70.78 | 0.9991 | same program |
| Q 1, K 4096 | FP4 | 32 | 4.00 | 4.00 | 1.0000 | same program |
| Q 1, K 32768 | FP4 | 32 | 4.74 | 4.75 | 1.0000 | same program |
| Q 1, K 131072 | FP4 | 32 | 6.54 | 6.54 | 1.0024 | same program |
| Q 1, K 131328 | FP4 | 32 | 6.69 | 6.70 | 0.9977 | same program |
| Q 7, K 2048 | FP4 | 32 | 4.86 | 4.85 | 1.0000 | same program |
| Q 16, K 4096 | FP4 | 32 | 5.09 | 5.09 | 1.0000 | same program |
| Q 16, K 32768 | FP4 | 32 | 7.18 | 7.17 | 1.0044 | same program |
| Q 16, K 131072 | FP4 | 32 | 13.55 | 13.57 | 1.0000 | same program |
| Q 16, K 1048576 | FP4 | 32 | 63.18 | 63.20 | 1.0000 | same program |
| Q 16, K 1048832 | FP4 | 32 | 65.94 | 65.76 | 0.9998 | same program |
| Q 33, K 8192 | FP4 | 32 | 5.76 | 5.78 | 0.9972 | same program |
| Q 33, K 1048832 | FP4 | 32 | 136.91 | 136.43 | 1.0005 | same program |
| Q 128, K 4096 | FP4 | 32 | 6.75 | 6.74 | 1.0024 | same program |
| Q 128, K 32768 | FP4 | 32 | 19.71 | 19.74 | 1.0000 | same program |
| Q 128, K 131072 | FP4 | 32 | 61.50 | 61.49 | 1.0003 | same program |
| Q 130, K 65536 | FP4 | 32 | 35.84 | 35.86 | 0.9996 | same program |
| Q 130, K 65792 | FP4 | 32 | 37.78 | 37.78 | 1.0002 | same program |
| Q 1024, K 2048 | FP4 | 32 | 14.11 | 14.18 | 0.9955 | same program |
| Q 2052, K 2048 | FP4 | 32 | 24.05 | 24.05 | 0.9993 | same program |
| Q 2052, K 65792 | FP4 | 32 | 466.85 | 469.63 | 0.9956 | same program |

The family's other Cake variants (dense FP8 with 32 or 64 heads, dense
FP4 with 32 heads including fused metadata + logits sequences, and paged
FP8) ship on sm_100a and sm_103a only.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added an optimized FP8 short-route option for select query and
key/value sizes on supported hardware.
* **Tests**
  * Expanded coverage for additional query sizes on the FP8 short route.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery Huang <averyh@nvidia.com>

### [7ff89bc](https://github.com/flashinfer-ai/flashinfer/commit/7ff89bc5ece7de86e1891d59cee77d60c2e03739)

- **作者**: eigen
- **时间**: 2026-11-01T10:10:40Z
- **提交信息**: perf(cake_causal_conv1d): faster dweight flush in the non-deterministic autograd backward (#8176)

This PR speeds up the opt-in non-deterministic training backward
(`deterministic=False`) of the Cake causal conv1d kernels. It is a
performance follow-up to #8134, which added this mode and is merged on
main. The default stays deterministic. Rubin (`sm_107a`) timings are
still being measured and will be added to this description.

The kernels compute a packed width-4 depthwise causal convolution with
SiLU, training forward and backward. Activations are packed BF16 `[S,
C]`, and `cu_seqlens` gives the documents. The taps are `w[C, 4]`, with
an optional per-channel bias. Single rank takes FP32 or BF16 taps, an
optional FP32 or BF16 bias, and one of two SiLU-gradient policies:
`silu_grad_preactivation="bf16"` (default) or `"fp32"`. KCP (context
parallel) takes FP32 taps without bias, any world size W, and the
contiguous, zigzag and zigzag per document layouts.

What this PR changes:

- Single-rank backward: the dweight / dbias flush is chosen per program
and architecture (23 of the 34 programs change).
- KCP backward: coalesced dweight flush.
- CUDA graphs: captured backward calls without a caller workspace share
one zeroed workspace per capture and stream.
- Two benchmark fixes, both review follow-ups from #8134: `format_sota`
no longer raises `KeyError` when the non-deterministic time is missing,
and the KCP ahead column aligns the ranks' start.

The y and dx outputs stay bitwise equal to the deterministic packages,
dweight / dbias stay within their error budgets, and the forward
programs do not change.

Speedup is baseline latency / new latency. Above 1 means new is faster.
These are the backward geomean speedups over all rows of each
architecture:

- B200 (`sm_100a`): 1.016 vs #8134, 1.018 vs deterministic Cake, 3.640
vs the non-Cake SOTA.
- GB300 (`sm_103a`): 1.014 vs #8134, 1.019 vs deterministic Cake, 3.695
vs the non-Cake SOTA.

For the checkpointed step, the same three ratios are 1.009, 1.009 and
2.590 on B200, and 1.008, 1.010 and 2.673 on GB300. The table gives each
geomean with [min, max] over all shape rows of the op. The SOTA column
covers only the supported rows, with the count in parentheses.

| architecture | op | rows | det/new | SOTA/new (rows) | #8134/new |
|---|---|---|---|---|---|
| B200 (sm_100a) | fwd | 252 | 1.000 [0.950, 1.049] | 1.685 [1.061,
2.681] (198) | 0.999 [0.972, 1.026] |
| B200 (sm_100a) | bwd | 252 | 1.018 [0.966, 1.109] | 3.640 [1.447,
7.769] (198) | 1.016 [0.985, 1.142] |
| B200 (sm_100a) | ckpt | 252 | 1.009 [0.977, 1.065] | 2.590 [1.474,
4.578] (198) | 1.009 [0.981, 1.066] |
| GB300 (sm_103a) | fwd | 252 | 0.999 [0.954, 1.045] | 1.738 [1.167,
2.766] (198) | 1.000 [0.973, 1.041] |
| GB300 (sm_103a) | bwd | 252 | 1.019 [0.988, 1.119] | 3.695 [1.441,
8.126] (198) | 1.014 [0.991, 1.115] |
| GB300 (sm_103a) | ckpt | 252 | 1.010 [0.992, 1.072] | 2.673 [1.525,
4.897] (198) | 1.008 [0.993, 1.069] |

New is faster than the strongest eligible non-Cake implementation on
every supported row. The minimum SOTA/new is 1.061 on B200 and 1.167 on
GB300. The list below gives the backward geomean against #8134 by group.
Each range spans the single-rank routes or the KCP layouts of the group.

- B200: single rank 0.999-1.002, KCP W=1 1.012, W=2 1.014-1.020, W=4
1.018-1.028, W=8 1.028-1.031.
- GB300: single rank 1.003-1.011, W=1 1.012, W=2 1.011-1.012, W=4
1.018-1.026, W=8 1.023-1.024.

### Baselines

- **Deterministic Cake.** `flashinfer.cake_causal_conv1d_det_train`
(single rank) and `flashinfer.cake_causal_conv1d_det_train_kcp` (KCP),
at FlashInfer main `94666bab`. This PR does not change them.
- **#8134 (previous non-deterministic Cake).** This is the
`flashinfer.experimental.cake.cake_causal_conv1d_train_backend` package,
with its host files and rendered programs, as on main
`94666babec1801020de588103238954fc519d552`. #8134 merged as
`e8ab20d42ea4`, and the package has not changed on main since. It runs
with this branch's benchmark files, so only the package differs between
the #8134 and new arms.
- **New.** Branch head `81f952e8`. It was measured at `8ba1a4ae`, which
differs only in benchmark comments.
- **Non-Cake SOTA.** For each row, this is the fastest eligible
implementation among these candidates:
- Single rank: flash-linear-attention 0.6.0 `causal_conv1d`, Triton
backend and Gluon backend (`FLA_CONV_GLUON=1`). Dao-AILab causal-conv1d
1.7.0 `causal_conv1d_fn`, with atomic and with deterministic weight
gradient. nvidia-cudnn-frontend 1.32.1 `cudnn.ops.causal_conv1d`.
- KCP: flash-linear-attention 0.6.0 context-parallel `causal_conv1d`
(`cp_context`), Triton backend and CUDA backend (Dao kernel, contiguous
layout only). attention-gym `7d6439c19625`
`context_parallel_conv_history` + `short_conv`.
- **Eligibility.** An eligible implementation has the same features as
the Cake route at the same or higher precision. It must also pass the
numerics check against the Cake non-deterministic result. A mismatched
implementation is measured but never counts as best.
- **Why this is the strongest applicable comparison.** The SOTA cell is
the minimum latency over all eligible candidates for that row. Each
ratio therefore compares against the best eligible library for that row,
not against one fixed library. The candidates and rules are the same as
in #8134. On both B200 and GB300, the cells are set by FLA Gluon, cuDNN
FE, Dao (atomic and deterministic), FLA CP Triton and FLA CP CUDA. The
tables name the implementation of each cell, with the legend in each
caption.
- **Unsupported.** KCP zigzag per document covers 54 of the 252 rows per
op on each architecture (18 shapes × W=2, 4, 8). No eligible non-Cake
implementation exists for it. flash-linear-attention CP partitions are
contiguous or zigzag only. attention-gym CP is less precise: it uses
BF16 taps against Cake's FP32 taps, and it computes SiLU' at a different
preactivation precision.

### How the numbers were taken

- **Passes.** There are four passes per group, all on the same node (the
same two nodes for GB300 W=8), in the order #8134 (main), new, new,
#8134. Each pass imports the same benchmark files from `benchmarks/` at
the branch head. Det Cake and every non-Cake candidate run in every
pass, interleaved with the Cake non-deterministic mode in the same
rounds.
- **Statistic.** A pass value is the benchmark's median over rounds of
each round's median. Det Cake and SOTA take the median of the 4 pass
values. #8134 and new take the median of their 2 pass values, which is
their mean. Latency ranges in the tables are [min, max] over the passes.
Speedup ranges are [min, max] over shapes.
- **L2, launch mode and checks.** L2 is cold before every timed sample.
All timing uses eager PyTorch autograd, with no CUDA graph. Each KCP
pass checks every row on every rank: y and dx must be bitwise equal to
the deterministic result, and each dweight partial must be within
budget. Each single-rank pass records whether dx is bitwise equal and
the largest relative dweight difference.
- **Single rank.** fwd and bwd use the CUPTI span of the phase's kernels
(`flashinfer.testing.bench_gpu_time(enable_cupti=True,
cold_l2_cache=True)`). ckpt
(`torch.utils.checkpoint(use_reentrant=False)`, 2 × fwd + bwd) is
enqueued as a whole step behind a spin kernel and timed with CUDA
events, so the host enqueue is hidden. Each pass has 7 rounds. Even
rounds run det, non-det, then the non-Cake arms; odd rounds run them in
reverse order.
- **KCP, ahead column.** A barrier and an L2 flush come first. Then
every rank runs the same spin kernel while the host enqueues the phase.
A one-element all_reduce aligns the ranks, and CUDA events surround the
phase. The slowest rank is reported. Each pass has 3 rounds (the
benchmark default is 21). The arm order (det, non-det, then the non-Cake
candidates) rotates by one arm each round and is reversed in odd rounds.
With 3 rounds per pass, det leads the first two rounds and the first
non-Cake candidate leads the third. The non-deterministic arm never
leads; it takes the same positions in the #8134 and new passes. The ops
are fwd, bwd (the backward of a recorded forward) and ckpt (2 × fwd +
bwd).
- **Ops in the tables.** The tables report fwd, bwd and ckpt. The
single-rank fwd + bwd step was also measured, but it is not in the
tables.
- **Workloads.** There are 14 workloads. Single rank has 4 routes: FP32
taps without bias (the default), FP32 taps with the FP32 SiLU-gradient
preactivation, FP32 taps + FP32 bias, and BF16 taps + BF16 bias. KCP has
W=1, plus W=2, W=4 and W=8, each with the three layouts.
- **Shapes (18).** C=512 at S in {239718, 245028, 249866, 250340,
258574, 259042, 259584, 261393}, and S=250340 at C in {128, 256, 1024,
1160, 1280, 1344, 1536, 2048, 4096, 8192}. Each pack holds four unequal
documents.
- **Table layout.** Speedup is computed per shape. The summary tables
give latencies at S=250340, C=512, and speedups as geomean [min, max]
over the 18 shapes.
- **Noise floor.** The forward programs did not change, so the fwd
ratios show the noise floor. Against #8134 they are 0.999 [0.972, 1.026]
on B200 and 1.000 [0.973, 1.041] on GB300. Against det Cake they are
1.000 [0.950, 1.049] on B200 and 0.999 [0.954, 1.045] on GB300.
- **Hardware.** Versions are in each architecture's caption. On B200, no
other process was on the GPUs when each pass began, and clocks and power
were logged at the beginning and end of every pass. GB300 has 4 GPUs per
node.

| architecture | rows | node | concurrency |
|---|---|---|---|
| B200 | single rank × 4 routes; KCP W=1 and W=2 × 3 layouts | B200 node
1 | Concurrent on separate GPUs of one node: single-rank routes on
GPU0-3, one per GPU. KCP at the same time: W=2 contiguous then W=2
zigzag per document on GPU4-5; W=2 zigzag then W=1 on GPU6-7. |
| B200 | KCP W=4 × 3 layouts | B200 node 2 | W=4 contiguous and W=4
zigzag concurrently on GPU0-3 / GPU4-7, then W=4 zigzag per document
alone. |
| B200 | KCP W=8 × 3 layouts | B200 node 3 | One layout at a time on all
8 GPUs. |
| GB300 | single rank × 4 routes | GB300 node 1 | One route per GPU,
concurrently. |
| GB300 | KCP W=1 + W=2 | GB300 node 2 | W=2 contiguous and W=2 zigzag
concurrently, then W=2 zigzag per document and W=1 concurrently. |
| GB300 | KCP W=4 | GB300 node 3 | One layout at a time. |
| GB300 | KCP W=8 contiguous | GB300 nodes 4+5 | 2 nodes × 4 GPUs, one
NVLink domain. |
| GB300 | KCP W=8 zigzag and zigzag per document | GB300 nodes 6+7 | 2
nodes × 4 GPUs, one NVLink domain. |

### Where the new mode is slower

The slower lists count rows below 0.995 (more than 0.5 % slower than det
Cake or #8134) over all ops. There are 83 such rows on B200 (41 fwd) and
66 on GB300 (52 fwd). The forward programs did not change, so the fwd
rows show timing variation, not an effect of this PR. On 16 of those
B200 fwd rows and 28 of the GB300 fwd rows, the pass ranges do not
overlap, so this variation can exceed the pass-to-pass spread.

The row ids below match the slower-list comments:

- `sr_default`: single rank, FP32 taps, no bias, BF16 SiLU-gradient
preactivation (the default).
- `sr_fp32g`: FP32 SiLU-gradient preactivation.
- `sr_bias_f32`: FP32 taps + FP32 bias.
- `sr_dt_bias_bf16`: BF16 taps + BF16 bias.
- `kcp_wN[_layout]`: KCP W=N.

Rows given only by C are at S=250340.

bwd and ckpt rows more than 0.5 % slower than #8134 (speedup vs #8134):

- B200, 7 rows (worst first):
  - `sr_dt_bias_bf16` C4096 ckpt: 0.981 (pass ranges do not overlap)
  - `sr_default` C1536 ckpt: 0.984
  - `sr_fp32g` C4096 bwd: 0.985 (pass ranges do not overlap)
  - `kcp_w4_zigzag` S=261393, C=512 bwd: 0.989
  - `sr_bias_f32` C4096 ckpt: 0.991
  - `sr_bias_f32` C1024 bwd: 0.993
  - `sr_fp32g` C8192 bwd: 0.994
- GB300, 3 rows:
- `kcp_w2_zigzag` S=259584, C=512 bwd: 0.991 (pass ranges do not
overlap)
  - `sr_fp32g` C256 ckpt: 0.993 (pass ranges do not overlap)
  - `kcp_w8_contiguous` S=258574, C=512 bwd: 0.993

bwd and ckpt rows more than 0.5 % slower than det Cake (speedup vs det
Cake):

- B200, 38 rows. The largest are single-rank rows at large C:
- `sr_default` C8192 bwd: 0.966 (det 2189.53 us vs new 2266.47 us; 0.996
vs #8134; pass ranges do not overlap with either)
  - `sr_default` C4096 bwd: 0.974
  - `sr_default` C8192 ckpt: 0.977 (pass ranges do not overlap)

  #8134 is also slower than det Cake on these rows.
- GB300, 11 rows. The worst is `kcp_w1` C8192 bwd at 0.988 (pass ranges
do not overlap).

### B200 (sm_100a)

NVIDIA B200, sm_100a, 148 SMs, driver 580.82.07, CUDA 13.4 toolkit (nvcc
13.4.92), torch 2.14.1+cu130, x86_64. Timing: passes main (#8134),
branch (new), branch, main on the same node(s) per group; det Cake and
every non-Cake arm are timed in every pass, interleaved with the Cake
mode in the same rounds. Each pass value is the benchmark's median over
rounds of each round's median; det Cake and SOTA = median of the 4
passes, #8134 and new = median (the mean) of their 2 passes. Cold L2
before every timed sample; eager PyTorch autograd (no CUDA graph).
Single rank: fwd / bwd = CUPTI span of the phase's kernels
(flashinfer.testing.bench_gpu_time, enable_cupti, cold_l2_cache), 7
rounds per pass; ckpt = CUDA events around the whole checkpointed step
enqueued behind a spin kernel (host enqueue hidden). KCP: the 'ahead'
column: after a barrier and an L2 flush, a spin kernel of the same
length on every rank while the host enqueues the phase, a one-element
all_reduce aligns the ranks, CUDA events around the phase; slowest rank;
3 rounds per pass, the arm order rotated each round and reversed in odd
rounds. Latencies at S=250340, C=512: median [min, max] over passes;
speedups: geomean [min, max] over the workload's 18 shapes. SOTA = the
fastest eligible non-Cake implementation of the row (CU =
nvidia-cudnn-frontend 1.32.1 cudnn.ops.causal_conv1d; DA = Dao-AILab
causal-conv1d 1.7.0 causal_conv1d_fn, atomic weight gradient; DD =
Dao-AILab causal-conv1d 1.7.0 causal_conv1d_fn, deterministic weight
gradient; CPC = flash-linear-attention 0.6.0 context-parallel
causal_conv1d, CUDA backend (Dao kernel); CPT = flash-linear-attention
0.6.0 context-parallel causal_conv1d, Triton backend; FG =
flash-linear-attention 0.6.0 causal_conv1d, Gluon backend); a feature-
or precision-mismatched implementation is measured but never the
baseline. Ratios above 1 mean the new mode is faster; #8134 = the
previous non-deterministic package on FI main 94666bab.

| workload | node | op | det Cake, S=250340 C=512 | non-Cake SOTA,
S=250340 C=512 | #8134, S=250340 C=512 | new, S=250340 C=512 | speedup
vs det Cake, geomean [min, max] of 18 shapes | speedup vs non-Cake SOTA,
geomean [min, max] of 18 shapes | speedup vs #8134, geomean [min, max]
of 18 shapes |
|---|---|---|---|---|---|---|---|---|---|
| KCP W=1, one rank (every layout is the same partition), BF16
activations, FP32 taps, no bias | B200 node 1 | forward | 110.59 us
[110.59, 110.59] | 181.25 us [181.25, 181.25] CPT | 110.58 us [110.58,
110.59] | 110.59 us [110.59, 110.59] | 1.001 [0.997, 1.008] | 1.587
[1.149, 1.931] | 1.001 [0.999, 1.008] |
| KCP W=1, one rank (every layout is the same partition), BF16
activations, FP32 taps, no bias | B200 node 1 | backward | 166.12 us
[165.89, 166.91] | 902.15 us [901.63, 902.21] CPT | 164.11 us [163.87,
164.35] | 163.84 us [163.84, 163.84] | 1.017 [0.995, 1.099] | 5.190
[3.748, 6.543] | 1.012 [0.997, 1.062] |
| KCP W=1, one rank (every layout is the same partition), BF16
activations, FP32 taps, no bias | B200 node 1 | 2 x fwd + bwd
(checkpointed) | 386.04 us [384.00, 386.05] | 1.243 ms [1.243, 1.244]
CPT | 379.88 us [379.86, 379.90] | 380.39 us [379.90, 380.88] | 1.013
[1.002, 1.065] | 3.109 [2.227, 3.804] | 1.005 [0.999, 1.027] |
| KCP W=2, contiguous, BF16 activations, FP32 taps, no bias | B200 node
1 | forward | 75.78 us [75.78, 75.78] | 131.06 us [131.04, 131.07] CPT |
75.76 us [75.74, 75.78] | 75.78 us [75.78, 75.78] | 1.000 [0.993, 1.005]
| 1.708 [1.210, 2.224] | 1.000 [0.994, 1.003] |
| KCP W=2, contiguous, BF16 activations, FP32 taps, no bias | B200 node
1 | backward | 120.82 us [120.78, 120.83] | 558.06 us [556.67, 559.10]
CPC | 118.79 us [118.78, 118.80] | 116.73 us [116.72, 116.74] | 1.020
[0.990, 1.088] | 4.651 [2.412, 7.344] | 1.020 [1.000, 1.088] |
| KCP W=2, contiguous, BF16 activations, FP32 taps, no bias | B200 node
1 | 2 x fwd + bwd (checkpointed) | 259.75 us [258.86, 260.03] | 817.08
us [816.83, 818.45] CPT | 258.06 us [258.03, 258.08] | 255.98 us
[255.98, 255.98] | 1.009 [0.994, 1.046] | 3.119 [1.935, 4.578] | 1.009
[1.002, 1.045] |
| KCP W=2, zigzag, BF16 activations, FP32 taps, no bias | B200 node 1 |
forward | 79.84 us [79.79, 79.87] | 140.29 us [140.26, 140.29] CPT |
79.86 us [79.84, 79.87] | 79.86 us [79.86, 79.86] | 1.002 [0.993, 1.049]
| 1.798 [1.374, 2.605] | 1.001 [0.995, 1.012] |
| KCP W=2, zigzag, BF16 activations, FP32 taps, no bias | B200 node 1 |
backward | 124.90 us [122.88, 126.75] | 574.29 us [573.97, 575.04] CPT |
123.34 us [122.88, 123.81] | 121.86 us [120.88, 122.85] | 1.020 [0.990,
1.081] | 4.895 [2.649, 7.769] | 1.014 [1.000, 1.082] |
| KCP W=2, zigzag, BF16 activations, FP32 taps, no bias | B200 node 1 |
2 x fwd + bwd (checkpointed) | 268.79 us [268.26, 269.94] | 838.93 us
[838.18, 839.65] CPT | 268.16 us [268.06, 268.26] | 266.24 us [266.22,
266.26] | 1.011 [0.997, 1.056] | 3.213 [2.014, 4.573] | 1.008 [1.002,
1.034] |
| KCP W=2, zigzag per document, BF16 activations, FP32 taps, no bias |
B200 node 1 | forward | 83.42 us [82.93, 83.95] | unsupported | 83.47 us
[82.98, 83.97] | 82.49 us [82.03, 82.94] | 1.001 [0.983, 1.046] |
unsupported | 0.998 [0.982, 1.012] |
| KCP W=2, zigzag per document, BF16 activations, FP32 taps, no bias |
B200 node 1 | backward | 132.46 us [131.97, 133.09] | unsupported |
129.01 us [128.99, 129.02] | 129.00 us [128.99, 129.01] | 1.021 [0.985,
1.085] | unsupported | 1.015 [1.000, 1.085] |
| KCP W=2, zigzag per document, BF16 activations, FP32 taps, no bias |
B200 node 1 | 2 x fwd + bwd (checkpointed) | 286.70 us [286.69, 286.72]
| unsupported | 283.56 us [282.62, 284.50] | 282.64 us [282.59, 282.69]
| 1.008 [0.993, 1.046] | unsupported | 1.005 [0.999, 1.023] |
| single rank, BF16 activations, FP32 taps + FP32 bias | B200 node 1 |
forward | 86.00 us [85.95, 86.02] | 137.66 us [137.60, 137.70] FG |
85.95 us [85.95, 85.95] | 85.95 us [85.92, 85.98] | 1.001 [0.997, 1.006]
| 1.569 [1.285, 1.639] | 0.999 [0.993, 1.000] |
| single rank, BF16 activations, FP32 taps + FP32 bias | B200 node 1 |
backward | 156.03 us [155.97, 156.16] | 545.64 us [545.57, 545.70] FG |
155.79 us [155.74, 155.84] | 155.82 us [155.81, 155.84] | 0.998 [0.983,
1.032] | 3.214 [2.244, 3.523] | 1.002 [0.993, 1.022] |
| single rank, BF16 activations, FP32 taps + FP32 bias | B200 node 1 | 2
x fwd + bwd (checkpointed) | 339.75 us [339.49, 339.97] | 816.13 us
[816.13, 816.14] FG | 338.95 us [338.94, 338.96] | 338.95 us [338.94,
338.96] | 1.000 [0.986, 1.025] | 2.254 [1.820, 2.413] | 1.001 [0.991,
1.013] |
| single rank, BF16 activations, FP32 taps, no bias, BF16 SiLU-gradient
preactivation (default) | B200 node 1 | forward | 84.26 us [84.26,
84.29] | 133.28 us [133.25, 133.28] FG | 83.92 us [83.90, 83.94] | 83.95
us [83.94, 83.97] | 1.000 [0.990, 1.016] | 1.552 [1.268, 1.645] | 0.999
[0.991, 1.001] |
| single rank, BF16 activations, FP32 taps, no bias, BF16 SiLU-gradient
preactivation (default) | B200 node 1 | backward | 148.21 us [148.16,
148.22] | 411.98 us [411.95, 412.06] FG | 147.89 us [147.87, 147.90] |
147.84 us [147.84, 147.84] | 1.000 [0.966, 1.039] | 2.750 [2.159, 3.193]
| 1.002 [0.996, 1.025] |
| single rank, BF16 activations, FP32 taps, no bias, BF16 SiLU-gradient
preactivation (default) | B200 node 1 | 2 x fwd + bwd (checkpointed) |
326.66 us [326.66, 326.66] | 676.86 us [676.86, 676.86] FG | 326.65 us
[326.64, 326.66] | 326.66 us [326.66, 326.66] | 1.000 [0.977, 1.035] |
2.013 [1.781, 2.094] | 1.001 [0.984, 1.023] |
| single rank, BF16 activations, BF16 taps + BF16 bias | B200 node 1 |
forward | 85.14 us [85.09, 85.15] | 133.71 us [133.66, 133.73] FG |
85.15 us [85.15, 85.15] | 85.14 us [85.12, 85.15] | 1.000 [0.993, 1.003]
| 1.538 [1.247, 1.650] | 0.999 [0.981, 1.001] |
| single rank, BF16 activations, BF16 taps + BF16 bias | B200 node 1 |
backward | 156.53 us [156.51, 156.59] | 405.12 us [405.10, 405.15] FG |
156.06 us [156.05, 156.06] | 156.02 us [155.94, 156.10] | 0.999 [0.985,
1.019] | 2.610 [2.207, 3.436] | 1.002 [0.997, 1.023] |
| single rank, BF16 activations, BF16 taps + BF16 bias | B200 node 1 | 2
x fwd + bwd (checkpointed) | 338.94 us [338.91, 338.94] | 674.82 us
[674.82, 674.82] FG | 338.94 us [338.94, 338.94] | 338.94 us [338.93,
338.94] | 0.999 [0.980, 1.026] | 1.955 [1.745, 2.160] | 1.001 [0.981,
1.017] |
| single rank, BF16 activations, FP32 taps, no bias, FP32 SiLU-gradient
preactivation | B200 node 1 | forward | 84.18 us [84.16, 84.19] | 217.50
us [216.90, 217.79] CU | 84.06 us [84.06, 84.06] | 84.06 us [84.06,
84.06] | 1.001 [0.996, 1.011] | 2.448 [2.026, 2.681] | 1.000 [0.993,
1.005] |
| single rank, BF16 activations, FP32 taps, no bias, FP32 SiLU-gradient
preactivation | B200 node 1 | backward | 148.58 us [148.58, 148.61] |
615.50 us [614.02, 615.97] CU | 145.81 us [145.79, 145.82] | 145.79 us
[145.73, 145.86] | 1.009 [0.981, 1.026] | 3.840 [2.800, 5.767] | 0.999
[0.985, 1.003] |
| single rank, BF16 activations, FP32 taps, no bias, FP32 SiLU-gradient
preactivation | B200 node 1 | 2 x fwd + bwd (checkpointed) | 327.43 us
[326.66, 328.70] | 967.68 us [967.65, 967.68] CU | 324.58 us [324.56,
324.61] | 324.10 us [323.68, 324.53] | 1.009 [0.997, 1.062] | 2.701
[2.353, 3.083] | 1.003 [0.996, 1.060] |
| KCP W=4, contiguous, BF16 activations, FP32 taps, no bias | B200 node
2 | forward | 53.25 us [53.25, 53.25] | 80.85 us [79.87, 81.92] CPT |
53.25 us [53.25, 53.25] | 53.25 us [53.25, 53.25] | 0.998 [0.972, 1.008]
| 1.557 [1.061, 2.168] | 0.999 [0.982, 1.009] |
| KCP W=4, contiguous, BF16 activations, FP32 taps, no bias | B200 node
2 | backward | 88.02 us [87.92, 88.03] | 313.09 us [312.86, 314.14] CPC
| 85.42 us [84.90, 85.95] | 83.94 us [83.94, 83.95] | 1.028 [1.002,
1.078] | 3.735 [1.805, 6.797] | 1.028 [1.001, 1.118] |
| KCP W=4, contiguous, BF16 activations, FP32 taps, no bias | B200 node
2 | 2 x fwd + bwd (checkpointed) | 180.22 us [180.21, 180.27] | 496.54
us [496.13, 498.18] CPT | 179.87 us [179.55, 180.19] | 178.15 us
[178.14, 178.16] | 1.012 [0.999, 1.047] | 2.753 [1.652, 4.376] | 1.012
[0.998, 1.059] |
| KCP W=4, zigzag, BF16 activations, FP32 taps, no bias | B200 node 2 |
forward | 57.34 us [57.34, 57.36] | 93.18 us [93.18, 93.22] CPT | 57.34
us [57.34, 57.34] | 57.35 us [57.34, 57.36] | 0.999 [0.989, 1.003] |
1.699 [1.290, 2.449] | 1.001 [0.988, 1.026] |
| KCP W=4, zigzag, BF16 activations, FP32 taps, no bias | B200 node 2 |
backward | 94.70 us [94.19, 95.18] | 356.73 us [356.00, 357.33] CPT |
91.63 us [91.10, 92.16] | 91.13 us [90.11, 92.14] | 1.028 [0.990, 1.109]
| 4.148 [2.268, 7.256] | 1.019 [0.989, 1.142] |
| KCP W=4, zigzag, BF16 activations, FP32 taps, no bias | B200 node 2 |
2 x fwd + bwd (checkpointed) | 192.54 us [192.51, 194.54] | 528.45 us
[528.35, 530.08] CPT | 193.51 us [192.50, 194.53] | 192.19 us [191.95,
192.43] | 1.012 [0.997, 1.047] | 2.873 [1.801, 4.376] | 1.012 [1.004,
1.059] |
| KCP W=4, zigzag per document, BF16 activations, FP32 taps, no bias |
B200 node 2 | forward | 59.93 us [59.41, 61.36] | unsupported | 60.41 us
[59.52, 61.30] | 60.38 us [60.37, 60.40] | 0.999 [0.950, 1.017] |
unsupported | 1.000 [0.983, 1.008] |
| KCP W=4, zigzag per document, BF16 activations, FP32 taps, no bias |
B200 node 2 | backward | 98.23 us [97.25, 98.30] | unsupported | 96.19
us [96.14, 96.24] | 94.21 us [94.21, 94.21] | 1.022 [0.990, 1.083] |
unsupported | 1.018 [0.998, 1.091] |
| KCP W=4, zigzag per document, BF16 activations, FP32 taps, no bias |
B200 node 2 | 2 x fwd + bwd (checkpointed) | 202.73 us [201.63, 202.83]
| unsupported | 202.58 us [202.43, 202.74] | 199.94 us [199.57, 200.30]
| 1.011 [1.001, 1.028] | unsupported | 1.013 [1.002, 1.055] |
| KCP W=8, contiguous, BF16 activations, FP32 taps, no bias | B200 node
3 | forward | 42.98 us [42.91, 42.98] | 61.96 us [61.44, 61.98] CPT |
42.98 us [42.98, 42.99] | 42.97 us [42.96, 42.98] | 0.997 [0.973, 1.011]
| 1.534 [1.266, 2.071] | 0.993 [0.972, 1.002] |
| KCP W=8, contiguous, BF16 activations, FP32 taps, no bias | B200 node
3 | backward | 75.73 us [75.66, 75.74] | 182.51 us [182.24, 183.57] CPC
| 74.24 us [73.73, 74.75] | 71.66 us [71.65, 71.68] | 1.028 [1.007,
1.099] | 2.848 [1.447, 6.025] | 1.031 [1.007, 1.134] |
| KCP W=8, contiguous, BF16 activations, FP32 taps, no bias | B200 node
3 | 2 x fwd + bwd (checkpointed) | 139.26 us [139.25, 139.26] | 308.07
us [307.20, 308.21] CPT | 139.70 us [139.12, 140.29] | 137.19 us
[137.18, 137.20] | 1.017 [1.004, 1.035] | 2.378 [1.474, 4.003] | 1.020
[1.002, 1.058] |
| KCP W=8, zigzag, BF16 activations, FP32 taps, no bias | B200 node 3 |
forward | 45.06 us [45.06, 45.09] | 75.64 us [74.86, 75.84] CPT | 45.06
us [45.06, 45.06] | 45.06 us [45.06, 45.06] | 1.000 [0.989, 1.013] |
1.719 [1.441, 2.322] | 1.001 [0.999, 1.006] |
| KCP W=8, zigzag, BF16 activations, FP32 taps, no bias | B200 node 3 |
backward | 75.78 us [75.78, 76.78] | 207.88 us [207.87, 207.95] CPT |
75.78 us [75.78, 75.78] | 74.73 us [74.70, 74.75] | 1.026 [1.001, 1.076]
| 3.214 [1.768, 6.462] | 1.028 [0.995, 1.142] |
| KCP W=8, zigzag, BF16 activations, FP32 taps, no bias | B200 node 3 |
2 x fwd + bwd (checkpointed) | 145.34 us [145.18, 146.24] | 336.11 us
[335.84, 336.40] CPT | 143.91 us [143.36, 144.46] | 143.31 us [143.31,
143.31] | 1.016 [1.000, 1.045] | 2.505 [1.640, 4.028] | 1.015 [1.002,
1.062] |
| KCP W=8, zigzag per document, BF16 activations, FP32 taps, no bias |
B200 node 3 | forward | 48.12 us [47.12, 49.12] | unsupported | 47.10 us
[47.09, 47.10] | 47.64 us [47.10, 48.18] | 1.000 [0.979, 1.024] |
unsupported | 0.999 [0.979, 1.018] |
| KCP W=8, zigzag per document, BF16 activations, FP32 taps, no bias |
B200 node 3 | backward | 79.86 us [79.82, 79.87] | unsupported | 78.27
us [77.82, 78.72] | 76.80 us [76.80, 76.80] | 1.031 [1.004, 1.089] |
unsupported | 1.030 [1.007, 1.142] |
| KCP W=8, zigzag per document, BF16 activations, FP32 taps, no bias |
B200 node 3 | 2 x fwd + bwd (checkpointed) | 151.54 us [151.49, 152.54]
| unsupported | 151.58 us [151.57, 151.58] | 149.50 us [149.49, 149.50]
| 1.012 [0.998, 1.049] | unsupported | 1.016 [1.000, 1.066] |

### GB300 (sm_103a)

NVIDIA GB300, sm_103a, 152 SMs, driver 580.159.03, CUDA 13.4 toolkit
(nvcc 13.4.92), torch 2.14.1+cu130, NCCL 2.30.7, aarch64. Timing: passes
main (#8134), branch (new), branch, main on the same node(s) per group;
det Cake and every non-Cake arm are timed in every pass, interleaved
with the Cake mode in the same rounds. Each pass value is the
benchmark's median over rounds of each round's median; det Cake and SOTA
= median of the 4 passes, #8134 and new = median (the mean) of their 2
passes. Cold L2 before every timed sample; eager PyTorch autograd (no
CUDA graph). Single rank: fwd / bwd = CUPTI span of the phase's kernels
(flashinfer.testing.bench_gpu_time, enable_cupti, cold_l2_cache), 7
rounds per pass; ckpt = CUDA events around the whole checkpointed step
enqueued behind a spin kernel (host enqueue hidden). KCP: the 'ahead'
column: after a barrier and an L2 flush, a spin kernel of the same
length on every rank while the host enqueues the phase, a one-element
all_reduce aligns the ranks, CUDA events around the phase; slowest rank;
3 rounds per pass, the arm order rotated each round and reversed in odd
rounds. Latencies at S=250340, C=512: median [min, max] over passes;
speedups: geomean [min, max] over the workload's 18 shapes. SOTA = the
fastest eligible non-Cake implementation of the row (CU =
nvidia-cudnn-frontend 1.32.1 cudnn.ops.causal_conv1d; DA = Dao-AILab
causal-conv1d 1.7.0 causal_conv1d_fn, atomic weight gradient; DD =
Dao-AILab causal-conv1d 1.7.0 causal_conv1d_fn, deterministic weight
gradient; CPC = flash-linear-attention 0.6.0 context-parallel
causal_conv1d, CUDA backend (Dao kernel); CPT = flash-linear-attention
0.6.0 context-parallel causal_conv1d, Triton backend; FG =
flash-linear-attention 0.6.0 causal_conv1d, Gluon backend); a feature-
or precision-mismatched implementation is measured but never the
baseline. Ratios above 1 mean the new mode is faster; #8134 = the
previous non-deterministic package on FI main 94666bab.

| workload | node | op | det Cake, S=250340 C=512 | non-Cake SOTA,
S=250340 C=512 | #8134, S=250340 C=512 | new, S=250340 C=512 | speedup
vs det Cake, geomean [min, max] of 18 shapes | speedup vs non-Cake SOTA,
geomean [min, max] of 18 shapes | speedup vs #8134, geomean [min, max]
of 18 shapes |
|---|---|---|---|---|---|---|---|---|---|
| single rank, BF16 activations, FP32 taps + FP32 bias | GB300 node 1 |
forward | 79.52 us [79.50, 79.52] | 124.69 us [124.67, 124.70] FG |
79.65 us [79.65, 79.65] | 79.64 us [79.62, 79.66] | 1.000 [0.996, 1.005]
| 1.582 [1.278, 1.713] | 1.000 [0.999, 1.000] |
| single rank, BF16 activations, FP32 taps + FP32 bias | GB300 node 1 |
backward | 140.49 us [140.46, 140.51] | 514.86 us [514.82, 514.91] FG |
140.61 us [140.61, 140.61] | 140.61 us [140.61, 140.61] | 1.007 [0.993,
1.039] | 3.371 [2.315, 3.723] | 1.003 [1.000, 1.057] |
| single rank, BF16 activations, FP32 taps + FP32 bias | GB300 node 1 |
2 x fwd + bwd (checkpointed) | 305.53 us [304.88, 305.55] | 756.13 us
[756.10, 756.22] FG | 304.51 us [304.51, 304.51] | 304.55 us [304.53,
304.58] | 1.004 [0.997, 1.018] | 2.363 [1.907, 2.497] | 1.002 [0.995,
1.028] |
| single rank, BF16 activations, FP32 taps, no bias, BF16 SiLU-gradient
preactivation (default) | GB300 node 1 | forward | 79.49 us [79.46,
79.52] | 123.74 us [123.74, 123.74] FG | 79.73 us [79.71, 79.74] | 79.73
us [79.71, 79.74] | 1.000 [0.997, 1.005] | 1.550 [1.317, 1.679] | 1.000
[1.000, 1.000] |
| single rank, BF16 activations, FP32 taps, no bias, BF16 SiLU-gradient
preactivation (default) | GB300 node 1 | backward | 135.95 us [135.94,
135.97] | 388.19 us [388.13, 388.22] FG | 136.30 us [136.29, 136.32] |
133.89 us [133.86, 133.92] | 1.013 [1.004, 1.027] | 2.850 [2.229, 3.101]
| 1.011 [1.000, 1.052] |
| single rank, BF16 activations, FP32 taps, no bias, BF16 SiLU-gradient
preactivation (default) | GB300 node 1 | 2 x fwd + bwd (checkpointed) |
298.63 us [298.43, 298.66] | 628.89 us [628.38, 629.38] FG | 299.16 us
[299.14, 299.18] | 296.88 us [296.64, 297.12] | 1.007 [1.000, 1.026] |
2.088 [1.860, 2.193] | 1.006 [0.999, 1.022] |
| single rank, BF16 activations, BF16 taps + BF16 bias | GB300 node 1 |
forward | 78.80 us [78.78, 78.82] | 120.93 us [120.93, 120.93] FG |
78.83 us [78.82, 78.85] | 78.83 us [78.82, 78.85] | 1.000 [0.996, 1.003]
| 1.561 [1.260, 1.721] | 1.000 [1.000, 1.000] |
| single rank, BF16 activations, BF16 taps + BF16 bias | GB300 node 1 |
backward | 140.64 us [140.64, 140.67] | 369.46 us [369.44, 369.47] FG |
140.42 us [140.42, 140.42] | 140.42 us [140.42, 140.43] | 1.009 [0.991,
1.024] | 2.646 [2.251, 3.122] | 1.003 [1.000, 1.041] |
| single rank, BF16 activations, BF16 taps + BF16 bias | GB300 node 1 |
2 x fwd + bwd (checkpointed) | 302.94 us [302.50, 303.44] | 608.67 us
[608.64, 608.72] FG | 303.99 us [303.50, 304.48] | 304.02 us [303.52,
304.53] | 1.005 [0.996, 1.036] | 2.027 [1.876, 2.312] | 1.002 [0.998,
1.026] |
| single rank, BF16 activations, FP32 taps, no bias, FP32 SiLU-gradient
preactivation | GB300 node 1 | forward | 79.62 us [79.58, 79.62] |
211.26 us [211.01, 211.58] CU | 79.74 us [79.74, 79.74] | 79.74 us
[79.71, 79.78] | 1.000 [0.997, 1.004] | 2.531 [2.190, 2.755] | 1.000
[1.000, 1.001] |
| single rank, BF16 activations, FP32 taps, no bias, FP32 SiLU-gradient
preactivation | GB300 node 1 | backward | 136.90 us [136.86, 136.90] |
597.27 us [595.62, 597.65] CU | 137.17 us [137.15, 137.18] | 136.50 us
[136.48, 136.51] | 1.009 [1.000, 1.053] | 3.942 [3.043, 5.071] | 1.003
[0.999, 1.008] |
| single rank, BF16 activations, FP32 taps, no bias, FP32 SiLU-gradient
preactivation | GB300 node 1 | 2 x fwd + bwd (checkpointed) | 298.66 us
[298.66, 298.69] | 934.54 us [934.51, 934.58] CU | 297.89 us [297.65,
298.13] | 297.62 us [297.60, 297.65] | 1.006 [1.000, 1.023] | 2.872
[2.481, 3.278] | 1.000 [0.993, 1.004] |
| KCP W=1, one rank (every layout is the same partition), BF16
activations, FP32 taps, no bias | GB300 node 2 | forward | 93.34 us
[92.77, 94.08] | 163.84 us [163.41, 164.26] CPT | 94.60 us [94.59,
94.61] | 94.62 us [94.61, 94.62] | 0.998 [0.986, 1.007] | 1.684 [1.250,
2.010] | 0.999 [0.986, 1.014] |
| KCP W=1, one rank (every layout is the same partition), BF16
activations, FP32 taps, no bias | GB300 node 2 | backward | 147.86 us
[147.84, 148.50] | 856.45 us [855.98, 857.46] CPT | 144.07 us [143.76,
144.38] | 143.79 us [143.78, 143.81] | 1.019 [0.988, 1.074] | 5.446
[3.794, 7.181] | 1.012 [1.002, 1.051] |
| KCP W=1, one rank (every layout is the same partition), BF16
activations, FP32 taps, no bias | GB300 node 2 | 2 x fwd + bwd
(checkpointed) | 331.16 us [330.27, 331.20] | 1.168 ms [1.168, 1.169]
CPT | 327.04 us [327.04, 327.04] | 327.07 us [327.07, 327.07] | 1.011
[0.995, 1.063] | 3.341 [2.349, 4.178] | 1.005 [0.999, 1.026] |
| KCP W=2, contiguous, BF16 activations, FP32 taps, no bias | GB300 node
2 | forward | 67.23 us [67.22, 67.28] | 120.46 us [120.43, 120.78] CPT |
67.26 us [67.25, 67.26] | 67.23 us [67.23, 67.23] | 0.995 [0.978, 1.008]
| 1.781 [1.167, 2.437] | 1.003 [0.986, 1.022] |
| KCP W=2, contiguous, BF16 activations, FP32 taps, no bias | GB300 node
2 | backward | 117.40 us [116.40, 118.43] | 529.04 us [529.01, 529.74]
CPT | 116.36 us [116.32, 116.40] | 114.35 us [114.34, 114.37] | 1.018
[0.993, 1.080] | 4.738 [2.306, 7.941] | 1.011 [1.000, 1.051] |
| KCP W=2, contiguous, BF16 activations, FP32 taps, no bias | GB300 node
2 | 2 x fwd + bwd (checkpointed) | 242.75 us [242.34, 243.34] | 757.94
us [757.41, 759.41] CPT | 242.29 us [242.26, 242.32] | 240.78 us
[240.26, 241.30] | 1.009 [0.997, 1.046] | 3.193 [1.803, 4.897] | 1.006
[0.999, 1.027] |
| KCP W=2, zigzag, BF16 activations, FP32 taps, no bias | GB300 node 2 |
forward | 72.60 us [72.05, 73.12] | 129.96 us [129.81, 130.43] CPT |
72.09 us [72.08, 72.10] | 71.67 us [71.23, 72.11] | 0.997 [0.954, 1.013]
| 1.843 [1.206, 2.766] | 0.999 [0.986, 1.012] |
| KCP W=2, zigzag, BF16 activations, FP32 taps, no bias | GB300 node 2 |
backward | 118.23 us [118.19, 119.15] | 534.90 us [534.40, 535.04] CPT |
118.18 us [118.16, 118.21] | 116.15 us [116.14, 116.16] | 1.020 [0.996,
1.119] | 4.843 [2.563, 8.126] | 1.011 [0.991, 1.068] |
| KCP W=2, zigzag, BF16 activations, FP32 taps, no bias | GB300 node 2 |
2 x fwd + bwd (checkpointed) | 249.23 us [249.20, 249.25] | 782.50 us
[782.21, 783.73] CPT | 249.29 us [249.23, 249.34] | 247.72 us [247.20,
248.24] | 1.009 [0.999, 1.044] | 3.260 [1.868, 4.892] | 1.006 [0.999,
1.029] |
| KCP W=2, zigzag per document, BF16 activations, FP32 taps, no bias |
GB300 node 2 | forward | 75.42 us [75.39, 75.44] | unsupported | 75.41
us [75.39, 75.42] | 75.42 us [75.42, 75.42] | 1.002 [0.999, 1.014] |
unsupported | 1.000 [0.993, 1.006] |
| KCP W=2, zigzag per document, BF16 activations, FP32 taps, no bias |
GB300 node 2 | backward | 124.04 us [123.54, 124.58] | unsupported |
122.54 us [122.53, 122.56] | 120.48 us [120.48, 120.48] | 1.021 [0.996,
1.088] | unsupported | 1.012 [0.996, 1.074] |
| KCP W=2, zigzag per document, BF16 activations, FP32 taps, no bias |
GB300 node 2 | 2 x fwd + bwd (checkpointed) | 263.81 us [262.75, 263.84]
| unsupported | 262.29 us [261.79, 262.78] | 260.73 us [259.71, 261.74]
| 1.010 [0.997, 1.036] | unsupported | 1.007 [1.000, 1.032] |
| KCP W=4, contiguous, BF16 activations, FP32 taps, no bias | GB300 node
3 | forward | 49.10 us [48.56, 50.13] | 76.45 us [76.43, 76.45] CPT |
48.66 us [48.54, 48.77] | 48.57 us [48.56, 48.58] | 0.999 [0.975, 1.011]
| 1.629 [1.167, 2.340] | 1.001 [0.991, 1.013] |
| KCP W=4, contiguous, BF16 activations, FP32 taps, no bias | GB300 node
3 | backward | 83.62 us [83.62, 84.62] | 297.60 us [297.09, 297.65] CPC
| 89.27 us [88.80, 89.74] | 83.62 us [83.60, 83.63] | 1.024 [1.000,
1.092] | 3.810 [1.832, 7.243] | 1.026 [1.001, 1.104] |
| KCP W=4, contiguous, BF16 activations, FP32 taps, no bias | GB300 node
3 | 2 x fwd + bwd (checkpointed) | 167.70 us [167.57, 168.58] | 467.59
us [466.10, 470.67] CPT | 174.28 us [173.92, 174.64] | 165.57 us
[165.54, 165.60] | 1.012 [1.001, 1.032] | 2.842 [1.633, 4.664] | 1.016
[1.000, 1.053] |
| KCP W=4, zigzag, BF16 activations, FP32 taps, no bias | GB300 node 3 |
forward | 52.88 us [52.86, 52.90] | 87.62 us [86.86, 87.71] CPT | 52.86
us [52.86, 52.86] | 52.86 us [52.85, 52.86] | 0.999 [0.986, 1.019] |
1.748 [1.321, 2.551] | 0.998 [0.973, 1.010] |
| KCP W=4, zigzag, BF16 activations, FP32 taps, no bias | GB300 node 3 |
backward | 91.77 us [90.75, 91.81] | 330.90 us [330.40, 331.42] CPT |
89.74 us [89.71, 89.76] | 89.73 us [89.73, 89.73] | 1.023 [1.005, 1.085]
| 4.116 [2.130, 7.563] | 1.018 [0.995, 1.085] |
| KCP W=4, zigzag, BF16 activations, FP32 taps, no bias | GB300 node 3 |
2 x fwd + bwd (checkpointed) | 182.42 us [181.92, 182.91] | 492.44 us
[491.65, 493.02] CPT | 179.78 us [179.76, 179.79] | 177.80 us [177.78,
177.82] | 1.013 [0.995, 1.072] | 2.924 [1.790, 4.654] | 1.010 [0.999,
1.054] |
| KCP W=4, zigzag per document, BF16 activations, FP32 taps, no bias |
GB300 node 3 | forward | 54.94 us [54.94, 54.94] | unsupported | 54.94
us [54.93, 54.94] | 54.94 us [54.94, 54.94] | 0.996 [0.966, 1.007] |
unsupported | 1.000 [0.989, 1.018] |
| KCP W=4, zigzag per document, BF16 activations, FP32 taps, no bias |
GB300 node 3 | backward | 94.86 us [94.83, 95.36] | unsupported | 94.37
us [93.86, 94.88] | 91.78 us [91.78, 91.78] | 1.025 [1.000, 1.103] |
unsupported | 1.022 [1.000, 1.115] |
| KCP W=4, zigzag per document, BF16 activations, FP32 taps, no bias |
GB300 node 3 | 2 x fwd + bwd (checkpointed) | 189.78 us [189.06, 190.10]
| unsupported | 188.71 us [188.35, 189.07] | 187.53 us [187.04, 188.02]
| 1.012 [0.998, 1.044] | unsupported | 1.012 [1.000, 1.057] |
| KCP W=8, contiguous, BF16 activations, FP32 taps, no bias | GB300
nodes 4+5 | forward | 38.54 us [38.48, 38.56] | 59.28 us [59.02, 59.57]
CPT | 38.54 us [38.53, 38.54] | 38.54 us [38.53, 38.56] | 0.999 [0.971,
1.026] | 1.627 [1.326, 2.210] | 0.997 [0.978, 1.017] |
| KCP W=8, contiguous, BF16 activations, FP32 taps, no bias | GB300
nodes 4+5 | backward | 69.79 us [69.25, 71.30] | 174.50 us [173.70,
175.78] CPC | 69.78 us [69.28, 70.27] | 69.26 us [69.25, 69.28] | 1.022
[0.991, 1.066] | 2.845 [1.441, 6.401] | 1.023 [0.993, 1.101] |
| KCP W=8, contiguous, BF16 activations, FP32 taps, no bias | GB300
nodes 4+5 | 2 x fwd + bwd (checkpointed) | 127.13 us [126.59, 127.65] |
288.66 us [287.92, 289.42] CPT | 129.16 us [128.66, 129.66] | 127.62 us
[126.61, 128.64] | 1.010 [0.992, 1.040] | 2.411 [1.525, 4.233] | 1.016
[1.000, 1.061] |
| KCP W=8, zigzag, BF16 activations, FP32 taps, no bias | GB300 nodes
6+7 | forward | 42.66 us [42.64, 42.66] | 71.31 us [70.82, 71.33] CPT |
42.64 us [42.62, 42.66] | 42.65 us [42.64, 42.66] | 1.002 [0.993, 1.032]
| 1.757 [1.483, 2.387] | 1.000 [0.991, 1.012] |
| KCP W=8, zigzag, BF16 activations, FP32 taps, no bias | GB300 nodes
6+7 | backward | 69.79 us [69.30, 71.33] | 194.47 us [194.22, 195.20]
CPT | 69.26 us [69.25, 69.28] | 67.24 us [67.23, 67.25] | 1.028 [1.000,
1.101] | 3.136 [1.771, 6.612] | 1.024 [0.996, 1.111] |
| KCP W=8, zigzag, BF16 activations, FP32 taps, no bias | GB300 nodes
6+7 | 2 x fwd + bwd (checkpointed) | 136.01 us [134.82, 136.83] | 311.99
us [311.82, 312.96] CPT | 136.86 us [136.83, 136.88] | 133.27 us
[132.77, 133.78] | 1.015 [0.998, 1.035] | 2.487 [1.615, 4.239] | 1.014
[1.000, 1.052] |
| KCP W=8, zigzag per document, BF16 activations, FP32 taps, no bias |
GB300 nodes 6+7 | forward | 46.70 us [46.69, 46.75] | unsupported |
44.67 us [44.67, 44.67] | 44.69 us [44.67, 44.70] | 0.997 [0.960, 1.045]
| unsupported | 1.003 [0.986, 1.041] |
| KCP W=8, zigzag per document, BF16 activations, FP32 taps, no bias |
GB300 nodes 6+7 | backward | 75.92 us [75.42, 76.45] | unsupported |
75.87 us [75.42, 76.32] | 75.39 us [75.39, 75.39] | 1.026 [1.005, 1.091]
| unsupported | 1.023 [1.000, 1.100] |
| KCP W=8, zigzag per document, BF16 activations, FP32 taps, no bias |
GB300 nodes 6+7 | 2 x fwd + bwd (checkpointed) | 147.07 us [147.06,
147.10] | unsupported | 142.99 us [142.99, 142.99] | 142.98 us [142.96,
143.01] | 1.015 [1.002, 1.054] | unsupported | 1.013 [1.000, 1.069] |

### Rubin (sm_107a): pending, results to be added

### Other variants and per-shape data

This PR does not change the other Cake variants, the deterministic
packages `flashinfer.cake_causal_conv1d_det_train` and
`flashinfer.cake_causal_conv1d_det_train_kcp`; both the deterministic
and the non-deterministic packages cover `sm_100a`, `sm_103a` and
`sm_107a`.

Every shape row with absolute values (756 per architecture) and the full
lists of rows below 0.995 are in the PR comments: two comments per
architecture for the shape rows, plus one comment per slower list.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

- **Bug Fixes**
- Improved gradient-reduction behavior across supported GPU
architectures.
- Backward calls recorded on the same CUDA Graph capture and stream now
reuse a zeroed workspace; larger calls replace it with a sufficiently
sized buffer.
- Benchmark output now handles missing non-deterministic timings without
attempting to calculate an unavailable ratio.
- **Chores**
- Benchmark rounds increased from 7 to 21, with rotating arm order and
shared spin durations for more consistent comparisons.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [3bcec81](https://github.com/flashinfer-ai/flashinfer/commit/3bcec819fc4531ce18591d5ced9e478297212ad8)

- **作者**: eigen
- **时间**: 2026-11-01T10:00:21Z
- **提交信息**: perf(cake_gdn_train): re-plan sm_107a scan segment tables for the R200 SM count (#8181)

This PR changes only host-side planning in
`flashinfer.experimental.cake.cake_gdn_train`, the non-deterministic
single-GPU variant of Cake's Gated DeltaNet (GDN) chunked training
kernel with gradients. On sm_107a (R200), it re-plans the scan segment
tables of the forward and adjoint chains for the R200 SM count. It also
adds a per-architecture cost table, `CHAIN_PLAN`, which prices each
candidate scan table for the chain that runs it and takes a deeper (64,
1) split table when that saves at least 2 µs and prices at or below
0.95x the default. Only sm_107a is listed, and no device code changes on
any architecture. The planned tables on B200 (sm_100a) and B300 / GB300
(sm_103a) are byte-identical to main, so those architectures are
unaffected.

Speedup is baseline latency / new latency, so values above 1 mean the
new non-deterministic head is faster. Each speedup is the median of the
paired group ratios measured inside one process, and the bracketed
values are the [min, max] of those ratios. The first baseline is the
deterministic Cake package `flashinfer.experimental.cake_gdn_det_train`
from current main, which already includes the two-stream overlap from
#8161. The second is, per cell, the fastest cuDNN frontend 1.32.1 FROST
GDN arm. In the arm names, ck0 / ck64 keep chunk states every 0 / 64
tokens and bi is batch-invariant mode. ck0 keeps no chunk states and its
backward recomputes them, so ck64 is the like-for-like arm. FROST is the
strongest non-Cake implementation that runs on R200: FLA 0.6.0 (Triton),
measured on the same R200 class earlier in this series, was never the
fastest, and FlashQLA does not support sm_107a. Each row is one packed
variable-length GDN chunked training call on one GPU with head dim 128,
BF16 q/k/v and output gradient, and FP32 g and beta (H = query/key
heads, HV = value heads, T = total tokens). Five shapes have tables
changed by this PR and three are unchanged controls, as the last column
shows. Every changed shape passes the same accuracy budget as the rest
of the series against an FP64 chunked reference: rel-RMS ≤ 1e-2 and
max-abs ≤ 2e-2 of max|ref| on every output and gradient. Worst measured
rel-RMS is 4.17e-03 to 4.18e-03, identical to the deterministic package,
and worst max-abs/max|ref| is 6.55e-03 to 7.68e-03. Results are bitwise
reproducible run to run. All three arms ran in one process on one NVIDIA
R200 (sm_107a, compute capability 10.7, 212 SMs; driver 620.62, CUDA
13.0 runtime, PyTorch 2.14.1+cu130). They were timed in ABBA-paired
groups with 100 warm-up and 300 steady iterations per block under a
sustained-load protocol (group tolerance 1%, drift limit 2%, at least 5
groups for any re-run). No cell needed a re-run and no power-cap
throttling was observed. The operations are fwd, bwd, fwd+bwd and ckpt,
an activation-checkpointed step (two forwards plus one backward).

R200 (sm_107a, 212 SMs), CUDA 13.0, latencies in ms, three arms timed in
one process.

| GPU / architecture | workload / shape / dtype / mode | operation |
deterministic Cake latency | non-Cake SOTA latency | new
non-deterministic Cake latency | speedup vs deterministic Cake | speedup
vs non-Cake SOTA | tables changed by this PR |
|---|---|---|---|---|---|---|---|---|
| R200 sm_107a (212 SMs) | `r07_1x16384_h8` (H=8, HV=16, T=16384) BF16
packed | fwd | 0.1956 ms | 0.1973 ms FROST ck0 | 0.1728 ms | 1.131
[1.131, 1.132] | 1.142 [1.140, 1.143] | yes |
| R200 sm_107a (212 SMs) | `r07_1x16384_h8` (H=8, HV=16, T=16384) BF16
packed | bwd | 0.2735 ms | 0.6081 ms FROST ck64 | 0.2532 ms | 1.081
[1.079, 1.081] | 2.408 [2.403, 2.410] | yes |
| R200 sm_107a (212 SMs) | `r07_1x16384_h8` (H=8, HV=16, T=16384) BF16
packed | fwd+bwd | 0.4341 ms | 0.8006 ms FROST ck64 | 0.3923 ms | 1.106
[1.106, 1.107] | 2.040 [2.038, 2.044] | yes |
| R200 sm_107a (212 SMs) | `r07_1x16384_h8` (H=8, HV=16, T=16384) BF16
packed | ckpt | 0.6801 ms | 1.2598 ms FROST ck64 | 0.6408 ms | 1.062
[1.058, 1.062] | 1.940 [1.940, 1.946] | yes |
| R200 sm_107a (212 SMs) | `pair_h1_hv3` (H=1, HV=3, T=32768) BF16
packed | fwd | 0.1282 ms | 0.1689 ms FROST ck0 | 0.1098 ms | 1.166
[1.165, 1.170] | 1.543 [1.537, 1.544] | yes |
| R200 sm_107a (212 SMs) | `pair_h1_hv3` (H=1, HV=3, T=32768) BF16
packed | bwd | 0.1820 ms | 0.3924 ms FROST ck64 | 0.1674 ms | 1.087
[1.086, 1.089] | 2.343 [2.338, 2.345] | yes |
| R200 sm_107a (212 SMs) | `pair_h1_hv3` (H=1, HV=3, T=32768) BF16
packed | fwd+bwd | 0.2812 ms | 0.5906 ms FROST ck64 | 0.2452 ms | 1.147
[1.145, 1.149] | 2.408 [2.402, 2.408] | yes |
| R200 sm_107a (212 SMs) | `pair_h1_hv3` (H=1, HV=3, T=32768) BF16
packed | ckpt | 0.5608 ms | 1.0535 ms FROST ck64 | 0.5497 ms | 1.017
[1.017, 1.024] | 1.921 [1.913, 1.922] | yes |
| R200 sm_107a (212 SMs) | `pair_h2_hv6` (H=2, HV=6, T=32768) BF16
packed | fwd | 0.1539 ms | 0.1781 ms FROST ck0 | 0.1400 ms | 1.100
[1.098, 1.101] | 1.274 [1.273, 1.275] | yes |
| R200 sm_107a (212 SMs) | `pair_h2_hv6` (H=2, HV=6, T=32768) BF16
packed | bwd | 0.2484 ms | 0.5046 ms FROST ck64 | 0.2358 ms | 1.052
[1.052, 1.055] | 2.135 [2.133, 2.138] | yes |
| R200 sm_107a (212 SMs) | `pair_h2_hv6` (H=2, HV=6, T=32768) BF16
packed | fwd+bwd | 0.3673 ms | 0.6975 ms FROST ck64 | 0.3419 ms | 1.074
[1.074, 1.075] | 2.038 [2.035, 2.045] | yes |
| R200 sm_107a (212 SMs) | `pair_h2_hv6` (H=2, HV=6, T=32768) BF16
packed | ckpt | 0.6215 ms | 1.1609 ms FROST ck64 | 0.6143 ms | 1.012
[1.008, 1.012] | 1.884 [1.883, 1.887] | yes |
| R200 sm_107a (212 SMs) | `g3_16x4096_h1` (H=1, HV=3, T=65536) BF16
packed | fwd | 0.1359 ms | 0.1685 ms FROST ck0 | 0.1366 ms | 0.995
[0.993, 0.996] | 1.235 [1.234, 1.236] | yes |
| R200 sm_107a (212 SMs) | `g3_16x4096_h1` (H=1, HV=3, T=65536) BF16
packed | bwd | 0.2430 ms | 0.5127 ms FROST ck64 | 0.2273 ms | 1.070
[1.066, 1.071] | 2.257 [2.256, 2.259] | yes |
| R200 sm_107a (212 SMs) | `g3_16x4096_h1` (H=1, HV=3, T=65536) BF16
packed | fwd+bwd | 0.3441 ms | 0.7090 ms FROST ck64 | 0.3299 ms | 1.043
[1.043, 1.043] | 2.147 [2.143, 2.148] | yes |
| R200 sm_107a (212 SMs) | `g3_16x4096_h1` (H=1, HV=3, T=65536) BF16
packed | ckpt | 0.6178 ms | 1.1646 ms FROST ck64 | 0.6074 ms | 1.019
[1.016, 1.021] | 1.912 [1.912, 1.916] | yes |
| R200 sm_107a (212 SMs) | `pair_h16_hv48` (H=16, HV=48, T=32768) BF16
packed | fwd | 0.7692 ms | 0.3369 ms FROST ck0 | 0.7147 ms | 1.076
[1.076, 1.077] | 0.471 [0.471, 0.472] | yes |
| R200 sm_107a (212 SMs) | `pair_h16_hv48` (H=16, HV=48, T=32768) BF16
packed | bwd | 1.3261 ms | 2.1370 ms FROST ck64 | 1.3454 ms | 0.986
[0.985, 0.986] | 1.589 [1.589, 1.590] | yes |
| R200 sm_107a (212 SMs) | `pair_h16_hv48` (H=16, HV=48, T=32768) BF16
packed | fwd+bwd | 2.0534 ms | 2.4677 ms FROST ck64 | 2.0238 ms | 1.015
[1.014, 1.015] | 1.219 [1.219, 1.220] | yes |
| R200 sm_107a (212 SMs) | `pair_h16_hv48` (H=16, HV=48, T=32768) BF16
packed | ckpt | 2.8542 ms | 2.8986 ms FROST ck64 | 2.7720 ms | 1.030
[1.030, 1.030] | 1.046 [1.045, 1.046] | yes |
| R200 sm_107a (212 SMs) | `r01_4x4096_h8` (H=8, HV=16, T=16384) BF16
packed | fwd | 0.1652 ms | 0.1745 ms FROST ck0 bi | 0.1659 ms | 0.996
[0.996, 0.996] | 1.052 [1.051, 1.053] | no |
| R200 sm_107a (212 SMs) | `r01_4x4096_h8` (H=8, HV=16, T=16384) BF16
packed | bwd | 0.2460 ms | 0.6069 ms FROST ck64 | 0.2470 ms | 0.996
[0.996, 0.997] | 2.455 [2.449, 2.458] | no |
| R200 sm_107a (212 SMs) | `r01_4x4096_h8` (H=8, HV=16, T=16384) BF16
packed | fwd+bwd | 0.3773 ms | 0.8021 ms FROST ck64 | 0.3789 ms | 0.996
[0.995, 0.996] | 2.115 [2.107, 2.128] | no |
| R200 sm_107a (212 SMs) | `r01_4x4096_h8` (H=8, HV=16, T=16384) BF16
packed | ckpt | 0.6262 ms | 1.2573 ms FROST ck64 | 0.6326 ms | 0.991
[0.989, 0.991] | 1.989 [1.981, 1.992] | no |
| R200 sm_107a (212 SMs) | `p7074_P1_241817x6_h2` (H=2, HV=6, T=241817)
BF16 packed | fwd | 0.6537 ms | 0.5108 ms FROST ck0 bi | 0.6556 ms |
0.997 [0.996, 0.999] | 0.779 [0.779, 0.780] | no |
| R200 sm_107a (212 SMs) | `p7074_P1_241817x6_h2` (H=2, HV=6, T=241817)
BF16 packed | bwd | 1.1960 ms | 2.4179 ms FROST ck64 bi | 1.1916 ms |
1.004 [1.004, 1.004] | 2.031 [2.030, 2.031] | no |
| R200 sm_107a (212 SMs) | `p7074_P1_241817x6_h2` (H=2, HV=6, T=241817)
BF16 packed | fwd+bwd | 1.8159 ms | 2.9241 ms FROST ck64 bi | 1.8127 ms
| 1.002 [1.002, 1.002] | 1.613 [1.613, 1.613] | no |
| R200 sm_107a (212 SMs) | `p7074_P1_241817x6_h2` (H=2, HV=6, T=241817)
BF16 packed | ckpt | 2.5081 ms | 3.5398 ms FROST ck64 bi | 2.5053 ms |
1.001 [1.001, 1.001] | 1.413 [1.412, 1.413] | no |
| R200 sm_107a (212 SMs) | `pair_h8_hv24` (H=8, HV=24, T=32768) BF16
packed | fwd | 0.3821 ms | 0.3134 ms FROST ck0 | 0.3837 ms | 0.997
[0.996, 0.997] | 0.818 [0.818, 0.819] | no |
| R200 sm_107a (212 SMs) | `pair_h8_hv24` (H=8, HV=24, T=32768) BF16
packed | bwd | 0.7020 ms | 1.5200 ms FROST ck64 bi | 0.7024 ms | 1.000
[0.999, 1.000] | 2.164 [2.163, 2.165] | no |
| R200 sm_107a (212 SMs) | `pair_h8_hv24` (H=8, HV=24, T=32768) BF16
packed | fwd+bwd | 1.0514 ms | 1.7650 ms FROST ck64 | 1.0523 ms | 0.999
[0.999, 0.999] | 1.677 [1.677, 1.678] | no |
| R200 sm_107a (212 SMs) | `pair_h8_hv24` (H=8, HV=24, T=32768) BF16
packed | ckpt | 1.4722 ms | 2.1704 ms FROST ck64 | 1.4726 ms | 1.000
[1.000, 1.000] | 1.474 [1.472, 1.475] | no |

Reading:

- Against deterministic Cake on the changed shapes, fwd+bwd / ckpt are:
`r07_1x16384_h8` 1.106 / 1.062, `pair_h1_hv3` 1.147 / 1.017,
`pair_h2_hv6` 1.074 / 1.012, `g3_16x4096_h1` 1.043 / 1.019 and
`pair_h16_hv48` 1.015 / 1.030. Forward is 1.076 to 1.166 on every
changed shape except `g3_16x4096_h1`. Backward is 1.052 to 1.087 on
every changed shape except `pair_h16_hv48`.
- Two changed-shape cells are below 1 against deterministic Cake.
`pair_h16_hv48` bwd is 0.986: deterministic main gained a two-stream
adjoint grouping on this shape in #8161, and this PR changes only that
shape's forward table. `g3_16x4096_h1` fwd is 0.995, and its forward
table is unchanged.
- The three controls are at parity with deterministic Cake, from 0.991
to 1.004.
- Against FROST, the new head is faster on every bwd, fwd+bwd and ckpt
cell (1.046 to 2.455). Its forward is also faster on `r07_1x16384_h8`,
`pair_h1_hv3`, `pair_h2_hv6`, `g3_16x4096_h1` and `r01_4x4096_h8` (1.052
to 1.543). FROST ck0 is faster on the forward of `pair_h16_hv48`
(0.471), `p7074_P1_241817x6_h2` (0.779, ck0 bi) and `pair_h8_hv24`
(0.818).

Rows for the 216-SM R200 are still being measured and will be added to
this PR as a comment or body edit when they are ready.

The kernel's other Cake variants, all on main, are the deterministic
single-GPU `flashinfer.experimental.cake_gdn_det_train`, the
non-deterministic single-GPU
`flashinfer.experimental.cake.cake_gdn_train` (#8157, which this PR
tunes), the deterministic context-parallel
`flashinfer.experimental.cake_gdn_det_train_kcp` and the
non-deterministic context-parallel
`flashinfer.experimental.cake_gdn_train_kcp` (#8172). The two
context-parallel variants are both reached through
`flashinfer.cake_gdn_train_kcp(deterministic=...)`, and the family ships
on sm_100a, sm_103a and sm_107a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added architecture-aware scan planning that can select deeper forward
and backward tables when estimated savings meet configured thresholds.
* Documented how the new table selections affect segment-boundary
outputs and how to keep results deterministic by pinning scan settings.
* **Bug Fixes**
* Improved validation of selected plans, including checks for accuracy,
repeatability, and compatibility with pinned settings.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [4fc6840](https://github.com/flashinfer-ai/flashinfer/commit/4fc68403245081c50a2cb240388a25d31f0d166e)

- **作者**: eigen
- **时间**: 2026-11-01T09:41:44Z
- **提交信息**: perf(cake_kda): take the BF16 KDA prefill bin-mix build on sm_103a where its plan shortens the longest bin (#8180)

The Cake chunked KDA (Kimi Delta Attention) prefill behind
`flashinfer.recurrent_kda(..., backend="cake")` has 85 modules: 51 with
BF16 inputs and 34 with TF32 inputs. They come in a fused single-kernel
form (M128, M64 value split, N16 chain) and a split form (map prefix,
carry scan, affine apply), with FP32 or BF16 state and optional
checkpoint rows. This PR adds no module and no new generated program. It
changes the prepared BF16-input path with FP32 state
(`flashinfer.prepare_bf16_kda_prefill`) on sm_103a. The bin-mix build of
the work-binned turnover program already ships on sm_100a. This PR also
lists its sm_103a build. On sm_103a, a launch runs bin-mix only when
three conditions hold. First, the bin-mix rule admits the launch.
Second, its plan shortens the launch's longest bin, with each give
counted as one chunk on its helper. Third, no single-chunk give goes to
a helper whose own task is longer than the owner's shorter task. Other
admitted sm_103a launches keep the turnover build. The sm_100a rule does
not change, and no B200 launch changes program. The baseline is the
previous Cake version on FlashInfer main. Outputs are bit-identical to
main on every measured row. On GB300, three rows with 12 heads and no
gate bound are faster: BS16 x T64 goes from 23.10 to 21.41 us (1.08x),
BS16 x T128 from 34.18 to 33.83 us (1.01x), and BS16 x T256 from 57.09
to 52.22 us (1.09x). All other rows on both GPUs are TIE, which means no
difference beyond the measurement band. The table has one row per shape:
12 or 16 heads, no gate lower bound or -5, and 14 sequence-length
shapes. It gives the median latency in microseconds per call, with cold
L2.

B200: NVIDIA B200, sm_100a, 148 SMs, driver 580.82.07. GB300: NVIDIA
GB300, sm_103a, 152 SMs, driver 580.159.03. CUDA 13.4 (nvcc), PyTorch
2.14.1+cu130.

| heads | gate lower bound | sequence lengths | B200 main | B200 this PR
| speedup | GB300 main | GB300 this PR | speedup |
|---:|---|---|---:|---:|---:|---:|---:|---:|
| 12 | none | 8192 | 218.56 | 218.69 | 1.00x TIE | 212.83 | 213.22 |
1.00x TIE |
| 12 | none | 16384 | 378.53 | 378.37 | 1.00x TIE | 362.31 | 362.72 |
1.00x TIE |
| 12 | none | 32768 | 687.62 | 688.27 | 1.00x TIE | 648.07 | 648.24 |
1.00x TIE |
| 12 | none | 2x8192 | 371.70 | 372.38 | 1.00x TIE | 358.05 | 358.55 |
1.00x TIE |
| 12 | none | 3000+13384 | 395.39 | 395.28 | 1.00x TIE | 381.52 | 382.43
| 1.00x TIE |
| 12 | none | 4x4096 | 232.90 | 232.80 | 1.00x TIE | 219.30 | 219.26 |
1.00x TIE |
| 12 | none | 2x(8128+64) | 376.00 | 376.06 | 1.00x TIE | 361.68 |
362.13 | 1.00x TIE |
| 12 | none | 8x(1024+64) | 109.76 | 109.79 | 1.00x TIE | 101.70 |
101.76 | 1.00x TIE |
| 12 | none | BS4 x T64 | 16.19 | 16.19 | 1.00x TIE | 15.20 | 15.20 |
1.00x TIE |
| 12 | none | BS16 x T64 | 22.85 | 22.85 | 1.00x TIE | 23.10 | 21.41 |
1.08x |
| 12 | none | BS64 x T64 | 58.94 | 58.86 | 1.00x TIE | 54.08 | 54.05 |
1.00x TIE |
| 12 | none | BS16 x T128 | 36.45 | 36.42 | 1.00x TIE | 34.18 | 33.83 |
1.01x |
| 12 | none | BS16 x T256 | 56.67 | 56.67 | 1.00x TIE | 57.09 | 52.22 |
1.09x |
| 12 | none | BS16 x T(17..255) | 37.34 | 37.31 | 1.00x TIE | 35.30 |
35.33 | 1.00x TIE |
| 16 | none | 8192 | 268.16 | 268.22 | 1.00x TIE | 266.42 | 267.01 |
1.00x TIE |
| 16 | none | 16384 | 466.32 | 465.68 | 1.00x TIE | 447.65 | 449.19 |
1.00x TIE |
| 16 | none | 32768 | 879.41 | 879.60 | 1.00x TIE | 823.28 | 824.61 |
1.00x TIE |
| 16 | none | 2x8192 | 486.78 | 486.78 | 1.00x TIE | 466.75 | 468.47 |
1.00x TIE |
| 16 | none | 3000+13384 | 478.64 | 479.90 | 1.00x TIE | 461.86 | 462.85
| 1.00x TIE |
| 16 | none | 4x4096 | 264.13 | 264.21 | 1.00x TIE | 245.95 | 246.11 |
1.00x TIE |
| 16 | none | 2x(8128+64) | 492.58 | 492.78 | 1.00x TIE | 470.87 |
471.59 | 1.00x TIE |
| 16 | none | 8x(1024+64) | 112.30 | 112.35 | 1.00x TIE | 104.74 |
104.80 | 1.00x TIE |
| 16 | none | BS4 x T64 | 16.42 | 16.42 | 1.00x TIE | 15.41 | 15.41 |
1.00x TIE |
| 16 | none | BS16 x T64 | 25.82 | 25.86 | 1.00x TIE | 23.52 | 23.55 |
1.00x TIE |
| 16 | none | BS64 x T64 | 69.09 | 69.06 | 1.00x TIE | 65.12 | 65.12 |
1.00x TIE |
| 16 | none | BS16 x T128 | 39.10 | 39.14 | 1.00x TIE | 35.23 | 35.23 |
1.00x TIE |
| 16 | none | BS16 x T256 | 66.02 | 66.02 | 1.00x TIE | 58.47 | 58.56 |
1.00x TIE |
| 16 | none | BS16 x T(17..255) | 41.54 | 41.54 | 1.00x TIE | 37.25 |
37.25 | 1.00x TIE |
| 12 | -5 | 8192 | 161.30 | 161.18 | 1.00x TIE | 150.98 | 151.74 | 0.99x
TIE |
| 12 | -5 | 16384 | 261.25 | 261.60 | 1.00x TIE | 244.67 | 245.89 |
1.00x TIE |
| 12 | -5 | 32768 | 453.50 | 453.92 | 1.00x TIE | 424.26 | 424.83 |
1.00x TIE |
| 12 | -5 | 2x8192 | 285.79 | 285.57 | 1.00x TIE | 240.27 | 240.80 |
1.00x TIE |
| 12 | -5 | 3000+13384 | 275.04 | 275.20 | 1.00x TIE | 255.63 | 256.37 |
1.00x TIE |
| 12 | -5 | 4x4096 | 193.28 | 193.31 | 1.00x TIE | 179.68 | 179.71 |
1.00x TIE |
| 12 | -5 | 2x(8128+64) | 356.13 | 356.22 | 1.00x TIE | 243.68 | 245.46
| 0.99x TIE |
| 12 | -5 | 8x(1024+64) | 111.36 | 111.42 | 1.00x TIE | 103.17 | 103.17
| 1.00x TIE |
| 12 | -5 | BS4 x T64 | 11.30 | 11.30 | 1.00x TIE | 10.50 | 10.46 |
1.00x TIE |
| 12 | -5 | BS16 x T64 | 27.71 | 27.71 | 1.00x TIE | 25.89 | 25.92 |
1.00x TIE |
| 12 | -5 | BS64 x T64 | 67.65 | 67.62 | 1.00x TIE | 63.04 | 63.10 |
1.00x TIE |
| 12 | -5 | BS16 x T128 | 33.34 | 33.36 | 1.00x TIE | 31.20 | 31.17 |
1.00x TIE |
| 12 | -5 | BS16 x T256 | 47.76 | 47.71 | 1.00x TIE | 44.83 | 44.83 |
1.00x TIE |
| 12 | -5 | BS16 x T(17..255) | 31.10 | 31.14 | 1.00x TIE | 29.41 |
29.34 | 1.00x TIE |
| 16 | -5 | 8192 | 195.14 | 195.78 | 1.00x TIE | 191.43 | 192.43 | 0.99x
TIE |
| 16 | -5 | 16384 | 323.18 | 323.52 | 1.00x TIE | 307.94 | 308.66 |
1.00x TIE |
| 16 | -5 | 32768 | 584.72 | 583.01 | 1.00x TIE | 557.15 | 556.29 |
1.00x TIE |
| 16 | -5 | 2x8192 | 289.15 | 289.89 | 1.00x TIE | 273.57 | 273.95 |
1.00x TIE |
| 16 | -5 | 3000+13384 | 337.76 | 337.02 | 1.00x TIE | 331.38 | 332.47 |
1.00x TIE |
| 16 | -5 | 4x4096 | 205.41 | 205.41 | 1.00x TIE | 182.56 | 182.56 |
1.00x TIE |
| 16 | -5 | 2x(8128+64) | 358.43 | 358.48 | 1.00x TIE | 341.86 | 341.86
| 1.00x TIE |
| 16 | -5 | 8x(1024+64) | 88.61 | 88.61 | 1.00x TIE | 76.74 | 76.64 |
1.00x TIE |
| 16 | -5 | BS4 x T64 | 11.68 | 11.68 | 1.00x TIE | 10.82 | 10.82 |
1.00x TIE |
| 16 | -5 | BS16 x T64 | 25.09 | 25.09 | 1.00x TIE | 23.23 | 23.23 |
1.00x TIE |
| 16 | -5 | BS64 x T64 | 67.55 | 67.62 | 1.00x TIE | 63.91 | 63.90 |
1.00x TIE |
| 16 | -5 | BS16 x T128 | 34.18 | 34.18 | 1.00x TIE | 32.00 | 32.03 |
1.00x TIE |
| 16 | -5 | BS16 x T256 | 48.96 | 48.99 | 1.00x TIE | 45.66 | 45.70 |
1.00x TIE |
| 16 | -5 | BS16 x T(17..255) | 36.27 | 36.32 | 1.00x TIE | 33.76 |
33.74 | 1.00x TIE |

- B200: speedup 1.00x .. 1.00x over 56 rows (0 faster, 56 TIE: no
difference beyond the measurement band)
- GB300: speedup 0.99x .. 1.09x over 56 rows (3 faster, 53 TIE: no
difference beyond the measurement band)

The kernel's other Cake variants, the TF32-input modules and the
BF16-state forms, keep their behavior; the family ships on sm_100a and
sm_103a, and this PR changes only the sm_103a routing.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added bin-mix prefill support for SM_103a GPUs when workloads meet the
required scheduling conditions.
* Eligible workloads can now use the bin-mix execution path on both
SM_100a and SM_103a GPUs.
* Workloads that do not meet the SM_103a conditions continue using the
existing execution path.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery Huang <averyh@nvidia.com>

### [f061f72](https://github.com/flashinfer-ai/flashinfer/commit/f061f7267364b14098658f609741267e0b361623)

- **作者**: eigen
- **时间**: 2026-11-01T09:15:15Z
- **提交信息**: docs(cake_mhc_det_train): side-stream token ranges at hidden 5120 / 7168 after #8175 (#8185)

The side-stream note in `docs/api/mhc.rst` still says `backward_finish`
waits under a full-SM side hold at every token count up to 4096 on SM100
at hidden 5120 and 7168. Since #8175 it completes at most of those token
counts. This updates the note to list the ranges that still wait: 1-896,
1921-2112, 2689-2816 and 3585-3648 at hidden 5120, and 1-640 and
961-1024 at hidden 7168. Docs only.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Documentation**
* Clarified the documented `backward_finish` wait conditions for SM100:
at hidden size 5120, they apply to token counts 1–896, 1921–2112,
2689–2816, and 3585–3648; at hidden size 7168, they apply to counts
1–640 and 961–1024.
* Documentation for hidden size 4096 and other architectures remains
unchanged.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery Huang <averyh@nvidia.com>

### [73bf098](https://github.com/flashinfer-ai/flashinfer/commit/73bf098e1c0bc9ce73c08fb32ba403ab78c4256e)

- **作者**: eigen
- **时间**: 2026-11-01T09:13:01Z
- **提交信息**: perf(cake_rmsnorm_silu_gate): non-deterministic long-input forward/backward routes and backward kernel update (#8178)

`cake_rmsnorm_silu_gate` computes `y = RMSNorm(x, w) * SiLU(z)` on BF16
rows of head dim 128 and has five variants: one forward, plus a
deterministic and a non-deterministic backward that each write the
weight gradient in BF16 or FP32. This PR changes only the
`deterministic=False` (non-deterministic) path from #8164; the API and
the numerical contract stay the same: y, dx and dz remain bitwise equal
to the deterministic path, and dw stays within the deterministic
backward's error bound. On sm_100a and sm_103a, inputs from 2400 rows (T
x H) per SM run a new forward kernel (T >= 8192 in the tables); each CTA
walks up to six 32-row blocks and loads the next block while it computes
the current one. On sm_107a, inputs from 1024 rows per SM run the
backward on 128-thread CTAs of 8-row blocks, with at most 8 CTAs per SM
(T >= 8192 on the 212-SM board). On all three targets, a backward CTA
that runs few blocks now sums its weight gradient in FP32 before the
FP64 cross-CTA reduction, and it issues its relaxed block-claim atomic
after the block's loads.

### Speedup

A ratio above 1 means this PR's non-deterministic path is faster. Ranges
are given per band: T <= 129 / T 1031-4097 / T >= 8192.

- **vs deterministic Cake, `fwd`:** from T = 8192 the new forward is
1.097-1.132x on B200 and 1.084-1.134x on GB300. At all other T, and at
every T on R200 (212-SM board), both modes run the same kernel (B200
0.997-1.000x, GB300 0.987-1.014x, R200 (212-SM board) 0.998-1.006x).
- **vs deterministic Cake, eager `bwd`:** B200 4.073-4.713x /
1.109-1.729x / 1.047-1.061x, GB300 8.390-10.567x / 1.270-3.286x /
1.055-1.073x, R200 (212-SM board) 2.146-2.377x / 1.079-1.298x /
1.031-1.070x. The new path is faster in every `bwd`, `bwd (CUDA graph)`
and captured ckpt row on all three GPUs except R200 (212-SM board) ckpt
at T = 7.
- **vs deterministic Cake, `bwd (CUDA graph)`:** B200 1.145-1.183x /
1.110-1.188x / 1.049-1.063x, GB300 1.271-1.354x / 1.076-1.276x /
1.054-1.074x, R200 (212-SM board) 1.009-1.172x (T = 1 and 7 n.s.) /
1.064-1.252x / 1.027-1.064x.
- **vs deterministic Cake, `ckpt 2×fwd+bwd (CUDA graph)`:** B200
1.021-1.072x / 1.027-1.085x / 1.068-1.092x, GB300 1.103-1.128x /
1.020-1.116x / 1.071-1.100x, R200 (212-SM board) 0.969-1.062x /
1.026-1.114x / 1.012-1.025x. T = 1 and 7 are n.s. on all three GPUs.
- **vs best non-Cake, eager `bwd`:** faster at every T. B200
7.451-14.644x / 3.396-7.235x / 1.056-2.040x, GB300 5.153-10.330x /
2.865-6.523x / 1.020-1.696x, R200 (212-SM board) 1.791-3.218x /
1.109-1.659x / 1.004-1.042x.
- **vs best non-Cake, ckpt and long forward:** `ckpt 2×fwd+bwd (CUDA
graph)` is B200 0.817-1.181x / 1.024-1.276x / 1.058-1.074x, GB300
1.002-1.433x / 1.000-1.298x / 1.044-1.072x, R200 (212-SM board)
0.689-0.988x / 0.986-1.370x / 0.950-0.962x. From T = 8192 the forward is
0.984-1.102x on B200 and 1.047-1.089x on GB300.
- **vs #8164, long inputs (read with det drift):** from T = 8192 the
forward is 1.096-1.130x on B200 and 1.089-1.131x on GB300 (det drift
0.994-1.005). `ckpt 2×fwd+bwd (CUDA graph)` is 1.042-1.093x on B200,
1.049-1.067x on GB300 and 1.015-1.056x on R200 (212-SM board) (det drift
0.996-1.006).
- **vs #8164, backward (read with det drift):** on R200 (212-SM board),
`bwd` is 1.036-1.149x and `bwd (CUDA graph)` 1.035-1.138x at every T.
From T = 8192 the same values are 1.036-1.109x and 1.038-1.107x (det
drift 0.998-1.002). On GB300 at T <= 4097, `bwd (CUDA graph)` is
1.008-1.389x (det drift 1.002-1.045) and `bwd` 1.007-1.410x. On B200 at
T 1031-2048, `bwd (CUDA graph)` is 1.016-1.065x (det drift 1.000-1.004).

### Slower or at parity

- **vs best non-Cake, `fwd`:** slower at T <= 4097 on all three GPUs,
except GB300 at T = 2048 (1.006x). It is also slower at every T on R200
(212-SM board). B200 0.712-0.855x / 0.913-0.956x, GB300 0.888-0.974x /
0.940-1.006x, R200 (212-SM board) 0.767-0.824x / 0.931-0.944x /
0.907-0.922x. B200 is also slower at T = 8192 (0.984x).
- **vs best non-Cake, `ckpt 2×fwd+bwd (CUDA graph)`:** B200 is slower at
T = 1 and 7 (0.817x, 0.953x). R200 (212-SM board) is slower at T <= 129
(0.689-0.988x), at T = 4097 (0.986x) and at T >= 8192 (0.950-0.962x,
FLA).
- **vs deterministic Cake:** R200 (212-SM board) ckpt at T = 7 is 0.969x
(n.s.). R200 (212-SM board) `fwd` at T = 16384 and 32737 is 0.998x and
not marked n.s. (round spread <= 0.1 %). Both modes run the same forward
kernel there.
- **vs #8164, B200 long-input backward:** at T >= 8192, `bwd` is
0.990-0.997x and `bwd (CUDA graph)` 0.992-1.012x (det drift
0.995-1.003). This matches #8164 within about 1 %. The eager path may be
up to about 0.5-1 % slower.
- **vs #8164, other parity rows:** the GB300 backward at T >= 8192 is
0.997-1.003x (equal). At T = 4097, B200 is 0.998x in `bwd (CUDA graph)`
and 0.995x in ckpt (equal within drift).
- **vs #8164, B200 small T:** `bwd (CUDA graph)` at T <= 129 reads
1.078-1.121x. However, the deterministic baseline itself moved
1.046-1.107 between the two processes. So the B200 small-T gain over
#8164 is not established.

### Baselines and timing

- **Deterministic Cake:** `flashinfer.cake_rmsnorm_silu_gate_det_train`
(forward; backward kernel plus its fixed-order weight-gradient reduction
kernel). It is unchanged on this PR's base and measured in the same
process as the new path.
- **Best non-Cake:** the table names the fastest of four
implementations, chosen per row and operation. They are `fla` 0.6.0
`fla.modules.fused_norm_gate.rms_norm_gated` (Triton kernel of its
`FusedRMSNormGated` module, swish gate), mamba_ssm v2.3.2
`mamba_ssm.ops.triton.layernorm_gated.rmsnorm_fn(..., z=z,
norm_before_gate=True)` (Triton), and `torch.compile` of the FP32
formula in inductor default mode ("torch.compile") and
`max-autotune-no-cudagraphs` mode ("torch.compile max-autotune").
Versions are PyTorch 2.14.1 and Triton 3.8.0.
- **Why strongest applicable:** these are the fused gated-RMSNorm
training kernels of fla and Mamba-2, plus compiler fusion of the same
formula. All four meet the same dw accuracy budget on these inputs. The
set is the same as in #8097 and #8164.
- **Previous Cake version:** the non-deterministic path as merged in
#8164 (head c8d08a01), measured on the same GPU in a separate process
just before or after this PR's run.
- **Workload:** x, z, dy of shape [T, 48, 128] BF16, BF16 w, eps 1e-6,
BF16 weight gradient. T = 1, 7, 129, 1031, 2048, 4097, 8192, 16384,
30000, 30193, 32388, 32737, 33000.
- **`fwd`:** one forward call. Cake writes a preallocated output; the
others run the autograd-recording forward.
- **`bwd`:** one complete eager backward, including the weight-gradient
reduction and the final cast. Its value is the CUPTI span of the call's
kernels, so a multi-kernel backward includes host launch gaps. Cake uses
preallocated gradients and workspace; the others run `autograd.grad` of
one recorded forward.
- **`bwd (CUDA graph)`:** the same backward call replayed from a CUDA
graph, timed as the GPU span of the replay (no host gaps).
- **`ckpt 2×fwd+bwd (CUDA graph)`:**
`torch.utils.checkpoint(use_reentrant=False)` forward then backward,
captured and replayed from a CUDA graph, timed as the GPU span of the
replay.
- **Eager checkpointed step:** not shown. Host autograd time dominates
its span, and its differences are not significant.
- **Timing:** CUPTI through FlashInfer's timer in `flashinfer.testing`,
cold L2, 10 rounds. Each cell is the median of the per-round medians.
- **Round spread:** max / min − 1 of the per-round medians (det / new).
A vs det ratio inside the larger of the two spreads is marked "(n.s.)".
- **Ratios:** vs det = det latency / new latency; vs non-Cake = best
non-Cake latency / new latency; vs #8164 = #8164 non-det latency / new
latency.
- **#8164 column and det drift:** the #8164 values come from a separate
process. det drift = deterministic latency in the #8164 run /
deterministic latency in this run, so it shows how much the two
processes differ on an unchanged kernel. Below the long-forward
threshold both versions run the same forward kernel, so their `fwd` "vs
#8164" ratio equals the det drift.
- **n/a in `bwd (CUDA graph)`:** capturing the non-Cake autograd
backward alone fails, because its autograd node holds a stale reference
to the default stream from warm-up. The non-Cake backward is compared in
eager `bwd` and inside the captured checkpointed step.

**NVIDIA B200 (sm_100a, 148 SMs), driver 580.82.07, CUDA 13.4 toolkit,
PyTorch 2.14.1+cu130**

| T | op | det Cake (µs) | best non-Cake (µs) | #8164 non-det Cake (µs)
| new non-det Cake (µs) | vs det | vs non-Cake | vs #8164 | round spread
det / new | det drift (#8164 run / this run) |
|---:|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 1 | fwd | 2.5 | 1.9 (torch.compile max-autotune) | 2.7 | 2.5 | 1.000x
(n.s.) | 0.744x | 1.064x | 0.0 % / 0.0 % | 1.064 |
| 1 | bwd | 16.0 | 29.3 (torch.compile max-autotune) | 4.3 | 3.9 |
4.073x | 7.451x | 1.101x | 25.3 % / 0.8 % | 0.982 |
| 1 | bwd (CUDA graph) | 4.9 | n/a | 4.6 | 4.1 | 1.183x | n/a | 1.121x |
13.7 % / 0.8 % | 1.046 |
| 1 | ckpt 2×fwd+bwd (CUDA graph) | 9.7 | 7.5 (torch.compile) | 9.6 |
9.2 | 1.056x (n.s.) | 0.817x | 1.051x | 21.8 % / 16.2 % | 1.005 |
| 7 | fwd | 2.9 | 2.1 (torch.compile) | 3.0 | 2.9 | 1.000x (n.s.) |
0.712x | 1.022x | 1.1 % / 1.1 % | 1.022 |
| 7 | bwd | 20.4 | 63.3 (torch.compile) | 4.6 | 4.3 | 4.713x | 14.644x |
1.074x | 22.3 % / 0.7 % | 0.839 |
| 7 | bwd (CUDA graph) | 5.1 | n/a | 4.8 | 4.4 | 1.145x | n/a | 1.083x |
13.0 % / 3.8 % | 1.107 |
| 7 | ckpt 2×fwd+bwd (CUDA graph) | 9.4 | 8.8 (torch.compile
max-autotune) | 10.2 | 9.2 | 1.021x (n.s.) | 0.953x | 1.108x | 16.3 % /
14.5 % | 1.097 |
| 129 | fwd | 3.7 | 3.2 (torch.compile) | 4.0 | 3.7 | 1.000x (n.s.) |
0.855x | 1.060x | 0.0 % / 0.8 % | 1.060 |
| 129 | bwd | 25.7 | 84.1 (torch.compile) | 6.8 | 6.3 | 4.100x | 13.414x
| 1.082x | 18.4 % / 0.5 % | 0.762 |
| 129 | bwd (CUDA graph) | 7.7 | n/a | 7.0 | 6.5 | 1.181x | n/a | 1.078x
| 2.5 % / 0.5 % | 1.046 |
| 129 | ckpt 2×fwd+bwd (CUDA graph) | 12.9 | 14.2 (torch.compile
max-autotune) | 13.3 | 12.0 | 1.072x | 1.181x | 1.109x | 2.0 % / 2.7 % |
1.092 |
| 1031 | fwd | 10.7 | 9.8 (torch.compile max-autotune) | 10.7 | 10.7 |
0.997x (n.s.) | 0.913x | 1.000x | 1.5 % / 1.8 % | 0.997 |
| 1031 | bwd | 33.0 | 138.0 (mamba_ssm) | 20.2 | 19.1 | 1.729x | 7.235x
| 1.057x | 13.0 % / 0.3 % | 0.731 |
| 1031 | bwd (CUDA graph) | 22.8 | n/a | 20.4 | 19.2 | 1.188x | n/a |
1.065x | 0.8 % / 0.3 % | 1.004 |
| 1031 | ckpt 2×fwd+bwd (CUDA graph) | 38.9 | 45.8 (FLA) | 37.5 | 35.9 |
1.085x | 1.276x | 1.045x | 1.5 % / 2.6 % | 1.000 |
| 2048 | fwd | 17.7 | 16.9 (torch.compile max-autotune) | 17.9 | 17.7 |
0.998x (n.s.) | 0.956x | 1.013x | 0.7 % / 0.7 % | 1.020 |
| 2048 | bwd | 38.3 | 159.3 (mamba_ssm) | 30.9 | 30.4 | 1.257x (n.s.) |
5.233x | 1.015x | 119.5 % / 0.5 % | 0.928 |
| 2048 | bwd (CUDA graph) | 35.4 | n/a | 31.0 | 30.5 | 1.159x | n/a |
1.016x | 0.9 % / 0.2 % | 1.000 |
| 2048 | ckpt 2×fwd+bwd (CUDA graph) | 65.4 | 65.9 (FLA) | 63.7 | 63.2 |
1.035x | 1.043x | 1.008x | 1.0 % / 1.6 % | 1.004 |
| 4097 | fwd | 32.4 | 29.8 (torch.compile) | 32.5 | 32.5 | 0.997x (n.s.)
| 0.915x | 0.999x | 0.5 % / 0.5 % | 1.001 |
| 4097 | bwd | 59.8 | 183.2 (FLA) | 54.0 | 54.0 | 1.109x (n.s.) | 3.396x
| 1.000x | 36.3 % / 0.1 % | 0.996 |
| 4097 | bwd (CUDA graph) | 59.9 | n/a | 53.9 | 54.0 | 1.110x | n/a |
0.998x | 0.3 % / 0.2 % | 0.992 |
| 4097 | ckpt 2×fwd+bwd (CUDA graph) | 118.9 | 118.6 (FLA) | 115.2 |
115.8 | 1.027x | 1.024x | 0.995x | 0.4 % / 0.4 % | 0.995 |
| 8192 | fwd | 59.5 | 53.3 (torch.compile max-autotune) | 59.4 | 54.2 |
1.097x | 0.984x | 1.096x | 0.3 % / 0.1 % | 1.002 |
| 8192 | bwd | 105.8 | 203.4 (FLA) | 99.2 | 99.7 | 1.061x | 2.040x |
0.995x | 0.2 % / 0.1 % | 1.003 |
| 8192 | bwd (CUDA graph) | 105.9 | n/a | 98.8 | 99.6 | 1.063x | n/a |
0.992x | 0.4 % / 0.1 % | 0.998 |
| 8192 | ckpt 2×fwd+bwd (CUDA graph) | 218.5 | 217.2 (FLA) | 213.3 |
204.7 | 1.068x | 1.061x | 1.042x | 0.3 % / 0.2 % | 0.997 |
| 16384 | fwd | 113.2 | 101.7 (torch.compile max-autotune) | 113.7 |
101.7 | 1.114x | 1.000x | 1.119x | 0.1 % / 0.1 % | 1.005 |
| 16384 | bwd | 196.2 | 237.6 (FLA) | 185.8 | 186.8 | 1.050x | 1.272x |
0.995x | 0.0 % / 0.1 % | 1.000 |
| 16384 | bwd (CUDA graph) | 196.2 | n/a | 185.1 | 186.5 | 1.052x | n/a
| 0.993x | 0.1 % / 0.1 % | 0.997 |
| 16384 | ckpt 2×fwd+bwd (CUDA graph) | 415.6 | 411.7 (FLA) | 406.7 |
384.8 | 1.080x | 1.070x | 1.057x | 0.1 % / 0.1 % | 0.999 |
| 30000 | fwd | 202.2 | 188.9 (torch.compile max-autotune) | 202.0 |
178.8 | 1.131x | 1.056x | 1.130x | 0.1 % / 0.1 % | 0.998 |
| 30000 | bwd | 347.7 | 350.1 (FLA) | 329.1 | 330.0 | 1.054x | 1.061x |
0.997x | 0.1 % / 0.3 % | 0.998 |
| 30000 | bwd (CUDA graph) | 347.9 | n/a | 330.0 | 329.6 | 1.056x | n/a
| 1.001x | 0.1 % / 1.5 % | 0.996 |
| 30000 | ckpt 2×fwd+bwd (CUDA graph) | 744.3 | 731.3 (FLA) | 728.4 |
683.1 | 1.090x | 1.070x | 1.066x | 0.3 % / 2.3 % | 1.005 |
| 30193 | fwd | 204.2 | 198.8 (FLA) | 203.2 | 180.4 | 1.132x | 1.102x |
1.126x | 0.1 % / 0.2 % | 0.995 |
| 30193 | bwd | 349.4 | 353.2 (FLA) | 330.4 | 331.9 | 1.053x | 1.064x |
0.995x | 0.1 % / 0.2 % | 0.999 |
| 30193 | bwd (CUDA graph) | 349.6 | n/a | 335.4 | 331.6 | 1.054x | n/a
| 1.012x | 0.1 % / 0.1 % | 0.998 |
| 30193 | ckpt 2×fwd+bwd (CUDA graph) | 750.3 | 737.8 (FLA) | 750.9 |
687.1 | 1.092x | 1.074x | 1.093x | 0.6 % / 0.9 % | 0.999 |
| 32388 | fwd | 218.1 | 203.1 (torch.compile max-autotune) | 217.7 |
192.9 | 1.131x | 1.052x | 1.128x | 0.1 % / 0.2 % | 0.999 |
| 32388 | bwd | 373.3 | 379.4 (FLA) | 354.0 | 356.5 | 1.047x | 1.064x |
0.993x | 0.1 % / 0.3 % | 0.998 |
| 32388 | bwd (CUDA graph) | 373.7 | n/a | 354.2 | 356.2 | 1.049x | n/a
| 0.994x | 0.2 % / 1.2 % | 0.997 |
| 32388 | ckpt 2×fwd+bwd (CUDA graph) | 800.2 | 783.1 (torch.compile
max-autotune) | 802.4 | 740.0 | 1.081x | 1.058x | 1.084x | 0.7 % / 2.4 %
| 1.000 |
| 32737 | fwd | 220.5 | 214.2 (torch.compile max-autotune) | 219.7 |
195.5 | 1.128x | 1.096x | 1.124x | 0.2 % / 0.8 % | 0.997 |
| 32737 | bwd | 378.6 | 380.5 (FLA) | 357.2 | 360.5 | 1.050x | 1.056x |
0.991x | 0.1 % / 0.3 % | 0.997 |
| 32737 | bwd (CUDA graph) | 378.8 | n/a | 363.2 | 360.4 | 1.051x | n/a
| 1.008x | 0.2 % / 0.2 % | 0.995 |
| 32737 | ckpt 2×fwd+bwd (CUDA graph) | 811.9 | 795.6 (FLA) | 806.0 |
744.1 | 1.091x | 1.069x | 1.083x | 0.1 % / 1.1 % | 0.997 |
| 33000 | fwd | 222.7 | 208.0 (torch.compile max-autotune) | 221.7 |
197.3 | 1.129x | 1.054x | 1.123x | 0.2 % / 0.3 % | 0.994 |
| 33000 | bwd | 380.6 | 385.4 (FLA) | 359.9 | 363.4 | 1.047x | 1.060x |
0.990x | 0.1 % / 0.9 % | 0.997 |
| 33000 | bwd (CUDA graph) | 380.9 | n/a | 364.4 | 363.2 | 1.049x | n/a
| 1.003x | 0.1 % / 0.5 % | 0.995 |
| 33000 | ckpt 2×fwd+bwd (CUDA graph) | 816.3 | 792.5 (torch.compile
max-autotune) | 815.9 | 749.2 | 1.090x | 1.058x | 1.089x | 0.3 % / 1.2 %
| 0.998 |

**NVIDIA GB300 (sm_103a, 152 SMs), driver 580.159.03, CUDA 13.4 toolkit,
PyTorch 2.14.1+cu130**

| T | op | det Cake (µs) | best non-Cake (µs) | #8164 non-det Cake (µs)
| new non-det Cake (µs) | vs det | vs non-Cake | vs #8164 | round spread
det / new | det drift (#8164 run / this run) |
|---:|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 1 | fwd | 2.4 | 2.3 (mamba_ssm) | 2.6 | 2.4 | 0.987x (n.s.) | 0.934x |
1.059x | 6.7 % / 8.0 % | 1.067 |
| 1 | bwd | 37.6 | 20.4 (torch.compile max-autotune) | 5.1 | 4.0 |
9.472x | 5.153x | 1.274x | 17.4 % / 0.0 % | 0.945 |
| 1 | bwd (CUDA graph) | 5.4 | n/a | 5.3 | 4.1 | 1.314x | n/a | 1.287x |
9.8 % / 1.6 % | 1.024 |
| 1 | ckpt 2×fwd+bwd (CUDA graph) | 9.8 | 8.7 (torch.compile
max-autotune) | 10.1 | 8.7 | 1.125x (n.s.) | 1.002x | 1.165x | 16.8 % /
17.8 % | 1.034 |
| 7 | fwd | 2.8 | 2.5 (mamba_ssm) | 2.8 | 2.8 | 1.000x (n.s.) | 0.888x |
1.000x | 0.0 % / 0.0 % | 1.000 |
| 7 | bwd | 45.3 | 44.3 (torch.compile max-autotune) | 5.3 | 4.3 |
10.567x | 10.330x | 1.239x | 10.8 % / 0.0 % | 0.835 |
| 7 | bwd (CUDA graph) | 5.7 | n/a | 5.4 | 4.2 | 1.354x | n/a | 1.285x |
11.0 % / 2.7 % | 1.037 |
| 7 | ckpt 2×fwd+bwd (CUDA graph) | 9.8 | 9.5 (torch.compile
max-autotune) | 10.3 | 8.9 | 1.103x (n.s.) | 1.076x | 1.164x | 15.1 % /
13.3 % | 1.080 |
| 129 | fwd | 3.7 | 3.6 (FLA) | 3.8 | 3.7 | 1.000x (n.s.) | 0.974x |
1.026x | 0.0 % / 0.0 % | 1.026 |
| 129 | bwd | 52.4 | 60.3 (torch.compile max-autotune) | 8.8 | 6.2 |
8.390x | 9.659x | 1.410x | 20.1 % / 0.0 % | 0.772 |
| 129 | bwd (CUDA graph) | 8.3 | n/a | 9.0 | 6.5 | 1.271x | n/a | 1.389x
| 2.4 % / 0.0 % | 1.045 |
| 129 | ckpt 2×fwd+bwd (CUDA graph) | 13.1 | 16.7 (FLA) | 15.2 | 11.6 |
1.128x | 1.433x | 1.303x | 2.2 % / 2.5 % | 1.077 |
| 1031 | fwd | 10.0 | 9.9 (FLA) | 10.0 | 10.0 | 1.000x (n.s.) | 0.998x |
1.010x | 1.6 % / 1.6 % | 1.000 |
| 1031 | bwd | 58.6 | 116.3 (mamba_ssm) | 20.1 | 17.8 | 3.286x | 6.523x
| 1.126x | 15.5 % / 0.2 % | 0.785 |
| 1031 | bwd (CUDA graph) | 22.9 | n/a | 20.3 | 18.0 | 1.276x | n/a |
1.132x | 1.4 % / 0.4 % | 1.012 |
| 1031 | ckpt 2×fwd+bwd (CUDA graph) | 37.1 | 43.2 (FLA) | 37.6 | 33.3 |
1.116x | 1.298x | 1.130x | 1.4 % / 1.1 % | 1.029 |
| 2048 | fwd | 16.9 | 16.7 (torch.compile max-autotune) | 17.0 | 16.6 |
1.014x | 1.006x | 1.023x | 1.3 % / 1.2 % | 1.018 |
| 2048 | bwd | 62.8 | 134.4 (FLA) | 31.1 | 28.2 | 2.226x | 4.765x |
1.102x | 12.2 % / 0.1 % | 0.753 |
| 2048 | bwd (CUDA graph) | 34.6 | n/a | 31.2 | 28.3 | 1.220x | n/a |
1.102x | 1.0 % / 0.2 % | 1.008 |
| 2048 | ckpt 2×fwd+bwd (CUDA graph) | 62.1 | 62.0 (FLA) | 61.9 | 58.6 |
1.060x | 1.059x | 1.057x | 1.1 % / 1.1 % | 1.004 |
| 4097 | fwd | 30.4 | 28.6 (torch.compile max-autotune) | 30.5 | 30.5 |
0.999x (n.s.) | 0.940x | 1.000x | 0.5 % / 0.5 % | 1.004 |
| 4097 | bwd | 67.5 | 152.3 (FLA) | 53.5 | 53.2 | 1.270x | 2.865x |
1.007x | 18.3 % / 0.1 % | 0.852 |
| 4097 | bwd (CUDA graph) | 57.3 | n/a | 53.6 | 53.2 | 1.076x | n/a |
1.008x | 0.7 % / 0.1 % | 1.002 |
| 4097 | ckpt 2×fwd+bwd (CUDA graph) | 112.9 | 110.7 (FLA) | 111.4 |
110.7 | 1.020x | 1.000x | 1.007x | 0.4 % / 0.5 % | 1.002 |
| 8192 | fwd | 56.1 | 54.8 (FLA) | 56.4 | 51.7 | 1.084x | 1.059x |
1.089x | 0.3 % / 0.1 % | 1.004 |
| 8192 | bwd | 101.1 | 160.6 (FLA) | 94.6 | 94.7 | 1.068x | 1.696x |
0.999x | 0.2 % / 0.1 % | 1.000 |
| 8192 | bwd (CUDA graph) | 100.9 | n/a | 94.5 | 94.7 | 1.065x | n/a |
0.998x | 0.3 % / 0.1 % | 0.998 |
| 8192 | ckpt 2×fwd+bwd (CUDA graph) | 207.1 | 202.2 (FLA) | 202.7 |
193.3 | 1.071x | 1.046x | 1.049x | 0.1 % / 0.2 % | 1.000 |
| 16384 | fwd | 105.8 | 103.7 (FLA) | 106.3 | 95.6 | 1.107x | 1.086x |
1.113x | 0.2 % / 0.1 % | 1.005 |
| 16384 | bwd | 184.4 | 183.2 (FLA) | 175.2 | 174.8 | 1.055x | 1.048x |
1.003x | 0.2 % / 0.1 % | 1.002 |
| 16384 | bwd (CUDA graph) | 184.2 | n/a | 174.9 | 174.8 | 1.054x | n/a
| 1.001x | 0.1 % / 0.0 % | 1.002 |
| 16384 | ckpt 2×fwd+bwd (CUDA graph) | 389.2 | 382.9 (FLA) | 383.8 |
361.0 | 1.078x | 1.060x | 1.063x | 0.1 % / 0.2 % | 1.005 |
| 30000 | fwd | 191.0 | 184.2 (FLA) | 191.0 | 169.2 | 1.129x | 1.089x |
1.129x | 0.1 % / 0.0 % | 0.999 |
| 30000 | bwd | 327.4 | 323.5 (FLA) | 305.4 | 306.2 | 1.069x | 1.056x |
0.997x | 0.1 % / 0.0 % | 1.000 |
| 30000 | bwd (CUDA graph) | 327.2 | n/a | 305.2 | 305.9 | 1.070x | n/a
| 0.998x | 0.1 % / 0.0 % | 0.999 |
| 30000 | ckpt 2×fwd+bwd (CUDA graph) | 703.2 | 684.3 (FLA) | 682.9 |
640.8 | 1.097x | 1.068x | 1.066x | 0.2 % / 0.1 % | 0.999 |
| 30193 | fwd | 191.0 | 178.1 (torch.compile max-autotune) | 191.2 |
170.1 | 1.123x | 1.047x | 1.124x | 0.2 % / 0.0 % | 1.002 |
| 30193 | bwd | 329.9 | 323.2 (torch.compile max-autotune) | 306.5 |
307.5 | 1.073x | 1.051x | 0.997x | 0.1 % / 0.0 % | 0.999 |
| 30193 | bwd (CUDA graph) | 329.7 | n/a | 306.2 | 307.1 | 1.074x | n/a
| 0.997x | 0.1 % / 0.0 % | 0.999 |
| 30193 | ckpt 2×fwd+bwd (CUDA graph) | 705.2 | 681.0 (torch.compile
max-autotune) | 684.2 | 643.6 | 1.096x | 1.058x | 1.063x | 0.2 % / 0.1 %
| 0.999 |
| 32388 | fwd | 205.8 | 191.8 (torch.compile max-autotune) | 205.7 |
182.2 | 1.129x | 1.053x | 1.129x | 0.1 % / 0.1 % | 1.000 |
| 32388 | bwd | 352.0 | 335.2 (torch.compile max-autotune) | 328.2 |
328.8 | 1.071x | 1.020x | 0.998x | 0.1 % / 0.0 % | 1.000 |
| 32388 | bwd (CUDA graph) | 351.9 | n/a | 328.0 | 328.4 | 1.071x | n/a
| 0.999x | 0.1 % / 0.0 % | 0.999 |
| 32388 | ckpt 2×fwd+bwd (CUDA graph) | 756.9 | 718.6 (torch.compile
max-autotune) | 734.5 | 688.1 | 1.100x | 1.044x | 1.067x | 0.0 % / 0.1 %
| 0.999 |
| 32737 | fwd | 207.8 | 193.2 (torch.compile max-autotune) | 207.2 |
183.2 | 1.134x | 1.055x | 1.131x | 0.1 % / 0.0 % | 0.996 |
| 32737 | bwd | 354.8 | 351.1 (FLA) | 331.5 | 332.6 | 1.067x | 1.056x |
0.997x | 0.1 % / 0.1 % | 1.000 |
| 32737 | bwd (CUDA graph) | 354.7 | n/a | 331.3 | 332.4 | 1.067x | n/a
| 0.997x | 0.1 % / 0.1 % | 1.000 |
| 32737 | ckpt 2×fwd+bwd (CUDA graph) | 764.3 | 744.3 (FLA) | 740.7 |
694.5 | 1.100x | 1.072x | 1.066x | 0.1 % / 0.1 % | 0.996 |
| 33000 | fwd | 209.6 | 195.0 (torch.compile max-autotune) | 209.4 |
185.9 | 1.128x | 1.049x | 1.127x | 0.1 % / 0.1 % | 0.999 |
| 33000 | bwd | 358.1 | 353.5 (FLA) | 334.0 | 334.7 | 1.070x | 1.056x |
0.998x | 0.1 % / 0.1 % | 1.001 |
| 33000 | bwd (CUDA graph) | 358.0 | n/a | 333.7 | 334.4 | 1.071x | n/a
| 0.998x | 0.1 % / 0.2 % | 1.001 |
| 33000 | ckpt 2×fwd+bwd (CUDA graph) | 770.6 | 750.4 (FLA) | 748.3 |
702.4 | 1.097x | 1.068x | 1.065x | 0.0 % / 0.1 % | 1.000 |

**NVIDIA R200 (sm_107a, 212-SM board), driver 620.62, CUDA 13.4 toolkit,
PyTorch 2.14.1+cu130**

| T | op | det Cake (µs) | best non-Cake (µs) | #8164 non-det Cake (µs)
| new non-det Cake (µs) | vs det | vs non-Cake | vs #8164 | round spread
det / new | det drift (#8164 run / this run) |
|---:|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 1 | fwd | 2.5 | 2.0 (torch.compile) | 2.6 | 2.5 | 1.000x (n.s.) |
0.767x | 1.006x | 1.3 % / 1.3 % | 1.006 |
| 1 | bwd | 12.0 | 10.0 (torch.compile max-autotune) | 5.9 | 5.6 |
2.146x | 1.791x | 1.060x | 8.6 % / 1.7 % | 0.988 |
| 1 | bwd (CUDA graph) | 5.8 | n/a | 5.9 | 5.4 | 1.074x (n.s.) | n/a |
1.092x | 13.1 % / 3.6 % | 1.003 |
| 1 | ckpt 2×fwd+bwd (CUDA graph) | 10.1 | 6.8 (torch.compile
max-autotune) | 10.5 | 9.9 | 1.015x (n.s.) | 0.689x | 1.061x | 16.0 % /
9.2 % | 1.008 |
| 7 | fwd | 2.7 | 2.2 (torch.compile) | 2.8 | 2.7 | 1.000x (n.s.) |
0.824x | 1.012x | 1.2 % / 1.2 % | 1.012 |
| 7 | bwd | 12.9 | 17.5 (torch.compile max-autotune) | 6.0 | 5.4 |
2.377x | 3.218x | 1.112x | 12.3 % / 0.6 % | 0.924 |
| 7 | bwd (CUDA graph) | 5.5 | n/a | 6.0 | 5.5 | 1.009x (n.s.) | n/a |
1.105x | 6.4 % / 3.0 % | 1.084 |
| 7 | ckpt 2×fwd+bwd (CUDA graph) | 9.6 | 8.7 (torch.compile
max-autotune) | 11.0 | 10.0 | 0.969x (n.s.) | 0.878x | 1.108x | 9.7 % /
11.9 % | 1.098 |
| 129 | fwd | 3.2 | 2.6 (torch.compile max-autotune) | 3.3 | 3.2 |
1.000x (n.s.) | 0.802x | 1.030x | 0.0 % / 0.0 % | 1.030 |
| 129 | bwd | 15.1 | 18.9 (torch.compile max-autotune) | 7.4 | 6.5 |
2.342x | 2.923x | 1.149x | 4.8 % / 1.0 % | 0.910 |
| 129 | bwd (CUDA graph) | 7.6 | n/a | 7.4 | 6.5 | 1.172x | n/a | 1.138x
| 2.1 % / 1.0 % | 1.013 |
| 129 | ckpt 2×fwd+bwd (CUDA graph) | 12.4 | 11.5 (torch.compile
max-autotune) | 12.4 | 11.7 | 1.062x | 0.988x | 1.063x | 1.8 % / 3.3 % |
1.004 |
| 1031 | fwd | 6.9 | 6.5 (torch.compile) | 7.0 | 6.9 | 1.000x (n.s.) |
0.944x | 1.019x | 1.9 % / 1.9 % | 1.014 |
| 1031 | bwd | 19.1 | 24.4 (FLA) | 16.1 | 14.7 | 1.298x | 1.659x |
1.091x | 4.6 % / 0.2 % | 1.000 |
| 1031 | bwd (CUDA graph) | 18.3 | n/a | 15.9 | 14.6 | 1.252x | n/a |
1.084x | 1.6 % / 0.7 % | 1.009 |
| 1031 | ckpt 2×fwd+bwd (CUDA graph) | 28.8 | 35.4 (FLA) | 27.2 | 25.8 |
1.114x | 1.370x | 1.051x | 0.8 % / 1.0 % | 1.003 |
| 2048 | fwd | 11.1 | 10.3 (FLA) | 11.3 | 11.1 | 1.006x (n.s.) | 0.931x
| 1.017x | 1.7 % / 1.4 % | 1.009 |
| 2048 | bwd | 25.3 | 26.3 (FLA) | 23.3 | 21.4 | 1.181x | 1.228x |
1.085x | 0.6 % / 0.4 % | 1.006 |
| 2048 | bwd (CUDA graph) | 24.9 | n/a | 23.0 | 21.4 | 1.162x | n/a |
1.077x | 1.3 % / 0.9 % | 1.007 |
| 2048 | ckpt 2×fwd+bwd (CUDA graph) | 44.1 | 43.5 (FLA) | 43.4 | 41.4 |
1.065x | 1.051x | 1.049x | 0.9 % / 1.2 % | 1.012 |
| 4097 | fwd | 19.0 | 17.8 (FLA) | 19.3 | 19.0 | 1.000x (n.s.) | 0.934x
| 1.015x | 0.5 % / 0.5 % | 1.013 |
| 4097 | bwd | 38.3 | 39.4 (FLA) | 36.8 | 35.5 | 1.079x | 1.109x |
1.036x | 0.4 % / 0.2 % | 1.002 |
| 4097 | bwd (CUDA graph) | 37.8 | n/a | 36.7 | 35.5 | 1.064x | n/a |
1.035x | 0.4 % / 0.5 % | 1.002 |
| 4097 | ckpt 2×fwd+bwd (CUDA graph) | 74.1 | 71.2 (FLA) | 74.0 | 72.2 |
1.026x | 0.986x | 1.025x | 0.4 % / 0.4 % | 1.008 |
| 8192 | fwd | 34.3 | 31.6 (FLA) | 34.5 | 34.3 | 1.001x (n.s.) | 0.922x
| 1.007x | 0.3 % / 0.3 % | 1.003 |
| 8192 | bwd | 64.7 | 63.0 (FLA) | 62.6 | 60.4 | 1.070x | 1.042x |
1.036x | 0.1 % / 0.1 % | 1.001 |
| 8192 | bwd (CUDA graph) | 64.1 | n/a | 62.6 | 60.3 | 1.064x | n/a |
1.038x | 0.3 % / 0.3 % | 1.002 |
| 8192 | ckpt 2×fwd+bwd (CUDA graph) | 130.7 | 122.5 (FLA) | 129.5 |
127.6 | 1.025x | 0.960x | 1.015x | 0.6 % / 0.6 % | 1.006 |
| 16384 | fwd | 64.8 | 59.2 (FLA) | 65.0 | 64.9 | 0.998x | 0.911x |
1.001x | 0.1 % / 0.0 % | 1.001 |
| 16384 | bwd | 113.6 | 112.4 (FLA) | 122.0 | 110.2 | 1.031x | 1.020x |
1.107x | 0.0 % / 0.1 % | 1.000 |
| 16384 | bwd (CUDA graph) | 113.2 | n/a | 122.0 | 110.2 | 1.027x | n/a
| 1.107x | 0.1 % / 0.1 % | 1.000 |
| 16384 | ckpt 2×fwd+bwd (CUDA graph) | 241.3 | 227.5 (FLA) | 252.0 |
238.5 | 1.012x | 0.954x | 1.056x | 0.1 % / 0.2 % | 1.001 |
| 30000 | fwd | 115.0 | 105.0 (FLA) | 114.8 | 114.9 | 1.001x | 0.914x |
0.999x | 0.0 % / 0.0 % | 0.998 |
| 30000 | bwd | 197.3 | 196.1 (FLA) | 200.5 | 190.7 | 1.035x | 1.028x |
1.052x | 0.0 % / 0.1 % | 0.999 |
| 30000 | bwd (CUDA graph) | 196.8 | n/a | 200.0 | 190.6 | 1.033x | n/a
| 1.049x | 0.0 % / 0.1 % | 0.999 |
| 30000 | ckpt 2×fwd+bwd (CUDA graph) | 425.7 | 402.0 (FLA) | 429.1 |
419.9 | 1.014x | 0.957x | 1.022x | 0.1 % / 0.1 % | 0.998 |
| 30193 | fwd | 116.1 | 105.5 (FLA) | 116.1 | 115.9 | 1.001x | 0.910x |
1.001x | 0.0 % / 0.0 % | 1.001 |
| 30193 | bwd | 198.1 | 194.6 (FLA) | 206.5 | 191.7 | 1.033x | 1.015x |
1.077x | 0.0 % / 0.1 % | 1.001 |
| 30193 | bwd (CUDA graph) | 197.7 | n/a | 206.3 | 191.6 | 1.031x | n/a
| 1.076x | 0.1 % / 0.1 % | 1.001 |
| 30193 | ckpt 2×fwd+bwd (CUDA graph) | 428.1 | 404.3 (FLA) | 437.9 |
422.5 | 1.013x | 0.957x | 1.036x | 0.1 % / 0.1 % | 1.000 |
| 32388 | fwd | 124.3 | 112.7 (FLA) | 124.3 | 123.9 | 1.003x | 0.909x |
1.003x | 0.0 % / 0.0 % | 1.000 |
| 32388 | bwd | 211.8 | 207.9 (FLA) | 222.7 | 204.5 | 1.036x | 1.016x |
1.089x | 0.0 % / 0.1 % | 1.000 |
| 32388 | bwd (CUDA graph) | 211.3 | n/a | 222.6 | 204.4 | 1.034x | n/a
| 1.089x | 0.2 % / 0.1 % | 1.000 |
| 32388 | ckpt 2×fwd+bwd (CUDA graph) | 457.5 | 431.9 (FLA) | 474.3 |
450.8 | 1.015x | 0.958x | 1.052x | 0.1 % / 0.1 % | 1.001 |
| 32737 | fwd | 125.2 | 114.3 (FLA) | 125.7 | 125.4 | 0.998x | 0.911x |
1.002x | 0.0 % / 0.0 % | 1.003 |
| 32737 | bwd | 213.5 | 210.6 (FLA) | 227.0 | 205.6 | 1.038x | 1.024x |
1.104x | 0.0 % / 0.1 % | 0.999 |
| 32737 | bwd (CUDA graph) | 213.0 | n/a | 226.8 | 205.6 | 1.036x | n/a
| 1.103x | 0.0 % / 0.1 % | 0.998 |
| 32737 | ckpt 2×fwd+bwd (CUDA graph) | 462.1 | 437.7 (FLA) | 478.6 |
455.2 | 1.015x | 0.962x | 1.052x | 0.1 % / 0.2 % | 1.000 |
| 33000 | fwd | 126.2 | 114.5 (FLA) | 126.5 | 126.2 | 1.000x (n.s.) |
0.907x | 1.003x | 0.0 % / 0.0 % | 1.000 |
| 33000 | bwd | 214.9 | 208.9 (FLA) | 230.8 | 208.1 | 1.033x | 1.004x |
1.109x | 0.0 % / 0.0 % | 0.999 |
| 33000 | bwd (CUDA graph) | 214.4 | n/a | 230.3 | 208.0 | 1.031x | n/a
| 1.107x | 0.0 % / 0.1 % | 0.999 |
| 33000 | ckpt 2×fwd+bwd (CUDA graph) | 464.7 | 436.0 (FLA) | 483.7 |
458.8 | 1.013x | 0.950x | 1.054x | 0.1 % / 0.0 % | 1.002 |

Both modes cover sm_100a, sm_103a and sm_107a, and so do the other Cake
variants of this op (the default deterministic forward and backward, and
the FP32 weight-gradient output of both backward forms).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

- **New Features**
- Improved RMSNorm/SiLU-gate training performance for large inputs on
supported GPUs, while preserving forward output bits.
- Added support for additional GPU architectures and optimized gradient
calculations for long inputs.
- **Documentation**
- Clarified when optimized paths are used and documented their output
consistency and workspace requirements.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [be8cf03](https://github.com/flashinfer-ai/flashinfer/commit/be8cf032365621ec328658ff7127fffd974cadc5)

- **作者**: eigen
- **时间**: 2026-11-01T08:56:32Z
- **提交信息**: perf(cake_msa_icp_indexer): faster sm_107a decode via early index-K prefetch and fused chain at page size 128 (#8177)

The MiniMax-M3 index-context-parallel (ICP) sparse-attention indexer
(`flashinfer.msa_ops` `msa_icp_*`, experimental backend
`cake_msa_icp_indexer`) has two decode chains. The default chain is
score plane + select publish. The fused chain is list scorer + list
publisher (`msa_icp_decode_score_publish`). This PR changes only sm_107a
decode, in two ways:

1. At 64 and 32 local K rows per page (P128 TP2, P128 TP4, P256 TP4),
the score plane now prefetches the history index-K before the PDL wait.
2. At page size 128 (TP2 and TP4) with 8 or more requests,
`MSAIcpIndexerPlan.decode` without a caller pool now runs the fused
chain. It uses a pool that the plan allocates once, so it is CUDA Graph
safe.

Smaller batches and P256 keep the score plane. Speedup against the
previous version in FlashInfer main:

| World | Page | Cohort | Previous (ms) | New (ms) | Speedup |
|---|---|---|---:|---:|---:|
| TP4 | P128 | steady | 9.539 | 9.404 | 1.014x |
| TP4 | P128 | mixed | 9.992 | 9.831 | 1.016x |
| TP4 | P256 | steady | 9.303 | 9.202 | 1.011x |
| TP4 | P256 | mixed | 9.734 | 9.618 | 1.012x |
| TP2 | P128 | steady | 14.544 | 14.400 | 1.010x |
| TP2 | P128 | mixed | 15.043 | 14.843 | 1.013x |
| TP2 | P256 | steady | 14.339 | 14.351 | 1.00x (parity; this layout
uses the 128-row plane, unchanged) |
| TP2 | P256 | mixed | 15.035 | 15.024 | 1.00x (parity) |

*NVIDIA VR200 (sm_107a), 4 GPUs per node, CUDA 13.4. Workload:
MiniMax-M3 serving, 163840 input tokens, 8192 output tokens, 14
concurrent requests. Steady means 14 requests decode together. Mixed
means the same plus one request whose chunked prefill runs in mixed
batches. Metric: median GPU time of a decode step. n = 4 rounds (TP2
P256: 3), with previous and new run back to back on one node each round.
Speedup = previous / new.*

End-to-end output throughput (tok/s), same setup:

| World | Page | Steady: previous -> new (ratio) | Mixed: previous ->
new (ratio) |
|---|---|---|---|
| TP4 | P128 | 2036.9 -> 2055.0 (1.009) | 1937.6 -> 1955.2 (1.009) |
| TP4 | P256 | 2059.3 -> 2070.7 (1.006) | 1970.6 -> 1985.4 (1.008) |
| TP2 | P128 | 1493.6 -> 1502.7 (1.006) | 1476.7 -> 1489.4 (1.009) |
| TP2 | P256 | 1488.1 -> 1488.1 (1.000) | 1471.5 -> 1471.0 (1.000) |

The indexer ships the prefill path, the tagged and legacy receive rows,
and the P128/P256 x TP2/TP4 decode layouts on sm_100a (B200), sm_103a
(GB300) and sm_107a (VR200), and this PR changes only the sm_107a decode
path, leaving sm_100a and sm_103a code unchanged.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Decode now automatically uses a fused scoring-and-publishing path on
supported compute capability 10.7 configurations (P128, TP2 or TP4) for
batches of 8 or more requests. Smaller batches and other configurations
continue to use the score-plane path.
* The decode facade manages the pool needed for the fused path when that
configuration is available; callers can also provide their own pool.
* **Documentation**
* Updated guidance on fused-path selection, batch thresholds, and
supported page sizes.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [bcb5c54](https://github.com/flashinfer-ai/flashinfer/commit/bcb5c54e781178dc1dd510f6351c1233cbb162e5)

- **作者**: eigen
- **时间**: 2026-11-01T08:45:00Z
- **提交信息**: perf(cake_mhc_det_train): H=5120/7168 backward_finish completes under full-SM side loads on sm_100a (#8175)

`cake_mhc_det_train` is Cake's deterministic mHC (manifold-constrained
hyper-connection) training layer. It ships H = 4096, 5120 and 7168 on
sm_100a and sm_103a, and H = 4096 on sm_107a. This PR changes only
sm_100a at H = 5120 and H = 7168. In token bands up to T = 4096,
`backward_finish` uses a dynamic-claim form of its column-slab pass, and
it also uses new per-size final-reduction maps. Outputs are bitwise
identical to `main`. The baseline is the previous Cake version on
FlashInfer `main` (after #8146).

## Under a full-SM side hold

**full-SM hold** means one 128-thread CTA resident on every SM at the
maximum shared-memory carveout, on a second stream. That is 148 CTAs on
B200 and 152 on GB200. **blocked** means `main` does not finish
`backward_finish` at these T while the hold is resident. With the PR,
`backward_finish` finishes. **PR loaded/unloaded** is the PR time under
the hold divided by the PR unloaded time, shown per session (session 1 /
session 2).

**NVIDIA B200 (sm_100a, 148 SMs), CUDA 13.4**

| H | T | main | PR ms | PR loaded/unloaded |
|---|---|---|---|---|
| 5120 | 1024 | blocked | 0.0676 | 1.0154 / 1.0154 |
| 5120 | 1536 | blocked | 0.0799 | 1.0385 / 1.0392 |
| 5120 | 1920 | blocked | 0.0901 | 1.0340 / 1.0344 |
| 5120 | 2304 | blocked | 0.1024 | 1.0300 / 1.0305 |
| 5120 | 2688 | blocked | 0.1229 | 1.0386 / 1.0320 |
| 5120 | 3072 | blocked | 0.1328 | 1.0344 / 1.0377 |
| 5120 | 3584 | blocked | 0.1457 | 1.0220 / 1.0258 |
| 5120 | 4096 | blocked | 0.1650 | 1.0205 / 1.0231 |
| 7168 | 1536 | blocked | 0.1053 | 1.0290 / 1.0429 |
| 7168 | 1920 | blocked | 0.1188 | 1.0281 / 1.0270 |
| 7168 | 2048 | blocked | 0.1273 | 1.0254 / 1.0299 |
| 7168 | 2304 | blocked | 0.1372 | 1.0380 / 1.0355 |
| 7168 | 2688 | blocked | 0.1617 | 1.0308 / 1.0323 |
| 7168 | 2752 | blocked | 0.1618 | 1.0326 / 1.0328 |
| 7168 | 3072 | blocked | 0.1731 | 1.0293 / 1.0325 |
| 7168 | 3584 | blocked | 0.2110 | 1.0352 / 1.0347 |
| 7168 | 4096 | blocked | 0.2192 | 1.0337 / 1.0337 |

**NVIDIA GB200 (sm_100a, 152 SMs), CUDA 13.4**

| H | T | main | PR ms | PR loaded/unloaded |
|---|---|---|---|---|
| 5120 | 1024 | blocked | 0.0668 | 0.9232 / 0.9341 |
| 5120 | 1536 | blocked | 0.0758 | 1.0277 / 1.0230 |
| 5120 | 1920 | blocked | 0.0850 | 1.0302 / 1.0127 |
| 5120 | 2304 | blocked | 0.0971 | 1.0216 / 1.0162 |
| 5120 | 2688 | blocked | 0.1188 | 1.0266 / 1.0266 |
| 5120 | 3072 | blocked | 0.1290 | 1.0244 / 1.0259 |
| 5120 | 3584 | blocked | 0.1413 | 1.0222 / 1.0222 |
| 5120 | 4096 | blocked | 0.1569 | 1.0201 / 1.0244 |
| 7168 | 1536 | blocked | 0.0964 | 1.0129 / 1.0140 |
| 7168 | 1920 | blocked | 0.1147 | 1.0327 / 1.0341 |
| 7168 | 2048 | blocked | 0.1147 | 1.0255 / 1.0275 |
| 7168 | 2304 | blocked | 0.1249 | 1.0252 / 1.0267 |
| 7168 | 2688 | blocked | 0.1517 | 1.0233 / 1.0208 |
| 7168 | 2752 | blocked | 0.1516 | 1.0207 / 1.0207 |
| 7168 | 3072 | blocked | 0.1618 | 1.0226 / 1.0250 |
| 7168 | 3584 | blocked | 0.1783 | 1.0176 / 1.0198 |
| 7168 | 4096 | blocked | 0.2051 | 1.0222 / 1.0252 |

These token ranges keep the static form: T = 1–896, 1921–2112, 2689–2816
and 3585–3648 at H = 5120, and T = 1–640 and 961–1024 at H = 7168. As in
`main`, they still wait for a full-SM side kernel.

## Unloaded

**NVIDIA B200 (sm_100a, 148 SMs), CUDA 13.4**

| H | T | main ms | PR ms | Speedup |
|---|---|---|---|---|
| 5120 | 1024 | 0.0665 | 0.0666 | 0.999x |
| 5120 | 4096 | 0.1608 | 0.1615 | 0.996x |
| 5120 | 8192 | 0.2907 | 0.2906 | 1.000x |
| 5120 | 14928 | 0.4929 | 0.4930 | 1.000x |
| 5120 | 15288 | 0.5039 | 0.5041 | 1.000x |
| 5120 | 15566 | 0.5255 | 0.5253 | 1.000x |
| 5120 | 15590 | 0.5254 | 0.5252 | 1.000x |
| 5120 | 16114 | 0.5295 | 0.5295 | 1.000x |
| 5120 | 16132 | 0.5309 | 0.5303 | 1.001x |
| 5120 | 16164 | 0.5314 | 0.5318 | 0.999x |
| 5120 | 16263 | 0.5490 | 0.5489 | 1.000x |
| 5120 | 32768 | 1.0698 | 1.0693 | 1.001x |
| 5120 | 65536 | 2.1468 | 2.1483 | 0.999x |
| 7168 | 1024 | 0.0748 | same program as main | 1.00x (same program) |
| 7168 | 4096 | 0.2143 | 0.2120 | 1.011x |
| 7168 | 8192 | 0.3971 | 0.3961 | 1.003x |
| 7168 | 14928 | 0.7018 | 0.7014 | 1.001x |
| 7168 | 15288 | 0.7130 | 0.7123 | 1.001x |
| 7168 | 15566 | 0.7343 | 0.7337 | 1.001x |
| 7168 | 15590 | 0.7351 | 0.7345 | 1.001x |
| 7168 | 16114 | 0.7633 | 0.7629 | 1.001x |
| 7168 | 16132 | 0.7587 | 0.7581 | 1.001x |
| 7168 | 16164 | 0.7589 | 0.7590 | 1.000x |
| 7168 | 16263 | 0.7653 | 0.7650 | 1.000x |
| 7168 | 32768 | 1.4981 | 1.4971 | 1.001x |
| 7168 | 65536 | 3.0095 | 3.0157 | 0.998x |

**NVIDIA GB200 (sm_100a, 152 SMs), CUDA 13.4**

| H | T | main ms | PR ms | Speedup |
|---|---|---|---|---|
| 5120 | 1024 | 0.0722 | 0.0719 | 1.005x |
| 5120 | 4096 | 0.1545 | 0.1529 | 1.010x |
| 5120 | 8192 | 0.2755 | 0.2755 | 1.000x |
| 5120 | 14928 | 0.4696 | 0.4683 | 1.003x |
| 5120 | 15288 | 0.4783 | 0.4779 | 1.001x |
| 5120 | 15566 | 0.4886 | 0.4888 | 1.000x |
| 5120 | 15590 | 0.4898 | 0.4894 | 1.001x |
| 5120 | 16114 | 0.5285 | 0.5302 | 0.997x |
| 5120 | 16132 | 0.5201 | 0.5200 | 1.000x |
| 5120 | 16164 | 0.5110 | 0.5118 | 0.998x |
| 5120 | 16263 | 0.5105 | 0.5104 | 1.000x |
| 5120 | 32768 | 0.9837 | 0.9844 | 0.999x |
| 5120 | 65536 | 1.9384 | 1.9369 | 1.001x |
| 7168 | 1024 | 0.0709 | same program as main | 1.00x (same program) |
| 7168 | 4096 | 0.2012 | 0.2002 | 1.005x |
| 7168 | 8192 | 0.3635 | 0.3634 | 1.000x |
| 7168 | 14928 | 0.6390 | 0.6395 | 0.999x |
| 7168 | 15288 | 0.6459 | 0.6461 | 1.000x |
| 7168 | 15566 | 0.6588 | 0.6584 | 1.001x |
| 7168 | 15590 | 0.6595 | 0.6590 | 1.001x |
| 7168 | 16114 | 0.6850 | 0.6849 | 1.000x |
| 7168 | 16132 | 0.6869 | 0.6862 | 1.001x |
| 7168 | 16164 | 0.6865 | 0.6861 | 1.001x |
| 7168 | 16263 | 0.6885 | 0.6883 | 1.000x |
| 7168 | 32768 | 1.3503 | 1.3507 | 1.000x |
| 7168 | 65536 | 2.6755 | 2.6784 | 0.999x |

Unloaded, the speedup is 0.996x–1.011x on B200 and 0.997x–1.010x on
GB200, which is parity. These ranges exclude the same-program rows.

Times are `backward_finish` ms per call from CUDA events, with the
median taken per repeat. Under the hold, each session ran 8 repeats.
`main` was blocked in 8 of 8 and the PR completed in 8 of 8, in both
sessions on both boards. Each table shows the mean of two sessions per
board. On B200, the two sessions ran on different nodes. On GB200, both
sessions ran on one node, one after the other. Speedup = main ms / PR
ms, and above 1 means the PR is faster.

Cake also ships the mHC training head (stream-mean forward and its
backward) as `cake_mhc_det_train_head` and an experimental
non-deterministic backend at H = 4096, and this family ships on sm_100a,
sm_103a and sm_107a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* Added an additional backward-training execution path for hidden sizes
5120 and 7168 on supported hardware.
* Updated dispatch choices across token-count ranges and refined
reduction selection for these configurations.
* Adjusted data staging and memory access patterns in several training
kernels.

* **Bug Fixes**
* Corrected shared-memory data transfers in selected forward-training
paths to avoid redundant or misaligned chunks.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery Huang <averyh@nvidia.com>

### [3d971ef](https://github.com/flashinfer-ai/flashinfer/commit/3d971efa707be97b6eb63dc468b8767393e4c70c)

- **作者**: eigen
- **时间**: 2026-11-01T08:17:54Z
- **提交信息**: feat(cake_kda): opt-in lean local arena for the KCP backward (local_arena="lean", lean_passes=2) (#8174)

This PR adds an opt-in lean local arena for the KDA deterministic KCP
(context-parallel) backward. You turn it on with
`flashinfer.cake_kda_det_train_kcp.WorkspaceDetKcp(local_arena="lean",
lean_passes=...)`; `lean_passes` defaults to 2, and
`kda_det_workspace_bytes_kcp(..., local_arena="lean", lean_passes=...)`
reports the matching workspace size. `"replay"` stays the default, so
existing callers see no change. The lean arena uses a smaller workspace
in exchange for a slightly slower backward. The forward is unchanged,
and outputs and gradients are bitwise identical to replay (compared byte
for byte on every timed sample).

| GPU (arch, SMs, driver) | shape | workspace bytes replay | workspace
bytes lean | bytes saved | fwd ms replay | fwd ms lean | fwd lean/replay
| bwd ms replay | bwd ms lean | bwd lean/replay [95% CI] | n |
|---|---|---|---|---|---|---|---|---|---|---|---|
| B200 (sm_100a, 148 SMs, driver 580.82.07) | H4 | 4729623808 |
3925615956 | 17.0% | 2.4100 | 2.4067 | 0.9986 | 4.9050 | 4.9462 | 1.0084
[1.0077, 1.0088] | 42 |
| B200 (sm_100a, 148 SMs, driver 580.82.07) | H64 | 4926668800 |
4083621488 | 17.1% | 1.5063 | 1.5048 | 0.9990 | 4.5143 | 4.5366 | 1.0050
[1.0037, 1.0061] | 42 |
| GB300 (sm_103a, 152 SMs, driver 580.159.03) | H4 | 4729623808 |
3655471392 | 22.7% | 2.2279 | 2.2273 | 0.9998 | 4.4202 | 4.4673 | 1.0107
[1.0103, 1.0111] | 42 |
| GB300 (sm_103a, 152 SMs, driver 580.159.03) | H64 | 4926668800 |
3800407124 | 22.9% | 1.3687 | 1.3677 | 0.9993 | 3.9973 | 4.0122 | 1.0037
[1.0031, 1.0041] | 42 |
| R200 (sm_107a, 216 SMs, driver 615.71.10) | H4 | 4742206976 |
3668054560 | 22.7% | 1.3648 | 1.3660 | 1.0009 | 2.9142 | 2.9404 | 1.0090
[1.0084, 1.0095] | 70 |
| R200 (sm_107a, 216 SMs, driver 615.71.10) | H64 | 4926668800 |
3800407124 | 22.9% | 0.8531 | 0.8524 | 0.9992 | 2.6777 | 2.6889 | 1.0042
[1.0032, 1.0048] | 70 |

*Workload: one rank (W = 1) of the KCP layer, head dim 128, BF16
q/k/v/beta/dout, FP32 g and FP32 states. H4 uses H = 4 heads and 4
documents of 120001, 70707, 65537 and 5148 tokens (261393 tokens). H64
uses H = 64 heads and 12 documents of 3000, 1000, 2500, 64, 1, 4000,
2000, 1500, 700, 600, 500 and 515 tokens (16380 tokens). Workspace bytes
are the reserved KCP workspace of each arm; the lean column uses
`lean_passes = 2`. Timing uses CUDA events and reports the median of n
samples, with the two arms interleaved in one process. Ratio = lean /
replay, with a bootstrap 95% CI. Software: PyTorch 2.14.1+cu130 (CUDA
13.0 runtime).*

**Notes**
- Forward side-stream overrun: on the measured base (before #8159), with
one SM held by a resident side-stream kernel, the KCP forward slows down
by about 3-5% for every arm, including the unchanged default path. This
comes from the KCP forward output stage, not from this PR; #8159 (now on
main) schedules that stage with Cluster Launch Control and removes the
overrun.
- The multi-rank (W = 8) lean layouts were validated only on one node
with 8 GPUs over NVLink, not on a two-node GB200 topology.

Part of #7815



<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added an optional lean local workspace arena for eligible backward
plans, with configurable tail-pass counts.
* Workspace-size queries now accept options for selecting the local
arena and setting its pass count.
* Plans that aren’t supported by the lean arena continue to use the
existing replay-based layout; the default behavior is unchanged.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [1f7e30a](https://github.com/flashinfer-ai/flashinfer/commit/1f7e30ae2b380ad59e3b0da66c96ecd573ed950f)

- **作者**: eigen
- **时间**: 2026-11-01T08:09:25Z
- **提交信息**: feat(cake_gdn_kcp): with grad, add non-deterministic context-parallel Cake GDN chunked autograd backend (#8172)

This PR adds `flashinfer.experimental.cake_gdn_train_kcp`, the
non-deterministic context-parallel variant of Cake's Gated DeltaNet
(GDN) chunked training kernel with gradients. It is reached through
`flashinfer.cake_gdn_train_kcp` with `deterministic=False` and is the
only one of the kernel's four variants not yet on main. The tables give
speedup as baseline latency / new latency, so values above 1 mean the
new package is faster, against two baselines: the deterministic Cake KCP
package exactly as on main, and, per row, the strongest non-Cake
implementation that passes the same accuracy budget against an FP64
reference (chosen from FLA 0.6.0 context-parallel kernels, a
head-parallel all-to-all around the cuDNN frontend 1.32.1 FROST GDN
engine, and FlashQLA 0.1.3, which has no sm_107a build). The current
tables cover R200 (sm_107a, 212 SMs) at CP4 and CP2, where the new
package is at near parity with the deterministic one (1.00–1.02×) and
about 3.7–5.2× faster than the strongest non-Cake implementation on
forward+backward and checkpointed steps; B200 and GB300 rows will be
added when measured.

**R200 (sm_107a, 212 SMs), CUDA 13.0 — CP4**

Protocol: eager; CUDA events on every rank, the slowest rank's time
counts; 5 groups, in each the implementations run in palindromic order
(A … B, B … A) 2 times, each call 12 timed iterations after 10 warm-up,
256 MiB L2 flush before every iteration, no cool-down; latency = median
of the timed iterations; speedup = median of the 5 per-group ratios
[min, max]; unpaired = ratio of the medians (the non-Cake value ran with
another layout); (medians) = backward from the medians (forward+backward
− forward).

| GPU / architecture | workload (pack, (H, HV), S tokens, CP, layout) |
operation | deterministic Cake (ms) | strongest non-Cake (ms,
implementation) | new non-deterministic Cake (ms) | speedup vs
deterministic Cake | speedup vs non-Cake SOTA |
|---|---|---|---|---|---|---|---|
| R200 sm_107a (212 SMs) | P1, (16, 48), 241817, CP4, C | forward |
2.650 | 13.583 (FROST head-CP) | 2.619 | 1.012 [1.011, 1.012] | 5.185
[5.181, 5.189] |
| R200 sm_107a (212 SMs) | P1, (16, 48), 241817, CP4, C | backward (=
forward+backward − forward) | 4.674 | 18.322 (FROST head-CP) | 4.673 |
1.000 (medians) | 3.921 (medians) |
| R200 sm_107a (212 SMs) | P1, (16, 48), 241817, CP4, C |
forward+backward | 7.324 | 31.905 (FROST head-CP) | 7.293 | 1.004
[1.004, 1.005] | 4.375 [4.372, 4.376] |
| R200 sm_107a (212 SMs) | P1, (16, 48), 241817, CP4, C | checkpointed
2×forward+backward | 8.282 | 42.732 (FROST head-CP) | 8.209 | 1.009
[1.008, 1.009] | 5.205 [5.204, 5.208] |
| R200 sm_107a (212 SMs) | P1, (16, 48), 241817, CP4, C | checkpointed
with recompute handle (Cake only) | 8.107 | n/a | 8.033 | 1.009 [1.008,
1.010] | n/a |
| R200 sm_107a (212 SMs) | P1, (16, 48), 241817, CP4, D | forward |
3.249 | 13.583 (FROST head-CP) | 3.205 | 1.014 [1.013, 1.014] | 4.238
unpaired |
| R200 sm_107a (212 SMs) | P1, (16, 48), 241817, CP4, D | backward (=
forward+backward − forward) | 5.165 | 18.322 (FROST head-CP) | 5.167 |
1.000 (medians) | 3.546 (medians) |
| R200 sm_107a (212 SMs) | P1, (16, 48), 241817, CP4, D |
forward+backward | 8.414 | 31.905 (FROST head-CP) | 8.371 | 1.005
[1.005, 1.005] | 3.811 unpaired |
| R200 sm_107a (212 SMs) | P1, (16, 48), 241817, CP4, D | checkpointed
2×forward+backward | 9.890 | 42.732 (FROST head-CP) | 9.802 | 1.009
[1.008, 1.010] | 4.360 unpaired |
| R200 sm_107a (212 SMs) | P1, (16, 48), 241817, CP4, D | checkpointed
with recompute handle (Cake only) | 9.418 | n/a | 9.332 | 1.009 [1.009,
1.010] | n/a |
| R200 sm_107a (212 SMs) | P1, (16, 48), 241817, CP4, Z | forward |
2.790 | 13.583 (FROST head-CP) | 2.758 | 1.012 [1.010, 1.013] | 4.924
unpaired |
| R200 sm_107a (212 SMs) | P1, (16, 48), 241817, CP4, Z | backward (=
forward+backward − forward) | 4.789 | 18.322 (FROST head-CP) | 4.785 |
1.001 (medians) | 3.829 (medians) |
| R200 sm_107a (212 SMs) | P1, (16, 48), 241817, CP4, Z |
forward+backward | 7.579 | 31.905 (FROST head-CP) | 7.543 | 1.005
[1.003, 1.006] | 4.230 unpaired |
| R200 sm_107a (212 SMs) | P1, (16, 48), 241817, CP4, Z | checkpointed
2×forward+backward | 8.537 | 42.732 (FROST head-CP) | 8.467 | 1.008
[1.007, 1.010] | 5.047 unpaired |
| R200 sm_107a (212 SMs) | P1, (16, 48), 241817, CP4, Z | checkpointed
with recompute handle (Cake only) | 8.382 | n/a | 8.309 | 1.009 [1.009,
1.009] | n/a |
| R200 sm_107a (212 SMs) | P2, (16, 48), 261987, CP4, C | forward |
2.871 | 12.974 (FROST head-CP) | 2.828 | 1.015 [1.015, 1.017] | 4.587
[4.585, 4.591] |
| R200 sm_107a (212 SMs) | P2, (16, 48), 261987, CP4, C | backward (=
forward+backward − forward) | 5.081 | 18.870 (FROST head-CP) | 5.080 |
1.000 (medians) | 3.714 (medians) |
| R200 sm_107a (212 SMs) | P2, (16, 48), 261987, CP4, C |
forward+backward | 7.952 | 31.844 (FROST head-CP) | 7.908 | 1.006
[1.005, 1.006] | 4.026 [4.025, 4.029] |
| R200 sm_107a (212 SMs) | P2, (16, 48), 261987, CP4, C | checkpointed
2×forward+backward | 9.020 | 41.826 (FROST head-CP) | 8.939 | 1.009
[1.009, 1.010] | 4.679 [4.677, 4.682] |
| R200 sm_107a (212 SMs) | P2, (16, 48), 261987, CP4, C | checkpointed
with recompute handle (Cake only) | 8.806 | n/a | 8.716 | 1.010 [1.010,
1.011] | n/a |
| R200 sm_107a (212 SMs) | P2, (16, 48), 261987, CP4, D | forward |
2.995 | 12.974 (FROST head-CP) | 2.960 | 1.012 [1.011, 1.013] | 4.382
unpaired |
| R200 sm_107a (212 SMs) | P2, (16, 48), 261987, CP4, D | backward (=
forward+backward − forward) | 5.067 | 18.870 (FROST head-CP) | 5.068 |
1.000 (medians) | 3.723 (medians) |
| R200 sm_107a (212 SMs) | P2, (16, 48), 261987, CP4, D |
forward+backward | 8.062 | 31.844 (FROST head-CP) | 8.028 | 1.004
[1.004, 1.005] | 3.966 unpaired |
| R200 sm_107a (212 SMs) | P2, (16, 48), 261987, CP4, D | checkpointed
2×forward+backward | 9.281 | 41.826 (FROST head-CP) | 9.210 | 1.008
[1.008, 1.008] | 4.541 unpaired |
| R200 sm_107a (212 SMs) | P2, (16, 48), 261987, CP4, D | checkpointed
with recompute handle (Cake only) | 8.997 | n/a | 8.920 | 1.009 [1.008,
1.009] | n/a |
| R200 sm_107a (212 SMs) | P2, (16, 48), 261987, CP4, Z | forward |
2.960 | 12.974 (FROST head-CP) | 2.918 | 1.014 [1.014, 1.015] | 4.446
unpaired |
| R200 sm_107a (212 SMs) | P2, (16, 48), 261987, CP4, Z | backward (=
forward+backward − forward) | 5.135 | 18.870 (FROST head-CP) | 5.133 |
1.000 (medians) | 3.676 (medians) |
| R200 sm_107a (212 SMs) | P2, (16, 48), 261987, CP4, Z |
forward+backward | 8.095 | 31.844 (FROST head-CP) | 8.051 | 1.005
[1.005, 1.007] | 3.955 unpaired |
| R200 sm_107a (212 SMs) | P2, (16, 48), 261987, CP4, Z | checkpointed
2×forward+backward | 9.217 | 41.826 (FROST head-CP) | 9.130 | 1.010
[1.009, 1.010] | 4.581 unpaired |
| R200 sm_107a (212 SMs) | P2, (16, 48), 261987, CP4, Z | checkpointed
with recompute handle (Cake only) | 8.982 | n/a | 8.895 | 1.010 [1.009,
1.011] | n/a |
| R200 sm_107a (212 SMs) | P3, (16, 48), 259174, CP4, C | forward |
2.836 | 12.832 (FROST head-CP) | 2.806 | 1.010 [1.010, 1.011] | 4.573
[4.570, 4.575] |
| R200 sm_107a (212 SMs) | P3, (16, 48), 259174, CP4, C | backward (=
forward+backward − forward) | 4.784 | 18.686 (FROST head-CP) | 4.782 |
1.000 (medians) | 3.908 (medians) |
| R200 sm_107a (212 SMs) | P3, (16, 48), 259174, CP4, C |
forward+backward | 7.620 | 31.518 (FROST head-CP) | 7.588 | 1.004
[1.004, 1.005] | 4.154 [4.151, 4.157] |
| R200 sm_107a (212 SMs) | P3, (16, 48), 259174, CP4, C | checkpointed
2×forward+backward | 8.583 | 41.396 (FROST head-CP) | 8.520 | 1.007
[1.006, 1.008] | 4.858 [4.856, 4.862] |
| R200 sm_107a (212 SMs) | P3, (16, 48), 259174, CP4, C | checkpointed
with recompute handle (Cake only) | 8.444 | n/a | 8.376 | 1.008 [1.008,
1.008] | n/a |
| R200 sm_107a (212 SMs) | P3, (16, 48), 259174, CP4, D | forward |
2.818 | 12.832 (FROST head-CP) | 2.778 | 1.015 [1.014, 1.015] | 4.619
unpaired |
| R200 sm_107a (212 SMs) | P3, (16, 48), 259174, CP4, D | backward (=
forward+backward − forward) | 4.772 | 18.686 (FROST head-CP) | 4.771 |
1.000 (medians) | 3.917 (medians) |
| R200 sm_107a (212 SMs) | P3, (16, 48), 259174, CP4, D |
forward+backward | 7.591 | 31.518 (FROST head-CP) | 7.549 | 1.006
[1.004, 1.007] | 4.175 unpaired |
| R200 sm_107a (212 SMs) | P3, (16, 48), 259174, CP4, D | checkpointed
2×forward+backward | 8.709 | 41.396 (FROST head-CP) | 8.627 | 1.009
[1.009, 1.010] | 4.799 unpaired |
| R200 sm_107a (212 SMs) | P3, (16, 48), 259174, CP4, D | checkpointed
with recompute handle (Cake only) | 8.496 | n/a | 8.411 | 1.010 [1.010,
1.011] | n/a |
| R200 sm_107a (212 SMs) | P3, (16, 48), 259174, CP4, Z | forward |
2.876 | 12.832 (FROST head-CP) | 2.841 | 1.012 [1.011, 1.012] | 4.517
unpaired |
| R200 sm_107a (212 SMs) | P3, (16, 48), 259174, CP4, Z | backward (=
forward+backward − forward) | 4.817 | 18.686 (FROST head-CP) | 4.814 |
1.001 (medians) | 3.882 (medians) |
| R200 sm_107a (212 SMs) | P3, (16, 48), 259174, CP4, Z |
forward+backward | 7.693 | 31.518 (FROST head-CP) | 7.654 | 1.005
[1.005, 1.005] | 4.118 unpaired |
| R200 sm_107a (212 SMs) | P3, (16, 48), 259174, CP4, Z | checkpointed
2×forward+backward | 8.695 | 41.396 (FROST head-CP) | 8.623 | 1.008
[1.008, 1.009] | 4.801 unpaired |
| R200 sm_107a (212 SMs) | P3, (16, 48), 259174, CP4, Z | checkpointed
with recompute handle (Cake only) | 8.544 | n/a | 8.469 | 1.009 [1.008,
1.010] | n/a |
| R200 sm_107a (212 SMs) | P4, (16, 48), 254976, CP4, C | forward |
2.673 | 12.514 (FROST head-CP) | 2.643 | 1.011 [1.011, 1.012] | 4.734
[4.731, 4.739] |
| R200 sm_107a (212 SMs) | P4, (16, 48), 254976, CP4, C | backward (=
forward+backward − forward) | 4.583 | 18.127 (FROST head-CP) | 4.577 |
1.001 (medians) | 3.961 (medians) |
| R200 sm_107a (212 SMs) | P4, (16, 48), 254976, CP4, C |
forward+backward | 7.256 | 30.641 (FROST head-CP) | 7.220 | 1.005
[1.003, 1.006] | 4.244 [4.236, 4.247] |
| R200 sm_107a (212 SMs) | P4, (16, 48), 254976, CP4, C | checkpointed
2×forward+backward | 8.194 | 40.249 (FROST head-CP) | 8.129 | 1.008
[1.007, 1.009] | 4.953 [4.950, 4.954] |
| R200 sm_107a (212 SMs) | P4, (16, 48), 254976, CP4, C | checkpointed
with recompute handle (Cake only) | 8.080 | n/a | 8.010 | 1.009 [1.008,
1.009] | n/a |
| R200 sm_107a (212 SMs) | P4, (16, 48), 254976, CP4, D | forward |
3.074 | 12.514 (FROST head-CP) | 3.035 | 1.013 [1.012, 1.013] | 4.123
unpaired |
| R200 sm_107a (212 SMs) | P4, (16, 48), 254976, CP4, D | backward (=
forward+backward − forward) | 5.276 | 18.127 (FROST head-CP) | 5.276 |
1.000 (medians) | 3.436 (medians) |
| R200 sm_107a (212 SMs) | P4, (16, 48), 254976, CP4, D |
forward+backward | 8.350 | 30.641 (FROST head-CP) | 8.311 | 1.005
[1.004, 1.005] | 3.687 unpaired |
| R200 sm_107a (212 SMs) | P4, (16, 48), 254976, CP4, D | checkpointed
2×forward+backward | 9.559 | 40.249 (FROST head-CP) | 9.481 | 1.008
[1.008, 1.009] | 4.245 unpaired |
| R200 sm_107a (212 SMs) | P4, (16, 48), 254976, CP4, D | checkpointed
with recompute handle (Cake only) | 9.312 | n/a | 9.231 | 1.009 [1.009,
1.009] | n/a |
| R200 sm_107a (212 SMs) | P4, (16, 48), 254976, CP4, Z | forward |
2.705 | 12.514 (FROST head-CP) | 2.672 | 1.012 [1.012, 1.013] | 4.683
unpaired |
| R200 sm_107a (212 SMs) | P4, (16, 48), 254976, CP4, Z | backward (=
forward+backward − forward) | 4.612 | 18.127 (FROST head-CP) | 4.605 |
1.001 (medians) | 3.936 (medians) |
| R200 sm_107a (212 SMs) | P4, (16, 48), 254976, CP4, Z |
forward+backward | 7.317 | 30.641 (FROST head-CP) | 7.277 | 1.006
[1.004, 1.007] | 4.210 unpaired |
| R200 sm_107a (212 SMs) | P4, (16, 48), 254976, CP4, Z | checkpointed
2×forward+backward | 8.299 | 40.249 (FROST head-CP) | 8.231 | 1.008
[1.008, 1.009] | 4.890 unpaired |
| R200 sm_107a (212 SMs) | P4, (16, 48), 254976, CP4, Z | checkpointed
with recompute handle (Cake only) | 8.154 | n/a | 8.072 | 1.010 [1.010,
1.011] | n/a |
| R200 sm_107a (212 SMs) | P5, (16, 48), 249856, CP4, C | forward |
2.765 | 12.341 (FROST head-CP) | 2.727 | 1.014 [1.013, 1.015] | 4.525
[4.523, 4.527] |
| R200 sm_107a (212 SMs) | P5, (16, 48), 249856, CP4, C | backward (=
forward+backward − forward) | 4.756 | 17.882 (FROST head-CP) | 4.755 |
1.000 (medians) | 3.761 (medians) |
| R200 sm_107a (212 SMs) | P5, (16, 48), 249856, CP4, C |
forward+backward | 7.521 | 30.223 (FROST head-CP) | 7.482 | 1.005
[1.005, 1.005] | 4.039 [4.038, 4.040] |
| R200 sm_107a (212 SMs) | P5, (16, 48), 249856, CP4, C | checkpointed
2×forward+backward | 8.505 | 39.718 (FROST head-CP) | 8.430 | 1.009
[1.009, 1.009] | 4.711 [4.710, 4.713] |
| R200 sm_107a (212 SMs) | P5, (16, 48), 249856, CP4, C | checkpointed
with recompute handle (Cake only) | 8.305 | n/a | 8.237 | 1.008 [1.008,
1.009] | n/a |
| R200 sm_107a (212 SMs) | P5, (16, 48), 249856, CP4, D | forward |
2.892 | 12.341 (FROST head-CP) | 2.855 | 1.013 [1.012, 1.015] | 4.322
unpaired |
| R200 sm_107a (212 SMs) | P5, (16, 48), 249856, CP4, D | backward (=
forward+backward − forward) | 4.529 | 17.882 (FROST head-CP) | 4.526 |
1.001 (medians) | 3.951 (medians) |
| R200 sm_107a (212 SMs) | P5, (16, 48), 249856, CP4, D |
forward+backward | 7.421 | 30.223 (FROST head-CP) | 7.381 | 1.006
[1.004, 1.007] | 4.095 unpaired |
| R200 sm_107a (212 SMs) | P5, (16, 48), 249856, CP4, D | checkpointed
2×forward+backward | 8.806 | 39.718 (FROST head-CP) | 8.733 | 1.008
[1.008, 1.009] | 4.548 unpaired |
| R200 sm_107a (212 SMs) | P5, (16, 48), 249856, CP4, D | checkpointed
with recompute handle (Cake only) | 8.235 | n/a | 8.159 | 1.010 [1.009,
1.011] | n/a |
| R200 sm_107a (212 SMs) | P5, (16, 48), 249856, CP4, Z | forward |
2.793 | 12.341 (FROST head-CP) | 2.765 | 1.011 [1.009, 1.011] | 4.463
unpaired |
| R200 sm_107a (212 SMs) | P5, (16, 48), 249856, CP4, Z | backward (=
forward+backward − forward) | 4.783 | 17.882 (FROST head-CP) | 4.780 |
1.000 (medians) | 3.741 (medians) |
| R200 sm_107a (212 SMs) | P5, (16, 48), 249856, CP4, Z |
forward+backward | 7.576 | 30.223 (FROST head-CP) | 7.546 | 1.004
[1.004, 1.005] | 4.005 unpaired |
| R200 sm_107a (212 SMs) | P5, (16, 48), 249856, CP4, Z | checkpointed
2×forward+backward | 8.559 | 39.718 (FROST head-CP) | 8.499 | 1.007
[1.007, 1.008] | 4.674 unpaired |
| R200 sm_107a (212 SMs) | P5, (16, 48), 249856, CP4, Z | checkpointed
with recompute handle (Cake only) | 8.394 | n/a | 8.330 | 1.008 [1.007,
1.008] | n/a |

**R200 (sm_107a, 212 SMs), CUDA 13.0 — CP2**

Protocol: eager; CUDA events on every rank, the slowest rank's time
counts; 5 groups, in each the implementations run in palindromic order
(A … B, B … A) 2 times, each call 12 timed iterations after 10 warm-up,
256 MiB L2 flush before every iteration, no cool-down; latency = median
of the timed iterations; speedup = median of the 5 per-group ratios
[min, max]; unpaired = ratio of the medians (the non-Cake value ran with
another layout); (medians) = backward from the medians (forward+backward
− forward).

| GPU / architecture | workload (pack, (H, HV), S tokens, CP, layout) |
operation | deterministic Cake (ms) | strongest non-Cake (ms,
implementation) | new non-deterministic Cake (ms) | speedup vs
deterministic Cake | speedup vs non-Cake SOTA |
|---|---|---|---|---|---|---|---|
| R200 sm_107a (212 SMs) | P1, (16, 48), 241817, CP2, C | forward |
4.890 | 22.540 (FROST head-CP) | 4.835 | 1.011 [1.010, 1.012] | 4.662
[4.659, 4.663] |
| R200 sm_107a (212 SMs) | P1, (16, 48), 241817, CP2, C | backward (=
forward+backward − forward) | 8.600 | 32.695 (FROST head-CP) | 8.610 |
0.999 (medians) | 3.797 (medians) |
| R200 sm_107a (212 SMs) | P1, (16, 48), 241817, CP2, C |
forward+backward | 13.490 | 55.236 (FROST head-CP) | 13.446 | 1.004
[1.002, 1.004] | 4.108 [4.107, 4.111] |
| R200 sm_107a (212 SMs) | P1, (16, 48), 241817, CP2, C | checkpointed
2×forward+backward | 15.150 | 72.198 (FROST head-CP) | 15.042 | 1.007
[1.006, 1.008] | 4.800 [4.798, 4.802] |
| R200 sm_107a (212 SMs) | P1, (16, 48), 241817, CP2, C | checkpointed
with recompute handle (Cake only) | 14.895 | n/a | 14.789 | 1.007
[1.007, 1.008] | n/a |
| R200 sm_107a (212 SMs) | P1, (16, 48), 241817, CP2, D | forward |
5.504 | 22.540 (FROST head-CP) | 5.426 | 1.014 [1.014, 1.015] | 4.154
unpaired |
| R200 sm_107a (212 SMs) | P1, (16, 48), 241817, CP2, D | backward (=
forward+backward − forward) | 9.333 | 32.695 (FROST head-CP) | 9.332 |
1.000 (medians) | 3.504 (medians) |
| R200 sm_107a (212 SMs) | P1, (16, 48), 241817, CP2, D |
forward+backward | 14.837 | 55.236 (FROST head-CP) | 14.758 | 1.005
[1.005, 1.006] | 3.743 unpaired |
| R200 sm_107a (212 SMs) | P1, (16, 48), 241817, CP2, D | checkpointed
2×forward+backward | 17.045 | 72.198 (FROST head-CP) | 16.881 | 1.010
[1.009, 1.010] | 4.277 unpaired |
| R200 sm_107a (212 SMs) | P1, (16, 48), 241817, CP2, D | checkpointed
with recompute handle (Cake only) | 16.558 | n/a | 16.390 | 1.010
[1.010, 1.011] | n/a |
| R200 sm_107a (212 SMs) | P1, (16, 48), 241817, CP2, Z | forward |
4.941 | 22.540 (FROST head-CP) | 4.874 | 1.014 [1.013, 1.014] | 4.625
unpaired |
| R200 sm_107a (212 SMs) | P1, (16, 48), 241817, CP2, Z | backward (=
forward+backward − forward) | 8.831 | 32.695 (FROST head-CP) | 8.832 |
1.000 (medians) | 3.702 (medians) |
| R200 sm_107a (212 SMs) | P1, (16, 48), 241817, CP2, Z |
forward+backward | 13.771 | 55.236 (FROST head-CP) | 13.705 | 1.005
[1.004, 1.005] | 4.030 unpaired |
| R200 sm_107a (212 SMs) | P1, (16, 48), 241817, CP2, Z | checkpointed
2×forward+backward | 15.412 | 72.198 (FROST head-CP) | 15.272 | 1.009
[1.008, 1.009] | 4.727 unpaired |
| R200 sm_107a (212 SMs) | P1, (16, 48), 241817, CP2, Z | checkpointed
with recompute handle (Cake only) | 15.227 | n/a | 15.089 | 1.009
[1.009, 1.009] | n/a |
| R200 sm_107a (212 SMs) | P2, (16, 48), 261987, CP2, C | forward |
5.097 | 25.817 (FROST head-CP) | 5.032 | 1.013 [1.012, 1.013] | 5.131
[5.128, 5.133] |
| R200 sm_107a (212 SMs) | P2, (16, 48), 261987, CP2, C | backward (=
forward+backward − forward) | 9.258 | 37.431 (FROST head-CP) | 9.253 |
1.001 (medians) | 4.045 (medians) |
| R200 sm_107a (212 SMs) | P2, (16, 48), 261987, CP2, C |
forward+backward | 14.355 | 63.249 (FROST head-CP) | 14.285 | 1.005
[1.004, 1.005] | 4.428 [4.425, 4.429] |
| R200 sm_107a (212 SMs) | P2, (16, 48), 261987, CP2, C | checkpointed
2×forward+backward | 16.026 | 83.082 (FROST head-CP) | 15.892 | 1.009
[1.008, 1.009] | 5.228 [5.227, 5.230] |
| R200 sm_107a (212 SMs) | P2, (16, 48), 261987, CP2, C | checkpointed
with recompute handle (Cake only) | 15.875 | n/a | 15.740 | 1.009
[1.008, 1.009] | n/a |
| R200 sm_107a (212 SMs) | P2, (16, 48), 261987, CP2, D | forward |
5.489 | 25.817 (FROST head-CP) | 5.408 | 1.015 [1.014, 1.015] | 4.774
unpaired |
| R200 sm_107a (212 SMs) | P2, (16, 48), 261987, CP2, D | backward (=
forward+backward − forward) | 9.778 | 37.431 (FROST head-CP) | 9.777 |
1.000 (medians) | 3.829 (medians) |
| R200 sm_107a (212 SMs) | P2, (16, 48), 261987, CP2, D |
forward+backward | 15.267 | 63.249 (FROST head-CP) | 15.185 | 1.005
[1.005, 1.006] | 4.165 unpaired |
| R200 sm_107a (212 SMs) | P2, (16, 48), 261987, CP2, D | checkpointed
2×forward+backward | 17.116 | 83.082 (FROST head-CP) | 16.958 | 1.009
[1.009, 1.010] | 4.899 unpaired |
| R200 sm_107a (212 SMs) | P2, (16, 48), 261987, CP2, D | checkpointed
with recompute handle (Cake only) | 16.859 | n/a | 16.702 | 1.009
[1.009, 1.010] | n/a |
| R200 sm_107a (212 SMs) | P2, (16, 48), 261987, CP2, Z | forward |
5.338 | 25.817 (FROST head-CP) | 5.257 | 1.016 [1.015, 1.016] | 4.911
unpaired |
| R200 sm_107a (212 SMs) | P2, (16, 48), 261987, CP2, Z | backward (=
forward+backward − forward) | 9.499 | 37.431 (FROST head-CP) | 9.490 |
1.001 (medians) | 3.944 (medians) |
| R200 sm_107a (212 SMs) | P2, (16, 48), 261987, CP2, Z |
forward+backward | 14.837 | 63.249 (FROST head-CP) | 14.747 | 1.006
[1.005, 1.007] | 4.289 unpaired |
| R200 sm_107a (212 SMs) | P2, (16, 48), 261987, CP2, Z | checkpointed
2×forward+backward | 16.620 | 83.082 (FROST head-CP) | 16.456 | 1.010
[1.010, 1.010] | 5.049 unpaired |
| R200 sm_107a (212 SMs) | P2, (16, 48), 261987, CP2, Z | checkpointed
with recompute handle (Cake only) | 16.439 | n/a | 16.273 | 1.010
[1.010, 1.011] | n/a |
| R200 sm_107a (212 SMs) | P3, (16, 48), 259174, CP2, C | forward |
5.062 | 8.001 (FLA KCP, layout C) | 4.996 | 1.013 [1.012, 1.014] | 1.601
[1.601, 1.602] |
| R200 sm_107a (212 SMs) | P3, (16, 48), 259174, CP2, C | backward (=
forward+backward − forward) | 9.141 | 36.113 (FROST head-CP) | 9.144 |
1.000 (medians) | 3.949 (medians) |
| R200 sm_107a (212 SMs) | P3, (16, 48), 259174, CP2, C |
forward+backward | 14.203 | 60.846 (FROST head-CP) | 14.141 | 1.004
[1.004, 1.005] | 4.303 [4.301, 4.304] |
| R200 sm_107a (212 SMs) | P3, (16, 48), 259174, CP2, C | checkpointed
2×forward+backward | 15.933 | 72.333 (FLA KCP, layout C) | 15.805 |
1.008 [1.008, 1.009] | 4.577 [4.575, 4.580] |
| R200 sm_107a (212 SMs) | P3, (16, 48), 259174, CP2, C | checkpointed
with recompute handle (Cake only) | 15.761 | n/a | 15.627 | 1.008
[1.008, 1.009] | n/a |
| R200 sm_107a (212 SMs) | P3, (16, 48), 259174, CP2, D | forward |
5.417 | 8.001 (FLA KCP, layout C) | 5.342 | 1.014 [1.013, 1.015] | 1.498
unpaired |
| R200 sm_107a (212 SMs) | P3, (16, 48), 259174, CP2, D | backward (=
forward+backward − forward) | 9.525 | 36.113 (FROST head-CP) | 9.523 |
1.000 (medians) | 3.792 (medians) |
| R200 sm_107a (212 SMs) | P3, (16, 48), 259174, CP2, D |
forward+backward | 14.942 | 60.846 (FROST head-CP) | 14.865 | 1.005
[1.005, 1.006] | 4.093 unpaired |
| R200 sm_107a (212 SMs) | P3, (16, 48), 259174, CP2, D | checkpointed
2×forward+backward | 16.813 | 72.333 (FLA KCP, layout C) | 16.664 |
1.009 [1.009, 1.009] | 4.341 unpaired |
| R200 sm_107a (212 SMs) | P3, (16, 48), 259174, CP2, D | checkpointed
with recompute handle (Cake only) | 16.596 | n/a | 16.445 | 1.009
[1.009, 1.010] | n/a |
| R200 sm_107a (212 SMs) | P3, (16, 48), 259174, CP2, Z | forward |
5.373 | 8.001 (FLA KCP, layout C) | 5.296 | 1.015 [1.014, 1.015] | 1.511
unpaired |
| R200 sm_107a (212 SMs) | P3, (16, 48), 259174, CP2, Z | backward (=
forward+backward − forward) | 9.656 | 36.113 (FROST head-CP) | 9.660 |
1.000 (medians) | 3.738 (medians) |
| R200 sm_107a (212 SMs) | P3, (16, 48), 259174, CP2, Z |
forward+backward | 15.029 | 60.846 (FROST head-CP) | 14.956 | 1.005
[1.004, 1.006] | 4.068 unpaired |
| R200 sm_107a (212 SMs) | P3, (16, 48), 259174, CP2, Z | checkpointed
2×forward+backward | 16.946 | 72.333 (FLA KCP, layout C) | 16.799 |
1.009 [1.008, 1.009] | 4.306 unpaired |
| R200 sm_107a (212 SMs) | P3, (16, 48), 259174, CP2, Z | checkpointed
with recompute handle (Cake only) | 16.624 | n/a | 16.463 | 1.010
[1.009, 1.011] | n/a |
| R200 sm_107a (212 SMs) | P4, (16, 48), 254976, CP2, C | forward |
5.134 | 24.128 (FROST head-CP) | 5.075 | 1.011 [1.011, 1.012] | 4.753
[4.753, 4.756] |
| R200 sm_107a (212 SMs) | P4, (16, 48), 254976, CP2, C | backward (=
forward+backward − forward) | 9.154 | 35.332 (FROST head-CP) | 9.153 |
1.000 (medians) | 3.860 (medians) |
| R200 sm_107a (212 SMs) | P4, (16, 48), 254976, CP2, C |
forward+backward | 14.288 | 59.459 (FROST head-CP) | 14.229 | 1.004
[1.004, 1.005] | 4.179 [4.178, 4.180] |
| R200 sm_107a (212 SMs) | P4, (16, 48), 254976, CP2, C | checkpointed
2×forward+backward | 15.972 | 77.755 (FROST head-CP) | 15.854 | 1.007
[1.007, 1.008] | 4.904 [4.903, 4.906] |
| R200 sm_107a (212 SMs) | P4, (16, 48), 254976, CP2, C | checkpointed
with recompute handle (Cake only) | 15.760 | n/a | 15.643 | 1.008
[1.006, 1.008] | n/a |
| R200 sm_107a (212 SMs) | P4, (16, 48), 254976, CP2, D | forward |
5.247 | 24.128 (FROST head-CP) | 5.177 | 1.014 [1.013, 1.014] | 4.661
unpaired |
| R200 sm_107a (212 SMs) | P4, (16, 48), 254976, CP2, D | backward (=
forward+backward − forward) | 9.311 | 35.332 (FROST head-CP) | 9.308 |
1.000 (medians) | 3.796 (medians) |
| R200 sm_107a (212 SMs) | P4, (16, 48), 254976, CP2, D |
forward+backward | 14.557 | 59.459 (FROST head-CP) | 14.485 | 1.005
[1.004, 1.006] | 4.105 unpaired |
| R200 sm_107a (212 SMs) | P4, (16, 48), 254976, CP2, D | checkpointed
2×forward+backward | 16.412 | 77.755 (FROST head-CP) | 16.270 | 1.009
[1.008, 1.009] | 4.779 unpaired |
| R200 sm_107a (212 SMs) | P4, (16, 48), 254976, CP2, D | checkpointed
with recompute handle (Cake only) | 16.180 | n/a | 16.037 | 1.009
[1.009, 1.009] | n/a |
| R200 sm_107a (212 SMs) | P4, (16, 48), 254976, CP2, Z | forward |
5.235 | 24.128 (FROST head-CP) | 5.167 | 1.013 [1.013, 1.013] | 4.670
unpaired |
| R200 sm_107a (212 SMs) | P4, (16, 48), 254976, CP2, Z | backward (=
forward+backward − forward) | 9.300 | 35.332 (FROST head-CP) | 9.298 |
1.000 (medians) | 3.800 (medians) |
| R200 sm_107a (212 SMs) | P4, (16, 48), 254976, CP2, Z |
forward+backward | 14.535 | 59.459 (FROST head-CP) | 14.465 | 1.005
[1.005, 1.005] | 4.111 unpaired |
| R200 sm_107a (212 SMs) | P4, (16, 48), 254976, CP2, Z | checkpointed
2×forward+backward | 16.377 | 77.755 (FROST head-CP) | 16.245 | 1.008
[1.008, 1.009] | 4.786 unpaired |
| R200 sm_107a (212 SMs) | P4, (16, 48), 254976, CP2, Z | checkpointed
with recompute handle (Cake only) | 16.142 | n/a | 16.001 | 1.009
[1.009, 1.009] | n/a |
| R200 sm_107a (212 SMs) | P5, (16, 48), 249856, CP2, C | forward |
5.059 | 21.895 (FLA KCP, layout C) | 4.985 | 1.015 [1.015, 1.015] |
4.393 [4.390, 4.395] |
| R200 sm_107a (212 SMs) | P5, (16, 48), 249856, CP2, C | backward (=
forward+backward − forward) | 9.003 | 35.550 (FROST head-CP) | 9.007 |
1.000 (medians) | 3.947 (medians) |
| R200 sm_107a (212 SMs) | P5, (16, 48), 249856, CP2, C |
forward+backward | 14.062 | 59.614 (FLA KCP, layout C) | 13.992 | 1.005
[1.004, 1.005] | 4.261 [4.260, 4.262] |
| R200 sm_107a (212 SMs) | P5, (16, 48), 249856, CP2, C | checkpointed
2×forward+backward | 15.721 | 79.008 (FROST head-CP) | 15.572 | 1.009
[1.009, 1.011] | 5.073 [5.073, 5.075] |
| R200 sm_107a (212 SMs) | P5, (16, 48), 249856, CP2, C | checkpointed
with recompute handle (Cake only) | 15.574 | n/a | 15.424 | 1.010
[1.010, 1.010] | n/a |
| R200 sm_107a (212 SMs) | P5, (16, 48), 249856, CP2, D | forward |
5.343 | 21.895 (FLA KCP, layout C) | 5.274 | 1.013 [1.013, 1.014] |
4.152 unpaired |
| R200 sm_107a (212 SMs) | P5, (16, 48), 249856, CP2, D | backward (=
forward+backward − forward) | 8.486 | 35.550 (FROST head-CP) | 8.485 |
1.000 (medians) | 4.190 (medians) |
| R200 sm_107a (212 SMs) | P5, (16, 48), 249856, CP2, D |
forward+backward | 13.829 | 59.614 (FLA KCP, layout C) | 13.758 | 1.005
[1.004, 1.006] | 4.333 unpaired |
| R200 sm_107a (212 SMs) | P5, (16, 48), 249856, CP2, D | checkpointed
2×forward+backward | 16.248 | 79.008 (FROST head-CP) | 16.113 | 1.008
[1.007, 1.009] | 4.903 unpaired |
| R200 sm_107a (212 SMs) | P5, (16, 48), 249856, CP2, D | checkpointed
with recompute handle (Cake only) | 15.316 | n/a | 15.183 | 1.009
[1.009, 1.009] | n/a |
| R200 sm_107a (212 SMs) | P5, (16, 48), 249856, CP2, Z | forward |
5.123 | 21.895 (FLA KCP, layout C) | 5.047 | 1.015 [1.014, 1.015] |
4.339 unpaired |
| R200 sm_107a (212 SMs) | P5, (16, 48), 249856, CP2, Z | backward (=
forward+backward − forward) | 9.125 | 35.550 (FROST head-CP) | 9.124 |
1.000 (medians) | 3.896 (medians) |
| R200 sm_107a (212 SMs) | P5, (16, 48), 249856, CP2, Z |
forward+backward | 14.248 | 59.614 (FLA KCP, layout C) | 14.171 | 1.005
[1.005, 1.006] | 4.207 unpaired |
| R200 sm_107a (212 SMs) | P5, (16, 48), 249856, CP2, Z | checkpointed
2×forward+backward | 15.894 | 79.008 (FROST head-CP) | 15.738 | 1.010
[1.010, 1.010] | 5.020 unpaired |
| R200 sm_107a (212 SMs) | P5, (16, 48), 249856, CP2, Z | checkpointed
with recompute handle (Cake only) | 15.757 | n/a | 15.604 | 1.010
[1.009, 1.010] | n/a |

P1–P5: packed variable-length document mixes (documents: P1 6, P2 3, P3
2, P4 1, P5 4; P1–P3 are the packs of issue #7082); (H, HV) = query/key
heads and value heads; S = total tokens; layouts C contiguous, Z zigzag,
D zigzag per document.

Non-Cake implementations (the fastest one that passed the accuracy
check, per row): FROST head-CP = head-parallel all-to-all around the
cuDNN frontend 1.32.1 FROST GDN engine; FLA KCP = FLA 0.6.0
context-parallel; n/a = no recompute-handle form; FlashQLA: unsupported
(no sm_107a build).

B200 sm_100a (CP2 / CP4 / CP8 / CP16): pending (measurement queued).

GB300 sm_103a: pending (measurement queued).

The kernel's other Cake variants, all on main, are the deterministic
single-GPU `flashinfer.experimental.cake_gdn_det_train`, the
non-deterministic single-GPU
`flashinfer.experimental.cake.cake_gdn_train` (#8157) and the
deterministic context-parallel
`flashinfer.experimental.cake_gdn_det_train_kcp`
(`flashinfer.cake_gdn_train_kcp` with `deterministic=True`), and the
kernel covers sm_100a, sm_103a and sm_107a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added context-parallel packed GDN training with deterministic and
experimental numerical routes, plus configurable checkpointing,
recomputation, and replay options.
* Added support for querying workspace, saved-state, and communication
memory requirements.
* Added benchmark coverage for training workflows and optional
comparisons with other implementations.

* **Documentation**
* Added guidance on the new training backend, supported inputs, options,
and known limitations.

* **Tests**
* Added correctness and build checks, including coverage for outputs,
gradients, replay, and workspace behavior.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [872d657](https://github.com/flashinfer-ai/flashinfer/commit/872d6572d2691fc8ca0086b5ef5fcc6151596d74)

- **作者**: eigen
- **时间**: 2026-11-01T07:41:26Z
- **提交信息**: perf(cake_deepgemm_dense_mqa): serve fp8:q128:short and fp8:full:le32:short on sm_100a with a four-stage TMEM ring bucket program (#8173)

This PR follows up #7607, #7643, #7741, #7779, #8113, #8124, #8142,
#8150, #8151 and #8153. FlashInfer's Cake DeepGEMM-form MQA logits
programs for Blackwell back `flashinfer.dense_mqa` and
`flashinfer.paged_mqa`. The variants are dense FP8 with 32 or 64 heads,
dense FP4 with 32 heads (including fused metadata + logits sequences),
and paged FP8. This PR changes dense FP8 with 32 heads, on sm_100a
(B200) only. It adds one program,
`cake_deepgemm_dense_mqa_0532d98e460720fde283`, as two generated units
(a kernel and a binding). Its kernel text is the same as
`cake_deepgemm_dense_mqa_d928b7322c3819144a52`. It uses a 4-stage TMEM
accumulator ring instead of the shipped ring. Each math warpgroup
therefore gets its own double buffer. On sm_100a, two routes gain a
stage bucket that runs the new program for the `logits` stage. Route
`fp8:q128:short` uses it for K up to 4096 keys. Route
`fp8:full:le32:short` uses it for K up to 32768 keys. Longer K keeps
`cake_deepgemm_dense_mqa_d928b7322c3819144a52`. Every other call keeps
its program, and sm_103a is unchanged. The only other changes are the
catalog, the `dense_mqa.py` docstring, the README and the tests. Logits
are bitwise equal on every row of both tables (106/106 on each GPU). The
baseline is the previous version, FlashInfer b895321c5cb9 (#8153), for
the dense MQA paths. On B200, 3 of the 106 rows run the updated program.
`Q 16, K 32768` FP8 goes from 7.84 to 7.63 µs (1.0295). `Q 128, K 2048`
FP8 goes from 6.14 to 5.82 µs (1.0551). `Q 128, K 4096` FP8 goes from
7.39 to 7.09 µs (1.0429). Each of these 3 rows is faster in all 3
sessions. The other 103 rows run byte-identical programs in both
versions. They read 0.9960–1.0102 (median 1.0000), which is measurement
noise. On GB300, no row changes route. All 106 rows run byte-identical
programs and read 0.9941–1.0077 (median 1.0000), which is also
measurement noise.

**NVIDIA B200** (sm_100a, 148 SMs), CUDA 13.4 (nvcc V13.4.92,
JIT-compiled), driver 580.82.07, torch 2.14.1+cu130. Previous version =
FlashInfer b895321c5cb9 (dense MQA paths). Timing is CUPTI GPU time per
call with a cold L2. µs is the median over the 3 sessions of each
session's median. Speedup is the median over the sessions of previous /
this (> 1 = faster). Rows that launch more than one kernel per call
report the sum of kernel times. The notation is the same as in #7643. `Q
q, K k` is q queries over k keys. `prefill Q q, prefix p, causal` is q
new queries attending causally over p cached keys plus themselves (K = p
+ q). "2 sequences" and "2048-query chunks" mean the same as in #7643.
"updated" means the row now runs
`cake_deepgemm_dense_mqa_0532d98e460720fde283` instead of
`cake_deepgemm_dense_mqa_d928b7322c3819144a52`. "same program" means
every program on the row is byte-identical to the previous version.

| shape | dtype | heads | previous µs | this PR µs | speedup | program |
|---|---|---:|---:|---:|---:|---|
| prefill Q 37, prefix 4100, causal | FP8 | 32 | 5.31 | 5.31 | 1.0000 |
same program |
| prefill Q 1024, prefix 32779, causal | FP8 | 32 | 138.03 | 138.09 |
1.0001 | same program |
| prefill Q 1, prefix 0, causal | FP8 | 64 | 4.09 | 4.09 | 0.9999 | same
program |
| prefill Q 1, prefix 4100, causal | FP8 | 64 | 4.16 | 4.16 | 1.0000 |
same program |
| prefill Q 1, prefix 32779, causal | FP8 | 64 | 5.15 | 5.15 | 1.0000 |
same program |
| prefill Q 1, prefix 131077, causal | FP8 | 64 | 8.06 | 8.06 | 1.0019 |
same program |
| prefill Q 2, prefix 0, causal | FP8 | 64 | 4.08 | 4.08 | 1.0000 | same
program |
| prefill Q 2, prefix 4100, causal | FP8 | 64 | 4.83 | 4.83 | 1.0000 |
same program |
| prefill Q 3, prefix 0, causal | FP8 | 64 | 3.90 | 3.90 | 1.0000 | same
program |
| prefill Q 3, prefix 4100, causal | FP8 | 64 | 4.61 | 4.61 | 1.0000 |
same program |
| prefill Q 7, prefix 0, causal | FP8 | 64 | 3.98 | 3.98 | 1.0000 | same
program |
| prefill Q 7, prefix 4100, causal | FP8 | 64 | 4.58 | 4.58 | 0.9999 |
same program |
| prefill Q 8, prefix 0, causal | FP8 | 64 | 3.93 | 3.94 | 1.0000 | same
program |
| prefill Q 8, prefix 4100, causal | FP8 | 64 | 4.58 | 4.58 | 1.0000 |
same program |
| prefill Q 16, prefix 0, causal | FP8 | 64 | 3.92 | 3.90 | 1.0000 |
same program |
| prefill Q 16, prefix 4100, causal | FP8 | 64 | 4.64 | 4.64 | 1.0000 |
same program |
| prefill Q 37, prefix 0, causal | FP8 | 64 | 3.94 | 3.94 | 1.0000 |
same program |
| prefill Q 37, prefix 4100, causal | FP8 | 64 | 5.66 | 5.66 | 0.9999 |
same program |
| prefill Q 37, prefix 32779, causal | FP8 | 64 | 14.34 | 14.34 | 1.0000
| same program |
| prefill Q 37, prefix 131077, causal | FP8 | 64 | 40.19 | 40.21 |
0.9996 | same program |
| prefill Q 64, prefix 0, causal | FP8 | 64 | 3.97 | 3.97 | 1.0000 |
same program |
| prefill Q 64, prefix 4100, causal | FP8 | 64 | 6.62 | 6.62 | 1.0000 |
same program |
| prefill Q 128, prefix 0, causal | FP8 | 64 | 4.13 | 4.11 | 1.0000 |
same program |
| prefill Q 128, prefix 4100, causal | FP8 | 64 | 9.31 | 9.31 | 1.0000 |
same program |
| prefill Q 128, prefix 4100, causal, 2 sequences | FP8 | 64 | 8.26 |
8.22 | 0.9980 | same program |
| prefill Q 128, prefix 32779, causal | FP8 | 64 | 34.64 | 34.62 |
1.0005 | same program |
| prefill Q 128, prefix 131077, causal | FP8 | 64 | 127.89 | 126.60 |
1.0102 | same program |
| prefill Q 129, prefix 0, causal | FP8 | 64 | 4.11 | 4.11 | 0.9999 |
same program |
| prefill Q 129, prefix 4100, causal | FP8 | 64 | 9.34 | 9.31 | 1.0017 |
same program |
| prefill Q 1023, prefix 0, causal | FP8 | 64 | 10.30 | 10.30 | 1.0000 |
same program |
| prefill Q 1023, prefix 4100, causal | FP8 | 64 | 40.50 | 40.48 |
1.0004 | same program |
| prefill Q 1024, prefix 0, causal | FP8 | 64 | 10.40 | 10.40 | 1.0000 |
same program |
| prefill Q 1024, prefix 4100, causal | FP8 | 64 | 40.30 | 40.32 |
1.0000 | same program |
| prefill Q 1024, prefix 32779, causal | FP8 | 64 | 265.77 | 265.74 |
0.9999 | same program |
| prefill Q 1024, prefix 131077, causal | FP8 | 64 | 1088.43 | 1089.64 |
0.9993 | same program |
| prefill Q 4096, prefix 0, causal | FP8 | 64 | 70.72 | 70.72 | 1.0000 |
same program |
| prefill Q 4096, prefix 4100, causal | FP8 | 64 | 202.22 | 201.65 |
1.0067 | same program |
| prefill Q 4096, prefix 32779, causal | FP8 | 64 | 1149.57 | 1150.09 |
0.9995 | same program |
| prefill Q 4096, prefix 32779, causal, 2 sequences | FP8 | 64 | 791.89
| 790.68 | 1.0012 | same program |
| prefill Q 4096, prefix 32779, causal, 2048-query chunks | FP8 | 64 |
1154.75 | 1154.59 | 1.0020 | same program |
| prefill Q 4096, prefix 131077, causal | FP8 | 64 | 4467.74 | 4475.04 |
0.9989 | same program |
| prefill Q 4096, prefix 131077, causal, 2048-query chunks | FP8 | 64 |
4467.12 | 4471.55 | 0.9990 | same program |
| prefill Q 8192, prefix 0, causal | FP8 | 64 | 280.45 | 280.02 | 1.0004
| same program |
| prefill Q 8192, prefix 4100, causal | FP8 | 64 | 553.44 | 553.20 |
0.9995 | same program |
| prefill Q 8192, prefix 32779, causal | FP8 | 64 | 2471.00 | 2470.25 |
1.0002 | same program |
| prefill Q 8192, prefix 32779, causal, 2048-query chunks | FP8 | 64 |
2489.46 | 2484.08 | 1.0028 | same program |
| prefill Q 8192, prefix 131077, causal | FP8 | 64 | 9141.81 | 9185.84 |
0.9961 | same program |
| prefill Q 8192, prefix 131077, causal, 2048-query chunks | FP8 | 64 |
9100.74 | 9100.53 | 1.0000 | same program |
| prefill Q 16231, prefix 0, causal | FP8 | 64 | 1117.95 | 1108.38 |
1.0078 | same program |
| prefill Q 16231, prefix 4100, causal | FP8 | 64 | 1651.55 | 1651.39 |
1.0003 | same program |
| prefill Q 16231, prefix 32779, causal | FP8 | 64 | 5458.13 | 5472.92 |
0.9975 | same program |
| prefill Q 16231, prefix 32779, causal, 2048-query chunks | FP8 | 64 |
5571.38 | 5546.85 | 1.0024 | same program |
| prefill Q 16231, prefix 131077, causal | FP8 | 64 | 18673.42 |
18679.00 | 0.9994 | same program |
| prefill Q 16231, prefix 131077, causal, 2048-query chunks | FP8 | 64 |
18668.55 | 18701.85 | 1.0000 | same program |
| Q 1, K 4096 | FP8 | 32 | 4.02 | 4.00 | 1.0000 | same program |
| Q 1, K 32768 | FP8 | 32 | 4.83 | 4.83 | 1.0000 | same program |
| Q 1, K 131072 | FP8 | 32 | 7.74 | 7.74 | 1.0000 | same program |
| Q 1, K 1048576 | FP8 | 32 | 31.07 | 31.02 | 1.0000 | same program |
| Q 1, K 1048832 | FP8 | 32 | 31.07 | 31.06 | 0.9995 | same program |
| Q 3, K 8192 | FP8 | 32 | 4.86 | 4.83 | 1.0000 | same program |
| Q 3, K 1048832 | FP8 | 32 | 34.88 | 34.85 | 1.0009 | same program |
| Q 16, K 2048 | FP8 | 32 | 4.61 | 4.61 | 1.0000 | same program |
| Q 16, K 4096 | FP8 | 32 | 4.74 | 4.74 | 1.0000 | same program |
| Q 16, K 32768 | FP8 | 32 | 7.84 | 7.63 | 1.0295 | updated |
| Q 16, K 131072 | FP8 | 32 | 14.80 | 14.80 | 0.9989 | same program |
| Q 16, K 1048576 | FP8 | 32 | 70.18 | 70.21 | 0.9996 | same program |
| Q 16, K 1048832 | FP8 | 32 | 71.63 | 71.58 | 1.0007 | same program |
| Q 33, K 8192 | FP8 | 32 | 5.52 | 5.54 | 1.0000 | same program |
| Q 33, K 1048832 | FP8 | 32 | 191.09 | 191.07 | 1.0003 | same program |
| Q 37, K 4137 | FP8 | 32 | 5.31 | 5.31 | 1.0000 | same program |
| Q 128, K 2048 | FP8 | 32 | 6.14 | 5.82 | 1.0551 | updated |
| Q 128, K 4096 | FP8 | 32 | 7.39 | 7.09 | 1.0429 | updated |
| Q 128, K 32768 | FP8 | 32 | 21.12 | 21.15 | 1.0000 | same program |
| Q 128, K 131072 | FP8 | 32 | 64.61 | 64.48 | 1.0020 | same program |
| Q 128, K 131328 | FP8 | 32 | 64.62 | 64.50 | 1.0003 | same program |
| Q 130, K 8192 | FP8 | 32 | 10.40 | 10.40 | 1.0000 | same program |
| Q 130, K 8448 | FP8 | 32 | 10.62 | 10.62 | 1.0000 | same program |
| Q 130, K 65792 | FP8 | 32 | 39.23 | 39.17 | 0.9996 | same program |
| Q 132, K 2048 | FP8 | 32 | 6.83 | 6.82 | 1.0000 | same program |
| Q 132, K 8448 | FP8 | 32 | 10.56 | 10.56 | 0.9985 | same program |
| Q 132, K 65792 | FP8 | 32 | 39.45 | 39.46 | 1.0018 | same program |
| Q 1024, K 33803 | FP8 | 32 | 140.11 | 140.40 | 0.9987 | same program |
| Q 2052, K 2048 | FP8 | 32 | 23.87 | 23.84 | 0.9993 | same program |
| Q 2052, K 8448 | FP8 | 32 | 70.45 | 70.42 | 1.0011 | same program |
| Q 2053, K 2048 | FP8 | 32 | 24.11 | 24.16 | 0.9980 | same program |
| Q 2053, K 8448 | FP8 | 32 | 71.04 | 71.02 | 1.0004 | same program |
| Q 1, K 4096 | FP4 | 32 | 4.03 | 4.03 | 1.0000 | same program |
| Q 1, K 32768 | FP4 | 32 | 4.75 | 4.75 | 1.0000 | same program |
| Q 1, K 131072 | FP4 | 32 | 6.58 | 6.54 | 1.0024 | same program |
| Q 1, K 131328 | FP4 | 32 | 6.72 | 6.72 | 1.0001 | same program |
| Q 7, K 2048 | FP4 | 32 | 4.91 | 4.91 | 1.0000 | same program |
| Q 16, K 4096 | FP4 | 32 | 5.06 | 5.06 | 1.0000 | same program |
| Q 16, K 32768 | FP4 | 32 | 7.18 | 7.17 | 1.0045 | same program |
| Q 16, K 131072 | FP4 | 32 | 13.60 | 13.60 | 1.0000 | same program |
| Q 16, K 1048576 | FP4 | 32 | 63.18 | 63.22 | 0.9995 | same program |
| Q 16, K 1048832 | FP4 | 32 | 65.82 | 65.82 | 0.9995 | same program |
| Q 33, K 8192 | FP4 | 32 | 5.78 | 5.79 | 0.9972 | same program |
| Q 33, K 1048832 | FP4 | 32 | 136.16 | 136.30 | 0.9989 | same program |
| Q 128, K 4096 | FP4 | 32 | 6.77 | 6.77 | 1.0048 | same program |
| Q 128, K 32768 | FP4 | 32 | 19.79 | 19.79 | 0.9992 | same program |
| Q 128, K 131072 | FP4 | 32 | 61.54 | 61.52 | 1.0003 | same program |
| Q 130, K 65536 | FP4 | 32 | 35.84 | 35.87 | 0.9991 | same program |
| Q 130, K 65792 | FP4 | 32 | 37.73 | 37.66 | 1.0004 | same program |
| Q 1024, K 2048 | FP4 | 32 | 14.19 | 14.24 | 0.9966 | same program |
| Q 2052, K 2048 | FP4 | 32 | 23.97 | 24.06 | 0.9960 | same program |
| Q 2052, K 65792 | FP4 | 32 | 474.30 | 474.76 | 0.9990 | same program |

**NVIDIA GB300** (sm_103a, 152 SMs), CUDA 13.4 (nvcc V13.4.92,
JIT-compiled), driver 580.159.03, torch 2.14.1+cu130. Previous version =
FlashInfer b895321c5cb9 (dense MQA paths). Timing, notation and the
labels are the same as in the B200 table.

| shape | dtype | heads | previous µs | this PR µs | speedup | program |
|---|---|---:|---:|---:|---:|---|
| prefill Q 37, prefix 4100, causal | FP8 | 32 | 5.31 | 5.31 | 1.0000 |
same program |
| prefill Q 1024, prefix 32779, causal | FP8 | 32 | 107.57 | 107.49 |
1.0003 | same program |
| prefill Q 1, prefix 0, causal | FP8 | 64 | 3.57 | 3.55 | 1.0001 | same
program |
| prefill Q 1, prefix 4100, causal | FP8 | 64 | 3.76 | 3.74 | 1.0000 |
same program |
| prefill Q 1, prefix 32779, causal | FP8 | 64 | 4.93 | 4.93 | 1.0000 |
same program |
| prefill Q 1, prefix 131077, causal | FP8 | 64 | 7.62 | 7.58 | 1.0021 |
same program |
| prefill Q 2, prefix 0, causal | FP8 | 64 | 3.57 | 3.58 | 1.0000 | same
program |
| prefill Q 2, prefix 4100, causal | FP8 | 64 | 4.35 | 4.35 | 1.0000 |
same program |
| prefill Q 3, prefix 0, causal | FP8 | 64 | 3.62 | 3.62 | 1.0000 | same
program |
| prefill Q 3, prefix 4100, causal | FP8 | 64 | 4.22 | 4.22 | 1.0000 |
same program |
| prefill Q 7, prefix 0, causal | FP8 | 64 | 3.58 | 3.58 | 1.0000 | same
program |
| prefill Q 7, prefix 4100, causal | FP8 | 64 | 4.27 | 4.27 | 1.0000 |
same program |
| prefill Q 8, prefix 0, causal | FP8 | 64 | 3.55 | 3.55 | 1.0000 | same
program |
| prefill Q 8, prefix 4100, causal | FP8 | 64 | 4.42 | 4.42 | 1.0000 |
same program |
| prefill Q 16, prefix 0, causal | FP8 | 64 | 3.57 | 3.57 | 1.0000 |
same program |
| prefill Q 16, prefix 4100, causal | FP8 | 64 | 4.35 | 4.35 | 1.0036 |
same program |
| prefill Q 37, prefix 0, causal | FP8 | 64 | 3.78 | 3.78 | 1.0000 |
same program |
| prefill Q 37, prefix 4100, causal | FP8 | 64 | 5.23 | 5.23 | 1.0000 |
same program |
| prefill Q 37, prefix 32779, causal | FP8 | 64 | 12.54 | 12.54 | 0.9993
| same program |
| prefill Q 37, prefix 131077, causal | FP8 | 64 | 33.82 | 33.84 |
0.9995 | same program |
| prefill Q 64, prefix 0, causal | FP8 | 64 | 3.84 | 3.84 | 1.0000 |
same program |
| prefill Q 64, prefix 4100, causal | FP8 | 64 | 6.05 | 6.05 | 1.0000 |
same program |
| prefill Q 128, prefix 0, causal | FP8 | 64 | 4.03 | 4.03 | 1.0000 |
same program |
| prefill Q 128, prefix 4100, causal | FP8 | 64 | 8.58 | 8.58 | 1.0000 |
same program |
| prefill Q 128, prefix 4100, causal, 2 sequences | FP8 | 64 | 7.50 |
7.52 | 0.9979 | same program |
| prefill Q 128, prefix 32779, causal | FP8 | 64 | 30.19 | 30.21 |
0.9995 | same program |
| prefill Q 128, prefix 131077, causal | FP8 | 64 | 102.64 | 102.64 |
1.0000 | same program |
| prefill Q 129, prefix 0, causal | FP8 | 64 | 4.00 | 4.00 | 1.0000 |
same program |
| prefill Q 129, prefix 4100, causal | FP8 | 64 | 8.54 | 8.54 | 1.0000 |
same program |
| prefill Q 1023, prefix 0, causal | FP8 | 64 | 9.57 | 9.58 | 0.9983 |
same program |
| prefill Q 1023, prefix 4100, causal | FP8 | 64 | 35.58 | 35.57 |
0.9996 | same program |
| prefill Q 1024, prefix 0, causal | FP8 | 64 | 9.63 | 9.63 | 1.0000 |
same program |
| prefill Q 1024, prefix 4100, causal | FP8 | 64 | 35.62 | 35.58 |
1.0000 | same program |
| prefill Q 1024, prefix 32779, causal | FP8 | 64 | 205.76 | 205.68 |
0.9998 | same program |
| prefill Q 1024, prefix 131077, causal | FP8 | 64 | 828.68 | 829.55 |
0.9965 | same program |
| prefill Q 4096, prefix 0, causal | FP8 | 64 | 61.44 | 61.44 | 1.0000 |
same program |
| prefill Q 4096, prefix 4100, causal | FP8 | 64 | 155.42 | 155.39 |
1.0002 | same program |
| prefill Q 4096, prefix 32779, causal | FP8 | 64 | 871.99 | 874.23 |
0.9960 | same program |
| prefill Q 4096, prefix 32779, causal, 2 sequences | FP8 | 64 | 580.43
| 581.97 | 1.0003 | same program |
| prefill Q 4096, prefix 32779, causal, 2048-query chunks | FP8 | 64 |
876.14 | 876.60 | 1.0020 | same program |
| prefill Q 4096, prefix 131077, causal | FP8 | 64 | 3484.52 | 3488.72 |
1.0063 | same program |
| prefill Q 4096, prefix 131077, causal, 2048-query chunks | FP8 | 64 |
3504.58 | 3471.24 | 1.0077 | same program |
| prefill Q 8192, prefix 0, causal | FP8 | 64 | 211.33 | 211.58 | 1.0001
| same program |
| prefill Q 8192, prefix 4100, causal | FP8 | 64 | 411.86 | 412.35 |
1.0001 | same program |
| prefill Q 8192, prefix 32779, causal | FP8 | 64 | 1865.00 | 1874.80 |
1.0054 | same program |
| prefill Q 8192, prefix 32779, causal, 2048-query chunks | FP8 | 64 |
1911.22 | 1907.48 | 0.9990 | same program |
| prefill Q 8192, prefix 131077, causal | FP8 | 64 | 7176.99 | 7139.61 |
1.0009 | same program |
| prefill Q 8192, prefix 131077, causal, 2048-query chunks | FP8 | 64 |
7185.46 | 7179.69 | 0.9994 | same program |
| prefill Q 16231, prefix 0, causal | FP8 | 64 | 828.80 | 830.31 |
0.9976 | same program |
| prefill Q 16231, prefix 4100, causal | FP8 | 64 | 1248.53 | 1246.48 |
0.9985 | same program |
| prefill Q 16231, prefix 32779, causal | FP8 | 64 | 4247.67 | 4249.47 |
1.0008 | same program |
| prefill Q 16231, prefix 32779, causal, 2048-query chunks | FP8 | 64 |
4289.40 | 4288.17 | 0.9991 | same program |
| prefill Q 16231, prefix 131077, causal | FP8 | 64 | 14667.32 |
14683.30 | 0.9990 | same program |
| prefill Q 16231, prefix 131077, causal, 2048-query chunks | FP8 | 64 |
14772.36 | 14778.64 | 0.9993 | same program |
| Q 1, K 4096 | FP8 | 32 | 3.57 | 3.55 | 1.0045 | same program |
| Q 1, K 32768 | FP8 | 32 | 4.58 | 4.58 | 1.0000 | same program |
| Q 1, K 131072 | FP8 | 32 | 7.31 | 7.31 | 0.9999 | same program |
| Q 1, K 1048576 | FP8 | 32 | 30.10 | 30.08 | 1.0005 | same program |
| Q 1, K 1048832 | FP8 | 32 | 30.03 | 30.06 | 1.0005 | same program |
| Q 3, K 8192 | FP8 | 32 | 4.54 | 4.54 | 1.0000 | same program |
| Q 3, K 1048832 | FP8 | 32 | 33.44 | 33.57 | 0.9962 | same program |
| Q 16, K 2048 | FP8 | 32 | 4.54 | 4.54 | 1.0000 | same program |
| Q 16, K 4096 | FP8 | 32 | 4.74 | 4.74 | 1.0000 | same program |
| Q 16, K 32768 | FP8 | 32 | 7.15 | 7.14 | 1.0022 | same program |
| Q 16, K 131072 | FP8 | 32 | 13.38 | 13.39 | 1.0000 | same program |
| Q 16, K 1048576 | FP8 | 32 | 58.02 | 58.05 | 1.0000 | same program |
| Q 16, K 1048832 | FP8 | 32 | 58.78 | 58.80 | 0.9999 | same program |
| Q 33, K 8192 | FP8 | 32 | 5.38 | 5.41 | 1.0000 | same program |
| Q 33, K 1048832 | FP8 | 32 | 180.42 | 180.88 | 0.9974 | same program |
| Q 37, K 4137 | FP8 | 32 | 5.31 | 5.31 | 1.0000 | same program |
| Q 128, K 2048 | FP8 | 32 | 5.86 | 5.86 | 1.0000 | same program |
| Q 128, K 4096 | FP8 | 32 | 7.01 | 7.01 | 1.0000 | same program |
| Q 128, K 32768 | FP8 | 32 | 18.37 | 18.37 | 1.0000 | same program |
| Q 128, K 131072 | FP8 | 32 | 53.36 | 53.34 | 1.0003 | same program |
| Q 128, K 131328 | FP8 | 32 | 54.90 | 54.91 | 0.9997 | same program |
| Q 130, K 8192 | FP8 | 32 | 9.50 | 9.49 | 0.9983 | same program |
| Q 130, K 8448 | FP8 | 32 | 9.76 | 9.76 | 1.0000 | same program |
| Q 130, K 65792 | FP8 | 32 | 32.43 | 32.45 | 0.9995 | same program |
| Q 132, K 2048 | FP8 | 32 | 6.45 | 6.43 | 1.0000 | same program |
| Q 132, K 8448 | FP8 | 32 | 9.63 | 9.60 | 1.0000 | same program |
| Q 132, K 65792 | FP8 | 32 | 32.43 | 32.45 | 0.9995 | same program |
| Q 1024, K 33803 | FP8 | 32 | 109.54 | 109.49 | 1.0004 | same program |
| Q 2052, K 2048 | FP8 | 32 | 20.86 | 20.85 | 0.9992 | same program |
| Q 2052, K 8448 | FP8 | 32 | 60.46 | 60.45 | 1.0000 | same program |
| Q 2053, K 2048 | FP8 | 32 | 21.34 | 21.31 | 1.0007 | same program |
| Q 2053, K 8448 | FP8 | 32 | 61.06 | 61.06 | 0.9997 | same program |
| Q 1, K 4096 | FP4 | 32 | 3.81 | 3.81 | 1.0000 | same program |
| Q 1, K 32768 | FP4 | 32 | 4.48 | 4.48 | 1.0000 | same program |
| Q 1, K 131072 | FP4 | 32 | 6.21 | 6.24 | 0.9949 | same program |
| Q 1, K 131328 | FP4 | 32 | 6.59 | 6.59 | 1.0000 | same program |
| Q 7, K 2048 | FP4 | 32 | 4.38 | 4.38 | 1.0000 | same program |
| Q 16, K 4096 | FP4 | 32 | 4.86 | 4.88 | 0.9967 | same program |
| Q 16, K 32768 | FP4 | 32 | 6.75 | 6.75 | 1.0000 | same program |
| Q 16, K 131072 | FP4 | 32 | 12.03 | 12.05 | 1.0000 | same program |
| Q 16, K 1048576 | FP4 | 32 | 54.37 | 54.34 | 1.0003 | same program |
| Q 16, K 1048832 | FP4 | 32 | 54.16 | 54.18 | 0.9997 | same program |
| Q 33, K 8192 | FP4 | 32 | 5.57 | 5.57 | 1.0000 | same program |
| Q 33, K 1048832 | FP4 | 32 | 118.23 | 118.35 | 1.0008 | same program |
| Q 128, K 4096 | FP4 | 32 | 6.35 | 6.37 | 0.9975 | same program |
| Q 128, K 32768 | FP4 | 32 | 17.10 | 17.09 | 1.0009 | same program |
| Q 128, K 131072 | FP4 | 32 | 52.93 | 52.95 | 0.9997 | same program |
| Q 130, K 65536 | FP4 | 32 | 30.64 | 30.62 | 1.0005 | same program |
| Q 130, K 65792 | FP4 | 32 | 30.75 | 30.74 | 1.0000 | same program |
| Q 1024, K 2048 | FP4 | 32 | 13.95 | 14.06 | 0.9977 | same program |
| Q 2052, K 2048 | FP4 | 32 | 21.62 | 21.74 | 0.9941 | same program |
| Q 2052, K 65792 | FP4 | 32 | 394.47 | 394.42 | 0.9997 | same program |

The family's other Cake variants (dense FP8 with 32 or 64 heads, dense
FP4 with 32 heads including fused metadata + logits sequences, and paged
FP8) ship on sm_100a and sm_103a only.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Improvements**
* On sm_100a, two FP8 dense-MQA configurations now use a specialized
execution path for supported sequence lengths: `fp8:q128:short` up to
K=4096 and `fp8:full:le32:short` up to K=32768. The selected path
produces the same logits and scheduling information as the corresponding
route.
* **Documentation**
* Clarified the supported sequence-length ranges and execution behavior
for these configurations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery Huang <averyh@nvidia.com>

### [1ec41b4](https://github.com/flashinfer-ai/flashinfer/commit/1ec41b4b0e21b1005c61f9b37cc33a3edcfd1258)

- **作者**: eigen
- **时间**: 2026-11-01T07:16:13Z
- **提交信息**: perf(cake_causal_conv1d_det): exact products in the backward on the targets that measured faster (#8169)

`flashinfer.cake_causal_conv1d_det_train` is the deterministic packed
depthwise causal conv1d + SiLU for training. It has a forward pass and
these backward routes: `bwd`, `bwd_dt`, `bwd_bias`, `bwd_bias_bf16`,
`bwd_fp32g` and `bwd_bias_fp32g`. Each route is compiled separately for
each shape band and target arch. On CUDA 13.4 or newer, this PR emits
the products feeding an exact pairwise add as `mul.rn.f32x2` instead of
`fma.rn.f32x2` with a -0.0 addend. It does this only in the programs
where the new form measured faster: one on B200 (sm_100a), three on
GB300 (sm_103a) and six on R200 (sm_107a). The outputs y, dx, dw and db
are bitwise identical. Every other program keeps the current code, and
so does every build with an older toolkit. The baseline is the Cake
package currently shipped on FlashInfer main.

Per-GPU results on CUDA 13.4 (the R200 is a 212-SM node), using the same
GPU and inputs with paired interleaved A/B over 3 sessions. Latency is
the median span of one timed step in microseconds, and ± is half the
difference between two copies of the same build. Speedup is the median
per-block baseline / new ratio. q is the A/A noise: the 95th percentile
of |1 - ratio| between those copies. `faster` means the median ratio is
above 1 + q, a Mann-Whitney test rejects equality, and the new build is
faster in every session and in both run orders; any other row is a `tie`
(no row is slower beyond q). Programs that keep the current code are not
listed.

### B200 (sm_100a)

| route | S | C | timed | baseline us | new us | speedup (median paired
ratio) | A/A noise q | result |
|---|---|---|---|---|---|---|---|---|
| bwd | 250340 | 64 | forward + backward | 67.68 ± 0.20 | 67.08 ± 0.20 |
1.0158x | 0.0239 | tie |
| bwd | 250340 | 64 | backward | 36.18 ± 0.01 | 35.26 ± 0.00 | 1.0266x |
0.0066 | faster |
| bwd | 250340 | 128 | forward + backward | 83.66 ± 0.14 | 82.62 ± 0.08
| 1.0141x | 0.0183 | tie |
| bwd | 250340 | 128 | backward | 51.31 ± 0.02 | 50.31 ± 0.02 | 1.0196x
| 0.0049 | faster |
| bwd | 250340 | 192 | forward + backward | 125.34 ± 0.03 | 123.75 ±
0.11 | 1.0137x | 0.0091 | faster |
| bwd | 250340 | 192 | backward | 83.88 ± 0.00 | 82.28 ± 0.00 | 1.0195x
| 0.0027 | faster |
| bwd | 250340 | 256 | forward + backward | 134.12 ± 0.04 | 132.26 ±
0.09 | 1.0143x | 0.0095 | faster |
| bwd | 250340 | 256 | backward | 84.45 ± 0.03 | 82.89 ± 0.00 | 1.0190x
| 0.0028 | faster |
| bwd | 250340 | 384 | forward + backward | 242.49 ± 0.10 | 241.05 ±
0.09 | 1.0060x | 0.0050 | tie |
| bwd | 250340 | 384 | backward | 168.32 ± 0.01 | 166.93 ± 0.00 |
1.0082x | 0.0014 | faster |
| bwd | 250340 | 480 | forward + backward | 271.22 ± 0.04 | 269.96 ±
0.08 | 1.0053x | 0.0034 | tie |
| bwd | 250340 | 480 | backward | 187.09 ± 0.00 | 185.68 ± 0.01 |
1.0073x | 0.0019 | faster |
| bwd | 262144 | 128 | forward + backward | 85.59 ± 0.14 | 84.16 ± 0.12
| 1.0172x | 0.0132 | tie |
| bwd | 262144 | 128 | backward | 52.78 ± 0.05 | 51.45 ± 0.00 | 1.0255x
| 0.0066 | faster |
| bwd | 262144 | 256 | forward + backward | 139.99 ± 0.12 | 138.19 ±
0.16 | 1.0130x | 0.0128 | tie |
| bwd | 262144 | 256 | backward | 87.67 ± 0.01 | 86.49 ± 0.02 | 1.0138x
| 0.0025 | faster |


### GB300 (sm_103a)

| route | S | C | timed | baseline us | new us | speedup (median paired
ratio) | A/A noise q | result |
|---|---|---|---|---|---|---|---|---|
| bwd | 239718 | 512 | forward + backward | 206.49 ± 0.11 | 204.05 ±
0.09 | 1.0115x | 0.0020 | faster |
| bwd | 239718 | 512 | backward | 130.52 ± 0.01 | 128.36 ± 0.00 |
1.0168x | 0.0016 | faster |
| bwd | 245028 | 512 | forward + backward | 212.32 ± 0.06 | 210.12 ±
0.00 | 1.0107x | 0.0023 | faster |
| bwd | 245028 | 512 | backward | 134.90 ± 0.00 | 132.75 ± 0.03 |
1.0165x | 0.0022 | faster |
| bwd | 249866 | 512 | forward + backward | 216.18 ± 0.07 | 213.59 ±
0.06 | 1.0119x | 0.0020 | faster |
| bwd | 249866 | 512 | backward | 137.10 ± 0.02 | 134.75 ± 0.01 |
1.0179x | 0.0026 | faster |
| bwd | 250340 | 64 | forward + backward | 103.82 ± 0.35 | 103.10 ± 0.13
| 1.0061x | 0.0146 | tie |
| bwd | 250340 | 64 | backward | 32.30 ± 0.01 | 32.01 ± 0.01 | 1.0085x |
0.0051 | faster |
| bwd | 250340 | 128 | forward + backward | 120.11 ± 0.42 | 119.75 ±
0.14 | 1.0039x | 0.0183 | tie |
| bwd | 250340 | 128 | backward | 47.01 ± 0.01 | 46.57 ± 0.02 | 1.0101x
| 0.0115 | tie |
| bwd | 250340 | 192 | forward + backward | 144.90 ± 0.02 | 143.91 ±
0.22 | 1.0075x | 0.0125 | tie |
| bwd | 250340 | 192 | backward | 74.31 ± 0.00 | 73.68 ± 0.00 | 1.0087x
| 0.0017 | faster |
| bwd | 250340 | 256 | forward + backward | 149.75 ± 0.30 | 148.93 ±
0.01 | 1.0053x | 0.0154 | tie |
| bwd | 250340 | 256 | backward | 76.85 ± 0.04 | 75.98 ± 0.01 | 1.0132x
| 0.0039 | faster |
| bwd | 250340 | 384 | forward + backward | 225.76 ± 0.15 | 224.32 ±
0.21 | 1.0058x | 0.0061 | tie |
| bwd | 250340 | 384 | backward | 154.69 ± 0.02 | 153.63 ± 0.02 |
1.0069x | 0.0011 | faster |
| bwd | 250340 | 480 | forward + backward | 245.34 ± 0.19 | 243.45 ±
0.03 | 1.0078x | 0.0053 | faster |
| bwd | 250340 | 480 | backward | 167.06 ± 0.00 | 165.48 ± 0.01 |
1.0095x | 0.0012 | faster |
| bwd | 250340 | 512 | forward + backward | 215.08 ± 0.01 | 212.60 ±
0.02 | 1.0114x | 0.0016 | faster |
| bwd | 250340 | 512 | backward | 136.06 ± 0.00 | 133.77 ± 0.01 |
1.0169x | 0.0021 | faster |
| bwd | 258574 | 512 | forward + backward | 220.57 ± 0.04 | 217.93 ±
0.04 | 1.0118x | 0.0023 | faster |
| bwd | 258574 | 512 | backward | 139.26 ± 0.01 | 136.88 ± 0.00 |
1.0175x | 0.0020 | faster |
| bwd | 259042 | 512 | forward + backward | 221.35 ± 0.07 | 218.82 ±
0.11 | 1.0118x | 0.0025 | faster |
| bwd | 259042 | 512 | backward | 139.98 ± 0.00 | 137.63 ± 0.00 |
1.0172x | 0.0022 | faster |
| bwd | 259584 | 512 | forward + backward | 222.17 ± 0.02 | 219.44 ±
0.00 | 1.0123x | 0.0021 | faster |
| bwd | 259584 | 512 | backward | 140.62 ± 0.02 | 138.10 ± 0.01 |
1.0181x | 0.0025 | faster |
| bwd | 261393 | 512 | forward + backward | 224.04 ± 0.01 | 221.46 ±
0.06 | 1.0113x | 0.0022 | faster |
| bwd | 261393 | 512 | backward | 141.79 ± 0.02 | 139.56 ± 0.03 |
1.0161x | 0.0021 | faster |
| bwd | 262144 | 128 | forward + backward | 119.97 ± 0.02 | 119.57 ±
0.09 | 1.0046x | 0.0242 | tie |
| bwd | 262144 | 128 | backward | 47.66 ± 0.01 | 47.20 ± 0.00 | 1.0091x
| 0.0065 | faster |
| bwd | 262144 | 256 | forward + backward | 152.83 ± 0.03 | 152.28 ±
0.06 | 1.0072x | 0.0130 | tie |
| bwd | 262144 | 256 | backward | 79.46 ± 0.02 | 78.72 ± 0.00 | 1.0093x
| 0.0038 | faster |
| bwd_dt | 250340 | 64 | forward + backward | 103.70 ± 0.24 | 103.16 ±
0.08 | 1.0046x | 0.0163 | tie |
| bwd_dt | 250340 | 64 | backward | 33.20 ± 0.02 | 32.07 ± 0.02 |
1.0347x | 0.0073 | faster |
| bwd_dt | 250340 | 128 | forward + backward | 122.15 ± 0.44 | 121.18 ±
0.06 | 1.0067x | 0.0208 | tie |
| bwd_dt | 250340 | 128 | backward | 50.04 ± 0.00 | 48.55 ± 0.00 |
1.0311x | 0.0043 | faster |
| bwd_dt | 250340 | 192 | forward + backward | 149.48 ± 0.32 | 147.08 ±
0.11 | 1.0147x | 0.0137 | tie |
| bwd_dt | 250340 | 192 | backward | 78.96 ± 0.00 | 76.72 ± 0.00 |
1.0292x | 0.0019 | faster |
| bwd_dt | 250340 | 256 | forward + backward | 152.26 ± 0.09 | 150.61 ±
0.07 | 1.0092x | 0.0116 | tie |
| bwd_dt | 250340 | 256 | backward | 82.01 ± 0.02 | 79.24 ± 0.02 |
1.0348x | 0.0022 | faster |
| bwd_dt | 250340 | 384 | forward + backward | 237.00 ± 0.10 | 232.51 ±
0.20 | 1.0192x | 0.0063 | faster |
| bwd_dt | 250340 | 384 | backward | 165.98 ± 0.00 | 160.86 ± 0.01 |
1.0322x | 0.0009 | faster |
| bwd_dt | 250340 | 480 | forward + backward | 253.65 ± 0.01 | 248.68 ±
0.03 | 1.0194x | 0.0035 | faster |
| bwd_dt | 250340 | 480 | backward | 177.07 ± 0.01 | 171.81 ± 0.00 |
1.0306x | 0.0009 | faster |
| bwd_dt | 262144 | 128 | forward + backward | 122.24 ± 0.12 | 121.06 ±
0.25 | 1.0052x | 0.0201 | tie |
| bwd_dt | 262144 | 128 | backward | 49.93 ± 0.02 | 48.66 ± 0.01 |
1.0275x | 0.0046 | faster |
| bwd_dt | 262144 | 256 | forward + backward | 155.04 ± 0.23 | 152.44 ±
0.12 | 1.0138x | 0.0113 | faster |
| bwd_dt | 262144 | 256 | backward | 84.54 ± 0.02 | 81.72 ± 0.01 |
1.0342x | 0.0036 | faster |


### R200 (sm_107a, 212 SMs)

| route | S | C | timed | baseline us | new us | speedup (median paired
ratio) | A/A noise q | result |
|---|---|---|---|---|---|---|---|---|
| bwd | 239718 | 512 | forward + backward | 132.49 ± 0.01 | 130.77 ±
0.00 | 1.0132x | 0.0026 | faster |
| bwd | 239718 | 512 | backward | 85.47 ± 0.02 | 83.84 ± 0.00 | 1.0187x
| 0.0023 | faster |
| bwd | 245028 | 512 | forward + backward | 133.17 ± 0.00 | 131.41 ±
0.02 | 1.0134x | 0.0013 | faster |
| bwd | 245028 | 512 | backward | 85.34 ± 0.00 | 83.74 ± 0.00 | 1.0191x
| 0.0015 | faster |
| bwd | 249866 | 512 | forward + backward | 139.90 ± 0.00 | 138.28 ±
0.02 | 1.0122x | 0.0017 | faster |
| bwd | 249866 | 512 | backward | 91.53 ± 0.02 | 90.04 ± 0.00 | 1.0173x
| 0.0020 | faster |
| bwd | 250340 | 512 | forward + backward | 135.55 ± 0.01 | 134.02 ±
0.00 | 1.0116x | 0.0018 | faster |
| bwd | 250340 | 512 | backward | 87.59 ± 0.01 | 86.05 ± 0.01 | 1.0180x
| 0.0022 | faster |
| bwd | 250340 | 1024 | forward + backward | 251.55 ± 0.04 | 246.44 ±
0.02 | 1.0208x | 0.0026 | faster |
| bwd | 250340 | 1024 | backward | 161.33 ± 0.03 | 156.03 ± 0.02 |
1.0339x | 0.0024 | faster |
| bwd | 250340 | 1160 | forward + backward | 320.46 ± 0.10 | 319.29 ±
0.01 | 1.0037x | 0.0020 | faster |
| bwd | 250340 | 1160 | backward | 199.85 ± 0.02 | 198.39 ± 0.05 |
1.0074x | 0.0047 | faster |
| bwd | 250340 | 1280 | forward + backward | 313.75 ± 0.03 | 312.07 ±
0.00 | 1.0055x | 0.0020 | faster |
| bwd | 250340 | 1280 | backward | 197.89 ± 0.02 | 196.49 ± 0.12 |
1.0070x | 0.0034 | faster |
| bwd | 250340 | 1344 | forward + backward | 358.77 ± 0.08 | 356.02 ±
0.03 | 1.0077x | 0.0022 | faster |
| bwd | 250340 | 1344 | backward | 233.71 ± 0.06 | 230.93 ± 0.10 |
1.0118x | 0.0029 | faster |
| bwd | 250340 | 1536 | forward + backward | 369.05 ± 0.09 | 366.60 ±
0.02 | 1.0068x | 0.0019 | faster |
| bwd | 250340 | 1536 | backward | 232.65 ± 0.04 | 230.44 ± 0.06 |
1.0094x | 0.0029 | faster |
| bwd | 250340 | 2048 | forward + backward | 483.89 ± 0.02 | 469.82 ±
0.07 | 1.0300x | 0.0014 | faster |
| bwd | 250340 | 2048 | backward | 302.27 ± 0.02 | 288.63 ± 0.00 |
1.0475x | 0.0023 | faster |
| bwd | 250340 | 2560 | forward + backward | 590.95 ± 0.04 | 573.21 ±
0.04 | 1.0310x | 0.0012 | faster |
| bwd | 250340 | 2560 | backward | 372.88 ± 0.00 | 355.54 ± 0.00 |
1.0486x | 0.0016 | faster |
| bwd | 250340 | 4096 | forward + backward | 924.62 ± 0.10 | 896.94 ±
0.01 | 1.0308x | 0.0007 | faster |
| bwd | 250340 | 4096 | backward | 579.66 ± 0.07 | 552.35 ± 0.01 |
1.0494x | 0.0016 | faster |
| bwd | 250340 | 8192 | forward + backward | 1814.94 ± 0.03 | 1760.75 ±
0.03 | 1.0309x | 0.0004 | faster |
| bwd | 250340 | 8192 | backward | 1141.34 ± 0.03 | 1087.59 ± 0.04 |
1.0495x | 0.0010 | faster |
| bwd | 258574 | 512 | forward + backward | 139.22 ± 0.01 | 137.20 ±
0.01 | 1.0155x | 0.0020 | faster |
| bwd | 258574 | 512 | backward | 90.32 ± 0.03 | 87.90 ± 0.02 | 1.0279x
| 0.0035 | faster |
| bwd | 259042 | 512 | forward + backward | 139.27 ± 0.02 | 137.90 ±
0.01 | 1.0102x | 0.0014 | faster |
| bwd | 259042 | 512 | backward | 89.65 ± 0.01 | 88.29 ± 0.01 | 1.0150x
| 0.0022 | faster |
| bwd | 259584 | 512 | forward + backward | 140.94 ± 0.07 | 139.21 ±
0.01 | 1.0128x | 0.0038 | faster |
| bwd | 259584 | 512 | backward | 91.52 ± 0.02 | 89.97 ± 0.02 | 1.0171x
| 0.0041 | faster |
| bwd | 261393 | 512 | forward + backward | 141.00 ± 0.02 | 139.25 ±
0.02 | 1.0126x | 0.0015 | faster |
| bwd | 261393 | 512 | backward | 91.53 ± 0.03 | 89.87 ± 0.00 | 1.0188x
| 0.0019 | faster |
| bwd | 262144 | 256 | forward + backward | 81.89 ± 0.03 | 81.17 ± 0.04
| 1.0089x | 0.0049 | faster |
| bwd | 262144 | 256 | backward | 51.44 ± 0.01 | 50.82 ± 0.00 | 1.0126x
| 0.0038 | faster |
| bwd | 262144 | 1160 | forward + backward | 336.04 ± 0.03 | 334.89 ±
0.05 | 1.0033x | 0.0024 | faster |
| bwd | 262144 | 1160 | backward | 210.72 ± 0.04 | 209.93 ± 0.02 |
1.0035x | 0.0029 | faster |
| bwd | 262144 | 1280 | forward + backward | 328.92 ± 0.00 | 326.57 ±
0.02 | 1.0072x | 0.0019 | faster |
| bwd | 262144 | 1280 | backward | 208.27 ± 0.08 | 206.49 ± 0.04 |
1.0089x | 0.0040 | faster |
| bwd | 262144 | 1536 | forward + backward | 386.22 ± 0.16 | 383.83 ±
0.08 | 1.0062x | 0.0022 | faster |
| bwd | 262144 | 1536 | backward | 244.72 ± 0.03 | 242.15 ± 0.12 |
1.0105x | 0.0029 | faster |
| bwd_bias | 250340 | 1024 | forward + backward | 264.91 ± 0.07 | 260.91
± 0.01 | 1.0155x | 0.0020 | faster |
| bwd_bias | 250340 | 1024 | backward | 171.32 ± 0.01 | 167.32 ± 0.01 |
1.0239x | 0.0020 | faster |
| bwd_bias | 250340 | 1160 | forward + backward | 345.12 ± 0.03 | 340.89
± 0.02 | 1.0124x | 0.0022 | faster |
| bwd_bias | 250340 | 1160 | backward | 219.69 ± 0.01 | 214.92 ± 0.03 |
1.0232x | 0.0050 | faster |
| bwd_bias | 250340 | 1280 | forward + backward | 339.82 ± 0.08 | 335.01
± 0.08 | 1.0146x | 0.0033 | faster |
| bwd_bias | 250340 | 1280 | backward | 219.27 ± 0.02 | 213.91 ± 0.05 |
1.0251x | 0.0045 | faster |
| bwd_bias | 250340 | 1344 | forward + backward | 386.81 ± 0.00 | 382.36
± 0.02 | 1.0116x | 0.0017 | faster |
| bwd_bias | 250340 | 1344 | backward | 258.75 ± 0.11 | 253.65 ± 0.08 |
1.0201x | 0.0044 | faster |
| bwd_bias | 250340 | 1536 | forward + backward | 397.43 ± 0.11 | 392.64
± 0.01 | 1.0119x | 0.0026 | faster |
| bwd_bias | 250340 | 1536 | backward | 257.49 ± 0.04 | 252.40 ± 0.03 |
1.0203x | 0.0040 | faster |
| bwd_bias | 250340 | 2048 | forward + backward | 521.28 ± 0.08 | 508.07
± 0.02 | 1.0260x | 0.0016 | faster |
| bwd_bias | 250340 | 2048 | backward | 340.36 ± 0.10 | 327.28 ± 0.05 |
1.0401x | 0.0021 | faster |
| bwd_bias | 250340 | 2560 | forward + backward | 631.77 ± 0.00 | 623.19
± 0.01 | 1.0138x | 0.0015 | faster |
| bwd_bias | 250340 | 2560 | backward | 409.68 ± 0.04 | 400.70 ± 0.09 |
1.0225x | 0.0020 | faster |
| bwd_bias | 250340 | 4096 | forward + backward | 978.94 ± 0.10 | 963.54
± 0.10 | 1.0160x | 0.0011 | faster |
| bwd_bias | 250340 | 4096 | backward | 632.98 ± 0.02 | 616.71 ± 0.08 |
1.0265x | 0.0014 | faster |
| bwd_bias | 250340 | 8192 | forward + backward | 1915.18 ± 0.15 |
1886.05 ± 0.02 | 1.0154x | 0.0005 | faster |
| bwd_bias | 250340 | 8192 | backward | 1239.36 ± 0.03 | 1210.06 ± 0.07
| 1.0242x | 0.0006 | faster |
| bwd_bias | 262144 | 1160 | forward + backward | 363.82 ± 0.10 | 357.08
± 0.04 | 1.0189x | 0.0018 | faster |
| bwd_bias | 262144 | 1160 | backward | 234.90 ± 0.11 | 228.45 ± 0.02 |
1.0280x | 0.0037 | faster |
| bwd_bias | 262144 | 1280 | forward + backward | 358.92 ± 0.10 | 350.73
± 0.06 | 1.0233x | 0.0025 | faster |
| bwd_bias | 262144 | 1280 | backward | 234.44 ± 0.11 | 226.17 ± 0.03 |
1.0362x | 0.0042 | faster |
| bwd_bias | 262144 | 1536 | forward + backward | 418.00 ± 0.09 | 410.12
± 0.03 | 1.0192x | 0.0023 | faster |
| bwd_bias | 262144 | 1536 | backward | 272.19 ± 0.09 | 264.22 ± 0.03 |
1.0302x | 0.0028 | faster |
| bwd_bias_bf16 | 250340 | 1024 | forward + backward | 264.74 ± 0.02 |
260.62 ± 0.04 | 1.0157x | 0.0020 | faster |
| bwd_bias_bf16 | 250340 | 1024 | backward | 171.16 ± 0.01 | 167.21 ±
0.01 | 1.0236x | 0.0021 | faster |
| bwd_bias_bf16 | 250340 | 1160 | forward + backward | 344.62 ± 0.01 |
340.37 ± 0.05 | 1.0124x | 0.0013 | faster |
| bwd_bias_bf16 | 250340 | 1160 | backward | 220.05 ± 0.00 | 215.42 ±
0.09 | 1.0216x | 0.0060 | faster |
| bwd_bias_bf16 | 250340 | 1280 | forward + backward | 339.29 ± 0.01 |
334.40 ± 0.02 | 1.0147x | 0.0026 | faster |
| bwd_bias_bf16 | 250340 | 1280 | backward | 219.36 ± 0.09 | 214.11 ±
0.27 | 1.0240x | 0.0065 | faster |
| bwd_bias_bf16 | 250340 | 1344 | forward + backward | 386.20 ± 0.06 |
381.38 ± 0.05 | 1.0124x | 0.0020 | faster |
| bwd_bias_bf16 | 250340 | 1344 | backward | 259.16 ± 0.03 | 254.42 ±
0.14 | 1.0183x | 0.0049 | faster |
| bwd_bias_bf16 | 250340 | 1536 | forward + backward | 397.09 ± 0.15 |
392.34 ± 0.04 | 1.0121x | 0.0025 | faster |
| bwd_bias_bf16 | 250340 | 1536 | backward | 257.73 ± 0.04 | 252.79 ±
0.12 | 1.0195x | 0.0042 | faster |
| bwd_bias_bf16 | 250340 | 2048 | forward + backward | 520.40 ± 0.03 |
507.10 ± 0.04 | 1.0261x | 0.0029 | faster |
| bwd_bias_bf16 | 250340 | 2048 | backward | 340.20 ± 0.03 | 327.36 ±
0.10 | 1.0393x | 0.0022 | faster |
| bwd_bias_bf16 | 250340 | 2560 | forward + backward | 631.59 ± 0.02 |
622.96 ± 0.05 | 1.0139x | 0.0020 | faster |
| bwd_bias_bf16 | 250340 | 2560 | backward | 409.82 ± 0.03 | 400.88 ±
0.09 | 1.0225x | 0.0018 | faster |
| bwd_bias_bf16 | 250340 | 4096 | forward + backward | 977.82 ± 0.02 |
962.54 ± 0.05 | 1.0159x | 0.0007 | faster |
| bwd_bias_bf16 | 250340 | 4096 | backward | 633.06 ± 0.06 | 617.23 ±
0.12 | 1.0257x | 0.0018 | faster |
| bwd_bias_bf16 | 250340 | 8192 | forward + backward | 1914.20 ± 0.03 |
1885.01 ± 0.10 | 1.0155x | 0.0006 | faster |
| bwd_bias_bf16 | 250340 | 8192 | backward | 1239.59 ± 0.10 | 1210.04 ±
0.02 | 1.0245x | 0.0008 | faster |
| bwd_bias_bf16 | 262144 | 1160 | forward + backward | 363.36 ± 0.01 |
356.67 ± 0.09 | 1.0187x | 0.0033 | faster |
| bwd_bias_bf16 | 262144 | 1160 | backward | 235.03 ± 0.04 | 228.55 ±
0.06 | 1.0288x | 0.0043 | faster |
| bwd_bias_bf16 | 262144 | 1280 | forward + backward | 358.54 ± 0.17 |
350.40 ± 0.09 | 1.0229x | 0.0027 | faster |
| bwd_bias_bf16 | 262144 | 1280 | backward | 234.30 ± 0.07 | 226.10 ±
0.05 | 1.0362x | 0.0034 | faster |
| bwd_bias_bf16 | 262144 | 1536 | forward + backward | 417.29 ± 0.05 |
409.57 ± 0.03 | 1.0187x | 0.0019 | faster |
| bwd_bias_bf16 | 262144 | 1536 | backward | 272.61 ± 0.00 | 264.43 ±
0.12 | 1.0308x | 0.0026 | faster |
| bwd_fp32g | 250340 | 1024 | forward + backward | 247.54 ± 0.01 |
245.48 ± 0.07 | 1.0085x | 0.0019 | faster |
| bwd_fp32g | 250340 | 1024 | backward | 157.08 ± 0.00 | 155.08 ± 0.02 |
1.0129x | 0.0033 | faster |
| bwd_fp32g | 250340 | 1160 | forward + backward | 318.71 ± 0.10 |
317.85 ± 0.05 | 1.0028x | 0.0029 | tie |
| bwd_fp32g | 250340 | 1160 | backward | 200.15 ± 0.15 | 199.19 ± 0.10 |
1.0045x | 0.0058 | tie |
| bwd_fp32g | 250340 | 1280 | forward + backward | 311.65 ± 0.14 |
310.27 ± 0.12 | 1.0043x | 0.0033 | faster |
| bwd_fp32g | 250340 | 1280 | backward | 198.15 ± 0.03 | 196.92 ± 0.06 |
1.0066x | 0.0065 | tie |
| bwd_fp32g | 250340 | 1344 | forward + backward | 355.00 ± 0.01 |
353.18 ± 0.01 | 1.0052x | 0.0017 | faster |
| bwd_fp32g | 250340 | 1344 | backward | 231.99 ± 0.05 | 230.62 ± 0.04 |
1.0054x | 0.0039 | faster |
| bwd_fp32g | 250340 | 1536 | forward + backward | 365.75 ± 0.05 |
363.80 ± 0.04 | 1.0057x | 0.0018 | faster |
| bwd_fp32g | 250340 | 1536 | backward | 231.76 ± 0.10 | 230.21 ± 0.06 |
1.0068x | 0.0039 | faster |
| bwd_fp32g | 250340 | 2048 | forward + backward | 478.36 ± 0.01 |
476.73 ± 0.05 | 1.0036x | 0.0015 | faster |
| bwd_fp32g | 250340 | 2048 | backward | 299.75 ± 0.06 | 298.40 ± 0.01 |
1.0044x | 0.0025 | faster |
| bwd_fp32g | 250340 | 2560 | forward + backward | 582.02 ± 0.10 |
578.85 ± 0.06 | 1.0054x | 0.0015 | faster |
| bwd_fp32g | 250340 | 2560 | backward | 366.54 ± 0.04 | 364.08 ± 0.05 |
1.0064x | 0.0022 | faster |
| bwd_fp32g | 250340 | 4096 | forward + backward | 902.90 ± 0.10 |
898.04 ± 0.04 | 1.0054x | 0.0009 | faster |
| bwd_fp32g | 250340 | 4096 | backward | 561.36 ± 0.02 | 557.00 ± 0.02 |
1.0075x | 0.0013 | faster |
| bwd_fp32g | 250340 | 8192 | forward + backward | 1766.08 ± 0.00 |
1756.58 ± 0.03 | 1.0055x | 0.0006 | faster |
| bwd_fp32g | 250340 | 8192 | backward | 1094.95 ± 0.03 | 1085.92 ± 0.02
| 1.0081x | 0.0007 | faster |
| bwd_fp32g | 262144 | 1160 | forward + backward | 335.17 ± 0.24 |
334.85 ± 0.06 | 1.0011x | 0.0039 | tie |
| bwd_fp32g | 262144 | 1160 | backward | 210.51 ± 0.02 | 210.57 ± 0.05 |
0.9994x | 0.0049 | tie |
| bwd_fp32g | 262144 | 1280 | forward + backward | 327.53 ± 0.04 |
325.95 ± 0.00 | 1.0050x | 0.0020 | faster |
| bwd_fp32g | 262144 | 1280 | backward | 207.79 ± 0.06 | 206.47 ± 0.02 |
1.0055x | 0.0045 | tie |
| bwd_fp32g | 262144 | 1536 | forward + backward | 383.75 ± 0.00 |
382.54 ± 0.05 | 1.0035x | 0.0019 | tie |
| bwd_fp32g | 262144 | 1536 | backward | 243.16 ± 0.00 | 242.37 ± 0.03 |
1.0025x | 0.0032 | tie |

The kernel's other Cake variants are the context-parallel KCP package
(`flashinfer.cake_causal_conv1d_det_train_kcp`) and the opt-in
`bwd_grid_mult` backward split, which is already on main; the family
ships on sm_100a, sm_103a and sm_107a.

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-11-02
**监控日期**: 2026-11-01
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4769
- **最后更新**: 2026-11-02T01:07:57Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 1
- **主要提交者**: Aryan Kumar

## AI分析总结

## FastVideo 昨日提交分析（2025年1月）

### 1. 主要更新类型

- **性能优化**：一条提交专注于 DiT 融合算子的更快内核（tier 2）
- **Bug 修复**：一条提交修复了 FA4（Flash Attention 4）变长（varlen）内核中错误传递 `max_seqlen` 参数的问题

### 2. 关键变更点及与项目方向的关系

- **MiniMax H3 内核优化**：为 DiT（Diffusion Transformer）的融合算子提供了可选的"更快内核层级"（faster kernel tier），用户可选择性启用更高性能路径。这直接服务于 FastVideo 作为高效视频生成推理引擎的核心目标——在不损失质量的前提下最大化吞吐和降低延迟。
- **FA4 变长内核修复**：在 Flash Attention 4 的 varlen（variable-length）内核调用中移除了不当的 `max_seqlen` 参数转发。这是一个典型的内核接口对齐问题，可能导致变长序列场景下注意力计算结果不正确或触发运行时异常。

### 3. 对项目的影响和潜在意义

- **性能提升**：MiniMax H3 的优化内核为用户提供了一个性能与兼容性之间的选择空间——opt-in 设计意味着默认行为不变，风险可控。
- **稳定性增强**：FA4 修复消除了在视频生成中常见的变长序列处理场景下的潜在崩溃或精度问题，提升了推理管线的鲁棒性。
- **两条提交均由同一协作者完成**，表明团队内部有专人负责底层内核与硬件适配层的持续维护。

### 4. 值得关注的技术点

- **Opt-in 性能分层策略**：通过可选启用（opt-in）的方式引入更激进的内核实现，是平衡"性能前沿"与"稳定兼容"的成熟工程实践，值得关注其具体设计模式（例如环境变量、配置开关还是 API 参数）。
- **FA4 变长注意力**：视频生成模型的序列长度天然多变（不同分辨率、不同帧数），varlen kernel 是核心路径。移除错误的 `max_seqlen` 转发说明团队正在深入适配 Flash Attention 4 的最新接口变更，体现了对前沿注意力内核的紧跟。
- **DiT 融合算子**：融合算子（fused ops）是降低内核启动开销和内存带宽压力的关键手段，"faster kernel tier" 暗示可能存在多级内核选择机制（如 split-k、不同 tiling 策略等）。

### 5. 对项目发展的综合影响

基于 README，FastVideo 是一个面向高效视频生成推理的开源框架，拥有完善的文档体系（Quick Start、Cookbook）和活跃的社区协作机制（Weekly Dev Meeting、Discord/Slack）。这两条提交虽然体量较小，但体现了项目在两个关键方向上的持续深耕：

- **硬件性能极致化**：通过内核级优化不断逼近硬件性能上限，这是与同类推理框架竞争的核心壁垒。
- **工程质量与稳定性**：及时修复底层内核调用错误，确保生产环境可靠性。

总体而言，这类提交是项目从"功能可用"向"生产级高性能"演进的典型表现，对于吸引对推理性能敏感的用户（如企业部署、大规模视频生成服务）具有重要意义。

## 详细提交记录

### [0d1244a](https://github.com/hao-ai-lab/FastVideo/commit/0d1244a8699d3f2c2bd290e3bb08deed6b1e6e85)

- **作者**: Aryan Kumar
- **时间**: 2026-11-01T23:22:09Z
- **提交信息**: [perf] MiniMax H3: opt-in faster kernel tier for the DiT fused ops (#2042)

Co-authored-by: Aryan Kumar <aryan5v@users.noreply.github.com>

### [18b2a35](https://github.com/hao-ai-lab/FastVideo/commit/18b2a3510637a1941c57e32b976e55ea511eea8f)

- **作者**: Aryan Kumar
- **时间**: 2026-11-01T23:21:38Z
- **提交信息**: [bugfix] FA4: stop forwarding max_seqlen to the varlen kernel (#2043)

Co-authored-by: Aryan Kumar <aryan5v@users.noreply.github.com>

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-11-02
**监控日期**: 2026-11-01
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34845
- **最后更新**: 2026-11-02T00:47:11Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-11-02
**监控日期**: 2026-11-01
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 432
- **最后更新**: 2026-10-19T05:38:59Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-11-02
**监控日期**: 2026-11-01
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13334
- **最后更新**: 2026-11-01T22:45:09Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-11-02
**监控日期**: 2026-11-01
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 38350
- **最后更新**: 2026-11-02T01:35:03Z

## 提交统计

- **昨日提交总数**: 29
- **提交者数量**: 16
- **主要提交者**: Yanbin Jiang, em-dreyer, Ke Bao

## AI分析总结

## sgl-project/sglang 昨日提交分析（第1/1批，共29条）

### 1. 主要更新类型分布
- **Bug修复**：约12条，占比最高，集中在扩散（diffusion）、分组解耦（disaggregation）与调度器模块
- **性能优化**：约7条，涵盖扩散推理、AMD GPU内核、注意力机制
- **功能新增**：约7条，以AMD gfx950支持和分布式特性为主
- **重构/测试/CI**：约4条，涉及调度器重构、LoRA测试简化、CI稳定性

### 2. 关键变更点与项目方向的关系
- **扩散模型支持持续深化**：动态批处理下的轨迹/条件保持、LoRA缓存LRU淘汰、Wan-Animate-2去噪加速（FA3+FP8）、LTX-2预热修复等，表明SGLang正从LLM推理平台扩展为多模态/扩散模型统一推理引擎，与README中"LLM与多模态模型快速推理"的定位一致。
- **AMD gfx950硬件生态大幅投入**：约5条提交集中于gfx950的MoE、路由GEMV、块FP8 GEMM、稀疏注意力、NVFP4 KV、分布式快速all-reduce及ROCm镜像构建，显示项目正积极拓展AMD Instinct加速卡的生产级支持。
- **分组解耦（Prefill-Decode分离）成熟化**：KV写入linker跳页、bootstrap服务器初始化顺序、死节点连接清理、断点续传prefill CUDA图等，体现PD分离架构走向稳定。
- **调度器稳定性加固**：早结果处理时机、在途步骤计数统一钩子、测试缓存修复，属于内核级可靠性建设。

### 3. 对项目的影响与潜在意义
- 扩散模型相关修复与优化提升了SGLang在视频/图像生成推理场景的可靠性与吞吐，扩大了用户面。
- AMD支持的集中落地降低了对NVIDIA的硬件依赖，增强了部署灵活性，有利于企业级多硬件落地。
- PD分离与调度器修复直接改善大规模分布式推理的稳定性，是高并发服务场景的关键基础。

### 4. 值得关注的技术点
- **Wan-Animate-2 1.7倍去噪加速**：结合FA3上下文内注意力与可选FP8参考K/V，是扩散推理性能的显著突破。
- **gfx950 JIT快速all-reduce（TP4）**：利用编译期定制通信内核降低延迟，思路值得其他后端借鉴。
- **DeepSeek-V4.1 dense indexer日志分块对齐整SM波次**：极致的GPU利用率微优化，体现团队对内核级性能的深耕。
- **Triton softmax top-k路由统一到Qwen3-Next**：以单一Triton实现替代专用内核，降低维护成本。
- **调度器在途步骤计数重构**：为后续更复杂的调度策略（如投机解码、混合批）铺路。

### 5. 对项目发展的整体影响
这批提交反映出SGLang当前的三条主线：一是**多模态/扩散推理能力的快速补齐**，使其真正兑现README宣称的多模态目标；二是**AMD硬件生态的系统性建设**，为跨平台部署铺平道路；三是**分布式与调度内核的稳定性打磨**，支撑生产级高并发服务。三者共同推动SGLang从"快速LLM推理引擎"演进为"覆盖多硬件、多模态、大规模部署的统一推理基础设施"。大量Claude/LLM辅助协作（Co-authored-by）的出现也表明AI辅助开发已深度融入该项目的工程流程。

## 详细提交记录

### [38d9e4a](https://github.com/sgl-project/sglang/commit/38d9e4a3fe4a493b0ae468477a274e83defda81a)

- **作者**: Avaya Aggarwal
- **时间**: 2026-11-01T23:59:04Z
- **提交信息**: [Fix] diffusion: Keep each request's rollout trajectory and conditioning under dynamic batching (#46274)

### [e8bf40b](https://github.com/sgl-project/sglang/commit/e8bf40b8eed8605e9e006857cb8562a076fa4bf7)

- **作者**: Avaya Aggarwal
- **时间**: 2026-11-01T23:51:47Z
- **提交信息**: [Feat] diffusion: LRU eviction for LoRA merge cache (#47605)

### [1367b51](https://github.com/sgl-project/sglang/commit/1367b51139c5041fb8e4fed5c05269a1595ddfac)

- **作者**: pratik naik
- **时间**: 2026-11-01T23:43:31Z
- **提交信息**: [Test] model_loader: Cover unindexed Mistral shard filtering (#47601)

Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>

### [c3654cd](https://github.com/sgl-project/sglang/commit/c3654cd93bd8d68baca4caf6c22b1969e26c159d)

- **作者**: Xinyi Song
- **时间**: 2026-11-01T23:33:00Z
- **提交信息**: [Chore] [AMD] docker: Build uTLX into the gfx950 rocm10 images (#46883)

### [e37c1fb](https://github.com/sgl-project/sglang/commit/e37c1fb020acec0efa386f83d35d2a03d887132a)

- **作者**: Kevin Mi
- **时间**: 2026-11-01T23:16:08Z
- **提交信息**: [Feat] [AMD] minimax: gfx950 MoE, router GEMV, block-fp8 GEMM and fp8 producer kernels (#46691)

Co-authored-by: Kevin Mi <kevin.mi@radixark.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [fdf2266](https://github.com/sgl-project/sglang/commit/fdf2266c8861597690e978e7346d140856220689)

- **作者**: Kevin Mi
- **时间**: 2026-11-01T23:15:42Z
- **提交信息**: [Feat] [AMD] distributed: JIT quick all-reduce for TP4 on gfx950 (#46692)

Co-authored-by: Kevin Mi <kevin.mi@radixark.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [9431d2c](https://github.com/sgl-project/sglang/commit/9431d2caf603351f4a7087a87a8317f0b0f88f1f)

- **作者**: Avaya Aggarwal
- **时间**: 2026-11-01T22:59:56Z
- **提交信息**: [Fix] diffusion: LoRA alpha reload, auto-mode skip, critic coverage (#46255)

### [03f9054](https://github.com/sgl-project/sglang/commit/03f90543787cb4ff35892054d350cee44193aca1)

- **作者**: Kevin Mi
- **时间**: 2026-11-01T22:36:00Z
- **提交信息**: [Feat] [AMD] minimax: gfx950 sparse attention, NVFP4 KV and DSpark verify kernels (#46690)

Co-authored-by: Kevin Mi <kevin.mi@radixark.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [240f2a0](https://github.com/sgl-project/sglang/commit/240f2a0a649c2359224216fed3daf065a6685efe)

- **作者**: Ziyi Xu
- **时间**: 2026-11-01T22:04:27Z
- **提交信息**: [Fix] disagg: Give the decode queue test scheduler a tree_cache (#47758)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [1c0dc02](https://github.com/sgl-project/sglang/commit/1c0dc0293d4cce8d13872080b2a20936dffb2232)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-01T21:54:37Z
- **提交信息**: [Fix] scheduler: Decide early result processing before scheduling the next batch (#47716)

### [cdc2f7d](https://github.com/sgl-project/sglang/commit/cdc2f7d1b21dece2421522bc50d5da1e591b27a5)

- **作者**: em-dreyer
- **时间**: 2026-11-01T21:50:21Z
- **提交信息**: [CI] nightly: Disable the MiniMax-M3.1-Flash H200 test while it times out (#47789)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [d3bf0b4](https://github.com/sgl-project/sglang/commit/d3bf0b4e52115f87ac41b6bca51915e9dc6baab2)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-01T21:49:37Z
- **提交信息**: [Refactor] scheduler: Route every step launch through one hook and count in-flight steps (#43900)

### [6dda2f0](https://github.com/sgl-project/sglang/commit/6dda2f02f775637b405ad19f4590dedf7b9c7eec)

- **作者**: Mick
- **时间**: 2026-11-01T21:49:21Z
- **提交信息**: [Fix] tests: Initialize DCP replay backend capability (#47736)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [a52ee80](https://github.com/sgl-project/sglang/commit/a52ee805c88ea4326335fb53b0aec59ba9e03304)

- **作者**: Avaya Aggarwal
- **时间**: 2026-11-01T20:22:58Z
- **提交信息**: [Perf] diffusion: opt-in Wan UMT5 padding trim (SGLANG_DIFFUSION_WAN_TEXT_PADDING) (#46328)

### [b50d439](https://github.com/sgl-project/sglang/commit/b50d4394945d3dcacea05ee4afd334a9b225cbdc)

- **作者**: Eric.Chin.AMD
- **时间**: 2026-11-01T19:17:08Z
- **提交信息**: [Perf] [AMD] dsa: Replicate the DCP query projection on the owned route (#47180)

Co-authored-by: Thomas Wang <thomawan@amd.com>

### [0f93be7](https://github.com/sgl-project/sglang/commit/0f93be7b654d6a208676d060deb995af5df8f7c1)

- **作者**: Ke Bao
- **时间**: 2026-11-01T17:44:38Z
- **提交信息**: [Refactor] memory-pool: Build draft sidecar host pools from buffer info (#40914)

### [e298298](https://github.com/sgl-project/sglang/commit/e2982985110fb432fd8ddba5f0147a5004fd03ab)

- **作者**: Mick
- **时间**: 2026-11-01T14:21:05Z
- **提交信息**: [Fix] diffusion/bcg: Warm up LTX-2 two-stage at the output resolution (#47474)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Sonnet 5.5 <noreply@anthropic.com>

### [f171859](https://github.com/sgl-project/sglang/commit/f171859219b54e1dad45dda60028034490836974)

- **作者**: Ziyi Xu
- **时间**: 2026-11-01T13:48:29Z
- **提交信息**: [Perf] attention: Round the DeepSeek-V4.1 dense indexer logits tiles to whole SM waves (#47684)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [e232ebf](https://github.com/sgl-project/sglang/commit/e232ebf6b0b7eeb5a784d1b9cc2a108d93191bd5)

- **作者**: Yang, Chenyi
- **时间**: 2026-11-01T13:28:16Z
- **提交信息**: [Perf] [AMD] moe/topk: Use the Triton softmax top-k router for Qwen3-Next (hidden 2048) (#47236)

Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [cb0a7a9](https://github.com/sgl-project/sglang/commit/cb0a7a953fa6b8409b67959d445c95c802e50c14)

- **作者**: Shuwen Wang
- **时间**: 2026-11-01T12:52:15Z
- **提交信息**: [Feat] disagg: Write PD decode KV to the linker and skip pages the prefill already stored (#46395)

### [4ffc9e1](https://github.com/sgl-project/sglang/commit/4ffc9e1b7df1e8ec2bea9e68c2dd355606cbe4d3)

- **作者**: Zeta
- **时间**: 2026-11-01T12:26:31Z
- **提交信息**: [Fix] diffusion: Fail fast on offline runtime failures (#47488)

Co-authored-by: Zeta <233192986+Zeta-li@users.noreply.github.com>
Co-authored-by: BBuf <35585791+BBuf@users.noreply.github.com>

### [c757c4b](https://github.com/sgl-project/sglang/commit/c757c4bb7c55d1eb69fdb2bdc6e6fb8507acb7a0)

- **作者**: Shangming Cai
- **时间**: 2026-11-01T09:29:30Z
- **提交信息**: [Fix] kv_events: Offset ipc endpoints per DP rank and finish shutdown when the queue is full (#47732)

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [4aaa899](https://github.com/sgl-project/sglang/commit/4aaa8997af8cf3415c2b7f90b1e0804b9bf5585b)

- **作者**: Yanbin Jiang
- **时间**: 2026-11-01T09:24:08Z
- **提交信息**: [CI] lora: Simplify LoRA tests and add a lora rerun group (#45981)

### [1ad0149](https://github.com/sgl-project/sglang/commit/1ad0149814bfbe0cdcc22fca3d757dd23d0fbe11)

- **作者**: Avaya Aggarwal
- **时间**: 2026-11-01T08:56:45Z
- **提交信息**: [Perf] diffusion: Nomas camera attention reads each frame's value directly when camera_chunk_size is 1 (#47686)

### [43881a7](https://github.com/sgl-project/sglang/commit/43881a719e42165ff987fb0273a6bf12eaeb7662)

- **作者**: Shangming Cai
- **时间**: 2026-11-01T08:17:37Z
- **提交信息**: [Fix] disaggregation: Call finalize_bootstrap outside the assert statement (#47727)

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [928e285](https://github.com/sgl-project/sglang/commit/928e285bc10fc4119277e73ee2d3d29b6412bec6)

- **作者**: Kurt Shuster
- **时间**: 2026-11-01T08:09:10Z
- **提交信息**: [Feat] dcp: Support breakable prefill CUDA graphs under decode context parallelism (#38943)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [76066d6](https://github.com/sgl-project/sglang/commit/76066d6908411bf9afcd740cfac61fdf0d5d8050)

- **作者**: Shangming Cai
- **时间**: 2026-11-01T07:57:51Z
- **提交信息**: [Fix] disaggregation: Initialize the bootstrap server loop and runner before the server thread starts (#47725)

### [3edea93](https://github.com/sgl-project/sglang/commit/3edea93cbc0d857026253df0535a4d89791032a3)

- **作者**: Shangming Cai
- **时间**: 2026-11-01T07:22:12Z
- **提交信息**: [Fix] disaggregation: Match the whole bootstrap address when evicting a dead prefill's connections (#47704)

### [4f45b15](https://github.com/sgl-project/sglang/commit/4f45b15e74effb079dc998ed16d31c2956a0ec15)

- **作者**: Avaya Aggarwal
- **时间**: 2026-11-01T07:17:23Z
- **提交信息**: [Perf] diffusion: Wan-Animate-2 1.7x faster denoising via exact FA3 in-context attention, opt-in FP8 reference K/V (#47121)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-11-02
**监控日期**: 2026-11-01
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for 100+ DiTs.
- **语言**: Python
- **星标数**: 1297
- **最后更新**: 2026-11-01T14:32:31Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

## 提交分析：vipshop/cache-dit 昨日提交（1/1 批）

### 1. 主要更新类型
**文档更新**。该提交（`eafa114`，PR #1208）仅涉及 `OVERVIEW.md` 的修改，无代码、功能或性能层面的变更。

### 2. 关键变更点及与项目方向的关系
- **按"社区价值"与"缓存适配度"对待支持模型进行排序**：这是本次提交的核心改动。cache-dit 作为面向 DiT（Diffusion Transformer）的推理引擎，其竞争力在于对各类 DiT 模型的 Cache、并行、量化和 CPU offload 支持。以"缓存适配度"为排序维度，直接呼应了引擎的核心卖点——哪些模型最能从该框架的缓存机制中获益。
- 该排序方式将项目资源与社区需求对齐，明确了后续优先开发支持的模型顺序，属于路线图性质的文档梳理。

### 3. 对项目的影响和潜在意义
- **短期影响**：为贡献者和用户提供了清晰的模型支持优先级参考，降低社区参与的决策成本，有助于吸引更多针对高优先级模型的 PR。
- **长期意义**：建立了"社区价值 + 技术适配性"双标准的模型准入机制，使项目发展方向更透明、可预期，有利于形成稳定的社区协作节奏。
- 作为纯文档变更，风险极低，但其排序逻辑可能影响后续数个版本的功能投入方向。

### 4. 值得关注的技术点
- **"缓存适配度"的评估维度**：虽然本次提交未给出量化标准，但这一概念值得关注——它暗示项目对不同 DiT 架构（注意力结构、时序依赖模式等）能否有效应用缓存存在技术判断标准，这可能是后续文档或代码中会进一步展开的内容。
- 提交信息采用规范的 `docs:` 前缀并附带 PR 编号，体现了项目遵循 Conventional Commits 与 code review 流程，协作规范成熟。

### 5. 对项目发展的影响（结合 README 背景）
README 表明 cache-dit 是一个已发布至 PyTorch、具备下载量的成熟开源推理引擎，功能覆盖 Cache、并行、量化、CPU offload 四大方向。本次文档提交虽小，但体现了项目在**功能广度扩展期对优先级的主动管理**：通过明确模型支持排序，将有限的开发资源集中于社区最需要、且最能发挥缓存优势的模型上，避免盲目铺开。这种"以缓存收益为导向"的扩展策略，有助于巩固其在 DiT 推理加速细分领域的差异化定位，对项目持续吸引用户和贡献者具有积极意义。

## 详细提交记录

### [eafa114](https://github.com/vipshop/cache-dit/commit/eafa1149748833fc6ebc50dcb25e85e01dabc79e)

- **作者**: DefTruth
- **时间**: 2026-11-01T14:32:27Z
- **提交信息**: docs: update OVERVIEW.md (#1208)

* docs: rank pending models by community value and cache fit

* docs: update OVERVIEW.md

* docs: update OVERVIEW.md

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-11-02
**监控日期**: 2026-11-01
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 96083
- **最后更新**: 2026-11-02T01:26:33Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 6
- **主要提交者**: jthomson04, Thien Tran, MINJUN GIL

## AI分析总结

# vLLM 仓库昨日提交分析

## 1. 主要更新类型

- **性能优化（4项）**：KV 缓存卸载（KV Offload）的元数据处理优化、MoE 路由的 padding 跳过融合、CUDA 上 GDN 的 `in_proj_ba` 重叠恢复。
- **Bug修复（1项）**：GDN（可能是某种门控/路由机制）在 CUDA 路径下的算子重叠问题回退。
- **重构/核心架构改进（1项）**：注意力运行时中按层解析 KV dtype。

## 2. 关键变更点与项目方向的关系

- **KV Offload 成为本次提交的绝对主线**（3/6），包括：将卸载事件元数据移出循环 GC、在原始存储事件上携带请求上下文、清理 CachePolicy 与 OffloadingManager 中未使用的 `touch` 方法。这与 vLLM 追求"快速、低成本 LLM 服务"的定位高度一致——KV 缓存卸载直接降低长上下文场景的显存压力和成本。
- **注意力内核的按层 KV dtype 解析**属于核心调度层的精细化改进，使不同层可使用不同精度的 KV 缓存，为混合精度推理铺路。
- **MoE 路由 padding 跳过融合**直接对应 vLLM 对 MoE 模型（如 DeepSeek 系列）推理吞吐的持续优化，是大规模专家模型部署的关键路径。

## 3. 对项目的影响和潜在意义

- KV Offload 相关的三项提交（GC 元数据隔离、上下文携带、死代码清理）表明该子系统正从"功能可用"走向**工程成熟期**：消除 GC 停顿风险、保留请求上下文以支持更精确的缓存策略、精简 API。这为后续更智能的分层卸载策略打下基础。
- 按层 KV dtype 解析意味着 vLLM 正在支持**更灵活的内存-精度权衡**，对边缘/低成本部署场景有直接价值。
- MoE 融合优化延续了 vLLM 在 MoE 推理上的性能领先策略，对新模型的 day-one 支持能力是项目核心竞争力。

## 4. 值得关注的技术点

- **循环 GC 与卸载事件元数据的隔离**：Python 循环 GC 扫描大量事件对象会引入延迟抖动，将其移出 GC 跟踪范围是典型的延迟敏感系统优化手法，值得关注其实现方式（如 `__slots__`、`__dict__` 隔离或注册回调）。
- **原始存储事件携带请求上下文**：暗示卸载系统正引入请求级别的缓存归属语义，可能与后续的租户隔离、配额管理相关。
- **按层 KV dtype 的运行时解析**：在 attention 调度热路径上做 dtype 分派需要极致的开销控制，其实现值得深入阅读。
- **AI 协作署名现象**：多条提交含 Claude/Codex/vllm-agent 共同署名，反映该项目已高度采用 AI 辅助开发流程。

## 5. 基于 README 背景的项目发展影响

README 明确 vLLM 的目标是"为所有人提供简单、快速、廉价的 LLM 服务"。本批提交从三个维度支撑这一愿景：**廉价**——KV Offload 成熟化让大模型长上下文服务的显存成本进一步下降；**快速**——MoE 路由融合与 CUDA 算子重叠修复直接提升吞吐；**简单**——按层 dtype 的运行时自动解析减少了用户的配置负担。KV Offload 子系统在一日内集中落地多项改进，预示它将成为 vLLM 下一阶段的重点特性，可能很快对用户暴露更完整的分层缓存 API，从而显著增强 vLLM 在成本敏感的大规模部署场景中的竞争力。

## 详细提交记录

### [b8c04dd](https://github.com/vllm-project/vllm/commit/b8c04dd3b455affd8d91f0ab436b815491c9af38)

- **作者**: jthomson04
- **时间**: 2026-11-01T18:27:46Z
- **提交信息**: [Perf][KV Offload] Keep offload event metadata out of the cyclic GC (#63927)

Signed-off-by: jthomson04 <jwillthomson19@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [b2d07f5](https://github.com/vllm-project/vllm/commit/b2d07f59c7a5909287f9ef5f037fd575ebdbbed0)

- **作者**: Thien Tran
- **时间**: 2026-11-01T18:27:25Z
- **提交信息**: [Bugfix][GDN] Restore in_proj_ba overlap on CUDA (#64999)

Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [8530a77](https://github.com/vllm-project/vllm/commit/8530a778f78dc7cd9a31e108ebc035c4b27ceb3c)

- **作者**: Wei-Ming Chen
- **时间**: 2026-11-01T15:03:44Z
- **提交信息**: [Core][Attention] Resolve per-layer KV dtype in attention runtime (#56155)

Signed-off-by: weimingc <17592131+meenchen@users.noreply.github.com>
Co-authored-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: Lucas Wilkinson <LucasWilkinson@users.noreply.github.com>

### [5d55ef1](https://github.com/vllm-project/vllm/commit/5d55ef1590c92213e3893dc8e8712f7f2e0bc508)

- **作者**: MINJUN GIL
- **时间**: 2026-11-01T08:02:49Z
- **提交信息**: [KV Offload] Remove unused touch from CachePolicy and OffloadingManager (#63900)

Signed-off-by: mindungil <alswnsrlf12@naver.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [17e6759](https://github.com/vllm-project/vllm/commit/17e675965d54bef8a3eb77ea92c6bae195ef793c)

- **作者**: Chang Guo
- **时间**: 2026-11-01T07:34:52Z
- **提交信息**: [KV Offload] Carry request context on raw stored events (#63695)

Signed-off-by: Chang Guo <cguo51@asu.edu>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [2a4792d](https://github.com/vllm-project/vllm/commit/2a4792ddcc4ba2091aaf743358866c86bc53bf75)

- **作者**: Woosuk Kwon
- **时间**: 2026-11-01T07:06:25Z
- **提交信息**: [Perf][MoE] Fuse padding skipping in grouped and Muse prepared routing (#64955)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: Codex <noreply@openai.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-11-02
**监控日期**: 2026-11-01
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7473
- **最后更新**: 2026-11-02T01:18:06Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---
