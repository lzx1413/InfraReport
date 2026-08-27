# GitHub Stars 合并报告 - 2026-08-26

**合并日期**: 2026-08-27
**监控日期**: 2026-08-26
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


**报告日期**: 2026-08-27
**监控日期**: 2026-08-26
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2173
- **最后更新**: 2026-08-26T09:23:31Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Bin Jia

## AI分析总结

### 提交分析总结

**1. 主要更新类型**  
本次提交为**功能新增**，核心是引入面向 DeepSeek-V4 的上下文并行（Context Parallel）基础设施，属于分布式训练能力的关键扩展。

**2. 关键变更点与项目方向**  
- 新增上下文并行基础设施，专门针对 DeepSeek-V4 模型架构优化。  
- 与 VeOmni 的“模型中心化分布式训练配方库”定位高度一致，旨在通过可复用的并行策略支持任意模态模型的高效扩展。  
- 该功能直接服务于长序列训练场景，是当前大模型（尤其是多模态）训练中解决显存与计算瓶颈的核心手段。

**3. 对项目的影响与潜在意义**  
- **扩展模型支持范围**：使 VeOmni 能够适配 DeepSeek-V4 这类超长上下文模型，提升配方库的通用性和吸引力。  
- **增强分布式能力**：上下文并行是训练超长序列的关键技术，该基础设施的加入将显著提升项目在工业级训练场景中的实用性。  
- **社区吸引力**：针对热门模型（DeepSeek-V4）的专项支持，可能吸引更多开发者关注和贡献，加速生态建设。

**4. 值得关注的技术点**  
- **上下文并行实现细节**：需关注其如何切分序列、通信模式（如环形/树形）及与现有张量/流水线并行的协同方式。  
- **DeepSeek-V4 适配性**：是否针对其注意力机制（如 MLA）或 MoE 结构做了定制优化，这直接影响性能上限。  
- **可扩展性设计**：基础设施是否模块化，能否快速迁移到其他长上下文模型（如 Qwen、Llama 变体）。

**5. 对项目发展的影响**  
- **战略契合**：VeOmni 的愿景是“任意模态模型训练配方库”，本次提交通过支持前沿模型（DeepSeek-V4）的并行策略，强化了其作为“分布式训练解决方案”的技术壁垒。  
- **生态演进**：上下文并行基础设施的成熟将吸引更多模型适配，逐步形成“模型-策略-硬件”闭环，推动项目从论文原型走向生产级工具。  
- **潜在风险**：若实现仅针对 DeepSeek-V4 硬编码，可能降低通用性；需观察后续是否抽象为通用组件。  

**总结**：本次提交是 VeOmni 在分布式训练能力上的重要里程碑，直接响应了长序列模型训练需求，既巩固了技术领先性，也为社区扩展奠定了基础。后续应关注其通用化程度及性能基准测试结果。

## 详细提交记录

### [1d5651f](https://github.com/ByteDance-Seed/VeOmni/commit/1d5651fcb9d569441188395a1a23bc79fb7edb62)

- **作者**: Bin Jia
- **时间**: 2026-08-26T09:16:54Z
- **提交信息**: [dist, parallel, ci] feat: context-parallel infrastructure for DeepSeek-V4 (#1111)

Co-authored-by: Cursor <cursoragent@cursor.com>

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-08-27
**监控日期**: 2026-08-26
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2733
- **最后更新**: 2026-08-26T19:47:13Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 3
- **主要提交者**: Shiqiao Gu (谷石桥), Xin Qiu, STwangyingrui

## AI分析总结

### 1. 主要更新类型
- **功能新增**：为MiniMax-H3模型引入DiT预/后权重常驻加速器的可选特性，并新增convrot-int8量化支持。
- **配置更新**：更新MiniMax-H3的int8量化配置文件。
- **文档更新**：补充Intel XPU技能文档及分布式推理文档。

### 2. 关键变更点与项目方向
- **权重驻留优化**：允许DiT预/后权重跨请求常驻加速器，而Transformer块仍使用块级卸载。该设计在默认行为不变的前提下，减少重复传输开销，同时兼容动态LoRA切换，契合LightX2V“轻量高效推理”的核心目标。
- **convrot-int8支持**：新增卷积旋转位置编码的int8量化路径，扩展模型量化覆盖范围，强化框架对低精度推理的适配能力。
- **配置与文档同步**：更新配置文件确保新特性开箱即用，XPU文档完善则提升跨硬件平台的可操作性，与项目多后端支持策略一致。

### 3. 对项目的影响与潜在意义
- **性能提升**：权重驻留可显著降低长序列或多请求场景下的I/O开销，尤其利于服务端持续推理场景。
- **生态扩展**：convrot-int8与XPU文档完善，降低用户在新硬件或新模型上的部署门槛，吸引更广泛社区采用。
- **稳定性保障**：默认行为不变的设计确保现有用户无感升级，动态LoRA兼容性则避免功能冲突，提升框架健壮性。

### 4. 值得关注的技术点
- **混合驻留策略**：区分DiT权重与Transformer块的卸载策略，体现对模型结构差异的精细化内存管理，是推理优化的典型实践。
- **量化路径扩展**：convrot-int8需处理旋转位置编码与量化协同的数值稳定性，其实现质量直接影响生成质量。
- **配置驱动特性开关**：通过JSON配置启用新功能，保持代码简洁的同时提供灵活性，符合工程化最佳实践。

### 5. 对项目发展的影响
LightX2V定位为轻量视频生成推理框架，本次提交在三个维度强化其竞争力：**性能**（权重驻留）、**兼容性**（int8+XPU）、**易用性**（配置与文档）。这些更新不仅直接提升MiniMax-H3的推理效率，更通过模块化设计为其他模型复用铺路，推动框架向“多模型、多硬件、多精度”的通用推理平台演进。文档完善则有助于吸引开发者贡献，形成良性生态循环。整体上，提交体现了项目在优化推理路径与扩展硬件支持上的持续投入，符合其“轻量高效”的长期愿景。

## 详细提交记录

### [b220e26](https://github.com/ModelTC/LightX2V/commit/b220e26198fc90769114b6751236be96a3838069)

- **作者**: STwangyingrui
- **时间**: 2026-08-26T11:24:40Z
- **提交信息**: feat(minimax_h3): keep DiT pre/post weights resident (#1443)

Keep MiniMax-H3 DiT pre/post weights on the accelerator across requests
while transformer blocks continue using block offload. The opt-in
setting removes repeated pre/post transfers without changing the default
behavior and remains compatible with dynamic LoRA switching.

### [3b027ff](https://github.com/ModelTC/LightX2V/commit/3b027ff850ff7a0f98e665996290d9bee70f9c57)

- **作者**: Shiqiao Gu (谷石桥)
- **时间**: 2026-08-26T11:18:51Z
- **提交信息**: Update minimax_h3_int8_convrot_8step.json (#1444)

### [b753fe3](https://github.com/ModelTC/LightX2V/commit/b753fe31895a72eed95a0023b881e14b031a65a2)

- **作者**: Shiqiao Gu (谷石桥)
- **时间**: 2026-08-26T10:16:21Z
- **提交信息**: add convrot-int8 (#1441)

### [83dcebe](https://github.com/ModelTC/LightX2V/commit/83dcebe33d1ce8e7a10ab7ef60d4ca5a34347c9e)

- **作者**: Xin Qiu
- **时间**: 2026-08-26T09:15:36Z
- **提交信息**: docs(xpu): update Intel XPU skill docs, and add dist_infer docs (#1436)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-08-27
**监控日期**: 2026-08-26
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2212
- **最后更新**: 2026-08-26T23:29:12Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-08-27
**监控日期**: 2026-08-26
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 6252
- **最后更新**: 2026-08-27T01:27:12Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 4
- **主要提交者**: Ka-Hyun Nam, RuQing Xu, Zixin Huang

## AI分析总结

## 提交分析总结

### 1. 主要更新类型
本批4个提交涵盖**性能优化**（1个）、**Bug修复**（3个），无新增功能或文档更新。

### 2. 关键变更点及与项目方向的关系

- **性能优化**：`act_and_mul_kernel`（激活函数与乘法融合核）通过将线程块大小上限从1024降至256，在B200上实现大隐藏维度（d=8192）下17-19%的加速。该核服务于`silu_and_mul`/`gelu_and_mul`等常用激活函数，直接提升LLM FFN层性能。

- **CI修复**：跳过夜间发布中因缺少仓库专属配置文件而失败的CUDA配置一致性测试，保持源码树预提交检查的完整性。

- **KDA内核回退修复**：解决CuTe DSL版本低于4.7时`recurrent_kda`预填充内核因缺少`cutlass.experimental`命名空间而崩溃的问题，新增探测函数并激活已有的Cake回退路径。

- **FMHA缩放参数接线修复**：将`scale_qkvo`正确接入CuTe DSL FMHA后端，此前因量化支持缺失被禁止，现随FP8量化变体就绪而成为必要前提。

### 3. 对项目的影响和潜在意义

这些修复共同提升了FlashInfer作为**高性能GPU推理内核库**的稳定性和兼容性。性能优化直接增强核心推理路径效率；KDA回退修复避免了特定环境下的硬崩溃；FMHA缩放接线为FP8量化推理铺平道路；CI修复保障了发布流程可靠性。

### 4. 值得关注的技术点

- **占用率优化策略**：通过降低线程块大小而非增加并行度来提升SM驻留块数，利用已有block-stride循环弥补，是典型的寄存器压力与占用率权衡。
- **版本兼容性探测**：以命名空间存在性作为功能可用性判据，实现优雅降级而非硬失败。
- **`__launch_bounds__(256)`**：显式告知编译器寄存器分配上限，避免为更大块预留资源。

### 5. 对项目发展的影响

作为面向推理场景的高性能GPU内核库，本批提交体现了**性能极致优化**与**生态兼容性**并重的发展策略：一方面通过微调内核配置榨取硬件性能，另一方面确保在不同CUDA/CuTe DSL版本环境下稳定运行，并逐步完善FP8量化支持——这些都是FlashInfer在LLM推理竞争中保持领先地位的关键方向。

## 详细提交记录

### [9caa448](https://github.com/flashinfer-ai/flashinfer/commit/9caa4488a485bb34ac05a065b694b28ca21b2b4e)

- **作者**: Zixin Huang
- **时间**: 2026-08-26T23:08:54Z
- **提交信息**: perf(activation): cap act_and_mul_kernel block size for ~17-19% speedup at large hidden dims (#4733)

## Description

**~17-19% faster `act_and_mul_kernel`** (used by `silu_and_mul` /
`gelu_and_mul` /
`gelu_tanh_and_mul`) **at large hidden dims** — measured 1.17x–1.19x at
`d=8192` on NVIDIA B200
(see Performance Results below) — by capping the kernel's thread block
size instead of letting it
scale up to 1024 threads.

`act_and_mul_kernel` sizes its thread block directly off the hidden
dimension:
`blockDim = min(d / vec_size, 1024)`. For large hidden sizes (e.g.
`d=8192`, a common LLM FFN
width), this drives the block to 1024 threads, raising per-block
register pressure enough to limit
how many blocks can be resident on an SM at once.

The kernel body already contains a block-stride loop over `d /
vec_size`, so it doesn't need one
thread per element — capping the block size and letting that existing
loop iterate more is enough
to improve occupancy/DRAM throughput, with no change to kernel
semantics.

What changed:
1. `flashinfer/jit/activation.py`: cap `blockDim` at 256 instead of
scaling up to 1024 for large `d`.
   For small `d` (`d / vec_size < 256`), behavior is unchanged.
2. `include/flashinfer/activation.cuh`: add `__launch_bounds__(256)` so
the compiler doesn't need to
   plan register allocation for a larger block.

## Related Issues

No existing issue tracks this specific problem. Two other open PRs touch
nearby code in the same
kernel and may be worth cross-checking for conflicts: #2613
(non-power-of-2 `vec_size` handling)
and #2720 (rewrites the PDL/`griddepcontrol` block). Neither overlaps
with this fix's specific
change (block-size capping), but both touch the same function.

## Pre-commit Checks
- [ ] Ran `pre-commit run -a`

## Performance Results

**Testing environment:** NVIDIA B200 (SM100a), fp16.

| shape (tokens × hidden) | before | after | speedup |
|---|---|---|---|
| 16384 × 8192 | 139.3us (DRAM 72.7%, occupancy 84.0%) | 119.3us (DRAM
84.5%, occupancy 88.7%) | 1.17x |
| 4096 × 8192 | 34.6us (DRAM 64.9%, occupancy 82.9%) | 29.0us (DRAM
75.6%, occupancy 82.9%) | 1.19x |

2/2 measured shapes improved, no regressions observed. The 16384×8192
gain comes from both higher
occupancy and higher DRAM throughput; the 4096×8192 gain is from higher
DRAM throughput at
unchanged occupancy — the underlying mechanism is "more/better-scheduled
blocks per SM," which
doesn't always show up as an occupancy-metric change.

Both configurations compiled to 32 registers/thread on the toolchain
used here; the exact register
count (and therefore the exact gain) will vary by CUDA/compiler version.
This change should not
regress any shape — it only shrinks the block size in a regime where the
old size already exceeded
what was needed for full occupancy, and small-`d` shapes are unaffected.

## Key Limitations
- Only one GPU SKU (B200) tested; not verified on Hopper/SM90 or SM120,
though the change is
architecture-agnostic (host-side launch config only, no kernel math
changed).
- Only 2 shapes profiled with Nsight Compute; broader shape sweep not
run.
- No new test added — this is a launch-config-only change exercised by
the existing test suite's
  coverage, not a new code path.

## Tests
- [x] `pytest tests/utils/test_activation.py` — all `dim` values
(128–16384) × `silu_and_mul` /
  `gelu_tanh_and_mul` pass against the PyTorch reference.

## Reviewer Notes
@yzh119 — this touches the launch-config code from #930. @cyx-6 — most
recent author of this
function. @bkryu — you're an auto-requested reviewer on #2613 which
touches the same kernel,
flagging in case of overlap.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Performance**
* Optimized activation and elementwise multiplication kernels by
adjusting their launch configuration.
  * Preserved existing kernel behavior and results.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [e4b7fa4](https://github.com/flashinfer-ai/flashinfer/commit/e4b7fa4b7c3ba5e17286d9c59f2bcf2ca07e0a6d)

- **作者**: Jonathan Dierksen
- **时间**: 2026-08-26T21:25:43Z
- **提交信息**: fix(ci): skip source-only CUDA config test in nightlies (#4750)

## 📌 Description

Keep `test_supported_jit_cache_versions_match_cuda_config` active in
source-tree presubmit runs, but skip it when `ci/cuda-versions.json` is
intentionally absent from the isolated installed-package layout used by
Nightly Release.

This fixes the identical cu129/cu130 shard 5 failures in Nightly Release
#360 without copying repository-only CI metadata into the
installed-package test directory.

## 🔍 Related Issues

- Nightly Release #360:
https://github.com/flashinfer-ai/flashinfer/actions/runs/32920335499

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

Validation performed:

- `python3 -m compileall -q tests/cli/test_cli_cmds.py`
- `pre-commit run --files tests/cli/test_cli_cmds.py`
- `git diff --check`

Targeted pytest was not run locally because the existing repository
virtualenv does not contain a usable pytest installation. PR CI should
confirm both the source-tree pass and isolated-nightly skip behavior.

## Reviewer Notes

The test still protects the duplicated CLI/config CUDA-version invariant
during presubmit. The skip applies only when the repository-only
`ci/cuda-versions.json` file is unavailable, as it is in the Nightly
Release installed-wheel test directory.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Tests**
  * Improved CUDA version consistency testing.
* Tests now skip gracefully when the required configuration file is
unavailable.
  * Added support for running tests with `pytest`.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [919a24e](https://github.com/flashinfer-ai/flashinfer/commit/919a24e5b1d971d50c97a3cd38862f801527eab5)

- **作者**: Ka-Hyun Nam
- **时间**: 2026-08-26T18:02:55Z
- **提交信息**: fix(kda): fall back to Cake when CuTe DSL predates cutlass.experimental (#4667)

## 📌 Description

The BT=16 recurrent KDA prefill kernel added in #4605 is built on
`cutlass.experimental`, a namespace that only exists from CuTe DSL 4.7
onwards. `_is_cute_dsl_kda_prefill_eligible` checked only the tensor
contract and the compute capability, so on SM100/SM103 with the 4.6.2
floor that `requirements.txt` still permits, an ordinary `recurrent_kda`
prefill using the default `backend="auto"` dispatched into the kernel
and failed with a bare `ModuleNotFoundError` — even though the caller
never asked for the CuTe DSL backend.

The graceful path already existed
(`test_public_prefill_auto_falls_back_to_cake` covers the ineligible
case); the probe simply had no way to know that a missing
`cutlass.experimental` is a reason to decline. This PR adds that probe:

- `is_cute_dsl_experimental_available()` in
`flashinfer/cute_dsl/utils.py`, modelled on the neighbouring
`is_rubin_cute_dsl_available()`. It probes the `cutlass.experimental`
package rather than a leaf module because the whole namespace
(`experimental.cuda`, `experimental.primitives`,
`experimental.task_scheduling`) is the 4.6.2/4.7.0 boundary, so the same
helper can gate other 4.7-only kernels.
- `_is_cute_dsl_kda_prefill_eligible` consults it, which activates the
existing Cake fallback for `backend="auto"`.
- `recurrent_kda` reports the version requirement directly when
`backend="cute-dsl"` is requested explicitly, instead of claiming the
prefill *contract* is unsupported. That report is scoped to the compute
capabilities this kernel serves, so the SM120 backend added in #4633 —
which does not use `cutlass.experimental` and runs fine on 4.6.2 — keeps
its own rejection message.

Reproduced and verified on a B200 (SM100) against a genuine cutlass-dsl
4.6.2 install.

Before, on `main`:

```
cutlass-dsl : 4.6.2
--- backend="auto"      ModuleNotFoundError: No module named 'cutlass.experimental'
--- backend="cute-dsl"  ModuleNotFoundError: No module named 'cutlass.experimental'
```

After:

```
cutlass-dsl : 4.6.2
--- backend="auto"      OK   shape=(1, 32, 2, 128) torch.bfloat16 finite=True
--- backend="cute-dsl"  ImportError: backend='cute-dsl' requires nvidia-cutlass-dsl>=4.7.0
                        (cutlass.experimental); backend='auto' falls back to Cake
```

On 4.7.0 both backends behave exactly as before.

## 🔬 Why only KDA: the 4.6.2 vs 4.7 audit

This fix came out of a wider audit of `main` against the 4.6.2 floor,
done by diffing the extracted 4.6.2 and 4.7.0 wheels and AST-parsing
every `cutlass` import in the package. Summarising it here so reviewers
can see why the change is scoped to KDA:

- **45 files import 4.7-only `cutlass.experimental` modules** across 248
import sites. 44 of them are `flashinfer/attention/prims_ts/**`; the
45th is `flashinfer/kda_kernels/kda_chunked_bt16.py`, the kernel this PR
guards.
- **`import flashinfer` is unaffected on 4.6.2.** No 4.7-only module is
reachable through module-scope imports, which was confirmed by actually
importing the package under a real 4.6.2 install.
- **PrimTS decode and MLA need no change.** Their entry points in
`flashinfer/decode.py` and `flashinfer/mla/__init__.py` are already lazy
`__getattr__` hooks, and the APIs are opt-in: nothing dispatches into
them implicitly, so on 4.6.2 they can only fail for a caller who
explicitly asked for a PrimTS kernel by name. There is no alternative
backend to fall back to, so the only possible improvement there is a
clearer message — worth doing, but it is a separate cosmetic change
rather than a correctness fix.
- **The test suite already copes.** The five PrimTS attention tests
carry `pytest.importorskip("cutlass", minversion="4.7.0")` and skip
cleanly, and `tests/trace/template_registry.py` filters unimportable
modules with `except ImportError`.

KDA was the only place where an *automatic* dispatch on a default code
path turned a missing optional dependency into a crash, which is why it
is the only behaviour changed here.

For completeness, the SM107/Rubin kernels depend on
`cutlass.utils.rubin_helpers` and `tcgen05.mma.CollectorOp`, which are
absent from both 4.6.2 and 4.7.0 (they arrive in 4.8). Those are already
gated by `is_rubin_cute_dsl_available()` and are untouched by this PR;
that existing helper is the pattern the new probe follows.

## 🔍 Related Issues

Follow-up to #4605, which introduced the CuTe DSL recurrent prefill
backend.

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

`tests/kda/` on a B200, after merging `main`: **577 passed, 112
skipped**, including the real CuTe DSL kernel tests
(`test_cute_dsl_checkpoints_match_cake`,
`test_cute_dsl_padded_indexed_state_matches_cake`). 88 of the skips are
the new SM120 suite asking for a CC 12.0 device and the rest are `fla`
not being installed; none are new here.

Also run against a genuine cutlass-dsl 4.6.2 install on the same B200,
where the fix takes `tests/kda/` from **23 failed / 410 passed** to **9
failed / 424 passed**. The 9 remaining are pre-existing tests that drive
the CuTe DSL API directly and have no version guard; they fail
identically before this PR and are left alone here.

Added `test_prefill_without_cute_dsl_experimental_falls_back_to_cake`,
which runs on ordinary 4.7.0 CI by simulating the older DSL through the
probe. It computes a reference through the real CuTe DSL kernel, then
forces the probe false and patches `_run_cute_dsl_kda_prefill` to
`pytest.fail`, so it asserts the routing actually changed rather than
only that the numbers match; it then checks the fallback output against
the reference and that the explicit backend raises.

## Reviewer Notes

The probe lives inside `_is_cute_dsl_kda_prefill_eligible` rather than
as a separate gate in `recurrent_kda`. A standalone gate reads more
cleanly, but the existing routing tests monkeypatch the eligibility
function to exercise dispatch on CPU tensors, and an ungated check in
`kda.py` would have made those pure-Python tests require cutlass >= 4.7
to run at all.

Within that function the probe runs *after* the contract checks rather
than before them. That ordering is deliberate: it confines the probe to
calls that would have imported the kernel anyway, so anything rejected
on tensor shape, dtype or compute capability reaches Cake by exactly the
path it did before this PR.

One consequence worth naming: on an old DSL the version error takes
precedence, so an explicit `backend="cute-dsl"` call on an SM100-family
device that *also* violates the kernel contract is told to upgrade and
only sees the contract error afterwards. Reporting both would mean
evaluating the contract and the runtime separately at the dispatch site,
which would make the existing CPU-only routing tests depend on cutlass
>= 4.7. The upgrade is a genuine prerequisite either way, so the message
is incomplete rather than wrong.

That precedence is why `_is_cute_dsl_kda_prefill_dsl_too_old` takes the
compute capability into account instead of reusing the bare runtime
probe at the dispatch site. `main` now tries the SM120 backend first and
records its rejection reason for the shared explicit-backend error, so
an unscoped version check would have replaced that reason with an
irrelevant upgrade instruction on CC 12.0.
`test_dsl_version_guard_is_scoped_to_the_sm100_family` pins the scoping
for CC 10.0, 10.3 and 12.0 without needing any of those devices.

`_is_cute_dsl_kda_runtime_available` imports the helper lazily inside a
`try`: `flashinfer/cute_dsl/utils.py` imports `cutlass` at module scope,
and `kda_prefill_cute.py` deliberately keeps the DSL stack off the
import path.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

- **Bug Fixes**
  - Improved error handling when the CuTe DSL backend is unavailable.
  - Added clear installation guidance for the required CuTe DSL version.
- Preserved contract-specific validation errors when the runtime is
available.
- Improved automatic fallback behavior for eligible recurrent KDA
prefill operations.

- **Documentation**
- Clarified CuTe DSL runtime requirements and fallback behavior in the
API documentation.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [b045865](https://github.com/flashinfer-ai/flashinfer/commit/b0458658677d24681a96a246f2c922152b9225d9)

- **作者**: RuQing Xu
- **时间**: 2026-08-26T16:54:49Z
- **提交信息**: fix: Correctly wire scale_qkvo to cute-dsl fmha backends (#4665)

<!-- .github/pull_request_template.md -->

## 📌 Description

Correctly wire scale_qkvo to cute-dsl fmha backends.

`scale_q`, `scale_k`, and `scale_v` was forbidden previously because
modular CuTeDSL FMHA didn't support quantization. Now we have multiple
variants with FP8 quantization support, so this wiring becomes a hard
prerequisite.

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

- **Bug Fixes**
- Improved FP8 scale handling for dense and causal attention operations.
  - Corrected value and output scaling during attention computation.
- Clarified validation behavior for unsupported scaling options in
modular attention execution.
- Ensured scaled attention results remain accurate across supported
execution modes.
- **Tests**
- Expanded verification to cover scaled outputs and log-sum-exp results.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-08-27
**监控日期**: 2026-08-26
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4076
- **最后更新**: 2026-08-26T22:37:43Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 2
- **主要提交者**: Raghav K, KyleNeverGivesUp

## AI分析总结

# FastVideo 提交分析报告

## 主要更新类型

本次提交全部为**性能优化**（perf），无功能新增、Bug修复或文档更新，体现了项目当前阶段对推理效率的集中攻关。

## 关键变更点

1. **统一内存架构下的Offload路径优化**：在支持统一内存的硬件（如GB10）上，禁用所有CPU offload路径，避免不必要的内存拷贝开销。
2. **检查点加载优化**：DiT模型加载时不再持有整个checkpoint，改为流式/分块加载，大幅降低峰值内存占用。
3. **VSA Triton内核调优**：扩展autotune的num_stages搜索范围，使编译器能找到更优的流水线配置。
4. **文本编码器offload跳过**：在统一内存环境下，跳过文本编码器的CPU offload，将耗时从5分49秒降至30毫秒。

## 与项目方向的关系

FastVideo定位为**高效视频生成框架**，核心目标是降低推理门槛、提升生成速度。这四项优化均围绕**MiniMax H3模型在单块GB10（NVIDIA Grace Blackwell）上的部署**展开，直接服务于“在消费级/边缘硬件上运行先进视频模型”的项目愿景。GB10是统一内存架构，传统CPU offload策略反而成为瓶颈，团队针对该硬件特性进行了精准适配。

## 项目影响与潜在意义

- **硬件适配里程碑**：使MiniMax H3首次能在单GB10上完成生成，大幅降低硬件门槛，扩大潜在用户群。
- **性能数量级提升**：文本编码器优化带来近千倍加速（349秒→0.03秒），显著改善用户体验。
- **内存占用优化**：checkpoint流式加载使大模型在受限内存设备上可运行，为后续更多模型适配奠定基础。
- **生态扩展**：这些优化可能吸引更多开发者在边缘设备上探索视频生成，推动社区发展。

## 值得关注的技术点

1. **统一内存感知的优化策略**：团队没有盲目套用传统offload方案，而是识别出统一内存架构下“offload反而有害”的反直觉现象，体现了对硬件特性的深入理解。
2. **加载路径的内存工程**：避免持有完整checkpoint是系统级优化，涉及数据流重构，而非简单参数调整。
3. **Triton autotune范围扩展**：说明默认搜索空间可能不覆盖最优配置，需要针对特定硬件和模型进行扩展。
4. **优化协同性**：四项优化相互配合——先解决内存瓶颈（checkpoint加载），再消除不必要的拷贝（offload禁用），最后微调内核（num_stages），形成完整的优化链条。

## 对项目发展的影响

这批提交标志着FastVideo从“通用框架”向“硬件感知的深度优化”阶段迈进。通过攻克GB10这一具体硬件目标，项目积累了统一内存架构下的优化经验，这些经验可迁移至其他类似硬件（如Apple Silicon、AMD APU）。同时，MiniMax H3的成功部署证明了框架的灵活性和工程能力，有望吸引更多模型贡献者和硬件合作伙伴，加速视频生成技术的普及化进程。

## 详细提交记录

### [e9bbaca](https://github.com/hao-ai-lab/FastVideo/commit/e9bbaca07d511b2ee7e16474dae6f923426223dc)

- **作者**: KyleNeverGivesUp
- **时间**: 2026-08-26T22:32:56Z
- **提交信息**: [perf] Disable every offload path on unified memory, unblocking MiniMax H3 generation on one GB10 (#1715)

### [9bfa585](https://github.com/hao-ai-lab/FastVideo/commit/9bfa58544872ac050816088435c9c4b0fbd91324)

- **作者**: KyleNeverGivesUp
- **时间**: 2026-08-26T22:23:51Z
- **提交信息**: [perf]: stop holding the whole checkpoint during DiT load, unblocking MiniMax H3 on one GB10 (#1714)

### [b206255](https://github.com/hao-ai-lab/FastVideo/commit/b2062556a9bc100a4edd7636cda47078efc41389)

- **作者**: Raghav K
- **时间**: 2026-08-26T19:30:56Z
- **提交信息**: [perf] VSA Triton: widen the autotune num_stages range (the optimum was outside it) (#1706)

### [c9c5585](https://github.com/hao-ai-lab/FastVideo/commit/c9c558575804037ee95fd41014385a69bdbf7a85)

- **作者**: KyleNeverGivesUp
- **时间**: 2026-08-26T19:03:14Z
- **提交信息**: [perf]: MiniMax H3 on GB10 - skip text encoder CPU offload on unified memory (5m49s to 30ms) (#1710)

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-08-27
**监控日期**: 2026-08-26
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34386
- **最后更新**: 2026-08-27T01:40:28Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Sayak Paul, Akshan Krithick

## AI分析总结

# 提交分析总结

## 1. 主要更新类型

本次提交主要属于**测试基础设施重构**和**代码质量维护**类别，不涉及新功能开发或Bug修复，而是对现有测试体系的结构性调整。

## 2. 关键变更点及与项目方向的关系

- **迁移多个模型测试到新Mixin结构**：将acestep、auraflow、cogview4和helios四个模型的测试迁移到新的Mixin测试结构，同时重构了DeepFloyd IF的inpainting超分辨率pipeline测试。这与diffusers项目持续推动的**测试代码模块化和复用性提升**方向一致，通过统一的Mixin结构减少重复代码，提高测试维护效率。

- **测试结构标准化**：此次变更是项目长期测试体系演进的一部分，反映了diffusers在模型数量快速增长后，对测试代码可维护性的重视。

## 3. 对项目的影响和潜在意义

- **降低维护成本**：随着diffusers支持的模型数量持续增加，统一的测试结构能显著降低新增模型时的测试编写工作量。
- **提高测试可靠性**：标准化的测试结构有助于保证不同模型测试覆盖的一致性，减少因测试代码差异导致的遗漏。
- **为后续扩展铺路**：清晰的测试架构使得社区贡献者更容易理解和编写测试，降低参与门槛。

## 4. 值得关注的技术点

- **Mixin测试模式**：这是Python测试中常用的组合式设计，通过混入类共享通用测试逻辑，同时允许模型特定配置的覆盖。
- **渐进式迁移策略**：项目选择分批迁移而非一次性重构，降低了回归风险，这种稳健的工程实践值得借鉴。

## 5. 对项目发展的影响

结合README中diffusers作为**多模态扩散模型统一工具库**的定位，这些提交虽不直接面向用户功能，但通过夯实测试基础设施，间接支撑了项目持续扩展模型生态的战略目标。随着模型数量增长，良好的测试架构是保持项目健康发展的关键保障，也为未来引入更多复杂pipeline（如视频生成、3D生成等）奠定了质量基础。整体而言，这是典型的**技术债务偿还**工作，对项目长期可持续发展具有积极意义。

## 详细提交记录

### [d57cecd](https://github.com/huggingface/diffusers/commit/d57cecde92a6d396845ab35425aa27469dff8173)

- **作者**: Sayak Paul
- **时间**: 2026-08-26T09:29:16Z
- **提交信息**: [tests] migrate acestep, auraflow, cogview4, and helios tests (#14582)

* migrate acestep, auraflow, cogview4, and helios tests

* fixes

### [e300a4e](https://github.com/huggingface/diffusers/commit/e300a4ee2e982ab83cdc6aadec7b6118c9465e38)

- **作者**: Akshan Krithick
- **时间**: 2026-08-26T08:56:26Z
- **提交信息**: refactor deepfloyd if inpainting superresolution pipeline tests to the new mixin structure (#14606)

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-08-27
**监控日期**: 2026-08-26
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


**报告日期**: 2026-08-27
**监控日期**: 2026-08-26
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13003
- **最后更新**: 2026-08-26T20:28:03Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-08-27
**监控日期**: 2026-08-26
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 32507
- **最后更新**: 2026-08-27T01:44:16Z

## 提交统计

- **昨日提交总数**: 35
- **提交者数量**: 21
- **主要提交者**: siyu, weireweire, paulzhang-tm

## AI分析总结

# SGLang 昨日提交分析报告

## 一、主要更新类型

本次提交涵盖功能新增、Bug修复、性能优化、文档更新、配置重构、内核优化及CI调整等多类变更，整体呈现高频迭代态势。

## 二、关键变更点与项目方向

1. **核心推理能力增强**：新增Beam Search支持（#31626）和FullCG跨DP-attention ranks的预填充协调（#35640），显著扩展了推理场景覆盖。前者提升解码质量，后者优化大规模并行下的预填充效率，均直接服务于项目“高性能推理引擎”的核心定位。

2. **配置系统重构**：连续6个提交（#36250-#36255）重构配置架构，将“发布-读取”职责分离，ServerArgs持有原始输入，运行时读取已发布配置包。这是面向可维护性的深度重构，为后续配置扩展奠定基础。

3. **内核与硬件适配**：针对NVIDIA sm_107优化自定义all-reduce v2（#36397）、拆分all-reduce通信器为push/pull平面（#35735）、修复Hopper上mxfp4 MoE权重缩放越界读取（#36456）、扩展fp8 k-cache量化kernel的token_id至int64（#30859）。这些底层优化直接提升GPU利用率与数值稳定性。

4. **新模型支持**：新增GLM-5.3-Flash和Qwen3.8-Flash-Next cookbook（含FP8 KV + TRT-LLM DSA基准），并针对Blackwell平台默认FP8 KV配置，体现对最新模型和硬件的快速跟进。

5. **扩散模型优化**：支持Cosmos3动作生成的批处理（#36301）、融合tanh-GELU到LongCat-Image DiT FFN上投影（#36322）、缓存种子可配置化（#36463），持续强化多模态生成能力。

6. **内存与缓存管理**：HiCache改进辅助加载回填逻辑（#36317）、统一内存停止驱逐机制（#33091）、权重缓存守护进程路径可配置（#36299），提升资源利用效率。

## 三、项目影响与潜在意义

- **推理效率与质量双提升**：Beam Search和FullCG协调直接增强核心推理能力，all-reduce优化和内核修复降低延迟、提升吞吐。
- **架构可维护性增强**：配置系统重构和通信器拆分表明项目正从“功能堆叠”转向“架构治理”，为大规模部署和社区协作铺路。
- **生态适配加速**：多款新模型cookbook和CUDA 13.4容器支持，巩固了SGLang作为“最新模型+最新硬件”首选推理框架的地位。

## 四、值得关注的技术点

- **FlashInfer autotune策略跨TP ranks同步**（#35343）：解决多卡推理时自动调优不一致问题，对大规模部署至关重要。
- **FP8 KV Cache + TRT-LLM DSA组合**：在Blackwell平台上的默认配置，代表高吞吐低显存占用的前沿方向。
- **PyTorch ABI依赖声明**（#36465）：确保sglang-kernel wheel的二进制兼容性，降低用户安装门槛。

## 五、对项目发展的影响

结合README中SGLang“高性能、易用、多模态”的定位，本次提交呈现三大趋势：**一是底层性能持续深挖**（内核、通信、内存），巩固技术壁垒；**二是架构现代化**（配置重构、职责分离），为长期演进打基础；**三是生态快速扩张**（新模型、新硬件、扩散模型），扩大用户覆盖面。整体上，项目正从“功能领先”向“架构领先+生态领先”双轮驱动演进，有望在LLM推理框架竞争中保持头部地位。

## 详细提交记录

### [ec4bdbf](https://github.com/sgl-project/sglang/commit/ec4bdbfa4a17dc7afab258a488c36184bb0de134)

- **作者**: Liangsheng Yin
- **时间**: 2026-08-26T23:56:15Z
- **提交信息**: [Feature] Beam search support (#31626)

Co-authored-by: cswuyg <cswuyg@gmail.com>
Co-authored-by: cswuyg <496090217@qq.com>
Co-authored-by: Vedant Jhaveri <vedantjh2@gmail.com>
Co-authored-by: Vedant Jhaveri <vjhaveri@linkedin.com>

### [e5a1c5a](https://github.com/sgl-project/sglang/commit/e5a1c5a4231694625b6a0c3a2cfd4032d32e5107)

- **作者**: Cheng Wan
- **时间**: 2026-08-26T23:17:02Z
- **提交信息**: Fix _is_compiling dynamo tracing: import torch instead of sys.modules lookup (#36573)

### [7f27bf4](https://github.com/sgl-project/sglang/commit/7f27bf470824f452a34e866d22ab5e332a23e26f)

- **作者**: kuma_Gu2006
- **时间**: 2026-08-26T22:24:26Z
- **提交信息**: [Kernel] Declare the PyTorch ABI dependency in sglang-kernel wheels (#36465)

### [1eb629a](https://github.com/sgl-project/sglang/commit/1eb629ab4fc0db4b1c784700d596dde8b26386e6)

- **作者**: Trevor Morris
- **时间**: 2026-08-26T22:19:31Z
- **提交信息**: [NVIDIA] Tune custom all reduce v2 for sm_107 (#36397)

### [3ce243d](https://github.com/sgl-project/sglang/commit/3ce243da3f3d21f15dba140212987f93ef14d00a)

- **作者**: Trevor Morris
- **时间**: 2026-08-26T22:02:16Z
- **提交信息**: [NVIDIA] Add CUDA 13.4 container for initial Rubin support (#36233)

### [0669407](https://github.com/sgl-project/sglang/commit/06694071c6552383af9dce3f55e805d394ec4438)

- **作者**: paulzhang-tm
- **时间**: 2026-08-26T21:51:31Z
- **提交信息**: [Spec] Avoid tensor scalar reads in spec decode allocation (#35377)

### [45c85c1](https://github.com/sgl-project/sglang/commit/45c85c198bc754c4e07d2a005ca651ff81f40541)

- **作者**: Liangsheng Yin
- **时间**: 2026-08-26T21:43:20Z
- **提交信息**: [CI] Lower the AWQ Marlin MMLU threshold to 0.80 (#36570)

### [a8d716c](https://github.com/sgl-project/sglang/commit/a8d716ce8d4d1e018aad5c27fec4a7567ec17579)

- **作者**: Xinyuan Tong
- **时间**: 2026-08-26T21:22:24Z
- **提交信息**: dsa: widen the fp8 k-cache quant kernel's token_id to int64 (#30859)

### [2935bb8](https://github.com/sgl-project/sglang/commit/2935bb8e79e669b71aa4fef3b412fa25bc656c25)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-08-26T20:36:49Z
- **提交信息**: Fix OOB read in mxfp4 MoE weight scales on Hopper (#36456)

Co-authored-by: Mohammad Angkad <mohammad.angkad@radixark.ai>

### [e7e7894](https://github.com/sgl-project/sglang/commit/e7e78940168f3ba65c762a6f82fd8bc5b6ee04e3)

- **作者**: siyu
- **时间**: 2026-08-26T19:38:50Z
- **提交信息**: [Weight Cache] Make daemon socket/ready paths configurable via env (#36299)

### [5263568](https://github.com/sgl-project/sglang/commit/5263568bcbf9da7b463e25c136f6aa92eedc3c08)

- **作者**: weireweire
- **时间**: 2026-08-26T17:30:38Z
- **提交信息**: [HiCache] Keep auxiliary load-back out of Full KV pending ownership (#36317)

Co-authored-by: weireweire <20922698+weireweire@users.noreply.github.com>

### [e27a7fa](https://github.com/sgl-project/sglang/commit/e27a7fac772bccb9f867c86ef7c4cbcf13738cf0)

- **作者**: Xinyuan Tong
- **时间**: 2026-08-26T16:51:05Z
- **提交信息**: GLM-5.3-Flash cookbook: default Blackwell recipes to FP8 KV + TRT-LLM DSA (#36519)

### [f8cc1f9](https://github.com/sgl-project/sglang/commit/f8cc1f9525c3a0bf3b14480cc76eccb79db1b4ea)

- **作者**: Xinyuan Tong
- **时间**: 2026-08-26T14:39:27Z
- **提交信息**: GLM-5.3-Flash cookbook: FP8 KV + TRT-LLM DSA benchmark card (#36513)

### [c8b56b1](https://github.com/sgl-project/sglang/commit/c8b56b1f44d5c5370f47470ee490da3b04375e1c)

- **作者**: Shangming Cai
- **时间**: 2026-08-26T14:21:15Z
- **提交信息**: chore: bump mooncake version to 0.3.13 (#36493)

### [924aeee](https://github.com/sgl-project/sglang/commit/924aeee59cb68ea99bf7c7c183512958ed3d6272)

- **作者**: XuFu
- **时间**: 2026-08-26T14:15:03Z
- **提交信息**: [diffusion] feat: support batching for cosmos3 action generation (#36301)

Signed-off-by: FxxxxU <fu18801374388@163.com>
Signed-off-by: Mick <mickjagger19@icloud.com>
Co-authored-by: Mick <mickjagger19@icloud.com>

### [dfc40e0](https://github.com/sgl-project/sglang/commit/dfc40e0efe10af66db91d234ae10715e9990e5ea)

- **作者**: Xinyuan Tong
- **时间**: 2026-08-26T14:00:16Z
- **提交信息**: Add GLM-5.3-Flash cookbook (#36440)

### [8eaffdf](https://github.com/sgl-project/sglang/commit/8eaffdf382e06b7dc50fc5c76cc5aad9c36bb0e4)

- **作者**: Yuhao Yang
- **时间**: 2026-08-26T12:53:55Z
- **提交信息**: docs: point the Qwen3.8-Flash-Next cookbook at model support PR #36497 (#36499)

### [c7b5e76](https://github.com/sgl-project/sglang/commit/c7b5e76fa925eac1c98d7e62cc7a27fb1f05a9f9)

- **作者**: Yuhao Yang
- **时间**: 2026-08-26T12:36:59Z
- **提交信息**: Add Qwen3.8-Flash-Next cookbook (#36496)

Co-authored-by: Zijie Xia <zijie.xia@radixark.ai>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [413df1f](https://github.com/sgl-project/sglang/commit/413df1f8db4fd159c5d07e960f9ec5547edeb5c1)

- **作者**: Cheng Wan
- **时间**: 2026-08-26T12:14:05Z
- **提交信息**: config: ServerArgs holds the raw input (#36255)

### [27c3636](https://github.com/sgl-project/sglang/commit/27c36368b6389e98aa6708aa514aca5ec9e9ca41)

- **作者**: Jikui Xie
- **时间**: 2026-08-26T12:12:21Z
- **提交信息**: fix(moe): guard FP8 delegate activation params (#36275)

Signed-off-by: jikuixie <jikuixie@gmail.com>
Co-authored-by: Mohammad Angkad <mohammad.angkad@radixark.ai>
Co-authored-by: Mohammad Miadh Angkad <176301910+mmangkad@users.noreply.github.com>
Co-authored-by: shyeh25 <206795756+shyeh25@users.noreply.github.com>

### [937af85](https://github.com/sgl-project/sglang/commit/937af8538b07fb162ea9b171a099382c785389ff)

- **作者**: Cheng Wan
- **时间**: 2026-08-26T12:08:25Z
- **提交信息**: config: the runtime readers take the published bags (#36254)

### [5b7fc61](https://github.com/sgl-project/sglang/commit/5b7fc61306138582e0fb3536047fcdbd12aedd57)

- **作者**: Cheng Wan
- **时间**: 2026-08-26T12:05:28Z
- **提交信息**: config: resolution reads the declarations, not the fields (#36253)

### [ae5feb4](https://github.com/sgl-project/sglang/commit/ae5feb4b9c83552c624171bac91d0d11e6b8c84e)

- **作者**: Cheng Wan
- **时间**: 2026-08-26T12:02:17Z
- **提交信息**: config: stop handing the record to code that does not read it (#36252)

### [d7b144f](https://github.com/sgl-project/sglang/commit/d7b144f64e62cc33dcda1eb03c512d376eda8c15)

- **作者**: Cheng Wan
- **时间**: 2026-08-26T11:58:41Z
- **提交信息**: config: publishing is the process entry's job (#36251)

### [702de26](https://github.com/sgl-project/sglang/commit/702de2631057d11542f1930b47e84a05cdd57587)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-08-26T11:04:46Z
- **提交信息**: [diffusion] make benchmark caches seedable and cover missing native families (#36463)

### [170da72](https://github.com/sgl-project/sglang/commit/170da72c13b75a3778a5ca9452667922a00ce3ee)

- **作者**: iterhui
- **时间**: 2026-08-26T11:04:06Z
- **提交信息**: [diffusion] perf: fuse tanh-GELU into the LongCat-Image DiT FFN up-proj (#36322)

Co-authored-by: 登辉 <yangdenghui.ydh@alibaba-inc.com>
Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

### [8005df6](https://github.com/sgl-project/sglang/commit/8005df61d32ccbd4d3f3034c7b9af9bc54dcd5dd)

- **作者**: Cheng Wan
- **时间**: 2026-08-26T10:00:28Z
- **提交信息**: config: spell the parallel config tier at the call site (#36250)

### [689ade6](https://github.com/sgl-project/sglang/commit/689ade69d1c8889c871da5491c7b328ec619e097)

- **作者**: DarkSharpness
- **时间**: 2026-08-26T09:40:28Z
- **提交信息**: [kernel] Split the custom all-reduce communicator into push/pull planes (#35735)

### [58ecbba](https://github.com/sgl-project/sglang/commit/58ecbba0bd8c2aec9adc91dbc66e125e8c211028)

- **作者**: Aurick Qiao
- **时间**: 2026-08-26T09:16:02Z
- **提交信息**: [Feature] Coordinate FullCG prefill across DP-attention ranks (#35640)

Co-authored-by: Yuwei An <ayw.sirius19@gmail.com>

### [2511743](https://github.com/sgl-project/sglang/commit/2511743bd784e69e5a81ca3d926a000711dae4ab)

- **作者**: SuperSong
- **时间**: 2026-08-26T09:06:32Z
- **提交信息**: [unified-memory] Stop eviction when shared allocation capacity is sufficient (#33091)

Co-authored-by: seokwoosong <seokwoosong@users.noreply.github.com>

### [ffc431c](https://github.com/sgl-project/sglang/commit/ffc431cd4c284e3204413b66f128a588c715b54d)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-08-26T08:34:39Z
- **提交信息**: [CI] Fix stale tool_call_parser key in Spark2.5 detector test (#36464)

Co-authored-by: Mohammad Angkad <mohammad.angkad@radixark.ai>

### [a3c4936](https://github.com/sgl-project/sglang/commit/a3c493643876895efbb2ce784b807281d246f6af)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-08-26T08:30:47Z
- **提交信息**: Sync FlashInfer autotune tactic choice across TP ranks (#35343)

Co-authored-by: Mohammad Angkad <mohammad.angkad@radixark.ai>

### [bede6bc](https://github.com/sgl-project/sglang/commit/bede6bc37c5d9638099ebb948d93b9e2a7799f10)

- **作者**: Jialin Ouyang
- **时间**: 2026-08-26T07:35:18Z
- **提交信息**: Fix unified HiCache PP test import (#36454)

### [c3c529c](https://github.com/sgl-project/sglang/commit/c3c529c28e6da00fcac63e3dccdbb6bbb8cf60b5)

- **作者**: Mick
- **时间**: 2026-08-26T07:16:18Z
- **提交信息**: [diffusion] docs: distinguish MiniMax H3 checkpoint variants (#36412)

### [7ef49e8](https://github.com/sgl-project/sglang/commit/7ef49e8f7d7f895f880e441b306f9279056606be)

- **作者**: KnightYao
- **时间**: 2026-08-26T07:04:46Z
- **提交信息**: Rename Spark3 to Spark2.5 (#36416)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-08-27
**监控日期**: 2026-08-26
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1259
- **最后更新**: 2026-08-26T02:00:00Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-08-27
**监控日期**: 2026-08-26
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 90154
- **最后更新**: 2026-08-27T01:36:06Z

## 提交统计

- **昨日提交总数**: 33
- **提交者数量**: 31
- **主要提交者**: Jee Jee Li, rasmith, Andrey Talman

## AI分析总结

## 提交分析总结

### 1. 主要更新类型

本批次共33个提交，涵盖**Bug修复**（约12个）、**性能优化**（约5个）、**硬件适配**（AMD ROCm/Intel XPU相关约6个）、**CI/构建改进**（约5个）、**文档更新**（2个）、**代码重构与清理**（约4个）及**新功能支持**（2个）。

### 2. 关键变更点与项目方向

- **多后端通信优化**：恢复portable all2all默认后端、启用fi_one_sided模式，体现vLLM对多GPU通信灵活性的重视。
- **DeepSeek V4/K3系列优化**：针对DeepSeek V4的C4压缩器GEMM融合、top-k buffer清理，以及Kimi K3的`eh_proj`线性计算优化（12.9~25.2%内核性能提升），显示对前沿模型的高效推理支持。
- **AMD ROCm生态强化**：FP8 asm MLA prefill扩展、CUDA graph流捕获修复、MoRIIO共享KV内存注册修复、ROCm基础镜像更新，持续完善AMD硬件支持。
- **Rust前端与协议修复**：LogprobsTensors wire schema不匹配修复，保障新前端架构的稳定性。
- **分布式推理增强**：DP同步、disagg场景KV传输参数传递、Mooncake Mamba截断修复，强化多节点推理可靠性。

### 3. 项目影响与潜在意义

- **稳定性提升**：多项Bugfix（工具调用JSON解析、空FlatLogprobs处理、Gemma4 MTP CUDA-graph安全）直接改善生产环境可靠性。
- **性能竞争力**：K3内核优化和DeepSeek V4 GEMM融合为高负载场景带来显著吞吐提升。
- **硬件覆盖扩大**：Intel XPU CI超时调整、LoRA Multimodal迁移至B70，以及ROCm多项修复，巩固多硬件平台战略。
- **架构演进**：PCP兼容性检查委托给管理器、rank-local IPC权重更新，体现模块化与可扩展性设计思路。

### 4. 值得关注的技术点

- **DeepEPv2 MXFp8激活缩放调度**：支持新型低精度格式，可能影响未来MoE推理精度与性能平衡。
- **Pixtral打包多模态编码器注意力**：提升多模态模型处理效率。
- **HPC-ops stride KV cache支持**：增强对非连续KV缓存布局的兼容性。
- **Offloader子模块卸载扩展**：解决`make_layers`无法覆盖的模块卸载问题，优化显存管理。
- **Python 3.14兼容性准备**：CI中使用`model_class_overrides`，提前适配未来Python版本。

### 5. 对项目发展的影响

结合README中“Easy, fast, and cheap LLM serving for everyone”的定位，本批次提交体现了vLLM在**多硬件适配**（AMD/Intel/XPU）、**前沿模型优化**（DeepSeek V4/K3、Gemma4、Pixtral）、**分布式扩展**（disagg、DP、Mooncake）和**工程化成熟度**（CI改进、类型检查、文档修正）上的持续投入。这些变更共同推动vLLM向更广泛硬件生态、更高推理性能、更稳定生产部署的方向演进，同时通过Rust前端和模块化重构为未来架构升级奠定基础。整体上，项目正从“高性能推理引擎”向“全栈式LLM服务平台”过渡，兼顾前沿模型支持与大规模部署可靠性。

## 详细提交记录

### [d1e5e66](https://github.com/vllm-project/vllm/commit/d1e5e66ee30ba4bc020ac8e14b05e7a8c41b9302)

- **作者**: vllm-agent
- **时间**: 2026-08-26T23:19:49Z
- **提交信息**: [Bugfix] Restore portable all2all backend default (#53952)

Signed-off-by: Kevin Luu <51931015+khluu@users.noreply.github.com>
Co-authored-by: Kevin Luu <51931015+khluu@users.noreply.github.com>

### [3fd72ff](https://github.com/vllm-project/vllm/commit/3fd72ffd7b78bc80f249cdfc28d67177dbab2b56)

- **作者**: Jung Jiyu
- **时间**: 2026-08-26T23:16:43Z
- **提交信息**: [Bugfix][Rust Frontend] Fix LogprobsTensors wire schema mismatch (#53939)

Signed-off-by: jungjiyu <libraryofjiyu@gmail.com>
Signed-off-by: Tyler Michael Smith <tlrmchlsmth@gmail.com>
Co-authored-by: Tyler Michael Smith <tlrmchlsmth@gmail.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [a27e88c](https://github.com/vllm-project/vllm/commit/a27e88c8627bcdd86f1cd35e0c84830944ad5b3c)

- **作者**: liuzhenwei
- **时间**: 2026-08-26T22:57:36Z
- **提交信息**: [XPU][CI] increase timeout of extract_hidden_states tp2 (#53862)

### [f18d0ba](https://github.com/vllm-project/vllm/commit/f18d0ba90d972a852a351c98be3f42b31372cfe4)

- **作者**: Shenglei Fu
- **时间**: 2026-08-26T22:29:10Z
- **提交信息**: [Doc] Add Granite 3.1 series to batch invariance tested models (#53650)

Signed-off-by: Shenglei Fu <117230642+ShengleiFu@users.noreply.github.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [76cfe1c](https://github.com/vllm-project/vllm/commit/76cfe1cd88d30d525eec8be5bff75f8b77471c88)

- **作者**: Wentao Ye
- **时间**: 2026-08-26T21:08:02Z
- **提交信息**: [Kimi K3 Perf] Optimize `eh_proj` linear calculation, 12.9 ~ 25.2% kernel performance improvement (#53942)

### [161ffd3](https://github.com/vllm-project/vllm/commit/161ffd37d207e7def333f07f650e90c67b8bd43b)

- **作者**: Venkat Balaji S
- **时间**: 2026-08-26T20:26:00Z
- **提交信息**: [Bugfix] Guard tool call argument JSON parsing in chat message postprocessing (#48922)

Signed-off-by: VBS2004 <venkatbalaji2004@gmail.com>
Co-authored-by: Ben Browning <56071+bbrowning@users.noreply.github.com>

### [00ca27d](https://github.com/vllm-project/vllm/commit/00ca27d0c1ca8c10caee9f00dd86a6fed3dd3769)

- **作者**: xiangdong
- **时间**: 2026-08-26T20:04:10Z
- **提交信息**: [XPU][TEST]Move LoRA Multimodal to B70 in Intel GPU CI (#53841)

Signed-off-by: zengxian <xiangdong.zeng@intel.com>

### [0a5ad6f](https://github.com/vllm-project/vllm/commit/0a5ad6f0d42c1ace54f27d7dd6a852be86e42148)

- **作者**: Woosuk Kwon
- **时间**: 2026-08-26T18:59:09Z
- **提交信息**: [Model] Remove unused DeepSeek V4 top-k buffer helper (#53697)

### [1a085da](https://github.com/vllm-project/vllm/commit/1a085dadf254b7cb2b5f904747a5750256d413fa)

- **作者**: xiaohuguo2023
- **时间**: 2026-08-26T17:47:16Z
- **提交信息**: [ROCm][K3] Extend FP8 asm MLA prefill to non-divisor small head counts (#51040)

Signed-off-by: Xiaohu Guo <Xiaohu.Guo@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [17da485](https://github.com/vllm-project/vllm/commit/17da48596c98946d3e3e6896e2ebd341e809f3bd)

- **作者**: aoshen02
- **时间**: 2026-08-26T16:50:33Z
- **提交信息**: [Bugfix][DP] Synchronize the device on pause completion (#52914)

Signed-off-by: aoshen02 <aoshen@inferact.ai>

### [8d301f0](https://github.com/vllm-project/vllm/commit/8d301f075b970427ae2486194f3694cdc04fde71)

- **作者**: Avinash Paul
- **时间**: 2026-08-26T16:10:57Z
- **提交信息**: [Bugfix][ROCm][Disagg] Fix MoRIIO shared KV memory region registration (#53698)

Signed-off-by: avininjamay8 <avpaul@amd.com>
Co-authored-by: avininjamay8 <avpaul@amd.com>

### [c71f6f8](https://github.com/vllm-project/vllm/commit/c71f6f8a81d3d3c49a045c8b88eed36366cc7d92)

- **作者**: Konstantin Dunas
- **时间**: 2026-08-26T15:42:52Z
- **提交信息**: [Bugfix] Thread kv_transfer_params into engine for /inference/v1/generate (disagg) (#42644)

Signed-off-by: hallerite <git@hallerite.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [2ab1874](https://github.com/vllm-project/vllm/commit/2ab187430b6be67abdecf116e1cd13e14968ddf5)

- **作者**: Luciano Martins
- **时间**: 2026-08-26T15:39:19Z
- **提交信息**: [Bugfix] Make Gemma4 MTP suppress_tokens masking CUDA-graph-safe (#53884)

Signed-off-by: Luciano Martins <lucianommartins@users.noreply.github.com>
Co-authored-by: Luciano Martins <lucianommartins@users.noreply.github.com>

### [657f9b9](https://github.com/vllm-project/vllm/commit/657f9b9ce241a5452a36fc37d8e2e1e936722bfc)

- **作者**: Fangzhou Ai
- **时间**: 2026-08-26T15:36:14Z
- **提交信息**: [ROCm][DSV4][Perf] Fuse DeepSeek V4 C4 compressor GEMMs (#53838)

Signed-off-by: fai <fangzhouai@gmail.com>

### [080a66a](https://github.com/vllm-project/vllm/commit/080a66a69c6fd1fe464756f88ab958baad66ce69)

- **作者**: fanxingran
- **时间**: 2026-08-26T15:16:45Z
- **提交信息**: [Bugfix][ROCm] Capture CUDA graphs on the current stream (#53818)

Signed-off-by: fanxingran <xingran.fan@amd.com>

### [28b484e](https://github.com/vllm-project/vllm/commit/28b484e5d741519feb72e5c0bf6ebc3b08176292)

- **作者**: Oliver Holworthy
- **时间**: 2026-08-26T14:14:40Z
- **提交信息**: [Model] Pixtral: use packed multimodal encoder attention (#52185)

Signed-off-by: Oliver Holworthy <1216955+oliverholworthy@users.noreply.github.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [c47ca4a](https://github.com/vllm-project/vllm/commit/c47ca4aaebafbbcbe47d0ae1f3b9672bcf1b4ed8)

- **作者**: Jensen Chen
- **时间**: 2026-08-26T14:12:11Z
- **提交信息**: [Mypy Fix] Mypy fix for "vllm/model_executor/models/[tT]" (#53466)

Signed-off-by: Jensen Chen <a1043904820@gmail.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [903a021](https://github.com/vllm-project/vllm/commit/903a02192fca19e4c89705af7017c0f24971ea4f)

- **作者**: Tony
- **时间**: 2026-08-26T13:00:54Z
- **提交信息**: [Bugfix] Handle empty FlatLogprobs slices and delta output (#53704)

Signed-off-by: tony <864832769@qq.com>

### [6a5e8f5](https://github.com/vllm-project/vllm/commit/6a5e8f5979376e666c930f668d0f58d78a9933c6)

- **作者**: Robert Shaw
- **时间**: 2026-08-26T12:26:11Z
- **提交信息**: [DeepEPv2] Support MXFp8 Activation Scale Dispatch (#51398)

Signed-off-by: Robert Shaw <robshaw@redhat.com>
Co-authored-by: Robert Shaw <robshaw@redhat.com>

### [15baeae](https://github.com/vllm-project/vllm/commit/15baeaee98263725aed9492dbb5df3ec8525bdff)

- **作者**: QWERQWERQWE86
- **时间**: 2026-08-26T12:17:56Z
- **提交信息**: [Doc] Fix local input path in run-batch examples across docs (#53220)

### [2cd6c66](https://github.com/vllm-project/vllm/commit/2cd6c664c1ec050328a33be5a8b8167605663536)

- **作者**: Artem Perevedentsev
- **时间**: 2026-08-26T12:03:45Z
- **提交信息**: [MoE] enable all2all fi_one_sided by default (#53311)

Signed-off-by: Artem Perevedentsev <aperevedents@nvidia.com>

### [31739ce](https://github.com/vllm-project/vllm/commit/31739ceb0b9f3beb8bebc01c0700b9e516b953ef)

- **作者**: Cyrus Leung
- **时间**: 2026-08-26T11:22:48Z
- **提交信息**: [CI/Build] Improve pre-commit fail message (#53866)

Signed-off-by: DarkLight1337 <tlleungac@connect.ust.hk>

### [61d4f56](https://github.com/vllm-project/vllm/commit/61d4f56635e0f2faae4bd60e6da88a53c9d3affb)

- **作者**: ray24777
- **时间**: 2026-08-26T10:37:00Z
- **提交信息**: [Offloader] Offload submodules that make_layers never reaches (#53120)

Signed-off-by: ray24777 <103923677+ray24777@users.noreply.github.com>
Signed-off-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [7a99938](https://github.com/vllm-project/vllm/commit/7a9993878cccc5b598d0b8934becf6fffb03e6fb)

- **作者**: Andrey Talman
- **时间**: 2026-08-26T09:51:26Z
- **提交信息**: [CI] forward fix CRCR report step in the torch-nightly lane (#53732)

Signed-off-by: Andrey Talman <atalman@fb.com>

### [b821d7b](https://github.com/vllm-project/vllm/commit/b821d7b2a648b0c0186c8f7d0784965b6d0cd5bc)

- **作者**: Andrey Talman
- **时间**: 2026-08-26T09:31:08Z
- **提交信息**: [CI] Build mamba-ssm with C++20 for torch 2.14 nightly compatibility (#49600)

Co-authored-by: Shengqi Chen <harry-chen@outlook.com>

### [73bd7c8](https://github.com/vllm-project/vllm/commit/73bd7c83c4847cd38cb0054dbd9aa912e0eafd03)

- **作者**: adisivaprasad
- **时间**: 2026-08-26T09:10:54Z
- **提交信息**: [Bugfix][Processor] Replace bare asserts with ValueError in DeepseekVLV2/OCR processors (#53854)

Signed-off-by: adisivaprasad <adisivaprasad@users.noreply.github.com>
Co-authored-by: adisivaprasad <adisivaprasad@users.noreply.github.com>

### [2267d3b](https://github.com/vllm-project/vllm/commit/2267d3b1124a8b93c6fa5cb4e53cc8dae88b3c06)

- **作者**: Cheng Jiang
- **时间**: 2026-08-26T08:20:28Z
- **提交信息**: [AttentionBackend][HPC-ops] update hpc rope norm to support stride kv cache (#53705)

Signed-off-by: chengvjiang <chengvjiang@tencent.com>
Co-authored-by: chengvjiang <chengvjiang@tencent.com>
Co-authored-by: Yongye Zhu <zyy1102000@gmail.com>

### [75aa189](https://github.com/vllm-project/vllm/commit/75aa189ba06768f2fc7aa9dd255799c7ed672b5e)

- **作者**: Jee Jee Li
- **时间**: 2026-08-26T08:19:35Z
- **提交信息**: [LoRA] Cleanup VocabParallelEmbedding (#53843)

Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>

### [e376d45](https://github.com/vllm-project/vllm/commit/e376d45e82cb7e220da430e3179e81eb0922cf56)

- **作者**: Qiu Chunshuo
- **时间**: 2026-08-26T08:16:01Z
- **提交信息**: [Config] Delegate PCP compatibility checks to PCP manager (#53853)

Signed-off-by: QiuChunshuo <qiuchunshuo@huawei.com>

### [f14369c](https://github.com/vllm-project/vllm/commit/f14369c7f9fcd5f29c33c3ff6753a59664db59e5)

- **作者**: Ziming Huang
- **时间**: 2026-08-26T08:08:37Z
- **提交信息**: [Bugfix][Mooncake] Fix Mamba prefill truncation ordering (#53663)

Signed-off-by: Ziming Huang <zelda.huanghuang@gmail.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [cde7ba9](https://github.com/vllm-project/vllm/commit/cde7ba92da0e1e94bad2a410f9ec2e68bda1c7f7)

- **作者**: rasmith
- **时间**: 2026-08-26T07:55:07Z
- **提交信息**: [CI/Build][The Rock] Use model_class_overrides so spawned worker can use test PredictableLlamaForCausalLM class when worker spawned using Python 3.14 (#49218)

Signed-off-by: Randall Smith <Randall.Smith@amd.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [796822d](https://github.com/vllm-project/vllm/commit/796822d141382ab8ce82ef6101c6d802046f94e0)

- **作者**: Matt
- **时间**: 2026-08-26T07:38:20Z
- **提交信息**: [Hardware][AMD][Perf][Bugfix] Update ROCr and clr in base image (#53712)

Signed-off-by: Matthew Wong <Matthew.Wong2@amd.com>

### [ee5ae2a](https://github.com/vllm-project/vllm/commit/ee5ae2ae70e03b328c7a197681b7b8485617f4ed)

- **作者**: aoshen02
- **时间**: 2026-08-26T07:36:57Z
- **提交信息**: [RL] Add rank-local IPC weight updates (#52497)

Signed-off-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: Roger Wang <hey@rogerw.io>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-08-27
**监控日期**: 2026-08-26
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 6371
- **最后更新**: 2026-08-27T01:18:10Z

## 提交统计

- **昨日提交总数**: 12
- **提交者数量**: 11
- **主要提交者**: psv666, harley, Mu GuanLin

## AI分析总结

## 提交分析总结

### 1. 主要更新类型

本次提交涵盖**功能新增**（Nemotron VoiceChat全双工服务、MiniMax-H3 Turbo LoRA支持）、**Bug修复**（设备布局验证、FLASH_ATTN跨注意力、Realtime音频补全、LTX音频一致性）、**性能优化**（事件驱动编排循环）、**文档更新**（MiMo-Audio配方）、**测试补充**（MiniMax-H3 DLO DP2 T2VA冒烟测试）以及**配方新增**（GLM-TTS）等类型，整体以Bug修复和功能增强为主。

### 2. 关键变更点与项目方向的关系

- **Nemotron VoiceChat全双工服务**：这是最核心的变更，直接呼应项目“omni-modality model serving”的定位，将语音对话从半双工推向原生全双工，是实时交互能力的重要突破。
- **事件驱动编排循环（S1）**：作为性能优化的一期，为后续异步调度铺路，符合项目“fast”和“cheap”的核心理念，是引擎架构演进的关键一步。
- **设备布局验证与FLASH_ATTN修复**：提升多卡部署的稳定性和注意力计算的正确性，保障大规模推理的可靠性。
- **MiniMax-H3 Turbo LoRA与DLO支持**：扩展了模型生态和低秩适配能力，增强项目对不同模型和微调场景的兼容性。
- **GLM-TTS与MiMo-Audio配方**：提供具体硬件配置下的部署指南，降低用户上手门槛，促进社区采用。

### 3. 对项目的影响和潜在意义

- **实时交互能力跃升**：全双工语音支持使vllm-omni在实时语音助手、电话机器人等场景具备竞争力，扩大了应用边界。
- **架构演进信号**：事件驱动编排是引擎向更高并发、更低延迟方向演进的重要里程碑，虽为opt-in，但为后续默认启用奠定基础。
- **稳定性提升**：多处Bug修复（尤其是设备布局和注意力机制）直接减少多卡部署和长序列推理中的失败率，提升生产可用性。
- **生态扩展**：新增模型配方和LoRA支持，使项目覆盖更多模型族和硬件配置，增强“everyone”的可及性承诺。

### 4. 值得关注的技术点

- **全双工会话锁机制**：提交#6318拒绝在锁定会话上修改指令，说明全双工实现涉及会话状态管理，需关注并发控制设计。
- **事件驱动编排的分阶段实施**：S1仅引入opt-in循环，后续阶段可能涉及调度器重构，值得跟踪其性能收益和兼容性影响。
- **FLASH_ATTN跨注意力unpad修复**：涉及key-padding mask处理，对长序列和可变长度输入场景有直接影响。
- **设备布局验证前置**：在spawn workers前校验布局，可避免运行时才发现配置错误，是工程实践上的良好改进。

### 5. 对项目发展的影响

结合README中“Easy, fast, and cheap omni-modality model serving for everyone”的愿景，本次提交从三个维度推动项目前进：**功能上**，全双工语音和LoRA支持拓展了模态覆盖和定制化能力；**性能上**，事件驱动编排和注意力优化强化了“fast”和“cheap”的承诺；**易用性上**，新配方文档和测试降低了部署门槛。整体来看，项目正从“支持多模态推理”向“支持实时、可定制、高吞吐的omni-modality服务”演进，社区活跃度和工程成熟度均在提升。

## 详细提交记录

### [432b2c6](https://github.com/vllm-project/vllm-omni/commit/432b2c6ca3a0bc29c9cf65b6de11196d13c2ddf7)

- **作者**: Sy03
- **时间**: 2026-08-26T20:19:20Z
- **提交信息**: [Model] Add native full-duplex Nemotron VoiceChat serving (#6089)

Signed-off-by: Sysy <1370724210@qq.com>
Signed-off-by: sy03 <137072421@qq.com>
Co-authored-by: sy03 <137072421@qq.com>

### [c272397](https://github.com/vllm-project/vllm-omni/commit/c2723979c0a559b71ca719366c83c304b68d5116)

- **作者**: ChoHee
- **时间**: 2026-08-26T19:25:22Z
- **提交信息**: [Bugfix] Validate per-stage device layout before spawning workers (#5003) (#5742)

Signed-off-by: ChoHee15 <cc5281@126.com>
Signed-off-by: Gao Han <hgaoaf@connect.ust.hk>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Gao Han <hgaoaf@connect.ust.hk>

### [2d4724e](https://github.com/vllm-project/vllm-omni/commit/2d4724eb74b26e5a0420d87be2da9c9ba73804db)

- **作者**: vOv
- **时间**: 2026-08-26T17:20:59Z
- **提交信息**: [Bugfix][Diffusion] Fix FLASH_ATTN cross-attention key-padding unpad (#5866)

Signed-off-by: cr-gao <gaochenrui@sjtu.edu.cn>

### [91dd7fc](https://github.com/vllm-project/vllm-omni/commit/91dd7fcaec7419cfc93586f2cc2dca1b09240a4e)

- **作者**: Anurag
- **时间**: 2026-08-26T16:50:31Z
- **提交信息**: [Bugfix] Reject instructions changes on locked native duplex sessions (#6318)

Signed-off-by: ANURAG KANADE <anuragkanade6@gmail.com>

### [926e7fb](https://github.com/vllm-project/vllm-omni/commit/926e7fbfa2340d033016be79bc5b57dff9152a20)

- **作者**: harley
- **时间**: 2026-08-26T14:16:49Z
- **提交信息**: [Recipe] zai-org/GLM-TTS (2x non-standard RTX 4090 48GB) (#5769)

Signed-off-by: harley <480497125@qq.com>

### [8cfede4](https://github.com/vllm-project/vllm-omni/commit/8cfede4309cb22048013393212a21fd233876ffa)

- **作者**: Yueqian Lin
- **时间**: 2026-08-26T14:15:25Z
- **提交信息**: [Perf][Engine] Event-driven orchestration loop (opt-in) — S1 of #4855 (#5221)

Signed-off-by: Yueqian Lin <gao@yueqian.us>
Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: Yueqian Lin <gao@yueqian.us>

### [d3c990d](https://github.com/vllm-project/vllm-omni/commit/d3c990dca8c3787ffdfe1d1424cfda9584d6bff9)

- **作者**: Mu GuanLin
- **时间**: 2026-08-26T12:59:10Z
- **提交信息**: [Model][Bugfix] Improve LTX audio parity and similarity guards (#6342)

Signed-off-by: mglyn <1203789601@qq.com>

### [5ec576a](https://github.com/vllm-project/vllm-omni/commit/5ec576ab4c241afa8b56bee729776ccf7a0eb5eb)

- **作者**: psv666
- **时间**: 2026-08-26T10:27:25Z
- **提交信息**: [Bugfix] Fix missing Realtime audio completion (#6564)

Signed-off-by: psv666 <2693925048@qq.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [030fccb](https://github.com/vllm-project/vllm-omni/commit/030fccb2bfdc9f7d1c323650b8301a4448cbf8a8)

- **作者**: WeiQing Chen
- **时间**: 2026-08-26T09:17:10Z
- **提交信息**: [Test] Add MiniMax-H3 DLO DP2 T2VA smoke (#6555)

Signed-off-by: david6666666 <530634352@qq.com>

### [816335c](https://github.com/vllm-project/vllm-omni/commit/816335cb46191287e1bc1d734b8a496ae2e00da2)

- **作者**: Zhichao Zhang
- **时间**: 2026-08-26T08:26:24Z
- **提交信息**: [Doc] Add MiMo-Audio recipe for RTX 5090/5090D 32GB (#6559)

Signed-off-by: chaosansui <zzc15560846421@163.com>

### [59cf3ad](https://github.com/vllm-project/vllm-omni/commit/59cf3add400be1744f308f497bd31dcceb7be262)

- **作者**: Mu GuanLin
- **时间**: 2026-08-26T08:15:47Z
- **提交信息**: [Feature] Support MiniMax-H3 Turbo LoRA with DLO (#6550)

Signed-off-by: mglyn <1203789601@qq.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [7439ed4](https://github.com/vllm-project/vllm-omni/commit/7439ed41c27d6e817843cff7704d2068c5214ec6)

- **作者**: Gao Han
- **时间**: 2026-08-26T07:02:47Z
- **提交信息**: Revert "[Bugfix] Restore name-based model detection for HF cache snapshot paths" (#6642)

---
