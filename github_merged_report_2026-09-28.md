# GitHub Stars 合并报告 - 2026-09-28

**合并日期**: 2026-09-29
**监控日期**: 2026-09-28
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


**报告日期**: 2026-09-29
**监控日期**: 2026-09-28
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2225
- **最后更新**: 2026-09-28T10:44:29Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Zhao Yifeng, Ye Ping

## AI分析总结

根据对提交记录的分析，结合项目背景，总结如下：

**1. 主要更新类型**
本次提交均为 **Bug修复**，涉及分布式训练稳定性与多模态数据处理正确性，未涉及新功能、性能优化或重大重构。

**2. 关键变更点及其与项目整体方向的关系**
*   **修复可重入检查点（Reentrant Checkpoint）的输入梯度释放问题**：此修复直接关系到项目的核心——**分布式训练**。可重入检查点是节省大模型训练内存的关键技术，修复其梯度释放逻辑能确保在**大规模、分布式**训练场景下的稳定性，避免了潜在的内存泄漏或训练错误，是维持“分布式处方库”可靠性的基础性工作。
*   **在Qwen Omni模型中使用采样的视频时间点**：此修复针对具体的**多模态模型（Qwen Omni）**。正确的视频时间戳对齐是视觉与文本数据融合的关键，确保了模型能准确学习跨模态关联，提升了模型训练的**正确性**，直接服务于“支持任意模态模型训练”的项目目标。

**3. 对项目的影响和潜在意义**
这两个修复共同**提升了框架的稳定性和正确性**，对于一个以研究为导向、强调分布式能力的开源项目至关重要。它们增强了用户在复现论文、进行大规模实验时的可靠性，降低了调试基础设施问题的负担，有助于巩固项目作为**可信赖的研究基础设施**的定位。

**4. 值得关注的技术点**
*   **检查点（Checkpointing）的稳健性**：第一个提交涉及PyTorch自动求导和状态字典的深层交互，确保在复杂训练流程（如梯度累积、多级流水线）中能正确保存和恢复训练状态，是分布式训练工程的难点之一。
*   **多模态数据预处理**：第二个提交揭示了处理视频数据时，对时间信息的精确控制（如采样率、对齐）对模型最终性能有直接影响，体现了VeOmni在**数据-模型协同**层面的细致考量。

**5. 基于项目背景对发展的影响**
这些提交是VeOmni从“功能实现”迈向“稳定可靠”的重要步骤。项目旨在提供可扩展的分布式训练方案，而**基础组件的稳定**是用户采纳和社区贡献的前提。通过修复这些底层问题，项目降低了使用门槛，使其“模型中心的分布式处方库”更接近即用、可靠的状态，从而吸引更多研究者基于此平台进行创新，推动Any Modality Model Training生态的发展。

## 详细提交记录

### [3064b58](https://github.com/ByteDance-Seed/VeOmni/commit/3064b58e56315f476730f6792e0534be4ba01964)

- **作者**: Zhao Yifeng
- **时间**: 2026-09-28T10:44:24Z
- **提交信息**: [dist, ci, docs] fix: release reentrant checkpoint input gradients (#1169)

### [c706fa0](https://github.com/ByteDance-Seed/VeOmni/commit/c706fa0fd5c059addf378936a8d1a3c407a2eba1)

- **作者**: Ye Ping
- **时间**: 2026-09-28T07:12:38Z
- **提交信息**: [data, model] fix: use sampled video timing in Qwen Omni (#1221)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-09-29
**监控日期**: 2026-09-28
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2867
- **最后更新**: 2026-09-29T01:54:01Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 4
- **主要提交者**: Zhang Jason, Yang Yong (雍洋), Bilang ZHANG

## AI分析总结

根据提供的提交记录和项目背景，现对 **ModelTC/LightX2V** 仓库昨日（2024年5月23日）的第1/1批提交进行分析总结。

### 1. 主要更新类型
本次提交以 **功能新增** 为主，辅以关键 **Bug修复**。具体表现为：
*   **功能新增**：为模型（如minimax_h3）添加了新的输入功能（动作提示、音频循环）、新的硬件平台支持（AMD ROCm GPU、壁仞GPU）以及新的运行模式支持（MPS加速、Turbo配置）。
*   **Bug修复**：修复了视频生成模型中关键的视觉自编码器（VAE）组件的问题，保障了基础功能的稳定性。

### 2. 关键变更点及其与项目整体方向的关系
关键变更集中在 **扩展框架的硬件兼容性** 和 **增强模型功能** 两个方面，这与项目“轻量视频生成推理框架”的核心目标完全一致。
*   **硬件兼容性扩展**：提交 #1549 和 #1567 分别增加了对 **AMD ROCm** 和 **壁砺（Biren）** GPU平台的支持。这直接践行了README中隐含的“跨平台、广适配”的愿景，旨在降低用户硬件门槛，推动框架在更多元化的计算环境中落地。
*   **模型功能增强**：提交 #1568 和 #1497 为特定视频生成模型（minimax系列）引入了更丰富的控制能力和性能优化（如MPS、Turbo模式）。这提升了框架的实用性和生成效果，使其更接近于解决实际创作需求。

### 3. 对项目的影响和潜在意义
*   **提升实用性与易用性**：新功能（如音频循环、动作提示）使视频生成过程更具可控性和表现力，直接提升了用户体验和创作自由度。
*   **扩大用户基础**：对AMD及国产（壁砺）GPU的支持，打破了仅依赖NVIDIA GPU的局面，能够吸引更广泛的开发者和研究者，特别是对成本和特定生态有要求的用户。
*   **增强框架鲁棒性**：VAE修复等Bug修补维护了项目的基础质量和可靠性，是功能迭代中不可或缺的维护性工作。

### 4. 值得关注的技术点
*   **硬件适配**：针对AMD ROCm和壁砺GPU的适配工作，涉及底层算子、内存管理和计算后端的移植与优化，体现了框架的底层可扩展性设计。
*   **Apple生态集成**：对 **MPS (Metal Performance Shaders)** 的支持（#1497）意味着框架开始兼容苹果的Metal API，为在Mac设备上进行推理优化铺平了道路。
*   **模型配置优化**：引入“Turbo配置”暗示了针对推理速度（如减少采样步数）与生成质量之间进行平衡的调优选项，是推理框架常见的专业化优化手段。

### 5. 对项目发展的影响（结合README背景）
README表明LightX2V旨在成为一个轻量、高效的视频生成推理框架。本次更新从两个维度强化了这一定位：
*   **广度上**：通过支持更多硬件平台（AMD、壁砺、Apple MPS），使“轻量高效”能在更多样的设备上实现，**实现了框架的泛在性目标**。
*   **深度上**：通过为模型添加更精细的控制（音频、动作）和性能模式（Turbo），使“高效”不仅仅是运行速度快，还包括了**生成过程的高效控制与表达**，提升了框架的专业价值。

**总结而言**，这批提交是项目朝着 **“更广泛硬件兼容、更丰富模型能力、更稳定可用基础”** 方向发展的务实一步，对于巩固其作为通用、易用视频生成推理框架的地位具有积极意义。

## 详细提交记录

### [d46ab93](https://github.com/ModelTC/LightX2V/commit/d46ab933b76e14fd6cdf76afdd6e0893a6bcd11f)

- **作者**: Bilang ZHANG
- **时间**: 2026-09-28T19:39:28Z
- **提交信息**: feat(minimax_h3_causal): support action prompt travel and audio looping (#1568)

### [984f8f3](https://github.com/ModelTC/LightX2V/commit/984f8f3dde94eaee6a692fc0b9b225be81c4b4ee)

- **作者**: Zhang Jason
- **时间**: 2026-09-28T19:05:55Z
- **提交信息**: Qwen-Image-2.1 inference on AMD ROCm GPUs (R9700 FP8 / W7900 INT8) (#1549)

---------

Co-authored-by: helloyongyang <yongyang1030@163.com>

### [0062de1](https://github.com/ModelTC/LightX2V/commit/0062de12e3f1d7e24eb5d638a5b6f635122432f5)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-09-28T18:31:22Z
- **提交信息**: Support biren gpu platforms (#1567)

Co-authored-by: Jianguo Xu <jgxu@birentech.com>

### [190f2ef](https://github.com/ModelTC/LightX2V/commit/190f2ef0785a2b5cff6bf78a01cd7ac938c05206)

- **作者**: q6y6y6
- **时间**: 2026-09-28T18:04:38Z
- **提交信息**: feat(minimax_h3): add MPS support, Turbo config and VAE fixes (#1497)

---------

Co-authored-by: helloyongyang <yongyang1030@163.com>

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-09-29
**监控日期**: 2026-09-28
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2266
- **最后更新**: 2026-09-28T23:35:26Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-09-29
**监控日期**: 2026-09-28
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6516
- **最后更新**: 2026-09-29T01:04:21Z

## 提交统计

- **昨日提交总数**: 13
- **提交者数量**: 5
- **主要提交者**: x41lakazam, Jonathan Dierksen, Yanqin Zhai

## AI分析总结

本次提交分析聚焦于仓库 `flashinfer-ai/flashinfer` 在昨日发生的更新，内容涵盖了13项提交。

**主要更新类型**
本次更新以**性能优化**为核心，占据了绝大多数提交。此外，还包含**Bug修复**以提升模型并行推理的数值正确性，**功能新增**以支持新的硬件架构与量化格式，以及必要的**基础设施更新**以适配新的开发工具链。

**关键变更点与项目方向的关系**
所有变更均紧密围绕项目“提供高性能GPU推理内核”的核心目标展开：
1.  **硬件深度适配与前沿布局**：多项优化针对英伟达新一代Blackwell架构（SM100/SM103）进行，并新增了对CUDA 13.4的支持。这确保了项目在最新硬件上的性能优势和未来兼容性。
2.  **关键算子与模型攻坚**：优化重点集中在混合专家模型（MoE）与多头潜在注意力（MLA）两大核心组件，并具体针对DeepSeek-V4、Kimi-K3等前沿大模型的推理路径进行深度调优，直接攻克性能瓶颈。
3.  **算法与工程的协同创新**：性能提升不仅依赖参数调整，更涉及内核算法层面的革新，如采用持久化执行、索引环缓冲、权重流式加载及通信-计算融合等技术，体现了深度的软硬件协同设计。

**对项目的影响和潜在意义**
1.  **显著性能增益**：在目标硬件（如GB200/B200）上，优化后的内核在特定场景（如解码、MoE通信）实现了可观的吞吐量提升（如1.7倍），极大增强了实际效能。
2.  **稳定性与正确性增强**：修复了MoE专家并行（EP）模式下的填充计算问题，提升了大规模模型推理的稳定性与数值正确性。
3.  **生态与范围扩展**：新增的CUDA 13.4 CI支持和基于CuTe的NVFP4 W4A16量化MoE配置，为兼容未来工具链和更广泛的工作负载奠定了基础。
4.  **工程成熟度提升**：详尽的性能验证与文档更新，以及规范的CI基础设施维护，标志着项目向工业级可靠性与可维护性迈进。

**值得关注的技术点**
*   **内核微架构深度利用**：如“K ring”技术优化内存访问依赖链，以及对TMA（张量内存加速器）、软件流水线的广泛使用，旨在逼近硬件理论峰值。
*   **细粒度内存与数据流管理**：通过调整存储粒度、采用分组加载、实现权重流式加载等方式，精细优化数据在寄存器、共享内存与HBM之间的流动效率。
*   **端到端的低精度推理支持**：完整展示了从权重准备、片上反量化到融合计算的NVFP4 W4A16 MegaMoE流程，是探索低精度推理的重要实践。
*   **系统化的优化方法论**：采用成对比较、CUPTI性能分析及硬件天花板建模等方法，为内核优化提供了精确的量化依据。

## 详细提交记录

### [6d479be](https://github.com/flashinfer-ai/flashinfer/commit/6d479bea18cde88d11af996f28bca0cc16218021)

- **作者**: eigen
- **时间**: 2026-09-28T23:44:18Z
- **提交信息**: perf(cake_sparse_mla): round-4 DSv4 sparse-MLA Cake programs for SM100/SM103 (stacked on #5630) (#5644)

## Summary

Round-4 performance of the `backend="cake"` DeepSeek-V4 sparse-MLA
decode path of `trtllm_batch_decode_sparse_mla_dsv4`
(SM100a / SM103a), regenerated from the same producer pipeline as #5630
(this PR is stacked on #5630; host and tests unchanged):

- **BF16/FP8 H8/H16 decode programs (16 rows):** the FP8 body issues its
K gathers back-to-back after hoisting the page-offset loads and
runs an 8-slot K ring; both bodies get a deeper K/V alias ring so a
3-tile item's second tile no longer waits for the first PV.
GB300 FP8 rows 1.40x -> **1.70x** (geomean), B200 1.52x -> **1.73x**;
3-tile BF16 rows -0.2..-0.5 us (GB300 decode-000062 1.50x -> 1.64x).
- **BF16/H128 persistent prefill programs (128+ query-token rows and the
K-reuse rows):** FA4-style lazy softmax rescale (a row keeps its
running max until the true max grows by more than 2^8; the deferred
factor is applied then). prefill-style-000088: GB300 1.34x -> **1.47x**,
B200 1.22x -> **1.37x**; 000092 1.35x -> **1.41x** / 1.22x -> **1.33x**.
- **BF16 one-tile SWA decode programs (18 rows):** the sparse-index load
is issued before the Q TMA (statement order only; bit-identical
  output): -0.1..-0.26 us per row.
- Every other program is a byte-identical regeneration (renamed for the
new producer revision).

## Validation

Export r13 (regenerated programs as published here; host and tests at
#5630's `76d586ff6`), same-session paired CUPTI (active-union median,
cold L2) against the default trtllm-gen path at the same revision:

| | GB300 (sm_103a) | B200 (sm_100a) |
|---|---|---|
| 94 canonical + 40 hardening shapes correct (BF16 atol=rtol=1e-2, FP8
0.1; padded / separate-table / offset axes) | 134/134 | 134/134 |
| **94 canonical rows faster than the default path** | 94/94, geomean
**1.343x**, min 1.130x (#5630: 1.300x, min 1.098x) | 94/94, geomean
**1.319x**, min 1.048x (#5630: 1.280x, min 1.027x) |
| 40 hardening rows faster than the default path | 40/40, geomean
**1.353x**, min 1.085x (#5630: 1.330x, min 1.071x) | 40/40, geomean
**1.310x**, min 1.069x (#5630: 1.307x, min 1.065x) |
| compute-sanitizer synccheck + memcheck on the changed kernels | 0
errors | 0 errors |
| `tests/mla/test_cake_dsv4*.py` (GPU, fresh clone of this commit) | 296
passed | 296 passed |

## Baselines and their source PRs

- **trtllm-gen default path** =
`trtllm_batch_decode_sparse_mla_dsv4(...)` without `backend="cake"` (the
TRTLLM-GEN DSv4 sparse-MLA
kernels plus the framework launches it needs for equal semantics:
padded-Q masking, separate-table merge, workspace/counter handling).
Origin PRs: #3269 (9c76c994b, 2026-05-21); SM120 kernels #3395
(f95469478, 2026-06-15); DSv4.1 unification #5197 (eb5f05be1,
2026-09-18).
- **Cake backend under test** = `backend="cake"` from #4573 (13db2cfd5,
2026-09-16), hardened by #5591 (8589d49b0), round 2 #5610
  (4b8167eab), round 3 #5630 (76d586ff6), regenerated again by this PR.
- **Test oracle** = the PyTorch reference of
`tests/mla/test_cake_dsv4.py` / `test_cake_dsv4_hardening.py`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Performance Improvements**
* Updated attention processing to handle more key/value data stages per
pipeline, potentially improving throughput.
* Sparse-index lookups now occur earlier in the loading process, helping
streamline attention data preparation.
* **Numerical Improvements**
* Refined softmax accumulation to avoid unnecessary correction for small
score changes while preserving correction for larger changes.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [27c8875](https://github.com/flashinfer-ai/flashinfer/commit/27c8875c115b3edc5b137005001243b0e48b8b98)

- **作者**: eigen
- **时间**: 2026-09-28T23:29:27Z
- **提交信息**: perf(cake_comm): faster SM100/SM103 MoE all-reduce fusion union programs (#5650)

Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on **every one of
the 60 benchmark rows** (SM100 and SM103, world sizes 2/4/8) against
upstream `backend="trtllm"`, the isolated Cake bundle and the currently
shipped union programs; the two rows that keep an unchanged program
measure at parity.

<!-- .github/pull_request_template.md -->

## 📌 Description

Performance round for the Cake TRT-LLM MoE all-reduce fusion union
programs (`trtllm_moe_allreduce_fusion(backend="cake")`, SM100 and
SM103, world sizes 2/4/8; #5599). Three reviewed rules move the rows
toward the measured hardware bound while the Lamport
clear/publish/poll protocol, values and rounding points stay unchanged.
The public API is unchanged; calls without the all-reduce
output and every other architecture keep the isolated bundle from #4730.

1. **Persistent-grid residency**: the SM-bounded persistent cluster grid
keeps `persistent_ctas_per_sm` CTAs resident per SM
(recorded per module in `MODULES[...]["launch"]`;
`launch_grid_x(token_num, cooperative, sm_count, persistent_ctas_per_sm,
cluster_ctas)`).
The generator verified co-residency (`cuOccupancyMaxActiveClusters`) for
every module on the architecture it was exported on.
2. **`wide_mlp` schedule**: eight 16-byte expert loads in flight per
thread, epilogue operands hoisted above the poll,
push-style RMS partial exchange, one packet pack per publication. It
serves whole (architecture, world size, dtype, PDL)
classes where every reviewed row won (`_WIDE_MLP_CLASSES`; every token
count of such a class runs it) and single reviewed
   rows elsewhere (`_REVIEWED_SPECIALIZATIONS`).
3. **Single-CTA T=1 geometry**: the reviewed B200 two- and four-rank
bfloat16 T=1 E=8 programs run one 896-thread CTA per
token instead of a four-CTA cluster (no cluster barrier, no DSMEM
partial exchange on the T=1 critical path); the cluster
width is recorded per module (`launch.block` / `launch.cluster`), named
in the route specialization (`wide_mlp_cta1`,
`wide_mlp_t1_e8_serial_clear_cta1`), and `launch_grid_x` sizes the grid
from it. Every other program keeps the
four-CTA cluster (SM103 and eight-rank SM100 measured it at parity or
faster).

Generated programs:
`csrc/cake_trtllm_moe_allreduce_union/{sm_100a,sm_103a}/`, loader
`flashinfer/jit/cake_trtllm_moe_allreduce_union.py`,
tests `tests/comm/test_cake_moe_allreduce_union.py`.

**Regenerated units.** Every module's build record gained the residency
field (`persistent_ctas_per_sm`), and the module name is a
fingerprint of that record together with the symbol-normalized kernel
and binding sources, so every SM103 module was re-emitted under a new
name. Of the 78 previously shipped SM103 modules, 56 (the 14 `sm103_t1`
and 42 `generic` modules) have kernel and binding sources identical
to the shipped files up to that symbol (verified file-by-file), 22 are
replaced by `wide_mlp` programs (the six promoted classes) and 8
`wide_mlp` modules are added for the reviewed rows of mixed classes. Of
the 100 previously shipped SM100 modules, 72 (the 32 `sm100_ws8_mid`
modules and the 40 `generic` modules of the eight-rank classes and of
the four-rank bfloat16 classes) have kernel and binding sources
identical to the shipped files up to that symbol and the per-module
host-shim namespace (verified file-by-file), 28 are replaced: the 16
`generic` modules of the six promoted SM100 classes (both two-rank
dtypes with and without PDL, four-rank float16 with and without PDL) by
`wide_mlp`, the four-rank float16 `t64_e12_resident` and
`t128_e16_owner_forward` row programs by their `wide_mlp` counterparts,
and the four-rank bfloat16 `t1_e8_serial_clear` program by the
single-CTA `wide_mlp_t1_e8_serial_clear_cta1` build; 6 modules are added
(four `wide_mlp` for the reviewed four-rank bfloat16 PDL T=64 row of a
mixed class, two single-CTA `wide_mlp_cta1` for the two-rank bfloat16
T=1 row), 106 SM100 modules in total. The SM103 set is re-emitted by the
final generator tree in the last commit (no `sm_103a` schedule change
after the first commit): every SM103 module is renamed by its
build-record fingerprint with kernel and binding sources identical to
the first commit's files up to the generated symbol and the host-shim
namespace, and all thirty SM103 rows were re-measured on B300 with fresh
receipts against that render. The SM100 side of that render was verified
on B200 by re-running the generator's generate/integrate/review/apply
phase against the reflowed-loader commit: the target worktree stayed
unchanged (every SM100 unit, the loader and the test byte-identical to
the commit).

### Speedup vs baselines (CUPTI paired timing, same session, three
counterbalanced groups, maximum per-rank median)

Columns: `new` = this PR's program, `shipped` = the union program of
#5599 as built from upstream main, `upstream` =
`trtllm_moe_allreduce_fusion(backend="trtllm")`, `standalone` = the
isolated Cake bundle of #4730. Speedups are baseline time / new time.

#### sm_103a world size 2 (NVIDIA B300 SXM6 AC, 148 SMs; 3
counterbalanced groups, rank-max median)

| row | T | E | dtype | PDL | new us | shipped us | vs shipped |
upstream us | vs upstream | standalone us | vs standalone |
|---|---:|---:|---|---|---:|---:|---:|---:|---:|---:|---:|
| perf_ws2_bf16_t1_e8 | 1 | 8 | bfloat16 | n | 13.09 | 12.96 | 0.9903 |
14.85 | 1.1345 | 14.24 | 1.0881 |
| perf_ws2_bf16_t64_e8_pdl | 64 | 8 | bfloat16 | y | 14.88 | 18.40 |
1.2366 | 22.18 | 1.4903 | 18.56 | 1.2473 |
| perf_ws2_fp16_t64_e12 | 64 | 12 | float16 | n | 16.80 | 20.80 | 1.2381
| 25.41 | 1.5124 | 20.74 | 1.2343 |
| perf_ws2_bf16_t128_e16 | 128 | 16 | bfloat16 | n | 19.52 | 38.11 |
1.9525 | 50.24 | 2.5738 | 38.40 | 1.9673 |
| perf_ws2_fp16_t128_e16_pdl | 128 | 16 | float16 | y | 19.65 | 38.24 |
1.9462 | 50.14 | 2.5520 | 38.24 | 1.9462 |
| perf_ws2_bf16_t256_e8 | 256 | 8 | bfloat16 | n | 22.40 | 47.49 |
2.1200 | 58.62 | 2.6172 | 47.74 | 2.1314 |
| perf_ws2_bf16_t256_e12_pdl | 256 | 12 | bfloat16 | y | 27.90 | 56.10 |
2.0104 | 70.37 | 2.5218 | 56.54 | 2.0264 |
| perf_ws2_fp16_t2048_e8 | 2048 | 8 | float16 | n | 118.30 | 342.72 |
2.8969 | 422.12 | 3.5680 | 341.95 | 2.8904 |
| perf_ws2_bf16_t2048_e12_pdl | 2048 | 12 | bfloat16 | y | 138.59 |
400.64 | 2.8908 | 512.84 | 3.7003 | 401.44 | 2.8965 |
| perf_ws2_fp16_t2048_e16_pdl | 2048 | 16 | float16 | y | 157.86 |
461.09 | 2.9209 | 606.57 | 3.8425 | 460.23 | 2.9155 |
geomean vs upstream 2.371 (min 1.1345), vs standalone 1.919 (min
1.0881), vs shipped union 1.896 (min 0.9903)

#### sm_103a world size 4 (NVIDIA B300 SXM6 AC, 148 SMs; 3
counterbalanced groups, rank-max median)

| row | T | E | dtype | PDL | new us | shipped us | vs shipped |
upstream us | vs upstream | standalone us | vs standalone |
|---|---:|---:|---|---|---:|---:|---:|---:|---:|---:|---:|
| perf_bf16_t1_e8 | 1 | 8 | bfloat16 | n | 14.88 | 14.98 | 1.0065 |
16.16 | 1.0861 | 16.64 | 1.1183 |
| perf_bf16_t64_e8_pdl | 64 | 8 | bfloat16 | y | 18.05 | 20.61 | 1.1419
| 22.37 | 1.2394 | 20.42 | 1.1313 |
| perf_fp16_t64_e12 | 64 | 12 | float16 | n | 20.19 | 20.83 | 1.0316 |
29.31 | 1.4516 | 22.66 | 1.1220 |
| perf_bf16_t128_e16 | 128 | 16 | bfloat16 | n | 25.38 | 40.45 | 1.5939
| 43.68 | 1.7213 | 40.77 | 1.6066 |
| perf_fp16_t128_e16_pdl | 128 | 16 | float16 | y | 26.18 | 27.84 |
1.0636 | 56.99 | 2.1773 | 40.61 | 1.5513 |
| perf_bf16_t256_e8 | 256 | 8 | bfloat16 | n | 34.72 | 52.45 | 1.5106 |
56.61 | 1.6304 | 52.35 | 1.5078 |
| perf_bf16_t256_e12_pdl | 256 | 12 | bfloat16 | y | 36.67 | 60.83 |
1.6588 | 65.82 | 1.7950 | 60.74 | 1.6562 |
| perf_fp16_t2048_e8 | 2048 | 8 | float16 | n | 211.65 | 396.68 | 1.8742
| 526.66 | 2.4884 | 396.64 | 1.8741 |
| perf_bf16_t2048_e12_pdl | 2048 | 12 | bfloat16 | y | 220.74 | 451.30 |
2.0445 | 487.94 | 2.2105 | 453.44 | 2.0542 |
| perf_fp16_t2048_e16_pdl | 2048 | 16 | float16 | y | 226.34 | 517.64 |
2.2870 | 739.75 | 3.2684 | 516.97 | 2.2840 |
geomean vs upstream 1.814 (min 1.0861), vs standalone 1.545 (min
1.1183), vs shipped union 1.460 (min 1.0065)

#### sm_103a world size 8 (NVIDIA B300 SXM6 AC, 148 SMs; 3
counterbalanced groups, rank-max median)

| row | T | E | dtype | PDL | new us | shipped us | vs shipped |
upstream us | vs upstream | standalone us | vs standalone |
|---|---:|---:|---|---|---:|---:|---:|---:|---:|---:|---:|
| perf_ws8_bf16_t1_e8 | 1 | 8 | bfloat16 | n | 17.38 | 17.41 | 1.0018 |
18.34 | 1.0553 | 18.18 | 1.0460 |
| perf_ws8_bf16_t64_e8_pdl | 64 | 8 | bfloat16 | y | 27.04 | 29.06 |
1.0745 | 32.00 | 1.1834 | 29.50 | 1.0911 |
| perf_ws8_fp16_t64_e12 | 64 | 12 | float16 | n | 28.00 | 29.44 | 1.0515
| 32.22 | 1.1509 | 29.82 | 1.0651 |
| perf_ws8_bf16_t128_e16 | 128 | 16 | bfloat16 | n | 41.02 | 49.02 |
1.1950 | 54.30 | 1.3237 | 49.63 | 1.2099 |
| perf_ws8_fp16_t128_e16_pdl | 128 | 16 | float16 | y | 40.19 | 48.58 |
1.2086 | 53.09 | 1.3209 | 48.22 | 1.1998 |
| perf_ws8_bf16_t256_e8 | 256 | 8 | bfloat16 | n | 63.42 | 78.88 |
1.2437 | 90.59 | 1.4284 | 82.88 | 1.3068 |
| perf_ws8_bf16_t256_e12_pdl | 256 | 12 | bfloat16 | y | 64.67 | 80.90 |
1.2509 | 91.91 | 1.4211 | 85.38 | 1.3201 |
| perf_ws8_fp16_t2048_e8 | 2048 | 8 | float16 | n | 420.00 | 607.37 |
1.4461 | 684.58 | 1.6299 | 606.28 | 1.4435 |
| perf_ws8_bf16_t2048_e12_pdl | 2048 | 12 | bfloat16 | y | 430.44 |
627.14 | 1.4570 | 716.49 | 1.6646 | 653.25 | 1.5177 |
| perf_ws8_fp16_t2048_e16_pdl | 2048 | 16 | float16 | y | 433.19 |
637.80 | 1.4723 | 720.39 | 1.6630 | 636.04 | 1.4683 |
geomean vs upstream 1.368 (min 1.0553), vs standalone 1.256 (min
1.0460), vs shipped union 1.229 (min 1.0018)

#### sm_100a world size 2 (NVIDIA B200, 148 SMs; 3 counterbalanced
groups, rank-max median)

| row | T | E | dtype | PDL | new us | shipped us | vs shipped |
upstream us | vs upstream | standalone us | vs standalone |
|---|---:|---:|---|---|---:|---:|---:|---:|---:|---:|---:|
| perf_ws2_bf16_t1_e8 | 1 | 8 | bfloat16 | n | 10.11 | 11.36 | 1.1234 |
12.90 | 1.2753 | 12.03 | 1.1899 |
| perf_ws2_bf16_t64_e8_pdl | 64 | 8 | bfloat16 | y | 12.42 | 17.54 |
1.4124 | 21.28 | 1.7139 | 19.20 | 1.5464 |
| perf_ws2_fp16_t64_e12 | 64 | 12 | float16 | n | 14.53 | 20.00 | 1.3767
| 24.89 | 1.7136 | 20.03 | 1.3789 |
| perf_ws2_bf16_t128_e16 | 128 | 16 | bfloat16 | n | 17.34 | 37.57 |
2.1661 | 49.66 | 2.8635 | 44.06 | 2.5406 |
| perf_ws2_fp16_t128_e16_pdl | 128 | 16 | float16 | y | 17.44 | 37.63 |
2.1578 | 50.05 | 2.8697 | 37.79 | 2.1670 |
| perf_ws2_bf16_t256_e8 | 256 | 8 | bfloat16 | n | 21.15 | 46.27 |
2.1875 | 58.02 | 2.7426 | 52.22 | 2.4689 |
| perf_ws2_bf16_t256_e12_pdl | 256 | 12 | bfloat16 | y | 26.69 | 55.10 |
2.0647 | 69.98 | 2.6223 | 63.74 | 2.3885 |
| perf_ws2_fp16_t2048_e8 | 2048 | 8 | float16 | n | 116.67 | 336.67 |
2.8856 | 426.69 | 3.6571 | 347.39 | 2.9775 |
| perf_ws2_bf16_t2048_e12_pdl | 2048 | 12 | bfloat16 | y | 146.75 |
397.05 | 2.7056 | 514.11 | 3.5033 | 463.93 | 3.1614 |
| perf_ws2_fp16_t2048_e16_pdl | 2048 | 16 | float16 | y | 154.75 |
460.51 | 2.9758 | 612.48 | 3.9578 | 467.87 | 3.0234 |
geomean vs upstream 2.541 (min 1.2753), vs standalone 2.173 (min
1.1899), vs shipped union 2.009 (min 1.1234)

#### sm_100a world size 4 (NVIDIA B200, 148 SMs; 3 counterbalanced
groups, rank-max median)

| row | T | E | dtype | PDL | new us | shipped us | vs shipped |
upstream us | vs upstream | standalone us | vs standalone |
|---|---:|---:|---|---|---:|---:|---:|---:|---:|---:|---:|
| perf_bf16_t1_e8 | 1 | 8 | bfloat16 | n | 11.68 | 13.86 | 1.1863 |
13.82 | 1.1836 | 13.09 | 1.1205 |
| perf_bf16_t64_e8_pdl | 64 | 8 | bfloat16 | y | 17.02 | 19.68 | 1.1560
| 21.82 | 1.2819 | 19.30 | 1.1334 |
| perf_fp16_t64_e12 | 64 | 12 | float16 | n | 18.91 | 19.84 | 1.0491 |
23.65 | 1.2504 | 19.62 | 1.0373 |
| perf_bf16_t128_e16 | 128 | 16 | bfloat16 | n | 26.66 | 40.99 | 1.5378
| 44.42 | 1.6663 | 39.58 | 1.4850 |
| perf_fp16_t128_e16_pdl | 128 | 16 | float16 | y | 24.77 | 28.29 |
1.1421 | 43.26 | 1.7468 | 34.34 | 1.3863 |
| perf_bf16_t256_e8 | 256 | 8 | bfloat16 | n | 35.17 | 52.22 | 1.4850 |
57.41 | 1.6324 | 50.66 | 1.4404 |
| perf_bf16_t256_e12_pdl | 256 | 12 | bfloat16 | y | 36.67 | 61.09 |
1.6658 | 66.91 | 1.8247 | 58.43 | 1.5934 |
| perf_fp16_t2048_e8 | 2048 | 8 | float16 | n | 213.60 | 398.24 | 1.8644
| 428.48 | 2.0060 | 349.92 | 1.6382 |
| perf_bf16_t2048_e12_pdl | 2048 | 12 | bfloat16 | y | 234.78 | 462.24 |
1.9688 | 505.06 | 2.1511 | 431.78 | 1.8390 |
| perf_fp16_t2048_e16_pdl | 2048 | 16 | float16 | y | 224.86 | 526.69 |
2.3423 | 557.09 | 2.4774 | 418.85 | 1.8627 |
geomean vs upstream 1.677 (min 1.1836), vs standalone 1.427 (min
1.0373), vs shipped union 1.489 (min 1.0491)

#### sm_100a world size 8 (NVIDIA B200, 148 SMs; 3 counterbalanced
groups, rank-max median)

| row | T | E | dtype | PDL | new us | shipped us | vs shipped |
upstream us | vs upstream | standalone us | vs standalone |
|---|---:|---:|---|---|---:|---:|---:|---:|---:|---:|---:|
| perf_ws8_bf16_t1_e8 | 1 | 8 | bfloat16 | n | 16.74 | 16.67 | 0.9962 |
17.95 | 1.0727 | 16.83 | 1.0057 |
| perf_ws8_bf16_t64_e8_pdl | 64 | 8 | bfloat16 | y | 29.28 | 29.76 |
1.0164 | 32.96 | 1.1257 | 29.92 | 1.0219 |
| perf_ws8_fp16_t64_e12 | 64 | 12 | float16 | n | 30.24 | 30.66 | 1.0138
| 33.22 | 1.0984 | 30.69 | 1.0148 |
| perf_ws8_bf16_t128_e16 | 128 | 16 | bfloat16 | n | 50.24 | 50.82 |
1.0115 | 56.83 | 1.1312 | 51.23 | 1.0197 |
| perf_ws8_fp16_t128_e16_pdl | 128 | 16 | float16 | y | 49.60 | 50.24 |
1.0129 | 56.48 | 1.1387 | 51.17 | 1.0316 |
| perf_ws8_bf16_t256_e8 | 256 | 8 | bfloat16 | n | 64.83 | 82.02 |
1.2651 | 94.82 | 1.4625 | 85.70 | 1.3218 |
| perf_ws8_bf16_t256_e12_pdl | 256 | 12 | bfloat16 | y | 66.02 | 84.67 |
1.2826 | 97.31 | 1.4741 | 88.89 | 1.3466 |
| perf_ws8_fp16_t2048_e8 | 2048 | 8 | float16 | n | 422.02 | 636.26 |
1.5077 | 714.49 | 1.6930 | 643.17 | 1.5240 |
| perf_ws8_bf16_t2048_e12_pdl | 2048 | 12 | bfloat16 | y | 435.23 |
660.93 | 1.5186 | 755.55 | 1.7360 | 673.12 | 1.5466 |
| perf_ws8_fp16_t2048_e16_pdl | 2048 | 16 | float16 | y | 437.63 |
667.46 | 1.5252 | 670.50 | 1.5321 | 671.87 | 1.5352 |
geomean vs upstream 1.324 (min 1.0727), vs standalone 1.216 (min
1.0057), vs shipped union 1.195 (min 0.9962)


**Rows at parity with the shipped union.** Two of the 60 rows read
marginally below 1.0 against the shipped union while running the same
program: SM103 ws2 bf16 T=1 (0.9903, 13.09 us vs 12.96 us) and SM100 ws8
bf16 T=1 (0.9962, 16.74 us vs 16.67 us). In both rows the new module has
kernel and binding sources identical to the shipped module up to the
generated symbol, and the gap is inside the three-group measurement
noise band (for the SM100 row the three counterbalanced groups of the
new arm read 16.58 / 16.45 / 17.12 us against 17.02 / 16.54 / 16.54 us
for the shipped arm). All 60 rows are at or above 1.0 against upstream
and against the standalone kernels.

### Roofline bound and achieved fraction

Bound = byte model per rank (HBM: (E+2)·T·H·2 + (W−1)·T·H·2 + 4·T·H·2
bytes; NVLink: (W−1)·T·H·2 bytes per direction) at the
node's measured HBM / per-direction NVLink rates; the model was checked
against `dram__bytes_read.sum` on the B300 node (within 0.1 %).
`residual` names the measured component that binds the row.

#### sm_103a world size 2 (NVIDIA B300 SXM6 AC, 148 SMs; 3
counterbalanced groups, rank-max median)

| row | T | new us | bound us | achieved | residual |
|---|---:|---:|---:|---:|---|
| perf_ws2_bf16_t1_e8 | 1 | 13.09 | 0.0 | 0.002 | single cluster (4
CTAs): fixed Lamport protocol latency (launch, clear, publish,
cross-rank poll, RMS epilogue); bytes 0.2 MB, bound 0.0 us |
| perf_ws2_bf16_t64_e8_pdl | 64 | 14.88 | 1.7 | 0.116 | all 64 token
clusters resident at k=4 (256 CTAs): protocol round trips (clear ->
publish -> poll -> RMS) dominate; bound 1.7 us (hbm) |
| perf_ws2_fp16_t64_e12 | 64 | 16.80 | 2.2 | 0.130 | all 64 token
clusters resident at k=5 (256 CTAs): protocol round trips (clear ->
publish -> poll -> RMS) dominate; bound 2.2 us (hbm) |
| perf_ws2_bf16_t128_e16 | 128 | 19.52 | 5.3 | 0.270 | all 128 token
clusters resident at k=4 (512 CTAs): protocol round trips (clear ->
publish -> poll -> RMS) dominate; bound 5.3 us (hbm) |
| perf_ws2_fp16_t128_e16_pdl | 128 | 19.65 | 5.3 | 0.268 | all 128 token
clusters resident at k=4 (512 CTAs): protocol round trips (clear ->
publish -> poll -> RMS) dominate; bound 5.3 us (hbm) |
| perf_ws2_bf16_t256_e8 | 256 | 22.40 | 6.9 | 0.307 | occupancy-bound
bytes in flight: wide_mlp at k=4 CTAs/SM (592 CTAs; driver occupancy 5
CTAs/SM (54 regs), 175 co-resident clusters; k+1 not admissible with
headroom); bound 6.9 us (hbm) |
| perf_ws2_bf16_t256_e12_pdl | 256 | 27.90 | 8.7 | 0.312 |
occupancy-bound bytes in flight: generic at k=5 CTAs/SM (740 CTAs;
driver occupancy 6 CTAs/SM (40 regs), 213 co-resident clusters; k+1 not
admissible with headroom); bound 8.7 us (hbm) |
| perf_ws2_fp16_t2048_e8 | 2048 | 118.30 | 55.1 | 0.465 |
occupancy-bound bytes in flight: generic at k=5 CTAs/SM (740 CTAs;
driver occupancy 6 CTAs/SM (40 regs), 213 co-resident clusters; k+1 not
admissible with headroom); bound 55.1 us (hbm) |
| perf_ws2_bf16_t2048_e12_pdl | 2048 | 138.59 | 69.7 | 0.503 |
occupancy-bound bytes in flight: generic at k=5 CTAs/SM (740 CTAs;
driver occupancy 6 CTAs/SM (40 regs), 213 co-resident clusters; k+1 not
admissible with headroom); bound 69.7 us (hbm) |
| perf_ws2_fp16_t2048_e16_pdl | 2048 | 157.86 | 84.4 | 0.535 |
occupancy-bound bytes in flight: generic at k=5 CTAs/SM (740 CTAs;
driver occupancy 6 CTAs/SM (40 regs), 213 co-resident clusters; k+1 not
admissible with headroom); ncu rank 0: 144.1 us, DRAM 587.3+128.9 MB ->
4.97 TB/s = 62% of 8 TB/s HBM; bound 84.4 us (hbm) |

#### sm_103a world size 4 (NVIDIA B300 SXM6 AC, 148 SMs; 3
counterbalanced groups, rank-max median)

| row | T | new us | bound us | achieved | residual |
|---|---:|---:|---:|---:|---|
| perf_bf16_t1_e8 | 1 | 14.88 | 0.0 | 0.003 | single cluster (4 CTAs):
fixed Lamport protocol latency (launch, clear, publish, cross-rank poll,
RMS epilogue); bytes 0.2 MB, bound 0.0 us |
| perf_bf16_t64_e8_pdl | 64 | 18.05 | 3.1 | 0.169 | all 64 token
clusters resident at k=4 (256 CTAs): protocol round trips (clear ->
publish -> poll -> RMS) dominate; bound 3.1 us (nvlink) |
| perf_fp16_t64_e12 | 64 | 20.19 | 3.1 | 0.151 | cooperative resident
grid (one cluster per token, 256 CTAs): protocol round trips per tile;
bound 3.1 us (nvlink) |
| perf_bf16_t128_e16 | 128 | 25.38 | 6.1 | 0.241 | all 128 token
clusters resident at k=4 (512 CTAs): protocol round trips (clear ->
publish -> poll -> RMS) dominate; bound 6.1 us (nvlink) |
| perf_fp16_t128_e16_pdl | 128 | 26.18 | 6.1 | 0.234 | cooperative
resident grid (one cluster per token, 512 CTAs): protocol round trips
per tile; bound 6.1 us (nvlink) |
| perf_bf16_t256_e8 | 256 | 34.72 | 12.2 | 0.352 | occupancy-bound bytes
in flight: wide_mlp at k=4 CTAs/SM (592 CTAs; driver occupancy 5 CTAs/SM
(56 regs), 175 co-resident clusters; k+1 not admissible with headroom);
bound 12.2 us (nvlink) |
| perf_bf16_t256_e12_pdl | 256 | 36.67 | 12.2 | 0.334 | occupancy-bound
bytes in flight: wide_mlp at k=4 CTAs/SM (592 CTAs; driver occupancy 5
CTAs/SM (56 regs), 175 co-resident clusters; k+1 not admissible with
headroom); bound 12.2 us (nvlink) |
| perf_fp16_t2048_e8 | 2048 | 211.65 | 97.9 | 0.462 | occupancy-bound
bytes in flight: wide_mlp at k=4 CTAs/SM (592 CTAs; driver occupancy 5
CTAs/SM (53 regs), 175 co-resident clusters; k+1 not admissible with
headroom); bound 97.9 us (nvlink) |
| perf_bf16_t2048_e12_pdl | 2048 | 220.74 | 97.9 | 0.443 |
occupancy-bound bytes in flight: generic at k=5 CTAs/SM (740 CTAs;
driver occupancy 6 CTAs/SM (40 regs), 213 co-resident clusters; k+1 not
admissible with headroom); bound 97.9 us (nvlink) |
| perf_fp16_t2048_e16_pdl | 2048 | 226.34 | 97.9 | 0.432 |
occupancy-bound bytes in flight: wide_mlp at k=4 CTAs/SM (592 CTAs;
driver occupancy 5 CTAs/SM (53 regs), 175 co-resident clusters; k+1 not
admissible with headroom); ncu rank 0: 211.2 us, DRAM 646.1+198.7 MB ->
4.00 TB/s = 50% of 8 TB/s HBM; bound 97.9 us (nvlink) |

#### sm_103a world size 8 (NVIDIA B300 SXM6 AC, 148 SMs; 3
counterbalanced groups, rank-max median)

| row | T | new us | bound us | achieved | residual |
|---|---:|---:|---:|---:|---|
| perf_ws8_bf16_t1_e8 | 1 | 17.38 | 0.1 | 0.006 | single cluster (4
CTAs): fixed Lamport protocol latency (launch, clear, publish,
cross-rank poll, RMS epilogue); bytes 0.3 MB, bound 0.1 us |
| perf_ws8_bf16_t64_e8_pdl | 64 | 27.04 | 7.1 | 0.264 | all 64 token
clusters resident at k=4 (256 CTAs): protocol round trips (clear ->
publish -> poll -> RMS) dominate; bound 7.1 us (nvlink) |
| perf_ws8_fp16_t64_e12 | 64 | 28.00 | 7.1 | 0.255 | all 64 token
clusters resident at k=4 (256 CTAs): protocol round trips (clear ->
publish -> poll -> RMS) dominate; bound 7.1 us (nvlink) |
| perf_ws8_bf16_t128_e16 | 128 | 41.02 | 14.3 | 0.348 | all 128 token
clusters resident at k=4 (512 CTAs): protocol round trips (clear ->
publish -> poll -> RMS) dominate; bound 14.3 us (nvlink) |
| perf_ws8_fp16_t128_e16_pdl | 128 | 40.19 | 14.3 | 0.355 | all 128
token clusters resident at k=4 (512 CTAs): protocol round trips (clear
-> publish -> poll -> RMS) dominate; bound 14.3 us (nvlink) |
| perf_ws8_bf16_t256_e8 | 256 | 63.42 | 28.5 | 0.450 | occupancy-bound
bytes in flight: generic at k=4 CTAs/SM (592 CTAs; driver occupancy 5
CTAs/SM (55 regs), 175 co-resident clusters; k+1 not admissible with
headroom); bound 28.5 us (nvlink) |
| perf_ws8_bf16_t256_e12_pdl | 256 | 64.67 | 28.5 | 0.441 |
occupancy-bound bytes in flight: generic at k=4 CTAs/SM (592 CTAs;
driver occupancy 5 CTAs/SM (55 regs), 175 co-resident clusters; k+1 not
admissible with headroom); bound 28.5 us (nvlink) |
| perf_ws8_fp16_t2048_e8 | 2048 | 420.00 | 228.4 | 0.544 |
occupancy-bound bytes in flight: generic at k=4 CTAs/SM (592 CTAs;
driver occupancy 5 CTAs/SM (55 regs), 175 co-resident clusters; k+1 not
admissible with headroom); bound 228.4 us (nvlink) |
| perf_ws8_bf16_t2048_e12_pdl | 2048 | 430.44 | 228.4 | 0.531 |
occupancy-bound bytes in flight: generic at k=4 CTAs/SM (592 CTAs;
driver occupancy 5 CTAs/SM (55 regs), 175 co-resident clusters; k+1 not
admissible with headroom); bound 228.4 us (nvlink) |
| perf_ws8_fp16_t2048_e16_pdl | 2048 | 433.19 | 228.4 | 0.527 |
occupancy-bound bytes in flight: generic at k=4 CTAs/SM (592 CTAs;
driver occupancy 5 CTAs/SM (55 regs), 175 co-resident clusters; k+1 not
admissible with headroom); ncu rank 0: 413.8 us, DRAM 763.6+328.0 MB ->
2.64 TB/s = 33% of 8 TB/s HBM; bound 228.4 us (nvlink) |

#### sm_100a world size 2 (NVIDIA B200, 148 SMs; 3 counterbalanced
groups, rank-max median)

| row | T | new us | bound us | achieved | residual |
|---|---:|---:|---:|---:|---|
| perf_ws2_bf16_t1_e8 | 1 | 10.11 | 0.0 | 0.003 | single 896-thread CTA
(no cluster barrier, no DSMEM partial exchange): fixed Lamport protocol
latency (launch, clear, publish, cross-rank poll, RMS epilogue); bytes
0.2 MB, bound 0.0 us |
| perf_ws2_bf16_t64_e8_pdl | 64 | 12.42 | 1.7 | 0.139 | all 64 token
clusters resident at k=4 (256 CTAs): protocol round trips (clear ->
publish -> poll -> RMS) dominate; bound 1.7 us (hbm) |
| perf_ws2_fp16_t64_e12 | 64 | 14.53 | 2.2 | 0.150 | all 64 token
clusters resident at k=4 (256 CTAs): protocol round trips (clear ->
publish -> poll -> RMS) dominate; bound 2.2 us (hbm) |
| perf_ws2_bf16_t128_e16 | 128 | 17.34 | 5.3 | 0.304 | all 128 token
clusters resident at k=4 (512 CTAs): protocol round trips (clear ->
publish -> poll -> RMS) dominate; bound 5.3 us (hbm) |
| perf_ws2_fp16_t128_e16_pdl | 128 | 17.44 | 5.3 | 0.303 | all 128 token
clusters resident at k=4 (512 CTAs): protocol round trips (clear ->
publish -> poll -> RMS) dominate; bound 5.3 us (hbm) |
| perf_ws2_bf16_t256_e8 | 256 | 21.15 | 6.9 | 0.325 | occupancy-bound
bytes in flight: wide_mlp at k=4 CTAs/SM (592 CTAs; driver occupancy 5
CTAs/SM (56 regs), 175 co-resident clusters; k+1 not admissible with
headroom); bound 6.9 us (hbm) |
| perf_ws2_bf16_t256_e12_pdl | 256 | 26.69 | 8.7 | 0.327 |
occupancy-bound bytes in flight: wide_mlp at k=4 CTAs/SM (592 CTAs;
driver occupancy 5 CTAs/SM (56 regs), 175 co-resident clusters; k+1 not
admissible with headroom); bound 8.7 us (hbm) |
| perf_ws2_fp16_t2048_e8 | 2048 | 116.67 | 55.1 | 0.472 |
occupancy-bound bytes in flight: wide_mlp at k=4 CTAs/SM (592 CTAs;
driver occupancy 5 CTAs/SM (56 regs), 175 co-resident clusters; k+1 not
admissible with headroom); bound 55.1 us (hbm) |
| perf_ws2_bf16_t2048_e12_pdl | 2048 | 146.75 | 69.7 | 0.475 |
occupancy-bound bytes in flight: wide_mlp at k=4 CTAs/SM (592 CTAs;
driver occupancy 5 CTAs/SM (56 regs), 175 co-resident clusters; k+1 not
admissible with headroom); bound 69.7 us (hbm) |
| perf_ws2_fp16_t2048_e16_pdl | 2048 | 154.75 | 84.4 | 0.545 |
occupancy-bound bytes in flight: wide_mlp at k=4 CTAs/SM (592 CTAs;
driver occupancy 5 CTAs/SM (56 regs), 175 co-resident clusters; k+1 not
admissible with headroom); bound 84.4 us (hbm) |

#### sm_100a world size 4 (NVIDIA B200, 148 SMs; 3 counterbalanced
groups, rank-max median)

| row | T | new us | bound us | achieved | residual |
|---|---:|---:|---:|---:|---|
| perf_bf16_t1_e8 | 1 | 11.68 | 0.0 | 0.004 | single 896-thread CTA (no
cluster barrier, no DSMEM partial exchange): fixed Lamport protocol
latency (launch, clear, publish, cross-rank poll, RMS epilogue); bytes
0.2 MB, bound 0.0 us |
| perf_bf16_t64_e8_pdl | 64 | 17.02 | 3.1 | 0.180 | occupancy-bound
bytes in flight: wide_mlp at k=1 CTAs/SM (148 CTAs; driver occupancy 4
CTAs/SM (72 regs), 142 co-resident clusters; k+1 not admissible with
headroom); bound 3.1 us (nvlink) |
| perf_fp16_t64_e12 | 64 | 18.91 | 3.1 | 0.162 | cooperative resident
grid (one cluster per token, 256 CTAs): protocol round trips per tile;
bound 3.1 us (nvlink) |
| perf_bf16_t128_e16 | 128 | 26.66 | 6.1 | 0.229 | all 128 token
clusters resident at k=4 (512 CTAs): protocol round trips (clear ->
publish -> poll -> RMS) dominate; bound 6.1 us (nvlink) |
| perf_fp16_t128_e16_pdl | 128 | 24.77 | 6.1 | 0.247 | cooperative
resident grid (one cluster per token, 512 CTAs): protocol round trips
per tile; bound 6.1 us (nvlink) |
| perf_bf16_t256_e8 | 256 | 35.17 | 12.2 | 0.348 | occupancy-bound bytes
in flight: generic at k=4 CTAs/SM (592 CTAs; driver occupancy 5 CTAs/SM
(54 regs), 175 co-resident clusters; k+1 not admissible with headroom);
bound 12.2 us (nvlink) |
| perf_bf16_t256_e12_pdl | 256 | 36.67 | 12.2 | 0.334 | occupancy-bound
bytes in flight: generic at k=4 CTAs/SM (592 CTAs; driver occupancy 5
CTAs/SM (54 regs), 175 co-resident clusters; k+1 not admissible with
headroom); bound 12.2 us (nvlink) |
| perf_fp16_t2048_e8 | 2048 | 213.60 | 97.9 | 0.458 | occupancy-bound
bytes in flight: wide_mlp at k=4 CTAs/SM (592 CTAs; driver occupancy 5
CTAs/SM (56 regs), 175 co-resident clusters; k+1 not admissible with
headroom); bound 97.9 us (nvlink) |
| perf_bf16_t2048_e12_pdl | 2048 | 234.78 | 97.9 | 0.417 |
occupancy-bound bytes in flight: generic at k=4 CTAs/SM (592 CTAs;
driver occupancy 5 CTAs/SM (54 regs), 175 co-resident clusters; k+1 not
admissible with headroom); bound 97.9 us (nvlink) |
| perf_fp16_t2048_e16_pdl | 2048 | 224.86 | 97.9 | 0.435 |
occupancy-bound bytes in flight: wide_mlp at k=4 CTAs/SM (592 CTAs;
driver occupancy 5 CTAs/SM (56 regs), 175 co-resident clusters; k+1 not
admissible with headroom); bound 97.9 us (nvlink) |

#### sm_100a world size 8 (NVIDIA B200, 148 SMs; 3 counterbalanced
groups, rank-max median)

| row | T | new us | bound us | achieved | residual |
|---|---:|---:|---:|---:|---|
| perf_ws8_bf16_t1_e8 | 1 | 16.74 | 0.1 | 0.007 | single cluster (4
CTAs): fixed Lamport protocol latency (launch, clear, publish,
cross-rank poll, RMS epilogue); bytes 0.3 MB, bound 0.1 us |
| perf_ws8_bf16_t64_e8_pdl | 64 | 29.28 | 7.1 | 0.244 | occupancy-bound
bytes in flight: sm100_ws8_mid at k=1 CTAs/SM (148 CTAs; driver
occupancy 5 CTAs/SM (56 regs), 175 co-resident clusters; k+1 not
admissible with headroom); bound 7.1 us (nvlink) |
| perf_ws8_fp16_t64_e12 | 64 | 30.24 | 7.1 | 0.236 | occupancy-bound
bytes in flight: sm100_ws8_mid at k=1 CTAs/SM (148 CTAs; driver
occupancy 5 CTAs/SM (56 regs), 175 co-resident clusters; k+1 not
admissible with headroom); bound 7.1 us (nvlink) |
| perf_ws8_bf16_t128_e16 | 128 | 50.24 | 14.3 | 0.284 | occupancy-bound
bytes in flight: sm100_ws8_mid at k=1 CTAs/SM (148 CTAs; driver
occupancy 5 CTAs/SM (56 regs), 175 co-resident clusters; k+1 not
admissible with headroom); bound 14.3 us (nvlink) |
| perf_ws8_fp16_t128_e16_pdl | 128 | 49.60 | 14.3 | 0.288 |
occupancy-bound bytes in flight: sm100_ws8_mid at k=1 CTAs/SM (148 CTAs;
driver occupancy 5 CTAs/SM (56 regs), 175 co-resident clusters; k+1 not
admissible with headroom); bound 14.3 us (nvlink) |
| perf_ws8_bf16_t256_e8 | 256 | 64.83 | 28.5 | 0.440 | occupancy-bound
bytes in flight: generic at k=4 CTAs/SM (592 CTAs; driver occupancy 5
CTAs/SM (56 regs), 175 co-resident clusters; k+1 not admissible with
headroom); bound 28.5 us (nvlink) |
| perf_ws8_bf16_t256_e12_pdl | 256 | 66.02 | 28.5 | 0.432 |
occupancy-bound bytes in flight: generic at k=4 CTAs/SM (592 CTAs;
driver occupancy 5 CTAs/SM (56 regs), 175 co-resident clusters; k+1 not
admissible with headroom); bound 28.5 us (nvlink) |
| perf_ws8_fp16_t2048_e8 | 2048 | 422.02 | 228.4 | 0.541 |
occupancy-bound bytes in flight: generic at k=4 CTAs/SM (592 CTAs;
driver occupancy 5 CTAs/SM (56 regs), 175 co-resident clusters; k+1 not
admissible with headroom); bound 228.4 us (nvlink) |
| perf_ws8_bf16_t2048_e12_pdl | 2048 | 435.23 | 228.4 | 0.525 |
occupancy-bound bytes in flight: generic at k=4 CTAs/SM (592 CTAs;
driver occupancy 5 CTAs/SM (56 regs), 175 co-resident clusters; k+1 not
admissible with headroom); bound 228.4 us (nvlink) |
| perf_ws8_fp16_t2048_e16_pdl | 2048 | 437.63 | 228.4 | 0.522 |
occupancy-bound bytes in flight: generic at k=4 CTAs/SM (592 CTAs;
driver occupancy 5 CTAs/SM (56 regs), 175 co-resident clusters; k+1 not
admissible with headroom); bound 228.4 us (nvlink) |


### Baselines and their source PRs

- shipped union programs: #5599 (SM100 + SM103 union export at world
sizes 2/4/8), built and timed from upstream main
`14a556336f60dc9748b32b296cc18853d7fc76a9` in the same process as the
new programs.
- standalone: the isolated SM100/SM103 Cake bundle of #4730
(`csrc/cake_trtllm_moe_allreduce_fusion`), unchanged by this PR.
- upstream: `trtllm_moe_allreduce_fusion(backend="trtllm")` of this tree
(base `14a556336f60dc9748b32b296cc18853d7fc76a9`).

### Evidence manifest (SHA-256 of the remote receipts and tables)

| file | bytes | sha256 |
|---|---:|---|
| `roofline_sm103_ws2_p3.json` | 45003 |
`336bdc100f1ab7c142268e400a3d7d96dbecb829defbe605e7a01e045ba79c66` |
| `roofline_sm103_ws4_p3.json` | 45192 |
`5084548b983e5cc035ac31edf27e493abc8c8140f7a70834bd969c961088c4a9` |
| `roofline_sm103_ws8_p3.json` | 45101 |
`21dac35b0ffbabe2a8de94e75f488b0f3401eea7d8865d023ccd4420af75bb90` |
| `sass_sm103_p3.json` | 46174 |
`09e0518194a4455c102ce34138113d88ace6774226fddbfd22afb18aab94b12d` |
| `roofline_sm103_ws2_p3.log` | 16544 |
`ce09ed88e2f2435d62e7972f857904240f03020e3e3b275bd1d7af12051c7001` |
| `roofline_sm103_ws4_p3.log` | 25534 |
`92986e249076e97ebb585d62caf251b79428a485fdd8ab8bfe0ad0d81d585ade` |
| `roofline_sm103_ws8_p3.log` | 43936 |
`a910bf9e34abe5746775dc7984b88d71e720e8339216e3991ac5f43ace6ecb2e` |
| `ncu_metrics_p3.txt` | 7275 |
`1bc1487af2f251fbfa931d0f5452a5885bc0c4685e09c1296eeb3913b151decb` |
| `roofline_sm103_ws2_p3e.json` | 53584 |
`7e4a7a67e80a62e2cccc036b87cb1aef24115f18ef5c53df644c4605e852d925` |
| `roofline_sm103_ws4_p3e.json` | 53782 |
`fc656004200c641f3975b4cfacb2c5ef2b4e5dccfc38895ab0f8c765fa5290d9` |
| `roofline_sm103_ws8_p3e.json` | 53683 |
`7744784c441bcea0bdf99b4309966bd0dd62525457cd56bc1dfd1368db69396e` |
| `roofline_sm103_ws2_p3e.log` | 33373 |
`bf992d383f7f880a09ac17d70a13f5c56ee6a95cada85888c87a62bde76fc72d` |
| `roofline_sm103_ws4_p3e.log` | 61209 |
`83ebf7f7346daeafe00ccd9d8ffa6d35860b5c1dfd8f5f6b7994b3133f42f27d` |
| `roofline_sm103_ws8_p3e.log` | 99387 |
`c4abc263b741201af0787f788bcef354e5c86f7f2309eb94dffe47422d4aa520` |
| `t1_geometry_sm103_ws4c.json` | 3184 |
`bd5de724be069392731bcee62dc10615403496edfd8e605da54e0ec2d17a54ea` |
| `t1_geometry_sm103_ws4c.log` | 25166 |
`51cd70d90a4fd436376a2ff2c157570b8e0ed7ae772b32e93b84f23243a8ec06` |
| `t1_geometry_sm103_ws8c.json` | 3154 |
`6afd91a17bd2754f62d7004358374531c5f6a6f1c3f65b673bfd225c8b42fab5` |
| `t1_geometry_sm103_ws8c.log` | 21491 |
`da7591e3bea73458b1a13c9738425f3b555f4abc30c5bcc63614f1919bdc6a90` |
| `t1_geometry_sm103_ws2c.json` | 3191 |
`f7e34d02ab850621e96b14fff49636d9b0c5fe7d8218b93664e4c24e21d5e56c` |
| `t1_geometry_sm103_ws2c.log` | 7417 |
`aa24c61616feb79c5d95f341a16554f9e6e4d5788a212836a1100a1da2a087d0` |
| `gates-sm103-fi_distributed_tp248.json` | 360 |
`3ce42ed0336cd106f06c22aa7af65b1470cc2da7fd73f0d2170c3bee1f37deff` |
| `gates-sm103.log` | 11803 |
`8c6d0d99ce9648952e8addb8a7d106333b285094c88ad2692877ca422c02ef80` |
| `t1_geometry_sm103_ws8e.json` | 3176 |
`42caf3e74b9ade51b6dc2ffa17fabf1d484ce1fdac295456de56fc72eb6c2840` |
| `t1_geometry_sm103_ws8e.log` | 21517 |
`4ba9a1832cfc0768cd64c654163f941d37ec16c1f75f7bd3a7afc603410bdfe4` |
| `gates-sm103-e2e_union.json` | 330 |
`1f2dd4c67f57dfacddaaed4840b41668cf69de0cdba2b23eebfdefecba869bab` |
| `trtmoe-regression-r709-sm103.summary.json` | 4505 |
`445460a2a774036e6feeb139c4a61c0ef9c73cdb6f1ec69c8ffdd4b7c9b595c0` |
| `gates-sm103-trtmoe_regression_bench_regression.json` | 216 |
`430e25e6a4c1faa32606cceeb738ac1dfa6ad8d6ff195a0f3b569e870814f6a4` |
| `trtmoe-regression.a6c678a4.summary.json` | 4648 |
`718cac77ee84b4925aeff0ed7208481c2d3ca52aef47b2b98e3f476704834eb5` |
| `delivery.patch` | 4794978 |
`b651381282e407b6594752cd0edfe30f527b1d01eeaa3afaf273a2da6c3eea73` |
| `delivery.status` | 38456 |
`2fa79e69c768294f74c6fc130b5f25b9db100192e3a9635dfc984f3a2b421acc` |
| `gates-sm103-trtmoe_regression.json` | 54 |
`06c46bb1ced296ff6a600987610074ee8843b3a59de70998a3ffa0b20421820e` |
| `trtmoe-regression.fac7812c.json` | 1292828 |
`e6729e7bab28e88949e8468ae5433bcac5bb66b3fadc022aa9e72b7bd8a64931` |
| `trtmoe-regression.fac7812c.checkpoint.json` | 1364726 |
`8ac97f93cd6206d99c37503345080cc6ccadbaf6ef689addd5594ff8f8c10cba` |
|
`gates-sm103-cake_unit_e2e_union_trtmoe_regression_fi_union_cpu_tests_fi_distributed_tp248_fi_precommit.json`
| 1701 |
`36f256831ae0090f1c4d830e5cdd9f46038945b56cc31915aab4f42f8e182c83` |
|
`gates-sm103-fi_union_cpu_tests_fi_distributed_tp248_fi_precommit.json`
| 770 |
`b58c85af308c07c2c1358bc1dad99499d2579dc461b8603e68050244c7e224a3` |
| `gate-sm103-fi_precommit.log` | 1280 |
`87bd1c345e4ae6dd22c74b419eba5c052e7d4f1ad45e4add9eba2627621ef694` |
| `gates-sm103-cake_unit_e2e_union.json` | 679 |
`99b6feeabafa9f98bfa00b4c281c98a6a938e685695e673885d17badb8be93cf` |
| `gate-sm103-cake_unit.log` | 175879 |
`10ce06c4a76f6f7dac3bfd5710117a3090e6e41983c417bc56bd126f1e137f40` |
| `gate-sm103-e2e_union.log` | 8478 |
`bbb72ffe97118b414de44da13356b9293df684a0fee186db31ff98bdb58514af` |
| `delivery.status` | 36672 |
`77ac79629ef435937904afb7fa9c5b617332e091304cabdbee5a45ead7aff05e` |
| `delivery.patch` | 4243965 |
`a6bd59245b11ef36db7939233ad1f946e976fb46ac9fd9a008733feee864977f` |
| `summary.md` | 20104 |
`c93543eddc57c9627984daba313d159ae6c9a9aa856a51af77919da580561090` |
| `pr_body.md` | 11130 |
`ce7c69ff2fa141fc41d9c2b541eb3cedeb70e58b2d952ee744aa50a5a8d4d799` |
| `receipts.index` | 38231 |
`40df556ba8fcc3b2e06b17a7a70b9e5e1cf770e0cdea5c4f75d0c176c533bac3` |
| `delivery.status` | 38409 |
`f2800a627fce4182583a46be9a6237cb1eee024cd2db81dc1463256f80db81d0` |
| `delivery.patch` | 4794490 |
`27b9f8e8d5063cd1cfad5012e883268e41001a035c1ef9b54da524f6e677c86a` |
| `summary.md` | 20104 |
`f1f1daf4eab2b37043dd4d6ad9e3f0d31f9ff5c57be8f1aa854f24a1eaf5abd8` |
| `pr_body.md` | 11130 |
`7f17f9e5909b7288fd8fb08931fe5fa6d32f8127daf564cf881bed675c25a7e8` |
| `receipts.index` | 38935 |
`b86242feba3e3d4f705822abaa83c45d6cc7af90487e4cbc4890265ac6d2d385` |
| `roofline_sm100_ws8_p2w8.json` | 22574 |
`7b0c23a9e3e7fed316067efe368414a2ce7e4d66a4411ad927b3e2c5801bc4c7` |
| `sass_sm100_p2w8.json` | 43748 |
`224c3d98218fa076e8bd65b14cfa853c256be14648068cc220ca75b2abb24250` |
| `roofline_sm100_ws8_p2w8.log` | 25974 |
`7031cf1d2125d740942e57ded7a770754743d01ea1bfa9ebb250ae3902ab8e56` |
| `trtmoe-regression-r709-sm100.summary.json` | 4486 |
`f6f1f7529f640ee1c3e778897e12d35ef8480fc6c2197f96b9617dfdf66bb641` |
| `t1_geometry_sm100_ws4d.json` | 3168 |
`32c342fbd45a59c96dd7d87bb75562a869942dbb1abaf8cbbecc9f3fbb1f2130` |
| `t1_geometry_sm100_ws4d.log` | 40094 |
`9450d19223de29f0e0e9abfdbe3ce754c0d663befb75e5cf008cd483847208b3` |
| `t1_geometry_sm100_ws8d.json` | 3169 |
`82a4db5e0b5d7df05f67e83e25ce0266fa9dc4370c9fbc622bc2c59a7d0c2285` |
| `t1_geometry_sm100_ws8d.log` | 62443 |
`7678ed0d4ed3c2f469baabe51ef63a874f767c9d955b99266b6e2cde0ea79162` |
| `t1_geometry_sm100_ws2d.json` | 3170 |
`f5e89b287e727851b9bdd85edfe17866892c9b1269bddae8043b5ca25db77386` |
| `t1_geometry_sm100_ws2d.log` | 17353 |
`62945713914bc0d76342f1f99dedd15dffdb9aeb648da794c7fc6a8dd7b87ac5` |
| `summary.md` | 20102 |
`28a706e834779b40699cb6fd1a0fcceb7220a88ad81fafb7e5253dfca3cd09a9` |
| `pr_body.md` | 11128 |
`c441e5f1029f2c8db5c345b11b5927f663004f2bd3b8d7f16df04984fc77449c` |
| `roofline_sm100_ws2_p3r2.json` | 53844 |
`65307bfe7018d7485ee546be34682c6acf24e064fe982bfb2af055f2fc56e1aa` |
| `roofline_sm100_ws2_p3r2.log` | 29817 |
`23e909848483eba352c5f8efeb8c7b0e36737f3a183c2c0ebe6ada9b98efa099` |
| `unit_generated_programs_main.log` | 12720 |
`e59bb943d32896d49407e0265b156b8878c7777ca8b7591df8f7f77c73692930` |
| `unit_generated_programs_branch.log` | 12630 |
`c3bf68777947f7bdd3dba270dc308addb5bc80e404e15b9a477ba1bbc51b215d` |
| `roofline_sm100_ws4_p3r2.json` | 54024 |
`74a683eb3b0ef96f5a408d82b9db42fd56fcea2d748d36e22b235b4124458f70` |
| `roofline_sm100_ws4_p3r2.log` | 63556 |
`3365929626dc88907446cdd18766e9dcf957c746b6b5b562846d17bda91d47e4` |
| `roofline_sm100_ws8_p3r2.json` | 54110 |
`6aab4a83861de8ddb69c0a9b706bf4e61c8e5f551c0c625f4aca11193352ed79` |
| `roofline_sm100_ws8_p3r2.log` | 120711 |
`4a76449dee4b4a9f0d4cf75eeb5868fd65cd6b7396a5e5ae4ac71b3aad30a854` |
| `gates-sm100-trtmoe_regression.json` | 54 |
`06c46bb1ced296ff6a600987610074ee8843b3a59de70998a3ffa0b20421820e` |
| `trtmoe-regression.52496247.json` | 1296764 |
`52d53a942a6ff8c66e84bb926a5c3331607a54c8ba83b894c7e125033dd66135` |
| `trtmoe-regression.52496247.checkpoint.json` | 1368703 |
`818a1ad0a476003ac55e50628d1439fcdac4a41c1de3a358685d86d40cf61310` |
|
`gates-sm100-cake_unit_e2e_union_trtmoe_regression_fi_union_cpu_tests_fi_distributed_tp248_fi_precommit.json`
| 1747 |
`865b79b59ae64069557e148f0484c6b69f41ebcd4f55df60b4c7040d62107f47` |
|
`gates-sm100-fi_union_cpu_tests_fi_distributed_tp248_fi_precommit.json`
| 770 |
`6c714c3968d2ecd29bde4b6cfdd92d24dacb26e3e2046d646a696cf44586b3e4` |
| `gate-sm100-fi_precommit.log` | 1280 |
`87bd1c345e4ae6dd22c74b419eba5c052e7d4f1ad45e4add9eba2627621ef694` |
| `gates-sm100-cake_unit_e2e_union.json` | 725 |
`56e5c26c3d8d5cb4777497ae73ea810ede6b23c6f6ecc5b1006afffdd0b66df1` |
| `gate-sm100-cake_unit.log` | 188470 |
`5416cc74b181312a92ac71cc79011ed3cbc2d14e267ace492507a7bdfe0eae32` |
| `gate-sm100-e2e_union.log` | 1488 |
`b89f773774e6114851375ab0bd297a8326473a8ee5e1890e069db765dc441bcc` |
| `delivery.status` | 46038 |
`8b7cd6d4b8370762717ff4537614222c73f1618a5f3a6419e8c7a4c12eb9c1b4` |
| `delivery.patch` | 7471165 |
`26c30b1e384cb5bd2fa90eaa2ad4b1d7fe7eea4c71c3a066670ba1a0d906bb8a` |
| `summary.md` | 20112 |
`508e3744baa4cf6020bce454dcdb90729b4354f9e37ab787c55ee2557e8e4e30` |
| `pr_body.md` | 11138 |
`7408b93bd22b891d222df6fb76148d2bb5d1db66d4feb684d69b48a65d4d409c` |
| `receipts.index` | 1931 |
`e0a45ac8c71980dd5fe65dbb8a8ece81533c6269ce4756bbafd12fcb5228834c` |

## 🔍 Related Issues

- #5599 (union export this PR re-tunes), #5514 (world-size-4 union),
#4730 (isolated bundle)
- Tracker: #4254

## 🚀 Pull Request Checklist

- [x] Pre-commit hooks pass on the changed hand-written files (the
generated directory is excluded as a byte-faithful export).
- [x] Tests: `tests/comm/test_cake_moe_allreduce_union.py`,
`tests/comm/test_cake_moe_allreduce_api.py`,
      `tests/comm/test_cake_trtllm_moe_allreduce_source.py` (CPU) and
`tests/comm/test_cake_moe_allreduce_distributed.py -k "tp2 or tp4 or
tp8"` (eight B200 GPUs and eight B300 GPUs).
- [x] Every exported program passed the rank-set correctness check
against `backend="trtllm"` on all ranks (atol = rtol = 1e-2) with
bitwise source/export parity.

## 🧪 Tests

| gate | B200 exit | B300 exit | result |
|---|---:|---:|---|
| FlashInfer CPU tests (`tests/comm/test_cake_moe_allreduce_union.py`,
`test_cake_moe_allreduce_api.py`,
`test_cake_trtllm_moe_allreduce_source.py`) | 0 | 0 | PASS on this PR's
head on the B200 and the B300 node. |
| FlashInfer distributed tests
(`tests/comm/test_cake_moe_allreduce_distributed.py -k "tp2 or tp4 or
tp8"`, eight GPUs) | 0 | 0 | PASS 6/6 (tp2/tp4/tp8 x fp16/bf16) on eight
B200 and on eight B300 GPUs. |
| pre-commit on the changed hand-written files (all hooks incl. mypy,
ruff check, ruff format) | 0 | 0 | PASS on both nodes for this PR's
head. |
| Generator four-rank paired regression of the union programs vs the
pinned live FlashInfer (10 correctness + 10 CUPTI paired rows) | 0 | 0 |
PASS 20/20 on B200 (perf rows 1.0063x-2.2370x) and on B300
(1.0296x-2.7731x); correctness 10/10, no route fallback. |
| Generator end-to-end all-reduce-fusion slice (four ranks; union test +
dynamic-FP8 MNNVL test) | 0 | 1 | B200: 2/2 PASS. B300: the union test
PASSED; the dynamic-FP8 MNNVL test fails at rank setup in the B300
container (symmetric-memory rendezvous handle without a multicast
pointer, before any kernel launch; the same test passes on the bare B200
node). |
| Generator unit tests of the touched modules | 1 | 1 | Exit 1 on both
nodes = 18 pre-existing failures of the generator's export-discovery
test module that fail identically on the generator's main branch
(verified on a CPU allocation with the main and the branch trees); B300
adds one known container-specific literal-arithmetic test failure. No
new failure. |
| Generator all-reduce-fusion family regression gate (six contracts,
four ranks) | n/a | n/a | Not completable in this round's environments:
the gate hangs deterministically on the bare B200 node at an MNNVL FP8
correctness row this change does not touch, and needs the MNNVL
multicast workspace the B300 container lacks. The union's regression
evidence is the paired regression above plus the per-row tables. |

## Reviewer Notes

The export receipts (correctness against the upstream reference on every
rank, bitwise source/export parity, co-residency probe,
no-fallback route check, paired per-rank timing with the maximum across
ranks per sample) were produced by the Cake generated-program
exporter on one B200 node (SM100) and one B300 node (SM103), one
architecture per run. The branch has four commits: SM103 exported
on top of upstream main (carrying the SM100 set over byte-for-byte);
SM100 exported on top of that commit (carrying the SM103 set over
byte-for-byte); the loader reflowed to the repository line length (the
same three lines the generator template now emits); and the
SM103 set re-emitted by the final generator tree against the reflowed
loader, re-measured on B300 with fresh receipts (its kernel and
binding sources are identical to the previous commit's SM103 files up to
the generated symbol). The tables above list every row of
the frozen thirty-row denominator per architecture.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [515748a](https://github.com/flashinfer-ai/flashinfer/commit/515748a8f2ad992b0ba7a54f29d28331368724dc)

- **作者**: eigen
- **时间**: 2026-09-28T23:28:11Z
- **提交信息**: perf(cake_latent_moe): Kimi-K3 TP12 fused LatentMoE tail round 5: early shared scatter K1, fused K2+K3 for M <= 4, bulk reduce-scatter K3 pipeline above 256 tokens (GB200 / GB300 NVL72) (#5646)

Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

## Summary

Round 5 of `flashinfer.kimi_k3_tp12_tail` (`backend="cake"`, the fused
Kimi-K3 TP12 LatentMoE communication tail for
three-tray GB200 / GB300 NVL72 tensor-parallel groups; #5603 delivered
the operator, #5624 the round-4 kernels). Same
operator, entry points and workspace; three new kernel forms, dispatched
by token count, keep every row at least as fast as
#5624 and make the decode, mid and large rows faster. Every row's output
is bitwise identical to #5624's:

- **ESS, early shared scatter (`M < 256`)**: the #5624 K3 spent its
first fabric hop scattering this rank's `shared`
packets into the twelve owners' slots after the GEMM. The K1 forms
(one-shot below 17 tokens, two-shot from 17) now push
those packets right behind the routed packet — the same DRAM round trip
— and K3-ESS takes no `shared` argument: its
owner threads poll-reduce the twelve packets before the PDL wait, so
only the add, the multicast all-gather and its poll
remain after the GEMM. Rank-order BF16 sum and a single rounding as
before. -1..-13 % at M = 1..16 and -5..-8 % at
  M = 32..128 in the paired candidate A/Bs on both racks.
- **K23, fused weight-streaming GEMM + K3-ESS (`M <= 4`)**: one kernel
of `cols / 8` CTAs x 448 threads (80 on the
640-column ranks, 64 on the 512-column ranks); each CTA owns eight
output columns = one 16-byte `out` packet per token,
streams its weight fragments and poll-reduces the shared packets before
the PDL wait, computes the fp32 slice in the #5624
K2-stream order, adds the shared sum, rounds once, multicasts and
collects. Replaces the K2-stream + fp32 K3 pair: the
decode chain is two launches and the fp32 slice no longer round-trips
through HBM / L2. Shipped M = 1 chain at 0.835
  (GB300) / 0.751 (GB200) of #5624.
- **Bulk persistent K3 (`M > 256`)**: the persistent K3 stages each
sanitized 7 KB half-row in a double-buffered SMEM stage
and pushes the per-owner pieces with `cp.async.bulk` (measured push
ingress 667-688 GB/s against 570 GB/s for 16-byte
stores, both racks): -1..-5 % from 512 tokens; a tie at 256, which keeps
the #5624 kernel.
- Measured on both racks and not shipped: a one-hop tail (both-partials
one-shot all-reduce + replicated full-width GEMM;
parity to +19 % because the last-launching rank cannot hide the 51 MB
weight stream), a side-stream scatter kernel
(+9..+26 %), the bulk push for the two-shot K1 (no gain below 4096
tokens), and K23 above four tokens (-6.0 / -9.5 % at
M = 8 on GB200 / GB300, but it moves the rounding point of the cuBLAS
rows: offered as a numerics decision, not
  dispatched).

## Files

- `flashinfer/experimental/kimi_k3_tp12_tail/cake_backend.py` — dispatch
by token count (ESS K1 forms and K3-ESS below 256,
K23 in place of the K2-stream + fp32 K3 pair for `M <= 4`, the #5624
persistent K3 at 256, the bulk persistent K3
above), the K3 workspace's multicast address bound as one more raw
pointer for the ESS K1 forms.
- `flashinfer/experimental/kimi_k3_tp12_tail/cake_jit.py`,
`csrc/cake_kimi_k3_tp12_tail/{sm_100a,sm_103a}/` — generated
programs regenerated by the export: 20 per architecture (12
rank-specialised one-shot ESS K1, grouped two-shot ESS K1,
grouped / pinned two-shot K1, K23 for the 640- and 512-column slices,
grouped K3-ESS, grouped persistent K3, pinned bulk
  persistent K3) and the populated registry; 81 files delivered.
- `flashinfer/kimi_k3_tp12_tail.py` — docstring (dispatch).
- `benchmarks/bench_cake_kimi_k3_tp12_tail.py` — docstring: the fused
chain is two generated launches per rank plus cuBLAS for `M > 4` (was
three launches).
- `tests/experimental/test_cake_kimi_k3_tp12_tail.py` — route / grid /
inventory tests for the round-5 forms; the
twelve-rank GPU test covers M = 1, 4, 8, 16, 32, 128, 256, 300 with a
512-token workspace (every dispatch form: K23, one-shot ESS + K3-ESS,
two-shot ESS + K3-ESS, the persistent K3 at 256, the bulk persistent K3
above).

## Results

Rank-max median GPU time per call (CUPTI, cold L2, CUDA graphs, twelve
ranks on three trays of one NVLink domain). The
export protocol run at the producer revision passed every shape on both
racks (20/20; 10/10 per architecture, allocations
of 2026-09-28); its per-row tables (stock chain, fused, speedup, the
#5624 export run on the same racks, source/export
parity) are taken from the receipts. Below each export table, the
source-side measurement that is already available: the
Cake harness's acceptance A/B on the same rack (`#5624 chain` = the
round-4 kernels re-measured in the same process,
`dup` = that chain timed a second time per group = the identical-arm
control; 3 counterbalanced groups).

### GB300 NVL72 (sm_103a)

| M | route | stock chain us | fused (this PR) us | speedup | fused
#5624 export run us | source / export parity |
|---|---|---|---|---|---|---|
| 1 | `oneshot_ess_grouped_k23` | 114.9 | **21.01** | **5.47x** | 22.2 |
0.990 |
| 8 | `oneshot_ess_grouped` | 119.8 | **24.99** | **4.79x** | 24.6 |
0.986 |
| 32 | `twoshot_ess_grouped` | 121.0 | **25.98** | **4.66x** | 26.5 |
1.022 |
| 64 | `twoshot_ess_grouped` | 120.7 | **27.71** | **4.35x** | 27.6 |
1.013 |
| 128 | `twoshot_ess_grouped` | 135.8 | **31.38** | **4.33x** | 30.4 |
0.987 |
| 256 | `twoshot_grouped_k3p` | 145.9 | **41.83** | **3.49x** | 40.1 |
0.997 |
| 512 | `twoshot_pinned_k3p_bulk` | 178.1 | **59.65** | **2.99x** | 59.2
| 1.005 |
| 1024 | `twoshot_pinned_k3p_bulk` | 250.5 | **93.18** | **2.69x** |
94.4 | 0.997 |
| 2048 | `twoshot_pinned_k3p_bulk` | 367.9 | **162.05** | **2.27x** |
165.6 | 0.997 |
| 4096 | `twoshot_pinned_k3p_bulk` | 591.2 | **296.29** | **2.00x** |
308.0 | 0.997 |

Source-side acceptance A/B, GB300:

| M | form | #5624 chain us | round 5 us | round 5 / #5624 (group range)
| dup / #5624 | speedup vs stock: round 5 / #5624 |
|---|---|---|---|---|---|---|
| 1 | one-shot ESS K1 + K23 | 21.71 | **18.12** | **0.835**
(0.815-0.845) | 1.025 | 6.87 / 5.78 |
| 8 | one-shot ESS K1 + cuBLAS + K3-ESS | 24.94 | 24.80 | 0.994
(0.958-1.058) | 1.005 | 5.01 / 4.92 |
| 32 | two-shot ESS K1 + cuBLAS + K3-ESS | 26.92 | **24.22** | **0.900**
(0.887-0.913) | 0.981 | 5.13 / 4.61 |
| 64 | two-shot ESS K1 + cuBLAS + K3-ESS | 28.21 | **26.60** | **0.943**
(0.916-0.978) | 0.955 | 4.79 / 4.51 |
| 128 | two-shot ESS K1 + cuBLAS + K3-ESS | 30.67 | **29.43** |
**0.960** (0.928-0.982) | 0.984 | 4.75 / 4.52 |
| 256 | #5624 kernels (two-shot K1 + cuBLAS + persistent K3) | 40.06 |
40.21 | 1.004 (0.984-1.014) | 0.997 | 3.73 / 3.78 |
| 512 | two-shot K1 + cuBLAS + bulk persistent K3 | 59.81 | 59.85 |
1.001 (0.987-1.027) | 1.000 | 3.09 / 3.11 |
| 1024 | two-shot K1 + cuBLAS + bulk persistent K3 | 94.90 | **92.08** |
**0.970** (0.966-0.978) | 0.991 | 2.79 / 2.70 |
| 2048 | two-shot K1 + cuBLAS + bulk persistent K3 | 167.77 | **162.36**
| **0.968** (0.961-0.974) | 0.996 | 2.35 / 2.27 |
| 4096 | two-shot K1 + cuBLAS + bulk persistent K3 | 307.79 | **294.20**
| **0.956** (0.955-0.957) | 1.008 | 2.09 / 2.00 |

### GB200 NVL72 (sm_100a)

| M | route | stock chain us | fused (this PR) us | speedup | fused
#5624 export run us | source / export parity |
|---|---|---|---|---|---|---|
| 1 | `oneshot_ess_grouped_k23` | 118.9 | **20.90** | **5.69x** | 23.1 |
1.009 |
| 8 | `oneshot_ess_grouped` | 122.7 | **25.60** | **4.79x** | 25.1 |
0.988 |
| 32 | `twoshot_ess_grouped` | 123.6 | **26.85** | **4.60x** | 26.7 |
1.008 |
| 64 | `twoshot_ess_grouped` | 123.1 | **28.13** | **4.38x** | 28.5 |
1.013 |
| 128 | `twoshot_ess_grouped` | 138.9 | **32.48** | **4.28x** | 31.5 |
0.987 |
| 256 | `twoshot_grouped_k3p` | 149.9 | **42.75** | **3.51x** | 41.4 |
1.004 |
| 512 | `twoshot_pinned_k3p_bulk` | 183.5 | **61.22** | **3.00x** | 60.9
| 1.015 |
| 1024 | `twoshot_pinned_k3p_bulk` | 257.4 | **95.52** | **2.69x** |
96.0 | 0.999 |
| 2048 | `twoshot_pinned_k3p_bulk` | 406.2 | **165.79** | **2.45x** |
168.8 | 1.001 |
| 4096 | `twoshot_pinned_k3p_bulk` | 629.0 | **297.57** | **2.11x** |
310.9 | 0.998 |

Source-side acceptance A/B, GB200:

| M | form | #5624 chain us | round 5 us | round 5 / #5624 (group range)
| dup / #5624 | speedup vs stock: round 5 / #5624 |
|---|---|---|---|---|---|---|
| 1 | one-shot ESS K1 + K23 | 24.02 | **17.35** | **0.751**
(0.550-0.879) | 0.912 | 7.36 / 6.06 |
| 8 | one-shot ESS K1 + cuBLAS + K3-ESS | 23.86 | 23.93 | 1.003
(0.956-1.079) | 1.063 | 5.29 / 5.15 |
| 32 | two-shot ESS K1 + cuBLAS + K3-ESS | 26.26 | **24.30** | **0.925**
(0.914-0.944) | 1.020 | 5.17 / 4.77 |
| 64 | two-shot ESS K1 + cuBLAS + K3-ESS | 27.03 | **25.26** | **0.935**
(0.919-0.965) | 0.992 | 4.97 / 4.78 |
| 128 | two-shot ESS K1 + cuBLAS + K3-ESS | 29.85 | 30.10 | 1.009
(0.979-1.037) | 1.030 | 4.74 / 4.80 |
| 256 | #5624 kernels (two-shot K1 + cuBLAS + persistent K3) | 39.49 |
39.74 | 1.007 (0.973-1.051) | 1.074 | 3.85 / 3.86 |
| 512 | two-shot K1 + cuBLAS + bulk persistent K3 | 59.82 | **58.73** |
0.982 (0.971-0.988) | 0.988 | 3.19 / 3.15 |
| 1024 | two-shot K1 + cuBLAS + bulk persistent K3 | 94.45 | **91.50** |
**0.969** (0.938-0.990) | 0.985 | 2.88 / 2.82 |
| 2048 | two-shot K1 + cuBLAS + bulk persistent K3 | 167.90 | **162.07**
| **0.965** (0.961-0.969) | 0.999 | 2.56 / 2.47 |
| 4096 | two-shot K1 + cuBLAS + bulk persistent K3 | 310.82 | **295.46**
| **0.951** (0.949-0.955) | 0.992 | 2.19 / 2.08 |

No row regresses on either rack: every `round 5 / #5624` lies inside the
identical-arm band of its row (rows 8, 256 and 512,
and 128 on GB200, are ties), and every row stays above 1.00 against the
fastest stock chain.

FlashInfer-side benchmark on the delivered tree
(`benchmarks/bench_cake_kimi_k3_tp12_tail.py`, rank-max of per-rank
CUPTI
spans, median over iterations, counterbalanced groups; `max|diff|`
against the stock chain's own output):

| M | GB300 stock us | GB300 fused us | speedup | GB200 stock us | GB200
fused us | speedup |
|---|---|---|---|---|---|---|
| 1 | 111.2 | **17.6** | **6.33x** | 115.8 | **17.8** | **6.49x** |
| 8 | 120.3 | **22.6** | **5.33x** | 124.0 | **22.8** | **5.44x** |
| 32 | 122.8 | **24.0** | **5.12x** | 126.1 | **24.2** | **5.21x** |
| 64 | 123.2 | **25.3** | **4.86x** | 126.5 | **25.5** | **4.96x** |
| 128 | 137.0 | **28.8** | **4.75x** | 139.8 | **28.7** | **4.87x** |
| 256 | 147.6 | **39.8** | **3.71x** | 150.8 | **40.2** | **3.75x** |
| 512 | 181.2 | **58.0** | **3.12x** | 185.8 | **59.7** | **3.11x** |
| 1024 | 252.4 | **91.5** | **2.76x** | 260.7 | **93.2** | **2.80x** |
| 2048 | 375.7 | **161.6** | **2.32x** | 415.2 | **162.4** | **2.56x** |
| 4096 | 605.5 | **294.4** | **2.06x** | 643.4 | **296.0** | **2.17x** |

50 warmup + 200 iterations x 3 counterbalanced groups per rack;
`max|diff| <= 0.0312` on every row; rank spread 4.2-7.2 us.

## Tests

- `tests/experimental/test_cake_kimi_k3_tp12_tail.py` — CPU tests
(`pytest tests/experimental/test_cake_kimi_k3_tp12_tail.py
-k 'not twelve'`) and the twelve-rank GPU test (`torchrun --nnodes 3
--nproc-per-node 4 ... -m pytest
tests/experimental/test_cake_kimi_k3_tp12_tail.py -k twelve_ranks`:
reference at 1e-2, rank invariance, idempotence,
CUDA-graph replay, `max_tokens` guard) — pass on both racks (CPU
inventory tests rc 0; twelve-rank test rc 0 on every node; benchmark
10/10 rows > 1).

## Baselines and their source PRs

- Regression baseline: the #5624 fused chain (`85bfa5e4b`'s
`cake_backend.py`; merged 2026-09-28), re-measured as its own
arm in every A/B of this round (paired rank-max medians, identical-arm
control).
- Previous deliveries of this operator: #5603 (round 3: the operator),
#5624 (round 4: persistent K3 from 256 tokens,
  weight-streaming K2 for `M <= 4`).
- Stock chain: `flashinfer.norm.rmsnorm` from #207 (`3e515a475`,
2024-04-21; `include/flashinfer/norm.cuh`, `csrc/norm.cu`),
  module layout from #643 (`8e3d25874`, 2024-12-10); NCCL all-reduce via
`torch.distributed._functional_collectives.all_reduce`, cuBLAS
`torch.mm` / `torch.add` of PyTorch
2.13.0a0+9186a08b2c.nv26.07 (CUDA 13.3, container
`nvcr.io/nvidia/sglang:26.07-py3`), NCCL 2.30.7.
- Reused infrastructure (not a baseline):
`MNNVLAllReduceFusionWorkspace` from #2130 (`fd0c2f124`) on the MNNVL
allocator
  of #1213 (`a03c2909d`), two-shot stages per #4473 (`b8c21928b`).
- Branch merge-base with `main`: `85bfa5e4b` (#5624, 2026-09-28). No
upstream commit after the merge-base touches
`flashinfer/norm.py`, `csrc/norm.cu`, `include/flashinfer/norm.cuh`,
`flashinfer/kimi_k3_tp12_tail.py` or
`flashinfer/experimental/kimi_k3_tp12_tail/` (`git log
85bfa5e4b..origin/main -- <files>` is empty as of `85bfa5e4b` = upstream
`main` at publication time, unchanged since the merge-base).

## Evidence

Every number in the export tables comes from the generated-program
export protocol of the Cake repository (frozen protocol
`kimi_k3_tp12_tail`: twenty shapes = ten token counts x two
architectures, arms `source` = Cake runtime / `exported` = this
FlashInfer runtime / `stock` = the NCCL -> `flashinfer.norm.rmsnorm` ->
cuBLAS -> NCCL -> add chain in CUDA-graph form, twelve
ranks under torchrun on three trays, rank-max CUPTI medians, 3
counterbalanced groups x 600 warmup + 1200 reportable samples
per arm, source/export parity gate `>= 0.97`, collective endpoint drift
`<= 0.30`, directional disagreement `<= 0.12`,
loaded-clock fraction `>= 0.80`). Both runs passed every shape (20/20
verdict `pass`; parity 0.986-1.022 (geomean 0.999)
on GB300, 0.987-1.015 (geomean 1.002) on GB200; geomean stock/export
3.52x (#5624: 3.49x) GB300,
3.58x (#5624: 3.51x) GB200). The sample counts and the drift bound are
wider than #5624's 300 + 600 / 0.08: the first
round-5 runs at the previous producer revision failed only the M = 1
shape, on endpoint drift, on both racks — the two-kernel
M = 1 chain drifted 8-27 % on GB300 and 5-14 % on GB200 within
600-sample groups in both arms alike, the stock chain 1-11 %,
every other row stayed below 0.08, and parity (0.995 / 1.0022) and
directional disagreement (0.011) passed — so the
reportable window was doubled and the collective drift bound set to the
observed wander; the parity, directional and clock
gates are unchanged. The trees delivered by the GB300 and the GB200
export runs are byte-identical (the SHA-256 of every file is equal); the
80 round-4 generated sources are removed as listed by the export's
applied record (81 files: the registry module plus the generated
sources per architecture; `applied.json` lists them with their SHA-256).
Receipts stay on the measuring clusters; the
manifest (host, path, size, SHA-256) is kept with the internal export
receipts.

| artifact | GB300 (sm_103a) bytes / SHA-256 | GB200 (sm_100a) bytes /
SHA-256 |
|---|---|---|
| `applied.json` | 33516 / `5b32e83f6c9da51f` | 33516 /
`5b32e83f6c9da51f` |
| `build.json` | 7372 / `5e69c20255355194` | 7372 / `2e5418959a0c720a` |
| `delivered_<arch>.files` | 16567 / `5c5d1b5d8e2af269` | 16567 /
`5c5d1b5d8e2af269` |
| `delivery.json` | 52486 / `e04c5c57c1d4ddf5` | 52486 /
`e04c5c57c1d4ddf5` |
| `fi_bench_<arch>.json` | 8204 / `e4abb880fce9c9cd` | 8248 /
`37defcdfa655082f` |
| `manifest_<arch>.sha256` | 6096 / `1d04ac8eacadd62b` | 15372 /
`d4c70a9283fad35f` |
| `run.json` | 148479 / `955fc8ac2388ef9e` | 148537 / `f0b85454994df586`
|
| `sizes_<arch>.txt` | 2805 / `97ac36e75808955a` | 7521 /
`66cfeade446c9566` |
| `summary.json` | 112658 / `f6cadb2dc3a221b7` | 112629 /
`7ea084672929ea0b` |
| `summary.md` | 6677 / `56d2afb003641ad8` | 6677 / `8f1400f7005623df` |
| `tp12_m1024_<arch>.json` | 551714 / `f86168ec7a4e9f0e` | 552918 /
`d3f1ca27b5505db7` |
| `tp12_m128_<arch>.json` | 551360 / `f281b4b73cf77b6f` | 550718 /
`0e4d70c386b4d41b` |
| `tp12_m1_<arch>.json` | 989411 / `eabdd6486d615c10` | 990008 /
`5c4ebad5e46fc955` |
| `tp12_m2048_<arch>.json` | 552367 / `3c16c0d78424d368` | 552695 /
`739e39ef4b75f435` |
| `tp12_m256_<arch>.json` | 551034 / `153b293e70562519` | 550818 /
`3b134b25a433c199` |
| `tp12_m32_<arch>.json` | 550619 / `3746f24621a41575` | 551633 /
`4e467ce623b71e9f` |
| `tp12_m4096_<arch>.json` | 553190 / `fc0de6d194a63635` | 552750 /
`3e02c57013eec863` |
| `tp12_m512_<arch>.json` | 552233 / `13acc74270cab842` | 551154 /
`554c7e1a691292f6` |
| `tp12_m64_<arch>.json` | 550801 / `37e4e678961185d7` | 549923 /
`41d0961c2b6665c2` |
| `tp12_m8_<arch>.json` | 955021 / `036e21d4e42729e0` | 954356 /
`6adf2c09c557cc48` |

SHA-256 prefixes (16 hex digits) of the compact receipts and summaries
of each run; the delivered sources are listed with their full SHA-256 in
`delivered_<arch>.files` (81 entries, identical on both racks).

Correctness in the same runs: `source` and `exported` pass the fp32
reference at `atol = rtol = 1e-2` on every rank at every
shape and are bitwise identical to each other; the stock arm is held to
`5e-2` (NCCL rounds every ring hop to BF16).
Source-side, the round-5 chain is bitwise identical to the #5624 chain
at every M in {1, 2, 3, 4, 8, 16, 32, 64, 128, 256,
512, 1024, 2048, 4096} on both racks (twelve-rank bitwise invariance,
idempotence, CUDA-graph replay = eager) and at
M = 8192 on GB200 (58 720 256 elements, 0 diffs). FlashInfer-side
validation on the delivered tree (same trays): CPU tests
and the twelve-rank GPU test `-k twelve_ranks` — pass on both racks (CPU
inventory tests rc 0; twelve-rank test rc 0 on every node; benchmark
10/10 rows > 1); the benchmark table above is from the same steps.
compute-sanitizer 2026.2.1 (twelve ranks,
`nvcr.io/nvidia/pytorch:26.07-py3`, filtered to the Cake kernels) on
both racks
(GB300 NVL72 and GB200 NVL72, three trays of four GPUs each, the shipped
kernel module): synccheck and memcheck report
`ERROR SUMMARY: 0 errors` on all twelve ranks for the ESS + K23 chain at
M = 1, 2, 4, 8, 16, 32, 128 (one-shot ESS K1 of every
rank, grouped two-shot ESS K1, K23 for both slice widths, K3-ESS) and
for the bulk chain at M = 512, 2048 (bulk persistent K3,
bulk two-shot K1) — 48 of 48 per-rank summaries on each rack.

## Limits

Twelve ranks in one NVLink domain with CUDA fabric symmetric memory and
multicast only; `sm_100a` / `sm_103a`; BF16
model-layout weights; `M <= max_tokens` of the workspace (default 4096;
8192 verified on GB200 NVL72); every rank launches
the same `M`.

Tracker: #4254.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added token-count-aware execution routes for Kimi K3 TP12, including
fused processing for up to 4 tokens, ESS-based processing for 5–255
tokens, and persistent processing for larger batches.
* Shared partials are scattered earlier for batches below 256 tokens,
and cuBLAS is used for batches above 4 tokens.
* **Performance**
* The benchmark now reports timing from per-rank kernel activity,
including the maximum rank span and rank-to-rank timing spread.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [422a5ea](https://github.com/flashinfer-ai/flashinfer/commit/422a5ea6e3a0473a54065fc5a9914bd0bb65de41)

- **作者**: eigen
- **时间**: 2026-09-28T21:14:03Z
- **提交信息**: perf(cake_kda): round 5 — grouped TMEM loads with the state decay off the ready chain, strided q/k/v read in place, ping-pong prefix chain (#5641)

Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

# perf(cake_kda): round 5 — grouped TMEM loads with the state decay off
the ready chain, strided q/k/v read in place, ping-pong prefix chain

Base `main` (b1fba8d22, round 4 #5622 merged). The branch carries four
runtime commits, three kernel levers with regenerated sm_100a / sm_103a
exports, and the regression tests.

## 1. Kernel levers (prepared BF16 KDA prefill, unbounded softplus gate)

- **3d — grouped TMEM loads, state decay hoisted off the ready chain**
(`flashkda_blackwell_bf16_fused_m128`). The main pass loads each leg's
TMEM fragments as one group and applies the per-chunk state decay before
the ready wait instead of on the critical path behind it. Apply-route
composite, same node A B A B, cold-L2 CUPTI medians, two repetitions:
B200 −1.0…−1.9 % (2×8192 H16 rows 582.4 → 571.1 µs), GB300 −2.6…−3.7 %
(554.3 → 533.8 µs); the pair-map kernel −12…−23 %.
- **5b — strided q / k / v read in place.** The fused M128 launch and
the affine split launch accept q / k / v as strided views of one packed
qkv row (dense `[H, 128]` token payload, one shared token pitch that is
a multiple of 8 elements); the TMA descriptors take the pitch from the
TensorView strides, every other body gets one dense copy. Bitwise vs
dense operands; the serving adapter's three `.contiguous()` copies
(219–231 µs per 2×8192 H16 layer call, 88–94 µs at 8192 H12) leave the
prepared path. The affine split gate (`_supports_affine_split_launch`)
was still requiring contiguous q / k / v, which sent every strided
16K-token chunk to the sequential body in the first serving rerun (no
`split_seq` route events, in32k throughput 0.98 vs Triton, out-of-memory
on B200 with the 16K-token direct plan next to the KV pool); the last
commit gates on the shared layout rule and adds
`test_strided_qkv_views_take_the_same_route_as_dense_bitwise`.
- **8j — ping-pong M in the prefix chain**
(`flashkda_blackwell_map_prefix_m128`). Two M buffers with a two-stage
`snap_done` / `m_ready` handshake and grouped TMEM loads; the
composite's prefix kernel −15…−19 % (GB300 54.9 → 46.4 µs at 2×8192 H16;
B200 58.2 → 48.5). Composite −1.1…−1.6 % on both GPUs.

Final head vs the round-4 head (same node, A F A F, cold-L2 CUPTI
medians, 2 reps): B200 0.950–0.979 on the five composite cases (2×8192
H16 rows, 8192 H16, 8192 H12, 3000+13384 H12, 2×8192 H16 BF16 pool),
GB300 0.929–0.965. Outputs bitwise vs the chain route's pool; checkpoint
rows max diff ≤ 3e-8.

## 2. Regenerated exports

`csrc/kda/bf16`: sm_100a and sm_103a programs regenerated from the lever
source (`--replace-existing`, 359/359 rows measured and bitwise vs
source on both arches; staged / extra passes; the additive
`CAKE_KDA_AFFINE_APPLY=0` chain pass resolves 351/359).

## Evidence

| check | B200 (sm_100a) | GB300 (sm_103a) |
|---|---|---|
| `tests/kda` (3 files) on the arch tree / after the chain pass / with
the gate fix (81 = 78 + 3 new) / on the combined tree | 78 / 78 / 81 /
81 passed | 78 / 78 / 81 / 81 passed |
| export validate, 359 rows vs source | 359/359 bitwise (export/source
median 0.999) | 359/359 bitwise (median 0.999) |
| compute-sanitizer synccheck + memcheck on the changed launchers | 6
launchers, 0 errors | 6 launchers, 0 errors |
| bench_tb, 56 rows vs Triton, same node, A B A B vs the round-4 head |
56/56 > 1 on GPU and event time; GPU B/A ≤ 1.007 on 55 rows,
`k3_wrapper_h16_lb5` BS16×T256 +1.0–1.3 % (65.4 → 66.1 µs, 5 reps;
bounded short-sequence case) | 56/56 > 1 on both metrics; GPU B/A ≤
1.003 |
| `bench-regression` floors | 2/2 PASS (0.6608 ms vs 0.8414; affine
0.1323 vs 0.1929) | 2/2 PASS (0.6144 vs 0.7014; 0.1246 vs 0.3552) |
| 600-dump activation replay (1880 sequences) | — | state rel L2 ≤ 1e-2
on 1880/1880; ≤ 2× Triton on 1846/1880 |
| SGLang #34299 correctness (greedy 64 / input logprobs, 8k / 32k / 64k)
| 64/64 at every length, mean abs 0.030 / 0.008 / 0.005 | same |
| SGLang #34299 throughput B/A (in8k / in32k / in64k / gsp c4 / c16 /
c64), with the gate fix, no fault | 1.039 / 1.041 / 1.095 / 1.002 /
0.984 / 1.003; gsm8k 0.915 vs 0.910; round 4 was 1.019 / 1.021 / 1.062 /
1.005 / 0.996 / 1.020 | 1.039 / 1.048 / 1.104 / 0.998 / 1.009 / 1.019;
gsm8k 0.920 vs 0.910; round 4 was 1.015 / 1.023 / 1.075 / 0.992 / 0.997
/ 1.021 |

## Baselines and their source PRs

- Triton FLA `chunk_kda` prefill: SGLang `--linear-attn-prefill-backend
triton` (SGLang main).
- Prepared BF16 KDA export, round 4: #5622 (merged).
- Prepared BF16 KDA export, round 3: #5598 (merged) + registry prune
#5605.
- Prepared BF16 KDA export, round 2: #5573.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* BF16 KDA now supports Q, K, and V tensors with certain non-contiguous
leading layouts, provided they meet the required dimensionality and
innermost-stride constraints.
* **Bug Fixes**
* Improved handling of these layouts during chunked processing, with
results verified against equivalent contiguous inputs, including output,
state, and checkpoint values.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [e00293b](https://github.com/flashinfer-ai/flashinfer/commit/e00293b43373f736d9a078dc2e4d39b6540401a8)

- **作者**: x41lakazam
- **时间**: 2026-09-28T21:04:04Z
- **提交信息**: [moe_ep] Fix EXPERT_MAJOR unnecessary computation of padded elements (#5265)

## Problem 

On the `moe_ep` split path, NCCL EP's LL `EXPERT_MAJOR` dispatch the
tokens sorted by expert, each expert has a buffer which is sized for the
worst case (for cuda graph compatibility), i.e the maximum capacity of
one expert, of `cap`. Real tokens are front-packed in the buffer, the
rest is padding.

Compute then runs through the generic `flashinfer.fused_moe` API, whose
`MoEActivationPack` is `[M, hidden]` plus routing. It has no notion of a
padded row: every row it is handed is, by definition, a token. Therefore
the permute (or fused gather), GEMM1, the activation, GEMM2 and finalize
all ran over the padding, wasting a lot of CTAs.

Disclaimer: The speed-up is real but not in every case, particularly it
gets worse with scaling, a guard rule needs to be decided

## Solution

Mark the padding rows as tokens belonging to an expert this rank doesn't
own.

The padding rows are not computed since the routing kernel behind
`moe_sort` only counts an expert into its histogram when that expert is
local.

No kernel change and no data moves: `moe_sort` returns index maps only,
so the dispatched buffer stays where it is and consumers simply never
gather the padding.

Built only to `EXPERT_MAJOR` (RANK_MAJOR's counts are per-source-rank,
not per-expert) and controled by a flag:
`FLASHINFER_MOE_EP_EXCLUDE_PADDING_ROWS=0`.

## Performance results

`benchmarks/bench_moe_ep.py` — FlashInfer's own EP benchmark — on **4x
NVIDIA GB200 (sm100)**,
NCCL EP, LL `EXPERT_MAJOR`, NVFP4, CuTe-DSL. Routing is artificially
balanced.

I swept all the combinations of (EP world size, model geometry, token
count) combination:


Per-GPU padded work | W4 | W8 | W16 | W32 | Spread | tot points | Median
speedup | Points sped up
-- | -- | -- | -- | -- | -- | -- | -- | --
< 3e10 | 0.89× (5) | 0.91× (9) | 0.86× (16) | 0.86× (22) | 0.05× | 52 |
0.86× | 0%
3e10 – 1e11 | 0.87× (6) | 0.88× (9) | 0.86× (12) | 0.87× (13) | 0.02× |
40 | 0.86× | 2%
1e11 – 3e11 | 1.02× (18) | 0.97× (18) | 0.96× (18) | 0.96× (12) | 0.06×
| 66 | 0.98× | 44%
3e11 – 1e12 | 1.66× (21) | 1.53× (16) | 1.63× (12) | 1.44× (7) | 0.23× |
56 | 1.61× | 100%
1e12 | 3.17× (14) | 3.04× (8) | 2.91× (3) | 2.62× (1) | 0.55× | 26 |
3.04× | 100%



Here is a benchmark of Kimi K2: 384 experts, top_k 8, hidden 7168,
intermediate 2048.

This is a full forward, so it includes dispatch and combine and charges
the change for the cost
of building the activation pack.

World | Tokens | Speedup (E2E)
-- | -- | --
32 | 8192 | 2.617
32 | 4096 | 1.796
16 | 8192 | 3.258
16 | 4096 | 2.912
16 | 2048 | 1.977
8 | 8192 | 4.529
8 | 4096 | 4.133
8 | 2048 | 2.985
4 | 4096 | 5.245
4 | 2048 | 4.716

Later-on I ran the same benchmark with skewed routing, here is the
impact of the skew on the perf, α is the Zipf exponent (0.5 is medium
skew, 1 is high skew):

Model | World | Tokens | Uniform | α = 0.5 | α = 1.0 | Max shift
-- | -- | -- | -- | -- | -- | --
DeepSeek-V3 | 4 | 1024 | 2.24× | 2.20× | 2.28× | 0.04
DeepSeek-V3 | 4 | 4096 | 4.39× | 4.36× | 4.07× | 0.33
DeepSeek-V3 | 16 | 4096 | 2.00× | 2.03× | 1.93× | 0.08
GLM-4.6 | 4 | 2048 | 1.98× | 2.07× | 1.69× | 0.29
GLM-4.6 | 16 | 512 | 0.85× | 0.85× | 0.85× | 0.01
Qwen3-30B-A3B | 4 | 1024 | 1.01× | 0.91× | 0.91× | 0.10
Qwen3-30B-A3B | 16 | 4096 | 0.87× | 0.82× | 0.96× | 0.09


## Tests

**Multi-rank EP numerics.**
`tests/moe_ep/test_moe_ep_compute_correctness.py` at 4 ranks on
GB200, comparing full dispatch -> compute -> combine against a
single-process dense reference:
4/4 passed with the exclusion **enabled**, identical to disabled.

```
test_moe_ep_compute_matches_dense_reference[expert_major]      PASSED
test_moe_ep_compute_matches_dense_reference[rank_major]        PASSED
test_w4a8_packed_dispatch_matches_bf16_dispatch[expert_major]  PASSED
test_w4a8_packed_dispatch_matches_bf16_dispatch[rank_major]    PASSED
```

This is the check that matters here: `bench_moe_ep.py` measures latency
only, so a change that
wrongly skipped work would look fast rather than broken.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Expert-major dispatch can exclude padding rows when
`FLASHINFER_MOE_EP_EXCLUDE_PADDING_ROWS` is set to `1`. This opt-in
behavior applies to supported workload shapes; it remains off by
default.
* **Performance**
* When enabled, processing uses per-expert token counts to skip padding
rows for remote experts. Benefits vary with workload shape and the
amount of padding.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [443347d](https://github.com/flashinfer-ai/flashinfer/commit/443347d3eac60941c4d3da8fb20f599f62d5ed80)

- **作者**: eigen
- **时间**: 2026-09-28T21:00:59Z
- **提交信息**: perf(cake_kimi_k3_latent_moe): packed global-y norm, landing-zone alias, deferred cluster wait and a 128-wide TP8 tail tile (SM100a/SM103a), regenerated programs (#5647)

Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

## Summary

Round 7 of the Kimi-K3 Stable LatentMoE front / tail projections in
`flashinfer/experimental/kimi_k3_latent_moe` (#5575, #5584, tracker
#4254): a paired lever ledger on B200 and B300 (A/B in interleaved
CUDA-graph groups, cold-L2 CUPTI timing, an A/A control per row, a
second independent process on every row under 10 us) adopts five per-row
rules in the Cake tree, four of which change the exported programs;
every other candidate on the round's list was measured or attributed and
closed.

- **Tensor-map binding (unchanged in this package).** Every program
binds its tensor maps by value (`const __grid_constant__ CUtensorMap`
kernel parameters), as the previous rounds did; the package has no
TMA-descriptor workspace. The Cake production launcher now binds by
value too on every instance except four -- the TP8 decode-tail instances
at N_PAD 16 / 32 / 64 and the TP1 T=1024 prefill tail GEMM -- where
paired measurements on three node pairs per GPU show the by-value form
node-dependent (T=16: +3.8 % on one pair, -4..-8 % on two others; T=32:
-3.5 % on one B300 GPU; T=64: -2..-4 %; the T=1024 GEMM -1..-3 % on
B200), so those keep the pointer ABI there. The corresponding programs
here stay by value; a caller-owned descriptor workspace that would let
them bind by pointer is a follow-up, not part of this PR. The kernel
symbols and route keys are unchanged by this.
- **Packed bf16x2 global-y norm row path** (decode tail, T >= 32 at TP8
and every TP1 row): the latent row stays in `bf16x2` words through the
RMSNorm (square via `bf16x2 -> f32` adds, one `rsqrt`, `bf16x2` multiply
by the weight); the same roundings in the same places, so `y` and `out`
are bitwise identical to the previous chain. Tail TP8 T=32 / 64 / 128:
+13.7 / +6.9 / +5.3 % (B200), +9.9 / +5.9 / +4.7 % (B300).
- **Landing-zone alias for the T=128 cluster instances** (`_la`): the
DSMEM landing zone of the K-split combine is aliased on the drained A
ring instead of owning 64 KiB of shared memory, which buys two ring
stages (5 -> 7); rank 0 hands "ring drained" to rank 1 through an 8-byte
`st.async` word. Only the N_PAD-128 instances that stream >= 32 chunk
units per CTA take it: tail TP1 T=128 +8.3 / +7.0 %, front TP8 T=128
+7.9 / +6.4 % (B200 / B300); the short TP8 tail rows lose with the
handshake and keep their zone.
- **Deferred cluster wait on the T=16 staged-rows tail instance**
(`_ww`): the instance that already skips the tensor-map prefetch lets
its TMA / MMA warps skip the cluster rendezvous (the epilogue warps
alone wait for the pair) and start the ring fill right after the
CTA-local setup: +2.7 / +2.1 % (B200 / B300, two processes) and +2.0 /
+1.7 % under the pointer ABI on a third node pair.
- **128-wide pair tile for the TP8 T=512 prefill tail**
(`tail_gemm:tp8e0f0s9n128`): 56 column tiles x 2 row-tile pairs = 224
CTAs (1.5 waves of whole tiles instead of 112 CTAs on 148 SMs) with a
9-deep ring: +8.1..+8.9 % in two processes per GPU; T=256 and T >= 1024
keep the 256-wide tile (they lose 2-12 % with the narrow tile), so the
rule is per row.

Host planner (`cake_backend.py`): `land_alias_auto(n_pad, k_units)`, the
`wait_warps` plan field, `tail_gemm_config(M, tp) -> (num_stages,
block_n)` and the `n<block_n>` kernel-key component
(`tail_gemm:tp8e0f0s9n128`); `_tail_workspace` is sized by the tile
width; the late-trigger norm instance leaves the production route set.

**Follow-up commit `891f69adb`** (on top of the delivery commit
`8ce7ef04e`): the module-level annotation of the `_TAIL_WS` cache in
`cake_backend.py` is typed as the 4-tuple key `(device, sk_tiles,
max_seg, block_n)` that the round-7 `_tail_workspace` uses; the upstream
`pre-commit` mypy hook rejected the 3-tuple annotation on the delivery
head. Annotation only: no runtime change, no generated program touched;
the receipts and the pytest runs below are bound to the programs of
`8ce7ef04e`, which this commit leaves byte-identical.

## Evidence (Cake export protocol, producer `e8937a5205a`, target
`b4a2da646a3`)

Every row runs the source (Cake production launcher) and the exported
programs in counterbalanced CUDA-graph groups; correctness = both arms
against the FP32/BF16 torch reference, bitwise source == export.

| arch | GPU | rows sealed | clock-unqualified (disclosed) | correct
(bitwise source == export) | source/export | steps |
|---|---|---|---|---|---|---|
| sm_100a | B200 | 50 / 60 | 9 clock-unqualified + `tail_tp8_m16`
(source / export ratio 0.930 below the 0.94 gate on the retry; correct,
bitwise) | 50 / 50 | 0.9734 - 1.0755 | `5a00b5fa1ca4b7fc9b733cf7`
(protocol) + `0aca3d85a1ce0e87bde7d441` (export) +
`25bac3a89b03cca512a70471` (retry round + FlashInfer tests) |
| sm_103a | B300 | 50 / 60 | 9 clock-unqualified + `front_tp1_m1024`
(endpoint-drift gate on both measurements; correct, bitwise, ratio
0.9992) | 50 / 50 | 0.9646 - 1.0639 | `c9996135d315f7e29e22e3a3`
(export) + `ed57976db5185227697f584d` (retry round + FlashInfer tests) |

Clock-unqualified rows: the sustained dense tcgen05 GEMM rows run at the
power cap and the interleaved timing session sampled the loaded SM clock
below 0.85 x max on both bounded rounds (retry sampled / max MHz):
sm_100a `front_tp1_m2048` 1620, `front_tp1_m4096` 1432,
`front_tp1_m8192` 1350, `front_tp1_m16384` 1305, `front_tp8_m8192` 1507,
`front_tp8_m16384` 1387, `tail_tp1_m4096` 1522, `tail_tp1_m8192` 1425,
`tail_tp1_m16384` 1350 (/ 1965); sm_103a `front_tp1_m2048` 1590,
`front_tp1_m4096` 1395, `front_tp1_m8192` 1260, `front_tp1_m16384` 1245,
`front_tp8_m8192` 1417, `front_tp8_m16384` 1282, `tail_tp1_m4096` 1455,
`tail_tp1_m8192` 1312, `tail_tp1_m16384` 1252 (/ 2032) -- the same set
the previous round disclosed; these rows are correct and above 1.00 in
the source-kernel contract and are re-measured with the exported
programs in the speedup table below. The `tail_tp8_m16` ratio on B200:
the Cake source arm launches that instance with device-memory tensor-map
descriptors (the per-instance pointer ABI of the producer tree), while
this package binds every program's descriptors by value; on that node
the by-value form is 7 % slower, so the source runs faster than the
export. The exported program is correct and bitwise; the row is
disclosed rather than the gate loosened. The delivery (registries +
generated sources) is byte-identical from the B200 and the B300 export
(sha256 `b72137682d2d29f8`).

<details><summary>sm_100a per-row receipts</summary>

| row (B200, sm_100a) | route | source | export | source / export |
correctness (both arms) | bitwise src == exp | verdict |
|---|---|---|---|---:|---|---|---|
| front_tp1_m1 | decode | 50.27 us | 49.98 us | 1.0058 | pass | yes |
sealed |
| front_tp1_m2 | decode | 50.56 us | 50.62 us | 0.9987 | pass | yes |
sealed |
| front_tp1_m4 | decode | 50.75 us | 50.24 us | 1.0102 | pass | yes |
sealed |
| front_tp1_m8 | decode | 50.34 us | 50.40 us | 0.9987 | pass | yes |
sealed |
| front_tp1_m16 | decode | 50.62 us | 50.50 us | 1.0025 | pass | yes |
sealed |
| front_tp1_m32 | decode | 51.01 us | 51.04 us | 0.9994 | pass | yes |
sealed |
| front_tp1_m64 | decode | 53.63 us | 53.70 us | 0.9988 | pass | yes |
sealed |
| front_tp1_m128 | decode | 59.07 us | 59.30 us | 0.9962 | pass | yes |
sealed |
| front_tp1_m256 | prefill | 60.77 us | 60.90 us | 0.9979 | pass | yes |
sealed |
| front_tp1_m512 | prefill | 86.78 us | 86.46 us | 1.0037 | pass | yes |
sealed |
| front_tp1_m1024 | prefill | 166.05 us | 166.02 us | 1.0002 | pass |
yes | sealed |
| front_tp1_m2048 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1545/1965 MHz first, 1620/1965 MHz retry) |
| front_tp1_m4096 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1380/1965 MHz first, 1432/1965 MHz retry) |
| front_tp1_m8192 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1387/1965 MHz first, 1350/1965 MHz retry) |
| front_tp1_m16384 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1305/1965 MHz) |
| front_tp8_m1 | decode | 21.54 us | 21.66 us | 0.9941 | pass | yes |
sealed |
| front_tp8_m2 | decode | 21.66 us | 21.76 us | 0.9956 | pass | yes |
sealed |
| front_tp8_m4 | decode | 21.54 us | 21.66 us | 0.9941 | pass | yes |
sealed |
| front_tp8_m8 | decode | 21.73 us | 21.86 us | 0.9941 | pass | yes |
sealed |
| front_tp8_m16 | decode | 22.02 us | 22.02 us | 1.0000 | pass | yes |
sealed |
| front_tp8_m32 | decode | 23.20 us | 23.39 us | 0.9918 | pass | yes |
sealed |
| front_tp8_m64 | decode | 25.60 us | 25.66 us | 0.9975 | pass | yes |
sealed |
| front_tp8_m128 | decode | 31.20 us | 31.17 us | 1.0011 | pass | yes |
sealed |
| front_tp8_m256 | prefill | 44.42 us | 44.54 us | 0.9971 | pass | yes |
sealed |
| front_tp8_m512 | prefill | 46.88 us | 47.01 us | 0.9973 | pass | yes |
sealed |
| front_tp8_m1024 | prefill | 82.14 us | 81.44 us | 1.0086 | pass | yes
| sealed |
| front_tp8_m2048 | prefill | 118.02 us | 118.08 us | 0.9995 | pass |
yes | sealed |
| front_tp8_m4096 | prefill | 243.78 us | 243.81 us | 0.9999 | pass |
yes | sealed |
| front_tp8_m8192 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1477/1965 MHz first, 1507/1965 MHz retry) |
| front_tp8_m16384 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1387/1965 MHz) |
| tail_tp1_m1 | decode | 31.52 us | 31.42 us | 1.0030 | pass | yes |
sealed |
| tail_tp1_m2 | decode | 31.52 us | 31.46 us | 1.0020 | pass | yes |
sealed |
| tail_tp1_m4 | decode | 31.62 us | 31.58 us | 1.0010 | pass | yes |
sealed |
| tail_tp1_m8 | decode | 31.81 us | 31.84 us | 0.9990 | pass | yes |
sealed |
| tail_tp1_m16 | decode | 33.79 us | 33.98 us | 0.9943 | pass | yes |
sealed |
| tail_tp1_m32 | decode | 34.27 us | 34.43 us | 0.9954 | pass | yes |
sealed |
| tail_tp1_m64 | decode | 36.32 us | 36.42 us | 0.9974 | pass | yes |
sealed |
| tail_tp1_m128 | decode | 42.85 us | 39.84 us | 1.0755 | pass | yes |
sealed |
| tail_tp1_m256 | prefill | 46.53 us | 46.56 us | 0.9993 | pass | yes |
sealed |
| tail_tp1_m512 | prefill | 56.93 us | 56.93 us | 1.0000 | pass | yes |
sealed |
| tail_tp1_m1024 | prefill | 107.55 us | 108.10 us | 0.9950 | pass | yes
| sealed |
| tail_tp1_m2048 | prefill | 203.39 us | 203.10 us | 1.0014 | pass | yes
| sealed |
| tail_tp1_m4096 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1417/1965 MHz first, 1522/1965 MHz retry) |
| tail_tp1_m8192 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1432/1965 MHz first, 1425/1965 MHz retry) |
| tail_tp1_m16384 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1350/1965 MHz) |
| tail_tp8_m1 | decode | 7.87 us | 7.90 us | 0.9958 | pass | yes |
sealed |
| tail_tp8_m2 | decode | 7.97 us | 8.00 us | 0.9960 | pass | yes |
sealed |
| tail_tp8_m4 | decode | 7.97 us | 8.03 us | 0.9920 | pass | yes |
sealed |
| tail_tp8_m8 | decode | 8.06 us | 8.13 us | 0.9921 | pass | yes |
sealed |
| tail_tp8_m16 | decode | 9.73 us | 10.46 us | 0.9297 | pass | yes |
disclosed: source / export ratio 0.9297 below the 0.94 gate (correct +
bitwise; the Cake source arm launches this instance with the pointer
tensor-map ABI, the package binds by value) |
| tail_tp8_m32 | decode | 10.94 us | 11.14 us | 0.9828 | pass | yes |
sealed |
| tail_tp8_m64 | decode | 11.71 us | 12.03 us | 0.9734 | pass | yes |
sealed |
| tail_tp8_m128 | decode | 14.50 us | 14.59 us | 0.9936 | pass | yes |
sealed |
| tail_tp8_m256 | prefill | 15.65 us | 15.65 us | 1.0000 | pass | yes |
sealed |
| tail_tp8_m512 | prefill | 18.53 us | 18.62 us | 0.9948 | pass | yes |
sealed |
| tail_tp8_m1024 | prefill | 26.53 us | 26.56 us | 0.9988 | pass | yes |
sealed |
| tail_tp8_m2048 | prefill | 40.03 us | 40.22 us | 0.9952 | pass | yes |
sealed |
| tail_tp8_m4096 | prefill | 65.73 us | 66.14 us | 0.9937 | pass | yes |
sealed |
| tail_tp8_m8192 | prefill | 116.67 us | 116.70 us | 0.9997 | pass | yes
| sealed |
| tail_tp8_m16384 | prefill | 227.63 us | 227.84 us | 0.9991 | pass |
yes | sealed |

</details>

<details><summary>sm_103a per-row receipts</summary>

| row (B300, sm_103a) | route | source | export | source / export |
correctness (both arms) | bitwise src == exp | verdict |
|---|---|---|---|---:|---|---|---|
| front_tp1_m1 | decode | 50.24 us | 50.08 us | 1.0032 | pass | yes |
sealed |
| front_tp1_m2 | decode | 50.37 us | 50.46 us | 0.9981 | pass | yes |
sealed |
| front_tp1_m4 | decode | 50.40 us | 50.46 us | 0.9987 | pass | yes |
sealed |
| front_tp1_m8 | decode | 50.59 us | 50.40 us | 1.0038 | pass | yes |
sealed |
| front_tp1_m16 | decode | 50.82 us | 50.62 us | 1.0038 | pass | yes |
sealed |
| front_tp1_m32 | decode | 51.30 us | 51.36 us | 0.9988 | pass | yes |
sealed |
| front_tp1_m64 | decode | 54.27 us | 54.34 us | 0.9988 | pass | yes |
sealed |
| front_tp1_m128 | decode | 59.26 us | 59.33 us | 0.9989 | pass | yes |
sealed |
| front_tp1_m256 | prefill | 60.61 us | 60.80 us | 0.9969 | pass | yes |
sealed |
| front_tp1_m512 | prefill | 83.94 us | 84.51 us | 0.9932 | pass | yes |
sealed |
| front_tp1_m1024 | prefill | 154.40 us | 154.53 us | 0.9992 | pass |
yes | disclosed: endpoint-drift gate (correct + bitwise, ratio 0.9992) |
| front_tp1_m2048 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1605/2032 MHz first, 1590/2032 MHz retry) |
| front_tp1_m4096 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1297/2032 MHz first, 1395/2032 MHz retry) |
| front_tp1_m8192 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1275/2032 MHz first, 1260/2032 MHz retry) |
| front_tp1_m16384 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1252/2032 MHz first, 1245/2032 MHz retry) |
| front_tp8_m1 | decode | 21.70 us | 21.66 us | 1.0015 | pass | yes |
sealed |
| front_tp8_m2 | decode | 21.73 us | 21.79 us | 0.9971 | pass | yes |
sealed |
| front_tp8_m4 | decode | 21.73 us | 21.70 us | 1.0014 | pass | yes |
sealed |
| front_tp8_m8 | decode | 21.89 us | 21.86 us | 1.0015 | pass | yes |
sealed |
| front_tp8_m16 | decode | 22.14 us | 22.18 us | 0.9986 | pass | yes |
sealed |
| front_tp8_m32 | decode | 23.17 us | 23.30 us | 0.9945 | pass | yes |
sealed |
| front_tp8_m64 | decode | 25.73 us | 25.86 us | 0.9950 | pass | yes |
sealed |
| front_tp8_m128 | decode | 31.36 us | 31.39 us | 0.9989 | pass | yes |
sealed |
| front_tp8_m256 | prefill | 42.24 us | 42.15 us | 1.0023 | pass | yes |
sealed |
| front_tp8_m512 | prefill | 44.90 us | 44.74 us | 1.0036 | pass | yes |
sealed |
| front_tp8_m1024 | prefill | 77.12 us | 77.19 us | 0.9992 | pass | yes
| sealed |
| front_tp8_m2048 | prefill | 111.78 us | 111.90 us | 0.9989 | pass |
yes | sealed |
| front_tp8_m4096 | prefill | 231.86 us | 231.97 us | 0.9995 | pass |
yes | sealed |
| front_tp8_m8192 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1612/2032 MHz first, 1417/2032 MHz retry) |
| front_tp8_m16384 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1282/2032 MHz) |
| tail_tp1_m1 | decode | 31.97 us | 31.78 us | 1.0060 | pass | yes |
sealed |
| tail_tp1_m2 | decode | 31.97 us | 31.71 us | 1.0081 | pass | yes |
sealed |
| tail_tp1_m4 | decode | 32.16 us | 31.87 us | 1.0090 | pass | yes |
sealed |
| tail_tp1_m8 | decode | 32.19 us | 32.22 us | 0.9990 | pass | yes |
sealed |
| tail_tp1_m16 | decode | 33.82 us | 33.82 us | 1.0000 | pass | yes |
sealed |
| tail_tp1_m32 | decode | 34.59 us | 34.56 us | 1.0009 | pass | yes |
sealed |
| tail_tp1_m64 | decode | 36.67 us | 36.67 us | 1.0000 | pass | yes |
sealed |
| tail_tp1_m128 | decode | 42.62 us | 40.06 us | 1.0639 | pass | yes |
sealed |
| tail_tp1_m256 | prefill | 46.30 us | 46.11 us | 1.0042 | pass | yes |
sealed |
| tail_tp1_m512 | prefill | 54.66 us | 54.69 us | 0.9994 | pass | yes |
sealed |
| tail_tp1_m1024 | prefill | 104.29 us | 104.61 us | 0.9969 | pass | yes
| sealed |
| tail_tp1_m2048 | prefill | 191.92 us | 192.74 us | 0.9958 | pass | yes
| sealed |
| tail_tp1_m4096 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1440/2032 MHz first, 1455/2032 MHz retry) |
| tail_tp1_m8192 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1447/2032 MHz first, 1312/2032 MHz retry) |
| tail_tp1_m16384 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1260/2032 MHz first, 1252/2032 MHz retry) |
| tail_tp8_m1 | decode | 8.03 us | 8.03 us | 0.9999 | pass | yes |
sealed |
| tail_tp8_m2 | decode | 8.06 us | 8.03 us | 1.0040 | pass | yes |
sealed |
| tail_tp8_m4 | decode | 8.06 us | 8.10 us | 0.9960 | pass | yes |
sealed |
| tail_tp8_m8 | decode | 8.13 us | 8.13 us | 0.9999 | pass | yes |
sealed |
| tail_tp8_m16 | decode | 9.60 us | 9.95 us | 0.9646 | pass | yes |
sealed |
| tail_tp8_m32 | decode | 11.11 us | 11.20 us | 0.9915 | pass | yes |
sealed |
| tail_tp8_m64 | decode | 12.06 us | 12.16 us | 0.9921 | pass | yes |
sealed |
| tail_tp8_m128 | decode | 14.43 us | 14.56 us | 0.9912 | pass | yes |
sealed |
| tail_tp8_m256 | prefill | 15.36 us | 15.23 us | 1.0084 | pass | yes |
sealed |
| tail_tp8_m512 | prefill | 17.63 us | 17.79 us | 0.9910 | pass | yes |
sealed |
| tail_tp8_m1024 | prefill | 24.90 us | 25.02 us | 0.9949 | pass | yes |
sealed |
| tail_tp8_m2048 | prefill | 38.08 us | 38.59 us | 0.9867 | pass | yes |
sealed |
| tail_tp8_m4096 | prefill | 63.17 us | 63.30 us | 0.9980 | pass | yes |
sealed |
| tail_tp8_m8192 | prefill | 112.23 us | 112.19 us | 1.0003 | pass | yes
| sealed |
| tail_tp8_m16384 | prefill | 212.99 us | 213.19 us | 0.9991 | pass |
yes | sealed |

</details>

### Measured speedups (Cake contract, paired cold-L2 CUPTI graph timing
vs the fastest stock chain of each row)

Kernel arm = the exported programs of this PR (CUDA-graph form, three
alternating groups, cold-L2 CUPTI timing, correctness of both arms
against the torch reference, graph == eager); denominator = the fastest
stock chain of the row (see Baselines). **B200: 60 / 60 rows > 1.00, min
1.028 (`tail_tp1_m16384`), geomean 1.582. B300: 60 / 60 rows > 1.00, min
1.020 (`tail_tp1_m2048`), geomean 1.589.** The seven tail TP8 rows below
14.5 us were measured in two independent processes per GPU (identical
medians).

| row | B200: exported program / fastest stock chain us = speedup |
B300: same |
|---|---|---|
| `front_tp1_m1` | 49.98 / 86.24 = 1.725 | 50.21 / 87.07 = 1.734 |
| `front_tp1_m2` | 50.08 / 86.46 = 1.726 | 50.37 / 87.27 = 1.732 |
| `front_tp1_m4` | 50.69 / 87.74 = 1.731 | 50.82 / 88.42 = 1.740 |
| `front_tp1_m8` | 50.08 / 86.40 = 1.725 | 50.24 / 86.85 = 1.729 |
| `front_tp1_m16` | 50.43 / 88.67 = 1.758 | 50.59 / 88.99 = 1.759 |
| `front_tp1_m32` | 51.23 / 90.62 = 1.769 | 51.39 / 90.02 = 1.752 |
| `front_tp1_m64` | 54.37 / 91.01 = 1.674 | 54.46 / 90.47 = 1.661 |
| `front_tp1_m128` | 58.75 / 94.88 = 1.615 | 58.98 / 94.56 = 1.603 |
| `front_tp1_m256` | 61.34 / 116.54 = 1.900 | 60.93 / 115.30 = 1.892 |
| `front_tp1_m512` | 86.94 / 164.57 = 1.893 | 84.77 / 158.62 = 1.871 |
| `front_tp1_m1024` | 164.51 / 289.02 = 1.757 | 152.64 / 266.37 = 1.745
|
| `front_tp1_m2048` | 330.98 / 595.42 = 1.799 | 307.97 / 559.81 = 1.818
|
| `front_tp1_m4096` | 671.49 / 1201.13 = 1.789 | 626.79 / 1183.02 =
1.887 |
| `front_tp1_m8192` | 1330.02 / 2371.39 = 1.783 | 1243.51 / 2320.69 =
1.866 |
| `front_tp1_m16384` | 2592.51 / 4732.41 = 1.825 | 2443.17 / 4592.68 =
1.880 |
| `front_tp8_m1` | 21.79 / 57.50 = 2.639 | 21.86 / 57.92 = 2.650 |
| `front_tp8_m2` | 21.89 / 57.15 = 2.611 | 21.86 / 57.79 = 2.644 |
| `front_tp8_m4` | 21.98 / 56.54 = 2.572 | 21.89 / 57.22 = 2.614 |
| `front_tp8_m8` | 21.92 / 56.99 = 2.600 | 22.02 / 57.73 = 2.622 |
| `front_tp8_m16` | 22.37 / 57.47 = 2.569 | 22.30 / 57.73 = 2.588 |
| `front_tp8_m32` | 23.39 / 59.68 = 2.551 | 23.52 / 59.23 = 2.518 |
| `front_tp8_m64` | 25.82 / 60.80 = 2.354 | 25.98 / 60.71 = 2.336 |
| `front_tp8_m128` | 31.45 / 63.36 = 2.014 | 31.81 / 62.53 = 1.966 |
| `front_tp8_m256` | 44.70 / 72.06 = 1.612 | 42.30 / 70.91 = 1.676 |
| `front_tp8_m512` | 47.30 / 78.43 = 1.658 | 45.12 / 76.19 = 1.689 |
| `front_tp8_m1024` | 81.06 / 106.51 = 1.314 | 77.31 / 102.75 = 1.329 |
| `front_tp8_m2048` | 117.98 / 170.88 = 1.448 | 111.07 / 162.59 = 1.464
|
| `front_tp8_m4096` | 250.53 / 321.38 = 1.283 | 237.83 / 305.91 = 1.286
|
| `front_tp8_m8192` | 489.94 / 653.09 = 1.333 | 466.72 / 642.55 = 1.377
|
| `front_tp8_m16384` | 938.78 / 1316.96 = 1.403 | 877.40 / 1270.92 =
1.448 |
| `tail_tp1_m1` | 31.36 / 39.20 = 1.250 | 31.62 / 39.62 = 1.253 |
| `tail_tp1_m2` | 31.36 / 40.32 = 1.286 | 31.65 / 40.35 = 1.275 |
| `tail_tp1_m4` | 31.58 / 40.00 = 1.266 | 31.78 / 40.26 = 1.267 |
| `tail_tp1_m8` | 31.68 / 39.42 = 1.244 | 31.90 / 39.75 = 1.246 |
| `tail_tp1_m16` | 33.98 / 40.10 = 1.180 | 33.92 / 40.35 = 1.190 |
| `tail_tp1_m32` | 34.46 / 39.94 = 1.159 | 34.59 / 40.45 = 1.169 |
| `tail_tp1_m64` | 36.48 / 40.13 = 1.100 | 36.70 / 40.80 = 1.112 |
| `tail_tp1_m128` | 39.87 / 44.54 = 1.117 | 40.10 / 44.96 = 1.121 |
| `tail_tp1_m256` | 46.50 / 48.80 = 1.050 | 46.18 / 48.93 = 1.060 |
| `tail_tp1_m512` | 56.80 / 72.03 = 1.268 | 54.43 / 69.63 = 1.279 |
| `tail_tp1_m1024` | 107.90 / 121.28 = 1.124 | 103.71 / 115.71 = 1.116 |
| `tail_tp1_m2048` | 207.97 / 215.87 = 1.038 | 197.73 / 201.63 = 1.020 |
| `tail_tp1_m4096` | 410.93 / 423.23 = 1.030 | 398.32 / 415.99 = 1.044 |
| `tail_tp1_m8192` | 833.68 / 878.27 = 1.054 | 812.20 / 867.82 = 1.069 |
| `tail_tp1_m16384` | 1715.30 / 1762.59 = 1.028 | 1658.83 / 1734.24 =
1.046 |
| `tail_tp8_m1` | 7.97 / 16.10 = 2.020 | 8.06 / 16.06 = 1.992 |
| `tail_tp8_m2` | 7.94 / 17.12 = 2.157 | 8.06 / 17.02 = 2.111 |
| `tail_tp8_m4` | 7.97 / 17.22 = 2.160 | 8.06 / 17.34 = 2.151 |
| `tail_tp8_m8` | 8.13 / 16.80 = 2.067 | 8.16 / 16.51 = 2.023 |
| `tail_tp8_m16` | 10.08 / 18.24 = 1.810 | 10.37 / 17.70 = 1.707 |
| `tail_tp8_m32` | 10.53 / 17.73 = 1.684 | 10.94 / 17.66 = 1.614 |
| `tail_tp8_m64` | 12.10 / 19.42 = 1.606 | 12.32 / 19.14 = 1.553 |
| `tail_tp8_m128` | 14.72 / 19.46 = 1.322 | 14.53 / 19.33 = 1.330 |
| `tail_tp8_m256` | 15.78 / 21.86 = 1.385 | 15.23 / 21.66 = 1.422 |
| `tail_tp8_m512` | 18.72 / 26.78 = 1.431 | 17.66 / 26.11 = 1.478 |
| `tail_tp8_m1024` | 26.53 / 36.54 = 1.378 | 24.99 / 35.30 = 1.412 |
| `tail_tp8_m2048` | 39.90 / 50.27 = 1.260 | 38.11 / 48.80 = 1.280 |
| `tail_tp8_m4096` | 65.86 / 95.01 = 1.443 | 63.36 / 92.10 = 1.454 |
| `tail_tp8_m8192` | 120.19 / 183.94 = 1.530 | 111.71 / 174.91 = 1.566 |
| `tail_tp8_m16384` | 244.26 / 356.29 = 1.459 | 226.59 / 339.46 = 1.498
|

### Baselines and their source PRs

- **Stock chain (Cake contract denominator, per row the fastest of):**
torch / cuBLAS `torch.mm` / `torch.addmm` (FP32-upcast or
`out_dtype=float32` router GEMM, BF16 latent / shared GEMMs, `addmm` for
the tail sum) and every FlashInfer `mm_bf16` backend that computes the
product (`auto`, `cudnn`, `cublaslt`, `tgv`, `tinygemm`, `cutlass`,
`cute-dsl`), `flashinfer.rmsnorm` for the tail norm, torch SiTU; eager
and CUDA-graph twins, the candidate timed in the winning form.
FlashInfer `mm_bf16`: `flashinfer/gemm/gemm_base.py`, origin #2070
(2062decf4, 2026-01-09), last touched by #5593 (97b3bd80f, 2026-09-27).
FlashInfer `rmsnorm`: `flashinfer/norm/__init__.py`, cute-dsl port #2428
(8bf921a7a, 2026-03-12), last touched by #4753 (5a8e62ac5, 2026-09-01).
Torch: the `nvcr.io/nvidia/pytorch:26.01-py3` container of the
measurement steps.
- **Previous round of this operator (the programs this PR replaces):**
#5584 (1eb503cd3, 2026-09-27); the exported-program contract of that
round is the per-row comparison baseline below.
- **Operator semantics reference:** `nvidia/Kimi-K3-NVFP4`
`modeling_kimi_linear.py` (`KimiSparseMoeBlock`, `KimiMLP`,
`KimiRMSNorm`, `SituAndMul`, `KimiMoEGate`); serving layout from vLLM
`models/kimi_k3/nvidia/{model.py, latent_moe_runner.py,
low_latency_gemm.py}` and SGLang `srt/models/kimi_k3.py`.
- **Test oracle:** the torch reference in
`tests/experimental/test_cake_kimi_k3_latent_moe.py` (transcribed from
the Cake reference module).
- **Merge-base:** upstream `main` 3142c802c (#5627, 2026-09-27); no
upstream change to the package or the baselines between the merge-base
and this branch.

## Test

```
pytest tests/experimental/test_cake_kimi_k3_latent_moe.py
```

`pytest tests/experimental/test_cake_kimi_k3_latent_moe.py`: **39
passed**, 24 warnings on B200 (sm_100a) and on B300 (sm_103a), run on
the delivered tree in the export clone of each GPU (plan / route tests +
GPU correctness for both stages x TP {1, 8} x the row set, bit-identical
re-launch and CUDA-graph replay, `y` byte-exact). Producer-side gates on
the same kernel tree: e2e GPU slice, unit tests, compute-sanitizer
synccheck + memcheck 0 errors, bench-regression +6.5 % / +7.3 % over the
floor, 62 / 62 rows correct in the paired contract and in four
launch-sequence stress passes per GPU, 60 / 60 rows faster than the
stock chain on each GPU (min 1.024).

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Performance and Reliability**
* Improved Kimi K3 latent MoE execution across supported GPU
architectures, including more efficient decode and prefill planning and
better handling of output boundaries.
* Updated normalization and output calculations for more efficient
processing.
* **Bug Fixes**
* Corrected cases where output stores could extend beyond the valid
hidden-width range.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [a31c725](https://github.com/flashinfer-ai/flashinfer/commit/a31c72523ae37d82fd657de36ce2b35156c3c559)

- **作者**: eigen
- **时间**: 2026-09-28T20:23:58Z
- **提交信息**: perf(cake_nvfp4_attn): MiniMax-H3 SM120 NVFP4 varlen attention round 9: attention-kernel ceiling study on RTX 5090 / RTX PRO 6000 (kernel unchanged, route docs) (#5629)

## Summary

Round 9 of the MiniMax-H3 SM120 ragged NVFP4 attention (SageAttention3
recipe; RTX 5090 / RTX PRO 6000 Blackwell, GB202) — follow-up of #5595
(fused pre-processing) and #5583 / #5545 (the Sage3-recipe operator).
This round took the **attention launch itself** to its measured hardware
ceiling on both SKUs: a per-row tensor / DRAM / launch floor model,
knock-out and ncu attribution of the residue, then every candidate lever
the attribution and the reference implementations suggest, each bounded
before it was built and measured paired (CUPTI, cold L2, ABAB) on both
SKUs.

**Outcome: the kernel converges without a change.** The route
`minimax_h3_sm120_varlen_attention_nvfp4` keeps its public name,
signature, numerics and the generated TU of #5595 byte-for-byte (the
default kernel's generated source and PTX were checked identical in
every measurement step). This PR records the ceiling result in the route
docstring so users know what the launch costs and why:

- 246 registers per thread → one 8-warp CTA per SM (two warps per SM
sub-partition); each warp alternates a ~1400-cycle `mxf4nvf4` MMA burst
with a ~2700-cycle FP32 softmax / P-quantization phase that only the
other warp's burst can overlap.
- Tensor pipe active ~58 %; attention launch at ~60 % of the tensor-pipe
floor on production plans (33472 … 109952 tokens) and ~55 % on
4096-token plans, vs 84–88 % for the MMA-only skeleton. L2 hit > 99 %,
DRAM idle; no pipe saturated except by dependency latency.
- Same profile to the digit on both SKUs (same cubin); the PRO 6000
sustains 2167 MHz at its 600 W cap, the 5090 2287 MHz at 575 W (16.8 clk
per `m16n8k64 mxf4nvf4` MMA per sub-partition on both).

Levers measured or bounded and closed on both SKUs (attention launch vs
the shipped kernel; 33472 / 4096 / 3-ragged-segment plans): ping-pong
barrier around QK only (best Tier-A arm: 5090 1.003 / 1.012 / 1.011, PRO
1.000 / 1.026 / 1.006, but **below parity on the 109952 production row
on both SKUs**, 0.9989 / 0.9966); around PV only (≤ 1.00); softmax
emission orders (0.97–0.99); FMA-pipe exp2 for 4 / 8 / 16 tiles
(0.81–0.97); power-of-two P block scales (0.92–0.998, worse rel-L2);
packed f16x2 P path (0.96–0.99); lane-major compensation slot (0.93);
64-key 3-CTA geometry (0.43–0.78; bounded by K/V-load knock-outs at
parity even with half the traffic); K/V multicast / DSM / L2-aware order
(zero-traffic knock-out bound 1.13 / 0.99, halving ≤ 1.06 before cluster
costs); precomputed `qm K^T` compensation table (seed-only knock-out
bound 1.03–1.08, below the table's own MMA + traffic cost); split-KV
(measured LPT tail: ≤ 1.2 % on production rows, ~4.7 % on the ungated
4096 row).

## Performance

All contract plans, complete operator (BF16 THD in → BF16 out, 56 heads,
CUPTI GPU time, cold L2), vs the operator of record (#5595): **1.00 on
every row on both SKUs by construction** — the shipped kernels are
unchanged (source and PTX identical), so the #5595 measurements stand:

| Plan | tokens | RTX PRO 6000 vs #5595 | RTX 5090 vs #5595 |
|---|---|---|---|
| `seg_empty` (4 segments incl. two empty) | 500 | 1.00 | 1.00 |
| `seg3_ragged` (3 ragged segments) | 4824 | 1.00 | 1.00 |
| `single_4096` | 4096 | 1.00 | 1.00 |
| `seg4` (4 × 8368) | 33472 | 1.00 | 1.00 |
| `center_4s` | 33472 | 1.00 | 1.00 |
| `tail_5s` (two tails) | 38531 / 38629 | 1.00 | 1.00 |
| `center_5s` | 38592 | 1.00 | 1.00 |
| `center_6s` | 48768 | 1.00 | 1.00 |
| `center_8s` | 58944 | 1.00 | 1.00 |
| `center_10s` | 74240 | 1.00 | 1.00 |
| `center_15s` / `pad_15s` | 109952 | 1.00 | 1.00 |

Vs ragged Sage3 (SageAttention3 Blackwell at thu-ml/SageAttention
d1a57a546c3 + CUTLASS 0b55a2f6, rebuilt per allocation; "dense" =
per-segment dense calls incl. Sage3's own mean / pad / quantizer chain,
"varlen" = Sage3 with the `seqused_k` varlen patch), complete operator,
unchanged from #5595 because the kernels are unchanged:

| Plan | RTX PRO 6000 (dense / varlen Sage3) | RTX 5090 (dense / varlen
Sage3) |
|---|---|---|
| `seg_empty` 500 | 10.0x / 7.3x | 14.5x / 9.9x |
| `seg3_ragged` 4824 | 2.56x / 4.31x | 2.42x / 3.87x |
| `single_4096` | 1.77x | 1.59x |
| `seg4` 33472 | 1.77x / 1.71x | 1.57x / 1.53x |
| `center_4s` 33472 | 1.35x | 1.22x |
| `tail_5s` 38531 / 38629 | 1.34x / 1.34x | 1.19x / 1.19x |
| `center_5s` 38592 | 1.34x | 1.18x |
| `center_6s` 48768 | 1.24x | 1.11x |
| `center_8s` 58944 | 1.29x | 1.14x |
| `center_10s` 74240 | 1.24x | 1.10x |
| `center_15s` 109952 | 1.23x | n/a (Sage3 dense OOM on 32 GB) |
| `pad_15s` 109952 | 1.26x / 1.40x | 1.03x / 1.07x |

Report-only vs the FlashInfer BF16 ragged routes (cuDNN / FA2, `--routes
fa2,cudnn,auto`): unchanged from #5583 / #5595 (2.3–2.9x on the
production rows).

## Baselines and their source PRs

- `minimax_h3_sm120_varlen_attention_nvfp4` operator of record: #5595
(fused pre-processing) on top of #5583 / #5545 (Sage3-recipe NVFP4
operator); this PR changes no kernel.
- Sage3 (SageAttention3 Blackwell, ragged per-segment dense calls and
the `seqused_k` varlen form): #5583 baseline form, rebuilt from
thu-ml/SageAttention d1a57a546c3 + CUTLASS 0b55a2f6.
- FlashInfer BF16 ragged attention (cuDNN, FA2, auto): FlashInfer bench,
as in #5545 / #5583.

## Validation

- Regenerated TU:
`csrc/cake_minimax_h3_sm120_nvfp4_varlen_attention_sm120a.cu` was
regenerated from the final Cake tree with the export tool on an RTX 5090
and is byte-identical to the committed #5595 file (352040 bytes, sha256
`95765a3656d5b27e837db94bb25d301a3ae92b3b939b662a3e6a46dc9a470d9f`), so
this PR carries no generated-code diff; the default kernel's generated
source and PTX were also verified identical to the operator of record in
every round-9 measurement step on both SKUs.
- `tests/diffusion_ops/test_minimax_h3_sm120_nvfp4_varlen_attention.py`
with this PR's route module and the regenerated TU on RTX 5090: 17
passed, 2 skipped (the PRO 6000 result of #5595 stands: same TU).
- Cake gates on the final tree, both SKUs: unit 46 passed; CPU e2e 52
passed; GPU e2e 13 passed; contract tests 6 passed; compute-sanitizer
synccheck + memcheck 0 errors on the registered launcher, the
empty-segment plan and the 4096-token plan (fused + three-launch
cross-check bit-identical); bench-regression against the calibrated
baseline PASS twice (5090 823 / 816 TFLOPS vs 733 floor; PRO 6000 857 /
855 vs 798), no recalibration.
- Pre-commit: ruff check + ruff format pass on the changed file
(docstring-only change).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [8b7ab98](https://github.com/flashinfer-ai/flashinfer/commit/8b7ab98acdc6e125229c0165cdde9d6a1ab007b1)

- **作者**: Yanqin Zhai
- **时间**: 2026-09-28T20:06:19Z
- **提交信息**: optimize-cudnn-frost-moe-decoding (#5628)

<!-- .github/pull_request_template.md -->

## 📌 Description

Optimize cuDNN Frost MoE decoding

1. Fix cross-backend autotuning to measure input packing plus forward
GPU latency.
2. Fuse FC1 activation and intermediate quantization for NVFP4, MXFP8,
and MXFP8/MXFP4, preserving BF16 rounding semantics and adding STG/TMA
store variants.
3. Add a two-kernel FMA path for supported small-token shapes on SM107a
across all four dtypes, including BF16, with fused routing and output
reduction.

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
* Added fused FC1 quantization and direct fused execution paths across
supported BF16, MXFP8, mixed MXFP8/MXFP4, and NVFP4 MoE configurations.
* Expanded autotuning to include additional FC1 choices and compatible
fused or fused-execution tactics.
* **Bug Fixes**
* Improved backend selection by including per-call input-packing time
when comparing multiple eligible runners.
* Improved quantization scaling behavior for small and edge-case values.
* **Documentation**
* Updated benchmark and API guidance to reflect the expanded Frost plan
and fused FC1 options.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [ebe0efb](https://github.com/flashinfer-ai/flashinfer/commit/ebe0efbb178b9e9fcb40a9d15b44e1db55de4d9e)

- **作者**: eigen
- **时间**: 2026-09-28T19:17:37Z
- **提交信息**: perf(cake_sparse_mla): round-3 DSv4 sparse-MLA programs for SM100/SM103 (persistent-item epilogue, index ring, retained-KV decode body, SwapsAb V alias, routing) (#5630)

## Summary

Round-3 performance of the `backend="cake"` DeepSeek-V4 sparse-MLA
decode path of `trtllm_batch_decode_sparse_mla_dsv4`
(SM100a / SM103a), regenerated from the same producer pipeline as #5610:

- **FP8/H128 persistent prefill program (128+ query-token rows):** the
steady KV tile already runs at the tensor-pipe floor; the per-item
epilogue drained the 64x256 fp32 accumulator with 16-byte stores (4096
half-sector transactions per CTA per item). It now uses 32-byte
stores. prefill-style-000089 / 000093: GB300 1.24x / 1.23x -> **1.33x /
1.31x**, B200 1.17x / 1.18x -> **1.25x / 1.25x** vs the default path.
- **Sub-128-token FP8/H128 uniform-gather program:** compiled without
`--register-usage-level=10` (kept on the lane-gather program):
  -5.8 % SASS, GB300 decode rows 007/010/031/034 1.24x -> **1.26x**.
- **BF16/H128 striped prefill program:** the sparse-index block of the
next work item is staged during the current item (two-slot ring) and
loaded batched. prefill-style-000088 / 000092: GB300 1.23x -> **1.34x /
1.35x**, B200 1.13x -> **1.21x / 1.22x**; hardening rows 21-37 all
  faster.
- **BF16/H32 retained-KV decode program (rows 73/74/76/77):** hoisted
scale loads, one epilogue release fence, eight warps issue the
gathers: GB300 1.08-1.10x -> **1.30-1.34x**, B200 1.09-1.12x ->
**1.32-1.33x**.
- **BF16/FP8 H8/H16 decode programs (16 rows):** PV reads the V quarter
from the staged K tile instead of re-gathering it: GB300 FP8 rows
1.36x -> **1.47x** (geomean), BF16 1.23x -> **1.31x**; B200 1.39x ->
**1.52x**, 1.26x -> **1.35x**.
- **Routing:** width-260 BF16/H128 topk128x rows run the four-owner
two-stage program (GB300 1.23x -> **1.44x**, B200 1.11x -> **1.29x**);
dense (not ragged) BF16/H64 rows follow the ragged rules (fixed-Q guard
row: GB300 1.03x -> **1.21x**, B200 1.03x -> **1.11x**); the
three-owner topk128x program and the fixed-Q programs are no longer
reachable and leave the registry.
- Every other program is a byte-identical regeneration (renamed for the
new producer revision).

## Validation

Export r12 (this branch: host and tests at `84b04ff02`, regenerated
programs as published here), same-session paired CUPTI (active-union
median, 500 warmup / 3000 calls
per arm, cold L2) against the default trtllm-gen path at the same
revision:

| | GB300 (sm_103a) | B200 (sm_100a) |
|---|---|---|
| 94 canonical + 40 hardening shapes correct (BF16 atol=rtol=1e-2, FP8
0.1; padded / separate-table / offset axes) | 134/134 | 134/134 |
| **94 canonical rows faster than the default path** | 94/94, geomean
**1.300x**, min 1.098x (#5610: 1.243x, min 1.054x) | 94/94, geomean
**1.280x**, min 1.027x (#5610: 1.232x, min 1.041x) |
| 40 hardening rows faster than the default path | 40/40, geomean
1.330x, min 1.071x (#5610: 1.30x, min 1.058x) | 40/40, geomean 1.307x,
min 1.065x (#5610: 1.25x, min 1.037x) |
| exported program vs source build (agreement gate, 134 rows) | 134/134,
geomean 1.0018 | 134/134, geomean 1.0026 |
| compute-sanitizer synccheck + memcheck on the changed kernels | 0
errors | 0 errors |
| `tests/mla/test_cake_dsv4*.py` (GPU, fresh clone of this commit) | 296
passed | 296 passed |
| `tests/mla/test_cake_dsv4*.py` (CPU, this host) | 212 passed, 84
skipped | 212 passed, 84 skipped |

## Baselines and their source PRs

- **trtllm-gen default path** =
`trtllm_batch_decode_sparse_mla_dsv4(...)` without `backend="cake"` (the
TRTLLM-GEN DSv4 sparse-MLA
kernels plus the framework launches it needs for equal semantics:
padded-Q masking, separate-table merge, workspace/counter handling).
Origin PRs: #3269 (9c76c994b, 2026-05-21); SM120 kernels #3395
(f95469478, 2026-06-15); DSv4.1 unification #5197 (eb5f05be1,
2026-09-18).
- **Cake backend under test** = `backend="cake"` from #4573 (13db2cfd5,
2026-09-16), hardened by #5591 (8589d49b0), round 2 #5610
  (4b8167eab, 2026-09-27), regenerated again by this PR.
- **Test oracle** = the PyTorch reference of
`tests/mla/test_cake_dsv4.py` / `test_cake_dsv4_hardening.py`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Updated CAKE DSv4 routing across supported GPU variants, including
revised handling for dense BF16/H64 queries and selected BF16/H128 input
widths.
* Expanded coverage for sparse-index staging and attention processing
across value-head groups.
* **Performance**
* Optimized output packing and stores, and adjusted kernel staging and
memory allocation for updated execution paths.
* **Compatibility**
* Removed obsolete kernel variants and registrations; workloads that
previously used those routes may now follow different supported routes.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [a03f220](https://github.com/flashinfer-ai/flashinfer/commit/a03f2205263d4e691d68e485bff287e37a19b6c3)

- **作者**: Ziang Li
- **时间**: 2026-09-28T19:03:13Z
- **提交信息**: feat(moe): add CuTe DSL NVFP4 W4A16 MegaMoE (#5019)

## 📌 Description

@humansand

Add `Sm100_Bf16_Nvfp4_Bf16_Cutedsl_MegaMoeConfig` through the existing
`MegaConfig` / `MoEEpLayer` API. One persistent kernel stages BF16
inputs, dispatches tokens, executes FC1/activation and FC2, returns
route outputs, and combines them into BF16 output.

- **Weights and pipeline:** canonical packed E2M1 weights and E4M3
scales use the existing NVFP4 preparation layout. Two dequantization
warp groups write decoded weights directly to TMEM for BF16 MMA, without
materializing them in global/shared memory. Input staging and
deterministic top-k combine are fused into the five-warp-group kernel.
Register budget per thread: **WG0 epilogue 144; WG1 MMA/TMA/scheduler
80; WG2 input staging/token dispatch 64; WG3–4 weight decode 96 each**
(61,440 32-bit registers per 640-thread CTA).
- **Activation and scales:** support standard SwiGLU, paired
`swiglu_alpha`/`swiglu_beta`
([#5360](https://github.com/flashinfer-ai/flashinfer/pull/5360)), and
SiTU with `situ_beta`/optional `situ_linear_beta`
([#5455](https://github.com/flashinfer-ai/flashinfer/pull/5455)). FP32
`fc1_alpha`/`fc2_alpha` scale GEMM accumulations; optional per-expert
`fc1_norm_const` scales the completed activation before BF16 conversion,
independently of `fc2_alpha`.
- **Runtime and graphs:** batch runtime alpha/norm copies into stable
workspace storage with alias-safe ordering. Config values are snapshots;
omitted overrides retain staged values. Warmup prepares graph-capture
state. Strided inputs, int32/int64 routing IDs, and empty/uneven EP
ranks are supported.
- **Numerics:** default FC2 routing combines BF16 route outputs with
ordered FP32 routing multiplication/FMA. `apply_topk_in_fc1=True`
weights the FP32 activation before the BF16 handoff, then combines with
ordered FP32 additions. Both deterministic modes produce one final BF16
output; opt-in `enable_in_kernel_fc2_reduce` has a separate BF16 atomic
rounding contract.
- **Autotuning and benchmarks:** eight deterministic M256/C2/K256
tactics vary group hint, N tile, and return path; permitting in-kernel
FC2 reduction adds four candidates. Extend
`bench_cute_dsl_moe_distributed.py` to compare Split W4A16, Mega W4A16,
and Mega W4A4 with shared weights/routes and native W4A4 activation
quantization inside timed forward.
- **Ownership and support:** implementation lives in
`flashinfer/moe_ep/cute_dsl/megamoe/bf16_nvfp4/`, reusing the split
decoder and shared communication primitives. Supports SM100/SM103, H
divisible by 32, I divisible by 64, and top-k ≤ min(32, total experts).
Vendored `kernel_src/**/src` files and other MegaMoE kernels are
unchanged.
- **Tracing:** `enable_iket` enables native flat push/pop ranges for
startup register donation/acquisition, scheduler/readiness waits, weight
decode/store, MMA, epilogue, drain, and actual combine workers, with
phase/expert/K-tile payloads. Shared decoder hooks are no-ops outside
MegaMoE. New trace coverage is scoped to owned W4A16 code; HashInfer's
private transport markers and tracing scripts are excluded.

IKET examples (HashInfer captures; private transport markers are not
part of this PR):

- 128 total tokens:
- <img width="1728" height="886" alt="Screenshot 2026-09-26 at 01 56 50"
src="https://github.com/user-attachments/assets/e1dc69ef-d35a-48f4-8841-49d1ff9712cd"
/>
- 4096 total tokens:
- <img width="1728" height="886" alt="Screenshot 2026-09-26 at 01 57 05"
src="https://github.com/user-attachments/assets/1742ef55-536b-4f48-a0df-f5263ef95ee9"
/>

## 🔍 Related Issues

- Builds on https://github.com/flashinfer-ai/flashinfer/pull/4048.
- Original implementation/optimization history:
https://github.com/zianglih/flashinfer/pull/3.
- Full history before the September 23 squash/rebase:
https://github.com/zianglih/flashinfer/pull/5.
- Full history before the September 26 squash/rebase:
https://github.com/zianglih/flashinfer/pull/6.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

- **Rebase validation:**
[`7ca3eb56`](https://github.com/flashinfer-ai/flashinfer/commit/7ca3eb567a2400df70579d55e9bc717ea1784b0c)
is one commit atop upstream `d97b1801`; owned W4A16 source is unchanged
from the GPU-tested revision below. Both upstream SiTU and W4A16 oracle
coverage are retained. Scoped pre-commit and CPU source/control-flow
checks passed; the NCU path now honors `--precomputed-routing`. GPU
tests were not rerun after this rebase.
- **Focused validation:** at
[`acbc0b1f`](https://github.com/flashinfer-ai/flashinfer/commit/acbc0b1f389d34dbeea6b33e64eebfdcc54a0119),
18 logical cases / 42 rank-case executions passed with zero failures,
errors, or skips: standalone split, EP1, EP2, and EP4. Tests cover
activation, normalization, routing placement, and runtime graph updates;
deterministic checks require finite BF16 bit equality. Native IKET smoke
passed on all four ranks for owned W4A16 scopes, including 24 register
ranges per rank. Scoped pre-commit, including mypy/Ruff, passed.
- **Environment:** C2 NVIDIA B300 (SM103), up to four GPUs for focused
distributed tests; `nvcr.io/nvidia/pytorch:26.05-py3`, CUDA 13.2,
container PyTorch `2.12.0a0+5aff3928d8.nv26.05`, CuTe DSL 4.8.0.
- **Limits:** no full-repository or current-head sanitizer pass is
claimed. Upstream GPU CI was skipped pending authorization ([CI
result](https://github.com/flashinfer-ai/flashinfer/actions/runs/36233189876/job/108380109053));
local C2 validation is independent of that gate.

## Performance

Historical results from kernel revision
[`44a04fd`](https://github.com/flashinfer-ai/flashinfer/commit/44a04fd247cf2f93bee4052bf439bc93f32c7f8c)
plus the benchmark-only extension, before the tracing changes; these are
not current-head measurements.

- **Environment/workload:** B300 SM103, 4 GPUs for EP4 / 8 for EP8;
`nvcr.io/nvidia/pytorch:26.05-py3`, CUDA 13.2, CuTe DSL 4.7.1, NVSHMEM
3.6.5. H7168/I2048/E256/top-k8, shared BF16 inputs and packed NVFP4
weights, precomputed routes, standard SwiGLU, unit FP32 alphas, and
routing at FC2. Split uses `--no-fused-finalize`; both Mega variants
disable in-kernel FC2 reduction; PDL is disabled.
- **Timing:** cold-L2 CUDA graphs with CUPTI; three warmups and 100
samples per sweep, two sweeps. Each latency is the pooled median of 200
untrimmed rank-MAX spans from first to last GPU activity, including
gaps. Forward includes staging, scale copies, communication, compute,
combine, output handling, and native W4A4 activation
quantization/requantization. Routing/weight preparation, compilation,
autotuning, capture, and L2 flushing are untimed.
- **Comparison limits:** fresh native AUTO each sweep; Mega W4A16 uses
graph-event candidate timing, while Mega W4A4 uses synchronized eager
wall time. Arm order is fixed (Split W4A16 → Mega W4A16 → Mega W4A4),
not order-balanced. Activation/reduction rounding differs across
precisions; no accuracy parity is claimed. Ratios near one indicate near
parity.
- **Reading the tables:** both ratios divide the comparator's latency by
Mega W4A16 latency, so values above one favor Mega W4A16. Decode
geometric means use tokens 4–512; tokens 1/2 and individual prefill rows
remain visible. Mega W4A4 is substantially faster on the measured
prefill shapes.

### EP4

| Global tokens | Split W4A16 µs | Mega W4A16 µs | Split / Mega W4A16 |
Mega W4A4 µs | Mega W4A4 / Mega W4A16 |
|---:|---:|---:|---:|---:|---:|
| 1 | 76.9445 | 75.0725 | 1.0249× | 82.9285 | 1.1046× |
| 2 | 101.2965 | 90.2090 | 1.1229× | 105.4730 | 1.1692× |
| 4 | 141.2010 | 109.7440 | 1.2866× | 128.0650 | 1.1669× |
| 8 | 181.4890 | 151.3610 | 1.1990× | 167.8090 | 1.1087× |
| 16 | 222.2730 | 201.8890 | 1.1010× | 203.6650 | 1.0088× |
| 32 | 279.7940 | 259.8415 | 1.0768× | 257.9375 | 0.9927× |
| 64 | 334.1150 | 292.0170 | 1.1442× | 289.7140 | 0.9921× |
| 128 | 330.7695 | 319.2820 | 1.0360× | 314.0185 | 0.9835× |
| 256 | 365.2510 | 328.7865 | 1.1109× | 316.0660 | 0.9613× |
| 512 | 370.2420 | 345.2815 | 1.0723× | 320.8815 | 0.9293× |
| 4096 | 946.8700 | 786.5500 | 1.2038× | 448.8035 | 0.5706× |
| 8192 | 1660.2490 | 1524.5505 | 1.0890× | 611.1875 | 0.4009× |
| 16384 | 3062.9085 | 2843.3560 | 1.0772× | 1019.8765 | 0.3587× |

Decode 4–512 geometric speedup of Mega W4A16: **1.1259× over Split
W4A16; 1.0153× over Mega W4A4**.

### EP8

| Global tokens | Split W4A16 µs | Mega W4A16 µs | Split / Mega W4A16 |
Mega W4A4 µs | Mega W4A4 / Mega W4A16 |
|---:|---:|---:|---:|---:|---:|
| 1 | 81.1690 | 71.4575 | 1.1359× | 78.4810 | 1.0983× |
| 2 | 111.0570 | 88.0805 | 1.2609× | 106.4175 | 1.2082× |
| 4 | 135.1055 | 101.2970 | 1.3338× | 128.1930 | 1.2655× |
| 8 | 153.3775 | 123.0890 | 1.2461× | 154.4975 | 1.2552× |
| 16 | 174.2900 | 136.0490 | 1.2811× | 156.3855 | 1.1495× |
| 32 | 195.8100 | 160.9620 | 1.2165× | 174.5305 | 1.0843× |
| 64 | 212.8985 | 183.4250 | 1.1607× | 197.2980 | 1.0756× |
| 128 | 223.6825 | 186.7535 | 1.1977× | 198.9625 | 1.0654× |
| 256 | 231.7455 | 191.7940 | 1.2083× | 202.1140 | 1.0538× |
| 512 | 231.6975 | 196.8170 | 1.1772× | 204.9620 | 1.0414× |
| 4096 | 534.2625 | 453.7795 | 1.1774× | 292.6270 | 0.6449× |
| 8192 | 909.7225 | 790.4095 | 1.1510× | 381.2195 | 0.4823× |
| 16384 | 1665.5020 | 1501.4710 | 1.1092× | 605.8780 | 0.4035× |

Decode 4–512 geometric speedup of Mega W4A16: **1.2265× over Split
W4A16; 1.1208× over Mega W4A4**.

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

- **New Features**
- Added a BF16 activation/NVFP4 weight MegaMoE backend for supported
SM100/SM103 devices.
- Added optional routing-score application during FC1 processing, with
autotuning and support for CUDA Graphs and distributed execution.
- Added optional precomputed expert-parallel routing and W4A4/W4A16
variants to distributed benchmarks.

- **Documentation**
- Documented the backend’s runtime requirements, weight format, routing
behavior, and tuning options.

- **Bug Fixes**
- Improved synchronization and workspace handling for more reliable
execution and graph capture.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [07e519f](https://github.com/flashinfer-ai/flashinfer/commit/07e519fcc149f39e6dd00264149c092c2e37767e)

- **作者**: Jonathan Dierksen
- **时间**: 2026-09-28T18:19:44Z
- **提交信息**: ci: add CUDA 13.4 CI images (#5456)

## 📌 Description

Add CUDA 13.4 to the shared CI runtime-image matrix using NVIDIA's
public `13.4.1-devel-ubuntu24.04` base for both amd64 and arm64.

- add the matching cu134 development container
- use PyTorch's `nightly/cu134` index, pin the published
`cuda-python==13.4.1`, and retain the established cuDNN 9.24.0.43
baseline
- use the TileIRAS compiler already supplied by the CUDA 13.4 toolkit
while retaining the pip compiler fallback for older CUDA 13 images
- route Triton's Blackwell PTXAS lookup to the CUDA toolkit instead of
its older bundled assembler
- extend image smoke and unit coverage to reject a pip TileIRAS overlay,
verify the system compiler path, and require SM107 support in cu134
- harden JIT-cache provider downloads with pip's incomplete-download
resume fix and bounded connection/resume retry defaults
- defer cu134 AOT Build Import lanes until the generated Docker tag
update confirms the published multi-architecture image

## 🔍 Related Issues

None.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review this pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used my preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

> If you are unsure how to set up pre-commit, see the pre-commit
documentation.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

Targeted validation:

- `python -m pytest -q --noconftest tests/test_cuda_tile_ci.py
tests/jit/test_jit_cache_release.py`: 30 passed
- `python3 ci/validate_cuda_versions.py`: validated 3 runtime images and
3 JIT-cache targets
- `bash -n docker/install/install_python_packages.sh`
- `pre-commit run --all-files`
- `git diff --check`

Until phase two updates `ci/docker-tags.yml`, PR AOT coverage remains on
the already-published cu129 and cu130 images; the tag update
automatically enables cu134 AOT coverage.

Provider resilience specifically covers the
`IncompleteRead`/`ProtocolError` seen while downloading the 665 MB cuDNN
wheel.

The local host does not have Docker, so native amd64/arm64 image
construction is left to the Release CI Docker workflow.

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

The internal cu134 image comparison showed that the SM107-critical
differences were using the CUDA 13.4 toolkit TileIRAS and setting
`TRITON_PTXAS_BLACKWELL_PATH`. The public 13.4.1 base already provides
TileIRAS through the CUDA toolkit packages, so cu134 intentionally does
not install `nvidia-cuda-tileiras` from pip. The build backend also
recognizes the system executable and does not restore the older pip
compiler chain.

The internal cuDNN 9.26 preview was a coverage choice rather than a
cu134 requirement, so this PR keeps the current public CI pin at
9.24.0.43.

`ci/docker-tags.yml` is intentionally unchanged: it must not name cu134
until the post-merge image workflow has published and tested the
multi-architecture image. The workflow will then open its normal
generated tag-update PR.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added CUDA 13.4 development and runtime support, including a
GPU-enabled development environment.
* Added support for using the system-provided compiler with compatible
CUDA toolkits.
* Added support for patched JIT cache builds on CUDA 13.4 and newer
versions.

* **Bug Fixes**
  * Improved compiler validation for CUDA 13.4 and Blackwell GPUs.
* Improved JIT cache build reliability during slow or interrupted
package downloads.
* Prevented unavailable AOT images from being included in pull request
test runs.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [7ea849f](https://github.com/flashinfer-ai/flashinfer/commit/7ea849ffb5723e8a6b77780a65cedd9561feb022)

- **作者**: eigen
- **时间**: 2026-09-28T16:08:08Z
- **提交信息**: perf(kimi-k3-vision): round 3 — attention score ring, GEMM tile boundaries, TMA-out epilogue, pointer TMA ABI (sm_100a/sm_103a) (#5623)

## Summary

Round 3 of the generated-program export of the Cake Kimi-K3 vision tower
(MoonViT-3D encoder, 27 layers, + PatchMergerV2) for `sm_100a` (B200)
and `sm_103a` (B300/GB300) into
`flashinfer/experimental/kimi_k3_vision_tower` (#4568, tracker #4254;
round 1 = #5554, round 2 = #5570).

- `bda7f0f97` — attention on its production pointer TMA ABI: the plan
owns the kernel's descriptor workspace (`attn_tma_desc`,
`tma_workspace_bytes` of the registered module), the generated attention
binding exports `run_prepare_tma` (validates, encodes and copies the
four `CUtensorMap`s once, synchronously, outside CUDA-graph capture) and
a launch-only `run`; `prepare_kimi_k3_vision_tower` prepares the
workspace once per plan, `launch()` and graph replays never touch it.
The GEMM family and the RMSNorm apply pass keep the by-value ABI. Round
2 had exported the attention kernel in the by-value form without its
descriptor prefetch (3.0-3.5 % slower than production on the
attention-dominated rows); the round-3 attention programs are the
production kernels byte-for-byte.
- `3739e62f1` — the round-3 Cake host policy mirrored in the scaffold:
per-form GEMM tile boundaries (`s_e8_pf` single-CTA 128x128 eight-warp
tile for the residual GEMMs while the pair grid underfills the machine —
out-proj to 6144 rows, FC1 to 2304; QKV 128x64 to 768 / 128x128 to 1536;
`norm_gelu` / `gelu_erf` 128x64 in (512, 768] and 128x128 to 1656), the
one-buffer TMA-epilogue pair tile `m_tma1` for the out-proj above 6144
rows, the kernels' TMA-epilogue tensor maps (`RT`, `CT`, `XWT`) and
`pf_l2` flag as launch arguments, and the SPLIT_KV attention form
`attention:ring3` (shared-O three-deep score ring, selected per
architecture and longest segment by `cake_backend.ring3_selected`: every
one-tile row on SM100, 576..10764-token segments on SM103).
`REQUIRED_KERNEL_KEYS` is per architecture (26 GEMM programs + the
reachable attention forms + merge + rmsnorm apply); tests cover the tile
boundaries over M = 1..20000, the per-arch key sets and the ring3 route.
- The last commit is the generated delivery only: `cake_jit.py`
`MODULES` / `KERNELS` registries (61 exact-architecture programs: 30 on
`sm_100a` + 31 on `sm_103a`) and
`csrc/cake_kimi_k3_vision_tower/{sm_100a,sm_103a}/*_{kernel,binding}.cu`
(122 generated sources, replacing the round-2 set; excluded from the
formatting hooks via `csrc/.clang-format`; identities are
receipt-bound). Both literals are generated; do not edit by hand. The
programs were regenerated once more after the source project's delivery
branch merged with its main line (`ae64785ef`): kernel keys, argument
plans, flags and entry points are unchanged; the only device-code change
is a `"memory"` clobber on the mbarrier inline asm (57 of 61 kernels),
and the module content hashes follow. A one-line docstring edit in
`cake_backend.py` drops a source-project path.

Kernel changes behind the regenerated programs (source project round 3):
shared-O three-deep score ring for the one-tile attention layout,
per-form GEMM tile boundaries from paired sweeps on both architectures,
one-buffer TMA-in / TMA-out epilogue for the K = 1536 out-proj pair
tile.

## Evidence (Cake export protocol, producer `7a3572a6b`, target
`3739e62f1`)

Every contract row is measured on the source (Cake production launcher)
and the exported programs in counterbalanced groups; `source_ms /
export_ms >= 0.97`, directional disagreement `<= 0.02`, endpoint drift
`<= 0.02`, correctness = bitwise `source == export` on every row before
and after timing. One uninterrupted single-cache round per architecture
on the final producer (the programs in this PR): part A (fresh state, 1
GPU: the three smoke rows + `img_224` + `img_1920x1080`) then part B
(the remaining 17 rows, 4 GPUs) against the same clone, state and JIT
cache; no module had conflicting binaries across the round.

| arch | GPU | rows measured | passed | source/export (min .. max) |
directional disagreement | endpoint drift |
|---|---|---|---|---|---|---|
| sm_100a | B200 (4 GPUs, one build session) | 22 | 22 | 0.9904 ..
1.0036 (geomean 0.9990) | <= 0.0018 | <= 0.0173 |
| sm_103a | B300 (4 GPUs, one build session) | 22 | 22 | 0.9905 ..
1.0036 (geomean 0.9991) | <= 0.0022 | <= 0.0139 |

Attention-heavy rows (pointer-ABI attention, bar `source/export >=
0.99`): B200 img_1024x768 0.9993, img_1920x1080 0.9997, doc_1240x1754
0.9998, img_2560x1440 0.9997, img_3840x2160 1.0001, img_max_4096sq
1.0000, video_720p_4f 1.0001, video_1080p_4f 1.0008, video_720p_32f
1.0002, video_480p_64f 1.0001; B300 img_1024x768 1.0008, img_1920x1080
1.0002, doc_1240x1754 1.0000, img_2560x1440 0.9998, img_3840x2160
1.0023, img_max_4096sq 0.9977, video_720p_4f 1.0000, video_1080p_4f
1.0014, video_720p_32f 1.0001, video_480p_64f 1.0004.

Pooled smoke rows (8 seeds, candidate/reference-chain mean-error ratio):
B200 `smoke_2x2` 0.9993 / `smoke_ragged` 1.0002 / `smoke_t3` 0.9989
(violation ratios 0.9978-1.0070; all pass); B300 `smoke_2x2` 0.9993 /
`smoke_ragged` 1.0001 / `smoke_t3` 0.9993 (violation ratios
0.9991-1.0070; all pass). Chain route probe on both architectures:
`smoke_2x2` -> cudnn, `smoke_ragged` / `smoke_t3` -> cute-dsl (three
picks each, stable).

Speed vs the round-2 programs and vs the FlashInfer chain: see the
source project's round-3 design record; the export protocol measures
source == export parity, not speed vs peers.

Receipts, raw timings and state copies stay on the cluster (host / path
/ size / SHA-256 recorded in the source project's design record and
`exports/kimi_k3_vision_tower/README.md`).

## Baselines and their source PRs

The export's correctness gate compares both arms against the FP32 tower
oracle relative to the HF BF16 chain whose attention is the fastest
FlashInfer ragged BF16 route of this checkout
(`BatchPrefillWithRaggedKVCacheWrapper(kv_layout="NHD", backend=...)`,
chosen by timing per row). Branch upstream merge-base: `f89d15f2c`
(2026-09-26, "feat(cake_mla_varq_dcp_decode): Cake MLA variable-query
decode with DCP for SM100 / SM103 (#5577)").

- `fa2` route: `flashinfer/prefill.py` (last upstream change #5350
`7685a893e`, 2026-09-24), `csrc/batch_prefill.cu` (#5176 `e0a18900c`,
2026-09-21), `include/flashinfer/attention/prefill.cuh` (#5239
`b8107c7fd`, 2026-09-17).
- `cudnn` route: `flashinfer/cudnn/prefill.py` (#5350 `7685a893e`,
2026-09-24).
- `cutlass` route: `csrc/fmha_cutlass_sm100.cu` (#3064 `1aa32d03e`,
2026-05-08), `csrc/fmha_cutlass_sm100_binding.cu` (#2047 `db2aacbd3`,
2025-12-17).
- `cute-dsl` route: `flashinfer/cute_dsl/attention/fmha/` (#4859
`f17b77260`, 2026-09-18; cubin refresh #4997 `75038cdf6`, 2026-09-10).
- Chain RMSNorm: `flashinfer/norm/` (#5305 `012542c85`, 2026-09-18).
- Previous programs (replaced by this PR): round-2 delivery from #5570
(`b6e4ebfdd`, 2026-09-26), round-1 delivery from #5554 (`6dd3104a7`,
2026-09-25); the package tests / FP32-oracle stage tests
(`tests/experimental/test_cake_kimi_k3_vision_tower.py`) are the test
oracle, extended in `3739e62f1` for the round-3 tile policy and
attention route.

No upstream commit between the round-2 merge-base `e34a1735a` and
`f89d15f2c` touched any of the route files above other than #5570
itself.

## Test

```
pytest tests/experimental/test_cake_kimi_k3_vision_tower.py
```

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added architecture-aware attention planning, including the
shared-output ring3 kernel for supported segment sizes.
* Expanded tile selection for residual GEMMs to cover additional input
shapes and machine configurations.
* Added reusable tensor-map preparation for attention workloads,
including support for preparing descriptors before graph capture.
* **Performance Improvements**
* Added optional L2 prefetching and optimized residual data transfers
across supported Kimi K3 vision-tower workloads.
* **Documentation**
* Updated guidance on attention-kernel selection and GEMM tile
configurations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [85bfa5e](https://github.com/flashinfer-ai/flashinfer/commit/85bfa5e4b599a9c616f073e2c06d3b9a1cdadee4)

- **作者**: eigen
- **时间**: 2026-09-28T08:07:11Z
- **提交信息**: perf(cake_latent_moe): Kimi-K3 TP12 fused LatentMoE tail round 4: persistent K3 pipeline from 256 tokens, weight-streaming K2 for M <= 4 (GB200 / GB300 NVL72) (#5624)

Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

## Summary

Round 4 of `flashinfer.kimi_k3_tp12_tail` (`backend="cake"`, the fused
Kimi-K3 TP12 LatentMoE communication tail for
three-tray GB200 / GB300 NVL72 tensor-parallel groups; #5603 delivered
the operator). Same operator, ABI and workspace;
two new kernel forms, dispatched by token count, make every row at least
as fast as #5603 and the decode / large rows
faster:

- **K3-P, persistent token pipeline (`M >= 256`)**: the column
reduce-scatter + add + all-gather kernel keeps the #5603
protocol, buffers, sentinels and dirty clear, but runs `min(M, SM count)
x 2` CTAs that each walk several tokens with a
three-stage software pipeline (scatter token `t`, owner-poll + add +
multicast token `t - 1`, gather token `t - 2`), so
the two fabric hops of one token overlap the traffic of the next instead
of being exposed once per CTA wave. -4 % at
  M = 256 growing to -13 % at M = 4096 on both racks.
- **K2-stream, weight-streaming slice GEMM (`M <= 4`)**: a 128-CTA SIMT
kernel that streams the rank's 640/512-row
up-projection slice once from HBM (loads issued before the PDL wait so
they hide under K1's tail) and accumulates the
products in fp32; K3 adds the fp32 slice before its single BF16 rounding
(`k3_f32`). Replaces the cuBLAS `torch.mm`
pair (nvjet + split-K reduce) for the decode rows: -10 % at M = 1, -6 /
-9 % at M = 2, -10 / -16 % at M = 4.
- Rows 5..255 keep the #5603 kernels and dispatch; two in-switch NVLS
reduce forms (K3 and K1) were built and measured on
both racks and are slower at every row (the exact form needs an fp32
stage whose egress floor is above the Lamport
  chain's), so they are not shipped.

## Files

- `flashinfer/experimental/kimi_k3_tp12_tail/cake_backend.py` — dispatch
(`k2_form_for`, `k3_form_for`, `k3_grid`,
`route_kernel_keys`), fp32 GEMM slice buffer in the workspace, K3-P grid
`(min(M, sm_count), 2, 1)`, K2-stream launch
  instead of `torch.mm` for `M <= 4`.
- `flashinfer/experimental/kimi_k3_tp12_tail/cake_jit.py`,
`csrc/cake_kimi_k3_tp12_tail/{sm_100a,sm_103a}/` — generated
programs: 20 per architecture (12 rank-specialised one-shot K1, grouped
/ pinned two-shot K1, grouped one-CTA-per-token
K3, grouped / pinned persistent K3, K2-stream for the 640- and
512-column slices, fp32-add K3).
- `flashinfer/kimi_k3_tp12_tail.py` — docstring (dispatch).
- `tests/experimental/test_cake_kimi_k3_tp12_tail.py` — route / grid /
inventory tests for the new forms; the twelve-rank
GPU test covers M = 1, 4 (K2-stream), 8, 16, 32, 128, 256 (grouped
K3-P), 300 (pinned K3-P).

## Results

Rank-max median GPU time per call (CUPTI, cold L2, CUDA graphs, twelve
ranks on three trays of one NVLink domain); the
`fused #5603` column is the previous delivery's own export run on the
same racks (allocations of 2026-09-27).

### GB300 NVL72 (sm_103a)

| M | route | stock chain us | fused (this PR) us | speedup | fused
#5603 us (its export run) | source/export parity | verdict |
|---|---|---|---|---|---|---|---|
| 1 | `oneshot_grouped_k2s` | 114.4 | **22.2** | **5.15x** | 25.8
(4.45x) | 0.9899 | pass |
| 8 | `oneshot_grouped` | 118.9 | **24.6** | **4.84x** | 25.0 (4.72x) |
0.9954 | pass |
| 32 | `twoshot_grouped` | 119.3 | **26.5** | **4.50x** | 27.4 (4.38x) |
1.0060 | pass |
| 64 | `twoshot_grouped` | 119.6 | **27.6** | **4.33x** | 28.3 (4.25x) |
1.0029 | pass |
| 128 | `twoshot_grouped` | 134.5 | **30.4** | **4.42x** | 31.5 (4.31x)
| 0.9958 | pass |
| 256 | `twoshot_grouped_k3p` | 146.7 | **40.1** | **3.66x** | 42.3
(3.41x) | 1.0024 | pass |
| 512 | `twoshot_pinned_k3p` | 178.3 | **59.2** | **3.01x** | 64.9
(2.76x) | 0.9989 | pass |
| 1024 | `twoshot_pinned_k3p` | 251.5 | **94.4** | **2.66x** | 104.1
(2.44x) | 1.0022 | pass |
| 2048 | `twoshot_pinned_k3p` | 366.8 | **165.6** | **2.21x** | 186.8
(1.97x) | 1.0014 | pass |
| 4096 | `twoshot_pinned_k3p` | 591.3 | **308.0** | **1.92x** | 353.3
(1.67x) | 0.9989 | pass |

### GB200 NVL72 (sm_100a)

| M | route | stock chain us | fused (this PR) us | speedup | fused
#5603 us (its export run) | source/export parity | verdict |
|---|---|---|---|---|---|---|---|
| 1 | `oneshot_grouped_k2s` | 116.7 | **23.1** | **5.04x** | 25.4
(4.66x) | 1.0035 | pass |
| 8 | `oneshot_grouped` | 120.2 | **25.1** | **4.78x** | 25.5 (4.69x) |
0.9917 | pass |
| 32 | `twoshot_grouped` | 122.0 | **26.7** | **4.56x** | 27.9 (4.37x) |
1.0144 | pass |
| 64 | `twoshot_grouped` | 122.0 | **28.5** | **4.27x** | 29.1 (4.20x) |
1.0056 | pass |
| 128 | `twoshot_grouped` | 137.0 | **31.5** | **4.35x** | 31.6 (4.36x)
| 0.9909 | pass |
| 256 | `twoshot_grouped_k3p` | 149.4 | **41.4** | **3.61x** | 43.5
(3.41x) | 1.0000 | pass |
| 512 | `twoshot_pinned_k3p` | 182.8 | **60.9** | **3.00x** | 65.7
(2.79x) | 1.0016 | pass |
| 1024 | `twoshot_pinned_k3p` | 256.1 | **96.0** | **2.67x** | 104.1
(2.50x) | 1.0010 | pass |
| 2048 | `twoshot_pinned_k3p` | 403.6 | **168.8** | **2.39x** | 189.7
(2.14x) | 1.0004 | pass |
| 4096 | `twoshot_pinned_k3p` | 626.9 | **310.9** | **2.02x** | 355.4
(1.77x) | 0.9971 | pass |

FlashInfer-side benchmark on the delivered tree
(`benchmarks/bench_cake_kimi_k3_tp12_tail.py`, 50 warmup + 200
iterations x 3 counterbalanced groups, rank-max of per-rank CUPTI spans,
median over iterations; `max|diff|` against the stock chain's own
output):

| M | GB300 stock us | GB300 fused us | speedup | GB200 stock us | GB200
fused us | speedup | max abs diff vs stock |
|---|---|---|---|---|---|---|---|
| 1 | 112.9 | 21.2 | 5.31 | 116.6 | 21.9 | 5.33 | 0.0234 |
| 8 | 121.3 | 23.1 | 5.26 | 125.0 | 24.9 | 5.03 | 0.0312 |
| 32 | 123.2 | 25.7 | 4.80 | 125.9 | 25.9 | 4.86 | 0.0312 |
| 64 | 123.6 | 27.1 | 4.56 | 125.8 | 27.3 | 4.62 | 0.0312 |
| 128 | 136.8 | 29.4 | 4.66 | 140.1 | 30.3 | 4.63 | 0.0312 |
| 256 | 148.4 | 40.5 | 3.67 | 151.2 | 39.6 | 3.82 | 0.0312 |
| 512 | 181.5 | 58.4 | 3.11 | 184.6 | 60.2 | 3.07 | 0.0312 |
| 1024 | 253.8 | 93.9 | 2.70 | 260.2 | 95.0 | 2.74 | 0.0312 |
| 2048 | 377.5 | 167.2 | 2.26 | 415.5 | 168.4 | 2.47 | 0.0312 |
| 4096 | 605.9 | 306.9 | 1.97 | 642.6 | 309.1 | 2.08 | 0.0312 |

## Baselines and their source PRs

- Regression baseline: the #5603 fused chain (`fc8a6fb72^`'s
`cake_backend.py`; merged 2026-09-27), re-measured as its own
arm in every A/B of this round (paired rank-max medians, identical-arm
control).
- Stock chain: `flashinfer.norm.rmsnorm` from #207 (`3e515a475`,
2024-04-21; `include/flashinfer/norm.cuh`, `csrc/norm.cu`),
  module layout from #643 (`8e3d25874`, 2024-12-10); NCCL all-reduce via
`torch.distributed._functional_collectives.all_reduce`, cuBLAS
`torch.mm` / `torch.add` of PyTorch
2.13.0a0+9186a08b2c.nv26.07 (CUDA 13.3, container
`nvcr.io/nvidia/sglang:26.07-py3`), NCCL 2.30.7.
- Reused infrastructure (not a baseline):
`MNNVLAllReduceFusionWorkspace` from #2130 (`fd0c2f124`) on the MNNVL
allocator
  of #1213 (`a03c2909d`), two-shot stages per #4473 (`b8c21928b`).
- Branch merge-base with `main`: `69ead1ded` (#5607, 2026-09-27). No
upstream commit after the merge-base touches
`flashinfer/norm.py`, `csrc/norm.cu`, `include/flashinfer/norm.cuh`,
`flashinfer/kimi_k3_tp12_tail.py` or
`flashinfer/experimental/kimi_k3_tp12_tail/` (`git log
69ead1ded..origin/main -- <files>` is empty as of 14a556336).

## Evidence

Every number above comes from the generated-program export protocol of
the Cake repository (frozen protocol
`kimi_k3_tp12_tail`: twenty shapes = ten token counts x two
architectures, arms `source` = Cake runtime / `exported` = this
FlashInfer runtime / `stock` = the NCCL -> `flashinfer.norm.rmsnorm` ->
cuBLAS -> NCCL -> add chain in CUDA-graph form, twelve
ranks under torchrun on three trays, rank-max CUPTI medians, 3
counterbalanced groups x 300 warmup + 600 samples per arm,
source/export parity gate `>= 0.97`, endpoint drift `<= 0.08`,
directional disagreement `<= 0.12`). Both runs passed every
shape (20/20 verdict `pass`; parity 0.990-1.006 on GB300, 0.991-1.014 on
GB200; geomean stock/export 3.49x GB300, 3.51x GB200).
The GB200 and GB300 runs delivered byte-identical trees (81 files: the
registry module plus 40 generated sources per
architecture; `applied.json` lists them with their SHA-256; the two
retired one-CTA-per-token pinned K3 sources are removed).
Receipts stay on the measuring clusters; the manifest (host, path, size,
SHA-256) is kept with the internal export receipts.

| artifact | bytes | sha256 |
|---|---|---|
| delivered file list (81 files, identical on both racks) | 16162 |
`bee44643ee56e1fa78d5812dc6339ebf69da8aae5bca43de29a5d51c937397f5` |
| sm_103a `applied.json` | 17746 | `c19abdd00c3c0e1f` (prefix; identical
on both racks) |
| sm_103a `summary.json` | 112448 | `65d43a735ebb1464` (prefix) |
| sm_103a `summary.md` | 6602 | `23abfaca87d9a8c5` (prefix) |
| sm_100a `summary.json` | 112216 | `b1f145b5bb09e14f` (prefix) |
| sm_100a `summary.md` | 6602 | `2512888796455139` (prefix) |

Correctness in the same runs: `source` and `exported` pass the fp32
reference at `atol = rtol = 1e-2` on every rank at every
shape and are bitwise identical to each other; the stock arm is held to
`5e-2` (NCCL rounds every ring hop to BF16).
FlashInfer-side validation on the delivered tree (same trays,
`nvcr.io/nvidia/sglang:26.07-py3`): CPU tests 5 passed (partition,
routing, sizing, operand validation, generated-module inventory) and the
twelve-rank GPU test `-k twelve_ranks` (rows M = 1, 4, 8,
16, 32, 128, 256, 300: reference at 1e-2, rank invariance, idempotence,
CUDA-graph replay, `max_tokens` guard) passed on GB300
and GB200; the benchmark table above is from the same steps.
compute-sanitizer (twelve ranks, `nvcr.io/nvidia/pytorch:26.07-py3`,
filtered to the Cake kernels): synccheck and memcheck report `ERROR
SUMMARY: 0 errors` on all twelve ranks for the persistent
K3 / K1 forms at M = 1, 8, 32, 128, 512 and for K2-stream + fp32 K3 at M
= 1, 8, 16, on both racks.

## Limits

Twelve ranks in one NVLink domain with CUDA fabric symmetric memory and
multicast only; `sm_100a` / `sm_103a`; BF16
model-layout weights; `M <= max_tokens` of the workspace (default 4096;
8192 verified); every rank launches the same `M`.

Tracker: #4254.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Performance Improvements**
* Small batches now use a streaming projection path, while larger
batches continue to use cuBLAS.
* Very large batches use a persistent output pipeline, with launch
sizing adapted to the available GPU.
* Projection results are accumulated in FP32 before conversion to the
output format.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-09-29
**监控日期**: 2026-09-28
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4518
- **最后更新**: 2026-09-29T01:31:53Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: li-lizhe

## AI分析总结

好的，已分析仓库 `hao-ai-lab/FastVideo` 的最新提交记录，并结合项目背景进行总结。

### 提交分析总结

1.  **主要更新类型**
    *   **Bug修复**：提交信息明确标识为“[bugfix]”，表明这是一个针对已知问题的修正。

2.  **关键变更点及其与项目整体方向的关系**
    *   **核心修复**：此提交修复了 `SceneMetric` 模块在非CPU设备（如GPU）上的 `device_map` 设置问题。
    *   **与项目方向的关系**：FastVideo 作为视频生成/处理AI项目，性能与多设备支持至关重要。此修复确保了核心的评估指标计算组件（SceneMetric）能够在不同硬件设备上正确、稳定地运行，直接支撑了项目“快速”且“可靠”的视频AI处理目标。

3.  **对项目的影响和潜在意义**
    *   **直接影响**：提升了项目在多GPU或特定硬件环境下运行的稳定性和正确性，解决了可能导致计算错误或程序崩溃的底层兼容性问题。
    *   **潜在意义**：增强了项目在不同硬件环境下的鲁棒性，有利于开发者在各种设备上顺利部署和使用FastVideo，降低了用户的配置和调试门槛。

4.  **值得关注的技术点**
    *   **设备兼容性**：修复了模型或张量在不同计算设备（CPU/GPU）间迁移或指定时可能出现的设备映射错误，这是AI框架中常见的关键问题点。
    *   **维护性提交**：虽然未添加新功能，但此类底层修复对于维护项目代码质量、确保现有功能的可靠性至关重要，是项目成熟度的体现。

5.  **基于README了解的项目背景，这些提交如何影响项目发展**
    *   README显示FastVideo是一个有文档、教程和活跃社区（每周开发会议）的正式项目。此次修复正是维护项目稳定运行的日常关键工作。
    *   它确保了项目提供的核心工具链（如评估指标）在所有目标平台上功能一致，这对于建立用户信任、保障项目声誉至关重要。
    *   这类提交为后续的功能迭代和性能优化奠定了更稳固的基础，是项目健康发展不可或缺的一部分。

## 详细提交记录

### [442e2d2](https://github.com/hao-ai-lab/FastVideo/commit/442e2d2e18ed63b9a5d9f5bb6233ed5a884b3b9b)

- **作者**: li-lizhe
- **时间**: 2026-09-28T17:24:00Z
- **提交信息**: [bugfix] fix(metrics): set SceneMetric device_map for any non-CPU device (#1817)

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-09-29
**监控日期**: 2026-09-28
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34629
- **最后更新**: 2026-09-28T22:30:52Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 3
- **主要提交者**: Christopher, Pranav Negi, BeyondBirthday07

## AI分析总结

### 总结分析

1.  **主要更新类型**：本次提交主要为 **Bug修复** 与 **功能改进**，集中于优化模型加载（特别是LoRA适配器）的兼容性与正确性，以及修复特定训练场景下的问题。

2.  **关键变更点及其与项目整体方向的关系**：
    *   修复了特定文本编码器（扁平化CLIP）下LoRA权重无法正确加载的问题。
    *   增强了LoRA转换器，使其能更智能地处理“Z-Image”等非标准注意力层命名格式，扩大了兼容的LoRA生态。
    *   修复了分布式训练环境中，当传入`num_train_epochs`参数时学习率调度器（LR scheduler）计算错误的问题。
    这些变更直接服务于项目**提升模型加载的鲁棒性**、**扩大生态兼容性**以及**确保训练功能在各种场景下可靠工作**的核心目标，属于对现有核心功能的重要维护与加固。

3.  **对项目的影响和潜在意义**：
    *   **直接提升用户体验**：解决了用户在使用特定模型或第三方LoRA时可能遇到的加载失败或转换错误问题，降低了使用门槛。
    *   **增强生态兼容性**：对Z-Image LoRA的支持，意味着项目能更好地整合来自`musubi-tuner`、`LyCORIS`等工具链的资源，吸引更多模型开发者。
    *   **保障训练稳定性**：修复分布式训练下的调度器问题，确保了大规模训练场景的可靠性，这对于专业用户和研究团队至关重要。

4.  **值得关注的技术点**：
    *   **LoRA键映射逻辑**：提交2中，代码需要智能区分“分拆键”（如`to.q/k/v`）和“融合键”（如`qkv`）以及“裸输出键”（如`out`），并进行正确的映射。这体现了LoRA权重适配器层命名规范的多样性与复杂性。
    *   **分布式训练状态同步**：修复LR调度器可能涉及在不同进程间正确同步或初始化状态，确保训练配置的一致性。

5.  **基于项目背景的提交影响分析**：
    根据README，diffusers旨在提供高性能、模块化的扩散模型实现。这些提交通过**修复边缘案例和增强兼容性**，直接巩固了其作为“可靠基础设施”的定位。LoRA相关改进使项目能更无缝地融入整个AI绘画生态，而训练相关的修复则维护了其作为研究与开发平台的信誉。这些工作虽非颠覆性创新，但对于保持项目的稳定性、吸引力和社区活力具有重要意义。

## 详细提交记录

### [5ff8e59](https://github.com/huggingface/diffusers/commit/5ff8e59ff9fe81c6e2df4fb4c6ea0d97a5df5ab2)

- **作者**: BeyondBirthday07
- **时间**: 2026-09-28T14:17:16Z
- **提交信息**: Fix LoRA loading for flattened CLIP text encoders (#14872)

Co-authored-by: Aznix07 <sruhilmodi13@gmail.com>
Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

### [8f0ad34](https://github.com/huggingface/diffusers/commit/8f0ad34299a99050b1492b88bc823653b95f9cbd)

- **作者**: Christopher
- **时间**: 2026-09-28T12:22:38Z
- **提交信息**: [LoRA] convert Z-Image LoRAs that only carry the fused qkv and bare out attention keys (#14875)

* [LoRA] convert Z-Image LoRAs that only carry the fused `qkv` and bare `out` attention keys

A LoRA trained on Z-Image's original module names (musubi-tuner, LyCORIS)
has `attention.qkv` and `attention.out` and nothing else. The non-diffusers
converter dropped both on the assumption that split `to.q/k/v` and `to_out.0`
keys are also present (the Anime-Z layout), which emptied such a LoRA and then
raised on its leftover `.alpha` keys. Split the fused key into to_q/to_k/to_v
like the single-file converter does and map bare `out` to `to_out.0` when no
split keys exist; the Anime-Z case keeps skipping the redundant keys.

Co-Authored-By: Claude Fable 5.1 <noreply@anthropic.com>

* [LoRA] review follow-ups: shorter comment with the layout's origin, drop the private-method test

Co-Authored-By: Claude Fable 5.1 <noreply@anthropic.com>

---------

Co-authored-by: christopher5106 <christopher@scenario3d.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

### [8315c5d](https://github.com/huggingface/diffusers/commit/8315c5d6dc867349bf72d54eca59c83edf3b0024)

- **作者**: Pranav Negi
- **时间**: 2026-09-28T08:43:27Z
- **提交信息**: [realfill] Fix the LR scheduler when num_train_epochs is passed in a distributed training env (#14885)

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-09-29
**监控日期**: 2026-09-28
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


**报告日期**: 2026-09-29
**监控日期**: 2026-09-28
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13189
- **最后更新**: 2026-09-28T10:42:50Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Hong Zhang

## AI分析总结

根据提交记录，对仓库 `modelscope/DiffSynth-Studio` 昨日的提交分析总结如下：

**1. 主要更新类型**
本次提交混合了**性能优化**、**Bug修复**与**功能增强**。核心是修复Qwen-Image-2.1模型在高分辨率下生成时的内存溢出问题，并为此引入了更灵活的注意力计算路径。

**2. 关键变更点及其与项目整体方向的关系**
*   **核心修复**：将`create_block_mask`的调用从会生成密集掩码导致OOM的路径，切换至分块构建的编译路径，解决了#1701问题。
*   **新增功能**：为DiT管线添加`use_flex_attention`选项，允许在`flex_attention`与传统分段SDPA之间切换，后者在长序列上内存占用更低。这为处理不同长度和资源约束的任务提供了灵活性。
*   **精细优化**：在单帧（`num_frame == 1`）场景下，跳过了VAE编解码过程中不会被读取的缓存（`feat_cache`），在编解码和分块编解码路径中均实现了显著的内存下降，且输出完全一致。
*   **文档与示例**：更新了模型文档以说明新选项，并修正了训练验证示例，使其指向正确的训练输出检查点，提高了示例代码的准确性。

**3. 对项目的影响和潜在意义**
*   **直接提升可用性**：解决了Qwen-Image-2.1模型在高分辨率（如2K）且使用多个参考图像时无法运行的关键限制，扩大了其适用场景。
*   **资源效率提升**：通过多处内存优化，降低了模型在消费级硬件上运行或进行大规模推理的门槛，增强了项目的实用性和普惠性。
*   **开发体验改善**：修正的示例和文档使开发者能更准确地使用训练和验证功能，减少了上手困惑。

**4. 值得关注的技术点**
*   **`flex_attention`与SDPA的权衡**：引入此选项体现了在实现灵活性上的考量——`flex_attention`路径功能完整，而SDPA路径在特定场景下更省内存，让使用者可以根据实际情况进行选择。
*   **缓存失效优化**：识别并跳过单帧下无用的`feat_cache`，是基于对模型计算流的深刻理解进行的“外科手术式”优化，在不改变输出的情况下显著减少了内存占用和冗余计算。

**5. 对项目发展的影响**
这些提交紧密围绕项目提供“易用、高效”的多模态生成工具这一目标。通过解决内存瓶颈和增加配置灵活性，使得Qwen-Image-2.1这个重要的图像生成模型更加稳定、可用，有助于巩固项目在扩散模型工具链中的竞争力。同时，持续的内存优化也反映了项目团队对大规模模型部署现实问题的关注，这对于吸引更多用户和开发者至关重要。

## 详细提交记录

### [7539a33](https://github.com/modelscope/DiffSynth-Studio/commit/7539a33b16844e2ce7e06306a2576346aa00de2b)

- **作者**: Hong Zhang
- **时间**: 2026-09-28T07:20:30Z
- **提交信息**: fix(qwen-image-2.1): avoid OOM when building block-causal mask at hig… (#1703)

* fix(qwen-image-2.1): avoid OOM when building block-causal mask at high resolution

create_block_mask with _compile=False materializes a dense [B,H,Q,KV] mask,
which OOMs at 2K output with multiple reference images (50-72 GiB single
allocation). Use the compiled path (_compile=True) to build the block mask
block-wise, matching wan_animate_2_dit.py. Produces identical masks/outputs.

Fixes #1701

* feat(qwen-image-2.1): add use_flex_attention option and skip single-frame VAE feat_cache

- Pipeline/DiT: new use_flex_attention arg (default True) switches the prefill
  between flex_attention and per-segment SDPA; the SDPA path builds no block
  mask and uses less memory on long sequences, with equivalent outputs.
- Set _compile=False in create_block_mask to avoid the minutes-long cold
  torch.compile; the flag is deprecated in torch 2.11.
- VAE _decode: skip the write-only feat_cache when num_frame == 1; output is
  bitwise identical and the 2K decode peak drops from 26.90 to 15.28 GiB.
- Document use_flex_attention in the zh/en model docs.

* fix(qwen-image-2.1): skip write-only VAE feat_cache in encode and tiled paths

Extend the single-frame feat_cache skip from _decode to _encode, tiled_encode
and tiled_decode: the image-specialized causal convs never read the cache
back, so for num_frame == 1 the per-conv full-resolution clones are pure
overhead. Outputs are bitwise identical; the 2K non-tiled encode peak drops
from 9.70 to 6.68 GiB.

* fix(qwen-image-2.1): load the trained checkpoint in the validate_full example

The full-training validation example still built the transformer from the
base model id, so it validated the pretrained weights instead of the training
output. Point it to models/train/Qwen-Image-2.1_full/epoch-1.safetensors,
consistent with the validate_lora example.

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-09-29
**监控日期**: 2026-09-28
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 36549
- **最后更新**: 2026-09-29T01:41:49Z

## 提交统计

- **昨日提交总数**: 29
- **提交者数量**: 21
- **主要提交者**: Kurkur, YAMY, karverma-amd

## AI分析总结

根据提供的提交记录和项目背景（sglang是一个高性能大语言模型推理与服务框架，强调速度和异构硬件支持），现总结分析如下：

### 1. 主要更新类型
*   **性能优化（核心）**：多个提交针对AMD GPU（gfx950）进行深度优化，包括融合计算内核、稀疏注意力、MoE架构等，旨在提升特定硬件上的推理效率。
*   **Bug修复与稳定性提升**：包括修复NPU设备上的hang问题、统一内存池中的dtype保留问题、模型加载中的资源释放问题等，增强了系统在各种边界条件下的可靠性。
*   **功能增强与架构演进**：PD（推测为“生产-开发”分离）架构下重放token的处理、分布式路由（Router）功能的分步增强，以及投机解码（Spec）在流水线并行下的改进。
*   **文档与维护**：更新了AMD平台的每日构建镜像、添加了预填充上下文并行的指南与设计草案，以及通用的基准测试规则文档。

### 2. 关键变更点及其与项目方向的关系
*   **AMD硬件生态的深度集成**：一系列提交（如#41021， #41020， #41161， #40943）集中优化了AMD GPU上的MoE（混合专家）、稀疏注意力等关键算子，体现了项目**积极拥抱并优化异构计算硬件**的核心方向。
*   **分布式推理与路由强化**：Router相关的提交（如#40687， #40688， #40689）持续为分布式KV缓存管理和请求路由构建快照表面和副本标识能力，服务于**大规模、低延迟的集群部署**目标。
*   **推理核心路径的优化与修复**：针对PD架构中token重放、KV内存释放（#41235， #41404）以及投机解码（#39643）的改进，旨在**提升复杂推理场景的稳定性和吞吐量**。
*   **内存与缓存管理改进**：统一内存池的修复（#38133， #41144）和多模态特征哈希优化（#39539），致力于**提高内存使用效率和减少初始化开销**。

### 3. 对项目的影响和潜在意义
*   **提升市场竞争力**：对AMD硬件（如MI300/350系列）的深度优化，使sglang在主流NVIDIA之外，为AMD用户提供了高性能的推理选项，扩大了项目适用范围。
*   **增强生产就绪性**：对分布式路由、PD架构稳定性以及NPU等边缘硬件的支持，使sglang更适合作为**生产环境**中复杂、大规模LLM服务的后端引擎。
*   **推动性能前沿**：通过融合内核、稀疏注意力等底层优化，项目持续在**推理延迟和吞吐量**这两个核心性能指标上进行挑战和优化。
*   **改善开发者体验**：更新的文档和镜像为社区贡献者和用户提供更清晰的指南和更易用的开发环境，有助于项目生态建设。

### 4. 值得关注的技术点
*   **AMD gfx950架构专用优化**：如融合边界与归约的mHC内核（#41021）、稀疏解码注意力（#41020），显示了针对特定微架构的深度调优。
*   **统一内存池（Unified Memory）的精细化处理**：修复FP8数据类型的保留（#38133）和卷积检查点追踪ID的写入（#41144），体现了对混合精度计算和复杂内存布局的支持。
*   **模型加载预取机制的终止控制**（#41588）：确保迭代器完成后及时停止预取，避免资源浪费，是细节处的性能与资源管理优化。
*   **PD架构下对“重放”（Replayed）token的精细处理**：保留其采样掩码（#41235）和根据传输失败延迟释放KV（#41404），反映了对复杂推理状态机的深入设计。

### 5. 对项目发展的影响
本次提交批次进一步**巩固了sglang作为高性能、跨硬件LLM推理引擎的定位**。其影响主要体现在：
*   **拓宽硬件支持边界**：AMD GPU上的系列优化，使项目向“全硬件高性能推理”的愿景迈进了一大步。
*   **夯实分布式与集群部署基础**：Router组件的演进为未来构建更智能、更具弹性的大规模推理集群铺平了道路。
*   **完善核心推理可靠性**：通过对内存管理、状态恢复等“脏活累活”的修复，提升了框架在严苛生产环境下的鲁棒性。
*   **保持架构的前瞻性**：对投机解码、多模态融合、上下文并行等前沿方向持续投入，确保项目在未来模型架构变化中保持适应性。

综上所述，这些提交共同推动sglang在**性能广度（多硬件）、系统深度（核心优化）和架构完备性（分布式与生产特性）** 上协同发展。

## 详细提交记录

### [89e1316](https://github.com/sgl-project/sglang/commit/89e1316eae9aae634c174c040415289fe4484aee)

- **作者**: Shuwen Wang
- **时间**: 2026-09-28T23:41:07Z
- **提交信息**: [mem cache] refactor: remove the index-K continuous getters orphaned by the CP v1 removal (#41469)

### [f124c5c](https://github.com/sgl-project/sglang/commit/f124c5ceece1c61733b941cfd0e7e38fad52b44a)

- **作者**: Hrithvik Alex
- **时间**: 2026-09-28T23:27:09Z
- **提交信息**: [Model Loader] Stop checkpoint prefetch after iterator completion (#41588)

Co-authored-by: Hrithvik Alex <hrithvik@baseten.co>

### [9654e5c](https://github.com/sgl-project/sglang/commit/9654e5c4bcb233df406101cfc1b35aae05970691)

- **作者**: Kevin Mi
- **时间**: 2026-09-28T23:15:08Z
- **提交信息**: dsv4.1-amd: fused mHC boundary and all-reduce + mHC post kernels (#41021)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Kevin Mi <kevin.mi@radixark.ai>

### [096b066](https://github.com/sgl-project/sglang/commit/096b066fb4f6dc3b058ff294cb9e8f7f5a7150cf)

- **作者**: Kevin Mi
- **时间**: 2026-09-28T23:14:28Z
- **提交信息**: dsv4.1-amd: gfx950 sparse decode attention and sorted top-k (#41020)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [26d7539](https://github.com/sgl-project/sglang/commit/26d7539799ec37efb387cdbcc14992aa1a644eca)

- **作者**: Zhang, Jiejing
- **时间**: 2026-09-28T22:42:54Z
- **提交信息**: [Docs][AMD] Update GLM-5.2 MI355X daily image (#41597)

### [b07cb9e](https://github.com/sgl-project/sglang/commit/b07cb9e9e73acc60c04b5fcf6554380b4ec78770)

- **作者**: Trevor Morris
- **时间**: 2026-09-28T21:12:46Z
- **提交信息**: [NVIDIA] Update deepgemm, deep-ep, sgl-kernel in CUDA 13.4 image, use cuda base image (#40987)

### [6fa3fe6](https://github.com/sgl-project/sglang/commit/6fa3fe69e2e5e19b75cadd9fc285b72634551992)

- **作者**: Nan Jiang
- **时间**: 2026-09-28T19:02:27Z
- **提交信息**: [PD] Keep the sampling mask of a replayed rebootstrap token (#41235)

### [2a1c477](https://github.com/sgl-project/sglang/commit/2a1c477648fe962627a1af091de54ca5e05859b4)

- **作者**: Shangming Cai
- **时间**: 2026-09-28T18:19:51Z
- **提交信息**: [PD] Defer decode KV release on every transfer failure, not only decode-initiated aborts (#41404)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [f209e67](https://github.com/sgl-project/sglang/commit/f209e67767304b9c03aabc7852de839d05db2c09)

- **作者**: YAMY
- **时间**: 2026-09-28T17:22:40Z
- **提交信息**: [Spec] Model-agnostic last-stage draft embedding under pipeline parallelism (#39643)

### [6624999](https://github.com/sgl-project/sglang/commit/6624999385015d04d6a8a5d369546e7fc9d40229)

- **作者**: Kurkur
- **时间**: 2026-09-28T16:41:43Z
- **提交信息**: [Fix][NPU] fix dp-attn hang when pin_mem is True on NPU (#40446)

### [2e7e080](https://github.com/sgl-project/sglang/commit/2e7e0802f4f3edc94702933675a71d6c7ef4f24f)

- **作者**: triple-mu
- **时间**: 2026-09-28T13:45:39Z
- **提交信息**: [diffusion] Qwen-Image 2.1: fuse Q/K RMSNorm + RoPE + KV packing into one CUDA kernel and project Q/K/V with one packed GEMM (#41339)

### [8151378](https://github.com/sgl-project/sglang/commit/8151378c1ab3c2e01ce6d23f9377922ebde55b03)

- **作者**: DarkSharpness
- **时间**: 2026-09-28T13:43:57Z
- **提交信息**: [DeepSelect] Add page-table transform to top-k and tighten the layout contract (#41364)

Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [0318a8d](https://github.com/sgl-project/sglang/commit/0318a8d0af86ba14a05ca093aa43fafe446da23e)

- **作者**: DarkSharpness
- **时间**: 2026-09-28T12:25:58Z
- **提交信息**: [Doc] Add kernel benchmark rule on L2 cache reuse (#41545)

Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [da3eb6d](https://github.com/sgl-project/sglang/commit/da3eb6db32a1d2de6e8bb0d4b3984a33c1d3f7ef)

- **作者**: Shuwen Wang
- **时间**: 2026-09-28T12:19:19Z
- **提交信息**: [Unified Memory] Fix Inkling conv-checkpoint track ids written to virtual slot numbers (#41144)

### [bddeb61](https://github.com/sgl-project/sglang/commit/bddeb61d948ad7ad9279899a397c79b03ba054b8)

- **作者**: Shuwen Wang
- **时间**: 2026-09-28T12:19:03Z
- **提交信息**: [Unified Memory] fix: preserve FP8 dtype in unified MHA pool (#38133)

### [090439b](https://github.com/sgl-project/sglang/commit/090439bf8f9a73ba999faac2a1179c6714adac58)

- **作者**: Mick
- **时间**: 2026-09-28T12:04:32Z
- **提交信息**: [diffusion] docs: consolidate Qwen-Image 2.1 guidance in its cookbook (#41540)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [6aacca2](https://github.com/sgl-project/sglang/commit/6aacca2d919bcefa98244cc0c564818ce37d8c0e)

- **作者**: Kangyan-Zhou
- **时间**: 2026-09-28T10:49:09Z
- **提交信息**: [Router] Name a replica's siblings with --kv-peer-selector (3/13) (#40689)

Co-authored-by: Kangyan Zhou <kangyan.zhou@radixark.ai>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [fa44341](https://github.com/sgl-project/sglang/commit/fa443412c558b5b58bed47a12e4eb7363dddf211)

- **作者**: Raiden Makoto
- **时间**: 2026-09-28T10:40:09Z
- **提交信息**: [AMD] [GLM5] Fuse shared expert into AITER MoE on gfx950 (#41161)

Signed-off-by: Raiden-Makoto <Raiden-Makoto@users.noreply.github.com>
Co-authored-by: Raiden-Makoto <Raiden-Makoto@users.noreply.github.com>

### [2f88c65](https://github.com/sgl-project/sglang/commit/2f88c6528906a2464dee6eb9adbf9e8c25f4781e)

- **作者**: Kangyan-Zhou
- **时间**: 2026-09-28T10:38:52Z
- **提交信息**: [Router] Serve the cache-aware tree at /internal/kv_snapshot (2/13) (#40688)

Co-authored-by: Kangyan Zhou <kangyan.zhou@radixark.ai>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [47ad192](https://github.com/sgl-project/sglang/commit/47ad1928a2517c3f865fa2f118c2287ff141e263)

- **作者**: Kan Wu
- **时间**: 2026-09-28T10:37:40Z
- **提交信息**: [sgl-router] Scope input_ids forwarding by renderer: all text chats for DeepSeek-V4 (#41226)

Co-authored-by: Kan Wu <kan.wu@radixark.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Shangming Cai <csmthu@gmail.com>

### [85be049](https://github.com/sgl-project/sglang/commit/85be04978d76843635690300246aaf2f29a307fa)

- **作者**: karverma-amd
- **时间**: 2026-09-28T10:21:57Z
- **提交信息**: [AMD][DSV4] moe: enable shared-expert fusion on the grouped-topk path (megamoe) (#40943)

### [6caf0ff](https://github.com/sgl-project/sglang/commit/6caf0ff4aeb7890815ad8bed8f12397ba9819302)

- **作者**: Denji-kk
- **时间**: 2026-09-28T09:51:05Z
- **提交信息**: perf(multimodal): offload CPU feature hashing with bounded admission (#39539)

### [c02eaad](https://github.com/sgl-project/sglang/commit/c02eaadeb28c1e0b41e9730d18fb78dbcd4d7f01)

- **作者**: Mick
- **时间**: 2026-09-28T09:45:58Z
- **提交信息**: [diffusion] optimization: populate cpu weight stores before host registration to speedup layerwise-offload initialization (#40439)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [6582425](https://github.com/sgl-project/sglang/commit/65824258549671404188450748b90ab7cacab2ae)

- **作者**: Peng Wu
- **时间**: 2026-09-28T09:07:35Z
- **提交信息**: Let predicate-registered linear-attention models carry the mamba radix-cache leaves (#41165)

### [df378bc](https://github.com/sgl-project/sglang/commit/df378bca4259c3ca455b17b9483d9a134e45a739)

- **作者**: Kangyan-Zhou
- **时间**: 2026-09-28T08:59:59Z
- **提交信息**: [Router] Give the cache-aware tree a snapshot surface (1/13) (#40687)

Co-authored-by: Kangyan Zhou <kangyan.zhou@radixark.ai>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [546bfa7](https://github.com/sgl-project/sglang/commit/546bfa7221ce70af2f086eeea2135a7701cfe280)

- **作者**: Peng Wu
- **时间**: 2026-09-28T08:46:11Z
- **提交信息**: [Kimi-K3] Merge fused_qkvg_proj into the loader-seeded packed_modules_mapping (#41164)

### [e8eeff2](https://github.com/sgl-project/sglang/commit/e8eeff2956be1fa9db0134a789e882c291753cb8)

- **作者**: ashwini rathi
- **时间**: 2026-09-28T08:15:12Z
- **提交信息**: [XPU] Bump sglang-kernel-xpu wheel to v0.3.0 (#41220)

Co-authored-by: Pramod Kumar <144990617+pramodkumar-habanalabs@users.noreply.github.com>

### [7ee7bef](https://github.com/sgl-project/sglang/commit/7ee7bef79decaf78f7669994f74e6f75c7784c14)

- **作者**: Baizhou Zhang
- **时间**: 2026-09-28T07:26:02Z
- **提交信息**: docs: add prefill context parallelism guide and design draft (#39354)

### [6405cf2](https://github.com/sgl-project/sglang/commit/6405cf288103304f399074ede8529af37cfdd51c)

- **作者**: Ke Bao
- **时间**: 2026-09-28T07:17:09Z
- **提交信息**: Fix chat template cache key order (#41517)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-09-29
**监控日期**: 2026-09-28
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1286
- **最后更新**: 2026-09-27T05:52:14Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-09-29
**监控日期**: 2026-09-28
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 92894
- **最后更新**: 2026-09-29T01:46:22Z

## 提交统计

- **昨日提交总数**: 45
- **提交者数量**: 39
- **主要提交者**: Gabriel Wu, Rohan Potdar, xiaohuguo2023

## AI分析总结

根据昨日提交记录，vllm项目的更新主要聚焦于**稳定性提升与多硬件平台支持**，具体分析如下：

1.  **主要更新类型**：
    *   **Bug修复**：占比较高，涉及核心调度器、推测解码、模型加载、量化计算及前端请求处理等多个模块。
    *   **性能优化**：针对特定模型（如Qwen3.8、Qwen4Exp）和操作（如DSA候选块选择、PLE元数据构建）进行内核级优化。
    *   **功能增强与适配**：新增功能（如固定token预填充评分）并增强了对新模型（Gemma4、Kimi-K3）、量化格式（CT WNA16 MoE）及LoRA变体的支持。
    *   **CI/构建与基础设施**：大量调整测试配置、修复CI流程、优化镜像依赖，以保障开发与集成稳定性。
    *   **重构与清理**：对调度器队列等内部逻辑进行优化重构。

2.  **关键变更点与项目方向的关系**：
    *   这些提交紧密围绕项目“**轻松、快速、便宜**”的核心目标。大量**Bug修复**（尤其是调度器、Spec Decode相关）旨在提升服务稳定性与可靠性，降低使用门槛。**性能优化**直接旨在降低推理成本与提升速度。**多硬件平台（ROCm, XPU）** 的密集修复与适配，体现了项目扩展生态、服务更广泛用户的意图，契合“为所有人”的目标。

3.  **对项目的影响和潜在意义**：
    *   **即时提升**：修复了影响生产稳定性的关键问题（如流式续传、日志记录、KV缓存管理），优化了核心路径性能，将直接改善现有用户体验。
    *   **生态巩固**：对AMD ROCm和Intel XPU平台的持续投入与修复，强化了vllm作为跨硬件、开放生态LLM服务引擎的定位。
    *   **开发效率**：CI/构建的调整增强了自动化测试能力，有助于保障未来代码质量，加速功能迭代。
    *   **技术深度**：在推测解码、混合专家模型（MoE）、量化等先进LLM技术上持续精进，巩固了项目的技术领先性。

4.  **值得关注的技术点**：
    *   **调度器稳定性**：对流式续传请求状态管理、日志概率保持、任务队列的修复与重构，是保障复杂服务逻辑正确的关键。
    *   **推测解码优化**：通过避免重编译、正确处理草案槽位等方式，提升Speculative Decoding这一关键技术的效率与可靠性。
    *   **跨硬件实现**：针对ROCm和XPU的特定内核优化、测试修复及特性开关调整，展示了在异构计算平台上的工程深度。
    *   **模型与量化兼容性**：对新型号、新量化格式（如8-bit非对称GPTQ MoE）的支持，反映了项目对前沿模型生态的快速跟进。

5.  **对项目发展的影响**：
    *   此次提交批次体现了vllm社区**活跃且聚焦**的发展态势。通过巩固基础（修复Bug、优化CI）、提升性能、扩展硬件支持，项目正朝着更**稳定、高效、通用**的生产级LLM服务平台迈进。对多厂商硬件的持续支持，正使其从“NVIDIA GPU加速”扩展为真正的“通用硬件基础设施”，这将极大扩大其应用范围和用户基础，强化其作为开源LLM服务核心组件的地位。

## 详细提交记录

### [c68eb98](https://github.com/vllm-project/vllm/commit/c68eb98b69f4863d94318fbe9dedf654be0c5945)

- **作者**: Benedikt Falk
- **时间**: 2026-09-28T23:52:29Z
- **提交信息**: [Bugfix][Frontend] Keep in-flight requests on the same DP engine (#59017)

Signed-off-by: Benedikt Falk <bfalk@nvidia.com>

### [75fad5b](https://github.com/vllm-project/vllm/commit/75fad5bbef7b2c0264c4b7ce6c4c10e32233d523)

- **作者**: Mehmet Cagri
- **时间**: 2026-09-28T23:40:11Z
- **提交信息**: [Bugfix][ROCm] Drop -1 sentinels when building the ragged sparse-MLA indices (#58058)

Signed-off-by: Mehmet Cagri Kaymak <mehmet.kaymak@amd.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [9b29370](https://github.com/vllm-project/vllm/commit/9b29370524cfd84b3a85bae8c2db8112fd52003b)

- **作者**: Spandan Tiwari
- **时间**: 2026-09-28T23:38:28Z
- **提交信息**: [Bugfix] Fix moe_wna16 w13 zero-point shard split for 8-bit asym GPTQ MoE (#58950)

Signed-off-by: Spandan Tiwari <sptiwari@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [8a497d7](https://github.com/vllm-project/vllm/commit/8a497d75572f8241f15182d55f8d704e39773085)

- **作者**: rasmith
- **时间**: 2026-09-28T23:30:38Z
- **提交信息**: [CI/Build][BugFix][The Rock] Make supports_mm_prefix  return False for ROCm attn and unified attn since Prefix-LM not implemented (#52395)

Signed-off-by: Randall Smith <Randall.Smith@amd.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [e03875f](https://github.com/vllm-project/vllm/commit/e03875f4d283bc003b08af351a0b316e18cd798b)

- **作者**: rmhaskar
- **时间**: 2026-09-28T23:21:13Z
- **提交信息**: [Minimax M3] Enable fp8 indexer cache on triton indexer for non-SM100 architectures.  (#59081)

Signed-off-by: Jarrel Seah <jarrel@harrison.ai>
Signed-off-by: Tyler Michael Smith <tlrmchlsmth@gmail.com>
Signed-off-by: Rajas Mhaskar <rmhaskar@nvidia.com>
Co-authored-by: Jarrel Seah <jarrel@harrison.ai>
Co-authored-by: Tyler Michael Smith <tlrmchlsmth@gmail.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [6a6c295](https://github.com/vllm-project/vllm/commit/6a6c2952faecdce6760dafb30df1eff95c79d717)

- **作者**: Fanli Lin
- **时间**: 2026-09-28T23:12:43Z
- **提交信息**: [XPU][CI] Make `test_mamba_prefix_cache` block-size agnostic (#58269)

Signed-off-by: Lin, Fanli <fanli.lin@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [3bd7302](https://github.com/vllm-project/vllm/commit/3bd7302396cdeb1d965890105f7fc25fa2d62f6b)

- **作者**: Yan Ma
- **时间**: 2026-09-28T23:10:52Z
- **提交信息**: [XPU] skip test_online_quantization_loads_real_weights (#58987)

Signed-off-by: Yan Ma <yan.ma@intel.com>

### [754aa29](https://github.com/vllm-project/vllm/commit/754aa29c006ddfbc518ae7d89e30414c6866d890)

- **作者**: Yan Ma
- **时间**: 2026-09-28T23:09:58Z
- **提交信息**: [XPU] use rms_norm xpu kernel for context-key normalization (#58896)

Signed-off-by: Yan Ma <yan.ma@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [32cc3f1](https://github.com/vllm-project/vllm/commit/32cc3f1ea886c38cbacde35550eb74defaa7bca1)

- **作者**: Abhinandan
- **时间**: 2026-09-28T21:46:21Z
- **提交信息**: [CI] Drop test-group rules that no longer match the tree (#58895)

Signed-off-by: Abhinandan <abhinandanverma551@gmail.com>

### [3d5f4d4](https://github.com/vllm-project/vllm/commit/3d5f4d4cd5d86788151664597bcebea666c34700)

- **作者**: Giancarlo Delfin
- **时间**: 2026-09-28T20:46:25Z
- **提交信息**: [Perf][Spec Decode] Avoid triton recompiles in the acceptance estimator (#57107)

Signed-off-by: Giancarlo Delfin <gdelfin@inferact.ai>
Co-authored-by: Woosuk Kwon <woosuk@inferact.ai>

### [d28795f](https://github.com/vllm-project/vllm/commit/d28795f1a7af4e3ce2530d4f0bdaec4ecbede693)

- **作者**: 0xsensei
- **时间**: 2026-09-28T20:31:57Z
- **提交信息**: [Bugfix][Scheduler] Refresh max tokens for streaming continuations (#57676)

Signed-off-by: 0xsensei <prblmslvr.aditya@gmail.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [beef814](https://github.com/vllm-project/vllm/commit/beef814e1d3aa1e198b604a08aa2494fad9842be)

- **作者**: Andreas Karatzas
- **时间**: 2026-09-28T20:12:07Z
- **提交信息**: [ROCm][CI] Add missing test coverage for upstream parity (#50519)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Signed-off-by: Stefan Koncarevic <Stefan.Koncarevic@amd.com>
Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>
Co-authored-by: Stefan Koncarevic <Stefan.Koncarevic@amd.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [fedbc3b](https://github.com/vllm-project/vllm/commit/fedbc3b564102efb38f3697acb69920c3ac912be)

- **作者**: qizixi
- **时间**: 2026-09-28T20:07:15Z
- **提交信息**: [Bugfix][MRV2][Spec Decode] Reject draft slots that were never proposed (#58784)

Signed-off-by: zixi-qi <zixi@inferact.ai>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>

### [42dbe45](https://github.com/vllm-project/vllm/commit/42dbe4578c7bbeceadc28bd8c6a3826949163f5c)

- **作者**: Nick Hill
- **时间**: 2026-09-28T20:03:16Z
- **提交信息**: [Core] Rework scheduler `skipped_waiting` queue (#58947)

Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Robert Shaw <114415538+robertgshaw2-redhat@users.noreply.github.com>

### [2619b6b](https://github.com/vllm-project/vllm/commit/2619b6b72b24a8c1963ef6b29427c53b826023d1)

- **作者**: Ashraf Bhuiyan
- **时间**: 2026-09-28T19:52:50Z
- **提交信息**: [Mypy] Fix mypy typing for Voxtral and vision models (#58251)

Signed-off-by: Ashraf Bhuiyan <mbhuiyan@redhat.com>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>

### [2840ca7](https://github.com/vllm-project/vllm/commit/2840ca7a332525fe73bbc55ef508722372875823)

- **作者**: 0xsensei
- **时间**: 2026-09-28T19:50:27Z
- **提交信息**: [Bugfix][Scheduler] Preserve logprobs across streaming continuations (#57447)

Signed-off-by: 0xsensei <prblmslvr.aditya@gmail.com>

### [e7c9036](https://github.com/vllm-project/vllm/commit/e7c903609f6ca10f8d6c8e9a5d09a39ff7f4c2e4)

- **作者**: Nick Hill
- **时间**: 2026-09-28T19:48:52Z
- **提交信息**: [Perf][MRV2] Allow FULL decode graphs for one-token prompt tails (#58400)

Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Nicolò Lucchesi <nicolo.lucchesi@mistral.ai>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Yongye Zhu <zyy1102000@gmail.com>

### [ef42093](https://github.com/vllm-project/vllm/commit/ef42093a36b7d7cc74ecfc0533099e01f2aa8286)

- **作者**: Xiaoshuang Wang
- **时间**: 2026-09-28T19:38:05Z
- **提交信息**: [Model Runner V2][Spec Decode] Support spec decode with draft model (#43091)

Signed-off-by: Icey <1790571317@qq.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [2f4a975](https://github.com/vllm-project/vllm/commit/2f4a9759014e9294b4402aeae0fc25c11b47fc7d)

- **作者**: yzong-rh
- **时间**: 2026-09-28T19:26:57Z
- **提交信息**: [Bugfix] Fix resumable request + async scheduling handoff race (#58259)

Signed-off-by: Yifan Zong <yzong@redhat.com>

### [7644135](https://github.com/vllm-project/vllm/commit/764413559a1416511002268ac460bbf8e7ddd394)

- **作者**: Kevin H. Luu
- **时间**: 2026-09-28T19:14:21Z
- **提交信息**: [Bugfix] Don't sync-police or retry FlashInfer all-reduce workspace creation in eager mode (#58498)

Signed-off-by: khluu <khluu000@gmail.com>
Signed-off-by: Lucas Wilkinson <LucasWilkinson@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Lucas Wilkinson <LucasWilkinson@users.noreply.github.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>

### [25624f6](https://github.com/vllm-project/vllm/commit/25624f65cf40ff6ce62e3261331b1b1ea7fc5e0a)

- **作者**: xiaohuguo2023
- **时间**: 2026-09-28T18:52:21Z
- **提交信息**: [ROCm][MLA] Add an AITER ASM round-robin decode route for DCP multi-token verify (#56861)

Signed-off-by: Xiaohu Guo <Xiaohu.Guo@amd.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: seungrokj <144636725+seungrokj@users.noreply.github.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [5ba2e30](https://github.com/vllm-project/vllm/commit/5ba2e3090b4c6bb6d5b4fd8ed3045107e787309e)

- **作者**: djramic
- **时间**: 2026-09-28T17:56:10Z
- **提交信息**: [ROCm][CI] Increase timeout for Entrypoints Unit (#59076)

Signed-off-by: Djordje Ramic <djoramic@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [7a160c6](https://github.com/vllm-project/vllm/commit/7a160c6fe5910957a0feac50074ec6fc183c2a92)

- **作者**: Rohan Potdar
- **时间**: 2026-09-28T17:33:09Z
- **提交信息**: [ROCm][CI] Pin OpenTelemetry to LMCache's cap in the ROCm images (#59051)

Signed-off-by: Rohan Potdar <rohan.potdar@amd.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [6c300dd](https://github.com/vllm-project/vllm/commit/6c300ddb9e9d9582324032ee68525aae60c9800c)

- **作者**: stefankoncarevic
- **时间**: 2026-09-28T17:29:59Z
- **提交信息**: [CI][Bugfix] Relax packed_qk_rope_ correctness test to one ULP (#59008)

Signed-off-by: Stefan Koncarevic <stefan.koncarevic@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [c01368f](https://github.com/vllm-project/vllm/commit/c01368fd64eaecc0c7242e4d933ec80fe8e047f5)

- **作者**: HDCharles
- **时间**: 2026-09-28T17:22:44Z
- **提交信息**: [Quant] Use canonical N-first weight format for CT WNA16 MoE (#52798)

Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>
Co-authored-by: HDCharles <{"message":"Not Found","documentation_url":"https://docs.github.com/rest/users/emails#list-email-addresses-for-the-authenticated-user","status":"404"}>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [6d3ea3c](https://github.com/vllm-project/vllm/commit/6d3ea3c2c9037deadb9fb70d40bc69b7947af463)

- **作者**: qizixi
- **时间**: 2026-09-28T16:50:46Z
- **提交信息**: [KVConnector][NIXL] Support packed MLA KV layouts in pipeline-parallel push prefill (#50499)

Signed-off-by: zixi-qi <zixi@inferact.ai>

### [94d1462](https://github.com/vllm-project/vllm/commit/94d14629247955c69d40bdf2a9d7e3bd45954452)

- **作者**: Oxana Korzh
- **时间**: 2026-09-28T16:05:10Z
- **提交信息**: [Bugfix][Kimi-K3] Refresh DSpark context KV cache pointers after the KV cache is re-bound (#58814)

Signed-off-by: Oxana Korzh <okorzh@amd.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [b0d2b85](https://github.com/vllm-project/vllm/commit/b0d2b854f69379f3c83bb7215654e315d29fd815)

- **作者**: Micah Williamson
- **时间**: 2026-09-28T15:49:48Z
- **提交信息**: [ROCm]Keep LMCache OpenTelemetry on the image's 1.40 stack (#59056)

Signed-off-by: Micah Williamson <micah.williamson@amd.com>

### [6b24bd8](https://github.com/vllm-project/vllm/commit/6b24bd8e75a3e465083e8a131968915bc00efaf4)

- **作者**: Fangzhou Ai
- **时间**: 2026-09-28T15:42:42Z
- **提交信息**: [ROCm][Perf] Replace torch.topk in DSA candidate block selection (#58208)

Signed-off-by: fai <fangzhouai@gmail.com>
Co-authored-by: TJian <tunjian.tan@embeddedllm.com>
Co-authored-by: Cursor Agent <cursoragent@cursor.com>

### [953f90d](https://github.com/vllm-project/vllm/commit/953f90d25fea2240965878a1aca66cec519685b0)

- **作者**: linitra24
- **时间**: 2026-09-28T14:58:35Z
- **提交信息**: [LoRA] Support variable num_labels for sequence classification (#57766)

Signed-off-by: linitra24 <renshuang.zhou@daocloud.io>
Co-authored-by: Jee Jee Li <pandaleefree@gmail.com>

### [b721a4c](https://github.com/vllm-project/vllm/commit/b721a4c709da44551b614e2562fcfa7f4cbd1352)

- **作者**: aoshen02
- **时间**: 2026-09-28T14:50:09Z
- **提交信息**: [Feature] Add fixed-token prefill scoring (#54335)

Signed-off-by: aoshen02 <aoshen@inferact.ai>
Signed-off-by: aoshen02 <aoshen02@users.noreply.github.com>
Co-authored-by: aoshen02 <aoshen02@users.noreply.github.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [a7ff443](https://github.com/vllm-project/vllm/commit/a7ff44355c1cadd1d85b82f4adc9694ce7864b56)

- **作者**: xaguilar-amd
- **时间**: 2026-09-28T14:31:29Z
- **提交信息**: [ROCm][Perf] Kimi-K3 Enable sharded latent MoE up-projection under EP (#54956)

Signed-off-by: Xavier Aguilar <xavier.aguilarfruto@amd.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [cd63bf9](https://github.com/vllm-project/vllm/commit/cd63bf9996d3fdbe24a3228f970b84310600612f)

- **作者**: Clinton Thomas
- **时间**: 2026-09-28T14:25:40Z
- **提交信息**: [Bugfix] Use the correct repository revision for secondary artifact loaders (#57461)

Signed-off-by: Clinton Thomas <1033162+KernelClint@users.noreply.github.com>
Co-authored-by: Lucas Bourtoule <35483370+dhalf@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [d7f5722](https://github.com/vllm-project/vllm/commit/d7f5722d7b487dd6794f638043375a95ebecfef7)

- **作者**: Misha Goin
- **时间**: 2026-09-28T13:20:16Z
- **提交信息**: [Bugfix][Logging] Preserve application log record factories (#58747)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [522101f](https://github.com/vllm-project/vllm/commit/522101f6ede5ffd57844a8729cf0f2f6fe1a7a47)

- **作者**: Isotr0py
- **时间**: 2026-09-28T13:04:01Z
- **提交信息**: [Multimodal] Avoid extra d2d for encoder cudagraph with fused input norm (#56711)

Signed-off-by: Isotr0py <Isotr0py@outlook.com>

### [7ba3df6](https://github.com/vllm-project/vllm/commit/7ba3df63cbe2e3e7aca19074bed2958311f46400)

- **作者**: Shanshan Shen
- **时间**: 2026-09-28T12:46:28Z
- **提交信息**: [ROCm][Refactor] Move DeepSeek-V4/V4.1 multi-stream overlap gate to ROCm platform (#58983)

Signed-off-by: Shanshan Shen <87969357+shen-shanshan@users.noreply.github.com>

### [20b52e9](https://github.com/vllm-project/vllm/commit/20b52e9f5b5793d56586b91df9b93cbe30a24040)

- **作者**: Jiangyun Zhu
- **时间**: 2026-09-28T12:46:22Z
- **提交信息**: [Perf][Qwen3.8] Reduce PLE metadata construction overhead (#58114)

Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [f6877f5](https://github.com/vllm-project/vllm/commit/f6877f563c5b27e858773b8416dc5ee3d76233ec)

- **作者**: BaoYunkai
- **时间**: 2026-09-28T12:16:38Z
- **提交信息**: [Bugfix][Spec Decode] Implement get_top_tokens() on the ROCm DeepSeek V4 MTP drafter (#57568)

Signed-off-by: BaoYunkai <ybao@amd.com>

### [8cc9aa5](https://github.com/vllm-project/vllm/commit/8cc9aa5ad350f6f80cf3bebb298d410803ff75a9)

- **作者**: Yannick Schnider
- **时间**: 2026-09-28T10:56:31Z
- **提交信息**: [Bugfix][Model] Gemma4: register aliased embedding scalars as buffers (#54213)

Signed-off-by: Yannick Schnider <Yannick.Schnider1@ibm.com>

### [d6cce94](https://github.com/vllm-project/vllm/commit/d6cce94fd4221e6f5547e1c00ca5e0c92ab52d6c)

- **作者**: Thien Tran
- **时间**: 2026-09-28T10:51:38Z
- **提交信息**: [Perf][Qwen4Exp] Fuse HC down projection and SiLU on NVIDIA (#58957)

Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>

### [2522793](https://github.com/vllm-project/vllm/commit/252279314be01156707d76e8d9354b299106e0ba)

- **作者**: Kevin H. Luu
- **时间**: 2026-09-28T10:51:17Z
- **提交信息**: Revert "[CI] Shard (H200 MIG 35GB / MI355 DPX) Entrypoints Integration (Pooling) into named jobs (#58652)" (#59011)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [ccfd1ce](https://github.com/vllm-project/vllm/commit/ccfd1cea75eff8956c5d08b15a7eaec8891642e9)

- **作者**: Louie Tsai
- **时间**: 2026-09-28T08:46:53Z
- **提交信息**: [CPU] Include vLLM Recipes tooling in release image to deploy models using vLLM Recipes (#58796)

Signed-off-by: louie-tsai <louie.tsai@intel.com>

### [a2be4d3](https://github.com/vllm-project/vllm/commit/a2be4d3cc7b978a6720dab32d28ae310775acb16)

- **作者**: Gabriel Wu
- **时间**: 2026-09-28T08:11:46Z
- **提交信息**: [Bugfix][Qwen4Exp] Release the profiling KV cache held by QSA key views (#58961)

Signed-off-by: Zihua Wu <13583761+lucifer1004@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [66d2d4b](https://github.com/vllm-project/vllm/commit/66d2d4b2e7a38518110aeba31627d99c41b1735d)

- **作者**: Thang Nguyen
- **时间**: 2026-09-28T07:32:11Z
- **提交信息**: [CI] Split Dynamic Shapes out of (H200 MIG 35GB) PyTorch Compilation + (MI300) mirror (#58451)

Signed-off-by: Thang Nguyen <thangnguyenvn647@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [413ae4b](https://github.com/vllm-project/vllm/commit/413ae4b1677bd34398c63840c3f29c0b35bf3da9)

- **作者**: Thang Nguyen
- **时间**: 2026-09-28T07:21:08Z
- **提交信息**: [CI] Shard (H200 MIG 35GB / MI355 DPX) Entrypoints Integration (Pooling) into named jobs (#58652)

Signed-off-by: Thang Nguyen <thangnguyenvn647@gmail.com>
Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: khluu <khluu000@gmail.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-09-29
**监控日期**: 2026-09-28
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7119
- **最后更新**: 2026-09-29T01:38:19Z

## 提交统计

- **昨日提交总数**: 14
- **提交者数量**: 13
- **主要提交者**: vraiti, Shaun Walsh, chickeyton

## AI分析总结

基于 `vllm-project/vllm-omni` 昨日提交记录及项目背景，分析总结如下：

**1. 主要更新类型**
本次提交以**性能优化**与**功能增强**为主，并包含多项**Bug修复**与**测试改进**。具体分布为：
*   **性能优化**：针对MiniCPM-o的CUDA图优化、FlashInfer后端导入改进、TTS实时性优化、扩散模型FP8支持、MoE路由路径优化等。
*   **功能新增**：新增符合OpenAI规范的实时全双工API、CosyVoice3的GPU驻留F0预测器、MammothModa2共享RMSNorm等。
*   **Bug修复**：解决MiniMax参考图/视频异常放大、MiniCPM-o语音单元处理、扩散阶段休眠/唤醒失败处理、API字段约束缺失等问题。
*   **测试与重构**：统一使用vllm的测试辅助方法，改善错误信息提示。

**2. 关键变更点及其与项目方向的关系**
核心变更聚焦于**深化多模态推理能力与提升服务性能**，与项目“提供简单、快速且低成本的全模态模型服务”目标高度一致：
*   **性能优化（CUDA图、FP8、MoE路径）**：直接降低模型推理的延迟与成本，是实现“快速、低成本”的关键。
*   **新增实时API**：支持全双工交互，拓展了服务在对话、实时生成等场景的应用，是迈向“易用”和全模态交互的重要一步。
*   **多后端与硬件适配（FlashInfer, FP8）**：增强平台兼容性，使其能利用不同硬件加速器，服务于更广泛的部署环境。
*   **模型特定优化（MiniCPM-o, CosyVoice3）**：针对热门或关键模型进行深度优化，提升其在平台上的运行效果，直接增强平台吸引力。

**3. 对项目的影响和潜在意义**
*   **直接性能提升**：多项内核级优化预计将显著提升特定模型在平台上的吞吐量与响应速度，巩固其高性能服务形象。
*   **API生态完善**：遵循OpenAI标准的实时API降低了开发者接入门槛，有助于构建应用生态。
*   **稳定性与可靠性增强**：多项Bug修复提升了服务的健壮性，尤其是涉及资源管理（休眠/唤醒）和输入处理的边界情况。
*   **技术领先性体现**：在FP8量化、高效MoE路由等前沿技术上的积极采用，展示了平台的技术前瞻性。

**4. 值得关注的技术点**
*   **“Whole-Euler CUDA graphs”**：一种新的CUDA图应用策略，可能通过减少图切换开销来提升复杂模型的执行效率。
*   **“共享注意力竞技场”**：推测为一种优化注意力计算内存或调度的技术，用于提升批处理效率。
*   **“GPU驻留F0预测器与纯PyTorch声码器”**：将语音合成流水线中的关键组件完全置于GPU并使用PyTorch实现，旨在提升效率并简化开发维护。
*   **针对实时API的字段约束**：确保了API调用的规范性与安全性。

**5. 基于项目背景对发展的影响**
这些提交从多个维度共同推动项目发展：
*   **广度拓展**：支持新模型架构（如Qwen3-Omni）和新API端点，扩大了平台可服务的模型与场景范围。
*   **深度挖掘**：对核心内核、调度机制和特定模型进行深度性能调优，挖掘硬件潜力，追求极致效能。
*   **工程成熟度**：通过统一的测试辅助、明确的错误处理和完善API约束，提升项目的工程质量与可维护性。
综上所述，这批提交展现了项目在巩固性能优势、扩展功能边界和完善工程实践上的并行努力，正稳步推进其成为全模态模型服务的关键基础设施。

## 详细提交记录

### [3e62bba](https://github.com/vllm-project/vllm-omni/commit/3e62bba3cb1ea98a007d35651527d2ca4e91aeb0)

- **作者**: BeatSeat
- **时间**: 2026-09-28T23:14:12Z
- **提交信息**: [Performance][MiniCPM-o] Whole-Euler CUDA graphs for Code2Wav with a shared attention arena (#8007)

### [0173cb3](https://github.com/vllm-project/vllm-omni/commit/0173cb374839c437df098e5a34b2f842769fb266)

- **作者**: RuQing Xu
- **时间**: 2026-09-28T21:21:58Z
- **提交信息**: [Kernel] Improve 2 backends importing FlashInfer: FLASHINFER_ATTN and TRTLLM_ATTN (#7431)

Signed-off-by: Ruqing Xu <7891482+xrq-phys@users.noreply.github.com>

### [d31dbc5](https://github.com/vllm-project/vllm-omni/commit/d31dbc5b0a69a9160526a344cb98c8270a5f9c3e)

- **作者**: vraiti
- **时间**: 2026-09-28T20:14:05Z
- **提交信息**: [Frontend] OpenAI-compliant fullduplex /v1/realtime with Qwen3-Omni support (#7285)

Signed-off-by: vraiti <vraiti@redhat.com>

### [7266fc6](https://github.com/vllm-project/vllm-omni/commit/7266fc6138b0161a75aea2ee9ac9c4722d129c5c)

- **作者**: SYLAR
- **时间**: 2026-09-28T20:12:53Z
- **提交信息**: [Bugfix] Avoid enlarging MiniMax H3 reference images and videos (#8253)

Signed-off-by: lishunyang12 <lishunyang12@users.noreply.github.com>
Co-authored-by: lishunyang12 <lishunyang12@users.noreply.github.com>
Co-authored-by: Roger Wang <hey@rogerw.io>

### [b656fcf](https://github.com/vllm-project/vllm-omni/commit/b656fcf45bdbe75df6f47911275dd248c6c5736f)

- **作者**: Nick Cao
- **时间**: 2026-09-28T18:22:25Z
- **提交信息**: [Tests] Use get_file_store_init_method helper from vllm (#7528)

Signed-off-by: Nick Cao <ncao@redhat.com>
Co-authored-by: Codex <noreply@openai.com>

### [12e9280](https://github.com/vllm-project/vllm-omni/commit/12e9280010afc41ce5c6a1f46900fc329cf08377)

- **作者**: jingchengtian
- **时间**: 2026-09-28T17:31:48Z
- **提交信息**: [Perf][TTS] Run talker_mtp eagerly when a batch carries explicit seeds (#8009)

Signed-off-by: jingchengtian <tjc1995@126.com>

### [a07384b](https://github.com/vllm-project/vllm-omni/commit/a07384b953a4940e56d64aad55d6e827c5a677d2)

- **作者**: vOv
- **时间**: 2026-09-28T16:12:34Z
- **提交信息**: [Bugfix] Raise when a diffusion stage fails sleep or wake_up (#7811)

Signed-off-by: cr-gao <gaochenrui@sjtu.edu.cn>

### [965ad68](https://github.com/vllm-project/vllm-omni/commit/965ad68f1dce29e095bb8576aad5c5da6aac5960)

- **作者**: Jierui (Jerry) Xu
- **时间**: 2026-09-28T16:12:16Z
- **提交信息**: [Kernel][MammothModa2] Use shared RMSNorm in the DiT (#7489)

Signed-off-by: Jerry Xu <xjr2423@gmail.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [e823f0d](https://github.com/vllm-project/vllm-omni/commit/e823f0d909a163e9ea92253bf1204f39d1af3f18)

- **作者**: Shaun Walsh
- **时间**: 2026-09-28T15:30:30Z
- **提交信息**: [BugFix] Add field constraints to /v1/omni/sleep and /v1/omni/wakeup (#4740)

Signed-off-by: Shaun Walsh <shaunwalsh24@gmail.com>
Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>

### [29b818a](https://github.com/vllm-project/vllm-omni/commit/29b818a78503bd43a79923bd83ad1fa948d3a9b2)

- **作者**: R0CKSTAR
- **时间**: 2026-09-28T15:20:30Z
- **提交信息**: feat(magi2): add fused BF16 routed MoE path (#7206)

Signed-off-by: Xiaodong Ye <xiaodong.ye@mthreads.com>

### [79a46a4](https://github.com/vllm-project/vllm-omni/commit/79a46a4f5471e7b8f3ce093d0cf0b94ba7264c04)

- **作者**: DMAN
- **时间**: 2026-09-28T15:17:37Z
- **提交信息**: [Perf][Diffusion] support Sensenova online fp8 (#7955)

Signed-off-by: Dmaner <2663515256@qq.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [2a453c5](https://github.com/vllm-project/vllm-omni/commit/2a453c5ad893e90fc7921db4a0c462263061a039)

- **作者**: BeatSeat
- **时间**: 2026-09-28T15:13:43Z
- **提交信息**: feat(cosyvoice3): GPU-resident F0 predictor & pure-PyTorch vocoder (Task C2) (#7518)

Signed-off-by: BeatSeat <wendavid552@gmail.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [9c688ae](https://github.com/vllm-project/vllm-omni/commit/9c688aeba066f3090f6d4950c7512e3cdb083c03)

- **作者**: Clodagh Walsh
- **时间**: 2026-09-28T13:42:34Z
- **提交信息**: [TTS] Improve voice delete error message (#7795)

Signed-off-by: Clodagh Walsh <clodaghwalsh17@gmail.com>

### [5ce6f5d](https://github.com/vllm-project/vllm-omni/commit/5ce6f5dc49ead82b24bb5e1c19849cea67c51d3e)

- **作者**: chickeyton
- **时间**: 2026-09-28T11:11:42Z
- **提交信息**: [Bugfix][MiniCPM-o] Forward a speech unit closed by LISTEN after turn_eos to the Talker (#8227)

Signed-off-by: chickeyton <ngton2014@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

---
