# GitHub Stars 合并报告 - 2026-09-15

**合并日期**: 2026-09-16
**监控日期**: 2026-09-15
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


**报告日期**: 2026-09-16
**监控日期**: 2026-09-15
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2211
- **最后更新**: 2026-09-15T11:32:15Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Coach257

## AI分析总结

# VeOmni 昨日提交分析（d20513f）

## 1. 主要更新类型
这是一次 **破坏性变更（BREAKING）**，融合了**功能新增、重构与文档更新**三类性质：
- 功能层面：按“状态所有者（state owner）”拆分 checkpoint 的 step 目录结构；
- 重构层面：调整了检查点存储的组织方式；
- 文档层面：同步更新了相关说明，并涉及 LoRA 相关逻辑。

## 2. 关键变更点与项目方向的关系
核心变更是把原先统一的 checkpoint step 目录，按不同 state owner（如模型参数、优化器状态、LoRA 适配器等）分别存放。这与 VeOmni 的定位高度一致——它主打“模型中心的分布式配方动物园（Model-Centric Distributed Recipe Zoo）”，需要支持任意模态、多种并行策略与训练配方。不同组件（全参、LoRA、优化器）的状态生命周期和加载需求不同，分目录管理正是为多配方、多模态训练提供更清晰的存储边界。

## 3. 对项目的影响与潜在意义
- **兼容性影响**：标记为 BREAKING，意味着旧的 checkpoint 目录结构不再直接兼容，用户升级后需迁移或重新保存检查点。
- **可维护性提升**：状态分离后，加载/保存逻辑更模块化，便于按需只读取某类状态（例如仅加载 LoRA 权重）。
- **扩展性增强**：为未来引入更多状态类型（新并行维度、新模态组件）预留了结构空间。
- **协作与调试**：目录语义更明确，便于分布式训练中定位问题与团队协作。

## 4. 值得关注的技术点
- “state owner”这一抽象如何界定边界（模型/优化器/LoRA/调度器等）；
- LoRA 与全参 checkpoint 的隔离方式，是否支持混合加载与热切换；
- 破坏性变更是否提供迁移脚本或兼容读取旧格式的过渡路径；
- 与分布式并行（FSDP/TP/PP 等）下分片状态的对应关系；
- 由 Cursor 协作生成，反映 AI 辅助开发在基础设施重构中的参与。

## 5. 结合项目背景看发展影响
VeOmni 目标是“以模型为中心”统一任意模态的大规模训练。checkpoint 是训练配方可复现、可续训、可迁移的关键载体。此次按状态所有者拆分目录，实质是把“配方”的存储粒度细化，使不同训练策略（全参微调 vs LoRA、不同并行配置）能更独立地管理自身状态。这为项目后续支持更丰富的分布式配方、降低跨配方迁移成本打下基础，也表明项目正从“能跑通”走向“工程化、可维护”的成熟阶段。短期会带来升级阵痛，长期利好生态扩展与用户体验。

## 详细提交记录

### [d20513f](https://github.com/ByteDance-Seed/VeOmni/commit/d20513fb758dc30c315b128787c019df57dd6210)

- **作者**: Coach257
- **时间**: 2026-09-15T11:32:08Z
- **提交信息**: [BREAKING][ckpt, lora, docs] feat: split the checkpoint step directory by state owner (#1181)

Co-authored-by: Cursor <cursoragent@cursor.com>

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-09-16
**监控日期**: 2026-09-15
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2818
- **最后更新**: 2026-09-15T11:31:26Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: STwangyingrui, Bilang ZHANG

## AI分析总结

# LightX2V 昨日提交分析（共 2 条）

## 1. 主要更新类型

- **重构（refactor）**：对齐 Shot 请求逻辑并简化推理默认值（#1517）。
- **Bug 修复（fix）**：修复 MiniMax-H3 在 VAE 分块数少于并行 rank 数时的崩溃问题（#1516）。

整体属于“稳定性修复 + 接口/默认值收敛”的组合，没有引入全新大功能。

## 2. 关键变更点与项目方向的关系

- **Shot 请求对齐 + 推理默认值简化**：说明项目正在统一请求参数的处理路径，减少调用方需要显式指定的配置。这与 LightX2V 作为“轻量视频生成推理框架”的定位一致——降低使用门槛、让默认配置即可跑通，是推理框架走向成熟和易用的必经步骤。
- **H3 VAE 并行编码/解码支持空闲 rank**：此前当输入产生的 tile 数少于并行 rank 数时会崩溃，现在允许部分 rank 空闲。这直接关系到框架的**并行推理能力**，是视频生成中 VAE 阶段多卡扩展的关键健壮性改进。

## 3. 对项目的影响与潜在意义

- 修复 #1516 消除了一个**边界条件下的崩溃**，使 H3 模型在多卡/多 rank 环境下对小分辨率或短输入也能稳定运行，扩大了可用场景。
- #1517 的默认值简化降低了用户配置负担，有助于减少因参数不一致导致的隐性错误，提升开箱即用体验。
- 两者共同指向项目从“能跑”向“稳定、易用、可扩展”演进，符合推理框架面向生产部署的发展诉求。

## 4. 值得关注的技术点

- **并行 VAE 的负载不均处理**：允许空闲 rank 意味着需要正确处理 tile 到 rank 的映射与同步，避免集合通信死锁，这是分布式推理中较易出错的环节。
- **默认值收敛策略**：简化默认值可能改变既有行为，需关注是否影响向后兼容及已有用户的推理结果一致性。
- **Shot 请求语义对齐**：涉及请求结构的规范化，可能为后续统一多模型接口打基础。

## 5. 结合项目背景的发展影响

LightX2V 主打“轻量视频生成推理”，核心价值在于高效、易用地部署视频生成模型。本次两条提交分别从**并行推理健壮性**（H3 多卡 VAE）和**接口易用性**（默认值简化）两个方向加固框架基础能力。这类看似细小的修复与重构，正是推理框架支撑多模型、多硬件规模化落地所必需的积累，有助于提升项目在真实部署场景中的可靠性与用户口碑，为后续扩展更多模型和并行策略奠定稳定基础。

## 详细提交记录

### [aeed044](https://github.com/ModelTC/LightX2V/commit/aeed0443b4da666a314f3efe3d8044b0f5ff8a73)

- **作者**: Bilang ZHANG
- **时间**: 2026-09-15T11:31:20Z
- **提交信息**: refactor: align Shot requests and simplify inference defaults (#1517)

### [67019e3](https://github.com/ModelTC/LightX2V/commit/67019e3c7ffc837728e9e22ce3368cc980c0ca94)

- **作者**: STwangyingrui
- **时间**: 2026-09-15T11:00:31Z
- **提交信息**: fix(minimax-h3): support fewer VAE tiles than ranks (#1516)

Allow idle ranks in parallel H3 VAE encoding and decoding, avoiding
crashes when an input produces fewer tiles than ranks.

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-09-16
**监控日期**: 2026-09-15
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2248
- **最后更新**: 2026-09-15T07:34:20Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-09-16
**监控日期**: 2026-09-15
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6416
- **最后更新**: 2026-09-16T00:01:07Z

## 提交统计

- **昨日提交总数**: 13
- **提交者数量**: 10
- **主要提交者**: Anerudhan Gopal, Jonathan Dierksen, Haoran FENG

## AI分析总结

# FlashInfer 昨日提交总结

## 一、主要更新类型

昨日工作以**性能优化**与**功能新增**为主线，辅以**Bug 修复**、**重构**和**CI/工程化改进**，整体呈现“扩展硬件覆盖 + 提升推理性能 + 修复设备/架构适配”的特征，与 FlashInfer 高性能 GPU 推理内核库的定位高度一致。

## 二、关键变更点

- **性能优化**：`cake_gdn` 刷新 85 个 Blackwell GDN prefill 变体，去除 FP32 shuffle 开销并应用合格调度；`backend="auto"` 在 Blackwell ragged prefill 上可触达 cuDNN/CUTLASS，最高提速 3.3 倍。
- **功能扩展**：cuTile MoE 新增 MXFP4/W4A16 支持，覆盖 SM89/90/120/121；primsTS 支持 QK-BF16/PV-FP8 混合精度 FMHA context，平均提速 10–26%；新增 Frost DS4.1 稀疏 MLA 解码，引入 MXFP8 滑窗 + FP4 压缩的混合量化缓存，支持 CUDA Graph 复用与 per-head attention sink。
- **重构**：将 SM90 CuTe-DSL BF16 MoE 的 tactic、合法性与调优层对齐 SM100 约定，用单一 tactic 元组取代多轴关键字，并把合法性判断下沉到内核（`can_implement`）。
- **Bug 修复**：修复 GDN CuTe-DSL decode 内核按设备 0 而非操作数设备编译/调优的问题；修复 JIT 架构检测陈旧状态并允许 SM120 在 CUDA 12.8 运行；topk 在 SM120 上回退 CUB 以保证图安全；恢复 Blackwell 默认 GDN prefill 走 CuTe 实现；修复 Nightly 隔离布局下 BF16 rank-major MoE EP 测试。
- **工程化**：CI 缓存校验和验证的 cubin 下载，减少约 4.2 万次文件传输；新增 GDN/Mamba/KDA 的 CODEOWNER。

## 三、项目影响与意义

低精度 MoE 与混合精度注意力显著提升吞吐，直接服务大模型推理降本增效。GDN 修复带来约 35% 的默认延迟下降（0.117 ms → 0.076 ms），并新增 CUDA Graph 回归测试锁定行为。MoE 重构降低 SM90/SM100 双后端维护成本，减少“Python 与内核规则漂移”类 bug。设备目标修复与 JIT 架构检测改进提升了异构多 GPU 环境的可靠性。CI 优化降低夜间构建失败率，增强发布稳定性。显式 cuDNN 路径归一化为 token-unit indptr 属破坏性变更，但统一了后端契约。

## 四、值得关注的技术点

- 合法性下沉内核：`is_valid_tile_and_cluster_shape` / `can_implement` 成为单一事实来源，调优器与 wrapper 共用。
- GEMM2 去掉 `tile_k`：K tile 固定为 4 个 WGMMA K-step，末块由 TMA 零填充，放宽 per-rank 中间尺寸约束。
- E8M0 尺度修正：将 scale code `0` 解释为 `2^-127` 而非零，避免合法 MXFP8 缓存被静默清零。
- sink 归一化数值稳定：用稳定 log-sigmoid 表达式处理超大有限 FP32 logits，防止溢出产生 NaN。
- GDN 中“编译目标按设备解析、磁盘缓存仅按架构命名”的双重身份策略，兼顾正确性与缓存复用。

## 五、结合项目背景的发展方向

FlashInfer 定位为“High-Performance GPU Kernels for Inference”，强调跨架构（Hopper/Blackwell）与多量化格式支持。昨日提交正沿此主线推进：通过 FP4/FP8 量化、Blackwell 新架构适配和 cuDNN/CUTLASS 后端接入，持续拓宽高性能推理的硬件与精度边界；以设备目标修复和 CI 加固保障工程可靠性；MoE 重构强化跨代内核一致性抽象，GDN 修复维护“开箱即高性能”承诺，Frost 解码把能力延伸至稀疏 MLA 与混合精度缓存前沿。整体看，项目正从“提供多个可用内核”向“统一策略层 + 可验证默认路径 + 新硬件特性快速落地”演进，工程成熟度与前沿覆盖同步提升。

## 详细提交记录

### [698f055](https://github.com/flashinfer-ai/flashinfer/commit/698f0551a56897cd6ee4a0176116e63d16f7310d)

- **作者**: eigen
- **时间**: 2026-09-15T23:19:57Z
- **提交信息**: perf(cake_gdn): optimize prefill kernels for SM100 and SM103 (#5243)

## Summary

Refresh all 85 generated Blackwell GDN prefill variants to remove
indexed FP32
shuffle collective-helper overhead and apply the qualified prefill
schedules.
Explicit `backend="cake_gdn"` uses the new sources. Automatic prefill
dispatch
continues to use CuTe, as restored by #5225; the 19 decode variants are
preserved.

This updates generated CUDA, the generated prefill helper header,
manifest
checksums, and the loader's manifest pin. Host bindings, ABI, semantic
wrappers,
routes and compile options are unchanged.

The cuDNN-versus-default comparison tests now require CUDA 13+, matching
the
default Blackwell CuTe backend. CUDA 12.9 continues to run the
independent
cuDNN reference and cache tests; only the unsupported default comparison
skips.

## Validation

- B200 original B4/S2048, Q/K/V heads 16/16/32, D128, BF16 inputs and
FP32 state:
  **0.0748635 / 0.0748000 ms**, both below **0.0768 ms**, with refcheck,
CUDA Graph and CUPTI. These CLI logs do not contain paired CuTe medians.
- A separate five-shape matrix passes output/state checks before and
after
timing. Its B4/S2048 exported medians are **0.074719 / 0.074912 ms**,
versus
  CuTe **0.076128 / 0.075936 ms**.
- Each architecture: **137/137 performance rows pass**, comprising 47
fresh
measurements and 90 historical rows authenticated through unchanged
artifacts.
  Minimum CuTe/exported is **1.000987× on B200 / 1.008746× on B300**;
  minimum previous-backend/exported is **1.267218× / 1.290698×**.
- Each architecture: 1713 original correctness inputs plus one
separately
  validated caller-normalized fixture, including 27 expected rejections.
Coverage comprises 83 fresh rows and 1631 retained rows. Public API
integration
  checks and the registered source correctness/benchmark slices pass.
- Synccheck and racecheck: **SKIP on both architectures**, each after
its enforced
20-second timeout. No errors were reported before timeout; these are not
passes.

The full portfolio uses pinned CuTe
`8044d94bf9acc5369857baf88d28906bb32bf264`,
three counterbalanced groups, 100 ms warmup and 1000 ms measurement per
API arm,
CUDA Graph, CUPTI, cold L2 and clocks of at least 1900 MHz. The separate
five-shape
matrix uses CuTe `85da10187476d1a33e560fddbdbf7447d4937d31`.

[Detailed
results](https://github.com/yyihuang/flashinfer/blob/d20e1e865a44219b1ed59abb56d121d8d6012a51/csrc/gdn/cake/RESULTS.md)
and the
[validation
header](https://github.com/yyihuang/flashinfer/blob/d20e1e865a44219b1ed59abb56d121d8d6012a51/csrc/gdn/cake/validation-header.json)
record the qualified
manifest, protocol and evidence boundaries. Physical turnaround through
qualification was **4.86 hours**; kernel medians exclude preparation and
queueing.

The measured integration was based on
`85da10187476d1a33e560fddbdbf7447d4937d31`.
This publication is based on current main
`24c30bddbe1628e225458380b476de756b506f69`;
the GDN wrappers, loader implementation and GDN tests match the measured
checkout.
General JIT environment changes are outside that measured checkout.
Existing
artifact qualification is reused; full-checkout CI for this PR is
separate.


## Per-shape speedup against CuTe (complete 137-row portfolio)

CuTe baseline: `8044d94bf9acc5369857baf88d28906bb32bf264`. Cake is the
qualified exported backend. Each speedup is **CuTe median / Cake
median**; larger than 1 means Cake is faster. Medians pool the retained
reportable GPU samples across all three counterbalanced groups; the
speedup is not the minimum directional ratio. Timings use CUDA Graph
replay, CUPTI and cold L2, with 100 ms warmup and 1,000 ms measurement
per arm and SM clocks at least 1,900 MHz.

Each architecture contains 137 passing rows: **47 fresh measurements and
90 historical measurements reused through unchanged generated CUDA, host
code, ABI, headers, compile options, routes and API bytes**. These are
the recorded qualified export measurements, not new measurements of a
later source integration. `F` marks fresh and `R` marks
unchanged-artifact reuse. Row IDs preserve the sealed case identity;
cases with similar tensor dimensions remain separate.

All latencies below are milliseconds. `B` is batch size, and sequence
lengths use `length×count` for uniform batches or `+` for a
heterogeneous batch. `Hq/Hk/Hv` gives query/key/value heads, `D` is head
dimension, `I/S` gives input/state precision, and `Init` records whether
an initial state is supplied. `A/B/F/P` records alpha gate / beta gate /
final-state output / preallocated output (`1` enabled, `0` disabled).
All rows use automatic scaling and no intermediate checkpoints.

| Row | B | Sequence lengths | Hq/Hk/Hv | D | I/S | Init | A/B/F/P |
Evidence | B200 Cake ms | B200 CuTe ms | B200 speedup | B300 Cake ms |
B300 CuTe ms | B300 speedup |
|---|---:|---|---|---:|---|---|---|---|---:|---:|---:|---:|---:|---:|
| prefill_focus-0001 | 1 | 16384×1 | 2/2/8 | 128 | FP16/FP32 | yes |
1/1/1/1 | R | 0.4392000 | 0.4753600 | 1.082332× | 0.4170270 | 0.4611550
| 1.105816× |
| prefill_focus-0002 | 1 | 2048×1 | 8/8/32 | 128 | FP16/FP32 | yes |
1/1/1/1 | R | 0.0657930 | 0.0783680 | 1.191130× | 0.0615370 | 0.0756810
| 1.229845× |
| prefill_focus-0003 | 1 | 65536×1 | 16/16/16 | 128 | FP16/FP32 | yes |
1/1/1/1 | R | 1.6847330 | 1.8558360 | 1.101561× | 1.6238830 | 1.7944755
| 1.105052× |
| prefill_focus-0004 | 1 | 32768×1 | 16/16/16 | 128 | FP16/FP32 | yes |
1/1/1/1 | R | 0.8471010 | 0.9372450 | 1.106415× | 0.8143750 | 0.9067280
| 1.113404× |
| prefill_focus-0005 | 1 | 8192×1 | 16/16/16 | 128 | FP16/FP32 | yes |
1/1/1/1 | R | 0.2197440 | 0.2496960 | 1.136304× | 0.2126410 | 0.2412820
| 1.134692× |
| prefill_focus-0006 | 1 | 4096×1 | 16/16/16 | 128 | FP16/FP32 | yes |
1/1/1/1 | R | 0.1157760 | 0.1350400 | 1.166390× | 0.1110730 | 0.1306890
| 1.176605× |
| prefill_focus-0007 | 2 | 6144+2048 | 16/16/16 | 128 | FP16/FP32 | yes
| 1/1/1/1 | R | 0.1690240 | 0.1924800 | 1.138773× | 0.1624650 |
0.1867210 | 1.149300× |
| prefill_focus-0008 | 2 | 4096×2 | 16/16/16 | 128 | FP16/FP32 | yes |
1/1/1/1 | R | 0.1186560 | 0.1359350 | 1.145623× | 0.1120330 | 0.1305930
| 1.165665× |
| prefill_focus-0009 | 2 | 2048+6144 | 16/16/16 | 128 | FP16/FP32 | yes
| 1/1/1/1 | R | 0.1697600 | 0.1924160 | 1.133459× | 0.1624970 |
0.1862730 | 1.146317× |
| prefill_focus-0010 | 2 | 1024+7168 | 16/16/16 | 128 | FP16/FP32 | yes
| 1/1/1/1 | R | 0.1955850 | 0.2208640 | 1.129248× | 0.1866570 |
0.2142410 | 1.147779× |
| prefill_focus-0011 | 4 | 2048×4 | 16/16/16 | 128 | FP16/FP32 | yes |
1/1/1/1 | R | 0.0690560 | 0.0807680 | 1.169601× | 0.0676810 | 0.0764810
| 1.130022× |
| prefill_focus-0012 | 8 | 8192×8 | 16/16/16 | 128 | FP16/FP32 | yes |
1/1/1/1 | F | 0.2585590 | 0.2669440 | 1.032430× | 0.2439390 | 0.2505630
| 1.027154× |
| prefill_focus-0013 | 16 | 8192×16 | 16/16/16 | 128 | FP16/FP32 | yes |
1/1/1/1 | F | 0.5171515 | 0.5357120 | 1.035890× | 0.4775720 | 0.4990750
| 1.045026× |
| prefill_focus-0014 | 32 | 8192×32 | 16/16/16 | 128 | FP16/FP32 | yes |
1/1/1/1 | F | 1.0530890 | 1.0971205 | 1.041812× | 0.9696060 | 1.0089345
| 1.040561× |
| prefill_focus-0015 | 8 | 1024×8 | 32/32/32 | 128 | FP16/FP32 | yes |
1/1/1/1 | F | 0.0920310 | 0.1042240 | 1.132488× | 0.0886730 | 0.1009610
| 1.138577× |
| prefill_focus-0016 | 4 | 64×4 | 4/4/8 | 128 | BF16/FP32 | no | 0/0/0/0
| R | 0.0116160 | 0.0153910 | 1.324983× | 0.0103680 | 0.0141760 |
1.367284× |
| prefill_regression-0001 | 1 | 65536×1 | 2/2/8 | 128 | FP16/FP32 | yes
| 1/1/1/1 | R | 1.7323490 | 1.8432610 | 1.064024× | 1.6558065 |
1.7864430 | 1.078896× |
| prefill_regression-0002 | 1 | 32768×1 | 2/2/8 | 128 | FP16/FP32 | yes
| 1/1/1/1 | R | 0.8701730 | 0.9311970 | 1.070129× | 0.8311440 |
0.9032410 | 1.086744× |
| prefill_regression-0003 | 1 | 16384×1 | 2/2/8 | 128 | FP16/FP32 | yes
| 1/1/1/1 | R | 0.4393920 | 0.4755840 | 1.082368× | 0.4179550 |
0.4610910 | 1.103207× |
| prefill_regression-0004 | 1 | 8192×1 | 2/2/8 | 128 | FP16/FP32 | yes |
1/1/1/1 | R | 0.2245120 | 0.2469750 | 1.100053× | 0.2142740 | 0.2400020
| 1.120071× |
| prefill_regression-0005 | 1 | 4096×1 | 2/2/8 | 128 | FP16/FP32 | yes |
1/1/1/1 | R | 0.1168320 | 0.1330240 | 1.138592× | 0.1119360 | 0.1297290
| 1.158957× |
| prefill_regression-0006 | 1 | 2048×1 | 2/2/8 | 128 | FP16/FP32 | yes |
1/1/1/1 | R | 0.0630400 | 0.0762560 | 1.209645× | 0.0600320 | 0.0738890
| 1.230827× |
| prefill_regression-0007 | 2 | 6144+2048 | 2/2/8 | 128 | FP16/FP32 |
yes | 1/1/1/1 | R | 0.1711350 | 0.1896640 | 1.108271× | 0.1610250 |
0.1842900 | 1.144481× |
| prefill_regression-0008 | 2 | 4096×2 | 2/2/8 | 128 | FP16/FP32 | yes |
1/1/1/1 | R | 0.1181440 | 0.1334720 | 1.129740× | 0.1110090 | 0.1289290
| 1.161428× |
| prefill_regression-0009 | 2 | 2048+6144 | 2/2/8 | 128 | FP16/FP32 |
yes | 1/1/1/1 | R | 0.1712320 | 0.1902720 | 1.111194× | 0.1613130 |
0.1845460 | 1.144024× |
| prefill_regression-0010 | 2 | 1024+7168 | 2/2/8 | 128 | FP16/FP32 |
yes | 1/1/1/1 | R | 0.1978230 | 0.2188160 | 1.106120× | 0.1872970 |
0.2126100 | 1.135149× |
| prefill_regression-0011 | 4 | 2048×4 | 2/2/8 | 128 | FP16/FP32 | yes |
1/1/1/1 | R | 0.0658560 | 0.0765760 | 1.162779× | 0.0606730 | 0.0738560
| 1.217280× |
| prefill_regression-0012 | 8 | 1024×8 | 2/2/8 | 128 | FP16/FP32 | yes |
1/1/1/1 | R | 0.0402240 | 0.0496310 | 1.233865× | 0.0391690 | 0.0475520
| 1.214021× |
| prefill_regression-0013 | 8 | 8192×8 | 2/2/8 | 128 | FP16/FP32 | yes |
1/1/1/1 | R | 0.2406070 | 0.2507840 | 1.042297× | 0.2309140 | 0.2417310
| 1.046844× |
| prefill_regression-0014 | 16 | 8192×16 | 2/2/8 | 128 | FP16/FP32 | yes
| 1/1/1/1 | F | 0.2593920 | 0.2641590 | 1.018378× | 0.2380180 |
0.2438740 | 1.024603× |
| prefill_regression-0015 | 32 | 8192×32 | 2/2/8 | 128 | FP16/FP32 | yes
| 1/1/1/1 | F | 0.4980480 | 0.5053430 | 1.014647× | 0.4671410 |
0.4835890 | 1.035210× |
| prefill_regression-0016 | 1 | 65536×1 | 4/4/16 | 128 | FP16/FP32 | yes
| 1/1/1/1 | R | 1.7069115 | 1.8463360 | 1.081682× | 1.6394035 |
1.7892940 | 1.091430× |
| prefill_regression-0017 | 1 | 32768×1 | 4/4/16 | 128 | FP16/FP32 | yes
| 1/1/1/1 | R | 0.8636470 | 0.9338220 | 1.081254× | 0.8169350 |
0.9070800 | 1.110345× |
| prefill_regression-0018 | 1 | 16384×1 | 4/4/16 | 128 | FP16/FP32 | yes
| 1/1/1/1 | R | 0.4356160 | 0.4771840 | 1.095423× | 0.4177300 |
0.4636190 | 1.109853× |
| prefill_regression-0019 | 1 | 8192×1 | 4/4/16 | 128 | FP16/FP32 | yes
| 1/1/1/1 | R | 0.2241920 | 0.2484480 | 1.108193× | 0.2124820 |
0.2411700 | 1.135014× |
| prefill_regression-0020 | 1 | 4096×1 | 4/4/16 | 128 | FP16/FP32 | yes
| 1/1/1/1 | R | 0.1176320 | 0.1338880 | 1.138194× | 0.1109130 |
0.1297930 | 1.170224× |
| prefill_regression-0021 | 1 | 2048×1 | 4/4/16 | 128 | FP16/FP32 | yes
| 1/1/1/1 | R | 0.0630400 | 0.0764800 | 1.213198× | 0.0602890 |
0.0743370 | 1.233011× |
| prefill_regression-0022 | 2 | 6144+2048 | 4/4/16 | 128 | FP16/FP32 |
yes | 1/1/1/1 | R | 0.1737600 | 0.1919040 | 1.104420× | 0.1623370 |
0.1859540 | 1.145481× |
| prefill_regression-0023 | 2 | 4096×2 | 4/4/16 | 128 | FP16/FP32 | yes
| 1/1/1/1 | R | 0.1203200 | 0.1350390 | 1.122332× | 0.1121600 |
0.1305610 | 1.164060× |
| prefill_regression-0024 | 2 | 2048+6144 | 4/4/16 | 128 | FP16/FP32 |
yes | 1/1/1/1 | R | 0.1719360 | 0.1915510 | 1.114083× | 0.1615380 |
0.1858260 | 1.150355× |
| prefill_regression-0025 | 2 | 1024+7168 | 4/4/16 | 128 | FP16/FP32 |
yes | 1/1/1/1 | R | 0.1973760 | 0.2200640 | 1.114948× | 0.1871700 |
0.2133780 | 1.140022× |
| prefill_regression-0026 | 4 | 2048×4 | 4/4/16 | 128 | FP16/FP32 | yes
| 1/1/1/1 | R | 0.0682880 | 0.0787510 | 1.153219× | 0.0668490 |
0.0761280 | 1.138805× |
| prefill_regression-0027 | 8 | 1024×8 | 4/4/16 | 128 | FP16/FP32 | yes
| 1/1/1/1 | F | 0.0465280 | 0.0531520 | 1.142366× | 0.0440970 |
0.0503680 | 1.142209× |
| prefill_regression-0028 | 8 | 8192×8 | 4/4/16 | 128 | FP16/FP32 | yes
| 1/1/1/1 | F | 0.2610890 | 0.2649920 | 1.014949× | 0.2391070 |
0.2454110 | 1.026365× |
| prefill_regression-0029 | 16 | 8192×16 | 4/4/16 | 128 | FP16/FP32 |
yes | 1/1/1/1 | F | 0.5012165 | 0.5067200 | 1.010980× | 0.4687090 |
0.4862130 | 1.037345× |
| prefill_regression-0030 | 32 | 8192×32 | 4/4/16 | 128 | FP16/FP32 |
yes | 1/1/1/1 | F | 1.0005600 | 1.0214405 | 1.020869× | 0.9384090 |
0.9643610 | 1.027655× |
| prefill_regression-0031 | 1 | 65536×1 | 8/8/32 | 128 | FP16/FP32 | yes
| 1/1/1/1 | R | 1.7142225 | 1.8623660 | 1.086420× | 1.6446870 |
1.7995360 | 1.094151× |
| prefill_regression-0032 | 1 | 32768×1 | 8/8/32 | 128 | FP16/FP32 | yes
| 1/1/1/1 | R | 0.8638730 | 0.9381770 | 1.086013× | 0.8286780 |
0.9108860 | 1.099204× |
| prefill_regression-0033 | 1 | 16384×1 | 8/8/32 | 128 | FP16/FP32 | yes
| 1/1/1/1 | R | 0.4433910 | 0.4806870 | 1.084115× | 0.4190120 |
0.4654760 | 1.110889× |
| prefill_regression-0034 | 1 | 8192×1 | 8/8/32 | 128 | FP16/FP32 | yes
| 1/1/1/1 | R | 0.2281930 | 0.2508480 | 1.099280× | 0.2148180 |
0.2426580 | 1.129598× |
| prefill_regression-0035 | 1 | 4096×1 | 8/8/32 | 128 | FP16/FP32 | yes
| 1/1/1/1 | R | 0.1207680 | 0.1362560 | 1.128246× | 0.1129290 |
0.1318410 | 1.167468× |
| prefill_regression-0036 | 1 | 2048×1 | 8/8/32 | 128 | FP16/FP32 | yes
| 1/1/1/1 | R | 0.0649920 | 0.0776950 | 1.195455× | 0.0618890 |
0.0752000 | 1.215079× |
| prefill_regression-0037 | 2 | 6144+2048 | 8/8/32 | 128 | FP16/FP32 |
yes | 1/1/1/1 | R | 0.1805760 | 0.1953600 | 1.081871× | 0.1769940 |
0.1879060 | 1.061652× |
| prefill_regression-0038 | 2 | 4096×2 | 8/8/32 | 128 | FP16/FP32 | yes
| 1/1/1/1 | R | 0.1258880 | 0.1370570 | 1.088722× | 0.1222420 |
0.1324500 | 1.083506× |
| prefill_regression-0039 | 2 | 2048+6144 | 8/8/32 | 128 | FP16/FP32 |
yes | 1/1/1/1 | R | 0.1813110 | 0.1952320 | 1.076780× | 0.1773780 |
0.1885780 | 1.063142× |
| prefill_regression-0040 | 2 | 1024+7168 | 8/8/32 | 128 | FP16/FP32 |
yes | 1/1/1/1 | R | 0.2088320 | 0.2236160 | 1.070794× | 0.2049940 |
0.2165470 | 1.056358× |
| prefill_regression-0041 | 4 | 2048×4 | 8/8/32 | 128 | FP16/FP32 | yes
| 1/1/1/1 | F | 0.0787200 | 0.0845120 | 1.073577× | 0.0746890 |
0.0798410 | 1.068979× |
| prefill_regression-0042 | 8 | 1024×8 | 8/8/32 | 128 | FP16/FP32 | yes
| 1/1/1/1 | F | 0.0875840 | 0.1000960 | 1.142857× | 0.0834250 |
0.0948170 | 1.136554× |
| prefill_regression-0043 | 8 | 8192×8 | 8/8/32 | 128 | FP16/FP32 | yes
| 1/1/1/1 | F | 0.5116160 | 0.5186240 | 1.013698× | 0.4736360 |
0.4862760 | 1.026687× |
| prefill_regression-0044 | 16 | 8192×16 | 8/8/32 | 128 | FP16/FP32 |
yes | 1/1/1/1 | F | 0.9941445 | 1.0165440 | 1.022531× | 0.9428910 |
0.9695465 | 1.028270× |
| prefill_regression-0045 | 32 | 8192×32 | 8/8/32 | 128 | FP16/FP32 |
yes | 1/1/1/1 | F | 1.8601455 | 1.9250740 | 1.034905× | 1.7016790 |
1.7658395 | 1.037704× |
| prefill_regression-0046 | 1 | 65536×1 | 16/16/64 | 128 | FP16/FP32 |
yes | 1/1/1/1 | R | 1.7983375 | 1.8610260 | 1.034859× | 1.7821340 |
1.8023260 | 1.011330× |
| prefill_regression-0047 | 1 | 32768×1 | 16/16/64 | 128 | FP16/FP32 |
yes | 1/1/1/1 | R | 0.9118225 | 0.9465270 | 1.038061× | 0.8985070 |
0.9118510 | 1.014851× |
| prefill_regression-0048 | 1 | 16384×1 | 16/16/64 | 128 | FP16/FP32 |
yes | 1/1/1/1 | R | 0.4662070 | 0.4826560 | 1.035283× | 0.4545020 |
0.4667260 | 1.026895× |
| prefill_regression-0049 | 1 | 8192×1 | 16/16/64 | 128 | FP16/FP32 |
yes | 1/1/1/1 | R | 0.2390720 | 0.2522240 | 1.055013× | 0.2331550 |
0.2438750 | 1.045978× |
| prefill_regression-0050 | 1 | 4096×1 | 16/16/64 | 128 | FP16/FP32 |
yes | 1/1/1/1 | R | 0.1264000 | 0.1387840 | 1.097975× | 0.1224330 |
0.1326730 | 1.083638× |
| prefill_regression-0051 | 1 | 2048×1 | 16/16/64 | 128 | FP16/FP32 |
yes | 1/1/1/1 | R | 0.0689600 | 0.0799360 | 1.159165× | 0.0668170 |
0.0764810 | 1.144634× |
| prefill_regression-0052 | 2 | 6144+2048 | 16/16/64 | 128 | FP16/FP32 |
yes | 1/1/1/1 | F | 0.2004480 | 0.2015040 | 1.005268× | 0.1855700 |
0.1907530 | 1.027930× |
| prefill_regression-0053 | 2 | 4096×2 | 16/16/64 | 128 | FP16/FP32 |
yes | 1/1/1/1 | F | 0.1394870 | 0.1450560 | 1.039925× | 0.1317460 |
0.1354900 | 1.028418× |
| prefill_regression-0054 | 2 | 2048+6144 | 16/16/64 | 128 | FP16/FP32 |
yes | 1/1/1/1 | F | 0.1959040 | 0.1997440 | 1.019601× | 0.1868180 |
0.1908820 | 1.021754× |
| prefill_regression-0055 | 2 | 1024+7168 | 16/16/64 | 128 | FP16/FP32 |
yes | 1/1/1/1 | F | 0.2280310 | 0.2282560 | 1.000987× | 0.2138580 |
0.2189780 | 1.023941× |
| prefill_regression-0056 | 4 | 2048×4 | 16/16/64 | 128 | FP16/FP32 |
yes | 1/1/1/1 | F | 0.1492165 | 0.1596480 | 1.069908× | 0.1416330 |
0.1515220 | 1.069821× |
| prefill_regression-0057 | 8 | 1024×8 | 16/16/64 | 128 | FP16/FP32 |
yes | 1/1/1/1 | F | 0.1676480 | 0.1952000 | 1.164344× | 0.1600330 |
0.1837460 | 1.148176× |
| prefill_regression-0058 | 8 | 8192×8 | 16/16/64 | 128 | FP16/FP32 |
yes | 1/1/1/1 | F | 1.0108800 | 1.0255360 | 1.014498× | 0.9519140 |
0.9666970 | 1.015530× |
| prefill_regression-0059 | 16 | 8192×16 | 16/16/64 | 128 | FP16/FP32 |
yes | 1/1/1/1 | F | 1.8548810 | 1.9180485 | 1.034055× | 1.7148040 |
1.7572525 | 1.024754× |
| prefill_regression-0060 | 32 | 8192×32 | 16/16/64 | 128 | FP16/FP32 |
yes | 1/1/1/1 | F | 3.7464670 | 3.8945750 | 1.039533× | 3.4082080 |
3.5666900 | 1.046500× |
| prefill_regression-0061 | 1 | 65536×1 | 16/16/32 | 128 | FP16/FP32 |
yes | 1/1/1/1 | R | 1.7116460 | 1.8665090 | 1.090476× | 1.6475960 |
1.8027330 | 1.094160× |
| prefill_regression-0062 | 1 | 32768×1 | 16/16/32 | 128 | FP16/FP32 |
yes | 1/1/1/1 | R | 0.8665900 | 0.9428780 | 1.088032× | 0.8281035 |
0.9114980 | 1.100705× |
| prefill_regression-0063 | 1 | 16384×1 | 16/16/32 | 128 | FP16/FP32 |
yes | 1/1/1/1 | R | 0.4394890 | 0.4815690 | 1.095748× | 0.4198780 |
0.4659910 | 1.109825× |
| prefill_regression-0064 | 1 | 8192×1 | 16/16/32 | 128 | FP16/FP32 |
yes | 1/1/1/1 | R | 0.2266240 | 0.2518400 | 1.111268× | 0.2157140 |
0.2432340 | 1.127576× |
| prefill_regression-0065 | 1 | 4096×1 | 16/16/32 | 128 | FP16/FP32 |
yes | 1/1/1/1 | R | 0.1184960 | 0.1364480 | 1.151499× | 0.1136330 |
0.1321610 | 1.163051× |
| prefill_regression-0066 | 1 | 2048×1 | 16/16/32 | 128 | FP16/FP32 |
yes | 1/1/1/1 | R | 0.0647040 | 0.0784640 | 1.212661× | 0.0614410 |
0.0755850 | 1.230205× |
| prefill_regression-0067 | 2 | 6144+2048 | 16/16/32 | 128 | FP16/FP32 |
yes | 1/1/1/1 | R | 0.1818560 | 0.1959675 | 1.077597× | 0.1771850 |
0.1880020 | 1.061049× |
| prefill_regression-0068 | 2 | 4096×2 | 16/16/32 | 128 | FP16/FP32 |
yes | 1/1/1/1 | R | 0.1258240 | 0.1396480 | 1.109868× | 0.1224650 |
0.1327050 | 1.083616× |
| prefill_regression-0069 | 2 | 2048+6144 | 16/16/32 | 128 | FP16/FP32 |
yes | 1/1/1/1 | R | 0.1811200 | 0.1968640 | 1.086926× | 0.1771530 |
0.1888970 | 1.066293× |
| prefill_regression-0070 | 2 | 1024+7168 | 16/16/32 | 128 | FP16/FP32 |
yes | 1/1/1/1 | R | 0.2070400 | 0.2254080 | 1.088717× | 0.2048020 |
0.2168980 | 1.059062× |
| prefill_regression-0071 | 4 | 2048×4 | 16/16/32 | 128 | FP16/FP32 |
yes | 1/1/1/1 | F | 0.0795200 | 0.0860810 | 1.082508× | 0.0763200 |
0.0823050 | 1.078420× |
| prefill_regression-0072 | 8 | 1024×8 | 16/16/32 | 128 | FP16/FP32 |
yes | 1/1/1/1 | F | 0.0894400 | 0.1018870 | 1.139166× | 0.0846730 |
0.0960970 | 1.134919× |
| prefill_regression-0073 | 8 | 8192×8 | 16/16/32 | 128 | FP16/FP32 |
yes | 1/1/1/1 | F | 0.5043840 | 0.5172955 | 1.025599× | 0.4791090 |
0.4944050 | 1.031926× |
| prefill_regression-0074 | 16 | 8192×16 | 16/16/32 | 128 | FP16/FP32 |
yes | 1/1/1/1 | F | 1.0213115 | 1.0486080 | 1.026727× | 0.9505005 |
0.9785360 | 1.029496× |
| prefill_regression-0075 | 32 | 8192×32 | 16/16/32 | 128 | FP16/FP32 |
yes | 1/1/1/1 | F | 1.8972340 | 1.9682730 | 1.037443× | 1.7090215 |
1.7877610 | 1.046073× |
| prefill_regression-0076 | 1 | 65536×1 | 16/16/48 | 128 | FP16/FP32 |
yes | 1/1/1/1 | R | 1.7279320 | 1.8422530 | 1.066161× | 1.6532330 |
1.7884655 | 1.081799× |
| prefill_regression-0077 | 1 | 32768×1 | 16/16/48 | 128 | FP16/FP32 |
yes | 1/1/1/1 | R | 0.8752970 | 0.9350730 | 1.068292× | 0.8334470 |
0.9087760 | 1.090382× |
| prefill_regression-0078 | 1 | 16384×1 | 16/16/48 | 128 | FP16/FP32 |
yes | 1/1/1/1 | R | 0.4474570 | 0.4798730 | 1.072445× | 0.4229480 |
0.4638440 | 1.096693× |
| prefill_regression-0079 | 1 | 8192×1 | 16/16/48 | 128 | FP16/FP32 |
yes | 1/1/1/1 | R | 0.2314560 | 0.2514880 | 1.086548× | 0.2178580 |
0.2425610 | 1.113390× |
| prefill_regression-0080 | 1 | 4096×1 | 16/16/48 | 128 | FP16/FP32 |
yes | 1/1/1/1 | R | 0.1223040 | 0.1371520 | 1.121402× | 0.1152650 |
0.1312650 | 1.138811× |
| prefill_regression-0081 | 1 | 2048×1 | 16/16/48 | 128 | FP16/FP32 |
yes | 1/1/1/1 | R | 0.0668790 | 0.0785910 | 1.175122× | 0.0630730 |
0.0755210 | 1.197359× |
| prefill_regression-0082 | 2 | 6144+2048 | 16/16/48 | 128 | FP16/FP32 |
yes | 1/1/1/1 | F | 0.1907200 | 0.1976960 | 1.036577× | 0.1818900 |
0.1886740 | 1.037297× |
| prefill_regression-0083 | 2 | 4096×2 | 16/16/48 | 128 | FP16/FP32 |
yes | 1/1/1/1 | F | 0.1370560 | 0.1434240 | 1.046463× | 0.1276810 |
0.1332170 | 1.043358× |
| prefill_regression-0084 | 2 | 2048+6144 | 16/16/48 | 128 | FP16/FP32 |
yes | 1/1/1/1 | F | 0.1916470 | 0.1975360 | 1.030728× | 0.1812180 |
0.1881630 | 1.038324× |
| prefill_regression-0085 | 2 | 1024+7168 | 16/16/48 | 128 | FP16/FP32 |
yes | 1/1/1/1 | F | 0.2183040 | 0.2256640 | 1.033714× | 0.2075540 |
0.2163540 | 1.042399× |
| prefill_regression-0086 | 4 | 2048×4 | 16/16/48 | 128 | FP16/FP32 |
yes | 1/1/1/1 | F | 0.1488320 | 0.1578880 | 1.060847× | 0.1383690 |
0.1492820 | 1.078869× |
| prefill_regression-0087 | 8 | 1024×8 | 16/16/48 | 128 | FP16/FP32 |
yes | 1/1/1/1 | F | 0.1292480 | 0.1469120 | 1.136667× | 0.1219860 |
0.1391050 | 1.140336× |
| prefill_regression-0088 | 8 | 8192×8 | 16/16/48 | 128 | FP16/FP32 |
yes | 1/1/1/1 | F | 0.7615680 | 0.7679680 | 1.008404× | 0.7057985 |
0.7243590 | 1.026297× |
| prefill_regression-0089 | 16 | 8192×16 | 16/16/48 | 128 | FP16/FP32 |
yes | 1/1/1/1 | F | 1.5237285 | 1.5719045 | 1.031617× | 1.4034040 |
1.4511170 | 1.033998× |
| prefill_regression-0090 | 32 | 8192×32 | 16/16/48 | 128 | FP16/FP32 |
yes | 1/1/1/1 | F | 2.8859720 | 3.0100995 | 1.043011× | 2.6528925 |
2.7656125 | 1.042489× |
| prefill_regression-0091 | 1 | 65536×1 | 16/16/16 | 128 | FP16/FP32 |
yes | 1/1/1/1 | R | 1.6819050 | 1.8571210 | 1.104177× | 1.6217090 |
1.7928790 | 1.105549× |
| prefill_regression-0092 | 1 | 32768×1 | 16/16/16 | 128 | FP16/FP32 |
yes | 1/1/1/1 | R | 0.8481115 | 0.9379520 | 1.105930× | 0.8159760 |
0.9068880 | 1.111415× |
| prefill_regression-0093 | 1 | 16384×1 | 16/16/16 | 128 | FP16/FP32 |
yes | 1/1/1/1 | R | 0.4285450 | 0.4790090 | 1.117757× | 0.4132510 |
0.4636840 | 1.122040× |
| prefill_regression-0094 | 1 | 8192×1 | 16/16/16 | 128 | FP16/FP32 |
yes | 1/1/1/1 | R | 0.2209910 | 0.2500160 | 1.131340× | 0.2118100 |
0.2415070 | 1.140206× |
| prefill_regression-0095 | 1 | 4096×1 | 16/16/16 | 128 | FP16/FP32 |
yes | 1/1/1/1 | R | 0.1152960 | 0.1344950 | 1.166519× | 0.1110410 |
0.1299210 | 1.170027× |
| prefill_regression-0096 | 1 | 2048×1 | 16/16/16 | 128 | FP16/FP32 |
yes | 1/1/1/1 | R | 0.0629120 | 0.0765760 | 1.217192× | 0.0605450 |
0.0740810 | 1.223569× |
| prefill_regression-0097 | 2 | 6144+2048 | 16/16/16 | 128 | FP16/FP32 |
yes | 1/1/1/1 | R | 0.1706560 | 0.1925440 | 1.128258× | 0.1621780 |
0.1862730 | 1.148571× |
| prefill_regression-0098 | 2 | 4096×2 | 16/16/16 | 128 | FP16/FP32 |
yes | 1/1/1/1 | R | 0.1186560 | 0.1361600 | 1.147519× | 0.1121930 |
0.1312010 | 1.169422× |
| prefill_regression-0099 | 2 | 2048+6144 | 16/16/16 | 128 | FP16/FP32 |
yes | 1/1/1/1 | R | 0.1701110 | 0.1925430 | 1.131867× | 0.1621460 |
0.1861460 | 1.148015× |
| prefill_regression-0100 | 2 | 1024+7168 | 16/16/16 | 128 | FP16/FP32 |
yes | 1/1/1/1 | R | 0.1949760 | 0.2206080 | 1.131462× | 0.1874260 |
0.2141460 | 1.142563× |
| prefill_regression-0101 | 4 | 2048×4 | 16/16/16 | 128 | FP16/FP32 |
yes | 1/1/1/1 | R | 0.0691520 | 0.0803190 | 1.161485× | 0.0675210 |
0.0769930 | 1.140282× |
| prefill_regression-0102 | 8 | 1024×8 | 16/16/16 | 128 | FP16/FP32 |
yes | 1/1/1/1 | F | 0.0497920 | 0.0557440 | 1.119537× | 0.0478720 |
0.0524170 | 1.094941× |
| prefill_regression-0103 | 8 | 8192×8 | 16/16/16 | 128 | FP16/FP32 |
yes | 1/1/1/1 | F | 0.2639030 | 0.2718070 | 1.029950× | 0.2446100 |
0.2507230 | 1.024991× |
| prefill_regression-0104 | 16 | 8192×16 | 16/16/16 | 128 | FP16/FP32 |
yes | 1/1/1/1 | F | 0.5133920 | 0.5346560 | 1.041419× | 0.4797800 |
0.5012205 | 1.044688× |
| prefill_regression-0105 | 32 | 8192×32 | 16/16/16 | 128 | FP16/FP32 |
yes | 1/1/1/1 | F | 1.0530575 | 1.0933770 | 1.038288× | 0.9829220 |
1.0160105 | 1.033663× |
| prefill_regression-0106 | 1 | 65536×1 | 32/32/32 | 128 | FP16/FP32 |
yes | 1/1/1/1 | R | 1.7110070 | 1.8696940 | 1.092745× | 1.6499030 |
1.8065760 | 1.094959× |
| prefill_regression-0107 | 1 | 32768×1 | 32/32/32 | 128 | FP16/FP32 |
yes | 1/1/1/1 | R | 0.8639680 | 0.9448640 | 1.093633× | 0.8306625 |
0.9143740 | 1.100777× |
| prefill_regression-0108 | 1 | 16384×1 | 32/32/32 | 128 | FP16/FP32 |
yes | 1/1/1/1 | R | 0.4391670 | 0.4831030 | 1.100044× | 0.4204515 |
0.4672040 | 1.111196× |
| prefill_regression-0109 | 1 | 8192×1 | 32/32/32 | 128 | FP16/FP32 |
yes | 1/1/1/1 | R | 0.2272010 | 0.2516480 | 1.107601× | 0.2164820 |
0.2435860 | 1.125202× |
| prefill_regression-0110 | 1 | 4096×1 | 32/32/32 | 128 | FP16/FP32 |
yes | 1/1/1/1 | R | 0.1198720 | 0.1370560 | 1.143353× | 0.1139530 |
0.1320010 | 1.158381× |
| prefill_regression-0111 | 1 | 2048×1 | 32/32/32 | 128 | FP16/FP32 |
yes | 1/1/1/1 | R | 0.0650550 | 0.0784640 | 1.206118× | 0.0620490 |
0.0761930 | 1.227949× |
| prefill_regression-0112 | 2 | 6144+2048 | 32/32/32 | 128 | FP16/FP32 |
yes | 1/1/1/1 | R | 0.1798720 | 0.1958400 | 1.088774× | 0.1774100 |
0.1890590 | 1.065661× |
| prefill_regression-0113 | 2 | 4096×2 | 32/32/32 | 128 | FP16/FP32 |
yes | 1/1/1/1 | R | 0.1258560 | 0.1399050 | 1.111628× | 0.1225290 |
0.1336340 | 1.090632× |
| prefill_regression-0114 | 2 | 2048+6144 | 32/32/32 | 128 | FP16/FP32 |
yes | 1/1/1/1 | R | 0.1794560 | 0.1960000 | 1.092190× | 0.1773460 |
0.1899550 | 1.071098× |
| prefill_regression-0115 | 2 | 1024+7168 | 32/32/32 | 128 | FP16/FP32 |
yes | 1/1/1/1 | R | 0.2074550 | 0.2257280 | 1.088082× | 0.2047060 |
0.2177630 | 1.063784× |
| prefill_regression-0116 | 4 | 2048×4 | 32/32/32 | 128 | FP16/FP32 |
yes | 1/1/1/1 | F | 0.0831040 | 0.0897600 | 1.080092× | 0.0793930 |
0.0842570 | 1.061265× |
| prefill_regression-0117 | 8 | 1024×8 | 32/32/32 | 128 | FP16/FP32 |
yes | 1/1/1/1 | F | 0.0911680 | 0.1042240 | 1.143208× | 0.0885450 |
0.1001930 | 1.131549× |
| prefill_regression-0118 | 8 | 8192×8 | 32/32/32 | 128 | FP16/FP32 |
yes | 1/1/1/1 | F | 0.5264320 | 0.5407370 | 1.027174× | 0.5012850 |
0.5056690 | 1.008746× |
| prefill_regression-0119 | 16 | 8192×16 | 32/32/32 | 128 | FP16/FP32 |
yes | 1/1/1/1 | F | 1.0648175 | 1.1026885 | 1.035566× | 1.0026990 |
1.0279150 | 1.025148× |
| prefill_regression-0120 | 32 | 8192×32 | 32/32/32 | 128 | FP16/FP32 |
yes | 1/1/1/1 | F | 1.9593590 | 2.0743195 | 1.058673× | 1.8729120 |
1.9136810 | 1.021768× |
| prefill_regression-0121 | 4 | 64×4 | 4/4/8 | 128 | BF16/FP32 | no |
0/0/0/0 | R | 0.0111680 | 0.0151680 | 1.358166× | 0.0110080 | 0.0149120
| 1.354651× |

## Adjacent-shape paired repeats (B200)

This separate matrix uses CuTe
`85da10187476d1a33e560fddbdbf7447d4937d31`, Q/K/V heads 16/16/32, D128,
BF16 inputs and FP32 state. Output and state checks pass before and
after CUDA Graph/CUPTI timing. Entries show independent repeat 1 /
repeat 2; speedup is CuTe / Cake for the corresponding repeat. These are
separate from the original acceptance CLI medians of 0.0748635 /
0.0748000 ms, whose logs do not contain paired CuTe medians.

| Shape | Cake ms (1 / 2) | CuTe ms (1 / 2) | Speedup (1 / 2) |
|---|---:|---:|---:|
| B2/S2048 | 0.069056 / 0.068928 | 0.071840 / 0.071999 | 1.040315× /
1.044554× |
| B3/S2048 | 0.072704 / 0.072672 | 0.073984 / 0.073920 | 1.017606× /
1.017173× |
| B4/S2048 | 0.074719 / 0.074912 | 0.076128 / 0.075936 | 1.018857× /
1.013669× |
| B4/S2049 | 0.078112 / 0.078208 | 0.079712 / 0.079552 | 1.020483× /
1.017185× |
| B4/S128 | 0.015776 / 0.015744 | 0.016672 / 0.016672 | 1.056795× /
1.058943× |


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Performance**
  * Refreshed GDN prefill validation for B200 and B300 hardware.
* Confirmed performance and correctness across supported shapes against
acceptance thresholds.

* **Documentation**
* Added benchmark results, validation details, and reproducibility
artifacts.
* Documented explicit Cake GDN backend selection while preserving
automatic CuTe dispatch.

* **Reliability**
* Improved synchronization behavior in generated prefill kernels while
preserving numerical behavior and public APIs.
* GDN prefill backend comparisons now skip automatically on CUDA
versions below 13.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [5306db7](https://github.com/flashinfer-ai/flashinfer/commit/5306db71665aeed6617f608ded9148d7a4da8e90)

- **作者**: Brian K. Ryu
- **时间**: 2026-09-15T23:11:30Z
- **提交信息**: feat(moe): add cuTile MXFP4 and W4A16 support (#5099)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

This PR expands cuTile fused MoE precision support:
- Add MXFP4-weight/MXFP4-activation W4A4 support on SM120 and SM121.
- Add NVFP4-weight/BF16-activation and MXFP4-weight/BF16-activation
W4A16 paths on SM89, SM90, SM120, and SM121.
- SM120/121 W4A16 and W4A4 to consume the same prepared packed weights
and scale layout.
- Use architecture-appropriate weight-scale layouts and FP4 decoding on
SM89/90.
- Extend the unified MoE API, autotuning, documentation, benchmarks, and
tests for the new combinations.

Suppot matrix:
| Precision | Supported architectures |
|---|---|
| NVFP4 W4A16 | SM89, SM90, SM120, SM121 |
| MXFP4 W4A16 | SM89, SM90, SM120, SM121 |
| MXFP4 W4A4 | SM120, SM121 |

<details>
<summary><strong>Performance: cuTile versus CUTLASS and
b12x</strong></summary>

Measured on H100 NVL (SM90) and RTX PRO 6000 Blackwell Server Edition
(SM120).

| Model shape | Activation | Hidden | Intermediate | Experts | Top-k |
|---|---|---:|---:|---:|---:|
| Qwen3.6-35B-A3B | SwiGLU | 2048 | 512 | 256 | 8 |
| Nemotron-3.5-Lightning-30B-A3B | ReLU2 | 2688 | 1856 | 128 | 6 |

<details>
<summary>SM90: NVFP4 W4A16 — Qwen and Nemotron</summary>

| Model | Tokens | cuTile (µs) | CUTLASS (µs) | Speedup (CUTLASS/cuTile)
|
|---|---:|---:|---:|---:|
| Qwen | 1 | 93.49 | N/A | N/A |
| Qwen | 2 | 98.77 | N/A | N/A |
| Qwen | 4 | 116.64 | N/A | N/A |
| Qwen | 8 | 207.27 | N/A | N/A |
| Qwen | 16 | 378.58 | N/A | N/A |
| Qwen | 32 | 708.38 | N/A | N/A |
| Qwen | 64 | 708.07 | N/A | N/A |
| Qwen | 128 | 714.98 | N/A | N/A |
| Qwen | 256 | 724.07 | N/A | N/A |
| Qwen | 512 | 818.55 | N/A | N/A |
| Qwen | 1024 | 841.95 | N/A | N/A |
| Qwen | 2048 | 1594.21 | N/A | N/A |
| Qwen | 4096 | 3063.65 | N/A | N/A |
| Qwen | 8192 | 5581.72 | N/A | N/A |
| Nemotron | 1 | 125.03 | N/A | N/A |
| Nemotron | 2 | 170.72 | N/A | N/A |
| Nemotron | 4 | 289.76 | N/A | N/A |
| Nemotron | 8 | 530.50 | N/A | N/A |
| Nemotron | 16 | 974.95 | N/A | N/A |
| Nemotron | 32 | 1274.12 | N/A | N/A |
| Nemotron | 64 | 1277.15 | N/A | N/A |
| Nemotron | 128 | 1280.40 | N/A | N/A |
| Nemotron | 256 | 1374.30 | N/A | N/A |
| Nemotron | 512 | 1388.21 | N/A | N/A |
| Nemotron | 1024 | 1991.16 | N/A | N/A |
| Nemotron | 2048 | 3873.66 | N/A | N/A |
| Nemotron | 4096 | 5687.88 | N/A | N/A |
| Nemotron | 8192 | 11194.30 | N/A | N/A |

</details>

<details>
<summary>SM90: MXFP4 W4A16 — Qwen and Nemotron</summary>

| Model | Tokens | cuTile (µs) | CUTLASS (µs) | Speedup (CUTLASS/cuTile)
|
|---|---:|---:|---:|---:|
| Qwen | 1 | 84.24 | 51.19 | 0.61x |
| Qwen | 2 | 89.84 | 59.01 | 0.66x |
| Qwen | 4 | 133.27 | 78.29 | 0.59x |
| Qwen | 8 | 226.69 | 113.22 | 0.50x |
| Qwen | 16 | 422.68 | 176.48 | 0.42x |
| Qwen | 32 | 766.14 | 304.10 | 0.40x |
| Qwen | 64 | 767.26 | 303.84 | 0.40x |
| Qwen | 128 | 769.05 | 310.79 | 0.40x |
| Qwen | 256 | 769.88 | 315.65 | 0.41x |
| Qwen | 512 | 964.15 | 354.88 | 0.37x |
| Qwen | 1024 | 971.90 | 454.21 | 0.47x |
| Qwen | 2048 | 1460.58 | 526.47 | 0.36x |
| Qwen | 4096 | 3727.61 | 918.87 | 0.25x |
| Qwen | 8192 | 5033.58 | 1813.38 | 0.36x |
| Nemotron | 1 | 95.25 | N/A | N/A |
| Nemotron | 2 | 138.85 | N/A | N/A |
| Nemotron | 4 | 235.41 | N/A | N/A |
| Nemotron | 8 | 434.25 | N/A | N/A |
| Nemotron | 16 | 795.98 | N/A | N/A |
| Nemotron | 32 | 1048.97 | N/A | N/A |
| Nemotron | 64 | 1051.36 | N/A | N/A |
| Nemotron | 128 | 1053.53 | N/A | N/A |
| Nemotron | 256 | 1316.97 | N/A | N/A |
| Nemotron | 512 | 1332.86 | N/A | N/A |
| Nemotron | 1024 | 1764.42 | N/A | N/A |
| Nemotron | 2048 | 3809.26 | N/A | N/A |
| Nemotron | 4096 | 5020.93 | N/A | N/A |
| Nemotron | 8192 | 9855.48 | N/A | N/A |

</details>

<details>
<summary>SM120: NVFP4 W4A16 — Qwen and Nemotron</summary>

| Model | Tokens | cuTile (µs) | b12x (µs) | Speedup (b12x/cuTile) |
|---|---:|---:|---:|---:|
| Qwen | 1 | 42.75 | 27.49 | 0.64x |
| Qwen | 2 | 52.72 | 41.41 | 0.79x |
| Qwen | 4 | 79.34 | N/A* | N/A |
| Qwen | 8 | 134.77 | 135.18 | 1.00x |
| Qwen | 16 | 232.47 | 233.31 | 1.00x |
| Qwen | 32 | 387.73 | 401.55 | 1.04x |
| Qwen | 64 | 389.62 | 409.55 | 1.05x |
| Qwen | 128 | 393.73 | 426.54 | 1.08x |
| Qwen | 256 | 403.01 | 452.24 | 1.12x |
| Qwen | 512 | 425.68 | 528.32 | 1.24x |
| Qwen | 1024 | 447.68 | 679.57 | 1.52x |
| Qwen | 2048 | 524.31 | 1014.12 | 1.93x |
| Qwen | 4096 | 1014.77 | 1871.02 | 1.84x |
| Qwen | 8192 | 1677.80 | 3704.26 | 2.21x |
| Nemotron | 1 | 60.74 | 46.98 | 0.77x |
| Nemotron | 2 | 82.99 | 75.74 | 0.91x |
| Nemotron | 4 | 154.08 | 139.94 | 0.91x |
| Nemotron | 8 | 265.71 | 258.54 | 0.97x |
| Nemotron | 16 | 452.22 | 438.64 | 0.97x |
| Nemotron | 32 | 576.62 | 563.25 | 0.98x |
| Nemotron | 64 | 581.15 | 567.25 | 0.98x |
| Nemotron | 128 | 589.76 | 576.88 | 0.98x |
| Nemotron | 256 | 612.20 | 595.06 | 0.97x |
| Nemotron | 512 | 629.65 | 667.97 | 1.06x |
| Nemotron | 1024 | 710.98 | 873.73 | 1.23x |
| Nemotron | 2048 | 1093.00 | 1663.53 | 1.52x |
| Nemotron | 4096 | 1817.74 | 2601.77 | 1.43x |
| Nemotron | 8192 | 3717.83 | 5158.66 | 1.39x |

</details>

<details>
<summary>SM120: MXFP4 W4A16 — Qwen and Nemotron</summary>

| Model | Tokens | cuTile (µs) | b12x (µs) | Speedup (b12x/cuTile) |
|---|---:|---:|---:|---:|
| Qwen | 1 | 39.54 | N/A | N/A |
| Qwen | 2 | 52.22 | N/A | N/A |
| Qwen | 4 | 76.05 | N/A | N/A |
| Qwen | 8 | 127.68 | N/A | N/A |
| Qwen | 16 | 220.51 | N/A | N/A |
| Qwen | 32 | 367.73 | N/A | N/A |
| Qwen | 64 | 370.14 | N/A | N/A |
| Qwen | 128 | 372.95 | N/A | N/A |
| Qwen | 256 | 382.27 | N/A | N/A |
| Qwen | 512 | 398.80 | N/A | N/A |
| Qwen | 1024 | 418.96 | N/A | N/A |
| Qwen | 2048 | 538.64 | N/A | N/A |
| Qwen | 4096 | 1021.01 | N/A | N/A |
| Qwen | 8192 | 1763.85 | N/A | N/A |
| Nemotron | 1 | 59.09 | N/A | N/A |
| Nemotron | 2 | 79.63 | N/A | N/A |
| Nemotron | 4 | 146.38 | N/A | N/A |
| Nemotron | 8 | 254.83 | N/A | N/A |
| Nemotron | 16 | 429.23 | N/A | N/A |
| Nemotron | 32 | 547.27 | N/A | N/A |
| Nemotron | 64 | 550.75 | N/A | N/A |
| Nemotron | 128 | 560.95 | N/A | N/A |
| Nemotron | 256 | 583.65 | N/A | N/A |
| Nemotron | 512 | 602.45 | N/A | N/A |
| Nemotron | 1024 | 689.00 | N/A | N/A |
| Nemotron | 2048 | 1087.25 | N/A | N/A |
| Nemotron | 4096 | 1776.46 | N/A | N/A |
| Nemotron | 8192 | 4749.42 | N/A | N/A |

</details>

<details>
<summary>SM120: NVFP4 W4A4 — Qwen and Nemotron</summary>

| Model | Tokens | cuTile (µs) | b12x (µs) | Speedup (b12x/cuTile) |
|---|---:|---:|---:|---:|
| Qwen | 1 | 49.23 | 27.71 | 0.56x |
| Qwen | 2 | 63.41 | 47.47 | 0.75x |
| Qwen | 4 | 84.00 | 68.74 | 0.82x |
| Qwen | 8 | 132.32 | 141.25 | 1.07x |
| Qwen | 16 | 228.80 | 224.31 | 0.98x |
| Qwen | 32 | 385.17 | 377.60 | 0.98x |
| Qwen | 64 | 384.59 | 383.54 | 1.00x |
| Qwen | 128 | 388.88 | 386.22 | 0.99x |
| Qwen | 256 | 395.95 | 399.01 | 1.01x |
| Qwen | 512 | 412.91 | 411.47 | 1.00x |
| Qwen | 1024 | 422.93 | 429.60 | 1.02x |
| Qwen | 2048 | 527.46 | 488.98 | 0.93x |
| Qwen | 4096 | 753.60 | 467.17 | 0.62x |
| Qwen | 8192 | 1185.11 | 608.43 | 0.51x |
| Nemotron | 1 | 72.62 | 66.21 | 0.91x |
| Nemotron | 2 | 91.57 | 169.15 | 1.85x |
| Nemotron | 4 | 152.71 | 201.50 | 1.32x |
| Nemotron | 8 | 269.15 | 284.13 | 1.06x |
| Nemotron | 16 | 455.44 | 504.51 | 1.11x |
| Nemotron | 32 | 577.52 | 646.11 | 1.12x |
| Nemotron | 64 | 578.83 | 653.09 | 1.13x |
| Nemotron | 128 | 583.84 | 679.49 | 1.16x |
| Nemotron | 256 | 596.50 | 610.29 | 1.02x |
| Nemotron | 512 | 612.15 | 626.74 | 1.02x |
| Nemotron | 1024 | 669.12 | 685.64 | 1.02x |
| Nemotron | 2048 | 843.40 | 821.01 | 0.97x |
| Nemotron | 4096 | 1174.24 | 1423.08 | 1.21x |
| Nemotron | 8192 | 2043.66 | 2333.96 | 1.14x |

</details>

<details>
<summary>SM120: MXFP4 W4A4 — Qwen and Nemotron</summary>

| Model | Tokens | cuTile (µs) | b12x (µs) | Speedup (b12x/cuTile) |
|---|---:|---:|---:|---:|
| Qwen | 1 | 37.81 | N/A | N/A |
| Qwen | 2 | 51.79 | N/A | N/A |
| Qwen | 4 | 78.48 | N/A | N/A |
| Qwen | 8 | 130.26 | N/A | N/A |
| Qwen | 16 | 225.70 | N/A | N/A |
| Qwen | 32 | 372.37 | N/A | N/A |
| Qwen | 64 | 373.39 | N/A | N/A |
| Qwen | 128 | 373.54 | N/A | N/A |
| Qwen | 256 | 381.54 | N/A | N/A |
| Qwen | 512 | 395.52 | N/A | N/A |
| Qwen | 1024 | 402.66 | N/A | N/A |
| Qwen | 2048 | 484.27 | N/A | N/A |
| Qwen | 4096 | 695.86 | N/A | N/A |
| Qwen | 8192 | 1179.20 | N/A | N/A |
| Nemotron | 1 | 59.82 | N/A | N/A |
| Nemotron | 2 | 90.10 | N/A | N/A |
| Nemotron | 4 | 146.30 | N/A | N/A |
| Nemotron | 8 | 257.79 | N/A | N/A |
| Nemotron | 16 | 434.82 | N/A | N/A |
| Nemotron | 32 | 555.30 | N/A | N/A |
| Nemotron | 64 | 554.67 | N/A | N/A |
| Nemotron | 128 | 552.28 | N/A | N/A |
| Nemotron | 256 | 567.57 | N/A | N/A |
| Nemotron | 512 | 583.20 | N/A | N/A |
| Nemotron | 1024 | 628.55 | N/A | N/A |
| Nemotron | 2048 | 749.27 | N/A | N/A |
| Nemotron | 4096 | 1080.24 | N/A | N/A |
| Nemotron | 8192 | 1916.04 | N/A | N/A |

</details>

<details>
<summary>SM90 reproducible testlist — save as sm90.txt</summary>

```text
# PR #5099: autotuned, cold-L2, one MoE invocation per CUDA graph replay.
--routine unified_moe --backends cutlass cutile --quant-variant mxfp4_w4a16 --num_tokens 1 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_mxfp4_w4a16
--routine unified_moe --backends cutlass cutile --quant-variant mxfp4_w4a16 --num_tokens 2 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_mxfp4_w4a16
--routine unified_moe --backends cutlass cutile --quant-variant mxfp4_w4a16 --num_tokens 4 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_mxfp4_w4a16
--routine unified_moe --backends cutlass cutile --quant-variant mxfp4_w4a16 --num_tokens 8 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_mxfp4_w4a16
--routine unified_moe --backends cutlass cutile --quant-variant mxfp4_w4a16 --num_tokens 16 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_mxfp4_w4a16
--routine unified_moe --backends cutlass cutile --quant-variant mxfp4_w4a16 --num_tokens 32 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_mxfp4_w4a16
--routine unified_moe --backends cutlass cutile --quant-variant mxfp4_w4a16 --num_tokens 64 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_mxfp4_w4a16
--routine unified_moe --backends cutlass cutile --quant-variant mxfp4_w4a16 --num_tokens 128 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_mxfp4_w4a16
--routine unified_moe --backends cutlass cutile --quant-variant mxfp4_w4a16 --num_tokens 256 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_mxfp4_w4a16
--routine unified_moe --backends cutlass cutile --quant-variant mxfp4_w4a16 --num_tokens 512 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_mxfp4_w4a16
--routine unified_moe --backends cutlass cutile --quant-variant mxfp4_w4a16 --num_tokens 1024 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_mxfp4_w4a16
--routine unified_moe --backends cutlass cutile --quant-variant mxfp4_w4a16 --num_tokens 2048 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_mxfp4_w4a16
--routine unified_moe --backends cutlass cutile --quant-variant mxfp4_w4a16 --num_tokens 4096 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_mxfp4_w4a16
--routine unified_moe --backends cutlass cutile --quant-variant mxfp4_w4a16 --num_tokens 8192 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_mxfp4_w4a16
--routine unified_moe --backends cutile --quant-variant nvfp4_w4a16 --num_tokens 1 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_nvfp4_w4a16
--routine unified_moe --backends cutile --quant-variant nvfp4_w4a16 --num_tokens 2 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_nvfp4_w4a16
--routine unified_moe --backends cutile --quant-variant nvfp4_w4a16 --num_tokens 4 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_nvfp4_w4a16
--routine unified_moe --backends cutile --quant-variant nvfp4_w4a16 --num_tokens 8 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_nvfp4_w4a16
--routine unified_moe --backends cutile --quant-variant nvfp4_w4a16 --num_tokens 16 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_nvfp4_w4a16
--routine unified_moe --backends cutile --quant-variant nvfp4_w4a16 --num_tokens 32 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_nvfp4_w4a16
--routine unified_moe --backends cutile --quant-variant nvfp4_w4a16 --num_tokens 64 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_nvfp4_w4a16
--routine unified_moe --backends cutile --quant-variant nvfp4_w4a16 --num_tokens 128 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_nvfp4_w4a16
--routine unified_moe --backends cutile --quant-variant nvfp4_w4a16 --num_tokens 256 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_nvfp4_w4a16
--routine unified_moe --backends cutile --quant-variant nvfp4_w4a16 --num_tokens 512 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_nvfp4_w4a16
--routine unified_moe --backends cutile --quant-variant nvfp4_w4a16 --num_tokens 1024 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_nvfp4_w4a16
--routine unified_moe --backends cutile --quant-variant nvfp4_w4a16 --num_tokens 2048 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_nvfp4_w4a16
--routine unified_moe --backends cutile --quant-variant nvfp4_w4a16 --num_tokens 4096 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_nvfp4_w4a16
--routine unified_moe --backends cutile --quant-variant nvfp4_w4a16 --num_tokens 8192 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_nvfp4_w4a16
--routine unified_moe --backends cutile --quant-variant mxfp4_w4a16 --num_tokens 1 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_mxfp4_w4a16
--routine unified_moe --backends cutile --quant-variant mxfp4_w4a16 --num_tokens 2 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_mxfp4_w4a16
--routine unified_moe --backends cutile --quant-variant mxfp4_w4a16 --num_tokens 4 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_mxfp4_w4a16
--routine unified_moe --backends cutile --quant-variant mxfp4_w4a16 --num_tokens 8 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_mxfp4_w4a16
--routine unified_moe --backends cutile --quant-variant mxfp4_w4a16 --num_tokens 16 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_mxfp4_w4a16
--routine unified_moe --backends cutile --quant-variant mxfp4_w4a16 --num_tokens 32 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_mxfp4_w4a16
--routine unified_moe --backends cutile --quant-variant mxfp4_w4a16 --num_tokens 64 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_mxfp4_w4a16
--routine unified_moe --backends cutile --quant-variant mxfp4_w4a16 --num_tokens 128 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_mxfp4_w4a16
--routine unified_moe --backends cutile --quant-variant mxfp4_w4a16 --num_tokens 256 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_mxfp4_w4a16
--routine unified_moe --backends cutile --quant-variant mxfp4_w4a16 --num_tokens 512 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_mxfp4_w4a16
--routine unified_moe --backends cutile --quant-variant mxfp4_w4a16 --num_tokens 1024 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_mxfp4_w4a16
--routine unified_moe --backends cutile --quant-variant mxfp4_w4a16 --num_tokens 2048 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_mxfp4_w4a16
--routine unified_moe --backends cutile --quant-variant mxfp4_w4a16 --num_tokens 4096 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_mxfp4_w4a16
--routine unified_moe --backends cutile --quant-variant mxfp4_w4a16 --num_tokens 8192 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_mxfp4_w4a16
--routine unified_moe --backends cutile --quant-variant nvfp4_w4a16 --num_tokens 1 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_nvfp4_w4a16
--routine unified_moe --backends cutile --quant-variant nvfp4_w4a16 --num_tokens 2 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_nvfp4_w4a16
--routine unified_moe --backends cutile --quant-variant nvfp4_w4a16 --num_tokens 4 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_nvfp4_w4a16
--routine unified_moe --backends cutile --quant-variant nvfp4_w4a16 --num_tokens 8 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_nvfp4_w4a16
--routine unified_moe --backends cutile --quant-variant nvfp4_w4a16 --num_tokens 16 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_nvfp4_w4a16
--routine unified_moe --backends cutile --quant-variant nvfp4_w4a16 --num_tokens 32 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_nvfp4_w4a16
--routine unified_moe --backends cutile --quant-variant nvfp4_w4a16 --num_tokens 64 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_nvfp4_w4a16
--routine unified_moe --backends cutile --quant-variant nvfp4_w4a16 --num_tokens 128 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_nvfp4_w4a16
--routine unified_moe --backends cutile --quant-variant nvfp4_w4a16 --num_tokens 256 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_nvfp4_w4a16
--routine unified_moe --backends cutile --quant-variant nvfp4_w4a16 --num_tokens 512 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_nvfp4_w4a16
--routine unified_moe --backends cutile --quant-variant nvfp4_w4a16 --num_tokens 1024 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_nvfp4_w4a16
--routine unified_moe --backends cutile --quant-variant nvfp4_w4a16 --num_tokens 2048 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_nvfp4_w4a16
--routine unified_moe --backends cutile --quant-variant nvfp4_w4a16 --num_tokens 4096 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_nvfp4_w4a16
--routine unified_moe --backends cutile --quant-variant nvfp4_w4a16 --num_tokens 8192 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_nvfp4_w4a16
```

</details>

<details>
<summary>SM120 reproducible testlist — save as sm120.txt</summary>

```text
# PR #5099: autotuned, cold-L2, one MoE invocation per CUDA graph replay.
--routine unified_moe --backends b12x cutile --quant-variant nvfp4_w4a16 --num_tokens 1 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_nvfp4_w4a16
--routine unified_moe --backends b12x cutile --quant-variant nvfp4_w4a16 --num_tokens 2 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_nvfp4_w4a16
--routine unified_moe --backends b12x cutile --quant-variant nvfp4_w4a16 --num_tokens 4 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_nvfp4_w4a16
--routine unified_moe --backends b12x cutile --quant-variant nvfp4_w4a16 --num_tokens 8 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_nvfp4_w4a16
--routine unified_moe --backends b12x cutile --quant-variant nvfp4_w4a16 --num_tokens 16 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_nvfp4_w4a16
--routine unified_moe --backends b12x cutile --quant-variant nvfp4_w4a16 --num_tokens 32 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_nvfp4_w4a16
--routine unified_moe --backends b12x cutile --quant-variant nvfp4_w4a16 --num_tokens 64 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_nvfp4_w4a16
--routine unified_moe --backends b12x cutile --quant-variant nvfp4_w4a16 --num_tokens 128 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_nvfp4_w4a16
--routine unified_moe --backends b12x cutile --quant-variant nvfp4_w4a16 --num_tokens 256 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_nvfp4_w4a16
--routine unified_moe --backends b12x cutile --quant-variant nvfp4_w4a16 --num_tokens 512 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_nvfp4_w4a16
--routine unified_moe --backends b12x cutile --quant-variant nvfp4_w4a16 --num_tokens 1024 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_nvfp4_w4a16
--routine unified_moe --backends b12x cutile --quant-variant nvfp4_w4a16 --num_tokens 2048 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_nvfp4_w4a16
--routine unified_moe --backends b12x cutile --quant-variant nvfp4_w4a16 --num_tokens 4096 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_nvfp4_w4a16
--routine unified_moe --backends b12x cutile --quant-variant nvfp4_w4a16 --num_tokens 8192 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_nvfp4_w4a16
--routine unified_moe --backends cutile --quant-variant mxfp4_w4a16 --num_tokens 1 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_mxfp4_w4a16
--routine unified_moe --backends cutile --quant-variant mxfp4_w4a16 --num_tokens 2 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_mxfp4_w4a16
--routine unified_moe --backends cutile --quant-variant mxfp4_w4a16 --num_tokens 4 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_mxfp4_w4a16
--routine unified_moe --backends cutile --quant-variant mxfp4_w4a16 --num_tokens 8 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_mxfp4_w4a16
--routine unified_moe --backends cutile --quant-variant mxfp4_w4a16 --num_tokens 16 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_mxfp4_w4a16
--routine unified_moe --backends cutile --quant-variant mxfp4_w4a16 --num_tokens 32 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_mxfp4_w4a16
--routine unified_moe --backends cutile --quant-variant mxfp4_w4a16 --num_tokens 64 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_mxfp4_w4a16
--routine unified_moe --backends cutile --quant-variant mxfp4_w4a16 --num_tokens 128 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_mxfp4_w4a16
--routine unified_moe --backends cutile --quant-variant mxfp4_w4a16 --num_tokens 256 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_mxfp4_w4a16
--routine unified_moe --backends cutile --quant-variant mxfp4_w4a16 --num_tokens 512 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_mxfp4_w4a16
--routine unified_moe --backends cutile --quant-variant mxfp4_w4a16 --num_tokens 1024 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_mxfp4_w4a16
--routine unified_moe --backends cutile --quant-variant mxfp4_w4a16 --num_tokens 2048 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_mxfp4_w4a16
--routine unified_moe --backends cutile --quant-variant mxfp4_w4a16 --num_tokens 4096 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_mxfp4_w4a16
--routine unified_moe --backends cutile --quant-variant mxfp4_w4a16 --num_tokens 8192 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_mxfp4_w4a16
--routine unified_moe --backends cutile --quant-variant mxfp4 --num_tokens 1 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_mxfp4
--routine unified_moe --backends cutile --quant-variant mxfp4 --num_tokens 2 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_mxfp4
--routine unified_moe --backends cutile --quant-variant mxfp4 --num_tokens 4 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_mxfp4
--routine unified_moe --backends cutile --quant-variant mxfp4 --num_tokens 8 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_mxfp4
--routine unified_moe --backends cutile --quant-variant mxfp4 --num_tokens 16 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_mxfp4
--routine unified_moe --backends cutile --quant-variant mxfp4 --num_tokens 32 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_mxfp4
--routine unified_moe --backends cutile --quant-variant mxfp4 --num_tokens 64 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_mxfp4
--routine unified_moe --backends cutile --quant-variant mxfp4 --num_tokens 128 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_mxfp4
--routine unified_moe --backends cutile --quant-variant mxfp4 --num_tokens 256 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_mxfp4
--routine unified_moe --backends cutile --quant-variant mxfp4 --num_tokens 512 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_mxfp4
--routine unified_moe --backends cutile --quant-variant mxfp4 --num_tokens 1024 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_mxfp4
--routine unified_moe --backends cutile --quant-variant mxfp4 --num_tokens 2048 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_mxfp4
--routine unified_moe --backends cutile --quant-variant mxfp4 --num_tokens 4096 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_mxfp4
--routine unified_moe --backends cutile --quant-variant mxfp4 --num_tokens 8192 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_mxfp4
--routine unified_moe --backends b12x cutile --quant-variant nvfp4 --num_tokens 1 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_nvfp4
--routine unified_moe --backends b12x cutile --quant-variant nvfp4 --num_tokens 2 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_nvfp4
--routine unified_moe --backends b12x cutile --quant-variant nvfp4 --num_tokens 4 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_nvfp4
--routine unified_moe --backends b12x cutile --quant-variant nvfp4 --num_tokens 8 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_nvfp4
--routine unified_moe --backends b12x cutile --quant-variant nvfp4 --num_tokens 16 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_nvfp4
--routine unified_moe --backends b12x cutile --quant-variant nvfp4 --num_tokens 32 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_nvfp4
--routine unified_moe --backends b12x cutile --quant-variant nvfp4 --num_tokens 64 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_nvfp4
--routine unified_moe --backends b12x cutile --quant-variant nvfp4 --num_tokens 128 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_nvfp4
--routine unified_moe --backends b12x cutile --quant-variant nvfp4 --num_tokens 256 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_nvfp4
--routine unified_moe --backends b12x cutile --quant-variant nvfp4 --num_tokens 512 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_nvfp4
--routine unified_moe --backends b12x cutile --quant-variant nvfp4 --num_tokens 1024 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_nvfp4
--routine unified_moe --backends b12x cutile --quant-variant nvfp4 --num_tokens 2048 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_nvfp4
--routine unified_moe --backends b12x cutile --quant-variant nvfp4 --num_tokens 4096 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_nvfp4
--routine unified_moe --backends b12x cutile --quant-variant nvfp4 --num_tokens 8192 --hidden_size 2048 --intermediate_size 512 --num_experts 256 --top_k 8 --activation-type Swiglu --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag qwen_nvfp4
--routine unified_moe --backends b12x cutile --quant-variant nvfp4_w4a16 --num_tokens 1 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_nvfp4_w4a16
--routine unified_moe --backends b12x cutile --quant-variant nvfp4_w4a16 --num_tokens 2 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_nvfp4_w4a16
--routine unified_moe --backends b12x cutile --quant-variant nvfp4_w4a16 --num_tokens 4 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_nvfp4_w4a16
--routine unified_moe --backends b12x cutile --quant-variant nvfp4_w4a16 --num_tokens 8 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_nvfp4_w4a16
--routine unified_moe --backends b12x cutile --quant-variant nvfp4_w4a16 --num_tokens 16 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_nvfp4_w4a16
--routine unified_moe --backends b12x cutile --quant-variant nvfp4_w4a16 --num_tokens 32 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_nvfp4_w4a16
--routine unified_moe --backends b12x cutile --quant-variant nvfp4_w4a16 --num_tokens 64 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_nvfp4_w4a16
--routine unified_moe --backends b12x cutile --quant-variant nvfp4_w4a16 --num_tokens 128 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_nvfp4_w4a16
--routine unified_moe --backends b12x cutile --quant-variant nvfp4_w4a16 --num_tokens 256 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_nvfp4_w4a16
--routine unified_moe --backends b12x cutile --quant-variant nvfp4_w4a16 --num_tokens 512 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_nvfp4_w4a16
--routine unified_moe --backends b12x cutile --quant-variant nvfp4_w4a16 --num_tokens 1024 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_nvfp4_w4a16
--routine unified_moe --backends b12x cutile --quant-variant nvfp4_w4a16 --num_tokens 2048 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_nvfp4_w4a16
--routine unified_moe --backends b12x cutile --quant-variant nvfp4_w4a16 --num_tokens 4096 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_nvfp4_w4a16
--routine unified_moe --backends b12x cutile --quant-variant nvfp4_w4a16 --num_tokens 8192 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_nvfp4_w4a16
--routine unified_moe --backends cutile --quant-variant mxfp4_w4a16 --num_tokens 1 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_mxfp4_w4a16
--routine unified_moe --backends cutile --quant-variant mxfp4_w4a16 --num_tokens 2 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_mxfp4_w4a16
--routine unified_moe --backends cutile --quant-variant mxfp4_w4a16 --num_tokens 4 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_mxfp4_w4a16
--routine unified_moe --backends cutile --quant-variant mxfp4_w4a16 --num_tokens 8 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_mxfp4_w4a16
--routine unified_moe --backends cutile --quant-variant mxfp4_w4a16 --num_tokens 16 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_mxfp4_w4a16
--routine unified_moe --backends cutile --quant-variant mxfp4_w4a16 --num_tokens 32 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_mxfp4_w4a16
--routine unified_moe --backends cutile --quant-variant mxfp4_w4a16 --num_tokens 64 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_mxfp4_w4a16
--routine unified_moe --backends cutile --quant-variant mxfp4_w4a16 --num_tokens 128 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_mxfp4_w4a16
--routine unified_moe --backends cutile --quant-variant mxfp4_w4a16 --num_tokens 256 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_mxfp4_w4a16
--routine unified_moe --backends cutile --quant-variant mxfp4_w4a16 --num_tokens 512 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_mxfp4_w4a16
--routine unified_moe --backends cutile --quant-variant mxfp4_w4a16 --num_tokens 1024 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_mxfp4_w4a16
--routine unified_moe --backends cutile --quant-variant mxfp4_w4a16 --num_tokens 2048 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_mxfp4_w4a16
--routine unified_moe --backends cutile --quant-variant mxfp4_w4a16 --num_tokens 4096 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_mxfp4_w4a16
--routine unified_moe --backends cutile --quant-variant mxfp4_w4a16 --num_tokens 8192 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_mxfp4_w4a16
--routine unified_moe --backends cutile --quant-variant mxfp4 --num_tokens 1 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_mxfp4
--routine unified_moe --backends cutile --quant-variant mxfp4 --num_tokens 2 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_mxfp4
--routine unified_moe --backends cutile --quant-variant mxfp4 --num_tokens 4 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_mxfp4
--routine unified_moe --backends cutile --quant-variant mxfp4 --num_tokens 8 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_mxfp4
--routine unified_moe --backends cutile --quant-variant mxfp4 --num_tokens 16 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_mxfp4
--routine unified_moe --backends cutile --quant-variant mxfp4 --num_tokens 32 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_mxfp4
--routine unified_moe --backends cutile --quant-variant mxfp4 --num_tokens 64 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_mxfp4
--routine unified_moe --backends cutile --quant-variant mxfp4 --num_tokens 128 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_mxfp4
--routine unified_moe --backends cutile --quant-variant mxfp4 --num_tokens 256 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_mxfp4
--routine unified_moe --backends cutile --quant-variant mxfp4 --num_tokens 512 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_mxfp4
--routine unified_moe --backends cutile --quant-variant mxfp4 --num_tokens 1024 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_mxfp4
--routine unified_moe --backends cutile --quant-variant mxfp4 --num_tokens 2048 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_mxfp4
--routine unified_moe --backends cutile --quant-variant mxfp4 --num_tokens 4096 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_mxfp4
--routine unified_moe --backends cutile --quant-variant mxfp4 --num_tokens 8192 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_mxfp4
--routine unified_moe --backends b12x cutile --quant-variant nvfp4 --num_tokens 1 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_nvfp4
--routine unified_moe --backends b12x cutile --quant-variant nvfp4 --num_tokens 2 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_nvfp4
--routine unified_moe --backends b12x cutile --quant-variant nvfp4 --num_tokens 4 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_nvfp4
--routine unified_moe --backends b12x cutile --quant-variant nvfp4 --num_tokens 8 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_nvfp4
--routine unified_moe --backends b12x cutile --quant-variant nvfp4 --num_tokens 16 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_nvfp4
--routine unified_moe --backends b12x cutile --quant-variant nvfp4 --num_tokens 32 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_nvfp4
--routine unified_moe --backends b12x cutile --quant-variant nvfp4 --num_tokens 64 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_nvfp4
--routine unified_moe --backends b12x cutile --quant-variant nvfp4 --num_tokens 128 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_nvfp4
--routine unified_moe --backends b12x cutile --quant-variant nvfp4 --num_tokens 256 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_nvfp4
--routine unified_moe --backends b12x cutile --quant-variant nvfp4 --num_tokens 512 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_nvfp4
--routine unified_moe --backends b12x cutile --quant-variant nvfp4 --num_tokens 1024 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_nvfp4
--routine unified_moe --backends b12x cutile --quant-variant nvfp4 --num_tokens 2048 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_nvfp4
--routine unified_moe --backends b12x cutile --quant-variant nvfp4 --num_tokens 4096 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_nvfp4
--routine unified_moe --backends b12x cutile --quant-variant nvfp4 --num_tokens 8192 --hidden_size 2688 --intermediate_size 1856 --num_experts 128 --top_k 6 --activation-type Relu2 --input_dtype bfloat16 --autotune --refcheck --num_iters 30 --dry_run_iters 5 -vv --generate_repro_command --case_tag nemotron_nvfp4
```

</details>


</details>

## 🔍 Related Issues

<!-- Link any related issues here -->

Progress towards #4857

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

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
  * Added cuTile support for MXFP4 and NVFP4 with BF16 activations.
  * Added W4A16 execution for supported FP4 configurations.
* Expanded MoE benchmark options with a…

### [c11c109](https://github.com/flashinfer-ai/flashinfer/commit/c11c1090172f578bad37b8bca2b40e4161d72144)

- **作者**: Brian K. Ryu
- **时间**: 2026-09-15T22:16:38Z
- **提交信息**: fix(topk): fall back to CUB for graph-safe page-table transforms on SM120 (#5226)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

Use CUB when `dsa_graph_safe=True` and native `FilteredTopK` cannot
support the device or requested `k`, bypassing the performance
heuristic. Preserve explicit backend overrides and raise a clear error
when neither backend supports the call.

## 🔍 Related Issues

<!-- Link any related issues here -->

Fixes #5058

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

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Improved graph-safe Top-K dispatch across standard, paged, and ragged
inputs.
* Graph-safe requests now select a supported execution path more
reliably and report a clear unsupported-operation error when none is
available.
* Preserved sorted-output behavior instead of silently falling back to
an incompatible path.
* Improved correctness during CUDA graph replay when scores, lengths, or
offsets change.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [35a3e97](https://github.com/flashinfer-ai/flashinfer/commit/35a3e9730f2f94bf2e890e2888d5c82cecd12d9f)

- **作者**: Ka-Hyun Nam
- **时间**: 2026-09-15T21:45:44Z
- **提交信息**: chore: add @jhjpark as CODEOWNER for GDN, Mamba, and KDA (#5247)

## Summary
- Add `@jhjpark` to the GDN, Mamba, and KDA CODEOWNERS rules (domain
expert on linear attention / cuDNN backend).
- Catch-all and other sections are unchanged.

## Test plan
- [ ] Confirm GitHub CODEOWNERS syntax check passes
- [ ] Confirm `@jhjpark` has write access on `flashinfer-ai/flashinfer`
so review requests apply (currently `read` as a collaborator; GitHub
ignores CODEOWNERS without write)

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Chores**
* Updated repository ownership assignments for GDN, MAMBA, and KDA
areas.
  * Added an additional code owner to the relevant review rules.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [43630b9](https://github.com/flashinfer-ai/flashinfer/commit/43630b93bcfdc22cf337e1979e0ea6d2b6be75a8)

- **作者**: Ka-Hyun Nam
- **时间**: 2026-09-15T21:17:07Z
- **提交信息**: fix(gdn): compile and tune CuTe-DSL decode kernels for the operand device (#4507)

## Summary

PR #2 of the GDN CuTe-DSL cache audit (#4214), covering **GDN-H2** and
**GDN-H3**: GDN decode compiled and tuned for whatever GPU is CUDA
device 0, not for the device the operands live on.

- **GDN-H2** — `gdn_decode_bf16_state.py` read SM count and compute
capability from device 0 at import time. Those drive the `tile_v` wave
heuristic and the `use_packed_fma` Constexpr, so operands elsewhere got
the wrong specialization. On a mixed L40S + H100 NVL box,
`_get_bf16_mtp_config(B=17, T=2, HV=32, V=128)` picks `tile_v=64` from
the L40S's 142 SMs but `tile_v=128` from the H100's 132.
- **GDN-H3** — every GDN `cute.compile` omitted an explicit target, so
the DSL resolved the arch from device 0, and the cubin was cached under
a key containing neither arch nor device.

## What this does

New `flashinfer/gdn_kernels/device_target.py` resolves one target per
device (arch, SM count, `use_packed_fma`, honoring `CUTE_DSL_ARCH`). The
GDN decode and Blackwell prefill compile sites now drive both their
compile options and their cache keys from that target, and launch
streams follow `q.device`.

Two constraints shaped it:

- Compile options had to move from the string form to option objects.
The DSL replaces subscripted options wholesale when a string `options=`
is present, so `cute.compile[(GPUArch(...),)](..., options="...")`
silently drops the arch.
- The target splits across two identities. The in-process key carries
`(device_index, arch)` because those entries also hold device-resident
default tensors that nothing else keys by device; the compiled artifact
itself is device agnostic from DSL 4.6.2 on. The on-disk artifact name
carries the arch alone — naming it by device would give every GPU its
own copy of every kernel and defeat the disk cache.

Pinning `GPUArch` does not by itself let one process serve another
device's architecture: the DSL builds a JIT engine only when its
process-global arch (`CUTE_DSL_ARCH`, else device 0) can run the
requested target. That case now raises an error naming
`CUTE_DSL_ARCH=<arch>` instead of a DSL internal error or a launch-time
`cudaErrorNoKernelImageForDevice`.

On homogeneous hardware this is a no-op: the arch suffix rule is the one
the DSL's own `detect_gpu_arch` uses, so the compiled arch string is
byte-identical to what it picked implicitly.

## Testing

B200 (`sm_100a`), `nvidia-cutlass-dsl==4.7.0`: full `tests/gdn/` — 3810
passed, 928 skipped, 13 failed, with all 13 reproducing on unmodified
main in the same environment (12 isolated-subprocess tests that import
`flashinfer` from the editable install; 1 disk-cache round trip that
never triggers a compile). Earlier run on the mixed L40S + H100 NVL box:
3760 passed, 984 skipped, 0 failed.

`tests/gdn/test_gdn_device_target.py` adds resolver coverage (requested
device, `CUTE_DSL_ARCH` override of arch *and* policy, rejection of a
target the DSL would cross-compile), two AST guards — compile sites must
pin the operand's target, and adopters must not read launch policy or
streams off the ambient device — and a multi-GPU bit-exactness test that
skips on a single-GPU box. The guards are mutation-checked: dropping the
arch from the options, the device from the key's consumers, or the
device from a stream or policy read each fails at least one.

Still to do before leaving draft: the multi-GPU test on a homogeneous
two-GPU box. Its bf16-state MTP arm is the one that can fail there,
since that cache value holds per-B index tensors the kernel
dereferences; both arms have been run single-device.

## Out of scope

- GDN-H4 staging / workspace ownership → #4476
- `delta_rule_dsl/` and `blackwell/gdn_cp_prefill.py` compile through
their own `cached_compile` shim (~20 sites). They do pin an arch, but
from a module constant rather than the operand's device, and their cache
is not keyed by device — the same GDN-H3 defect, left for a follow-up.
- `_get_compile_arch()` in `flashinfer/jit/cute_dsl_core.py` resolves
the disk cache's arch from the *current* device, which need not be the
operand's — the same defect one layer down. Harmless today only because
this PR puts the arch in the kernel name, so a mislabeled directory
cannot collide with a correctly labeled one.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **New Features**
- Added device-aware compilation for GDN kernels, automatically
selecting architecture-specific options and execution settings.
- Added support for cross-compilation architecture overrides with
validation.
- Improved kernel caching to distinguish device targets and
architectures while sharing compatible compiled artifacts.

- **Bug Fixes**
- Ensured kernels use the correct device-associated CUDA stream and
runtime properties.

- **Tests**
- Expanded coverage for device targeting, compilation options, cache
specialization, multi-device execution, and cross-device consistency.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [46c4c9f](https://github.com/flashinfer-ai/flashinfer/commit/46c4c9fb7bcb5b76f0ecb901717c78a5167a457a)

- **作者**: Xiaogang Zhou
- **时间**: 2026-09-15T21:12:55Z
- **提交信息**: fix(jit): refresh stale arch detection and allow SM120 on CUDA 12.8 (#3633)

## 📌 Description

This PR fixes two JIT architecture-detection issues on consumer
Blackwell (`SM120`) environments.

- Refresh `current_compilation_context` before `check_cuda_arch()` so
JIT does not rely on stale import-time arch state.
- Allow `SM120` on CUDA 12.8 in
`CompilationContext._normalize_cuda_arch()`, while keeping `SM121+`
gated on CUDA 12.9.
- Add regression tests for stale context refresh and `SM120` / `SM121`
normalization behavior.

This is needed because PyTorch could already detect an RTX 5090
(`SM120`), but FlashInfer JIT could still fail with a misleading `sm75`
error, and later with an overly strict `SM12.x requires CUDA >= 12.9`
check.

## 🔍 Related Issues

- Related to SM120 / consumer Blackwell JIT detection issues
- Reproduced on RTX 5090 (`SM120`) with a CUDA 12.8 toolkit environment

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [ ] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

> If you are unsure about how to set up `pre-commit`, see
`https://pre-commit.com/` .

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

Validated with:

```bash
python -m pytest tests/utils/test_jit_arch_detection.py -q -s
```

Result:

```text
5 passed in 0.03s
```

## Reviewer Notes

Main things to review:

- whether refreshing the shared JIT compilation context in
`check_cuda_arch()` is the right place to fix the stale-state issue
- whether allowing `SM120` on CUDA 12.8 in `_normalize_cuda_arch()` is
the right normalization policy


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Improved handling and reporting when CUDA device capability detection
fails, including more detailed CUDA availability information.
* Refreshed CUDA architecture detection to prevent stale results and
improved validation errors by listing detected architectures.
* Updated CUDA 12.x SM architecture normalization with explicit CUDA
12.8 and 12.9+ behavior and stricter requirements for SM 12.1+.

* **Tests**
* Added coverage for CUDA architecture detection, refresh behavior,
normalization edge cases, and error messaging.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: xiaogang.zhou <xiaogang.zhou@bytedance.com>
Co-authored-by: xiaogang.zhou <xiaogang.zhou@bytedance.com>
Co-authored-by: Brian K. Ryu <bryu@nvidia.com>

### [521bdd2](https://github.com/flashinfer-ai/flashinfer/commit/521bdd2f17742a095cf47c084f985ddb6f40760d)

- **作者**: Jonathan Dierksen
- **时间**: 2026-09-15T20:13:09Z
- **提交信息**: ci: cache checksum-verified cubin downloads (#5240)

<!-- .github/pull_request_template.md -->

## 📌 Description

Cache the raw cubin download tree used by the nightly `flashinfer-cubin`
wheel build so repeated runs do not issue roughly 42,757 Edge URM file
transfers when artifact pins are unchanged.

The downloader reuses only files whose SHA-256 matches the expected
manifest and downloads missing or corrupt entries. The workflow
preserves progress from failed downloads under unique immutable
partial-cache keys, restores the newest partial cache on the next run,
and promotes a successful tree to the stable content key.

## 🔍 Related Issues

Related operational context: recurring anonymous HTTP 403 responses from
Edge URM during nightly cubin downloads.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

> If you are unsure about how to set up `pre-commit`, see the
[pre-commit documentation](https://pre-commit.com/).

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

Validation:

- `python -m pytest tests/test_artifacts.py -q` — 9 passed in an
isolated Python 3.10 environment
- `pre-commit run --files .github/workflows/nightly-release.yml
flashinfer/artifacts.py tests/test_artifacts.py`
- workflow YAML parsed successfully
- `git diff --check`

A full live cubin-wheel build was not run locally because it would
repeat approximately 42,757 Edge URM transfers. The first successful
GitHub Actions run will seed and promote the cache; a failed run
followed by a retry is the required end-to-end validation of
partial-cache recovery.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **Performance**
- Reuses valid cached CUDA artifacts to reduce repeated downloads and
build times.
- Automatically re-downloads missing or corrupted files when checksums
do not match.

- **Reliability**
  - Detects and rejects artifacts with invalid checksums.
- Reports clear failures when cubin or header artifacts cannot be
retrieved, instead of silently returning incomplete results.
  - Improves cache recovery across nightly and standard releases.
- Cleans up temporary lock files after builds to support reliable
subsequent runs.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [24c30bd](https://github.com/flashinfer-ai/flashinfer/commit/24c30bddbe1628e225458380b476de756b506f69)

- **作者**: Harrison Zhang
- **时间**: 2026-09-15T11:28:12Z
- **提交信息**: feat(prims-ts): support QK-BF16/PV-FP8 in FMHA context (#4879)

<!-- .github/pull_request_template.md -->

## 📌 Description

Adds support for a differing PV dtype (e.g. QK-BF16/PV-FP8) in primsTS
context/prefill attention. Splits `qk_dtype`/`pv_dtype` through the
geometry, compile-spec, and kernel config, fixes TMA copy
granularity/SMEM descriptor/swizzle assumptions that previously derived
V's layout from Q/K's dtype, and gives K and V independent SMEM pipeline
configs since a shared TMA pipeline can't satisfy both dtypes'
byte-count wait conditions.

## 🔍 Related Issues

N/A

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

## Reviewer Notes

Scoped to `fmha_context` kernels only. Decode has not been modified in
this PR (but coming soon).

Tested on B300: 

**No performance regression for QKV-BF16 context case.**

[qkvbf16-perf-b300.md](https://github.com/user-attachments/files/32069254/qkvbf16-perf-b300.md)

**Average of 10-26% performance gain with QK-BF16/PV-FP8 quantization
over QKV-BF16 baseline.**
Certain configs lead to smaller gains: head_dim_256 and
page_size_128/page_size_64 (causal=False) at +3-8%
Largest gains cluster around chunked-prefill and large-batch configs at
+25-31%. Moreover, max abs error against FA2 is what we expect for
PV-FP8 quantization.

[qkbf16-pvfp8-perf-b300.md](https://github.com/user-attachments/files/32069275/qkbf16-pvfp8-perf-b300.md)

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

## New Features
- Context attention now supports separate data types for query/key and
value inputs.
- Added support for mixed BF16 query/key with FP8 value configurations.
- Added independent key and value processing for mixed-precision
attention workloads.
- Benchmarks now support selecting a separate value data type.

## Bug Fixes
- Improved validation for supported query/key and value-type
combinations.

## Documentation
- Updated usage guidance for mixed-dtype context attention and value
scaling.

## Tests
- Added coverage for packed and paged context attention with mixed
BF16/FP8 inputs.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [2694e1e](https://github.com/flashinfer-ai/flashinfer/commit/2694e1e025e8e5cb8d9117299027ebe816229a33)

- **作者**: Anerudhan Gopal
- **时间**: 2026-09-15T11:06:16Z
- **提交信息**: feat(prefill): let backend="auto" reach cuDNN/CUTLASS on Blackwell ragged prefill (up to 3.3x) (#5133)

<!-- .github/pull_request_template.md -->

## 📌 Description

On Blackwell, ragged prefill with `backend="auto"` resolves to **FA2
unconditionally**. `determine_attention_backend` can only answer `"fa3"`
or `"fa2"`, and FA3 is gated on `is_sm90a_supported()`, which is `False`
on SM100:

```python
>>> determine_attention_backend(cuda, NONE, False, False, bf16, bf16, head_dim_qk=128, head_dim_vo=128)
'fa2'
>>> is_sm90a_supported(cuda), is_sm100a_supported(cuda)
(False, True)
```

So `auto` misses not just cuDNN but *every* Blackwell-capable backend.
FA2 has no tcgen05 path and measures at ~320–390 TFLOPS, roughly 17% of
B200 bf16 peak.

This adds a post-resolution upgrade in
`BatchPrefillWithRaggedKVCacheWrapper.plan()`, modelled on the `fmha_v2`
SM120 precedent directly above it: `auto` tries cuDNN, then CUTLASS,
then stays on FA2. It is **not** implemented by teaching
`determine_attention_backend` a new answer — that function is shared
with decode, paged prefill and sparse, none of which accept `"cutlass"`,
so a new return value would have to be filtered back out at four other
call sites.

cuDNN is chosen only when the installed cuDNN can consume the caller's
**token-unit** indptrs directly, which keeps the caller contract
byte-identical to every other backend.

The final commit goes further and **normalizes the explicit
`backend="cudnn"` path to token-unit `qo_indptr` as well**, so every
backend in this wrapper now takes the same thing. That is a breaking
change for existing explicit-cuDNN callers, who previously passed
element-unit offsets (`cumsum(seq_lens) * num_qo_heads * head_dim_qk`);
the wrapper detects that shape and raises a message naming the new
convention rather than computing something wrong.
`benchmarks/routines/attention.py` and the three `test_cudnn_prefill*`
files are updated to match.

**The exclusions are load-bearing.** Both candidate run paths receive
only `causal` and the scales — never `window_left`, `logits_soft_cap`, a
custom mask, or the multi-item-scoring pointers. Upgrading while any of
those were requested would silently drop them and return quietly wrong
numbers, so each is an explicit disqualifier.

### Performance

All numbers below were re-taken on one standardised stack so the two
parts are comparable:
**CUDA 13.4**, **cuDNN frontend 1.29.0 / backend 9.26.0 (92600)**, bf16,
causal, ragged prefill,
median of 20 iterations after 5 warmup, via
`benchmarks/flashinfer_benchmark.py`.

- **B200** — cc 10.0, torch 2.14.0+cu130, nvidia-cutlass-dsl 4.7.1
- **B300 (GB300)** — cc 10.3, torch 2.13.0a0 (NGC container), same CUDA
13.4 / cuDNN 1.29 + 92600 overlay

Every backend is measured at every shape, so CUTLASS and cuDNN can be
compared directly rather
than only through `auto`'s pick. **Correctness:** all 16 shapes below
were re-run with
`--refcheck` and without `--allow_output_mismatch`; FA2 is the reference
and every cuDNN and
CUTLASS output matched it elementwise within tolerance (any difference
raises). `auto` was FA2 in **every** row before this PR, so the
"cudnn vs fa2" column is exactly what `auto` gains.

#### By head dimension

The `d192/128` and `d256/256` rows use GLM-5.3's attention shape: MLA
with
`qk_nope 192` + `qk_rope 64` → `qk_head_dim 256`, `v_head_dim 256`, **64
heads**.

| shape | fa2 | cutlass | cudnn | cudnn vs fa2 | `auto` picks |
|---|---|---|---|---|---|
| **B200 (cc 10.0)** | | | | | |
| b16 s4096 64×8 d128 | 12.277 ms | 5.752 | **4.006** | **3.06×** |
cudnn |
| b4 s16384 64×8 d128 | 46.763 | 19.647 | **17.170** | **2.72×** | cudnn
|
| b64 s1024 32×8 d128 | 1.776 | 1.440 | **0.733** | **2.42×** | cudnn |
| b16 s4096 64×64 d192/128 | 14.808 | 7.239 | **6.005** | **2.47×** |
cudnn |
| b64 s1024 64×64 d192/128 | 4.471 | 3.139 | **1.970** | **2.27×** |
cudnn |
| b16 s2048 64×64 **d256/256** | 7.016 | *declined* | **2.287** |
**3.07×** | cudnn |
| b8 s4096 64×64 **d256/256** | 13.346 | *declined* | **3.919** |
**3.41×** | cudnn |
| **B300 / GB300 (cc 10.3)** | | | | | |
| b16 s4096 64×8 d128 | 10.128 | 4.588 | **2.499** | **4.05×** | cudnn |
| b4 s16384 64×8 d128 | 38.942 | 12.892 | **9.443** | **4.12×** | cudnn
|
| b64 s1024 32×8 d128 | 1.477 | 1.251 | **0.480** | **3.08×** | cudnn |
| b16 s4096 64×64 d192/128 | 12.119 | 5.501 | **4.002** | **3.03×** |
cudnn |
| b64 s1024 64×64 d192/128 | 3.616 | 2.809 | **1.401** | **2.58×** |
cudnn |
| b16 s2048 64×64 **d256/256** | 5.950 | *declined* | **1.492** |
**3.99×** | cudnn |
| b8 s4096 64×64 **d256/256** | 11.357 | *declined* | **2.536** |
**4.48×** | cudnn |

`d256/256` is new coverage: CUTLASS rejects it outright (*"CUTLASS
backend requires head dimension
to be 128 or 192"*), so before this PR that shape had no Blackwell path
at all and ran on FA2.
The gains are consistently larger on B300 than on B200 — cuDNN scales
onto sm103 better than FA2 does.

#### GLM-5.3 attention across input / output sequence lengths

Same GLM-5.3 shape throughout (`d_qk 256`, `d_vo 256`, 64 heads, batch
4), sweeping the query
length (`s_qo`, the chunk being computed) against the context length
(`s_kv`). The first five rows
are square full prefill; the last four are chunked prefill, where a
short query chunk attends a
long cached context — the shape that actually dominates long-context
serving. CUTLASS declines
every row here on head dimension, so `auto`'s alternative is FA2 in all
nine.

| s_qo → s_kv | B200 fa2 | B200 cudnn | B200 speedup | B300 fa2 | B300
cudnn | B300 speedup |
|---|---|---|---|---|---|---|
| 1k → 1k | 0.669 ms | **0.192** | **3.49×** | 0.442 ms | **0.145** |
**3.05×** |
| 2k → 2k | 1.952 | **0.579** | **3.37×** | 1.540 | **0.396** |
**3.89×** |
| 4k → 4k | 6.827 | **1.954** | **3.49×** | 5.763 | **1.289** |
**4.47×** |
| 8k → 8k | 25.944 | **7.722** | **3.36×** | 22.202 | **4.661** |
**4.76×** |
| 16k → 16k | 101.536 | **33.264** | **3.05×** | 87.285 | **19.228** |
**4.54×** |
| 512 → 4k | 1.738 | **0.494** | **3.52×** | 1.401 | **0.323** |
**4.34×** |
| 1k → 8k | 6.257 | **1.755** | **3.56×** | 5.243 | **1.111** |
**4.72×** |
| 2k → 16k | 24.049 | **6.933** | **3.47×** | 20.534 | **4.127** |
**4.98×** |
| 512 → 32k | 12.882 | **3.885** | **3.32×** | 11.221 | **2.437** |
**4.60×** |

The speedup is flat in sequence length — **3.05–3.56× on B200 and
3.05–4.98× on B300** across a
64× span of context length — and does not decay in the chunked-prefill
rows. `auto` picks cuDNN
for all of them.

Repro:

```bash
python benchmarks/flashinfer_benchmark.py --routine BatchPrefillWithRaggedKVCacheWrapper \
  --backends fa2 cutlass cudnn --batch_size 4 --s_qo 2048 --s_kv 16384 \
  --num_qo_heads 64 --num_kv_heads 64 --head_dim_qk 256 --head_dim_vo 256 \
  --causal --q_dtype bfloat16 --kv_dtype bfloat16 --refcheck -vv
```

### Two caveats reviewers should weigh

**1. At d192/128 the cuDNN-first order is right on average but not
universally.** An earlier
revision of this PR ordered CUTLASS ahead of cuDNN at `(192, 128)` on
the strength of a single
configuration — b16/s4096 with **128×128** heads — where CUTLASS
measured ~10% faster over four
independent runs (14.11/14.88/14.71/14.16 ms vs
15.65/16.16/16.43/15.62). Sweeping the rest of
that cell on B200 showed the winner flips with sequence length and head
config, so a
`head_dim`-keyed override generalises one point to a space where it is
wrong more often than
right (medians, 30 iters after 10 warmup):

| config (d192/128) | cutlass | cudnn | winner |
|---|---|---|---|
| b4 s1024 128×128 | 0.334 ms | **0.265** | cudnn 1.26× |
| b16 s1024 128×128 | 1.257 | **1.030** | cudnn 1.22× |
| b64 s1024 128×128 | 5.764 | **4.178** | cudnn 1.38× |
| b8 s2048 32×8 | 0.509 | **0.383** | cudnn 1.33× |
| b8 s2048 64×8 | 0.969 | **0.716** | cudnn 1.35× |
| b1 s4096 128×128 | **0.738** | 0.816 | cutlass 1.11× |
| b16 s4096 128×128 | **14.061** | 15.818 | cutlass 1.12× |
| b4 s16384 128×128 | **49.555** | 68.782 | cutlass 1.39× |

cuDNN takes 5 of 8 — every short-sequence case and every GQA case;
CUTLASS leads only
long-sequence MHA. On **GLM-5.3's own 64×64 head config** cuDNN wins
d192/128 outright on both
parts (tables above). The override was therefore removed and the
measurements kept in a source
comment. Callers who *do* know their shape can pin the order with
`FLASHINFER_RAGGED_AUTO_BACKEND_ORDER=cutlass,cudnn`. A principled fix
needs a heuristic keyed on
the axes that actually discriminate (sequence length, MHA vs GQA),
measured per architecture;
that is deliberately not attempted here.

**2. The cuDNN path is silently inert on older cuDNN.**
`_cudnn_supports_direct_seqlens` requires
cuDNN **library** ≥ 9.24 for fp16/bf16. On a 9.19 runtime — the version
torch's
`nvidia-cudnn-cu12` pulled here by default — `auto` resolved to
`cutlass` at d128/d192 and **all
the way back to FA2 at d256**, and 8 of the new tests skipped. The same
measurement on 9.19 would
report CUTLASS numbers under a cuDNN label. The headline gains need a
9.24+ runtime.

### End-to-end impact

**Not measured, and deliberately not claimed.** Everything above is
per-op prefill attention.
Converting it to TTFT is Amdahl arithmetic over attention's share of
prefill, which varies widely
with model (dense vs MoE), sequence length and TP degree — at a 30%
attention share a 3.4× kernel
gives ~21% lower prefill time; at 10% it gives ~7%. No end-to-end
serving benchmark was run, so no
single number is quoted. The per-op measurements and the repro command
are what this PR stands on.

## 🔍 Related Issues

None.

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

All measurements above were re-taken on the final commit (after the
`qo_indptr` normalization, which also changed how
`benchmarks/routines/attention.py` feeds cuDNN) and then re-taken again
on the standardised CUDA 13.4 / cuDNN frontend 1.29 + backend 92600
stack described in Performance; they land within run-to-run noise of the
pre-normalization figures, confirming the change is a calling convention
and not a kernel change.

New `tests/attention/test_auto_backend_upgrade.py` — **22 passed, 0
skipped** on B200 with cuDNN 9.26. A new
`tests/attention/test_cudnn_prefill_token_indptr.py` covers the
normalized explicit-cuDNN contract, including the element-unit-offset
detection error. Covers the upgrade firing, every negative case (sliding
window, logits soft cap, out-of-domain head dims, HND layout), numerics
against FA2 over seeded byte-identical inputs, indptr preservation on
the auto-resolved cuDNN path, packed-LSE output, and that an explicit
`backend=` is never rewritten.

On a 9.19 runtime the same file is **13 passed, 8 skipped** — the skips
are the cuDNN cases, see caveat 2.

Existing ragged suite (`test_batch_prefill_with_ragged_kv_cache`,
`_custom_mask`, `test_ragged_prefill_one_valid_key`): **3278 passed, 180
skipped, 0 failed**.

A green regression run only means something if the changed code ran, so
the suite's own parametrization was replayed through `plan()` and the
resolutions counted: **192/1152 configs (16.7%)** leave FA2 — exactly
the `d=128 + pos_encoding=NONE` cell, with `d=64`, `d=256` and all
`ROPE_LLAMA` correctly staying on FA2 (measured on the CUTLASS-only
first commit; the second commit widens this to d256).

The selection tests deliberately stop at `plan()`: an HND `run()` would
fail on tensor shapes, so a naive test would "pass" while proving
nothing about which backend was picked.

## Reviewer Notes

- Worth a look at the `d192/128` ordering (caveat 1). An earlier
revision pinned CUTLASS first there; a wider sweep showed the winner
flips with sequence length and head config, so the override was removed
and `FLASHINFER_RAGGED_AUTO_BACKEND_ORDER` is the supported escape
hatch. The ordering is the judgement call most worth a second opinion.
- Environment note that cost me time: building from a bare worktree
needs `git submodule update --init` **and** the
`flashinfer/data/{csrc,include,cccl,cutlass,spdlog}` symlinks an
editable install creates. Without `data/cccl` specifically, nvcc
silently falls back to the CUDA toolkit's older libcu++ and
`fastdiv.cuh` fails with `"impl_" is not a nonstatic data member` — a
confusing error with an unrelated-looking cause.

AI-assisted (Claude Code); all measurements taken in-tree on the B200
described above.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added shape-aware automatic backend selection for Blackwell ragged
prefill.
* Added an environment variable override for ragged prefill backend
order.
* Added support for packed LSE shapes when batch offset statistics are
provided.
* Added validation and guidance for token-based offsets in cuDNN
prefill.

* **Bug Fixes**
* Improved cuDNN prefill offset handling and backend selection across
supported shapes.

* **Documentation**
  * Documented the new backend-order environment variable.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: Yang Xu <yanxu@nvidia.com>
Co-authored-by: Emil Gilliam <egilliam@nvidia.com>

### [ff8f8b1](https://github.com/flashinfer-ai/flashinfer/commit/ff8f8b1a97c4c26fabc1082c7b89633f164a68de)

- **作者**: Hiki
- **时间**: 2026-09-15T10:05:34Z
- **提交信息**: refactor(moe): update and refactor the SM90 CuTe-DSL MoE tactics (#5004)

<!-- .github/pull_request_template.md -->

## 📌 Description

Aligns the SM90 CuTe-DSL BF16 MoE backend's tactic, legality and tuning
layer with the SM100 CuTe-DSL MoE tuner convention, and re-measures it.

1. **One tactic tuple, one fixed default.** A tactic is `(tile_size,
((m, n), swizzle_size), ((m, n), cluster_shape_mn, raster_along_m))`,
one sub-tuple per GEMM. `cute_dsl_fused_moe_bf16` and
`CuteDslBf16MoEWrapper.run` take a single `tactic=` keyword (replacing
the per-axis `tile_size` / `gemm1_tile_n` / `gemm2_tile_n` /
`gemm2_tile_k` / cluster / raster keywords of #4878); `None` / `-1`
select the fixed default `(128, ((128, 64), 1), ((128, 64), (1, 1),
False))`.
2. **The kernels own legality.** Both Hopper kernels gain
`is_valid_tile_and_cluster_shape` and `can_implement(a_dtype, b_dtype,
c_dtype, tile_shape_mn, cluster_shape_mn, m, n, k, l)` classmethods
(SM100 signature, `m` = `permuted_m`). The wrappers reject a request the
kernel cannot run, and the tuner filters candidates through the same
predicate, so no tile rule is duplicated in Python.
3. **GEMM2 loses `tile_k`.** The K tile is four WGMMA K-steps (64
elements for 16-bit inputs, one SW128 atom) and a partial last K tile is
zero-filled by TMA on both operands, so the per-rank intermediate size
only has to keep 16 B rows (`I % 8 == 0` for bf16) instead of a multiple
of the K tile.
4. **The tuner enumerates every legal N tile of both GEMMs**, with the
GEMM1 persistent-walk swizzle (1/8/16) as a tuned axis, and prunes only
scheduling options that never won: swizzle on batches with fewer than
eight routed rows per expert or with >48 MiB of expert weights and >16
local experts, GEMM2 `(1,2)` multicast below per-rank `I = 192`, M-major
raster off the 128-row tile or above `I = 384`.
5. **Profiling uses realistic routing.** Tuning candidates are timed
under a seeded uniform top-k routing draw over the global experts
(distinct experts per token, real load imbalance) instead of a balanced
assignment. Balanced routing makes the 64-row tile look best at exactly
64 rows per expert; under real routing those winners were 15–20% slower
than the 128-row tile at 256–1024 tokens.

The design doc (`docs/design_docs/cute_dsl_moe_sm90.md`) §5 and §8 are
updated accordingly.

## 🔍 Related Issues

Follow-up to #4878 (SM90 CuTe-DSL BF16 MoE backend).

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

## Performance

### Setup

Measured on **H200 (141 GB HBM3e)** with the protocol of #4878, both
backends freshly autotuned:

- Both backends run through `benchmarks/flashinfer_benchmark.py`
(`cute_dsl_bf16_moe` vs `cutlass_fused_moe`, `base` BF16 variant) on
identical tensors and routing, e.g.:

  ```
python benchmarks/flashinfer_benchmark.py --routine cute_dsl_bf16_moe \
      --num_tokens 256 --hidden_size 4096 --intermediate_size 14336 \
      --num_experts 8 --top_k 2 --input_dtype bfloat16 \
      --use_cupti --num_iters 50 --dry_run_iters 10 \
      --autotune_cache tune.json
  ```

- Each backend is autotuned once per suite (winners stored via
`--autotune_cache`); all measured rounds replay the stored tactics with
autotune disabled, and run only after every tune leg on the node has
finished (concurrent JIT/tactic compiles inflate long-kernel timings
~10% without raising the between-round CV).
- Per-round value = median of 50 CUPTI timings after 10 dry runs, cold
L2 before every timing, CUDA-graph replayed; cell = median of three
alternating backend-pair rounds (AB/BA/AB); reported only when
between-round CV ≤ 5% on both backends.
- Workloads: routed-expert geometries from the models' published
configs, TP ∈ {1, 4}, unexpanded token counts T ∈ {1, 256, 1024, 4096,
16384}.

### Result

Over the 70 cells (all publishable), the geo-mean speedup over
`cutlass_fused_moe` goes from **1.16x on main (#4878) to 1.19x**.
CuTe-DSL is faster in **62** cells, at 1.00x in 5 and slower in 3.
Per-model geo-mean ranges from 1.06x (Mixtral-8x7B) to 1.41x
(Qwen3-30B-A3B, Qwen3-Next-80B-A3B); the best cell is 2.34x
(Qwen3-Next-80B-A3B TP4, T=1). Column geo-means: T=1 1.38x, T=256 1.05x,
T=1024 1.12x, T=4096 1.16x, T=16384 1.26x. Values > 1 mean CuTe-DSL is
faster:

| model (h / I global / E / top_k) | tp -> I/rank | T=1 | 256 | 1024 |
4096 | 16384 |
|---|---|---|---|---|---|---|
| Qwen3-30B-A3B (2048/768/128/8) | 1 -> 768 | 1.39x | 1.02x | 1.15x |
1.25x | 1.27x |
| | 4 -> 192 | 1.88x | 1.25x | 1.51x | 1.76x | 1.90x |
| Qwen3-235B-A22B (4096/1536/128/8) | 1 -> 1536 | 1.11x | 1.00x | 1.08x
| 1.09x | 1.14x |
| | 4 -> 384 | 1.50x | 1.05x | 1.26x | 1.25x | 1.43x |
| Qwen3-Next-80B-A3B (2048/512/512/10) | 1 -> 512 | 1.71x | 0.99x |
1.04x | 1.18x | 1.33x |
| | 4 -> 128 | 2.34x | 1.17x | 1.26x | 1.72x | 1.82x |
| GLM-4.5-Air (4096/1408/128/8) | 1 -> 1408 | 1.14x | 1.00x | 1.06x |
1.08x | 1.16x |
| | 4 -> 352 | 1.54x | 1.09x | 1.15x | 1.10x | 1.07x |
| Kimi-K2 (7168/2048/384/8) | 1 -> 2048 | 1.08x | 1.00x | 1.03x | 1.02x
| 1.22x |
| | 4 -> 512 | 1.47x | 1.01x | 1.05x | 1.13x | 1.23x |
| DeepSeek-V3 (7168/2048/256/8) | 1 -> 2048 | 1.08x | 1.00x | 1.04x |
0.90x | 1.10x |
| | 4 -> 512 | 1.33x | 1.02x | 1.10x | 1.02x | 1.16x |
| Mixtral-8x7B (4096/14336/8/2) | 1 -> 14336 | 1.06x | 1.06x | 0.95x |
1.00x | 1.06x |
| | 4 -> 3584 | 1.19x | 1.11x | 1.08x | 1.05x | 1.07x |

The three losses are DeepSeek-V3 TP1 T=4096 (0.90x), Mixtral-8x7B TP1
T=1024 (0.95x) and Qwen3-Next-80B-A3B TP1 T=256 (0.99x). Between-round
CV: CuTe-DSL median 0.17%, p95 2.20%, max 2.88%; CUTLASS median 0.15%,
p95 2.16%, max 4.65%.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

## Reviewer Notes

- API change vs #4878: the per-axis tactic keywords are replaced by one
`tactic=` tuple on `cute_dsl_fused_moe_bf16` and
`CuteDslBf16MoEWrapper.run`. Old autotune caches are rejected at the
first dispatch with a `ValueError` naming the expected structure.
- Behavior change: the finalize kernel accepts `tile_n % 32 == 0` only
(was `% 8`).
- The kernel bodies are unchanged apart from the `tile_k` removal; the
diff in the two kernel files is the `can_implement` /
`is_valid_tile_and_cluster_shape` block plus the constructor check.
- No per-call `validate_tactic`, matching `tuner.py`: a persisted winner
of another schema fails at its first dispatch with a `ValueError` naming
the expected structure (the API has not shipped in a release, so no
cache migration is needed). Candidate lists depend only on the problem
shapes and the global expert count, so expert-parallel ranks tuning
under `set_autotune_process_group` profile identical sequences.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **New Features**
- Added configurable persistent-walk swizzling for SM90 fused MoE
workloads.
  - Consolidated tuning options into a single tactic configuration.
- Improved automatic tactic selection based on workload characteristics
and hardware feasibility.

- **Bug Fixes**
- Added clearer validation and error reporting for unsupported
configurations.
- Improved consistency of tactic selection across expert-parallel
execution.
  - Standardized grouped-GEMM K-tile handling.

- **Documentation**
  - Updated SM90 MoE tactic guidance and benchmark results.

- **Tests**
- Added coverage for swizzled grouped-GEMM correctness, invalid
configurations, and partial K-tail workloads.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Haobin Guo <haobing@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [dd69038](https://github.com/flashinfer-ai/flashinfer/commit/dd690389da0e15ccda1a0ee65bb04ef76b5db569)

- **作者**: eigen
- **时间**: 2026-09-15T09:54:24Z
- **提交信息**: fix: restore default GDN prefill dispatch to CuTe (#5225)

Restore the established CuTe implementation for default GDN prefill
calls on Blackwell. Previously, `backend="auto"` could select a slower
exported kernel solely because a compiled specialization matched. One
affected case uses BF16 inputs, batch 4, sequence length 2048, Q/K/V
heads 16/16/32, head size 128, zero initial state and FP32 final state.

With this change, omitting `backend` or requesting `auto` follows the
same architecture and context-parallel dispatch as
`backend="flashinfer"`. Exported prefill kernels remain available
through explicit `backend="cake_gdn"`, with the existing
unsupported-input errors. Decode dispatch is unchanged.

Validation on B200:

- Both new CUDA Graph regression tests pass, covering the affected long
prefill shape and a short context-parallel shape. They compare actual
GPU kernel launches and bit-exact output/final-state values for default,
explicit `auto`, and `flashinfer` calls.
- Same-fixture, same-process CUDA Graph/CUPTI measurements: default
latency decreases from **0.117088 / 0.117087 ms** to **0.075743 /
0.075776 ms** in two repetitions. The measurements use 100 warmups and
101 samples per arm; they are standalone measurements, not scheduled CI
results.
- Targeted pre-commit checks pass.

Two independent repetitions of the original `flashinfer_benchmark.py`
command also pass refcheck and the 0.0768 ms acceptance threshold:
**0.075840 / 0.075904 ms**, with the official default 5 warmups and 30
CUPTI samples, CUDA Graph enabled. These are standalone B200 runs, not
normal scheduled CI results. The two benchmark processes took 19 seconds
combined; their managed validation step took 103 seconds including
container startup.

Pre-commit and documentation CI checks pass; the broader PR test
workflow is still running.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Updated automatic backend selection to consistently use FlashInfer
kernels on supported hardware.
* Prevented automatic fallback to Cake GDN when FlashInfer dispatch is
unavailable.
* Cake GDN now runs only when explicitly selected; unsupported inputs
report an error.

* **Tests**
* Added coverage verifying that automatic and default backend selection
match explicit FlashInfer behavior, including CUDA graph execution and
output consistency.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [cd4a9b0](https://github.com/flashinfer-ai/flashinfer/commit/cd4a9b0f76fb5ded46a67ec6cebb3dc31595370e)

- **作者**: Haoran FENG
- **时间**: 2026-09-15T09:16:58Z
- **提交信息**: fix(ci): support installed BF16 rank-major session tests (#5171)

<!-- .github/pull_request_template.md -->

## 📌 Description

Fix the BF16 rank-major MoE EP CPU contract tests so they work in
Nightly Release package-test isolation.

The tests previously loaded `session.py` from a path derived from the
copied test file. Nightly intentionally copies only `tests/` and
`pytest.ini`, so that source-tree path does not exist. Resolve the
installed file through `flashinfer-python` distribution metadata without
importing the FlashInfer package tree, preserving the optional
CUDA-driver import contract. Keep the source-tree path as the fast path.

The `pyproject.toml` package-data assertion remains active in
source-tree CI and is skipped only when that repository-only file is
absent from the isolated installed-package layout.

## 🔍 Related Issues

Fixes https://github.com/flashinfer-ai/flashinfer/issues/5162

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

Validation performed:

- Source-tree full file: `40 passed`.
- Isolated Nightly layout with installed-distribution staging: `39
passed, 1 skipped`; the skip is the source-only `pyproject.toml`
assertion.
- `python -m py_compile
tests/moe_ep/test_bf16_rank_major_cuda_session_cpu.py`.
- `git diff --check`.

The available GPU validation environment did not contain `pre-commit`;
the public pre-commit CI job remains the formatting check.

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

The distribution-metadata lookup is deliberate:
`importlib.resources.files()` imports the parent `flashinfer` package
and caused `cuda.bindings.driver` to load during this CPU-only contract
test. `Distribution.locate_file()` finds the unpacked wheel resource
without importing the package.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

- **Tests**
- Improved test coverage and reliability when running from either a
source checkout or an installed package.
- Updated validation to use the correct session implementation in each
environment.
- Adjusted package-specific checks to avoid false failures when testing
installed distributions.

- **User Impact**
  - No changes to product functionality or user-facing behavior.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: zhaoye <yzhao04@iquestlab.com>
Co-authored-by: Cindy Zhang <cindyz@nvidia.com>

### [e9a1ce4](https://github.com/flashinfer-ai/flashinfer/commit/e9a1ce40888284d45f61c8654f68b95887e7224c)

- **作者**: Yang Xu
- **时间**: 2026-09-15T07:04:03Z
- **提交信息**: feat: add low-latency Frost DSv4.1 sparse MLA decode (#5119)

<!-- .github/pull_request_template.md -->

## 📌 Description

The sink normalization also handles very large finite FP32 logits
safely: split merge and the non-split epilogue share a helper that
stabilizes `sink - real-key LSE` in natural-log space before base
conversion. It uses the stable log-sigmoid expression with nonpositive
exponential arguments, preventing NaNs from an overflowing `sink *
LOG2_E`. The public LSE remains sink-exclusive, and empty rows retain
zero output and `-inf` LSE.

The E8M0 correctness fix handles E8M0 scale code `0` as `2^-127` instead
of zero. This prevents silently zeroed KV values and incorrect
output/LSE for legal finite MXFP8 cache entries. The fix changes only
the shared scale decoder; API, scheduling and numerical tolerances
remain unchanged. New tests cover analytical changed-input graph replay
across the three decode schedules and bitwise conversion checks across
all finite scale encodings.

Adds an experimental **Frost** DS4.1 mixed-cache decode entry point with
reusable CUDA Graph plans and one CuTe DSL implementation using
`cutlass.experimental.primitives`. It gathers MXFP8 sliding-window KV
and FP4 compressed KV directly, decodes to BF16, and applies the
per-head attention sink. Window-only decode uses the same kernel family.

This is **adapted from Mengyu Guo's CuTe DSL HCA (#3943/#4368)**, with
his original attribution and license retained. The DS4.1 port adds mixed
quantized-cache gathers, the H64 single-CTA schedule, primitives-based
hardware operations, split/merge tuning and sink semantics. **FlashMLA
is an important design reference**: its SM100 head64 resource budget,
deferred softmax rescaling, WS QK/PV layouts with partial-score
exchange, fused softmax/correction and shared-memory/TMA output informed
this implementation. These contributions are explicitly acknowledged in
the source and example documentation.

`deepseek_v41_decode` and its window-only convenience entry point
prepare and reuse output/LSE/workspace through the same CuTe backend.
There is no decode backend selector or external provider dependency. The
only additional API is an **optional `deepseek_v41_quantize_cache`
helper**, narrowed from #5117's Triton quantizer to the two D512/page64
cache formats consumed here. It fuses quantization with cache writing,
including caller-owned `out`/`slots` for incremental updates. Decode
accepts compatible cache bytes from any producer and never calls this
helper. Callers supply model-appropriate RoPE and physical slot IDs.
General quantization, GEMM activation quantization, paging, RoPE and
index-cache APIs are outside this PR.

Initial scope: **SM100, contiguous BF16 `[B,1,64,512]` Q, 64-token
pages, 128 MXFP8 window slots and up to 512 FP4 compressed slots**.
Probabilities use BF16; accumulation and softmax use FP32. Output is
BF16 and public LSE is natural-log and sink-exclusive. Invalid physical
slots are masked without reading cache data. Empty rows produce zero
output and `-inf` LSE. Plans reject declaration drift and aliasing;
prepared plans support allocation-free graph replay and must not execute
concurrently on multiple streams.

This update improves large-batch mainloop and output efficiency while
retaining the measured low-latency split schedule for small batches.
K512/B128+ selects WS QK/PV and fused softmax/correction. Q occupies
TMEM, and the two partial score matrices are combined before softmax.
Each 64-key tile uses 16 QK plus 8 PV MMA issues instead of 32 plus 16.
P uses INTER layout. The output epilogue overlaps TMA stores with
subsequent TMEM reads, reusing the Q shared tile. Above one SM wave,
persistent CTAs distribute requests across a balanced grid; a boundary
barrier protects shared-memory/index reuse between requests. The grid
and physical SM count are included in the JIT key. These schedules share
the kernel class, cache conversion, pipelines, masks and split
reduction. The implementation retains only its supported single-CTA
primitives paths: inherited dual-CTA/DSMEM and non-primitives branches,
unused support/split/workspace helpers, diagnostic modes and the
unreachable WS split-output fallback have been removed. The
native-conversion fallback remains. The optional cache writer retains
only the main FP4 and window MXFP8 paths. WS raw KV vectors use public
`.cg` loads to bypass L1, while scale loads and the small-batch schedule
retain the default cache policy. The numerical algorithm is unchanged.
Persistent dequant warps now prefetch the next request's indices and
compute its data/scale offsets in registers while the current request
finishes. The existing all-role boundary barrier still protects
publication into shared metadata. Gather warps reuse these offsets,
avoiding repeated per-lane page arithmetic. For persistent CTAs, when
both complete cache pools are below 32 GiB, these offsets use signed
Int32 metadata in 16-byte units. Loads widen to Int64 before
reconstructing byte addresses. Larger pools retain Int64 byte offsets;
the complete-pool bound and private JIT specialization preserve
wide-address support. Unsigned page masks also avoid signed division
fixups. Nonpersistent CTAs retain the original slot representation.

Historical measurements before the E8M0 correction: **decode+merge GPU
latency in microseconds**, local device reported as **NVIDIA Graphics
Device, SM100, 148 SMs** (not identified as B200). H64/Sq1/D512, 128
window slots plus 512 selected compressed slots from a private 32K-token
pool per request. All arms pass the original independent FP64 gate
before timing. Warm CUDA Graph/event timing uses 32 invocations per
replay, symmetric order and 30 samples per arm; quantization,
preparation, JIT, capture and CPU overhead are excluded.

| Per-rank B | Before compact metadata (`3412b7b4`) | Frost (CuTe DSL
primitives) | FlashMLA |
|---:|---:|---:|---:|
| 1 | 11.89 | 11.72 | 21.56 |
| 4 | 12.35 | 12.39 | 21.63 |
| 32 | 18.04 | 18.06 | 22.32 |
| 128 | 22.70 | 22.64 | 24.09 |
| 149 | 41.09 | 41.22 | 45.10 |
| 256 | 59.24 | 58.01 | 62.76 |
| 512 | 119.20 | 117.18 | 127.41 |

Seed 11023, measured through the public API at `b53fc738` against the
frozen decoder at `3412b7b4`. Compact metadata and unsigned page
arithmetic reduce latency by **2.1% at B256 and 1.7% at B512** in this
pair. Two earlier candidate pairs measured reductions of 2.4–2.6% and
1.6–1.8%, respectively. B149 covers unequal request counts across
persistent CTAs and shows no consistent gain. The final B1 machine
instructions and control words are identical to the frozen decoder after
normalizing generated symbol names; small timing differences should not
be interpreted as changes to that schedule.

An independent public-API repeat with seed 10031, using the same GPU and
protocol:

| Per-rank B | Before (`3412b7b4`) | Frost | FlashMLA |
|---:|---:|---:|---:|
| 149 | 40.50 | 40.70 | 44.43 |
| 256 | 57.55 | 56.03 | 61.18 |
| 512 | 118.25 | 116.59 | 126.28 |

Across the two public-API pairs, B256 improves by 2.1–2.6% and B512 by
1.4–1.7%; B149 is 0.3–0.5% slower. Absolute times vary between runs, so
improvements are assessed within each paired run. Compared with the
external FlashMLA provider, the seed-11023 run has **7.6% lower latency
at B256 and 8.0% lower latency at B512**. Margins depend on inputs and
the device. These component measurements do not establish model token
latency, throughput or checkpoint accuracy.

The PR contains only Frost decode and its minimal optional cache writer,
across 12 files. The cache writer occupies 145 implementation lines. Its
purpose is to provide the exact cache layout and a self-contained
example; **no competitive-performance claim is made for it**. Negative
or out-of-capacity update slots are masked in the kernel. Valid slots
must be unique, an explicit caller precondition rather than an implicit
duplicate-validation pass. Current before/after checks use the
same-format writer from `3ad633ed`, not a serving-provider baseline:

| BF16 D512 rows, contiguous write | Main FP4 before / current (us) |
Window MXFP8 before / current (us) |
|---:|---:|---:|
| 1 | 3.12 / 2.99 | 1.08 / 1.06 |
| 128 | 1.98 / 1.94 | 1.27 / 1.27 |
| 512 | 2.03 / 1.97 | 1.33 / 1.32 |
| 32768 | 17.91 / 17.90 | 9.32 / 8.82 |

Same SM100 device, warm CUDA Graph/event timing with preallocated
outputs, 32 calls per graph and 30 symmetric samples per arm. Every
measured case passes exact-byte reference checks before timing,
including changed-input and poisoned-output graph replay. These are
contiguous helper-write measurements, not scatter-update timings or
comparisons with fused serving preprocessing. The cache helper is
optional and its latency is separate from decode.

The existing deferred-rescaling threshold, packed FP4 conversion and
numerical gates remain unchanged. Native conversion is selected from the
bundled compiler version (CUDA >= 13.2); older bundled compilers retain
the previous conversion sequence. Small public `prims.inline_ptx`
helpers cover packed conversion and WS MMA because CUTLASS DSL 4.7 lacks
the conversion wrapper and its typed WS wrapper forwards an unsupported
operand. Other MMA/TMEM/memory operations use public primitives.

The historical pre-correction B256 Nsight Compute profile records **zero
local/shared register-spill requests**, 80 launch registers per thread
and 225,280 bytes of dynamic shared memory, down 5,120 bytes from the
previous decoder. Executed warp instructions decrease from 15,256,576 to
14,410,752 (5.5%). Residency remains one CTA per SM; scalar exchange
lifetimes remain protected. The profile uses 128 CTAs of 768 threads;
profiler replay timings are separate from the warm-graph table.

Reproduce Frost/FlashMLA measurements with `python
benchmarks/bench_deepseek_v41_decode.py --batches 1,4,32,128,149,256,512
--context 32768 --seed 11023 --flashmla --output paired.json`. Omit
`--flashmla` to run without that optional external dependency. The
before arm is the Frost decoder at `3412b7b4`; use seed 10031 and
batches 149,256,512 for the independent repeat. See
`examples/deepseek_v41/README.md` for the API and numerical contract.

## 🔍 Related Issues

Tracks #5115. This PR is self-contained and does not require the other
DS4.1 draft PRs to merge.

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
- [ ] All tests are passing (`unittest`, etc.).

## 🔬 Experimental Track

<!-- Only for PRs submitted under the experimental policy
(CONTRIBUTING.md → "Experimental APIs and Backends").
     Leave this section untouched for normal PRs. -->

- [x] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.
Tracking issue: #5115
- [x] The tracking issue names an owner, the reason for the experimental
path, and a graduation plan with a target release.
- [x] Core changes are limited to a thin entry point (signature, shared
validation, feature-gate check, backend selection, handoff).
- [x] Tests live in `tests/experimental/` and were validated on the
intended hardware; a runnable example is included.
- [x] Nothing is registered in `flashinfer/aot.py`, and no experimental
backend is reachable from `backend="auto"` without
`FLASHINFER_ALLOW_EXPERIMENTAL_AUTO_BACKENDS=1`. (Calling an
`@flashinfer_experimental_api` or naming a backend explicitly is itself
the opt-in and needs no environment variable.)
- [x] **Test scope declared below.** The experimental CI lane runs
exactly these targets, so keep them as narrow as the change allows.

<!-- Required for experimental PRs. Replace the commented lines below
with your targets.
Do not delete the fence or change its `experimental-tests` tag — the
experimental-track
watcher reads it verbatim to decide which targets to ask CI for. -->

```experimental-tests
tests/experimental/test_deepseek_v41_decode.py
tests/experimental/test_deepseek_v41_cache.py
```

## Reviewer Notes

The latest sink-normalization fix passes **68 scoped tests with zero
skips** (46 decode and 22 cache). All 46 decode cases pass memcheck and
synccheck with zero errors. All six new sink-overflow regressions pass
racecheck with zero errors, warnings or hazards; these six cases fail
with NaN output on the pre-fix implementation. They cover FP32 extrema
and conversion-overflow boundaries, ordinary and disabled sinks,
changed-Q/sink graph replay, and empty rows across split, non-split and
persistent schedules. The numerical gates are unchanged, and pre-commit
hooks are installed and `pre-commit run --all-files` passes on the
branch refreshed from main.

The preceding E8M0 correction passed **62 scoped tests with zero skips**
(40 decode and 22 cache). All 40 decode tests pass memcheck and
synccheck. All 10 new regressions pass racecheck with zero errors,
warnings or hazards. The frozen pre-fix implementation fails the three
scale-zero decode regressions and exhaustive MXFP8 conversion test; six
control cases pass. With the correction, all ten pass. Pre-commit hooks
are installed and `pre-commit run --all-files` passes on the branch
refreshed from main.

The benchmark tables, profiler data and earlier validation details
describe earlier revisions and are retained as historical evidence; they
are not new measurements of the E8M0 correction. New device-specific
timing data remains in the local review report.

Validated with PyTorch 2.13.0+cu130, CUTLASS DSL 4.7 and system CUDA
13.2 on the SM100 device named above. CuTe compilation uses its
**bundled CUDA 13.3 compiler**, independently of `CUDA_HOME`. The
optional cache writer uses **Triton 3.7.1 and its bundled Blackwell
ptxas CUDA 13.1.80**. These tested versions do not add a package-wide
CUDA-major requirement.

Ordinary plan calls may change input addresses with matching
declarations. A captured graph retains its recorded pointers: buffers
stay alive and values change in place; new addresses require recapture
or an appropriate graph update. The FlashMLA comparison uses the
[upstream lazy FlashMLASchedMeta
API](https://github.com/deepseek-ai/FlashMLA/blob/main/flash_mla/flash_mla_interface.py):
`get_mla_metadata()` accepts no arguments, and the first eager
correctness call initializes metadata from the fixture before capture.
The unmodified shipped benchmark was directly rechecked at B1/B128 with
private 32K context and passed the FP64 gate and timing; the
Frost-labeled benchmark also passed.

Before the E8M0 regressions were added, the dedicated decode suite
passed **30 tests, zero skips**, including unequal request counts at
B=SM-count+1, B512's four requests per persistent CTA and B256
normalization-anchor crossings with different consecutive requests.
Coverage includes split/unsplit, mixed/window-only, invalid/all-masked
slots, dominating/disabled sinks, offsets above 2 GiB, both cache
formats just below and above the 32-GiB compact-metadata boundary,
independent FP64 output/LSE, changed Q/cache/indices/sinks under
nondefault-stream graph replay, poisoned outputs, corruption negative
controls, plan reuse and declaration/alias rejection.
Normalization-anchor crossings, conversion fallback and exhaustive
packed native-conversion cases remain covered. The four
capacity-boundary cases allocate real large pools, read initialized
tails against independent small-pool oracles, and replay changed
Q/indices with poisoned outputs. They skip if insufficient free device
memory is available; all four ran on this device. The unchanged
numerical gates are relative-L2 < 0.005, max-scaled < 0.01 and absolute
LSE error < 1e-5.

Historical CUDA 13.2 compute-sanitizer validation: all **30 decode tests
pass memcheck and synccheck**, zero errors. Unfiltered racecheck passes
seven hash-verified FP64 fixtures: B1/B16/B64 split, B128 unsplit,
persistent B256/B512, and persistent B256 with cache byte offsets above
2 GiB; **zero errors, warnings or hazards**. A separate public-API
racecheck exercises changed Q/cache/indices/sinks and nondefault-stream
graph replay at B=SM-count+1. The next request's metadata stays in
registers until the existing all-role boundary barrier completes. The
full `pre-commit run --all-files` check passes, including mypy and Ruff;
the pre-commit checklist is complete.

The earlier scoped suite recorded **52 passed, zero skips**: 30 decode
cases and 22 cache-writer cases. The cache suite covers exact FP4/MXFP8
bytes, RNE halfway cases and signed zero, partial pages,
changed-input/slot graph replay, poisoned output and corruption negative
controls, untouched slots, offsets above 2 GiB, declaration/alias
rejection and feeding the produced caches into the FP64-gated decoder.
All **22 cache tests pass memcheck**, including negative/out-of-capacity
slot masking and changed-input graph replay. Racecheck passes **20 cache
cases**, zero errors or hazards; the two wide-address cases are covered
by memcheck. The self-contained decode example runs successfully.

API/CI/integration review and target B200 validation remain outstanding.
SM103, multi-token/MTP, training and model E2E have not been validated.
Non-SM100 runners skip the decode suite; a skip is not target-hardware
correctness evidence. No experimental backend is added to AOT or
automatic dispatch.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **New Features**
- Added experimental DeepSeek V4.1 decoding for SM100/Blackwell GPUs
with reusable plans and CUDA Graph support.
- Added FP4 and MXFP8 cache quantization with optional slot-based
placement.
  - Added runnable decoding examples and performance benchmarks.

- **Bug Fixes**
  - Invalid cache slots are safely ignored.
- Improved validation for unsupported inputs, overlapping buffers, and
cache configurations.

- **Documentation**
- Expanded guidance for cache formats, CUDA Graph replay, toolchain
requirements, and FlashMLA metadata.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-09-16
**监控日期**: 2026-09-15
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4397
- **最后更新**: 2026-09-16T00:03:18Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 3
- **主要提交者**: Raghav K, William Lin, li-lizhe

## AI分析总结

# FastVideo 昨日提交分析（3 条）

## 1. 主要更新类型
- **功能新增（feat）**：支持 FastH3 8-Step V2 checkpoint，含 checkpoint 定义的 shift、显式 DMD 调度与新示例。
- **Bug 修复（bugfix）**：修复 Cosmos 中 AdaLayerNorm 的 autocast 设备兼容问题。
- **CI/测试改进（ci）**：将 Dreamverse provider race test 改为确定性测试。

## 2. 关键变更点与项目方向
- FastH3 8-Step V2 的引入，延续了 FastVideo 追求**少步数、高吞吐视频生成**的核心目标。checkpoint 自定义 shift 与显式 DMD（分布匹配蒸馏）调度，说明项目正把蒸馏/加速策略从硬编码转向**配置驱动**，便于快速接入新模型。
- Cosmos AdaLayerNorm 的设备无关修复，体现项目对**多后端、多硬件（CUDA/CPU/其他）** 兼容性的持续打磨。
- CI 测试确定性化，反映项目在快速迭代中仍重视**回归稳定性**，避免 flaky test 干扰开发节奏。

## 3. 对项目的影响与潜在意义
- 新 checkpoint 支持直接扩展了可用模型矩阵，用户可开箱体验 8 步推理，降低显存与延迟门槛，利好 Quick Start 与 Cookbook 场景。
- 设备无关的 autocast 修复减少了跨平台报错，提升框架鲁棒性，对部署到异构环境有实际价值。
- 确定性 CI 降低维护成本，为后续高频 PR 合并提供更可靠的守门机制。

## 4. 值得关注的技术点
- **checkpoint 定义的 shift**：把采样偏移参数交给权重文件描述，是解耦模型与推理逻辑的设计信号。
- **显式 DMD 调度**：蒸馏调度从隐式变为显式，利于调参与复现。
- **autocast 设备无关**：避免硬编码 device，是跨设备推理的通用最佳实践。

## 5. 结合 README 的项目发展意义
FastVideo 定位为高效视频生成框架，强调快速推理与易用文档。本次提交一方面通过 FastH3 V2 强化“**快**”的核心卖点（8 步生成），另一方面通过 Cosmos 修复与 CI 稳定化夯实工程基础。整体看，项目正从“能跑”走向“**稳定、可配置、跨平台**”，符合其面向社区推广（Slack、Cookbook、Weekly Meeting）的开放协作路线。

## 详细提交记录

### [9b0e57f](https://github.com/hao-ai-lab/FastVideo/commit/9b0e57fe4b3a8c112ff24cc22f752eb0608ccfab)

- **作者**: Raghav K
- **时间**: 2026-09-15T21:13:56Z
- **提交信息**: [ci] Make Dreamverse provider race test deterministic (#1729)

### [0100218](https://github.com/hao-ai-lab/FastVideo/commit/01002185948f9318b8da9067896b61c96bf9a2bd)

- **作者**: William Lin
- **时间**: 2026-09-15T21:13:45Z
- **提交信息**: [feat] Support the FastH3 8-Step V2 checkpoint: checkpoint-defined shifts, explicit DMD schedule, new example (#1852)

### [39718cd](https://github.com/hao-ai-lab/FastVideo/commit/39718cd54d74e3ae869a18772ff5a24fb7920606)

- **作者**: li-lizhe
- **时间**: 2026-09-15T14:44:51Z
- **提交信息**: [bugfix] fix(cosmos): make AdaLayerNorm autocast device-agnostic (#1818)

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-09-16
**监控日期**: 2026-09-15
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34527
- **最后更新**: 2026-09-15T20:15:06Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Sayak Paul

## AI分析总结

# 提交分析：d77d530 [torchao] 修复 FqnConfig 的解析与处理

## 1. 主要更新类型
- **Bug 修复为主**：修复 `FqnConfig` 传递给 `TorchAoConfig` 时的解析逻辑。
- 附带**依赖版本调整**：同步修改 `setup.py` 中的 torchao 版本要求。
- 涉及少量**测试验证**：使用 `quantize_()` 进行测试。

## 2. 关键变更点与项目方向
- 核心是修正 `FqnConfig`（Fully Qualified Name 配置）在传入 `TorchAoConfig` 时的解析方式，确保配置能被正确识别和处理。
- 同步更新 `setup.py` 中的 torchao 版本，说明该修复依赖特定版本的 torchao 行为。
- 这与 diffusers 持续集成 **torchao 量化后端**的方向一致——diffusers 正不断扩展对模型量化（如 int8、int4）的支持，以降低推理显存占用、提升部署效率。

## 3. 对项目的影响与潜在意义
- 修复后，用户通过 `TorchAoConfig` 指定量化配置时不再因 Fqn 解析错误而失败，**提升了 torchao 量化流程的可用性与稳定性**。
- 版本约束的同步避免了因 torchao API 变动导致的兼容性问题，减少用户环境配置的踩坑成本。
- 对量化这一相对较新的功能而言，此类修复是**走向生产可用**的必要打磨。

## 4. 值得关注的技术点
- **FQN（全限定名）解析**：量化配置常需按模块名精确匹配层，FQN 解析正确与否直接决定哪些层被量化。
- **配置传递链路**：`FqnConfig → TorchAoConfig → quantize_()` 的传递与解析是本次修复的关键路径。
- **版本耦合**：torchao 迭代较快，diffusers 需通过版本约束锁定兼容行为，这是集成第三方量化库的典型挑战。

## 5. 结合项目背景看发展影响
- diffusers 作为扩散模型的核心库，README 强调其易用性与多后端支持。torchao 量化是其在**推理优化与部署**方向的重要拼图。
- 本次修复虽小，但属于量化功能成熟化过程中的关键一环：只有配置解析稳定，用户才能可靠地对 UNet、Transformer 等组件做量化。
- 长远看，这类修复推动 diffusers 从“支持量化”走向“量化开箱即用”，契合其降低扩散模型使用门槛、提升推理效率的整体目标。

**总结**：这是一次聚焦 torchao 量化配置解析的精准 Bug 修复，配合版本约束调整，提升了量化功能的可靠性，体现了 diffusers 在推理优化方向上的持续投入与工程打磨。

## 详细提交记录

### [d77d530](https://github.com/huggingface/diffusers/commit/d77d53044518ed45583ce3ff680f9f87f816aeb3)

- **作者**: Sayak Paul
- **时间**: 2026-09-15T19:01:21Z
- **提交信息**: [torchao]: fix how FqnConfig is resolved and handled (#14686)

* fix: how fqnconfig passed to torchaoconfig is resolved.

* testing with quantize_()

* change torchao version in setup.py as well.

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-09-16
**监控日期**: 2026-09-15
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


**报告日期**: 2026-09-16
**监控日期**: 2026-09-15
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13119
- **最后更新**: 2026-09-15T17:59:36Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-09-16
**监控日期**: 2026-09-15
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 36003
- **最后更新**: 2026-09-16T00:09:20Z

## 提交统计

- **昨日提交总数**: 30
- **提交者数量**: 22
- **主要提交者**: Kangyan-Zhou, Lianmin Zheng, Liangsheng Yin

## AI分析总结

# SGLang 昨日提交分析总结

## 1. 主要更新类型

昨日 30 条提交以**功能新增与优化**为主，辅以大量 **Bug 修复**和 **CI/测试增强**，另有少量**重构**。核心集中在三大方向：Router 路由系统、HiCache 缓存、以及多硬件后端（AMD/NPU/DeepEP）支持。

## 2. 关键变更点与项目方向

- **Router 系统演进**：引入按 worker 注册时解析 wire protocol（#39004）、将 worker 选择抽取为 `policies::selection`（#39322）、暴露 KV 存储分层与树占用指标（#39109），并补充真实 GPU 端到端覆盖（#39110）。这表明 SGLang 正把 Router 打造成可插拔、可观测的独立调度层。
- **HiCache 深度优化**：重构 buffer 模式预取流水线与重试记账（#39283）、优化存储存在性记账（#39480），指向大规模 KV 缓存分层存储的性能与可靠性。
- **内存与推理正确性**：统一混合 SWA 的共享字节预算（#36729）、修复首 token 元数据与复用注意力层索引（#39328）、保持 Router GEMM 为 fp32 以实现确定性推理（#38176），呼应项目对**确定性、可复现推理**的追求。
- **硬件后端扩展**：DeepEP v2 支持 BF16 与 batch-invariant（#38160）、AMD CI 整合并退役 ROCm 7.0（#38632）、NPU nightly 目录按镜像划分（#39585），体现多硬件生态的持续投入。

## 3. 对项目的影响与潜在意义

- Router 的策略化与指标化，为生产环境下的**负载均衡与缓存感知调度**奠定基础，是 SGLang 从推理引擎向**服务化平台**演进的关键一步。
- HiCache 与 SWA 内存优化直接提升长上下文、大并发场景的**吞吐与显存效率**。
- 确定性推理（fp32 GEMM、batch-invariant）对**评测、调试与合规场景**意义重大。
- 大量 CI 修复（EADDRINUSE、NIXL import、artifact 目录）反映项目在快速迭代中**持续加固测试基础设施**。

## 4. 值得关注的技术点

- **wire protocol 按 worker 解析**：为异构 worker 集群提供协议灵活性。
- **共享字节预算的混合 SWA**：统一管理滑动窗口注意力内存，避免碎片化。
- **DeepEP v2 的 batch-invariant 支持**：在专家并行下保证批次无关的数值一致性。
- **辅助输出泛化**（#39164）与 **draft/verify 步骤标注**（#38630）：提升可扩展性与可观测性。
- **非严格 GLM47 工具调用 + EBNF 约束**（#38890）：增强结构化输出的鲁棒性。

## 5. 结合项目背景的发展影响

SGLang 定位为高性能 LLM 推理引擎，强调**高吞吐、低延迟、多硬件支持**。昨日提交整体延续这一主线：Router 与 HiCache 的持续打磨强化了**服务化与缓存分层**能力；确定性推理与多后端支持（AMD/NPU/DeepEP）扩大了**适用场景与硬件覆盖**；密集的 CI 修复则保障了**工程质量与迭代速度**。这些变更共同推动 SGLang 从单一推理引擎向**可观测、可调度、跨硬件的生产级推理平台**稳步演进。

## 详细提交记录

### [63845a1](https://github.com/sgl-project/sglang/commit/63845a1bb2d9f431ce11f7745cde709659e02efb)

- **作者**: Kangyan-Zhou
- **时间**: 2026-09-15T23:54:37Z
- **提交信息**: [router] Resolve a wire protocol per worker at registration (#39004)

Co-authored-by: Kangyan Zhou <kangyan.zhou@radixark.ai>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [0dabef3](https://github.com/sgl-project/sglang/commit/0dabef3d30714cca1fb047eaf8e5f9d54ee2ea53)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-15T23:37:22Z
- **提交信息**: [misc] Fix tool-call index, graph padded-row count, and prefill-graph input_embeds refresh (#39574)

### [fb91bae](https://github.com/sgl-project/sglang/commit/fb91baedab3e1de668d6e8f391ccd81cab9e9acd)

- **作者**: Kangyan-Zhou
- **时间**: 2026-09-15T22:48:51Z
- **提交信息**: [Router] Real-GPU e2e coverage for storage-tier-aware cache routing (3/4) (#39110)

Co-authored-by: Kangyan Zhou <kangyan.zhou@radixark.ai>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [b803cfa](https://github.com/sgl-project/sglang/commit/b803cfa0c46d3320c3decb3e6aa61573e4ae0e31)

- **作者**: Lianmin Zheng
- **时间**: 2026-09-15T22:38:47Z
- **提交信息**: Add external multimodal processors to the Rust frontend (#39329)

### [2929a39](https://github.com/sgl-project/sglang/commit/2929a39927a3943cee03e498f4e5f651185f1b1f)

- **作者**: Yonghao Zhuang
- **时间**: 2026-09-15T22:27:00Z
- **提交信息**: Use a shared byte budget for unified hybrid-SWA memory (#36729)

Co-authored-by: yhzhuang <yhzhuang@fb.com>
Co-authored-by: Cheng Wan <cheng.wan@radixark.ai>

### [4da5599](https://github.com/sgl-project/sglang/commit/4da5599e93b2d4b351a8934aa1a72ac5bc76d69e)

- **作者**: Lianmin Zheng
- **时间**: 2026-09-15T22:22:26Z
- **提交信息**: Fix first-token metadata and reused attention-layer indexing (#39328)

Co-authored-by: Jinghui Zhang <jinghui@meta.com>
Co-authored-by: Lucia Fang <116399278+luccafong@users.noreply.github.com>

### [08b1922](https://github.com/sgl-project/sglang/commit/08b19224054088e36aa25762a99b3e53adaadb21)

- **作者**: Yash Agarwal
- **时间**: 2026-09-15T22:16:39Z
- **提交信息**: fix(gemma4): set lm_head_is_tied for Gemma4UnifiedForConditionalGeneration (#35809)

Co-authored-by: kpham-sgl <khoa.pham@radixark.ai>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [87c9f78](https://github.com/sgl-project/sglang/commit/87c9f78e994f6e956b1e25291766288c7928d319)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-15T22:07:42Z
- **提交信息**: [Fix][PD] Give prefill and decode their own RDMA NICs in disaggregation tests (#39584)

### [406c9c7](https://github.com/sgl-project/sglang/commit/406c9c71d833570aa89bc26ccb2e9d1518cd4564)

- **作者**: Cheng Wan
- **时间**: 2026-09-15T21:30:50Z
- **提交信息**: [Feature] Support BF16 and batch-invariant inference with DeepEP v2 (#38160)

### [d58342d](https://github.com/sgl-project/sglang/commit/d58342deab27e6f8bb507d9db2a0f87c6f42cee3)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-15T20:39:15Z
- **提交信息**: [Fix] Release NCCL on scheduler exit and let the ASGI server own shutdown (#39560)

### [3c48c1e](https://github.com/sgl-project/sglang/commit/3c48c1e967f64a6b2b116b8f6719d51eb360eb55)

- **作者**: Kangyan-Zhou
- **时间**: 2026-09-15T20:30:05Z
- **提交信息**: [Router] Expose the KV storage-tier stream and tree occupancy on /metrics (2/4) (#39109)

Co-authored-by: Kangyan Zhou <kangyan.zhou@radixark.ai>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [24874f9](https://github.com/sgl-project/sglang/commit/24874f90a3246a7c2895cea13cc0e4cdb875280e)

- **作者**: YAMY
- **时间**: 2026-09-15T19:40:28Z
- **提交信息**: [Test] Fix DeepGEMM batch invariance test output dtype (#39636)

### [073fdf9](https://github.com/sgl-project/sglang/commit/073fdf97cc69c01b9433fcc73b1f1d01683eded8)

- **作者**: jasonjk-park
- **时间**: 2026-09-15T19:05:13Z
- **提交信息**: Generalize auxiliary outputs (#39164)

Co-authored-by: jasonjk <jasonjk@twshared0085.36.lco2.facebook.com>

### [49f540f](https://github.com/sgl-project/sglang/commit/49f540f3c0b87c41ceb8c3f1a8cc9a11e15caf31)

- **作者**: Zhiqiang Xie
- **时间**: 2026-09-15T17:49:58Z
- **提交信息**: [HiCache] Optimize buffer-mode storage existence bookkeeping (#39480)

### [7f5dd19](https://github.com/sgl-project/sglang/commit/7f5dd192563a5fd1ae1a2d2ae0a1bc94b5a84f33)

- **作者**: Zhiqiang Xie
- **时间**: 2026-09-15T17:48:49Z
- **提交信息**: [HiCache] Rework the buffer-mode storage prefetch pipeline and retry bookkeeping (#39283)

### [03ea13a](https://github.com/sgl-project/sglang/commit/03ea13a54557de52da5faab2c422da07c3727407)

- **作者**: Bingxu Chen
- **时间**: 2026-09-15T15:45:22Z
- **提交信息**: [AMD][CI] Consolidate AMD workflows and retire ROCm 7.0 CI (#38632)

### [47a157f](https://github.com/sgl-project/sglang/commit/47a157f257f13311a4408dbde3506f6a9cedaa74)

- **作者**: Shangming Cai
- **时间**: 2026-09-15T15:05:05Z
- **提交信息**: [CI][Disaggregation] Fix EADDRINUSE flake in test_disaggregation_dwdp_gpt_oss (#39611)

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [1aeeb25](https://github.com/sgl-project/sglang/commit/1aeeb25e86df5c8561da48478d5549d836d8d518)

- **作者**: pllimax
- **时间**: 2026-09-15T14:55:53Z
- **提交信息**: [NPU][CI] Scope NPU nightly artifact dirs by image; fix stale glm5_2 case (#39585)

### [832ec39](https://github.com/sgl-project/sglang/commit/832ec39cc0324cb0e7823dc8385e27a30c356bdd)

- **作者**: Siyuan Chen
- **时间**: 2026-09-15T13:08:33Z
- **提交信息**: [Intra-node PD][DSV4] Pack all layers into one batch for INTRA_NODE_NVLINK path (#38984)

Co-authored-by: BJWang-ant <wangbingjia.wbj@ant-intl.com>

### [a2a2619](https://github.com/sgl-project/sglang/commit/a2a261963f7698a730ac94f2ebd8b41cc44123c8)

- **作者**: Po-Han Huang (NVIDIA)
- **时间**: 2026-09-15T13:01:05Z
- **提交信息**: [CI] Fix SWA decode radix cache NIXL import (#39600)

### [1895cab](https://github.com/sgl-project/sglang/commit/1895cabfa8d0c7b171d72717812abe0c5d831791)

- **作者**: Yoray Zack
- **时间**: 2026-09-15T11:07:25Z
- **提交信息**: Fix mooncake scale joiner groups (#38503)

Co-authored-by: Po-Han Huang (NVIDIA) <53919306+nvpohanh@users.noreply.github.com>

### [fb01a07](https://github.com/sgl-project/sglang/commit/fb01a079a6b4f4c753e271c434ee7da884ffddb0)

- **作者**: Elizaveta Martirosian
- **时间**: 2026-09-15T11:03:11Z
- **提交信息**: [NPU] [CI] Fix multimodal_gen filter leakage and add daily scheduled run (#39411)

Co-authored-by: ronnie_zheng <zl19940307@163.com>

### [17ba2c2](https://github.com/sgl-project/sglang/commit/17ba2c2e7c7b81f31a8a9e693e7435ab262c16b4)

- **作者**: Yuxuan Zhang
- **时间**: 2026-09-15T08:41:48Z
- **提交信息**: Support non-strict GLM47 tool calls with EBNF constraints (#38890)

Co-authored-by: Xinyuan Tong <xinyuantong.cs@gmail.com>

### [2c0a709](https://github.com/sgl-project/sglang/commit/2c0a70960c7a3335f6a6472620defe4726b83caf)

- **作者**: Qiaolin Yu
- **时间**: 2026-09-15T08:36:14Z
- **提交信息**: [qwen 3.8 next] reuse old cuda stream instead of endlessly creating streams (#39474)

### [8565b11](https://github.com/sgl-project/sglang/commit/8565b110031e0449ad4db0503859b36d71331046)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-15T08:24:46Z
- **提交信息**: [misc] Trim redundant variants from the 8-gpu-h20 disaggregation test suite (#39544)

### [4f52c99](https://github.com/sgl-project/sglang/commit/4f52c9948bc8fd0d5d0185fc8ca23f1f9dc2806b)

- **作者**: Carrie Chen
- **时间**: 2026-09-15T08:16:09Z
- **提交信息**: keeping router GEMM in fp32 for deterministic inference (DeepSeek V3/V4) (#38176)

Co-authored-by: Brayden Zhong <b8zhong@uwaterloo.ca>
Co-authored-by: Brayden Zhong <brayden@radixark.ai>

### [37ebacb](https://github.com/sgl-project/sglang/commit/37ebacb50f867aa900ce1f7df3a7e2081beb18e2)

- **作者**: Beihao Zhou
- **时间**: 2026-09-15T08:14:41Z
- **提交信息**: [EPLB] Drop defensive getattr for ep_dispatch_algorithm (#31804)

Co-authored-by: Brayden Zhong <b8zhong@uwaterloo.ca>

### [df254b0](https://github.com/sgl-project/sglang/commit/df254b0a112c0a9e01deba571ab9125d7233cfd1)

- **作者**: Bi Xue
- **时间**: 2026-09-15T07:57:05Z
- **提交信息**: [profiler] Label draft-runner steps DRAFT and target verify VERIFY in step spans (#38630)

Co-authored-by: Lianmin Zheng <lianminzheng@gmail.com>

### [0e9b6bf](https://github.com/sgl-project/sglang/commit/0e9b6bf8d8be2e9be237cb7236b936980fabc34d)

- **作者**: Kangyan-Zhou
- **时间**: 2026-09-15T07:49:31Z
- **提交信息**: [Router] Extract worker selection into policies::selection (no behavior change) (#39322)

Co-authored-by: Kangyan Zhou <kangyan.zhou@radixark.ai>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [e4a6b09](https://github.com/sgl-project/sglang/commit/e4a6b090f45f9eaece80c6abfbdb45ccd80b3627)

- **作者**: Khoa Pham
- **时间**: 2026-09-15T07:35:01Z
- **提交信息**: [CI] Run test_unified_radix_cache_kl_dcp on cutedsl_mla with bf16 KV cache (#39553)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-09-16
**监控日期**: 2026-09-15
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1278
- **最后更新**: 2026-09-15T13:20:30Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-09-16
**监控日期**: 2026-09-15
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 91865
- **最后更新**: 2026-09-16T00:07:01Z

## 提交统计

- **昨日提交总数**: 36
- **提交者数量**: 30
- **主要提交者**: Wentao Ye, Kevin H. Luu, Nick Hill

## AI分析总结

# vLLM 昨日提交分析总结（36 条）

## 1. 主要更新类型分布

- **Bug 修复**（约 12 条）：占比最高，覆盖稀疏 MLA 越界访问、KV cache 偏移、beam search 中止请求、Rust 前端渲染、EPLB 未初始化状态等。
- **性能优化**（约 7 条）：Nemotron latent-MoE all-reduce 跳过、DeepGEMM Mega-mHC 集成、ROCm DSV4.1 top-k 优化、DSpark 状态折叠等。
- **功能新增/扩展**（约 6 条）：NIXL attention-HMA 布局、PCP decode-only FULL CUDA graphs、Rust 前端 token 直方图。
- **重构与清理**（约 5 条）：StructuredOutputManager 与投机解码重构、移除死代码、MRV2 buffer 简化。
- **构建/CI**（约 6 条）：Rubin 依赖更新、DeepGEMM pin 迁移至 vLLM fork、CI 分片与超时调整。

## 2. 关键变更点与项目方向

- **DeepSeek V4.1 深度适配**：多条提交（DeepGEMM 稀疏 MQA、Mega-mHC、XGrammar schema 约束、DSpark drafter 修复）集中强化对 DeepSeek V4.1 的支持，显示 vLLM 正快速跟进最新大模型架构。
- **KV Connector 与流水线并行**：NIXL 支持 attention-HMA 布局、HiSparse 配置推断，呼应 vLLM 在分布式推理与 KV 缓存复用上的持续投入。
- **Rust 前端演进**：token 直方图、`add_generation_prompt` 修复，表明 Rust 前端正逐步成熟，是 vLLM 提升服务性能的重要方向。
- **ROCm/XPU 多硬件支持**：AMD gfx950 优化、Aiter MLA 解码、Intel GPU CI 调整，体现跨平台战略。

## 3. 对项目的影响与潜在意义

- 大量 Bug 修复提升了**生产环境稳定性**，尤其是稀疏注意力与投机解码路径的边界问题。
- 性能优化（如 Nemotron ~13% decode 提升）直接降低服务成本，契合 README 中"cheap LLM serving"目标。
- DeepGEMM pin 迁移至 vLLM fork，意味着项目对关键 kernel 依赖的**自主可控性增强**。
- StructuredOutputManager 重构为后续结构化输出与投机解码协同奠定基础。

## 4. 值得关注的技术点

- **attention-HMA 布局**在流水线并行 push prefill 中的支持，是 KV 传输效率的关键。
- **decode-only FULL CUDA graphs**（PCP）可显著降低解码延迟。
- **Mega-mHC / Mega-MoE** 与 DeepGEMM 的集成，代表 MoE 推理的前沿优化。
- **sampled filtering for persistent top-k** 是采样 kernel 的性能细节优化。

## 5. 结合项目背景的发展影响

vLLM 定位为"Easy, fast, and cheap LLM serving for everyone"。本批提交从三方面推进该目标：**广度**上扩展硬件（ROCm/XPU）与模型（DeepSeek V4.1、Gemma 4、Nemotron）覆盖；**深度**上通过 kernel 级优化与 CUDA graph 提升吞吐；**稳健性**上以密集 Bug 修复保障生产可用。整体呈现"紧跟新模型 + 强化分布式 + 多硬件并行"的成熟工程节奏，符合其作为主流推理引擎的演进路径。

## 详细提交记录

### [031f581](https://github.com/vllm-project/vllm/commit/031f5810c1957b6ec2a7666f65a3fe68c1f7e534)

- **作者**: Shang Wang
- **时间**: 2026-09-15T23:29:13Z
- **提交信息**: [Build][NVIDIA] Update public Rubin dependencies and MSA compatibility (#56545)

Signed-off-by: Shang Wang <samshang.wang@mail.utoronto.ca>
Co-authored-by: Codex <noreply@openai.com>

### [0fefffc](https://github.com/vllm-project/vllm/commit/0fefffc9346644a01dc132e544b881ad646ea81b)

- **作者**: qizixi
- **时间**: 2026-09-15T22:43:56Z
- **提交信息**: [KVConnector][NIXL] Support attention-HMA layouts in pipeline-parallel push prefill (#50494)

Signed-off-by: zixi-qi <zixi@inferact.ai>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Yiliu Dong <91178480+qianlihuang@users.noreply.github.com>
Co-authored-by: Codex <noreply@openai.com>

### [c6fa1f0](https://github.com/vllm-project/vllm/commit/c6fa1f05d1bc627171c3a58c05f23a1c41202ac1)

- **作者**: Misha Goin
- **时间**: 2026-09-15T21:15:59Z
- **提交信息**: [Perf][Kernel] Add sampled filtering for persistent top-k (#56346)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [1257512](https://github.com/vllm-project/vllm/commit/12575123059c2142e39c9af4e217a4792c3c8176)

- **作者**: Jared Wen
- **时间**: 2026-09-15T21:07:14Z
- **提交信息**: [DSA] Wire DeepGEMM sparse MQA logits into the DeepSeek V4.1 indexer (#56254)

Signed-off-by: Jared Wen <w13431838023@gmail.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [f2aad6a](https://github.com/vllm-project/vllm/commit/f2aad6aa70749ccc4604d31d6f8a04c6728c3361)

- **作者**: Nick Hill
- **时间**: 2026-09-15T20:36:51Z
- **提交信息**: [MRV2] Buffer util simplifications (#56888)

Signed-off-by: Nick Hill <nickhill123@gmail.com>

### [b6ce714](https://github.com/vllm-project/vllm/commit/b6ce7143548a937b10764eaddfd03e459d0dab33)

- **作者**: zwang86
- **时间**: 2026-09-15T20:35:54Z
- **提交信息**: [Bugfix] Format kernel-import errors eagerly so warning_once does not retain them (#54098)

Signed-off-by: Zeyu Wang <zwang86@users.noreply.github.com>
Co-authored-by: Zeyu Wang <zwang86@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [38ca7a8](https://github.com/vllm-project/vllm/commit/38ca7a899cd3a9aa6f1e948b1b63f4fae7a685ce)

- **作者**: Lucas Wilkinson
- **时间**: 2026-09-15T20:27:11Z
- **提交信息**: [Bugfix][HiSparse] Preserve per-layer offsets in KV cache bindings (#57027)

Signed-off-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [18f8aa0](https://github.com/vllm-project/vllm/commit/18f8aa04656de0a37eb5c7e9efc8ebb595ac73cf)

- **作者**: Wentao Ye
- **时间**: 2026-09-15T20:17:53Z
- **提交信息**: [Refactor] Remove dead kernel code (#56845)

Signed-off-by: yewentao256 <zhyanwentao@126.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [df42d11](https://github.com/vllm-project/vllm/commit/df42d112ee88dd4a9b64efbad55621af6a66a44b)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-09-15T19:44:26Z
- **提交信息**: [Config] Infer HiSparse attention config from HiSparseConnector (#57041)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [2fcc524](https://github.com/vllm-project/vllm/commit/2fcc5247882849b675088b3146b27c006e87d87f)

- **作者**: Taneem Ibrahim
- **时间**: 2026-09-15T19:41:54Z
- **提交信息**: [Bugfix] Avoid nested score cancellation handlers for /v1/score alias (#57024)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [dffbb71](https://github.com/vllm-project/vllm/commit/dffbb714e4e8e4b95ccc888df98d47c7d2cef78d)

- **作者**: Fangzhou Ai
- **时间**: 2026-09-15T18:34:24Z
- **提交信息**: [ROCm][Perf] Optimize DSV4.1 K=512 decode top-k on gfx950 (#56743)

Signed-off-by: fai <fangzhouai@gmail.com>

### [2f46a1d](https://github.com/vllm-project/vllm/commit/2f46a1d9c6ab33c4ea8196c375ff85b661982bff)

- **作者**: Kevin H. Luu
- **时间**: 2026-09-15T18:19:14Z
- **提交信息**: [CI] Keep Qwen3 Omni DSpark config fixture complete (#57044)

Signed-off-by: Kevin Luu <51931015+khluu@users.noreply.github.com>

### [35dc273](https://github.com/vllm-project/vllm/commit/35dc273072ff133743bc5fcfa306bf030fa8730b)

- **作者**: ppalanga
- **时间**: 2026-09-15T17:18:09Z
- **提交信息**: [ROCm][Spec Decode] Add Aiter MLA decode support non-causal draft block (#55966)

Signed-off-by: Poovaiah Palangappa <poovaiah.palangappa@amd.com>
Co-authored-by: Poovaiah Palangappa <poovaiah.palangappa@amd.com>
Co-authored-by: John Qin <zhengsheng1997@gmail.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Hongxia Yang <62075498+hongxiayang@users.noreply.github.com>

### [241e939](https://github.com/vllm-project/vllm/commit/241e9391ed85f6c967432135427717a529776a63)

- **作者**: Kevin H. Luu
- **时间**: 2026-09-15T16:58:30Z
- **提交信息**: [Bugfix][Attention] Stabilize sparse-MLA DCP for GLM PCP evals (#55879)

Signed-off-by: khluu <khluu000@gmail.com>
Signed-off-by: Kevin Luu <51931015+khluu@users.noreply.github.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Tyler Michael Smith <tlrmchlsmth@gmail.com>
Co-authored-by: Jason Yao <wsyjh8@gmail.com>

### [836bb38](https://github.com/vllm-project/vllm/commit/836bb3839ffefcda8283ea7d41671a89e1a613df)

- **作者**: Chauncey
- **时间**: 2026-09-15T15:03:58Z
- **提交信息**: [Bugfix] Prevent out-of-bounds access in FlashInfer SM90 sparse MLA mixed batches (#56969)

Signed-off-by: chaunceyjiang <chaunceyjiang@gmail.com>

### [9446ea1](https://github.com/vllm-project/vllm/commit/9446ea168067c141992f86c3a796e8551f37139e)

- **作者**: drslark
- **时间**: 2026-09-15T14:59:02Z
- **提交信息**: [Bugfix][Spec Decode] Only create draft_id_to_target_id when draft vocab differs (#53458)

Signed-off-by: drslark <slarksblood@qq.com>
Signed-off-by: Isotr0py <2037008807@qq.com>
Co-authored-by: GLM-5.3 <glm@z.ai>
Co-authored-by: Isotr0py <2037008807@qq.com>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>

### [1e47ec0](https://github.com/vllm-project/vllm/commit/1e47ec00d2e6ad911969508068b72f7d1aae1968)

- **作者**: Abhinav Verma
- **时间**: 2026-09-15T14:57:32Z
- **提交信息**: [Bugfix][Gemma 4] Don't read fft_length when profiling unified audio (#56721)

Signed-off-by: Abhinav Verma <verma.abhinav275@gmail.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [f0fbc98](https://github.com/vllm-project/vllm/commit/f0fbc98c488b40a07d3b269aeba2bda3c4c3b03b)

- **作者**: Chauncey
- **时间**: 2026-09-15T14:50:26Z
- **提交信息**: [Frontend] Share max_num_queued_reqs across API server processes (#54746)

Signed-off-by: chaunceyjiang <chaunceyjiang@gmail.com>

### [0136df9](https://github.com/vllm-project/vllm/commit/0136df94b0d75732be6c66f620f51289c888e41d)

- **作者**: zack
- **时间**: 2026-09-15T14:35:47Z
- **提交信息**: [Bugfix][Spec Decode][MoE] Avoid uninitialized EPLB state in DeepSeek V4.1 DSpark drafter (#56387)

Signed-off-by: zack <51604064+luoyuctl@users.noreply.github.com>

### [4bac767](https://github.com/vllm-project/vllm/commit/4bac767695d2dfecd4098a77f71dacd100061247)

- **作者**: Junhao Shen
- **时间**: 2026-09-15T14:33:51Z
- **提交信息**: [Perf][Nemotron] Skip redundant latent-MoE all-reduce at TP>1 (~13% decode win) (#52301)

Signed-off-by: Junhao Shen <junshen@nvidia.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: Misha Goin <mgoin64@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [a2e8f1e](https://github.com/vllm-project/vllm/commit/a2e8f1ea94b1332428e2282744cec12ce7c75d88)

- **作者**: xiangdong
- **时间**: 2026-09-15T14:04:09Z
- **提交信息**: [XPU][CI]Skip test_chat_completion_with_tools in Intel GPU CI (#56934)

Signed-off-by: zengxian <xiangdong.zeng@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [e6960af](https://github.com/vllm-project/vllm/commit/e6960af33b379d502f409e3e2241bbf2b2c2f68d)

- **作者**: yzong-rh
- **时间**: 2026-09-15T13:48:49Z
- **提交信息**: [Refactor] StructuredOutputManager x Speculative Decoding Refactor (#48200)

### [6485608](https://github.com/vllm-project/vllm/commit/64856080b05054fc62754f37234f7b483b753445)

- **作者**: Taneem Ibrahim
- **时间**: 2026-09-15T13:21:05Z
- **提交信息**: [Bugfix] Measure complete pooling responses (#56760)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [78eaaad](https://github.com/vllm-project/vllm/commit/78eaaad2c7a7f8c7864d9c9c72772e3f9f2669d0)

- **作者**: Bugen Zhao
- **时间**: 2026-09-15T12:12:15Z
- **提交信息**: [Rust Frontend] Add iteration token histogram (#56990)

Co-authored-by: Codex <noreply@openai.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>

### [bb55077](https://github.com/vllm-project/vllm/commit/bb5507741155a698750bc422cda1f7c57f7d114d)

- **作者**: Juntian Liu
- **时间**: 2026-09-15T11:01:06Z
- **提交信息**: [Perf][Kernel] Integrate Mega-mHC from DeepGEMM for DeepSeek V4.1  (reopen of #56255) (#56962)

Signed-off-by: Yongye Zhu <zyy1102000@gmail.com>
Signed-off-by: Juntian Liu <Juntianl777@gmail.com>
Co-authored-by: Yongye Zhu <zyy1102000@gmail.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: Thien Tran <gau.nernst@yahoo.com.sg>

### [5be911e](https://github.com/vllm-project/vllm/commit/5be911ee871604895c5a950ac1a5675c71896fd2)

- **作者**: ALEX LILUZ
- **时间**: 2026-09-15T10:31:25Z
- **提交信息**: [Bugfix] Load reasoning parser plugins before headless engine config (#53124)

Signed-off-by: alexliluz <49665315+alexliluz@users.noreply.github.com>
Co-authored-by: Jiangyun Zhu <riverclouds.zhu@qq.com>

### [24bfbd5](https://github.com/vllm-project/vllm/commit/24bfbd5d4d530a2657a8925e5d12e86b1ccb9cca)

- **作者**: Flora Feng
- **时间**: 2026-09-15T10:07:58Z
- **提交信息**: [Refactor] Derive is_reasoning_end from the engine grammar (#56200)

Signed-off-by: sfeng33 <4florafeng@gmail.com>

### [142020c](https://github.com/vllm-project/vllm/commit/142020c6c2c0d4fec4d36df28290e3d9b654a385)

- **作者**: Yeonwoo Sung
- **时间**: 2026-09-15T10:03:26Z
- **提交信息**: [Bugfix][Rust Frontend] Honor `add_generation_prompt` in DeepSeek V3.2/V4/V4.1 renderers (#56593)

Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Signed-off-by: YeonwooSung <neos960518@gmail.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>

### [073f883](https://github.com/vllm-project/vllm/commit/073f883b56a5b585366da874473db100bc6fff7e)

- **作者**: Juntian Liu
- **时间**: 2026-09-15T09:58:57Z
- **提交信息**: [Perf][DSpark] Collapse DeepSeek-V4.1 draft states before SP all-gather (#56903)

Signed-off-by: Juntian Liu <Juntianl777@gmail.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Woosuk Kwon <woosuk@inferact.ai>

### [abb4cb9](https://github.com/vllm-project/vllm/commit/abb4cb9fc5f1b1039876ed8a657b025f65643d11)

- **作者**: Thang Nguyen
- **时间**: 2026-09-15T09:58:42Z
- **提交信息**: [CI] Shard V1 KV Connectors 1→4 (#56324)

Signed-off-by: Thang Nguyen <thang.nguyen@inferact.ai>
Co-authored-by: Thang Nguyen <thang.nguyen@inferact.ai>
Co-authored-by: Kimi Code <noreply@moonshot.cn>

### [2983fc6](https://github.com/vllm-project/vllm/commit/2983fc62869de7943bd68ea58730eec7a39ff597)

- **作者**: Kevin H. Luu
- **时间**: 2026-09-15T09:00:58Z
- **提交信息**: [CI] Fix NIXL push worker test stub after failure deferral (#56955)

Signed-off-by: Kevin Luu <51931015+khluu@users.noreply.github.com>

### [2c2cbd8](https://github.com/vllm-project/vllm/commit/2c2cbd84fdf199901f3f4e6b0e708ee0664aadd6)

- **作者**: Yixin Dong
- **时间**: 2026-09-15T08:36:16Z
- **提交信息**: [Frontend] Use XGrammar schema constraints for DeepSeek V4.1 (#56408)

Signed-off-by: Ubospica <ubospica@gmail.com>
Co-authored-by: Flora Feng <4florafeng@gmail.com>

### [6766503](https://github.com/vllm-project/vllm/commit/676650397ff71cd802e7e0e30c2e46a215ab86ee)

- **作者**: Qiu Chunshuo
- **时间**: 2026-09-15T08:27:46Z
- **提交信息**: [Feature][PCP] Support decode-only FULL CUDA graphs (#53867)

Signed-off-by: QiuChunshuo <qiuchunshuo@huawei.com>
Signed-off-by: QiuChunshuo <chunshuoq@gmail.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Lucas Wilkinson <LucasWilkinson@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [ca67438](https://github.com/vllm-project/vllm/commit/ca67438c088d5ada7da901b77f9aeaebc1b9542c)

- **作者**: shaohuaxi
- **时间**: 2026-09-15T08:17:30Z
- **提交信息**: [Bugfix][Frontend] Handle aborted requests in beam search (#56249)

Signed-off-by: 子华 <huaxi.shx@alibaba-inc.com>
Co-authored-by: Codex <noreply@openai.com>

### [2e2fdaa](https://github.com/vllm-project/vllm/commit/2e2fdaa99a512b58e6fa3b9fd24a07f7699d694c)

- **作者**: Kevin H. Luu
- **时间**: 2026-09-15T08:00:40Z
- **提交信息**: [CI] Extend Arm CPU kernel shard timeout (#56601)

Signed-off-by: Kevin Luu <51931015+khluu@users.noreply.github.com>
Co-authored-by: Sherlock <sherlock@openai.com>

### [8263ea1](https://github.com/vllm-project/vllm/commit/8263ea12bd8fa7584277f5200d521193259707b7)

- **作者**: Yongye Zhu
- **时间**: 2026-09-15T07:57:18Z
- **提交信息**: [Build] Move DeepGEMM pin to the vLLM fork and update the Mega MoE call convention (#56876)

Signed-off-by: Yongye Zhu <zyy1102000@gmail.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-09-16
**监控日期**: 2026-09-15
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 6808
- **最后更新**: 2026-09-15T23:50:44Z

## 提交统计

- **昨日提交总数**: 8
- **提交者数量**: 8
- **主要提交者**: wtz2333, xuexueligao, LOGO127

## AI分析总结

# vllm-omni 昨日提交分析（8 条）

## 1. 主要更新类型
- **功能新增**：Gepard-1.0 语音合成服务、MiniMax H3 视频放大工作流（WF-07）、Cosmos3 的 SeaCache 支持。
- **性能优化**：Qwen-Image 的 QK RoPE Triton 路径、Lingbot World 图像条件存储与时间 RoPE 扩展。
- **Bug 修复**：delta 输出中采样率快照的边界控制。
- **测试/CI**：ROCm 非阻塞入口 GPU 覆盖、tiny 模型框架的图像编辑输入限制测试。

## 2. 关键变更点与项目方向
- 新增 **/v1/audio/speech** 服务，直接对齐 README 中“omni-modality serving”的核心定位，扩展音频模态的 OpenAI 兼容接口。
- **SeaCache** 与 **QK RoPE Triton** 均属推理加速，契合“fast and cheap”目标。
- **ROCm CI 覆盖**体现多硬件后端支持，符合“for everyone”的普惠方向。
- 视频放大工作流与图像编辑测试，强化多模态（视频/图像）能力矩阵。

## 3. 对项目的影响与潜在意义
- 音频服务落地使 vllm-omni 从文本/图像进一步覆盖语音，向真正的“全模态”服务迈进。
- 缓存与 RoPE 优化可显著降低扩散模型推理成本，提升长序列/高分辨率场景可用性。
- ROCm 覆盖降低 AMD 用户接入门槛，扩大生态。
- 边界修复与输入限制测试提升稳定性，减少生产环境隐患。

## 4. 值得关注的技术点
- **SeaCache** 在 Cosmos3 上的缓存策略，可能成为扩散模型通用加速范式。
- **QK RoPE Triton** 自定义内核，展示对注意力算子的深度优化。
- **delta 采样率快照有界化**，涉及流式输出的内存安全，值得关注其实现细节。
- **Lingbot World 时间 RoPE 扩展**，对视频时序建模有直接价值。

## 5. 结合项目背景的发展影响
README 强调“easy、fast、cheap、omni-modality”。本批提交在三个维度同时推进：**omni**（音频、视频、图像）、**fast/cheap**（SeaCache、Triton RoPE）、**everyone**（ROCm CI）。整体看，项目正从单一模态服务向多模态统一推理平台演进，并通过性能与硬件兼容性双轮驱动，巩固其作为通用全模态推理引擎的定位。

## 详细提交记录

### [65693b3](https://github.com/vllm-project/vllm-omni/commit/65693b30fb52da47f1ce9129508e9cd524c86513)

- **作者**: LOGO127
- **时间**: 2026-09-15T23:50:32Z
- **提交信息**: [Bugfix][Core] Keep sample-rate snapshots bounded in delta output (#7448)

Signed-off-by: luozijian <luozijian0924@gmail.com>

### [bbf77cc](https://github.com/vllm-project/vllm-omni/commit/bbf77cce69bff7dfd43234e938f1b8149e2a4359)

- **作者**: andyluo7
- **时间**: 2026-09-15T23:25:56Z
- **提交信息**: [CI][ROCm] Add non-blocking entrypoint GPU coverage (#7398)

Signed-off-by: andyluo7 <andy.luo@amd.com>

### [6040bb9](https://github.com/vllm-project/vllm-omni/commit/6040bb97e2036927632151a87b0aaed94ccbce7d)

- **作者**: yzhautouskay
- **时间**: 2026-09-15T21:57:15Z
- **提交信息**: [Perf][Cosmos3] Add SeaCache support for Cosmos3 (#6922)

Signed-off-by: Yuliya Zhautouskaya <yzhautouskay@nvidia.com>

### [c17126c](https://github.com/vllm-project/vllm-omni/commit/c17126c21994edc5aaf1fa3a6248d67bd0ab9d29)

- **作者**: Mengjie Zhao
- **时间**: 2026-09-15T21:56:51Z
- **提交信息**: [Model] Add Gepard-1.0 OpenAI /v1/audio/speech serving (#7499)

Signed-off-by: Mengjie Zhao <zmj0129@gmail.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [7893475](https://github.com/vllm-project/vllm-omni/commit/78934753ff7e092b24ada0e34062cf3d121efd25)

- **作者**: Nick Cao
- **时间**: 2026-09-15T16:36:34Z
- **提交信息**: [Tests] Test image edit input limits in tiny model framework (#7434)

Signed-off-by: Nick Cao <ncao@redhat.com>
Co-authored-by: Codex <noreply@openai.com>

### [952022c](https://github.com/vllm-project/vllm-omni/commit/952022c8ec62aa0b3ad0ed57d89630e54fd041ec)

- **作者**: dongbo910220
- **时间**: 2026-09-15T14:28:48Z
- **提交信息**: [Diffusion][Perf] Add Qwen-Image QK RoPE Triton path (#5931)

Signed-off-by: dongbo910220 <1275604947@qq.com>

### [a3dee6f](https://github.com/vllm-project/vllm-omni/commit/a3dee6fdf52267fd56f0237f47b5bbe68dbb13b2)

- **作者**: wtz2333
- **时间**: 2026-09-15T10:49:55Z
- **提交信息**: [Lingbot World] Bound image condition storage and extend temporal RoPE (#6838)

Signed-off-by: wtz2333 <2955110911@qq.com>

### [4a8ac29](https://github.com/vllm-project/vllm-omni/commit/4a8ac297751b03fbe21f2d8a4550a027fe02e7cd)

- **作者**: xuexueligao
- **时间**: 2026-09-15T10:46:13Z
- **提交信息**: [Frontend] Add MiniMax H3 video upscale workflow (WF-07) (#7472)

Signed-off-by: xuezhihao <89690814+xuexueligao@users.noreply.github.com>
Signed-off-by: 汪志鹏 <wangzhipeng628@gmail.com>
Co-authored-by: 汪志鹏 <wangzhipeng628@gmail.com>

---
