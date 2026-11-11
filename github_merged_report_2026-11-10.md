# GitHub Stars 合并报告 - 2026-11-10

**合并日期**: 2026-11-11
**监控日期**: 2026-11-10
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


**报告日期**: 2026-11-11
**监控日期**: 2026-11-10
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2289
- **最后更新**: 2026-11-10T11:24:12Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Coach257

## AI分析总结

## 分析总结

### 1. 主要更新类型
- **功能新增为主**：为 SeedOmni 框架添加 Qwen3-VL（多模态视觉语言模型）的支持。
- 涉及范围较广（omni、model、config、docs、agent 多个模块），说明这是一次端到端的集成，而非单点改动，可能还伴随少量配置与文档更新。

### 2. 关键变更点及与项目方向的关系
- **核心是接入 Qwen3-VL**：作为新一代视觉语言模型，它的加入扩展了 VeOmni 可支持的模型谱系，直接呼应项目 "Scaling Any Modality Model Training" 的多模态模型训练目标。
- **改动横跨 model/config/agent 等模块**：表明需要为新模型编写模型定义、训练配置、以及可能的推理/评测 agent 逻辑，体现了项目 "Model-Centric Distributed Recipe Zoo"（以模型为中心的分布式配方库）的设计理念——每接入一个新模型，就沉淀一套完整的分布式训练配方。
- **docs 更新**：与项目重视文档（readthedocs）的惯例一致，保证新模型的使用方式可被社区复现。

### 3. 对项目的影响和潜在意义
- **扩大模型覆盖面**：Qwen3-VL 是社区关注度高的多模态模型，支持它能提升 VeOmni 在开源多模态训练生态中的实用价值与吸引力。
- **验证框架的可扩展性**：一次 PR 即完成从模型定义到配置、文档、agent 的全链路接入，侧面证明了 VeOmni 抽象层设计良好，新增模型的成本可控。
- **生态协同**：作为 ByteDance-Seed 系列项目，接入阿里 Qwen 系列模型也体现了跨生态兼容的开放姿态，有利于社区采纳。

### 4. 值得关注的技术点
- **多模态数据流与并行策略**：Qwen3-VL 含视觉编码器，需要在分布式训练中处理图文混合数据、视觉 token 的序列长度不均、以及可能的异构并行（视觉塔与 LLM 的分组并行），这是 VeOmni 分布式配方能力的试金石。
- **Recipe 的参数化设计**：关注配置文件如何声明 Qwen3-VL 的特有超参（分辨率、视觉编码器结构等），这决定配方库是否可复用。
- **agent 模块的角色**：若涉及评测/推理 agent，需注意其与训练配方的一致性维护。

### 5. 对项目发展的整体影响
- 结合 README，VeOmni 的定位是提供"任意模态模型"的分布式训练配方库。本次提交**丰富了模型配方库的多模态（视觉-语言）维度**，使项目在 "Any Modality" 的承诺上更进一步。
- 单日内即合并此类跨模块功能 PR，反映项目处于活跃迭代期，正快速扩充模型支持矩阵以建立生态壁垒。
- 长期看，持续接入主流多模态模型（如 Qwen3-VL）将强化 VeOmni 作为"训练配方中枢"的地位，吸引更多研究者将其作为多模态训练的默认基础设施，从而推动项目向社区标准工具演进。

**总而言之**，这次提交是 VeOmni 多模态能力版图上的一次标志性扩张，既验证了其模型中心化架构的可扩展性，也为其在开源多模态训练生态中的竞争卡位奠定了基础。

## 详细提交记录

### [1eb463f](https://github.com/ByteDance-Seed/VeOmni/commit/1eb463fb420f9caefa2429ffb33da8b121b3681a)

- **作者**: Coach257
- **时间**: 2026-11-10T06:13:39Z
- **提交信息**: [omni, model, config, docs, agent] feat: support Qwen3-VL in SeedOmni (#1409)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-11-11
**监控日期**: 2026-11-10
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2999
- **最后更新**: 2026-11-10T18:01:28Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: STwangyingrui

## AI分析总结

## 1. 主要更新类型

- **功能新增（部署与推理配置扩展）**：为 Thor 硬件增加 Docker 镜像构建支持，并新增 NeoPP 后端在 Thor 上的推理配置文件，属于典型的硬件生态适配类提交，而非 Bug 修复或性能调优。

## 2. 关键变更点及与项目方向的关系

- 新增 **Thor Dockerfile**，将运行环境、依赖与镜像构建流程固化，属于基础设施层面的补充。
- 新增 **NeoPP Thor 推理配置**，把 Thor 硬件接入 NeoPP 推理路径，使框架在该加速硬件上具备可直接运行的参数模板。
- 与 LightX2V "轻量视频生成推理框架" 的定位高度一致：项目核心价值在于以更低开销完成视频生成推理，多硬件后端的打通正是"轻量"在异构算力上的直接体现，也是 PR 编号已至 #1687 的成熟项目持续扩展覆盖面的常规动作。

## 3. 对项目的影响和潜在意义

- **降低部署门槛**：Thor 用户无需自行摸索环境，可依据 Dockerfile 一键复现运行环境，显著缩短上手时间。
- **扩大硬件覆盖**：使 Thor 成为框架正式支持的目标之一，向社区传递"多后端、多芯片可用"的信号，有利于在特定硬件生态（如国产/专用加速卡）中的落地。
- **提升可复现性**：容器化 + 明确配置文件，使推理结果与性能基准更易被第三方复现和对比，增强项目可信度。
- **配置即文档**：推理配置文件本身可作为 NeoPP 后端关键参数（步数、分辨率、调度策略等）的参考样例，减少用户试错成本。

## 4. 值得关注的技术点

- **Dockerfile 的构建策略**：是否采用多阶段构建、基础镜像选型以及 Thor 驱动/运行时的挂载方式，直接决定镜像体积与跨机器兼容性。
- **NeoPP 后端与 Thor 的适配深度**：配置项透露出 NeoPP 在 Thor 上的算子支持范围、显存管理与调度方式，是判断该后端成熟度的关键线索。
- **配置与主干的解耦程度**：新增配置是否通过统一的配置加载机制接入，而非硬编码，关系到后续新增硬件时的扩展成本。
- **CI 与镜像发布流程**：Dockerfile 是否纳入持续集成与镜像仓库自动发布，决定该支持是长期维护的还是一次性的。

## 5. 对项目发展的整体影响

结合 README 可知，LightX2V 由 ModelTC 维护、采用 Apache 2.0 协议，并提供中英双语文档，目标是打造一个轻量、开放、易部署的视频生成推理框架。本次提交延续了项目"在保持轻量的同时持续拓宽硬件适配边界"的发展主线：一方面通过 Docker 化把部署体验标准化，符合开源项目降低采纳门槛的普遍规律；另一方面以 NeoPP + Thor 的组合探索 GPU 之外的推理路径，为项目在异构算力时代的差异化竞争积累筹码。若后续能配套文档、基准测试与 CI 自动构建，该提交将成为 Thor 生态支持的起点，进一步巩固 LightX2V 作为多后端轻量推理框架的定位。

## 详细提交记录

### [e8ddf40](https://github.com/ModelTC/LightX2V/commit/e8ddf40d577b0f0310a25098d8f6ae387328b7ff)

- **作者**: STwangyingrui
- **时间**: 2026-11-10T13:48:22Z
- **提交信息**: Add Thor dockerfile and NeoPP Thor inference config (#1687)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-11-11
**监控日期**: 2026-11-10
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2329
- **最后更新**: 2026-11-10T16:59:35Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-11-11
**监控日期**: 2026-11-10
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6893
- **最后更新**: 2026-11-11T01:55:40Z

## 提交统计

- **昨日提交总数**: 35
- **提交者数量**: 26
- **主要提交者**: smoothsmooth, 0z5a, Brian K. Ryu

## AI分析总结

# FlashInfer 昨日提交合并分析总结

## 一、主要更新类型
昨日 35 个提交以**性能优化**为主线，辅以 **Bug 修复**、**功能新增**与**发布工程**。性能方向集中在 MoE、GEMM、采样、LayerNorm、KDA、通信融合等算子，并新增 Cake 训练内核变体、W8A16 FP8 GEMM、DeepSeek-V4.1 Prims-TS 解码后端与 NVFP4 MoE 候选；修复覆盖竞态、越界、内存序、并发正确性等隐蔽缺陷；期间完成 0.7.4 版本发布。

## 二、关键变更点
- **正确性加固**：RoPE 双修复（#9104、#4349）消除任意 rotary_dim/布局下的错误值、粘性 misaligned address 及越界读导致的跨头数据污染；TopK 多 CTA 补齐三处跨 CTA 屏障（#8832）；Rubin MTP 将 mbarrier 等待改为 cluster 作用域 acquire（#8856）；并发采样以进程内锁序列化 Philox 偏移预留（#9148），修复共享 CUDA Generator 被覆盖的问题。
- **性能优化**：MXFP8×MXFP4 MoE 引入容量感知默认配置（#9033，GB300 延迟降 1.3%–13.9%）；NVFP4 MoE 修正 N/K 配置并新增 N64 候选（#9245，最高约 4%），Frost 分组打包 NVFP4 带来 1.19–1.75× 加速（#7384）；KDA 在 B300 上 PTX prefill 达 3.5×（#9247）；确定性 top-p 采样用 32 位原子加替代 CAS 循环，最高 1.40× 且输出逐位一致（#8913）；LayerNorm 回退 32 位行偏移挽回 2.7–5.5% 回退（#8935）；Cake 稠密 GEMM 训练非确定性版（#9299）为 BF16 K1 内核族新增四个程序并重路由 B200/GB200/GB300/R200，B200 上 98 行测试中 81 行加速、最高 2.42×；Cake mHC 四流训练反向（#9297）修复反向内核与满占用旁路 CTA 共享 SM 时的启动问题。
- **融合与调度**：低 M BF16 GEMM 直写对端 Lamport 缓冲，边界时间降 5%–21%（#8945）；H100 backward kernel 寄存器压至 120 以实现与全占用 kernel 共存（#9037）；RTX 5090 通过路由表复用获 1.03×–1.22×（#9313）；TVM-FFI 启动将 SM90 MoE 主机开销降约 40%（#9246）；GEMM PDL 自动调优显著压缩冷启动（#8414）。
- **修复与工程发布**：NVFP4 在 SM107（Rubin）上的量化路由阈值回归修复（#9292），恢复 DeepSeek-V4-Pro 的 6.91us 性能；0.7.4 发布附带 cherry-pick 清单与 API 审计（#8876），并修复 release wheel 误删 HC JIT 源码（#9244）；MXFP8 CuTe-DSL 引入磁盘缓存与有界并行预编译（#6615）改善冷启动；`batch_invariant` 默认改为 False（#9295）并新增 fp8 确定性模式（#9280）；CI 改用临时文件替代 TCP 端口解决 EADDRINUSE（#8998）。

## 三、项目影响
这批工作呈双轮驱动：一方面系统性清理竞态、越界、内存序、并发 RNG 等隐蔽缺陷，提升生产可靠性并降低 vLLM/SGLang 等下游排错成本；另一方面在 Blackwell（SM100/103/107）与 Hopper（SM90）上持续压榨性能，并优化编译缓存、打包与启动体验。项目正越过"纯推理"边界向训练侧内核延伸，同时快速跟进 DeepSeek-V4.1、NVFP4/MXFP4 等新模型与低精度格式，巩固其作为可信赖 serving 基础设施与推理内核标杆的地位。

## 四、值得关注的技术点
- CuTe-DSL 正全面替代 CUTLASS C++，贯穿 GEMM、MoE、编译缓存三条线，降低构建复杂度。
- 寄存器子分区模型（四子分区各 16K、warp 按 8 对齐）解释了 121 与 120 寄存器决定 kernel 能否共存的精细调度；Lamport 双缓冲协议（epoch 交替、multimem.st 组播、PDL 依赖点）是通信原语设计的优秀范例。
- 按架构与形状分段路由取代全局阈值，表明 GPU 优化已进入按 SKU 精细化调参阶段。
- 分阶段带证据的调优文化：各 PR 附同 GPU 对照基准（CUPTI 时间、冷 L2 缓存、中位数、CUDA graph），并主动披露慢于主分支的行；部分候选（如 N64 grid）在特定形状下会反增延迟，需按条件筛选。
- `static_assert`、布局前置校验、设备守卫等防御式编程贯穿多个修复，形成分层防御。

以上工作共同巩固 FlashInfer 作为跨代 GPU 高性能推理内核库的地位，为后续硬件适配与生态整合铺平道路。

## 详细提交记录

### [a984f0f](https://github.com/flashinfer-ai/flashinfer/commit/a984f0f6e8c950571de8fbb12f5e0fd948ad1b0b)

- **作者**: 0z5a
- **时间**: 2026-11-10T23:25:15Z
- **提交信息**: fix(rope): make cos/sin cache RoPE correct for any rotary_dim and layout (#9104)

Fixes #9068.

`apply_rope_with_cos_sin_cache[_inplace]` and `rope_quantize_fp8`
returned wrong values or raised a sticky `misaligned address` error at
many head and rotary sizes. There are three separate causes:

| Cause | Hits on main | Result |
|---|---|---|
| `rotary_dim / 2` is not a multiple of the vector width, so one vector
gets the wrong partner and sign | neox at rotary 16, 48, 80; (512, 48) |
Wrong values |
| A tensor, sub-range or stride is not on 16 bytes | (24, 24), (40, 40),
(64, 20), (100, 32), (100, 40), (128, 24), (128, 40), including
StableLM-3B's (80, 20); any tensor starting off 16 bytes | `misaligned
address`, and every later CUDA call in the process fails |
| In place in the neox layout, a token's threads span two warps, so a
thread can read its partner after another warp stored over it | Heads
768 and 1024 on GH200 | Wrong values on some calls |

## Fix

- Sizes and layouts that miss the first two conditions go to kernels
that load and store one element at a time. The choice is made per call,
on the host.
- In place, threads per token are rounded up to a divisor of the warp
size, so a token stays in one warp. Above 32 threads there is no such
divisor, so those sizes use the element-wise kernels.
- Heads 64/128/256/512 keep their dedicated kernel wherever its limits
hold. The append path still rejects sizes that aren't multiples of 16.
- An odd `rotary_dim` now raises, and so does `rope_dim` 0 in
`RopeQuantize`, which used to divide by zero on the host.

## Results on GH200

**Issue repro:** main is OK on 42 of 48 rows and this PR on all 48. The
six wrong rows on main give the same errors as the issue's table (4.48,
1.90e37, 1.37e16, 4.75, 3.10e4, 721.7).

**In-place race:** share of calls with wrong values, at 64 tokens:

| Head = rotary | BF16 on main | FP16 on main | This PR |
|---|---|---|---|
| 768 | 90 % | 95 % | 0 % |
| 1024 | 33 % | 50 % | 0 % |

At head 768, every wrong element had its partner in another warp,
against 67 % of all lanes. This PR had 0 wrong calls of 93,240 across
heads 32, 64, 96, 192, 768 and 1024.

**Head 96 from the issue does not reproduce on GH200:** 0 wrong of
29,404 calls on main. It has the same layout, with a token spanning two
warps, so the rounding covers it, but I can't confirm that from here.
@weireweire, could you run your repro on this branch on GB300?

**Speed:** in place, neox, BF16, 4096 tokens, 32 + 8 heads, median of
200 calls, in µs:

| Head, rotary | main | This PR |
|---|---|---|
| 96, 96 | 50.8 | 45.9 |
| 192, 192 | 68.8 | 70.2 |
| 768, 768 | 210.8 (wrong values) | 587.4 |
| 1024, 1024 | 274.0 (wrong values) | 426.1 |
| 80, 80 | not comparable (wrong values) | 59.2 |
| 16, 16 | not comparable (wrong values) | 63.2 |
| 80, 20 | raises | 130.6 |

Above 32 threads per token, 768 and 1024 take the element-wise path,
which is slower but returns correct values. Times are measured on the
host and include the launch.

Sizes that keep their kernel, measured on an earlier revision of this
branch with the same test:

| Head, rotary | main | This branch |
|---|---|---|
| 64, 64 in place | 29.5 | 29.7 |
| 128, 128 in place | 43.1 | 42.0 |
| 512, 512 in place | 125.7 | 124.0 |
| 96, 96 out of place | 54.1 | 54.8 |
| 80, 32 out of place (Phi-2) | 53.1 | 54.1 |

Since that revision, the last two rows' kernel has gained one bounds
check per thread.

## Tests

- `test_rope.py` plus the append layout tests, in one process: 669
passed, 81 skipped.
- The new race test fails on main in 3 of 3 processes at heads 768 and
1024, BF16 and FP16, and passes with this PR in 3 of 3.
- Removing each guard makes the new tests fail. I ran those controls on
the previous revision of this branch, before the in-place rounding and
the element-wise kernel's new thread mapping.
- Compute Sanitizer memcheck reports no errors for (96, 96) in place.
(80, 20) was also clean on the previous revision, which takes the same
path at that size.

I ran everything on GH200 only. The rope sources are unchanged by the
rebase onto current main.

## Not changed

`apply_rope_pos_ids` has the same limits: on main it is wrong at (512,
48) neox and raises `misaligned address` at (64, 20), (128, 24) and
(128, 40). It computes cos/sin in the kernel, so it can't use this
routing and needs its own change.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved rotary embedding and quantization reliability across varied
rotary dimensions, unaligned data, and in-place operations, including
cases that cross warp boundaries.
* Improved paged-cache append behavior for quantized keys and values
across supported attention types and cache alignments.
* Improved consistency across data formats and launch configurations,
including FP8 quantization with distinct query and key/value scales.
  * Invalid zero or odd rotary dimensions are now rejected.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: 0z5a <dezhen.lu@student.uni-tuebingen.de>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [edac99f](https://github.com/flashinfer-ai/flashinfer/commit/edac99f9177685bfa16d9ca4a313cdbd39181450)

- **作者**: Leoy
- **时间**: 2026-11-10T22:55:05Z
- **提交信息**: fix(rope): guard rotary_dim <= head_dim to prevent silent cross-head corruption (#4349)

## 📌 Description

Adds a `head_dim < rotary_dim` guard across the RoPE surface, mirroring
the guard that already exists in `BatchQKApplyRotaryPosIdsCosSinCache`
(`include/flashinfer/pos_enc.cuh:1301`).

**Why this matters:** the RoPE kernel `vec_apply_llama_rope`
(`pos_enc.cuh:107-126`) computes `x + rotary_dim/2` with no bounds
check. When `rotary_dim > head_dim` (a misconfiguration that is easy to
hit when porting partial-RoPE configs between HF and vLLM — e.g.
`rotary_dim=192` on a `head_dim=128` tensor), the offset reads past the
current head's data into the adjacent head/token. The result is **silent
cross-head corruption**: no crash, no NaN — just wrong attention output
downstream, which is far harder to diagnose than a clear error.

Coverage in the final diff:

- **Native guards (four launchers that lacked one):**
`BatchQKApplyRotaryPosIds`, `BatchQKApplyRotary`,
`BatchQKApplyLlama31Rotary`, `BatchQKApplyLlama31RotaryPosIds`. The
check is mirrored from the existing one (`FLASHINFER_ERROR` +
`std::ostringstream`, same message wording) and placed at the top of
each launcher body before any kernel dispatch.
`BatchQKApplyRotaryInPlace` delegates to `BatchQKApplyRotary`, so it is
covered by that guard instead of carrying a duplicate.
- **Host-side guards (all eight public Python wrappers — four in-place,
four out-of-place):** a shared `_check_rotary_dim` raises `ValueError`
when `rotary_dim > min(q.size(-1), k.size(-1))`, naming both dimensions
in the message. It runs before any JIT/kernel work, and in the
out-of-place wrappers before the output tensors are allocated.
- The native guard sits before the interleave/non-interleave layout
selection, so both layouts are rejected.

## 🔍 Related Issues

Refs #4312 (the prefill `head_dim` validation PR) — same class of
"validate head_dim/rotary_dim at the launch boundary" fix; this covers
the RoPE side that #4312 does not touch. No filed issue exists for the
RoPE `rotary_dim` gap specifically — the corruption is silent, so it
tends to be attributed to model weights/config rather than the kernel.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] `ruff check` passes on the changed Python files
(`flashinfer/rope.py`, `tests/attention/test_rope.py`); `pos_enc.cuh` is
C++ (out of ruff scope).
- [ ] Full `pre-commit run --all-files` (mypy / codespell /
clang-format) deferred to CI — no local toolchain for the CUDA/mypy
parts.

## 🧪 Tests

All RoPE bound tests live in `tests/attention/test_rope.py`, next to the
other RoPE tests, and cover every public entry point
(`ROPE_ENTRY_POINTS`, eight wrappers):

- `test_rope_rotary_dim_exceeds_head_dim_raises` — parametrized over all
eight entry points and `rotary_dim` in `2 * head_dim` / `3 * head_dim`;
asserts the `ValueError` on CPU, i.e. the Python guard fires before any
kernel work, so this needs no GPU.
- `test_rope_rotary_dim_exceeds_smaller_qk_head_raises` —
`q_head_dim=128`, `k_head_dim=64`; asserts the message names both
dimensions (`head_dim (q=128, k=64)`).
- `test_rope_rotary_dim_equal_head_dim_does_not_raise` — `skipif(not
torch.cuda.is_available())`; the valid `rotary_dim == head_dim` case is
accepted, and the out-of-place wrappers exercise the native launcher's
own guard.

The out-of-place cases are included so the C++ guard is exercised, not
only the Python one.

## Reviewer Notes

- The guard is mechanical and byte-identical to the existing
`BatchQKApplyRotaryPosIdsCosSinCache` guard (`pos_enc.cuh:1301`), so
review should be short — it is "propagate the guard the team already
wrote to the launchers that missed it."
- The C++ guards are a backstop for direct TVM-FFI / JAX callers; the
Python guards cover the common Python-API path. Both layers mirror each
other.
- Pre-empting the "this is just user error" concern: agreed that
`rotary_dim > head_dim` is a caller misconfiguration, but the cost of a
host-side bounds check (one comparison per launch) is negligible, and
the alternative — silently wrong attention output attributed to model
weights — is materially worse for users debugging partial-RoPE setups.
The existing `BatchQKApplyRotaryPosIdsCosSinCache` guard (line 1301)
already encodes this judgment; this PR just makes it consistent across
the RoPE surface.

### [8fcb1f7](https://github.com/flashinfer-ai/flashinfer/commit/8fcb1f7449c7d435ecc8fd94bd88a55da608cc95)

- **作者**: Zixin Huang
- **时间**: 2026-11-10T21:53:12Z
- **提交信息**: fix(topk): order three cross-CTA group-state accesses in the multi-CTA radix kernels (#8832)

## Impact
Three cross-CTA races in the multi-CTA radix kernels of
`include/flashinfer/topk.cuh` can silently return wrong output when one
CTA of a group runs late. Nothing raises.

- `top_k_page_table_transform` (multi-CTA): some output slots keep stale
values instead of translated page entries.
- `top_k_renorm_probs`: a row with `k >= vocab_size` that follows an
ordinary row in the same CTA group can be normalized by `1 / 1e-8`
instead of `1 / sum`. In one witness the row's normalized probabilities
sum to 74869.9.
- `top_k_mask_logits`: an ordinary row's output can keep far more than
`k` elements (one witness keeps 299 instead of 128) when the same CTA
group then runs two `k >= vocab_size` rows.

The last two need a per-row `k` with at least one `k >= vocab_size` row,
and rows long enough to use more than one CTA per row. Which rows share
a CTA group depends on the SM count.

## Problem
The group barrier `AdvanceRadixGroupBarrier` orders only what happens
before it. Each race has a write that another CTA of the group can still
need, with no barrier in between:

1. **`RadixTopKKernel_Unified`, PageTableTransform, multi-CTA.** Every
thread writes raw indices to `row_output` in pass 2. Thread 0 then
arrives at the group barrier with `red_release`, and the peers translate
those slots through the page table. `red_release` releases only what the
CTA wrote before its last `__syncthreads()`, and there is no
`__syncthreads()` between the pass-2 writes and the arrival. A peer can
read a slot before a late warp of the writing CTA has stored it. #5251
added the same missing `__syncthreads()` at the per-round barriers; this
barrier was not covered.
2. **`RadixTopKRenormProbKernel_MultiCTA`, `k >= vocab_size` row.** CTA
0 resets `state->sum_topk` (or `sum_topk_fixed`) at the start of the
row. A peer reads the previous row's sum after that row's last group
barrier, with no barrier after the read. CTA 0 can reset the sum before
a slow peer reads it, and the peer then normalizes by `1 / max(0,
1e-8)`.
3. **`RadixTopKMaskLogitsKernel_MultiCTA`, `k >= vocab_size` rows.** A
trivial row has no group barrier, and CTA 0 clears `histogram[((iter +
1) * NUM_ROUNDS) % 3]` for the next row. After an ordinary row and two
trivial rows, the buffer cleared is the one the ordinary row's last
radix round reads. A slow peer is still reading it in that round and
picks the wrong pivot.

## Fix
- (1) `__syncthreads()` before the group barrier that publishes the
pass-2 `row_output` writes.
- (2) and (3) A group barrier before CTA 0 resets the sum or clears the
histogram, so every CTA of the group has finished the previous row
first. This adds one group barrier per `k >= vocab_size` row in these
two kernels and changes nothing for other rows.

The tail state reset (`RadixGroupResetStateLastCTA`) still sees the same
barrier count on every CTA of a group.

## Test
New tests in `tests/utils/test_topk.py`:
- `test_top_k_mask_logits_multi_cta_trivial_rows_after_ordinary_row`
- `test_top_k_renorm_probs_multi_cta_trivial_row_after_ordinary_row`
(deterministic and non-deterministic)
- `test_top_k_page_table_transform_multi_cta_publishes_all_indices`
(deterministic and non-deterministic)

Each test uses fp32 rows of length 128256 or 131072, so every row spans
several CTAs, and checks every row over 10 runs.
- Mask and renorm: the first `num_sms` rows are ordinary and the next `2
* num_sms` rows have `k >= vocab_size`, so every CTA group sees the
triggering sequence for any SM count. The output is compared with a
torch reference.
- Page-table transform: scores take four values, so every selected index
ties with the pivot and all `k` slots are written in pass 2. The output
buffer is prefilled with a sentinel and the page table maps `i -> 2 * i
+ 1`; every output must be a translated, in-range, unique index whose
score is at least the k-th largest.

These races need a peer CTA to be late, so plain runs rarely trigger
them: a plain stress loop did not trigger (1) in 300 runs. The tests
guard the triggering row sequences, but without injected delays they
will usually pass on unfixed `main` too. We found and witnessed each
race on B200 (148 SMs) by injecting delays into chosen CTAs and warps
(CTA 0's odd warps for (1), every other CTA after the group barrier for
(2) and (3)). The fixed kernels are clean under the same delays.

Run:
```
pytest tests/utils/test_topk.py -k "multi_cta_trivial_row or multi_cta_publishes_all_indices" -v
```

The B200 run of the new tests and the existing top-k and sampling tests
with this change is in progress and will be posted as a comment.

#4131 (open) converges the CTA before every group-barrier arrival, which
would also cover (1), but not (2) or (3). #4126 (a crash in
`RadixTopKRenormProbKernel_MultiCTA` on sm_103) may be related; this PR
does not claim to fix it.

cc @aleozlx @bkryu

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved reliability of top-k masking, probability renormalization,
and page-table transformations in multi-CTA operations, including
batches that mix different top-k sizes. This helps ensure selected
indices are translated consistently and results remain valid when
processing rows with different top-k requirements.
* **Tests**
* Added repeated regression coverage for these multi-CTA scenarios,
including checks for valid, non-duplicate transformed indices.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [823173d](https://github.com/flashinfer-ai/flashinfer/commit/823173dc4e94e3606cfe4aa19b0f9727c7a2e03c)

- **作者**: Yuheng Cai
- **时间**: 2026-11-10T21:47:36Z
- **提交信息**: perf(norm): keep 32-bit row offsets in CUDA LayerNorm when they fit (#8935)

<!-- .github/pull_request_template.md -->

## 📌 Description

Follow-up to #8378, addressing two non-blocking review comments left
there by kahyunnam.

**1. 32-bit row offsets when they fit.** #8378 made every
`generalLayerNorm` row offset 64-bit. Its review measured contiguous
rows on B200 2.7–5.5% slower than before at hidden=2048. The per-tensor
fp8 path (`LayerNormQuant`) uses the same kernel with both strides set
to `hidden_dim`, so it slowed down too. This PR templates the kernel on
its index type. The host selects `int32_t` when `tokens *
max(input_stride, output_stride) + hidden_dim` fits in int32, and
`int64_t` otherwise. A stride of 0 (broadcast rows) is covered because
`hidden_dim` is part of the bound.

**2. Backend-specific docstring.** The default CuTe DSL backend does not
accept arbitrary row strides. On A100 at `main` it raises `ValueError`
for row stride 129 ("Invalid mX.strides[0]") and for a 2-byte input
offset ("Misaligned Tensor data"). Row stride 144 with a 16-byte offset,
padded rows (stride 256) and broadcast rows work. The CUDA backend
accepts all six layouts. The `layernorm` docstring now says this per
backend.

**Measurements.** A100-SXM4-40GB, CUDA 13.0, torch 2.11, bf16,
`FLASHINFER_USE_CUDA_NORM=1`. Times are median kernel time in µs from
`bench_gpu_time(use_cuda_graph=True)` with a cold L2, averaged over two
alternating rounds. Each build runs in its own process and JIT
workspace. *before* is `main` with the two #8378 kernel/binding files
reverted.

| op | hidden | tokens | before #8378 | `main` | this PR | `main` vs
before | this PR vs before |
|---|---|---|---|---|---|---|---|
| layernorm | 1024 | 32768 | 374.1 | 399.1 | 398.6 | +6.7% | +6.6% |
| layernorm | 2048 | 1024 | 17.7 | 18.5 | 18.1 | +4.6% | +2.3% |
| layernorm | 2048 | 8192 | 113.8 | 119.9 | 118.2 | +5.4% | +3.9% |
| layernorm | 2048 | 32768 | 442.4 | 466.7 | 460.2 | +5.5% | +4.0% |
| layernorm | 4096 | 32768 | 621.9 | 669.0 | 651.4 | +7.6% | +4.7% |
| layernorm | 8192 | 32768 | 1088.7 | 1128.6 | 1083.2 | +3.7% | −0.5% |
| layernorm_quant | 1024 | 32768 | 481.7 | 534.5 | 495.4 | +11.0% |
+2.8% |
| layernorm_quant | 2048 | 32768 | 706.9 | 748.6 | 723.9 | +5.9% | +2.4%
|
| layernorm_quant | 4096 | 32768 | 1109.0 | 1204.6 | 1127.5 | +8.6% |
+1.7% |
| layernorm_quant | 8192 | 32768 | 1982.8 | 2105.2 | 1996.0 | +6.2% |
+0.7% |

- Across the full grid (hidden 1024–8192, 1–32768 tokens), this PR is
between −7.5% and +3.1% against `main`. It is slower in only one cell:
plain, hidden 1024, 1 token, at about 3.4 µs, where the two rounds
varied by 6%.
- A second pair of rounds in reverse build order (hidden 1024 and 2048)
reproduced the 8192- and 32768-token numbers to within 0.5%. The
1024-token cases varied more.
- **On A100 this does not fully close the gap for plain `layernorm`.**
It still runs 2–7% slower than before #8378 at hidden ≤ 4096. The quant
path is within about 3%.
- For the plain bf16 shared-memory kernel, the `int32_t` instantiation's
SASS is 320 instructions versus 312 before #8378, and its loads, stores
and integer address arithmetic match. The remaining differences are a
few uniform-register instructions for the signed divide of the int64
stride parameters, plus instruction reordering around the block
reductions.
- An unsigned divide removed under 1% and did not change the instruction
count, so it is not included.
- All variants use 22–32 registers, so occupancy at 1024 threads is
unchanged. I do not know where the remaining plain-path gap on A100
comes from. B200 numbers, which the review had, would show whether it
exists there.

## 🔍 Related Issues

Follow-up to #8378 (review comments on `include/flashinfer/norm.cuh` and
`flashinfer/norm/__init__.py`).

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues. (Run as `pre-commit run --files` on the
three changed files; all hooks passed.)

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.). Targeted tests listed
below; the full library suite was not run.
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/utils/test_norm.py`

On A100 (SM80), CUDA 13.0, PyTorch 2.11.0+cu130, `main` at `3757bab3`:

- `FLASHINFER_USE_CUDA_NORM=1 pytest tests/utils/test_norm.py -k
layernorm`: 197 passed, 169 skipped. This covers the 10 row-stride cases
from #8378 and the existing LayerNorm and quant cases.
- New `test_layernorm_cuda_row_offset_beyond_int32` places the second
row at element offset 2³¹ + 1. The odd stride selects the scalar path,
where offsets count single elements. The test needs about 5 GB of free
GPU memory and skips otherwise.
- With the 64-bit path forced off, the same test fails with
`cudaErrorIllegalAddress`. With this PR it passes.
- The docstring change was not rerun; the kernel and test diff is
byte-identical to the one tested.
- No non-A100 validation is claimed.

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

AI assistance was used for implementation, tests and measurement. The
selection bound is the main thing to check. It is computed in scalar
elements, while packed offsets are at most half of that. It includes
`hidden_dim` so that broadcast rows (stride 0) and the last row's tail
are covered. The `generalLayerNorm` instantiations double. I did not
measure the JIT compile time.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* LayerNorm now supports tensors with row offsets beyond the 32-bit
range when using the CUDA backend.
* **Documentation**
* Clarified that the default CuTe DSL backend requires row strides to
meet its vector-width alignment and data pointers to be 16-byte aligned.
The CUDA backend accepts any row stride and is selected with
`FLASHINFER_USE_CUDA_NORM=1` or when CuTe DSL is unavailable.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [a26df10](https://github.com/flashinfer-ai/flashinfer/commit/a26df10c81a30998c5ac604a55122c1ff3aad9cb)

- **作者**: smoothsmooth
- **时间**: 2026-11-10T21:34:00Z
- **提交信息**: KDA for KDA updated: 3.512x speedup (#9247)

<!-- .github/pull_request_template.md -->

## 📌 Description

Optimize the existing explicit `backend="ptx"` KDA prefill path on B300.
The updated revision achieves a six-workload geometric mean speedup of
**3.509× over raw FlashKDA**. The **original PR measurement was
3.512×**.

The latest measurement includes the review fixes and the explicit
dual-stream completion dependency before fixed-split correction, with
redundant global dual-completion counters removed. These review fixes
are now included in the PR at
[`a28516b2`](https://github.com/smoothsmooth/flashinfer/commit/a28516b265db362f8aeab5574ab630b021eac0c4).
The measurements below were taken from the matching implementation.

### Latest measurement (review fixes applied)

| Workload | FlashKDA (ms) | PTX public API (ms) | Speedup vs FlashKDA |
|---|---:|---:|---:|
| h96-fixed | 1.001561 | 0.286210 | 3.499× |
| h96-mixed_varlen | 0.878407 | 0.239170 | 3.673× |
| h96-uniform_varlen | 0.715013 | 0.231170 | 3.093× |
| h64-fixed | 0.907400 | 0.231826 | 3.914× |
| h64-mixed_varlen | 0.657525 | 0.165890 | 3.964× |
| h64-uniform_varlen | 0.483381 | 0.159570 | 3.029× |

In a fresh before/after check on the same allocated B300, the previous
synchronization version remeasured at **3.515×**, versus **3.509×**
after the synchronization correction. The geometric mean candidate GPU
latency increased by **0.214%**; FlashKDA latency increased by
**0.065%**. These sequential measurements are point estimates, not a
claim of statistical significance. Each speedup uses its own paired
FlashKDA baseline.

<details>
<summary>Original PR measurement: 3.512× geometric mean
speedup</summary>

Retained for comparison. These are the originally published
measurements, before the review fixes; they are not substituted for the
latest baseline.

| Workload | FlashKDA (ms) | PTX public API (ms) | Speedup vs FlashKDA |
|---|---:|---:|---:|
| h96-fixed | 1.000123 | 0.285556 | 3.502× |
| h96-mixed_varlen | 0.875115 | 0.238595 | 3.668× |
| h96-uniform_varlen | 0.714296 | 0.231107 | 3.091× |
| h64-fixed | 0.905882 | 0.229747 | 3.943× |
| h64-mixed_varlen | 0.656888 | 0.165553 | 3.968× |
| h64-uniform_varlen | 0.482837 | 0.159826 | 3.021× |

</details>

- Split a fixed long sequence into a prefix and parallel
zero-state/identity-state tail recurrences, followed by correction
retaining the full recurrence. State storage is FP32; state composition
uses TF32 products and output correction uses BF16 state operands, both
with FP32 accumulation under the validated reference tolerances. Join
dual-tail completion before launching correction.
- Improve piece packing, state handoffs, identity-token padding for
partial pieces, V prefetch, state-conversion/MMA overlap, and
deferred-decay PTX variants.
- Reuse FlashInfer's shared recurrence, fallback, front end, host shim,
per-plan TMA descriptors, and public workspace handling. Preparation
preserves aliased initial/final state; native FP32 stores apply the
public in-place update directly, eliminating an intermediate state
buffer and copy.
- Prefer driver JIT when the driver supports PTX ISA 9.2. Preserve the
ptxas/cubin fallback for older CUDA 13 drivers; the benchmark records
the selected image kind and NVIDIA driver version.
- Select the optimized schedules only for the six validated layouts on
148-SM SM103 devices. Other layouts use the existing scheduler. The
public signature and explicit backend selection are unchanged.
- Retain four additional PTX programs with content and
instruction-stream checksums. Publication comments are normalized
without changing instructions.

Operator: **Kimi Delta Attention**. Inputs are contiguous BF16, B=1,
T=8192, H=96/64, D=128, with FP32 state. Sequence lengths are `[8192]`,
`[1300, 547, 2048, 963, 271, 3063]`, or `[1024] * 8`.

Baseline:
[MoonshotAI/FlashKDA](https://github.com/MoonshotAI/FlashKDA/tree/7afb9f454f160a6c4bbc0999beca0a8c40a38934),
raw fused CUTLASS entry point, revision `7afb9f4`. Both implementations
were measured on the same physical **NVIDIA B300 SXM6 AC**, 148 SMs,
with PyTorch 2.14.1+cu130, CUDA runtime 13.0, a CUDA-13.4-capable NVIDIA
615.71.10 driver (driver PTX JIT for the optimized result; ptxas 13.2
available for fallback), Triton 3.6.0, and TVM FFI
0.1.13.dev57+gd1fd51222.

Both arms update FP32 state in place. Each graph is captured once; state
evolves during timed repetitions and resets to identical initial values
outside each trial. Timing uses cold-L2 CUPTI GPU activity spans, 3
warmup iterations, 30 measured iterations, and 3 trials with alternating
arm order; reported latency is the median of trial medians. Allocation,
compilation, planning, capture, and state reset are outside timing. All
GPU work launched by the public API is included, including split
correction and native in-place state stores. No extra state copy is
required. These numbers measure GPU execution, rather than CPU-inclusive
end-to-end latency.

Both candidate output/final state and FlashKDA output/final state pass
an independent FLA `chunk_kda` reference on every workload: relative L2
≤ 0.03, finite outputs, and per-element error ≤ `max(0.5 *
RMS(reference), 0.05 * abs(reference))`.

Reproduce with a clean FlashKDA checkout at the revision above, built in
place for SM103a, plus `fla-core==0.5.2` and `cupti-python`:

```bash
python benchmarks/bench_recurrent_kda_ptx.py \
  --flash-kda-source-dir ../FlashKDA --output results.json
python -m pytest -q tests/kda/test_recurrent_kda_ptx.py
```


## 🔍 Related Issues

Follow-up to #5665.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

All hooks passed on the changed files using `pre-commit run --files
...`, including Ruff 0.12.8 and mypy. Repository-wide `--all-files`
checks and hook installation are left unchecked above.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

Targeted validation after the review fixes: **52 passed** in
`tests/kda/test_recurrent_kda_ptx.py` on B300, including all six INT21
layouts, nondefault streams, graph replay with changed inputs, weak
decay, zero norms, state ownership, invalid-contract checks, and
preparation with aliased initial/final state. The full repository suite
was not run. The direct-state cubin path also passed all 50 tests before
enabling driver PTX JIT.
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: Not requested; the change is scoped to the existing PTX KDA
backend.

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/kda/test_recurrent_kda_ptx.py`

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

Review the exact split composition, side-stream joins, per-plan mutable
workspace ownership, and in-place state update. The existing
numeric-domain restrictions and fallback scheduler remain in effect.
Review the CUDA-driver-version selection and the older-driver cubin
fallback as well. Approximate splitting and expected-norm substitution
are disabled by the adapter. No new environment variables, AOT
registrations, or backend="auto" routing changes are introduced.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added optimized KDA execution for six supported long-sequence layouts
on compatible NVIDIA GPUs. Other workloads continue to use existing
execution paths.
* Added direct PTX loading on newer CUDA drivers, with a compiled
fallback for older supported drivers.
* **Documentation**
* Updated KDA guidance with workload and hardware eligibility, driver
requirements, and execution behavior.
* **Bug Fixes**
* Improved handling of KDA state inputs and one-dimensional bias values.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yahui Cui <smoothsmooth@users.noreply.github.com>

### [241c1e4](https://github.com/flashinfer-ai/flashinfer/commit/241c1e475ef93f0f43f400089c0003a8292e3451)

- **作者**: Ziming Wang
- **时间**: 2026-11-10T21:32:48Z
- **提交信息**: perf(sampling): accumulate deterministic AIR top-p bins with native 32-bit atomics (#8913)

## 📌 Description

the deterministic AIR top-p renorm (`top_p_renorm_probs(...,
is_deterministic=True)` on rows of 2048 or more elements) sums float
mantissas per radix bin with a 64-bit integer `atomicAdd` on shared
memory. there's no native 64-bit integer add for shared memory, so every
one of those adds compiles to a compare-and-swap loop
(`ATOMS.CAST.SPIN.64` in nvcc 13.4 SASS for sm_80, sm_90, sm_100a and
sm_120), while a 32-bit integer add is a single `ATOMS.ADD`.

this PR keeps each bin's 64 bits of shared storage but accumulates the
mantissa there as two 32-bit words, the high 11 bits and the low 12
bits, and folds them back into the existing 64-bit global histogram when
the block publishes its bins. the global histogram, the threshold search
and the output path don't change.

a block only scans part of its own row, so the scanned length bounds
every bin's count. below 2^20 elements neither word can overflow, since
(2^20 − 1)(2^12 − 1) < 2^32, and `(hi << 12) + lo` is the exact 64-bit
sum, so the output is bitwise identical to the 64-bit path. rows of 2^20
elements or more keep the 64-bit adds. only the `float` instantiation is
deterministic today, and a `static_assert` ties the split to 64-bit
histogram storage.

### performance

H100 80GB HBM3, CUDA 12.9, torch 2.8 (NGC 25.06), base `11aa7628b`. each
configuration replays 50 `top_p_renorm_probs` calls in a CUDA graph and
takes the median of 7 replays, the better of two interleaved rounds per
build. the table shows the median over temperature 0.7 and 1.0 and top_p
0.5 and 0.9, in µs per call.

| vocab | batch | deterministic, main | deterministic, this PR | speedup
| non-deterministic |
| ---: | ---: | ---: | ---: | ---: | ---: |
| 32000 | 1 | 37.5 | 35.8 | 1.05x | 34.1 |
| 32000 | 128 | 82.5 | 58.8 | 1.40x | 66.9 |
| 32000 | 1024 | 511.4 | 378.3 | 1.35x | 408.2 |
| 128256 | 1 | 72.4 | 70.8 | 1.02x | 68.2 |
| 128256 | 16 | 93.2 | 81.2 | 1.15x | 84.8 |
| 128256 | 128 | 296.3 | 211.8 | 1.40x | 245.3 |
| 128256 | 1024 | 1800.8 | 1143.1 | 1.58x | 1424.3 |
| 151936 | 128 | 344.7 | 243.9 | 1.41x | 284.9 |
| 151936 | 1024 | 2116.1 | 1330.7 | 1.59x | 1675.3 |
| 1100000 | 1 | 406.0 | 406.3 | 1.00x | 398.2 |
| 1100000 | 8 | 789.2 | 786.7 | 1.00x | 759.1 |

across the full sweep of 92 configurations (vocab 32000, 128256 and
151936 at batch 1 to 1024, plus 1.1M-element rows), the deterministic
output has the same SHA-256 on main and on this PR, repeated
deterministic calls stay bitwise equal, and the non-deterministic
timings agree within 2.4%. from batch 64 up the deterministic path now
takes 0.79x to 0.93x of the non-deterministic time at vocab 128256 and
151936 and 0.88x to 1.05x at vocab 32000, against 1.16x to 1.27x on
main. the 1.1M-element rows keep the 64-bit adds and their time doesn't
move.

with nvcc 13.4 the split raises the deterministic radix kernel from 32
to 40 registers on sm_90, which lowers residency from 4 to 3 blocks of
512 threads per SM. the timings above already include that, and sm_100a
was at 38 registers before this change.

### tests

`test_top_p_renorm_probs` runs with `is_deterministic` off and on,
skipping the deterministic case for rows narrower than 2048, which use
the ternary search path, and checks that repeated deterministic calls
are bitwise equal. `test_top_p_renorm_probs_deterministic_wide_rows`
covers 2^20 − 1 elements (split words) and 2^20 (64-bit words) against a
float64 sorted reference. it checks the kept set with one token of slack
at the cumulative-mass boundary, the renormalized values with
`rtol=1e-3, atol=0`, and repeat equality.

on the head, `pytest tests/utils/test_sampling.py -k top_p_renorm` on
the same H100 gives 71 passed and 12 skipped, and the 12 skips are the
deterministic cases at vocab 111.

## 🔍 Related Issues

#8404 documents the deterministic switches and states the deterministic
top-p overhead. with this change the deterministic path is within 5% of
the non-deterministic one or faster on H100 from batch 64 up, so
whichever of the two lands second should update that sentence. both PRs
also append to `test_top_p_renorm_probs`.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks on the changed files (`pre-commit run --files
...`) and fixed any reported issues.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/utils/test_sampling.py`


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved deterministic top-p probability renormalization, including
for large vocabularies. Repeated deterministic calls now produce
consistent results, with retained probabilities normalized correctly.
* **Tests**
* Expanded coverage for deterministic and non-deterministic modes,
including large vocabulary sizes and checks of retained-token selection
and probability normalization.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: ZenAlexa <zimingwang945@gmail.com>

### [52da258](https://github.com/flashinfer-ai/flashinfer/commit/52da2580d120e6a45fc1f2f493092fbadee91928)

- **作者**: Bastian Hagedorn
- **时间**: 2026-11-10T20:39:22Z
- **提交信息**: fix(attention): acquire at cluster scope on the Rubin MTP correction-factor wait (#8856)

## 📌 Description

In `flashinfer/cute_dsl/attention/rubin_mtp/kernel.py` the QK CTA writes
each tile's `(row_sum, row_max)` into the **peer** CTA's `smem_corr`
slot with `cute.arch.store_async_dsmem(slot_ptr, ...,
cor_full_mbar[stage], dsmem_data_peer)`, an `st.async ...
mbarrier::complete_tx` whose complete-tx is a release at `.cluster`
scope by the QK CTA's thread. The reader then runs
`common_params.cor_full_mbar.wait(index, phase)`, which is
`pipeline.MbarrierArray.wait` and lowers to `mbarrier.try_wait.parity`
with no scope qualifier, i.e. `.acquire.cta`, and reads `smem_corr[tidx,
w, stage]`. Under the PTX memory model a CTA-scope acquire only
synchronizes with releases by threads of the same CTA, so that read has
no happens-before edge to the peer's store. The comments around the
producer (near the `store_async_dsmem` call and at the consumer's wait
helper) say the wait acquires at cluster scope, but the emitted PTX is
`.acquire.cta`; the TMA analogy in the `_wait_cluster_mbarrier`
docstring does not apply here because the releasing agent is the peer
CTA's thread, not this CTA's async proxy.

**Change**: a `_wait_cluster_mbarrier_acquire` helper and its use at
that one wait. The helper is a `@cute.jit` loop over
`cutlass.experimental.primitives.mbarrier_try_wait_parity(...,
scope=MBarrierScope.CLUSTER)`, which lowers to
`mbarrier.try_wait.parity.acquire.cluster` (the spelling the cuDNN Frost
gather kernels in this tree already use); `cute.arch.mbarrier_wait` has
no scope argument. The first revision used the inline-asm spin from
`dense_bf16_gemm_sm100_splitk.py` (#7443), the second commit replaces it
so the scope is visible to the compiler. The other waits are left alone:
the `p_full` / UMMA rendezvous is consumed by the async proxy, and the
remote-arrive helper is a WAR hand-back where CTA scope is fine.

No wrong result was observed on hardware, and I do not expect one on
current parts: payload and complete-tx travel together on the DSMEM
path. The ISA does not promise that. The cost is one `.acquire.cluster`
wait per tile in the correction path; if that is measurable in your
benchmarks, I would like to know, and this PR can stay a draft until
then.

## Update (2026-11-10): relaxed cluster wait plus restricted acquire
fence

The wait is now `mbarrier.try_wait.parity.relaxed.cluster` followed by
`fence.acquire.sync_restrict::shared::cluster.cluster`, the PTX ISA's
own form for acquiring shared memory through the generic proxy (the
acquire pattern of section 8.8, and the fence's documented example). A
plain `.acquire.cluster` wait has to cover global memory as well, so
ptxas emits an L1 invalidate (`CCTL.IVALL`) after every try_wait; the
restricted fence covers only shared memory and emits no SASS
instruction. On sm_100a with ptxas 13.0 the `.acquire.cluster` form
costs two `CCTL.IVALL` per wait loop and this form none, with no extra
`MEMBAR`; the sm_107a build shows the same two fewer `CCTL.IVALL` and
otherwise identical instruction counts. That removes the per-tile cost
the description above worried about. Both forms are
`cutlass.experimental.primitives` wrappers in nvidia-cutlass-dsl 4.8.0,
the version this repository pins; the kernel compiles for sm_107a with
4.8.1.

## 🔍 Related Issues

#7443 (same change in the bf16 split-K GEMM); the two blockscaled
split-K GEMMs get the same fix in #8853.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues. (ruff 0.12.8 check + format and codespell
on the changed file; mypy not run.)

## 🧪 Tests

- [ ] Tests have been added or updated as needed. (Not applicable:
memory-model conformance, no observable failure to test for.)
- [ ] All tests are passing (`unittest`, etc.). (Not yet run on CI. The
kernel compiles for sm_107a with the change.)
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).

Suggested CI test targets: `tests/attention/test_rubin_mtp_native.py
tests/attention/test_rubin_mtp_reducer.py`

## Reviewer Notes

Opened as a draft for the Rubin MTP authors: the change is one wait, but
it is on the per-tile path.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved synchronization when reading attention correction metadata,
helping ensure it is available before use.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [4fb4db0](https://github.com/flashinfer-ai/flashinfer/commit/4fb4db0920d0b57c037bb3df52818ee34878a971)

- **作者**: Artem Perevedentsev
- **时间**: 2026-11-10T19:07:11Z
- **提交信息**: perf(gemm): mm_bf16 pdl=True autotunes every backend; pdl=None now the same as pdl=False (#8414)

Couple of days ago I added pdl=None option for gemmBF16 to allow
autotunner to sweep through both kernels that support PDL and that does
not support PDL. This PR was merged
https://github.com/flashinfer-ai/flashinfer/pull/8032
But after that I did some more manual e2e vllm model runs with cold-run
autotuning of gemmBF16 and realized that 20-30 minutes it takes to
autotune gemmBF16. After that I decided to stop using pdl=None and to
abandon breaking API now this PR considers pdl=None the same as
pdl=False. At the same time this PR extend logic behind pdl=True sweep
by these:
1) pdl=True mode now sweeps through both: kernels that support PDL and
kernels that do not support PDL
2) If kernel has both versions with PDL and without PDL then autotuner
runs only PDL version of this kernel because based on my experience with
real models using vllm there is no evidence that there is a case when
kernel that does not enable PDL better performs than the same kernel
with PDL enabled

Probably this change should help to cut down autotuning time.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

## Behavior Changes

* BF16 matrix multiplication now defaults to PDL being disabled instead
of automatically profiling both PDL modes.
* Enabling PDL uses it with supported backends, including TGV, TinyGEMM,
and CuTeDSL. Explicitly selecting CUTLASS or cuBLASLt with PDL enabled
remains unsupported; automatic backend selection may still choose them
without PDL.
* Autotuning now uses the operation name corresponding to the selected
PDL setting.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Artem Perevedentsev <aperevedents@nvidia.com>

### [6abdf8b](https://github.com/flashinfer-ai/flashinfer/commit/6abdf8b0dad1e23e8e7da56d12992c4f2f465fe7)

- **作者**: NVJiangShao
- **时间**: 2026-11-10T18:01:40Z
- **提交信息**: fix(build): retain HC JIT sources in release wheels (#9244)

<!-- .github/pull_request_template.md -->

## 📌 Description

Release wheel post-processing removes the two CUDA sources required by
the HC backend from #8944, even though its Python API is included. With
`FLASHINFER_WHEEL_EXCLUDE_EXPERIMENTAL_SOURCES=1`, HC preparation
therefore fails its source-availability check.

Retain exactly `hc_sum_sm100/csrc/binding.cu` and `kernels.cuh` (7,372
bytes uncompressed), while continuing to trim other experimental source
entries. Update the omission marker and installation guidance. HC
remains experimental and JIT-only; no kernel or AOT registration changes
are included.

## 🔍 Related Issues

Follow-up to #8944.

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

Scoped pre-commit checks pass for all six changed files. Repository-wide
`pre-commit run --all-files` was not run.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust):
`tests/cpu/infra/test_build_backend_slim_wheel.py`

```bash
PYTEST_DISABLE_PLUGIN_AUTOLOAD=1 python -m pytest --confcutdir=tests/cpu tests/cpu/infra/test_build_backend_slim_wheel.py -q
```

- Existing suite before changes: 4 passed.
- New regression before the fix: release case failed; source-enabled
case passed.
- After the fix: 6 passed, including actual HC source-byte preservation,
RECORD hashes/sizes, and continued exclusion of an extra HC source.
- Installed-style source preflight (local, not committed): rejected the
old synthetic release wheel and accepted the fixed one.

These tests exercise the real wheel post-processor with synthetic wheels
containing the repository HC source files. No full wheel build or GPU
test was run for this packaging-only change.

## 🔬 Experimental Track

<!-- Only for PRs submitted under the experimental policy
(CONTRIBUTING.md → "Experimental APIs and Backends").
     Leave this section untouched for normal PRs. -->

- [x] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.
Tracking issue: not yet assigned (existing feature from #8944).
- [ ] The tracking issue names an owner, the reason for the experimental
path, and a graduation plan with a target release.
- [ ] Core changes are limited to a thin entry point (signature, shared
validation, feature-gate check, backend selection, handoff).
- [ ] Tests live in `tests/experimental/` and were validated on the
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
tests/experimental/test_hc_sum_sm100.py
```

## Reviewer Notes

The new regression lives with the existing CPU wheel-packaging tests.
The experimental test target above names the existing HC suite for CI;
its CUDA implementation is unchanged. This change affects wheels built
from this revision and does not retrofit previously published artifacts.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Release wheels now retain the HC sum-state JIT sources even when
experimental-source exclusion is enabled. Other experimental sources
matched by the exclusion continue to be omitted.
* APIs that require omitted sources can still be imported, but fail when
compiling a kernel that needs those sources.

* **Documentation**
* Updated guidance explains which sources remain in release wheels and
where to turn when required sources are missing.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: Jiang Shao <91270701+StudyingShao@users.noreply.github.com>

### [74a0440](https://github.com/flashinfer-ai/flashinfer/commit/74a04401c67f8dd6d64527562860a20c8bc8afc8)

- **作者**: Brian K. Ryu
- **时间**: 2026-11-10T17:26:48Z
- **提交信息**: fix(batch_invariant): `sampling.log_probs` / `sampling.log_softmax` default to `batch_invariant=False`. (#9295)

<!-- .github/pull_request_template.md -->

## 📌 Description

Follow-up to #8999. The two entries it added defaulted to
`batch_invariant=True` and raised `ValueError` on `False`. That is the
wrong shape for the flag: on `softmax` it means "`True` runs the pinned
batch-invariant class `lse.row`, `False` runs the operator's regular
kernel", and a future, faster non-invariant kernel for `log_probs` /
`log_softmax` would have had no place to go. This change makes both
entries default to `False`, and `False` routes to the operator's regular
kernel for the entry, which today is the batch-invariant class itself,
so both values give the same bits now. `True` stays the pinned contract
(the fingerprint, the batch / position / SM-count invariance, run-to-run
determinism); callers that need the contract pass `True` explicitly, as
they do for `softmax`.

No kernel, dispatcher or numerics change; the class's fingerprints are
untouched. Docstrings and the README's Sampling rows describe the two
values; the tests that asserted the `ValueError` on `False` now check
that `False` takes the same path (device-free the device check follows
the flag; on the device `False` and `True` give the same bits as the
class).


<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

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

- [ ] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).
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

* **Updates**
* `log_probs` and `log_softmax` now default to `batch_invariant=False`.
* Setting `batch_invariant=False` no longer raises an error; it
currently produces the same results as `True`.
* **Documentation**
* Updated the sampling guide to describe the behavior of both
`batch_invariant` settings.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [bf1d290](https://github.com/flashinfer-ai/flashinfer/commit/bf1d29092ae43913cf04c509454666dc42031ed3)

- **作者**: Aurelien Chartier
- **时间**: 2026-11-10T16:06:29Z
- **提交信息**: perf(moe_ep): select MXFP4 defaults by expert fill and FC1 depth (#9033)

<!-- .github/pull_request_template.md -->

## 📌 Description

The MXFP8 × MXFP4 standard MoE backend currently inherits MXFP8 tuning
defaults. Give it capacity-based defaults that select N64 below 64
expected routed rows per expert and N128 otherwise. Use grouped
scheduling for shallow FC1 work and phase interleaving from 128 rows per
expert when FC1 work reaches seven tiles per active cluster.

Preserve explicit tile/scheduler overrides, including phase-only hints
and static-claim overrides. Validate legacy schedule values, use the
kernel's cached occupancy probe, and collectively check validation
errors during explicit workspace creation, then configurations and
preparation errors before pool lookup and symmetric allocation. Add
configuration and public-API GPU tests.

Same-GPU GB300 EP2/EP4 comparisons against the inherited upstream
defaults: H4096, I6400, eight experts, top-2, random routing. Each
comparison uses the same GPUs, weights and routing for both arms.
Latency is microseconds, mean of seven round medians; cold-L2 CUPTI
timing of pre-staged CUDA-graph kernel execution, taking the per-sample
maximum across ranks. Negative changes mean lower latency.

| EP | Tokens/rank | Upstream (µs) | This PR (µs) | Latency change |
|---:|---:|---:|---:|---:|
| 2 | 32 | 70.896 | 66.528 | -6.16% |
| 2 | 128 | 74.252 | 68.985 | -7.09% |
| 2 | 192 | 74.096 | 69.948 | -5.60% |
| 2 | 256 | 90.460 | 81.669 | -9.72% |
| 2 | 512 | 100.483 | 99.221 | -1.26% |
| 2 | 768 | 134.080 | 123.239 | -8.09% |
| 2 | 1024 | 159.881 | 146.005 | -8.68% |
| 4 | 32 | 65.001 | 62.414 | -3.98% |
| 4 | 128 | 69.968 | 67.881 | -2.98% |
| 4 | 256 | 90.389 | 77.868 | -13.85% |
| 4 | 384 | 94.055 | 90.944 | -3.31% |
| 4 | 512 | 108.746 | 99.596 | -8.41% |
| 4 | 513 | 102.727 | 97.790 | -4.81% |
| 4 | 640 | 119.431 | 109.950 | -7.94% |
| 4 | 641 | 119.207 | 109.813 | -7.88% |
| 4 | 768 | 137.952 | 124.540 | -9.72% |
| 4 | 1024 | 163.582 | 148.446 | -9.25% |

Both tables come from the feature validation run at `881bf880a`; the
review follow-ups preserve its selected default configurations. Timing
excludes input quantization and workspace construction.

<details>
<summary>Reproduce the EP2/EP4 comparison</summary>

Run from this branch in a FlashInfer development environment with
NVSHMEM, CuTe DSL 4.6.3, and CUPTI installed. The table used GB300,
PyTorch 2.12.0a0 and CUDA 13.2. Use an otherwise idle node with four
GPUs and run the two commands sequentially.

The baseline explicitly restores tile `(256, 128, 128)`, grouped
scheduling with hint `512`, atomic work claims, and token-input flag
batch `4`. The candidate resolves the actual adapter defaults. Both
retain epilogue flag batches `(2, 4)` and the inherited token-back mode.
Each capacity gets identical seeded weights, activations and routing in
both arms. Timing excludes quantization, staging, workspace construction
and host-side agreement checks. Each arm must match a sampled reference
(relative L2 below 0.03), and both arms must agree bitwise before and
after timing.

Save and run the standalone driver:

```bash
cat > /tmp/bench_mxfp4_defaults.py <<'PY'
"""Cold-L2 CUPTI comparison of native profiles and actual adapter defaults."""

import argparse
import dataclasses
import hashlib
import importlib.metadata
import json
import os
from pathlib import Path
import statistics
import subprocess

import torch
import torch.distributed as dist


def main():
    p = argparse.ArgumentParser(description=__doc__)
    p.add_argument("--hidden", type=int, default=4096)
    p.add_argument("--intermediate", type=int, default=6400)
    p.add_argument("--experts", type=int, default=8)
    p.add_argument("--topk", type=int, default=2)
    p.add_argument("--seed", type=int, default=42)
    p.add_argument("--tokens", type=int, nargs="+", required=True)
    p.add_argument("--arms", nargs="+", default=["baseline", "default"])
    p.add_argument("--rounds", type=int, default=3)
    p.add_argument("--repeats", type=int, default=100)
    p.add_argument("--output", type=Path, required=True)
    a = p.parse_args()
    rank, local_rank, world = (
        int(os.environ[k]) for k in ("RANK", "LOCAL_RANK", "WORLD_SIZE")
    )
    assert world in (2, 4) and a.experts == 8 and a.topk == 2
    assert a.arms[0] == "baseline"
    torch.cuda.set_device(local_rank)
    cc = torch.cuda.get_device_capability()
    os.environ["CUTE_DSL_ARCH"] = f"sm_{cc[0]}{cc[1]}a"
    dist.init_process_group("nccl", device_id=torch.device("cuda", local_rank))
    importlib.import_module("cupti.cupti")  # Require CUPTI; do not use event fallback.
    from flashinfer.moe_ep import (
        BootstrapConfig,
        FleetParams,
        Sm100_Mxfp8_Mxfp4_Bf16_Cutedsl_MegaMoeConfig,
    )
    from flashinfer.moe_ep.backends.mega.kernel.sm100.standard_cutedsl import (
        StandardMxfp8Mxfp4Backend,
    )
    import flashinfer.moe_ep.backends.mega.kernel.sm100.standard_cutedsl as adapter_module

    adapter_path = Path(adapter_module.__file__).resolve()
    adapter_sha256 = hashlib.sha256(adapter_path.read_bytes()).hexdigest()
    from flashinfer.moe_ep.core.runtime.bootstrap import (
        bootstrap_moe_ep_runtime,
        cutedsl_runtime_requirements,
        finalize_moe_ep_runtime,
    )
    from flashinfer.moe_ep.kernel_src.sm100 import next_cutedsl_megamoe as pkg
    from flashinfer.testing import bench_gpu_time

    bootstrap = BootstrapConfig(world_size=world, rank=rank, device=local_rank)
    runtime = bootstrap_moe_ep_runtime(
        bootstrap, cutedsl_runtime_requirements(bootstrap)
    )
    props = torch.cuda.get_device_properties(local_rank)
    uuid = str(props.uuid)
    if not uuid.startswith("GPU-"):
        uuid = "GPU-" + uuid

    def clocks():
        return subprocess.check_output(
            [
                "nvidia-smi",
                f"--id={uuid}",
                "--query-gpu=uuid,clocks.sm,clocks.mem,clocks_event_reasons.active",
                "--format=csv,noheader,nounits",
            ],
            text=True,
        ).strip()

    def barrier():
        torch.cuda.synchronize()
        dist.barrier()

    def emit(record):
        rows = [None] * world
        dist.all_gather_object(rows, record)
        if rank == 0:
            a.output.parent.mkdir(parents=True, exist_ok=True)
            with a.output.open("a") as f:
                for row in rows:
                    f.write(json.dumps(row) + "\n")
            record = dict(record, median_us=statistics.median(
                max(row["samples_us"][i] for row in rows)
                for i in range(len(rows[0]["samples_us"]))
            ))
            print(
                json.dumps(
                    {
                        k: record[k]
                        for k in ("case", "arm", "round", "median_us", "bitwise")
                    }
                ),
                flush=True,
            )

    rng = torch.Generator(device="cuda").manual_seed(a.seed + rank)
    e = a.experts // world
    w1 = torch.randn(
        e,
        2 * a.intermediate,
        a.hidden,
        dtype=torch.bfloat16,
        device="cuda",
        generator=rng,
    ).div_(10)
    w2 = torch.randn(
        e, a.hidden, a.intermediate, dtype=torch.bfloat16, device="cuda", generator=rng
    ).div_(10)
    weights = pkg.preprocess_block_scaled_weights(
        w1, w2, quant_kind="mxfp4_mxfp8", intermediate_size=a.intermediate
    )
    del w1, w2
    cases = [(f"random-{t}", t) for t in a.tokens]
    profiles = {
        "baseline": dict(
            mma_tiler_mnk=(256, 128, 128),
            schedule_policy=("grouped", 512),
            work_id_mode="atomic_counter",
            token_in_flag_batch=4,
        ),
        "default": {},
    }
    for case, tokens in cases:
        rng = torch.Generator(device="cuda").manual_seed(
            a.seed + 100000 + tokens + rank
        )
        x = torch.randn(
            tokens, a.hidden, dtype=torch.bfloat16, device="cuda", generator=rng
        ).div_(10)
        ids = (
            torch.rand(tokens, a.experts, device="cuda", generator=rng)
            .topk(a.topk, dim=1)
            .indices.to(torch.int32)
        )
        scores = torch.full((tokens, a.topk), 1 / a.topk, device="cuda")
        data, scales = pkg.quantize_mxfp8_block32(x, torch.float8_e4m3fn)
        backend = StandardMxfp8Mxfp4Backend(
            Sm100_Mxfp8_Mxfp4_Bf16_Cutedsl_MegaMoeConfig(
                intermediate_size=a.intermediate,
                top_k=a.topk,
                apply_routing_weights_before_fc2=False,
            )
        )
        backend.bind_ep_bootstrap(bootstrap)
        default = backend._workspace_config(
            FleetParams(
                num_experts=a.experts,
                max_tokens_per_rank=tokens,
                token_hidden_size=a.hidden,
            )
        )
        workspaces, graphs, configs = {}, {}, {}
        try:
            for arm in a.arms:
                cfg = dataclasses.replace(default, **profiles[arm])
                configs[arm] = cfg
                ws = pkg.Sm100BlockScaledSymmBuffer(cfg)
                workspaces[arm] = ws
                ws.x[:tokens].view(torch.uint8).copy_(data.view(torch.uint8))
                ws.x_sf[:tokens, : scales.shape[1]].view(torch.uint8).copy_(
                    scales.view(torch.uint8)
                )
                ws.topk_idx[:tokens].copy_(ids)
                ws.topk_weights[:tokens].copy_(scores)
                ws.note_staged_tokens(tokens)
                launch = pkg.sm100_block_scaled_mega_launch_thunk(*weights, ws)
                barrier()
                launch()
                barrier()
                output = ws.output_activation[:tokens]
                assert torch.isfinite(output).all() and output.count_nonzero() > 0
                if arm == "baseline":
                    oracle = output.clone()
                    indices, expected = pkg.sampled_reference(
                        ws, *weights, tokens, sample_size=32
                    )
                    error = pkg.output_error(output, indices, expected)
                    assert error < 0.03, error
                    oracle_sha = hashlib.sha256(
                        oracle.cpu().view(torch.uint8).numpy().tobytes()
                    ).hexdigest()
                torch.testing.assert_close(output, oracle, atol=0, rtol=0)
                graph = torch.cuda.CUDAGraph()
                with torch.cuda.graph(graph):
                    launch()
                graphs[arm] = graph
                for _ in range(5):
                    graph.replay()
                barrier()
                torch.testing.assert_close(output, oracle, atol=0, rtol=0)
            for rnd in range(a.rounds):
                order = a.arms[rnd % len(a.arms) :] + a.arms[: rnd % len(a.arms)]
                for arm in order:
                    barrier()
                    before = clocks()
                    times = bench_gpu_time(
                        graphs[arm].replay,
                        dry_run_iters=10,
                        repeat_iters=a.repeats,
                        enable_cupti=True,
                        use_cuda_graph=False,
                        cold_l2_cache=True,
                    )
                    after = clocks()
                    torch.testing.assert_close(
                        workspaces[arm].output_activation[:tokens],
                        oracle,
                        atol=0,
                        rtol=0,
                    )
                    emit(
                        dict(
                            adapter_sha256=adapter_sha256,
                            adapter_path=str(adapter_path),
                            depth_cutoff=7,
                            case=case,
                            arm=arm,
                            round=rnd,
                            rank=rank,
                            ep=world,
                            tokens=tokens,
                            hidden=a.hidden,
                            intermediate=a.intermediate,
                            experts=a.experts,
                            topk=a.topk,
                            seed=a.seed,
                            routing="uniform_top2",
                            config=dataclasses.asdict(configs[arm]),
                            gpu=props.name,
                            uuid=uuid,
                            sm_count=props.multi_processor_count,
                            clocks_before=before,
                            clocks_after=after,
                            bitwise=True,
                            baseline_reference_rel_l2=error,
                            oracle_sha256=oracle_sha,
                            median_us=statistics.median(times) * 1000,
                            samples_us=[v * 1000 for v in times],
                            torch=torch.__version__,
                            cuda=torch.version.cuda,
                            cutlass=importlib.metadata.version("nvidia-cutlass-dsl"),
                        )
                    )
        finally:
            for graph in graphs.values():
                graph.reset()
            for ws in workspaces.values():
                ws.destroy()
        barrier()
    finalize_moe_ep_runtime(runtime)
    dist.destroy_process_group()


if __name__ == "__main__":
    main()
PY
export PYTHONPATH="$PWD${PYTHONPATH:+:$PYTHONPATH}"
export FLASHINFER_MOE_EP_KNOB_CACHE=off
export NVSHMEM_REMOTE_TRANSPORT=none NVSHMEM_IB_DISABLE=1 NVSHMEM_MAX_TEAMS=512
export NCCL_DEBUG=WARN PYTHONUNBUFFERED=1
# Use fresh output paths; the driver appends raw records.
run_dir=$(mktemp -d)
torchrun --standalone --nproc-per-node=2 /tmp/bench_mxfp4_defaults.py \
  --tokens 32 128 192 256 512 768 1024 --rounds 7 --output "$run_dir/ep2.jsonl"
torchrun --standalone --nproc-per-node=4 /tmp/bench_mxfp4_defaults.py \
  --tokens 32 128 256 384 512 513 640 641 768 1024 --rounds 7 --output "$run_dir/ep4.jsonl"
```

Reduce the raw samples to the table's mean of seven round medians,
taking the maximum across ranks for each sample:

```bash
python - "$run_dir/ep2.jsonl" "$run_dir/ep4.jsonl" <<'PY'
import collections
import json
import statistics
import sys
from pathlib import Path

for filename in sys.argv[1:]:
    records = [json.loads(line) for line in Path(filename).read_text().splitlines()]
    groups = collections.defaultdict(list)
    for row in records:
        assert row["bitwise"] and row["baseline_reference_rel_l2"] < 0.03
        groups[(row["ep"], row["tokens"], row["arm"], row["round"])].append(row)
    medians = collections.defaultdict(list)
    for (ep, tokens, arm, rnd), ranks in groups.items():
        assert len(ranks) == ep and {r["rank"] for r in ranks} == set(range(ep))
        assert all(len(r["samples_us"]) == 100 for r in ranks)
        samples = [max(r["samples_us"][i] for r in ranks) for i in range(100)]
        medians[(ep, tokens, arm)].append(statistics.median(samples))
    print(filename)
    for ep, tokens in sorted({(k[0], k[1]) for k in medians}):
        before, after = [statistics.mean(medians[(ep, tokens, arm)]) for arm in ("baseline", "default")]
        print(f"| {ep} | {tokens} | {before:.3f} | {after:.3f} | {(after / before - 1) * 100:+.2f}% |")
PY
```

</details>

## 🔍 Related Issues

Related: #7149, #7908.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

All applicable hooks passed on the changed files and during commit. The
repository-wide `--all-files` run was not performed.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: targeted MoE EP configuration and Blackwell GPU tests cover this
adapter change.

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/moe_ep/test_mega_mxfp4_default_knobs.py
tests/moe_ep/test_mega_mxfp4_default_bands.py
tests/moe_ep/test_sm100_standard_features.py`

Validation completed on GB300 (PyTorch 2.12.0a0, CUDA 13.2, CuTe DSL
4.6.3):

- 87 configuration tests passed, including phase-only and explicit-hint
overrides, incompatible claims, local/peer validation and preparation
failures, and single-rank/pre-bootstrap validation.
- Six band/override smoke cases passed on each of four ranks, including
sampled-reference checks and bitwise CUDA-graph replay with poisoned
outputs before every replay.
- Three four-rank pool regression cases passed: matching layers reuse
their workspace, and all ranks reject a configuration mismatch, invalid
configuration, or occupancy-probe failure on one rank before pool
lookup. The GPU test module is marked node-exclusive.
- Two four-rank `create_workspace()` tests passed: a rank-local
validation error or occupancy failure is propagated before any rank
calls `prepare_workspace()`, and a later valid handle can still be
created and destroyed.
- A before/after reproducer verified that `b1a28a181` raises the
validation error locally while this revision reports it collectively.
- Three existing MXFP4 public-API cases passed on each of four ranks.
- Default configurations match `b1a28a181` at all 17 EP2/EP4 points
using the native 76-cluster probe. Same-GPU three-round comparisons
passed reference and bitwise checks.
- Fresh seven-round A/B comparisons passed reference and bitwise checks
at seven EP2 points and ten EP4 points. The table above uses the
runnable driver below it.

Full repository tests were not run locally.

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

The seven-tile separator is bracketed by measured depths of 5.3 and 7.9
tiles/cluster; it is not a measured optimum for every geometry.
Selection intentionally uses buffer capacity, including underfilled
graph replays.

This PR is AI-assisted and contains a feature commit plus separate
review-fix commits.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* MXFP4 inference now selects tile sizes and scheduling defaults based
on workload characteristics, while allowing supported options to be
overridden.
* Phase-interleaved scheduling is available for supported
configurations; incompatible combinations are rejected.
* Multi-rank workspace preparation checks that ranks agree on
configuration and active-cluster results, and reports errors when they
do not.
* Active-cluster information is available through the package’s public
interface.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [5f562e3](https://github.com/flashinfer-ai/flashinfer/commit/5f562e34069171e0055befc4c0a24ada65fcd8d2)

- **作者**: Igor Shovkun
- **时间**: 2026-11-10T14:44:41Z
- **提交信息**: feat(gemm): add mm_bf16_fp8 / mm_fp16_fp8, a W8A16 FP8 GEMM for Hopper and Blackwell (CuTe-DSL) (#7495)

<!-- .github/pull_request_template.md -->

## 📌 Description

Add `flashinfer.gemm.mm_bf16_fp8` and `mm_fp16_fp8` (with
`mm_bf16_fp8_workspace_bytes` / `mm_fp16_fp8_workspace_bytes`) for
Hopper and Blackwell: one W8A16 kernel family behind two names, one per
activation dtype, following the `mm_*` argument convention (`a`, `b`,
`alpha`, `out_dtype`, `backend`, `tactic`). The operation consumes a
contiguous FP8 e4m3 weight in `[N, K]` layout, one FP32 weight scale,
and FP16/BF16 activations; the weight is dequantized inside the kernel,
so no 16-bit copy of it is ever materialized. Output and workspace
buffers may be supplied by the caller; `tactic=` pins a kernel variant.

The kernels are CuTe-DSL (Python, `nvidia-cutlass-dsl`), compiled on
first use per architecture, tile variant, activation dtype and bias
presence; nothing is added to the AOT packages and no nvcc build is
involved.

- Hopper (`sm_90a`): warp-specialized WGMMA mainloop with the fp8 weight
fragments converted in registers; cooperative 128-row tiles and
ping-pong 64-row tiles, plus split-K with a fused in-kernel fix-up for
grids that do not fill the machine.
- Blackwell (`sm_100a`, `sm_103a`): 2-SM and 1-SM `tcgen05` tiles
(256x128, 256x160, 256x192, 128x128) with dedicated transform warpgroups
converting the weight into TMEM, plus split-K with a separate reduce.
- Variant selection is a per-architecture cost model over tile shapes
and split-K slice counts. For grids where a stream-K decomposition would
be the natural choice, the best of the available variants is scored and
taken instead.
- The per-call host cost is 12 us (plan cached per shape, pointer
objects built only at compile time, raw stream handle).

This replaces the CUTLASS C++ implementation that earlier revisions of
this PR carried. It was kept as the reference while the port was brought
to parity: under CUDA-graph timing the CuTe-DSL kernels are at or ahead
of it on every tp-4 row of H100, GB200, B200 and B300 (the table under
Tests).

### Blackwell tile walk order (commit abb925094)

Nsight Compute on a B200 showed the persistent scheduler walking the
activation tiles fast for N >= 1.5 M, which keeps the bf16 activation,
the larger operand, as the one that must stay L2-resident. Walking the
weight rows fast whenever the fp8 weight is the smaller operand (`n < 2
m`) fixes that. At M=8192, N=10240, K=5120: L2 hit rate 59% to 84%, DRAM
reads 1.27 GB to 0.32 GB, 576 us to 536 us at native clocks. At a locked
clock, over twenty Cosmos layer shapes, the new rule is within 0.7%
where it does not help and faster wherever M >= 7296:

| M | N | K | old walk | new walk | gain |
|---|---|---|---|---|---|
| 16384 | 12800 | 5120 | 1630 us | 1400 us | 14.1% |
| 32768 | 3200 | 5120 | 853 us | 683 us | 19.9% |
| 8192 | 10240 | 5120 | 578 us | 535 us | 7.4% |
| 8192 | 6400 | 5120 | 354 us | 331 us | 6.6% |
| 8192 | 12800 | 5120 | 739 us | 699 us | 5.4% |
| 7296 | 5120 | 5120 | 249 us | 240 us | 3.8% |

The tile group size made no further difference once the direction was
right. The B200 plot below was re-measured after this change
(umb-b200-240); the B300 and GB200 plots predate it, and their rows with
M >= 8192 understate the kernel by these amounts.

### Performance comparison plots

Full-grid measurements with BF16 activations and FP8 weights: every
Cosmos3 layer, TP shard (1, 2, 4, 8) and token count. Green is this PR's
W8A16 kernel with automatic variant selection, gray cuBLAS with a
pre-dequantized weight (conversion excluded), orange the complete Torch
cast/scale plus cuBLAS. Higher TFLOP/s is better. Timing: a CUDA graph
of back-to-back calls with a 256 MB memset (L2 flush) before each,
replayed in rounds alternating implementations, flush-only graph
subtracted, median; the H100 and GB200 grids had a two-second idle
before each cell so the long rows are not measured on a throttled part.
Throughput is `2 * M * N * K / elapsed`, with every kernel of the
cast-copy path inside its elapsed time; the benchmark is
`benchmarks/bench_mm_bf16_fp8.py`.

**Hopper — H100**

![H100: W8A16 versus cuBLAS and
cast-copy](https://gist.githubusercontent.com/ishovkun/ee4a6fe765e79bb07b265b1855a4a916/raw/4d4dcecc93abb4688dd26b7eab18907d2f4b2d9e/w8a16_h100_tflops_grid.png)

**Blackwell — B200**

![B200: W8A16 versus cuBLAS and
cast-copy](https://gist.githubusercontent.com/ishovkun/ee4a6fe765e79bb07b265b1855a4a916/raw/50bd5e635f9a16f267f5627373eb87e11ba13d24/w8a16_b200_tflops_grid.png)

**Blackwell — B300**

![B300: W8A16 versus cuBLAS and
cast-copy](https://gist.githubusercontent.com/ishovkun/ee4a6fe765e79bb07b265b1855a4a916/raw/4d4dcecc93abb4688dd26b7eab18907d2f4b2d9e/w8a16_b300_tflops_grid.png)

**Blackwell — GB200**

![GB200: W8A16 versus cuBLAS and
cast-copy](https://gist.githubusercontent.com/ishovkun/ee4a6fe765e79bb07b265b1855a4a916/raw/4d4dcecc93abb4688dd26b7eab18907d2f4b2d9e/w8a16_gb200_tflops_grid.png)

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

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

`tests/gemm/test_mm_bf16_fp8.py`,
`tests/gemm/test_mm_bf16_fp8_dispatch.py` and
`tests/trace/test_mm_bf16_fp8_trace.py` at the PR head (3dc268ab5),
public CUDA 13.3.1:

| GPU | Result |
|---|---|
| H100 80 GB | 366 passed, 49 architecture-specific skips |
| B200 | 347 passed, 68 architecture-specific skips |

Coverage: every forced variant on both architectures, FP16/BF16, all
finite FP8 encodings, bias, grouped traversal, K/N tails, minimal
split-K, caller workspace reuse on a non-default stream with canaries,
aliasing and alignment rules, empty outputs, dimension bounds, device
resolution.

Reproducible benchmark: `python benchmarks/bench_mm_bf16_fp8.py --tp 4
--m 1024 4096 8192` (CUPTI timing; the `kernel` column is this op,
`cublas` the pre-dequantized reference, `cast` the Torch cast-copy
path). CUDA-graph medians, DSL time relative to the replaced C++
implementation, tp 4, bf16, M in {1024, 4096, 8192}:

| GPU | 18 rows |
|---|---|
| H100 (s4124-0017) | −0.2% to −4.9% |
| GB200 (gb-nvl-057) | −0.4% to −4.8% |
| B200 (umb-b200-248) | +0.1% worst, otherwise −0.1% to −3.8% |
| B300 (umb-b300-023) | −0.1% to −4.0%; und.q 8192 within ±0.6% across
repeats |

## Reviewer Notes

- `flashinfer/gemm/w8a16_fp8.py`: the public contract (checks, aliasing,
workspace rules) is unchanged from the C++ revisions; it now launches
`flashinfer/gemm/w8a16_fp8_dispatch.py`, which holds the variant
selection and the launch.
- `flashinfer/gemm/kernels/cute_dsl/w8a16_fp8_gemm_sm90.py` and
`w8a16_fp8_gemm_sm100.py` are the kernels; `w8a16_fp8_splitk_reduce.py`
the Blackwell split-K reduce. The Blackwell kernel derives from
FlashInfer's dense W4A16 CuTe-DSL kernel.
- A split-K `algo` on a `K` that cannot be sliced now raises
`ValueError` (it was a `RuntimeError` from the native launcher).

### [7f30bea](https://github.com/flashinfer-ai/flashinfer/commit/7f30bea1efd82a0e38314db7ad0373c8645aa5d1)

- **作者**: linquanh
- **时间**: 2026-11-10T10:54:02Z
- **提交信息**: feat(deepseek_v41): experimental Prims-TS decode backend for DS4.1 sparse MLA (SM100/SM103/SM107) (#6988)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

Adds a native **Prims-TS** (task-scheduled CuTe-DSL) decode backend for
DeepSeek-V4.1 sparse MLA — H64 / Sq1 / D512 attention over a 128-row SWA
window plus up to 512 selected compressed (FP4) rows — as an explicit
experimental alternative to the existing CuTe DSL (Frost) backend,
together with the Prims-TS MLA kernel extensions it needs.

**Why.** The Frost DS4.1 decode is SM100-only and runs BF16 Q/P MMAs.
Prims-TS runs E4M3 QK/PV on SM100, SM103 and SM107 directly from the
serving cache formats (E4M3 SWA, packed FP4 main), with live per-call
metadata and CUDA Graph replay. Against upstream FlashMLA (`395cb3a`) it
is 1.51-2.71x faster on B200 and 1.30-3.04x faster on Rubin R100.
Against TRTLLM-GEN's DSv4 sparse MLA decode on B200 it ranges from 1.08x
slower to 1.37x faster depending on shape. Tables are below.

**Commits** (one concern each):
1. `feat(prims_ts): Keep-AB sparse MLA hooks for custom KV producers,
retained-K V split and PDL`: generic 1CTA throughput-latency sparse MLA
changes. KV-producer and sparse-view hooks let a backend bind the
original index table and stage producer-owned data before a KV slot is
acquired. Keep-AB V owners can split V across CTAs over a retained K
tile. The kernel gains opt-in PDL, branch-free epilogue stores with
prefetched sinks, and early publication of the softmax maxima. Existing
generic profiles are unchanged.
2. `feat(prims_ts): warp-specialized FP8 Keep-AB sparse MLA with TMA
output`: opt-in `ws_mma` / `ws_store_cols` / `ws_tma_store` /
`ws_tail_staged_stripes` / `ws_q_in_kv` schedule for D512 E4M3
retained-K tiles with TMA output stores. It also supports grouped MXFP8
output through quantizers that declare `stages_ws_sw128_rows` (used by
TensorRT-LLM's CSA2 prefill, not by DS4.1 decode), plus the related
guards.
3. `feat(deepseek_v41): native Prims-TS decode backend for DS4.1 sparse
MLA`: the backend, public API, cache-writer format, examples, benchmark
and tests.

**Public API** (experimental, explicit opt-in; existing callers are
unaffected because the default stays `backend="cute-dsl"`):
- `deepseek_v41_decode(query, swa_kv_cache, workspace_buffer,
sparse_indices, compressed_kv_cache, sparse_topk_lens, seq_lens,
out=None, bmm1_scale=1.0, bmm2_scale=1.0, sinks=None, kv_layout="HND",
backend="prims-ts")` and `deepseek_v41_window_decode(...,
backend="prims-ts")` (K=0) take the following inputs:
  - E4M3 Q `[B,1,64,512]`.
- Typed E4M3 SWA (width 512) and packed FP4 main (width 288) page64
caches in common cache units, HND or NHD.
- int32 `sparse_indices [B,128+K]` (K = 0..512, step 64), with
`sparse_topk_lens` / `seq_lens` refreshed on every call or replay.
  - Runtime FP32 `bmm1_scale` / `bmm2_scale` and optional FP32 sinks.

They return BF16 output only. Prims-TS keywords passed without
`backend="prims-ts"` raise instead of reaching the Frost signature.
- `deepseek_v41_decode_workspace_size(B, K, backend="prims-ts")` is pure
arithmetic and returns the size of the caller-owned workspace (private
LSE, an 18 KB K0 main page, bounded KV-split partials). The size is
monotone in B and K, so one buffer sized for the largest call serves
every smaller one.
- `deepseek_v41_quantize_cache` gains `format="swa_fp8"` and `kv_layout`
(default NHD, as on main). The generic MLA output-quantizer ABI stays
positional, including `None`.

**Kernel.** One finalizing Keep-AB / M64 / BK128 Prims-TS attention
jointly attends the SWA tile and `ceil(K/128)` main tiles, with inline
metadata masking and sinks.
- **Loaders:** they gather SWA rows with `cp.async` and convert staged
FP4 main rows to E4M3. The conversion uses PTX 9.4's dense E2M1 x E4M3
multiply on SM100/SM103 and an F16 route on SM107, where ptxas has no
packed form.
- **Work split:** small batches split KV (merged by a PDL-chained
reducer) and/or V across CTAs according to a scored policy. Batches
above one wave run on the persistent scheduler.

**Limitations.**
- Shapes and model: H64 / Sq1 / D512 only, single-token DS4.1 decode
only, no automatic backend selection, JIT-only.
- CUDA Graph capture needs an eager warmup plus caller-owned `out` and
workspace.
- The (KV split, V split) cost table was fitted on B200, so R100 is not
tuned; see the R100 notes below.
- No full-model qualification is claimed.

**Validation** at the PR head `8eaaf1809` (tree identical to the locally
validated `efe61e03f`).

Internal CI, pipeline
[#80470100](https://nv/flashinfer-ci/-/pipelines/80470100) (GitLab MR
!2359), scoped to the seven test files the PR touches (921 cases): no
failures on any GPU.

| GPU | Arch | CI images | Passed | Skipped |
|---|---|---|--:|--:|
| B200, GB200 | SM100 | cu129, cu130, cu134 | 921 | 0 |
| GB300 | SM103 | cu129, cu130, cu134 | 874 | 47 |
| VR NVL72 (Rubin) | SM107 | cu134 | 874 | 47 |
| H100, RTX PRO 6000 Blackwell | SM90, SM120 | cu130 | 381 | 540 |

- On SM103/SM107, 46 of the 47 skips are the SM100-only CuTe DSL (Frost)
cases in `test_deepseek_v41_decode.py`; the other is in
`test_deepseek_v41_cache.py`. The H100 and RTX PRO 6000 skips are the
cases that need SM100, SM103 or SM107.
- The only failed job, `unit_test_spark` (GB10, allowed to fail),
stopped during dependency setup (`apt-get` permission error) before
running any test.

Public CI ([PR
Test](https://github.com/flashinfer-ai/flashinfer/actions/runs/42558498841)):
the H100 targeted tests and all six AOT build/import jobs pass;
pre-commit (ruff 0.12.8, mypy 1.17.1) passes.

Local, on B200 with the `flashinfer-ci-cu130` image, CuTe-DSL 4.8.0 and
bundled CUDA 13.4:
- `tests/experimental/test_deepseek_v41_decode.py`: 131/131.
- DS4.1 cache/CPU suites
(`test_deepseek_v41_{cache,defaults_cpu,sparse_views_cpu,workspace_cpu}.py`):
384/384.
- `tests/attention/test_attention_ts_mla_decode.py`: 196/196.
- `tests/attention/test_attention_ts_sparse_mla.py`: 210/210.
- Commit 1 on its own passes the two generic attention suites: sparse
MLA 203/203 (its test file) and MLA decode 196/196.

The R100 FlashMLA comparison below ran only the benchmark's per-arm FP64
gates (21/21 shapes). DS4.1 output and LSE at the head are bitwise
identical to the pre-review revision `d80b3221a` on 28 cases (B 1-256 x
K 0-512, covering split, unsplit and persistent schedules).

## Measurements

Latency in us per call (lower is better) from warm CUDA Graph replay,
with JIT, allocation and capture excluded; every arm passes its own FP64
gate before timing. Measured at the PR head `8eaaf1809`.

| # | Comparison | GPU | Result |
|--:|---|---|---|
| 1 | DS4.1 decode vs upstream FlashMLA `395cb3a` | B200 | Prims-TS
1.51-2.71x faster |
| 1 | DS4.1 decode vs FlashMLA `395cb3a` (local `sm_107a` build) | Rubin
R100 | Prims-TS 1.30-3.04x faster |
| 2 | DS4.1 decode vs TRTLLM-GEN DSv4 sparse MLA | B200 | TRTLLM-GEN /
Prims-TS 0.93-1.37x |

### 1. DS4.1 decode vs upstream FlashMLA (B200 and Rubin R100)

- Fixture (same on both GPUs):
`benchmarks/bench_deepseek_v41_decode.py`, H64/Sq1/D512, 128 SWA rows
plus K FP4 main rows, context 32768, sinks enabled. ABBA order, 3 rounds
of 15 samples, median (round medians agree within 0.8%).
- B200: PyTorch 2.14.1+cu130, CuTe-DSL 4.8.0 (CUDA 13.4), upstream
FlashMLA `sm_100a` build.
- R100 (pre-production, 216 SMs, 280 GB HBM at 4752 MHz): PyTorch
2.14.0+cu130, CuTe-DSL 4.8.0 (CUDA 13.4). FlashMLA has no SM107 build,
so it was built for `sm_107a` with CUDA 13.4 and a CUTLASS config change
that enables the SM100 tcgen05 atoms.
- Precision differs: Prims-TS runs E4M3 QK/PV MMAs, while FlashMLA runs
BF16 MMAs over exactly dequantized KV. FP8 MMA peak is twice BF16, so
part of the gap comes from that contract.

| B | K | R100 FlashMLA | R100 Prims-TS | R100 speedup | B200 FlashMLA |
B200 Prims-TS | B200 speedup |
|--:|--:|--:|--:|--:|--:|--:|--:|
| 1 | 512 | 22.38 | 9.54 | 2.35x | 21.33 | 7.88 | 2.71x |
| 4 | 512 | 22.37 | 10.23 | 2.19x | 21.52 | 8.08 | 2.66x |
| 16 | 512 | 22.44 | 12.71 | 1.76x | 21.49 | 11.00 | 1.95x |
| 32 | 512 | 23.13 | 17.77 | 1.30x | 21.50 | 11.71 | 1.84x |
| 64 | 512 | 23.17 | 10.98 | 2.11x | 22.35 | 12.82 | 1.74x |
| 128 | 512 | 24.23 | 16.81 | 1.44x | 23.66 | 14.26 | 1.66x |
| 256 | 512 | 42.23 | 32.20 | 1.31x | 45.58 | 30.19 | 1.51x |
| 1 | 128 | 14.66 | 8.97 | 1.63x | 12.44 | 6.53 | 1.90x |
| 4 | 128 | 14.70 | 5.51 | 2.67x | 12.57 | 6.78 | 1.85x |
| 16 | 128 | 14.76 | 5.58 | 2.65x | 12.42 | 6.71 | 1.85x |
| 32 | 128 | 14.75 | 5.84 | 2.53x | 12.45 | 6.88 | 1.81x |
| 64 | 128 | 15.20 | 6.42 | 2.37x | 13.03 | 7.57 | 1.72x |
| 128 | 128 | 16.20 | 7.60 | 2.13x | 14.20 | 8.94 | 1.59x |
| 256 | 128 | 27.74 | 17.85 | 1.55x | 27.63 | 15.91 | 1.74x |
| 1 | 0 | 11.84 | 6.65 | 1.78x | 9.44 | 4.88 | 1.94x |
| 4 | 0 | 11.84 | 3.90 | 3.04x | 9.53 | 5.00 | 1.90x |
| 16 | 0 | 11.89 | 3.95 | 3.01x | 9.41 | 4.99 | 1.89x |
| 32 | 0 | 11.89 | 4.01 | 2.97x | 9.44 | 5.05 | 1.87x |
| 64 | 0 | 11.93 | 4.60 | 2.59x | 9.68 | 5.76 | 1.68x |
| 128 | 0 | 12.87 | 5.47 | 2.35x | 10.55 | 6.91 | 1.53x |
| 256 | 0 | 22.47 | 9.08 | 2.47x | 21.26 | 11.67 | 1.82x |

**R100 notes** (R100 is not tuned in this PR):
- At K=512, R100 is 7-52% slower than B200 except at B=64: SM107 has no
packed E2M1 x E4M3 multiply, so the FP4 conversion uses an F16 route. At
K <= 128 with 4 <= B <= 128 it is 15-22% faster.
- The split policy was fitted on B200's 148 SMs, so B=32/K=512 (17.77
us) is slower than B=64/K=512 (10.98 us). B=1 is 2.75-3.45 us slower
than B=4 at K <= 128 (not yet profiled).
- On R100 nodes with 186 GB HBM at 3186 MHz, Prims-TS is up to 1.50x
slower while FlashMLA stays within 4.2%.

### 2. DS4.1 decode vs TRTLLM-GEN (B200)

- TRTLLM-GEN arm: `trtllm_batch_decode_sparse_mla_dsv4(...,
backend="trtllm-gen")` from the base `799c47e77`. Same shapes as section
1, HND, both arms with PDL.
- PyTorch 2.11.0+cu128, CuTe-DSL 4.8.0. ABBA order, 15 rounds, mean of
two runs' medians, one K per GPU.
- Both arms run E4M3 MMAs on the same E4M3 Q and SWA, but TRTLLM-GEN
needs its main cache in dense E4M3 (512 B/token versus Prims-TS's packed
FP4 at 288 B/token).

| B | K | TRTLLM-GEN | Prims-TS | TRTLLM-GEN / Prims-TS |
|--:|--:|--:|--:|--:|
| 1 | 512 | 8.56 | 7.98 | 1.07x |
| 4 | 512 | 9.36 | 8.07 | 1.16x |
| 16 | 512 | 10.71 | 10.96 | 0.98x |
| 24 | 512 | 12.40 | 11.28 | 1.10x |
| 32 | 512 | 13.89 | 11.74 | 1.18x |
| 64 | 512 | 17.37 | 12.64 | 1.37x |
| 128 | 512 | 15.42 | 14.46 | 1.07x |
| 149 | 512 | 25.19 | 25.77 | 0.98x |
| 256 | 512 | 28.31 | 30.47 | 0.93x |
| 1 | 128 | 6.18 | 6.65 | 0.93x |
| 4 | 128 | 6.39 | 6.73 | 0.95x |
| 16 | 128 | 6.61 | 6.93 | 0.95x |
| 24 | 128 | 6.66 | 7.04 | 0.95x |
| 32 | 128 | 7.09 | 7.13 | 0.99x |
| 64 | 128 | 8.57 | 7.77 | 1.10x |
| 128 | 128 | 10.71 | 9.12 | 1.17x |
| 149 | 128 | 16.05 | 15.38 | 1.04x |
| 256 | 128 | 17.29 | 16.23 | 1.07x |
| 1 | 0 | 4.98 | 4.67 | 1.07x |
| 4 | 0 | 5.40 | 5.11 | 1.06x |
| 16 | 0 | 5.55 | 5.15 | 1.08x |
| 24 | 0 | 5.66 | 5.21 | 1.09x |
| 32 | 0 | 5.83 | 5.23 | 1.11x |
| 64 | 0 | 7.18 | 5.96 | 1.20x |
| 128 | 0 | 9.11 | 7.09 | 1.29x |
| 149 | 0 | 13.01 | 11.24 | 1.16x |
| 256 | 0 | 14.08 | 11.86 | 1.19x |

TRTLLM-GEN is faster at K=512 for B=16, 149 and 256 (by 2-8%) and at
K=128 for B <= 32 (by up to 8%); Prims-TS is faster everywhere else, by
up to 1.37x at B=64/K=512. Without PDL, TRTLLM-GEN takes a further
0.55-1.52 us per call.

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

- [ ] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

## 🔬 Experimental Track

<!-- Only for PRs submitted under the experimental policy
(CONTRIBUTING.md → "Experimental APIs and Backends").
     Leave this section untouched for normal PRs. -->

- [x] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.
Tracking issue: #9314
- [x] The tracking issue names an owner, the reason for the experimental
path, and a graduation plan with a target release.
- Owner @kris1025; graduation review by 2026-12-07, release chosen by
maintainers.
- [ ] Core changes are limited to a thin entry point (signature, shared
validation, feature-gate check, backend selection, handoff).
- Not fully met. `flashinfer/deepseek_v41.py` is a thin entry point: it
selects the backend, rejects Prims-TS keywords on the default backend
and hands off through a deferred import.
- Commits 1-2 also change the shared Prims-TS MLA decode kernels in
`flashinfer/attention/prims_ts/kernels/mla_decode/`. These changes add
opt-in hooks and an opt-in schedule, leave existing profiles unchanged,
and are covered by `tests/attention/test_attention_ts_sparse_mla.py`.
They follow normal core review.
- [x] Tests live in `tests/experimental/` and were validated on the
intended hardware; a runnable example is included.
- Validated on SM100 (B200, GB200), SM103 (GB300) and SM107 (VR NVL72);
see Validation. The example is `examples/deepseek_v41/decode.py
--backend prims-ts`.
- [x] Nothing is registered in `flashinfer/aot.py`, and no experimental
backend is reachable from `backend="auto"` without
`FLASHINFER_ALLOW_EXPERIMENTAL_AUTO_BACKENDS=1`. (Calling an
`@flashinfer_experimental_api` or naming a backend explicitly is itself
the opt-in and needs no environment variable.)
- The DS4.1 APIs accept only an explicit `backend="cute-dsl"` (the
default) or `backend="prims-ts"`; there is no `"auto"`.
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
tests/experimental/test_deepseek_v41_defaults_cpu.py
tests/experimental/test_deepseek_v41_sparse_views_cpu.py
tests/experimental/test_deepseek_v41_workspace_cpu.py
```

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->

TensorRT-LLM's vendored Prims-TS: when it re-vendors this code, its CSA2
`MXFP8OutputQuant` must set `stages_ws_sw128_rows = True` to keep the WS
TMA quantized output path; otherwise that profile is rejected.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added an experimental Prims-TS backend for DeepSeek V4.1 mixed-cache
and window decoding, alongside the existing CuTe DSL backend.
* Added FP8 SWA cache quantization and support for NHD or HND cache
layouts.
* Added a helper to calculate workspace requirements for Prims-TS
decoding.
* Updated decode examples and benchmarks to select between backends and
optionally measure FlashMLA.
* **Documentation**
* Expanded DeepSeek V4.1 guidance with backend requirements, input and
cache formats, workspace and capture considerations, and example
commands.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude <noreply@anthropic.com>

### [f877311](https://github.com/flashinfer-ai/flashinfer/commit/f877311e407f8bc5e9ea893c7be190d1174a8a87)

- **作者**: Yang Xu
- **时间**: 2026-11-10T10:50:18Z
- **提交信息**: perf(gemm): cache and parallelize MXFP8 CuTe-DSL autotune compilation (#6615)

<!-- .github/pull_request_template.md -->

## 📌 Description

SM100-family `mm_mxfp8(backend="cute-dsl")` currently compiles
persistent and tcgen05 split-K candidates on demand in each fresh
process. Large autotune searches repeat this work during serving
startup, even when tuning winners are saved separately. Persist these
compiled objects and precompile cache misses with a bounded,
shared-cache-coordinated dedicated worker processes.

- Reuse the existing FP4 CuTe-DSL disk-cache infrastructure with a
separate MXFP8 namespace, complete code-generation keys (including
split-K), and source invalidation.
- Precompile exactly the autotuner-filtered candidates, respecting
tactic blocklists. Deduplicate object names, recheck the disk cache
under a process lock, and bound workers by CPU affinity and available
host/cgroup memory. Failed preparations fall back to on-demand
compilation.
- Workers import a dedicated compiler entry point without reexecuting
the calling application. Source/editable import paths are preserved;
ordinary scripts need no `__main__` guard.
- Each worker chunk has a 600-second default timeout;
`FLASHINFER_MM_MXFP8_CUTE_DSL_COMPILE_TIMEOUT=0` disables it. Timed-out
workers are killed before cache-lock release and on-demand fallback.
- Default to up to four compilation workers;
`FLASHINFER_MM_MXFP8_CUTE_DSL_COMPILE_WORKERS=0` or `1` keeps on-demand
compilation. Disabling disk caching or JIT disables the precompile pool.
- Preserve the full tactic search by default.
`FLASHINFER_MM_MXFP8_CUTE_DSL_MAX_TACTICS` is an opt-in ranked top-N
limit that retains split-K candidates; it needs broader performance
calibration before any default change.
- Add a fresh-process startup benchmark, cache/coordinator tests, and
documentation.

Measured on one B300 PCIe TS1 GPU (SM103; device name reports `NVIDIA
Graphics Device`), 16 allocated CPUs, 96 GiB host memory, driver
615.71.09, CUDA toolkit 13.2, PyTorch 2.14.1+cu130 and CuTe DSL 4.8.0.
Source is `76a0b3bc31ef1a91b6443e74ee0a517c98a0e370`, including the
dedicated-worker fix and current-main integration. BF16 output;
M={8,64,256}, N=1024, K=7168; full search, 137 unique GEMM artifacts and
389 profiling calls:

| Fresh-process case | Autotune wall time | Caller GEMM compilations |
Precompile tasks | Profiling calls |
| --- | ---: | ---: | ---: | ---: |
| Persistence and precompile disabled (baseline) | 74.844 s | 137 | 0 |
389 |
| Parallel disk-cache population, 4 dedicated workers, unguarded calling
script | 34.681 s | 0 | 137 | 389 |
| Disk cache reused | 3.517 s | 0 | 0 | 389 |
| Disk cache and saved tuning winners reused | 0.120 s | 0 | 0 | 0 |

The parallel case produced all 137 GEMM objects without on-demand
compilation in the caller. It ran from a top-level script without a
`__main__` guard and completed normally. Both warm cases forbid GEMM
compilation and pool creation; the saved-winner case also asserts zero
profiling calls.

These are single-run component measurements of the autotune context,
excluding Python import, quantization setup, model loading and full
serving startup. The baseline uses the same kernels and candidate set
with persistence/precompilation disabled, with a separate cache root; it
is not a replay of FlashInfer 0.6.17. Native utility compilation
encountered inside the tuning context is included. System/driver caches
are not claimed empty. The full-search cold case improves by about 2.16x
in this sample; no serial-persistence or top-N speedup is inferred from
it.

Baseline and parallel-cold hot-L2 CUDA-event graph-replay medians were
both 3.4176 / 8.1280 / 8.3328 us for M=8 / 64 / 256. All four cases
checked finite outputs and numerical agreement after replay (cosine >
0.99928). This is BF16 SM103 component qualification, not full vLLM/TP
serving validation or a new qualification of every dtype/architecture.

The repository benchmark reproduces baseline, serial/parallel
population, disk reuse and saved-winner cases with new cache
directories:

```bash
python benchmarks/bench_mxfp8_startup.py \
  --output-dir /tmp/mxfp8-startup-full \
  --n 1024 --k 7168 --buckets 8,64,256 --top-n 0
```

Follow-up commits `dd31b0a05` and `86ffb80dc` add the finite worker
timeout and repair the portable MoE staging test fixture. The
performance table remains pinned to `76a0b3bc`; current-head host
validation passes 105 tests, including real child termination and
lock-release checks. The current-head native rerun passed on B300 SXM6
(SM103): the complete portable staging file passed 11 tests after
reproducing the three original fixture failures; unguarded MXFP8 cold
tuning completed 131 worker tasks with zero caller compilations, and
fresh-process saved-winner reuse compiled/profiled nothing. Both MXFP8
cases checked all three M buckets after graph replay. This is a separate
validation device from the performance table above. Fresh full CI
remains in progress.

The unguarded entry-point regression is independently reproducible with
`pytest --confcutdir=tests/jit -q tests/jit/test_mxfp8_precompile.py -k
unguarded`.

## 🔍 Related Issues

Builds on the persistence work in #5047 (co-authored credit retained for
WikAlie). Adds bounded parallel preparation, optional candidate ranking,
shared-cache coordination, and startup regression coverage. This PR does
not close the separate BF16 cache issue #6455 or the autotune-result
reuse issue #6554.

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

Changed-file pre-commit hooks passed, including Ruff and mypy. The
repository-wide `--all-files` run and hook installation are not claimed
by the unchecked items above.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

Targeted CPU suite on current head `86ffb80dc`: **105 passed**:

```bash
pytest --confcutdir=tests/jit -q \
  tests/jit/test_cute_dsl_cache.py tests/jit/test_mxfp8_precompile.py
```

GPU validation: the four fresh-process cases above passed on the current
head, including all three M buckets after CUDA Graph replay. The cold
parallel case used an unguarded calling script; disk-warm and
saved-winner runs compiled no GEMMs or worker pools, and saved-winner
reuse performed no profiling.

The real-process host regression failed on the preceding spawn-pool
implementation: a 40-second timeout, with the calling script executed
three times while contending for the cache lock. The dedicated-worker
fix executes it once and completes. Worker-error fallback is exercised
using invalid compile descriptions without GPU work. The current-main
test conflict is resolved by retaining both test families; shared-runner
dispatch is covered by the host suite.

Full CI was attempted on `76a0b3bc` in run 40056312888. The portable MoE
staging test's manually constructed workspace omitted its constructor's
`_tuning_state`, causing three failures and fail-fast cancellation of
other lanes. This PR now initializes the fixture with the real state
object and verifies graph capture marks it; production MoE code is
unchanged. Fresh full CI has been requested for `86ffb80dc`; it is not
yet reported as passing.

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

Open for review of the implementation and existing validation.
Production B300 SXM / DeepSeek-V4.1 TP4 startup validation remains
outstanding. The SXM attempts stopped during environment
import/preflight before GEMM execution; they provide no kernel
performance result.

Scope: SM100-family persistent/tcgen05 split-K MXFP8 runner only. Warp
split-K, SM107/SM12x runners, other APIs/backends, portable CuTe-DSL
artifacts in `flashinfer-jit-cache` wheels, and autotune-result
persistence policy are outside this patch. Default public signatures and
full-search candidate coverage are unchanged; bounded precompilation is
the intended default startup-behavior change.

Please focus review on cache-key/source coverage, the FP8 compile
contract (distinct from FP4 packed storage), filtered-candidate
preparation, cross-process lock/recheck behavior, and resource bounds.
The shared FP4 compile helper retains its original defaults. The
optional ranking reuses the FP4 heuristic and is deliberately disabled
by default pending a broader MXFP8 shape sweep.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* MXFP8 CuTe-DSL GEMM can precompile tactics, falling back to on-demand
compilation if precompilation fails.
* An optional setting limits MXFP8 autotune candidates while retaining
eligible split-K tactics.
* **Documentation**
* Added guidance on MXFP8 startup caching, configuration options,
limitations, and performance measurements.
* **Tests**
* Added coverage for MXFP8 cache behavior, precompilation, and tactic
selection, plus a benchmark for startup and warm-graph scenarios.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: WikAlie <ww224645775@126.com>

### [119cf05](https://github.com/flashinfer-ai/flashinfer/commit/119cf05beeb69ed7f66c576f81ed828702449314)

- **作者**: Jimmy Zhou
- **时间**: 2026-11-10T08:45:39Z
- **提交信息**: bump version to 0.7.4 (#8876)

<!-- .github/pull_request_template.md -->

## 📌 Description

Bump version to 0.7.4 for release.

`release-v0.7.4` was cut from `main` at `e5eda939f`; `v0.7.4rc1` is that
commit plus the rc version bump on the release branch (`main` never
carries `rcN`). The API audit baseline is the latest published stable
release, `v0.7.3`. This PR changes only `version.txt`.

## 🔍 Related Issues


https://github.com/flashinfer-ai/flashinfer/issues?q=is%3Aopen+label%3Av0.7.4

### Tracked for v0.7.4 (label `v0.7.4`, as of 2026-11-10, release tip
368bd90ec)

PRs:

- In the `release-v0.7.4` cut: #6908, #7833, #8078, #8464, #8583, #8684,
#8696, #8727, #8752
- Cherry-picked onto `release-v0.7.4`: #7834, #8536, #8537, #8599,
#8821, #8968, #8985 (GDN device-scope fix only), #8996, #8997, #8998,
#9030, #9036, #9037 (adapted to the release file layout), #9038, #9041
(picked directly; on main the same fix is in #9016), #9292
- Merged on `main`, not picked: #9215 does not apply (its docs cover
APIs renamed after the cut)

Issues from v0.7.4rc1 validation and earlier:

| Issue | Fix | State |
|---|---|---|
| #8969 | #8985 | fix on `release-v0.7.4` |
| #8967 | #9030 | fix on `release-v0.7.4` |
| #8299 | #8996 | fix on `release-v0.7.4` |
| #9025 | #9036 | fix on `release-v0.7.4` |
| #7452 | #8997, #8998 | fix on `release-v0.7.4` |
| #8466 | #9037 | fix on `release-v0.7.4` |
| #9028 | #9038 | fix on `release-v0.7.4` |
| #8964 | #9041 (main: #9016) | fix on `release-v0.7.4` |
| #7687 | none yet | open |
| #8868 | none yet | open |
| #6907, #8000, #8077, #8745, #8825 | #6908, #8583, #8078, #8752, #8464
| in the cut |

## Reviewer Notes

**API changes review**

API changes since `v0.7.3`, using `scripts/list_apis.sh` at `e5eda939f`.

```diff
diff -u \
  <(scripts/list_apis.sh -d -p --ref v0.7.3) \
  <(scripts/list_apis.sh -d -p)
--- v0.7.3
+++ main-e5eda939f
@@ -127,9 +127,33 @@
     output_dtypes: Optional[Tuple[torch.dtype, ...]] = None,
     batch_sizes: Optional[Sequence[int]] = None,
 ) -> None:
+class FP8MQATopKWrapper:
+    @flashinfer_api
+    def plan(
+        self,
+        qo_indptr: torch.Tensor,
+        kv_indptr: torch.Tensor,
+        *,
+        num_query_rows: int | None = None,
+        next_n: int | None = None,
+        host_length_hints: tuple[torch.Tensor, torch.Tensor] | None = None,
+    ) -> None:
+
+    @flashinfer_api
+    def run(
+        self,
+        q: torch.Tensor,
+        weights: torch.Tensor,
+        k: torch.Tensor,
+        *,
+        k_scale: torch.Tensor,
+        out: torch.Tensor | None = None,
+        q_scale: torch.Tensor | None = None,
+    ) -> torch.Tensor:
+
 [Global Functions]
 @flashinfer_api
-def cake_causal_conv1d_train_forward(
+def cake_causal_conv1d_det_train_forward(
     x: torch.Tensor,
     weight: torch.Tensor,
     cu_seqlens: torch.Tensor,
@@ -141,7 +165,7 @@
 
 
 @flashinfer_api
-def cake_causal_conv1d_train_backward(
+def cake_causal_conv1d_det_train_backward(
     x: torch.Tensor,
     weight: torch.Tensor,
     cu_seqlens: torch.Tensor,
@@ -153,30 +177,45 @@
     dx: Optional[torch.Tensor] = None,
     dweight: Optional[torch.Tensor] = None,
     dbias: Optional[torch.Tensor] = None,
+    bwd_grid_mult: int = 1,
 ) -> tuple[torch.Tensor, ...]:
 
 
 @flashinfer_api
-def cake_causal_conv1d(
+def cake_causal_conv1d_det(
     x: torch.Tensor,
     weight: torch.Tensor,
     cu_seqlens: torch.Tensor,
     bias: Optional[torch.Tensor] = None,
     *,
     silu_grad_preactivation: str = "bf16",
+    bwd_grid_mult: int = 1,
 ) -> torch.Tensor:
 
 
+[Global Functions]
 @flashinfer_api
-def cake_causal_conv1d_kcp(
+def cake_causal_conv1d_det_kcp(
     x_local: torch.Tensor,
     weight: torch.Tensor,
     ctx: Any,
     *,
     recompute_handle: Optional[Any] = None,
+    cooperative: Optional[bool] = None,
 ) -> torch.Tensor:
 
 
+@flashinfer_api
+def cake_causal_conv1d_det_multi_kcp(
+    xs: Sequence[torch.Tensor],
+    weights: Sequence[torch.Tensor],
+    ctx: Any,
+    *,
+    recompute_handle: Optional[Any] = None,
+    cooperative: Optional[bool] = None,
+) -> tuple[torch.Tensor, ...]:
+
+
 [Global Functions]
 @flashinfer_api
 def cake_fused_qk_rmsnorm_rope_append_paged_kv_cache(
@@ -198,6 +237,7 @@
     out_k: Optional[torch.Tensor] = None,
     out_v: Optional[torch.Tensor] = None,
     clear_unused_last_page_rows: bool = True,
+    enable_pdl: bool = False,
 ) -> torch.Tensor:
 [Global Functions]
 @flashinfer_api
@@ -223,6 +263,8 @@
     out_v: Optional[torch.Tensor] = None,
     q_scale: Optional[torch.Tensor] = None,
     split_k_flag: Optional[torch.Tensor] = None,
+    *,
+    enable_pdl: bool = False,
 ) -> Tuple[torch.Tensor, torch.Tensor, torch.Tensor]:
 [Global Functions]
 @flashinfer_api
@@ -245,7 +287,7 @@
 ) -> tuple[torch.Tensor, torch.Tensor]:
 [Global Functions]
 @flashinfer_api
-def cake_mhc_train_forward_prepare(
+def cake_mhc_det_train_forward_prepare(
     X: torch.Tensor,
     fn: torch.Tensor,
     scale: torch.Tensor,
@@ -261,7 +303,7 @@
 
 
 @flashinfer_api
-def cake_mhc_train_forward_stats(
+def cake_mhc_det_train_forward_stats(
     X: torch.Tensor,
     fn: torch.Tensor,
     scale: torch.Tensor,
@@ -276,7 +318,7 @@
 
 
 @flashinfer_api
-def cake_mhc_train_forward_finish(
+def cake_mhc_det_train_forward_finish(
     X: torch.Tensor,
     B: torch.Tensor,
     stats: torch.Tensor,
@@ -286,7 +328,7 @@
 
 
 @flashinfer_api
-def cake_mhc_train_backward_prepare(
+def cake_mhc_det_train_backward_prepare(
     dY: torch.Tensor,
     B: torch.Tensor,
     X: torch.Tensor,
@@ -298,7 +340,7 @@
 
 
 @flashinfer_api
-def cake_mhc_train_backward_finish(
+def cake_mhc_det_train_backward_finish(
     X: torch.Tensor,
     dY: torch.Tensor,
     dU: torch.Tensor,
@@ -322,7 +364,7 @@
 
 
 @flashinfer_api
-def cake_mhc_train_prepare(
+def cake_mhc_det_train_prepare(
     X: torch.Tensor,
     fn: torch.Tensor,
     scale: torch.Tensor,
@@ -338,17 +380,17 @@
 
 
 @flashinfer_api
-def cake_mhc_train_finish(X: torch.Tensor, B: torch.Tensor, handle) -> torch.Tensor:
+def cake_mhc_det_train_finish(X: torch.Tensor, B: torch.Tensor, handle) -> torch.Tensor:
 
 
 @flashinfer_api
-def cake_mhc_train_head_forward(
+def cake_mhc_det_train_head_forward(
     X: torch.Tensor, *, out: Optional[torch.Tensor] = None
 ) -> torch.Tensor:
 
 
 @flashinfer_api
-def cake_mhc_train_head_backward(
+def cake_mhc_det_train_head_backward(
     dY: torch.Tensor,
     *,
     dX: Optional[torch.Tensor] = None,
@@ -357,7 +399,7 @@
 
 
 @flashinfer_api
-def cake_mhc_train_head(X: torch.Tensor) -> torch.Tensor:
+def cake_mhc_det_train_head(X: torch.Tensor) -> torch.Tensor:
 class MiniMaxH3Mxfp8PreAttention:
     @flashinfer_api(trace=minimax_h3_mxfp8_pre_attention_trace)
     def run(
@@ -417,7 +459,44 @@
     ) -> tuple[torch.Tensor, torch.Tensor]:
 [Global Functions]
 @flashinfer_api
-def cake_rmsnorm_silu_gate_train_forward(
+def cake_rmsnorm_det_train_forward(
+    x: torch.Tensor,
+    w: torch.Tensor,
+    eps: float,
+    *,
+    residual: Optional[torch.Tensor] = None,
+    out: Optional[torch.Tensor] = None,
+    rstd: Optional[torch.Tensor] = None,
+    residual_out: Optional[torch.Tensor] = None,
+) -> tuple[torch.Tensor, ...]:
+
+
+@flashinfer_api
+def cake_rmsnorm_det_train_backward(
+    g: torch.Tensor,
+    x: torch.Tensor,
+    w: torch.Tensor,
+    rstd: torch.Tensor,
+    *,
+    deterministic: bool = True,
+    g_residual: Optional[torch.Tensor] = None,
+    workspace: Optional[torch.Tensor] = None,
+    dx: Optional[torch.Tensor] = None,
+    dw: Optional[torch.Tensor] = None,
+) -> tuple[torch.Tensor, torch.Tensor]:
+
+
+@flashinfer_api
+def cake_rmsnorm_det(
+    x: torch.Tensor,
+    w: torch.Tensor,
+    eps: float = 1e-6,
+    residual: Optional[torch.Tensor] = None,
+    deterministic: bool = True,
+):
+[Global Functions]
+@flashinfer_api
+def cake_rmsnorm_silu_gate_det_train_forward(
     x: torch.Tensor,
     z: torch.Tensor,
     weight: torch.Tensor,
@@ -428,7 +507,7 @@
 
 
 @flashinfer_api
-def cake_rmsnorm_silu_gate_train_backward(
+def cake_rmsnorm_silu_gate_det_train_backward(
     grad_out: torch.Tensor,
     x: torch.Tensor,
     z: torch.Tensor,
@@ -445,11 +524,73 @@
 
 
 @flashinfer_api
-def cake_rmsnorm_silu_gate(
+def cake_rmsnorm_silu_gate_det(
     x: torch.Tensor, z: torch.Tensor, weight: torch.Tensor, eps: float = 1e-6
 ) -> torch.Tensor:
 [Global Functions]
 @flashinfer_api
+def is_cake_rmsnorm_silu_gate_train_supported(
+    device: torch.device, *, deterministic: bool = True
+) -> bool:
+
+
+@flashinfer_api
+def cake_rmsnorm_silu_gate_train_forward(
+    x: torch.Tensor,
+    z: torch.Tensor,
+    weight: torch.Tensor,
+    eps: float = 1e-6,
+    *,
+    out: Optional[torch.Tensor] = None,
+    deterministic: bool = True,
+) -> torch.Tensor:
+
+
+@flashinfer_api
+def cake_rmsnorm_silu_gate_train_backward_workspace_bytes(
+    rows: int, device: torch.device, *, deterministic: bool = True
+) -> int:
+
+
+@flashinfer_api
+def cake_rmsnorm_silu_gate_train_backward_workspace(
+    rows: int, device: torch.device, *, deterministic: bool = True
+) -> torch.Tensor:
+
+
+@flashinfer_api
+def cake_rmsnorm_silu_gate_train_reset_workspace(
+    workspace: torch.Tensor, *, deterministic: bool = True
+) -> None:
+
+
+@flashinfer_api
+def cake_rmsnorm_silu_gate_train_backward(
+    grad_out: torch.Tensor,
+    x: torch.Tensor,
+    z: torch.Tensor,
+    weight: torch.Tensor,
+    eps: float = 1e-6,
+    *,
+    grad_x: Optional[torch.Tensor] = None,
+    grad_z: Optional[torch.Tensor] = None,
+    grad_weight: Optional[torch.Tensor] = None,
+    accumulate_grad_weight: bool = False,
+    compute_grad_weight: bool = True,
+    workspace: Optional[torch.Tensor] = None,
+    deterministic: bool = True,
+) -> tuple[torch.Tensor, torch.Tensor, Optional[torch.Tensor]]:
+@flashinfer_api
+def cake_rmsnorm_silu_gate(
+    x: torch.Tensor,
+    z: torch.Tensor,
+    weight: torch.Tensor,
+    eps: float = 1e-6,
+    *,
+    deterministic: bool = True,
+) -> torch.Tensor:
+[Global Functions]
+@flashinfer_api
 def cake_rmsnorm_train_forward(
     x: torch.Tensor,
     w: torch.Tensor,
@@ -459,6 +600,7 @@
     out: Optional[torch.Tensor] = None,
     rstd: Optional[torch.Tensor] = None,
     residual_out: Optional[torch.Tensor] = None,
+    deterministic: bool = True,
 ) -> tuple[torch.Tensor, ...]:
 
 
@@ -485,6 +627,8 @@
     residual: Optional[torch.Tensor] = None,
     deterministic: bool = True,
 ):
+
+
 [Global Functions]
 @flashinfer_api
 def top_k_top_p_sampling_from_probs(
@@ -581,6 +725,48 @@
 ) -> None:
 
 
+    total_tiles: int, sm_count: int
+) -> tuple[int, int, int]:
+
+
+
+
+    *,
+    arch: str,
+    per_head_profile: str,
+    selected: int,
+    mb: int,
+    fewest: int,
+    most: int,
+    tiles: int,
+    sm_count: int,
+) -> bool:
+
+
+    dense: torch.Tensor,
+    row_counts: torch.Tensor,
+    kv_block_lens: torch.Tensor,
+    *,
+    C: int,
+    mb: int,
+    num_qo_heads: int,
+    device: torch.device,
+    per_head_profile: str,
+    fewest: int,
+    most: int,
+) -> Optional[dict[str, Any]]:
+
+
+    plan: dict[str, Any],
+    q: torch.Tensor,
+    k: torch.Tensor,
+    v: torch.Tensor,
+    out: torch.Tensor,
+    stats: torch.Tensor,
+    return_lse: bool,
+) -> None:
+
+
     plan: dict[str, Any],
     q: torch.Tensor,
     k: torch.Tensor,
@@ -739,6 +925,291 @@
         rope_scale: Optional[float] = None,
         rope_theta: Optional[float] = None,
     ) -> torch.Tensor:
+[Global Functions]
+@flashinfer_api
+def capability(
+    device: Optional[Union[int, str, torch.device]] = None,
+) -> Dict[str, Any]:
+
+
+    layout: Any, device: Optional[Union[int, str, torch.device]]
+) -> bool:
+
+
+@flashinfer_api
+def payload_spec(
+    *,
+    batch_size: int,
+    local_sequence: int,
+    num_heads: int,
+    head_dim: int,
+    world_size: int,
+) -> Dict[str, Union[int, float]]:
+
+
+@flashinfer_api(trace=ulysses_lowp_k_sum_v_amax_trace)
+def k_sum_v_amax(
+    k: torch.Tensor,
+    v: torch.Tensor,
+    *,
+    out: Optional[Tuple[torch.Tensor, torch.Tensor]] = None,
+    enable_pdl: Optional[bool] = None,
+) -> Tuple[torch.Tensor, torch.Tensor]:
+
+
+
+
+@flashinfer_api(trace=ulysses_lowp_q_grouped_amax_trace)
+def q_grouped_amax(
+    q: torch.Tensor,
+    *,
+    rank: int,
+    world_size: int,
+    enable_pdl: Optional[bool] = None,
+) -> torch.Tensor:
+
+
+
+
+@flashinfer_api(trace=ulysses_lowp_k_grouped_amax_trace)
+def k_grouped_amax(
+    k: torch.Tensor,
+    k_mean_global: torch.Tensor,
+    *,
+    rank: int,
+    world_size: int,
+    used_sequence: Optional[int] = None,
+    enable_pdl: Optional[bool] = None,
+) -> torch.Tensor:
+
+
+    k, k_mean_global, rank, world_size, used_sequence, group, enable_pdl, module
+):
+
+
+
+
+    grouped_amax,
+    gathered_minmax,
+    k_mean_global,
+    rank,
+    local_sequence,
+    world_size,
+    group,
+):
+
+
+
+
+@flashinfer_api
+def boundary_descriptors(
+    grouped_amax: torch.Tensor,
+    *,
+    rank: int,
+    local_sequence: int,
+    group: int,
+    world_size: int,
+) -> torch.Tensor:
+
+
+
+
+@flashinfer_api
+def merge_boundary_amax(
+    grouped_amax: torch.Tensor,
+    gathered_descriptors: torch.Tensor,
+    *,
+    rank: int,
+    local_sequence: int,
+    group: int,
+    world_size: int,
+) -> torch.Tensor:
+
+
+    grouped_amax, gathered_descriptors, rank, local_sequence, group, world_size
+):
+
+
+@flashinfer_api
+def k_boundary_minmax(
+    k: torch.Tensor,
+    *,
+    rank: int,
+    world_size: int,
+    used_sequence: Optional[int] = None,
+) -> torch.Tensor:
+
+
+@flashinfer_api
+def derive_k_boundary_amax(
+    grouped_amax: torch.Tensor,
+    gathered_minmax: torch.Tensor,
+    k_mean_global: torch.Tensor,
+    *,
+    rank: int,
+    local_sequence: int,
+    world_size: int,
+) -> torch.Tensor:
+
+
+    send_u8: torch.Tensor,
+    *,
+    batch_size: int,
+    local_sequence: int,
+    num_heads: int,
+    world_size: int,
+    head_dim: int,
+) -> Dict[str, Union[int, float]]:
+
+
+@flashinfer_api
+def zero_scale_and_padding(
+    send_u8: torch.Tensor, spec: Dict[str, Union[int, float]]
+) -> None:
+
+
+@flashinfer_api
+def quant_q_into_payload(
+    q: torch.Tensor,
+    q_amax_final: torch.Tensor,
+    send_u8: torch.Tensor,
+    *,
+    rank: int,
+    world_size: int,
+    enable_pdl: Optional[bool] = None,
+) -> None:
+
+
+@flashinfer_api
+def quant_kv_into_payload(
+    k: torch.Tensor,
+    v: torch.Tensor,
+    k_mean_global: torch.Tensor,
+    k_amax_final: torch.Tensor,
+    v_scale_global: torch.Tensor,
+    send_u8: torch.Tensor,
+    *,
+    rank: int,
+    world_size: int,
+    enable_pdl: Optional[bool] = None,
+) -> None:
+
+
+@flashinfer_api(trace=ulysses_lowp_quant_qkv_pack_trace)
+def quant_qkv_pack(
+    q: torch.Tensor,
+    k: torch.Tensor,
+    v: torch.Tensor,
+    k_mean_global: torch.Tensor,
+    q_amax_final: torch.Tensor,
+    k_amax_final: torch.Tensor,
+    v_scale_global: torch.Tensor,
+    *,
+    rank: int,
+    world_size: int,
+    out: Optional[torch.Tensor] = None,
+    enable_pdl: Optional[bool] = None,
+) -> torch.Tensor:
+
+
+
+
+
+
+@flashinfer_api(trace=ulysses_lowp_unpack_for_sage_trace)
+def unpack_for_sage(
+    recv_u8: torch.Tensor,
+    *,
+    batch_size: int,
+    local_sequence: int,
+    local_heads: int,
+    head_dim: int,
+    world_size: int,
+    aligned: Optional[bool] = None,
+    scale_sequence: Optional[int] = None,
+    out: Optional[
+        Tuple[torch.Tensor, torch.Tensor, torch.Tensor, torch.Tensor, torch.Tensor]
+    ] = None,
+    enable_pdl: Optional[bool] = None,
+) -> Tuple[torch.Tensor, torch.Tensor, torch.Tensor, torch.Tensor, torch.Tensor]:
+
+
+    recv_u8, out, local_sequence, world_size, scale_sequence, enable_pdl, module
+):
+
+
+
+
+
+
+    n_tokens: int, world_size: int, stats_protocol: str, k_group: int = K_GROUP
+) -> int:
+
+
+@flashinfer_api
+def local_stats(
+    q: torch.Tensor,
+    k: torch.Tensor,
+    v: torch.Tensor,
+    *,
+    rank: int,
+    world_size: int,
+    used_sequence: Optional[int] = None,
+    enable_pdl: Optional[bool] = None,
+) -> Tuple[torch.Tensor, StatsContext]:
+
+
+    q, k, v, rank, world_size, used_sequence, q_group, k_group, enable_pdl, module
+):
+
+
+@flashinfer_api
+def finalize_stats(
+    gathered: torch.Tensor,
+    ctx: StatsContext,
+    k: torch.Tensor,
+    *,
+    enable_pdl: Optional[bool] = None,
+) -> V2GStats:
+
+
+
+
+@flashinfer_api
+def quant_and_pack(
+    q: torch.Tensor,
+    k: torch.Tensor,
+    v: torch.Tensor,
+    stats: V2GStats,
+    *,
+    out: Optional[torch.Tensor] = None,
+    enable_pdl: Optional[bool] = None,
+) -> torch.Tensor:
+
+
+@flashinfer_api
+def verify_duplicate_scale_slots(
+    recv_u8: torch.Tensor,
+    *,
+    batch_size: int,
+    local_sequence: int,
+    local_heads: int,
+    head_dim: int,
+    world_size: int,
+    q_group: int = Q_GROUP,
+    k_group: int = K_GROUP,
+    spec: Optional[Dict[str, Union[int, float]]] = None,
+) -> bool:
+
+
+@flashinfer_api
+def quant_v_fp8_with_scale(
+    v: torch.Tensor,
+    v_scale_global: torch.Tensor,
+    scale_max: float = V_SCALE_MAX,
+    *,
+    enable_pdl: Optional[bool] = None,
+) -> torch.Tensor:
 class TRTLLMAllReduceFusionWorkspace(AllReduceFusionWorkspace):
     @flashinfer_api
     def checkpoint_prepare(self) -> None:
@@ -1139,6 +1610,26 @@
     @flashinfer_api
     def create_workspace(self, *, max_elems: Optional[int] = None) -> UlyssesWorkspace:
 
+    @flashinfer_api
+    def prepare_qkv(
+        self,
+        qkv_shape: Sequence[int],
+        *,
+        quantization: str = "sage2",
+        used_sequence: Optional[int] = None,
+    ) -> UlyssesQKVWorkspace:
+
+    @flashinfer_api(trace=ulysses_scatter_qkv_trace_dispatch)
+    def scatter_qkv(
+        self,
+        q: torch.Tensor,
+        k: torch.Tensor,
+        v: torch.Tensor,
+        *,
+        workspace: UlyssesQKVWorkspace,
+        out: Optional[UlyssesQKV] = None,
+    ) -> UlyssesQKV:
+
     @flashinfer_api(trace=ulysses_scatter_heads_trace)
     def scatter_heads(
         self,
@@ -1403,9 +1894,9 @@
     block_tables: Optional[torch.Tensor] = None,
     causal: bool,
     return_lse: bool,
-    q_scale: Optional[torch.Tensor] = None,
-    k_scale: Optional[torch.Tensor] = None,
-    v_scale: Optional[torch.Tensor] = None,
+    q_scale: Optional[Union[float, torch.Tensor]] = None,
+    k_scale: Optional[Union[float, torch.Tensor]] = None,
+    v_scale: Optional[Union[float, torch.Tensor]] = None,
     batch_offsets_q: Optional[torch.Tensor] = None,
     batch_offsets_o: Optional[torch.Tensor] = None,
     batch_offsets_k: Optional[torch.Tensor] = None,
@@ -1418,6 +1909,8 @@
     backend: Optional[str] = None,
     o_data_type: Optional[torch.dtype] = None,
     lse_base: str = "log2",
+    window_left: Optional[int] = None,
+    sinks: Optional[torch.Tensor] = None,
 ) -> tuple[torch.Tensor, Optional[torch.Tensor]]:
 [Global Functions]
 @flashinfer_api(trace=add_rmsnorm_fp4quant_trace_dispatch)
@@ -1881,6 +2374,7 @@
     request_order: Optional[torch.Tensor] = None,
     request_order_plan: Optional[Any] = None,
     sparse_top_k: int = 0,
+    length_aware_schedule: bool = False,
 ) -> Union[
     torch.Tensor, FP4Tensor, Tuple[Union[torch.Tensor, FP4Tensor], torch.Tensor]
 ]:
@@ -3337,7 +3831,7 @@
     enable_pdl: Optional[bool] = None,
     activation_type: ActivationType = ActivationType.Swiglu,
     swizzled_input_sf: bool = True,
-    use_fused_finalize: bool = True,
+    use_fused_finalize: Optional[bool] = None,
     profile_ids: Optional[List[int]] = None,
     workspace_buffer: Optional[torch.Tensor] = None,
     *,
@@ -3367,7 +3861,7 @@
     use_deepseek_fp8_block_scale: bool = False,
     use_w4_group_scaling: bool = False,
     use_mxfp8_act_scaling: bool = False,
-    use_fused_finalize: bool = True,
+    use_fused_finalize: Optional[bool] = None,
     use_packed_weights: bool = False,
     use_wfp4afp8_humming: bool = False,
     device: Optional[torch.device] = None,
@@ -3742,6 +4236,7 @@
     hidden_states_scale_layout: Optional[SfLayout] = None,
     workspace_buffer: Optional[torch.Tensor] = None,
     nvfp4_4over6: Optional[NVFP44Over6Config] = _UNSET,
+    routing_metadata: Optional[TrtllmMoERoutingMetadataSlot] = None,
 ) -> List[torch.Tensor]:
 
 
@@ -3955,6 +4450,8 @@
         situ_linear_beta: Optional[float] = None,
         use_fused_finalize: bool = True,
         quant_mode: str = "w4a4",
+        clamped_relu2_limit: Optional[torch.Tensor] = None,
+        swap_ab: bool = False,
     ):
 
     @flashinfer_api(trace=cute_dsl_moe_wrapper_run_trace)
@@ -4019,6 +4516,8 @@
     localized_allow_nonlocalized: bool = False,
     autotune_use_cuda_graph: bool = False,
     nvfp4_4over6: Optional[NVFP44Over6Config] = _UNSET,
+    clamped_relu2_limit: Optional[torch.Tensor] = None,
+    swap_ab: bool = False,
 ) -> torch.Tensor:
 @flashinfer_api(trace=cute_dsl_fused_moe_trace)
 def cute_dsl_fused_moe_nvfp4(
@@ -4058,6 +4557,7 @@
     localized_allow_nonlocalized: bool = False,
     autotune_use_cuda_graph: bool = False,
     nvfp4_4over6: Optional[NVFP44Over6Config] = _UNSET,
+    clamped_relu2_limit: Optional[torch.Tensor] = None,
 ) -> torch.Tensor:
 @flashinfer_api(trace=cute_dsl_fused_moe_mxfp8_mxfp4_trace)
 def cute_dsl_fused_moe_mxfp8_mxfp4(
@@ -4514,6 +5014,25 @@
     device: Optional[torch.device] = None,
 ) -> Dict[str, torch.Tensor]:
 
+@flashinfer_api
+def interleave_cute_dsl_moe_weights(
+    weight: torch.Tensor, block_scales: torch.Tensor, swap_ab: bool = False
+) -> Tuple[torch.Tensor, torch.Tensor]:
+
+
+    w1_bf16: torch.Tensor,
+    w2_bf16: torch.Tensor,
+    *,
+    quant: QuantConfig,
+    num_local_experts: int,
+    hidden_size: int,
+    intermediate_size: int,
+    activation=None,
+    device: Optional[torch.device] = None,
+    nvfp4_4over6: Optional[NVFP44Over6Config] = None,
+    swap_ab: bool = False,
+) -> Dict[str, Union[torch.Tensor, int]]:
+
 [Global Functions]
 @flashinfer_api(trace=trtllm_gen_routing_trace)
 def trtllm_gen_routing(
@@ -5019,7 +5538,7 @@
     a: torch.Tensor,
     b: torch.Tensor,
     bias: Optional[torch.Tensor] = None,
-    pdl: bool = False,
+    pdl: Optional[bool] = False,
     out: Optional[torch.Tensor] = None,
     out_dtype: torch.dtype = torch.bfloat16,
     backend: Literal[
@@ -5032,6 +5551,8 @@
         "cute-dsl",
         "auto",
     ] = "cudnn",
+    *,
+    batch_invariant: bool = False,
 ) -> torch.Tensor:
     A: torch.Tensor,
     B: torch.Tensor,
@@ -5347,6 +5868,7 @@
     dtype: torch.dtype,
     out: Optional[torch.Tensor] = None,
     backend: Literal["cudnn", "cublas", "cutlass", "auto"] = "cublas",
+    batch_invariant: bool = False,
 ):
     A: torch.Tensor,
     B: torch.Tensor,
@@ -5355,6 +5877,7 @@
     dtype: torch.dtype,
     out: Optional[torch.Tensor] = None,
     backend: Literal["cudnn", "cublas", "cutlass", "auto"] = "cublas",
+    batch_invariant: bool = False,
 ):
     A: torch.Tensor,
     B: torch.Tensor,
@@ -5363,6 +5886,7 @@
     dtype: torch.dtype,
     out: Optional[torch.Tensor] = None,
     backend: Literal["cudnn", "cublas", "cutlass", "auto"] = "cublas",
+    batch_invariant: bool = False,
 ):
     A: torch.Tensor,
     B: torch.Tensor,
@@ -5371,6 +5895,7 @@
     dtype: torch.dtype,
     out: Optional[torch.Tensor] = None,
     backend: Literal["cudnn", "cublas", "cutlass", "cute-dsl", "auto"] = "cublas",
+    batch_invariant: bool = False,
 ):
     A: torch.Tensor,
     B: torch.Tensor,
@@ -5379,6 +5904,7 @@
     dtype: torch.dtype,
     out: Optional[torch.Tensor] = None,
     backend: Literal["cudnn", "cublas", "cutlass", "auto"] = "cublas",
+    batch_invariant: bool = False,
 ):
 
 
@@ -5390,6 +5916,7 @@
     dtype: torch.dtype,
     out: Optional[torch.Tensor] = None,
     backend: Literal["cudnn", "cublas", "cutlass", "cute-dsl", "auto"] = "cublas",
+    batch_invariant: bool = False,
 ):
 @flashinfer_api(trace=bmm_fp8_trace)
 def bmm_fp8(
@@ -5400,6 +5927,8 @@
     dtype: torch.dtype,
     out: Optional[torch.Tensor] = None,
     backend: Literal["cudnn", "cublas", "cutlass", "cute-dsl", "auto"] = "cublas",
+    *,
+    batch_invariant: bool = False,
 ) -> torch.Tensor:
     a: torch.Tensor,
     b: torch.Tensor,
@@ -6171,6 +6700,34 @@
 ):
 [Global Functions]
 @flashinfer_api
+def causal_conv1d_fn(
+    x: torch.Tensor,
+    weight: torch.Tensor,
+    conv_state: torch.Tensor,
+    cu_seqlens: torch.Tensor,
+    cache_indices: torch.Tensor,
+    has_initial_state: Optional[torch.Tensor] = None,
+    *,
+    bias: Optional[torch.Tensor] = None,
+    out: Optional[torch.Tensor] = None,
+    workspace: Optional[torch.Tensor] = None,
+) -> torch.Tensor:
+
+
+@flashinfer_api
+def causal_conv1d_update(
+    x: torch.Tensor,
+    weight: torch.Tensor,
+    conv_state: torch.Tensor,
+    state_indices: torch.Tensor,
+    *,
+    cu_seqlens: Optional[torch.Tensor] = None,
+    num_accepted_tokens: Optional[torch.Tensor] = None,
+    bias: Optional[torch.Tensor] = None,
+    out: Optional[torch.Tensor] = None,
+) -> torch.Tensor:
+[Global Functions]
+@flashinfer_api
 def checkpointing_ssu(
     state: torch.Tensor,
     x_cache: torch.Tensor,
@@ -9050,6 +9607,20 @@
     scale: float = 1 / 16,
 ) -> tuple[torch.Tensor, torch.Tensor, torch.Tensor]:
 [Global Functions]
+@flashinfer_api
+def encode_csf_scales(scales: torch.Tensor) -> CsfScales:
+
+
+@flashinfer_api
+def expand_csf_scales(
+    csf: CsfScales,
+    out: torch.Tensor,
+    token_selected_experts: Optional[torch.Tensor] = None,
+    layout: SfLayout = SfLayout.layout_linear,
+    swap_row_halves: bool = False,
+    local_expert_offset: int = 0,
+) -> torch.Tensor:
+[Global Functions]
 @flashinfer_api(trace=silu_and_mul_nvfp4_quantize_trace)
 def silu_and_mul_nvfp4_quantize(
     input: torch.Tensor,
@@ -9063,6 +9634,17 @@
 ) -> Tuple[torch.Tensor, torch.Tensor]:
 
 
+    input: torch.Tensor,
+    sf_vec_size: int,
+    sf_use_ue8m0: bool,
+    nvfp4_4over6: Optional[NVFP44Over6Config],
+) -> Optional[NVFP44Over6Config]:
+
+
+    sf_vec_size: int, sf_use_ue8m0: bool
+) -> ValueError:
+
+
 @flashinfer_api(trace=fp4_quantize_trace)
 def fp4_quantize(
     input: torch.Tensor,
@@ -9073,9 +9655,11 @@
     is_sf_8x4_layout: bool = False,
     is_global_scale_inversed: bool = False,
     enable_pdl: Optional[bool] = None,
-    backend: str = "cuda",
+    backend: str = "auto",
     # Appended last so existing positional construction keeps working.
     nvfp4_4over6: Optional[NVFP44Over6Config] = _UNSET,
+    *,
+    batch_invariant: bool = False,
 ) -> Tuple[torch.Tensor, torch.Tensor]:
     input: torch.Tensor,
     global_scale: Optional[torch.Tensor] = None,
@@ -9149,21 +9733,25 @@
     do_shuffle=False,
     sf_vec_size=16,
     enable_pdl=None,
-    backend: str = "cuda",
+    backend: str = "auto",
     per_token_activation: bool = False,
     expanded_idx_to_permuted_idx: Optional[torch.Tensor] = None,
     out_scale: Optional[torch.Tensor] = None,
     # Appended last so existing positional construction keeps working.
     nvfp4_4over6: Optional[NVFP44Over6Config] = _UNSET,
+    *,
+    batch_invariant: bool = False,
 ):
 
 
 @flashinfer_api(trace=mxfp4_quantize_trace)
 def mxfp4_quantize(
     a: torch.Tensor,
-    backend: str = "cuda",
+    backend: str = "auto",
     enable_pdl: Optional[bool] = None,
     sfLayout: SfLayout = SfLayout.layout_128x4,
+    *,
+    batch_invariant: bool = False,
 ) -> Tuple[torch.Tensor, torch.Tensor]:
 
 
@@ -9247,8 +9835,10 @@
     is_sf_swizzled_layout: bool = True,
     alignment: int = 32,
     enable_pdl: Optional[bool] = None,
-    backend: Literal["cuda", "cute-dsl"] = "cuda",
+    backend: Literal["auto", "cuda", "cute-dsl"] = "auto",
     sf_swizzle_layout: Optional[SfLayout] = None,
+    *,
+    batch_invariant: bool = False,
 ) -> Tuple[torch.Tensor, torch.Tensor]:
 @flashinfer_api(trace=mxfp8_grouped_quantize_trace)
 def mxfp8_grouped_quantize(
@@ -9285,23 +9875,11 @@
     column_major_scales: bool = False,
     scale_tma_aligned: bool = False,
     scale_ue8m0: bool = False,
-    backend: Literal["cutile"] = "cutile",
+    backend: Literal["cutile", "cuda"] = "cutile",
 ) -> Tuple[torch.Tensor, torch.Tensor]:
-[Global Functions]
-@flashinfer_api
-def mxfp4_quantize_cute_dsl(
-    input: torch.Tensor,
-    sf_layout: int = SF_LAYOUT_128x4,
-    enable_pdl: bool | None = None,
-) -> Tuple[torch.Tensor, torch.Tensor]:
-[Global Functions]
-@flashinfer_api
-def mxfp8_quantize_cute_dsl(
-    input: torch.Tensor,
-    is_sf_swizzled_layout: bool = True,
-    alignment: int = 32,
-    enable_pdl: bool | None = None,
-    is_sf_8x4_layout: bool = False,
+
+
+    x: torch.Tensor, backend: Literal["cuda", "cute-dsl"] = "cuda"
 ) -> Tuple[torch.Tensor, torch.Tensor]:
 [Global Functions]
 @flashinfer_api
@@ -9318,47 +9896,31 @@
     kv_page_indptr: Optional[torch.Tensor] = None,
     num_pages: Optional[int] = None,
 ) -> Tuple[torch.Tensor, torch.Tensor]:
-[Global Functions]
-@flashinfer_api
-def nvfp4_quantize_cute_dsl(
-    input: torch.Tensor,
-    global_scale: float | torch.Tensor,
-    sf_layout: int = SF_LAYOUT_128x4,
-    enable_pdl: bool | None = None,
-    # Appended last so existing positional construction keeps working.
-    nvfp4_4over6: Optional[NVFP44Over6Config] = _UNSET,
-    out: Optional[Tuple[torch.Tensor, torch.Tensor]] = None,
-) -> Tuple[torch.Tensor, torch.Tensor]:
-
-
-    input: torch.Tensor,
-    pre_quant_scale: torch.Tensor,
-    global_scale: torch.Tensor,
-    enable_pdl: bool | None = None,
-    # Appended last so existing positional construction keeps working.
-    nvfp4_4over6: Optional[NVFP44Over6Config] = _UNSET,
-) -> Tuple[torch.Tensor, torch.Tensor]:
-
-
-    input: torch.Tensor,
-    global_scale: torch.Tensor,
-    sf_layout: int = SF_LAYOUT_128x4,
-    enable_pdl: bool | None = None,
-    # Appended last so existing positional construction keeps working.
-    nvfp4_4over6: Optional[NVFP44Over6Config] = _UNSET,
-) -> Tuple[torch.Tensor, torch.Tensor]:
-
+class NVFP4KVMaterializer:
+    @flashinfer_api
+    def __init__(
+        self,
+        num_kv_heads: int,
+        page_size: int,
+        head_dim: int,
+        device: Union[str, int, torch.device] = "cuda",
+        uses_shared_paged_kv_idx: bool = True,
+    ) -> None:
 
-@flashinfer_api
-def nvfp4_quantize_per_token_cute_dsl(
-    input: torch.Tensor,
-    global_scale_inv: torch.Tensor,
-    sf_layout: int = SF_LAYOUT_128x4,
-    enable_pdl: bool | None = None,
-    out_scale: torch.Tensor | None = None,
-    # Appended last so existing positional construction keeps working.
-    nvfp4_4over6: Optional[NVFP44Over6Config] = _UNSET,
-) -> Tuple[torch.Tensor, torch.Tensor, torch.Tensor]:
+    @flashinfer_api
+    def run(
+        self,
+        k_cache: torch.Tensor,
+        v_cache: torch.Tensor,
+        k_block_scales: torch.Tensor,
+        v_block_scales: torch.Tensor,
+        block_tables: torch.Tensor,
+        seq_lens: torch.Tensor,
+        kv_page_indptr: torch.Tensor,
+        *,
+        out: torch.Tensor,
+        fp8_block_tables: torch.Tensor,
+    ) -> Tuple[torch.Tensor, torch.Tensor]:
 [Global Functions]
 @flashinfer_api
 def packbits(x: torch.Tensor, bitorder: str = "big") -> torch.Tensor:
@@ -9654,6 +10216,7 @@
     x: torch.Tensor,
     top_k: Union[torch.Tensor, int],
     top_p: Union[torch.Tensor, float],
+    indices: Optional[torch.Tensor],
     *,
     top_k_max: Optional[int] = None,
     from_logits: bool,
@@ -9732,6 +10295,89 @@
     seed: Optional[Union[int, torch.Tensor]] = None,
     offset: Optional[Union[int, torch.Tensor]] = None,
 ) -> Tuple[torch.Tensor, torch.Tensor, torch.Tensor]:
+[Global Functions]
+@flashinfer_api(trace=indexer_scores_trace)
+def indexer_scores(
+    query: torch.Tensor,
+    key_cache: torch.Tensor,
+    block_table: torch.Tensor,
+    context_lengths: torch.Tensor,
+    *,
+    requests: torch.Tensor,
+    scores: torch.Tensor,
+    query_scales: Optional[torch.Tensor] = None,
+    key_scales: Optional[torch.Tensor] = None,
+) -> None:
+
+
+
+
+@flashinfer_api(trace=indexer_threshold_select_trace)
+def indexer_threshold_select(
+    query: torch.Tensor,
+    key_cache: torch.Tensor,
+    row_ends: torch.Tensor,
+    tile_requests: torch.Tensor,
+    block_table: torch.Tensor,
+    *,
+    thresholds: torch.Tensor,
+    counters: torch.Tensor,
+    candidates: torch.Tensor,
+    max_context: int,
+    top_k: int,
+    query_scales: Optional[torch.Tensor] = None,
+    key_scales: Optional[torch.Tensor] = None,
+    arrivals: Optional[torch.Tensor] = None,
+    ranges: Optional[torch.Tensor] = None,
+) -> None:
+
+
+@flashinfer_api(trace=top_k_from_candidates_trace)
+def top_k_from_candidates(
+    candidates: torch.Tensor,
+    ranges: torch.Tensor,
+    *,
+    top_keys: torch.Tensor,
+) -> None:
+
+
+@flashinfer_api(trace=quantize_write_index_qk_nvfp4_trace)
+def quantize_write_index_qk_nvfp4(
+    key: torch.Tensor,
+    slots: torch.Tensor,
+    query: torch.Tensor,
+    query_rows: torch.Tensor,
+    *,
+    key_cache: torch.Tensor,
+    key_scales: torch.Tensor,
+    packed_query: torch.Tensor,
+    query_scales: torch.Tensor,
+) -> None:
+
+
+@flashinfer_api(trace=gather_key_sample_trace)
+def gather_key_sample(
+    key_cache: torch.Tensor,
+    block_table: torch.Tensor,
+    offsets: torch.Tensor,
+    sample_ends: torch.Tensor,
+    *,
+    sample_keys: torch.Tensor,
+    samples_per_run: int,
+    pages_per_run: int,
+    key_scales: Optional[torch.Tensor] = None,
+    sample_scales: Optional[torch.Tensor] = None,
+) -> None:
+
+
+@flashinfer_api(trace=thresholds_from_sample_trace)
+def thresholds_from_sample(
+    sample_scores: torch.Tensor,
+    sample_top: torch.Tensor,
+    *,
+    thresholds: torch.Tensor,
+    counters: torch.Tensor,
+) -> None:
 class BlockSparseAttentionWrapper:
     @flashinfer_api
     def __init__(
```

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

- [ ] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

Version-only change, no new tests. Release validation runs on
`release-v0.7.4`.

- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).

## 🔬 Experimental Track

- [ ] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.
Tracking issue: #

```experimental-tests
```

### [7752881](https://github.com/flashinfer-ai/flashinfer/commit/77528818d83b712e1805eec1e9e36700c2091d09)

- **作者**: Yang Xu
- **时间**: 2026-11-10T08:09:28Z
- **提交信息**: feat(moe): add grouped packed NVFP4 Tensor Core candidates to Frost (#7384)

<!-- .github/pull_request_template.md -->

## 📌 Description

Add bounded grouped Tensor Core candidates for packed NVFP4 weights with
16-bit activations. Multiple routed tokens that share an expert reuse
its weight tile; weights remain packed in global/shared memory and
expand into typed MMA register fragments with their live block scales.
FC1/FC2 expert scales keep their existing positions relative to the dot
product and activation.

| Architecture | Candidate region |
|---|---|
| SM103 | BF16 or FP16, matching output dtype; T8/H2048/I512/top-k10,
default SwiGLU, finalized output; K256 with route groups4/8 |
| SM120 | BF16 or FP16 with matching output; the same shape/activation
envelope; K128/K256 with route groups4/8 |

SM120 group8/stages2/K256 additionally requires the loaded CuTe DSL cu13
compiler component; cu12, missing and future unknown components decline
that candidate. Enumeration, explicit execution and tuning-cache
identity share the compiler boundary. The other three SM120 choices
remain available on cu12.

This extends the shared warp-MMA pipeline and reuses preparation,
routing, typed activation, workspace binding and ordered combine. The
shared projection also preserves the predecessor's bounded SM90 BF16
W8A16 K256 candidates; packed-NVFP4 format and architecture admission
remain unchanged. All existing FMA candidates remain available, and
untuned dispatch is unchanged. Tune with representative routes and cache
conditions: a cached choice does not automatically adapt to changes in
expert reuse.

This PR now targets main after #7379 merged. The in-repo reproducer and
[quantitative performance
report](https://github.com/flashinfer-ai/flashinfer/pull/7384#issuecomment-6487404501)
are available. Historical SM103 shared/half-reuse measurements show
1.188–1.753× versus offline-expanded CUTLASS (four times the packed
weight storage). SM120 FP16 shared/half reuse shows 1.294–1.658× versus
the best retained FFMA/packed-native baseline, while disjoint/uniform
routes lose. The report includes absolute timings, candidate pools,
tactics, warm/cold conditions, numerical contracts and environment
details. These are archived-source routed-expert GPU measurements, not
final-head or model-throughput qualification.

Current integration head `b3dd4df1ec9ab9c67df0780e3e4b7c4c89decb10`
merges main at `b1cf76608bb6519b5e5fc7972c490fb96c9258d4` and resolves
the overlap between packed NVFP4 scale staging and the landed
weight-first producer ordering. The follow-up rejects packed NVFP4
combined with the serial weight-first producer before constructing the
kernel; the new metadata-only JIT regression covers BF16 and FP16.
Current-head independent review found no new actionable defect and
required public checks pass. The historical report and separate
final-head SM120/SM103 performance reports are now published (linked
below). Final-head measurement is complete for the declared synthetic
workloads. On November 10, 2026, the owner accepted the published scoped
performance evidence and authorized normal merge with the existing
approval and required checks enforced.

## 🔍 Related Issues

Builds on merged #7379 and #7368. This batch includes matching FP16
activation/output on SM120 within the same bounded SwiGLU region.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [x] Ran scoped hooks with `pre-commit run --files`; all passed.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

Current head `b3dd4df1ec9ab9c67df0780e3e4b7c4c89decb10` has independent
review, 73 CPU test passes and 36 offline compilations; these are not
GPU executions. Required public checks pass. Existing native CI
qualifies preceding integration
`36f0bb2018d5742a287535769e0bac42aadf11b7`, including 17 grouped-NVFP4
tests on SM120. The following guard leaves admitted paths unchanged; CI
revision attribution is preserved. Separate final-head SM120 and SM103
benchmark matrices now cover 12 conditions each with post-replay
correctness and actual kernel-route proof; see the reports below for
scope and limitations. The historical results below and the October 26
report retain their original revision attribution.

- Scoped pre-commit checks passed for the changed files.
- At previous head `5f03e1f958b99b48ffc44ce54834e845f32cbbeb`, after
merging main and addressing review feedback: 17 CPU
compiler-admission/cache tests passed with no skips; four CPU helper
checks confirm incorrect output dtypes are rejected and matching
BF16/FP16 dtypes remain valid. No new GPU test run is claimed for this
documentation/test-assertion update. The only projection-source
difference from the reviewed head is a ValueError message; its AST is
otherwise unchanged.
- Targeted local correctness, graph replay,
fresh-storage/nondefault-stream binding, and regression checks completed
on the implemented architectures. The cumulative combination preserves
packed-NVFP4 cooperative gathering while incorporating the predecessor
W8A16 scheduling change.
- The grouped NVFP4 suite covers live packed weights, block/expert
scales and routes, packed/unpacked routing, invalid IDs with nonfinite
scores, workspace poisoning, graph replay, dtype boundaries and excluded
configurations. Sanitizer checks cover the admitted device paths.
- `benchmarks/bench_frost_low_latency_w4a16.py` measures the complete
routed-expert GPU interval and retains captured outputs for reference
validation. SM120 has a packed native comparator. SM103 expanded CUTLASS
controls require four times the packed weight storage and exclude
offline expansion from timing; the script labels this explicitly.

- [x] Tests have been added or updated as needed.
- [x] Required public checks and the declared targeted validation
passed; full-repository test coverage is not claimed.

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

Review packed-nibble and block-scale indexing, gate/up row mapping,
shared-stage synchronization, typed preactivation/expert-output
rounding, and current-pointer binding. The new packed-NVFP4 candidates
have their own bounded K256 admission; the predecessor's dense/W8A16
choices are preserved. Native and Frost FP16 preactivation/expert-output
rounding boundaries differ and are checked against their respective
references. Admission is deliberately bounded to the tested geometry and
activation. This remains a three-kernel projection/activation/combine
pipeline.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added grouped NVFP4 execution for selected low-latency MoE workloads
on SM120 and SM103, supporting BF16 and FP16 inputs and outputs.
* Added grouped Tensor Core execution choices for eligible W8A16
workloads on SM90, SM103, and SM120, alongside existing options.
* Expanded benchmark comparisons to include FP16, additional activations
and routing patterns, and the `half` expert-reuse option. Expanded-BF16
benchmarking is now available on SM103.
* **Documentation**
* Added guidance on supported configurations, execution choices,
benchmark comparisons, and numerical boundaries.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### Current-head performance follow-up

The [November 1 SM120
report](https://github.com/flashinfer-ai/flashinfer/pull/7384#issuecomment-6553151980)
and [November 1 SM103
report](https://github.com/flashinfer-ai/flashinfer/pull/7384#issuecomment-6563153424)
both execute `b3dd4df1ec9ab9c67df0780e3e4b7c4c89decb10` across
BF16/FP16, shared/half/disjoint expert reuse and warm/cold cache: 12
conditions per architecture. Each reports absolute
FFMA/grouped-TC/native timings, selected tactics, post-replay
correctness and actual kernel traces, including low-reuse TC losses.

The baselines differ: SM120 uses packed native; SM103 uses
offline-expanded BF16/FP16 CUTLASS with 4x payload storage and excluded
expansion cost. The SM103 dataset is from a disclosed engineering board
and includes a material difference between single-call CUPTI and chained
CUDA-event timing. These synthetic routed-expert results are not
model/vLLM E2E qualification. The October 26 report above remains
historical.

Final-head measurement is complete within those declared scopes. **The
owner accepted this scoped evidence and authorized normal merge on
November 10, 2026.** This records the owner's merge decision; it does
not represent a new reviewer approval or a serving E2E result.

<!-- pr7384-final-head-sm120-link:v1536 -->
<!-- pr7384-final-head-sm103-link:v1581 -->

### [8e0a8af](https://github.com/flashinfer-ai/flashinfer/commit/8e0a8afd6fda653d65661cb2feb7d122a3d9b681)

- **作者**: Adrian
- **时间**: 2026-11-10T07:23:15Z
- **提交信息**: test(comm): use a private file store for MXFP8 rendezvous (#8998)

<!-- .github/pull_request_template.md -->

## 📌 Description

The November 5, 2026 nightly pipeline 79471854 failed the B200 CUDA 13.4
unified MXFP8 all-reduce test with `TCPStore EADDRINUSE`; peers then
waited for connection timeouts. The helper selected an ephemeral TCP
port and closed its socket before starting workers, allowing another
process to claim the port.

Use a fresh temporary file store for each local worker group. Keep its
directory alive until workers finish and use
`torch.multiprocessing.spawn` to propagate child failures and terminate
peers. Both the legacy and unified API workers use the same launcher.

## 🔍 Related Issues

Found in the November 5, 2026 nightly pipeline 79471854.

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

Pre-commit hooks passed on the changed file.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust):
`tests/comm/test_trtllm_allreduce_fusion_mxfp8.py`

Validation: real two-rank Gloo all-reduces, concurrent invocations with
separate stores, and child-failure propagation with peer termination and
directory cleanup. Multi-GPU NCCL cases require CI; this host has one
GPU. No new tests were added.

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
* Updated multiprocess test setup to use a temporary file-based
rendezvous instead of a manually managed TCP connection.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [ccf0baa](https://github.com/flashinfer-ai/flashinfer/commit/ccf0baafb46063245d111f29c3cc35dca2ce65e4)

- **作者**: Jimmy Zhou
- **时间**: 2026-11-10T07:18:37Z
- **提交信息**: fix(cake_rmsnorm): cap the H 2048 backward main kernels at 120 registers so they start beside an all-SM kernel (#9037)

## Problem


`test_cake_rmsnorm_det_train_stall.py::test_calls_beside_an_all_sm_kernel_with_the_max_shared_carveout`
and `::test_calls_beside_an_all_sm_kernel_holding_shared_memory` fail on
GB300 with the CUDA 12.9 and 13.0 CI images (passing with CUDA 13.4), on
main and in the v0.7.4rc1 CI run (#8466):

```
wait but not in WHOLE_SM: [('bwd', 2048, False, 'bf16', 55296, None, 65536), ('bwd', 2048, False, 'f32', 32768, 55296, 44032), ('bwd', 2048, False, 'f32', 55296, None, 65536)]
```

The H 2048 backward at large token counts waits until the whole lifetime
of a kernel resident on every SM has passed, instead of starting beside
it. The package documents that only the residual H 6144 backward does
that on SM100/SM103.

## Root cause

The work unit of these backward programs is one block (CTA) of 512
threads per SM, launched with `__launch_bounds__(512, 1)`, so nvcc may
give them up to 128 registers per thread. Registers are allocated per
warp in units of 8 per thread. Each SM has four sub-partitions with 16 K
registers each, and a 512-thread block puts four warps on each of them:

- at 120 registers or fewer, the four warps take at most 15 K, which
leaves room for one warp of a kernel resident on another stream;
- at 121-128 registers (rounded up to 128), the four warps take all 16
K, so the block cannot start until the resident kernel leaves.

Register counts from `ptxas -v` with the package's own flags, in the CI
images:

| program (arch) | CUDA 12.9 | CUDA 13.0 | CUDA 13.4 |
|---|---|---|---|
| `018f0cd7` H 2048 BF16 top window (sm_103a) | 121 | 121 | 119 |
| `ca8ca467` H 2048 FP32-weight top window (sm_103a) | 121 | 121 | 118 |
| `e98cb156` H 2048 FP32-weight (32768, 55296] (sm_103a) | 121 | 112 |
114 |
| `2fa223ac` H 2048 BF16 top window (sm_100a, main only) | 119 | 123 |
113 |

The rows at 121-123 are exactly the windows the CI run reports as
waiting, toolkit by toolkit. The package was rendered and measured with
CUDA 13.4, but it supports CUDA 12.9 and newer. The non-deterministic
package (`cake_rmsnorm_train`) ships byte-identical copies of the three
sm_103a programs in its large-T det-pair windows.

## Fix

Replace `__launch_bounds__(512, LAUNCH_MIN_BLOCKS)` with
`__maxnreg__(120)` on these seven kernel sources (four in
`cake_rmsnorm_det_train`, three in `cake_rmsnorm_train`). nvcc rejects
the two qualifiers on one kernel, and `-maxrregcount` is ignored for a
kernel with launch bounds. Each `build.json` entry gets the new source
digest and a new closure digest, so a stale JIT cache entry is never
reused. With the cap, every toolkit compiles them at 120 registers or
fewer with no spills.

## Validation

Release-v0.7.4 (a2599b01b) on GB300, the CI images
`flashinfer-ci-cu129`, `-cu130` and `-cu134` (tag `20260930-b1420f1`),
before and after this patch (adapted to the release branch, which does
not have `2fa223ac`):

| GB300 | release-v0.7.4 | + this patch |
|---|---|---|
| CUDA 12.9 | 2 failed (the 3 windows above wait) | 2 passed |
| CUDA 13.0 | 2 failed (2 windows wait) | 2 passed |
| CUDA 13.4 | 2 passed | 2 passed |

B200 with CUDA 13.0, main (which adds `2fa223ac`, 123 registers there):
before, the BF16 H 2048 top window waits and both tests fail. After, the
window starts and
`test_calls_beside_an_all_sm_kernel_with_the_max_shared_carveout`
passes. The shared-memory variant was skipped because the side kernel
could not hold every SM on the shared test box.

Non-regression: the 16 `tests/norm/test_cake_rmsnorm_*train*.py` files
(both packages), patched tree:

- GB300, release-v0.7.4 + patch: CUDA 12.9: 2480 passed / 196 skipped.
CUDA 13.0: 2481 / 195. CUDA 13.4: 2481 / 195. No failures.
- B200, CUDA 13.0, main + this patch + #9038: 2480 passed / 196 skipped.
No failures.
- R200 dev box, CUDA 13.4: the only failures (5 in
`test_cake_rmsnorm_det_train_pairs.py::test_workspace_puts_the_counters_first_and_grows_with_the_rows`
and the 2 `det_train_stall` all-SM tests on small-T sm_107a windows)
fail identically on unpatched release-v0.7.4 on that box. They do not
fail in the VR CI job.

Fixes #8466


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* Updated RMSNorm training kernels with an explicit register limit and
revised GPU scheduling constraints. This may affect kernel occupancy and
execution performance.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [504035d](https://github.com/flashinfer-ai/flashinfer/commit/504035ddab474b0b90c8ee48f0347963d4619dc6)

- **作者**: Yuxian Qiu
- **时间**: 2026-11-10T07:05:18Z
- **提交信息**: fix(prims-ts): work around QuACK AST rewrite in MLA reduction (#9087)

<!-- .github/pull_request_template.md -->

## 📌 Description

When QuACK is imported before PrimTS compilation, its process-wide patch
of CuTe's `DSLPreprocessor.visit_If` rewrites mixed compile-time/runtime
conditions in other libraries' kernels too. With QuACK 0.6.2 and CuTe
DSL 4.8.0, this exposes `UNOBSERVED_WRITE_POSITION_UNKNOWN` when the MLA
reducer reuses `stats_split_idx` in its normalized-weight phase after
intervening control-flow boundaries.

This PR is a compatibility workaround for that QuACK/CuTe interaction,
tracked in
[Dao-AILab/quack#217](https://github.com/Dao-AILab/quack/issues/217). It
gives the normalized-weight phase of
`_run_parallel_gmem_reduction_g1_shared_stats` its own
`weight_split_idx` local, separate from the LSE-load phase's
`stats_split_idx`. Arithmetic, addresses, loop bounds, and
synchronization are unchanged.

The original local name is valid without QuACK's AST rewrite. Standalone
probes without the patch pass before and after the rename. Restoring
only CuTe's original `visit_If` also makes the unmodified reducer and
the TRT-LLM integration test pass, confirming the import-dependent
compiler interaction. Scoping QuACK's rewrite remains the underlying
upstream fix; this change keeps PrimTS compatible with affected
environments.

This is a follow-up to the compatibility backport in
NVIDIA/TensorRT-LLM#21354. The current TRT-LLM vendor pin and patch are
unchanged by this follow-up.

## 🔍 Related Issues

- https://github.com/Dao-AILab/quack/issues/217 — underlying
process-wide AST patch issue
- #8103
- https://github.com/NVIDIA/TensorRT-LLM/pull/21354

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

- [ ] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/attention/test_attention_ts_mla_decode.py`

The full GitHub Actions [H100 run
#42548670290](https://github.com/flashinfer-ai/flashinfer/actions/runs/42548670290/job/128939297203)
reported 127 failing CPU-test cases in `test_cudnn_prepared_contract.py`
and `test_cake_kcp_partition_parity.py`. These are unrelated baseline
fixture/API-discovery issues, outside the MLA reducer change. Their
fixes are not included in this PR.

Local validation on NVIDIA B300/SM103, PyTorch
2.14.0a0+b2c75dd062.nv26.09 / CUDA 13.4, and CuTe DSL 4.8.0:

- Existing `test_mla_runtime_count_changes[8-1-9216-dtype0]` passed,
including varying split counts and graph replay.
- A local no-LSE probe (BF16, batch 2, 32 heads, one query, KV capacity
1024) passed against the existing independent MLA reference.
- Both probes also pass on the unmodified standalone base
`f5ab85cc77edbd0257b0145eefe0113074dc6ee2`. No redundant GPU test or
test-matrix expansion is added to CI.
- AST comparison confirms that only the index identifier changes; the
reducer operations are unchanged. Scoped pre-commit passes.
- The original TRT-LLM
`test_prims_ts_mla_live_wrapper_cuda_graph_replay[regular-kv]` failed
with the compiler diagnostic before its backport and passed after it.
- A standalone reducer reproduction with a direct QuACK 0.6.2 import
also fails with the original variable names. Restoring only CuTe's
original `DSLPreprocessor.visit_If` makes both that reducer and the full
TRT-LLM integration test pass without renaming the variable. These
comparisons used separate fresh compiler caches.
- The diagnostic reproductions are local only; no additional GPU tests
are added to CI. Full upstream CI has not been run.

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

Please review this as a narrow compatibility workaround for QuACK's
process-wide AST rewrite. The underlying rewrite-scoping issue is
tracked in Dao-AILab/quack#217. The reducer schedule and numerical
implementation are unchanged.



<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Refactor**
* Clarified parallel-reduction bookkeeping. Calculations and results
remain unchanged.
* **Tests**
* Strengthened checks for prepared-state cleanup and function selection,
helping ensure these behaviors remain consistent. No user-facing
behavior changes are included.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: Yuxian Qiu <142763828+yuxianq@users.noreply.github.com>

### [5af9cfe](https://github.com/flashinfer-ai/flashinfer/commit/5af9cfe0252c80c34326eec9065fc761b00703f7)

- **作者**: eigen
- **时间**: 2026-11-10T05:39:08Z
- **提交信息**: perf(cake_deepgemm): route eight SM120 RTX 5090 paged MQA decode steps to faster programs (#9313)

The SM120 paged FP8 MQA logits kernel picks its program from a route
catalog. Each heads/page/next_n configuration has a default route, and
device routes pick a tuned program for individual shapes. This PR moves
eight RTX 5090 decode shapes to faster programs: heads 32 and 64, page
64 and 128, next_n 3, 5 and 6, at batch 256 with context 4096 or batch
64 with context 16384. Each shape now runs a program that the catalog
already ships, so the PR changes only the catalog and adds no new
program or kernel code. On these shapes the speedup over the previous
version of this kernel ranges from 1.029× to 1.220×, with a geomean of
1.076× (seed 760) and 1.079× (seed 52021). RTX PRO 6000 routes do not
change, and every other shape keeps its current route.

The kernel's other Cake variants are the dense FP4 and FP8
lightning-indexer logits and the paged FP8 MQA logits for SM100a/SM103a
(`deepgemm_dense_mqa`), and this paged FP8 package ships on sm_120a
only.

NVIDIA GeForce RTX 5090 (170 SMs, sm_120a), driver 620.62, CUDA 13.4.92
toolchain (CUDA 13.0 runtime, PyTorch 2.14.1+cu130). Baseline: the
previous Cake version of this kernel on main (36718d11). Latency: median
µs of the paged FP8 MQA logits call (CUPTI, L2 flushed before each
launch, 5 interleaved baseline/new groups). Each seed (760, 52021) runs
on its own GPU. Speedup = baseline µs / new µs. The table covers all 216
shapes. The 8 changed shapes have a geomean speedup of 1.076× (seed 760)
and 1.079× (seed 52021). On unchanged shapes both sides run the same
program.

| heads | page | next_n | batch | context | state | baseline µs (760) |
new µs (760) | speedup (760) | baseline µs (52021) | new µs (52021) |
speedup (52021) |
|---:|---:|---:|---:|---:|:--|---:|---:|---:|---:|---:|---:|
| 32 | 64 | 1 | 8 | 4096 | unchanged | 7.17 | 7.17 | 1.000× | 7.30 |
7.30 | 1.000× |
| 32 | 64 | 1 | 64 | 4096 | unchanged | 29.34 | 29.31 | 1.001× | 29.44 |
29.38 | 1.002× |
| 32 | 64 | 1 | 256 | 4096 | unchanged | 100.54 | 100.51 | 1.000× |
100.54 | 100.54 | 1.000× |
| 32 | 64 | 1 | 1 | 16384 | unchanged | 6.17 | 6.14 | 1.005× | 6.27 |
6.24 | 1.005× |
| 32 | 64 | 1 | 8 | 16384 | unchanged | 16.61 | 16.61 | 1.000× | 16.61 |
16.61 | 1.000× |
| 32 | 64 | 1 | 32 | 16384 | unchanged | 52.38 | 52.35 | 1.001× | 52.35
| 52.35 | 1.000× |
| 32 | 64 | 1 | 64 | 16384 | unchanged | 100.93 | 100.96 | 1.000× |
100.51 | 100.48 | 1.000× |
| 32 | 64 | 1 | 128 | 16384 | unchanged | 193.12 | 193.21 | 1.000× |
192.48 | 192.61 | 0.999× |
| 32 | 64 | 1 | 256 | 16384 | unchanged | 374.20 | 374.23 | 1.000× |
374.11 | 374.20 | 1.000× |
| 32 | 64 | 1 | 8 | 65536 | unchanged | 55.74 | 55.74 | 1.000× | 55.84 |
55.90 | 0.999× |
| 32 | 64 | 1 | 32 | 65536 | unchanged | 188.99 | 189.02 | 1.000× |
188.80 | 188.83 | 1.000× |
| 32 | 64 | 1 | 128 | 65536 | unchanged | 724.12 | 724.47 | 1.000× |
721.21 | 721.21 | 1.000× |
| 32 | 64 | 2 | 8 | 4096 | unchanged | 7.49 | 7.49 | 1.000× | 7.62 |
7.58 | 1.004× |
| 32 | 64 | 2 | 64 | 4096 | unchanged | 30.24 | 30.21 | 1.001× | 30.30 |
30.27 | 1.001× |
| 32 | 64 | 2 | 256 | 4096 | unchanged | 104.86 | 104.86 | 1.000× |
104.51 | 104.54 | 1.000× |
| 32 | 64 | 2 | 1 | 16384 | unchanged | 6.40 | 6.40 | 1.000× | 6.50 |
6.50 | 1.000× |
| 32 | 64 | 2 | 8 | 16384 | unchanged | 17.38 | 17.41 | 0.998× | 17.41 |
17.41 | 1.000× |
| 32 | 64 | 2 | 32 | 16384 | unchanged | 53.85 | 53.85 | 1.000× | 53.70
| 53.76 | 0.999× |
| 32 | 64 | 2 | 64 | 16384 | unchanged | 104.48 | 104.51 | 1.000× |
104.25 | 104.32 | 0.999× |
| 32 | 64 | 2 | 128 | 16384 | unchanged | 203.45 | 203.55 | 1.000× |
203.29 | 203.52 | 0.999× |
| 32 | 64 | 2 | 256 | 16384 | unchanged | 393.63 | 393.85 | 0.999× |
393.50 | 393.53 | 1.000× |
| 32 | 64 | 2 | 8 | 65536 | unchanged | 57.15 | 57.15 | 1.000× | 57.28 |
57.28 | 1.000× |
| 32 | 64 | 2 | 32 | 65536 | unchanged | 198.62 | 198.62 | 1.000× |
198.30 | 198.17 | 1.001× |
| 32 | 64 | 2 | 128 | 65536 | unchanged | 763.00 | 762.61 | 1.001× |
759.64 | 759.85 | 1.000× |
| 32 | 64 | 3 | 8 | 4096 | unchanged | 8.58 | 8.61 | 0.996× | 8.64 |
8.64 | 1.000× |
| 32 | 64 | 3 | 64 | 4096 | unchanged | 31.78 | 31.78 | 1.000× | 31.84 |
31.78 | 1.002× |
| 32 | 64 | 3 | 256 | 4096 | unchanged | 112.03 | 112.03 | 1.000× |
111.49 | 111.42 | 1.001× |
| 32 | 64 | 3 | 1 | 16384 | unchanged | 6.43 | 6.46 | 0.995× | 6.66 |
6.69 | 0.995× |
| 32 | 64 | 3 | 8 | 16384 | unchanged | 17.95 | 17.98 | 0.998× | 18.11 |
18.05 | 1.004× |
| 32 | 64 | 3 | 32 | 16384 | unchanged | 56.45 | 56.45 | 1.000× | 56.41
| 56.45 | 0.999× |
| 32 | 64 | 3 | 64 | 16384 | unchanged | 110.75 | 110.75 | 1.000× |
110.75 | 110.85 | 0.999× |
| 32 | 64 | 3 | 128 | 16384 | unchanged | 215.36 | 215.23 | 1.001× |
214.84 | 214.91 | 1.000× |
| 32 | 64 | 3 | 256 | 16384 | unchanged | 418.68 | 418.76 | 1.000× |
417.55 | 417.24 | 1.001× |
| 32 | 64 | 3 | 8 | 65536 | unchanged | 59.71 | 59.71 | 1.000× | 59.74 |
59.77 | 0.999× |
| 32 | 64 | 3 | 32 | 65536 | unchanged | 209.15 | 209.21 | 1.000× |
209.15 | 209.15 | 1.000× |
| 32 | 64 | 3 | 128 | 65536 | unchanged | 808.31 | 808.66 | 1.000× |
812.56 | 812.65 | 1.000× |
| 32 | 64 | 4 | 8 | 4096 | unchanged | 7.65 | 7.68 | 0.996× | 7.81 |
7.78 | 1.004× |
| 32 | 64 | 4 | 64 | 4096 | unchanged | 33.44 | 33.47 | 0.999× | 33.34 |
33.28 | 1.002× |
| 32 | 64 | 4 | 256 | 4096 | unchanged | 119.20 | 119.10 | 1.001× |
119.36 | 119.36 | 1.000× |
| 32 | 64 | 4 | 1 | 16384 | unchanged | 6.62 | 6.62 | 1.000× | 6.88 |
6.85 | 1.005× |
| 32 | 64 | 4 | 8 | 16384 | unchanged | 18.50 | 18.50 | 1.000× | 18.98 |
18.88 | 1.005× |
| 32 | 64 | 4 | 32 | 16384 | unchanged | 59.55 | 59.55 | 1.000× | 59.42
| 59.49 | 0.999× |
| 32 | 64 | 4 | 64 | 16384 | unchanged | 117.66 | 117.73 | 0.999× |
117.44 | 117.50 | 0.999× |
| 32 | 64 | 4 | 128 | 16384 | unchanged | 226.40 | 226.40 | 1.000× |
226.21 | 226.20 | 1.000× |
| 32 | 64 | 4 | 256 | 16384 | unchanged | 440.89 | 440.57 | 1.001× |
440.60 | 440.70 | 1.000× |
| 32 | 64 | 4 | 8 | 65536 | unchanged | 62.37 | 62.37 | 1.000× | 62.94 |
62.91 | 1.000× |
| 32 | 64 | 4 | 32 | 65536 | unchanged | 221.02 | 221.02 | 1.000× |
219.71 | 219.74 | 1.000× |
| 32 | 64 | 4 | 128 | 65536 | unchanged | 851.08 | 851.99 | 0.999× |
846.29 | 846.15 | 1.000× |
| 32 | 64 | 5 | 8 | 4096 | unchanged | 8.86 | 8.86 | 1.000× | 8.86 |
8.86 | 1.000× |
| 32 | 64 | 5 | 64 | 4096 | unchanged | 35.23 | 35.23 | 1.000× | 36.13 |
36.10 | 1.001× |
| 32 | 64 | 5 | 256 | 4096 | changed | 131.71 | 124.86 | 1.055× | 132.57
| 124.96 | 1.061× |
| 32 | 64 | 5 | 1 | 16384 | unchanged | 7.23 | 7.23 | 1.000× | 7.42 |
7.42 | 1.000× |
| 32 | 64 | 5 | 8 | 16384 | unchanged | 20.06 | 20.06 | 1.000× | 20.19 |
20.10 | 1.005× |
| 32 | 64 | 5 | 32 | 16384 | unchanged | 65.28 | 65.25 | 1.000× | 64.96
| 64.89 | 1.001× |
| 32 | 64 | 5 | 64 | 16384 | changed | 131.07 | 124.03 | 1.057× | 131.20
| 124.19 | 1.056× |
| 32 | 64 | 5 | 128 | 16384 | unchanged | 245.41 | 245.60 | 0.999× |
245.66 | 245.72 | 1.000× |
| 32 | 64 | 5 | 256 | 16384 | unchanged, CE (760, 52021) | 457.34 |
456.86 | 1.001×² | 455.29 | 456.00 | 0.998×² |
| 32 | 64 | 5 | 8 | 65536 | unchanged | 67.29 | 67.26 | 1.000× | 68.93 |
68.89 | 1.000× |
| 32 | 64 | 5 | 32 | 65536 | unchanged | 234.17 | 234.27 | 1.000× |
234.27 | 234.05 | 1.001× |
| 32 | 64 | 5 | 128 | 65536 | unchanged, CE (760, 52021) | 903.72 |
904.60 | 0.999×² | 908.21 | 909.05 | 0.999×² |
| 32 | 64 | 6 | 8 | 4096 | unchanged | 8.77 | 8.77 | 1.000× | 8.80 |
8.80 | 1.000× |
| 32 | 64 | 6 | 64 | 4096 | unchanged | 38.94 | 38.91 | 1.001× | 39.26 |
39.17 | 1.002× |
| 32 | 64 | 6 | 256 | 4096 | unchanged | 149.34 | 149.41 | 1.000× |
149.76 | 149.73 | 1.000× |
| 32 | 64 | 6 | 1 | 16384 | unchanged | 7.07 | 7.07 | 1.000× | 7.30 |
7.30 | 1.000× |
| 32 | 64 | 6 | 8 | 16384 | unchanged | 22.59 | 22.59 | 1.000× | 22.24 |
22.21 | 1.001× |
| 32 | 64 | 6 | 32 | 16384 | unchanged | 72.80 | 72.80 | 1.000× | 73.76
| 73.66 | 1.001× |
| 32 | 64 | 6 | 64 | 16384 | unchanged | 146.53 | 146.46 | 1.000× |
147.17 | 147.26 | 0.999× |
| 32 | 64 | 6 | 128 | 16384 | unchanged | 271.32 | 271.26 | 1.000× |
272.54 | 272.64 | 1.000× |
| 32 | 64 | 6 | 256 | 16384 | unchanged | 529.88 | 530.71 | 0.998× |
529.13 | 530.35 | 0.998× |
| 32 | 64 | 6 | 8 | 65536 | unchanged | 74.53 | 74.53 | 1.000× | 75.71 |
75.74 | 1.000× |
| 32 | 64 | 6 | 32 | 65536 | unchanged | 263.13 | 263.04 | 1.000× |
264.32 | 264.38 | 1.000× |
| 32 | 64 | 6 | 128 | 65536 | unchanged, CE (760, 52021) | 1058.68 |
1057.37 | 1.001×² | 1067.24 | 1064.15 | 1.003×² |
| 32 | 128 | 1 | 8 | 4096 | unchanged | 7.17 | 7.17 | 1.000× | 7.36 |
7.39 | 0.996× |
| 32 | 128 | 1 | 64 | 4096 | unchanged | 29.63 | 29.63 | 1.000× | 29.70
| 29.73 | 0.999× |
| 32 | 128 | 1 | 256 | 4096 | unchanged | 100.45 | 100.45 | 1.000× |
100.48 | 100.45 | 1.000× |
| 32 | 128 | 1 | 1 | 16384 | unchanged | 6.14 | 6.14 | 1.000× | 6.30 |
6.27 | 1.005× |
| 32 | 128 | 1 | 8 | 16384 | unchanged | 16.83 | 16.83 | 1.000× | 16.86
| 16.86 | 1.000× |
| 32 | 128 | 1 | 32 | 16384 | unchanged | 52.26 | 52.26 | 1.000× | 52.22
| 52.32 | 0.998× |
| 32 | 128 | 1 | 64 | 16384 | unchanged | 100.41 | 100.41 | 1.000× |
100.48 | 100.45 | 1.000× |
| 32 | 128 | 1 | 128 | 16384 | unchanged | 193.15 | 193.34 | 0.999× |
193.41 | 193.34 | 1.000× |
| 32 | 128 | 1 | 256 | 16384 | unchanged | 373.72 | 373.69 | 1.000× |
373.44 | 373.31 | 1.000× |
| 32 | 128 | 1 | 8 | 65536 | unchanged | 55.71 | 55.71 | 1.000× | 55.71
| 55.68 | 1.001× |
| 32 | 128 | 1 | 32 | 65536 | unchanged | 188.83 | 188.83 | 1.000× |
188.44 | 188.48 | 1.000× |
| 32 | 128 | 1 | 128 | 65536 | unchanged | 723.13 | 723.10 | 1.000× |
721.61 | 721.54 | 1.000× |
| 32 | 128 | 2 | 8 | 4096 | unchanged | 7.52 | 7.52 | 1.000× | 7.65 |
7.62 | 1.004× |
| 32 | 128 | 2 | 64 | 4096 | unchanged | 30.46 | 30.46 | 1.000× | 30.40
| 30.46 | 0.998× |
| 32 | 128 | 2 | 256 | 4096 | unchanged | 105.53 | 105.57 | 1.000× |
105.57 | 105.57 | 1.000× |
| 32 | 128 | 2 | 1 | 16384 | unchanged | 6.43 | 6.43 | 1.000× | 6.56 |
6.59 | 0.995× |
| 32 | 128 | 2 | 8 | 16384 | unchanged | 17.12 | 17.15 | 0.998× | 17.09
| 17.15 | 0.996× |
| 32 | 128 | 2 | 32 | 16384 | unchanged | 53.92 | 53.92 | 1.000× | 53.85
| 53.92 | 0.999× |
| 32 | 128 | 2 | 64 | 16384 | unchanged | 104.70 | 104.73 | 1.000× |
104.99 | 104.93 | 1.001× |
| 32 | 128 | 2 | 128 | 16384 | unchanged | 204.28 | 204.13 | 1.001× |
203.71 | 203.84 | 0.999× |
| 32 | 128 | 2 | 256 | 16384 | unchanged | 394.46 | 394.48 | 1.000× |
393.13 | 393.05 | 1.000× |
| 32 | 128 | 2 | 8 | 65536 | unchanged | 57.09 | 57.09 | 1.000× | 57.22
| 57.25 | 0.999× |
| 32 | 128 | 2 | 32 | 65536 | unchanged | 199.10 | 199.04 | 1.000× |
198.53 | 198.33 | 1.001× |
| 32 | 128 | 2 | 128 | 65536 | unchanged | 765.72 | 766.01 | 1.000× |
761.43 | 760.98 | 1.001× |
| 32 | 128 | 3 | 8 | 4096 | unchanged | 8.70 | 8.70 | 1.000× | 8.77 |
8.74 | 1.004× |
| 32 | 128 | 3 | 64 | 4096 | unchanged | 31.97 | 31.97 | 1.000× | 32.19
| 32.22 | 0.999× |
| 32 | 128 | 3 | 256 | 4096 | unchanged | 111.58 | 111.58 | 1.000× |
112.19 | 112.19 | 1.000× |
| 32 | 128 | 3 | 1 | 16384 | unchanged | 6.72 | 6.72 | 1.000× | 6.88 |
6.88 | 1.000× |
| 32 | 128 | 3 | 8 | 16384 | unchanged | 18.05 | 18.05 | 1.000× | 18.34
| 18.43 | 0.995× |
| 32 | 128 | 3 | 32 | 16384 | unchanged | 56.70 | 56.70 | 1.000× | 56.67
| 56.73 | 0.999× |
| 32 | 128 | 3 | 64 | 16384 | unchanged | 111.45 | 111.42 | 1.000× |
110.85 | 110.88 | 1.000× |
| 32 | 128 | 3 | 128 | 16384 | unchanged | 214.85 | 214.94 | 1.000× |
214.81 | 215.07 | 0.999× |
| 32 | 128 | 3 | 256 | 16384 | unchanged | 417.28 | 417.34 | 1.000× |
418.68 | 418.94 | 0.999× |
| 32 | 128 | 3 | 8 | 65536 | unchanged | 60.19 | 60.22 | 0.999× | 60.16
| 60.22 | 0.999× |
| 32 | 128 | 3 | 32 | 65536 | unchanged | 211.00 | 210.94 | 1.000× |
210.05 | 209.98 | 1.000× |
| 32 | 128 | 3 | 128 | 65536 | unchanged | 810.07 | 809.62 | 1.001× |
816.49 | 816.41 | 1.000× |
| 32 | 128 | 4 | 8 | 4096 | unchanged | 8.99 | 8.96 | 1.004× | 9.09 |
9.09 | 1.000× |
| 32 | 128 | 4 | 64 | 4096 | unchanged | 33.22 | 33.22 | 1.000× | 33.41
| 33.34 | 1.002× |
| 32 | 128 | 4 | 256 | 4096 | unchanged | 118.62 | 118.62 | 1.000× |
119.55 | 119.61 | 0.999× |
| 32 | 128 | 4 | 1 | 16384 | unchanged | 7.55 | 7.52 | 1.004× | 7.78 |
7.74 | 1.004× |
| 32 | 128 | 4 | 8 | 16384 | unchanged | 18.81 | 18.82 | 1.000× | 18.69
| 18.62 | 1.003× |
| 32 | 128 | 4 | 32 | 16384 | unchanged | 59.07 | 59.04 | 1.001× | 59.20
| 59.10 | 1.002× |
| 32 | 128 | 4 | 64 | 16384 | unchanged | 117.41 | 117.44 | 1.000× |
118.75 | 118.75 | 1.000× |
| 32 | 128 | 4 | 128 | 16384 | unchanged | 226.65 | 226.64 | 1.000× |
226.33 | 226.30 | 1.000× |
| 32 | 128 | 4 | 256 | 16384 | unchanged | 441.18 | 441.31 | 1.000× |
441.11 | 441.66 | 0.999× |
| 32 | 128 | 4 | 8 | 65536 | unchanged | 62.43 | 62.43 | 1.000× | 62.18
| 62.27 | 0.998× |
| 32 | 128 | 4 | 32 | 65536 | unchanged | 220.03 | 220.29 | 0.999× |
219.65 | 219.74 | 1.000× |
| 32 | 128 | 4 | 128 | 65536 | unchanged | 856.18 | 855.77 | 1.000× |
859.69 | 859.88 | 1.000× |
| 32 | 128 | 5 | 8 | 4096 | unchanged | 8.93 | 8.93 | 1.000× | 8.93 |
8.90 | 1.004× |
| 32 | 128 | 5 | 64 | 4096 | unchanged | 35.42 | 35.42 | 1.000× | 36.03
| 36.00 | 1.001× |
| 32 | 128 | 5 | 256 | 4096 | changed | 132.51 | 125.28 | 1.058× |
132.77 | 124.73 | 1.064× |
| 32 | 128 | 5 | 1 | 16384 | unchanged | 7.30 | 7.30 | 1.000× | 7.39 |
7.42 | 0.996× |
| 32 | 128 | 5 | 8 | 16384 | unchanged | 19.74 | 19.71 | 1.002× | 19.87
| 19.78 | 1.005× |
| 32 | 128 | 5 | 32 | 16384 | unchanged | 64.99 | 65.02 | 1.000× | 65.25
| 65.21 | 1.001× |
| 32 | 128 | 5 | 64 | 16384 | changed | 131.36 | 124.70 | 1.053× |
130.85 | 123.29 | 1.061× |
| 32 | 128 | 5 | 128 | 16384 | unchanged | 241.37 | 241.41 | 1.000× |
242.17 | 242.30 | 0.999× |
| 32 | 128 | 5 | 256 | 16384 | unchanged, CE (760, 52021) | 456.38 |
456.99 | 0.999×² | 455.55 | 456.60 | 0.998×² |
| 32 | 128 | 5 | 8 | 65536 | unchanged | 67.74 | 67.78 | 1.000× | 68.03
| 68.00 | 1.000× |
| 32 | 128 | 5 | 32 | 65536 | unchanged | 234.46 | 234.46 | 1.000× |
235.13 | 235.10 | 1.000× |
| 32 | 128 | 5 | 128 | 65536 | unchanged, CE (760, 52021) | 903.30 |
902.69 | 1.001×² | 905.22 | 909.15 | 0.996×² |
| 32 | 128 | 6 | 8 | 4096 | unchanged | 8.83 | 8.83 | 1.000× | 8.80 |
8.80 | 1.000× |
| 32 | 128 | 6 | 64 | 4096 | unchanged | 39.29 | 39.26 | 1.001× | 38.34
| 38.34 | 1.000× |
| 32 | 128 | 6 | 256 | 4096 | changed | 148.16 | 133.50 | 1.110× |
148.41 | 133.44 | 1.112× |
| 32 | 128 | 6 | 1 | 16384 | unchanged | 7.23 | 7.23 | 1.000× | 7.39 |
7.42 | 0.996× |
| 32 | 128 | 6 | 8 | 16384 | unchanged | 21.95 | 21.95 | 1.000× | 22.34
| 22.40 | 0.997× |
| 32 | 128 | 6 | 32 | 16384 | unchanged | 72.58 | 72.58 | 1.000× | 73.31
| 73.31 | 1.000× |
| 32 | 128 | 6 | 64 | 16384 | unchanged | 146.30 | 146.27 | 1.000× |
147.62 | 147.65 | 1.000× |
| 32 | 128 | 6 | 128 | 16384 | unchanged | 271.77 | 271.74 | 1.000× |
272.67 | 272.35 | 1.001× |
| 32 | 128 | 6 | 256 | 16384 | unchanged | 529.90 | 530.78 | 0.998× |
527.45 | 528.99 | 0.997× |
| 32 | 128 | 6 | 8 | 65536 | unchanged | 74.82 | 74.85 | 1.000× | 75.84
| 75.90 | 0.999× |
| 32 | 128 | 6 | 32 | 65536 | unchanged | 263.49 | 263.58 | 1.000× |
264.00 | 264.03 | 1.000× |
| 32 | 128 | 6 | 128 | 65536 | unchanged, CE (760, 52021) | 1075.70 |
1076.47 | 0.999×² | 1084.87 | 1084.05 | 1.001×² |
| 64 | 64 | 1 | 8 | 4096 | unchanged | 7.49 | 7.49 | 1.000× | 7.55 |
7.55 | 1.000× |
| 64 | 64 | 1 | 64 | 4096 | unchanged | 30.02 | 30.02 | 1.000× | 30.08 |
30.02 | 1.002× |
| 64 | 64 | 1 | 256 | 4096 | unchanged | 101.98 | 102.02 | 1.000× |
101.76 | 101.79 | 1.000× |
| 64 | 64 | 1 | 1 | 16384 | unchanged | 6.34 | 6.34 | 1.000× | 6.46 |
6.46 | 1.000× |
| 64 | 64 | 1 | 8 | 16384 | unchanged | 17.09 | 17.09 | 1.000× | 16.99 |
16.99 | 1.000× |
| 64 | 64 | 1 | 32 | 16384 | unchanged | 52.80 | 52.80 | 1.000× | 52.80
| 52.73 | 1.001× |
| 64 | 64 | 1 | 64 | 16384 | unchanged | 101.44 | 101.47 | 1.000× |
101.28 | 101.31 | 1.000× |
| 64 | 64 | 1 | 128 | 16384 | unchanged | 194.81 | 194.94 | 0.999× |
194.17 | 194.08 | 1.000× |
| 64 | 64 | 1 | 256 | 16384 | unchanged | 376.03 | 376.03 | 1.000× |
375.34 | 375.49 | 1.000× |
| 64 | 64 | 1 | 8 | 65536 | unchanged | 56.22 | 56.22 | 1.000× | 56.13 |
56.16 | 0.999× |
| 64 | 64 | 1 | 32 | 65536 | unchanged | 189.76 | 189.82 | 1.000× |
189.41 | 189.37 | 1.000× |
| 64 | 64 | 1 | 128 | 65536 | unchanged | 725.91 | 726.01 | 1.000× |
727.34 | 727.13 | 1.000× |
| 64 | 64 | 2 | 8 | 4096 | unchanged | 8.26 | 8.22 | 1.004× | 8.35 |
8.38 | 0.996× |
| 64 | 64 | 2 | 64 | 4096 | unchanged | 32.09 | 32.10 | 1.000× | 32.16 |
32.06 | 1.003× |
| 64 | 64 | 2 | 256 | 4096 | unchanged | 109.12 | 109.15 | 1.000× |
110.05 | 110.02 | 1.000× |
| 64 | 64 | 2 | 1 | 16384 | unchanged | 6.78 | 6.78 | 1.000× | 6.85 |
6.85 | 1.000× |
| 64 | 64 | 2 | 8 | 16384 | unchanged | 18.14 | 18.14 | 1.000× | 18.37 |
18.21 | 1.009× |
| 64 | 64 | 2 | 32 | 16384 | unchanged | 55.71 | 55.74 | 0.999× | 55.61
| 55.68 | 0.999× |
| 64 | 64 | 2 | 64 | 16384 | unchanged | 108.16 | 108.16 | 1.000× |
108.29 | 108.32 | 1.000× |
| 64 | 64 | 2 | 128 | 16384 | unchanged | 209.41 | 209.41 | 1.000× |
209.09 | 209.15 | 1.000× |
| 64 | 64 | 2 | 256 | 16384 | unchanged | 405.31 | 404.89 | 1.001× |
406.49 | 406.36 | 1.000× |
| 64 | 64 | 2 | 8 | 65536 | unchanged | 58.91 | 58.94 | 0.999× | 59.07 |
59.07 | 1.000× |
| 64 | 64 | 2 | 32 | 65536 | unchanged | 203.90 | 203.77 | 1.001× |
203.17 | 203.04 | 1.001× |
| 64 | 64 | 2 | 128 | 65536 | unchanged | 789.05 | 789.43 | 1.000× |
784.98 | 783.99 | 1.001× |
| 64 | 64 | 3 | 8 | 4096 | unchanged | 11.94 | 11.94 | 1.000× | 11.81 |
11.81 | 1.000× |
| 64 | 64 | 3 | 64 | 4096 | unchanged | 35.74 | 35.77 | 0.999× | 36.06 |
36.16 | 0.997× |
| 64 | 64 | 3 | 256 | 4096 | changed | 146.11 | 119.81 | 1.220× | 146.30
| 120.00 | 1.219× |
| 64 | 64 | 3 | 1 | 16384 | unchanged | 7.52 | 7.52 | 1.000× | 7.58 |
7.55 | 1.004× |
| 64 | 64 | 3 | 8 | 16384 | unchanged | 21.02 | 21.02 | 1.000× | 20.64 |
20.70 | 0.997× |
| 64 | 64 | 3 | 32 | 16384 | unchanged | 65.98 | 65.98 | 1.000× | 66.24
| 66.18 | 1.001× |
| 64 | 64 | 3 | 64 | 16384 | unchanged | 143.42 | 143.49 | 1.000× |
144.03 | 144.22 | 0.999× |
| 64 | 64 | 3 | 128 | 16384 | unchanged | 267.48 | 267.42 | 1.000× |
268.28 | 268.44 | 0.999× |
| 64 | 64 | 3 | 256 | 16384 | unchanged | 523.00 | 521.75 | 1.002× |
520.54 | 518.91 | 1.003× |
| 64 | 64 | 3 | 8 | 65536 | unchanged | 67.78 | 67.78 | 1.000× | 69.63 |
69.60 | 1.000× |
| 64 | 64 | 3 | 32 | 65536 | unchanged | 259.10 | 259.00 | 1.000× |
260.38 | 260.44 | 1.000× |
| 64 | 64 | 3 | 128 | 65536 | unchanged, CE (760, 52021); clock-matched:
T (760) / T (52021) | 866.97 | 867.25 | 1.000×² | 843.53 | 844.09 |
0.999×² |
| 64 | 64 | 4 | 8 | 4096 | unchanged | 9.12 | 9.12 | 1.000× | 9.22 |
9.22 | 1.000× |
| 64 | 64 | 4 | 64 | 4096 | unchanged | 39.71 | 39.68 | 1.001× | 39.81 |
39.71 | 1.002× |
| 64 | 64 | 4 | 256 | 4096 | unchanged | 182.14 | 182.17 | 1.000× |
183.36 | 183.45 | 0.999× |
| 64 | 64 | 4 | 1 | 16384 | unchanged | 7.52 | 7.52 | 1.000× | 7.62 |
7.65 | 0.996× |
| 64 | 64 | 4 | 8 | 16384 | unchanged | 23.04 | 23.04 | 1.000× | 22.91 |
22.91 | 1.000× |
| 64 | 64 | 4 | 32 | 16384 | unchanged | 79.33 | 79.36 | 1.000× | 80.70
| 80.67 | 1.000× |
| 64 | 64 | 4 | 64 | 16384 | unchanged | 179.87 | 179.81 | 1.000× |
180.22 | 180.57 | 0.998× |
| 64 | 64 | 4 | 128 | 16384 | unchanged | 340.67 | 340.64 | 1.000× |
341.47 | 341.21 | 1.001× |
| 64 | 64 | 4 | 256 | 16384 | unchanged | 677.13 | 677.69 | 0.999× |
673.72 | 671.42 | 1.003× |
| 64 | 64 | 4 | 8 | 65536 | unchanged | 84.64 | 84.67 | 1.000× | 86.43 |
86.46 | 1.000× |
| 64 | 64 | 4 | 32 | 65536 | unchanged | 330.14 | 330.09 | 1.000× |
331.11 | 331.13 | 1.000× |
| 64 | 64 | 4 | 128 | 65536 | unchanged | 1346.69 | 1346.40 | 1.000× |
1343.82 | 1342.88 | 1.001× |
| 64 | 64 | 5 | 8 | 4096 | unchanged | 11.04 | 11.04 | 1.000× | 11.04 |
11.04 | 1.000× |
| 64 | 64 | 5 | 64 | 4096 | unchanged | 50.91 | 50.91 | 1.000× | 51.30 |
51.23 | 1.001× |
| 64 | 64 | 5 | 256 | 4096 | changed | 230.56 | 222.65 | 1.035× | 231.00
| 223.13 | 1.035× |
| 64 | 64 | 5 | 1 | 16384 | unchanged | 8.54 | 8.54 | 1.000× | 8.61 |
8.64 | 0.996× |
| 64 | 64 | 5 | 8 | 16384 | unchanged | 28.29 | 28.29 | 1.000× | 28.32 |
28.41 | 0.997× |
| 64 | 64 | 5 | 32 | 16384 | unchanged | 92.35 | 92.38 | 1.000× | 95.07
| 94.85 | 1.002× |
| 64 | 64 | 5 | 64 | 16384 | unchanged | 216.61 | 216.35 | 1.001× |
216.35 | 216.96 | 0.997× |
| 64 | 64 | 5 | 128 | 16384 | unchanged | 424.70 | 425.12 | 0.999× |
427.29 | 426.85 | 1.001× |
| 64 | 64 | 5 | 256 | 16384 | unchanged | 858.45 | 858.60 | 1.000× |
851.35 | 852.34 | 0.999× |
| 64 | 64 | 5 | 8 | 65536 | unchanged | 94.43 | 94.43 | 1.000× | 96.25 |
96.13 | 1.001× |
| 64 | 64 | 5 | 32 | 65536 | unchanged; clock-matched: T (760) / T
(52021) | 409.92 | 409.63 | 1.001× | 410.62 | 410.36 | 1.001× |
| 64 | 64 | 5 | 128 | 65536 | unchanged | 1690.73 | 1694.19 | 0.998× |
1686.57 | 1687.80 | 0.999× |
| 64 | 64 | 6 | 8 | 4096 | unchanged | 11.07 | 11.07 | 1.000× | 11.07 |
11.07 | 1.000× |
| 64 | 64 | 6 | 64 | 4096 | unchanged | 55.20 | 55.20 | 1.000× | 55.52 |
55.52 | 1.000× |
| 64 | 64 | 6 | 256 | 4096 | changed | 269.82 | 262.24 | 1.029× | 269.69
| 261.44 | 1.032× |
| 64 | 64 | 6 | 1 | 16384 | unchanged | 8.45 | 8.45 | 1.000× | 8.58 |
8.58 | 1.000× |
| 64 | 64 | 6 | 8 | 16384 | unchanged | 27.97 | 27.94 | 1.001× | 27.94 |
27.94 | 1.000× |
| 64 | 64 | 6 | 32 | 16384 | unchanged | 102.50 | 102.46 | 1.000× |
105.57 | 105.38 | 1.002× |
| 64 | 64 | 6 | 64 | 16384 | unchanged | 260.19 | 260.25 | 1.000× |
260.28 | 260.44 | 0.999× |
| 64 | 64 | 6 | 128 | 16384 | unchanged | 503.58 | 502.68 | 1.002× |
500.91 | 501.55 | 0.999× |
| 64 | 64 | 6 | 256 | 16384 | unchanged | 1023.24 | 1023.97 | 0.999× |
1016.28 | 1015.91 | 1.000× |
| 64 | 64 | 6 | 8 | 65536 | unchanged | 118.62 | 118.85 | 0.998× |
119.39 | 119.39 | 1.000× |
| 64 | 64 | 6 | 32 | 65536 | unchanged | 486.78 | 488.44 | 0.997× |
486.64 | 484.83 | 1.004× |
| 64 | 64 | 6 | 128 | 65536 | unchanged | 2017.56 | 2020.54 | 0.999× |
2017.15 | 2015.72 | 1.001× |

² Clock-gate miss: the SM clock gate (min ≥ 2500 MHz, spread ≤ 250 MHz)
failed after one re-time, and the numbers are shown as recorded. 14
row-seeds have this mark, all on unchanged shapes.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Improvements**
* Updated kernel selection for selected SM120 workloads. Some
configurations now have no mapped kernel at batch sizes 33 or 65, while
other batch-size mappings use parallel kernel variants.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery Huang <averyh@nvidia.com>

### [b8ef7f2](https://github.com/flashinfer-ai/flashinfer/commit/b8ef7f2312fd80d719ee2c62184cd936de0f0161)

- **作者**: Haobin Guo
- **时间**: 2026-11-10T04:44:19Z
- **提交信息**: perf(moe): reduce the host overhead of the SM90 CuTe DSL fused MoE (#9246)

<!-- .github/pull_request_template.md -->

## 📌 Description

On the eager (non-graphed) path, `cute_dsl_fused_moe_bf16` on SM90
spends about 200 us of host time per call. In tensor-parallel serving of
a mid-size MoE model, eager prefill is host-bound: each decoder layer
takes more host time than GPU time, so the MoE call's host time goes
straight into time to first token. For example, serving Qwen3-30B-A3B
with TP8 on 8x H100 in vLLM, the single-request TTFT for a 4096-token
prompt is about 15% higher than with the Triton MoE backend, even though
the CuTe DSL kernels are faster.

About 40% of that host time was per-call Python overhead rather than
work: argument marshalling and pointer objects for the two GEMM
launches, and building a runner on every call. This PR removes that
overhead without changing the kernels:

- **TVM-FFI kernel launches**
(`sm90_contiguous_gather_grouped_gemm_act_fusion.py`,
`sm90_contiguous_grouped_gemm_finalize_fusion.py`). Both GEMM kernels
are compiled with `options="--enable-tvm-ffi"`, and each call passes raw
device addresses, dimensions and the stream handle. The `make_ptr`
pointer objects are built only when a specialization is compiled, as
typed examples for `cute.compile`, not on every call. A launch with 13
arguments takes about 3 us of host time this way, against about 25 us
through the default `JitExecutor`. Wrapper signatures are unchanged.
- **Cached runner** (`sm90_fused_moe.py`). `cute_dsl_fused_moe_bf16`
keeps one `CuteDslFusedMoESm90Runner` per static MoE configuration
instead of building one, with its tuning config and activation
validation, on every call (about 8-10 us of host time). A rejected
configuration is not cached.

### Host time per call

`cute_dsl_fused_moe_bf16`, bf16, E=128, top_k=8, hidden=2048,
intermediate=96 (the TP8 expert shard of Qwen3-30B-A3B). Host time is
the wall time of 100 back-to-back eager calls with the GPU running
asynchronously; GPU time comes from CUDA events around the same loop.
Each process reports the median of 5 rounds; `main` and this PR ran as 3
alternating process pairs, and the table gives the median over the 3
processes.

H100 80GB HBM3:

| M | tactic | host us, main | host us, this PR | GPU us, main | GPU us,
this PR |
|---|---|---|---|---|---|
| 4096 | autotuner lookup | 199.1 | 114.5 | 243.3 | 244.3 |
| 4096 | fixed | 167.1 | 90.4 | 244.2 | 242.4 |
| 128 | autotuner lookup | 194.3 | 110.9 | 194.6 (host-bound) | 111.5
(host-bound) |
| 128 | fixed | 163.4 | 87.3 | 163.8 (host-bound) | 88.0 (host-bound) |

Between-process CV is at most 1.1% in every cell. At M=4096 the call is
GPU-bound either way; host time matters where the GPU work per call is
smaller than the host work, as for small expert shards and moderate
token counts.

<details>
<summary>Benchmark script</summary>

```python
import statistics, time
import torch
from flashinfer.fused_moe.cute_dsl.sm90_contiguous_gather_grouped_gemm_act_fusion import (
    interleave_up_gate_sm90,
)
from flashinfer.fused_moe.cute_dsl.sm90_fused_moe import cute_dsl_fused_moe_bf16
from flashinfer.fused_moe.cute_dsl.sm90_tuner import DEFAULT_SM90_MOE_TACTIC

E, TOPK, HIDDEN, INTER, ITERS = 128, 8, 2048, 96, 100
dev, dt = "cuda", torch.bfloat16
w1 = interleave_up_gate_sm90(torch.randn(E, 2 * INTER, HIDDEN, device=dev, dtype=dt) * 0.05)
w2 = torch.randn(E, HIDDEN, INTER, device=dev, dtype=dt) * 0.05
for m in (4096, 128):
    x = torch.randn(m, HIDDEN, device=dev, dtype=dt)
    scales, ids = torch.topk(torch.randn(m, E, device=dev).softmax(-1), TOPK, dim=-1)
    ids, scales = ids.to(torch.int32), scales.float()
    out = torch.empty(m, HIDDEN, device=dev, dtype=dt)
    for label, tactic in (("autotuner lookup", None), ("fixed", DEFAULT_SM90_MOE_TACTIC)):
        def fn():
            cute_dsl_fused_moe_bf16(x, ids, scales, w1, w2, num_experts=E, top_k=TOPK,
                                    moe_output=out, tactic=tactic)
        for _ in range(10):
            fn()
        host, gpu = [], []
        for _ in range(5):
            torch.cuda.synchronize()
            start, end = torch.cuda.Event(True), torch.cuda.Event(True)
            start.record()
            t0 = time.perf_counter()
            for _ in range(ITERS):  # no sync: the GPU runs asynchronously
                fn()
            t1 = time.perf_counter()
            end.record()
            torch.cuda.synchronize()
            host.append(1e6 * (t1 - t0) / ITERS)
            gpu.append(1e3 * start.elapsed_time(end) / ITERS)
        print(f"M={m} {label}: host {statistics.median(host):.1f} us/call, "
              f"GPU {statistics.median(gpu):.1f} us/call")
```
</details>

### Serving

vLLM serving Qwen3-30B-A3B bf16 with TP8 on 8x H100 80GB HBM3, `vllm
bench serve --dataset-name random`, 4096 input / 512 output tokens,
`--ignore-eos`, concurrency 1 (100 prompts) and 16 (300 prompts). The
server uses a vLLM adapter for this MoE backend that is not yet
upstream. The three configurations ran in alternating order over two
rounds, the second reversed; each cell gives round 1 / round 2:

| concurrency | metric | Triton MoE | CuTe DSL MoE, main | CuTe DSL MoE,
this PR |
|---|---|---|---|---|
| 1 | median TTFT (ms) | 66.2 / 65.3 | 77.6 / 73.9 | 67.5 / 68.2 |
| 1 | median TPOT (ms) | 3.34 / 3.34 | 3.29 / 3.30 | 3.31 / 3.30 |
| 16 | median TTFT (ms) | 273.5 / 273.1 | 291.9 / 279.7 | 248.6 / 245.7
|
| 16 | median TPOT (ms) | 6.01 / 6.03 | 5.33 / 5.39 | 5.26 / 5.36 |
| 16 | output tok/s | 2377 / 2417 | 2687 / 2685 | 2764 / 2736 |

The single-request 4096-token prefill is host-bound for both MoE
backends: an nsys trace of the TP8 server shows each decoder layer
spending about 1.3-1.4 ms of host time on the slowest rank, against
about 0.5-0.6 ms of GPU work. This change narrows the c=1 TTFT gap to
the Triton MoE backend from about 10 ms to about 2 ms. At concurrency 16
it lowers the median TTFT by about 14% and raises the output throughput
by about 2%.

## 🔍 Related Issues

Related to #3521 (integrating this backend into vLLM, where the eager
host overhead showed up as a TTFT regression).

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

The existing end-to-end tests, including CUDA-graph capture and replay,
cover the new launch path. `test_cute_dsl_bf16_moe_bad_inputs` and
`test_cute_dsl_bf16_moe_gemm2_bad_inputs` additionally check that
misaligned operands and non-float32 `token_final_scales` raise
`ValueError`.

Results:
- H100 80GB HBM3, this branch on current `main`:
`tests/moe/test_cute_dsl_bf16_moe.py`,
`tests/moe/test_cute_dsl_bf16_gather_grouped_gemm.py` and
`tests/moe/test_cute_dsl_bf16_grouped_gemm_finalize.py`: 187 passed.

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

- `make_ptr` used to check the alignment of every pointer on each call.
The GEMM wrappers now check the 16-byte alignment of the activation,
weight and output pointers on every call; the int32 routing metadata and
float32 `token_final_scales`, which torch always allocates 4-byte
aligned, are checked only when a kernel is compiled, as the wrapper
docstrings state. `cute_dsl_fused_moe_bf16` rejects non-float32
`token_final_scales` before launching anything; previously only GEMM2
checked it, after `moe_sort` and GEMM1 had run.
- The remaining host time per call is mostly `moe_sort` (about 25 us),
the autotuner lookup (about 23 us) and the aux-stream fork/join that
overlaps the output memset with GEMM1 (about 15 us). All three are
unchanged; the fork/join keeps the GPU time unchanged, and `moe_sort`
and the autotuner are shared with other MoE backends.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* Reduced launch overhead for supported fused MoE operations by reusing
compiled runners and streamlining kernel launches.
* **Bug Fixes**
* Added checks that reject misaligned tensor addresses and routing
weights with unsupported data types before kernel launch.
* **Documentation**
* Clarified alignment requirements and kernel compilation and warmup
guidance for saved tuning results, graph capture, and latency-sensitive
serving.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [71945d4](https://github.com/flashinfer-ai/flashinfer/commit/71945d4fa83fa1582a6740bc4e6b15abbbad8588)

- **作者**: Jiahan Chang (Cyrus)
- **时间**: 2026-11-10T03:45:53Z
- **提交信息**: fix(moe): exclude unsupported NVFP4 LoRA tile 192 (#9212)

<!-- .github/pull_request_template.md -->

## 📌 Description

NVFP4 routed MoE with `gemm1_lora_delta` can select tile 192 even though
the E2m1 x E2m1 MN-bias kernel is unavailable. At 3073 tokens with 128
experts and top-k 8, this makes the default launch fail with "No kernel
found"; autotune can fail while enumerating the same tile.

Make FP4 supported tiles depend on the GEMM1 bias type and exclude tile
192 for NVFP4 MN bias in both launcher construction and tactic
enumeration.

## 🔍 Related Issues

Fixes #8272

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

- [ ] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/moe/test_trtllm_gen_per_token_moe.py`

Validation:

- B300 (SM103), PyTorch 2.13.0+cu130: local validation of this
tile-filtering fix on base `8a3e9d263` passed all four combinations of
3072/3073 tokens and autotuning off/on (`4 passed`, exit 0), including
numerical checks and exclusion of tile 192 from LoRA tactics. The
validation harness is not included in this PR.
- This PR is based on `6c23b76b5`. The exact PR revision has not yet
been GPU-tested.
- Touched-file pre-commit checks and `git diff --check` pass. The full
repository hook/test suite was not run.

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

The local numerical checks used `do_finalize=True`; the original issue's
`do_finalize=False` configuration has not been separately exercised. The
filtering is shared by both finalize modes. No public API or kernel
binary changes. AI-assisted implementation and validation.

### [9d274f6](https://github.com/flashinfer-ai/flashinfer/commit/9d274f6ab7b33aaed4756d56e601c4e7e50c6e69)

- **作者**: Jimmy Zhou
- **时间**: 2026-11-10T02:51:18Z
- **提交信息**: test(cake_rmsnorm): count a det-pair window as det-inherited when it runs any det program of its route (#9038)

## Problem


`test_cake_rmsnorm_train_all_sm.py::test_backward_beside_an_all_sm_kernel_with_the_max_shared_carveout[res-h6144-{bf16,f32}-256]`
fails on sm_107a (VR) on main and in the v0.7.4rc1 CI run (#9028):

```
listed=True det_program=False program=0dcdc563 det_program=c15868b8 ... assert 'waits' == 'starts'
```

## Root cause

The non-deterministic package lets a backward call wait beside a kernel
resident on every SM only when its window is in the package's whole-SM
list (`cake_windows.WHOLE_SM`) and the call runs the deterministic
package's program, so the wait is inherited from that program. The test
checked the second condition by comparing with the program the
deterministic package selects *at the same token count*.

#8813 moved the deterministic package's sm_107a residual H 6144 backward
at T <= 960 to a new column-task program (`c15868b8`), which starts
beside the all-SM kernel. The non-deterministic package still runs the
deterministic pair program `0dcdc563` in its listed window (64, 448],
and the deterministic package still runs that program above T 960.
Neither kernel nor the whole-SM list changed. Only the reference program
at T = 256 changed, so the comparison failed.

## Fix

Count the call as det-inherited when its main program is any main
program of the deterministic package's route (any token count), for the
BF16 owner and the FP32-weight twin paths alike. A wait in a
single-kernel window, in an unlisted window, or from a program the
deterministic package does not ship still fails.

A possible follow-up, separate from this PR: export the new small-T
program into the non-deterministic package, so its residual backward at
T <= 448 starts beside an all-SM kernel like the deterministic one now
does.

## Validation

R200 (sm_107a), CI image `flashinfer-ci-cu134:20260930-b1420f1`,
release-v0.7.4 (a2599b01b) before and after:

- before: `[res-h6144-bf16-256]` and `[res-h6144-f32-256]` fail exactly
as in CI; the other 29 cases pass.
- after: those two are reported as not measured (det-inherited, program
`0dcdc563`), and the other 29 still pass.

Non-regression: the 16 `tests/norm/test_cake_rmsnorm_*train*.py` files
(both packages), patched tree:

- GB300, release-v0.7.4 + patch: CUDA 12.9: 2480 passed / 196 skipped.
CUDA 13.0: 2481 / 195. CUDA 13.4: 2481 / 195. No failures.
- B200, CUDA 13.0, main + this patch + #9038: 2480 passed / 196 skipped.
No failures.
- R200 dev box, CUDA 13.4: the only failures (5 in
`test_cake_rmsnorm_det_train_pairs.py::test_workspace_puts_the_counters_first_and_grows_with_the_rows`
and the 2 `det_train_stall` all-SM tests on small-T sm_107a windows)
fail identically on unpatched release-v0.7.4 on that box. They do not
fail in the VR CI job.

Fixes #9028


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Tests**
* Expanded validation of deterministic training behavior across
different token counts and precision variants, including cases that use
configured pre-move programs.
* Retained checks for the complete streaming-multiprocessor list and
program form when identifying inherited waits.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [3f3d029](https://github.com/flashinfer-ai/flashinfer/commit/3f3d0294c54d4deb97218cb93ed1e373ac624328)

- **作者**: Akaash Parthasarathy
- **时间**: 2026-11-10T02:33:08Z
- **提交信息**: fix(moe_ep): validate Kimi staged outputs and async flag batches (#9197)

<!-- .github/pull_request_template.md -->

## 📌 Description

`compute_staged()` bypasses the layer's forward validation, allowing a
destination with the wrong width, dtype or device to reach Kimi's
reducer. Validate the destination before launch while preserving empty
batches and buffers with extra rows. Ordinary forwards use a prepared
path after validation and staging, avoiding repeated output and
workspace checks.

Reject asynchronous `epi_flag_batches` above the four publisher warps,
which can drop completion signals and stall execution. Synchronous NVFP4
batches keep their existing limit.

## 🔍 Related Issues

Follow-up to #8934.

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

Native eager and graph tests pass on B300 (EP1) and B200 (EP8). The host
suite passes with 132 tests; two installed-wheel checks are skipped.

- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/cpu/moe_ep/test_kimi_k3_runtime.py
tests/cpu/moe_ep/test_mega_workspace_api.py
tests/moe_ep/test_sm100_kimi_k3.py`

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

Paired B300 EP1 measurements against pre-PR main (`0df62d94d`) show
1.3–2.8 µs less CPU enqueue time per eager forward from removing
repeated checks after staging. At 256 tokens/rank with NVFP4/BF16, host
enqueue is 229.0 → 226.8 µs; CUDA timing is 819.1 → 819.0 µs and graph
replay remains about 806 µs. The extra staged-output checks add about
0.26 µs of CPU work in isolation. Measurements use the benchmark's
sparse layout-test weights (896 experts, hidden 3584, intermediate 3072,
top-16) and exclude compilation, weight preparation and workspace
allocation.

Run the updated benchmark against each revision's source:

```bash
python -m benchmarks.bench_kimi_k3_moe_ep --tokens 256 --quant-kind nvfp4 --wire bf16 --execution-mode eager --output-mode owned
```



<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* The Kimi K3 MoE benchmark now supports eager and CUDA graph execution,
caller-provided or layer-owned outputs, and reports host enqueue time
alongside CUDA-event timings.
* **Bug Fixes**
* Invalid staged-computation outputs are now rejected unless they meet
the required shape, dtype, device, contiguity, and alignment
constraints.
* MXFP4/MXFP8 configurations now reject asynchronous epilogue batch
values outside the supported range of 1–4.
* **Tests**
* Added coverage for output validation, batch limits, staged-computation
accuracy, and CUDA graph replay. The expanded suite passes on B300 at
EP1 and B200 at EP8; staged-output and batch checks have not been rerun
at EP16.
* **Documentation**
  * Clarified asynchronous batch limits and validation coverage.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [fe8dbf2](https://github.com/flashinfer-ai/flashinfer/commit/fe8dbf224ee8f58117a2afbd07356d9d694e80a6)

- **作者**: Adrian
- **时间**: 2026-11-10T02:31:47Z
- **提交信息**: test(mhc): remove gitignore dependency from package wiring checks (#9302)

<!-- .github/pull_request_template.md -->

## 📌 Description

The November 7 nightly (pipeline 80095586), November 8 nightly (pipeline
80310859), and November 9 nightly (pipeline 80549007) failed three MHC
`test_package_wiring` cases because their source archives omitted
package-local `.gitignore` files. Each test read that file and required
a literal `aot/` entry, although source archives can omit Git metadata
and equivalent ignore rules can live in parent directories.

Remove those three assertions and update their descriptions. Keep the
ignore rules and all package, build-manifest, registry, former-path, and
pre-commit wiring checks unchanged.

## 🔍 Related Issues

No separate issue; observed in the nightly pipelines listed above.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

The hooks pass on all three changed files (`pre-commit run --files
...`); a repository-wide hook run was not requested.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: Not requested; this change only removes three CPU-test
assertions and updates their descriptions.

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/cpu/mhc/test_cake_mhc_det_train_names.py
tests/cpu/mhc/test_cake_mhc_head_det_train_names.py
tests/cpu/mhc/test_cake_mhc_head_nondet_train_names.py`

Validation: with all three package `.gitignore` files temporarily
absent, the unchanged tests fail with `FileNotFoundError` (**3
failed**), and the updated tests pass (**3 passed**). The targeted tests
were rerun after rebasing onto `49e9ffef9`, using the CUDA 13.4 CI image
without GPU access. The ignore files were restored unchanged. No new
test functions were added; the full GPU suite was not run.

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

The remaining package-wiring assertions are unchanged. This removes a
repository-hygiene requirement from tests that also run against source
archives.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Tests**
* Updated package-wiring test coverage to focus on package mapping,
included package data, manifests, and related configuration. Checks for
ignored build directories are no longer included.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [2fb1ea6](https://github.com/flashinfer-ai/flashinfer/commit/2fb1ea6705c86bb6bd8a8cac6a2da164ce803e79)

- **作者**: Akaash Parthasarathy
- **时间**: 2026-11-10T02:06:26Z
- **提交信息**: fix(moe_ep): correct standard Blackwell NVFP4 configuration and tuning (#9245)

<!-- .github/pull_request_template.md -->

## 📌 Description

Fix configuration of the standard SM100 NVFP4 backend at workspace
capacities of 1024 tokens and above. Its inherited N256/K256 default is
invalid for this kernel; use N256/K128 and apply native overrides before
validating the final configuration. Resolve in-kernel reduction before
choosing the finalizer.

Add N64 to the NVFP4 tuning candidates, with one FC2 TMA stage for bulk
stores. Keep N128/N256 candidates and existing cache entries.

Use integer row indices in the tuning reference. With a BF16 default
dtype, floating-point sampling can round row 511 up to 512 and read out
of bounds.

Vendored kernel sources are unchanged.

### NVFP4 operator tuning

Four B200s, EP4, NVFP4 weights/activations, BF16 input/combine, 512
experts, top-k 10, late routing weights and unit runtime alphas. Both
columns use independently tuned configurations at the same capacity. The
comparison isolates the N64 candidates added here; lower latency is
better.

| Hidden / intermediate | Live tokens / capacity | Routing | N128/N256
grid (µs) | N64 grid (µs) | Latency change |
|---|---:|---|---:|---:|---:|
| 2048 / 512 | 32 / 32 | uniform | 102.368 | 98.304 | -3.97% |
| 2048 / 512 | 32 / 8192 | uniform | 141.344 | 139.168 | -1.54% |
| 2048 / 512 | 2048 / 2048 | uniform | 210.880 | 204.640 | -2.96% |
| 4096 / 1024 | 32 / 32 | uniform | 192.432 | 188.400 | -2.10% |
| 4096 / 1024 | 32 / 8192 | uniform | 260.096 | 258.064 | -0.78% |
| 4096 / 1024 | 2048 / 2048 | uniform | 346.128 | 380.800 | +10.02% |
| 4096 / 1024 | 32 / 32 | skewed | 79.856 | 86.064 | +7.77% |

Times cover the full `MoEEpMegaLayer.forward()` in a CUDA graph,
including staging and finalization, with 64-row padding. Each value is
the median of three rounds, using the slowest rank's median over 50
samples after 20 warmups. A 300 MiB L2 flush runs outside each timed
window. Skewed routes select from 16 experts. N128/N256 candidates
remain available where N64 loses.

## 🔍 Related Issues

Follow-up to #7001.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks on the changed files with `pre-commit run
--files ...` and fixed any reported issues.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] Affected host tests and GPU qualification pass.
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
      Reason: targeted MoE EP coverage is sufficient.

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/moe_ep/test_mega_workspace_knobs.py
tests/moe_ep/test_sm100_standard_config.py
tests/moe_ep/test_sm100_tuning_protocol.py
tests/moe_ep/test_sm100_standard_features.py
tests/moe_ep/test_sm100_auto_multirank.py`

265 host checks pass. GPU checks on B200 and B300 cover large
capacities, native overrides, N64 tuning, finalization modes, persisted
winners and CUDA graph replay. The integer-sampling regression covers
FP16/BF16 default dtypes, sample sizes of 1 and 64, and empty,
single-row and large inputs.

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

The N64 candidate expansion is limited to standard NVFP4/NVFP4. MXFP8,
MXFP4, BF16 and GenPhase keep their existing tuning policies. The
native-override fix applies across the standard backends; integer
reference sampling is shared by standard and GenPhase. Legacy selectors
and cache revisions are unchanged.

### [0bdafda](https://github.com/flashinfer-ai/flashinfer/commit/0bdafda8f721aaa4981c017a61b99f1122267edf)

- **作者**: eigen
- **时间**: 2026-11-10T01:42:08Z
- **提交信息**: perf(cake_comm): SM90 decoupled-storer producer and SM90 / SM100 / SM103 plan updates for QKV norm-RoPE exchange (#9276)

`QkvNormRopeExchangeOverlap` (`flashinfer.comm`, kernel
`cake_qkv_norm_rope_exchange_overlap`) is a Cake kernel. It fuses the
QKV projection, per-head QK RMSNorm and RoPE with the Ulysses QKV
all-to-all exchange. It supports one data type: BF16 activations and
weights with fp32 accumulation. This PR updates the SM90 (`sm_90a`),
SM100 (`sm_100a`) and SM103 (`sm_103a`) builds of that variant. On SM90,
the producer now uses a decoupled storer. The exception is 8-rank rows
with hidden ≥ 6144 and M = B·S/W ≥ 8192, which keep the previous
producer build. The plans change on all three architectures. Outputs are
bit-identical to the baseline. The baseline is the previous Cake version
of the kernel on FlashInfer main (11bf37df). The mean gain over the
baseline is +1.47 % on B300 (72 rows) and +1.24 % on B200 (72 rows). On
H100 it is +2.33 % over the 24 W 8 rows.

The kernel has no other Cake variant, and the family ships on `sm_90a`,
`sm_100a`, `sm_103a` and `sm_107a`.

## B300 (`sm_103a`)

Kernel latency in ms on 8 × NVIDIA B300 SXM6 AC (Blackwell Ultra,
`sm_103a`), CUDA 13.4.2. Measured with
`benchmarks/comm/bench_qkv_norm_rope_exchange_overlap.py --rows all`
(CUPTI, cold L2). For each run, the value is the maximum over ranks, and
then the median over samples. Each table value is the mean of 4
repetitions. A row with W ranks uses W GPUs. Speedup = baseline / this
PR.

Mean gain over the 72 rows: +1.47 %.

| W | hidden | S_global | baseline (ms) | this PR (ms) | speedup |
|---:|---:|---:|---:|---:|---:|
| 8 | 3072 | 4096 | 0.0667 | 0.0711 | 0.9370 |
| 8 | 3072 | 8192 | 0.1007 | 0.0799 | 1.2604 |
| 8 | 3072 | 16384 | 0.1451 | 0.1179 | 1.2304 |
| 8 | 3072 | 32768 | 0.1655 | 0.1648 | 1.0044 |
| 8 | 3072 | 65536 | 0.3778 | 0.3470 | 1.0887 |
| 8 | 3072 | 131072 | 0.7769 | 0.6787 | 1.1448 |
| 8 | 4096 | 4096 | 0.0791 | 0.1003 | 0.7887 |
| 8 | 4096 | 8192 | 0.0913 | 0.0928 | 0.9835 |
| 8 | 4096 | 16384 | 0.1539 | 0.1559 | 0.9876 |
| 8 | 4096 | 32768 | 0.2609 | 0.2609 | 1.0000 |
| 8 | 4096 | 65536 | 0.5204 | 0.5309 | 0.9802 |
| 8 | 4096 | 131072 | 1.1303 | 1.0830 | 1.0437 |
| 8 | 6144 | 4096 | 0.1151 | 0.0982 | 1.1726 |
| 8 | 6144 | 8192 | 0.1566 | 0.1653 | 0.9474 |
| 8 | 6144 | 16384 | 0.2829 | 0.2828 | 1.0004 |
| 8 | 6144 | 32768 | 0.5800 | 0.5897 | 0.9835 |
| 8 | 6144 | 65536 | 1.2968 | 1.2918 | 1.0039 |
| 8 | 6144 | 131072 | 2.9789 | 2.9784 | 1.0002 |
| 8 | 8192 | 4096 | 0.1584 | 0.1759 | 0.9003 |
| 8 | 8192 | 8192 | 0.2777 | 0.2796 | 0.9930 |
| 8 | 8192 | 16384 | 0.5200 | 0.5111 | 1.0175 |
| 8 | 8192 | 32768 | 1.0912 | 1.0895 | 1.0015 |
| 8 | 8192 | 65536 | 2.5676 | 2.5738 | 0.9976 |
| 8 | 8192 | 131072 | 5.2224 | 5.2543 | 0.9939 |
| 4 | 3072 | 4096 | 0.0718 | 0.0705 | 1.0178 |
| 4 | 3072 | 8192 | 0.0935 | 0.0929 | 1.0073 |
| 4 | 3072 | 16384 | 0.1610 | 0.1537 | 1.0472 |
| 4 | 3072 | 32768 | 0.3416 | 0.2931 | 1.1654 |
| 4 | 3072 | 65536 | 0.6319 | 0.5858 | 1.0785 |
| 4 | 3072 | 131072 | 1.3383 | 1.2092 | 1.1067 |
| 4 | 4096 | 4096 | 0.0946 | 0.0921 | 1.0272 |
| 4 | 4096 | 8192 | 0.1445 | 0.1432 | 1.0090 |
| 4 | 4096 | 16384 | 0.2630 | 0.2625 | 1.0018 |
| 4 | 4096 | 32768 | 0.5085 | 0.5108 | 0.9955 |
| 4 | 4096 | 65536 | 1.0405 | 1.0529 | 0.9882 |
| 4 | 4096 | 131072 | 2.4673 | 2.4782 | 0.9956 |
| 4 | 6144 | 4096 | 0.1517 | 0.1521 | 0.9975 |
| 4 | 6144 | 8192 | 0.2864 | 0.2855 | 1.0030 |
| 4 | 6144 | 16384 | 0.5728 | 0.5778 | 0.9913 |
| 4 | 6144 | 32768 | 1.2472 | 1.2414 | 1.0047 |
| 4 | 6144 | 65536 | 2.8713 | 2.8738 | 0.9991 |
| 4 | 6144 | 131072 | 5.7694 | 5.7749 | 0.9991 |
| 4 | 8192 | 4096 | 0.2760 | 0.2737 | 1.0086 |
| 4 | 8192 | 8192 | 0.5085 | 0.5075 | 1.0021 |
| 4 | 8192 | 16384 | 1.0563 | 1.0985 | 0.9615 |
| 4 | 8192 | 32768 | 2.5555 | 2.5414 | 1.0055 |
| 4 | 8192 | 65536 | 5.1341 | 5.1432 | 0.9982 |
| 4 | 8192 | 131072 | 10.5728 | 10.5223 | 1.0048 |
| 2 | 3072 | 4096 | 0.1028 | 0.0945 | 1.0878 |
| 2 | 3072 | 8192 | 0.1576 | 0.1573 | 1.0017 |
| 2 | 3072 | 16384 | 0.3100 | 0.2927 | 1.0591 |
| 2 | 3072 | 32768 | 0.5880 | 0.5882 | 0.9995 |
| 2 | 3072 | 65536 | 1.2985 | 1.3013 | 0.9979 |
| 2 | 3072 | 131072 | 2.8218 | 2.8193 | 1.0009 |
| 2 | 4096 | 4096 | 0.1406 | 0.1406 | 1.0000 |
| 2 | 4096 | 8192 | 0.2629 | 0.2637 | 0.9970 |
| 2 | 4096 | 16384 | 0.5129 | 0.5172 | 0.9917 |
| 2 | 4096 | 32768 | 1.1143 | 1.1248 | 0.9907 |
| 2 | 4096 | 65536 | 2.4864 | 2.4866 | 0.9999 |
| 2 | 4096 | 131072 | 5.1890 | 5.2198 | 0.9941 |
| 2 | 6144 | 4096 | 0.2806 | 0.2816 | 0.9966 |
| 2 | 6144 | 8192 | 0.5696 | 0.5722 | 0.9955 |
| 2 | 6144 | 16384 | 1.3058 | 1.2539 | 1.0414 |
| 2 | 6144 | 32768 | 2.7981 | 2.7796 | 1.0066 |
| 2 | 6144 | 65536 | 5.9162 | 5.9231 | 0.9988 |
| 2 | 6144 | 131072 | 12.4129 | 12.3658 | 1.0038 |
| 2 | 8192 | 4096 | 0.5102 | 0.5083 | 1.0038 |
| 2 | 8192 | 8192 | 1.1003 | 1.0884 | 1.0109 |
| 2 | 8192 | 16384 | 2.5175 | 2.5183 | 0.9997 |
| 2 | 8192 | 32768 | 5.1488 | 5.1499 | 0.9998 |
| 2 | 8192 | 65536 | 11.0941 | 11.0489 | 1.0041 |
| 2 | 8192 | 131072 | 22.8553 | 22.7962 | 1.0026 |

## B200 (`sm_100a`)

Kernel latency in ms on 8 × NVIDIA B200 (Blackwell, `sm_100a`), CUDA
13.4.2. This uses the same benchmark and statistic as the B300 table. W
8 and W 4 values are the mean of 4 repetitions. W 2 values are the mean
of 6 repetitions for the baseline and 7 for this PR. Speedup = baseline
/ this PR.

Mean gain over the 72 rows: +1.24 % (W 8 and W 4: +1.99 %; W 2: −0.27
%).

| W | hidden | S_global | baseline (ms) | this PR (ms) | speedup |
|---:|---:|---:|---:|---:|---:|
| 8 | 3072 | 4096 | 0.0825 | 0.0810 | 1.0185 |
| 8 | 3072 | 8192 | 0.0735 | 0.0728 | 1.0102 |
| 8 | 3072 | 16384 | 0.1228 | 0.0991 | 1.2399 |
| 8 | 3072 | 32768 | 0.1664 | 0.1657 | 1.0046 |
| 8 | 3072 | 65536 | 0.3874 | 0.3316 | 1.1682 |
| 8 | 3072 | 131072 | 0.8085 | 0.6541 | 1.2362 |
| 8 | 4096 | 4096 | 0.0721 | 0.0674 | 1.0683 |
| 8 | 4096 | 8192 | 0.0856 | 0.1126 | 0.7603 |
| 8 | 4096 | 16384 | 0.1541 | 0.1483 | 1.0387 |
| 8 | 4096 | 32768 | 0.2729 | 0.2823 | 0.9667 |
| 8 | 4096 | 65536 | 0.5669 | 0.5737 | 0.9881 |
| 8 | 4096 | 131072 | 1.1461 | 1.1557 | 0.9917 |
| 8 | 6144 | 4096 | 0.1025 | 0.0903 | 1.1350 |
| 8 | 6144 | 8192 | 0.1589 | 0.1573 | 1.0100 |
| 8 | 6144 | 16384 | 0.3018 | 0.3013 | 1.0016 |
| 8 | 6144 | 32768 | 0.6324 | 0.6321 | 1.0004 |
| 8 | 6144 | 65536 | 1.3147 | 1.3150 | 0.9997 |
| 8 | 6144 | 131072 | 2.9955 | 2.9368 | 1.0200 |
| 8 | 8192 | 4096 | 0.1570 | 0.1614 | 0.9730 |
| 8 | 8192 | 8192 | 0.2978 | 0.2980 | 0.9993 |
| 8 | 8192 | 16384 | 0.5583 | 0.5590 | 0.9988 |
| 8 | 8192 | 32768 | 1.2126 | 1.1720 | 1.0346 |
| 8 | 8192 | 65536 | 2.6887 | 2.7048 | 0.9940 |
| 8 | 8192 | 131072 | 5.3028 | 5.2969 | 1.0011 |
| 4 | 3072 | 4096 | 0.0678 | 0.0684 | 0.9906 |
| 4 | 3072 | 8192 | 0.0912 | 0.0911 | 1.0016 |
| 4 | 3072 | 16384 | 0.1577 | 0.1569 | 1.0050 |
| 4 | 3072 | 32768 | 0.3476 | 0.3134 | 1.1090 |
| 4 | 3072 | 65536 | 0.6605 | 0.6300 | 1.0485 |
| 4 | 3072 | 131072 | 1.3752 | 1.2601 | 1.0913 |
| 4 | 4096 | 4096 | 0.0927 | 0.0928 | 0.9996 |
| 4 | 4096 | 8192 | 0.1514 | 0.1503 | 1.0074 |
| 4 | 4096 | 16384 | 0.2839 | 0.2834 | 1.0017 |
| 4 | 4096 | 32768 | 0.5585 | 0.5588 | 0.9995 |
| 4 | 4096 | 65536 | 1.1145 | 1.1205 | 0.9947 |
| 4 | 4096 | 131072 | 2.5251 | 2.4506 | 1.0304 |
| 4 | 6144 | 4096 | 0.1590 | 0.1588 | 1.0012 |
| 4 | 6144 | 8192 | 0.3056 | 0.3052 | 1.0013 |
| 4 | 6144 | 16384 | 0.6300 | 0.6302 | 0.9996 |
| 4 | 6144 | 32768 | 1.2845 | 1.2925 | 0.9939 |
| 4 | 6144 | 65536 | 2.9358 | 2.9625 | 0.9910 |
| 4 | 6144 | 131072 | 5.8645 | 5.8471 | 1.0030 |
| 4 | 8192 | 4096 | 0.2997 | 0.2994 | 1.0011 |
| 4 | 8192 | 8192 | 0.5619 | 0.5651 | 0.9943 |
| 4 | 8192 | 16384 | 1.1519 | 1.1540 | 0.9981 |
| 4 | 8192 | 32768 | 2.5480 | 2.4958 | 1.0209 |
| 4 | 8192 | 65536 | 5.3095 | 5.2587 | 1.0097 |
| 4 | 8192 | 131072 | 10.8838 | 10.8476 | 1.0033 |
| 2 | 3072 | 4096 | 0.0950 | 0.0987 | 0.9623 |
| 2 | 3072 | 8192 | 0.1642 | 0.1642 | 0.9999 |
| 2 | 3072 | 16384 | 0.3252 | 0.3122 | 1.0416 |
| 2 | 3072 | 32768 | 0.6421 | 0.6258 | 1.0259 |
| 2 | 3072 | 65536 | 1.2644 | 1.2713 | 0.9946 |
| 2 | 3072 | 131072 | 2.7525 | 2.7868 | 0.9877 |
| 2 | 4096 | 4096 | 0.1468 | 0.1469 | 0.9994 |
| 2 | 4096 | 8192 | 0.2805 | 0.2804 | 1.0003 |
| 2 | 4096 | 16384 | 0.5570 | 0.5567 | 1.0006 |
| 2 | 4096 | 32768 | 1.1195 | 1.1143 | 1.0047 |
| 2 | 4096 | 65536 | 2.4073 | 2.4202 | 0.9947 |
| 2 | 4096 | 131072 | 5.0050 | 5.0716 | 0.9869 |
| 2 | 6144 | 4096 | 0.2996 | 0.2992 | 1.0012 |
| 2 | 6144 | 8192 | 0.6146 | 0.6147 | 0.9999 |
| 2 | 6144 | 16384 | 1.2380 | 1.2472 | 0.9926 |
| 2 | 6144 | 32768 | 2.6713 | 2.8289 | 0.9443 |
| 2 | 6144 | 65536 | 5.7687 | 5.7941 | 0.9956 |
| 2 | 6144 | 131072 | 12.3725 | 12.3647 | 1.0006 |
| 2 | 8192 | 4096 | 0.5566 | 0.5569 | 0.9994 |
| 2 | 8192 | 8192 | 1.1171 | 1.1183 | 0.9989 |
| 2 | 8192 | 16384 | 2.4044 | 2.4212 | 0.9931 |
| 2 | 8192 | 32768 | 5.0450 | 5.0369 | 1.0016 |
| 2 | 8192 | 65536 | 10.9296 | 10.8995 | 1.0028 |
| 2 | 8192 | 131072 | 23.6474 | 23.4889 | 1.0067 |

## H100 (`sm_90a`)

Kernel latency in ms on 8 × NVIDIA H100 80GB HBM3 (Hopper, `sm_90a`),
CUDA 13.4.2. This uses the same benchmark and statistic as the B300
table. W 8 values are the mean of 8 repetitions. W 4 and W 2 values are
the mean of 4 repetitions. Speedup = baseline / this PR. The W 8 rows
with hidden 6144 or 8192 and S_global 65536 or 131072 keep the previous
producer build.

Mean gain over the 24 W 8 rows: +2.33 %.

| W | hidden | S_global | baseline (ms) | this PR (ms) | speedup |
|---:|---:|---:|---:|---:|---:|
| 8 | 3072 | 4096 | 0.0892 | 0.0861 | 1.0360 |
| 8 | 3072 | 8192 | 0.1477 | 0.1373 | 1.0757 |
| 8 | 3072 | 16384 | 0.2642 | 0.2523 | 1.0473 |
| 8 | 3072 | 32768 | 0.5056 | 0.4959 | 1.0197 |
| 8 | 3072 | 65536 | 1.0212 | 0.9927 | 1.0287 |
| 8 | 3072 | 131072 | 2.7688 | 2.7277 | 1.0151 |
| 8 | 4096 | 4096 | 0.1278 | 0.1246 | 1.0259 |
| 8 | 4096 | 8192 | 0.1943 | 0.1839 | 1.0567 |
| 8 | 4096 | 16384 | 0.3694 | 0.3474 | 1.0633 |
| 8 | 4096 | 32768 | 0.7044 | 0.6832 | 1.0310 |
| 8 | 4096 | 65536 | 1.4333 | 1.4169 | 1.0116 |
| 8 | 4096 | 131072 | 3.9087 | 3.9133 | 0.9988 |
| 8 | 6144 | 4096 | 0.2469 | 0.2428 | 1.0168 |
| 8 | 6144 | 8192 | 0.3987 | 0.3935 | 1.0132 |
| 8 | 6144 | 16384 | 0.7093 | 0.6941 | 1.0219 |
| 8 | 6144 | 32768 | 1.5507 | 1.5485 | 1.0014 |
| 8 | 6144 | 65536 | 3.1524 | 3.1426 | 1.0031 |
| 8 | 6144 | 131072 | 8.7441 | 8.6841 | 1.0069 |
| 8 | 8192 | 4096 | 0.3309 | 0.3210 | 1.0309 |
| 8 | 8192 | 8192 | 0.6324 | 0.6137 | 1.0304 |
| 8 | 8192 | 16384 | 1.3187 | 1.2845 | 1.0266 |
| 8 | 8192 | 32768 | 2.7377 | 2.7451 | 0.9973 |
| 8 | 8192 | 65536 | 5.4430 | 5.4381 | 1.0009 |
| 8 | 8192 | 131072 | 15.5557 | 15.5421 | 1.0009 |
| 4 | 3072 | 4096 | 0.1389 | 0.1349 | 1.0297 |
| 4 | 3072 | 8192 | 0.2329 | 0.2246 | 1.0372 |
| 4 | 3072 | 16384 | 0.4303 | 0.3873 | 1.1109 |
| 4 | 3072 | 32768 | 0.8559 | 0.7374 | 1.1608 |
| 4 | 3072 | 65536 | 2.2250 | 2.0366 | 1.0925 |
| 4 | 3072 | 131072 | 4.6378 | 4.5893 | 1.0106 |
| 4 | 4096 | 4096 | 0.1837 | 0.1786 | 1.0288 |
| 4 | 4096 | 8192 | 0.3530 | 0.3450 | 1.0231 |
| 4 | 4096 | 16384 | 0.6968 | 0.6805 | 1.0239 |
| 4 | 4096 | 32768 | 1.4165 | 1.3077 | 1.0832 |
| 4 | 4096 | 65536 | 3.8794 | 3.5206 | 1.1019 |
| 4 | 4096 | 131072 | 8.0805 | 7.7641 | 1.0407 |
| 4 | 6144 | 4096 | 0.3899 | 0.3801 | 1.0259 |
| 4 | 6144 | 8192 | 0.7277 | 0.7005 | 1.0388 |
| 4 | 6144 | 16384 | 1.4907 | 1.5197 | 0.9809 |
| 4 | 6144 | 32768 | 3.1440 | 3.1271 | 1.0054 |
| 4 | 6144 | 65536 | 8.6389 | 8.2899 | 1.0421 |
| 4 | 6144 | 131072 | 17.6034 | 17.2578 | 1.0200 |
| 4 | 8192 | 4096 | 0.6227 | 0.6072 | 1.0254 |
| 4 | 8192 | 8192 | 1.2847 | 1.2407 | 1.0355 |
| 4 | 8192 | 16384 | 2.7268 | 2.7232 | 1.0013 |
| 4 | 8192 | 32768 | 5.4956 | 5.4399 | 1.0102 |
| 4 | 8192 | 65536 | 15.2623 | 15.3741 | 0.9927 |
| 4 | 8192 | 131072 | 31.7875 | 31.7244 | 1.0020 |
| 2 | 3072 | 4096 | 0.2282 | 0.2272 | 1.0045 |
| 2 | 3072 | 8192 | 0.4164 | 0.4065 | 1.0245 |
| 2 | 3072 | 16384 | 0.8168 | 0.7181 | 1.1375 |
| 2 | 3072 | 32768 | 2.1089 | 2.0121 | 1.0481 |
| 2 | 3072 | 65536 | 4.3289 | 4.2547 | 1.0174 |
| 2 | 3072 | 131072 | 8.7660 | 8.6650 | 1.0117 |
| 2 | 4096 | 4096 | 0.3392 | 0.3334 | 1.0172 |
| 2 | 4096 | 8192 | 0.6721 | 0.6641 | 1.0121 |
| 2 | 4096 | 16384 | 1.3656 | 1.2548 | 1.0882 |
| 2 | 4096 | 32768 | 3.6193 | 3.4629 | 1.0452 |
| 2 | 4096 | 65536 | 7.4110 | 7.2855 | 1.0172 |
| 2 | 4096 | 131072 | 14.8662 | 15.0742 | 0.9862 |
| 2 | 6144 | 4096 | 0.7179 | 0.7032 | 1.0209 |
| 2 | 6144 | 8192 | 1.5113 | 1.4941 | 1.0116 |
| 2 | 6144 | 16384 | 3.1298 | 3.0999 | 1.0097 |
| 2 | 6144 | 32768 | 8.0404 | 8.0175 | 1.0029 |
| 2 | 6144 | 65536 | 16.5333 | 16.4486 | 1.0052 |
| 2 | 6144 | 131072 | 34.1799 | 34.3541 | 0.9949 |
| 2 | 8192 | 4096 | 1.2584 | 1.2434 | 1.0121 |
| 2 | 8192 | 8192 | 2.6926 | 2.6600 | 1.0123 |
| 2 | 8192 | 16384 | 5.3954 | 5.3742 | 1.0039 |
| 2 | 8192 | 32768 | 14.2865 | 13.9875 | 1.0214 |
| 2 | 8192 | 65536 | 29.0721 | 29.4731 | 0.9864 |
| 2 | 8192 | 131072 | 59.7039 | 59.6786 | 1.0004 |


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added destination-interleaving options for communication plans,
including launch-gate precedence and plan reporting.
* Added 128-column pair-tile selection for eligible SM100 and SM103
configurations.
* Expanded producer-build selection by architecture and group size,
including `sw3` as the SM90 default and row-specific build selection.
* **Performance**
* Lowered the cross-destination-band eligibility threshold from 4096 to
2048 rows for supported configurations.
* **Documentation**
* Updated documented producer-build defaults, row-specific selection
rules, and launch thresholds.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [381960f](https://github.com/flashinfer-ai/flashinfer/commit/381960f63f9ede0a58d95d30218795fa361ce563)

- **作者**: Brian K. Ryu
- **时间**: 2026-11-10T01:18:07Z
- **提交信息**: feat(batch_invariant): `gemm_fp8_nt_groupwise(batch_invariant=True)`, the block-scale fp8 GEMM class (#9280)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

Adds batch invariant mode to `flashinfer.gemm_fp8_nt_groupwise(a, b,
a_scale, b_scale, scale_major_mode, backend="auto",
batch_invariant=True)`. Runs a batch-invariant DeepSeek-style
block-scale fp8 GEMM in place of the backends, with the mode's
guarantee: an output row's bits depend on the input values, their block
scales and the weight's K alone, not on the batch size, the row's
position, the configuration the dispatcher or the autotuner picks or the
SM count.

**Why.** The current groupwise backends are batch-variant where their
small-M and split-K paths engage (CUTLASS switches to a swap-AB
low-latency kernel at M <= 32; the SM107 CuTe-DSL kernel splits K by a
shape rule; `backend="auto"` changes backend with M), so the same row
gives different bits at different batch sizes. The class fixes one
dataflow per K and output dtype.

## Performance
`gemm_fp8_nt_groupwise(..., backend="auto", batch_invariant=True)` vs.
existing backends on the same tensors: **CUTLASS** (both scale layouts),
the SM107 **CuTe-DSL** kernel (split-K by a shape rule, not
batch-invariant; absent on sm_100) and **TRT-LLM**.
* Cold-L2 device time as TFLOP/s, bf16 output, the DeepSeek-V3 dense
weight shapes (8 weights x 10 M values per part). Two batch-invariant
modes untuned and autotuned.
* Two scale layouts: 
  * **MN-layout** = the layout the kernel consumes; 
* **K-layout** = the caller's row-major scales, where the
batch-invariant path copies them to the MN layout at M > 64 and stages
them natively at M <= 64 (that copy is in its time).
* "Best existing" = the fastest of CUTLASS / CuTe-DSL / TRT-LLM for the
cell.

**Rubin (sm_107, 212 SMs)**, reference = best existing backend unless
the column names one:

| M | untuned, K-layout scales vs. best | untuned, MN-layout scales vs.
best | autotuned, MN-layout vs. best | untuned MN vs CUTLASS (best
layout) | untuned MN vs CuTe-DSL | untuned MN vs TRT-LLM |
|---|---|---|---|---|---|---|
| 1 | 1.08 | 0.94 | 0.94 | 0.97 | - | 1.00 |
| 4 | 1.13 | 0.96 | 0.96 | 1.00 | 1.23 | 1.02 |
| 16 | 1.13 | 0.94 | 0.92 | 0.99 | 1.21 | 1.02 |
| 64 | 1.07 | 1.07 | 1.07 | 1.50 | 1.07 | 1.33 |
| 128 | 0.86 | 1.14 | 1.20 | 1.53 | 1.19 | 1.86 |
| 256 | 0.87 | 1.17 | 1.19 | 1.49 | 1.17 | 2.41 |
| 1024 | 0.91 | 1.08 | 1.08 | 1.23 | 1.07 | 2.86 |
| 4096 | 1.01 | 1.12 | 1.12 | 1.25 | 1.10 | 4.36 |
| 8192 | 1.12 | 1.20 | 1.21 | 1.37 | 1.18 | 5.03 |
| 16384 | 1.22 | 1.29 | 1.29 | 1.46 | 1.28 | 5.37 |
| **decode (M <= 16)** | 1.11 | 0.95 | 0.94 | 0.99 | 1.22 | 1.01 |
| **mid (64 .. 256)** | 0.93 | 1.13 | 1.15 | 1.50 | 1.14 | 1.81 |
| **prefill (M >= 1024)** | 1.06 | 1.17 | 1.17 | 1.32 | 1.16 | 4.29 |
| **all 80 points** | 1.03 | 1.08 | 1.09 | 1.26 | 1.17 | 2.15 |

**B200 (sm_100, 148 SMs, 1830 MHz)**, no CuTe-DSL groupwise backend on
sm_100:

| M | untuned, K-layout scales vs. best | untuned, MN-layout scales vs.
best | autotuned, MN-layout vs. best | untuned MN vs CUTLASS (best
layout) | untuned MN vs TRT-LLM |
|---|---|---|---|---|---|
| 1 | 0.93 | 0.90 | 0.95 | 1.00 | 0.94 |
| 4 | 0.98 | 0.95 | 0.97 | 1.06 | 0.98 |
| 16 | 0.97 | 0.96 | 0.97 | 1.07 | 1.00 |
| 64 | 1.13 | 1.14 | 1.15 | 1.41 | 1.30 |
| 128 | 0.96 | 1.19 | 1.23 | 1.36 | 1.76 |
| 256 | 0.91 | 1.14 | 1.18 | 1.26 | 2.37 |
| 1024 | 1.13 | 1.30 | 1.29 | 1.30 | 3.67 |
| 4096 | 1.15 | 1.22 | 1.19 | 1.22 | 3.91 |
| 8192 | 1.14 | 1.20 | 1.24 | 1.20 | 4.08 |
| 16384 | 1.28 | 1.31 | 1.31 | 1.31 | 4.64 |
| **decode (M <= 16)** | 0.96 | 0.94 | 0.97 | 1.04 | 0.98 |
| **mid (64 .. 256)** | 1.00 | 1.16 | 1.18 | 1.34 | 1.76 |
| **prefill (M >= 1024)** | 1.17 | 1.26 | 1.26 | 1.26 | 4.06 |
| **all 80 points** | 1.05 | 1.12 | 1.14 | 1.21 | 2.06 |

## 🔍 Related Issues

<!-- Link any related issues here -->
#9009


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
* Added batch-invariant execution for groupwise FP8 GEMM with block
scaling, supporting K- and MN-layout scales and BF16 or FP16 outputs.
* Added configuration selection and tuning for this mode, including
support for eligible zero-row inputs and supported GPU architectures.
* Added support for blockwise reduction in a fixed order, with scale
handling and output conversion for the new mode.

* **Tests**
* Added checks for bitwise consistency across supported configurations
and scale layouts, plus determinism, graph replay, and input validation.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [4213769](https://github.com/flashinfer-ai/flashinfer/commit/421376900dd09250800955d26965dd4f80fc037f)

- **作者**: tlysanhuo
- **时间**: 2026-11-10T01:09:57Z
- **提交信息**: fix(sampling): serialize shared generator RNG reservations (#9148)

<!-- .github/pull_request_template.md -->

## 📌 Description

Concurrent sampling calls sharing a CUDA Generator can read the same
Philox offset and overwrite each other's advancement. This reuses RNG
ranges even though each call individually advances the generator.

Serialize the existing read/reserve/write sequence in
`get_seed_and_offset()` with a process-local lock. Preserve the
current-range return value and four-offset alignment. The single lock
avoids retaining caller-owned generators in a lock cache; it also
serializes reservations from independent generators. Explicit
seed/offset paths and CUDA kernels are unchanged.

This coordinates FlashInfer reservations only. It does not synchronize
unrelated PyTorch operations that mutate the same generator, or make
thread scheduling deterministic. The API guide and helper docstring
document that mixed use requires caller serialization or separate
generators.

## 🔍 Related Issues

Found and reproduced against `15482962a1f607944dc412f56523afadbbc72507`.
Related: #5651 fixes sequential offset reservation; this preserves that
behavior and addresses concurrent reservations. #3506 concerns PyTorch
scalar conversion, and #2345 concerns per-request device RNG state.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

All applicable hooks passed for the changed files, including mypy and
Ruff. The repository-wide `--all-files` check was not run.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All targeted tests listed below are passing.
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: targeted sampling coverage is sufficient for this host-side
critical section.

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/utils/test_sampling.py
tests/utils/test_sampling_rng_threaded.py`

Validation on one H100 80GB, Python 3.12.16, PyTorch 2.14.0+cu130, CUDA
toolkit 13.0.88 (driver 535.230.02 with NVIDIA CUDA 13
forward-compatibility library 580.196.07):

```bash
pytest tests/utils/test_sampling_rng_threaded.py tests/utils/test_sampling.py \
  -k 'threaded or cuda_graph_replay or get_seed_and_offset' -q
```

Result: **22 passed, 2853 deselected** at
`a90667127aae5f7d38bf2f0e30feef81e291aa6a`. The subsequent documentation
update changes no executable statements (verified by AST comparison),
and its changed-file pre-commit checks pass.

- Six public samplers × explicit/default Generator: four host threads,
separate CUDA streams, 32 calls/thread. Check non-overlapping contiguous
reservations, final offset, and every real GPU output against an exact
explicit-seed/offset replay.
- Six CUDA Graph tests replay device seed/offset tensors at offsets 0,
128 and 4096 and compare against eager GPU results.
- Mixed-size reservation stress plus existing sequential offset
regressions.
- Negative control importing the unmodified base `sampling.py`: **12
threaded kernel tests failed, 6 graph tests passed**. The two helper
concurrency tests also fail on base and pass with the fix.

The complete sampling parameter matrix, multi-GPU configurations and
remote CI have not been run.

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

AI assistance: Codex helped with implementation, regression tests, local
review and this description. The new lock covers host RNG reservation
only, not kernel execution. A separate host-helper timing check on H100
/ PyTorch 2.9.0+cu128 measured a median 17.69 → 18.28 μs per serial
reservation (7 × 2,000 calls after 200 warmups); this is a correctness
fix, with no throughput improvement claim.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Concurrent sampling calls now reserve distinct, non-overlapping
random-number ranges, keeping generator offsets consistent across
threaded calls and CUDA graph replay.
* **Documentation**
* Clarified that reservations are serialized across host threads, but
not with PyTorch RNG operations or other changes to the same generator.
Callers sharing a generator should coordinate both sides with a common
lock or use separate generators.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: tly <2200895168@qq.com>

### [07e6330](https://github.com/flashinfer-ai/flashinfer/commit/07e633047c06f9ca1f5f04f87cd59e82e423165a)

- **作者**: nvamyt
- **时间**: 2026-11-10T01:09:17Z
- **提交信息**: test(cake_ssd_combined): mock program loading in the Rubin twins sour… (#8297)

## 📌 Description

The Rubin CPU-only source tests mock `_launch_program` but not
`_load_generated_program`, so `run()` can still reach nvcc. On runners
whose nvcc does not know sm_107a they fail:
```text
    nvcc fatal   : Unsupported gpu architecture 'sm_107a'
```

This PR mocks `_load_generated_program` in `_rubin()` of all four files
(`twins`, `single_sequence`, `batched_tail`, `claim`).

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

## 🔍 Related Issues
Fixes #8296
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

- [ ] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).
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

* **Tests**
* Source-level tests for Rubin CPU operations now run without loading
generated programs or invoking compilation through `nvcc`. This applies
to combined, batched-tail, claim, and single-sequence test cases,
reducing reliance on generated artifacts and compiler availability
during these test runs.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Sonnet 5.5 <noreply@anthropic.com>

### [9d8848f](https://github.com/flashinfer-ai/flashinfer/commit/9d8848fc3efdb6805ebf34f313f95f2bab3c0e09)

- **作者**: wuyaole
- **时间**: 2026-11-10T01:08:24Z
- **提交信息**: fix(quantization): reject unsupported CUDA MXFP8 devices (#7986)

<!-- .github/pull_request_template.md -->

## 📌 Description

`mxfp8_quantize(..., backend="cuda")` currently reaches the SM100 JIT
module on older CUDA devices too. Check the input device's compute
capability before PDL detection or module loading and raise
`RuntimeError` below SM100, matching the other SM100-only entry points.
CPU inputs keep their existing host path, and CuTe-DSL dispatch is
unchanged.

Add public-API dispatch tests for unsupported devices,
SM100/SM103/SM120, and CPU inputs. The FakeTensor negative cases verify
that unsupported devices never reach the JIT loader. An additional
unmocked case allocates a real CUDA tensor and checks the public API's
rejection when the current device is older than SM100.

## 🔍 Related Issues

Related to #7980 (CUDA MXFP8 dispatch only; FP4 recipes and native
launch-error checks are separate).

This is the execution-entry guard in the [related serving
work](https://github.com/sgl-project/sglang/issues/48626): #8793 offers
optional caller preflight, while this PR still validates the actual
MXFP8 call boundary. #8480 separately handles immediate native
setup/launch failures. These independently useful checks are related to
[MLA reuse RFC
#8795](https://github.com/flashinfer-ai/flashinfer/issues/8795), but are
not prerequisites for its BF16 value/gate primitive.

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

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/utils/test_mxfp8_dispatch.py
tests/utils/test_fp8_quantize.py`

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

Review closure at `6385f7a7`: the two inline requests are
implemented—the shared error is `RuntimeError`, and
`test_mxfp8_quantize_rejects_unsupported_real_cuda` remains unmocked for
pre-SM100 hardware. Current-head pre-commit, public API and docs checks
passed. PR Test run 41992517063 stops at unauthorized-PR reporting with
Setup/GPU skipped; the maintainer-requested native targets still have no
current-head completion receipt. The earlier hardware report is scoped
to its recorded source, not this revision.

Both the public quantizer and the exported SM100 module entry point now
use the same input-device capability check. The public path rejects
unsupported CUDA inputs before PDL/JIT loading. Direct calls to the
module quantizer reject them before PDL, output allocation and native
invocation; requesting the module factory itself can still build/load it
before any input is supplied. CPU host dispatch, CuTe-DSL and main's
batch-invariant routing are unchanged.

Normal-package dispatch checks pass: 16 CPU/FakeTensor cases and one
real-CUDA case skipped on this Mac. The direct-entry regressions
exercise the real exported factory's uncached implementation with a
mocked native binding, avoiding pollution of the global module cache.
Before the change, both pre-SM100 controls failed because no error was
raised; the fixed path rejects both, while supported-CUDA and CPU-host
controls retain their dispatch. These are control-flow checks, not
native quantization results. The existing unmocked pre-SM100 test
remains unchanged. Scoped mypy, Ruff, formatting and commit hooks pass;
independent source review found no actionable introduced issue.

The [last observed pre-merge public PR
Test](https://github.com/flashinfer-ai/flashinfer/actions/runs/41680020791)
passed six AOT build/import jobs but scheduled no GPU unit jobs. The
later merge's public Setup/GPU matrix was skipped. The maintainer's
latest internal scoped command had no new public pipeline receipt or
completion result in the inspected discussion. Neither a command nor AOT
import success establishes native GPU acceptance.

Still needed on the updated branch: the real-CUDA rejection case on a
pre-SM100 device, plus the maintainer-requested FP8 quantization and
fused-MoE targets on supported hardware. No local GPU, native numerical
or performance result is claimed.

Prepared with Codex assistance.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* CUDA MXFP8 quantization now reports an error on GPUs older than SM100
instead of attempting an unsupported operation.
* Supported GPUs use the appropriate quantization path, while CPU inputs
use the host path without requiring CUDA capability checks.
  * Unsupported GPU errors are reported before quantization begins.

* **Documentation**
* Clarified supported input types and hardware requirements for CUDA and
CPU host execution, including behavior on unsupported GPUs.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: wuyaole <112309453+LeslieWylie@users.noreply.github.com>
Co-authored-by: wuyaole <112309453+LeslieWylie@users.noreply.github.com>

### [a991a2b](https://github.com/flashinfer-ai/flashinfer/commit/a991a2b2e505fbbe92c27ddface0f01965a3a0e8)

- **作者**: Wookje Han
- **时间**: 2026-11-10T00:49:06Z
- **提交信息**: feat(gemm): Lamport peer-store epilogue for the low-M BF16 GEMMs (#8945)

<!-- .github/pull_request_template.md -->

## 📌 Description

Adds a **Lamport peer-store epilogue** to the low-M BF16 GEMMs (warp
split-K, cluster split-K, CuTe DSL TGV). The GEMM
stores its tile straight into every rank's Lamport buffers (unicast
`peer_ptrs` or `multimem.st` multicast), so the
downstream all-reduce / all-gather skips its own copy and only polls and
reduces, overlapping the GEMM tail.

- **API:**
`run_{warp_splitk_dense,splitk_dense,tgv_cute_ext}_peer_store` take the
plain runner's arguments plus a
destination config (`make_lamport_peer_store_config`); `out` only fixes
the shape and is not written.
- **Protocol** (full contract in the `LamportPeerStoreConfig`
docstring):
- two halves selected by `epoch & 1`, read after the grid-dependency
wait;
- a `"broadcast"` (all-reduce) and a `"gather"` (all-gather) slot
layout;
- an all-zero 32-bit word is stored as `0x00008000`, as in the existing
Lamport all-reduce.
- **PDL:** a pre-pushed consumer reads the epoch at launch, so in
peer-store mode cluster split-K and TGV release
dependents from the B loader, after its wait, instead of from the A
loader. **Without a peer-store config, nothing changes.**
- **Epilogue:** cluster split-K and TGV share `store_tile_to_peers`
(stmatrix into A's first stage, swizzled
read-back so each warp stores whole rows, stores predicated against M
and N). Warp split-K stores one reduced 16 B
  chunk per lane. All require bf16, 2D inputs, no bias and `N % 8 == 0`.

**Boundary time per layer** (SM107, Muse Spark decode with DFlash in
SGLang:

| TP | concurrency | o_proj -> all-reduce | pooler -> all-gather |
unpooler -> all-gather |
|---|---|---|---|---|
| 4 | 1 | 9.73 -> 8.32 us (-14.5%) | 7.65 -> 6.79 us (-11.2%) | 6.91 ->
5.44 us (-21.3%) |
| 4 | 2 | 11.20 -> 10.66 us (-4.8%) | 8.06 -> 6.82 us (-15.4%) | - |
| 4 | 4 | 12.16 -> 9.92 us (-18.4%) | 8.35 -> 7.17 us (-14.1%) | - |
| 8 | 1 | 9.12 -> 7.46 us (-18.2%) | 7.01 -> 6.27 us (-10.6%) | 6.56 ->
5.50 us (-16.2%) |
| 8 | 2 | 12.19 -> 9.18 us (-24.7%) | 7.01 -> 6.18 us (-11.8%) | - |
| 8 | 4 | (two-shot, not pushed) | 7.84 -> 6.75 us (-13.9%) | - |

Peer-store is used where the consumer is a one-shot collective; at
higher concurrency the producer or the
consumer takes a path that does not use it, and those boundaries are
unchanged. "-" marks a boundary that
does not exist at that batch size.

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
reviewers may adjust): `tests/gemm/test_bf16_gemm_peer_store.py
tests/gemm/test_mm_bf16_cute_dsl_splitk_sync.py
tests/gemm/test_mm_bf16.py tests/gemm/test_bmm_bf16.py`

New `tests/gemm/test_bf16_gemm_peer_store.py`: all three kernels, both
layouts, world sizes 2/4/8, both halves, zero
words, a partial feature tile / 2-CTA grid past N, and bad-argument
rejection; every byte outside the slot is checked
untouched. Multicast is covered by the SGLang multi-GPU tests. Passing
on SM107.

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

Ordinary GEMMs are unchanged: everything, including the PDL trigger
placement, is compiled out without a peer-store
config.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

## Summary by CodeRabbit

* **New Features**
* Added peer-buffer output options for supported BF16 split-K,
warp-split-K, and TGV GEMM operations, with broadcast and gather
layouts.
* Added epoch-based output placement and validation for peer-buffer
settings, tensor shapes, and output layouts.
* In peer-buffer mode, output is written to peer buffers; the separate
output tensor remains unchanged. Zero values are preserved using the
supported peer-buffer representation.
* **Tests**
* Added coverage for layouts, shapes, epochs, output placement,
unchanged output tensors, and invalid peer-buffer configurations.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [e4ae3bf](https://github.com/flashinfer-ai/flashinfer/commit/e4ae3bfd8aa79184d80c31bbefc681b4e80ff7a2)

- **作者**: eigen
- **时间**: 2026-11-10T00:45:49Z
- **提交信息**: perf(cake_dense_gemm_nondet_train): faster BF16 dense GEMM routes on B200, GB200, GB300 and R200 (#9299)

`flashinfer.cake_dense_gemm_nondet_train` (backend
`flashinfer.experimental.cake.cake_dense_gemm_nondet_train`) is the
nondeterministic Cake training dense GEMM. It has two kernel families.
K1 is the BF16 dense projection GEMM, covering the forward, input
gradient and weight gradient with BF16 operands, FP32 accumulation and
BF16 or FP32 output; it supports strided views, ragged token counts and
batched head projections. K2 is the FP32 router-gate GEMM through
split-BF16x3 tensor-core emulation. Following #9171 and #9194, this PR
adds four K1 programs and changes K1 routes and launch parameters (which
program, or which launch parameters of a plan, a row runs) on B200,
GB200, GB300 and R200; K2 is unchanged. Compared with FlashInfer main
(commit 263127bd), K1 is faster on 81 of 98 measured B200 rows (up to
2.420x), 1 of 6 GB200 rows, 50 of 55 GB300 rows and 60 of 106 R200 rows.
The only slower measured rows are 7 R200 FP32 weight gradients. On those
rows FlashInfer main's program exceeds the accuracy bound of 1.1x the
median FP64 error of the reference implementation (FlashInfer commit
2e989556) over six input kinds.

The other Cake variant of this kernel is the deterministic
`flashinfer.cake_dense_gemm_det_train` (same operations, dtypes and
accuracy budgets, with run-to-run identical bits), and both packages
ship on sm_100a, sm_103a and sm_107a.

**Method.** Times are CUPTI GPU time with a cold L2: 17 groups x 20
steps per arm in one process, with arms in rotated order. Each value is
the median over the groups, and each cell gives eager / CUDA graph.
B200, GB200 and GB300 values are the mean of two GPUs; R200 uses one
GPU. Row labels read `K->N op, output dtype, T=tokens` with BF16
operands. Each table lists the measured rows of the shapes and
token-count windows this PR re-routes on that GPU.

- **vs FlashInfer main** (commit 263127bd), from an A/B run: speedup =
FI main time / PR time of the shown values. The faster / within-noise /
slower verdict compares the median of the per-group ratios with the A/A
noise band. The band runs from the 3rd-lowest to the 3rd-highest of the
17 per-group ratios of an arm against a second copy of itself. A row is
faster when it is beyond the band in both eager and CUDA-graph mode on
every GPU. Each table shows the band and the verdict.
- **vs det Cake and non-Cake**, from a separate read-out run on the same
GPUs. In that run, det Cake (`flashinfer.cake_dense_gemm_det_train` at
commit 263127bd), the non-Cake arms and this PR were timed in the same
groups. Its PR times can differ from the FI main table by up to about
3%, and all ratios in these tables use only that run's numbers. The
read-out run covers 42 of 98 B200 rows, 6 of 6 GB200 rows and 17 of 55
GB300 rows, a subset limited by its time budget; R200 has no read-out
run.
- Speedup vs det Cake = det time / PR time per GPU, averaged over the
GPUs; it differs from dividing the shown values by at most 0.0004.
Speedup vs non-Cake = per GPU, the median over the groups of (fastest
non-Cake arm in that group / PR time), averaged over the GPUs. It can
differ from dividing the shown values by up to 0.016 and is the stricter
measure for Cake.
- Non-Cake candidates are the three fastest arms of an earlier sweep
plus `torch.mm` and cuBLASLt's first heuristic. The arms that appear are
QuACK 0.6.5 (`quack_gemm_parallel`, `quack_gemm_serial`), DeepGEMM 2.8.2
(`deepgemm_bf16_default`, `deepgemm_bf16_det`), cuBLASLt 13.8.0
heuristics (`cublaslt_0`..`cublaslt_3`), `torch_mm`, and FlashInfer mm
backends (`fi_mm_cublaslt`, `fi_mm_auto`, `fi_mm_cudnn`). Each row names
its fastest arm.
- Software: CUDA 13.4 toolkit (nvcc 13.4.92), PyTorch 2.14.1+cu130,
cuBLAS 13.8.0, cuDNN 9.24 (frontend 1.31.0, used by `fi_mm_cudnn`);
drivers 580.82.07 (B200), 580.126.20 (GB200), 580.159.03 (GB300), 620.43
(R200).

**B200** (sm_100a, 148 SMs). Of 98 rows, 81 are faster than FlashInfer
main (1.004-2.420x, median 1.021), 17 are within noise and none are
slower; the largest gain is the BF16 weight gradient 4096 -> 1024 at 961
tokens, 29.39 -> 12.14 us (eager). On the 42 read-out rows, the PR is
1.003-1.354x vs det Cake and 0.959-1.080x vs the fastest non-Cake arm
(ahead in both modes on 31 rows, behind in both on 11).

**B200 (sm_100a, 148 SMs, CUDA 13.4): this PR vs FI main**

| row | FI main Cake (us) | this PR (us) | speedup vs FI main | A/A
noise band | verdict |
|---|---|---|---|---|---|
| 4096→1024 dgrad, BF16 out, T=16172 | 80.84 / 80.73 | 80.39 / 80.34 |
1.006 / 1.005 | 0.003 / 0.003 | faster |
| 4096→1024 dgrad, BF16 out, T=16173 | 80.96 / 80.75 | 80.47 / 80.36 |
1.006 / 1.005 | 0.003 / 0.003 | faster |
| 4096→1024 dgrad, BF16 out, T=16230 | 80.40 / 80.32 | 80.11 / 79.96 |
1.004 / 1.004 | 0.003 / 0.003 | faster |
| 4096→1024 dgrad, BF16 out, T=16231 | 80.58 / 80.46 | 80.22 / 80.08 |
1.004 / 1.005 | 0.004 / 0.003 | faster |
| 4096→1024 dgrad, BF16 out, T=16232 | 80.52 / 80.44 | 80.22 / 80.08 |
1.004 / 1.004 | 0.003 / 0.003 | within noise |
| 4096→1024 dgrad, BF16 out, T=16300 | 80.58 / 80.52 | 80.17 / 80.13 |
1.005 / 1.005 | 0.003 / 0.004 | faster |
| 4096→1024 dgrad, BF16 out, T=16383 | 80.61 / 80.54 | 80.22 / 80.12 |
1.005 / 1.005 | 0.003 / 0.002 | faster |
| 4096→1024 dgrad, BF16 out, T=16384 | 80.80 / 80.72 | 80.39 / 80.31 |
1.005 / 1.005 | 0.004 / 0.004 | within noise |
| 4096→1024 wgrad, BF16 out, T=16100 | 104.40 / 104.34 | 87.00 / 86.97 |
1.200 / 1.200 | 0.003 / 0.002 | faster |
| 4096→1024 wgrad, BF16 out, T=16170 | 117.55 / 117.73 | 87.43 / 87.41 |
1.344 / 1.347 | 0.004 / 0.002 | faster |
| 4096→1024 wgrad, BF16 out, T=16171 | 117.30 / 117.46 | 87.16 / 87.13 |
1.346 / 1.348 | 0.007 / 0.003 | faster |
| 4096→1024 wgrad, BF16 out, T=2048 | 34.74 / 35.02 | 17.57 / 17.79 |
1.978 / 1.969 | 0.005 / 0.004 | faster |
| 4096→1024 wgrad, BF16 out, T=4096 | 44.98 / 45.14 | 27.90 / 28.10 |
1.612 / 1.606 | 0.004 / 0.003 | faster |
| 4096→1024 wgrad, BF16 out, T=8192 | 65.35 / 65.39 | 48.21 / 48.36 |
1.355 / 1.352 | 0.003 / 0.003 | faster |
| 4096→1024 wgrad, BF16 out, T=961 | 29.39 / 29.70 | 12.14 / 12.40 |
2.420 / 2.395 | 0.007 / 0.006 | faster |
| 4096→128 dgrad, BF16 out, T=16172 | 26.68 / 26.82 | 25.79 / 25.88 |
1.034 / 1.036 | 0.007 / 0.006 | faster |
| 4096→128 dgrad, BF16 out, T=16231 | 26.06 / 26.18 | 25.79 / 25.84 |
1.011 / 1.013 | 0.007 / 0.006 | faster |
| 4096→128 dgrad, BF16 out, T=16384 | 26.80 / 27.00 | 25.81 / 25.91 |
1.038 / 1.042 | 0.011 / 0.010 | faster |
| 4096→32 dgrad, BF16 out, T=16172 | 23.30 / 23.47 | 23.02 / 23.17 |
1.012 / 1.013 | 0.007 / 0.007 | faster |
| 4096→32 dgrad, BF16 out, T=16231 | 23.30 / 23.48 | 23.00 / 23.18 |
1.013 / 1.013 | 0.007 / 0.005 | faster |
| 4096→32 dgrad, BF16 out, T=16384 | 23.56 / 23.77 | 23.20 / 23.41 |
1.016 / 1.015 | 0.008 / 0.008 | faster |
| 4096→48 dgrad, BF16 out, T=16172 | 24.20 / 24.37 | 23.33 / 23.49 |
1.037 / 1.037 | 0.005 / 0.007 | faster |
| 4096→48 dgrad, BF16 out, T=16231 | 23.67 / 23.87 | 23.37 / 23.52 |
1.013 / 1.014 | 0.006 / 0.005 | faster |
| 4096→48 dgrad, BF16 out, T=16384 | 24.52 / 24.69 | 23.55 / 23.67 |
1.041 / 1.043 | 0.006 / 0.005 | faster |
| 4096→512 dgrad, BF16 out, T=16172 | 47.53 / 47.66 | 46.83 / 46.89 |
1.015 / 1.016 | 0.005 / 0.006 | faster |
| 4096→512 dgrad, BF16 out, T=16173 | 47.50 / 47.64 | 46.89 / 47.02 |
1.013 / 1.013 | 0.004 / 0.005 | faster |
| 4096→512 dgrad, BF16 out, T=16230 | 47.51 / 47.70 | 46.83 / 46.93 |
1.015 / 1.016 | 0.004 / 0.004 | faster |
| 4096→512 dgrad, BF16 out, T=16231 | 47.47 / 47.61 | 46.75 / 46.80 |
1.015 / 1.017 | 0.004 / 0.003 | faster |
| 4096→512 dgrad, BF16 out, T=16232 | 47.63 / 47.84 | 46.89 / 46.96 |
1.016 / 1.019 | 0.004 / 0.004 | faster |
| 4096→512 dgrad, BF16 out, T=16300 | 47.58 / 47.67 | 46.91 / 47.04 |
1.014 / 1.013 | 0.004 / 0.003 | faster |
| 4096→512 dgrad, BF16 out, T=16383 | 47.72 / 47.94 | 46.93 / 47.05 |
1.017 / 1.019 | 0.008 / 0.008 | faster |
| 4096→512 dgrad, BF16 out, T=16384 | 47.78 / 47.87 | 47.16 / 47.27 |
1.013 / 1.013 | 0.005 / 0.004 | faster |
| 4096→512 dgrad, FP32 out, T=16172 | 65.42 / 65.47 | 62.58 / 62.60 |
1.046 / 1.046 | 0.006 / 0.007 | faster |
| 4096→512 dgrad, FP32 out, T=16173 | 66.45 / 66.55 | 62.63 / 62.77 |
1.061 / 1.060 | 0.005 / 0.004 | faster |
| 4096→512 dgrad, FP32 out, T=16230 | 66.75 / 66.87 | 62.85 / 62.95 |
1.062 / 1.062 | 0.004 / 0.005 | faster |
| 4096→512 dgrad, FP32 out, T=16232 | 66.37 / 66.46 | 62.81 / 62.91 |
1.057 / 1.056 | 0.007 / 0.005 | faster |
| 4096→512 dgrad, FP32 out, T=16300 | 66.72 / 66.81 | 63.00 / 63.09 |
1.059 / 1.059 | 0.005 / 0.004 | faster |
| 4096→512 dgrad, FP32 out, T=16383 | 66.78 / 66.87 | 63.07 / 63.25 |
1.059 / 1.057 | 0.005 / 0.005 | faster |
| 4096→512 dgrad, FP32 out, T=16384 | 65.73 / 65.83 | 62.86 / 63.00 |
1.046 / 1.045 | 0.005 / 0.005 | faster |
| 4096→512 fwd, BF16 out, T=16172 | 44.53 / 44.55 | 44.42 / 44.48 |
1.002 / 1.001 | 0.003 / 0.004 | within noise |
| 4096→512 fwd, BF16 out, T=16231 | 44.77 / 44.77 | 44.56 / 44.66 |
1.005 / 1.003 | 0.003 / 0.004 | within noise |
| 5120→1024 dgrad, BF16 out, T=16172 | 100.55 / 100.81 | 99.96 / 100.24
| 1.006 / 1.006 | 0.005 / 0.003 | faster |
| 5120→1024 dgrad, BF16 out, T=16173 | 100.39 / 100.74 | 99.80 / 100.12
| 1.006 / 1.006 | 0.003 / 0.004 | faster |
| 5120→1024 dgrad, BF16 out, T=16230 | 100.71 / 101.07 | 100.13 / 100.50
| 1.006 / 1.006 | 0.002 / 0.003 | faster |
| 5120→1024 dgrad, BF16 out, T=16231 | 100.30 / 100.62 | 99.84 / 100.04
| 1.005 / 1.006 | 0.005 / 0.004 | within noise |
| 5120→1024 dgrad, BF16 out, T=16232 | 100.73 / 101.05 | 100.19 / 100.34
| 1.005 / 1.007 | 0.004 / 0.004 | faster |
| 5120→1024 dgrad, BF16 out, T=16300 | 100.66 / 100.96 | 100.04 / 100.26
| 1.006 / 1.007 | 0.006 / 0.004 | within noise |
| 5120→1024 dgrad, BF16 out, T=16383 | 100.97 / 101.33 | 100.36 / 100.62
| 1.006 / 1.007 | 0.004 / 0.003 | faster |
| 5120→1024 dgrad, BF16 out, T=16384 | 100.85 / 101.27 | 100.16 / 100.39
| 1.007 / 1.009 | 0.009 / 0.014 | within noise |
| 5120→128 dgrad, BF16 out, T=16172 | 32.58 / 32.80 | 31.80 / 31.91 |
1.024 / 1.028 | 0.005 / 0.005 | faster |
| 5120→128 dgrad, BF16 out, T=16384 | 32.76 / 32.91 | 31.95 / 32.06 |
1.025 / 1.026 | 0.005 / 0.004 | faster |
| 5120→32 dgrad, BF16 out, T=16172 | 29.21 / 29.41 | 28.54 / 28.68 |
1.024 / 1.026 | 0.007 / 0.008 | faster |
| 5120→32 dgrad, BF16 out, T=16231 | 28.76 / 28.93 | 28.52 / 28.69 |
1.008 / 1.008 | 0.006 / 0.005 | faster |
| 5120→32 dgrad, BF16 out, T=16384 | 29.45 / 29.66 | 28.72 / 28.89 |
1.026 / 1.027 | 0.010 / 0.008 | faster |
| 5120→48 dgrad, BF16 out, T=16172 | 29.70 / 29.90 | 28.98 / 29.21 |
1.025 / 1.024 | 0.006 / 0.008 | faster |
| 5120→48 dgrad, BF16 out, T=16384 | 29.73 / 29.91 | 29.06 / 29.28 |
1.023 / 1.021 | 0.005 / 0.007 | faster |
| 5120→512 dgrad, BF16 out, T=16172 | 58.56 / 58.95 | 57.61 / 57.76 |
1.017 / 1.020 | 0.003 / 0.004 | faster |
| 5120→512 dgrad, BF16 out, T=16173 | 58.55 / 58.97 | 57.62 / 57.88 |
1.016 / 1.019 | 0.004 / 0.005 | faster |
| 5120→512 dgrad, BF16 out, T=16230 | 58.64 / 59.03 | 57.66 / 57.83 |
1.017 / 1.021 | 0.006 / 0.005 | faster |
| 5120→512 dgrad, BF16 out, T=16231 | 58.48 / 58.89 | 57.56 / 57.72 |
1.016 / 1.020 | 0.005 / 0.004 | faster |
| 5120→512 dgrad, BF16 out, T=16232 | 58.45 / 58.80 | 57.59 / 57.95 |
1.015 / 1.015 | 0.003 / 0.005 | faster |
| 5120→512 dgrad, BF16 out, T=16300 | 58.52 / 58.78 | 57.48 / 57.60 |
1.018 / 1.021 | 0.007 / 0.008 | faster |
| 5120→512 dgrad, BF16 out, T=16383 | 58.53 / 58.92 | 57.50 / 57.69 |
1.018 / 1.021 | 0.004 / 0.006 | faster |
| 5120→512 dgrad, BF16 out, T=16384 | 58.51 / 58.90 | 57.67 / 57.97 |
1.015 / 1.016 | 0.005 / 0.005 | faster |
| 5120→512 dgrad, FP32 out, T=16172 | 81.12 / 81.12 | 77.28 / 77.31 |
1.050 / 1.049 | 0.009 / 0.006 | faster |
| 5120→512 dgrad, FP32 out, T=16173 | 83.19 / 83.30 | 77.34 / 77.31 |
1.076 / 1.077 | 0.004 / 0.004 | faster |
| 5120→512 dgrad, FP32 out, T=16230 | 83.50 / 83.69 | 77.71 / 77.76 |
1.075 / 1.076 | 0.004 / 0.004 | faster |
| 5120→512 dgrad, FP32 out, T=16232 | 83.52 / 83.66 | 77.78 / 77.78 |
1.074 / 1.076 | 0.005 / 0.004 | faster |
| 5120→512 dgrad, FP32 out, T=16300 | 83.40 / 83.53 | 77.97 / 77.99 |
1.070 / 1.071 | 0.004 / 0.003 | faster |
| 5120→512 dgrad, FP32 out, T=16383 | 83.77 / 83.94 | 78.06 / 78.12 |
1.073 / 1.075 | 0.004 / 0.004 | faster |
| 5120→512 dgrad, FP32 out, T=16384 | 81.72 / 81.66 | 78.09 / 78.16 |
1.046 / 1.045 | 0.008 / 0.009 | faster |
| 5120→512 fwd, BF16 out, T=16172 | 53.61 / 53.57 | 53.37 / 53.46 |
1.005 / 1.002 | 0.004 / 0.004 | within noise |
| 5120→512 fwd, BF16 out, T=16231 | 53.86 / 53.70 | 53.58 / 53.61 |
1.005 / 1.002 | 0.004 / 0.003 | within noise |
| 5120→64 dgrad, BF16 out, T=16172 | 29.38 / 29.51 | 28.90 / 29.01 |
1.016 / 1.017 | 0.016 / 0.014 | faster |
| 5120→64 dgrad, BF16 out, T=16384 | 29.05 / 29.18 | 28.44 / 28.67 |
1.022 / 1.018 | 0.022 / 0.020 | within noise |
| 6144→128 dgrad, BF16 out, T=16172 | 38.02 / 38.09 | 37.17 / 37.23 |
1.023 / 1.023 | 0.005 / 0.006 | faster |
| 6144→128 dgrad, BF16 out, T=16231 | 37.37 / 37.45 | 37.22 / 37.34 |
1.004 / 1.003 | 0.006 / 0.007 | within noise |
| 6144→128 dgrad, BF16 out, T=16384 | 38.11 / 38.25 | 37.34 / 37.41 |
1.021 / 1.022 | 0.004 / 0.005 | faster |
| 6144→32 dgrad, BF16 out, T=16172 | 34.16 / 34.36 | 33.52 / 33.77 |
1.019 / 1.018 | 0.005 / 0.004 | faster |
| 6144→32 dgrad, BF16 out, T=16231 | 33.61 / 33.83 | 33.50 / 33.73 |
1.003 / 1.003 | 0.005 / 0.005 | within noise |
| 6144→32 dgrad, BF16 out, T=16384 | 34.45 / 34.69 | 33.67 / 33.89 |
1.023 / 1.024 | 0.004 / 0.005 | faster |
| 6144→576 dgrad, BF16 out, T=16172 | 72.72 / 72.73 | 72.41 / 72.47 |
1.004 / 1.004 | 0.004 / 0.005 | within noise |
| 6144→576 dgrad, BF16 out, T=16173 | 72.87 / 72.88 | 72.37 / 72.44 |
1.007 / 1.006 | 0.005 / 0.006 | faster |
| 6144→576 dgrad, BF16 out, T=16230 | 72.91 / 72.96 | 72.73 / 72.80 |
1.002 / 1.002 | 0.005 / 0.005 | within noise |
| 6144→576 dgrad, BF16 out, T=16231 | 72.85 / 72.86 | 72.59 / 72.59 |
1.004 / 1.004 | 0.004 / 0.004 | faster |
| 6144→576 dgrad, BF16 out, T=16232 | 72.81 / 72.90 | 72.62 / 72.59 |
1.002 / 1.004 | 0.004 / 0.004 | within noise |
| 6144→576 dgrad, BF16 out, T=16300 | 72.82 / 72.84 | 72.48 / 72.53 |
1.005 / 1.004 | 0.004 / 0.004 | within noise |
| 6144→576 dgrad, BF16 out, T=16383 | 73.18 / 73.22 | 72.80 / 72.86 |
1.005 / 1.005 | 0.003 / 0.004 | faster |
| 6144→576 dgrad, BF16 out, T=16384 | 73.10 / 73.12 | 72.78 / 72.81 |
1.004 / 1.004 | 0.003 / 0.004 | within noise |
| 6144→576 dgrad, FP32 out, T=16172 | 102.51 / 102.67 | 98.03 / 98.21 |
1.046 / 1.045 | 0.009 / 0.009 | faster |
| 6144→576 dgrad, FP32 out, T=16173 | 102.73 / 102.85 | 98.75 / 99.02 |
1.040 / 1.039 | 0.011 / 0.009 | faster |
| 6144→576 dgrad, FP32 out, T=16230 | 102.73 / 102.83 | 97.89 / 97.89 |
1.050 / 1.050 | 0.006 / 0.016 | faster |
| 6144→576 dgrad, FP32 out, T=16232 | 102.91 / 103.00 | 99.67 / 99.78 |
1.032 / 1.032 | 0.007 / 0.007 | faster |
| 6144→576 dgrad, FP32 out, T=16300 | 102.68 / 102.82 | 98.38 / 98.65 |
1.044 / 1.042 | 0.008 / 0.007 | faster |
| 6144→576 dgrad, FP32 out, T=16383 | 102.97 / 103.04 | 99.42 / 99.55 |
1.036 / 1.035 | 0.007 / 0.009 | faster |
| 6144→576 dgrad, FP32 out, T=16384 | 102.75 / 102.87 | 97.88 / 98.22 |
1.050 / 1.047 | 0.010 / 0.006 | faster |
| 8192→128 dgrad, BF16 out, T=16172 | 48.47 / 48.55 | 47.67 / 47.73 |
1.017 / 1.017 | 0.004 / 0.004 | faster |
| 8192→128 dgrad, BF16 out, T=16384 | 48.73 / 48.83 | 47.88 / 47.90 |
1.018 / 1.020 | 0.005 / 0.005 | faster |

**B200 (sm_100a, 148 SMs, CUDA 13.4): this PR vs deterministic Cake and
the fastest non-Cake implementation (read-out run)**

| row | det Cake (us) | fastest non-Cake (us) | this PR (us) | speedup
vs det Cake | speedup vs non-Cake |
|---|---|---|---|---|---|
| 4096→1024 dgrad, BF16 out, T=16231 | 80.31 / 80.16 | 78.74 / 78.72
(torch_mm, deepgemm_bf16_default) | 79.98 / 79.82 | 1.004 / 1.004 |
0.983 / 0.986 |
| 4096→1024 wgrad, BF16 out, T=8192 | 65.47 / 65.50 | 46.50 / 46.58
(torch_mm, deepgemm_bf16_default, cublaslt_0) | 48.34 / 48.43 | 1.354 /
1.352 | 0.960 / 0.959 |
| 4096→128 dgrad, BF16 out, T=16172 | 27.02 / 27.27 | 26.38 / 26.58
(quack_gemm_serial) | 25.68 / 25.85 | 1.052 / 1.055 | 1.027 / 1.028 |
| 4096→128 dgrad, BF16 out, T=16231 | 27.06 / 27.28 | 27.18 / 27.28
(quack_gemm_parallel, quack_gemm_serial, cublaslt_0) | 25.70 / 25.78 |
1.053 / 1.058 | 1.057 / 1.056 |
| 4096→128 dgrad, BF16 out, T=16384 | 27.32 / 27.52 | 27.34 / 27.36
(torch_mm, deepgemm_bf16_default, cublaslt_0) | 25.78 / 25.86 | 1.060 /
1.064 | 1.058 / 1.055 |
| 4096→32 dgrad, BF16 out, T=16172 | 25.12 / 25.31 | 23.70 / 23.89
(quack_gemm_parallel) | 23.01 / 23.13 | 1.092 / 1.095 | 1.029 / 1.032 |
| 4096→32 dgrad, BF16 out, T=16231 | 25.11 / 25.33 | 23.70 / 23.89
(quack_gemm_parallel) | 23.09 / 23.22 | 1.088 / 1.091 | 1.026 / 1.029 |
| 4096→48 dgrad, BF16 out, T=16172 | 25.50 / 25.74 | 23.95 / 24.12
(quack_gemm_parallel, quack_gemm_serial) | 23.36 / 23.53 | 1.092 / 1.094
| 1.025 / 1.026 |
| 4096→48 dgrad, BF16 out, T=16231 | 24.26 / 24.46 | 23.99 / 24.14
(quack_gemm_parallel) | 23.43 / 23.59 | 1.036 / 1.037 | 1.023 / 1.023 |
| 4096→512 dgrad, BF16 out, T=16172 | 47.67 / 47.83 | 45.70 / 45.78
(cublaslt_0, deepgemm_bf16_default, torch_mm) | 47.07 / 47.14 | 1.013 /
1.015 | 0.970 / 0.970 |
| 4096→512 dgrad, BF16 out, T=16231 | 47.57 / 47.66 | 45.71 / 45.78
(deepgemm_bf16_default, cublaslt_0) | 46.90 / 47.02 | 1.014 / 1.014 |
0.974 / 0.973 |
| 4096→512 dgrad, BF16 out, T=16384 | 47.35 / 47.50 | 45.78 / 45.84
(cublaslt_0, torch_mm) | 46.82 / 46.95 | 1.011 / 1.012 | 0.977 / 0.975 |
| 4096→512 dgrad, FP32 out, T=16172 | 66.65 / 66.70 | 63.72 / 63.82
(quack_gemm_parallel, quack_gemm_serial) | 62.70 / 62.78 | 1.063 / 1.062
| 1.016 / 1.016 |
| 4096→512 dgrad, FP32 out, T=16300 | 66.35 / 66.37 | 63.98 / 64.10
(quack_gemm_parallel) | 62.82 / 62.87 | 1.056 / 1.056 | 1.019 / 1.019 |
| 4096→512 fwd, BF16 out, T=16231 | 51.93 / 52.30 | 46.65 / 46.63
(cublaslt_3, fi_mm_cublaslt) | 44.50 / 44.54 | 1.167 / 1.174 | 1.048 /
1.046 |
| 5120→1024 dgrad, BF16 out, T=16231 | 100.10 / 100.49 | 97.85 / 97.81
(cublaslt_1, cublaslt_0, deepgemm_bf16_default) | 99.71 / 99.93 | 1.004
/ 1.006 | 0.980 / 0.978 |
| 5120→128 dgrad, BF16 out, T=16172 | 32.97 / 33.19 | 33.46 / 33.66
(quack_gemm_serial, cublaslt_2) | 31.79 / 31.94 | 1.037 / 1.039 | 1.053
/ 1.054 |
| 5120→128 dgrad, BF16 out, T=16384 | 32.90 / 33.16 | 33.54 / 33.68
(quack_gemm_parallel, cublaslt_0) | 31.76 / 31.96 | 1.036 / 1.038 |
1.054 / 1.052 |
| 5120→32 dgrad, BF16 out, T=16172 | 30.66 / 30.81 | 30.73 / 30.86
(cublaslt_2) | 28.46 / 28.60 | 1.077 / 1.077 | 1.080 / 1.079 |
| 5120→32 dgrad, BF16 out, T=16231 | 30.65 / 30.89 | 30.09 / 30.27
(quack_gemm_parallel) | 28.41 / 28.51 | 1.079 / 1.083 | 1.059 / 1.061 |
| 5120→32 dgrad, BF16 out, T=16384 | 30.74 / 30.92 | 29.92 / 30.06
(cublaslt_3) | 28.64 / 28.73 | 1.073 / 1.076 | 1.045 / 1.046 |
| 5120→48 dgrad, BF16 out, T=16172 | 31.24 / 31.44 | 30.30 / 30.50
(quack_gemm_serial) | 28.86 / 28.98 | 1.083 / 1.085 | 1.050 / 1.053 |
| 5120→48 dgrad, BF16 out, T=16384 | 31.28 / 31.48 | 30.15 / 30.25
(quack_gemm_parallel, quack_gemm_serial) | 29.17 / 29.32 | 1.072 / 1.074
| 1.031 / 1.031 |
| 5120→512 dgrad, BF16 out, T=16231 | 58.31 / 58.53 | 56.68 / 56.67
(deepgemm_bf16_default, cublaslt_0) | 57.40 / 57.51 | 1.016 / 1.018 |
0.986 / 0.985 |
| 5120→512 dgrad, BF16 out, T=16384 | 58.27 / 58.55 | 56.75 / 56.80
(torch_mm, deepgemm_bf16_default) | 57.40 / 57.57 | 1.015 / 1.017 |
0.989 / 0.986 |
| 5120→512 dgrad, FP32 out, T=16172 | 82.90 / 82.95 | 79.54 / 79.66
(quack_gemm_serial) | 77.22 / 77.30 | 1.073 / 1.073 | 1.030 / 1.030 |
| 5120→512 dgrad, FP32 out, T=16300 | 83.10 / 83.23 | 81.07 / 81.17
(quack_gemm_serial) | 77.98 / 78.05 | 1.066 / 1.066 | 1.040 / 1.040 |
| 5120→512 dgrad, FP32 out, T=16384 | 83.10 / 83.32 | 78.57 / 78.56
(deepgemm_bf16_det) | 77.98 / 78.03 | 1.066 / 1.068 | 1.007 / 1.007 |
| 5120→512 fwd, BF16 out, T=16172 | 63.38 / 62.95 | 55.66 / 55.60
(cublaslt_2, fi_mm_cudnn) | 53.56 / 53.57 | 1.183 / 1.175 | 1.040 /
1.037 |
| 5120→512 fwd, BF16 out, T=16231 | 63.07 / 62.70 | 55.71 / 55.64
(cublaslt_2, fi_mm_auto) | 53.58 / 53.60 | 1.177 / 1.170 | 1.040 / 1.036
|
| 5120→64 dgrad, BF16 out, T=16172 | 29.14 / 29.36 | 29.76 / 29.90
(cublaslt_3) | 28.42 / 28.79 | 1.026 / 1.020 | 1.047 / 1.039 |
| 5120→64 dgrad, BF16 out, T=16384 | 29.74 / 29.88 | 29.73 / 29.94
(cublaslt_1, quack_gemm_serial) | 29.27 / 29.37 | 1.016 / 1.018 | 1.017
/ 1.019 |
| 6144→128 dgrad, BF16 out, T=16231 | 38.29 / 38.47 | 38.34 / 38.48
(quack_gemm_serial, quack_gemm_parallel) | 37.17 / 37.26 | 1.030 / 1.032
| 1.031 / 1.032 |
| 6144→128 dgrad, BF16 out, T=16384 | 38.22 / 38.42 | 38.31 / 38.47
(quack_gemm_serial) | 37.14 / 37.27 | 1.029 / 1.031 | 1.031 / 1.031 |
| 6144→32 dgrad, BF16 out, T=16172 | 36.09 / 36.33 | 34.29 / 34.42
(cublaslt_1, torch_mm) | 33.50 / 33.70 | 1.077 / 1.078 | 1.023 / 1.020 |
| 6144→32 dgrad, BF16 out, T=16231 | 36.10 / 36.33 | 34.34 / 34.46
(cublaslt_1, torch_mm, deepgemm_bf16_default) | 33.51 / 33.70 | 1.077 /
1.078 | 1.024 / 1.022 |
| 6144→576 dgrad, BF16 out, T=16172 | 72.38 / 72.45 | 71.30 / 71.18
(torch_mm) | 72.10 / 72.06 | 1.004 / 1.006 | 0.987 / 0.987 |
| 6144→576 dgrad, BF16 out, T=16231 | 72.33 / 72.28 | 71.18 / 71.18
(deepgemm_bf16_default, torch_mm) | 72.08 / 71.98 | 1.003 / 1.004 |
0.987 / 0.987 |
| 6144→576 dgrad, FP32 out, T=16300 | 101.70 / 101.81 | 99.42 / 99.53
(quack_gemm_serial, quack_gemm_parallel) | 97.17 / 97.26 | 1.047 / 1.047
| 1.023 / 1.023 |
| 6144→576 dgrad, FP32 out, T=16384 | 101.70 / 101.83 | 96.96 / 96.97
(deepgemm_bf16_det) | 97.13 / 97.09 | 1.047 / 1.049 | 0.998 / 0.999 |
| 8192→128 dgrad, BF16 out, T=16172 | 48.86 / 49.02 | 49.62 / 49.78
(quack_gemm_serial) | 47.81 / 47.82 | 1.022 / 1.025 | 1.038 / 1.041 |
| 8192→128 dgrad, BF16 out, T=16384 | 48.96 / 49.18 | 49.11 / 49.27
(quack_gemm_parallel) | 47.93 / 48.04 | 1.022 / 1.024 | 1.025 / 1.026 |

**GB200** (sm_100a, 152 SMs). Of 6 rows, 1 is faster than FlashInfer
main (1.028 / 1.034), 5 are within noise and none are slower. On all 6
read-out rows, the PR is 1.030-1.240x vs det Cake and 0.982-1.048x vs
the fastest non-Cake arm (ahead on 4, behind on 2).

**GB200 (sm_100a, 152 SMs, CUDA 13.4): this PR vs FI main**

| row | FI main Cake (us) | this PR (us) | speedup vs FI main | A/A
noise band | verdict |
|---|---|---|---|---|---|
| 4096→1024 fwd, BF16 out, T=16231 | 94.97 / 93.91 | 92.42 / 90.84 |
1.028 / 1.034 | 0.028 / 0.036 | faster |
| 4096→512 fwd, BF16 out, T=16172 | 46.75 / 45.60 | 46.22 / 44.84 |
1.011 / 1.017 | 0.061 / 0.049 | within noise |
| 4096→512 fwd, BF16 out, T=16231 | 45.95 / 45.14 | 45.00 / 44.37 |
1.021 / 1.017 | 0.020 / 0.024 | within noise |
| 5120→1024 fwd, BF16 out, T=16231 | 116.50 / 113.84 | 112.62 / 110.09 |
1.034 / 1.034 | 0.017 / 0.046 | within noise |
| 5120→512 fwd, BF16 out, T=16172 | 58.47 / 57.55 | 56.72 / 56.31 |
1.031 / 1.022 | 0.029 / 0.036 | within noise |
| 5120→512 fwd, BF16 out, T=16231 | 58.77 / 58.05 | 58.56 / 56.88 |
1.004 / 1.021 | 0.172 / 0.060 | within noise |

**GB200 (sm_100a, 152 SMs, CUDA 13.4): this PR vs deterministic Cake and
the fastest non-Cake implementation (read-out run)**

| row | det Cake (us) | fastest non-Cake (us) | this PR (us) | speedup
vs det Cake | speedup vs non-Cake |
|---|---|---|---|---|---|
| 4096→1024 fwd, BF16 out, T=16231 | 95.27 / 94.46 | 92.01 / 91.22
(cublaslt_1, fi_mm_auto) | 92.06 / 91.21 | 1.035 / 1.036 | 0.998 / 0.985
|
| 4096→512 fwd, BF16 out, T=16172 | 56.20 / 55.86 | 47.70 / 47.35
(cublaslt_1, fi_mm_cublaslt) | 45.64 / 45.03 | 1.231 / 1.240 | 1.042 /
1.048 |
| 4096→512 fwd, BF16 out, T=16231 | 54.70 / 54.72 | 47.80 / 47.25
(cublaslt_2, fi_mm_cudnn) | 45.66 / 45.18 | 1.198 / 1.211 | 1.043 /
1.042 |
| 5120→1024 fwd, BF16 out, T=16231 | 116.90 / 115.04 | 112.65 / 111.23
(cublaslt_1, fi_mm_auto) | 112.86 / 111.74 | 1.036 / 1.030 | 0.996 /
0.982 |
| 5120→512 fwd, BF16 out, T=16172 | 69.26 / 69.90 | 59.16 / 58.19
(cublaslt_1, fi_mm_cublaslt) | 58.49 / 57.22 | 1.184 / 1.222 | 1.005 /
1.009 |
| 5120→512 fwd, BF16 out, T=16231 | 69.68 / 69.76 | 59.07 / 58.20
(cublaslt_2) | 58.06 / 56.88 | 1.200 / 1.226 | 1.011 / 1.016 |

**GB300** (sm_103a, 152 SMs). Of 55 rows, 50 are faster than FlashInfer
main (1.011-1.081x, median 1.044), 5 are within noise and none are
slower. On the 17 read-out rows, the PR is 1.036-1.079x vs det Cake and
0.995-1.072x vs the fastest non-Cake arm (ahead on 15, behind on 2).

**GB300 (sm_103a, 152 SMs, CUDA 13.4): this PR vs FI main**

| row | FI main Cake (us) | this PR (us) | speedup vs FI main | A/A
noise band | verdict |
|---|---|---|---|---|---|
| 4096→1024 fwd, BF16 out, T=16231 | 72.63 / 72.69 | 71.38 / 71.31 |
1.018 / 1.020 | 0.015 / 0.009 | faster |
| 4096→128 dgrad, BF16 out, T=16172 | 24.05 / 24.26 | 23.09 / 23.27 |
1.042 / 1.043 | 0.008 / 0.005 | faster |
| 4096→128 dgrad, BF16 out, T=16231 | 23.77 / 23.89 | 23.20 / 23.37 |
1.024 / 1.022 | 0.006 / 0.008 | faster |
| 4096→128 dgrad, BF16 out, T=16384 | 24.41 / 24.63 | 23.36 / 23.53 |
1.045 / 1.047 | 0.007 / 0.008 | faster |
| 4096→48 dgrad, BF16 out, T=16172 | 22.98 / 23.17 | 21.92 / 22.18 |
1.048 / 1.045 | 0.012 / 0.017 | faster |
| 4096→48 dgrad, BF16 out, T=16384 | 23.23 / 23.38 | 22.37 / 22.66 |
1.038 / 1.032 | 0.013 / 0.013 | faster |
| 4096→512 dgrad, FP32 out, T=16172 | 59.34 / 59.36 | 56.53 / 56.70 |
1.050 / 1.047 | 0.008 / 0.006 | faster |
| 4096→512 dgrad, FP32 out, T=16173 | 59.49 / 59.58 | 56.25 / 56.41 |
1.058 / 1.056 | 0.008 / 0.013 | faster |
| 4096→512 dgrad, FP32 out, T=16230 | 59.80 / 59.86 | 56.42 / 56.50 |
1.060 / 1.060 | 0.009 / 0.007 | faster |
| 4096→512 dgrad, FP32 out, T=16231 | 59.30 / 59.37 | 56.35 / 56.52 |
1.052 / 1.050 | 0.005 / 0.007 | faster |
| 4096→512 dgrad, FP32 out, T=16232 | 59.97 / 60.16 | 56.30 / 56.45 |
1.065 / 1.066 | 0.008 / 0.005 | faster |
| 4096→512 dgrad, FP32 out, T=16300 | 59.78 / 59.95 | 56.72 / 56.86 |
1.054 / 1.054 | 0.010 / 0.026 | faster |
| 4096→512 dgrad, FP32 out, T=16383 | 60.09 / 60.25 | 56.74 / 56.87 |
1.059 / 1.059 | 0.008 / 0.008 | faster |
| 4096→512 dgrad, FP32 out, T=16384 | 59.64 / 59.83 | 56.61 / 56.76 |
1.054 / 1.054 | 0.007 / 0.010 | faster |
| 4096→512 fwd, BF16 out, T=16172 | 39.95 / 39.91 | 38.41 / 38.37 |
1.040 / 1.040 | 0.012 / 0.011 | faster |
| 4096→512 fwd, BF16 out, T=16231 | 39.48 / 39.41 | 38.13 / 38.13 |
1.035 / 1.034 | 0.007 / 0.011 | faster |
| 5120→1024 fwd, BF16 out, T=16384 | 90.70 / 90.72 | 88.57 / 88.96 |
1.024 / 1.020 | 0.036 / 0.042 | within noise |
| 5120→1024 wgrad, FP32 out, T=16100 | 96.21 / 96.37 | 92.02 / 92.58 |
1.046 / 1.041 | 0.008 / 0.012 | faster |
| 5120→1024 wgrad, FP32 out, T=16172 | 96.74 / 96.12 | 93.65 / 93.74 |
1.033 / 1.025 | 0.021 / 0.027 | within noise |
| 5120→1024 wgrad, FP32 out, T=16300 | 97.34 / 97.60 | 94.06 / 94.41 |
1.035 / 1.034 | 0.009 / 0.010 | faster |
| 5120→128 dgrad, BF16 out, T=16172 | 28.93 / 29.14 | 27.84 / 28.00 |
1.039 / 1.041 | 0.012 / 0.005 | faster |
| 5120→128 dgrad, BF16 out, T=16231 | 28.46 / 28.66 | 28.12 / 28.17 |
1.012 / 1.017 | 0.014 / 0.010 | within noise |
| 5120→128 dgrad, BF16 out, T=16384 | 29.19 / 29.37 | 28.30 / 28.45 |
1.031 / 1.032 | 0.008 / 0.006 | faster |
| 5120→32 dgrad, BF16 out, T=16172 | 27.15 / 27.30 | 26.52 / 26.59 |
1.023 / 1.027 | 0.018 / 0.016 | faster |
| 5120→32 dgrad, BF16 out, T=16384 | 27.77 / 28.04 | 26.91 / 27.15 |
1.032 / 1.033 | 0.009 / 0.012 | faster |
| 5120→48 dgrad, BF16 out, T=16172 | 27.51 / 27.60 | 26.60 / 26.62 |
1.034 / 1.037 | 0.010 / 0.009 | faster |
| 5120→48 dgrad, BF16 out, T=16384 | 27.84 / 27.91 | 27.05 / 27.13 |
1.029 / 1.029 | 0.010 / 0.012 | faster |
| 5120→512 dgrad, FP32 out, T=16172 | 71.26 / 71.36 | 68.14 / 68.34 |
1.046 / 1.044 | 0.006 / 0.006 | faster |
| 5120→512 dgrad, FP32 out, T=16173 | 73.77 / 73.97 | 68.24 / 68.42 |
1.081 / 1.081 | 0.011 / 0.007 | faster |
| 5120→512 dgrad, FP32 out, T=16230 | 73.31 / 73.50 | 68.39 / 68.43 |
1.072 / 1.074 | 0.007 / 0.006 | faster |
| 5120→512 dgrad, FP32 out, T=16231 | 71.59 / 71.76 | 68.45 / 68.66 |
1.046 / 1.045 | 0.011 / 0.013 | faster |
| 5120→512 dgrad, FP32 out, T=16232 | 73.00 / 73.22 | 68.25 / 68.33 |
1.070 / 1.071 | 0.006 / 0.004 | faster |
| 5120→512 dgrad, FP32 out, T=16300 | 73.61 / 73.84 | 68.50 / 68.68 |
1.075 / 1.075 | 0.015 / 0.021 | faster |
| 5120→512 dgrad, FP32 out, T=16383 | 73.75 / 73.96 | 68.66 / 68.81 |
1.074 / 1.075 | 0.005 / 0.004 | faster |
| 5120→512 dgrad, FP32 out, T=16384 | 71.73 / 71.84 | 68.73 / 68.84 |
1.044 / 1.044 | 0.007 / 0.007 | faster |
| 5120→512 fwd, BF16 out, T=16172 | 47.88 / 47.77 | 46.12 / 46.09 |
1.038 / 1.036 | 0.009 / 0.007 | faster |
| 5120→512 fwd, BF16 out, T=16231 | 47.98 / 47.89 | 46.38 / 46.20 |
1.034 / 1.037 | 0.018 / 0.013 | faster |
| 5120→64 dgrad, BF16 out, T=16172 | 27.84 / 27.98 | 27.20 / 27.44 |
1.024 / 1.020 | 0.009 / 0.012 | faster |
| 5120→64 dgrad, BF16 out, T=16384 | 28.07 / 28.23 | 27.58 / 27.77 |
1.018 / 1.017 | 0.008 / 0.009 | faster |
| 6144→128 dgrad, BF16 out, T=16172 | 34.07 / 34.30 | 33.19 / 33.38 |
1.027 / 1.028 | 0.003 / 0.004 | faster |
| 6144→128 dgrad, BF16 out, T=16231 | 33.34 / 33.58 | 33.16 / 33.34 |
1.005 / 1.007 | 0.005 / 0.004 | within noise |
| 6144→128 dgrad, BF16 out, T=16384 | 34.10 / 34.30 | 33.28 / 33.50 |
1.024 / 1.024 | 0.003 / 0.004 | faster |
| 6144→32 dgrad, BF16 out, T=16172 | 31.43 / 31.72 | 30.43 / 30.70 |
1.033 / 1.033 | 0.023 / 0.012 | faster |
| 6144→32 dgrad, BF16 out, T=16231 | 30.84 / 31.03 | 30.76 / 30.86 |
1.002 / 1.006 | 0.014 / 0.013 | within noise |
| 6144→32 dgrad, BF16 out, T=16384 | 31.63 / 31.85 | 30.99 / 31.09 |
1.021 / 1.024 | 0.010 / 0.011 | faster |
| 6144→576 dgrad, FP32 out, T=16172 | 91.00 / 91.45 | 85.72 / 85.73 |
1.062 / 1.067 | 0.005 / 0.006 | faster |
| 6144→576 dgrad, FP32 out, T=16173 | 91.47 / 92.05 | 86.28 / 86.32 |
1.060 / 1.066 | 0.016 / 0.020 | faster |
| 6144→576 dgrad, FP32 out, T=16230 | 91.13 / 91.37 | 86.36 / 86.53 |
1.055 / 1.056 | 0.005 / 0.005 | faster |
| 6144→576 dgrad, FP32 out, T=16231 | 91.68 / 91.85 | 86.42 / 86.52 |
1.061 / 1.062 | 0.013 / 0.019 | faster |
| 6144→576 dgrad, FP32 out, T=16232 | 91.22 / 91.52 | 86.19 / 86.32 |
1.058 / 1.060 | 0.005 / 0.007 | faster |
| 6144→576 dgrad, FP32 out, T=16300 | 91.74 / 92.16 | 86.59 / 86.75 |
1.060 / 1.062 | 0.009 / 0.011 | faster |
| 6144→576 dgrad, FP32 out, T=16383 | 91.34 / 91.68 | 86.69 / 86.78 |
1.054 / 1.056 | 0.009 / 0.008 | faster |
| 6144→576 dgrad, FP32 out, T=16384 | 92.00 / 92.31 | 87.00 / 87.05 |
1.058 / 1.060 | 0.014 / 0.018 | faster |
| 8192→128 dgrad, BF16 out, T=16172 | 43.64 / 43.84 | 42.99 / 43.17 |
1.015 / 1.016 | 0.004 / 0.004 | faster |
| 8192→128 dgrad, BF16 out, T=16384 | 43.92 / 44.19 | 43.45 / 43.64 |
1.011 / 1.012 | 0.009 / 0.006 | faster |

**GB300 (sm_103a, 152 SMs, CUDA 13.4): this PR vs deterministic Cake and
the fastest non-Cake implementation (read-out run)**

| row | det Cake (us) | fastest non-Cake (us) | this PR (us) | speedup
vs det Cake | speedup vs non-Cake |
|---|---|---|---|---|---|
| 4096→512 dgrad, FP32 out, T=16173 | 59.68 / 59.90 | 57.65 / 57.89
(quack_gemm_serial) | 56.18 / 56.34 | 1.062 / 1.063 | 1.026 / 1.027 |
| 4096→512 dgrad, FP32 out, T=16230 | 59.47 / 59.74 | 58.50 / 58.61
(quack_gemm_parallel) | 56.25 / 56.40 | 1.057 / 1.059 | 1.039 / 1.039 |
| 4096→512 dgrad, FP32 out, T=16232 | 59.60 / 59.76 | 57.95 / 58.11
(quack_gemm_parallel) | 56.38 / 56.54 | 1.057 / 1.057 | 1.027 / 1.028 |
| 4096→512 dgrad, FP32 out, T=16300 | 59.84 / 60.06 | 58.88 / 59.12
(quack_gemm_parallel) | 56.78 / 56.94 | 1.054 / 1.055 | 1.037 / 1.036 |
| 4096→512 dgrad, FP32 out, T=16383 | 59.90 / 59.94 | 56.58 / 56.71
(deepgemm_bf16_det) | 56.89 / 56.94 | 1.053 / 1.053 | 0.995 / 0.996 |
| 5120→1024 wgrad, FP32 out, T=16100 | 96.19 / 96.90 | 98.91 / 99.22
(deepgemm_bf16_default, cublaslt_0, torch_mm) | 92.01 / 92.74 | 1.046 /
1.045 | 1.072 / 1.069 |
| 5120→1024 wgrad, FP32 out, T=16300 | 97.35 / 97.66 | 99.92 / 100.18
(torch_mm, cublaslt_0) | 93.62 / 94.23 | 1.040 / 1.036 | 1.065 / 1.061 |
| 5120→512 dgrad, FP32 out, T=16173 | 73.57 / 73.74 | 70.58 / 70.82
(quack_gemm_parallel) | 68.38 / 68.57 | 1.076 / 1.075 | 1.032 / 1.032 |
| 5120→512 dgrad, FP32 out, T=16230 | 73.62 / 73.73 | 72.21 / 72.46
(quack_gemm_parallel) | 68.24 / 68.34 | 1.079 / 1.079 | 1.058 / 1.060 |
| 5120→512 dgrad, FP32 out, T=16232 | 73.65 / 73.88 | 70.56 / 70.79
(quack_gemm_parallel) | 68.40 / 68.50 | 1.077 / 1.079 | 1.032 / 1.033 |
| 5120→512 dgrad, FP32 out, T=16300 | 73.48 / 73.74 | 71.04 / 71.15
(quack_gemm_serial, quack_gemm_parallel) | 68.64 / 68.76 | 1.071 / 1.072
| 1.034 / 1.034 |
| 5120→512 dgrad, FP32 out, T=16383 | 73.50 / 73.81 | 68.54 / 68.60
(deepgemm_bf16_det) | 68.64 / 68.88 | 1.071 / 1.072 | 0.999 / 0.996 |
| 6144→576 dgrad, FP32 out, T=16173 | 91.91 / 92.24 | 90.54 / 90.89
(quack_gemm_parallel, quack_gemm_serial) | 85.98 / 86.34 | 1.069 / 1.068
| 1.053 / 1.052 |
| 6144→576 dgrad, FP32 out, T=16230 | 92.27 / 92.42 | 88.78 / 89.14
(quack_gemm_serial) | 86.66 / 86.82 | 1.065 / 1.065 | 1.023 / 1.026 |
| 6144→576 dgrad, FP32 out, T=16232 | 92.65 / 92.86 | 89.02 / 89.13
(quack_gemm_serial, quack_gemm_parallel) | 86.66 / 86.90 | 1.069 / 1.069
| 1.028 / 1.025 |
| 6144→576 dgrad, FP32 out, T=16300 | 92.94 / 93.21 | 90.12 / 90.37
(quack_gemm_parallel) | 87.18 / 87.23 | 1.066 / 1.069 | 1.035 / 1.036 |
| 6144→576 dgrad, FP32 out, T=16383 | 92.75 / 93.14 | 90.02 / 90.24
(quack_gemm_serial, deepgemm_bf16_det) | 86.78 / 86.94 | 1.069 / 1.071 |
1.037 / 1.037 |

**R200** (sm_107a, 212 SMs). Of 106 rows, 60 are faster than FlashInfer
main (1.011-1.232x, median 1.068), 36 are within noise, 3 run the same
program as FlashInfer main, and 7 are slower (0.954-0.996x). All 7
slower rows are FP32 weight gradients where FlashInfer main's program
exceeds the accuracy bound and this PR runs a program that meets it. In
two 212-SM FP32 weight-gradient ranges, this PR keeps FlashInfer main's
program even though that program misses the accuracy bound at some token
counts:
- 5120 -> 512 at odd K-block counts from 40962 tokens: 1.13x at T=40962
(a table row), and up to 1.83x at T=57345.
- 4096 -> 512 at odd counts from 24577 to 32767 tokens: 1.12x at
T=25601.

All R200 numbers are from 212-SM parts, with each row timed on one GPU;
the routes for 208- and 216-SM sm_107a parts were accuracy-checked, not
timed. R200 has no read-out run, so this table compares against
FlashInfer main only.

**R200 (sm_107a, 212 SMs, CUDA 13.4): this PR vs FI main**

| row | FI main Cake (us) | this PR (us) | speedup vs FI main | A/A
noise band | verdict |
|---|---|---|---|---|---|
| 4096→1024 wgrad, FP32 out, T=16100 | 52.27 / 52.40 | 52.46 / 52.53 |
0.996 / 0.998 | 0.008 / 0.007 | within noise |
| 4096→1024 wgrad, FP32 out, T=16170 | 56.56 / 56.56 | 57.20 / 57.20 |
0.989 / 0.989 | 0.008 / 0.006 | slower |
| 4096→1024 wgrad, FP32 out, T=16171 | 52.72 / 52.74 | 52.82 / 52.83 |
0.998 / 0.998 | 0.007 / 0.006 | within noise |
| 4096→1024 wgrad, FP32 out, T=16385 | 68.91 / 69.38 | 57.42 / 57.39 |
1.200 / 1.209 | 0.005 / 0.010 | faster |
| 4096→1024 wgrad, FP32 out, T=2048 | 14.93 / 14.99 | 14.86 / 14.91 |
1.005 / 1.005 | 0.022 / 0.023 | within noise |
| 4096→1024 wgrad, FP32 out, T=24576 | 72.83 / 72.99 | 72.96 / 72.88 |
0.998 / 1.002 | 0.003 / 0.005 | within noise |
| 4096→1024 wgrad, FP32 out, T=24577 | 83.50 / 84.64 | 74.13 / 73.90 |
1.126 / 1.145 | 0.022 / 0.037 | faster |
| 4096→1024 wgrad, FP32 out, T=32768 | 97.70 / 97.63 | 91.09 / 91.31 |
1.073 / 1.069 | 0.005 / 0.005 | faster |
| 4096→1024 wgrad, FP32 out, T=40961 | 115.98 / 115.98 | 115.84 / 115.87
| 1.001 / 1.001 | 0.002 / 0.003 | within noise |
| 4096→1024 wgrad, FP32 out, T=40962 | 135.17 / 135.73 | 124.56 / 124.32
| 1.085 / 1.092 | 0.005 / 0.007 | faster |
| 4096→1024 wgrad, FP32 out, T=49153 | 149.41 / 149.60 | 137.17 / 137.04
| 1.089 / 1.092 | 0.003 / 0.004 | faster |
| 4096→1024 wgrad, FP32 out, T=961 | 13.82 / 13.81 | 13.98 / 13.97 |
0.989 / 0.989 | 0.035 / 0.025 | within noise |
| 4096→128 dgrad, BF16 out, T=16172 | 18.24 / 18.27 | 16.74 / 16.78 |
1.090 / 1.089 | 0.011 / 0.016 | faster |
| 4096→128 dgrad, BF16 out, T=16231 | 19.95 / 19.97 | 18.53 / 18.59 |
1.077 / 1.074 | 0.008 / 0.011 | faster |
| 4096→128 dgrad, BF16 out, T=16384 | 18.37 / 18.43 | 16.85 / 16.90 |
1.090 / 1.091 | 0.005 / 0.009 | faster |
| 4096→32 dgrad, BF16 out, T=16172 | 17.50 / 17.57 | 15.89 / 15.89 |
1.101 / 1.106 | 0.015 / 0.012 | faster |
| 4096→32 dgrad, BF16 out, T=16231 | 17.02 / 17.06 | 15.90 / 15.98 |
1.070 / 1.068 | 0.007 / 0.011 | faster |
| 4096→32 dgrad, BF16 out, T=16384 | 17.52 / 17.55 | 15.90 / 15.97 |
1.102 / 1.099 | 0.006 / 0.011 | faster |
| 4096→48 dgrad, BF16 out, T=16172 | 17.33 / 17.36 | 15.89 / 16.00 |
1.091 / 1.085 | 0.010 / 0.017 | faster |
| 4096→48 dgrad, BF16 out, T=16231 | 17.86 / 17.90 | 16.03 / 16.22 |
1.114 / 1.104 | 0.010 / 0.013 | faster |
| 4096→48 dgrad, BF16 out, T=16384 | 17.36 / 17.41 | 16.10 / 16.19 |
1.078 / 1.075 | 0.010 / 0.015 | faster |
| 4096→512 fwd, BF16 out, T=16172 | 33.36 / 33.50 | 33.44 / 33.46 |
0.998 / 1.001 | 0.005 / 0.009 | within noise |
| 4096→512 fwd, BF16 out, T=16231 | 32.58 / 32.69 | 29.98 / 30.03 |
1.087 / 1.089 | 0.013 / 0.016 | faster |
| 4096→512 fwd, BF16 out, T=16384 | 32.43 / 32.48 | 32.38 / 32.45 |
1.002 / 1.001 | 0.005 / 0.009 | within noise |
| 4096→512 wgrad, FP32 out, T=16100 | 35.73 / 35.81 | 33.23 / 32.80 |
1.075 / 1.092 | 0.004 / 0.007 | faster |
| 4096→512 wgrad, FP32 out, T=16170 | 38.34 / 38.35 | 38.37 / 38.38 |
0.999 / 0.999 | 0.011 / 0.011 | within noise |
| 4096→512 wgrad, FP32 out, T=16171 | 35.79 / 35.82 | 35.86 / 35.81 |
0.998 / 1.000 | 0.005 / 0.005 | within noise |
| 4096→512 wgrad, FP32 out, T=16172 | 38.48 / 38.34 | 38.48 / 38.35 |
1.000 / 1.000 | 0.012 / 0.010 | within noise |
| 4096→512 wgrad, FP32 out, T=16173 | 35.82 / 35.89 | 35.87 / 35.95 |
0.999 / 0.998 | 0.005 / 0.005 | within noise |
| 4096→512 wgrad, FP32 out, T=16230 | 38.62 / 38.48 | 35.97 / 35.81 |
1.074 / 1.075 | 0.008 / 0.014 | faster |
| 4096→512 wgrad, FP32 out, T=16232 | 36.06 / 36.14 | 33.41 / 33.09 |
1.079 / 1.092 | 0.006 / 0.006 | faster |
| 4096→512 wgrad, FP32 out, T=16300 | 38.66 / 38.58 | 38.56 / 38.67 |
1.003 / 0.998 | 0.008 / 0.010 | within noise |
| 4096→512 wgrad, FP32 out, T=16383 | 36.22 / 36.24 | 33.46 / 33.10 |
1.083 / 1.095 | 0.006 / 0.007 | faster |
| 4096→512 wgrad, FP32 out, T=16385 | 37.25 / 37.14 | 39.06 / 38.94 |
0.954 / 0.954 | 0.009 / 0.009 | slower |
| 4096→512 wgrad, FP32 out, T=2048 | 9.17 / 9.17 | 9.17 / 9.18 | 1.000 /
0.999 | 0.009 / 0.017 | within noise |
| 4096→512 wgrad, FP32 out, T=24577 | 48.88 / 48.77 | same program as FI
main | - | - | same program |
| 4096→512 wgrad, FP32 out, T=32768 | 67.84 / 67.86 | 55.15 / 55.10 |
1.230 / 1.232 | 0.004 / 0.006 | faster |
| 4096→512 wgrad, FP32 out, T=40961 | 86.59 / 86.53 | 72.86 / 72.48 |
1.188 / 1.194 | 0.009 / 0.014 | faster |
| 4096→512 wgrad, FP32 out, T=961 | 7.10 / 7.17 | 7.14 / 7.15 | 0.994 /
1.003 | 0.009 / 0.020 | within noise |
| 4096→64 dgrad, BF16 out, T=16172 | 17.58 / 17.54 | 15.98 / 15.98 |
1.100 / 1.098 | 0.007 / 0.013 | faster |
| 4096→64 dgrad, BF16 out, T=16231 | 16.88 / 16.77 | 16.00 / 16.10 |
1.055 / 1.042 | 0.018 / 0.021 | faster |
| 4096→64 dgrad, BF16 out, T=16384 | 17.70 / 17.57 | 16.06 / 16.13 |
1.102 / 1.089 | 0.014 / 0.016 | faster |
| 5120→1024 wgrad, FP32 out, T=16100 | 63.14 / 63.30 | 63.09 / 63.20 |
1.001 / 1.002 | 0.005 / 0.004 | within noise |
| 5120→1024 wgrad, FP32 out, T=16170 | 63.47 / 63.38 | 63.71 / 63.76 |
0.996 / 0.994 | 0.003 / 0.003 | slower |
| 5120→1024 wgrad, FP32 out, T=16171 | 63.51 / 63.54 | 63.84 / 63.81 |
0.995 / 0.996 | 0.002 / 0.003 | slower |
| 5120→1024 wgrad, FP32 out, T=16172 | 63.68 / 63.74 | 63.71 / 63.76 |
1.000 / 1.000 | 0.003 / 0.005 | within noise |
| 5120→1024 wgrad, FP32 out, T=16173 | 63.78 / 63.81 | 64.00 / 64.02 |
0.997 / 0.997 | 0.004 / 0.005 | within noise |
| 5120→1024 wgrad, FP32 out, T=16300 | 67.84 / 67.87 | 68.05 / 68.08 |
0.997 / 0.997 | 0.005 / 0.006 | within noise |
| 5120→1024 wgrad, FP32 out, T=16385 | 63.97 / 64.06 | 64.58 / 64.64 |
0.991 / 0.991 | 0.006 / 0.006 | slower |
| 5120→1024 wgrad, FP32 out, T=2048 | 17.30 / 17.52 | 17.28 / 17.44 |
1.001 / 1.005 | 0.021 / 0.015 | within noise |
| 5120→1024 wgrad, FP32 out, T=24576 | 91.55 / 91.62 | 91.31 / 91.38 |
1.003 / 1.003 | 0.003 / 0.003 | within noise |
| 5120→1024 wgrad, FP32 out, T=24577 | 93.97 / 94.00 | 94.98 / 94.99 |
0.989 / 0.990 | 0.003 / 0.005 | slower |
| 5120→1024 wgrad, FP32 out, T=32768 | 118.98 / 118.98 | 118.90 / 118.82
| 1.001 / 1.001 | 0.003 / 0.003 | within noise |
| 5120→1024 wgrad, FP32 out, T=40961 | 148.85 / 148.91 | 149.89 / 150.08
| 0.993 / 0.992 | 0.001 / 0.001 | slower |
| 5120→1024 wgrad, FP32 out, T=961 | 11.36 / 11.42 | 11.20 / 11.23 |
1.014 / 1.017 | 0.013 / 0.021 | within noise |
| 5120→128 dgrad, BF16 out, T=16172 | 23.01 / 22.98 | 21.55 / 21.60 |
1.068 / 1.064 | 0.008 / 0.011 | faster |
| 5120→128 dgrad, BF16 out, T=16231 | 21.41 / 21.46 | 20.03 / 20.16 |
1.069 / 1.065 | 0.006 / 0.010 | faster |
| 5120→128 dgrad, BF16 out, T=16384 | 22.98 / 23.06 | 21.70 / 21.71 |
1.059 / 1.062 | 0.006 / 0.018 | faster |
| 5120→32 dgrad, BF16 out, T=16172 | 19.79 / 19.89 | 18.91 / 18.96 |
1.046 / 1.049 | 0.007 / 0.009 | faster |
| 5120→32 dgrad, BF16 out, T=16231 | 20.50 / 20.53 | 18.82 / 18.90 |
1.089 / 1.086 | 0.008 / 0.013 | faster |
| 5120→32 dgrad, BF16 out, T=16384 | 20.00 / 20.05 | 19.15 / 19.20 |
1.044 / 1.044 | 0.008 / 0.008 | faster |
| 5120→32 fwd, BF16 out, T=16172 | 20.83 / 20.88 | 20.58 / 20.61 | 1.012
/ 1.013 | 0.009 / 0.008 | faster |
| 5120→32 fwd, BF16 out, T=16231 | 20.72 / 20.74 | 20.48 / 20.51 | 1.012
/ 1.011 | 0.005 / 0.007 | faster |
| 5120→32 fwd, BF16 out, T=16384 | 20.90 / 20.98 | 20.62 / 20.66 | 1.014
/ 1.016 | 0.005 / 0.006 | faster |
| 5120→48 dgrad, BF16 out, T=16172 | 20.18 / 20.22 | 19.12 / 19.17 |
1.055 / 1.055 | 0.008 / 0.011 | faster |
| 5120→48 dgrad, BF16 out, T=16231 | 20.90 / 20.98 | 19.20 / 19.26 |
1.089 / 1.089 | 0.009 / 0.013 | faster |
| 5120→48 dgrad, BF16 out, T=16384 | 20.34 / 20.35 | 19.20 / 19.28 |
1.059 / 1.056 | 0.014 / 0.010 | faster |
| 5120→48 fwd, BF16 out, T=16172 | 20.77 / 20.80 | 20.51 / 20.56 | 1.013
/ 1.012 | 0.004 / 0.006 | faster |
| 5120→48 fwd, BF16 out, T=16231 | 20.80 / 20.80 | 20.58 / 20.58 | 1.011
/ 1.011 | 0.004 / 0.007 | faster |
| 5120→48 fwd, BF16 out, T=16384 | 21.02 / 21.09 | 20.80 / 20.83 | 1.011
/ 1.012 | 0.005 / 0.010 | faster |
| 5120→512 fwd, BF16 out, T=16172 | 38.90 / 39.01 | 35.44 / 35.47 |
1.098 / 1.100 | 0.004 / 0.008 | faster |
| 5120→512 fwd, BF16 out, T=16231 | 39.34 / 39.49 | 38.88 / 38.96 |
1.012 / 1.014 | 0.007 / 0.011 | faster |
| 5120→512 fwd, BF16 out, T=16384 | 38.93 / 39.02 | 35.07 / 35.02 |
1.110 / 1.114 | 0.017 / 0.021 | faster |
| 5120→512 wgrad, FP32 out, T=16100 | 40.94 / 40.80 | 40.88 / 40.82 |
1.002 / 1.000 | 0.007 / 0.009 | within noise |
| 5120→512 wgrad, FP32 out, T=16170 | 37.76 / 37.76 | 37.76 / 37.84 |
1.000 / 0.998 | 0.005 / 0.009 | within noise |
| 5120→512 wgrad, FP32 out, T=16171 | 41.09 / 41.22 | 41.20 / 41.20 |
0.997 / 1.000 | 0.008 / 0.012 | within noise |
| 5120→512 wgrad, FP32 out, T=16172 | 37.79 / 37.92 | 37.95 / 37.87 |
0.996 / 1.001 | 0.007 / 0.006 | within noise |
| 5120→512 wgrad, FP32 out, T=16173 | 41.25 / 41.25 | 41.22 / 41.25 |
1.001 / 1.000 | 0.010 / 0.013 | within noise |
| 5120→512 wgrad, FP32 out, T=16300 | 38.03 / 38.13 | 38.08 / 38.05 |
0.999 / 1.002 | 0.006 / 0.009 | within noise |
| 5120→512 wgrad, FP32 out, T=16385 | 41.60 / 41.66 | 41.60 / 41.73 |
1.000 / 0.998 | 0.007 / 0.011 | within noise |
| 5120→512 wgrad, FP32 out, T=2048 | 9.66 / 9.70 | 9.68 / 9.73 | 0.998 /
0.997 | 0.008 / 0.017 | within noise |
| 5120→512 wgrad, FP32 out, T=24576 | 59.04 / 59.04 | 59.06 / 59.01 |
1.000 / 1.000 | 0.005 / 0.009 | within noise |
| 5120→512 wgrad, FP32 out, T=24577 | 54.45 / 54.54 | 54.54 / 54.69 |
0.998 / 0.997 | 0.005 / 0.011 | within noise |
| 5120→512 wgrad, FP32 out, T=32768 | 76.18 / 76.21 | 76.29 / 76.21 |
0.999 / 1.000 | 0.007 / 0.007 | within noise |
| 5120→512 wgrad, FP32 out, T=40961 | 87.28 / 87.26 | 87.23 / 87.39 |
1.001 / 0.999 | 0.005 / 0.005 | within noise |
| 5120→512 wgrad, FP32 out, T=40962 | 99.49 / 99.46 | same program as FI
main | - | - | same program |
| 5120→512 wgrad, FP32 out, T=49153 | 117.54 / 118.19 | same program as
FI main | - | - | same program |
| 5120→512 wgrad, FP32 out, T=961 | 8.61 / 8.66 | 8.58 / 8.64 | 1.004 /
1.002 | 0.013 / 0.024 | within noise |
| 5120→64 dgrad, BF16 out, T=16172 | 19.94 / 19.95 | 19.01 / 19.06 |
1.049 / 1.047 | 0.013 / 0.023 | faster |
| 5120→64 dgrad, BF16 out, T=16231 | 21.06 / 20.96 | 19.25 / 19.38 |
1.094 / 1.081 | 0.008 / 0.013 | faster |
| 5120→64 dgrad, BF16 out, T=16384 | 20.03 / 20.06 | 19.07 / 19.14 |
1.050 / 1.048 | 0.010 / 0.018 | faster |
| 5120→64 fwd, BF16 out, T=16172 | 20.88 / 20.90 | 20.53 / 20.58 | 1.017
/ 1.016 | 0.005 / 0.006 | faster |
| 5120→64 fwd, BF16 out, T=16231 | 20.83 / 20.86 | 20.50 / 20.48 | 1.016
/ 1.019 | 0.004 / 0.009 | faster |
| 5120→64 fwd, BF16 out, T=16384 | 21.10 / 21.15 | 20.75 / 20.75 | 1.017
/ 1.019 | 0.005 / 0.008 | faster |
| 6144→128 dgrad, BF16 out, T=16172 | 24.42 / 24.46 | 23.15 / 23.17 |
1.055 / 1.056 | 0.007 / 0.012 | faster |
| 6144→128 dgrad, BF16 out, T=16231 | 26.08 / 26.16 | 24.85 / 24.86 |
1.050 / 1.052 | 0.005 / 0.010 | faster |
| 6144→128 dgrad, BF16 out, T=16384 | 24.46 / 24.53 | 23.33 / 23.47 |
1.048 / 1.045 | 0.009 / 0.013 | faster |
| 6144→32 dgrad, BF16 out, T=16172 | 22.91 / 23.04 | 21.44 / 21.54 |
1.069 / 1.070 | 0.006 / 0.013 | faster |
| 6144→32 dgrad, BF16 out, T=16231 | 22.74 / 22.82 | 21.55 / 21.74 |
1.055 / 1.050 | 0.010 / 0.013 | faster |
| 6144→32 dgrad, BF16 out, T=16384 | 23.38 / 23.38 | 21.76 / 21.81 |
1.074 / 1.072 | 0.006 / 0.009 | faster |
| 8192→128 dgrad, BF16 out, T=16172 | 30.53 / 30.66 | 29.14 / 29.25 |
1.048 / 1.048 | 0.010 / 0.011 | faster |
| 8192→128 dgrad, BF16 out, T=16231 | 32.10 / 32.16 | 30.48 / 30.54 |
1.053 / 1.053 | 0.007 / 0.008 | faster |
| 8192→128 dgrad, BF16 out, T=16384 | 30.70 / 30.82 | 29.23 / 29.30 |
1.050 / 1.052 | 0.011 / 0.010 | faster |
| 8192→128 fwd, BF16 out, T=16172 | 30.46 / 30.53 | 29.90 / 30.02 |
1.019 / 1.017 | 0.005 / 0.004 | faster |
| 8192→128 fwd, BF16 out, T=16231 | 30.90 / 30.93 | 30.40 / 30.50 |
1.016 / 1.014 | 0.004 / 0.008 | faster |
| 8192→128 fwd, BF16 out, T=16384 | 30.98 / 31.01 | 30.46 / 30.50 |
1.017 / 1.017 | 0.004 / 0.005 | faster |


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Expanded dense GEMM kernel routing across additional GPU
architectures, matrix shapes, and token ranges.
* Added new optimized paths for forward, input-gradient, and
weight-gradient calculations, including parity-based routing.
* Improved reuse of selected kernel bindings in supported execution
paths.

* **Documentation**
* Updated routing and accuracy guidance, including cases where some
weight-gradient routes do not meet stated accuracy criteria.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [49e9ffe](https://github.com/flashinfer-ai/flashinfer/commit/49e9ffef944c8737dbac64c98152e07f79542b23)

- **作者**: eigen
- **时间**: 2026-11-10T00:19:51Z
- **提交信息**: perf(cake_mhc_det): backward forms that share an SM with a side kernel on SM100 / SM103 / SM107 (#9297)

The Cake four-stream mHC training kernel has two modes, deterministic
(`flashinfer.cake_mhc_det_train`) and non-deterministic
(`flashinfer.cake_mhc_nondet_train`). It works on BF16 residual streams
`X[T, 4, H]` at hidden 4096, 5120 and 7168. This PR changes only
backward kernels, in both modes: the deterministic mode on sm_100a,
sm_103a and sm_107a, and the non-deterministic mode at hidden 5120 and
7168, T ≥ 14928, on sm_100a and sm_103a.

Unloaded speedup is main / this PR, so values above 1 mean this PR is
faster. In the deterministic mode, valid (non-void) rows with changed
kernels range from 0.987–1.162 on B200, 0.991–1.206 on GB300,
0.985–1.057 on R200 with 216 SMs and 0.984–1.051 on R200 with 212 SMs.
The B200 and GB300 maxima are at hidden 7168, T 1, backward. The largest
slowdowns are:

- B200, hidden 7168, checkpoint backward, T 32768: 0.987 (2612.24 →
2646.24 us)
- GB300, hidden 5120, backward, T 64: 0.991 (33.53 → 33.82 us)
- R200, hidden 4096, T 8192: checkpoint backward 0.984 (212 SMs) and
backward 0.985 (216 SMs)

On R200 at hidden 5120 and 7168 and T 8193–65536, backward and
checkpoint backward range from 1.020–1.057. On B200 and GB300 at hidden
5120 and 7168 and T ≥ 14928, the range is 0.987–1.006 (B200) and
0.993–1.010 (GB300). Rows with unchanged kernels measure 0.989–1.007
(B200), 0.994–1.007 (GB300), 0.996–1.005 (R200, 216 SMs) and 0.997–1.004
(R200, 212 SMs). In the non-deterministic mode at hidden 5120 and 7168,
T 14928–32768, the unloaded speedup is 0.998–1.016 (B200) and
0.999–1.014 (GB300).

The side-load results were measured on the same GPUs with the CUDA 13.4
toolkit. "L1" runs 16 side CTAs of 640 threads next to the kernel. "Full
hold" keeps one 128-thread side CTA on every SM for the whole run.

- **Full hold, small T:** main cannot start in 27 of 27 measured cells
on B200 (T 64–3648), 30 of 30 on GB300 (T 64–1535) and 45 of 75 on each
R200 board (T 1024–16263; every backward_finish, backward and
checkpointed step cell). This PR starts in all of them.
- **Full hold, larger T:** at hidden 5120 and 7168, T 14928–32768 on
B200 and GB300, neither build is blocked. This PR's time is 0.99–1.02
times main's, both alone and under full hold.
- **Full hold, worst case for this PR:** the highest full-hold slowdown
(full-hold time / time alone) is backward_prepare at hidden 7168 on
R200: 1.57–1.58 (216 SMs) and 1.59–1.60 (212 SMs).
- **L1 on R200:** on the 216-SM R200 at T 14928–16263, main's backward
takes 1.26–1.41 (hidden 5120) and 1.34–1.37 (hidden 7168) times its
unloaded time. With this PR it takes 1.06–1.18 and 1.16–1.18.
- **L1 on B200 and GB300:** at small T, this PR's L1 time is 0.94–1.03
(B200) and 0.86–1.13 (GB300) times main's L1 time; GB300 small-T ratios
are noisy. At hidden 5120 and 7168, T 14928–32768, it is 0.84–0.96
(B200) and 0.85–1.00 (GB300). For backward_finish at hidden 7168 it is
0.84–0.85 (B200) and 0.85–0.86 (GB300).

The other Cake variant is the non-deterministic mode, which this PR also
changes at the shapes above, and the Cake family ships on sm_100a
(B200), sm_103a (GB300) and sm_107a (R200).

Deterministic mode, unloaded A/B timing per GPU:

Operations: forward = forward pass (prepare + finish); backward =
backward from saved forward statistics; checkpoint backward =
forward-statistics recompute + backward (the backward of a checkpointed
forward); checkpointed step = `torch.utils.checkpoint` training step
(forward, then recompute + backward) in one timed region. speedup > 1
means this PR is faster. Forward kernels are unchanged on every board.

### B200 (sm_100a, 148 SMs)

B200, sm_100a, 148 SMs, CUDA 13.4 toolkit, PyTorch 2.14.1+cu130. CUPTI
kernel time with L2 flushed before every call; main, this PR and a
second main copy interleaved ABC/CBA, 12 groups × 64 calls, median of
group medians; noise band = |main copy / main − 1|; void = main copy
differs from main by more than 1 % (no conclusion); † second
measurement.

| H | operation | T | main (us) | this PR (us) | speedup (main / PR) |
noise band | kernels changed |
|---:|---|---:|---:|---:|---:|---:|---|
| 4096 | forward | 1024 | 36.86 | 36.98 | 0.997 | ±0.2 % | no |
| 4096 | forward | 4096 | 100.83 | 101.97 | 0.989 | ±0.1 % | no |
| 4096 | forward | 8192 | 200.80 | 199.95 | 1.004 | ±0.0 % | no |
| 4096 | forward | 14928 | 354.57 | 354.24 | 1.001 | ±0.1 % | no |
| 4096 | forward | 15288 | 360.59 | 361.04 | 0.999 | ±0.0 % | no |
| 4096 | forward | 15566 | 366.10 | 366.54 | 0.999 | ±0.0 % | no |
| 4096 | forward | 15590 | 366.20 | 366.72 | 0.999 | ±0.0 % | no |
| 4096 | forward | 16114 | 376.69 | 376.05 | 1.002 | ±0.0 % | no |
| 4096 | forward | 16132 | 377.20 | 377.22 | 1.000 | ±0.0 % | no |
| 4096 | forward | 16164 | 377.49 | 377.54 | 1.000 | ±0.0 % | no |
| 4096 | forward | 16263 | 378.40 | 378.24 | 1.000 | ±0.0 % | no |
| 4096 | forward | 32768 | 740.51 | 741.36 | 0.999 | ±0.0 % | no |
| 4096 | forward | 65536 | 1464.81 | 1465.05 | 1.000 | ±0.0 % | no |
| 4096 | backward | 1024 | 67.05 | 66.87 | 1.003 | ±0.1 % | no |
| 4096 | backward | 4096 | 184.97 | 185.18 | 0.999 | ±0.0 % | no |
| 4096 | backward | 8192 | 335.15 | 334.72 | 1.001 | ±0.1 % | no |
| 4096 | backward | 14928 | 584.21 | 584.01 | 1.000 | ±0.1 % | no |
| 4096 | backward | 15288 | 598.09 | 599.64 | 0.997 | ±0.0 % | no |
| 4096 | backward | 15566 | 617.71 | 618.57 | 0.999 | ±0.0 % | no |
| 4096 | backward | 15590 | 620.80 | 619.91 | 1.001 | ±0.1 % | no |
| 4096 | backward | 16114 | 630.51 | 630.70 | 1.000 | ±0.0 % | no |
| 4096 | backward | 16132 | 645.87 | 645.77 | 1.000 | ±0.3 % | no |
| 4096 | backward | 16164 | 643.46 | 642.60 | 1.001 | ±0.2 % | no |
| 4096 | backward | 16263 | 638.41 | 638.39 | 1.000 | ±0.2 % | no |
| 4096 | backward | 32768 | 1280.43 | 1274.57 | 1.005 | ±0.5 % | no |
| 4096 | backward | 65536 | 2643.89 | 2632.23 | 1.004 | ±0.1 % | no |
| 4096 | checkpoint backward | 1024 | 78.98 | 78.76 | 1.003 | ±0.0 % |
no |
| 4096 | checkpoint backward | 4096 | 207.45 | 208.70 | 0.994 | ±0.0 % |
no |
| 4096 | checkpoint backward | 8192 | 399.70 | 399.19 | 1.001 | ±0.0 % |
no |
| 4096 | checkpoint backward | 14928 | 697.30 | 696.25 | 1.002 | ±0.2 %
| no |
| 4096 | checkpoint backward | 15288 | 715.59 | 717.16 | 0.998 | ±0.1 %
| no |
| 4096 | checkpoint backward | 15566 | 734.57 | 734.70 | 1.000 | ±0.1 %
| no |
| 4096 | checkpoint backward | 15590 | 734.80 | 735.68 | 0.999 | ±0.2 %
| no |
| 4096 | checkpoint backward | 16114 | 744.89 | 752.57 | 0.990 | ±0.8 %
| no |
| 4096 | checkpoint backward | 16132 | 764.12 | 763.75 | 1.000 | ±0.4 %
| no |
| 4096 | checkpoint backward | 16164 | 763.94 | 765.97 | 0.997 | ±0.3 %
| no |
| 4096 | checkpoint backward | 16263 | 760.73 | 758.92 | 1.002 | ±0.5 %
| no |
| 4096 | checkpoint backward | 32768 | 1502.14 | 1491.31 | 1.007 | ±0.3
% | no |
| 4096 | checkpoint backward | 65536 | 3066.49 | 3086.02 | 0.994 | ±0.3
% | no |
| 4096 | checkpointed step | 4096 | 457.24 | 455.99 | 1.003 | ±0.0 % |
no |
| 4096 | checkpointed step | 16263 | 1687.09 | 1685.83 | 1.001 | ±0.0 %
| no |
| 5120 | forward | 1024 | 47.39 | 47.45 | 0.999 | ±0.0 % | no |
| 5120 | forward | 4096 | 129.73 | 129.91 | 0.999 | ±0.0 % | no |
| 5120 | forward | 14928 | 430.18 | 430.06 | 1.000 | ±0.0 % | no |
| 5120 | forward | 15288 | 438.43 | 438.54 | 1.000 | ±0.0 % | no |
| 5120 | forward | 16263 | 466.36 | 465.97 | 1.001 | ±0.0 % | no |
| 5120 | backward | 1 | 39.13 | 33.85 | 1.156 | ±0.0 % | yes |
| 5120 | backward | 64 | 32.70 | 32.86 | 0.995 | ±0.0 % | yes |
| 5120 | backward | 128 | 35.52 | 34.94 | 1.017 | ±0.0 % | yes |
| 5120 | backward | 129 | 45.12 | 42.28 | 1.067 | ±0.1 % | yes |
| 5120 | backward | 256 | 42.40 | 42.35 | 1.001 | ±0.0 % | yes |
| 5120 | backward | 448 | 51.87 | 52.07 | 0.996 | ±0.1 % | yes |
| 5120 | backward | 512 | 55.53 | 55.81 | 0.995 | ±0.1 % | yes |
| 5120 | backward | 640 | 60.99 | 60.91 | 1.001 | ±0.0 % | yes |
| 5120 | backward | 704 | 67.17 | 67.24 | 0.999 | ±0.0 % | yes |
| 5120 | backward | 896 | 73.80 | 74.31 | 0.993 | ±0.0 % | yes |
| 5120 | backward | 897 | 74.99 | 75.38 | 0.995 | ±0.0 % | no |
| 5120 | backward | 1024 | 83.48 | 84.11 | 0.993 | ±0.0 % | no |
| 5120 | backward | 1921 | 124.74 | 125.05 | 0.998 | ±0.1 % | yes |
| 5120 | backward | 2048 | 128.11 | 128.55 | 0.997 | ±0.1 % | yes |
| 5120 | backward | 2112 | 130.08 | 130.46 | 0.997 | ±0.1 % | yes |
| 5120 | backward | 2689 | 164.76 | 165.25 | 0.997 | ±0.0 % | yes |
| 5120 | backward | 2752 | 166.06 | 166.41 | 0.998 | ±0.0 % | yes |
| 5120 | backward | 2816 | 167.70 | 168.09 | 0.998 | ±0.0 % | yes |
| 5120 | backward | 3585 | 208.37 | 209.04 | 0.997 | ±0.0 % | yes |
| 5120 | backward | 3648 | 209.81 | 211.29 | 0.993 | ±0.0 % | yes |
| 5120 | backward | 4096 | 226.97 | 227.45 | 0.998 | ±0.0 % | no |
| 5120 | backward | 14927 | 721.32 | 723.83 | 0.997 | ±0.1 % | no |
| 5120 | backward | 14928 | 721.76 | 723.73 | 0.997 | ±0.4 % | yes |
| 5120 | backward | 15288 | 742.73 | 740.85 | 1.003 | ±0.8 % | yes |
| 5120 | backward | 16263 | 796.63 | 798.88 | 0.997 | ±0.1 % | yes |
| 5120 | backward | 32768 | 1565.90 | 1558.71 | 1.005† | ±0.2 % | yes |
| 5120 | backward | 65536 | 3206.68 | 3198.49 | 1.003 | ±0.2 % | yes |
| 5120 | checkpoint backward | 64 | 49.32 | 49.27 | 1.001 | ±0.2 % | yes
|
| 5120 | checkpoint backward | 512 | 73.28 | 73.70 | 0.994 | ±0.1 % |
yes |
| 5120 | checkpoint backward | 896 | 94.92 | 95.22 | 0.997 | ±0.0 % |
yes |
| 5120 | checkpoint backward | 1024 | 104.99 | 105.10 | 0.999 | ±0.0 % |
no |
| 5120 | checkpoint backward | 2048 | 158.03 | 159.41 | 0.991 | ±0.0 % |
yes |
| 5120 | checkpoint backward | 3648 | 249.94 | 251.58 | 0.993 | ±0.0 % |
yes |
| 5120 | checkpoint backward | 4096 | 268.24 | 268.30 | 1.000 | ±0.0 % |
no |
| 5120 | checkpoint backward | 14927 | 844.70 | 843.39 | 1.002 | ±0.1 %
| no |
| 5120 | checkpoint backward | 14928 | 844.45 | 844.88 | 0.999 | ±0.0 %
| yes |
| 5120 | checkpoint backward | 15288 | 861.27 | 864.71 | 0.996 | ±0.1 %
| yes |
| 5120 | checkpoint backward | 16263 | 927.51 | 931.36 | 0.996 | ±0.2 %
| yes |
| 5120 | checkpoint backward | 32768 | 1817.85 | 1818.43 | 1.000 | ±0.7
% | yes |
| 5120 | checkpoint backward | 65536 | 3743.14 | 3755.95 | 0.997 | ±0.3
% | yes |
| 5120 | checkpointed step | 896 | 191.66 | 191.36 | 1.002 | ±0.0 % |
yes |
| 5120 | checkpointed step | 2048 | 339.04 | 339.26 | 0.999 | ±0.0 % |
yes |
| 5120 | checkpointed step | 16263 | 2071.26 | 2075.58 | 0.998 | ±0.0 %
| yes |
| 7168 | forward | 1024 | 60.22 | 60.33 | 0.998 | ±0.1 % | no |
| 7168 | forward | 4096 | 175.63 | 174.65 | 1.006 | ±0.0 % | no |
| 7168 | forward | 14928 | 593.45 | 593.75 | 0.999 | ±0.0 % | no |
| 7168 | forward | 15288 | 604.90 | 603.88 | 1.002 | ±0.0 % | no |
| 7168 | forward | 16263 | 642.86 | 643.20 | 0.999 | ±0.0 % | no |
| 7168 | backward | 1 | 43.14 | 37.12 | 1.162 | ±0.0 % | yes |
| 7168 | backward | 64 | 35.10 | 35.07 | 1.001 | ±0.0 % | yes |
| 7168 | backward | 320 | 53.70 | 53.62 | 1.001 | ±0.1 % | yes |
| 7168 | backward | 576 | 71.05 | 70.58 | 1.007 | ±0.1 % | yes |
| 7168 | backward | 577 | 73.47 | 72.57 | 1.012 | ±0.0 % | yes |
| 7168 | backward | 640 | 73.93 | 73.97 | 0.999 | ±0.1 % | yes |
| 7168 | backward | 961 | 107.74 | 99.65 | 1.081 | ±0.0 % | yes |
| 7168 | backward | 992 | 103.02 | 100.06 | 1.030 | ±0.1 % | yes |
| 7168 | backward | 1024 | 100.30 | 100.83 | 0.995 | ±0.1 % | yes |
| 7168 | backward | 4096 | 300.59 | 300.21 | 1.001 | ±0.1 % | no |
| 7168 | backward | 14927 | 1011.69 | 1012.69 | 0.999 | ±0.1 % | no |
| 7168 | backward | 14928 | 1021.32 | 1023.14 | 0.998 | ±0.3 % | yes |
| 7168 | backward | 15288 | 1028.27 | 1036.90 | 0.992 | ±0.1 % | yes |
| 7168 | backward | 16263 | 1107.23 | 1116.60 | 0.992 | ±0.1 % | yes |
| 7168 | backward | 32768 | 2268.19 | 2250.21 | 1.008 | void | yes |
| 7168 | backward | 65536 | 4602.59 | 4628.79 | 0.994 | ±0.0 % | yes |
| 7168 | checkpoint backward | 64 | 53.58 | 53.58 | 1.000 | ±0.1 % | yes
|
| 7168 | checkpoint backward | 640 | 97.63 | 98.26 | 0.994 | ±0.0 % |
yes |
| 7168 | checkpoint backward | 1024 | 124.10 | 125.05 | 0.992 | ±0.0 % |
yes |
| 7168 | checkpoint backward | 4096 | 352.65 | 352.53 | 1.000 | ±0.0 % |
no |
| 7168 | checkpoint backward | 14927 | 1193.02 | 1193.21 | 1.000 | ±0.8
% | no |
| 7168 | checkpoint backward | 14928 | 1188.88 | 1186.81 | 1.002 | ±0.6
% | yes |
| 7168 | checkpoint backward | 15288 | 1214.37 | 1206.71 | 1.006 | ±0.3
% | yes |
| 7168 | checkpoint backward | 16263 | 1299.51 | 1301.20 | 0.999 | ±0.2
% | yes |
| 7168 | checkpoint backward | 32768 | 2612.24 | 2646.24 | 0.987 | ±0.2
% | yes |
| 7168 | checkpoint backward | 65536 | 5331.84 | 5326.96 | 1.001 | ±0.0
% | yes |
| 7168 | checkpointed step | 640 | 203.89 | 203.62 | 1.001 | ±0.1 % |
yes |
| 7168 | checkpointed step | 1024 | 262.79 | 263.90 | 0.996 | ±0.0 % |
yes |
| 7168 | checkpointed step | 16263 | 2883.05 | 2890.36 | 0.997 | ±0.4 %
| yes |

### GB300 (sm_103a, 152 SMs)

GB300, sm_103a, 152 SMs, CUDA 13.4 toolkit, PyTorch 2.14.1+cu130. CUPTI
kernel time with L2 flushed before every call; main, this PR and a
second main copy interleaved ABC/CBA, 12 groups × 64 calls, median of
group medians; noise band = |main copy / main − 1|.

| H | operation | T | main (us) | this PR (us) | speedup (main / PR) |
noise band | kernels changed |
|---:|---|---:|---:|---:|---:|---:|---|
| 4096 | forward | 1024 | 36.35 | 36.34 | 1.000 | ±0.0 % | no |
| 4096 | forward | 4096 | 99.46 | 100.08 | 0.994 | ±0.0 % | no |
| 4096 | forward | 8192 | 194.61 | 194.38 | 1.001 | ±0.0 % | no |
| 4096 | forward | 14928 | 340.39 | 340.26 | 1.000 | ±0.0 % | no |
| 4096 | forward | 15288 | 347.95 | 347.68 | 1.001 | ±0.0 % | no |
| 4096 | forward | 15566 | 353.10 | 353.06 | 1.000 | ±0.0 % | no |
| 4096 | forward | 15590 | 353.36 | 353.55 | 0.999 | ±0.0 % | no |
| 4096 | forward | 16114 | 363.86 | 363.86 | 1.000 | ±0.0 % | no |
| 4096 | forward | 16132 | 364.77 | 364.98 | 0.999 | ±0.0 % | no |
| 4096 | forward | 16164 | 365.03 | 365.14 | 1.000 | ±0.0 % | no |
| 4096 | forward | 16263 | 366.85 | 367.22 | 0.999 | ±0.0 % | no |
| 4096 | forward | 32768 | 725.31 | 725.11 | 1.000 | ±0.0 % | no |
| 4096 | forward | 65536 | 1431.13 | 1430.78 | 1.000 | ±0.0 % | no |
| 4096 | backward | 1024 | 65.30 | 65.28 | 1.000 | ±0.0 % | no |
| 4096 | backward | 4096 | 187.14 | 187.04 | 1.001 | ±0.0 % | no |
| 4096 | backward | 8192 | 325.81 | 325.79 | 1.000 | ±0.1 % | no |
| 4096 | backward | 14928 | 567.30 | 567.46 | 1.000 | ±0.0 % | no |
| 4096 | backward | 15288 | 580.70 | 582.38 | 0.997 | ±0.1 % | no |
| 4096 | backward | 15566 | 588.43 | 587.26 | 1.002 | ±0.0 % | no |
| 4096 | backward | 15590 | 590.13 | 587.78 | 1.004 | ±0.0 % | no |
| 4096 | backward | 16114 | 606.08 | 603.06 | 1.005 | ±0.0 % | no |
| 4096 | backward | 16132 | 610.82 | 611.35 | 0.999 | ±0.0 % | no |
| 4096 | backward | 16164 | 611.62 | 610.60 | 1.002 | ±0.0 % | no |
| 4096 | backward | 16263 | 616.31 | 613.15 | 1.005 | ±0.0 % | no |
| 4096 | backward | 32768 | 1181.94 | 1179.64 | 1.002 | ±0.0 % | no |
| 4096 | backward | 65536 | 2328.64 | 2323.18 | 1.002 | ±0.0 % | no |
| 4096 | checkpoint backward | 1024 | 77.47 | 77.34 | 1.002 | ±0.1 % |
no |
| 4096 | checkpoint backward | 4096 | 213.34 | 212.42 | 1.004 | ±0.0 % |
no |
| 4096 | checkpoint backward | 8192 | 383.22 | 384.01 | 0.998 | ±0.0 % |
no |
| 4096 | checkpoint backward | 14928 | 666.70 | 665.76 | 1.001 | ±0.0 %
| no |
| 4096 | checkpoint backward | 15288 | 679.61 | 681.79 | 0.997 | ±0.0 %
| no |
| 4096 | checkpoint backward | 15566 | 688.48 | 687.01 | 1.002 | ±0.0 %
| no |
| 4096 | checkpoint backward | 15590 | 690.06 | 687.37 | 1.004 | ±0.0 %
| no |
| 4096 | checkpoint backward | 16114 | 706.82 | 705.33 | 1.002 | ±0.1 %
| no |
| 4096 | checkpoint backward | 16132 | 712.97 | 714.30 | 0.998 | ±0.0 %
| no |
| 4096 | checkpoint backward | 16164 | 714.09 | 712.31 | 1.002 | ±0.0 %
| no |
| 4096 | checkpoint backward | 16263 | 719.37 | 715.78 | 1.005 | ±0.0 %
| no |
| 4096 | checkpoint backward | 32768 | 1378.25 | 1376.30 | 1.001 | ±0.0
% | no |
| 4096 | checkpoint backward | 65536 | 2702.13 | 2696.77 | 1.002 | ±0.0
% | no |
| 4096 | checkpointed step | 4096 | 449.80 | 451.18 | 0.997 | ±0.0 % |
no |
| 4096 | checkpointed step | 16263 | 1615.85 | 1615.82 | 1.000 | ±0.0 %
| no |
| 5120 | forward | 1024 | 46.24 | 46.19 | 1.001 | ±0.1 % | no |
| 5120 | forward | 4096 | 128.20 | 128.10 | 1.001 | ±0.0 % | no |
| 5120 | forward | 14928 | 421.86 | 422.27 | 0.999 | ±0.0 % | no |
| 5120 | forward | 15288 | 429.42 | 429.42 | 1.000 | ±0.0 % | no |
| 5120 | forward | 16263 | 457.73 | 458.37 | 0.999 | ±0.0 % | no |
| 5120 | backward | 1 | 39.93 | 34.46 | 1.159 | ±0.1 % | yes |
| 5120 | backward | 64 | 33.53 | 33.82 | 0.991 | ±0.0 % | yes |
| 5120 | backward | 128 | 36.42 | 35.94 | 1.013 | ±0.2 % | yes |
| 5120 | backward | 129 | 46.39 | 44.64 | 1.039 | ±0.4 % | yes |
| 5120 | backward | 256 | 44.61 | 44.67 | 0.999 | ±0.0 % | yes |
| 5120 | backward | 448 | 55.63 | 55.94 | 0.994 | ±0.1 % | yes |
| 5120 | backward | 640 | 63.35 | 63.10 | 1.004 | ±0.1 % | yes |
| 5120 | backward | 704 | 73.49 | 73.35 | 1.002 | ±0.3 % | yes |
| 5120 | backward | 896 | 76.46 | 76.86 | 0.995 | ±0.2 % | yes |
| 5120 | backward | 960 | 77.67 | 77.28 | 1.005 | ±0.1 % | yes |
| 5120 | backward | 961 | 84.19 | 83.90 | 1.003 | ±0.0 % | yes |
| 5120 | backward | 1024 | 85.67 | 85.58 | 1.001 | ±0.0 % | yes |
| 5120 | backward | 1152 | 89.74 | 89.79 | 0.999 | ±0.1 % | yes |
| 5120 | backward | 1280 | 92.17 | 91.71 | 1.005 | ±0.0 % | yes |
| 5120 | backward | 1408 | 104.04 | 103.86 | 1.002 | ±0.0 % | yes |
| 5120 | backward | 1535 | 103.54 | 103.39 | 1.001 | ±0.2 % | yes |
| 5120 | backward | 4096 | 222.49 | 222.65 | 0.999 | ±0.0 % | no |
| 5120 | backward | 14927 | 697.20 | 696.29 | 1.001 | ±0.0 % | no |
| 5120 | backward | 14928 | 697.84 | 696.34 | 1.002 | ±0.0 % | yes |
| 5120 | backward | 15288 | 711.65 | 710.74 | 1.001 | ±0.0 % | yes |
| 5120 | backward | 16263 | 757.70 | 757.15 | 1.001 | ±0.0 % | yes |
| 5120 | backward | 32768 | 1465.86 | 1455.10 | 1.007 | ±0.0 % | yes |
| 5120 | backward | 65536 | 2878.59 | 2849.06 | 1.010 | ±0.0 % | yes |
| 5120 | checkpoint backward | 64 | 48.17 | 47.84 | 1.007 | ±0.0 % | yes
|
| 5120 | checkpoint backward | 512 | 72.10 | 72.22 | 0.998 | ±0.0 % |
yes |
| 5120 | checkpoint backward | 1024 | 104.50 | 105.02 | 0.995 | ±0.1 % |
yes |
| 5120 | checkpoint backward | 1535 | 129.58 | 128.82 | 1.006 | ±0.0 % |
yes |
| 5120 | checkpoint backward | 4096 | 262.93 | 263.06 | 1.000 | ±0.0 % |
no |
| 5120 | checkpoint backward | 14927 | 816.78 | 816.32 | 1.001 | ±0.0 %
| no |
| 5120 | checkpoint backward | 14928 | 816.50 | 816.72 | 1.000 | ±0.0 %
| yes |
| 5120 | checkpoint backward | 15288 | 831.60 | 832.54 | 0.999 | ±0.0 %
| yes |
| 5120 | checkpoint backward | 16263 | 885.41 | 887.90 | 0.997 | ±0.0 %
| yes |
| 5120 | checkpoint backward | 32768 | 1699.93 | 1692.56 | 1.004 | ±0.0
% | yes |
| 5120 | checkpoint backward | 65536 | 3326.69 | 3302.73 | 1.007 | ±0.0
% | yes |
| 5120 | checkpointed step | 1024 | 203.58 | 203.64 | 1.000 | ±0.0 % |
yes |
| 5120 | checkpointed step | 1535 | 263.96 | 263.90 | 1.000 | ±0.0 % |
yes |
| 5120 | checkpointed step | 16263 | 2007.62 | 2015.71 | 0.996 | ±0.0 %
| yes |
| 7168 | forward | 1024 | 57.05 | 56.67 | 1.007 | ±0.1 % | no |
| 7168 | forward | 4096 | 171.59 | 171.31 | 1.002 | ±0.0 % | no |
| 7168 | forward | 14928 | 578.98 | 579.01 | 1.000 | ±0.0 % | no |
| 7168 | forward | 15288 | 590.34 | 590.31 | 1.000 | ±0.0 % | no |
| 7168 | forward | 16263 | 632.72 | 633.21 | 0.999 | ±0.0 % | no |
| 7168 | backward | 1 | 44.94 | 37.26 | 1.206 | ±0.2 % | yes |
| 7168 | backward | 64 | 37.33 | 36.75 | 1.016 | ±0.0 % | yes |
| 7168 | backward | 192 | 44.82 | 44.41 | 1.009 | ±0.1 % | yes |
| 7168 | backward | 193 | 55.89 | 53.46 | 1.045 | ±0.4 % | yes |
| 7168 | backward | 256 | 50.14 | 49.99 | 1.003 | ±0.1 % | yes |
| 7168 | backward | 320 | 53.83 | 52.80 | 1.020 | ±0.0 % | yes |
| 7168 | backward | 512 | 65.94 | 66.10 | 0.998 | ±0.3 % | yes |
| 7168 | backward | 576 | 68.97 | 68.62 | 1.005 | ±0.1 % | yes |
| 7168 | backward | 640 | 77.17 | 76.50 | 1.009 | ±0.1 % | yes |
| 7168 | backward | 641 | 78.13 | 78.45 | 0.996 | ±0.1 % | yes |
| 7168 | backward | 1024 | 95.24 | 95.35 | 0.999 | ±0.1 % | yes |
| 7168 | backward | 1151 | 105.41 | 105.33 | 1.001 | ±0.1 % | yes |
| 7168 | backward | 4096 | 287.16 | 287.13 | 1.000 | ±0.0 % | no |
| 7168 | backward | 14927 | 944.64 | 943.22 | 1.002 | ±0.0 % | no |
| 7168 | backward | 14928 | 944.38 | 945.60 | 0.999 | ±0.0 % | yes |
| 7168 | backward | 15288 | 957.57 | 964.73 | 0.993 | ±0.0 % | yes |
| 7168 | backward | 16263 | 1019.29 | 1023.38 | 0.996 | ±0.0 % | yes |
| 7168 | backward | 32768 | 2033.79 | 2048.13 | 0.993 | ±0.0 % | yes |
| 7168 | backward | 65536 | 4002.54 | 4016.49 | 0.997 | ±0.0 % | yes |
| 7168 | checkpoint backward | 64 | 52.90 | 53.11 | 0.996 | ±0.0 % | yes
|
| 7168 | checkpoint backward | 640 | 99.50 | 99.07 | 1.004 | ±0.1 % |
yes |
| 7168 | checkpoint backward | 1024 | 118.07 | 117.99 | 1.001 | ±0.1 % |
yes |
| 7168 | checkpoint backward | 1151 | 128.68 | 128.20 | 1.004 | ±0.0 % |
yes |
| 7168 | checkpoint backward | 4096 | 338.70 | 338.53 | 1.001 | ±0.0 % |
no |
| 7168 | checkpoint backward | 14927 | 1103.33 | 1103.90 | 0.999 | ±0.0
% | no |
| 7168 | checkpoint backward | 14928 | 1103.82 | 1104.14 | 1.000 | ±0.0
% | yes |
| 7168 | checkpoint backward | 15288 | 1118.78 | 1123.46 | 0.996 | ±0.0
% | yes |
| 7168 | checkpoint backward | 16263 | 1195.34 | 1200.70 | 0.996 | ±0.0
% | yes |
| 7168 | checkpoint backward | 32768 | 2353.43 | 2368.39 | 0.994 | ±0.0
% | yes |
| 7168 | checkpoint backward | 65536 | 4624.66 | 4638.48 | 0.997 | ±0.0
% | yes |
| 7168 | checkpointed step | 1024 | 244.78 | 244.31 | 1.002 | ±0.0 % |
yes |
| 7168 | checkpointed step | 1151 | 266.06 | 266.36 | 0.999 | ±0.1 % |
yes |
| 7168 | checkpointed step | 16263 | 2753.33 | 2759.38 | 0.998 | ±0.0 %
| yes |

### R200 (sm_107a, 216 SMs)

R200, sm_107a, 216 SMs, CUDA 13.4 toolkit, PyTorch 2.14.1+cu130. CUPTI
kernel time with L2 flushed before every call; main, this PR and a
second main copy interleaved ABC/CBA, 6 groups × 32 calls, median of
group medians; noise band = |main copy / main − 1|; void = main copy
differs from main by more than 1 % (no conclusion).

| H | operation | T | main (us) | this PR (us) | speedup (main / PR) |
noise band | kernels changed |
|---:|---|---:|---:|---:|---:|---:|---|
| 4096 | forward | 1024 | 29.15 | 29.27 | 0.996 | ±0.0 % | no |
| 4096 | forward | 4096 | 75.74 | 75.66 | 1.001 | ±0.1 % | no |
| 4096 | forward | 8192 | 133.66 | 133.50 | 1.001 | ±0.2 % | no |
| 4096 | forward | 14928 | 232.21 | 231.86 | 1.002 | ±0.1 % | no |
| 4096 | forward | 15288 | 237.41 | 237.45 | 1.000 | ±0.0 % | no |
| 4096 | forward | 15566 | 244.06 | 244.65 | 0.998 | ±0.4 % | no |
| 4096 | forward | 15590 | 243.91 | 244.74 | 0.997 | ±0.4 % | no |
| 4096 | forward | 16114 | 250.36 | 250.06 | 1.001 | ±0.0 % | no |
| 4096 | forward | 16132 | 250.10 | 250.97 | 0.997 | ±0.1 % | no |
| 4096 | forward | 16164 | 251.02 | 250.68 | 1.001 | ±0.1 % | no |
| 4096 | forward | 16263 | 252.31 | 252.16 | 1.001 | ±0.2 % | no |
| 4096 | forward | 32768 | 484.02 | 485.94 | 0.996 | ±0.2 % | no |
| 4096 | forward | 65536 | 951.53 | 952.54 | 0.999 | ±0.1 % | no |
| 4096 | backward | 1024 | 49.64 | 49.67 | 0.999 | ±0.7 % | yes |
| 4096 | backward | 4096 | 127.98 | 128.37 | 0.997 | ±0.4 % | yes |
| 4096 | backward | 8192 | 215.47 | 218.73 | 0.985 | ±0.1 % | yes |
| 4096 | backward | 14928 | 384.00 | 384.10 | 1.000 | ±0.4 % | yes |
| 4096 | backward | 15288 | 389.58 | 390.38 | 0.998 | ±0.8 % | yes |
| 4096 | backward | 15566 | 396.90 | 393.96 | 1.007 | ±0.5 % | yes |
| 4096 | backward | 15590 | 396.95 | 394.68 | 1.006 | ±0.2 % | yes |
| 4096 | backward | 16114 | 405.19 | 405.38 | 1.000 | ±0.3 % | yes |
| 4096 | backward | 16132 | 407.51 | 405.62 | 1.005 | ±0.0 % | yes |
| 4096 | backward | 16164 | 406.90 | 407.78 | 0.998 | ±0.2 % | yes |
| 4096 | backward | 16263 | 409.29 | 408.04 | 1.003 | ±0.4 % | yes |
| 4096 | backward | 32768 | 823.85 | 823.03 | 1.001 | ±0.4 % | yes |
| 4096 | backward | 65536 | 1595.23 | 1602.02 | 0.996 | ±0.1 % | yes |
| 4096 | checkpoint backward | 1024 | 60.84 | 61.23 | 0.994 | ±0.1 % |
yes |
| 4096 | checkpoint backward | 4096 | 149.35 | 148.95 | 1.003 | ±0.1 % |
yes |
| 4096 | checkpoint backward | 8192 | 259.01 | 262.18 | 0.988 | ±0.7 % |
yes |
| 4096 | checkpoint backward | 14928 | 459.43 | 459.53 | 1.000 | ±0.4 %
| yes |
| 4096 | checkpoint backward | 15288 | 460.31 | 461.80 | 0.997 | ±0.6 %
| yes |
| 4096 | checkpoint backward | 15566 | 468.50 | 464.90 | 1.008 | ±0.0 %
| yes |
| 4096 | checkpoint backward | 15590 | 469.75 | 465.70 | 1.009 | ±0.1 %
| yes |
| 4096 | checkpoint backward | 16114 | 478.50 | 477.49 | 1.002 | ±0.0 %
| yes |
| 4096 | checkpoint backward | 16132 | 480.14 | 477.14 | 1.006 | ±0.1 %
| yes |
| 4096 | checkpoint backward | 16164 | 479.98 | 480.43 | 0.999 | ±0.1 %
| yes |
| 4096 | checkpoint backward | 16263 | 482.43 | 480.43 | 1.004 | ±0.1 %
| yes |
| 4096 | checkpoint backward | 32768 | 949.83 | 950.27 | 1.000 | ±0.3 %
| yes |
| 4096 | checkpoint backward | 65536 | 1850.11 | 1849.99 | 1.000 | ±0.1
% | yes |
| 5120 | forward | 1024 | 39.35 | 39.35 | 1.000 | ±0.1 % | no |
| 5120 | forward | 4096 | 96.58 | 96.07 | 1.005 | ±0.1 % | no |
| 5120 | forward | 8192 | 168.19 | 168.11 | 1.000 | ±0.2 % | no |
| 5120 | forward | 8193 | 172.06 | 171.59 | 1.003 | ±0.3 % | no |
| 5120 | forward | 14928 | 290.18 | 289.70 | 1.002 | ±0.3 % | no |
| 5120 | forward | 15288 | 296.27 | 296.38 | 1.000 | ±0.2 % | no |
| 5120 | forward | 16263 | 315.58 | 315.62 | 1.000 | ±0.1 % | no |
| 5120 | forward | 32768 | 603.79 | 604.62 | 0.999 | ±0.1 % | no |
| 5120 | forward | 65536 | 1182.78 | 1183.92 | 0.999 | ±0.1 % | no |
| 5120 | backward | 1024 | 61.10 | 61.67 | 0.991 | ±0.1 % | yes |
| 5120 | backward | 4096 | 156.11 | 157.99 | 0.988 | ±0.1 % | yes |
| 5120 | backward | 8192 | 271.56 | 272.53 | 0.996 | ±0.3 % | yes |
| 5120 | backward | 8193 | 295.63 | 279.92 | 1.056 | ±0.3 % | yes |
| 5120 | backward | 14928 | 493.17 | 471.77 | 1.045 | ±0.1 % | yes |
| 5120 | backward | 15288 | 501.82 | 479.36 | 1.047 | ±0.0 % | yes |
| 5120 | backward | 16263 | 524.78 | 504.67 | 1.040 | ±0.3 % | yes |
| 5120 | backward | 32768 | 1030.48 | 976.26 | 1.056 | ±0.6 % | yes |
| 5120 | backward | 65536 | 2082.49 | 1990.64 | 1.046 | ±0.1 % | yes |
| 5120 | checkpoint backward | 1024 | 81.00 | 81.78 | 0.990 | ±0.2 % |
yes |
| 5120 | checkpoint backward | 4096 | 191.11 | 192.39 | 0.993 | ±0.1 % |
yes |
| 5120 | checkpoint backward | 8192 | 331.63 | 330.74 | 1.003 | ±0.1 % |
yes |
| 5120 | checkpoint backward | 8193 | 362.88 | 344.91 | 1.052 | ±0.0 % |
yes |
| 5120 | checkpoint backward | 14928 | 595.84 | 571.31 | 1.043 | ±0.2 %
| yes |
| 5120 | checkpoint backward | 15288 | 598.29 | 569.90 | 1.050 | ±0.1 %
| yes |
| 5120 | checkpoint backward | 16263 | 627.94 | 601.78 | 1.043 | ±0.0 %
| yes |
| 5120 | checkpoint backward | 32768 | 1201.53 | 1136.82 | 1.057 | ±0.4
% | yes |
| 5120 | checkpoint backward | 65536 | 2398.04 | 2291.93 | 1.046 | ±0.1
% | yes |
| 7168 | forward | 1024 | 47.57 | 47.63 | 0.999 | void | no |
| 7168 | forward | 4096 | 124.62 | 124.64 | 1.000 | ±0.1 % | no |
| 7168 | forward | 8192 | 226.66 | 226.62 | 1.000 | ±0.2 % | no |
| 7168 | forward | 8193 | 230.09 | 230.30 | 0.999 | ±0.2 % | no |
| 7168 | forward | 14928 | 396.02 | 395.97 | 1.000 | ±0.2 % | no |
| 7168 | forward | 15288 | 403.47 | 404.33 | 0.998 | ±0.1 % | no |
| 7168 | forward | 16263 | 430.70 | 430.66 | 1.000 | ±0.1 % | no |
| 7168 | forward | 32768 | 831.35 | 831.31 | 1.000 | ±0.2 % | no |
| 7168 | forward | 65536 | 1636.78 | 1635.94 | 1.001 | ±0.2 % | no |
| 7168 | backward | 1024 | 77.49 | 76.29 | 1.016 | ±0.8 % | yes |
| 7168 | backward | 4096 | 219.89 | 217.30 | 1.012 | ±0.5 % | yes |
| 7168 | backward | 8192 | 404.84 | 398.51 | 1.016 | ±0.1 % | yes |
| 7168 | backward | 8193 | 413.15 | 398.67 | 1.036 | ±0.2 % | yes |
| 7168 | backward | 14928 | 721.62 | 689.18 | 1.047 | ±0.3 % | yes |
| 7168 | backward | 15288 | 736.21 | 708.91 | 1.039 | ±0.1 % | yes |
| 7168 | backward | 16263 | 784.33 | 758.66 | 1.034 | ±0.2 % | yes |
| 7168 | backward | 32768 | 1517.76 | 1471.02 | 1.032 | ±0.2 % | yes |
| 7168 | backward | 65536 | 2913.23 | 2834.49 | 1.028 | ±0.0 % | yes |
| 7168 | checkpoint backward | 1024 | 100.01 | 98.75 | 1.013 | ±0.7 % |
yes |
| 7168 | checkpoint backward | 4096 | 260.80 | 257.93 | 1.011 | ±0.2 % |
yes |
| 7168 | checkpoint backward | 8192 | 477.19 | 471.31 | 1.012 | ±0.3 % |
yes |
| 7168 | checkpoint backward | 8193 | 494.67 | 480.39 | 1.030 | ±0.4 % |
yes |
| 7168 | checkpoint backward | 14928 | 844.93 | 812.96 | 1.039 | ±0.4 %
| yes |
| 7168 | checkpoint backward | 15288 | 850.99 | 823.19 | 1.034 | ±0.1 %
| yes |
| 7168 | checkpoint backward | 16263 | 909.51 | 883.36 | 1.030 | ±0.2 %
| yes |
| 7168 | checkpoint backward | 32768 | 1716.28 | 1662.04 | 1.033 | ±0.2
% | yes |
| 7168 | checkpoint backward | 65536 | 3300.28 | 3232.86 | 1.021 | ±0.1
% | yes |

### R200 (sm_107a, 212 SMs)

R200, sm_107a, 212 SMs, CUDA 13.4 toolkit, PyTorch 2.14.1+cu130. CUPTI
kernel time with L2 flushed before every call; main, this PR and a
second main copy interleaved ABC/CBA, 6 groups × 32 calls, median of
group medians; noise band = |main copy / main − 1|; void = main copy
differs from main by more than 1 % (no conclusion); † second
measurement.

| H | operation | T | main (us) | this PR (us) | speedup (main / PR) |
noise band | kernels changed |
|---:|---|---:|---:|---:|---:|---:|---|
| 4096 | forward | 1024 | 28.96 | 28.90 | 1.002 | ±0.2 % | no |
| 4096 | forward | 4096 | 73.42 | 73.13 | 1.004 | ±0.2 % | no |
| 4096 | forward | 8192 | 127.31 | 127.59 | 0.998 | ±0.1 % | no |
| 4096 | forward | 14928 | 219.68 | 219.76 | 1.000 | ±0.3 % | no |
| 4096 | forward | 15288 | 229.19 | 229.19 | 1.000 | ±0.1 % | no |
| 4096 | forward | 15566 | 230.08 | 230.34 | 0.999 | ±0.1 % | no |
| 4096 | forward | 15590 | 230.08 | 230.49 | 0.998 | ±0.2 % | no |
| 4096 | forward | 16114 | 235.87 | 236.13 | 0.999 | ±0.0 % | no |
| 4096 | forward | 16132 | 236.41 | 236.35 | 1.000 | ±0.1 % | no |
| 4096 | forward | 16164 | 236.71 | 236.75 | 1.000 | ±0.1 % | no |
| 4096 | forward | 16263 | 237.67 | 237.76 | 1.000 | ±0.1 % | no |
| 4096 | forward | 32768 | 454.76 | 454.99 | 0.999 | ±0.0 % | no |
| 4096 | forward | 65536 | 888.95 | 889.34 | 1.000 | ±0.1 % | no |
| 4096 | backward | 1024 | 47.94 | 48.14 | 0.996 | ±0.1 % | yes |
| 4096 | backward | 4096 | 121.63 | 121.65 | 1.000 | ±0.7 % | yes |
| 4096 | backward | 8192 | 205.67 | 206.73 | 0.995 | ±0.1 % | yes |
| 4096 | backward | 14928 | 351.13 | 353.40 | 0.994 | ±0.0 % | yes |
| 4096 | backward | 15288 | 363.80 | 359.88 | 1.011 | ±0.3 % | yes |
| 4096 | backward | 15566 | 365.91 | 366.49 | 0.998 | ±0.3 % | yes |
| 4096 | backward | 15590 | 366.53 | 367.96 | 0.996 | ±0.2 % | yes |
| 4096 | backward | 16114 | 387.56 | 386.77 | 1.002 | ±0.0 % | yes |
| 4096 | backward | 16132 | 385.96 | 386.03 | 1.000 | ±0.1 % | yes |
| 4096 | backward | 16164 | 389.44 | 387.66 | 1.005 | ±0.3 % | yes |
| 4096 | backward | 16263 | 377.64 | 380.88 | 0.991 | ±0.0 % | yes |
| 4096 | backward | 32768 | 722.45 | 725.02 | 0.996 | ±0.1 % | yes |
| 4096 | backward | 65536 | 1398.50 | 1399.49 | 0.999 | ±0.1 % | yes |
| 4096 | checkpoint backward | 1024 | 60.16 | 60.30 | 0.998 | ±0.3 % |
yes |
| 4096 | checkpoint backward | 4096 | 142.97 | 142.68 | 1.002 | ±0.1 % |
yes |
| 4096 | checkpoint backward | 8192 | 244.47 | 248.39 | 0.984† | ±0.4 %
| yes |
| 4096 | checkpoint backward | 14928 | 418.67 | 418.89 | 0.999 | ±0.3 %
| yes |
| 4096 | checkpoint backward | 15288 | 436.22 | 427.56 | 1.020 | ±0.4 %
| yes |
| 4096 | checkpoint backward | 15566 | 432.98 | 434.36 | 0.997 | ±0.4 %
| yes |
| 4096 | checkpoint backward | 15590 | 433.97 | 433.72 | 1.001 | ±0.3 %
| yes |
| 4096 | checkpoint backward | 16114 | 456.25 | 454.10 | 1.005 | ±0.0 %
| yes |
| 4096 | checkpoint backward | 16132 | 456.07 | 453.70 | 1.005 | ±0.0 %
| yes |
| 4096 | checkpoint backward | 16164 | 458.17 | 453.95 | 1.009 | ±0.1 %
| yes |
| 4096 | checkpoint backward | 16263 | 444.44 | 448.05 | 0.992 | ±0.4 %
| yes |
| 4096 | checkpoint backward | 32768 | 849.78 | 844.07 | 1.007 | ±0.1 %
| yes |
| 4096 | checkpoint backward | 65536 | 1643.62 | 1632.16 | 1.007† | ±0.7
% | yes |
| 5120 | forward | 1024 | 39.01 | 38.93 | 1.002 | ±0.3 % | no |
| 5120 | forward | 4096 | 92.30 | 92.38 | 0.999 | ±0.0 % | no |
| 5120 | forward | 8192 | 159.76 | 160.27 | 0.997 | ±0.0 % | no |
| 5120 | forward | 8193 | 163.22 | 163.64 | 0.997 | ±0.0 % | no |
| 5120 | forward | 14928 | 274.60 | 274.85 | 0.999 | ±0.1 % | no |
| 5120 | forward | 15288 | 285.00 | 285.12 | 1.000 | ±0.1 % | no |
| 5120 | forward | 16263 | 298.32 | 298.36 | 1.000 | ±0.1 % | no |
| 5120 | forward | 32768 | 569.00 | 569.32 | 0.999 | ±0.0 % | no |
| 5120 | forward | 65536 | 1113.40 | 1113.13 | 1.000 | ±0.1 % | no |
| 5120 | backward | 1024 | 59.30 | 59.65 | 0.994 | ±0.0 % | yes |
| 5120 | backward | 4096 | 149.18 | 148.84 | 1.002 | ±0.0 % | yes |
| 5120 | backward | 8192 | 262.54 | 263.16 | 0.998 | ±0.3 % | yes |
| 5120 | backward | 8193 | 272.76 | 262.30 | 1.040 | ±0.2 % | yes |
| 5120 | backward | 14928 | 471.71 | 447.56 | 1.054 | void | yes |
| 5120 | backward | 15288 | 471.09 | 448.25 | 1.051 | ±0.1 % | yes |
| 5120 | backward | 16263 | 500.52 | 481.38 | 1.040 | ±0.3 % | yes |
| 5120 | backward | 32768 | 945.67 | 905.15 | 1.045 | ±0.1 % | yes |
| 5120 | backward | 65536 | 1836.46 | 1771.19 | 1.037 | ±0.1 % | yes |
| 5120 | checkpoint backward | 1024 | 79.02 | 79.39 | 0.995 | ±0.2 % |
yes |
| 5120 | checkpoint backward | 4096 | 181.26 | 181.74 | 0.997 | ±0.1 % |
yes |
| 5120 | checkpoint backward | 8192 | 315.49 | 315.38 | 1.000 | ±0.0 % |
yes |
| 5120 | checkpoint backward | 8193 | 335.00 | 320.48 | 1.045 | ±0.1 % |
yes |
| 5120 | checkpoint backward | 14928 | 566.23 | 535.05 | 1.058 | void |
yes |
| 5120 | checkpoint backward | 15288 | 562.16 | 536.20 | 1.048 | ±0.2 %
| yes |
| 5120 | checkpoint backward | 16263 | 593.94 | 571.33 | 1.040 | ±0.3 %
| yes |
| 5120 | checkpoint backward | 32768 | 1104.13 | 1058.55 | 1.043 | ±0.2
% | yes |
| 5120 | checkpoint backward | 65536 | 2123.30 | 2049.27 | 1.036 | ±0.1
% | yes |
| 7168 | forward | 1024 | 46.90 | 46.78 | 1.003 | ±0.6 % | no |
| 7168 | forward | 4096 | 119.24 | 119.03 | 1.002 | ±0.4 % | no |
| 7168 | forward | 8192 | 214.48 | 214.03 | 1.002 | ±0.2 % | no |
| 7168 | forward | 8193 | 218.08 | 217.49 | 1.003 | ±0.4 % | no |
| 7168 | forward | 14928 | 372.28 | 372.84 | 0.998 | ±0.1 % | no |
| 7168 | forward | 15288 | 386.82 | 386.96 | 1.000 | ±0.1 % | no |
| 7168 | forward | 16263 | 405.55 | 405.02 | 1.001 | ±0.1 % | no |
| 7168 | forward | 32768 | 779.14 | 779.77 | 0.999 | ±0.1 % | no |
| 7168 | forward | 65536 | 1532.54 | 1532.81 | 1.000 | ±0.0 % | no |
| 7168 | backward | 1024 | 75.32 | 74.38 | 1.013 | ±0.3 % | yes |
| 7168 | backward | 4096 | 203.79 | 204.11 | 0.998 | ±0.2 % | yes |
| 7168 | backward | 8192 | 368.10 | 368.79 | 0.998 | ±0.3 % | yes |
| 7168 | backward | 8193 | 376.59 | 368.50 | 1.022 | ±0.1 % | yes |
| 7168 | backward | 14928 | 661.93 | 638.75 | 1.036 | ±0.1 % | yes |
| 7168 | backward | 15288 | 690.97 | 667.00 | 1.036 | ±0.2 % | yes |
| 7168 | backward | 16263 | 726.80 | 706.00 | 1.029 | ±0.3 % | yes |
| 7168 | backward | 32768 | 1435.93 | 1390.41 | 1.033 | ±0.2 % | yes |
| 7168 | backward | 65536 | 2767.91 | 2664.09 | 1.039 | ±0.2 % | yes |
| 7168 | checkpoint backward | 1024 | 97.59 | 96.65 | 1.010 | ±0.1 % |
yes |
| 7168 | checkpoint backward | 4096 | 243.11 | 242.85 | 1.001 | ±0.1 % |
yes |
| 7168 | checkpoint backward | 8192 | 437.72 | 436.62 | 1.003 | ±0.1 % |
yes |
| 7168 | checkpoint backward | 8193 | 451.25 | 442.32 | 1.020 | ±0.0 % |
yes |
| 7168 | checkpoint backward | 14928 | 775.85 | 748.63 | 1.036 | ±0.7 %
| yes |
| 7168 | checkpoint backward | 15288 | 805.82 | 781.36 | 1.031 | ±0.1 %
| yes |
| 7168 | checkpoint backward | 16263 | 842.91 | 822.39 | 1.025 | ±0.4 %
| yes |
| 7168 | checkpoint backward | 32768 | 1631.17 | 1582.73 | 1.031 | ±0.1
% | yes |
| 7168 | checkpoint backward | 65536 | 3126.47 | 3008.53 | 1.039 | ±0.3
% | yes |

Non-deterministic mode, unloaded A/B timing per GPU:

### Non-deterministic mode, B200 (sm_100a, 148 SMs)

B200, sm_100a, 148 SMs, CUDA 13.4 toolkit, PyTorch 2.14.1+cu130.
Per-call time from CUDA events over back-to-back calls, median of 5
groups; speedup = main / this PR.

| H | operation | T | main (us) | this PR (us) | speedup (main / PR) |
|---:|---|---:|---:|---:|---:|
| 5120 | backward | 14928 | 705.8 | 702.5 | 1.005 |
| 5120 | backward | 15288 | 720.7 | 715.6 | 1.007 |
| 5120 | backward | 16263 | 768.7 | 766.2 | 1.003 |
| 5120 | backward | 32768 | 1519.6 | 1500.2 | 1.013 |
| 5120 | backward_finish | 14928 | 480.4 | 479.0 | 1.003 |
| 5120 | backward_finish | 15288 | 488.8 | 486.5 | 1.005 |
| 5120 | backward_finish | 16263 | 526.1 | 523.9 | 1.004 |
| 5120 | backward_finish | 32768 | 1033.0 | 1016.3 | 1.016 |
| 5120 | checkpointed step | 14928 | 1254.4 | 1250.8 | 1.003 |
| 5120 | checkpointed step | 15288 | 1280.0 | 1273.8 | 1.005 |
| 5120 | checkpointed step | 16263 | 1362.9 | 1359.5 | 1.003 |
| 5120 | checkpointed step | 32768 | 2663.9 | 2647.0 | 1.006 |
| 7168 | backward | 14928 | 994.0 | 994.3 | 1.000 |
| 7168 | backward | 15288 | 1012.0 | 1014.0 | 0.998 |
| 7168 | backward | 16263 | 1079.8 | 1082.4 | 0.998 |
| 7168 | backward | 32768 | 2118.2 | 2120.4 | 0.999 |
| 7168 | backward_finish | 14928 | 689.2 | 689.1 | 1.000 |
| 7168 | backward_finish | 15288 | 697.9 | 699.5 | 0.998 |
| 7168 | backward_finish | 16263 | 749.5 | 749.6 | 1.000 |
| 7168 | backward_finish | 32768 | 1449.5 | 1450.5 | 0.999 |
| 7168 | checkpointed step | 14928 | 1749.9 | 1749.0 | 1.001 |
| 7168 | checkpointed step | 15288 | 1774.6 | 1777.6 | 0.998 |
| 7168 | checkpointed step | 16263 | 1893.4 | 1894.3 | 1.000 |
| 7168 | checkpointed step | 32768 | 3719.4 | 3698.7 | 1.006 |

### Non-deterministic mode, GB300 (sm_103a, 152 SMs)

GB300, sm_103a, 152 SMs, CUDA 13.4 toolkit, PyTorch 2.14.1+cu130.
Per-call time from CUDA events over back-to-back calls, median of 5
groups; speedup = main / this PR.

| H | operation | T | main (us) | this PR (us) | speedup (main / PR) |
|---:|---|---:|---:|---:|---:|
| 5120 | backward | 14928 | 678.4 | 675.2 | 1.005 |
| 5120 | backward | 15288 | 693.2 | 688.1 | 1.007 |
| 5120 | backward | 16263 | 739.1 | 733.7 | 1.007 |
| 5120 | backward | 32768 | 1434.9 | 1417.8 | 1.012 |
| 5120 | backward_finish | 14928 | 461.8 | 459.8 | 1.004 |
| 5120 | backward_finish | 15288 | 471.6 | 467.2 | 1.009 |
| 5120 | backward_finish | 16263 | 504.1 | 499.2 | 1.010 |
| 5120 | backward_finish | 32768 | 962.3 | 949.2 | 1.014 |
| 5120 | checkpointed step | 14928 | 1287.2 | 1282.8 | 1.003 |
| 5120 | checkpointed step | 15288 | 1311.1 | 1305.1 | 1.005 |
| 5120 | checkpointed step | 16263 | 1325.6 | 1321.0 | 1.003 |
| 5120 | checkpointed step | 32768 | 2561.3 | 2544.1 | 1.007 |
| 7168 | backward | 14928 | 937.2 | 935.9 | 1.001 |
| 7168 | backward | 15288 | 954.7 | 954.4 | 1.000 |
| 7168 | backward | 16263 | 1015.0 | 1013.7 | 1.001 |
| 7168 | backward | 32768 | 2005.2 | 2006.1 | 1.000 |
| 7168 | backward_finish | 14928 | 640.3 | 635.6 | 1.007 |
| 7168 | backward_finish | 15288 | 650.2 | 646.2 | 1.006 |
| 7168 | backward_finish | 16263 | 691.1 | 687.1 | 1.006 |
| 7168 | backward_finish | 32768 | 1357.4 | 1357.5 | 1.000 |
| 7168 | checkpointed step | 14928 | 1761.0 | 1758.7 | 1.001 |
| 7168 | checkpointed step | 15288 | 1795.1 | 1795.3 | 1.000 |
| 7168 | checkpointed step | 16263 | 1813.5 | 1813.5 | 1.000 |
| 7168 | checkpointed step | 32768 | 3558.9 | 3561.0 | 0.999 |


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added dynamic row-count backward-processing options for Cake training
at hidden sizes 5120 and 7168, with expanded coverage across supported
GPU architectures and token ranges.
* Added additional backward-reduction and slab-kernel variants for
larger hidden sizes.
* **Bug Fixes**
* Improved compatibility of backward kernels with newer GPU
architectures.
* Updated token loading and shared-memory addressing in selected slab
kernels.
* **Refactor**
* Removed standalone backward-prepare kernels for hidden sizes 5120 and
7168; their prior interfaces are no longer available.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [b55d50e](https://github.com/flashinfer-ai/flashinfer/commit/b55d50edc070024833dabc60461c8d98ec083c3d)

- **作者**: Ka-Hyun Nam
- **时间**: 2026-11-10T00:18:18Z
- **提交信息**: fix(quantization): route NVFP4 quantize to the TMA kernel from m=2048 on SM107 (#9292)

## 📌 Description

#6691 sends NVFP4 quantize to the TMA kernel only for inputs of at least
32 MiB with a work tile per SM. That threshold was measured on B200 and
RTX 5080, and on SM107 it is too high: BF16 3072x3072 (18 MiB) went from
6.91 us to 9.95 us (+44%), the regression reported against 725a39e for
DeepSeek-V4-Pro nvfp4_quantize on Rubin.

On SM107 the TMA kernel is faster for every input with m >= 2048 and
slower only at m = 1024, so this PR routes SM107 to the TMA kernel for m
>= 2048 and leaves every other architecture on the #6691 rule.

Forced-path sweep on SM107 (216 SMs, CUDA 13.5), 128x4 layout, CUPTI
kernel time, cold L2, median, vectorized -> TMA in us:

| input | m x n | MiB | vectorized | TMA | TMA / vectorized |
|---|---|---|---|---|---|
| BF16 | 1024 x 3072 | 6 | 5.15 | 5.95 | 1.16 |
| BF16 | 2048 x 3072 | 12 | 7.62 | 6.46 | 0.85 |
| BF16 | 3072 x 3072 | 18 | 9.92 | 6.94 | 0.70 |
| BF16 | 4096 x 3072 | 24 | 12.29 | 8.13 | 0.66 |
| BF16 | 2048 x 7168 | 28 | 11.39 | 10.30 | 0.90 |
| BF16 | 1024 x 7168 | 14 | 7.10 | 9.70 | 1.36 |
| FP8 | 2048 x 3072 | 6 | 5.73 | 5.34 | 0.93 |
| FP8 | 4096 x 4096 | 16 | 10.50 | 8.86 | 0.84 |

The full sweep covers BF16 and FP8, m from 1024 to 16384 and n from 2048
to 32768. TMA wins at every m >= 2048 (ratio 0.47-1.00) and loses at
every m = 1024 (ratio 1.04-1.64).

After the change, BF16 3072x3072 takes 6.91 us again, and the 1024-row
shapes keep the vectorized kernel (1024 x 3072 5.12 us, 1024 x 7168 7.10
us).

## 🔍 Related Issues

Follow-up to #6691.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing.

`(2048, 3072)` joins the TMA parity shapes, so SM107 exercises the new
route. `tests/utils/test_fp4_quantize.py -k tma`: 1574 passed on an
SM107 board (CUDA 13.5).

Not measured: B200 and other architectures (their path is unchanged
apart from reordering the checks), batched input with m = 1024 on SM107
(stays on the vectorized kernel), and the VR200 NVL72 part (the numbers
above come from a GR100 bring-up board).

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* Quantization uses an optimized path on supported SM107 hardware
starting at 2,048 rows for the 128x4 layout and 3,072 rows for other
layouts.
* On other supported hardware, the path retains its existing minimum
input-size and workload requirements.
* Inputs with fewer than 1,024 rows or column counts that do not match
the supported chunk size are not eligible.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Sonnet 5.5 <noreply@anthropic.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-11-11
**监控日期**: 2026-11-10
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4803
- **最后更新**: 2026-11-11T01:24:46Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 2
- **主要提交者**: FV SuperAgent, William Lin

## AI分析总结

# FastVideo 昨日提交分析（2025-XX-XX，共3笔）

## 1. 主要更新类型
- **功能新增**：重新引入 PAN2（PAN 2）视频生成模型，覆盖文本生成视频（T2V）与图像生成视频（I2V）两条推理管线。
- **文档更新**：README 新增 "day-0 PAN 2 support" 公告与 news 归档；补充 Security Policy、Contributing Guide、Code of Conduct 等社区治理文档。
- **性能优化与安全加固**：PAN2 重加入时附带推理优化（inference optimizations）与防护机制（guardrails）。

## 2. 关键变更点与项目整体方向的关系
- PAN2 的回归直接对应 FastVideo 作为"新模型 day-0 快速推理支持平台"的定位——README 中的文档站、Cookbook、Quick Start 与 Weekly Dev Meeting 均强调社区协作与快速跟进前沿模型。
- 推理优化延续了项目核心卖点：以高效推理（Fast Inference）支撑视频生成模型落地。
- 社区治理文档（安全政策、贡献指南、行为准则）表明项目正从个人实验室项目向成熟开源社区演进，配合 Slack/周会等既有协作渠道，提升外部贡献门槛与安全性。

## 3. 对项目的影响与潜在意义
- **生态位巩固**：day-0 级别支持 PAN2，强化了 FastVideo "新模型首发推理加速" 的品牌心智，吸引更多模型作者与用户采用。
- **质量与安全双轨**：guardrails 的加入说明项目开始重视生成内容安全与推理鲁棒性，为商业化/大规模部署铺路。
- **社区可持续性**：正式的治理文件有助于规范 PR 流程、明确安全漏洞上报路径，降低维护成本并吸引更多贡献者。

## 4. 值得关注的技术点
- PAN2 推理优化的具体手段（量化、算子融合、KV/特征缓存、并行策略等）值得后续深入 commit 内容查看。
- "Re-add" 措辞暗示此前曾因质量或性能原因移除过 PAN2，此次重加入门包含 guardrails，体现项目对模型质量的把关策略。
- 文档提交与功能提交分批分离（#2029 vs #2086/#2087），反映团队规范的 PR 拆分习惯。

## 5. 基于README背景对项目发展的影响
FastVideo 由 Hao AI Lab 维护，README 中的文档站、Quick Start、Cookbook 与周会链接构成完整的开发者体验闭环。本次提交组同时推进**新模型能力**（PAN2 T2V/I2V）与**社区基础设施**（治理文档），与项目"快速推理 + 开源协作"的双主线高度一致。短期看，PAN2 支持可立即提升项目在新模型覆盖上的竞争力；长期看，治理文档为项目规模化协作打下基础，有助于在视频生成推理这一快速演进的赛道中保持活跃度与可信度。

## 详细提交记录

### [4deb3a5](https://github.com/hao-ai-lab/FastVideo/commit/4deb3a50fff8fff8c469d686c8e40fe6d9b03551)

- **作者**: William Lin
- **时间**: 2026-11-10T17:16:04Z
- **提交信息**: [docs] Announce day-0 PAN 2 support in the README and news archive (#2087)

### [0dc6ce5](https://github.com/hao-ai-lab/FastVideo/commit/0dc6ce5d0af849293ed030f92376f4c28ce5bb8e)

- **作者**: FV SuperAgent
- **时间**: 2026-11-10T16:26:51Z
- **提交信息**: [docs] Add security policy, contributing guide and code of conduct (#2086)

Co-authored-by: Aryan Kumar <156166681+aryan5v@users.noreply.github.com>

### [fcbe895](https://github.com/hao-ai-lab/FastVideo/commit/fcbe895b5591123449e64cf0528a83e1532280d4)

- **作者**: William Lin
- **时间**: 2026-11-10T10:50:19Z
- **提交信息**: [new-model] Re-add PAN2 text-to-video and image-to-video, with inference optimizations and guardrails (#2029)

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-11-11
**监控日期**: 2026-11-10
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34902
- **最后更新**: 2026-11-10T22:58:05Z

## 提交统计

- **昨日提交总数**: 8
- **提交者数量**: 8
- **主要提交者**: Steven Liu, YiYi Xu, drbh

## AI分析总结

## huggingface/diffusers 昨日提交批次分析（8 项提交）

### 1. 主要更新类型
- **功能新增**：PAN 2 与 MiniMax H3-Image 两套完整模型/管线的模块化接入
- **文档更新**：分布式推理文档重构、Cosmos3 FP8 文档化、链接与 URL 修复
- **Bug/体验修复**：Flash Attention 2 版本偏好修正、doc-builder 渲染数学公式

### 2. 关键变更点及与项目方向的关系
- **PAN 2（#15202）**：29B MoT 视频-文本双流 Transformer，t2v/i2v 工作流，配套 Qwen3.5 文本编码器与 Wan2.2 VAE，支持 Ulysses 上下文并行、安全护栏检查、转换脚本与测试——体现了项目向**超大规模视频生成**与**模块化管线（modular pipelines）架构**推进的方向。
- **MiniMax H3-Image（#15230）**：文本生图与图像编辑的完整栈（DiT、2D ViT 解码 Autoencoder、euler_update_form 调度器），并引入 `additional_denoiser_kwargs` 转发机制与未使用字段告警——展示了**新架构组件的标准化接入范式**与管线健壮性改进。
- **分布式推理文档拆分（#15172）** 及其后续链接修复：文档结构化重组，配套 PAN 2 等大模型的并行推理需求。
- **Cosmos3 FP8 文档**：补充量化检查点的独立仓库指引，呼应实际部署中的显存优化需求。

### 3. 影响与潜在意义
- 一天内落地两个完整模型栈（均含转换、测试、文档全流程），强化了 diffusers 作为**统一模型接入平台**的地位，降低新模型的集成成本。
- 周边修复（死链、FA2 偏好、数学渲染）虽小，但直接保障 CI 文档检查与开发者体验，反映项目维护成熟度高。
- denoiser 字段校验告警是可推广的**通用健壮性改进**，惠及所有自定义管线。

### 4. 值得关注的技术点
- **上下文并行（Ulysses）** 与安全性检查（pan2-guardrail）在 29B 级模型上的工程落地方式。
- **模块化管线**中 block 拆装模式（如通过 `blocks.sub_blocks.pop("decode")` 跳过解码）取代硬编码快捷路径，更灵活也更可测试。
- MiniMax H3 的**多步采样头设计**（one output head per sampling step）与 2D ViT 解码器结构，值得与现有 DiT 架构对比参考。
- 文本编码器/VAE 的**本地副本化**策略（converter 内嵌而非外部索引），提升发布仓库的自洽性。

### 5. 对项目发展的整体意义
README 明确该项目是 HuggingFace 团队维护的扩散模型库。这些提交表明项目当前的核心节奏是：**（a）以模块化管线架构快速吞吐新的大模型（视频与图像双线并行）；（b）为超大模型配套分布式/量化推理的文档与工程支持；（c）通过持续的小修与自动化测试维持文档和链接健康**。三者结合，使 diffusers 在模型覆盖面与生产可用性上同步领先，持续巩固其作为开源扩散模型生态基础设施的角色。

## 详细提交记录

### [f598e6e](https://github.com/huggingface/diffusers/commit/f598e6e6a99528858b962c1399c45b59a6c25484)

- **作者**: Yiming Zhao
- **时间**: 2026-11-10T19:29:01Z
- **提交信息**: Document Cosmos3 Nano, Super, and Edge FP8 as standalone repos (#15236)

Document Cosmos3 Nano, Super, and Edge FP8 as standalone repos.

The published checkpoints are nvidia/Cosmos3-*-FP8 on main. Edge has no fp8 branch, and Super-Image2Video still loads revision=fp8.

Co-authored-by: YiYi Xu <yixu310@gmail.com>

### [b83cc0a](https://github.com/huggingface/diffusers/commit/b83cc0a692dfa38aa3d30be50fd22b1142427bad)

- **作者**: YiYi Xu
- **时间**: 2026-11-10T19:22:15Z
- **提交信息**: [docs] Fix the PAN 2 context parallelism link after the distributed i… (#15238)

[docs] Fix the PAN 2 context parallelism link after the distributed inference docs split

#15172 moved the section to `optimization/context_parallelism.md`, so the old anchor no longer exists and the
docs link check fails on main.

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [19ffc4c](https://github.com/huggingface/diffusers/commit/19ffc4c570b36e18db70c1b8bd4f64c09901b42f)

- **作者**: Mishig
- **时间**: 2026-11-10T18:50:08Z
- **提交信息**: Bump doc-builder to render math in docstring descriptions (#15223)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [87b6f2d](https://github.com/huggingface/diffusers/commit/87b6f2dde07d28d1ace7130be403869483944d8e)

- **作者**: Nabid Nur
- **时间**: 2026-11-10T18:11:38Z
- **提交信息**: Update dead Kaggle Cats vs Dogs download URL in create_dataset doc (#15231)

Update dead Kaggle Cats vs Dogs download URL (3367a -> 5340)

### [8069682](https://github.com/huggingface/diffusers/commit/8069682140c675652a886736121f4e3b86f4187c)

- **作者**: Steven Liu
- **时间**: 2026-11-10T17:42:28Z
- **提交信息**: [docs] Distributed inference (#15172)

* split distributed inference

* fix style

* feedback - unite tp pages

* feedback - use local rank

* remote inference, serve concurrent requests

### [875373a](https://github.com/huggingface/diffusers/commit/875373ac7f5856071e345a3e394c74efccc6b9e6)

- **作者**: Sayak Paul
- **时间**: 2026-11-10T16:22:35Z
- **提交信息**: MiniMax H3 Image (#15230)

* Add MiniMax H3-Image (text-to-image and image editing)

- MiniMaxH3ImageTransformer2DModel: the MiniMax-H3 DiT without audio, with one output head per sampling step
- AutoencoderKLMiniMaxH3Image: the MiniMax-H3 encoder with a 2D ViT decoder
- MiniMaxH3ImageBlocks / MiniMaxH3ImageModularPipeline in modular_pipelines/minimax_h3_image
- MiniMaxH3Scheduler: new euler_update_form config
- conversion script (--version image), tests and docs

Co-Authored-By: Claude Fable 5.1 <noreply@anthropic.com>

* Add the H3-Image integration example scripts

Co-Authored-By: Claude Fable 5.1 <noreply@anthropic.com>

* Keep a copy of the text encoder in the H3-Image repository

The converter copies it in from --text_encoder_path instead of pointing the index at MiniMax-H3.

Co-Authored-By: Claude Fable 5.1 <noreply@anthropic.com>

* Address review feedback

- docs: separate text-to-image and editing snippets; drop the CPU-generator note
- AutoencoderKLMiniMaxH3Image: inline `_encode_tile`
- tests: standalone block tests in their own class; the scheduler's velocity
  form is checked in the pipeline tests instead of a scheduler test file;
  `test_edit_reference_noise` compares latents rather than the 8-bit image

Co-Authored-By: Claude Fable 5.1 <noreply@anthropic.com>

* Warn about denoiser_input_fields the transformer does not take

Tagged fields are forwarded to the transformer by parameter name. A field
whose name is not a parameter is not used; the loop denoiser now says so
once, on the first step. `latents` and `prompt_embeds` go in as
`hidden_states` and `encoder_hidden_states`, so they are left out of the
check. The forwarded dict is renamed `additional_denoiser_kwargs`, since it
holds whatever is tagged, not only the layout fields.

Co-Authored-By: Claude Fable 5.1 <noreply@anthropic.com>

* Merge pull request #3 from huggingface/prompt-enhancement

Prompt enhancement

* correct memory consumption.

* remove integration notes

* change references to vae_diffusers and transformer_diffusers.

---------

Co-authored-by: yiyixuxu <yixu310@gmail.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [74fb49b](https://github.com/huggingface/diffusers/commit/74fb49b5506a6960d55de0f7e6f4e0631213dc63)

- **作者**: drbh
- **时间**: 2026-11-10T09:23:04Z
- **提交信息**: fix: prefer latest flash attn2 (#15000)

fix: reapply changes on latest

### [a17ab72](https://github.com/huggingface/diffusers/commit/a17ab726a823aef1868af3b54a84af37dd1efd6c)

- **作者**: Yi Gu
- **时间**: 2026-11-10T08:47:35Z
- **提交信息**: [Modular] Add PAN 2 (#15202)

* Add PAN2 text-to-video and image-to-video

PAN2 transformer (29B MoT, video and text streams) and a modular pipeline with
t2v and i2v workflows, using a Qwen3.5 text encoder and the Wan2.2 VAE:
- standard CFG, 50 steps by default
- context parallelism (Ulysses)
- optional safety checker on the prompt and the generated video (pan2-guardrail), following Cosmos
- checkpoint conversion script, docs, model and pipeline tests on a tiny checkpoint

* PAN2: address self-review and overnight test findings

- return annotations on all blocks and the rotary embedding
- "video" wording in block inputs and the auto docstrings
- reset stateful cache hooks after each call, as Cosmos3 does
- move context_type_embedding to the text device (device_map="auto")
- test that latent output skips decoding and the video check
- document the custom safety checker contract; dtype= in the conversion script

Signed-off-by: Yi Gu <Yi.Gu@mbzuai.ac.ae>

* PAN2: address review comments

- Keep only the default-on safety-checker test and drop the dummy checker, since the PAN2 guardrail package tests the checker itself (test_modular_pipeline_pan2.py).
- Raise a ValueError when user-provided latents do not have the expected shape (PAN2PrepareLatentsStep).
- Write the full pipeline in the conversion script only with --save_pipeline, with --text_encoder_path and --vae_path defaulting to Qwen/Qwen3.5-9B and Wan-AI/Wan2.2-TI2V-5B-Diffusers, so the text encoder and VAE can no longer be given partially.

* drop manual "skip decoder" pattern

Co-authored-by: YiYi Xu <yixu310@gmail.com>

* PAN2: drop the test of the removed output_type="latent" decoder shortcut

The decoder step no longer returns the latents for output_type="latent"; to get them, pop the decode block (blocks.sub_blocks.pop("decode")).

* PAN2: derive height and width from image_latents for image-to-video

Add PAN2Image2VideoInputStep to the image-to-video denoise blocks, after the text input step. As Anima's image input step does, it takes `height` and `width` from the shape of `image_latents`, and raises a ValueError when they are passed and do not match it. The VAE encoder and prepare-latents steps no longer declare 704 x 1248 as input defaults and fall back to the pipeline's `default_height` / `default_width` (from `default_sample_height` / `default_sample_width`) at run time, as in Wan, so that these defaults do not override the size of `image_latents`. Test the image-to-video workflow from standalone-encoded `image_latents`.

* PAN2: stop declaring the guider as a component of the text encoder step

The guider belongs to the denoise step. In the full pipeline, it decides through `requires_unconditional_embeds` whether the negative prompt is encoded, with a warning when a `negative_prompt` is given but guidance does not use it. Standalone, the text encoder has no guider and still encodes the negative prompt, since the PAN2 denoise step uses classifier-free guidance by default.

* use "flash_hub" instead of "flash" in PAN2 doc

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

* PAN2: point the guardrail links to github.com/ifm-ai/pan2-guardrail

* PAN2: describe PAN2 as a foundation world model and the guardrails without their models

Describe PAN2 as a foundation world model (intro, pipeline and transformer docstrings, conversion script) instead of a video generation model. Describe the guardrails as checking the prompt and each generated video, without naming the guard models, and say that turning them off with `disable_safety_checker()` is at your own risk (docs, error messages and a new docstring).

* PAN2: adapt safety checker code and doc to our policy

* PAN2: use the tiny test checkpoint from hf-internal-testing

* PAN2: write the model name as PAN 2 in docs, docstrings and messages

* PAN2: no guidance on the given first frame of image-to-video; default CFG 2.5 and shift 9.0

* PAN2: run the timestep embedder and modulation in float32

* PAN2: drop the test_save_from_pretrained override

* PAN2: default to the released negative prompt, its time ranges set to the clip

* PAN2: pin the workflow defaults in the modular pipeline tests

* PAN2: load the safety checker in load_components and move it with the pipeline

The guardrail is loaded once by `load_components()` when the checks are on and the package is
installed, and `pipe.to()` moves it with the other components. The text encoder and decoder steps
no longer load it or move it between devices during a call; they only raise when the checks are on
and it is not loaded.

* PAN2: drop the __call__ override

* PAN2: take height and width only from image_latents in the image-to-video input step

* PAN2: drop the revision note from the docs

* PAN2: encode the negative prompt standalone only when it is passed

* PAN2: register the safety checker as a component

---------

Signed-off-by: Yi Gu <Yi.Gu@mbzuai.ac.ae>
Co-authored-by: YiYi Xu <yixu310@gmail.com>
Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-11-11
**监控日期**: 2026-11-10
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


**报告日期**: 2026-11-11
**监控日期**: 2026-11-10
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13354
- **最后更新**: 2026-11-10T17:23:10Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Jinyan Ye

## AI分析总结

## 提交分析：modelscope/DiffSynth-Studio

### 1. 主要更新类型
- **功能新增 + 工具化/自动化增强**：为仓库添加了 Agent Skills（智能体技能），用于辅助 AI 编码代理（如 Claude Code、Copilot 等）更好地理解和操作该代码库。

### 2. 关键变更点及与项目方向的关系
- **新增 Agent Skills 文件**：通常包括自定义的技能定义文件（如 `.claude/skills/`、`.github/copilot-instructions.md` 或类似配置），指导 AI 代理如何正确遵循项目的开发规范、构建流程和测试约定。
- **与项目方向的关联**：DiffSynth-Studio 是一个面向扩散模型合成（Diffusion Synthesis）的图像/视频生成工具库，涉及大量复杂的模型加载、Pipeline 编排和 GPU 推理逻辑。添加 Agent Skills 表明项目维护者希望降低 AI 辅助开发的门槛，使外部贡献者和内部开发都能借助 AI 工具更准确地修改代码，减少因不了解项目结构而引入的错误。
- 这反映了开源项目在 AI 时代的一种趋势：**将项目知识显式化、结构化**，使 AI 成为真正的协作者而非简单的补全工具。

### 3. 对项目的影响和潜在意义
- **短期影响**：开发者使用 AI 编码工具时，能更快速上手项目，产出更符合项目规范的 PR，从而提高合并效率。
- **长期意义**：随着贡献者增多，这类 Agent Skills 可以作为"活文档"持续演进，帮助项目在快速迭代中保持代码质量和架构一致性，同时降低维护者的代码审查负担。
- **社区层面**：降低贡献门槛，鼓励更多开发者参与扩散模型相关的功能开发和实验。

### 4. 值得关注的技术点
- **Agent Skills 的具体形式**：需关注是采用 Claude 的 Skills 格式、GitHub Copilot 的 Instructions 还是通用的 AGENTS.md 约定，这决定了其兼容性和可移植性。
- **技能内容的覆盖范围**：是否涵盖了模型注册、Pipeline 扩展、训练脚本配置等核心开发场景，以及是否包含性能调优（如显存优化）的指导。
- **是否附带 CI/工具链更新**：Agent Skills 有时会配套自动化校验脚本，确保 AI 生成的代码符合格式和测试要求。

### 5. 对项目发展的整体影响
基于 README 可知，DiffSynth-Studio 是 ModelScope 生态下的重点项目，目标是提供一站式的扩散模型合成方案（包括图像和视频生成）。此次提交虽然不直接新增模型能力或修复 Bug，但属于**开发者体验（DX）层面的重要基建**：通过将项目知识编码为 AI 可消费的技能文件，它使后续的功能迭代、Bug 修复和文档完善都能以更高的效率推进。这在一定程度上为项目未来更快地接入新模型、扩展新功能（如多模态合成、实时视频生成等）奠定了更好的协作基础，是项目走向成熟化、工程化管理的一个标志性动作。

## 详细提交记录

### [7f61872](https://github.com/modelscope/DiffSynth-Studio/commit/7f6187275d45eb715bbc3e49e7ae5399f7fcdb1c)

- **作者**: Jinyan Ye
- **时间**: 2026-11-10T09:16:46Z
- **提交信息**: Add agent skills (#1813)

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-11-11
**监控日期**: 2026-11-10
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 38700
- **最后更新**: 2026-11-11T01:24:43Z

## 提交统计

- **昨日提交总数**: 93
- **提交者数量**: 60
- **主要提交者**: Yue Fei, Po-Han Huang (NVIDIA), Alan Kao

## AI分析总结

# SGLang 昨日提交总结（93 条）

## 一、主要更新类型
功能新增约 30 条，覆盖新模型接入、多硬件支持与 API 扩展；性能优化约 22 条，集中于 NVIDIA/AMD/NPU 内核调优与解码路径；Bug 修复约 30 条，涉及内存缓存、调度、CUDA graph、分布式推理的稳定性；其余为重构与 CI、测试、文档、CODEOWNERS 维护。

## 二、关键变更
模型覆盖显著扩展：接入 MiniMax-H3-Image、Longcat2.0、Qwen3.8-Flash-Next、Kimi-K3 与 K3.1（wire 格式、thinking 映射、流式工具调用）、DeepSeek-V4.1-Flash、Qwen3-Next、gemma4，以及 Z-Image、FLUX.3 等扩散模型。
多硬件三线并进：AMD 侧新增 GPTQ/AutoRound INT4、gpt-oss W4A8 混合量化、muse-spark ROCm day0、MI35x MXFP4 与 DSpARK、gfx950 确定性 matmul；NPU 侧新增 GLM-5.3 测试、DSA 分片、MLA 混合分块、mxfp8 KV cache；NVIDIA 侧密集落地 SM10x/12x 专用内核、sm_107a、fp8 Triton GEMM 与 FlashInfer CuTe DSL autotune。
内存与分布式加固：unified memory 需求式抽象、容量查询、双重释放检测、写后读屏障、行状态重置；hicache 存储确认、worker 死亡处理与修复；PD/PP 共识校验、PP 循环屏障与事件记录、NIXL TP 异构 KV 打包。
服务化能力补强：score/embedding 支持原始向量输出与 rid 打分、调度决策日志、gRPC 编排器发现上报、访问日志媒体计数，以及 sgl-router 的 StepFun 模型渲染与异步 worker 修正。

## 三、项目影响与潜在意义
统一内存与 hicache 一系列修复显著降低长序列、多请求场景下静默数据损坏的风险，配合 MoE 非法内存访问、cuda_graph 重放输入保留、ZeroMQ 等修复，夯实了长时运行的生产可用性。量化内核自 Triton 迁移至 JIT 内核（MXFP8），减少外部依赖并提升可维护性。AMD、NPU、Muse Spark 的 day0 支持表明项目正从单点性能领先转向全栈平台化，降低跨硬件部署门槛；embedding/score API、gRPC 发现与路由能力的补强，配合 CODEOWNERS 和 MI35x 精度门禁，说明项目正由"推理引擎"向完整的模型服务基础设施过渡，质量回归体系亦趋成熟。

## 四、值得关注的技术点
JIT 内核替代 Triton 的自研量化趋势；CuTe DSL/CUTLASS 架构规范化，含 TMEM 释放顺序修复与 sm_100f 模块解耦；DSpARK 系列构成延迟 draft KV 写入、RAGGED top-k 变换、BF16 状态验证的完整投机解码优化链，另有语法拒绝时剪枝 draft 分支的健壮性处理与 MXFP8 draft lm_head 可选项；统一内存需求式抽象为异构内存调度打基础；CUDA Graph 捕获期间暂停 GC 解决了图捕获与垃圾回收的竞争；gfx950 上的 batch-invariant 确定性 matmul 满足可复现部署需求。此外，大量 Claude/Copilot 协同署名提交显示 AI 辅助开发已深度融入工程流程，需要更严格的 CI 把关。

## 五、整体展望
SGLang 正沿三条主线推进：持续压榨 NVIDIA 各代架构的内核级性能以巩固速度标杆；系统性补齐 AMD/NPU 多后端能力以扩张硬件版图；通过内存、缓存、分布式与调度路径的深度修复夯实大规模生产稳定性。文档与 CLI 指南的同步完善降低了使用门槛，共同支撑其在 LLM 与多模态高速推理领域的平台化领先地位。

## 详细提交记录

### [76589d6](https://github.com/sgl-project/sglang/commit/76589d6fde51c4145a862de652be6f3ec4dff43b)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-10T23:43:16Z
- **提交信息**: [Refactor] scheduler: Each request records the list that holds it (#49623)

### [51401ba](https://github.com/sgl-project/sglang/commit/51401babd16ead3e5ea39f6c5a4daba050066872)

- **作者**: Baizhou Zhang
- **时间**: 2026-11-10T23:31:00Z
- **提交信息**: [Refactor] quantization: Quantize MXFP8 weights with a JIT kernel instead of triton_kernels (#49659)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [187fdba](https://github.com/sgl-project/sglang/commit/187fdba29c569915d5770145df6d16bda0a8ba99)

- **作者**: em-dreyer
- **时间**: 2026-11-10T23:27:09Z
- **提交信息**: [CI] megakernel: Run sgl-nvidia-mega PRs' tests on SGLang's GB300 runners (#49642)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [c67437c](https://github.com/sgl-project/sglang/commit/c67437c22ef1fac4e7b77928f80b99c2d1fe8f78)

- **作者**: Tri Dao
- **时间**: 2026-11-10T23:16:29Z
- **提交信息**: [Perf] [NVIDIA] dsv41: Gather 16 local Engram rows per program on SM103 and SM107 (#48731)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [97abea6](https://github.com/sgl-project/sglang/commit/97abea64deadeb9bdd8a802a23f53079c896dd81)

- **作者**: Chao Shi
- **时间**: 2026-11-10T23:05:18Z
- **提交信息**: [Fix] PD/PP: Fix consensus checker failure while using PP prefill (#46548)

### [680b626](https://github.com/sgl-project/sglang/commit/680b626c6a3266192ee6bad922389a9348e1f09a)

- **作者**: Chunan Zeng
- **时间**: 2026-11-10T23:04:20Z
- **提交信息**: [Fix] test: pin speculative_dspark_lm_head_dtype in the resolvable-field whitelist (#49647)

Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>

### [dec8242](https://github.com/sgl-project/sglang/commit/dec824224503b129c210a21275e4143b5d231658)

- **作者**: Chunan Zeng
- **时间**: 2026-11-10T23:00:30Z
- **提交信息**: [Perf] [NVIDIA] unquant: Re-land low-M BF16 autotune via FlashInfer CuTe DSL mm_bf16 (#49139)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [4da93c2](https://github.com/sgl-project/sglang/commit/4da93c2318c1a594c4a1e299e069efa8c1347bdf)

- **作者**: Kangyan-Zhou
- **时间**: 2026-11-10T22:58:34Z
- **提交信息**: [Feat] sgl-router: Render StepFun (Step-3.5-Flash, Step-3.7-Flash, Step-5-Preview) through sglang-processor (#49392)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [7dc1e38](https://github.com/sgl-project/sglang/commit/7dc1e38e5338b196253d02aae0045c1a9ae8c633)

- **作者**: Shuwen Wang
- **时间**: 2026-11-10T22:57:04Z
- **提交信息**: [Feat] linker: Support Kimi-K3.1 DSA, MLA draft and DCP pools in the direct linker (#49355)

Co-authored-by: Baizhou Zhang <56809903+Fridge003@users.noreply.github.com>
Co-authored-by: Yuhao Yang <47235274+yhyang201@users.noreply.github.com>
Co-authored-by: Khoa Pham <264503018+kpham-sgl@users.noreply.github.com>
Co-authored-by: kpham-sgl <khoa.pham@radixark.ai>

### [4a0351e](https://github.com/sgl-project/sglang/commit/4a0351e8495cc952dafce1dc416c1b485ba3c503)

- **作者**: Kangyan-Zhou
- **时间**: 2026-11-10T22:55:18Z
- **提交信息**: [Fix] sgl-router: Render and tokenize off the async workers (#49606)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [ba0454f](https://github.com/sgl-project/sglang/commit/ba0454f70f3ec47349bb8f3f53ed79c078edbdbe)

- **作者**: Clint
- **时间**: 2026-11-10T22:42:29Z
- **提交信息**: [Feat] [AMD] quantization: enable GPTQ and AutoRound INT4 checkpoints (#42119)

Co-authored-by: Clint Greene <7388379+clintg6@users.noreply.github.com>
Co-authored-by: Hubert Lu <Hubert.Lu@amd.com>

### [a6f190e](https://github.com/sgl-project/sglang/commit/a6f190e8fe440985d28d88daee43a76662081ca7)

- **作者**: Wookje Han
- **时间**: 2026-11-10T22:25:18Z
- **提交信息**: [Perf] NIXL: KV packing for TP-heterogeneous transfer (Muse Spark Open) (#44615)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Po-Han Huang <pohanh@nvidia.com>

### [3fa7109](https://github.com/sgl-project/sglang/commit/3fa710998d175a7ffa11d118f5b58395134755d7)

- **作者**: Shangming Cai
- **时间**: 2026-11-10T22:17:36Z
- **提交信息**: [Fix] spec: Prune the draft branch instead of crashing when the grammar rejects a token (#48117)

### [2145321](https://github.com/sgl-project/sglang/commit/214532133bcf8a632cb63ed6b98bc35e871bdfc0)

- **作者**: Yuhao Yang
- **时间**: 2026-11-10T22:15:12Z
- **提交信息**: [Fix] dsa: Give each FlashMLA decode graph its own schedule for native-head kernels (#49616)

Co-authored-by: Xiaoyu Zhang <35585791+BBuf@users.noreply.github.com>

### [6d12127](https://github.com/sgl-project/sglang/commit/6d12127cbb61a3acb51f24b0c83298d6edea1af4)

- **作者**: Yuwei An
- **时间**: 2026-11-10T21:54:43Z
- **提交信息**: [CI] docker: Follow Mega main for nightly and pin releases (#49410)

### [791a654](https://github.com/sgl-project/sglang/commit/791a654049d026775fd90b40042c88b1c13181ac)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-10T21:52:07Z
- **提交信息**: [Feat] kimi-k3: Shape chat responses to the K3 wire format (#48777)

### [789db63](https://github.com/sgl-project/sglang/commit/789db63fdadf457d31aad63a39458596453c9801)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-10T21:48:53Z
- **提交信息**: [Refactor] scheduler: Move a request between owner lists in one call (#49496)

### [9fdd392](https://github.com/sgl-project/sglang/commit/9fdd39206d13d875c93679eb4808a29e8f978e36)

- **作者**: Chunan Zeng
- **时间**: 2026-11-10T21:22:07Z
- **提交信息**: [Perf] dspark: opt-in MXFP8 draft lm_head on SM10x via --speculative-dspark-lm-head-dtype (#49595)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [3d04a48](https://github.com/sgl-project/sglang/commit/3d04a48798e5698deee5ac31bd9a82f69c2ea7da)

- **作者**: weireweire
- **时间**: 2026-11-10T21:16:40Z
- **提交信息**: [Perf] [NVIDIA] dsv41: Fork the decode attention mHC mix at the MegaAttention core (#49321)

Co-authored-by: weireweire <20922698+weireweire@users.noreply.github.com>

### [10e5008](https://github.com/sgl-project/sglang/commit/10e5008141adbffc4a28481e8c3347ce4b5183ff)

- **作者**: Shuwen Wang
- **时间**: 2026-11-10T21:14:30Z
- **提交信息**: [Fix] linker: Renew Mooncake read leases that lapse during a load (#49043)

Co-authored-by: Baizhou Zhang <56809903+Fridge003@users.noreply.github.com>

### [d2e30c7](https://github.com/sgl-project/sglang/commit/d2e30c7e11a4ac1255383356fe5cba8a92bbf481)

- **作者**: Yichi Zhang
- **时间**: 2026-11-10T21:12:53Z
- **提交信息**: [Feat] cli: Add the CLI Guide (#49081)

### [418f4db](https://github.com/sgl-project/sglang/commit/418f4db7debc90a95a2d26e919aee50b8551cc4c)

- **作者**: zijie
- **时间**: 2026-11-10T20:49:26Z
- **提交信息**: [Feat] [AMD] muse-spark: Add the ROCm day0 implementation (#47371)

Co-authored-by: 1am9trash <1am9trash@gmail.com>
Co-authored-by: HAI <hixiao@gmail.com>
Co-authored-by: Zijie Chen <300606707+zijiecode@users.noreply.github.com>
Co-authored-by: jacky.cheng <yichiche@amd.com>

### [be4d8b8](https://github.com/sgl-project/sglang/commit/be4d8b857c548ab0d3da680fac38d39d667de512)

- **作者**: Lee Nau
- **时间**: 2026-11-10T20:48:05Z
- **提交信息**: [Fix] bench: Check the chat template on the tokenizer the benchmark loads (#49573)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [946cc59](https://github.com/sgl-project/sglang/commit/946cc59d11fe7a0a1b2f6f71082bde85443b0bd4)

- **作者**: Bingxu Chen
- **时间**: 2026-11-10T20:13:31Z
- **提交信息**: [CI] [AMD] nightly-benchmark: Run InferenceX's AgentX DeepSeek-V4.1-Flash curve on MI35x (#49443)

Co-authored-by: Michael <13900043+michaelzhang-ai@users.noreply.github.com>

### [9855788](https://github.com/sgl-project/sglang/commit/98557885591f69b6105374c2da4b453d3c4b05f7)

- **作者**: Mick
- **时间**: 2026-11-10T19:59:46Z
- **提交信息**: [Test] diffusion: Make cancellation backpressure deterministic (#49423)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [3f403a7](https://github.com/sgl-project/sglang/commit/3f403a753ffe86cc17589c509334f3ae34bda5ea)

- **作者**: Ethereal49
- **时间**: 2026-11-10T19:54:45Z
- **提交信息**: [CI] ci: Raise jit-kernel Run test timeout to 90 minutes (#49577)

### [c7e5751](https://github.com/sgl-project/sglang/commit/c7e5751ca258b1ecfde3dd175da8ba4212f4dcb6)

- **作者**: Mick
- **时间**: 2026-11-10T19:53:28Z
- **提交信息**: [Doc] diffusion: Surface measured H3-Image deployment performance (#49593)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [f39a0a0](https://github.com/sgl-project/sglang/commit/f39a0a083f0dab0e6ff2141eca59cdaf68d678f8)

- **作者**: Shangming Cai
- **时间**: 2026-11-10T19:25:07Z
- **提交信息**: [Fix] sgl-router: Count media in typed gRPC Generate, embeddings and rerank access logs (#49192)

### [daa1718](https://github.com/sgl-project/sglang/commit/daa171846f2dfc8162b4fbcfac13b073d7a6353a)

- **作者**: Zhiqiang Xie
- **时间**: 2026-11-10T18:12:22Z
- **提交信息**: [Fix] hicache: settle storage backups at the rank-agreed written prefix (#47626)

### [fadf83b](https://github.com/sgl-project/sglang/commit/fadf83be2047a6657ca5d576d519a7363d05b778)

- **作者**: Zhiqiang Xie
- **时间**: 2026-11-10T18:12:06Z
- **提交信息**: [Fix] hicache: keep the storage ack sequence on backend failures, stop workers in lockstep, fail the rank when a worker dies (#47617)

### [219b7e7](https://github.com/sgl-project/sglang/commit/219b7e7a688363bac9ef09eacf80e44eef9efe4b)

- **作者**: leon
- **时间**: 2026-11-10T17:33:02Z
- **提交信息**: [Perf] DeepSeek-V4.1-Flash: Use segmented fastokens for prompt encoding (#48928)

### [9a1979b](https://github.com/sgl-project/sglang/commit/9a1979b19260aebe0233744bd5cfee686976dd65)

- **作者**: Cheng Wan
- **时间**: 2026-11-10T17:24:25Z
- **提交信息**: [Doc] mem_cache: Document unified memory (#49312)

### [e674ed7](https://github.com/sgl-project/sglang/commit/e674ed71c67a1730edba939ed424a71f08dc7046)

- **作者**: Cheng Wan
- **时间**: 2026-11-10T17:23:06Z
- **提交信息**: [Fix] mem_cache: Signal a double free of unified pages when invariant checks are on (#49311)

### [e8a2bee](https://github.com/sgl-project/sglang/commit/e8a2bee913f8d7c7c00db86630db100b5f467d10)

- **作者**: Cheng Wan
- **时间**: 2026-11-10T17:21:56Z
- **提交信息**: [Fix] scheduler: Apply the write-after-read barrier in the PP loops and on every unified-memory device (#49310)

### [347c07e](https://github.com/sgl-project/sglang/commit/347c07e89e7c4e0cb475fb9c9072cccf29799c22)

- **作者**: Cheng Wan
- **时间**: 2026-11-10T17:20:40Z
- **提交信息**: [Fix] mamba: Commit verified states into the slots the verify forward resolved (#49309)

### [1b51a11](https://github.com/sgl-project/sglang/commit/1b51a11129bba53d43d2b741229ff38420a36467)

- **作者**: Cheng Wan
- **时间**: 2026-11-10T17:19:15Z
- **提交信息**: [Feat] mem_cache: Ask every unified memory capacity question of every pipeline stage (#49301)

### [2a7c267](https://github.com/sgl-project/sglang/commit/2a7c267efaa93786fe5fbe80877c568054b1f455)

- **作者**: Cheng Wan
- **时间**: 2026-11-10T17:18:15Z
- **提交信息**: [Refactor] mem_cache: Ask unified memory every capacity question as a demand (#49300)

### [e38dff3](https://github.com/sgl-project/sglang/commit/e38dff3e800e02d117d866cb5baf9e608767f807)

- **作者**: Cheng Wan
- **时间**: 2026-11-10T17:16:56Z
- **提交信息**: [Fix] mem_cache: Reset a reused request row's state in the next forward (#49299)

### [eb73a50](https://github.com/sgl-project/sglang/commit/eb73a50b1d6183deb1d79ca425677bd0cf93342f)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-11-10T14:20:29Z
- **提交信息**: [Fix] [AMD] rocprofiler-sdk: fix torch.profiler hang on TP for gfx1250-rocm1010 (#49004)

### [c31c8b8](https://github.com/sgl-project/sglang/commit/c31c8b81432ede1cca33e2b62e5bf89c7ee63950)

- **作者**: Han-Yin Chang
- **时间**: 2026-11-10T14:07:26Z
- **提交信息**: [Fix] cosmos3: Keep single-GPU BF16 CFG arithmetic under CFG parallel (#49162)

Signed-off-by: Han-Yin Chang <nick20350@gmail.com>

### [d684cc9](https://github.com/sgl-project/sglang/commit/d684cc9f8478f5063a5079d230d23bbee87d04f6)

- **作者**: Yue Fei
- **时间**: 2026-11-10T14:06:45Z
- **提交信息**: [Perf] [NVIDIA] mhc: Use BLOCK_K=32 for the hc_mix kernel on SM120 (#45264)

Co-authored-by: moria97 <feiyue2533@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [6c0c4d3](https://github.com/sgl-project/sglang/commit/6c0c4d32f9c643e89ad0d85509fe28dc860fd6be)

- **作者**: Yue Fei
- **时间**: 2026-11-10T14:06:30Z
- **提交信息**: [Perf] [NVIDIA] fp8: Use FlashInfer b12x for block-fp8-as-MXFP8 linears on SM12x (#45262)

Co-authored-by: moria97 <feiyue2533@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [4e86447](https://github.com/sgl-project/sglang/commit/4e864477f85cca9d5bf9b31c7c71e99c3c326ffa)

- **作者**: Alan Kao
- **时间**: 2026-11-10T14:06:13Z
- **提交信息**: [Feat] [AMD] gpt-oss: Mixed W4A8 MoE on gfx1250, Gluon below a token count and FlyDSL above (#47398)

Co-authored-by: Claude <noreply@anthropic.com>

### [fea2330](https://github.com/sgl-project/sglang/commit/fea23302428baadd150f24cfdb9a792624bf1a46)

- **作者**: Xinwei Qiang
- **时间**: 2026-11-10T14:04:14Z
- **提交信息**: [Perf] [NVIDIA] dspark: Opt-in fused int8 Markov walk kernel for bs <= 64 on Hopper (#42855)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [effa5b7](https://github.com/sgl-project/sglang/commit/effa5b7e440f4b93710fd85130fbbe0b0c7640bf)

- **作者**: vOv
- **时间**: 2026-11-10T14:03:44Z
- **提交信息**: [Feat] diffusion/sana-video2: Support sequence parallelism (#49405)

Signed-off-by: cr-gao <gaochenrui@sjtu.edu.cn>

### [170804b](https://github.com/sgl-project/sglang/commit/170804b40a403881256b600ffb337e23f37b4e30)

- **作者**: yz-wqf
- **时间**: 2026-11-10T13:49:15Z
- **提交信息**: [Feat] diffusion/model: Support MiniMaxAI/MiniMax-H3-Image (#49552)

Co-authored-by: Reynor <reynor@minimaxi.com>
Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: niehen6174 <1639206518@qq.com>

### [5c42444](https://github.com/sgl-project/sglang/commit/5c4244400236730771655f877b20d47ea2b0877b)

- **作者**: pllimax
- **时间**: 2026-11-10T13:28:51Z
- **提交信息**: [Test] [Ascend] npu: GLM-5.3 1P1D accuracy cases + weekday gsm8k (#48807)

### [18d862f](https://github.com/sgl-project/sglang/commit/18d862f93092a5e8a21c06b56f36c78f31a85b04)

- **作者**: Tamir Baydasov
- **时间**: 2026-11-10T13:17:29Z
- **提交信息**: [Feat] [NPU] dsa: Shard indexer prefill queries across attention TP (1/2) (#42977)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Артем Савкин <58187114+OrangeRedeng@users.noreply.github.com>
Co-authored-by: ronnie_zheng <zl19940307@163.com>

### [e9fd9ef](https://github.com/sgl-project/sglang/commit/e9fd9efea44ee4e06e6d7a48779b19c48b24ba07)

- **作者**: fengshaoyi-amd
- **时间**: 2026-11-10T12:57:20Z
- **提交信息**: [Fix] cuda-graph: Pause automatic GC during CUDA graph capture (#49263)

### [1f7eef8](https://github.com/sgl-project/sglang/commit/1f7eef8e39eddf8da6d2e5aa8073a493f1d626c9)

- **作者**: zyt329
- **时间**: 2026-11-10T12:39:51Z
- **提交信息**: [Fix] gemma4: Honor OOT attention defaults (#41293)

### [2d93fbf](https://github.com/sgl-project/sglang/commit/2d93fbfe5115131dd443dcbccde4426270119d6b)

- **作者**: LinyuanLi
- **时间**: 2026-11-10T11:13:23Z
- **提交信息**: [Feat] [NPU] longcat: Support Longcat2.0 for arch22 NPU (#47917)

### [a2ffd21](https://github.com/sgl-project/sglang/commit/a2ffd214696ea7144d3c237133a15df3315d900b)

- **作者**: Lee Nau
- **时间**: 2026-11-10T10:41:54Z
- **提交信息**: [CI] pp: Launch the PP test servers on DEFAULT_URL_FOR_TEST (#49335)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [626b95d](https://github.com/sgl-project/sglang/commit/626b95d503321e01bd145b12b2f82aac43d78fc0)

- **作者**: shiyang.814
- **时间**: 2026-11-10T10:33:45Z
- **提交信息**: [Feat] Qwen3.8-Flash-Next: Avoid padded PLE prefill activations (#43032)

### [4c08984](https://github.com/sgl-project/sglang/commit/4c08984a69b076b0eea37ab271f996bf735f3a23)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-10T10:32:48Z
- **提交信息**: [Feat] kimi-k3: Read the `thinking` object and map reasoning effort onto K3 tiers (#48776)

### [533c067](https://github.com/sgl-project/sglang/commit/533c06768925b7758fffc809f0f0d4c3d830f5e0)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-11-10T09:51:02Z
- **提交信息**: [Fix] diffusion: Keep explicit cuDNN attention inside LTX breakable CUDA graphs (#48615)

Co-authored-by: Po-Han Huang (NVIDIA) <53919306+nvpohanh@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [ed06877](https://github.com/sgl-project/sglang/commit/ed068770728d5e6ec506a178d300c82fee46875f)

- **作者**: yz-wqf
- **时间**: 2026-11-10T09:12:38Z
- **提交信息**: [Perf] [AMD] wan2.2: Gate FlyDSL norm and scale-shift fusion on high quality (#49024)

Co-authored-by: WenhaoZhang <42087078+niehen6174@users.noreply.github.com>

### [3830fb0](https://github.com/sgl-project/sglang/commit/3830fb0713d2451d4e7a993ce7bef8c0490a15ed)

- **作者**: weireweire
- **时间**: 2026-11-10T09:08:35Z
- **提交信息**: [Perf] [NVIDIA] dflash: Top up decode KV pages for the whole batch on allocation steps (#47685)

Co-authored-by: weireweire <20922698+weireweire@users.noreply.github.com>

### [670265c](https://github.com/sgl-project/sglang/commit/670265cd4b136f14363721257e0a60c43298e8fb)

- **作者**: Lee Nau
- **时间**: 2026-11-10T09:03:50Z
- **提交信息**: [Refactor] moe: Rename --moe-a2a-backend flashinfer to flashinfer_nvlink_one_sided (#48994)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [7e1cf12](https://github.com/sgl-project/sglang/commit/7e1cf1238442cf2b896df128aff40cfd08b18c1f)

- **作者**: shun8686
- **时间**: 2026-11-10T09:02:03Z
- **提交信息**: [CI] NPU: increase NPU coverage timeout and relax non-denoise stage tolerance (#49509)

### [66f47cd](https://github.com/sgl-project/sglang/commit/66f47cd634556c9b511c8a2454ec1e0a74b67907)

- **作者**: Lee Nau
- **时间**: 2026-11-10T08:57:58Z
- **提交信息**: [CI] rust-server: Pass architectures to ModelConfig in the crash-dump test (#49459)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [d50f98e](https://github.com/sgl-project/sglang/commit/d50f98e7f8c281d6451935b2a475009f94201549)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-10T08:47:21Z
- **提交信息**: [Feat] kimi-k3: Stream tool-call arguments incrementally (#48775)

### [b2616ca](https://github.com/sgl-project/sglang/commit/b2616cabbf1271352be6da98242a2a0edc84089e)

- **作者**: Nguyễn Thế Duy
- **时间**: 2026-11-10T08:25:48Z
- **提交信息**: [Fix] openai: Validate sampling bounds and preserve chat output limits (#44047)

Co-authored-by: Claude Sonnet 5.5 <noreply@anthropic.com>
Co-authored-by: Xinyuan Tong <xinyuantong.cs@gmail.com>

### [0c44fbf](https://github.com/sgl-project/sglang/commit/0c44fbff44da7d1a11f0e8b4299e4b8a702ac414)

- **作者**: Rita Brugarolas
- **时间**: 2026-11-10T07:02:59Z
- **提交信息**: [Perf] [AMD] Qwen3-Next: consume the fused AR+norm+quant output (#44566)

Signed-off-by: Rita Brugarolas Brufau <rita.brugarolasbrufau@amd.com>
Co-authored-by: jacky.cheng <yichiche@amd.com>

### [d565013](https://github.com/sgl-project/sglang/commit/d565013acdcb4590d6b88ffb7557a6f83f3a4793)

- **作者**: iridiumine
- **时间**: 2026-11-10T06:47:43Z
- **提交信息**: [Feat] [NPU] attention: enable mixed-chunk for pure MLA on the ascend backend (#47857)

### [73bf84e](https://github.com/sgl-project/sglang/commit/73bf84e90f1cc14ccf65de37b57f4d3d8653ea85)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-10T06:36:42Z
- **提交信息**: [Fix] dspark: Write deferred draft KV only for carried requests (#49436)

### [fa703d6](https://github.com/sgl-project/sglang/commit/fa703d685adc2465a86b53fb1929cfc870707756)

- **作者**: Michael
- **时间**: 2026-11-10T06:20:12Z
- **提交信息**: [CI] [AMD] minimax-m3.1: Add a MI35x MXFP4 + DSpark nightly accuracy gate (#46944)

### [ae1347a](https://github.com/sgl-project/sglang/commit/ae1347a5c36a668ace327a60f6929c0f5949eabf)

- **作者**: Yue Fei
- **时间**: 2026-11-10T06:13:33Z
- **提交信息**: [Perf] [NVIDIA] fp8: Add Triton block-fp8 GEMM configs for RTX PRO 5000 (#45263)

Co-authored-by: moria97 <feiyue2533@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [6dc7e3e](https://github.com/sgl-project/sglang/commit/6dc7e3ea7e08840d38a93220cb904ed4870a51f6)

- **作者**: jsheng_Linkedin
- **时间**: 2026-11-10T05:54:23Z
- **提交信息**: [Feat] score/embedding: Add raw embeddings, score rids, encode input_ids, and schedule-decision logging (#44152)

Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>
Co-authored-by: Sundara Raman Ramachandran <suramach@suramach-mn6488.linkedin.biz>
Co-authored-by: Richard Wang <wangrichard08@gmail.com>

### [c678ef8](https://github.com/sgl-project/sglang/commit/c678ef8dc4b7aa9f4e0d297510927bca2092d745)

- **作者**: Sundara Raman Ramachandran
- **时间**: 2026-11-10T05:52:41Z
- **提交信息**: [Fix] CODEOWNERS: Restore prefill-only test ownership (#49470)

Co-authored-by: Sundara Raman Ramachandran <suramach@suramach-mn6488.linkedin.biz>

### [e03f9ee](https://github.com/sgl-project/sglang/commit/e03f9eef09bcd833515049b625796c21de89aa37)

- **作者**: Po-Han Huang (NVIDIA)
- **时间**: 2026-11-10T05:39:25Z
- **提交信息**: [Fix] rust-server: Pass architectures to ModelConfig in test_rust_server_crash_dump (#49461)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [2fb4f3d](https://github.com/sgl-project/sglang/commit/2fb4f3db431190255a56ebcf03c8dd35a27573e3)

- **作者**: Kevin Mi
- **时间**: 2026-11-10T05:35:18Z
- **提交信息**: [Doc] [AMD] cookbook: Match the Kimi-K3.1-Pro MI35x cells to InferenceX #4928 and mount the Ionic provider for PD (#49453)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [29aaf75](https://github.com/sgl-project/sglang/commit/29aaf7589965a09b14731afd7504367c927995e7)

- **作者**: Trevor Morris
- **时间**: 2026-11-10T05:29:27Z
- **提交信息**: [Fix] [NVIDIA] jit: Build sm_107a on CC 10.7, keeping sm_100f only for modules that use CUTLASS (#49420)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: kpham-sgl <khoa.pham@radixark.ai>

### [e018726](https://github.com/sgl-project/sglang/commit/e0187268f64165fa6969fb166dd5c11f05462e3c)

- **作者**: Aarne Talman
- **时间**: 2026-11-10T04:05:49Z
- **提交信息**: [Perf] [AMD] batch-invariant: Segmented split-K bf16 matmul for gfx950 (#45599)

Signed-off-by: Aarne Talman <aarne.talman@amd.com>
Co-authored-by: HAI <hixiao@gmail.com>
Co-authored-by: Xinyi Song <xinyisong0111@gmail.com>

### [1be97a0](https://github.com/sgl-project/sglang/commit/1be97a0a6312ef5bf1e613bb50beb0081ec8ea31)

- **作者**: 黄云龙
- **时间**: 2026-11-10T03:01:22Z
- **提交信息**: [Doc] cookbook: Fix the dead MiniMax-H3 "Learn more" anchors (#46052)

### [ea712f5](https://github.com/sgl-project/sglang/commit/ea712f5652e2af11c7d7337bbd1aa23cdeffb3b7)

- **作者**: Haomiao Qiu
- **时间**: 2026-11-10T02:49:49Z
- **提交信息**: [Fix] moe: Fix illegal memory access in the W4A16/W8A16 Triton MoE kernel (unmasked K tail) (#48556)

### [d766f19](https://github.com/sgl-project/sglang/commit/d766f19301357f30323370c8f19bdc4aac877c78)

- **作者**: Han-Yin Chang
- **时间**: 2026-11-10T02:49:37Z
- **提交信息**: [Fix] diffusion: Use K/V gather when auto SP cannot split the DiT's heads (Z-Image on 4 GPUs) (#49225)

Signed-off-by: Han-Yin Chang <nick20350@gmail.com>

### [66ad892](https://github.com/sgl-project/sglang/commit/66ad8925d28cd80419249f4f363fc70c06f8852b)

- **作者**: Spectrum-o
- **时间**: 2026-11-10T02:49:21Z
- **提交信息**: [Fix] cuda_graph: Retain capture inputs for full graph replay (#48860)

### [5379f2c](https://github.com/sgl-project/sglang/commit/5379f2cbe303208a874650a0b3c9b9aa7fa165fc)

- **作者**: Han-Yin Chang
- **时间**: 2026-11-10T02:49:03Z
- **提交信息**: [Fix] diffusion: Let FLUX.3 Image start with --num-gpus alone (#49224)

Signed-off-by: Han-Yin Chang <nick20350@gmail.com>

### [d76112d](https://github.com/sgl-project/sglang/commit/d76112d39f2800b32a2ecdfec1075ccc4e1213a8)

- **作者**: Woody-Hu
- **时间**: 2026-11-10T02:48:45Z
- **提交信息**: [Perf] moe/paged-experts: decide block-wide and skip empty page-ins (#48605)

### [98d32a4](https://github.com/sgl-project/sglang/commit/98d32a4fba1a9a0d94cced6831a27fca44063fbb)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-11-10T02:46:15Z
- **提交信息**: [Test] comfyui: Attach loaded plugin modules to their parents so mock.patch works on Python 3.10 (#49235)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [340f70f](https://github.com/sgl-project/sglang/commit/340f70fbe2843261b54b3f26b5961e3152587765)

- **作者**: Ziyi Xu
- **时间**: 2026-11-10T02:46:06Z
- **提交信息**: [Test] gemma4: Cover the multimem.ld_reduce rounding in the AR fusion residual check (#49346)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [e886acf](https://github.com/sgl-project/sglang/commit/e886acfa8b0a57e835c490fa59d7b3804060c2e0)

- **作者**: Zhiqiang Xie
- **时间**: 2026-11-10T02:43:09Z
- **提交信息**: [Fix] hicache: vote the prefetch timeout once per tick, not per admission poll (#47620)

### [8d5411e](https://github.com/sgl-project/sglang/commit/8d5411e478a66d29cf9d272a1f499387fa9077c3)

- **作者**: elvischenv
- **时间**: 2026-11-10T02:23:46Z
- **提交信息**: [Perf] kda: Run the fused CuTe DSpARK verify kernel on a BF16 SSM state (#48613)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Po-Han Huang <pohanh@nvidia.com>

### [211b22c](https://github.com/sgl-project/sglang/commit/211b22c60749d78eb7a0e23e9dde4c320cb04906)

- **作者**: Bastian Hagedorn
- **时间**: 2026-11-10T02:22:22Z
- **提交信息**: [Fix] gemm: Order the CuTe DSL kernels' TMEM release after the epilogue's tcgen05.ld (#48616)

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: Po-Han Huang <pohanh@nvidia.com>

### [5604b31](https://github.com/sgl-project/sglang/commit/5604b31bde2176322f9a43518d781ef2217b1e6f)

- **作者**: BourneSun0527
- **时间**: 2026-11-10T01:40:18Z
- **提交信息**: [Fix] [NPU] dsv4: Use explicit compressor state on Ascend 950 (#49000)

### [5175c31](https://github.com/sgl-project/sglang/commit/5175c315896642b4d1bba9ffa20aa83b9d6b5be5)

- **作者**: Sundara Raman Ramachandran
- **时间**: 2026-11-10T01:31:54Z
- **提交信息**: [Chore] CODEOWNERS: Update score, decisions, and embeddings API owners (#48956)

Co-authored-by: Sundara Raman Ramachandran <suramach@suramach-mn6488.linkedin.biz>
Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>

### [e85fac4](https://github.com/sgl-project/sglang/commit/e85fac452f4e82a278a5ae1f2f13e1fab6dbbc5a)

- **作者**: jain-ria
- **时间**: 2026-11-10T01:26:13Z
- **提交信息**: [Feat] rust/grpc: Report orchestrator launch facts in api.v1 discovery (#45859)

Signed-off-by: jain-ria <riajain@NVIDIA.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: ishandhanani <82981111+ishandhanani@users.noreply.github.com>

### [b5a7900](https://github.com/sgl-project/sglang/commit/b5a7900ae4ea821aba339ea2a6fa47a80ef498f1)

- **作者**: Baizhou Zhang
- **时间**: 2026-11-10T01:23:29Z
- **提交信息**: [Feat] kernels: Kimi-K3.1 kernel changes split out of #48414 (#49411)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [56ee8ed](https://github.com/sgl-project/sglang/commit/56ee8ed5f591d2233f42674ad9d3814b3d953e2d)

- **作者**: Jack Zhang
- **时间**: 2026-11-10T01:18:54Z
- **提交信息**: [Fix] ZeroMQ: make blocking send wait for queue space (#47943)

### [5f7f971](https://github.com/sgl-project/sglang/commit/5f7f971d3f597bd7e1b871677d6eac07cc0487aa)

- **作者**: LinyuanLi
- **时间**: 2026-11-10T01:15:24Z
- **提交信息**: [Feat] [NPU] attention: Support Modelslim GQA mxfp8 kvcache for 950 NPU (#48126)

### [33d0465](https://github.com/sgl-project/sglang/commit/33d0465c27756eecc41e48a0cb13ca98a42b6b4c)

- **作者**: Jimmy Shong
- **时间**: 2026-11-10T01:14:41Z
- **提交信息**: [Perf] flashinfer-megamoe: Add an optional decode workspace (#46213)

### [4e9e7e8](https://github.com/sgl-project/sglang/commit/4e9e7e82f5131c8df43f5d1e99b0674406960562)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-10T01:07:24Z
- **提交信息**: [Fix] scheduler: Record every PP result completion event after the local forward (#49386)

### [eafc491](https://github.com/sgl-project/sglang/commit/eafc49148eb9515546a3ff64c0407d221f90e900)

- **作者**: yunyang_nv
- **时间**: 2026-11-10T00:22:03Z
- **提交信息**: [Fix] dsa: Route mixed-chunk batches to the RAGGED top-k transform for bf16-only sparse prefill (#44176)

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: Po-Han Huang (NVIDIA) <53919306+nvpohanh@users.noreply.github.com>
Co-authored-by: Po-Han Huang <pohanh@nvidia.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-11-11
**监控日期**: 2026-11-10
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for 100+ DiTs.
- **语言**: Python
- **星标数**: 1303
- **最后更新**: 2026-11-10T14:53:12Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

# cache-dit 昨日提交分析（第1/1批，共3条）

## 1. 主要更新类型

- **功能新增**：原生支持 Boogu-Image 模型及其专属 CUDA kernel 家族
- **重构**：SVDQ 量化路径大幅简化，合并分散的 INT4/FP4 GEMM 入口
- **性能优化**：CuTe 量化生产者按 rank 特化，扩展体积缩减约 42%

## 2. 关键变更点及与项目方向的关系

- **Boogu-Image 原生化（#1269）**：将 Boogu-Image 栈直接 vendor 进 `src/cache_dit/models/pipelines/boogu_image/`，摆脱对第三方 `boogu` 包的依赖；新增第四套 CUDA kernel 家族 `_C_models`，包含融合 QK-Norm+RoPE、gated RMSNorm、scaled RMSNorm 等算子，并移除 Triton RMSNorm 依赖。CP 并行扩展到 refiner 双流/单流栈，实现 **CP + cache 叠加**。这直接呼应项目"推理引擎"定位——通过自研 kernel 减少外部依赖、提升开箱性能。
- **SVDQ 重构（#1273）**：删除原生 INT4 GEMM 及其三个分阶段实例化 TU，扁平化 `native/{core,int4,fp4}` 目录结构，Python 侧收敛为单一 `svdq_gemm_w4a4` op。扩展体积从 45.5MB 降至 26.6MB，且核心 GEMM 主循环、MMA 分解和 epilogue 数学保持不变——典型的"减枝不减力"重构。
- **CuTe 生产者特化（#1271）**：按 rank 特化激活量化生产者，校验 fused/split-K 尾部情况，默认 CuTe 路径采用 row-major LoRA 布局，属于内核级性能打磨。

## 3. 对项目的影响和潜在意义

- **生态独立性提升**：摆脱 `boogu` 三方依赖意味着更可控的版本演进、更简单的安装体验（PyPI 下载量是 README 强调的指标，依赖精简直接利好用户）。
- **维护成本下降**：SVDQ 路径从多套 GEMM/多层目录坍缩为单一线性路径，消除零调用方入口和不可达 ABI 参数，减少死代码与潜在 bug 面。
- **性能可信度**：扩展体积减半但算子数学不变，说明此前存在大量未被激活的编译产物，重构后二进制加载和分发效率都会改善。
- **并行能力扩展**：CP 覆盖到单流/双流栈，且 `ulysses_async` 由静默降级改为显式报错——工程上更诚实，避免用户在不知情下拿到错误结果。

## 4. 值得关注的技术点

- `cache_dit._C_models` 作为第四套 kernel 家族的定位与边界（与 Triton 路径的取舍关系）。
- CP 中"cached 栈外 split、transformer 内 gather"的设计模式，可复用到其他模型栈。
- LoRA 布局默认切到 row-major 对下游用户的影响面（是否需要迁移配置）。
- SVDQ `runtime.h` 中 `RuntimeParams`/`LoraLayout` 的合并是否会成为后续公共 ABI 的锚点。

## 5. 对项目发展的整体影响

结合 README 中"Cache、并行、量化、CPU offload 的 PyTorch 原生 DiT 推理引擎"这一目标，昨日提交呈现出清晰的三条主线：**量化路径瘦身**（SVDQ 重构 + CuTe 优化）、**模型覆盖扩展**（Boogu-Image 原生化）、**并行语义补全**（CP 覆盖全栈）。这表明项目正处于从"功能铺开"转向"工程收敛"的阶段——通过自研 kernel 替换三方依赖、通过重构压低维护负担，同时保持核心算子性能不变。这类改动虽不带来炫目的新特性，却是项目走向稳定、可长期维护的基础设施的必要沉淀，对提升用户信任度和扩展更多 DiT 模型支持都具有基础性意义。

## 详细提交记录

### [227fb9a](https://github.com/vipshop/cache-dit/commit/227fb9a1b04f60f189aff02072b6831c4afc3dbe)

- **作者**: DefTruth
- **时间**: 2026-11-10T11:46:45Z
- **提交信息**: refactor(svdq): collapse the native W4A4 path into a single GEMM (#1273)

Delete the plain INT4 GEMM, its three stage instantiation TUs and the CACHE_DIT_SVDQ_BLOCK_M knob; rename gemm_w4a4_ext_* to gemm_w4a4_* and flatten native/{core,int4,fp4} into native/. Drop the runtime stage selector end to end, remove the zero-caller native entries and the unreachable ext ABI arguments (keeping fuse_silu/fuse_glu), and consolidate RuntimeParams/LoraLayout into svdq/runtime.h. Python collapses to a single svdq_gemm_w4a4 op. The extension shrinks from 45.5MB to 26.6MB with the GEMM main loop, MMA decomposition and epilogue math unchanged.

### [9849ff1](https://github.com/vipshop/cache-dit/commit/9849ff1118b7bbdea73a9cff650d05a25fa2b398)

- **作者**: DefTruth
- **时间**: 2026-11-10T09:11:57Z
- **提交信息**: perf(svdq): specialize CuTe quantize producer by rank (#1271)

Add rank-specialized CuTe activation producers, validate fused/split-K tails, and default the CuTe path to row-major LoRA layout.

### [2c969e7](https://github.com/vipshop/cache-dit/commit/2c969e77abb2f785880d6b15b6c81f60f49eb8c5)

- **作者**: DefTruth
- **时间**: 2026-11-10T08:28:16Z
- **提交信息**: feat(model): support Boogu-Image natively with the _C_models kernel family (#1269)

Vendors the Boogu-Image stack into `src/cache_dit/models/pipelines/boogu_image/` so
cache-dit no longer needs the third-party `boogu` package, adds a fourth CUDA
kernel family (`cache_dit._C_models` with fused QK-Norm+RoPE, gated RMSNorm and
scaled RMSNorm), drops the Triton RMSNorm dependency, and extends CP to the three
refiner stacks, the double-stream stack and the single-stream stack (split outside
the cached stacks, gather in the transformer, so CP + cache works). TP keeps the
FFN + modulation plan; `ulysses_async` raises instead of degrading silently.

Closes #1268

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-11-11
**监控日期**: 2026-11-10
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 96694
- **最后更新**: 2026-11-11T01:57:00Z

## 提交统计

- **昨日提交总数**: 77
- **提交者数量**: 59
- **主要提交者**: Lucas Wilkinson, Fangzhou Ai, AlexHuang

## AI分析总结

## vLLM 昨日提交合并分析

### 一、主要更新类型
- **性能优化**（约20项）：Rust 前端 SSE 序列化提速、ROCm/AMD 特化解码、MoE 快速 SiLU 激活、EPLB 专家重平衡单次内核拷贝、DeepSeek v4.1 CuTe DSL 内核调优、NVLink 复制引擎 PP 传输通道等。
- **Bug 修复**（约20项）：Rust 前端请求取消、KV Connector 内存注册、量化 scale 索引、MoE 权重连续性、多模态前缀 LM 在各 PP 阶段的注意力区间构建、YaRN 嵌套配置、投机解码稳定性等。
- **功能新增与重构**：KV 缓存外部注册声明、Mooncake 连接器拆包、ModelOpt INT8_PB_WO 按块仅权重量化、PP 复制引擎传输通道、Kimi K3.1/K3 模型更新、异步 KV 加载限流、MRv1 清理等。
- **CI 与基础设施**：CUDA 13.0→13.2、MI355X 上的 ROCm 夜间任务、B200 夜间评测修复、测试自动分片、示例 pytest 化等。

### 二、关键变更点与项目方向的关系
1. **Rust 前端持续成熟**：SSE 序列化提速、工具调用流式解析（DeepSeek DSML）、取消与推理标记修复，体现向高性能 Rust 服务层演进。
2. **PP 流水线并行体系化**：从零散修复走向"修复—验证—加速"闭环——新增 PP 等价性测试套件、tied embedding 移至最后一个 PP rank、默认启用 NVLink 复制引擎通道，预示其将成为规模化部署的默认优选路径。
3. **ROCm/AMD 走向生产级**：避免运行时 JIT、本地哈希查询、UMBP 独立模式，配合 MI355X 的 XPress/EPLB 夜间任务，AMD 后端正从"能跑"迈向可靠与高性能；同时跟进 Blackwell SM100 内核，硬件覆盖持续拓宽。
4. **P/D 分离与 KV 体系深化**：MRV2 prefill 的 KV-only 模式、KV Connector 外部注册、卸载 junction 修复、异步加载限流，强化分布式推理能力。
5. **量化与 MoE 降本**：INT8 per-channel scale 修复、INT8_PB_WO 按块权重量化、Muse Spark FP8 路由专家、快速激活优化，直接服务"fast and cheap"的成本目标。

### 三、对项目的影响与潜在意义
- **可靠性**：PP、投机解码、多模态注意力等核心路径修复降低大规模部署的静默错误风险；muse 二次复杂度扫描、Kimi K3 原生编码要求等安全修复提升生产可用性。
- **硬件多元化**：ROCm 与 B200 相关 CI 密集投入，强化异构生态的中立支持，降低推理算力的供应链与成本门槛。
- **迭代效率**：CI 自动分片与夜间评测缩短反馈周期；弃用旧 grpc_server/api_server/run_batch 并推进 CUDA 13.2，标志技术债清理与版本现代化，为 v0.37.0 及后续版本奠定基础。

### 四、值得关注的技术点
- DeepSeek v4.1 的 CuTe DSL 边界处理与 JIT 消除，代表内核优化新范式。
- NVLink 复制引擎异步搬运张量、释放计算流，是 PP 性能的关键杠杆。
- ModelOpt INT8_PB_WO 在精度与显存间提供新平衡，适合大模型权重压缩。
- MiniMax-M3 的 fmha_sm100 升级体现对 Blackwell 架构的前瞻适配。
- `max_async_kv_loads_per_step` 等调度级资源控制机制值得借鉴。
- Kimi K3.1 分阶段合入策略体现大型模型适配的工程成熟度；Claude/Codex/Cursor 等 AI 代理作为共同作者深度参与，反映协作开发模式的显著变化。

### 五、对项目发展的整体影响
总体而言，vLLM 在保持高频迭代的同时正沿三条主线演进：以 PP 与投机解码夯实多卡、低成本推理的性能底座，以 Rust 前端与 ROCm/Blackwell 适配拓宽技术栈和硬件覆盖面，以 KV 体系、量化优化与 CI 自动化保障质量与成本效率，持续兑现其"简单、快速、廉价"的大模型服务承诺。

## 详细提交记录

### [209af43](https://github.com/vllm-project/vllm/commit/209af43cc4ff6e7434ee4328eb3da14ccc4e5edd)

- **作者**: David Teather
- **时间**: 2026-11-10T23:51:56Z
- **提交信息**: [Perf][Rust Frontend] Serialize SSE chunks before building the event (#65028)

Signed-off-by: davidteather <34144122+davidteather@users.noreply.github.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [f3a752c](https://github.com/vllm-project/vllm/commit/f3a752c201c951764d8608111a019f1f5cc1e50f)

- **作者**: bzsuni
- **时间**: 2026-11-10T23:51:43Z
- **提交信息**: [Bugfix][Rust Frontend] Fix cancellation during request submission (#64742)

Signed-off-by: bzsuni <bingzhe.sun@daocloud.io>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [0a37f46](https://github.com/vllm-project/vllm/commit/0a37f464dacf1357b45fdfe4176250dc8d8f0dba)

- **作者**: Ketor
- **时间**: 2026-11-10T22:59:00Z
- **提交信息**: [KVConnector] Let external connectors declare KV cache memory registration (#66605)

Signed-off-by: Ketor <d.ketor@gmail.com>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Signed-off-by: ApostaC <yihua@tensormesh.ai>
Co-authored-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: ApostaC <yihua@tensormesh.ai>

### [539366a](https://github.com/vllm-project/vllm/commit/539366a773793e8219fb5d5699d0778e75f271a7)

- **作者**: Yifan Qiao
- **时间**: 2026-11-10T22:45:39Z
- **提交信息**: [Attention][MiniMax-M3] Allow the BLHNC KV cache layout with an NVFP4 KV cache (#66892)

Signed-off-by: Yifan Qiao <yifanqiao@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [a92ab5b](https://github.com/vllm-project/vllm/commit/a92ab5b196430ec62e761f0d751a8c96abc43a6e)

- **作者**: James E T Smith
- **时间**: 2026-11-10T22:25:23Z
- **提交信息**: [ROCm][Perf][Kimi-K3] Mono decode layer for Kimi-K3 on MI355X w/ vanilla decode (#61498)

Signed-off-by: hyukjlee <hyukjlee@amd.com>
Signed-off-by: James E T Smith <jamesmit@amd.com>
Signed-off-by: James E T Smith <james.smith9113@gmail.com>
Signed-off-by: jamesETsmith <james.smith9113@gmail.com>
Co-authored-by: hyukjlee <hyukjlee@amd.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Shanshan Shen <467638484@qq.com>

### [f460a5e](https://github.com/vllm-project/vllm/commit/f460a5ed01599c549f24751bdf6ee8026c590f14)

- **作者**: Andreas Karatzas
- **时间**: 2026-11-10T21:51:25Z
- **提交信息**: [ROCm][Bugfix] Key the FSE MXFP8 scale-layout test check on the selected backend (#66875)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [6faba98](https://github.com/vllm-project/vllm/commit/6faba98396058547de9ee0b2adae7b9990ca7d45)

- **作者**: Leizhen Zhang
- **时间**: 2026-11-10T21:17:05Z
- **提交信息**: [Bugfix][Security] muse: fix quadratic attribute scans in tool-call extraction (#62345)

Signed-off-by: LeizhenZhang <zhangleizhen645@gmail.com>
Co-authored-by: Flora Feng <4florafeng@gmail.com>

### [1479deb](https://github.com/vllm-project/vllm/commit/1479deb0392f1e7d2a69399e4150202284c24509)

- **作者**: Dilber
- **时间**: 2026-11-10T20:09:21Z
- **提交信息**: [Bugfix][Benchmark] Take openai-audio input tokens from server usage (#62791)

Signed-off-by: Dilber P Shakir <dilbersha@gmail.com>

### [bc4ca78](https://github.com/vllm-project/vllm/commit/bc4ca78fd13f5647b34f8e4145296a00a23aad36)

- **作者**: rasmith
- **时间**: 2026-11-10T19:16:04Z
- **提交信息**: [ROCm][CI] Add  `vllm/v1/attention/backend.py` to the :`amd: (MI355 DPX) MLA Kernels` test group in main CI (#66854)

Signed-off-by: Randall Smith <Randall.Smith@amd.com>

### [b76e240](https://github.com/vllm-project/vllm/commit/b76e2401f844857635f2662ce95b636d2cce52ac)

- **作者**: mispa-ms
- **时间**: 2026-11-10T19:04:15Z
- **提交信息**: [Recipe] Kimi-K3.1-Pro: add GB300 AgentX presets, align with InferenceX#4907 (#66642)

Signed-off-by: Mi Sun Park <misunp@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [29b6280](https://github.com/vllm-project/vllm/commit/29b6280ec193ec2d550d693494dcee71fe9551f4)

- **作者**: Sahithi Chigurupati
- **时间**: 2026-11-10T18:19:36Z
- **提交信息**: [Bugfix][GLM-5.3] Build the MTP eh_proj low-latency GEMM plan (#65704)

Co-authored-by: Roberto L. Castro <38211239+LopezCastroRoberto@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [57988c0](https://github.com/vllm-project/vllm/commit/57988c08c27c273ef67816323aea507d4e229603)

- **作者**: Keita Watanabe
- **时间**: 2026-11-10T18:12:56Z
- **提交信息**: [Doc] Named and required tool_choice need a tool parser (#64663)

Signed-off-by: Keita Watanabe <keitaw09@gmail.com>
Co-authored-by: Flora Feng <4florafeng@gmail.com>

### [75be5c3](https://github.com/vllm-project/vllm/commit/75be5c3919b6a82fa1885c0d0a2250adba477413)

- **作者**: stefankoncarevic
- **时间**: 2026-11-10T17:20:01Z
- **提交信息**: [ROCm][CI] Stub owns_indexer and index_epoch in the merged-cache sparse MLA test (#66798)

Signed-off-by: Stefan Koncarevic <Stefan.Koncarevic@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [dd5299b](https://github.com/vllm-project/vllm/commit/dd5299b11684a63fd3d341160c866ea6cc95bb33)

- **作者**: Andreas Karatzas
- **时间**: 2026-11-10T17:18:19Z
- **提交信息**: [Bugfix][Core] Re-prepare model state after extensible KV cache extension (Kimi-K3 AMD specialized decode) (#66370)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Signed-off-by: Divakar Verma <divakar.verma@amd.com>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Divakar Verma <divakar.verma@amd.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Nick Hill <nickhill123@gmail.com>

### [e3dc02e](https://github.com/vllm-project/vllm/commit/e3dc02e56ca6fe836e77d469d34ea2498d1b8f67)

- **作者**: qizixi
- **时间**: 2026-11-10T17:01:34Z
- **提交信息**: [Spec Decode][MRV2] Add prefill_context_kv_only for P/D prefill instances (#65217)

Signed-off-by: zixi-qi <zixi@inferact.ai>
Co-authored-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Zihua Wu <13583761+lucifer1004@users.noreply.github.com>
Co-authored-by: LLLZeSheng <93436081+LLLZeSheng@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [b8343e1](https://github.com/vllm-project/vllm/commit/b8343e1855801783727e3fb0db435230c42d539a)

- **作者**: djramic
- **时间**: 2026-11-10T16:58:17Z
- **提交信息**: [ROCm][CI] Re-enable ROCM_AITER_UNIFIED_ATTN in Whisper transcription tests (#66824)

Signed-off-by: Djordje Ramic <djoramic@amd.com>

### [ca3c154](https://github.com/vllm-project/vllm/commit/ca3c154d26749c2b59d9d99050d2bd631d2c63f7)

- **作者**: schopde-nvidia
- **时间**: 2026-11-10T16:12:48Z
- **提交信息**: [Kernel] Register the cudnn backend for FlashInfer BF16 mm (#59025)

Signed-off-by: Siddharth Chopde <schopde@nvidia.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [bec08b7](https://github.com/vllm-project/vllm/commit/bec08b70193cef26c1b9a6bd39c44bf7f4e031e6)

- **作者**: A&W
- **时间**: 2026-11-10T15:45:34Z
- **提交信息**: [MM] Support mm_device_do_normalize for Gemma 4 Unified (#65724)

Signed-off-by: Alex-Wengg <hanweng9@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [b5c8627](https://github.com/vllm-project/vllm/commit/b5c8627078cdc41235e0e58a792df72df9299cc4)

- **作者**: Misha Goin
- **时间**: 2026-11-10T15:41:59Z
- **提交信息**: [Perf][Quantization] Use fast SiLU intrinsics in Humming MoE activations (#65975)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [df7ce08](https://github.com/vllm-project/vllm/commit/df7ce08e959c426ae0db63bd02088b8ad1f1b615)

- **作者**: xiangdong
- **时间**: 2026-11-10T14:49:23Z
- **提交信息**: [XPU][CI]Migrate more B70 jobs from intel_gpu to intel_gpu_k8s (#66603)

Signed-off-by: zengxian <xiangdong.zeng@intel.com>

### [9f3644b](https://github.com/vllm-project/vllm/commit/9f3644bbdc94c158c9588a7579a06ef040f10079)

- **作者**: Bo Pang
- **时间**: 2026-11-10T13:59:15Z
- **提交信息**: [Bugfix][Model] MiMo-V2 omni: label video grids with the sampled frames' media time (#66201)

Signed-off-by: Bo Pang <bopang314@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [07aea9d](https://github.com/vllm-project/vllm/commit/07aea9dc1c0f301ca2e3c8e96231aa01bdb39990)

- **作者**: fxmarty-amd
- **时间**: 2026-11-10T13:42:53Z
- **提交信息**: [Bugfix][Quantization] Index INT8 MoE per-channel weight scales independently of act quant - #58570 (#65177)

Signed-off-by: Felix Marty <Felix.Marty@amd.com>
Signed-off-by: Ahsan Saghir <ahsaghir@amd.com>
Co-authored-by: GokayAI <60583610+gokay-ai@users.noreply.github.com>
Co-authored-by: GokayAI <gokay-ai@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Ahsan Saghir <ahsaghir@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [c021a8b](https://github.com/vllm-project/vllm/commit/c021a8b0a9049c39db7142823126b1c28a4fb85b)

- **作者**: GalMeiromN
- **时间**: 2026-11-10T13:39:01Z
- **提交信息**: [RL] Add configurable staging and parallel stage pulls to sharded RDT (#61076)

Signed-off-by: gmeirom <gmeirom@nvidia.com>
Co-authored-by: Cursor <noreply@cursor.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [65711a1](https://github.com/vllm-project/vllm/commit/65711a1617a04c03d0a13c7308d578f1a6163ba0)

- **作者**: Hexiang Wang
- **时间**: 2026-11-10T12:14:00Z
- **提交信息**: [ROCm][Perf] Skip DSA indexer scoring for short dense-MHA prefills (#61942)

Signed-off-by: whx-sjtu <56632993+whx-sjtu@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [b2b5ae8](https://github.com/vllm-project/vllm/commit/b2b5ae8f79ceea861a3ed2786563a2d0bacfb6bd)

- **作者**: Krishnan Prashanth
- **时间**: 2026-11-10T11:59:13Z
- **提交信息**: [Rust Frontend] Accept media_io_kwargs video fps over gRPC (#66187)

Signed-off-by: Krishnan Prashanth <kprashanth@nvidia.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [9b38c83](https://github.com/vllm-project/vllm/commit/9b38c833ee5a0c9e241f055a6d47327d8f33e9ef)

- **作者**: AlexHuang
- **时间**: 2026-11-10T11:25:46Z
- **提交信息**: [Bugfix][KV Offload] Preserve confirmed junction after lookup retry (#66544)

Signed-off-by: Alex <alex.tech.lab@outlook.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [3996083](https://github.com/vllm-project/vllm/commit/3996083d37324d4df913ec133e8d993b21199030)

- **作者**: Andrey Talman
- **时间**: 2026-11-10T11:13:53Z
- **提交信息**: [CI/Build] Move the default CUDA build from 13.0 to 13.2 (#55387)

Signed-off-by: Andrey Talman <atalman@users.noreply.github.com>
Signed-off-by: khluu <khluu000@gmail.com>
Signed-off-by: Andrey Talman <atalman@fb.com>
Co-authored-by: Andrey Talman <atalman@users.noreply.github.com>
Co-authored-by: khluu <khluu000@gmail.com>
Co-authored-by: Kimi <noreply@moonshot.cn>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [4e3463c](https://github.com/vllm-project/vllm/commit/4e3463c87493ebd2c5d5fbe4be6469911e23e2bf)

- **作者**: Arian Boukani
- **时间**: 2026-11-10T10:20:24Z
- **提交信息**: [Bugfix][Rust Frontend] Don't reopen reasoning after the prompt closed it (#66380)

Signed-off-by: Arian Boukani <boukani.arian@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [d6b696d](https://github.com/vllm-project/vllm/commit/d6b696d60df12b034537a4f7aa014bba4fa4ab9b)

- **作者**: Thang Nguyen
- **时间**: 2026-11-10T10:11:00Z
- **提交信息**: [CI] Prebuild mamba-ssm and causal-conv1d from pinned commits in a torch-keyed test-image stage (#58795)

Signed-off-by: Kevin Luu <51931015+khluu@users.noreply.github.com>
Signed-off-by: Thang Nguyen <thangnguyenvn647@gmail.com>
Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Kevin Luu <51931015+khluu@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: khluu <khluu000@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [feb4cb0](https://github.com/vllm-project/vllm/commit/feb4cb019f445b2b3cd2bd0ba0f258610100910e)

- **作者**: 王金旭
- **时间**: 2026-11-10T09:43:16Z
- **提交信息**: [Bugfix][Tests] Fix iteration-details recomputation test setup (#66744)

Signed-off-by: wjinxu <1299461899@qq.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [d74e22b](https://github.com/vllm-project/vllm/commit/d74e22b08edd1398021982543e7a506a66ce9f54)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-11-10T09:16:23Z
- **提交信息**: [Misc] Separate Mooncake PD and Store connectors into sibling packages (#65877)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [83f5de4](https://github.com/vllm-project/vllm/commit/83f5de466a889c29ac5fbfbe342d6fe4c09811e8)

- **作者**: Juntian Liu
- **时间**: 2026-11-10T08:27:34Z
- **提交信息**: [Perf][EPLB] Copy rebalanced experts back from the buffer in one launch per weight (#66660)

Signed-off-by: Juntian Liu <Juntianl777@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [2858aa5](https://github.com/vllm-project/vllm/commit/2858aa5901cc8b6b09d2ce41efe5a97942a09f82)

- **作者**: Juntian Liu
- **时间**: 2026-11-10T08:26:47Z
- **提交信息**: [Perf][DSv4.1] CuTe DSL mHC boundary for decode batches up to 336 tokens (#66652)

Signed-off-by: Juntian Liu <Juntianl777@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [4fa367b](https://github.com/vllm-project/vllm/commit/4fa367bd8fa6d8ead1fb4cb91cf0037fc4e94015)

- **作者**: Thang Nguyen
- **时间**: 2026-11-10T08:06:53Z
- **提交信息**: [CI] Run the offline examples as pytest and shard the Examples step (#66678)

Signed-off-by: Thang Nguyen <thangnguyenvn647@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [3a10410](https://github.com/vllm-project/vllm/commit/3a104103ac70740824599453c7036edcca1e8548)

- **作者**: Josh Schell
- **时间**: 2026-11-10T07:49:49Z
- **提交信息**: [ROCm] AITER bump to v0.1.29 (#66596)

Signed-off-by: josh schell <josh.schell@amd.com>
Co-authored-by: Micah Williamson <micah.williamson@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [0d96fb6](https://github.com/vllm-project/vllm/commit/0d96fb65891e13f2b1a1037684e59ebff9d26e7a)

- **作者**: Xun Sun
- **时间**: 2026-11-10T07:23:54Z
- **提交信息**: [Fast Start] Seed compiled caches through the D2D transport (#63753)

Signed-off-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>

### [ade4fee](https://github.com/vllm-project/vllm/commit/ade4feed90d9c74baf8c056dbacd2d7324183351)

- **作者**: Jared Wen
- **时间**: 2026-11-10T07:08:39Z
- **提交信息**: [Perf][GLM-5.3-Flash] Specialized decode for GB300 TP4 (#63102)

Signed-off-by: Jared Wen <jaredwen@inferact.ai>
Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [def8588](https://github.com/vllm-project/vllm/commit/def85884a87ee9a5d553193b499257ffa40328f8)

- **作者**: Mark McLoughlin
- **时间**: 2026-11-10T07:00:56Z
- **提交信息**: [Core][Metrics] Collect iteration details during scheduling (#61424)

Signed-off-by: Mark McLoughlin <markmc@redhat.com>
Co-authored-by: Codex <noreply@openai.com>

### [d0014ff](https://github.com/vllm-project/vllm/commit/d0014ff91ca2b5a2656a829ec424823ca6603a52)

- **作者**: Kevin H. Luu
- **时间**: 2026-11-10T06:44:31Z
- **提交信息**: Revert "[ZenCPU] Add zen5 CPU tests reusing the pushed zen image (#60824)" (#66737)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [68776b0](https://github.com/vllm-project/vllm/commit/68776b023c46e89c9b15215e714961c4ab97a38f)

- **作者**: Andreas Karatzas
- **时间**: 2026-11-10T06:31:27Z
- **提交信息**: [ROCm][Bugfix] Remove step-path GPU syncs in EPLB skip-rearrange, AITER GDN prefill metadata, Moondream3 BOS and INT4 RHT signs (#66399)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [499a3d1](https://github.com/vllm-project/vllm/commit/499a3d1e1e338e3e866c0719cfe1f429e2b0b762)

- **作者**: yuvalluria
- **时间**: 2026-11-10T06:02:13Z
- **提交信息**: [Bugfix] Make fused MoE expert weights contiguous before GPU copy in Llama-4 (#65987)

Co-authored-by: Claude Sonnet 5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [9671024](https://github.com/vllm-project/vllm/commit/96710245ece8fe57a0df3ea18cdc79cbb8ce93cf)

- **作者**: Bugen Zhao
- **时间**: 2026-11-10T05:52:43Z
- **提交信息**: [Rust Frontend] Stream DeepSeek DSML tool-call arguments (#66529)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [5219c43](https://github.com/vllm-project/vllm/commit/5219c4336d2a209048ea50bce8a3330da19499fd)

- **作者**: Bugen Zhao
- **时间**: 2026-11-10T05:52:43Z
- **提交信息**: [Rust Frontend] Write tool-call arguments in the template's JSON style (#66528)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [ce3d8c2](https://github.com/vllm-project/vllm/commit/ce3d8c258804926c99e254e1c08ac65c7cd84c18)

- **作者**: Wentao Ye
- **时间**: 2026-11-10T05:50:03Z
- **提交信息**: [Refactor] Clean up MRv1 remaining stuff (#66661)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [d9f94a9](https://github.com/vllm-project/vllm/commit/d9f94a98b32e38143a3171dd4b57d03f48d863e7)

- **作者**: nulllt2
- **时间**: 2026-11-10T05:27:42Z
- **提交信息**: [Bugfix][Model] Avoid host synchronization in dots.ocr vision encoder (#66390)

Signed-off-by: litian <18374328@buaa.edu.cn>
Co-authored-by: litian <18374328@buaa.edu.cn>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [14680ca](https://github.com/vllm-project/vllm/commit/14680ca4bb239bded32d394cdb714dabb4dd1211)

- **作者**: Vineeth Sai Varikuntla
- **时间**: 2026-11-10T05:27:35Z
- **提交信息**: [Frontend] Honour --host for the run-batch Prometheus metrics server (#51859)

Signed-off-by: Vineeth Sai <vineethsai4444@gmail.com>

### [47236ef](https://github.com/vllm-project/vllm/commit/47236ef76e076a7fb469dfc2a3f19f339008b71a)

- **作者**: Hexiang Wang
- **时间**: 2026-11-10T05:23:58Z
- **提交信息**: [Perf][KV Connector][ROCm] MoRIIO WRITE: skip blocks the decoder prefix cache already holds (#65822)

Signed-off-by: whx-sjtu <xiaowang990929@gmail.com>
Co-authored-by: Cursor Agent <cursoragent@cursor.com>

### [bdc7e10](https://github.com/vllm-project/vllm/commit/bdc7e1052a153851559c3ede8aad04274a5283ba)

- **作者**: Oxana Korzh
- **时间**: 2026-11-10T05:23:09Z
- **提交信息**: [ROCm][Perf][DSv4.1] Mono: batch TP8 K2's X8 copies, load its push's peer bases late (#64153)

Signed-off-by: Oxana Korzh <okorzh@amd.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Fangzhou Ai <31551580+Fangzhou-Ai@users.noreply.github.com>

### [d8e1cbb](https://github.com/vllm-project/vllm/commit/d8e1cbb09a9ec599b13fc91fc194d1b1de47a6af)

- **作者**: Oxana Korzh
- **时间**: 2026-11-10T05:22:52Z
- **提交信息**: [ROCm][Perf][DSv4.1] Mono: tuned K1 at TP4 (#63893)

Signed-off-by: Oxana Korzh <okorzh@amd.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [71a550e](https://github.com/vllm-project/vllm/commit/71a550ecd4cebd82e77f6f387eb470b9683cf777)

- **作者**: Fangzhou Ai
- **时间**: 2026-11-10T05:21:40Z
- **提交信息**: [ROCm][DSv4.1] Wire AITER MegaMoE into the V4.1 model (#66644)

Signed-off-by: Fangzhou Ai <fangzhou.ai@amd.com>
Co-authored-by: Claude Sonnet 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [99af156](https://github.com/vllm-project/vllm/commit/99af1568ccbacad0064eeaa2a175991e9ef7472c)

- **作者**: wang.yuqi
- **时间**: 2026-11-10T05:17:26Z
- **提交信息**: [Misc] Normalize filename by replacing typing with types. (#66693)

Signed-off-by: wang.yuqi <yuqi.wang@daocloud.io>

### [ec7b28a](https://github.com/vllm-project/vllm/commit/ec7b28a0ad30200d8e22acf0ad0a7658bb7a6fc5)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-11-10T05:13:50Z
- **提交信息**: [Security] Require native chat encoding in Kimi K3 mode (#66257)

Signed-off-by: Juan Pérez de Algaba <jperezde@redhat.com>
Co-authored-by: Codex <codex@openai.com>

### [738fc72](https://github.com/vllm-project/vllm/commit/738fc72f7edba64e49b0f7b86a7ef6b711b8490c)

- **作者**: Juntian Liu
- **时间**: 2026-11-10T05:13:39Z
- **提交信息**: [Bugfix][DSv4.1] Avoid runtime JIT of two prefill sparse-attention kernels (#66654)

Signed-off-by: Juntian Liu <Juntianl777@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [f1a7d49](https://github.com/vllm-project/vllm/commit/f1a7d49657aa8a23dd5474297c502ddc80eb33a0)

- **作者**: wang.yuqi
- **时间**: 2026-11-10T04:51:48Z
- **提交信息**: [Deprecate] We will remove legacy grpc_server, api_server, and run_batch in v0.37.0. (#66688)

Signed-off-by: wang.yuqi <yuqi.wang@daocloud.io>

### [ec87d33](https://github.com/vllm-project/vllm/commit/ec87d33289e61ea61a67b4ae27bc2cb49a132619)

- **作者**: Lucas Wilkinson
- **时间**: 2026-11-10T04:42:56Z
- **提交信息**: [ROCm][CI] Fix aiter sparse MLA KV-connector test after parameter rename (#66710)

Signed-off-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>

### [7abe724](https://github.com/vllm-project/vllm/commit/7abe7247209d3b4ee80117d56adee25137a159a8)

- **作者**: mikume
- **时间**: 2026-11-10T04:23:02Z
- **提交信息**: [MM] Support mm_device_do_normalize for Qwen2.5-Omni (#66690)

Signed-off-by: gordan12 <gordan941222@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [8afb5e9](https://github.com/vllm-project/vllm/commit/8afb5e9ffeca2fd433f455c0e2b17814aea34c6d)

- **作者**: Hotragn Pettugani
- **时间**: 2026-11-10T04:12:11Z
- **提交信息**: [Bugfix][Frontend] Keep is_embed when round-tripping rendered placeholders (#54548)

Signed-off-by: hotragn <hotragn.pettugani_2024@woxsen.edu.in>
Signed-off-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>
Co-authored-by: aoshen02 <aoshen@inferact.ai>

### [34b495a](https://github.com/vllm-project/vllm/commit/34b495a4d982a0c7f29b0c77021ed751dd2ebb4a)

- **作者**: Ning Liu
- **时间**: 2026-11-10T03:58:56Z
- **提交信息**: [Bugfix][MoE] Only divide shared expert output in FP16 for models that compensate (#65842)

Signed-off-by: Ning Liu <3339723+nliu365@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [24edda7](https://github.com/vllm-project/vllm/commit/24edda7de3bd4eccdbafd6c62fe176801daadaf1)

- **作者**: Shihao Xu
- **时间**: 2026-11-10T03:49:11Z
- **提交信息**: [Model][Quantization] Muse Spark: online FP8 routed experts (fp8_per_channel) on Hopper (#66139)

Signed-off-by: Shihao Xu <shihaoxu@meta.com>
Co-authored-by: Shihao Xu <shihaoxu@meta.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [dc74b8c](https://github.com/vllm-project/vllm/commit/dc74b8cbbbe3dbb9399fe369757d63defd614cc2)

- **作者**: Juntian Liu
- **时间**: 2026-11-10T03:06:11Z
- **提交信息**: [Core] Add max_async_kv_loads_per_step to cap new async KV loads per step (#61725)

Signed-off-by: Juntian Liu <Juntianl777@gmail.com>
Signed-off-by: Yifan Qiao <yifanqiao@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Yifan Qiao <yifanqiao@inferact.ai>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [244b0e1](https://github.com/vllm-project/vllm/commit/244b0e10f0a24d035dfe0541be0bf8c235e88a26)

- **作者**: Andreas Karatzas
- **时间**: 2026-11-10T02:58:06Z
- **提交信息**: [ROCm][CI] Run XPress on MI355 with a GEMM latent MLP and mirror its nightly (#66309)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Signed-off-by: Divakar Verma <divakar.verma@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Divakar Verma <divakar.verma@amd.com>

### [7691ff6](https://github.com/vllm-project/vllm/commit/7691ff6e5b70930b80d09ec14fed84d1a2ea612f)

- **作者**: BaoYunkai
- **时间**: 2026-11-10T02:42:39Z
- **提交信息**: [ROCm][DSv4.1] Avoid runtime JIT for offset combine_topk_swa_indices inputs (#64001)

Signed-off-by: BaoYunkai <ybao@amd.com>

### [5621649](https://github.com/vllm-project/vllm/commit/5621649ce1243d1ded768c88b4d7714fde0d46eb)

- **作者**: Yuedong Wu
- **时间**: 2026-11-10T02:41:04Z
- **提交信息**: [Bugfix][ROCm] Avoid unused index caches in MiniMax-M3 sharing layers (#64403)

Signed-off-by: Yuedong Wu <dwcn22@outlook.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [db1a63c](https://github.com/vllm-project/vllm/commit/db1a63c17812a14f14ec5f21bc0a33eaa5c31a25)

- **作者**: Yifei Wang
- **时间**: 2026-11-10T02:32:14Z
- **提交信息**: [Bugfix][MRV2] Build multimodal prefix-LM attention ranges on every PP stage (#65996)

Signed-off-by: Yifei Wang <yifei.w@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>

### [f7adac3](https://github.com/vllm-project/vllm/commit/f7adac3220eda62e9191aa951b3c4573f08940f8)

- **作者**: Vadim Gimpelson
- **时间**: 2026-11-10T02:31:04Z
- **提交信息**: [Bugfix][Spec Decode] Keep nested-config and YaRN drafts within their rotary cache (#63432)

Signed-off-by: Vadim Gimpelson <vadim.gimpelson@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Francesco Fusco <159429316+fuscof-ibm@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [f10b040](https://github.com/vllm-project/vllm/commit/f10b0408be6bc4d24b00e03653a58395a1dc1c05)

- **作者**: Yifei Wang
- **时间**: 2026-11-10T02:29:03Z
- **提交信息**: [Bugfix][Model] Build the tied embedding on the last PP rank for ERNIE 4.5 MoE and Falcon-H1 (#65983)

Signed-off-by: Yifei Wang <yifei.w@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [dc2137c](https://github.com/vllm-project/vllm/commit/dc2137cd398462c0b1bc5367aeb8d0c56c7ef007)

- **作者**: Jiangyun Zhu
- **时间**: 2026-11-10T02:23:04Z
- **提交信息**: [Model] Kimi K3.1: NVIDIA specialized decode and AMD model updates, ROCm TP8 support (Kimi K3.1 split 4/6) (#66532)

Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>
Signed-off-by: Hongxia Yang <hongxia.yang@amd.com>
Signed-off-by: zjy0516 <zhujiangyun@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Hongxia Yang <hongxia.yang@amd.com>

### [3cfa8ae](https://github.com/vllm-project/vllm/commit/3cfa8ae3a26ff8742cfd299d2b470060dc1c3910)

- **作者**: Yifei Wang
- **时间**: 2026-11-10T02:22:02Z
- **提交信息**: [CI][Test] Add pipeline-parallel equivalence tests for text models (#66291)

Signed-off-by: Yifei Wang <yifei.w@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [3bf570e](https://github.com/vllm-project/vllm/commit/3bf570ec05cd93686acd791905f470a47792933b)

- **作者**: Fangzhou Ai
- **时间**: 2026-11-10T02:20:32Z
- **提交信息**: [ROCm][DSv4.1] Look up only local Engram hashes for peer-read tables (#66500)

Signed-off-by: Fangzhou Ai <fangzhou.ai@amd.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [ee263bc](https://github.com/vllm-project/vllm/commit/ee263bc88afc22a4cc319ce34750f8969c981b41)

- **作者**: Shanshan Shen
- **时间**: 2026-11-10T02:19:41Z
- **提交信息**: [ROCm][UMBP] Support UMBP standalone mode for DeepSeek-V4.1-Flash (#64715)

Signed-off-by: shen-shanshan <467638484@qq.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [7c9a2fa](https://github.com/vllm-project/vllm/commit/7c9a2fa2b3c9e012384fecd40f50c614016e1d35)

- **作者**: Andreas Karatzas
- **时间**: 2026-11-10T01:38:12Z
- **提交信息**: [CI][ROCm] Run EP Weight Filter with EPLB on MI355 (#66306)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [05caae0](https://github.com/vllm-project/vllm/commit/05caae03c20f69436ff7ec23ded339ea104f1a01)

- **作者**: Sahithi Chigurupati
- **时间**: 2026-11-10T00:54:29Z
- **提交信息**: [CI] Fix B200 nightly gsm8k evals: ReplaySSM and DeepEP LL (#66207)

Signed-off-by: Sahithi Chigurupati <chigurupati.sahithi@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [0e0a4dc](https://github.com/vllm-project/vllm/commit/0e0a4dc1e8ab39ca18bc8318a9a5c8e24608aefe)

- **作者**: Yongye Zhu
- **时间**: 2026-11-10T00:42:10Z
- **提交信息**: [Build][MiniMax-M3] Bump fmha_sm100 to 1443786 (#66669)

Signed-off-by: Yongye Zhu <zyy1102000@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [87431e4](https://github.com/vllm-project/vllm/commit/87431e48d3716cf700269d9bf1a199b80e94bf7f)

- **作者**: Chenjie Luo
- **时间**: 2026-11-10T00:30:01Z
- **提交信息**: [Quantization] Support ModelOpt INT8_PB_WO (per-block INT8 weight-only) linear layers (#65272)

Signed-off-by: Chenjie Luo <chenjiel@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Pavani Majety <pmajety@nvidia.com>

### [03ce803](https://github.com/vllm-project/vllm/commit/03ce803be96d8dfba476a1c9090fe3d8a094b5e2)

- **作者**: Thang Nguyen
- **时间**: 2026-11-10T00:14:52Z
- **提交信息**: [CI] Move the MoRIIO unit tests into their own folder and shard the step (#66480)

Signed-off-by: Thang Nguyen <thangnguyenvn647@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [4a87038](https://github.com/vllm-project/vllm/commit/4a870383a1c9c21f02eb16b6be921422a6b8c442)

- **作者**: Thang Nguyen
- **时间**: 2026-11-10T00:14:31Z
- **提交信息**: [CI] Enroll 4 steps in automatic sharding (#66479)

Signed-off-by: Thang Nguyen <thangnguyenvn647@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [ce896d6](https://github.com/vllm-project/vllm/commit/ce896d69cc80bfd8393d457629cfbc3a9427979d)

- **作者**: Thien Tran
- **时间**: 2026-11-10T00:09:09Z
- **提交信息**: [Perf][PP] Copy-engine PP transport, on by default where supported (NVLink only) (#65896)

Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-11-11
**监控日期**: 2026-11-10
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7681
- **最后更新**: 2026-11-11T01:23:12Z

## 提交统计

- **昨日提交总数**: 29
- **提交者数量**: 22
- **主要提交者**: 汪志鹏, dongyang1006, Hniii98

## AI分析总结

## vllm-omni 昨日提交分析（29 条）

### 1. 主要更新类型
- **功能新增（约 8 条）**：新模型/流水线支持（PAN2 文生视频/图生视频、LFM3-Omni-2B Ascend NPU、Flux3 BF16 图像生成、Qwen2.5-Omni FP8 量化）
- **Bug 修复（约 9 条）**：扩散模型图像模糊、长音频输入、CUDA graph 捕获问题、请求清理竞争等
- **性能优化（约 5 条）**：超页 KV cache、VAE 解码前显存回收、VAE 解码间隔调优等
- **CI/构建（约 6 条）**：AMD READY/MERGE 任务提升为阻塞级、测试分片再平衡、A5 测试暂停
- **文档更新（约 4 条）**：MiniMax-H3-Image、IFM/PAN2、Qwen3-TTS 部署配方

### 2. 关键变更点与项目方向的关系
项目定位是"易用、快速、低成本的全模态模型服务"。本批次提交高度契合：
- **多模态广度扩展**：PAN2（视频）、Flux3（图像）、LFM3-Omni-2B（NPU）、Qwen2.5-Omni FP8 量化，直接扩充可服务的模型矩阵，降低成本（量化）与硬件覆盖（Ascend、AMD）。
- **多硬件生态**：AMD/Ascend 相关提交占比显著（CI 提升、fused SHMEM Ulysses all-to-all、显存回收），体现对非 NVIDIA 硬件的持续投入。
- **扩散模型管线成熟**：注意力调度应用到 Wan2.2/HunyuanImage-3.0、采样默认值统一、控制请求清理防护，说明扩散推理是核心工作负载之一。
- **全双工与核心架构**：版本化双工历史快照（#9311）、OmniSerializer 编码缓冲区路径，属底层服务能力加固。

### 3. 对项目的影响和潜在意义
- **稳定性提升**：多个竞态与环境隔离类修复（attention schedule 测试隔离、diffusion controls 围栏）降低回归风险。
- **CI 门禁收紧**：AMD 任务转为阻塞意味着合并质量门槛提高，长期有利于多硬件兼容性保障，但短期可能影响合并速度。
- **性能与显存效率**：超页 KV cache、VAE 解码前显存回收等针对长视频/高分辨率场景的优化，直接呼应"cheap serving"目标。
- **生态友好**：新增多个可复现部署配方（recipe），降低用户上手门槛，符合"for everyone"的定位。

### 4. 值得关注的技术点
- **超页 KV cache + TMA attention**（#9978）：利用 GPU 大页提升注意力加载效率，是较前沿的显存优化手段。
- **版本化双工历史快照**（#9311）：为实时全双工对话提供可回溯的状态管理，是语音交互可靠性的关键。
- **mask-keyed CUDA graphs 在 AR FULL replay 上的选择**（#9911）：涉及 CUDA graph 与动态 mask 的兼容，技术深度较高。
- **FP8 量化仅限 thinker LM**（#3466）：分阶段量化策略，需关注后续对其他组件的扩展。
- **CI 中出现 Claude/Cursor 等 AI 协作者**：反映项目开发流程已纳入 AI 辅助。

### 5. 对项目发展的整体影响
这批提交显示 vllm-omni 正从"功能铺开"转向"多硬件成熟 + 性能打磨"阶段：一方面通过新模型（PAN2、Flux3、LFM3）扩大 omni-modality 覆盖面，另一方面通过 AMD/Ascend CI 门禁、显存与注意力优化夯实 serving 的"fast & cheap"承诺。扩散与全双工两条主线的持续加固，加上部署配方的完善，将直接推动项目向生产可用的全模态服务基础设施演进。

## 详细提交记录

### [2869e5c](https://github.com/vllm-project/vllm-omni/commit/2869e5c3b4adb548ca25ec495ff82e0968ce5418)

- **作者**: Hongxia Yang
- **时间**: 2026-11-10T22:20:25Z
- **提交信息**: [Doc] MiniMax-H3-Image: use minimax-h3-image-rocm image on AMD Instinct (#10129)

Signed-off-by: Hongxia Yang <hongxia.yang@amd.com>
Signed-off-by: andyluo7 <andy.luo@amd.com>
Co-authored-by: andyluo7 <andy.luo@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [0699404](https://github.com/vllm-project/vllm-omni/commit/069940438be8497ba1b3e98cdb63e4c99d1a9ee2)

- **作者**: Yi Gu
- **时间**: 2026-11-10T20:55:22Z
- **提交信息**: [Doc] Add IFM/PAN2 recipe (#10126)

Signed-off-by: Yi Gu <Yi.Gu@mbzuai.ac.ae>

### [2007556](https://github.com/vllm-project/vllm-omni/commit/20075569b08f9702e9e453b02bbb44bc2d3c3205)

- **作者**: blonde
- **时间**: 2026-11-10T19:48:36Z
- **提交信息**: [Bugfix] Fix blurred Stable Diffusion 3.5 images with Cache-DiT when CFG is on (#8747)

Signed-off-by: blonde <164845202+blondeCS@users.noreply.github.com>

### [c4d63a7](https://github.com/vllm-project/vllm-omni/commit/c4d63a7b5b719bacea6aaed3512224181a98093f)

- **作者**: hac17
- **时间**: 2026-11-10T19:28:27Z
- **提交信息**: [CI/Build] Promote three AMD READY jobs to blocking (#10083)

Signed-off-by: hac17 <29197483+hacZ17@users.noreply.github.com>
Co-authored-by: hac17 <29197483+hacZ17@users.noreply.github.com>
Co-authored-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>

### [0e05e83](https://github.com/vllm-project/vllm-omni/commit/0e05e836703d724f699a7c70c422ee7e3f393f5b)

- **作者**: hac17
- **时间**: 2026-11-10T19:27:45Z
- **提交信息**: [CI/Build] Promote three AMD MERGE jobs to blocking (#10082)

Signed-off-by: hac17 <29197483+hacZ17@users.noreply.github.com>
Co-authored-by: hac17 <29197483+hacZ17@users.noreply.github.com>
Co-authored-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>

### [99c1ab5](https://github.com/vllm-project/vllm-omni/commit/99c1ab59091a3569a6011618e269c0f40f96a9fd)

- **作者**: Hniii98
- **时间**: 2026-11-10T17:44:47Z
- **提交信息**: [Bugfix][Step-Audio2] Use native chat format in offline ASR example (#10050)

Signed-off-by: Hniii98 <752608928@qq.com>

### [171ab6a](https://github.com/vllm-project/vllm-omni/commit/171ab6a930b254851aeeb4ad180f5a02f17cf5f9)

- **作者**: Yi Gu
- **时间**: 2026-11-10T16:03:38Z
- **提交信息**: [Model] Add PAN2 text-to-video and image-to-video (#8602)

Signed-off-by: Yi Gu <Yi.Gu@mbzuai.ac.ae>

### [d8751cd](https://github.com/vllm-project/vllm-omni/commit/d8751cd14a854369b5b349eb23c885f595d68ca5)

- **作者**: 汪志鹏
- **时间**: 2026-11-10T14:53:27Z
- **提交信息**: [Doc] Add MiniMax-H3-Image recipes (#10121)

Signed-off-by: princepride <wangzhipeng628@gmail.com>
Co-authored-by: haic0 <149741444+haic0@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [859f150](https://github.com/vllm-project/vllm-omni/commit/859f150595e156fe064d07da21cd05509fe500f1)

- **作者**: Qing7364
- **时间**: 2026-11-10T13:01:47Z
- **提交信息**: [Core] Add versioned duplex history snapshots (#9311)

Signed-off-by: qingpeng <vera.xpq@gmail.com>

### [23ab240](https://github.com/vllm-project/vllm-omni/commit/23ab2406ba4ac03a59b293146dfd2a3fb599d9c8)

- **作者**: Sheng GAO
- **时间**: 2026-11-10T12:23:42Z
- **提交信息**: [CI] Attach OmniServer stderr to startup early-exit errors (#10098)

Signed-off-by: Sheng GAO <sheng.gao.dev@gmail.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: wangyu <53896905+yenuo26@users.noreply.github.com>

### [d613fdb](https://github.com/vllm-project/vllm-omni/commit/d613fdb62c432a342681e88b307d36b54f6ed5f0)

- **作者**: zzh
- **时间**: 2026-11-10T12:14:08Z
- **提交信息**: [Bugfix][MammothModa2] Select mask-keyed CUDA graphs on AR FULL replay (#9911)

Signed-off-by: zzh <943967662@qq.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [3967775](https://github.com/vllm-project/vllm-omni/commit/39677752fee375eddf203c0fc769255f62ebb508)

- **作者**: Weiming Liao
- **时间**: 2026-11-10T11:12:22Z
- **提交信息**: [CI/Build] Temporarily pause A5 Ready tests (#10105)

Signed-off-by: Weiming Liao <liaowm5@gmail.com>

### [09d581b](https://github.com/vllm-project/vllm-omni/commit/09d581bce524987316f923296aa37c0bf0b5e678)

- **作者**: amy-why-3459
- **时间**: 2026-11-10T11:04:14Z
- **提交信息**: [Model] Add LFM3-Omni-2B on Ascend NPU (#9827)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>
Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: Yueqian Lin <linyueqian@outlook.com>

### [976b297](https://github.com/vllm-project/vllm-omni/commit/976b29747f4de9164006434557e5d46eff6c5c6b)

- **作者**: wuli666
- **时间**: 2026-11-10T10:04:26Z
- **提交信息**: [Feature] Add FP8 quantization for Qwen2.5-Omni (thinker LM only) (#3466)

Signed-off-by: wuli666 <djjpro975@gmail.com>
Signed-off-by: wuli666 <421774554@qq.com>
Co-authored-by: wuli666 <djjpro975@gmail.com>

### [124d6b8](https://github.com/vllm-project/vllm-omni/commit/124d6b8ebc5e8a43401aa5017c3b8903ff6b63fd)

- **作者**: Sheehan20
- **时间**: 2026-11-10T10:02:26Z
- **提交信息**: [Doc] Qwen3-TTS: add 0.6B on 1x RTX 4070 Ti SUPER 16GB (#7488)

Signed-off-by: Sheehan20 <li.xiya@northeastern.edu>
Signed-off-by: Sheehan20 <124013480+Sheehan20@users.noreply.github.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: Weiming Liao <fayespica@outlook.com>

### [bdf477b](https://github.com/vllm-project/vllm-omni/commit/bdf477b4a7c80709535f235de2ffd96c0da5f8f6)

- **作者**: Weiming Liao
- **时间**: 2026-11-10T09:31:58Z
- **提交信息**: [Bugfix] Apply sampling defaults across diffusion APIs (#9700)

Signed-off-by: Weiming Liao <liaowm5@gmail.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [40f16e3](https://github.com/vllm-project/vllm-omni/commit/40f16e38849be40b2e4fed930eb8f47f23450b00)

- **作者**: Hniii98
- **时间**: 2026-11-10T07:22:52Z
- **提交信息**: [Bugfix][Step-Audio2] Support long audio input in Thinker (#9927)

Signed-off-by: Hniii98 <752608928@qq.com>

### [2a80279](https://github.com/vllm-project/vllm-omni/commit/2a80279ca6219352b79047c39bc4edfcaefaa9f0)

- **作者**: Chenchao Xu
- **时间**: 2026-11-10T07:22:13Z
- **提交信息**: [Perf] AR-Diffusion: superpage KV cache for TMA attention loads (#9978)

Signed-off-by: chenchaox <chenchaox@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [03720b2](https://github.com/vllm-project/vllm-omni/commit/03720b2dfc3af0b5f3f1dc4402a1dc3b9d9e7ec5)

- **作者**: amy-why-3459
- **时间**: 2026-11-10T06:39:02Z
- **提交信息**: [Benchmark][Omni-DuplexEval] Match the official judge limits (#10069)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [19dd677](https://github.com/vllm-project/vllm-omni/commit/19dd6770babcbf99f9d4205973209172a49367ea)

- **作者**: xiangrong zhong
- **时间**: 2026-11-10T05:47:45Z
- **提交信息**: [Core][Diffusion] Apply attention schedules to Wan2.2 and HunyuanImage-3.0 (#8718)

Signed-off-by: zhongc1211 <huixindaddy@yahoo.com>

### [abd1442](https://github.com/vllm-project/vllm-omni/commit/abd144229ac34c859bce2d41d4bf23f844f14d2d)

- **作者**: Sheng GAO
- **时间**: 2026-11-10T04:38:56Z
- **提交信息**: [BugFix] Isolate attention schedule candidate tests from backend env (#10091)

Signed-off-by: Sheng GAO <sheng.gao.dev@gmail.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [fb70434](https://github.com/vllm-project/vllm-omni/commit/fb70434769827a916dd24d52ddc631a2190d620c)

- **作者**: Yukim1
- **时间**: 2026-11-10T04:13:17Z
- **提交信息**: [Ascend] Add fused SHMEM Ulysses all-to-all (#9510)

Signed-off-by: zwhzzz0821 <zwhzzz0821@users.noreply.github.com>
Co-authored-by: zwhzzz0821 <zwhzzz0821@users.noreply.github.com>
Co-authored-by: dengyunyang <584797741@qq.com>

### [f48a7c7](https://github.com/vllm-project/vllm-omni/commit/f48a7c73e1d8d857f8eabb83d99770b90a83064d)

- **作者**: Isotr0py
- **时间**: 2026-11-10T03:34:03Z
- **提交信息**: [Model] Add Flux3 base BF16 image generation pipeline support (#9523)

Signed-off-by: Isotr0py <Isotr0py@outlook.com>
Signed-off-by: Zhipeng Wang <zhipeng.wang@inferact.ai>
Co-authored-by: Stefan Niebler <82932102+stnie@users.noreply.github.com>
Co-authored-by: Stefan Niebler <74457-sniebler@users.noreply.gitlab-master.nvidia.com>
Co-authored-by: Fabio Camaiora <fcamaiora@nvidia.com>
Co-authored-by: Sandro Cavallari <scavallari@gmail.com>
Co-authored-by: 汪志鹏 <wangzhipeng628@gmail.com>
Co-authored-by: Zhipeng Wang <zhipeng.wang@inferact.ai>

### [fec324d](https://github.com/vllm-project/vllm-omni/commit/fec324dee6dbbccea17a059149b33fd59bc04fee)

- **作者**: dingdangmao
- **时间**: 2026-11-10T03:23:15Z
- **提交信息**: [Core] Add encode_into buffer path for OmniSerializer (#9977)

Signed-off-by: apex-mochen <apex-mochen@users.noreply.github.com>
Signed-off-by: apex-mochen <2756823972@qq.com>
Co-authored-by: apex-mochen <apex-mochen@users.noreply.github.com>

### [90eeebb](https://github.com/vllm-project/vllm-omni/commit/90eeebbd173c2c3cceac75fe299fb98e06813500)

- **作者**: jeffaa729
- **时间**: 2026-11-10T02:28:14Z
- **提交信息**: [Bugfix][MiMo-Audio] Disable dropout before CUDA graph capture (#8607)

Signed-off-by: jeffaa729 <hoiwanglo@gmail.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [ed78daa](https://github.com/vllm-project/vllm-omni/commit/ed78daad94a7011478061cae8c3b99b2ba8e351f)

- **作者**: maithilijoshi20
- **时间**: 2026-11-10T02:26:04Z
- **提交信息**: [Bugfix] Fence diffusion controls against request cleanup (#9856)

Signed-off-by: maithilijoshi20 <97733343+maithilijoshi20@users.noreply.github.com>

### [4ee583c](https://github.com/vllm-project/vllm-omni/commit/4ee583c06072d905c86f64f605f93c0048ec2956)

- **作者**: dongyang1006
- **时间**: 2026-11-10T02:23:58Z
- **提交信息**: [Hardware][Ascend] Reclaim denoise-loop allocator blocks before streaming VAE decode (#9313)

Signed-off-by: dongyang1006 <40831215@qq.com>

### [813618b](https://github.com/vllm-project/vllm-omni/commit/813618b5a22b9106d324aed5057fa14c295eddc6)

- **作者**: Lingwei1943
- **时间**: 2026-11-10T01:56:52Z
- **提交信息**: [perf][VoxCPM2]: default vae_decode_every=2 for zero-buffer continuity  (#8929)

Signed-off-by: Lingwei1943 <lingwei1943@users.noreply.github.com>
Co-authored-by: Lingwei1943 <lingwei1943@users.noreply.github.com>
Co-authored-by: Weiming Liao <liaowm5@gmail.com>

### [49738a8](https://github.com/vllm-project/vllm-omni/commit/49738a8ab80e221be2965a6aac1d4a2438528119)

- **作者**: hac17
- **时间**: 2026-11-10T01:10:13Z
- **提交信息**: [CI/Build] Rebalance AMD Diffusion CPU shards and bound reference-test threads (#10080)

Signed-off-by: hac17 <29197483+hacZ17@users.noreply.github.com>
Signed-off-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>
Co-authored-by: hac17 <29197483+hacZ17@users.noreply.github.com>
Co-authored-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>

---
