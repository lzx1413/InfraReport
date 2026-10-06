# GitHub Stars 合并报告 - 2026-10-05

**合并日期**: 2026-10-06
**监控日期**: 2026-10-05
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


**报告日期**: 2026-10-06
**监控日期**: 2026-10-05
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2233
- **最后更新**: 2026-10-05T18:27:27Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-10-06
**监控日期**: 2026-10-05
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2877
- **最后更新**: 2026-10-05T10:30:30Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Chengtao Lv

## AI分析总结

# LightX2V 仓库提交分析 (commit 0c2edc1)

## 1. 主要更新类型

**功能新增**：提交标题 "add realtimewam" 表明这是一次**功能扩展**，为框架添加了实时水印（real-time watermark）相关能力。该提交由外部贡献者 Charles2530 提交（Co-authored-by 信息表明是社区协作开发），并通过 PR #1577 合并入库，属于典型的**社区驱动的功能演进**。

## 2. 关键变更点及与项目整体方向的关系

**核心变更**：引入实时水印（realtime wam，推测为 "real-time watermark"）处理模块，可能涉及视频生成推理流程中的帧级水印添加逻辑。

**与项目方向的契合度**：
- **轻量化目标**：LightX2V 定位为 "Light Video Generation Inference Framework"，该功能以轻量方式扩展框架能力，而非引入重量级依赖，与项目命名理念一致。
- **推理框架完整性**：视频生成推理框架不仅需要"生成"能力，还需要"后处理/安全合规"能力。实时水印的加入完善了从生成到输出的完整流水线。
- **社区协作模式**：外部贡献者提交核心功能，说明项目社区生态活跃，社区开发者愿意为框架的生产级能力贡献代码。

## 3. 对项目的影响和潜在意义

**直接影响**：
- **功能完整性提升**：框架具备了实时水印能力，输出视频可直接携带水印标识，满足版权保护、来源追溯等合规需求。
- **使用场景拓宽**：对于需要批量、实时生成带水印内容的场景（如内容平台、广告生成），LightX2V 从纯推理工具升级为更完整的端到端解决方案。
- **生产就绪度增强**：水印是许多商业应用的硬性需求，此功能降低了企业用户采用 LightX2V 的合规门槛。

**潜在风险**：
- 实时水印处理可能引入轻微的推理延迟，需关注其对整体吞吐量的影响。
- 若水印处理逻辑与推理流程耦合度较高，可能需要后续的解耦重构。

## 4. 值得关注的技术点

- **实时水印的实现方式**：推测采用帧级叠加（如在推理输出帧上直接叠加水印图层），这种方式可在不额外启动独立后处理服务的情况下，保持端到端的低延迟特性。
- **与推理引擎的集成点**：水印处理应在模型推理后的轻量阶段执行，而非侵入核心推理路径，关注其在 pipeline 中的位置设计。
- **水印配置灵活性**：值得关注是否支持水印位置、透明度、内容等参数的自定义配置，这决定了功能的实用价值。
- **PR 模式（#1577）**：通过独立 PR 提交功能而非直接 push，符合项目良好的工程协作规范。

## 5. 对项目发展的整体影响

基于 README 项目背景——LightX2V 致力于构建**轻量、高效的视频生成推理框架**——本次提交体现了项目的演进路径：**从核心推理能力的构建，逐步转向生产级完整工作流的完善**。

- **短期影响**：功能上补齐了水印这一合规短板，对商业用户吸引力提升。
- **长期意义**：社区外部贡献者持续输出功能模块，表明项目已进入"社区共建"阶段，有利于降低核心开发团队的维护压力，加速功能迭代节奏。
- **方向预示**：后续可能围绕"实时后处理"方向继续扩展（如实时画质增强、格式转码、安全过滤等），将 LightX2V 打造成覆盖完整生成-处理链的轻量级视频生成平台。

## 详细提交记录

### [0c2edc1](https://github.com/ModelTC/LightX2V/commit/0c2edc124227fcb6e22399e12c35f23298a7299a)

- **作者**: Chengtao Lv
- **时间**: 2026-10-05T10:30:24Z
- **提交信息**: add realtimewam (#1577)

Co-authored-by: Charles2530 <2569337619@qq.com>

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-10-06
**监控日期**: 2026-10-05
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2283
- **最后更新**: 2026-10-06T01:27:34Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-10-06
**监控日期**: 2026-10-05
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6549
- **最后更新**: 2026-10-06T02:18:56Z

## 提交统计

- **昨日提交总数**: 15
- **提交者数量**: 8
- **主要提交者**: Nikita Korobov, Alex Yang, roigarnettNvidia

## AI分析总结

# FlashInfer 昨日提交合并总结

## 一、主要更新概览

昨日提交覆盖功能新增、性能优化、Bug 修复与文档更新四类。功能侧重点在 MoE 模型扩展、新一代硬件适配、前沿模型算子支持与融合 GEMM 内核；性能侧延续采样、attention、Mamba 等关键路径的极致优化；修复侧则聚焦 autotuner 缓存策略、MoE 路由契约与 DSL 版本兼容性；同时通过架构门控审计恢复了大量被无意义跳过的测试用例。

## 二、关键变更

**MoE 与超大模型覆盖**：`cake_warp_decode` 后端新增 Qwen3.5-397B 与 MiniMax-M2 的 TP2/TP4 分片 SwiGLU 几何结构（SM100/SM103），每个模型新增 256 条路由，输出与 trtllm-gen 位级一致。同时，fused route-pack 将路由打包嵌入 persistent FC1 的 prologue，消除独立内核启动开销，配合 metadata-prefetch FC2 的 144 workfeed CTA，形成端到端的 MoE 路由加速。

**硬件代际适配**：CuTe DSL GEMM 家族（TGV、低延迟块缩放、连续分组 GEMM）将 `supported_compute_capability` 白名单从 [100, 103] 扩展到包含 SM107（Rubin），消除了过时的模块加载限制。MLA 自动选择路径延伸至 SM103/SM107，使新一代 GPU 用户无需手动指定后端即可走优化路径。SM12x MoE 的未路由专家 ID 修复则解决了客户端 GPU 上的非法内存访问问题。NVFP4 低延迟 GEMM 在 SM103 上获得 3x 支持与专用 epilogue。

**前沿模型算子**：DeepSeek-V3.2 的 DSA indexer logits 以 DeepGEMM 签名形式公开 API（dense/paged 两类），不改变张量布局与 chunking 即可切换引擎调用点。Prims-TS 层新增 FP8 与 NVFP4 GEMM，集成 SwiGLU、RoPE、QKNorm 融合。Mamba 状态更新启用 SM107 原生随机舍入，性能提升 1.4–1.6 倍。

**采样与 attention 优化**：cake_sampling round 9 引入 leader-push 交换孪生内核（18 个新 stage-1 内核），各 CTA 直写 rank-0 共享内存接收缓冲区，省去 DSM 读与退出集合点，避免 push-to-all 的 N 倍字节放大。MiniMax-H3 NVFP4 注意力实现 warp 特化，在 FP32 操作顺序不变前提下位精确输出；Hopper BF16 MegaMoE 的 `prereduced` 合并线在固定累加顺序下保持确定性，两者均在 SOTA 基准上超越或持平竞品。

**修复与工程卫生**：autotuner 修复了 `ProfilingCacheKey` 未包含 replay/L2 测量策略导致的短名单缓存污染问题；MoE 侧统一将 `topk_ids=-1` 定义为"未路由"，修复 vLLM 填充行场景下的数据损坏。CuTe DSL 通过导入时探测上下文支持、区分 4.7/4.8 调用签名并用 `cutlass.const_expr` 固定编译期分支，解决了版本兼容问题。另有 442 个测试函数（约 8400 个用例）因过时架构门控被恢复，每个提交具备独立可回滚证据链。

## 三、项目影响

- **模型生态**：Qwen3.5-397B、MiniMax-M2、DeepSeek-V3.2 等超大模型获得原生内核支持，直接提升 FlashInfer 在主流 LLM 服务场景的可用性。
- **生产稳定性**：MoE 契约修复与 DSL 兼容修复降低下游框架（vLLM、Nemotron/MegaMoE）的崩溃与静默数据损坏风险。
- **生态整合**：MLA 自动选择覆盖新硬件，降低接入门槛；DeepGEMM 签名兼容层降低引擎迁移成本。
- **性能天花板**：MoE 路由、GEMM、采样、attention 均在特定硬件形态下刷新性能记录，维持项目竞争地位。
- **硬件前瞻**：SM107 Rubin 支持收尾为下一代 GPU 预铺完整推理路径。

## 四、值得关注的技术点

跨硬件内核与框架契约的一致性维护、版本感知的编译器 DSL 适配模式、数值精确性约束下的性能优化方法论，以及架构门控审计的可复用性，均为多硬件平台项目提供了有价值的工程实践参考。

## 五、发展方向评估

FlashInfer 正沿着三条主线清晰演进：**扩大对主流 MoE 超大模型的原生内核覆盖**、**跟进最新 GPU 架构保持适配前沿性**、**在推理关键路径上持续内核级极致优化**。文档修复与 autotuner 修复表明项目在快速迭代的同时系统性提升工程健壮性。整体而言，FlashInfer 正从一个算子库向面向现代 MoE 大模型服务的**全栈推理加速平台**演进，其位精确验证、可回滚提交与严格测试证据，使项目从研究型内核库向可依赖的生产基础设施转型，并巩固了作为 vLLM 等推理框架底层算子首选的地位。

## 详细提交记录

### [d4b19b8](https://github.com/flashinfer-ai/flashinfer/commit/d4b19b87dec883dcdfc8ac9807bd5abbd1256e88)

- **作者**: eigen
- **时间**: 2026-10-05T23:38:06Z
- **提交信息**: feat(cake_warp_decode): cover the sharded Qwen3.5-397B TP2/TP4 and MiniMax-M2 TP2/TP4 slices (SM100 / SM103) (#6067)

# fused_moe: Cake warp-decode backend covers four sharded TP slices of
Qwen3.5-397B and MiniMax-M2

Extends the `backend="cake"` NVFP4 warp-decode portfolio
(`trtllm_fp4_block_scale_routed_moe` small-batch decode)
with four sharded per-partition SwiGLU geometries on SM100 and SM103,
`num_tokens` 1-32 each (256 new routes):

| geometry | hidden | intermediate | experts | top-k |
|---|---:|---:|---:|---:|
| Qwen3.5-397B TP2 | 4096 | 512 | 512 | 10 |
| Qwen3.5-397B TP4 | 4096 | 256 | 512 | 10 |
| MiniMax-M2 TP2 | 3072 | 768 | 256 | 8 |
| MiniMax-M2 TP4 | 3072 | 384 | 256 | 8 |

Every new row runs the fused route-pack schedule: persistent
device-workfeed FC1 with the route packer in its
prologue (no separate route-pack kernel), metadata-prefetch K256
device-workfeed FC2 (144 workfeed CTAs) and the
model-top-k packed finalizer; the SM100 clones stream their expert
weights with the L2 `evict_first` hint.

## Changes

- `csrc/fused_moe/warp_decode/cake_warp_decode_contract.cuh`: geometry
enum, `IsFusedRoutePackRow`,
`SelectSm100aSchedule` / `SelectSm103aSchedule` branches,
`CheckPublicBoundaries` and `static_assert` coverage.
- `csrc/fused_moe/warp_decode/generated/`: generated device programs and
the route inventory for the new rows
  (existing routes unchanged).
- `flashinfer/fused_moe/runners.py`, `flashinfer/fused_moe/api.py`,
`docs/api/fused_moe.rst`: supported-configuration
  list and documentation.
- `tests/moe/test_cake_warp_decode.py`: selector boundaries and GPU
parity rows for the new geometries;
  `benchmarks/cake_warp_decode.py`: benchmark geometries.

## Measurements

Cold-L2 CUPTI paired timing against the trtllm-gen path of
`trtllm_fp4_block_scale_routed_moe` on the same inputs,
32 token counts per geometry, outputs bitwise identical to the
trtllm-gen kernel. Speed-up (trtllm-gen time / Cake
time), min / median / max over `num_tokens` 1-32:

| arch | Q397 TP2 | Q397 TP4 | M2 TP2 | M2 TP4 |
|---|---|---|---|---|
| SM103 (GB300) | 1.108 / 1.158 / 1.254 | 1.096 / 1.128 / 1.205 | 1.104
/ 1.153 / 1.183 | 1.140 / 1.160 / 1.180 |
| SM100 (B200) | 1.104 / 1.154 / 1.218 | 1.093 / 1.128 / 1.179 | 1.099 /
1.141 / 1.177 | 1.121 / 1.145 / 1.168 |

All 256 new rows are faster than the trtllm-gen path on both
architectures. The generated files were produced by the Cake
exporter from one producer revision; the SM100 (B200) and SM103 (GB300)
export runs delivered byte-identical files (106-entry
listing, same SHA-256), and every row's exported module reproduces the
source module's timing within the protocol's
directional tolerance. The seven previously published geometries are
measured again in the same run as a report-only
reference and keep their kernels byte-identical to the current `main`.

In-model note (informational): driven from sglang's engine-side top-k
path on one 4x GB200 node, these slices currently
lose 15-25 % decode throughput against sglang's in-kernel-routing
TRT-LLM path. An official engine-routed reference
(`trtllm_fp4_block_scale_routed_moe` fed by the same engine top-k) runs
within 1-5 % of the Cake route on Qwen3.5-397B TP2
and is itself 8-18 % behind in-kernel routing there, so the gap is the
integration's routing path, not these programs;
the integration-side follow-up is tracked outside this PR.

## Tests

`tests/moe/test_cake_warp_decode.py` on the delivered tree: SM103
(GB300) 183 passed; SM100 (B200) 183 passed.
CPU-only rows (selector boundaries, `_SUPPORTED_CONFIGURATIONS`,
manifest checks) run without a GPU.


## Export measurement record

The tables below are the exporter's public summary for the two runs of
record (one per architecture). The SM103 record is complete; for SM100
the hardware stages and geomeans are shown and the per-shape table (480
rows, same layout) lives in the exporter summary artifact.

### SM103 run of record

## Generated-program export evidence

Baseline: **Production generated-program dispatcher** at Cake revision
`ed6cb1593ce482ae54a828dc06b899b942d5d86f`.

## Hardware stages

- `sm_103a` / world size `1`: GPUs `NVIDIA GB300`, capabilities `10.3`,
drivers `580.159.03`, UUIDs `GPU-f0fff0f5-f475-c7c1-5f03-49b613ce7618`;
120 shapes (named in the per-shape tables below).
- `sm_103a` / world size `1`: GPUs `NVIDIA GB300`, capabilities `10.3`,
drivers `580.159.03`, UUIDs `GPU-ef786da4-6295-6f7c-799a-4eb667abe785`;
120 shapes (named in the per-shape tables below).
- `sm_103a` / world size `1`: GPUs `NVIDIA GB300`, capabilities `10.3`,
drivers `580.159.03`, UUIDs `GPU-e4f092e8-91fe-a32f-f7e0-31d72bb2baa5`;
120 shapes (named in the per-shape tables below).
- `sm_103a` / world size `1`: GPUs `NVIDIA GB300`, capabilities `10.3`,
drivers `580.159.03`, UUIDs `GPU-8db1b5d6-5e68-edfe-18a0-633277da4cd7`;
120 shapes (named in the per-shape tables below).

Target revision: `ac30bfabfc40cca1971bea7a41ac10e6960d6bfd`.

Benchmark execution: `symmetric_external_cuda_graph_population_v1`; 3
counterbalanced groups, 50.000 ms warmup and 100.000 ms reportable
budget per arm/group.
Latency metric: CUPTI GPU span per sample, first compute-kernel start to
last compute-kernel end of one arm call (every kernel the call launches,
asynchronous copies excluded), after a cold-L2 flush before each
measured sample, with the SM clock held at or above 1900 MHz; the
reported value is the per-arm median. Each row's ``sm_clock_mhz_range``
in the summary JSON is the SM clock range observed while the row was
timed (group-boundary probes and, in the symmetric graph mode, every
sampled warmup/measurement phase).
Each sample follows one unmeasured same-arm launch, state restoration,
and a fresh cold-L2 flush.

The complete semantic arguments and machine-readable receipts remain in
`summary.json`; the table below retains every registered shape without
repeating those arguments, keys routes and external baselines against
the legends that follow it, and inlines each shape's external
comparison.

## Per-shape results

|Shape|GPU|Route|Source ms|Export ms|Source / Export|Baseline|Baseline
ms|Baseline / Export|Verdict|
|---|---|---|---:|---:|---:|---|---:|---:|---|

|sm103a_swiglu_e128_h2048_i768_k8_t01|G0|R3|0.015296|0.015392|0.9938x|B2|0.016768|1.0894x|pass|

|sm103a_swiglu_e128_h2048_i768_k8_t02|G1|R3|0.019520|0.019456|1.0033x|B2|0.021760|1.1184x|pass|

|sm103a_swiglu_e128_h2048_i768_k8_t03|G2|R3|0.023488|0.023680|0.9919x|B2|0.025376|1.0716x|pass|

|sm103a_swiglu_e128_h2048_i768_k8_t04|G3|R3|0.027104|0.026880|1.0083x|B2|0.028832|1.0726x|pass|

|sm103a_swiglu_e128_h2048_i768_k8_t05|G0|R3|0.030336|0.030272|1.0021x|B2|0.030304|1.0011x|pass|

|sm103a_swiglu_e128_h2048_i768_k8_t06|G1|R3|0.033280|0.033216|1.0019x|B2|0.033472|1.0077x|pass|

|sm103a_swiglu_e128_h2048_i768_k8_t07|G2|R3|0.036512|0.036544|0.9991x|B2|0.036928|1.0105x|pass|

|sm103a_swiglu_e128_h2048_i768_k8_t08|G3|R4|0.033536|0.033536|1.0000x|B2|0.038720|1.1546x|pass|

|sm103a_swiglu_e128_h2048_i768_k8_t09|G0|R4|0.035840|0.035937|0.9973x|B2|0.040928|1.1389x|pass|

|sm103a_swiglu_e128_h2048_i768_k8_t10|G1|R4|0.037152|0.037185|0.9991x|B2|0.042305|1.1377x|pass|

|sm103a_swiglu_e128_h2048_i768_k8_t11|G2|R4|0.038240|0.038272|0.9992x|B2|0.043584|1.1388x|pass|

|sm103a_swiglu_e128_h2048_i768_k8_t12|G3|R4|0.039392|0.039104|1.0074x|B2|0.044864|1.1473x|pass|

|sm103a_swiglu_e128_h2048_i768_k8_t13|G0|R4|0.040960|0.040992|0.9992x|B2|0.046880|1.1436x|pass|

|sm103a_swiglu_e128_h2048_i768_k8_t14|G1|R4|0.041344|0.041376|0.9992x|B2|0.047392|1.1454x|pass|

|sm103a_swiglu_e128_h2048_i768_k8_t15|G2|R4|0.042752|0.042720|1.0007x|B2|0.049536|1.1596x|pass|

|sm103a_swiglu_e128_h2048_i768_k8_t16|G3|R4|0.043648|0.043424|1.0052x|B2|0.050368|1.1599x|pass|

|sm103a_swiglu_e128_h2048_i768_k8_t17|G0|R4|0.044897|0.044768|1.0029x|B2|0.052160|1.1651x|pass|

|sm103a_swiglu_e128_h2048_i768_k8_t18|G1|R4|0.045984|0.045888|1.0021x|B2|0.053281|1.1611x|pass|

|sm103a_swiglu_e128_h2048_i768_k8_t19|G2|R4|0.046401|0.046272|1.0028x|B2|0.053568|1.1577x|pass|

|sm103a_swiglu_e128_h2048_i768_k8_t20|G3|R4|0.047456|0.047584|0.9973x|B2|0.054144|1.1379x|pass|

|sm103a_swiglu_e128_h2048_i768_k8_t21|G0|R4|0.048512|0.048736|0.9954x|B2|0.055361|1.1359x|pass|

|sm103a_swiglu_e128_h2048_i768_k8_t22|G1|R4|0.049792|0.049856|0.9987x|B2|0.056736|1.1380x|pass|

|sm103a_swiglu_e128_h2048_i768_k8_t23|G2|R4|0.049504|0.049664|0.9968x|B2|0.056544|1.1385x|pass|

|sm103a_swiglu_e128_h2048_i768_k8_t24|G3|R4|0.049696|0.049888|0.9962x|B2|0.057152|1.1456x|pass|

|sm103a_swiglu_e128_h2048_i768_k8_t25|G0|R4|0.051360|0.051456|0.9981x|B2|0.059072|1.1480x|pass|

|sm103a_swiglu_e128_h2048_i768_k8_t26|G1|R4|0.053024|0.052992|1.0006x|B2|0.060608|1.1437x|pass|

|sm103a_swiglu_e128_h2048_i768_k8_t27|G2|R4|0.053472|0.053504|0.9994x|B2|0.060864|1.1376x|pass|

|sm103a_swiglu_e128_h2048_i768_k8_t28|G3|R4|0.053824|0.054048|0.9959x|B2|0.061440|1.1368x|pass|

|sm103a_swiglu_e128_h2048_i768_k8_t29|G0|R4|0.054785|0.054752|1.0006x|B2|0.062848|1.1479x|pass|

|sm103a_swiglu_e128_h2048_i768_k8_t30|G1|R4|0.055136|0.055040|1.0017x|B2|0.063040|1.1453x|pass|

|sm103a_swiglu_e128_h2048_i768_k8_t31|G2|R4|0.056000|0.055904|1.0017x|B2|0.063776|1.1408x|pass|

|sm103a_swiglu_e128_h2048_i768_k8_t32|G3|R4|0.055936|0.056096|0.9971x|B2|0.064161|1.1438x|pass|

|sm103a_swiglu_e128_h4096_i1536_k8_t01|G0|R3|0.031969|0.031648|1.0101x|B2|0.039680|1.2538x|pass|

|sm103a_swiglu_e128_h4096_i1536_k8_t02|G1|R3|0.042272|0.042240|1.0008x|B2|0.063776|1.5098x|pass|

|sm103a_swiglu_e128_h4096_i1536_k8_t03|G2|R3|0.055872|0.055648|1.0040x|B2|0.084704|1.5221x|pass|

|sm103a_swiglu_e128_h4096_i1536_k8_t04|G3|R3|0.067712|0.067649|1.0009x|B2|0.101664|1.5028x|pass|

|sm103a_swiglu_e128_h4096_i1536_k8_t05|G0|R3|0.077345|0.077344|1.0000x|B2|0.117153|1.5147x|pass|

|sm103a_swiglu_e128_h4096_i1536_k8_t06|G1|R3|0.086976|0.087232|0.9971x|B2|0.135296|1.5510x|pass|

|sm103a_swiglu_e128_h4096_i1536_k8_t07|G2|R3|0.099488|0.099552|0.9994x|B2|0.155713|1.5641x|pass|

|sm103a_swiglu_e128_h4096_i1536_k8_t08|G3|R3|0.110592|0.110400|1.0017x|B2|0.166401|1.5073x|pass|

|sm103a_swiglu_e128_h4096_i1536_k8_t09|G0|R3|0.120705|0.120705|1.0000x|B2|0.178304|1.4772x|pass|

|sm103a_swiglu_e128_h4096_i1536_k8_t10|G1|R3|0.130113|0.129921|1.0015x|B2|0.186273|1.4337x|pass|

|sm103a_swiglu_e128_h4096_i1536_k8_t11|G2|R4|0.116256|0.116193|1.0005x|B2|0.194496|1.6739x|pass|

|sm103a_swiglu_e128_h4096_i1536_k8_t12|G3|R4|0.120704|0.120416|1.0024x|B2|0.202401|1.6808x|pass|

|sm103a_swiglu_e128_h4096_i1536_k8_t13|G0|R4|0.126560|0.126752|0.9985x|B2|0.213856|1.6872x|pass|

|sm103a_swiglu_e128_h4096_i1536_k8_t14|G1|R4|0.128160|0.128096|1.0005x|B2|0.216417|1.6895x|pass|

|sm103a_swiglu_e128_h4096_i1536_k8_t15|G2|R4|0.134048|0.133793|1.0019x|B2|0.227072|1.6972x|pass|

|sm103a_swiglu_e128_h4096_i1536_k8_t16|G3|R4|0.136640|0.136545|1.0007x|B2|0.232353|1.7017x|pass|

|sm103a_swiglu_e128_h4096_i1536_k8_t17|G0|R4|0.140896|0.140737|1.0011x|B2|0.241184|1.7137x|pass|

|sm103a_swiglu_e128_h4096_i1536_k8_t18|G1|R4|0.145120|0.144960|1.0011x|B2|0.249281|1.7197x|pass|

|sm103a_swiglu_e128_h4096_i1536_k8_t19|G2|R4|0.146688|0.146433|1.0017x|B2|0.251552|1.7179x|pass|

|sm103a_swiglu_e128_h4096_i1536_k8_t20|G3|R4|0.148064|0.147936|1.0009x|B2|0.254240|1.7186x|pass|

|sm103a_swiglu_e128_h4096_i1536_k8_t21|G0|R4|0.151072|0.150993|1.0005x|B2|0.259840|1.7209x|pass|

|sm103a_swiglu_e128_h4096_i1536_k8_t22|G1|R4|0.155456|0.155265|1.0012x|B2|0.267872|1.7253x|pass|

|sm103a_swiglu_e128_h4096_i1536_k8_t23|G2|R4|0.155713|0.155392|1.0021x|B2|0.267329|1.7204x|pass|

|sm103a_swiglu_e128_h4096_i1536_k8_t24|G3|R4|0.156864|0.156864|1.0000x|B2|0.270177|1.7224x|pass|

|sm103a_swiglu_e128_h4096_i1536_k8_t25|G0|R4|0.162720|0.162433|1.0018x|B2|0.280961|1.7297x|pass|

|sm103a_swiglu_e128_h4096_i1536_k8_t26|G1|R4|0.168352|0.168224|1.0008x|B2|0.292096|1.7364x|pass|

|sm103a_swiglu_e128_h4096_i1536_k8_t27|G2|R4|0.170209|0.169728|1.0028x|B2|0.294304|1.7340x|pass|

|sm103a_swiglu_e128_h4096_i1536_k8_t28|G3|R4|0.171392|0.171360|1.0002x|B2|0.296961|1.7330x|pass|

|sm103a_swiglu_e128_h4096_i1536_k8_t29|G0|R4|0.174432|0.174240|1.0011x|B2|0.302529|1.7363x|pass|

|sm103a_swiglu_e128_h4096_i1536_k8_t30|G1|R4|0.175840|0.175648|1.0011x|B2|0.305345|1.7384x|pass|

|sm103a_swiglu_e128_h4096_i1536_k8_t31|G2|R4|0.178849|0.178592|1.0014x|B2|0.310209|1.7370x|pass|

|sm103a_swiglu_e128_h4096_i1536_k8_t32|G3|R4|0.178624|0.178656|0.9998x|B2|0.310625|1.7387x|pass|

|sm103a_swiglu_e256_h2048_i512_k8_t01|G0|R3|0.013248|0.013280|0.9976x|B2|0.014624|1.1012x|pass|

|sm103a_swiglu_e256_h2048_i512_k8_t02|G1|R3|0.016096|0.016224|0.9921x|B2|0.018688|1.1519x|pass|

|sm103a_swiglu_e256_h2048_i512_k8_t03|G2|R3|0.020000|0.019936|1.0032x|B2|0.022144|1.1108x|pass|

|sm103a_swiglu_e256_h2048_i512_k8_t04|G3|R3|0.022432|0.022368|1.0029x|B2|0.024224|1.0830x|pass|

|sm103a_swiglu_e256_h2048_i512_k8_t05|G0|R3|0.025696|0.025761|0.9975x|B2|0.026592|1.0323x|pass|

|sm103a_swiglu_e256_h2048_i512_k8_t06|G1|R3|0.027680|0.027712|0.9988x|B2|0.029440|1.0624x|pass|

|sm103a_swiglu_e256_h2048_i512_k8_t07|G2|R3|0.030432|0.030144|1.0096x|B2|0.032512|1.0786x|pass|

|sm103a_swiglu_e256_h2048_i512_k8_t08|G3|R3|0.033376|0.033056|1.0097x|B2|0.035072|1.0610x|pass|

|sm103a_swiglu_e256_h2048_i512_k8_t09|G0|R3|0.035456|0.035521|0.9982x|B2|0.036992|1.0414x|pass|

|sm103a_swiglu_e256_h2048_i512_k8_t10|G1|R3|0.037280|0.037088|1.0052x|B2|0.038304|1.0328x|pass|

|sm103a_swiglu_e256_h2048_i512_k8_t11|G2|R3|0.039360|0.039008|1.0090x|B2|0.040385|1.0353x|pass|

|sm103a_swiglu_e256_h2048_i512_k8_t12|G3|R3|0.040800|0.040768|1.0008x|B2|0.041184|1.0102x|pass|

|sm103a_swiglu_e256_h2048_i512_k8_t13|G0|R3|0.042080|0.042080|1.0000x|B2|0.043200|1.0266x|pass|

|sm103a_swiglu_e256_h2048_i512_k8_t14|G1|R3|0.043585|0.043712|0.9971x|B2|0.044128|1.0095x|pass|

|sm103a_swiglu_e256_h2048_i512_k8_t15|G2|R4|0.044992|0.044928|1.0014x|B2|0.045568|1.0142x|pass|

|sm103a_swiglu_e256_h2048_i512_k8_t16|G3|R4|0.046016|0.045984|1.0007x|B2|0.046752|1.0167x|pass|

|sm103a_swiglu_e256_h2048_i512_k8_t17|G0|R4|0.047712|0.047680|1.0007x|B2|0.048960|1.0268x|pass|

|sm103a_swiglu_e256_h2048_i512_k8_t18|G1|R4|0.048640|0.048449|1.0039x|B2|0.049824|1.0284x|pass|

|sm103a_swiglu_e256_h2048_i512_k8_t19|G2|R4|0.049888|0.049920|0.9994x|B2|0.051296|1.0276x|pass|

|sm103a_swiglu_e256_h2048_i512_k8_t20|G3|R4|0.051136|0.051136|1.0000x|B2|0.052512|1.0269x|pass|

|sm103a_swiglu_e256_h2048_i512_k8_t21|G0|R4|0.052096|0.052096|1.0000x|B2|0.053280|1.0227x|pass|

|sm103a_swiglu_e256_h2048_i512_k8_t22|G1|R4|0.053424|0.053440|0.9997x|B2|0.054304|1.0162x|pass|

|sm103a_swiglu_e256_h2048_i512_k8_t23|G2|R4|0.054304|0.054336|0.9994x|B2|0.055392|1.0194x|pass|

|sm103a_swiglu_e256_h2048_i512_k8_t24|G3|R4|0.054848|0.054848|1.0000x|B2|0.055872|1.0187x|pass|

|sm103a_swiglu_e256_h2048_i512_k8_t25|G0|R4|0.056160|0.056064|1.0017x|B2|0.057440|1.0245x|pass|

|sm103a_swiglu_e256_h2048_i512_k8_t26|G1|R4|0.057696|0.057568|1.0022x|B2|0.058816|1.0217x|pass|

|sm103a_swiglu_e256_h2048_i512_k8_t27|G2|R4|0.058817|0.058752|1.0011x|B2|0.059776|1.0174x|pass|

|sm103a_swiglu_e256_h2048_i512_k8_t28|G3|R4|0.060288|0.060257|1.0005x|B2|0.061376|1.0186x|pass|

|sm103a_swiglu_e256_h2048_i512_k8_t29|G0|R4|0.061728|0.061792|0.9990x|B2|0.063297|1.0244x|pass|

|sm103a_swiglu_e256_h2048_i512_k8_t30|G1|R4|0.062912|0.063072|0.9975x|B2|0.064896|1.0289x|pass|

|sm103a_swiglu_e256_h2048_i512_k8_t31|G2|R4|0.064864|0.064992|0.9980x|B2|0.066656|1.0256x|pass|

|sm103a_swiglu_e256_h2048_i512_k8_t32|G3|R4|0.065632|0.065696|0.9990x|B2|0.067584|1.0287x|pass|

|sm103a_swiglu_e512_h4096_i1024_k10_t01|G0|R3|0.025312|0.025312|1.0000x|B2|0.027104|1.0708x|pass|

|sm103a_swiglu_e512_h4096_i1024_k10_t02|G1|R3|0.038336|0.038272|1.0017x|B2|0.040224|1.0510x|pass|

|sm103a_swiglu_e512_h4096_i1024_k10_t03|G2|R3|0.049952|0.049952|1.0000x|B2|0.052640|1.0538x|pass|

|sm103a_swiglu_e512_h4096_i1024_k10_t04|G3|R3|0.062336|0.062080|1.0041x|B2|0.064128|1.0330x|pass|

|sm103a_swiglu_e512_h4096_i1024_k10_t05|G0|R3|0.074593|0.074112|1.0065x|B2|0.075648|1.0207x|pass|

|sm103a_swiglu_e512_h4096_i1024_k10_t06|G1|R3|0.084320|0.084096|1.0027x|B2|0.086656|1.0304x|pass|

|sm103a_swiglu_e512_h4096_i1024_k10_t07|G2|R3|0.092640|0.092704|0.9993x|B2|0.093312|1.0066x|pass|

|sm103a_swiglu_e512_h4096_i1024_k10_t08|G3|R4|0.099872|0.100448|0.9943x|B2|0.101280|1.0083x|pass|

|sm103a_swiglu_e512_h4096_i1024_k10_t09|G0|R4|0.108256|0.108480|0.9979x|B2|0.110528|1.0189x|pass|

|sm103a_swiglu_e512_h4096_i1024_k10_t10|G1|R4|0.117216|0.117185|1.0003x|B2|0.119776|1.0221x|pass|

|sm103a_swiglu_e512_h4096_i1024_k10_t11|G2|R4|0.123456|0.123328|1.0010x|B2|0.125696|1.0192x|pass|

|sm103a_swiglu_e512_h4096_i1024_k10_t12|G3|R4|0.129505|0.129472|1.0003x|B2|0.131329|1.0143x|pass|

|sm103a_swiglu_e512_h4096_i1024_k10_t13|G0|R4|0.137505|0.137024|1.0035x|B2|0.139328|1.0168x|pass|

|sm103a_swiglu_e512_h4096_i1024_k10_t14|G1|R4|0.144736|0.144641|1.0007x|B2|0.147104|1.0170x|pass|

|sm103a_swiglu_e512_h4096_i1024_k10_t15|G2|R4|0.153760|0.153536|1.0015x|B2|0.156097|1.0167x|pass|

|sm103a_swiglu_e512_h4096_i1024_k10_t16|G3|R4|0.160929|0.161056|0.9992x|B2|0.163872|1.0175x|pass|

|sm103a_swiglu_e512_h4096_i1024_k10_t17|G0|R4|0.164384|0.164480|0.9994x|B2|0.170017|1.0337x|pass|

|sm103a_swiglu_e512_h4096_i1024_k10_t18|G1|R4|0.172673|0.172992|0.9982x|B2|0.178976|1.0346x|pass|

|sm103a_swiglu_e512_h4096_i1024_k10_t19|G2|R4|0.180608|0.180513|1.0005x|B2|0.186817|1.0349x|pass|

|sm103a_swiglu_e512_h4096_i1024_k10_t20|G3|R4|0.186017|0.186400|0.9979x|B2|0.192225|1.0312x|pass|

|sm103a_swiglu_e512_h4096_i1024_k10_t21|G0|R4|0.192289|0.191936|1.0018x|B2|0.197857|1.0308x|pass|

|sm103a_swiglu_e512_h4096_i1024_k10_t22|G1|R4|0.195905|0.196129|0.9989x|B2|0.201857|1.0292x|pass|

|sm103a_swiglu_e512_h4096_i1024_k10_t23|G2|R4|0.200705|0.200801|0.9995x|B2|0.207600|1.0339x|pass|

|sm103a_swiglu_e512_h4096_i1024_k10_t24|G3|R4|0.206241|0.206369|0.9994x|B2|0.212929|1.0318x|pass|

|sm103a_swiglu_e512_h4096_i1024_k10_t25|G0|R4|0.212225|0.212065|1.0008x|B2|0.218337|1.0296x|pass|

|sm103a_swiglu_e512_h4096_i1024_k10_t26|G1|R4|0.216929|0.216784|1.0007x|B2|0.223393|1.0305x|pass|

|sm103a_swiglu_e512_h4096_i1024_k10_t27|G2|R4|0.222081|0.222176|0.9996x|B2|0.228545|1.0287x|pass|

|sm103a_swiglu_e512_h4096_i1024_k10_t28|G3|R4|0.224673|0.224577|1.0004x|B2|0.231041|1.0288x|pass|

|sm103a_swiglu_e512_h4096_i1024_k10_t29|G0|R4|0.232577|0.232833|0.9989x|B2|0.238641|1.0249x|pass|

|sm103a_swiglu_e512_h4096_i1024_k10_t30|G1|R4|0.235233|0.235201|1.0001x|B2|0.241537|1.0269x|pass|

|sm103a_swiglu_e512_h4096_i1024_k10_t31|G2|R4|0.241249|0.241185|1.0003x|B2|0.247617|1.0267x|pass|

|sm103a_swiglu_e512_h4096_i1024_k10_t32|G3|R4|0.245921|0.245665|1.0010x|B2|0.251040|1.0219x|pass|

|sm103a_swiglu_e256_h3072_i1536_k8_t01|G0|R3|0.027488|0.027584|0.9965x|B2|0.033664|1.2204x|pass|

|sm103a_swiglu_e256_h3072_i1536_k8_t02|G1|R3|0.034464|0.034688|0.9935x|B2|0.052224|1.5055x|pass|

|sm103a_swiglu_e256_h3072_i1536_k8_t03|G2|R3|0.045952|0.045760|1.0042x|B2|0.070849|1.5483x|pass|

|sm103a_swiglu_e256_h3072_i1536_k8_t04|G3|R3|0.056832|0.056992|0.9972x|B2|0.088384|1.5508x|pass|

|sm103a_swiglu_e256_h3072_i1536_k8_t05|G0|R3|0.065696|0.065633|1.0010x|B2|0.101889|1.5524x|pass|

|sm103a_swiglu_e256_h3072_i1536_k8_t06|G1|R3|0.075265|0.075233|1.0004x|B2|0.119936|1.5942x|pass|

|sm103a_swiglu_e256_h3072_i1536_k8_t07|G2|R3|0.084577|0.084928|0.9959x|B2|0.137889|1.6236x|pass|

|sm103a_swiglu_e256_h3072_i1536_k8_t08|G3|R3|0.093856|0.093857|1.0000x|B2|0.152769|1.6277x|pass|

|sm103a_swiglu_e256_h3072_i1536_k8_t09|G0|R3|0.102592|0.102432|1.0016x|B2|0.167040|1.6307x|pass|

|sm103a_swiglu_e256_h3072_i1536_k8_t10|G1|R3|0.109089|0.109089|1.0000x|B2|0.175520|1.6090x|pass|

|sm103a_swiglu_e256_h3072_i1536_k8_t11|G2|R3|0.115969|0.115744|1.0019x|B2|0.188000|1.6243x|pass|

|sm103a_swiglu_e256_h3072_i1536_k8_t12|G3|R3|0.124096|0.123552|1.0044x|B2|0.193377|1.5651x|pass|

|sm103a_swiglu_e256_h3072_i1536_k8_t13|G0|R3|0.131537|0.131872|0.9975x|B2|0.205809|1.5607x|pass|

|sm103a_swiglu_e256_h3072_i1536_k8_t14|G1|R3|0.139073|0.139136|0.9995x|B2|0.212240|1.5254x|pass|

|sm103a_swiglu_e256_h3072_i1536_k8_t15|G2|R3|0.147617|0.147776|0.9989x|B2|0.219840|1.4877x|pass|

|sm103a_swiglu_e256_h3072_i1536_k8_t16|G3|R4|0.134976|0.134737|1.0018x|B2|0.227585|1.6891x|pass|

|sm103a_swiglu_e256_h3072_i1536_k8_t17|G0|R3|0.165024|0.164737|1.0017x|B2|0.238688|1.4489x|pass|

|sm103a_swiglu_e256_h3072_i1536_k8_t18|G1|R3|0.170976|0.171329|0.9979x|B2|0.244897|1.4294x|pass|

|sm103a_swiglu_e256_h3072_i1536_k8_t19|G2|R4|0.147616|0.147681|0.9996x|B2|0.252609|1.7105x|pass|

|sm103a_swiglu_e256_h3072_i1536_k8_t20|G3|R4|0.152192|0.151841|1.0023x|B2|0.260161|1.7134x|pass|

|sm103a_swiglu_e256_h3072_i1536_k8_t21|G0|R4|0.155361|0.155328|1.0002x|B2|0.266593|1.7163x|pass|

|sm103a_swiglu_e256_h3072_i1536_k8_t22|G1|R4|0.159329|0.159649|0.9980x|B2|0.274545|1.7197x|pass|

|sm103a_swiglu_e256_h3072_i1536_k8_t23|G2|R4|0.162816|0.163136|0.9980x|B2|0.280256|1.7179x|pass|

|sm103a_swiglu_e256_h3072_i1536_k8_t24|G3|R4|0.164865|0.164993|0.9992x|B2|0.283840|1.7203x|pass|

|sm103a_swiglu_e256_h3072_i1536_k8_t25|G0|R4|0.170432|0.170369|1.0004x|B2|0.293681|1.7238x|pass|

|sm103a_swiglu_e256_h3072_i1536_k8_t26|G1|R4|0.175712|0.175489|1.0013x|B2|0.304161|1.7332x|pass|

|sm103a_swiglu_e256_h3072_i1536_k8_t27|G2|R4|0.179329|0.179297|1.0002x|B2|0.309921|1.7285x|pass|

|sm103a_swiglu_e256_h3072_i1536_k8_t28|G3|R4|0.185665|0.185249|1.0022x|B2|0.321345|1.7347x|pass|

|sm103a_swiglu_e256_h3072_i1536_k8_t29|G0|R4|0.190785|0.190976|0.9990x|B2|0.331489|1.7358x|pass|

|sm103a_swiglu_e256_h3072_i1536_k8_t30|G1|R4|0.196097|0.196256|0.9992x|B2|0.341792|1.7416x|pass|

|sm103a_swiglu_e256_h3072_i1536_k8_t31|G2|R4|0.202848|0.202784|1.0003x|B2|0.353313|1.7423x|pass|

|sm103a_swiglu_e256_h3072_i1536_k8_t32|G3|R4|0.205793|0.206145|0.9983x|B2|0.359393|1.7434x|pass|

|sm103a_swiglu_e128_h6144_i3072_k4_t01|G0|R3|0.036896|0.036672|1.0061x|B2|0.037440|1.0209x|pass|

|sm103a_swiglu_e128_h6144_i3072_k4_t02|G1|R3|0.056737|0.056640|1.0017x|B2|0.057984|1.0237x|pass|

|sm103a_swiglu_e128_h6144_i3072_k4_t03|G2|R3|0.076288|0.076352|0.9992x|B2|0.079456|1.0407x|pass|

|sm103a_swiglu_e128_h6144_i3072_k4_t04|G3|R3|0.095744|0.096048|0.9968x|B2|0.097824|1.0185x|pass|

|sm103a_swiglu_e128_h6144_i3072_k4_t05|G0|R4|0.106048|0.105696|1.0033x|B2|0.105184|0.9952x|pass|

|sm103a_swiglu_e128_h6144_i3072_k4_t06|G1|R4|0.123105|0.123168|0.9995x|B2|0.124992|1.0148x|pass|

|sm103a_swiglu_e128_h6144_i3072_k4_t07|G2|R4|0.141121|0.140993|1.0009x|B2|0.142049|1.0075x|pass|

|sm103a_swiglu_e128_h6144_i3072_k4_t08|G3|R4|0.153696|0.153696|1.0000x|B2|0.154497|1.0052x|pass|

|sm103a_swiglu_e128_h6144_i3072_k4_t09|G0|R4|0.171457|0.171361|1.0006x|B2|0.172640|1.0075x|pass|

|sm103a_swiglu_e128_h6144_i3072_k4_t10|G1|R4|0.175616|0.175440|1.0010x|B2|0.177824|1.0136x|pass|

|sm103a_swiglu_e128_h6144_i3072_k4_t11|G2|R4|0.184577|0.184384|1.0010x|B2|0.186048|1.0090x|pass|

|sm103a_swiglu_e128_h6144_i3072_k4_t12|G3|R4|0.193440|0.192833|1.0031x|B2|0.194785|1.0101x|pass|

|sm103a_swiglu_e128_h6144_i3072_k4_t13|G0|R4|0.210113|0.209984|1.0006x|B2|0.212000|1.0096x|pass|

|sm103a_swiglu_e128_h6144_i3072_k4_t14|G1|R4|0.209824|0.209728|1.0005x|B2|0.211841|1.0101x|pass|

|sm103a_swiglu_e128_h6144_i3072_k4_t15|G2|R4|0.227168|0.227360|0.9992x|B2|0.229504|1.0094x|pass|

|sm103a_swiglu_e128_h6144_i3072_k4_t16|G3|R4|0.236033|0.235745|1.0012x|B2|0.238209|1.0105x|pass|

|sm103a_swiglu_e128_h6144_i3072_k4_t17|G0|R4|0.249153|0.248833|1.0013x|B2|0.250977|1.0086x|pass|

|sm103a_swiglu_e128_h6144_i3072_k4_t18|G1|R4|0.262049|0.261696|1.0013x|B2|0.263521|1.0070x|pass|

|sm103a_swiglu_e128_h6144_i3072_k4_t19|G2|R4|0.270848|0.270881|0.9999x|B2|0.272769|1.0070x|pass|

|sm103a_swiglu_e128_h6144_i3072_k4_t20|G3|R4|0.270529|0.270272|1.0010x|B2|0.272929|1.0098x|pass|

|sm103a_swiglu_e128_h6144_i3072_k4_t21|G0|R4|0.283745|0.283777|0.9999x|B2|0.285761|1.0070x|pass|

|sm103a_swiglu_e128_h6144_i3072_k4_t22|G1|R4|0.291585|0.291793|0.9993x|B2|0.294081|1.0078x|pass|

|sm103a_swiglu_e128_h6144_i3072_k4_t23|G2|R4|0.296609|0.296321|1.0010x|B2|0.298785|1.0083x|pass|

|sm103a_swiglu_e128_h6144_i3072_k4_t24|G3|R4|0.304929|0.304833|1.0003x|B2|0.307393|1.0084x|pass|

|sm103a_swiglu_e128_h6144_i3072_k4_t25|G0|R4|0.322049|0.322081|0.9999x|B2|0.324769|1.0083x|pass|

|sm103a_swiglu_e128_h6144_i3072_k4_t26|G1|R4|0.330113|0.330113|1.0000x|B2|0.332833|1.0082x|pass|

|sm103a_swiglu_e128_h6144_i3072_k4_t27|G2|R4|0.335041|0.335073|0.9999x|B2|0.337697|1.0078x|pass|

|sm103a_swiglu_e128_h6144_i3072_k4_t28|G3|R4|0.343617|0.344225|0.9982x|B2|0.346401|1.0063x|pass|

|sm103a_swiglu_e128_h6144_i3072_k4_t29|G0|R4|0.352481|0.352129|1.0010x|B2|0.354785|1.0075x|pass|

|sm103a_swiglu_e128_h6144_i3072_k4_t30|G1|R4|0.364993|0.365505|0.9986x|B2|0.367553|1.0056x|pass|

|sm103a_swiglu_e128_h6144_i3072_k4_t31|G2|R4|0.378497|0.378305|1.0005x|B2|0.380737|1.0064x|pass|

|sm103a_swiglu_e128_h6144_i3072_k4_t32|G3|R4|0.377889|0.378177|0.9992x|B2|0.380609|1.0064x|pass|

|sm103a_situ_e896_h3584_i3072_k16_t01|G0|R2|0.072545|0.072480|1.0009x|B2|0.110816|1.5289x|pass|

|sm103a_situ_e896_h3584_i3072_k16_t02|G1|R2|0.116001|0.116320|0.9973x|B2|0.195168|1.6779x|pass|

|sm103a_situ_e896_h3584_i3072_k16_t03|G2|R2|0.158256|0.158144|1.0007x|B2|0.284545|1.7993x|pass|

|sm103a_situ_e896_h3584_i3072_k16_t04|G3|R2|0.203744|0.203553|1.0009x|B2|0.368321|1.8095x|pass|

|sm103a_situ_e896_h3584_i3072_k16_t05|G0|R2|0.248528|0.247745|1.0032x|B2|0.447137|1.8048x|pass|

|sm103a_situ_e896_h3584_i3072_k16_t06|G1|R2|0.294096|0.293153|1.0032x|B2|0.532706|1.8172x|pass|

|sm103a_situ_e896_h3584_i3072_k16_t07|G2|R2|0.337921|0.337377|1.0016x|B2|0.612737|1.8162x|pass|

|sm103a_situ_e896_h3584_i3072_k16_t08|G3|R2|0.383681|0.382785|1.0023x|B2|0.690882|1.8049x|pass|

|sm103a_situ_e896_h3584_i3072_k16_t09|G0|R2|0.428385|0.427585|1.0019x|B2|0.768226|1.7967x|pass|

|sm103a_situ_e896_h3584_i3072_k16_t10|G1|R2|0.472769|0.472225|1.0012x|B2|0.846627|1.7928x|pass|

|sm103a_situ_e896_h3584_i3072_k16_t11|G2|R2|0.516833|0.516417|1.0008x|B2|0.928467|1.7979x|pass|

|sm103a_situ_e896_h3584_i3072_k16_t12|G3|R2|0.563297|0.562401|1.0016x|B2|1.010179|1.7962x|pass|

|sm103a_situ_e896_h3584_i3072_k16_t13|G0|R2|0.607857|0.607458|1.0007x|B2|1.070659|1.7625x|pass|

|sm103a_situ_e896_h3584_i3072_k16_t14|G1|R2|0.652065|0.652338|0.9996x|B2|1.154531|1.7698x|pass|

|sm103a_situ_e896_h3584_i3072_k16_t15|G2|R2|0.696290|0.696322|1.0000x|B2|1.231699|1.7689x|pass|

|sm103a_situ_e896_h3584_i3072_k16_t16|G3|R2|0.742882|0.741970|1.0012x|B2|1.303363|1.7566x|pass|

|sm103a_situ_e896_h3584_i3072_k16_t17|G0|R2|0.786226|0.786690|0.9994x|B2|1.359091|1.7276x|pass|

|sm103a_situ_e896_h3584_i3072_k16_t18|G1|R2|0.830514|0.831346|0.9990x|B2|1.407924|1.6935x|pass|

|sm103a_situ_e896_h3584_i3072_k16_t19|G2|R2|0.875139|0.875747|0.9993x|B2|1.463556|1.6712x|pass|

|sm103a_situ_e896_h3584_i3072_k16_t20|G3|R2|0.922627|0.921091|1.0017x|B2|1.511988|1.6415x|pass|

|sm103a_situ_e896_h3584_i3072_k16_t21|G0|R2|0.965987|0.966179|0.9998x|B2|1.566997|1.6218x|pass|

|sm103a_situ_e896_h3584_i3072_k16_t22|G1|R2|1.011842|1.010082|1.0017x|B2|1.631717|1.6154x|pass|

|sm103a_situ_e896_h3584_i3072_k16_t23|G2|R2|1.055395|1.054147|1.0012x|B2|1.697317|1.6101x|pass|

|sm103a_situ_e896_h3584_i3072_k16_t24|G3|R2|1.100803|1.100131|1.0006x|B2|1.752485|1.5930x|pass|

|sm103a_situ_e896_h3584_i3072_k16_t25|G0|R2|1.144803|1.144003|1.0007x|B2|1.781013|1.5568x|pass|

|sm103a_situ_e896_h3584_i3072_k16_t26|G1|R2|1.191524|1.189604|1.0016x|B2|1.844725|1.5507x|pass|

|sm103a_situ_e896_h3584_i3072_k16_t27|G2|R2|1.235107|1.234420|1.0006x|B2|1.895333|1.5354x|pass|

|sm103a_situ_e896_h3584_i3072_k16_t28|G3|R2|1.280147|1.280308|0.9999x|B2|1.950373|1.5234x|pass|

|sm103a_situ_e896_h3584_i3072_k16_t29|G0|R2|1.325844|1.324547|1.0010x|B2|1.996069|1.5070x|pass|

|sm103a_situ_e896_h3584_i3072_k16_t30|G1|R2|1.370516|1.370132|1.0003x|B2|2.038533|1.4878x|pass|

|sm103a_situ_e896_h3584_i3072_k16_t31|G2|R2|1.414116|1.414372|0.9998x|B2|2.079478|1.4702x|pass|

|sm103a_situ_e896_h3584_i3072_k16_t32|G3|R2|1.459540|1.460852|0.9991x|B2|2.135990|1.4622x|pass|

|sm103a_swiglu_e512_h4096_i512_k10_t01|G0|R4|0.017056|0.016769|1.0171x|B1|0.020032|1.1946x|pass|

|sm103a_swiglu_e512_h4096_i512_k10_t02|G1|R4|0.023040|0.022784|1.0112x|B1|0.028576|1.2542x|pass|

|sm103a_swiglu_e512_h4096_i512_k10_t03|G2|R4|0.027712|0.027584|1.0046x|B1|0.034432|1.2483x|pass|

|sm103a_swiglu_e512_h4096_i512_k10_t04|G3|R4|0.034208|0.034336|0.9963x|B1|0.041504|1.2088x|pass|

|sm103a_swiglu_e512_h4096_i512_k10_t05|G0|R4|0.038656|0.038752|0.9975x|B1|0.047072|1.2147x|pass|

|sm103a_swiglu_e512_h4096_i512_k10_t06|G1|R4|0.044928|0.044960|0.9993x|B1|0.053728|1.1950x|pass|

|sm103a_swiglu_e512_h4096_i512_k10_t07|G2|R4|0.047616|0.047969|0.9926x|B1|0.058304|1.2155x|pass|

|sm103a_swiglu_e512_h4096_i512_k10_t08|G3|R4|0.052288|0.052224|1.0012x|B1|0.062688|1.2004x|pass|

|sm103a_swiglu_e512_h4096_i512_k10_t09|G0|R4|0.056864|0.056960|0.9983x|B1|0.067744|1.1893x|pass|

|sm103a_swiglu_e512_h4096_i512_k10_t10|G1|R4|0.061984|0.062433|0.9928x|B1|0.073696|1.1804x|pass|

|sm103a_swiglu_e512_h4096_i512_k10_t11|G2|R4|0.064928|0.065248|0.9951x|B1|0.076992|1.1800x|pass|

|sm103a_swiglu_e512_h4096_i512_k10_t12|G3|R4|0.068864|0.068672|1.0028x|B1|0.079936|1.1640x|pass|

|sm103a_swiglu_e512_h4096_i512_k10_t13|G0|R4|0.072640|0.073121|0.9934x|B1|0.084544|1.1562x|pass|

|sm103a_swiglu_e512_h4096_i512_k10_t14|G1|R4|0.076673|0.077088|0.9946x|B1|0.088384|1.1465x|pass|

|sm103a_swiglu_e512_h4096_i512_k10_t15|G2|R4|0.081697|0.082080|0.9953x|B1|0.093568|1.1400x|pass|

|sm103a_swiglu_e512_h4096_i512_k10_t16|G3|R4|0.085984|0.086432|0.9948x|B1|0.097952|1.1333x|pass|

|sm103a_swiglu_e512_h4096_i512_k10_t17|G0|R4|0.087616|0.087520|1.0011x|B1|0.102849|1.1751x|pass|

|sm103a_swiglu_e512_h4096_i512_k10_t18|G1|R4|0.091904|0.092160|0.9972x|B1|0.107969|1.1715x|pass|

|sm103a_swiglu_e512_h4096_i512_k10_t19|G2|R4|0.096576|0.096448|1.0013x|B1|0.112256|1.1639x|pass|

|sm103a_swiglu_e512_h4096_i512_k10_t20|G3|R4|0.099712|0.099488|1.0023x|B1|0.115169|1.1576x|pass|

|sm103a_swiglu_e512_h4096_i512_k10_t21|G0|R4|0.102593|0.102400|1.0019x|B1|0.118080|1.1531x|pass|

|sm103a_swiglu_e512_h4096_i512_k10_t22|G1|R4|0.104865|0.104352|1.0049x|B1|0.120416|1.1539x|pass|

|sm103a_swiglu_e512_h4096_i512_k10_t23|G2|R4|0.107488|0.107009|1.0045x|B1|0.124033|1.1591x|pass|

|sm103a_swiglu_e512_h4096_i512_k10_t24|G3|R4|0.110176|0.110401|0.9980x|B1|0.126753|1.1481x|pass|

|sm103a_swiglu_e512_h4096_i512_k10_t25|G0|R4|0.113441|0.113248|1.0017x|B1|0.129248|1.1413x|pass|

|sm103a_swiglu_e512_h4096_i512_k10_t26|G1|R4|0.116384|0.116097|1.0025x|B1|0.131905|1.1362x|pass|

|sm103a_swiglu_e512_h4096_i512_k10_t27|G2|R4|0.119009|0.118688|1.0027x|B1|0.134752|1.1353x|pass|

|sm103a_swiglu_e512_h4096_i512_k10_t28|G3|R4|0.120320|0.120353|0.9997x|B1|0.136001|1.1300x|pass|

|sm103a_swiglu_e512_h4096_i512_k10_t29|G0|R4|0.124737|0.124513|1.0018x|B1|0.140001|1.1244x|pass|

|sm103a_swiglu_e512_h4096_i512_k10_t30|G1|R4|0.126016|0.125665|1.0028x|B1|0.141697|1.1276x|pass|

|sm103a_swiglu_e512_h4096_i512_k10_t31|G2|R4|0.129281|0.128864|1.0032x|B1|0.144832|1.1239x|pass|

|sm103a_swiglu_e512_h4096_i512_k10_t32|G3|R4|0.131585|0.131328|1.0020x|B1|0.145536|1.1082x|pass|

|sm103a_swiglu_e512_h4096_i256_k10_t01|G0|R4|0.014464|0.014848|0.9741x|B1|0.017409|1.1725x|pass|

|sm103a_swiglu_e512_h4096_i256_k10_t02|G1|R4|0.017472|0.017152|1.0187x|B1|0.020673|1.2053x|pass|

|sm103a_swiglu_e512_h4096_i256_k10_t03|G2|R4|0.020992|0.020928|1.0031x|B1|0.024641|1.1774x|pass|

|sm103a_swiglu_e512_h4096_i256_k10_t04|G3|R4|0.025152|0.025184|0.9987x|B1|0.029184|1.1588x|pass|

|sm103a_swiglu_e512_h4096_i256_k10_t05|G0|R4|0.028064|0.028128|0.9977x|B1|0.032704|1.1627x|pass|

|sm103a_swiglu_e512_h4096_i256_k10_t06|G1|R4|0.030945|0.030944|1.0000x|B1|0.036192|1.1696x|pass|

|sm103a_swiglu_e512_h4096_i256_k10_t07|G2|R4|0.033376|0.033504|0.9962x|B1|0.039136|1.1681x|pass|

|sm103a_swiglu_e512_h4096_i256_k10_t08|G3|R4|0.036896|0.037088|0.9948x|B1|0.041376|1.1156x|pass|

|sm103a_swiglu_e512_h4096_i256_k10_t09|G0|R4|0.039424|0.039360|1.0016x|B1|0.045408|1.1537x|pass|

|sm103a_swiglu_e512_h4096_i256_k10_t10|G1|R4|0.042240|0.042081|1.0038x|B1|0.048160|1.1445x|pass|

|sm103a_swiglu_e512_h4096_i256_k10_t11|G2|R4|0.044064|0.043776|1.0066x|B1|0.050112|1.1447x|pass|

|sm103a_swiglu_e512_h4096_i256_k10_t12|G3|R4|0.045856|0.045856|1.0000x|B1|0.051297|1.1187x|pass|

|sm103a_swiglu_e512_h4096_i256_k10_t13|G0|R4|0.048576|0.048320|1.0053x|B1|0.053888|1.1152x|pass|

|sm103a_swiglu_e512_h4096_i256_k10_t14|G1|R4|0.051072|0.051040|1.0006x|B1|0.056704|1.1110x|pass|

|sm103a_swiglu_e512_h4096_i256_k10_t15|G2|R4|0.054112|0.053792|1.0059x|B1|0.059648|1.1089x|pass|

|sm103a_swiglu_e512_h4096_i256_k10_t16|G3|R4|0.056384|0.056288|1.0017x|B1|0.061696|1.0961x|pass|

|sm103a_swiglu_e512_h4096_i256_k10_t17|G0|R4|0.057056|0.057184|0.9978x|B1|0.066272|1.1589x|pass|

|sm103a_swiglu_e512_h4096_i256_k10_t18|G1|R4|0.060065|0.060288|0.9963x|B1|0.069152|1.1470x|pass|

|sm103a_swiglu_e512_h4096_i256_k10_t19|G2|R4|0.062688|0.062784|0.9985x|B1|0.071392|1.1371x|pass|

|sm103a_swiglu_e512_h4096_i256_k10_t20|G3|R4|0.063904|0.064320|0.9935x|B1|0.072480|1.1269x|pass|

|sm103a_swiglu_e512_h4096_i256_k10_t21|G0|R4|0.066304|0.066432|0.9981x|B1|0.074304|1.1185x|pass|

|sm103a_swiglu_e512_h4096_i256_k10_t22|G1|R4|0.068001|0.067584|1.0062x|B1|0.076160|1.1269x|pass|

|sm103a_swiglu_e512_h4096_i256_k10_t23|G2|R4|0.069568|0.069184|1.0056x|B1|0.078945|1.1411x|pass|

|sm103a_swiglu_e512_h4096_i256_k10_t24|G3|R4|0.070528|0.070881|0.9950x|B1|0.080384|1.1341x|pass|

|sm103a_swiglu_e512_h4096_i256_k10_t25|G0|R4|0.072768|0.073024|0.9965x|B1|0.082400|1.1284x|pass|

|sm103a_swiglu_e512_h4096_i256_k10_t26|G1|R4|0.074368|0.074977|0.9919x|B1|0.084289|1.1242x|pass|

|sm103a_swiglu_e512_h4096_i256_k10_t27|G2|R4|0.076257|0.076320|0.9992x|B1|0.086112|1.1283x|pass|

|sm103a_swiglu_e512_h4096_i256_k10_t28|G3|R4|0.076320|0.077056|0.9904x|B1|0.086208|1.1188x|pass|

|sm103a_swiglu_e512_h4096_i256_k10_t29|G0|R4|0.080000|0.080000|1.0000x|B1|0.088704|1.1088x|pass|

|sm103a_swiglu_e512_h4096_i256_k10_t30|G1|R4|0.081152|0.080768|1.0048x|B1|0.089953|1.1137x|pass|

|sm103a_swiglu_e512_h4096_i256_k10_t31|G2|R4|0.083008|0.082688|1.0039x|B1|0.093056|1.1254x|pass|

|sm103a_swiglu_e512_h4096_i256_k10_t32|G3|R4|0.083776|0.083840|0.9992x|B1|0.092737|1.1061x|pass|

|sm103a_swiglu_e256_h3072_i768_k8_t01|G0|R4|0.015744|0.015808|0.9960x|B1|0.018560|1.1741x|pass|

|sm103a_swiglu_e256_h3072_i768_k8_t02|G1|R4|0.021568|0.022016|0.9797x|B1|0.025856|1.1744x|pass|

|sm103a_swiglu_e256_h3072_i768_k8_t03|G2|R4|0.027072|0.027072|1.0000x|B1|0.031936|1.1797x|pass|

|sm103a_swiglu_e256_h3072_i768_k8_t04|G3|R4|0.031489|0.031392|1.0031x|B1|0.037568|1.1967x|pass|

|sm103a_swiglu_e256_h3072_i768_k8_t05|G0|R4|0.035520|0.035392|1.0036x|B1|0.042144|1.1908x|pass|

|sm103a_swiglu_e256_h3072_i768_k8_t06|G1|R4|0.040096|0.040320|0.9944x|B1|0.047552|1.1794x|pass|

|sm103a_swiglu_e256_h3072_i768_k8_t07|G2|R4|0.044928|0.045056|0.9972x|B1|0.053216|1.1811x|pass|

|sm103a_swiglu_e256_h3072_i768_k8_t08|G3|R4|0.049440|0.049600|0.9968x|B1|0.058208|1.1735x|pass|

|sm103a_swiglu_e256_h3072_i768_k8_t09|G0|R4|0.053696|0.053728|0.9994x|B1|0.062272|1.1590x|pass|

|sm103a_swiglu_e256_h3072_i768_k8_t10|G1|R4|0.056032|0.056032|1.0000x|B1|0.065120|1.1622x|pass|

|sm103a_swiglu_e256_h3072_i768_k8_t11|G2|R4|0.059360|0.059520|0.9973x|B1|0.069313|1.1645x|pass|

|sm103a_swiglu_e256_h3072_i768_k8_t12|G3|R4|0.061600|0.061440|1.0026x|B1|0.070752|1.1516x|pass|

|sm103a_swiglu_e256_h3072_i768_k8_t13|G0|R4|0.064672|0.065153|0.9926x|B1|0.075392|1.1572x|pass|

|sm103a_swiglu_e256_h3072_i768_k8_t14|G1|R4|0.066497|0.066912|0.9938x|B1|0.077248|1.1545x|pass|

|sm103a_swiglu_e256_h3072_i768_k8_t15|G2|R4|0.068928|0.069121|0.9972x|B1|0.079889|1.1558x|pass|

|sm103a_swiglu_e256_h3072_i768_k8_t16|G3|R4|0.071104|0.071201|0.9986x|B1|0.081824|1.1492x|pass|

|sm103a_swiglu_e256_h3072_i768_k8_t17|G0|R4|0.074112|0.074016|1.0013x|B1|0.085792|1.1591x|pass|

|sm103a_swiglu_e256_h3072_i768_k8_t18|G1|R4|0.075873|0.075585|1.0038x|B1|0.087488|1.1575x|pass|

|sm103a_swiglu_e256_h3072_i768_k8_t19|G2|R4|0.078016|0.077952|1.0008x|B1|0.089952|1.1539x|pass|

|sm103a_swiglu_e256_h3072_i768_k8_t20|G3|R4|0.080545|0.080416|1.0016x|B1|0.091520|1.1381x|pass|

|sm103a_swiglu_e256_h3072_i768_k8_t21|G0|R4|0.082369|0.082145|1.0027x|B1|0.093696|1.1406x|pass|

|sm103a_swiglu_e256_h3072_i768_k8_t22|G1|R4|0.084193|0.084192|1.0000x|B1|0.095936|1.1395x|pass|

|sm103a_swiglu_e256_h3072_i768_k8_t23|G2|R4|0.086049|0.086017|1.0004x|B1|0.097792|1.1369x|pass|

|sm103a_swiglu_e256_h3072_i768_k8_t24|G3|R4|0.087840|0.087648|1.0022x|B1|0.098432|1.1230x|pass|

|sm103a_swiglu_e256_h3072_i768_k8_t25|G0|R4|0.089984|0.090304|0.9965x|B1|0.101345|1.1223x|pass|

|sm103a_swiglu_e256_h3072_i768_k8_t26|G1|R4|0.092672|0.093088|0.9955x|B1|0.104224|1.1196x|pass|

|sm103a_swiglu_e256_h3072_i768_k8_t27|G2|R4|0.094432|0.094816|0.9960x|B1|0.106145|1.1195x|pass|

|sm103a_swiglu_e256_h3072_i768_k8_t28|G3|R4|0.098592|0.098304|1.0029x|B1|0.109505|1.1139x|pass|

|sm103a_swiglu_e256_h3072_i768_k8_t29|G0|R4|0.100993|0.101152|0.9984x|B1|0.112641|1.1136x|pass|

|sm103a_swiglu_e256_h3072_i768_k8_t30|G1|R4|0.103424|0.103936|0.9951x|B1|0.115713|1.1133x|pass|

|sm103a_swiglu_e256_h3072_i768_k8_t31|G2|R4|0.107009|0.107328|0.9970x|B1|0.119073|1.1094x|pass|

|sm103a_swiglu_e256_h3072_i768_k8_t32|G3|R4|0.109601|0.109440|1.0015x|B1|0.120544|1.1015x|pass|

|sm103a_swiglu_e256_h3072_i384_k8_t01|G0|R4|0.013600|0.013824|0.9838x|B1|0.015872|1.1481x|pass|

|sm103a_swiglu_e256_h3072_i384_k8_t02|G1|R4|0.016832|0.016768|1.0038x|B1|0.019488|1.1622x|pass|

|sm103a_swiglu_e256_h3072_i384_k8_t03|G2|R4|0.019904|0.020096|0.9904x|B1|0.023040|1.1465x|pass|

|sm103a_swiglu_e256_h3072_i384_k8_t04|G3|R4|0.022496|0.022432|1.0029x|B1|0.026048|1.1612x|pass|

|sm103a_swiglu_e256_h3072_i384_k8_t05|G0|R4|0.024448|0.024480|0.9987x|B1|0.028576|1.1673x|pass|

|sm103a_swiglu_e256_h3072_i384_k8_t06|G1|R4|0.027392|0.027552|0.9942x|B1|0.031840|1.1556x|pass|

|sm103a_swiglu_e256_h3072_i384_k8_t07|G2|R4|0.030400|0.030432|0.9989x|B1|0.035680|1.1725x|pass|

|sm103a_swiglu_e256_h3072_i384_k8_t08|G3|R4|0.032192|0.032096|1.0030x|B1|0.037888|1.1805x|pass|

|sm103a_swiglu_e256_h3072_i384_k8_t09|G0|R4|0.034593|0.034720|0.9963x|B1|0.040225|1.1586x|pass|

|sm103a_swiglu_e256_h3072_i384_k8_t10|G1|R4|0.036064|0.036000|1.0018x|B1|0.041504|1.1529x|pass|

|sm103a_swiglu_e256_h3072_i384_k8_t11|G2|R4|0.037697|0.037984|0.9924x|B1|0.044096|1.1609x|pass|

|sm103a_swiglu_e256_h3072_i384_k8_t12|G3|R4|0.039008|0.039104|0.9975x|B1|0.044800|1.1457x|pass|

|sm103a_swiglu_e256_h3072_i384_k8_t13|G0|R4|0.040576|0.040736|0.9961x|B1|0.047200|1.1587x|pass|

|sm103a_swiglu_e256_h3072_i384_k8_t14|G1|R4|0.041440|0.041472|0.9992x|B1|0.048128|1.1605x|pass|

|sm103a_swiglu_e256_h3072_i384_k8_t15|G2|R4|0.042624|0.042656|0.9992x|B1|0.049824|1.1680x|pass|

|sm103a_swiglu_e256_h3072_i384_k8_t16|G3|R4|0.044416|0.044128|1.0065x|B1|0.050880|1.1530x|pass|

|sm103a_swiglu_e256_h3072_i384_k8_t17|G0|R4|0.045472|0.045632|0.9965x|B1|0.053600|1.1746x|pass|

|sm103a_swiglu_e256_h3072_i384_k8_t18|G1|R4|0.046432|0.046592|0.9966x|B1|0.054496|1.1696x|pass|

|sm103a_swiglu_e256_h3072_i384_k8_t19|G2|R4|0.047585|0.047552|1.0007x|B1|0.055713|1.1716x|pass|

|sm103a_swiglu_e256_h3072_i384_k8_t20|G3|R4|0.048961|0.049056|0.9981x|B1|0.057056|1.1631x|pass|

|sm103a_swiglu_e256_h3072_i384_k8_t21|G0|R4|0.050240|0.050113|1.0025x|B1|0.058208|1.1615x|pass|

|sm103a_swiglu_e256_h3072_i384_k8_t22|G1|R4|0.051200|0.051264|0.9988x|B1|0.059872|1.1679x|pass|

|sm103a_swiglu_e256_h3072_i384_k8_t23|G2|R4|0.051649|0.051904|0.9951x|B1|0.060768|1.1708x|pass|

|sm103a_swiglu_e256_h3072_i384_k8_t24|G3|R4|0.052576|0.052192|1.0074x|B1|0.061184|1.1723x|pass|

|sm103a_swiglu_e256_h3072_i384_k8_t25|G0|R4|0.053984|0.054112|0.9976x|B1|0.062752|1.1597x|pass|

|sm103a_swiglu_e256_h3072_i384_k8_t26|G1|R4|0.055712|0.055761|0.9991x|B1|0.064032|1.1483x|pass|

|sm103a_swiglu_e256_h3072_i384_k8_t27|G2|R4|0.056704|0.056704|1.0000x|B1|0.065281|1.1513x|pass|

|sm103a_swiglu_e256_h3072_i384_k8_t28|G3|R4|0.058784|0.058368|1.0071x|B1|0.067296|1.1530x|pass|

|sm103a_swiglu_e256_h3072_i384_k8_t29|G0|R4|0.060064|0.060320|0.9958x|B1|0.069280|1.1485x|pass|

|sm103a_swiglu_e256_h3072_i384_k8_t30|G1|R4|0.061568|0.061889|0.9948x|B1|0.070816|1.1442x|pass|

|sm103a_swiglu_e256_h3072_i384_k8_t31|G2|R4|0.063264|0.063584|0.9950x|B1|0.072672|1.1429x|pass|

|sm103a_swiglu_e256_h3072_i384_k8_t32|G3|R4|0.064417|0.064321|1.0015x|B1|0.073344|1.1403x|pass|

|sm103a_swiglu_e512_h2048_i512_k10_t01|G0|R3|0.015296|0.014976|1.0214x|—|—|—|pass|

|sm103a_swiglu_e512_h2048_i512_k10_t02|G1|R3|0.018720|0.018592|1.0069x|—|—|—|pass|

|sm103a_swiglu_e512_h2048_i512_k10_t03|G2|R3|0.021792|0.021728|1.0029x|—|—|—|pass|

|sm103a_swiglu_e512_h2048_i512_k10_t04|G3|R3|0.026528|0.026401|1.0048x|—|—|—|pass|

|sm103a_swiglu_e512_h2048_i512_k10_t05|G0|R3|0.029024|0.029473|0.9848x|—|—|—|pass|

|sm103a_swiglu_e512_h2048_i512_k10_t06|G1|R3|0.032672|0.032768|0.9971x|—|—|—|pass|

|sm103a_swiglu_e512_h2048_i512_k10_t07|G2|R3|0.035808|0.035904|0.9973x|—|—|—|pass|

|sm103a_swiglu_e512_h2048_i512_k10_t08|G3|R3|0.037984|0.037824|1.0042x|—|—|—|pass|

|sm103a_swiglu_e512_h2048_i512_k10_t09|G0|R3|0.040864|0.040545|1.0079x|—|—|—|pass|

|sm103a_swiglu_e512_h2048_i512_k10_t10|G1|R3|0.043552|0.043456|1.0022x|—|—|—|pass|

|sm103a_swiglu_e512_h2048_i512_k10_t11|G2|R3|0.045921|0.046112|0.9958x|—|—|—|pass|

|sm103a_swiglu_e512_h2048_i512_k10_t12|G3|R3|0.048064|0.047840|1.0047x|—|—|—|pass|

|sm103a_swiglu_e512_h2048_i512_k10_t13|G0|R3|0.050528|0.050592|0.9987x|—|—|—|pass|

|sm103a_swiglu_e512_h2048_i512_k10_t14|G1|R3|0.052992|0.053440|0.9916x|—|—|—|pass|

|sm103a_swiglu_e512_h2048_i512_k10_t15|G2|R3|0.055712|0.055840|0.9977x|—|—|—|pass|

|sm103a_swiglu_e512_h2048_i512_k10_t16|G3|R3|0.058624|0.058528|1.0016x|—|—|—|pass|

|sm103a_swiglu_e512_h2048_i512_k10_t17|G0|R3|0.060097|0.060321|0.9963x|—|—|—|pass|

|sm103a_swiglu_e512_h2048_i512_k10_t18|G1|R3|0.062528|0.062881|0.9944x|—|—|—|pass|

|sm103a_swiglu_e512_h2048_i512_k10_t19|G2|R3|0.064864|0.065376|0.9922x|—|—|—|pass|

|sm103a_swiglu_e512_h2048_i512_k10_t20|G3|R3|0.067072|0.067040|1.0005x|—|—|—|pass|

|sm103a_swiglu_e512_h2048_i512_k10_t21|G0|R3|0.069329|0.069153|1.0025x|—|—|—|pass|

|sm103a_swiglu_e512_h2048_i512_k10_t22|G1|R3|0.071297|0.070945|1.0050x|—|—|—|pass|

|sm103a_swiglu_e512_h2048_i512_k10_t23|G2|R4|0.070369|0.070272|1.0014x|—|—|—|pass|

|sm103a_swiglu_e512_h2048_i512_k10_t24|G3|R4|0.071776|0.072000|0.9969x|—|—|—|pass|

|sm103a_swiglu_e512_h2048_i512_k10_t25|G0|R4|0.073696|0.073313|1.0052x|—|—|—|pass|

|sm103a_swiglu_e512_h2048_i512_k10_t26|G1|R4|0.075104|0.074945|1.0021x|—|—|—|pass|

|sm103a_swiglu_e512_h2048_i512_k10_t27|G2|R4|0.076321|0.076288|1.0004x|—|—|—|pass|

|sm103a_swiglu_e512_h2048_i512_k10_t28|G3|R4|0.076992|0.077024|0.9996x|—|—|—|pass|

|sm103a_swiglu_e512_h2048_i512_k10_t29|G0|R4|0.079553|0.079201|1.0044x|—|—|—|pass|

|sm103a_swiglu_e512_h2048_i512_k10_t30|G1|R4|0.080289|0.080096|1.0024x|—|—|—|pass|

|sm103a_swiglu_e512_h2048_i512_k10_t31|G2|R4|0.081952|0.081728|1.0027x|—|—|—|pass|

|sm103a_swiglu_e512_h2048_i512_k10_t32|G3|R4|0.082816|0.082688|1.0015x|—|—|—|pass|

|sm103a_swiglu_e60_h2048_i1536_k4_t01|G0|R3|0.012928|0.013088|0.9878x|—|—|—|pass|

|sm103a_swiglu_e60_h2048_i1536_k4_t02|G1|R3|0.017376|0.017472|0.9945x|—|—|—|pass|

|sm103a_swiglu_e60_h2048_i1536_k4_t03|G2|R3|0.022528|0.022304|1.0100x|—|—|—|pass|

|sm103a_swiglu_e60_h2048_i1536_k4_t04|G3|R3|0.025952|0.025601|1.0137x|—|—|—|pass|

|sm103a_swiglu_e60_h2048_i1536_k4_t05|G0|R3|0.029472|0.029632|0.9946x|—|—|—|pass|

|sm103a_swiglu_e60_h2048_i1536_k4_t06|G1|R3|0.031392|0.031392|1.0000x|—|—|—|pass|

|sm103a_swiglu_e60_h2048_i1536_k4_t07|G2|R3|0.033760|0.033664|1.0029x|—|—|—|pass|

|sm103a_swiglu_e60_h2048_i1536_k4_t08|G3|R3|0.036449|0.036033|1.0115x|—|—|—|pass|

|sm103a_swiglu_e60_h2048_i1536_k4_t09|G0|R3|0.038624|0.038368|1.0067x|—|—|—|pass|

|sm103a_swiglu_e60_h2048_i1536_k4_t10|G1|R3|0.040737|0.040736|1.0000x|—|—|—|pass|

|sm103a_swiglu_e60_h2048_i1536_k4_t11|G2|R4|0.043392|0.043168|1.0052x|—|—|—|pass|

|sm103a_swiglu_e60_h2048_i1536_k4_t12|G3|R4|0.045920|0.045536|1.0084x|—|—|—|pass|

|sm103a_swiglu_e60_h2048_i1536_k4_t13|G0|R4|0.046401|0.045984|1.0091x|—|—|—|pass|

|sm103a_swiglu_e60_h2048_i1536_k4_t14|G1|R4|0.048928|0.048929|1.0000x|—|—|—|pass|

|sm103a_swiglu_e60_h2048_i1536_k4_t15|G2|R4|0.051072|0.051169|0.9981x|—|—|—|pass|

|sm103a_swiglu_e60_h2048_i1536_k4_t16|G3|R4|0.051840|0.051648|1.0037x|—|—|—|pass|

|sm103a_swiglu_e60_h2048_i1536_k4_t17|G0|R4|0.052800|0.052641|1.0030x|—|—|—|pass|

|sm103a_swiglu_e60_h2048_i1536_k4_t18|G1|R4|0.052768|0.052576|1.0037x|—|—|—|pass|

|sm103a_swiglu_e60_h2048_i1536_k4_t19|G2|R4|0.052800|0.053089|0.9946x|—|—|—|pass|

|sm103a_swiglu_e60_h2048_i1536_k4_t20|G3|R4|0.053472|0.053601|0.9976x|—|—|—|pass|

|sm103a_swiglu_e60_h2048_i1536_k4_t21|G0|R4|0.055649|0.055329|1.0058x|—|—|—|pass|

|sm103a_swiglu_e60_h2048_i1536_k4_t22|G1|R4|0.055584|0.055265|1.0058x|—|—|—|pass|

|sm103a_swiglu_e60_h2048_i1536_k4_t23|G2|R4|0.055648|0.055552|1.0017x|—|—|—|pass|

|sm103a_swiglu_e60_h2048_i1536_k4_t24|G3|R4|0.056321|0.056256|1.0012x|—|—|—|pass|

|sm103a_swiglu_e60_h2048_i1536_k4_t25|G0|R4|0.057792|0.057504|1.0050x|—|—|—|pass|

|sm103a_swiglu_e60_h2048_i1536_k4_t26|G1|R4|0.058945|0.059072|0.9979x|—|—|—|pass|

|sm103a_swiglu_e60_h2048_i1536_k4_t27|G2|R4|0.060768|0.060608|1.0026x|—|—|—|pass|

|sm103a_swiglu_e60_h2048_i1536_k4_t28|G3|R4|0.061440|0.061216|1.0037x|—|—|—|pass|

|sm103a_swiglu_e60_h2048_i1536_k4_t29|G0|R4|0.061504|0.061728|0.9964x|—|—|—|pass|

|sm103a_swiglu_e60_h2048_i1536_k4_t30|G1|R4|0.062337|0.062464|0.9980x|—|—|—|pass|

|sm103a_swiglu_e60_h2048_i1536_k4_t31|G2|R4|0.062336|0.062272|1.0010x|—|—|—|pass|

|sm103a_swiglu_e60_h2048_i1536_k4_t32|G3|R4|0.062240|0.062081|1.0026x|—|—|—|pass|

|sm103a_swiglu_e384_h2560_i768_k4_t01|G0|R3|0.013184|0.013280|0.9928x|—|—|—|pass|

|sm103a_swiglu_e384_h2560_i768_k4_t02|G1|R3|0.015136|0.015072|1.0042x|—|—|—|pass|

|sm103a_swiglu_e384_h2560_i768_k4_t03|G2|R3|0.017824|0.018176|0.9806x|—|—|—|pass|

|sm103a_swiglu_e384_h2560_i768_k4_t04|G3|R3|0.020704|0.020992|0.9863x|—|—|—|pass|

|sm103a_swiglu_e384_h2560_i768_k4_t05|G0|R3|0.023456|0.023328|1.0055x|—|—|—|pass|

|sm103a_swiglu_e384_h2560_i768_k4_t06|G1|R3|0.026240|0.026016|1.0086x|—|—|—|pass|

|sm103a_swiglu_e384_h2560_i768_k4_t07|G2|R3|0.029153|0.029312|0.9946x|—|—|—|pass|

|sm103a_swiglu_e384_h2560_i768_k4_t08|G3|R3|0.031201|0.031072|1.0042x|—|—|—|pass|

|sm103a_swiglu_e384_h2560_i768_k4_t09|G0|R3|0.034016|0.034080|0.9981x|—|—|—|pass|

|sm103a_swiglu_e384_h2560_i768_k4_t10|G1|R3|0.035840|0.035744|1.0027x|—|—|—|pass|

|sm103a_swiglu_e384_h2560_i768_k4_t11|G2|R3|0.038400|0.038432|0.9992x|—|—|—|pass|

|sm103a_swiglu_e384_h2560_i768_k4_t12|G3|R3|0.039552|0.039520|1.0008x|—|—|—|pass|

|sm103a_swiglu_e384_h2560_i768_k4_t13|G0|R3|0.041856|0.042016|0.9962x|—|—|—|pass|

|sm103a_swiglu_e384_h2560_i768_k4_t14|G1|R3|0.043584|0.043392|1.0044x|—|—|—|pass|

|sm103a_swiglu_e384_h2560_i768_k4_t15|G2|R3|0.045568|0.045920|0.9923x|—|—|—|pass|

|sm103a_swiglu_e384_h2560_i768_k4_t16|G3|R3|0.046689|0.046784|0.9980x|—|—|—|pass|

|sm103a_swiglu_e384_h2560_i768_k4_t17|G0|R3|0.048768|0.049088|0.9935x|—|—|—|pass|

|sm103a_swiglu_e384_h2560_i768_k4_t18|G1|R3|0.050208|0.050432|0.9956x|—|—|—|pass|

|sm103a_swiglu_e384_h2560_i768_k4_t19|G2|R3|0.052416|0.052352|1.0012x|—|—|—|pass|

|sm103a_swiglu_e384_h2560_i768_k4_t20|G3|R3|0.053665|0.053696|0.9994x|—|—|—|pass|

|sm103a_swiglu_e384_h2560_i768_k4_t21|G0|R3|0.056000|0.056128|0.9977x|—|—|—|pass|

|sm103a_swiglu_e384_h2560_i768_k4_t22|G1|R3|0.058048|0.058272|0.9962x|—|—|—|pass|

|sm103a_swiglu_e384_h2560_i768_k4_t23|G2|R3|0.060640|0.060608|1.0005x|—|—|—|pass|

|sm103a_swiglu_e384_h2560_i768_k4_t24|G3|R3|0.061472|0.061504|0.9995x|—|—|—|pass|

|sm103a_swiglu_e384_h2560_i768_k4_t25|G0|R3|0.063489|0.063648|0.9975x|—|—|—|pass|

|sm103a_swiglu_e384_h2560_i768_k4_t26|G1|R3|0.065248|0.065408|0.9976x|—|—|—|pass|

|sm103a_swiglu_e384_h2560_i768_k4_t27|G2|R3|0.067168|0.067104|1.0010x|—|—|—|pass|

|sm103a_swiglu_e384_h2560_i768_k4_t28|G3|R3|0.068224|0.068096|1.0019x|—|—|—|pass|

|sm103a_swiglu_e384_h2560_i768_k4_t29|G0|R3|0.070144|0.070176|0.9995x|—|—|—|pass|

|sm103a_swiglu_e384_h2560_i768_k4_t30|G1|R3|0.071265|0.071456|0.9973x|—|—|—|pass|

|sm103a_swiglu_e384_h2560_i768_k4_t31|G2|R3|0.072833|0.072913|0.9989x|—|—|—|pass|

|sm103a_swiglu_e384_h2560_i768_k4_t32|G3|R3|0.073856|0.073633|1.0030x|—|—|—|pass|

|sm103a_silu_e192_h6144_i1536_k4_t01|G0|R1|0.020608|0.020992|0.9817x|—|—|—|pass|

|sm103a_silu_e192_h6144_i1536_k4_t02|G1|R1|0.027648|0.027680|0.9988x|—|—|—|pass|

|sm103a_silu_e192_h6144_i1536_k4_t03|G2|R1|0.034657|0.033696|1.0285x|—|—|—|pass|

|sm103a_silu_e192_h6144_i1536_k4_t04|G3|R1|0.042529|0.042368|1.0038x|—|—|—|pass|

|sm103a_silu_e192_h6144_i1536_k4_t05|G0|R1|0.048832|0.048512|1.0066x|—|—|—|pass|

|sm103a_silu_e192_h6144_i1536_k4_t06|G1|R1|0.055808|0.055777|1.0006x|—|—|—|pass|

|sm103a_silu_e192_h6144_i1536_k4_t07|G2|R1|0.063584|0.063840|0.9960x|—|—|—|pass|

|sm103a_silu_e192_h6144_i1536_k4_t08|G3|R1|0.069697|0.069760|0.9991x|—|—|—|pass|

|sm103a_silu_e192_h6144_i1536_k4_t09|G0|R1|0.075456|0.075424|1.0004x|—|—|—|pass|

|sm103a_silu_e192_h6144_i1536_k4_t10|G1|R1|0.081568|0.081505|1.0008x|—|—|—|pass|

|sm103a_silu_e192_h6144_i1536_k4_t11|G2|R1|0.087073|0.087072|1.0000x|—|—|—|pass|

|sm103a_silu_e192_h6144_i1536_k4_t12|G3|R1|0.093760|0.093760|1.0000x|—|—|—|pass|

|sm103a_silu_e192_h6144_i1536_k4_t13|G0|R1|0.098881|0.099040|0.9984x|—|—|—|pass|

|sm103a_silu_e192_h6144_i1536_k4_t14|G1|R1|0.104672|0.105056|0.9963x|—|—|—|pass|

|sm103a_silu_e192_h6144_i1536_k4_t15|G2|R1|0.111632|0.111008|1.0056x|—|—|—|pass|

|sm103a_silu_e192_h6144_i1536_k4_t16|G3|R1|0.116257|0.116704|0.9962x|—|—|—|pass|

|sm103a_silu_e192_h6144_i1536_k4_t17|G0|R1|0.120448|0.119777|1.0056x|—|—|—|pass|

|sm103a_silu_e192_h6144_i1536_k4_t18|G1|R1|0.125921|0.125312|1.0049x|—|—|—|pass|

|sm103a_silu_e192_h6144_i1536_k4_t19|G2|R1|0.132736|0.132001|1.0056x|—|—|—|pass|

|sm103a_silu_e192_h6144_i1536_k4_t20|G3|R1|0.138241|0.138240|1.0000x|—|—|—|pass|

|sm103a_silu_e192_h6144_i1536_k4_t21|G0|R1|0.142337|0.142305|1.0002x|—|—|—|pass|

|sm103a_silu_e192_h6144_i1536_k4_t22|G1|R1|0.148737|0.148289|1.0030x|—|—|—|pass|

|sm103a_silu_e192_h6144_i1536_k4_t23|G2|R1|0.152321|0.152576|0.9983x|—|—|—|pass|

|sm103a_silu_e192_h6144_i1536_k4_t24|G3|R1|0.157760|0.157889|0.9992x|—|—|—|pass|

|sm103a_silu_e192_h6144_i1536_k4_t25|G0|R1|0.163521|0.163713|0.9988x|—|—|—|pass|

|sm103a_silu_e192_h6144_i1536_k4_t26|G1|R1|0.169313|0.169280|1.0002x|—|—|—|pass|

|sm103a_silu_e192_h6144_i1536_k4_t27|G2|R1|0.175297|0.176033|0.9958x|—|—|—|pass|

|sm103a_silu_e192_h6144_i1536_k4_t28|G3|R1|0.181120|0.180609|1.0028x|—|—|—|pass|

|sm103a_silu_e192_h6144_i1536_k4_t29|G0|R1|0.186593|0.187265|0.9964x|—|—|—|pass|

|sm103a_silu_e192_h6144_i1536_k4_t30|G1|R1|0.190401|0.190625|0.9988x|—|—|—|pass|

|sm103a_silu_e192_h6144_i1536_k4_t31|G2|R1|0.194816|0.195040|0.9989x|—|—|—|pass|

|sm103a_silu_e192_h6144_i1536_k4_t32|G3|R1|0.199680|0.199425|1.0013x|—|—|—|pass|

## Route legend

|Key|Route|
|---|---|
|R1|adaptive_103a_silu_direct|
|R2|adaptive_103a_situ_direct|
|R3|adaptive_103a_swiglu_direct|
|R4|adaptive_103a_swiglu_gpu_packed|

## Baseline legend

Each shape row above inlines its applicable external baselines (paired
export ms is the shape's Export ms column); keys resolve here.

|Key|Baseline|Label|Rows|Gate|
|---|---|---|---:|---|
|B1|flashinfer_trtllm|FlashInfer TRT-LLM routed MoE|128|Baseline /
Export > 1.0|
|B2|flashinfer_trtllm_lineage|FlashInfer TRT-LLM routed MoE (lineage
rows, byte-identical to the previously published
delivery)|224|report-only|

## Geomeans over all correct timed rows

Gate-failing performance rows remain in these geomeans; only rows
without valid correctness and timing are excluded and remain visible
above.

|Shape tag|Timed rows|Denominator|Source ms|Export ms|Source / Export|
|---|---:|---:|---:|---:|---:|
|all|480|480|0.080218|0.080208|1.000124x|
|activation_silu|32|32|0.100512|0.100443|1.000687x|
|activation_situ|32|32|0.612069|0.611637|1.000706x|
|activation_swiglu|416|416|0.067430|0.067428|1.000036x|
|production|480|480|0.080218|0.080208|1.000124x|
|sm103a|480|480|0.080218|0.080208|1.000124x|
|sm103a_silu_e192_h6144_i1536_k4|32|32|0.100512|0.100443|1.000687x|
|sm103a_situ_e896_h3584_i3072_k16|32|32|0.612069|0.611637|1.000706x|
|sm103a_swiglu_e128_h2048_i768_k8|32|32|0.040606|0.040612|0.999840x|
|sm103a_swiglu_e128_h4096_i1536_k8|32|32|0.121391|0.121248|1.001176x|
|sm103a_swiglu_e128_h6144_i3072_k4|32|32|0.204585|0.204483|1.000500x|
|sm103a_swiglu_e256_h2048_i512_k8|32|32|0.041315|0.041282|1.000801x|
|sm103a_swiglu_e256_h3072_i1536_k8|32|32|0.120337|0.120366|0.999753x|
|sm103a_swiglu_e256_h3072_i384_k8|32|32|0.040124|0.040185|0.998470x|
|sm103a_swiglu_e256_h3072_i768_k8|32|32|0.062973|0.063076|0.998363x|
|sm103a_swiglu_e384_h2560_i768_k4|32|32|0.042478|0.042546|0.998383x|
|sm103a_swiglu_e512_h2048_i512_k10|32|32|0.050938|0.050896|1.000835x|
|sm103a_swiglu_e512_h4096_i1024_k10|32|32|0.136159|0.136116|1.000318x|
|sm103a_swiglu_e512_h4096_i256_k10|32|32|0.049388|0.049411|0.999527x|
|sm103a_swiglu_e512_h4096_i512_k10|32|32|0.073364|0.073332|1.000446x|
|sm103a_swiglu_e60_h2048_i1536_k4|32|32|0.044059|0.043968|1.002065x|

### Geomeans: FlashInfer TRT-LLM routed MoE

|Shape tag|Timed rows|Denominator|Baseline ms|Paired export ms|Baseline
/ Export|
|---|---:|---:|---:|---:|---:|
|all|128|128|0.063442|0.055051|1.152432x|
|activation_swiglu|128|128|0.063442|0.055051|1.152432x|
|production|128|128|0.063442|0.055051|1.152432x|
|sm103a|128|128|0.063442|0.055051|1.152432x|
|sm103a_swiglu_e256_h3072_i384_k8|32|32|0.046578|0.040185|1.159074x|
|sm103a_swiglu_e256_h3072_i768_k8|32|32|0.072451|0.063076|1.148634x|
|sm103a_swiglu_e512_h4096_i256_k10|32|32|0.056140|0.049411|1.136195x|
|sm103a_swiglu_e512_h4096_i512_k10|32|32|0.085508|0.073332|1.166046x|

### Geomeans: FlashInfer TRT-LLM routed MoE (lineage rows,
byte-identical to the previously published delivery)

|Shape tag|Timed rows|Denominator|Baseline ms|Paired export ms|Baseline
/ Export|
|---|---:|---:|---:|---:|---:|
|all|224|224|0.155909|0.122609|1.271595x|
|activation_situ|32|32|1.021184|0.611637|1.669591x|
|activation_swiglu|192|192|0.113981|0.093798|1.215174x|
|production|224|224|0.155909|0.122609|1.271595x|
|sm103a|224|224|0.155909|0.122609|1.271595x|
|sm103a_situ_e896_h3584_i3072_k16|32|32|1.021184|0.611637|1.669591x|
|sm103a_swiglu_e128_h2048_i768_k8|32|32|0.045678|0.040612|1.124743x|
|sm103a_swiglu_e128_h4096_i1536_k8|32|32|0.198771|0.121248|1.639376x|
|sm103a_swiglu_e128_h6144_i3072_k4|32|32|0.206567|0.204483|1.010190x|
|sm103a_swiglu_e256_h2048_i512_k8|32|32|0.042867|0.041282|1.038399x|
|sm103a_swiglu_e256_h3072_i1536_k8|32|32|0.194934|0.120366|1.619503x|
|sm103a_swiglu_e512_h4096_i1024_k10|32|32|0.139914|0.136116|1.027899x|

Complete denominator: **true** (480/480).

All gates passed: **true** (480/480).

### SM100 run of record (hardware stages and geomeans)

## Hardware stages

- `sm_100a` / world size `1`: GPUs `NVIDIA B200`, capabilities `10.0`,
drivers `580.82.07`, UUIDs `GPU-36ef1b22-87e2-93d8-0139-584381261fae`;
118 shapes (named in the per-shape tables below).
- `sm_100a` / world size `1`: GPUs `NVIDIA B200`, capabilities `10.0`,
drivers `580.82.07`, UUIDs `GPU-91d986a1-1a8a-4a24-c599-ed755a01aeb7`;
121 shapes (named in the per-shape tables below).
- `sm_100a` / world size `1`: GPUs `NVIDIA B200`, capabilities `10.0`,
drivers `580.82.07`, UUIDs `GPU-72af6a98-59b1-aab9-91c3-3ac6d383424c`;
121 shapes (named in the per-shape tables below).
- `sm_100a` / world size `1`: GPUs `NVIDIA B200`, capabilities `10.0`,
drivers `580.82.07`, UUIDs `GPU-801dfe4c-c8f7-8072-3f9b-ba9345e8509e`;
120 shapes (named in the per-shape tables below).

Target revision: `ac30bfabfc40cca1971bea7a41ac10e6960d6bfd`.

Benchmark execution: `symmetric_external_cuda_graph_population_v1`; 3
counterbalanced groups, 50.000 ms warmup and 100.000 ms reportable
budget per arm/group.
Latency metric: CUPTI GPU span per sample, first compute-kernel start to
last compute-kernel end of one arm call (every kernel the call launches,
asynchronous copies excluded), after a cold-L2 flush before each
measured sample, with the SM clock held at or above 1900 MHz; the
reported value is the per-arm median. Each row's ``sm_clock_mhz_range``
in the summary JSON is the SM clock range observed while the row was
timed (group-boundary probes and, in the symmetric graph mode, every
sampled warmup/measurement phase).
Each sample follows one unmeasured same-arm launch, state restoration,
and a fresh cold-L2 flush.

The complete semantic arguments and machine-readable receipts remain in
`summary.json`; the table below retains every registered shape without
repeating those arguments, keys routes and external baselines against
the legends that follow it, and inlines each shape's external
comparison.

## Route legend

|Key|Route|
|---|---|
|R1|adaptive_100a_silu_direct|
|R2|adaptive_100a_situ_direct|
|R3|adaptive_100a_swiglu_direct|
|R4|adaptive_100a_swiglu_gpu_packed|

## Baseline legend

Each shape row above inlines its applicable external baselines (paired
export ms is the shape's Export ms column); keys resolve here.

|Key|Baseline|Label|Rows|Gate|
|---|---|---|---:|---|
|B1|flashinfer_trtllm|FlashInfer TRT-LLM routed MoE|128|Baseline /
Export > 1.0|
|B2|flashinfer_trtllm_lineage|FlashInfer TRT-LLM routed MoE (lineage
rows, byte-identical to the previously published
delivery)|224|report-only|

## Geomeans over all correct timed rows

Gate-failing performance rows remain in these geomeans; only rows
without valid correctness and timing are excluded and remain visible
above.

|Shape tag|Timed rows|Denominator|Source ms|Export ms|Source / Export|
|---|---:|---:|---:|---:|---:|
|all|480|480|0.082941|0.082895|1.000563x|
|activation_silu|32|32|0.101356|0.101148|1.002061x|
|activation_situ|32|32|0.579572|0.579346|1.000390x|
|activation_swiglu|416|416|0.070327|0.070295|1.000462x|
|production|480|480|0.082941|0.082895|1.000563x|
|sm100a|480|480|0.082941|0.082895|1.000563x|
|sm100a_silu_e192_h6144_i1536_k4|32|32|0.101356|0.101148|1.002061x|
|sm100a_situ_e896_h3584_i3072_k16|32|32|0.579572|0.579346|1.000390x|
|sm100a_swiglu_e128_h2048_i768_k8|32|32|0.045539|0.045437|1.002258x|
|sm100a_swiglu_e128_h4096_i1536_k8|32|32|0.129995|0.130135|0.998927x|
|sm100a_swiglu_e128_h6144_i3072_k4|32|32|0.204434|0.204538|0.999488x|
|sm100a_swiglu_e256_h2048_i512_k8|32|32|0.042510|0.042550|0.999045x|
|sm100a_swiglu_e256_h3072_i1536_k8|32|32|0.127197|0.127095|1.000803x|
|sm100a_swiglu_e256_h3072_i384_k8|32|32|0.041808|0.041795|1.000302x|
|sm100a_swiglu_e256_h3072_i768_k8|32|32|0.064864|0.064703|1.002501x|
|sm100a_swiglu_e384_h2560_i768_k4|32|32|0.043590|0.043575|1.000349x|
|sm100a_swiglu_e512_h2048_i512_k10|32|32|0.053940|0.053966|0.999504x|
|sm100a_swiglu_e512_h4096_i1024_k10|32|32|0.137409|0.137454|0.999675x|
|sm100a_swiglu_e512_h4096_i256_k10|32|32|0.051339|0.051372|0.999362x|
|sm100a_swiglu_e512_h4096_i512_k10|32|32|0.074804|0.074723|1.001081x|
|sm100a_swiglu_e60_h2048_i1536_k4|32|32|0.046755|0.046628|1.002719x|

### Geomeans: FlashInfer TRT-LLM routed MoE

|Shape tag|Timed rows|Denominator|Baseline ms|Paired export ms|Baseline
/ Export|
|---|---:|---:|---:|---:|---:|
|all|128|128|0.064825|0.056762|1.142053x|
|activation_swiglu|128|128|0.064825|0.056762|1.142053x|
|production|128|128|0.064825|0.056762|1.142053x|
|sm100a|128|128|0.064825|0.056762|1.142053x|
|sm100a_swiglu_e256_h3072_i384_k8|32|32|0.047847|0.041795|1.144779x|
|sm100a_swiglu_e256_h3072_i768_k8|32|32|0.073528|0.064703|1.136396x|
|sm100a_swiglu_e512_h4096_i256_k10|32|32|0.058019|0.051372|1.129404x|
|sm100a_swiglu_e512_h4096_i512_k10|32|32|0.086517|0.074723|1.157830x|

### Geomeans: FlashInfer TRT-LLM routed MoE (lineage rows,
byte-identical to the previously published delivery)

|Shape tag|Timed rows|Denominator|Baseline ms|Paired export ms|Baseline
/ Export|
|---|---:|---:|---:|---:|---:|
|all|224|224|0.163089|0.126586|1.288363x|
|activation_situ|32|32|1.163216|0.579346|2.007809x|
|activation_swiglu|192|192|0.117549|0.098241|1.196531x|
|production|224|224|0.163089|0.126586|1.288363x|
|sm100a|224|224|0.163089|0.126586|1.288363x|
|sm100a_situ_e896_h3584_i3072_k16|32|32|1.163216|0.579346|2.007809x|
|sm100a_swiglu_e128_h2048_i768_k8|32|32|0.046964|0.045437|1.033606x|
|sm100a_swiglu_e128_h4096_i1536_k8|32|32|0.211551|0.130135|1.625634x|
|sm100a_swiglu_e128_h6144_i3072_k4|32|32|0.206003|0.204538|1.007159x|
|sm100a_swiglu_e256_h2048_i512_k8|32|32|0.043955|0.042550|1.033020x|
|sm100a_swiglu_e256_h3072_i1536_k8|32|32|0.207435|0.127095|1.632119x|
|sm100a_swiglu_e512_h4096_i1024_k10|32|32|0.141373|0.137454|1.028509x|

Complete denominator: **true** (480/480).

All gates passed: **true** (480/480).

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added Cake Warp Decode support for four sharded expert configurations,
covering hidden sizes 3072 and 4096. These configurations support token
counts from 1 to 32 and are available on both SM100a and SM103a GPUs.
  * Added the new configurations to the documented supported options.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [ba7a4ae](https://github.com/flashinfer-ai/flashinfer/commit/ba7a4ae689b694f31ee6769b61a249c45de7615a)

- **作者**: Alex Yang
- **时间**: 2026-10-05T23:29:19Z
- **提交信息**: fix(autotuner): re-rank tactics when the profiling policy changes (#5715)

<!-- .github/pull_request_template.md -->

## 📌 Description

`rank_tactics(k>1)` caches its shortlist in `_ranked_tactics_cache`
under the `ProfilingCacheKey`, which does not include the replay/L2
measurement policy. As a result, a shortlist measured with hot L2 was
returned for a later cold-L2 request on the same workload (and vice
versa) without profiling, even though `choose_one` already treats a
policy change as a reason to retune (`_profiling_cache_policies`).

This PR stores the policy (`_profiling_policy(tuning_config)`) with each
shortlist and re-ranks on a mismatch. Shortlists are process-local and
never persisted, so no file format changes.

## 🔍 Related Issues

Found while reviewing #5705. That PR persists the policy for the
`choose_one` winner in v1 saved configs; this PR fixes the separate
in-memory shortlist cache. The two are independent and can merge in
either order (they touch adjacent lines in `rank_tactics`, so the second
one may need a trivial rebase).

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

Added `test_rank_tactics_reranks_when_profiling_policy_changes` in
`tests/autotuner/test_autotuner_core.py` (profiling is mocked, so it
needs no particular GPU). Not yet run locally; relying on CI.

## Reviewer Notes

Python-only, no kernel changes.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Tactic rankings are recalculated when profiling settings change, so
results measured under one policy aren’t reused under another.
* Requests using the same profiling settings reuse cached rankings. This
also applies when a later request asks for a larger shortlist, avoiding
unnecessary re-profiling.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [3f94a47](https://github.com/flashinfer-ai/flashinfer/commit/3f94a4725a11d406960dd0f92b92b2a370035b4f)

- **作者**: Nikita Korobov
- **时间**: 2026-10-05T22:53:14Z
- **提交信息**: feat(prims-ts): add FP8/NVFP4 GEMMs with SwiGLU and RoPE fusion (#5758)

## 📌 Description

Add dense Prims-TS GEMM APIs for FP8 and packed NVFP4, including linear,
fused SwiGLU, and QKV with QKNorm and RoPE operations. Add prepared
NVFP4 linear operations and autotuning with cached tactic selection. The
NVFP4 implementation
includes SM103 3x support and specialized epilogues.
Add correctness and autotuning tests, plus a GEMM benchmark.

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
* Added dense FP8 and NVFP4 GEMM operations for linear, SwiGLU, and QKV
with normalization and RoPE.
* Added reusable prepared NVFP4 projections and automatic tactic tuning.
* Added a benchmark for comparing GEMM performance across shapes and
tactics.

* **Documentation**
  * Documented the new GEMM operations and supported hardware.

* **Tests**
* Added coverage for GEMM outputs, validation, tuning, and supported
configurations.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: jimmzhou <jimmzhou@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [125c989](https://github.com/flashinfer-ai/flashinfer/commit/125c989e0e04a5117cb789d49e1ca4879fa62886)

- **作者**: kangbintNV
- **时间**: 2026-10-05T22:15:05Z
- **提交信息**: docs: document cutlass fused MoE backend parameter (#6042)

<!-- .github/pull_request_template.md -->

## 📌 Description

Move the existing `backend` documentation for `cutlass_fused_moe` into
the NumPy-style `Parameters` section.

The text currently appears after `Notes`, so the documentation checker
does not associate it with the function argument and reports a real Args
Consistency failure. This is a documentation-only change; the API and
runtime behavior are unchanged.

## 🔍 Related Issues

- The parameter was introduced in #5183.

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

- [x] Tests have been added or updated as needed. (Documentation-only
change; no test change is needed.)
- [x] All relevant tests are passing:
  - `pre-commit run --files flashinfer/fused_moe/core.py`
- `python3 -m scripts.pr_checks.check_docstrings` (0 Docstring
Completeness failures, 0 Args Consistency failures)
- `python3 scripts/check_pr_document.py --base origin/main --head HEAD
--strict` (0 new findings)

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

The content of the `backend` description is unchanged; only its
placement in the docstring is corrected.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Documentation**
* Clarified the available backend options and the requirements for the
TP8-local SiTU call.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [ab929e6](https://github.com/flashinfer-ai/flashinfer/commit/ab929e6647f828b83b74665669e6c9b493f993c1)

- **作者**: kangbintNV
- **时间**: 2026-10-05T22:14:44Z
- **提交信息**: docs: document environment variables and cake RMSNorm (#6041)

<!-- .github/pull_request_template.md -->

## 📌 Description

Document four runtime environment variables that are present on current
`main` but missing from the environment-variable quick reference:

- `FLASHINFER_KDA_PTXAS`
- `FLASHINFER_KDA_PTX_CACHE_DIR`
- `FLASHINFER_SM90_CAKE_BF16_DEV_LAUNCHER`
- `FLASHINFER_SM90_CAKE_BF16_COMBINE_WIRE`

The first two are the Env Vars Consistency failures in the linked
report. The third was introduced by #5958 after the report's `c3c33367f`
snapshot. The fourth was introduced by #6058 after the latest report was
generated. All four are real failures on current `main`.

The documented defaults, lookup behavior, accepted value format, and
source paths match the runtime implementations. The cache-directory
wording also distinguishes its default from a user-supplied override,
addressing the CodeRabbit review comment.

The PR additionally documents every parameter and return form of the new
autograd-enabled `cake_rmsnorm` API reported by the latest documentation
check. This PR changes documentation only and does not modify checker
code under `scripts/`.

## 🔍 Related Issues

- KDA PTX variables were introduced in #5665.
- The SM90 CAKE BF16 development launcher variable was introduced in
#5958.
- The SM90 CAKE BF16 combine-wire override was introduced in #6058.
- `cake_rmsnorm` was introduced in #5741.

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

- [x] Tests have been added or updated as needed. (Documentation-only
change; no test change is needed.)
- [x] All relevant tests are passing:
  - `pre-commit run --files CLAUDE.md flashinfer/cake_rmsnorm_train.py`
- `python3 -m scripts.pr_checks.check_docstrings` (`cake_rmsnorm`
Docstring Completeness: 0 failures)
- `python3 -m scripts.pr_checks.check_cross_sources` (0 failures in all
categories)
- `python3 scripts/check_pr_document.py --base origin/main --head HEAD
--strict` (0 new findings)

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

This PR intentionally keeps the fixes in documentation and docstrings;
no `scripts/` checker or runtime changes are included.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Documentation**
* Expanded the environment-variable reference with `ptxas` discovery
requirements, a compiled-cubin cache location and override, and options
for selecting the SM90 BF16 CAKE development launcher and combine-wire
behavior. The combine-wire documentation covers available modes, default
selection by token capacity, and the requirement for ranks in a pipe to
agree.
* Expanded `cake_rmsnorm` documentation to cover its parameters, CUDA
and BF16 requirements, epsilon evaluation, residual behavior,
deterministic-gradient restriction, return shapes, and fused backward
kernels.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [2e43e62](https://github.com/flashinfer-ai/flashinfer/commit/2e43e62dff2c81e490ad435d7a18a7f621a082e8)

- **作者**: Vincent
- **时间**: 2026-10-05T22:04:36Z
- **提交信息**: feat(gemm): enable TGV, CuTe DSL low-latency block-scaled and contiguous-grouped GEMMs on SM107 (Rubin) (#5394)

## What

Enables the CuTe DSL GEMM family on SM107 (Rubin). Four commits:

1. **TGV GEMM** (BF16/FP16 mm + bmm and the block-scaled FP4/FP8
variant) — formerly PR #5333, folded in here to keep the review in one
place. Four static allowlists, five lines: `_tgv_gemm_requirement`,
`_tgv_bmm_bf16_requirement`, a hardcoded `_match_sm_version` inside
`tgv_gemm_sm100`, and the low-latency runner's `valid_tactics`
`sm_version not in (100, 103)`, plus the test guard. The gate dated from
a CuTe DSL module-load failure on SM107 that no longer exists: an A/B on
one GR100 with one source tree shows DSL `4.8.0a0+20260810` failing
every kernel (even a trivial `@cute.kernel`) with
`cudaErrorInvalidValue` — the cu12/cu13 runtime mismatch of nvbug
6640205 — while `4.8.0.dev0` passes all 29 TGV tactics × 4 shapes × PDL
on/off (232/232). Kernel source is byte-identical throughout.
3. **(test-only)** the two `test_mm_bf16.py` low-M CuTe-DSL tests pinned
themselves to 10.0/10.3 although the library dispatch already accepts
SM107.
2. **Low-latency block-scaled GEMMs** (FP8, MXFP8, FP4) and the
**contiguous grouped FP8 GEMM** — add 107 to their
`@supported_compute_capability([100, 103])` allowlists plus the matching
test predicates. These share the `valid_tactics` allowlist from commit
1; without it every low-latency call on SM107 raises `The low-latency
block-scaled GEMM kernel cannot implement problem (...)`.

## GR100 (cc 10.7) results

| test file | baseline | branch |
|---|---|---|
| `tests/gemm/test_tgv_gemm.py` + TGV cases of `test_mm_bf16.py` /
`test_bmm_bf16.py` | 94 + 2 + 16 skipped | **273 passed / 163 skipped, 0
failed** across the three files |
| `tests/gemm/test_mm_fp8.py` (`cutedsl_low_latency`) | 30 passed / 30
skipped | **54 passed / 6 skipped** |
| `tests/gemm/test_mm_fp4.py` (`cutedsl_low_latency`) | 11 passed / 22
skipped | **21 passed / 12 skipped** |
| `tests/gemm/test_low_latency_blockscaled_gemm.py` | 7 passed / 10
skipped | **17 passed** |
| `tests/gemm/test_groupwise_scaled_gemm_fp8.py` | 2011 passed / 1694
skipped | **2080 passed / 1625 skipped** |
| `tests/trace/test_tgv_gemm_sm100_reference_correctness.py` (test-only
pin, commit 4; the "precompiled cubin" comment was stale — TGV is
JIT-compiled) | 2 skipped | **2 passed** |
| `tests/gemm/test_mm_bf16.py` low-M cute-dsl tests (test-only pins,
commit 3) | 2 tests skipped | **+4 cases passed** (14 passed / 13
skipped overall; the rest are backends #5308 enables or `tgv`, commit 1)
|

Zero new failures. The remaining skips are not architecture gates:
- `mm_fp8` / `mm_fp4`: `M <= 8` (the low-latency kernel is a
decode-shape kernel), and the `b12x` / `auto` backends, which are
SM120-only.
- `groupwise`: the 69 recovered cases are exactly the two SM100/SM103
predicates (53 + 16). Of the 1625 left, **749** are `cuda-tile /
tileiras compiler not available` — the validation image predates
flashinfer-ci !435, which installs the sm_107-capable tileiras (the
cuTile *arch* gate itself is widened in #5308) — and **876** are
scale-major-mode / `k < 256` restrictions that skip identically on
Blackwell.

## Why it is safe

These kernels are the same species as the TGV cute_ext GEMM:
`blackwell_helpers` layouts, `get_smem_capacity_in_bytes("sm_100")`
budgets (≤ Rubin's 232448-byte opt-in), tcgen05 MMA. With CuTe DSL ≥
4.8.0.dev0 they compile natively for `sm_107a` and the tests above
verify numerics against torch references. Only the static allowlists
excluded them.

## Not included

- Blackwell-native / -tiled **BF16×FP4** GEMM
(`test_blackwell_bf16_fp4.py`, 9 cases): behind its two decorators sit
two more gates (`gemm_bf16_fp4_blackwell.py`,
`jit/blackwell_bf16_fp4.py::_target_for_capability`) over a per-target
*generated* 4.5 MB source bundle (`…_generated_sm100.cu` /
`…_generated_sm103.cu`, differing only in `TARGET_SM` and an
ABI-manifest hash). A relabel is mechanical but is the generator's
artifact to produce.
- Cake NVFP4 SVDQuant (`cake` backend, 10 cases) and Cake BF16 BMM:
separately generated per-architecture sources. The CUTLASS SVDQuant path
already runs on SM107 (#4509).
- The cudnn / cublaslt / cuTile mm+bmm allowlists are in #5308 and are
not duplicated here.
- Requires CuTe DSL >= 4.8.0.dev0 (the version the Rubin CI job
installs); on the image's baked 4.7.0 the `Arch` enum has no `sm_107a`
member and these tests fail with `KeyError: 'sm_107a'` rather than skip.

## Validation

Image `flashinfer-ci:cu134-nightly-py3.67144516-whl-amd64` with the CI
job's `nvidia-cutlass-dsl[cu13]==4.8.0.dev0` override, against an
`upstream/main` baseline on the same tree/image. x86_64 only; the Rubin
CI nodes are arm64.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added SM107 support across TGV GEMM, grouped FP8 GEMM, and low-latency
FP8, MXFP8, and FP4 GEMM workloads.
* Expanded SM107 compatibility for BF16, batch-matrix, and block-scaled
GEMM paths.
* Low-latency block-scaled GEMM supports SM107 for workloads with `n ≤
8`.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Vincent Tombari <Vinnie6167@users.noreply.github.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [58171ea](https://github.com/flashinfer-ai/flashinfer/commit/58171ea83f32185a7990cfc15c969ecf79bb406c)

- **作者**: eigen
- **时间**: 2026-10-05T20:23:43Z
- **提交信息**: feat(cake_deepgemm): DeepSeek-V3.2 DSA indexer logits with the DeepGEMM signatures -- 64-head dense fp8_mqa_logits routes for any Q/K and paged FP8 fp8_paged_mqa_logits + metadata over the block table, admitted per arch (SM100a, SM103a) (#6059)

## 📌 Description

DeepSeek-V3.2 lightning-indexer logits for serving engines: the
experimental `deepgemm_dense_mqa` family gains public entries with the
exact signatures of the DeepGEMM calls the engines make today, so an
engine can switch call sites without changing tensors or chunking:

* `flashinfer.dense_mqa.fp8_mqa_logits(q, (kv, kv_scales), weights, ks,
ke, clean_logits=False, max_seqlen_k=0, *, sm_count=None)` — ragged
prefill, one shot on a `DenseMqaPlan` (pads `Q < BLOCK_Q` for the
32-head programs, copies short KV-scale storage into an `align4(K)`
buffer); `clean_logits=True` is rejected on routes whose program stores
raw tiles (`route record clean_logits == "raw"`).
* `flashinfer.paged_mqa.get_paged_mqa_logits_metadata(context_lens,
block_kv, num_sms, indices=None)`, `fp8_paged_mqa_logits(q, kv_cache,
weights, context_lens, block_table, schedule_meta, max_context_len,
clean_logits=False, indices=None)` and `prepare_paged_mqa_logits(...)` →
`PagedMqaPlan` — paged decode / verify on the fused 132-byte FP8 cache
rows (`[pages, block_kv, 1, 132]`), 2-D context lengths, any block-table
stride.

Catalog schema `dense_mqa.v6`: policy `heads` / `block_q` /
`kv_alignment` / `max_q_blocks` / `metadata_tier_blocks` / `paged`
(`heads`, `block_kv`, `split_kv`, `next_n_atoms`, `max_batch`); route
records carry `num_heads`, `block_q`, `clean_logits` (`"fused"` /
`"raw"`) and `kv_alignment`; new `paged_routes` table. The 16 shipped
32-head routes, their names and programs are unchanged. 64-head dense
routes (`fp8:h64:*`, single-stage gridDim-strided programs, any `K >=
1`, any `Q`) and the paged routes (`paged:fp8:h<H>:p<page>:n<next_n>`)
are served by the catalog as their programs land;
`dense_route_available(H, Q, K)` / `paged_route_available(H, block_kv,
next_n)` answer availability on the host so engines admit by table, not
by restated rules.

Admission of the 64-head family is tiered by query count and decided per
device architecture: a tier's route is served on an arch only when every
acceptance row of the tier is faster than stock DeepGEMM on that arch;
the catalog policy `dense_admission` lists `admitted_routes` /
`withheld_routes` / `reason` per arch, `dense_route_available(H, Q, K,
arch=...)` (and `dense_admission(arch)`, `device_arch(device)`) return
False for withheld tiers so engines fall back to their stock kernel by
table. Shipped lists: sm_103a admits `fp8:h64:partial:any`; sm_100a
admits no 64-head tier yet (reason recorded in the catalog). The host
tests (`tests/experimental/test_dense_mqa_admission.py`) pin the shipped
lists against the routes table.

Paged routes are admitted per (arch, route, batch, max_context_len) from
`policy.paged.admission` (ordered `(max_batch, max_context_len)` rules,
`null` = unbounded): sm_100a serves every route for batch <= 16 at any
context length (larger batches are still unmeasured there); sm_103a
serves `h64:p64:n4` unbounded, `n2` and `n1` with batch-dependent
context bounds (large-batch long-context rows did not clear).
`paged_route_available(..., arch=, batch=, max_context_len=)` answers
the table and `PagedMqaPlan` refuses a point outside it unless
`enforce_admission=False`.

The paged runtime binds `num_sms` as a kernel argument (the
single-kernel logits programs partition the (request, KV-split) walk
over the CTA budget in-kernel; `schedule_meta` stays an API mirror).
Host-only coverage tests assert that every program argument of every
dense and paged program is produced by the runtime binding builders.

Every program launches under `tvm_ffi.use_torch_stream()` (current
stream resolved at launch time), so calls captured in a CUDA graph land
on the capture stream.

## 🔍 Related Issues

<!-- engine issue / tracking issue links go here -->

## 🚀 Pull Request Checklist

- [x] Pre-commit checks (`pre-commit run --all-files`) pass.
- [x] Tests: `tests/experimental/test_dense_mqa_admission.py` (per-arch
admission table, 23 tests),
`tests/experimental/test_dense_mqa_generated.py` (route table, one-shot
entry vs the PyTorch specification and DeepGEMM when importable,
CUDA-graph replay of the one-shot entry, catalog ↔ generated-source
consistency), `tests/experimental/test_paged_mqa_generated.py` (paged
plan / one-shot entries vs reference and DeepGEMM, chunking equivalence,
admission bounds per arch, host helpers and rejections, CUDA-graph
replay).
- [x] Benchmarks: `benchmarks/bench_dense_mqa_generated.py` (dense),
`benchmarks/bench_paged_mqa_generated.py` (paged).
- [x] Documentation:
`flashinfer/experimental/deepgemm_dense_mqa/README.md`
("DeepGEMM-signature entries", "Catalog schema").

## Validation

Generated programs exported from the Cake producer on both architectures
(export protocol: bitwise source/export parity of the logits, identical
per-call kernel counts, paired CUPTI timing of the FlashInfer plan
against the production launcher; sgl-project DeepGEMM 0.2.0 as the
correctness oracle). The receipts of record for this head:

| arch | rows | passed | notes |
|---|---|---|---|
| sm_103a (GB300) | 53 (39 dense + 14 paged) | 53 | every generated
kernel and binding byte-identical to the previous sealed export; paged
rows 1 kernel per call, FlashInfer plan vs production launcher geomean
1.0005 (previous seal) |
| sm_100a (B200) | 53 (39 dense + 14 paged) | 53 | same byte-identical
program set; paged rows 1 kernel per call, geomean 0.9988 (previous
seal) |

Re-running the exporter against this head leaves the tree unchanged
except for the hand-maintained `generated/.clang-format` (which the
exporter does not emit).

Host + GPU test run on this head (both architectures, every class
green):

```
tests/experimental/test_dense_mqa_admission.py      23 passed
tests/experimental/test_dense_mqa_generated.py      16 passed (host)  +  5 passed, 3 skipped (one-shot GPU)  +  8 passed (32-head routes GPU)
tests/experimental/test_paged_mqa_generated.py      12 passed (GPU; on sm_100a this includes the admission refusals at batch 256 / 2*SMs+5)
```

`pre-commit run --all-files` passes on this head (generated units carry
a `.clang-format` with `DisableFormat: true`; host files are
ruff-formatted with the hook pin).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Avery Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [9c6797e](https://github.com/flashinfer-ai/flashinfer/commit/9c6797eda4d208b4b56dcb30383b8772b112240b)

- **作者**: eigen
- **时间**: 2026-10-05T19:47:43Z
- **提交信息**: perf(cake_sampling): round 9 -- leader-push exchange twins of the multi-CTA streams, graph-replay host fix (#6065)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

## Cake radix sampling, round 9: leader-push exchange twins of the
multi-CTA streams, graph-replay host fix

Follow-up of #5439, #5482, #5585, #5607, #5636, #5684, #5731, #5847 and
#5950 (the round-8 bundle `0df0c683` as merged in #5950 and re-listed by
the lean loader of #5985 is the baseline; this PR's `fi9-base` tree is
upstream `f2794d5890`).

### What changes

- **Leader-push exchange twins (`_lp`, `_cs_lp`, `_sp_lp`; launch flag
bit 9, manifest `leader_push`, 18 new stage-1 kernels).** In the
multi-CTA streaming variants (cluster 2 / 4 / 8 x ept 16 / 32) every CTA
stores its compacted candidate list straight into rank 0's shared-memory
receive buffer and its list length into every CTA before the single
exchange barrier; rank 0 gathers locally, resolves the threshold,
collects and runs the fused tail, the other CTAs exit. This removes the
pull form's DSM read round and its exit rendezvous (`fused_sync`) -- two
cluster rounds -- without the N-copy byte amplification of a push-to-all
exchange. Outputs are bit-identical to the pull form (fused launches:
positions and bits; two-launch chains: the same exact candidate set
handed to stage 2/3, whose samples / counts / renorm are bitwise
identical end to end).
- **Host rule (`_leader_push_flag`).** Bit 9 is taken on compute
capability 9.0 / 10.0 / 10.3 / 10.7 (RTX PRO 6000 keeps the round-8
routes), for any row on an ept-16 stream and for a row of at most one
register chunk per CTA on an ept-32 stream
(`_LEADER_PUSH_WIDE_MAX_CHUNKS = 1`: the two-to-five-chunk ept-32 rows
measured 1.01-1.31 with the pushes on R200 / B200 / H100), never with
the whole-CTA tail (bit 3); where it applies it displaces the slab tail
(bit 7) and the pushed coarse sums (bit 8). The binding rejects bit 9 on
a resident / single-CTA variant and with bits 3 / 7 / 8; the loader
validates `leader_push` only on multi-CTA stream entries without
`block_tail` / `slab_tail` / `coarse_push`.
- **Graph-replay host fix.** Reading the default generator
(`get_state()`) inside a CUDA-graph capture registers the generator with
the graph and adds two `FillFunctor<long>` kernels to every replay
(+17-19 us on GB300) although both routes take the Philox parameters by
value. Under capture `_philox_params` now uses the generator's initial
seed and a host-side per-(device, generator) offset counter and never
touches the generator; outside capture the generator is read and
advanced exactly as before (lockstep with `top_k_first`). Replays stay
bitwise reproducible per (seed, offset); the k = 1000 graph rows drop to
0.53-0.83 of round 8 and the k <= 50 graph rows to 0.40-0.85 on all four
GPUs.
- The 88 kernels of the round-8 bundle are byte-identical (normalised
source identity of the generated bundle; cubin `.text` identity of the
JIT modules on sm_90a / sm_100a / sm_103a / sm_107a), so every unchanged
route keeps its binary.
- Tests: `tests/utils/test_cake_sampling.py` gains
`test_leader_push_build_matches_pull_build` (fused: bitwise; chains:
candidate-set identity + end-to-end bitwise), the capability / ept /
chunk-rule pins of the bit-9 policy, and the graph-replay generator test
(no generator access inside capture, draws reproducible per (seed,
offset)); the manifest / loader tests cover the new field.

### Speedup (same node / run CUPTI medians, round-8 tree -> round-9
tree; eager small cells and every k = 1000 eager row re-measured as
medians over 10 fresh perturbed processes per tree)

| GPU | k | mode | cells | round-9 / round-8 time (median, min .. max) |
rows > +0.5 % in both tree orders | speedup vs top_k_first (min .. max)
|
|---|---|---|---|---|---|---|
| B200 | 10 | eager | 32 | 1.000 (0.938 .. 1.010) | 0 | 3.1x .. 9.7x |
| B200 | 10 | graph | 32 | 0.560 (0.404 .. 0.789) | 0 | 3.9x .. 8.4x |
| B200 | 50 | eager | 32 | 1.000 (0.955 .. 1.000) | 0 | 3.2x .. 9.6x |
| B200 | 50 | graph | 32 | 0.562 (0.507 .. 0.792) | 0 | 3.8x .. 7.8x |
| B200 | 1000 | eager | 32 | 1.000 (0.980 .. 1.028) | 5 | 2.9x .. 7.9x |
| B200 | 1000 | graph | 32 | 0.651 (0.571 .. 0.825) | 0 | 2.9x .. 7.4x |
| B200 | all | | 192 | summary: FLAGGED_BOTH_ORDERS 5 (all k = 1000
eager), NOT_FASTER 0 | | |
| GB300 | 10 | eager | 32 | 1.000 (0.905 .. 1.000) | 0 | 5.3x .. 17.6x |
| GB300 | 10 | graph | 32 | 0.506 (0.443 .. 0.737) | 0 | 3.9x .. 7.3x |
| GB300 | 50 | eager | 32 | 1.000 (0.923 .. 1.008) | 0 | 5.0x .. 16.6x |
| GB300 | 50 | graph | 32 | 0.516 (0.466 .. 0.754) | 0 | 3.8x .. 7.5x |
| GB300 | 1000 | eager | 32 | 1.006 (0.883 .. 1.087) | 17 | 3.8x .. 7.7x
|
| GB300 | 1000 | graph | 32 | 0.606 (0.531 .. 0.787) | 0 | 2.9x .. 8.6x
|
| GB300 | all | | 192 | summary: FLAGGED_BOTH_ORDERS 17 (all k = 1000
eager), NOT_FASTER 0 | | |
| H100 | 10 | eager | 32 | 0.944 (0.819 .. 1.004) | 0 | 2.5x .. 10.9x |
| H100 | 10 | graph | 32 | 0.512 (0.437 .. 0.846) | 0 | 2.7x .. 7.8x |
| H100 | 50 | eager | 32 | 0.944 (0.827 .. 1.000) | 0 | 2.5x .. 10.8x |
| H100 | 50 | graph | 32 | 0.514 (0.447 .. 0.842) | 0 | 2.8x .. 8.1x |
| H100 | 1000 | eager | 32 | 1.000 (0.970 .. 1.025) | 2 | 2.5x .. 6.7x |
| H100 | 1000 | graph | 32 | 0.635 (0.559 .. 0.850) | 0 | 2.9x .. 7.1x |
| H100 | all | | 192 | summary: FLAGGED_BOTH_ORDERS 2 (all k = 1000
eager), NOT_FASTER 0 | | |
| R200 | 10 | eager | 32 | 1.000 (0.992 .. 1.009) | 0 | 3.3x .. 6.4x |
| R200 | 10 | graph | 32 | 0.635 (0.561 .. 0.792) | 0 | 3.7x .. 6.3x |
| R200 | 50 | eager | 32 | 1.000 (0.992 .. 1.010) | 0 | 3.4x .. 6.4x |
| R200 | 50 | graph | 32 | 0.639 (0.570 .. 0.791) | 0 | 3.2x .. 6.6x |
| R200 | 1000 | eager | 32 | 0.994 (0.929 .. 1.021) | 2 | 2.4x .. 7.7x |
| R200 | 1000 | graph | 32 | 0.614 (0.524 .. 0.780) | 0 | 2.7x .. 8.7x |
| R200 | all | | 192 | summary: FLAGGED_BOTH_ORDERS 2 (all k = 1000
eager), NOT_FASTER 0 | | |

Perturbed-process medians of the served leader-push cells: B200 V128256
B1-8 k10 0.927-0.949 / k50 0.945-0.973; GB300 V128256 B1-8 k10
0.946-0.955 / k50 0.956-0.974; H100 cluster-8 cells V128256 / V151936 /
V262144 B1-8 0.81-0.86 (12.8 / 13.3 / 14.0 -> 10.4 / 11.0 / 11.6 us at
B1), c2 / c4 e16 chains 0.94-1.00; R200 ept-16 cells 0.84-0.96,
cluster-8 chains 0.91-0.96. Every flagged row (all k = 1000 eager) is a
byte-identical kernel on an unchanged host route or a kernel change that
the same-node interleaved A/B contradicts (H100 V151936 B32 `_sp` ->
`_sp_lp` chain 0.987): the cross-tree per-kernel cold-L2 timeline (fresh
process per tree, alternating, identical address offsets) reads the same
kernel durations in both trees on every flagged GB300 cell (e.g. the
fused V151936 B1 k = 1000 kernel 20.4 us in both), and the call launches
no other GPU work -> **0 confirmed regressions on every GPU; every cell
faster than `top_k_first`**. Nodes: B200 nsc-svg gpu-188, GB300 oci-jhb
nvl72d056-T02, H100 cw-dfw pool0-01616, R200 hecate0356.

### Correctness

- Exactness suite (bitwise vs the pull builds) on B200 / GB300 / H100 /
R200; FlashInfer tests at this head: 258 passed / 18 skipped per GPU
(GB300, B200, H100, R200); RTX PRO 6000 (sm_120, this head): 252 passed
/ 24 skipped (dlcluster 2380558, Docker pytorch:26.07,
`supported_capability (12, 0)`, route `pipeline` as in rounds 7 / 8 --
sm_120 semantics unchanged).
- compute-sanitizer synccheck + memcheck: 0 errors on B200 and R200 for
the leader-push form of every multi-CTA stream.
- sglang GSM8K parity on B200 (Qwen3.5-35B-A3B, n = 1319; k50 p0.9 x2,
k1000 p0.9): cake 0.7066 / 0.7043 / 0.6869 vs top_k_first 0.7036 /
0.6854 / 0.6937 vs joint 0.7180 / 0.7172 / 0.6945; greedy-equivalent k =
1 identical; next-token histograms within the reported support in both
arms.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [9494815](https://github.com/flashinfer-ai/flashinfer/commit/94948158fd36a25a811af13cf5b44c3296efcfb5)

- **作者**: Alex Yang
- **时间**: 2026-10-05T18:32:01Z
- **提交信息**: fix(moe): skip unrouted (-1) expert ids in the SM12x fp8/mxfp8_mxfp4 grouped MoE route (#5977)

## 📌 Description

This is the sibling of #5451 (#5446 / NVBug 6828109), for the SM12x fp8
and mxfp8_mxfp4 grouped-MoE runners added in v0.7.1 by #4720. These are
the `MoELayer` backends `sm12x_fp8` and `sm12x_mxfp8_mxfp4`.

**The bug:**
- **Input:** vLLM pads CUDA-graph rows with `topk_ids = -1` and leaves
the weights nonzero (`VLLM_MOE_SKIP_PADDING=1`).
- **Where it goes wrong:** the shared Q0 route-metadata kernels
(`moe_route_meta.py`) index `counts`, `expert_cursor` and `offsets` with
`-1`.
- **Results on main (RTX 5090):**
  - mxfp8_mxfp4 prefill: illegal memory access.
  - fp8 prefill: nonzero padded rows and corrupted valid rows.
  - decode: wrong valid rows.

**The fix (3 files, +63/−28)** treats a negative expert id as "not
routed", the same contract as #5451:
- `count_routes`, `route_assign` and `route_assign_decode` mask `id < 0`
and set dst/scale rows to −1 for those pairs.
- The Q0 scatter kernels skip rows < 0.
- Fully padded tokens come out as exact zeros, and valid rows are
unchanged.
- Ids ≥ `num_experts` remain a caller error.

## 🔍 Related Issues

Sibling of #5451 / #5446. The affected code was added by #4720.

## 🧪 Tests

- **Q0-route unit tests:** `test_sm12x_{fp8,mxfp8}_q0_route.py` gain
`*_q0_route_skips_unrouted`, covering decode, prefill and the
>1024-expert fallback × tail/all/mixed padding, on dirty workspaces.
- **Unified-runner tests:**
`test_unified_moe_sm12x_{fp8,mxfp8_mxfp4}.py` gain
`*_unified_runner_skips_unrouted`. Padded slots keep nonzero weights,
padded rows must be exactly 0, and routed rows must match the torch
reference.

RTX 5090 (SM120), CI image `flashinfer-ci-cu130:20260930-b1420f1`:

| Check | main | this branch |
|---|---|---|
| Repro matrix (fp8/mxfp8 × M 8/64/1024 × none/tail/mixed/all, plus
NaN/zero-weight extras) | 17 pass / 6 fail / 5 IMA | 28/28 pass |
| New tests (one process each) | 7 / 30 | 30 / 30 |
| Existing SM12x MoE tests | 32 passed | 32 passed (+30 new) |
| CUDA-graph capture valid / replay padded | — | 6/6 |
| Route-kernel perf, all-valid ids | — | identical (within 0.01 µs) |

- [x] pre-commit run on changed files
- [x] Tests added/updated

## Reviewer Notes

- **v0.7.1:** labeled for rc3. The code is new in 0.7.1, and this is the
sibling of the already-picked #5451.
- **Not covered:** this was not run on SM121 (GB10) or end-to-end in
vLLM.
- The internal GitLab bot is currently down; the evidence above is from
a manual computelab run.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Routing now treats negative expert IDs as unrouted slots, excluding
them from route counts and assignments.
* Unrouted slots no longer write quantized values or scales into output
buffers, and their destination rows are marked as unavailable.
* Tokens with no routed slots produce zero outputs, while routed slots
continue to be processed normally.
* Added coverage for fully unrouted, partially unrouted, and trailing
unrouted slots across decode and prefill workloads.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [797c3d8](https://github.com/flashinfer-ai/flashinfer/commit/797c3d82fb4046734c864fe280ea6f2ca95b678f)

- **作者**: Perkz Zheng
- **时间**: 2026-10-05T18:31:30Z
- **提交信息**: fix(prims-ts): support CuTe DSL 4.7 and 4.8 (#5478)

<!-- .github/pull_request_template.md -->

## 📌 Description

CuTe DSL 4.8 removes the explicit `context` argument from Task execution
methods, causing PrimTS attention to raise `TypeError` during tracing.
Adapt those calls to the installed signature while retaining CuTe DSL
4.7 support.

- Detect context support once at import and adapt FMHA/MLA task bodies,
persistent pre/post-loop entries, packed HEAD/TAIL groups, and
stage-info construction. DSL 4.7 receives the explicit context; 4.8 uses
the context stored by `Task.init_variables()`.
- Stage the 1CTA MLA `init_variables` and `get_domain` overrides with
`@cute.jit`, keeping configuration branches `cutlass.const_expr`. This
fixes 4.8 resource-container tracing errors and incorrect KV-length
cache propagation.
- Separate statistics-branch and output-phase locals in the G1 MLA
reducer to avoid 4.8's `SCOPE_READ_NEVER_SET` error.

## 🔍 Related Issues

Fixes #5459

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

All applicable hooks passed on the six changed files using `pre-commit
run --files ...`, including Ruff lint and formatting. `git diff --check`
passed. The unchecked items above reflect that repository-wide hooks and
Git hook installation were not run.

## 🧪 Tests

- [x] Tests have been added or updated as needed. Existing suites cover
these regressions; no additional tests were needed.
- [x] All tests are passing (`unittest`, etc.). All four affected suites
passed with both DSL versions.

Before the fix, six selected public-interface cases passed on DSL 4.7.0
and failed on 4.8.0, reproducing all three reported context-argument
errors. Full validation after the fix used separate
`nvidia-cutlass-dsl[cu13]==4.7.0` and `==4.8.0` environments on
GB300/SM103, CUDA 13.3.33, and PyTorch `2.13.0a0+8145d630e8.nv26.06`:

| Existing suite | DSL 4.7.0 | DSL 4.8.0 |
| --- | --- | --- |
| FMHA decode | 376 passed | 376 passed |
| MLA decode | 143 passed | 143 passed |
| Block-sparse | 217 passed, 1 skipped | 217 passed, 1 skipped |
| Q-token/KV-block-sparse | 122 passed | 122 passed |
| Total | 858 passed, 1 skipped | 858 passed, 1 skipped |

```bash
python -m pytest --full \
  tests/attention/test_attention_ts_decode.py \
  tests/attention/test_attention_ts_mla_decode.py \
  tests/attention/test_attention_ts_block_sparse.py \
  tests/attention/test_attention_ts_q_token_kv_block_sparse_metadata.py
```

For GB300 validation, an external pytest hook bypassed only the existing
FMHA SM103 qualification-pending skip; repository test guards are
unchanged. The single skipped case requires explicit opt-in to fatal
device-assertion testing. The 4.8 MLA collection was split across three
processes and checked for exact coverage of all 143 cases.

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

The diff contains five Python implementation files and the PrimTS
README. Existing numerical and CUDA-graph tests provide the regression
coverage. SM100/B200 and SM107/Rubin were not tested in this allocation;
the validation results above are local, not CI results.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Compatibility**
* Task-scheduled attention kernels support CuTe DSL versions 4.7 and
4.8.
* **Bug Fixes**
* Improved compatibility across attention decode and task-scheduling
paths while preserving existing behavior.
* **Tests**
  * Enabled PrimTS attention tests to run on SM107 GPUs.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Vincent Tombari <Vinnie6167@users.noreply.github.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [f835997](https://github.com/flashinfer-ai/flashinfer/commit/f83599719018ab93c35af1936dea6388bdc95d5d)

- **作者**: Vincent
- **时间**: 2026-10-05T18:22:58Z
- **提交信息**: Recover SM107 (Rubin) test coverage lost to stale architecture gates (#5308)

## 📌 Description

Recovers test coverage on Rubin (SM107) that is skipped by architecture
gates written before SM107 existed.

An audit of the nightly SM107 lane against GB300/GB200 found 442 test
functions fully skipped on Rubin but running on both Blackwell SKUs.
This PR addresses the subset where the gate is contradicted by something
already in this repo — a sibling backend that lists 107, a library table
the test ignores, an artifact pin that ships `sm_107a`, or a probe
asking the wrong question. Gates that assert *validation* or *signoff*
on SM107 are deliberately left alone and routed to their owners instead.

Measured against the 2026-09-17 nightly, the seven commits address
**~8,400 skipped cases**:

| commit | change | cases |
|---|---|---|
| `test(mamba)` | probe the ptxas Triton actually uses | 761 |
| `fix(attention)` | drop stale NVFP4-KV and cute-dsl FMHA guards |
5,969 |
| `gemm` | add 107 to 11 backend lists that tests exercise | 1,030 |
| `test(moe,topk)` | align test-side arch sets with library tables | 607
|
| `test` | fix the `arch_blackwell` marker's description (docs-only) | —
|
| `test(trace)` | admit SM107 in the reference-correctness gate | 10 |
| `gemm` | add 107 to the cuDNN batched BF16 list | — |

Each commit is independently revertable and stands on its own evidence:

**Stale guards.** `flashinfer/decode.py` and `flashinfer/prefill.py`
raised `ValueError("KV Cache NVFP4 is not supported on SM107")`,
mirrored by three test skips. The trtllm-gen FMHA pin in
`flashinfer/artifacts.py` is `2d6a5a02…`, the pin that brought sm107a
`KvE2m1` to parity — the claim has not been true since it landed.
Likewise the cute-dsl FMHA prefill skips: `DSL_FMHA` is pinned at
`6efb974a…` and `DSL_FMHA_ARCHS` lists `sm_107a` explicitly. The library
raises are removed in the same commit as the skips on purpose; removing
only the skips would turn a clean skip into a hard `ValueError`.

**Allowlist omissions.** Eleven `@supported_compute_capability` lists
jump from 103 straight to 110, excluding Rubin while admitting newer
architectures. The skip messages print the list back verbatim, e.g.
`_check_grouped_mm_fp4 supports sm[100, 103, 110, 120, 121], got sm107`.
The strongest evidence they are oversights is that the omission is
inconsistent *within* the cuDNN backend — `_cudnn_gemm_fp4_requirement`
and `_cudnn_bmm_fp8_requirement` already list 107 while `_cudnn_mm_bf16`
and friends do not. One cuDNN cannot be four different pieces of
hardware. Every deliberate 107 decision elsewhere in the tree carries a
comment saying so; none of these does.

**The mamba probe.** `tests/mamba/conftest.py` blanket-skips the whole
directory when Triton cannot target the device. The probe globbed the
wheel's *bundled* ptxas and asked it for `sm_107a`, which can never
succeed — Triton 3.8 bundles a CUDA 12.9 `ptxas` and a CUDA 13.3
`ptxas-blackwell`, neither containing `sm_107`. But Triton 3.8 does
support SM107: it lowers LLVM/PTX as `sm_100` and assembles the raw arch
through `get_ptxas(arch)`, which for `arch >= 100` reads
`TRITON_PTXAS_BLACKWELL_PATH`. The probe now mirrors that resolution. It
deliberately keeps the subprocess isolation and the fail-open default,
because Triton's nvptxcompiler calls `abort()` on an arch it cannot
target — that takes the whole pytest process down and cannot be caught
at test time, so a wrong answer costs a CI shard rather than one red
test.

## 🔍 Related Issues

<!-- none filed yet -->

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [ ] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

> Partial, and worth stating precisely: `ruff check` and `ruff format
--check` were run at the pinned version (0.12.8) over all 17 changed
files and pass. The full `pre-commit run --all-files` was **not** run —
the dev box has no GPU and no torch, so the hooks that import the
package cannot execute there.

## 🧪 Tests

- [ ] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

> No tests are added: this PR removes and widens gates so that
**existing** tests run on SM107, and the tests it unblocks are the
verification.
>
> **Not yet validated on hardware.** The dev box has no GPU. The
affected files should be run on an SM107 part (Hecate VR200 or a GR100
lab host) before merge. When they are, note that a widened gate can fail
in three distinct ways and they mean different things:
> - an **import/build** error (traceback ends in `flashinfer/jit/`,
ninja or nvcc; every test in the file fails identically) means no
`sm_107a` artifact — revert, do not paper over it with a probe;
> - a **launch** failure (`no kernel image is available`; compiles then
dies, and poisons the CUDA context so neighbours cascade) means the
cubin is for a different arch;
> - a **numerical** mismatch (assertion in test code; neighbours
unaffected) means the kernel ran and the question is tolerance — that is
the only mode that should escalate rather than revert.
>
> Run with process isolation so a sticky CUDA failure cannot mask the
classification.

## Reviewer Notes

Three things I would look at first:

1. **`test_unified_moe_fp8.py` is deliberately *not* widened**, and it
looks like it should be. It hardcoded `((10, 0), (10, 3))`, and the
obvious move is to defer to `_TRTLLM_ROUTED_ARCHS = (100, 103, 107)`.
That would be wrong: the FP8 path has its own table,
`_TRTLLM_ROUTED_FP8_ARCHS = (100, 103)`, carrying the comment "the FP8
kernels are validated on the SM100 family only". Test and library
already agree and 107 is excluded on purpose. It is changed only to read
that table rather than restate it, so the two cannot drift; behaviour is
identical. Whether FP8 MoE is in fact validated on SM107 is a question
for the MoE owners.

2. **The `trace` commit is the weakest and is last on purpose.** Its
skip text says the tests are "only guaranteed to work on" SM100/SM103 —
a statement about validation, not capability, and nothing in the repo
contradicts it. If the Rubin run shows numerical mismatches there rather
than passes, revert that commit and route the question rather than
loosening a tolerance. The same applies to the bgmv `_SUPPORTED_SM`
widening, whose original reason string was "not validated on SM107".

3. **Scope held back deliberately.** Seven cuTile
`@supported_compute_capability` lists and
`_tinygemm_mm_bf16_requirement` have the same 103→110 shape but no
covering test, and cuTile is not installed in the Rubin CI image —
widening them would be unverifiable either way, so they are left for a
follow-up. A change to `_TRTLLM_GEN_ROUTING_SUPPORTED_CC` (whose own
comment says the module is "compiled for SM 10.x and 12.x", and SM 10.7
is SM 10.x) is also held back for a separate reason: it trips an
internal push-scanner rule, so it needs to be landed through a different
route.

One implementation note for reviewers of the attention commit: it also
deletes the now-unused `skip_if_nvfp4_kv_unsupported()` helper and its
single call site. A stale caller there would have been a `NameError` at
runtime rather than a syntax error, so the grep that caught it was
deliberate rather than incidental.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **New Features**
- Added SM107 (Rubin) support for BF16, MXFP8, FP4, and grouped matrix
multiplication operations.
- Enabled NVFP4 key-value cache decoding and prefill on SM107 GPUs when
the required scaling data is provided.
  - Expanded MoE and related GPU workflows to run on SM107 hardware.

- **Tests**
- Updated GPU validation coverage to include the broader SM10x
architecture family, including SM107.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Vincent Tombari <Vinnie6167@users.noreply.github.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [a1b9e13](https://github.com/flashinfer-ai/flashinfer/commit/a1b9e13a4aa0093b0585a65d4808f6469b390555)

- **作者**: roigarnettNvidia
- **时间**: 2026-10-05T18:10:40Z
- **提交信息**: perf(mamba): enable native SM107 stochastic rounding (#5267)

<!-- .github/pull_request_template.md -->

## 📌 Description

Enable native stochastic rounding on Rubin (SM107a) for Mamba state
updates. The existing architecture guard omitted SM107a, causing Rubin
to use software conversion. This PR adds `__CUDA_ARCH_FEAT_SM107_ALL` to
`FLASHINFER_MAMBA_HAS_CVT_RS`, adds compute capability `(10, 7)` to
`is_cvt_rs_supported()`, and updates the hardware-test descriptions and
skip messages. The shared guard enables the existing FP16 and E4M3
native conversion paths.

### Performance

Compared using CUDA 13.4, PyTorch `2.14.0a0+4fdf77b940.nv26.08`, and
Triton 3.8.0.

Workload: Nemotron 3 Ultra TP1, 256 heads, head dimension 64, state
dimension 128, and 8 groups. Horizontal single-token update (`T=1`),
FP16 state, BF16 inputs/output, FP32 A, seeded stochastic rounding with
`philox_rounds=5`.

| Batch | Before (µs) | After (µs) | Paired speedup | Latency reduction
|
|---:|---:|---:|---:|---:|
| 1 | 10.848 | 7.648 | 1.413× | 29.21% |
| 64 | 132.768 | 85.808 | 1.547× | 35.37% |
| 256 | 502.880 | 319.760 | 1.573× | 36.41% |

Each measurement used 20 warmups and 100 eager CUDA-event samples; state
restoration and a 2×L2 flush occurred outside timing. Each revision used
a fresh JIT cache, with compilation outside timing. CUDA graphs and
clock locks were disabled.

Latencies are pooled medians over 200 samples per revision/batch. Paired
speedup is the geometric mean of the two within-round median ratios;
latency reduction is `1 − 1 / paired_speedup`. Consequently, the pooled
latency ratio may differ slightly from the paired speedup.

These are SSU kernel/API timings. The two rounds do not establish
statistical significance or measure full-model serving throughput.

## 🔍 Related Issues

None linked.

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


## Reviewer Notes

The capability helper and CUDA guard should remain synchronized. The
shared guard affects both FP16 and E4M3 conversion, while the
performance results above cover FP16 horizontal single-token updates
only.

Internal benchmark provenance: `login-hecate`, run directory
`/lustre/fsw/coreai_nvfm_llm/rgarnett/lights-out-inference/runs/flashinfer-ssu-5f29e0eb-before-after-20260916-125122/`.
The directory contains `report.md`, the benchmark scripts, per-round
CSVs, raw timing samples, numerical errors, loaded binary hashes, and
environment metadata. Slurm job `595820` completed successfully. These
artifacts require internal access.

GPU test provenance: Slurm job `595895` completed with exit `0:0` in
17m59s. Full pytest logs, JUnit XML, per-case outcomes and environment
metadata are under
`/lustre/fsw/coreai_nvfm_llm/rgarnett/lights-out-inference/runs/flashinfer-sm107-tests-cc5a53a6-20260916-132253/`
on `login-hecate`.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added hardware-accelerated stochastic rounding support for SM107
(Rubin) GPUs, alongside SM100 and SM103.
* Updated FP16 and FP8 conversion support to recognize SM107-compatible
hardware.
* **Bug Fixes**
* Improved capability detection so supported architectures are
identified consistently.
* **Tests**
* Updated hardware compatibility checks and unsupported-device messages
to include SM107 GPUs and the supported architecture list.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: Roi Garnett <rgarnett@nvidia.com>

### [6973044](https://github.com/flashinfer-ai/flashinfer/commit/69730446181dfb2e0324832cbf1e6399c2b74371)

- **作者**: Mingyang Wang
- **时间**: 2026-10-05T18:05:53Z
- **提交信息**: Enable MLA auto-selection on SM103 and SM107 (#5984)

<!-- .github/pull_request_template.md -->

## 📌 Description

Enable planned MLA auto-selection on SM103 and SM107 using the SM100
ordering. SM107 has its own delegation entry point to allow future
architecture-specific tuning.

Enable TRT-LLM gen, CuTe DSL and cuTile support on SM107 while
preserving backend eligibility checks and cuTile experimental opt-in.
Keep the measured small-head, noncausal Q4 correction that prefers FA2
over modular CuTe; Q3 ordering is unchanged. Remove the obsolete
Blackwell auto-fallback warning and update focused regression tests and
architecture documentation.

## 🔍 Related Issues

Follow-up to #5712 and #5463.

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

Validation: 287 targeted CPU policy/contract tests passed (zero failures
or skips). Changed-file pre-commit checks, including mypy and Ruff,
passed; diff checks passed. The all-files hook and all-tests checkboxes
above are left unchecked because validation was targeted.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added automatic MLA backend selection for SM107, with fallback to
compatible backends.
* Expanded SM107 support across cuTile, TRTLLM-GEN, and CuTe DSL,
subject to compiler and toolkit availability. cuTile selection remains
experimental-gated.
* Added SM107 support for matching BF16 and FP8 E4M3 inputs in
TRTLLM-GEN; FP16 is not supported.
* Documented CuTe DSL target requirements for SM107 when native target
support is unavailable.

* **Bug Fixes**
  * Improved backend selection for certain small-head Q4 workloads.
  * Updated FP8 KV scaling behavior for supported architectures.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [188bdd7](https://github.com/flashinfer-ai/flashinfer/commit/188bdd769dbb06a4846fb059d5ed4a6a24373cd8)

- **作者**: eigen
- **时间**: 2026-10-05T09:28:26Z
- **提交信息**: perf(cake_nvfp4_attn): warp-specialised attention form for the MiniMax-H3 SM120 NVFP4 varlen attention, selected per call on RTX PRO 6000 (#6060)

Regenerated
`csrc/cake_minimax_h3_sm120_nvfp4_varlen_attention_sm120a.cu`: two
kernels and a host-side selector added; the existing
kernels are the same programs as in #5660 (identical IR, bit-exact
outputs), rendered by the current exporter, which also brings this
TU the host-helper sharing of #5905 (`cake_minimax_h3_sm120_host.cuh`,
already in `csrc/`) and the generator's de-duplicated device
helpers / `LAUNCH_MIN_BLOCKS` launch-bounds macro that the other
MiniMax-H3 SM120 TUs already carry. Both host entries
(`minimax_h3_sm120_varlen_attention_nvfp4`, `_nodelta`) keep their
signatures and contracts.

**What changes**
- Two new device kernels: the warp-specialised form of the compensated
and of the uncompensated attention program (8 QK/softmax
warps + 4 PV warps, 384 threads, one CTA per SM). Same FP32 operations
in the same order as the existing kernels -> bit-exact
outputs (verified on all 13 contract shapes on RTX 5090 and RTX PRO 6000
Blackwell).
- Host selector: the new kernel is launched when the mean segment length
(`tokens / segments`) is >= 1536 tokens and the device has
>= 188 SMs (RTX PRO 6000); every other call runs the existing kernel.
Numerics-neutral by construction (one of two bit-exact kernels).

**Measured (RTX PRO 6000 Blackwell Server Edition, paired ABAB CUPTI
cold-L2, complete operator, 56 heads x 128)**
| Shape (cu_seqlens) | existing kernel op ms | new selector op ms |
operator speedup (min..max of 3 paired groups) | attention launch
speedup | uncompensated entry speedup |
|---|---|---|---|---|---|
| center_4s (0,33472) | 37.954 | 36.770 | **1.0330** (1.0322..1.0379) |
1.0401 (1.0381..1.0418) | 1.0399 (1.0383..1.0424) |
| center_5s (0,38592) | 50.294 | 48.562 | **1.0357** (1.0337..1.0370) |
1.0372 (1.0347..1.0416) | 1.0405 (1.0390..1.0432) |
| center_6s (0,48768) | 79.592 | 76.937 | **1.0345** (1.0328..1.0347) |
1.0382 (1.0373..1.0401) | 1.0393 (1.0390..1.0393) |
| center_8s (0,58944) | 116.001 | 112.051 | **1.0352** (1.0317..1.0379)
| 1.0331 (1.0331..1.0369) | 1.0415 (1.0321..1.0432) |
| center_10s (0,74240) | 182.998 | 177.308 | **1.0332** (1.0321..1.0355)
| 1.0365 (1.0336..1.0366) | 1.0365 (1.0352..1.0397) |
| center_15s (0,109952) | 401.544 | 388.490 | **1.0339**
(1.0336..1.0340) | 1.0344 (1.0340..1.0357) | 1.0347 (1.0344..1.0364) |
| tail_5s_a (0,38531) | 50.781 | 49.037 | **1.0356** (1.0345..1.0364) |
1.0375 (1.0371..1.0379) | 1.0433 (1.0421..1.0434) |
| tail_5s_b (0,38629) | 50.765 | 49.041 | **1.0351** (1.0343..1.0354) |
1.0371 (1.0362..1.0383) | 1.0423 (1.0415..1.0455) |
| pad_15s (0,109901,109952) | 401.478 | 387.689 | **1.0356**
(1.0347..1.0369) | 1.0356 (1.0338..1.0357) | 1.0352 (1.0312..1.0357) |
| seg4 (0,8368,16736,25104,33472) | 11.805 | 11.259 | **1.0485**
(1.0480..1.0506) | 1.0507 (1.0493..1.0510) | 1.0479 (1.0475..1.0480) |
| seg3_ragged (0,257,4567,4824) | 0.924 | 0.878 | **1.0519**
(1.0509..1.0526) | 1.0835 (1.0830..1.0845) | 1.0598 (1.0593..1.0601) |
| seg_empty (0,0,129,129,500) | 0.056 | 0.056 | **1.0069**
(1.0065..1.0071) | 1.0124 (1.0124..1.0124) | 1.0065 (1.0059..1.0068) |
| single_4096 (0,4096) | 0.792 | 0.750 | **1.0564** (1.0564..1.0574) |
1.1089 (1.1079..1.1104) | 1.0660 (1.0658..1.0661) |

All 13 shapes bit-exact against the existing kernel (max |diff| 0) and
idempotent; `seg_empty` runs the existing kernel (mean segment below the
threshold). Tree: Cake kernel tree 736f44258c0, step 10720492
(2026-10-05).

RTX 5090: the form needs 8 % fewer cycles (ncu, locked clocks) but
lowers the sustained clock ~7 % at the 575 W power cap, so the
gain is board-dependent (+4.5 % to -3.3 %); the selector keeps the
existing kernel on 170-SM parts (bit-identical behaviour).

Baselines carried from #5660 / #5629 / #5595 / #5583 / #5545 (all-shape
tables in the Cake design doc; ragged SageAttention3
d1a57a546c3 + CUTLASS 0b55a2f6 same-session comparison: RTX PRO 6000
1.19-1.34x on the single-segment shapes 33472..109952 (1.80x / 2.69x /
1.76x on the 4-segment, 3-segment ragged and 4096 shapes); RTX 5090
(existing kernel) 1.07-1.20x / 1.56x / 2.35x / 1.56x).

Tracker: #4254. Tests:
`tests/diffusion_ops/test_minimax_h3_sm120_nvfp4_varlen_attention.py`
and `..._nodelta.py` (unchanged;
shapes (0, 257, 4567, 4824) and (0, 4097) exercise the new kernel on >=
188-SM parts) -- 17 passed + 2 skipped / 17 passed on RTX PRO 6000 (new
kernel exercised) and on RTX 5090, FlashInfer 745b12352 with this TU and
the `csrc/cake_minimax_h3_sm120_host.cuh` header of #5905.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [f7a4874](https://github.com/flashinfer-ai/flashinfer/commit/f7a4874ccf0926ac9ba32e259b0d5c940bdc1c4a)

- **作者**: eigen
- **时间**: 2026-10-05T09:27:17Z
- **提交信息**: feat(cake_mega_moe): pre-reduced BF16 combine wire and fixed-cost levers for the SM90 MegaMoE backend (#6058)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

## Summary

Round 2 of the Hopper native BF16 MegaMoE backend
(`sm90_bf16_bf16_bf16_push_cake`): pre-reduced combine wire, protocol
fixed-cost levers and a re-rendered grouped-GEMM epilogue. Follow-up to
#5958 (`sm90_bf16_bf16_bf16_push_cake`, the Hopper native BF16 MegaMoE
backend through `MoEEpLayer`). Part of #4254; round-2 discussion in
#5708. One export commit on top of main, regenerated from the merged
generator state; the whole path stays BF16 operands / fp32 accumulation,
no FP8, no fast-math.

## What changed

**Combine wire** (the only numerics change; deterministic)
- `combine_wire="prereduced"` (new): each expert rank pre-reduces, in
fp32 (`fmaf`) and in ascending route order, the routes of a token that
it computed, rounds once to bf16 and publishes one row per (token,
source rank) into the owner's inbox. The owning rank sums the per-rank
rows in ascending rank order in fp32 and rounds once. Inbox traffic
drops from `T * top_k` rows to `T * world` rows (EP8, top-8: 7.0 to 4.6
rows per token on uniform routing).
- `combine_wire="prereduced_hilo"` (new): the pre-reduced row plus a
bf16 residual row for multi-route groups; a precision-conservative
variant kept selectable (it is not faster).
- `combine_wire="per_route"`: the round-1 wire (one row per route),
unchanged and bitwise identical to #5958.
- **Default** (`combine_wire=None`, env unset): `per_route` when the
per-rank token capacity is `<= 8`, `prereduced` above.
`FLASHINFER_SM90_CAKE_BF16_COMBINE_WIRE=prereduced|prereduced_hilo|per_route`
overrides. All ranks must agree; the construction-time allgather rejects
mismatches with `MoEEpConfigError`.
- Determinism: fixed accumulation order (routes ascending within a rank,
ranks ascending across ranks), no fp32 atomics on outputs or partial
sums; bitwise run-to-run; eager == CUDA graph.

**Protocol fixed-cost levers** (output bit-identical to round 1):
publish scratch self-resets instead of four per-round memsets; the
pre-reduced worklist is built inside the compact pass (one launch
fewer); grid completion counts participating blocks only; compact
assigns rows by static grid stride instead of an atomic work queue;
publish groups are split across blocks at decode sizes.

**Grouped-GEMM epilogue** (sealed sources re-rendered from the
generator; output bit-identical): bf16x2 pack, quad transpose and
16-byte stores (FC1+FC2 +4.5 % at T >= 1024; no register or spill
change, 168 regs).

## Validation

### Numerics

Against an independent fp32 reference over the 290 EP1/EP2/EP4/EP8 test
cases (max-abs, mean-abs, rel-L2 per case): the pre-reduced wire's
aggregate mean-abs is 0.000888 vs 0.000974 for round 1 and rel-L2
0.00341 vs 0.00365; 6/290 cases have a max-abs one bf16 ulp above round
1 (outputs with |y| in [2, 4)), with lower mean-abs and rel-L2 on those
cases. Per-case rel-L2 differs from round 1 by at most +0.33 %. The
`atol=rtol=1e-2` test gate is unchanged. With the per-shape default,
rounds with per-rank token capacity `<= 8` keep round-1 numerics
bitwise.

### Performance

One 8xH100 node (NVLink), CUDA graph replay, CUPTI kernel time (cold L2)
over dispatch + FC1 + FC2 + combine, max over ranks; paired same-process
A/B against the round-1 backend (#5958) with rotated ABBA blocks, two
independent sessions per row, pooled median and 95 % bootstrap CI.
Geometries: A = hidden 7168, intermediate 2048, 256 experts, top-8; B =
7168 / 3072 / 384 / top-6; C = 4096 / 2048 / 256 / top-6. Rows are
speedups (> 1 = this PR faster) with `combine_wire=prereduced`:

| EP | geometry | T=8 | 16 | 32 | 64 | 128 | 512 | 1024 | 2048 | 4096 |
|---|---|---|---|---|---|---|---|---|---|---|
| 8 | A | 1.002 | 1.005 | 1.004 | 1.007 | 1.009 | 1.057 | 1.076 | 1.082
| 1.092 |
| 8 | B | 1.011 | 1.002 | 1.002 | 1.001 | 1.004 | 1.017 | 1.035 | 1.057
| 1.049 |
| 8 | C | 0.998 | 1.003 | 1.002 | 1.003 | 1.007 | 1.023 | 1.060 | 1.073
| 1.077 |
| 4 | A | 1.002 | | | | 1.008 | | 1.079 | | 1.117 |
| 2 | A | 1.003 | | | | 1.003 | | 1.037 | | 1.095 |

- Geomean 1.031 over the 35 rows; 33/35 rows improved (CI lower bound >
1); informational T=8192 (EP8 A) 1.103. Stage breakdown at EP8 A T=4096
(6411 vs 7036 us): publish -401 us (wire), FC2 -159 us and FC1 -39 us
(epilogue), wait -40 us, tail -14 us, compact +26 us.
- Against the split `nccl_ep` + CUTLASS BF16 path (the fastest
numerically valid split arm per row): geomean 1.55, faster on 33/35
rows; the two remaining rows (EP4 A and EP2 A at T=8) are within 0.7 %
and are the push protocol's per-round fixed cost against nccl LL, shared
with round 1.
- At T=8 per rank the shipped default selects `per_route`, so those rows
run round-1 code and time (paired A/B within the +-0.1 % measurement
floor of a 0.6-1.6 ms round).
- Eager mode (reported, not the acceptance number): geomean 1.031 vs
round 1; 1.71 vs the split path.

### Tests

- `tests/moe_ep/test_sm90_bf16_push_cake_frozen_sources.py`: the sealed
GEMM sources and the new combine sources are covered by the manifest
seal.
- `tests/moe_ep/test_sm90_bf16_push_cake_backend.py`: EP1 cases for
every wire (uniform, cross-rank skew, hotspot, empty experts, masked
routes, duplicate routes to one rank, duplicate remote/local routes,
boundary capacities), the per-shape default at both sides of the
threshold and both overrides, wire-mismatch rejection, workspace reuse,
eager vs graph bitwise, 3x run-to-run bitwise; EP2/EP4/EP8 under
`torchrun` with per-rank validation. `run_tests.sh sm90_bf16_push_cake`
section.
- Multi-rank `compute-sanitizer` synccheck + memcheck on the new/changed
kernels: 0 errors (EP2/EP4), with a negative control that fires.
- `benchmarks/bench_moe_ep_sm90_bf16_mega.py --combine-wire
{prereduced,prereduced_hilo,per_route}` for paired A/B.

### Docs

`docs/design_docs/moe_ep_architecture.md` and
`docs/design_docs/moe_ep_runbook.md`: wire semantics and selection,
determinism note, benchmark flag.

### Files (21)

- New:
`flashinfer/moe_ep/kernel_src/sm90/cake_bf16_megamoe/src/cake_combine_prereduced_bf16.cu`,
`src/cake_combine_tail_prereduced_bf16.cu`.
- Changed: `shim/cake_jit.py`, `shim/cake_runner.py`,
`shim/__init__.py`, package `__init__.py`, `src/cake_compact_bf16.cu`,
the six sealed GEMM kernel/binding sources and
`cake_sm90_bf16_megamoe_manifest.json`,
`backends/mega/kernel/sm90/bf16_bf16_bf16_push_cake/{cake_config.py,cake_backend.py}`,
the two tests, the reference module, the benchmark and the two docs.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added selectable SM90 BF16 MoE combine formats: `prereduced`,
`prereduced_hilo`, and `per_route`, with token-capacity-based defaults
and an optional environment override.
  * Added benchmark options for selecting and comparing combine formats.
* **Bug Fixes**
* Improved handling of overlapping communication rounds across CUDA
streams and validation of inconsistent format selections across ranks.
* **Documentation**
* Expanded guidance on format selection, compatibility, reduction
behavior, rounding, and validation.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-10-06
**监控日期**: 2026-10-05
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4549
- **最后更新**: 2026-10-05T15:28:28Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-10-06
**监控日期**: 2026-10-05
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34658
- **最后更新**: 2026-10-06T02:12:22Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 3
- **主要提交者**: Aritra Roy Gosthipaty, Sayak Paul, naykun

## AI分析总结

# huggingface/diffusers 昨日提交分析

## 1. 主要更新类型

本次提交涉及**功能新增**（Echo 模块化管线、Qwen 采样参数配置）、**重构**（注意力处理器测试清理）、**Bug/废弃处理修复**（移除 Siglip2ImageProcessorFast）以及**文档更新**（采样 sigmas 说明）。整体以维护性开发为主，兼顾新模型管线的实验性落地。

## 2. 关键变更点与项目方向的关系

- **QwenImage21Pipeline 配置化采样 sigmas**：允许用户在管线层面固定采样步长分布，而非依赖默认值。这与 diffusers 近期持续扩展图像生成类管线（尤其是大厂私有/开放权重模型）的方向一致，强调参数可配置性和复现性。
- **Echo 模块化管线**：新增一条完整的模块化管线（含输入归一化内联、latent 边界与批扩展对齐、官方权重加载、分块测试与文档润色）。这反映了项目通过 "modular" 管线机制让社区快速集成新架构的策略，Echo 本身带有团队协作/学术项目色彩（合作方为 Gelercatty）。
- **注意力处理器测试重构**：删除独立 utils.py，将测试逻辑收敛到管线级用例中，属于降低维护成本、统一测试入口的标准化工作。
- **Siglip2ImageProcessorFast 弃用移除**：跟进上游处理器 API 变化，移除不再推荐的 fast processor，减少用户配置困惑。

## 3. 对项目的影响和潜在意义

- 对普通用户而言，**Qwen 管线采样行为更透明可控**，文档补充降低了误用概率。
- **Echo 管线**为项目提供了新的社区集成范例，展示了从贡献者 PR 到官方主线的完整流程，对鼓励模块化贡献有示范意义。
- **测试重构**提升了 CI 可维护性，但短期内对下游行为无可见影响。
- **Siglip2 fast processor 移除**是一次破坏性/清理性变更，使用该处理器的旧代码需迁移到默认 processor 路径。

## 4. 值得关注的技术点

- **采样 sigmas 的管线级固定机制**：涉及调度器（scheduler）与管线采样循环的解耦设计，值得关注其 API 形态（是否向其他管线推广）。
- **Echo 管线的 latent 边界与批扩展对齐**：这类细节往往是自定义管线常见的隐性 bug 来源，贡献者专门修正说明团队对数值一致性的重视。
- **测试中删除 utils.py、内联处理逻辑**：体现了"减少测试辅助抽象、让被测代码路径更接近生产"的测试理念。

## 5. 对项目发展的综合影响

结合 README 背景，diffusers 作为 HuggingFace 官方的扩散模型库，目标是为社区提供统一、可扩展的生成式模型基础设施。这批提交体现了三条主线：**一是持续丰富对新模型（Qwen、Echo）的官方级支持**，降低用户接入门槛；**二是通过 modular 管线机制让模型集成流程标准化**，维持开源贡献的可持续性；**三是技术债清理与 API 治理**，如测试重构和废弃处理器的移除，保证库长期可维护。这些工作共同巩固了项目"快速吸纳社区创新、同时保持工程质量"的核心竞争力，对后续更多私有/新兴扩散架构的落地具有铺垫意义。

## 详细提交记录

### [da1d382](https://github.com/huggingface/diffusers/commit/da1d3829cf08d4f329b526d89e17cc035c049d8d)

- **作者**: naykun
- **时间**: 2026-10-05T19:11:49Z
- **提交信息**: Configure fixed sampling sigmas on QwenImage21Pipeline (#14950)

* feat(qwenimage21): configure sampling sigmas on the pipeline

* docs(qwenimage21): clarify default and runtime sampling sigmas

### [c2798cc](https://github.com/huggingface/diffusers/commit/c2798cc7859f258c6cfc5b2460e82b6cac71f235)

- **作者**: Sayak Paul
- **时间**: 2026-10-05T10:08:23Z
- **提交信息**: [tests] refactor the pipeline-level attention processor tests (#14701)

* refactor the pipeline-level attention processor tests

* simplify stuff.

* remove utils.py

### [cff9daf](https://github.com/huggingface/diffusers/commit/cff9dafbbf493e2a08c6f1951fb2d8845da71841)

- **作者**: Sayak Paul
- **时间**: 2026-10-05T08:34:27Z
- **提交信息**: [modular] Echo team joy future academy jd echo by @Gelercatty (#14941)

* Add Echo modular pipeline

* Address Echo modular pipeline review feedback

* Inline Echo input list normalization

* Align Echo latent boundaries and batch expansion

* Polish Echo documentation per review

* Load official Echo checkpoint and separate block tests

* consolidate testing.

* formatting

---------

Co-authored-by: Yanwen Ma <gelercat117@gmail.com>

### [9aababd](https://github.com/huggingface/diffusers/commit/9aababd75583bc178ff8c5c8ffe394b76170b8d4)

- **作者**: Aritra Roy Gosthipaty
- **时间**: 2026-10-05T08:23:28Z
- **提交信息**: Fix: Deprecating Siglip2ImageProcessorFast (#14781)

remove fast processor

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-10-06
**监控日期**: 2026-10-05
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


**报告日期**: 2026-10-06
**监控日期**: 2026-10-05
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13203
- **最后更新**: 2026-10-05T12:42:49Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-10-06
**监控日期**: 2026-10-05
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 36803
- **最后更新**: 2026-10-06T02:18:42Z

## 提交统计

- **昨日提交总数**: 32
- **提交者数量**: 21
- **主要提交者**: ADiL, elvischenv, liuke

## AI分析总结

# sgl-project/sglang 昨日提交分析（共32条）

## 1. 主要更新类型

- **功能新增**：约12条，涵盖投机解码、异步输出、LoRA配方、DeepEP v2预填充分发等
- **性能优化**：约13条，集中在diffusion视频生成路径（VAE解码、RoPE缓存、kernel融合）和推理内核层面
- **Bug修复**：约6条，包括QKV布局、IPv6调度、FP8 KV cache等
- **重构/文档**：约4条，如sgl-router策略重构、设计文档更新、cookbook文档整理

## 2. 关键变更点及与项目方向的关系

- **Diffusion模块成为绝对焦点**（约19条提交），项目正在大力扩展多模态图像/视频生成能力，支持MiniMax-H3、LTX-2等视频模型，优化从DiT到VAE的完整推理链路，这与README中"多模态模型快速推理"的目标高度一致。
- **sgl-router持续演进**：引入balanced mode改进、reorg bucket配置、per-group admission控制，以及压力/前缀信号从旧策略迁出，表明路由层正在向更精细的负载均衡和弹性伸缩方向发展。
- **投机解码与内核级优化并行**：block verification、XQA draft extend FP8修复、MiMo音频注意力优化、DeepEP v2预填充等，持续夯实LLM推理的核心性能。

## 3. 对项目的影响和潜在意义

- Diffusion子系统正从"可用"走向"生产级"：通过异步输出保存、启动预热、OOM保护、多GPU FSDP修复等，显著提升视频生成服务的稳定性与吞吐量，为将sglang定位为统一的LLM+多模态推理引擎奠定基础。
- Router层的重构表明项目在为更大规模集群部署做准备，精细化的准入控制和负载信号迁移有利于企业级部署场景。
- 大量AMD/ROCm贡献和硬件适配（gfx942、HIP kernel）说明项目在积极拓展多硬件生态。

## 4. 值得关注的技术点

- **视频生成链路的性能工程**：VAE解码中RMSNorm+QK RoPE融合、全视频clone消除、RoPE坐标缓存、256-token逻辑页池（DSA k-pool）等都是针对视频推理高开销的精准优化。
- **投机解码的鲁棒性**：DFlash2对全NaN行的处理、block verification opt-in，表明项目在推动投机解码走向更安全的生产可用状态。
- **DeepEP v2预填充扩展**：do_expand=True的pre-fill dispatch支持，对MoD/分布式推理有重要价值。
- AI编程工具（Claude、Cursor、Devin）作为共同贡献者的高频出现，反映AI辅助开发已成为该项目的常态工作流。

## 5. 对项目发展的综合影响

从README看，sglang定位为LLM和多模态模型的快速推理引擎。本次提交表明项目发展呈现两条主线：一是**LLM推理核心持续精进**（投机解码、分布式内核、路由优化）；二是**多模态生成能力的快速补全**，特别是视频扩散模型的推理路径正被系统性地优化和加固。Diffusion模块的密集投入意味着sglang正从"LLM推理框架"向"统一多模态推理平台"转型，这将帮助其在与vLLM等竞品的差异化竞争中占据多模态生成场景的先机。

## 详细提交记录

### [968726f](https://github.com/sgl-project/sglang/commit/968726f3cea0f6d6f44bea84797e5e5914658f4e)

- **作者**: ADiL
- **时间**: 2026-10-05T22:33:49Z
- **提交信息**: [HiCache] Route --file-storage-path to the file storage backend (#33883)

Signed-off-by: adlashab <adlashab@amd.com>

### [61ba984](https://github.com/sgl-project/sglang/commit/61ba98443d2a9e67b79b06b01ee227515bf3c9ea)

- **作者**: Khoa Pham
- **时间**: 2026-10-05T22:02:44Z
- **提交信息**: [DSA] k-pool: 256-token logical page so index page id = logical page id (#42178)

Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Ke Bao <ispobaoke@gmail.com>

### [c765f88](https://github.com/sgl-project/sglang/commit/c765f8818afae5a4eaa91bc7708e99e1026330ef)

- **作者**: rodamani
- **时间**: 2026-10-05T21:29:13Z
- **提交信息**: [DFlash2] Keep the greedy selector walk in range for all-NaN score rows (#41737)

Co-authored-by: Rahul Chalamala <22563365+rchalamala@users.noreply.github.com>
Co-authored-by: Devin AI <158243242+devin-ai-integration[bot]@users.noreply.github.com>

### [57826a6](https://github.com/sgl-project/sglang/commit/57826a62ea082624c414e8adcef61bfb578dddc7)

- **作者**: maocheng23
- **时间**: 2026-10-05T18:49:23Z
- **提交信息**: [Speculative] Add opt-in block verification (#42297)

### [70f0b73](https://github.com/sgl-project/sglang/commit/70f0b7351e74b372cc928db533824d3993d65922)

- **作者**: Kan Wu
- **时间**: 2026-10-05T16:48:37Z
- **提交信息**: [sgl-router] Improved policy balanced mode (#42545)

Co-authored-by: Kan Wu <kan.wu@MacBook-Pro.local>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Kan Wu <kan.wu@radixark.ai>

### [efb62ce](https://github.com/sgl-project/sglang/commit/efb62ce269b499123e2d1c89005ee4cea8c31098)

- **作者**: debanshd
- **时间**: 2026-10-05T15:01:37Z
- **提交信息**: [diffusion] fix: resolve QKV layout inference for MiniMax-H3 checkpoints (#40158)

Signed-off-by: Debanshu Das <debanshu@google.com>

### [150f568](https://github.com/sgl-project/sglang/commit/150f568900db878ed3cf179ae896805d78c55747)

- **作者**: Mick
- **时间**: 2026-10-05T14:21:01Z
- **提交信息**: [diffusion] kernels: stop specializing on per-request sequence lengths (#41710)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [a977e3b](https://github.com/sgl-project/sglang/commit/a977e3b9d517a1eb16e68ae5c6b06562073d661a)

- **作者**: Mick
- **时间**: 2026-10-05T13:58:27Z
- **提交信息**: [diffusion] optimization: stream an oversized DiT in auto mode instead of OOMing (#41721)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [ad3e80d](https://github.com/sgl-project/sglang/commit/ad3e80d4de6808a77428eb651b30d831fe41b67b)

- **作者**: Mick
- **时间**: 2026-10-05T13:58:00Z
- **提交信息**: [diffusion] chore: warm the image writer and the HTTP route models at startup (#41833)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [c83c84b](https://github.com/sgl-project/sglang/commit/c83c84b422a96d46460de60c18fa4c5427d6a444)

- **作者**: Mick
- **时间**: 2026-10-05T13:56:52Z
- **提交信息**: [diffusion] chore: keep the DiT off component offload under explicit multi-GPU fsdp (#41722)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [23bf107](https://github.com/sgl-project/sglang/commit/23bf10746973aaf8a027a8ce6ffb4b0b1cccce43)

- **作者**: wxy
- **时间**: 2026-10-05T13:21:36Z
- **提交信息**: [diffusion] optimization: cache LTX-2 RoPE coords to avoid per-step recompute (#22441)

### [91f9bf8](https://github.com/sgl-project/sglang/commit/91f9bf8d179f411d0724821638f74840e15661bc)

- **作者**: Shiwen Cheng
- **时间**: 2026-10-05T13:14:09Z
- **提交信息**: [diffusion] fix: fix scheduler host not working when ipv6 in multi modal gen (#22813)

### [f20f8e1](https://github.com/sgl-project/sglang/commit/f20f8e120dbcdfbd5a05030d08af802a46903e13)

- **作者**: liuke
- **时间**: 2026-10-05T13:10:06Z
- **提交信息**: [diffusion] model: restore folded H3 GGUF patch embedding (#39523)

Co-authored-by: Mick <mickjagger19@icloud.com>

### [83a6e1d](https://github.com/sgl-project/sglang/commit/83a6e1d39b465034dd78f63bce255f07e2851521)

- **作者**: Mick
- **时间**: 2026-10-05T12:02:43Z
- **提交信息**: [diffusion] docs: keep model compatibility details in cookbook recipes (#42227)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [860ebe7](https://github.com/sgl-project/sglang/commit/860ebe720efe458b8752bbb1d4b20b7cbf16e629)

- **作者**: Akshat Anand
- **时间**: 2026-10-05T11:59:35Z
- **提交信息**: [diffusion] fix: skip warmup preferred preload when it would OOM (#40761)

Co-authored-by: cipheraxat <cipheraxat@users.noreply.github.com>

### [8663e3b](https://github.com/sgl-project/sglang/commit/8663e3b670b3250892cd9aeb3ab77b43dfb74a17)

- **作者**: aiyueqi
- **时间**: 2026-10-05T11:56:11Z
- **提交信息**: [diffusion] optimization: avoid full-video clone in VAE post-processing for MiniMax-H3 (#40095)

Co-authored-by: Mick <mickjagger19@icloud.com>

### [d349e67](https://github.com/sgl-project/sglang/commit/d349e672bc7eefb532010ec7830bff0ed682bc0e)

- **作者**: Mick
- **时间**: 2026-10-05T11:55:30Z
- **提交信息**: [diffusion] feat: recycle warmup-only entries of conditioning-cache at the first served store (#41832)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [7352073](https://github.com/sgl-project/sglang/commit/7352073ec64faf21b08d52d6690b72f341636935)

- **作者**: Yihao Wang
- **时间**: 2026-10-05T11:53:38Z
- **提交信息**: [diffusion] feat: support --async-output-save to overlap output saving with the next request (#37549)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [f048d5a](https://github.com/sgl-project/sglang/commit/f048d5aa4bc1bcad7fa2c60d067590d83d6dbe4a)

- **作者**: WenhaoZhang
- **时间**: 2026-10-05T10:22:56Z
- **提交信息**: [diffusion] feat: add community LoRA recipes and Kohya mapping (#35857)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [08fa37e](https://github.com/sgl-project/sglang/commit/08fa37e48d003910dff0facc7a3792eaced2515a)

- **作者**: Kan Wu
- **时间**: 2026-10-05T10:17:32Z
- **提交信息**: [sgl-router] Add reorg bucket config with per-group admission (#42429)

Co-authored-by: Kan Wu <kan.wu@radixark.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Kan Wu <kan.wu@MacBook-Pro.local>

### [ab4f8a4](https://github.com/sgl-project/sglang/commit/ab4f8a44f43887725a8f3635ad155cd74ce1f67d)

- **作者**: Shangming Cai
- **时间**: 2026-10-05T10:16:42Z
- **提交信息**: [sgl-router] Point the design doc at the shared engine ranking (#42572)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [a96b146](https://github.com/sgl-project/sglang/commit/a96b1464917805fa5edb167242f5be32eab8ea57)

- **作者**: Kan Wu
- **时间**: 2026-10-05T10:10:29Z
- **提交信息**: [sgl-router] Move pressure and prefix signals out of legacy policies (#42428)

Co-authored-by: Kan Wu <kan.wu@radixark.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [26a1377](https://github.com/sgl-project/sglang/commit/26a1377c5016bd3df7dada250686dcc45e1aa547)

- **作者**: mrusanovsky
- **时间**: 2026-10-05T09:43:59Z
- **提交信息**: [Spec] LiLiCorr: named head MLPs and quantized head linears (#42057)

Co-authored-by: Po-Han Huang (NVIDIA) <53919306+nvpohanh@users.noreply.github.com>

### [284cda0](https://github.com/sgl-project/sglang/commit/284cda01fb2c029892c421844fb1e1fe90f930e1)

- **作者**: WenhaoZhang
- **时间**: 2026-10-05T09:30:39Z
- **提交信息**: [diffusion] optimization: fuse the video VAE decoder's RMSNorm and QK RoPE for MiniMax-H3 (#41906)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [0263fda](https://github.com/sgl-project/sglang/commit/0263fdacb223e92035ebc947f098ba724ee5634f)

- **作者**: Mick
- **时间**: 2026-10-05T09:23:06Z
- **提交信息**: [diffusion] fix: keep generic warmup valid for step-floored models and stop reporting a failed warmup as warm (#41641)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [55dcf32](https://github.com/sgl-project/sglang/commit/55dcf3254fa9e42d536971a952b273d7a2e29bfa)

- **作者**: elvischenv
- **时间**: 2026-10-05T08:37:54Z
- **提交信息**: Fix XQA draft extend with FP8 KV cache in trtllm_mha (#41656)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [abd6c37](https://github.com/sgl-project/sglang/commit/abd6c374c71c53ce59a83f96a56e02a07218e50a)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-10-05T08:14:56Z
- **提交信息**: [Perf] Optimize MiMo local audio attention on Hopper (#42101)

### [b3f967e](https://github.com/sgl-project/sglang/commit/b3f967e8094dec6d965acbc27a38d09b5c3bf555)

- **作者**: Michael
- **时间**: 2026-10-05T08:12:21Z
- **提交信息**: Revert "Revert "[AMD][ROCm] Keep cos_sin_cache fp32 on HIP for fused QSA indexer kernel (#41282)"" (#42558)

### [9f7d38f](https://github.com/sgl-project/sglang/commit/9f7d38ffd3c463f103942bfdfe1cab1886b4c97b)

- **作者**: Aleksi Vesanto
- **时间**: 2026-10-05T07:22:53Z
- **提交信息**: [diffusion] attention: Allow disabling sequence masking in SP (#33855)

Co-authored-by: jacky.cheng <yichiche@amd.com>

### [c41b2d2](https://github.com/sgl-project/sglang/commit/c41b2d26e551a1628fc3c1c866b8cf0686e090e6)

- **作者**: Aleksi Vesanto
- **时间**: 2026-10-05T07:21:04Z
- **提交信息**: [diffusion][ROCm][Perf]: Set gfx942 AITER FMHA rounding mode to rtz instead of rtna (#28650)

Co-authored-by: jacky.cheng <yichiche@amd.com>

### [dd2ffdb](https://github.com/sgl-project/sglang/commit/dd2ffdb68058c96dec2b7d0fb707b50efc4f103e)

- **作者**: Mick
- **时间**: 2026-10-05T07:19:21Z
- **提交信息**: [diffusion] nightly: keep nightly regression baselines on a comparable methodology (#42226)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [438d9d2](https://github.com/sgl-project/sglang/commit/438d9d2074a2abfaf67b7247f2a8e5f87ff09ac8)

- **作者**: Ziyang Zhang
- **时间**: 2026-10-05T07:02:10Z
- **提交信息**: [Feature] DeepEP v2: expanded (do_expand=True) prefill dispatch (#37261)

Co-authored-by: Cheng Wan <cheng.wan@radixark.ai>
Co-authored-by: Cheng Wan <54331508+ch-wan@users.noreply.github.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-10-06
**监控日期**: 2026-10-05
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1288
- **最后更新**: 2026-10-03T18:50:23Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-10-06
**监控日期**: 2026-10-05
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 93229
- **最后更新**: 2026-10-06T02:18:10Z

## 提交统计

- **昨日提交总数**: 44
- **提交者数量**: 35
- **主要提交者**: charlesli640, roikoren755, Martin Hickey

## AI分析总结

# vLLM 仓库昨日提交分析（第 1/1 批，共 44 个提交）

## 一、主要更新类型

- **Bug 修复**（约 20 个）：占据最大比例，覆盖投机解码、MoE 路由、前端渲染、多模态缓存、NIXL 分布式传输等核心链路
- **性能优化**（约 10 个）：集中在 Qwen4Exp（QSA 注意力融合）、ROCm/AMD 平台（hipBLASLt、QSA pre-indexer）、SM121 瘦 GEMM 等
- **功能新增**（约 8 个）：Nemotron 3.5 ASR 转录、Transformers 后端视频支持、HiSparse 指标暴露、GLM-5.3-Flash DCP 等
- **CI/构建维护**（约 6 个）：ROCm 测试等待引擎清理、profiler 测试修复、CODEOWNERS 补充
- **重构与清理**：LoRA 移除 tensorizer、前端批次聊天去渲染的解析/组装提取
- **安全加固**：限制不可信媒体路径的 Pillow 图像格式

## 二、关键变更与项目方向的关系

结合 README 中"为每个人提供简单、快速、廉价的 LLM 服务"这一目标，本批提交体现了几个与项目战略高度一致的方向：

1. **投机解码全面修复与调优**：多条提交（#56531、#57053、#59105、#59975、#52824）系统性地修复了投机解码中 recurrent state 一致性、动态 K 值（1.2~1.3x kernel 性能提升）、DSpark bonus KV 槽位、Mamba 页大小 AssertionError 等问题，强化了这一核心降本增效机制的可靠性。
2. **Qwen4Exp 系列深度优化**：约 5 条提交围绕 QSA 注意力做融合（QKVG 与 indexer QK 投影合并、HC 上投影走瘦 GEMM、PLE 表加载修复、kv-cache-dtype-skip-layers 支持），直接服务于新兴高效架构模型的性能竞争力。
3. **AMD/ROCm 平台支持深化**：ROCm CI 修复、bf16x3 router 使用堆叠 hipBLASLt GEMM、fused QSA pre-indexer 接入 AMD 路径、CohereCompass 视频模态声明等，表明项目在持续拓宽硬件生态，符合"cheap serving"对多硬件可及性的诉求。
4. **多模态与语音能力扩展**：Nemotron 3.5 ASR、Qwen3ASR EAGLE3 声明、Transformers 视频支持、设备侧 mm normalization 扩展到 Kimi K2.5/K3、编码器缓存引用保留等，持续丰富 LLM serving 的模态覆盖。
5. **HiSparse 模块成型**：日志与 host-tier 利用率指标、启动时拒绝 cudagraph_mode=FULL、CODEOWNERS 建立，显示该稀疏注意力子系统正从开发走向规范化维护。

## 三、对项目的影响与潜在意义

- **稳定性提升**：大量 Bug 修复聚焦于并发、多模态缓存、数据并行 RNG 隔离（#59788）、NIXL 心跳计数等基础层问题，降低了大规模部署时的运行风险，对生产环境用户价值显著。
- **推理吞吐与成本改善**：投机解码性能路径的优化与 QSA 注意力融合直接提高 token 吞吐、降低单位推理成本，与项目"cheap"定位契合。
- **生态扩展**：新增模型（DeepSeek-V4 MegaMoE、GLM-5.3-Flash、Kimi K3、Nemotron）与新模态（视频、ASR）支持增强了 vLLM 作为统一 serving 层的覆盖面。
- **工程质量**：CI 修复、CODEOWNERS、依赖清理（TPU）、LoRA 重构等提升了项目的可维护性和协作效率。

## 四、值得关注的技术点

1. **投机解码状态一致性**（#56531）：将所有投机能力行路由到投机路径以保持 recurrent state 一致，这对混合架构（Mamba/Transformer）模型的正确性至关重要。
2. **数据并行 RNG 独立流**（#59788）：每个 DP 引擎拥有独立的全局随机数流，避免多引擎间的随机性干扰。
3. **动态 K 值投机调度**（#57053）：支持自适应投机草稿长度并带来 1.2~1.3 倍 kernel 性能提升。
4. **安全加固**（#60022）：对不可信媒体路径的 Pillow 解码做格式限制，防范恶意输入攻击。
5. **工具调用语法构建修复**（#59879）：基于提示词实际渲染的工具构建约束语法，修复了此前与实际 prompt 不匹配的问题，对结构化输出可靠性有直接帮助。

## 五、对项目整体发展的意义

综上，这批提交集中于"巩固基础、优化性能、扩展生态"三个层面：在保持 vLLM 作为高效 LLM serving 引擎核心优势的同时，系统性修复底层正确性问题、压榨关键内核性能、并扩展硬件与模态覆盖面。这些工作共同支撑了项目"easy, fast, and cheap"的长期愿景，尤其是通过投机解码与 QSA 优化强化性能护城河，通过多平台与多模型支持降低用户的采用门槛。

## 详细提交记录

### [fa423b6](https://github.com/vllm-project/vllm/commit/fa423b614c5328913ffcb87eaf28817f5acd89f2)

- **作者**: Aarushi Jain
- **时间**: 2026-10-05T23:39:59Z
- **提交信息**: [CI][ROCm] Wait for engine teardown between LM Eval models (#60100)

Signed-off-by: aarushjain29 <aarushi.jain2@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [6dd813e](https://github.com/vllm-project/vllm/commit/6dd813e0b7ca8314fed28c13a73cfb5fc5310163)

- **作者**: Mason
- **时间**: 2026-10-05T23:24:14Z
- **提交信息**: [Bugfix][MoE] Allow MiniMax2 routing in TRTLLM BF16 monolithic backend (#59571)

Signed-off-by: Mason Pitt <bradley.b.pitt@gmail.com>
Co-authored-by: Yongye Zhu <zyy1102000@gmail.com>

### [0eac152](https://github.com/vllm-project/vllm/commit/0eac15270710ddb7f5296d7244fcd0496c2daa0f)

- **作者**: Vadim Gimpelson
- **时间**: 2026-10-05T23:03:44Z
- **提交信息**: [Bugfix] Route every speculation-capable row through the speculative path so recurrent state stays consistent (#56531)

Signed-off-by: Vadim Gimpelson <vadim.gimpelson@gmail.com>
Co-authored-by: Cursor Agent <cursoragent@cursor.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [4a705c7](https://github.com/vllm-project/vllm/commit/4a705c7b54ac775e6436eae6e1ee573f8d4c7775)

- **作者**: Ting SUN
- **时间**: 2026-10-05T22:43:31Z
- **提交信息**: [Bugfix][Frontend] Preserve logprobs when top_logprobs is null (#47838)

Signed-off-by: Ting Sun <suntcrick@gmail.com>
Signed-off-by: Flora Feng <4florafeng@gmail.com>
Co-authored-by: Flora Feng <4florafeng@gmail.com>

### [89a0099](https://github.com/vllm-project/vllm/commit/89a00995c944d934c4c83ef853670cdd838c8bcb)

- **作者**: Kevin H. Luu
- **时间**: 2026-10-05T22:25:11Z
- **提交信息**: [CI] Read each profiler round's trace as it stops in test_gpu_profiler (#59769)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [2e06395](https://github.com/vllm-project/vllm/commit/2e06395fd384f3bd6755faded96d90a19d87e31e)

- **作者**: RomeJay
- **时间**: 2026-10-05T22:01:03Z
- **提交信息**: [Bugfix][Frontend] Build tool-call grammars from the tools the prompt renders (#59879)

Signed-off-by: Rongjie Jiang <j1870831863@outlook.com>
Signed-off-by: sfeng33 <4florafeng@gmail.com>
Co-authored-by: Flora Feng <4florafeng@gmail.com>

### [3fb1cd7](https://github.com/vllm-project/vllm/commit/3fb1cd796bfd318d3261844237a88c371704829d)

- **作者**: Martin Hickey
- **时间**: 2026-10-05T21:57:45Z
- **提交信息**: [Frontend] Extract parse and assembly out of batch chat derender (#60073)

Signed-off-by: Martin Hickey <martin.hickey@ie.ibm.com>
Co-authored-by: Flora Feng <4florafeng@gmail.com>

### [2e3154a](https://github.com/vllm-project/vllm/commit/2e3154aa18b3d2df2253c3e55f8b32fe9af5cfe8)

- **作者**: Robert Shaw
- **时间**: 2026-10-05T21:20:32Z
- **提交信息**: [HiSparse] Log steady-state max concurrency and expose host-tier utilization gauges (#58949)

Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Matthew Bonanni <mbonanni@redhat.com>

### [8542c3e](https://github.com/vllm-project/vllm/commit/8542c3eff5809a79d6d825958f39187c54007851)

- **作者**: Matthew Bonanni
- **时间**: 2026-10-05T21:17:00Z
- **提交信息**: [CI] Fix test_mixed_warmup_gate after #57053 (#60116)

Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [18c8a65](https://github.com/vllm-project/vllm/commit/18c8a65eddebb1ac39021d87f059173656e4a77b)

- **作者**: Yida Weng
- **时间**: 2026-10-05T20:39:25Z
- **提交信息**: [BugFix][Frontend] Pass reasoning_ended through render → generate (#60059) (#60062)

Signed-off-by: Yida Weng <84164537+YidaWeng@users.noreply.github.com>
Signed-off-by: Flora Feng <4florafeng@gmail.com>
Co-authored-by: Flora Feng <4florafeng@gmail.com>

### [74c5cbc](https://github.com/vllm-project/vllm/commit/74c5cbcd7b6fa07fa5568ba7f7dfbfedc502964e)

- **作者**: Wentao Ye
- **时间**: 2026-10-05T18:54:11Z
- **提交信息**: [Bugfix][MRV2][Spec Decode] Honor dynamic K in autoregressive speculators, 1.2~1.3x kernel perf improvement (#57053)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [c32495d](https://github.com/vllm-project/vllm/commit/c32495d58ff580b518cf4c5e5d6b69adc4d38351)

- **作者**: Raphaël Rialland
- **时间**: 2026-10-05T18:37:13Z
- **提交信息**: [watermark] compatibility validation (#56801)

Signed-off-by: Raphael Rialland <raphael.rialland@mistral.ai>
Signed-off-by: Simon Veitner <sveitner@redhat.com>
Co-authored-by: Simon Veitner <sveitner@redhat.com>

### [88f3c60](https://github.com/vllm-project/vllm/commit/88f3c601b336871ab19c742a67915da99b64232c)

- **作者**: Giancarlo Delfin
- **时间**: 2026-10-05T18:35:19Z
- **提交信息**: [Docs] Add reviewer area of interest for TheEpicDolphin (#60092)

Signed-off-by: Giancarlo Delfin <gdelfin@inferact.ai>

### [d09ff77](https://github.com/vllm-project/vllm/commit/d09ff7763747bbe7cd153edd8017479804f47be7)

- **作者**: aoshen02
- **时间**: 2026-10-05T17:38:18Z
- **提交信息**: [Bugfix] Give each data-parallel engine its own global RNG streams (#59788)

Signed-off-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [877ddcc](https://github.com/vllm-project/vllm/commit/877ddcc45639d2363b9081917ef489619e3f29de)

- **作者**: Evgeny Savinov
- **时间**: 2026-10-05T17:35:51Z
- **提交信息**: [Bugfix][Spec Decode] Reserve the bonus KV slot for fill-in DSpark (#59105)

Signed-off-by: Evgeny Savinov <notime.sea@gmail.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Tomas Ruiz <tomas.ruiz.te@gmail.com>

### [1822472](https://github.com/vllm-project/vllm/commit/182247257fb030fe0b41d342ae9e2a4486ae787e)

- **作者**: akii96
- **时间**: 2026-10-05T17:28:07Z
- **提交信息**: [ROCm][Perf] Use a stacked hipBLASLt GEMM for the bf16x3 router  (#52668)

Signed-off-by: Aakif Nawaz <aakif.nawaz@amd.com>

### [54d93af](https://github.com/vllm-project/vllm/commit/54d93af9fb89d0bb8392bdb72db42bb6a17cb4ca)

- **作者**: Matthew Bonanni
- **时间**: 2026-10-05T16:42:27Z
- **提交信息**: [Bugfix][HiSparse] Reject cudagraph_mode=FULL at startup (#59688)

Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [64cb683](https://github.com/vllm-project/vllm/commit/64cb68384241f046d07ba3797e1b14dbc82a0b2d)

- **作者**: Sohaib Ahmed
- **时间**: 2026-10-05T16:28:09Z
- **提交信息**: [Model] Add Nemotron 3.5 ASR transcription support (#59827)

Signed-off-by: Sohaib-Ahmed21 <sohaibahmed1919@gmail.com>

### [87954c5](https://github.com/vllm-project/vllm/commit/87954c5b042391db2fde6bbccd50760e7b7eb8f0)

- **作者**: stefankoncarevic
- **时间**: 2026-10-05T16:25:42Z
- **提交信息**: [CI/Build] Declare the video modality on the CohereCompass reference model (#60063)

Signed-off-by: Stefan Koncarevic <Stefan.Koncarevic@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [d23af12](https://github.com/vllm-project/vllm/commit/d23af12cb1d4071d9ccb4f77012285b62a319f5b)

- **作者**: Mikko Tukiainen
- **时间**: 2026-10-05T16:22:29Z
- **提交信息**: [ROCm][Perf] Reach the fused QSA pre-indexer from the AMD path (#57947)

Signed-off-by: mjkvaak-amd <mjkvaak-amd@users.noreply.github.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [528772a](https://github.com/vllm-project/vllm/commit/528772a4bf589fd52eec40bc8ca79c84d99206b5)

- **作者**: bzsuni
- **时间**: 2026-10-05T15:52:46Z
- **提交信息**: [Bugfix][Core] Retain encoder cache references for repeated multimodal inputs (#59942)

Signed-off-by: bzsuni <bingzhe.sun@daocloud.io>
Signed-off-by: cjackal <44624812+cjackal@users.noreply.github.com>
Co-authored-by: cjackal <44624812+cjackal@users.noreply.github.com>

### [edde9d2](https://github.com/vllm-project/vllm/commit/edde9d2ce4b1cb284679fc4cb2500a57bbc5bbe3)

- **作者**: charlesli640
- **时间**: 2026-10-05T15:45:37Z
- **提交信息**: Remove redundant dependency requirement for TPU (#59977)

Signed-off-by: Charles Li <licharles@google.com>

### [f2d8fbf](https://github.com/vllm-project/vllm/commit/f2d8fbf4590daed7245800840a48298f4c961a9f)

- **作者**: stefankoncarevic
- **时间**: 2026-10-05T15:32:33Z
- **提交信息**: [CI/Build] Run the prefill token scoring test under batch invariance (#60056)

Signed-off-by: Stefan Koncarevic <Stefan.Koncarevic@amd.com>

### [9e931a0](https://github.com/vllm-project/vllm/commit/9e931a0c6c374cd36bd1163c1e31f05480ac0fa7)

- **作者**: Matthew Bonanni
- **时间**: 2026-10-05T15:18:29Z
- **提交信息**: [CI] Add CODEOWNERS for HiSparse (#60060)

Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [60932a6](https://github.com/vllm-project/vllm/commit/60932a6401522039650377d5004a7680459910d1)

- **作者**: Abhay Joshi
- **时间**: 2026-10-05T15:12:40Z
- **提交信息**: [Bugfix][Structured Output] Preserve literal values in Guidance disable_additional_properties (#58709)

Signed-off-by: Abhay Joshi <105213625+abhayjoshi201@users.noreply.github.com>
Co-authored-by: Antigravity <noreply@google.com>
Co-authored-by: Artem Perevedentsev <aperevedents@nvidia.com>

### [30d4032](https://github.com/vllm-project/vllm/commit/30d4032363d4a1f6412d9a235049673b41309f98)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-10-05T14:44:14Z
- **提交信息**: [Model][GLM-5.3-Flash] Support DCP for the kpool sparse indexer (#59211)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [f9c9e8a](https://github.com/vllm-project/vllm/commit/f9c9e8ac248cd19c1e1826693761e69b0eec1822)

- **作者**: Jee Jee Li
- **时间**: 2026-10-05T14:01:56Z
- **提交信息**: [LoRA] Remove tensorizer (#60024)

Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>

### [d3547f9](https://github.com/vllm-project/vllm/commit/d3547f9d03b519abbc2cbed89590244b526ab2cd)

- **作者**: Abhay Shukla
- **时间**: 2026-10-05T13:43:49Z
- **提交信息**: [Test] Re-enable Voxtral HF reference test on Transformers v5 (#59771)

Signed-off-by: AbhayShuklaIIT <abhay.shukla@live.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [0e468ad](https://github.com/vllm-project/vllm/commit/0e468adb43d60484b5a6546e0124b686fd76baf3)

- **作者**: cjackal
- **时间**: 2026-10-05T13:28:13Z
- **提交信息**: [Model] Extend device-side mm normalization to Kimi K2.5 / K3 (#59278)

Signed-off-by: cjackal <44624812+cjackal@users.noreply.github.com>

### [ff53f32](https://github.com/vllm-project/vllm/commit/ff53f324092a7e0777c8f3df32e2c2faf57162d4)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-10-05T13:12:00Z
- **提交信息**: [Attention][MLA] Support fp8_ds_mla KV cache for NoPE-512 models on SM90 (#59246)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>
Co-authored-by: Leoyzen <leoyzen@gmail.com>

### [d0d6e5f](https://github.com/vllm-project/vllm/commit/d0d6e5f3a26f484786e7f20490152e911fd4e220)

- **作者**: Vadim Gimpelson
- **时间**: 2026-10-05T12:49:47Z
- **提交信息**: [Bugfix] Fix Mamba page size AssertionError with spec decoding on GraniteMoeHybrid, FalconH1 and Zamba2 (#59975)

Signed-off-by: Vadim Gimpelson <vadim.gimpelson@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [51eeb0c](https://github.com/vllm-project/vllm/commit/51eeb0c58f77f845e6170a71ee894de9f465c0ca)

- **作者**: roikoren755
- **时间**: 2026-10-05T12:26:55Z
- **提交信息**: [Bugfix] Load stacked expert weights for non-gated MoE (#59031)

Signed-off-by: Roi Koren <roik@nvidia.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [4ff028d](https://github.com/vllm-project/vllm/commit/4ff028d77e063e0055849ffec3855c6634179158)

- **作者**: Stefano Castagnetta
- **时间**: 2026-10-05T12:13:30Z
- **提交信息**: [Bugfix][Qwen4Exp] Honor --kv-cache-dtype-skip-layers in QSA attention (#60023)

Signed-off-by: Stefano Castagnetta <scastagnetta@nvidia.com>
Co-authored-by: Thien Tran <gau.nernst@yahoo.com.sg>

### [55b8022](https://github.com/vllm-project/vllm/commit/55b80221ed571adc1d6bfcc3edf4b48fa23e9884)

- **作者**: Stefano Castagnetta
- **时间**: 2026-10-05T12:09:36Z
- **提交信息**: [Perf][Qwen4Exp] Keep the HC up projection on the skinny GEMM path (#60027)

Signed-off-by: Stefano Castagnetta <scastagnetta@nvidia.com>
Co-authored-by: Thien Tran <gau.nernst@yahoo.com.sg>

### [710ac56](https://github.com/vllm-project/vllm/commit/710ac56e691d4713feca50a43e6c440f07d373fd)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-10-05T10:40:15Z
- **提交信息**: [Security] Restrict Pillow image formats on untrusted media paths (#60022)

Signed-off-by: Juan Pérez de Algaba <jperezde@redhat.com>

### [edca360](https://github.com/vllm-project/vllm/commit/edca360f13aeff2f5a76cc288c87d5af55d080b8)

- **作者**: Mikko Tukiainen
- **时间**: 2026-10-05T10:40:02Z
- **提交信息**: [Bugfix][Qwen4Exp] Load PLE tables unquantized under Quark checkpoints (#59443)

Signed-off-by: Mikko Tukiainen <Mikko.Tukiainen@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: TJian <tunjian.tan@embeddedllm.com>

### [c04c79e](https://github.com/vllm-project/vllm/commit/c04c79e50dbf3d6093af5029a5bd8b9644f22321)

- **作者**: sudhanshu shukla
- **时间**: 2026-10-05T10:27:51Z
- **提交信息**: [Performance] Add SM121 TP=2 skinny-GEMM plans (#59632)

Signed-off-by: sudhanshu shukla <sudhanshu112233shukla@users.noreply.github.com>
Co-authored-by: sudhanshu shukla <sudhanshu112233shukla@users.noreply.github.com>
Co-authored-by: Thien Tran <gau.nernst@yahoo.com.sg>

### [b1401e0](https://github.com/vllm-project/vllm/commit/b1401e0aa7eb7803c38e4d2d306cb2a16c8828a2)

- **作者**: Maroon Ayoub
- **时间**: 2026-10-05T09:36:13Z
- **提交信息**: [Bugfix][NIXL] Count heartbeats as remote engine activity (#59873)

Signed-off-by: Maroon Ayoub <mayoub@redhat.com>

### [ae53b06](https://github.com/vllm-project/vllm/commit/ae53b06898bcd4ae13553eb019f7381dab90edb2)

- **作者**: bcsdhjew
- **时间**: 2026-10-05T09:31:45Z
- **提交信息**: [Bugfix][GLM-5.3-Flash] Keep batch x heads out of gridDim.z in the GLM-5.3-Flash fused recurrent KDA kernel (#56974)

Signed-off-by: NolenLiang <nliang@nvidia.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Codex <noreply@openai.com>

### [b1f229f](https://github.com/vllm-project/vllm/commit/b1f229fb75ddf800494393f21dc6fe2938b5249e)

- **作者**: Ian Eaves
- **时间**: 2026-10-05T09:23:47Z
- **提交信息**: [Model] Declare SupportsEagle3 on Qwen3ASRForConditionalGeneration (#52824)

Signed-off-by: Ian Eaves <ian.k.eaves@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [e3af5bf](https://github.com/vllm-project/vllm/commit/e3af5bf3ced40cc1a5ac1a6c59185abe3111829f)

- **作者**: Jee Jee Li
- **时间**: 2026-10-05T09:15:53Z
- **提交信息**: [LoRA] Code cleanup (#60017)

Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>

### [4a30c4c](https://github.com/vllm-project/vllm/commit/4a30c4cad01401d778adb03b029d9da767c59fed)

- **作者**: aoshen02
- **时间**: 2026-10-05T08:39:49Z
- **提交信息**: [Model][DeepSeek-V4] Make MegaMoE shared-expert finalize independent of linear post-load order (#59927)

Signed-off-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [34051ad](https://github.com/vllm-project/vllm/commit/34051ad7145104e73ba3a7f5b39506ad0949bb8d)

- **作者**: Harshal Janjani
- **时间**: 2026-10-05T07:51:15Z
- **提交信息**: feat: Add video support for the Transformers backend (#57441)

Signed-off-by: Harshal Janjani <harshaljanjani@gmail.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [042ab03](https://github.com/vllm-project/vllm/commit/042ab0305cc4215e2c6fb215f1d6f2e65dd7d4ac)

- **作者**: Thien Tran
- **时间**: 2026-10-05T07:03:29Z
- **提交信息**: [Perf][Qwen4Exp] Merge QSA QKVG and indexer QK projections (#59533)

Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: namgyu-youn <namgyu.dev@gmail.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-10-06
**监控日期**: 2026-10-05
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7054
- **最后更新**: 2026-10-06T01:35:08Z

## 提交统计

- **昨日提交总数**: 12
- **提交者数量**: 12
- **主要提交者**: Linze Shi, Jungle, Sy03

## AI分析总结

## 1. 主要更新类型

- **性能优化占比最高**：PersonaPlex、MiniCPM-o、IndexTTS2 等多个 omni 模型获得深度加速（向量化、CUDA Graph、算子融合、显存驻留优化）。
- **Bug 修复密集**：涵盖 CLI/API 日志配置、扩散执行器错误状态、资源调度校验、设备放置、并发推理预处理等多类问题。
- **基础设施重构**：核心层新增统一的 token_ids 输出类型并规范命名，属于 API/数据层面的收敛性改进。

## 2. 关键变更点与项目方向的关系

- vllm-omni 的目标是"为所有人提供简单、快速、便宜的全模态模型服务"，这批提交高度对齐**"快"与"便宜"**两条主线：性能优化直接降低推理延迟与成本，Bug 修复提升"简单"（易用性与稳定性）。
- 提交集中在 **PersonaPlex、MiniCPM-o、Qwen3-Omni、IndexTTS2** 等语音/多模态模型上，说明项目正把各模态模型从"能跑"推进到"生产级高吞吐"阶段。
- 核心层的 token_ids 输出类型统一（#7843）体现了项目向**标准化推理接口**演进的努力，利于上游生态集成与多后端兼容。

## 3. 对项目的影响与潜在意义

- 性能提交（CUDA Graph、DiT 融合、Euler slot 池、消除每步 D2H 拷贝）显著降低音频生成与扩散模型的开销，推动 vllm-omni 在**实时语音/全模态生成**场景落地，直接支撑 README 中"便宜"的承诺。
- Bug 修复覆盖调度（sleep stage_ids 校验）、错误传播（扩散执行器状态保持）、设备放置等，能提升多卡/混合负载场景下的**稳定性和可观测性**，是进入生产环境的前提。
- 多处联合署名（华为、Red Hat、Codex 等）显示项目**社区协作活跃、外部贡献涌入**，生态建设态势健康。

## 4. 值得关注的技术点

- **CUDA Graph 应用于输入编码器**：将 MiniCPM-o 编译进图中，减少 kernel 启动开销，是 vLLM 深度优化思路向 omni 输入侧的延伸。
- **Resident Euler slot pool + 融合 DiT body**：把常驻显存池与算子融合结合，属于显存与算力双优化的典型做法。
- **Exact HiFT graphs**：用精确图替代近似实现，在不损失质量的前提下提速，值得后续模型推广。
- **token_ids 输出类型强制规范**：为后续多模态输出对齐奠定基础，可能成为 vllm-omni 与其他框架互操作的锚点。

## 5. 对项目发展的整体影响

结合 README 可知 vllm-omni 承诺提供"全模态模型的低成本服务"，这批提交正好补齐了性能与稳定性两块短板：性能上通过向量化、图捕获与显存驻留压低推理成本；稳定性上通过日志、错误状态与调度校验加固服务可靠性；核心层则以规范输出接口巩固架构基础。

这些改动使 vllm-omni 从早期"支持多模型"的阶段，稳步迈向"高可用、低开销的生产级全模态服务平台"。预计后续发布将以这些优化为基础，进一步统一各模态模型的加速路径与接口规范，从而降低企业接入全模态服务的门槛，扩大项目在实际部署场景中的覆盖面。

## 详细提交记录

### [aad3090](https://github.com/vllm-project/vllm-omni/commit/aad30908772a8188c17997341d62768dc0bab3b7)

- **作者**: Linze Shi
- **时间**: 2026-10-05T18:52:41Z
- **提交信息**: [Model][PersonaPlex] Vectorize prefill embedding construction (#7481)

Signed-off-by: Linze-Shi <linzeshi0@gmail.com>

### [ae430dd](https://github.com/vllm-project/vllm-omni/commit/ae430dddc0db6c12054b9935e6df7e0b708a32d4)

- **作者**: LOGO127
- **时间**: 2026-10-05T18:49:33Z
- **提交信息**: [Model][PersonaPlex] Encode only consumed Mimi codebooks (#7399)

Signed-off-by: luozijian <luozijian0924@gmail.com>

### [79562e9](https://github.com/vllm-project/vllm-omni/commit/79562e97ad8e08a3f9d9480ed99cc9abee69b98a)

- **作者**: BeatSeat
- **时间**: 2026-10-05T18:36:28Z
- **提交信息**: [Perf][MiniCPM-o] Code2Wav resident Euler slot pool, fused DiT body, and exact HiFT graphs (#8443)

Signed-off-by: BeatSeat <wendavid552@gmail.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [3aab128](https://github.com/vllm-project/vllm-omni/commit/3aab12851f15f6ec3d8c1b8c3672a6b0b2a99eb7)

- **作者**: Nick Cao
- **时间**: 2026-10-05T17:53:14Z
- **提交信息**: [Bugfix] Configure logging in the Omni CLI/API Server (#8518)

Signed-off-by: Nick Cao <ncao@redhat.com>
Co-authored-by: Codex <noreply@openai.com>

### [539c533](https://github.com/vllm-project/vllm-omni/commit/539c53376217f6a8a9d549bf6c0c5fc1c5ab5e32)

- **作者**: Wenbo Ji　嵇文博
- **时间**: 2026-10-05T17:09:34Z
- **提交信息**: [Bugfix] Keep client error status in the single-GPU diffusion executor (#8474)

Signed-off-by: Wenbo Ji <36562829+fusheng-ji@users.noreply.github.com>

### [9146284](https://github.com/vllm-project/vllm-omni/commit/9146284c16abbe7309f3f79dfdacfb48cdf2499a)

- **作者**: amy-why-3459
- **时间**: 2026-10-05T15:01:07Z
- **提交信息**: [Perf] Add CUDA graphs for MiniCPM-o 4.5 input encoders (#8332)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [a0e626c](https://github.com/vllm-project/vllm-omni/commit/a0e626caafa14a1d165d615aa1ae97aeb59a2d84)

- **作者**: Yufeng He
- **时间**: 2026-10-05T14:27:53Z
- **提交信息**: [Bugfix] Validate sleep stage_ids before blocking admission (#8501)

Signed-off-by: Yufeng He <40085740+he-yufeng@users.noreply.github.com>

### [023716e](https://github.com/vllm-project/vllm-omni/commit/023716ecc45af566a4f8f0d6e0924fdd41d77f3e)

- **作者**: Sy03
- **时间**: 2026-10-05T13:29:38Z
- **提交信息**: [Bugfix] Do not assume a stream decoder in MRv2 eager-MTP preprocess (#8484)

Signed-off-by: Sy03 <1370724210@qq.com>

### [5351cd6](https://github.com/vllm-project/vllm-omni/commit/5351cd6645fbf49b4ef8f74b6f1f259b6e4f2f8a)

- **作者**: Johnny
- **时间**: 2026-10-05T13:00:04Z
- **提交信息**: [Bugfix] Qwen3-Omni thinker: create deepstack buffers on the real device (#8461)

Signed-off-by: John Nunez <johnnynunez@users.noreply.github.com>
Co-authored-by: John Nunez <johnnynunez@users.noreply.github.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [091b256](https://github.com/vllm-project/vllm-omni/commit/091b256674afa1bae476553c35ab1d22d155608a)

- **作者**: ztyan
- **时间**: 2026-10-05T12:20:25Z
- **提交信息**: [Model][Perf] IndexTTS2: drop per-step hidden D2H in latent mode (#8478)

Signed-off-by: ztyan <191593482+vivivi-111@users.noreply.github.com>

### [6dd0d1f](https://github.com/vllm-project/vllm-omni/commit/6dd0d1f9310f7598b773c796b434c8000c2816ec)

- **作者**: Yueqian Lin
- **时间**: 2026-10-05T09:40:07Z
- **提交信息**: [Bugfix] Update routed-expert tests for native auxiliary output (#8500)

Signed-off-by: Yueqian Lin <linyueqian@outlook.com>

### [67d21b5](https://github.com/vllm-project/vllm-omni/commit/67d21b5fff4e4c136ebcbd23a0cacd81f4e6faa8)

- **作者**: Jungle
- **时间**: 2026-10-05T08:49:03Z
- **提交信息**: [Core] Add token_ids output type and enforce canonical names (#7843)

Signed-off-by: Jungle430 <junglece430@gmail.com>
Co-authored-by: Codex <noreply@openai.com>

---
