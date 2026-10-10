# GitHub Stars 合并报告 - 2026-10-09

**合并日期**: 2026-10-10
**监控日期**: 2026-10-09
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


**报告日期**: 2026-10-10
**监控日期**: 2026-10-09
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2235
- **最后更新**: 2026-10-09T08:55:55Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Coach257, Albert Zhang

## AI分析总结

## 1. 主要更新类型

- **文档更新**：记录 Ascend 容器使用中的安全风险与注意事项。
- **功能新增 + 文档配套**：新增 `ShardedEmbedding`——基于词表分片（vocab-sharded）的 all-to-all 通信嵌入实现。

## 2. 关键变更点及与项目方向的关系

- **ShardedEmbedding**：将大词表嵌入表切分到多个设备，通过 all-to-all 通信按需获取所需 embedding，而非每张卡复制完整嵌入表。这与 VeOmni "Model-Centric 分布式配方库" 的核心定位高度一致——把分布式训练策略沉淀为可复用组件，降低大规模多模态模型（尤其是带巨大词表的 LLM/VLM）的显存开销。
- **Ascend 安全文档**：明确昇腾容器环境的已知风险与缓解措施，表明项目在国产硬件（NPU）适配上已从"能跑"走向"工程化合规"阶段。
- 两个提交分别对应"能力扩展"和"生态稳健性"，是并行推进的两条线。

## 3. 对项目的影响和潜在意义

- **训练规模上限提升**：嵌入表往往是 LLM 参数与显存的最大单体之一（词表千万级时尤为突出），分片化后单卡可承载更大词表或多模态并集词表，直接影响可训练模型规模。
- **降低多模态融合成本**：多模态模型需合并文本、代码、多语言等词表，ShardedEmbedding 使词表扩张不再线性增加每卡显存。
- **增强企业/生产可用性**：Ascend 安全文档减少用户在受限环境部署的踩坑成本，扩大在国产算力集群中的落地可行性。
- **配套文档同步**：说明该特性按开源项目规范交付（代码 + 说明 + PR 讨论），利于社区采纳。

## 4. 值得关注的技术点

- **词表分片策略**：如何按词频/均匀切分，以及非均匀分布对 all-to-all 负载均衡的影响。
- **all-to-all 通信实现**：是否兼容 PyTorch 原生分布式后端与 Ascend HCCL，通信与前向计算的 overlap 优化程度。
- **与 ZeRO/FSDP 的叠加**：分片嵌入与已有的分片优化器是否存在冗余或冲突，VeOmni 的配方库如何编排。
- **安全性边界的表述**：Ascend 容器风险涉及镜像来源、特权权限、网络隔离等，值得在自身环境中对照检查。

## 5. 对项目发展的综合影响

结合 README，VeOmni 的目标是为任意模态模型训练提供可扩展的分布式配方集合。本次第 1/1 批提交虽只有两条，却分别补强了两个关键维度：

- **技术纵深**：ShardedEmbedding 把"大词表 + 多模态"这一核心场景的分布式方案补齐，强化了"任何模态"的承诺，也让配方库从通信并行、优化器分片延伸到模型结构内部的分片。
- **生态广度**：Ascend 安全文档延续了项目对国产硬件适配的投入，配合已有 NPU 支持，形成"功能可用 + 风险透明"的完整叙事，有助于在合规敏感的行业场景推广。

总体看，这批提交属于"稳步扩展能力边界 + 巩固工程可信度"的健康节奏，为后续发布更大规模多模态模型配方和更广泛硬件适配奠定了基础。后续值得持续关注 ShardedEmbedding 的性能基准、与更多后端（Ascend/其他 NPU）的适配进展，以及在实际配方中的默认启用策略。

## 详细提交记录

### [b0a4543](https://github.com/ByteDance-Seed/VeOmni/commit/b0a4543687202e5777c30ef9d9835a9b776e152b)

- **作者**: Albert Zhang
- **时间**: 2026-10-09T08:55:49Z
- **提交信息**: [docs] chore: document Ascend container security risks (#1272)

### [6438cbe](https://github.com/ByteDance-Seed/VeOmni/commit/6438cbe3cb5ac1ebf314213a7e6c71d59d5db1ab)

- **作者**: Coach257
- **时间**: 2026-10-09T08:05:00Z
- **提交信息**: [dist, omni, docs] feat: add ShardedEmbedding, a vocab-sharded all-to-all embedding (#1213)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-10-10
**监控日期**: 2026-10-09
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2889
- **最后更新**: 2026-10-09T10:57:01Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Chernobyllight, Musisoul

## AI分析总结

## LightX2V 昨日提交分析（1/1批）

### 1. 主要更新类型
- **Bug修复**：修复音频引用计数问题（audio reference count），解决资源管理层面的内存泄漏或提前释放隐患。
- **重构**：大规模整理连续块（contiguous block）offload机制与模型启动脚本布局，属于结构性整理而非功能新增。

### 2. 关键变更点及其与项目方向的关系
- **统一offload后端与权重存储**：将分散的offload实现收敛为更一致的代码结构，简化block分组管理。这与LightX2V"轻量化视频生成推理"的核心目标直接契合——offload是低显存场景下推理的关键技术。
- **重组启动脚本目录**：Wan、Qwen Image、MiniMax-H3三个基线模型的启动器被统一归入`scripts/<model>/offload_layout/`，形成规范化的目录结构，便于用户按模型查找offload配置。
- **文档聚焦化**：中英文指南精简为权重准备、GPU/NPU命令和输出位置三项核心内容，并明确MiniMax-H3所需的AdaLN缓存，降低用户上手门槛。
- **NVIDIA平台初始化被刻意保留**，说明重构以向后兼容为前提。

### 3. 对项目的影响和潜在意义
- 目录规范化后，后续新增模型（如更多基线）可以直接沿用`offload_layout`模式，**降低了项目长期维护和社区贡献的摩擦成本**。
- 音频引用计数修复虽小，但对涉及音频条件的视频生成管线是稳定性保障，避免潜在的显存/内存异常。
- 作者中包含Codex协作，反映出项目已在采用AI辅助工具进行工程重构，这与LightX2V团队（ModelTC）一贯的高效工程风格一致。

### 4. 值得关注的技术点
- **offload的统一抽象**：合并多个后端实现意味着可能设计了更通用的权重搬运接口，值得深入阅读具体diff了解其抽象层次。
- **AdaLN缓存的显式文档化**：MiniMax-H3（一种DiT类架构）的自适应LayerNorm缓存成为用户必须知晓的要素，暗示该模型的offload流程比其他模型更复杂。
- **验证策略**：提交说明明确指出仅做了shell语法和dry-run参数校验，未重跑完整推理，属于"目录与文档变更"的安全边界判断——这种透明的验证声明值得借鉴。

### 5. 对项目发展的综合影响
LightX2V定位为轻量视频生成推理框架，其竞争力在于多模型支持与低显存推理方案的易用性。本次提交从**工程整洁度和用户引导**两个维度强化了这一竞争力：目录结构的规范化使多模型offload配置一目了然，文档精简让目标用户（需要在消费级GPU或NPU上跑视频生成的开发者）能更快完成环境搭建。结合项目已提供的英文文档站和DeepWiki集成，这类基础设施层面的梳理虽不产生可见的新功能，却是**从个人项目向可持续开源生态过渡的重要一步**，为未来接入更多模型和硬件后端（如NPU支持的扩展）铺平了道路。总体而言，这是一次质量高于炫技的提交，体现了成熟开源项目的迭代节奏。

## 详细提交记录

### [b6d3828](https://github.com/ModelTC/LightX2V/commit/b6d38283cb8176303f9155e639bcd496553d3402)

- **作者**: Musisoul
- **时间**: 2026-10-09T10:04:46Z
- **提交信息**: fix: audio refrence count (#1585)

### [913a974](https://github.com/ModelTC/LightX2V/commit/913a974d9b985cee12155c103fd20f12660966d4)

- **作者**: Chernobyllight
- **时间**: 2026-10-09T08:05:55Z
- **提交信息**: Refactor contiguous block offload and organize model launchers (#1570)

Consolidate offload backends and weight storage, simplify block group
management, and streamline the model launchers while preserving NVIDIA
platform initialization.

Organize the Wan, Qwen Image, and MiniMax-H3 baseline and contiguous
launchers under `scripts/<model>/offload_layout/`. Keep the English and
Chinese guides focused on weight preparation, GPU/NPU commands, and
output locations, including the required MiniMax-H3 AdaLN cache. Update
the integration skill links to match the new paths.

Validation for this update: all 12 launchers pass shell syntax and
dry-run argument checks; their contents and executable modes are
unchanged by the move. All 14 README shell examples and the updated
links were checked, and formatting checks passed. Full model inference
was not rerun for this directory and documentation change.

---------

Co-authored-by: liuhongda <liuhongda@sensetime.com>
Co-authored-by: helloyongyang <yongyang1030@163.com>
Co-authored-by: Codex <codex@openai.com>

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-10-10
**监控日期**: 2026-10-09
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2287
- **最后更新**: 2026-10-09T14:49:40Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-10-10
**监控日期**: 2026-10-09
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6579
- **最后更新**: 2026-10-09T23:13:09Z

## 提交统计

- **昨日提交总数**: 10
- **提交者数量**: 7
- **主要提交者**: Vincent, Emil Gilliam, Adrian

## AI分析总结

## FlashInfer 昨日提交分析总结

### 1. 主要更新类型
- **功能新增**：多个新量化与激活函数支持（W4A8、CuTeDSL MegaMoE、SwiGLU StepFun、ClampedRelu2 激活融合）
- **Bug/路由修复**：SM107（Rubin）上 MXFP8 CuTeDSL kernel 误用 SM100 kernel 的修复
- **重构与测试优化**：多项测试参数矩阵剪枝、cuDNN LSE 输出格式统一
- **依赖升级**：nvidia-cudnn-frontend 提升至 >=1.31.0

### 2. 关键变更点及与项目方向的关系
FlashInfer 的核心目标是提供**高性能 GPU 推理 kernel**，本次提交从三条主线推进该目标：

- **硬件覆盖扩展**：新增 SM120（RTX Pro 5000）W4A8 MegaMoE 后端（MXFP4 权重 × MXFP8 激活），并修复 SM107 Rubin 上 `mm_mxfp8` 的 autotuning 路由，确保新一代 GPU（Rubin、Blackwell 系列）能发挥专用 kernel 性能。
- **量化与激活融合深化**：CUTLASS MoE 后端融合 Nemotron 所需的 tanh-clamped squared ReLU 激活到 GEMM1 epilogue，避免中间结果物化；TRTLLM Gen SwiGLU StepFun 支持 BF16/FP8/MXFP8/NVFP4 四种精度，覆盖主流 MoE 推理需求。
- **cuDNN 后端整合**：linear attention 状态池与 KDA/GDN 自动调度整合，prefill 返回符合 FlashInfer API 契约的 packed LSE（ragged Stats），统一了与 cascade/merge kernel 的接口。

### 3. 对项目的影响和潜在意义
- **性能提升**：MoE 激活融合在 GB300 上实测显著优于 vLLM 式 grouped-GEMM；Rubin kernel 路由修复直接释放新硬件算力。
- **生态兼容**：StepFun、ClampedRelu2 等激活支持 Nemotron、StepFun 等模型家族，降低用户集成成本。
- **测试基建**：6 项测试参数矩阵剪枝（pairwise 覆盖 + `--full` 全量模式）在不损失覆盖率的前提下大幅缩短日常 CI 时间。
- **API 一致性**：LSE 格式统一修复了下游 cascade/merge kernel 无法消费 cuDNN 输出的隐患。

### 4. 值得关注的技术点
- **SM107/SM100 kernel 解耦**：为 SM107 独立 `TunableRunner` 和 tactic 枚举，含 `can_implement` 过滤与 MXFP8 MMA 形状约束，架构清晰。
- **W4A8 MegaMoE**：利用 SM120 混合块缩放 QMMA（E2M1×E4M3, m16n8k32），保留通信/计算重叠与 CUDA Graph 支持，但跨 NUMA IBGDA 集成尚待后续。
- **cuDNN ragged Stats**：让 cuDNN 直接写入 packed 缓冲区，消除 padding 与后续 gather；对非连续 q 视图（T3HD）的偏移修正体现了细节严谨性。
- **有界自动调度**：仅在构建阶段声明的 decline 才允许回退，执行错误直接传播，GB200 上 555 项测试全通过。

### 5. 对项目发展的影响
FlashInfer 正加速成为**多架构（SM100/SM107/SM120）、多精度（FP4/FP8/MXFP8/NVFP4）、多模型族（Dense/MoE/Linear Attention）**的统一高性能推理 kernel 库。本次提交补齐了 Rubin/SM120 硬件路径、主流 MoE 激活函数与 cuDNN 线性注意力整合，同时通过系统性测试剪枝改善工程效率，为其作为 vLLM 等框架底层算子库的定位进一步巩固了竞争力。

## 详细提交记录

### [65b2b94](https://github.com/flashinfer-ai/flashinfer/commit/65b2b946bc76fbf79485607ad1f161afc35eacd7)

- **作者**: Adrian
- **时间**: 2026-10-09T23:12:55Z
- **提交信息**: test: prune FP4 quantization parameter matrix (#5426)

## 📌 Description

Convert the Cartesian parameter matrix or matrices in
`tests/utils/test_fp4_quantize.py` to `parametrize_product`. Regular
pytest runs use deterministic pairwise coverage, while `pytest --full`
retains the exhaustive matrices for nightly testing.

## 🔍 Related Issues

N/A

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] Repository commit hooks passed for the modified file.

## 🧪 Tests

- [x] Python compilation and diff validation passed.

## 🔬 Experimental Track

- [ ] This PR is experimental.

## Reviewer Notes

This PR intentionally changes only one test file so each pruning
candidate can be reviewed independently.

### [2a2ccea](https://github.com/flashinfer-ai/flashinfer/commit/2a2cceab07c7bfca0525065fbfdc5fb2cff0c33a)

- **作者**: Adrian
- **时间**: 2026-10-09T20:13:37Z
- **提交信息**: test: prune GDN decode parameter matrices (#5422)

## 📌 Description

Convert the Cartesian parameter matrix or matrices in
`tests/gdn/test_decode_delta_rule.py` to `parametrize_product`. Regular
pytest runs use deterministic pairwise coverage, while `pytest --full`
retains the exhaustive matrices for nightly testing.

## 🔍 Related Issues

N/A

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] Repository commit hooks passed for the modified file.

## 🧪 Tests

- [x] Python compilation and diff validation passed.

## 🔬 Experimental Track

- [ ] This PR is experimental.

## Reviewer Notes

This PR intentionally changes only one test file so each pruning
candidate can be reviewed independently.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Tests**
* Updated coverage for delta-rule decoding and FP32 scatter scenarios to
organize existing parameter combinations more consistently. The same
test cases remain covered; no user-facing behavior changes are included
in this update.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [1413635](https://github.com/flashinfer-ai/flashinfer/commit/14136353ca6ed83ef4a347e3e580ce9556111b88)

- **作者**: Vincent
- **时间**: 2026-10-09T18:19:06Z
- **提交信息**: fix(gemm): use the SM107 CuTe-DSL kernel for mm_mxfp8(backend="cute-dsl") on Rubin (#6136)

<!-- .github/pull_request_template.md -->

## 📌 Description

On SM107 (Rubin), `mm_mxfp8(backend="cute-dsl")` never used the Rubin
CuTe-DSL kernel. It
autotuned, and defaulted to, only the SM100 kernels:
`Sm100BlockScaledPersistentDenseGemmKernel`
and its split-K variant. `Sm107BlockScaledPersistentDenseGemmKernel`
documents MXFP8 support but
was wired only into `mm_fp4`.

With this PR, on SM107:
- **Autotuning** covers only the SM107 kernel's tactics.
- **Without autotuning**, the default tactic is an SM107-kernel tactic.

The SM100 kernels remain only as a fallback for inputs the SM107 kernel
cannot run: a
non-contiguous output, or N not a multiple of 8. Other architectures are
unchanged.

Changes:

- `flashinfer/gemm/gemm_base.py`:
- Adds `_cute_dsl_gemm_mxfp8_sm107_runner`, a separate `TunableRunner`
for the SM107 kernel
with its own tactic format `(mma_tiler_mn, cluster_shape_mn, swap_ab,
mma_inst_shape_m)`
    and its own compiled-kernel cache.
    - `get_valid_tactics` returns `_get_sm107_mxfp8_tactics`.
- The untuned default comes from
`_select_sm107_mm_mxfp8_cute_dsl_tactic`.
- `mm_mxfp8`'s `"cute-dsl"` factory picks the SM107 runner via
`_use_sm107_mxfp8_cute_dsl`:
SM107, a contiguous `out`, N % 8 == 0, K % 16 == 0, and the SM107 kernel
importable (guarded
import, cached in `_sm107_mxfp8_cute_dsl_kernel`). Otherwise it uses the
existing SM100
    runner.
- `_cute_dsl_gemm_mxfp8_runner` (the SM100 runner) is unchanged from
main.
- `flashinfer/gemm/kernels/utils.py`:
- Adds `_get_sm107_mxfp8_tactics`, the SM107 tactic enumeration shared
by the runner and
the untuned selector. The candidates are: MMA tile in {128, 256, 512} x
{64, 128, 192,
256}; MMA instruction M in {128, 256}; the cluster shapes; swap-AB. Each
is filtered by
the kernel's `can_implement` with the MXFP8 MMA shape (instruction K 64,
K tile 128). A
512-row tile runs as two 256-row MMAs per CTA (B-reuse). The 512-row
tiles are in an
    MXFP8-only list, so the `mm_fp4` SM107 selector is unchanged.
- Adds `_select_sm107_mm_mxfp8_cute_dsl_tactic`, which picks one SM107
tactic per M bucket
and caches it per (N, K, SM count), like the `mm_fp4` selectors. It
ranks the enumerated
tactics whose MMA instruction M equals the tile M with the existing
scorer, renamed
from `_score_mm_fp4_tactic` to `_score_block_scaled_tactic` because it
reads only tile,
    cluster and swap-AB, never the data type.
- Renames `_SM100_CLUSTER_SHAPE_MN_CANDIDATES` to
`_CLUSTER_SHAPE_MN_CANDIDATES`. The list
{1, 2, 4} x {1, 2, 4} is also exactly the SM107 kernel's valid cluster
set: power-of-two
dimensions, at most 4 each, product at most 16. The `mm_fp4` uses are
renamed too, with
    no behavior change.
- `flashinfer/gemm/kernels/dense_blockscaled_gemm_sm107.py`,
FlashInfer-side shims only (the
  TRT-LLM-synced kernel body is untouched):
- `can_implement` takes an `mma_tiler_k` argument. It defaults to 256,
so FP4 callers are
    unchanged; MXFP8 passes 128.
- `wrapper` accepts float8 A/B in addition to packed-uint8 FP4,
mirroring the SM100
    `wrapper` (`dense_blockscaled_gemm_sm100_common.py`).

Before/after, `mm_mxfp8(backend="cute-dsl")`, bf16 output:
- **Hardware:** GR100 lab board, SM107, 208 SMs, SM clock locked at 2424
MHz, no other GPU
  process during the runs. The shapes include odd M (1, 3, 100, 129).
- **Software:** FlashInfer `upstream/main` `125c989e0` vs this branch,
nvidia-cutlass-dsl
  4.8.0a0.
- **Timing:** CUPTI with CUDA graphs
(`flashinfer.testing.bench_gpu_time`, 20 warm-up and 100
  timed iterations, cold L2), median per shape.
- **Columns:** "untuned" is the call outside `autotune()`; "autotuned"
is the call after
`with autotune(True)`. Each column compares that mode against the same
mode on main.

| M | N | K | untuned speedup | autotuned speedup |
|---:|---:|---:|---:|---:|
| 1 | 1536 | 6144 | 1.50x | 1.08x |
| 3 | 1536 | 6144 | 1.51x | 1.12x |
| 8 | 1536 | 6144 | 1.52x | 1.13x |
| 64 | 1536 | 6144 | 2.03x | 1.62x |
| 100 | 1536 | 6144 | 1.90x | 1.60x |
| 129 | 1536 | 6144 | 1.95x | 1.59x |
| 256 | 1536 | 6144 | 1.97x | 1.60x |
| 1024 | 1536 | 6144 | 1.44x | 1.29x |
| 4096 | 1536 | 6144 | 1.16x | 1.08x |
| 8192 | 1536 | 6144 | 1.34x | 1.26x |
| 1 | 4096 | 4096 | 1.45x | 1.16x |
| 3 | 4096 | 4096 | 1.46x | 1.16x |
| 8 | 4096 | 4096 | 1.45x | 1.15x |
| 64 | 4096 | 4096 | 1.82x | 1.49x |
| 100 | 4096 | 4096 | 1.77x | 1.49x |
| 129 | 4096 | 4096 | 1.63x | 1.40x |
| 256 | 4096 | 4096 | 1.63x | 1.41x |
| 1024 | 4096 | 4096 | 1.42x | 1.14x |
| 4096 | 4096 | 4096 | 1.23x | 1.17x |
| 8192 | 4096 | 4096 | 1.50x | 1.24x |
| 1 | 6144 | 1536 | 1.50x | 1.40x |
| 3 | 6144 | 1536 | 1.48x | 1.37x |
| 8 | 6144 | 1536 | 1.48x | 1.38x |
| 64 | 6144 | 1536 | 1.65x | 1.49x |
| 100 | 6144 | 1536 | 1.65x | 1.46x |
| 129 | 6144 | 1536 | 1.59x | 1.49x |
| 256 | 6144 | 1536 | 1.54x | 1.46x |
| 1024 | 6144 | 1536 | 1.07x | 1.25x |
| 4096 | 6144 | 1536 | 1.29x | 1.06x |
| 8192 | 6144 | 1536 | 1.30x | 1.14x |
| 1 | 7168 | 2048 | 1.43x | 1.29x |
| 3 | 7168 | 2048 | 1.43x | 1.30x |
| 8 | 7168 | 2048 | 1.45x | 1.26x |
| 64 | 7168 | 2048 | 1.61x | 1.50x |
| 100 | 7168 | 2048 | 1.61x | 1.46x |
| 129 | 7168 | 2048 | 1.45x | 1.48x |
| 256 | 7168 | 2048 | 1.46x | 1.44x |
| 1024 | 7168 | 2048 | 1.24x | 1.26x |
| 4096 | 7168 | 2048 | 1.29x | 1.09x |
| 8192 | 7168 | 2048 | 1.42x | 1.12x |

The table was measured before the 512-row tiles were added; with them
the autotuned results on
these shapes are unchanged within noise (see Reviewer Notes). Speedup =
main time / this PR's
time (>1 = this PR is faster). Over these 40 shapes, untuned geomean is
**1.50x** (min 1.07x, max 2.03x) and autotuned geomean is **1.31x** (min
1.06x, max 1.62x). No shape is slower than main in either mode, and
output cosine similarity against a bf16 reference is 0.9993 in every
case. Autotuned results on this board repeat within about ±10% from run
to run, so treat small autotuned differences as noise.

## 🔍 Related Issues

Fixes #6088.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [ ] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

(So far only `ruff check` and `ruff format`, pinned 0.12.8 as in
`.pre-commit-config.yaml`, have
been run on the changed files.)

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

New test in `tests/gemm/test_mm_mxfp8.py`:
`test_mm_mxfp8_cute_dsl_sm107`, marked
`@pytest.mark.arch_rubin` and skipped when
`is_rubin_cute_dsl_available()` reports no Rubin support in
the installed CuTe DSL.
- **Coverage:** six shapes, including odd M (1, 100, 129) and K % 128 !=
0 (544, 2080), each run untuned
  and autotuned through `mm_mxfp8(backend="cute-dsl")`.
- **Assertions:**
  - The output matches a bf16 reference.
- The SM107 runner ran, recorded through its factory: untuned, exactly
once with the default
    tactic; autotuned, last with a tuned SM107 tactic.
- Untuned only: every SM107 tactic for the shape also matches the
reference, because autotuning only
    checks the tactic it picks.
- **Runtime:** 12 cases, about 2.5 minutes on GR100. Almost all of it is
the first case compiling every
  SM107 tactic once; the other cases take seconds.

Ran on the same GR100 board (SM107), in the `rubin-latest` CI image:
- `pytest tests/gemm/test_mm_mxfp8.py -k cute`: **530 passed**, 0
failed, 0 skipped.
- `pytest tests/gemm/test_mm_fp4.py -k cute`: **30 passed**, 40 skipped.
All 40 skips are the
existing "per-token alpha needs the cute-dsl FP4 GEMM (SM100/SM103)"
skip. This file covers
  the FP4 path through the edited SM107 `wrapper`.
- Probe outside pytest: all 240 SM107 tactics were run directly at M/N/K
= 256/1536/6144,
1000/4096/1024, 100/1536/1024 and 3/4096/1024. Minimum cosine similarity
against the bf16
  reference was 0.99926, with 0 failures.
- At K = 160, 544, 1056, 2080 and 6176 with M = 1, 100 and 256, one
tactic per tile group
    also matched. So did main's SM100 path, with identical results.

## Reviewer Notes

- **Behavior change on SM107 only:** both the autotune candidate set and
the untuned default
of `mm_mxfp8(backend="cute-dsl")` move from the SM100 kernels to the
SM107 kernel. SM100,
  SM103 and other architectures take the same code path as before.
- **Why SM100 is dropped on SM107:** in a first pass that autotuned over
SM100 and SM107 tactics
together, an SM107 tactic won all 24 shapes above, and the autotuned
results are the same
with or without the SM100 candidates. Dropping them also keeps cold
autotuning in check.
`mm_mxfp8` has no on-disk CuTe-DSL kernel cache, so a fresh process
autotuning 4 shapes
compiles every candidate; this takes **about 1.1x main's wall time**.
Offering both kernel
  families took about 1.8x main.
- **512-row tiles:** added for workloads outside this benchmark.
- On the shapes above they are performance-neutral: autotuned geomean
1.00x with versus
without them (0.95x-1.05x, within run-to-run noise), and the autotuner
picks one for
    several large-M shapes.
- They add 48 candidates per shape, about 25% more cold-autotuning time.
- The untuned default never selects them, because it only considers
tactics whose MMA
    instruction M equals the tile M.
- **SM100 fallback:** stays for the cases the SM107 kernel cannot
express: N % 8 != 0, K % 16
!= 0, or a non-contiguous output. A non-contiguous `out` is mishandled
by the cute-dsl and
  cutlass paths on main as well; that is tracked separately in #6210.
- **Swap-AB at any M:** swap-AB does not need M % 8 == 0. The kernel's
16-byte alignment rule
applies to each tensor's contiguous dimension: K for A and B, and N for
the output in both
orientations, because swap-AB writes the same row-major `(M, N)` buffer
through a
column-major `(N, M)` view. Allowing it at odd M makes the untuned
default at M = 1 and 3
  about 1.8-1.9x faster than restricting it.
- **Separate SM107 runner:** the SM100 and SM107 kernels have their own
runners and tactic
formats instead of sharing one tuple. So the SM100 runner is main's
code, and the autotune
cache keys the two by runner class: persisted SM100 tactics keep
working, and SM107 results
  cannot collide with them.
- The SM107 runner repeats about 35 lines of the SM100 runner's
compile-and-launch sequence
    rather than refactoring main's runner into a shared helper.
- The SM107 kernel takes no `enable_pdl`, so PDL does not apply on
SM107.
- **Prefetch:** `prefetch_dist` is fixed at the kernel default (0). In a
first pass that also
  offered `prefetch_dist=None`, it never won.
- **Scorer:** the untuned selector reuses the existing block-scaled
scorer rather than adding
  an MXFP8-specific model (see the accuracy note under the table).
- Its constants were calibrated on `mm_fp4`, so
`_MM_FP4_SWAP_PENALTY_MAX_M` keeps its name.
- It models every 256-row tile as a 2-CTA MMA, so the untuned default
never picks B-reuse
(a 256-row tile issued as two 128-row MMAs by one CTA). The autotuner
still does, and
    sometimes picks it.
- **`backend="auto"` unchanged:** it still resolves to `cutlass` for
`mm_mxfp8`; this PR does
  not change backend selection.

AI-assisted (Claude Code).

---------

Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [c1af49e](https://github.com/flashinfer-ai/flashinfer/commit/c1af49ecbad5433d4332aaec986d1a3bd1e1e610)

- **作者**: Emil Gilliam
- **时间**: 2026-10-09T17:12:56Z
- **提交信息**: cudnn prefill: return a packed LSE, declared as ragged Stats (#5161)

<!-- .github/pull_request_template.md -->

## 📌 Description

`cudnn_batch_prefill_with_kv_cache(..., return_lse=True)` returns the
packed LSE that FlashInfer's API documents, `(total_qo_tokens,
num_qo_heads)`, and declares it to cuDNN as a **ragged Stats tensor**
over the query token indptr, the same packing as `q`. A caller-provided
padded `(batch, max_token_per_sequence, num_qo_heads)` buffer is still
accepted. Built on the prepared-plan flow from #5350.

**Why.** FlashInfer's LSE contract is a packed `[qo_len, num_qo_heads]`
tensor: the wrappers allocate that shape, the cascade / merge kernels
consume it, and every other backend returns it. Since #5350 both
wrappers already plan a ragged Stats offset; the low-level function
still defaulted to the padded per-request block, a shape nothing
downstream accepts. A ragged Stats tensor lets cuDNN write each
request's rows straight into the packed buffer, with no padding rows and
no gather afterwards.

**Change.** `flashinfer/cudnn/prefill.py`
- `lse=None` allocates the packed buffer on the cuDNN graph path; the
`"cubin"` backend keeps the padded form it writes.
- A passed-in `lse` must be contiguous float32 on `q`'s device, packed
or padded; `batch_offsets_stats` with a padded `lse` is rejected (the
offsets address packed rows). A passed-in `out` must be contiguous on
`q`'s device. Both are checked before the graph binds them.
- For a packed LSE the Stats offsets are derived when omitted: the
token-unit q indptr, `batch_offsets_q // q.stride(0) * h_qo` for element
units, or a device-built `[0, total]` for a single request (CUDA-graph
capturable).
- `_PrefillMetadata.resolve` scales element offsets by each tensor's
real token stride, so a non-contiguous `q` (a T3HD view) addresses
correctly on the conversion path, matching the direct path's
multipliers.
- **Single-token GQA on cuDNN < 9.27.** The `s_q == 1` GQA kernel
mis-stores a ragged Stats tensor there: most heads of a packed LSE are
never written (fixed in cuDNN 9.27.0). When every request has exactly
one token, the unragged `(b, h, 1, 1)` Stats declaration is
byte-identical to the packed buffer, so
`_PrefillMetadata.bind_single_token_stats_unragged` drops the Stats
offset for those plans. Both wrappers' plans and the public function
apply it. Native head-major Stats (`lse_layout="HN"`) needs the ragged
offset to place tokens, so such plans stage NH and transpose instead.
The only shape it cannot serve is a batch that mixes zero-length and
one-token requests.

`flashinfer/prefill.py`
- The ragged wrapper's `auto` gate and explicit-cudnn `return_lse` guard
from #5245, and the paged wrapper's refusal from #5350, narrow to that
one unservable shape on affected cuDNN. `auto` now keeps cuDNN for
ordinary single-token GQA rows, LSE included.

**Behaviour change to flag:** low-level callers passing
`return_lse=True, lse=None` receive the packed 2-D LSE instead of the
padded 3-D one. The trace template already documented `["num_tokens",
"num_heads_qo"]`. Callers that pass their own padded buffer are
unchanged. vLLM and SGLang call the low level and discard the LSE.

## 🔍 Related Issues

Deferred from #4663; builds on #5133, #5245 and #5350;
NVIDIA/cudnn-frontend#1023, #1036.

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

`tests/attention/test_cudnn_prefill_lse_layout.py` (new): packed by
default on both unit paths × batch 1/4 × causal, per token against a
float reference; an explicit padded buffer still works; non-contiguous
`q`; single-token GQA and MHA, ragged and paged, at the low level and
through both wrappers in `NH` and `HN` layouts, each with a NaN-poisoned
LSE buffer; a single request with no offsets captured into a CUDA graph;
wrong shape, dtype, contiguity and padded-plus-offsets each rejected.
Updated: `test_cudnn_prefill_lse_is_base2` for the packed shape; the
#5245 single-token tests and #5350's
`test_paged_single_token_gqa_rejects_incomplete_lse` become correctness
tests; the strict xfail `test_cudnn_single_token_gqa_lse_is_correct`
becomes a plain test.

Local, 2026-10-07, cudnn-frontend 1.31, on current main, against public
cuDNN 9.24.0 (FlashInfer CI's pin; bug present, paged wrapper takes the
public-function path), public 9.26.0 (bug present, prepared-plan path)
and a 9.28 dev build (fixed):

| GPU | cuDNN | suites | result |
|---|---|---|---|
| H100 (sm90) | 9.24 / 9.26 / 9.28 | `test_cudnn_prefill*`,
`test_cudnn_prepared*`, wrapper regressions, graph cache key, ragged
shape override | 705 / 748 / 748 passed, 0 failed |
| B200-class (sm100) | 9.24 / 9.26 / 9.28 | `test_auto_backend_upgrade`,
LSE layout, wrapper regressions, prepared graph, ragged shape override |
210 / 227 / 226 passed, 0 failed |

## Reviewer Notes

The earlier review threads (Zhi's stride fix, Yang's single-token and
CUDA-graph findings, CodeRabbit's buffer checks) are all carried into
this single commit on the prepared-plan flow.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [8803e2f](https://github.com/flashinfer-ai/flashinfer/commit/8803e2fc2272892f0eac4b9859632f5e028d396e)

- **作者**: Anerudhan Gopal
- **时间**: 2026-10-09T15:23:06Z
- **提交信息**: feat: integrate cuDNN linear attention pools and bounded auto dispatch (#6259)

<!-- .github/pull_request_template.md -->

## 📌 Description

Integrate cuDNN linear-attention state pools, raw GDN gates, and bounded
SM100 auto dispatch on current main. Raise `nvidia-cudnn-frontend` to
`>=1.31.0`.

This follows merged #6218. The new frontend baseline is the released
`v1.31.0` tag (`51a3de73e122aeedafe68070acf3b7ff3970534e`). KDA and GDN
use its fixed additive normalization. The retired epsilon API argument
is not reintroduced, and GDN does not add an external normalization
pass.

The imported policies retain their narrow shape, layout, state and
runtime checks. Only marked pre-execution build declines may fall back;
execution errors propagate. State pools stay explicit and require
unique, in-range slots.

**GB200 validation complete:** 555 scoped tests passed, with zero
failures, errors or skips. Fresh Lyris baseline/candidate
microbenchmarks and all 2,880 new GPU traces passed audit. Results and
limits are below.

## 🔍 Related Issues

Original work by @yanxu, retained through attributed commits:
- #6186: state pools and raw GDN gates.
- #6187: bounded KDA auto dispatch and build-decline caching.
- #6192: raw-gate GDN auto dispatch and benchmark route checks.

Existing work from #6078, #6183 and #6182 was merged through #6218 and
remains in the base. Native additive normalization comes from
NVIDIA/cudnn-frontend#1454, included in the frontend `v1.31.0` tag.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

Scoped `pre-commit run --files` passed for the full diff, including mypy
and Ruff. The all-files checkbox remains unchecked because unrelated
files were not checked.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

- Ten benchmark route-observation CPU tests passed with `pytest
--noconftest tests/kda/test_cudnn_linear_attention_benchmark.py -q`.
- Full local pytest collection is blocked by missing `tvm_ffi`; this is
not a GPU validation result.
- 555 scoped GPU/contract tests passed on Lyris GB200, including state
pools, raw gates, alias checks, auto fallback and changed-input replay.
This is scoped validation, not the full repository test suite.
- Four fresh timing-run numerical gates passed 144 case executions /
2,304 output and final-state tensor checks; two preliminary gates passed
another 1,152 tensor checks. Ordinary/tiny/zero Q/K and short/decode
references retain relative RMSE <3% OR maximum absolute error ≤1e-6.
- All 48 timing processes, 28,800 CPU samples and 2,880 GPU traces
passed external audit. CPU and GPU use separate processes; GPU kernels
must correlate to launches inside the measured caller scope. Every
repeat and range is retained.

### CI trace fix

Commit `e97930a47e5756eda9782bff4e009f06d5c546ed` derives GDP pool
output heads from required Q/V shapes when optional gates and states are
absent. Fifteen regression cases cover equal, grouped-query and
grouped-value heads through both the template and public trace API.
These and the two GDP trace-completeness checks pass on CPU; the same
checks reproduce 13 failures before the fix. The local check loads exact
source and test functions without CUDA package initialization or
unrelated registry imports; full CI remains separate. Scoped pre-commit,
including mypy and Ruff, passed.

The four inherited MoE pack-contract failures came from #5453
(`73b63f88`) and are fixed on main by #6264 (`fa7c741e`). This follow-up
changes only GDP trace metadata and tests. The branch is rebased on main
`a7103ae2`, which includes the MoE fix. All 14 PR patches are unchanged
by the rebase; the 17 CPU checks and scoped pre-commit pass again. The
GPU measurements below retain their original `669a153d` pin.

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

The source PRs predate fixed additive normalization. Their KDA epsilon
forwarding, old-attribute fallback and clamp references were removed.
Small-input checks retain the existing numerical tolerances. GDN now
delegates additive normalization to frontend 1.31.0.

Review pool ownership and pre-execution fallback boundaries. Existing
signatures retain their positional arguments; new gate options are
keyword-only. Auto selection can change the provider inside the
documented bounded region. No cuDNN source change or vLLM change is
included.

The current vLLM GDN caller passes precomputed gates. Its measured path
must remain distinct from new raw-gate API tests; a slower Torch gate
producer is not a substitute for vLLM's fused producer. GB200
measurements below retain that current vLLM caller boundary.


## GB200 microbenchmark results

Lyris job **3275022**, node `lyris0252`, completed in 55m55s. Same-node
baseline/candidate/candidate/baseline order. **B1 × 8,192-token
prefill**; cells are **active CPU / GPU kernel union (µs/call)**,
averaged over four fresh-process medians. These are operator timings,
not model TTFT.

| Model | vLLM auto | FlashInfer auto | FlashInfer cuDNN |
|---|---:|---:|---:|
| Kimi-K3 H6/TP16 | 91.216 / 319.663 | 213.388 / 115.296 | 156.604 /
111.760 |
| GLM-5.3 H16/TP4 | 163.516 / 457.645 | 285.176 / 340.012 | 158.200 /
184.161 |
| QwenNext Q8/V16/TP2 | 259.956 / 118.064 | 265.132 / 117.528 | 219.848
/ 129.161 |
| Qwen3.5 Q16/V32/TP1 | 272.872 / 179.055 | 277.384 / 179.354 | 230.468
/ 171.261 |

Kimi auto now uses cuDNN for this shape: GPU time changes
**199.566→115.296 µs (−42.23%)**, while CPU changes **173.512→213.388 µs
(+22.98%)**. GLM auto remains native. Qwen vLLM auto and FI auto select
the same native provider, with nearly unchanged GPU time; the current
precomputed-gate caller and Qwen head counts are outside the new raw-GDN
auto policy. Explicit cuDNN CPU is 4.14–6.73% lower at B1, but
unchanged-control CPU also shifts. These small sequential-run
differences do not isolate a branch effect or establish statistical
significance.

Measured commits:

- FlashInfer baseline: `461037fbf52227e6343ccbc9fc977337c1bf672b`.
- FlashInfer candidate: `669a153d63767d5f5ea3fc94b6b344f4f19c5faa`.
- vLLM caller: `29ad8bdac62250209d0e7c694eb0246f1882efab`.
- Frontend **v1.31.0**, both arms:
`51a3de73e122aeedafe68070acf3b7ff3970534e`.
- Harness: `894fc8cb5bf0b026b593aed06aa402198b2e71e5`.

Same frontend source/native wheel, cuDNN9.20, CuTe DSL4.7.1,
Torch2.13.0+cu132. BF16 KDA state and FP32 GDN state. Prefill B1/B8/B32
and shared one-token decode are included. Qwen fused gate/normalization
preparation is outside the timed call. CPU and GPU times must not be
added; no model accuracy equivalence or serving-latency claim is made.

[Full report, all rows/repeats/ranges, numerical checks and raw trace
archives](https://gitlab-master.nvidia.com/agopal/kda-vllm-microbench/-/blob/codex/kda-vllm-microbench/measurements/lyris-native-pools-3275022/report.md)
(NVIDIA GitLab access required).

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added indexed state-pool support for GDN, GDN-2, GDP, and eligible KDA
prefill, allowing selected state slots to be updated while others remain
unchanged.
* Added GDN options for log-domain gates, in-kernel gate computation,
and beta-logit conversion.
* Added automatic cuDNN routing for eligible GDN and KDA prefill
workloads, with fallback to existing backends when appropriate.
  * Added additive-epsilon Q/K normalization for cuDNN linear attention.
* **Documentation**
* Expanded guidance for state pools, gate options, backend selection,
and performance benchmarking.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yang Xu <yanxu@nvidia.com>

### [6dc4f76](https://github.com/flashinfer-ai/flashinfer/commit/6dc4f76598340a2ec6aaaaa8f7c925ea1d60f1d3)

- **作者**: helen ngo
- **时间**: 2026-10-09T14:44:24Z
- **提交信息**: feat(moe): fuse tanh-clamped squared relu in CUTLASS epilogues (#5696)

<!-- .github/pull_request_template.md -->

## 📌 Description

Nemotron uses a tanh-clamped squared ReLU activation function: `output =
(limit * tanh(relu(x) / limit))²`

The existing CUTLASS MoE backend supports squared relu but does not
support clamping. This change fuses the activation into the GEMM1
epilogue to avoid materializing the GEMM1 result. For MXFP8 it also
avoids launching a separate activation quantization pass.

This adds `ActivationType.ClampedRelu2` for the SM10x CUTLASS MoE
backend and fuses the activation into the GEMM1 epilogue for:
* BF16 activations × BF16 weights
* MXFP8 activations × MXFP8 weights, including GEMM2 block-scale
generation (used in NT4 inference)

It also filters autotuning to compatible activation-fusion tactics and
gives fused MXFP8 separate scratch buffers to avoid intrakernel
overwrite races.

**Performance**
Experiments run on Nemotron. 
<img width="1171" height="594" alt="Screenshot 2026-09-29 at 1 35 08 PM"
src="https://github.com/user-attachments/assets/2062bba0-db29-4351-be44-41f07945223f"
/>

<img width="1170" height="593" alt="Screenshot 2026-09-30 at 2 46 13 PM"
src="https://github.com/user-attachments/assets/20edd0f5-81e4-449d-8de5-250683b076fa"
/>
"vLLM" here denotes a vLLM-style grouped-GEMM implementation, not the
full e2e vllm.

These results were produced in Megatron Inference. 
- GPU: NVIDIA GB300, 4 GPUs with EP=4
- CUDA graphs enabled
- 256 forced decode tokens per request; EOS termination disabled
- FlashInfer setup autotuning completed before the measured interval
- No autotuning fallbacks occurred during measurement
- Reported values are medians of two fresh-process runs


**Tests + Verification**

Validated on GB300 with:
- Exact BF16 activation reference
- Random multi-expert BF16 reference
- Exact MXFP8 activation/quantization reference with BF16 outputs
- Invalid activation-parameter validation
- Token-count sweep from 1 -> 4096 tokens (manual)

**Notes**

- `ClampedRelu2 = 12` is intentionally placed after `InvalidType = 11`.
This preserves all existing activation
enum values and keeps the TRTLLM backend rejecting this CUTLASS-only
activation.
- The clamp limit is a model-wide one-element FP32 CUDA tensor.
- The initial implementation is limited to SM10x BF16×BF16 and
MXFP8×MXFP8 MoE without FC1 bias, LoRA, or min- latency mode.
- Determinism tests disable fused finalize because its atomic top-k
reduction is documented as nondeterministic.

## 🔍 Related Issues

TODO: link downstream Megatron-LM integration; can only be done after
this is available in a FlashInfer release.

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
* Added the ClampedRelu2 activation for supported MoE configurations on
SM10x, with BF16 and MXFP8 support.
* Eligible GEMM1 operations can now apply the activation directly,
including writing quantized MXFP8 output and activation scales.
* Added validation for the required positive scalar limit and
unsupported configuration combinations.
* Added tests covering activation results, input validation, MXFP8
quantization, and repeated autotuned calls.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Helen Ngo <helenn@nvidia.com>
Co-authored-by: Haobin Guo <haobing@nvidia.com>

### [b97624e](https://github.com/flashinfer-ai/flashinfer/commit/b97624ed102c0233c1df8e1d6bb9939d15933241)

- **作者**: Adrian
- **时间**: 2026-10-09T14:14:12Z
- **提交信息**: test: prune SM-constrained GEMM parameter matrix (#5424)

## 📌 Description

Convert the Cartesian parameter matrix or matrices in
`tests/gemm/test_sm_constraint_gemm.py` to `parametrize_product`.
Regular pytest runs use deterministic pairwise coverage, while `pytest
--full` retains the exhaustive matrices for nightly testing.

## 🔍 Related Issues

N/A

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] Repository commit hooks passed for the modified file.

## 🧪 Tests

- [x] Python compilation and diff validation passed.

## 🔬 Experimental Track

- [ ] This PR is experimental.

## Reviewer Notes

This PR intentionally changes only one test file so each pruning
candidate can be reviewed independently.

### [cbd37b2](https://github.com/flashinfer-ai/flashinfer/commit/cbd37b2274342bd0abb3453680924b1c9c157f4c)

- **作者**: Adrian
- **时间**: 2026-10-09T14:13:26Z
- **提交信息**: test: prune FP8 blockscale GEMM parameter matrix (#5423)

## 📌 Description

Convert the Cartesian parameter matrix or matrices in
`tests/gemm/test_fp8_blockscale_gemm.py` to `parametrize_product`.
Regular pytest runs use deterministic pairwise coverage, while `pytest
--full` retains the exhaustive matrices for nightly testing.

## 🔍 Related Issues

N/A

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] Repository commit hooks passed for the modified file.

## 🧪 Tests

- [x] Python compilation and diff validation passed.

## 🔬 Experimental Track

- [ ] This PR is experimental.

## Reviewer Notes

This PR intentionally changes only one test file so each pruning
candidate can be reviewed independently.

### [50829ac](https://github.com/flashinfer-ai/flashinfer/commit/50829ac2644704439260ac646067c0fc8c9bd0f5)

- **作者**: Euynaheh
- **时间**: 2026-10-09T10:35:52Z
- **提交信息**: [SM120] Add W4A8 CuTeDSL MegaMoE backend (#4632)

## Summary

This PR adds an SM120 CuTeDSL MegaMoE backend for:

- **Weights:** MXFP4 / E2M1
- **Activations:** MXFP8 / E4M3
- **Block scales:** E8M0 with K32 granularity
- **Accumulator:** FP32
- **Output:** BF16

The implementation extends the split MegaMoE backend introduced by #4387
and preserves its communication/computation overlap, ready-queue
scheduling, CUDA Graph support, symmetric workspace management, and
top-k reduction path.

## Dependency

> [!IMPORTANT]
> This PR depends on and is stacked on top of
[#4387](https://github.com/flashinfer-ai/flashinfer/pull/4387).
>
> It should not be merged before #4387. After #4387 is merged, this
branch will be rebased onto the latest `main` so that the final diff
contains only the incremental SM120 W4A8 changes.

## Implementation

The main W4A8 changes include:

- Use packed `Float4E2M1FN` weights and `Float8E4M3FN` activations.
- Use the SM120 mixed block-scaled QMMA path:
  - `E2M1 × E4M3`
  - `m16n8k32`
  - E8M0 block scales
- Add packed MXFP4 weight preprocessing and workspace sizing.
- Add the SM120 packed-E2M1 TMA/LDSM path.
- Keep FC1 output quantized as MXFP8 E4M3 with per-K32 E8M0 scales.
- Reuse the split K1/K2 Green Graph execution and independent K3 top-k
reduction.
- Support CUDA Graph capture/replay and uneven token counts across
ranks.
- Add a FlashInfer-facing W4A8 configuration and frontend independent of
the benchmark runner.

The initial FlashInfer frontend supports single-rank and same-NUMA
multi-rank `p2p_direct`. Cross-NUMA IBGDA frontend integration is left
as follow-up work.

## Correctness

Validated on RTX Pro 5000 / SM120 with public CUTLASS DSL 4.6:

- Single-rank eager execution and repeated replay.
- Single-rank CUDA Graph capture and replay.
- Four-rank uneven tail-wave execution.
- Four-rank CUDA Graph capture and 16 repeated replays.
- Deterministic eager/replay outputs.
- Relative L2 error below `0.03` against the Torch reference.
- Shared symmetric workspace across multiple MegaMoE layers.

## Performance Methodology

- Hardware: **4× RTX Pro 5000**
- Latency: **maximum rank critical-path time**
- Routing: balanced
- Reported latency includes dispatch -> FC1 -> FC2 -> combine -> top-k
reduction.
- TFLOP/s counts FC1 and FC2 GEMM FLOPs.

## Performance

### DSV4-Flash

Configuration (the --intermediate size is gate+up here):

```text
--num_topk 6
--hidden 4096
--intermediate 4096
--num_total_experts 256
```

| Tokens/rank | MegaMoE EP4 MXFP4×MXFP8 |
| --- | --- |
| 16 | 740.75 us / 6.523 TFLOP/s |
| 32 | 838.00 us / 11.532 TFLOP/s |
| 64 | 871.86 us / 22.168 TFLOP/s |
| 128 | 1,036.03 us / 37.310 TFLOP/s |
| 512 | 1,730.50 us / 89.349 TFLOP/s |
| 1,024 | 1,868.66 us / 165.486 TFLOP/s |
| 2,048 | 3,676.90 us / 168.206 TFLOP/s |
| 4,096 | 5,514.24 us / 224.319 TFLOP/s |
| 8,192 | 10,831.15 us / 228.406 TFLOP/s |
| 12,288 | 16,077.31 us / 230.813 TFLOP/s |
| 16,384 | 21,311.49 us / 232.166 TFLOP/s |
| 20,480 | 26,685.04 us / 231.769 TFLOP/s |
| 24,576 | 32,170.86 us / 230.696 TFLOP/s |

## Follow-up Work
- Rebase onto the latest main after #4387 is merged.
- Add cross-NUMA NVSHMEM IBGDA selection to the FlashInfer frontend.
- Extend multi-node and 8-rank correctness coverage.
- Continue tuning model- and topology-dependent scheduling heuristics.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **New Features**
- Added SM120/SM121 Blackwell support for MegaMoE expert-parallel
workloads.
  - Added MXFP8 and mixed MXFP4/MXFP8 execution paths with BF16 outputs.
- Added distributed dispatch, token routing, top-k reduction, and
optional CUDA Graph execution.
- Added caller-provided output buffers, staged execution, compile-token
buckets, and topology-aware communication.
- Added single-GPU and multi-rank runtime modes with configurable launch
and scheduling options.
- **Documentation**
  - Added runbooks and usage guidance for SM120 MegaMoE configurations.
- **Tests**
- Added correctness, routing, workspace, graph replay, quantization, and
multi-rank coverage.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Md Anik <mhoqueanik@s4124-0010.ipp1a1.colossus.nvidia.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: Md Saidul Hoque Anik <mhoqueanik@nvidia.com>
Co-authored-by: hanyueh <hanyueh@R6KD-CX8aaS-GPU-09.cm.cluster>
Co-authored-by: Hanyue Hu <hanyueh@nvidia.com>
Co-authored-by: Anerudhan Gopal <agopal@nvidia.com>

### [bfe80f7](https://github.com/flashinfer-ai/flashinfer/commit/bfe80f7594c98bd8a67167ee891a7b44dd6e31ba)

- **作者**: Jiahan Chang (Cyrus)
- **时间**: 2026-10-09T07:42:49Z
- **提交信息**: feat(moe): add TRTLLM Gen SwiGLU StepFun support (#6226)

<!-- .github/pull_request_template.md -->

## 📌 Description

Add native TRTLLM Gen SwiGLU StepFun support to the flat and unified MoE
APIs for BF16, FP8 per tensor, MXFP8, and NVFP4:

```text
StepFun(up, gate, L) = clamp(up, -L, L) * min(silu(gate), L)
```

The default physical limit is 7. Per-expert limits support mixed
routed/shared expert caps, with typed FP8 preparation converting
physical limits into accumulator units. Includes native validation, DA
and per-token NVFP4 forwarding, trace references, end-to-end numerical
tests, and documentation.

Step trace references restore native layouts before evaluating the
activation: BF16 BlockMajorK, FC1 gate/up interleave and FC1/FC2 row
permutations, and MXFP8/NVFP4 128x4 weight-scale swizzles. NVFP4 bias
rows are restored as well.

The test changes retain actual MoE execution against independent
numerical references: four-precision mixed expert limits, NVFP4/MXFP8
shared expert limits, BF16 clipping and CUDA graph replay, FP8
per-tensor non-unit scales/default limits, and NVFP4 per-token scaling.
New internal-helper, mocked capability, argument-forwarding, and
standalone trace-reference tests were removed. The standalone comparison
benchmark was also removed; its historical source and performance
records remain available in #6022.

The FP8 per-tensor public APIs append an optional `gemm1_clamp_limit`
parameter; existing positional arguments and defaults are preserved.

## 🔍 Related Issues

Carries the four commits from #6022 (through
`22988ec5c9a77a4f3ba115e4ab43049ed3756116`), preserving their original
authorship, plus the trace-layout correction.

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

Validation after the test cleanup:

- Existing CPU trace tests and template-consistency checks: **887
passed, 2 skipped**. These results do not establish GPU accuracy.
- The selected native and unified FP8 accuracy cases collect
successfully; **14 skipped** because this host has no CUDA device.
- The NVFP4 graph test file could not be collected in this CPU
environment because its CuTe DSL dependencies are incomplete
(`cutlass._mlir` unavailable).
- Pre-commit hooks pass for every retained file touched by this cleanup;
`git diff --check` passes.
- No new helper functions or smoke tests remain under `tests/`; existing
numerical-reference utilities were extended only as needed by the
retained accuracy cases. Existing capability-table expectations stay
synchronized with the added activation.

GPU accuracy and performance must be rerun on the final branch with the
published Step cubins. #6022 contains the original B300 reports, which
are historical evidence rather than validation of this revision.

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

Draft pending publication and pinning of batched-GEMM cubins with
StepFun epilogues (export ABI `7.0.5.0.4.0` or later). The currently
pinned public artifact lacks Step kernels; Step requests raise the
explicit missing-artifact error. GPU CI must be rerun with the published
artifact before merging, including Rubin validation.

The layout corrections affect Step trace references and schemas; native
kernel execution is unchanged. Row restoration is shared across
precisions, 128x4 decoding reuses the existing GEMM trace
implementation, and duplicate reference-dependency registrations were
removed. Serialized references remain executable with PyTorch alone.



<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added SwiGLUStep activation support for TRT-LLM MoE with BF16, FP8,
MXFP8, and NVFP4 configurations.
* Added configurable per-expert clamp limits for supported routed and
shared-expert workflows, plus SwiGLUStep trace references.
* **Bug Fixes**
* Improved error messages when no compatible MoE kernel configuration is
available.
* Corrected handling of activation parameters and clamp limits during
supported launches.
* **Documentation**
* Documented SwiGLUStep behavior, supported formats, clamp limits,
weight layouts, and configuration requirements.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: mengw <12670782+wm2012011492@users.noreply.github.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-10-10
**监控日期**: 2026-10-09
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4581
- **最后更新**: 2026-10-09T22:49:14Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Yixing Wang

## AI分析总结

## 提交分析：[d5253fd] Add serving cookbook recipes and configuration API (#1941)

### 1. 主要更新类型
- **功能新增**：为服务（serving）模块添加 cookbook 配方和配置 API。
- 附带文档性质的示例/配方更新，帮助用户快速上手。

### 2. 关键变更点及与项目整体方向的关系
- 引入 **配置 API（configuration API）**，意味着服务端部署从"零散脚本/命令行参数"向**结构化、可编程配置**演进，便于统一管理模型加载、推理参数、服务端口等。
- 添加 **serving cookbook recipes**：README 中已将 Cookbook 作为核心入口之一，此次把 serving 场景（如单卡/多卡推理、不同模型变体部署）以配方形式沉淀，降低用户从"能跑"到"生产可用"的门槛。
- 与项目主线——**高效视频扩散模型的训练与推理服务化**——高度一致，是从"研究代码"走向"可用系统"的重要一步。

### 3. 对项目的影响和潜在意义
- 降低用户部署视频生成服务的学习成本，提升项目采用率。
- 配置 API 为后续功能（如自动扩缩容、模型切换、A/B 测试）预留了扩展基础。
- cookbook 化的配方便于社区贡献与验证，契合项目活跃的社区运营（README 中的 Weekly Dev Meeting、Slack 群等）。
- 可能推动 serving 模块的 API 稳定化，为 1.0 级别发布或下游集成（如 ComfyUI、云服务商）铺路。

### 4. 值得关注的技术点
- 配置 API 的设计：是采用 dataclass/pydantic 式的强类型配置，还是 YAML/JSON 驱动？强类型更利于 IDE 补全和校验，YAML 更利于非开发者使用。
- cookbook recipes 涵盖的场景范围：是否包含多节点分布式推理、量化/蒸馏模型的服务化、长视频生成的内存管理等。
- 是否与既有推理 API（README 提到的 Inference Quick Start）保持一致的抽象层，避免两套并行接口。
- Co-author 涉及两位开发者，说明这是团队协作的 feature PR（#1941），可关注后续 PR 中对该 API 的迭代与修正。

### 5. 基于 README 背景对项目发展的影响
FastVideo 的定位是"快速视频扩散模型"的训练+推理工具链，README 强调 Documentation/Cookbook/Quick Start 三位一体。本次提交补齐了 **serving 方向的 cookbook 与配置 API**，意味着项目正在从"研究型推理库"向"**可落地部署的视频生成服务框架**"转型。这对希望将视频生成能力接入产品的用户（云服务、内容平台）是关键信号：服务化路径正在被官方支持和文档化。建议持续关注 serving 模块的 API 稳定性与性能基准，以及是否会出现独立的 serving 文档页面或 benchmark 报告。

## 详细提交记录

### [d5253fd](https://github.com/hao-ai-lab/FastVideo/commit/d5253fd71055927f12aa6c4aa679b93a00238851)

- **作者**: Yixing Wang
- **时间**: 2026-10-09T22:49:08Z
- **提交信息**: [feat] Add serving cookbook recipes and configuration API (#1941)

Co-authored-by: leo <yixingwang@YIXINGs-MacBook-Pro.local>
Co-authored-by: Aryan Kumar <aryan5v@users.noreply.github.com>

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-10-10
**监控日期**: 2026-10-09
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34695
- **最后更新**: 2026-10-10T00:30:42Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Christopher, Jingya HUANG

## AI分析总结

## huggingface/diffusers 昨日提交分析（1/1批，共2个提交）

### 1. 主要更新类型
- **功能新增**为主：TorchTPU后端集成（提交1）、LoKr适配器支持（提交2）
- 辅以文档更新、Bug修复和代码清理/重构

### 2. 关键变更点及与项目方向的关系

**提交1 — TorchTPU后端集成（#14039）**
- 为diffusers引入TorchTPU后端，支持eager模式、torch.compile及张量并行（TP），覆盖SDXL、Flux、Flux2/Klein、Wan等主流模型系列
- 修复了Wan数值溢出、编译模式错误、TPU设备放置等问题，并将`text_encoder.device`修复传播到多个`# Copied from`派生管道
- 注册了`tpu.md`文档至目录树（修复文档构建失败），并清理了`DiffusionPipeline._execution_device`中的冗余逻辑

**提交2 — LoKr适配器支持（#14163，修复#13221）**
- 在Z-Image和Flux2/Klein的LoRA加载混合器中新增LyCORIS LoKr（Kronecker积）适配器加载能力
- 实现了`_create_lokr_config`从张量形状自动推断配置，并支持多种野外格式的权重转换（ai-toolkit Z-Image、BFL Flux2 fused-QKV、LyCORIS下划线格式等）
- 处理了fused-QKV无法精确拆分的技术难题：通过将模型QKV投影融合后1:1映射适配器，保证精确加载

### 3. 对项目的影响和潜在意义
- **扩大硬件生态**：TorchTPU使diffusers可运行于Google TPU，降低了对NVIDIA GPU的依赖，对大规模推理/训练场景意义重大
- **增强LoRA生态兼容性**：LoKr是LyCORIS社区广泛使用的低秩适配格式，此前diffusers仅支持标准LoRA；此提交让用户无需切换到其他框架即可加载Z-Image/Flux2生态中的LoKr权重，直接提升了模型可用性
- **维护性提升**：删除冗余设备检查、传播修复到派生管道、规范文档结构，减少了`# Copied from`机制带来的维护债务

### 4. 值得关注的技术点
- **Kronecker积的融合QKV处理**：fused-QKV投影无法分解为独立Q/K/V的Kronecker因子，PR巧妙地反向操作——融合模型侧而非拆分适配器侧，保证数学精确性
- **Alpha的LyCORIS约定处理**：缩放仅应用于秩分解因子，且在权重转换时烘焙进权重，避免运行时语义偏差
- **多格式权重转换**：一张适配器需兼容4种路径/命名格式，体现了对开源生态碎片化的务实处理
- **AI辅助开发痕迹**：多个提交标注Co-Authored-By Claude系列模型，反映了该项目已将AI工具深度纳入开发流程

### 5. 对项目发展的整体影响
作为diffusion模型推理/训练的核心库，这两个提交分别从**硬件广度**（TPU支持）和**适配器生态广度**（LoKr格式）两个维度扩展了项目覆盖面，符合diffusers"成为扩散模型标准基础设施"的定位。TPU支持可能吸引更多非NVIDIA环境的用户和企业；LoKr支持则巩固了其在LoRA/低秩微调领域的中心地位，减少用户流失到ComfyUI等替代方案。同时，文档和冗余代码的清理表明项目在快速扩张中仍重视工程质量，这对维持大规模开源项目的可持续发展至关重要。

## 详细提交记录

### [1d5d056](https://github.com/huggingface/diffusers/commit/1d5d056ecff3a8c1d887a7dd1aa66ca4a0323458)

- **作者**: Jingya HUANG
- **时间**: 2026-10-09T10:46:23Z
- **提交信息**: [TPU] TorchTPU backend integration - eager / torch.compile / tp (#14039)

* feat: add torchtpu

* feat:draft TorchTPU support

* fix: wan overflow issue + compile mode error on sdxl

* doc: enhance with TorchTPU doc

* doc: enhance with TorchTPU doc

* style: remove unused imports flagged by ruff

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* docs: remove Debug Eager and Fused Eager sections from tpu.md

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* feat: add TP for TPU

* style: fix import sorting in TPU test scripts

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* style: ruff format TPU test scripts

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* fix: style

* fix: test for native 4 devices

* fix: propagate TPU device fixes to Flux/Flux2/Wan-family copies; register tpu.md; drop redundant execution_device check

- Propagate the text_encoder.device-based fix (introduced for TPU CPU-offload
  support) from FluxPipeline/Flux2KleinPipeline/WanPipeline into their
  `# Copied from` copies (flux/*, flux2_klein_inpaint, visualcloze, anyflow,
  chronoedit, lucy_edit, skyreels_v2/*). SDXL-family copies of
  StableDiffusionXLPipeline.encode_prompt are intentionally left untouched;
  they'll be handled in a follow-up PR that fixes device placement for every
  pipeline component (not just text encoders).
- Register docs/source/en/optimization/tpu.md in _toctree.yml (was breaking
  the docs build: "not present in the table of contents").
- Remove the redundant "prefer non-CPU, non-meta component" loop from
  DiffusionPipeline._execution_device: PR #14383 already fixed this in
  DiffusionPipeline.device, which _execution_device falls back to. Verified
  on TPU hardware that _execution_device still resolves correctly for a
  split-placement pipeline after the removal.

Co-Authored-By: Claude Sonnet 5 <noreply@anthropic.com>

* tests: cleanup

* fix: fix compile mode

* Update docs/source/en/optimization/tpu.md

Co-authored-by: Steven Liu <59462357+stevhliu@users.noreply.github.com>

* Update docs/source/en/optimization/tpu.md

Co-authored-by: Steven Liu <59462357+stevhliu@users.noreply.github.com>

* Update docs/source/en/optimization/tpu.md

Co-authored-by: Steven Liu <59462357+stevhliu@users.noreply.github.com>

* Update docs/source/en/optimization/tpu.md

Co-authored-by: Steven Liu <59462357+stevhliu@users.noreply.github.com>

* Update docs/source/en/optimization/tpu.md

Co-authored-by: Steven Liu <59462357+stevhliu@users.noreply.github.com>

* Update docs/source/en/optimization/tpu.md

Co-authored-by: Steven Liu <59462357+stevhliu@users.noreply.github.com>

* Update docs/source/en/optimization/tpu.md

Co-authored-by: Steven Liu <59462357+stevhliu@users.noreply.github.com>

* Update docs/source/en/optimization/tpu.md

Co-authored-by: Steven Liu <59462357+stevhliu@users.noreply.github.com>

* Update docs/source/en/optimization/tpu.md

Co-authored-by: Steven Liu <59462357+stevhliu@users.noreply.github.com>

* Update docs/source/en/optimization/tpu.md

Co-authored-by: Steven Liu <59462357+stevhliu@users.noreply.github.com>

* Update docs/source/en/optimization/tpu.md

Co-authored-by: Steven Liu <59462357+stevhliu@users.noreply.github.com>

* test: remove flux2 e2e test

* doc: apply suggestions

* doc: apply suggestions

* review: remove monkey patch

* review: revert neuron-specific changes in the tests

* review: apply suggestions

* Update docs/source/en/optimization/tpu.md

Co-authored-by: Steven Liu <59462357+stevhliu@users.noreply.github.com>

* doc: add tpu to tp doc

* review: remove unnecessary for tpu

* test: assert every _tp_plan parameter is sharded after a TP load

Co-Authored-By: Claude Opus 5.5 <noreply@anthropic.com>

* removal: delete redundant tp shard helpers

* removal: drop TPU workarounds no longer needed after recent main changes

* doc: keep the FLUX.2-dev text encoder off a single TPU chip in the TP example

* doc: encode the prompt on CPU in the TPU TP example so it runs end to end

* test: tighten TPU TP tolerance and simplify the TPU TP worker

* doc: use enable_model_cpu_offload() in the TPU eager example

* doc: shard both FLUX.2-dev text encoder and transformer in the TPU TP example

* doc: run the text encoders on TPU in the compiled example

* test: drop the redundant TPU sync in the TP worker

* test: trim comments in the TPU TP tests

* test: run the TPU TP test with mp.spawn like the CUDA one

* test: pin the TPU TP test to 4 chips

* Update docs/source/en/optimization/tpu.md

Co-authored-by: Steven Liu <59462357+stevhliu@users.noreply.github.com>

* doc: use DistributedConfig and dtype, and drop the torch_tpu import in the TPU examples

* test: skip the TPU TP test for models without a _tp_plan

* doc: correct the warning of recompilation

* fix: clone the SD3 timestep so torch.compile doesn't recompile every step, thus we can use it for the tpu.md compile mode snippet

* doc: update advice for compile mode when one chip doesn't fit

* test: pass the TPU TP tolerances as test arguments

* review: apply suggestions to the doc

* review: view compilation patch for tpu-only

---------

Co-authored-by: Claude Sonnet 4.6 <noreply@anthropic.com>
Co-authored-by: JingyaHuang <huang_jingya@outlok.com>
Co-authored-by: Steven Liu <59462357+stevhliu@users.noreply.github.com>
Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

### [78bf2c6](https://github.com/huggingface/diffusers/commit/78bf2c6266668a1c7185b28053b807f786b6f34e)

- **作者**: Christopher
- **时间**: 2026-10-09T07:26:56Z
- **提交信息**: [LoRA] add LoKr adapter support (Z-Image, Flux2/Klein) (#14163)

* [LoRA] add LoKr adapter support (Z-Image, Flux2/Klein)

Adds loading of LoKr (LyCORIS Kronecker product) adapters:

- `load_lora_adapter` detects `lokr_` keys and injects a peft `LoKrConfig`,
  inferred from the tensor shapes via `_create_lokr_config` (decompose
  factor, per-module rank/alpha patterns).
- State dict conversions for the formats in the wild: ai-toolkit Z-Image
  (dotted diffusers paths under `diffusion_model.`), ai-toolkit BFL Flux2
  (fused qkv), LyCORIS underscore format, and bare dotted diffusers paths.
- BFL fused-QKV LoKr cannot be split exactly into separate Q/K/V Kronecker
  factors, so `Flux2LoraLoaderMixin.load_lora_weights` fuses the model's
  QKV projections and maps the adapter 1:1 (exact).
- Alpha follows the LyCORIS convention: scaling applies only to
  rank-decomposed factors and is baked into the weights at conversion.

Fixes #13221

* [LoRA] LoKr review follow-ups: adapter-agnostic error message, refuse fused-QKV load over an unfused adapter

- "Invalid adapter checkpoint. We currently support LoRA and LoKr." replaces the
  message that still said "LoRA checkpoint" and described the substring check.
- Loading a fused-QKV LoKr checkpoint now refuses when an adapter is already
  injected on to_q/to_k/to_v or add_{q,k,v}_proj: fuse_qkv_projections() would
  replace those modules and orphan it. Covered by a test.

Co-Authored-By: Claude Fable 5.1 <noreply@anthropic.com>

* [LoRA] rename the LoKr tests to test_lokr_conversion.py

The file exercises checkpoint conversion and loading for LoKr adapters, not LoRA.

Co-Authored-By: Claude Opus 5.5 <noreply@anthropic.com>

* [LoRA] LoKr review follow-ups: scope to Z-Image/Flux2, model-level fused QKV, LoKrTesterMixin

- Only the Z-Image and Flux2 loader mixins accept LoKr checkpoints, the two that
  convert them; the other mixins are back to their LoRA-only check.
- The fused-QKV handling moves to `_maybe_fuse_qkv_projections_for_lokr` in
  peft_utils, called from `load_lora_adapter`, so the model fuses its projections
  whichever entry point loads the adapter. The quantized-model error explains why.
- `_bake_lokr_alpha` becomes `_bake_lokr_alpha_` as it edits the dict in place.
- The BFL Flux2 converter no longer accepts expanded diffusers block names under
  `diffusion_model.`: no LoKr checkpoint uses that layout; diffusers-named
  checkpoints have no prefix and take the generic converter.
- The LyCORIS converter names the keys it does not recognize.
- Tests move from tests/lora to a `LoKrTesterMixin` in tests/models/testing_utils,
  with the checkpoint formats tested on the Flux2 and Z-Image model test classes.

Co-Authored-By: Claude Opus 5.5 <noreply@anthropic.com>

* [LoRA] mark ZImageLoraLoaderMixin.load_lora_weights as copied from Flux2

---------

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-10-10
**监控日期**: 2026-10-09
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


**报告日期**: 2026-10-10
**监控日期**: 2026-10-09
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13214
- **最后更新**: 2026-10-09T17:43:41Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 1
- **主要提交者**: Zhongjie Duan

## AI分析总结

## 一、主要更新类型
本次提交以**功能新增**为主，辅以版本发布管理。具体而言，是为项目新增了对 Qwen-Image-2.1-Turbo 模型的支持，并同步将版本号升级至 2.1.9。

## 二、关键变更点及与项目方向的关系
- **新增 Qwen-Image-2.1-Turbo 支持（PR #1733）**：DiffSynth-Studio 的核心定位是提供统一的扩散合成（Diffusion Synthesis）训练与推理框架，持续集成前沿的视频/图像生成模型。本次集成 Qwen（通义千问）图像生成模型的 Turbo 版本，延续了该项目紧跟国内大模型生态、丰富模型矩阵的发展路线。
- **版本号更新至 2.1.9（PR #1734）**：紧随功能合并后发布新版本，表明这是一个面向用户的正式发布节点，便于通过 PyPI 更新使用。

## 三、对项目的影响和潜在意义
- **降低用户使用门槛**：用户无需自行适配即可通过 DiffSynth 统一接口使用 Qwen-Image-2.1-Turbo，享受更快速的图像生成推理体验。
- **增强框架竞争力**：在开源扩散合成工具竞争激烈的背景下，及时支持最新的 Turbo 加速模型有助于保持项目的活跃度和用户吸引力，与其在 Trendshift 上的高热度趋势相符。
- **生态协同**：与 ModelScope 平台生态进一步打通，便于模型下载、微调与部署的一体化流程。

## 四、值得关注的技术点
- **Turbo 模型的推理加速机制**：Qwen-Image-2.1-Turbo 通常采用少步数蒸馏（如 Rectified Flow 蒸馏或对抗蒸馏）技术实现快速推理，关注 DiffSynth 如何在统一管线中适配其采样步数、CFG 策略与调度器配置。
- **统一模型注册机制**：作为框架型项目，如何通过最小改动新增模型（如模型配置文件、Pipeline 类、权重加载逻辑）体现了 DiffSynth 的可扩展架构设计。
- **版本迭代节奏**：从 2.1.8 到 2.1.9 的快速小版本迭代，说明项目采用轻量、频繁的发布策略以保持与上游模型更新同步。

## 五、对项目发展的影响
结合 README 可知，DiffSynth-Studio 是 ModelScope 旗下的开源扩散合成工作室，目标是让用户便捷地训练和使用最新的图像/视频生成模型。本次"新增模型 + 版本发布"的组合提交，正是该目标的直接体现：一方面持续扩展模型覆盖范围（尤其是国产大模型），另一方面通过规范化的版本管理保障用户体验。这种"功能驱动小版本发布"的模式有助于项目在保持技术前沿性的同时，建立稳定的发布节奏，进一步巩固其作为主流扩散合成工具链的地位。

## 详细提交记录

### [acf2ad2](https://github.com/modelscope/DiffSynth-Studio/commit/acf2ad29c65f436633f57beec1caaa1296760331)

- **作者**: Zhongjie Duan
- **时间**: 2026-10-09T08:04:38Z
- **提交信息**: update version to 2.1.9 (#1734)

### [34de10c](https://github.com/modelscope/DiffSynth-Studio/commit/34de10cb739ab3a0df72b0dd87a5f773aa46fb69)

- **作者**: Zhongjie Duan
- **时间**: 2026-10-09T07:51:26Z
- **提交信息**: support Qwen-Image-2.1-Turbo (#1733)

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-10-10
**监控日期**: 2026-10-09
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 36930
- **最后更新**: 2026-10-10T01:45:22Z

## 提交统计

- **昨日提交总数**: 67
- **提交者数量**: 34
- **主要提交者**: Wenbo Ji　嵇文博, James Xu, weireweire

## AI分析总结

# SGLang 昨日提交综合分析（共 67 条提交）

## 一、主要更新类型
昨日提交集中在**性能优化**、**模型支持**、**Bug 修复**与**架构重构**四大方向：
- **性能优化**占比最高，涵盖 CUDA Graph（breakable graph 默认启用）、AMD/aiter 内核、MoE 调度、Mooncake KV 缓存批处理、Blackwell 融合 GEMM 与启动时间优化。
- **模型支持**新增/完善 LLaDA2.2 Block Routing MoE、Wan-Animate-2、SANA-Video 2.0、MiniMax-H3、GLM-5.3、DeepSeek-V4/V4.1、Qwen3.8-Flash-Next、Kimi K3、FLUX.2 Klein、LTX-2。
- **Bug 修复**覆盖分布式启动阻塞、CFG 归一化、两批重叠残差缺失、CUDA Graph 崩溃、MLX 后端稳定性等。
- **重构**包括 sgl-router 共享 OpenAI 兼容层、rust-processor 多主机状态共享、Kimi K3 层通信清理、diffusion 模块去重。

## 二、关键变更点
1. **扩散/视频多模态成最活跃方向**：超 15 条 diffusion 提交围绕 MiniMax-H3 做算子融合（RMSNorm+AdaLN、modulation 分块）、Ulysses 通信流水线化与 CFG 修正，并新增 Wan-Animate-2、SANA-Video 2.0 支持，直接扩展多模态推理版图。
2. **前沿模型定制深入**：GLM-5.3 启用 DeepEP v2 与 breakable prefill CUDA graph；DeepSeek-V4.1 增加 MXFP8 dispatch 缓存；Qwen3.8-Flash-Next 做 Blackwell BF16 decode 优化；Kimi K3 重构 PP 分片并修复 KDA value head、SiTU 对齐与阶段边界。
3. **正确性加固**：DeepSeek-V4 修复流水线交接中 FFN 输出未回写 attention 行、两批重叠微批合并遗漏残差等数值问题；LTX-2 修正全局 unpadded 序列的 SP 掩码。
4. **多机/分离式部署**：PP+PD bootstrap 延迟降低、DP 控制器与调度器启动重叠、A2A 后端修复、reasoning splitter 与 tool constraint 跨主机共享。
5. **API 收敛**：sgl-router 的 `/v1/completions` 复用 `/generate` 共享层，统一限流、日志与中间件逻辑。
6. **多硬件扩展**：AMD MI35X/gfx95 FP8 内核、NPU 适配、MLX 后端 KV 回写与 radix 前缀稳定性连续修复。
7. **协作开发特征**：多条提交署名 Claude Opus 5.x，NVIDIA、AMD、radixark 等外部贡献活跃；同时更新 Clef 部署指南与 thinking budget 文档。

## 三、技术关注点
- **Breakable CUDA graph** 在 GLM-5.3-Flash 与 FLUX.2 Klein 默认启用，是变长 prefill 图捕获的重要演进。
- **两批重叠调度的数值等价性**：残差遗漏类 bug 提示激进批处理优化易引入静默偏差，版本升级时需关注。
- **流水线并行的张量路由**：FFN→attention 回写修复暴露了维度/索引映射隐患。
- **多主机有状态共享**与共享 OpenAI 层设计，为分布式部署和企业级扩展奠定架构基础。

## 四、对项目发展的整体影响
这批提交显示 SGLang 正从纯 LLM 推理引擎加速演进为 **LLM + 扩散/视频统一推理平台**，并通过多硬件适配（NVIDIA/AMD/NPU/MLX）、分布式调度优化与大量模型定制巩固"Fast inference"的核心定位。项目处于"极致吞吐"向"吞吐与正确性并重"过渡的阶段，日均 60+ 提交的活跃度反映高速迭代。短期需关注 MLX 与 diffusion 模块的稳定性收敛；中期看，路由层与处理器层的抽象收敛正为大规模多机部署和云厂商生态接入做准备，有利于强化其生产级推理引擎的可靠性口碑。

## 详细提交记录

### [961bcf4](https://github.com/sgl-project/sglang/commit/961bcf481d184be65c2a2879e62faa3e9d2fdc65)

- **作者**: Rain Jiang
- **时间**: 2026-10-09T23:57:12Z
- **提交信息**: support DeepEP v2 on GLM-5.3 (#43432)

### [2d38934](https://github.com/sgl-project/sglang/commit/2d3893449380864c178ec74be0a6bf24d0131175)

- **作者**: Yuwei An
- **时间**: 2026-10-09T23:36:28Z
- **提交信息**: [DSv4.1] mxfp8 dispatch cache (#42156)

Co-authored-by: Yuwei An <yuwei.an@MacBook-Pro-yuweian.local>

### [46498bc](https://github.com/sgl-project/sglang/commit/46498bc8c5cd9dc48147dffe10f98a770ce84b2c)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-09T23:20:45Z
- **提交信息**: [MLX] Sync decode KV to the pool once at release, clamped to the owned prefix (#43292)

### [114cb44](https://github.com/sgl-project/sglang/commit/114cb44920574e98f860dd76edcb15291df7988b)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-09T23:18:58Z
- **提交信息**: [MLX] Read radix prefix slots from the model runner's `req_to_token` pool (#43291)

### [8020ea2](https://github.com/sgl-project/sglang/commit/8020ea2ee959bff10938eefcaea966192822a763)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-09T23:16:59Z
- **提交信息**: [MLX] Drop a retracted request's runner state at its re-prefill (#43284)

### [f7e601b](https://github.com/sgl-project/sglang/commit/f7e601b93664b78f003c037f58d4cb01a9cec809)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-09T23:14:23Z
- **提交信息**: [MLX] Drain in-flight jobs before a retract-mode `pause_generation` (#43282)

### [f6c848c](https://github.com/sgl-project/sglang/commit/f6c848c882ba8b60a80518b38088046e0bc5ce03)

- **作者**: metamergebot
- **时间**: 2026-10-09T22:50:52Z
- **提交信息**: [PD] Use 1 to disable decode host receive and 0 for always-on (#43407)

Co-authored-by: Hanming Lu <69857889+hanming-lu@users.noreply.github.com>
Co-authored-by: cctry <cctry@users.noreply.github.com>

### [f6e3444](https://github.com/sgl-project/sglang/commit/f6e3444b2e90cb3d9d1e43ab2b60ad1e05235001)

- **作者**: Alison Shao
- **时间**: 2026-10-09T22:47:47Z
- **提交信息**: ci: diffusion-only option for the runner utilization report (#41620)

### [58f6976](https://github.com/sgl-project/sglang/commit/58f6976ce76665342b5b7f3df161e590f46a3192)

- **作者**: Cheng Wan
- **时间**: 2026-10-09T22:39:59Z
- **提交信息**: [Fix] Unblock CUDA graph startup for hybrid parallelism (#43211)

### [cb9bd1d](https://github.com/sgl-project/sglang/commit/cb9bd1d4d4b14828efe8dc7758fcd94020ab501c)

- **作者**: Liu Ke
- **时间**: 2026-10-09T22:32:14Z
- **提交信息**: [Perf] Reduce multi-detokenizer router IPC sends (#42238)

Co-authored-by: hnyls2002 <lsyincs@gmail.com>
Co-authored-by: Liangsheng Yin <hnyls2002@gmail.com>

### [66d840a](https://github.com/sgl-project/sglang/commit/66d840a8ef27cf400d8fdcf47d9c72b997ad1153)

- **作者**: metamergebot
- **时间**: 2026-10-09T22:21:23Z
- **提交信息**: [cuda_graph] Size dp-local decode graphs by the runner's own gather requirement (#43303)

Co-authored-by: Hanming Lu <69857889+hanming-lu@users.noreply.github.com>
Co-authored-by: charlotte12l <charlotte12l@users.noreply.github.com>

### [6d8ddaf](https://github.com/sgl-project/sglang/commit/6d8ddaf1d786c43cc84c6292f930c174c07e4b02)

- **作者**: Kevin Mi
- **时间**: 2026-10-09T22:05:50Z
- **提交信息**: [AMD] MiniMax-M3 indexer CP: packed scoring for EAGLE verify rows (#42614)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [fbf8d73](https://github.com/sgl-project/sglang/commit/fbf8d730fd9ff94d13b4345b394b9c0c9cd92032)

- **作者**: Thanhhao
- **时间**: 2026-10-09T22:05:05Z
- **提交信息**: [Fix] MiniMax-M3: default to the breakable prefill CUDA graph (#41845)

Co-authored-by: Hao Phan <htphan@nvidia.com>
Co-authored-by: Po-Han Huang (NVIDIA) <53919306+nvpohanh@users.noreply.github.com>
Co-authored-by: Kevin Mi <45493463+kevin-mii@users.noreply.github.com>
Co-authored-by: Po-Han Huang <pohanh@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [70e82f7](https://github.com/sgl-project/sglang/commit/70e82f7b731f341960d72d13be5f5ed4e638af78)

- **作者**: Kevin Mi
- **时间**: 2026-10-09T22:04:25Z
- **提交信息**: [AMD] Run the MiniMax indexer CP test on MI35X, not MI300 (#43259)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [46c2585](https://github.com/sgl-project/sglang/commit/46c2585faa4fcb6fa8febf4d2d4534a7cf33da79)

- **作者**: weireweire
- **时间**: 2026-10-09T21:40:28Z
- **提交信息**: [DSpark] Fold draft sampling for DeepSeek-V4.1 heads under AUTO (#42987)

Co-authored-by: weireweire <20922698+weireweire@users.noreply.github.com>

### [2f1acef](https://github.com/sgl-project/sglang/commit/2f1acef3d8860ffe1c4744d99368772cb940f983)

- **作者**: Huabin
- **时间**: 2026-10-09T19:14:44Z
- **提交信息**: [Model] Add LLaDA2.2 Block Routing MoE support (#31768)

### [72eab59](https://github.com/sgl-project/sglang/commit/72eab59bf6395c342a60967ec2a31761c505e151)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-10-09T18:41:02Z
- **提交信息**: [GLM-5.3-Flash] Enable breakable prefill CUDA graph by default (#42845)

Co-authored-by: Mohammad Angkad <mohammad.angkad@radixark.ai>

### [87845cd](https://github.com/sgl-project/sglang/commit/87845cda2bc1d8c1d4b10c608813e26f421d1bde)

- **作者**: metamergebot
- **时间**: 2026-10-09T17:57:01Z
- **提交信息**: [Multimodal] Chunk and cache audio items whose offsets span several placeholder runs (#43301)

Co-authored-by: Hanming Lu <69857889+hanming-lu@users.noreply.github.com>
Co-authored-by: YavorGIvanov <YavorGIvanov@users.noreply.github.com>

### [3bffe69](https://github.com/sgl-project/sglang/commit/3bffe69b74b1391c1735f57f9d2262a0630ef14e)

- **作者**: metamergebot
- **时间**: 2026-10-09T17:55:02Z
- **提交信息**: [moe] Fill num_token_non_padded for the customized A2A backend at EP 1 (#43245)

Co-authored-by: Hanming Lu <69857889+hanming-lu@users.noreply.github.com>
Co-authored-by: cctry <cctry@users.noreply.github.com>

### [3c61213](https://github.com/sgl-project/sglang/commit/3c612132fdd22ae947d19d9e83d641e9eae3d247)

- **作者**: metamergebot
- **时间**: 2026-10-09T17:54:22Z
- **提交信息**: Overlap scheduler startup with the data parallel controller (#43177)

Co-authored-by: Hanming Lu <69857889+hanming-lu@users.noreply.github.com>
Co-authored-by: Yongji Wu <30348494+libertyeagle@users.noreply.github.com>

### [5cbf949](https://github.com/sgl-project/sglang/commit/5cbf949839b1fc73802d20670943ccbeb805d3f2)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-10-09T15:51:30Z
- **提交信息**: Fix torch.compile crash in fused gate-sigmoid-mul launcher (#43384)

Co-authored-by: Mohammad Angkad <mohammad.angkad@radixark.ai>

### [76ccf08](https://github.com/sgl-project/sglang/commit/76ccf0850caf7e2fa996c06653070063a3872977)

- **作者**: Wenbo Ji　嵇文博
- **时间**: 2026-10-09T15:20:13Z
- **提交信息**: [diffusion] fix: fix TeaCache CFG state lifecycle and skip boundaries (#42422)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Mick <mickjagger19@icloud.com>

### [121aa8d](https://github.com/sgl-project/sglang/commit/121aa8dcc72ff81db69b17c80bed2db5513e7ed4)

- **作者**: Mick
- **时间**: 2026-10-09T14:39:11Z
- **提交信息**: [diffusion] perf: fuse MiniMax-H3's RMSNorm and indexed AdaLN under quality lossless (#43327)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [408f5d0](https://github.com/sgl-project/sglang/commit/408f5d057a957189d92624f2df4bd96719bbc2b8)

- **作者**: Jimmy Shong
- **时间**: 2026-10-09T14:19:27Z
- **提交信息**: docs: add Clef accuracy results to the deployment wizard (#43349)

### [1203eb9](https://github.com/sgl-project/sglang/commit/1203eb918127a370a9ece4c33593df62467a15b0)

- **作者**: Mick
- **时间**: 2026-10-09T14:04:29Z
- **提交信息**: [diffusion] perf: pipeline MiniMax-H3's Ulysses exchange against attention over the copy engine (#43164)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [fba3ad4](https://github.com/sgl-project/sglang/commit/fba3ad4b1f4563143f3352beb148c4c28d4be9ed)

- **作者**: xiaofei-zheng
- **时间**: 2026-10-09T13:30:22Z
- **提交信息**: [Frontend] Parallelize long chat prompt encoding (#41259)

### [db32673](https://github.com/sgl-project/sglang/commit/db32673b78dfbda223122a00e65f3d1af29df2e8)

- **作者**: xiaofei-zheng
- **时间**: 2026-10-09T13:28:45Z
- **提交信息**: [AMD] Let the GLM DSA NextN draft declare its own shared-expert fusion architecture (#41258)

### [d5c3ae9](https://github.com/sgl-project/sglang/commit/d5c3ae975282eaa312b0e033517243e2b3f3ae4e)

- **作者**: xiaofei-zheng
- **时间**: 2026-10-09T13:27:38Z
- **提交信息**: [AMD] Eliminate remaining gfx95 FP8 scale relayout copies (#41030)

### [78996e3](https://github.com/sgl-project/sglang/commit/78996e3f02a88e914b1000fd734da5d3df8ebab8)

- **作者**: weireweire
- **时间**: 2026-10-09T13:12:42Z
- **提交信息**: [Performance] Batch Mooncake hybrid-pool metadata and puts (#39696)

Co-authored-by: weireweire <20922698+weireweire@users.noreply.github.com>
Co-authored-by: Po-Han Huang (NVIDIA) <53919306+nvpohanh@users.noreply.github.com>
Co-authored-by: Po-Han Huang <pohanh@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [d511e6b](https://github.com/sgl-project/sglang/commit/d511e6bd1d132ba9bf2fd1325ee0f182869567e9)

- **作者**: Kan Wu
- **时间**: 2026-10-09T13:07:30Z
- **提交信息**: [sgl-router] Parse tool calls when serving chat through /generate (#42999)

Co-authored-by: Kan Wu <kan.wu@radixark.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [67d063f](https://github.com/sgl-project/sglang/commit/67d063f63b0b4237fb70b410031c1474a35b347c)

- **作者**: Aleksi Vesanto
- **时间**: 2026-10-09T12:57:29Z
- **提交信息**: [diffusion] feat: allow per-role attention backend override (#35310)

Co-authored-by: Mick <mickjagger19@icloud.com>
Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [348689d](https://github.com/sgl-project/sglang/commit/348689da40fac15a48620dc2437a44453b797375)

- **作者**: Chao Shi
- **时间**: 2026-10-09T12:53:48Z
- **提交信息**: [PP+PD] Fix #38206 Reduce bootstrap consensus latency (#38959)

Co-authored-by: inkcherry <mingzhi.liu@amd.com>
Co-authored-by: Shangming Cai <csmthu@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [f1e0472](https://github.com/sgl-project/sglang/commit/f1e0472fcc7dc34e2b9daaef1b41c9ffe53f487c)

- **作者**: Ankit Dhall
- **时间**: 2026-10-09T12:46:23Z
- **提交信息**: [diffusion] model: support Wan-Animate-2 (#42941)

Co-authored-by: Ankit Dhall <8938083+ankitdhall@users.noreply.github.com>
Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [0955169](https://github.com/sgl-project/sglang/commit/0955169ed26f0b4d931818689c83839e681c9e48)

- **作者**: Shuwen Wang
- **时间**: 2026-10-09T12:25:33Z
- **提交信息**: [mem_cache] Bound FlexKV checkpoint stores and restore DSPARK cache checks (#35694)

### [59eb71a](https://github.com/sgl-project/sglang/commit/59eb71a831f6b87babc2400737c7faabed5ee01c)

- **作者**: Prozac614
- **时间**: 2026-10-09T11:47:03Z
- **提交信息**: [diffusion] fix: align SGLD CFG combine formula with diffusers Z-Image (#23772)

Co-authored-by: SGLang CI <ci@sglang.ai>
Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Mick <mickjagger19@icloud.com>

### [f48ed21](https://github.com/sgl-project/sglang/commit/f48ed2127e3457e88f5ee86debd4d12a7735c69f)

- **作者**: Shuwen Wang
- **时间**: 2026-10-09T11:24:39Z
- **提交信息**: test: allow bounded checkpoint lag in Mamba HiCache tests (#42523)

### [3805d78](https://github.com/sgl-project/sglang/commit/3805d787963ad15caaa9f7544cba2612cdc78232)

- **作者**: Kan Wu
- **时间**: 2026-10-09T11:17:52Z
- **提交信息**: [sgl-router] Serve /v1/chat/completions through /generate, with reasoning parsing (#42998)

Co-authored-by: Kan Wu <kan.wu@radixark.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Shangming Cai <csmthu@gmail.com>

### [0eb24e7](https://github.com/sgl-project/sglang/commit/0eb24e7d5b0b1593bd96723882679aaecbf417b6)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-10-09T10:46:12Z
- **提交信息**: [Performance] Optimize Qwen3.8-Flash-Next BF16 decode on Blackwell (#42175)

### [516fd1c](https://github.com/sgl-project/sglang/commit/516fd1c1b5221b6cab5d53052ac7b9c582b2608a)

- **作者**: Mick
- **时间**: 2026-10-09T10:23:52Z
- **提交信息**: [diffusion] perf: tile MiniMax-H3's indexed modulation kernels by 2048 columns (#43267)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [91b3692](https://github.com/sgl-project/sglang/commit/91b3692a4c39453694f53ff54b67186ca4a7f34c)

- **作者**: Xinyuan Tong
- **时间**: 2026-10-09T09:50:34Z
- **提交信息**: docs: add thinking budget guide (#41601)

### [888de24](https://github.com/sgl-project/sglang/commit/888de24cc8a5c919ec952be938c319a36442edbb)

- **作者**: BingjiaWang
- **时间**: 2026-10-09T09:31:38Z
- **提交信息**: Add BJWang-ant to CI_Permission (#43321)

### [e1c6ddc](https://github.com/sgl-project/sglang/commit/e1c6ddca1dad879aa0cecfb0d549f83de53d994c)

- **作者**: 黄孝君
- **时间**: 2026-10-09T09:30:38Z
- **提交信息**: [NPU] Bump SGLANG_KERNEL_NPU_TAG to 2026.9.0.post9 (#43340)

### [7cfecbe](https://github.com/sgl-project/sglang/commit/7cfecbef567c9d5b4e0656bc8b34c27454f344b5)

- **作者**: vOv
- **时间**: 2026-10-09T09:28:03Z
- **提交信息**: [diffusion][model] Add native SANA-Video 2.0 support (#41492)

Signed-off-by: cr-gao <gaochenrui@sjtu.edu.cn>
Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

### [4debae7](https://github.com/sgl-project/sglang/commit/4debae75348737b4960800a5bffeced62e37d842)

- **作者**: DevashishLal-CB
- **时间**: 2026-10-09T09:26:33Z
- **提交信息**: Add blackwell dual gemm fusion support for MLP (#41887)

Signed-off-by: Devashish Lal <devcode@meta.com>

### [5eca4d8](https://github.com/sgl-project/sglang/commit/5eca4d8caf1d0ef7f8c43b8701e51159da6a6468)

- **作者**: Thomas Wang
- **时间**: 2026-10-09T09:15:43Z
- **提交信息**: [AMD] Set maxseq length limit for DSV4.1 BCG metadata buffers (#42570)

### [23f8906](https://github.com/sgl-project/sglang/commit/23f890613e1798a99e9eee4453350f67751b1637)

- **作者**: Xinyi Song
- **时间**: 2026-10-09T09:08:44Z
- **提交信息**: [AMD] Patch aiter's group32 MXFP8 GEMM masked-scale fix (#43319)

### [14e3414](https://github.com/sgl-project/sglang/commit/14e3414513bc0a4b54ed6041f778ab5dc3fa5f9e)

- **作者**: Jimmy Shong
- **时间**: 2026-10-09T08:56:45Z
- **提交信息**: [Docs] Add Clef cookbook with selectable Clef Flash variant (#43235)

### [ff146fa](https://github.com/sgl-project/sglang/commit/ff146fa20c1b0da699c22cad843774461487a967)

- **作者**: amote-i
- **时间**: 2026-10-09T08:55:39Z
- **提交信息**: [NPU] [DOC] remove --enable-torch-compile from Ascend support matrix (#43336)

### [7578432](https://github.com/sgl-project/sglang/commit/7578432c217ef03cc859df0698eb1aa91b81175c)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-10-09T08:51:01Z
- **提交信息**: [LoRA][Test] Use the 0.9 ROUGE-L tolerance for the CUDA multi-LoRA batch test (#43297)

Co-authored-by: Mohammad Angkad <mohammad.angkad@radixark.ai>

### [d677848](https://github.com/sgl-project/sglang/commit/d677848968f997802cb200892139ed280df371a7)

- **作者**: Avaya Aggarwal
- **时间**: 2026-10-09T08:43:18Z
- **提交信息**: [diffusion] fix: fix CFG normalization to use per-sample norm instead of batch-flattened norm (#41706)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [3ab142a](https://github.com/sgl-project/sglang/commit/3ab142adc4c796229dc6d4f7049d811c968a5822)

- **作者**: Murthy L
- **时间**: 2026-10-09T08:40:09Z
- **提交信息**: [diffusion] feat: enable breakable CUDA graphs for FLUX.2 Klein (#36470)

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [b922f5c](https://github.com/sgl-project/sglang/commit/b922f5ca20872c2088af681f30451eef536b0dc3)

- **作者**: Mick
- **时间**: 2026-10-09T08:31:55Z
- **提交信息**: [diffusion] fix: share the IPC all-to-all transport between AllToAll4D and USP (#43269)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [17b2f35](https://github.com/sgl-project/sglang/commit/17b2f35ae71daeccadf8f1eb6b64413c6b0ed643)

- **作者**: Mick
- **时间**: 2026-10-09T08:30:55Z
- **提交信息**: [diffusion] refactor: remove unused helpers and write-only state (#43064)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [ee4e2f7](https://github.com/sgl-project/sglang/commit/ee4e2f78181743e6fddd29ddf4704bf73e98ab90)

- **作者**: James Xu
- **时间**: 2026-10-09T08:29:46Z
- **提交信息**: [diffusion] optimization: enable channels_last_3d for Cosmos3 VAE (#28021)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [dc0b394](https://github.com/sgl-project/sglang/commit/dc0b394471be5bb0738ea43d9ff24fe0aad2dba9)

- **作者**: Cheng Wan
- **时间**: 2026-10-09T08:27:46Z
- **提交信息**: [Refactor] Remove Kimi K3's own layer communication and let the consumer set an FFN's exit (#42936)

### [305ad55](https://github.com/sgl-project/sglang/commit/305ad5503da016b8ee40392aa4c52cb3538da81c)

- **作者**: Cheng Wan
- **时间**: 2026-10-09T08:27:23Z
- **提交信息**: [Refactor] Run Kimi K3's fused collectives through stage boundaries (#42898)

### [2b46904](https://github.com/sgl-project/sglang/commit/2b469040d2cc466726565c4ae203dde2bd802f9b)

- **作者**: Cheng Wan
- **时间**: 2026-10-09T08:27:00Z
- **提交信息**: [Refactor] Support attention-TP dense FFNs and unpadded batches on stage boundaries (#42897)

### [b9ae3d1](https://github.com/sgl-project/sglang/commit/b9ae3d1a65e1a30ae7f1f33e4ab983591b212203)

- **作者**: Cheng Wan
- **时间**: 2026-10-09T08:26:38Z
- **提交信息**: [Fix] Run attention on a padded extend batch's real rows (#42896)

### [7203747](https://github.com/sgl-project/sglang/commit/7203747cc89a23de8370aa34ede694d981524c58)

- **作者**: Cheng Wan
- **时间**: 2026-10-09T08:26:15Z
- **提交信息**: [Fix] Shard Kimi K3's shared experts over the TP group they sum over (#42895)

### [45ad463](https://github.com/sgl-project/sglang/commit/45ad463c8793cbfd2609d0f5e775784659cd29f7)

- **作者**: Mick
- **时间**: 2026-10-09T08:26:04Z
- **提交信息**: [diffusion] refactor: deduplicate UniPC solvers and Gemma3 shard loading (#42899)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [125f88c](https://github.com/sgl-project/sglang/commit/125f88cb759cccb3f73f4f7c29107af1066211d6)

- **作者**: Cheng Wan
- **时间**: 2026-10-09T08:25:51Z
- **提交信息**: [Refactor] Run Kimi K3 through stage boundaries (#42894)

### [666da4f](https://github.com/sgl-project/sglang/commit/666da4f56b3f27b549ffdc496b3a51d6696255c2)

- **作者**: Cheng Wan
- **时间**: 2026-10-09T08:25:28Z
- **提交信息**: [Fix] Kimi K3 KDA value head size and SiTU input alignment (#42893)

### [48a6c0a](https://github.com/sgl-project/sglang/commit/48a6c0a5d0012498e2e30e08c6930dab30eabc46)

- **作者**: Cheng Wan
- **时间**: 2026-10-09T08:25:05Z
- **提交信息**: [Fix] Return an FFN's output to the attention rows at a pipeline handoff (#42892)

### [b2402cc](https://github.com/sgl-project/sglang/commit/b2402ccad63a2f5313f770d46156676ff20ae30e)

- **作者**: Cheng Wan
- **时间**: 2026-10-09T08:24:42Z
- **提交信息**: [Fix] Merge DeepSeek-V4 two-batch-overlap microbatches without a residual (#42891)

### [b130f8a](https://github.com/sgl-project/sglang/commit/b130f8af0223c8cc9b3c89b88ea8d1a7dccad5a2)

- **作者**: Kan Wu
- **时间**: 2026-10-09T08:04:04Z
- **提交信息**: [sgl-router] Serve /v1/completions through /generate, with the shared OpenAI layer (#42997)

Co-authored-by: Kan Wu <kan.wu@radixark.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [f620d73](https://github.com/sgl-project/sglang/commit/f620d733d256c535b00d6e2f6b8e43c27fa81214)

- **作者**: Kan Wu
- **时间**: 2026-10-09T07:19:41Z
- **提交信息**: [rust-processor] Share the reasoning splitter and tool constraint across hosts (#42996)

Co-authored-by: Kan Wu <kan.wu@radixark.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Shangming Cai <csmthu@gmail.com>

### [37ae292](https://github.com/sgl-project/sglang/commit/37ae292e6f84cb8ec9503892d6cf74f9c8b2bfaf)

- **作者**: Mick
- **时间**: 2026-10-09T07:08:41Z
- **提交信息**: [diffusion] fix: skip LTX-2 SP masks only for globally unpadded sequences (#43134)

Co-authored-by: yatholam <yatholam@amd.com>
Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-10-10
**监控日期**: 2026-10-09
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1289
- **最后更新**: 2026-10-09T21:06:33Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-10-10
**监控日期**: 2026-10-09
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 93467
- **最后更新**: 2026-10-10T01:33:30Z

## 提交统计

- **昨日提交总数**: 58
- **提交者数量**: 50
- **主要提交者**: Taewoong Kim, wang.yuqi, Abhijit Roy

## AI分析总结

# vLLM 昨日提交分析总结

## 一、主要更新类型分布

- **Bug修复**（约20条）：占比最高，涵盖解码、结构化输出、NIXL、XPU、LoRA等模块
- **性能优化**（约12条）：MLA解码、ROCm/AMD、DSv4.1、Qwen4、kernel融合等
- **功能新增**（约12条）：Rust前端流式控制、cache salt、sharded state loader支持PP、HiSparse指标等
- **CI/工程**（约8条）：自动分片扩展、测试稳定性、pydantic固定等
- **文档更新**（约5条）：嵌入模型、CPU缓存配置等
- **安全**（1条）：Phi-4 MM音频注意力矩阵不保留

## 二、关键变更点与项目方向的关系

1. **多硬件生态深化**：Intel XPU（量化、KV offload、DP+EP修复）、AMD ROCm（QSA kernel融合、CUDA-graph offload、MQA logits）、NVIDIA持续投入（H200调优、3D激活量化融合）。直接支撑README中"人人可负担的快速LLM服务"的跨平台目标。

2. **Rust前端成熟化**：`--stream-interval`、reasoning控制传递、byte-level解码修复、内存优化（Box稀有字段）。表明前端层正成为生产级组件。

3. **投机解码与新模型支持**：GLM-5.3-Flash的packed KV布局+投机ring slots、DFlash2/EAGLE3 hidden state修复、自适应验证文档化。紧跟前沿架构落地。

4. **分布式与KV缓存**：NIXL不同P/D block size修复、Mooncake超时重试、sharded loader支持PP、WideEP文档。服务于大规模推理部署场景。

5. **基础设施可靠性**：CI自动分shard连续三批推进、ROCm/H200测试环境稳定、配置校验（max_num_scheduled_tokens=0、max_tokens语义修正、beam search拒绝等）。降低维护成本。

## 三、影响与意义

- **短期**：修复了投机解码、结构化输出、XPU量化等用户可见缺陷，提升稳定性；ROCm/XPU补强有利于扩大硬件覆盖用户群。
- **中期**：Rust前端和cache salt等特性为多模态/实时场景（如Voxtral realtime修复配套）铺路；CI分shard化加速大型仓库的迭代效率。
- **长期**：性能方向聚焦kernel融合（FP fusion、QSA融合）与低精度（MXFP8、FP8），符合"cheap serving"的成本承诺。

## 四、值得关注的技术点

1. **TokenSpeed MLA最小KV split配置**（#60345）：解码阶段内存调度精细化。
2. **shm tensor arena**（#51207）：CPU→GPU广播走共享内存，减少序列化开销——核心调度路径优化。
3. **int64索引映射修复row-offset溢出**（#60736）：超长序列场景的隐蔽正确性隐患。
4. **max_tokens语义修正**（#57035）：从"输入空间预留"改为"输出上界"，属API语义级变更，需关注下游兼容。
5. **Transformers 5.16.1去vendored化**（#60623）：减少代码分叉，依赖上游生态。
6. **DeepEP v2 NCCL版本说明**（#60449）：WideEP生态文档补全。

## 五、对项目发展的整体影响

这批提交反映出vLLM处于**"广度扩张+深度打磨"并行阶段**：一方面通过XPU/ROCm/Rust前端拓展能力边界和用户基数；另一方面以大量Bug修复、CI基建和语义修正夯实核心推理链路的可靠性，持续兑现其"easy, fast, and cheap"的定位承诺。多模态（Voxtral、Pixtral融合）与投机解码（GLM-5.3-Flash）的密集投入，显示项目正为下一代混合架构模型的规模化服务做准备。

## 详细提交记录

### [03a7d37](https://github.com/vllm-project/vllm/commit/03a7d3776fc2f520a70c8d2da1724eab6df6d0e1)

- **作者**: Wei Zhao
- **时间**: 2026-10-09T23:33:47Z
- **提交信息**: [Perf] Support minimum KV splits configuration for TokenSpeed MLA decode  (#60345)

Signed-off-by: Wei Zhao <51183510+wzhao18@users.noreply.github.com>
Signed-off-by: wzhao18 <wzhao18.sz@gmail.com>
Co-authored-by: Codex <noreply@openai.com>

### [04b02fc](https://github.com/vllm-project/vllm/commit/04b02fc8a56fc0140d8559b3a07d84b2fdc46ae8)

- **作者**: Bolin Sun
- **时间**: 2026-10-09T23:13:24Z
- **提交信息**: [Core] shm tensor arena for efficient cpu->gpu worker broadcast (#51207)

Signed-off-by: Bolin Sun <bolins@nvidia.com>
Signed-off-by: <bolins@nvidia.com>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>

### [fa94ad4](https://github.com/vllm-project/vllm/commit/fa94ad41431d7942abcd1adfffd3262edaed975a)

- **作者**: Rohan Potdar
- **时间**: 2026-10-09T22:54:06Z
- **提交信息**: [Test] Allow one bf16 ulp in the fused mHC post/pre residual check (#60724)

Signed-off-by: Rohan138 <rohanpotdar138@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [4c43254](https://github.com/vllm-project/vllm/commit/4c43254d52785d7a69300fdfb6c79987200c277c)

- **作者**: Matthew Bonanni
- **时间**: 2026-10-09T22:45:34Z
- **提交信息**: [HiSparse] Report host-pool block residency as HiSparse metrics (#59485)

Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [783ac12](https://github.com/vllm-project/vllm/commit/783ac12071ec319d7d3e5af29d039034115d8934)

- **作者**: Kevin H. Luu
- **时间**: 2026-10-09T22:43:37Z
- **提交信息**: [CI] Accept whitespace around /ci commands and reply instead of going silent (#60925)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [ed7ae70](https://github.com/vllm-project/vllm/commit/ed7ae705a1f366c2008964af562a7543e91d934e)

- **作者**: Nick Hill
- **时间**: 2026-10-09T21:38:11Z
- **提交信息**: [Bugfix][MRV2] Use int64 index mappings to fix row-offset overflow (#60736)

Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: vllmellm <vllm.ellm@embeddedllm.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [51144dd](https://github.com/vllm-project/vllm/commit/51144dd83ec557afa6fc6032bbf03d7f50a55b89)

- **作者**: Ting SUN
- **时间**: 2026-10-09T21:22:31Z
- **提交信息**: [Bugfix][Spec Decode] Trim token_ids/logprobs left past a stop string under speculative decoding (#47616)

Signed-off-by: Ting Sun <suntcrick@gmail.com>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [35e920d](https://github.com/vllm-project/vllm/commit/35e920d671539d7066b648dc82058f8ef5348b9f)

- **作者**: Bugen Zhao
- **时间**: 2026-10-09T21:10:42Z
- **提交信息**: [Rust Frontend] Support `--stream-interval` and per-request `stream_interval` (#60589)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [ffdde24](https://github.com/vllm-project/vllm/commit/ffdde24f546c503c7e47c5264b180c16fd668888)

- **作者**: Giancarlo Delfin
- **时间**: 2026-10-09T20:54:40Z
- **提交信息**: [Docs] Document adaptive verification without a confidence head (#60913)

Signed-off-by: Giancarlo Delfin <gdelfin@inferact.ai>

### [e0cb3ef](https://github.com/vllm-project/vllm/commit/e0cb3efce05388e21454556193d4069984b3154a)

- **作者**: Kai Hoang
- **时间**: 2026-10-09T20:52:08Z
- **提交信息**: [Bugfix][Structured Output] Decode choice specs as JSON in outlines and LMFE (#60748)

Signed-off-by: hpdkhoa <hpdkhoa2311@gmail.com>
Co-authored-by: Flora Feng <4florafeng@gmail.com>

### [02e55d2](https://github.com/vllm-project/vllm/commit/02e55d2af38adab51ec5ffb985063d355b20805b)

- **作者**: Dakai An
- **时间**: 2026-10-09T19:48:37Z
- **提交信息**: [KV Cache] GLM-5.3-Flash: use the generic packed KV layout; CircularBufferSpec tail with speculative ring slots (#57169)

Signed-off-by: Yifan Qiao <yifanqiao@inferact.ai>
Signed-off-by: Dakai An <dakaian108@gmail.com>
Signed-off-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: Yifan Qiao <yifanqiao@inferact.ai>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: Lucas Wilkinson <LucasWilkinson@users.noreply.github.com>

### [3766a67](https://github.com/vllm-project/vllm/commit/3766a67a32f7ea8130d84383f72883cee5e8b006)

- **作者**: Misha Goin
- **时间**: 2026-10-09T19:34:58Z
- **提交信息**: [WideEP] Explain how to fix a too-old NCCL for DeepEP v2 (#60449)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [0446273](https://github.com/vllm-project/vllm/commit/04462732a40a8329ad60593d754b576c54c5fe5d)

- **作者**: Vadim Gimpelson
- **时间**: 2026-10-09T19:15:10Z
- **提交信息**: [Bugfix] Reject max_num_scheduled_tokens=0 at config time instead of hanging (#60714)

Signed-off-by: Vadim Gimpelson <vadim.gimpelson@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Hui Li <40770106+untrall@users.noreply.github.com>

### [ad8a606](https://github.com/vllm-project/vllm/commit/ad8a6065f4bcbdfafd38828a4b3f1c6fac4dbf89)

- **作者**: Willow Lopez
- **时间**: 2026-10-09T18:59:02Z
- **提交信息**: [Bugfix] Validate guidance tokenizer compatibility before EngineCore (#52298)

Signed-off-by: Oxygen56 <jiangth99@163.com>
Signed-off-by: Artem Perevedentsev <aperevedents@nvidia.com>
Co-authored-by: Artem Perevedentsev <aperevedents@nvidia.com>

### [1dc60dd](https://github.com/vllm-project/vllm/commit/1dc60dd36734f4436dbc438265bbd9c24164cbad)

- **作者**: Misha Goin
- **时间**: 2026-10-09T18:42:41Z
- **提交信息**: [CI] Pin pydantic in the mypy pre-commit hook (#60894)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [a0f28d7](https://github.com/vllm-project/vllm/commit/a0f28d73a83bbf0491428efb0f11c2b8f9dc9067)

- **作者**: Ning Xie
- **时间**: 2026-10-09T18:08:31Z
- **提交信息**: [sharded state loader] support pp in sharded state loader (#52110)

Signed-off-by: Andy Xie <andy.xning@gmail.com>
Co-authored-by: Simon Mo <simon.mo@hey.com>

### [c811943](https://github.com/vllm-project/vllm/commit/c811943137dbfecdf9c7af849bc66270917a9d79)

- **作者**: premsurawut
- **时间**: 2026-10-09T18:06:26Z
- **提交信息**: [Bugfix][Frontend] Reject beam search with echo and logprobs in /v1/completions (#60876)

Signed-off-by: surawut.j <surawut.jirasaktavee@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [5dc9bcd](https://github.com/vllm-project/vllm/commit/5dc9bcd8cd9656b852edfd6c5b4a8c9c46a34530)

- **作者**: Bugen Zhao
- **时间**: 2026-10-09T18:04:49Z
- **提交信息**: [Rust Frontend] Pass reasoning controls through render -> generate (#60546)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [ce4603c](https://github.com/vllm-project/vllm/commit/ce4603cad676af27f08f39b696a31a4022eb9ca4)

- **作者**: Bugen Zhao
- **时间**: 2026-10-09T18:04:00Z
- **提交信息**: [Bugfix][Rust Frontend] Pass through raw characters in byte-level decode (#59861)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [9a585c6](https://github.com/vllm-project/vllm/commit/9a585c62aade0bfd290dfc7a975d54cab8ebfa54)

- **作者**: Bugen Zhao
- **时间**: 2026-10-09T18:01:16Z
- **提交信息**: [Rust Frontend] Box rarely-set fields of per-token output types (#60588)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [1a3a7a8](https://github.com/vllm-project/vllm/commit/1a3a7a8f01a8c1a3184151b8185072efda11daab)

- **作者**: Yuvraj Singh Bhadoria
- **时间**: 2026-10-09T17:15:22Z
- **提交信息**: [Bugfix] Treat max_tokens as output upper bound, not input-space reservation (#57035)

Signed-off-by: YuvrajSinghBhadoria2 <245782664+YuvrajSinghBhadoria2@users.noreply.github.com>
Signed-off-by: YuvrajSinghBhadoria2 <yuvrajsinghbhado2030@gmail.com>
Signed-off-by: Yuvraj Singh Bhadoria <yuvrajsinghbhado2030@gmail.com>
Co-authored-by: YuvrajSinghBhadoria2 <245782664+YuvrajSinghBhadoria2@users.noreply.github.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>
Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [89ac8d9](https://github.com/vllm-project/vllm/commit/89ac8d971be7d2f598598c1551a21c646bdf8b0d)

- **作者**: Andrey Talman
- **时间**: 2026-10-09T16:59:17Z
- **提交信息**: [CI][Test] Allow 10% ngram acceptance drop under preemption on CUDA in test_async_scheduling_accuracy (#60715)

Signed-off-by: Andrey Talman <atalman@users.noreply.github.com>
Co-authored-by: Andrey Talman <atalman@users.noreply.github.com>

### [b742338](https://github.com/vllm-project/vllm/commit/b74233860d4f2419ac5a763f6c83859bfe742ad0)

- **作者**: stefankoncarevic
- **时间**: 2026-10-09T16:48:43Z
- **提交信息**: [CI][ROCm] Wait for VRAM to settle before building LLM in test_full_graph (#60872)

Signed-off-by: Stefan Koncarevic <Stefan.Koncarevic@amd.com>

### [75e3b17](https://github.com/vllm-project/vllm/commit/75e3b17c055c609f02c64cd4ad3f8692b8170d8e)

- **作者**: Taewoong Kim
- **时间**: 2026-10-09T16:07:50Z
- **提交信息**: [Frontend] Add cache salt support to generative scoring (#60841)

Signed-off-by: Taewoong Kim <ktw2172@gmail.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>

### [90ba2f3](https://github.com/vllm-project/vllm/commit/90ba2f34b5a29d85b8301672e5735676f78fa00c)

- **作者**: Greg Pereira
- **时间**: 2026-10-09T15:05:54Z
- **提交信息**: [Build] Find compatible published wheels for precompiled installs (#58871)

Signed-off-by: greg pereira <grpereir@redhat.com>
Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [970dc63](https://github.com/vllm-project/vllm/commit/970dc63478da41409dec009690f462e8e33d22f2)

- **作者**: Abhijit Roy
- **时间**: 2026-10-09T14:41:38Z
- **提交信息**: [Docs] Add Giga-Embeddings bidirectional Qwen3 usage to embed docs (#60854)

Signed-off-by: Abhijit <abroy@redhat.com>

### [a6b39f0](https://github.com/vllm-project/vllm/commit/a6b39f02620e23422113823810148dfda9876304)

- **作者**: Taneem Ibrahim
- **时间**: 2026-10-09T14:32:47Z
- **提交信息**: [Bugfix] Clean up async client sockets after event loop closure (#57757)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [fc39317](https://github.com/vllm-project/vllm/commit/fc39317392714b571868d7a49239db471f2dee0d)

- **作者**: Warren Deng
- **时间**: 2026-10-09T14:25:41Z
- **提交信息**: [Bugfix][Kernel] Remove invalid NC from Kimi-K3 KDA autotune keys (#60446)

Signed-off-by: Warren Deng <warrdeng@meta.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [3d52578](https://github.com/vllm-project/vllm/commit/3d52578e13454de0bb8352cac988347cdcc89928)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-10-09T14:23:35Z
- **提交信息**: [Security] Do not retain Phi-4 MM audio attention matrices (#60614)

Signed-off-by: Juan Pérez de Algaba <jperezde@redhat.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [81c9936](https://github.com/vllm-project/vllm/commit/81c993658e0bbdbf9d30c92cfc52baa73853b242)

- **作者**: Mikko Tukiainen
- **时间**: 2026-10-09T13:14:49Z
- **提交信息**: [ROCm][Perf] Fuse main QK-norm/RoPE/gate and KV-cache write into the AMD QSA prepare launch (#59732)

Signed-off-by: Mikko Tukiainen <Mikko.Tukiainen@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [9adba10](https://github.com/vllm-project/vllm/commit/9adba10f3f4bb3bb756f9de53fbf6820668157db)

- **作者**: Li, Jiang
- **时间**: 2026-10-09T12:48:32Z
- **提交信息**: [Bugfix] Fix pre-commit check (#60840)

Signed-off-by: jiang1.li <jiang1.li@intel.com>

### [1ee69dd](https://github.com/vllm-project/vllm/commit/1ee69dde9cdfc949cfae896016b44357ca864a50)

- **作者**: Suraj Sharan
- **时间**: 2026-10-09T12:39:58Z
- **提交信息**: [Bugfix][LoRA] Reject PEFT adapter features vLLM does not implement (#60225)

Signed-off-by: suraj <surajsharan85@gmail.com>
Co-authored-by: linitra24 <renshuang.zhou@daocloud.io>

### [c17fadc](https://github.com/vllm-project/vllm/commit/c17fadcfdc80c9f8cfa97a7eec02a66d823989c4)

- **作者**: Yan Ma
- **时间**: 2026-10-09T12:16:35Z
- **提交信息**: [XPU] fix fused_input_norm for MM (#59865)

Signed-off-by: Yan Ma <yan.ma@intel.com>

### [0cc0460](https://github.com/vllm-project/vllm/commit/0cc046087024bdb403b2032617ea0f713209a185)

- **作者**: YiSheng5
- **时间**: 2026-10-09T12:01:54Z
- **提交信息**: [XPU]Fix the accuracy issue when meet topk_ids=-1 on DP+EP scenarios (#57787)

Signed-off-by: yisheng <yi.sheng@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [196483e](https://github.com/vllm-project/vllm/commit/196483e25b43511e13aa179ed52f50574ecd9fee)

- **作者**: Louie Tsai
- **时间**: 2026-10-09T11:44:09Z
- **提交信息**: [Tools] Recipes sweep workflow (#57307)

Signed-off-by: louie-tsai <louie.tsai@intel.com>

### [1c47ebf](https://github.com/vllm-project/vllm/commit/1c47ebfc57d9e2415486e6080027ba319c73362a)

- **作者**: Praneeth Reddy A
- **时间**: 2026-10-09T11:43:55Z
- **提交信息**: [Docs] Fix VLLM_CPU_KVCACHE_SPACE default and units (#60053)

Signed-off-by: Praneeth <praneethreddyarikatla@gmail.com>
Co-authored-by: Li, Jiang <jiang1.li@intel.com>

### [d095e61](https://github.com/vllm-project/vllm/commit/d095e61c0b389753ae86ccd7b2b7d1f2e1f5cd58)

- **作者**: Chen Cheng
- **时间**: 2026-10-09T11:35:48Z
- **提交信息**: [Bugfix][Spec Decode] Fix GLM-5.3-Flash DFlash2/EAGLE3 aux hidden-state capture with the upstream config (#60763)

Signed-off-by: Chen Cheng <85005591+ischencheng@users.noreply.github.com>
Signed-off-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>

### [7368fad](https://github.com/vllm-project/vllm/commit/7368fadebd6c3f0c470d0e64b62cf6eea3b0987d)

- **作者**: wang.yuqi
- **时间**: 2026-10-09T11:34:38Z
- **提交信息**: [CI Failure] Move MTEB tests to h200_35gb (#60817)

Signed-off-by: wang.yuqi <yuqi.wang@daocloud.io>

### [83ed0c7](https://github.com/vllm-project/vllm/commit/83ed0c7c0944e9d124589d8fa3f82a019343a726)

- **作者**: Luca Motz
- **时间**: 2026-10-09T11:30:11Z
- **提交信息**: [Bugfix][NIXL] Fix receive post-process for different P/D block sizes (#58860)

Signed-off-by: Luca Motz <luca.motz@icloud.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [28d76f3](https://github.com/vllm-project/vllm/commit/28d76f3bad3df9270019b850a5c29f241b3d7bbf)

- **作者**: Shreyansh Jain
- **时间**: 2026-10-09T11:16:13Z
- **提交信息**: [Bugfix][Structured Output] Reject unsupported regex inside groups (#60359)

Signed-off-by: Shreyansh Jain <shreyanshjain646@gmail.com>
Signed-off-by: Artem Perevedentsev <aperevedents@nvidia.com>
Co-authored-by: Artem Perevedentsev <aperevedents@nvidia.com>

### [b027ac8](https://github.com/vllm-project/vllm/commit/b027ac831253e83ff605a2ff5d4aa7c00619802c)

- **作者**: Chaojun Zhang
- **时间**: 2026-10-09T10:58:07Z
- **提交信息**: [XPU] Support register KV offload mmap region as pinned host memory on XPU (#51956)

Signed-off-by: Chaojun Zhang <chaojun.zhang@intel.com>

### [5cadabf](https://github.com/vllm-project/vllm/commit/5cadabfafde31dcccf4e1f773d00cc6e8a134cfb)

- **作者**: yuvalluria
- **时间**: 2026-10-09T10:41:29Z
- **提交信息**: [Docs] Add Qwen2.5-Coder-7B-Instruct to batch invariance tested models (#46368)

Signed-off-by: Yuval Luria <yluria@redhat.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [4e318ac](https://github.com/vllm-project/vllm/commit/4e318ac56319476be1bc81f44acaf99516891afb)

- **作者**: Yan Ma
- **时间**: 2026-10-09T10:38:01Z
- **提交信息**: [XPU] fix online fp8_per_channel quantization (#56027)

Signed-off-by: Yan Ma <yan.ma@intel.com>

### [efd1410](https://github.com/vllm-project/vllm/commit/efd141047d8e879536806a86e3f93c02e6164add)

- **作者**: Thang Nguyen
- **时间**: 2026-10-09T10:26:47Z
- **提交信息**: [CI] Enroll a third batch of five steps in automatic sharding (#60757)

Signed-off-by: Thang Nguyen <thangnguyenvn647@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [b8bd335](https://github.com/vllm-project/vllm/commit/b8bd3357548ac07b1877053b6c5ba415763bad36)

- **作者**: Thang Nguyen
- **时间**: 2026-10-09T10:26:27Z
- **提交信息**: [CI] Enroll five more steps in automatic sharding (#60662)

Signed-off-by: Thang Nguyen <thangnguyenvn647@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [59ffd73](https://github.com/vllm-project/vllm/commit/59ffd73e8597d860730f4a8c4f778f27c75a0dfa)

- **作者**: Warren Deng
- **时间**: 2026-10-09T09:46:41Z
- **提交信息**: [Bugfix][Kernel] Restore FP fusion for indexer Q quantization (#60716)

Signed-off-by: Warren Deng <warrdeng@meta.com>

### [2186b89](https://github.com/vllm-project/vllm/commit/2186b89a9a02fac11fa0e274f3201b9812dbf65c)

- **作者**: Damien Laine
- **时间**: 2026-10-09T09:40:29Z
- **提交信息**: [Bugfix][Model] Voxtral realtime: fix boot OOM and engine crash at max_model_len (#45022)

Signed-off-by: Damien Laine <damien.laine@gmail.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>

### [2c99ee9](https://github.com/vllm-project/vllm/commit/2c99ee9333821030daf84718b2a76ea28d94ba3c)

- **作者**: Harry Mellor
- **时间**: 2026-10-09T09:29:03Z
- **提交信息**: [Chore] Remove vendored code made redundant by Transformers 5.16.1 (#60623)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [bc713cf](https://github.com/vllm-project/vllm/commit/bc713cf8cc861c0d0ccfe46c9ce322ab81993ace)

- **作者**: Chao Lei
- **时间**: 2026-10-09T09:19:33Z
- **提交信息**: [Bugfix]MooncakeConnect add query timeout and retry (#55923)

### [18c19ea](https://github.com/vllm-project/vllm/commit/18c19eaf239f09bc2543637c73f3b2d05f9bf5c5)

- **作者**: Taewoong Kim
- **时间**: 2026-10-09T08:53:50Z
- **提交信息**: [Frontend] Add cache salt and tracing to structured decisions (#60786)

Signed-off-by: Taewoong Kim <ktw2172@gmail.com>
Co-authored-by: Chauncey <chaunceyjiang@gmail.com>

### [a6f43e5](https://github.com/vllm-project/vllm/commit/a6f43e57d6bdcbe1a42cc07fd5298ae33052180d)

- **作者**: aoshen02
- **时间**: 2026-10-09T08:29:55Z
- **提交信息**: [ROCm] Enable the cuMem CUDA-graph pool offload on ROCm (#59523)

Signed-off-by: aoshen02 <aoshen@inferact.ai>
Signed-off-by: indianspeedster <cspandey016@gmail.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: indianspeedster <cspandey016@gmail.com>

### [bacbbe1](https://github.com/vllm-project/vllm/commit/bacbbe187885db62859f5a4a1443f8ec3006e987)

- **作者**: The Anh Nguyen
- **时间**: 2026-10-09T08:22:18Z
- **提交信息**: [Bugfix][NIXL] Guard record_transfer against None telemetry (#57734)

Signed-off-by: The Anh Nguyen <ntheanh201@gmail.com>

### [560fae6](https://github.com/vllm-project/vllm/commit/560fae64cdaf84468590fd362916969f18bb4d9b)

- **作者**: Sriram Kumar
- **时间**: 2026-10-09T08:16:20Z
- **提交信息**: [ROCm][Bugfix] Pass per-sequence context lengths to the AITER paged MQA-logits kernels (#59420)

Signed-off-by: Sriram Kumar <sriramkumar.kishorekumar@amd.com>

### [8a03ccf](https://github.com/vllm-project/vllm/commit/8a03ccf7b3a26dc0c6ccf2a3ba12113475824db3)

- **作者**: Maroon Ayoub
- **时间**: 2026-10-09T08:14:13Z
- **提交信息**: [Frontend] Add return_mm_kwargs to render requests (#60728)

Signed-off-by: Maroon Ayoub <mayoub@redhat.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [f43e4c3](https://github.com/vllm-project/vllm/commit/f43e4c39e30120abf6250a209a42e5cd4849ca23)

- **作者**: Denis Ermakov
- **时间**: 2026-10-09T07:49:47Z
- **提交信息**: [Structured Output] Allow propertyNames with additionalProperties on xgrammar (#57594)

Signed-off-by: errmakov <ide404@gmail.com>
Signed-off-by: Artem Perevedentsev <aperevedents@nvidia.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: Artem Perevedentsev <aperevedents@nvidia.com>

### [efaca95](https://github.com/vllm-project/vllm/commit/efaca9547dbdfd2d5269f274aaf3798c1f730435)

- **作者**: Juntian Liu
- **时间**: 2026-10-09T07:30:18Z
- **提交信息**: [Perf][DSv4.1] Exchange packed FP8 Engram rows across DP and feed wkv MXFP8 (#59923)

Signed-off-by: Juntian Liu <Juntianl777@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [82e89e9](https://github.com/vllm-project/vllm/commit/82e89e99440661f3404c58c9c60d712657305cac)

- **作者**: Zheng Cai
- **时间**: 2026-10-09T07:18:50Z
- **提交信息**: [Perf][Qwen4Exp] Retune H200 M=4 merged QSA LL-GEMM plan (#60776)

Signed-off-by: zigzagcai <zigzagcai@users.noreply.github.com>
Co-authored-by: zigzagcai <zigzagcai@users.noreply.github.com>
Co-authored-by: Claude Code <noreply@anthropic.com>

### [19c0bed](https://github.com/vllm-project/vllm/commit/19c0bed584bde3fe785296d2923247ab9d678483)

- **作者**: Jakub Zakrzewski
- **时间**: 2026-10-09T07:12:03Z
- **提交信息**: [Fusion] Support 3D activation quantization fusion and enable it for Pixtral (#59612)

Signed-off-by: Jakub Zakrzewski <jzakrzewski@nvidia.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Misha Goin <mgoin64@gmail.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-10-10
**监控日期**: 2026-10-09
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7107
- **最后更新**: 2026-10-10T00:02:46Z

## 提交统计

- **昨日提交总数**: 15
- **提交者数量**: 8
- **主要提交者**: haic0, Yueqian Lin, NumberWan

## AI分析总结

# vllm-omni 昨日提交分析总结

## 1. 主要更新类型
本次15条提交中，**性能优化**（4条）和 **Bug修复/测试修复**（4条）占比最高，其次是**新功能支持**（如MUSA硬件适配）、**模型功能扩展**（MiniMax-H3、MOSS-TTS）和**CI/测试增强**（2条），内核级优化1条。

## 2. 关键变更点与项目方向的关系
- **多硬件生态扩展**：MUSA（摩尔线程）GPU的 MAGI-2 模型支持（#8498）及后续的BF16 MoE GEMM优化、FP32 mHC流收缩、W13 bank修复、int32路由计数等一系列打磨，体现了项目"面向所有人提供低成本多模态推理服务"的普惠目标——持续拓宽硬件后端覆盖面。
- **模型管线优化（MiniMax-H3）**：独立VAE解码阶段支持（#8104）、参考音频提取与视频解码重叠执行（#8229）、RGB帧转换减少（#8129），三条提交共同指向音视频多模态模型的流水线并行化与冗余计算消除。
- **音频/TTS链路加速**：MOSS-TTS 的快速PCM转换与stage0首帧codec（#8640）、PersonaPlex 每个音频块只发送一帧codec（#8662），提升实时语音生成吞吐。
- **内核层优化**：Ring attention 输出融合（#8494），减少分布式注意力场景的kernel launch和中间拷贝。
- **服务稳定性与CI治理**：Duplex会话在session.created未送达客户端时正确关闭（#7997）修复了会话泄漏；PersonaPlex负载驱动器保持在capture时钟（#8650）及压力测试移至nightly（#8670），平衡CI时长与覆盖度；Qwen3 Omni Thinker变体测试补充（#4944）增强模型回归防护。

## 3. 对项目的影响
- 端到端延迟和吞吐得到系统性改善（视频-音频解码重叠、内核融合、codec帧精简）。
- MUSA等国产硬件的首发支持+快速迭代修复，降低新硬件引入的稳定性风险。
- CI从PR门禁向nightly迁移压力测试，减少主线阻塞，加快合并节奏。
- 会话管理修复直接提升在线服务（Realtime/Duplex API场景）的资源正确性。

## 4. 值得关注的技术点
- **MUSA MoE优化组合拳**：64宽K tile的BF16 MoE GEMM、FP32 mHC流收缩、int32路由计数，是典型的"从数值精度到内存布局"的分层优化思路，且修复了融合路径中bank复用的正确性问题。
- **Ring attention 输出融合**：将分布式attention尾部的多次规约/拼接合并，对长上下文多模态推理意义明显。
- **流水线重叠（overlap）模式**：MiniMax-H3 用视频解码掩盖音频提取开销，是多模态serving中异构计算协同的实用范式。

## 5. 对项目发展的意义
结合README定位（"Easy, fast, and cheap omni-modality model serving for everyone"），这批提交精准服务三大支柱：**fast**——通过内核融合、流水线重叠、codec精简持续压低延迟；**everyone**——MUSA首发与快速迭代扩展硬件可及性；**easy/cheap**——CI治理与会话修复保障开发者体验和服务成本可控。多条MiniMax-H3与PersonaPlex的连续提交表明这两个omni模型正被系统性打磨至生产可用状态，是项目"全模态serving"叙事的核心载体。总体上，项目处于从"能跑"向"跑得快、跑得稳、跑在更多硬件上"的成熟化阶段演进。

## 详细提交记录

### [b65107d](https://github.com/vllm-project/vllm-omni/commit/b65107d61331327424910c72e7a2da137dcfb3df)

- **作者**: haic0
- **时间**: 2026-10-09T17:47:54Z
- **提交信息**: [CI/Build][ROCm] Move PersonaPlex temporal stress to nightly (#8670)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>
Signed-off-by: andyluo7 <andy.luo@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [f3391da](https://github.com/vllm-project/vllm-omni/commit/f3391da7c58ee8dc990829aab82166edf865d19b)

- **作者**: Clodagh Walsh
- **时间**: 2026-10-09T14:33:43Z
- **提交信息**: [CI] Add tests for Qwen3 Omni Thinker variant (#4944)

Signed-off-by: Clodagh Walsh <clodaghwalsh17@gmail.com>

### [4c5541c](https://github.com/vllm-project/vllm-omni/commit/4c5541cfc17143f80bdb89bbb7a5840b08bb52c6)

- **作者**: R0CKSTAR
- **时间**: 2026-10-09T10:31:31Z
- **提交信息**: [Perf] MAGI-2: use FP32 mHC stream contractions on MUSA (#8510)

Signed-off-by: Xiaodong Ye <xiaodong.ye@mthreads.com>

### [7d08e4e](https://github.com/vllm-project/vllm-omni/commit/7d08e4e66c9f611d29f3e273d6d0e401c54dc4a6)

- **作者**: R0CKSTAR
- **时间**: 2026-10-09T10:31:04Z
- **提交信息**: [Model][Hardware][MUSA] Add MAGI-2 Preview MUSA support (#8498)

Signed-off-by: Xiaodong Ye <xiaodong.ye@mthreads.com>

### [7eb48e6](https://github.com/vllm-project/vllm-omni/commit/7eb48e647dec0cdf70189044bb5bb12bca222c58)

- **作者**: Canlin Guo
- **时间**: 2026-10-09T10:29:36Z
- **提交信息**: [MOSS-TTS] Fast pcm convert and first-frame codec in stage0 (#8640)

Signed-off-by: Canlin Guo <canlinguosdu@gmail.com>

### [e5efa0f](https://github.com/vllm-project/vllm-omni/commit/e5efa0fea57b73ac249851c8d3dea15070c7114b)

- **作者**: R0CKSTAR
- **时间**: 2026-10-09T10:22:15Z
- **提交信息**: [Bugfix] MAGI-2: keep a single W13 bank for the fused BF16 MoE path (#8497)

Signed-off-by: Xiaodong Ye <xiaodong.ye@mthreads.com>

### [877e9c2](https://github.com/vllm-project/vllm-omni/commit/877e9c2f866703f7b82e259442aa465314a705b1)

- **作者**: R0CKSTAR
- **时间**: 2026-10-09T10:19:35Z
- **提交信息**: [Perf] MAGI-2: use a 64-wide K tile for the BF16 MoE GEMMs on MUSA (#8506)

Signed-off-by: Xiaodong Ye <xiaodong.ye@mthreads.com>

### [2b2a5f0](https://github.com/vllm-project/vllm-omni/commit/2b2a5f00602b0308d9d99bb897681c7ce8e43f25)

- **作者**: R0CKSTAR
- **时间**: 2026-10-09T10:18:19Z
- **提交信息**: [Perf] MAGI-2: count BF16 MoE routes in int32 (#8496)

Signed-off-by: Xiaodong Ye <xiaodong.ye@mthreads.com>

### [3b666e9](https://github.com/vllm-project/vllm-omni/commit/3b666e9196528f00edb6ad9f558bfafde5d6cddf)

- **作者**: NumberWan
- **时间**: 2026-10-09T09:41:06Z
- **提交信息**: [Bugfix][Duplex] Close session when session.created never reaches the client  (#7997)

Signed-off-by: NumberWan <wantszkin2003@gmail.com>
Co-authored-by: NATURE <wzliu@connect.hku.hk>

### [ee81f33](https://github.com/vllm-project/vllm-omni/commit/ee81f33001922f8d91dd09da0a57ee1531a8df82)

- **作者**: QianCyrus
- **时间**: 2026-10-09T08:25:57Z
- **提交信息**: [Kernel][Core] Fuse Ring attention output merging (#8494)

Signed-off-by: QianCyrus <101633534+QianCyrus@users.noreply.github.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [06afa31](https://github.com/vllm-project/vllm-omni/commit/06afa310c942c0506f0ed9bdd189fa331c46bb97)

- **作者**: Dong1017
- **时间**: 2026-10-09T07:57:22Z
- **提交信息**: [Model] Overlap MiniMax-H3 reference audio extraction with video decode (#8229)

Signed-off-by: GUOGUO <xwdong1998@163.com>

### [d8bfc78](https://github.com/vllm-project/vllm-omni/commit/d8bfc78ecfbaeddcfd8c7359aab8751899436515)

- **作者**: Yueqian Lin
- **时间**: 2026-10-09T07:56:02Z
- **提交信息**: [Bugfix][Test] Keep the PersonaPlex load driver on the capture clock (#8650)

Signed-off-by: Yueqian Lin <linyueqian@outlook.com>

### [d0b0cfd](https://github.com/vllm-project/vllm-omni/commit/d0b0cfd02e79eab631fec7cd9437cd88fe11245f)

- **作者**: Dong1017
- **时间**: 2026-10-09T07:53:45Z
- **提交信息**: [Model] MiniMax-H3: Support an independent VAE decoder stage (#8104)

Signed-off-by: GUOGUO <xwdong1998@163.com>

### [36082d2](https://github.com/vllm-project/vllm-omni/commit/36082d2ec47b1d524bb08234fc71a4f594d3eb62)

- **作者**: Yueqian Lin
- **时间**: 2026-10-09T07:39:57Z
- **提交信息**: [Perf][PersonaPlex] Send one codec frame per audio chunk (#8662)

Signed-off-by: Yueqian Lin <linyueqian@outlook.com>

### [88a35c0](https://github.com/vllm-project/vllm-omni/commit/88a35c092107317ea42f5578b7cae3485f18ce70)

- **作者**: Dong1017
- **时间**: 2026-10-09T07:24:06Z
- **提交信息**: [Model] Reduce MiniMax-H3 Ref2VA RGB frame conversion (#8129)

Signed-off-by: GUOGUO <xwdong1998@163.com>

---
