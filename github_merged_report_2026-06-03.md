# GitHub Stars 合并报告 - 2026-06-03

**合并日期**: 2026-06-04
**监控日期**: 2026-06-03
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


**报告日期**: 2026-06-04
**监控日期**: 2026-06-03
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 1976
- **最后更新**: 2026-06-03T23:06:19Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-06-04
**监控日期**: 2026-06-03
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Light Image Video Generation Inference Framework
- **语言**: Python
- **星标数**: 2337
- **最后更新**: 2026-06-03T23:33:14Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 1
- **主要提交者**: Shiqiao Gu (谷石桥)

## AI分析总结

好的，根据您提供的仓库README摘要和提交记录，以下是昨日更新的要点分析：

### 1. 主要更新类型

*   **重构**：对VAE（变分自编码器）配置中的数据类型处理逻辑进行了重构。
*   **功能更新**：更新了自回归（AR）模型的相关代码。

### 2. 关键变更点及其与项目整体方向的关系

*   **VAE数据类型处理重构 (`ba61815`)**：
    *   **变更点**：重构了VAE配置中的`dtype`（数据类型）处理方式。
    *   **与项目关系**：LightX2V是一个**轻量级视频生成推理框架**。VAE是视频生成模型（如扩散模型）中的关键组件，负责将视频压缩到潜在空间。重构数据类型处理，通常是为了提高代码的健壮性、可维护性，或为支持更广泛的硬件（如不同精度的GPU）做准备，这与项目“轻量”和“高效推理”的目标一致。

*   **更新自回归模型 (`27e5c90`)**：
    *   **变更点**：更新了自回归（AR）模型的相关实现。
    *   **与项目关系**：自回归模型是视频生成的另一条重要技术路线（如CogVideo、Emu Video等）。更新AR模型表明项目正在**扩展其支持的模型架构**，不局限于扩散模型，旨在成为一个更通用的视频生成推理框架。

### 3. 对项目的影响和潜在意义

*   **提升代码质量与兼容性**：VAE数据类型处理的重构，可以减少因数据类型不匹配导致的推理错误，并可能为未来支持FP8、INT8等低精度推理铺平道路，从而**提升推理速度和降低显存占用**。
*   **扩展模型生态**：更新AR模型意味着框架正在积极适配更多类型的视频生成模型。这能**吸引更多用户和开发者**，使LightX2V成为一个更全面的解决方案，而不仅仅是某个特定模型的推理工具。

### 4. 值得关注的技术点

*   **VAE的`dtype`处理**：重构的具体细节值得关注，例如是否引入了更灵活的配置方式（如自动检测硬件支持的数据类型），或者统一了不同模型VAE的精度管理逻辑。这直接关系到推理的稳定性和性能。
*   **AR模型的更新内容**：需要查看具体更新了哪些AR模型（例如，是否新增了对某个热门开源AR视频模型的支持），以及更新是否涉及性能优化或bug修复。

### 5. 基于项目背景的综合影响

*   **强化“轻量”与“通用”定位**：LightX2V的目标是“轻量视频生成推理框架”。本次更新通过重构核心组件（VAE）和扩展支持模型类型（AR模型），**同时提升了框架的健壮性和通用性**。这有助于项目在竞争激烈的视频生成推理领域（如与Hugging Face Diffusers等框架对比）中，突出其轻量、高效且支持模型多样的特点。
*   **推动项目成熟度**：重构和模型更新是项目走向成熟的重要标志。这表明项目团队不仅关注功能实现，也注重代码质量和生态建设，为后续的稳定版本发布和社区贡献打下了基础。

## 详细提交记录

### [ba61815](https://github.com/ModelTC/LightX2V/commit/ba61815406df5f81cfd824a11c95241c9b7ad9a7)

- **作者**: Shiqiao Gu (谷石桥)
- **时间**: 2026-06-03T08:04:08Z
- **提交信息**: Refactor dtype handling in VAE configuration (#1117)

### [27e5c90](https://github.com/ModelTC/LightX2V/commit/27e5c906eacfc894abc22c3ecf4cb7689d5b6db3)

- **作者**: Shiqiao Gu (谷石桥)
- **时间**: 2026-06-03T07:28:42Z
- **提交信息**: update ar models (#1110)

Co-authored-by: root <root@pt-1c1e8af781e1483583621882e0652eec-worker-0.pt-1c1e8af781e1483583621882e0652eec.ns-devsft-3460edd0.svc.cluster.local>

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-06-04
**监控日期**: 2026-06-03
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2111
- **最后更新**: 2026-06-03T02:22:09Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-06-04
**监控日期**: 2026-06-03
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5736
- **最后更新**: 2026-06-03T22:11:49Z

## 提交统计

- **昨日提交总数**: 5
- **提交者数量**: 5
- **主要提交者**: Yong Wu, Mingyang Wang, Ziang Li

## AI分析总结

好的，作为专业的代码分析助手，我将结合项目背景，对 `flashinfer-ai/flashinfer` 仓库昨日的提交记录进行分析和总结。

### 昨日更新要点总结

**项目背景回顾**：FlashInfer 是一个专注于**高性能 GPU 推理内核**的库，其核心目标是提供高效、易用的算子（如注意力、MoE、量化等），以加速大语言模型（LLM）的推理过程。

---

#### 1. 主要更新类型

- **功能新增**：2项
- **Bug修复**：1项
- **重构/代码清理**：1项
- **API改进**：1项

#### 2. 关键变更点及其与项目整体方向的关系

*   **功能新增：NVFP4 4over6 量化后端 (CuTe DSL)** (`d9b175a`)
    *   **变更点**：为 NVFP4 量化算法新增了一个基于 CuTe DSL（一种用于编写 GPU 内核的领域特定语言）的 4over6 量化后端。该后端支持 per-token 和 per-tensor 两种激活量化模式，并提供了 MAE/MSE 两种误差度量模式。
    *   **与项目方向的关系**：**高度契合**。FlashInfer 的核心目标之一是提供高性能的推理内核。量化是降低模型显存占用和计算延迟的关键技术。引入 CuTe DSL 后端，旨在利用其表达能力和优化潜力，**显著提升量化内核的性能**（提交中的基准测试显示，CuTe DSL 后端相比 CUDA 后端有 2-4 倍的加速）。这直接服务于项目“高性能”的核心目标。

*   **功能新增：MoE 路由回放输出** (`b54d28b`)
    *   **变更点**：为 FlashInfer 自定义的 MoE（混合专家）路由内核增加了 `routing_replay_out` 功能。现在，所有非 DeepSeekV3 的路由方法（如 Renormalize, TopK 等）也能正确地将选中的专家 ID 写入到调用者提供的缓冲区中。
    *   **与项目方向的关系**：**增强项目完整性和实用性**。MoE 是当前 LLM 扩展的关键架构。提供完整的路由信息回放功能，对于需要记录或分析路由决策的调试、监控和高级推理调度场景至关重要。这填补了功能空白，使 FlashInfer 的 MoE 支持更加成熟和可靠。

*   **Bug修复：修复测试资源汇总时的间歇性 SIGPIPE 错误** (`7a263cd`)
    *   **变更点**：修复了在运行完整单元测试时，由于 `scripts/test_utils.sh` 脚本中 `sort | head | awk` 管道链引发的间歇性 `exit code 141 (SIGPIPE)` 错误。通过将 `head` 的逻辑合并到 `awk` 中，避免了 `sort` 进程因管道被提前关闭而收到 SIGPIPE 信号。
    *   **与项目方向的关系**：**提升项目稳定性和开发者体验**。一个稳定可靠的 CI/CD 流程是高质量开源项目的基石。修复这种“假阳性”的测试失败，能确保开发者对测试结果的信任，避免因基础设施问题浪费调试时间，从而保障项目持续、健康地发展。

*   **重构：替换已弃用的 CuTe API** (`335ba37`)
    *   **变更点**：将代码中已弃用的 `cute::make_fragment` 调用替换为新的 `cute::make_rmem_tensor`。
    *   **与项目方向的关系**：**维护代码健康和前瞻性**。这是典型的“技术债务”清理工作。及时跟进上游依赖（CuTe）的 API 变更，可以避免未来因 API 移除导致的编译错误，确保项目能持续集成最新的 CuTe 优化和特性，是项目长期健康发展的必要投入。

*   **API改进：支持 TRTLLM API 中的 LSE 缓冲区** (`2c30bc2`)
    *   **变更点**：改进了 FlashInfer 中直接调用 TRTLLM-Gen 的 Paged Attention API 的行为。现在，即使 `return_lse=False`，只要调用者提供了 `lse` 缓冲区，内核也会填充它。这解决了 Issue #2755。
    *   **与项目方向的关系**：**增强灵活性和互操作性**。LSE（Log-Sum-Exp）缓冲区对于某些高级采样算法（如 Min P、Top P 的某些实现）是必需的。此改动允许用户在不开启 `return_lse` 功能（可能带来额外开销）的情况下，通过提供自己的缓冲区来获取 LSE 值，提供了更细粒度的控制，增强了与 TRTLLM 生态的兼容性。

#### 3. 对项目的影响和潜在意义

*   **性能提升**：`NVFP4 4over6` 的 CuTe DSL 后端是本次更新中**最具影响力**的变更。它直接带来了数倍的量化性能提升，这对于需要高吞吐量推理的 LLM 服务场景意义重大。
*   **功能完善**：`MoE 路由回放` 和 `LSE 缓冲区支持` 填补了重要功能缺口，使 FlashInfer 在 MoE 和 Attention 这两个核心推理组件上更加完备和灵活。
*   **可靠性提升**：`SIGPIPE 修复` 提升了 CI 流程的可靠性，是项目走向成熟的重要标志。
*   **技术债务清理**：`CuTe API 替换` 确保了代码

## 详细提交记录

### [7a263cd](https://github.com/flashinfer-ai/flashinfer/commit/7a263cd3a704db2fd642ed40ae6d03ae7a8f164d)

- **作者**: Yong Wu
- **时间**: 2026-06-03T22:11:43Z
- **提交信息**: fix intermittent exit 141 (SIGPIPE) in test resource summary (#3498)

<!-- .github/pull_request_template.md -->

## 📌 Description

## 📌 Description

Full unit test runs (e.g. H100) intermittently failed with exit code 141
**even when all tests passed**, right after printing the "TEST RUN
RESOURCE SUMMARY" tables. (The failed workflow job:
https://github.com/flashinfer-ai/flashinfer/actions/runs/26796385673/job/78993606387
)

root cause: `print_top_resource_rows` in `scripts/test_utils.sh` used
`sort | head -10 | awk`. `head` closes the pipe after 10 lines, sending
SIGPIPE to `sort`. Under the script's `set -eo pipefail`, that SIGPIPE
(141) becomes the exit code of the whole run. Whether it triggers
depends on a buffering/scheduling race between `sort` finishing its
writes and `head` closing — hence the intermittency (different summary
tables died on different runs; some runs passed entirely).

Fix: Move the "top 10" limit into awk (`NR <= 10`) and drop `head`, so
awk reads `sort`'s full output to EOF — the pipe never closes early and
SIGPIPE cannot occur. Output is unchanged.


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

* **Bug Fixes**
* Improved stability of test utility scripts to prevent failures during
execution in certain conditions.
* Fixed test selection fallback behavior to gracefully handle edge
cases.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [d9b175a](https://github.com/flashinfer-ai/flashinfer/commit/d9b175ac61a5f20367fc3392243f74a87704680f)

- **作者**: Ziang Li
- **时间**: 2026-06-03T19:40:25Z
- **提交信息**: Add CuTe DSL NVFP4 quantization with 4over6 FP16 scoring (#3448)

<!-- .github/pull_request_template.md -->

## 📌 Description

@humansand

Adds a CuTe DSL NVFP4 quantization backend with support for per-token
activation quantization and NVFP4 4over6 scale-candidate selection.

The 4over6 configuration remains environment-driven to match the
existing kernel configuration flow:

- `FLASHINFER_NVFP4_4OVER6=1`
- `FLASHINFER_NVFP4_4OVER6_ERR_MODE=MAE|MSE`
- `FLASHINFER_NVFP4_4OVER6_ERR_USE_FAST_MATH=0|1`
- `FLASHINFER_NVFP4_4OVER6_E4M3_USE_256=0|1`
- `FLASHINFER_DISABLE_FP4_QUANT_FAST_MATH=0|1`
- C++ dispatch also accepts `TRTLLM_DISABLE_FP4_QUANT_FAST_MATH=1` as a
compatibility fallback. Python/CuTe DSL paths use the FlashInfer env
name.

The public 4over6 error-mode surface is now only `MAE` and `MSE`. The
former FP16-specific public modes were removed. Instead,
`FLASHINFER_NVFP4_4OVER6_ERR_USE_FAST_MATH` selects the candidate-error
contract:

- `0`: strict full-dequant candidate scoring with explicit RN
arithmetic.
- Per-token NVFP4 uses the online row amax and scores candidates with
the TE-style expression `(e2m1 * sf * global_amax) / (6 * e4m3_max)`.
- Per-tensor NVFP4 uses the global decode scale path derived from the
provided global scale, rather than materializing a separate global amax
in the Python API. This avoids adding an always-on input reduction for
per-tensor callers.
  - CUDA and CuTe DSL follow the same per-token/per-tensor split.
- `1`: FP16-domain candidate scoring. Candidates are decoded through the
E2M1 x E4M3 FP16 conversion path and compared against `x *
global_encode_scale`; this path also uses explicit RN arithmetic for
candidate error scoring.

~~Earlier revisions treated the strict full-dequant path as a single
TE-style expression for both per-token and per-tensor NVFP4.~~ The
current contract only requires the TE expression for the per-token path
where amax is already computed online; per-tensor uses the existing
global decode scale expression to avoid extra overhead.

CUDA, CuTe DSL, and fused MoE dispatch all route through the shared
`NVFP44Over6Config<e4m3_max, err_mode, err_use_fast_math>`
configuration. The old 4over6 candidate-error paths that used
unqualified fast-math arithmetic were removed.

## 🔍 Related Issues

TE PR that implements the same contract:
- https://github.com/NVIDIA/TransformerEngine/pull/3068

Other relevant PRs:
- https://github.com/flashinfer-ai/flashinfer/pull/3387
- https://github.com/NVIDIA/TransformerEngine/pull/2972
- https://github.com/flashinfer-ai/flashinfer/pull/3264
- https://github.com/flashinfer-ai/flashinfer/pull/3027

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

Unit tests extended:

- `tests/test_helpers/utils_fp4.py` extends the TE-style NVFP4/4over6
reference path for both full-dequant scoring and FP16-domain scoring.
- `tests/utils/test_fp4_quantize.py` extends
`test_nvfp4_quantize_te_reference` to cover strict bitwise CUDA and CuTe
DSL agreement for NVFP4, per-token activation, scale-factor layouts,
zero inputs, and 4over6 MAE/MSE configurations.

Commands run:

```bash
pre-commit run --all-files
```

Passed.

```bash
python3 -m compileall \
  flashinfer/quantization/nvfp4_quantization_utils.py \
  tests/test_helpers/utils_fp4.py
```

Passed.

```bash
CUDA_VISIBLE_DEVICES=0 \
python3 -m pytest -q --tb=short tests/utils/test_fp4_quantize.py::test_nvfp4_quantize_te_reference
```

Passed: `9504 passed in 756.79s (0:12:36)`.

```bash
CUDA_VISIBLE_DEVICES=0 \
python3 -m pytest -q --tb=short tests/moe/test_trtllm_cutlass_fused_moe.py
```

Passed: `75 passed, 25 skipped, 1 warning in 74.79s (0:01:14)`.

```bash
CUDA_VISIBLE_DEVICES=0 \
python3 -m pytest -q --tb=short tests/moe/test_trtllm_gen_per_token_moe.py
```

Passed: `108 passed in 785.08s (0:13:05)`.

## Benchmarking

Updated benchmark run compares PR head (`b44e847b`) against the earliest
PR commit with CUDA 4over6 support (`e30a0b14`). The denominator for
every 4over6 speedup is the baseline CUDA 4over6 MSE no-fast time for
the same `(M, K)` case.

Common config:

- dtype: `bfloat16`
- scale-factor layout: `swizzled_128x4`
- `FLASHINFER_NVFP4_4OVER6=1`
- `FLASHINFER_NVFP4_4OVER6_ERR_MODE=MSE`
- `FLASHINFER_NVFP4_4OVER6_E4M3_USE_256=1`
- `FLASHINFER_DISABLE_FP4_QUANT_FAST_MATH=1`
- CUDA graph disabled, CUPTI timing enabled, cold L2 cache enabled

Per-token runs add `--per-token-activation`; per-tensor runs omit it.
`FLASHINFER_NVFP4_4OVER6_ERR_USE_FAST_MATH` is set to `0` for no-fast
rows and `1` for fast rows.

Each table cell is `geomean / min / max` speedup over the scanned M/K
cases.

| Activation scale | CUDA no fast math | CUDA fast math | CuTe DSL no
fast math | CuTe DSL fast math |
| --- | ---: | ---: | ---: | ---: |
| Per-tensor | 2.83x / 1.65x / 5.81x | 3.22x / 1.67x / 7.25x | 2.17x /
1.21x / 8.26x | 4.12x / 2.45x / 20.92x |
| Per-token | 0.89x / 0.71x / 0.98x | 1.41x / 1.05x / 3.40x | 2.05x /
1.03x / 2.89x | 3.00x / 1.80x / 4.17x |

Pure per-token NVFP4 without 4over6, same dtype/layout/quant-fast-math
setting:

| Mode | CuTe DSL vs CUDA geomean/min/max |
| --- | ---: |
| Pure per-token no 4over6 | 2.24x / 1.04x / 3.76x |

Heat maps:

![NVFP4 4over6 MSE per-tensor speedup heat
map](https://gist.githubusercontent.com/zianglih/1e1fdd42d27244692d66cd6a5b2b904f/raw/2f4f7965c0b57e7b148acdde64a632daa11072a6/nvfp4_4over6_mse_speedup_vs_baseline_per_tensor.svg)

![NVFP4 4over6 MSE per-token speedup heat
map](https://gist.githubusercontent.com/zianglih/1e1fdd42d27244692d66cd6a5b2b904f/raw/23fc9c84605795b9c17febac47f0175fc14c3a07/nvfp4_4over6_mse_speedup_vs_baseline_per_token.svg)

![NVFP4 pure per-token no-4over6 CuTe DSL vs CUDA heat
map](https://gist.githubusercontent.com/zianglih/1e1fdd42d27244692d66cd6a5b2b904f/raw/34e161c89dc0a23378c5d23041567953b8f7c9b2/nvfp4_pure_per_token_no_4over6_cute_vs_cuda.svg)

Previous benchmark snapshot kept for review context:

| Activation scale | Baseline CUDA no-fast geomean (ms) | CUDA no-fast |
CUDA fast | CuTe DSL no-fast | CuTe DSL fast |
| --- | ---: | ---: | ---: | ---: | ---: |
| Per-tensor | ~~0.074336~~ | ~~1.000x~~ | ~~1.668x~~ | ~~1.434x~~ |
~~1.738x~~ |
| Per-token | ~~0.065345~~ | ~~0.974x~~ | ~~1.554x~~ | ~~2.297x~~ |
~~3.267x~~ |

- ~~Previous benchmark run compared current PR head (`e5349fc2`) against
a pre-FP16-refactor baseline (`99a21fcd`).~~
- ~~Previous common config used
`FLASHINFER_NVFP4_4OVER6_E4M3_USE_256=0`.~~
- ~~Previous table reported only geomean speedup.~~

Full 22x15 per-case data was generated separately and kept out of the PR
body.

## Reviewer Notes

The 4over6 path can become compute-bound at large inputs. The benchmark
path keeps the built-in sweep and uses environment variables for 4over6
mode selection rather than adding 4over6-specific shape or mode CLI
arguments.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added 4over6 quantization mode for NVFP4 with configurable error
metrics (MAE/MSE)
  * Added per-token activation support for NVFP4 quantization
* Extended CuTe-DSL backend capabilities for improved quantization
operations

* **Documentation**
* Updated quantization benchmarks with new 4over6 mode configuration
examples
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Ziang Li <ziangli@umich.edu>

### [b54d28b](https://github.com/flashinfer-ai/flashinfer/commit/b54d28bea0639510d79c5ac58a60a4087585ff00)

- **作者**: Julien Debache
- **时间**: 2026-06-03T17:27:21Z
- **提交信息**: feat(moe): write routing_replay_out from custom routing kernels (#3382)

The custom routing dispatch in trtllm_fused_moe_runner.cu already plumbs
mPtrRoutingReplayOut to routingCustom::Data for all routing methods
(Default, Renormalize, RenormalizeNaive, TopK, SigmoidRenorm, Sigmoid,
MiniMax2), but the kernels themselves only set the pointer and skip the
write -- only the DeepSeekV3 path (in
trtllm_fused_moe_routing_deepseek.cu) actually records the selected
expert IDs. Callers that allocate a replay buffer for any non-DSV3
routing therefore observe uninitialized memory.

Mirror the DeepSeek write site in each of the five kernels that compute
top-K from raw scores in routingIndicesCustom:

  * routingIndicesBlockKernel        (<= 4 tokens)
  * routingIndicesDynBlockKernel     (<= 16 tokens)
  * routingIndicesClusterKernel      (<= 256 tokens, SM90+)
  * routingIndicesHistogramScoresKernel (warp-per-token, large BS)
  * routingIndicesBlockScoresKernel  (block-per-token, split path)

Each addition is a conditional int16 write next to the existing
mPtrTopKPacked / smemPackedScoreIdx / smemKIdx write, using the same
[num_tokens, topK] layout as the DeepSeek path. The pre-computed-topK
branches (mPtrTopKIds / mPtrTopKPacked input) are intentionally
untouched since the caller already knows the IDs.

Validated on B200 with bf16 trtllm_bf16_moe across Renormalize and
RenormalizeNaive at num_tokens in {2, 8, 64, 512} and top_k in {2, 4},
exercising each of the four main dispatch paths; captured buffer
contained valid expert IDs and top_k distinct experts per token.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [X] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [X] I have installed the hooks with `pre-commit install`.
- [X] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

- [X] Tests have been added or updated as needed.
- [X] All tests are passing (`unittest`, etc.).

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added routing replay output across multiple routing kernel paths to
record selected expert IDs per token/top-K position, without changing
inference behavior.

* **Tests**
* Added tests covering multiple routing methods and kernel tiers;
validate replay buffer contents are in-range, per-token selections are
distinct, rows beyond active tokens keep the sentinel value, and outputs
match with/without replay enabled.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 4.7 (1M context) <noreply@anthropic.com>

### [335ba37](https://github.com/flashinfer-ai/flashinfer/commit/335ba37fdbb46d279fe922685d6a075b20e09333)

- **作者**: brandonsun
- **时间**: 2026-06-03T17:09:36Z
- **提交信息**: NFC: replace deprecated API: cute.make_fragment (#3473)

<!-- .github/pull_request_template.md -->

## 📌 Description

More mechanical change to replace deprecated API:

- cute.make_fragment --> cute.make_rmem_tensor

## 🔍 Related Issues

N/A

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

N/A

## 🧪 Tests

- [ ] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

N/A

## Reviewer Notes

N/A


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Refactor**
* Updated internal tensor representation in GPU kernel epilogue
operations for block-scaled matrix computations to improve
implementation consistency.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [2c30bc2](https://github.com/flashinfer-ai/flashinfer/commit/2c30bc287b832a510b631db25a3713c42945a2ad)

- **作者**: Mingyang Wang
- **时间**: 2026-06-03T16:46:59Z
- **提交信息**: Support LSE buffers in TRTLLM API (#3410)

<!-- .github/pull_request_template.md -->

## 📌 Description

This PR updates the direct TRTLLM-Gen paged attention APIs so a
caller-provided `lse` buffer is honored independently from `return_lse`.

- `flashinfer.decode.trtllm_batch_decode_with_kv_cache` now validates
and passes a provided `lse` buffer to the TRTLLM-Gen kernel even when
`return_lse=False`.
- Direct decode/context API docs now state that a provided `lse` buffer
is filled regardless of `return_lse`.
- `tests/attention/test_trtllm_gen_attention.py` adds focused direct
TRTLLM-Gen coverage for the `return_lse` x caller-provided `lse` matrix.

The wrapper API scope is intentionally unchanged; this PR only covers
the direct TRTLLM APIs.

## 🔍 Related Issues

Fixes #2755

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

Validation run:

- `uv run python -m py_compile
tests/attention/test_trtllm_gen_attention.py`
- `git diff --check`
- pre-commit hooks during commit: passed

Focused pytest collection/runtime was not rerun locally because the
worktree venv lacks `pytest`.

## Reviewer Notes

The direct test helper uses `return_lse=None` as an internal auto mode
so existing broad tests keep their previous `return_lse=check_lse`
behavior. The focused LSE contract tests pass explicit booleans to cover
all four direct API cases.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Ensure provided LSE buffers are always filled; allocate a new LSE
buffer only when LSE return is requested.

* **Documentation**
* Clarified LSE parameter behavior in batch prefill and decode
operations.

* **Tests**
* Added parametrized LSE contract tests for prefill and decode, with
conditional validation depending on reference availability and backend
support.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-06-04
**监控日期**: 2026-06-03
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3675
- **最后更新**: 2026-06-03T22:19:30Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-06-04
**监控日期**: 2026-06-03
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 33768
- **最后更新**: 2026-06-03T22:03:55Z

## 提交统计

- **昨日提交总数**: 5
- **提交者数量**: 4
- **主要提交者**: Wang, Yi, Dhruv Nair, Akshan Krithick

## AI分析总结

好的，根据您提供的仓库README摘要和提交记录，以下是对昨日更新的分析总结：

### 昨日更新要点总结

#### 1. 主要更新类型

*   **功能新增**: 新增了对 `Ideogram 4` 文本到图像模型的支持。
*   **重构**: 对多个自动编码器（Autoencoder）的测试代码进行了大规模重构。
*   **Bug修复/兼容性**: 修复了CI测试中的导入问题，并更新了测试以支持XPU设备。

#### 2. 关键变更点及其与项目整体方向的关系

*   **新增 Ideogram 4 模型支持**:
    *   **变更**: 添加了完整的 `Ideogram 4` 模型支持，包括Transformer、标准Pipeline、模块化Pipeline、文档和测试。同时，将注意力层从融合的 `qkv` 投影重构为标准的分裂 `to_q`/`to_k`/`to_v`/`to_out` 投影。
    *   **与项目方向关系**: 这直接体现了 `diffusers` 作为“最先进扩散模型库”的核心目标。通过集成 `Ideogram 4`，项目持续扩展其支持的模型生态，为用户提供更多样化、更强大的文本到图像生成选择。将注意力层重构为标准格式，也符合项目追求代码一致性、可维护性和可扩展性的方向。

*   **大规模重构自动编码器测试**:
    *   **变更**: 对 `VQModel`、`KVAE Video`、`Oobleck`、`Consistency Decoder VAE`、`Autoencoder Tiny`、`VidTok` 和 `CogVideoX` 等多个自动编码器的测试代码进行了重构。
    *   **与项目方向关系**: 这体现了项目对代码质量和测试基础设施的持续投入。重构测试代码（如移除未使用的变量、统一测试逻辑）是提升项目长期健康度、降低维护成本、确保新功能引入时不会破坏现有功能的关键举措。这与 `diffusers` 作为一个成熟、稳定库的定位相符。

*   **修复CI和硬件兼容性问题**:
    *   **变更**: 修复了 `AutoencoderTesterMixin` 中的 `torch_device` 导入问题，并更新了 `Marigold` 测试以在XPU设备上通过。
    *   **与项目方向关系**: 这些是典型的维护性工作。修复CI问题确保了自动化测试流程的可靠性，而XPU兼容性更新则扩展了项目的硬件支持范围，使其能更好地服务于使用Intel等非NVIDIA硬件的用户，符合项目“开放”和“广泛兼容”的理念。

#### 3. 对项目的影响和潜在意义

*   **正面影响**:
    *   **用户**: 用户现在可以直接使用 `diffusers` 调用 `Ideogram 4` 模型，无需额外适配，降低了使用门槛。
    *   **开发者**: 重构后的测试代码更清晰、更易于维护和扩展，为未来添加新的自动编码器或修改现有逻辑提供了更坚实的基础。
    *   **项目**: 增强了项目的模型库丰富度和代码健壮性，巩固了其在扩散模型领域的领先地位。

*   **潜在意义**:
    *   `Ideogram 4` 的加入可能吸引更多用户和开发者关注 `diffusers`，尤其是在文本到图像生成领域。
    *   对注意力层的重构（从融合到分裂）是一个重要的技术决策，表明项目倾向于采用更标准、更模块化的架构，这有利于社区贡献和模型间的代码复用。

#### 4. 值得关注的技术点

*   **注意力层重构**: 将 `Ideogram 4` 的融合 `qkv` 投影拆分为标准的 `to_q`/`to_k`/`to_v` 投影。这虽然数学上等价，但更符合 `diffusers` 的通用注意力层设计模式，使得模型可以更好地利用库内已有的优化（如Flash Attention）和工具。
*   **模块化Pipeline**: `Ideogram 4` 同时提供了标准Pipeline和模块化Pipeline，这体现了 `diffusers` 在API设计上的灵活性，允许用户根据需求选择不同粒度的控制。
*   **测试重构的深度**: 重构涉及了从 `VQ` 到 `VidTok` 等多种不同类型的自动编码器，说明这是一次系统性的代码清理，而非零散的修改。

#### 5. 基于README背景，这些提交如何影响项目发展

*   **强化“模型中心”地位**: 根据README，`diffusers` 的目标是成为“最先进的预训练扩散模型库”。新增 `Ideogram 4` 直接服务于这一目标，通过集成来自不同研究团队和公司的模型，使项目成为一个更全面的模型集散地。
*   **提升“模块化”与“可扩展性”**: README强调项目设计是“模块化的”。将 `Ideogram 4` 的注意力层重构为标准形式，以及提供模块化Pipeline，都是对这一设计原则的践行。这使得模型更容易被理解、修改和与其他组件组合。
*   **保障“可靠性”与“质量”**: README提及项目提供了“高质量的Pipeline和模型”。大规模重构测试代码、修复CI问题，正是为了确保代码库的长期可靠性和质量，防止因代码腐化而影响用户体验。
*   **促进“社区贡献”**: 通过统一代码风格（如注意力层）和清理测试基础设施，项目降低了社区贡献的门槛。新的贡献者可以更容易地理解代码结构并为其添加新模型或功能，从而形成一个良性循环，推动项目持续发展。

## 详细提交记录

### [9b0818c](https://github.com/huggingface/diffusers/commit/9b0818cf87413b4b9ca2501bf49406eed6d881af)

- **作者**: apolinário
- **时间**: 2026-06-03T22:03:48Z
- **提交信息**: Add Ideogram 4 (#13859)

* Add Ideogram 4

Adds the Ideogram 4 text-to-image model: transformer, standard pipeline,
modular pipeline, docs, and tests.

Checkpoint: ideogram-ai/ideogram-4-nf4

Co-Authored-By: YiYi Xu <yiyi@huggingface.co>

* Use split q/k/v projections in Ideogram4 attention

Replace the fused `qkv`/`o` linears with canonical `to_q`/`to_k`/`to_v`/`to_out`
projections, matching the standard diffusers attention layout and the split
checkpoint format. Mathematically equivalent to the fused form (q/k/v are
contiguous row-slices of the fused weight). Drops the now-inapplicable
fuse/unfuse overrides.

---------

Co-authored-by: Jin <jin.li@ideogram.ai>
Co-authored-by: YiYi Xu <yiyi@huggingface.co>

### [f34de43](https://github.com/huggingface/diffusers/commit/f34de4330ee0d7b931aaf77b4176886e74cf797f)

- **作者**: Dhruv Nair
- **时间**: 2026-06-03T19:05:18Z
- **提交信息**: [CI] Fix `torch_device` import in AutoencoderTesterMixin (#13852)

update

### [525d483](https://github.com/huggingface/diffusers/commit/525d483add6652ee2fe1da051d209040c24e7075)

- **作者**: Wang, Yi
- **时间**: 2026-06-03T10:53:41Z
- **提交信息**: updatge the test marigold to make it pass in xpu (#13856)

Signed-off-by: Wang, Yi <yi.a.wang@intel.com>
Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

### [4c77dcd](https://github.com/huggingface/diffusers/commit/4c77dcdbac6c75c8a1fdfaa1657c70f8930c8f3e)

- **作者**: Akshan Krithick
- **时间**: 2026-06-03T08:00:57Z
- **提交信息**: refactor autoencoder tests (vq, kvae_video, oobleck, consistency_decoder, tiny, vidtok) (#13849)

* refactor vq tests

* refactor autoencoder_kl_kvae_video tests

* refactor autoencoder_oobleck tests

* refactor consistency_decoder_vae tests

* refactor autoencoder_tiny tests

* refactor autoencoder_vidtok tests

* remove unused base_precision and test_outputs_equivalence skips

---------

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

### [334ef1a](https://github.com/huggingface/diffusers/commit/334ef1aa1fae89a5a14955d40fa1ca453396198e)

- **作者**: Akshan Krithick
- **时间**: 2026-06-03T07:17:48Z
- **提交信息**: refactor autoencoder_kl_cogvideox tests (#13840)

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-06-04
**监控日期**: 2026-06-03
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 410
- **最后更新**: 2026-06-03T21:05:47Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-06-04
**监控日期**: 2026-06-03
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12527
- **最后更新**: 2026-06-03T19:14:45Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-06-04
**监控日期**: 2026-06-03
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 28929
- **最后更新**: 2026-06-03T23:56:11Z

## 提交统计

- **昨日提交总数**: 34
- **提交者数量**: 25
- **主要提交者**: Chunan Zeng, Ye (Charlotte) Qi, ybyang

## AI分析总结

好的，作为专业的代码分析助手，以下是对仓库 `sgl-project/sglang` 昨日提交记录的分析总结。

### 昨日更新要点分析

#### 1. 主要更新类型

- **Bug修复 (Bug Fixes):** 占比最高，涉及AMD平台、TokenizerManager、MLA解码、MOE、HiCache等多个模块。
- **性能优化 (Performance Optimization):** 包括融合Triton内核、优化扩散模型KV通信、统一CUDA图输入缓冲区等。
- **功能新增 (New Features):** 支持无编码器的统一文本/视觉/音频模型、集成`flash_mla_sparse_fwd`、为Mamba添加延迟缓冲区支持。
- **文档更新 (Documentation):** 更新了多个模型的使用指南和部署命令。
- **重构 (Refactoring):** 统一了`full→SWA`索引转换逻辑、重构了CUDA图运行器输入缓冲区管理。
- **CI/测试 (CI/Testing):** 增加了AMD平台的夜间测试覆盖、为NPU扩散模型生成CI基准数据。
- **依赖更新 (Dependency Updates):** 升级了FlashInfer和cuDNN。

#### 2. 关键变更点及其与项目整体方向的关系

- **AMD平台支持强化 (AMD Platform Enhancement):**
    - **修复:** 修复了DeepSeek-R1在TP2配置下的MLA解码崩溃问题 (`cfb7fb4`)；修复了Kimi-K2.6在gfx942上的挂起问题 (`8e77af1`)。
    - **优化:** 将`compress norm+rope+hadamard`融合为单个Triton内核 (`1dd9432`)。
    - **测试:** 增加了夜间测试覆盖 (`cfb7fb4`)，移除了硬编码路径 (`d7013b6`)。
    - **关系:** 这与项目README中强调的“支持多种硬件后端”高度一致。这些提交显著提升了SGLang在AMD GPU上的稳定性和性能，是项目拓展硬件生态的关键步骤。

- **模型支持与推理优化 (Model Support & Inference Optimization):**
    - **新模型:** 支持了无编码器的统一文本/视觉/音频模型 (`fa5c8a3`)，这符合README中“支持多种模型架构”的目标，特别是多模态模型。
    - **MLA优化:** 集成了`flash_mla_sparse_fwd` (`93173b2`)，这是对DeepSeek等模型使用的Multi-head Latent Attention (MLA) 的稀疏化加速，直接提升推理效率。
    - **投机解码 (Speculative Decoding):** 重新实现了`spec v2 tree drafting` (`ac99794`)，这是对高级推理加速技术的持续迭代。
    - **关系:** 这些更新直接服务于项目核心目标——提供高性能、多模型支持的推理引擎。

- **基础设施与代码质量 (Infrastructure & Code Quality):**
    - **重构:** 统一了`full→SWA`索引转换 (`c9ca56d`)，重构了CUDA图运行器输入缓冲区 (`45604a0`)，提升了代码的可维护性和一致性。
    - **Bug修复:** 修复了`TokenizerManager`崩溃 (`7716ba0`)、`trace_modules`门控问题 (`578f232`)等，提升了系统的健壮性。
    - **关系:** 这些是项目长期健康发展的基础，确保了核心逻辑的稳定和可扩展性。

#### 3. 对项目的影响和潜在意义

- **提升AMD平台竞争力:** 通过修复关键bug和性能优化，SGLang在AMD GPU上的可用性和性能得到显著提升，有助于吸引更多AMD用户，扩大项目影响力。
- **加速多模态模型推理:** 支持无编码器多模态模型和优化MLA，直接提升了当前最热门的多模态和长上下文模型的推理效率，增强了项目的技术领先性。
- **增强系统稳定性:** 修复了多个可能导致服务崩溃的bug（如TokenizerManager、MOE），对于生产环境的部署至关重要。
- **降低开发者门槛:** 更新文档和移除硬编码路径，使得新用户和开发者更容易上手和贡献代码。

#### 4. 值得关注的技术点

- **`flash_mla_sparse_fwd` 集成:** 这是一个非常前沿的优化技术，通过稀疏化计算来加速MLA，对于DeepSeek等模型有重大意义。
- **Triton内核融合:** 将多个操作融合为一个Triton内核 (`1dd9432`)，是减少Kernel Launch开销、提升GPU利用率的标准且有效的优化手段。
- **CUDA图输入缓冲区重构:** `CudaGraphBufferRegistry` (`45604a0`) 的引入，为CUDA图捕获提供了更灵活、更统一的输入管理方式，是优化推理延迟的关键基础设施。
- **HiCache相关修复:** 对HiCache (推测是高性能缓存) 的多次修复 (`f65aae8`, `978fb6e`)，表明项目在优化KV Cache管理方面持续投入，这对于长序列推理至关重要。

#### 5. 基于项目背景，这些提交如何影响项目发展

- **巩固“多硬件、多模型”定位:** 对AMD平台的持续投入和对新模型架构（无编码器多模态、MLA）的支持，直接强化了README中“支持多种硬件后端和模型架构”的核心定位，使SGLang成为一个更具通用性的推理框架。
- **向“生产级”推理引擎迈进:** 大量的Bug修复、稳定性增强（如TokenizerManager、MOE）以及CI/测试的完善，表明项目正从研究原型向生产级系统演进，这对于吸引企业

## 详细提交记录

### [cfb7fb4](https://github.com/sgl-project/sglang/commit/cfb7fb4fad032687306d357f7dbdd4b1c67e1db9)

- **作者**: Clint
- **时间**: 2026-06-03T23:56:05Z
- **提交信息**: [AMD] Fix TP2 DeepSeek-R1 nhead=64 MLA decode crash and add nightly coverage (#27188)

Co-authored-by: clintg6 <7388379+clintg6@users.noreply.github.com>

### [c9ca56d](https://github.com/sgl-project/sglang/commit/c9ca56da8c5e79ed731570859c06204bfb8a6964)

- **作者**: Cheng Wan
- **时间**: 2026-06-03T23:12:27Z
- **提交信息**: Unify full→SWA index translation in init_forward_metadata; drop pool caches (#27091)

Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>

### [8980eb8](https://github.com/sgl-project/sglang/commit/8980eb82de90f0d25dcaed3c9d1cc8c4ac4c3776)

- **作者**: Yihao Wang
- **时间**: 2026-06-03T21:55:30Z
- **提交信息**: [Docs] Update Nemotron3-Nano-Omni cookbook to reflect new model paths (#25198)

### [61aa329](https://github.com/sgl-project/sglang/commit/61aa3293d35a010ab610acf46d401ba03cb5ff22)

- **作者**: Cheng Wan
- **时间**: 2026-06-03T21:53:28Z
- **提交信息**: Revert "Fix TokenizerManager crash on top_logprobs with tensor values" (#27187)

### [9098511](https://github.com/sgl-project/sglang/commit/90985117a5f7b13fdd4374e2115716b0e18ec448)

- **作者**: Jiajun Li
- **时间**: 2026-06-03T21:52:47Z
- **提交信息**: docs: fix Nemotron Super MTP deployment command (spec-v2 + B200) (#27184)

Co-authored-by: zijiexia <37504505+zijiexia@users.noreply.github.com>

### [978fb6e](https://github.com/sgl-project/sglang/commit/978fb6ed1a1f113a46201439453dfc1313368109)

- **作者**: ishandhanani
- **时间**: 2026-06-03T21:52:25Z
- **提交信息**: hicache kv events: publish split write-through fragments (#27072)

### [1dd9432](https://github.com/sgl-project/sglang/commit/1dd9432889b756b46799274ae91559d59a47136e)

- **作者**: jacky.cheng
- **时间**: 2026-06-03T21:20:40Z
- **提交信息**: [AMD] Fuse compress norm+rope+hadamard into single Triton kernel (#26894)

### [c670609](https://github.com/sgl-project/sglang/commit/c670609ac5e4b73ede1643b1956762153f2afb38)

- **作者**: Elizaveta Martirosian
- **时间**: 2026-06-03T21:14:37Z
- **提交信息**: [NPU] Diffusion CI Ground Truth Generation (NPU) (#24630)

Co-authored-by: github-actions[bot] <github-actions[bot]@users.noreply.github.com>
Co-authored-by: Elizaveta Martirosian <you@example.com>
Co-authored-by: Elizaveta Martirosian <elizaveta.martirosian@gmail.com>
Co-authored-by: ronnie_zheng <zl19940307@163.com>

### [e485ad6](https://github.com/sgl-project/sglang/commit/e485ad6ac1a4723d15f2c1450150744a314ce61d)

- **作者**: Cheng Wan
- **时间**: 2026-06-03T21:11:14Z
- **提交信息**: Fix hybrid linear attention dispatch by layer id with draft-worker awareness (#27120)

Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>

### [7716fa0](https://github.com/sgl-project/sglang/commit/7716fa00e0efd03960fe2c3abfb09ce155aaf5ef)

- **作者**: Kevin Flansburg
- **时间**: 2026-06-03T20:55:02Z
- **提交信息**: Fix TokenizerManager crash on top_logprobs with tensor values (#26825)

### [d1bc06b](https://github.com/sgl-project/sglang/commit/d1bc06b63b459d57d917d7ba3046c3ec3b8d6ed6)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-06-03T20:38:34Z
- **提交信息**: [AMD] Disable AITER custom all-gather in DeepSeek-R1-MXFP4 8-GPU test (#27163)

### [293816a](https://github.com/sgl-project/sglang/commit/293816ab14afad98add682c36be383257f69f547)

- **作者**: fxmarty-amd
- **时间**: 2026-06-03T19:55:24Z
- **提交信息**: [AMD][MXFP4] Online MXFP4 quantization 1/N - dense and MOE models w. original BF16 weight (#18005)

Co-authored-by: Bowen Bao <bowenbao@amd.com>
Co-authored-by: Colin Zeng <Colin.Zeng@amd.com>

### [e0b6926](https://github.com/sgl-project/sglang/commit/e0b692600f1072af46846aa83a14520125974aa2)

- **作者**: Hanming Lu
- **时间**: 2026-06-03T19:42:11Z
- **提交信息**: [Mamba] extra buffer lazy support (#27118)

Co-authored-by: YAMY <74099316+YAMY1234@users.noreply.github.com>

### [ac99794](https://github.com/sgl-project/sglang/commit/ac99794e64e054224dbdd52b4318629ad06540c8)

- **作者**: Liangsheng Yin
- **时间**: 2026-06-03T19:40:05Z
- **提交信息**: Reland spec v2 tree drafting (eagle topk>1) with page_size==1 (#26866) (#26997)

Co-authored-by: Alison Shao <54658187+alisonshao@users.noreply.github.com>

### [7f706f4](https://github.com/sgl-project/sglang/commit/7f706f4cfba061b906cb11298abe39b3dc5d4279)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-06-03T19:09:18Z
- **提交信息**: [Deps] Bump FI to 0.6.12 and cutedsl to 4.5.2 (#26854)

### [578f232](https://github.com/sgl-project/sglang/commit/578f232e5e059b6c16622754b7c565594b7a8e3f)

- **作者**: Liangsheng Yin
- **时间**: 2026-06-03T18:03:42Z
- **提交信息**: Fix trace_modules gate disabling default trace contexts (#27173)

### [45604a0](https://github.com/sgl-project/sglang/commit/45604a0f4a7f378c4e7b0e435b49257b6242ca0a)

- **作者**: Cheng Wan
- **时间**: 2026-06-03T17:54:10Z
- **提交信息**: [refactor] Unify CUDA graph runner input buffers behind CudaGraphBufferRegistry (#26742)

Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [b0f78be](https://github.com/sgl-project/sglang/commit/b0f78bef97b31f197fb1e3af3303dbac9e544e6d)

- **作者**: Mick
- **时间**: 2026-06-03T16:33:56Z
- **提交信息**: [diffusion] improve: improve realtime webui playback pacing (#27148)

### [45a66f4](https://github.com/sgl-project/sglang/commit/45a66f4088acfe7142beb51f7f5c2178b1c73cd4)

- **作者**: Xinyuan Tong
- **时间**: 2026-06-03T16:32:08Z
- **提交信息**: [Docs] Update unified Text/Vision/Audio model cookbook: install + sgl-eval accuracy (#27171)

### [9d0e6a2](https://github.com/sgl-project/sglang/commit/9d0e6a2df41623105423738c767f1320686ba436)

- **作者**: Lijuan Tang
- **时间**: 2026-06-03T16:03:46Z
- **提交信息**: fix(mlx): set canary_manager and materialize overlap-loop inputs on Apple Silicon (#26882)

Signed-off-by: Xiaodong Ye <yeahdongcn@gmail.com>
Signed-off-by: LijuanTang94 <tang.lij@northeastern.edu>
Co-authored-by: Xiaodong Ye <yeahdongcn@gmail.com>

### [fa5c8a3](https://github.com/sgl-project/sglang/commit/fa5c8a31015bf3792d78f2d41b3433a600b8a900)

- **作者**: Xinyuan Tong
- **时间**: 2026-06-03T15:58:06Z
- **提交信息**: [model] support encoder-free unified Text/Vision/Audio model (#27167)

### [f65aae8](https://github.com/sgl-project/sglang/commit/f65aae849366cfab82cd027a722a67ec7193f454)

- **作者**: shuwenn
- **时间**: 2026-06-03T14:06:18Z
- **提交信息**: [HiCache] fix: truncate prefetch key on degraded allocation (#25991)

### [33f943f](https://github.com/sgl-project/sglang/commit/33f943fbf57ba3e5ea83c1137c6e5a0b4dc4c0f4)

- **作者**: Mick
- **时间**: 2026-06-03T13:22:39Z
- **提交信息**: [diffusion] optimize: batch usp replicated kv prefix all-to-all (#27143)

### [03c77dc](https://github.com/sgl-project/sglang/commit/03c77dc33d0a051aa15c1235407440d9d107b98f)

- **作者**: Ye (Charlotte) Qi
- **时间**: 2026-06-03T11:08:15Z
- **提交信息**: [PD] Deduplicate PD logprob normalization (#27085)

### [44d4a25](https://github.com/sgl-project/sglang/commit/44d4a25a077ae04366407fc767e3b79c35d86332)

- **作者**: Ke Bao
- **时间**: 2026-06-03T10:57:25Z
- **提交信息**: Type hicache transfer hook kwargs in unified cache (#27071)

### [d7013b6](https://github.com/sgl-project/sglang/commit/d7013b6537b283cdd1e889fa7a2aa8fc88106a42)

- **作者**: Bingxu Chen
- **时间**: 2026-06-03T09:14:32Z
- **提交信息**: [AMD] [CI] Remove hardcoded model/cache paths from MI35x nightly tests (#27001)

### [e67810b](https://github.com/sgl-project/sglang/commit/e67810bea71f515f4ba83f82c8058480f5d3a2dc)

- **作者**: Feng Su
- **时间**: 2026-06-03T08:43:29Z
- **提交信息**: [SGLang Tracing] Add pd disaggregation mooncake backend tracing (#23755)

Co-authored-by: Mu Huai <tianbowen.tbw@antgroup.com>
Co-authored-by: Shangming Cai <csmthu@gmail.com>

### [73b53e7](https://github.com/sgl-project/sglang/commit/73b53e7a873821c1bfd1c1a56732d22e1357b28b)

- **作者**: Cheng Wan
- **时间**: 2026-06-03T08:29:52Z
- **提交信息**: Revert "Support NextN = 2/4 in DSV32" (#27138)

### [63dc20a](https://github.com/sgl-project/sglang/commit/63dc20ae6cc84b51c49994d83990d8d9e23f61de)

- **作者**: Vladislav Nosivskoy
- **时间**: 2026-06-03T08:10:27Z
- **提交信息**: [UnifiedTree] Add CP sync (#25395)

Co-authored-by: Zhangheng <hzh0425@apache.org>

### [93173b2](https://github.com/sgl-project/sglang/commit/93173b27e8a656bd3bbc9319cdd97acf23a35655)

- **作者**: Chunan Zeng
- **时间**: 2026-06-03T08:09:25Z
- **提交信息**: integrate flash_mla_sparse_fwd (#25418)

Co-authored-by: Yuan Luo <yuan.luo@hotmail.com>
Co-authored-by: Baizhou Zhang <sobereddiezhang@gmail.com>
Co-authored-by: laixinn <q865809639@gmail.com>
Co-authored-by: MeowGrange <276466210+MeowGrange@users.noreply.github.com>
Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [f790674](https://github.com/sgl-project/sglang/commit/f790674ad8a59ddff20c5547cbf004ece8c24445)

- **作者**: ybyang
- **时间**: 2026-06-03T07:44:28Z
- **提交信息**: fix(moe): avoid unpacking None from masked deep_gemm without overlap when sbo enabled (#26839)

### [9450696](https://github.com/sgl-project/sglang/commit/9450696aa5dac5fd49a411786e164402fcdee9f5)

- **作者**: Mick
- **时间**: 2026-06-03T07:42:51Z
- **提交信息**: [diffusion] CI: add cosmos3 nano t2v gpu test (#26963)

### [ac16dbf](https://github.com/sgl-project/sglang/commit/ac16dbf4125098a4b5dc1dd0b45fa5e4f0eea0f2)

- **作者**: xutizhou
- **时间**: 2026-06-03T07:37:45Z
- **提交信息**: docs: add DeepSeek-V4 EPLB Waterfill tips (#27049)

### [8e77af1](https://github.com/sgl-project/sglang/commit/8e77af1afcee81d8c5ca627ff864bb0ac1a38a62)

- **作者**: Bingxu Chen
- **时间**: 2026-06-03T07:13:18Z
- **提交信息**: [AMD] fix(triton-mla): cap max_kv_splits at 256 on gfx942 (Kimi-K2.6 hang) (#24762)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-06-04
**监控日期**: 2026-06-03
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization for Diffusion Transformers.
- **语言**: Python
- **星标数**: 1184
- **最后更新**: 2026-06-03T07:41:26Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

好的，根据您提供的仓库README摘要和提交记录，以下是昨日更新的要点分析：

### 1. 主要更新类型
- **功能新增**：新增了对 `svdquant nvfp4` 的 PTQ（训练后量化）和 DQ（反量化）支持。
- **文档更新**：修复了 README 中的文档链接。

### 2. 关键变更点及其与项目整体方向的关系
- **`feat: support svdquant nvfp4 ptq/dq`**：这是核心变更。项目 `cache-dit` 的目标是构建一个面向 Diffusion Transformers 的、原生 PyTorch 推理引擎，核心特性包括**缓存、并行化和量化**。此提交直接增强了项目的**量化**能力，引入了 `nvfp4` 这种新的、更高效的量化格式（NVIDIA FP4）。
- **`chore: Update README.md`**：修复了文档链接，指向 `cache-dit.io`。这属于项目维护和用户体验优化，确保用户能正确访问官方文档。

### 3. 对项目的影响和潜在意义
- **提升模型推理效率**：`nvfp4` 是一种极低精度的浮点格式（4-bit）。支持其 PTQ/DQ 意味着用户可以将 Diffusion Transformer 模型量化到更小的尺寸和更低的计算精度，从而在保持可接受质量的前提下，**大幅降低显存占用和推理延迟**。这对于在资源受限的设备（如消费级GPU）上部署大型扩散模型至关重要。
- **扩展量化生态**：项目原本可能只支持 INT8 或 FP8 等常见量化格式。引入 `nvfp4` 表明项目正在积极拥抱最新的硬件特性和量化技术，**增强了其在量化领域的先进性和竞争力**。
- **提升项目可用性**：修复文档链接是一个小但重要的改进，确保了新用户能顺利找到官方文档，降低了使用门槛。

### 4. 值得关注的技术点
- **`svdquant`**：这很可能是一个结合了 SVD（奇异值分解）和量化的技术。SVD 用于模型压缩（低秩近似），再结合 `nvfp4` 量化，可以实现“压缩+量化”的双重效果，进一步压缩模型。
- **`nvfp4`**：这是 NVIDIA 在 Hopper 架构（如 H100）及后续架构上引入的 4-bit 浮点格式。支持它意味着 `cache-dit` 能够充分利用最新 GPU 的硬件加速能力，实现极致的推理性能。
- **PTQ/DQ**：支持训练后量化（PTQ）和反量化（DQ）是实用性的体现。PTQ 允许用户在不重新训练模型的情况下进行量化，非常方便；DQ 则保证了推理时数据格式的正确转换。

### 5. 基于项目背景，这些提交如何影响项目发展
- **强化核心价值主张**：`cache-dit` 的核心卖点是“原生 PyTorch + 缓存 + 并行化 + 量化”。新增 `nvfp4` 量化支持，直接强化了其**量化**这一核心竞争力，使其在“如何让 Diffusion Transformer 跑得更快、更省显存”这个问题上，提供了更极致的解决方案。
- **吸引特定用户群体**：拥有 H100 等最新 NVIDIA GPU 的用户，将能从 `nvfp4` 支持中获得最大收益。这有助于项目吸引高端硬件用户和追求极致性能的研究者/开发者。
- **保持技术前沿性**：通过快速集成 `svdquant` 和 `nvfp4` 等前沿技术，`cache-dit` 展示了其紧跟学术界和工业界最新进展的能力，有助于其在快速发展的 Diffusion 模型推理领域保持领先地位。

## 详细提交记录

### [3d49eae](https://github.com/vipshop/cache-dit/commit/3d49eae2642db8b5c4b5fdf4c7a1f4389a011848)

- **作者**: DefTruth
- **时间**: 2026-06-03T07:41:22Z
- **提交信息**: chore: Update README.md (#1030)

* Fix documentation links in README.md

Updated documentation links to point to cache-dit.io.

* Update README.md

### [86d4510](https://github.com/vipshop/cache-dit/commit/86d4510bc4ed32477c6f10f8a6abbc4a2e5dac6d)

- **作者**: DefTruth
- **时间**: 2026-06-03T07:25:39Z
- **提交信息**: feat: support svdquant nvfp4 ptq/dq (#1029)

* feat: support svdquant nvfp4 ptq/dq

* feat: support svdquant nvfp4 ptq/dq

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-06-04
**监控日期**: 2026-06-03
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 81869
- **最后更新**: 2026-06-03T23:56:10Z

## 提交统计

- **昨日提交总数**: 32
- **提交者数量**: 28
- **主要提交者**: Giancarlo Delfin, Li, Jiang, Flora Feng

## AI分析总结

好的，作为一名专业的代码分析助手，以下是对 vllm-project/vllm 仓库昨日（基于提交时间）更新要点的分析总结。

### 1. 主要更新类型

- **Bug修复 (Bug Fix)**: 修复了流式工具调用、模型预热、配置验证、LoRA别名去重等多个问题。
- **功能新增 (Feature)**: 新增了对 Gemma4 Unified (encoder-free) 模型的支持、可插拔的 KVCacheSpec、动态 LoRA 端点、Rust 前端 `/server_info` 接口等。
- **性能优化 (Perf)**: 优化了多模态数据处理（从 O(n) 到 O(log n)）、CPU→GPU 显存交换的 Triton 快速路径。
- **重构 (Refactor)**: 移除了 FlashInfer 版本检查、死代码（FP量化）、迁移自定义算子至 libtorch 稳定 ABI。
- **文档更新 (Doc)**: 更新了 ViT CUDA 图接口文档。
- **CI/测试 (CI/Test)**: 调整了 ROCm 测试平台、对齐 PD 测试、修复 LoRA 测试。
- **基础设施 (Infra)**: 更新了依赖（`actions/stale`）、处理了外部加载失败、添加了 Rust 前端扩展钩子。

### 2. 关键变更点及其与项目整体方向的关系

- **模型支持扩展**: 新增 **Gemma4 Unified (encoder-free)** 模型支持。这直接响应了 vLLM “Easy, fast, and cheap LLM serving for everyone” 的目标，通过支持最新的前沿模型，扩大了其服务生态。
- **性能与效率提升**:
    - **多模态处理优化**: 将多模态项目处理从 O(n) 优化到 O(log n)，显著提升了多模态模型（如 LLaVA）的推理效率，符合“fast”和“cheap”的承诺。
    - **显存交换优化**: 为 CPU→GPU 的 `swap_blocks_batch` 添加 Triton 快速路径，优化了 KV Cache 卸载场景下的性能，这对于长上下文或高并发场景下的成本控制至关重要。
- **架构与可扩展性增强**:
    - **可插拔 KVCacheSpec**: 允许用户自定义 KV Cache 的布局和策略，这是对 vLLM 核心缓存机制的深度抽象，使其能更灵活地适配不同模型和硬件，是迈向更通用推理引擎的关键一步。
    - **Rust 前端功能丰富**: 新增动态 LoRA 端点、`/server_info` 接口和服务器路由扩展钩子。这标志着 vLLM 正在构建一个更强大、更模块化、更易于集成的 Rust 前端，以替代或补充现有的 Python 前端，提升整体性能和可维护性。
    - **算子迁移**: 将自定义 all-reduce、DeepSeek V4 MLA 等关键算子迁移到 libtorch 稳定 ABI。这有助于减少对特定 PyTorch 版本的依赖，提升库的兼容性和稳定性。
- **Bug修复与稳定性**:
    - **流式工具调用修复**: 修复了 `tool_choice="none"` 和流式响应中工具调用参数丢失的问题，这对于依赖函数调用（Function Calling）的 Agent 应用至关重要，提升了 API 的可靠性和用户体验。
    - **模型预热修复**: 修复了推测解码（Spec Decode）中预填充阶段的预热问题，确保了该高级优化功能的正确性和稳定性。
- **硬件支持**: 为 **XPU (Intel)** 添加了块级缩放 W8A8 FP8 路径，并修复了 ViT 注意力在 XPU 上的 float32 回退问题。这体现了 vLLM 对多样化硬件生态的支持，特别是对 Intel 独立显卡（如 Arc 系列）的持续投入。

### 3. 对项目的影响和潜在意义

- **提升核心性能**: 多模态和显存交换的优化将直接降低延迟和成本，使 vLLM 在服务多模态模型和长上下文场景下更具竞争力。
- **增强灵活性与可定制性**: 可插拔 KVCacheSpec 和 Rust 前端的扩展钩子，为高级用户和开发者提供了强大的定制能力，使 vLLM 能更好地融入复杂的生产环境。
- **巩固模型生态领先地位**: 快速支持 Gemma4 等最新模型，确保了 vLLM 作为主流推理引擎的吸引力。
- **提升工程质量和稳定性**: 大量的 Bug 修复、重构和 CI 调整，表明项目在追求新功能的同时，也在持续打磨代码质量和系统稳定性，这对于生产级服务至关重要。
- **推动架构演进**: Rust 前端的持续增强和算子迁移，预示着 vLLM 正从纯 Python 架构向 Python+Rust 混合架构演进，以追求更高的性能和更好的工程实践。

### 4. 值得关注的技术点

- **`[KVCache] Support Pluggable KVCacheSpec`**: 这是一个重大的架构变更，允许用户通过插件机制定义 KV Cache 的格式（如布局、精度、分块策略）。这为未来的硬件特定优化（如 HBM 与 CXL 内存的混合使用）和模型特定优化（如 MHA、GQA、MLA 的不同缓存策略）打开了大门。
- **`[Rust Frontend] Add dynamic LoRA endpoints`**: 允许在运行时动态加载/卸载 LoRA 适配器，而无需重启服务。这对于需要频繁切换不同微调模型的应用（如个性化聊天机器人）非常实用。
- **`[Perf] Improve multimodal item

## 详细提交记录

### [bdbf08f](https://github.com/vllm-project/vllm/commit/bdbf08fc0277c63b90478fae2566aaacdaa71d9b)

- **作者**: dependabot[bot]
- **时间**: 2026-06-03T21:14:41Z
- **提交信息**: Bump actions/stale from 10.1.1 to 10.2.0 (#35078)

Signed-off-by: dependabot[bot] <support@github.com>
Co-authored-by: dependabot[bot] <49699333+dependabot[bot]@users.noreply.github.com>

### [6bad553](https://github.com/vllm-project/vllm/commit/6bad553f4e7a1d628b2c81ccc03c13f16f6cfd1a)

- **作者**: Woosuk Kwon
- **时间**: 2026-06-03T21:06:00Z
- **提交信息**: [Minor] Remove FlashInfer version check in topk_topp_sampler (#44442)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>

### [91945b6](https://github.com/vllm-project/vllm/commit/91945b6e4ade361125837228179cee01e6573023)

- **作者**: Giancarlo Delfin
- **时间**: 2026-06-03T20:32:40Z
- **提交信息**: [Bug Fix][Model Runner V2][Spec Decode] Warmup & capture with different attention states for speculator prefill (#44253)

Signed-off-by: Giancarlo Delfin <gdelfin@inferact.ai>
Co-authored-by: Woosuk Kwon <woosuk@inferact.ai>

### [2b237c7](https://github.com/vllm-project/vllm/commit/2b237c7a4100316de7843884d72af9c402e35e53)

- **作者**: hoobnn
- **时间**: 2026-06-03T20:27:45Z
- **提交信息**: [Bugfix] Honor tool_choice="none" in Chat Completions streaming (#42752)

Signed-off-by: hoobnn <111053672+hoobnn@users.noreply.github.com>
Signed-off-by: sfeng33 <4florafeng@gmail.com>
Co-authored-by: sfeng33 <4florafeng@gmail.com>

### [dad95e3](https://github.com/vllm-project/vllm/commit/dad95e34d896d75badd1d67c203021fb59374b75)

- **作者**: Wentao Ye
- **时间**: 2026-06-03T19:22:01Z
- **提交信息**: [Feature] Support batch invariant rms norm with residual (#42453)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [a248b45](https://github.com/vllm-project/vllm/commit/a248b45d0548d2db110d45799340bf525cbce0e8)

- **作者**: Luciano Martins
- **时间**: 2026-06-03T19:01:39Z
- **提交信息**: [Model] Add Gemma4 Unified (encoder-free)  support (#44429)

Signed-off-by: Luciano Martins <lucianommartins@users.noreply.github.com>
Co-authored-by: Luciano Martins <lucianommartins@users.noreply.github.com>

### [271328e](https://github.com/vllm-project/vllm/commit/271328e256bae5d5728eea32eccf44c91ad5f147)

- **作者**: linitra24
- **时间**: 2026-06-03T18:23:23Z
- **提交信息**: [LoRA] Fix dedup for post-replacement module aliases (#44413)

Signed-off-by: bk-201 <joy25810@foxmail.com>

### [2b91012](https://github.com/vllm-project/vllm/commit/2b9101265008f333ba69d58dabdd1da9ae653d7c)

- **作者**: Wentao Ye
- **时间**: 2026-06-03T18:22:23Z
- **提交信息**: [Refactor] Remove dead code fp quant (#44122)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [5b2a2be](https://github.com/vllm-project/vllm/commit/5b2a2beade03a029a9cae2dd11abe24bb41f39f7)

- **作者**: JartX
- **时间**: 2026-06-03T17:23:51Z
- **提交信息**: [ROCm][CI] Move Model Executor test step from MI250 to MI300 (gfx942) (#44370)

Signed-off-by: JartX <sagformas@epdcenter.es>

### [59d0236](https://github.com/vllm-project/vllm/commit/59d0236193a1cb5e88bee9cd4a3692a5587c9558)

- **作者**: Chris Leonard
- **时间**: 2026-06-03T16:29:46Z
- **提交信息**: [10b/n] Migrate custom all-reduce, DeepSeek V4 fused MLA, MiniMax reduce-RMS, and MXFP8 MoE to libtorch stable ABI (#44365)

Signed-off-by: Chris Leonard <chleonar@redhat.com>
Signed-off-by: Shengqi Chen <harry-chen@outlook.com>
Co-authored-by: Shengqi Chen <harry-chen@outlook.com>

### [0a5cbf6](https://github.com/vllm-project/vllm/commit/0a5cbf633e1f0e8cfbcc9888598a358ecbdecb2f)

- **作者**: pschlan-amd
- **时间**: 2026-06-03T16:09:52Z
- **提交信息**: Handle spinloop ext load failure gracefully (#43659)

Signed-off-by: Patrick Schlangen <pschlan@amd.com>
Co-authored-by: Shengqi Chen <harry-chen@outlook.com>

### [51e0c57](https://github.com/vllm-project/vllm/commit/51e0c579b0e51445662caf601930db26b3636a7f)

- **作者**: Willow Lopez
- **时间**: 2026-06-03T16:06:45Z
- **提交信息**: fix(config): validate max_num_scheduled_tokens >= 0 on all paths (#44207)

Signed-off-by: Oxygen56 <1391083091@qq.com>

### [0c6631f](https://github.com/vllm-project/vllm/commit/0c6631f02a05eec5bd3209d3cadaa2c7dcac0793)

- **作者**: Mengqing Cao
- **时间**: 2026-06-03T16:05:16Z
- **提交信息**: [KVCache] Support Pluggable KVCacheSpec (#37505)

Signed-off-by: MengqingCao <cmq0113@163.com>
Signed-off-by: Mengqing Cao <cmq0113@163.com>
Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [df7252c](https://github.com/vllm-project/vllm/commit/df7252c343a0bca1a3739d7700501e41ded85122)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-06-03T16:04:30Z
- **提交信息**: [CI] Align PD tests to HMA on by default (#44174)

Signed-off-by: NickLucche <nlucches@redhat.com>

### [4d1fd13](https://github.com/vllm-project/vllm/commit/4d1fd13613ca056c5ffd46df9fab17012e93695c)

- **作者**: Jee Jee Li
- **时间**: 2026-06-03T15:58:06Z
- **提交信息**: [CI/Build] Fix LoRA testing (#44425)

Signed-off-by: Jee Jee Li <pandaleefree@gmail.com>

### [ec8d60b](https://github.com/vllm-project/vllm/commit/ec8d60bea8658b715370543e785ed6a866d4c93f)

- **作者**: Nick Hill
- **时间**: 2026-06-03T14:59:31Z
- **提交信息**: [Model Runner V2] Use FlashInfer sampler (#42472)

### [27f1d34](https://github.com/vllm-project/vllm/commit/27f1d34a23e79fbcf8c988839fed6989ab2645dc)

- **作者**: Chauncey
- **时间**: 2026-06-03T14:52:24Z
- **提交信息**: [Frontend][Responses API] Move developer-to-system conversion into HF renderer (#43590)

Signed-off-by: chaunceyjiang <chaunceyjiang@gmail.com>
Co-authored-by: kdcyberdude <kdsingh.cyberdude@gmail.com>
Co-authored-by: Ben Browning <bbrownin@redhat.com>

### [e3e132d](https://github.com/vllm-project/vllm/commit/e3e132d2dd99af9d48f04c21e82c756211d730ae)

- **作者**: Flora Feng
- **时间**: 2026-06-03T14:42:19Z
- **提交信息**: [Refactor] Suppress SyntaxWarning from ast.literal_eval in tool parsers (#44346)

Signed-off-by: sfeng33 <4florafeng@gmail.com>

### [e523267](https://github.com/vllm-project/vllm/commit/e5232679a349fc8a8f09ca8434b9bceb7b829642)

- **作者**: Xiaochang Wu
- **时间**: 2026-06-03T12:16:19Z
- **提交信息**: [XPU] Add XPU block-scaled W8A8 fp8 path (#39968)

Signed-off-by: Wu, Xiaochang <xiaochang.wu@intel.com>
Signed-off-by: Xiaochang Wu <xiaochang.wu@intel.com>
Co-authored-by: Yuxiang <yuxiang.liang@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [309385a](https://github.com/vllm-project/vllm/commit/309385a359b1722ed0f2720540421a3fba08a9ac)

- **作者**: Xunzhuo
- **时间**: 2026-06-03T11:30:47Z
- **提交信息**: [Rust Frontend] Add /server_info to Rust frontend (#43942)

Signed-off-by: xunzhuo <xunzhuo@vllm-semantic-router.ai>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>

### [3d76f39](https://github.com/vllm-project/vllm/commit/3d76f395e3e25ec3cb9c63fb3c7662fd734222f1)

- **作者**: Varun Sundar Rabindranath
- **时间**: 2026-06-03T11:25:57Z
- **提交信息**: [SharedOffloadRegion] Align blocks to page-size   (#43689)

Signed-off-by: varun sundar rabindranath <vsundarr@redhat.com>
Co-authored-by: varun sundar rabindranath <vsundarr@redhat.com>

### [823d271](https://github.com/vllm-project/vllm/commit/823d271c0dc7dce43f6a9716be3c99aaf82ced37)

- **作者**: Li, Jiang
- **时间**: 2026-06-03T11:03:09Z
- **提交信息**: [Attention][CPU] Standardize kv layout to blocks first (#44393)

Signed-off-by: jiang1.li <jiang1.li@intel.com>

### [95b1615](https://github.com/vllm-project/vllm/commit/95b1615ec97dac31e670ed71e5cd2f3134d67ba2)

- **作者**: Andy Lo
- **时间**: 2026-06-03T11:00:26Z
- **提交信息**: [Perf] Improve multimodal item handling from O(n) to O(log n) per step (#44212)

Signed-off-by: Andy Lo <andy@mistral.ai>

### [1fa9ea0](https://github.com/vllm-project/vllm/commit/1fa9ea09f61b9b639f59f170eef159d0c7bf163f)

- **作者**: Itay Etelis
- **时间**: 2026-06-03T10:38:17Z
- **提交信息**: [Perf] Triton fast path for small CPU→GPU `swap_blocks_batch` in the offloading connector (#42212)

Signed-off-by: Itay Etelis <itay.etelis@ibm.com>
Co-authored-by: Itay Etelis <itay.etelis@ibm.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [02564b4](https://github.com/vllm-project/vllm/commit/02564b4de069a02d9f6abca57ebfd49115eaae39)

- **作者**: Yan Ma
- **时间**: 2026-06-03T10:20:21Z
- **提交信息**: [XPU]fallback to TRITON_ATTN for vit attn on xpu when use float32 dtype (#43759)

Signed-off-by: Yan Ma <yan.ma@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [209709a](https://github.com/vllm-project/vllm/commit/209709a8c131f15ed5c1ea231f4365f61a05d009)

- **作者**: Flora Feng
- **时间**: 2026-06-03T10:19:08Z
- **提交信息**: [Bugfix] Fix unstreamed tool call args dropped in Responses API streaming (#44348)

Signed-off-by: sfeng33 <4florafeng@gmail.com>

### [ace95c9](https://github.com/vllm-project/vllm/commit/ace95c9cf8307301fbcdffacc4ab44e4d5e6829a)

- **作者**: Wei Zhao
- **时间**: 2026-06-03T09:56:43Z
- **提交信息**: [Bugfix] Update TrtLLM MoE routing methods (#44347)

Signed-off-by: wzhao18 <wzhao18.sz@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [0e2b131](https://github.com/vllm-project/vllm/commit/0e2b13103b886e3b53a4b67d2a8c31d6a29e47e4)

- **作者**: Shanshan Shen
- **时间**: 2026-06-03T08:20:59Z
- **提交信息**: [Doc] Update ViT CUDA graph interfaces (#44388)

Signed-off-by: shen-shanshan <467638484@qq.com>

### [449be4f](https://github.com/vllm-project/vllm/commit/449be4f93484d2b8b9ae06bb2f86c6e42c6760d7)

- **作者**: Bugen Zhao
- **时间**: 2026-06-03T08:04:43Z
- **提交信息**: [Rust Frontend] Fix several hf chat template rendering issues (#44311)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>

### [6550ff1](https://github.com/vllm-project/vllm/commit/6550ff12f21721b1694e6299df0470b419cebb67)

- **作者**: Xunzhuo
- **时间**: 2026-06-03T07:55:29Z
- **提交信息**: [Rust Frontend] Add dynamic LoRA endpoints (#43778)

Signed-off-by: xunzhuo <xunzhuo@vllm-semantic-router.ai>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>

### [4aaed4c](https://github.com/vllm-project/vllm/commit/4aaed4ca225a3745aa1e18864dad0599d3ac7626)

- **作者**: NolanHo
- **时间**: 2026-06-03T07:45:31Z
- **提交信息**: [Rust Frontend] Add server router extension hook (#43774)

Signed-off-by: NolanHo <kujyo.eia.serias@gmail.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>

### [7268457](https://github.com/vllm-project/vllm/commit/7268457999d54f4014f2815911837c9277ca23f5)

- **作者**: Varun Sundar Rabindranath
- **时间**: 2026-06-03T07:03:00Z
- **提交信息**: [KV Offloading] Enable HMA models for Tiering Offloading (#44287)

Signed-off-by: varun sundar rabindranath <vsundarr@redhat.com>
Co-authored-by: varun sundar rabindranath <vsundarr@redhat.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-06-04
**监控日期**: 2026-06-03
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 4908
- **最后更新**: 2026-06-03T20:04:55Z

## 提交统计

- **昨日提交总数**: 10
- **提交者数量**: 8
- **主要提交者**: zzh, bastefaniak, Sy03

## AI分析总结

好的，这是对 `vllm-project/vllm-omni` 仓库昨日提交记录的分析总结。

### 1. 主要更新类型

- **功能新增**: 1项 (Cosmos3 action modality)
- **Bug修复**: 2项 (启动失败、流式输入问题)
- **性能优化**: 1项 (VoxCPM2高并发解码)
- **重构**: 1项 (HunyuanImage3 SigLIP2 ViT)
- **CI/测试**: 3项 (移除测试标记、添加CI流程、添加回归/精度测试)
- **文档/代码清理**: 1项 (更新代码注释)

### 2. 关键变更点及其与项目整体方向的关系

- **功能新增 - Cosmos3 Action Modality**: 为Cosmos3模型添加了“动作”模态支持。这直接契合项目“omni-modality”（全模态）的定位，将服务能力从文本、图像、音频扩展到更复杂的交互式动作序列，是向“全模态”目标迈出的重要一步。
- **Bug修复 - 启动失败 & 流式输入**: 修复了vLLM无法启动和流式输入处理的问题。这些是影响服务可用性和用户体验的核心问题，修复它们确保了项目基础的稳定性和可靠性。
- **性能优化 - VoxCPM2高并发解码**: 优化了VoxCPM2模型在高并发场景下的解码吞吐量。这与项目“fast”和“cheap”的目标一致，通过提升效率来降低服务成本，对实际部署至关重要。
- **重构 - HunyuanImage3 SigLIP2 ViT**: 将HunyuanImage3模型中的SigLIP2视觉Transformer层重构为vLLM的标准层。这体现了项目“easy”和“cheap”的长期目标，通过标准化和复用vLLM的优化内核，可以简化模型集成、提升性能并降低维护成本。
- **CI/测试增强**: 新增了音频实时API的CI流程，以及HunyuanImage3的像素精度测试和夜间CI。这强化了项目的质量保障体系，确保新功能（如音频实时API）和复杂模型（如HunyuanImage3）的稳定性和准确性，是项目走向成熟的关键。

### 3. 对项目的影响和潜在意义

- **提升模型生态的广度与深度**: 通过支持Cosmos3的动作模态和优化VoxCPM2，项目在“全模态”和“高性能”两个维度上同时扩展，吸引了更广泛的用户和模型开发者。
- **增强生产环境的可靠性**: 修复启动和流式问题，并增加CI/测试，显著提升了项目在生产环境中的可用性和稳定性，降低了用户的使用风险。
- **奠定长期架构基础**: 对HunyuanImage3的重构工作，是推动项目架构标准化、模块化的具体实践。这为未来高效集成更多新模型铺平了道路，是项目可持续发展的基石。
- **加速音频相关应用落地**: 针对VoxCPM2的性能优化和音频实时API的CI建设，表明项目正积极推动音频模态（特别是语音）从研究走向实际应用，如实时语音助手等。

### 4. 值得关注的技术点

- **Cosmos3 Action Modality**: 这是一个相对前沿的模态，其实现方式（如何将动作序列编码为模型可处理的token）值得关注，可能涉及新的模型架构或输入处理方式。
- **VoxCPM2高并发优化**: 具体的优化策略（如KV Cache管理、批处理策略、算子融合等）对于其他音频或序列模型的高并发部署有重要参考价值。
- **SigLIP2 ViT重构**: 将特定模型的视觉部分重构为vLLM标准层，其具体实现（如何抽象接口、如何复用vLLM的PagedAttention等机制）是理解vLLM架构扩展性的关键。
- **音频实时API的CI**: 实时API的测试通常比离线推理更复杂，涉及延迟、流式处理等。其CI设计思路（如何模拟实时场景、如何度量性能）值得学习。

### 5. 这些提交如何影响项目发展

结合README中“Easy, fast, and cheap omni-modality model serving for everyone”的愿景，这些提交共同推动了项目在以下方面的发展：

- **迈向真正的“全模态”**: 新增Cosmos3动作模态，是项目从支持文本、图像、音频等传统模态，向支持更广泛、更复杂模态（如动作、视频、触觉等）迈出的关键一步，强化了“omni”的定位。
- **兑现“fast”和“cheap”的承诺**: 对VoxCPM2的性能优化直接降低了推理成本并提高了响应速度。对HunyuanImage3的重构，通过复用vLLM的优化，长远来看也会提升其性能并降低维护成本。
- **夯实“easy”的基础**: 修复启动和流式问题，以及增加全面的CI/测试，降低了用户的使用门槛和风险，让“serving for everyone”变得更加现实。重构工作也使得未来集成新模型对开发者来说更“easy”。
- **构建健康的项目生态**: 这些提交体现了项目在功能、性能、稳定性和架构四个维度的均衡发展，表明项目正从一个原型验证阶段，稳步迈向一个成熟、可靠、可扩展的服务平台。

## 详细提交记录

### [706bad2](https://github.com/vllm-project/vllm-omni/commit/706bad253dc8d5abf1fbb83b59f3a274f2245db5)

- **作者**: bastefaniak
- **时间**: 2026-06-03T19:30:39Z
- **提交信息**: Add Cosmos3 action modality (#4102)

Signed-off-by: Maciej Bala <mbala@nvidia.com>
Signed-off-by: Bartosz Stefaniak <bstefaniak@nvidia.com>
Signed-off-by: lishunyang12 <lishunyang12@163.com>
Co-authored-by: Maciej Bala <mbala@nvidia.com>
Co-authored-by: lishunyang12 <lishunyang12@163.com>
Co-authored-by: SYLAR <125541396+lishunyang12@users.noreply.github.com>

### [8949fdc](https://github.com/vllm-project/vllm-omni/commit/8949fdc440fa3d4e71610085e54dffda478c846b)

- **作者**: amy-why-3459
- **时间**: 2026-06-03T15:44:46Z
- **提交信息**: [BugFix] Fix the issue of vllm failing to start. (#4105)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [3818ba4](https://github.com/vllm-project/vllm-omni/commit/3818ba4c65194e2322ac198421ec48e84e8b8cea)

- **作者**: Canlin Guo
- **时间**: 2026-06-03T15:12:11Z
- **提交信息**: [CI] Remove omni mark for MOSS-TTS and temporarily skipped (#4097)

Signed-off-by: gcanlin <canlinguosdu@gmail.com>

### [c33ca60](https://github.com/vllm-project/vllm-omni/commit/c33ca602088f24cc21585dc1edf697740ca4fe43)

- **作者**: Sy03
- **时间**: 2026-06-03T15:08:32Z
- **提交信息**: [Perf][VoxCPM2] Optimize VoxCPM2 high-concurrency decode throughput. (#3882)

Signed-off-by: Sy03 <1370724210@qq.com>
Co-authored-by: Yueqian Lin <70319226+linyueqian@users.noreply.github.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>
Co-authored-by: Gao Han <hgaoaf@connect.ust.hk>

### [0fc4032](https://github.com/vllm-project/vllm-omni/commit/0fc4032a712c5d8fec5cbab87ace8786f0fc42c7)

- **作者**: tanhaoan333
- **时间**: 2026-06-03T13:34:47Z
- **提交信息**: Update qwen3_tts_code2wav.py (#4075)

Signed-off-by: tanhaoan333 <tanhaoan@huawei.com>

### [2e108a4](https://github.com/vllm-project/vllm-omni/commit/2e108a4109d9ee6291db87c59668f4b2e4678dc1)

- **作者**: ChenWenjing
- **时间**: 2026-06-03T10:57:16Z
- **提交信息**: [ci] add merge/ready ci for audio realtime api (#4069)

Signed-off-by: CHEN <116010019@link.cuhk.edu.cn>

### [ce69eb3](https://github.com/vllm-project/vllm-omni/commit/ce69eb35e96f6eab689fc105cc04656b26a95748)

- **作者**: Canlin Guo
- **时间**: 2026-06-03T09:51:06Z
- **提交信息**: [Refactor] Refactor HunyuanImage3 SigLIP2 ViT to vLLM layers (#3297)

Signed-off-by: gcanlin <canlinguosdu@gmail.com>

### [07737e6](https://github.com/vllm-project/vllm-omni/commit/07737e6c6198eec5aa7b0b49a82db2a0132589d8)

- **作者**: Ricardo Noriega
- **时间**: 2026-06-03T09:17:53Z
- **提交信息**: [Test] Add prefix caching + audio output regression test (#3510) (#3604)

Signed-off-by: Ricardo Noriega De Soto <rnoriega@redhat.com>
Signed-off-by: Alex Brooks <albrooks@redhat.com>
Co-authored-by: Claude Opus 4.6 (1M context) <noreply@anthropic.com>
Co-authored-by: Alex Brooks <albrooks@redhat.com>

### [d2e65a9](https://github.com/vllm-project/vllm-omni/commit/d2e65a92f1cdc53ccb5e2ad6cf78305fe936fcd2)

- **作者**: zzh
- **时间**: 2026-06-03T08:59:21Z
- **提交信息**: [CI][Accuracy] Add HunyuanImage3 pixel accuracy test and nightly CI (#3790)

Signed-off-by: zzh <943967662@qq.com>
Co-authored-by: Alicia <115451386+congw729@users.noreply.github.com>
Co-authored-by: Gao Han <hgaoaf@connect.ust.hk>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [3842970](https://github.com/vllm-project/vllm-omni/commit/3842970a82f0a9e52cdb563e4c4fd8a3b3d780fc)

- **作者**: ChenWenjing
- **时间**: 2026-06-03T08:07:41Z
- **提交信息**: [bugfix] fix streaming input issue after rebase 0.22.0 (#4085)

Signed-off-by: CHEN <116010019@link.cuhk.edu.cn>

---
