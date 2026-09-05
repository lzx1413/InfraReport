# GitHub Stars 合并报告 - 2026-09-05

**合并日期**: 2026-09-06
**监控日期**: 2026-09-05
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


**报告日期**: 2026-09-06
**监控日期**: 2026-09-05
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2193
- **最后更新**: 2026-09-05T23:09:22Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-09-06
**监控日期**: 2026-09-05
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2780
- **最后更新**: 2026-09-05T07:09:25Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Bilang ZHANG

## AI分析总结

### 提交分析总结

**1. 主要更新类型**  
本次提交属于 **Bug修复**，具体针对Wan系列视频生成模型的蒸馏预设配置进行对齐修正，属于模型推理链路中的细节调优。

**2. 关键变更点与项目方向关系**  
- 变更内容：修复了在**禁用CFG（Classifier-Free Guidance）** 场景下，Wan模型的蒸馏预设（distillation presets）与预期行为不一致的问题。  
- 与项目方向关联：LightX2V定位为**轻量级视频生成推理框架**，核心目标是提升推理效率与灵活性。蒸馏技术是模型压缩和加速的关键手段，而CFG是控制生成质量与多样性平衡的重要机制。该修复确保在关闭CFG时，蒸馏预设仍能正确生效，直接服务于框架“轻量高效”的核心理念。

**3. 对项目的影响与潜在意义**  
- **影响**：修复后，使用Wan模型且选择关闭CFG的用户，将获得更稳定、可预期的生成结果，避免因预设错位导致的输出异常或性能退化。  
- **潜在意义**：  
  - 增强框架对**不同推理配置组合**的兼容性，降低用户使用门槛。  
  - 为后续支持更多模型或更复杂的蒸馏策略打下基础，体现项目对细节正确性的重视。  
  - 可能间接提升在低资源或实时推理场景下的可用性，因为关闭CFG常被用于加速。

**4. 值得关注的技术点**  
- **CFG与蒸馏的交互逻辑**：蒸馏模型通常已内化条件信息，关闭CFG时需确保预设参数（如引导强度、步数）能自动适配，避免冲突。  
- **预设对齐机制**：修复可能涉及对预设配置的校验或动态调整逻辑，确保不同开关组合下的一致性，这是框架设计中对“配置可组合性”的体现。

**5. 对项目发展的影响**  
基于README中“轻量视频生成推理框架”的定位，该修复虽小但意义明确：  
- **巩固可靠性**：在追求速度与低资源占用的同时，保证输出质量不因配置简化而受损，增强用户信任。  
- **支持生态扩展**：Wan是当前主流视频生成模型之一，对其蒸馏场景的精细支持，有助于吸引更多开发者基于LightX2V进行二次开发或部署。  
- **长期方向**：此类细节修复表明项目已进入**成熟优化阶段**，从“功能可用”转向“场景适配与鲁棒性提升”，为未来支持更多模型架构和推理优化策略奠定基础。

**总结**：本次提交是面向特定模型（Wan）与特定配置（禁用CFG）的精准修复，虽不涉及新功能，但通过消除配置组合下的潜在缺陷，强化了框架的通用性与可靠性，符合LightX2V作为轻量级、高灵活性推理框架的长期发展目标。

## 详细提交记录

### [bb964f8](https://github.com/ModelTC/LightX2V/commit/bb964f8a125ab5147b4645ec6895b727e67f37ba)

- **作者**: Bilang ZHANG
- **时间**: 2026-09-05T07:09:21Z
- **提交信息**: fix(wan): align CFG-disabled distillation presets (#1486)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-09-06
**监控日期**: 2026-09-05
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2236
- **最后更新**: 2026-09-04T17:45:19Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-09-06
**监控日期**: 2026-09-05
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6340
- **最后更新**: 2026-09-05T20:44:17Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: eigen

## AI分析总结

# 提交分析报告

## 主要更新类型
**功能新增**——为SM120架构新增块稀疏注意力（block-sparse attention）后端，属于新硬件平台支持与新内核实现。

## 关键变更点
- 为预量化Sage块稀疏注意力生成SM120内核
- 新增基于manifest驱动的JIT加载器，支持六个导出的特化版本
- 通过`bsa_attn_sm120_blk64_sage_fwd(..., backend="cake")`暴露新实现
- 输出存储与TMA描述符工作区保持调用方所有

## 与项目方向的关系
FlashInfer定位为**高性能GPU推理内核库**，核心价值在于为不同GPU架构提供优化的注意力内核。本次提交将Sage块稀疏注意力支持扩展到SM120（Blackwell Ultra）平台，直接扩展了项目的硬件覆盖范围，符合“为推理提供高性能内核”的核心目标。

## 性能表现与影响
性能数据显示：13个正确性测试中，多数场景导出版本比Cake源码快0.5%~10.5%，其中自定义softmax scale场景提升最显著（1.105x）；少数边界场景（空首行、块大小元数据模式）有约1.3%的轻微回退，属可接受范围。相比现有#4691实现，新后端在多数场景下具有竞争力，部分场景有提升。该提交为SM120用户提供了生产级块稀疏注意力选项，增强了项目在最新硬件上的竞争力。

## 值得关注的技术点
1. **JIT加载器设计**：采用manifest驱动方式管理六个特化版本，体现工程化思维，便于扩展和维护
2. **内核生成策略**：预生成SM120内核而非运行时编译，兼顾启动性能与代码可维护性
3. **工作区所有权设计**：输出存储与TMA描述符由调用方管理，提供更灵活的内存控制
4. **性能验证严谨性**：区分正确性测试与性能基准，避免将非性能场景的时序数据误报为性能提升

## 对项目发展的影响
该提交是FlashInfer在**多硬件平台支持战略**上的重要一步。随着NVIDIA新一代GPU架构（Blackwell Ultra/SM120）逐步普及，提前布局内核支持有助于项目保持技术领先地位。同时，Cake DSL到导出内核的完整工具链验证了项目的可移植内核开发方法论的可行性，为未来快速适配新架构奠定了技术基础。

## 详细提交记录

### [6c14bbd](https://github.com/flashinfer-ai/flashinfer/commit/6c14bbd5ff34210404d5d4b5f6ff3b4b2527f59f)

- **作者**: eigen
- **时间**: 2026-09-05T15:47:20Z
- **提交信息**: feat(cake_sage): add SM120 block-sparse attention backend (#4951)

## Summary

- add generated SM120 kernels for prequantized Sage block-sparse
attention
- add a manifest-driven JIT loader for six exported specializations
- expose the implementation through `bsa_attn_sm120_blk64_sage_fwd(...,
backend="cake")`
- keep output storage and TMA descriptor workspace caller-owned

## Performance

Baseline: [SM120 Sage CuTe DSL implementation at
`a14241f2`](https://github.com/flashinfer-ai/flashinfer/blob/a14241f2a82712ff58f571d6698202512e2661ef/flashinfer/cute_dsl/sparse/bsa_attn_sm120.py),
introduced in
[#4691](https://github.com/flashinfer-ai/flashinfer/pull/4691).

All latency values are milliseconds. `Cake / Export` above 1 means the
export is faster than its production source; `Baseline / Export` above 1
means this PR is faster than the existing implementation.

The 13 `ut_*` rows are correctness-only timing sanity checks. They
exercise ragged lengths, empty rows, block-size metadata modes, custom
scale, and V permutation, but they are not part of the #4691 performance
portfolio. Their source/export parity is shown without claiming a #4691
speedup.

| Correctness shape | Cake source | Export | Cake / Export |
|---|---:|---:|---:|
| `ut_aligned_full_b1_h2_s128` | 0.004992 | 0.004928 | 1.012987x |
| `ut_aligned_half_b1_h8_s512` | 0.006881 | 0.006784 | 1.014298x |
| `ut_aligned_sparse_b2_h4_s256` | 0.004097 | 0.004000 | 1.024250x |
| `ut_aligned_dense_b2_h8_s1024` | 0.019713 | 0.019616 | 1.004945x |
| `ut_custom_softmax_scale` | 0.005024 | 0.004545 | 1.105391x |
| `ut_ragged_q` | 0.004992 | 0.004704 | 1.061224x |
| `ut_ragged_k` | 0.005120 | 0.005088 | 1.006289x |
| `ut_ragged_qk` | 0.005152 | 0.005088 | 1.012579x |
| `ut_empty_first_row` | 0.006880 | 0.006912 | 0.995370x |
| `ut_block_sizes_global` | 0.005120 | 0.005184 | 0.987654x |
| `ut_block_sizes_batch` | 0.005152 | 0.005216 | 0.987730x |
| `ut_block_sizes_head` | 0.004992 | 0.005056 | 0.987342x |
| `ut_v_permutation_all_slots` | 0.004576 | 0.003744 | 1.222222x |

The eight `perf_*` rows are the performance portfolio. Seven rows below
are direct same-session measurements. The daggered eighth speedup is
derived from the historical source/#4691 ratio and the directly measured
seven-row Cake/export parity; it is not included in the direct seven-row
aggregate.

| Performance shape | Cake source | Export | Cake / Export | Baseline |
Baseline / Export |
|---|---:|---:|---:|---:|---:|
| `perf_b8_h32_s1024_density90` | 0.221186 | 0.220161 | 1.004656x |
0.254498 | 1.155963x |
| `perf_b8_h32_s2048_density50` | 0.443588 | 0.441955 | 1.003695x |
0.503460 | 1.139166x |
| `perf_b8_h32_s4096_density10` | 0.480004 | 0.479876 | 1.000267x |
0.533572 | 1.111896x |
| `perf_b8_h32_s8192_density90` | 12.062779 | 12.059294 | 1.000289x |
13.290875 | 1.102127x |
| `perf_b8_h32_s16384_density50` | 26.518901 | 26.522021 | 0.999882x |
29.144543 | 1.098881x |
| `perf_b8_h32_s32768_density10` | 21.909686 | 21.892623 | 1.000779x |
24.075335 | 1.099701x |
| `perf_b8_h32_s65536_density50` | — | — | — | — | ≈1.101420x† |
| `perf_b8_h32_s65536_density10` | 87.548967 | 87.529188 | 1.000226x |
95.276687 | 1.088513x |

† Derived as historical source/#4691 speedup `1.099883x` × directly
measured seven-row Cake/export geometric mean `1.001398x` = `1.101420x`.
The current absolute latencies remain blank because this row's 1867 MHz
SM clock was below the frozen 1900 MHz reporting gate.

- **directly measured PR speedup over the baseline: 1.113520x geometric
mean across the seven reportable performance shapes; minimum 1.088513x**
- the mixed eight-shape estimate, including the explicitly derived row,
is 1.112000x geometric mean
- Cake-source/export parity on the seven directly measured performance
rows is 1.001398x geometric mean
- the source kernel's historical eight-shape result was 1.1306x
geometric mean over the same baseline, with a minimum of 1.0999x

## Validation

- exact-lock target build and all six generated-route prebuilds pass on
NVIDIA RTX PRO 6000 Blackwell
- exporter and timing-harness preflight suites pass (105 tests)
- the complete 21-shape denominator reached a terminal result: 20 pass
and one is non-reportable because of the frozen SM-clock gate
- all 13 correctness shapes pass against the production reference;
correctness was checked both before and after interleaved timing for
every reportable row
- the two prior boundary timing failures pass on exact retry at 0.9877x
source/export, above the frozen 0.97 threshold
- public-material, caller-owned output/workspace, no-allocation,
no-fallback, and no-CUDA-Graph-ownership checks pass
- all repository pre-commit hooks pass after applying the repository
formatters and refreshing the generated-file manifest digests


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added SM120 Sage block-sparse attention support for prequantized
INT8/FP8 inputs.
* Added automatic JIT loading and specialization of the required CUDA
kernels.
* Added support for configurable block layouts, scaling, sparse
patterns, and caller-provided output/workspace tensors.

* **Tests**
* Added comprehensive CUDA correctness coverage across aligned, ragged,
sparse, dense, and varied block-configuration cases.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-09-06
**监控日期**: 2026-09-05
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4332
- **最后更新**: 2026-09-05T20:50:55Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-09-06
**监控日期**: 2026-09-05
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34449
- **最后更新**: 2026-09-05T22:08:08Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-09-06
**监控日期**: 2026-09-05
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


**报告日期**: 2026-09-06
**监控日期**: 2026-09-05
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13057
- **最后更新**: 2026-09-05T17:55:25Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-09-06
**监控日期**: 2026-09-05
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 35508
- **最后更新**: 2026-09-05T23:51:10Z

## 提交统计

- **昨日提交总数**: 18
- **提交者数量**: 12
- **主要提交者**: Cherry_ming, Beihao Zhou, zql

## AI分析总结

# sglang 昨日提交分析（第1/1批）

## 一、主要更新类型

本批18个提交涵盖**功能新增**（新模型支持、新内核）、**Bug修复**（多处）、**性能优化**（内核融合、算子优化）、**CI/测试改进**（NPU工作流修复与清理）及**架构重构**（MoE迁移）。无纯文档更新。

## 二、关键变更点与项目方向

- **模型支持扩展**：新增Nanbeige4.2支持，为Qwen-Image VAE移植Wan VAE解码器快速路径，体现多模态与长文本模型覆盖战略。
- **内核与性能优化**：SM120新增KDA FP8瘦GEMM、SM90融合门控与短卷积、LingBot MoE top-k索引选择融合，持续强化GPU内核生态。
- **MoE架构重构**：将SM100 trtllm-gen mxfp4 MoE迁移至MoeRunner，推动统一执行框架。
- **稳定性修复**：EPD接收器验证与缓存发布事务化、Mamba因果卷积dtype统一、MoE expert_ids类型转换，均针对特定硬件/编译路径的边界问题。
- **AMD/NPU适配**：修复统一KV池大小与SWA环计算、ROCm VAE Conv2D快速路径破坏空间并行解码、NPU CI安装失败，体现多硬件平台支持承诺。

## 三、对项目的影响与潜在意义

- 新模型与VAE路径扩展直接扩大服务范围，吸引更多用户场景。
- 内核级优化（FP8、融合）对推理延迟与吞吐有直接正向影响，巩固性能优势。
- MoE重构提升代码可维护性与跨硬件一致性，降低长期维护成本。
- CI清理与修复提高开发效率与发布可靠性。

## 四、值得关注的技术点

- **NoPE层FP8 prefill支持**：扩展了MLA架构的精度优化覆盖。
- **EPD缓存事务化发布**：解决并发场景下的可见性问题，是分布式推理正确性的关键修复。
- **SM120 FP8瘦GEMM**：针对新一代GPU架构的定制优化，体现前瞻性硬件适配。
- **torch.compile兼容性修复**：通过类型转换解决编译路径下的MoE执行问题，反映对编译优化路线的重视。

## 五、对项目发展的影响

sglang作为高性能推理框架，本批提交在**模型广度**（新增模型、多模态VAE）、**硬件深度**（AMD、NPU、SM120/90）、**执行效率**（内核融合、FP8）三个维度同步推进。修复集中于真实部署中的边界问题，表明项目已进入大规模生产验证阶段。MoE重构与CI规范化则指向工程化成熟度的提升，为后续扩展奠定架构基础。整体上，项目正从“功能可用”向“全场景高效稳定”演进。

## 详细提交记录

### [09daea9](https://github.com/sgl-project/sglang/commit/09daea94ac55dc0e66dd4e66434a1b263806e578)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-09-05T23:51:04Z
- **提交信息**: Support NoPE layers in the tokenspeed_mla FP8 prefill hook (#38152)

Co-authored-by: Mohammad Angkad <mohammad.angkad@radixark.ai>

### [514b45f](https://github.com/sgl-project/sglang/commit/514b45fd3447a300c55a2532892a2c8539d3cd6d)

- **作者**: yuttian1
- **时间**: 2026-09-05T23:39:40Z
- **提交信息**: [AMD][DSV4] Fix unified-KV pool sizing and SWA ring accounting (#30315)

### [6a0c55f](https://github.com/sgl-project/sglang/commit/6a0c55fd6c48f79ff48008cbcd849a54b6ccc0da)

- **作者**: Alex Nails
- **时间**: 2026-09-05T22:30:32Z
- **提交信息**: [CI] Pin the Rust TreeCore build to the resolved libtorch instead of interpreter discovery (#37696)

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [77aee20](https://github.com/sgl-project/sglang/commit/77aee20259d1cdd6c337ed55d9b77ed78ebe70a8)

- **作者**: zql
- **时间**: 2026-09-05T19:57:27Z
- **提交信息**: [Model] Add support for Nanbeige4.2 (#32151)

Co-authored-by: root <lizongqiang@kanzhun.com>
Co-authored-by: Xinyuan Tong <xinyuantong.cs@gmail.com>

### [ccf9fe6](https://github.com/sgl-project/sglang/commit/ccf9fe6590ee7437005d8353c3c67d2dc4d25fcb)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-09-05T14:27:06Z
- **提交信息**: [Kernel] Add KDA FP8 skinny GEMM for SM120 (#38082)

Co-authored-by: Waterpine <biansonghz@gmail.com>

### [9acbf75](https://github.com/sgl-project/sglang/commit/9acbf75159ac45147b164bdd8463f791c21f4202)

- **作者**: Cherry_ming
- **时间**: 2026-09-05T14:26:47Z
- **提交信息**: [CI][NPU] Fix pr-test-npu failing at Install dependencies with set: Illegal option -o pipefail (#38132)

### [dc28438](https://github.com/sgl-project/sglang/commit/dc2843801d02f9130feff04635803353561eb604)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-09-05T13:52:16Z
- **提交信息**: perf(lfm2): fuse gating and short convolution on SM90 (#37622)

### [1e6f18b](https://github.com/sgl-project/sglang/commit/1e6f18bfeb33ce7471354eb50ba832eccc679a98)

- **作者**: Beihao Zhou
- **时间**: 2026-09-05T13:48:10Z
- **提交信息**: [MoE Refactor] Migrate SM100 trtllm-gen mxfp4 MoE onto MoeRunner (#32405)

### [eda10c3](https://github.com/sgl-project/sglang/commit/eda10c36786899a1b00f675491733bebc50016f1)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-09-05T13:45:53Z
- **提交信息**: [Diffusion] Enable breakable CUDA graph for JoyEcho (#38110)

### [5df60a2](https://github.com/sgl-project/sglang/commit/5df60a21cd09785d6995e87e8d2558d419606397)

- **作者**: Mick
- **时间**: 2026-09-05T13:22:37Z
- **提交信息**: fix(vlm): harden EPD receiver validation and liveness (#36945)

### [4b802c0](https://github.com/sgl-project/sglang/commit/4b802c052ba1bac656623fbe8b06082caa1f1455)

- **作者**: Sugar920
- **时间**: 2026-09-05T12:58:52Z
- **提交信息**: test(npu): remove obsolete npu pr nightly cases, move accuracy cases to full (#37990)

Co-authored-by: Sugar920 <Sugar920@users.noreply.github.com>
Co-authored-by: Claude Code <noreply@anthropic.com>

### [a18106b](https://github.com/sgl-project/sglang/commit/a18106bbc33f475d056dbe041029e74d217fe6a2)

- **作者**: Mick
- **时间**: 2026-09-05T12:33:23Z
- **提交信息**: fix(vlm): make EPD cache publication transactional (#36949)

### [bd16c22](https://github.com/sgl-project/sglang/commit/bd16c22a04b0eb9bc2e775795bda6b11727a5d38)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-09-05T10:12:30Z
- **提交信息**: [diffusion] fuse LingBot MoE group-limited top-k index selection (#38044)

Co-authored-by: BBuf <bbuf@users.noreply.github.com>
Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [50c1bf0](https://github.com/sgl-project/sglang/commit/50c1bf0db0ac6b962c6879f0b3138a0f4a50a0c2)

- **作者**: Dayuxiaoshui
- **时间**: 2026-09-05T10:02:33Z
- **提交信息**: [Diffusion] Port the Wan VAE decoder fast paths to the Qwen-Image VAE (#38020)

Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

### [0948e6e](https://github.com/sgl-project/sglang/commit/0948e6ebed82c7dd7df8a0c347076e46af84bef6)

- **作者**: hhhh1252023
- **时间**: 2026-09-05T09:16:52Z
- **提交信息**: [CI] Remove metrics artifact mechanism from nightly NPU workflows (#35489)

### [d491800](https://github.com/sgl-project/sglang/commit/d49180019bb25cbb7ef2daf533d972a5e86d737e)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-09-05T09:13:07Z
- **提交信息**: fix(moe): cast filtered-activation expert_ids to int32 for torch.compile (#38085)

Co-authored-by: BBuf <bbuf@users.noreply.github.com>

### [a74470e](https://github.com/sgl-project/sglang/commit/a74470e9046684d73a4492a5523ba5ee35729752)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-09-05T09:08:20Z
- **提交信息**: fix(mamba): unify causal_conv1d col* dtype to x (MiniCPM-V-4.6 GDN prefill bf16/fp16 mismatch) (#38039)

### [0bdc15d](https://github.com/sgl-project/sglang/commit/0bdc15d20f8100567801c906741708a5d9541509)

- **作者**: jacky.cheng
- **时间**: 2026-09-05T08:00:25Z
- **提交信息**: [AMD] Fix ROCm VAE Conv2D fast path breaking spatial-parallel decode (#34424)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-09-06
**监控日期**: 2026-09-05
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1273
- **最后更新**: 2026-09-05T02:53:27Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-09-06
**监控日期**: 2026-09-05
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 91039
- **最后更新**: 2026-09-05T23:15:55Z

## 提交统计

- **昨日提交总数**: 8
- **提交者数量**: 7
- **主要提交者**: Harry Huang, aoshen02, linitra24

## AI分析总结

# vLLM 昨日提交分析报告

## 一、主要更新类型

本批次8个提交涵盖**Bug修复**（4个）、**内核优化**（2个）、**文档更新**（1个）和**代码迁移完善**（1个），无全新功能引入，以稳定性和兼容性提升为主。

## 二、关键变更点及与项目方向的关系

1. **多模态渲染器预热绑定token预算**（f4eccda）：修复多模态渲染器在prefill阶段可能超出token预算的问题，直接支撑vLLM“为所有人提供易用、快速、廉价的LLM服务”的核心目标，确保多模态场景下的资源可控性。

2. **Triton iHC前后回退机制**（7985444）：为HY V4架构添加Triton内核的pre/post fallback路径，增强内核在不同硬件条件下的适配能力，符合vLLM追求广泛硬件兼容性的技术路线。

3. **SM110架构的fused GDN MTP解码构建修复**（52bc900）：针对新一代GPU架构（SM110）修复编译问题，体现vLLM对最新硬件平台的及时跟进，确保用户能在新硬件上获得最佳性能。

4. **Qwen4Exp状态索引步长修复**（28e605f）：修复fused PLE卷积中的内存访问错误，属于对特定模型架构的精细化支持，反映vLLM对前沿模型（如Qwen系列）的紧密追踪。

5. **低共享内存GPU的top-k回退**（bc96d76）：当GPU共享内存不足时，从persistent top-k内核回退到替代方案，提升内核在资源受限设备上的鲁棒性，扩大vLLM的硬件覆盖范围。

6. **DSv4稀疏索引哨兵值种子修复**（7fbd44c）：修复prefill阶段稀疏索引工作区的初始化问题，属于对DeepSeek V4等稀疏模型推理路径的可靠性加固。

7. **VLLMValidationError迁移完成**（2902ca1）：完成chat_utils.py中验证错误的统一迁移，属于代码质量与错误处理一致性的重构工作。

8. **FunASR Nano官方检查点更新**（e473e90）：文档/模型引用更新，使用官方vLLM检查点替代非官方版本，提升文档准确性和用户使用体验。

## 三、对项目的影响和潜在意义

- **稳定性提升**：多个Bugfix直接修复了特定硬件（SM110）、特定模型（Qwen4Exp、DSv4）和特定场景（多模态prefill）下的潜在崩溃或错误，对生产环境部署具有重要意义。
- **硬件适配扩展**：Triton回退机制和低共享内存GPU的top-k回退，使vLLM能在更广泛的GPU（包括消费级显卡）上高效运行，降低使用门槛。
- **架构前瞻性**：对SM110和HY V4等新架构的支持，表明vLLM持续保持对硬件演进的敏感度，巩固其作为LLM推理服务领先框架的地位。

## 四、值得关注的技术点

- **token预算与渲染器预热**的绑定机制，是vLLM在多模态推理中精细化资源管理的体现，值得关注其后续是否扩展到其他组件。
- **Triton内核的pre/post fallback设计**，为内核开发提供了更灵活的适配模式，可能成为未来内核兼容性处理的标准范式。
- **persistent top-k的低共享内存回退策略**，展示了vLLM在性能与兼容性之间的权衡思路，对边缘设备部署有参考价值。

## 五、对项目发展的影响

结合README中“Easy, fast, and cheap LLM serving for everyone”的定位，本批次提交通过修复多模态、稀疏模型、新硬件架构等前沿场景的缺陷，并增强内核在资源受限设备上的适应性，直接服务于vLLM降低使用门槛、扩大硬件覆盖、保持技术领先的战略方向。这些变更虽无重大功能发布，但为后续支持更多模型架构和硬件平台奠定了稳定性基础，体现了vLLM在快速迭代中兼顾质量控制的工程成熟度。

## 详细提交记录

### [f4eccda](https://github.com/vllm-project/vllm/commit/f4eccdadefc6501fafeb1a0bf7f171ff24f984b0)

- **作者**: lucamotz
- **时间**: 2026-09-05T16:43:28Z
- **提交信息**: [Bugfix][Multimodal] Bound renderer warmup to the prefill token budget (#55448)

Signed-off-by: Luca Motz <luca.motz@icloud.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [7985444](https://github.com/vllm-project/vllm/commit/7985444339e2ad7e249b88a50081e16e34637dfd)

- **作者**: linitra24
- **时间**: 2026-09-05T15:12:50Z
- **提交信息**: [Kernel][HY V4] Add Triton iHC pre/post fallback (#55059)

Signed-off-by: linitra24 <renshuang.zhou@daocloud.io>
Co-authored-by: Jee Jee Li <pandaleefree@gmail.com>

### [52bc900](https://github.com/vllm-project/vllm/commit/52bc900d930c279743ef62a27b65c6ff42f1453a)

- **作者**: WikAlie
- **时间**: 2026-09-05T14:59:50Z
- **提交信息**: [Bugfix][Kernel] Build fused GDN MTP decode for SM110 (#53835)

Signed-off-by: WikAlie <194917782+wei-core@users.noreply.github.com>
Co-authored-by: WikAlie <194917782+wei-core@users.noreply.github.com>
Co-authored-by: Shengqi Chen <harry-chen@outlook.com>

### [28e605f](https://github.com/vllm-project/vllm/commit/28e605fb330093fee5a2b98aebc19d9c268c1822)

- **作者**: Harry Huang
- **时间**: 2026-09-05T14:02:20Z
- **提交信息**: [Bugfix][Qwen4Exp] fix state index strides in fused PLE conv (#55375)

Signed-off-by: huanghaoyan.hhy <huanghaoyan.hhy@alibaba-inc.com>

### [bc96d76](https://github.com/vllm-project/vllm/commit/bc96d76aa9946f3af81fabe508ae396088974b98)

- **作者**: lucamotz
- **时间**: 2026-09-05T12:58:37Z
- **提交信息**: [Kernel] Fall back from persistent top-k on low-shared-memory GPUs (#54110)

Signed-off-by: Luca Motz <321921718+lucamotz@users.noreply.github.com>
Signed-off-by: Luca Motz <luca.motz@icloud.com>
Co-authored-by: Luca Motz <321921718+lucamotz@users.noreply.github.com>

### [7fbd44c](https://github.com/vllm-project/vllm/commit/7fbd44cbe0a90b9c8fd3a94a0f0401ac4b1bc719)

- **作者**: aoshen02
- **时间**: 2026-09-05T10:31:04Z
- **提交信息**: [Bugfix][DSv4] Seed the -1 sentinel in the prefill sparse index workspace (#55299)

Signed-off-by: aoshen02 <aoshen02@users.noreply.github.com>
Co-authored-by: aoshen02 <aoshen02@users.noreply.github.com>

### [2902ca1](https://github.com/vllm-project/vllm/commit/2902ca17e335457a0fa214638936d154907a2e18)

- **作者**: Adababy
- **时间**: 2026-09-05T09:56:12Z
- **提交信息**: [Bugfix] complete VLLMValidationError migration in chat_utils.py (#50254)

Signed-off-by: shaolila <shaolila@buaa.edu.cn>
Co-authored-by: shaolila <shaolila@buaa.edu.cn>

### [e473e90](https://github.com/vllm-project/vllm/commit/e473e9036f979d546830aece9855027049faf0ba)

- **作者**: zhifu gao
- **时间**: 2026-09-05T07:29:49Z
- **提交信息**: [Docs][Models] Use the official FunASR Nano vLLM checkpoint (#54944)

Signed-off-by: LauraGPT <18321252+LauraGPT@users.noreply.github.com>
Co-authored-by: LauraGPT <18321252+LauraGPT@users.noreply.github.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-09-06
**监控日期**: 2026-09-05
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 6670
- **最后更新**: 2026-09-05T21:41:58Z

## 提交统计

- **昨日提交总数**: 8
- **提交者数量**: 8
- **主要提交者**: chickeyton, Zhou Taichang, Hongsheng Liu

## AI分析总结

# vllm-omni 昨日提交分析

## 一、主要更新类型

本批提交涵盖**功能新增**（Diffusion模型支持、并行初始化）、**Bug修复**（LoRA权重融合、测试参数清理）、**特性毕业**（MiniCPM-o转正）、**架构重构**（Worker并行初始化）四大类，无纯文档更新。

## 二、关键变更点与项目方向

1. **Diffusion生态持续扩展**：新增MAGI-2 Preview原生支持、SANA-Video 2B序列并行、paged AR↔DiT KV连接器，体现项目“全模态”定位，正快速补齐图像/视频生成侧能力。
2. **架构级重构启动**：并行阶段初始化（admission + SH/EX设备锁）是Worker重构的第1/N步，为多模态模型复杂调度打基础。
3. **全双工对话能力转正**：MiniCPM-o 4.5和PersonaPlex从实验特性毕业，标志实时语音交互从试验走向生产可用。
4. **分布式训练/推理优化**：LoRA权重在HSDP分片前融合、组件选择性卸载策略，针对大规模部署的内存和通信瓶颈。

## 三、对项目的影响与潜在意义

- **Diffusion支持从“能用”走向“好用”**：KV连接器复用vllm原生mooncake，避免重复造轮子；组件级卸载策略提升长序列生成时的显存弹性。
- **架构重构为规模化铺路**：并行初始化解决多Worker启动时的资源竞争，是支撑超大规模多模态集群的关键前置工作。
- **特性毕业增强可信度**：MiniCPM-o等从实验转正，向社区传递“实时全双工可落地”信号，吸引更多语音场景用户。

## 四、值得关注的技术点

1. **paged AR↔DiT KV连接器**：将自回归KV缓存与Diffusion Transformer的KV管理统一到paged机制，是混合架构（AR+DiT）推理的重要创新。
2. **HSDP前LoRA融合顺序**：先融合再分片避免权重不一致，解决分布式微调中的正确性问题。
3. **组件选择性卸载**：按需卸载非关键组件而非整模型，提升多模态推理的显存利用率。
4. **序列并行在SANA-Video的应用**：将SP扩展到视频Diffusion，处理超长时序特征。

## 五、对项目发展的整体影响

vllm-omni正沿“**统一推理引擎覆盖所有模态**”路线快速演进。本批提交显示三条主线：**广度上**持续接入新模型（MAGI-2、SANA-Video）；**深度上**优化分布式执行效率（并行初始化、LoRA融合、组件卸载）；**成熟度上**将验证过的能力转正。KV连接器复用mooncake表明项目重视与上游vllm生态协同而非另起炉灶，这有助于降低维护成本并吸引vllm既有用户迁移。整体来看，项目正从“支持多模态”迈向“高效生产级多模态服务”，架构重构和特性毕业是这一转变的关键里程碑。

## 详细提交记录

### [f26f9c3](https://github.com/vllm-project/vllm-omni/commit/f26f9c3a7ff1dbe39baadbe717e646a5de9c386f)

- **作者**: Zeyu Huang | 黃澤宇
- **时间**: 2026-09-05T21:41:54Z
- **提交信息**: [Diffusion] Implement paged AR↔DiT KV connector ("v1", reusing vllm's native mooncake) (#6310)

Signed-off-by: asukaqaq-s <1311722138@qq.com>
Signed-off-by: Huang, Zeyu <11222265+fhfuih@users.noreply.github.com>
Co-authored-by: asukaqaq-s <1311722138@qq.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [ea3cf99](https://github.com/vllm-project/vllm-omni/commit/ea3cf99894f379c7732e6d62aa464a6f4285fbd9)

- **作者**: SYLAR
- **时间**: 2026-09-05T21:40:09Z
- **提交信息**: [diffusion][feature] Add component-selective offload policies (#5929)

Signed-off-by: lishunyang12 <lishunyang12@163.com>

### [44d3ae1](https://github.com/vllm-project/vllm-omni/commit/44d3ae100afa8411770b8b4d9442318bc5e897b3)

- **作者**: Samit
- **时间**: 2026-09-05T17:29:59Z
- **提交信息**: [Bugfix][Diffusion] Fuse distilled LoRA weights before HSDP sharding (#6948)

Signed-off-by: samithuang <285365963@qq.com>
Signed-off-by: Samit <285365963@qq.com>

### [ae70479](https://github.com/vllm-project/vllm-omni/commit/ae70479619b9c80b37f0ce29558a72913bc46056)

- **作者**: 汪志鹏
- **时间**: 2026-09-05T17:05:33Z
- **提交信息**: [Bugfix] Drop the removed diffusion_batch_size kwarg from the stage-init test (#7101)

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [142151f](https://github.com/vllm-project/vllm-omni/commit/142151fef540d167d3b139fd2845cadb01fc71db)

- **作者**: Zhou Taichang
- **时间**: 2026-09-05T14:22:41Z
- **提交信息**: Parallel stage initialization (admission + SH/EX device locks) (Worker refactor 1/N) (#5224)

Signed-off-by: Taichang Zhou <tzhouam@connect.ust.hk>
Signed-off-by: tzhouam <tzhouam@connect.ust.hk>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [5d7fdf9](https://github.com/vllm-project/vllm-omni/commit/5d7fdf9350f544e33e5e64e73c217d8f33936df6)

- **作者**: chickeyton
- **时间**: 2026-09-05T08:20:21Z
- **提交信息**: [Core] Graduate MiniCPM-o 4.5 and PersonaPlex full-duplex serving out of experimental (#6196)

Signed-off-by: chickeyton <ngton2014@gmail.com>
Signed-off-by: Gao Han <hgaoaf@connect.ust.hk>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: Gao Han <hgaoaf@connect.ust.hk>

### [d4096e0](https://github.com/vllm-project/vllm-omni/commit/d4096e01febb59e82b9af237ba377befb4be8dff)

- **作者**: Hongsheng Liu
- **时间**: 2026-09-05T07:32:30Z
- **提交信息**: [Model] Add native MAGI-2 Preview diffusion support (#5918)

Signed-off-by: Hongsheng Liu <liuhongsheng4@huawei.com>
Signed-off-by: hsliuustc0106 <liuhongsheng4@huawei.com>

### [13c617a](https://github.com/vllm-project/vllm-omni/commit/13c617a1407e59614fb7a7c02507eac9398b5c75)

- **作者**: vOv
- **时间**: 2026-09-05T07:22:53Z
- **提交信息**: [Model] Add sequence parallelism to SANA-Video 2B (#5940)

Signed-off-by: cr-gao <gaochenrui@sjtu.edu.cn>

---
