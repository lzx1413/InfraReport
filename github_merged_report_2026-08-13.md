# GitHub Stars 合并报告 - 2026-08-13

**合并日期**: 2026-08-14
**监控日期**: 2026-08-13
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


**报告日期**: 2026-08-14
**监控日期**: 2026-08-13
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2147
- **最后更新**: 2026-08-13T19:14:14Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Albert Zhang

## AI分析总结

# 提交分析报告

## 1. 主要更新类型

本次提交为**文档更新**，具体为新增Ascend（昇腾）Docker镜像的概述文档及支持的标签（tags）列表。

## 2. 关键变更点及与项目方向的关系

该提交为VeOmni项目添加了Ascend硬件平台的Docker镜像使用文档，包括镜像概述和可用标签说明。VeOmni的核心理念是“模型中心的分布式训练配方库”（Model-Centric Distributed Recipe Zoo），旨在支持多种模态模型的训练。新增Ascend支持文档与项目“多硬件平台适配”的方向高度一致——通过提供昇腾NPU的容器化部署指南，扩展了项目在国产AI芯片生态中的可用性。

## 3. 对项目的影响和潜在意义

- **降低使用门槛**：为Ascend用户提供清晰的镜像获取和使用指引，减少部署试错成本
- **生态扩展**：表明项目已适配昇腾硬件，吸引使用国产算力的研究者和企业用户
- **社区信号**：文档先行通常意味着后续会有更多Ascend相关的功能支持或优化提交

## 4. 值得关注的技术点

- Docker镜像的“支持标签”设计反映了项目对版本管理和可复现性的重视
- Ascend适配涉及CANN（昇腾计算架构）与分布式训练框架的集成，文档的完善暗示底层代码已完成相应适配工作

## 5. 对项目发展的影响

VeOmni定位于“任意模态模型训练”的分布式方案，硬件兼容性是影响其采用率的关键因素。此次Ascend支持文档的加入，使项目从依赖单一GPU生态（如NVIDIA）向多硬件平台迈进，有助于覆盖更广泛的算力场景，特别是中国本土AI基础设施环境。这一举措与项目论文中强调的“可扩展性”目标相呼应，为后续在国产芯片上的性能优化和配方扩展奠定了基础。整体来看，这是一次小而重要的生态建设步骤，预示着项目正朝着“硬件无关”的通用训练框架方向演进。

## 详细提交记录

### [81d1c9b](https://github.com/ByteDance-Seed/VeOmni/commit/81d1c9b28b922fda7435820d364d44b10aca9c30)

- **作者**: Albert Zhang
- **时间**: 2026-08-13T13:32:57Z
- **提交信息**: [docs] feat: add Ascend Docker image overview and supported tags (#1046)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-08-14
**监控日期**: 2026-08-13
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2665
- **最后更新**: 2026-08-13T21:16:19Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 1
- **主要提交者**: Bilang ZHANG

## AI分析总结

### 1. 主要更新类型
- **Bug修复**：两次提交均针对`minimax h3`模型的**warmup（预热）**问题，属于运行时稳定性修复。
- **性能优化**：涉及`video encoder`的warmup逻辑，可能影响推理延迟和显存占用。
- **工程化改进**：包含编译流程修复（`compile`）和技能（`skills`）更新，属于开发工具链优化。

### 2. 关键变更点与项目方向的关系
- **warmup修复**：LightX2V定位为**轻量视频生成推理框架**，warmup是模型加载后首次推理前的必要步骤，直接影响服务启动速度和首token延迟。修复h3模型的warmup，直接服务于“轻量”和“高效”的核心目标。
- **video encoder预热**：视频编码器是视频生成链路的前端组件，其预热不充分可能导致后续生成阶段出现显存峰值或计算错误，修复后能提升端到端推理的稳定性。
- **编译与技能更新**：编译修复可能针对特定硬件（如GPU）的算子融合或JIT编译，技能更新可能涉及模型配置或推理策略的调优，均属于对推理管线的持续打磨。

### 3. 对项目的影响和潜在意义
- **稳定性提升**：修复warmup可减少生产环境中的偶发崩溃或性能抖动，增强框架在真实部署中的可靠性。
- **用户体验改善**：更快的启动和更稳定的推理，降低用户接入门槛，尤其对需要快速迭代的开发者友好。
- **生态完善**：技能更新可能意味着对更多模型或场景的支持，扩大框架适用范围，吸引更多社区贡献。

### 4. 值得关注的技术点
- **warmup机制设计**：如何针对不同模型（如h3）定制预热策略，避免通用预热带来的资源浪费或覆盖不全。
- **编译流程优化**：修复编译问题可能涉及算子库版本兼容性或动态shape处理，这关系到框架对多样硬件和模型结构的适配能力。
- **技能（skills）更新**：若技能指推理调度策略，则可能涉及KV Cache管理、并行度调整等，直接影响吞吐量和显存效率。

### 5. 对项目发展的影响
- **夯实基础**：这些修复虽小，但解决了实际使用中的痛点，为后续功能迭代（如新模型支持、分布式扩展）扫清障碍。
- **强化“轻量”定位**：通过优化warmup和编译，进一步降低资源开销，巩固LightX2V在轻量级视频推理领域的竞争力。
- **社区信任**：及时修复问题并更新技能，体现项目维护的活跃度和专业性，有助于吸引更多用户和贡献者，推动项目向更成熟的框架演进。

**总结**：本次提交聚焦于`minimax h3`模型的warmup和编译修复，属于典型的稳定性与性能优化，虽不涉及新功能，但直接提升了框架的实用性和可靠性，与LightX2V“轻量高效”的定位高度契合，为长期发展奠定了更坚实的基础。

## 详细提交记录

### [377973e](https://github.com/ModelTC/LightX2V/commit/377973e267aa36183cec38bdf3b551220d5d66a5)

- **作者**: Bilang ZHANG
- **时间**: 2026-08-13T11:26:39Z
- **提交信息**: fix：warmup of minimax h3 and video encoder (#1377)

### [54b1479](https://github.com/ModelTC/LightX2V/commit/54b1479ea18619a6a1b9e4e2ddbe976d81c82d0e)

- **作者**: Bilang ZHANG
- **时间**: 2026-08-13T07:29:39Z
- **提交信息**: fix: minimax h3 warmup and compile; update skills (#1375)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-08-14
**监控日期**: 2026-08-13
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2197
- **最后更新**: 2026-08-13T10:13:52Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: hkz

## AI分析总结

## 提交分析总结

### 1. 主要更新类型
**功能新增**。本次提交为Wan2.1和Wan2.2模型添加了DFD（可能指Diffusion Feature Distillation或类似技术）支持，属于模型能力扩展。

### 2. 关键变更点及项目方向关系
- 为Wan系列模型（Wan2.1、Wan2.2）新增DFD功能，与项目README中展示的Wan-Fun模型支持方向一致
- 项目本身定位为多模型视频生成工具（同时支持CogVideoX和Wan系列），此次更新进一步强化了Wan系列模型的功能完整性
- 提交编号#505表明项目处于活跃迭代阶段，持续扩展模型生态

### 3. 对项目的影响和潜在意义
- 提升Wan系列模型的生成质量或效率（取决于DFD具体含义）
- 增强项目在多模型支持上的竞争力，使用户在Wan模型上获得更优体验
- 可能吸引更多Wan模型用户，扩大项目社区影响力

### 4. 值得关注的技术点
- DFD技术本身：若为特征蒸馏，则涉及模型压缩或知识迁移；若为扩散特征引导，则涉及生成质量优化
- 跨版本兼容性：同时支持Wan2.1和Wan2.2，说明代码架构具备良好的版本适配能力
- 该功能可能涉及推理流程优化或训练策略调整，值得关注后续文档或示例更新

### 5. 对项目发展的影响
基于README背景，VideoX-Fun致力于提供多模型视频生成解决方案。此次提交：
- 巩固了Wan系列模型的支持深度，与CogVideoX形成双轮驱动
- 表明项目正从“可用”向“好用”演进，通过引入先进技术提升生成效果
- 为后续可能的新模型接入或功能扩展奠定技术基础，保持项目在视频生成工具中的领先地位

总体而言，这是一次聚焦模型能力增强的常规迭代，体现了项目持续优化多模型生态的长期战略。

## 详细提交记录

### [6787dc8](https://github.com/aigc-apps/VideoX-Fun/commit/6787dc8ed4902b2a49f16e2541bd97936cc1e157)

- **作者**: hkz
- **时间**: 2026-08-13T08:56:53Z
- **提交信息**: Add DFD for Wan2.1 and Wan2.2 (#505)

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-08-14
**监控日期**: 2026-08-13
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 6158
- **最后更新**: 2026-08-13T22:51:54Z

## 提交统计

- **昨日提交总数**: 12
- **提交者数量**: 11
- **主要提交者**: Jimmy Zhou, Ace Eldeib, akhilg-nv

## AI分析总结

# FlashInfer 提交分析总结

## 主要更新类型

本批提交涵盖**性能优化**、**功能新增**、**Bug修复**、**测试调整**和**文档维护**，整体以性能优化和功能扩展为核心，聚焦Blackwell架构深度优化与生产级MoE推理能力提升。

## 关键变更点与项目方向

**性能优化方面**，两个GDN相关提交通过将编译期静态参数改为运行时动态值，显著减少内核特化数量：MTP解码内核将缓存模式标志改为CTA统一运行时布尔值，使编译调用从20次降至10次，冷编译时间从111秒降至58秒；pretranspose内核将池容量和前导步长动态化，冷编译时间减少约62%，且均无稳态性能回退。这通过减少JIT编译开销直接提升实际使用体验。

**功能新增方面**，多个提交扩展了不同后端的支持范围：cuDNN paged prefill新增直接混合序列长度路径，避免KV侧累积前缀和计算及int32溢出风险；fmha_v2支持非交错paged KV输入，适配分离K/V缓存场景；SM12x MXFP8稠密GEMM新增b12x后端，在目标形状上较CUTLASS后端有1.43-3.25倍加速。cuTile量化内核新增FP8/INT8逐token-group量化及融合RoPE+FP8量化内核，直指DeepSeek MLA路径的paged-KV追加场景，将两次kernel launch合并为一次。MXFP8×MXFP4融合MoE为SM100新增混合精度路径，同时通过连续per-CTA路由窗口将大batch下的TLB页足迹从228页降至约30页，显著缓解地址转换瓶颈。

**Bug修复方面**，TRTLLM ragged prefill修复了空KV行的未定义行为，通过包装器定义空注意力恒等（out=0, lse=-inf），并仅对活跃行启动内核，解决了vLLM中的实际问题。b12x GEMM修复了多波次短K启动时输出损坏的共享内核epilogue竞态问题。

**自动调优方面**，分布感知自动调优针对TRT-LLM MoE，将路由分布纳入tactic选择，突破传统仅按shape调优的局限，提升真实负载下的性能。

## 值得关注的技术点

1. **运行时布尔替代编译期特化**：利用`cutlass.Boolean`实现CTA统一运行时分支，在保持性能的同时消除冗余编译。
2. **混合序列长度形式**：cuDNN paged路径利用token-unit Q indptr和per-batch KV长度，避免元素级偏移转换。
3. **key-major调度**：fp8解码路径采用key-major融合调度，每个KV头只读一次共享index-k，配合TMA双级流水线降低固定开销。
4. **TMA UNPACK_U8加载窄操作数**：规避了`vector<2xE8M0>`不支持的转换/存储lowering。
5. **Dirichlet分布生成exemplar**：合并相同tactic的exemplar，兼顾调优精度与存储/查找开销。
6. **GEMM2 can_implement放宽N整除约束**：通过finalize epilogue的`valid_columns`钳制覆盖部分N-tile场景。

## 项目影响与潜在意义

这些提交体现了FlashInfer作为高性能推理内核库的持续演进：一方面通过减少冗余内核编译提升开发体验和冷启动性能，另一方面通过扩展后端支持（cuDNN、b12x、SM100）和输入格式兼容性（非交错KV、FP8）增强了对多样化生产环境的适配能力。量化内核为FP8推理链路提供更细粒度的后端选择，分布感知调优使MoE在专家倾斜分布下仍能保持最优性能，路由局部性优化则直接解决Blackwell架构在超长序列下的可扩展性问题，是支撑128K+ token上下文的关键技术储备。三者共同强化了项目在DeepSeek等前沿模型场景中的竞争力，有助于吸引更多框架（如vLLM、SGLang）集成采用。

## 详细提交记录

### [ed6c709](https://github.com/flashinfer-ai/flashinfer/commit/ed6c709849fe1c02d4545b4e743a436405f6ca5b)

- **作者**: A*
- **时间**: 2026-08-13T22:51:48Z
- **提交信息**: perf(gdn): reuse MTP decode kernels across cache modes (#4128)

## 📌 Description

This partially addresses #4110 by removing one redundant specialization
axis from the FP32-state MTP verify kernels.

`cache_intermediate_states=True` and `False` previously produced
separate CuTe-DSL binaries even though the flag does not change launch
geometry or shared-memory size. The flag is now a CTA-uniform runtime
`cutlass.Boolean`, so both modes share one compiled kernel. The disabled
path uses a cached `[1, V, K]` placeholder because TVM-FFI still
validates static inner dimensions even when the runtime branch does not
access the tensor.

Cold-compilation telemetry for the existing 30-case
`test_verify_kernel_mtp` matrix on GB10 / SM121, PyTorch 2.13.0+cu130,
and nvidia-cutlass-dsl 4.6.0.dev0:

| | `cute.compile` calls | compile time | total test time |
|---|---:|---:|---:|
| current `main` | 20 | 111.3 s | 112.7 s |
| this PR | 10 | 58.2 s | 59.5 s |

Steady-state GPU latency did not regress in the same environment for
`B=8, T=4, H=16, HV=32, K=V=128`:

| mode | current `main` median | this PR median |
|---|---:|---:|
| intermediate cache on | 397.9 µs | 396.5 µs |
| intermediate cache off | 42.208 µs | 42.208 µs |

The remaining T/tile/kernel-selection specializations are intentionally
unchanged in this PR.

## 🔍 Related Issues

Partially addresses #4110.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

> If you are unsure about how to set up pre-commit, see the [pre-commit
documentation](https://pre-commit.com/).

The complete hook set passed for both changed files via:

```text
pre-commit run --files flashinfer/gdn_kernels/gdn_decode_mtp.py tests/gdn/test_decode_delta_rule.py
```

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All relevant tests are passing.

Validation on GB10 / SM121:

- `72 passed` across MTP cache modes, state writeback representatives,
contiguous and non-contiguous pools, pool indexing, and packed QKV.
- New regression test executes cache-on then cache-off and asserts
exactly one `cute.compile` call.
- Reverse-order cache-off then cache-on validation also passed.
- Ruff, mypy, standard pre-commit hooks for changed files, and `git diff
--check` passed.

## Reviewer Notes

The new branch is uniform across the CTA and only guards
intermediate-state stores; it does not alter barriers, tile selection,
launch geometry, or shared-memory allocation. Cross-architecture CI on
SM90/SM100/SM120 would still be valuable because local kernel execution
was on SM121.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Performance**
* Improved MTP decoding by compiling kernel code once and reusing it
across intermediate-state caching modes.
* Reduced recompilation when switching between caching-on and
caching-off.

* **Bug Fixes**
* Ensured correct behavior when intermediate-state caching is disabled
by using a properly-shaped placeholder intermediate tensor.

* **Tests**
* Added a test that verifies compiled MTP kernels are reused across both
cache modes (for multiple batch sizes).
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: hebo1221 <hebo1221@users.noreply.github.com>

### [61011f7](https://github.com/flashinfer-ai/flashinfer/commit/61011f79790ea0b1046e0ebda15617dcd050fca9)

- **作者**: Emil Gilliam
- **时间**: 2026-08-13T22:49:40Z
- **提交信息**: feat(attention): cuDNN paged prefill via direct mixed-form cu_seq_lens (#4222)

## 📌 Description

Extends the cuDNN prefill **direct (token-unit) sequence-length path**
(#3921) to **paged KV**, using the cuDNN **mixed sequence-length form**
(cumulative on Q, per-batch on KV) that landed in cuDNN backend 9.25 +
cudnn-frontend (per-side relaxation).

**How it works.** The paged case binds:
- the token-unit `qo_indptr` as `cu_seq_len_q` — which *also* serves as
the Q/O ragged offset (per-tensor multipliers applied in the graph
builder), and
- the per-request KV lengths as `seq_len_kv`.

KV is addressed through the page tables, so — unlike the non-paged
both-cumulative path — **no KV-side cumulative prefix sum is
materialized, and no element-unit offset conversion is performed**. This
is the FlashInfer paged shape the mixed-form work was built to enable.

Gated separately from the non-paged path via
`_cudnn_supports_direct_seqlens(dtype, mixed=True)` (backend `>= 92500`,
frontend `>= 1.27`). Below the gate, the existing legacy
element-conversion paged graph is used unchanged — no behavior change
for current cuDNN versions.

Aside: the direct path also sidesteps the int32 overflow latent in the
legacy path's element-unit offsets (`token_offset * num_heads *
head_dim`) for large models, since token-unit indptrs stay at token
scale.

## Scope / status

Core low-level path only, kept localized to
`flashinfer/cudnn/prefill.py`. **The following are deferred to a
separate follow-up PR:**
- Wiring `BatchPrefillWithPagedKVCacheWrapper` (`backend="cudnn"`) to
pass token-unit `qo_indptr` + `actual_seq_lens_kv` so the wrapper takes
the direct path.
- LSE base-2 fold / de-pad for the unified-attention output contract.
- A NOT_SUPPORTED feature-probe fallback (the FE exposes no
compiled/effective-version query, so the gate is a version compare
today).

## 🔍 Related

- #3921 (token-unit indptr / cu_seq_len direct path — non-paged)
- cuDNN mixed-form sequence-length support (backend + cudnn-frontend,
merged separately)
- Aligns with P2 of the paged-prefill unification proposal (cuDNN
adapter: paged + cu_seq_len direct plumbing)

## 🧪 Tests

New `tests/attention/test_cudnn_prefill_paged_cu_seqlens.py`: compares
the paged **direct** path against the paged **legacy** path (itself
validated against the fa2 reference by `test_cudnn_prefill`) across
batch × seqlen × page_size × GQA × causal — **32/32 passed on H100
(sm90)**. The test probes real mixed-paged capability and skips cleanly
on older cuDNN.

Regression: `test_cudnn_prefill` (paged) 288 passed,
`test_cudnn_prefill_token_indptr` (non-paged direct) 130 passed.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **New Features**
  - Added mixed sequence-length handling for paged attention.
- Added support for independently supplied query and key/value sequence
lengths.
- Improved compatibility with direct sequence-length processing for
standard and paged inputs.

- **Bug Fixes**
- Updated processing to use direct handling when supported, with safe
fallback behavior otherwise.

- **Tests**
- Added coverage across batch sizes, sequence lengths, page sizes, head
counts, and causal attention modes.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>
Co-authored-by: Yang Xu <38851819+YangXu1990uiuc@users.noreply.github.com>

### [1711993](https://github.com/flashinfer-ai/flashinfer/commit/171199368056a56d676968b437e79b535b2edea8)

- **作者**: akhilg-nv
- **时间**: 2026-08-13T22:17:01Z
- **提交信息**: Support non-interleaved KV input to fmha_v2 (#4124)

<!-- .github/pull_request_template.md -->

## 📌 Description

Enables fmha_v2 API to accept non-interleaved paged KV input. If K & V
are allocated with a set offset, we can use `mUsesSharedKVIdx=false`
with a pre-expanded table of pointer offsets for the kernel to consume.

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

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added support for non-interleaved paged-KV prefill with separate key
and value cache tensors.
* Added support for NHD and HND layouts, multiple page sizes, and
different KV head configurations.
* Added support for shared and pre-expanded block-table formats in FMHA
v2 paged-KV execution.

* **Bug Fixes**
* Added validation for block-table types, dimensions, cache
compatibility, and memory alignment.
  * Improved paged-cache offset handling for more reliable execution.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Jimmy Zhou <79552142+jimmyzho@users.noreply.github.com>

### [d898ed0](https://github.com/flashinfer-ai/flashinfer/commit/d898ed046b6d1ebcf5d9a43ad3c7495add45d0c5)

- **作者**: Ace Eldeib
- **时间**: 2026-08-13T22:00:18Z
- **提交信息**: Fix TRTLLM ragged prefill edge cases (#3779)

<!-- .github/pull_request_template.md -->

## 📌 Description

I found my way here while debugging
https://github.com/vllm-project/vllm/issues/42426 which eventually
brought me to #3047 which seemed very similar to my issue, and porting a
similar fix to the trtllm ragged path solved it for me. This approach
uses a wrapper since the underlying kernel appears to still be closed
source despite the variety of OSS kernel dumps to flashinfer.

I had a similar branch to vllm
https://github.com/vllm-project/vllm/compare/main...alexeldeib:ace/trtllm-ragged-empty-row-compact-no-lse
but since #3047 was originally affecting sglang I thought it might make
sense to take it here instead

also i'm a kernel noob so forgive any basic errors, this was AI
assisted, but conceptually it seems to align with prior art/bugs, and it
does reliably resolve my issue in vllm (happy to share more details but
I figure 3047 is already validation of the theory in some part)

---

TRTLLM-GEN ragged attention packs non-paged SeparateQkv K/V rows along a
single token axis. Do not pass a synthetic batch stride into the TMA
descriptor for that singleton-batch layout; use zero stride instead so
both negative and positive int32 wraparound cases are avoided.

The Python wrapper now defines the empty-attention identity for rows
that have query tokens but no current KV tokens: out=0 and lse=-inf. It
launches the kernel only for active rows and scatters active results
back into the original output buffers, avoiding undefined empty-KV
kernel behavior.

Optional trusted CPU length mirrors let framework callers keep the
all-active fast path asynchronous. Direct callers without mirrors still
derive lengths from device indptrs and take the correctness-preserving
compaction path when empty rows are present. CUDA regression coverage
exercises stride overflow, positive stride wraparound, mixed empty-KV
rows, all-empty rows, direct-caller fallback, and invalid CPU length
mirrors.

Note, that last part does change the signature and may be an issue, but
might be useful in lieu of modifying the underlying kernel to handle
this directly?

## 🔍 Related Issues

Related: https://github.com/flashinfer-ai/flashinfer/issues/3047. This
is the TRTLLM-GEN empty-KV case called out in
https://github.com/flashinfer-ai/flashinfer/issues/3047#issuecomment-4473332762,
distinct from the FA2/FA3 path fixed in
https://github.com/flashinfer-ai/flashinfer/pull/3251.

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
- [ ] All tests are passing (`unittest`, etc.).

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added optional CPU-side Q/KV sequence-length mirrors to compact ragged
batches and efficiently handle empty KV rows.
* **Bug Fixes**
  * Corrected K/V batch-stride handling for SeparateQkv layouts.
* Ensured empty KV rows produce zero outputs and `-inf` log-sum-exp
values.
* Added validation requiring CPU length mirrors during CUDA graph
capture.
* **Tests**
* Expanded coverage for stride behavior, empty-row semantics, CPU-mirror
equivalence, and CUDA graph capture.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: Ace Eldeib <aeldeib@coreweave.com>

### [d69ab74](https://github.com/flashinfer-ai/flashinfer/commit/d69ab74db20f36ae35ac7394b649692140796963)

- **作者**: yichengj
- **时间**: 2026-08-13T20:59:02Z
- **提交信息**: feat(msa): fp8 index-k and index-q support in the SM12x proxy-score kernels (#4345)

## 📌 Description

This PR lets the MiniMax-M3 MSA proxy-score op on SM120/SM121
(`msa_proxy_score`) consume the fp8 (e4m3) index cache directly at every
shape, flat or paged, matching the vLLM MiniMax-M3 fp8 path where both
index-q and index-k are stored in fp8, so callers no longer dequantize
either operand.

Why fp8 proxy scoring at decode shapes was slow:

- fp8 index-k went to the general prefill schedule: every query head
re-read the shared index-k, and the schedule's per-KV-block barriers
dominate the one-block-per-CTA grids that split-K produces at decode
batch sizes.
- The e4m3 upconvert ran element by element on the CUDA cores, so the
convert rather than the K read became the bottleneck.
- fp8 index-q had to be dequantized by the caller on every call.

Fixes:

- Decode shapes with fp8 K route to two new head-fused schedules that
read the shared index-k once per kv head:
- Key-major (`MsaProxyScoreDecodeKeyMajorSm12x`, derived from vllm#48582
by @gau-nernst) for fused tiles of at most 32 head x token rows: keys
become the MMA M dimension, Q stays in registers across KV blocks, and a
TMA producer warp feeds a two-stage pipeline, cutting per-CTA fixed
cost.
- Key-split (`MsaProxyScoreDecodePackedFp8Sm12x`) for larger fused
tiles: warps split over keys instead of query rows, and K stays raw e4m3
through cp.async and shared memory.
- The upconvert runs once per K element with packed cvt instructions, in
registers between the shared-memory loads and the mma.
- fp8 index-q is consumed natively on the decode paths and upconverted
once internally elsewhere.

Public API and behavior changes:

- `msa_proxy_score` additionally accepts fp8 `q` when `k` is fp8, and
raises `ValueError` for fp8 `q` with non-fp8 `k`.
- Kernel routing changes for decode shapes with fp8 K and for bf16
multi-token fused tiles of at most 32 rows (now key-major).

### Performance

The MiniMax-M3 indexer shape (4 query heads, one index-k head, head dim
128), swept over context length S and decode batch B on RTX PRO 6000
Blackwell (Server Edition), RTX 5080, and GB10 (SM121). Timing is CUPTI
kernel time with L2 flushed between iterations, and only the score stage
is timed (top-k excluded). The baseline is vLLM's Triton MSA scoring
kernels (the SM12x path), at vLLM main `76d995df2c80`.

Each cell is a PRO 6000 / RTX 5080 / GB10 speedup triple (baseline time
/ FlashInfer time, so >1 means FlashInfer is faster). MTP = multi-token
prediction: MTP=N is the verify step for N draft tokens, i.e. m = N+1
query tokens per request.

#### fp8 decode vs FlashInfer w/o PR, MTP=0 (m=1)

| S | B=1 | B=8 | B=32 | B=128 |
|--:|:--:|:--:|:--:|:--:|
| 2k | 2.77 / 2.71 / 2.50 | 3.35 / 5.46 / 2.16 | 3.92 / 7.55 / 2.15 |
3.38 / 6.76 / 3.50 |
| 8k | 2.86 / 4.21 / 2.04 | 3.79 / 7.72 / 2.56 | 4.09 / 8.21 / 3.39 |
4.29 / 8.64 / 4.08 |
| 32k | 3.27 / 6.95 / 2.15 | 4.17 / 8.08 / 4.00 | 5.67 / 9.62 / 3.81 |
5.71 / 8.68 / 4.24 |

MTP=3 speedups are within about 10% of these.

#### fp8 decode vs vLLM Triton, MTP=0 (m=1)

| S | B=1 | B=8 | B=32 | B=128 |
|--:|:--:|:--:|:--:|:--:|
| 2k | 1.08 / 1.06 / 1.11 | 1.04 / 1.05 / 1.05 | 1.03 / 1.04 / 1.17 |
0.97 / 1.05 / 1.16 |
| 8k | 1.06 / 1.10 / 1.02 | 1.02 / 1.05 / 1.21 | 0.91 / 1.06 / 1.18 |
1.11 / 1.09 / 1.04 |
| 32k | 1.03 / 1.02 / 1.05 | 0.99 / 1.01 / 1.20 | 1.12 / 1.08 / 1.06 |
1.10 / 1.03 / 1.01 |

#### fp8 decode vs vLLM Triton, MTP=3 (m=4)

| S | B=1 | B=8 | B=32 | B=128 |
|--:|:--:|:--:|:--:|:--:|
| 2k | 0.95 / 0.98 / 1.02 | 0.93 / 0.97 / 1.02 | 0.98 / 1.01 / 1.18 |
0.98 / 1.01 / 1.18 |
| 8k | 0.96 / 1.00 / 0.98 | 1.00 / 1.02 / 1.19 | 0.89 / 1.06 / 1.17 |
1.11 / 1.10 / 1.04 |
| 32k | 1.00 / 0.99 / 1.04 | 0.88 / 0.99 / 1.19 | 1.11 / 1.08 / 1.05 |
1.09 / 1.03 / 1.01 |

<details>
<summary>bf16 decode, MTP=3 (m=4)</summary>

Listed because this PR also reroutes bf16 multi-token fused tiles of at
most 32 rows to the key-major schedule; bf16 single-token decode is
unchanged. Same cell format.

vs FlashInfer w/o PR:

| S | B=1 | B=8 | B=32 | B=128 |
|--:|:--:|:--:|:--:|:--:|
| 2k | 2.16 / 2.16 / 1.52 | 1.45 / 1.28 / 1.18 | 1.10 / 1.17 / 1.27 |
1.05 / 1.09 / 1.11 |
| 8k | 1.78 / 1.72 / 1.17 | 1.16 / 1.12 / 1.32 | 1.06 / 1.12 / 1.13 |
1.21 / 1.06 / 1.00 |
| 32k | 1.19 / 1.47 / 1.25 | 1.07 / 1.11 / 1.12 | 1.20 / 1.07 / 1.01 |
1.07 / 1.04 / 0.99 |

vs vLLM Triton:

| S | B=1 | B=8 | B=32 | B=128 |
|--:|:--:|:--:|:--:|:--:|
| 2k | 1.03 / 1.06 / 0.99 | 1.02 / 0.81 / 1.07 | 0.94 / 0.97 / 1.28 |
0.97 / 1.08 / 1.08 |
| 8k | 1.04 / 0.99 / 1.01 | 1.00 / 0.93 / 1.28 | 0.98 / 1.10 / 1.11 |
1.18 / 1.08 / 1.01 |
| 32k | 0.96 / 0.98 / 1.18 | 0.96 / 1.10 / 1.08 | 1.17 / 1.09 / 1.02 |
1.05 / 1.07 / 0.99 |

</details>

<details>
<summary>fp8 decode vs vLLM CuTe DSL (PR #48582)</summary>

This is the kernel vLLM's SM100 MSA path uses for small decode tiles,
and the one this PR's key-major schedule derives from.

MTP=0 (m=1):

| S | B=1 | B=8 | B=32 | B=128 |
|--:|:--:|:--:|:--:|:--:|
| 2k | 0.98 / 0.97 / 1.00 | 1.00 / 0.98 / 1.01 | 1.01 / 1.45 / 1.14 |
1.28 / 1.68 / 1.26 |
| 8k | 1.00 / 1.04 / 1.00 | 1.01 / 1.04 / 0.99 | 0.99 / 1.09 / 1.03 |
1.09 / 1.13 / 1.05 |
| 32k | 1.00 / 1.00 / 0.99 | 1.01 / 0.98 / 0.99 | 0.99 / 0.99 / 0.99 |
0.99 / 0.99 / 0.98 |

MTP=3 (m=4):

| S | B=1 | B=8 | B=32 | B=128 |
|--:|:--:|:--:|:--:|:--:|
| 2k | 0.94 / 0.99 / 0.97 | 0.95 / 1.16 / 1.04 | 1.12 / 1.71 / 1.25 |
1.52 / 1.96 / 1.43 |
| 8k | 0.97 / 1.02 / 0.99 | 1.02 / 1.07 / 0.99 | 1.00 / 1.18 / 1.05 |
1.15 / 1.20 / 1.09 |
| 32k | 0.98 / 1.01 / 0.97 | 0.99 / 0.97 / 0.96 | 0.99 / 1.00 / 0.99 |
0.99 / 0.98 / 1.00 |

</details>

fp8 proxy scoring at prefill shapes runs on the general schedule and is
compute-bound: fp8-K measured up to ~5% slower than bf16-K across S
512-8k (the in-register convert cost). fp8 support there exists so
callers can pass the fp8 index cache at every shape without
dequantizing, not for speed.

## 🔍 Related Issues

Stacked on #4324; the first commits here are that PR and drop out of the
diff once it merges.

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

- Extended
`tests/msa_ops/test_msa_ops.py::test_msa_proxy_score_paged_fp8` with
decode-shape fp8 coverage: flat and paged K, bf16/fp16/fp8 q,
single-token and multi-token (spec-decode) query lengths, plus the
prefill-shape fp8-q fallback. All fp8 results assert bit-exact equality
against the dequantized-K reference.
- Full `tests/msa_ops/` suite passing on RTX 5080 (SM120), DGX Spark
GB10 (SM121), and RTX PRO 6000 Blackwell Server Edition (SM120).

## Reviewer Notes

- The fp8 tests assert bit-exact equality (`torch.equal`) against
dequantized-K runs, which is sound because the e4m3 -> f16/bf16
upconvert is exact. The key-major schedule regroups mma products, so its
test feeds e4m3-representable q (what deployment provides) to keep every
f32 dot term exact.

AI-assisted (Claude Code).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added FP8 E4M3 support for query and key inputs during proxy-score
decoding.
  * Added optimized packed and key-major decoding paths.
* Expanded support for paged key-value data, varied group sizes, and
non-divisible groups.
* Added handling for causal offsets, padding masks, empty sequences, and
multiple decode modes.

* **Bug Fixes**
* Improved dispatch and data conversion for consistent results across
supported input formats.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [140be0e](https://github.com/flashinfer-ai/flashinfer/commit/140be0ea099e64c78803c803a980a3c9de72153e)

- **作者**: qsang-nv
- **时间**: 2026-08-13T20:57:06Z
- **提交信息**: skip the deliberate-trap test under compute-sanitizer (#4493)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->
fix https://nvbugspro.nvidia.com/bug/6563314

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

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Tests**
* Updated CUDA graph testing to skip a test when compute-sanitizer is
active.
* Added a clear explanation for the skip, preventing intentional kernel
traps from causing sanitizer timeouts.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: Qidi Sang <200703406+qsang-nv@users.noreply.github.com>

### [ed4ed65](https://github.com/flashinfer-ai/flashinfer/commit/ed4ed65c031715bf64c93f69ae83fe3a6a377409)

- **作者**: Jimmy Zhou
- **时间**: 2026-08-13T20:37:32Z
- **提交信息**: chore(codeowners): add @jimmyzho to tests/attention/ (#4508)

<!-- .github/pull_request_template.md may exist; body kept short and
factual -->
## 📌 Description

Adds `@jimmyzho` as a code owner for `tests/attention/`, matching the
existing ownership of `csrc/fmha_v2/`.

## 🔍 Related Issues

N/A

## ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

- [x] Tests have been added or updated as needed. (N/A — CODEOWNERS-only
change)
- [x] All tests are passing (`unittest`, etc.).

## Reviewer Notes

Docs/ownership-only change; no code or build impact.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Chores**
  * Updated code ownership settings for attention-related tests.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [ba6bf4e](https://github.com/flashinfer-ai/flashinfer/commit/ba6bf4e5b63b299952afaa768c1caa863829f309)

- **作者**: leonardHONG
- **时间**: 2026-08-13T17:59:27Z
- **提交信息**: perf(gdn): reuse pretranspose kernels across pool capacity and stride (#4444)

## 📌 Description

Make the leading pool dimension of the GDN pretranspose path dynamic:

- Treat pool capacity and `stride[0]` as runtime values.
- Keep `HV/V/K` and inner strides compile-time static.
- Remove pool capacity and leading stride from the compilation cache
key.
- Preserve 64-bit pool-offset arithmetic.

This allows one compiled kernel to be reused across non-contiguous state
pools with different capacities and leading strides.

## 🔍 Related Issues

Partially addresses #4110.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit`.
- [x] I have installed the hooks.
- [x] I have run `pre-commit run --all-files`.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All relevant tests are passing.

Validated on H800/SM90a and RTX 5090/SM120, including non-contiguous
pools, compile reuse, and large 64-bit offsets. No steady-state
regression was observed; cold compilation time was reduced by
approximately 62%.

## Reviewer Notes

Only the outer pool mode is dynamic. Inner dimensions and strides remain
static for kernel specialization.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Performance**
* Improved pretranspose kernel reuse across different pool capacities
and outer memory layouts, reducing unnecessary recompilation.
* Preserved separate handling for layouts with differing inner strides.

* **Reliability**
* Added validation to reject pool slot strides that are not properly
aligned for efficient data transfer.

* **Tests**
* Expanded coverage for cache reuse, layout variations, alignment
validation, and environments where the optional kernel is unavailable.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: 梁厚宏 <2695316095@qq.com>

### [2febce5](https://github.com/flashinfer-ai/flashinfer/commit/2febce559f466aa2b0adaca3f78c172c22066321)

- **作者**: yichengj
- **时间**: 2026-08-13T15:49:59Z
- **提交信息**: feat(gemm): port SM12x MXFP8 dense GEMM from b12x (#4305)

## 📌 Description

Adds a `b12x` backend to `mm_mxfp8` for SM120/SM121, ported from
[b12x](https://github.com/local-inference-lab/sparkinfer). It
outperforms the existing CUTLASS backend at small and large token counts
on the target shapes (numbers below) and serves the MXFP8 W8A8
projections of Nemotron-family checkpoints.

Changes:

- Extend the SM120 warp-level block-scaled GEMM kernel, also used by
`mm_fp4(backend="b12x")`, with an MXFP8 operand path and small-M tile
shapes.
- Register `b12x` as a new `mm_mxfp8` backend and prefer it in `auto`
mode on SM120/SM121.
- Fix an epilogue race in the shared kernel: the next work tile could
overwrite the output tile's smem while its TMA store was still in
flight, corrupting short-K multi-wave launches.

Public API and behavior changes:

- `mm_mxfp8` accepts `backend="b12x"`. On SM120/SM121, `auto` now
selects it when eligible (CUDA 13+, nvidia-cutlass-dsl >= 4.6.0
installed, K a multiple of 128).
- `mm_fp4(backend="b12x")` no longer corrupts output on short-K launches
that span more than one wave.

## 📊 Performance

Speedup over the CUTLASS backend on the linear-projection shapes of the
target checkpoints:

| m | DGX Spark GB10 | RTX 5080 | RTX Pro 6000 SE |
|---|---|---|---|
| 1-8 | 1.43-2.18x | 2.07-2.67x | 1.83-3.25x |
| 16-32 | 0.98-1.68x | 1.13-2.45x | 1.04-2.55x |
| 64-128 | 0.94-1.00x | 1.00-1.46x | 0.81-1.24x |
| 512-2048 | 1.11-1.48x | 1.18-1.51x | 1.12-1.45x |

## 🔍 Related Issues

#4223 (item 6).

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added b12x backend support for MXFP8 matrix multiplication on
SM120/SM121 GPUs.
* Added automatic planning, compilation, caching, and execution for
supported MXFP8 workloads.
  * Expanded support for smaller dense GEMM tile sizes.

* **Bug Fixes**
  * Improved shared-memory synchronization during kernel execution.
* Added validation for supported scale layouts, tile shapes, and K
dimensions.

* **Tests**
* Added coverage for low-M, short-K, decode-M, and multi-wave MXFP8 and
FP4 workloads.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [c517c07](https://github.com/flashinfer-ai/flashinfer/commit/c517c07bddc0aa22709728a18d63d35ca6703d62)

- **作者**: yifeis-nv
- **时间**: 2026-08-13T15:48:14Z
- **提交信息**: feat(quantization): cuTile per-token-group 8bit quant + fused RoPE-FP8 (#4019)

## 📌 Description

Adds two cuTile quantization kernels (public `cuda.tile` API), opt-in
`backend="cutile"`.

**Why FlashInfer wants this:** `rope_quantize_fp8` fuses RoPE + FP8
quantization into one pass for the MLA / DeepSeek paged-KV append path
(replaces separate rope + quant launches); `per_token_group_quant_8bit`
provides the block-scaled FP8/INT8 quantizer feeding the groupwise FP8
GEMM path.

**Added**
- `per_token_group_quant_8bit_cutile` — FP8 / INT8 per-token-group
quant, row/col-major scale.
- `rope_quantize_fp8_cutile` — fused RoPE + FP8 quant (MLA 2D latent
key) → `rope_quantize_fp8(..., backend="cutile")`.

### Benchmarks

Canonical `benchmarks/bench_*_backend_comparison.py` (argparse
`--providers`/`--csv`, inline correctness verify, `bench_gpu_time`
kernel self-time, speedup-vs-SOTA table + heatmap):
- `bench_per_token_group_quant_8bit.py` — cuTile vs **sgl_kernel**
(SOTA) / SGLang triton / torch, over a (num_tokens × hidden_dim) sweep.
- `bench_rope_quantize_fp8_backend_comparison.py` — fused MLA RoPE+fp8
cuTile vs the **native fused CUDA** kernel (SOTA) / torch, over a
num_tokens sweep.

Measured on **B200 (sm100)**, median kernel time, speedup = SOTA ÷
cuTile (>1 = cuTile faster).

**`per_token_group_quant_8bit`** vs sgl_kernel — sweep
num_tokens{1…4096} × hidden{2048,4096,7168}, **geomean 0.72×**. cuTile
is at parity while the op is launch-bound and falls behind once it
becomes bandwidth-bound:

| num_tokens | hidden 2048 | 4096 | 7168 |
|---|---|---|---|
| 1–64 | 1.00× | 1.00× | 1.00× |
| 128 | 0.99× | 1.00× | 0.79× |
| 256 | 1.00× | 0.80× | 0.71× |
| 512 | 0.80× | 0.71× | 0.57× |
| 1024 | 0.71× | 0.58× | 0.50× |
| 4096 | 0.45× | 0.42× | 0.39× |

SGLang's triton kernel tracks cuTile closely (0.9–1.0× across the
sweep); torch is 3–6× slower than both. So cuTile is competitive with
sgl_kernel at small token counts and ~2–2.5× behind at serving-scale
batches — a per-token-group memory-access follow-up, not a default-path
regression (the backend is opt-in).

**`rope_quantize_fp8` (MLA, 128 heads, head_size 576)** vs the native
fused CUDA kernel — sweep num_tokens{1…4096}, **geomean 0.87×**: cuTile
**wins at ntok ≤ 16** (1.00–1.10×), ~0.90–0.94× at 32–128, settling at
0.75–0.83× for ntok ≥ 256. Both are ~3× faster than the torch reference.

## 🔍 Related Issues

Part of a 3-way split of the cuTile migration (attention / quantization
/ GEMM), replacing #3959. Sibling PRs: #4018 (attention), #4020 (GEMM).

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

Measured on B300 / sm103:
- rope MLA + per-token-quant: 66 passed
- GQA/MHA rope correctly gated (`NotImplementedError`, not a crash)
- new coverage: non-power-of-two `group_size`, column-major scale
strides, TMA scale padding, UE8M0 power-of-two scales

## Reviewer Notes

Carries the shared `cached_replace_hints` helper in
`flashinfer/cutile/cutile_common.py` (also in the GEMM PR, #4020) —
whichever merges second drops the duplicate hunk on rebase.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added public per-token-group 8-bit quantization API with FP8/INT8
outputs, row/column-major scales, TMA-aligned scales, and UE8M0
encoding.
  * Added a selectable `cutile` backend for fused FP8 RoPE quantization.
* Re-exported an additional FP8 quantization utility in the public
quantization API.
* **Performance**
* Reduced repeated cuTile compilation overhead via cached hinted-kernel
launches.
* **Tests**
* Extended RoPE and per-token-group 8-bit quantization tests to validate
both CUDA and cuTile paths and scale layout/edge cases.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [b065838](https://github.com/flashinfer-ai/flashinfer/commit/b065838a4710b527d6c73ab7d95af161e83aee1a)

- **作者**: En-Ming Huang
- **时间**: 2026-08-13T12:15:41Z
- **提交信息**: Add distribution-aware autotuning for TRT-LLM MoE (#4106)

## 📌 Description


MoE performance depends on routing distribution as well as tensor shape.
The existing TRTLLM-Gen autotuner benchmarks tactics with randomly
generated routing inputs and reuses one shape-only winner for all
requests of that shape. Different expert-skew patterns can change load
balance, memory access, and communication behavior, making different
tactics optimal.

This MR adds opt-in distribution-aware (DA) autotuning for TRTLLM-Gen
MoE.


## 🔍 Related Issues

No.

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

## Reviewer Notes

### Distribution-aware autotuning

Instead of benchmarking tactics with one random routing distribution,
the autotuner generates routing logits from Dirichlet distributions with
different concentration parameters, producing varying degrees of expert
skew. It benchmarks every fused-MoE configuration (a **tactic**) for
every routing distribution and token-count bucket, then records the
fastest tactic.

Each routing distribution is represented by an **exemplar**: an
*N*-dimensional normalized occupancy vector, where *N* is the number of
local experts and each element is that expert's fraction of assigned
tokens. The vector is sorted in ascending order so equivalent expert
permutations have the same representation. This produces a `(token
count, exemplar) -> tactic` mapping. Exemplars that choose the same
tactic are merged by averaging their normalized occupancy vectors,
reducing both storage and runtime lookup cost.

### Runtime kernel selection

At runtime, the expert assignments are already GPU-resident. The graph
counts tokens per local expert, normalizes and sorts the counts to form
the runtime occupancy vector, and compares it with the stored exemplars
in the matching token bucket using cosine similarity. The nearest
exemplar selects the tactic, and a CUDA conditional `SWITCH` graph node
dispatches its fixed fused-MoE kernel. All selection work stays on
device: no routing-value transfer, host-side lookup, synchronization, or
CUDA-graph recapture is required.

## Implementation Details

The generic autotuner is extended with `DynamicValueSpec`, which
supplies bucketed routing-value profiles and input generators for
value-aware benchmarking. The autotuner records tactic timings for each
representative routing distribution while also publishing the winner for
the default, caller-provided profile to the existing shape-only cache.
This preserves the existing eager-execution behavior and API.

The DA policy and graph runtime are implemented under
`flashinfer/fused_moe/dist_aware/`. This code generates Dirichlet-based
routing samples, builds the per-token-bucket exemplar plan, and owns
plan serialization, compatibility checks, and the baseline-guard
decision.

`flashinfer/fused_moe/core.py` integrates DA preparation into the
existing public MoE wrappers rather than adding a parallel API. Each
wrapper retains its normal validation and runner construction, while
additionally providing a fixed-tactic, metadata-based launch path for
graph replay. Unsupported configurations, unavailable plans, and eager
calls fall back to the original monolithic wrapper path.

`DynamicValueSpec` is used only during autotuning, not for
inference-time dispatch. During graph capture, the runtime computes live
occupancy from GPU routing data, matches it on device, and selects a
pre-captured fixed-tactic body. Outside CUDA graphs, eager execution
continues to use the shape-only tactic selected from the default routing
profile.

Before publishing a DA plan, a baseline guard compares recorded
per-distribution latency against the corresponding shape-only NoDA
tactic, including estimated selector/control overhead. If DA does not
provide a sufficient win, the plan is rejected and graph capture uses
the original monolithic NoDA path instead. DA is experimental and opt-in
(`FLASHINFER_DIST_AWARE_AUTOTUNE=1`).


## Usage

### Enable distribution-aware autotuning

DA-MoE is disabled by default. Enable it before starting the serving
process or benchmark:

```bash
export FLASHINFER_DIST_AWARE_AUTOTUNE=1
```

No API change is required: supported TRTLLM blocked-MoE wrappers
automatically tune during the normal AutoTuner warmup and realize the
resulting plan during CUDA-graph capture. Set the variable to `0` or
unset it to disable DA.

### Run the ordinary DeepSeek MoE benchmark

The existing DeepSeek benchmark exercises DA through the ordinary public
MoE wrappers. Graph mode is the default; routed mode supplies
caller-provided expert IDs and routing weights to the TRTLLM path:

```bash
# Run from the FlashInfer repository root.
export FLASHINFER_DIST_AWARE_AUTOTUNE=1

python -u benchmarks/bench_moe_deepseek.py \
  --num-tokens 64,128,256,512,1024 \
  --num-experts 128 \
  --ep 2 \
  --backends cutedsl,trtllm \
  --distributions ddist:0.1,ddist:1,ddist:2,ddist:3,ddist:4 \
  --routing-input-mode routed
```

`--backends` accepts any subset of `cutedsl,cutlass,trtllm`. Use `--ep`
to derive the local expert count from `--num-experts`. `--no-cuda-graph`
is an eager diagnostic and does not exercise device-side DA selection.
The benchmark sets the DA distribution list from `--distributions` and
performs its autotuning warmup before timed graph replay. Routed graph
mode explicitly enables DA inside this benchmark; use the dedicated
benchmark below for a matched graph-mode NoDA-versus-DA comparison.

### Tune and save the tuning cache

Pass a new JSON path to the normal `autotune(..., cache=path)` context.
The cache is loaded on context entry and saved automatically on
tuning-context exit. The dedicated benchmark exposes the same path as
`--cache` (`--tuning-cache` and the historical `--bundle-output`
spelling remain aliases):

```bash
# Run from the FlashInfer repository root.
python benchmarks/bench_trtllm_moe_da.py \
  --precision nvfp4 \
  --distributions uniform,ddist:1.1,ddist:1.5,ddist:2,ddist:3,ddist:4 \
  --num-tokens 8,32,64,128,256,512,1024,2048,4096,8192 \
  --num-experts 256 \
  --local-num-experts 32 \
  --top-k 8 \
  --hidden-size 7168 \
  --intermediate-size 2048 \
  --n-group 8 \
  --topk-group 4 \
  --tune-max-num-tokens 8192 \
  --warmup 3 \
  --iters 10 \
  --execution-mode graph \
  --cache "$artifact_root/tuning-cache.json" \
  --out "$artifact_root/results.csv" \
  --json-out "$artifact_root/results.json"
```

The cache contains ordinary AutoTuner tactics and namespaced DA records
in one JSON file. DA records include the exact operation/configuration
identity, compiled plan mode, selector exemplars, deduplicated bodies,
and graph-free eager selection. The cache is environment-specific. A
current-schema record mismatch is ignored and requires retuning; a
definite cross-environment metadata conflict is ignored and is not
overwritten. Use one writer per cache path while publishing DA records.

The default tuner catalog contains seven distributions (`ddist:1.1`,
`ddist:1.3`, `ddist:1.5`, `ddist:1.7`, `ddist:2`, `ddist:2.5`, and
`ddist:4`) with one realization each. The dedicated benchmark's replay
default is the six-distribution list shown above. At most eight total
selector exemplars may be requested, so `number of distributions ×
FLASHINFER_DA_DISTRIBUTION_SAMPLES` must not exceed eight.

### Reload a saved tuning cache

Use the same cache path and operation/configuration in a fresh process.
`autotune(False, cache=path)` loads without profiling. For the dedicated
benchmark, repeat the tuning command with `--skip-autotune` and new
result paths:

```bash
python benchmarks/bench_trtllm_moe_da.py \
  --precision nvfp4 \
  --distributions uniform,ddist:1.1,ddist:1.5,ddist:2,ddist:3,ddist:4 \
  --num-tokens 8,32,64,128,256,512,1024,2048,4096,8192 \
  --num-experts 256 \
  --local-num-experts 32 \
  --top-k 8 \
  --hidden-size 7168 \
  --intermediate-size 2048 \
  --n-group 8 \
  --topk-group 4 \
  --tune-max-num-tokens 8192 \
  --warmup 1 \
  --iters 10 \
  --execution-mode graph \
  --cache "$artifact_root/tuning-cache.json" \
  --skip-autotune \
  --out "$artifact_root/cache-only-results.csv" \
  --json-out "$artifact_root/cache-only-results.json"
```

The public wrapper restores compatible DA state automatically before
capture. The cache-only benchmark fails instead of silently profiling
when the requested operation/configuration has no compatible saved
record.

### Expected tuning time

Exact-current Full AC tuning and fresh-process cache times are below.
The run reused a warm JIT workspace after the focused CUDA suites; these
values measure the requested tuning/cache transactions rather than
first-use compiler and download latency. They are diagnostic because the
authorized node was oversubscribed.

| Precision | NoDA fresh (s) | DA fresh (s) | NoDA cache (s) | DA cache
(s) |
|---|---:|---:|---:|---:|
| NVFP4 | 19.719 | 24.148 | 0.506 | 0.162 |
| MXFP4 | 27.123 | 28.500 | 0.510 | 0.176 |
| W4A16 | 10.874 | 69.608 | 0.512 | 1.158 |
| BF16 | 8.746 | 25.762 | 0.376 | 0.147 |
| FP8 per-tensor | 5.397 | 20.570 | 1.641 | 1.183 |
| FP8 block | 4.179 | 25.965 | 0.391 | 0.168 |
| MXFP8 | 32.849 | 38.034 | 0.511 | 0.173 |
| MXINT4 | 9.261 | 49.403 | 0.515 | 0.171 |

## Benchmark Results

### Ordinary public-wrapper benchmark

The `benchmarks/bench_moe_deepseek.py` workflow above was measured on
1000 W B200 nodes with a 128-expert, EP=2 DeepSeek-shaped MoE, routed
input, tokens 64–1024, and distributions `ddist:0.1`, `ddist:1`,
`ddist:2`, `ddist:3`, and `ddist:4`. It produced 25 paired graph-mode
TRTLLM rows. Each cell is the minimum–maximum `DA-disabled TRTLLM
latency / DA-enabled TRTLLM latency` across the five distributions;
values above 1.0 favor DA.

| 64 | 128 | 256 | 512 | 1024 |
|---:|---:|---:|---:|---:|
| 1.004–1.007x | 1.004–1.008x | 1.506–2.552x | 0.976–1.000x |
1.488–1.655x |

### Dedicated NoDA-versus-DA benchmark

DeepSeek-V3 EP8 shape: 256 global experts, 32 local experts, top-k 8,
hidden size 7168, intermediate size 2048, `n-group=8`, and
`topk-group=4`. It evaluates eight precision families, six routing
distributions, and ten token counts with three warmups and the median of
ten CUDA-graph replays per row.


| Precision | 8 | 32 | 64 | 128 | 256 | 512 | 1024 | 2048 | 4096 | 8192
| Overall |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| NVFP4 | 0.9974x | 1.0031x | 1.0163x | 1.1177x | 1.1160x | 1.0008x |
0.9983x | 0.9995x | 0.9932x | 0.9952x | 1.0227x |
| MXFP4 | 1.0063x | 1.0033x | 1.0661x | 1.3152x | 1.3387x | 0.9879x |
0.9895x | 1.0238x | 0.9948x | 0.9956x | 1.0651x |
| W4A16 | 1.0004x | 1.0220x | 1.2578x | 1.7240x | 1.4206x | 1.5738x |
0.9887x | 0.9983x | 0.9887x | 0.9740x | 1.1677x |
| BF16 | 1.0031x | 1.0063x | 1.0928x | 1.3677x | 1.2830x | 1.1377x |
1.1969x | 1.0281x | 0.9917x | 0.9647x | 1.0999x |
| FP8 per-tensor | 1.0046x | 1.0384x | 1.1651x | 1.1941x | 1.1557x |
1.1008x | 1.2138x | 0.9905x | 1.0100x | 1.0027x | 1.0844x |
| FP8 block | 1.0034x | 1.0807x | 1.3598x | 1.3423x | 1.1516x | 0.9923x
| 1.1187x | 1.1861x | 0.9615x | 0.9850x | 1.1101x |
| MXFP8 | 1.0007x | 1.0654x | 1.2058x | 1.2346x | 1.2281x | 0.9996x |
1.0015x | 0.9721x | 1.0038x | 0.9885x | 1.0653x |
| MXINT4 | 1.0024x | 1.4091x | 2.0148x | 2.0042x | 1.5466x | 1.1914x |
1.3027x | 0.9778x | 0.9800x | 0.9822x | 1.2913x |

Fresh compiled plan outcomes were 330 `da_single_body`, 114
`da_fallback`, and 36 `da_switch` rows. Actual capture outcomes were 330
single-body, 114 fallback, 30 switch, and 6 pristine
`noda_capture_fallback` rows. The carried per-row performance waiver
remains explicit; the aggregate table is release evidence, not a claim
that every row speeds up.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added distribution-aware MoE routing/autotuning with CUDA Graph
capture improvements and optional baseline-guard behavior.
* Introduced value-aware autotuning (value buckets/profiling) with
reusable profiling bundles.
* Added routing-metadata replay execution across BF16/FP8/FP4/MXINT4,
plus multi-tile DeepSeek routing on supported GPUs.
* Expanded MoE benchmarks and CLI options (routing modes, distributions,
precisions) with CSV reporting.

* **Bug Fixes**
  * Improved FP4 tensor dtype deduction for more scale layouts.
  * Corrected cuBLASLt handle management in FP8 paths.

* **Documentation**
* Documented new distribution-aware and value-aware autotuning/dispatch
environment options.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Anthony Chang <27950904+rosenrodt@users.noreply.github.com>

### [0d25b18](https://github.com/flashinfer-ai/flashinfer/commit/0d25b1834093af06f47823b1df1d9deab286f494)

- **作者**: Bi Tiekai
- **时间**: 2026-08-13T09:41:12Z
- **提交信息**: feat(moe): MXFP8 x MXFP4 CuTe-DSL fused MoE for SM100, plus large-batch routing locality (#4440)

## 📌 Description

  Two related changes to the Blackwell CuTe-DSL MoE path.

  **1. MXFP8 x MXFP4 fused MoE (SM100/SM103)** — `e3bc88b3`

A mixed-precision path: MXFP8 (E4M3 + linear block-32 E8M0) activations
against
packed MXFP4 (E2M1 + MMA-layout block-32 E8M0) weights, with an MXFP8
FC1
  intermediate and BF16 finalized output.

- Both grouped-GEMM kernels take separate `a_dtype`/`b_dtype`, size SMEM
from
`smem_alloc_*_dtype`, and load the narrow operand via TMA `UNPACK_U8`.
- The FC1 epilogue emits the same exact UE8M0 codes as `mxfp8_quantize`
and
scalar-stores them as bytes, avoiding the unsupported `vector<2xE8M0>`
    conversion/store lowering.
  - New public APIs `cute_dsl_fused_moe_mxfp8_mxfp4` and
`CuteDslMxfp8Mxfp4MoEWrapper`, with their own tactic space and autotune
cache
    namespace so NVFP4 results and cache entries are unaffected.
- GEMM2 `can_implement` no longer requires N to divide the MMA N tile:
the
finalize epilogue already clamps its bulk-reduce to `valid_columns`,
which
`tests/moe/test_cute_dsl_moe_can_implement.py` documents. A
partial-N-tile
    case is added to the grouped-GEMM test to cover it.

**2. Contiguous per-CTA route windows in `moe_sort` at large batches** —
`5e0f9e64`

The cooperative routing kernel assigns each CTA a grid stride of
expanded
indices, and an expert's rows land in CTA-arrival order, so one expert's
rows
are drawn from the whole batch. A grouped-GEMM tile then gathers across
the
entire activation tensor, and the footprint grows with the batch:
measured on
B200 (hidden 6144, 256 experts, top_k 8, 32 local, tile 256) a GEMM1
tile
touches 94 distinct 2 MiB pages at 64K tokens, 190 at 128K and 228 at
256K,
  which outgrows the uTLB.

With `mUseContiguousRouteWindows` each CTA owns one contiguous span
instead, so
a tile gathers from a few narrow token windows and the footprint stays
flat at
  ~28-38 pages. `moe_sort` enables it from 65536 tokens:

  | tokens | GEMM1 | full MoE pipeline | 2 MiB pages / tile |
  |---:|:--|:--|:--|
  | 65536 | 1.00-1.10x | 0.99-1.03x | 94 -> 38 |
  | 131072 | 1.40-1.44x | **1.17-1.18x** | 190 -> 32 |
  | 262144 | 1.43-1.47x | **1.24-1.28x** | 228 -> 29 |

The flag defaults to off, so every other caller of the routing kernels,
including the TRT-LLM MoE backend, keeps its current ordering bit for
bit.

  ## 🔍 Related Issues

  <!-- link related issues here -->

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

  New tests: `tests/moe/test_cute_dsl_mxfp8_mxfp4_grouped_gemm.py`,
  `tests/moe/test_cute_dsl_mxfp8_mxfp4_fused_moe.py`,
  `tests/moe/test_moe_sort_route_windows.py`.

  Run on B200 (SM100):

- `tests/moe/test_cute_dsl_fused_moe.py` plus the three MXFP8 x MXFP4 /
    `can_implement` files — 564 passed
- `tests/moe/test_moe_sort_route_windows.py` plus MXFP8 x MXFP4 end to
end — 12 passed
  - `tests/trace/test_fi_trace_template_consistency.py`,
    `tests/trace/test_template_init.py` — 818 passed, 167 skipped

  ## Reviewer Notes

- The routing change touches `RoutingKernel.cuh`, shared with the
TRT-LLM MoE
backend. It is gated behind a `DataBase` flag that only `moe_sort` sets,
so
TRT-LLM paths are unchanged; that separation is the main thing worth
checking.
  - Scope of the new ordering: all three CuTe-DSL MoE entry points share
`moe_sort` (`cute_dsl_fused_moe_nvfp4`, `cute_dsl_fused_moe_mxfp8_mxfp4`
and
the W4A16 path), so all three pick it up above the threshold. NVFP4 uses
the same gather kernel so the
mechanism applies, but its packed-FP4 activations are half the bytes per
    token, so its benefit is not that much.
- Only the cooperative routing path honours the flag, so it applies
while that
path is selected (roughly 65536 to ~570K tokens at 256 experts / top_k 8
on a
148-SM B200). Above that the multi-kernel path runs and the flag is
ignored.
- This is a locality change, not an ordering guarantee: rows within an
expert
    still land in atomic-arrival order and the permutation stays
non-deterministic run to run, exactly as before. Only each CTA's source
range
    becomes contiguous.
- Two subtleties in the coop kernel are load-bearing: the per-CTA span
is sized
to keep every CTA busy rather than fixed at the per-thread maximum, and
each
CTA must stop at its own span end. Without the latter the trailing
iterations
    run into the next CTA's span — still below `expandedIdxSize`, so the
batch-size check alone does not stop them — and those routes get counted
and
permuted twice. `test_moe_sort_route_windows.py` asserts per-expert row
counts
against the routing histogram, which is what catches this class of bug;
a
bijection check alone does not, since a duplicated permutation is still
    self-consistent.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added MXFP8 activation × MXFP4 weight support for fused
Mixture-of-Experts workloads on compatible GPUs.
* Added public APIs, reusable wrappers, autotuning, tracing, and
documentation for mixed-precision fused MoE operations.
* Improved large-batch routing with contiguous route windows for more
localized processing.

* **Bug Fixes**
* Improved validation, scaling, alignment, memory handling, and output
quantization.
  * Preserved compatibility with existing NVFP4 APIs.

* **Tests**
* Added functional, integration, routing, and numerical correctness
coverage.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Tiekai Bi <tiekaib@nvidia.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-08-14
**监控日期**: 2026-08-13
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3945
- **最后更新**: 2026-08-13T17:31:40Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-08-14
**监控日期**: 2026-08-13
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34306
- **最后更新**: 2026-08-13T20:52:54Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 4
- **主要提交者**: YiYi Xu, Wang, Yi, Sayak Paul

## AI分析总结

# 提交分析总结

## 1. 主要更新类型

本批次提交以**文档更新**为主，辅以**Bug修复**和**代码清理**。具体包括：Agent文档完善、Nunchaku Lite性能指南补充、PEFT版本逻辑清理、AuraFlow模型并行性修复及XPU测试更新。

## 2. 关键变更点与项目方向的关系

- **Agent文档系统化**（#14452）：基于Wan-Animate-2模块化集成的实战经验，系统记录了`_skip_keys`分组卸载机制、模块化模型打包规范、变体预设配置等关键模式。这与diffusers作为统一多模态生成框架的目标高度一致，通过文档沉淀最佳实践，降低社区集成新模型的成本。
- **Nunchaku Lite性能文档**（#14458）：补充融合内核性能数据，帮助用户在量化场景下做出更明智的部署决策，强化了项目在高效推理方向的价值主张。
- **PEFT版本逻辑清理**（#14463）：移除复杂的版本条件判断，简化代码路径，提升可维护性，符合项目长期演进中对依赖管理清晰化的需求。
- **AuraFlow设备不匹配修复**（#14273）：修复`device_map="auto"`下`register_tokens`与编码器隐藏状态的跨设备拼接问题，同时更新XPU后端版本差异的测试期望值，体现了对多硬件后端（XPU）和模型并行场景的持续支持。

## 3. 项目影响与潜在意义

文档更新显著降低了新模型集成门槛，特别是模块化规范的确立，为社区贡献者提供了明确指引。PEFT清理减少了维护负担，而AuraFlow修复提升了模型并行场景的稳定性，对大规模部署至关重要。XPU测试更新表明项目正积极扩展Intel硬件生态支持。

## 4. 值得关注的技术点

- **`_skip_keys`机制**：用于分组卸载时排除特定键，是处理大模型显存优化的关键工具。
- **模块化模型打包规范**：包括独立子模块、`InsertableDict`分组、变体预设自带`model_name`等约定，形成了清晰的架构模式。
- **`randn_tensor`陷阱**：文档特别提醒了该函数的潜在问题，帮助开发者避免常见错误。
- **AuraFlow修复细节**：将`register_tokens`移至投影后的编码器隐藏状态所在设备并转换dtype，是跨设备张量操作的典型解决方案。

## 5. 对项目发展的影响

结合README背景，diffusers致力于提供统一的扩散模型工具链。本批次提交通过**文档规范化**和**代码清理**，巩固了项目作为社区协作平台的基础设施地位。模块化集成指南的完善将吸引更多高质量模型接入，而多硬件支持和性能文档则强化了项目的生产级可用性。整体上，这些变更体现了项目从功能扩张向**生态成熟度提升**的过渡，为长期稳定发展奠定基础。

## 详细提交记录

### [35ab485](https://github.com/huggingface/diffusers/commit/35ab485bdea676dbcbc77de60d77f7acb4f390fd)

- **作者**: YiYi Xu
- **时间**: 2026-08-13T20:52:44Z
- **提交信息**: [Agent docs] some updated based on recent integration  (#14452)

* Add agent-doc lessons from the Wan-Animate-2 modular integration

- models.md: document _skip_keys (group offloading exclude_kwargs +
  device_map dispatch skip_keys) with the in-tree cache examples
- modular.md: canonical flat-blockset packing (standalone children,
  InsertableDict groups, no cross-preset-file imports); variant presets
  carry their own model_name + mapping entry (#14451); composed-blockset
  inputs/outputs overrides; guider ownership and
  requires_unconditional_embeds; always ship modular_model_index.json;
  auto-docstring drift + check_forward_call_docstrings checklist items;
  randn_tensor gotcha
- pipelines.md: the same randn_tensor gotcha

Co-Authored-By: Claude Fable 5 <noreply@anthropic.com>

* Apply suggestions from code review

Co-authored-by: Steven Liu <59462357+stevhliu@users.noreply.github.com>

* Address review comments

Reword the `_skip_keys` guidance: "non-tensor runtime objects holding large tensors"
contradicted itself, say "state the model places itself" instead.

Drop the paragraph claiming the guider spec is declared only by the denoise blocks —
`WanTextEncoderStep` declares one too, and the codebase is inconsistent enough that no
rule can be stated yet (see #14469).

Co-Authored-By: Claude Opus 5 <noreply@anthropic.com>

---------

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: Steven Liu <59462357+stevhliu@users.noreply.github.com>

### [788e802](https://github.com/huggingface/diffusers/commit/788e80206a9722b133fc4907bbb8da2ba26d5181)

- **作者**: Vinh H. Pham
- **时间**: 2026-08-13T16:00:17Z
- **提交信息**: docs: document fused-kernel performance in Nunchaku Lite guide (#14458)

* docs: document fused-kernel performance in Nunchaku Lite guide

* Apply suggestions from code review

Co-authored-by: Steven Liu <59462357+stevhliu@users.noreply.github.com>

* Apply suggestion from @rootonchair

---------

Co-authored-by: Steven Liu <59462357+stevhliu@users.noreply.github.com>

### [6b3740b](https://github.com/huggingface/diffusers/commit/6b3740be8fff9e0f45ec651e821ab653484c80be)

- **作者**: Sayak Paul
- **时间**: 2026-08-13T10:18:18Z
- **提交信息**: feat: clean up peft related versioning voodoo. (#14463)

* feat: clean up peft related versioning voodoo.

* USE_PEFT_BACKEND usage

### [bb56997](https://github.com/huggingface/diffusers/commit/bb56997d4b7e87f0743f26a612f49ec4e7ce7213)

- **作者**: Wang, Yi
- **时间**: 2026-08-13T07:36:08Z
- **提交信息**: Fix AuraFlow model parallelism device mismatch and update XPU IP-Adap… (#14273)

* Fix AuraFlow model parallelism device mismatch and update XPU IP-Adapter expectations

Description

This PR fixes two test issues currently reflected in the working tree.

Changes

Fixed AuraFlow model parallelism in auraflow_transformer_2d.py.
Under device_map="auto", context_embedder can place encoder_hidden_states on a different device from the top-level register_tokens parameter. The forward pass now moves register_tokens to the projected encoder hidden states device and dtype before concatenation, avoiding cross-device torch.cat failures.

Updated XPU-specific expected slices in test_ip_adapter_stable_diffusion.py.
The IP-Adapter SD integration expectation now distinguishes XPU backend versions 3 and 5, since they produce slightly different deterministic slices.

Signed-off-by: Wang, Yi A <yi.a.wang@intel.com>

* update

Signed-off-by: Wang, Yi A <yi.a.wang@intel.com>

* update

Signed-off-by: Wang, Yi A <yi.a.wang@intel.com>

* fmt

Signed-off-by: Wang, Yi A <yi.a.wang@intel.com>

---------

Signed-off-by: Wang, Yi A <yi.a.wang@intel.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-08-14
**监控日期**: 2026-08-13
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 431
- **最后更新**: 2026-08-11T01:47:46Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-08-14
**监控日期**: 2026-08-13
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12934
- **最后更新**: 2026-08-13T22:18:23Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Zhongjie Duan

## AI分析总结

### 提交分析总结

**主要更新类型**：功能新增（支持Minimax H3文本嵌入）及配套的框架与示例更新。

**关键变更点**：
- 在`minimax-h3`模型中新增文本嵌入（text embeddings）支持，扩展了模型输入能力。
- 更新了`Diffusion-Templates`框架，以适配新功能，可能涉及接口或数据处理流程的调整。
- 更新了示例代码，帮助用户快速上手新特性。

**与项目方向的关系**：DiffSynth-Studio致力于提供多样化的扩散模型合成工具，支持多种模型和灵活的应用场景。本次更新直接丰富了`minimax-h3`的输入模态，使其能处理更复杂的文本条件生成任务，符合项目“多模型、多模态支持”的核心定位。

**对项目的影响与潜在意义**：
- 提升`minimax-h3`的实用性和竞争力，吸引更多需要文本引导生成的用户。
- 框架更新可能为后续其他模型添加类似功能奠定基础，增强项目可扩展性。
- 示例更新降低了新用户的上手门槛，有助于社区推广。

**值得关注的技术点**：
- 文本嵌入的集成方式（如是否使用预训练编码器、嵌入维度对齐等），可能影响生成质量。
- 框架更新是否引入了新的抽象层或API变化，对现有用户兼容性需留意。

**对项目发展的影响**：结合README中项目强调的“灵活、易用的扩散模型工具”目标，本次提交通过增强模型输入能力，进一步巩固了项目在文本到图像/视频生成领域的工具链完整性。持续的功能迭代和框架优化，有助于保持项目在Trendshift等榜单上的活跃度，并吸引更多开发者贡献，形成良性生态循环。

## 详细提交记录

### [b134eb7](https://github.com/modelscope/DiffSynth-Studio/commit/b134eb70739980d97ae21dd93c017a0a5b93c963)

- **作者**: Zhongjie Duan
- **时间**: 2026-08-13T14:06:33Z
- **提交信息**: Support Minimax H3 text embeddings (#1590)

* support using text embeddings in minimax-h3

* update Diffusion-Templates framework

* update examples

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-08-14
**监控日期**: 2026-08-13
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 31755
- **最后更新**: 2026-08-13T22:26:30Z

## 提交统计

- **昨日提交总数**: 37
- **提交者数量**: 28
- **主要提交者**: Khoa Pham, Xinyi Song, jthomson04

## AI分析总结

# SGLang 昨日提交分析报告

## 一、主要更新类型

本次提交涵盖**性能优化**（约40%）、**Bug修复**（约25%）、**功能新增**（约15%）、**CI/测试改进**（约15%）及**文档与重构**（约5%），整体以性能优化和稳定性提升为核心。

## 二、关键变更点与项目方向

1. **Diffusion模型深度优化**：多提交针对FLUX.2、HunyuanVideo、Wan2.2-TI2V等模型进行算子融合（QKNorm、AdaLN、SwiGLU、QKV packing），实现13%左右的推理加速且保持bit-exact精度，体现项目对生成模型推理效率的持续投入。

2. **PD（Prefill-Decode）分离架构完善**：修复NIXL bootstrap超时、固定NCCL rendezvous端口、禁用P worker的prefill CUDA graph，提升分离式推理的稳定性，这是SGLang核心架构方向。

3. **AMD ROCm平台适配**：MTP draft-extend CUDA graph支持、GatedDeltaNet Triton kernel融合、CI调整，显示对多硬件平台的支持力度。

4. **新模型支持**：新增LongCat-Image、MiniMax-H3缓存修复、DeepSeek-V4混合HostPoolGroup支持，保持模型生态领先。

## 三、项目影响与意义

- **推理性能显著提升**：Wan2.2-TI2V在H100/H200上分别获得13.1%/12.6%的denoise加速，Diffusion系列融合优化使eager模式超越compile，降低用户使用门槛。
- **稳定性增强**：多项CI修复和超时配置解决flaky测试问题，提升分布式场景可靠性。
- **启动优化**：checkpoint staging与CUDA graph捕获重叠，缩短模型启动时间，改善用户体验。

## 四、值得关注的技术点

1. **Cache事件合并**（#31479）：通过coalesce减少KV cache事件开销，对长序列场景收益明显。
2. **环境变量注册表整理**（#34730）：系统化管理配置项，提升可维护性。
3. **DSA indexer fp8量化kernel占用率调优**：面向特定硬件的精细性能优化。
4. **CPU AMX支持auto-round量化**：扩展Intel平台能力。
5. **错误响应统一重构**：提升API一致性和可调试性。

## 五、对项目发展的影响

SGLang正从“高性能LLM推理引擎”向**全模态、多硬件、生产级平台**演进。Diffusion系列优化巩固其在生成模型推理的领先地位；PD架构持续完善支撑超长上下文和分布式场景；AMD/CPU适配扩大硬件覆盖；新模型快速跟进保持生态竞争力。整体呈现“性能极致优化+架构稳健演进+生态广度扩展”的三线并行发展态势，符合其作为下一代AI推理基础设施的定位。

## 详细提交记录

### [f3beb2c](https://github.com/sgl-project/sglang/commit/f3beb2c52903ad77202a1e307017996d1ada22a1)

- **作者**: Khoa Pham
- **时间**: 2026-08-13T22:26:21Z
- **提交信息**: [CI] Disable the prefill CUDA graph on the P worker of test_kimi_linear_pd_dcp4 (#34779)

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [81fe452](https://github.com/sgl-project/sglang/commit/81fe452810d9256b5d307cad3a3e261c70170591)

- **作者**: Khoa Pham
- **时间**: 2026-08-13T22:06:02Z
- **提交信息**: [DCP] Share one pack kernel between both a2a backends (#34651)

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [8bbca87](https://github.com/sgl-project/sglang/commit/8bbca87780d1a075dd54d1a5ca357760a4904bbe)

- **作者**: Lianmin Zheng
- **时间**: 2026-08-13T21:25:37Z
- **提交信息**: [Core] Organize environment variable registry (#34730)

### [652a270](https://github.com/sgl-project/sglang/commit/652a2709d180d08d34b1e280d5cd84b71886c3bd)

- **作者**: Khoa Pham
- **时间**: 2026-08-13T20:51:57Z
- **提交信息**: [Docs] Add decode context parallelism to advanced features (#34654)

Co-authored-by: Cursor <cursoragent@cursor.com>

### [9034390](https://github.com/sgl-project/sglang/commit/903439044a58a61965449804ec5d21cf45a061e9)

- **作者**: jthomson04
- **时间**: 2026-08-13T20:36:53Z
- **提交信息**: perf(kv-events): coalesce cache events (#31479)

### [8554d9a](https://github.com/sgl-project/sglang/commit/8554d9a5bc9d38d38d9cb8a76d3bdd29ad0fcdf9)

- **作者**: Liangsheng Yin
- **时间**: 2026-08-13T20:30:33Z
- **提交信息**: [Fix] Carry the backend on Kimi-K3 deferred preprocessing configs (#34766)

### [8ad04a9](https://github.com/sgl-project/sglang/commit/8ad04a9bee38a6e80ddde5085d7733f08226bb93)

- **作者**: Lukas Humbel
- **时间**: 2026-08-13T20:04:13Z
- **提交信息**: docs(nixl): document OBJ throughput target (#30405)

### [29b0672](https://github.com/sgl-project/sglang/commit/29b067245b8e558365d38d1132186a7260f6c222)

- **作者**: kangwangamd
- **时间**: 2026-08-13T19:48:58Z
- **提交信息**: [AMD] CI: drop the spaces from SGL_EVAL_SPEC (fixes ROCm 7.2 stage-a sgl-eval install) (#34689)

Co-authored-by: Bingxu Chen <bingxche@amd.com>

### [96db53e](https://github.com/sgl-project/sglang/commit/96db53ec7087d6628821073b3e4e8aea709e65c0)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-08-13T19:47:03Z
- **提交信息**: [CI] Fix test_resolution_is_reproducible after cuda_ipc became opt-in (#34746)

### [6b94d39](https://github.com/sgl-project/sglang/commit/6b94d39f13086d4e22b647db6f936e6299be789f)

- **作者**: Han Yu
- **时间**: 2026-08-13T19:26:25Z
- **提交信息**: [Model Loading] Overlap checkpoint staging with CUDA graph capture during startup (#32017)

Co-authored-by: Wenhui Zhu <wzhu59@asu.edu>
Co-authored-by: Alex Nails <alex.nails@radixark.ai>

### [0772e79](https://github.com/sgl-project/sglang/commit/0772e79ee7192074cf55cf0fb0ee0c8971e4d8a7)

- **作者**: Shangming Cai
- **时间**: 2026-08-13T17:44:20Z
- **提交信息**: [CI][PD] Pin nccl rendezvous port per side to fix flaky disaggregation tests (#34755)

### [a82f8e1](https://github.com/sgl-project/sglang/commit/a82f8e1777d52312eefc161d1df8fd2db5f11169)

- **作者**: jambow0320
- **时间**: 2026-08-13T17:08:09Z
- **提交信息**: [PD] Add the missing Prefill bootstrap timeout for NIXL (#34692)

### [69a31ce](https://github.com/sgl-project/sglang/commit/69a31ce342e7ce5a4c230a3d2c728f0eed2e696f)

- **作者**: E
- **时间**: 2026-08-13T16:39:58Z
- **提交信息**: fix: make Cache-DiT actually cache on MiniMax-H3 (#33827)

Signed-off-by: YZLi <yuanli@nvidia.com>
Signed-off-by: yunch <yunch@nvidia.com>
Co-authored-by: YZLi <yuanli@nvidia.com>
Co-authored-by: Mick <mickjagger19@icloud.com>
Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

### [c255fbc](https://github.com/sgl-project/sglang/commit/c255fbc4fed05a4f8ffce64e88c682a3edb70088)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-08-13T16:37:49Z
- **提交信息**: [Diffusion] Add @triple-mu as a code owner (#34748)

### [ea7a6e0](https://github.com/sgl-project/sglang/commit/ea7a6e0e997d00708a8f6f4502225f50578974ef)

- **作者**: triple-mu
- **时间**: 2026-08-13T15:24:00Z
- **提交信息**: fix(diffusion): unshard FSDP root group for custom encoder entry points (#34575)

### [ebca0bb](https://github.com/sgl-project/sglang/commit/ebca0bbde46dc5f2486774bc2ea1241a7ac31250)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-08-13T15:23:21Z
- **提交信息**: [Diffusion][ERNIE] Fuse QKNorm with full-width RoPE (#34620)

### [82f7afb](https://github.com/sgl-project/sglang/commit/82f7afb881064250739747113227186d553464e8)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-08-13T15:20:55Z
- **提交信息**: [Diffusion] Make auto residency decisions component-scoped (#34615)

### [07821e9](https://github.com/sgl-project/sglang/commit/07821e9d568d2732575ab769b079ec59d99265ba)

- **作者**: Michael
- **时间**: 2026-08-13T14:22:42Z
- **提交信息**: [AMD][CI] Stop scheduling Grok-1 and Grok-2 on MI30x (#34643)

Co-authored-by: Cursor Agent <cursoragent@cursor.com>
Co-authored-by: Michael <michaelzhang-ai@users.noreply.github.com>

### [c114267](https://github.com/sgl-project/sglang/commit/c1142677a801cdfa9eb9826a8d601032d0264150)

- **作者**: Yuhao Yang
- **时间**: 2026-08-13T13:35:15Z
- **提交信息**: [do not merge] add new cookbooks (#34658)

Co-authored-by: Jianfei Wang <jianfei.wangg@outlook.com>
Co-authored-by: Jianfei Wang <905787410@qq.com>

### [74c0322](https://github.com/sgl-project/sglang/commit/74c032234201aa0ed64b7a58c738d9ea393e319c)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-08-13T11:55:53Z
- **提交信息**: [Diffusion][FLUX.2] Fuse eager AdaLN and packed SwiGLU (#34616)

### [3c1791a](https://github.com/sgl-project/sglang/commit/3c1791a7df4d29bb4f0a332b51a549ed2b380e36)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-08-13T11:54:00Z
- **提交信息**: [Diffusion][HunyuanVideo] Fuse eager QKV packing and high-quality QKNorm (#34617)

### [993e24d](https://github.com/sgl-project/sglang/commit/993e24df750d2730d673350d05569efdeb778102)

- **作者**: triple-mu
- **时间**: 2026-08-13T11:49:56Z
- **提交信息**: [diffusion] Add --dit-layerwise-residency-policy for strided DiT residency (#34534)

Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

### [b764194](https://github.com/sgl-project/sglang/commit/b764194e810f9ca7ad2c21e4d307d86158acfd12)

- **作者**: Liu Zhenlong
- **时间**: 2026-08-13T11:48:26Z
- **提交信息**: [diffusion] model: support LongCat-Image (#23274)

Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

### [eea2e5d](https://github.com/sgl-project/sglang/commit/eea2e5d6e5eb19bddddd9cc7e687fbbaa7397a7c)

- **作者**: Estrella-xx
- **时间**: 2026-08-13T11:15:47Z
- **提交信息**: Optimize delayed sample and mrope position computation (#32637)

### [9c0d4cb](https://github.com/sgl-project/sglang/commit/9c0d4cba3f8ff1f9b76ab6e426e84467127a38f3)

- **作者**: Baizhou Zhang
- **时间**: 2026-08-13T10:20:50Z
- **提交信息**: [CI] Split Kimi K2.5 performance batches by config (#34669)

### [a23670d](https://github.com/sgl-project/sglang/commit/a23670ddbf89678a53230ceb2cc5ed75236c4d85)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-08-13T09:26:46Z
- **提交信息**: [diffusion] Wan2.2-TI2V: fuse per-token adaLN table add into contiguous slices + hoist rope cache (denoise -13.1% H100 / -12.6% H200, bit-exact; eager beats compile) (#34584)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [ba23846](https://github.com/sgl-project/sglang/commit/ba23846ccfd5e35e87e105b3733680904b43d463)

- **作者**: Rain Jiang
- **时间**: 2026-08-13T09:13:43Z
- **提交信息**: move the PD bootstrap registry under api_server::disaggregation (#33895)

### [34206c0](https://github.com/sgl-project/sglang/commit/34206c00175a56300040541901d561f465399cc0)

- **作者**: Thomas Wang
- **时间**: 2026-08-13T09:00:45Z
- **提交信息**: [AMD] Run V4 MTP target-verify through the decode kernel (#34597)

Co-authored-by: RolaoDenthu <xinyis10@illinois.edu>
Co-authored-by: 1am9trash <1am9trash>
Co-authored-by: kk <43161300+kkHuang-amd@users.noreply.github.com>

### [fd1e04d](https://github.com/sgl-project/sglang/commit/fd1e04d95269a406c70446b24e5dde989b092933)

- **作者**: Rain Jiang
- **时间**: 2026-08-13T08:30:29Z
- **提交信息**: refactor error responses into shared utils::response helpers (#33894)

### [dbebc1d](https://github.com/sgl-project/sglang/commit/dbebc1deb42b00befa3d0de67265d7003994c1ad)

- **作者**: Rainchar9119
- **时间**: 2026-08-13T08:15:27Z
- **提交信息**:  [Perf] Occupancy tuning for DSA indexer fp8-quant Q kernel (#32755)

Signed-off-by: Rainchar9119 <1134601163@qq.com>

### [fad376d](https://github.com/sgl-project/sglang/commit/fad376d3ee5807cd5412a1ebb1e24b53dad99dff)

- **作者**: Weiwei
- **时间**: 2026-08-13T07:50:59Z
- **提交信息**: [CPU][QUANT] add amx cpu support for auto-round (#29593)

Signed-off-by: WeiweiZhang1 <weiwei1.zhang@intel.com>
Signed-off-by: sys-lpot-val <sys_lpot_val@intel.com>
Co-authored-by: sys-lpot-val <sys_lpot_val@intel.com>
Co-authored-by: Weiwei Zhang <WeiweiZhang1@users.noreply.github.com>
Co-authored-by: Ma Mingfei <mingfei.ma@intel.com>

### [c034120](https://github.com/sgl-project/sglang/commit/c034120cb88694e2b84c77b591483b942c799ef4)

- **作者**: Xinyi Song
- **时间**: 2026-08-13T07:50:19Z
- **提交信息**: [AMD] Enable draft-extend CUDA graph and reduce bubble for MTP (#29202)

Co-authored-by: Thomas Wang <thomawan@amd.com>

### [a34f812](https://github.com/sgl-project/sglang/commit/a34f81251f78bab5b818144649a45c6bd51a2665)

- **作者**: AMD-yanfeiwang
- **时间**: 2026-08-13T07:40:07Z
- **提交信息**: fix(hicache/umbp): support DeepSeek-V4 hybrid HostPoolGroup (multi-po… (#30762)

Co-authored-by: Zhangheng <hzh0425@apache.org>

### [b7f87a2](https://github.com/sgl-project/sglang/commit/b7f87a2513c2761952ca018c7b98b144cecd3b09)

- **作者**: jacky.cheng
- **时间**: 2026-08-13T07:18:35Z
- **提交信息**: [AMD][Perf] Fuse GatedDeltaNet QKVZBA split/reshape/cat into a single Triton kernel for Qwen3.5-architecture MoE on HIP (#34421)

### [5a5c3d3](https://github.com/sgl-project/sglang/commit/5a5c3d309ba82ff60c02ef69e178d8cc74b78843)

- **作者**: Ke Bao
- **时间**: 2026-08-13T07:16:05Z
- **提交信息**: Drop the mmlu case from the unified radix cache kit (#34667)

### [969921b](https://github.com/sgl-project/sglang/commit/969921b32d30af7ccf277d0dfe72bd913228e527)

- **作者**: Mick
- **时间**: 2026-08-13T07:12:26Z
- **提交信息**: [diffusion] chore: track minimax-h3 in the nightly diffusion benchmark (#34655)

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [3f6ef01](https://github.com/sgl-project/sglang/commit/3f6ef01322caddab11748e630eda3d9ae1920da8)

- **作者**: Xinguo Zhu
- **时间**: 2026-08-13T07:04:16Z
- **提交信息**: Optimize MiniMax-M2.7 on CPU (#31956)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-08-14
**监控日期**: 2026-08-13
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1247
- **最后更新**: 2026-08-13T15:22:06Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-08-14
**监控日期**: 2026-08-13
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 88990
- **最后更新**: 2026-08-13T22:37:43Z

## 提交统计

- **昨日提交总数**: 39
- **提交者数量**: 35
- **主要提交者**: Vineeta Tiwari, TomerBN-Nvidia, Misha Goin

## AI分析总结

# vLLM 昨日提交分析报告

## 一、主要更新类型

本批39个提交涵盖多种类型：**Bug修复**（约14个，占比最高）、**新功能/特性**（约8个）、**平台适配**（ROCm/XPU/CPU相关约7个）、**文档与CI改进**（约5个）、**代码重构与清理**（约4个）、**安全修复**（1个）。

## 二、关键变更点与项目方向

1. **Kimi-K3模型深度优化**：多个提交围绕Kimi-K3展开，包括GEMM-RS序列并行、ROCm V2模型运行器启用、预填充流水线停顿消除、fused MLA内核CI修复等，表明vLLM正加速对前沿MoE模型的支持。

2. **ROCm/AMD平台持续强化**：AITER MLA解码元数据修复、tilelang延迟导入、Kimi-K3 ROCm支持、LLM生命周期测试等，体现vLLM对AMD生态的投入。

3. **新模型与架构支持**：Ling混合MXFP4路由专家、Gemma4视觉塔LoRA、NanoNemotronVL音频解码安全限制、Dots3 NOTE序列并行禁用等，持续扩展模型覆盖。

4. **推理正确性与安全**：xgrammar结构化输出停止token掩码、Anthropic并行工具调用保留、音频解码时长限制等，提升服务可靠性和安全性。

## 三、项目影响与潜在意义

- **多硬件平台战略加速**：ROCm、XPU、CPU的持续适配使vLLM从NVIDIA独占走向真正的硬件无关，扩大用户基础。
- **前沿模型快速跟进**：对Kimi-K3、Ling等最新模型的及时支持，巩固vLLM作为“最快跟进新模型”的推理框架地位。
- **工程化成熟度提升**：CI修复、文档更新、代码清理（如删除死代码、统一权重绑定）表明项目从快速迭代转向工程规范化。

## 四、值得关注的技术点

1. **torch.compile兼容性修复**（mrope.py）：解决PyTorch 2.13下的编译问题，对生产环境性能优化至关重要。
2. **FlashInfer SM12x prefill修复**：涉及sink缓存处理，直接影响长上下文场景的推理质量。
3. **Mask Replay特性**：作为新功能提交，可能与路由/缓存机制相关，值得关注其设计思路。
4. **硬件无关模型定义（1/N）**：通过HF transformer后端实现硬件无关模型定义，这是架构层面的重要演进方向。
5. **自定义编码器缓存管理器配置**：从VllmConfig配置，增强多模态模型的灵活性。

## 五、对项目发展的影响

结合README中“Easy, fast, and cheap LLM serving for everyone”的定位，本批提交体现了vLLM的三大发展方向：**一是通过多平台适配降低使用门槛**（ROCm/XPU/CPU），**二是通过性能优化维持速度优势**（Kimi-K3、FlashInfer等），**三是通过架构演进提升可维护性**（硬件无关定义、代码标准化）。安全修复和结构化输出改进则强化了企业级应用的可靠性。整体来看，vLLM正从“NVIDIA GPU上的高性能推理引擎”向“全平台、全模型、生产级”的通用LLM服务基础设施演进，这批提交是该战略的典型体现。

## 详细提交记录

### [71b0da7](https://github.com/vllm-project/vllm/commit/71b0da7c4ecca10a9f11f535fc370cf988ce12d7)

- **作者**: bastefaniak
- **时间**: 2026-08-13T22:08:40Z
- **提交信息**: [Bugfix] Fix .../mrope.py::apply_interleaved_rope() when torch.compile is used in torch==2.13 (#52005)

Signed-off-by: Bartosz Stefaniak <bstefaniak@nvidia.com>

### [51def78](https://github.com/vllm-project/vllm/commit/51def7848a68397213f83f90893cafb275ff4d3f)

- **作者**: Benjamin Chislett
- **时间**: 2026-08-13T22:08:07Z
- **提交信息**: [Bugfix] Reapply 50869 (#52223)

Signed-off-by: Benjamin Chislett <bchislett@nvidia.com>

### [6355051](https://github.com/vllm-project/vllm/commit/63550515b498261c820a1540be86a96e50802725)

- **作者**: Stan Wozniak
- **时间**: 2026-08-13T21:51:24Z
- **提交信息**: [Bugfix] Correct prompt lengths for timed_traces benchmark (#45423)

Signed-off-by: Stanislaw Wozniak <stw@zurich.ibm.com>
Co-authored-by: Thomas Parnell <tpa@zurich.ibm.com>

### [b652ded](https://github.com/vllm-project/vllm/commit/b652dedd0c505b6d300788f9b4f6c494d2d12d5c)

- **作者**: Andrii Skliar
- **时间**: 2026-08-13T21:25:09Z
- **提交信息**: [Attention] Fix FlashInfer SM12x prefill with sinks (#52148)

Signed-off-by: Andrii Skliar <askliar@nvidia.com>
Co-authored-by: Andrii Skliar <askliar@nvidia.com>
Co-authored-by: Michael Goin <mgoin64@gmail.com>

### [2e2ffd1](https://github.com/vllm-project/vllm/commit/2e2ffd104bd0b12e36704c957d09cda9488d5773)

- **作者**: Misha Goin
- **时间**: 2026-08-13T20:56:36Z
- **提交信息**: [CI Failure] Fix CUDA wheel build for the Kimi K3 fused MLA kernel (#52210)

### [73b8394](https://github.com/vllm-project/vllm/commit/73b83949f76bfb806f3beca1be11b1dfb120145a)

- **作者**: wangxiyuan
- **时间**: 2026-08-13T19:25:07Z
- **提交信息**: [Platform] Add check_runner_kv_caches_multi_layer (#51633)

Signed-off-by: wangxiyuan <wangxiyuan1007@gmail.com>

### [11c3fa4](https://github.com/vllm-project/vllm/commit/11c3fa4adc8105bd1dbad888d6df81617ee7c8fc)

- **作者**: stefankoncarevic
- **时间**: 2026-08-13T18:35:00Z
- **提交信息**: [Bugfix][ROCm][CI] Give the AITER MLA decode metadata stub its MLA dims (#52139)

Signed-off-by: Stefan Koncarevic <Stefan.Koncarevic@amd.com>

### [c5b7c06](https://github.com/vllm-project/vllm/commit/c5b7c069a43e88dc1fb67e91286887cc664e2af9)

- **作者**: fxmarty-amd
- **时间**: 2026-08-13T18:12:40Z
- **提交信息**: [ROCm] Defer `tilelang` import through its import `from vllm.tilelang_utils import tilelang` and relaxed `has_tilelang` (#51159)

Signed-off-by: Felix Marty <Felix.Marty@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [e6b2a8a](https://github.com/vllm-project/vllm/commit/e6b2a8ad5eb1757b211475cdd57fdf1f37e94331)

- **作者**: yzong-rh
- **时间**: 2026-08-13T18:07:59Z
- **提交信息**: [Bugfix][Structured Output] Mask request stop tokens in xgrammar until grammar terminates (#50595)

Signed-off-by: Yifan Zong <yzong@redhat.com>

### [48825ac](https://github.com/vllm-project/vllm/commit/48825acc232f06380f15124b9a1ea7076939e88c)

- **作者**: fxmarty-amd
- **时间**: 2026-08-13T17:58:31Z
- **提交信息**: [Quantization] Remove dead `QuantizationConfig.is_mxfp4_quant` (#51793)

Signed-off-by: Felix Marty <Felix.Marty@amd.com>

### [b96bcd0](https://github.com/vllm-project/vllm/commit/b96bcd0b474fe469c42423f6a4e7de8ba16baa01)

- **作者**: Andreas Karatzas
- **时间**: 2026-08-13T17:24:02Z
- **提交信息**: [ROCm][CI] Solidify entrypoint LLM lifecycle (#51280)

Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>
Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [69d4c3a](https://github.com/vllm-project/vllm/commit/69d4c3a06bf8d087455544db8cea570721eca415)

- **作者**: Cyrus Leung
- **时间**: 2026-08-13T16:40:38Z
- **提交信息**: Auto-ping Cohere on related issues (#52091)

Signed-off-by: DarkLight1337 <tlleungac@connect.ust.hk>

### [83d4c61](https://github.com/vllm-project/vllm/commit/83d4c6196ad90f98515c6be113cb2e957b60a832)

- **作者**: Nick Iusiumbeli
- **时间**: 2026-08-13T16:22:50Z
- **提交信息**: [Bugfix] Declare SupportsEagle3 on KimiLinearForCausalLM (#52171)

Signed-off-by: Nick Iusiumbeli <nickuspro@gmail.com>

### [b245d8e](https://github.com/vllm-project/vllm/commit/b245d8e73f67f1fffed3b46b6152078dc1683fe6)

- **作者**: Harry Mellor
- **时间**: 2026-08-13T16:21:55Z
- **提交信息**: Apply logit softcapping in Transformers modelling backend (#52173)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [6014f9e](https://github.com/vllm-project/vllm/commit/6014f9e67291ea96548e263b8784a33a3f055954)

- **作者**: Thien Tran
- **时间**: 2026-08-13T16:02:28Z
- **提交信息**: [Kimi-K3] Add GEMM-RS for sequence parallelism (#52079)

Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>

### [96acd47](https://github.com/vllm-project/vllm/commit/96acd473a7f1b4dd5a8e09752183617d3b82089e)

- **作者**: Qiming Zhang
- **时间**: 2026-08-13T15:44:03Z
- **提交信息**: [Bugfix][MiniCPM-V] Fix AssertionError in get_dummy_mm_data when passing VideoDummyOptions to _get_dummy_images (#52122)

Signed-off-by: mayuyuace <qiming1.zhang@intel.com>

### [64ca614](https://github.com/vllm-project/vllm/commit/64ca614fe49bfce92b0f5eb69625021297a7e003)

- **作者**: Ali Jaseem
- **时间**: 2026-08-13T15:12:26Z
- **提交信息**: [Bugfix] Fix `--data-parallel-start-rank 0` being treated as unset in `create_engine_config` (#47692)

Signed-off-by: Syed Ali Jaseem <syedali0057@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [80d6d55](https://github.com/vllm-project/vllm/commit/80d6d557f307448fdad46995b5e237817b31144e)

- **作者**: Harry Mellor
- **时间**: 2026-08-13T15:10:09Z
- **提交信息**: Standardise weight tying on `ParallelLMHead.tie_weights` (#52147)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [7553aac](https://github.com/vllm-project/vllm/commit/7553aac77b678d58f6f8034b4f25300933f0bd84)

- **作者**: aoshen02
- **时间**: 2026-08-13T15:09:00Z
- **提交信息**: [Frontend] Add routed-experts prompt offset (#51906)

Signed-off-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [f3c1638](https://github.com/vllm-project/vllm/commit/f3c1638927eee6ea31ad5a66e86e5b7ed6ebaa02)

- **作者**: vllmellm
- **时间**: 2026-08-13T14:34:53Z
- **提交信息**: [ROCm] Enable V2 model runner for Kimi-K3 on ROCm (#51653)

Signed-off-by: vllmellm <vllm.ellm@embeddedllm.com>

### [2d24355](https://github.com/vllm-project/vllm/commit/2d24355eb87b716fc1169e66731dc0386ed1a3a2)

- **作者**: Michael Goin
- **时间**: 2026-08-13T14:19:08Z
- **提交信息**: [Bugfix] Fix packed GDN decode launch for large batch-head grids (#52030)

Signed-off-by: mgoin <mgoin64@gmail.com>

### [170592a](https://github.com/vllm-project/vllm/commit/170592a931d92572f65ee808b3b03e6eed2f54a3)

- **作者**: 范裕达
- **时间**: 2026-08-13T14:13:00Z
- **提交信息**: [Bugfix] Disable sequence parallelism for Dots3 NOTE (#52172)

Signed-off-by: KurodaKanbei <mistergalahad@gmail.com>

### [95c9144](https://github.com/vllm-project/vllm/commit/95c9144424060a3ec11090050318a5e702a70be2)

- **作者**: linitra24
- **时间**: 2026-08-13T14:07:43Z
- **提交信息**: [LoRA][Gemma4] Support vision tower LoRA (#42662)

Signed-off-by: bk-201 <joy25810@foxmail.com>
Signed-off-by: linitra24 <Joy25810@foxmail.com>
Signed-off-by: linitra24 <joy25810@gmail.com>
Co-authored-by: Jee Jee Li <pandaleefree@gmail.com>
Co-authored-by: linitra24 <joy25810@gmail.com>

### [8e1131e](https://github.com/vllm-project/vllm/commit/8e1131e1d1d47ae06acecb820b4c4a734697c0b2)

- **作者**: zexplorerhj
- **时间**: 2026-08-13T13:46:53Z
- **提交信息**: [Model] [Quantization] Add Ling hybrid MXFP4 routed experts support (#52114)

Signed-off-by: zexplorerhj <zhjoneson@163.com>

### [152c913](https://github.com/vllm-project/vllm/commit/152c913a6309305820a98745ae53d9e39b9200fc)

- **作者**: yang rui
- **时间**: 2026-08-13T13:11:51Z
- **提交信息**: [Frontend] Log output token IDs at DEBUG level (#52098)

Signed-off-by: ruirui6946 <142162413+ruirui6946@users.noreply.github.com>

### [015660d](https://github.com/vllm-project/vllm/commit/015660da91a6710465d2a24eec3394c178fb7181)

- **作者**: Vineeta Tiwari
- **时间**: 2026-08-13T12:58:45Z
- **提交信息**: [Misc] Add missing return type annotations in outputs.py (#52145)

Signed-off-by: Vineeta Tiwari <vineeta.tiwari2@ibm.com>
Co-authored-by: Vineeta Tiwari <vineeta.tiwari2@ibm.com>

### [c4e9692](https://github.com/vllm-project/vllm/commit/c4e969294ecab9ffefb995b734303f13f62b723f)

- **作者**: pmanczak
- **时间**: 2026-08-13T12:36:55Z
- **提交信息**: [XPU] Add tuned Mamba SSU configs for Intel Arc Pro B70 (#50534)

Signed-off-by: pmanczak <pawel.manczak@intel.com>

### [d0ae25e](https://github.com/vllm-project/vllm/commit/d0ae25e2f283c96e4c5c6f9000f945209f871a4f)

- **作者**: Taneem Ibrahim
- **时间**: 2026-08-13T12:25:55Z
- **提交信息**: [Bugfix] Preserve Anthropic disable_parallel_tool_use (#52021)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [5fee0a8](https://github.com/vllm-project/vllm/commit/5fee0a872dc31dd3476d61bb72b782b2d9d47492)

- **作者**: JasonCohere
- **时间**: 2026-08-13T12:05:36Z
- **提交信息**: chore: Upstream Cohere parser fixes + tests (#51998)

Signed-off-by: Jason Ozuzu <jasonozuzu@cohere.com>

### [443fa5a](https://github.com/vllm-project/vllm/commit/443fa5aca0253fd6b27ae94bd4b232418612ac51)

- **作者**: QWERQWERQWE86
- **时间**: 2026-08-13T10:56:27Z
- **提交信息**: [Doc] Fix stale rejection_sample_method and synthetic_acceptance_rate (#51611)

Signed-off-by: qwerqwerqwe8688-jpg <xuuuuu2021@163.com>

### [37c3bdf](https://github.com/vllm-project/vllm/commit/37c3bdf5a7ef379ac4cc9678a46b6bc26479be12)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-08-13T10:31:55Z
- **提交信息**: fix(security): enforce audio decode duration limit in NanoNemotronVL (#50221)

Signed-off-by: jperezde <jperezde@redhat.com>

### [b8baa31](https://github.com/vllm-project/vllm/commit/b8baa31a28650b6f3189bc7fcb051e1360c9270c)

- **作者**: Thomas Ortner
- **时间**: 2026-08-13T10:21:50Z
- **提交信息**: Hardware-agnostic model definition via HF transformer backend (1/N) (#49458)

Signed-off-by: Thomas Ortner <boh@zurich.ibm.com>

### [903da60](https://github.com/vllm-project/vllm/commit/903da602f3868a10aa418ba5513c280dfa7ef635)

- **作者**: Harry Mellor
- **时间**: 2026-08-13T09:32:14Z
- **提交信息**: [Docs] Fix `WhisperEncoderLayer.forward` docstring in `dots3_note` (#52134)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [1c3633a](https://github.com/vllm-project/vllm/commit/1c3633acafd6bbde1f3636cee9799e3ab0879d13)

- **作者**: Li, Jiang
- **时间**: 2026-08-13T09:17:00Z
- **提交信息**: [CI/Build][CPU] Shrink triton-cpu-build layer by dropping build artifacts (#52127)

Signed-off-by: jiang1.li <jiang1.li@intel.com>

### [f962616](https://github.com/vllm-project/vllm/commit/f96261637c05d372e077a8aeb6df03cda7f5b354)

- **作者**: kliuae
- **时间**: 2026-08-13T09:11:45Z
- **提交信息**: [ROCm][Perf] Kimi-K3 Remove prefill pipeline stall in chunk KDA (#51862)

Signed-off-by: kliuae <kuanfu.liu@embeddedllm.com>

### [50ba4bc](https://github.com/vllm-project/vllm/commit/50ba4bc6b2cacd70c4711a1904dd7ad9740a578b)

- **作者**: vx120
- **时间**: 2026-08-13T08:44:31Z
- **提交信息**: [Feature] Mask Replay (#49577)

Signed-off-by: vx120 <893600387@qq.com>
Signed-off-by: vx120 <57470515+vx120@users.noreply.github.com>
Signed-off-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Claude Opus 4.6 (1M context) <noreply@anthropic.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [10bcad2](https://github.com/vllm-project/vllm/commit/10bcad25233c97929595122962c0c449debaf507)

- **作者**: Cyrus Leung
- **时间**: 2026-08-13T08:43:07Z
- **提交信息**: Update CODEOWNERS (#52123)

Signed-off-by: DarkLight1337 <tlleungac@connect.ust.hk>

### [7bbbf7c](https://github.com/vllm-project/vllm/commit/7bbbf7c8e5040f7ebd374e8cbc657e01af1136dd)

- **作者**: hotTea
- **时间**: 2026-08-13T08:08:01Z
- **提交信息**: [Core] Configure custom encoder cache managers from VllmConfig (#51251)

Signed-off-by: hotTea <958436561@qq.com>
Signed-off-by: HMCCMH <chenminghaoscu@163.com>
Co-authored-by: HMCCMH <chenminghaoscu@163.com>

### [399f974](https://github.com/vllm-project/vllm/commit/399f97424e61ea918135bd80176491646cb69d17)

- **作者**: TomerBN-Nvidia
- **时间**: 2026-08-13T07:18:08Z
- **提交信息**: [Bugfix][R3] Size monolithic routing replay buffer for DP (#50874)

Signed-off-by: tbarnatan <tbarnatan@nvidia.com>
Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: zjy0516 <riverclouds.zhu@qq.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-08-14
**监控日期**: 2026-08-13
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 6095
- **最后更新**: 2026-08-13T22:12:05Z

## 提交统计

- **昨日提交总数**: 7
- **提交者数量**: 7
- **主要提交者**: Weiming Liao, Mu GuanLin, Canlin Guo

## AI分析总结

## 提交分析总结

### 1. 主要更新类型

本次提交涵盖**功能新增**（TTS模型接入、视频生成流水线）、**Bug修复**（音频模型解码问题、TTS参数修正）、**重构**（移除内部配置路径）、**依赖升级**（NPU版本更新）和**文档更新**（社区文档刷新）五类变更，整体呈现多维度推进态势。

### 2. 关键变更点与项目方向的关系

- **新增dots.tts连续AR 48kHz TTS模型**：扩展了项目的文本转语音能力，与vllm-omni“全模态模型服务”的定位高度契合，填补了高质量TTS模型的空白。
- **LTX标准两阶段流水线**：为视频生成任务引入更灵活的流水线架构，强化了项目在视频模态的服务能力。
- **Higgs-Audio-V3禁用XQA解码**：修复了音频模型在特定解码路径下的潜在问题，保障了音频模态的推理稳定性。
- **移除stage_configs_path内部管道**：简化了多阶段模型的配置管理，属于架构层面的清理优化，为后续扩展奠定基础。

### 3. 对项目的影响与潜在意义

TTS模型的加入使vllm-omni在语音合成领域获得实际落地能力，配合已有的音频理解模型，有望形成完整的语音交互闭环。LTX两阶段流水线则提升了视频生成任务的灵活性和可扩展性。Bug修复和重构虽不显眼，但直接关系到生产环境的稳定性和可维护性，是项目走向成熟的重要标志。

### 4. 值得关注的技术点

- **连续AR（自回归）48kHz TTS**：高采样率连续自回归架构是当前TTS领域的前沿方向，该实现可能带来更自然的语音合成效果。
- **XQA解码禁用**：XQA（交叉量化注意力）在音频模型上的适配问题值得关注，可能涉及注意力机制在音频特征上的数值稳定性。
- **两阶段流水线设计**：LTX采用标准化的两阶段方案，为视频生成中的“结构先验+细节增强”范式提供了参考实现。
- **NPU升级至v0.27.0**：持续跟进昇腾NPU生态，确保项目在国产硬件上的兼容性。

### 5. 对项目发展的影响

结合README中“Easy, fast, and cheap omni-modality model serving for everyone”的愿景，本次提交清晰体现了vllm-omni在**多模态覆盖广度**（新增TTS、视频生成）和**工程成熟度**（Bug修复、重构、依赖升级）上的双线推进。TTS和视频能力的补全，使项目从“多模态理解”向“多模态生成”延伸，更贴近“全模态”的定位。同时，对NPU等异构硬件的持续适配，也呼应了“cheap”和“for everyone”的普惠目标。整体来看，项目正从核心推理引擎向完整的全模态服务平台演进。

## 详细提交记录

### [90a08c0](https://github.com/vllm-project/vllm-omni/commit/90a08c0edaa15eda9f0b7bc740fd226703b77470)

- **作者**: Lucas(Ruijie)
- **时间**: 2026-08-13T17:58:33Z
- **提交信息**: [Model][TTS][WIP] Add dots.tts (rednote-hilab) — continuous-AR 48kHz TTS (#4765)

Signed-off-by: Moore-Z <zhumoore9661996@gmail.com>

### [dbc0dd6](https://github.com/vllm-project/vllm-omni/commit/dbc0dd6d85272aab507c78b35f837d8651807087)

- **作者**: Sy03
- **时间**: 2026-08-13T17:00:50Z
- **提交信息**: [Bugfix][Higgs-Audio-V3] Disable XQA decode (#6068)

Signed-off-by: Sy03 <1370724210@qq.com>
Signed-off-by: Sysy <1370724210@qq.com>

### [83d1f11](https://github.com/vllm-project/vllm-omni/commit/83d1f11449a0eaf2910a0a8e34c055df20e4f169)

- **作者**: Mu GuanLin
- **时间**: 2026-08-13T16:13:14Z
- **提交信息**: [Feat] LTX Standard Two-Stage Pipeline (#5500)

Signed-off-by: mglyn <1203789601@qq.com>

### [4b66f62](https://github.com/vllm-project/vllm-omni/commit/4b66f62e10f1b765dc6dc6baa5bbfe633234ec25)

- **作者**: Yukim1
- **时间**: 2026-08-13T13:29:03Z
- **提交信息**: [Refactor] Remove internal stage_configs_path plumbing (#5741)

Signed-off-by: zwhzzz0821 <2831474076@qq.com>
Signed-off-by: Hongsheng Liu <liuhongsheng4@huawei.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [f41451f](https://github.com/vllm-project/vllm-omni/commit/f41451f64c8b2fc20f8296f4c2a12c7d3bb16181)

- **作者**: Weiming Liao
- **时间**: 2026-08-13T12:01:01Z
- **提交信息**: [NPU] Upgrade to v0.27.0 (#6096)

Signed-off-by: Weiming Liao <liaowm5@gmail.com>

### [bbe6ccc](https://github.com/vllm-project/vllm-omni/commit/bbe6ccc512a404a2df8c977ea29003002f2683e8)

- **作者**: Hongsheng Liu
- **时间**: 2026-08-13T09:04:06Z
- **提交信息**: [Doc] Refresh community documentation (#6141)

Signed-off-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [bbb709c](https://github.com/vllm-project/vllm-omni/commit/bbb709cfb56358500cbd89a9cca0b3a24e66dbe5)

- **作者**: Canlin Guo
- **时间**: 2026-08-13T08:56:26Z
- **提交信息**: [BugFix] Use MOSS-TTS-Local official sample params (#6156)

Signed-off-by: Canlin Guo <canlinguosdu@gmail.com>

---
