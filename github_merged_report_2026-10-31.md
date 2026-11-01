# GitHub Stars 合并报告 - 2026-10-31

**合并日期**: 2026-11-01
**监控日期**: 2026-10-31
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


**报告日期**: 2026-11-01
**监控日期**: 2026-10-31
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2271
- **最后更新**: 2026-10-31T05:30:09Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-11-01
**监控日期**: 2026-10-31
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2979
- **最后更新**: 2026-10-31T19:19:05Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-11-01
**监控日期**: 2026-10-31
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2321
- **最后更新**: 2026-10-31T11:06:11Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-11-01
**监控日期**: 2026-10-31
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6827
- **最后更新**: 2026-11-01T01:01:49Z

## 提交统计

- **昨日提交总数**: 49
- **提交者数量**: 3
- **主要提交者**: Yang Xu, eigen, Akaash Parthasarathy

## AI分析总结

# FlashInfer 昨日提交综合分析（共 49 条提交）

## 一、主要更新方向

昨日提交集中于四条主线：Blackwell 全系新硬件（B200/GB300/Rubin/RTX 5090）的内核性能调优；确定性（deterministic）内核命名体系的统一重构；训练能力的系统性扩展；以及前沿模型的推理链路适配。性能优化占绝对多数，其次为功能新增与 Bug 修复，整体延续"高性能 GPU 推理内核"定位并向训练场景延伸。

## 二、关键变更

**Blackwell 全系架构深度调优。** 大量提交针对 sm_100a、sm_103a、sm_107a、sm_120a 精细优化。MQA logits 在多代架构上新增并行调度与路由窗口，几何平均提速约 10%–1.19×。程序化依赖启动（PDL）通过动态共享内存控制每 SM 的 CTA 数量，fused QK RoPE 的 BF16/FP8 变体新增 PDL 路径，提速约 1.14–1.19×。SM90 WCX 压缩窗口从 decode 轮扩展到 128–1024 token 场景。门控残差 RMSNorm、张量并行 MoE finalize 等路径也按 token 数分段调优，部分提速约 19%。

**MoE 推理链路完善。** SM107 量化 combine 支持 masked slot 跳过；SM90 BF16 MegaMoE 压缩扩展到更多形状；分组 GEMM 与 all-reduce 融合在 sm_103a 上按 token 数路由；MegaMoE 新增 `kernel_variant="auto"`，通过 autotune v2 智能选择内核变体，服务 Rubin 平台。

**分页注意力与新模型适配。** Cake FMHA FP8 分页 prefill 引入短 KV 单 stage 与多 wave 构建，B200 上最高提速 1.472×。新增 MiniMax-M3 稀疏注意力 indexer（MSA + ICP），对接 vLLM 生态。Qwen 3.5 的 GDN 实验性 block 将投影、卷积、门控、delta rule、RMSNorm 融合为单次调用，B200 上 MTP verify 最高 1.62× 加速，并引入后端注册机制。

**确定性命名规范确立。** 因果卷积（causal conv1d）及分块 LM-head + loss 后端统一重命名为带 `det` 前缀的版本，明确 "`det` = 逐位一致结果" 的 API 约定。旧名称保留为兼容别名，环境变量不变，零破坏性。通过 SASS 逐字节对比与性能复测（差异 0.9958–1.0056，处于噪声范围）证明纯命名整理、性能无损。

**训练能力系统性扩展。** mHC 确定性训练层从 H=4096 扩展到 H=5120/7168，并新增 sm_107a 快速系数链程序；LM-head 损失、Mamba2 chunk-scan/varlen、GDN 训练反向均提供位级可复现版本，同时新增 `deterministic=False` 的非确定性可选路径，性能持平或更优（RMSNorm 反向最高 13×+）。新增为 Cake 上下文并行（KCP）定制的打包 width-4 深度可分离因果卷积 + SiLU 实现，包含 halo exchange 逻辑，覆盖 sm_100a/sm_103a/sm_107a，配套 `RecomputeHandleDetKcp` 句柄按需重算以节省显存。causal conv1d 新增非确定性反向及 `bwd_grid_mult` 选项，缓解多流并发波次尾延迟。

## 三、Bug 修复要点

dX 梯度在 V=256 时因空 K 切片写入未初始化累加器导致错误，经三层守卫修复；CUDA Graph 捕获期间禁止 mHC workspace 的 `torch.zeros` 分配，防止污染重放；修复 GPU 抢占下 Kimi-K3 E384 TP4/TP8 程序的死锁；修复宿主侧绑定缓存按 `data_ptr` 键控的 miss 与多线程共享变量竞争；重新生成 41 个 GEMM 程序解决寄存器溢出。

## 四、技术关注点

项目采用"注册表 + 路由目录"架构，大量性能来自按形状特征选择已有程序而非重写内核，调优成本显著降低。位级一致性纪律贯穿全部提交，PDL、bwd_grid_mult 等路径均保证与基线逐位相同。基准方法论严谨（中位数、冷 L2、成对交替、CUPTI GPU 时间），高风险优化默认 opt-in。分块 LM-head 后端同时支持 CE loss、policy loss、logprob 和 KL 计算，但目前仅支持 BF16。halo exchange 的确定性实现是将上下文并行引入训练侧的关键细节；MoE finalize 的 token-owner 窗口调优展示了用"策略阈值"适配新硬件的思路。

## 五、对项目发展的整体影响

FlashInfer 正从推理内核库演进为跨硬件、跨场景、跨精度的全栈 GPU 计算基础设施：推理侧紧跟 DeepSeek-V4、Kimi-K3、MiniMax-M3、Qwen 3.5 等前沿模型，硬件覆盖从消费级 RTX 到 Rubin 数据中心级；训练侧通过确定性与非确定性双轨方案补齐正确性与并发安全性。确定性命名规范为后续更多 `det` 内核奠定统一基础，零破坏性的 API 演进体现了项目成熟度。严格的位级验证与测试加固，是其在生产环境被广泛采用的关键，进一步强化了作为 LLM 推理与训练关键基础设施的定位。

## 详细提交记录

### [b6fa0cf](https://github.com/flashinfer-ai/flashinfer/commit/b6fa0cfc4395deb2ea08679bcff3c74e58450dc9)

- **作者**: eigen
- **时间**: 2026-10-31T23:54:54Z
- **提交信息**: perf(cake_deepgemm_dense_mqa): serve fp4:le32:short on sm_100a up to K = 4096 with a bucket program of its own (#8151)

This PR follows up #7607, #7643, #7741, #7779, #8113, #8124 and #8142.
FlashInfer's Cake DeepGEMM-form MQA logits programs for Blackwell back
`flashinfer.dense_mqa` and `flashinfer.paged_mqa`. The variants are
dense FP8 with 32 or 64 heads, dense FP4 with 32 heads (including fused
metadata + logits sequences), and paged FP8. This PR changes dense FP4
with 32 heads, on sm_100a (B200) only. It adds one generated program,
`cake_deepgemm_dense_mqa_72ba84de495cdb32a8de`. This FP4 scan32 logits
program prefetches the first KV tile into L2. The catalog gains one
sm_100a stage bucket on the route `fp4:le32:short`. For K up to 4096
keys, that route now runs 72ba84de instead of
`cake_deepgemm_dense_mqa_63c7e49139b05539648a`. Above K 4096, and on
sm_103a, routes are unchanged. The only other changes are the catalog
reader and README, which now allow a stage bucket on a `:short` route,
and the generated tests. Logits are bitwise equal on every row of both
tables (106/106 on each GPU). The baseline is the previous version,
FlashInfer main 35ea8e25aa5a, for the dense MQA paths. On B200, 3 of the
106 rows run the updated route, and each is faster in all 3 sessions. `Q
7, K 2048` FP4 goes from 4.74 to 4.54 µs (1.0423). `Q 16, K 4096` FP4
goes from 5.36 to 5.09 µs (1.0531). `Q 128, K 4096` FP4 goes from 6.85
to 6.74 µs (1.0166). The other 103 rows run byte-identical programs in
both versions. They read 0.9964–1.0040 (median 1.0000), which is
measurement noise. On GB300, no row changes route. All 106 rows run
byte-identical programs and read 0.9930–1.0142 (median 1.0000), which is
also measurement noise.

**NVIDIA B200** (sm_100a, 148 SMs), CUDA 13.4 (nvcc V13.4.92,
JIT-compiled), driver 580.82.07, torch 2.14.1+cu130. Previous version =
FlashInfer main 35ea8e25aa5a (dense MQA paths). Timing is CUPTI GPU time
per call with a cold L2. µs is the median over the 3 sessions of each
session's median. Speedup is the median over the sessions of previous /
this (> 1 = faster). Rows that launch more than one kernel per call
report the sum of kernel times. The notation is the same as in #7643. `Q
q, K k` is q queries over k keys. `prefill Q q, prefix p, causal` is q
new queries attending causally over p cached keys plus themselves (K = p
+ q). "2 sequences" and "2048-query chunks" mean the same as in #7643.
"updated" means the row now runs
`cake_deepgemm_dense_mqa_72ba84de495cdb32a8de` instead of
`cake_deepgemm_dense_mqa_63c7e49139b05539648a`. "same program" means
every program on the row is byte-identical to the previous version.

| shape | dtype | heads | previous µs | this PR µs | speedup | program |
|---|---|---:|---:|---:|---:|---|
| prefill Q 37, prefix 4100, causal | FP8 | 32 | 5.18 | 5.18 | 1.0000 |
same program |
| prefill Q 1024, prefix 32779, causal | FP8 | 32 | 138.66 | 138.61 |
0.9993 | same program |
| prefill Q 1, prefix 0, causal | FP8 | 64 | 3.71 | 3.70 | 1.0022 | same
program |
| prefill Q 1, prefix 4100, causal | FP8 | 64 | 3.87 | 3.87 | 1.0000 |
same program |
| prefill Q 1, prefix 32779, causal | FP8 | 64 | 5.06 | 5.06 | 1.0000 |
same program |
| prefill Q 1, prefix 131077, causal | FP8 | 64 | 7.97 | 7.97 | 1.0000 |
same program |
| prefill Q 2, prefix 0, causal | FP8 | 64 | 3.71 | 3.71 | 1.0000 | same
program |
| prefill Q 2, prefix 4100, causal | FP8 | 64 | 4.51 | 4.51 | 1.0000 |
same program |
| prefill Q 3, prefix 0, causal | FP8 | 64 | 3.79 | 3.78 | 1.0000 | same
program |
| prefill Q 3, prefix 4100, causal | FP8 | 64 | 4.46 | 4.46 | 1.0000 |
same program |
| prefill Q 7, prefix 0, causal | FP8 | 64 | 3.78 | 3.78 | 1.0000 | same
program |
| prefill Q 7, prefix 4100, causal | FP8 | 64 | 4.48 | 4.48 | 1.0000 |
same program |
| prefill Q 8, prefix 0, causal | FP8 | 64 | 3.71 | 3.71 | 1.0000 | same
program |
| prefill Q 8, prefix 4100, causal | FP8 | 64 | 4.54 | 4.54 | 1.0000 |
same program |
| prefill Q 16, prefix 0, causal | FP8 | 64 | 3.78 | 3.78 | 1.0000 |
same program |
| prefill Q 16, prefix 4100, causal | FP8 | 64 | 4.58 | 4.58 | 1.0000 |
same program |
| prefill Q 37, prefix 0, causal | FP8 | 64 | 3.78 | 3.78 | 1.0000 |
same program |
| prefill Q 37, prefix 4100, causal | FP8 | 64 | 5.63 | 5.63 | 1.0000 |
same program |
| prefill Q 37, prefix 32779, causal | FP8 | 64 | 14.30 | 14.32 | 1.0000
| same program |
| prefill Q 37, prefix 131077, causal | FP8 | 64 | 40.37 | 40.35 |
1.0004 | same program |
| prefill Q 64, prefix 0, causal | FP8 | 64 | 4.06 | 4.06 | 1.0000 |
same program |
| prefill Q 64, prefix 4100, causal | FP8 | 64 | 6.56 | 6.58 | 1.0001 |
same program |
| prefill Q 128, prefix 0, causal | FP8 | 64 | 4.06 | 4.06 | 1.0000 |
same program |
| prefill Q 128, prefix 4100, causal | FP8 | 64 | 9.30 | 9.28 | 1.0017 |
same program |
| prefill Q 128, prefix 4100, causal, 2 sequences | FP8 | 64 | 8.14 |
8.13 | 1.0020 | same program |
| prefill Q 128, prefix 32779, causal | FP8 | 64 | 34.43 | 34.45 |
1.0000 | same program |
| prefill Q 128, prefix 131077, causal | FP8 | 64 | 126.13 | 126.13 |
0.9988 | same program |
| prefill Q 129, prefix 0, causal | FP8 | 64 | 4.03 | 4.03 | 1.0000 |
same program |
| prefill Q 129, prefix 4100, causal | FP8 | 64 | 9.23 | 9.18 | 1.0017 |
same program |
| prefill Q 1023, prefix 0, causal | FP8 | 64 | 10.21 | 10.21 | 1.0000 |
same program |
| prefill Q 1023, prefix 4100, causal | FP8 | 64 | 40.50 | 40.48 |
1.0006 | same program |
| prefill Q 1024, prefix 0, causal | FP8 | 64 | 10.30 | 10.30 | 1.0000 |
same program |
| prefill Q 1024, prefix 4100, causal | FP8 | 64 | 40.35 | 40.40 |
1.0004 | same program |
| prefill Q 1024, prefix 32779, causal | FP8 | 64 | 267.12 | 266.39 |
1.0028 | same program |
| prefill Q 1024, prefix 131077, causal | FP8 | 64 | 1081.78 | 1084.90 |
0.9971 | same program |
| prefill Q 4096, prefix 0, causal | FP8 | 64 | 70.35 | 70.38 | 1.0007 |
same program |
| prefill Q 4096, prefix 4100, causal | FP8 | 64 | 201.11 | 200.74 |
1.0040 | same program |
| prefill Q 4096, prefix 32779, causal | FP8 | 64 | 1147.63 | 1141.69 |
1.0013 | same program |
| prefill Q 4096, prefix 32779, causal, 2 sequences | FP8 | 64 | 788.23
| 786.74 | 1.0019 | same program |
| prefill Q 4096, prefix 32779, causal, 2048-query chunks | FP8 | 64 |
1151.78 | 1147.92 | 1.0034 | same program |
| prefill Q 4096, prefix 131077, causal | FP8 | 64 | 4443.03 | 4447.44 |
0.9990 | same program |
| prefill Q 4096, prefix 131077, causal, 2048-query chunks | FP8 | 64 |
4435.37 | 4433.33 | 1.0011 | same program |
| prefill Q 8192, prefix 0, causal | FP8 | 64 | 280.61 | 281.07 | 0.9985
| same program |
| prefill Q 8192, prefix 4100, causal | FP8 | 64 | 553.57 | 554.00 |
0.9993 | same program |
| prefill Q 8192, prefix 32779, causal | FP8 | 64 | 2472.66 | 2472.39 |
1.0001 | same program |
| prefill Q 8192, prefix 32779, causal, 2048-query chunks | FP8 | 64 |
2489.43 | 2488.77 | 1.0010 | same program |
| prefill Q 8192, prefix 131077, causal | FP8 | 64 | 9088.08 | 9106.12 |
0.9971 | same program |
| prefill Q 8192, prefix 131077, causal, 2048-query chunks | FP8 | 64 |
9093.10 | 9093.75 | 0.9999 | same program |
| prefill Q 16231, prefix 0, causal | FP8 | 64 | 1095.48 | 1094.67 |
0.9986 | same program |
| prefill Q 16231, prefix 4100, causal | FP8 | 64 | 1649.90 | 1649.91 |
1.0000 | same program |
| prefill Q 16231, prefix 32779, causal | FP8 | 64 | 5451.25 | 5460.11 |
0.9984 | same program |
| prefill Q 16231, prefix 32779, causal, 2048-query chunks | FP8 | 64 |
5514.07 | 5515.96 | 0.9992 | same program |
| prefill Q 16231, prefix 131077, causal | FP8 | 64 | 18671.60 |
18673.82 | 1.0001 | same program |
| prefill Q 16231, prefix 131077, causal, 2048-query chunks | FP8 | 64 |
18676.12 | 18672.47 | 1.0000 | same program |
| Q 1, K 4096 | FP8 | 32 | 3.71 | 3.71 | 1.0000 | same program |
| Q 1, K 32768 | FP8 | 32 | 4.80 | 4.80 | 1.0000 | same program |
| Q 1, K 131072 | FP8 | 32 | 7.71 | 7.71 | 1.0000 | same program |
| Q 1, K 1048576 | FP8 | 32 | 31.31 | 31.34 | 0.9980 | same program |
| Q 1, K 1048832 | FP8 | 32 | 31.36 | 31.34 | 1.0000 | same program |
| Q 3, K 8192 | FP8 | 32 | 4.77 | 4.77 | 1.0000 | same program |
| Q 3, K 1048832 | FP8 | 32 | 34.57 | 34.51 | 0.9991 | same program |
| Q 16, K 2048 | FP8 | 32 | 4.58 | 4.58 | 1.0000 | same program |
| Q 16, K 4096 | FP8 | 32 | 4.69 | 4.67 | 1.0034 | same program |
| Q 16, K 32768 | FP8 | 32 | 7.78 | 7.78 | 1.0021 | same program |
| Q 16, K 131072 | FP8 | 32 | 14.91 | 14.93 | 1.0010 | same program |
| Q 16, K 1048576 | FP8 | 32 | 71.66 | 71.94 | 0.9980 | same program |
| Q 16, K 1048832 | FP8 | 32 | 71.94 | 72.14 | 0.9971 | same program |
| Q 33, K 8192 | FP8 | 32 | 5.47 | 5.47 | 1.0000 | same program |
| Q 33, K 1048832 | FP8 | 32 | 199.92 | 199.25 | 1.0034 | same program |
| Q 37, K 4137 | FP8 | 32 | 5.17 | 5.15 | 1.0000 | same program |
| Q 128, K 2048 | FP8 | 32 | 6.11 | 6.11 | 1.0000 | same program |
| Q 128, K 4096 | FP8 | 32 | 7.38 | 7.36 | 1.0022 | same program |
| Q 128, K 32768 | FP8 | 32 | 21.14 | 21.20 | 1.0000 | same program |
| Q 128, K 131072 | FP8 | 32 | 64.52 | 64.61 | 0.9986 | same program |
| Q 128, K 131328 | FP8 | 32 | 64.66 | 64.56 | 1.0015 | same program |
| Q 130, K 8192 | FP8 | 32 | 10.46 | 10.46 | 1.0000 | same program |
| Q 130, K 8448 | FP8 | 32 | 10.61 | 10.61 | 1.0000 | same program |
| Q 130, K 65792 | FP8 | 32 | 38.80 | 38.86 | 0.9984 | same program |
| Q 132, K 2048 | FP8 | 32 | 6.74 | 6.74 | 0.9976 | same program |
| Q 132, K 8448 | FP8 | 32 | 10.51 | 10.50 | 1.0015 | same program |
| Q 132, K 65792 | FP8 | 32 | 38.88 | 38.91 | 0.9996 | same program |
| Q 1024, K 33803 | FP8 | 32 | 140.67 | 140.72 | 1.0007 | same program |
| Q 2052, K 2048 | FP8 | 32 | 23.84 | 23.81 | 1.0006 | same program |
| Q 2052, K 8448 | FP8 | 32 | 70.21 | 70.16 | 1.0014 | same program |
| Q 2053, K 2048 | FP8 | 32 | 24.21 | 24.22 | 0.9997 | same program |
| Q 2053, K 8448 | FP8 | 32 | 70.85 | 70.84 | 0.9992 | same program |
| Q 1, K 4096 | FP4 | 32 | 3.95 | 3.95 | 1.0000 | same program |
| Q 1, K 32768 | FP4 | 32 | 4.67 | 4.66 | 1.0000 | same program |
| Q 1, K 131072 | FP4 | 32 | 6.35 | 6.34 | 1.0000 | same program |
| Q 1, K 131328 | FP4 | 32 | 6.61 | 6.62 | 1.0000 | same program |
| Q 7, K 2048 | FP4 | 32 | 4.74 | 4.54 | 1.0423 | updated |
| Q 16, K 4096 | FP4 | 32 | 5.36 | 5.09 | 1.0531 | updated |
| Q 16, K 32768 | FP4 | 32 | 7.33 | 7.34 | 0.9978 | same program |
| Q 16, K 131072 | FP4 | 32 | 13.63 | 13.63 | 0.9989 | same program |
| Q 16, K 1048576 | FP4 | 32 | 63.09 | 63.09 | 1.0000 | same program |
| Q 16, K 1048832 | FP4 | 32 | 65.90 | 65.84 | 1.0010 | same program |
| Q 33, K 8192 | FP4 | 32 | 5.95 | 5.94 | 1.0026 | same program |
| Q 33, K 1048832 | FP4 | 32 | 139.16 | 138.85 | 1.0022 | same program |
| Q 128, K 4096 | FP4 | 32 | 6.85 | 6.74 | 1.0166 | updated |
| Q 128, K 32768 | FP4 | 32 | 19.74 | 19.73 | 1.0008 | same program |
| Q 128, K 131072 | FP4 | 32 | 61.78 | 61.73 | 1.0010 | same program |
| Q 130, K 65536 | FP4 | 32 | 36.05 | 36.14 | 0.9964 | same program |
| Q 130, K 65792 | FP4 | 32 | 38.11 | 38.06 | 1.0021 | same program |
| Q 1024, K 2048 | FP4 | 32 | 14.19 | 14.22 | 0.9966 | same program |
| Q 2052, K 2048 | FP4 | 32 | 24.08 | 24.13 | 1.0000 | same program |
| Q 2052, K 65792 | FP4 | 32 | 475.71 | 473.86 | 1.0011 | same program |

**NVIDIA GB300** (sm_103a, 152 SMs), CUDA 13.4 (nvcc V13.4.92,
JIT-compiled), driver 580.159.03, torch 2.14.1+cu130. Previous version =
FlashInfer main 35ea8e25aa5a (dense MQA paths). Timing, notation and the
labels are the same as in the B200 table.

| shape | dtype | heads | previous µs | this PR µs | speedup | program |
|---|---|---:|---:|---:|---:|---|
| prefill Q 37, prefix 4100, causal | FP8 | 32 | 5.39 | 5.38 | 1.0030 |
same program |
| prefill Q 1024, prefix 32779, causal | FP8 | 32 | 108.35 | 108.30 |
1.0004 | same program |
| prefill Q 1, prefix 0, causal | FP8 | 64 | 3.90 | 3.90 | 1.0000 | same
program |
| prefill Q 1, prefix 4100, causal | FP8 | 64 | 4.00 | 4.00 | 1.0000 |
same program |
| prefill Q 1, prefix 32779, causal | FP8 | 64 | 4.96 | 4.99 | 1.0000 |
same program |
| prefill Q 1, prefix 131077, causal | FP8 | 64 | 7.78 | 7.78 | 1.0000 |
same program |
| prefill Q 2, prefix 0, causal | FP8 | 64 | 3.94 | 3.94 | 1.0000 | same
program |
| prefill Q 2, prefix 4100, causal | FP8 | 64 | 4.61 | 4.61 | 1.0000 |
same program |
| prefill Q 3, prefix 0, causal | FP8 | 64 | 3.71 | 3.71 | 1.0000 | same
program |
| prefill Q 3, prefix 4100, causal | FP8 | 64 | 4.37 | 4.37 | 1.0000 |
same program |
| prefill Q 7, prefix 0, causal | FP8 | 64 | 3.78 | 3.78 | 1.0000 | same
program |
| prefill Q 7, prefix 4100, causal | FP8 | 64 | 4.38 | 4.38 | 1.0000 |
same program |
| prefill Q 8, prefix 0, causal | FP8 | 64 | 3.71 | 3.71 | 1.0000 | same
program |
| prefill Q 8, prefix 4100, causal | FP8 | 64 | 4.38 | 4.38 | 1.0000 |
same program |
| prefill Q 16, prefix 0, causal | FP8 | 64 | 3.71 | 3.71 | 1.0000 |
same program |
| prefill Q 16, prefix 4100, causal | FP8 | 64 | 4.45 | 4.43 | 1.0036 |
same program |
| prefill Q 37, prefix 0, causal | FP8 | 64 | 3.76 | 3.76 | 1.0000 |
same program |
| prefill Q 37, prefix 4100, causal | FP8 | 64 | 5.41 | 5.41 | 1.0000 |
same program |
| prefill Q 37, prefix 32779, causal | FP8 | 64 | 12.72 | 12.74 | 1.0000
| same program |
| prefill Q 37, prefix 131077, causal | FP8 | 64 | 34.22 | 34.26 |
0.9995 | same program |
| prefill Q 64, prefix 0, causal | FP8 | 64 | 3.81 | 3.81 | 1.0000 |
same program |
| prefill Q 64, prefix 4100, causal | FP8 | 64 | 6.08 | 6.08 | 1.0000 |
same program |
| prefill Q 128, prefix 0, causal | FP8 | 64 | 3.92 | 3.94 | 1.0000 |
same program |
| prefill Q 128, prefix 4100, causal | FP8 | 64 | 8.59 | 8.61 | 0.9981 |
same program |
| prefill Q 128, prefix 4100, causal, 2 sequences | FP8 | 64 | 7.55 |
7.55 | 1.0000 | same program |
| prefill Q 128, prefix 32779, causal | FP8 | 64 | 30.54 | 30.56 |
1.0000 | same program |
| prefill Q 128, prefix 131077, causal | FP8 | 64 | 103.07 | 103.10 |
1.0003 | same program |
| prefill Q 129, prefix 0, causal | FP8 | 64 | 3.92 | 3.90 | 1.0000 |
same program |
| prefill Q 129, prefix 4100, causal | FP8 | 64 | 8.69 | 8.67 | 1.0018 |
same program |
| prefill Q 1023, prefix 0, causal | FP8 | 64 | 9.62 | 9.63 | 1.0000 |
same program |
| prefill Q 1023, prefix 4100, causal | FP8 | 64 | 35.66 | 35.68 |
1.0000 | same program |
| prefill Q 1024, prefix 0, causal | FP8 | 64 | 9.66 | 9.66 | 0.9983 |
same program |
| prefill Q 1024, prefix 4100, causal | FP8 | 64 | 35.81 | 35.82 |
1.0000 | same program |
| prefill Q 1024, prefix 32779, causal | FP8 | 64 | 204.75 | 204.96 |
0.9990 | same program |
| prefill Q 1024, prefix 131077, causal | FP8 | 64 | 826.30 | 824.83 |
1.0056 | same program |
| prefill Q 4096, prefix 0, causal | FP8 | 64 | 61.92 | 61.95 | 1.0005 |
same program |
| prefill Q 4096, prefix 4100, causal | FP8 | 64 | 156.05 | 156.05 |
0.9997 | same program |
| prefill Q 4096, prefix 32779, causal | FP8 | 64 | 874.69 | 871.74 |
1.0034 | same program |
| prefill Q 4096, prefix 32779, causal, 2 sequences | FP8 | 64 | 580.51
| 579.46 | 1.0000 | same program |
| prefill Q 4096, prefix 32779, causal, 2048-query chunks | FP8 | 64 |
867.94 | 871.48 | 0.9973 | same program |
| prefill Q 4096, prefix 131077, causal | FP8 | 64 | 3528.62 | 3486.48 |
0.9959 | same program |
| prefill Q 4096, prefix 131077, causal, 2048-query chunks | FP8 | 64 |
3503.42 | 3456.66 | 1.0142 | same program |
| prefill Q 8192, prefix 0, causal | FP8 | 64 | 209.33 | 209.42 | 1.0003
| same program |
| prefill Q 8192, prefix 4100, causal | FP8 | 64 | 407.74 | 410.37 |
0.9936 | same program |
| prefill Q 8192, prefix 32779, causal | FP8 | 64 | 1846.04 | 1852.08 |
0.9975 | same program |
| prefill Q 8192, prefix 32779, causal, 2048-query chunks | FP8 | 64 |
1896.16 | 1891.62 | 1.0036 | same program |
| prefill Q 8192, prefix 131077, causal | FP8 | 64 | 7136.69 | 7130.07 |
1.0003 | same program |
| prefill Q 8192, prefix 131077, causal, 2048-query chunks | FP8 | 64 |
7224.89 | 7219.87 | 1.0002 | same program |
| prefill Q 16231, prefix 0, causal | FP8 | 64 | 829.14 | 832.67 |
0.9977 | same program |
| prefill Q 16231, prefix 4100, causal | FP8 | 64 | 1243.33 | 1246.14 |
0.9999 | same program |
| prefill Q 16231, prefix 32779, causal | FP8 | 64 | 4287.95 | 4291.36 |
0.9993 | same program |
| prefill Q 16231, prefix 32779, causal, 2048-query chunks | FP8 | 64 |
4245.92 | 4239.64 | 1.0016 | same program |
| prefill Q 16231, prefix 131077, causal | FP8 | 64 | 14620.21 |
14581.58 | 1.0005 | same program |
| prefill Q 16231, prefix 131077, causal, 2048-query chunks | FP8 | 64 |
14867.10 | 14884.68 | 0.9986 | same program |
| Q 1, K 4096 | FP8 | 32 | 3.84 | 3.84 | 1.0000 | same program |
| Q 1, K 32768 | FP8 | 32 | 4.67 | 4.67 | 1.0000 | same program |
| Q 1, K 131072 | FP8 | 32 | 7.47 | 7.46 | 1.0021 | same program |
| Q 1, K 1048576 | FP8 | 32 | 29.84 | 29.84 | 1.0000 | same program |
| Q 1, K 1048832 | FP8 | 32 | 29.81 | 29.78 | 1.0000 | same program |
| Q 3, K 8192 | FP8 | 32 | 4.74 | 4.74 | 1.0000 | same program |
| Q 3, K 1048832 | FP8 | 32 | 33.36 | 33.22 | 1.0014 | same program |
| Q 16, K 2048 | FP8 | 32 | 4.72 | 4.70 | 1.0000 | same program |
| Q 16, K 4096 | FP8 | 32 | 4.80 | 4.80 | 1.0000 | same program |
| Q 16, K 32768 | FP8 | 32 | 7.31 | 7.25 | 1.0088 | same program |
| Q 16, K 131072 | FP8 | 32 | 13.38 | 13.38 | 1.0000 | same program |
| Q 16, K 1048576 | FP8 | 32 | 59.14 | 59.17 | 1.0000 | same program |
| Q 16, K 1048832 | FP8 | 32 | 60.14 | 60.11 | 0.9996 | same program |
| Q 33, K 8192 | FP8 | 32 | 5.44 | 5.44 | 1.0000 | same program |
| Q 33, K 1048832 | FP8 | 32 | 177.36 | 177.36 | 0.9986 | same program |
| Q 37, K 4137 | FP8 | 32 | 5.38 | 5.38 | 1.0000 | same program |
| Q 128, K 2048 | FP8 | 32 | 5.90 | 5.90 | 1.0000 | same program |
| Q 128, K 4096 | FP8 | 32 | 7.06 | 7.04 | 1.0023 | same program |
| Q 128, K 32768 | FP8 | 32 | 18.27 | 18.27 | 1.0000 | same program |
| Q 128, K 131072 | FP8 | 32 | 53.73 | 53.71 | 0.9997 | same program |
| Q 128, K 131328 | FP8 | 32 | 55.20 | 55.22 | 0.9997 | same program |
| Q 130, K 8192 | FP8 | 32 | 9.55 | 9.55 | 1.0000 | same program |
| Q 130, K 8448 | FP8 | 32 | 9.84 | 9.82 | 1.0000 | same program |
| Q 130, K 65792 | FP8 | 32 | 33.57 | 33.57 | 1.0000 | same program |
| Q 132, K 2048 | FP8 | 32 | 6.50 | 6.50 | 1.0000 | same program |
| Q 132, K 8448 | FP8 | 32 | 9.79 | 9.78 | 1.0016 | same program |
| Q 132, K 65792 | FP8 | 32 | 33.46 | 33.35 | 1.0031 | same program |
| Q 1024, K 33803 | FP8 | 32 | 109.79 | 109.74 | 1.0001 | same program |
| Q 2052, K 2048 | FP8 | 32 | 20.94 | 20.96 | 1.0000 | same program |
| Q 2052, K 8448 | FP8 | 32 | 61.15 | 61.12 | 1.0005 | same program |
| Q 2053, K 2048 | FP8 | 32 | 21.42 | 21.41 | 1.0000 | same program |
| Q 2053, K 8448 | FP8 | 32 | 61.62 | 61.63 | 0.9997 | same program |
| Q 1, K 4096 | FP4 | 32 | 3.84 | 3.84 | 1.0000 | same program |
| Q 1, K 32768 | FP4 | 32 | 4.54 | 4.56 | 0.9930 | same program |
| Q 1, K 131072 | FP4 | 32 | 6.42 | 6.45 | 0.9975 | same program |
| Q 1, K 131328 | FP4 | 32 | 6.66 | 6.67 | 0.9977 | same program |
| Q 7, K 2048 | FP4 | 32 | 4.67 | 4.67 | 1.0000 | same program |
| Q 16, K 4096 | FP4 | 32 | 4.85 | 4.85 | 1.0000 | same program |
| Q 16, K 32768 | FP4 | 32 | 6.66 | 6.64 | 1.0024 | same program |
| Q 16, K 131072 | FP4 | 32 | 12.06 | 12.06 | 1.0027 | same program |
| Q 16, K 1048576 | FP4 | 32 | 54.37 | 54.34 | 0.9994 | same program |
| Q 16, K 1048832 | FP4 | 32 | 54.18 | 54.16 | 1.0009 | same program |
| Q 33, K 8192 | FP4 | 32 | 5.54 | 5.54 | 1.0000 | same program |
| Q 33, K 1048832 | FP4 | 32 | 118.53 | 118.62 | 0.9993 | same program |
| Q 128, K 4096 | FP4 | 32 | 6.40 | 6.43 | 1.0000 | same program |
| Q 128, K 32768 | FP4 | 32 | 17.12 | 17.12 | 1.0000 | same program |
| Q 128, K 131072 | FP4 | 32 | 52.96 | 52.96 | 1.0000 | same program |
| Q 130, K 65536 | FP4 | 32 | 30.66 | 30.66 | 1.0000 | same program |
| Q 130, K 65792 | FP4 | 32 | 30.80 | 30.82 | 0.9995 | same program |
| Q 1024, K 2048 | FP4 | 32 | 13.97 | 13.95 | 1.0023 | same program |
| Q 2052, K 2048 | FP4 | 32 | 21.52 | 21.71 | 0.9948 | same program |
| Q 2052, K 65792 | FP4 | 32 | 394.56 | 394.61 | 0.9996 | same program |

The family's other Cake variants (dense FP8 with 32 or 64 heads, dense
FP4 with 32 heads including fused metadata + logits sequences, and paged
FP8) ship on sm_100a and sm_103a only.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* FP4 short-route execution is now supported on sm_100a for inputs with
K up to 4096, expanding the available configurations.
* **Documentation**
* Clarified stage-bucket options for short and KV-split routes,
including how route stages are selected.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery Huang <averyh@nvidia.com>

### [a531cb1](https://github.com/flashinfer-ai/flashinfer/commit/a531cb1b97a3258dfeaa8d4769d134d53b7a92cb)

- **作者**: eigen
- **时间**: 2026-10-31T23:45:01Z
- **提交信息**: perf(cake_deepgemm_dense_mqa): serve small query counts one KV block past the fused Q <= 2048 bound on sm_103a (#8150)

This PR follows up #7607, #7643, #7741, #7779, #8113, #8124 and #8142.
FlashInfer's Cake DeepGEMM-form MQA logits programs for Blackwell back
`flashinfer.dense_mqa` and `flashinfer.paged_mqa`. The variants are
dense FP8 with 32 or 64 heads, dense FP4 with 32 heads (including fused
metadata + logits sequences), and paged FP8. This PR changes dense FP8
with 32 heads, on sm_103a only. The catalog policy gains a
per-architecture small-Q band for the single-launch fused Q <= 2048
route `fp8:qle2048:short`. The band uses two new keys,
`fused_qle2048_small_q_max_queries` and `fused_qle2048_small_q_max_kv`.
On sm_103a, a 32-head FP8 call with 128 < Q <= 256 and K <= 65792 now
runs `fp8:qle2048:short`. Before this change, it ran the two-launch
sequence. Larger query counts keep the 65536 KV bound. sm_100a has no
band, so its routes are unchanged. No program is added or changed. The
only changes are the catalog reader, the catalog policy, the README and
the tests. Logits are bitwise equal on every row of both tables (106/106
on each GPU). The baseline is the previous version, FlashInfer main
35ea8e25aa5a, for the dense MQA paths. On GB300, 2 of the 106 rows run
the updated route, and each is faster in all 3 sessions. `Q 130, K
65792` FP8 goes from 33.31 to 32.42 µs (1.0276). `Q 132, K 65792` FP8
goes from 33.70 to 32.42 µs (1.0409). The other 104 rows run
byte-identical programs in both versions. They read 0.9929–1.0078
(median 1.0000), which is measurement noise. On B200, no row changes
route. All 106 rows run byte-identical programs and read 0.9935–1.0125
(median 1.0000), which is also measurement noise.

**NVIDIA GB300** (sm_103a, 152 SMs), CUDA 13.4 (nvcc V13.4.92,
JIT-compiled), driver 580.159.03, torch 2.14.1+cu130. Previous version =
FlashInfer main 35ea8e25aa5a (dense MQA paths). Timing is CUPTI GPU time
per call with a cold L2. µs is the median over the 3 sessions of each
session's median. Speedup is the median over the sessions of previous /
this (> 1 = faster). Rows that launch more than one kernel per call
report the sum of kernel times. The notation is the same as in #7643. `Q
q, K k` is q queries over k keys. `prefill Q q, prefix p, causal` is q
new queries attending causally over p cached keys plus themselves (K = p
+ q). "2 sequences" and "2048-query chunks" mean the same as in #7643.
"updated" means the row now runs the single-launch `fp8:qle2048:short`
route instead of the two-launch sequence. "same program" means every
program on the row is byte-identical to the previous version.

| shape | dtype | heads | previous µs | this PR µs | speedup | program |
|---|---|---:|---:|---:|---:|---|
| prefill Q 37, prefix 4100, causal | FP8 | 32 | 5.31 | 5.33 | 1.0000 |
same program |
| prefill Q 1024, prefix 32779, causal | FP8 | 32 | 108.13 | 108.16 |
1.0000 | same program |
| prefill Q 1, prefix 0, causal | FP8 | 64 | 3.56 | 3.55 | 1.0023 | same
program |
| prefill Q 1, prefix 4100, causal | FP8 | 64 | 3.74 | 3.74 | 1.0000 |
same program |
| prefill Q 1, prefix 32779, causal | FP8 | 64 | 4.90 | 4.93 | 0.9968 |
same program |
| prefill Q 1, prefix 131077, causal | FP8 | 64 | 7.78 | 7.79 | 1.0000 |
same program |
| prefill Q 2, prefix 0, causal | FP8 | 64 | 3.55 | 3.55 | 1.0000 | same
program |
| prefill Q 2, prefix 4100, causal | FP8 | 64 | 4.35 | 4.35 | 1.0000 |
same program |
| prefill Q 3, prefix 0, causal | FP8 | 64 | 3.62 | 3.62 | 1.0000 | same
program |
| prefill Q 3, prefix 4100, causal | FP8 | 64 | 4.27 | 4.27 | 1.0000 |
same program |
| prefill Q 7, prefix 0, causal | FP8 | 64 | 3.58 | 3.58 | 1.0000 | same
program |
| prefill Q 7, prefix 4100, causal | FP8 | 64 | 4.29 | 4.29 | 1.0000 |
same program |
| prefill Q 8, prefix 0, causal | FP8 | 64 | 3.54 | 3.52 | 1.0000 | same
program |
| prefill Q 8, prefix 4100, causal | FP8 | 64 | 4.38 | 4.38 | 1.0000 |
same program |
| prefill Q 16, prefix 0, causal | FP8 | 64 | 3.55 | 3.55 | 1.0000 |
same program |
| prefill Q 16, prefix 4100, causal | FP8 | 64 | 4.35 | 4.38 | 1.0017 |
same program |
| prefill Q 37, prefix 0, causal | FP8 | 64 | 3.74 | 3.78 | 0.9979 |
same program |
| prefill Q 37, prefix 4100, causal | FP8 | 64 | 5.31 | 5.31 | 1.0000 |
same program |
| prefill Q 37, prefix 32779, causal | FP8 | 64 | 12.56 | 12.56 | 1.0000
| same program |
| prefill Q 37, prefix 131077, causal | FP8 | 64 | 33.98 | 33.98 |
1.0000 | same program |
| prefill Q 64, prefix 0, causal | FP8 | 64 | 3.84 | 3.84 | 1.0000 |
same program |
| prefill Q 64, prefix 4100, causal | FP8 | 64 | 6.05 | 6.05 | 1.0000 |
same program |
| prefill Q 128, prefix 0, causal | FP8 | 64 | 3.94 | 3.94 | 1.0000 |
same program |
| prefill Q 128, prefix 4100, causal | FP8 | 64 | 8.58 | 8.58 | 1.0001 |
same program |
| prefill Q 128, prefix 4100, causal, 2 sequences | FP8 | 64 | 7.46 |
7.47 | 0.9979 | same program |
| prefill Q 128, prefix 32779, causal | FP8 | 64 | 30.27 | 30.22 |
1.0000 | same program |
| prefill Q 128, prefix 131077, causal | FP8 | 64 | 103.17 | 103.14 |
0.9998 | same program |
| prefill Q 129, prefix 0, causal | FP8 | 64 | 3.84 | 3.84 | 1.0000 |
same program |
| prefill Q 129, prefix 4100, causal | FP8 | 64 | 8.56 | 8.54 | 1.0000 |
same program |
| prefill Q 1023, prefix 0, causal | FP8 | 64 | 9.54 | 9.54 | 1.0000 |
same program |
| prefill Q 1023, prefix 4100, causal | FP8 | 64 | 35.60 | 35.60 |
1.0004 | same program |
| prefill Q 1024, prefix 0, causal | FP8 | 64 | 9.60 | 9.58 | 1.0000 |
same program |
| prefill Q 1024, prefix 4100, causal | FP8 | 64 | 35.63 | 35.63 |
1.0000 | same program |
| prefill Q 1024, prefix 32779, causal | FP8 | 64 | 205.10 | 205.12 |
0.9999 | same program |
| prefill Q 1024, prefix 131077, causal | FP8 | 64 | 833.86 | 832.84 |
1.0021 | same program |
| prefill Q 4096, prefix 0, causal | FP8 | 64 | 61.63 | 61.66 | 1.0003 |
same program |
| prefill Q 4096, prefix 4100, causal | FP8 | 64 | 156.34 | 156.37 |
0.9998 | same program |
| prefill Q 4096, prefix 32779, causal | FP8 | 64 | 880.24 | 878.04 |
1.0032 | same program |
| prefill Q 4096, prefix 32779, causal, 2 sequences | FP8 | 64 | 581.73
| 581.22 | 1.0008 | same program |
| prefill Q 4096, prefix 32779, causal, 2048-query chunks | FP8 | 64 |
879.03 | 881.52 | 0.9987 | same program |
| prefill Q 4096, prefix 131077, causal | FP8 | 64 | 3568.18 | 3552.19 |
1.0046 | same program |
| prefill Q 4096, prefix 131077, causal, 2048-query chunks | FP8 | 64 |
3551.74 | 3535.66 | 1.0045 | same program |
| prefill Q 8192, prefix 0, causal | FP8 | 64 | 210.29 | 210.47 | 0.9989
| same program |
| prefill Q 8192, prefix 4100, causal | FP8 | 64 | 408.50 | 408.39 |
1.0016 | same program |
| prefill Q 8192, prefix 32779, causal | FP8 | 64 | 1909.59 | 1907.75 |
1.0078 | same program |
| prefill Q 8192, prefix 32779, causal, 2048-query chunks | FP8 | 64 |
1933.97 | 1934.83 | 0.9992 | same program |
| prefill Q 8192, prefix 131077, causal | FP8 | 64 | 7287.53 | 7258.86 |
1.0040 | same program |
| prefill Q 8192, prefix 131077, causal, 2048-query chunks | FP8 | 64 |
7307.25 | 7307.00 | 0.9998 | same program |
| prefill Q 16231, prefix 0, causal | FP8 | 64 | 835.12 | 835.76 |
0.9992 | same program |
| prefill Q 16231, prefix 4100, causal | FP8 | 64 | 1260.34 | 1261.77 |
0.9971 | same program |
| prefill Q 16231, prefix 32779, causal | FP8 | 64 | 4342.86 | 4340.33 |
1.0004 | same program |
| prefill Q 16231, prefix 32779, causal, 2048-query chunks | FP8 | 64 |
4344.06 | 4352.74 | 0.9990 | same program |
| prefill Q 16231, prefix 131077, causal | FP8 | 64 | 14908.41 |
14884.35 | 1.0016 | same program |
| prefill Q 16231, prefix 131077, causal, 2048-query chunks | FP8 | 64 |
15069.32 | 15068.84 | 1.0000 | same program |
| Q 1, K 4096 | FP8 | 32 | 3.58 | 3.55 | 1.0000 | same program |
| Q 1, K 32768 | FP8 | 32 | 4.58 | 4.58 | 1.0000 | same program |
| Q 1, K 131072 | FP8 | 32 | 7.41 | 7.39 | 1.0022 | same program |
| Q 1, K 1048576 | FP8 | 32 | 30.06 | 30.03 | 0.9995 | same program |
| Q 1, K 1048832 | FP8 | 32 | 29.94 | 29.97 | 0.9989 | same program |
| Q 3, K 8192 | FP8 | 32 | 4.54 | 4.54 | 1.0000 | same program |
| Q 3, K 1048832 | FP8 | 32 | 33.30 | 33.34 | 0.9990 | same program |
| Q 16, K 2048 | FP8 | 32 | 4.54 | 4.54 | 1.0000 | same program |
| Q 16, K 4096 | FP8 | 32 | 4.74 | 4.74 | 1.0000 | same program |
| Q 16, K 32768 | FP8 | 32 | 7.20 | 7.17 | 1.0045 | same program |
| Q 16, K 131072 | FP8 | 32 | 13.39 | 13.38 | 0.9988 | same program |
| Q 16, K 1048576 | FP8 | 32 | 58.64 | 58.71 | 0.9991 | same program |
| Q 16, K 1048832 | FP8 | 32 | 59.33 | 59.37 | 0.9996 | same program |
| Q 33, K 8192 | FP8 | 32 | 5.38 | 5.38 | 1.0000 | same program |
| Q 33, K 1048832 | FP8 | 32 | 176.96 | 176.46 | 1.0032 | same program |
| Q 37, K 4137 | FP8 | 32 | 5.31 | 5.31 | 1.0000 | same program |
| Q 128, K 2048 | FP8 | 32 | 5.86 | 5.86 | 1.0000 | same program |
| Q 128, K 4096 | FP8 | 32 | 6.98 | 6.98 | 1.0000 | same program |
| Q 128, K 32768 | FP8 | 32 | 18.31 | 18.34 | 1.0000 | same program |
| Q 128, K 131072 | FP8 | 32 | 53.60 | 53.58 | 0.9994 | same program |
| Q 128, K 131328 | FP8 | 32 | 55.14 | 55.10 | 1.0003 | same program |
| Q 130, K 8192 | FP8 | 32 | 9.50 | 9.50 | 1.0000 | same program |
| Q 130, K 8448 | FP8 | 32 | 9.82 | 9.82 | 1.0000 | same program |
| Q 130, K 65792 | FP8 | 32 | 33.31 | 32.42 | 1.0276 | updated |
| Q 132, K 2048 | FP8 | 32 | 6.43 | 6.43 | 1.0000 | same program |
| Q 132, K 8448 | FP8 | 32 | 9.74 | 9.73 | 1.0000 | same program |
| Q 132, K 65792 | FP8 | 32 | 33.70 | 32.42 | 1.0409 | updated |
| Q 1024, K 33803 | FP8 | 32 | 109.90 | 110.00 | 0.9996 | same program |
| Q 2052, K 2048 | FP8 | 32 | 20.99 | 20.98 | 1.0000 | same program |
| Q 2052, K 8448 | FP8 | 32 | 60.75 | 60.83 | 0.9987 | same program |
| Q 2053, K 2048 | FP8 | 32 | 21.42 | 21.41 | 1.0008 | same program |
| Q 2053, K 8448 | FP8 | 32 | 61.18 | 61.18 | 0.9984 | same program |
| Q 1, K 4096 | FP4 | 32 | 3.79 | 3.79 | 1.0000 | same program |
| Q 1, K 32768 | FP4 | 32 | 4.48 | 4.48 | 0.9929 | same program |
| Q 1, K 131072 | FP4 | 32 | 6.37 | 6.37 | 1.0000 | same program |
| Q 1, K 131328 | FP4 | 32 | 6.61 | 6.62 | 1.0024 | same program |
| Q 7, K 2048 | FP4 | 32 | 4.37 | 4.37 | 1.0000 | same program |
| Q 16, K 4096 | FP4 | 32 | 4.86 | 4.86 | 1.0000 | same program |
| Q 16, K 32768 | FP4 | 32 | 6.69 | 6.69 | 1.0000 | same program |
| Q 16, K 131072 | FP4 | 32 | 11.92 | 11.92 | 0.9974 | same program |
| Q 16, K 1048576 | FP4 | 32 | 54.14 | 54.16 | 1.0000 | same program |
| Q 16, K 1048832 | FP4 | 32 | 53.98 | 53.98 | 0.9997 | same program |
| Q 33, K 8192 | FP4 | 32 | 5.52 | 5.54 | 1.0000 | same program |
| Q 33, K 1048832 | FP4 | 32 | 118.42 | 118.42 | 1.0001 | same program |
| Q 128, K 4096 | FP4 | 32 | 6.40 | 6.40 | 1.0000 | same program |
| Q 128, K 32768 | FP4 | 32 | 17.07 | 17.06 | 1.0000 | same program |
| Q 128, K 131072 | FP4 | 32 | 52.78 | 52.78 | 1.0000 | same program |
| Q 130, K 65536 | FP4 | 32 | 30.58 | 30.59 | 0.9995 | same program |
| Q 130, K 65792 | FP4 | 32 | 30.72 | 30.72 | 1.0005 | same program |
| Q 1024, K 2048 | FP4 | 32 | 13.95 | 13.97 | 0.9977 | same program |
| Q 2052, K 2048 | FP4 | 32 | 21.63 | 21.63 | 0.9978 | same program |
| Q 2052, K 65792 | FP4 | 32 | 393.91 | 394.00 | 0.9998 | same program |

**NVIDIA B200** (sm_100a, 148 SMs), CUDA 13.4 (nvcc V13.4.92,
JIT-compiled), driver 580.82.07, torch 2.14.1+cu130. Previous version =
FlashInfer main 35ea8e25aa5a (dense MQA paths). Timing, notation and the
labels are the same as in the GB300 table.

| shape | dtype | heads | previous µs | this PR µs | speedup | program |
|---|---|---:|---:|---:|---:|---|
| prefill Q 37, prefix 4100, causal | FP8 | 32 | 5.28 | 5.28 | 1.0000 |
same program |
| prefill Q 1024, prefix 32779, causal | FP8 | 32 | 135.82 | 135.63 |
1.0014 | same program |
| prefill Q 1, prefix 0, causal | FP8 | 64 | 4.10 | 4.10 | 1.0001 | same
program |
| prefill Q 1, prefix 4100, causal | FP8 | 64 | 4.10 | 4.10 | 1.0000 |
same program |
| prefill Q 1, prefix 32779, causal | FP8 | 64 | 5.15 | 5.15 | 1.0000 |
same program |
| prefill Q 1, prefix 131077, causal | FP8 | 64 | 8.06 | 8.06 | 1.0000 |
same program |
| prefill Q 2, prefix 0, causal | FP8 | 64 | 4.08 | 4.08 | 1.0001 | same
program |
| prefill Q 2, prefix 4100, causal | FP8 | 64 | 4.77 | 4.77 | 1.0000 |
same program |
| prefill Q 3, prefix 0, causal | FP8 | 64 | 3.88 | 3.88 | 1.0001 | same
program |
| prefill Q 3, prefix 4100, causal | FP8 | 64 | 4.59 | 4.58 | 1.0001 |
same program |
| prefill Q 7, prefix 0, causal | FP8 | 64 | 3.90 | 3.90 | 1.0000 | same
program |
| prefill Q 7, prefix 4100, causal | FP8 | 64 | 4.53 | 4.53 | 1.0001 |
same program |
| prefill Q 8, prefix 0, causal | FP8 | 64 | 3.90 | 3.90 | 0.9980 | same
program |
| prefill Q 8, prefix 4100, causal | FP8 | 64 | 4.61 | 4.61 | 1.0000 |
same program |
| prefill Q 16, prefix 0, causal | FP8 | 64 | 3.90 | 3.89 | 1.0001 |
same program |
| prefill Q 16, prefix 4100, causal | FP8 | 64 | 4.58 | 4.58 | 1.0000 |
same program |
| prefill Q 37, prefix 0, causal | FP8 | 64 | 3.94 | 3.94 | 1.0000 |
same program |
| prefill Q 37, prefix 4100, causal | FP8 | 64 | 5.63 | 5.63 | 1.0000 |
same program |
| prefill Q 37, prefix 32779, causal | FP8 | 64 | 14.34 | 14.32 | 1.0000
| same program |
| prefill Q 37, prefix 131077, causal | FP8 | 64 | 40.22 | 40.24 |
0.9996 | same program |
| prefill Q 64, prefix 0, causal | FP8 | 64 | 3.97 | 3.95 | 1.0000 |
same program |
| prefill Q 64, prefix 4100, causal | FP8 | 64 | 6.62 | 6.61 | 1.0023 |
same program |
| prefill Q 128, prefix 0, causal | FP8 | 64 | 4.11 | 4.10 | 1.0002 |
same program |
| prefill Q 128, prefix 4100, causal | FP8 | 64 | 9.34 | 9.34 | 1.0000 |
same program |
| prefill Q 128, prefix 4100, causal, 2 sequences | FP8 | 64 | 8.22 |
8.21 | 1.0019 | same program |
| prefill Q 128, prefix 32779, causal | FP8 | 64 | 34.59 | 34.67 |
0.9991 | same program |
| prefill Q 128, prefix 131077, causal | FP8 | 64 | 123.39 | 123.30 |
1.0001 | same program |
| prefill Q 129, prefix 0, causal | FP8 | 64 | 4.13 | 4.13 | 1.0000 |
same program |
| prefill Q 129, prefix 4100, causal | FP8 | 64 | 9.28 | 9.26 | 1.0017 |
same program |
| prefill Q 1023, prefix 0, causal | FP8 | 64 | 10.37 | 10.40 | 1.0000 |
same program |
| prefill Q 1023, prefix 4100, causal | FP8 | 64 | 40.67 | 40.67 |
1.0000 | same program |
| prefill Q 1024, prefix 0, causal | FP8 | 64 | 10.48 | 10.45 | 1.0015 |
same program |
| prefill Q 1024, prefix 4100, causal | FP8 | 64 | 40.50 | 40.50 |
1.0004 | same program |
| prefill Q 1024, prefix 32779, causal | FP8 | 64 | 260.36 | 259.78 |
1.0022 | same program |
| prefill Q 1024, prefix 131077, causal | FP8 | 64 | 1056.78 | 1056.90 |
0.9999 | same program |
| prefill Q 4096, prefix 0, causal | FP8 | 64 | 70.13 | 70.19 | 0.9991 |
same program |
| prefill Q 4096, prefix 4100, causal | FP8 | 64 | 199.55 | 196.90 |
1.0104 | same program |
| prefill Q 4096, prefix 32779, causal | FP8 | 64 | 1132.61 | 1114.42 |
1.0125 | same program |
| prefill Q 4096, prefix 32779, causal, 2 sequences | FP8 | 64 | 783.98
| 782.95 | 1.0020 | same program |
| prefill Q 4096, prefix 32779, causal, 2048-query chunks | FP8 | 64 |
1127.11 | 1127.43 | 0.9994 | same program |
| prefill Q 4096, prefix 131077, causal | FP8 | 64 | 4370.19 | 4369.79 |
1.0002 | same program |
| prefill Q 4096, prefix 131077, causal, 2048-query chunks | FP8 | 64 |
4356.56 | 4355.84 | 1.0003 | same program |
| prefill Q 8192, prefix 0, causal | FP8 | 64 | 277.20 | 276.99 | 1.0008
| same program |
| prefill Q 8192, prefix 4100, causal | FP8 | 64 | 547.78 | 547.58 |
0.9986 | same program |
| prefill Q 8192, prefix 32779, causal | FP8 | 64 | 2442.40 | 2441.69 |
1.0003 | same program |
| prefill Q 8192, prefix 32779, causal, 2048-query chunks | FP8 | 64 |
2426.45 | 2422.81 | 1.0003 | same program |
| prefill Q 8192, prefix 131077, causal | FP8 | 64 | 8985.93 | 8983.98 |
1.0000 | same program |
| prefill Q 8192, prefix 131077, causal, 2048-query chunks | FP8 | 64 |
8949.04 | 8924.31 | 1.0007 | same program |
| prefill Q 16231, prefix 0, causal | FP8 | 64 | 1079.51 | 1080.46 |
0.9997 | same program |
| prefill Q 16231, prefix 4100, causal | FP8 | 64 | 1629.13 | 1622.66 |
1.0049 | same program |
| prefill Q 16231, prefix 32779, causal | FP8 | 64 | 5369.70 | 5370.32 |
1.0000 | same program |
| prefill Q 16231, prefix 32779, causal, 2048-query chunks | FP8 | 64 |
5431.14 | 5428.40 | 1.0013 | same program |
| prefill Q 16231, prefix 131077, causal | FP8 | 64 | 18297.08 |
18313.68 | 1.0002 | same program |
| prefill Q 16231, prefix 131077, causal, 2048-query chunks | FP8 | 64 |
18319.63 | 18252.60 | 1.0003 | same program |
| Q 1, K 4096 | FP8 | 32 | 3.94 | 3.94 | 1.0000 | same program |
| Q 1, K 32768 | FP8 | 32 | 4.85 | 4.83 | 1.0000 | same program |
| Q 1, K 131072 | FP8 | 32 | 7.74 | 7.74 | 1.0000 | same program |
| Q 1, K 1048576 | FP8 | 32 | 31.13 | 31.14 | 0.9992 | same program |
| Q 1, K 1048832 | FP8 | 32 | 31.10 | 31.08 | 1.0010 | same program |
| Q 3, K 8192 | FP8 | 32 | 4.83 | 4.83 | 1.0000 | same program |
| Q 3, K 1048832 | FP8 | 32 | 34.91 | 34.98 | 0.9982 | same program |
| Q 16, K 2048 | FP8 | 32 | 4.61 | 4.59 | 1.0000 | same program |
| Q 16, K 4096 | FP8 | 32 | 4.70 | 4.70 | 1.0000 | same program |
| Q 16, K 32768 | FP8 | 32 | 7.87 | 7.90 | 1.0020 | same program |
| Q 16, K 131072 | FP8 | 32 | 14.82 | 14.82 | 1.0000 | same program |
| Q 16, K 1048576 | FP8 | 32 | 69.92 | 69.88 | 1.0018 | same program |
| Q 16, K 1048832 | FP8 | 32 | 70.43 | 70.26 | 1.0024 | same program |
| Q 33, K 8192 | FP8 | 32 | 5.54 | 5.54 | 1.0000 | same program |
| Q 33, K 1048832 | FP8 | 32 | 191.38 | 191.09 | 1.0016 | same program |
| Q 37, K 4137 | FP8 | 32 | 5.25 | 5.25 | 1.0000 | same program |
| Q 128, K 2048 | FP8 | 32 | 6.19 | 6.19 | 0.9999 | same program |
| Q 128, K 4096 | FP8 | 32 | 7.46 | 7.46 | 1.0021 | same program |
| Q 128, K 32768 | FP8 | 32 | 21.33 | 21.28 | 1.0000 | same program |
| Q 128, K 131072 | FP8 | 32 | 64.45 | 64.45 | 1.0002 | same program |
| Q 128, K 131328 | FP8 | 32 | 64.48 | 64.48 | 1.0000 | same program |
| Q 130, K 8192 | FP8 | 32 | 10.53 | 10.53 | 1.0000 | same program |
| Q 130, K 8448 | FP8 | 32 | 10.66 | 10.66 | 1.0000 | same program |
| Q 130, K 65792 | FP8 | 32 | 39.17 | 39.09 | 0.9996 | same program |
| Q 132, K 2048 | FP8 | 32 | 6.80 | 6.80 | 1.0000 | same program |
| Q 132, K 8448 | FP8 | 32 | 10.53 | 10.51 | 1.0015 | same program |
| Q 132, K 65792 | FP8 | 32 | 39.65 | 39.62 | 0.9996 | same program |
| Q 1024, K 33803 | FP8 | 32 | 136.94 | 137.25 | 0.9995 | same program |
| Q 2052, K 2048 | FP8 | 32 | 23.78 | 23.81 | 1.0000 | same program |
| Q 2052, K 8448 | FP8 | 32 | 70.78 | 70.74 | 1.0016 | same program |
| Q 2053, K 2048 | FP8 | 32 | 24.21 | 24.16 | 0.9993 | same program |
| Q 2053, K 8448 | FP8 | 32 | 71.34 | 71.34 | 1.0041 | same program |
| Q 1, K 4096 | FP4 | 32 | 3.97 | 3.97 | 1.0001 | same program |
| Q 1, K 32768 | FP4 | 32 | 4.75 | 4.75 | 1.0000 | same program |
| Q 1, K 131072 | FP4 | 32 | 6.53 | 6.51 | 1.0025 | same program |
| Q 1, K 131328 | FP4 | 32 | 6.78 | 6.78 | 1.0000 | same program |
| Q 7, K 2048 | FP4 | 32 | 4.90 | 4.93 | 0.9935 | same program |
| Q 16, K 4096 | FP4 | 32 | 5.36 | 5.36 | 1.0001 | same program |
| Q 16, K 32768 | FP4 | 32 | 7.36 | 7.34 | 1.0000 | same program |
| Q 16, K 131072 | FP4 | 32 | 13.71 | 13.73 | 0.9989 | same program |
| Q 16, K 1048576 | FP4 | 32 | 63.41 | 63.41 | 1.0000 | same program |
| Q 16, K 1048832 | FP4 | 32 | 66.77 | 66.58 | 1.0043 | same program |
| Q 33, K 8192 | FP4 | 32 | 5.98 | 5.98 | 1.0000 | same program |
| Q 33, K 1048832 | FP4 | 32 | 136.19 | 136.62 | 0.9995 | same program |
| Q 128, K 4096 | FP4 | 32 | 6.94 | 6.94 | 1.0000 | same program |
| Q 128, K 32768 | FP4 | 32 | 19.89 | 19.89 | 1.0000 | same program |
| Q 128, K 131072 | FP4 | 32 | 61.76 | 61.74 | 1.0003 | same program |
| Q 130, K 65536 | FP4 | 32 | 35.87 | 35.87 | 0.9996 | same program |
| Q 130, K 65792 | FP4 | 32 | 38.19 | 38.08 | 0.9992 | same program |
| Q 1024, K 2048 | FP4 | 32 | 14.30 | 14.42 | 0.9955 | same program |
| Q 2052, K 2048 | FP4 | 32 | 24.06 | 24.00 | 1.0014 | same program |
| Q 2052, K 65792 | FP4 | 32 | 463.43 | 461.30 | 1.0046 | same program |

The family's other Cake variants (dense FP8 with 64 heads, dense FP4
with 32 heads including fused metadata + logits sequences, and paged
FP8) ship on sm_100a and sm_103a only.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Improvements**
* Updated fused FP8 routing to support a larger key/value range for
small query counts on supported architectures. The applicable limits
vary by architecture; one retains its existing query range without the
extension.
* **Documentation**
* Clarified the architecture-specific query and key/value limits for the
fused route.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery Huang <averyh@nvidia.com>

### [f0a12f2](https://github.com/flashinfer-ai/flashinfer/commit/f0a12f29a0e1c02008115132bbcfa2142f75c06e)

- **作者**: eigen
- **时间**: 2026-10-31T23:19:36Z
- **提交信息**: perf(cake_fused_qk_rope_append, cake_fused_qk_rope_fp8_append): faster enable_pdl=True decode launches on sm_100a/sm_103a (#8149)

The Cake fused QK RMSNorm + NeoX RoPE + paged KV-cache append kernel has
two variants. They are BF16 (`cake_fused_qk_rope_append`) and FP8 E4M3
(`cake_fused_qk_rope_fp8_append`). #8112 added `enable_pdl`, which uses
programmatic dependent launch behind the QKV projection GEMM. This PR
changes only the `enable_pdl=True` path on sm_100a and sm_103a.
`enable_pdl=False` selects exactly the existing builds. The kernels are
unchanged, and outputs are bitwise identical to `enable_pdl=False`. With
`enable_pdl=True`, three launch choices change. FP8 8/1 decode in the
clearing class now takes the page-prefetch PDL build. On GB300 it does
so only where that build was faster. Both page-prefetch PDL builds now
launch with a per-call CTA cap. When the grid needs k >= 2 CTAs per SM,
the call uses the smallest dynamic shared memory that limits the kernel
to k CTAs per SM. CTAs that start while the GEMM is still running then
no longer pile up on the SMs it has already left. This replaces the 8/1
decode request window where PDL was off. That window began at 129
(B200), 177 (GB200) or 187 (B300, GB300) requests. BF16 8/1 decode with
pages of at most 64 entries and fewer than 1792 clearing CTAs takes the
one-unit-per-warp PDL build. BF16 PDL stays off at 512 requests. The
baseline is FlashInfer main, which includes #8112, with
`enable_pdl=True` on both sides. Every changed row is faster, and its 95
% bootstrap CI of the ratio excludes 1 in all 3 sessions. Geomean
speedups over changed rows on B200, GB200, B300 and GB300 are as
follows. FP8 representative rows: 1.070x to 1.089x, with 8 to 12 of 44
rows changed. FP8 sweep rows: 1.115x to 1.141x. BF16 sweep rows: 1.046x
to 1.056x. No BF16 representative row changes. On changed rows, per-row
speedups range from 1.004x to 1.227x.

Each row times one step of QKV projection GEMM followed by this kernel.
The producer is BF16 `torch.mm(x, W, out=qkv)` (cuBLAS), with x [T,
Hq*128] and W [Hq*128, (Hq+2*Hkv)*128]. Each side runs one CUDA graph of
8 x [L2 flush, GEMM, fused kernel]. Each event-timed slot covers 8
replays. The two sides alternate in ABBA cycles with rotated arm order,
across 3 fresh-process sessions. The L2-flush time is subtracted. Each
value is therefore the GEMM plus fused-kernel time per step, in µs.
FlashInfer's JIT builds both packages with CUDA 13.4 and PyTorch
2.14.1+cu130. Both run through the public API on the same GPU in one
process. The GPUs are B200 (sm_100a, 148 SMs), GB200 (sm_100a, 152 SMs),
B300 (sm_103a, 148 SMs) and GB300 (sm_103a, 152 SMs). Speedup is main /
this PR. The "launch" column says "changed" or "same". "same" rows run
the same launch as main, so their ratios only show measurement spread.
Row names: `64x8`/`8x1` are query/KV heads (head_dim 128). `q1`/`q2`
mean Q is quantized with a dynamic per-token/per-head scale (`q1`) or a
static scale (`q2`). `n0`/`n1`/`n2` mean no RMSNorm, RoPE then RMSNorm,
or RMSNorm then RoPE. `P_decode` is 32 requests x 1 new token and
`P_prefill` is 8 requests x 16 new tokens, with 2048 cached tokens and
page size 64 unless the name says otherwise.
`E_prefill_*_q127/q128/q129` is 4 requests x 127/128/129 new tokens,
which is the 128-row scale-padding boundary. In `X_*` rows,
`B1`/`B128`/`B256` = 1/128/256 requests, `Q1024` = 1024 new tokens,
`page16`/`page128` = page size 16/128, `ctx32768` = 32768 cached tokens,
`outkv` = caller-owned `out_k`/`out_v`, `ragged` = 8 requests with
ragged new-token counts, and `maxseq1024` = 8 requests x 16 new tokens
with max_seqlen 1024. In sweep rows, `S<hq>x<hkv>_B<n>` is decode with n
requests x 1 new token, 2048 cached tokens and page size 64.
`R3_p<page>_B<n>` is 8/1 decode with page size `<page>`.
`R3_prefill_B<n>_Q<q>` is 8/1 prefill. BF16 rows and sweep rows carry
their geometry in the shape column.

This PR covers both Cake variants; the family ships on sm_90a, sm_100a
and sm_103a, but the PDL path exists only on sm_100a and sm_103a.

**NVIDIA B200, sm_100a (148 SMs), CUDA 13.4. Speedup = FlashInfer main /
this PR, both with `enable_pdl=True`.**


FP8 E4M3 (`cake_fused_qk_rope_fp8_append`)

| shape | launch | FlashInfer main (µs) | this PR (µs) | speedup |
|---|---|---:|---:|---:|
| `P_decode_8x1_q1_n0` | same | 5.096 | 5.088 | 1.0016 |
| `P_decode_8x1_q1_n1` | same | 5.333 | 5.271 | 1.0118 |
| `P_decode_8x1_q1_n2` | same | 5.879 | 5.920 | 0.9931 |
| `P_decode_8x1_q2_n0` | same | 5.712 | 5.696 | 1.0028 |
| `P_decode_8x1_q2_n1` | same | 5.174 | 5.141 | 1.0064 |
| `P_decode_8x1_q2_n2` | same | 5.184 | 5.184 | 1.0000 |
| `P_decode_64x8_q1_n0` | same | 40.637 | 40.679 | 0.9990 |
| `P_decode_64x8_q1_n1` | same | 40.967 | 40.704 | 1.0065 |
| `P_decode_64x8_q1_n2` | same | 40.657 | 40.664 | 0.9998 |
| `P_decode_64x8_q2_n0` | same | 40.872 | 40.688 | 1.0045 |
| `P_decode_64x8_q2_n1` | same | 40.561 | 40.591 | 0.9993 |
| `P_decode_64x8_q2_n2` | same | 40.919 | 40.782 | 1.0034 |
| `P_prefill_8x1_q1_n0` | same | 5.447 | 5.472 | 0.9954 |
| `P_prefill_8x1_q1_n1` | same | 5.727 | 5.712 | 1.0026 |
| `P_prefill_8x1_q1_n2` | same | 5.696 | 5.696 | 1.0000 |
| `P_prefill_8x1_q2_n0` | same | 5.357 | 5.356 | 1.0002 |
| `P_prefill_8x1_q2_n1` | same | 5.504 | 5.472 | 1.0058 |
| `P_prefill_8x1_q2_n2` | same | 5.631 | 5.600 | 1.0055 |
| `P_prefill_64x8_q1_n0` | same | 43.288 | 43.297 | 0.9998 |
| `P_prefill_64x8_q1_n1` | same | 43.678 | 43.600 | 1.0018 |
| `P_prefill_64x8_q1_n2` | same | 43.576 | 43.647 | 0.9984 |
| `P_prefill_64x8_q2_n0` | same | 43.351 | 43.288 | 1.0015 |
| `P_prefill_64x8_q2_n1` | same | 43.486 | 43.519 | 0.9992 |
| `P_prefill_64x8_q2_n2` | same | 43.569 | 43.528 | 1.0009 |
| `E_prefill_8x1_q127` | changed | 7.504 | 6.656 | 1.1274 |
| `E_prefill_8x1_q128` | changed | 7.648 | 6.719 | 1.1383 |
| `E_prefill_8x1_q129` | changed | 7.568 | 6.718 | 1.1265 |
| `E_prefill_64x8_q127` | same | 72.632 | 72.688 | 0.9992 |
| `E_prefill_64x8_q128` | same | 72.831 | 72.823 | 1.0001 |
| `E_prefill_64x8_q129` | same | 79.897 | 79.928 | 0.9996 |
| `X_decode_8x1_B1_q1_n2` | same | 5.117 | 5.121 | 0.9992 |
| `X_decode_8x1_B128_q1_n2` | same | 6.455 | 6.447 | 1.0012 |
| `X_decode_8x1_B256_q1_n2` | changed | 8.031 | 6.933 | 1.1584 |
| `X_prefill_8x1_B1_Q1024_q1_n2` | changed | 8.944 | 8.480 | 1.0547 |
| `X_decode_64x8_B1_q1_n2` | same | 39.358 | 39.312 | 1.0012 |
| `X_decode_64x8_B128_q1_n2` | same | 46.512 | 46.495 | 1.0004 |
| `X_decode_64x8_B256_q1_n2` | same | 56.641 | 56.609 | 1.0006 |
| `X_prefill_64x8_B1_Q1024_q1_n2` | same | 151.586 | 151.890 | 0.9980 |
| `X_decode_8x1_q1_n2_page16` | changed | 5.663 | 5.464 | 1.0364 |
| `X_decode_8x1_q1_n2_page128` | same | 5.280 | 5.216 | 1.0123 |
| `X_decode_8x1_q1_n2_ctx32768` | changed | 5.632 | 5.439 | 1.0355 |
| `X_prefill_8x1_ragged_q1_n2` | same | 6.113 | 6.112 | 1.0002 |
| `X_decode_8x1_q1_n2_outkv` | changed | 5.472 | 5.312 | 1.0301 |
| `X_prefill_8x1_q1_n2_maxseq1024` | same | 5.783 | 5.727 | 1.0098 |

FP8 E4M3 (`cake_fused_qk_rope_fp8_append`), request-count and page-size
sweep

| shape | launch | FlashInfer main (µs) | this PR (µs) | speedup |
|---|---|---:|---:|---:|
| `S8x1_B129` 8/1 decode, 129 req x 1 new, ctx 2048, page 64 | changed |
7.233 | 6.369 | 1.1357 |
| `S8x1_B136` 8/1 decode, 136 req x 1 new, ctx 2048, page 64 | changed |
7.256 | 6.336 | 1.1452 |
| `S8x1_B148` 8/1 decode, 148 req x 1 new, ctx 2048, page 64 | changed |
8.141 | 6.784 | 1.2000 |
| `S8x1_B160` 8/1 decode, 160 req x 1 new, ctx 2048, page 64 | changed |
8.063 | 6.570 | 1.2272 |
| `S8x1_B176` 8/1 decode, 176 req x 1 new, ctx 2048, page 64 | changed |
7.614 | 6.632 | 1.1481 |
| `S8x1_B177` 8/1 decode, 177 req x 1 new, ctx 2048, page 64 | changed |
7.615 | 6.582 | 1.1569 |
| `S8x1_B187` 8/1 decode, 187 req x 1 new, ctx 2048, page 64 | changed |
7.677 | 6.709 | 1.1443 |
| `S8x1_B188` 8/1 decode, 188 req x 1 new, ctx 2048, page 64 | changed |
7.680 | 6.606 | 1.1626 |
| `S8x1_B200` 8/1 decode, 200 req x 1 new, ctx 2048, page 64 | changed |
7.679 | 6.606 | 1.1624 |
| `S8x1_B223` 8/1 decode, 223 req x 1 new, ctx 2048, page 64 | changed |
7.760 | 6.672 | 1.1631 |
| `S8x1_B224` 8/1 decode, 224 req x 1 new, ctx 2048, page 64 | changed |
7.641 | 6.656 | 1.1480 |
| `S8x1_B256` 8/1 decode, 256 req x 1 new, ctx 2048, page 64 | changed |
8.137 | 7.073 | 1.1504 |
| `S8x1_B384` 8/1 decode, 384 req x 1 new, ctx 2048, page 64 | changed |
8.609 | 7.936 | 1.0848 |
| `S8x1_B512` 8/1 decode, 512 req x 1 new, ctx 2048, page 64 | changed |
9.248 | 8.944 | 1.0340 |
| `R3_prefill_B2_Q100` 8/1 prefill, 2 req x 100 new | changed | 6.911 |
6.208 | 1.1132 |
| `R3_prefill_B3_Q120` 8/1 prefill, 3 req x 120 new | changed | 7.169 |
6.593 | 1.0874 |

BF16 (`cake_fused_qk_rope_append`)

| shape | launch | FlashInfer main (µs) | this PR (µs) | speedup |
|---|---|---:|---:|---:|
| `M1` 8/1, 32 req x 1 new, ctx 2048, page 64, n2 | same | 5.313 | 5.281
| 1.0061 |
| `M1a` 8/1, 32 req x 1 new, ctx 2048, page 64, n0 | same | 5.376 |
5.360 | 1.0030 |
| `M1b` 8/1, 32 req x 1 new, ctx 2048, page 64, n1 | same | 5.759 |
5.783 | 0.9958 |
| `M2` 8/1, 8 req x 16 new, ctx 2048, page 64, n2 | same | 6.047 | 6.077
| 0.9951 |
| `M2a` 8/1, 8 req x 16 new, ctx 2048, page 64, n0 | same | 5.696 |
5.665 | 1.0055 |
| `M2b` 8/1, 8 req x 16 new, ctx 2048, page 64, n1 | same | 5.824 |
5.823 | 1.0002 |
| `H1` 64/8, 32 req x 1 new, ctx 2048, page 64, n2 | same | 11.416 |
11.424 | 0.9993 |
| `H2` 64/8, 8 req x 16 new, ctx 2048, page 64, n2 | same | 12.352 |
12.350 | 1.0002 |
| `H3` 64/8, 128 req x 1 new, ctx 2048, page 64, n2 | same | 12.624 |
12.610 | 1.0011 |
| `H4` 64/8, 1 req x 128 new, ctx 2048, page 64, n2 | same | 12.384 |
12.400 | 0.9987 |
| `D1` 8/1, 1 req x 1 new, ctx 2048, page 64, n2 | same | 5.151 | 5.120
| 1.0061 |
| `D2` 8/1, 8 req x 1 new, ctx 2048, page 64, n2 | same | 5.130 | 5.120
| 1.0020 |
| `D3` 8/1, 128 req x 1 new, ctx 2048, page 64, n2 | same | 6.400 |
6.365 | 1.0055 |
| `D4` 8/1, 256 req x 1 new, ctx 2048, page 64, n2 | same | 7.145 |
7.168 | 0.9968 |
| `P1` 8/1, 1 req x 128 new, ctx 2048, page 64, n2 | same | 5.596 |
5.620 | 0.9957 |
| `P2` 8/1, 4 req x 64 new, ctx 2048, page 64, n2 | same | 5.792 | 5.824
| 0.9945 |
| `P3` 8/1, 32 req x 8 new, ctx 2048, page 64, n2 | same | 6.222 | 6.159
| 1.0102 |
| `E1` 8/1, 32 req x 1 new, ctx 2048, page 16, n2 | same | 4.928 | 4.912
| 1.0033 |
| `E2` 8/1, 32 req x 1 new, ctx 2048, page 128, n2 | same | 5.601 |
5.559 | 1.0076 |
| `E3` 8/1, 32 req x 1 new, ctx 0, page 64, n2 | same | 5.215 | 5.217 |
0.9996 |
| `E4` 8/1, 8 req x 16 new, ctx 2047, page 64, n2 | same | 5.696 | 5.665
| 1.0055 |
| `E5` 8/1, 32 req x 1 new, ctx 2048, page 64, n2, outkv | same | 5.392
| 5.408 | 0.9970 |
| `E6` 8/1, 16 req ragged (1-64 new, 0-4095 cached), page 64, n2 | same
| 6.241 | 6.239 | 1.0003 |
| `X1` 8/1, 32 req x 1 new, ctx 32768, page 64, n2 | same | 5.374 |
5.344 | 1.0056 |
| `X2` 8/1, 512 req x 1 new, ctx 2048, page 64, n2 | same | 9.058 |
9.061 | 0.9997 |
| `X3` 64/8, 32 req x 1 new, ctx 2048, page 64, n0 | same | 11.136 |
11.184 | 0.9957 |
| `X4` 64/8, 32 req x 1 new, ctx 2048, page 64, n1 | same | 11.288 |
11.296 | 0.9993 |
| `X5` 8/1, 32 req x 1 new, ctx 2048, page 32, n2 | same | 5.120 | 5.071
| 1.0097 |

BF16 (`cake_fused_qk_rope_append`), request-count and page-size sweep

| shape | launch | FlashInfer main (µs) | this PR (µs) | speedup |
|---|---|---:|---:|---:|
| `S8x1_B512` 8/1 decode, 512 req x 1 new, ctx 2048, page 64 | same |
9.252 | 9.249 | 1.0003 |
| `S8x1_B513` 8/1 decode, 513 req x 1 new, ctx 2048, page 64 | changed |
9.281 | 9.213 | 1.0074 |
| `S8x1_B514` 8/1 decode, 514 req x 1 new, ctx 2048, page 64 | changed |
9.999 | 9.599 | 1.0417 |
| `S8x1_B547` 8/1 decode, 547 req x 1 new, ctx 2048, page 64 | changed |
10.788 | 9.793 | 1.1016 |
| `S8x1_B640` 8/1 decode, 640 req x 1 new, ctx 2048, page 64 | changed |
10.304 | 9.919 | 1.0388 |
| `S8x1_B768` 8/1 decode, 768 req x 1 new, ctx 2048, page 64 | changed |
11.919 | 11.134 | 1.0705 |
| `S8x1_B896` 8/1 decode, 896 req x 1 new, ctx 2048, page 64 | same |
12.080 | 12.066 | 1.0012 |
| `S8x1_B960` 8/1 decode, 960 req x 1 new, ctx 2048, page 64 | same |
12.608 | 12.616 | 0.9994 |
| `S8x1_B1024` 8/1 decode, 1024 req x 1 new, ctx 2048, page 64 | same |
13.088 | 13.072 | 1.0012 |
| `R3_p64_B880` 8/1 decode, 880 req x 1 new, ctx 2048, page 64 | changed
| 12.105 | 11.680 | 1.0364 |
| `R3_p128_B384` 8/1 decode, 384 req x 1 new, ctx 2048, page 128 | same
| 9.513 | 9.568 | 0.9943 |
| `R3_p128_B512` 8/1 decode, 512 req x 1 new, ctx 2048, page 128 | same
| 12.405 | 12.378 | 1.0022 |
| `R3_p16_B2048` 8/1 decode, 2048 req x 1 new, ctx 2048, page 16 |
changed | 15.967 | 14.928 | 1.0696 |
| `R3_p16_B3500` 8/1 decode, 3500 req x 1 new, ctx 2048, page 16 |
changed | 22.532 | 22.032 | 1.0227 |
| `R3_p32_B1024` 8/1 decode, 1024 req x 1 new, ctx 2048, page 32 |
changed | 12.160 | 11.022 | 1.1032 |
| `R3_p32_B1536` 8/1 decode, 1536 req x 1 new, ctx 2048, page 32 |
changed | 14.863 | 13.897 | 1.0695 |
| `R3_p32_B1792` 8/1 decode, 1792 req x 1 new, ctx 2048, page 32 | same
| 15.872 | 15.934 | 0.9961 |

**NVIDIA GB200, sm_100a (152 SMs), CUDA 13.4. Speedup = FlashInfer main
/ this PR, both with `enable_pdl=True`.**


FP8 E4M3 (`cake_fused_qk_rope_fp8_append`)

| shape | launch | FlashInfer main (µs) | this PR (µs) | speedup |
|---|---|---:|---:|---:|
| `P_decode_8x1_q1_n0` | same | 4.945 | 4.992 | 0.9906 |
| `P_decode_8x1_q1_n1` | same | 5.080 | 5.128 | 0.9906 |
| `P_decode_8x1_q1_n2` | same | 5.713 | 5.697 | 1.0028 |
| `P_decode_8x1_q2_n0` | same | 5.568 | 5.567 | 1.0002 |
| `P_decode_8x1_q2_n1` | same | 4.905 | 4.920 | 0.9970 |
| `P_decode_8x1_q2_n2` | same | 4.991 | 4.958 | 1.0067 |
| `P_decode_64x8_q1_n0` | same | 39.016 | 39.048 | 0.9992 |
| `P_decode_64x8_q1_n1` | same | 39.120 | 38.966 | 1.0040 |
| `P_decode_64x8_q1_n2` | same | 39.056 | 39.072 | 0.9996 |
| `P_decode_64x8_q2_n0` | same | 39.054 | 39.003 | 1.0013 |
| `P_decode_64x8_q2_n1` | same | 39.024 | 39.024 | 1.0000 |
| `P_decode_64x8_q2_n2` | same | 39.153 | 39.031 | 1.0031 |
| `P_prefill_8x1_q1_n0` | same | 5.280 | 5.312 | 0.9940 |
| `P_prefill_8x1_q1_n1` | same | 5.520 | 5.504 | 1.0029 |
| `P_prefill_8x1_q1_n2` | same | 5.440 | 5.463 | 0.9958 |
| `P_prefill_8x1_q2_n0` | same | 5.153 | 5.153 | 1.0000 |
| `P_prefill_8x1_q2_n1` | same | 5.249 | 5.301 | 0.9902 |
| `P_prefill_8x1_q2_n2` | same | 5.312 | 5.312 | 1.0000 |
| `P_prefill_64x8_q1_n0` | same | 42.032 | 42.096 | 0.9985 |
| `P_prefill_64x8_q1_n1` | same | 42.154 | 42.130 | 1.0006 |
| `P_prefill_64x8_q1_n2` | same | 42.278 | 42.211 | 1.0016 |
| `P_prefill_64x8_q2_n0` | same | 41.952 | 41.912 | 1.0010 |
| `P_prefill_64x8_q2_n1` | same | 42.123 | 42.139 | 0.9996 |
| `P_prefill_64x8_q2_n2` | same | 42.161 | 42.129 | 1.0008 |
| `E_prefill_8x1_q127` | changed | 7.288 | 6.472 | 1.1261 |
| `E_prefill_8x1_q128` | changed | 7.319 | 6.575 | 1.1132 |
| `E_prefill_8x1_q129` | changed | 7.168 | 6.432 | 1.1144 |
| `E_prefill_64x8_q127` | same | 92.207 | 92.191 | 1.0002 |
| `E_prefill_64x8_q128` | same | 92.336 | 92.464 | 0.9986 |
| `E_prefill_64x8_q129` | same | 81.098 | 81.151 | 0.9993 |
| `X_decode_8x1_B1_q1_n2` | same | 4.929 | 4.864 | 1.0134 |
| `X_decode_8x1_B128_q1_n2` | same | 6.080 | 6.079 | 1.0002 |
| `X_decode_8x1_B256_q1_n2` | changed | 7.743 | 6.687 | 1.1579 |
| `X_prefill_8x1_B1_Q1024_q1_n2` | changed | 8.544 | 7.968 | 1.0723 |
| `X_decode_64x8_B1_q1_n2` | same | 38.544 | 38.728 | 0.9952 |
| `X_decode_64x8_B128_q1_n2` | same | 45.071 | 44.975 | 1.0021 |
| `X_decode_64x8_B256_q1_n2` | same | 56.863 | 56.894 | 0.9995 |
| `X_prefill_64x8_B1_Q1024_q1_n2` | same | 148.863 | 147.783 | 1.0073 |
| `X_decode_8x1_q1_n2_page16` | changed | 5.632 | 5.377 | 1.0474 |
| `X_decode_8x1_q1_n2_page128` | same | 5.095 | 5.122 | 0.9947 |
| `X_decode_8x1_q1_n2_ctx32768` | changed | 5.695 | 5.350 | 1.0645 |
| `X_prefill_8x1_ragged_q1_n2` | same | 5.632 | 5.613 | 1.0034 |
| `X_decode_8x1_q1_n2_outkv` | changed | 5.185 | 5.088 | 1.0191 |
| `X_prefill_8x1_q1_n2_maxseq1024` | same | 5.479 | 5.536 | 0.9897 |

FP8 E4M3 (`cake_fused_qk_rope_fp8_append`), request-count and page-size
sweep

| shape | launch | FlashInfer main (µs) | this PR (µs) | speedup |
|---|---|---:|---:|---:|
| `S8x1_B129` 8/1 decode, 129 req x 1 new, ctx 2048, page 64 | changed |
6.952 | 5.960 | 1.1664 |
| `S8x1_B136` 8/1 decode, 136 req x 1 new, ctx 2048, page 64 | changed |
6.960 | 5.920 | 1.1757 |
| `S8x1_B148` 8/1 decode, 148 req x 1 new, ctx 2048, page 64 | changed |
7.681 | 6.712 | 1.1444 |
| `S8x1_B160` 8/1 decode, 160 req x 1 new, ctx 2048, page 64 | changed |
7.856 | 6.768 | 1.1608 |
| `S8x1_B176` 8/1 decode, 176 req x 1 new, ctx 2048, page 64 | changed |
7.337 | 6.337 | 1.1578 |
| `S8x1_B177` 8/1 decode, 177 req x 1 new, ctx 2048, page 64 | changed |
7.336 | 6.312 | 1.1622 |
| `S8x1_B187` 8/1 decode, 187 req x 1 new, ctx 2048, page 64 | changed |
7.424 | 6.435 | 1.1537 |
| `S8x1_B188` 8/1 decode, 188 req x 1 new, ctx 2048, page 64 | changed |
7.265 | 6.336 | 1.1466 |
| `S8x1_B200` 8/1 decode, 200 req x 1 new, ctx 2048, page 64 | changed |
7.440 | 6.353 | 1.1711 |
| `S8x1_B223` 8/1 decode, 223 req x 1 new, ctx 2048, page 64 | changed |
7.536 | 6.368 | 1.1834 |
| `S8x1_B224` 8/1 decode, 224 req x 1 new, ctx 2048, page 64 | changed |
7.368 | 6.376 | 1.1556 |
| `S8x1_B256` 8/1 decode, 256 req x 1 new, ctx 2048, page 64 | changed |
7.697 | 6.641 | 1.1590 |
| `S8x1_B384` 8/1 decode, 384 req x 1 new, ctx 2048, page 64 | changed |
8.304 | 7.664 | 1.0835 |
| `S8x1_B512` 8/1 decode, 512 req x 1 new, ctx 2048, page 64 | changed |
8.867 | 8.546 | 1.0376 |
| `R3_prefill_B2_Q100` 8/1 prefill, 2 req x 100 new | changed | 6.345 |
5.880 | 1.0791 |
| `R3_prefill_B3_Q120` 8/1 prefill, 3 req x 120 new | changed | 6.713 |
6.337 | 1.0593 |

BF16 (`cake_fused_qk_rope_append`)

| shape | launch | FlashInfer main (µs) | this PR (µs) | speedup |
|---|---|---:|---:|---:|
| `M1` 8/1, 32 req x 1 new, ctx 2048, page 64, n2 | same | 5.115 | 5.147
| 0.9938 |
| `M1a` 8/1, 32 req x 1 new, ctx 2048, page 64, n0 | same | 5.096 |
5.128 | 0.9938 |
| `M1b` 8/1, 32 req x 1 new, ctx 2048, page 64, n1 | same | 5.671 |
5.616 | 1.0098 |
| `M2` 8/1, 8 req x 16 new, ctx 2048, page 64, n2 | same | 5.872 | 5.886
| 0.9976 |
| `M2a` 8/1, 8 req x 16 new, ctx 2048, page 64, n0 | same | 5.328 |
5.328 | 1.0000 |
| `M2b` 8/1, 8 req x 16 new, ctx 2048, page 64, n1 | same | 5.447 |
5.456 | 0.9984 |
| `H1` 64/8, 32 req x 1 new, ctx 2048, page 64, n2 | same | 10.739 |
10.688 | 1.0048 |
| `H2` 64/8, 8 req x 16 new, ctx 2048, page 64, n2 | same | 11.868 |
11.852 | 1.0013 |
| `H3` 64/8, 128 req x 1 new, ctx 2048, page 64, n2 | same | 11.952 |
11.960 | 0.9993 |
| `H4` 64/8, 1 req x 128 new, ctx 2048, page 64, n2 | same | 11.832 |
11.813 | 1.0016 |
| `D1` 8/1, 1 req x 1 new, ctx 2048, page 64, n2 | same | 4.880 | 4.888
| 0.9984 |
| `D2` 8/1, 8 req x 1 new, ctx 2048, page 64, n2 | same | 4.919 | 4.920
| 0.9998 |
| `D3` 8/1, 128 req x 1 new, ctx 2048, page 64, n2 | same | 6.208 |
6.207 | 1.0002 |
| `D4` 8/1, 256 req x 1 new, ctx 2048, page 64, n2 | same | 6.898 |
6.866 | 1.0047 |
| `P1` 8/1, 1 req x 128 new, ctx 2048, page 64, n2 | same | 5.441 |
5.415 | 1.0048 |
| `P2` 8/1, 4 req x 64 new, ctx 2048, page 64, n2 | same | 5.679 | 5.695
| 0.9972 |
| `P3` 8/1, 32 req x 8 new, ctx 2048, page 64, n2 | same | 5.936 | 5.950
| 0.9976 |
| `E1` 8/1, 32 req x 1 new, ctx 2048, page 16, n2 | same | 4.945 | 4.961
| 0.9968 |
| `E2` 8/1, 32 req x 1 new, ctx 2048, page 128, n2 | same | 5.400 |
5.391 | 1.0017 |
| `E3` 8/1, 32 req x 1 new, ctx 0, page 64, n2 | same | 4.960 | 4.960 |
1.0000 |
| `E4` 8/1, 8 req x 16 new, ctx 2047, page 64, n2 | same | 5.409 | 5.409
| 1.0000 |
| `E5` 8/1, 32 req x 1 new, ctx 2048, page 64, n2, outkv | same | 5.184
| 5.183 | 1.0002 |
| `E6` 8/1, 16 req ragged (1-64 new, 0-4095 cached), page 64, n2 | same
| 6.079 | 6.080 | 0.9998 |
| `X1` 8/1, 32 req x 1 new, ctx 32768, page 64, n2 | same | 5.058 |
5.048 | 1.0020 |
| `X2` 8/1, 512 req x 1 new, ctx 2048, page 64, n2 | same | 8.786 |
8.838 | 0.9941 |
| `X3` 64/8, 32 req x 1 new, ctx 2048, page 64, n0 | same | 10.960 |
10.944 | 1.0015 |
| `X4` 64/8, 32 req x 1 new, ctx 2048, page 64, n1 | same | 10.704 |
10.728 | 0.9978 |
| `X5` 8/1, 32 req x 1 new, ctx 2048, page 32, n2 | same | 4.960 | 4.960
| 1.0000 |

BF16 (`cake_fused_qk_rope_append`), request-count and page-size sweep

| shape | launch | FlashInfer main (µs) | this PR (µs) | speedup |
|---|---|---:|---:|---:|
| `S8x1_B512` 8/1 decode, 512 req x 1 new, ctx 2048, page 64 | same |
8.813 | 8.816 | 0.9997 |
| `S8x1_B513` 8/1 decode, 513 req x 1 new, ctx 2048, page 64 | changed |
8.888 | 8.744 | 1.0165 |
| `S8x1_B514` 8/1 decode, 514 req x 1 new, ctx 2048, page 64 | changed |
9.616 | 9.049 | 1.0627 |
| `S8x1_B547` 8/1 decode, 547 req x 1 new, ctx 2048, page 64 | changed |
10.463 | 9.423 | 1.1104 |
| `S8x1_B640` 8/1 decode, 640 req x 1 new, ctx 2048, page 64 | changed |
9.801 | 9.618 | 1.0190 |
| `S8x1_B768` 8/1 decode, 768 req x 1 new, ctx 2048, page 64 | changed |
11.417 | 10.664 | 1.0706 |
| `S8x1_B896` 8/1 decode, 896 req x 1 new, ctx 2048, page 64 | same |
11.954 | 11.962 | 0.9993 |
| `S8x1_B960` 8/1 decode, 960 req x 1 new, ctx 2048, page 64 | same |
12.037 | 12.041 | 0.9997 |
| `S8x1_B1024` 8/1 decode, 1024 req x 1 new, ctx 2048, page 64 | same |
12.305 | 12.364 | 0.9952 |
| `R3_p64_B880` 8/1 decode, 880 req x 1 new, ctx 2048, page 64 | changed
| 11.925 | 11.544 | 1.0330 |
| `R3_p128_B384` 8/1 decode, 384 req x 1 new, ctx 2048, page 128 | same
| 9.255 | 9.259 | 0.9996 |
| `R3_p128_B512` 8/1 decode, 512 req x 1 new, ctx 2048, page 128 | same
| 12.086 | 12.088 | 0.9998 |
| `R3_p16_B2048` 8/1 decode, 2048 req x 1 new, ctx 2048, page 16 |
changed | 15.441 | 14.513 | 1.0639 |
| `R3_p16_B3500` 8/1 decode, 3500 req x 1 new, ctx 2048, page 16 |
changed | 21.677 | 21.328 | 1.0164 |
| `R3_p32_B1024` 8/1 decode, 1024 req x 1 new, ctx 2048, page 32 |
changed | 11.424 | 10.304 | 1.1087 |
| `R3_p32_B1536` 8/1 decode, 1536 req x 1 new, ctx 2048, page 32 |
changed | 13.815 | 13.296 | 1.0390 |
| `R3_p32_B1792` 8/1 decode, 1792 req x 1 new, ctx 2048, page 32 | same
| 15.486 | 15.479 | 1.0005 |

**NVIDIA B300, sm_103a (148 SMs), CUDA 13.4. Speedup = FlashInfer main /
this PR, both with `enable_pdl=True`.**


FP8 E4M3 (`cake_fused_qk_rope_fp8_append`)

| shape | launch | FlashInfer main (µs) | this PR (µs) | speedup |
|---|---|---:|---:|---:|
| `P_decode_8x1_q1_n0` | same | 4.801 | 4.830 | 0.9940 |
| `P_decode_8x1_q1_n1` | same | 5.113 | 5.086 | 1.0053 |
| `P_decode_8x1_q1_n2` | same | 5.712 | 5.760 | 0.9917 |
| `P_decode_8x1_q2_n0` | same | 5.537 | 5.505 | 1.0058 |
| `P_decode_8x1_q2_n1` | same | 4.944 | 4.930 | 1.0028 |
| `P_decode_8x1_q2_n2` | same | 4.960 | 4.957 | 1.0006 |
| `P_decode_64x8_q1_n0` | same | 41.263 | 41.384 | 0.9971 |
| `P_decode_64x8_q1_n1` | same | 41.178 | 41.177 | 1.0000 |
| `P_decode_64x8_q1_n2` | same | 41.657 | 41.775 | 0.9972 |
| `P_decode_64x8_q2_n0` | same | 41.515 | 41.251 | 1.0064 |
| `P_decode_64x8_q2_n1` | same | 41.454 | 41.535 | 0.9980 |
| `P_decode_64x8_q2_n2` | same | 41.412 | 41.444 | 0.9992 |
| `P_prefill_8x1_q1_n0` | same | 5.320 | 5.343 | 0.9957 |
| `P_prefill_8x1_q1_n1` | same | 5.559 | 5.567 | 0.9986 |
| `P_prefill_8x1_q1_n2` | same | 5.569 | 5.568 | 1.0002 |
| `P_prefill_8x1_q2_n0` | same | 5.163 | 5.152 | 1.0021 |
| `P_prefill_8x1_q2_n1` | same | 5.367 | 5.347 | 1.0037 |
| `P_prefill_8x1_q2_n2` | same | 5.423 | 5.375 | 1.0089 |
| `P_prefill_64x8_q1_n0` | same | 45.292 | 45.279 | 1.0003 |
| `P_prefill_64x8_q1_n1` | same | 45.257 | 45.161 | 1.0021 |
| `P_prefill_64x8_q1_n2` | same | 45.456 | 45.454 | 1.0000 |
| `P_prefill_64x8_q2_n0` | same | 45.173 | 45.216 | 0.9990 |
| `P_prefill_64x8_q2_n1` | same | 45.333 | 45.320 | 1.0003 |
| `P_prefill_64x8_q2_n2` | same | 45.484 | 45.500 | 0.9996 |
| `E_prefill_8x1_q127` | changed | 7.087 | 6.371 | 1.1124 |
| `E_prefill_8x1_q128` | changed | 7.248 | 6.464 | 1.1213 |
| `E_prefill_8x1_q129` | changed | 7.253 | 6.496 | 1.1165 |
| `E_prefill_64x8_q127` | same | 70.340 | 70.391 | 0.9993 |
| `E_prefill_64x8_q128` | same | 70.426 | 70.370 | 1.0008 |
| `E_prefill_64x8_q129` | same | 71.680 | 71.680 | 1.0000 |
| `X_decode_8x1_B1_q1_n2` | same | 4.920 | 4.953 | 0.9933 |
| `X_decode_8x1_B128_q1_n2` | same | 6.248 | 6.247 | 1.0002 |
| `X_decode_8x1_B256_q1_n2` | changed | 7.712 | 6.639 | 1.1616 |
| `X_prefill_8x1_B1_Q1024_q1_n2` | changed | 8.438 | 8.111 | 1.0403 |
| `X_decode_64x8_B1_q1_n2` | same | 39.506 | 39.472 | 1.0009 |
| `X_decode_64x8_B128_q1_n2` | same | 48.176 | 48.185 | 0.9998 |
| `X_decode_64x8_B256_q1_n2` | same | 57.153 | 57.134 | 1.0003 |
| `X_prefill_64x8_B1_Q1024_q1_n2` | same | 135.889 | 135.790 | 1.0007 |
| `X_decode_8x1_q1_n2_page16` | changed | 5.439 | 5.222 | 1.0416 |
| `X_decode_8x1_q1_n2_page128` | changed | 5.592 | 5.086 | 1.0995 |
| `X_decode_8x1_q1_n2_ctx32768` | changed | 5.440 | 5.369 | 1.0132 |
| `X_prefill_8x1_ragged_q1_n2` | same | 5.710 | 5.710 | 1.0000 |
| `X_decode_8x1_q1_n2_outkv` | changed | 5.418 | 5.097 | 1.0630 |
| `X_prefill_8x1_q1_n2_maxseq1024` | same | 5.505 | 5.505 | 1.0000 |

FP8 E4M3 (`cake_fused_qk_rope_fp8_append`), request-count and page-size
sweep

| shape | launch | FlashInfer main (µs) | this PR (µs) | speedup |
|---|---|---:|---:|---:|
| `S8x1_B129` 8/1 decode, 129 req x 1 new, ctx 2048, page 64 | same |
6.112 | 6.108 | 1.0007 |
| `S8x1_B136` 8/1 decode, 136 req x 1 new, ctx 2048, page 64 | same |
6.031 | 5.983 | 1.0080 |
| `S8x1_B148` 8/1 decode, 148 req x 1 new, ctx 2048, page 64 | same |
6.519 | 6.583 | 0.9903 |
| `S8x1_B160` 8/1 decode, 160 req x 1 new, ctx 2048, page 64 | same |
6.747 | 6.760 | 0.9981 |
| `S8x1_B176` 8/1 decode, 176 req x 1 new, ctx 2048, page 64 | same |
7.247 | 7.228 | 1.0026 |
| `S8x1_B177` 8/1 decode, 177 req x 1 new, ctx 2048, page 64 | same |
7.217 | 7.199 | 1.0025 |
| `S8x1_B187` 8/1 decode, 187 req x 1 new, ctx 2048, page 64 | changed |
7.423 | 6.446 | 1.1516 |
| `S8x1_B188` 8/1 decode, 188 req x 1 new, ctx 2048, page 64 | changed |
7.380 | 6.400 | 1.1531 |
| `S8x1_B200` 8/1 decode, 200 req x 1 new, ctx 2048, page 64 | changed |
7.424 | 6.375 | 1.1645 |
| `S8x1_B223` 8/1 decode, 223 req x 1 new, ctx 2048, page 64 | changed |
7.502 | 6.497 | 1.1547 |
| `S8x1_B224` 8/1 decode, 224 req x 1 new, ctx 2048, page 64 | changed |
7.329 | 6.495 | 1.1284 |
| `S8x1_B256` 8/1 decode, 256 req x 1 new, ctx 2048, page 64 | changed |
7.745 | 6.722 | 1.1522 |
| `S8x1_B384` 8/1 decode, 384 req x 1 new, ctx 2048, page 64 | changed |
8.190 | 7.648 | 1.0709 |
| `S8x1_B512` 8/1 decode, 512 req x 1 new, ctx 2048, page 64 | changed |
8.958 | 8.662 | 1.0342 |
| `R3_prefill_B2_Q100` 8/1 prefill, 2 req x 100 new | changed | 6.630 |
5.966 | 1.1113 |
| `R3_prefill_B3_Q120` 8/1 prefill, 3 req x 120 new | changed | 6.848 |
6.320 | 1.0835 |

BF16 (`cake_fused_qk_rope_append`)

| shape | launch | FlashInfer main (µs) | this PR (µs) | speedup |
|---|---|---:|---:|---:|
| `M1` 8/1, 32 req x 1 new, ctx 2048, page 64, n2 | same | 4.992 | 4.959
| 1.0067 |
| `M1a` 8/1, 32 req x 1 new, ctx 2048, page 64, n0 | same | 5.215 |
5.185 | 1.0058 |
| `M1b` 8/1, 32 req x 1 new, ctx 2048, page 64, n1 | same | 5.474 |
5.559 | 0.9847 |
| `M2` 8/1, 8 req x 16 new, ctx 2048, page 64, n2 | same | 5.822 | 5.853
| 0.9947 |
| `M2a` 8/1, 8 req x 16 new, ctx 2048, page 64, n0 | same | 5.515 |
5.502 | 1.0024 |
| `M2b` 8/1, 8 req x 16 new, ctx 2048, page 64, n1 | same | 5.628 |
5.650 | 0.9961 |
| `H1` 64/8, 32 req x 1 new, ctx 2048, page 64, n2 | same | 11.104 |
11.121 | 0.9985 |
| `H2` 64/8, 8 req x 16 new, ctx 2048, page 64, n2 | same | 12.159 |
12.173 | 0.9988 |
| `H3` 64/8, 128 req x 1 new, ctx 2048, page 64, n2 | same | 12.510 |
12.495 | 1.0012 |
| `H4` 64/8, 1 req x 128 new, ctx 2048, page 64, n2 | same | 12.175 |
12.151 | 1.0020 |
| `D1` 8/1, 1 req x 1 new, ctx 2048, page 64, n2 | same | 4.806 | 4.767
| 1.0082 |
| `D2` 8/1, 8 req x 1 new, ctx 2048, page 64, n2 | same | 4.948 | 4.933
| 1.0030 |
| `D3` 8/1, 128 req x 1 new, ctx 2048, page 64, n2 | same | 6.210 |
6.180 | 1.0049 |
| `D4` 8/1, 256 req x 1 new, ctx 2048, page 64, n2 | same | 6.876 |
6.897 | 0.9970 |
| `P1` 8/1, 1 req x 128 new, ctx 2048, page 64, n2 | same | 5.376 |
5.406 | 0.9945 |
| `P2` 8/1, 4 req x 64 new, ctx 2048, page 64, n2 | same | 5.567 | 5.585
| 0.9968 |
| `P3` 8/1, 32 req x 8 new, ctx 2048, page 64, n2 | same | 6.142 | 6.088
| 1.0089 |
| `E1` 8/1, 32 req x 1 new, ctx 2048, page 16, n2 | same | 4.830 | 4.759
| 1.0149 |
| `E2` 8/1, 32 req x 1 new, ctx 2048, page 128, n2 | same | 5.376 |
5.374 | 1.0004 |
| `E3` 8/1, 32 req x 1 new, ctx 0, page 64, n2 | same | 5.215 | 5.198 |
1.0033 |
| `E4` 8/1, 8 req x 16 new, ctx 2047, page 64, n2 | same | 5.632 | 5.632
| 1.0000 |
| `E5` 8/1, 32 req x 1 new, ctx 2048, page 64, n2, outkv | same | 5.152
| 5.182 | 0.9942 |
| `E6` 8/1, 16 req ragged (1-64 new, 0-4095 cached), page 64, n2 | same
| 5.939 | 5.940 | 0.9998 |
| `X1` 8/1, 32 req x 1 new, ctx 32768, page 64, n2 | same | 5.100 |
5.100 | 1.0000 |
| `X2` 8/1, 512 req x 1 new, ctx 2048, page 64, n2 | same | 8.942 |
8.915 | 1.0030 |
| `X3` 64/8, 32 req x 1 new, ctx 2048, page 64, n0 | same | 10.987 |
10.977 | 1.0009 |
| `X4` 64/8, 32 req x 1 new, ctx 2048, page 64, n1 | same | 11.072 |
11.016 | 1.0051 |
| `X5` 8/1, 32 req x 1 new, ctx 2048, page 32, n2 | same | 4.906 | 4.880
| 1.0053 |

BF16 (`cake_fused_qk_rope_append`), request-count and page-size sweep

| shape | launch | FlashInfer main (µs) | this PR (µs) | speedup |
|---|---|---:|---:|---:|
| `S8x1_B512` 8/1 decode, 512 req x 1 new, ctx 2048, page 64 | same |
8.944 | 8.929 | 1.0017 |
| `S8x1_B513` 8/1 decode, 513 req x 1 new, ctx 2048, page 64 | changed |
8.935 | 8.784 | 1.0172 |
| `S8x1_B514` 8/1 decode, 514 req x 1 new, ctx 2048, page 64 | changed |
9.553 | 9.182 | 1.0404 |
| `S8x1_B547` 8/1 decode, 547 req x 1 new, ctx 2048, page 64 | changed |
10.403 | 9.310 | 1.1174 |
| `S8x1_B640` 8/1 decode, 640 req x 1 new, ctx 2048, page 64 | changed |
9.840 | 9.567 | 1.0285 |
| `S8x1_B768` 8/1 decode, 768 req x 1 new, ctx 2048, page 64 | changed |
11.504 | 10.816 | 1.0636 |
| `S8x1_B896` 8/1 decode, 896 req x 1 new, ctx 2048, page 64 | same |
11.585 | 11.581 | 1.0003 |
| `S8x1_B960` 8/1 decode, 960 req x 1 new, ctx 2048, page 64 | same |
12.269 | 12.242 | 1.0022 |
| `S8x1_B1024` 8/1 decode, 1024 req x 1 new, ctx 2048, page 64 | same |
12.627 | 12.593 | 1.0027 |
| `R3_p64_B880` 8/1 decode, 880 req x 1 new, ctx 2048, page 64 | changed
| 11.544 | 11.105 | 1.0395 |
| `R3_p128_B384` 8/1 decode, 384 req x 1 new, ctx 2048, page 128 | same
| 9.207 | 9.233 | 0.9972 |
| `R3_p128_B512` 8/1 decode, 512 req x 1 new, ctx 2048, page 128 | same
| 12.015 | 12.035 | 0.9983 |
| `R3_p16_B2048` 8/1 decode, 2048 req x 1 new, ctx 2048, page 16 |
changed | 15.262 | 14.337 | 1.0645 |
| `R3_p16_B3500` 8/1 decode, 3500 req x 1 new, ctx 2048, page 16 |
changed | 21.647 | 21.272 | 1.0176 |
| `R3_p32_B1024` 8/1 decode, 1024 req x 1 new, ctx 2048, page 32 |
changed | 11.583 | 10.592 | 1.0936 |
| `R3_p32_B1536` 8/1 decode, 1536 req x 1 new, ctx 2048, page 32 |
changed | 14.430 | 13.472 | 1.0711 |
| `R3_p32_B1792` 8/1 decode, 1792 req x 1 new, ctx 2048, page 32 | same
| 15.344 | 15.358 | 0.9991 |

**NVIDIA GB300, sm_103a (152 SMs), CUDA 13.4. Speedup = FlashInfer main
/ this PR, both with `enable_pdl=True`.**


FP8 E4M3 (`cake_fused_qk_rope_fp8_append`)

| shape | launch | FlashInfer main (µs) | this PR (µs) | speedup |
|---|---|---:|---:|---:|
| `P_decode_8x1_q1_n0` | changed | 5.183 | 4.928 | 1.0517 |
| `P_decode_8x1_q1_n1` | changed | 5.247 | 5.024 | 1.0444 |
| `P_decode_8x1_q1_n2` | changed | 5.822 | 5.626 | 1.0348 |
| `P_decode_8x1_q2_n0` | changed | 5.657 | 5.385 | 1.0505 |
| `P_decode_8x1_q2_n1` | changed | 5.184 | 4.832 | 1.0728 |
| `P_decode_8x1_q2_n2` | changed | 5.216 | 4.832 | 1.0795 |
| `P_decode_64x8_q1_n0` | same | 39.592 | 39.632 | 0.9990 |
| `P_decode_64x8_q1_n1` | same | 39.696 | 39.624 | 1.0018 |
| `P_decode_64x8_q1_n2` | same | 39.664 | 39.728 | 0.9984 |
| `P_decode_64x8_q2_n0` | same | 39.598 | 39.551 | 1.0012 |
| `P_decode_64x8_q2_n1` | same | 39.632 | 39.613 | 1.0005 |
| `P_decode_64x8_q2_n2` | same | 39.696 | 39.632 | 1.0016 |
| `P_prefill_8x1_q1_n0` | same | 5.312 | 5.312 | 1.0000 |
| `P_prefill_8x1_q1_n1` | same | 5.440 | 5.439 | 1.0002 |
| `P_prefill_8x1_q1_n2` | same | 5.518 | 5.550 | 0.9942 |
| `P_prefill_8x1_q2_n0` | same | 5.121 | 5.096 | 1.0049 |
| `P_prefill_8x1_q2_n1` | same | 5.312 | 5.313 | 0.9998 |
| `P_prefill_8x1_q2_n2` | same | 5.312 | 5.312 | 1.0000 |
| `P_prefill_64x8_q1_n0` | same | 43.968 | 43.968 | 1.0000 |
| `P_prefill_64x8_q1_n1` | same | 44.009 | 44.008 | 1.0000 |
| `P_prefill_64x8_q1_n2` | same | 44.500 | 44.376 | 1.0028 |
| `P_prefill_64x8_q2_n0` | same | 44.161 | 44.151 | 1.0002 |
| `P_prefill_64x8_q2_n1` | same | 44.393 | 44.305 | 1.0020 |
| `P_prefill_64x8_q2_n2` | same | 44.320 | 44.272 | 1.0011 |
| `E_prefill_8x1_q127` | changed | 6.953 | 6.400 | 1.0864 |
| `E_prefill_8x1_q128` | changed | 6.896 | 6.336 | 1.0884 |
| `E_prefill_8x1_q129` | changed | 6.880 | 6.336 | 1.0859 |
| `E_prefill_64x8_q127` | same | 74.160 | 74.151 | 1.0001 |
| `E_prefill_64x8_q128` | same | 74.320 | 74.149 | 1.0023 |
| `E_prefill_64x8_q129` | same | 68.877 | 68.896 | 0.9997 |
| `X_decode_8x1_B1_q1_n2` | same | 4.936 | 4.895 | 1.0084 |
| `X_decode_8x1_B128_q1_n2` | same | 5.919 | 5.897 | 1.0037 |
| `X_decode_8x1_B256_q1_n2` | changed | 7.680 | 6.625 | 1.1592 |
| `X_prefill_8x1_B1_Q1024_q1_n2` | changed | 8.032 | 7.679 | 1.0460 |
| `X_decode_64x8_B1_q1_n2` | same | 38.911 | 38.896 | 1.0004 |
| `X_decode_64x8_B128_q1_n2` | same | 46.800 | 46.757 | 1.0009 |
| `X_decode_64x8_B256_q1_n2` | same | 56.264 | 56.280 | 0.9997 |
| `X_prefill_64x8_B1_Q1024_q1_n2` | same | 115.237 | 115.229 | 1.0001 |
| `X_decode_8x1_q1_n2_page16` | same | 5.336 | 5.312 | 1.0045 |
| `X_decode_8x1_q1_n2_page128` | changed | 5.289 | 5.055 | 1.0463 |
| `X_decode_8x1_q1_n2_ctx32768` | same | 5.349 | 5.312 | 1.0070 |
| `X_prefill_8x1_ragged_q1_n2` | same | 5.568 | 5.518 | 1.0091 |
| `X_decode_8x1_q1_n2_outkv` | same | 5.153 | 5.153 | 1.0000 |
| `X_prefill_8x1_q1_n2_maxseq1024` | same | 5.440 | 5.472 | 0.9942 |

FP8 E4M3 (`cake_fused_qk_rope_fp8_append`), request-count and page-size
sweep

| shape | launch | FlashInfer main (µs) | this PR (µs) | speedup |
|---|---|---:|---:|---:|
| `S8x1_B129` 8/1 decode, 129 req x 1 new, ctx 2048, page 64 | same |
5.959 | 5.992 | 0.9945 |
| `S8x1_B136` 8/1 decode, 136 req x 1 new, ctx 2048, page 64 | same |
5.974 | 5.968 | 1.0010 |
| `S8x1_B148` 8/1 decode, 148 req x 1 new, ctx 2048, page 64 | same |
6.753 | 6.688 | 1.0097 |
| `S8x1_B160` 8/1 decode, 160 req x 1 new, ctx 2048, page 64 | same |
6.697 | 6.625 | 1.0109 |
| `S8x1_B176` 8/1 decode, 176 req x 1 new, ctx 2048, page 64 | same |
6.104 | 6.194 | 0.9855 |
| `S8x1_B177` 8/1 decode, 177 req x 1 new, ctx 2048, page 64 | same |
6.272 | 6.225 | 1.0076 |
| `S8x1_B187` 8/1 decode, 187 req x 1 new, ctx 2048, page 64 | changed |
7.112 | 6.200 | 1.1471 |
| `S8x1_B188` 8/1 decode, 188 req x 1 new, ctx 2048, page 64 | changed |
7.153 | 6.256 | 1.1434 |
| `S8x1_B200` 8/1 decode, 200 req x 1 new, ctx 2048, page 64 | changed |
7.176 | 6.216 | 1.1544 |
| `S8x1_B223` 8/1 decode, 223 req x 1 new, ctx 2048, page 64 | changed |
7.287 | 6.312 | 1.1545 |
| `S8x1_B224` 8/1 decode, 224 req x 1 new, ctx 2048, page 64 | changed |
7.135 | 6.208 | 1.1493 |
| `S8x1_B256` 8/1 decode, 256 req x 1 new, ctx 2048, page 64 | changed |
7.594 | 6.496 | 1.1690 |
| `S8x1_B384` 8/1 decode, 384 req x 1 new, ctx 2048, page 64 | changed |
8.128 | 7.488 | 1.0855 |
| `S8x1_B512` 8/1 decode, 512 req x 1 new, ctx 2048, page 64 | changed |
8.698 | 8.385 | 1.0373 |
| `R3_prefill_B2_Q100` 8/1 prefill, 2 req x 100 new | changed | 6.311 |
5.896 | 1.0704 |
| `R3_prefill_B3_Q120` 8/1 prefill, 3 req x 120 new | changed | 6.489 |
6.176 | 1.0507 |

BF16 (`cake_fused_qk_rope_append`)

| shape | launch | FlashInfer main (µs) | this PR (µs) | speedup |
|---|---|---:|---:|---:|
| `M1` 8/1, 32 req x 1 new, ctx 2048, page 64, n2 | same | 4.961 | 4.993
| 0.9936 |
| `M1a` 8/1, 32 req x 1 new, ctx 2048, page 64, n0 | same | 4.993 |
5.088 | 0.9813 |
| `M1b` 8/1, 32 req x 1 new, ctx 2048, page 64, n1 | same | 5.567 |
5.471 | 1.0175 |
| `M2` 8/1, 8 req x 16 new, ctx 2048, page 64, n2 | same | 5.856 | 5.855
| 1.0002 |
| `M2a` 8/1, 8 req x 16 new, ctx 2048, page 64, n0 | same | 5.216 |
5.247 | 0.9941 |
| `M2b` 8/1, 8 req x 16 new, ctx 2048, page 64, n1 | same | 5.432 |
5.440 | 0.9985 |
| `H1` 64/8, 32 req x 1 new, ctx 2048, page 64, n2 | same | 10.688 |
10.608 | 1.0075 |
| `H2` 64/8, 8 req x 16 new, ctx 2048, page 64, n2 | same | 11.673 |
11.633 | 1.0034 |
| `H3` 64/8, 128 req x 1 new, ctx 2048, page 64, n2 | same | 11.785 |
11.808 | 0.9981 |
| `H4` 64/8, 1 req x 128 new, ctx 2048, page 64, n2 | same | 11.601 |
11.561 | 1.0035 |
| `D1` 8/1, 1 req x 1 new, ctx 2048, page 64, n2 | same | 4.895 | 4.896
| 0.9998 |
| `D2` 8/1, 8 req x 1 new, ctx 2048, page 64, n2 | same | 4.856 | 4.864
| 0.9984 |
| `D3` 8/1, 128 req x 1 new, ctx 2048, page 64, n2 | same | 6.080 |
6.112 | 0.9948 |
| `D4` 8/1, 256 req x 1 new, ctx 2048, page 64, n2 | same | 6.689 |
6.656 | 1.0050 |
| `P1` 8/1, 1 req x 128 new, ctx 2048, page 64, n2 | same | 5.248 |
5.216 | 1.0061 |
| `P2` 8/1, 4 req x 64 new, ctx 2048, page 64, n2 | same | 5.473 | 5.472
| 1.0002 |
| `P3` 8/1, 32 req x 8 new, ctx 2048, page 64, n2 | same | 5.793 | 5.824
| 0.9947 |
| `E1` 8/1, 32 req x 1 new, ctx 2048, page 16, n2 | same | 4.865 | 4.876
| 0.9977 |
| `E2` 8/1, 32 req x 1 new, ctx 2048, page 128, n2 | same | 5.152 |
5.183 | 0.9940 |
| `E3` 8/1, 32 req x 1 new, ctx 0, page 64, n2 | same | 4.864 | 4.896 |
0.9935 |
| `E4` 8/1, 8 req x 16 new, ctx 2047, page 64, n2 | same | 5.247 | 5.248
| 0.9998 |
| `E5` 8/1, 32 req x 1 new, ctx 2048, page 64, n2, outkv | same | 5.025
| 4.994 | 1.0062 |
| `E6` 8/1, 16 req ragged (1-64 new, 0-4095 cached), page 64, n2 | same
| 5.888 | 5.888 | 1.0000 |
| `X1` 8/1, 32 req x 1 new, ctx 32768, page 64, n2 | same | 5.008 |
4.993 | 1.0030 |
| `X2` 8/1, 512 req x 1 new, ctx 2048, page 64, n2 | same | 8.503 |
8.497 | 1.0007 |
| `X3` 64/8, 32 req x 1 new, ctx 2048, page 64, n0 | same | 10.816 |
10.832 | 0.9985 |
| `X4` 64/8, 32 req x 1 new, ctx 2048, page 64, n1 | same | 10.623 |
10.648 | 0.9977 |
| `X5` 8/1, 32 req x 1 new, ctx 2048, page 32, n2 | same | 4.876 | 4.896
| 0.9959 |

BF16 (`cake_fused_qk_rope_append`), request-count and page-size sweep

| shape | launch | FlashInfer main (µs) | this PR (µs) | speedup |
|---|---|---:|---:|---:|
| `S8x1_B512` 8/1 decode, 512 req x 1 new, ctx 2048, page 64 | same |
8.576 | 8.544 | 1.0037 |
| `S8x1_B547` 8/1 decode, 547 req x 1 new, ctx 2048, page 64 | changed |
9.344 | 8.845 | 1.0564 |
| `S8x1_B640` 8/1 decode, 640 req x 1 new, ctx 2048, page 64 | changed |
9.800 | 9.760 | 1.0041 |
| `S8x1_B768` 8/1 decode, 768 req x 1 new, ctx 2048, page 64 | changed |
11.439 | 10.800 | 1.0592 |
| `S8x1_B896` 8/1 decode, 896 req x 1 new, ctx 2048, page 64 | same |
11.583 | 11.583 | 1.0000 |
| `S8x1_B960` 8/1 decode, 960 req x 1 new, ctx 2048, page 64 | same |
11.713 | 11.680 | 1.0028 |
| `S8x1_B1024` 8/1 decode, 1024 req x 1 new, ctx 2048, page 64 | same |
12.015 | 12.033 | 0.9985 |
| `R3_p64_B880` 8/1 decode, 880 req x 1 new, ctx 2048, page 64 | changed
| 11.519 | 11.247 | 1.0242 |
| `R3_p128_B384` 8/1 decode, 384 req x 1 new, ctx 2048, page 128 | same
| 9.039 | 9.056 | 0.9981 |
| `R3_p128_B512` 8/1 decode, 512 req x 1 new, ctx 2048, page 128 | same
| 11.603 | 11.568 | 1.0030 |
| `R3_p16_B2048` 8/1 decode, 2048 req x 1 new, ctx 2048, page 16 |
changed | 14.720 | 13.808 | 1.0660 |
| `R3_p16_B3500` 8/1 decode, 3500 req x 1 new, ctx 2048, page 16 |
changed | 20.463 | 20.127 | 1.0167 |
| `R3_p32_B1024` 8/1 decode, 1024 req x 1 new, ctx 2048, page 32 |
changed | 11.112 | 10.081 | 1.1023 |
| `R3_p32_B1536` 8/1 decode, 1536 req x 1 new, ctx 2048, page 32 |
changed | 13.498 | 12.912 | 1.0454 |
| `R3_p32_B1792` 8/1 decode, 1792 req x 1 new, ctx 2048, page 32 | same
| 14.944 | 14.928 | 1.0011 |


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

- **Performance**
- Attention workloads can now select optimized execution paths based on
GPU architecture, workload shape, and cache-page configuration.
- FP8 workloads may use page prefetching and adjusted GPU occupancy
limits to better match supported hardware and workload conditions.
- **Compatibility**
- Expanded execution-policy coverage for additional NVIDIA GPU
configurations, batch sizes, and context lengths.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [21bde11](https://github.com/flashinfer-ai/flashinfer/commit/21bde11c7ab41bebb00a9dcef98d4a841d633b73)

- **作者**: Akaash Parthasarathy
- **时间**: 2026-10-31T23:19:32Z
- **提交信息**: perf(moe_ep): skip masked slots in SM107 quantized combine (#7910)

<!-- .github/pull_request_template.md -->

## 📌 Description

NVFP4 and MXFP8 combine now skip masked routes before loading their
payloads, scales or scores. This removes the need to clear their combine
buffers before each forward. The reducers use the existing caller-output
binding and live-token bounds from #7806.

SM107 staging preserves masked scores instead of zeroing them. Routing
value checks are now opt-in through
`FLASHINFER_SM107_MEGA_CHECK_ROUTES=1`; metadata checks remain enabled.
In-kernel reduction retains its accumulation reset.

## 🔍 Related Issues

Follow-up to #7806.

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
- [x] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust):
`tests/moe_ep/test_sm107_block_scaled_contracts.py
tests/moe_ep/test_sm107_combine.py
tests/moe_ep/test_sm107_preparation.py
tests/moe_ep/test_sm107_quantized_masked_combine.py
tests/moe_ep/test_moe_ep_sm107_block_scaled_mega_multirank.py`

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

* **Behavior Changes**
* Routing value checks are disabled by default. Set
`FLASHINFER_SM107_MEGA_CHECK_ROUTES=1` to enable them; metadata checks
and staging remain active.
* SM107 staging preserves scores for masked routes, including non-finite
values. Dispatch and reduction exclude masked routes, and
caller-provided routing tensors remain unchanged.
* NVFP4 and MXFP8 combine operations skip invalid routes without reading
their payloads or scales. Reducers leave combine buffers unchanged,
while rows with no valid routes produce zero results.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [12adf08](https://github.com/flashinfer-ai/flashinfer/commit/12adf0855dac8dd114beceeb0ccc70b562861017)

- **作者**: eigen
- **时间**: 2026-10-31T22:54:46Z
- **提交信息**: perf(cake_mega_moe): WCX mid-round windows for three SM90 BF16 shapes (#8147)

This PR extends WCX in the Cake SM90 BF16 MegaMoE push backend in
`flashinfer.moe_ep` (`Sm90_Bf16_Bf16_Bf16_PushCake_MegaMoeConfig`,
backend `bf16_bf16_bf16_push_cake`) from decode rounds to three mid-size
shapes. One EP round runs NVLink push dispatch, expert-major compact,
grouped GEMM FC1 with fused SwiGLU, grouped GEMM FC2, combine publish
and a top-k reduce tail. All variants use one data type (BF16 x BF16 ->
BF16 with FP32 accumulation). They cover FC1 with or without the SwiGLU
clamp, per-route and pre-reduced combine wire forms, and EP 2/4/8. WCX
is an optional compressed format for expert weights and stays opt-in
(`wcx_max_tokens`, env `FLASHINFER_SM90_CAKE_BF16_WCX_MAX_TOKENS`,
default 0 means off). Before this PR it ran only for rounds with 0 < T
<= `wcx_max_tokens` (at most 128) local tokens per rank. This PR adds a
fixed window table, keyed by EP and layer geometry, that also runs WCX
in three cases: 128 < T <= 1024 at EP2 with hidden 7168, intermediate
2048, 256 experts and top-8; 128 < T <= 512 at EP8 with hidden 7168,
intermediate 3072, 384 experts and top-6; and 128 < T <= 512 at EP8 with
hidden 4096, intermediate 2048, 256 experts and top-6. The table is not
a general rule, and nothing changes for shapes outside it. These rounds
use the existing swap-AB WCX FC1/FC2 kernels and the FC2 early-start
pair, with no kernel changes. Outputs stay bit-identical to the bf16
path because the products and their order are unchanged. Expert-weight
memory with WCX on is unchanged, and the compressed copies are now
encoded only for layers where the runner will use WCX. The baseline is
the previous Cake version of this backend on FlashInfer main (WCX as
shipped) with `wcx_max_tokens=128`, and "this change" is this PR, also
with `wcx_max_tokens=128`. Each of the 35 shapes was run with CUDA
graphs and in eager mode. The three window rows are faster: 1.201x
(graph and eager) for EP2 7168/2048/256/top-8 at T=1024, 1.166x graph
and 1.167x eager for EP8 7168/3072/384/top-6 at T=512, and 1.081x graph
and 1.043x eager for EP8 4096/2048/256/top-6 at T=512. The other 32 rows
run the same code path as before and stay within noise (0.998x to
1.002x).

Each latency is one MoE layer forward on NVIDIA H100 80GB HBM3 (sm_90a)
with CUDA 13.3 (V13.3.73). Absolute times are pooled medians of the
CUPTI per-iteration max-rank samples from two sessions. Speedup = 1 /
pooled median of the paired per-segment ratios (this change / previous),
so a speedup above 1 means this change is faster. The 95 % CI is 1 / the
session-stratified paired bootstrap CI of that median. "same code path"
marks a row where this change runs the previous version's code, which
here means every row outside the three windows.

**CUDA graph**

| hidden | intermediate | experts | top-k | EP | tokens per rank |
previous (us) | this change (us) | speedup [95% CI] | note |
|---|---|---|---|---|---|---|---|---|---|
| 7168 | 2048 | 256 | 8 | 8 | 8 | 789.6 | 789.8 | 1.000 [1.000, 1.000] |
same code path |
| 7168 | 2048 | 256 | 8 | 8 | 16 | 828.3 | 828.6 | 1.000 [0.999, 1.000]
| same code path |
| 7168 | 2048 | 256 | 8 | 8 | 32 | 841.6 | 841.6 | 1.000 [1.000, 1.000]
| same code path |
| 7168 | 2048 | 256 | 8 | 8 | 64 | 869.6 | 869.6 | 1.000 [1.000, 1.000]
| same code path |
| 7168 | 2048 | 256 | 8 | 8 | 128 | 928.8 | 928.8 | 1.000 [1.000, 1.001]
| same code path |
| 7168 | 2048 | 256 | 8 | 8 | 512 | 1362.3 | 1362.1 | 1.000 [1.000,
1.001] | same code path |
| 7168 | 2048 | 256 | 8 | 8 | 1024 | 1942.4 | 1944.3 | 1.000 [0.999,
1.000] | same code path |
| 7168 | 2048 | 256 | 8 | 8 | 2048 | 3323.6 | 3323.1 | 1.000 [0.999,
1.000] | same code path |
| 7168 | 2048 | 256 | 8 | 8 | 4096 | 6294.1 | 6291.2 | 1.001 [1.000,
1.001] | same code path |
| 7168 | 3072 | 384 | 6 | 8 | 8 | 1288.0 | 1287.1 | 1.000 [1.000, 1.000]
| same code path |
| 7168 | 3072 | 384 | 6 | 8 | 16 | 1616.1 | 1617.8 | 1.000 [1.000,
1.000] | same code path |
| 7168 | 3072 | 384 | 6 | 8 | 32 | 1730.3 | 1729.2 | 1.000 [1.000,
1.001] | same code path |
| 7168 | 3072 | 384 | 6 | 8 | 64 | 1766.4 | 1765.7 | 1.000 [1.000,
1.000] | same code path |
| 7168 | 3072 | 384 | 6 | 8 | 128 | 1834.9 | 1834.8 | 1.000 [0.999,
1.000] | same code path |
| 7168 | 3072 | 384 | 6 | 8 | 512 | 2468.4 | 2115.0 | 1.166 [1.162,
1.168] | |
| 7168 | 3072 | 384 | 6 | 8 | 1024 | 2784.0 | 2783.8 | 1.000 [1.000,
1.000] | same code path |
| 7168 | 3072 | 384 | 6 | 8 | 2048 | 3955.5 | 3954.9 | 1.000 [0.999,
1.001] | same code path |
| 7168 | 3072 | 384 | 6 | 8 | 4096 | 6939.2 | 6944.4 | 0.999 [0.999,
1.000] | same code path |
| 4096 | 2048 | 256 | 6 | 8 | 8 | 460.1 | 460.5 | 1.000 [0.999, 1.001] |
same code path |
| 4096 | 2048 | 256 | 6 | 8 | 16 | 502.3 | 502.1 | 1.000 [1.000, 1.000]
| same code path |
| 4096 | 2048 | 256 | 6 | 8 | 32 | 513.7 | 513.7 | 1.000 [1.000, 1.001]
| same code path |
| 4096 | 2048 | 256 | 6 | 8 | 64 | 527.3 | 527.2 | 1.000 [1.000, 1.001]
| same code path |
| 4096 | 2048 | 256 | 6 | 8 | 128 | 561.3 | 561.0 | 1.000 [1.000, 1.001]
| same code path |
| 4096 | 2048 | 256 | 6 | 8 | 512 | 779.0 | 720.4 | 1.081 [1.078, 1.082]
| |
| 4096 | 2048 | 256 | 6 | 8 | 1024 | 982.3 | 982.2 | 1.000 [1.000,
1.000] | same code path |
| 4096 | 2048 | 256 | 6 | 8 | 2048 | 1593.8 | 1594.1 | 1.000 [0.999,
1.001] | same code path |
| 4096 | 2048 | 256 | 6 | 8 | 4096 | 2859.9 | 2860.7 | 1.000 [1.000,
1.001] | same code path |
| 7168 | 2048 | 256 | 8 | 4 | 8 | 1141.1 | 1141.6 | 1.000 [1.000, 1.000]
| same code path |
| 7168 | 2048 | 256 | 8 | 4 | 128 | 1623.1 | 1623.1 | 1.000 [1.000,
1.000] | same code path |
| 7168 | 2048 | 256 | 8 | 4 | 1024 | 2415.1 | 2415.1 | 1.000 [0.999,
1.000] | same code path |
| 7168 | 2048 | 256 | 8 | 4 | 4096 | 6070.1 | 6072.1 | 1.002 [1.000,
1.004] | same code path |
| 7168 | 2048 | 256 | 8 | 2 | 8 | 1308.4 | 1308.5 | 1.000 [1.000, 1.000]
| same code path |
| 7168 | 2048 | 256 | 8 | 2 | 128 | 3046.1 | 3046.0 | 1.000 [1.000,
1.000] | same code path |
| 7168 | 2048 | 256 | 8 | 2 | 1024 | 4214.6 | 3515.0 | 1.201 [1.198,
1.203] | |
| 7168 | 2048 | 256 | 8 | 2 | 4096 | 6522.7 | 6510.1 | 1.001 [0.999,
1.003] | same code path |

**eager**

| hidden | intermediate | experts | top-k | EP | tokens per rank |
previous (us) | this change (us) | speedup [95% CI] | note |
|---|---|---|---|---|---|---|---|---|---|
| 7168 | 2048 | 256 | 8 | 8 | 8 | 795.5 | 794.4 | 1.000 [0.999, 1.000] |
same code path |
| 7168 | 2048 | 256 | 8 | 8 | 16 | 832.5 | 832.7 | 1.000 [1.000, 1.000]
| same code path |
| 7168 | 2048 | 256 | 8 | 8 | 32 | 845.9 | 846.0 | 1.000 [0.999, 1.000]
| same code path |
| 7168 | 2048 | 256 | 8 | 8 | 64 | 873.2 | 873.2 | 1.000 [0.999, 1.000]
| same code path |
| 7168 | 2048 | 256 | 8 | 8 | 128 | 932.0 | 932.2 | 0.999 [0.999, 1.000]
| same code path |
| 7168 | 2048 | 256 | 8 | 8 | 512 | 1364.6 | 1364.9 | 1.000 [0.999,
1.000] | same code path |
| 7168 | 2048 | 256 | 8 | 8 | 1024 | 1945.7 | 1945.9 | 1.000 [1.000,
1.001] | same code path |
| 7168 | 2048 | 256 | 8 | 8 | 2048 | 3325.7 | 3325.7 | 1.000 [0.999,
1.001] | same code path |
| 7168 | 2048 | 256 | 8 | 8 | 4096 | 6294.4 | 6299.0 | 1.000 [0.999,
1.001] | same code path |
| 7168 | 3072 | 384 | 6 | 8 | 8 | 1293.3 | 1292.9 | 1.000 [1.000, 1.001]
| same code path |
| 7168 | 3072 | 384 | 6 | 8 | 16 | 1622.2 | 1623.7 | 1.000 [1.000,
1.000] | same code path |
| 7168 | 3072 | 384 | 6 | 8 | 32 | 1735.3 | 1735.5 | 1.000 [0.999,
1.001] | same code path |
| 7168 | 3072 | 384 | 6 | 8 | 64 | 1770.4 | 1770.3 | 1.000 [0.999,
1.000] | same code path |
| 7168 | 3072 | 384 | 6 | 8 | 128 | 1839.0 | 1839.3 | 1.000 [0.999,
1.001] | same code path |
| 7168 | 3072 | 384 | 6 | 8 | 512 | 2473.6 | 2114.4 | 1.167 [1.163,
1.169] | |
| 7168 | 3072 | 384 | 6 | 8 | 1024 | 2788.5 | 2787.9 | 1.000 [1.000,
1.001] | same code path |
| 7168 | 3072 | 384 | 6 | 8 | 2048 | 3956.4 | 3956.4 | 1.000 [0.999,
1.001] | same code path |
| 7168 | 3072 | 384 | 6 | 8 | 4096 | 6944.1 | 6943.7 | 1.000 [0.999,
1.001] | same code path |
| 4096 | 2048 | 256 | 6 | 8 | 8 | 464.9 | 464.7 | 0.999 [0.999, 1.000] |
same code path |
| 4096 | 2048 | 256 | 6 | 8 | 16 | 510.8 | 510.9 | 1.000 [1.000, 1.001]
| same code path |
| 4096 | 2048 | 256 | 6 | 8 | 32 | 519.6 | 519.5 | 1.000 [1.000, 1.001]
| same code path |
| 4096 | 2048 | 256 | 6 | 8 | 64 | 530.9 | 531.0 | 1.000 [0.999, 1.000]
| same code path |
| 4096 | 2048 | 256 | 6 | 8 | 128 | 564.4 | 564.5 | 1.000 [1.000, 1.000]
| same code path |
| 4096 | 2048 | 256 | 6 | 8 | 512 | 783.1 | 747.8 | 1.043 [1.035, 1.049]
| |
| 4096 | 2048 | 256 | 6 | 8 | 1024 | 986.6 | 986.4 | 1.000 [1.000,
1.001] | same code path |
| 4096 | 2048 | 256 | 6 | 8 | 2048 | 1597.5 | 1596.9 | 1.000 [0.999,
1.001] | same code path |
| 4096 | 2048 | 256 | 6 | 8 | 4096 | 2862.3 | 2863.1 | 1.000 [1.000,
1.000] | same code path |
| 7168 | 2048 | 256 | 8 | 4 | 8 | 1146.2 | 1147.1 | 1.000 [0.999, 1.000]
| same code path |
| 7168 | 2048 | 256 | 8 | 4 | 128 | 1626.0 | 1626.2 | 1.000 [1.000,
1.000] | same code path |
| 7168 | 2048 | 256 | 8 | 4 | 1024 | 2418.5 | 2417.8 | 1.000 [0.999,
1.000] | same code path |
| 7168 | 2048 | 256 | 8 | 4 | 4096 | 6062.1 | 6067.6 | 0.998 [0.997,
1.001] | same code path |
| 7168 | 2048 | 256 | 8 | 2 | 8 | 1313.3 | 1313.0 | 1.000 [1.000, 1.000]
| same code path |
| 7168 | 2048 | 256 | 8 | 2 | 128 | 3048.2 | 3048.6 | 1.000 [1.000,
1.000] | same code path |
| 7168 | 2048 | 256 | 8 | 2 | 1024 | 4217.5 | 3515.7 | 1.201 [1.200,
1.203] | |
| 7168 | 2048 | 256 | 8 | 2 | 4096 | 6519.0 | 6513.8 | 1.000 [0.998,
1.003] | same code path |

The other Cake MegaMoE variants in FlashInfer are BF16 x NVFP4
(sm_103a), MXFP4 x MXFP8 (sm_120a), MXFP8 EP16 (sm_100a / sm_103a), W8A8
EP16 (sm_103a) and the MegaMoE v3 kernels (sm_100a / sm_103a), and this
backend is the sm_90a member of the family.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* WCX compressed-weight processing now applies to additional token-count
windows for selected model shapes and EP sizes when WCX and the required
early-start configuration are enabled.
* Shapes and rounds outside the supported windows, or without compatible
compressed weights, continue to use the BF16 path.
* **Documentation**
* Updated configuration guidance to clarify WCX eligibility, supported
token windows, and BF16 fallback behavior.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [94666ba](https://github.com/flashinfer-ai/flashinfer/commit/94666babec1801020de588103238954fc519d552)

- **作者**: eigen
- **时间**: 2026-10-31T22:07:45Z
- **提交信息**: feat(cake_mhc_det): with grad, add H=5120 and H=7168, faster H=4096 under side loads (#8146)

`cake_mhc_det_train` is Cake's deterministic mHC (manifold-constrained
hyper-connection) training layer. Its four with-grad entry points are
`forward_prepare`, `forward_finish`, `backward_prepare` and
`backward_finish`. Before this PR, it supports hidden size H = 4096
only. This PR adds H = 5120 and H = 7168 on sm_100a (B200, GB200) and
sm_103a (GB300). sm_107a keeps H = 4096. This PR also changes two H =
4096 schedules on sm_100a so they run faster under side loads.

## H = 5120 and H = 7168

On all three GPUs, Cake is 10.61x to 14.99x faster than the best PyTorch
baseline on forward. It is 5.86x to 7.08x faster on backward and on
forward + backward.

No previous Cake version exists at these sizes. FlashInfer's existing
mHC kernels are inference forward kernels with no backward, so the
baseline is the same layer in PyTorch. It runs three ways: eager,
torch.compile (default mode) and torch.compile mode="max-autotune".
Every side uses the same math, with IEEE FP32 arithmetic and TF32 off.
Activations are BF16 in and out, parameters and their gradients are
FP32, and Sinkhorn runs 20 iterations. Input X is BF16 `[T, 4, H]` with
T = 4096, 14928 and 16263. **forward** is `forward_prepare` +
`forward_finish`. **backward** is `backward_prepare` +
`backward_finish`, and an untimed forward runs before each timed
backward. **forward + backward** is the four calls back to back. Times
are ms per call from CUDA events, and compile time is excluded. Each
repeat runs 3 warm-up calls and 20 timed calls. There are 2 repeats in
each of 3 worker processes. The tables show the median over processes of
each process's median. No side load runs. **Speedup vs best baseline**
is the fastest of the three PyTorch times divided by the Cake time, per
row. The best baseline is torch.compile max-autotune on every backward
and forward + backward row. On forward, it is mostly default
torch.compile.

**NVIDIA B200 (sm_100a, 148 SMs), CUDA 13.4, PyTorch 2.14.1+cu130**

| H | T | Pass | eager ms | torch.compile ms | torch.compile
max-autotune ms | Cake ms | Speedup vs best baseline |
|---|---|---|---|---|---|---|---|
| 5120 | 4096 | forward | 2.857 | 1.513 | 4.845 | 0.1311 | 11.54x |
| 5120 | 4096 | backward | 4.764 | 1.784 | 1.418 | 0.2335 | 6.07x |
| 5120 | 4096 | forward + backward | 7.62 | 3.293 | 2.493 | 0.3592 |
6.94x |
| 5120 | 14928 | forward | 8.977 | 4.794 | 7.103 | 0.4318 | 11.10x |
| 5120 | 14928 | backward | 15.08 | 5.819 | 4.629 | 0.727 | 6.37x |
| 5120 | 14928 | forward + backward | 24.05 | 10.61 | 7.832 | 1.17 |
6.69x |
| 5120 | 16263 | forward | 11.53 | 7.005 | 7.245 | 0.4672 | 14.99x |
| 5120 | 16263 | backward | 16.31 | 6.289 | 5.029 | 0.8015 | 6.27x |
| 5120 | 16263 | forward + backward | 27.83 | 13.29 | 8.386 | 1.282 |
6.54x |
| 7168 | 4096 | forward | 3.851 | 2.074 | 5.489 | 0.1761 | 11.78x |
| 7168 | 4096 | backward | 6.308 | 2.402 | 1.893 | 0.3143 | 6.02x |
| 7168 | 4096 | forward + backward | 10.16 | 4.475 | 3.424 | 0.4835 |
7.08x |
| 7168 | 14928 | forward | 14.74 | 9.043 | 8.266 | 0.5939 | 13.92x |
| 7168 | 14928 | backward | 20.53 | 7.914 | 6.209 | 1.026 | 6.05x |
| 7168 | 14928 | forward + backward | 35.27 | 16.96 | 10.56 | 1.671 |
6.32x |
| 7168 | 16263 | forward | 15.97 | 9.799 | 8.569 | 0.6448 | 13.29x |
| 7168 | 16263 | backward | 22.23 | 8.579 | 6.748 | 1.123 | 6.01x |
| 7168 | 16263 | forward + backward | 38.19 | 18.38 | 11.43 | 1.795 |
6.37x |

**NVIDIA GB200 (sm_100a, 152 SMs), CUDA 13.4, PyTorch 2.14.1+cu130**

| H | T | Pass | eager ms | torch.compile ms | torch.compile
max-autotune ms | Cake ms | Speedup vs best baseline |
|---|---|---|---|---|---|---|---|
| 5120 | 4096 | forward | 2.704 | 1.439 | 5.545 | 0.1269 | 11.34x |
| 5120 | 4096 | backward | 4.557 | 1.706 | 1.395 | 0.2274 | 6.13x |
| 5120 | 4096 | forward + backward | 7.256 | 3.141 | 2.469 | 0.3489 |
7.08x |
| 5120 | 14928 | forward | 8.461 | 4.51 | 7.601 | 0.4239 | 10.64x |
| 5120 | 14928 | backward | 14.36 | 5.527 | 4.414 | 0.7018 | 6.29x |
| 5120 | 14928 | forward + backward | 22.82 | 10.04 | 7.447 | 1.117 |
6.67x |
| 5120 | 16263 | forward | 10.84 | 6.581 | 7.639 | 0.4584 | 14.36x |
| 5120 | 16263 | backward | 15.53 | 5.973 | 4.769 | 0.7629 | 6.25x |
| 5120 | 16263 | forward + backward | 26.37 | 12.55 | 7.97 | 1.212 |
6.58x |
| 7168 | 4096 | forward | 3.64 | 1.959 | 6.401 | 0.1699 | 11.53x |
| 7168 | 4096 | backward | 5.977 | 2.248 | 1.803 | 0.2986 | 6.04x |
| 7168 | 4096 | forward + backward | 9.612 | 4.205 | 3.255 | 0.4603 |
7.07x |
| 7168 | 14928 | forward | 13.87 | 8.498 | 8.658 | 0.5789 | 14.68x |
| 7168 | 14928 | backward | 19.55 | 7.501 | 5.847 | 0.9555 | 6.12x |
| 7168 | 14928 | forward + backward | 33.43 | 16 | 9.981 | 1.526 | 6.54x
|
| 7168 | 16263 | forward | 15.02 | 9.2 | 9.288 | 0.6287 | 14.63x |
| 7168 | 16263 | backward | 21.17 | 8.124 | 6.367 | 1.03 | 6.18x |
| 7168 | 16263 | forward + backward | 36.18 | 17.32 | 11.06 | 1.651 |
6.70x |

**NVIDIA GB300 (sm_103a, 152 SMs), CUDA 13.4, PyTorch 2.14.1+cu130**

| H | T | Pass | eager ms | torch.compile ms | torch.compile
max-autotune ms | Cake ms | Speedup vs best baseline |
|---|---|---|---|---|---|---|---|
| 5120 | 4096 | forward | 2.677 | 1.426 | 5.469 | 0.127 | 11.23x |
| 5120 | 4096 | backward | 4.502 | 1.693 | 1.354 | 0.231 | 5.86x |
| 5120 | 4096 | forward + backward | 7.176 | 3.116 | 2.408 | 0.3525 |
6.83x |
| 5120 | 14928 | forward | 8.372 | 4.487 | 7.426 | 0.423 | 10.61x |
| 5120 | 14928 | backward | 14.2 | 5.493 | 4.392 | 0.7021 | 6.26x |
| 5120 | 14928 | forward + backward | 22.57 | 9.979 | 7.393 | 1.117 |
6.62x |
| 5120 | 16263 | forward | 10.73 | 6.527 | 7.554 | 0.4585 | 14.24x |
| 5120 | 16263 | backward | 15.36 | 5.971 | 4.753 | 0.7635 | 6.23x |
| 5120 | 16263 | forward + backward | 26.09 | 12.5 | 7.904 | 1.214 |
6.51x |
| 7168 | 4096 | forward | 3.604 | 1.947 | 6.217 | 0.1708 | 11.40x |
| 7168 | 4096 | backward | 5.91 | 2.23 | 1.756 | 0.2966 | 5.92x |
| 7168 | 4096 | forward + backward | 9.509 | 4.174 | 3.195 | 0.4627 |
6.91x |
| 7168 | 14928 | forward | 13.73 | 8.443 | 8.533 | 0.5793 | 14.57x |
| 7168 | 14928 | backward | 19.35 | 7.471 | 5.864 | 0.953 | 6.15x |
| 7168 | 14928 | forward + backward | 33.08 | 15.91 | 9.958 | 1.525 |
6.53x |
| 7168 | 16263 | forward | 14.86 | 9.133 | 8.905 | 0.6325 | 14.08x |
| 7168 | 16263 | backward | 20.94 | 8.126 | 6.359 | 1.029 | 6.18x |
| 7168 | 16263 | forward + backward | 35.8 | 17.26 | 10.76 | 1.654 |
6.51x |

## H = 4096 under side loads on sm_100a

On sm_100a, this PR changes two H = 4096 schedules that slow down or
block under side loads.

- `backward_finish`: At some token ranges, main runs its column-slab
pass in a static form. On B200 these ranges are T in 1665–1728,
2689–2880, 3201–3456 and 3713–4032; the GB200 rows are in the table. The
static form waits for every CTA to become resident. So it does not
finish while another stream holds every SM. This PR routes those ranges
to the dynamic-claim form. Under full-SM hold, main is blocked at every
row and the PR completes. Under 16 x 640, the PR is 1.21x–1.27x faster
on B200 and 1.14x–1.19x faster on GB200. Under the all-reduce-like load,
it is 1.28x–1.34x faster on B200 and 1.20x–1.23x faster on GB200.
Unloaded, the speedup is 1.00x–1.01x on B200 and 1.00x on GB200.
- `forward_prepare`: The mapping pass's tail round now gives each CTA
one K unit. This applies near T = 4096; the table shows the measured T.
Under full-SM hold, the PR is 1.17x faster on B200 and 1.13x–1.18x
faster on GB200. Unloaded and under the 16 x 640 and all-reduce-like
loads, the speedup is 1.00x–1.01x.

The baseline is the previous Cake version of these kernels on FlashInfer
`main`. Input is BF16 X `[T, 4, 4096]`. Each load runs on a second
stream. **none** means no load. **16 x 640** means 16 CTAs of 640
threads. **full-SM hold** means one 128-thread CTA per SM at the maximum
shared-memory carveout. That is 148 CTAs on B200 and 152 on GB200. **32
x 544 (all-reduce-like)** means 32 CTAs of 544 threads, each with
119,040 B of shared memory. Times are ms per call from CUDA events. Each
repeat runs 3 warm-up calls and 20 timed calls, and the median is taken
per repeat. Then the median is taken over groups. The tables show the
mean of two sessions on two different nodes. Speedup = main ms / PR ms,
and above 1 means the PR is faster. **blocked** means main does not
finish while the hold is resident.

**NVIDIA B200 (sm_100a, 148 SMs), CUDA 13.4, PyTorch 2.14.1+cu130**

| Kernel | T | Side load | main ms | PR ms | Speedup |
|---|---|---|---|---|---|
| backward_finish | 1665 | none | 0.0707 | 0.0707 | 1.00x |
| backward_finish | 1665 | 16 x 640 | 0.0942 | 0.0778 | 1.21x |
| backward_finish | 1665 | full-SM hold | blocked | 0.0748 | — |
| backward_finish | 1665 | 32 x 544 (all-reduce-like) | 0.1024 | 0.0779
| 1.31x |
| backward_finish | 1696 | none | 0.0707 | 0.0707 | 1.00x |
| backward_finish | 1696 | 16 x 640 | 0.0942 | 0.0778 | 1.21x |
| backward_finish | 1696 | full-SM hold | blocked | 0.0737 | — |
| backward_finish | 1696 | 32 x 544 (all-reduce-like) | 0.1024 | 0.0783
| 1.31x |
| backward_finish | 1728 | none | 0.0707 | 0.0707 | 1.00x |
| backward_finish | 1728 | 16 x 640 | 0.0942 | 0.0778 | 1.21x |
| backward_finish | 1728 | full-SM hold | blocked | 0.0737 | — |
| backward_finish | 1728 | 32 x 544 (all-reduce-like) | 0.1024 | 0.0779
| 1.31x |
| backward_finish | 2689 | none | 0.1054 | 0.1055 | 1.00x |
| backward_finish | 2689 | 16 x 640 | 0.1374 | 0.1127 | 1.22x |
| backward_finish | 2689 | full-SM hold | blocked | 0.1086 | — |
| backward_finish | 2689 | 32 x 544 (all-reduce-like) | 0.1495 | 0.1168
| 1.28x |
| backward_finish | 2784 | none | 0.1054 | 0.1055 | 1.00x |
| backward_finish | 2784 | 16 x 640 | 0.1413 | 0.1147 | 1.23x |
| backward_finish | 2784 | full-SM hold | blocked | 0.1086 | — |
| backward_finish | 2784 | 32 x 544 (all-reduce-like) | 0.1520 | 0.1169
| 1.30x |
| backward_finish | 2880 | none | 0.1055 | 0.1058 | 1.00x |
| backward_finish | 2880 | 16 x 640 | 0.1434 | 0.1167 | 1.23x |
| backward_finish | 2880 | full-SM hold | blocked | 0.1100 | — |
| backward_finish | 2880 | 32 x 544 (all-reduce-like) | 0.1550 | 0.1187
| 1.31x |
| backward_finish | 3201 | none | 0.1158 | 0.1158 | 1.00x |
| backward_finish | 3201 | 16 x 640 | 0.1537 | 0.1230 | 1.25x |
| backward_finish | 3201 | full-SM hold | blocked | 0.1201 | — |
| backward_finish | 3201 | 32 x 544 (all-reduce-like) | 0.1679 | 0.1291
| 1.30x |
| backward_finish | 3328 | none | 0.1158 | 0.1158 | 1.00x |
| backward_finish | 3328 | 16 x 640 | 0.1559 | 0.1270 | 1.23x |
| backward_finish | 3328 | full-SM hold | blocked | 0.1198 | — |
| backward_finish | 3328 | 32 x 544 (all-reduce-like) | 0.1701 | 0.1308
| 1.30x |
| backward_finish | 3456 | none | 0.1176 | 0.1177 | 1.00x |
| backward_finish | 3456 | 16 x 640 | 0.1618 | 0.1295 | 1.25x |
| backward_finish | 3456 | full-SM hold | blocked | 0.1209 | — |
| backward_finish | 3456 | 32 x 544 (all-reduce-like) | 0.1761 | 0.1311
| 1.34x |
| backward_finish | 3713 | none | 0.1269 | 0.1260 | 1.01x |
| backward_finish | 3713 | 16 x 640 | 0.1700 | 0.1338 | 1.27x |
| backward_finish | 3713 | full-SM hold | blocked | 0.1294 | — |
| backward_finish | 3713 | 32 x 544 (all-reduce-like) | 0.1966 | 0.1530
| 1.28x |
| backward_finish | 3872 | none | 0.1280 | 0.1273 | 1.01x |
| backward_finish | 3872 | 16 x 640 | 0.1756 | 0.1405 | 1.25x |
| backward_finish | 3872 | full-SM hold | blocked | 0.1311 | — |
| backward_finish | 3872 | 32 x 544 (all-reduce-like) | 0.2130 | 0.1664
| 1.28x |
| backward_finish | 4032 | none | 0.1281 | 0.1281 | 1.00x |
| backward_finish | 4032 | 16 x 640 | 0.1803 | 0.1434 | 1.26x |
| backward_finish | 4032 | full-SM hold | blocked | 0.1311 | — |
| backward_finish | 4032 | 32 x 544 (all-reduce-like) | 0.2190 | 0.1680
| 1.30x |
| forward_prepare | 4096 | none | 0.0584 | 0.0586 | 1.00x |
| forward_prepare | 4096 | 16 x 640 | 0.0593 | 0.0593 | 1.00x |
| forward_prepare | 4096 | full-SM hold | 0.0740 | 0.0635 | 1.17x |
| forward_prepare | 4096 | 32 x 544 (all-reduce-like) | 0.0721 | 0.0720
| 1.00x |

**NVIDIA GB200 (sm_100a, 152 SMs), CUDA 13.4, PyTorch 2.14.1+cu130**

| Kernel | T | Side load | main ms | PR ms | Speedup |
|---|---|---|---|---|---|
| backward_finish | 2689 | none | 0.1019 | 0.1020 | 1.00x |
| backward_finish | 2689 | 16 x 640 | 0.1290 | 0.1080 | 1.19x |
| backward_finish | 2689 | full-SM hold | blocked | 0.1072 | — |
| backward_finish | 2689 | 32 x 544 (all-reduce-like) | 0.1331 | 0.1107
| 1.20x |
| backward_finish | 2784 | none | 0.1026 | 0.1023 | 1.00x |
| backward_finish | 2784 | 16 x 640 | 0.1290 | 0.1106 | 1.17x |
| backward_finish | 2784 | full-SM hold | blocked | 0.1060 | — |
| backward_finish | 2784 | 32 x 544 (all-reduce-like) | 0.1352 | 0.1107
| 1.22x |
| backward_finish | 2880 | none | 0.1030 | 0.1034 | 1.00x |
| backward_finish | 2880 | 16 x 640 | 0.1298 | 0.1135 | 1.14x |
| backward_finish | 2880 | full-SM hold | blocked | 0.1069 | — |
| backward_finish | 2880 | 32 x 544 (all-reduce-like) | 0.1381 | 0.1121
| 1.23x |
| forward_prepare | 3585 | none | 0.0530 | 0.0532 | 1.00x |
| forward_prepare | 3585 | 16 x 640 | 0.0532 | 0.0532 | 1.00x |
| forward_prepare | 3585 | full-SM hold | 0.0676 | 0.0573 | 1.18x |
| forward_prepare | 3585 | 32 x 544 (all-reduce-like) | 0.0532 | 0.0532
| 1.00x |
| forward_prepare | 4096 | none | 0.0566 | 0.0568 | 1.00x |
| forward_prepare | 4096 | 16 x 640 | 0.0558 | 0.0558 | 1.00x |
| forward_prepare | 4096 | full-SM hold | 0.0717 | 0.0614 | 1.17x |
| forward_prepare | 4096 | 32 x 544 (all-reduce-like) | 0.0696 | 0.0696
| 1.00x |
| forward_prepare | 4608 | none | 0.0613 | 0.0611 | 1.00x |
| forward_prepare | 4608 | 16 x 640 | 0.0755 | 0.0755 | 1.00x |
| forward_prepare | 4608 | full-SM hold | 0.0778 | 0.0676 | 1.15x |
| forward_prepare | 4608 | 32 x 544 (all-reduce-like) | 0.0739 | 0.0738
| 1.00x |
| forward_prepare | 4864 | none | 0.0637 | 0.0637 | 1.00x |
| forward_prepare | 4864 | 16 x 640 | 0.0761 | 0.0761 | 1.00x |
| forward_prepare | 4864 | full-SM hold | 0.0794 | 0.0701 | 1.13x |
| forward_prepare | 4864 | 32 x 544 (all-reduce-like) | 0.0775 | 0.0769
| 1.01x |

Cake also ships the mHC training head (stream-mean forward and its
backward) as `cake_mhc_det_train_head`, and this family on sm_100a,
sm_103a and sm_107a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Deterministic mHC training now supports hidden sizes 4096, 5120, and
7168 on SM100/SM103, and 4096 on SM107.
* Workspace sizing and allocation helpers accept a `hidden` option,
defaulting to 4096.
* **Documentation**
* Clarified supported hidden sizes, workspace usage, and side-stream
behavior.
* **Compatibility**
* The experimental nondeterministic package remains limited to hidden
size 4096; other sizes raise `ValueError`.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [35ea8e2](https://github.com/flashinfer-ai/flashinfer/commit/35ea8e25aa5aab5bf32978947bb1dd3d39aade0b)

- **作者**: eigen
- **时间**: 2026-10-31T21:48:02Z
- **提交信息**: feat(cake_msa_icp_indexer): MSA-compatible index-context-parallel indexer for TP2/TP4, P128/P256, SM100/SM103/SM107 (#8122)

This PR adds the experimental `cake_msa_icp_indexer` package and the
`flashinfer.msa_ops` facade. Together they provide the MiniMax-M3
sparse-attention (MSA) indexer with index context parallelism (ICP). It
is compatible with the MSA indexer CP contract of vllm-project/MSA#46,
which vLLM#61929 and vLLM#63671 consume. The kernel family uses FP8
index Q/K with head dim 128 and ranks on logical 128-token blocks. It
supports tensor-parallel worlds TP2 and TP4, with page sizes 128 (P128,
rows interleaved across ranks) and 256 (P256, contiguous shards). This
PR delivers all of these variants. The tables compare end-to-end serving
with this PR (FI) against the existing MSA indexer path (MSA).

**Steady cohort (concurrency 14)**

| GPU | TP | Page | Decode MSA (ms) | Decode FI (ms) | Speedup (MSA/FI)
| Throughput MSA (tok/s) | Throughput FI (tok/s) | Speedup (FI/MSA) |
|---|---|---|---|---|---|---|---|---|
| GB300 | 2 | 128 | 18.002 | 17.335 | 1.04x | 1044.059 | 1092.343 |
1.05x |
| GB300 | 2 | 256 | 18.663 | 17.099 | 1.09x | 1013.028 | 1076.320 |
1.06x |
| GB300 | 4 | 128 | 12.879 | 12.513 | 1.03x | 1255.302 | 1314.064 |
1.05x |
| GB300 | 4 | 256 | 12.777 | 12.140 | 1.05x | 1236.385 | 1310.138 |
1.06x |
| VR200 | 2 | 128 | 14.771 | 14.504 | 1.02x | 1397.364 | 1485.943 |
1.06x |
| VR200 | 2 | 256 | 14.788 | 14.332 | 1.03x | 1397.063 | 1476.033 |
1.06x |
| VR200 | 4 | 128 | 9.761 | 9.520 | 1.03x | 1873.592 | 2031.197 | 1.08x
|
| VR200 | 4 | 256 | 9.745 | 9.344 | 1.04x | 1907.858 | 2044.431 | 1.07x
|

**Mixed cohort (concurrency 14+1)**

| GPU | TP | Page | Decode MSA (ms) | Decode FI (ms) | Speedup (MSA/FI)
| Throughput MSA (tok/s) | Throughput FI (tok/s) | Speedup (FI/MSA) |
|---|---|---|---|---|---|---|---|---|
| GB300 | 2 | 128 | 18.947 | 18.767 | 1.01x | 1026.866 | 1059.097 |
1.03x |
| GB300 | 2 | 256 | 19.583 | 18.675 | 1.05x | 997.367 | 1037.341 | 1.04x
|
| GB300 | 4 | 128 | 13.120 | 12.707 | 1.03x | 1280.003 | 1295.962 |
1.01x |
| GB300 | 4 | 256 | 13.048 | 12.573 | 1.04x | 1245.489 | 1281.821 |
1.03x |
| VR200 | 2 | 128 | 15.299 | 15.030 | 1.02x | 1405.086 | 1469.175 |
1.05x |
| VR200 | 2 | 256 | 15.421 | 15.004 | 1.03x | 1400.678 | 1459.226 |
1.04x |
| VR200 | 4 | 128 | 10.195 | 9.976 | 1.02x | 1791.990 | 1926.870 | 1.08x
|
| VR200 | 4 | 256 | 10.091 | 9.721 | 1.04x | 1841.901 | 1962.768 | 1.07x
|

*GPUs: GB300 (sm_103a, 152 SMs) and VR200/R200 (sm_107a, 212-SM board).
The kernels were built with CUDA 13.4 (nvcc 13.4) and run on PyTorch
2.14.0+cu130. Workload: full-model vLLM serving of MiniMax-M3-NVFP4 with
EAGLE3 speculative decoding (k=3), ISL 163840 / OSL 8192, at concurrency
14 (steady) and 14+1 (mixed). Values are rank-0 GPU-time medians. Decode
is the decode step time and throughput is output throughput. Rounds per
row: GB300 n=2 (ABBA), VR200 TP4 n=3, VR200 TP2 n=1. Baseline (MSA): the
MSA indexer path, vllm-project/MSA#46 at f380d0e88e2e, called through
vLLM#63671 (a76900d6eee7).*

The kernels ship for sm_100a (B200), sm_103a (GB300) and sm_107a
(R200/VR200, which uses its own native sm_107a programs), and there are
no variants beyond FP8 Q/K head dim 128, TP2/TP4 and P128/P256; no B200
end-to-end measurement exists, so the tables have no sm_100a rows.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added experimental MSA ICP indexing for prefill and decode, including
sharded scoring, Top16 selection, candidate merging, and an optional
fused decode path.
* Added serving-plan helpers, communication layouts, and support for
compute capabilities 10.0, 10.3, and 10.7.
  * Added a configurable benchmark comparing FlashInfer and MSA paths.
* **Documentation**
* Expanded guidance for setup, buffer management, communication, warmup,
and graph capture.
* **Breaking Changes**
* Removed the previous decode-chain preparation and workspace lifecycle
APIs; use the per-rank serving-plan and operation APIs instead.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [b882566](https://github.com/flashinfer-ai/flashinfer/commit/b8825667b3dbfaa05b3f5cb0eafd2043054caa6d)

- **作者**: eigen
- **时间**: 2026-10-31T21:44:50Z
- **提交信息**: perf(cake_kimi_k3_attn_res): retune dense routes at M 384 and 512 on B200 and B300 (#8143)

### [22eb882](https://github.com/flashinfer-ai/flashinfer/commit/22eb8825a5d2f51432001abce0c29a5f36782257)

- **作者**: eigen
- **时间**: 2026-10-31T21:44:24Z
- **提交信息**: perf(cake_dsa_indexer_det): retune host-side split policy and sm_107a l6 program choice (#8145)

### [6a08f19](https://github.com/flashinfer-ai/flashinfer/commit/6a08f19e1da9e8d2d7a6a7a102c38f8f8541cb8e)

- **作者**: eigen
- **时间**: 2026-10-31T21:44:09Z
- **提交信息**: perf(cake_deepgemm_dense_mqa): extend the FP4 single-launch scan classes by one KV block on sm_103a (#8142)

### [f342c41](https://github.com/flashinfer-ai/flashinfer/commit/f342c41fb68094e36dd0f387d3f0399c7176082b)

- **作者**: eigen
- **时间**: 2026-10-31T21:43:54Z
- **提交信息**: perf(cake_fmha): FP8 paged context routes for short-KV and one-wave launches (#8140)

### [58ece34](https://github.com/flashinfer-ai/flashinfer/commit/58ece34ea74ad39f9d641443fa14be28e5c7dabb)

- **作者**: eigen
- **时间**: 2026-10-31T21:43:39Z
- **提交信息**: perf(cake_moe_finalize_allreduce_fusion): extend the small-token program to top_k 4 without a shared expert at world size 4 (#8139)

### [ce393bc](https://github.com/flashinfer-ai/flashinfer/commit/ce393bc11b893da6f504f4e3dcb59711b3dca9c9)

- **作者**: eigen
- **时间**: 2026-10-31T21:43:24Z
- **提交信息**: perf(cake_dsv4): faster BF16 / FP8 sparse-MLA third follow-up on SM100 / SM103 (#8138)

### [9112f5b](https://github.com/flashinfer-ai/flashinfer/commit/9112f5b919b7eed550b26f617a303820115c8905)

- **作者**: eigen
- **时间**: 2026-10-31T20:38:15Z
- **提交信息**: perf(cake_dense_projection_det_gemm): regenerate programs and use eight-warp input-gradient programs on sm_100a (#8129)

The Cake `dense_projection_det_gemm` package in
`flashinfer.experimental` is the deterministic dense projection GEMM.
Its previous name, `dense_projection_gemm`, still works as an alias. The
package has 127 programs built from 124 templates. Most are BF16-operand
dense GEMMs that write BF16 or FP32 output in four operand layouts (kk,
kn, nk, nn), and there is also an FP32 router GEMM that runs through
BF16x3 emulation. This PR regenerates the package from the current
kernel sources with two code-generation fixes. First, the
transposed-output weight-gradient programs keep the one-CTA-per-SM
register budget again and no longer spill registers. Second, the
half-tile split forms no longer keep a dead workspace store, so the
narrow 4096/5120 -> 32/48 input-gradient program is back to 131
registers. 41 of the 127 programs change machine code, and no program or
template is added. On `sm_100a` (GB200), 10 input-gradient rows now use
the eight-warp CTA programs that already ship for `sm_103a`: 4096->64,
5120->64, 4096->512, 5120->512 and 6144->576 (kv_a), each at both T
values. The FP32 router GEMM's single-split kk and kn launches store
16-byte vectors into the output. Those launches now raise `ValueError`
when the output tensor does not start at a 16-byte-aligned address,
where such a call used to fault with a CUDA misaligned-address error.
Other launches are unchanged.

The baseline is the previous Cake version, which is the package
currently on main, run on the same GPU with CUDA 13.4. Across the
294-row shape list, the geomean speedup is 1.004 on NVIDIA GB200
(`sm_100a`, per-row 0.990-1.138), 1.002 on NVIDIA GB300 (`sm_103a`,
0.990-1.040) and 1.006 on Rubin (`sm_107a`, 0.991-1.244). No row is
below 0.990 on any GPU. The largest gains are:

- Rubin FP32 weight gradients 4096/5120 -> 32/48/64: 1.09-1.24x. For
example, 4096->64 at T16384 goes from 30.7 to 24.7 µs and 5120->64 at
T16384 from 32.6 to 26.4 µs.
- Thin 4096 -> 32/48/64/128 weight gradients on GB200 and GB300:
1.02-1.04x.
- GB200 4096->512 BF16 input gradient: 51.2 -> 49.3 µs (1.038) at T16231
and 50.6 -> 49.5 µs (1.024) at T16384.

On rows whose programs and plans do not change, the ratios are
run-to-run variation: Rubin 0.991-1.026, GB300 0.990-1.013 and GB200
0.990-1.116 (GB200 timing varies more between runs). Outputs are bitwise
identical to the previous version on all 294 shapes on all three GPUs.

The package ships BF16 and FP32 outputs in the kk, kn, nk and nn operand
layouts, weight- and input-gradient forms including the half-tile split
forms, eight-warp CTA programs on `sm_100a` and `sm_103a`, and the FP32
router GEMM through BF16x3 emulation. It has programs for `sm_100a`
(GB200), `sm_103a` (GB300) and `sm_107a` (Rubin): 256 build entries (83
/ 86 / 87, two more on `sm_100a` than before) and 127 registry records.

Times in µs on NVIDIA GB200 (`sm_100a`, 152 SMs), NVIDIA GB300
(`sm_103a`, 152 SMs) and Rubin (`sm_107a`, 216 SMs) with CUDA 13.4: one
row per shape of the 294-row shape list at T = 16172, 16231 or 16384
token rows, speedup = previous Cake version / this PR, and rows
re-measured in a 10-group confirmation run show that measurement.

| shape (K→N) | op | out | T | GB200 previous µs | GB200 this PR µs |
GB200 speedup | GB300 previous µs | GB300 this PR µs | GB300 speedup |
Rubin previous µs | Rubin this PR µs | Rubin speedup |
|---|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| indexer_q (2048→4096) | dgrad | bf16 | 16172 | 173.7 | 173.8 | 1.000 |
141.9 | 141.7 | 1.001 | 79.4 | 79.5 | 0.999 |
| indexer_q (2048→4096) | dgrad | bf16 | 16231 | 173.4 | 173.8 | 0.998 |
141.8 | 141.8 | 1.001 | 79.2 | 79.3 | 0.999 |
| indexer_q (2048→4096) | fwd | bf16 | 16172 | 170.7 | 170.2 | 1.003 |
138.7 | 138.8 | 0.999 | 79.1 | 79.0 | 1.001 |
| indexer_q (2048→4096) | fwd | bf16 | 16231 | 171.3 | 171.0 | 1.002 |
139.5 | 139.6 | 1.000 | 79.1 | 79.1 | 1.000 |
| indexer_q (2048→4096) | wgrad | bf16 | 16172 | 179.0 | 179.2 | 0.999 |
147.5 | 147.6 | 0.999 | 78.8 | 78.9 | 0.999 |
| indexer_q (2048→4096) | wgrad | bf16 | 16231 | 180.2 | 180.4 | 0.999 |
148.1 | 148.3 | 0.999 | 79.2 | 79.2 | 0.999 |
| indexer_q (2048→4096) | wgrad | f32 | 16172 | 175.8 | 177.4 | 0.991 |
146.2 | 146.3 | 0.999 | 81.0 | 81.0 | 1.000 |
| indexer_q (2048→4096) | wgrad | f32 | 16231 | 177.7 | 178.1 | 0.998 |
146.8 | 147.1 | 0.998 | 81.2 | 81.3 | 0.999 |
| shared_down (2048→6144) | dgrad | bf16 | 16172 | 257.3 | 258.1 | 0.997
| 215.1 | 216.4 | 0.994 | 115.7 | 115.7 | 1.000 |
| shared_down (2048→6144) | dgrad | bf16 | 16231 | 256.1 | 256.1 | 1.000
| 216.0 | 215.8 | 1.001 | 115.6 | 115.7 | 0.999 |
| shared_down (2048→6144) | dgrad | f32 | 16172 | 259.1 | 260.8 | 0.994
| 218.9 | 219.5 | 0.997 | 117.8 | 117.8 | 1.000 |
| shared_down (2048→6144) | dgrad | f32 | 16231 | 259.6 | 259.4 | 1.001
| 218.3 | 217.9 | 1.002 | 117.9 | 117.9 | 1.001 |
| shared_down (2048→6144) | fwd | bf16 | 16172 | 248.1 | 249.9 | 0.993 |
211.4 | 211.6 | 0.999 | 111.2 | 111.2 | 1.000 |
| shared_down (2048→6144) | fwd | bf16 | 16231 | 248.3 | 249.8 | 0.994 |
211.3 | 211.4 | 1.000 | 111.2 | 111.1 | 1.000 |
| shared_down (2048→6144) | wgrad | bf16 | 16172 | 259.6 | 259.4 | 1.001
| 218.4 | 218.4 | 1.000 | 115.4 | 115.6 | 0.998 |
| shared_down (2048→6144) | wgrad | bf16 | 16231 | 260.5 | 261.2 | 0.997
| 218.6 | 218.9 | 0.999 | 115.8 | 116.1 | 0.998 |
| shared_down (2048→6144) | wgrad | f32 | 16172 | 262.9 | 262.1 | 1.003
| 219.8 | 219.4 | 1.002 | 116.6 | 116.5 | 1.001 |
| shared_down (2048→6144) | wgrad | f32 | 16231 | 262.1 | 262.6 | 0.998
| 220.6 | 220.2 | 1.002 | 117.1 | 117.0 | 1.001 |
| q_b (2048→16384) | dgrad | bf16 | 16172 | 648.8 | 649.2 | 0.999 |
577.4 | 576.9 | 1.001 | 297.6 | 298.5 | 0.997 |
| q_b (2048→16384) | dgrad | bf16 | 16231 | 648.4 | 648.5 | 1.000 |
576.8 | 577.0 | 1.000 | 299.0 | 299.5 | 0.998 |
| q_b (2048→16384) | dgrad | f32 | 16172 | 647.9 | 649.1 | 0.998 | 578.0
| 578.9 | 0.998 | 305.2 | 304.8 | 1.001 |
| q_b (2048→16384) | dgrad | f32 | 16231 | 648.8 | 649.1 | 1.000 | 577.9
| 577.3 | 1.001 | 305.5 | 305.2 | 1.001 |
| q_b (2048→16384) | fwd | bf16 | 16172 | 612.6 | 613.3 | 0.999 | 549.1
| 549.8 | 0.999 | 295.9 | 295.8 | 1.000 |
| q_b (2048→16384) | fwd | bf16 | 16231 | 613.6 | 615.5 | 0.997 | 547.3
| 548.5 | 0.998 | 296.3 | 296.1 | 1.001 |
| q_b (2048→16384) | wgrad | bf16 | 16172 | 632.8 | 634.2 | 0.998 |
566.2 | 564.5 | 1.003 | 294.9 | 295.2 | 0.999 |
| q_b (2048→16384) | wgrad | bf16 | 16231 | 637.1 | 637.4 | 0.999 |
565.5 | 566.4 | 0.999 | 297.0 | 296.4 | 1.002 |
| q_b (2048→16384) | wgrad | f32 | 16172 | 642.0 | 645.6 | 0.994 | 572.1
| 572.1 | 1.000 | 296.1 | 295.8 | 1.001 |
| q_b (2048→16384) | wgrad | f32 | 16231 | 647.6 | 645.0 | 1.004 | 574.5
| 575.0 | 0.999 | 297.0 | 297.3 | 0.999 |
| 4096→32 | dgrad | bf16 | 16231 | 24.4 | 24.3 | 1.003 | 23.2 | 23.2 |
0.997 | 16.8 | 16.8 | 1.004 |
| 4096→32 | dgrad | bf16 | 16384 | 24.3 | 24.4 | 0.998 | 23.5 | 23.3 |
1.007 | 16.8 | 16.9 | 0.996 |
| 4096→32 | dgrad | f32 | 16231 | 44.8 | 44.8 | 1.000 | 43.1 | 42.9 |
1.005 | 30.2 | 30.3 | 0.999 |
| 4096→32 | dgrad | f32 | 16384 | 45.3 | 45.2 | 1.004 | 43.1 | 43.4 |
0.993 | 30.4 | 30.4 | 1.001 |
| 4096→32 | fwd | bf16 | 16231 | 25.9 | 25.9 | 1.002 | 26.9 | 27.0 |
0.999 | 19.3 | 19.4 | 0.996 |
| 4096→32 | fwd | bf16 | 16384 | 25.8 | 25.7 | 1.002 | 26.7 | 26.6 |
1.004 | 19.7 | 19.8 | 0.998 |
| 4096→32 | wgrad | bf16 | 16231 | 28.0 | 27.4 | 1.025 | 28.5 | 27.4 |
1.040 | 20.0 | 20.1 | 0.995 |
| 4096→32 | wgrad | bf16 | 16384 | 27.9 | 27.1 | 1.029 | 28.5 | 27.6 |
1.035 | 20.3 | 20.3 | 1.002 |
| 4096→32 | wgrad | f32 | 16231 | 28.2 | 27.4 | 1.029 | 28.4 | 27.5 |
1.033 | 26.3 | 24.1 | 1.089 |
| 4096→32 | wgrad | f32 | 16384 | 28.0 | 27.1 | 1.036 | 28.8 | 27.7 |
1.040 | 26.6 | 24.3 | 1.095 |
| 4096→48 | dgrad | bf16 | 16231 | 24.6 | 24.6 | 0.999 | 23.0 | 22.9 |
1.001 | 17.2 | 17.2 | 0.999 |
| 4096→48 | dgrad | bf16 | 16384 | 24.8 | 24.8 | 0.997 | 23.3 | 23.3 |
1.000 | 17.2 | 17.2 | 0.999 |
| 4096→48 | dgrad | f32 | 16231 | 45.2 | 45.2 | 1.002 | 43.3 | 43.2 |
1.002 | 30.5 | 30.6 | 0.998 |
| 4096→48 | dgrad | f32 | 16384 | 45.5 | 45.6 | 0.998 | 43.6 | 43.6 |
0.999 | 30.7 | 30.7 | 1.001 |
| 4096→48 | fwd | bf16 | 16231 | 26.0 | 26.1 | 0.998 | 26.9 | 27.0 |
0.995 | 19.5 | 19.5 | 0.998 |
| 4096→48 | fwd | bf16 | 16384 | 25.8 | 25.8 | 1.003 | 26.7 | 26.8 |
0.995 | 19.7 | 19.8 | 0.998 |
| 4096→48 | wgrad | bf16 | 16231 | 28.3 | 27.7 | 1.023 | 28.6 | 27.9 |
1.025 | 20.4 | 20.4 | 0.997 |
| 4096→48 | wgrad | bf16 | 16384 | 28.2 | 27.5 | 1.026 | 28.8 | 28.1 |
1.024 | 20.7 | 20.8 | 0.996 |
| 4096→48 | wgrad | f32 | 16231 | 28.3 | 27.7 | 1.022 | 28.5 | 27.9 |
1.022 | 27.5 | 24.3 | 1.134 |
| 4096→48 | wgrad | f32 | 16384 | 28.4 | 27.6 | 1.031 | 28.9 | 28.0 |
1.034 | 27.8 | 24.4 | 1.137 |
| 4096→64 | dgrad | bf16 | 16231 | 24.6 | 24.5 | 1.002 | 23.5 | 23.6 |
0.996 | 16.8 | 16.8 | 0.998 |
| 4096→64 | dgrad | bf16 | 16384 | 24.7 | 24.6 | 1.003 | 23.7 | 23.7 |
1.001 | 16.9 | 16.9 | 0.999 |
| 4096→64 | dgrad | f32 | 16231 | 45.3 | 45.3 | 1.001 | 43.4 | 43.6 |
0.996 | 30.5 | 30.5 | 1.001 |
| 4096→64 | dgrad | f32 | 16384 | 45.6 | 45.5 | 1.002 | 43.6 | 43.6 |
1.002 | 30.6 | 30.6 | 1.001 |
| 4096→64 | fwd | bf16 | 16231 | 26.3 | 26.2 | 1.002 | 27.2 | 27.2 |
1.000 | 19.6 | 19.6 | 0.999 |
| 4096→64 | fwd | bf16 | 16384 | 26.1 | 26.1 | 1.000 | 27.0 | 27.0 |
0.999 | 19.9 | 19.8 | 1.002 |
| 4096→64 | wgrad | bf16 | 16231 | 28.7 | 27.8 | 1.032 | 28.9 | 28.0 |
1.029 | 20.3 | 20.4 | 0.996 |
| 4096→64 | wgrad | bf16 | 16384 | 28.2 | 27.4 | 1.031 | 28.8 | 27.8 |
1.035 | 20.6 | 20.7 | 0.996 |
| 4096→64 | wgrad | f32 | 16231 | 28.7 | 27.7 | 1.034 | 28.8 | 27.9 |
1.033 | 29.6 | 24.6 | 1.203 |
| 4096→64 | wgrad | f32 | 16384 | 28.4 | 27.4 | 1.038 | 28.9 | 28.0 |
1.031 | 30.7 | 24.7 | 1.244 |
| 4096→128 | dgrad | bf16 | 16231 | 25.8 | 25.8 | 1.000 | 24.3 | 24.4 |
0.999 | 18.5 | 18.5 | 1.000 |
| 4096→128 | dgrad | bf16 | 16384 | 26.0 | 26.1 | 0.996 | 24.5 | 24.5 |
1.000 | 18.6 | 18.6 | 1.001 |
| 4096→128 | dgrad | f32 | 16231 | 47.5 | 47.6 | 0.996 | 45.0 | 44.8 |
1.003 | 32.6 | 32.6 | 1.001 |
| 4096→128 | dgrad | f32 | 16384 | 47.7 | 47.6 | 1.001 | 45.2 | 44.9 |
1.005 | 32.8 | 32.9 | 0.998 |
| 4096→128 | fwd | bf16 | 16231 | 27.2 | 27.2 | 0.999 | 28.1 | 28.1 |
0.998 | 20.1 | 20.2 | 0.995 |
| 4096→128 | fwd | bf16 | 16384 | 26.9 | 26.7 | 1.007 | 27.6 | 27.5 |
1.001 | 20.1 | 20.1 | 1.002 |
| 4096→128 | wgrad | bf16 | 16231 | 29.5 | 28.4 | 1.037 | 29.6 | 28.6 |
1.033 | 21.1 | 21.1 | 1.001 |
| 4096→128 | wgrad | bf16 | 16384 | 29.1 | 28.3 | 1.031 | 29.6 | 28.6 |
1.038 | 21.0 | 21.0 | 0.999 |
| 4096→128 | wgrad | f32 | 16231 | 29.4 | 28.5 | 1.031 | 29.5 | 28.9 |
1.022 | 21.0 | 21.0 | 0.998 |
| 4096→128 | wgrad | f32 | 16384 | 29.1 | 28.2 | 1.033 | 29.5 | 28.5 |
1.033 | 21.1 | 21.1 | 0.999 |
| 4096→512 | dgrad | bf16 | 16231 | 51.2 | 49.3 | 1.038 | 41.2 | 41.2 |
0.998 | 29.9 | 30.0 | 0.998 |
| 4096→512 | dgrad | bf16 | 16384 | 50.6 | 49.5 | 1.024 | 41.2 | 41.0 |
1.004 | 29.9 | 29.9 | 0.999 |
| 4096→512 | dgrad | f32 | 16231 | 71.4 | 71.5 | 0.998 | 60.4 | 60.4 |
1.000 | 39.4 | 39.4 | 1.002 |
| 4096→512 | dgrad | f32 | 16384 | 71.7 | 71.6 | 1.003 | 60.3 | 60.4 |
0.998 | 39.5 | 39.5 | 1.000 |
| 4096→512 | fwd | bf16 | 16231 | 56.5 | 56.5 | 1.001 | 48.4 | 48.4 |
1.000 | 33.5 | 33.6 | 0.999 |
| 4096→512 | fwd | bf16 | 16384 | 56.5 | 56.5 | 1.000 | 48.3 | 48.5 |
0.996 | 33.6 | 33.6 | 1.000 |
| 4096→512 | wgrad | bf16 | 16231 | 51.7 | 51.3 | 1.008 | 43.4 | 43.4 |
1.001 | 36.4 | 36.1 | 1.007 |
| 4096→512 | wgrad | bf16 | 16384 | 52.2 | 51.7 | 1.010 | 43.7 | 43.3 |
1.010 | 36.6 | 36.4 | 1.004 |
| 4096→512 | wgrad | f32 | 16231 | 51.3 | 51.3 | 0.999 | 43.2 | 43.1 |
1.003 | 74.0 | 73.9 | 1.001 |
| 4096→512 | wgrad | f32 | 16384 | 51.7 | 51.4 | 1.006 | 43.5 | 43.4 |
1.002 | 74.4 | 74.3 | 1.002 |
| 4096→1024 | dgrad | bf16 | 16231 | 93.4 | 93.3 | 1.001 | 72.0 | 72.3 |
0.996 | 45.1 | 45.1 | 0.999 |
| 4096→1024 | dgrad | bf16 | 16384 | 93.7 | 93.6 | 1.001 | 72.6 | 72.4 |
1.003 | 45.3 | 45.3 | 0.999 |
| 4096→1024 | fwd | bf16 | 16231 | 96.2 | 95.8 | 1.004 | 75.2 | 75.2 |
1.001 | 46.6 | 46.7 | 0.999 |
| 4096→1024 | fwd | bf16 | 16384 | 96.2 | 96.4 | 0.998 | 75.0 | 75.1 |
0.998 | 46.6 | 46.6 | 1.001 |
| 4096→1024 | wgrad | bf16 | 16231 | 95.7 | 96.3 | 0.994 | 73.8 | 73.6 |
1.002 | 52.9 | 53.2 | 0.995 |
| 4096→1024 | wgrad | bf16 | 16384 | 96.9 | 96.6 | 1.003 | 74.3 | 74.5 |
0.997 | 53.5 | 53.7 | 0.997 |
| 4096→1024 | wgrad | f32 | 16231 | 98.1 | 97.8 | 1.003 | 75.8 | 75.8 |
1.000 | 75.2 | 75.2 | 1.000 |
| 4096→1024 | wgrad | f32 | 16384 | 98.7 | 99.1 | 0.996 | 76.3 | 76.7 |
0.995 | 75.8 | 75.8 | 1.001 |
| 4096→4096 | dgrad | bf16 | 16231 | 321.4 | 316.2 | 1.016 | 271.7 |
272.7 | 0.996 | 150.4 | 150.4 | 1.000 |
| 4096→4096 | dgrad | bf16 | 16384 | 317.6 | 318.0 | 0.998 | 270.2 |
270.3 | 1.000 | 150.3 | 150.4 | 1.000 |
| 4096→4096 | fwd | bf16 | 16231 | 318.1 | 318.6 | 0.998 | 270.7 | 270.9
| 0.999 | 149.8 | 149.8 | 1.000 |
| 4096→4096 | fwd | bf16 | 16384 | 317.4 | 318.2 | 0.997 | 270.9 | 271.1
| 0.999 | 149.9 | 149.8 | 1.001 |
| 4096→4096 | wgrad | bf16 | 16231 | 329.2 | 329.3 | 1.000 | 281.4 |
281.2 | 1.001 | 175.4 | 175.3 | 1.001 |
| 4096→4096 | wgrad | bf16 | 16384 | 332.0 | 332.0 | 1.000 | 283.7 |
283.6 | 1.000 | 176.5 | 176.6 | 1.000 |
| 4096→4096 | wgrad | f32 | 16231 | 333.0 | 332.6 | 1.001 | 286.1 |
286.3 | 0.999 | 233.9 | 233.9 | 1.000 |
| 4096→4096 | wgrad | f32 | 16384 | 334.6 | 334.7 | 1.000 | 288.7 |
288.5 | 1.001 | 235.6 | 235.6 | 1.000 |
| 4096→12288 | dgrad | bf16 | 16231 | 923.4 | 928.6 | 0.994 | 831.5 |
831.5 | 1.000 | 468.4 | 468.0 | 1.001 |
| 4096→12288 | dgrad | bf16 | 16384 | 927.2 | 935.4 | 0.991 | 833.6 |
838.7 | 0.994 | 470.9 | 471.2 | 0.999 |
| 4096→12288 | fwd | bf16 | 16231 | 893.9 | 893.9 | 1.000 | 809.1 |
809.1 | 1.000 | 454.8 | 454.7 | 1.000 |
| 4096→12288 | fwd | bf16 | 16384 | 913.0 | 912.1 | 1.001 | 811.2 |
812.1 | 0.999 | 456.6 | 454.7 | 1.004 |
| 4096→12288 | wgrad | bf16 | 16231 | 931.2 | 920.6 | 1.011 | 837.4 |
832.4 | 1.006 | 470.3 | 468.6 | 1.004 |
| 4096→12288 | wgrad | bf16 | 16384 | 930.4 | 911.3 | 1.021 | 837.4 |
842.6 | 0.994 | 473.7 | 472.7 | 1.002 |
| 4096→12288 | wgrad | f32 | 16231 | 929.0 | 920.1 | 1.010 | 853.9 |
853.1 | 1.001 | 467.5 | 468.2 | 0.998 |
| 4096→12288 | wgrad | f32 | 16384 | 938.3 | 925.7 | 1.014 | 856.8 |
856.4 | 1.000 | 472.1 | 472.4 | 0.999 |
| 5120→32 | dgrad | bf16 | 16231 | 33.0 | 29.0 | 1.138 | 27.6 | 27.5 |
1.003 | 20.0 | 19.9 | 1.002 |
| 5120→32 | dgrad | bf16 | 16384 | 29.2 | 29.2 | 1.001 | 27.7 | 27.6 |
1.002 | 20.0 | 20.1 | 0.996 |
| 5120→32 | dgrad | f32 | 16231 | 53.6 | 53.6 | 1.001 | 51.7 | 51.5 |
1.005 | 36.5 | 36.5 | 1.000 |
| 5120→32 | dgrad | f32 | 16384 | 54.0 | 54.1 | 0.999 | 52.0 | 52.0 |
1.000 | 36.8 | 36.8 | 1.000 |
| 5120→32 | fwd | bf16 | 16231 | 30.9 | 30.9 | 1.002 | 31.6 | 31.6 |
1.001 | 23.2 | 23.2 | 0.999 |
| 5120→32 | fwd | bf16 | 16384 | 31.6 | 31.6 | 0.999 | 32.7 | 32.7 |
1.000 | 23.3 | 23.3 | 0.999 |
| 5120→32 | wgrad | bf16 | 16231 | 32.6 | 32.4 | 1.006 | 34.3 | 34.1 |
1.007 | 22.8 | 22.9 | 0.999 |
| 5120→32 | wgrad | bf16 | 16384 | 32.9 | 32.8 | 1.005 | 34.4 | 34.3 |
1.002 | 23.2 | 23.2 | 1.003 |
| 5120→32 | wgrad | f32 | 16231 | 32.5 | 32.2 | 1.009 | 34.1 | 34.1 |
1.000 | 28.0 | 25.6 | 1.096 |
| 5120→32 | wgrad | f32 | 16384 | 32.8 | 32.7 | 1.005 | 34.5 | 34.2 |
1.011 | 28.3 | 25.9 | 1.092 |
| 5120→48 | dgrad | bf16 | 16231 | 29.2 | 29.4 | 0.994 | 27.8 | 27.7 |
1.002 | 20.5 | 20.5 | 1.002 |
| 5120→48 | dgrad | bf16 | 16384 | 29.7 | 29.7 | 0.999 | 27.9 | 27.9 |
0.998 | 20.6 | 20.4 | 1.011 |
| 5120→48 | dgrad | f32 | 16231 | 54.3 | 54.2 | 1.002 | 52.1 | 51.9 |
1.005 | 37.0 | 37.0 | 1.001 |
| 5120→48 | dgrad | f32 | 16384 | 54.6 | 54.7 | 0.998 | 52.4 | 52.3 |
1.001 | 37.2 | 37.3 | 0.998 |
| 5120→48 | fwd | bf16 | 16231 | 30.9 | 30.9 | 0.998 | 31.7 | 31.7 |
0.999 | 23.1 | 23.2 | 0.998 |
| 5120→48 | fwd | bf16 | 16384 | 31.7 | 31.5 | 1.005 | 32.7 | 32.6 |
1.003 | 23.3 | 23.3 | 1.001 |
| 5120→48 | wgrad | bf16 | 16231 | 33.3 | 32.5 | 1.023 | 34.7 | 34.5 |
1.006 | 23.4 | 23.3 | 1.004 |
| 5120→48 | wgrad | bf16 | 16384 | 33.8 | 32.9 | 1.027 | 34.9 | 34.7 |
1.007 | 23.6 | 23.5 | 1.005 |
| 5120→48 | wgrad | f32 | 16231 | 33.2 | 32.5 | 1.024 | 34.4 | 34.2 |
1.005 | 29.2 | 26.0 | 1.123 |
| 5120→48 | wgrad | f32 | 16384 | 33.7 | 33.0 | 1.021 | 34.8 | 34.8 |
1.001 | 29.5 | 26.1 | 1.127 |
| 5120→64 | dgrad | bf16 | 16231 | 29.4 | 29.3 | 1.001 | 27.9 | 27.9 |
1.002 | 19.9 | 20.0 | 0.998 |
| 5120→64 | dgrad | bf16 | 16384 | 29.6 | 29.6 | 0.997 | 28.1 | 28.0 |
1.004 | 20.2 | 20.2 | 0.999 |
| 5120→64 | dgrad | f32 | 16231 | 54.7 | 54.7 | 0.999 | 52.4 | 52.3 |
1.001 | 36.9 | 36.9 | 0.999 |
| 5120→64 | dgrad | f32 | 16384 | 54.8 | 55.1 | 0.995 | 52.7 | 52.7 |
1.001 | 37.2 | 37.2 | 1.000 |
| 5120→64 | fwd | bf16 | 16231 | 31.5 | 31.4 | 1.004 | 32.4 | 32.3 |
1.003 | 23.2 | 23.2 | 1.000 |
| 5120→64 | fwd | bf16 | 16384 | 32.1 | 32.0 | 1.003 | 33.1 | 33.1 |
1.000 | 23.4 | 23.5 | 0.997 |
| 5120→64 | wgrad | bf16 | 16231 | 33.4 | 33.2 | 1.007 | 34.8 | 34.5 |
1.009 | 22.8 | 22.8 | 1.002 |
| 5120→64 | wgrad | bf16 | 16384 | 33.6 | 33.4 | 1.006 | 35.0 | 34.9 |
1.003 | 23.3 | 23.3 | 1.002 |
| 5120→64 | wgrad | f32 | 16231 | 33.2 | 33.1 | 1.004 | 34.7 | 34.4 |
1.009 | 31.2 | 26.3 | 1.190 |
| 5120→64 | wgrad | f32 | 16384 | 33.6 | 33.6 | 1.000 | 34.8 | 34.7 |
1.003 | 32.6 | 26.4 | 1.232 |
| 5120→128 | dgrad | bf16 | 16231 | 31.2 | 31.4 | 0.995 | 29.1 | 29.2 |
0.998 | 21.7 | 21.7 | 1.001 |
| 5120→128 | dgrad | bf16 | 16384 | 31.3 | 31.2 | 1.004 | 29.2 | 29.2 |
1.002 | 21.7 | 21.7 | 1.004 |
| 5120→128 | dgrad | f32 | 16231 | 57.1 | 57.1 | 0.999 | 54.2 | 54.2 |
1.001 | 39.5 | 39.5 | 1.000 |
| 5120→128 | dgrad | f32 | 16384 | 57.4 | 57.4 | 1.000 | 54.4 | 54.3 |
1.002 | 39.8 | 39.8 | 1.000 |
| 5120→128 | fwd | bf16 | 16231 | 32.6 | 32.7 | 0.996 | 33.6 | 33.5 |
1.001 | 23.7 | 23.6 | 1.001 |
| 5120→128 | fwd | bf16 | 16384 | 32.4 | 32.3 | 1.002 | 33.2 | 33.2 |
1.000 | 23.8 | 23.9 | 0.998 |
| 5120→128 | wgrad | bf16 | 16231 | 33.8 | 33.7 | 1.003 | 36.0 | 35.6 |
1.012 | 23.6 | 23.6 | 1.001 |
| 5120→128 | wgrad | bf16 | 16384 | 34.4 | 34.2 | 1.005 | 36.4 | 36.1 |
1.009 | 23.7 | 23.8 | 0.998 |
| 5120→128 | wgrad | f32 | 16231 | 33.8 | 33.6 | 1.006 | 35.9 | 35.6 |
1.008 | 23.6 | 23.6 | 0.998 |
| 5120→128 | wgrad | f32 | 16384 | 34.3 | 34.2 | 1.004 | 36.3 | 35.9 |
1.010 | 23.7 | 23.8 | 0.999 |
| 5120→512 | dgrad | bf16 | 16231 | 63.7 | 62.9 | 1.013 | 50.1 | 49.7 |
1.008 | 35.1 | 35.1 | 1.001 |
| 5120→512 | dgrad | bf16 | 16384 | 63.5 | 63.4 | 1.002 | 50.0 | 50.1 |
0.999 | 34.8 | 34.9 | 0.998 |
| 5120→512 | dgrad | f32 | 16231 | 88.0 | 87.6 | 1.003 | 73.9 | 73.9 |
1.000 | 47.3 | 47.3 | 1.001 |
| 5120→512 | dgrad | f32 | 16384 | 87.6 | 87.5 | 1.001 | 74.4 | 74.2 |
1.003 | 47.4 | 47.5 | 0.998 |
| 5120→512 | fwd | bf16 | 16231 | 70.2 | 69.9 | 1.004 | 58.4 | 58.4 |
1.001 | 39.7 | 39.6 | 1.001 |
| 5120→512 | fwd | bf16 | 16384 | 70.4 | 70.2 | 1.003 | 58.4 | 58.5 |
0.998 | 39.8 | 39.8 | 1.002 |
| 5120→512 | wgrad | bf16 | 16231 | 69.0 | 68.6 | 1.005 | 53.9 | 53.2 |
1.013 | 38.3 | 38.1 | 1.005 |
| 5120→512 | wgrad | bf16 | 16384 | 69.6 | 69.7 | 0.997 | 53.9 | 54.0 |
0.997 | 38.6 | 38.3 | 1.008 |
| 5120→512 | wgrad | f32 | 16231 | 70.0 | 70.0 | 1.000 | 55.3 | 55.1 |
1.004 | 74.2 | 74.1 | 1.001 |
| 5120→512 | wgrad | f32 | 16384 | 70.4 | 70.2 | 1.002 | 55.4 | 55.0 |
1.008 | 74.5 | 74.6 | 1.000 |
| 5120→1024 | dgrad | bf16 | 16231 | 113.1 | 113.5 | 0.996 | 90.6 | 90.1
| 1.005 | 53.3 | 53.3 | 1.000 |
| 5120→1024 | dgrad | bf16 | 16384 | 113.3 | 112.8 | 1.004 | 89.6 | 89.9
| 0.997 | 53.2 | 53.3 | 0.999 |
| 5120→1024 | fwd | bf16 | 16231 | 116.1 | 117.1 | 0.992 | 93.2 | 93.4 |
0.997 | 55.8 | 55.7 | 1.002 |
| 5120→1024 | fwd | bf16 | 16384 | 117.6 | 117.2 | 1.004 | 93.7 | 93.6 |
1.002 | 55.8 | 55.9 | 0.999 |
| 5120→1024 | wgrad | bf16 | 16231 | 121.8 | 122.2 | 0.997 | 98.9 | 99.2
| 0.997 | 63.7 | 63.7 | 1.000 |
| 5120→1024 | wgrad | bf16 | 16384 | 122.3 | 121.7 | 1.005 | 99.6 | 99.8
| 0.998 | 64.2 | 64.2 | 1.000 |
| 5120→1024 | wgrad | f32 | 16231 | 122.6 | 122.9 | 0.998 | 100.4 |
100.3 | 1.001 | 78.2 | 78.2 | 1.001 |
| 5120→1024 | wgrad | f32 | 16384 | 123.5 | 122.9 | 1.005 | 101.4 |
101.2 | 1.002 | 78.5 | 78.2 | 1.003 |
| 5120→5120 | dgrad | bf16 | 16231 | 487.0 | 486.2 | 1.002 | 426.0 |
424.6 | 1.003 | 227.3 | 227.0 | 1.001 |
| 5120→5120 | dgrad | bf16 | 16384 | 487.3 | 488.0 | 0.999 | 424.6 |
425.3 | 0.998 | 227.5 | 227.6 | 0.999 |
| 5120→5120 | fwd | bf16 | 16231 | 486.4 | 487.1 | 0.998 | 424.4 | 424.5
| 1.000 | 227.1 | 227.1 | 1.000 |
| 5120→5120 | fwd | bf16 | 16384 | 488.4 | 487.6 | 1.002 | 425.1 | 425.4
| 0.999 | 227.6 | 227.6 | 1.000 |
| 5120→5120 | wgrad | bf16 | 16231 | 488.8 | 489.3 | 0.999 | 431.3 |
430.3 | 1.002 | 233.2 | 233.3 | 1.000 |
| 5120→5120 | wgrad | bf16 | 16384 | 493.2 | 493.5 | 0.999 | 435.2 |
435.5 | 0.999 | 235.2 | 235.2 | 1.000 |
| 5120→5120 | wgrad | f32 | 16231 | 492.2 | 490.7 | 1.003 | 433.0 |
433.0 | 1.000 | 238.3 | 238.3 | 1.000 |
| 5120→5120 | wgrad | f32 | 16384 | 496.1 | 495.1 | 1.002 | 436.8 |
437.5 | 0.998 | 240.1 | 240.1 | 1.000 |
| 5120→17408 | dgrad | bf16 | 16231 | 1584.9 | 1596.3 | 0.993 | 1463.8 |
1458.5 | 1.004 | 859.7 | 860.7 | 0.999 |
| 5120→17408 | dgrad | bf16 | 16384 | 1591.6 | 1599.5 | 0.995 | 1485.7 |
1476.8 | 1.006 | 865.1 | 866.0 | 0.999 |
| 5120→17408 | fwd | bf16 | 16231 | 1584.0 | 1579.8 | 1.003 | 1434.9 |
1436.7 | 0.999 | 827.9 | 829.2 | 0.998 |
| 5120→17408 | fwd | bf16 | 16384 | 1599.3 | 1589.6 | 1.006 | 1442.6 |
1442.5 | 1.000 | 828.6 | 831.7 | 0.996 |
| 5120→17408 | wgrad | bf16 | 16231 | 1575.4 | 1563.3 | 1.008 | 1446.1 |
1455.0 | 0.994 | 847.1 | 843.6 | 1.004 |
| 5120→17408 | wgrad | bf16 | 16384 | 1598.7 | 1600.2 | 0.999 | 1466.5 |
1459.3 | 1.005 | 855.4 | 858.4 | 0.996 |
| 5120→17408 | wgrad | f32 | 16231 | 1578.8 | 1579.2 | 1.000 | 1463.8 |
1463.9 | 1.000 | 836.2 | 836.9 | 0.999 |
| 5120→17408 | wgrad | f32 | 16384 | 1587.7 | 1603.5 | 0.990 | 1484.5 |
1465.0 | 1.013 | 845.0 | 843.8 | 1.001 |
| indexer_hw (6144→32) | dgrad | bf16 | 16172 | 41.2 | 36.9 | 1.116 |
32.7 | 32.8 | 0.998 | 23.6 | 23.2 | 1.014 |
| indexer_hw (6144→32) | dgrad | bf16 | 16231 | 34.5 | 34.5 | 0.999 |
32.6 | 32.6 | 1.000 | 22.6 | 22.6 | 1.001 |
| indexer_hw (6144→32) | dgrad | f32 | 16172 | 61.3 | 61.3 | 0.999 |
58.2 | 58.4 | 0.997 | 38.6 | 38.7 | 0.998 |
| indexer_hw (6144→32) | dgrad | f32 | 16231 | 61.5 | 61.6 | 0.998 |
58.5 | 58.5 | 1.001 | 38.8 | 38.8 | 1.001 |
| indexer_hw (6144→32) | fwd | bf16 | 16172 | 36.4 | 36.4 | 1.002 | 37.5
| 37.5 | 1.001 | 26.5 | 26.5 | 1.001 |
| indexer_hw (6144→32) | fwd | bf16 | 16231 | 36.3 | 36.4 | 0.999 | 37.4
| 37.5 | 0.996 | 26.5 | 26.5 | 1.001 |
| indexer_hw (6144→32) | wgrad | bf16 | 16172 | 37.6 | 37.6 | 1.000 |
39.6 | 39.7 | 0.997 | 26.7 | 26.7 | 1.001 |
| indexer_hw (6144→32) | wgrad | bf16 | 16231 | 37.5 | 37.6 | 0.999 |
39.4 | 39.6 | 0.996 | 26.7 | 26.8 | 0.999 |
| indexer_hw (6144→32) | wgrad | f32 | 16172 | 37.5 | 37.6 | 0.996 |
39.3 | 39.4 | 0.998 | 26.8 | 26.8 | 0.999 |
| indexer_hw (6144→32) | wgrad | f32 | 16231 | 37.4 | 37.6 | 0.997 |
39.6 | 39.4 | 1.005 | 26.6 | 26.7 | 0.996 |
| indexer_k (6144→128) | dgrad | bf16 | 16172 | 36.4 | 36.2 | 1.004 |
34.2 | 34.2 | 0.999 | 24.5 | 24.6 | 0.998 |
| indexer_k (6144→128) | dgrad | bf16 | 16231 | 36.4 | 36.4 | 0.999 |
34.2 | 34.2 | 1.000 | 24.6 | 24.7 | 0.998 |
| indexer_k (6144→128) | dgrad | f32 | 16172 | 65.7 | 65.6 | 1.000 |
62.2 | 62.1 | 1.002 | 41.6 | 41.7 | 0.998 |
| indexer_k (6144→128) | dgrad | f32 | 16231 | 65.5 | 65.6 | 0.999 |
62.1 | 62.0 | 1.001 | 41.8 | 41.9 | 0.998 |
| indexer_k (6144→128) | fwd | bf16 | 16172 | 38.0 | 37.9 | 1.005 | 38.9
| 39.0 | 0.998 | 26.8 | 26.8 | 0.998 |
| indexer_k (6144→128) | fwd | bf16 | 16231 | 37.9 | 37.8 | 1.003 | 38.9
| 38.8 | 1.003 | 27.3 | 27.3 | 1.000 |
| indexer_k (6144→128) | wgrad | bf16 | 16172 | 38.6 | 38.5 | 1.002 |
40.9 | 40.6 | 1.006 | 27.6 | 27.7 | 0.996 |
| indexer_k (6144→128) | wgrad | bf16 | 16231 | 38.7 | 38.7 | 1.000 |
41.1 | 41.4 | 0.994 | 28.0 | 28.0 | 0.998 |
| indexer_k (6144→128) | wgrad | f32 | 16172 | 38.5 | 38.4 | 1.003 |
40.7 | 40.6 | 1.002 | 27.8 | 27.8 | 0.998 |
| indexer_k (6144→128) | wgrad | f32 | 16231 | 38.7 | 38.5 | 1.005 |
41.1 | 41.1 | 1.001 | 28.4 | 28.2 | 1.005 |
| kv_a (6144→576) | dgrad | bf16 | 16172 | 83.3 | 82.5 | 1.009 | 63.9 |
63.9 | 0.999 | 42.6 | 42.6 | 1.000 |
| kv_a (6144→576) | dgrad | bf16 | 16231 | 83.2 | 82.5 | 1.009 | 64.2 |
64.2 | 1.001 | 42.5 | 42.4 | 1.001 |
| kv_a (6144→576) | dgrad | f32 | 16172 | 110.0 | 109.8 | 1.002 | 91.8 |
92.1 | 0.997 | 56.8 | 56.9 | 0.998 |
| kv_a (6144→576) | dgrad | f32 | 16231 | 110.5 | 109.7 | 1.007 | 92.9 |
92.7 | 1.003 | 56.8 | 56.7 | 1.003 |
| kv_a (6144→576) | fwd | bf16 | 16172 | 94.5 | 94.1 | 1.005 | 72.8 |
72.3 | 1.007 | 41.8 | 41.7 | 1.002 |
| kv_a (6144→576) | fwd | bf16 | 16231 | 94.7 | 94.3 | 1.004 | 72.6 |
72.6 | 1.000 | 41.8 | 41.8 | 1.001 |
| kv_a (6144→576) | wgrad | bf16 | 16172 | 83.1 | 82.9 | 1.003 | 65.2 |
65.0 | 1.004 | 44.3 | 44.5 | 0.996 |
| kv_a (6144→576) | wgrad | bf16 | 16231 | 84.1 | 83.5 | 1.007 | 65.6 |
65.1 | 1.008 | 43.6 | 43.8 | 0.996 |
| kv_a (6144→576) | wgrad | f32 | 16172 | 84.5 | 85.2 | 0.992 | 66.3 |
66.3 | 1.000 | 45.4 | 45.6 | 0.996 |
| kv_a (6144→576) | wgrad | f32 | 16231 | 85.1 | 85.2 | 0.999 | 66.2 |
66.4 | 0.997 | 46.2 | 45.7 | 1.011 |
| q_a (6144→2048) | dgrad | bf16 | 16172 | 248.8 | 251.2 | 0.990 | 211.0
| 211.1 | 0.999 | 111.1 | 111.2 | 0.999 |
| q_a (6144→2048) | dgrad | bf16 | 16231 | 249.2 | 248.5 | 1.003 | 211.0
| 211.2 | 0.999 | 111.2 | 111.1 | 1.000 |
| q_a (6144→2048) | dgrad | f32 | 16172 | 259.9 | 260.4 | 0.998 | 223.2
| 223.0 | 1.001 | 115.5 | 115.5 | 1.000 |
| q_a (6144→2048) | dgrad | f32 | 16231 | 259.7 | 259.6 | 1.001 | 223.4
| 223.3 | 1.000 | 115.6 | 115.5 | 1.001 |
| q_a (6144→2048) | fwd | bf16 | 16172 | 251.4 | 251.0 | 1.002 | 210.1 |
210.4 | 0.999 | 114.7 | 114.9 | 0.998 |
| q_a (6144→2048) | fwd | bf16 | 16231 | 251.3 | 252.0 | 0.998 | 210.3 |
210.4 | 0.999 | 114.8 | 114.7 | 1.001 |
| q_a (6144→2048) | wgrad | bf16 | 16172 | 259.6 | 260.3 | 0.997 | 218.1
| 218.6 | 0.998 | 115.9 | 115.5 | 1.004 |
| q_a (6144→2048) | wgrad | bf16 | 16231 | 260.5 | 261.3 | 0.997 | 218.8
| 218.8 | 1.000 | 116.0 | 115.6 | 1.004 |
| q_a (6144→2048) | wgrad | f32 | 16172 | 261.2 | 261.4 | 1.000 | 219.2
| 219.5 | 0.999 | 116.8 | 116.9 | 0.999 |
| q_a (6144→2048) | wgrad | f32 | 16231 | 261.4 | 262.5 | 0.996 | 220.0
| 220.0 | 1.000 | 117.2 | 117.2 | 1.000 |
| shared_gate_up (6144→2048) | dgrad | bf16 | 16172 | 248.6 | 248.8 |
0.999 | 210.8 | 210.6 | 1.001 | 111.2 | 111.1 | 1.000 |
| shared_gate_up (6144→2048) | dgrad | bf16 | 16231 | 248.5 | 248.8 |
0.999 | 211.3 | 211.3 | 1.000 | 111.1 | 111.1 | 1.000 |
| shared_gate_up (6144→2048) | dgrad | f32 | 16172 | 259.6 | 260.3 |
0.998 | 223.6 | 223.2 | 1.002 | 115.7 | 115.7 | 1.000 |
| shared_gate_up (6144→2048) | dgrad | f32 | 16231 | 260.6 | 260.2 |
1.002 | 223.6 | 223.4 | 1.001 | 116.6 | 116.9 | 0.997 |
| shared_gate_up (6144→2048) | fwd | bf16 | 16172 | 251.8 | 251.6 |
1.001 | 210.5 | 210.0 | 1.002 | 114.8 | 114.9 | 1.000 |
| shared_gate_up (6144→2048) | fwd | bf16 | 16231 | 251.9 | 251.2 |
1.003 | 210.2 | 210.9 | 0.997 | 115.1 | 115.0 | 1.001 |
| shared_gate_up (6144→2048) | wgrad | bf16 | 16172 | 260.4 | 260.4 |
1.000 | 218.4 | 218.8 | 0.998 | 115.8 | 115.3 | 1.004 |
| shared_gate_up (6144→2048) | wgrad | bf16 | 16231 | 261.6 | 261.0 |
1.002 | 219.6 | 219.4 | 1.001 | 116.1 | 115.6 | 1.004 |
| shared_gate_up (6144→2048) | wgrad | f32 | 16172 | 261.4 | 261.3 |
1.001 | 219.6 | 219.4 | 1.001 | 116.8 | 116.8 | 1.000 |
| shared_gate_up (6144→2048) | wgrad | f32 | 16231 | 261.8 | 262.0 |
0.999 | 220.4 | 220.5 | 1.000 | 117.1 | 117.2 | 0.999 |
| dense_gate_up (6144→12288) | wgrad | bf16 | 16172 | 1352.8 | 1345.0 |
1.006 | 1220.9 | 1222.3 | 0.999 | 677.6 | 677.0 | 1.001 |
| dense_gate_up (6144→12288) | wgrad | bf16 | 16231 | 1358.7 | 1319.5 |
1.030 | 1226.7 | 1226.5 | 1.000 | 681.6 | 677.5 | 1.006 |
| dense_gate_up (6144→12288) | wgrad | f32 | 16172 | 1350.1 | 1353.3 |
0.998 | 1227.5 | 1230.7 | 0.997 | 683.3 | 682.8 | 1.001 |
| dense_gate_up (6144→12288) | wgrad | f32 | 16231 | 1359.2 | 1364.5 |
0.996 | 1233.0 | 1230.5 | 1.002 | 686.8 | 687.1 | 1.000 |
| 8192→128 | dgrad | bf16 | 16231 | 53.8 | 52.0 | 1.034 | 43.9 | 43.9 |
1.001 | 31.1 | 31.1 | 0.998 |
| 8192→128 | dgrad | bf16 | 16384 | 47.9 | 47.6 | 1.007 | 43.7 | 43.9 |
0.996 | 31.2 | 31.3 | 0.997 |
| 8192→128 | dgrad | f32 | 16231 | 91.4 | 91.4 | 1.000 | 85.5 | 85.4 |
1.001 | 58.5 | 58.6 | 0.999 |
| 8192→128 | dgrad | f32 | 16384 | 90.5 | 90.5 | 1.000 | 84.9 | 84.7 |
1.002 | 59.2 | 59.1 | 1.002 |
| 8192→128 | fwd | bf16 | 16231 | 48.0 | 47.9 | 1.001 | 48.8 | 48.7 |
1.002 | 35.1 | 35.1 | 1.000 |
| 8192→128 | fwd | bf16 | 16384 | 48.3 | 48.5 | 0.995 | 49.3 | 49.3 |
1.001 | 35.5 | 35.3 | 1.004 |
| 8192→128 | wgrad | bf16 | 16231 | 44.9 | 44.6 | 1.007 | 45.8 | 45.6 |
1.006 | 34.4 | 34.4 | 1.000 |
| 8192→128 | wgrad | bf16 | 16384 | 45.1 | 44.7 | 1.008 | 45.9 | 45.9 |
1.001 | 34.9 | 34.8 | 1.003 |
| 8192→128 | wgrad | f32 | 16231 | 44.9 | 44.5 | 1.009 | 45.6 | 45.6 |
0.999 | 34.4 | 34.4 | 1.000 |
| 8192→128 | wgrad | f32 | 16384 | 45.2 | 44.7 | 1.011 | 45.8 | 46.0 |
0.997 | 34.8 | 34.8 | 1.000 |
| 12288→4096 | dgrad | bf16 | 16231 | 895.9 | 895.7 | 1.000 | 816.8 |
816.5 | 1.000 | 454.3 | 454.4 | 1.000 |
| 12288→4096 | dgrad | bf16 | 16384 | 915.4 | 898.1 | 1.019 | 817.3 |
816.5 | 1.001 | 458.1 | 457.4 | 1.001 |
| 12288→4096 | fwd | bf16 | 16231 | 920.6 | 923.4 | 0.997 | 824.1 |
830.1 | 0.993 | 468.8 | 468.9 | 1.000 |
| 12288→4096 | fwd | bf16 | 16384 | 920.6 | 924.7 | 0.996 | 826.7 |
827.4 | 0.999 | 467.5 | 470.2 | 0.994 |
| 12288→4096 | wgrad | bf16 | 16231 | 906.9 | 915.0 | 0.991 | 820.1 |
823.2 | 0.996 | 466.0 | 465.6 | 1.001 |
| 12288→4096 | wgrad | bf16 | 16384 | 916.8 | 901.1 | 1.017 | 824.7 |
826.3 | 0.998 | 470.4 | 470.2 | 1.001 |
| 12288→4096 | wgrad | f32 | 16231 | 926.0 | 917.5 | 1.009 | 839.2 |
844.5 | 0.994 | 465.9 | 465.8 | 1.000 |
| 12288→4096 | wgrad | f32 | 16384 | 922.0 | 919.3 | 1.003 | 847.9 |
846.9 | 1.001 | 469.5 | 469.6 | 1.000 |
| dense_down (12288→6144) | wgrad | bf16 | 16172 | 1341.0 | 1335.5 |
1.004 | 1212.3 | 1210.0 | 1.002 | 671.2 | 671.2 | 1.000 |
| dense_down (12288→6144) | wgrad | bf16 | 16231 | 1337.2 | 1344.7 |
0.994 | 1221.4 | 1217.6 | 1.003 | 679.7 | 680.3 | 0.999 |
| dense_down (12288→6144) | wgrad | f32 | 16172 | 1340.4 | 1339.1 |
1.001 | 1221.3 | 1224.2 | 0.998 | 680.8 | 681.8 | 0.998 |
| dense_down (12288→6144) | wgrad | f32 | 16231 | 1348.0 | 1333.7 |
1.011 | 1224.0 | 1226.2 | 0.998 | 685.9 | 689.6 | 0.995 |
| o_proj (16384→6144) | dgrad | bf16 | 16172 | 1824.6 | 1789.5 | 1.020 |
1643.6 | 1629.8 | 1.008 | 933.4 | 936.8 | 0.996 |
| o_proj (16384→6144) | dgrad | bf16 | 16231 | 1820.4 | 1816.8 | 1.002 |
1639.5 | 1655.8 | 0.990 | 958.4 | 956.3 | 1.002 |
| o_proj (16384→6144) | dgrad | f32 | 16172 | 1826.1 | 1822.4 | 1.002 |
1674.1 | 1679.8 | 0.997 | 952.6 | 953.1 | 0.999 |
| o_proj (16384→6144) | dgrad | f32 | 16231 | 1836.1 | 1823.4 | 1.007 |
1680.8 | 1669.9 | 1.007 | 956.6 | 955.6 | 1.001 |
| o_proj (16384→6144) | fwd | bf16 | 16172 | 1806.9 | 1797.4 | 1.005 |
1664.2 | 1663.9 | 1.000 | 916.4 | 912.4 | 1.004 |
| o_proj (16384→6144) | fwd | bf16 | 16231 | 1812.2 | 1820.6 | 0.995 |
1661.8 | 1670.9 | 0.995 | 945.9 | 931.9 | 1.015 |
| o_proj (16384→6144) | wgrad | bf16 | 16172 | 1773.5 | 1770.1 | 1.002 |
1634.5 | 1636.2 | 0.999 | 935.0 | 919.6 | 1.017 |
| o_proj (16384→6144) | wgrad | bf16 | 16231 | 1802.9 | 1769.5 | 1.019 |
1647.5 | 1640.5 | 1.004 | 940.8 | 916.7 | 1.026 |
| o_proj (16384→6144) | wgrad | f32 | 16172 | 1816.7 | 1811.3 | 1.003 |
1632.8 | 1644.6 | 0.993 | 957.2 | 948.5 | 1.009 |
| o_proj (16384→6144) | wgrad | f32 | 16231 | 1872.3 | 1807.3 | 1.036 |
1652.5 | 1643.9 | 1.005 | 949.3 | 951.6 | 0.998 |
| 17408→5120 | dgrad | bf16 | 16231 | 1589.1 | 1586.9 | 1.001 | 1445.2 |
1446.6 | 0.999 | 840.2 | 838.0 | 1.003 |
| 17408→5120 | dgrad | bf16 | 16384 | 1583.3 | 1567.0 | 1.010 | 1454.2 |
1449.8 | 1.003 | 833.2 | 840.4 | 0.991 |
| 17408→5120 | fwd | bf16 | 16231 | 1603.9 | 1593.2 | 1.007 | 1452.3 |
1455.2 | 0.998 | 873.8 | 869.8 | 1.005 |
| 17408→5120 | fwd | bf16 | 16384 | 1589.1 | 1574.6 | 1.009 | 1460.3 |
1453.7 | 1.005 | 879.5 | 874.2 | 1.006 |
| 17408→5120 | wgrad | bf16 | 16231 | 1602.0 | 1580.5 | 1.014 | 1445.4 |
1434.9 | 1.007 | 850.2 | 842.7 | 1.009 |
| 17408→5120 | wgrad | bf16 | 16384 | 1577.5 | 1593.1 | 0.990 | 1453.2 |
1452.4 | 1.001 | 848.0 | 852.5 | 0.995 |
| 17408→5120 | wgrad | f32 | 16231 | 1575.5 | 1586.3 | 0.993 | 1446.0 |
1453.3 | 0.995 | 841.2 | 839.3 | 1.002 |
| 17408→5120 | wgrad | f32 | 16384 | 1614.5 | 1590.3 | 1.015 | 1458.6 |
1465.5 | 0.995 | 847.0 | 846.4 | 1.001 |
| qabs (None→None) | dgrad | bf16 | 16172 | 239.2 | 239.2 | 1.000 |
232.4 | 232.5 | 0.999 | 152.8 | 152.8 | 1.000 |
| qabs (None→None) | dgrad | bf16 | 16231 | 237.1 | 236.7 | 1.002 |
230.8 | 230.7 | 1.000 | 153.0 | 153.0 | 1.000 |
| qabs (None→None) | fwd | bf16 | 16172 | 268.2 | 268.1 | 1.000 | 241.4
| 241.5 | 1.000 | 159.3 | 159.5 | 0.999 |
| qabs (None→None) | fwd | bf16 | 16231 | 277.0 | 277.2 | 0.999 | 245.9
| 245.9 | 1.000 | 160.4 | 160.6 | 0.999 |
| qabs (None→None) | wgrad | bf16 | 16172 | 213.9 | 214.2 | 0.999 |
218.9 | 218.6 | 1.001 | 143.0 | 142.8 | 1.001 |
| qabs (None→None) | wgrad | bf16 | 16231 | 214.8 | 214.7 | 1.000 |
220.0 | 220.0 | 1.000 | 143.4 | 143.2 | 1.001 |
| vproj (None→None) | dgrad | bf16 | 16172 | 292.1 | 292.0 | 1.000 |
265.6 | 265.5 | 1.000 | 172.1 | 172.0 | 1.001 |
| vproj (None→None) | dgrad | bf16 | 16231 | 293.4 | 293.8 | 0.998 |
264.4 | 264.6 | 0.999 | 173.3 | 173.2 | 1.001 |
| vproj (None→None) | fwd | bf16 | 16172 | 261.6 | 261.4 | 1.001 | 253.0
| 252.8 | 1.001 | 166.1 | 166.1 | 1.000 |
| vproj (None→None) | fwd | bf16 | 16231 | 264.3 | 264.1 | 1.001 | 256.8
| 256.9 | 1.000 | 165.9 | 165.9 | 1.000 |
| vproj (None→None) | wgrad | bf16 | 16172 | 233.0 | 232.8 | 1.001 |
236.4 | 236.6 | 0.999 | 156.2 | 155.9 | 1.002 |
| vproj (None→None) | wgrad | bf16 | 16231 | 234.1 | 234.2 | 1.000 |
237.0 | 237.3 | 0.999 | 156.2 | 156.7 | 0.997 |
| router 4096→256 | dgrad | f32 | 16231 | 188.4 | 187.9 | 1.002 | 173.5
| 173.1 | 1.002 | 105.6 | 105.8 | 0.998 |
| router 4096→256 | fwd | f32 | 16231 | 192.5 | 192.5 | 1.000 | 166.5 |
166.5 | 1.000 | 105.9 | 106.0 | 1.000 |
| router 4096→256 | wgrad | f32 | 16231 | 187.7 | 187.9 | 0.999 | 163.5
| 163.6 | 0.999 | 98.5 | 98.4 | 1.001 |
| router 5120→256 | dgrad | f32 | 16231 | 235.3 | 235.6 | 0.999 | 225.7
| 225.3 | 1.002 | 134.6 | 134.6 | 1.000 |
| router 5120→256 | fwd | f32 | 16231 | 226.2 | 226.1 | 1.000 | 195.9 |
195.9 | 1.000 | 123.9 | 124.1 | 0.998 |
| router 5120→256 | wgrad | f32 | 16231 | 235.8 | 235.6 | 1.001 | 210.0
| 209.4 | 1.003 | 136.0 | 136.0 | 0.999 |
| router 6144→256 | dgrad | f32 | 16172 | 270.6 | 270.2 | 1.001 | 260.7
| 260.4 | 1.001 | 154.5 | 154.5 | 1.000 |
| router 6144→256 | dgrad | f32 | 16231 | 272.1 | 272.6 | 0.998 | 263.2
| 262.8 | 1.001 | 155.9 | 155.7 | 1.001 |
| router 6144→256 | fwd | f32 | 16172 | 260.4 | 260.9 | 0.998 | 227.6 |
228.1 | 0.998 | 142.8 | 143.0 | 0.999 |
| router 6144→256 | fwd | f32 | 16231 | 258.5 | 259.4 | 0.996 | 226.2 |
226.4 | 0.999 | 142.0 | 142.1 | 1.000 |
| router 6144→256 | wgrad | f32 | 16172 | 249.6 | 248.7 | 1.004 | 215.8
| 216.1 | 0.999 | 137.8 | 138.0 | 0.999 |
| router 6144→256 | wgrad | f32 | 16231 | 248.3 | 248.9 | 0.998 | 216.3
| 216.5 | 0.999 | 137.8 | 138.2 | 0.997 |


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

- **Bug Fixes**
- Improved partial-result handling across dense projection operations
and adjusted workspace sizing for supported split-K plans.
- Added validation for unsupported split-K configurations and misaligned
outputs in applicable single-split launches.
- **Performance**
- Updated kernel configurations for selected input-gradient cases and
expanded eight-warp form coverage on newer GPU architectures.
- **Tests**
- Added coverage for output alignment, split-K behavior, transposed
stores, and architecture-specific kernel selections.
- **Documentation**
- Clarified the 16-byte alignment requirement for certain output buffers
and documented additional split-K constraints.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Avery Huang <averyh@nvidia.com>

### [e8ab20d](https://github.com/flashinfer-ai/flashinfer/commit/e8ab20d42ea4e7c470177b0867fe8313bd3db067)

- **作者**: eigen
- **时间**: 2026-10-31T19:44:32Z
- **提交信息**: feat(cake_causal_conv1d): opt-in non-deterministic causal conv1d auto grad backend (#8134)

### [933292e](https://github.com/flashinfer-ai/flashinfer/commit/933292e2031240137ecf1435e61599d2cc74d8bb)

- **作者**: eigen
- **时间**: 2026-10-31T19:43:45Z
- **提交信息**: perf(cake_deepgemm_mega_mhc): faster sm_107a FP8 group-128 raw, UE8M0 det and BF16 det (#8128)

### [cf54585](https://github.com/flashinfer-ai/flashinfer/commit/cf54585e8484060d16741d0fcdc22a18469e3c79)

- **作者**: eigen
- **时间**: 2026-10-31T19:43:21Z
- **提交信息**: fix(cake_tinygemm2_tcgen05): require CUDA 13.4 for the sm_107a programs (#8123)

### [8930931](https://github.com/flashinfer-ai/flashinfer/commit/8930931133addb6047fde08b7a8953df38ec423d)

- **作者**: eigen
- **时间**: 2026-10-31T19:42:33Z
- **提交信息**: perf(cake_mhc): run the non-deterministic backward's fn split beside the token-owner pass (#8116)

### [a049b1a](https://github.com/flashinfer-ai/flashinfer/commit/a049b1a53958160cba77650bdedadcae838160d1)

- **作者**: eigen
- **时间**: 2026-10-31T19:42:15Z
- **提交信息**: perf(cake_moe_grouped_gemm): skip forward recompute under checkpoint early stop (#8114)

### [56472bf](https://github.com/flashinfer-ai/flashinfer/commit/56472bf4fc534dc43aad54c01b85c57aa3dc5b78)

- **作者**: Yang Xu
- **时间**: 2026-10-31T19:34:02Z
- **提交信息**: [Experimental] Qwen 3.5 GDN block: decode and MTP verify behind a backend registry, with an SM100 CuTe DSL backend (#8131)

Adds `flashinfer.qwen_3_5_gdn_block` (experimental). It runs the gated-delta-net sub-layer of Qwen 3.5-architecture models for one decode or MTP-verify step as one call: BA projection, causal conv update, gating, gated delta rule over the caller's SSM state pool, gated RMSNorm, static FP8 output.

- Backends plug in through a registry (`register_backend(name, support_fn, build_fn)`).
- The first backend, `frost`, is CuTe DSL for SM100 at the Qwen3.8-27B TP 1 geometry. It serves verify up to 4 requests and decode up to 65535 rows.
- `benchmarks/bench_qwen_3_5_gdn_block.py` times any registered backend under CUDA-graph replay with a cold L2.

B200 (1000 W), us per layer, `frost` vs vLLM main's chain for the same sub-layer:

- MTP verify, T 6: 1 request 14.47 vs 23.42 (1.62x); 2 requests 21.09 vs 25.83 (1.22x); 4 requests 33.14 vs 34.17 (1.03x).
- Decode: 1.07-1.27x at 2-64 rows, 0.89x at 1 row.

Tracking issue: #8130. AI-assisted.

Co-Authored-By: Claude Opus 5.5 <noreply@anthropic.com>

### [e5eb9a5](https://github.com/flashinfer-ai/flashinfer/commit/e5eb9a501959ab6b61a72b5f0185d99138c58c11)

- **作者**: eigen
- **时间**: 2026-10-31T19:05:10Z
- **提交信息**: [SM120] Paged FP8 MQA logits: route nine RTX 5090 h64 next_n 5/6 shapes to the native-atom programs (#8136)

The SM120a paged FP8 MQA logits kernel
(`flashinfer/experimental/deepgemm_sm120_paged_mqa_logits`) runs a
metadata scheduler and then a logits kernel. It picks a route for each
device from a table keyed by the GPU's SM count. A route pairs a
scheduler (the one-warp static scheduler, the dynamic scheduler or the
CTA-parallel static scheduler) with a logits program. That program is
either the catalog default program, which is built with
`--use_fast_math`, or a tuned program. The native-atom programs
`atom5_mpf_bta_ha_k2q_ef` (next_n 5) and `atom6_mpf_bta_ha_ef` (next_n
6) and their routes are already on main. This PR changes only the
catalog: 6 new keys and 1 changed entry in the RTX 5090 (170 SMs) device
table. It adds no program, unit or route. Nine h64, page-64, next_n 5/6
shapes on RTX 5090 move from the default route to the native-atom route,
which is built without fast math. For next_n 5 and 6, batches 129..255
at the 16384-token context also move to the native-atom route, because
they fall between two moved grid rows. The other 207 measured shapes run
the same program on both sides. RTX PRO 6000 (188 SMs) reads only its
own table, which is unchanged, so its routes are the same and were not
re-timed. Over two independent runs, the geometric-mean speedup on the 9
changed shapes is 1.078× / 1.082× (per shape 1.027×-1.178×).

Table: kernel time of one call (scheduler + logits kernels) on NVIDIA
GeForce RTX 5090 (170 SMs, sm_120a), driver 620.62, with the CUDA 13.0
runtime (torch 2.14.1+cu130) and the CUDA 13.4.92 JIT toolchain. Each
row is one shape (heads, page size, next_n, batch, context tokens).
Baseline is the shipped route on main and new is this PR. Latency is in
µs, and speedup = baseline µs / new µs. The table covers two independent
runs (seeds 760 and 52021, one GPU per seed). On `changed` rows the new
side runs the native-atom program. On `unchanged` rows both sides run
the same shipped program.

**RTX 5090**

| heads | page | next_n | batch | context | state | baseline µs (760) |
new µs | speedup | baseline µs (52021) | new µs | speedup |
|---:|---:|---:|---:|---:|:--|---:|---:|---:|---:|---:|---:|
| 32 | 64 | 1 | 8 | 4096 | unchanged | 7.20 | 7.20 | 1.000× | 7.23 |
7.26 | 0.996× |
| 32 | 64 | 1 | 64 | 4096 | unchanged | 29.41 | 29.41 | 1.000× | 29.25 |
29.21 | 1.001× |
| 32 | 64 | 1 | 256 | 4096 | unchanged | 100.70 | 100.67 | 1.000× |
100.03 | 100.06 | 1.000× |
| 32 | 64 | 1 | 1 | 16384 | unchanged | 6.18 | 6.18 | 1.000× | 6.14 |
6.11 | 1.005× |
| 32 | 64 | 1 | 8 | 16384 | unchanged | 16.67 | 16.67 | 1.000× | 16.51 |
16.51 | 1.000× |
| 32 | 64 | 1 | 32 | 16384 | unchanged | 52.51 | 52.51 | 1.000× | 52.06
| 52.03 | 1.001× |
| 32 | 64 | 1 | 64 | 16384 | unchanged | 101.18 | 101.18 | 1.000× |
100.06 | 100.00 | 1.001× |
| 32 | 64 | 1 | 128 | 16384 | unchanged | 192.96 | 192.99 | 1.000× |
191.48 | 191.42 | 1.000× |
| 32 | 64 | 1 | 256 | 16384 | unchanged | 374.36 | 374.36 | 1.000× |
373.13 | 373.12 | 1.000× |
| 32 | 64 | 1 | 8 | 65536 | unchanged | 55.87 | 55.87 | 1.000× | 55.55 |
55.55 | 1.000× |
| 32 | 64 | 1 | 32 | 65536 | unchanged | 188.83 | 188.83 | 1.000× |
187.52 | 187.58 | 1.000× |
| 32 | 64 | 1 | 128 | 65536 | unchanged | 725.27 | 725.44 | 1.000× |
719.90 | 720.03 | 1.000× |
| 32 | 64 | 2 | 8 | 4096 | unchanged | 7.52 | 7.49 | 1.004× | 7.52 |
7.52 | 1.000× |
| 32 | 64 | 2 | 64 | 4096 | unchanged | 30.34 | 30.30 | 1.001× | 30.18 |
30.14 | 1.001× |
| 32 | 64 | 2 | 256 | 4096 | unchanged | 105.02 | 105.02 | 1.000× |
103.90 | 103.94 | 1.000× |
| 32 | 64 | 2 | 1 | 16384 | unchanged | 6.43 | 6.40 | 1.005× | 6.37 |
6.37 | 1.000× |
| 32 | 64 | 2 | 8 | 16384 | unchanged | 17.44 | 17.44 | 1.000× | 17.31 |
17.25 | 1.004× |
| 32 | 64 | 2 | 32 | 16384 | unchanged | 53.98 | 53.98 | 1.000× | 53.34
| 53.41 | 0.999× |
| 32 | 64 | 2 | 64 | 16384 | unchanged | 104.70 | 104.67 | 1.000× |
103.65 | 103.68 | 1.000× |
| 32 | 64 | 2 | 128 | 16384 | unchanged | 203.42 | 203.42 | 1.000× |
201.76 | 201.76 | 1.000× |
| 32 | 64 | 2 | 256 | 16384 | unchanged | 394.11 | 394.46 | 0.999× |
391.64 | 391.90 | 0.999× |
| 32 | 64 | 2 | 8 | 65536 | unchanged | 57.28 | 57.31 | 0.999× | 56.99 |
56.99 | 1.000× |
| 32 | 64 | 2 | 32 | 65536 | unchanged | 197.92 | 197.85 | 1.000× |
196.67 | 196.64 | 1.000× |
| 32 | 64 | 2 | 128 | 65536 | unchanged | 764.15 | 764.48 | 1.000× |
756.79 | 756.92 | 1.000× |
| 32 | 64 | 3 | 8 | 4096 | unchanged | 8.67 | 8.67 | 1.000× | 8.51 |
8.51 | 1.000× |
| 32 | 64 | 3 | 64 | 4096 | unchanged | 31.87 | 31.87 | 1.000× | 31.62 |
31.58 | 1.001× |
| 32 | 64 | 3 | 256 | 4096 | unchanged | 112.19 | 112.25 | 0.999× |
110.69 | 110.66 | 1.000× |
| 32 | 64 | 3 | 1 | 16384 | unchanged | 6.43 | 6.43 | 1.000× | 6.56 |
6.56 | 1.000× |
| 32 | 64 | 3 | 8 | 16384 | unchanged | 18.02 | 18.05 | 0.998× | 17.92 |
17.98 | 0.996× |
| 32 | 64 | 3 | 32 | 16384 | unchanged | 56.58 | 56.58 | 1.000× | 56.06
| 56.09 | 0.999× |
| 32 | 64 | 3 | 64 | 16384 | unchanged | 110.91 | 110.94 | 1.000× |
110.02 | 110.05 | 1.000× |
| 32 | 64 | 3 | 128 | 16384 | unchanged | 214.88 | 214.91 | 1.000× |
213.05 | 213.10 | 1.000× |
| 32 | 64 | 3 | 256 | 16384 | unchanged | 418.55 | 418.52 | 1.000× |
414.81 | 414.30 | 1.001× |
| 32 | 64 | 3 | 8 | 65536 | unchanged | 59.81 | 59.81 | 1.000× | 59.33 |
59.33 | 1.000× |
| 32 | 64 | 3 | 32 | 65536 | unchanged | 208.61 | 208.57 | 1.000× |
207.33 | 207.39 | 1.000× |
| 32 | 64 | 3 | 128 | 65536 | unchanged | 808.20 | 808.77 | 0.999× |
804.54 | 804.25 | 1.000× |
| 32 | 64 | 4 | 8 | 4096 | unchanged | 10.46 | 10.46 | 1.000× | 10.30 |
10.30 | 1.000× |
| 32 | 64 | 4 | 64 | 4096 | unchanged | 33.50 | 33.54 | 0.999× | 33.09 |
33.05 | 1.001× |
| 32 | 64 | 4 | 256 | 4096 | unchanged | 119.01 | 118.99 | 1.000× |
118.59 | 118.50 | 1.001× |
| 32 | 64 | 4 | 1 | 16384 | unchanged | 6.69 | 6.69 | 1.000× | 6.69 |
6.72 | 0.995× |
| 32 | 64 | 4 | 8 | 16384 | unchanged | 18.56 | 18.56 | 1.000× | 18.78 |
18.72 | 1.003× |
| 32 | 64 | 4 | 32 | 16384 | unchanged | 59.62 | 59.58 | 1.001× | 58.78
| 58.82 | 0.999× |
| 32 | 64 | 4 | 64 | 16384 | unchanged | 117.82 | 117.82 | 1.000× |
116.45 | 116.42 | 1.000× |
| 32 | 64 | 4 | 128 | 16384 | unchanged | 226.14 | 226.17 | 1.000× |
223.97 | 223.97 | 1.000× |
| 32 | 64 | 4 | 256 | 16384 | unchanged | 439.74 | 439.71 | 1.000× |
436.83 | 437.15 | 0.999× |
| 32 | 64 | 4 | 8 | 65536 | unchanged | 62.43 | 62.43 | 1.000× | 62.34 |
62.37 | 1.000× |
| 32 | 64 | 4 | 32 | 65536 | unchanged | 223.36 | 223.32 | 1.000× |
220.06 | 220.09 | 1.000× |
| 32 | 64 | 4 | 128 | 65536 | unchanged | 860.19 | 860.31 | 1.000× |
855.24 | 855.93 | 0.999× |
| 32 | 64 | 5 | 8 | 4096 | unchanged | 11.65 | 11.65 | 1.000× | 11.36 |
11.36 | 1.000× |
| 32 | 64 | 5 | 64 | 4096 | unchanged | 35.26 | 35.26 | 1.000× | 35.94 |
35.90 | 1.001× |
| 32 | 64 | 5 | 256 | 4096 | unchanged | 138.65 | 138.59 | 1.000× |
137.44 | 137.47 | 1.000× |
| 32 | 64 | 5 | 1 | 16384 | unchanged | 7.26 | 7.30 | 0.996× | 7.26 |
7.26 | 1.000× |
| 32 | 64 | 5 | 8 | 16384 | unchanged | 20.13 | 20.13 | 1.000× | 20.03 |
19.97 | 1.003× |
| 32 | 64 | 5 | 32 | 16384 | unchanged | 64.73 | 64.70 | 1.000× | 63.68
| 63.65 | 1.001× |
| 32 | 64 | 5 | 64 | 16384 | unchanged | 134.01 | 134.01 | 1.000× |
132.70 | 132.73 | 1.000× |
| 32 | 64 | 5 | 128 | 16384 | unchanged | 245.05 | 245.50 | 0.998× |
240.96 | 240.73 | 1.001× |
| 32 | 64 | 5 | 256 | 16384 | unchanged | 455.87 | 455.35 | 1.001× |
451.90 | 452.28 | 0.999× |
| 32 | 64 | 5 | 8 | 65536 | unchanged | 69.47 | 69.47 | 1.000× | 70.21 |
70.21 | 1.000× |
| 32 | 64 | 5 | 32 | 65536 | unchanged | 236.89 | 236.77 | 1.001× |
234.78 | 234.72 | 1.000× |
| 32 | 64 | 5 | 128 | 65536 | unchanged | 879.38 | 879.99 | 0.999× |
867.29 | 865.03 | 1.003× |
| 32 | 64 | 6 | 8 | 4096 | unchanged | 11.58 | 11.58 | 1.000× | 11.30 |
11.30 | 1.000× |
| 32 | 64 | 6 | 64 | 4096 | unchanged | 38.85 | 38.85 | 1.000× | 38.69 |
38.66 | 1.001× |
| 32 | 64 | 6 | 256 | 4096 | unchanged | 148.67 | 148.67 | 1.000× |
145.63 | 145.57 | 1.000× |
| 32 | 64 | 6 | 1 | 16384 | unchanged | 7.14 | 7.14 | 1.000× | 7.10 |
7.14 | 0.996× |
| 32 | 64 | 6 | 8 | 16384 | unchanged | 22.62 | 22.62 | 1.000× | 22.05 |
22.11 | 0.997× |
| 32 | 64 | 6 | 32 | 16384 | unchanged | 72.70 | 72.73 | 1.000× | 73.15
| 73.12 | 1.000× |
| 32 | 64 | 6 | 64 | 16384 | unchanged | 145.79 | 145.82 | 1.000× |
142.78 | 142.85 | 1.000× |
| 32 | 64 | 6 | 128 | 16384 | unchanged | 270.78 | 270.62 | 1.001× |
266.56 | 266.65 | 1.000× |
| 32 | 64 | 6 | 256 | 16384 | unchanged | 531.70 | 530.62 | 1.002× |
519.07 | 519.10 | 1.000× |
| 32 | 64 | 6 | 8 | 65536 | unchanged | 72.03 | 72.10 | 0.999× | 72.58 |
72.58 | 1.000× |
| 32 | 64 | 6 | 32 | 65536 | unchanged | 266.36 | 266.56 | 0.999× |
261.60 | 261.82 | 0.999× |
| 32 | 64 | 6 | 128 | 65536 | unchanged | 1050.77 | 1051.33 | 0.999× |
1025.29 | 1028.17 | 0.997× |
| 32 | 128 | 1 | 8 | 4096 | unchanged | 7.20 | 7.20 | 1.000× | 7.23 |
7.23 | 1.000× |
| 32 | 128 | 1 | 64 | 4096 | unchanged | 29.70 | 29.70 | 1.000× | 29.57
| 29.60 | 0.999× |
| 32 | 128 | 1 | 256 | 4096 | unchanged | 100.61 | 100.64 | 1.000× |
99.94 | 99.97 | 1.000× |
| 32 | 128 | 1 | 1 | 16384 | unchanged | 6.17 | 6.14 | 1.005× | 6.21 |
6.18 | 1.005× |
| 32 | 128 | 1 | 8 | 16384 | unchanged | 16.89 | 16.90 | 1.000× | 16.70
| 16.74 | 0.998× |
| 32 | 128 | 1 | 32 | 16384 | unchanged | 52.42 | 52.38 | 1.001× | 51.97
| 51.94 | 1.001× |
| 32 | 128 | 1 | 64 | 16384 | unchanged | 100.61 | 100.58 | 1.000× |
99.97 | 99.93 | 1.000× |
| 32 | 128 | 1 | 128 | 16384 | unchanged | 193.25 | 193.28 | 1.000× |
192.25 | 192.16 | 1.000× |
| 32 | 128 | 1 | 256 | 16384 | unchanged | 373.59 | 373.79 | 0.999× |
372.32 | 372.09 | 1.001× |
| 32 | 128 | 1 | 8 | 65536 | unchanged | 55.81 | 55.81 | 1.000× | 55.36
| 55.36 | 1.000× |
| 32 | 128 | 1 | 32 | 65536 | unchanged | 188.67 | 188.70 | 1.000× |
187.23 | 187.29 | 1.000× |
| 32 | 128 | 1 | 128 | 65536 | unchanged | 723.93 | 724.02 | 1.000× |
719.80 | 720.09 | 1.000× |
| 32 | 128 | 2 | 8 | 4096 | unchanged | 7.55 | 7.55 | 1.000× | 7.58 |
7.55 | 1.004× |
| 32 | 128 | 2 | 64 | 4096 | unchanged | 30.56 | 30.56 | 1.000× | 30.18
| 30.14 | 1.001× |
| 32 | 128 | 2 | 256 | 4096 | unchanged | 105.69 | 105.73 | 1.000× |
104.96 | 104.99 | 1.000× |
| 32 | 128 | 2 | 1 | 16384 | unchanged | 6.46 | 6.46 | 1.000× | 6.46 |
6.50 | 0.995× |
| 32 | 128 | 2 | 8 | 16384 | unchanged | 17.18 | 17.22 | 0.998× | 16.96
| 17.02 | 0.996× |
| 32 | 128 | 2 | 32 | 16384 | unchanged | 54.05 | 54.05 | 1.000× | 53.50
| 53.57 | 0.999× |
| 32 | 128 | 2 | 64 | 16384 | unchanged | 104.83 | 104.83 | 1.000× |
104.35 | 104.32 | 1.000× |
| 32 | 128 | 2 | 128 | 16384 | unchanged | 203.68 | 203.71 | 1.000× |
201.95 | 201.97 | 1.000× |
| 32 | 128 | 2 | 256 | 16384 | unchanged | 395.29 | 395.32 | 1.000× |
391.39 | 392.03 | 0.998× |
| 32 | 128 | 2 | 8 | 65536 | unchanged | 57.22 | 57.22 | 1.000× | 56.93
| 56.93 | 1.000× |
| 32 | 128 | 2 | 32 | 65536 | unchanged | 198.56 | 198.53 | 1.000× |
196.70 | 196.64 | 1.000× |
| 32 | 128 | 2 | 128 | 65536 | unchanged | 766.68 | 767.09 | 0.999× |
758.04 | 758.55 | 0.999× |
| 32 | 128 | 3 | 8 | 4096 | unchanged | 8.74 | 8.74 | 1.000× | 8.61 |
8.61 | 1.000× |
| 32 | 128 | 3 | 64 | 4096 | unchanged | 32.06 | 32.06 | 1.000× | 31.97
| 31.97 | 1.000× |
| 32 | 128 | 3 | 256 | 4096 | unchanged | 111.77 | 111.78 | 1.000× |
111.58 | 111.58 | 1.000× |
| 32 | 128 | 3 | 1 | 16384 | unchanged | 6.78 | 6.78 | 1.000× | 6.78 |
6.75 | 1.005× |
| 32 | 128 | 3 | 8 | 16384 | unchanged | 18.11 | 18.18 | 0.997× | 18.18
| 18.30 | 0.993× |
| 32 | 128 | 3 | 32 | 16384 | unchanged | 56.80 | 56.77 | 1.001× | 56.29
| 56.32 | 0.999× |
| 32 | 128 | 3 | 64 | 16384 | unchanged | 111.68 | 111.65 | 1.000× |
110.24 | 110.27 | 1.000× |
| 32 | 128 | 3 | 128 | 16384 | unchanged | 214.56 | 214.65 | 1.000× |
212.96 | 213.12 | 0.999× |
| 32 | 128 | 3 | 256 | 16384 | unchanged | 417.34 | 417.27 | 1.000× |
415.42 | 415.54 | 1.000× |
| 32 | 128 | 3 | 8 | 65536 | unchanged | 60.32 | 60.32 | 1.000× | 59.71
| 59.71 | 1.000× |
| 32 | 128 | 3 | 32 | 65536 | unchanged | 210.27 | 210.33 | 1.000× |
207.71 | 207.65 | 1.000× |
| 32 | 128 | 3 | 128 | 65536 | unchanged | 808.61 | 808.10 | 1.001× |
809.34 | 810.50 | 0.999× |
| 32 | 128 | 4 | 8 | 4096 | unchanged | 9.02 | 9.02 | 1.000× | 8.90 |
8.86 | 1.004× |
| 32 | 128 | 4 | 64 | 4096 | unchanged | 33.31 | 33.31 | 1.000× | 33.15
| 33.12 | 1.001× |
| 32 | 128 | 4 | 256 | 4096 | unchanged | 118.46 | 118.43 | 1.000× |
118.69 | 118.72 | 1.000× |
| 32 | 128 | 4 | 1 | 16384 | unchanged | 7.58 | 7.55 | 1.004× | 7.58 |
7.55 | 1.004× |
| 32 | 128 | 4 | 8 | 16384 | unchanged | 18.85 | 18.88 | 0.998× | 18.53
| 18.46 | 1.003× |
| 32 | 128 | 4 | 32 | 16384 | unchanged | 59.04 | 59.04 | 1.000× | 58.66
| 58.56 | 1.002× |
| 32 | 128 | 4 | 64 | 16384 | unchanged | 117.63 | 117.60 | 1.000× |
117.79 | 117.86 | 0.999× |
| 32 | 128 | 4 | 128 | 16384 | unchanged | 225.98 | 225.85 | 1.001× |
224.32 | 224.35 | 1.000× |
| 32 | 128 | 4 | 256 | 16384 | unchanged | 439.35 | 439.19 | 1.000× |
437.18 | 437.88 | 0.998× |
| 32 | 128 | 4 | 8 | 65536 | unchanged | 62.46 | 62.43 | 1.001× | 61.60
| 61.66 | 0.999× |
| 32 | 128 | 4 | 32 | 65536 | unchanged | 223.29 | 223.00 | 1.001× |
220.19 | 220.16 | 1.000× |
| 32 | 128 | 4 | 128 | 65536 | unchanged | 850.39 | 849.76 | 1.001× |
851.53 | 851.59 | 1.000× |
| 32 | 128 | 5 | 8 | 4096 | unchanged | 11.71 | 11.71 | 1.000× | 11.39 |
11.39 | 1.000× |
| 32 | 128 | 5 | 64 | 4096 | unchanged | 35.45 | 35.45 | 1.000× | 35.81
| 35.78 | 1.001× |
| 32 | 128 | 5 | 256 | 4096 | unchanged | 138.78 | 138.81 | 1.000× |
137.41 | 137.37 | 1.000× |
| 32 | 128 | 5 | 1 | 16384 | unchanged | 7.33 | 7.33 | 1.000× | 7.26 |
7.30 | 0.996× |
| 32 | 128 | 5 | 8 | 16384 | unchanged | 19.78 | 19.78 | 1.000× | 19.65
| 19.62 | 1.002× |
| 32 | 128 | 5 | 32 | 16384 | unchanged | 64.54 | 64.51 | 1.000× | 64.22
| 64.19 | 1.000× |
| 32 | 128 | 5 | 64 | 16384 | unchanged | 134.17 | 134.14 | 1.000× |
131.71 | 131.78 | 1.000× |
| 32 | 128 | 5 | 128 | 16384 | unchanged | 245.02 | 245.05 | 1.000× |
244.48 | 244.41 | 1.000× |
| 32 | 128 | 5 | 256 | 16384 | unchanged | 452.89 | 453.47 | 0.999× |
449.63 | 449.34 | 1.001× |
| 32 | 128 | 5 | 8 | 65536 | unchanged | 69.95 | 69.92 | 1.000× | 69.22
| 69.22 | 1.000× |
| 32 | 128 | 5 | 32 | 65536 | unchanged | 236.19 | 236.12 | 1.000× |
235.01 | 234.91 | 1.000× |
| 32 | 128 | 5 | 128 | 65536 | unchanged | 879.54 | 880.37 | 0.999× |
862.30 | 863.24 | 0.999× |
| 32 | 128 | 6 | 8 | 4096 | unchanged | 11.62 | 11.62 | 1.000× | 11.30 |
11.30 | 1.000× |
| 32 | 128 | 6 | 64 | 4096 | unchanged | 39.14 | 39.14 | 1.000× | 37.86
| 37.82 | 1.001× |
| 32 | 128 | 6 | 256 | 4096 | unchanged | 148.03 | 148.09 | 1.000× |
145.82 | 145.82 | 1.000× |
| 32 | 128 | 6 | 1 | 16384 | unchanged | 7.26 | 7.26 | 1.000× | 7.26 |
7.26 | 1.000× |
| 32 | 128 | 6 | 8 | 16384 | unchanged | 22.02 | 22.02 | 1.000× | 22.11
| 22.18 | 0.997× |
| 32 | 128 | 6 | 32 | 16384 | unchanged | 72.48 | 72.48 | 1.000× | 72.42
| 72.45 | 1.000× |
| 32 | 128 | 6 | 64 | 16384 | unchanged | 144.83 | 144.83 | 1.000× |
143.01 | 143.23 | 0.998× |
| 32 | 128 | 6 | 128 | 16384 | unchanged | 269.69 | 269.72 | 1.000× |
265.66 | 265.66 | 1.000× |
| 32 | 128 | 6 | 256 | 16384 | unchanged | 546.30 | 546.50 | 1.000× |
535.71 | 535.71 | 1.000× |
| 32 | 128 | 6 | 8 | 65536 | unchanged | 72.13 | 72.13 | 1.000× | 72.45
| 72.45 | 1.000× |
| 32 | 128 | 6 | 32 | 65536 | unchanged | 264.80 | 264.76 | 1.000× |
260.48 | 260.48 | 1.000× |
| 32 | 128 | 6 | 128 | 65536 | unchanged | 1078.70 | 1078.07 | 1.001× |
1059.89 | 1058.66 | 1.001× |
| 64 | 64 | 1 | 8 | 4096 | unchanged | 7.49 | 7.49 | 1.000× | 7.46 |
7.49 | 0.996× |
| 64 | 64 | 1 | 64 | 4096 | unchanged | 30.08 | 30.08 | 1.000× | 29.86 |
29.82 | 1.001× |
| 64 | 64 | 1 | 256 | 4096 | unchanged | 102.08 | 102.08 | 1.000× |
101.25 | 101.25 | 1.000× |
| 64 | 64 | 1 | 1 | 16384 | unchanged | 6.40 | 6.40 | 1.000× | 6.34 |
6.34 | 1.000× |
| 64 | 64 | 1 | 8 | 16384 | unchanged | 17.15 | 17.15 | 1.000× | 16.83 |
16.83 | 1.000× |
| 64 | 64 | 1 | 32 | 16384 | unchanged | 52.89 | 52.89 | 1.000× | 52.45
| 52.42 | 1.001× |
| 64 | 64 | 1 | 64 | 16384 | unchanged | 101.53 | 101.53 | 1.000× |
100.80 | 100.73 | 1.001× |
| 64 | 64 | 1 | 128 | 16384 | unchanged | 194.53 | 194.49 | 1.000× |
192.93 | 192.89 | 1.000× |
| 64 | 64 | 1 | 256 | 16384 | unchanged | 376.12 | 376.03 | 1.000× |
373.92 | 374.01 | 1.000× |
| 64 | 64 | 1 | 8 | 65536 | unchanged | 56.29 | 56.29 | 1.000× | 55.81 |
55.84 | 0.999× |
| 64 | 64 | 1 | 32 | 65536 | unchanged | 189.31 | 189.31 | 1.000× |
188.25 | 188.32 | 1.000× |
| 64 | 64 | 1 | 128 | 65536 | unchanged | 726.39 | 726.39 | 1.000× |
725.15 | 725.34 | 1.000× |
| 64 | 64 | 2 | 8 | 4096 | unchanged | 8.29 | 8.29 | 1.000× | 8.22 |
8.22 | 1.000× |
| 64 | 64 | 2 | 64 | 4096 | unchanged | 32.16 | 32.16 | 1.000× | 31.97 |
31.87 | 1.003× |
| 64 | 64 | 2 | 256 | 4096 | unchanged | 109.28 | 109.28 | 1.000× |
109.21 | 109.22 | 1.000× |
| 64 | 64 | 2 | 1 | 16384 | unchanged | 6.85 | 6.82 | 1.005× | 6.69 |
6.72 | 0.995× |
| 64 | 64 | 2 | 8 | 16384 | unchanged | 18.18 | 18.21 | 0.998× | 18.08 |
17.98 | 1.005× |
| 64 | 64 | 2 | 32 | 16384 | unchanged | 55.71 | 55.74 | 0.999× | 55.10
| 55.17 | 0.999× |
| 64 | 64 | 2 | 64 | 16384 | unchanged | 108.26 | 108.29 | 1.000× |
107.45 | 107.52 | 0.999× |
| 64 | 64 | 2 | 128 | 16384 | unchanged | 208.41 | 208.38 | 1.000× |
206.97 | 206.88 | 1.000× |
| 64 | 64 | 2 | 256 | 16384 | unchanged | 403.45 | 403.45 | 1.000× |
402.69 | 402.65 | 1.000× |
| 64 | 64 | 2 | 8 | 65536 | unchanged | 59.01 | 59.01 | 1.000× | 58.49 |
58.50 | 1.000× |
| 64 | 64 | 2 | 32 | 65536 | unchanged | 202.56 | 202.59 | 1.000× |
200.70 | 200.73 | 1.000× |
| 64 | 64 | 2 | 128 | 65536 | unchanged | 783.21 | 783.09 | 1.000× |
775.74 | 775.56 | 1.000× |
| 64 | 64 | 3 | 8 | 4096 | unchanged | 11.94 | 11.94 | 1.000× | 11.65 |
11.65 | 1.000× |
| 64 | 64 | 3 | 64 | 4096 | unchanged | 35.68 | 35.71 | 0.999× | 35.68 |
35.74 | 0.998× |
| 64 | 64 | 3 | 256 | 4096 | unchanged | 150.94 | 150.94 | 1.000× |
147.13 | 147.26 | 0.999× |
| 64 | 64 | 3 | 1 | 16384 | unchanged | 7.55 | 7.55 | 1.000× | 7.52 |
7.46 | 1.008× |
| 64 | 64 | 3 | 8 | 16384 | unchanged | 21.06 | 21.09 | 0.999× | 20.45 |
20.45 | 1.000× |
| 64 | 64 | 3 | 32 | 16384 | unchanged | 65.06 | 65.06 | 1.000× | 65.41
| 65.34 | 1.001× |
| 64 | 64 | 3 | 64 | 16384 | unchanged | 145.50 | 145.47 | 1.000× |
143.36 | 143.30 | 1.000× |
| 64 | 64 | 3 | 128 | 16384 | unchanged | 269.02 | 269.05 | 1.000× |
264.48 | 264.57 | 1.000× |
| 64 | 64 | 3 | 256 | 16384 | unchanged | 519.64 | 519.07 | 1.001× |
510.36 | 510.57 | 1.000× |
| 64 | 64 | 3 | 8 | 65536 | unchanged | 64.77 | 64.77 | 1.000× | 66.43 |
66.37 | 1.001× |
| 64 | 64 | 3 | 32 | 65536 | unchanged | 259.07 | 259.33 | 0.999× |
254.94 | 255.13 | 0.999× |
| 64 | 64 | 3 | 128 | 65536 | unchanged | 1022.98 | 1022.18 | 1.001× |
998.57 | 997.85 | 1.001× |
| 64 | 64 | 4 | 8 | 4096 | unchanged | 11.84 | 11.84 | 1.000× | 11.65 |
11.65 | 1.000× |
| 64 | 64 | 4 | 64 | 4096 | unchanged | 39.20 | 39.20 | 1.000× | 38.72 |
38.75 | 0.999× |
| 64 | 64 | 4 | 256 | 4096 | unchanged | 180.16 | 180.09 | 1.000× |
176.93 | 176.99 | 1.000× |
| 64 | 64 | 4 | 1 | 16384 | unchanged | 7.55 | 7.55 | 1.000× | 7.49 |
7.49 | 1.000× |
| 64 | 64 | 4 | 8 | 16384 | unchanged | 23.10 | 23.10 | 1.000× | 22.72 |
22.78 | 0.997× |
| 64 | 64 | 4 | 32 | 16384 | unchanged | 72.29 | 72.35 | 0.999× | 76.21
| 76.00 | 1.003× |
| 64 | 64 | 4 | 64 | 16384 | unchanged | 177.98 | 177.92 | 1.000× |
174.75 | 174.59 | 1.001× |
| 64 | 64 | 4 | 128 | 16384 | unchanged | 338.59 | 338.24 | 1.001× |
332.25 | 332.00 | 1.001× |
| 64 | 64 | 4 | 256 | 16384 | unchanged | 665.11 | 665.50 | 0.999× |
647.75 | 646.92 | 1.001× |
| 64 | 64 | 4 | 8 | 65536 | unchanged | 77.28 | 77.28 | 1.000× | 81.50 |
81.50 | 1.000× |
| 64 | 64 | 4 | 32 | 65536 | unchanged | 328.44 | 328.41 | 1.000× |
322.30 | 322.27 | 1.000× |
| 64 | 64 | 4 | 128 | 65536 | unchanged | 1328.33 | 1328.75 | 1.000× |
1301.84 | 1300.64 | 1.001× |
| 64 | 64 | 5 | 8 | 4096 | unchanged | 11.14 | 11.14 | 1.000× | 10.85 |
10.85 | 1.000× |
| 64 | 64 | 5 | 64 | 4096 | unchanged | 50.08 | 50.11 | 0.999× | 49.41 |
49.38 | 1.001× |
| 64 | 64 | 5 | 256 | 4096 | changed | 253.31 | 228.19 | 1.110× | 248.77
| 223.55 | 1.113× |
| 64 | 64 | 5 | 1 | 16384 | unchanged | 8.57 | 8.54 | 1.004× | 8.45 |
8.48 | 0.996× |
| 64 | 64 | 5 | 8 | 16384 | unchanged | 28.42 | 28.41 | 1.000× | 27.90 |
27.97 | 0.998× |
| 64 | 64 | 5 | 32 | 16384 | unchanged | 113.89 | 113.86 | 1.000× |
112.93 | 112.77 | 1.001× |
| 64 | 64 | 5 | 64 | 16384 | unchanged | 213.24 | 213.34 | 1.000× |
213.66 | 213.44 | 1.001× |
| 64 | 64 | 5 | 128 | 16384 | changed | 495.26 | 421.24 | 1.176× |
488.41 | 414.75 | 1.178× |
| 64 | 64 | 5 | 256 | 16384 | changed | 932.92 | 838.79 | 1.112× |
914.63 | 816.98 | 1.120× |
| 64 | 64 | 5 | 8 | 65536 | unchanged | 119.39 | 119.49 | 0.999× |
118.08 | 117.98 | 1.001× |
| 64 | 64 | 5 | 32 | 65536 | unchanged | 520.70 | 520.95 | 1.000× |
516.86 | 517.02 | 1.000× |
| 64 | 64 | 5 | 128 | 65536 | changed | 1918.45 | 1664.91 | 1.152× |
1880.56 | 1627.91 | 1.155× |
| 64 | 64 | 6 | 8 | 4096 | unchanged | 11.10 | 11.14 | 0.997× | 10.85 |
10.82 | 1.003× |
| 64 | 64 | 6 | 64 | 4096 | unchanged | 49.44 | 49.41 | 1.001× | 49.22 |
49.25 | 0.999× |
| 64 | 64 | 6 | 256 | 4096 | changed | 275.23 | 268.06 | 1.027× | 271.29
| 261.79 | 1.036× |
| 64 | 64 | 6 | 1 | 16384 | unchanged | 8.48 | 8.48 | 1.000× | 8.54 |
8.51 | 1.004× |
| 64 | 64 | 6 | 8 | 16384 | unchanged | 28.06 | 28.06 | 1.000× | 27.62 |
27.55 | 1.002× |
| 64 | 64 | 6 | 32 | 16384 | unchanged | 114.59 | 114.69 | 0.999× |
114.05 | 114.11 | 0.999× |
| 64 | 64 | 6 | 64 | 16384 | changed | 269.21 | 259.26 | 1.038× | 264.29
| 253.63 | 1.042× |
| 64 | 64 | 6 | 128 | 16384 | changed | 517.40 | 498.01 | 1.039× |
507.71 | 489.24 | 1.038× |
| 64 | 64 | 6 | 256 | 16384 | changed | 1037.23 | 1006.96 | 1.030× |
1012.29 | 974.26 | 1.039× |
| 64 | 64 | 6 | 8 | 65536 | unchanged | 117.76 | 117.89 | 0.999× |
117.31 | 117.25 | 1.001× |
| 64 | 64 | 6 | 32 | 65536 | unchanged | 527.54 | 528.19 | 0.999× |
528.71 | 528.35 | 1.001× |
| 64 | 64 | 6 | 128 | 65536 | changed | 2047.97 | 1994.74 | 1.027× |
2013.73 | 1951.49 | 1.032× |

The kernel's other variants are the dense FP4 and FP8 lightning-indexer
logits and the paged FP8 MQA logits for SM100a/SM103a
(`deepgemm_dense_mqa`). This paged FP8 package ships on sm_120a only.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* Improved kernel selection for additional 64-head, 64-page workload
configurations, including batch sizes 64 and above. Certain cases that
previously had no selected kernel now use an optimized option. This may
improve support and execution efficiency for affected workloads.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery Huang <averyh@nvidia.com>

### [5086eb9](https://github.com/flashinfer-ai/flashinfer/commit/5086eb9db8be53c5b7bd331bfe810843034ce4fe)

- **作者**: eigen
- **时间**: 2026-10-31T18:43:24Z
- **提交信息**: perf(cake_mega_moe_v3): faster TP/EP rank programs on sm_103a (#8133)

`flashinfer.experimental.mega_moe_v3` runs the Cake MegaMoE v3 prepared
pipeline for the 384-expert, top-6, hidden-5120 model with activation
clamp 10. A single kernel launch covers dispatch, FC1, clamped SwiGLU,
MXFP8 activation quantization, FC2 and weighted combine. The kernel has
four variants on main, and this PR updates one of them: the TP/EP rank
variant. It changes the schedule of 9 of the variant's 32 programs:

- TP4 EP1 and TP8 EP1 at 128 and 512 tokens issue two FC2 N clusters per
ring task.
- TP8 EP1 at 1024 tokens uses evict-first loads in the combine.
- TP4 EP4 and TP8 EP8 at 4096 tokens load A in 32-row boxes. TP8 EP8
also prefetches the dispatch mask.
- TP8 EP8 at 128 and 512 tokens uses a 32-row source tile.

The other 23 programs keep their schedules. The baseline is the previous
Cake version on main, which is the rank variant delivered by #7633 and
#8095. The changed shapes run up to 1.054x faster (TP8 EP1 at 128
tokens).

| Configuration | Tokens | previous a (µs) | this PR a (µs) | speedup a
| previous b (µs) | this PR b (µs) | speedup b |
|---|---:|---:|---:|---:|---:|---:|---:|
| TP4 EP1 | 1 | 13.74 | 13.75 | 0.999 | 13.92 | 13.92 | 1.000 |
| TP4 EP1 | 4 | 26.21 | 26.18 | 1.001 | 25.76 | 25.78 | 0.999 |
| TP4 EP1 | 16 | 82.20 | 82.18 | 1.000 | 80.92 | 80.93 | 1.000 |
| TP4 EP1 | 32 | 153.14 | 153.12 | 1.000 | 150.69 | 150.71 | 1.000 |
| TP4 EP1 | 128 | 300.34 | 294.61 | 1.020 | 296.28 | 290.39 | 1.020 |
| TP4 EP1 | 512 | 311.08 | 305.53 | 1.018 | 307.08 | 301.05 | 1.020 |
| TP4 EP1 | 1024 | 332.70 | 332.69 | 1.000 | 329.26 | 329.27 | 1.000 |
| TP4 EP1 | 4096 | 439.87 | 439.82 | 1.000 | 438.66 | 438.69 | 1.000 |
| TP8 EP1 | 1 | 12.28 | 12.27 | 1.000 | 12.21 | 12.22 | 0.999 |
| TP8 EP1 | 4 | 18.39 | 18.39 | 1.000 | 18.39 | 18.37 | 1.001 |
| TP8 EP1 | 16 | 53.99 | 53.99 | 1.000 | 53.64 | 53.62 | 1.000 |
| TP8 EP1 | 32 | 96.60 | 96.59 | 1.000 | 96.06 | 96.02 | 1.000 |
| TP8 EP1 | 128 | 189.86 | 180.16 | 1.054 | 189.05 | 179.36 | 1.054 |
| TP8 EP1 | 512 | 199.42 | 189.39 | 1.053 | 198.25 | 188.17 | 1.054 |
| TP8 EP1 | 1024 | 214.73 | 214.59 | 1.001 | 213.20 | 212.98 | 1.001 |
| TP8 EP1 | 4096 | 315.95 | 316.00 | 1.000 | 318.44 | 318.28 | 1.000 |
| TP4 EP4 | 1 | 14.40 | 14.40 | 1.000 | 14.52 | 14.52 | 1.000 |
| TP4 EP4 | 4 | 24.21 | 24.22 | 0.999 | 23.98 | 23.99 | 0.999 |
| TP4 EP4 | 16 | 72.88 | 72.95 | 0.999 | 71.62 | 71.58 | 1.000 |
| TP4 EP4 | 32 | 140.18 | 140.17 | 1.000 | 137.52 | 137.55 | 1.000 |
| TP4 EP4 | 128 | 268.71 | 268.74 | 1.000 | 264.72 | 264.73 | 1.000 |
| TP4 EP4 | 512 | 275.56 | 275.59 | 1.000 | 270.59 | 270.64 | 1.000 |
| TP4 EP4 | 1024 | 282.55 | 282.54 | 1.000 | 277.42 | 277.45 | 1.000 |
| TP4 EP4 | 4096 | 348.06 | 345.31 | 1.008 | 344.02 | 341.33 | 1.008 |
| TP8 EP8 | 1 | 13.05 | 13.06 | 0.999 | 13.06 | 13.07 | 1.000 |
| TP8 EP8 | 4 | 16.00 | 16.00 | 1.000 | 15.95 | 15.96 | 1.000 |
| TP8 EP8 | 16 | 39.45 | 39.46 | 1.000 | 38.72 | 38.71 | 1.000 |
| TP8 EP8 | 32 | 76.03 | 76.00 | 1.000 | 74.72 | 74.74 | 1.000 |
| TP8 EP8 | 128 | 142.58 | 139.50 | 1.022 | 141.17 | 137.22 | 1.029 |
| TP8 EP8 | 512 | 147.43 | 142.16 | 1.037 | 144.14 | 138.33 | 1.042 |
| TP8 EP8 | 1024 | 146.78 | 146.56 | 1.002 | 144.95 | 144.67 | 1.002 |
| TP8 EP8 | 4096 | 195.52 | 193.79 | 1.009 | 194.12 | 192.44 | 1.009 |

*NVIDIA GB300 (sm_103a), CUDA 13.4, driver 580.159.03. Per-call latency.
Speedup = previous / this PR. Columns a and b are two independent
replicates.*

The kernel's other three Cake variants (single-rank routed-FP4 pipeline,
single-rank routed-FP8 pipeline and grouped-GEMM routes) ship on sm_100a
and sm_103a, and the rank variant ships on sm_103a only.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Improvements**
* Updated processing configurations for select FP4 mixture-of-experts
workloads, including 48-expert models at two input lengths. These
adjustments affect how those workloads are handled; other listed route
settings remain unchanged. No new user-facing controls or capabilities
are included in this update.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [6ccf040](https://github.com/flashinfer-ai/flashinfer/commit/6ccf040752ed8f370d2698ca9a7727f16b3b83a0)

- **作者**: eigen
- **时间**: 2026-10-31T18:26:45Z
- **提交信息**: perf(cake_ssd_combined): sm_107a seq_idx check program for single-sequence varlen calls (#8132)

`cake_ssd_combined` holds FlashInfer's Mamba2 SSD combined chunk-scan
prefill kernels. It has 56 programs in seven families: retained exact
scan (11), fused exact scan `exactfused` (11, ring and no-ring
schedules), two-kernel exact scan `exactpre` (12, including the
tail-wave pair programs), metadata-stage fused varlen `exactmeta` (5),
one-launch fused varlen `exactone` (5), chunk-parallel `chunkpar` (6)
and three-phase chunk-parallel `chunkpar3` (6). This PR adds one route
and 4 programs that exist only on sm_107a:
`exactfused_{bf16,f32}_batched_chk` and
`exactfused_{bf16,f32}_batched_zpfchk`. Each one is the fused batched
program (plain or z-prefetch) with one extra CTA added to its persistent
grid. The extra CTA owns no work item. It runs the segment preprocess's
seq_idx check and stores 1 into status word 0 when a sequence id is out
of range or below the previous one, so the status word means the same as
before. A packed-varlen call qualifies for the new route when all of
these hold: it has one sequence, it uses the seq_idx triple form, the
device derives its chunk table, it has no checkpoint outputs, its state
is bf16 or f32, it has fewer heads than SMs, and its batched [1, T] view
is exact-scan and inside the fused window. Such a call now runs as one
launch of the check program, with no preprocess stage. It takes
`_zpfchk` when the z-prefetch rule takes the view (z and at least two
chunks), and `_chk` otherwise. cu_seqlens-form calls and calls with a
caller-supplied chunk table keep their program. For valid calls, outputs
and final states are bitwise identical to those of the previous program.
#7869 is now on main, and this PR is one commit on top of it. The first
table compares with FlashInfer main 4f14b25dc, which has the Cake
version before #7869 (#7740). Against it, all 93 shapes are faster on
both nodes (93/93). The geometric-mean speedup is 1.1963 on node 1 and
1.1951 on node 2, and the smallest speedup is 1.026 (`cp_b4h8c16`).
These numbers include the #7869 changes; the second table compares with
#7869 itself.

**NVIDIA R200 (sm_107a, Rubin), CUDA 13.4.** Each value is the latency
of one whole `cake_ssd_combined` call with a cold L2, as the mean over 8
rounds of 4 input copies. There were two runs on two different nodes,
and both sides were measured on the same GPU in each run. Speedup = main
/ this PR.

| Shape | Node 1 main (µs) | Node 1 this PR (µs) | Node 1 speedup | Node
2 main (µs) | Node 2 this PR (µs) | Node 2 speedup |
|---|---:|---:|---:|---:|---:|---:|
| perf_varlen_1x1 | 7.495 | 7.070 | 1.0602 | 7.697 | 7.167 | 1.0740 |
| perf_varlen_4x1 | 7.727 | 7.256 | 1.0648 | 7.928 | 7.301 | 1.0859 |
| perf_varlen_8x1 | 8.045 | 7.539 | 1.0671 | 8.223 | 7.600 | 1.0820 |
| perf_varlen_32x1 | 13.416 | 11.885 | 1.1288 | 13.377 | 11.853 | 1.1286
|
| perf_varlen_64x1 | 21.627 | 16.094 | 1.3438 | 21.570 | 16.026 | 1.3459
|
| perf_varlen_128x1 | 31.912 | 24.260 | 1.3154 | 31.874 | 24.211 |
1.3165 |
| perf_varlen_256x1 | 56.892 | 41.424 | 1.3734 | 56.818 | 41.344 |
1.3743 |
| perf_varlen_4x8 | 22.652 | 20.567 | 1.1014 | 22.792 | 20.589 | 1.1070
|
| perf_varlen_8x8 | 23.647 | 20.889 | 1.1320 | 23.626 | 20.917 | 1.1295
|
| perf_varlen_16x8 | 28.425 | 23.971 | 1.1858 | 28.411 | 23.913 | 1.1881
|
| perf_varlen_32x8 | 51.014 | 38.811 | 1.3144 | 50.939 | 38.760 | 1.3142
|
| perf_varlen_64x8 | 75.923 | 60.321 | 1.2587 | 75.860 | 60.252 | 1.2590
|
| perf_varlen_32x32 | 150.631 | 100.095 | 1.5049 | 150.533 | 99.982 |
1.5056 |
| perf_varlen_64x32 | 258.781 | 179.597 | 1.4409 | 258.632 | 179.533 |
1.4406 |
| perf_varlen_128x32 | 453.647 | 347.356 | 1.3060 | 453.180 | 347.404 |
1.3045 |
| perf_batched_1x1 | 6.400 | 5.724 | 1.1181 | 6.446 | 5.767 | 1.1177 |
| perf_batched_1x4 | 11.386 | 10.608 | 1.0733 | 11.409 | 10.647 | 1.0716
|
| perf_batched_4x1 | 6.495 | 5.897 | 1.1014 | 6.553 | 5.908 | 1.1092 |
| perf_batched_4x4 | 11.645 | 10.806 | 1.0776 | 11.668 | 10.800 | 1.0804
|
| perf_batched_16x1 | 7.544 | 6.843 | 1.1024 | 7.587 | 6.834 | 1.1102 |
| perf_batched_16x4 | 13.825 | 12.248 | 1.1287 | 13.774 | 12.216 |
1.1275 |
| perf_batched_16x16 | 39.612 | 33.382 | 1.1866 | 39.583 | 33.347 |
1.1870 |
| perf_batched_64x1 | 14.441 | 12.523 | 1.1532 | 14.476 | 12.450 |
1.1627 |
| perf_batched_64x4 | 37.621 | 29.679 | 1.2676 | 37.566 | 29.595 |
1.2693 |
| perf_batched_64x16 | 99.641 | 87.784 | 1.1351 | 99.509 | 87.697 |
1.1347 |
| perf_batched_128x1 | 23.492 | 18.615 | 1.2620 | 23.362 | 18.472 |
1.2648 |
| perf_batched_128x4 | 55.208 | 48.404 | 1.1406 | 55.111 | 48.335 |
1.1402 |
| perf_batched_128x16 | 172.051 | 159.481 | 1.0788 | 171.849 | 159.444 |
1.0778 |
| perf_batched_256x1 | 41.268 | 32.501 | 1.2697 | 41.143 | 32.364 |
1.2713 |
| perf_batched_256x4 | 100.488 | 88.287 | 1.1382 | 100.423 | 88.335 |
1.1368 |
| perf_batched_256x16 | 331.696 | 307.983 | 1.0770 | 331.735 | 308.382 |
1.0757 |
| perf_batched_512x2 | 109.908 | 92.535 | 1.1877 | 109.782 | 92.440 |
1.1876 |
| correctness_base_b2_n1 | 6.428 | 5.794 | 1.1093 | 6.454 | 5.830 |
1.1071 |
| correctness_D_head_dim | 6.392 | 5.730 | 1.1155 | 6.433 | 5.794 |
1.1104 |
| correctness_no_D | 6.415 | 5.714 | 1.1227 | 6.461 | 5.758 | 1.1221 |
| correctness_initial_bf16 | 6.444 | 5.782 | 1.1145 | 6.499 | 5.889 |
1.1037 |
| correctness_varlen_single_256 | 9.721 | 7.385 | 1.3163 | 9.853 | 7.463
| 1.3203 |
| correctness_varlen_nonaligned_z | 13.032 | 10.438 | 1.2485 | 13.083 |
10.500 | 1.2460 |
| correctness_preallocated_output | 6.377 | 5.709 | 1.1170 | 6.421 |
5.758 | 1.1152 |
| correctness_no_final_states | 6.362 | 5.720 | 1.1122 | 6.423 | 5.762 |
1.1147 |
| correctness_seq_idx_int64 | 9.814 | 9.439 | 1.0397 | 9.968 | 9.489 |
1.0504 |
| correctness_fp16_state | 6.437 | 5.814 | 1.1072 | 6.535 | 5.927 |
1.1026 |
| correctness_z_b1_n1 | 7.322 | 6.422 | 1.1401 | 7.429 | 6.531 | 1.1375
|
| perf_nemotron_h_8b_c128_projection_batched_b1x1 | 8.295 | 7.757 |
1.0693 | 8.370 | 7.815 | 1.0710 |
| perf_nemotron_h_8b_c128_projection_varlen_4x1 | 21.255 | 19.061 |
1.1151 | 21.156 | 18.984 | 1.1144 |
| nem_v1x128_bfloat16 | 10.197 | 7.769 | 1.3126 | 10.229 | 7.849 |
1.3032 |
| nem_v4x128_bfloat16 | 21.318 | 19.119 | 1.1150 | 21.232 | 19.064 |
1.1137 |
| nem_v16x128_bfloat16 | 56.643 | 48.280 | 1.1732 | 56.450 | 48.335 |
1.1679 |
| nem_v64x128_bfloat16 | 202.138 | 174.656 | 1.1574 | 201.959 | 174.579
| 1.1568 |
| nem_v160x128_bfloat16 | 496.922 | 422.804 | 1.1753 | 496.750 | 422.695
| 1.1752 |
| nem_v64_64_bfloat16 | 21.223 | 13.784 | 1.5397 | 20.525 | 13.788 |
1.4887 |
| nem_v8x64_bfloat16 | 45.907 | 28.756 | 1.5964 | 45.690 | 28.568 |
1.5993 |
| nem_v1024_bfloat16 | 32.013 | 24.201 | 1.3228 | 32.233 | 24.207 |
1.3315 |
| nem_v1024x2_bfloat16 | 54.827 | 45.134 | 1.2148 | 54.658 | 45.063 |
1.2129 |
| nem_v2048_bfloat16 | 53.624 | 42.862 | 1.2511 | 54.056 | 42.947 |
1.2587 |
| nem_v128p896_bfloat16 | 34.696 | 29.120 | 1.1915 | 34.636 | 29.210 |
1.1858 |
| nem_v96p160_bfloat16 | 24.188 | 16.562 | 1.4604 | 23.815 | 16.432 |
1.4493 |
| nem_v1000_bfloat16 | 31.937 | 24.111 | 1.3246 | 32.144 | 24.105 |
1.3335 |
| nem_v1024p100_bfloat16 | 37.123 | 32.139 | 1.1551 | 37.239 | 32.550 |
1.1441 |
| nem_b1x1024_bfloat16 | 26.763 | 24.014 | 1.1145 | 26.812 | 24.020 |
1.1162 |
| nem_b1x2048_bfloat16 | 46.997 | 42.446 | 1.1072 | 47.119 | 42.559 |
1.1071 |
| nem_b1x1000_bfloat16 | 26.675 | 23.929 | 1.1147 | 26.731 | 23.932 |
1.1170 |
| nem_v1x128_float32 | 10.372 | 8.083 | 1.2832 | 10.446 | 8.184 | 1.2764
|
| nem_v4x128_float32 | 21.740 | 19.203 | 1.1321 | 21.767 | 19.414 |
1.1212 |
| nem_v16x128_float32 | 54.718 | 47.849 | 1.1436 | 54.590 | 48.003 |
1.1372 |
| nem_v64x128_float32 | 201.263 | 162.854 | 1.2359 | 201.310 | 162.853 |
1.2361 |
| nem_v160x128_float32 | 499.190 | 391.965 | 1.2736 | 498.839 | 391.952
| 1.2727 |
| nem_v64_64_float32 | 21.735 | 13.502 | 1.6098 | 20.825 | 13.566 |
1.5351 |
| nem_v8x64_float32 | 47.041 | 27.805 | 1.6918 | 46.703 | 27.789 |
1.6806 |
| nem_v1024_float32 | 32.272 | 24.296 | 1.3283 | 32.501 | 24.287 |
1.3382 |
| nem_v1024x2_float32 | 53.519 | 45.949 | 1.1647 | 53.424 | 45.948 |
1.1627 |
| nem_v2048_float32 | 53.940 | 43.321 | 1.2451 | 54.415 | 43.383 |
1.2543 |
| nem_v128p896_float32 | 35.326 | 29.478 | 1.1984 | 35.248 | 29.485 |
1.1955 |
| nem_v96p160_float32 | 24.526 | 16.680 | 1.4704 | 24.045 | 16.544 |
1.4534 |
| nem_v1000_float32 | 32.233 | 24.237 | 1.3299 | 32.479 | 24.234 |
1.3402 |
| nem_v1024p100_float32 | 37.215 | 32.231 | 1.1546 | 37.428 | 32.965 |
1.1354 |
| nem_b1x1024_float32 | 26.664 | 24.148 | 1.1042 | 26.751 | 24.115 |
1.1093 |
| nem_b1x2048_float32 | 47.091 | 42.914 | 1.0973 | 47.189 | 42.938 |
1.0990 |
| nem_b1x1000_float32 | 26.330 | 24.087 | 1.0931 | 26.407 | 24.049 |
1.0981 |
| short_varlen_1 | 7.318 | 5.494 | 1.3320 | 7.436 | 5.598 | 1.3282 |
| short_varlen_8 | 7.355 | 5.603 | 1.3126 | 7.476 | 5.692 | 1.3134 |
| short_varlen_8_f32 | 7.957 | 5.788 | 1.3747 | 8.134 | 5.973 | 1.3618 |
| short_varlen_127 | 8.954 | 6.733 | 1.3299 | 9.183 | 6.954 | 1.3206 |
| short_varlen_64_60 | 9.962 | 7.095 | 1.4041 | 9.965 | 7.215 | 1.3812 |
| short_batched_2x50 | 10.851 | 10.091 | 1.0753 | 10.835 | 10.066 |
1.0763 |
| short_batched_1x1 | 6.482 | 5.858 | 1.1066 | 6.558 | 5.980 | 1.0966 |
| perf_batched_1x16 | 21.534 | 20.103 | 1.0712 | 21.535 | 20.061 |
1.0735 |
| perf_batched_1x64 | 35.054 | 34.043 | 1.0297 | 35.008 | 34.054 |
1.0280 |
| perf_batched_1x256 | 70.692 | 68.578 | 1.0308 | 70.811 | 68.512 |
1.0335 |
| perf_batched_4x16 | 33.013 | 32.166 | 1.0263 | 32.962 | 32.101 |
1.0268 |
| perf_batched_4x64 | 73.278 | 65.841 | 1.1130 | 73.411 | 65.729 |
1.1169 |
| cp_b1h32c16 | 32.651 | 31.581 | 1.0339 | 32.596 | 31.500 | 1.0348 |
| cp_b4h8c16 | 33.319 | 32.474 | 1.0260 | 33.264 | 32.416 | 1.0262 |

The 13 of the 93 shapes that take the new route, compared with the head
of #7869 (06d0ffda636) and measured the same way on two other nodes
(Before = #7869, After = this PR, speedups 1.07 to 1.26):

| Shape | Node | Before (us) | After (us) | Speedup |
|---|---|---:|---:|---:|
| 1 x 128 tokens, 128 heads, z, init, bf16 state | 1 | 9.889 | 8.063 |
1.2265 |
| 1 x 128 tokens, 128 heads, z, init, bf16 state | 2 | 9.560 | 7.818 |
1.2228 |
| 1 x 128 tokens, 128 heads, z, init, f32 state | 1 | 10.029 | 8.388 |
1.1956 |
| 1 x 128 tokens, 128 heads, z, init, f32 state | 2 | 9.728 | 8.128 |
1.1969 |
| 1 x 1000 tokens, 128 heads, z, init, bf16 state | 1 | 28.797 | 25.179
| 1.1437 |
| 1 x 1000 tokens, 128 heads, z, init, bf16 state | 2 | 27.907 | 24.117
| 1.1572 |
| 1 x 1000 tokens, 128 heads, z, init, f32 state | 1 | 29.134 | 25.266 |
1.1531 |
| 1 x 1000 tokens, 128 heads, z, init, f32 state | 2 | 27.916 | 24.290 |
1.1492 |
| 1 x 1024 tokens, 128 heads, z, init, bf16 state | 1 | 28.796 | 25.277
| 1.1392 |
| 1 x 1024 tokens, 128 heads, z, init, bf16 state | 2 | 27.857 | 24.217
| 1.1503 |
| 1 x 1024 tokens, 128 heads, z, init, f32 state | 1 | 29.276 | 25.327 |
1.1559 |
| 1 x 1024 tokens, 128 heads, z, init, f32 state | 2 | 28.189 | 24.347 |
1.1578 |
| 1 x 2048 tokens, 128 heads, z, init, bf16 state | 1 | 48.574 | 45.305
| 1.0721 |
| 1 x 2048 tokens, 128 heads, z, init, bf16 state | 2 | 47.329 | 42.845
| 1.1047 |
| 1 x 2048 tokens, 128 heads, z, init, f32 state | 1 | 49.345 | 45.543 |
1.0835 |
| 1 x 2048 tokens, 128 heads, z, init, f32 state | 2 | 47.834 | 43.355 |
1.1033 |
| 1 x 1 token, 8 heads, init, bf16 state | 1 | 6.788 | 5.472 | 1.2406 |
| 1 x 1 token, 8 heads, init, bf16 state | 2 | 6.857 | 5.536 | 1.2386 |
| 1 x 8 tokens, 8 heads, bf16 state | 1 | 6.798 | 5.558 | 1.2231 |
| 1 x 8 tokens, 8 heads, bf16 state | 2 | 6.819 | 5.659 | 1.2050 |
| 1 x 8 tokens, 8 heads, init, f32 state | 1 | 7.256 | 5.775 | 1.2565 |
| 1 x 8 tokens, 8 heads, init, f32 state | 2 | 7.317 | 5.877 | 1.2450 |
| 1 x 127 tokens, 8 heads, z, init, bf16 state | 1 | 8.171 | 6.516 |
1.2540 |
| 1 x 127 tokens, 8 heads, z, init, bf16 state | 2 | 8.492 | 6.815 |
1.2461 |
| 1 x 256 tokens, 8 heads, init, bf16 state | 1 | 9.199 | 7.358 | 1.2502
|
| 1 x 256 tokens, 8 heads, init, bf16 state | 2 | 9.273 | 7.425 | 1.2489
|

The other 80 of the 93 shapes run the same machine code as #7869.

The same 56 programs also ship for sm_100a and sm_103a (Blackwell). This
PR leaves their programs and routes unchanged, and the 4 new programs
and the new route exist only on sm_107a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* Added a more efficient execution path for eligible single-sequence
packed variable-length operations on supported hardware.

* **Bug Fixes**
* Improved capture-time error guidance when checkpoint outputs require
additional warm-up.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [78420fa](https://github.com/flashinfer-ai/flashinfer/commit/78420faf3092e2b9f617551e214e3eddd7dfec91)

- **作者**: eigen
- **时间**: 2026-10-31T17:58:15Z
- **提交信息**: perf(cake_lm_head_det_loss): zero-fill the global sparse dW as FP32 words (#8125)

The package `flashinfer.experimental.cake_lm_head_det_loss` has three kinds of entry: the fused cross-entropy / policy-loss entry, the log-probability entry, and the support-set entries. The support-set entries run in three modes (kl, selected = "sel", log-probability = "lp") and have sparse and dense paths. This PR changes only the support-set entries' sparse weight gradient in the global mode. dW (BF16, [V, H]) used to be zero-filled one BF16 element at a time. It is now zero-filled through its FP32 view, which writes the same +0 bits at about twice the fill rate.

The baseline is main's version of the same package. Against it, a forward + backward support call is 0.22-0.23 ms faster on each of the 17 sparse-dW rows per GPU. The ratio is 0.748-0.991 on GB300 and 0.754-0.992 on B200, and small calls gain the most in relative terms. The 4 dense-dW rows per GPU are unchanged.

Timings are the median CUPTI GPU span of one forward + backward support call with a cold L2, over 64 paired, interleaved rounds per state. In the "cooled" state the GPU idles for about one call span before each call. In the "pre-loaded" state a 2.0 ms GPU load runs before each call. Ratio = this PR / main (lower is faster), with CI95 from a paired bootstrap. Rows marked "dense (unchanged)" compute dW on the dense path, so they do not run the changed code.

### NVIDIA B200 (sm_100a, CUDA 13.4)

| shape (H=6144, V=154880) | mode | dW path | cooled: main / this PR (ms) | ratio [CI95] | pre-loaded: main / this PR (ms) | ratio [CI95] |
|---|---|---|---|---|---|---|
| real top-k supports (w1), T=16384, K≤2048 | kl | sparse, global | 0.933 / 0.704 | 0.7540 [0.7537, 0.7544] | 0.933 / 0.704 | 0.7544 [0.7542, 0.7546] |
| real top-k supports (w1), T=16384, K≤2048 | sel | sparse, global | 0.938 / 0.709 | 0.7555 [0.7553, 0.7558] | 0.938 / 0.709 | 0.7557 [0.7554, 0.7560] |
| real top-k supports (w1), T=16384, K≤2048 | lp | sparse, global | 0.935 / 0.706 | 0.7547 [0.7544, 0.7549] | 0.935 / 0.706 | 0.7548 [0.7546, 0.7552] |
| real top-k supports (w2), T=16338, K≤2048 | kl | sparse, global | 1.090 / 0.861 | 0.7894 [0.7891, 0.7898] | 1.091 / 0.861 | 0.7893 [0.7890, 0.7895] |
| independent supports, T=16231, K≤8 | kl | sparse, global | 1.281 / 1.051 | 0.8206 [0.8203, 0.8207] | 1.282 / 1.052 | 0.8204 [0.8201, 0.8207] |
| independent supports, T=16231, K≤32 | kl | sparse, global | 2.541 / 2.311 | 0.9093 [0.9092, 0.9094] | 2.542 / 2.311 | 0.9092 [0.9092, 0.9093] |
| independent supports, T=16231, K≤128 | kl | sparse, global | 7.395 / 7.163 | 0.9687 [0.9686, 0.9688] | 7.394 / 7.163 | 0.9687 [0.9686, 0.9688] |
| independent supports, T=16231, K≤512 | kl | sparse, global | 27.037 / 26.808 | 0.9915 [0.9915, 0.9916] | 27.039 / 26.813 | 0.9916 [0.9916, 0.9917] |
| independent supports, T=16231, K≤2048 | kl | dense (unchanged) | 63.175 / 63.043 | 0.9979 [0.9957, 1.0006] | 69.644 / 69.723 | 1.0011 [0.9987, 1.0029] |
| Zipf supports, T=16231, K≤8 | kl | sparse, global | 1.198 / 0.968 | 0.8080 [0.8078, 0.8081] | 1.199 / 0.970 | 0.8091 [0.8086, 0.8096] |
| Zipf supports, T=16231, K≤32 | kl | sparse, global | 2.268 / 2.037 | 0.8983 [0.8981, 0.8984] | 2.268 / 2.037 | 0.8981 [0.8979, 0.8982] |
| Zipf supports, T=16231, K≤128 | kl | sparse, global | 6.287 / 6.056 | 0.9632 [0.9631, 0.9633] | 6.288 / 6.057 | 0.9632 [0.9631, 0.9634] |
| Zipf supports, T=16231, K≤512 | kl | sparse, global | 23.145 / 22.917 | 0.9902 [0.9901, 0.9902] | 23.162 / 22.936 | 0.9902 [0.9902, 0.9903] |
| Zipf supports, T=16231, K≤2048 | kl | dense (unchanged) | 57.499 / 57.339 | 0.9972 [0.9944, 0.9997] | 63.313 / 63.538 | 1.0036 [0.9983, 1.0072] |
| shared supports, T=16231, K≤128 | kl | sparse, global | 6.603 / 6.372 | 0.9650 [0.9647, 0.9656] | 6.609 / 6.382 | 0.9657 [0.9656, 0.9658] |
| shared supports, T=16231, K≤2048 | kl | dense (unchanged) | 57.986 / 57.892 | 0.9984 [0.9968, 1.0009] | 63.974 / 63.907 | 0.9989 [0.9966, 1.0019] |
| independent supports, T=16231, K≤512 | sel | sparse, global | 26.541 / 26.315 | 0.9915 [0.9914, 0.9915] | 26.542 / 26.316 | 0.9915 [0.9915, 0.9915] |
| independent supports, T=16231, K≤512 | lp | sparse, global | 27.004 / 26.776 | 0.9916 [0.9915, 0.9916] | 27.011 / 26.785 | 0.9916 [0.9916, 0.9916] |
| independent supports, T=4096, K≤128 | kl | sparse, global | 2.450 / 2.219 | 0.9059 [0.9057, 0.9059] | 2.450 / 2.223 | 0.9075 [0.9073, 0.9076] |
| independent supports, T=4096, K≤2048 | kl | dense (unchanged) | 15.946 / 15.949 | 1.0001 [0.9997, 1.0004] | 16.244 / 16.246 | 1.0001 [0.9959, 1.0042] |
| Zipf supports, T=4096, K≤128 | kl | sparse, global | 2.138 / 1.906 | 0.8918 [0.8916, 0.8920] | 2.138 / 1.906 | 0.8917 [0.8916, 0.8920] |

### NVIDIA GB300 (sm_103a, CUDA 13.4)

| shape (H=6144, V=154880) | mode | dW path | cooled: main / this PR (ms) | ratio [CI95] | pre-loaded: main / this PR (ms) | ratio [CI95] |
|---|---|---|---|---|---|---|
| real top-k supports (w1), T=16384, K≤2048 | kl | sparse, global | 0.892 / 0.667 | 0.7478 [0.7474, 0.7481] | 0.892 / 0.668 | 0.7483 [0.7480, 0.7486] |
| real top-k supports (w1), T=16384, K≤2048 | sel | sparse, global | 0.895 / 0.670 | 0.7488 [0.7487, 0.7491] | 0.895 / 0.670 | 0.7489 [0.7485, 0.7490] |
| real top-k supports (w1), T=16384, K≤2048 | lp | sparse, global | 0.892 / 0.667 | 0.7478 [0.7475, 0.7481] | 0.892 / 0.667 | 0.7480 [0.7476, 0.7481] |
| real top-k supports (w2), T=16338, K≤2048 | kl | sparse, global | 1.049 / 0.823 | 0.7852 [0.7849, 0.7855] | 1.049 / 0.824 | 0.7856 [0.7852, 0.7858] |
| independent supports, T=16231, K≤8 | kl | sparse, global | 1.238 / 1.012 | 0.8178 [0.8176, 0.8180] | 1.238 / 1.012 | 0.8178 [0.8176, 0.8181] |
| independent supports, T=16231, K≤32 | kl | sparse, global | 2.381 / 2.155 | 0.9053 [0.9052, 0.9054] | 2.381 / 2.156 | 0.9053 [0.9052, 0.9054] |
| independent supports, T=16231, K≤128 | kl | sparse, global | 6.932 / 6.706 | 0.9674 [0.9674, 0.9675] | 6.930 / 6.705 | 0.9674 [0.9673, 0.9675] |
| independent supports, T=16231, K≤512 | kl | sparse, global | 25.325 / 25.098 | 0.9910 [0.9910, 0.9911] | 25.333 / 25.106 | 0.9910 [0.9910, 0.9910] |
| independent supports, T=16231, K≤2048 | kl | dense (unchanged) | 55.069 / 55.081 | 1.0002 [0.9997, 1.0006] | 57.086 / 57.221 | 1.0024 [0.9991, 1.0051] |
| Zipf supports, T=16231, K≤8 | kl | sparse, global | 1.151 / 0.926 | 0.8043 [0.8042, 0.8046] | 1.150 / 0.925 | 0.8039 [0.8036, 0.8042] |
| Zipf supports, T=16231, K≤32 | kl | sparse, global | 2.109 / 1.884 | 0.8930 [0.8928, 0.8932] | 2.110 / 1.884 | 0.8931 [0.8929, 0.8932] |
| Zipf supports, T=16231, K≤128 | kl | sparse, global | 5.836 / 5.610 | 0.9613 [0.9612, 0.9613] | 5.835 / 5.609 | 0.9614 [0.9613, 0.9614] |
| Zipf supports, T=16231, K≤512 | kl | sparse, global | 21.392 / 21.165 | 0.9894 [0.9893, 0.9894] | 21.407 / 21.180 | 0.9894 [0.9893, 0.9894] |
| Zipf supports, T=16231, K≤2048 | kl | dense (unchanged) | 50.555 / 50.555 | 1.0000 [0.9991, 1.0009] | 52.532 / 52.600 | 1.0013 [1.0002, 1.0021] |
| shared supports, T=16231, K≤128 | kl | sparse, global | 6.083 / 5.857 | 0.9629 [0.9628, 0.9630] | 6.083 / 5.857 | 0.9628 [0.9627, 0.9629] |
| shared supports, T=16231, K≤2048 | kl | dense (unchanged) | 51.285 / 51.274 | 0.9998 [0.9995, 1.0001] | 52.991 / 53.051 | 1.0011 [0.9998, 1.0025] |
| independent supports, T=16231, K≤512 | sel | sparse, global | 24.883 / 24.659 | 0.9910 [0.9909, 0.9911] | 24.897 / 24.669 | 0.9909 [0.9908, 0.9909] |
| independent supports, T=16231, K≤512 | lp | sparse, global | 25.311 / 25.084 | 0.9910 [0.9910, 0.9911] | 25.316 / 25.089 | 0.9910 [0.9910, 0.9911] |
| independent supports, T=4096, K≤128 | kl | sparse, global | 2.321 / 2.096 | 0.9029 [0.9028, 0.9030] | 2.321 / 2.095 | 0.9027 [0.9025, 0.9028] |
| independent supports, T=4096, K≤2048 | kl | dense (unchanged) | 14.522 / 14.521 | 1.0000 [0.9999, 1.0001] | 14.531 / 14.531 | 1.0000 [0.9997, 1.0002] |
| Zipf supports, T=4096, K≤128 | kl | sparse, global | 2.002 / 1.777 | 0.8874 [0.8872, 0.8875] | 2.003 / 1.778 | 0.8875 [0.8872, 0.8876] |

The GB300 row "Zipf supports, T=16231, K≤2048" reads 1.0013 [1.0002, 1.0021] pre-loaded, but it runs the unchanged dense path. A rerun of the four dense rows on the same node read 1.0008 [0.9991, 1.0018] (this PR vs main) and 1.0001 [0.9984, 1.0012] (main vs main) for this row and state, so the difference is within measurement noise.

This PR does not change the package's other entries: the fused cross-entropy / policy-loss entry, the log-probability entry, and the support-set dense path. The package ships for sm_100a (B200) and sm_103a (GB300).

### [785e84e](https://github.com/flashinfer-ai/flashinfer/commit/785e84e4dc01c0597138f6db6a515e761b5778f2)

- **作者**: eigen
- **时间**: 2026-10-31T17:28:19Z
- **提交信息**: fix(cake_lm_head_det_loss): per-thread hidden-count state and a layout-keyed logprob backward binding (#8126)

## Summary

This PR fixes two host-side bugs in `flashinfer.experimental.cake_lm_head_det_loss`, the deterministic chunked LM-head + loss package. The log-probability backward missed its binding cache whenever `lse` or `dlogp` moved to another block, and every thread shared three per-device module globals. The kernels are unchanged because the PR has no device source, `build.json` or JIT module table changes.

## Problems

1. **Log-probability backward binding cache misses.** `logprob_backward_binding_key` keyed `lse` and `dlogp` by `data_ptr`, along with shape, stride and dtype. Both are fresh tensors on every training step: `lse` is a forward output and `dlogp` is the incoming gradient. When the caching allocator places one of them on another block, the backward misses the binding cache. It then builds and validates a new runner and stores one more binding in the 64-entry LRU. No plan reads the addresses of `lse` or `dlogp`, and the launches re-bind both on every call. We saw this on main with B200, T=4097 with 3892 valid rows, chunk 4096, and the previous step's outputs still alive. The logprob entry missed on steps 1-2, and timed runs had 1-9 miss steps per 96 steps. Each miss step costs 0.7-3.9 ms of host time (median miss step minus median hit step, across 7 shapes).

2. **Thread race in per-device module globals.** Every thread shared three per-device objects:
   - The pinned `int32[1]` cell and the CUDA event that carry the hidden valid-row count from device to host. A second thread can call between one call's copy and its read and overwrite the count. The first call then plans its chunks on the wrong count, which gives wrong outputs or out-of-range rows.
   - The growing int32 constant 1, 2, ... used to build the compaction index. One thread creates it on its own stream, and nothing orders it against another thread's stream. A reader can see an unfilled constant, or one that was freed and reused, and so builds a wrong compaction.
   - The dW side stream and its fork event. One thread can re-record the fork event between another thread's record and wait. This breaks that thread's dW dependency.

   On main, the new two-thread tests fail, including with an illegal memory access.

## Fixes

- In both backends, `lse` and `dlogp` are now keyed by layout (shape, stride and dtype). `X` is still keyed by address because its address is a plan input (16-byte alignment check).
- The count cell and event, the constant, and the dW side stream with its fork event are now per-thread, per-device state held in `threading.local`.
- The constant is recorded with `record_stream` once per stream it is used on. The allocator keeps every recorded stream until the tensor is freed. Recording on every call cost about 1.6 us per call. Instead, each constant keeps the raw handles of the streams already recorded, and only a new stream gets recorded. A grown constant gets a new set of handles.
- `preload` now prepares the calling thread's state.
- Single-thread behavior is unchanged: the same kernels run in the same order.

Changed files, in three commits:
- `flashinfer/experimental/cake_lm_head_det_loss/cake_backend.py`
- `flashinfer/experimental/cake_lm_head_det_loss/cake_backend_opt_in.py`
- `tests/experimental/test_cake_lm_head_loss.py`
- `tests/experimental/test_cake_lm_head_det_loss_host_state.py` (new)

## Tests

The new file `tests/experimental/test_cake_lm_head_det_loss_host_state.py` has 6 tests. They cover:
- Logprob training steps hit one backward binding (T=4097 / chunk 4096 and T=1000 / chunk 256).
- Per-thread state identity.
- The constant is recorded once per stream.
- Two threads run policy forward + backward with zero-weight and ignored rows. The test forces one thread to interleave between the other thread's count copy and its read. Both results must equal the single-thread bits.
- A second thread extends the constant behind a ~1 s GPU sleep on its own stream, while the first thread counts on an idle stream. Both results must equal the single-thread bits.

In `tests/experimental/test_cake_lm_head_loss.py`, the binding-key unit test and `test_device_preload` now read the new state.

## Validation

We tested on main `96ca3d01` on B200 (sm_100a) and GB300 (sm_103a) with CUDA 13.4 and PyTorch 2.14.1. The branch is now rebased onto current main; the only change to this package in between is a CPU-only test fix (#8117).

| check | B200 | GB300 |
| --- | --- | --- |
| new host-state tests | main: fail (incl. illegal memory access); this PR: 6/6 pass | main: fail (incl. crash); this PR: 6/6 pass |
| each new two-thread test in its own process | main fails, this PR passes | main fails, this PR passes |
| outputs / logp / dX / dW bitwise vs main, 58 rows (37 representative loss/logprob rows + 21 support rows) | 58/58 identical | 58/58 identical |
| `test_cake_lm_head_loss` / `_api` / `_standalone` / `_support` | 316 passed 2 skipped / 15 / 2 / 335 on both; same failure set (none) | 317 passed 1 skipped / 15 / 2 / 335 on both; same failure set (none) |
| pre-commit (ruff check/format) | clean | clean |

## Host time

We compared main with this PR in paired, interleaved A/B runs of 48 rounds x 8 steps, with a main-vs-main control. There were 5 shapes (T/chunk): 1000/256 loss, plus 1000/256, 16172/4096, 16231/2048 and 4097/4096 logprob. On both GPUs, per-step wall time shows no detectable change on any shape, and per-step host time on B200 shows none either (all 95 % intervals include 0). On GB300, two host-time intervals exclude 0: 1000/256 loss at +0.0157 ms [+0.0102, +0.0213] and 16172/4096 logprob at +0.0135 ms [+0.0005, +0.0264]. However, the main-vs-main control on the same node also excluded 0 on the 1000/256 loss row (+0.0074 ms [+0.0018, +0.0131]). Timing the three accessors in isolation puts the per-thread state at about 0.34 us per call on B200 (71->123 ns, 127->367 ns, 71->122 ns) and 0.46 us per call on GB300 (93->174 ns, 147->438 ns, 93->178 ns). The binding-key fix removes the 0.7-3.9 ms host stall of each cache-miss step, but at these GPU-bound shapes (22-173 ms per step) it does not change the steady-state step time.

### [fe08dc5](https://github.com/flashinfer-ai/flashinfer/commit/fe08dc597e955714db9e79f4eadb66b8b28460d5)

- **作者**: eigen
- **时间**: 2026-10-31T17:12:07Z
- **提交信息**: perf(cake_deepgemm_dense_mqa): extend the single-launch FP8 Q = 1 / Q = 128 and FP4 Q = 1 chains by one KV block (#8124)

This PR follows up #7607, #7643, #7741, #7779 and #8113. FlashInfer's
Cake DeepGEMM-form MQA logits programs for Blackwell back
`flashinfer.dense_mqa` and `flashinfer.paged_mqa`. The variants are
dense FP8 with 32 or 64 heads, dense FP4 with 32 heads (including fused
metadata + logits sequences), and paged FP8. This PR changes dense FP8
with 32 heads and dense FP4 with 32 heads, on sm_100a and sm_103a. It
raises three 32-head policy bounds by 256 keys each, using the same
value on every architecture: `fused_q1_max_kv` 1048576 -> 1048832 (FP8,
Q = 1), `fused_q128_max_kv` 131072 -> 131328 (FP8, Q = 128), and
`fp4.fused_q1_max_kv` 131072 -> 131328 (FP4, Q = 1). The first KV length
past each old bound now runs on the existing single-launch chain instead
of the two-launch pair. No program is added or changed. Only the catalog
policy and its route tests change. Logits are bitwise equal on every row
of both tables (106/106 on each GPU). The baseline is the previous
version, FlashInfer main 9d55883c15d0, for the dense MQA paths. On B200,
3 of the 106 rows in the #7607/#7643 shape list run the updated route: Q
1, K 1048832 FP8 goes from 33.49 to 31.30 µs (1.0685), Q 128, K 131328
FP8 from 65.63 to 65.07 µs (1.0086), and Q 1, K 131328 FP4 from 11.42 to
6.61 µs (1.7317). On GB300, the same 3 rows go from 32.45 to 30.00 µs
(1.0817), 56.27 to 54.88 µs (1.0254), and 13.90 to 6.72 µs (2.0771).
Each updated row is faster in all 3 sessions on both GPUs. The other 103
rows run byte-identical programs in both versions. They read
0.9862–1.0078 (median 1.0000) on B200 and 0.9926–1.0125 (median 1.0000)
on GB300, which is measurement noise.

**NVIDIA B200** (sm_100a, 148 SMs), CUDA 13.4 (nvcc V13.4.92,
JIT-compiled), driver 580.82.07, torch 2.14.1+cu130. Previous version =
FlashInfer main 9d55883c15d0 (#8113) (dense MQA paths). Timing is CUPTI
GPU time per call with a cold L2. µs is the median over the 3 sessions
of each session's median. Speedup is the median over the sessions of
previous / this (> 1 = faster). Rows that launch more than one kernel
per call report the sum of kernel times. The notation is the same as in
#7643. `Q q, K k` is q queries over k keys. `prefill Q q, prefix p,
causal` is q new queries attending causally over p cached keys plus
themselves (K = p + q). "2 sequences" and "2048-query chunks" mean the
same as in #7643. "updated" means the row now runs the existing
single-launch chain instead of the two-launch pair. "same program" means
every program on the row is byte-identical to the previous version.

| shape | dtype | heads | previous µs | this PR µs | speedup | program |
|---|---|---:|---:|---:|---:|---|
| prefill Q 37, prefix 4100, causal | FP8 | 32 | 5.22 | 5.22 | 0.9971 |
same program |
| prefill Q 1024, prefix 32779, causal | FP8 | 32 | 138.98 | 138.83 |
0.9993 | same program |
| prefill Q 1, prefix 0, causal | FP8 | 64 | 3.60 | 3.60 | 1.0000 | same
program |
| prefill Q 1, prefix 4100, causal | FP8 | 64 | 3.87 | 3.87 | 1.0000 |
same program |
| prefill Q 1, prefix 32779, causal | FP8 | 64 | 5.09 | 5.09 | 1.0000 |
same program |
| prefill Q 1, prefix 131077, causal | FP8 | 64 | 7.94 | 7.94 | 1.0000 |
same program |
| prefill Q 2, prefix 0, causal | FP8 | 64 | 3.62 | 3.60 | 1.0001 | same
program |
| prefill Q 2, prefix 4100, causal | FP8 | 64 | 4.51 | 4.51 | 1.0000 |
same program |
| prefill Q 3, prefix 0, causal | FP8 | 64 | 3.70 | 3.70 | 1.0000 | same
program |
| prefill Q 3, prefix 4100, causal | FP8 | 64 | 4.48 | 4.48 | 1.0000 |
same program |
| prefill Q 7, prefix 0, causal | FP8 | 64 | 3.72 | 3.71 | 1.0022 | same
program |
| prefill Q 7, prefix 4100, causal | FP8 | 64 | 4.48 | 4.48 | 1.0000 |
same program |
| prefill Q 8, prefix 0, causal | FP8 | 64 | 3.66 | 3.65 | 1.0042 | same
program |
| prefill Q 8, prefix 4100, causal | FP8 | 64 | 4.58 | 4.58 | 1.0000 |
same program |
| prefill Q 16, prefix 0, causal | FP8 | 64 | 3.70 | 3.71 | 1.0000 |
same program |
| prefill Q 16, prefix 4100, causal | FP8 | 64 | 4.58 | 4.58 | 1.0000 |
same program |
| prefill Q 37, prefix 0, causal | FP8 | 64 | 3.76 | 3.76 | 1.0000 |
same program |
| prefill Q 37, prefix 4100, causal | FP8 | 64 | 5.66 | 5.66 | 1.0000 |
same program |
| prefill Q 37, prefix 32779, causal | FP8 | 64 | 14.29 | 14.30 | 1.0000
| same program |
| prefill Q 37, prefix 131077, causal | FP8 | 64 | 40.14 | 40.14 |
0.9996 | same program |
| prefill Q 64, prefix 0, causal | FP8 | 64 | 4.03 | 4.03 | 1.0001 |
same program |
| prefill Q 64, prefix 4100, causal | FP8 | 64 | 6.62 | 6.62 | 1.0000 |
same program |
| prefill Q 128, prefix 0, causal | FP8 | 64 | 4.06 | 4.06 | 1.0000 |
same program |
| prefill Q 128, prefix 4100, causal | FP8 | 64 | 9.28 | 9.28 | 1.0000 |
same program |
| prefill Q 128, prefix 4100, causal, 2 sequences | FP8 | 64 | 8.19 |
8.18 | 1.0020 | same program |
| prefill Q 128, prefix 32779, causal | FP8 | 64 | 34.30 | 34.30 |
1.0000 | same program |
| prefill Q 128, prefix 131077, causal | FP8 | 64 | 126.85 | 126.26 |
1.0047 | same program |
| prefill Q 129, prefix 0, causal | FP8 | 64 | 4.03 | 4.03 | 1.0000 |
same program |
| prefill Q 129, prefix 4100, causal | FP8 | 64 | 9.24 | 9.22 | 0.9983 |
same program |
| prefill Q 1023, prefix 0, causal | FP8 | 64 | 10.26 | 10.27 | 1.0000 |
same program |
| prefill Q 1023, prefix 4100, causal | FP8 | 64 | 40.37 | 40.38 |
0.9996 | same program |
| prefill Q 1024, prefix 0, causal | FP8 | 64 | 10.37 | 10.37 | 1.0000 |
same program |
| prefill Q 1024, prefix 4100, causal | FP8 | 64 | 40.42 | 40.40 |
1.0004 | same program |
| prefill Q 1024, prefix 32779, causal | FP8 | 64 | 267.33 | 266.14 |
1.0043 | same program |
| prefill Q 1024, prefix 131077, causal | FP8 | 64 | 1096.43 | 1087.93 |
1.0078 | same program |
| prefill Q 4096, prefix 0, causal | FP8 | 64 | 70.22 | 70.22 | 0.9993 |
same program |
| prefill Q 4096, prefix 4100, causal | FP8 | 64 | 203.90 | 202.46 |
1.0056 | same program |
| prefill Q 4096, prefix 32779, causal | FP8 | 64 | 1157.89 | 1151.39 |
1.0057 | same program |
| prefill Q 4096, prefix 32779, causal, 2 sequences | FP8 | 64 | 794.16
| 797.41 | 0.9969 | same program |
| prefill Q 4096, prefix 32779, causal, 2048-query chunks | FP8 | 64 |
1153.90 | 1152.43 | 1.0009 | same program |
| prefill Q 4096, prefix 131077, causal | FP8 | 64 | 4465.82 | 4466.02 |
1.0000 | same program |
| prefill Q 4096, prefix 131077, causal, 2048-query chunks | FP8 | 64 |
4467.50 | 4467.90 | 1.0000 | same program |
| prefill Q 8192, prefix 0, causal | FP8 | 64 | 282.90 | 282.75 | 1.0003
| same program |
| prefill Q 8192, prefix 4100, causal | FP8 | 64 | 558.13 | 556.34 |
1.0026 | same program |
| prefill Q 8192, prefix 32779, causal | FP8 | 64 | 2467.14 | 2501.12 |
0.9862 | same program |
| prefill Q 8192, prefix 32779, causal, 2048-query chunks | FP8 | 64 |
2473.44 | 2472.76 | 1.0003 | same program |
| prefill Q 8192, prefix 131077, causal | FP8 | 64 | 9188.80 | 9187.92 |
1.0000 | same program |
| prefill Q 8192, prefix 131077, causal, 2048-query chunks | FP8 | 64 |
9066.56 | 9064.10 | 1.0006 | same program |
| prefill Q 16231, prefix 0, causal | FP8 | 64 | 1104.41 | 1108.44 |
0.9973 | same program |
| prefill Q 16231, prefix 4100, causal | FP8 | 64 | 1646.77 | 1655.21 |
0.9992 | same program |
| prefill Q 16231, prefix 32779, causal | FP8 | 64 | 5496.39 | 5500.86 |
0.9992 | same program |
| prefill Q 16231, prefix 32779, causal, 2048-query chunks | FP8 | 64 |
5545.15 | 5549.11 | 0.9993 | same program |
| prefill Q 16231, prefix 131077, causal | FP8 | 64 | 18880.66 |
18925.27 | 0.9976 | same program |
| prefill Q 16231, prefix 131077, causal, 2048-query chunks | FP8 | 64 |
18671.09 | 18672.25 | 1.0000 | same program |
| Q 1, K 4096 | FP8 | 32 | 3.71 | 3.71 | 1.0000 | same program |
| Q 1, K 32768 | FP8 | 32 | 4.83 | 4.83 | 0.9968 | same program |
| Q 1, K 131072 | FP8 | 32 | 7.71 | 7.71 | 1.0000 | same program |
| Q 1, K 1048576 | FP8 | 32 | 31.31 | 31.36 | 0.9987 | same program |
| Q 1, K 1048832 | FP8 | 32 | 33.49 | 31.30 | 1.0685 | updated |
| Q 3, K 8192 | FP8 | 32 | 4.80 | 4.80 | 1.0000 | same program |
| Q 3, K 1048832 | FP8 | 32 | 34.46 | 34.48 | 1.0023 | same program |
| Q 16, K 2048 | FP8 | 32 | 4.58 | 4.58 | 1.0000 | same program |
| Q 16, K 4096 | FP8 | 32 | 4.67 | 4.67 | 1.0000 | same program |
| Q 16, K 32768 | FP8 | 32 | 7.83 | 7.82 | 1.0041 | same program |
| Q 16, K 131072 | FP8 | 32 | 14.88 | 14.90 | 0.9989 | same program |
| Q 16, K 1048576 | FP8 | 32 | 72.29 | 72.21 | 1.0020 | same program |
| Q 16, K 1048832 | FP8 | 32 | 72.50 | 72.54 | 0.9982 | same program |
| Q 33, K 8192 | FP8 | 32 | 5.50 | 5.50 | 1.0000 | same program |
| Q 33, K 1048832 | FP8 | 32 | 197.78 | 197.10 | 1.0006 | same program |
| Q 37, K 4137 | FP8 | 32 | 5.18 | 5.18 | 1.0000 | same program |
| Q 128, K 2048 | FP8 | 32 | 6.14 | 6.16 | 0.9974 | same program |
| Q 128, K 4096 | FP8 | 32 | 7.41 | 7.39 | 1.0022 | same program |
| Q 128, K 32768 | FP8 | 32 | 21.18 | 21.20 | 1.0007 | same program |
| Q 128, K 131072 | FP8 | 32 | 65.07 | 64.91 | 1.0007 | same program |
| Q 128, K 131328 | FP8 | 32 | 65.63 | 65.07 | 1.0086 | updated |
| Q 130, K 8192 | FP8 | 32 | 10.46 | 10.46 | 1.0000 | same program |
| Q 130, K 8448 | FP8 | 32 | 10.61 | 10.61 | 1.0015 | same program |
| Q 130, K 65792 | FP8 | 32 | 38.59 | 38.64 | 0.9988 | same program |
| Q 132, K 2048 | FP8 | 32 | 6.77 | 6.78 | 0.9976 | same program |
| Q 132, K 8448 | FP8 | 32 | 10.51 | 10.53 | 0.9985 | same program |
| Q 132, K 65792 | FP8 | 32 | 38.82 | 38.88 | 0.9988 | same program |
| Q 1024, K 33803 | FP8 | 32 | 141.12 | 141.02 | 1.0001 | same program |
| Q 2052, K 2048 | FP8 | 32 | 23.82 | 23.81 | 1.0007 | same program |
| Q 2052, K 8448 | FP8 | 32 | 70.13 | 70.04 | 1.0013 | same program |
| Q 2053, K 2048 | FP8 | 32 | 24.16 | 24.18 | 0.9993 | same program |
| Q 2053, K 8448 | FP8 | 32 | 70.69 | 70.70 | 0.9998 | same program |
| Q 1, K 4096 | FP4 | 32 | 3.97 | 3.97 | 1.0000 | same program |
| Q 1, K 32768 | FP4 | 32 | 4.67 | 4.67 | 0.9967 | same program |
| Q 1, K 131072 | FP4 | 32 | 6.35 | 6.37 | 0.9976 | same program |
| Q 1, K 131328 | FP4 | 32 | 11.42 | 6.61 | 1.7317 | updated |
| Q 7, K 2048 | FP4 | 32 | 4.74 | 4.75 | 1.0000 | same program |
| Q 16, K 4096 | FP4 | 32 | 5.31 | 5.30 | 1.0029 | same program |
| Q 16, K 32768 | FP4 | 32 | 7.36 | 7.34 | 1.0000 | same program |
| Q 16, K 131072 | FP4 | 32 | 13.66 | 13.65 | 1.0000 | same program |
| Q 16, K 1048576 | FP4 | 32 | 62.94 | 62.98 | 0.9995 | same program |
| Q 16, K 1048832 | FP4 | 32 | 66.48 | 66.32 | 1.0017 | same program |
| Q 33, K 8192 | FP4 | 32 | 5.97 | 5.95 | 1.0026 | same program |
| Q 33, K 1048832 | FP4 | 32 | 139.87 | 139.87 | 0.9999 | same program |
| Q 128, K 4096 | FP4 | 32 | 6.86 | 6.86 | 1.0001 | same program |
| Q 128, K 32768 | FP4 | 32 | 19.65 | 19.65 | 1.0000 | same program |
| Q 128, K 131072 | FP4 | 32 | 61.46 | 61.41 | 1.0005 | same program |
| Q 130, K 65536 | FP4 | 32 | 35.79 | 35.81 | 0.9991 | same program |
| Q 130, K 65792 | FP4 | 32 | 38.06 | 38.06 | 1.0017 | same program |
| Q 1024, K 2048 | FP4 | 32 | 14.18 | 14.22 | 0.9955 | same program |
| Q 2052, K 2048 | FP4 | 32 | 24.08 | 24.08 | 1.0013 | same program |
| Q 2052, K 65792 | FP4 | 32 | 476.37 | 476.78 | 1.0014 | same program |

**NVIDIA GB300** (sm_103a, 152 SMs), CUDA 13.4 (nvcc V13.4.92,
JIT-compiled), driver 580.159.03, torch 2.14.1+cu130. Previous version =
FlashInfer main 9d55883c15d0 (#8113) (dense MQA paths). Timing, notation
and the "updated" / "same program" labels are the same as in the B200
table.

| shape | dtype | heads | previous µs | this PR µs | speedup | program |
|---|---|---:|---:|---:|---:|---|
| prefill Q 37, prefix 4100, causal | FP8 | 32 | 5.34 | 5.34 | 1.0000 |
same program |
| prefill Q 1024, prefix 32779, causal | FP8 | 32 | 107.97 | 108.06 |
0.9997 | same program |
| prefill Q 1, prefix 0, causal | FP8 | 64 | 3.97 | 3.95 | 1.0040 | same
program |
| prefill Q 1, prefix 4100, causal | FP8 | 64 | 4.00 | 4.00 | 1.0000 |
same program |
| prefill Q 1, prefix 32779, causal | FP8 | 64 | 4.93 | 4.96 | 1.0000 |
same program |
| prefill Q 1, prefix 131077, causal | FP8 | 64 | 7.74 | 7.74 | 1.0000 |
same program |
| prefill Q 2, prefix 0, causal | FP8 | 64 | 3.98 | 3.98 | 1.0000 | same
program |
| prefill Q 2, prefix 4100, causal | FP8 | 64 | 4.58 | 4.58 | 1.0000 |
same program |
| prefill Q 3, prefix 0, causal | FP8 | 64 | 3.71 | 3.71 | 1.0000 | same
program |
| prefill Q 3, prefix 4100, causal | FP8 | 64 | 4.35 | 4.35 | 1.0000 |
same program |
| prefill Q 7, prefix 0, causal | FP8 | 64 | 3.81 | 3.81 | 1.0000 | same
program |
| prefill Q 7, prefix 4100, causal | FP8 | 64 | 4.37 | 4.35 | 1.0000 |
same program |
| prefill Q 8, prefix 0, causal | FP8 | 64 | 3.74 | 3.74 | 1.0000 | same
program |
| prefill Q 8, prefix 4100, causal | FP8 | 64 | 4.38 | 4.38 | 1.0000 |
same program |
| prefill Q 16, prefix 0, causal | FP8 | 64 | 3.74 | 3.74 | 1.0000 |
same program |
| prefill Q 16, prefix 4100, causal | FP8 | 64 | 4.42 | 4.42 | 1.0000 |
same program |
| prefill Q 37, prefix 0, causal | FP8 | 64 | 3.74 | 3.78 | 0.9958 |
same program |
| prefill Q 37, prefix 4100, causal | FP8 | 64 | 5.34 | 5.34 | 1.0000 |
same program |
| prefill Q 37, prefix 32779, causal | FP8 | 64 | 12.54 | 12.54 | 1.0000
| same program |
| prefill Q 37, prefix 131077, causal | FP8 | 64 | 33.87 | 33.86 |
1.0000 | same program |
| prefill Q 64, prefix 0, causal | FP8 | 64 | 3.81 | 3.81 | 1.0000 |
same program |
| prefill Q 64, prefix 4100, causal | FP8 | 64 | 6.05 | 6.05 | 1.0000 |
same program |
| prefill Q 128, prefix 0, causal | FP8 | 64 | 3.92 | 3.92 | 1.0000 |
same program |
| prefill Q 128, prefix 4100, causal | FP8 | 64 | 8.51 | 8.51 | 1.0000 |
same program |
| prefill Q 128, prefix 4100, causal, 2 sequences | FP8 | 64 | 7.44 |
7.46 | 1.0000 | same program |
| prefill Q 128, prefix 32779, causal | FP8 | 64 | 30.34 | 30.34 |
0.9995 | same program |
| prefill Q 128, prefix 131077, causal | FP8 | 64 | 103.07 | 103.15 |
0.9997 | same program |
| prefill Q 129, prefix 0, causal | FP8 | 64 | 3.89 | 3.90 | 1.0000 |
same program |
| prefill Q 129, prefix 4100, causal | FP8 | 64 | 8.64 | 8.62 | 1.0019 |
same program |
| prefill Q 1023, prefix 0, causal | FP8 | 64 | 9.52 | 9.52 | 1.0000 |
same program |
| prefill Q 1023, prefix 4100, causal | FP8 | 64 | 35.57 | 35.57 |
1.0000 | same program |
| prefill Q 1024, prefix 0, causal | FP8 | 64 | 9.57 | 9.57 | 1.0017 |
same program |
| prefill Q 1024, prefix 4100, causal | FP8 | 64 | 35.65 | 35.62 |
1.0000 | same program |
| prefill Q 1024, prefix 32779, causal | FP8 | 64 | 206.75 | 206.76 |
0.9988 | same program |
| prefill Q 1024, prefix 131077, causal | FP8 | 64 | 828.00 | 829.92 |
0.9985 | same program |
| prefill Q 4096, prefix 0, causal | FP8 | 64 | 61.54 | 61.55 | 1.0000 |
same program |
| prefill Q 4096, prefix 4100, causal | FP8 | 64 | 156.90 | 156.83 |
1.0005 | same program |
| prefill Q 4096, prefix 32779, causal | FP8 | 64 | 869.06 | 868.02 |
1.0012 | same program |
| prefill Q 4096, prefix 32779, causal, 2 sequences | FP8 | 64 | 576.91
| 577.61 | 1.0004 | same program |
| prefill Q 4096, prefix 32779, causal, 2048-query chunks | FP8 | 64 |
869.05 | 871.71 | 0.9962 | same program |
| prefill Q 4096, prefix 131077, causal | FP8 | 64 | 3504.38 | 3517.44 |
0.9963 | same program |
| prefill Q 4096, prefix 131077, causal, 2048-query chunks | FP8 | 64 |
3525.80 | 3467.26 | 1.0125 | same program |
| prefill Q 8192, prefix 0, causal | FP8 | 64 | 211.95 | 212.38 | 0.9984
| same program |
| prefill Q 8192, prefix 4100, causal | FP8 | 64 | 410.79 | 410.98 |
1.0056 | same program |
| prefill Q 8192, prefix 32779, causal | FP8 | 64 | 1888.68 | 1892.53 |
0.9967 | same program |
| prefill Q 8192, prefix 32779, causal, 2048-query chunks | FP8 | 64 |
1901.34 | 1891.64 | 0.9994 | same program |
| prefill Q 8192, prefix 131077, causal | FP8 | 64 | 7162.82 | 7162.21 |
1.0001 | same program |
| prefill Q 8192, prefix 131077, causal, 2048-query chunks | FP8 | 64 |
7263.99 | 7267.31 | 0.9995 | same program |
| prefill Q 16231, prefix 0, causal | FP8 | 64 | 829.44 | 828.59 |
1.0008 | same program |
| prefill Q 16231, prefix 4100, causal | FP8 | 64 | 1238.63 | 1243.47 |
0.9947 | same program |
| prefill Q 16231, prefix 32779, causal | FP8 | 64 | 4267.74 | 4268.86 |
1.0007 | same program |
| prefill Q 16231, prefix 32779, causal, 2048-query chunks | FP8 | 64 |
4323.13 | 4314.24 | 1.0022 | same program |
| prefill Q 16231, prefix 131077, causal | FP8 | 64 | 14709.21 |
14710.78 | 1.0001 | same program |
| prefill Q 16231, prefix 131077, causal, 2048-query chunks | FP8 | 64 |
14879.64 | 14913.46 | 1.0005 | same program |
| Q 1, K 4096 | FP8 | 32 | 3.81 | 3.82 | 0.9958 | same program |
| Q 1, K 32768 | FP8 | 32 | 4.64 | 4.64 | 1.0000 | same program |
| Q 1, K 131072 | FP8 | 32 | 7.44 | 7.42 | 1.0022 | same program |
| Q 1, K 1048576 | FP8 | 32 | 30.11 | 30.11 | 1.0000 | same program |
| Q 1, K 1048832 | FP8 | 32 | 32.45 | 30.00 | 1.0817 | updated |
| Q 3, K 8192 | FP8 | 32 | 4.70 | 4.70 | 1.0000 | same program |
| Q 3, K 1048832 | FP8 | 32 | 33.58 | 33.60 | 1.0010 | same program |
| Q 16, K 2048 | FP8 | 32 | 4.70 | 4.67 | 1.0000 | same program |
| Q 16, K 4096 | FP8 | 32 | 4.77 | 4.77 | 1.0000 | same program |
| Q 16, K 32768 | FP8 | 32 | 7.25 | 7.17 | 1.0112 | same program |
| Q 16, K 131072 | FP8 | 32 | 13.22 | 13.25 | 1.0000 | same program |
| Q 16, K 1048576 | FP8 | 32 | 58.62 | 58.66 | 1.0003 | same program |
| Q 16, K 1048832 | FP8 | 32 | 59.66 | 59.63 | 1.0005 | same program |
| Q 33, K 8192 | FP8 | 32 | 5.41 | 5.41 | 1.0000 | same program |
| Q 33, K 1048832 | FP8 | 32 | 179.38 | 179.42 | 0.9998 | same program |
| Q 37, K 4137 | FP8 | 32 | 5.33 | 5.33 | 1.0000 | same program |
| Q 128, K 2048 | FP8 | 32 | 5.87 | 5.87 | 1.0000 | same program |
| Q 128, K 4096 | FP8 | 32 | 7.01 | 7.01 | 1.0000 | same program |
| Q 128, K 32768 | FP8 | 32 | 18.21 | 18.21 | 1.0000 | same program |
| Q 128, K 131072 | FP8 | 32 | 53.62 | 53.58 | 1.0006 | same program |
| Q 128, K 131328 | FP8 | 32 | 56.27 | 54.88 | 1.0254 | updated |
| Q 130, K 8192 | FP8 | 32 | 9.44 | 9.44 | 0.9999 | same program |
| Q 130, K 8448 | FP8 | 32 | 9.73 | 9.73 | 1.0000 | same program |
| Q 130, K 65792 | FP8 | 32 | 33.46 | 33.44 | 1.0000 | same program |
| Q 132, K 2048 | FP8 | 32 | 6.46 | 6.46 | 1.0000 | same program |
| Q 132, K 8448 | FP8 | 32 | 9.66 | 9.65 | 1.0001 | same program |
| Q 132, K 65792 | FP8 | 32 | 33.58 | 33.38 | 1.0115 | same program |
| Q 1024, K 33803 | FP8 | 32 | 109.97 | 109.97 | 1.0004 | same program |
| Q 2052, K 2048 | FP8 | 32 | 20.80 | 20.80 | 1.0000 | same program |
| Q 2052, K 8448 | FP8 | 32 | 60.86 | 60.85 | 1.0010 | same program |
| Q 2053, K 2048 | FP8 | 32 | 21.31 | 21.30 | 1.0008 | same program |
| Q 2053, K 8448 | FP8 | 32 | 61.50 | 61.50 | 1.0003 | same program |
| Q 1, K 4096 | FP4 | 32 | 3.84 | 3.84 | 1.0000 | same program |
| Q 1, K 32768 | FP4 | 32 | 4.51 | 4.54 | 0.9930 | same program |
| Q 1, K 131072 | FP4 | 32 | 6.38 | 6.40 | 0.9975 | same program |
| Q 1, K 131328 | FP4 | 32 | 13.90 | 6.72 | 2.0771 | updated |
| Q 7, K 2048 | FP4 | 32 | 4.67 | 4.67 | 1.0000 | same program |
| Q 16, K 4096 | FP4 | 32 | 4.85 | 4.85 | 1.0000 | same program |
| Q 16, K 32768 | FP4 | 32 | 6.64 | 6.66 | 0.9976 | same program |
| Q 16, K 131072 | FP4 | 32 | 12.03 | 12.05 | 1.0007 | same program |
| Q 16, K 1048576 | FP4 | 32 | 54.34 | 54.37 | 1.0000 | same program |
| Q 16, K 1048832 | FP4 | 32 | 60.77 | 60.62 | 1.0013 | same program |
| Q 33, K 8192 | FP4 | 32 | 5.54 | 5.54 | 1.0000 | same program |
| Q 33, K 1048832 | FP4 | 32 | 125.15 | 125.09 | 1.0005 | same program |
| Q 128, K 4096 | FP4 | 32 | 6.38 | 6.40 | 1.0000 | same program |
| Q 128, K 32768 | FP4 | 32 | 17.04 | 17.04 | 1.0009 | same program |
| Q 128, K 131072 | FP4 | 32 | 52.94 | 52.96 | 1.0003 | same program |
| Q 130, K 65536 | FP4 | 32 | 30.61 | 30.61 | 1.0000 | same program |
| Q 130, K 65792 | FP4 | 32 | 36.42 | 36.48 | 0.9961 | same program |
| Q 1024, K 2048 | FP4 | 32 | 14.00 | 14.08 | 0.9954 | same program |
| Q 2052, K 2048 | FP4 | 32 | 21.54 | 21.76 | 0.9926 | same program |
| Q 2052, K 65792 | FP4 | 32 | 397.38 | 397.43 | 0.9998 | same program |

The family's other Cake variants (dense FP8 with 32 or 64 heads, dense
FP4 with 32 heads including fused metadata + logits sequences, and paged
FP8) ship on sm_100a and sm_103a only.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* FP4 fused-query processing now supports key/value lengths up to
131,328 for the affected query sizes, and up to 1,048,832 for the longer
Q1 route.
* **Bug Fixes**
* Route-selection coverage now includes additional boundary lengths for
FP4 and FP8, including cases that use two-launch routes beyond
fused-route limits.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery Huang <averyh@nvidia.com>

### [36bebfb](https://github.com/flashinfer-ai/flashinfer/commit/36bebfbdb9834ff508efef1e0649c08a607597d9)

- **作者**: eigen
- **时间**: 2026-10-31T16:28:31Z
- **提交信息**: perf(cake_gdn_det_train): faster deterministic GDN chunked backward on long packs and HV = 3H (#8121)

This PR speeds up the backward pass of FlashInfer's deterministic Gated
DeltaNet chunked training kernel. The kernel runs packed,
variable-length training (forward and backward) on one GPU, and its
outputs and gradients are bitwise reproducible. The kernel ships FP32
and BF16 beta/dbeta forms and key/value head groups HV = H, 2H and 3H,
and it covers sm_100a (B200), sm_103a (GB300) and sm_107a (R200). Within
that set, this PR changes the backward path only:

- **HV = 3H:** a fused tail running in one three-CTA cluster kernel.
- **HV = 2H:** a faster tail.
- **Adjoint pre-scan:** it now computes the local value gradient itself,
which removes one launch on split plans.

The forward kernels are unchanged.

The baseline is the previous version of this kernel on current
FlashInfer main. Compared with that baseline:

- **GB300:** all 15 shapes are faster, at 0.71x-0.98x of the previous
time.
- **R200:** all 15 shapes are faster, at 0.73x-0.97x.
- **B200:** 13 of 15 shapes are faster, at 0.73x-0.98x, and 2 are within
noise.

The largest gains are on long packs, up to about 1.4x faster.

The metric is forward+backward latency per training step in ms, measured
as paired, interleaved runs. The ratio is new/previous with a 95%
bootstrap CI, so lower is faster. Shape
`rNN_<sequences>x<length>_h<heads>` is a pack of that many sequences of
that length with that many heads. A `real` shape uses a measured
real-workload length mix; for example, `real3x4.25k` is 3 sequences
averaging 4.25k tokens. The `p7074_*` shapes come from FlashInfer issue
#7074; for example, `241817x6` is 6 sequences with 241817 tokens in
total.

**B200 (sm_100a), CUDA 13.4**

| shape | previous ms | new ms | ratio new/previous [95% CI] |
|---|---|---|---|
| r01_4x4096_h8 | 0.6533 | 0.6375 | 0.9757 [0.9738, 0.9847] |
| r02_real3x4.25k_h8 | 0.7225 | 0.7524 | 1.0414 [0.9857, 1.1112] |
| r03_8x4096_h8 | 1.0803 | 1.0548 | 0.9764 [0.9763, 0.9773] |
| r04_real7x4.3k_h8 | 1.3098 | 1.1095 | 0.8471 [0.8466, 0.8474] |
| r05_16x4096_h8 | 2.1104 | 2.0633 | 0.9777 [0.9755, 0.9801] |
| r06_real15x4.3k_h8 | 2.1289 | 2.0766 | 0.9754 [0.9729, 0.9772] |
| r07_1x16384_h8 | 0.7124 | 0.6794 | 0.9536 [0.9204, 0.9716] |
| r08_4x4096_h16 | 1.0884 | 1.0619 | 0.9756 [0.9756, 0.9762] |
| r09_16x4096_h16 | 4.2645 | 4.1893 | 0.9824 [0.9770, 0.9899] |
| r10_1x16384_h16 | 1.3414 | 1.2320 | 0.9185 [0.9184, 0.9193] |
| p7074_64x4096_h2 | 3.9523 | 3.2456 | 0.8212 [0.8201, 0.8226] |
| p7074_A16_32768x3_h16 | 4.0161 | 3.2820 | 0.8172 [0.8154, 0.8190] |
| p7074_P1_241817x6_h2 | 4.3400 | 3.1527 | 0.7264 [0.7248, 0.7280] |
| p7074_P3_259174x2_h2 | 4.5984 | 3.3791 | 0.7349 [0.7338, 0.7365] |
| p7074_issue_261987x3_h2 | 4.6380 | 3.4120 | 0.7357 [0.7341, 0.7375] |

**GB300 (sm_103a), CUDA 13.4**

| shape | previous ms | new ms | ratio new/previous [95% CI] |
|---|---|---|---|
| r01_4x4096_h8 | 0.6071 | 0.5897 | 0.9714 [0.9705, 0.9716] |
| r02_real3x4.25k_h8 | 0.5642 | 0.4844 | 0.8585 [0.8576, 0.8599] |
| r03_8x4096_h8 | 1.0068 | 0.9810 | 0.9743 [0.9742, 0.9745] |
| r04_real7x4.3k_h8 | 1.2016 | 0.9897 | 0.8236 [0.8226, 0.8243] |
| r05_16x4096_h8 | 1.9389 | 1.8895 | 0.9745 [0.9729, 0.9757] |
| r06_real15x4.3k_h8 | 1.9691 | 1.9193 | 0.9747 [0.9745, 0.9750] |
| r07_1x16384_h8 | 0.6637 | 0.6072 | 0.9149 [0.9139, 0.9156] |
| r08_4x4096_h16 | 1.0128 | 0.9850 | 0.9726 [0.9722, 0.9727] |
| r09_16x4096_h16 | 3.8060 | 3.7137 | 0.9758 [0.9753, 0.9761] |
| r10_1x16384_h16 | 1.2457 | 1.0585 | 0.8498 [0.8494, 0.8501] |
| p7074_64x4096_h2 | 3.6408 | 2.9411 | 0.8078 [0.8077, 0.8081] |
| p7074_A16_32768x3_h16 | 3.6997 | 2.9695 | 0.8026 [0.8023, 0.8032] |
| p7074_P1_241817x6_h2 | 4.0296 | 2.8673 | 0.7116 [0.7113, 0.7119] |
| p7074_P3_259174x2_h2 | 4.2079 | 3.0410 | 0.7227 [0.7226, 0.7228] |
| p7074_issue_261987x3_h2 | 4.2775 | 3.1011 | 0.7250 [0.7248, 0.7252] |

**R200 (sm_107a), CUDA 13.4**

| shape | previous ms | new ms | ratio new/previous [95% CI] |
|---|---|---|---|
| r01_4x4096_h8 | 0.4499 | 0.3764 | 0.8367 [0.8356, 0.8381] |
| r02_real3x4.25k_h8 | 0.3737 | 0.3179 | 0.8505 [0.8483, 0.8527] |
| r03_8x4096_h8 | 0.8478 | 0.7043 | 0.8307 [0.8300, 0.8312] |
| r04_real7x4.3k_h8 | 0.7934 | 0.6597 | 0.8314 [0.8297, 0.8330] |
| r05_16x4096_h8 | 1.3056 | 1.2584 | 0.9638 [0.9633, 0.9644] |
| r06_real15x4.3k_h8 | 1.3552 | 1.3082 | 0.9653 [0.9648, 0.9659] |
| r07_1x16384_h8 | 0.4593 | 0.4153 | 0.9041 [0.9033, 0.9051] |
| r08_4x4096_h16 | 0.8627 | 0.7102 | 0.8232 [0.8224, 0.8238] |
| r09_16x4096_h16 | 2.5873 | 2.4737 | 0.9561 [0.9545, 0.9576] |
| r10_1x16384_h16 | 0.8189 | 0.7288 | 0.8900 [0.8890, 0.8912] |
| p7074_64x4096_h2 | 2.1788 | 1.8342 | 0.8419 [0.8414, 0.8422] |
| p7074_A16_32768x3_h16 | 2.6792 | 1.9847 | 0.7408 [0.7405, 0.7410] |
| p7074_P1_241817x6_h2 | 2.4503 | 1.7884 | 0.7299 [0.7293, 0.7306] |
| p7074_P3_259174x2_h2 | 2.5439 | 1.8820 | 0.7398 [0.7396, 0.7400] |
| p7074_issue_261987x3_h2 | 2.5628 | 1.8981 | 0.7406 [0.7397, 0.7415] |


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added cost-based selection for a split adjoint scan route, with
controls to force or disable it.
* Added fused backward processing for groups of three value heads, with
a compatible fallback.
  * Exported a pricing helper for estimating scan-route costs.

* **Bug Fixes**
* Improved handling of gradients and segment states in training
workflows, including split scans and varied input layouts.

* **Documentation**
* Updated guidance on scan-route selection, fused tails, and route pins.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [6bb0973](https://github.com/flashinfer-ai/flashinfer/commit/6bb09734fe3e3a1b65f70d4b6ee10422064e6aa4)

- **作者**: eigen
- **时间**: 2026-10-31T16:26:28Z
- **提交信息**: perf(cake_kimi_k3_attn_res): retune dense routes on B200, B300 and GB300 (#8120)

This PR changes routes of the Cake AttnRes operator,
`flashinfer.experimental.cake_kimi_k3_attn_res`, on sm_100a and sm_103a.
It is exposed as `flashinfer.kimi_k3_attn_res.prepare_kimi_k3_attn_res`
and `kimi_k3_attn_res`. The operator runs residual add, an optional
snapshot write, K+1 candidate scoring, softmax, mix and output RMSNorm
in one launch. It takes BF16 inputs with hidden size 7168 and K in [0,
8]. It has one data type, one layout and two fused forms: dense and
snapshot write. The package keeps the shared-launcher, tabular-registry
layout of PR #7792. Among the measured shapes, this PR changes the
routes of 9 dense shapes on B300, 8 on GB300 and 16 on B200, at both PDL
modes.

- **Fast-math small-M programs:** on B200, K 0 at M 6, 7, 12, 24, 48,
64, 96, 128 and 256 moves from `small_m_direct:k0` to the fast-math
`small_m_direct:k0_fm` program. On B300, M 128 K 3 moves from
`small_m_direct:k3` to `small_m_direct:k3_fm`.
- **384-thread pair programs:** these use the pair layout of PRs #7540
and #7737. `cr232` programs have 232-register consumers, and `cr200_pk1`
programs have 200-register parked-accumulator consumers.
- B300: M 256 K 5 (`native_k5` to `pair:k5_nc2_pbf16a_fm_cr232`), M 256
K 6 (`persistent:k6_nc4_d2_f011000000000000_fm` to
`pair:k6_nc2_pbf16a_fm_cr200_pk1`), M 256 K 8 (`native_k8` to
`pair:k8_nc2_pbf16a_fm_cr200_pk1`), M 768 K 4
(`persistent:k4_nc5_d2_f110000000000000_fm` to
`pair:k4_nc2_pbf16a_fm_cr232`), M 768 K 5 (`native_k5` to
`pair:k5_nc2_pbf16a_fm_cr232`) and M 768 K 6
(`persistent:k6_nc4_d2_f111000000000000_fm` to
`pair:k6_nc2_pbf16a_fm_cr200_pk1`).
- GB300: the same six cells and programs as B300, except that M 768 K 4
moves from `persistent:k4_nc5_d2_f101000000000000_fm` to
`pair:k4_nc2_pbf16a_fm_cr232`.
- B200: M 256 K 6 (`persistent:k6_nc4_d2_f111000000000000_fm` to
`pair:k6_nc2_pbf16a_fm_cr200_pk1`), M 256 K 8 (`native_k8` to
`pair:k8_nc2_pbf16a_fm_cr232`), M 768 K 4
(`persistent:k4_nc3_d2_f110000000000000_fm` to
`pair:k4_nc2_pbf16a_fm_cr232`) and M 768 K 5 (`native_k5` to
`pair:k5_nc2_pbf16a_fm_cr232`).
- **Persistent programs (M 256, K 2):** this cell moves from the small-M
program `small_m_direct:k2_fm` to persistent programs. B300 and GB300
use `persistent:k2_nc3_d1_f101000000000000_fm_cta2` and B200 uses
`persistent:k2_nc2_d2_f111010000000000_fm`.
- **Packed-register-carry programs (new):** three new `_rcp` builds of
existing persistent programs have no local-memory spills.
- B300 and GB300 M 1024 K 5 move from
`persistent:k5_nc4_d3_f001000000000000_fm_crheld` to the sm_103a
`persistent:k5_nc4_d3_f001000000000000_fm_crheld_rcp`.
- B200 M 512 K 5 moves from `persistent:k5_nc4_d2_f111000000000000` to
the sm_100a `persistent:k5_nc4_d2_f111000000000000_rcp`.
- B200 M 1536 K 4 moves from `persistent:k4_nc3_d3_f110000000000000_fm`
to the sm_100a `persistent:k4_nc3_d3_f110000000000000_fm_rcp`.

The program set goes from 187 programs (220 libraries: 100 sm_100a, 120
sm_103a) to 186 programs (218 libraries: 101 sm_100a, 117 sm_103a). The
PR adds 3 programs in 3 libraries, which are the three `_rcp` programs
above. It removes 4 programs in 4 libraries because no route uses them
any more. It also drops the sm_103a library of the native K 5 program,
which stays on sm_100a. One persistent K 5 program for sm_103a now
compiles its own kernel source instead of sharing the source of a
removed program, and its SASS is unchanged.

The baseline is the previous Cake version of this operator on current
main, which includes PR #7737 and the restructure of PR #7792. All
measured changed cells are faster than the previous version at both PDL
modes. The speedup is 1.2 % to 12.0 % on B300 (ratios 1.0118 to 1.1205),
1.6 % to 12.5 % on GB300 (ratios 1.0160 to 1.1248) and 1.1 % to 20.6 %
on B200 (ratios 1.0105 to 1.2061). The tables below list both latencies
and the ratio previous / new for each cell.

The other 215 program/library pairs have SASS identical to the previous
version. For shapes not in the tables below, see the timings in PRs
#6980, #7014, #7338, #7374, #7411, #7453, #7540 and #7737.

NVIDIA B300 SXM6 AC (sm_103a, 148 SMs), driver 580.126.09, CUDA 13.4.92,
torch 2.14.1+cu130.
| Shape | Previous µs (PDL off) | New µs (PDL off) | Ratio | Previous µs
(PDL on) | New µs (PDL on) | Ratio |
|---|---|---|---|---|---|---|
| M 128, K 3 (dense) | 5.696 | 5.632 | 1.0133 | 5.727 | 5.632 | 1.0151 |
| M 256, K 2 (dense) | 8.625 | 7.712 | 1.1183 | 8.640 | 7.712 | 1.1205 |
| M 256, K 5 (dense) | 10.144 | 10.016 | 1.0138 | 10.144 | 10.016 |
1.0118 |
| M 256, K 6 (dense) | 10.848 | 10.656 | 1.0180 | 10.848 | 10.655 |
1.0190 |
| M 256, K 8 (dense) | 12.544 | 12.224 | 1.0258 | 12.513 | 12.208 |
1.0258 |
| M 768, K 4 (dense) | 20.608 | 19.200 | 1.0739 | 20.608 | 19.168 |
1.0745 |
| M 768, K 5 (dense) | 22.112 | 21.632 | 1.0232 | 22.144 | 21.600 |
1.0247 |
| M 768, K 6 (dense) | 24.288 | 23.137 | 1.0493 | 24.320 | 23.168 |
1.0497 |
| M 1024, K 5 (dense) | 26.353 | 25.952 | 1.0158 | 26.400 | 25.952 |
1.0165 |

NVIDIA GB300 (sm_103a, 152 SMs), driver 580.159.03, CUDA 13.4.92, torch
2.14.1+cu130.
| Shape | Previous µs (PDL off) | New µs (PDL off) | Ratio | Previous µs
(PDL on) | New µs (PDL on) | Ratio |
|---|---|---|---|---|---|---|
| M 256, K 2 (dense) | 8.512 | 7.552 | 1.1248 | 8.480 | 7.552 | 1.1227 |
| M 256, K 5 (dense) | 10.016 | 9.728 | 1.0296 | 10.016 | 9.728 | 1.0285
|
| M 256, K 6 (dense) | 10.752 | 10.400 | 1.0339 | 10.752 | 10.368 |
1.0349 |
| M 256, K 8 (dense) | 12.320 | 11.840 | 1.0396 | 12.288 | 11.840 |
1.0383 |
| M 768, K 4 (dense) | 19.584 | 18.529 | 1.0563 | 19.569 | 18.560 |
1.0532 |
| M 768, K 5 (dense) | 21.312 | 20.768 | 1.0267 | 21.344 | 20.704 |
1.0304 |
| M 768, K 6 (dense) | 23.488 | 22.368 | 1.0498 | 23.488 | 22.321 |
1.0518 |
| M 1024, K 5 (dense) | 25.392 | 24.992 | 1.0160 | 25.472 | 25.024 |
1.0170 |

NVIDIA B200 (sm_100a, 148 SMs), driver 580.82.07, CUDA 13.4.92, torch
2.14.1+cu130.
| Shape | Previous µs (PDL off) | New µs (PDL off) | Ratio | Previous µs
(PDL on) | New µs (PDL on) | Ratio |
|---|---|---|---|---|---|---|
| M 6, K 0 (dense) | 2.944 | 2.912 | 1.0110 | 2.944 | 2.912 | 1.0110 |
| M 7, K 0 (dense) | 3.007 | 2.912 | 1.0292 | 3.007 | 2.912 | 1.0326 |
| M 12, K 0 (dense) | 2.976 | 2.944 | 1.0145 | 3.008 | 2.944 | 1.0252 |
| M 24, K 0 (dense) | 3.072 | 3.008 | 1.0212 | 3.072 | 3.008 | 1.0213 |
| M 48, K 0 (dense) | 3.169 | 3.136 | 1.0139 | 3.168 | 3.135 | 1.0105 |
| M 64, K 0 (dense) | 3.296 | 3.232 | 1.0198 | 3.296 | 3.232 | 1.0196 |
| M 96, K 0 (dense) | 3.488 | 3.424 | 1.0187 | 3.488 | 3.424 | 1.0187 |
| M 128, K 0 (dense) | 3.776 | 3.711 | 1.0174 | 3.776 | 3.711 | 1.0203 |
| M 256, K 0 (dense) | 4.800 | 4.736 | 1.0135 | 4.800 | 4.736 | 1.0135 |
| M 256, K 2 (dense) | 8.800 | 7.296 | 1.2061 | 8.800 | 7.296 | 1.2061 |
| M 256, K 6 (dense) | 11.007 | 10.784 | 1.0197 | 10.976 | 10.784 |
1.0169 |
| M 256, K 8 (dense) | 12.512 | 12.224 | 1.0227 | 12.496 | 12.224 |
1.0222 |
| M 512, K 5 (dense) | 16.159 | 15.776 | 1.0250 | 16.160 | 15.776 |
1.0243 |
| M 768, K 4 (dense) | 20.256 | 19.040 | 1.0644 | 20.287 | 19.040 |
1.0650 |
| M 768, K 5 (dense) | 21.792 | 21.536 | 1.0114 | 21.824 | 21.504 |
1.0156 |
| M 1536, K 4 (dense) | 33.248 | 32.703 | 1.0168 | 33.200 | 32.671 |
1.0165 |

Cake ships no other data types or layouts for this operator, since the
dense and snapshot-write forms are the whole family, and 186 programs
(218 libraries: 101 sm_100a, 117 sm_103a) cover B200 (sm_100a, 148 SMs),
B300 (sm_103a, 148 SMs) and GB300 (sm_103a, 152 SMs).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Updates**
* Updated experimental attention-residual processing across supported
GPU configurations, including revised handling of prefix and delta
values.
* Adjusted kernel selection for several hardware and workload
combinations, including expanded pair-kernel coverage and changes to
selected native and persistent routes.
* Updated routing coverage across token counts, GPU architectures, and
execution modes.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery Huang <averyh@nvidia.com>

### [9f6a84c](https://github.com/flashinfer-ai/flashinfer/commit/9f6a84c6ae801ab60b10b9baa435bc57638c759b)

- **作者**: eigen
- **时间**: 2026-10-31T15:37:47Z
- **提交信息**: test(cake_lm_head_det_loss): compare the compacted logprob statistic in one CPU thread (#8117)

On CPU, `test_logprob_entry_matches_unchunked` passes or fails depending on the number of intra-op threads. This PR computes the compared pair in a single CPU thread and keeps the exact bitwise check. This changes only the test. No library code changes.

### Problem

On a CPU device, the test checks two forward statistics (`lse`) for bitwise equality. The first is the compacted log-probability statistic, which covers only rows with a valid label. The second is the same rows taken from the uncompacted statistic (`compact_rows=False`). Both use `backend="reference"`. The two matrices have different shapes. A multi-threaded CPU GEMM can split their rows differently, so the summation order changes and the bits can differ. On a 46-core node, the test fails at 16 and 26 intra-op threads. It passes at 1, 4, 46 and 48 threads. So the result depends on the thread count of the CI machine. The test passes on CUDA devices.

### Fix

The test now computes the compacted and uncompacted pair under `torch.set_num_threads(1)`. A `finally` block restores the previous thread count. The comparison is still exact (`torch.equal`), and the tolerance is not relaxed. The test's other assertions are unchanged. The only changed file is `tests/experimental/test_cake_lm_head_loss.py`.

### Validation

Environment: CPU-only node, 46 cores, PyTorch 2.14.1, CUDA disabled. Base is `main` at `96ca3d01`.

| Intra-op threads | `main` | This PR |
|---|---|---|
| 1 | 3/3 pass | 3/3 pass |
| 4 | 3/3 pass | 3/3 pass |
| 16 | 3/3 fail | 3/3 pass |
| 26 | 3/3 fail | 3/3 pass |
| 46 | 3/3 pass | 3/3 pass |
| 48 | 3/3 pass | 3/3 pass |

I also ran the whole `tests/experimental/test_cake_lm_head_loss.py` file on CPU at the default thread count. Both `main` and this PR give 226 passed, 92 skipped. pre-commit (`ruff check`, `ruff format`) passes on the changed file.


<!-- This is an auto-generated comment: release notes by coderabbit.ai -->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Tests**
  * Updated a test to compare compacted and uncompacted statistics using serial CPU execution and the compacted forward’s log-sum-exp values.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [9d55883](https://github.com/flashinfer-ai/flashinfer/commit/9d55883c15d07e956b4ee3f93113954805b5297a)

- **作者**: eigen
- **时间**: 2026-10-31T15:19:16Z
- **提交信息**: perf(cake_deepgemm_dense_mqa): add a parallel-schedule logits program for the partial-block qle128 kvsplit route on sm_100a up to K = 8192 (#8113)

This PR follows up #7607, #7643, #7741 and #7779. FlashInfer's Cake
DeepGEMM-form MQA logits programs for Blackwell back
`flashinfer.dense_mqa` and `flashinfer.paged_mqa`. The variants are
dense FP8 with 32 or 64 heads, dense FP4 with 32 heads (including fused
metadata + logits sequences), and paged FP8. This PR changes dense FP8
with 64 heads, on sm_100a only. On sm_100a, for K ≤ 8192, the logits
stage of the `fp8:h64:partial:qle128:kvsplit` route now launches a new
logits program, `cake_deepgemm_dense_mqa_1974e6db96c173903467`, through
a stage bucket on that route. The new program runs the parallel
schedule. For longer K, the route keeps its previous program (43147329).
One program is added, and no existing program changes. sm_103a is
unchanged. Logits are bitwise equal on every row of the table (106/106).
The baseline is the previous version, FlashInfer main d9f4d8ed43f7, for
the dense MQA paths. On B200, 3 of the 106 rows in the #7607/#7643 shape
list run the updated route, with speedup 1.0506–1.0634 (median 1.0563).
Each of these rows is faster in all 3 sessions. They are prefill Q 3, Q
7 and Q 37, each with prefix 4100, causal (FP8, 64 heads). The other 103
rows run byte-identical programs in both versions. They read
0.9921–1.0104 with median 1.0000, which is measurement noise.

**NVIDIA B200** (sm_100a, 148 SMs), CUDA 13.4 (nvcc V13.4.92,
JIT-compiled), driver 580.82.07, torch 2.14.1+cu130. Previous version =
FlashInfer main d9f4d8ed43f7 (dense MQA paths). Timing is CUPTI GPU time
per call with a cold L2. µs is the median over the 3 sessions of each
session's median. Speedup is the median over the sessions of previous /
this (> 1 = faster). Rows that launch more than one kernel per call
report the sum of kernel times. The notation is the same as in #7643. `Q
q, K k` is q queries over k keys. `prefill Q q, prefix p, causal` is q
new queries attending causally over p cached keys plus themselves (K = p
+ q). "2 sequences" and "2048-query chunks" mean the same as in #7643.
"updated" means the row runs the new bucket program. "same program"
means every program on the row is byte-identical to the previous
version.

| shape | dtype | heads | previous µs | this PR µs | speedup | program |
|---|---|---:|---:|---:|---:|---|
| prefill Q 37, prefix 4100, causal | FP8 | 32 | 5.28 | 5.28 | 1.0000 |
same program |
| prefill Q 1024, prefix 32779, causal | FP8 | 32 | 137.89 | 137.79 |
1.0000 | same program |
| prefill Q 1, prefix 0, causal | FP8 | 64 | 4.08 | 4.08 | 1.0001 | same
program |
| prefill Q 1, prefix 4100, causal | FP8 | 64 | 4.13 | 4.13 | 1.0000 |
same program |
| prefill Q 1, prefix 32779, causal | FP8 | 64 | 5.12 | 5.12 | 1.0000 |
same program |
| prefill Q 1, prefix 131077, causal | FP8 | 64 | 8.03 | 8.05 | 1.0000 |
same program |
| prefill Q 2, prefix 0, causal | FP8 | 64 | 4.13 | 4.11 | 1.0000 | same
program |
| prefill Q 2, prefix 4100, causal | FP8 | 64 | 4.78 | 4.77 | 1.0002 |
same program |
| prefill Q 3, prefix 0, causal | FP8 | 64 | 3.90 | 3.90 | 1.0000 | same
program |
| prefill Q 3, prefix 4100, causal | FP8 | 64 | 4.83 | 4.54 | 1.0563 |
updated |
| prefill Q 7, prefix 0, causal | FP8 | 64 | 3.97 | 3.97 | 1.0003 | same
program |
| prefill Q 7, prefix 4100, causal | FP8 | 64 | 4.83 | 4.54 | 1.0634 |
updated |
| prefill Q 8, prefix 0, causal | FP8 | 64 | 3.92 | 3.92 | 1.0001 | same
program |
| prefill Q 8, prefix 4100, causal | FP8 | 64 | 4.56 | 4.56 | 1.0000 |
same program |
| prefill Q 16, prefix 0, causal | FP8 | 64 | 3.92 | 3.91 | 1.0020 |
same program |
| prefill Q 16, prefix 4100, causal | FP8 | 64 | 4.61 | 4.61 | 1.0000 |
same program |
| prefill Q 37, prefix 0, causal | FP8 | 64 | 3.92 | 3.94 | 1.0000 |
same program |
| prefill Q 37, prefix 4100, causal | FP8 | 64 | 5.97 | 5.68 | 1.0506 |
updated |
| prefill Q 37, prefix 32779, causal | FP8 | 64 | 14.32 | 14.30 | 1.0000
| same program |
| prefill Q 37, prefix 131077, causal | FP8 | 64 | 40.10 | 40.11 |
0.9996 | same program |
| prefill Q 64, prefix 0, causal | FP8 | 64 | 3.95 | 3.95 | 1.0000 |
same program |
| prefill Q 64, prefix 4100, causal | FP8 | 64 | 6.61 | 6.61 | 0.9999 |
same program |
| prefill Q 128, prefix 0, causal | FP8 | 64 | 4.10 | 4.10 | 1.0000 |
same program |
| prefill Q 128, prefix 4100, causal | FP8 | 64 | 9.26 | 9.26 | 1.0000 |
same program |
| prefill Q 128, prefix 4100, causal, 2 sequences | FP8 | 64 | 8.08 |
8.11 | 0.9961 | same program |
| prefill Q 128, prefix 32779, causal | FP8 | 64 | 34.56 | 34.56 |
1.0000 | same program |
| prefill Q 128, prefix 131077, causal | FP8 | 64 | 125.89 | 126.03 |
1.0019 | same program |
| prefill Q 129, prefix 0, causal | FP8 | 64 | 4.08 | 4.08 | 1.0000 |
same program |
| prefill Q 129, prefix 4100, causal | FP8 | 64 | 9.31 | 9.31 | 1.0000 |
same program |
| prefill Q 1023, prefix 0, causal | FP8 | 64 | 10.24 | 10.26 | 0.9992 |
same program |
| prefill Q 1023, prefix 4100, causal | FP8 | 64 | 40.22 | 40.26 |
1.0000 | same program |
| prefill Q 1024, prefix 0, causal | FP8 | 64 | 10.34 | 10.34 | 1.0000 |
same program |
| prefill Q 1024, prefix 4100, causal | FP8 | 64 | 40.21 | 40.21 |
0.9992 | same program |
| prefill Q 1024, prefix 32779, causal | FP8 | 64 | 263.90 | 264.22 |
1.0002 | same program |
| prefill Q 1024, prefix 131077, causal | FP8 | 64 | 1086.25 | 1086.19 |
1.0002 | same program |
| prefill Q 4096, prefix 0, causal | FP8 | 64 | 69.63 | 69.58 | 1.0000 |
same program |
| prefill Q 4096, prefix 4100, causal | FP8 | 64 | 200.77 | 200.10 |
1.0036 | same program |
| prefill Q 4096, prefix 32779, causal | FP8 | 64 | 1143.50 | 1152.51 |
0.9937 | same program |
| prefill Q 4096, prefix 32779, causal, 2 sequences | FP8 | 64 | 779.94
| 784.35 | 0.9921 | same program |
| prefill Q 4096, prefix 32779, causal, 2048-query chunks | FP8 | 64 |
1154.86 | 1156.25 | 1.0008 | same program |
| prefill Q 4096, prefix 131077, causal | FP8 | 64 | 4441.07 | 4437.35 |
1.0014 | same program |
| prefill Q 4096, prefix 131077, causal, 2048-query chunks | FP8 | 64 |
4429.62 | 4428.68 | 0.9998 | same program |
| prefill Q 8192, prefix 0, causal | FP8 | 64 | 280.22 | 279.18 | 1.0021
| same program |
| prefill Q 8192, prefix 4100, causal | FP8 | 64 | 548.43 | 547.04 |
1.0025 | same program |
| prefill Q 8192, prefix 32779, causal | FP8 | 64 | 2461.25 | 2463.88 |
0.9990 | same program |
| prefill Q 8192, prefix 32779, causal, 2048-query chunks | FP8 | 64 |
2467.41 | 2468.78 | 0.9993 | same program |
| prefill Q 8192, prefix 131077, causal | FP8 | 64 | 9100.63 | 9102.20 |
0.9999 | same program |
| prefill Q 8192, prefix 131077, causal, 2048-query chunks | FP8 | 64 |
9040.11 | 9037.23 | 1.0003 | same program |
| prefill Q 16231, prefix 0, causal | FP8 | 64 | 1097.92 | 1097.47 |
1.0006 | same program |
| prefill Q 16231, prefix 4100, causal | FP8 | 64 | 1637.95 | 1629.15 |
1.0054 | same program |
| prefill Q 16231, prefix 32779, causal | FP8 | 64 | 5424.55 | 5424.45 |
0.9998 | same program |
| prefill Q 16231, prefix 32779, causal, 2048-query chunks | FP8 | 64 |
5462.93 | 5470.32 | 0.9989 | same program |
| prefill Q 16231, prefix 131077, causal | FP8 | 64 | 18797.69 |
18798.54 | 1.0000 | same program |
| prefill Q 16231, prefix 131077, causal, 2048-query chunks | FP8 | 64 |
18532.49 | 18534.52 | 1.0003 | same program |
| Q 1, K 4096 | FP8 | 32 | 3.97 | 3.97 | 0.9999 | same program |
| Q 1, K 32768 | FP8 | 32 | 4.80 | 4.80 | 1.0000 | same program |
| Q 1, K 131072 | FP8 | 32 | 7.71 | 7.71 | 1.0000 | same program |
| Q 1, K 1048576 | FP8 | 32 | 31.10 | 31.10 | 1.0000 | same program |
| Q 1, K 1048832 | FP8 | 32 | 33.86 | 33.87 | 1.0000 | same program |
| Q 3, K 8192 | FP8 | 32 | 4.80 | 4.80 | 0.9968 | same program |
| Q 3, K 1048832 | FP8 | 32 | 34.99 | 34.83 | 1.0037 | same program |
| Q 16, K 2048 | FP8 | 32 | 4.58 | 4.58 | 1.0000 | same program |
| Q 16, K 4096 | FP8 | 32 | 4.66 | 4.64 | 1.0033 | same program |
| Q 16, K 32768 | FP8 | 32 | 7.84 | 7.76 | 1.0104 | same program |
| Q 16, K 131072 | FP8 | 32 | 14.75 | 14.75 | 1.0000 | same program |
| Q 16, K 1048576 | FP8 | 32 | 71.23 | 71.25 | 1.0001 | same program |
| Q 16, K 1048832 | FP8 | 32 | 71.92 | 72.14 | 0.9996 | same program |
| Q 33, K 8192 | FP8 | 32 | 5.50 | 5.52 | 0.9973 | same program |
| Q 33, K 1048832 | FP8 | 32 | 200.82 | 201.93 | 0.9921 | same program |
| Q 37, K 4137 | FP8 | 32 | 5.28 | 5.28 | 1.0000 | same program |
| Q 128, K 2048 | FP8 | 32 | 6.13 | 6.14 | 0.9999 | same program |
| Q 128, K 4096 | FP8 | 32 | 7.36 | 7.36 | 1.0000 | same program |
| Q 128, K 32768 | FP8 | 32 | 21.06 | 21.02 | 1.0015 | same program |
| Q 128, K 131072 | FP8 | 32 | 64.26 | 64.19 | 0.9995 | same program |
| Q 128, K 131328 | FP8 | 32 | 66.29 | 66.26 | 1.0005 | same program |
| Q 130, K 8192 | FP8 | 32 | 10.42 | 10.42 | 1.0000 | same program |
| Q 130, K 8448 | FP8 | 32 | 10.62 | 10.64 | 1.0000 | same program |
| Q 130, K 65792 | FP8 | 32 | 38.98 | 38.93 | 1.0014 | same program |
| Q 132, K 2048 | FP8 | 32 | 6.82 | 6.82 | 1.0001 | same program |
| Q 132, K 8448 | FP8 | 32 | 10.56 | 10.56 | 1.0000 | same program |
| Q 132, K 65792 | FP8 | 32 | 39.15 | 39.17 | 0.9996 | same program |
| Q 1024, K 33803 | FP8 | 32 | 140.10 | 139.76 | 1.0031 | same program |
| Q 2052, K 2048 | FP8 | 32 | 23.82 | 23.82 | 1.0000 | same program |
| Q 2052, K 8448 | FP8 | 32 | 69.81 | 69.82 | 1.0002 | same program |
| Q 2053, K 2048 | FP8 | 32 | 24.11 | 24.18 | 1.0000 | same program |
| Q 2053, K 8448 | FP8 | 32 | 70.53 | 70.59 | 0.9991 | same program |
| Q 1, K 4096 | FP4 | 32 | 4.00 | 4.00 | 1.0000 | same program |
| Q 1, K 32768 | FP4 | 32 | 4.74 | 4.75 | 0.9999 | same program |
| Q 1, K 131072 | FP4 | 32 | 6.51 | 6.51 | 1.0025 | same program |
| Q 1, K 131328 | FP4 | 32 | 11.38 | 11.44 | 0.9972 | same program |
| Q 7, K 2048 | FP4 | 32 | 5.18 | 5.15 | 1.0060 | same program |
| Q 16, K 4096 | FP4 | 32 | 5.34 | 5.33 | 1.0031 | same program |
| Q 16, K 32768 | FP4 | 32 | 7.30 | 7.28 | 1.0000 | same program |
| Q 16, K 131072 | FP4 | 32 | 13.98 | 13.98 | 0.9977 | same program |
| Q 16, K 1048576 | FP4 | 32 | 63.06 | 63.02 | 1.0000 | same program |
| Q 16, K 1048832 | FP4 | 32 | 66.02 | 65.82 | 1.0005 | same program |
| Q 33, K 8192 | FP4 | 32 | 6.05 | 6.05 | 1.0000 | same program |
| Q 33, K 1048832 | FP4 | 32 | 137.84 | 138.19 | 1.0020 | same program |
| Q 128, K 4096 | FP4 | 32 | 6.91 | 6.90 | 1.0023 | same program |
| Q 128, K 32768 | FP4 | 32 | 19.70 | 19.70 | 1.0000 | same program |
| Q 128, K 131072 | FP4 | 32 | 61.30 | 61.34 | 1.0003 | same program |
| Q 130, K 65536 | FP4 | 32 | 35.78 | 35.74 | 0.9991 | same program |
| Q 130, K 65792 | FP4 | 32 | 37.81 | 37.71 | 0.9987 | same program |
| Q 1024, K 2048 | FP4 | 32 | 14.16 | 14.16 | 1.0000 | same program |
| Q 2052, K 2048 | FP4 | 32 | 23.97 | 23.92 | 1.0033 | same program |
| Q 2052, K 65792 | FP4 | 32 | 471.18 | 470.54 | 1.0001 | same program |

The family's other Cake variants (dense FP8 with 32 or 64 heads, dense
FP4 with 32 heads including fused metadata + logits sequences, and paged
FP8) ship on sm_100a and sm_103a only.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

- **New Features**
- Added architecture-specific execution selection for FP8 dense MQA on
supported hardware when the KV length is 8,192 or less.
- KV-split routes can now use bucket-based stage selection for both full
and partial route types. For full routes, bucket programs correspond to
the matching partial route; partial routes can use route-specific
programs. Selection falls back to the route’s default stages when no
bucket covers the KV length.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery Huang <averyh@nvidia.com>

### [b194ced](https://github.com/flashinfer-ai/flashinfer/commit/b194cedd068278e4626f6db082078658c6de6ac8)

- **作者**: eigen
- **时间**: 2026-10-31T15:10:08Z
- **提交信息**: perf(cake_fused_qk_rope_append, cake_fused_qk_rope_fp8_append): add opt-in PDL launch on sm_100a/sm_103a (#8112)

FlashInfer has two Cake variants of the fused QK RMSNorm + NeoX RoPE +
paged KV-cache append kernel. They are BF16
(`cake_fused_qk_rope_append`) and FP8 E4M3
(`cake_fused_qk_rope_fp8_append`). This PR changes both. It adds
`enable_pdl: bool = False` to
`cake_fused_qk_rmsnorm_rope_append_paged_kv_cache` and
`cake_fused_qk_rmsnorm_rope_quantize_fp8_append_paged_kv_cache`. The new
path applies with `enable_pdl=True` on sm_100a or sm_103a with 64/8 or
8/1 heads. There, the call launches a programmatic dependent launch
(PDL) build of the stage it already selects. That kernel can start while
the preceding kernel on the stream is still running. It waits for that
kernel before it reads `qkv` and before any store. So the preceding
kernel may write `qkv`. It must not write `q_indptr`, `seq_lens`,
`page_indices`, `cos_sin` or the norm weights, because these are read
before the wait. Outputs are bitwise identical to `enable_pdl=False`.
The default and all other calls use exactly the existing builds. PDL
stays off where measurements showed no gain. For FP8, this covers 64/8
with num_rows >= 240, and 8/1 decode with 129..223 requests on sm_100a
or 187..223 on sm_103a. For BF16, it covers 64/8 with num_rows >= 600
and 8/1 decode with 512..547 requests. Other head configurations also
keep the plain launch. Against FlashInfer main, every PDL-on row is
faster on all four GPUs. On B200, GB200, B300 and GB300, the FP8 geomean
speedups are 1.1395, 1.1408, 1.1422 and 1.1499. The BF16 geomean
speedups are 1.1720, 1.1849, 1.1866 and 1.1886. Per-row speedups range
from 1.0044 to 1.3558 for FP8 and from 1.0498 to 1.3358 for BF16.

Measured on B200 (sm_100a, 148 SMs), GB200 (sm_100a, 152 SMs), B300
(sm_103a, 148 SMs) and GB300 (sm_103a, 152 SMs). Both packages were
built by FlashInfer's JIT with CUDA 13.4 and PyTorch 2.14.1+cu130. Both
were called through the public API on the same GPU in one process. PDL
only helps when the producer kernel triggers its dependents early. So
each row times one step of [QKV projection GEMM -> this kernel]. The
producer is the BF16 projection `torch.mm(x, W, out=qkv)` (cuBLAS), with
x [T, Hq*128] and W [Hq*128, (Hq+2*Hkv)*128]. Each side runs one CUDA
graph of 8 x [L2 flush, GEMM, fused kernel]. Each event-timed slot
replays it 8 times, in interleaved ABBA cycles across 2 fresh-process
sessions. The L2-flush time is subtracted, so each value is the GEMM +
fused-kernel time per step in µs. Speedup = FlashInfer main / this PR.
For every PDL-on row, the 95 % bootstrap CI of the ratio excludes 1 in
both sessions. Each GPU has 39 FP8 and 27 BF16 PDL-on rows, plus 5 FP8
and 1 BF16 "off" rows. "Off" rows run the same plain kernel as main, so
their ratio is measurement spread. Row names: `64x8`/`8x1` are query/KV
heads (head_dim 128). `q1`/`q2` mean Q is quantized with a dynamic
per-token/per-head scale (`q1`) or a static scale (`q2`). `n0`/`n1`/`n2`
mean no RMSNorm, RoPE then RMSNorm, or RMSNorm then RoPE. `P_decode` is
32 requests x 1 new token and `P_prefill` is 8 requests x 16 new tokens,
with 2048 cached tokens and page size 64 unless the name says otherwise.
`E_prefill_*_q127/q128/q129` is 4 requests x 127/128/129 new tokens,
which is the 128-row scale-padding boundary. In `X_*` rows,
`B1`/`B128`/`B256` = 1/128/256 requests, `Q1024` = 1024 new tokens,
`page16`/`page128` = page size 16/128, `ctx32768` = 32768 cached tokens,
`outkv` = caller-owned `out_k`/`out_v`, `ragged` = 8 requests with
ragged new-token counts, and `maxseq1024` = 8 requests x 16 new tokens
with max_seqlen 1024. The FP8 "off" rows are
`E_prefill_64x8_q127/q128/q129`, `X_decode_64x8_B256_q1_n2` and
`X_prefill_64x8_B1_Q1024_q1_n2`. BF16 rows give their geometry in the
table's shape column. This covers query/KV heads, requests x new tokens,
cached tokens, page size, `n0`/`n1`/`n2` and `outkv`. The BF16 "off" row
is `X2` (512-request decode).

The kernel's two variants, BF16 and FP8 E4M3, are both covered here. The
family ships on sm_90a, sm_100a and sm_103a, and PDL is enabled on
sm_100a and sm_103a only (`enable_pdl` is ignored on sm_90a).

**NVIDIA B200, sm_100a (148 SMs), CUDA 13.4. Speedup = FlashInfer main /
this PR.**


FP8 E4M3 (`cake_fused_qk_rope_fp8_append`)

| shape | PDL | FlashInfer main (µs) | this PR (µs) | speedup |
|---|---|---:|---:|---:|
| `P_decode_8x1_q1_n0` | on | 6.570 | 5.058 | 1.2989 |
| `P_decode_8x1_q1_n1` | on | 6.783 | 5.224 | 1.2984 |
| `P_decode_8x1_q1_n2` | on | 6.735 | 5.279 | 1.2758 |
| `P_decode_8x1_q2_n0` | on | 6.576 | 5.024 | 1.3089 |
| `P_decode_8x1_q2_n1` | on | 7.620 | 5.840 | 1.3048 |
| `P_decode_8x1_q2_n2` | on | 7.697 | 5.888 | 1.3072 |
| `P_decode_64x8_q1_n0` | on | 41.521 | 40.879 | 1.0157 |
| `P_decode_64x8_q1_n1` | on | 41.742 | 41.103 | 1.0155 |
| `P_decode_64x8_q1_n2` | on | 41.603 | 41.010 | 1.0145 |
| `P_decode_64x8_q2_n0` | on | 41.585 | 41.009 | 1.0140 |
| `P_decode_64x8_q2_n1` | on | 41.552 | 41.044 | 1.0124 |
| `P_decode_64x8_q2_n2` | on | 41.554 | 40.928 | 1.0153 |
| `P_prefill_8x1_q1_n0` | on | 7.040 | 5.568 | 1.2644 |
| `P_prefill_8x1_q1_n1` | on | 7.168 | 5.665 | 1.2653 |
| `P_prefill_8x1_q1_n2` | on | 7.217 | 5.787 | 1.2471 |
| `P_prefill_8x1_q2_n0` | on | 6.932 | 5.370 | 1.2909 |
| `P_prefill_8x1_q2_n1` | on | 7.120 | 5.600 | 1.2714 |
| `P_prefill_8x1_q2_n2` | on | 7.073 | 5.568 | 1.2703 |
| `P_prefill_64x8_q1_n0` | on | 44.384 | 43.256 | 1.0261 |
| `P_prefill_64x8_q1_n1` | on | 44.710 | 43.504 | 1.0277 |
| `P_prefill_64x8_q1_n2` | on | 44.643 | 43.536 | 1.0254 |
| `P_prefill_64x8_q2_n0` | on | 44.432 | 43.238 | 1.0276 |
| `P_prefill_64x8_q2_n1` | on | 44.721 | 43.464 | 1.0289 |
| `P_prefill_64x8_q2_n2` | on | 44.713 | 43.520 | 1.0274 |
| `E_prefill_8x1_q127` | on | 7.881 | 7.648 | 1.0305 |
| `E_prefill_8x1_q128` | on | 7.937 | 7.649 | 1.0377 |
| `E_prefill_8x1_q129` | on | 7.864 | 7.679 | 1.0241 |
| `E_prefill_64x8_q127` | off | 72.800 | 72.791 | 1.0001 |
| `E_prefill_64x8_q128` | off | 73.152 | 73.167 | 0.9998 |
| `E_prefill_64x8_q129` | off | 77.883 | 77.808 | 1.0010 |
| `X_decode_8x1_B1_q1_n2` | on | 6.672 | 5.278 | 1.2641 |
| `X_decode_8x1_B128_q1_n2` | on | 7.297 | 6.449 | 1.1315 |
| `X_decode_8x1_B256_q1_n2` | on | 8.414 | 8.154 | 1.0319 |
| `X_prefill_8x1_B1_Q1024_q1_n2` | on | 9.442 | 8.787 | 1.0745 |
| `X_decode_64x8_B1_q1_n2` | on | 39.921 | 39.432 | 1.0124 |
| `X_decode_64x8_B128_q1_n2` | on | 47.663 | 46.512 | 1.0247 |
| `X_decode_64x8_B256_q1_n2` | off | 56.992 | 57.064 | 0.9987 |
| `X_prefill_64x8_B1_Q1024_q1_n2` | off | 147.870 | 148.804 | 0.9937 |
| `X_decode_8x1_q1_n2_page16` | on | 6.991 | 5.929 | 1.1791 |
| `X_decode_8x1_q1_n2_page128` | on | 6.908 | 5.257 | 1.3141 |
| `X_decode_8x1_q1_n2_ctx32768` | on | 7.121 | 6.011 | 1.1847 |
| `X_prefill_8x1_ragged_q1_n2` | on | 7.263 | 5.981 | 1.2143 |
| `X_decode_8x1_q1_n2_outkv` | on | 6.695 | 5.345 | 1.2526 |
| `X_prefill_8x1_q1_n2_maxseq1024` | on | 7.136 | 5.633 | 1.2668 |

BF16 (`cake_fused_qk_rope_append`)

| shape | PDL | FlashInfer main (µs) | this PR (µs) | speedup |
|---|---|---:|---:|---:|
| `M1` 8/1, 32 req x 1 new, ctx 2048, page 64, n2 | on | 6.539 | 5.355 |
1.2211 |
| `M1a` 8/1, 32 req x 1 new, ctx 2048, page 64, n0 | on | 6.500 | 5.380
| 1.2082 |
| `M1b` 8/1, 32 req x 1 new, ctx 2048, page 64, n1 | on | 6.496 | 5.392
| 1.2047 |
| `M2` 8/1, 8 req x 16 new, ctx 2048, page 64, n2 | on | 6.702 | 5.723 |
1.1711 |
| `M2a` 8/1, 8 req x 16 new, ctx 2048, page 64, n0 | on | 7.553 | 6.145
| 1.2291 |
| `M2b` 8/1, 8 req x 16 new, ctx 2048, page 64, n1 | on | 7.775 | 6.303
| 1.2335 |
| `H1` 64/8, 32 req x 1 new, ctx 2048, page 64, n2 | on | 12.169 |
11.409 | 1.0666 |
| `H2` 64/8, 8 req x 16 new, ctx 2048, page 64, n2 | on | 13.224 |
12.568 | 1.0522 |
| `H3` 64/8, 128 req x 1 new, ctx 2048, page 64, n2 | on | 13.381 |
12.707 | 1.0530 |
| `H4` 64/8, 1 req x 128 new, ctx 2048, page 64, n2 | on | 13.168 |
12.499 | 1.0535 |
| `D1` 8/1, 1 req x 1 new, ctx 2048, page 64, n2 | on | 6.853 | 5.243 |
1.3071 |
| `D2` 8/1, 8 req x 1 new, ctx 2048, page 64, n2 | on | 6.619 | 5.118 |
1.2933 |
| `D3` 8/1, 128 req x 1 new, ctx 2048, page 64, n2 | on | 7.173 | 6.500
| 1.1035 |
| `D4` 8/1, 256 req x 1 new, ctx 2048, page 64, n2 | on | 8.086 | 7.222
| 1.1196 |
| `P1` 8/1, 1 req x 128 new, ctx 2048, page 64, n2 | on | 6.912 | 5.697
| 1.2133 |
| `P2` 8/1, 4 req x 64 new, ctx 2048, page 64, n2 | on | 7.107 | 6.000 |
1.1845 |
| `P3` 8/1, 32 req x 8 new, ctx 2048, page 64, n2 | on | 7.217 | 6.292 |
1.1470 |
| `E1` 8/1, 32 req x 1 new, ctx 2048, page 16, n2 | on | 6.593 | 5.248 |
1.2563 |
| `E2` 8/1, 32 req x 1 new, ctx 2048, page 128, n2 | on | 6.559 | 5.536
| 1.1848 |
| `E3` 8/1, 32 req x 1 new, ctx 0, page 64, n2 | on | 6.575 | 5.376 |
1.2230 |
| `E4` 8/1, 8 req x 16 new, ctx 2047, page 64, n2 | on | 6.880 | 5.927 |
1.1608 |
| `E5` 8/1, 32 req x 1 new, ctx 2048, page 64, n2, outkv | on | 6.545 |
5.504 | 1.1891 |
| `E6` 8/1, 16 req ragged (1-64 new, 0-4095 cached), page 64, n2 | on |
7.728 | 6.441 | 1.1998 |
| `X1` 8/1, 32 req x 1 new, ctx 32768, page 64, n2 | on | 6.464 | 5.250
| 1.2312 |
| `X2` 8/1, 512 req x 1 new, ctx 2048, page 64, n2 | off | 9.121 | 9.152
| 0.9966 |
| `X3` 64/8, 32 req x 1 new, ctx 2048, page 64, n0 | on | 12.047 |
11.280 | 1.0680 |
| `X4` 64/8, 32 req x 1 new, ctx 2048, page 64, n1 | on | 11.888 |
11.173 | 1.0640 |
| `X5` 8/1, 32 req x 1 new, ctx 2048, page 32, n2 | on | 6.600 | 5.183 |
1.2734 |

**NVIDIA GB200, sm_100a (152 SMs), CUDA 13.4. Speedup = FlashInfer main
/ this PR.**


FP8 E4M3 (`cake_fused_qk_rope_fp8_append`)

| shape | PDL | FlashInfer main (µs) | this PR (µs) | speedup |
|---|---|---:|---:|---:|
| `P_decode_8x1_q1_n0` | on | 6.472 | 4.984 | 1.2986 |
| `P_decode_8x1_q1_n1` | on | 6.640 | 5.184 | 1.2809 |
| `P_decode_8x1_q1_n2` | on | 6.656 | 5.168 | 1.2879 |
| `P_decode_8x1_q2_n0` | on | 6.450 | 4.913 | 1.3128 |
| `P_decode_8x1_q2_n1` | on | 7.152 | 5.600 | 1.2771 |
| `P_decode_8x1_q2_n2` | on | 7.019 | 5.539 | 1.2672 |
| `P_decode_64x8_q1_n0` | on | 40.135 | 39.240 | 1.0228 |
| `P_decode_64x8_q1_n1` | on | 39.975 | 39.152 | 1.0210 |
| `P_decode_64x8_q1_n2` | on | 39.929 | 39.225 | 1.0179 |
| `P_decode_64x8_q2_n0` | on | 39.850 | 39.048 | 1.0205 |
| `P_decode_64x8_q2_n1` | on | 39.992 | 39.327 | 1.0169 |
| `P_decode_64x8_q2_n2` | on | 39.840 | 39.168 | 1.0172 |
| `P_prefill_8x1_q1_n0` | on | 6.672 | 5.351 | 1.2469 |
| `P_prefill_8x1_q1_n1` | on | 6.896 | 5.480 | 1.2584 |
| `P_prefill_8x1_q1_n2` | on | 6.842 | 5.551 | 1.2326 |
| `P_prefill_8x1_q2_n0` | on | 6.641 | 5.105 | 1.3009 |
| `P_prefill_8x1_q2_n1` | on | 6.672 | 5.328 | 1.2523 |
| `P_prefill_8x1_q2_n2` | on | 6.717 | 5.311 | 1.2647 |
| `P_prefill_64x8_q1_n0` | on | 43.464 | 42.341 | 1.0265 |
| `P_prefill_64x8_q1_n1` | on | 43.899 | 42.568 | 1.0313 |
| `P_prefill_64x8_q1_n2` | on | 43.769 | 42.591 | 1.0277 |
| `P_prefill_64x8_q2_n0` | on | 43.478 | 42.192 | 1.0305 |
| `P_prefill_64x8_q2_n1` | on | 43.793 | 42.513 | 1.0301 |
| `P_prefill_64x8_q2_n2` | on | 43.743 | 42.511 | 1.0290 |
| `E_prefill_8x1_q127` | on | 7.429 | 7.237 | 1.0265 |
| `E_prefill_8x1_q128` | on | 7.411 | 7.245 | 1.0229 |
| `E_prefill_8x1_q129` | on | 7.504 | 7.295 | 1.0286 |
| `E_prefill_64x8_q127` | off | 91.706 | 91.760 | 0.9994 |
| `E_prefill_64x8_q128` | off | 91.647 | 91.664 | 0.9998 |
| `E_prefill_64x8_q129` | off | 80.552 | 80.565 | 0.9998 |
| `X_decode_8x1_B1_q1_n2` | on | 6.768 | 4.992 | 1.3558 |
| `X_decode_8x1_B128_q1_n2` | on | 7.192 | 6.009 | 1.1969 |
| `X_decode_8x1_B256_q1_n2` | on | 8.016 | 7.712 | 1.0394 |
| `X_prefill_8x1_B1_Q1024_q1_n2` | on | 8.993 | 8.545 | 1.0524 |
| `X_decode_64x8_B1_q1_n2` | on | 38.793 | 38.305 | 1.0127 |
| `X_decode_64x8_B128_q1_n2` | on | 46.321 | 45.126 | 1.0265 |
| `X_decode_64x8_B256_q1_n2` | off | 56.719 | 56.703 | 1.0003 |
| `X_prefill_64x8_B1_Q1024_q1_n2` | off | 143.560 | 143.008 | 1.0039 |
| `X_decode_8x1_q1_n2_page16` | on | 6.807 | 5.731 | 1.1878 |
| `X_decode_8x1_q1_n2_page128` | on | 6.713 | 5.113 | 1.3129 |
| `X_decode_8x1_q1_n2_ctx32768` | on | 6.761 | 5.603 | 1.2067 |
| `X_prefill_8x1_ragged_q1_n2` | on | 6.905 | 5.624 | 1.2278 |
| `X_decode_8x1_q1_n2_outkv` | on | 6.640 | 5.344 | 1.2425 |
| `X_prefill_8x1_q1_n2_maxseq1024` | on | 6.929 | 5.623 | 1.2323 |

BF16 (`cake_fused_qk_rope_append`)

| shape | PDL | FlashInfer main (µs) | this PR (µs) | speedup |
|---|---|---:|---:|---:|
| `M1` 8/1, 32 req x 1 new, ctx 2048, page 64, n2 | on | 6.223 | 5.087 |
1.2233 |
| `M1a` 8/1, 32 req x 1 new, ctx 2048, page 64, n0 | on | 6.271 | 5.195
| 1.2071 |
| `M1b` 8/1, 32 req x 1 new, ctx 2048, page 64, n1 | on | 6.369 | 5.184
| 1.2286 |
| `M2` 8/1, 8 req x 16 new, ctx 2048, page 64, n2 | on | 6.656 | 5.432 |
1.2253 |
| `M2a` 8/1, 8 req x 16 new, ctx 2048, page 64, n0 | on | 7.200 | 5.729
| 1.2568 |
| `M2b` 8/1, 8 req x 16 new, ctx 2048, page 64, n1 | on | 7.232 | 5.824
| 1.2418 |
| `H1` 64/8, 32 req x 1 new, ctx 2048, page 64, n2 | on | 11.615 |
10.816 | 1.0739 |
| `H2` 64/8, 8 req x 16 new, ctx 2048, page 64, n2 | on | 12.496 |
11.868 | 1.0529 |
| `H3` 64/8, 128 req x 1 new, ctx 2048, page 64, n2 | on | 12.681 |
12.080 | 1.0498 |
| `H4` 64/8, 1 req x 128 new, ctx 2048, page 64, n2 | on | 12.481 |
11.817 | 1.0562 |
| `D1` 8/1, 1 req x 1 new, ctx 2048, page 64, n2 | on | 6.336 | 4.816 |
1.3156 |
| `D2` 8/1, 8 req x 1 new, ctx 2048, page 64, n2 | on | 6.480 | 4.912 |
1.3192 |
| `D3` 8/1, 128 req x 1 new, ctx 2048, page 64, n2 | on | 6.897 | 6.241
| 1.1051 |
| `D4` 8/1, 256 req x 1 new, ctx 2048, page 64, n2 | on | 7.568 | 6.832
| 1.1077 |
| `P1` 8/1, 1 req x 128 new, ctx 2048, page 64, n2 | on | 6.721 | 5.387
| 1.2476 |
| `P2` 8/1, 4 req x 64 new, ctx 2048, page 64, n2 | on | 6.783 | 5.631 |
1.2046 |
| `P3` 8/1, 32 req x 8 new, ctx 2048, page 64, n2 | on | 6.832 | 5.983 |
1.1419 |
| `E1` 8/1, 32 req x 1 new, ctx 2048, page 16, n2 | on | 6.132 | 4.873 |
1.2584 |
| `E2` 8/1, 32 req x 1 new, ctx 2048, page 128, n2 | on | 6.513 | 5.551
| 1.1733 |
| `E3` 8/1, 32 req x 1 new, ctx 0, page 64, n2 | on | 6.128 | 5.024 |
1.2197 |
| `E4` 8/1, 8 req x 16 new, ctx 2047, page 64, n2 | on | 6.653 | 5.388 |
1.2348 |
| `E5` 8/1, 32 req x 1 new, ctx 2048, page 64, n2, outkv | on | 6.393 |
5.233 | 1.2217 |
| `E6` 8/1, 16 req ragged (1-64 new, 0-4095 cached), page 64, n2 | on |
7.536 | 6.127 | 1.2300 |
| `X1` 8/1, 32 req x 1 new, ctx 32768, page 64, n2 | on | 6.294 | 5.066
| 1.2424 |
| `X2` 8/1, 512 req x 1 new, ctx 2048, page 64, n2 | off | 8.920 | 8.913
| 1.0008 |
| `X3` 64/8, 32 req x 1 new, ctx 2048, page 64, n0 | on | 11.759 |
11.024 | 1.0667 |
| `X4` 64/8, 32 req x 1 new, ctx 2048, page 64, n1 | on | 11.568 |
10.758 | 1.0753 |
| `X5` 8/1, 32 req x 1 new, ctx 2048, page 32, n2 | on | 6.417 | 4.961 |
1.2935 |

**NVIDIA B300, sm_103a (148 SMs), CUDA 13.4. Speedup = FlashInfer main /
this PR.**


FP8 E4M3 (`cake_fused_qk_rope_fp8_append`)

| shape | PDL | FlashInfer main (µs) | this PR (µs) | speedup |
|---|---|---:|---:|---:|
| `P_decode_8x1_q1_n0` | on | 6.343 | 4.803 | 1.3206 |
| `P_decode_8x1_q1_n1` | on | 6.585 | 5.054 | 1.3029 |
| `P_decode_8x1_q1_n2` | on | 6.614 | 5.080 | 1.3020 |
| `P_decode_8x1_q2_n0` | on | 6.369 | 4.768 | 1.3358 |
| `P_decode_8x1_q2_n1` | on | 7.390 | 5.712 | 1.2938 |
| `P_decode_8x1_q2_n2` | on | 7.457 | 5.801 | 1.2855 |
| `P_decode_64x8_q1_n0` | on | 42.382 | 41.536 | 1.0204 |
| `P_decode_64x8_q1_n1` | on | 41.944 | 41.484 | 1.0111 |
| `P_decode_64x8_q1_n2` | on | 42.016 | 41.423 | 1.0143 |
| `P_decode_64x8_q2_n0` | on | 42.048 | 41.328 | 1.0174 |
| `P_decode_64x8_q2_n1` | on | 42.160 | 41.327 | 1.0202 |
| `P_decode_64x8_q2_n2` | on | 41.874 | 41.345 | 1.0128 |
| `P_prefill_8x1_q1_n0` | on | 6.866 | 5.376 | 1.2772 |
| `P_prefill_8x1_q1_n1` | on | 6.974 | 5.563 | 1.2536 |
| `P_prefill_8x1_q1_n2` | on | 6.945 | 5.615 | 1.2369 |
| `P_prefill_8x1_q2_n0` | on | 6.774 | 5.183 | 1.3070 |
| `P_prefill_8x1_q2_n1` | on | 6.912 | 5.376 | 1.2857 |
| `P_prefill_8x1_q2_n2` | on | 6.852 | 5.348 | 1.2812 |
| `P_prefill_64x8_q1_n0` | on | 46.303 | 45.065 | 1.0275 |
| `P_prefill_64x8_q1_n1` | on | 46.598 | 45.351 | 1.0275 |
| `P_prefill_64x8_q1_n2` | on | 46.599 | 45.342 | 1.0277 |
| `P_prefill_64x8_q2_n0` | on | 46.312 | 45.096 | 1.0270 |
| `P_prefill_64x8_q2_n1` | on | 46.641 | 45.352 | 1.0284 |
| `P_prefill_64x8_q2_n2` | on | 46.600 | 45.328 | 1.0281 |
| `E_prefill_8x1_q127` | on | 7.489 | 7.168 | 1.0448 |
| `E_prefill_8x1_q128` | on | 7.552 | 7.175 | 1.0525 |
| `E_prefill_8x1_q129` | on | 7.488 | 7.167 | 1.0448 |
| `E_prefill_64x8_q127` | off | 70.351 | 70.336 | 1.0002 |
| `E_prefill_64x8_q128` | off | 70.869 | 70.837 | 1.0005 |
| `E_prefill_64x8_q129` | off | 72.289 | 72.258 | 1.0004 |
| `X_decode_8x1_B1_q1_n2` | on | 6.400 | 4.928 | 1.2987 |
| `X_decode_8x1_B128_q1_n2` | on | 6.992 | 6.337 | 1.1034 |
| `X_decode_8x1_B256_q1_n2` | on | 7.808 | 7.774 | 1.0044 |
| `X_prefill_8x1_B1_Q1024_q1_n2` | on | 9.016 | 8.390 | 1.0746 |
| `X_decode_64x8_B1_q1_n2` | on | 40.161 | 39.726 | 1.0110 |
| `X_decode_64x8_B128_q1_n2` | on | 49.145 | 47.904 | 1.0259 |
| `X_decode_64x8_B256_q1_n2` | off | 57.728 | 57.791 | 0.9989 |
| `X_prefill_64x8_B1_Q1024_q1_n2` | off | 139.680 | 138.576 | 1.0080 |
| `X_decode_8x1_q1_n2_page16` | on | 6.674 | 5.462 | 1.2219 |
| `X_decode_8x1_q1_n2_page128` | on | 6.761 | 5.440 | 1.2428 |
| `X_decode_8x1_q1_n2_ctx32768` | on | 6.880 | 5.479 | 1.2557 |
| `X_prefill_8x1_ragged_q1_n2` | on | 6.934 | 5.697 | 1.2171 |
| `X_decode_8x1_q1_n2_outkv` | on | 6.524 | 5.344 | 1.2208 |
| `X_prefill_8x1_q1_n2_maxseq1024` | on | 6.802 | 5.465 | 1.2446 |

BF16 (`cake_fused_qk_rope_append`)

| shape | PDL | FlashInfer main (µs) | this PR (µs) | speedup |
|---|---|---:|---:|---:|
| `M1` 8/1, 32 req x 1 new, ctx 2048, page 64, n2 | on | 6.225 | 4.954 |
1.2566 |
| `M1a` 8/1, 32 req x 1 new, ctx 2048, page 64, n0 | on | 6.283 | 5.088
| 1.2349 |
| `M1b` 8/1, 32 req x 1 new, ctx 2048, page 64, n1 | on | 6.336 | 5.120
| 1.2375 |
| `M2` 8/1, 8 req x 16 new, ctx 2048, page 64, n2 | on | 6.543 | 5.441 |
1.2025 |
| `M2a` 8/1, 8 req x 16 new, ctx 2048, page 64, n0 | on | 7.329 | 5.868
| 1.2490 |
| `M2b` 8/1, 8 req x 16 new, ctx 2048, page 64, n1 | on | 7.471 | 6.143
| 1.2162 |
| `H1` 64/8, 32 req x 1 new, ctx 2048, page 64, n2 | on | 11.769 |
11.005 | 1.0694 |
| `H2` 64/8, 8 req x 16 new, ctx 2048, page 64, n2 | on | 12.817 |
12.130 | 1.0566 |
| `H3` 64/8, 128 req x 1 new, ctx 2048, page 64, n2 | on | 13.059 |
12.385 | 1.0544 |
| `H4` 64/8, 1 req x 128 new, ctx 2048, page 64, n2 | on | 12.789 |
12.086 | 1.0582 |
| `D1` 8/1, 1 req x 1 new, ctx 2048, page 64, n2 | on | 6.555 | 4.948 |
1.3248 |
| `D2` 8/1, 8 req x 1 new, ctx 2048, page 64, n2 | on | 6.374 | 4.894 |
1.3024 |
| `D3` 8/1, 128 req x 1 new, ctx 2048, page 64, n2 | on | 6.822 | 6.182
| 1.1035 |
| `D4` 8/1, 256 req x 1 new, ctx 2048, page 64, n2 | on | 7.710 | 6.912
| 1.1155 |
| `P1` 8/1, 1 req x 128 new, ctx 2048, page 64, n2 | on | 6.599 | 5.407
| 1.2205 |
| `P2` 8/1, 4 req x 64 new, ctx 2048, page 64, n2 | on | 6.678 | 5.599 |
1.1927 |
| `P3` 8/1, 32 req x 8 new, ctx 2048, page 64, n2 | on | 6.913 | 5.857 |
1.1803 |
| `E1` 8/1, 32 req x 1 new, ctx 2048, page 16, n2 | on | 6.303 | 4.893 |
1.2882 |
| `E2` 8/1, 32 req x 1 new, ctx 2048, page 128, n2 | on | 6.238 | 5.184
| 1.2033 |
| `E3` 8/1, 32 req x 1 new, ctx 0, page 64, n2 | on | 6.408 | 5.239 |
1.2231 |
| `E4` 8/1, 8 req x 16 new, ctx 2047, page 64, n2 | on | 6.591 | 5.538 |
1.1901 |
| `E5` 8/1, 32 req x 1 new, ctx 2048, page 64, n2, outkv | on | 6.371 |
5.152 | 1.2366 |
| `E6` 8/1, 16 req ragged (1-64 new, 0-4095 cached), page 64, n2 | on |
7.265 | 5.936 | 1.2239 |
| `X1` 8/1, 32 req x 1 new, ctx 32768, page 64, n2 | on | 6.210 | 4.994
| 1.2435 |
| `X2` 8/1, 512 req x 1 new, ctx 2048, page 64, n2 | off | 8.705 | 8.734
| 0.9967 |
| `X3` 64/8, 32 req x 1 new, ctx 2048, page 64, n0 | on | 11.644 |
10.878 | 1.0704 |
| `X4` 64/8, 32 req x 1 new, ctx 2048, page 64, n1 | on | 11.599 |
10.851 | 1.0689 |
| `X5` 8/1, 32 req x 1 new, ctx 2048, page 32, n2 | on | 6.301 | 4.865 |
1.2952 |

**NVIDIA GB300, sm_103a (152 SMs), CUDA 13.4. Speedup = FlashInfer main
/ this PR.**


FP8 E4M3 (`cake_fused_qk_rope_fp8_append`)

| shape | PDL | FlashInfer main (µs) | this PR (µs) | speedup |
|---|---|---:|---:|---:|
| `P_decode_8x1_q1_n0` | on | 6.624 | 5.152 | 1.2857 |
| `P_decode_8x1_q1_n1` | on | 6.616 | 5.327 | 1.2420 |
| `P_decode_8x1_q1_n2` | on | 6.640 | 5.281 | 1.2573 |
| `P_decode_8x1_q2_n0` | on | 6.592 | 5.184 | 1.2716 |
| `P_decode_8x1_q2_n1` | on | 7.176 | 5.776 | 1.2424 |
| `P_decode_8x1_q2_n2` | on | 7.104 | 5.652 | 1.2569 |
| `P_decode_64x8_q1_n0` | on | 41.002 | 39.776 | 1.0308 |
| `P_decode_64x8_q1_n1` | on | 41.120 | 39.888 | 1.0309 |
| `P_decode_64x8_q1_n2` | on | 41.118 | 39.920 | 1.0300 |
| `P_decode_64x8_q2_n0` | on | 40.945 | 39.848 | 1.0275 |
| `P_decode_64x8_q2_n1` | on | 41.008 | 39.848 | 1.0291 |
| `P_decode_64x8_q2_n2` | on | 40.913 | 39.857 | 1.0265 |
| `P_prefill_8x1_q1_n0` | on | 6.696 | 5.144 | 1.3017 |
| `P_prefill_8x1_q1_n1` | on | 6.896 | 5.359 | 1.2868 |
| `P_prefill_8x1_q1_n2` | on | 6.870 | 5.360 | 1.2817 |
| `P_prefill_8x1_q2_n0` | on | 6.657 | 5.056 | 1.3167 |
| `P_prefill_8x1_q2_n1` | on | 6.703 | 5.175 | 1.2953 |
| `P_prefill_8x1_q2_n2` | on | 6.784 | 5.220 | 1.2996 |
| `P_prefill_64x8_q1_n0` | on | 45.304 | 43.888 | 1.0323 |
| `P_prefill_64x8_q1_n1` | on | 45.736 | 44.287 | 1.0327 |
| `P_prefill_64x8_q1_n2` | on | 45.641 | 44.303 | 1.0302 |
| `P_prefill_64x8_q2_n0` | on | 45.209 | 43.889 | 1.0301 |
| `P_prefill_64x8_q2_n1` | on | 45.533 | 44.094 | 1.0326 |
| `P_prefill_64x8_q2_n2` | on | 45.496 | 44.161 | 1.0302 |
| `E_prefill_8x1_q127` | on | 7.199 | 6.816 | 1.0562 |
| `E_prefill_8x1_q128` | on | 7.232 | 6.848 | 1.0561 |
| `E_prefill_8x1_q129` | on | 7.383 | 6.864 | 1.0756 |
| `E_prefill_64x8_q127` | off | 74.703 | 74.521 | 1.0024 |
| `E_prefill_64x8_q128` | off | 74.455 | 74.666 | 0.9972 |
| `E_prefill_64x8_q129` | off | 68.831 | 68.848 | 0.9998 |
| `X_decode_8x1_B1_q1_n2` | on | 6.400 | 4.960 | 1.2903 |
| `X_decode_8x1_B128_q1_n2` | on | 7.168 | 6.013 | 1.1921 |
| `X_decode_8x1_B256_q1_n2` | on | 7.712 | 7.584 | 1.0169 |
| `X_prefill_8x1_B1_Q1024_q1_n2` | on | 8.768 | 7.967 | 1.1005 |
| `X_decode_64x8_B1_q1_n2` | on | 39.783 | 39.392 | 1.0099 |
| `X_decode_64x8_B128_q1_n2` | on | 47.944 | 46.672 | 1.0273 |
| `X_decode_64x8_B256_q1_n2` | off | 56.305 | 56.348 | 0.9992 |
| `X_prefill_64x8_B1_Q1024_q1_n2` | off | 114.452 | 114.287 | 1.0014 |
| `X_decode_8x1_q1_n2_page16` | on | 6.624 | 5.312 | 1.2470 |
| `X_decode_8x1_q1_n2_page128` | on | 6.661 | 5.312 | 1.2540 |
| `X_decode_8x1_q1_n2_ctx32768` | on | 6.663 | 5.311 | 1.2546 |
| `X_prefill_8x1_ragged_q1_n2` | on | 6.816 | 5.567 | 1.2244 |
| `X_decode_8x1_q1_n2_outkv` | on | 6.592 | 5.088 | 1.2956 |
| `X_prefill_8x1_q1_n2_maxseq1024` | on | 6.890 | 5.375 | 1.2819 |

BF16 (`cake_fused_qk_rope_append`)

| shape | PDL | FlashInfer main (µs) | this PR (µs) | speedup |
|---|---|---:|---:|---:|
| `M1` 8/1, 32 req x 1 new, ctx 2048, page 64, n2 | on | 6.311 | 5.024 |
1.2562 |
| `M1a` 8/1, 32 req x 1 new, ctx 2048, page 64, n0 | on | 6.261 | 5.105
| 1.2264 |
| `M1b` 8/1, 32 req x 1 new, ctx 2048, page 64, n1 | on | 6.337 | 5.088
| 1.2455 |
| `M2` 8/1, 8 req x 16 new, ctx 2048, page 64, n2 | on | 6.633 | 5.407 |
1.2267 |
| `M2a` 8/1, 8 req x 16 new, ctx 2048, page 64, n0 | on | 7.105 | 5.729
| 1.2402 |
| `M2b` 8/1, 8 req x 16 new, ctx 2048, page 64, n1 | on | 7.120 | 5.832
| 1.2209 |
| `H1` 64/8, 32 req x 1 new, ctx 2048, page 64, n2 | on | 11.577 |
10.848 | 1.0672 |
| `H2` 64/8, 8 req x 16 new, ctx 2048, page 64, n2 | on | 12.385 |
11.712 | 1.0575 |
| `H3` 64/8, 128 req x 1 new, ctx 2048, page 64, n2 | on | 12.616 |
11.968 | 1.0541 |
| `H4` 64/8, 1 req x 128 new, ctx 2048, page 64, n2 | on | 12.358 |
11.665 | 1.0594 |
| `D1` 8/1, 1 req x 1 new, ctx 2048, page 64, n2 | on | 6.520 | 4.881 |
1.3358 |
| `D2` 8/1, 8 req x 1 new, ctx 2048, page 64, n2 | on | 6.512 | 4.976 |
1.3087 |
| `D3` 8/1, 128 req x 1 new, ctx 2048, page 64, n2 | on | 6.824 | 6.193
| 1.1019 |
| `D4` 8/1, 256 req x 1 new, ctx 2048, page 64, n2 | on | 7.392 | 6.707
| 1.1021 |
| `P1` 8/1, 1 req x 128 new, ctx 2048, page 64, n2 | on | 6.625 | 5.376
| 1.2323 |
| `P2` 8/1, 4 req x 64 new, ctx 2048, page 64, n2 | on | 6.657 | 5.568 |
1.1956 |
| `P3` 8/1, 32 req x 8 new, ctx 2048, page 64, n2 | on | 6.792 | 5.952 |
1.1411 |
| `E1` 8/1, 32 req x 1 new, ctx 2048, page 16, n2 | on | 6.114 | 4.873 |
1.2547 |
| `E2` 8/1, 32 req x 1 new, ctx 2048, page 128, n2 | on | 6.384 | 5.280
| 1.2091 |
| `E3` 8/1, 32 req x 1 new, ctx 0, page 64, n2 | on | 6.240 | 4.960 |
1.2581 |
| `E4` 8/1, 8 req x 16 new, ctx 2047, page 64, n2 | on | 6.624 | 5.376 |
1.2321 |
| `E5` 8/1, 32 req x 1 new, ctx 2048, page 64, n2, outkv | on | 6.465 |
5.184 | 1.2471 |
| `E6` 8/1, 16 req ragged (1-64 new, 0-4095 cached), page 64, n2 | on |
7.361 | 5.972 | 1.2326 |
| `X1` 8/1, 32 req x 1 new, ctx 32768, page 64, n2 | on | 6.336 | 5.082
| 1.2468 |
| `X2` 8/1, 512 req x 1 new, ctx 2048, page 64, n2 | off | 8.639 | 8.648
| 0.9990 |
| `X3` 64/8, 32 req x 1 new, ctx 2048, page 64, n0 | on | 11.704 |
10.952 | 1.0687 |
| `X4` 64/8, 32 req x 1 new, ctx 2048, page 64, n1 | on | 11.717 |
10.912 | 1.0738 |
| `X5` 8/1, 32 req x 1 new, ctx 2048, page 32, n2 | on | 6.297 | 4.917 |
1.2807 |


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added opt-in Programmatic Dependent Launch (PDL) support to fused QK
RoPE append operations, including FP8 variants. PDL is used only for
supported hardware and workloads; it remains disabled by default.
* Added persistent-work execution paths for selected FP8 prefill
workloads.
* **Documentation**
* Clarified launch behavior, input readiness requirements, and that
enabling PDL preserves bitwise-identical outputs.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [f6b47a5](https://github.com/flashinfer-ai/flashinfer/commit/f6b47a55d9c5412af80b8b4711c4a8540a7c8e34)

- **作者**: eigen
- **时间**: 2026-10-31T15:00:06Z
- **提交信息**: perf(cake_kimi_k3_fp8_projection): SM100a tail-N-split GEMM for TP8 o_proj (#8111)

### [35be896](https://github.com/flashinfer-ai/flashinfer/commit/35be896095d5ef6057dae2d4ac67f0f73dc80ef3)

- **作者**: eigen
- **时间**: 2026-10-31T14:58:40Z
- **提交信息**: perf(cake_tinygemm2_tcgen05): add sm_107a routing windows for 9-16-row unbiased GEMMs with 4097-16384 outputs (#8110)

### [96ca3d0](https://github.com/flashinfer-ai/flashinfer/commit/96ca3d014b29f8e07b5215a98f65256ad4d62b69)

- **作者**: eigen
- **时间**: 2026-10-31T13:53:39Z
- **提交信息**: fix(cake_lm_head_det_loss): never leave a dX K-slice without a K step (#8108)

## Summary

When the vocabulary size is 256, the deterministic chunked LM-head + loss backend (`flashinfer.experimental.cake_lm_head_det_loss`) can return a wrong hidden-state gradient (dX). The K-sliced dX GEMM runs `V / 64` K steps, giving each slice `ceil(k_iters / S)` of them. At V = 256 there are 4 K steps, so 3 slices split them 2, 2, 0. The last slice runs no MMA but still stores its uninitialized accumulator into its FP32 partial-sum slab. The slab reduction then adds that tile into dX. The slice-count rule does not see V, so the default plan hits this whenever it picks 3 slices. One example is T = 1000, H = 6144 on 148-SM (B200) and 152-SM (GB300) devices. An explicit `gemm_tuning={"dx": {"k_slices": 3}}` at V = 256 was also accepted. At T = 4097 the default plan is [4, 3], which leaves the last slice of the 1-row tail chunk empty. That result is undefined, but we did not observe a wrong value there. Only V = 256 with 3 dX slices is affected, and it reaches `chunked_lm_head_det_loss` (ce and policy), `chunked_lm_head_det_logprob` and the `prepare_lm_head_det_loss` runners. Only dX is wrong: loss, logp and dW are identical before and after the fix.

The fix:
- **Slice counts are fitted.** `dx_slices_fit` lowers each count to the largest value at or below the request where every slice holds at least one K step. Every planner passes V to it. At V = 256 this turns 3 into 2, so T = 1000 plans [2] and T = 4097 plans [4, 2].
- **Bad pins raise.** An explicit `k_slices` pin that would leave a slice empty raises `ValueError`.
- **Launch-time guard.** `gemm_scalars` rejects launch scalars with an empty slice.

There is no device code change, and plans with V >= 512 are unchanged.

## Observed dX error

dX rel-L2 against an FP64 oracle, T = 1000, H = 6144, V = 256, default plan, ce / policy / logprob. For reference, the unchunked BF16 baseline is about 2.3e-3 to 2.6e-3.

| | B200 (148 SMs) | GB300 (152 SMs) |
| -- | -- | -- |
| before (plan [3]) | 0.682 / 0.688 / 0.682 | 0.694 / 0.692 / 0.696 |
| after (plan [2]) | 2.565e-3 / 2.523e-3 / 2.317e-3 | 2.556e-3 / 2.474e-3 / 2.361e-3 |

## Unchanged behaviour

On B200 and GB300, loss, logp, dX and dW are bitwise identical to main on all 58 rows (37 representative shapes plus 21 support rows). Every plan other than the six V = 256 plans fixed here is also identical, so their performance does not change.

## Tests

`tests/experimental/test_cake_lm_head_loss.py` gets 14 new tests: two host tests covering the slice fit, the planner rule and the pin, plus a 12-case device test at V = 256. All 14 fail on main and pass with this change on both B200 and GB300.


<!-- This is an auto-generated comment: release notes by coderabbit.ai -->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
  * dX calculations now limit K-slice counts to the available K steps, preventing slices with no work.
  * Explicitly pinned slice counts that exceed the available K steps now raise an error; valid pinned counts remain supported.
  * Automatic slice recommendations account for vocabulary size, including when planning workspace requirements.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [d29e16a](https://github.com/flashinfer-ai/flashinfer/commit/d29e16ae7261f8c16fb2cc717490cebf9c05a8bd)

- **作者**: eigen
- **时间**: 2026-10-31T12:31:07Z
- **提交信息**: perf(cake_causal_conv1d_det): add opt-in bwd_grid_mult backward split with grad (#8104)

`flashinfer.cake_causal_conv1d_det_train` provides deterministic packed
depthwise causal conv1d + SiLU training forward and backward. Bias is
optional, and the backward has three routes: FP32 taps with BF16-stored
dweight (`bwd`), BF16 taps (`bwd_dt`) and the FP32 weight-gradient
option (`bwd_fp32g`). Part of #7548: while any kernel is resident on
another stream, the backward runs at about 1.4x its isolated time
because its static token partition ends with a late second wave. This PR
adds the issue author's chosen option, a keyword-only `bwd_grid_mult:
int = 1` (1, 2, 3 or 4) that splits that partition into k times more
pieces. The default of 1 keeps today's program, launch and output bits.
With k > 1, y and dx stay bitwise unchanged. dweight/dbias use a
different fixed summation order that is bitwise reproducible from run to
run, including with side-stream kernels resident. Their low-order bits
differ from k = 1, and their accuracy against an FP64 reference is of
the same order. The setting is opt-in because it is a trade-off. In the
tables below, k > 1 runs at 1.06x-1.43x of the default with a 1-thread
side kernel and at 0.92x-1.15x with a 32-CTA side kernel. With no side
kernel it runs at 0.77x-1.00x.

Each table's baseline is the default `bwd_grid_mult=1`, measured on the
same GPU in the same session. All timings are medians of interleaved
blocks.

**B200 (sm_100a), CUDA 13.4.** Backward latency in ms; in parentheses
the speedup over the default `bwd_grid_mult=1` under the same side load.

| shape | side load | k=1 (default) | k=2 | k=3 | k=4 |
|---|---|---:|---:|---:|---:|
| S 261393 C 512 taps f32 policy fp32 (route bwd_fp32g) | no side kernel
| 0.1608 | 0.1731 (0.93x) | 0.1853 (0.87x) | 0.2019 (0.80x) |
| S 261393 C 512 taps f32 policy fp32 (route bwd_fp32g) | 1-thread side
kernel | 0.2284 | 0.2057 (1.11x) | 0.2018 (1.13x) | 0.2120 (1.08x) |
| S 261393 C 512 taps f32 policy fp32 (route bwd_fp32g) | 32 CTAs x 640
threads side kernel | 0.2326 | 0.2345 (0.99x) | 0.2282 (1.02x) | 0.2488
(0.93x) |
| S 262144 C 1280 taps bf16 policy bf16 (route bwd_dt) | no side kernel
| 0.3779 | 0.3840 (0.98x) | 0.3901 (0.97x) | 0.4004 (0.94x) |
| S 262144 C 1280 taps bf16 policy bf16 (route bwd_dt) | 1-thread side
kernel | 0.5376 | 0.4576 (1.17x) | 0.4332 (1.24x) | 0.4290 (1.25x) |
| S 262144 C 1280 taps bf16 policy bf16 (route bwd_dt) | 32 CTAs x 640
threads side kernel | 0.5437 | 0.5355 (1.02x) | 0.4946 (1.10x) | 0.5110
(1.06x) |
| S 250340 C 512 taps f32 policy bf16 (route bwd) | no side kernel |
0.1567 | 0.1628 (0.96x) | 0.1710 (0.92x) | 0.1772 (0.88x) |
| S 250340 C 512 taps f32 policy bf16 (route bwd) | 1-thread side kernel
| 0.2181 | 0.1894 (1.15x) | 0.1863 (1.17x) | 0.1874 (1.16x) |
| S 250340 C 512 taps f32 policy bf16 (route bwd) | 32 CTAs x 640
threads side kernel | 0.2221 | 0.2202 (1.01x) | 0.2099 (1.06x) | 0.2202
(1.01x) |
| S 250340 C 2048 taps f32 policy bf16 (route bwd) | no side kernel |
0.5437 | 0.5519 (0.99x) | 0.5540 (0.98x) | 0.5642 (0.96x) |
| S 250340 C 2048 taps f32 policy bf16 (route bwd) | 1-thread side
kernel | 0.7813 | 0.6707 (1.16x) | 0.6277 (1.24x) | 0.6175 (1.27x) |
| S 250340 C 2048 taps f32 policy bf16 (route bwd) | 32 CTAs x 640
threads side kernel | 0.7956 | 0.7834 (1.02x) | 0.7117 (1.12x) | 0.7383
(1.08x) |

**GB300 (sm_103a), CUDA 13.4.** Backward latency in ms; in parentheses
the speedup over the default `bwd_grid_mult=1` under the same side load.

| shape | side load | k=1 (default) | k=2 | k=3 | k=4 |
|---|---|---:|---:|---:|---:|
| S 261393 C 512 taps f32 policy fp32 (route bwd_fp32g) | no side kernel
| 0.1451 | 0.1614 (0.90x) | 0.1686 (0.86x) | 0.1829 (0.79x) |
| S 261393 C 512 taps f32 policy fp32 (route bwd_fp32g) | 1-thread side
kernel | 0.2055 | 0.1860 (1.10x) | 0.1839 (1.12x) | 0.1901 (1.08x) |
| S 261393 C 512 taps f32 policy fp32 (route bwd_fp32g) | 32 CTAs x 640
threads side kernel | 0.2055 | 0.2126 (0.97x) | 0.2055 (1.00x) | 0.2229
(0.92x) |
| S 262144 C 1280 taps bf16 policy bf16 (route bwd_dt) | no side kernel
| 0.3376 | 0.3478 (0.97x) | 0.3549 (0.95x) | 0.3683 (0.92x) |
| S 262144 C 1280 taps bf16 policy bf16 (route bwd_dt) | 1-thread side
kernel | 0.4799 | 0.4082 (1.18x) | 0.3888 (1.23x) | 0.3857 (1.24x) |
| S 262144 C 1280 taps bf16 policy bf16 (route bwd_dt) | 32 CTAs x 640
threads side kernel | 0.4768 | 0.4707 (1.01x) | 0.4399 (1.08x) | 0.4533
(1.05x) |
| S 250340 C 512 taps f32 policy bf16 (route bwd) | no side kernel |
0.1399 | 0.1512 (0.93x) | 0.1574 (0.89x) | 0.1696 (0.82x) |
| S 250340 C 512 taps f32 policy bf16 (route bwd) | 1-thread side kernel
| 0.2014 | 0.1798 (1.12x) | 0.1738 (1.16x) | 0.1819 (1.11x) |
| S 250340 C 512 taps f32 policy bf16 (route bwd) | 32 CTAs x 640
threads side kernel | 0.2024 | 0.2065 (0.98x) | 0.1963 (1.03x) | 0.2126
(0.95x) |
| S 250340 C 2048 taps f32 policy bf16 (route bwd) | no side kernel |
0.4912 | 0.4891 (1.00x) | 0.5076 (0.97x) | 0.5147 (0.95x) |
| S 250340 C 2048 taps f32 policy bf16 (route bwd) | 1-thread side
kernel | 0.7072 | 0.5915 (1.20x) | 0.5628 (1.26x) | 0.5526 (1.28x) |
| S 250340 C 2048 taps f32 policy bf16 (route bwd) | 32 CTAs x 640
threads side kernel | 0.7021 | 0.6908 (1.02x) | 0.6315 (1.11x) | 0.6519
(1.08x) |

**R200 (sm_107a), CUDA 13.4.** Backward latency in ms; in parentheses
the speedup over the default `bwd_grid_mult=1` under the same side load.
The R200 has 212 SMs.

| shape | side load | k=1 (default) | k=2 | k=3 | k=4 |
|---|---|---:|---:|---:|---:|
| S 261393 C 512 taps f32 policy fp32 (route bwd_fp32g) | no side kernel
| 0.1008 | 0.1113 (0.91x) | 0.1170 (0.86x) | 0.1265 (0.80x) |
| S 261393 C 512 taps f32 policy fp32 (route bwd_fp32g) | 1-thread side
kernel | 0.1589 | 0.1114 (1.43x) | 0.1348 (1.18x) | 0.1268 (1.25x) |
| S 261393 C 512 taps f32 policy fp32 (route bwd_fp32g) | 32 CTAs x 640
threads side kernel | 0.1611 | 0.1412 (1.14x) | 0.1479 (1.09x) | 0.1515
(1.06x) |
| S 262144 C 1280 taps bf16 policy bf16 (route bwd_dt) | no side kernel
| 0.2093 | 0.2189 (0.96x) | 0.2253 (0.93x) | 0.2327 (0.90x) |
| S 262144 C 1280 taps bf16 policy bf16 (route bwd_dt) | 1-thread side
kernel | 0.2990 | 0.2572 (1.16x) | 0.2478 (1.21x) | 0.2469 (1.21x) |
| S 262144 C 1280 taps bf16 policy bf16 (route bwd_dt) | 32 CTAs x 640
threads side kernel | 0.3006 | 0.2625 (1.15x) | 0.2753 (1.09x) | 0.2732
(1.10x) |
| S 250340 C 512 taps f32 policy bf16 (route bwd) | no side kernel |
0.0887 | 0.1005 (0.88x) | 0.1068 (0.83x) | 0.1153 (0.77x) |
| S 250340 C 512 taps f32 policy bf16 (route bwd) | 1-thread side kernel
| 0.1289 | 0.1176 (1.10x) | 0.1073 (1.20x) | 0.1211 (1.06x) |
| S 250340 C 512 taps f32 policy bf16 (route bwd) | 32 CTAs x 640
threads side kernel | 0.1308 | 0.1194 (1.10x) | 0.1302 (1.00x) | 0.1348
(0.97x) |

Legend: S = packed token count, C = channel count, taps f32/bf16 = conv
weight dtype, policy fp32 = FP32 weight-gradient output option, policy
bf16 = BF16-stored weight gradient, route = backward path.

The kernel also has a KCP (context-parallel) variant,
`flashinfer.cake_causal_conv1d_det_train_kcp`, and the package ships on
sm_100a, sm_103a and sm_107a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added an optional backward grid multiplier from 1 to 4 for causal
convolution training, available through the API and benchmark.
* The default remains 1. Higher values use more partial rows for weight
and bias gradients; input gradients remain bitwise identical to the
default, while weight and bias gradients may differ in their final bits.
* Backward workspace sizing supports the selected multiplier; provide a
workspace sized for the same or a larger value.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [fec6b56](https://github.com/flashinfer-ai/flashinfer/commit/fec6b5698fba1f273035fbbea37fd5b6b6bcad37)

- **作者**: eigen
- **时间**: 2026-10-31T11:32:44Z
- **提交信息**: perf(cake_deepgemm_mega_mhc): fast coefficient chain for sm_107a UE8M0/NVFP4 tailpipes (#8105)

`flashinfer.mega_mhc` (`prepare_mega_mhc`) runs the fused
manifold-constrained hyper-connection (mHC) inference step. FlashInfer
main ships 39 per-arch programs for it:

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
- Two sm_107a-only fast-chain forms: one of the BF16-output tailpipe
program and one of the FP8 group-128 weight-staging tailpipe program
(raw scale mode).

This PR adds two sm_107a programs, which brings main to 41. It also adds
loader routes to them. The existing programs do not change.

- **Fast-chain form of the FP8 group-128 tailpipe program, UE8M0 scale
mode.** It serves non-deterministic UE8M0-scale-mode launches with T =
385–832. In the tables below, that covers T = 512.
- **Fast-chain form of the NVFP4 tailpipe program.** It serves
non-deterministic NVFP4-output launches with T = 833–1008.

Every other launch keeps the program main dispatches. That includes
UE8M0-scale-mode tailpipe launches with T = 1281–3328 on 208 SMs and T =
1345–3456 on 216 SMs. It also includes NVFP4 tailpipe launches with T =
1009–3328 on 208 SMs and T = 1009–3456 on 216 SMs, and all deterministic
launches.

The two new programs compute the coefficient chain (the sigmoid, softmax
and Sinkhorn quotients) with the same fast, correctly rounded division
that the other sm_107a fast-chain programs on main use, and fall back to
IEEE division when an operand is out of range. Every quotient therefore
equals IEEE round-to-nearest division, and outputs are bitwise identical
to main.

The baseline is the previous Cake version of the kernel, which is what
FlashInfer main dispatches today. A is the program main dispatches, and
B is the program this PR dispatches. Speedup = A / B. Both sides run
through FlashInfer's loader on the same GPU with the same inputs in one
process. Both use programmatic dependent launch, as main already does.
The tables show medians.

- FP8 group-128 UE8M0 tailpipe, fast-chain form, T = 512: 1.036× on the
208-SM GPU and 1.035× on the 216-SM GPU. Across T = 385, 512 and 832 it
is 0.21–0.50 µs faster on the 208-SM GPU and 0.32–0.48 µs faster on the
216-SM GPU.
- NVFP4 tailpipe, fast-chain form: it serves T = 833–1008 and is
0.21–0.35 µs faster at T = 833 and T = 1008 on both GPUs. No owner row
falls in that range, so every row in the NVFP4 tables keeps its program.
- Rows that keep their program: 0.998–1.003× on the 208-SM GPU and
0.994–1.006× on the 216-SM GPU.

**FP8 group-128 output, UE8M0 scale mode, hidden 4096. NVIDIA R200
(sm_107a), 208 SMs, driver 615.71.10, CUDA 13.4 (nvcc 13.4.92), SM clock
2390–2412 MHz.**

| T (tokens) | Program dispatched by this PR | Splits | Previous
program, µs (A) | This PR, µs (B) | Speedup (A / B) |
|---:|:--|---:|---:|---:|---:|
| 1 | FP8 group-128 UE8M0 | 64 | 9.056 | 9.032 | 1.003× |
| 4 | FP8 group-128 UE8M0 | 64 | 9.224 | 9.200 | 1.003× |
| 8 | FP8 group-128 UE8M0 | 64 | 9.312 | 9.304 | 1.001× |
| 16 | FP8 group-128 UE8M0 | 64 | 9.399 | 9.376 | 1.002× |
| 32 | FP8 group-128 UE8M0 | 64 | 9.408 | 9.408 | 1.000× |
| 64 | FP8 group-128 UE8M0 | 64 | 9.856 | 9.864 | 0.999× |
| 128 | FP8 group-128 UE8M0 | 64 | 10.464 | 10.464 | 1.000× |
| 256 | FP8 group-128 UE8M0 | 32 | 12.096 | 12.080 | 1.001× |
| 512 | tailpipe (fast-chain form) | 22 | 14.392 | 13.888 | 1.036× |
| 1024 | FP8 group-128 UE8M0 | 13 | 19.616 | 19.616 | 1.000× |
| 2048 | tailpipe | 13 | 29.744 | 29.792 | 0.998× |
| 4096 | tailpipe (weight staged) | 16 | 56.616 | 56.664 | 0.999× |
| 8192 | tailpipe (weight staged) | 8 | 112.608 | 112.639 | 1.000× |

**NVFP4 output, hidden 4096. NVIDIA R200 (sm_107a), 208 SMs, driver
615.71.10, CUDA 13.4 (nvcc 13.4.92), SM clock 2389–2412 MHz.**

| T (tokens) | Program dispatched by this PR | Splits | Previous
program, µs (A) | This PR, µs (B) | Speedup (A / B) |
|---:|:--|---:|---:|---:|---:|
| 1 | NVFP4 | 64 | 8.752 | 8.744 | 1.001× |
| 4 | NVFP4 | 64 | 8.608 | 8.608 | 1.000× |
| 8 | NVFP4 | 64 | 8.840 | 8.848 | 0.999× |
| 16 | NVFP4 | 64 | 8.888 | 8.872 | 1.002× |
| 32 | NVFP4 | 64 | 9.056 | 9.056 | 1.000× |
| 64 | NVFP4 | 64 | 9.424 | 9.424 | 1.000× |
| 128 | NVFP4 | 64 | 10.176 | 10.176 | 1.000× |
| 256 | NVFP4 | 32 | 11.712 | 11.696 | 1.001× |
| 512 | NVFP4 | 22 | 14.288 | 14.272 | 1.001× |
| 1024 | tailpipe | 13 | 18.472 | 18.448 | 1.001× |
| 2048 | tailpipe | 13 | 28.992 | 28.976 | 1.001× |
| 4096 | tailpipe (weight staged) | 16 | 55.328 | 55.312 | 1.000× |
| 8192 | tailpipe (weight staged) | 8 | 110.896 | 110.888 | 1.000× |

**FP8 group-128 output, UE8M0 scale mode, hidden 4096. NVIDIA R200
(sm_107a), 216 SMs, driver 615.71.10, CUDA 13.4 (nvcc 13.4.92), SM clock
2383–2411 MHz.**

| T (tokens) | Program dispatched by this PR | Splits | Previous
program, µs (A) | This PR, µs (B) | Speedup (A / B) |
|---:|:--|---:|---:|---:|---:|
| 1 | FP8 group-128 UE8M0 | 64 | 9.288 | 9.344 | 0.994× |
| 4 | FP8 group-128 UE8M0 | 64 | 9.280 | 9.248 | 1.003× |
| 8 | FP8 group-128 UE8M0 | 64 | 9.504 | 9.504 | 1.000× |
| 16 | FP8 group-128 UE8M0 | 64 | 9.120 | 9.144 | 0.997× |
| 32 | FP8 group-128 UE8M0 | 64 | 9.344 | 9.344 | 1.000× |
| 64 | FP8 group-128 UE8M0 | 64 | 9.632 | 9.632 | 1.000× |
| 128 | FP8 group-128 UE8M0 | 64 | 10.272 | 10.272 | 1.000× |
| 256 | FP8 group-128 UE8M0 | 32 | 11.904 | 11.904 | 1.000× |
| 512 | tailpipe (fast-chain form) | 22 | 14.208 | 13.728 | 1.035× |
| 1024 | FP8 group-128 UE8M0 | 13 | 19.264 | 19.264 | 1.000× |
| 2048 | tailpipe | 13 | 28.608 | 28.640 | 0.999× |
| 4096 | tailpipe (weight staged) | 16 | 54.144 | 54.112 | 1.001× |
| 8192 | tailpipe (weight staged) | 8 | 109.744 | 109.760 | 1.000× |

**NVFP4 output, hidden 4096. NVIDIA R200 (sm_107a), 216 SMs, driver
615.71.10, CUDA 13.4 (nvcc 13.4.92), SM clock 2381–2413 MHz.**

| T (tokens) | Program dispatched by this PR | Splits | Previous
program, µs (A) | This PR, µs (B) | Speedup (A / B) |
|---:|:--|---:|---:|---:|---:|
| 1 | NVFP4 | 64 | 8.448 | 8.448 | 1.000× |
| 4 | NVFP4 | 64 | 8.608 | 8.608 | 1.000× |
| 8 | NVFP4 | 64 | 8.680 | 8.672 | 1.001× |
| 16 | NVFP4 | 64 | 8.864 | 8.864 | 1.000× |
| 32 | NVFP4 | 64 | 9.056 | 9.024 | 1.004× |
| 64 | NVFP4 | 64 | 9.376 | 9.345 | 1.003× |
| 128 | NVFP4 | 64 | 9.920 | 9.920 | 1.000× |
| 256 | NVFP4 | 32 | 11.616 | 11.608 | 1.001× |
| 512 | NVFP4 | 22 | 13.944 | 13.864 | 1.006× |
| 1024 | tailpipe | 13 | 18.208 | 18.200 | 1.000× |
| 2048 | tailpipe | 13 | 28.016 | 28.032 | 0.999× |
| 4096 | tailpipe (weight staged) | 16 | 53.392 | 53.408 | 1.000× |
| 8192 | tailpipe (weight staged) | 8 | 108.248 | 108.271 | 1.000× |

All other programs are unchanged and keep their routes: the BF16-output
and FP8 group-128 raw-scale-mode programs (including the existing
fast-chain and fast-division forms), the existing UE8M0-scale-mode and
NVFP4 programs, the hidden-5120 programs and every sm_100a and sm_103a
program. The family ships on sm_107a, sm_100a and sm_103a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added additional execution paths for hidden-4096 workloads on
supported SM107a hardware. These cover FP8 output for launches with
385–832 tokens and NVFP4 output for launches with 833–1008 tokens when
deterministic execution is not requested.
  * Existing routes remain in place for other launch configurations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery Huang <averyh@nvidia.com>

### [fc6d231](https://github.com/flashinfer-ai/flashinfer/commit/fc6d231178b858461a19c9c9dee253bbb880ee26)

- **作者**: eigen
- **时间**: 2026-10-31T11:09:49Z
- **提交信息**: fix(cake_mhc): no default mHC workspace allocation during CUDA graph capture (#8100)

Follow-up to #8092, addressing two review comments on it.

## What

- `_default_workspace` in
`flashinfer/experimental/cake/cake_mhc_train_backend/__init__.py` now
raises `ValueError` on a cache miss while the current stream is
capturing a CUDA graph. Before this change it allocated with
`torch.zeros`. This function provides the per-device default buffer used
when a call passes `workspace=None`, with one buffer per kernel kind and
power-of-two token-count bucket. The error caches nothing, and the next
eager call allocates the zeroed buffer. The cache-hit path is unchanged.
- The module docstring of `flashinfer.experimental.cake.cake_mhc_train`
and `docs/api/mhc.rst` now state that:
- The default workspaces of both packages are one buffer per device and
token-count bucket. Every stream and graph replay on the device shares
that buffer, so calls that can run concurrently on different streams
should pass caller-owned workspaces.
- `deterministic=False` creates no default buffer during a capture. Warm
up first with the same `deterministic` value and token count.
- Companions are allocated zeroed outside any capture, and every
completed launch leaves their ticket words at zero, so they need no
reset. `cake_mhc_train_reset_workspace` zeroes the buffer it is given.
- Adds `test_default_workspace_is_not_created_during_capture` to
`tests/experimental/test_cake_mhc_train_workspace.py`.

## Why

During a CUDA graph capture the `torch.zeros` fill is only recorded, so
the cached default buffer could hold non-zero ticket words until the
first replay. An eager call on that bucket before a replay could read
them. Raising instead matches the facade's deterministic-fallback
companions, which already raise in this situation. This PR doesn't key
the default buffers by stream: the deterministic package
(`flashinfer.cake_mhc_det_train_backend`) uses the same default-buffer
design and backs the facade's default `deterministic=True` path, so a
stream-keyed default needs changes in both packages and is left for a
separate PR.

## Tests

- `test_default_workspace_is_not_created_during_capture` runs in a fresh
subprocess at T=300. A call on a caller-owned workspace loads the
kernels. The same call with `workspace=None` inside `torch.cuda.graph`
raises `ValueError` and caches nothing. The next eager call caches the
bucket buffer and returns dX, dscale and dbase bitwise equal to the
caller-owned call.
- On B200 (sm_100a), the 13-file mHC test set (the 6
`tests/experimental/test_cake_mhc_train*.py` files and the 7
deterministic mHC files) passed 550/550.
- On B200 (sm_100a), the workspace, rules and API test files passed
83/83.
- pre-commit passed.

Targeted tests: `tests/experimental/test_cake_mhc_train_workspace.py
tests/experimental/test_cake_mhc_train_api.py
tests/experimental/test_cake_mhc_train_rules.py`


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Documentation**
* Clarified that default workspaces are shared across streams and graph
replays for each device and token-count bucket. Concurrent calls on
different streams should use caller-owned workspaces.
* Documented that a missing default workspace cannot be created during
CUDA graph capture. Warm up with the same mode and token count
beforehand, or provide a caller-owned workspace.
* Clarified that companion workspaces start zeroed and reset operations
zero the supplied buffer.
* **Bug Fixes**
* Requests requiring a new default workspace during capture now raise a
clear error; existing workspaces remain usable.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [83f6dc8](https://github.com/flashinfer-ai/flashinfer/commit/83f6dc870b4f0b9f22aa02dedc9e3eb9fc5c05a4)

- **作者**: eigen
- **时间**: 2026-10-31T10:48:49Z
- **提交信息**: perf(cake_trtllm_moe_allreduce_union): one-token bf16 launches at world size 2 on SM103 run the fence-warp program (#8102)

The Cake MoE all-reduce fusion union,
`flashinfer.comm.trtllm_moe_allreduce_fusion(..., backend="cake")`, does
four things in one call: the MoE finalize reduction (the scaled sum of
the active experts' outputs plus the shared token input), the all-reduce
across ranks, the residual add and RMSNorm. The union has 12 variants: 2
data types (bf16, fp16) x 3 world sizes (2, 4, 8) x PDL launch on/off.
This PR changes one-token bf16 calls with 8 active experts and PDL off
at world size 2 on sm_103a. The baseline is the previous Cake version of
this kernel, flashinfer-ai/flashinfer#8062, which this PR builds on.
#8062 added a bf16 latency program for 1-32 tokens with one extra warp
that waits for the block's publish to the peer ranks and then issues a
system-scope fence. It routed one-token bf16 8-expert PDL-off calls to
that program on sm_100a at world sizes 2, 4 and 8 and on sm_103a at
world sizes 4 and 8. This PR also routes world size 2 on sm_103a to the
fence-warp program, and the world-size-2 fence-warp program is now built
for sm_103a as well as sm_100a. Calls with 2 to 32 tokens keep the
previous program. Outputs are bitwise identical to #8062. Every other
program compiles to the same machine code as #8062. Routing and machine
code on sm_100a are unchanged, so B200 latency is unchanged from #8062;
it was not re-measured, and the table below covers B300 only. Of the 30
measured shapes, the world-size-2 one-token bf16 8-expert PDL-off row
runs the new routing and goes from 7.73 to 7.49 µs (1.0267x). The other
29 rows run the same machine code as #8062 and measure 0.9919x-1.0100x.

Median latency per call in µs at hidden size 7168 for the previous Cake
union (#8062) and this PR on NVIDIA B300 SXM6 AC (sm_103a) with CUDA
13.4, where speedup is the geometric mean of the per-run ratios. The
one-token bf16 8-expert rows are from 32 runs and the other rows are
from 8 runs.

| World size | dtype | Tokens | Active experts | PDL | B300 previous
(µs) | B300 this PR (µs) | B300 speedup |
|---:|---|---:|---:|---|---:|---:|---:|
| 2 | bf16 | 1 | 8 | off | 7.73 | 7.49 | 1.0267x |
| 2 | bf16 | 64 | 8 | on | 12.88 | 12.80 | 1.0044x |
| 2 | bf16 | 128 | 16 | off | 16.72 | 16.70 | 1.0041x |
| 2 | bf16 | 256 | 12 | on | 21.44 | 21.46 | 1.0022x |
| 2 | bf16 | 256 | 8 | off | 19.01 | 18.98 | 0.9966x |
| 2 | bf16 | 2048 | 12 | on | 109.98 | 110.05 | 1.0000x |
| 2 | fp16 | 64 | 12 | off | 12.58 | 12.56 | 0.9963x |
| 2 | fp16 | 128 | 16 | on | 16.88 | 16.72 | 1.0100x |
| 2 | fp16 | 2048 | 16 | on | 128.40 | 128.40 | 0.9997x |
| 2 | fp16 | 2048 | 8 | off | 88.96 | 89.01 | 0.9994x |
| 4 | bf16 | 1 | 8 | off | 7.36 | 7.42 | 0.9919x |
| 4 | bf16 | 64 | 8 | on | 14.21 | 14.21 | 0.9975x |
| 4 | bf16 | 128 | 16 | off | 19.10 | 19.04 | 1.0021x |
| 4 | bf16 | 256 | 12 | on | 26.02 | 26.02 | 1.0005x |
| 4 | bf16 | 256 | 8 | off | 23.23 | 23.14 | 1.0038x |
| 4 | bf16 | 2048 | 12 | on | 113.28 | 113.43 | 0.9992x |
| 4 | fp16 | 64 | 12 | off | 14.78 | 14.62 | 1.0077x |
| 4 | fp16 | 128 | 16 | on | 19.02 | 18.91 | 1.0031x |
| 4 | fp16 | 2048 | 16 | on | 134.13 | 134.14 | 1.0002x |
| 4 | fp16 | 2048 | 8 | off | 97.81 | 97.79 | 1.0000x |
| 8 | bf16 | 1 | 8 | off | 8.00 | 8.03 | 0.9976x |
| 8 | bf16 | 64 | 8 | on | 15.84 | 15.89 | 0.9983x |
| 8 | bf16 | 128 | 16 | off | 20.05 | 20.10 | 0.9982x |
| 8 | bf16 | 256 | 12 | on | 27.62 | 27.68 | 1.0001x |
| 8 | bf16 | 256 | 8 | off | 24.82 | 24.90 | 0.9990x |
| 8 | bf16 | 2048 | 12 | on | 121.81 | 121.95 | 1.0000x |
| 8 | fp16 | 64 | 12 | off | 15.89 | 15.79 | 1.0048x |
| 8 | fp16 | 128 | 16 | on | 20.19 | 20.24 | 0.9986x |
| 8 | fp16 | 2048 | 16 | on | 136.59 | 136.69 | 0.9997x |
| 8 | fp16 | 2048 | 8 | off | 105.09 | 105.04 | 1.0004x |

The other Cake kernel for this operation is the MoE finalize all-reduce
fusion, `flashinfer.comm.trtllm_moe_finalize_allreduce_fusion(...,
backend="cake")`; the union supports bf16 and fp16 at hidden size 7168
with no quantized outputs and ships only on sm_100a and sm_103a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* Updated routing for one-token, bfloat16 communication on supported
hardware to use a specialized processing path. Requests with 2–32 tokens
continue to use the existing path.
* Added architecture-specific handling for normalization calculations in
the specialized path.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery Huang <averyh@nvidia.com>

### [7aef24a](https://github.com/flashinfer-ai/flashinfer/commit/7aef24a43046f19f5cb631a89b5ccccfdb714fb9)

- **作者**: eigen
- **时间**: 2026-10-31T10:28:42Z
- **提交信息**: perf(cake_fmha): multi-wave and short-KV one-stage FP8 paged context programs (#8101)

Cake paged context (prefill) attention in `flashinfer.cake_fmha` has
three variants by data type, all on a paged KV cache: BF16, FP8 (FP8
Q/K/V with FP8 output), and FP8 Q with NVFP4 KV. This PR changes only
the FP8 variant and measures it against the previous Cake version on
FlashInfer main. The page-64 one-stage programs (one query stage per
tile) now use a short-KV build. On sm_100a (B200), some launches routed
to the pack-1 and pack-2 page-64 one-stage programs now run a multi-wave
build instead: those with more than 64 tiles and a maximum KV length of
at most 384. This build compiles to the same code as the previous
version's program. One-stage programs are ranked by tile query rows, and
exact-size calls can also take a one-stage program. On sm_103a (GB300),
launches of at most 128 keys go to one-stage programs that keep P in its
own S columns, taking the smallest pack of at most 64 tiles. The 44
tracked shapes do not change on either GPU. None is slower than before,
the largest median speedup is 1.003x, and all 44 stay faster than
trtllm-gen in every layout. The gains are on shapes with small
per-request query counts and short KV. On B200 the largest is FP8,
B=256, q=32, kv=1024, heads 32/32, page 64: 855.33 to 581.17 µs
(1.472x). The B=256 shapes that move to the multi-wave build gain 1.34x
to 1.44x. On GB300 the largest is FP8, B=1, q=32, kv=1024, heads 32/4,
page 64: 14.82 to 11.04 µs (1.342x), while the B=256 page-64 shapes are
unchanged.

Measured on NVIDIA B200 (sm_100a) and NVIDIA GB300 (sm_103a) with CUDA
13.0. Previous is the Cake version on FlashInfer main, and this PR is
the Cake programs in this branch. Times are the median over 5 memory
layouts of each layout's median of 6 rounds, with a cold L2. Speedup is
previous / this PR, as the median over layouts with the minimum layout
in parentheses. trtllm-gen is the TensorRT-LLM generated kernel on the
same shape, shown for reference.

These are the 44 shapes tracked for this kernel, across all three
variants:

| Shape (paged KV, head dim 128) | B200 previous (µs) | B200 this PR
(µs) | B200 speedup | B200 trtllm-gen (µs) | GB300 previous (µs) | GB300
this PR (µs) | GB300 speedup | GB300 trtllm-gen (µs) |
|---|---:|---:|---|---:|---:|---:|---|---:|
| BF16, B=1, q=8192, kv=8192, heads 64/8, page 16 | 897.39 | 897.42 |
1.000x (min 1.000x) | 1063.71 | 618.86 | 621.38 | 0.998x (min 0.992x) |
679.90 |
| BF16, B=4, q=511, kv=2047, heads 10/2, page 32 | 34.21 | 34.18 |
1.001x (min 0.999x) | 37.34 | 26.85 | 26.85 | 1.000x (min 1.000x) |
30.08 |
| BF16, B=128, q=64, kv=2048, heads 32/4, page 16 | 241.76 | 241.04 |
1.001x (min 0.998x) | 1010.74 | 174.42 | 174.50 | 1.000x (min 0.996x) |
713.47 |
| FP8, B=256, q=32, kv=1024, heads 32/4, page 64 | 109.73 | 109.79 |
1.000x (min 0.999x) | 770.91 | 82.83 | 82.86 | 1.000x (min 0.999x) |
513.01 |
| FP8 Q / NVFP4 KV, B=4, q=511, kv=2047, heads 32/4, page 16 | 57.66 |
57.66 | 1.000x (min 0.999x) | 62.21 | 51.46 | 51.46 | 1.000x (min
1.000x) | 52.24 |
| BF16, B=4, q=257, kv=1024, heads 10/2, page 1024 | 20.57 | 20.48 |
1.003x (min 0.995x) | 22.91 | 16.90 | 16.90 | 1.000x (min 1.000x) |
18.37 |
| FP8, B=256, q=64, kv=1024, heads 32/4, page 64 | 203.39 | 203.39 |
1.000x (min 0.999x) | 784.86 | 146.67 | 146.75 | 1.000x (min 0.999x) |
525.78 |
| FP8, B=128, q=128, kv=1024, heads 32/8, page 64 | 203.04 | 203.09 |
1.000x (min 0.999x) | 408.81 | 146.59 | 146.59 | 1.000x (min 1.000x) |
283.09 |
| FP8, B=256, q=32, kv=1024, heads 128/1, page 64 | 388.32 | 388.33 |
1.000x (min 1.000x) | 3080.60 | 268.77 | 268.82 | 1.000x (min 0.999x) |
2005.38 |
| FP8, B=16, q=256, kv=2048, heads 32/32, page 64 | 115.25 | 115.23 |
1.000x (min 1.000x) | 115.73 | 86.82 | 86.82 | 1.000x (min 0.999x) |
93.01 |
| FP8, B=256, q=32, kv=1024, heads 32/4, page 16 | 110.75 | 110.78 |
1.000x (min 0.999x) | 775.52 | 84.82 | 84.82 | 1.000x (min 0.999x) |
533.23 |
| FP8, B=256, q=32, kv=1024, heads 32/4, page 16, device scales | 110.45
| 110.49 | 1.000x (min 0.999x) | 794.27 | 84.72 | 84.74 | 1.000x (min
1.000x) | 569.95 |
| FP8, B=2, q=300, kv=1500, heads 32/4, page 16 | 25.65 | 25.65 | 1.000x
(min 1.000x) | 26.46 | 18.56 | 18.56 | 1.000x (min 1.000x) | 19.90 |
| FP8, B=256, q=32, kv=1024, heads 32/4, page 64, device scales | 109.01
| 109.05 | 0.999x (min 0.999x) | 778.83 | 82.88 | 82.88 | 1.000x (min
1.000x) | 555.22 |
| FP8 Q / NVFP4 KV, B=4, q=511, kv=2047, heads 32/4, page 16, device
scales | 58.02 | 58.02 | 1.000x (min 0.998x) | 77.90 | 51.26 | 51.30 |
1.000x (min 0.999x) | 90.18 |
| BF16, B=1, q=64, kv=16384, heads 32/4, page 16 | 195.39 | 195.39 |
1.000x (min 1.000x) | 214.91 | 157.47 | 157.47 | 1.000x (min 1.000x) |
191.17 |
| BF16, B=one wave of CTAs (18 on B200, 19 on GB300), q=64, kv=2048,
heads 32/4, page 16 | 36.83 | 36.86 | 1.000x (min 0.999x) | 133.33 |
32.77 | 32.77 | 1.000x (min 0.999x) | 108.64 |
| FP8, B=1, q=300, kv=1500, heads 32/4, page 16 | 24.38 | 24.38 | 1.000x
(min 1.000x) | 25.25 | 18.45 | 18.43 | 1.000x (min 0.999x) | 18.98 |
| FP8, B=2, q=300, kv=3000, heads 32/4, page 16 | 41.70 | 41.71 | 1.000x
(min 1.000x) | 45.70 | 31.10 | 31.10 | 1.000x (min 0.999x) | 33.20 |
| FP8, B=2, q=300, kv=6000, heads 32/4, page 16 | 72.35 | 72.29 | 1.001x
(min 1.000x) | 81.26 | 54.18 | 54.18 | 1.001x (min 1.000x) | 58.37 |
| FP8, B=2, q=128, kv=1500, heads 32/4, page 16 | 20.90 | 20.90 | 1.000x
(min 0.998x) | 24.64 | 15.78 | 15.78 | 1.000x (min 0.999x) | 18.85 |
| FP8, B=16, q=256, kv=4096, heads 32/32, page 64 | 203.65 | 203.65 |
1.000x (min 0.999x) | 218.88 | 156.75 | 156.78 | 1.000x (min 0.999x) |
169.44 |
| FP8, B=1, q=32, kv=16384, heads 32/4, page 64 | 44.38 | 44.38 | 1.000x
(min 0.999x) | 187.10 | 39.42 | 39.42 | 1.000x (min 1.000x) | 137.76 |
| FP8, B=1, q=32, kv=4096, heads 32/4, page 64 | 27.04 | 27.04 | 1.000x
(min 0.999x) | 51.36 | 23.62 | 23.62 | 1.000x (min 0.999x) | 37.86 |
| FP8, B=1, q=32, kv=8192, heads 32/4, page 64 | 33.31 | 33.31 | 1.000x
(min 1.000x) | 96.96 | 29.60 | 29.60 | 1.000x (min 0.999x) | 71.46 |
| FP8, B=1, q=32, kv=32768, heads 32/4, page 64 | 58.66 | 58.66 | 1.000x
(min 0.999x) | 366.46 | 52.64 | 52.64 | 1.000x (min 1.000x) | 271.52 |
| FP8, B=2, q=32, kv=16384, heads 32/4, page 64 | 48.45 | 48.48 | 1.000x
(min 0.999x) | 188.96 | 41.60 | 41.62 | 1.000x (min 1.000x) | 139.71 |
| FP8, B=4, q=32, kv=16384, heads 32/4, page 64 | 54.56 | 54.56 | 1.000x
(min 1.000x) | 191.62 | 48.90 | 48.90 | 1.000x (min 1.000x) | 142.59 |
| FP8, B=8, q=32, kv=8192, heads 32/4, page 64 | 47.49 | 47.47 | 1.000x
(min 1.000x) | 196.99 | 42.37 | 42.37 | 1.000x (min 1.000x) | 146.72 |
| FP8, B=1, q=128, kv=16384, heads 32/4, page 64 | 52.27 | 52.29 |
1.000x (min 1.000x) | 188.06 | 45.66 | 45.66 | 1.000x (min 1.000x) |
138.42 |
| FP8, B=1, q=512, kv=16384, heads 32/4, page 64 | 116.35 | 116.42 |
1.000x (min 0.999x) | 195.10 | 93.06 | 93.06 | 1.000x (min 1.000x) |
140.26 |
| FP8, B=2, q=300, kv=2000, heads 32/4, page 16 | 29.76 | 29.74 | 1.000x
(min 1.000x) | 33.09 | 22.78 | 22.78 | 1.000x (min 0.999x) | 24.32 |
| FP8, B=1, q=300, kv=3000, heads 32/4, page 16 | 30.94 | 30.94 | 1.000x
(min 0.999x) | 43.84 | 27.09 | 27.10 | 0.999x (min 0.999x) | 32.26 |
| FP8, B=16, q=256, kv=3072, heads 32/32, page 64 | 159.97 | 159.98 |
1.000x (min 1.000x) | 165.23 | 121.90 | 121.89 | 1.000x (min 1.000x) |
131.44 |
| FP8, B=1, q=32, kv=2048, heads 32/4, page 64 | 20.82 | 20.80 | 1.000x
(min 1.000x) | 28.29 | 18.75 | 18.75 | 1.000x (min 0.999x) | 21.06 |
| FP8, B=1, q=32, kv=12000, heads 32/4, page 64 | 39.62 | 39.62 | 1.000x
(min 0.999x) | 139.58 | 34.51 | 34.50 | 1.000x (min 1.000x) | 102.24 |
| FP8, B=3, q=32, kv=16384, heads 32/4, page 64 | 52.64 | 52.64 | 1.000x
(min 1.000x) | 189.92 | 47.62 | 47.62 | 1.000x (min 1.000x) | 141.34 |
| FP8, B=16, q=32, kv=16384, heads 32/4, page 64 | 119.87 | 119.87 |
1.000x (min 0.998x) | 757.13 | 102.06 | 102.08 | 1.000x (min 1.000x) |
543.52 |
| FP8, B=1, q=256, kv=16384, heads 32/4, page 64 | 70.98 | 71.01 |
1.000x (min 1.000x) | 193.38 | 58.59 | 58.59 | 1.000x (min 1.000x) |
139.38 |
| FP8, B=1, q=32, kv=16384, heads 32/8, page 64 | 44.96 | 44.96 | 1.000x
(min 1.000x) | 188.80 | 40.26 | 40.26 | 1.000x (min 1.000x) | 146.91 |
| FP8, B=1, q=32, kv=16384, heads 64/8, page 64 | 47.55 | 47.54 | 1.000x
(min 1.000x) | 188.35 | 41.76 | 41.76 | 1.000x (min 1.000x) | 139.55 |
| FP8, B=1, q=32, kv=16384, heads 16/2, page 64 | 42.98 | 42.99 | 1.000x
(min 0.999x) | 186.78 | 37.79 | 37.79 | 1.000x (min 1.000x) | 138.14 |
| FP8, B=1, q=32, kv=16384, heads 32/4, page 16 | 44.93 | 44.94 | 1.000x
(min 0.999x) | 189.65 | 39.74 | 39.74 | 1.000x (min 1.000x) | 143.94 |
| FP8, B=1, q=256, kv=8192, heads 32/32, page 64 | 47.23 | 47.23 |
1.000x (min 1.000x) | 103.58 | 41.81 | 41.81 | 1.000x (min 1.000x) |
81.09 |

<details><summary>FP8 sweep: 130 shapes with small per-request query
counts and short KV</summary>

On B200, 106 of the 116 shapes measured there are faster than the
previous version and 10 are unchanged; on GB300, 82 of 111 are faster
and 29 are unchanged; '-' marks a GPU on which the shape was not
measured.

| Shape (paged KV, head dim 128) | B200 previous (µs) | B200 this PR
(µs) | B200 speedup | B200 trtllm-gen (µs) | GB300 previous (µs) | GB300
this PR (µs) | GB300 speedup | GB300 trtllm-gen (µs) |
|---|---:|---:|---|---:|---:|---:|---|---:|
| FP8, B=1, q=32, kv=128, heads 32/4, page 64 | 8.00 | 6.11 | 1.309x
(min 1.274x) | 6.66 | 7.09 | 5.65 | 1.255x (min 1.241x) | 5.70 |
| FP8, B=1, q=32, kv=128, heads 32/8, page 64 | 6.27 | 6.18 | 1.013x
(min 1.008x) | 6.66 | 6.43 | 6.43 | 1.000x (min 1.000x) | 5.82 |
| FP8, B=1, q=32, kv=128, heads 32/16, page 64 | 6.42 | 6.18 | 1.039x
(min 1.026x) | 6.82 | 6.43 | 6.43 | 1.000x (min 0.995x) | 5.92 |
| FP8, B=1, q=32, kv=256, heads 32/4, page 64 | 9.70 | 7.30 | 1.328x
(min 1.302x) | 7.97 | 8.58 | 6.59 | 1.296x (min 1.295x) | 6.59 |
| FP8, B=1, q=32, kv=256, heads 32/8, page 64 | 7.81 | 7.36 | 1.061x
(min 1.039x) | 8.10 | 7.17 | 6.66 | 1.077x (min 1.075x) | 6.75 |
| FP8, B=1, q=32, kv=256, heads 32/16, page 64 | 7.71 | 7.42 | 1.028x
(min 1.026x) | 8.22 | 7.65 | 7.68 | 1.000x (min 0.996x) | 6.91 |
| FP8, B=1, q=32, kv=256, heads 32/32, page 64 | 7.78 | 7.57 | 1.025x
(min 1.021x) | 8.26 | - | - | - | - |
| FP8, B=1, q=32, kv=384, heads 32/4, page 64 | 11.10 | 8.51 | 1.313x
(min 1.305x) | 9.60 | 9.44 | 7.26 | 1.304x (min 1.300x) | 7.78 |
| FP8, B=1, q=32, kv=384, heads 32/8, page 64 | 8.99 | 8.56 | 1.050x
(min 1.034x) | 9.66 | 7.73 | 7.30 | 1.061x (min 1.057x) | 7.81 |
| FP8, B=1, q=32, kv=384, heads 32/16, page 64 | 9.06 | 8.77 | 1.033x
(min 1.029x) | 9.70 | 7.30 | 7.20 | 1.013x (min 1.011x) | 7.78 |
| FP8, B=1, q=32, kv=384, heads 32/32, page 64 | 8.96 | 8.74 | 1.026x
(min 1.018x) | 9.92 | 7.47 | 7.36 | 1.017x (min 1.011x) | 7.94 |
| FP8, B=1, q=32, kv=512, heads 32/4, page 64 | 12.67 | 9.70 | 1.310x
(min 1.300x) | 10.91 | 10.37 | 7.87 | 1.317x (min 1.313x) | 8.64 |
| FP8, B=1, q=32, kv=512, heads 32/8, page 64 | 10.34 | 9.92 | 1.042x
(min 1.039x) | 11.01 | 8.48 | 8.13 | 1.043x (min 1.039x) | 8.77 |
| FP8, B=1, q=32, kv=512, heads 32/16, page 64 | 10.18 | 9.98 | 1.019x
(min 1.016x) | 11.23 | 8.27 | 8.13 | 1.022x (min 1.014x) | 8.99 |
| FP8, B=1, q=32, kv=512, heads 32/32, page 64 | 10.14 | 9.89 | 1.026x
(min 1.019x) | 11.36 | 8.54 | 8.29 | 1.033x (min 1.023x) | 9.28 |
| FP8, B=1, q=32, kv=768, heads 32/4, page 64 | 15.81 | 12.00 | 1.321x
(min 1.312x) | 13.95 | 12.50 | 9.41 | 1.327x (min 1.322x) | 10.75 |
| FP8, B=1, q=32, kv=768, heads 32/8, page 64 | 12.16 | 12.00 | 1.017x
(min 1.012x) | 13.89 | 9.92 | 9.60 | 1.033x (min 1.032x) | 10.88 |
| FP8, B=1, q=32, kv=768, heads 32/16, page 64 | 12.29 | 12.06 | 1.016x
(min 1.008x) | 14.14 | 10.05 | 9.76 | 1.033x (min 1.030x) | 11.23 |
| FP8, B=1, q=32, kv=768, heads 32/32, page 64 | 12.64 | 12.38 | 1.018x
(min 1.018x) | 14.48 | 9.98 | 9.79 | 1.016x (min 1.016x) | 11.55 |
| FP8, B=1, q=32, kv=1024, heads 32/4, page 64 | 17.66 | 14.30 | 1.235x
(min 1.232x) | 16.83 | 14.82 | 11.04 | 1.342x (min 1.337x) | 12.78 |
| FP8, B=1, q=32, kv=1024, heads 32/8, page 64 | 15.30 | 14.62 | 1.048x
(min 1.039x) | 16.96 | 11.71 | 11.33 | 1.034x (min 1.031x) | 13.18 |
| FP8, B=1, q=32, kv=1024, heads 32/16, page 64 | 14.85 | 14.59 | 1.020x
(min 1.018x) | 17.09 | 11.54 | 11.36 | 1.013x (min 1.013x) | 13.76 |
| FP8, B=1, q=32, kv=1024, heads 32/32, page 64 | 14.94 | 14.62 | 1.020x
(min 1.015x) | 17.50 | 11.65 | 11.46 | 1.015x (min 1.011x) | 13.89 |
| FP8, B=2, q=32, kv=128, heads 32/4, page 64 | 7.94 | 6.16 | 1.292x
(min 1.266x) | 6.91 | 7.18 | 5.82 | 1.240x (min 1.225x) | 6.11 |
| FP8, B=2, q=32, kv=128, heads 32/8, page 64 | 6.69 | 6.24 | 1.067x
(min 1.066x) | 6.91 | 6.69 | 6.69 | 1.000x (min 1.000x) | 6.11 |
| FP8, B=2, q=32, kv=128, heads 32/16, page 64 | 6.53 | 6.30 | 1.036x
(min 1.025x) | 6.91 | - | - | - | - |
| FP8, B=2, q=32, kv=256, heads 32/4, page 64 | 9.73 | 7.47 | 1.299x
(min 1.296x) | 8.29 | 8.54 | 6.66 | 1.282x (min 1.269x) | 7.01 |
| FP8, B=2, q=32, kv=256, heads 32/8, page 64 | 7.90 | 7.52 | 1.051x
(min 1.030x) | 8.32 | 6.85 | 6.62 | 1.034x (min 1.029x) | 6.91 |
| FP8, B=2, q=32, kv=256, heads 32/16, page 64 | 7.90 | 7.68 | 1.029x
(min 1.021x) | 8.42 | - | - | - | - |
| FP8, B=2, q=32, kv=256, heads 32/32, page 64 | 8.19 | 7.94 | 1.028x
(min 1.028x) | 8.74 | - | - | - | - |
| FP8, B=2, q=32, kv=384, heads 32/4, page 64 | 10.98 | 8.61 | 1.275x
(min 1.264x) | 9.73 | 9.18 | 7.23 | 1.270x (min 1.265x) | 7.78 |
| FP8, B=2, q=32, kv=384, heads 32/8, page 64 | 9.22 | 8.77 | 1.051x
(min 1.043x) | 9.82 | 7.78 | 7.39 | 1.052x (min 1.047x) | 7.94 |
| FP8, B=2, q=32, kv=384, heads 32/16, page 64 | 9.12 | 8.90 | 1.025x
(min 1.018x) | 10.14 | 7.71 | 7.46 | 1.039x (min 1.034x) | 8.10 |
| FP8, B=2, q=32, kv=384, heads 32/32, page 64 | 9.41 | 9.18 | 1.028x
(min 1.024x) | 10.59 | 8.06 | 7.78 | 1.037x (min 1.029x) | 8.61 |
| FP8, B=2, q=32, kv=512, heads 32/4, page 64 | 12.83 | 9.78 | 1.314x
(min 1.287x) | 11.23 | 10.59 | 8.03 | 1.323x (min 1.312x) | 8.83 |
| FP8, B=2, q=32, kv=512, heads 32/8, page 64 | 10.06 | 9.86 | 1.023x
(min 1.018x) | 11.23 | 8.45 | 8.13 | 1.043x (min 1.035x) | 9.09 |
| FP8, B=2, q=32, kv=512, heads 32/16, page 64 | 10.21 | 9.95 | 1.023x
(min 1.016x) | 11.52 | 8.64 | 8.32 | 1.038x (min 1.031x) | 9.54 |
| FP8, B=2, q=32, kv=512, heads 32/32, page 64 | 10.78 | 10.43 | 1.028x
(min 1.024x) | 12.13 | 8.90 | 8.74 | 1.018x (min 1.011x) | 9.82 |
| FP8, B=2, q=32, kv=768, heads 32/4, page 64 | 15.97 | 12.22 | 1.303x
(min 1.300x) | 14.21 | 12.70 | 9.70 | 1.305x (min 1.300x) | 11.17 |
| FP8, B=2, q=32, kv=768, heads 32/8, page 64 | 12.77 | 12.45 | 1.026x
(min 1.021x) | 14.37 | 10.08 | 9.70 | 1.040x (min 1.038x) | 11.41 |
| FP8, B=2, q=32, kv=768, heads 32/16, page 64 | 12.67 | 12.45 | 1.018x
(min 1.015x) | 14.62 | 10.21 | 10.05 | 1.016x (min 1.013x) | 11.87 |
| FP8, B=2, q=32, kv=768, heads 32/32, page 64 | 12.99 | 12.78 | 1.016x
(min 1.014x) | 15.10 | 10.70 | 10.53 | 1.017x (min 1.014x) | 12.35 |
| FP8, B=2, q=32, kv=1024, heads 32/4, page 64 | 19.04 | 14.56 | 1.313x
(min 1.305x) | 17.09 | 14.78 | 11.30 | 1.309x (min 1.301x) | 13.31 |
| FP8, B=2, q=32, kv=1024, heads 32/8, page 64 | 15.17 | 14.85 | 1.022x
(min 1.017x) | 17.31 | 11.74 | 11.33 | 1.037x (min 1.034x) | 13.78 |
| FP8, B=2, q=32, kv=1024, heads 32/16, page 64 | 15.07 | 14.85 | 1.015x
(min 1.014x) | 17.63 | 11.90 | 11.68 | 1.017x (min 1.016x) | 14.27 |
| FP8, B=2, q=32, kv=1024, heads 32/32, page 64 | 15.39 | 15.14 | 1.017x
(min 1.015x) | 18.14 | 12.35 | 12.13 | 1.020x (min 1.018x) | 14.82 |
| FP8, B=2, q=32, kv=2048, heads 32/8, page 64 | - | - | - | - | 18.24 |
17.82 | 1.023x (min 1.020x) | 22.27 |
| FP8, B=2, q=32, kv=2048, heads 32/32, page 64 | - | - | - | - | 19.07
| 18.93 | 1.009x (min 1.006x) | 24.26 |
| FP8, B=16, q=32, kv=128, heads 32/4, page 64 | 8.32 | 7.14 | 1.169x
(min 1.156x) | 16.13 | 7.46 | 6.72 | 1.110x (min 1.104x) | 13.31 |
| FP8, B=16, q=32, kv=128, heads 32/8, page 64 | 7.55 | 7.52 | 1.006x
(min 0.996x) | 16.13 | - | - | - | - |
| FP8, B=16, q=32, kv=128, heads 32/16, page 64 | 9.22 | 9.22 | 1.000x
(min 1.000x) | 16.45 | - | - | - | - |
| FP8, B=16, q=32, kv=128, heads 32/32, page 64 | 13.25 | 13.25 | 1.000x
(min 0.999x) | 16.61 | - | - | - | - |
| FP8, B=16, q=32, kv=256, heads 32/4, page 64 | 10.45 | 8.67 | 1.206x
(min 1.203x) | 23.14 | 9.15 | 7.74 | 1.178x (min 1.177x) | 18.34 |
| FP8, B=16, q=32, kv=256, heads 32/8, page 64 | 9.18 | 9.04 | 1.011x
(min 1.005x) | 23.18 | 8.51 | 8.26 | 1.027x (min 1.023x) | 18.66 |
| FP8, B=16, q=32, kv=256, heads 32/16, page 64 | 12.22 | 12.21 | 1.000x
(min 1.000x) | 23.39 | 11.07 | 10.94 | 1.012x (min 1.006x) | 18.72 |
| FP8, B=16, q=32, kv=256, heads 32/32, page 64 | 17.82 | 17.82 | 1.000x
(min 0.998x) | 23.39 | 15.97 | 15.84 | 1.008x (min 1.004x) | 19.14 |
| FP8, B=16, q=32, kv=384, heads 32/4, page 64 | 12.06 | 9.86 | 1.237x
(min 1.218x) | 28.13 | 10.30 | 8.58 | 1.201x (min 1.194x) | 21.74 |
| FP8, B=16, q=32, kv=384, heads 32/8, page 64 | 10.59 | 10.27 | 1.031x
(min 1.022x) | 28.54 | 9.15 | 8.90 | 1.032x (min 1.029x) | 21.65 |
| FP8, B=16, q=32, kv=384, heads 32/16, page 64 | 14.66 | 14.66 | 1.000x
(min 1.000x) | 28.90 | 12.64 | 12.48 | 1.014x (min 1.012x) | 21.79 |
| FP8, B=16, q=32, kv=384, heads 32/32, page 64 | 23.06 | 23.04 | 1.000x
(min 0.999x) | 29.54 | 19.23 | 19.02 | 1.013x (min 1.009x) | 22.50 |
| FP8, B=16, q=32, kv=512, heads 32/4, page 64 | 13.82 | 11.10 | 1.254x
(min 1.245x) | 34.06 | 11.62 | 9.41 | 1.230x (min 1.226x) | 25.65 |
| FP8, B=16, q=32, kv=512, heads 32/8, page 64 | 11.81 | 11.58 | 1.022x
(min 1.019x) | 34.69 | 10.24 | 9.98 | 1.025x (min 1.022x) | 25.57 |
| FP8, B=16, q=32, kv=512, heads 32/16, page 64 | 17.38 | 17.18 | 1.010x
(min 1.006x) | 34.91 | 14.78 | 14.66 | 1.012x (min 1.007x) | 26.32 |
| FP8, B=16, q=32, kv=512, heads 32/32, page 64 | 28.80 | 28.66 | 1.006x
(min 1.004x) | 35.82 | 23.62 | 23.58 | 1.001x (min 1.000x) | 27.94 |
| FP8, B=16, q=32, kv=768, heads 32/4, page 64 | 17.12 | 13.60 | 1.264x
(min 1.256x) | 46.43 | 13.81 | 11.20 | 1.232x (min 1.228x) | 34.10 |
| FP8, B=16, q=32, kv=768, heads 32/8, page 64 | 14.50 | 14.24 | 1.018x
(min 1.014x) | 47.33 | 12.08 | 11.81 | 1.023x (min 1.022x) | 34.21 |
| FP8, B=16, q=32, kv=768, heads 32/16, page 64 | 23.17 | 22.91 | 1.010x
(min 1.010x) | 47.62 | 19.02 | 18.78 | 1.012x (min 1.010x) | 35.84 |
| FP8, B=16, q=32, kv=768, heads 32/32, page 64 | 40.26 | 39.94 | 1.008x
(min 1.007x) | 48.86 | 32.26 | 32.02 | 1.006x (min 1.005x) | 39.20 |
| FP8, B=16, q=32, kv=1024, heads 32/4, page 64 | 20.19 | 15.94 | 1.268x
(min 1.258x) | 58.85 | 15.81 | 12.64 | 1.249x (min 1.246x) | 41.97 |
| FP8, B=16, q=32, kv=1024, heads 32/8, page 64 | 17.30 | 16.90 | 1.023x
(min 1.017x) | 59.74 | 14.32 | 14.02 | 1.021x (min 1.018x) | 43.18 |
| FP8, B=16, q=32, kv=1024, heads 32/16, page 64 | 28.91 | 28.64 |
1.010x (min 1.009x) | 60.16 | 23.71 | 23.46 | 1.011x (min 1.010x) |
46.30 |
| FP8, B=16, q=32, kv=1024, heads 32/32, page 64 | 50.75 | 50.45 |
1.007x (min 1.005x) | 61.98 | 41.04 | 40.86 | 1.006x (min 1.004x) |
50.46 |
| FP8, B=16, q=32, kv=2048, heads 32/4, page 64 | 30.35 | 25.89 | 1.172x
(min 1.169x) | 107.71 | 24.62 | 19.68 | 1.254x (min 1.250x) | 76.42 |
| FP8, B=16, q=32, kv=2048, heads 32/8, page 64 | 28.93 | 28.58 | 1.011x
(min 1.010x) | 109.15 | 23.28 | 23.01 | 1.015x (min 1.012x) | 79.71 |
| FP8, B=16, q=32, kv=2048, heads 32/16, page 64 | 51.20 | 50.74 |
1.010x (min 1.008x) | 109.38 | 40.58 | 40.19 | 1.009x (min 1.008x) |
83.17 |
| FP8, B=16, q=32, kv=2048, heads 32/32, page 64 | 89.82 | 89.39 |
1.005x (min 1.004x) | 111.81 | 69.73 | 69.25 | 1.006x (min 1.006x) |
88.74 |
| FP8, B=256, q=32, kv=128, heads 32/8, page 64 | 55.39 | 39.60 | 1.399x
(min 1.389x) | 162.18 | 40.62 | 40.61 | 1.000x (min 1.000x) | 128.38 |
| FP8, B=256, q=32, kv=128, heads 32/16, page 64 | 89.07 | 64.99 |
1.371x (min 1.366x) | 161.65 | 66.72 | 66.64 | 1.001x (min 1.000x) |
128.19 |
| FP8, B=256, q=32, kv=128, heads 32/32, page 64 | 159.58 | 118.66 |
1.345x (min 1.342x) | 161.76 | 126.05 | 126.05 | 1.000x (min 1.000x) |
128.85 |
| FP8, B=256, q=32, kv=256, heads 32/8, page 64 | 75.94 | 52.19 | 1.456x
(min 1.450x) | 248.48 | 54.21 | 54.21 | 1.000x (min 0.999x) | 189.36 |
| FP8, B=256, q=32, kv=256, heads 32/16, page 64 | 131.46 | 91.38 |
1.441x (min 1.436x) | 247.44 | 94.64 | 94.67 | 1.000x (min 0.999x) |
189.12 |
| FP8, B=256, q=32, kv=256, heads 32/32, page 64 | 244.09 | 172.48 |
1.415x (min 1.414x) | 246.14 | 179.38 | 179.41 | 1.000x (min 1.000x) |
189.06 |
| FP8, B=256, q=32, kv=384, heads 32/8, page 64 | 99.81 | 70.13 | 1.423x
(min 1.417x) | 325.58 | 68.35 | 68.38 | 1.000x (min 1.000x) | 225.50 |
| FP8, B=256, q=32, kv=384, heads 32/16, page 64 | 179.66 | 126.05 |
1.427x (min 1.424x) | 330.38 | 121.58 | 121.52 | 1.000x (min 1.000x) |
227.26 |
| FP8, B=256, q=32, kv=384, heads 32/32, page 64 | 337.74 | 239.60 |
1.409x (min 1.409x) | 340.75 | 229.39 | 229.36 | 1.000x (min 0.999x) |
234.19 |
| FP8, B=256, q=32, kv=512, heads 32/8, page 64 | 124.14 | 87.96 |
1.409x (min 1.404x) | 410.26 | 85.01 | 85.02 | 1.000x (min 1.000x) |
283.90 |
| FP8, B=256, q=32, kv=512, heads 32/16, page 64 | 226.70 | 160.62 |
1.411x (min 1.409x) | 425.09 | 154.58 | 154.59 | 1.000x (min 1.000x) |
287.43 |
| FP8, B=256, q=32, kv=512, heads 32/32, page 64 | 443.95 | 307.66 |
1.442x (min 1.433x) | 445.33 | 293.12 | 293.17 | 1.000x (min 1.000x) |
298.38 |
| FP8, B=256, q=32, kv=768, heads 32/8, page 64 | 169.44 | 122.62 |
1.382x (min 1.375x) | 592.59 | 116.51 | 116.50 | 1.000x (min 1.000x) |
400.56 |
| FP8, B=256, q=32, kv=768, heads 32/16, page 64 | 325.26 | 228.48 |
1.424x (min 1.420x) | 619.10 | 214.59 | 214.61 | 1.001x (min 0.999x) |
411.11 |
| FP8, B=256, q=32, kv=768, heads 32/32, page 64 | 647.89 | 440.94 |
1.469x (min 1.468x) | 650.26 | 411.55 | 411.70 | 1.000x (min 0.999x) |
427.65 |
| FP8, B=256, q=32, kv=1024, heads 32/8, page 64 | 214.72 | 156.86 |
1.369x (min 1.368x) | 779.90 | 148.14 | 148.06 | 1.000x (min 1.000x) |
519.46 |
| FP8, B=256, q=32, kv=1024, heads 32/16, page 64 | 426.06 | 297.60 |
1.432x (min 1.422x) | 811.18 | 275.12 | 275.20 | 1.000x (min 0.998x) |
536.13 |
| FP8, B=256, q=32, kv=1024, heads 32/32, page 64 | 855.33 | 581.17 |
1.472x (min 1.468x) | 849.47 | 535.78 | 536.37 | 0.999x (min 0.997x) |
566.05 |
| FP8, B=256, q=32, kv=2048, heads 32/8, page 64 | 415.30 | 291.86 |
1.423x (min 1.418x) | 1514.80 | 273.22 | 273.19 | 1.000x (min 0.999x) |
1004.21 |
| FP8, B=256, q=32, kv=2048, heads 32/16, page 64 | 848.27 | 582.06 |
1.458x (min 1.449x) | 1597.39 | 519.67 | 519.20 | 1.001x (min 1.000x) |
1048.64 |
| FP8, B=256, q=32, kv=2048, heads 32/32, page 64 | 1677.92 | 1164.39 |
1.441x (min 1.440x) | 1661.75 | 1051.25 | 1048.92 | 1.001x (min 0.998x)
| 1118.05 |
| FP8, B=1, q=32, kv=128, heads 32/4, page 16 | 6.62 | 6.40 | 1.030x
(min 1.030x) | 6.75 | 6.88 | 5.79 | 1.188x (min 1.181x) | 5.79 |
| FP8, B=1, q=32, kv=1500, heads 32/4, page 16 | - | - | - | - | 15.49 |
14.98 | 1.034x (min 1.034x) | 17.63 |
| FP8, B=1, q=64, kv=128, heads 32/4, page 16 | 6.88 | 6.66 | 1.034x
(min 1.031x) | 7.04 | 6.53 | 5.82 | 1.121x (min 1.121x) | 5.98 |
| FP8, B=1, q=64, kv=128, heads 32/4, page 64 | 6.30 | 6.02 | 1.048x
(min 1.037x) | 6.88 | - | - | - | - |
| FP8, B=1, q=64, kv=1500, heads 32/4, page 16 | - | - | - | - | 15.46 |
15.17 | 1.019x (min 1.015x) | 17.68 |
| FP8, B=1, q=100, kv=100, heads 32/4, page 16 | - | - | - | - | 6.80 |
5.86 | 1.161x (min 1.152x) | 6.24 |
| FP8, B=1, q=128, kv=128, heads 32/4, page 16 | - | - | - | - | 6.85 |
5.98 | 1.144x (min 1.141x) | 6.46 |
| FP8, B=1, q=128, kv=128, heads 64/8, page 16 | - | - | - | - | 6.66 |
6.05 | 1.101x (min 1.089x) | 6.54 |
| FP8, B=2, q=32, kv=128, heads 32/4, page 16 | 6.98 | 6.82 | 1.023x
(min 1.021x) | 7.01 | 6.88 | 5.89 | 1.168x (min 1.158x) | 6.02 |
| FP8, B=2, q=64, kv=128, heads 32/4, page 16 | 6.91 | 6.75 | 1.019x
(min 1.014x) | 7.17 | 6.82 | 5.89 | 1.158x (min 1.158x) | 6.18 |
| FP8, B=2, q=128, kv=100, heads 32/4, page 16 | - | - | - | - | 6.66 |
6.06 | 1.100x (min 1.081x) | 6.59 |
| FP8, B=2, q=128, kv=128, heads 32/4, page 16 | - | - | - | - | 6.67 |
6.11 | 1.092x (min 1.089x) | 6.53 |
| FP8, B=2, q=128, kv=128, heads 32/8, page 16 | - | - | - | - | 7.26 |
6.24 | 1.164x (min 1.156x) | 6.66 |
| FP8, B=2, q=128, kv=1500, heads 32/4, page 64 | 20.38 | 19.90 | 1.026x
(min 1.023x) | 24.38 | 15.26 | 14.82 | 1.030x (min 1.029x) | 18.30 |
| FP8, B=4, q=64, kv=128, heads 32/4, page 16 | 6.91 | 6.85 | 1.009x
(min 1.000x) | 7.55 | 6.78 | 6.22 | 1.087x (min 1.084x) | 6.59 |
| FP8, B=4, q=128, kv=128, heads 32/4, page 16 | - | - | - | - | 6.88 |
6.69 | 1.029x (min 1.026x) | 7.26 |
| FP8, B=4, q=128, kv=128, heads 32/4, page 32 | - | - | - | - | 6.88 |
6.59 | 1.046x (min 1.041x) | 7.10 |
| FP8, B=8, q=64, kv=128, heads 32/4, page 16 | - | - | - | - | 7.10 |
6.62 | 1.072x (min 1.066x) | 9.31 |
| FP8, B=16, q=32, kv=128, heads 32/4, page 16 | - | - | - | - | 7.20 |
6.46 | 1.118x (min 1.113x) | 13.60 |
| FP8, B=64, q=32, kv=1024, heads 32/32, page 16 | 211.26 | 156.91 |
1.346x (min 1.343x) | 206.50 | - | - | - | - |
| FP8, B=128, q=32, kv=1024, heads 32/16, page 16 | 213.28 | 159.01 |
1.341x (min 1.340x) | 397.14 | - | - | - | - |
| FP8, B=128, q=32, kv=1024, heads 32/32, page 16 | 420.30 | 300.74 |
1.398x (min 1.392x) | 424.50 | - | - | - | - |
| FP8, B=256, q=32, kv=1024, heads 32/8, page 16 | 212.64 | 160.27 |
1.327x (min 1.325x) | 793.31 | - | - | - | - |
| FP8, B=256, q=32, kv=1024, heads 32/16, page 16 | 420.70 | 302.78 |
1.390x (min 1.388x) | 809.00 | - | - | - | - |
| FP8, B=256, q=64, kv=1024, heads 32/16, page 16 | 425.50 | 308.45 |
1.381x (min 1.378x) | 822.54 | - | - | - | - |
| FP8, B=256, q=64, kv=1024, heads 32/32, page 16 | 865.76 | 607.46 |
1.425x (min 1.421x) | 881.39 | - | - | - | - |
| FP8, B=256, q=128, kv=1024, heads 32/32, page 16 | 874.87 | 619.86 |
1.411x (min 1.411x) | 896.56 | - | - | - | - |
| FP8, B=512, q=16, kv=1024, heads 32/4, page 16 | 213.94 | 160.00 |
1.337x (min 1.335x) | 1529.78 | - | - | - | - |
| FP8, B=2, q=200, kv=1500, heads 32/4, page 16 | 25.89 | 25.89 | 1.000x
(min 0.999x) | 25.09 | - | - | - | - |
| FP8, B=2, q=400, kv=1500, heads 32/4, page 16 | 26.11 | 26.14 | 0.999x
(min 0.998x) | 25.84 | - | - | - | - |
| FP8, B=4, q=128, kv=4096, heads 32/32, page 64 | 50.34 | 50.05 |
1.006x (min 1.006x) | 60.35 | 40.08 | 39.81 | 1.008x (min 1.006x) |
50.98 |
| FP8, B=16, q=128, kv=2048, heads 32/32, page 64 | 91.33 | 90.96 |
1.004x (min 1.004x) | 114.72 | 71.14 | 70.72 | 1.006x (min 1.006x) |
91.65 |
| FP8, B=256, q=4, kv=1024, heads 32/32, page 64 | 843.94 | 578.03 |
1.460x (min 1.459x) | 839.26 | 529.30 | 529.46 | 0.999x (min 0.998x) |
553.83 |

</details>

Ten sweep shapes are not faster than trtllm-gen, and none of them is
slower than the previous version. On B200, two are slower than
trtllm-gen: FP8, B=2, kv=1500, heads 32/4, page 16 with q=200
(trtllm-gen / this PR 0.969x) and with q=400 (0.992x). On GB300, four
are slower, all FP8 with q=32 and page 64: B=1, kv=128, heads 32/8
(0.905x); B=1, kv=128, heads 32/16 (0.925x); B=1, kv=256, heads 32/16
(0.900x); and B=2, kv=128, heads 32/8 (0.914x). Four more on GB300 are
within the run-to-run band of trtllm-gen, all FP8 with B=1 and q=32:
kv=128, heads 32/4, page 64 (1.006x); kv=256, heads 32/4, page 64
(1.000x); kv=256, heads 32/8, page 64 (1.014x); and kv=128, heads 32/4,
page 16 (1.000x).

The kernel's other Cake variants, BF16 and FP8 Q with NVFP4 KV, are not
changed by this PR, and the kernel covers sm_100a (B200) and sm_103a
(GB300).

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [4d601a1](https://github.com/flashinfer-ai/flashinfer/commit/4d601a17ad5ba794a89cf44ef2bcc69567d47775)

- **作者**: eigen
- **时间**: 2026-10-31T09:59:39Z
- **提交信息**: perf(cake_deepgemm): SM120 paged FP8 MQA logits CTA-parallel scheduler routes for RTX 5090 and RTX PRO 6000 (#8099)

The SM120a paged FP8 MQA logits kernel
(`flashinfer/experimental/deepgemm_sm120_paged_mqa_logits`, the
DeepSeek-V3.2 / V4.1-Flash decode lightning indexer) runs a metadata
scheduler and then a logits kernel. It selects per-device routes by the
GPU's SM count. Until now its routes used one of two schedulers: the
one-warp static scheduler or the dynamic scheduler. This PR adds a
CTA-parallel version of the static scheduler. It writes the same
`schedule_meta` bit for bit. The PR also adds 75 device routes that pair
it with logits programs. With these routes, RTX 5090 (170 SMs) runs 158
of the 216 measured shapes with the parallel scheduler, and RTX PRO 6000
(188 SMs) runs 147. A route is enabled only on a GPU where it measured
faster. 52 of these shapes used the default route before (5 on RTX 5090,
47 on RTX PRO 6000). On those shapes the new route also changes the
logits kernel to the default program compiled without `--use_fast_math`.
The other shapes keep their shipped routes. The baseline is the shipped
routes on main, which already include the previous PR's 186 routed
shapes on RTX 5090 and 155 on RTX PRO 6000. Over two independent runs,
the geometric-mean speedup on the changed shapes is 1.107× / 1.101× on
RTX 5090 (158 shapes, per shape 1.006×-1.469×; the first run is 1.108×
without its one ² shape). On RTX PRO 6000 it is 1.096× / 1.096× (147
shapes, per shape 1.005×-1.416×). The logits stay bitwise identical to
DeepGEMM.

Table: kernel time of one call (scheduler + logits kernels) on NVIDIA
GeForce RTX 5090 (170 SMs, driver 620.62) and NVIDIA RTX PRO 6000
Blackwell Server Edition (188 SMs, driver 595.84.01). Both are sm_120a
with the CUDA 13.0 runtime (torch 2.14.1+cu130) and the CUDA 13.4.92 JIT
toolchain. There is one row per shape (heads, page size, next_n, batch,
context tokens). Baseline is the shipped route on main and new is this
PR, with latency in µs and speedup = baseline µs / new µs. The table
covers two independent runs (seeds 760 and 52021, one GPU per seed). On
`changed` rows the new side runs the CTA-parallel scheduler route. On
`unchanged` rows both sides run the same shipped program. ² marks a run
where the GPU clock was still below the clock floor after one re-time
(CE). Those numbers are shown as measured and are not judged.

**RTX 5090**

| heads | page | next_n | batch | context | state | baseline µs (760) |
new µs | speedup | baseline µs (52021) | new µs | speedup |
|---:|---:|---:|---:|---:|:--|---:|---:|---:|---:|---:|---:|
| 32 | 64 | 1 | 8 | 4096 | changed | 9.95 | 7.20 | 1.382× | 9.79 | 7.26
| 1.348× |
| 32 | 64 | 1 | 64 | 4096 | changed | 32.61 | 29.41 | 1.109× | 32.22 |
29.22 | 1.103× |
| 32 | 64 | 1 | 256 | 4096 | changed | 106.53 | 100.67 | 1.058× | 105.73
| 100.06 | 1.057× |
| 32 | 64 | 1 | 1 | 16384 | changed | 9.06 | 6.18 | 1.466× | 8.77 | 6.18
| 1.420× |
| 32 | 64 | 1 | 8 | 16384 | changed | 19.49 | 16.64 | 1.171× | 19.17 |
16.54 | 1.159× |
| 32 | 64 | 1 | 32 | 16384 | changed | 55.20 | 52.48 | 1.052× | 54.62 |
52.00 | 1.050× |
| 32 | 64 | 1 | 64 | 16384 | changed | 104.35 | 101.15 | 1.032× | 103.01
| 100.06 | 1.029× |
| 32 | 64 | 1 | 128 | 16384 | changed | 197.02 | 193.02 | 1.021× |
195.33 | 191.49 | 1.020× |
| 32 | 64 | 1 | 256 | 16384 | changed | 379.99 | 374.49 | 1.015× |
378.38 | 372.96 | 1.015× |
| 32 | 64 | 1 | 8 | 65536 | changed | 58.56 | 55.87 | 1.048× | 58.05 |
55.58 | 1.044× |
| 32 | 64 | 1 | 32 | 65536 | changed | 191.58 | 188.80 | 1.015× | 190.21
| 187.65 | 1.014× |
| 32 | 64 | 1 | 128 | 65536 | unchanged | 725.36 | 725.33 | 1.000× |
720.04 | 719.91 | 1.000× |
| 32 | 64 | 2 | 8 | 4096 | changed | 10.30 | 7.49 | 1.376× | 10.08 |
7.52 | 1.340× |
| 32 | 64 | 2 | 64 | 4096 | changed | 33.50 | 30.30 | 1.106× | 33.12 |
30.14 | 1.099× |
| 32 | 64 | 2 | 256 | 4096 | changed | 110.91 | 104.99 | 1.056× | 109.53
| 103.90 | 1.054× |
| 32 | 64 | 2 | 1 | 16384 | changed | 9.28 | 6.40 | 1.450× | 9.02 | 6.43
| 1.403× |
| 32 | 64 | 2 | 8 | 16384 | changed | 20.22 | 17.44 | 1.160× | 19.90 |
17.25 | 1.154× |
| 32 | 64 | 2 | 32 | 16384 | changed | 56.61 | 53.95 | 1.049× | 55.94 |
53.34 | 1.049× |
| 32 | 64 | 2 | 64 | 16384 | changed | 107.74 | 104.67 | 1.029× | 106.59
| 103.68 | 1.028× |
| 32 | 64 | 2 | 128 | 16384 | changed | 207.45 | 203.42 | 1.020× |
205.57 | 201.79 | 1.019× |
| 32 | 64 | 2 | 256 | 16384 | changed | 399.80 | 394.73 | 1.013× |
397.31 | 391.97 | 1.014× |
| 32 | 64 | 2 | 8 | 65536 | changed | 60.16 | 57.31 | 1.050× | 59.49 |
56.99 | 1.044× |
| 32 | 64 | 2 | 32 | 65536 | changed | 200.57 | 197.88 | 1.014× | 199.10
| 196.64 | 1.013× |
| 32 | 64 | 2 | 128 | 65536 | unchanged | 764.37 | 763.73 | 1.001× |
757.15 | 756.92 | 1.000× |
| 32 | 64 | 3 | 8 | 4096 | changed | 11.36 | 8.64 | 1.315× | 11.10 |
8.51 | 1.305× |
| 32 | 64 | 3 | 64 | 4096 | changed | 35.04 | 31.87 | 1.099× | 34.66 |
31.58 | 1.097× |
| 32 | 64 | 3 | 256 | 4096 | changed | 118.11 | 112.29 | 1.052× | 116.39
| 110.66 | 1.052× |
| 32 | 64 | 3 | 1 | 16384 | changed | 9.34 | 6.46 | 1.446× | 9.18 | 6.53
| 1.407× |
| 32 | 64 | 3 | 8 | 16384 | changed | 20.80 | 18.02 | 1.155× | 20.51 |
17.98 | 1.141× |
| 32 | 64 | 3 | 32 | 16384 | changed | 59.23 | 56.54 | 1.048× | 58.53 |
56.06 | 1.044× |
| 32 | 64 | 3 | 64 | 16384 | changed | 113.95 | 110.91 | 1.027× | 113.12
| 110.08 | 1.028× |
| 32 | 64 | 3 | 128 | 16384 | changed | 219.00 | 214.91 | 1.019× |
216.93 | 213.05 | 1.018× |
| 32 | 64 | 3 | 256 | 16384 | changed | 424.99 | 418.71 | 1.015× |
420.12 | 414.43 | 1.014× |
| 32 | 64 | 3 | 8 | 65536 | changed | 62.62 | 59.81 | 1.047× | 61.89 |
59.33 | 1.043× |
| 32 | 64 | 3 | 32 | 65536 | changed | 211.36 | 208.61 | 1.013× | 209.50
| 207.36 | 1.010× |
| 32 | 64 | 3 | 128 | 65536 | unchanged | 808.56 | 808.92 | 1.000× |
805.53 | 804.69 | 1.001× |
| 32 | 64 | 4 | 8 | 4096 | unchanged | 10.46 | 10.46 | 1.000× | 10.30 |
10.30 | 1.000× |
| 32 | 64 | 4 | 64 | 4096 | changed | 36.83 | 33.54 | 1.098× | 36.13 |
33.02 | 1.094× |
| 32 | 64 | 4 | 256 | 4096 | changed | 124.86 | 119.01 | 1.049× | 123.87
| 118.59 | 1.045× |
| 32 | 64 | 4 | 1 | 16384 | changed | 9.54 | 6.69 | 1.426× | 9.34 | 6.69
| 1.397× |
| 32 | 64 | 4 | 8 | 16384 | changed | 21.31 | 18.59 | 1.146× | 21.38 |
18.82 | 1.136× |
| 32 | 64 | 4 | 32 | 16384 | changed | 62.24 | 59.58 | 1.045× | 61.41 |
58.85 | 1.043× |
| 32 | 64 | 4 | 64 | 16384 | changed | 120.32 | 117.85 | 1.021× | 119.07
| 116.48 | 1.022× |
| 32 | 64 | 4 | 128 | 16384 | changed | 230.40 | 225.98 | 1.020× |
227.81 | 223.97 | 1.017× |
| 32 | 64 | 4 | 256 | 16384 | changed | 446.01 | 439.83 | 1.014× |
442.93 | 437.00 | 1.014× |
| 32 | 64 | 4 | 8 | 65536 | changed | 65.18 | 62.43 | 1.044× | 64.77 |
62.37 | 1.038× |
| 32 | 64 | 4 | 32 | 65536 | unchanged | 223.36 | 223.39 | 1.000× |
220.03 | 220.06 | 1.000× |
| 32 | 64 | 4 | 128 | 65536 | unchanged | 859.75 | 859.73 | 1.000× |
854.33 | 855.87 | 0.998× |
| 32 | 64 | 5 | 8 | 4096 | unchanged | 11.65 | 11.65 | 1.000× | 11.36 |
11.36 | 1.000× |
| 32 | 64 | 5 | 64 | 4096 | changed | 38.46 | 35.26 | 1.091× | 38.82 |
35.90 | 1.081× |
| 32 | 64 | 5 | 256 | 4096 | unchanged | 138.43 | 138.46 | 1.000× |
137.47 | 137.47 | 1.000× |
| 32 | 64 | 5 | 1 | 16384 | changed | 10.18 | 7.30 | 1.395× | 9.92 |
7.23 | 1.372× |
| 32 | 64 | 5 | 8 | 16384 | changed | 22.82 | 20.13 | 1.134× | 22.56 |
19.97 | 1.130× |
| 32 | 64 | 5 | 32 | 16384 | changed | 67.42 | 64.67 | 1.043× | 66.24 |
63.68 | 1.040× |
| 32 | 64 | 5 | 64 | 16384 | unchanged | 133.82 | 133.79 | 1.000× |
132.80 | 132.73 | 1.000× |
| 32 | 64 | 5 | 128 | 16384 | unchanged | 243.49 | 243.33 | 1.001× |
240.73 | 240.70 | 1.000× |
| 32 | 64 | 5 | 256 | 16384 | changed | 458.91 | 453.02 | 1.013× |
457.08 | 451.36 | 1.013× |
| 32 | 64 | 5 | 8 | 65536 | unchanged | 69.41 | 69.41 | 1.000× | 70.18 |
70.21 | 1.000× |
| 32 | 64 | 5 | 32 | 65536 | unchanged | 236.35 | 236.35 | 1.000× |
234.81 | 234.72 | 1.000× |
| 32 | 64 | 5 | 128 | 65536 | unchanged | 881.99 | 881.78 | 1.000× |
867.35 | 867.00 | 1.000× |
| 32 | 64 | 6 | 8 | 4096 | unchanged | 11.58 | 11.58 | 1.000× | 11.30 |
11.30 | 1.000× |
| 32 | 64 | 6 | 64 | 4096 | changed | 42.30 | 38.78 | 1.091× | 41.86 |
38.62 | 1.084× |
| 32 | 64 | 6 | 256 | 4096 | changed | 155.07 | 148.29 | 1.046× | 152.41
| 145.47 | 1.048× |
| 32 | 64 | 6 | 1 | 16384 | changed | 10.02 | 7.14 | 1.404× | 9.79 |
7.17 | 1.366× |
| 32 | 64 | 6 | 8 | 16384 | changed | 25.25 | 22.62 | 1.116× | 24.38 |
22.08 | 1.104× |
| 32 | 64 | 6 | 32 | 16384 | unchanged | 72.61 | 72.64 | 1.000× | 73.12
| 73.09 | 1.000× |
| 32 | 64 | 6 | 64 | 16384 | changed | 149.05 | 145.41 | 1.025× | 145.95
| 142.91 | 1.021× |
| 32 | 64 | 6 | 128 | 16384 | changed | 273.47 | 268.83 | 1.017× |
270.91 | 266.91 | 1.015× |
| 32 | 64 | 6 | 256 | 16384 | changed | 529.11 | 523.29 | 1.011× |
526.97 | 521.08 | 1.011× |
| 32 | 64 | 6 | 8 | 65536 | changed | 74.72 | 71.94 | 1.039× | 75.49 |
72.61 | 1.040× |
| 32 | 64 | 6 | 32 | 65536 | unchanged | 264.41 | 264.38 | 1.000× |
260.83 | 260.96 | 1.000× |
| 32 | 64 | 6 | 128 | 65536 | unchanged | 1036.08 | 1036.11 | 1.000× |
1027.00 | 1023.80 | 1.003× |
| 32 | 128 | 1 | 8 | 4096 | changed | 9.98 | 7.20 | 1.387× | 9.85 | 7.23
| 1.363× |
| 32 | 128 | 1 | 64 | 4096 | changed | 32.83 | 29.70 | 1.106× | 32.51 |
29.60 | 1.098× |
| 32 | 128 | 1 | 256 | 4096 | changed | 106.30 | 100.54 | 1.057× |
105.63 | 99.97 | 1.057× |
| 32 | 128 | 1 | 1 | 16384 | changed | 9.02 | 6.14 | 1.469× | 8.83 |
6.18 | 1.430× |
| 32 | 128 | 1 | 8 | 16384 | changed | 19.68 | 16.86 | 1.167× | 19.33 |
16.74 | 1.155× |
| 32 | 128 | 1 | 32 | 16384 | changed | 55.10 | 52.35 | 1.053× | 54.56 |
51.97 | 1.050× |
| 32 | 128 | 1 | 64 | 16384 | changed | 103.68 | 100.51 | 1.032× |
102.94 | 99.94 | 1.030× |
| 32 | 128 | 1 | 128 | 16384 | changed | 197.02 | 193.05 | 1.021× |
196.03 | 192.19 | 1.020× |
| 32 | 128 | 1 | 256 | 16384 | changed | 379.26 | 373.47 | 1.016× |
377.08 | 372.12 | 1.013× |
| 32 | 128 | 1 | 8 | 65536 | changed | 58.49 | 55.78 | 1.049× | 57.89 |
55.36 | 1.046× |
| 32 | 128 | 1 | 32 | 65536 | changed | 191.17 | 188.51 | 1.014× |
189.85 | 187.42 | 1.013× |
| 32 | 128 | 1 | 128 | 65536 | unchanged | 723.89 | 723.54 | 1.000× |
719.80 | 720.15 | 1.000× |
| 32 | 128 | 2 | 8 | 4096 | changed | 10.34 | 7.52 | 1.374× | 10.14 |
7.58 | 1.338× |
| 32 | 128 | 2 | 64 | 4096 | changed | 33.70 | 30.53 | 1.104× | 33.15 |
30.14 | 1.100× |
| 32 | 128 | 2 | 256 | 4096 | changed | 111.52 | 105.63 | 1.056× |
110.66 | 104.99 | 1.054× |
| 32 | 128 | 2 | 1 | 16384 | changed | 9.31 | 6.46 | 1.441× | 9.09 |
6.50 | 1.399× |
| 32 | 128 | 2 | 8 | 16384 | changed | 20.00 | 17.18 | 1.164× | 19.62 |
16.96 | 1.157× |
| 32 | 128 | 2 | 32 | 16384 | changed | 56.67 | 54.02 | 1.049× | 56.06 |
53.54 | 1.047× |
| 32 | 128 | 2 | 64 | 16384 | changed | 107.87 | 104.77 | 1.030× |
107.33 | 104.29 | 1.029× |
| 32 | 128 | 2 | 128 | 16384 | changed | 207.45 | 203.55 | 1.019× |
205.89 | 201.98 | 1.019× |
| 32 | 128 | 2 | 256 | 16384 | changed | 400.63 | 395.00 | 1.014× |
396.99 | 391.74 | 1.013× |
| 32 | 128 | 2 | 8 | 65536 | changed | 60.00 | 57.15 | 1.050× | 59.46 |
56.93 | 1.044× |
| 32 | 128 | 2 | 32 | 65536 | changed | 201.12 | 198.37 | 1.014× |
199.14 | 196.63 | 1.013× |
| 32 | 128 | 2 | 128 | 65536 | unchanged | 766.77 | 766.58 | 1.000× |
758.62 | 758.23 | 1.001× |
| 32 | 128 | 3 | 8 | 4096 | changed | 11.39 | 8.74 | 1.304× | 11.17 |
8.61 | 1.297× |
| 32 | 128 | 3 | 64 | 4096 | changed | 35.26 | 32.09 | 1.099× | 34.98 |
31.94 | 1.095× |
| 32 | 128 | 3 | 256 | 4096 | changed | 117.76 | 111.68 | 1.054× |
117.09 | 111.52 | 1.050× |
| 32 | 128 | 3 | 1 | 16384 | changed | 9.66 | 6.75 | 1.431× | 9.44 |
6.75 | 1.398× |
| 32 | 128 | 3 | 8 | 16384 | changed | 21.09 | 18.18 | 1.160× | 20.86 |
18.27 | 1.142× |
| 32 | 128 | 3 | 32 | 16384 | changed | 59.49 | 56.74 | 1.048× | 58.78 |
56.35 | 1.043× |
| 32 | 128 | 3 | 64 | 16384 | changed | 114.59 | 111.52 | 1.028× |
113.02 | 110.30 | 1.025× |
| 32 | 128 | 3 | 128 | 16384 | changed | 218.62 | 214.49 | 1.019× |
216.76 | 212.99 | 1.018× |
| 32 | 128 | 3 | 256 | 16384 | changed | 423.42 | 416.99 | 1.015× |
420.28 | 414.81 | 1.013× |
| 32 | 128 | 3 | 8 | 65536 | changed | 62.98 | 60.29 | 1.045× | 62.34 |
59.71 | 1.044× |
| 32 | 128 | 3 | 32 | 65536 | changed | 212.57 | 210.11 | 1.012× |
210.21 | 207.77 | 1.012× |
| 32 | 128 | 3 | 128 | 65536 | unchanged | 805.83 | 806.15 | 1.000× |
809.76 | 809.67 | 1.000× |
| 32 | 128 | 4 | 8 | 4096 | changed | 11.68 | 9.02 | 1.294× | 11.49 |
8.86 | 1.296× |
| 32 | 128 | 4 | 64 | 4096 | changed | 36.48 | 33.28 | 1.096× | 36.26 |
33.12 | 1.095× |
| 32 | 128 | 4 | 256 | 4096 | changed | 124.09 | 118.50 | 1.047× |
124.06 | 118.66 | 1.046× |
| 32 | 128 | 4 | 1 | 16384 | changed | 10.40 | 7.52 | 1.383× | 10.21 |
7.58 | 1.346× |
| 32 | 128 | 4 | 8 | 16384 | changed | 21.66 | 18.88 | 1.147× | 21.09 |
18.56 | 1.136× |
| 32 | 128 | 4 | 32 | 16384 | changed | 61.85 | 59.04 | 1.048× | 61.18 |
58.56 | 1.045× |
| 32 | 128 | 4 | 64 | 16384 | changed | 120.22 | 117.63 | 1.022× |
120.51 | 117.92 | 1.022× |
| 32 | 128 | 4 | 128 | 16384 | changed | 230.03 | 225.76 | 1.019× |
228.13 | 224.35 | 1.017× |
| 32 | 128 | 4 | 256 | 16384 | changed | 445.47 | 439.16 | 1.014× |
443.16 | 437.42 | 1.013× |
| 32 | 128 | 4 | 8 | 65536 | changed | 65.21 | 62.43 | 1.045× | 64.32 |
61.70 | 1.043× |
| 32 | 128 | 4 | 32 | 65536 | unchanged | 223.20 | 223.25 | 1.000× |
220.09 | 220.25 | 0.999× |
| 32 | 128 | 4 | 128 | 65536 | unchanged | 851.12 | 850.55 | 1.001× |
850.28 | 851.27 | 0.999× |
| 32 | 128 | 5 | 8 | 4096 | unchanged | 11.71 | 11.71 | 1.000× | 11.39 |
11.39 | 1.000× |
| 32 | 128 | 5 | 64 | 4096 | changed | 38.62 | 35.45 | 1.089× | 38.75 |
35.74 | 1.084× |
| 32 | 128 | 5 | 256 | 4096 | unchanged | 138.81 | 138.85 | 1.000× |
137.41 | 137.41 | 1.000× |
| 32 | 128 | 5 | 1 | 16384 | changed | 10.21 | 7.36 | 1.387× | 9.98 |
7.33 | 1.362× |
| 32 | 128 | 5 | 8 | 16384 | changed | 22.50 | 19.78 | 1.138× | 22.24 |
19.62 | 1.134× |
| 32 | 128 | 5 | 32 | 16384 | changed | 67.23 | 64.54 | 1.042× | 66.72 |
64.13 | 1.040× |
| 32 | 128 | 5 | 64 | 16384 | unchanged | 134.17 | 134.14 | 1.000× |
131.71 | 131.74 | 1.000× |
| 32 | 128 | 5 | 128 | 16384 | unchanged | 245.05 | 245.15 | 1.000× |
244.03 | 244.00 | 1.000× |
| 32 | 128 | 5 | 256 | 16384 | changed | 458.23 | 453.27 | 1.011× |
456.12 | 451.39 | 1.010× |
| 32 | 128 | 5 | 8 | 65536 | unchanged | 69.92 | 69.92 | 1.000× | 69.22
| 69.22 | 1.000× |
| 32 | 128 | 5 | 32 | 65536 | unchanged | 236.12 | 236.09 | 1.000× |
235.20 | 235.17 | 1.000× |
| 32 | 128 | 5 | 128 | 65536 | unchanged | 879.99 | 880.77 | 0.999× |
865.00 | 869.37 | 0.995× |
| 32 | 128 | 6 | 8 | 4096 | unchanged | 11.62 | 11.62 | 1.000× | 11.30 |
11.30 | 1.000× |
| 32 | 128 | 6 | 64 | 4096 | changed | 42.53 | 39.14 | 1.087× | 40.93 |
37.89 | 1.080× |
| 32 | 128 | 6 | 256 | 4096 | changed | 154.88 | 148.06 | 1.046× |
152.89 | 145.92 | 1.048× |
| 32 | 128 | 6 | 1 | 16384 | changed | 10.14 | 7.26 | 1.396× | 9.92 |
7.23 | 1.372× |
| 32 | 128 | 6 | 8 | 16384 | changed | 24.58 | 22.02 | 1.116× | 24.73 |
22.14 | 1.117× |
| 32 | 128 | 6 | 32 | 16384 | unchanged | 72.51 | 72.48 | 1.000× | 72.42
| 72.45 | 1.000× |
| 32 | 128 | 6 | 64 | 16384 | changed | 148.32 | 144.86 | 1.024× |
146.69 | 143.33 | 1.023× |
| 32 | 128 | 6 | 128 | 16384 | changed | 274.14 | 269.79 | 1.016× |
270.94 | 266.72 | 1.016× |
| 32 | 128 | 6 | 256 | 16384 | unchanged | 547.24 | 547.51 | 1.000× |
543.61 | 543.45 | 1.000× |
| 32 | 128 | 6 | 8 | 65536 | changed | 75.10 | 72.16 | 1.041× | 75.26 |
72.48 | 1.038× |
| 32 | 128 | 6 | 32 | 65536 | unchanged | 264.96 | 264.83 | 1.000× |
262.01 | 261.56 | 1.002× |
| 32 | 128 | 6 | 128 | 65536 | unchanged | 1078.83 | 1079.09 | 1.000× |
1066.40 | 1066.87 | 1.000× |
| 64 | 64 | 1 | 8 | 4096 | changed | 10.27 | 7.49 | 1.372× | 10.05 |
7.42 | 1.353× |
| 64 | 64 | 1 | 64 | 4096 | changed | 33.34 | 30.11 | 1.107× | 32.90 |
29.82 | 1.103× |
| 64 | 64 | 1 | 256 | 4096 | changed | 108.03 | 102.08 | 1.058× | 106.85
| 101.22 | 1.056× |
| 64 | 64 | 1 | 1 | 16384 | changed | 9.25 | 6.34 | 1.459× | 8.96 | 6.37
| 1.407× |
| 64 | 64 | 1 | 8 | 16384 | changed | 19.97 | 17.15 | 1.164× | 19.46 |
16.83 | 1.156× |
| 64 | 64 | 1 | 32 | 16384 | changed | 55.65 | 52.89 | 1.052× | 55.04 |
52.45 | 1.049× |
| 64 | 64 | 1 | 64 | 16384 | changed | 104.67 | 101.57 | 1.031× | 103.74
| 100.70 | 1.030× |
| 64 | 64 | 1 | 128 | 16384 | changed | 198.62 | 194.46 | 1.021× |
196.80 | 192.90 | 1.020× |
| 64 | 64 | 1 | 256 | 16384 | changed | 381.82 | 376.12 | 1.015× |
379.36 | 374.01 | 1.014× |
| 64 | 64 | 1 | 8 | 65536 | changed | 59.01 | 56.29 | 1.048× | 58.37 |
55.87 | 1.045× |
| 64 | 64 | 1 | 32 | 65536 | changed | 192.06 | 189.28 | 1.015× | 190.91
| 188.32 | 1.014× |
| 64 | 64 | 1 | 128 | 65536 | unchanged | 726.45 | 726.58 | 1.000× |
725.37 | 725.18 | 1.000× |
| 64 | 64 | 2 | 8 | 4096 | changed | 11.07 | 8.29 | 1.336× | 10.82 |
8.22 | 1.315× |
| 64 | 64 | 2 | 64 | 4096 | changed | 35.39 | 32.16 | 1.100× | 34.94 |
31.81 | 1.099× |
| 64 | 64 | 2 | 256 | 4096 | changed | 115.20 | 109.28 | 1.054× | 114.75
| 109.18 | 1.051× |
| 64 | 64 | 2 | 1 | 16384 | changed | 9.73 | 6.82 | 1.427× | 9.31 | 6.66
| 1.399× |
| 64 | 64 | 2 | 8 | 16384 | changed | 20.93 | 18.21 | 1.149× | 20.67 |
18.08 | 1.143× |
| 64 | 64 | 2 | 32 | 16384 | changed | 58.49 | 55.71 | 1.050× | 57.66 |
55.20 | 1.045× |
| 64 | 64 | 2 | 64 | 16384 | changed | 111.42 | 108.26 | 1.029× | 110.34
| 107.49 | 1.026× |
| 64 | 64 | 2 | 128 | 16384 | changed | 212.41 | 208.41 | 1.019× |
210.88 | 207.01 | 1.019× |
| 64 | 64 | 2 | 256 | 16384 | changed | 409.37 | 403.58 | 1.014× |
408.64 | 402.88 | 1.014× |
| 64 | 64 | 2 | 8 | 65536 | changed | 61.82 | 58.98 | 1.048× | 61.15 |
58.56 | 1.044× |
| 64 | 64 | 2 | 32 | 65536 | changed | 205.25 | 202.62 | 1.013× | 203.52
| 200.89 | 1.013× |
| 64 | 64 | 2 | 128 | 65536 | unchanged | 782.90 | 783.49 | 0.999× |
775.63 | 775.45 | 1.000× |
| 64 | 64 | 3 | 8 | 4096 | unchanged | 11.94 | 11.94 | 1.000× | 11.65 |
11.68 | 0.997× |
| 64 | 64 | 3 | 64 | 4096 | changed | 39.01 | 35.71 | 1.092× | 38.75 |
35.71 | 1.085× |
| 64 | 64 | 3 | 256 | 4096 | unchanged | 150.94 | 150.91 | 1.000× |
147.39 | 147.42 | 1.000× |
| 64 | 64 | 3 | 1 | 16384 | changed | 10.43 | 7.55 | 1.381× | 10.08 |
7.52 | 1.340× |
| 64 | 64 | 3 | 8 | 16384 | changed | 23.49 | 21.06 | 1.116× | 22.97 |
20.48 | 1.122× |
| 64 | 64 | 3 | 32 | 16384 | unchanged | 65.06 | 65.06 | 1.000× | 65.41
| 65.44 | 1.000× |
| 64 | 64 | 3 | 64 | 16384 | unchanged | 145.50 | 145.57 | 1.000× |
143.36 | 143.45 | 0.999× |
| 64 | 64 | 3 | 128 | 16384 | unchanged | 269.16 | 269.18 | 1.000× |
266.81 | 266.65 | 1.001× |
| 64 | 64 | 3 | 256 | 16384 | unchanged | 520.09 | 519.80 | 1.001× |
516.96 | 517.31 | 0.999× |
| 64 | 64 | 3 | 8 | 65536 | changed | 67.58 | 64.83 | 1.042× | 69.25 |
66.34 | 1.044× |
| 64 | 64 | 3 | 32 | 65536 | unchanged | 259.23 | 259.26 | 1.000× |
256.19 | 256.89 | 0.997× |
| 64 | 64 | 3 | 128 | 65536 | unchanged | 1023.09 | 1023.19 | 1.000× |
1020.34 | 1018.58 | 1.002× |
| 64 | 64 | 4 | 8 | 4096 | unchanged | 11.84 | 11.84 | 1.000× | 11.65 |
11.65 | 1.000× |
| 64 | 64 | 4 | 64 | 4096 | changed | 42.56 | 39.20 | 1.086× | 41.98 |
38.75 | 1.083× |
| 64 | 64 | 4 | 256 | 4096 | changed | 186.56 | 180.09 | 1.036× | 183.58
| 176.74 | 1.039× |
| 64 | 64 | 4 | 1 | 16384 | changed | 10.40 | 7.55 | 1.377× | 10.11 |
7.49 | 1.350× |
| 64 | 64 | 4 | 8 | 16384 | changed | 25.63 | 23.07 | 1.111× | 25.02 |
22.72 | 1.101× |
| 64 | 64 | 4 | 32 | 16384 | changed | 75.10 | 72.32 | 1.039× | 78.14 |
75.07 | 1.041× |
| 64 | 64 | 4 | 64 | 16384 | changed | 181.88 | 178.08 | 1.021× | 178.46
| 175.10 | 1.019× |
| 64 | 64 | 4 | 128 | 16384 | changed | 342.75 | 338.73 | 1.012× |
337.85 | 334.27 | 1.011× |
| 64 | 64 | 4 | 256 | 16384 | changed | 670.74 | 665.43 | 1.008× |
659.82 | 653.96 | 1.009× |
| 64 | 64 | 4 | 8 | 65536 | unchanged | 77.34 | 77.38 | 1.000× | 81.18 |
81.25 | 0.999× |
| 64 | 64 | 4 | 32 | 65536 | changed | 330.91 | 328.44 | 1.008× | 326.53
| 324.52 | 1.006× |
| 64 | 64 | 4 | 128 | 65536 | unchanged | 1328.75 | 1328.59 | 1.000× |
1309.81 | 1311.39 | 0.999× |
| 64 | 64 | 5 | 8 | 4096 | changed | 13.82 | 11.10 | 1.245× | 13.47 |
10.91 | 1.235× |
| 64 | 64 | 5 | 64 | 4096 | changed | 53.34 | 50.08 | 1.065× | 52.54 |
49.47 | 1.062× |
| 64 | 64 | 5 | 256 | 4096 | unchanged | 253.40 | 253.31 | 1.000× |
249.05 | 249.02 | 1.000× |
| 64 | 64 | 5 | 1 | 16384 | changed | 11.46 | 8.57 | 1.336× | 11.10 |
8.48 | 1.309× |
| 64 | 64 | 5 | 8 | 16384 | changed | 31.23 | 28.41 | 1.099× | 30.62 |
28.09 | 1.090× |
| 64 | 64 | 5 | 32 | 16384 | changed | 116.22 | 113.86 | 1.021× | 115.20
| 112.89 | 1.020× |
| 64 | 64 | 5 | 64 | 16384 | changed, CE (760) | 220.09 | 216.44 |
1.017×² | 217.21 | 213.85 | 1.016× |
| 64 | 64 | 5 | 128 | 16384 | unchanged | 496.70 | 496.41 | 1.001× |
490.96 | 490.84 | 1.000× |
| 64 | 64 | 5 | 256 | 16384 | unchanged | 929.32 | 928.31 | 1.001× |
923.32 | 923.58 | 1.000× |
| 64 | 64 | 5 | 8 | 65536 | changed | 122.21 | 119.61 | 1.022× | 120.61
| 118.14 | 1.021× |
| 64 | 64 | 5 | 32 | 65536 | unchanged | 521.90 | 520.94 | 1.002× |
516.99 | 517.28 | 0.999× |
| 64 | 64 | 5 | 128 | 65536 | unchanged | 1908.92 | 1908.21 | 1.000× |
1889.48 | 1896.55 | 0.996× |
| 64 | 64 | 6 | 8 | 4096 | changed | 13.82 | 11.14 | 1.241× | 13.47 |
10.85 | 1.242× |
| 64 | 64 | 6 | 64 | 4096 | changed | 52.67 | 49.41 | 1.066× | 52.29 |
49.25 | 1.062× |
| 64 | 64 | 6 | 256 | 4096 | unchanged | 275.32 | 275.23 | 1.000× |
271.45 | 271.52 | 1.000× |
| 64 | 64 | 6 | 1 | 16384 | changed | 11.36 | 8.51 | 1.335× | 11.07 |
8.38 | 1.321× |
| 64 | 64 | 6 | 8 | 16384 | changed | 31.01 | 28.06 | 1.105× | 30.21 |
27.55 | 1.096× |
| 64 | 64 | 6 | 32 | 16384 | changed | 117.06 | 114.59 | 1.022× | 116.57
| 114.05 | 1.022× |
| 64 | 64 | 6 | 64 | 16384 | unchanged | 268.93 | 268.96 | 1.000× |
264.16 | 264.25 | 1.000× |
| 64 | 64 | 6 | 128 | 16384 | unchanged | 516.95 | 516.51 | 1.001× |
510.92 | 510.36 | 1.001× |
| 64 | 64 | 6 | 256 | 16384 | unchanged | 1038.39 | 1038.83 | 1.000× |
1018.47 | 1015.38 | 1.003× |
| 64 | 64 | 6 | 8 | 65536 | changed | 120.57 | 118.30 | 1.019× | 120.67
| 117.76 | 1.025× |
| 64 | 64 | 6 | 32 | 65536 | unchanged | 527.87 | 528.09 | 1.000× |
527.29 | 527.67 | 0.999× |
| 64 | 64 | 6 | 128 | 65536 | unchanged | 2049.91 | 2049.41 | 1.000× |
2010.89 | 2010.67 | 1.000× |

**RTX PRO 6000**

| heads | page | next_n | batch | context | state | baseline µs (760) |
new µs | speedup | baseline µs (52021) | new µs | speedup |
|---:|---:|---:|---:|---:|:--|---:|---:|---:|---:|---:|---:|
| 32 | 64 | 1 | 8 | 4096 | changed | 14.40 | 11.10 | 1.297× | 14.43 |
11.14 | 1.296× |
| 32 | 64 | 1 | 64 | 4096 | changed | 44.51 | 40.90 | 1.088× | 44.32 |
40.67 | 1.090× |
| 32 | 64 | 1 | 256 | 4096 | changed | 131.97 | 125.34 | 1.053× | 132.48
| 125.76 | 1.053× |
| 32 | 64 | 1 | 1 | 16384 | changed | 11.55 | 8.16 | 1.416× | 11.55 |
8.16 | 1.416× |
| 32 | 64 | 1 | 8 | 16384 | changed | 27.36 | 24.13 | 1.134× | 27.17 |
23.90 | 1.137× |
| 32 | 64 | 1 | 32 | 16384 | unchanged | 73.41 | 73.41 | 1.000× | 73.70
| 73.70 | 1.000× |
| 32 | 64 | 1 | 64 | 16384 | changed | 128.48 | 124.77 | 1.030× | 129.22
| 125.51 | 1.030× |
| 32 | 64 | 1 | 128 | 16384 | changed | 230.02 | 225.44 | 1.020× |
229.79 | 225.28 | 1.020× |
| 32 | 64 | 1 | 256 | 16384 | changed | 431.33 | 425.09 | 1.015× |
431.43 | 424.90 | 1.015× |
| 32 | 64 | 1 | 8 | 65536 | unchanged | 79.04 | 79.04 | 1.000× | 78.98 |
78.98 | 1.000× |
| 32 | 64 | 1 | 32 | 65536 | changed | 223.04 | 219.87 | 1.014× | 223.55
| 220.38 | 1.014× |
| 32 | 64 | 1 | 128 | 65536 | unchanged | 818.43 | 818.51 | 1.000× |
821.62 | 821.51 | 1.000× |
| 32 | 64 | 2 | 8 | 4096 | changed | 14.69 | 11.52 | 1.275× | 14.78 |
11.55 | 1.280× |
| 32 | 64 | 2 | 64 | 4096 | changed | 44.83 | 41.28 | 1.086× | 44.96 |
41.41 | 1.086× |
| 32 | 64 | 2 | 256 | 4096 | changed | 136.67 | 130.02 | 1.051× | 136.74
| 130.15 | 1.051× |
| 32 | 64 | 2 | 1 | 16384 | changed | 11.97 | 8.58 | 1.396× | 11.90 |
8.48 | 1.404× |
| 32 | 64 | 2 | 8 | 16384 | changed | 27.42 | 24.22 | 1.132× | 27.42 |
24.22 | 1.132× |
| 32 | 64 | 2 | 32 | 16384 | unchanged | 74.02 | 74.02 | 1.000× | 74.69
| 74.69 | 1.000× |
| 32 | 64 | 2 | 64 | 16384 | changed | 132.67 | 128.99 | 1.029× | 132.77
| 129.15 | 1.028× |
| 32 | 64 | 2 | 128 | 16384 | changed | 236.77 | 232.13 | 1.020× |
237.41 | 232.99 | 1.019× |
| 32 | 64 | 2 | 256 | 16384 | changed | 447.55 | 441.31 | 1.014× |
446.75 | 440.26 | 1.015× |
| 32 | 64 | 2 | 8 | 65536 | unchanged | 80.03 | 80.03 | 1.000× | 79.81 |
79.81 | 1.000× |
| 32 | 64 | 2 | 32 | 65536 | changed | 230.50 | 227.49 | 1.013× | 230.56
| 227.42 | 1.014× |
| 32 | 64 | 2 | 128 | 65536 | unchanged | 848.71 | 848.58 | 1.000× |
849.06 | 849.03 | 1.000× |
| 32 | 64 | 3 | 8 | 4096 | changed | 15.20 | 11.94 | 1.273× | 15.23 |
12.00 | 1.269× |
| 32 | 64 | 3 | 64 | 4096 | changed | 45.47 | 41.92 | 1.085× | 45.38 |
41.82 | 1.085× |
| 32 | 64 | 3 | 256 | 4096 | changed | 140.42 | 133.70 | 1.050× | 140.67
| 133.86 | 1.051× |
| 32 | 64 | 3 | 1 | 16384 | changed | 12.38 | 8.99 | 1.377× | 12.38 |
8.93 | 1.387× |
| 32 | 64 | 3 | 8 | 16384 | changed | 27.81 | 24.61 | 1.130× | 27.65 |
24.48 | 1.129× |
| 32 | 64 | 3 | 32 | 16384 | unchanged | 75.90 | 75.91 | 1.000× | 75.07
| 75.07 | 1.000× |
| 32 | 64 | 3 | 64 | 16384 | changed | 136.54 | 132.87 | 1.028× | 136.48
| 132.77 | 1.028× |
| 32 | 64 | 3 | 128 | 16384 | changed | 245.70 | 241.06 | 1.019× |
245.76 | 241.03 | 1.020× |
| 32 | 64 | 3 | 256 | 16384 | changed | 461.03 | 454.08 | 1.015× |
461.09 | 454.24 | 1.015× |
| 32 | 64 | 3 | 8 | 65536 | unchanged | 79.74 | 79.74 | 1.000× | 79.71 |
79.71 | 1.000× |
| 32 | 64 | 3 | 32 | 65536 | changed | 237.06 | 233.86 | 1.014× | 236.93
| 233.86 | 1.013× |
| 32 | 64 | 3 | 128 | 65536 | unchanged | 875.04 | 875.11 | 1.000× |
874.75 | 874.63 | 1.000× |
| 32 | 64 | 4 | 8 | 4096 | unchanged | 15.10 | 15.10 | 1.000× | 15.04 |
15.04 | 1.000× |
| 32 | 64 | 4 | 64 | 4096 | changed | 46.56 | 42.98 | 1.083× | 46.37 |
42.82 | 1.083× |
| 32 | 64 | 4 | 256 | 4096 | changed | 145.31 | 138.56 | 1.049× | 146.18
| 139.36 | 1.049× |
| 32 | 64 | 4 | 1 | 16384 | changed | 13.34 | 9.95 | 1.341× | 13.34 |
9.98 | 1.337× |
| 32 | 64 | 4 | 8 | 16384 | changed | 28.06 | 24.87 | 1.129× | 28.03 |
24.80 | 1.130× |
| 32 | 64 | 4 | 32 | 16384 | changed | 76.96 | 73.95 | 1.041× | 77.06 |
74.05 | 1.041× |
| 32 | 64 | 4 | 64 | 16384 | changed | 140.55 | 136.93 | 1.026× | 140.61
| 136.86 | 1.027× |
| 32 | 64 | 4 | 128 | 16384 | changed | 253.34 | 248.67 | 1.019× |
252.16 | 247.46 | 1.019× |
| 32 | 64 | 4 | 256 | 16384 | changed | 475.01 | 468.61 | 1.014× |
477.06 | 469.92 | 1.015× |
| 32 | 64 | 4 | 8 | 65536 | unchanged | 80.80 | 80.77 | 1.000× | 80.16 |
80.13 | 1.000× |
| 32 | 64 | 4 | 32 | 65536 | changed | 243.49 | 240.19 | 1.014× | 243.52
| 240.58 | 1.012× |
| 32 | 64 | 4 | 128 | 65536 | unchanged | 900.83 | 900.99 | 1.000× |
900.84 | 900.87 | 1.000× |
| 32 | 64 | 5 | 8 | 4096 | unchanged | 15.81 | 15.81 | 1.000× | 15.84 |
15.84 | 1.000× |
| 32 | 64 | 5 | 64 | 4096 | changed | 47.07 | 43.49 | 1.082× | 47.26 |
43.68 | 1.082× |
| 32 | 64 | 5 | 256 | 4096 | changed | 151.71 | 144.74 | 1.048× | 151.91
| 144.80 | 1.049× |
| 32 | 64 | 5 | 1 | 16384 | changed | 13.47 | 10.08 | 1.337× | 13.54 |
10.08 | 1.343× |
| 32 | 64 | 5 | 8 | 16384 | changed | 28.19 | 25.02 | 1.127× | 28.19 |
25.02 | 1.127× |
| 32 | 64 | 5 | 32 | 16384 | unchanged | 77.86 | 77.86 | 1.000× | 77.86
| 77.86 | 1.000× |
| 32 | 64 | 5 | 64 | 16384 | changed | 146.75 | 143.04 | 1.026× | 147.07
| 143.58 | 1.024× |
| 32 | 64 | 5 | 128 | 16384 | changed | 262.56 | 257.50 | 1.020× |
261.06 | 256.38 | 1.018× |
| 32 | 64 | 5 | 256 | 16384 | changed | 492.90 | 486.37 | 1.013× |
491.62 | 484.19 | 1.015× |
| 32 | 64 | 5 | 8 | 65536 | unchanged | 83.71 | 83.71 | 1.000× | 81.22 |
81.22 | 1.000× |
| 32 | 64 | 5 | 32 | 65536 | changed | 253.06 | 249.73 | 1.013× | 251.11
| 247.97 | 1.013× |
| 32 | 64 | 5 | 128 | 65536 | unchanged | 927.60 | 927.59 | 1.000× |
929.57 | 929.64 | 1.000× |
| 32 | 64 | 6 | 8 | 4096 | unchanged | 15.87 | 15.87 | 1.000× | 15.90 |
15.90 | 1.000× |
| 32 | 64 | 6 | 64 | 4096 | changed | 48.13 | 44.48 | 1.082× | 47.62 |
44.06 | 1.081× |
| 32 | 64 | 6 | 256 | 4096 | changed | 156.13 | 149.66 | 1.043× | 155.78
| 149.15 | 1.044× |
| 32 | 64 | 6 | 1 | 16384 | changed | 13.44 | 10.02 | 1.342× | 13.47 |
10.05 | 1.341× |
| 32 | 64 | 6 | 8 | 16384 | changed | 28.61 | 25.38 | 1.127× | 28.45 |
25.25 | 1.127× |
| 32 | 64 | 6 | 32 | 16384 | unchanged | 82.24 | 82.24 | 1.000× | 81.79
| 81.79 | 1.000× |
| 32 | 64 | 6 | 64 | 16384 | changed | 149.22 | 145.63 | 1.025× | 149.54
| 145.70 | 1.026× |
| 32 | 64 | 6 | 128 | 16384 | changed | 267.78 | 263.01 | 1.018× |
267.94 | 263.23 | 1.018× |
| 32 | 64 | 6 | 256 | 16384 | unchanged | 512.24 | 512.00 | 1.000× |
508.58 | 508.51 | 1.000× |
| 32 | 64 | 6 | 8 | 65536 | changed | 84.51 | 81.41 | 1.038× | 85.19 |
81.95 | 1.039× |
| 32 | 64 | 6 | 32 | 65536 | unchanged | 259.01 | 259.04 | 1.000× |
259.39 | 259.43 | 1.000× |
| 32 | 64 | 6 | 128 | 65536 | unchanged | 975.65 | 975.55 | 1.000× |
976.20 | 976.36 | 1.000× |
| 32 | 128 | 1 | 8 | 4096 | changed | 14.37 | 11.07 | 1.298× | 14.43 |
11.14 | 1.296× |
| 32 | 128 | 1 | 64 | 4096 | changed | 44.83 | 41.25 | 1.087× | 44.86 |
41.22 | 1.089× |
| 32 | 128 | 1 | 256 | 4096 | changed | 131.84 | 125.12 | 1.054× |
131.81 | 125.15 | 1.053× |
| 32 | 128 | 1 | 1 | 16384 | changed | 11.74 | 8.35 | 1.406× | 11.71 |
8.32 | 1.408× |
| 32 | 128 | 1 | 8 | 16384 | changed | 27.42 | 24.22 | 1.132× | 27.33 |
24.13 | 1.133× |
| 32 | 128 | 1 | 32 | 16384 | changed | 75.62 | 72.45 | 1.044× | 75.87 |
72.77 | 1.043× |
| 32 | 128 | 1 | 64 | 16384 | changed | 128.86 | 125.22 | 1.029× |
128.67 | 125.02 | 1.029× |
| 32 | 128 | 1 | 128 | 16384 | changed | 229.38 | 224.90 | 1.020× |
229.31 | 224.64 | 1.021× |
| 32 | 128 | 1 | 256 | 16384 | changed | 430.62 | 424.03 | 1.016× |
430.34 | 423.78 | 1.015× |
| 32 | 128 | 1 | 8 | 65536 | unchanged | 79.42 | 79.42 | 1.000× | 78.85
| 78.85 | 1.000× |
| 32 | 128 | 1 | 32 | 65536 | changed | 222.72 | 219.55 | 1.014× |
222.85 | 219.75 | 1.014× |
| 32 | 128 | 1 | 128 | 65536 | unchanged | 818.69 | 818.69 | 1.000× |
816.74 | 816.82 | 1.000× |
| 32 | 128 | 2 | 8 | 4096 | changed | 14.85 | 11.58 | 1.282× | 14.82 |
11.62 | 1.275× |
| 32 | 128 | 2 | 64 | 4096 | changed | 45.12 | 41.60 | 1.085× | 44.86 |
41.28 | 1.087× |
| 32 | 128 | 2 | 256 | 4096 | changed | 136.61 | 129.86 | 1.052× |
136.48 | 129.89 | 1.051× |
| 32 | 128 | 2 | 1 | 16384 | changed | 12.00 | 8.61 | 1.394× | 11.94 |
8.58 | 1.392× |
| 32 | 128 | 2 | 8 | 16384 | changed | 27.46 | 24.29 | 1.130× | 27.58 |
24.38 | 1.131× |
| 32 | 128 | 2 | 32 | 16384 | changed | 75.52 | 72.35 | 1.044× | 75.46 |
72.35 | 1.043× |
| 32 | 128 | 2 | 64 | 16384 | changed | 132.74 | 129.12 | 1.028× |
132.00 | 128.51 | 1.027× |
| 32 | 128 | 2 | 128 | 16384 | changed | 237.50 | 232.83 | 1.020× |
237.60 | 232.99 | 1.020× |
| 32 | 128 | 2 | 256 | 16384 | changed | 445.92 | 439.27 | 1.015× |
445.35 | 438.79 | 1.015× |
| 32 | 128 | 2 | 8 | 65536 | unchanged | 79.49 | 79.46 | 1.000× | 79.20
| 79.20 | 1.000× |
| 32 | 128 | 2 | 32 | 65536 | changed | 229.47 | 226.46 | 1.013× |
229.38 | 226.37 | 1.013× |
| 32 | 128 | 2 | 128 | 65536 | unchanged | 847.33 | 847.27 | 1.000× |
846.45 | 846.50 | 1.000× |
| 32 | 128 | 3 | 8 | 4096 | changed | 15.17 | 11.94 | 1.271× | 15.17 |
11.97 | 1.267× |
| 32 | 128 | 3 | 64 | 4096 | changed | 45.63 | 41.98 | 1.087× | 45.82 |
42.24 | 1.085× |
| 32 | 128 | 3 | 256 | 4096 | changed | 141.41 | 134.62 | 1.050× |
141.09 | 134.30 | 1.051× |
| 32 | 128 | 3 | 1 | 16384 | changed | 12.67 | 9.31 | 1.361× | 12.64 |
9.25 | 1.367× |
| 32 | 128 | 3 | 8 | 16384 | changed | 27.71 | 24.45 | 1.134× | 27.78 |
24.58 | 1.130× |
| 32 | 128 | 3 | 32 | 16384 | unchanged | 75.27 | 75.26 | 1.000× | 74.72
| 74.72 | 1.000× |
| 32 | 128 | 3 | 64 | 16384 | changed | 136.93 | 133.25 | 1.028× |
136.90 | 133.31 | 1.027× |
| 32 | 128 | 3 | 128 | 16384 | changed | 245.15 | 240.48 | 1.019× |
244.55 | 239.75 | 1.020× |
| 32 | 128 | 3 | 256 | 16384 | changed | 462.27 | 454.85 | 1.016× |
460.71 | 454.02 | 1.015× |
| 32 | 128 | 3 | 8 | 65536 | unchanged | 80.22 | 80.22 | 1.000× | 79.81
| 79.81 | 1.000× |
| 32 | 128 | 3 | 32 | 65536 | changed | 236.39 | 233.19 | 1.014× |
236.22 | 233.28 | 1.013× |
| 32 | 128 | 3 | 128 | 65536 | unchanged | 871.91 | 871.91 | 1.000× |
873.76 | 873.92 | 1.000× |
| 32 | 128 | 4 | 8 | 4096 | changed | 15.23 | 12.06 | 1.263× | 15.10 |
11.87 | 1.272× |
| 32 | 128 | 4 | 64 | 4096 | changed | 46.08 | 42.56 | 1.083× | 46.30 |
42.94 | 1.078× |
| 32 | 128 | 4 | 256 | 4096 | changed | 146.34 | 139.62 | 1.048× |
146.69 | 139.58 | 1.051× |
| 32 | 128 | 4 | 1 | 16384 | changed | 13.50 | 10.11 | 1.335× | 13.47 |
10.14 | 1.328× |
| 32 | 128 | 4 | 8 | 16384 | changed | 28.03 | 24.90 | 1.126× | 28.03 |
24.90 | 1.126× |
| 32 | 128 | 4 | 32 | 16384 | changed | 77.57 | 74.59 | 1.040× | 77.28 |
74.14 | 1.042× |
| 32 | 128 | 4 | 64 | 16384 | changed | 141.28 | 137.47 | 1.028× |
140.61 | 136.99 | 1.026× |
| 32 | 128 | 4 | 128 | 16384 | changed | 251.97 | 247.20 | 1.019× |
251.91 | 247.07 | 1.020× |
| 32 | 128 | 4 | 256 | 16384 | changed | 474.79 | 467.71 | 1.015× |
474.05 | 466.88 | 1.015× |
| 32 | 128 | 4 | 8 | 65536 | unchanged | 79.97 | 79.94 | 1.000× | 80.26
| 80.26 | 1.000× |
| 32 | 128 | 4 | 32 | 65536 | changed | 244.94 | 241.63 | 1.014× |
244.13 | 240.96 | 1.013× |
| 32 | 128 | 4 | 128 | 65536 | unchanged | 897.44 | 897.76 | 1.000× |
899.72 | 899.65 | 1.000× |
| 32 | 128 | 5 | 8 | 4096 | unchanged | 15.81 | 15.81 | 1.000× | 15.78 |
15.78 | 1.000× |
| 32 | 128 | 5 | 64 | 4096 | changed | 47.46 | 43.90 | 1.081× | 47.33 |
43.71 | 1.083× |
| 32 | 128 | 5 | 256 | 4096 | changed | 152.19 | 145.18 | 1.048× |
152.29 | 145.50 | 1.047× |
| 32 | 128 | 5 | 1 | 16384 | changed | 13.44 | 9.98 | 1.346× | 13.41 |
10.05 | 1.334× |
| 32 | 128 | 5 | 8 | 16384 | changed | 28.22 | 24.99 | 1.129× | 28.51 |
25.25 | 1.129× |
| 32 | 128 | 5 | 32 | 16384 | changed | 78.66 | 75.52 | 1.042× | 78.82 |
75.62 | 1.042× |
| 32 | 128 | 5 | 64 | 16384 | changed | 146.56 | 142.56 | 1.028× |
147.04 | 143.39 | 1.025× |
| 32 | 128 | 5 | 128 | 16384 | changed | 261.99 | 256.93 | 1.020× |
261.09 | 256.38 | 1.018× |
| 32 | 128 | 5 | 256 | 16384 | changed | 493.34 | 486.31 | 1.014× |
491.68 | 484.77 | 1.014× |
| 32 | 128 | 5 | 8 | 65536 | unchanged | 83.71 | 83.68 | 1.000× | 83.30
| 83.33 | 1.000× |
| 32 | 128 | 5 | 32 | 65536 | changed | 252.48 | 249.15 | 1.013× |
251.74 | 248.74 | 1.012× |
| 32 | 128 | 5 | 128 | 65536 | unchanged | 928.58 | 928.48 | 1.000× |
926.53 | 926.98 | 1.000× |
| 32 | 128 | 6 | 8 | 4096 | unchanged | 15.90 | 15.90 | 1.000× | 15.90 |
15.90 | 1.000× |
| 32 | 128 | 6 | 64 | 4096 | changed | 47.71 | 44.10 | 1.082× | 47.94 |
44.29 | 1.082× |
| 32 | 128 | 6 | 256 | 4096 | changed | 155.94 | 148.83 | 1.048× |
156.06 | 149.02 | 1.047× |
| 32 | 128 | 6 | 1 | 16384 | changed | 13.41 | 10.05 | 1.334× | 13.47 |
10.14 | 1.328× |
| 32 | 128 | 6 | 8 | 16384 | changed | 28.45 | 25.28 | 1.125× | 28.67 |
25.47 | 1.126× |
| 32 | 128 | 6 | 32 | 16384 | unchanged | 80.03 | 80.00 | 1.000× | 79.65
| 79.65 | 1.000× |
| 32 | 128 | 6 | 64 | 16384 | changed | 149.73 | 146.27 | 1.024× |
149.73 | 145.99 | 1.026× |
| 32 | 128 | 6 | 128 | 16384 | changed | 271.84 | 267.39 | 1.017× |
269.82 | 264.87 | 1.019× |
| 32 | 128 | 6 | 256 | 16384 | unchanged | 508.87 | 508.80 | 1.000× |
509.67 | 509.63 | 1.000× |
| 32 | 128 | 6 | 8 | 65536 | unchanged | 84.64 | 84.64 | 1.000× | 85.98
| 85.95 | 1.000× |
| 32 | 128 | 6 | 32 | 65536 | unchanged | 258.21 | 258.18 | 1.000× |
258.08 | 258.08 | 1.000× |
| 32 | 128 | 6 | 128 | 65536 | unchanged | 973.67 | 974.12 | 1.000× |
973.35 | 973.16 | 1.000× |
| 64 | 64 | 1 | 8 | 4096 | changed | 14.56 | 11.33 | 1.285× | 14.66 |
11.42 | 1.283× |
| 64 | 64 | 1 | 64 | 4096 | changed | 45.15 | 41.47 | 1.089× | 44.96 |
41.34 | 1.087× |
| 64 | 64 | 1 | 256 | 4096 | changed | 133.47 | 126.75 | 1.053× | 133.22
| 126.72 | 1.051× |
| 64 | 64 | 1 | 1 | 16384 | changed | 11.87 | 8.45 | 1.405× | 11.81 |
8.42 | 1.403× |
| 64 | 64 | 1 | 8 | 16384 | changed | 27.58 | 24.32 | 1.134× | 27.58 |
24.39 | 1.131× |
| 64 | 64 | 1 | 32 | 16384 | unchanged | 73.89 | 73.89 | 1.000× | 74.08
| 74.08 | 1.000× |
| 64 | 64 | 1 | 64 | 16384 | changed | 129.41 | 125.73 | 1.029× | 129.76
| 126.11 | 1.029× |
| 64 | 64 | 1 | 128 | 16384 | changed | 230.72 | 226.02 | 1.021× |
231.17 | 226.69 | 1.020× |
| 64 | 64 | 1 | 256 | 16384 | changed | 434.37 | 427.68 | 1.016× |
435.14 | 428.29 | 1.016× |
| 64 | 64 | 1 | 8 | 65536 | unchanged | 79.36 | 79.36 | 1.000× | 79.42 |
79.42 | 1.000× |
| 64 | 64 | 1 | 32 | 65536 | changed | 224.00 | 220.83 | 1.014× | 224.29
| 221.03 | 1.015× |
| 64 | 64 | 1 | 128 | 65536 | unchanged | 822.69 | 822.83 | 1.000× |
822.12 | 822.02 | 1.000× |
| 64 | 64 | 2 | 8 | 4096 | changed | 15.14 | 11.87 | 1.275× | 15.23 |
11.90 | 1.279× |
| 64 | 64 | 2 | 64 | 4096 | changed | 45.79 | 42.27 | 1.083× | 45.98 |
42.50 | 1.082× |
| 64 | 64 | 2 | 256 | 4096 | changed | 139.84 | 133.18 | 1.050× | 139.81
| 133.31 | 1.049× |
| 64 | 64 | 2 | 1 | 16384 | changed | 12.35 | 8.99 | 1.374× | 12.38 |
8.99 | 1.377× |
| 64 | 64 | 2 | 8 | 16384 | changed | 28.10 | 24.87 | 1.130× | 28.00 |
24.80 | 1.129× |
| 64 | 64 | 2 | 32 | 16384 | changed | 76.99 | 73.82 | 1.043× | 77.66 |
74.40 | 1.044× |
| 64 | 64 | 2 | 64 | 16384 | changed | 135.33 | 131.68 | 1.028× | 135.36
| 131.58 | 1.029× |
| 64 | 64 | 2 | 128 | 16384 | changed | 240.71 | 236.26 | 1.019× |
241.02 | 236.35 | 1.020× |
| 64 | 64 | 2 | 256 | 16384 | changed | 453.47 | 447.07 | 1.014× |
453.38 | 446.59 | 1.015× |
| 64 | 64 | 2 | 8 | 65536 | unchanged | 79.55 | 79.58 | 1.000× | 79.33 |
79.33 | 1.000× |
| 64 | 64 | 2 | 32 | 65536 | changed | 233.38 | 230.34 | 1.013× | 233.50
| 230.31 | 1.014× |
| 64 | 64 | 2 | 128 | 65536 | unchanged | 857.76 | 857.89 | 1.000× |
856.29 | 856.48 | 1.000× |
| 64 | 64 | 3 | 8 | 4096 | unchanged | 15.68 | 15.68 | 1.000× | 15.65 |
15.65 | 1.000× |
| 64 | 64 | 3 | 64 | 4096 | changed | 47.68 | 44.10 | 1.081× | 47.49 |
43.90 | 1.082× |
| 64 | 64 | 3 | 256 | 4096 | changed | 146.18 | 139.39 | 1.049× | 145.09
| 138.34 | 1.049× |
| 64 | 64 | 3 | 1 | 16384 | changed | 12.96 | 9.70 | 1.337× | 12.99 |
9.66 | 1.344× |
| 64 | 64 | 3 | 8 | 16384 | changed | 28.16 | 25.02 | 1.125× | 28.03 |
24.86 | 1.127× |
| 64 | 64 | 3 | 32 | 16384 | unchanged | 77.47 | 77.47 | 1.000× | 77.51
| 77.50 | 1.000× |
| 64 | 64 | 3 | 64 | 16384 | changed | 139.97 | 136.45 | 1.026× | 140.10
| 136.48 | 1.026× |
| 64 | 64 | 3 | 128 | 16384 | changed | 278.59 | 274.40 | 1.015× |
279.04 | 274.53 | 1.016× |
| 64 | 64 | 3 | 256 | 16384 | unchanged | 499.23 | 499.26 | 1.000× |
502.27 | 502.08 | 1.000× |
| 64 | 64 | 3 | 8 | 65536 | unchanged | 82.14 | 82.18 | 1.000× | 81.98 |
81.98 | 1.000× |
| 64 | 64 | 3 | 32 | 65536 | unchanged | 241.66 | 241.63 | 1.000× |
241.50 | 241.50 | 1.000× |
| 64 | 64 | 3 | 128 | 65536 | unchanged | 914.69 | 914.31 | 1.000× |
914.21 | 914.05 | 1.000× |
| 64 | 64 | 4 | 8 | 4096 | unchanged | 15.71 | 15.71 | 1.000× | 15.68 |
15.68 | 1.000× |
| 64 | 64 | 4 | 64 | 4096 | changed | 50.47 | 47.39 | 1.065× | 50.21 |
47.26 | 1.062× |
| 64 | 64 | 4 | 256 | 4096 | unchanged | 156.67 | 156.67 | 1.000× |
156.67 | 156.67 | 1.000× |
| 64 | 64 | 4 | 1 | 16384 | changed | 13.92 | 10.53 | 1.322× | 13.95 |
10.56 | 1.321× |
| 64 | 64 | 4 | 8 | 16384 | changed | 30.75 | 27.39 | 1.123× | 30.59 |
27.39 | 1.117× |
| 64 | 64 | 4 | 32 | 16384 | changed | 83.20 | 80.45 | 1.034× | 83.65 |
80.90 | 1.034× |
| 64 | 64 | 4 | 64 | 16384 | unchanged | 147.89 | 147.91 | 1.000× |
147.26 | 147.27 | 1.000× |
| 64 | 64 | 4 | 128 | 16384 | unchanged, CE (760, 52021) | 289.73 |
289.76 | 1.000×² | 288.77 | 288.70 | 1.000×² |
| 64 | 64 | 4 | 256 | 16384 | unchanged, CE (760, 52021) | 517.15 |
516.96 | 1.000×² | 518.63 | 518.34 | 1.001×² |
| 64 | 64 | 4 | 8 | 65536 | unchanged | 85.70 | 85.69 | 1.000× | 86.21 |
86.24 | 1.000× |
| 64 | 64 | 4 | 32 | 65536 | unchanged, CE (52021) | 278.35 | 278.37 |
1.000× | 278.53 | 278.50 | 1.000×² |
| 64 | 64 | 4 | 128 | 65536 | unchanged, CE (760, 52021) | 942.47 |
942.26 | 1.000×² | 944.07 | 944.26 | 1.000×² |
| 64 | 64 | 5 | 8 | 4096 | unchanged | 16.86 | 16.86 | 1.000× | 17.02 |
17.02 | 1.000× |
| 64 | 64 | 5 | 64 | 4096 | unchanged | 54.30 | 54.27 | 1.001× | 54.46 |
54.46 | 1.000× |
| 64 | 64 | 5 | 256 | 4096 | changed | 168.39 | 161.15 | 1.045× | 167.46
| 160.58 | 1.043× |
| 64 | 64 | 5 | 1 | 16384 | changed | 14.56 | 11.20 | 1.300× | 14.69 |
11.30 | 1.300× |
| 64 | 64 | 5 | 8 | 16384 | changed | 34.11 | 30.66 | 1.113× | 34.11 |
30.46 | 1.120× |
| 64 | 64 | 5 | 32 | 16384 | changed | 87.55 | 84.26 | 1.039× | 87.71 |
84.48 | 1.038× |
| 64 | 64 | 5 | 64 | 16384 | unchanged | 159.01 | 158.94 | 1.000× |
159.91 | 159.97 | 1.000× |
| 64 | 64 | 5 | 128 | 16384 | unchanged, CE (52021) | 414.79 | 414.82 |
1.000× | 415.71 | 415.71 | 1.000×² |
| 64 | 64 | 5 | 256 | 16384 | changed | 919.33 | 914.55 | 1.005× |
919.91 | 913.99 | 1.006× |
| 64 | 64 | 5 | 8 | 65536 | changed | 92.83 | 89.41 | 1.038× | 93.63 |
90.43 | 1.035× |
| 64 | 64 | 5 | 32 | 65536 | unchanged | 509.09 | 508.96 | 1.000× |
510.82 | 510.85 | 1.000× |
| 64 | 64 | 5 | 128 | 65536 | unchanged | 1739.68 | 1738.79 | 1.001× |
1740.17 | 1739.93 | 1.000× |
| 64 | 64 | 6 | 8 | 4096 | unchanged | 17.31 | 17.31 | 1.000× | 17.38 |
17.38 | 1.000× |
| 64 | 64 | 6 | 64 | 4096 | changed | 55.23 | 51.36 | 1.075× | 55.65 |
52.00 | 1.070× |
| 64 | 64 | 6 | 256 | 4096 | changed | 261.34 | 254.72 | 1.026× | 261.28
| 254.48 | 1.027× |
| 64 | 64 | 6 | 1 | 16384 | changed | 14.40 | 11.07 | 1.301× | 14.43 |
11.04 | 1.307× |
| 64 | 64 | 6 | 8 | 16384 | changed | 32.54 | 29.22 | 1.114× | 32.70 |
29.34 | 1.115× |
| 64 | 64 | 6 | 32 | 16384 | changed | 92.06 | 88.93 | 1.035× | 91.17 |
88.00 | 1.036× |
| 64 | 64 | 6 | 64 | 16384 | unchanged | 177.44 | 177.41 | 1.000× |
176.42 | 176.45 | 1.000× |
| 64 | 64 | 6 | 128 | 16384 | unchanged, CE (760, 52021) | 419.04 |
419.04 | 1.000×² | 418.27 | 418.21 | 1.000×² |
| 64 | 64 | 6 | 256 | 16384 | unchanged | 931.31 | 931.60 | 1.000× |
930.15 | 930.24 | 1.000× |
| 64 | 64 | 6 | 8 | 65536 | changed | 96.51 | 93.02 | 1.037× | 95.81 |
92.22 | 1.039× |
| 64 | 64 | 6 | 32 | 65536 | changed | 521.38 | 517.76 | 1.007× | 518.27
| 515.36 | 1.006× |
| 64 | 64 | 6 | 128 | 65536 | unchanged, CE (52021) | 1741.41 | 1741.33
| 1.000× | 1736.44 | 1736.15 | 1.000×² |

The kernel's other variants are the dense FP4 and FP8 lightning-indexer
logits and the paged FP8 MQA logits for SM100a/SM103a
(`deepgemm_dense_mqa`), while this paged FP8 package ships on sm_120a
only.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Experimental paged-MQA device routing now supports CTA-parallel static
routes at explicitly configured batch sizes. Tuned routes remain
available for other listed batches, and null entries retain the default
route.
* Static and parallel routes produce the same schedule metadata;
standalone metadata execution continues to use single-warp scheduling.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Avery Huang <averyh@nvidia.com>

### [e1b2a15](https://github.com/flashinfer-ai/flashinfer/commit/e1b2a15998a4de561072f0e99c1484ba1f3715b3)

- **作者**: eigen
- **时间**: 2026-10-31T09:53:53Z
- **提交信息**: feat(cake_moe_grouped_gemm): opt-in non-deterministic MoE grouped GEMM training package (#8088)

This PR adds `flashinfer.experimental.cake.cake_moe_grouped_gemm`, an
opt-in non-deterministic mode for Cake's ragged BF16 grouped GEMM for
MoE expert training. The kernel covers forward (Y = X W^T), data
gradient (dX = G W) and weight gradient (dW = G^T X), with FP32
accumulation and a BF16 or FP32 weight-gradient output. You select the
new mode with `deterministic=False`, which also works through the facade
`flashinfer.experimental.cake.grouped_mm`; the facade's default stays
deterministic. The new mode differs from the deterministic package
`flashinfer.experimental.cake_moe_grouped_det_gemm` (the existing
default, on main) only in the 512-wide weight gradient. Forward, data
gradient and the 256-wide weight gradient run the deterministic
package's programs. Against that baseline, performance is on par on all
three GPUs, within about 1 %. Geomean speedup (weight gradient / 2 x fwd
+ bwd) is 0.992 / 1.003 on B200, 0.999 / 0.999 on GB300 and 1.000 /
0.999 on Rubin, so this variant is a numerical-mode option rather than a
speedup. Speedup = deterministic latency / non-deterministic latency,
taken as the median of paired groups run in alternating order (CUPTI,
cold L2). Rows cover the gate_up (N=4096, K=6144) and down (N=6144,
K=2048) projections, E = 4, 8, 16, 32 experts, balanced / skewed /
one-empty group sizes, and BF16 and FP32 weight-gradient output. "weight
gradient" rows time one weight-gradient launch; "2 x fwd + bwd" rows
time one checkpointed training step (two forwards and the backward).

### B200

NVIDIA B200 (sm_100a, 148 SMs, 1000 W), CUDA 13.4, driver 580.82.07,
torch 2.14.1+cu130; CUPTI, cold L2; paired groups in alternating order:
8 for the weight gradient, 6 for 2 x fwd + bwd

| pass | projection | E | M | group sizes | out dtype | N | K | det ms |
new ms | speedup det/new [min, max] |
|---|---|---|---|---|---|---|---|---|---|---|
| weight gradient | gate_up | 4 | 112576 | balanced | bf16 | 4096 | 6144
| 4.2173 | 4.2849 | 0.992 [0.945, 1.056] |
| weight gradient | gate_up | 4 | 112576 | balanced | f32 | 4096 | 6144
| 4.1878 | 4.2564 | 0.984 [0.961, 1.024] |
| weight gradient | gate_up | 4 | 112576 | one empty | bf16 | 4096 |
6144 | 4.1808 | 4.1999 | 0.998 [0.982, 1.015] |
| weight gradient | gate_up | 4 | 112576 | skewed | bf16 | 4096 | 6144 |
4.3317 | 4.3868 | 0.998 [0.942, 1.043] |
| weight gradient | gate_up | 4 | 136064 | balanced | bf16 | 4096 | 6144
| 4.8956 | 4.9402 | 0.992 [0.946, 1.014] |
| weight gradient | gate_up | 4 | 136064 | balanced | f32 | 4096 | 6144
| 5.0062 | 5.0773 | 0.989 [0.973, 1.015] |
| weight gradient | gate_up | 4 | 136064 | one empty | bf16 | 4096 |
6144 | 5.0752 | 5.0740 | 1.001 [0.979, 1.003] |
| weight gradient | gate_up | 4 | 136064 | skewed | bf16 | 4096 | 6144 |
4.9852 | 5.0135 | 0.994 [0.941, 0.998] |
| weight gradient | gate_up | 8 | 131072 | balanced | bf16 | 4096 | 6144
| 4.6719 | 4.7064 | 0.996 [0.979, 1.019] |
| weight gradient | gate_up | 16 | 131072 | balanced | bf16 | 4096 |
6144 | 4.6426 | 4.6863 | 1.000 [0.980, 1.019] |
| weight gradient | gate_up | 32 | 131072 | balanced | bf16 | 4096 |
6144 | 4.6923 | 4.7221 | 0.991 [0.968, 1.023] |
| weight gradient | down | 4 | 112576 | balanced | bf16 | 6144 | 2048 |
2.0619 | 2.0892 | 0.989 [0.928, 0.992] |
| weight gradient | down | 4 | 112576 | balanced | f32 | 6144 | 2048 |
2.1008 | 2.1853 | 0.968 [0.949, 1.018] |
| weight gradient | down | 4 | 112576 | one empty | bf16 | 6144 | 2048 |
2.0317 | 2.0377 | 1.000 [0.986, 1.027] |
| weight gradient | down | 4 | 112576 | skewed | bf16 | 6144 | 2048 |
2.0422 | 2.0805 | 0.983 [0.955, 1.005] |
| weight gradient | down | 4 | 136064 | balanced | bf16 | 6144 | 2048 |
2.4695 | 2.5120 | 0.987 [0.977, 1.004] |
| weight gradient | down | 4 | 136064 | balanced | f32 | 6144 | 2048 |
2.5125 | 2.5837 | 0.970 [0.958, 0.984] |
| weight gradient | down | 4 | 136064 | one empty | bf16 | 6144 | 2048 |
2.4670 | 2.4561 | 1.004 [1.002, 1.006] |
| weight gradient | down | 4 | 136064 | skewed | bf16 | 6144 | 2048 |
2.5098 | 2.5469 | 0.987 [0.971, 1.012] |
| weight gradient | down | 8 | 131072 | balanced | bf16 | 6144 | 2048 |
2.4030 | 2.3917 | 0.998 [0.962, 1.026] |
| weight gradient | down | 16 | 131072 | balanced | bf16 | 6144 | 2048 |
2.3852 | 2.3570 | 1.004 [0.991, 1.020] |
| weight gradient | down | 32 | 131072 | balanced | bf16 | 6144 | 2048 |
2.3753 | 2.3488 | 1.001 [0.980, 1.041] |
| 2 x fwd + bwd | gate_up | 4 | 112576 | balanced | bf16 | 4096 | 6144 |
16.2030 | 16.0767 | 1.014 [0.972, 1.041] |
| 2 x fwd + bwd | gate_up | 4 | 112576 | one empty | bf16 | 4096 | 6144
| 16.1836 | 15.8209 | 1.020 [1.011, 1.032] |
| 2 x fwd + bwd | gate_up | 4 | 112576 | skewed | bf16 | 4096 | 6144 |
16.0320 | 15.7829 | 1.012 [0.966, 1.037] |
| 2 x fwd + bwd | gate_up | 4 | 136064 | balanced | bf16 | 4096 | 6144 |
19.2101 | 19.1664 | 1.004 [0.987, 1.007] |
| 2 x fwd + bwd | gate_up | 4 | 136064 | one empty | bf16 | 4096 | 6144
| 19.4735 | 19.3529 | 1.004 [0.984, 1.028] |
| 2 x fwd + bwd | gate_up | 4 | 136064 | skewed | bf16 | 4096 | 6144 |
19.5103 | 19.5570 | 0.998 [0.983, 1.014] |
| 2 x fwd + bwd | gate_up | 8 | 131072 | balanced | bf16 | 4096 | 6144 |
18.5882 | 18.4903 | 1.012 [0.994, 1.024] |
| 2 x fwd + bwd | gate_up | 16 | 131072 | balanced | bf16 | 4096 | 6144
| 18.6253 | 18.6694 | 0.996 [0.982, 1.032] |
| 2 x fwd + bwd | gate_up | 32 | 131072 | balanced | bf16 | 4096 | 6144
| 18.6993 | 18.7372 | 1.000 [0.979, 1.008] |
| 2 x fwd + bwd | down | 4 | 112576 | balanced | bf16 | 6144 | 2048 |
8.0235 | 8.0371 | 0.997 [0.995, 1.017] |
| 2 x fwd + bwd | down | 4 | 112576 | one empty | bf16 | 6144 | 2048 |
7.9343 | 7.9297 | 1.001 [0.972, 1.030] |
| 2 x fwd + bwd | down | 4 | 112576 | skewed | bf16 | 6144 | 2048 |
7.9791 | 7.9362 | 1.007 [0.991, 1.018] |
| 2 x fwd + bwd | down | 4 | 136064 | balanced | bf16 | 6144 | 2048 |
9.5440 | 9.5660 | 0.995 [0.974, 1.024] |
| 2 x fwd + bwd | down | 4 | 136064 | one empty | bf16 | 6144 | 2048 |
9.5453 | 9.5656 | 0.998 [0.976, 1.026] |
| 2 x fwd + bwd | down | 4 | 136064 | skewed | bf16 | 6144 | 2048 |
9.5943 | 9.7946 | 0.993 [0.973, 0.995] |
| 2 x fwd + bwd | down | 8 | 131072 | balanced | bf16 | 6144 | 2048 |
9.2305 | 9.2546 | 0.998 [0.970, 1.020] |
| 2 x fwd + bwd | down | 16 | 131072 | balanced | bf16 | 6144 | 2048 |
9.3132 | 9.3206 | 1.001 [0.975, 1.021] |
| 2 x fwd + bwd | down | 32 | 131072 | balanced | bf16 | 6144 | 2048 |
9.4344 | 9.2509 | 1.010 [0.976, 1.036] |

geomean speedup wgrad over 22 rows: 0.9920

geomean speedup step over 18 rows: 1.0034

### GB300

NVIDIA GB300 (sm_103a, 152 SMs, 1400 W), CUDA 13.4, driver 580.159.03,
torch 2.14.1+cu130; CUPTI, cold L2; paired groups in alternating order:
8 for the weight gradient, 6 for 2 x fwd + bwd

| pass | projection | E | M | group sizes | out dtype | N | K | det ms |
new ms | speedup det/new [min, max] |
|---|---|---|---|---|---|---|---|---|---|---|
| weight gradient | gate_up | 4 | 112576 | balanced | bf16 | 4096 | 6144
| 3.1133 | 3.0982 | 1.001 [0.989, 1.012] |
| weight gradient | gate_up | 4 | 112576 | balanced | f32 | 4096 | 6144
| 3.1695 | 3.1829 | 1.001 [0.988, 1.019] |
| weight gradient | gate_up | 4 | 112576 | one empty | bf16 | 4096 |
6144 | 3.2087 | 3.2112 | 1.001 [0.993, 1.011] |
| weight gradient | gate_up | 4 | 112576 | skewed | bf16 | 4096 | 6144 |
3.2142 | 3.2409 | 0.992 [0.979, 1.008] |
| weight gradient | gate_up | 4 | 136064 | balanced | bf16 | 4096 | 6144
| 3.7897 | 3.8016 | 0.996 [0.992, 1.004] |
| weight gradient | gate_up | 4 | 136064 | balanced | f32 | 4096 | 6144
| 3.8455 | 3.8575 | 0.997 [0.992, 0.998] |
| weight gradient | gate_up | 4 | 136064 | one empty | bf16 | 4096 |
6144 | 3.9367 | 3.9209 | 1.004 [0.991, 1.018] |
| weight gradient | gate_up | 4 | 136064 | skewed | bf16 | 4096 | 6144 |
3.9023 | 3.9207 | 0.995 [0.989, 0.998] |
| weight gradient | gate_up | 8 | 131072 | balanced | bf16 | 4096 | 6144
| 3.6425 | 3.6499 | 0.999 [0.992, 1.014] |
| weight gradient | gate_up | 16 | 131072 | balanced | bf16 | 4096 |
6144 | 3.6485 | 3.6716 | 0.993 [0.992, 1.001] |
| weight gradient | gate_up | 32 | 131072 | balanced | bf16 | 4096 |
6144 | 3.6686 | 3.6521 | 1.003 [0.992, 1.020] |
| weight gradient | down | 4 | 112576 | balanced | bf16 | 6144 | 2048 |
1.5794 | 1.5704 | 1.006 [0.985, 1.017] |
| weight gradient | down | 4 | 112576 | balanced | f32 | 6144 | 2048 |
1.5871 | 1.5996 | 0.993 [0.959, 1.007] |
| weight gradient | down | 4 | 112576 | one empty | bf16 | 6144 | 2048 |
1.5762 | 1.5857 | 0.995 [0.961, 1.025] |
| weight gradient | down | 4 | 112576 | skewed | bf16 | 6144 | 2048 |
1.5822 | 1.5992 | 0.989 [0.977, 1.015] |
| weight gradient | down | 4 | 136064 | balanced | bf16 | 6144 | 2048 |
1.9089 | 1.9199 | 0.995 [0.992, 1.008] |
| weight gradient | down | 4 | 136064 | balanced | f32 | 6144 | 2048 |
1.9315 | 1.9198 | 1.006 [0.985, 1.017] |
| weight gradient | down | 4 | 136064 | one empty | bf16 | 6144 | 2048 |
1.9123 | 1.9036 | 1.004 [0.998, 1.017] |
| weight gradient | down | 4 | 136064 | skewed | bf16 | 6144 | 2048 |
1.9347 | 1.9299 | 1.001 [0.986, 1.013] |
| weight gradient | down | 8 | 131072 | balanced | bf16 | 6144 | 2048 |
1.8304 | 1.8274 | 1.001 [0.987, 1.003] |
| weight gradient | down | 16 | 131072 | balanced | bf16 | 6144 | 2048 |
1.8330 | 1.8263 | 1.004 [0.999, 1.011] |
| weight gradient | down | 32 | 131072 | balanced | bf16 | 6144 | 2048 |
1.8277 | 1.8402 | 0.995 [0.990, 0.998] |
| 2 x fwd + bwd | gate_up | 4 | 112576 | balanced | bf16 | 4096 | 6144 |
12.6067 | 12.6243 | 0.998 [0.986, 1.015] |
| 2 x fwd + bwd | gate_up | 4 | 112576 | one empty | bf16 | 4096 | 6144
| 12.7315 | 12.7519 | 1.000 [0.993, 1.008] |
| 2 x fwd + bwd | gate_up | 4 | 112576 | skewed | bf16 | 4096 | 6144 |
12.6978 | 12.7372 | 0.995 [0.990, 1.003] |
| 2 x fwd + bwd | gate_up | 4 | 136064 | balanced | bf16 | 4096 | 6144 |
15.3064 | 15.2113 | 1.001 [0.997, 1.015] |
| 2 x fwd + bwd | gate_up | 4 | 136064 | one empty | bf16 | 4096 | 6144
| 15.4502 | 15.4882 | 0.998 [0.989, 1.004] |
| 2 x fwd + bwd | gate_up | 4 | 136064 | skewed | bf16 | 4096 | 6144 |
15.5577 | 15.4623 | 1.005 [0.997, 1.009] |
| 2 x fwd + bwd | gate_up | 8 | 131072 | balanced | bf16 | 4096 | 6144 |
14.8567 | 14.7036 | 1.010 [0.979, 1.015] |
| 2 x fwd + bwd | gate_up | 16 | 131072 | balanced | bf16 | 4096 | 6144
| 14.8275 | 14.9911 | 0.994 [0.980, 1.001] |
| 2 x fwd + bwd | gate_up | 32 | 131072 | balanced | bf16 | 4096 | 6144
| 15.0289 | 15.0778 | 0.996 [0.989, 1.003] |
| 2 x fwd + bwd | down | 4 | 112576 | balanced | bf16 | 6144 | 2048 |
6.3499 | 6.3628 | 0.999 [0.987, 1.003] |
| 2 x fwd + bwd | down | 4 | 112576 | one empty | bf16 | 6144 | 2048 |
6.3212 | 6.3869 | 0.991 [0.980, 0.994] |
| 2 x fwd + bwd | down | 4 | 112576 | skewed | bf16 | 6144 | 2048 |
6.3655 | 6.3968 | 0.997 [0.991, 1.002] |
| 2 x fwd + bwd | down | 4 | 136064 | balanced | bf16 | 6144 | 2048 |
7.6420 | 7.6487 | 0.998 [0.995, 1.007] |
| 2 x fwd + bwd | down | 4 | 136064 | one empty | bf16 | 6144 | 2048 |
7.6946 | 7.7246 | 0.996 [0.991, 1.000] |
| 2 x fwd + bwd | down | 4 | 136064 | skewed | bf16 | 6144 | 2048 |
7.7318 | 7.7652 | 0.997 [0.991, 1.000] |
| 2 x fwd + bwd | down | 8 | 131072 | balanced | bf16 | 6144 | 2048 |
7.4182 | 7.4036 | 1.004 [0.995, 1.013] |
| 2 x fwd + bwd | down | 16 | 131072 | balanced | bf16 | 6144 | 2048 |
7.4352 | 7.4276 | 1.001 [0.991, 1.014] |
| 2 x fwd + bwd | down | 32 | 131072 | balanced | bf16 | 6144 | 2048 |
7.5243 | 7.5267 | 0.997 [0.989, 1.009] |

geomean speedup wgrad over 22 rows: 0.9987

geomean speedup step over 18 rows: 0.9988

### Rubin

NVIDIA Rubin (sm_107a, 208 SMs, 2300 W), CUDA 13.4, driver 615.71.10,
torch 2.14.1+cu130; CUPTI, cold L2; paired groups in alternating order:
8 for the weight gradient, 6 for 2 x fwd + bwd

| pass | projection | E | M | group sizes | out dtype | N | K | det ms |
new ms | speedup det/new [min, max] |
|---|---|---|---|---|---|---|---|---|---|---|
| weight gradient | gate_up | 4 | 112576 | balanced | bf16 | 4096 | 6144
| 1.8146 | 1.8249 | 1.004 [0.968, 1.035] |
| weight gradient | gate_up | 4 | 112576 | balanced | f32 | 4096 | 6144
| 1.8730 | 1.8699 | 1.000 [0.974, 1.036] |
| weight gradient | gate_up | 4 | 112576 | one empty | bf16 | 4096 |
6144 | 1.8729 | 1.8691 | 1.000 [0.970, 1.038] |
| weight gradient | gate_up | 4 | 112576 | skewed | bf16 | 4096 | 6144 |
1.8793 | 1.8621 | 1.005 [1.003, 1.042] |
| weight gradient | gate_up | 4 | 136064 | balanced | bf16 | 4096 | 6144
| 2.2291 | 2.2313 | 1.000 [0.978, 1.006] |
| weight gradient | gate_up | 4 | 136064 | balanced | f32 | 4096 | 6144
| 2.2641 | 2.2631 | 1.000 [0.984, 1.007] |
| weight gradient | gate_up | 4 | 136064 | one empty | bf16 | 4096 |
6144 | 2.2884 | 2.2775 | 1.003 [0.995, 1.033] |
| weight gradient | gate_up | 4 | 136064 | skewed | bf16 | 4096 | 6144 |
2.2951 | 2.3012 | 1.000 [0.993, 1.005] |
| weight gradient | gate_up | 8 | 131072 | balanced | bf16 | 4096 | 6144
| 2.1292 | 2.1286 | 1.000 [0.997, 1.001] |
| weight gradient | gate_up | 16 | 131072 | balanced | bf16 | 4096 |
6144 | 2.1261 | 2.1263 | 1.000 [0.999, 1.000] |
| weight gradient | gate_up | 32 | 131072 | balanced | bf16 | 4096 |
6144 | 2.1676 | 2.1633 | 1.002 [0.979, 1.023] |
| weight gradient | down | 4 | 112576 | balanced | bf16 | 6144 | 2048 |
0.9337 | 0.9302 | 1.000 [0.972, 1.022] |
| weight gradient | down | 4 | 112576 | balanced | f32 | 6144 | 2048 |
0.9461 | 0.9520 | 0.995 [0.978, 1.025] |
| weight gradient | down | 4 | 112576 | one empty | bf16 | 6144 | 2048 |
0.9552 | 0.9500 | 1.006 [1.003, 1.010] |
| weight gradient | down | 4 | 112576 | skewed | bf16 | 6144 | 2048 |
0.9381 | 0.9546 | 0.982 [0.971, 1.008] |
| weight gradient | down | 4 | 136064 | balanced | bf16 | 6144 | 2048 |
1.1332 | 1.1334 | 0.998 [0.965, 1.040] |
| weight gradient | down | 4 | 136064 | balanced | f32 | 6144 | 2048 |
1.1448 | 1.1459 | 0.999 [0.973, 1.038] |
| weight gradient | down | 4 | 136064 | one empty | bf16 | 6144 | 2048 |
1.1475 | 1.1564 | 0.994 [0.980, 1.004] |
| weight gradient | down | 4 | 136064 | skewed | bf16 | 6144 | 2048 |
1.1449 | 1.1502 | 0.996 [0.985, 1.026] |
| weight gradient | down | 8 | 131072 | balanced | bf16 | 6144 | 2048 |
1.0752 | 1.0730 | 1.002 [0.970, 1.040] |
| weight gradient | down | 16 | 131072 | balanced | bf16 | 6144 | 2048 |
1.0838 | 1.0748 | 1.008 [0.969, 1.010] |
| weight gradient | down | 32 | 131072 | balanced | bf16 | 6144 | 2048 |
1.0862 | 1.0856 | 1.001 [0.996, 1.029] |
| 2 x fwd + bwd | gate_up | 4 | 112576 | balanced | bf16 | 4096 | 6144 |
7.2905 | 7.2837 | 1.001 [0.949, 1.036] |
| 2 x fwd + bwd | gate_up | 4 | 112576 | one empty | bf16 | 4096 | 6144
| 7.4082 | 7.5002 | 0.993 [0.965, 1.030] |
| 2 x fwd + bwd | gate_up | 4 | 112576 | skewed | bf16 | 4096 | 6144 |
7.4936 | 7.3931 | 1.001 [0.986, 1.055] |
| 2 x fwd + bwd | gate_up | 4 | 136064 | balanced | bf16 | 4096 | 6144 |
9.0138 | 9.0930 | 0.991 [0.956, 1.018] |
| 2 x fwd + bwd | gate_up | 4 | 136064 | one empty | bf16 | 4096 | 6144
| 9.0826 | 9.0750 | 0.999 [0.980, 1.014] |
| 2 x fwd + bwd | gate_up | 4 | 136064 | skewed | bf16 | 4096 | 6144 |
9.1741 | 9.2345 | 0.992 [0.980, 1.010] |
| 2 x fwd + bwd | gate_up | 8 | 131072 | balanced | bf16 | 4096 | 6144 |
8.8675 | 8.7858 | 1.007 [0.982, 1.024] |
| 2 x fwd + bwd | gate_up | 16 | 131072 | balanced | bf16 | 4096 | 6144
| 8.6047 | 8.5956 | 1.002 [0.975, 1.020] |
| 2 x fwd + bwd | gate_up | 32 | 131072 | balanced | bf16 | 4096 | 6144
| 8.8055 | 8.8745 | 0.994 [0.972, 1.028] |
| 2 x fwd + bwd | down | 4 | 112576 | balanced | bf16 | 6144 | 2048 |
3.6523 | 3.6502 | 1.000 [0.974, 1.007] |
| 2 x fwd + bwd | down | 4 | 112576 | one empty | bf16 | 6144 | 2048 |
3.6848 | 3.6756 | 0.999 [0.973, 1.037] |
| 2 x fwd + bwd | down | 4 | 112576 | skewed | bf16 | 6144 | 2048 |
3.6847 | 3.6724 | 1.004 [0.997, 1.040] |
| 2 x fwd + bwd | down | 4 | 136064 | balanced | bf16 | 6144 | 2048 |
4.4951 | 4.5862 | 0.992 [0.973, 1.010] |
| 2 x fwd + bwd | down | 4 | 136064 | one empty | bf16 | 6144 | 2048 |
4.5439 | 4.4963 | 1.006 [0.990, 1.014] |
| 2 x fwd + bwd | down | 4 | 136064 | skewed | bf16 | 6144 | 2048 |
4.5413 | 4.5313 | 0.997 [0.993, 1.018] |
| 2 x fwd + bwd | down | 8 | 131072 | balanced | bf16 | 6144 | 2048 |
4.3903 | 4.3116 | 1.012 [0.984, 1.037] |
| 2 x fwd + bwd | down | 16 | 131072 | balanced | bf16 | 6144 | 2048 |
4.3855 | 4.3920 | 1.000 [0.984, 1.025] |
| 2 x fwd + bwd | down | 32 | 131072 | balanced | bf16 | 6144 | 2048 |
4.4149 | 4.4236 | 0.998 [0.965, 1.023] |

geomean speedup wgrad over 22 rows: 0.9997

geomean speedup step over 18 rows: 0.9994

The deterministic package provides the same forward / data-gradient /
weight-gradient entries, BF16 and FP32 weight-gradient outputs, and
256-wide and 512-wide k-tile weight-gradient forms, and both packages
cover sm_100a, sm_103a and sm_107a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added experimental BF16 MoE grouped GEMM operations for forward
passes, input gradients, and weight gradients, with selectable
deterministic behavior on supported NVIDIA GPUs.
* Added automatic differentiation support, performance benchmarks, and
options for FP32 weight-gradient outputs.
* **Documentation**
* Added API and usage guidance, including supported hardware, numerical
behavior, and known limitations.
* **Tests**
* Added coverage for numerical accuracy, reproducibility, CUDA graph
replay, and standalone package imports.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [5ab9a74](https://github.com/flashinfer-ai/flashinfer/commit/5ab9a74e44b1da22a5f102641a7ffd4dc339c3b3)

- **作者**: Akaash Parthasarathy
- **时间**: 2026-10-31T09:41:03Z
- **提交信息**: feat(moe_ep): select Rubin MegaMoE variants with autotune v2 (#7911)

<!-- .github/pull_request_template.md -->

## 📌 Description

Add `kernel_variant="auto"` for Rubin NVFP4, MXFP8 E4M3/E5M2 and
MXFP4/MXFP8 MegaMoE. With `knobs="auto"` and an enabled `autotune_v2()`
warmup, it selects knobs within each eligible variant, then compares the
winners. Every candidate is measured with input staging, compute and
output handling. Explicit inference and GenPhase tuning use the same
boundary. The Rubin offline CLI measures complete forwards with
generated BF16 inputs and an owned output. Compilation, weight
preparation and workspace allocation stay outside measurement.

Store each variant's winning knobs in its fixed-variant v2 records and
the overall variant/knob choice in a separate v2 entry. On an overall
miss, reuse compatible per-variant records, including capacity fallback,
and search missing variants. Cached knobs are checked and measured at
the current workload before comparing variants; their original records
keep their workload and score. Overall lookup requires a matching
workload and execution contract. Searches and cache hits preserve the
MegaMoE compatibility-file handoff when persistence is enabled.
Kernel-only records do not satisfy complete-forward tuning; the
low-level already-staged tuner remains available.

The selector reuses collective preparation, correctness checks and
timing policies. A variant with no passing candidate is skipped;
allocation, compilation and launch failures still abort. Replay misses
use inference defaults and leave selection pending. Prepared eager
forwards outside autotune contexts reuse the agreed workspace without
selection collectives or cache lookups. Calling the layer in an explicit
tuning or replay context retains collective checks and requires
reconciliation on the next bare forward. Unrelated contexts, including
tuning on another thread, leave prepared execution unchanged.
Process-wide store changes and reloads must be coordinated across EP
ranks; when changing stores, call the layer in the new context on every
rank.

Add `get_tuned_config()` to return the concrete variant and knobs for a
fixed layer. Automatic handles own independent storage. Later selection
can replace a captured default workspace while retaining its old storage
for existing graphs; a captured explicit handle requires another handle.

## 🔍 Related Issues

Follow-up to #6535. Blackwell variant selection is outside this change.

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
- [x] All targeted tests are passing.
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets: `tests/moe_ep/test_sm107_variant_selection.py
tests/moe_ep/test_sm107_variant_selection_multirank.py
tests/moe_ep/test_sm107_auto_multirank.py
tests/moe_ep/test_sm107_tuning_protocol.py
tests/moe_ep/test_sm107_tuning.py
tests/moe_ep/test_mega_workspace_knobs.py tests/cpu/moe_ep/
tests/cpu/autotuner/ tests/autotuner/test_autotune_cache_v2.py
tests/autotuner/test_autotune_cache_scope.py
tests/autotuner/test_autotuner_core.py`

On a4e71bb7b, 862 host tests passed, with four CUDA-only skips. All 117
affected protocol and selection regressions passed, including four
regressions that fail against the previous implementation. All-files
pre-commit and commit hooks passed.

GPU validation on a4e71bb7b passed five fixed-variant and three
automatic-variant cases per rank on both EP2 and EP4, with no skips.
Only rank zero enters unrelated contexts, including tuning held open on
another thread, while all ranks continue prepared eager forwards. The
tests check outputs with selection collectives, protocol calls and
cache-identity lookup forbidden. Coverage also includes later tuning,
coordinated reloads, explicit workspaces, existing captured graphs,
prequantized inputs and CUPTI. The shared cache-v2, cache-scope and
autotuner-core suites passed all 268 tests on GPU.

Earlier validation on 0ef89c259 passed the full EP2 matrix: 15
variant-selection and 21 fixed-variant cases per rank, including output
copies, cold L2 and cache reuse across capacities. The following CLI
checks also ran on that revision; the latest correction only changes
online prepared-state invalidation.

The offline CLI passed four full NVFP4 searches: inference and GenPhase
at two capacities. Fresh processes replayed both capacities for each
variant with the MegaMoE file disabled and searching forbidden. All four
MegaMoE file records matched their managed records.

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

The sweep receives a private trial wrapper that stages inputs and
executes fixed knobs. The same wrapper is used by explicit-variant
tuning and the offline CLI; candidate enumeration and collective
measurement remain shared. GenPhase eligibility follows the existing
configuration and candidate checks. Selection happens during warmup.
Prepared execution uses the generation captured at invocation entry, so
a process-store attachment or reload during preparation is rechecked on
the next forward.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added automatic selection between eligible inference and GenPhase
kernel variants based on complete-forward performance measurements.
* Added a way to retrieve the selected fixed kernel configuration for a
layer or workspace.
* Improved reuse of compatible tuning results, with fallback behavior
when cached results cannot be used.
* **Documentation**
* Expanded tuning guidance to cover variant selection, measurement
boundaries, cache reuse, and serving-time behavior.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [4e17968](https://github.com/flashinfer-ai/flashinfer/commit/4e17968b8555fd3a29cb55de5572027af47bc668)

- **作者**: eigen
- **时间**: 2026-10-31T09:06:40Z
- **提交信息**: feat(cake_rmsnorm_silu_gate): opt-in non-deterministic auto grad backend (#8097)

The Cake SiLU-gated RMSNorm training op computes `y = RMSNorm(x, w) *
SiLU(z)` on BF16 rows of head dim 128, with one weight `w[128]` shared
by all tokens and heads. It has five variants: one forward kernel, plus
a deterministic and a non-deterministic backward that each write the
weight gradient in BF16 or FP32. This PR adds the non-deterministic
backward, selected with `deterministic=False` on
`cake_rmsnorm_silu_gate`, `cake_rmsnorm_silu_gate_train_forward` and
`cake_rmsnorm_silu_gate_train_backward`. The deterministic backward
stays the default. We compare against two baselines: the previous Cake
version, which is the deterministic backward
`flashinfer.cake_rmsnorm_silu_gate_det_train`, and the fastest of four
non-Cake implementations of the same math in each row. At T <= 1031 the
non-deterministic bwd is 1.25-7.01x faster than the deterministic one
and 1.44-13.70x faster than the best non-Cake one. At T 30000-33000 it
is 0.97-1.02x of both baselines on B200 and GB300, but it regresses on
R200 (0.91-0.93x vs deterministic, 0.94-0.95x vs non-Cake). Both modes
use the same forward kernel, so the fwd rows compare the same program
(1.00-1.01x). The Cake forward is 0.68-0.98x of the best non-Cake
forward: at most 1 µs slower at T <= 129 and 0.93-0.98x at T >= 4097.

The deterministic baseline is
`flashinfer.cake_rmsnorm_silu_gate_det_train`: the backward kernel plus
its fixed-order weight-gradient reduction kernel, measured in the same
process. The non-Cake baseline is the fastest of four implementations of
the same math on the same inputs, chosen per row and operation. The
first is `fla` 0.6.0 `fla.modules.fused_norm_gate.rms_norm_gated`, the
Triton kernel of its `FusedRMSNormGated` module with a swish gate. The
second is mamba_ssm v2.3.2
`mamba_ssm.ops.triton.layernorm_gated.rmsnorm_fn(..., z=z,
norm_before_gate=True)` (Triton). The last two are `torch.compile` of
the FP32 formula, once in inductor default mode and once in
`max-autotune-no-cudagraphs` mode (PyTorch 2.14.1, Triton 3.8.0). These
are the fused gated-RMSNorm training kernels from `fla` and Mamba-2,
plus compiler fusion of the same formula, so they are the strongest
applicable comparison. All four meet the same accuracy budget as Cake on
these inputs, and the tables name the winner in each row. The workload
is x, z and dy of shape [T, 48, 128] in BF16, with BF16 w, eps 1e-6 and
a BF16 weight gradient, for T = 1, 7, 129, 1031, 4097, 30000, 30193,
32388, 32737, 33000. `fwd` is one forward call. Cake writes to a
preallocated output, and the others run the autograd-recording forward.
`bwd` is one complete backward, including the weight-gradient reduction
and the final cast. Cake uses preallocated gradients and workspace, and
the others run the autograd backward of one recorded forward. `ckpt
2×fwd+bwd` is the activation-checkpointed step:
`torch.utils.checkpoint(use_reentrant=False)` of the forward, then the
backward, timed end to end through autograd. We time with CUPTI and a
cold L2, using FlashInfer's timer in `flashinfer.testing`. Each sample
is the GPU span from the beginning of the operation's first kernel to
the end of its last kernel. Launch gaps between kernels therefore count,
and the ckpt step includes the host time of the autograd path. Each
value is the median of the per-round medians. B200 uses 4 rounds, with
the process pinned to one logical CPU per physical core on the GPU's
NUMA node. Unpinned runs on that host switched between two host states
about 250 µs apart. GB300 and R200 use 2 rounds. All runs are eager,
without CUDA graphs. vs det = det latency / non-det latency, and vs
non-Cake = best non-Cake latency / non-det latency. A value above 1
means the non-deterministic backward path is faster.

**NVIDIA B200 (sm_100a, 148 SMs), driver 580.82.07, CUDA 13.4 toolkit,
PyTorch 2.14.1+cu130**

| T | op | det Cake (µs) | best non-Cake (µs) | non-det Cake (µs) | vs
det | vs non-Cake |
|---:|---|---:|---:|---:|---:|---:|
| 1 | fwd | 3.0 | 2.0 (torch.compile) | 3.0 | 1.00x | 0.68x |
| 1 | bwd | 19.5 | 42.2 (torch.compile max-autotune) | 4.9 | 4.00x |
8.66x |
| 1 | ckpt 2×fwd+bwd | 766.6 | 791.3 (torch.compile max-autotune) |
745.9 | 1.03x | 1.06x |
| 7 | fwd | 2.9 | 2.2 (torch.compile) | 2.9 | 1.00x | 0.76x |
| 7 | bwd | 20.6 | 61.4 (torch.compile) | 4.5 | 4.60x | 13.70x |
| 7 | ckpt 2×fwd+bwd | 772.0 | 814.5 (torch.compile max-autotune) |
745.6 | 1.04x | 1.09x |
| 129 | fwd | 3.8 | 3.1 (torch.compile max-autotune) | 3.8 | 1.00x |
0.82x |
| 129 | bwd | 23.2 | 68.6 (torch.compile) | 6.5 | 3.59x | 10.62x |
| 129 | ckpt 2×fwd+bwd | 778.6 | 826.8 (torch.compile max-autotune) |
761.0 | 1.02x | 1.09x |
| 1031 | fwd | 10.7 | 9.6 (torch.compile) | 10.7 | 1.00x | 0.90x |
| 1031 | bwd | 26.8 | 105.1 (mamba_ssm) | 18.9 | 1.42x | 5.57x |
| 1031 | ckpt 2×fwd+bwd | 784.9 | 863.2 (mamba_ssm) | 772.0 | 1.02x |
1.12x |
| 4097 | fwd | 32.0 | 30.0 (torch.compile) | 32.0 | 1.00x | 0.94x |
| 4097 | bwd | 59.6 | 112.8 (FLA) | 56.3 | 1.06x | 2.00x |
| 4097 | ckpt 2×fwd+bwd | 819.9 | 909.1 (torch.compile max-autotune) |
830.3 | 0.99x | 1.09x |
| 30000 | fwd | 201.5 | 187.2 (torch.compile) | 201.4 | 1.00x | 0.93x |
| 30000 | bwd | 347.5 | 348.4 (FLA) | 347.7 | 1.00x | 1.00x |
| 30000 | ckpt 2×fwd+bwd | 1057.9 | 1135.9 (torch.compile max-autotune)
| 1075.9 | 0.98x | 1.06x |
| 30193 | fwd | 203.0 | 197.9 (torch.compile max-autotune) | 203.3 |
1.00x | 0.97x |
| 30193 | bwd | 348.9 | 351.1 (FLA) | 349.9 | 1.00x | 1.00x |
| 30193 | ckpt 2×fwd+bwd | 1052.7 | 1125.8 (torch.compile max-autotune)
| 1071.3 | 0.98x | 1.05x |
| 32388 | fwd | 216.8 | 202.8 (torch.compile max-autotune) | 216.7 |
1.00x | 0.94x |
| 32388 | bwd | 372.8 | 378.7 (FLA) | 371.8 | 1.00x | 1.02x |
| 32388 | ckpt 2×fwd+bwd | 1084.4 | 1144.8 (torch.compile max-autotune)
| 1087.6 | 1.00x | 1.05x |
| 32737 | fwd | 221.9 | 216.1 (FLA) | 221.5 | 1.00x | 0.98x |
| 32737 | bwd | 377.5 | 378.9 (FLA) | 378.0 | 1.00x | 1.00x |
| 32737 | ckpt 2×fwd+bwd | 1097.5 | 1141.5 (torch.compile max-autotune)
| 1101.5 | 1.00x | 1.04x |
| 33000 | fwd | 221.7 | 207.3 (torch.compile max-autotune) | 221.7 |
1.00x | 0.93x |
| 33000 | bwd | 379.2 | 382.2 (FLA) | 378.2 | 1.00x | 1.01x |
| 33000 | ckpt 2×fwd+bwd | 1102.4 | 1150.6 (torch.compile max-autotune)
| 1110.5 | 0.99x | 1.04x |

**NVIDIA GB300 (sm_103a, 152 SMs), driver 580.159.03, CUDA 13.4 toolkit,
PyTorch 2.14.1+cu130**

| T | op | det Cake (µs) | best non-Cake (µs) | non-det Cake (µs) | vs
det | vs non-Cake |
|---:|---|---:|---:|---:|---:|---:|
| 1 | fwd | 2.6 | 2.0 (torch.compile) | 2.6 | 1.00x | 0.77x |
| 1 | bwd | 36.1 | 18.1 (torch.compile max-autotune) | 5.2 | 6.91x |
3.46x |
| 1 | ckpt 2×fwd+bwd | 590.7 | 573.1 (torch.compile max-autotune) |
562.6 | 1.05x | 1.02x |
| 7 | fwd | 2.8 | 2.4 (torch.compile) | 2.8 | 1.00x | 0.86x |
| 7 | bwd | 37.2 | 28.7 (torch.compile) | 5.3 | 7.01x | 5.41x |
| 7 | ckpt 2×fwd+bwd | 619.1 | 611.6 (torch.compile max-autotune) |
592.0 | 1.05x | 1.03x |
| 129 | fwd | 3.7 | 3.5 (FLA) | 3.7 | 1.00x | 0.96x |
| 129 | bwd | 37.9 | 31.7 (torch.compile max-autotune) | 8.4 | 4.50x |
3.76x |
| 129 | ckpt 2×fwd+bwd | 601.3 | 621.0 (torch.compile max-autotune) |
578.4 | 1.04x | 1.07x |
| 1031 | fwd | 10.3 | 9.6 (FLA) | 10.2 | 1.01x | 0.94x |
| 1031 | bwd | 42.3 | 71.8 (FLA) | 19.4 | 2.18x | 3.71x |
| 1031 | ckpt 2×fwd+bwd | 665.2 | 695.6 (mamba_ssm) | 643.8 | 1.03x |
1.08x |
| 4097 | fwd | 30.7 | 28.8 (torch.compile max-autotune) | 30.7 | 1.00x |
0.94x |
| 4097 | bwd | 57.6 | 70.2 (FLA) | 55.5 | 1.04x | 1.26x |
| 4097 | ckpt 2×fwd+bwd | 647.0 | 707.6 (torch.compile max-autotune) |
649.4 | 1.00x | 1.09x |
| 30000 | fwd | 192.6 | 178.7 (torch.compile max-autotune) | 192.4 |
1.00x | 0.93x |
| 30000 | bwd | 328.5 | 323.9 (FLA) | 329.8 | 1.00x | 0.98x |
| 30000 | ckpt 2×fwd+bwd | 868.6 | 908.3 (torch.compile max-autotune) |
874.8 | 0.99x | 1.04x |
| 30193 | fwd | 191.2 | 177.5 (torch.compile max-autotune) | 191.0 |
1.00x | 0.93x |
| 30193 | bwd | 329.4 | 322.2 (torch.compile max-autotune) | 328.8 |
1.00x | 0.98x |
| 30193 | ckpt 2×fwd+bwd | 875.0 | 891.4 (torch.compile max-autotune) |
879.4 | 1.00x | 1.01x |
| 32388 | fwd | 206.3 | 192.4 (torch.compile max-autotune) | 206.2 |
1.00x | 0.93x |
| 32388 | bwd | 353.5 | 340.2 (torch.compile max-autotune) | 351.6 |
1.01x | 0.97x |
| 32388 | ckpt 2×fwd+bwd | 902.7 | 898.7 (torch.compile max-autotune) |
915.0 | 0.99x | 0.98x |
| 32737 | fwd | 207.7 | 193.9 (torch.compile max-autotune) | 207.6 |
1.00x | 0.93x |
| 32737 | bwd | 353.7 | 350.9 (FLA) | 356.8 | 0.99x | 0.98x |
| 32737 | ckpt 2×fwd+bwd | 899.6 | 936.6 (torch.compile) | 902.1 | 1.00x
| 1.04x |
| 33000 | fwd | 210.8 | 203.5 (FLA) | 210.5 | 1.00x | 0.97x |
| 33000 | bwd | 359.9 | 354.7 (FLA) | 361.2 | 1.00x | 0.98x |
| 33000 | ckpt 2×fwd+bwd | 966.4 | 972.0 (torch.compile) | 956.8 | 1.01x
| 1.02x |

**NVIDIA R200 (sm_107a, 216 SMs), driver 615.71.10, CUDA 13.4 toolkit,
PyTorch 2.14.1+cu130**

| T | op | det Cake (µs) | best non-Cake (µs) | non-det Cake (µs) | vs
det | vs non-Cake |
|---:|---|---:|---:|---:|---:|---:|
| 1 | fwd | 2.6 | 2.0 (torch.compile) | 2.6 | 1.00x | 0.80x |
| 1 | bwd | 11.3 | 7.6 (torch.compile max-autotune) | 5.3 | 2.14x |
1.44x |
| 1 | ckpt 2×fwd+bwd | 214.9 | 236.7 (torch.compile max-autotune) |
208.1 | 1.03x | 1.14x |
| 7 | fwd | 2.7 | 2.0 (torch.compile max-autotune) | 2.7 | 1.00x | 0.77x
|
| 7 | bwd | 11.6 | 13.3 (torch.compile max-autotune) | 5.3 | 2.18x |
2.50x |
| 7 | ckpt 2×fwd+bwd | 250.8 | 248.2 (torch.compile) | 245.8 | 1.02x |
1.01x |
| 129 | fwd | 3.2 | 2.5 (torch.compile max-autotune) | 3.2 | 1.00x |
0.79x |
| 129 | bwd | 13.4 | 18.7 (torch.compile max-autotune) | 7.1 | 1.88x |
2.63x |
| 129 | ckpt 2×fwd+bwd | 287.1 | 346.4 (mamba_ssm) | 280.3 | 1.02x |
1.24x |
| 1031 | fwd | 7.4 | 6.8 (torch.compile) | 7.4 | 1.00x | 0.91x |
| 1031 | bwd | 20.0 | 24.5 (FLA) | 16.0 | 1.25x | 1.53x |
| 1031 | ckpt 2×fwd+bwd | 294.1 | 367.8 (mamba_ssm) | 292.3 | 1.01x |
1.26x |
| 4097 | fwd | 20.5 | 19.6 (torch.compile) | 20.5 | 1.00x | 0.95x |
| 4097 | bwd | 41.5 | 44.3 (FLA) | 42.5 | 0.98x | 1.04x |
| 4097 | ckpt 2×fwd+bwd | 275.6 | 386.6 (FLA) | 280.6 | 0.98x | 1.38x |
| 30000 | fwd | 123.9 | 117.1 (FLA) | 123.9 | 1.00x | 0.94x |
| 30000 | bwd | 218.7 | 225.9 (FLA) | 240.3 | 0.91x | 0.94x |
| 30000 | ckpt 2×fwd+bwd | 464.5 | 495.5 (FLA) | 486.5 | 0.95x | 1.02x |
| 30193 | fwd | 124.2 | 117.8 (FLA) | 124.0 | 1.00x | 0.95x |
| 30193 | bwd | 221.3 | 227.1 (torch.compile) | 241.3 | 0.92x | 0.94x |
| 30193 | ckpt 2×fwd+bwd | 468.3 | 492.4 (FLA) | 488.7 | 0.96x | 1.01x |
| 32388 | fwd | 134.1 | 126.5 (FLA) | 134.4 | 1.00x | 0.94x |
| 32388 | bwd | 235.0 | 242.0 (torch.compile) | 254.2 | 0.92x | 0.95x |
| 32388 | ckpt 2×fwd+bwd | 516.0 | 552.7 (FLA) | 537.6 | 0.96x | 1.03x |
| 32737 | fwd | 136.2 | 127.8 (FLA) | 136.3 | 1.00x | 0.94x |
| 32737 | bwd | 237.2 | 243.1 (torch.compile) | 257.4 | 0.92x | 0.94x |
| 32737 | ckpt 2×fwd+bwd | 507.9 | 524.5 (FLA) | 528.6 | 0.96x | 0.99x |
| 33000 | fwd | 135.6 | 128.3 (FLA) | 135.6 | 1.00x | 0.95x |
| 33000 | bwd | 240.9 | 243.2 (torch.compile) | 258.9 | 0.93x | 0.94x |
| 33000 | ckpt 2×fwd+bwd | 542.6 | 595.8 (FLA) | 563.0 | 0.96x | 1.06x |

Both modes cover sm_100a, sm_103a and sm_107a, and the other Cake
variants of this op (the default deterministic backward and the FP32
weight-gradient outputs of both backward forms) cover the same three
targets.

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [2a946a6](https://github.com/flashinfer-ai/flashinfer/commit/2a946a6885dca747fc4e8984bc4d1cc899ddae87)

- **作者**: eigen
- **时间**: 2026-10-31T09:00:29Z
- **提交信息**: perf(cake_kimi_k3_latent_moe): faster Kimi-K3 LatentMoE TP1 decode tail on GB300 (#8098)

This PR updates the Cake programs for the Kimi-K3 Stable LatentMoE front
and tail projections of one rank in
`flashinfer.experimental.kimi_k3_latent_moe` (BF16, `sm_100a` and
`sm_103a`). The package has four variants: the front and the tail
projection, each for TP1 and TP8. Decode-sized token counts run a decode
instance, and the tail fuses the RMSNorm and the reduction of P routed
partials into it. Larger token counts run a prefill GEMM. The baseline
is the Cake programs of #7979, which are now on FlashInfer main
("previous"). Speedup = previous / this PR. This PR changes one route of
the TP1 decode tail variant on NVIDIA GB300 and adds no program. On
NVIDIA GB300, the TP1 decode tail row of 3 tokens with 8 routed partials
now takes the split rows, where #7979 kept its previous route. It now
uses the same split-rows instance as the other TP1 decode tail rows of
1-8 tokens with 8 or more partials on `sm_103a` GPUs (NVIDIA B300 SXM6
AC, NVIDIA GB300). Its outputs stay bitwise those of the previous
program. The row goes from 28.61 µs to 27.85 µs, a 1.027x speedup. Both
sides of this row are measured in the same run, so its previous value is
a new measurement of the #7979 program and not a copy of the #7979
table. The PR changes 1 of the 184 shape rows on NVIDIA GB300. The other
727 shape rows across the four parts run the same machine code and
routes as #7979. Both of their columns show one value, taken from the
table of #7979, so the rows that #7979 changed show no speedup here.

| Projection | TP | Tokens | B200 previous (µs) | B200 this PR (µs) |
B200 speedup | B300 previous (µs) | B300 this PR (µs) | B300 speedup |
GB200 previous (µs) | GB200 this PR (µs) | GB200 speedup | GB300
previous (µs) | GB300 this PR (µs) | GB300 speedup |
|:--|--:|--:|--:|--:|--:|--:|--:|--:|--:|--:|--:|--:|--:|--:|
| front | 1 | 1 | 42.88 | 42.88 | 1.000x | 42.90 | 42.90 | 1.000x |
41.50 | 41.50 | 1.000x | 41.49 | 41.49 | 1.000x |
| front | 1 | 2 | 42.13 | 42.13 | 1.000x | 43.02 | 43.02 | 1.000x |
41.50 | 41.50 | 1.000x | 41.60 | 41.60 | 1.000x |
| front | 1 | 4 | 42.05 | 42.05 | 1.000x | 42.93 | 42.93 | 1.000x |
41.41 | 41.41 | 1.000x | 41.70 | 41.70 | 1.000x |
| front | 1 | 5 | 42.05 | 42.05 | 1.000x | 43.12 | 43.12 | 1.000x |
41.39 | 41.39 | 1.000x | 41.71 | 41.71 | 1.000x |
| front | 1 | 8 | 41.86 | 41.86 | 1.000x | 42.85 | 42.85 | 1.000x |
41.31 | 41.31 | 1.000x | 41.79 | 41.79 | 1.000x |
| front | 1 | 9 | 42.06 | 42.06 | 1.000x | 42.91 | 42.91 | 1.000x |
41.49 | 41.49 | 1.000x | 41.97 | 41.97 | 1.000x |
| front | 1 | 16 | 42.34 | 42.34 | 1.000x | 43.34 | 43.34 | 1.000x |
41.94 | 41.94 | 1.000x | 42.53 | 42.53 | 1.000x |
| front | 1 | 32 | 42.66 | 42.66 | 1.000x | 43.49 | 43.49 | 1.000x |
41.92 | 41.92 | 1.000x | 42.42 | 42.42 | 1.000x |
| front | 1 | 64 | 44.26 | 44.26 | 1.000x | 44.43 | 44.43 | 1.000x |
43.25 | 43.25 | 1.000x | 43.58 | 43.58 | 1.000x |
| front | 1 | 128 | 49.09 | 49.09 | 1.000x | 48.90 | 48.90 | 1.000x |
48.46 | 48.46 | 1.000x | 48.03 | 48.03 | 1.000x |
| front | 1 | 200 | 50.78 | 50.78 | 1.000x | 52.29 | 52.29 | 1.000x |
51.15 | 51.15 | 1.000x | 48.53 | 48.53 | 1.000x |
| front | 1 | 256 | 51.04 | 51.04 | 1.000x | 52.48 | 52.48 | 1.000x |
52.03 | 52.03 | 1.000x | 48.83 | 48.83 | 1.000x |
| front | 1 | 512 | 85.44 | 85.44 | 1.000x | 79.71 | 79.71 | 1.000x |
92.45 | 92.45 | 1.000x | 68.21 | 68.21 | 1.000x |
| front | 1 | 768 | 126.77 | 126.77 | 1.000x | 128.29 | 128.29 | 1.000x
| 141.66 | 141.66 | 1.000x | 101.22 | 101.22 | 1.000x |
| front | 1 | 1024 | 167.33 | 167.33 | 1.000x | 165.51 | 165.51 | 1.000x
| 170.29 | 170.29 | 1.000x | 131.97 | 131.97 | 1.000x |
| front | 1 | 2048 | 324.30 | 324.30 | 1.000x | 314.63 | 314.63 | 1.000x
| 312.98 | 312.98 | 1.000x | 250.75 | 250.75 | 1.000x |
| front | 1 | 4096 | 614.83 | 614.83 | 1.000x | 547.78 | 547.78 | 1.000x
| 640.60 | 640.60 | 1.000x | 528.51 | 528.51 | 1.000x |
| front | 1 | 8192 | 1220.26 | 1220.26 | 1.000x | 1080.59 | 1080.59 |
1.000x | 1317.63 | 1317.63 | 1.000x | 1092.76 | 1092.76 | 1.000x |
| front | 1 | 16384 | 2404.14 | 2404.14 | 1.000x | 2213.30 | 2213.30 |
1.000x | 2668.08 | 2668.08 | 1.000x | 2193.13 | 2193.13 | 1.000x |
| front | 8 | 1 | 18.99 | 18.99 | 1.000x | 18.88 | 18.88 | 1.000x |
18.32 | 18.32 | 1.000x | 18.40 | 18.40 | 1.000x |
| front | 8 | 2 | 18.93 | 18.93 | 1.000x | 19.02 | 19.02 | 1.000x |
18.32 | 18.32 | 1.000x | 18.43 | 18.43 | 1.000x |
| front | 8 | 4 | 18.94 | 18.94 | 1.000x | 19.02 | 19.02 | 1.000x |
18.32 | 18.32 | 1.000x | 18.46 | 18.46 | 1.000x |
| front | 8 | 5 | 19.12 | 19.12 | 1.000x | 18.93 | 18.93 | 1.000x |
18.38 | 18.38 | 1.000x | 18.38 | 18.38 | 1.000x |
| front | 8 | 8 | 19.10 | 19.10 | 1.000x | 18.99 | 18.99 | 1.000x |
18.37 | 18.37 | 1.000x | 18.37 | 18.37 | 1.000x |
| front | 8 | 9 | 19.18 | 19.18 | 1.000x | 19.10 | 19.10 | 1.000x |
18.46 | 18.46 | 1.000x | 18.43 | 18.43 | 1.000x |
| front | 8 | 16 | 19.14 | 19.14 | 1.000x | 19.20 | 19.20 | 1.000x |
18.54 | 18.54 | 1.000x | 18.51 | 18.51 | 1.000x |
| front | 8 | 32 | 19.65 | 19.65 | 1.000x | 19.70 | 19.70 | 1.000x |
18.88 | 18.88 | 1.000x | 18.94 | 18.94 | 1.000x |
| front | 8 | 64 | 20.51 | 20.51 | 1.000x | 20.38 | 20.38 | 1.000x |
19.73 | 19.73 | 1.000x | 19.82 | 19.82 | 1.000x |
| front | 8 | 128 | 25.74 | 25.74 | 1.000x | 25.68 | 25.68 | 1.000x |
25.30 | 25.30 | 1.000x | 24.62 | 24.62 | 1.000x |
| front | 8 | 200 | 29.92 | 29.92 | 1.000x | 29.12 | 29.12 | 1.000x |
29.47 | 29.47 | 1.000x | 28.03 | 28.03 | 1.000x |
| front | 8 | 256 | 29.95 | 29.95 | 1.000x | 29.38 | 29.38 | 1.000x |
29.82 | 29.82 | 1.000x | 27.97 | 27.97 | 1.000x |
| front | 8 | 512 | 40.37 | 40.37 | 1.000x | 38.11 | 38.11 | 1.000x |
38.86 | 38.86 | 1.000x | 36.21 | 36.21 | 1.000x |
| front | 8 | 640 | 46.96 | 46.96 | 1.000x | 44.06 | 44.06 | 1.000x |
46.80 | 46.80 | 1.000x | 41.84 | 41.84 | 1.000x |
| front | 8 | 768 | 47.28 | 47.28 | 1.000x | 46.26 | 46.26 | 1.000x |
47.71 | 47.71 | 1.000x | 42.27 | 42.27 | 1.000x |
| front | 8 | 769 | — | — | — | — | — | — | 68.71 | 68.71 | 1.000x |
54.43 | 54.43 | 1.000x |
| front | 8 | 800 | — | — | — | — | — | — | 68.69 | 68.69 | 1.000x |
54.56 | 54.56 | 1.000x |
| front | 8 | 897 | — | — | — | — | — | — | 70.63 | 70.63 | 1.000x |
55.11 | 55.11 | 1.000x |
| front | 8 | 960 | — | — | — | — | — | — | 70.74 | 70.74 | 1.000x |
55.09 | 55.09 | 1.000x |
| front | 8 | 1000 | — | — | — | — | — | — | 71.36 | 71.36 | 1.000x |
55.25 | 55.25 | 1.000x |
| front | 8 | 1024 | 67.18 | 67.18 | 1.000x | 65.47 | 65.47 | 1.000x |
72.38 | 72.38 | 1.000x | 55.88 | 55.88 | 1.000x |
| front | 8 | 1793 | 114.55 | 114.55 | 1.000x | — | — | — | — | — | — |
— | — | — |
| front | 8 | 1800 | 114.91 | 114.91 | 1.000x | 110.59 | 110.59 | 1.000x
| 123.63 | 123.63 | 1.000x | 93.52 | 93.52 | 1.000x |
| front | 8 | 1900 | 116.06 | 116.06 | 1.000x | — | — | — | — | — | — |
— | — | — |
| front | 8 | 2000 | 114.52 | 114.52 | 1.000x | 112.45 | 112.45 | 1.000x
| 127.89 | 127.89 | 1.000x | 95.16 | 95.16 | 1.000x |
| front | 8 | 2048 | 119.73 | 119.73 | 1.000x | 114.37 | 114.37 | 1.000x
| 129.41 | 129.41 | 1.000x | 95.55 | 95.55 | 1.000x |
| front | 8 | 4096 | 235.01 | 235.01 | 1.000x | 230.29 | 230.29 | 1.000x
| 240.68 | 240.68 | 1.000x | 190.99 | 190.99 | 1.000x |
| front | 8 | 8192 | 492.32 | 492.32 | 1.000x | 480.21 | 480.21 | 1.000x
| 471.60 | 471.60 | 1.000x | 383.97 | 383.97 | 1.000x |
| front | 8 | 16384 | 909.49 | 909.49 | 1.000x | 800.25 | 800.25 |
1.000x | 959.91 | 959.91 | 1.000x | 804.95 | 804.95 | 1.000x |
| tail | 1 | 1 | 26.42 | 26.42 | 1.000x | 26.64 | 26.64 | 1.000x | 25.71
| 25.71 | 1.000x | 25.76 | 25.76 | 1.000x |
| tail | 1 | 2 | 26.42 | 26.42 | 1.000x | 26.72 | 26.72 | 1.000x | 25.70
| 25.70 | 1.000x | 25.86 | 25.86 | 1.000x |
| tail | 1 | 4 | 26.54 | 26.54 | 1.000x | 26.82 | 26.82 | 1.000x | 25.74
| 25.74 | 1.000x | 25.92 | 25.92 | 1.000x |
| tail | 1 | 5 | 26.48 | 26.48 | 1.000x | 26.88 | 26.88 | 1.000x | 25.74
| 25.74 | 1.000x | 26.03 | 26.03 | 1.000x |
| tail | 1 | 8 | 26.50 | 26.50 | 1.000x | 26.78 | 26.78 | 1.000x | 25.78
| 25.78 | 1.000x | 26.03 | 26.03 | 1.000x |
| tail | 1 | 9 | 27.98 | 27.98 | 1.000x | 27.66 | 27.66 | 1.000x | 26.88
| 26.88 | 1.000x | 26.82 | 26.82 | 1.000x |
| tail | 1 | 16 | 28.02 | 28.02 | 1.000x | 27.76 | 27.76 | 1.000x |
26.88 | 26.88 | 1.000x | 27.01 | 27.01 | 1.000x |
| tail | 1 | 32 | 27.63 | 27.63 | 1.000x | 27.59 | 27.59 | 1.000x |
26.78 | 26.78 | 1.000x | 26.80 | 26.80 | 1.000x |
| tail | 1 | 64 | 27.58 | 27.58 | 1.000x | 27.89 | 27.89 | 1.000x |
27.06 | 27.06 | 1.000x | 26.83 | 26.83 | 1.000x |
| tail | 1 | 128 | 29.60 | 29.60 | 1.000x | 30.02 | 30.02 | 1.000x |
28.80 | 28.80 | 1.000x | 28.62 | 28.62 | 1.000x |
| tail | 1 | 129 | 37.39 | 37.39 | 1.000x | 37.41 | 37.41 | 1.000x |
36.98 | 36.98 | 1.000x | 35.84 | 35.84 | 1.000x |
| tail | 1 | 256 | 38.46 | 38.46 | 1.000x | 38.70 | 38.70 | 1.000x |
38.19 | 38.19 | 1.000x | 36.67 | 36.67 | 1.000x |
| tail | 1 | 300 | 54.00 | 54.00 | 1.000x | 52.64 | 52.64 | 1.000x |
48.35 | 48.35 | 1.000x | 41.57 | 41.57 | 1.000x |
| tail | 1 | 384 | 54.62 | 54.62 | 1.000x | 52.67 | 52.67 | 1.000x |
47.63 | 47.63 | 1.000x | 41.42 | 41.42 | 1.000x |
| tail | 1 | 512 | 55.70 | 55.70 | 1.000x | 53.33 | 53.33 | 1.000x |
51.68 | 51.68 | 1.000x | 42.50 | 42.50 | 1.000x |
| tail | 1 | 1024 | 98.61 | 98.61 | 1.000x | 95.79 | 95.79 | 1.000x |
105.65 | 105.65 | 1.000x | 83.09 | 83.09 | 1.000x |
| tail | 1 | 2048 | 192.64 | 192.64 | 1.000x | 188.91 | 188.91 | 1.000x
| 189.74 | 189.74 | 1.000x | 147.74 | 147.74 | 1.000x |
| tail | 1 | 4096 | 387.46 | 387.46 | 1.000x | 385.22 | 385.22 | 1.000x
| 368.18 | 368.18 | 1.000x | 293.95 | 293.95 | 1.000x |
| tail | 1 | 8192 | 718.12 | 718.12 | 1.000x | 651.83 | 651.83 | 1.000x
| 743.41 | 743.41 | 1.000x | 625.10 | 625.10 | 1.000x |
| tail | 1 | 16384 | 1446.74 | 1446.74 | 1.000x | 1291.42 | 1291.42 |
1.000x | 1521.33 | 1521.33 | 1.000x | 1284.41 | 1284.41 | 1.000x |
| tail | 8 | 1 | 7.87 | 7.87 | 1.000x | 7.86 | 7.86 | 1.000x | 7.74 |
7.74 | 1.000x | 7.58 | 7.58 | 1.000x |
| tail | 8 | 2 | 7.90 | 7.90 | 1.000x | 7.84 | 7.84 | 1.000x | 7.65 |
7.65 | 1.000x | 7.58 | 7.58 | 1.000x |
| tail | 8 | 4 | 7.92 | 7.92 | 1.000x | 7.86 | 7.86 | 1.000x | 7.70 |
7.70 | 1.000x | 7.65 | 7.65 | 1.000x |
| tail | 8 | 5 | 7.95 | 7.95 | 1.000x | 7.79 | 7.79 | 1.000x | 7.70 |
7.70 | 1.000x | 7.65 | 7.65 | 1.000x |
| tail | 8 | 8 | 8.00 | 8.00 | 1.000x | 7.97 | 7.97 | 1.000x | 7.76 |
7.76 | 1.000x | 7.68 | 7.68 | 1.000x |
| tail | 8 | 9 | 8.70 | 8.70 | 1.000x | 8.59 | 8.59 | 1.000x | 8.45 |
8.45 | 1.000x | 8.40 | 8.40 | 1.000x |
| tail | 8 | 16 | 9.34 | 9.34 | 1.000x | 8.94 | 8.94 | 1.000x | 9.16 |
9.16 | 1.000x | 8.94 | 8.94 | 1.000x |
| tail | 8 | 32 | 10.26 | 10.26 | 1.000x | 10.32 | 10.32 | 1.000x | 9.87
| 9.87 | 1.000x | 9.95 | 9.95 | 1.000x |
| tail | 8 | 64 | 10.85 | 10.85 | 1.000x | 10.67 | 10.67 | 1.000x |
10.45 | 10.45 | 1.000x | 10.45 | 10.45 | 1.000x |
| tail | 8 | 128 | 12.58 | 12.58 | 1.000x | 12.24 | 12.24 | 1.000x |
12.19 | 12.19 | 1.000x | 12.05 | 12.05 | 1.000x |
| tail | 8 | 256 | 14.94 | 14.94 | 1.000x | 14.05 | 14.05 | 1.000x |
14.51 | 14.51 | 1.000x | 14.03 | 14.03 | 1.000x |
| tail | 8 | 300 | 17.09 | 17.09 | 1.000x | 17.62 | 17.62 | 1.000x |
16.67 | 16.67 | 1.000x | 17.90 | 17.90 | 1.000x |
| tail | 8 | 512 | 18.69 | 18.69 | 1.000x | 17.66 | 17.66 | 1.000x |
18.66 | 18.66 | 1.000x | 17.68 | 17.68 | 1.000x |
| tail | 8 | 1024 | 26.00 | 26.00 | 1.000x | 23.97 | 23.97 | 1.000x |
23.81 | 23.81 | 1.000x | 22.67 | 22.67 | 1.000x |
| tail | 8 | 2048 | 39.12 | 39.12 | 1.000x | 36.48 | 36.48 | 1.000x |
32.83 | 32.83 | 1.000x | 30.80 | 30.80 | 1.000x |
| tail | 8 | 4096 | 62.72 | 62.72 | 1.000x | 58.86 | 58.86 | 1.000x |
57.54 | 57.54 | 1.000x | 51.84 | 51.84 | 1.000x |
| tail | 8 | 8192 | 111.60 | 111.60 | 1.000x | 102.42 | 102.42 | 1.000x
| 112.70 | 112.70 | 1.000x | 93.39 | 93.39 | 1.000x |
| tail | 8 | 16384 | 219.62 | 219.62 | 1.000x | 213.55 | 213.55 | 1.000x
| 222.29 | 222.29 | 1.000x | 182.40 | 182.40 | 1.000x |

*Times are µs per call on one rank from `bench_gpu_time_with_cupti` with
cold L2 and CUDA graph replay; both sides interleave in groups over two
passes, the second in reversed order; each value is the mean of the two
per-pass medians on one GPU; rows this PR does not change show the value
of #7979 in both columns; speedup = previous / this PR; tail rows reduce
one routed partial; NVIDIA B200 (`sm_100a`, 148 SMs), NVIDIA B300 SXM6
AC (`sm_103a`, 148 SMs), NVIDIA GB200 (`sm_100a`, 152 SMs), NVIDIA GB300
(`sm_103a`, 152 SMs); CUDA 13.4; "—" = the row is not on that part's
shape list.*

| Projection | TP | Tokens | Partials | B200 previous (µs) | B200 this
PR (µs) | B200 speedup | B300 previous (µs) | B300 this PR (µs) | B300
speedup | GB200 previous (µs) | GB200 this PR (µs) | GB200 speedup |
GB300 previous (µs) | GB300 this PR (µs) | GB300 speedup |
|:--|--:|--:|--:|--:|--:|--:|--:|--:|--:|--:|--:|--:|--:|--:|--:|
| tail | 1 | 1 | 2 | 26.45 | 26.45 | 1.000x | 26.67 | 26.67 | 1.000x |
25.68 | 25.68 | 1.000x | 25.66 | 25.66 | 1.000x |
| tail | 1 | 1 | 5 | 26.70 | 26.70 | 1.000x | 26.77 | 26.77 | 1.000x |
25.78 | 25.78 | 1.000x | 25.97 | 25.97 | 1.000x |
| tail | 1 | 1 | 6 | 28.32 | 28.32 | 1.000x | 27.42 | 27.42 | 1.000x |
27.47 | 27.47 | 1.000x | 27.02 | 27.02 | 1.000x |
| tail | 1 | 1 | 7 | 29.36 | 29.36 | 1.000x | 29.31 | 29.31 | 1.000x |
28.18 | 28.18 | 1.000x | 28.27 | 28.27 | 1.000x |
| tail | 1 | 1 | 8 | 29.90 | 29.90 | 1.000x | 28.77 | 28.77 | 1.000x |
28.75 | 28.75 | 1.000x | 27.86 | 27.86 | 1.000x |
| tail | 1 | 1 | 16 | 34.21 | 34.21 | 1.000x | 28.93 | 28.93 | 1.000x |
32.86 | 32.86 | 1.000x | 28.02 | 28.02 | 1.000x |
| tail | 1 | 2 | 5 | 27.01 | 27.01 | 1.000x | 26.88 | 26.88 | 1.000x |
26.51 | 26.51 | 1.000x | 26.06 | 26.06 | 1.000x |
| tail | 1 | 2 | 6 | 28.90 | 28.90 | 1.000x | 28.32 | 28.32 | 1.000x |
27.26 | 27.26 | 1.000x | 26.58 | 26.58 | 1.000x |
| tail | 1 | 2 | 7 | 29.34 | 29.34 | 1.000x | 29.46 | 29.46 | 1.000x |
28.32 | 28.32 | 1.000x | 28.34 | 28.34 | 1.000x |
| tail | 1 | 2 | 8 | 29.71 | 29.71 | 1.000x | 28.77 | 28.77 | 1.000x |
28.54 | 28.54 | 1.000x | 27.55 | 27.55 | 1.000x |
| tail | 1 | 2 | 16 | 34.88 | 34.88 | 1.000x | 28.99 | 28.99 | 1.000x |
33.36 | 33.36 | 1.000x | 27.70 | 27.70 | 1.000x |
| tail | 1 | 3 | 5 | 27.07 | 27.07 | 1.000x | 26.85 | 26.85 | 1.000x |
26.75 | 26.75 | 1.000x | 26.16 | 26.16 | 1.000x |
| tail | 1 | 3 | 6 | 29.39 | 29.39 | 1.000x | 28.62 | 28.62 | 1.000x |
28.34 | 28.34 | 1.000x | 27.71 | 27.71 | 1.000x |
| tail | 1 | 3 | 7 | 29.39 | 29.39 | 1.000x | 29.52 | 29.52 | 1.000x |
28.18 | 28.18 | 1.000x | 28.38 | 28.38 | 1.000x |
| tail | 1 | 3 | 8 | 29.87 | 29.87 | 1.000x | 28.83 | 28.83 | 1.000x |
28.43 | 28.43 | 1.000x | 28.61 | 27.85 | 1.027x |
| tail | 1 | 3 | 16 | 34.66 | 34.66 | 1.000x | 28.99 | 28.99 | 1.000x |
33.39 | 33.39 | 1.000x | 28.06 | 28.06 | 1.000x |
| tail | 1 | 4 | 5 | 26.91 | 26.91 | 1.000x | 26.88 | 26.88 | 1.000x |
26.05 | 26.05 | 1.000x | 25.95 | 25.95 | 1.000x |
| tail | 1 | 4 | 6 | 28.59 | 28.59 | 1.000x | 27.87 | 27.87 | 1.000x |
28.08 | 28.08 | 1.000x | 27.42 | 27.42 | 1.000x |
| tail | 1 | 4 | 7 | 29.70 | 29.70 | 1.000x | 29.41 | 29.41 | 1.000x |
28.34 | 28.34 | 1.000x | 28.43 | 28.43 | 1.000x |
| tail | 1 | 4 | 8 | 29.68 | 29.68 | 1.000x | 28.80 | 28.80 | 1.000x |
28.59 | 28.59 | 1.000x | 27.54 | 27.54 | 1.000x |
| tail | 1 | 4 | 16 | 34.93 | 34.93 | 1.000x | 28.98 | 28.98 | 1.000x |
33.46 | 33.46 | 1.000x | 27.71 | 27.71 | 1.000x |
| tail | 1 | 5 | 2 | 26.56 | 26.56 | 1.000x | 26.86 | 26.86 | 1.000x |
25.76 | 25.76 | 1.000x | 25.78 | 25.78 | 1.000x |
| tail | 1 | 5 | 3 | 26.85 | 26.85 | 1.000x | 26.93 | 26.93 | 1.000x |
26.26 | 26.26 | 1.000x | 26.06 | 26.06 | 1.000x |
| tail | 1 | 5 | 4 | 28.66 | 28.66 | 1.000x | 28.94 | 28.94 | 1.000x |
27.94 | 27.94 | 1.000x | 28.02 | 28.02 | 1.000x |
| tail | 1 | 5 | 5 | 28.96 | 28.96 | 1.000x | 28.90 | 28.90 | 1.000x |
27.89 | 27.89 | 1.000x | 27.95 | 27.95 | 1.000x |
| tail | 1 | 5 | 6 | 29.33 | 29.33 | 1.000x | 29.01 | 29.01 | 1.000x |
28.05 | 28.05 | 1.000x | 28.08 | 28.08 | 1.000x |
| tail | 1 | 5 | 7 | 29.23 | 29.23 | 1.000x | 29.30 | 29.30 | 1.000x |
28.38 | 28.38 | 1.000x | 28.46 | 28.46 | 1.000x |
| tail | 1 | 5 | 8 | 29.76 | 29.76 | 1.000x | 28.83 | 28.83 | 1.000x |
28.51 | 28.51 | 1.000x | 27.94 | 27.94 | 1.000x |
| tail | 1 | 5 | 16 | 34.96 | 34.96 | 1.000x | 29.04 | 29.04 | 1.000x |
33.39 | 33.39 | 1.000x | 28.08 | 28.08 | 1.000x |
| tail | 1 | 6 | 3 | 27.07 | 27.07 | 1.000x | 27.12 | 27.12 | 1.000x |
26.32 | 26.32 | 1.000x | 26.19 | 26.19 | 1.000x |
| tail | 1 | 6 | 4 | 28.74 | 28.74 | 1.000x | 28.98 | 28.98 | 1.000x |
28.02 | 28.02 | 1.000x | 27.98 | 27.98 | 1.000x |
| tail | 1 | 6 | 5 | 28.98 | 28.98 | 1.000x | 28.85 | 28.85 | 1.000x |
27.90 | 27.90 | 1.000x | 27.95 | 27.95 | 1.000x |
| tail | 1 | 6 | 6 | 29.01 | 29.01 | 1.000x | 29.12 | 29.12 | 1.000x |
28.05 | 28.05 | 1.000x | 28.19 | 28.19 | 1.000x |
| tail | 1 | 6 | 7 | 29.46 | 29.46 | 1.000x | 29.25 | 29.25 | 1.000x |
28.38 | 28.38 | 1.000x | 28.45 | 28.45 | 1.000x |
| tail | 1 | 6 | 8 | 29.90 | 29.90 | 1.000x | 28.85 | 28.85 | 1.000x |
28.61 | 28.61 | 1.000x | 27.55 | 27.55 | 1.000x |
| tail | 1 | 6 | 16 | 34.37 | 34.37 | 1.000x | 29.06 | 29.06 | 1.000x |
33.76 | 33.76 | 1.000x | 27.76 | 27.76 | 1.000x |
| tail | 1 | 7 | 3 | 27.06 | 27.06 | 1.000x | 26.91 | 26.91 | 1.000x |
26.69 | 26.69 | 1.000x | 26.37 | 26.37 | 1.000x |
| tail | 1 | 7 | 4 | 28.78 | 28.78 | 1.000x | 28.96 | 28.96 | 1.000x |
27.92 | 27.92 | 1.000x | 27.98 | 27.98 | 1.000x |
| tail | 1 | 7 | 5 | 29.12 | 29.12 | 1.000x | 29.06 | 29.06 | 1.000x |
27.89 | 27.89 | 1.000x | 27.95 | 27.95 | 1.000x |
| tail | 1 | 7 | 6 | 28.96 | 28.96 | 1.000x | 29.06 | 29.06 | 1.000x |
28.00 | 28.00 | 1.000x | 28.03 | 28.03 | 1.000x |
| tail | 1 | 7 | 7 | 29.76 | 29.76 | 1.000x | 29.30 | 29.30 | 1.000x |
28.27 | 28.27 | 1.000x | 28.40 | 28.40 | 1.000x |
| tail | 1 | 7 | 8 | 29.55 | 29.55 | 1.000x | 28.86 | 28.86 | 1.000x |
28.54 | 28.54 | 1.000x | 27.58 | 27.58 | 1.000x |
| tail | 1 | 7 | 16 | 34.64 | 34.64 | 1.000x | 29.06 | 29.06 | 1.000x |
33.65 | 33.65 | 1.000x | 27.81 | 27.81 | 1.000x |
| tail | 1 | 8 | 2 | 26.82 | 26.82 | 1.000x | 27.07 | 27.07 | 1.000x |
25.82 | 25.82 | 1.000x | 25.84 | 25.84 | 1.000x |
| tail | 1 | 8 | 3 | 27.74 | 27.74 | 1.000x | 27.22 | 27.22 | 1.000x |
26.69 | 26.69 | 1.000x | 26.35 | 26.35 | 1.000x |
| tail | 1 | 8 | 4 | 28.69 | 28.69 | 1.000x | 28.91 | 28.91 | 1.000x |
28.00 | 28.00 | 1.000x | 28.03 | 28.03 | 1.000x |
| tail | 1 | 8 | 5 | 28.88 | 28.88 | 1.000x | 28.94 | 28.94 | 1.000x |
28.02 | 28.02 | 1.000x | 27.92 | 27.92 | 1.000x |
| tail | 1 | 8 | 6 | 29.02 | 29.02 | 1.000x | 28.99 | 28.99 | 1.000x |
28.03 | 28.03 | 1.000x | 28.13 | 28.13 | 1.000x |
| tail | 1 | 8 | 7 | 29.74 | 29.74 | 1.000x | 29.39 | 29.39 | 1.000x |
28.40 | 28.40 | 1.000x | 28.43 | 28.43 | 1.000x |
| tail | 1 | 8 | 8 | 29.73 | 29.73 | 1.000x | 28.90 | 28.90 | 1.000x |
28.58 | 28.58 | 1.000x | 27.63 | 27.63 | 1.000x |
| tail | 1 | 8 | 16 | 35.01 | 35.01 | 1.000x | 29.09 | 29.09 | 1.000x |
33.70 | 33.70 | 1.000x | 27.89 | 27.89 | 1.000x |
| tail | 1 | 9 | 2 | 28.38 | 28.38 | 1.000x | 28.40 | 28.40 | 1.000x |
27.49 | 27.49 | 1.000x | 27.25 | 27.25 | 1.000x |
| tail | 1 | 9 | 8 | 30.16 | 30.16 | 1.000x | 29.97 | 29.97 | 1.000x |
29.38 | 29.38 | 1.000x | 29.10 | 29.10 | 1.000x |
| tail | 1 | 16 | 2 | 28.35 | 28.35 | 1.000x | 28.56 | 28.56 | 1.000x |
27.60 | 27.60 | 1.000x | 27.33 | 27.33 | 1.000x |
| tail | 1 | 16 | 8 | 30.21 | 30.21 | 1.000x | 30.08 | 30.08 | 1.000x |
29.63 | 29.63 | 1.000x | 29.66 | 29.66 | 1.000x |
| tail | 1 | 32 | 2 | 28.08 | 28.08 | 1.000x | 28.02 | 28.02 | 1.000x |
27.28 | 27.28 | 1.000x | 27.18 | 27.18 | 1.000x |
| tail | 1 | 32 | 8 | 29.98 | 29.98 | 1.000x | 30.02 | 30.02 | 1.000x |
28.99 | 28.99 | 1.000x | 29.04 | 29.04 | 1.000x |
| tail | 1 | 64 | 2 | 28.42 | 28.42 | 1.000x | 28.50 | 28.50 | 1.000x |
27.61 | 27.61 | 1.000x | 27.52 | 27.52 | 1.000x |
| tail | 1 | 64 | 8 | 30.45 | 30.45 | 1.000x | 30.64 | 30.64 | 1.000x |
29.54 | 29.54 | 1.000x | 29.46 | 29.46 | 1.000x |
| tail | 1 | 128 | 2 | 30.21 | 30.21 | 1.000x | 30.38 | 30.38 | 1.000x |
29.52 | 29.52 | 1.000x | 29.31 | 29.31 | 1.000x |
| tail | 1 | 128 | 8 | 32.94 | 32.94 | 1.000x | 33.17 | 33.17 | 1.000x |
31.89 | 31.89 | 1.000x | 31.78 | 31.78 | 1.000x |
| tail | 8 | 1 | 2 | 10.86 | 10.86 | 1.000x | 10.40 | 10.40 | 1.000x |
10.53 | 10.53 | 1.000x | 10.35 | 10.35 | 1.000x |
| tail | 8 | 1 | 5 | 10.54 | 10.54 | 1.000x | 10.34 | 10.34 | 1.000x |
10.35 | 10.35 | 1.000x | 10.51 | 10.51 | 1.000x |
| tail | 8 | 1 | 6 | 11.38 | 11.38 | 1.000x | 10.94 | 10.94 | 1.000x |
10.66 | 10.66 | 1.000x | 10.61 | 10.61 | 1.000x |
| tail | 8 | 1 | 7 | 11.09 | 11.09 | 1.000x | 10.96 | 10.96 | 1.000x |
10.86 | 10.86 | 1.000x | 11.07 | 11.07 | 1.000x |
| tail | 8 | 1 | 8 | 11.62 | 11.62 | 1.000x | 11.09 | 11.09 | 1.000x |
10.91 | 10.91 | 1.000x | 10.71 | 10.71 | 1.000x |
| tail | 8 | 1 | 16 | 13.17 | 13.17 | 1.000x | 12.77 | 12.77 | 1.000x |
12.43 | 12.43 | 1.000x | 12.18 | 12.18 | 1.000x |
| tail | 8 | 2 | 4 | 10.37 | 10.37 | 1.000x | 10.48 | 10.48 | 1.000x |
10.35 | 10.35 | 1.000x | 10.67 | 10.67 | 1.000x |
| tail | 8 | 2 | 5 | 10.64 | 10.64 | 1.000x | 10.56 | 10.56 | 1.000x |
10.48 | 10.48 | 1.000x | 10.69 | 10.69 | 1.000x |
| tail | 8 | 2 | 6 | 11.10 | 11.10 | 1.000x | 10.90 | 10.90 | 1.000x |
10.91 | 10.91 | 1.000x | 11.09 | 11.09 | 1.000x |
| tail | 8 | 2 | 7 | 11.09 | 11.09 | 1.000x | 11.02 | 11.02 | 1.000x |
10.93 | 10.93 | 1.000x | 11.18 | 11.18 | 1.000x |
| tail | 8 | 2 | 8 | 11.18 | 11.18 | 1.000x | 11.09 | 11.09 | 1.000x |
11.02 | 11.02 | 1.000x | 11.17 | 11.17 | 1.000x |
| tail | 8 | 2 | 16 | 13.18 | 13.18 | 1.000x | 12.77 | 12.77 | 1.000x |
12.77 | 12.77 | 1.000x | 12.70 | 12.70 | 1.000x |
| tail | 8 | 3 | 4 | 10.53 | 10.53 | 1.000x | 10.42 | 10.42 | 1.000x |
10.38 | 10.38 | 1.000x | 10.53 | 10.53 | 1.000x |
| tail | 8 | 3 | 5 | 10.67 | 10.67 | 1.000x | 10.58 | 10.58 | 1.000x |
10.50 | 10.50 | 1.000x | 10.69 | 10.69 | 1.000x |
| tail | 8 | 3 | 6 | 11.10 | 11.10 | 1.000x | 11.04 | 11.04 | 1.000x |
10.90 | 10.90 | 1.000x | 11.10 | 11.10 | 1.000x |
| tail | 8 | 3 | 7 | 11.17 | 11.17 | 1.000x | 11.06 | 11.06 | 1.000x |
10.99 | 10.99 | 1.000x | 11.15 | 11.15 | 1.000x |
| tail | 8 | 3 | 8 | 11.25 | 11.25 | 1.000x | 11.12 | 11.12 | 1.000x |
11.04 | 11.04 | 1.000x | 11.28 | 11.28 | 1.000x |
| tail | 8 | 3 | 16 | 13.20 | 13.20 | 1.000x | 12.75 | 12.75 | 1.000x |
12.77 | 12.77 | 1.000x | 12.78 | 12.78 | 1.000x |
| tail | 8 | 4 | 2 | 11.33 | 11.33 | 1.000x | 11.01 | 11.01 | 1.000x |
10.96 | 10.96 | 1.000x | 10.82 | 10.82 | 1.000x |
| tail | 8 | 4 | 4 | 10.42 | 10.42 | 1.000x | 10.32 | 10.32 | 1.000x |
10.48 | 10.48 | 1.000x | 10.54 | 10.54 | 1.000x |
| tail | 8 | 4 | 5 | 10.69 | 10.69 | 1.000x | 10.51 | 10.51 | 1.000x |
10.50 | 10.50 | 1.000x | 10.67 | 10.67 | 1.000x |
| tail | 8 | 4 | 6 | 11.41 | 11.41 | 1.000x | 11.12 | 11.12 | 1.000x |
10.90 | 10.90 | 1.000x | 10.78 | 10.78 | 1.000x |
| tail | 8 | 4 | 7 | 11.20 | 11.20 | 1.000x | 11.04 | 11.04 | 1.000x |
11.01 | 11.01 | 1.000x | 11.18 | 11.18 | 1.000x |
| tail | 8 | 4 | 8 | 11.65 | 11.65 | 1.000x | 11.26 | 11.26 | 1.000x |
11.10 | 11.10 | 1.000x | 10.86 | 10.86 | 1.000x |
| tail | 8 | 4 | 16 | 13.30 | 13.30 | 1.000x | 12.90 | 12.90 | 1.000x |
12.82 | 12.82 | 1.000x | 12.70 | 12.70 | 1.000x |
| tail | 8 | 5 | 2 | 11.12 | 11.12 | 1.000x | 11.06 | 11.06 | 1.000x |
10.77 | 10.77 | 1.000x | 10.80 | 10.80 | 1.000x |
| tail | 8 | 5 | 8 | 15.55 | 15.55 | 1.000x | 15.30 | 15.30 | 1.000x |
15.18 | 15.18 | 1.000x | 15.12 | 15.12 | 1.000x |
| tail | 8 | 8 | 2 | 11.12 | 11.12 | 1.000x | 10.94 | 10.94 | 1.000x |
10.82 | 10.82 | 1.000x | 10.69 | 10.69 | 1.000x |
| tail | 8 | 8 | 8 | 15.57 | 15.57 | 1.000x | 15.49 | 15.49 | 1.000x |
15.36 | 15.36 | 1.000x | 15.17 | 15.17 | 1.000x |
| tail | 8 | 9 | 2 | 11.23 | 11.23 | 1.000x | 11.01 | 11.01 | 1.000x |
10.91 | 10.91 | 1.000x | 10.82 | 10.82 | 1.000x |
| tail | 8 | 9 | 8 | 15.89 | 15.89 | 1.000x | 15.62 | 15.62 | 1.000x |
15.42 | 15.42 | 1.000x | 15.14 | 15.14 | 1.000x |
| tail | 8 | 16 | 2 | 11.25 | 11.25 | 1.000x | 11.26 | 11.26 | 1.000x |
10.98 | 10.98 | 1.000x | 10.85 | 10.85 | 1.000x |
| tail | 8 | 16 | 8 | 15.97 | 15.97 | 1.000x | 15.66 | 15.66 | 1.000x |
15.46 | 15.46 | 1.000x | 15.34 | 15.34 | 1.000x |
| tail | 8 | 32 | 2 | 11.74 | 11.74 | 1.000x | 11.62 | 11.62 | 1.000x |
11.52 | 11.52 | 1.000x | 11.46 | 11.46 | 1.000x |
| tail | 8 | 32 | 8 | 16.40 | 16.40 | 1.000x | 16.10 | 16.10 | 1.000x |
15.92 | 15.92 | 1.000x | 15.94 | 15.94 | 1.000x |
| tail | 8 | 64 | 2 | 11.87 | 11.87 | 1.000x | 11.66 | 11.66 | 1.000x |
11.63 | 11.63 | 1.000x | 11.50 | 11.50 | 1.000x |
| tail | 8 | 64 | 8 | 16.48 | 16.48 | 1.000x | 16.26 | 16.26 | 1.000x |
16.18 | 16.18 | 1.000x | 16.05 | 16.05 | 1.000x |
| tail | 8 | 128 | 2 | 13.36 | 13.36 | 1.000x | 13.22 | 13.22 | 1.000x |
13.22 | 13.22 | 1.000x | 12.90 | 12.90 | 1.000x |
| tail | 8 | 128 | 8 | 18.35 | 18.35 | 1.000x | 18.05 | 18.05 | 1.000x |
17.86 | 17.86 | 1.000x | 17.52 | 17.52 | 1.000x |

*Times are µs per call on one rank from `bench_gpu_time_with_cupti` with
cold L2 and CUDA graph replay; both sides interleave in groups over 2
passes, the second in reversed order; rows this PR does not change show
the value of #7979 in both columns, the mean of the two per-pass medians
on one GPU; the NVIDIA GB300 row of 3 tokens and 8 partials measures
both sides in the same run in 8 processes on 4 GPUs: previous is the
median over the processes of each process's first-pass median, and this
PR adds to it the mean over both passes of the median over the processes
of the per-group difference; speedup = previous / this PR; decode tail
rows reduce P routed partials; NVIDIA B200 (`sm_100a`, 148 SMs), NVIDIA
B300 SXM6 AC (`sm_103a`, 148 SMs), NVIDIA GB200 (`sm_100a`, 152 SMs),
NVIDIA GB300 (`sm_103a`, 152 SMs); CUDA 13.4.*

Cake also ships a TP12 fused tail of this block in `kimi_k3_tp12_tail`;
both packages are BF16 only and target `sm_100a` and `sm_103a`.

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [18fb0bf](https://github.com/flashinfer-ai/flashinfer/commit/18fb0bfcc6d7e8a0c25a7784af559cc1e58124cb)

- **作者**: eigen
- **时间**: 2026-10-31T08:07:02Z
- **提交信息**: fix(cake_mega_moe_v3): hang of the E384 T=1024 rank programs under GPU preemption (#8095)

`flashinfer.experimental.mega_moe_v3` runs the Cake MegaMoE v3 prepared
pipeline for the 384-expert, top-6, hidden-5120 model with activation
clamp 10, and a single kernel launch covers dispatch, FC1, clamped
SwiGLU, MXFP8 activation quantization, FC2 and weighted combine. The
kernel has four variants on main, and this PR updates one of them: the
TP/EP rank variant. It fixes a hang in the TP4 EP1 and TP8 EP1 programs
at 1024 tokens, which could occur when the GPU was preempted
(time-sliced with another process). It also re-renders all 32 rank
programs from the current generator. The baseline is the previous Cake
version on main, which is the rank variant delivered by #7633.

| Configuration | Tokens | previous (µs) | this PR (µs) | speedup =
previous / this PR |
|---|---:|---:|---:|---:|
| TP4 EP1 | 1 | 13.69 | 13.70 | 0.999 |
| TP4 EP1 | 4 | 25.98 | 25.97 | 1.000 |
| TP4 EP1 | 16 | 80.98 | 80.97 | 1.000 |
| TP4 EP1 | 32 | 150.69 | 150.68 | 1.000 |
| TP4 EP1 | 128 | 295.50 | 295.49 | 1.000 |
| TP4 EP1 | 512 | 306.65 | 306.66 | 1.000 |
| TP4 EP1 | 1024 | 327.76 | 328.54 | 0.998 |
| TP4 EP1 | 4096 | 438.99 | 438.99 | 1.000 |
| TP8 EP1 | 1 | 12.26 | 12.26 | 1.000 |
| TP8 EP1 | 4 | 18.21 | 18.23 | 0.999 |
| TP8 EP1 | 16 | 53.41 | 53.41 | 1.000 |
| TP8 EP1 | 32 | 95.69 | 95.65 | 1.000 |
| TP8 EP1 | 128 | 188.25 | 188.24 | 1.000 |
| TP8 EP1 | 512 | 198.18 | 198.21 | 1.000 |
| TP8 EP1 | 1024 | 213.03 | 213.79 | 0.996 |
| TP8 EP1 | 4096 | 317.23 | 317.24 | 1.000 |
| TP4 EP4 | 1 | 14.32 | 14.31 | 1.000 |
| TP4 EP4 | 4 | 23.96 | 23.97 | 1.000 |
| TP4 EP4 | 16 | 71.65 | 71.64 | 1.000 |
| TP4 EP4 | 32 | 137.62 | 137.62 | 1.000 |
| TP4 EP4 | 128 | 263.84 | 263.80 | 1.000 |
| TP4 EP4 | 512 | 270.93 | 270.96 | 1.000 |
| TP4 EP4 | 1024 | 277.61 | 277.61 | 1.000 |
| TP4 EP4 | 4096 | 345.46 | 345.60 | 1.000 |
| TP8 EP8 | 1 | 12.99 | 12.99 | 1.000 |
| TP8 EP8 | 4 | 15.94 | 15.94 | 1.000 |
| TP8 EP8 | 16 | 38.82 | 38.81 | 1.000 |
| TP8 EP8 | 32 | 74.76 | 74.72 | 1.001 |
| TP8 EP8 | 128 | 140.08 | 140.07 | 1.000 |
| TP8 EP8 | 512 | 145.06 | 145.05 | 1.000 |
| TP8 EP8 | 1024 | 144.14 | 144.12 | 1.000 |
| TP8 EP8 | 4096 | 194.51 | 194.56 | 1.000 |

*NVIDIA GB300 (sm_103a, 152 SMs), CUDA 13.4 toolkit (13.4.92), driver
580.159.03, PyTorch 2.14.1+cu130. Per-call latency from CUDA-graph
replays (20 calls per graph). The previous and new versions ran in
separate processes, alternated over 6 rounds covering all orders, and
each value is the median of the 6 process medians. The table shows
replicate a of two independent replicates.*

- Speedup ranges from 0.996 to 1.001 in replicate a and from 0.997 to
1.001 in replicate b.
- The two fixed programs at 1024 tokens are 0.2-0.4 % slower in both
replicates (TP4 EP1 0.998 / 0.998, TP8 EP1 0.996 / 0.997). The other 30
shapes are within 0.24 % (within 0.06 % at 16 tokens and above).

The kernel's other three Cake variants (single-rank routed-FP4 pipeline,
single-rank routed-FP8 pipeline and grouped-GEMM routes) ship on sm_100a
and sm_103a, and the rank variant ships on sm_103a only.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Chores**
  * Updated catalog metadata for 32 FP4 pipeline entries.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [deacae9](https://github.com/flashinfer-ai/flashinfer/commit/deacae9249c213bf6b857ee8b2482024f766c457)

- **作者**: eigen
- **时间**: 2026-10-31T07:55:24Z
- **提交信息**: feat(cake_mhc): opt-in non-deterministic mHC autograd backend (#8092)

Cake's mHC (manifold-constrained hyper-connections) training kernel has
one path: BF16 activations, hidden size 4096, 4 residual streams and
FP32 mapping parameters. It covers the forward pass (stats, prepare,
finish) and the backward pass (prepare, finish), and comes in two
numerical modes: deterministic and non-deterministic. The deterministic
mode is the existing `flashinfer.cake_mhc_det_train` package (legacy
alias `flashinfer.cake_mhc_train`). This PR leaves it unchanged and uses
it as the baseline (**det**). This PR adds the non-deterministic mode
(**new**) through `flashinfer.experimental.cake.cake_mhc_train`, which
wraps the backend `flashinfer.experimental.cake.cake_mhc_train_backend`.
It is opt-in with `deterministic=False`, and the default
`deterministic=True` keeps the deterministic path. Only the backward
finish changes. The column slab adds the dfn (mapping-weight gradient)
partial sums straight into dfn with FP32 atomics, so the final reduction
kernel and its partials workspace are no longer needed. dX, dscale and
dbase stay bitwise equal to the deterministic path, and only dfn's
summation order varies from run to run. The forward pass, backward
prepare and the token pass run the deterministic package's programs.
Over 19 token counts, the geomean speedup against det for the backward
finish is 1.021 on B200 (1.000 to 1.051 per row), 1.054 on GB300 (1.017
to 1.132 per row) and 1.009 on Rubin (0.979 to 1.040 per row). For a
checkpointed training step it is 1.012 on B200 (1.000 to 1.024 per row),
1.021 on GB300 (1.006 to 1.055 per row) and 1.019 on Rubin (1.004 to
1.030 per row). On Rubin, the new backward finish is slightly slower
than det at the smallest token counts: 0.979 at 1024 tokens, and the
rows up to 3584 tokens fall within 0.979 to 1.002. When a concurrent
kernel holds every SM, det waits for it to end at some token counts on
B200 and at every measured token count on Rubin, while the new mode
completes beside it at every measured token count; on GB300 neither mode
waits.

### B200

Latency in microseconds on NVIDIA B200 (sm_100a, 148 SMs, 1000 W), CUDA
13.4, driver 580.82.07, torch 2.14.1+cu130. T is the number of tokens,
and speedup = det latency / new latency. "backward finish" times one
backward-finish call. "2 x fwd + bwd" times one checkpointed training
step (two forwards and the backward). Each sample is one CUDA graph
replay timed with CUDA events, with L2 flushed outside the timed region.
Each value is the median of 12 runs of 16 samples per arm: 6 groups,
each running the arms in the order det, new, new, det or new, det, det,
new, alternating from group to group.

| T | backward finish det us | backward finish new us | speedup det/new
| 2 x fwd + bwd det us | 2 x fwd + bwd new us | speedup det/new |
|---:|---:|---:|---:|---:|---:|---:|
| 1024 | 53.3 | 51.3 | 1.039 | 129.0 | 127.0 | 1.016 |
| 1536 | 67.6 | 65.5 | 1.031 | 161.8 | 159.7 | 1.013 |
| 2048 | 81.9 | 77.9 | 1.051 | 198.6 | 196.6 | 1.010 |
| 2304 | 86.0 | 84.0 | 1.024 | 207.7 | 204.8 | 1.014 |
| 2560 | 102.4 | 102.4 | 1.000 | 237.6 | 237.6 | 1.000 |
| 3072 | 116.7 | 112.6 | 1.036 | 288.8 | 282.7 | 1.022 |
| 3584 | 124.9 | 124.9 | 1.000 | 296.9 | 295.5 | 1.005 |
| 4096 | 139.3 | 133.1 | 1.046 | 326.6 | 321.5 | 1.016 |
| 8192 | 245.8 | 237.6 | 1.034 | 622.6 | 608.3 | 1.024 |
| 14928 | 434.2 | 430.0 | 1.010 | 1113.1 | 1105.9 | 1.006 |
| 15288 | 442.4 | 435.7 | 1.015 | 1141.8 | 1129.5 | 1.011 |
| 15566 | 456.7 | 452.6 | 1.009 | 1161.2 | 1155.1 | 1.005 |
| 15590 | 458.2 | 454.7 | 1.008 | 1159.1 | 1153.0 | 1.005 |
| 16114 | 461.8 | 456.2 | 1.012 | 1184.3 | 1180.7 | 1.003 |
| 16132 | 475.2 | 467.0 | 1.017 | 1199.1 | 1184.2 | 1.013 |
| 16164 | 475.1 | 463.9 | 1.024 | 1200.1 | 1183.2 | 1.014 |
| 16263 | 474.1 | 466.0 | 1.018 | 1205.3 | 1186.8 | 1.016 |
| 32768 | 965.7 | 955.4 | 1.011 | 2382.9 | 2356.2 | 1.011 |
| 65536 | 1964.5 | 1949.7 | 1.008 | 4804.4 | 4726.0 | 1.017 |

geomean speedup over 19 rows: backward finish 1.021, 2 x fwd + bwd 1.012

Latency in microseconds of one backward finish on the same NVIDIA B200
(sm_100a), CUDA 13.4, while a kernel on another CUDA stream spins for
20,000,000 cycles. Each value is the median of 7 samples, and the table
covers 10 of the T values. The column groups are: alone; with a side
kernel of 16 CTAs x 640 threads; and with a side kernel that holds one
CTA on every SM. Under the every-SM hold, the deterministic finish waits
for the side kernel to end (about 9.7 ms) at T = 1536, 2048, 2304, 2560
and 3584. The new mode completes beside it at every T.

| T | alone det us | alone new us | speedup | side 16 CTAs x 640 threads
det us | new us | speedup | side one CTA on every SM det us | new us |
speedup |
|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 1024 | 53.2 | 49.2 | 1.083 | 57.3 | 55.3 | 1.038 | 53.2 | 51.2 | 1.040
|
| 1536 | 65.5 | 63.5 | 1.031 | 75.8 | 73.8 | 1.027 | 9706.5 | 65.6 |
147.965 |
| 2048 | 75.8 | 75.7 | 1.001 | 86.0 | 84.0 | 1.024 | 9716.7 | 77.8 |
124.855 |
| 2304 | 84.0 | 79.9 | 1.051 | 122.9 | 98.3 | 1.250 | 9727.0 | 81.9 |
118.738 |
| 2560 | 102.4 | 98.3 | 1.042 | 118.8 | 118.8 | 1.000 | 9728.0 | 102.4 |
95.000 |
| 3072 | 114.7 | 108.5 | 1.057 | 139.3 | 135.2 | 1.030 | 118.8 | 112.6 |
1.055 |
| 3584 | 124.9 | 122.9 | 1.017 | 141.3 | 139.4 | 1.014 | 9749.5 | 126.9
| 76.801 |
| 4096 | 137.2 | 130.9 | 1.048 | 163.9 | 155.7 | 1.052 | 141.4 | 133.2 |
1.062 |
| 8192 | 243.7 | 235.5 | 1.035 | 297.0 | 290.8 | 1.021 | 251.9 | 243.7 |
1.033 |
| 16263 | 436.2 | 430.1 | 1.014 | 534.5 | 528.4 | 1.012 | 452.6 | 444.4
| 1.018 |

### GB300

Latency in microseconds on NVIDIA GB300 (sm_103a, 152 SMs, 1400 W), CUDA
13.4, driver 580.159.03, torch 2.14.1+cu130. T is the number of tokens,
and speedup = det latency / new latency. "backward finish" times one
backward-finish call. "2 x fwd + bwd" times one checkpointed training
step (two forwards and the backward). Each sample is one CUDA graph
replay timed with CUDA events, with L2 flushed outside the timed region.
Each value is the median of 12 runs of 16 samples per arm: 6 groups,
each running the arms in the order det, new, new, det or new, det, det,
new, alternating from group to group.

| T | backward finish det us | backward finish new us | speedup det/new
| 2 x fwd + bwd det us | 2 x fwd + bwd new us | speedup det/new |
|---:|---:|---:|---:|---:|---:|---:|
| 1024 | 52.9 | 49.3 | 1.073 | 126.1 | 122.0 | 1.033 |
| 1536 | 64.6 | 61.6 | 1.050 | 162.9 | 159.9 | 1.019 |
| 2048 | 81.0 | 73.8 | 1.097 | 197.7 | 189.6 | 1.043 |
| 2304 | 88.2 | 79.0 | 1.117 | 212.1 | 202.6 | 1.047 |
| 2560 | 102.5 | 94.3 | 1.087 | 242.3 | 234.4 | 1.034 |
| 3072 | 109.7 | 103.5 | 1.059 | 269.4 | 261.2 | 1.031 |
| 3584 | 117.9 | 110.8 | 1.064 | 294.0 | 284.8 | 1.032 |
| 4096 | 140.4 | 124.0 | 1.132 | 330.8 | 313.5 | 1.055 |
| 8192 | 234.9 | 222.3 | 1.057 | 576.8 | 568.4 | 1.015 |
| 14928 | 388.2 | 377.4 | 1.029 | 1002.6 | 994.4 | 1.008 |
| 15288 | 399.5 | 386.2 | 1.034 | 1027.2 | 1018.0 | 1.009 |
| 15566 | 402.6 | 390.3 | 1.031 | 1039.5 | 1028.2 | 1.011 |
| 15590 | 403.3 | 390.3 | 1.033 | 1041.5 | 1030.5 | 1.011 |
| 16114 | 410.7 | 399.5 | 1.028 | 1066.1 | 1055.8 | 1.010 |
| 16132 | 416.9 | 403.6 | 1.033 | 1072.3 | 1064.1 | 1.008 |
| 16164 | 416.9 | 404.6 | 1.030 | 1074.3 | 1064.1 | 1.010 |
| 16263 | 416.1 | 402.6 | 1.034 | 1076.4 | 1067.1 | 1.009 |
| 32768 | 806.0 | 781.4 | 1.031 | 2109.6 | 2087.0 | 1.011 |
| 65536 | 1553.5 | 1526.9 | 1.017 | 4118.6 | 4094.8 | 1.006 |

geomean speedup over 19 rows: backward finish 1.054, 2 x fwd + bwd 1.021

Latency in microseconds of one backward finish on the same NVIDIA GB300
(sm_103a), CUDA 13.4, while a kernel on another CUDA stream spins for
20,000,000 cycles. Each value is the median of 7 samples, and the table
covers 10 of the T values. The column groups are: alone; with a side
kernel of 16 CTAs x 640 threads; and with a side kernel that holds one
CTA on every SM. No call of either mode waits for the side kernel. Under
the every-SM hold, the deterministic finish takes 52.4 to 414.8 us and
the new mode 48.3 to 404.6 us.

| T | alone det us | alone new us | speedup | side 16 CTAs x 640 threads
det us | new us | speedup | side one CTA on every SM det us | new us |
speedup |
|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 1024 | 50.3 | 46.2 | 1.089 | 55.4 | 50.3 | 1.101 | 52.4 | 48.3 | 1.085
|
| 1536 | 62.6 | 58.5 | 1.070 | 72.8 | 68.7 | 1.060 | 64.6 | 60.5 | 1.068
|
| 2048 | 78.9 | 69.8 | 1.132 | 96.3 | 87.1 | 1.105 | 81.0 | 70.8 | 1.144
|
| 2304 | 85.1 | 73.9 | 1.152 | 101.5 | 89.2 | 1.138 | 87.1 | 74.9 |
1.164 |
| 2560 | 99.5 | 91.3 | 1.090 | 128.1 | 117.9 | 1.087 | 101.5 | 93.3 |
1.088 |
| 3072 | 107.6 | 99.5 | 1.082 | 138.4 | 128.1 | 1.080 | 109.7 | 101.5 |
1.081 |
| 3584 | 115.8 | 108.6 | 1.066 | 149.6 | 138.3 | 1.082 | 118.9 | 109.7 |
1.084 |
| 4096 | 138.4 | 119.9 | 1.154 | 167.0 | 142.5 | 1.173 | 139.4 | 122.0 |
1.143 |
| 8192 | 230.5 | 216.2 | 1.066 | 298.1 | 285.8 | 1.043 | 232.6 | 222.3 |
1.046 |
| 16263 | 407.7 | 396.4 | 1.028 | 535.6 | 525.4 | 1.019 | 414.8 | 404.6
| 1.025 |

### Rubin

Latency in microseconds on NVIDIA Rubin (sm_107a, 212 SMs, 2300 W), CUDA
13.4, driver 620.62, torch 2.14.1+cu130. T is the number of tokens, and
speedup = det latency / new latency. "backward finish" times one
backward-finish call. "2 x fwd + bwd" times one checkpointed training
step (two forwards and the backward). Each sample is one CUDA graph
replay timed with CUDA events, with L2 flushed outside the timed region.
Each value is the median of 12 runs of 16 samples per arm: 6 groups,
each running the arms in the order det, new, new, det or new, det, det,
new, alternating from group to group.

| T | backward finish det us | backward finish new us | speedup det/new
| 2 x fwd + bwd det us | 2 x fwd + bwd new us | speedup det/new |
|---:|---:|---:|---:|---:|---:|---:|
| 1024 | 37.6 | 38.4 | 0.979 | 92.4 | 89.6 | 1.030 |
| 1536 | 43.5 | 43.7 | 0.994 | 109.1 | 106.4 | 1.026 |
| 2048 | 52.2 | 52.1 | 1.002 | 134.6 | 132.1 | 1.019 |
| 2304 | 53.7 | 54.1 | 0.992 | 139.8 | 136.3 | 1.025 |
| 2560 | 57.6 | 58.2 | 0.990 | 149.8 | 147.6 | 1.015 |
| 3072 | 63.0 | 63.2 | 0.998 | 163.1 | 159.3 | 1.024 |
| 3584 | 79.4 | 79.5 | 0.999 | 194.3 | 190.2 | 1.022 |
| 4096 | 85.8 | 84.8 | 1.012 | 210.7 | 204.9 | 1.028 |
| 8192 | 140.8 | 137.8 | 1.021 | 348.6 | 341.1 | 1.022 |
| 14928 | 232.4 | 230.6 | 1.008 | 587.4 | 580.6 | 1.012 |
| 15288 | 240.6 | 236.3 | 1.018 | 605.6 | 597.0 | 1.014 |
| 15566 | 241.8 | 239.8 | 1.008 | 610.9 | 602.1 | 1.015 |
| 15590 | 241.8 | 240.3 | 1.006 | 611.7 | 602.8 | 1.015 |
| 16114 | 254.2 | 246.6 | 1.031 | 633.1 | 620.2 | 1.021 |
| 16132 | 254.8 | 246.3 | 1.034 | 633.8 | 620.5 | 1.021 |
| 16164 | 253.8 | 245.2 | 1.035 | 634.5 | 622.5 | 1.019 |
| 16263 | 248.8 | 246.9 | 1.008 | 630.7 | 624.2 | 1.010 |
| 32768 | 469.9 | 468.4 | 1.003 | 1192.8 | 1188.4 | 1.004 |
| 65536 | 932.4 | 896.2 | 1.040 | 2354.9 | 2316.3 | 1.017 |

geomean speedup over 19 rows: backward finish 1.009, 2 x fwd + bwd 1.019

Latency in microseconds of one backward finish on the same NVIDIA Rubin
(sm_107a), CUDA 13.4, while a kernel on another CUDA stream spins for
20,000,000 cycles. Each value is the median of 7 samples, and the table
covers 10 of the T values. The column groups are: alone; with a side
kernel of 16 CTAs x 640 threads; and with a side kernel that holds one
CTA on every SM. Under the every-SM hold, the deterministic finish waits
for the side kernel to end (about 7.9 ms; 7874.2 to 8032.1 us) at every
T in the table. The new mode completes beside it at every T, in at most
249.4 us.

| T | alone det us | alone new us | speedup | side 16 CTAs x 640 threads
det us | new us | speedup | side one CTA on every SM det us | new us |
speedup |
|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 1024 | 37.1 | 37.9 | 0.979 | 37.4 | 37.5 | 0.999 | 7874.2 | 38.5 |
204.545 |
| 1536 | 42.5 | 44.1 | 0.964 | 42.1 | 44.0 | 0.956 | 7879.5 | 44.5 |
177.019 |
| 2048 | 51.0 | 50.9 | 1.002 | 53.2 | 53.2 | 0.998 | 7885.5 | 51.6 |
152.868 |
| 2304 | 53.4 | 54.4 | 0.982 | 55.5 | 55.7 | 0.995 | 7887.0 | 55.1 |
143.212 |
| 2560 | 57.5 | 57.1 | 1.008 | 59.3 | 58.8 | 1.007 | 7890.7 | 57.8 |
136.612 |
| 3072 | 62.0 | 63.6 | 0.975 | 63.6 | 64.5 | 0.987 | 7896.1 | 64.8 |
121.913 |
| 3584 | 78.6 | 78.1 | 1.006 | 83.1 | 83.6 | 0.994 | 7900.9 | 80.3 |
98.368 |
| 4096 | 86.1 | 84.3 | 1.022 | 118.3 | 91.3 | 1.296 | 7904.6 | 86.5 |
91.387 |
| 8192 | 137.5 | 137.4 | 1.001 | 197.2 | 154.9 | 1.273 | 7947.4 | 140.3
| 56.651 |
| 16263 | 247.2 | 245.1 | 1.008 | 358.0 | 286.4 | 1.250 | 8032.1 | 249.4
| 32.209 |

Cake ships this mHC training family in only these two modes,
deterministic and non-deterministic, both for BF16 at hidden size 4096
and both with programs for sm_100a, sm_103a and sm_107a.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added experimental Cake mHC training APIs with selectable
deterministic and non-deterministic modes. Deterministic mode is the
default; PyTorch deterministic-algorithm settings trigger a fallback to
deterministic execution.
* Added support for training workflows including forward and backward
passes, autograd, checkpointing, and CUDA graph capture on supported
GPUs.
* Non-deterministic mode may produce small differences in the `dfn`
gradient due to summation order; other listed outputs and gradients
remain bitwise deterministic.
* **Documentation**
* Added guidance on numerical behavior, workspace use, supported modes,
and deterministic fallbacks.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [dd8325c](https://github.com/flashinfer-ai/flashinfer/commit/dd8325c1f547ad202c4e43e36421a5fcbc925bd9)

- **作者**: eigen
- **时间**: 2026-10-31T07:26:59Z
- **提交信息**: refactor(cake_causal_conv1d): deterministic KCP names for the context-parallel causal conv1d entry points (#8055)

This PR delivers Cake's context-parallel (KCP) packed width-4 depthwise
causal conv1d + SiLU with halo exchange under deterministic names. It
covers forward, backward and autograd, for one tensor or for several
tensors of one layer. Only names change, and the generated programs keep
their digests.

The new entry module `flashinfer.cake_causal_conv1d_det_train_kcp`
provides `cake_causal_conv1d_det_kcp`,
`cake_causal_conv1d_det_multi_kcp` and `RecomputeHandleDetKcp`. The
programs stay in `flashinfer.cake_causal_conv1d_det_train_backend`.
Their `kcp` names there are
`cake_causal_conv1d_det_{forward,backward}_kcp`,
`cake_causal_conv1d_det_multi_{forward,backward}_kcp`,
`CakeCausalConv1dDetFunctionKcp` and
`CakeCausalConv1dDetMultiFunctionKcp`. The previous names still point to
the same objects, including in
`flashinfer.cake_causal_conv1d_det_train`. Examples are
`cake_causal_conv1d_kcp`, `cake_causal_conv1d_kcp_multi`,
`KcpRecomputeHandle` and `CakeCausalConv1dKcpFunction`. Kernel libraries
are renamed `cake_causal_conv1d_det_train_<digest>_kcp`. All five are
used only for context parallelism. The supported targets are sm_100a,
sm_103a and sm_107a.

This PR also carries the complete single-rank deterministic rename and
supersedes #8074. The single-rank names are
`flashinfer.cake_causal_conv1d_det_train`, `cake_causal_conv1d_det`,
`CakeCausalConv1dDetFunction` and the deterministic forward/backward and
workspace entry points. All previous names and module paths remain
compatible aliases.

**Single-rank speed.** "Before" is FI main under the previous names;
"after" is this PR. S is the packed token count and C the channel count.
A ratio below 1 means this PR is faster. After/before ranges from 0.9958
to 1.0056, so speed is unchanged within run-to-run noise.

NVIDIA B200 (sm_100a), CUDA 13.4, torch 2.14.1+cu130

| S | C | pass | before (ms) | after (ms) | after/before |
|---:|---:|---|---:|---:|---:|
| 239718 | 512 | fwd | 0.08018 | 0.08020 | 1.0002 |
| 239718 | 512 | bwd | 0.14197 | 0.14194 | 0.9998 |
| 239718 | 512 | fwd+bwd | 0.22162 | 0.22159 | 0.9999 |
| 245028 | 512 | fwd | 0.08181 | 0.08179 | 0.9997 |
| 245028 | 512 | bwd | 0.14326 | 0.14326 | 1.0000 |
| 245028 | 512 | fwd+bwd | 0.22449 | 0.22449 | 1.0000 |
| 249866 | 512 | fwd | 0.08324 | 0.08326 | 1.0002 |
| 249866 | 512 | bwd | 0.14757 | 0.14752 | 0.9997 |
| 249866 | 512 | fwd+bwd | 0.23061 | 0.23074 | 1.0006 |
| 250340 | 512 | fwd | 0.08350 | 0.08351 | 1.0001 |
| 250340 | 512 | bwd | 0.14655 | 0.14653 | 0.9999 |
| 250340 | 512 | fwd+bwd | 0.22917 | 0.22920 | 1.0001 |
| 258574 | 512 | fwd | 0.08592 | 0.08590 | 0.9998 |
| 258574 | 512 | bwd | 0.14991 | 0.14990 | 0.9999 |
| 258574 | 512 | fwd+bwd | 0.23558 | 0.23560 | 1.0001 |
| 259042 | 512 | fwd | 0.08604 | 0.08604 | 0.9999 |
| 259042 | 512 | bwd | 0.15030 | 0.15032 | 1.0001 |
| 259042 | 512 | fwd+bwd | 0.23580 | 0.23580 | 1.0000 |
| 259584 | 512 | fwd | 0.08620 | 0.08620 | 1.0000 |
| 259584 | 512 | bwd | 0.15209 | 0.15206 | 0.9998 |
| 259584 | 512 | fwd+bwd | 0.23812 | 0.23812 | 1.0000 |
| 261393 | 512 | fwd | 0.08657 | 0.08659 | 1.0002 |
| 261393 | 512 | bwd | 0.14997 | 0.15000 | 1.0002 |
| 261393 | 512 | fwd+bwd | 0.23688 | 0.23697 | 1.0004 |
| 250340 | 128 | fwd | 0.02943 | 0.02942 | 0.9996 |
| 250340 | 128 | bwd | 0.05116 | 0.05121 | 1.0009 |
| 250340 | 128 | fwd+bwd | 0.08323 | 0.08351 | 1.0034 |
| 250340 | 256 | fwd | 0.04748 | 0.04748 | 1.0002 |
| 250340 | 256 | bwd | 0.08388 | 0.08386 | 0.9998 |
| 250340 | 256 | fwd+bwd | 0.13305 | 0.13380 | 1.0056 |
| 250340 | 1024 | fwd | 0.16458 | 0.16461 | 1.0002 |
| 250340 | 1024 | bwd | 0.26882 | 0.26887 | 1.0002 |
| 250340 | 1024 | fwd+bwd | 0.43340 | 0.43309 | 0.9993 |
| 250340 | 2048 | fwd | 0.31720 | 0.31786 | 1.0021 |
| 250340 | 2048 | bwd | 0.52717 | 0.52721 | 1.0001 |
| 250340 | 2048 | fwd+bwd | 0.89177 | 0.88991 | 0.9979 |
| 250340 | 4096 | fwd | 0.64286 | 0.64296 | 1.0002 |
| 250340 | 4096 | bwd | 1.09285 | 1.09101 | 0.9983 |
| 250340 | 4096 | fwd+bwd | 1.83452 | 1.82674 | 0.9958 |
| 250340 | 8192 | fwd | 1.33790 | 1.34240 | 1.0034 |
| 250340 | 8192 | bwd | 2.27470 | 2.27473 | 1.0000 |
| 250340 | 8192 | fwd+bwd | 3.75009 | 3.75094 | 1.0002 |
| 250340 | 1280 | fwd | 0.19944 | 0.19946 | 1.0001 |
| 250340 | 1280 | bwd | 0.34438 | 0.34487 | 1.0014 |
| 250340 | 1280 | fwd+bwd | 0.55374 | 0.55403 | 1.0005 |
| 262144 | 1280 | fwd | 0.20840 | 0.20840 | 1.0000 |
| 262144 | 1280 | bwd | 0.36126 | 0.36146 | 1.0006 |
| 262144 | 1280 | fwd+bwd | 0.58010 | 0.58030 | 1.0004 |
| 250340 | 1536 | fwd | 0.23050 | 0.23051 | 1.0000 |
| 250340 | 1536 | bwd | 0.40193 | 0.40197 | 1.0001 |
| 250340 | 1536 | fwd+bwd | 0.65502 | 0.65504 | 1.0000 |
| 262144 | 1536 | fwd | 0.24097 | 0.24098 | 1.0000 |
| 262144 | 1536 | bwd | 0.42038 | 0.42043 | 1.0001 |
| 262144 | 1536 | fwd+bwd | 0.68282 | 0.68423 | 1.0021 |
| 250340 | 2560 | fwd | 0.37849 | 0.37856 | 1.0002 |
| 250340 | 2560 | bwd | 0.66064 | 0.66168 | 1.0016 |
| 250340 | 2560 | fwd+bwd | 1.11339 | 1.11441 | 1.0009 |
| 250340 | 1344 | fwd | 0.21015 | 0.21014 | 0.9999 |
| 250340 | 1344 | bwd | 0.40603 | 0.40602 | 1.0000 |
| 250340 | 1344 | fwd+bwd | 0.62640 | 0.62695 | 1.0009 |
| 250340 | 1160 | fwd | 0.19931 | 0.19930 | 0.9999 |
| 250340 | 1160 | bwd | 0.36618 | 0.36648 | 1.0008 |
| 250340 | 1160 | fwd+bwd | 0.56317 | 0.56316 | 1.0000 |
| 262144 | 1160 | fwd | 0.20820 | 0.20819 | 1.0000 |
| 262144 | 1160 | bwd | 0.37148 | 0.37186 | 1.0010 |
| 262144 | 1160 | fwd+bwd | 0.58721 | 0.58780 | 1.0010 |

Each value is the mean of two independent package copies; each copy's
value is the median of 48 interleaved A/B measurements (3 fresh
processes x 8 buffer placements x 2 pairings), each measurement the
median of 3 x 64 timed calls (full call span, cold L2), all on one GPU;
after/before = after (ms) / before (ms).

**Context-parallel (KCP) speed: NVIDIA GB200 (sm_100a), 4 GPUs on one
node, CUDA 13.0 runtime (torch 2.14.1).** "Before" is the same KCP path
under the previous names on the parent branch. "After" is this PR. The
ratio is after/before, so a value below 1 means this PR is faster. Each
iteration of `benchmarks/bench_cake_kda_train_kcp.py` (torchrun, one
process per rank) times the KCP causal conv1d and then the KCP KDA step,
forward and backward, with CUDA events. The slowest rank's time counts.
The KDA programs are the same on both sides. The workload is a packed
seqlen of 65536 with 3 documents (15945, 21845 and 27746 tokens), 16
heads and 4096 channels. Each value is the median over interleaved runs
per side, in the order base, branch, branch, base. Each run's figure is
the bench's median over 3 groups of 8 timed iterations.

| CP | layout | runs per side | before (ms) | after (ms) | after/before
|
|---|---|---|---|---|---|
| 2 | `contiguous` | 4 | 4.4644 | 4.4728 | 1.0019 |
| 2 | `zigzag` | 4 | 4.5155 | 4.5170 | 1.0003 |
| 2 | `zigzag_per_document` | 4 | 4.6157 | 4.6383 | 1.0049 |
| 4 | `contiguous` | 10 | 3.3509 | 3.3424 | 0.9975 |
| 4 | `zigzag` | 4 | 3.4003 | 3.3931 | 0.9979 |
| 4 | `zigzag_per_document` | 4 | 3.4441 | 3.4374 | 0.9981 |

After/before ranges from 0.9975 to 1.0049, so speed is unchanged within
run-to-run noise.

This combined PR delivers both single-rank and KCP deterministic names,
including the KCP multi-tensor form, for sm_100a, sm_103a and sm_107a.



<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added deterministic causal-convolution training APIs for forward,
backward, and autograd, with optional bias and configurable gradient
precision.
* Added context-parallel APIs for single- and multi-tensor workloads,
with graph replay and checkpoint recomputation support.
* Added support for empty inputs and documented the deterministic
training and context-parallel APIs.

* **Compatibility**
* Existing training API names remain available as aliases to the
deterministic APIs, including context-parallel entry points.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [aa9932c](https://github.com/flashinfer-ai/flashinfer/commit/aa9932c869bbbc6450a73ef85614e431599d79f2)

- **作者**: eigen
- **时间**: 2026-10-31T07:21:40Z
- **提交信息**: feat(cake_lm_head_det_loss): det names for the chunked LM-head + loss backend (#8059)

The chunked LM-head + loss backend is deterministic: for fixed inputs,
hardware, chunk plan and initial accumulation buffers, its forward and
backward give bitwise-identical results run to run. This PR gives it
`det` names:

- the package `flashinfer.experimental.cake_lm_head_loss` becomes
`flashinfer.experimental.cake_lm_head_det_loss`; its generated sources,
kernels and libraries are named `cake_lm_head_det_loss_*`;
- the public entries become
`chunked_lm_head_det_{loss,logprob,preload,support_logprob,support_kl}`,
and the backend's functions and classes get the same `det` names.

Compatibility: every previous name stays as an alias of the same object,
including `load_cake_lm_head_loss_module` in `cake_jit`, `cake_backend`
and `cake_backend_opt_in`. The previous package path stays as a shim
package whose modules are the `det` package's modules. The
`FLASHINFER_CAKE_LM_HEAD_LOSS_*` environment variables keep their names.

Performance is unchanged: the generated programs differ from main only
in their names, and their SASS is identical to main's on sm_100a and
sm_103a.

The backend has one data type (BF16) and covers the CE and policy
losses, the log-probability entry and the support-set log-probability
and KL entries; it ships on sm_100a and sm_103a.

Merge after #8054, which carries the pre-commit exclusions for both
package paths, and after the companion internal export change; a final
build.json-only commit will record the published generator revision
before merge.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added deterministic, chunked language-model head loss and
log-probability operations, along with candidate-restricted
log-probabilities and KL calculations.
* Added fast and memory-budgeted backend options, including valid-row
controls and workspace reporting.
* **Compatibility**
* Preserved legacy API and package paths as aliases to the deterministic
entry points.
* **Documentation**
* Clarified determinism guarantees and updated guidance for the APIs,
naming conventions, and tuning options.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [95c1a09](https://github.com/flashinfer-ai/flashinfer/commit/95c1a09536515c6e0ffe9c5bc930c63d83cb5330)

- **作者**: eigen
- **时间**: 2026-10-31T07:03:05Z
- **提交信息**: perf(cake_muse_spark_norm, cake_tp_moe_finalize_rmsnorm): retune the gated residual RMSNorm routes on GB300, the next-RMSNorm routes on B200 and R200, and the MoE finalize token-owner windows on B200, GB300 and R200 (#8094)

This PR updates the Cake kernel package in FlashInfer. The package ships
these kernels:
- Gated residual RMSNorm: mode 0 without a weight and mode 1 with a
weight, each with plain and PDL routes.
- Gated residual next-RMSNorm: alpha tensor + post weight, alpha scalar
+ post weight, and alpha scalar without a post weight.
- RMSNorm + sigmoid gate: plain and PDL routes.
- Tensor-parallel MoE finalize RMSNorm: TP2, TP4 and TP8.

This PR changes:
- The gated residual RMSNorm routes on GB300 (`sm_103a`).
- The next-RMSNorm routes on B200 (`sm_100a`) and R200 (`sm_107a`).
- The MoE finalize token-owner windows on B200 TP8, GB300 TP4 and R200
TP4.

The speedup baseline is the previous Cake package already on FlashInfer
main. In the descriptions and tables below, M is the number of rows and
T is the number of tokens.

On GB300 (`sm_103a`), all four gated residual RMSNorm routes take
different programs above a row threshold (Tables 1-4):
- Plain routes: mode 0 and mode 1 change at M >= 1024. Mode 0 takes a
second new program at M >= 8193.
- PDL routes: mode 1 changes at M >= 513. Mode 0 changes at M = 513-1536
and M >= 2049, and its rows 1537-2048 do not change.

The changed rows measure 1.0174-1.0334 (mode 0) and 1.0112-1.0465 (mode
1) on the plain routes, and 1.0250-1.1204 (mode 0) and 1.0358-1.1932
(mode 1) on the PDL routes.

On B200 (`sm_100a`), two next-RMSNorm windows change. The alpha tensor +
post weight route takes a different program at M = 1281-2816, and the
alpha scalar route without a post weight takes a different program at M
= 65-104. The alpha tensor row M = 2048 measures 1.0172 (Table 5). Table
6 has no row inside M = 65-104, so it shows unchanged rows only.

The B200 TP8 MoE finalize moves T = 145-2304 off the previous multicast
token-owner program to two new token-owner programs: one for T = 448-576
and one for the rest of the window. T >= 2305 keeps the multicast
program. The changed rows measure 1.0133-1.2369 (Table 7).

The GB300 TP4 MoE finalize moves T = 153-16384 off the multicast
token-owner program to three new token-owner programs: one for T =
153-384, one for T = 448-576, and one for T = 385-447 and 577-16384. T
>= 16385 keeps the multicast program. The changed rows measure
1.0081-1.1933 (Table 8).

**Table 1.** Gated residual RMSNorm, mode 0 (no weight), plain route,
NVIDIA GB300 (`sm_103a`), CUDA 13.0, driver 580.167.08. Each kernel is
timed alone: CUPTI kernel-active median, cold L2 (memset flush).
Previous = the previous Cake package on FlashInfer main; this PR = this
PR's package. Latency in microseconds, median over 4 interleaved
sessions; speedup = previous / this PR ("same kernel": both sides run
the identical program).

| M (rows) | previous us | this PR us | speedup |
|---|---|---|---|
| 1 | 2.100 | 2.102 | same kernel |
| 2 | 2.074 | 2.073 | same kernel |
| 4 | 2.112 | 2.112 | same kernel |
| 8 | 2.142 | 2.142 | same kernel |
| 16 | 2.220 | 2.223 | same kernel |
| 32 | 2.505 | 2.506 | same kernel |
| 64 | 3.056 | 3.055 | same kernel |
| 128 | 4.307 | 4.307 | same kernel |
| 256 | 5.207 | 5.205 | same kernel |
| 1024 | 14.936 | 14.464 | 1.0326 |
| 2048 | 27.008 | 26.152 | 1.0327 |
| 4096 | 51.212 | 49.556 | 1.0334 |
| 8192 | 98.604 | 96.788 | 1.0188 |
| 16384 | 191.608 | 188.324 | 1.0174 |

**Table 2.** Gated residual RMSNorm, mode 0 (no weight), PDL route,
NVIDIA GB300 (`sm_103a`), CUDA 13.0, driver 580.167.08. Timed as CUDA
graph + PDL: 32 launches per graph, 20 replays, per-launch average.
Previous = the previous Cake package on FlashInfer main; this PR = this
PR's package. Latency in microseconds, median over 4 interleaved
sessions; speedup = previous / this PR ("same kernel": both sides run
the identical program).

| M (rows) | previous us | this PR us | speedup |
|---|---|---|---|
| 1 | 1.164 | 1.162 | same kernel |
| 2 | 1.152 | 1.095 | same kernel |
| 4 | 1.095 | 1.095 | same kernel |
| 8 | 1.158 | 1.094 | same kernel |
| 16 | 1.157 | 1.157 | same kernel |
| 32 | 1.349 | 1.349 | same kernel |
| 64 | 1.728 | 1.730 | same kernel |
| 128 | 2.183 | 2.181 | same kernel |
| 256 | 3.203 | 3.204 | same kernel |
| 1024 | 11.261 | 10.051 | 1.1204 |
| 2048 | 22.530 | 22.525 | same kernel |
| 4096 | 50.541 | 48.898 | 1.0336 |
| 8192 | 98.183 | 95.271 | 1.0306 |
| 16384 | 192.924 | 188.220 | 1.0250 |

**Table 3.** Gated residual RMSNorm, mode 1 (weight), plain route,
NVIDIA GB300 (`sm_103a`), CUDA 13.0, driver 580.167.08. Each kernel is
timed alone: CUPTI kernel-active median, cold L2 (memset flush).
Previous = the previous Cake package on FlashInfer main; this PR = this
PR's package. Latency in microseconds, median over 4 interleaved
sessions; speedup = previous / this PR ("same kernel": both sides run
the identical program).

| M (rows) | previous us | this PR us | speedup |
|---|---|---|---|
| 1 | 2.882 | 2.882 | same kernel |
| 2 | 2.862 | 2.863 | same kernel |
| 4 | 3.089 | 3.082 | same kernel |
| 8 | 3.079 | 3.075 | same kernel |
| 16 | 3.277 | 3.280 | same kernel |
| 32 | 3.010 | 3.010 | same kernel |
| 64 | 3.575 | 3.573 | same kernel |
| 128 | 4.417 | 4.417 | same kernel |
| 256 | 5.177 | 5.177 | same kernel |
| 1024 | 15.056 | 14.632 | 1.0290 |
| 2048 | 27.268 | 26.336 | 1.0354 |
| 4096 | 51.948 | 49.640 | 1.0465 |
| 8192 | 98.640 | 96.788 | 1.0191 |
| 16384 | 193.200 | 191.068 | 1.0112 |

**Table 4.** Gated residual RMSNorm, mode 1 (weight), PDL route, NVIDIA
GB300 (`sm_103a`), CUDA 13.0, driver 580.167.08. Timed as CUDA graph +
PDL: 32 launches per graph, 20 replays, per-launch average. Previous =
the previous Cake package on FlashInfer main; this PR = this PR's
package. Latency in microseconds, median over 4 interleaved sessions;
speedup = previous / this PR ("same kernel": both sides run the
identical program).

| M (rows) | previous us | this PR us | speedup |
|---|---|---|---|
| 1 | 1.223 | 1.224 | same kernel |
| 2 | 1.224 | 1.224 | same kernel |
| 4 | 1.285 | 1.285 | same kernel |
| 8 | 1.287 | 1.286 | same kernel |
| 16 | 1.413 | 1.413 | same kernel |
| 32 | 1.543 | 1.542 | same kernel |
| 64 | 1.955 | 1.962 | same kernel |
| 128 | 2.247 | 2.246 | same kernel |
| 256 | 3.264 | 3.265 | same kernel |
| 1024 | 11.921 | 9.991 | 1.1932 |
| 2048 | 24.267 | 22.429 | 1.0819 |
| 4096 | 50.919 | 48.851 | 1.0423 |
| 8192 | 98.737 | 95.224 | 1.0369 |
| 16384 | 194.361 | 187.637 | 1.0358 |

**Table 5.** Gated residual next-RMSNorm, alpha tensor + post weight,
NVIDIA B200 (`sm_100a`), CUDA 13.0, driver 580.82.07. Each kernel is
timed alone: CUPTI kernel-active median, cold L2 (memset flush).
Previous = the previous Cake package on FlashInfer main; this PR = this
PR's package. Latency in microseconds, median over 4 interleaved
sessions; speedup = previous / this PR ("same kernel": both sides run
the identical program).

| M (rows) | previous us | this PR us | speedup |
|---|---|---|---|
| 1 | 2.882 | 2.882 | same kernel |
| 8 | 2.905 | 2.901 | same kernel |
| 16 | 3.063 | 3.059 | same kernel |
| 32 | 3.363 | 3.362 | same kernel |
| 64 | 3.957 | 3.961 | same kernel |
| 128 | 4.890 | 4.889 | same kernel |
| 256 | 7.279 | 7.280 | same kernel |
| 1024 | 17.936 | 17.964 | same kernel |
| 2048 | 34.068 | 33.492 | 1.0172 |
| 4096 | 64.028 | 64.040 | same kernel |
| 8192 | 123.579 | 123.507 | same kernel |
| 16384 | 240.418 | 240.358 | same kernel |

**Table 6.** Gated residual next-RMSNorm, alpha scalar, no post weight,
NVIDIA B200 (`sm_100a`), CUDA 13.0, driver 580.82.07. Each kernel is
timed alone: CUPTI kernel-active median, cold L2 (memset flush).
Previous = the previous Cake package on FlashInfer main; this PR = this
PR's package. Latency in microseconds, median over 4 interleaved
sessions; speedup = previous / this PR ("same kernel": both sides run
the identical program).

| M (rows) | previous us | this PR us | speedup |
|---|---|---|---|
| 1 | 2.776 | 2.778 | same kernel |
| 8 | 2.829 | 2.830 | same kernel |
| 16 | 3.000 | 3.004 | same kernel |
| 32 | 3.308 | 3.309 | same kernel |
| 64 | 3.842 | 3.844 | same kernel |
| 128 | 4.893 | 4.892 | same kernel |
| 256 | 6.799 | 6.797 | same kernel |
| 1024 | 17.984 | 17.964 | same kernel |
| 2048 | 32.944 | 32.972 | same kernel |
| 4096 | 62.080 | 62.084 | same kernel |
| 8192 | 121.987 | 121.995 | same kernel |
| 16384 | 241.546 | 241.490 | same kernel |

**Table 7.** MoE finalize RMSNorm, TP8, NVIDIA B200 (`sm_100a`), CUDA
13.0, driver 580.82.07. Timed through the FlashInfer API: CUPTI
kernel-active median per rank, max over ranks, cold L2. Previous = the
previous Cake package on FlashInfer main; this PR = this PR's package.
Latency in microseconds, median over 4 interleaved sessions; speedup =
previous / this PR ("same kernel": both sides run the identical
program).

| T (tokens) | previous us | this PR us | speedup |
|---|---|---|---|
| 1 | 9.516 | 9.804 | same kernel |
| 4 | 11.188 | 11.472 | same kernel |
| 7 | 11.724 | 11.992 | same kernel |
| 8 | 13.628 | 13.864 | same kernel |
| 9 | 14.020 | 13.952 | same kernel |
| 16 | 14.440 | 14.676 | same kernel |
| 32 | 16.100 | 16.304 | same kernel |
| 33 | 17.668 | 17.940 | same kernel |
| 64 | 20.552 | 20.768 | same kernel |
| 72 | 21.352 | 21.616 | same kernel |
| 73 | 21.444 | 21.716 | same kernel |
| 128 | 26.564 | 26.520 | same kernel |
| 144 | 27.608 | 27.872 | same kernel |
| 145 | 38.983 | 31.516 | 1.2369 |
| 152 | 39.180 | 35.388 | 1.1072 |
| 153 | 39.256 | 35.408 | 1.1087 |
| 256 | 49.859 | 43.664 | 1.1419 |
| 512 | 76.955 | 67.916 | 1.1331 |
| 1024 | 124.027 | 122.399 | 1.0133 |
| 2048 | 226.126 | 220.342 | 1.0263 |
| 4096 | 427.033 | 427.077 | same kernel |
| 8192 | 823.259 | 823.307 | same kernel |

**Table 8.** MoE finalize RMSNorm, TP4, NVIDIA GB300 (`sm_103a`), CUDA
13.0, driver 580.167.08. Timed through the FlashInfer API: CUPTI
kernel-active median per rank, max over ranks, cold L2. Previous = the
previous Cake package on FlashInfer main; this PR = this PR's package.
Latency in microseconds, median over 4 interleaved sessions; speedup =
previous / this PR ("same kernel": both sides run the identical
program).

| T (tokens) | previous us | this PR us | speedup |
|---|---|---|---|
| 1 | 8.244 | 8.236 | same kernel |
| 4 | 8.588 | 8.608 | same kernel |
| 8 | 9.788 | 9.792 | same kernel |
| 15 | 10.452 | 10.464 | same kernel |
| 16 | 10.672 | 10.688 | same kernel |
| 17 | 10.736 | 10.760 | same kernel |
| 31 | 11.948 | 11.960 | same kernel |
| 32 | 11.992 | 12.000 | same kernel |
| 33 | 12.184 | 12.188 | same kernel |
| 48 | 13.948 | 13.932 | same kernel |
| 49 | 14.004 | 14.036 | same kernel |
| 64 | 15.376 | 15.372 | same kernel |
| 128 | 20.688 | 20.708 | same kernel |
| 148 | 22.112 | 22.116 | same kernel |
| 152 | 22.544 | 22.552 | same kernel |
| 153 | 28.392 | 23.792 | 1.1933 |
| 256 | 35.580 | 31.388 | 1.1336 |
| 512 | 59.064 | 52.524 | 1.1245 |
| 1024 | 97.980 | 95.920 | 1.0215 |
| 2048 | 186.472 | 182.972 | 1.0191 |
| 4096 | 353.828 | 349.804 | 1.0115 |
| 8192 | 689.936 | 684.424 | 1.0081 |

On R200 (`sm_107a`), the next-RMSNorm alpha tensor + post weight route
takes a different program at M = 928-1280. The alpha scalar route
without a post weight takes a different program at M >= 3072. The
changed rows measure 1.0525 for alpha tensor at M = 1024 (Table 9) and
1.0259-1.0389 for alpha scalar at M = 4096-16384 (Table 10).

**Table 9.** Gated residual next-RMSNorm, alpha tensor + post weight,
NVIDIA R200 (`sm_107a`, 216 SMs), CUDA 13.0, driver 615.71.10. Each
kernel is timed alone: CUPTI kernel-active median, cold L2 (memset
flush). Previous = the previous Cake package on FlashInfer main; this PR
= this PR's package. Latency in microseconds, median over 3 interleaved
sessions; speedup = previous / this PR ("same kernel": both sides run
the identical program).

| M (rows) | previous us | this PR us | speedup |
|---|---|---|---|
| 1 | 2.592 | 2.592 | same kernel |
| 8 | 2.560 | 2.560 | same kernel |
| 16 | 2.656 | 2.656 | same kernel |
| 32 | 2.784 | 2.792 | same kernel |
| 64 | 3.136 | 3.136 | same kernel |
| 128 | 3.808 | 3.808 | same kernel |
| 256 | 5.152 | 5.152 | same kernel |
| 1024 | 12.352 | 11.736 | 1.0525 |
| 2048 | 22.064 | 22.016 | same kernel |
| 4096 | 41.648 | 41.608 | same kernel |
| 8192 | 82.176 | 82.136 | same kernel |
| 16384 | 162.383 | 162.296 | same kernel |

**Table 10.** Gated residual next-RMSNorm, alpha scalar, no post weight,
NVIDIA R200 (`sm_107a`, 216 SMs), CUDA 13.0, driver 615.71.10. Each
kernel is timed alone: CUPTI kernel-active median, cold L2 (memset
flush). Previous = the previous Cake package on FlashInfer main; this PR
= this PR's package. Latency in microseconds, median over 3 interleaved
sessions; speedup = previous / this PR ("same kernel": both sides run
the identical program).

| M (rows) | previous us | this PR us | speedup |
|---|---|---|---|
| 1 | 2.464 | 2.464 | same kernel |
| 8 | 2.512 | 2.496 | same kernel |
| 16 | 2.624 | 2.624 | same kernel |
| 32 | 2.736 | 2.736 | same kernel |
| 64 | 3.104 | 3.104 | same kernel |
| 128 | 3.744 | 3.744 | same kernel |
| 256 | 5.088 | 5.088 | same kernel |
| 1024 | 11.880 | 11.864 | same kernel |
| 2048 | 22.600 | 22.600 | same kernel |
| 4096 | 42.816 | 41.736 | 1.0259 |
| 8192 | 85.528 | 82.328 | 1.0389 |
| 16384 | 167.656 | 162.408 | 1.0323 |

The R200 TP4 MoE finalize moves T = 213-2048 off the multicast
token-owner program to two new token-owner programs: one for T =
213-1024 and one for T = 1025-2048. T >= 2049 keeps the multicast
program.

The changed rows measure 1.0323-1.1853 (Table 11).

**Table 11.** MoE finalize RMSNorm, TP4, NVIDIA R200 (`sm_107a`, 212
SMs), CUDA 13.0, driver 620.62. Timed through the FlashInfer API: CUPTI
kernel-active median per rank, max over ranks, cold L2. Previous = the
previous Cake package on FlashInfer main; this PR = this PR's package.
Latency in microseconds, median over 3 interleaved sessions; speedup =
previous / this PR ("same kernel": both sides run the identical
program).

| T (tokens) | previous us | this PR us | speedup |
|---|---|---|---|
| 1 | 8.384 | 8.360 | same kernel |
| 4 | 9.024 | 9.008 | same kernel |
| 8 | 9.456 | 9.440 | same kernel |
| 15 | 10.976 | 10.944 | same kernel |
| 16 | 11.040 | 11.040 | same kernel |
| 17 | 11.040 | 11.040 | same kernel |
| 31 | 12.016 | 12.008 | same kernel |
| 32 | 12.008 | 12.032 | same kernel |
| 33 | 12.112 | 12.096 | same kernel |
| 48 | 13.040 | 13.040 | same kernel |
| 49 | 13.184 | 13.184 | same kernel |
| 64 | 13.872 | 13.888 | same kernel |
| 128 | 17.152 | 17.168 | same kernel |
| 148 | 18.088 | 18.112 | same kernel |
| 152 | 18.304 | 18.304 | same kernel |
| 153 | 18.352 | 18.336 | same kernel |
| 256 | 28.968 | 24.440 | 1.1853 |
| 512 | 44.921 | 42.904 | 1.0470 |
| 1024 | 73.353 | 66.521 | 1.1027 |
| 2048 | 125.905 | 121.961 | 1.0323 |
| 4096 | 229.642 | 229.306 | same kernel |
| 8192 | 442.379 | 442.204 | same kernel |

The other Cake variants ship unchanged: the RMSNorm + sigmoid gate
(plain and PDL), the next-RMSNorm alpha scalar + post weight route and
the TP2 MoE finalize. The norm kernels ship on `sm_100a`, `sm_103a` and
`sm_107a`, and the MoE finalize RMSNorm ships TP2 on `sm_100a` and
`sm_103a`, TP4 on `sm_103a` and `sm_107a`, and TP8 on `sm_100a`.

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-11-01
**监控日期**: 2026-10-31
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4765
- **最后更新**: 2026-10-31T20:10:36Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-11-01
**监控日期**: 2026-10-31
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34845
- **最后更新**: 2026-10-31T19:36:48Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-11-01
**监控日期**: 2026-10-31
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


**报告日期**: 2026-11-01
**监控日期**: 2026-10-31
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13332
- **最后更新**: 2026-10-31T16:25:34Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-11-01
**监控日期**: 2026-10-31
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 38328
- **最后更新**: 2026-11-01T00:41:53Z

## 提交统计

- **昨日提交总数**: 43
- **提交者数量**: 21
- **主要提交者**: Mick, metamergebot, Ke Bao

## AI分析总结

# SGLang 昨日提交分析（43 条记录）

## 1. 主要更新类型分布

- **性能优化（Perf）**：约 14 条，占比最高，集中在扩散模型、MoE、采样内核
- **Bug 修复（Fix）**：约 16 条，涉及 disaggregation、hicache、diffusion、rust-server 等
- **功能新增（Feat）**：约 6 条，涵盖 unified-memory、rust-server、新模型支持
- **重构（Refactor）**：3 条，全部聚焦 memory-pool
- **CI/文档**：约 6 条，包括 AMD/NPU 测试管线和 cookbook 更新

## 2. 关键变更点与项目方向的关系

- **PD 分离（Prefill-Decode Disaggregation）持续加固**：多条修复围绕解耦传输时序（延迟发送目标、忽略迟到的 STAGING_REQ、辅助缓冲长度注册），表明该架构已进入生产级打磨阶段，正从"能跑"转向"跑稳"。
- **扩散模型（Diffusion）成为新战场**：MiniMax-H3、Pika-H3-Flex、LTX-2.5 等模型的 ROCm 优化与功能支持密集出现，延续 README 所述"多模态模型快速推理"的目标，把 LLM 推理的工程能力向视频/图像生成迁移。
- **分层缓存（hicache）深化**：MXFP8 KV 以 payload+scales 形式存入 L3、保护字节的页缓存计费、sidecar 修复，支撑长上下文与多模态 KV 的高效管理。
- **统一内存管理**：Full 与 SWA KV 共享单一 LRU 序列（joint_lru），以及 DeepSeek V4 设备池的 buffer-info 描述，为混合注意力模型提供一致的显存治理。
- **Rust 服务端成熟**：abort 全 rank 广播、监听器映射发布、abort 语义对齐 Python，说明 Rust 化路径在补齐控制面语义。

## 3. 对项目的影响和潜在意义

- 生产稳定性显著提升：PD 分离与请求中止的竞态修复减少了分布式部署中的悬挂请求风险。
- 可观测性增强：TTFT 阶段分解写入响应 meta_info，让延迟瓶颈可定位，利于大规模服务调优。
- 硬件覆盖面扩大：AMD gfx950/MI355X、NPU、Blackwell（SM100）均有专门优化，契合 SGLang 作为跨平台推理引擎的定位。
- AI 辅助开发常态化：大量提交由 Claude 系列与 metamergebot 联合署名，反映项目已将 LLM 代理纳入核心开发流程。

## 4. 值得关注的技术点

- **CPU 填充内核替换小元数据写入**（PR #47550）：用 fill kernel 降低元数据同步开销，是 GPU-CPU 交互热点的典型优化。
- **GPU BLAKE3 加速 cosmos3 条件哈希**：将哈希卸载到 GPU，思路新颖，适合批量条件编码场景。
- **Cake softmax 启用于 SM100**：NVIDIA 新架构采样路径的原生适配。
- **Ulysses attention 按 head group 流水化至三个 wave**：通过通信-计算重叠压缩扩散模型注意力的 RCCL 交换延迟。
- **Qwen3 融合 QK-norm/RoPE 内核在 decode 复用**：减少解码路径的内核启动与中间读写。
- **Tile-sharding gloo 测试改用 file store rendezvous**：典型的 CI 确定性修复，值得其他分布式项目借鉴。

## 5. 对项目发展的影响

结合 README 定位——"LLM 与多模态模型的快速推理"——本次提交批次显示 SGLang 正沿三条主线推进：一是把 PD 分离、hicache 等分布式基础设施从功能验证推向生产可靠；二是将推理优化能力系统性复制到扩散/视频生成模型，开辟第二增长曲线；三是通过 unified-memory、buffer-info 描述等重构为 DeepSeek V4、多模态混合注意力模型铺路。整体而言，项目处于高速迭代期，工程成熟度与生态广度同步扩展，对追求高性能多模态服务的团队而言，其技术栈正变得愈发完整和值得依赖。

## 详细提交记录

### [fc32cbf](https://github.com/sgl-project/sglang/commit/fc32cbff6983c7573f4b60eab8b44815668130a0)

- **作者**: Yongji Wu
- **时间**: 2026-10-31T23:13:12Z
- **提交信息**: [Fix] disaggregation: Send decode transfer destinations to prefill only after the in-flight forward (#46373)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: Lianmin Zheng <lianminzheng@gmail.com>

### [3908210](https://github.com/sgl-project/sglang/commit/39082103118a35dce2783facaddf6986c40a495b)

- **作者**: Jeff D. Chen
- **时间**: 2026-10-31T22:59:38Z
- **提交信息**: [Perf] kimi-k3: Allow residual bank shards with NCCL (#47452)

Co-authored-by: Jeff D. Chen <12482210+Codoge@users.noreply.github.com>

### [1813806](https://github.com/sgl-project/sglang/commit/181380682b50f4606d1a09df3cbbbfc21de931e3)

- **作者**: metamergebot
- **时间**: 2026-10-31T20:41:58Z
- **提交信息**: [Fix] hicache: Withhold only protected bytes from page-cache credit (#47557)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: Yavor Ivanov <8558655+YavorGIvanov@users.noreply.github.com>
Co-authored-by: Zhiqiang Xie <22819949+xiezhq-hermann@users.noreply.github.com>

### [bd1f559](https://github.com/sgl-project/sglang/commit/bd1f5596f1d7d903ff4d5e480167309207520046)

- **作者**: Lee Nau
- **时间**: 2026-10-31T20:21:11Z
- **提交信息**: [CI] tests: Rendezvous the tile-sharding gloo test through a file store (#47551)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [01fde5c](https://github.com/sgl-project/sglang/commit/01fde5cb6285c2c4dfa90f5badd2b9ae123d2ee3)

- **作者**: Michael
- **时间**: 2026-10-31T19:37:45Z
- **提交信息**: [CI] [AMD] pr-test: Run the MI35x 1-GPU stage as one job; move two e2e tests to nightly (#47150)

### [e624174](https://github.com/sgl-project/sglang/commit/e624174f0734ef605fad45edffa4603e4ae62d80)

- **作者**: Shangming Cai
- **时间**: 2026-10-31T17:55:56Z
- **提交信息**: [Fix] disaggregation: Ignore a late STAGING_REQ for an already-scattered staging chunk (#47652)

### [a65c9c5](https://github.com/sgl-project/sglang/commit/a65c9c5969055788fce6b99ba78e3eb133e7e6d0)

- **作者**: metamergebot
- **时间**: 2026-10-31T17:13:57Z
- **提交信息**: [Feat] unified-memory: Evict Full and SWA KV from one shared LRU order (joint_lru) (#46827)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: ZYHowell <ZYHowell@users.noreply.github.com>

### [60b183d](https://github.com/sgl-project/sglang/commit/60b183d5c3cebd56033cd00b74310bc2f040c800)

- **作者**: metamergebot
- **时间**: 2026-10-31T17:13:27Z
- **提交信息**: [Feat] rust-server: Reach every attention-DP rank with aborts and publish the listener map (#47532)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [2410a09](https://github.com/sgl-project/sglang/commit/2410a09c6e1a1918b9cd25250ab1a653a43d6fea)

- **作者**: Ke Bao
- **时间**: 2026-10-31T17:00:14Z
- **提交信息**: [Refactor] memory-pool: Describe DeepSeek V4 device pools with buffer info (#44990)

### [571ddad](https://github.com/sgl-project/sglang/commit/571ddad70fae4cf7a8556e42bd14019c92af7aaf)

- **作者**: metamergebot
- **时间**: 2026-10-31T16:44:59Z
- **提交信息**: [Feat] observability: Report a TTFT phase breakdown in response meta_info (#47159)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: xiezhq-hermann <xiezhq-hermann@users.noreply.github.com>

### [005b8e0](https://github.com/sgl-project/sglang/commit/005b8e033f38846cb30b7ccc0503e2ecb92900df)

- **作者**: metamergebot
- **时间**: 2026-10-31T16:44:52Z
- **提交信息**: [Fix] tokenizer_manager: Do not dispatch a request whose abort was already sent (#47546)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [9767ce3](https://github.com/sgl-project/sglang/commit/9767ce3a5a5bbea1ee912e815ce41a1e0695a739)

- **作者**: metamergebot
- **时间**: 2026-10-31T16:43:01Z
- **提交信息**: [Perf] model_executor: Write small forward metadata with fill kernels behind SGLANG_ENABLE_MLP_SYNC_METADATA_FILL (#47550)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: ZYHowell <ZYHowell@users.noreply.github.com>

### [5eb7018](https://github.com/sgl-project/sglang/commit/5eb70183472d56326920e70a4dde5cfbabe6f376)

- **作者**: Shangming Cai
- **时间**: 2026-10-31T15:37:48Z
- **提交信息**: [Fix] disaggregation: Send aux_item_lens next to aux_ptrs in PD registration (#47638)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [9780c52](https://github.com/sgl-project/sglang/commit/9780c521554153b70bd62dbaee00a93dcfec83c7)

- **作者**: Peng Wu
- **时间**: 2026-10-31T15:25:19Z
- **提交信息**: [Feat] hicache: Store MXFP8 KV pages in L3 as payload + scales objects (#46936)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [140bb6d](https://github.com/sgl-project/sglang/commit/140bb6dc8d707ee052ad5b43b40a9d52943e0958)

- **作者**: Ke Bao
- **时间**: 2026-10-31T15:01:12Z
- **提交信息**: [Fix] reasoning: Reject reasoning_effort outside the enum for M3 (#47662)

### [25c3fd8](https://github.com/sgl-project/sglang/commit/25c3fd83085e76d7ba3694900a402f964e1533bf)

- **作者**: WenhaoZhang
- **时间**: 2026-10-31T14:14:56Z
- **提交信息**: [Fix] diffusion: MiniMax-H3 warms up at the short edge --warmup-resolutions names (#47583)

### [dc79ae4](https://github.com/sgl-project/sglang/commit/dc79ae47ca745752357a183babe26fa023604ddf)

- **作者**: WenhaoZhang
- **时间**: 2026-10-31T14:14:42Z
- **提交信息**: [Fix] diffusion: LTX-2.5 two-stage defaults to its 1920x1088 canvas (#47582)

### [0f92dda](https://github.com/sgl-project/sglang/commit/0f92ddaefbce09b7cf9797ba56e710b946fdd356)

- **作者**: Mick
- **时间**: 2026-10-31T14:12:58Z
- **提交信息**: [Perf] [ROCM] diffusion: Encode the MP4 while the VAE decodes on ROCm too (#47568)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [7585ccc](https://github.com/sgl-project/sglang/commit/7585ccc2c060f09c07e2652d8608360a6c7bb47a)

- **作者**: Mick
- **时间**: 2026-10-31T14:12:29Z
- **提交信息**: [Perf] [ROCM] diffusion: Bit-exact fast QK RMSNorm and fused RoPE for MiniMax-H3 (#47569)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [dff2c4e](https://github.com/sgl-project/sglang/commit/dff2c4e102ce22467e96cc5d7949e24dbb863b6e)

- **作者**: Ke Bao
- **时间**: 2026-10-31T14:09:12Z
- **提交信息**: [Refactor] memory-pool: Build unified page-envelope host pools from buffer info (#45020)

### [8368f86](https://github.com/sgl-project/sglang/commit/8368f86fd7a71b07e2b7dda5d4146695ec54cbfa)

- **作者**: Jayden Yu
- **时间**: 2026-10-31T13:27:14Z
- **提交信息**: [Perf] [NVIDIA] qwen3: Reuse fused QK-norm/RoPE kernel for decode (#46908)

Co-authored-by: Jayden Yu <jaydenyu@fb.com>

### [b44b02e](https://github.com/sgl-project/sglang/commit/b44b02e5103ded81577f9821d79f4c3217a26fff)

- **作者**: Ke Bao
- **时间**: 2026-10-31T13:23:59Z
- **提交信息**: [Refactor] memory-pool: Build DSA indexer host pools from buffer info (#45019)

### [504f9cf](https://github.com/sgl-project/sglang/commit/504f9cf720c835beb96563ec5186cb4e6802cc74)

- **作者**: Mick
- **时间**: 2026-10-31T12:29:06Z
- **提交信息**: [Fix] diffusion: select Blackwell subtile attention by execution mode and quality (#47301)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [e93f817](https://github.com/sgl-project/sglang/commit/e93f817325b7cc482421c3488c6e985b328baaff)

- **作者**: Mick
- **时间**: 2026-10-31T12:27:15Z
- **提交信息**: [Perf] [ROCM] diffusion: Pipeline MiniMax-H3's Ulysses exchange over head groups on RCCL (#47567)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [c0f710f](https://github.com/sgl-project/sglang/commit/c0f710f7dccc5d6c7cf05f0cb0109b76e8b5b60d)

- **作者**: Bruno Volpato
- **时间**: 2026-10-31T12:25:59Z
- **提交信息**: [Perf] [NVIDIA] sampling: Enable Cake softmax on SM100 (#44168)

### [37fc17b](https://github.com/sgl-project/sglang/commit/37fc17b8d60aa8a380b63fae0401c5d343ae604a)

- **作者**: WenhaoZhang
- **时间**: 2026-10-31T12:24:24Z
- **提交信息**: [Feat] diffusion/model: Support Pika-Labs/Pika-H3-Flex (MiniMax-H3 + 6-step LoRA) (#47378)

### [67bd749](https://github.com/sgl-project/sglang/commit/67bd749ada5bebf3f1ed9be16a814a3243f348bd)

- **作者**: Mick
- **时间**: 2026-10-31T12:09:09Z
- **提交信息**: [Perf] diffusion: Pipeline Ulysses attention over head groups down to three waves (#47565)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [6e011a7](https://github.com/sgl-project/sglang/commit/6e011a7097530703f386b54c7ed1fdc4aa89814a)

- **作者**: Mick
- **时间**: 2026-10-31T12:05:16Z
- **提交信息**: [Perf] [ROCM] diffusion: Skip dead math-SDPA work in the MiniMax-H3 VAE decoder on gfx950 (#47570)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [5c46d20](https://github.com/sgl-project/sglang/commit/5c46d20db9507804a9fb6954840fcd72e52bc70d)

- **作者**: Mick
- **时间**: 2026-10-31T12:04:35Z
- **提交信息**: [Fix] diffusion: Server warmup reaches every data-parallel replica (#47571)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Sonnet 5.5 <noreply@anthropic.com>

### [07a8535](https://github.com/sgl-project/sglang/commit/07a85353d6c6be47a268e33a416ad537985ef262)

- **作者**: Ziyi Xu
- **时间**: 2026-10-31T11:33:54Z
- **提交信息**: [Fix] kernels/jit: Correct the PDLTriggerSecondary comment on what griddepcontrol.wait covers (#47646)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [fb9846d](https://github.com/sgl-project/sglang/commit/fb9846d3e2d66811b372b28c73229e9dbbf54288)

- **作者**: Ziyi Xu
- **时间**: 2026-10-31T09:33:27Z
- **提交信息**: [Fix] hicache: Set host_only_checkpoint in the sidecar restore test (#47630)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [f78d906](https://github.com/sgl-project/sglang/commit/f78d906f3ed0c3802068cc4ee283eb8f0c4b27ab)

- **作者**: Aurick Qiao
- **时间**: 2026-10-31T09:32:47Z
- **提交信息**: [Fix] disaggregation: Preserve sampler customized_info across PD (#40107)

Co-authored-by: Aurick Qiao <6137920+aurickq@users.noreply.github.com>
Co-authored-by: ispobock <ispobaoke@gmail.com>
Co-authored-by: Shangming Cai <csmthu@gmail.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [03a27e2](https://github.com/sgl-project/sglang/commit/03a27e2a17567d04a4309a83df8771d012bc0950)

- **作者**: Pinjie Xu
- **时间**: 2026-10-31T09:26:16Z
- **提交信息**: [Perf] cosmos3: Accelerate conditioning hashing with GPU BLAKE3 (#46028)

Signed-off-by: pinjie <pinjiex@nvidia.com>
Co-authored-by: Mick <mickjagger19@icloud.com>
Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [ba78bce](https://github.com/sgl-project/sglang/commit/ba78bce729d8b2ba05c4b3ae95c32b9bf940a859)

- **作者**: metamergebot
- **时间**: 2026-10-31T09:14:48Z
- **提交信息**: [Fix] rust-server: End an /abort_request-ed request on the scheduler's abort finish reason, as Python does (#47321)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [e9c1825](https://github.com/sgl-project/sglang/commit/e9c18259c77dad912a13b0df3148a472d19630f4)

- **作者**: metamergebot
- **时间**: 2026-10-31T08:51:07Z
- **提交信息**: [Fix] request_logger: Redact client watermark keys in request logs when watermarking is off (#47545)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [53a8a22](https://github.com/sgl-project/sglang/commit/53a8a22fb1cd1ee4778a89fc0de0c55748d6c593)

- **作者**: pllimax
- **时间**: 2026-10-31T08:45:15Z
- **提交信息**: [CI] [NPU] tests: Add GSM8K PR gate for DSV4-Flash W8A8 8P GPQA (#45293)

### [419d31a](https://github.com/sgl-project/sglang/commit/419d31a7b21073cb43617924168bc6c9483b0755)

- **作者**: Shuwen Wang
- **时间**: 2026-10-31T08:39:23Z
- **提交信息**: [CI] diffusion: Fix image preprocessing test dependency environment (#47625)

### [a4a6edd](https://github.com/sgl-project/sglang/commit/a4a6eddd25343905245db7a8b54bcf24d9483c8b)

- **作者**: Avaya Aggarwal
- **时间**: 2026-10-31T08:24:56Z
- **提交信息**: [Fix] diffusion: Nomas KV budget counts freed cached memory, reject SP-indivisible segments up front (#47516)

### [1c1166a](https://github.com/sgl-project/sglang/commit/1c1166ad04b877f56ab358e016530cfd9969fd96)

- **作者**: Wookje Han
- **时间**: 2026-10-31T08:22:16Z
- **提交信息**: [Perf] [NVIDIA] muse-spark-open: Fuse MoE finalize with the 2shot_push all-reduce (#46724)

### [ef4f3f1](https://github.com/sgl-project/sglang/commit/ef4f3f1151f16a5cc67ed1d6601a4b8292810e01)

- **作者**: Duyi-Wang
- **时间**: 2026-10-31T08:17:47Z
- **提交信息**: [Perf] [AMD] moe: Resolve MoRI dispatch from the AITER activation contract (#37367)

### [2e80af2](https://github.com/sgl-project/sglang/commit/2e80af28577dc0ca19a3cc685841f4c49be108c8)

- **作者**: Zhang, Jiejing
- **时间**: 2026-10-31T07:51:53Z
- **提交信息**: [Doc] [AMD] cookbook: Add GLM-5.2 MI355X AgentX recipe (#47615)

### [7adb930](https://github.com/sgl-project/sglang/commit/7adb930d630f456f43e4978fa27ca8baeb80e319)

- **作者**: Ke Bao
- **时间**: 2026-10-31T07:48:36Z
- **提交信息**: [Doc] cookbook: Update MiniMax-M3.1-Flash AgentX launches (#47623)

### [1f834c1](https://github.com/sgl-project/sglang/commit/1f834c196414db0dd201f0a1ecc9fd143aaaf119)

- **作者**: Shuwen Wang
- **时间**: 2026-10-31T07:04:11Z
- **提交信息**: [Fix] hicache: Resolve derived sidecars over every source transfer (#43110)

Co-authored-by: Sam Shleifer <sshleifer@gmail.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-11-01
**监控日期**: 2026-10-31
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for 100+ DiTs.
- **语言**: Python
- **星标数**: 1297
- **最后更新**: 2026-10-31T15:34:00Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

## vipshop/cache-dit 昨日提交分析

### 1. 主要更新类型
- **功能新增（主导）**：1 个核心功能提交，支持新模型 CausVid-Wan。
- **文档更新**：1 个辅助提交，优化模型路线图的展示。

### 2. 关键变更点及与项目方向的关系
- **CausVid-Wan 支持（8888f9c）**：这是本次的核心变更。CausVid 将 Wan2.1-T2V-1.3B 蒸馏为 3 步分块自回归（chunk-autoregressive）的学生模型。该模型以原生 `model.pt` 形式发布，无 diffusers pipeline，因此项目选择将其作为 custom_models 进行 vendor 化，而非强行适配 diffusers。
- **文档路线图更新（16a4812）**：按社区价值和缓存适配度对待支持模型进行排序，属于社区运营和项目规划层面的优化。
- **与项目方向的关系**：README 明确项目目标是为 DiT 模型提供原生推理引擎，覆盖缓存、并行、量化、CPU offload 等能力。CausVid-Wan 的接入正是扩展模型覆盖面的典型动作，尤其契合"缓存"这一核心卖点——该模型的核心机制就是分块自回归与 KV 缓存生命周期管理。

### 3. 对项目的影响和潜在意义
- **扩展模型生态**：CausVid-Wan 是一种新颖的因果蒸馏视频生成模型（81 帧 = 7 个 chunk），支持它意味着项目能覆盖更多前沿的高效视频生成方案。
- **证明架构可扩展性**：通过自定义 Transformer 子类（仅替换注意力块类、RoPE 偏移和 forward），复用了 diffusers 的 Wan 模块命名体系，从而无需改动即可继续使用既有的张量并行（TP）方案、`DistributedRMSNorm`、区域量化、块级编译等基础设施。这验证了项目推理后端的通用性和可维护性。
- **社区信号**：文档提交按"社区价值"排序模型，表明项目在有意识地引导社区贡献方向。

### 4. 值得关注的技术点
- **状态字典兼容性**：自定义模块保持 diffusers 命名，825 个张量逐 key 匹配，`strict=True` 加载成功，说明集成方式干净、无隐式改动。
- **分块缓存生命周期管理**：pipeline 负责 chunk 循环与缓存刷新。关键设计包括 clean-latent 通道（`force_full_compute`，避免后续 chunk 误用带噪的 K/V）、chunk 边界的 `force_refresh_step_hint`，以及刷新步计数器重启以将预热窗口限制在一步。这些细节体现了对因果注意力缓存正确性的深入考量。
- **Ulysses 上下文并行 + 分头 KV 缓存**：每个 rank 只保留自己拥有的头的完整历史，注意力处理器自行交换 q/k/v，plan 仅切分 RoPE 输出和 `blocks.0` 隐藏态并在 `proj_out` 聚合。明确拒绝 Ring 并行和 `--ulysses-anything`，理由是缓存按全局 token 坐标寻址，padding 会破坏 KV 槽位——这是一个清晰且有说服力的设计边界声明。

### 5. 对项目发展的整体影响
结合 README 描述的项目定位——原生、高性能、功能完备的 DiT 推理引擎——这两个提交共同推进了两个方向：一是**模型覆盖广度**，通过引入因果蒸馏类自回归视频模型，触及了与传统全注意力 DiT 差异较大的缓存与并行模式，锻炼了推理后端的适配能力；二是**社区参与度**，文档提交以社区价值为导向梳理路线图，有助于集中资源回应真实需求。CausVid-Wan 的集成尤其有示范意义：它展示了如何在不改动核心并行与量化基础设施的前提下，以最小侵入方式接入结构特殊的模型，这种"模块级复用 + 局部替换"的集成范式，将降低未来类似模型的接入成本，从而巩固项目作为多模型 DiT 推理枢纽的长期价值。

## 详细提交记录

### [16a4812](https://github.com/vipshop/cache-dit/commit/16a48123946baac7434c136722cdc859dae13375)

- **作者**: DefTruth
- **时间**: 2026-10-31T15:33:55Z
- **提交信息**: docs: rank pending models by community value and cache fit (#1207)

### [8888f9c](https://github.com/vipshop/cache-dit/commit/8888f9c90ff12a62f887fa00cda8c6e72f3db955)

- **作者**: DefTruth
- **时间**: 2026-10-31T14:37:52Z
- **提交信息**: feat(causvid): support CausVid-Wan (Wan2.1-T2V-1.3B causal student) (#1205)

* feat(causvid): support CausVid-Wan (Wan2.1-T2V-1.3B causal student)

CausVid distils Wan2.1-T2V-1.3B into a 3-step chunk-autoregressive student:
81 frames = 7 chunks of 3 latent frames, each chunk runs the fixed DMD table
1000/757/522 and then a clean-latent pass that writes the K/V every later chunk
attends to. It ships as one native-Wan `model.pt` with no diffusers pipeline, so
the model is vendored (custom_models entry 1) instead of adapting diffusers:

- `models/pipelines/causvid/`: the transformer subclasses diffusers
  `WanTransformer3DModel` and only swaps the block class (causal self-attention
  with a KV cache), the RoPE offset and the forward. Module names therefore stay
  the diffusers Wan names, which keeps the Wan TP plan, `DistributedRMSNorm`,
  `_repeated_blocks`, regional quantization and block-level compile working; the
  state dict matches diffusers key-for-key (825 tensors) and the native->diffusers
  conversion loads `strict=True`.
- The pipeline owns the chunk loop and the cache lifecycle: the clean-latent pass
  replays the raw block stack (`force_full_compute`), because a block-skipped
  commit would leave the noisy K/V of the current chunk for every later chunk, and
  each chunk boundary arms `force_refresh_step_hint` so the first denoising step of
  a chunk always recomputes. The per-chunk counter restarts on that refresh, so the
  warmup window is capped at one step (logged once) or it would swallow every step.
- Context parallelism is Ulysses with a head-sharded KV cache: every rank keeps the
  full history of the heads it owns, the attention processor exchanges q/k/v itself
  and the plan only splits RoPE output and `blocks.0` hidden states and gathers at
  `proj_out`. Ring and `--ulysses-anything` are refused (the cache is addressed by
  global token coordinates, padding would land inside the KV slots).
- `causvid_wan` CLI example, `CAUSVID_DIR` env mapping, adapter, TP/CP planners,
  CPU tests (28) and 2-GPU CP/TP parity tests.

Verified against the release: fp32 rel 2.0e-6 per chunk versus upstream
`CausalWanModel`, CP2 bit-exact in the tiny parity test and 5.4e-7 in fp32 on the
real weights. Tier A matrix on RTX PRO 5000 (480x832x81f, 21 executed steps):
baseline 12.68s / 27.6 GiB; compile 1.04x; fp8-per-row+compile 1.16x;
svdq-nvfp4+compile 1.15x; `--attn ffpa_fp8`+compile 1.12x (attention is ~58% of the
FLOPs); TP2 1.04x, TP2+compile 1.11x, TP2+VAE-P 1.16x; Ulysses CP2 1.14x,
CP2+compile 1.17x, CP2+fp8 1.26x, CP2+svdq 1.26x; layerwise offload 15.8 GiB.

DBCache is ineffective here and the supported matrix marks it ✖️: the measured
per-chunk residual diffs are 0.96-1.20 (3-step DMD steps are far apart), so only
`--rdt 1.0` hits (14/21) and it changes the clip (SSIM 0.44). The clip is also
numerically chaotic — the same configuration in bf16 versus fp32 scores 20.8 dB —
so PSNR/SSIM rank fidelity to the bf16 trajectory, not quality; the fp32 parity and
visual checks carry the quality gate.

* Update CausVid-Wan entry in README

* Update CausVid-Wan entry in README

---------

Co-authored-by: DefTruth <DefTruth@users.noreply.github.com>

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-11-01
**监控日期**: 2026-10-31
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 96004
- **最后更新**: 2026-11-01T01:01:13Z

## 提交统计

- **昨日提交总数**: 19
- **提交者数量**: 17
- **主要提交者**: 0z5a, ChengYM, namgyu-yun

## AI分析总结

## vLLM 昨日提交总结（19条）

### 1. 主要更新类型分布
- **性能优化**（约7条）：内核优化、内存优化、前端优化
- **Bug修复**（约6条）：涉及工具解析、投机解码、注意力后端、模型加载等
- **文档更新**（3条）：均为ROCm平台的部署配方
- **功能新增/架构演进**：MORI EP V2、权重映射器能力扩展

### 2. 关键变更点及与项目方向的关系
- **ROCm/AMD生态持续扩张**：3条文档提交为MI355X等AMD GPU提供Mistral Large、MiniMax、DeepSeek等模型的TP4/TP8 AgentX部署预设，1条为Spark drafters添加ROCm量化支持。这与vLLM"为所有人提供易用、快速、低成本LLM服务"的多硬件平台战略一致，强化AMD GPU的生产级部署路径。
- **内核级性能深耕**：包括稀疏索引器prefill的单launch融合scoring+top-k内核（避免物化logits）、FlashInfer FP8/W4A16 NVFP4内核的批量不变性验证、针对GLM-5.3和Qwen3.8在SM121/SM103上的skinny-GEMM优化，直接服务"fast"目标。
- **投机解码（Spec Decode）修复与增强**：修复MRV2独立draft模型的MoE/注意力后端覆盖问题，体现对低延迟生成路径的持续打磨。

### 3. 对项目的影响和潜在意义
- **内存效率**：减少chunked prompt logprobs峰值内存、跳过权重张量的冗余clone，降低部署门槛，服务"cheap"目标。
- **前端正确性**：Rust前端中计算prompt块哈希（加速前缀缓存匹配）、批量chat补全中报告prompt_tokens_details，提升API兼容性与请求调度效率。
- **可靠性**：修复PP>1下FlashInfer attention预热死锁，对多卡流水线并行的生产环境稳定性有实质意义。

### 4. 值得关注的技术点
- **批量不变性（Batch invariance）验证**：将特定内核固定/验证，是高精度推理的重要质量保障手段，值得业界参考。
- **Rust前端的prompt块哈希计算**：将前缀缓存的关键路径移入Rust，性能收益可观。
- **权重映射器支持transform操作**：为异构权重格式和量化转换提供了更灵活的钩子。
- **AI辅助协作常态化**：大量提交的Co-authored-by包含Claude、Codex等AI署名，反映AI参与大模型推理引擎开发已成常态。
- **较长生命周期的修复合入**：如CohereASR FP16注意力偏置dtype修复（PR #54399）编号靠前，说明积压的正确性问题正在被清理。

### 5. 对项目发展的整体影响
这些提交共同体现了vLLM在"易用、快速、低成本"三大方向上的均衡推进：ROCm文档预设降低了AMD用户的上手成本（易用），多架构内核优化和内存节省提升吞吐（快速、低成本），而大量Bug修复则夯实了生产可靠性。多硬件支持（AMD、NVIDIA SM10x/SM12x）和投机解码、MORI专家并行等前沿特性的持续推进，使vLLM保持在LLM推理引擎领域的技术领先地位。整体而言，项目正处于从"功能扩展"向"性能调优与生产加固"并重的成熟阶段演进。

## 详细提交记录

### [564ac0d](https://github.com/vllm-project/vllm/commit/564ac0de1b228568cafcbfbe8ccaccc82d6023eb)

- **作者**: indivats
- **时间**: 2026-10-31T21:23:05Z
- **提交信息**: [Docs][ROCm] Mistral Large 4 recipe: adds TP4 and lowest-latency presets  (#64792)

Signed-off-by: Indira Vats <Indira.Vats@amd.com>

### [b03e788](https://github.com/vllm-project/vllm/commit/b03e78881268d92db162e8f73667746cbcf00f5d)

- **作者**: Fangzhou Ai
- **时间**: 2026-10-31T21:22:57Z
- **提交信息**: [Docs][ROCm] Add MiniMax-M3.1-Flash MI355X TP4 AgentX preset (#64805)

Signed-off-by: Fangzhou Ai <31551580+Fangzhou-Ai@users.noreply.github.com>
Co-authored-by: Claude Sonnet 5.5 <noreply@anthropic.com>
Co-authored-by: Hongxia Yang <62075498+hongxiayang@users.noreply.github.com>

### [3f9d184](https://github.com/vllm-project/vllm/commit/3f9d1847386932fc4f841e875f26c4e0035bc0b2)

- **作者**: Fangzhou Ai
- **时间**: 2026-10-31T21:18:41Z
- **提交信息**: [Docs][ROCm] Add DeepSeek-V4.1-Flash MI355X TP8 concurrency-1 AgentX preset (#64804)

Signed-off-by: Fangzhou Ai <31551580+Fangzhou-Ai@users.noreply.github.com>
Co-authored-by: Claude Sonnet 5.5 <noreply@anthropic.com>

### [cfa9f96](https://github.com/vllm-project/vllm/commit/cfa9f96f5efbb45c5c02ab127b51eaf8b86bb4ca)

- **作者**: Vegetog
- **时间**: 2026-10-31T20:28:34Z
- **提交信息**: [Bugfix][Tool Parser] Preserve whitespace in HYV4 argument names (#61542)

Signed-off-by: Vegetog <110553275+Vegetog@users.noreply.github.com>
Co-authored-by: Flora Feng <4florafeng@gmail.com>

### [d8fad92](https://github.com/vllm-project/vllm/commit/d8fad9202a52744efc7c34a67df6036b8e7cc023)

- **作者**: aoshen02
- **时间**: 2026-10-31T20:21:56Z
- **提交信息**: [Bugfix][Spec Decode] Honor draft moe/attention backend overrides for MRV2 standalone draft model (#64751)

Signed-off-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [e318ac0](https://github.com/vllm-project/vllm/commit/e318ac09796468ac31139d64d609143874e0ed3b)

- **作者**: Nick Hill
- **时间**: 2026-10-31T19:38:38Z
- **提交信息**: [Perf][Frontend] Compute prompt block hashes in the Rust frontend (#63842)

Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [25fc607](https://github.com/vllm-project/vllm/commit/25fc60723cf6c92c041b0c665450023b96544e9a)

- **作者**: Roberto L. Castro
- **时间**: 2026-10-31T19:01:17Z
- **提交信息**: [Perf][Kernel] Single-launch fused scoring+top-k kernel for sparse-indexer prefill, without materializing logits (#60618)

Signed-off-by: LopezCastroRoberto <rocastro@redhat.com>
Co-authored-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Ziqi Yin <62246771+Heisenberg-Yin@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [42258ca](https://github.com/vllm-project/vllm/commit/42258ca4afe8d3cee728a2d7cf52091f3ace15ff)

- **作者**: Nick Hill
- **时间**: 2026-10-31T18:48:16Z
- **提交信息**: [ModelRunner V2] Reduce peak memory of chunked prompt logprobs (#64841)

### [0c63ce9](https://github.com/vllm-project/vllm/commit/0c63ce9f0e0b5b2782f0f30cb491069dac158bb2)

- **作者**: Jack Liang
- **时间**: 2026-10-31T16:03:42Z
- **提交信息**: [Bugfix][Frontend] Report prompt_tokens_details in batched chat completions (#64757)

Signed-off-by: Jackmeson1 <130693642+Jackmeson1@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [50f622b](https://github.com/vllm-project/vllm/commit/50f622bdcf17071cf2e715c47e4a0bf13cf6cf2e)

- **作者**: Noa Neria
- **时间**: 2026-10-31T16:02:23Z
- **提交信息**: Skip redundant weight tensor clones for loaders that yield owned tensors (#63174)

Signed-off-by: Noa Neria <nneria@nvidia.com>
Co-authored-by: Claude Sonnet 5.5 <noreply@anthropic.com>

### [78161c2](https://github.com/vllm-project/vllm/commit/78161c28da3b17f95d27c16f7d329cc1f1987f27)

- **作者**: Jikui Xie
- **时间**: 2026-10-31T15:42:57Z
- **提交信息**: [Bugfix][Model] Fix CohereASR FP16 attention bias dtype (#54399)

Signed-off-by: jikuixie <jikuixie@gmail.com>
Signed-off-by: Jikui Xie <jikuixie@gmail.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [54beee8](https://github.com/vllm-project/vllm/commit/54beee831b0fd2df2a19967b7dcea661c32044c5)

- **作者**: 0z5a
- **时间**: 2026-10-31T15:25:09Z
- **提交信息**: [Kernel] Batch invariance: pin FlashInfer FP8 bmm and W4A16 NVFP4 kernels (#62192)

Signed-off-by: aoshen02 <aoshen@inferact.ai>
Signed-off-by: 0z5a <0z5a@users.noreply.github.com>
Co-authored-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [4aba9bf](https://github.com/vllm-project/vllm/commit/4aba9bf3a4da72745b1bcb2e0870a1dd6e9c4861)

- **作者**: yzong-rh
- **时间**: 2026-10-31T15:24:04Z
- **提交信息**: [Bugfix] Flashinfer attention warmup deadlock under PP>1 (#64338)

Signed-off-by: Yifan Zong <yzong@redhat.com>
Co-authored-by: Tyler Michael Smith <tlrmchlsmth@gmail.com>
Co-authored-by: Roberto L. Castro <38211239+LopezCastroRoberto@users.noreply.github.com>

### [e5196e2](https://github.com/vllm-project/vllm/commit/e5196e2959a42908313510f55fa21f213a48802e)

- **作者**: Tim002
- **时间**: 2026-10-31T13:55:23Z
- **提交信息**: [Perf][glm5next] Add SM121 TP=2 skinny-GEMM plans for GLM-5.3-Flash (#62956)

Signed-off-by: TimRen01 <HolaTim@hotmail.com>
Signed-off-by: LopezCastroRoberto <robertol.c510@gmail.com>
Co-authored-by: LopezCastroRoberto <robertol.c510@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Roberto L. Castro <38211239+LopezCastroRoberto@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [7b77ed5](https://github.com/vllm-project/vllm/commit/7b77ed581d92fa14e34ab43344837bb1ca1b4257)

- **作者**: AMD-yanfeiwang
- **时间**: 2026-10-31T10:23:36Z
- **提交信息**: [Spec Decode][ROCm] draft_lm_head_quantization for DSpark drafters (#64368)

Signed-off-by: Yanfei Wang <yanfei.wang@amd.com>
Co-authored-by: Shanshan Shen <467638484@qq.com>

### [87cb835](https://github.com/vllm-project/vllm/commit/87cb835db2bbbaa03e3faa6ae588ba92dce1eea4)

- **作者**: Isotr0py
- **时间**: 2026-10-31T09:20:12Z
- **提交信息**: [Misc] Allow weights mapper to transform weights (#64869)

Signed-off-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [10da92f](https://github.com/vllm-project/vllm/commit/10da92ff285612aa0c6947d1dd8c51fc2062771e)

- **作者**: Hangrui Cao
- **时间**: 2026-10-31T09:11:52Z
- **提交信息**: [Bugfix][Model] Make compile_mm_encoder work for RADIO/NaViT encoders (#63415)

Signed-off-by: HangruiCao2000 <caohangrui2000@gmail.com>

### [d5301a4](https://github.com/vllm-project/vllm/commit/d5301a4f5487db1d7e8d87daf7828225b95b1774)

- **作者**: ChengYM
- **时间**: 2026-10-31T08:54:46Z
- **提交信息**: [MORI] Add MORI EP V2 support (#61361)

Signed-off-by: inkcherry <mingzhi.liu@amd.com>
Signed-off-by: ChengYM5685 <Yueming.Cheng@amd.com>
Signed-off-by: ChengYM <320424417+ChengYM5685@users.noreply.github.com>
Co-authored-by: inkcherry <mingzhi.liu@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Shanshan Shen <467638484@qq.com>
Co-authored-by: ChengYM <320424417+ChengYM5685@users.noreply.github.com>
Co-authored-by: Codex <noreply@openai.com>

### [900b8b0](https://github.com/vllm-project/vllm/commit/900b8b08e2552c28a004e075866b5e1a39b99ac3)

- **作者**: namgyu-yun
- **时间**: 2026-10-31T07:50:07Z
- **提交信息**: [Perf][Qwen3.8] Add SM103 skinny GEMM plans for TP=1 (#64650)

Signed-off-by: namgyu-yun <namgyu.dev@gmail.com>
Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>
Co-authored-by: Thien Tran <gau.nernst@yahoo.com.sg>
Co-authored-by: Kimi Code <noreply@moonshot.cn>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-11-01
**监控日期**: 2026-10-31
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7452
- **最后更新**: 2026-11-01T00:53:24Z

## 提交统计

- **昨日提交总数**: 12
- **提交者数量**: 7
- **主要提交者**: Mohammad Hijjawi, tanhaoan333, wangyu

## AI分析总结

# vllm-omni 昨日提交批次分析

## 1. 主要更新类型

- **CI/Build 工程化（7/12）**：ROCm 硬件测试门控与 CI 流水线完善占主导
- **功能新增（2）**：Kokoro-82M TTS 模型、Ascend 图复用优化
- **性能优化（2）**：VoxCPM2 相关权重与内存传输优化
- **Bug 修复（1）**：Seed-TTS 基准测试指标展示

## 2. 关键变更点及与项目方向的关系

- **ROCm MI300 测试体系强化**：多条提交围绕 MiniCPM-o、Drama 3、Qwen-Image、Qwen3-Omni 等模型在 MI300 上建立 MERGE/READY 门控机制，将 ROCm 硬件验证从"事后检查"前移为"合并前强制关卡"，直接服务于 README 中"快速、廉价全模态推理"的跨硬件支持目标
- **TTS 模态能力扩展**：Kokoro-82M 单阶段 TTS 模型加入，Seed-TTS 基准补充 WER/SIM/UTMOS 指标，VoxCPM2 双项性能优化——体现 omni（全模态）中语音合成子方向的持续深化
- **Ascend 硬件适配**：静态形状解码未命中时复用已捕获的 ACL 图，减少图重捕获开销，是对国产硬件推理路径的针对性优化

## 3. 对项目的影响和潜在意义

- **稳定性提升**：MERGE gating 机制将硬件兼容问题拦截在主干合并前，降低下游用户在 AMD GPU 上的踩坑概率
- **语音服务能力增强**：新增模型 + 指标补全 + 性能优化三管齐下，使 TTS 功能对用户更透明、更高效
- **CI 负载再平衡**：Cosmos3 功能测试移至 weekly，缓解合并门禁压力，属于健康的测试策略调整

## 4. 值得关注的技术点

- **VoxCPM2 优化细节**：移除 weight_norm 并将 AudioVAE 转为 bf16 减少显存占用；stop-mask 异步 D2H 传输配合 pinned memory 消除同步传输瓶颈——典型的推理链路微优化组合
- **Ascend ACL 图复用**：静态形状解码 miss 时复用图缓存，涉及图捕获生命周期管理，对动态 batch 场景的吞吐有实际意义
- **CI 门控分层设计**：READY（快速就绪）与 MERGE（合并前强校验）两级机制，值得其他推理框架借鉴

## 5. 对项目发展的影响

结合 README"Easy, fast, and cheap omni-modality model serving"的定位：

- **硬件生态广度**：同一天内覆盖 ROCm、Ascend、以及原有 CUDA 路径的优化，说明项目正全力推进"不绑死单一 GPU 厂商"的普惠路线，降低用户获取全模态推理能力的硬件门槛
- **TTS 成为重要支柱**：四个提交聚焦语音合成，暗示 TTS 是当前 omni 模态矩阵中投入产出比最高的方向之一
- **工程质量意识**：大量 AI 辅助协作（Cursor、Grok、opencode 署名）与严格的 CI 门控并存，体现项目在快速迭代与质量守护之间的平衡策略，有利于吸引外部贡献者的同时保持主干稳定

综上，这批提交以 CI 硬件门控为主线，辅以 TTS 能力与推理性能的针对性增强，稳步推进项目向"跨硬件、全模态、可信赖"的推理服务框架目标迈进。

## 详细提交记录

### [49a5586](https://github.com/vllm-project/vllm-omni/commit/49a55865a08fc349044a5b2d38579957da51b099)

- **作者**: hac17
- **时间**: 2026-10-31T23:57:23Z
- **提交信息**: [CI/Build][ROCm] Qualify MiniCPM-o V1 fallback duplex on MI300 READY (#9670)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>
Co-authored-by: haic0 <149741444+haic0@users.noreply.github.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Grok 4.7 <noreply@x.ai>

### [f1f743a](https://github.com/vllm-project/vllm-omni/commit/f1f743ae0a1cd65895345c1738821030ba85b4b5)

- **作者**: Mohammad Hijjawi
- **时间**: 2026-10-31T23:55:29Z
- **提交信息**: [Bugfix] Show Seed-TTS WER/SIM/UTMOS in the TTS benchmark summaries (#8354)

Signed-off-by: Mohammad Hijjawi <mohammad.hijjawi1997@gmail.com>
Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: Yueqian Lin <linyueqian@outlook.com>

### [3189c37](https://github.com/vllm-project/vllm-omni/commit/3189c3720f2abe7c7a175b58ed5627d419c9ce97)

- **作者**: hac17
- **时间**: 2026-10-31T23:17:44Z
- **提交信息**: [CI/Build][ROCm] Make VeRL-Omni generate a blocking READY check (#9668)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>
Co-authored-by: haic0 <149741444+haic0@users.noreply.github.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Grok 4.7 <noreply@x.ai>

### [099ea77](https://github.com/vllm-project/vllm-omni/commit/099ea7705533328219d5b88e04fe2a6ecb1788f1)

- **作者**: haic0
- **时间**: 2026-10-31T23:10:00Z
- **提交信息**: [CI/Build][ROCm] Gate Drama 3 text-to-audio on MI300 MERGE (#9679)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [beeedd9](https://github.com/vllm-project/vllm-omni/commit/beeedd99df33b432b7cf74caa8b28e1893124827)

- **作者**: A&W
- **时间**: 2026-10-31T21:41:36Z
- **提交信息**: [Model] Add Kokoro-82M single-stage TTS (#9637)

Signed-off-by: Alex-Wengg <hanweng9@gmail.com>

### [edd2a1b](https://github.com/vllm-project/vllm-omni/commit/edd2a1b2313edd25fa9e11b552756bbae9a07e89)

- **作者**: haic0
- **时间**: 2026-10-31T20:09:26Z
- **提交信息**: [CI/Build][ROCm] Gate MiniCPM-o core cases on MI300 MERGE (#9680)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [1290d1c](https://github.com/vllm-project/vllm-omni/commit/1290d1c2b19e87a361a4f65fc1f1854f5cb4714c)

- **作者**: haic0
- **时间**: 2026-10-31T19:15:32Z
- **提交信息**: [CI/Build][ROCm] Gate the Qwen-Image default smoke on MI300 MERGE (#9681)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [3059eaf](https://github.com/vllm-project/vllm-omni/commit/3059eafa4ebaafc19061dae123d400bc20f78550)

- **作者**: haic0
- **时间**: 2026-10-31T18:28:54Z
- **提交信息**: [CI/Build][ROCm] Require the Qwen3-Omni SHM leak MERGE check (#9678)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [c7f56f0](https://github.com/vllm-project/vllm-omni/commit/c7f56f0155953c7d4a77276a2f4fcbd844ab0da2)

- **作者**: Lingwei1943
- **时间**: 2026-10-31T14:39:31Z
- **提交信息**: [perf][VoxCPM2] remove weight_norm and cast AudioVAE to bf16 (#8309)

Signed-off-by: Lingwei1943 <lingwei1943@users.noreply.github.com>
Co-authored-by: Lingwei1943 <lingwei1943@users.noreply.github.com>
Co-authored-by: opencode <opencode@ai>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [3bcd944](https://github.com/vllm-project/vllm-omni/commit/3bcd94425f87fa2b0ec68582bd7c58fd7a5bc66b)

- **作者**: tanhaoan333
- **时间**: 2026-10-31T10:26:53Z
- **提交信息**: [Hardware][Ascend] Reuse captured ACL graphs on static-shape decode misses (#9618)

Signed-off-by: tanhaoan333 <249022399+tanhaoan333@users.noreply.github.com>
Co-authored-by: tanhaoan333 <249022399+tanhaoan333@users.noreply.github.com>
Co-authored-by: buaa14211107 <784377394@qq.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [9fb6087](https://github.com/vllm-project/vllm-omni/commit/9fb60877e9f272875fd84861b59712de00b9558e)

- **作者**: Lingwei1943
- **时间**: 2026-10-31T09:34:45Z
- **提交信息**: [perf][VoxCPM2]: async stop-mask D2H transfer with pinned memory (#8310)

Signed-off-by: Lingwei1943 <lingwei1943@users.noreply.github.com>
Co-authored-by: Lingwei1943 <lingwei1943@users.noreply.github.com>
Co-authored-by: opencode <opencode@ai>
Co-authored-by: Weiming Liao <liaowm5@gmail.com>

### [88e606b](https://github.com/vllm-project/vllm-omni/commit/88e606b560de9b6384b3d10a8be033e38838e7cd)

- **作者**: wangyu
- **时间**: 2026-10-31T09:23:52Z
- **提交信息**: [CI/Build] Move Cosmos3 functional tests to weekly (#9685)

Signed-off-by: wangyu <410167048@qq.com>

---
