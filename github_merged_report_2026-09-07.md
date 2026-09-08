# GitHub Stars 合并报告 - 2026-09-07

**合并日期**: 2026-09-08
**监控日期**: 2026-09-07
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


**报告日期**: 2026-09-08
**监控日期**: 2026-09-07
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2196
- **最后更新**: 2026-09-07T17:21:27Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 2
- **主要提交者**: Sun, Joel

## AI分析总结

# VeOmni 昨日提交分析报告

## 一、主要更新类型

本次提交包含**功能新增**与**性能优化/重构**两类变更，无Bug修复或文档更新。核心聚焦于模型训练效率与量化推理能力的提升。

## 二、关键变更点及项目方向关联

1. **DeepSeek V4 QAT量化训练支持**（617ccf）：新增fake quant训练能力，使模型在训练阶段即可模拟量化误差，与VeOmni“任意模态模型训练”的定位高度契合，扩展了对量化感知训练场景的支持。

2. **MoE LoRA路由与投影重构**（6bd8c72、e54d29e）：两项重构均针对MoE架构下的LoRA微调效率。前者避免one-hot路由的冗余计算，后者将独立的gate和up投影计算改为累积式，减少kernel启动开销与中间张量内存占用。

## 三、对项目的影响与潜在意义

- **训练效率提升**：MoE LoRA重构可显著降低微调时的显存消耗与计算延迟，对大规模MoE模型的参数高效微调具有直接价值。
- **量化部署链路完善**：QAT支持使VeOmni从单纯训练框架延伸至“训练-量化-部署”全流程，增强对边缘设备与推理优化的适配能力。
- **架构通用性增强**：两项重构均为通用优化，不限于特定模型，可惠及所有基于MoE+LoRA的训练任务。

## 四、值得关注的技术点

- **fake quant训练**：在训练中模拟INT8/INT4量化误差，避免后训练量化带来的精度损失，是工业界实用的量化方案。
- **累积式投影计算**：将多次小矩阵乘法合并为累积操作，减少kernel launch次数，是GPU上提升算子效率的典型优化手段。
- **避免one-hot路由**：MoE路由通常产生稀疏one-hot向量，直接计算会浪费算力，重构后采用更紧凑的索引或加权方式，降低计算冗余。

## 五、对项目发展的影响

结合README背景，VeOmni定位为“以模型为中心的分布式训练方案库”。本次提交体现了两个发展方向：一是**横向扩展模态与模型支持**（新增QAT训练能力，覆盖量化场景）；二是**纵向深化训练效率优化**（MoE LoRA的性能重构）。这两条路径共同强化了VeOmni作为“配方动物园”的实用价值——不仅提供多样化的训练方案，还确保这些方案在真实硬件上具备竞争力。特别是MoE架构在当前大模型中的主导地位，相关优化将直接提升框架对主流模型微调任务的吸引力。整体而言，这些提交标志着项目从“功能覆盖”向“性能精调”阶段的过渡，对吸引生产环境用户具有积极意义。

## 详细提交记录

### [617cc0f](https://github.com/ByteDance-Seed/VeOmni/commit/617cc0fb7d7af70c07f4507fc31d871f4eef55d0)

- **作者**: Joel
- **时间**: 2026-09-07T11:56:11Z
- **提交信息**: [model] feat: DeepSeek V4 QAT fake quant training (#1089)

### [6bd8c72](https://github.com/ByteDance-Seed/VeOmni/commit/6bd8c724ce777b2287c293f74c3525cba558a50d)

- **作者**: Sun
- **时间**: 2026-09-07T10:31:41Z
- **提交信息**: [lora, perf] refactor: avoid one-hot routing in eager MoE LoRA (#1155)

Signed-off-by: levius <2114377220@qq.com>

### [e54d29e](https://github.com/ByteDance-Seed/VeOmni/commit/e54d29e6d77ef811c6c5f2b3b7714ca6bc4e84c1)

- **作者**: Sun
- **时间**: 2026-09-07T08:06:44Z
- **提交信息**: [lora, perf] refactor: accumulate independent MoE-LoRA gate and up projections (#1154)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-09-08
**监控日期**: 2026-09-07
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2795
- **最后更新**: 2026-09-07T21:31:33Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 3
- **主要提交者**: Yang Yong (雍洋), qinxinyi, Bilang ZHANG

## AI分析总结

## 提交分析总结

### 1. 主要更新类型
本批提交包含**功能重构**、**Bug修复**和**兼容性优化**三类变更，无新增功能或文档更新。

### 2. 关键变更点与项目方向关系
- **统一调度逻辑并移除遗留兼容代码（#1496）**：重构训练调度流程，消除历史遗留的兼容分支，同时修复相关Bug。这与LightX2V作为轻量级视频生成推理框架的定位一致——通过精简代码路径降低维护成本，提升调度效率。
- **修复SwiftVR HEVC输出标记（#1495）**：修正Apple平台兼容性，将HEVC编码输出标记为`hvc1`格式。这是针对特定硬件/软件生态的适配优化，直接服务于框架的跨平台部署能力。
- **显式化KV replay输入（#1494）**：重构neopp模块，将KV缓存重放的输入参数从隐式依赖改为显式传递。这属于接口清晰化改造，提升代码可读性和可测试性。

### 3. 对项目的影响与潜在意义
- **调度统一**降低多场景切换的复杂度，为后续支持更多视频生成模型奠定基础；移除遗留代码可减少潜在冲突，提升系统稳定性。
- **SwiftVR修复**直接解决Apple设备上视频播放兼容性问题，扩大框架在macOS/iOS生态的适用性，对专业用户（如使用Apple Silicon工作流的内容创作者）尤为重要。
- **KV replay显式化**改善模块间接口契约，降低误用风险，为未来优化KV缓存策略（如内存管理、长视频生成）提供更清晰的扩展点。

### 4. 值得关注的技术点
- **调度重构**可能涉及分布式训练或推理的时序控制，统一逻辑意味着更一致的资源分配策略，值得关注是否引入新的配置参数或行为变化。
- **hvc1标记**是Apple对HEVC的特定封装要求，与通用`hev1`不同，涉及`avformat`层封装细节，体现对平台特性的精细处理。
- **KV replay显式化**暗示neopp模块可能正在向更模块化、可组合的方向演进，未来或支持更灵活的视频生成控制（如局部重放、多段拼接）。

### 5. 对项目发展的影响
LightX2V定位为**轻量级视频生成推理框架**，强调高效与易用。本批提交从三个维度推动项目成熟：
- **工程化**：通过调度统一和接口显式化，提升代码质量与可维护性，吸引更多开发者贡献；
- **生态适配**：修复Apple兼容性，扩大用户基础，尤其覆盖创意产业中广泛使用的Mac平台；
- **架构演进**：KV replay的显式化是模块解耦的信号，为后续支持更复杂的视频生成工作流（如条件生成、交互式编辑）预留空间。

整体来看，这批提交虽无用户可见的新功能，但属于**夯实基础、面向未来扩展**的稳健更新，符合框架类项目“先稳定内核，再扩展外延”的发展规律。

## 详细提交记录

### [ae4a1d9](https://github.com/ModelTC/LightX2V/commit/ae4a1d9038f652a0b2d722346718569ead20efdf)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-09-07T18:31:09Z
- **提交信息**: [Train]: unify scheduling and remove legacy compatibility and fix bugs (#1496)

### [7425d1e](https://github.com/ModelTC/LightX2V/commit/7425d1ec631528d1390d07d727ff7181465d5019)

- **作者**: qinxinyi
- **时间**: 2026-09-07T10:55:13Z
- **提交信息**: fix: mark SwiftVR HEVC output as hvc1 (#1495)

SwiftVR runner 的封装参数问题，没有设置 Apple 兼容的 hvc1

### [0c39e7b](https://github.com/ModelTC/LightX2V/commit/0c39e7bf680ea246ce3032e4b55e0fde9185c7e7)

- **作者**: Bilang ZHANG
- **时间**: 2026-09-07T07:02:24Z
- **提交信息**: refactor(neopp): make KV replay inputs explicit (#1494)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-09-08
**监控日期**: 2026-09-07
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2238
- **最后更新**: 2026-09-07T12:39:42Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-09-08
**监控日期**: 2026-09-07
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6343
- **最后更新**: 2026-09-07T15:37:20Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 3
- **主要提交者**: Yan Wang, SeongJun Lee, CarstyYou

## AI分析总结

# 提交分析总结

## 1. 主要更新类型

本批提交包含**功能新增**（NVFP4稀疏MLA支持）、**性能优化**（NVFP4 tile重打包）和**代码重构**（SM120命名统一为SM12x）三类变更，无Bug修复或文档更新。

## 2. 关键变更点与项目方向

- **重构提交**将SM120 grouped GEMM组件统一更名为SM12x，涉及JIT模块、C++命名空间、Python后端包和测试文件，同时保留旧导入路径和公开API作为兼容层。这属于内部架构清理，不改变内核行为。
- **功能提交**为DeepSeek V4 Flash注意力路径新增NVFP4稀疏MLA支持，采用384字节/token的分页缓存ABI，包含独立的prefill和decode内核，并配套独立的校准命名空间。
- **性能提交**将NVFP4 KV tile的量化转换从逐片段循环中提取到tile级重打包阶段，在无原生E2M1指令的架构上显著降低指令开销。

## 3. 项目影响与意义

这些变更体现了FlashInfer在**Blackwell架构（SM120/SM121）上的持续深耕**。重构为后续多架构扩展奠定更清晰的代码基础；NVFP4支持扩展了低比特精度推理的覆盖面，与FP8方案互补；性能优化使NVFP4在旧架构（如sm_80）上的表现接近FP8水平，缩小了格式间的性能差距。

## 4. 值得关注的技术点

- NVFP4缓存采用448维NoPE部分按16组量化、64维RoPE保持BF16的混合精度设计
- prefill内核通过CTA局部存储完成候选tile转置，避免全局workspace，并实现双缓冲
- 性能优化利用FP4 b128恰好对应一个scale-factor组的特性，将复杂转换简化为单字节加载
- 架构差异处理策略明确：SM100+使用原生指令，旧架构采用重打包路径

## 5. 对项目发展的影响

结合README中“面向推理的高性能GPU内核”定位，这些提交**强化了FlashInfer在最新GPU架构和前沿模型（DeepSeek V4）上的支持能力**。通过同时优化新旧架构上的低比特精度推理性能，项目在保持技术前沿性的同时兼顾了广泛硬件兼容性，有助于巩固其在推理加速库领域的竞争地位。

## 详细提交记录

### [91bda04](https://github.com/flashinfer-ai/flashinfer/commit/91bda04c66f7cb851e1ab3b78b9fecea644b9844)

- **作者**: CarstyYou
- **时间**: 2026-09-07T11:36:09Z
- **提交信息**: Refactor SM120 grouped GEMM as SM12x GEMM (#4838)

## Summary
- Rename the cute SM120 grouped GEMM component root to
`cute_sm12x_gemm`.
- Rename related JIT module, runner/op files, C++ namespace, Python
backend packages, and tests to the SM12x naming.
- Keep public grouped MoE op names unchanged.
- Preserve the v0.6.18 `cute_sm120_{fp8,mxfp8}_groupwise` Python import
paths as compatibility shims, while the implementation lives under
`cute_sm12x_*`.
- Keep the public JIT accessor names `get_gemm_sm120_module_cute_fp8`
and `get_gemm_sm120_module_cute_mxfp8` for API compatibility.

## Validation
- `git diff --check`
- `pre-commit run -a`
- Python compile for touched JIT/grouped-mm/test files
- JIT build/load for `cute_sm12x_gemm` and symbol check for
`moe_gemm_mxfp8_nt_groupwise` / `moe_gemm_fp8_nt_groupwise`
- `python3 -m pytest -q tests/grouped_mm/test_cute_sm12x_mxfp8.py
tests/grouped_mm/test_cute_sm12x_fp8.py` -> 452 passed


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added JIT-accessible FP8 and MXFP8 groupwise MoE GEMM operations,
including tuned variants with configurable tile sizes.
* Expanded SM12x GEMM integration for supported FP8 and MXFP8 workloads.

* **Refactor**
* Consolidated SM120 GEMM components under the updated SM12x naming and
structure without changing kernel behavior.
* Updated internal interfaces and launch paths to use the unified
implementation.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [ab6d2c8](https://github.com/flashinfer-ai/flashinfer/commit/ab6d2c89062b4803334b029b5c27ae6a764dce07)

- **作者**: Yan Wang
- **时间**: 2026-09-07T11:35:38Z
- **提交信息**: feat(sm120): add NVFP4 sparse MLA support for DeepSeek V4 Flash (#4955)

## 📌 Description

This PR adds native NVFP4 sparse MLA support on SM120/SM121 for the
DeepSeek V4 Flash attention path. The feature is opt-in through
`kv_cache_format="nvfp4"` on the existing
`flashinfer.mla.trtllm_batch_decode_sparse_mla_dsv4` API; the existing
FP8 cache ABI and behavior remain unchanged and are still the default.

### Implementation

- Adds a 384-byte/token paged NVFP4 cache ABI:
- the 448-dimensional NoPE payload is quantized in groups of 16 to
packed E2M1 values with one E4M3 scale per group;
  - the 64-dimensional RoPE payload remains BF16;
- full-page packing and incremental slot-based append helpers support
HND/NHD layouts and page-strided vLLM cache allocations.
- Adds separate native attention kernels for both phases:
- a single-launch streaming prefill kernel that gathers paged NVFP4 V
directly, performs the candidate-tile transpose in CTA-local storage,
and double-buffers the next source tile without a global transposed-V
workspace;
- a grouped split-K decode kernel with an autotuned chunks-per-block
tactic and split reduction.
- Reuses the existing sparse-MLA facade and planner persistence
mechanism while maintaining an independent NVFP4 calibration namespace.
The planner measures the streaming-prefill versus split-K-decode
crossover and decode tactic for each supported serving shape; it does
not reuse FP8 measurements.
- Supports primary and optional extra sparse cache segments, dynamic
top-k lengths, attention sinks, caller-owned workspace, CUDA Graph
capture, AOT/JIT registration, and empty pipeline-parallel slices.
- Adds correctness tests plus reproducible cache, prefill, decode, and
planner benchmarks.

The currently supported NVFP4 surface is 16/32/64/128 query heads,
primary top-k 128 or 512, primary page size 64, and optional extra-cache
page size 2 or 64.

### Performance

Measurements below are medians on an NVIDIA RTX PRO 5000 Blackwell GPU
(SM120), CUDA 13.0. FP8 and NVFP4 use the same generated inputs and
independently selected tactics.

| Phase and shape | FP8 | NVFP4 | Speedup |
| --- | ---: | ---: | ---: |
| Prefill: T=8192, H=64, K=128 | 3909.632 us | 2337.792 us | 1.6724x
(+67.24%) |
| Prefill: T=8192, H=64, K=128+512 | 10216.448 us | 7179.264 us |
1.4230x (+42.30%) |
| Prefill: T=8192, H=128, K=128+512 | 20149.248 us | 14240.768 us |
1.4149x (+41.49%) |
| Decode: T=8, H=64, K=128+512 | 43.008 us | 32.768 us | 1.3125x
(+31.25%) |

Reproduction:

```bash
python benchmarks/bench_sparse_mla_nvfp4_prefill.py \
  --num-tokens 8192 --num-heads 64 --topk 128 \
  --extra-topk 512 --extra-page-size 64

python benchmarks/bench_sparse_mla_nvfp4_decode.py \
  --num-tokens 8 --num-heads 64 --topk 128 \
  --extra-topk 512 --extra-page-size 64
```

A paired DeepSeek-V4-Flash serving run using `vllm/vllm-openai:v0.26.0`,
PP=4, 256 requests, concurrency 32, ISL=8192, OSL=1, prefix cache
disabled, and a 16K scheduled-token budget measured 80.466 s for FP8 and
73.808 s for NVFP4 over three runs: 1.0902x end-to-end speedup and
+9.02% token throughput.

## 🔍 Related Issues

Related NVFP4 SM120 work: #3640 and #4502.

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

SM120 regression results:

```text
pytest -q   tests/attention/test_sparse_mla_nvfp4_sm120.py   tests/attention/test_sparse_mla_nvfp4_sm120_plan.py   tests/attention/test_sparse_mla_sm120_dispatch.py
# 77 passed

pytest -q tests/attention/test_sparse_mla_sm120.py -k dsv4_public_api
# 5 passed, 483 deselected

pre-commit run --all-files
# all hooks passed (clang-format, mypy, ruff check, ruff format, and repository checks)
```

The GPU test matrix covers bit-level cache packing/append, HND/NHD and
strided pages, numerical references for prefill and decode, single/dual
cache layouts, supported head counts, ragged lengths, attention sinks,
public API dispatch, empty PP slices, CUDA Graph replay, and planner
policy.

## Reviewer Notes

- FP8 remains the default. NVFP4 is explicitly selected with
`kv_cache_format="nvfp4"`.
- Operator gains are shape-dependent. Long-prompt production shapes show
the largest prefill gains; short-K/small-head decode shapes can be
neutral, so NVFP4 uses its own calibrated phase/CPB decisions rather
than an FP8 tactic or a fixed query-token threshold.
- In the strict ISL=8192/OSL=256 serving experiment, full-request
throughput improved by 3.67% due primarily to lower TTFT, while
steady-window decode throughput was 0.57% below FP8. The decode operator
path is included and independently tuned, but additional serving-level
decode optimization remains follow-up work.
- Implementation, tests, benchmarking, and PR drafting were AI-assisted;
the listed checks and measurements were run on hardware.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added NVFP4 cache packing and incremental append support for
DeepSeek-V4 sparse MLA.
* Added NVFP4 sparse MLA decode and prefill on compatible SM120/SM121
GPUs.
* Added FP8 or NVFP4 cache format selection, optional extra KV data,
attention sinks, and runtime top-k lengths.
* Added automatic performance planning and calibration for decode versus
prefill.

* **Documentation**
  * Documented the new NVFP4 cache APIs.

* **Benchmarks**
* Added NVFP4 packing, append, decode, prefill, and planning benchmarks.

* **Bug Fixes**
  * Added validation for invalid cache alignment and slot mappings.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: tiffany940107 <tiffany940107@users.noreply.github.com>
Co-authored-by: Yan Wang <yanwa@smc521ge-0080.ipp2a2.colossus.nvidia.com>
Co-authored-by: Yan Wang <yanwa@2u2g-spr-0094.ipp4a1.colossus.nvidia.com>

### [a4c17d7](https://github.com/flashinfer-ai/flashinfer/commit/a4c17d77a15fbff1ef7b34a4ad2b5faaa5bdd6dc)

- **作者**: SeongJun Lee
- **时间**: 2026-09-07T08:23:21Z
- **提交信息**: perf(attention): repack NVFP4 KV tiles to 16-bit on targets without a native E2M1 convert (#4769)

<!-- .github/pull_request_template.md -->

## 📌 Description

FP8 KV already dequantizes a whole tile into the 16-bit staging buffer
and lets the QK/PV MMAs read it back with the native `ldmatrix` path
(`repack_fp8_tile_to_bf16`, `KernelTraits::USE_KV_REPACK`). NVFP4 was
excluded from that path and kept dequantizing inside the fully unrolled
`(mma_d, mma_kv)` nest, so its dequant sequence — magnitude table, sign
spread, scale-factor gather, scale multiply, plus two `__shfl_sync` per
fragment register for the 4-bit fragment swizzle — was replicated once
per pair.

On targets without a native E2M1 conversion that turns the kernel
instruction-fetch bound rather than math bound. `ncu` on FA2 paged
prefill, batch 1, 2048x2048, head_dim 128, sm_80:

| | NVFP4 before | FP8 | NVFP4 after |
|---|---|---|---|
| `no_instruction` stall, % of warp-active | 24.9 | 1.4 | 1.3 |
| `sm__pipe_tensor_cycles_active`, % of peak | 18.7 | 51.5 | 48.6 |
| kernel time | 1.403 ms | 0.539 ms | 0.552 ms |

`repack_fp4_tile_to_16b` dequantizes one K or V tile, scale factors
included, into the same staging layout. One thing makes it cheaper than
the in-loop path it replaces, beyond amortizing the work over the tile:
one padded FP4 b128 spans exactly `HEAD_DIM` 16 == `NVFP4_SF_VEC_SIZE`
elements, i.e. one scale-factor group, so the per-fragment gather of two
scale factors plus a four-wide E4M3 convert collapses to one byte load
and one convert per b128. The cross-lane fragment swizzle disappears
with it.

### Architecture scope

The repack only makes sense where the E2M1 conversion is a software
sequence. From SM100 it is a single instruction, the premise above does
not hold, and the staging buffer would cost shared memory -- and a
smaller `NUM_MMA_KV`, since the occupancy budget counts it -- for
nothing.

That decision has to be visible to the host, which sizes the storage and
picks `NUM_MMA_KV`, not just to the device. `__CUDA_ARCH__` is not, but
`__CUDA_ARCH_LIST__` is: it names every target of the module in both
passes. So the policy is a template parameter, `ENABLE_FP4_REPACK`,
threaded through one predicate:

```cpp
template <typename DTypeKV, uint32_t CTA_TILE_Q, uint32_t HEAD_DIM_QK, uint32_t HEAD_DIM_VO>
constexpr bool use_kv_repack(bool enable_fp4_repack);
```

`KVRepackSmem`, `KernelTraits::USE_KV_REPACK` and the `kUseRepack` in
all three launcher budgets now go through it, so they cannot disagree.
Each launcher body became `...DispatchedImpl<..., ENABLE_FP4_REPACK>`
and the public entry point is a thin wrapper that picks the variant
before any budget arithmetic runs.

- a module built only for pre-SM100 targets folds to one variant, with
the repack;
- a module built only for SM100+ folds to one variant, with no staging
buffer and no budget for it;
- a module spanning both (the release wheel bundles SM7.5 through
SM12.x) builds both and selects on the device's compute capability. The
device query happens only on that path, so FP16, FP8 and single-regime
FP4 launches gain no CUDA API call.

Measured on the FP4 paged prefill translation unit, `head_dim` 128:

| built for | kernel entries | software dequant `prmt` | native e2m1 cvt
|
|---|---|---|---|
| `sm_80` | 13 | 340 | 0 |
| `sm_100a` | 13 | 0 | 2240 |
| `sm_80` + `sm_100a` | 36 | 740 | 2240 |

and the storage and budget follow, at `head_dim` 128 with `NUM_WARPS_KV`
1 and a 2-byte query dtype:

| variant | `use_kv_repack` | `kKVSmemPerMmaKV` | `sizeof(SmemStorage)`
|
|---|---|---|---|
| repack | 1 | 8448 | 41216 |
| native | 0 | 4352 | 37120 |

The 4096-byte difference is the staging buffer: on a native-only build
it is neither allocated nor charged.

The repack condition also gained a `HEAD_DIM_QK` bound for FP4. The
staging buffer is sized `max(HEAD_DIM_QK, HEAD_DIM_VO)`, so an
asymmetric shape such as `HEAD_DIM_QK` 480 with `HEAD_DIM_VO` 128 would
need more shared memory than the in-loop path it replaces and leave no
launchable `NUM_MMA_KV`.

Single prefill dispatches `CTA_TILE_Q` inside the Impl, so its
eligibility probe asks whether any CTA tile in the specialization could
be repack-eligible rather than whether a particular one is. A
mixed-architecture build therefore emits both policy variants for that
whole specialization, including its `CTA_TILE_Q` 16 kernels.

### Stacking

Both prerequisites have landed. #4746 brought in the `e2m1x8_to_f16x8` /
`e2m1x8_to_bf16x8` helpers and `nvfp4_sf4_to_packed2x2` that the repack
calls, and #4767 the scale-factor budget the corrected repack condition
depends on. Rebasing onto `main` dropped both by patch id with nothing
to resolve by hand, so this PR is now the repack and its policy default:
two commits touching only `include/flashinfer/attention/prefill.cuh`.

Earlier revisions of this section described those prerequisites while
they were still open, and one of them claimed that reviewing the last
commit alone was enough. Neither applies now.

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

## 🧪 Tests

- [ ] Tests have been added or updated as needed. — the repack is an
alternative lowering of an existing computation, covered by the existing
NVFP4 prefill/decode tests; the checks below are what I ran to establish
it is lossless.
- [ ] All tests are passing (`unittest`, etc.) — I ran the NVFP4 subset
on sm_80, not the full suite.

```bash
pytest -q tests/attention/test_batch_prefill_kernels.py \
          tests/attention/test_batch_decode_kernels.py \
          tests/attention/test_single_prefill.py -k "nvfp4 or fp4"
# 355 passed, 9 skipped
```

Re-run after the per-architecture variant work, same result: 355 passed,
9 skipped.

Output equivalence against FA2 attention run on the dequantized KV in
the query dtype, so kernel and reference consume the same values. This
covers the FP4 payload path end to end; the scale-factor conversion is a
separate path and is scoped below:

```
head_dim 128  f16  maxabs 0        head_dim 128  bf16  maxabs 0
head_dim 256  f16  maxabs 0        head_dim 256  bf16  maxabs 0
head_dim 512  f16  maxabs 0        head_dim 512  bf16  maxabs 0
```

Against the previous NVFP4 build, head_dim 128 and 512 are bit-identical
and head_dim 256 prefill is not: the corrected budget makes the chooser
pick a `NUM_MMA_KV` that actually fits two blocks per SM, which changes
the flash-attention accumulation order. The reference comparison above
is what settles which side is closer — at head_dim 256 the previous
build differs from the reference by up to 1.95e-3 (f16) and this one by
0.

Latency on sm_80, median of three, one process per dtype, FA2 paged:

| case | NVFP4 before | NVFP4 after | FP8 | FP16 |
|---|---|---|---|---|
| prefill b1 4096x4096 hd128 | 4.763 | 1.900 | 1.858 | 1.516 |
| prefill b4 2048x2048 hd128 | 4.427 | 1.840 | 1.857 | 1.546 |
| prefill b8 1024x1024 hd128 | 2.407 | 0.994 | 0.983 | 0.884 |
| prefill b2 2048 hd256 | 3.790 | 1.254 | 1.209 | 0.910 |
| decode b32 kv8192 hd128 | 1.154 | 1.036 | 0.718 | 0.848 |
| decode b16 kv4096 hd512 | 1.114 | 0.612 | n/a | 0.398 |

head_dim 512 keeps the in-loop path (`HEAD_DIM_VO <= 256`); its gain
comes from the sign-spread commit underneath.

Scale-factor contract. `nvfp4_sf4_to_packed2x2` arrives with #4746 and
is unchanged by the repack commits, but the repack calls it, so its
contract applies here too and is now written down at the declaration.
Enumerating all 256 E4M3 encodings, the software and hardware
conversions agree on 254 and differ only on the NaN encodings `0x7F` and
`0xFF`, which the software converter maps to +-480 instead of NaN:

| byte | software | hardware |
|---|---|---|
| `0x7F` | +480 | NaN |
| `0xFF` | -480 | NaN |

Scale factors are expected finite. Quantization does not produce a NaN
scale, and the only way one reaches the kernel is an out-of-range KV
row, whose scores `logits_mask` replaces with `-inf` before they can
reach the accumulator. The repack does not widen that exposure: it
converts the same scale factors the in-loop path converted, with the
same helper. Callers supplying an externally built `kv_cache_sf` that
can contain those encodings should not expect NaN to propagate.

Review follow-ups in this branch:

- the E2M1 nibble helpers moved out of the `FLASHINFER_ENABLE_FP4_E2M1`
guard. They have no FP4 type in their signatures, and
`repack_fp4_tile_to_16b` names them from a template whose FP4 branch is
discarded rather than removed, so a build without FP4 enabled failed to
compile. Checked `sm_80` and `sm_100a`, with and without the macro.
- `clang-format` applied (the pinned 19.1.1), covering both spots the
automated check flagged.
- the repack policy became a template parameter selected per
architecture regime, so a module built only for SM100+ neither allocates
the staging buffer nor charges `NUM_MMA_KV` for it; see Architecture
scope.
- the single-prefill kernel now takes the repack for NVFP4 as well. It
shares `SharedStorage` with the ragged kernel, so whenever the variant
allocates the staging buffer it is already counted in that kernel's
`NUM_MMA_KV` budget; NVFP4 was paying for it without using it. On a
native-only build there is no staging buffer to pay for. FP8 keeps the
in-loop path it has always taken in that kernel: switching it over is a
behavior change this PR does not measure, and
`tests/attention/test_single_prefill.py` has no FP8 KV case that would
catch a regression.

The `sm_80` code path is unchanged by the variant work in the sense that
matters -- it is the `ENABLE_FP4_REPACK = true` instantiation, and its
dequant/repack instruction sequences are the ones measured above.
Whole-cubin byte identity is not the right oracle here: the storage type
and its size differ per variant, so the comparison is per-path, plus the
functional checks below.

Additional runs for the single-prefill change and for the shared-memory
budget arithmetic:

```bash
pytest -q tests/attention/test_single_prefill.py \
       tests/attention/test_batch_prefill_kernels.py::test_batch_prefill_paged_cta_tile_q_smem_probe_qk448_vo256
# 207 passed, 13 skipped
```

The second one pins the `FA2DetermineCtaTileQ` probe at `(head_dim_qk,
head_dim_vo) = (448, 256)` for both a 2-byte and a 1-byte KV dtype,
which is the shape class the corrected budget and the new `HEAD_DIM_QK`
bound act on.

Not verified: the mixed-module runtime selection on an SM100+ device,
and latency on sm_89 and sm_90 -- no hardware for either. The numbers
above are local measurements; the fork's CI test matrix is
permission-gated and did not run them. Both compile, and `ptxas -v`
shows register spilling on the FP4 prefill kernels drops there too — 424
B to 28 B of spill stores on sm_89, 376 B to 28 B on sm_90a, against 392
B to 8 B on sm_80.




<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added optimized NVFP4 support for single, ragged, and paged prefill
attention workflows.
* Added automatic GPU architecture-aware selection of FP4 data
repacking.
* Added FP4 scale conversion and tile dequantization for attention
processing.
* Added faster FP4 conversion to FP16 and BF16 for supported vector
sizes.
* **Compatibility**
* Preserved FP8 behavior and fallback conversion paths across supported
configurations.
* Added support for consistent operation across older and newer GPU
architectures.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: lesj0610 <lesj0610@godoiksan.org>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-09-08
**监控日期**: 2026-09-07
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4346
- **最后更新**: 2026-09-07T23:03:07Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: William Lin, Junda Su

## AI分析总结

# FastVideo 仓库提交分析

## 主要更新类型

本次提交以**功能新增**和**代码重构**为主，包含两项核心变更：Wan采样流程的简化重构，以及Dreamverse新增H3架构支持。

## 关键变更点与项目方向关系

**提交1（556ac70）— Wan采样与测试重构**：对Wan模型的采样逻辑进行简化，并同步优化相关测试。Wan是FastVideo支持的重要视频生成模型之一，采样流程的简化直接降低使用门槛和推理复杂度，与项目“快速、易用”的定位高度一致。重构测试代码则体现项目对代码质量与可维护性的持续投入。

**提交2（e7456f1）— Dreamverse新增H3支持**：为Dreamverse框架引入H3（一种高效的序列建模架构）支持。Dreamverse是项目中的视频生成方案，H3的加入意味着扩展了底层架构选择，使模型在长序列建模和计算效率方面具备新的可能性。这一变更直接丰富了项目的技术栈和模型适配能力。

## 对项目的影响与潜在意义

两项变更分别从**工程效率**和**模型能力**两个维度推进项目发展。Wan采样重构使核心推理路径更加精简，降低用户使用成本，有助于吸引更多开发者基于FastVideo进行二次开发；H3支持则为Dreamverse带来架构层面的灵活性，可能提升模型在长视频生成任务中的表现，或为后续优化预留空间。整体上，这两项提交体现了项目在“易用性”与“先进性”双轨并进的策略。

## 值得关注的技术点

- **采样流程简化**：需关注重构后采样结果是否与原有逻辑完全一致，以及是否引入新的默认参数或配置方式，这可能影响已有用户的迁移成本。
- **H3架构集成**：H3作为较新的序列建模方案，其在视频生成中的实际效果值得观察，尤其是与原有架构的对比表现。
- **测试同步优化**：重构伴随测试更新，说明项目重视回归验证，这一工程实践值得肯定。

## 对项目发展的影响

结合README中FastVideo“快速视频生成与训练”的定位，本次提交一方面通过简化采样流程强化了“Fast”的核心理念，另一方面通过引入H3架构拓展了模型支持的广度，有助于项目在视频生成工具链中保持技术竞争力，并吸引更多研究者和工程师参与生态建设。

## 详细提交记录

### [556ac70](https://github.com/hao-ai-lab/FastVideo/commit/556ac7088e7b4750806d277d31e0db6cd25a5238)

- **作者**: William Lin
- **时间**: 2026-09-07T22:57:19Z
- **提交信息**: [refactor] Simplify Wan sampling and tests (#1825)

### [e7456f1](https://github.com/hao-ai-lab/FastVideo/commit/e7456f1b75805ded7eac11740cfd0569f31e2044)

- **作者**: Junda Su
- **时间**: 2026-09-07T20:09:44Z
- **提交信息**: Add H3 support into Dreamverse (#1800)

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-09-08
**监控日期**: 2026-09-07
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34457
- **最后更新**: 2026-09-07T19:52:56Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-09-08
**监控日期**: 2026-09-07
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


**报告日期**: 2026-09-08
**监控日期**: 2026-09-07
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13063
- **最后更新**: 2026-09-07T22:52:38Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Hong Zhang

## AI分析总结

### 1. 主要更新类型
- **Bug修复**：针对DDP（分布式数据并行）训练在特定条件下崩溃的问题。

### 2. 关键变更点及其与项目整体方向的关系
- 提交引入`exclude_quantized_params_from_ddp_sync`辅助函数，用于在DDP同步时排除量化参数（tensor-subclass类型）。
- 该函数通过`try/except`包裹，防止因Torch私有API（`torch.utils._python_dispatch`中的`is_traceable_wrapper_subclass`）不可用或行为变化导致训练启动失败。
- 项目方向：DiffSynth-Studio聚焦于扩散模型合成与训练，量化技术（如低比特权重）是提升效率的关键路径。此修复确保量化模型在分布式训练场景下的稳定性，直接支持项目对高效、可扩展训练能力的追求。

### 3. 对项目的影响和潜在意义
- **直接影响**：解决DDP训练与量化权重兼容性问题，避免因Torch版本差异导致的崩溃，提升训练鲁棒性。
- **潜在意义**：降低用户使用量化模型进行分布式训练的门槛，增强项目在资源受限环境下的实用性；同时通过优雅降级（警告而非报错），保持对旧版Torch的兼容性，扩大用户覆盖范围。

### 4. 值得关注的技术点
- **Tensor-subclass量化权重**：PyTorch中通过子类化`torch.Tensor`实现自定义量化逻辑，DDP同步时需特殊处理，避免梯度或状态同步错误。
- **私有API防御性调用**：对`torch.utils._python_dispatch`等私有模块的依赖需谨慎，采用`try/except`降级策略是稳健做法，防止未来Torch更新破坏功能。
- **DDP与量化协同**：量化参数通常无需完整精度同步，排除它们可减少通信开销，但需确保不影响训练正确性。

### 5. 基于README的项目背景，这些提交如何影响项目发展
- DiffSynth-Studio作为扩散模型合成工具，强调易用性和性能。此修复直接提升分布式训练场景的可靠性，使项目能更好地支持大规模实验或资源受限用户的量化训练需求。
- 结合README中提到的PyPI发布和Trendshift热度，项目正吸引广泛社区使用。此类兼容性修复有助于维护用户信任，减少因环境差异导致的挫败感，促进项目在更复杂生产环境中的落地。
- 长期看，该提交为后续引入更激进的量化策略（如混合精度或动态量化）铺平道路，强化项目在高效训练领域的竞争力，符合其“合成+优化”的定位。

## 详细提交记录

### [cba0dac](https://github.com/modelscope/DiffSynth-Studio/commit/cba0dac7fe796fa0d7f4d1286fdf2e9dbaa2b1b3)

- **作者**: Hong Zhang
- **时间**: 2026-09-07T13:27:00Z
- **提交信息**: Fix DDP training crash with tensor-subclass quantized weights (#1674)

* exclude_quantized_params_from_ddp_sync

* Guard exclude_quantized_params_from_ddp_sync against private torch API

is_traceable_wrapper_subclass comes from torch.utils._python_dispatch, a private
module. Wrap the whole helper in try/except so that a torch version where the
import or the introspection does not hold degrades to the previous behaviour
with a warning, instead of breaking training startup.

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-09-08
**监控日期**: 2026-09-07
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 35603
- **最后更新**: 2026-09-07T23:55:56Z

## 提交统计

- **昨日提交总数**: 28
- **提交者数量**: 23
- **主要提交者**: Mick, Baizhou Zhang, Jeffrey Wang

## AI分析总结

# sglang 仓库提交分析

## 一、主要更新类型

本次提交涵盖多种类型，以**硬件适配与优化**（AMD/NPU/Blackwell）、**Bug修复**、**CI测试改进**、**文档更新**和**内核优化**为主，同时包含少量架构重构（CP V1弃用）和代码清理工作。

## 二、关键变更点与项目方向

1. **多硬件平台深度优化**：大量提交针对AMD（gfx95、DSV4、Kimi-K3）、NPU（arch35）、Blackwell（DCP解码）等平台进行专项优化，体现项目“多硬件后端”战略。AMD相关提交尤为密集，包括SWA reprefill-tail恢复、统一KV池大小调整、EAGLE崩溃修复等，显示AMD平台正成为重点支持对象。

2. **DeepSeek-V4（DSV4）系列支持**：多个提交围绕DSV4展开，包括NPU上的DSV4处理增强、AMD上的dp-attention路由优化、统一KV池与SWA ring核算等，表明项目正积极适配新一代模型架构。

3. **内核精简与依赖整合**：移除自带的密集BF16 GEMM实现（转向FlashInfer 0.6.18）、删除flashinfer trtllm MoE中的路由偏置转换，体现“减少重复造轮子、拥抱成熟库”的技术路线。

4. **CI与测试体系重构**：大规模测试清理（净减11.4K行）、统一测试分类、修复多个CI测试问题，反映项目在快速迭代中对测试质量的重视。

5. **文档与配方（Cookbook）扩展**：新增Qwen3.8-Flash-Next NVFP4配方（DGX Spark/RTX PRO 6000）、MiniCPM5-2B配方、GB300/GB200 H3配方，强化项目作为“LLM推理部署指南”的定位。

## 三、对项目的影响与意义

- **硬件生态扩展**：AMD/NPU/Blackwell的持续优化将扩大sglang的适用硬件范围，吸引更多用户。
- **架构演进**：CP V1弃用（3.5/5步）表明项目正推进Context Parallel的版本升级，为后续架构简化铺路。
- **稳定性提升**：大量Bug修复（EAGLE崩溃、Mamba预填充、Mooncake链接器）直接提升生产环境的可靠性。
- **性能竞争力**：Blackwell DCP解码优化、MoE Triton配置、fp32 all-reduce缓冲区等改动直接提升推理吞吐和效率。

## 四、值得关注的技术点

1. **FlashInfer依赖加深**：用FlashInfer替代自研GEMM内核，反映项目对第三方高性能内核库的信任度提升。
2. **AMD SWA与KV池管理**：在HiCache关闭时恢复reprefill-tail、统一KV池核算，涉及显存管理的精细调优。
3. **EAGLE投机解码修复**：处理无kv_index_translator绑定时DSA fp8读取崩溃，属于投机解码链路的边界情况修复。
4. **Ray指标后端**：新增对Ray指标后端的支持，便于分布式场景下的可观测性。
5. **DSpark CUDA图回放修复**：解决MegaMoE TP注意力下的图回放问题，涉及CUDA图与动态形状的兼容性。

## 五、对项目发展的影响

sglang定位为**高性能LLM推理引擎**，强调多硬件支持和最新模型适配。本次提交显示项目正沿着“**广度扩展+深度优化**”双轨推进：广度上覆盖更多硬件（AMD、NPU、Blackwell）和模型（DSV4、Kimi-K3、MiniCPM5）；深度上通过内核精简、CI治理和文档建设提升工程质量和开发者体验。特别是AMD和NPU的大量提交，暗示项目正积极争夺非NVIDIA市场份额。整体来看，sglang正从“NVIDIA优先”走向“多平台并重”，同时通过依赖成熟内核库和强化测试体系，为长期可维护性奠定基础。

## 详细提交记录

### [20ca564](https://github.com/sgl-project/sglang/commit/20ca564bf77518604b89dc9f7fdba640daabd88b)

- **作者**: Ziang Li
- **时间**: 2026-09-07T23:08:11Z
- **提交信息**: Add zianglih as online NVFP4 and DSA Top-K code owner (#33624)

### [85d3940](https://github.com/sgl-project/sglang/commit/85d39401c85d143f62b38b716d97efaaea845840)

- **作者**: Baizhou Zhang
- **时间**: 2026-09-07T22:39:34Z
- **提交信息**: [CP V1 Deprecation 3.5/5]  Deprecate HIP/NPU/MUSA prefill CP and remove legacy implementation (#38293)

### [f4b75b5](https://github.com/sgl-project/sglang/commit/f4b75b5c36cabcd99e23ac2effe35c933b38199b)

- **作者**: Jimmy Shong
- **时间**: 2026-09-07T22:33:03Z
- **提交信息**: docs(cookbook): Qwen3.8-Flash-Next NVFP4 recipes for DGX Spark (1x, 2x) and RTX PRO 6000 (#37995)

Co-authored-by: Jiminator <rdxa@rdxa-int-spark-01.yvb.moe>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [5a5d8e4](https://github.com/sgl-project/sglang/commit/5a5d8e47c5080530321ddd984a392941195b2c1f)

- **作者**: Bingxu Chen
- **时间**: 2026-09-07T21:42:53Z
- **提交信息**: [AMD][CI] Remove obsolete split-dim check from Kimi-K3 prefill test (#38288)

### [e9e9e37](https://github.com/sgl-project/sglang/commit/e9e9e37ddcf2dfe20a0c4da0ff73598f33fe1460)

- **作者**: amd-danli103
- **时间**: 2026-09-07T21:27:53Z
- **提交信息**: [AMD] Restore SWA reprefill-tail on UnifiedRadixCache when HiCache is off (#32759)

Co-authored-by: Thomas Wang <thomawan@amd.com>

### [570087c](https://github.com/sgl-project/sglang/commit/570087ceda91333c3fb4bad86dfbc28ffb4f4723)

- **作者**: yuttian1
- **时间**: 2026-09-07T20:13:04Z
- **提交信息**: [AMD][DSV4] Reland unified-KV pool sizing and SWA ring accounting, fully gated (#38192)

Co-authored-by: hnyls2002 <lsyincs@gmail.com>
Co-authored-by: Liangsheng Yin <hnyls2002@gmail.com>

### [6287ebf](https://github.com/sgl-project/sglang/commit/6287ebf43a4408a706d42358d4dba0b688c1f3d8)

- **作者**: jiaryang
- **时间**: 2026-09-07T20:03:10Z
- **提交信息**: [AMD] Fix EAGLE crash when no kv_index_translator is bound on the DSA fp8 read door (#38318)

### [a711785](https://github.com/sgl-project/sglang/commit/a7117854754f52b0dd648d04094794de8102aa79)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-09-07T19:59:33Z
- **提交信息**: [Kernel] Drop the vendored dense BF16 GEMM port in favor of FlashInfer 0.6.18 (#38124)

Co-authored-by: Mohammad Angkad <mohammad.angkad@radixark.ai>

### [bf68369](https://github.com/sgl-project/sglang/commit/bf68369a181c05dc19e46323c12e6aeaa4c08a82)

- **作者**: Jeffrey Wang
- **时间**: 2026-09-07T19:43:19Z
- **提交信息**: [ray] Support Ray metric backend for engine metrics (#31415)

Signed-off-by: Jeffrey Wang <jeffreywang@anyscale.com>
Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>
Co-authored-by: Qiaolin Yu <liin1211@outlook.com>

### [8392c36](https://github.com/sgl-project/sglang/commit/8392c36bce22d3c54a6381aea6e003d6bf57719b)

- **作者**: Aurick Qiao
- **时间**: 2026-09-07T19:41:03Z
- **提交信息**: [Bugfix][Mamba] Clear deferred init metadata before speculative decode (#37165)

### [dcebe8c](https://github.com/sgl-project/sglang/commit/dcebe8c4733a5cb802fb679e0c8fbb886e2801b0)

- **作者**: Chan ahn
- **时间**: 2026-09-07T17:17:55Z
- **提交信息**: [Kernel] Add fused MoE Triton configs for Qwen3.8-Flash-Next FP8 on NVIDIA H200 NVL (TP2+EP2) (#38116)

### [c99d906](https://github.com/sgl-project/sglang/commit/c99d906effa8bd05573995127f0d4a0984c5a96a)

- **作者**: Brayden Zhong
- **时间**: 2026-09-07T16:04:33Z
- **提交信息**: Drop the routing bias casts in flashinfer trtllm MoE (#33591)

Co-authored-by: Brayden Zhong <brayden@radixark.ai>

### [62bca08](https://github.com/sgl-project/sglang/commit/62bca081a3860ec1301ca932bf28822e74401cff)

- **作者**: Shuwen Wang
- **时间**: 2026-09-07T15:52:32Z
- **提交信息**: [CI] Fix request receiver EP scale joiner test patch (#38342)

### [f3ccd1c](https://github.com/sgl-project/sglang/commit/f3ccd1c0e42926e795a4304d50935b8cbd210169)

- **作者**: Mick
- **时间**: 2026-09-07T15:13:14Z
- **提交信息**: [diffusion] CI: baseline the e2e of ten unguarded perf cases (#38335)

Co-authored-by: Mick Qian <mickqian@radixark.ai>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [b5c9b68](https://github.com/sgl-project/sglang/commit/b5c9b68f03c0552c94b717e200e7c2e6166c6741)

- **作者**: zijiexia
- **时间**: 2026-09-07T14:08:42Z
- **提交信息**: [Kimi-K3] Recover the reply when the model skips the think channel (#37743)

Co-authored-by: Xinyuan Tong <115166877+JustinTong0323@users.noreply.github.com>

### [e4008de](https://github.com/sgl-project/sglang/commit/e4008de757c10237a01c759d10d39f938de21b8a)

- **作者**: zijiexia
- **时间**: 2026-09-07T13:30:17Z
- **提交信息**: Add MiniCPM5-2B cookbook (#38295)

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [62a4a6e](https://github.com/sgl-project/sglang/commit/62a4a6ea0edcd389725aa7a3dd773e70dc2e4b35)

- **作者**: AndyLi429
- **时间**: 2026-09-07T13:08:06Z
- **提交信息**: [NPU] Add NPU arch35 support and enhance DSV4 processing in DeepSeek-V4 (#37373)

Co-authored-by: AndyLi429 <AndyLi429@noreply.gitcode.com>
Co-authored-by: Kailong Lu <kelonlu@163.com>
Co-authored-by: cx <chengxin65@huawei.com>
Co-authored-by: ranjiewen <ranjiewen@huawei.com>
Co-authored-by: HEX1A0A <1a0ahex@gmail.com>
Co-authored-by: vstone-w <374330057@qq.com>
Co-authored-by: Even Zhou <even.y.zhou@outlook.com>
Co-authored-by: ClownBin <chaobin1993@126.com>
Co-authored-by: sglang-npu-bot <sglangnpu@163.com>

### [df623d3](https://github.com/sgl-project/sglang/commit/df623d3cbd8ecb56e3cc08ec75285c9ec5000617)

- **作者**: Shuwen Wang
- **时间**: 2026-09-07T12:25:13Z
- **提交信息**: fix: keep queued Mooncake linker loads after abort (#38195)

Co-authored-by: huangtingwei <141888744+huangtingwei9988@users.noreply.github.com>

### [c5367fa](https://github.com/sgl-project/sglang/commit/c5367fa964af92d8c253cc129ea8a86e97cab2c5)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-09-07T11:25:12Z
- **提交信息**: [CI] Fix stale ServerArgs fake in chunked-SGMV LoRA test (#38315)

### [755f97c](https://github.com/sgl-project/sglang/commit/755f97c6223d4e70b11cc3aac934bde6c5fa2438)

- **作者**: Shuwen Wang
- **时间**: 2026-09-07T10:16:00Z
- **提交信息**: [CI] Fix the DSpark dp-tier unit test fixture after #34919 (#38314)

### [8ae9620](https://github.com/sgl-project/sglang/commit/8ae962021dbb5eb8ee408c578e772c13e2c934fe)

- **作者**: Carrie Chen
- **时间**: 2026-09-07T08:57:07Z
- **提交信息**: Use fp32 in TRTLLM all reduce buffers  (#36143)

Co-authored-by: Brayden Zhong <b8zhong@uwaterloo.ca>

### [861d40f](https://github.com/sgl-project/sglang/commit/861d40f3ee6f04837cccb29b341681b688e2365d)

- **作者**: BingjiaWang
- **时间**: 2026-09-07T08:35:35Z
- **提交信息**: Fix DSpark CUDA graph replay with MegaMoE TP attention (#34919)

### [ba6d3df](https://github.com/sgl-project/sglang/commit/ba6d3df69a3c17430cf9e3974d0fed6160d40135)

- **作者**: Mick
- **时间**: 2026-09-07T08:32:29Z
- **提交信息**: [diffusion] doc: document verified GB300 and derived GB200 H3 recipes (#38296)

### [b576633](https://github.com/sgl-project/sglang/commit/b5766336d4fa1f235a05e864b5c5be6fd13cd5e5)

- **作者**: Cheng Wan
- **时间**: 2026-09-07T08:10:44Z
- **提交信息**: [Perf] Unified memory: close the DCP decode gap on Blackwell (#37926)

### [a8edaff](https://github.com/sgl-project/sglang/commit/a8edafff7cf4a8096437141bd43c00a42faa230b)

- **作者**: lixiufei-leo
- **时间**: 2026-09-07T07:36:15Z
- **提交信息**: [AMD][gfx95] DSV4 wo_b (dp-attention): route to tuned bpreshuffle GEMM instead of triton (#38227)

Co-authored-by: lixiufei-leo <lixiufei-leo@users.noreply.github.com>

### [644841c](https://github.com/sgl-project/sglang/commit/644841c50cb3faccc518c935c71658b2cc6d463e)

- **作者**: billishyahao
- **时间**: 2026-09-07T07:31:24Z
- **提交信息**: [AMD] Support aiter fa mha chunked kv for Kimi-K3 (#37691)

Co-authored-by: HAI <hixiao@gmail.com>

### [4d23a4f](https://github.com/sgl-project/sglang/commit/4d23a4fa6d062a9a7ccc3008cb32f8a5454198e2)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-09-07T07:13:59Z
- **提交信息**: [Test] Consolidate test cleanup and CI taxonomy (net -11.4K lines) (#37436)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [6a1ff90](https://github.com/sgl-project/sglang/commit/6a1ff90f2dcbdc080d32a40492cde789705ffa7e)

- **作者**: Ma Mingfei
- **时间**: 2026-09-07T07:09:52Z
- **提交信息**: [CPU] use CustomTestCase for registered CPU tests (#38244)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-09-08
**监控日期**: 2026-09-07
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1273
- **最后更新**: 2026-09-07T04:46:10Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-09-08
**监控日期**: 2026-09-07
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 91188
- **最后更新**: 2026-09-08T00:08:43Z

## 提交统计

- **昨日提交总数**: 29
- **提交者数量**: 22
- **主要提交者**: Zhewen Li, Thien Tran, Kevin H. Luu

## AI分析总结

# vLLM 昨日提交分析总结

## 一、主要更新类型

本次提交涵盖**Bug修复**（约8项）、**功能新增**（约5项）、**CI/测试优化**（约6项）、**前端/API改进**（约4项）、**文档更新**（2项）及**内核迁移重构**（2项），整体呈现多维度并行推进态势。

## 二、关键变更点与项目方向

1. **Pooling与Responses API完善**：多项提交（fdfa0a1、ecd600d、167858e、7dbe386、6a2a2bb）聚焦于Pooling请求处理、`max_embed_len`支持及Responses API的验证错误迁移至`VLLMValidationError`，并新增无状态`/v1/responses/render`端点。这与vLLM“人人可用的快速LLM服务”目标一致，持续强化API规范性与开发者体验。

2. **新模型支持**：新增Cohere Compass模型（70584f6），并修复Qwen3.5多模态MTP的`n_predict`解析（b339d75），以及Qwen3.8-Flash-Next的FP8索引器缓存（94e26dd）。这体现了vLLM快速适配前沿模型的承诺。

3. **硬件平台扩展**：多项提交针对XPU（Intel）与ROCm（AMD）平台，包括LoRA支持DeepSeek V4（8648446）、`grouped_topk`路由至融合`_moe_C`内核（9b85112）、AITER稀疏MLA的attention-sink支持（e476556）等。这显著拓展了vLLM的硬件生态覆盖。

4. **DSv4内核迁移**：两批提交（42801b3、1713b98）将FA4 MLA、共享CuTeDSL及序列/DCP内核迁移至新架构，属于warmup系列的第2/3批，表明vLLM正系统性地重构底层内核架构。

5. **CI/测试稳定性**：多项提交修复多节点Docker网络、增加NPU CI超时、跳过非CUDA平台不支持的测试等，持续提升开发流水线可靠性。

## 三、项目影响与潜在意义

- **API成熟度提升**：Responses API验证错误统一迁移至`VLLMValidationError`，配合`request_id`支持和`render`端点，使vLLM的OpenAI兼容层更规范、更易集成。
- **硬件覆盖扩大**：XPU与ROCm的持续适配，使vLLM不再局限于NVIDIA GPU，向“人人可用”目标迈进。
- **内核现代化**：DSv4内核迁移为未来性能优化和新硬件支持奠定基础。
- **模型生态扩展**：Cohere Compass及Qwen系列修复，保持了对最新模型架构的及时支持。

## 四、值得关注的技术点

- **KV共享层条件创建**（f2d45f2）：Gemma模型中KV投影/范数的条件创建，是内存优化的精细操作。
- **OffloadingConnector修复**（4a806d0）：停止在MTP/EAGLE推测解码下清零offload命中，涉及推测解码与内存卸载的交互正确性。
- **MooncakeStore混合模型崩溃修复**（34b1e9f）：解决finish-time保存时的混合模型崩溃，涉及分布式KV缓存管理的边界情况。
- **MXFP4选择器修复**（5893426）：停止将显式别名窄化为BF16变体，确保精度选择正确性。

## 五、对项目发展的影响

结合README所述“Easy, fast, and cheap LLM serving for everyone”的愿景，本批提交从三个维度推动项目前进：**一是易用性**——通过API规范化、验证错误统一和文档澄清，降低开发者接入门槛；**二是性能与成本**——通过内核迁移、KV缓存优化和量化修复，提升推理效率并降低硬件要求；**三是生态广度**——通过XPU/ROCm适配和新模型支持，覆盖更多硬件平台与模型架构。整体而言，vLLM正从“NVIDIA GPU上的高性能引擎”向“多硬件、多模型、标准化API的通用LLM服务平台”演进，本批提交是该战略的扎实落地。

## 详细提交记录

### [fdfa0a1](https://github.com/vllm-project/vllm/commit/fdfa0a1659a4a75de607219f9a7004d09928d572)

- **作者**: Taneem Ibrahim
- **时间**: 2026-09-07T23:55:20Z
- **提交信息**: [Pooling] Honor request_id from request bodies (#55665)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [252ed87](https://github.com/vllm-project/vllm/commit/252ed876214a0a01a6d0ce93bb5bbe77685a4160)

- **作者**: Taneem Ibrahim
- **时间**: 2026-09-07T22:12:18Z
- **提交信息**: [Bugfix] Restore Responses validation error boundary (#55761)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [537af2c](https://github.com/vllm-project/vllm/commit/537af2c3a4ba7462ddc9bc94ec7a4ea496da6d2e)

- **作者**: Kevin H. Luu
- **时间**: 2026-09-07T19:53:13Z
- **提交信息**: [CI] Recover empty multi-node Docker networks and finish partial cleanup (#55454)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Codex <noreply@openai.com>

### [58f0921](https://github.com/vllm-project/vllm/commit/58f09211dd6a21207903a02c66e924ed518b74ae)

- **作者**: Kevin H. Luu
- **时间**: 2026-09-07T19:52:36Z
- **提交信息**: [CI] Synchronize shared offload unlink test before observing pathname (#55604)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Codex <noreply@openai.com>

### [51da0ca](https://github.com/vllm-project/vllm/commit/51da0ca66c8065619c79e35dff97aa99aeaf5644)

- **作者**: Sahil Patel
- **时间**: 2026-09-07T15:15:39Z
- **提交信息**: [CI/Build] Unskip ColQwen3 multimodal pooling tests on Transformers v5 (#55588)

Signed-off-by: Sahil <sip4818@gmail.com>

### [ad2f18e](https://github.com/vllm-project/vllm/commit/ad2f18e8af18f43af932e08a3dfb7c8c068aebc2)

- **作者**: Zeyu Yang
- **时间**: 2026-09-07T14:51:09Z
- **提交信息**: [CI] reduce npu CI use time and add timeout (#55731)

Signed-off-by: yangzeyu <yangzeyu7@huawei.com>

### [70584f6](https://github.com/vllm-project/vllm/commit/70584f69b1bf866224604029fae038864a368019)

- **作者**: am-cohere
- **时间**: 2026-09-07T14:36:49Z
- **提交信息**: [Model] Add Cohere Compass model (#54774)

Signed-off-by: am-cohere <312513976+am-cohere@users.noreply.github.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [7cc89a7](https://github.com/vllm-project/vllm/commit/7cc89a7ddabd6be3ff64535139bea20548062ca6)

- **作者**: Abhi
- **时间**: 2026-09-07T14:27:07Z
- **提交信息**: [Tests] Update SarvamMLA transformers v5 compatibility reason to hf (#55728)

Signed-off-by: Abhi <108084481+Aj2280@users.noreply.github.com>
Co-authored-by: Antigravity <antigravity@google.com>

### [cd64c2d](https://github.com/vllm-project/vllm/commit/cd64c2dea9c72af333de7ec05293d54bbf1bd128)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-09-07T14:08:48Z
- **提交信息**: [Docs] Clarify admission control limits apply server-wide, not per DP rank (#55124)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [f2d45f2](https://github.com/vllm-project/vllm/commit/f2d45f26bd6a2c841ffbd0030ebaefe87c274e58)

- **作者**: Asaf Gardin
- **时间**: 2026-09-07T14:04:00Z
- **提交信息**: [Bugfix][Gemma] Conditionally create KV projections/norms on KV-shared layers (#54917)

Signed-off-by: Josephasafg <ajgard7@gmail.com>
Co-authored-by: minyichen <96753147+cyc00518@users.noreply.github.com>
Co-authored-by: aoshen02 <aoshen@inferact.ai>

### [42801b3](https://github.com/vllm-project/vllm/commit/42801b3a6b3bb92397a04117449f4699b09db1df)

- **作者**: Roberto L. Castro
- **时间**: 2026-09-07T13:36:35Z
- **提交信息**: [3/N][warmup][DSv4] Migrate FA4 MLA and shared CuTeDSL kernels (#53565)

Signed-off-by: LopezCastroRoberto <rocastro@redhat.com>
Co-authored-by: Codex <codex@openai.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [1713b98](https://github.com/vllm-project/vllm/commit/1713b9866ae5c380d97da5796217064ac7ab57b8)

- **作者**: Roberto L. Castro
- **时间**: 2026-09-07T13:35:54Z
- **提交信息**: [2/N][warmup][DSv4] Migrate sequence and DCP kernels (#53564)

Signed-off-by: LopezCastroRoberto <rocastro@redhat.com>
Co-authored-by: Codex <codex@openai.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: Lucas Wilkinson <LucasWilkinson@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [ecd600d](https://github.com/vllm-project/vllm/commit/ecd600d91e373d939ede33253a75d86bc5bf7338)

- **作者**: Taneem Ibrahim
- **时间**: 2026-09-07T13:31:40Z
- **提交信息**: [Pooling] Honor max_embed_len for chunked embeddings (#55551)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [167858e](https://github.com/vllm-project/vllm/commit/167858ea174efd0655ae821d3f3a50b51d721525)

- **作者**: Adababy
- **时间**: 2026-09-07T13:30:11Z
- **提交信息**: [Frontend] Migrate Responses harmony input validation to VLLMValidationError (#55701)

Signed-off-by: shaolila <shaolila@buaa.edu.cn>
Co-authored-by: shaolila <shaolila@buaa.edu.cn>

### [b339d75](https://github.com/vllm-project/vllm/commit/b339d75a410e4e889049dff59042f385909bad67)

- **作者**: Soumyajit Ghosh
- **时间**: 2026-09-07T13:28:26Z
- **提交信息**: [Bugfix][Spec Decode] Resolve n_predict from text_config for Qwen3.5 multimodal MTP (#55369)

Signed-off-by: SOUMYAJIT GHOSH <23051387@kiit.ac.in>
Signed-off-by: Soumyajit Ghosh <jobsoumyajit6124@gmail.com>
Co-authored-by: SOUMYAJIT GHOSH <23051387@kiit.ac.in>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [6a2a2bb](https://github.com/vllm-project/vllm/commit/6a2a2bb02b563b83f946012959fd3927984d072a)

- **作者**: Francisco Javier Arceo
- **时间**: 2026-09-07T12:50:42Z
- **提交信息**: [Frontend] Add stateless /v1/responses/render endpoint (#50195)

Signed-off-by: Francisco Javier Arceo <farceo@redhat.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [5e6f6a8](https://github.com/vllm-project/vllm/commit/5e6f6a8ed42fd420ef206b938e3bb48739a95d6c)

- **作者**: Artur Fierka
- **时间**: 2026-09-07T12:20:17Z
- **提交信息**: [Bugfix][Quantization][XPU] Fix moe_wna16 linear weight loading (#52651)

Signed-off-by: Artur Fierka <artur.fierka@intel.com>

### [4a806d0](https://github.com/vllm-project/vllm/commit/4a806d08ee94b35356dd749bf814ee91ee93f8d0)

- **作者**: Kam Basra
- **时间**: 2026-09-07T12:16:05Z
- **提交信息**: [Bugfix] OffloadingConnector: stop zeroing offload hits under MTP/EAGLE spec decode (#52771)

Signed-off-by: Kam Basra <kameldipbasra@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [94e26dd](https://github.com/vllm-project/vllm/commit/94e26dd3dd7d6363b524c96521c78feb501bdc61)

- **作者**: Thien Tran
- **时间**: 2026-09-07T12:15:45Z
- **提交信息**: [Qwen3.8-Flash-Next] Support FP8 indexer cache for QSA (#54890)

Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>

### [58ad1f3](https://github.com/vllm-project/vllm/commit/58ad1f3b8973b23943107b51230d594050b42ec3)

- **作者**: Sean Westfall
- **时间**: 2026-09-07T09:56:49Z
- **提交信息**: [Docs] Add OLMo 2 to batch-invariance tested models (#55691)

Signed-off-by: Sean Westfall <sean.westfall@gmail.com>

### [8648446](https://github.com/vllm-project/vllm/commit/86484465153f08f4523d8be964fd6309146eab09)

- **作者**: Chaojun Zhang
- **时间**: 2026-09-07T09:44:12Z
- **提交信息**: [XPU][LoRA] Support LoRA for DeepSeek V4 on XPU (#53689)

Signed-off-by: Chaojun Zhang <chaojun.zhang@intel.com>

### [9b85112](https://github.com/vllm-project/vllm/commit/9b85112e130d8beffe9928ec0c86a4029d6ba7a8)

- **作者**: Marceli Fylcek
- **时间**: 2026-09-07T09:43:38Z
- **提交信息**: [XPU] Route grouped_topk to the fused _moe_C kernel on XPU (#53580)

Signed-off-by: Marceli Fylcek <marceli.fylcek@intel.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [7dbe386](https://github.com/vllm-project/vllm/commit/7dbe38683325126de96d442d6b494f4266001bec)

- **作者**: Adababy
- **时间**: 2026-09-07T09:33:51Z
- **提交信息**: [Frontend] Migrate Responses API validation errors to VLLMValidationError (#50257)

Signed-off-by: shaolila <shaolila@buaa.edu.cn>
Co-authored-by: shaolila <shaolila@buaa.edu.cn>

### [e476556](https://github.com/vllm-project/vllm/commit/e476556189506df612218c0888dc675e6ecbfc06)

- **作者**: Andreas Karatzas
- **时间**: 2026-09-07T09:26:47Z
- **提交信息**: [ROCm][CI] Add attention-sink support to ROCm AITER sparse MLA (#54404)

Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>
Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [392db56](https://github.com/vllm-project/vllm/commit/392db567b260cb4d1e5f91547b65d527038fe641)

- **作者**: Chaojun Zhang
- **时间**: 2026-09-07T08:57:15Z
- **提交信息**: [CI] [Test] skip test_wna16_cuda_high_bit_skips_humming on non-CUDA platforms (#55660)

Signed-off-by: Chaojun Zhang <chaojun.zhang@intel.com>

### [49eb2ac](https://github.com/vllm-project/vllm/commit/49eb2accf0610d220f451f2f3c1dfe93fe395c79)

- **作者**: AlexHuang
- **时间**: 2026-09-07T08:19:07Z
- **提交信息**: [KVConnector] Guard lmcache_mp_connector state transition with num_external_tokens (#47505)

Signed-off-by: Alex <alex.tech.lab@outlook.com>
Signed-off-by: Alex-ai-future <Alex-ai-future@users.noreply.github.com>

### [5893426](https://github.com/vllm-project/vllm/commit/5893426b88f7b3cd21101d194eb1c6f0a6f0e27b)

- **作者**: Gabriel Wu
- **时间**: 2026-09-07T07:19:13Z
- **提交信息**: [Bugfix] DSv4 MXFP4 selector: stop narrowing explicit aliases to their BF16 variant (#53586)

Signed-off-by: Zihua Wu <zihuaw@nvidia.com>
Signed-off-by: Zihua Wu <13583761+lucifer1004@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Jee Jee Li <pandaleefree@gmail.com>
Co-authored-by: Yongye Zhu <zyy1102000@gmail.com>

### [34b1e9f](https://github.com/vllm-project/vllm/commit/34b1e9f7a61e802b870c7d7f78bf90b000b691cc)

- **作者**: Zhewen Li
- **时间**: 2026-09-07T07:18:30Z
- **提交信息**: [Bugfix][MooncakeStore] Fix finish-time save crash on hybrid models (#54643)

Signed-off-by: zhewenl <zhewenl@users.noreply.github.com>
Co-authored-by: zhewenl <zhewenl@users.noreply.github.com>

### [195bc9c](https://github.com/vllm-project/vllm/commit/195bc9c4a1b480c7d2a6131cd8dbb49e9be72762)

- **作者**: Andreas Karatzas
- **时间**: 2026-09-07T07:17:36Z
- **提交信息**: [CI][ROCm] Temporarily skip unsupported HY-V4 initialization (#55653)

Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-09-08
**监控日期**: 2026-09-07
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 6704
- **最后更新**: 2026-09-08T00:09:00Z

## 提交统计

- **昨日提交总数**: 13
- **提交者数量**: 11
- **主要提交者**: 汪志鹏, Anjie Hou, summer

## AI分析总结

# vLLM-Omni 昨日提交分析报告

## 一、主要更新类型

本次提交以 **Bug修复** 为主（约8项），其次是 **性能优化**（3项）、**功能新增**（1项）和 **文档更新**（1项）。修复范围覆盖多个模型和硬件平台，体现了项目在多模态推理服务方面的持续完善。

## 二、关键变更点与项目方向的关系

**Cosmos3 模型相关修复最为集中**，涉及分布式传输输出、图像数组可写性、Ulysses序列自动填充以及视频API控制上传等多个方面。这表明 Cosmos3 作为视频生成模型正在快速迭代成熟，项目正着力解决其在分布式环境下的稳定性问题。

**MiniMax-H3 的修复**（NPU INT8量化分发、关键帧VAE编码稳定性）与 **MiniCPM-o 的音频特征长度处理** 共同反映了项目对多模态模型（视频、音频）推理质量的持续打磨。

**Wan VAE 流式传输** 和 **LTX Ulysses序列并行优化** 是重要的性能改进方向，直接服务于视频生成场景的实时性和效率提升。

**LoRA权重驻留优化** 针对扩散模型的激活周期管理，减少重复加载开销，属于推理性能的关键优化。

## 三、项目影响与潜在意义

这些提交显著提升了 vLLM-Omni 在**视频生成、多模态理解**等核心场景的稳定性和性能。Cosmos3 和 MiniMax-H3 的密集修复表明项目正在快速吸收并稳定支持最新的视频生成模型。NPU 平台的 INT8 量化修复则体现了项目对**多硬件生态**的重视，有助于扩大用户基础。

## 四、值得关注的技术点

1. **Ulysses序列并行** 在视频生成中的适配与自动填充策略，是分布式推理的关键技术细节
2. **流式VAE分块传输** 设计，对降低视频生成首token延迟有直接帮助
3. **LoRA权重的跨激活周期驻留** 机制，是扩散模型服务化的重要优化手段
4. **请求批处理键的规范化**（如cache_backend、guidance_scale参数），体现了对缓存一致性和批处理正确性的细致考量

## 五、对项目发展的影响

vLLM-Omni 定位于“人人可用的多模态模型服务”，本批提交通过修复多模型、多硬件平台的推理问题，并优化视频生成性能，**显著推进了项目的成熟度和可用性**。特别是对 Cosmos3、MiniMax-H3 等前沿视频模型的快速适配，有助于项目在视频生成服务领域建立竞争优势。文档更新（扩散运行时模块设计）则表明项目在架构规范化方面持续投入，为后续扩展奠定基础。整体来看，项目正处于**功能完善与性能调优并重**的快速发展阶段。

## 详细提交记录

### [6942a5b](https://github.com/vllm-project/vllm-omni/commit/6942a5b600375998ecbfcb6d120585283542af17)

- **作者**: Anjie Hou
- **时间**: 2026-09-07T23:41:13Z
- **提交信息**: [1/N] Stream Wan VAE chunks to the media consumer (#7016)

Signed-off-by: specture724 <specture724@gmail.com>
Co-authored-by: Claude Sonnet 5 <noreply@anthropic.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [3b33581](https://github.com/vllm-project/vllm-omni/commit/3b335814cc5aa9cd836a95e6b97edb5ddf9c3193)

- **作者**: Rahul Steiger
- **时间**: 2026-09-07T23:34:08Z
- **提交信息**: [Bugfix][Cosmos3] Fix distributed Transfer output envelope (#7205)

Signed-off-by: Rahul Steiger <rsteiger@nvidia.com>
Co-authored-by: Nils Hoffmann <nhoffmann@nvidia.com>

### [cf36f5e](https://github.com/vllm-project/vllm-omni/commit/cf36f5e4748c87a9bf10e744854fa69a66463561)

- **作者**: Pujitha Paladugu
- **时间**: 2026-09-07T15:51:13Z
- **提交信息**: [Bugfix][MiniCPM-o] Allow ragged audio_feature_lens across a batch (#7071)

Signed-off-by: Pujitha Paladugu <10557236+pujitha24@users.noreply.github.com>
Co-authored-by: Pujitha Paladugu <10557236+pujitha24@users.noreply.github.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [7be014b](https://github.com/vllm-project/vllm-omni/commit/7be014bce6374f06c95b703763bdbac4c6198f31)

- **作者**: Lei Ke
- **时间**: 2026-09-07T14:50:44Z
- **提交信息**: [Bugfix][NPU] Fix MiniMax-H3 INT8 quantization dispatch (#6876)

Signed-off-by: KrystalRay <keeleiray@gmail.com>
Co-authored-by: KrystalRay <keeleiray@gmail.com>

### [9b6a308](https://github.com/vllm-project/vllm-omni/commit/9b6a308914cf649134ccaf43879fd19a2f43cc51)

- **作者**: 汪志鹏
- **时间**: 2026-09-07T14:27:24Z
- **提交信息**: [Perf][Diffusion] Keep LoRA weights resident across activation cycles (#7195)

Signed-off-by: princepride <wangzhipeng628@gmail.com>

### [30d6a0b](https://github.com/vllm-project/vllm-omni/commit/30d6a0b4e61cb02cbdf11056c48bcc04376c7b22)

- **作者**: WeiQing Chen
- **时间**: 2026-09-07T13:52:54Z
- **提交信息**: [Bugfix][MiniMax-H3] Stabilize keyframe VAE encoding (#7191)

Signed-off-by: david6666666 <530634352@qq.com>
Signed-off-by: David Chen <530634352@qq.com>

### [4b96c57](https://github.com/vllm-project/vllm-omni/commit/4b96c57730e8ea83cf51a6ef66e29aa688b8592d)

- **作者**: Zeyu Huang | 黃澤宇
- **时间**: 2026-09-07T13:52:24Z
- **提交信息**: [skip ci][Doc] Module design doc for diffusion runtime (#6440)

Signed-off-by: Huang, Zeyu <11222265+fhfuih@users.noreply.github.com>
Co-authored-by: Alicia <115451386+congw729@users.noreply.github.com>

### [3204a0b](https://github.com/vllm-project/vllm-omni/commit/3204a0b2ade0f05424b7f11e3bcc03cb3542e0c6)

- **作者**: Mu GuanLin
- **时间**: 2026-09-07T10:48:26Z
- **提交信息**: [Model][Perf] Optimize LTX Ulysses sequence parallelism (#7079)

Signed-off-by: mglyn <1203789601@qq.com>

### [f080f41](https://github.com/vllm-project/vllm-omni/commit/f080f41e031e3876f45e42b62bf7fb4b8f1f5d8a)

- **作者**: Rahul Steiger
- **时间**: 2026-09-07T08:58:28Z
- **提交信息**: [Bugfix][Cosmos3] Auto-pad non-divisible Ulysses GEN sequences (#6918)

Signed-off-by: Rahul Steiger <rsteiger@nvl72d188-T17.cm.cluster>
Co-authored-by: Rahul Steiger <rsteiger@nvl72d188-T17.cm.cluster>

### [85b0bad](https://github.com/vllm-project/vllm-omni/commit/85b0bad2d3fbc63b5c674e148e4030c442f04f0b)

- **作者**: FredHuangNV
- **时间**: 2026-09-07T08:38:56Z
- **提交信息**: [Frontend][Model] Add Cosmos3 control uploads to video API (#7027)

Signed-off-by: Fred Huang <frhuang@nvidia.com>

### [677265b](https://github.com/vllm-project/vllm-omni/commit/677265b64b7870374705f18e81579c9d6e5ec8c7)

- **作者**: Rahul Steiger
- **时间**: 2026-09-07T08:06:16Z
- **提交信息**: [Bugfix][Diffusion] Make Cosmos3 transfer image arrays writable (#6915)

Signed-off-by: Rahul Steiger <rsteiger@nvl72d179-T17.cm.cluster>
Co-authored-by: Rahul Steiger <rsteiger@nvl72d179-T17.cm.cluster>
Co-authored-by: Rahul Steiger <rsteiger@aws-cmh-slurm-1-vscode-04.cm.cluster>

### [91dfafc](https://github.com/vllm-project/vllm-omni/commit/91dfafcaab9c400f4dc504d2a9d0be09cbf59603)

- **作者**: Shenglei Fu
- **时间**: 2026-09-07T07:58:19Z
- **提交信息**: [Bugfix][Diffusion] Include guidance_scale_2_provided in the request-batch key (#7078)

Signed-off-by: Shenglei Fu <sfu@confluent.io>
Co-authored-by: Claude <noreply@anthropic.com>

### [4b81f69](https://github.com/vllm-project/vllm-omni/commit/4b81f692d1efa9b4f2a4f6777e47f471a3b6d383)

- **作者**: summer
- **时间**: 2026-09-07T07:56:51Z
- **提交信息**: [Bugfix][Diffusion] Canonicalize cache_backend=None to "none" (#7041)

Signed-off-by: summer <128961079+zhang-keliang@users.noreply.github.com>
Co-authored-by: Alicia <115451386+congw729@users.noreply.github.com>

---
