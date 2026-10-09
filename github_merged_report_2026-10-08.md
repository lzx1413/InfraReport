# GitHub Stars 合并报告 - 2026-10-08

**合并日期**: 2026-10-09
**监控日期**: 2026-10-08
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


**报告日期**: 2026-10-09
**监控日期**: 2026-10-08
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2235
- **最后更新**: 2026-10-08T12:30:28Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Coach257

## AI分析总结

## 提交分析：[16c94aa] per-module metric meter 与 omni MFU roll-up

### 1. 主要更新类型
**功能新增**（性能监控/训练可观测性增强）。该提交同时带有 `omni` 和 `trainer` 模块标签，属于训练基础设施的功能扩展。

### 2. 关键变更点及与项目方向的关系
- **按模块的指标计量器（per-module metric meter）**：为多模态训练中各模态/组件（如视觉、音频、语言模块）提供独立的性能指标统计能力。
- **全局 MFU 聚合（omni MFU roll-up）**：MFU（Model FLOPs Utilization）是衡量大模型训练硬件利用效率的核心指标。"roll-up" 表示将各模块的 FLOPs/吞吐数据向上聚合为整体 omni 模型的综合 MFU。

与项目方向的关系：VeOmni 的核心目标是"以模型为中心的分布式配方库，扩展任意模态模型训练"。在跨多模态、多专家的分布式训练场景中，训练效率难以用单一 MFU 衡量——不同模态模块的计算特性（稠密/稀疏、计算/内存瓶颈）差异巨大。按模块计量并聚合，正是支撑"scaling any modality"这一愿景的必要工程基础。

### 3. 对项目的影响和潜在意义
- **训练效率可量化**：用户和开发者首次能在多模态混合训练中获得可靠的端到端 MFU 读数，而非仅能看到单一模块的指标，便于识别性能瓶颈（如某模态数据加载慢或某专家模块计算欠载）。
- **支撑配方调优**：VeOmni 提供分布式训练"配方"（recipe），MFU roll-up 让配方的效率评估有统一标尺，推动配方库向数据驱动优化演进。
- **对标工业级训练体系**：这种分层指标体系是 Megatron-LM、DeepSpeed 等成熟训练框架的常见能力，补齐此项增强了 VeOmni 在生产环境中的可用性与专业度。

### 4. 值得关注的技术点
- **多模态 MFU 的定义挑战**：不同模态的理论峰值 FLOPs 估算方式不同（如多模态中视觉编码器、音频编码器、LLM 主干的 FLOPs 混合），roll-up 的口径设计（加权方式、是否包含 encoder、稀疏 MoE 激活 FLOPs 如何计）是技术难点。
- **低开销计量设计**：per-module meter 需在训练热路径上近乎零开销，值得关注其是否采用异步聚合或减少 GPU-CPU 同步。
- **与 trainer 的解耦**：标签同时涉及 omni 和 trainer，暗示监控逻辑可能是模块化、可插拔的，符合 VeOmni "配方"化的设计哲学。

### 5. 对项目发展的整体影响
结合 README，VeOmni 的定位是学术论文（arXiv 2508.02317）支撑的开源训练框架，目标用户是需要训练跨模态大模型的研究者和工程师。本次提交标志着项目从"能跑通多模态分布式训练"向"能高效、可观测地训练"演进——这是开源训练框架走向成熟和被工业界采纳的关键一步。统一的 MFU 度量体系也为后续的自动化调参、弹性伸缩、硬件适配优化等高级特性奠定了数据基础。总体而言，该提交虽非模型能力上的突破，却是 VeOmni 作为"分布式配方库"这一基础设施定位的重要工程强化，体现了字节 Seed 团队在大规模多模态训练工程化上的持续深耕。

## 详细提交记录

### [16c94aa](https://github.com/ByteDance-Seed/VeOmni/commit/16c94aa32a7b8b95e3d29d82f77b85da6da04d34)

- **作者**: Coach257
- **时间**: 2026-10-08T07:54:18Z
- **提交信息**: [omni, trainer] feat: add per-module metric meter and omni MFU roll-up (#1212)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-10-09
**监控日期**: 2026-10-08
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2886
- **最后更新**: 2026-10-09T01:39:36Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 2
- **主要提交者**: Yang Yong (雍洋), Bilang ZHANG

## AI分析总结

# LightX2V 昨日提交分析（共3条）

## 1. 主要更新类型
- **功能新增**：为 Apple MPS 后端增加对 Qwen-Image-2.1 模型的支持，并引入新的 Qwen-Image-2.1-viggle-turbo-v0.3 变体。
- **重构与简化**：统一梳理推理配置文件与示例脚本（第二次迭代），并移除 SenseNova-Vision 相关支持代码。

## 2. 关键变更点及其与项目整体方向的关系
- **MPS 后端扩展**（217947d）：LightX2V 的核心定位是"轻量视频生成推理框架"，此前主要聚焦 CUDA 生态。此次将 Qwen-Image 系列模型支持扩展到 Apple Silicon 的 MPS 设备，直接呼应"Light"（轻量、低门槛）的项目理念，扩大了可运行硬件的覆盖面，让更多 Mac 用户能本地体验图像/视频生成。
- **引入 viggle-turbo 模型变体**：viggle-turbo 通常指经过蒸馏/量化的极速版模型，符合项目追求推理效率的一贯方向，丰富了"质量—速度"权衡的选项。
- **配置与脚本重构**（97853b1）：将原本可能分散的推理配置和示例脚本进一步收敛简化（且是 v2 二次迭代），说明团队重视用户体验与可维护性，降低新用户的上手成本。
- **移除 SenseNova-Vision 支持**（cabb8bb）：主动裁剪非核心模型支持，聚焦主线模型生态，避免维护负担拖累框架迭代速度。这与"减法"式的重构相辅相成。

## 3. 对项目的影响和潜在意义
- **用户群体扩大**：MPS 支持让大量 Mac 用户无需 GPU 服务器即可使用，有助于社区增长与生态渗透。
- **架构更健康**：清理冗余代码（SenseNova）与简化配置，使代码库更聚焦，后续贡献者的 PR 成本更低，框架的长期可维护性提升。
- **版本迭代信号**：配置重构标注为 v2，暗示项目正在为更稳定的对外 API/配置规范做准备，可能对应近期版本发布。
- **模型矩阵更新**：新增 Qwen-Image-2.1 及其 turbo 变体，说明项目紧跟主流开源模型发布节奏，保持时效性。

## 4. 值得关注的技术点
- **MPS 后端的兼容性处理**：MPS 在算子支持（如某些 attention kernel、attention backend、fp8/bf16 支持）上与 CUDA 差异较大，如何在不显著牺牲性能的前提下让 Qwen-Image-2.1 跑通，是值得关注的实现细节。
- **viggle-turbo 的加速手段**：是否采用一致性蒸馏、CFG 简化、步数蒸馏等技术，值得从代码中一探究竟，可作为其他模型移植的参考。
- **配置重构的模式**：v2 版配置很可能采用了更统一的 schema（如 YAML 集中管理、按模型/后端分层），对框架使用者和二次开发者都有借鉴价值。
- **移除功能时的向后兼容策略**：删除 SenseNova-Vision 时是否提供了迁移提示或版本过渡方案，体现了项目的工程成熟度。

## 5. 对项目发展的总体影响
基于 README，LightX2V 的目标是打造轻量、高效的视频生成推理框架。本次提交从三个维度强化了这一目标：**硬件广度上**通过 MPS 支持降低使用门槛，**模型深度上**通过 Qwen-Image-2.1/turbo 保持前沿模型覆盖，**工程健康度上**通过配置重构与冗余清理提升代码质量。三者共同作用，使项目朝着"更易用、更聚焦、更高效"的方向稳步演进，也为后续版本的稳定 API 与更广泛的平台支持（如更多 NPU/加速卡）打下了良好基础。

## 详细提交记录

### [217947d](https://github.com/ModelTC/LightX2V/commit/217947dca65982409e0099cfe1417edcc620a5a9)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-10-08T16:45:56Z
- **提交信息**: support qwen-image-2.1 for mps & support Qwen-Image-2.1-viggle-turbo-v0.3 (#1581)

### [97853b1](https://github.com/ModelTC/LightX2V/commit/97853b1b12e5d29ef3e2b63b781a67b23c191d4c)

- **作者**: Bilang ZHANG
- **时间**: 2026-10-08T11:52:47Z
- **提交信息**: refactor: simplify inference configs and example scripts(v2) (#1580)

### [cabb8bb](https://github.com/ModelTC/LightX2V/commit/cabb8bb684e44af5aa19be437f2e15082855cb96)

- **作者**: Bilang ZHANG
- **时间**: 2026-10-08T07:01:37Z
- **提交信息**: Remove SenseNova-Vision support and simplify related code (#1579)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-10-09
**监控日期**: 2026-10-08
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2286
- **最后更新**: 2026-10-08T08:25:42Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-10-09
**监控日期**: 2026-10-08
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6572
- **最后更新**: 2026-10-09T01:54:30Z

## 提交统计

- **昨日提交总数**: 14
- **提交者数量**: 5
- **主要提交者**: eigen, Harrison Zhang, Zixin Huang

## AI分析总结

# FlashInfer 昨日提交总结（共 14 项）

## 一、主要更新类型

- **Bug 修复**：3 项（MoE pack contract 路由、stale cubin/jit-cache 处理、NVFP4 MSA prefill 数值正确性）
- **性能优化**：4 项（Cake SSD combined 预填充、PrimTS dense FMHA、cake_sampling、cake_dsa_indexer）
- **重构**：1 项（MLA K/V 量化 kernel 由手写改为生成式）
- **CI/基础设施**：3 项（JIT 缓存构建重试、cubin 加载器日志、CUDA 13.4 镜像升级）
- **易用性与测试**：3 项（`--sm` 隐含 minimal 模式、测试门控收紧、HTTP 调试日志）

## 二、关键变更

**性能层面**：#6206 对 SM100/SM103 上 Cake Mamba2 SSD 组合预填充进行第三轮调优，段预处理降至约 4µs，新增 chunk-parallel 持久化内核使 32768 长序列场景从 688µs 降至 160µs（4 倍以上加速）；#5900 优化 PrimTS dense FMHA 的 QK-BF16/PV-FP8 内核，通过 SMEM 暂存 P 实现 QK 与 softmax 流水重叠，并采用 FP8 V 惰性缩放与 MUFU→FMA 卸载。#6143 为 cake_sampling 引入 radix pass 中的精确提前终止，位级一致下加速 2-10%。#6230 第三轮重调 cake_dsa_indexer（中位数快 4.3%）。

**正确性修复**：#6093 解决了最危险的一类 bug——`-use_fast_math` 下 FTZ 导致缩放因子精确为 0，NVFP4 MSA prefill 输出无声出错。修复方案将缩放拆为两个 `2^(d/2)` 因子，覆盖所有非下溢场景。#6264 修复 cuDNN grouped-GEMM runner 绕过共享 pack contract 检查的竞态问题。#6228 将 MiniMax-H3 JIT 测试门控从宽泛的 `major == 12` 收紧到精确 CC 12.0，消除 SM121 上的 52 个失败节点。

**架构演进**：#6163 用生成式 kernel 替换手写的 `concat_mla_kv_quant_fp8`，API 不变但消除非 12 头配置下 7-32% 的拷贝带宽损失，标志着 Cake 生成式 kernel 范式向 MLA 量化、采样、DSA indexer 全面扩展。

**体验与基建**：#5892 破解了"升级后旧版 kernel wheel 导致 import 失败、连修复命令都无法执行"的恶性循环，改为警告并优雅降级。#6095 让 `--sm` 隐含 minimal 模式。CI 方面，构建重试与 cuDNN 9.26/镜像升级解决了 Rubin 上 66 个测试失败的根因。

## 三、技术关注点

- **bitwise 一致性下的性能压榨**：多项优化以 DRAM 带宽下限或逐位一致为标尺，通过 host 代价模型选择内核变体而非改变算术，体现生产级调优纪律。
- **FTZ 与 subnormal 陷阱**：`2^-128` 在 fast-math 下精确为零，是 CUDA 数值编程的经典陷阱。
- **programmatic-dependent-launch 实测否决**：记录了两种触发变体的量化回归数据，工程参考价值高。
- **生成式系统的寄存器细粒度控制**：dsa_indexer 按 lane 分配 232 数学 / 40 I/O 寄存器。

## 四、项目影响

FlashInfer 正处于**向 Blackwell/Rubin 全系硬件（B200/B300/VR200/SM121）深耕**的关键阶段：微架构层面持续挖掘 attention 与 Mamba2 内核极限，同时以"不牺牲正确性换性能"的纪律、确定性采样契约和详尽 benchmark 证据建立工程质量标杆。生成式 kernel 范式的推进降低了长期维护成本，统一 MoE 契约、import 降级策略和 CLI 改进则标志着项目从"性能优先"向"生产级可靠性"平衡发展，有利于在 vLLM/SGLang 等推理框架生态中扩大深度集成与采用。

## 详细提交记录

### [fa7c741](https://github.com/flashinfer-ai/flashinfer/commit/fa7c741e0af4493a73352bf240c1bbc802cca288)

- **作者**: eigen
- **时间**: 2026-10-08T23:32:49Z
- **提交信息**: fix(moe): route the cuDNN grouped-GEMM runners through the shared pack contract (#6264)

## Summary


`tests/moe/test_unified_moe_pack_contract.py::test_every_pack_inputs_checks_the_contract`
fails on `main` for the four cuDNN grouped-GEMM runners
(`CudnnGroupedGemm{Bf16,Fp8PerTensor,Mxfp8,Nvfp4}Runner`): #5663 made
every unified runner call `MoERunner._validate_pack_contract` first in
`pack_inputs`, and #5453 landed two hours later with its own inline
routing-mode check instead. Because CI tests the merge commit, the four
failures show up on every open PR (for example the `PR Test` run on
`main` at 8e39ceb39 and the one on #6104).

## Change

`_CudnnGroupedGemmRunnerBase.pack_inputs` now calls the shared contract
check right after its two cuDNN-specific rejections (routing mode,
`per_token_scale`), which keep their messages and relative order, so
`tests/moe/test_unified_moe_cudnn_grouped_gemm.py` is unchanged; the
`per_token_scale` rejection moves up next to the routing-mode check. No
kernel or launch-path changes.

## Testing

Scoped `@flashinfer-bot run` on the two test files. The first revision
(668ecc85c) already passed `test_unified_moe_pack_contract.py` for all
four runners (156 passed, 5 skipped in that file); its one failure was a
cuDNN test matching the original routing-mode message, which this
revision keeps.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Input packing now applies consistent validation after checking for
pre-routed mode. Unsupported routing modes and non-null per-token
scaling settings are rejected before hidden states and routing tensors
are validated, making error reporting more predictable for grouped
matrix multiplication.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [f8935b9](https://github.com/flashinfer-ai/flashinfer/commit/f8935b9979630b829e84712ed892be893a9e52e3)

- **作者**: Jonathan Dierksen
- **时间**: 2026-10-08T21:47:18Z
- **提交信息**: ci: retry JIT cache image and dependency downloads (#5748)

## Description

Transient network failures can stop JIT-cache release jobs before
compilation: Docker Hub returned HTTP 502 while pulling a builder image,
and pip 26.2.1 raised `IncompleteRead` while installing isolated build
dependencies after a `RemoteDisconnected` retry.

- Preserve cached Docker images; retry missing-image pulls up to four
times with 5/10/20-second backoff, then run with `--pull=never`.
- Use PyPA build's isolated-environment API to retry dependency
installation up to three times with 10/20-second backoff when pip
reports an interrupted connection. Reuse the isolated environment and
pip cache between attempts. Dependency-resolution errors and
backend/compilation failures propagate immediately.
- Apply both mitigations to provider and shim wheel jobs while retaining
the provider output watchdog.

Evidence: [Docker Hub
502](https://github.com/flashinfer-ai/flashinfer/actions/runs/36672767918/job/109751200435),
[pip disconnect on this
PR](https://github.com/flashinfer-ai/flashinfer/actions/runs/36753687522/job/110018626978).

## Validation

- Three focused regression tests passed for dependency-install recovery,
retry exhaustion, and immediate failure on resolution errors.
- A real PyPA build 1.6.1 isolated-environment smoke test built a wheel
and confirmed a backend exception is not retried.
- Mocked Docker checks covered cached images, pull recovery, exhausted
retries, and build failure.
- Shell syntax checks, ShellCheck for the Docker wrapper, and commit
pre-commit hooks passed.

Live registry/disconnect recovery awaits CI. The production paths are
the provider and shim jobs calling
`build_flashinfer_jit_cache_artifact.sh` and
`build_flashinfer_jit_cache_whl.sh`.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Build setup retries downloading a required container image when it is
not available locally, with increasing waits between attempts. If all
attempts fail, the build stops with an error.
* Wheel builds retry certain temporary network failures while installing
build requirements, helping them recover from interrupted downloads.
Other errors are reported without retrying.
* **Build Improvements**
* Builds use an available local container image without attempting
another download when the image is already present.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [e4e212a](https://github.com/flashinfer-ai/flashinfer/commit/e4e212a2fc1e67d73750011b9bd64133d7871e8d)

- **作者**: Jonathan Dierksen
- **时间**: 2026-10-08T21:45:13Z
- **提交信息**: fix(jit): ignore stale cubin/jit-cache wheels at import so download-kernels can replace them (#5892)

<!-- .github/pull_request_template.md -->

## 📌 Description

After `flashinfer-python` is upgraded, the `flashinfer-cubin` and
`flashinfer-jit-cache` wheels installed for the previous version no
longer match it, and `flashinfer/jit/env.py` raised a `RuntimeError` at
import. The `flashinfer` console script (`flashinfer.__main__:cli`)
imports `flashinfer/__init__.py` before any CLI code runs. So the error
also blocked the commands that replace those wheels (`flashinfer
download-kernels`, `install-cubin-wheel`, `install-jit-cache-wheel`),
along with `show-config` and `collect-env`.

With this PR, a mismatched kernel wheel no longer fails the import.
FlashInfer ignores it, logs a warning that names the fix, and behaves as
if the wheel were not installed:

| Mismatched wheel | Fallback |
|---|---|
| `flashinfer-cubin` | `FLASHINFER_CUBIN_DIR` is
`~/.cache/flashinfer/cubins`; cubins are downloaded on demand |
| `flashinfer-jit-cache` shim | No AOT providers; modules are
JIT-compiled |

Mismatched jit-cache *provider* wheels are already handled this way
(`Ignoring incompatible flashinfer jit-cache provider ...`); this PR
extends it to the cubin wheel and the shim.
`FLASHINFER_DISABLE_VERSION_CHECK=1` keeps its meaning: use the
mismatched wheels anyway. The mismatch message now tells users to run
`flashinfer download-kernels`; before, it only said to install matching
versions.

Example (flashinfer 0.7.0.post1 with the 0.7.0 kernel wheels):

```text
$ python -c 'import flashinfer'
Ignoring incompatible flashinfer-cubin package (cubins will be downloaded on demand to /home/user/.cache/flashinfer/cubins): flashinfer-cubin version (0.7.0) does not match flashinfer version (0.7.0.post1). Run `flashinfer download-kernels` to install matching kernel wheels, or set FLASHINFER_DISABLE_VERSION_CHECK=1 to use the installed version anyway.
Ignoring incompatible flashinfer-jit-cache package (kernels will be JIT-compiled instead): flashinfer-jit-cache version (0.7.0+cu130) does not match flashinfer version (0.7.0.post1). Run `flashinfer download-kernels` to install matching kernel wheels, or set FLASHINFER_DISABLE_VERSION_CHECK=1 to use the installed version anyway.
```

**Behavior change:** `import flashinfer` no longer raises `RuntimeError`
when an installed kernel wheel's version does not match. It logs a
warning and does not use that wheel. Updated docs: the Download Kernels
section of `docs/cli.rst` and the `FLASHINFER_DISABLE_VERSION_CHECK` row
in `CLAUDE.md`.

**`collect-env` report** (second commit), which is what users paste when
they hit this:
- It compared `flashinfer-jit-cache` to `flashinfer-python` as exact
strings, so every correctly matched install (e.g. `0.7.0+cu130` with
`0.7.0`) was reported as `⚠ MISMATCH`. It now applies the rule
`jit/env.py` enforces: `flashinfer-cubin` must match exactly, and
jit-cache wheels may add a CUDA local version.
- The kernel-wheel versions are reported even when `import flashinfer`
fails. Older releases fail on exactly this mismatch, and the report used
to stop before printing them, which is why the report in #5886 shows
neither wheel.
- Installed jit-cache provider wheels are listed, and any whose version
differs from the shim, or that are installed without it, are flagged.

## 🔍 Related Issues

Fixes #5886

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

`pre-commit run --files` on the changed files passes; I did not run
`--all-files`.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.). (Only the touched test
files were run; see below.)

New tests:
-
`tests/cli/test_cli_cmds.py::test_download_kernels_cmd_with_stale_kernel_wheels_real`
runs `python -m flashinfer download-kernels --dry-run` in a fresh
interpreter, with stale `flashinfer_cubin` and `flashinfer_jit_cache`
packages first on `PYTHONPATH`. It needs a new process because the
failure happens at import. It skips when the version is `0.0.0+unknown`,
which disables the check.
- `tests/test_env.py`: a mismatched cubin package falls back to the
cache directory with a warning; a matching package is used;
`FLASHINFER_DISABLE_VERSION_CHECK=1` keeps the mismatched package.
- `tests/jit/test_jit_cache_providers.py`: a mismatched shim yields no
providers (and is not queried) and logs a warning;
`FLASHINFER_DISABLE_VERSION_CHECK=1` keeps its providers.
- `tests/utils/test_collect_env.py`: the version rule, matched and stale
wheels, provider/shim mismatch, providers without the shim, and
reporting versions when `import flashinfer` fails.

Results (x86_64 Linux, no GPU, CPU torch 2.14.1, nvcc 12.8, Python
3.10):
- `pytest tests/test_env.py tests/jit/test_jit_cache_providers.py
tests/cli/test_cli_cmds.py`: 106 passed.
- With `main`'s `env.py`, the new CLI test and the shim test fail with
the `RuntimeError` from the issue, and `tests/test_env.py` errors at
collection.
- `pytest tests/utils/test_collect_env.py`: 15 passed. With `main`'s
`collect_env.py`, the 11 new tests fail.

End-to-end with the real wheels, using this branch's source with build
version `0.7.0.post1` and the released `flashinfer-cubin==0.7.0` and
`flashinfer-jit-cache==0.7.0+cu130`:
- `main`: `python -m flashinfer download-kernels --dry-run` and `import
flashinfer` both fail with the `RuntimeError` from the issue.
- This PR: both succeed and log the warnings above. `download-kernels
--dry-run` resolves `flashinfer-cubin==0.7.0.post1` and
`flashinfer-jit-cache==0.7.0.post1+cu130`.
- Repair: `flashinfer install-cubin-wheel` and `flashinfer
install-jit-cache-wheel --cuda-version 13.0 --mode minimal --sm sm90a`
installed `flashinfer-cubin 0.7.0.post1`, `flashinfer-jit-cache
0.7.0.post1+cu130` and `flashinfer-jit-cache-sm90a 0.7.0.post1+cu130`.
The next `import flashinfer` logs nothing, uses the `flashinfer_cubin`
package directory, and finds the `sm90a` provider.

`collect-env` with the real wheels: on a matched install
(`flashinfer-python 0.7.0.post1`, `flashinfer-jit-cache
0.7.0.post1+cu130`), `main` reports `0.7.0.post1+cu130 ⚠ MISMATCH vs
flashinfer-python==0.7.0.post1`. This PR reports it clean and adds
`flashinfer-jit-cache providers : sm90a`.

The released 0.7.0.post1 package itself could not be run end-to-end on
that host: its `gdn_kernels` queries device properties at import, which
needs a GPU. `main` no longer does that.

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

- **Why not exempt only the CLI?** The console script imports
`flashinfer/__init__.py`, which reaches `jit/env.py`, before any
`__main__` code runs. A CLI-only exemption would have to guess from
`sys.argv` or `sys.orig_argv`. Making the mismatch non-fatal fixes the
CLI, `collect-env`, and downstream imports (for example vLLM after an
upgrade), and matches how mismatched provider wheels are already
handled.
- **Tradeoff:** a deployment with stale kernel wheels now runs on
downloaded cubins and JIT compilation instead of failing fast; the
import-time warning is the signal. An air-gapped host, or one without
nvcc, fails at the first kernel that needs a download or a compile, not
at import.
- **Nightly package lane:** `scripts/task_test_nightly_build.sh`
installs the cubin, jit-cache and python artifacts from one build and
runs with `FLASHINFER_DISABLE_JIT=1`. A version mismatch between them
used to fail at `show-config`. A mismatched jit-cache still fails, since
every AOT lookup misses with JIT disabled. A mismatched cubin wheel
would now quietly fall back to downloading cubins. To keep that guard,
the lane could assert after install that `jit_env.FLASHINFER_CUBIN_DIR`
points into `flashinfer_cubin`. I can add that here or in a follow-up.

AI-assisted (Claude Code).

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Mismatched kernel packages are ignored with a warning instead of
causing import failures. FlashInfer falls back to on-demand downloads
and JIT compilation until compatible packages are installed.
* Set `FLASHINFER_DISABLE_VERSION_CHECK=1` to allow use of packages with
mismatched versions.
* Environment diagnostics now report installed kernel package versions
and identify mismatches.

* **Documentation**
* Clarified that both kernel packages must match the installed
FlashInfer version and that `flashinfer download-kernels` should be
rerun after upgrading.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [bc7b96a](https://github.com/flashinfer-ai/flashinfer/commit/bc7b96ae5ac5d8a57aa0878f029929339784170c)

- **作者**: Jonathan Dierksen
- **时间**: 2026-10-08T21:44:54Z
- **提交信息**: fix(cubin_loader): log HTTP error response headers and body at DEBUG (#5980)

<!-- .github/pull_request_template.md -->

## 📌 Description

Cubin downloads from `edge.urm.nvidia.com` sometimes fail with HTTP
403s. The Artifactory edge team traced them to the Akamai security layer
in front of Artifactory, probably a rate or bot rule. To find which rule
fired, they need the `Reference #` from Akamai's error page.
`download_file()` discarded the error response, so that reference can't
be recovered after a failure.

`download_file()` now logs each HTTP error response's status, URL,
headers and body at **DEBUG** level, via a new `_log_error_response()`
helper in `flashinfer/jit/cubin_loader.py`:

```
HTTP 403 response from https://edge.urm.nvidia.com/.../kernel.cubin
headers:
  Server: AkamaiGHost
  ...
body:
<H1>Access Denied</H1>Reference&#32;&#35;18&#46;...
```

- **DEBUG only, so client logs don't change.** At the default `INFO`
level, users still see only the existing one-line `attempt N failed: 403
...` warning. The helper returns before reading the body when DEBUG is
off.
- **CI keeps it already.** The internal nightly unit-test pipeline
already runs with `FLASHINFER_LOGGING_LEVEL=DEBUG` and archives
`flashinfer_jit.log`, which this logger writes to, so CI needs no
changes.
- **Any HTTP error status, not just 403.** An Akamai rate limit can also
come back as 429 or 503 with a reference.
- **The body is logged as received.** Akamai HTML-escapes the reference,
so it shows up as `Reference&#32;&#35;18&#46;...` in the log.

This does not change the GitHub Actions cubin-wheel build
(`download_artifacts()`), which runs at INFO.

## 🔍 Related Issues

Internal edge/Akamai 403 investigation. The edge team asked for the 403
response headers and body, including the Akamai `Reference #`.

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

Hooks ran on the changed files at commit time and all passed. I did not
run `--all-files`.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

Added `test_download_file_logs_error_response_only_at_debug` to
`tests/test_artifacts.py`. It mocks a 403 with an Akamai-style body and
checks that the headers and body are logged at DEBUG and not at INFO.

I ran `tests/test_artifacts.py` locally (19 passed) on a machine without
torch or CUDA. `flashinfer/__init__.py` and the `flashinfer.jit` package
were stubbed out, and the real `cubin_loader.py` and `artifacts.py` were
under test. The DEBUG case fails when the new logging call is removed.
It has not run in the full CI environment yet.

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

- The test replaces `cubin_loader.logger` with a standard logger.
`FlashInferJITLogger` is created directly rather than through
`logging.getLogger`, so `caplog` can't capture it.
- No full-body dump at WARNING: during a long retry window (e.g. the 24h
nightly window), a persistently blocked endpoint would flood the log.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* HTTP download failures now include detailed response information in
debug logs, making issues easier to diagnose. The additional details are
hidden at standard log levels.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [7e04c08](https://github.com/flashinfer-ai/flashinfer/commit/7e04c08d61e01ce886f38f629c0624153f2a1fae)

- **作者**: Jonathan Dierksen
- **时间**: 2026-10-08T21:42:18Z
- **提交信息**: feat(cli): let install-jit-cache-wheel --sm imply minimal mode (#6095)

<!-- .github/pull_request_template.md -->

## 📌 Description

`flashinfer install-jit-cache-wheel --sm <arch>` previously failed with
"--sm can only be used with --mode minimal." unless `--mode minimal` was
also passed, even though naming target architectures only makes sense in
minimal mode.

This PR makes `--sm` imply minimal mode:

| Command | Before | After |
|---|---|---|
| `install-jit-cache-wheel` | all providers | all providers (unchanged)
|
| `install-jit-cache-wheel --sm sm90a` | error | shim + sm90a provider |
| `install-jit-cache-wheel --mode minimal --sm sm90a` | shim + sm90a
provider | unchanged |
| `install-jit-cache-wheel --mode all --sm sm90a` | error | error (`--sm
cannot be combined with --mode all.`) |

`--mode` no longer has a fixed default; it resolves to `minimal` when
`--sm` is given and `all` otherwise. The hidden `download-jit-cache`
alias picks this up automatically.

It also documents `--mode` and `--sm` in `docs/cli.rst`, which
previously did not mention them, and notes the implication in
`docs/design_docs/jit_cache_provider_wheels.md`.

## 🔍 Related Issues

- Follow-up to #4514, which introduced `--mode minimal` and `--sm`.
- Complements #5876, which adds `--sm` to `download-kernels` and already
treats it as implying minimal mode. This makes `install-jit-cache-wheel`
consistent with that. The two PRs touch different functions and doc
sections and can merge in either order.

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

Added `test_install_jit_cache_wheel_cmd_sm_implies_minimal` and
`test_install_jit_cache_wheel_cmd_rejects_sm_with_mode_all`. All 48
tests in `tests/cli/test_cli_cmds.py` pass. These were run locally on
macOS with CPU-only PyTorch and a stub `nvcc`; the CLI tests mock CUDA
detection and pip, so no GPU is involved.

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

- **Behaviour change (CLI only):** `--sm` without `--mode` used to be an
error and now selects minimal mode. The default with no flags is still
`all`, so existing scripts that don't pass `--sm` are unaffected. The
error text for `--mode all --sm` changed wording.
- The option-conflict check moved to the top of
`_install_jit_cache_wheel`, so it is reported before CUDA/version
detection rather than being masked by a detection failure.
- `_install_jit_cache_wheel`'s `mode` parameter now defaults to `None`.
Its only callers are the `install-jit-cache-wheel` command and
`_install_kernel_wheels` (which passes no mode, so it still resolves to
`all`). After #5876 lands, its explicit `mode="minimal" if
sm_architectures else "all"` can be simplified to just pass
`sm_architectures`; it remains correct either way.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Specifying one or more `--sm` targets when installing a JIT-cache
wheel now selects minimal mode automatically, installing only the
requested architecture-specific providers.
* When no `--sm` targets or mode are specified, installation continues
to include all declared providers.
* **Bug Fixes**
* Using `--sm` together with `--mode all` now reports an error before
installation begins.
* **Documentation**
* Updated CLI and installation guidance to explain target selection and
mode behavior.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [71310c9](https://github.com/flashinfer-ai/flashinfer/commit/71310c96abbb51db141d3e520753f9971a969512)

- **作者**: Jonathan Dierksen
- **时间**: 2026-10-08T21:41:51Z
- **提交信息**: ci: move the CUDA 13.4 CI image to cuDNN 9.26.0.51 (#5877)

## 📌 Description

Move the CUDA 13.4 CI runtime image from cuDNN 9.24.0.43 to the released
9.26.0.51.

cuDNN 9.24 cannot compile SM107 kernels at runtime. On Rubin, cuDNN
graphs fail to finalize with
`CUDNN_STATUS_INTERNAL_ERROR_COMPILATION_FAILED` and then
`cudnnGraphNotSupportedError: no plan in the list could be built`. That
breaks the cuDNN attention, prefill and GEMM tests on VR200: 66
additional failures across `tests/attention/test_cudnn_*`,
`test_non_contiguous_prefill`, `test_batch_prefill_kernels`, the cuDNN
cases of `test_unified_gemm_fuzz`, and `test_bmm_mxfp8` once VR200 moved
onto `flashinfer-ci-cu134:20260930-b1420f1`. The same lane passed those
tests with a cuDNN 9.26 preview.

9.26.0.51 is also the cuDNN release that torch's `nightly/cu134` wheels
pin. The image's final cuDNN install now matches torch instead of
replacing it.

- `ci/cuda-versions.json`: cu134 `cudnn_version` → `9.26.0.51`
- `.devcontainer/cu134/devcontainer.json`: matching `CUDNN_VERSION`

cu129 and cu130 stay on 9.24.0.43.

## 🔍 Related Issues

Follow-up to #5456.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

- [ ] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

`python ci/validate_cuda_versions.py` passes. `Release CI Docker` builds
both architectures on this PR, and `docker/test_ci_image.py` checks the
installed package and the loaded backend against
`FLASHINFER_CUDNN_VERSION`.

## Reviewer Notes

Merging triggers the CI image release and the follow-up `Update Docker
CI tags` PR. Once the new tag lands, the internal VR200 lane can drop
its temporary runtime override to cuDNN 9.26.0.51.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Chores**
* Updated the cuDNN version used by the CUDA 13.4 development
environment and runtime configuration.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [d217e89](https://github.com/flashinfer-ai/flashinfer/commit/d217e8915e32949b49d93bbda467ffef0e8d1329)

- **作者**: eigen
- **时间**: 2026-10-08T21:25:38Z
- **提交信息**: perf(cake_ssd_combined): preprocess, exact-scan and chunk-parallel prefill improvements (SM100 / SM103) (#6206)

# FI PR draft (round 3) — title: `perf(cake_ssd_combined): preprocess,
exact-scan and chunk-parallel prefill improvements (SM100 / SM103)`
<!-- PUBLIC TEXT: no issue-tracker ids, no tracker links, no internal
cluster/lease names, no dev-log text. grep before posting. -->

## Summary
Third performance round of the Cake Mamba2 SSD combined prefill
(`SSDCombined(backend="cake")`, `cake_ssd_combined_fwd`), SM100 (B200)
and SM103 (B300 / GB300). Exact arithmetic is preserved: every change
below is schedule-only or a new program with a host-side selection rule;
the outputs are bitwise identical to the previous release on the full
bitwise shape set on both architectures.

- **Segment preprocess**: one warp per (segment, head) tile, eight heads
per CTA, dt rows staged through shared memory for coalesced loads.
Single-chunk preprocess time drops from ~19–26 µs to ~4 µs (B200) / ~3.8
µs (B300). A programmatic-dependent-launch variant of the main kernel
was measured and dropped: the early-trigger form regressed multi-wave
rows (the 1×32768 batched row 26 → 59 µs) and the late-trigger form
gained nothing, so the two kernels stay plain back-to-back launches.
- **Exact scan**: in-place scaled-B operand (MN-major alias view) with a
double-buffered state operand, Q kept in the TMEM stage; 1–6 % faster on
multi-chunk shapes, bitwise identical.
- **Chunk-parallel program** (new generated family `chunkpar_*`): a
three-phase persistent kernel (per-chunk local states → cross-chunk scan
→ output) with a grid barrier, for long sequences with few (segment,
head) work items. Selected by a calibrated host cost model
(per-capability constants, 5 % margin, 256 MiB workspace cap, only when
`work_items < sm_count`);
`FLASHINFER_CAKE_SSD_CHUNK_PARALLEL=auto|always|never` overrides.
1×32768 tokens × 8 heads: 688 → 160 µs (B200), 667 → 153 µs (B300).
Bitwise identical to the exact scan.
- Loader: per-family host templates
(`host/mamba_ssd_combined_sequence.cpp`,
`host/mamba_ssd_combined_chunk_parallel_sequence.cpp`),
`_CHUNKPAR_MODULES`, workspace management, `last_program_name`.

## Measurements
<!-- FI-level 91-row gate (84 rows + 7 short-call rows), paired
interleaved CUPTI ×3, cold L2, Triton reference in its own process,
measured on this exact FI head with the bounded-drain benchmark harness.
Both rows are from the fixed-harness gates on this exact FI head. -->
| arch | rows ≥ 1.00 − band | min ratio (row) | 1×32768 vs stock Triton
| host overhead / call |
|---|---|---|---|---|
| SM100 B200 | 64/64 comparable rows ≥ 1.00 − band (91 rows measured: 84
+ 7 short-call rows, 0 failures) | 1.024 (perf_varlen_128x32) vs
previous release; geomean 1.620; vs CuTe min 1.314 / geomean 2.558; vs
stock Triton min 2.240 | 0.1623 ms vs 0.3930 ms (2.42×) | exposed
inter-kernel gap 0.29–0.32 µs per call (bounded-drain harness) |
| SM103 GB300 | 64/64 comparable rows ≥ 1.00 − band (91 rows measured:
84 + 7 short-call rows, 0 failures; one row at 0.997 inside the 0.005
A/A band) | 0.997 (perf_batched_256x16) vs previous release; geomean
1.504; vs CuTe min 1.475 / geomean 3.184; vs stock Triton min 2.392 |
0.1549 ms vs 0.4885 ms (3.15×) | exposed inter-kernel gap median 2.7 µs
on one-wave rows under the tracing harness, ≈ 1.5–2.3 µs with
kernel-only tracing (the Grace host's launch spacing; multi-wave rows
0.22 µs) |

## Validation
- Bitwise set (9 shapes incl. varlen, packed, dhd, f16/f32/bf16, z/no-z)
identical on SM100 and SM103, exact scan and chunk-parallel.
- `pytest tests/mamba/test_cake_ssd_combined.py` on this exact FI head:
**372 passed, 2 skipped** on GB300 (SM103); B200 (SM100): **372 passed,
2 skipped**.
- compute-sanitizer synccheck + memcheck on the exact-scan and
chunk-parallel programs: 0 errors on both archs.
- sglang adapter tests against this exact FI head: CPU route tests 47
passed (GB200, GB300), GPU route tests 42 passed (GB200, GB300); B200
pair: CPU route tests 47 passed, GPU route tests 42 passed.
- Nemotron-H-8B-Reasoning-128K BF16 TP1 end-to-end (sglang, GB200, this
exact FI head): GSM8K-200 accuracy 0.890 with the Cake SSD route vs
0.890 stock, 117/200 identical answers, 6/6 symmetric flips, no NaN/Inf,
all short-prompt and prefix-hit probes finite and greedy-identical
between the cached and cold paths.

## Launch contract
The chunk-parallel family (`chunkpar_*`) is a persistent kernel whose
CTAs meet at a software grid barrier. Its resources (512 threads,
`__launch_bounds__(512, 1)`, 231,936 B of dynamic shared memory, a full
512-column TMEM allocation) fit exactly one CTA per SM, and the host
launches `min(num_segments * nheads, sm_count)` CTAs, so on an otherwise
idle device every CTA is resident. The launch is an ordinary
(non-cooperative) launch: if other work holds SMs when the grid starts,
the resident CTAs wait at the barrier until those CTAs retire; a true
hang needs two grid-barrier kernels sharing the device and waiting on
each other. `FLASHINFER_CAKE_SSD_CHUNK_PARALLEL=never` disables the
family. The Cake host emitter carries the cooperative launch attribute
in its extended-launch form, but the prepared-sequence host used by this
family does not emit it yet; enabling it is an exporter change plus
regeneration and re-measurement, tracked as a follow-up (see the review
thread on the launch site).

## CI
Docs-only follow-up commit `6173dac0d` adds
`FLASHINFER_CAKE_SSD_CHUNK_PARALLEL` to the CLAUDE.md environment
variable reference (static documentation check); no code or
generated-file changes.
`@flashinfer-bot run tests/mamba/test_cake_ssd_combined.py`
`/bot run`

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added support for chunk-parallel processing alongside exact-scan
processing for BF16, FP16, and FP32 states in batched and
variable-length modes.
* Added automatic kernel selection based on workload and device
characteristics, with an option to force or disable chunk-parallel
processing.
* Added visibility into which kernel family was selected for the most
recent call.

* **Tests**
* Expanded coverage for kernel selection, supported modes and state
types, launch configuration, and matching results between kernel
families.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->


<!-- cake-shared-references:start -->
## References

The shared reference corpus for CAKE kernel development includes the
following projects, documentation, and existing CAKE work:

- **GPU programming and instructions:** [NVIDIA CUDA Programming
Guide](https://docs.nvidia.com/cuda/cuda-programming-guide/index.html),
[NVIDIA PTX
ISA](https://docs.nvidia.com/cuda/parallel-thread-execution/), and
gau-nernst's [tcgen05 tutorial](https://gau-nernst.github.io/tcgen05/)
and [CUDA kernel examples](https://github.com/gau-nernst/learn-cuda).
- **Kernel programming libraries and compilers:** [NVIDIA CUTLASS /
CuTe](https://github.com/NVIDIA/cutlass),
[Triton](https://github.com/triton-lang/triton),
[TileLang](https://github.com/tile-ai/tilelang), [NVIDIA cuTile
Python](https://github.com/NVIDIA/cutile-python), and
[ThunderKittens](https://github.com/HazyResearch/ThunderKittens)
([ThunderKittens 2.0
techniques](https://hazyresearch.stanford.edu/blog/2026-02-19-tk-2)).
- **Attention and inference:** [FlashAttention (including Hopper and
CuTe implementations)](https://github.com/Dao-AILab/flash-attention),
[FlashInfer, including its TRT-LLM kernel
integration](https://github.com/flashinfer-ai/flashinfer), [Flash Linear
Attention](https://github.com/fla-org/flash-linear-attention),
[SageAttention](https://github.com/thu-ml/SageAttention),
[FlashAttention-FP4](https://github.com/hao-ai-lab/flash-attention-fp4),
and [FastVideo](https://github.com/hao-ai-lab/FastVideo).
- **GEMM and MoE:** [DeepGEMM](https://github.com/deepseek-ai/DeepGEMM),
[SonicMoE](https://github.com/Dao-AILab/sonic-moe),
[Alpha-MoE](https://github.com/Aleph-Alpha/Alpha-MoE), and [Mixture of
Kittens](https://github.com/cursor/mixture-of-kittens).
- **Clustering and nearest-neighbor kernels:** [Flash
K-Means](https://github.com/svg-project/flash-kmeans) and
[FlashLib](https://github.com/FlashML-org/flashlib).
- **Existing CAKE implementations and PRs:** [CAKE-generated kernel
progress tracker and PR index
(#4254)](https://github.com/flashinfer-ai/flashinfer/issues/4254).

These are corpus-level references. PR-specific implementation details,
changes, and benchmark references are documented above.
<!-- cake-shared-references:end -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [0caca03](https://github.com/flashinfer-ai/flashinfer/commit/0caca03ce677d210d663c41431cb20e5ef8035c7)

- **作者**: eigen
- **时间**: 2026-10-08T19:50:06Z
- **提交信息**: fix(tests): count caching-allocator requests in the Cake DSv4 hardening no-allocation checks (#6244)

### [461037f](https://github.com/flashinfer-ai/flashinfer/commit/461037fbf52227e6343ccbc9fc977337c1bf672b)

- **作者**: Harrison Zhang
- **时间**: 2026-10-08T18:05:22Z
- **提交信息**: perf(prims-ts): qk-bf16/pv-fp8 and all-fp8 dense fmha context perf bringup (#5900)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

Kernel optimizations and performance bring-up of the PrimTS dense
context FMHA for **QK-BF16/PV-FP8** at D=128, stacked on
[PR-5475](https://github.com/flashinfer-ai/flashinfer/pull/5475) (the
QKV-BF16 bring-up). Every change is gated on 8-bit V, so all-FP8 (FP8
Q/K/V) inputs get the same kernel changes, plus two-CTA UMMA with FP8
Q/K.

Most of the changes reorder or skip work. The two error-affecting ones
(lazy correction, exp2 offload) match the cuDNN and FlashAttention 4
settings and stay within cuDNN error against the fp32 reference.

**Cumulative changes are described here as well as in the tables
below.**

- **(P-in-SMEM) P staged in SMEM instead of the TMEM S stage
(QK-BF16/PV-FP8)**. Softmax used to write P back into the TMEM stage
that held S, so QK(N+1) waited for PV(N) to read P and PV(N) waited for
the whole softmax(N). Softmax now writes P into an SMEM tile per query
group and releases the S stage as soon as S is in registers, so QK(N+1)
runs during exp2(N). The MMA warp issues QK0, PV0, QK1, PV1 per
iteration. The SMEM for the P tiles comes from staging the O epilogue in
two halves. Under two-CTA UMMA the P tile is published through the
cluster-scope P-ready barrier.
MUFU:  [softmax N]        [softmax N+1]
MMA:   [QK N+1] [PV N]    [QK N+2] [PV N+1]

- **(lazy-correction) Lazy correction for FP8 V**. As for BF16, the
running row max is frozen unless it grows by more than 2^8, so the O
rescale is skipped on almost every tile. The FP8 P pre-scale is derived
from that threshold so P never saturates e4m3.

- **(exp2-offload) exp2 offload to the FMA pipe**. 3 of 16 exp2 pairs
per softmax chunk are evaluated as an FMA polynomial. B200 only, where
MUFU bounds the softmax. Off on B300.

- **(fp8-pack) Cheaper P pack and row sum**. Each e4m3x4 word is packed
with two cvt and one mov.b32 instead of a PRMT per word. The tile row
sum accumulates over four packed FADD2 chains instead of two.

- **(early-token) Early S0/S1 token**. On B300 a softmax group hands the
pacing token to its peer before its P work, so the peer starts its row
max while this group computes P.

- **(two-CTA) Two-CTA UMMA for FP8 Q/K**. The existing 2-CTA form
accepts E4M3 Q/K. The per-CTA K/V half staging and the cta_group::2
descriptors do not depend on the Q/K dtype, so only the eligibility and
kernel guard change.

- **(scheduler) SMEM-P softmax work declared auxiliary**. exp2 and the P
store run after the S stage is released, so they are declared auxiliary
work for the task scheduler. Fixes the schedule build for persistent and
paged FP8 D128.

Already in PR-5475 and shared with this PR:

- Budget-sized K/V ring: sized from the SMEM left after every other
buffer instead of a fixed 3 stages.
- Partial-last-tile handling (regspill), pv-overlap, the two-CTA UMMA
form, and lazy correction and exp2 offload for bf16; this PR extends the
last three to 8-bit V.

The experiment e2e workload is Wan2.2-T2V-A14B self-attention sweeping
75.6k to 147.6k output tokens.

**Ablated results for B200 e2e speedup on Wan2.2-T2V-A14B.**
The QK-BF16/PV-FP8 results (orange) apply to this PR. The all-FP8 point
(dark orange) uses the same kernel path on B200.
<img width="2240" height="1184" alt="image"
src="https://github.com/user-attachments/assets/d92eddae-edfe-414d-99c2-aad4bc2a649c"
/>

**Ablated results for B300 e2e speedup on Wan2.2-T2V-A14B.**
The QK-BF16/PV-FP8 results (orange) apply to this PR.
<img width="2240" height="1184" alt="image"
src="https://github.com/user-attachments/assets/5ee97bcb-50a9-47a4-8598-a86e3b573341"
/>


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

The two-CTA test covers BF16, QK-BF16/PV-FP8 and all-FP8 inputs at 2:2,
4:2 and 3:1 Q/KV head ratios, each against the single-CTA kernel and the
SDPA reference. The 77 relevant context tests pass on B200 (fp8,
two-CTA, fixed-dense, schedule builds).

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

Stacked on
[PR-5475](https://github.com/flashinfer-ai/flashinfer/pull/5475)
(QKV-BF16 bring-up). Please review that one first. Only the six prims_ts
commits above the merge of main are new here.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Performance**
* Improved attention processing for supported dense, fixed-shape
workloads through device-specific tuning and multi-CTA execution.
* Optimized probability staging and softmax handling for eligible
attention configurations. Device-specific tuning also applies to
supported paged-attention workloads.
* Improved processing for eligible FP8 attention configurations with
updated probability scaling and staging.
* **Tests**
* Added coverage comparing multi-CTA attention results with reference
and single-CTA results across supported data types and head
configurations.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Harrison Zhang <harrisonz@nvidia.com>

### [26f2418](https://github.com/flashinfer-ai/flashinfer/commit/26f2418978a997450b5ba502316d3cd63af03a25)

- **作者**: Zixin Huang
- **时间**: 2026-10-08T16:43:53Z
- **提交信息**: fix(msa): keep earlier blocks when the NVFP4 prefill replay rebases deeply (#6093)

## 📌 Description

**Impact**
- **Correctness:** fixes silently wrong NVFP4 MSA prefill attention
output. When the replay rebases deeply, every block accumulated before
the rebase was dropped. On B200, softmax weights of **0.516 / 0.516 came
out as 0.000 / 1.031**, and on random data one row put 99.6% of its
weight on a single key (reference 0.61 / 0.39). No error is raised.
- **Cost:** the fast path is unchanged. The replay path adds one
multiply per rescaled value.

**Details**

The NVFP4 MSA prefill replay (`sparse_prefill_tile<true>` in
`csrc/msa_prefill_nvfp4_specialized.cu`) raises the softmax origin when
the running sum leaves the guard band. It then rescales `row_sum` and
the O accumulator by `exp2f(exp_origin - new_origin)`.

That exponent can be below -126. For example, the origin starts at 32
and the first rebase moves it to `block_max + 16 ~ 160`, giving 2^-128.
A factor that small is subnormal, and the unit is built with
`-use_fast_math` (FTZ), so the factor becomes **exactly 0**. The
rescaled values themselves are perfectly normal (`row_sum <= 2^112`
times `2^-128`), but every block accumulated before the rebase
disappears from the output.

**Repro on B200**: one query with two selected blocks holding one large
key each, key A in block 0 and key B in block 1 (`V_A = e0`, `V_B =
e1`), so output columns 0/1 are the softmax weights. With `q0 = 187`
(A's log2-logit ~143.1):
- the reference weights are 0.516 / 0.516;
- `main` returns **0.000 / 1.031**.

Below and above that window the kernel is exact. The same happens on
random data with a large `softmax_scale`: one row whose reference
weights are 0.61 / 0.39 gets ~99.6% of the weight on one key.

**Fix:** apply the rescale as two equal factors `2^(d/2)`.
- Each factor is normal for `d >= -252`.
- The rescaled value is only representable for `d >= -238`.
- So this covers every case where the result is not itself an underflow.
- The fast path is untouched, and the replay path gains one multiply per
rescaled value. FTZ stays on, as the JIT comment intends.

## 🔍 Related Issues

None filed.

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

New test: `test_a_replay_rebase_keeps_the_blocks_accumulated_before_it`.
It is the two-key construction above, swept over q0 in [180, 192] and
three values of the second key's offset.
- On B200 it fails on `main` at q0 = 187 and 188 and passes with this
PR.
- With this PR, `test_msa_nvfp4_prefill_sm100.py` and
`test_blackwell_msa_routes.py` pass (95 passed).

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved numerical stability during replay when rescaling small
values, preventing earlier-block contributions from being lost and
keeping outputs closer to expected results.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [8e39ceb](https://github.com/flashinfer-ai/flashinfer/commit/8e39ceb390302b0d1eeb5ccca6787f4b688efc9a)

- **作者**: eigen
- **时间**: 2026-10-08T11:24:31Z
- **提交信息**: feat(cake_concat_mla_kv_quant_fp8): generated Cake kernels for the fused MLA K/V pack + fp8 cast (#6163)

## Summary

Replaces the hand-written `concat_mla_kv_quant_fp8` CUDA kernel from
#5667 with generated Cake kernels behind the same public
API (`flashinfer.concat_mla_kv_quant_fp8(kv_nope, k_pe, key=None,
value=None, *, nope_dim=128) -> (key, value)`), dispatched by
compute capability (SM100 / SM103) and by the head-group plan the host
computes from `(num_tokens, num_heads)`. This PR is stacked
on #5667 and includes its commits; the API, the in-place semantics and
the byte-exact saturating e4m3 cast (RNE, clamp to
+-448, NaN -> 0x7F; verified on all 65536 bf16 input patterns) are
unchanged, and the composable torch fallback outside the
dispatch surface is #5667's with the NaN-sign fix of `a0475feae` (see
the credit note below).

Why: the generic head-count path of #5667 processes one head pair per
warp (1 KB in flight), which leaves 7-32 % against the raw
streaming-copy floor for `H != 12`; the generated kernels keep 4 KB in
flight per warp for every head count (one token per warp
group, immediate per-item offsets, the RoPE row loaded once per warp) at
328 SASS instructions. At `H = 12` the two kernels are
structurally equivalent (6 KB in flight per warp, 96 KB per SM) and sit
on the same copy floor at 93 % of DRAM peak (dirty-L2
write-back of the benchmark's cold-L2 flush excluded).

**Relationship to #5667 and credit (2026-10-08):** This PR keeps
everything from #5667 except its kernel and the JIT/AOT glue that built
it. The public API module and signature, the composable torch fallback,
the in-place semantics and the saturating-cast contract, the
`flashinfer.__init__` export, the `docs/api/concat_ops.rst` entry and
the workloads JSON (both updated for the new dispatch surface), the
trace template (unchanged) and the test module (extended here, every
original test kept) are Brandon Zhang's work from #5667 and remain in
this branch's history as his commits (`8c6077e81`, `f1eff7c94`,
`c624e2f0e`, `f4a3d3040`). What this PR removes is the hand-written CUDA
kernel (`csrc/mla_kv_pack_fp8.cu`,
`include/flashinfer/mla_kv_pack_fp8.cuh`), its JIT loader
(`flashinfer/jit/mla_kv_pack.py`) and its AOT entry (replaced by the
per-head-group Cake AOT modules). `concat_mla_kv_quant_fp8` now
dispatches to the generated Cake kernels on exact compute capability
10.0 / 10.3 (SM100 / SM103) for calls inside the dispatch surface and to
the torch fallback for every other call; the fallback is #5667's, except
that `a0475feae` routes its casts through a saturating helper that also
drops the NaN sign bit (so `-NaN` encodes as `0x7F` on torch < 2.13,
matching the kernel). The branch carries #5667's commits as of its
then-head `f4a3d3040`; #5667 has since been rebased (head `8ae82a66e`)
and gained two commits — `7dce8de79` (one saturating cast shared by the
fallback and the trace reference, plus the same AOT-entry move out of
`add_moe`) and `8ae82a66e` (the trace-template inventory registration) —
which overlap this PR's `a0475feae` and `0ab3b468b`. The plan is to
rebase this branch before merge so that only this PR's own changes
remain (onto `main` once #5667 lands, or onto #5667's head at that time
if it is still open), which drops the overlapping commits. Thanks to
@brandonfzhang for the API, the fallback and the test scaffolding this
PR builds on.

**Base note (2026-10-07):** upstream `main` moved under the stacked base
and conflicted on one `pyproject.toml` package-data line (#5667's
`mla_kv_pack_fp8_workloads.json` entry next to main's `cake_dsa_indexer`
entry). This branch therefore carries a merge of `main` with the
keep-both resolution (`770d719dd`); the diff against `main` is still
exactly #5667 plus this PR's commit. The merged tree was re-run on a
B200 before the push (`tests/utils/test_concat_mla_kv_quant_fp8.py` 59
passed / 1 skipped,
`tests/trace/test_concat_mla_kv_quant_fp8_reference_correctness.py` 2
passed).

**Update (2026-10-07, head `9b82bebf4`):** the fused route now serves a
**row-strided `k_pe`** directly (unit last stride, row stride a multiple
of 16 elements and >= 64), so a caller can hand over the last 64 columns
of a `[T, 576]` MLA latent without a `.contiguous()` copy; the generated
programs take the row stride as a launch immediate and the binding
checks exactly that layout. Every tensor base must be 32-byte aligned
(one 256-bit load per lane piece); the fused-route check enforces it and
falls back with reason `alignment`. New byte-exact tests:
`test_strided_k_pe_byte_exact` (3 shapes x 4 layouts incl. the `[T, 1,
64]` view) and `test_inadmissible_k_pe_layout_takes_fallback`;
compute-sanitizer (synccheck + memcheck) clean on the strided layouts on
SM100 and SM103; the contiguous path is unchanged (paired A/B against
the previous programs: geomean 1.000 on both, bytes identical).

**Update (2026-10-07, head `a0475feae`):** review follow-ups. The
composable torch fallback now encodes NaN exactly like the fused kernel
on every torch build (it kept the NaN sign bit, which torch < 2.13's
software fp8 cast turns into `0xFF` for `-NaN`; the kernel and the API
doc say `0x7F`), pinned by
`test_fallback_encodes_nan_and_overflow_like_the_kernel` (kill switch;
+-NaN / +-inf / overflow / -0.0 patterns in every column group); the
public docstring now states the 32-byte base-alignment rule and the
row-strided `k_pe` layout; the AOT inventory entry moved out of the
`add_moe` block to the unconditional Cake exact-target attention
packages. Generated kernels unchanged; both architectures re-exported
(receipts below).

## Files

- `csrc/cake_concat_mla_kv_quant_fp8/*_kernel.cu`, `*_binding.cu` —
generated kernels (one per head group 1-4, architecture-neutral text
compiled with the device's SM100a / SM103a flags) and their tvm-ffi
bindings.
- `flashinfer/jit/cake_concat_mla_kv_quant_fp8.py` — loader: one build
per (target, head group), route table (replaces
`flashinfer/jit/mla_kv_pack.py`, the loader of the hand-written kernel).
- `flashinfer/mla_kv_pack.py` — public API (unchanged signature) + the
head-group plan replica; it calls
`flashinfer/cake_concat_mla_kv_quant_fp8.py::launch` (the Cake-owned
launch path: binding arguments from the route's `arg_plan`, launch on
the torch stream).
- `flashinfer/aot.py`, `docs/api/concat_ops.rst`,
`flashinfer/mla_kv_pack_fp8_workloads.json`,
`tests/utils/test_concat_mla_kv_quant_fp8.py`.
- Removed: `csrc/mla_kv_pack_fp8.cu`,
`include/flashinfer/mla_kv_pack_fp8.cuh`,
`flashinfer/jit/mla_kv_pack.py`.

## Measurements

Kernel-level comparison against the #5667 kernel and the vLLM
`fused_kimi_k3_mla_kv_concat_quant_fp8` kernel (same-session interleaved
CUPTI cold-L2 graph replays, 5 rounds x 30 iterations, median of round
medians; B200 1965 MHz, B300 2032 MHz; "floor" = a raw streaming copy of
exactly the operator's bytes with no conversion):

| rows | arch | vs FI #5667 (harness) | vs vLLM fused (harness) | floor
/ cake | second session vs the #5667 kernel |
|---|---|---|---|---|---|
| H = 12 (18) | B200 | 0.970-1.000 (geomean 0.9883, 0/18 > 1) |
1.092-1.183 (18/18 > 1) | 0.956-1.086 | 0.958-1.012 (geomean 0.9958,
7/18 > 1) |
| H = 12 (18) | B300 | 0.968-1.002 (geomean 0.9889, 2/18 > 1) |
1.087-1.182 (18/18 > 1) | 0.969-1.076 | 0.963-1.013 (geomean 0.9950,
5/18 > 1) |
| H != 12 (12) | B200 | 1.047-1.389 (geomean 1.1727, 12/12 > 1) |
1.075-1.244 (12/12 > 1) | 0.947-1.117 | 1.045-1.438 (geomean 1.1813,
12/12 > 1) |
| H != 12 (12) | B300 | 1.026-1.360 (geomean 1.1501, 12/12 > 1) |
1.061-1.263 (12/12 > 1) | 0.959-1.087 | 1.026-1.405 (geomean 1.1531,
12/12 > 1) |

<details><summary>Per-row kernel comparison (T, H; cake/#5667,
cake/vLLM, floor/cake, second-session cake/#5667; B200 then
B300)</summary>

| T | H | B200 cake/FI | B200 cake/vLLM | B200 floor/cake | B200 gate |
B300 cake/FI | B300 cake/vLLM | B300 floor/cake | B300 gate |
|---|---|---|---|---|---|---|---|---|---|
| 66048 | 12 | 0.996 | 1.094 | 1.083 | 0.988 | 0.998 | 1.087 | 1.053 |
0.990 |
| 66038 | 12 | 0.996 | 1.104 | 1.083 | 0.990 | 0.996 | 1.093 | 1.073 |
0.992 |
| 62592 | 12 | 0.985 | 1.092 | 1.073 | 0.994 | 0.992 | 1.088 | 1.057 |
0.998 |
| 62262 | 12 | 0.993 | 1.099 | 1.086 | 0.996 | 0.995 | 1.095 | 1.058 |
0.997 |
| 56320 | 12 | 0.988 | 1.092 | 1.073 | 0.989 | 0.992 | 1.087 | 1.076 |
0.988 |
| 50688 | 12 | 0.987 | 1.104 | 1.077 | 0.995 | 0.991 | 1.097 | 1.046 |
0.996 |
| 34742 | 12 | 1.000 | 1.129 | 1.082 | 1.001 | 1.002 | 1.120 | 1.048 |
0.999 |
| 33792 | 12 | 1.000 | 1.130 | 1.058 | 1.006 | 1.000 | 1.122 | 1.060 |
1.007 |
| 33206 | 12 | 0.999 | 1.135 | 1.066 | 1.012 | 1.001 | 1.129 | 1.046 |
1.013 |
| 31168 | 12 | 0.983 | 1.113 | 1.061 | 1.008 | 0.982 | 1.106 | 1.060 |
1.008 |
| 30898 | 12 | 0.987 | 1.117 | 1.064 | 1.011 | 0.989 | 1.113 | 1.057 |
1.009 |
| 23936 | 12 | 0.975 | 1.123 | 1.008 | 0.988 | 0.968 | 1.111 | 1.000 |
0.986 |
| 21312 | 12 | 0.990 | 1.137 | 1.030 | 0.998 | 0.980 | 1.123 | 1.020 |
0.999 |
| 18432 | 12 | 0.983 | 1.153 | 1.033 | 0.987 | 0.986 | 1.152 | 1.031 |
0.990 |
| 16896 | 12 | 0.979 | 1.154 | 1.009 | 1.011 | 0.979 | 1.151 | 1.007 |
1.011 |
| 9344 | 12 | 0.984 | 1.171 | 0.979 | 0.958 | 0.997 | 1.171 | 0.975 |
0.963 |
| 5504 | 12 | 0.970 | 1.183 | 0.990 | 0.986 | 0.984 | 1.182 | 0.994 |
0.983 |
| 1536 | 12 | 0.994 | 1.144 | 0.956 | 1.006 | 0.969 | 1.137 | 0.969 |
0.982 |
| 1536 | 6 | 1.248 | 1.244 | 1.064 | 1.190 | 1.254 | 1.263 | 1.070 |
1.168 |
| 16384 | 6 | 1.141 | 1.165 | 0.967 | 1.196 | 1.136 | 1.156 | 0.965 |
1.187 |
| 65536 | 6 | 1.167 | 1.141 | 1.058 | 1.170 | 1.160 | 1.131 | 1.052 |
1.156 |
| 1536 | 24 | 1.281 | 1.159 | 0.947 | 1.289 | 1.276 | 1.178 | 0.974 |
1.276 |
| 16384 | 24 | 1.068 | 1.109 | 1.059 | 1.075 | 1.058 | 1.104 | 1.033 |
1.063 |
| 65536 | 24 | 1.047 | 1.083 | 1.094 | 1.045 | 1.026 | 1.072 | 1.087 |
1.026 |
| 1536 | 48 | 1.329 | 1.150 | 0.959 | 1.389 | 1.326 | 1.149 | 0.959 |
1.363 |
| 16384 | 48 | 1.096 | 1.086 | 1.069 | 1.100 | 1.069 | 1.085 | 1.068 |
1.069 |
| 65536 | 48 | 1.080 | 1.075 | 1.110 | 1.077 | 1.043 | 1.061 | 1.082 |
1.042 |
| 1536 | 96 | 1.389 | 1.145 | 0.980 | 1.438 | 1.360 | 1.136 | 0.977 |
1.405 |
| 16384 | 96 | 1.141 | 1.082 | 1.095 | 1.139 | 1.085 | 1.077 | 1.084 |
1.085 |
| 65536 | 96 | 1.140 | 1.183 | 1.117 | 1.136 | 1.071 | 1.174 | 1.084 |
1.072 |

</details>

For `H = 12` the #5667 kernel and the generated kernel sit on the same
streaming floor (the spread is the measurement-noise band of two
byte-identical programs); the generated kernels serve every other head
count from the same floor, 1.03-1.4x the #5667 generic path and
1.06-1.26x the vLLM kernel.

<details><summary>Export receipts (68 rows per architecture, source
program vs generated FlashInfer build: same-session interleaved CUPTI
cold-L2 medians of CUDA-graph replays; sm_100a 68/68 rows pass,
source/export geomean 0.9768; sm_103a 68/68 rows pass, geomean
0.9838)</summary>

<!-- sm_100a: producer 93430d835823 target f4a3d3040086 passed 68/68 all
n=68 geomean 0.9768, correctness n=38 geomean 0.9598, perf n=30 geomean
0.9988 -->
<!-- sm_103a: producer 93430d835823 target f4a3d3040086 passed 68/68 all
n=68 geomean 0.9838, correctness n=38 geomean 0.9720, perf n=30 geomean
0.9990 -->
| row | route | sm_100a source us | sm_100a export us | sm_100a src/exp
| sm_100a verdict | sm_103a source us | sm_103a export us | sm_103a
src/exp | sm_103a verdict |
|---|---|---:|---:|---:|---|---:|---:|---:|---|
| perf_t66048_h12 | concat_mla_kv_quant_fp8_hg3_t66048_h12 | 99.7 | 99.8
| 0.9994 | PASS | 99.8 | 99.9 | 0.9994 | PASS |
| perf_t66038_h12 | concat_mla_kv_quant_fp8_hg3_t66038_h12 | 99.8 | 99.8
| 1.0000 | PASS | 99.8 | 99.9 | 0.9997 | PASS |
| perf_t62592_h12 | concat_mla_kv_quant_fp8_hg3_t62592_h12 | 94.3 | 94.4
| 0.9987 | PASS | 94.9 | 94.9 | 1.0000 | PASS |
| perf_t62262_h12 | concat_mla_kv_quant_fp8_hg3_t62262_h12 | 93.9 | 94.0
| 0.9993 | PASS | 94.4 | 94.5 | 0.9997 | PASS |
| perf_t56320_h12 | concat_mla_kv_quant_fp8_hg3_t56320_h12 | 85.5 | 85.6
| 0.9996 | PASS | 85.9 | 85.9 | 1.0002 | PASS |
| perf_t50688_h12 | concat_mla_kv_quant_fp8_hg3_t50688_h12 | 77.4 | 77.4
| 1.0000 | PASS | 77.8 | 77.8 | 1.0000 | PASS |
| perf_t34742_h12 | concat_mla_kv_quant_fp8_hg3_t34742_h12 | 54.5 | 54.6
| 0.9988 | PASS | 54.8 | 54.8 | 1.0000 | PASS |
| perf_t33792_h12 | concat_mla_kv_quant_fp8_hg3_t33792_h12 | 52.9 | 53.0
| 0.9982 | PASS | 53.3 | 53.4 | 0.9982 | PASS |
| perf_t33206_h12 | concat_mla_kv_quant_fp8_hg3_t33206_h12 | 51.9 | 52.0
| 0.9988 | PASS | 52.3 | 52.3 | 0.9994 | PASS |
| perf_t31168_h12 | concat_mla_kv_quant_fp8_hg3_t31168_h12 | 49.2 | 49.3
| 0.9994 | PASS | 49.5 | 49.5 | 0.9994 | PASS |
| perf_t30898_h12 | concat_mla_kv_quant_fp8_hg3_t30898_h12 | 48.7 | 48.7
| 0.9993 | PASS | 49.0 | 49.0 | 1.0003 | PASS |
| perf_t23936_h12 | concat_mla_kv_quant_fp8_hg3_t23936_h12 | 38.2 | 38.2
| 1.0008 | PASS | 38.3 | 38.4 | 0.9992 | PASS |
| perf_t21312_h12 | concat_mla_kv_quant_fp8_hg3_t21312_h12 | 34.6 | 34.6
| 0.9991 | PASS | 34.9 | 34.9 | 0.9991 | PASS |
| perf_t18432_h12 | concat_mla_kv_quant_fp8_hg3_t18432_h12 | 30.7 | 30.7
| 0.9990 | PASS | 30.9 | 30.8 | 1.0010 | PASS |
| perf_t16896_h12 | concat_mla_kv_quant_fp8_hg3_t16896_h12 | 28.3 | 28.4
| 0.9977 | PASS | 28.5 | 28.5 | 0.9978 | PASS |
| perf_t9344_h12 | concat_mla_kv_quant_fp8_hg3_t9344_h12 | 17.3 | 17.3 |
0.9999 | PASS | 17.4 | 17.4 | 1.0000 | PASS |
| perf_t5504_h12 | concat_mla_kv_quant_fp8_hg3_t5504_h12 | 11.5 | 11.5 |
0.9972 | PASS | 11.6 | 11.6 | 1.0000 | PASS |
| perf_t1536_h12 | concat_mla_kv_quant_fp8_hg2_t1536_h12 | 5.3 | 5.3 |
0.9942 | PASS | 5.3 | 5.3 | 0.9940 | PASS |
| perf_t1536_h6 | concat_mla_kv_quant_fp8_hg3_t1536_h6 | 3.7 | 3.8 |
0.9829 | PASS | 3.7 | 3.8 | 0.9748 | PASS |
| perf_t16384_h6 | concat_mla_kv_quant_fp8_hg3_t16384_h6 | 15.6 | 15.6 |
0.9979 | PASS | 15.6 | 15.6 | 0.9980 | PASS |
| perf_t65536_h6 | concat_mla_kv_quant_fp8_hg3_t65536_h6 | 52.0 | 52.0 |
1.0000 | PASS | 52.4 | 52.5 | 0.9994 | PASS |
| perf_t1536_h24 | concat_mla_kv_quant_fp8_hg2_t1536_h24 | 7.6 | 7.6 |
1.0127 | PASS | 7.6 | 7.5 | 1.0171 | PASS |
| perf_t16384_h24 | concat_mla_kv_quant_fp8_hg4_t16384_h24 | 50.9 | 50.9
| 1.0000 | PASS | 51.2 | 51.2 | 1.0006 | PASS |
| perf_t65536_h24 | concat_mla_kv_quant_fp8_hg4_t65536_h24 | 191.1 |
191.1 | 1.0000 | PASS | 192.1 | 192.1 | 0.9998 | PASS |
| perf_t1536_h48 | concat_mla_kv_quant_fp8_hg2_t1536_h48 | 12.2 | 12.3 |
0.9922 | PASS | 12.2 | 12.3 | 0.9949 | PASS |
| perf_t16384_h48 | concat_mla_kv_quant_fp8_hg4_t16384_h48 | 98.1 | 98.1
| 0.9993 | PASS | 98.1 | 98.2 | 0.9990 | PASS |
| perf_t65536_h48 | concat_mla_kv_quant_fp8_hg4_t65536_h48 | 377.5 |
377.5 | 1.0002 | PASS | 378.3 | 378.3 | 1.0001 | PASS |
| perf_t1536_h96 | concat_mla_kv_quant_fp8_hg2_t1536_h96 | 21.2 | 21.2 |
1.0000 | PASS | 21.3 | 21.3 | 1.0000 | PASS |
| perf_t16384_h96 | concat_mla_kv_quant_fp8_hg4_t16384_h96 | 190.9 |
190.9 | 1.0000 | PASS | 191.5 | 191.6 | 0.9997 | PASS |
| perf_t65536_h96 | concat_mla_kv_quant_fp8_hg4_t65536_h96 | 748.1 |
748.0 | 1.0001 | PASS | 750.2 | 750.2 | 1.0000 | PASS |
| corr_t1_h1 | concat_mla_kv_quant_fp8_hg1_t1_h1 | 1.5 | 1.7 | 0.8868 |
PASS | 1.5 | 1.6 | 0.9020 | PASS |
| corr_t1_h6 | concat_mla_kv_quant_fp8_hg3_t1_h6 | 1.6 | 1.8 | 0.9091 |
PASS | 1.6 | 1.7 | 0.9074 | PASS |
| corr_t1_h12 | concat_mla_kv_quant_fp8_hg2_t1_h12 | 1.9 | 2.1 | 0.9091
| PASS | 1.8 | 2.0 | 0.9199 | PASS |
| corr_t1_h128 | concat_mla_kv_quant_fp8_hg2_t1_h128 | 2.0 | 2.2 |
0.9143 | PASS | 2.0 | 2.2 | 0.9275 | PASS |
| corr_t3_h1 | concat_mla_kv_quant_fp8_hg1_t3_h1 | 1.5 | 1.7 | 0.8868 |
PASS | 1.5 | 1.6 | 0.9210 | PASS |
| corr_t3_h6 | concat_mla_kv_quant_fp8_hg3_t3_h6 | 1.9 | 2.0 | 0.9206 |
PASS | 1.8 | 2.0 | 0.9194 | PASS |
| corr_t3_h12 | concat_mla_kv_quant_fp8_hg2_t3_h12 | 2.0 | 2.2 | 0.9138
| PASS | 2.0 | 2.1 | 0.9692 | PASS |
| corr_t3_h128 | concat_mla_kv_quant_fp8_hg2_t3_h128 | 2.2 | 2.3 |
0.9589 | PASS | 2.2 | 2.3 | 0.9449 | PASS |
| corr_t17_h1 | concat_mla_kv_quant_fp8_hg1_t17_h1 | 1.8 | 2.0 | 0.9048
| PASS | 1.9 | 2.0 | 0.9508 | PASS |
| corr_t17_h6 | concat_mla_kv_quant_fp8_hg3_t17_h6 | 2.0 | 2.2 | 0.9147
| PASS | 2.0 | 2.2 | 0.9412 | PASS |
| corr_t17_h12 | concat_mla_kv_quant_fp8_hg2_t17_h12 | 2.1 | 2.3 |
0.9028 | PASS | 2.0 | 2.2 | 0.9280 | PASS |
| corr_t17_h128 | concat_mla_kv_quant_fp8_hg2_t17_h128 | 2.6 | 2.6 |
1.0121 | PASS | 2.5 | 2.6 | 0.9753 | PASS |
| corr_t127_h1 | concat_mla_kv_quant_fp8_hg1_t127_h1 | 2.0 | 2.2 |
0.9118 | PASS | 2.0 | 2.1 | 0.9552 | PASS |
| corr_t127_h6 | concat_mla_kv_quant_fp8_hg3_t127_h6 | 2.3 | 2.4 |
0.9467 | PASS | 2.3 | 2.3 | 0.9726 | PASS |
| corr_t127_h12 | concat_mla_kv_quant_fp8_hg2_t127_h12 | 2.4 | 2.5 |
0.9740 | PASS | 2.4 | 2.4 | 0.9996 | PASS |
| corr_t127_h128 | concat_mla_kv_quant_fp8_hg2_t127_h128 | 5.0 | 5.0 |
0.9873 | PASS | 4.9 | 5.0 | 0.9808 | PASS |
| corr_t129_h1 | concat_mla_kv_quant_fp8_hg1_t129_h1 | 2.0 | 2.2 |
0.9118 | PASS | 2.0 | 2.1 | 0.9697 | PASS |
| corr_t129_h6 | concat_mla_kv_quant_fp8_hg3_t129_h6 | 2.3 | 2.4 |
0.9471 | PASS | 2.2 | 2.3 | 0.9722 | PASS |
| corr_t129_h12 | concat_mla_kv_quant_fp8_hg2_t129_h12 | 2.4 | 2.5 |
0.9744 | PASS | 2.4 | 2.5 | 0.9866 | PASS |
| corr_t129_h128 | concat_mla_kv_quant_fp8_hg2_t129_h128 | 5.0 | 5.1 |
0.9873 | PASS | 5.0 | 5.1 | 0.9812 | PASS |
| corr_t1536_h1 | concat_mla_kv_quant_fp8_hg1_t1536_h1 | 2.5 | 2.5 |
0.9872 | PASS | 2.5 | 2.5 | 1.0000 | PASS |
| corr_t1536_h6 | concat_mla_kv_quant_fp8_hg3_t1536_h6 | 3.8 | 3.8 |
0.9919 | PASS | 3.7 | 3.8 | 0.9833 | PASS |
| corr_t1536_h12 | concat_mla_kv_quant_fp8_hg2_t1536_h12 | 5.1 | 5.2 |
0.9876 | PASS | 5.1 | 5.1 | 0.9937 | PASS |
| corr_t1536_h128 | concat_mla_kv_quant_fp8_hg2_t1536_h128 | 27.3 | 27.4
| 0.9988 | PASS | 27.5 | 27.6 | 0.9971 | PASS |
| corr_t65536_h1 | concat_mla_kv_quant_fp8_hg1_t65536_h1 | 16.3 | 16.4 |
0.9961 | PASS | 15.9 | 16.0 | 0.9979 | PASS |
| corr_t65536_h6 | concat_mla_kv_quant_fp8_hg3_t65536_h6 | 51.9 | 52.0 |
0.9994 | PASS | 52.4 | 52.4 | 1.0000 | PASS |
| corr_t65536_h12 | concat_mla_kv_quant_fp8_hg3_t65536_h12 | 99.0 | 99.1
| 0.9990 | PASS | 99.2 | 99.2 | 1.0000 | PASS |
| corr_t65536_h128 | concat_mla_kv_quant_fp8_hg4_t65536_h128 | 995.8 |
995.7 | 1.0000 | PASS | 998.3 | 998.3 | 1.0000 | PASS |
| corr_t131072_h1 | concat_mla_kv_quant_fp8_hg1_t131072_h1 | 30.4 | 30.4
| 0.9989 | PASS | 29.7 | 29.7 | 0.9978 | PASS |
| corr_t131072_h6 | concat_mla_kv_quant_fp8_hg3_t131072_h6 | 100.2 |
100.2 | 0.9994 | PASS | 100.5 | 100.5 | 1.0000 | PASS |
| corr_t131072_h12 | concat_mla_kv_quant_fp8_hg3_t131072_h12 | 193.5 |
193.5 | 1.0000 | PASS | 193.8 | 193.8 | 1.0002 | PASS |
| corr_t131072_h128 | concat_mla_kv_quant_fp8_hg4_t131072_h128 | 1984.4
| 1984.3 | 1.0000 | PASS | 1989.5 | 1989.4 | 1.0000 | PASS |
| patterns_t1024_h1 | concat_mla_kv_quant_fp8_hg1_t1024_h1 | 2.3 | 2.3 |
0.9991 | PASS | 2.4 | 2.4 | 1.0000 | PASS |
| strided_t1536_h12_s576o512 | concat_mla_kv_quant_fp8_hg2_t1536_h12 |
5.2 | 5.2 | 0.9939 | PASS | 5.2 | 5.2 | 0.9996 | PASS |
| strided_t129_h13_s576o512 | concat_mla_kv_quant_fp8_hg4_t129_h13 | 2.5
| 2.6 | 0.9750 | PASS | 2.5 | 2.5 | 0.9996 | PASS |
| strided_t66048_h12_s576o512 | concat_mla_kv_quant_fp8_hg3_t66048_h12 |
99.0 | 99.1 | 0.9997 | PASS | 99.7 | 99.7 | 0.9997 | PASS |
| strided_t3_h1_s128o64 | concat_mla_kv_quant_fp8_hg1_t3_h1 | 1.5 | 1.7
| 0.9057 | PASS | 1.6 | 1.6 | 0.9602 | PASS |
| strided_t4096_h128_s80o16 | concat_mla_kv_quant_fp8_hg4_t4096_h128 |
66.7 | 66.8 | 0.9990 | PASS | 66.9 | 66.9 | 1.0000 | PASS |

</details>

## Test plan

- `pytest tests/utils/test_concat_mla_kv_quant_fp8.py` on SM100 and
SM103 (byte-exact vs the torch reference on the PR's matrix, in-place,
graph capture).
- `/bot run` and `@flashinfer-bot run`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added `concat_mla_kv_quant_fp8` to combine MLA key/value inputs and
convert them to FP8 E4M3 outputs. Outputs can be allocated automatically
or provided by the caller.
* Supported workloads can use an optimized path on select NVIDIA GPUs;
other workloads use a PyTorch fallback with saturating FP8 conversion.
Set `FLASHINFER_SPECIALIZED_KERNEL_DISABLE=1` to force the fallback.
* **Documentation**
* Added API documentation describing supported inputs, outputs, and
dispatch behavior.
* **Tests**
* Added coverage for reference correctness, supported workloads, output
buffers, and fallback behavior.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->


<!-- cake-shared-references:start -->
## References

The shared reference corpus for CAKE kernel development includes the
following projects, documentation, and existing CAKE work:

- **GPU programming and instructions:** [NVIDIA CUDA Programming
Guide](https://docs.nvidia.com/cuda/cuda-programming-guide/index.html),
[NVIDIA PTX
ISA](https://docs.nvidia.com/cuda/parallel-thread-execution/), and
gau-nernst's [tcgen05 tutorial](https://gau-nernst.github.io/tcgen05/)
and [CUDA kernel examples](https://github.com/gau-nernst/learn-cuda).
- **Kernel programming libraries and compilers:** [NVIDIA CUTLASS /
CuTe](https://github.com/NVIDIA/cutlass),
[Triton](https://github.com/triton-lang/triton),
[TileLang](https://github.com/tile-ai/tilelang), [NVIDIA cuTile
Python](https://github.com/NVIDIA/cutile-python), and
[ThunderKittens](https://github.com/HazyResearch/ThunderKittens)
([ThunderKittens 2.0
techniques](https://hazyresearch.stanford.edu/blog/2026-02-19-tk-2)).
- **Attention and inference:** [FlashAttention (including Hopper and
CuTe implementations)](https://github.com/Dao-AILab/flash-attention),
[FlashInfer, including its TRT-LLM kernel
integration](https://github.com/flashinfer-ai/flashinfer), [Flash Linear
Attention](https://github.com/fla-org/flash-linear-attention),
[SageAttention](https://github.com/thu-ml/SageAttention),
[FlashAttention-FP4](https://github.com/hao-ai-lab/flash-attention-fp4),
and [FastVideo](https://github.com/hao-ai-lab/FastVideo).
- **GEMM and MoE:** [DeepGEMM](https://github.com/deepseek-ai/DeepGEMM),
[SonicMoE](https://github.com/Dao-AILab/sonic-moe),
[Alpha-MoE](https://github.com/Aleph-Alpha/Alpha-MoE), and [Mixture of
Kittens](https://github.com/cursor/mixture-of-kittens).
- **Clustering and nearest-neighbor kernels:** [Flash
K-Means](https://github.com/svg-project/flash-kmeans) and
[FlashLib](https://github.com/FlashML-org/flashlib).
- **Existing CAKE implementations and PRs:** [CAKE-generated kernel
progress tracker and PR index
(#4254)](https://github.com/flashinfer-ai/flashinfer/issues/4254).

These are corpus-level references. PR-specific implementation details,
changes, and benchmark references are documented above.
<!-- cake-shared-references:end -->

---------

Signed-off-by: Brandon Zhang <31413216+brandonfzhang@users.noreply.github.com>
Co-authored-by: Brandon Zhang <31413216+brandonfzhang@users.noreply.github.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [42310f9](https://github.com/flashinfer-ai/flashinfer/commit/42310f9ac225f31501616a570aaf214be50c82ce)

- **作者**: Cindy Zhang
- **时间**: 2026-10-08T09:58:37Z
- **提交信息**: fix(tests): gate SM120-only MiniMax kernels on exact CC (#6228)

<!-- .github/pull_request_template.md -->

## 📌 Description

The MiniMax-H3 FC1 SwiGLU, MLP, and pre-attention JIT modules compile
only `sm_120a` cubins, but their tests used a broad `major == 12`
architecture gate. This caused the tests to run on DGX Spark (SM121) and
fail with:
```
  - `cudaErrorNoKernelImageForDevice`
  - `failed to opt in to dynamic shared memory: no kernel image is available for execution on
  the device`
```
Restrict these tests to compute capability 12.0, matching the existing
MiniMax-H3 quantized output-projection test.

  Affected tests:

- `test_minimax_h3_sm120_quant_fc1_swiglu.py` — 14 failing nodes on
Spark
  - `test_minimax_h3_sm120_quant_mlp.py` — 20 failing nodes on Spark
- `test_minimax_h3_sm120_quant_pre_attention.py` — 18 failing nodes on
Spark


## 🔍 Related Issues

Fixes #5723

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
This is a test-gating-only change; it does not modify the kernels or
public APIs.
The three affected JIT modules statically target sm_120a, so SM121 is
not binary-compatible with their generated kernel images. The two
MiniMax-H3 varlen-attention suites remain enabled on SM121 because they
dynamically generate native sm_121a code.



<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Tests**
* GPU-specific validation now runs only on compute capability 12.0
(GB202) devices. SM121 devices and other GPUs with compute capability 12
are skipped because they cannot run the embedded test binaries. This
narrows the supported hardware for these tests without changing the
behavior or availability of the product itself.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [9aa52b9](https://github.com/flashinfer-ai/flashinfer/commit/9aa52b935e55fcfb61fd9390e04bb32e7f3b9860)

- **作者**: eigen
- **时间**: 2026-10-08T08:49:00Z
- **提交信息**: perf(cake_sampling): round 11 -- exact early termination of the leader radix passes, per-capability dispatch, hard floors (SM90, SM100a, SM103a, SM107a) (#6143)

## cake_sampling round 11 -- exact early termination, per-capability
dispatch, hard floors

Follow-up of #5439, #5553, #5664, #5771, #5873, #5950, #6065, #6105
(rounds 3-10). Round 11 keeps the correctness contract
unchanged (exact top-k set and tie rule, eps-exact top-p cut,
deterministic sampling per (input, seed, offset), fp32 keys,
no reduced-precision paths, no approximate algorithms) and ships one
exact kernel lever plus four host-policy levers:

- **E1 exact early termination of the leader radix passes** (every
multi-CTA streaming build, bit-identical): the leader
stops its 11-bit passes as soon as the selected bucket's count equals
the remaining rank, so the exact result is reached
with fewer passes on the served distributions; `full_passes_tcomp` keeps
the pass count exact where the counts tie.
Perturbed-process A/Bs with the round-10 kernels as the base: GB300
0.947-0.977 (`_sp_lp_l1`), 0.957-0.974 (`_sp_lb`),
B200 0.935-0.989 on every served class-C / class-A build, H100
0.942-0.998 (`_cs_lp_l1`, `_cs_lp`), R200 0.903-0.972.
- **M4 one-chunk rows take the CTA-local select up to k 64**
(`LOCAL_SELECT_ONE_CHUNK_MAX_K_BY_CAPABILITY`, 10.0 and 10.3):
  k50 V128256 0.970-0.984 on GB300 and B200.
- **M4 R200 takes the CTA-local select up to k 20**
(`_LOCAL_SELECT_MAX_K_BY_CAPABILITY[(10, 7)] = 20`): k10 0.903-0.936,
k20 0.930-0.975 on every served leader-push cell; the list overflow
starts at k 24 (V262144) / k 28.
- **M4 H100 one-wave cluster-1 re-pick for long rows from batch 64**
(`_one_wave_c1_repick` on the 132-SM table): removes the
round-10 regression row (V262144 B2 k10 eager); the V262144 B64 cells
read 0.935-0.948 of round 10 (the rule alone is 1.4-1.9 %,
0.981-0.986 against the former cluster-2 pick with both arms on the
round-11 kernels).
- **M4-lb B200 two-chunk speculative rows at batch <= 2 take the leader
push** (`_LEADER_PUSH_TWO_CHUNK_SMALL_BATCH_BY_CAPABILITY`):
k50 V151936 B1 0.976, B2 0.995 against the slab-tail form once both
carry E1.

Bundle: 126 kernels, source digest `4834e729...`; 38 kernels
byte-identical to round 10 (`.text`), 88 re-rendered by E1 (every
build with a leader radix pass). `cake_sampling` tests 262 passed / 18
skipped on B200, GB300 and H100 at this head, and on R200 at the
previous host revision (the host changes since then are the 10.0-only
one-chunk cap and the batch <= 2 leader-push rule, the (10,7) cap 20 and
a test-only fix; the R200 run on this head is queued); RTX PRO 6000
(12.0, dlcluster, pytorch:26.07 container): 254 passed / 26 skipped;
compute-sanitizer synccheck + memcheck 0 errors on the whole kernel set
(B200, R200); sglang GSM8K parity on B200.

### Speedup vs `top_k_first` (192-cell matrix per device: k 10 / 50 /
1000 x eager / graph x 8 batches x 4 vocabularies; min / median / max
over the 32 cells of each row)

| device | k | mode | speedup | cells |
|---|---|---|---|---|
| gb300 | 10 | eager | 4.86x / 11.43x / 18.12x | 32 |
| gb300 | 10 | graph | 3.84x / 6.04x / 8.23x | 32 |
| gb300 | 50 | eager | 4.78x / 10.95x / 16.35x | 32 |
| gb300 | 50 | graph | 3.95x / 5.88x / 8.04x | 32 |
| gb300 | 1000 | eager | 3.55x / 5.35x / 7.86x | 32 |
| gb300 | 1000 | graph | 2.99x / 4.87x / 7.88x | 32 |
| b200 | 10 | eager | 3.12x / 6.93x / 11.07x | 32 |
| b200 | 10 | graph | 3.66x / 6.19x / 9.38x | 32 |
| b200 | 50 | eager | 3.14x / 6.96x / 10.29x | 32 |
| b200 | 50 | graph | 3.73x / 6.09x / 8.51x | 32 |
| b200 | 1000 | eager | 2.99x / 4.62x / 7.93x | 32 |
| b200 | 1000 | graph | 2.97x / 5.04x / 8.91x | 32 |
| h100 | 10 | eager | 2.51x / 6.57x / 12.06x | 32 |
| h100 | 10 | graph | 2.75x / 5.38x / 8.79x | 32 |
| h100 | 50 | eager | 2.50x / 6.10x / 11.43x | 32 |
| h100 | 50 | graph | 2.76x / 5.30x / 8.26x | 32 |
| h100 | 1000 | eager | 2.51x / 4.41x / 6.61x | 32 |
| h100 | 1000 | graph | 2.83x / 4.62x / 7.48x | 32 |
| r200 | 10 | eager | 3.16x / 5.24x / 7.28x | 32 |
| r200 | 10 | graph | 3.51x / 5.52x / 7.31x | 32 |
| r200 | 50 | eager | 3.28x / 5.22x / 7.25x | 32 |
| r200 | 50 | graph | 3.40x / 5.57x / 7.31x | 32 |
| r200 | 1000 | eager | 2.37x / 4.51x / 7.69x | 32 |
| r200 | 1000 | graph | 2.64x / 4.44x / 10.51x | 32 |

Every one of the 192 cells is faster than `top_k_first` on every device.
Regressions vs round 10 by the perturbed-process
protocol: GB300 0, B200 0, H100 0, R200 0; the round-10 regression row
(H100 V262144 batch 2 k 10 eager) now
reads 0.926 of round 10.

### Per-shape tables (matrix medians, us)

<details><summary>gb300 k=10 eager: 32 cells, speedup 4.86x / 11.43x /
18.12x</summary>

| V | B | route | top_k_first us | cake us | speedup |
|---|---|---|---|---|---|
| 32768 | 1 | pipeline | 64.0 | 9.40 | 6.80x |
| 32768 | 2 | pipeline | 61.7 | 9.30 | 6.60x |
| 32768 | 4 | pipeline | 65.6 | 9.35 | 7.02x |
| 32768 | 8 | pipeline | 69.2 | 9.40 | 7.39x |
| 32768 | 16 | pipeline | 69.1 | 9.50 | 7.24x |
| 32768 | 32 | pipeline | 72.4 | 9.90 | 7.33x |
| 32768 | 64 | pipeline | 72.9 | 10.50 | 6.97x |
| 32768 | 128 | pipeline | 74.4 | 11.40 | 6.53x |
| 128256 | 1 | pipeline | 165.2 | 9.20 | 17.99x |
| 128256 | 2 | pipeline | 168.7 | 9.30 | 18.12x |
| 128256 | 4 | pipeline | 171.2 | 9.50 | 17.95x |
| 128256 | 8 | pipeline | 169.4 | 9.80 | 17.30x |
| 128256 | 16 | pipeline | 172.2 | 12.70 | 13.56x |
| 128256 | 32 | pipeline | 171.9 | 13.30 | 12.88x |
| 128256 | 64 | pipeline | 171.5 | 16.50 | 10.41x |
| 128256 | 128 | pipeline | 174.8 | 21.50 | 8.13x |
| 151936 | 1 | pipeline | 168.1 | 12.00 | 13.97x |
| 151936 | 2 | pipeline | 167.2 | 12.20 | 13.68x |
| 151936 | 4 | pipeline | 166.7 | 11.50 | 14.51x |
| 151936 | 8 | pipeline | 174.1 | 11.80 | 14.70x |
| 151936 | 16 | pipeline | 171.5 | 13.90 | 12.32x |
| 151936 | 32 | pipeline | 171.9 | 15.20 | 11.31x |
| 151936 | 64 | pipeline | 172.5 | 18.60 | 9.28x |
| 151936 | 128 | pipeline | 175.5 | 25.00 | 7.01x |
| 262144 | 1 | pipeline | 173.1 | 11.10 | 15.55x |
| 262144 | 2 | pipeline | 173.1 | 11.30 | 15.32x |
| 262144 | 4 | pipeline | 177.6 | 11.60 | 15.33x |
| 262144 | 8 | pipeline | 172.2 | 12.15 | 14.16x |
| 262144 | 16 | pipeline | 172.5 | 14.90 | 11.54x |
| 262144 | 32 | pipeline | 172.4 | 17.30 | 9.96x |
| 262144 | 64 | pipeline | 180.0 | 24.70 | 7.29x |
| 262144 | 128 | pipeline | 174.2 | 35.80 | 4.86x |

</details>

<details><summary>gb300 k=10 graph: 32 cells, speedup 3.84x / 6.04x /
8.23x</summary>

| V | B | route | top_k_first us | cake us | speedup |
|---|---|---|---|---|---|
| 32768 | 1 | pipeline | 41.0 | 9.40 | 4.37x |
| 32768 | 2 | pipeline | 43.7 | 9.30 | 4.69x |
| 32768 | 4 | pipeline | 44.2 | 9.30 | 4.73x |
| 32768 | 8 | pipeline | 45.0 | 9.40 | 4.80x |
| 32768 | 16 | pipeline | 45.6 | 9.60 | 4.75x |
| 32768 | 32 | pipeline | 50.9 | 10.00 | 5.08x |
| 32768 | 64 | pipeline | 52.5 | 10.70 | 4.90x |
| 32768 | 128 | pipeline | 54.1 | 11.60 | 4.65x |
| 128256 | 1 | pipeline | 74.8 | 9.40 | 7.98x |
| 128256 | 2 | pipeline | 79.0 | 9.60 | 8.23x |
| 128256 | 4 | pipeline | 78.9 | 9.80 | 8.06x |
| 128256 | 8 | pipeline | 81.5 | 10.05 | 8.09x |
| 128256 | 16 | pipeline | 82.8 | 12.90 | 6.44x |
| 128256 | 32 | pipeline | 84.4 | 13.60 | 6.21x |
| 128256 | 64 | pipeline | 88.2 | 16.70 | 5.27x |
| 128256 | 128 | pipeline | 90.3 | 21.70 | 4.16x |
| 151936 | 1 | pipeline | 78.8 | 12.20 | 6.44x |
| 151936 | 2 | pipeline | 83.7 | 12.40 | 6.78x |
| 151936 | 4 | pipeline | 81.8 | 11.70 | 6.96x |
| 151936 | 8 | pipeline | 85.8 | 12.15 | 7.04x |
| 151936 | 16 | pipeline | 88.2 | 14.20 | 6.21x |
| 151936 | 32 | pipeline | 89.4 | 15.40 | 5.80x |
| 151936 | 64 | pipeline | 91.2 | 18.80 | 4.86x |
| 151936 | 128 | pipeline | 98.5 | 25.20 | 3.91x |
| 262144 | 1 | pipeline | 82.6 | 11.30 | 7.33x |
| 262144 | 2 | pipeline | 84.5 | 11.50 | 7.38x |
| 262144 | 4 | pipeline | 83.7 | 11.90 | 7.05x |
| 262144 | 8 | pipeline | 88.3 | 12.40 | 7.13x |
| 262144 | 16 | pipeline | 89.4 | 15.20 | 5.88x |
| 262144 | 32 | pipeline | 130.7 | 17.60 | 7.41x |
| 262144 | 64 | pipeline | 118.5 | 25.00 | 4.75x |
| 262144 | 128 | pipeline | 139.7 | 36.40 | 3.84x |

</details>

<details><summary>gb300 k=50 eager: 32 cells, speedup 4.78x / 10.95x /
16.35x</summary>

| V | B | route | top_k_first us | cake us | speedup |
|---|---|---|---|---|---|
| 32768 | 1 | pipeline | 64.5 | 9.80 | 6.59x |
| 32768 | 2 | pipeline | 64.8 | 9.70 | 6.68x |
| 32768 | 4 | pipeline | 68.8 | 9.70 | 7.07x |
| 32768 | 8 | pipeline | 69.8 | 9.75 | 7.17x |
| 32768 | 16 | pipeline | 71.7 | 9.80 | 7.30x |
| 32768 | 32 | pipeline | 73.4 | 10.10 | 7.26x |
| 32768 | 64 | pipeline | 74.0 | 10.80 | 6.86x |
| 32768 | 128 | pipeline | 75.0 | 11.70 | 6.39x |
| 128256 | 1 | pipeline | 163.2 | 10.00 | 16.35x |
| 128256 | 2 | pipeline | 163.5 | 10.10 | 16.22x |
| 128256 | 4 | pipeline | 161.9 | 10.30 | 15.66x |
| 128256 | 8 | pipeline | 161.2 | 10.70 | 15.12x |
| 128256 | 16 | pipeline | 159.7 | 12.90 | 12.36x |
| 128256 | 32 | pipeline | 167.0 | 14.10 | 11.81x |
| 128256 | 64 | pipeline | 164.7 | 16.65 | 9.88x |
| 128256 | 128 | pipeline | 167.6 | 22.10 | 7.59x |
| 151936 | 1 | pipeline | 164.0 | 11.80 | 13.89x |
| 151936 | 2 | pipeline | 168.9 | 12.10 | 14.00x |
| 151936 | 4 | pipeline | 160.3 | 12.30 | 13.08x |
| 151936 | 8 | pipeline | 166.4 | 12.60 | 13.16x |
| 151936 | 16 | pipeline | 168.6 | 14.20 | 11.84x |
| 151936 | 32 | pipeline | 167.8 | 15.45 | 10.86x |
| 151936 | 64 | pipeline | 168.5 | 18.80 | 8.96x |
| 151936 | 128 | pipeline | 172.1 | 25.40 | 6.78x |
| 262144 | 1 | pipeline | 162.5 | 11.95 | 13.61x |
| 262144 | 2 | pipeline | 170.0 | 12.20 | 13.91x |
| 262144 | 4 | pipeline | 165.9 | 12.50 | 13.29x |
| 262144 | 8 | pipeline | 169.3 | 13.30 | 12.72x |
| 262144 | 16 | pipeline | 166.4 | 15.10 | 11.04x |
| 262144 | 32 | pipeline | 166.3 | 17.35 | 9.57x |
| 262144 | 64 | pipeline | 172.7 | 24.80 | 6.97x |
| 262144 | 128 | pipeline | 171.9 | 35.90 | 4.78x |

</details>

<details><summary>gb300 k=50 graph: 32 cells, speedup 3.95x / 5.88x /
8.04x</summary>

| V | B | route | top_k_first us | cake us | speedup |
|---|---|---|---|---|---|
| 32768 | 1 | pipeline | 40.6 | 9.80 | 4.16x |
| 32768 | 2 | pipeline | 52.3 | 9.70 | 5.39x |
| 32768 | 4 | pipeline | 53.2 | 9.70 | 5.48x |
| 32768 | 8 | pipeline | 51.0 | 9.80 | 5.22x |
| 32768 | 16 | pipeline | 49.2 | 9.90 | 4.98x |
| 32768 | 32 | pipeline | 52.2 | 10.20 | 5.10x |
| 32768 | 64 | pipeline | 52.0 | 11.00 | 4.72x |
| 32768 | 128 | pipeline | 55.5 | 11.95 | 4.64x |
| 128256 | 1 | pipeline | 75.9 | 10.10 | 7.48x |
| 128256 | 2 | pipeline | 82.8 | 10.30 | 8.04x |
| 128256 | 4 | pipeline | 83.1 | 10.60 | 7.82x |
| 128256 | 8 | pipeline | 82.3 | 10.90 | 7.54x |
| 128256 | 16 | pipeline | 83.5 | 13.20 | 6.33x |
| 128256 | 32 | pipeline | 85.3 | 14.40 | 5.92x |
| 128256 | 64 | pipeline | 88.9 | 16.90 | 5.26x |
| 128256 | 128 | pipeline | 95.5 | 22.30 | 4.29x |
| 151936 | 1 | pipeline | 78.9 | 12.00 | 6.58x |
| 151936 | 2 | pipeline | 84.5 | 12.20 | 6.93x |
| 151936 | 4 | pipeline | 84.2 | 12.40 | 6.78x |
| 151936 | 8 | pipeline | 86.8 | 12.90 | 6.73x |
| 151936 | 16 | pipeline | 89.6 | 14.55 | 6.16x |
| 151936 | 32 | pipeline | 89.6 | 15.70 | 5.70x |
| 151936 | 64 | pipeline | 92.4 | 19.00 | 4.86x |
| 151936 | 128 | pipeline | 103.8 | 25.50 | 4.07x |
| 262144 | 1 | pipeline | 81.7 | 12.10 | 6.75x |
| 262144 | 2 | pipeline | 87.2 | 12.40 | 7.06x |
| 262144 | 4 | pipeline | 87.7 | 12.70 | 6.92x |
| 262144 | 8 | pipeline | 88.1 | 13.70 | 6.45x |
| 262144 | 16 | pipeline | 89.4 | 15.30 | 5.83x |
| 262144 | 32 | pipeline | 131.7 | 17.70 | 7.44x |
| 262144 | 64 | pipeline | 121.3 | 25.10 | 4.84x |
| 262144 | 128 | pipeline | 144.7 | 36.60 | 3.95x |

</details>

<details><summary>gb300 k=1000 eager: 32 cells, speedup 3.55x / 5.35x /
7.86x</summary>

| V | B | route | top_k_first us | cake us | speedup |
|---|---|---|---|---|---|
| 32768 | 1 | pipeline | 61.3 | 16.80 | 3.55x |
| 32768 | 2 | pipeline | 64.5 | 17.00 | 3.72x |
| 32768 | 4 | pipeline | 68.2 | 16.70 | 4.01x |
| 32768 | 8 | pipeline | 69.9 | 17.55 | 3.99x |
| 32768 | 16 | pipeline | 69.9 | 17.50 | 3.95x |
| 32768 | 32 | pipeline | 73.5 | 17.35 | 4.21x |
| 32768 | 64 | pipeline | 74.7 | 17.35 | 4.28x |
| 32768 | 128 | pipeline | 75.0 | 18.10 | 4.15x |
| 128256 | 1 | pipeline | 78.8 | 17.10 | 4.57x |
| 128256 | 2 | pipeline | 86.2 | 17.60 | 4.84x |
| 128256 | 4 | pipeline | 94.6 | 17.35 | 5.43x |
| 128256 | 8 | pipeline | 98.5 | 17.80 | 5.52x |
| 128256 | 16 | pipeline | 105.4 | 19.60 | 5.39x |
| 128256 | 32 | pipeline | 112.2 | 20.40 | 5.50x |
| 128256 | 64 | pipeline | 138.0 | 28.70 | 4.81x |
| 128256 | 128 | pipeline | 184.6 | 34.65 | 5.33x |
| 151936 | 1 | pipeline | 85.0 | 18.60 | 4.56x |
| 151936 | 2 | pipeline | 90.8 | 18.70 | 4.87x |
| 151936 | 4 | pipeline | 100.2 | 19.05 | 5.26x |
| 151936 | 8 | pipeline | 107.3 | 19.30 | 5.56x |
| 151936 | 16 | pipeline | 109.7 | 20.45 | 5.36x |
| 151936 | 32 | pipeline | 117.8 | 21.40 | 5.50x |
| 151936 | 64 | pipeline | 156.5 | 26.90 | 5.81x |
| 151936 | 128 | pipeline | 212.5 | 36.80 | 5.77x |
| 262144 | 1 | pipeline | 99.5 | 19.05 | 5.23x |
| 262144 | 2 | pipeline | 118.4 | 19.75 | 5.97x |
| 262144 | 4 | pipeline | 125.5 | 20.30 | 6.16x |
| 262144 | 8 | pipeline | 136.7 | 20.55 | 6.62x |
| 262144 | 16 | pipeline | 150.7 | 22.70 | 6.65x |
| 262144 | 32 | pipeline | 190.8 | 24.30 | 7.86x |
| 262144 | 64 | pipeline | 255.0 | 32.95 | 7.74x |
| 262144 | 128 | pipeline | 359.7 | 47.50 | 7.57x |

</details>

<details><summary>gb300 k=1000 graph: 32 cells, speedup 2.99x / 4.87x /
7.88x</summary>

| V | B | route | top_k_first us | cake us | speedup |
|---|---|---|---|---|---|
| 32768 | 1 | pipeline | 43.0 | 14.40 | 2.99x |
| 32768 | 2 | pipeline | 45.6 | 14.50 | 3.15x |
| 32768 | 4 | pipeline | 46.5 | 14.70 | 3.17x |
| 32768 | 8 | pipeline | 45.9 | 14.70 | 3.13x |
| 32768 | 16 | pipeline | 52.9 | 14.90 | 3.55x |
| 32768 | 32 | pipeline | 51.2 | 16.30 | 3.14x |
| 32768 | 64 | pipeline | 54.8 | 18.10 | 3.02x |
| 32768 | 128 | pipeline | 56.7 | 18.50 | 3.07x |
| 128256 | 1 | pipeline | 69.5 | 17.10 | 4.07x |
| 128256 | 2 | pipeline | 80.6 | 17.45 | 4.62x |
| 128256 | 4 | pipeline | 108.1 | 17.70 | 6.12x |
| 128256 | 8 | pipeline | 90.5 | 18.00 | 5.04x |
| 128256 | 16 | pipeline | 92.7 | 20.10 | 4.60x |
| 128256 | 32 | pipeline | 92.4 | 21.50 | 4.29x |
| 128256 | 64 | pipeline | 155.0 | 30.05 | 5.15x |
| 128256 | 128 | pipeline | 207.5 | 35.55 | 5.84x |
| 151936 | 1 | pipeline | 76.7 | 18.25 | 4.20x |
| 151936 | 2 | pipeline | 90.2 | 18.80 | 4.81x |
| 151936 | 4 | pipeline | 93.1 | 19.10 | 4.87x |
| 151936 | 8 | pipeline | 123.9 | 19.30 | 6.41x |
| 151936 | 16 | pipeline | 103.6 | 21.10 | 4.87x |
| 151936 | 32 | pipeline | 133.0 | 22.60 | 5.88x |
| 151936 | 64 | pipeline | 175.6 | 27.60 | 6.37x |
| 151936 | 128 | pipeline | 230.9 | 37.75 | 6.12x |
| 262144 | 1 | pipeline | 88.5 | 20.20 | 4.38x |
| 262144 | 2 | pipeline | 118.3 | 19.90 | 5.95x |
| 262144 | 4 | pipeline | 117.4 | 20.15 | 5.82x |
| 262144 | 8 | pipeline | 126.0 | 20.60 | 6.13x |
| 262144 | 16 | pipeline | 133.7 | 23.05 | 5.80x |
| 262144 | 32 | pipeline | 196.1 | 25.20 | 7.71x |
| 262144 | 64 | pipeline | 261.1 | 34.00 | 7.68x |
| 262144 | 128 | pipeline | 386.7 | 49.10 | 7.88x |

</details>

<details><summary>b200 k=10 eager: 32 cells, speedup 3.12x / 6.93x /
11.07x</summary>

| V | B | route | top_k_first us | cake us | speedup |
|---|---|---|---|---|---|
| 32768 | 1 | pipeline | 41.4 | 9.30 | 4.46x |
| 32768 | 2 | pipeline | 43.0 | 9.20 | 4.70x |
| 32768 | 4 | pipeline | 44.9 | 9.20 | 4.89x |
| 32768 | 8 | pipeline | 45.5 | 9.20 | 4.94x |
| 32768 | 16 | pipeline | 48.2 | 9.30 | 5.15x |
| 32768 | 32 | pipeline | 51.2 | 9.70 | 5.28x |
| 32768 | 64 | pipeline | 52.5 | 10.10 | 5.18x |
| 32768 | 128 | pipeline | 53.0 | 11.40 | 4.66x |
| 128256 | 1 | pipeline | 102.0 | 9.20 | 11.07x |
| 128256 | 2 | pipeline | 102.2 | 9.30 | 10.98x |
| 128256 | 4 | pipeline | 101.5 | 9.50 | 10.71x |
| 128256 | 8 | pipeline | 102.3 | 9.70 | 10.58x |
| 128256 | 16 | pipeline | 102.6 | 12.40 | 8.26x |
| 128256 | 32 | pipeline | 105.0 | 13.20 | 7.98x |
| 128256 | 64 | pipeline | 104.9 | 16.45 | 6.37x |
| 128256 | 128 | pipeline | 106.3 | 21.80 | 4.89x |
| 151936 | 1 | pipeline | 102.7 | 11.20 | 9.14x |
| 151936 | 2 | pipeline | 103.1 | 11.40 | 9.08x |
| 151936 | 4 | pipeline | 103.0 | 11.65 | 8.82x |
| 151936 | 8 | pipeline | 103.6 | 12.00 | 8.61x |
| 151936 | 16 | pipeline | 103.3 | 13.70 | 7.56x |
| 151936 | 32 | pipeline | 103.4 | 15.20 | 6.82x |
| 151936 | 64 | pipeline | 107.2 | 18.50 | 5.80x |
| 151936 | 128 | pipeline | 106.9 | 24.90 | 4.30x |
| 262144 | 1 | pipeline | 102.6 | 11.55 | 8.88x |
| 262144 | 2 | pipeline | 104.0 | 11.80 | 8.80x |
| 262144 | 4 | pipeline | 103.7 | 12.20 | 8.53x |
| 262144 | 8 | pipeline | 105.0 | 12.60 | 8.31x |
| 262144 | 16 | pipeline | 104.8 | 14.90 | 7.03x |
| 262144 | 32 | pipeline | 112.4 | 17.50 | 6.41x |
| 262144 | 64 | pipeline | 107.7 | 24.30 | 4.44x |
| 262144 | 128 | pipeline | 122.6 | 39.30 | 3.12x |

</details>

<details><summary>b200 k=10 graph: 32 cells, speedup 3.66x / 6.19x /
9.38x</summary>

| V | B | route | top_k_first us | cake us | speedup |
|---|---|---|---|---|---|
| 32768 | 1 | pipeline | 44.8 | 9.25 | 4.83x |
| 32768 | 2 | pipeline | 41.3 | 9.20 | 4.50x |
| 32768 | 4 | pipeline | 41.2 | 9.10 | 4.51x |
| 32768 | 8 | pipeline | 45.9 | 9.20 | 4.97x |
| 32768 | 16 | pipeline | 47.6 | 9.40 | 5.04x |
| 32768 | 32 | pipeline | 47.3 | 9.80 | 4.81x |
| 32768 | 64 | pipeline | 54.7 | 10.40 | 5.27x |
| 32768 | 128 | pipeline | 57.5 | 11.60 | 4.98x |
| 128256 | 1 | pipeline | 86.1 | 9.20 | 9.38x |
| 128256 | 2 | pipeline | 82.8 | 9.30 | 8.87x |
| 128256 | 4 | pipeline | 80.5 | 9.60 | 8.38x |
| 128256 | 8 | pipeline | 80.8 | 9.80 | 8.23x |
| 128256 | 16 | pipeline | 81.5 | 12.60 | 6.47x |
| 128256 | 32 | pipeline | 83.7 | 13.50 | 6.20x |
| 128256 | 64 | pipeline | 87.9 | 16.70 | 5.25x |
| 128256 | 128 | pipeline | 93.5 | 22.00 | 4.25x |
| 151936 | 1 | pipeline | 91.3 | 11.10 | 8.22x |
| 151936 | 2 | pipeline | 88.6 | 11.30 | 7.86x |
| 151936 | 4 | pipeline | 87.7 | 11.60 | 7.60x |
| 151936 | 8 | pipeline | 88.0 | 11.85 | 7.44x |
| 151936 | 16 | pipeline | 90.0 | 14.00 | 6.45x |
| 151936 | 32 | pipeline | 91.9 | 15.40 | 5.96x |
| 151936 | 64 | pipeline | 96.4 | 18.80 | 5.14x |
| 151936 | 128 | pipeline | 102.4 | 25.10 | 4.09x |
| 262144 | 1 | pipeline | 93.8 | 11.70 | 8.03x |
| 262144 | 2 | pipeline | 91.1 | 12.10 | 7.51x |
| 262144 | 4 | pipeline | 89.3 | 12.50 | 7.14x |
| 262144 | 8 | pipeline | 89.5 | 12.90 | 6.92x |
| 262144 | 16 | pipeline | 93.5 | 15.20 | 6.17x |
| 262144 | 32 | pipeline | 134.1 | 17.80 | 7.55x |
| 262144 | 64 | pipeline | 122.8 | 24.50 | 5.01x |
| 262144 | 128 | pipeline | 142.0 | 38.85 | 3.66x |

</details>

<details><summary>b200 k=50 eager: 32 cells, speedup 3.14x / 6.96x /
10.29x</summary>

| V | B | route | top_k_first us | cake us | speedup |
|---|---|---|---|---|---|
| 32768 | 1 | pipeline | 42.6 | 9.70 | 4.40x |
| 32768 | 2 | pipeline | 43.6 | 9.55 | 4.55x |
| 32768 | 4 | pipeline | 45.1 | 9.60 | 4.71x |
| 32768 | 8 | pipeline | 46.6 | 9.60 | 4.84x |
| 32768 | 16 | pipeline | 49.5 | 9.70 | 5.09x |
| 32768 | 32 | pipeline | 51.1 | 10.00 | 5.10x |
| 32768 | 64 | pipeline | 52.5 | 10.60 | 4.97x |
| 32768 | 128 | pipeline | 54.0 | 11.70 | 4.61x |
| 128256 | 1 | pipeline | 103.0 | 10.00 | 10.29x |
| 128256 | 2 | pipeline | 103.4 | 10.10 | 10.22x |
| 128256 | 4 | pipeline | 103.1 | 10.30 | 10.04x |
| 128256 | 8 | pipeline | 104.8 | 10.50 | 9.98x |
| 128256 | 16 | pipeline | 104.7 | 12.60 | 8.28x |
| 128256 | 32 | pipeline | 107.6 | 14.00 | 7.71x |
| 128256 | 64 | pipeline | 107.0 | 16.70 | 6.40x |
| 128256 | 128 | pipeline | 107.7 | 22.30 | 4.84x |
| 151936 | 1 | pipeline | 104.4 | 12.00 | 8.70x |
| 151936 | 2 | pipeline | 103.9 | 12.05 | 8.64x |
| 151936 | 4 | pipeline | 104.7 | 12.20 | 8.61x |
| 151936 | 8 | pipeline | 105.2 | 12.60 | 8.34x |
| 151936 | 16 | pipeline | 104.7 | 14.00 | 7.49x |
| 151936 | 32 | pipeline | 105.6 | 15.40 | 6.86x |
| 151936 | 64 | pipeline | 108.4 | 18.85 | 5.75x |
| 151936 | 128 | pipeline | 109.4 | 25.30 | 4.32x |
| 262144 | 1 | pipeline | 104.4 | 11.75 | 8.86x |
| 262144 | 2 | pipeline | 105.4 | 12.00 | 8.79x |
| 262144 | 4 | pipeline | 105.4 | 12.40 | 8.47x |
| 262144 | 8 | pipeline | 106.8 | 13.10 | 8.18x |
| 262144 | 16 | pipeline | 106.2 | 15.10 | 7.05x |
| 262144 | 32 | pipeline | 114.9 | 17.60 | 6.52x |
| 262144 | 64 | pipeline | 110.0 | 24.40 | 4.52x |
| 262144 | 128 | pipeline | 124.1 | 39.55 | 3.14x |

</details>

<details><summary>b200 k=50 graph: 32 cells, speedup 3.73x / 6.09x /
8.51x</summary>

| V | B | route | top_k_first us | cake us | speedup |
|---|---|---|---|---|---|
| 32768 | 1 | pipeline | 43.9 | 9.70 | 4.55x |
| 32768 | 2 | pipeline | 45.8 | 9.55 | 4.80x |
| 32768 | 4 | pipeline | 46.0 | 9.50 | 4.84x |
| 32768 | 8 | pipeline | 47.4 | 9.60 | 4.93x |
| 32768 | 16 | pipeline | 51.3 | 9.80 | 5.22x |
| 32768 | 32 | pipeline | 48.9 | 10.10 | 4.85x |
| 32768 | 64 | pipeline | 59.4 | 10.80 | 5.52x |
| 32768 | 128 | pipeline | 60.0 | 11.85 | 5.06x |
| 128256 | 1 | pipeline | 85.0 | 10.00 | 8.51x |
| 128256 | 2 | pipeline | 84.3 | 10.20 | 8.28x |
| 128256 | 4 | pipeline | 82.0 | 10.40 | 7.86x |
| 128256 | 8 | pipeline | 85.9 | 10.70 | 8.06x |
| 128256 | 16 | pipeline | 83.1 | 12.90 | 6.46x |
| 128256 | 32 | pipeline | 84.4 | 14.25 | 5.91x |
| 128256 | 64 | pipeline | 102.3 | 17.00 | 6.02x |
| 128256 | 128 | pipeline | 95.9 | 22.50 | 4.27x |
| 151936 | 1 | pipeline | 89.2 | 12.10 | 7.40x |
| 151936 | 2 | pipeline | 89.9 | 12.40 | 7.26x |
| 151936 | 4 | pipeline | 89.4 | 12.50 | 7.17x |
| 151936 | 8 | pipeline | 92.9 | 12.80 | 7.24x |
| 151936 | 16 | pipeline | 91.5 | 14.20 | 6.42x |
| 151936 | 32 | pipeline | 92.8 | 15.70 | 5.92x |
| 151936 | 64 | pipeline | 100.2 | 19.10 | 5.25x |
| 151936 | 128 | pipeline | 105.4 | 25.50 | 4.13x |
| 262144 | 1 | pipeline | 91.0 | 11.90 | 7.62x |
| 262144 | 2 | pipeline | 91.0 | 12.30 | 7.39x |
| 262144 | 4 | pipeline | 90.1 | 12.80 | 7.06x |
| 262144 | 8 | pipeline | 94.1 | 13.40 | 7.02x |
| 262144 | 16 | pipeline | 94.4 | 15.30 | 6.16x |
| 262144 | 32 | pipeline | 134.3 | 17.80 | 7.54x |
| 262144 | 64 | pipeline | 126.6 | 24.65 | 5.14x |
| 262144 | 128 | pipeline | 145.0 | 38.80 | 3.73x |

</details>

<details><summary>b200 k=1000 eager: 32 cells, speedup 2.99x / 4.62x /
7.93x</summary>

| V | B | route | top_k_first us | cake us | speedup |
|---|---|---|---|---|---|
| 32768 | 1 | pipeline | 43.5 | 14.40 | 3.01x |
| 32768 | 2 | pipeline | 46.4 | 14.70 | 3.17x |
| 32768 | 4 | pipeline | 46.3 | 14.60 | 3.17x |
| 32768 | 8 | pipeline | 48.6 | 14.60 | 3.33x |
| 32768 | 16 | pipeline | 51.1 | 15.10 | 3.39x |
| 32768 | 32 | pipeline | 52.7 | 15.80 | 3.33x |
| 32768 | 64 | pipeline | 54.4 | 17.20 | 3.16x |
| 32768 | 128 | pipeline | 54.8 | 18.40 | 2.99x |
| 128256 | 1 | pipeline | 62.7 | 17.20 | 3.64x |
| 128256 | 2 | pipeline | 72.1 | 17.50 | 4.11x |
| 128256 | 4 | pipeline | 77.6 | 17.60 | 4.41x |
| 128256 | 8 | pipeline | 81.0 | 18.00 | 4.50x |
| 128256 | 16 | pipeline | 90.3 | 19.40 | 4.66x |
| 128256 | 32 | pipeline | 100.5 | 20.30 | 4.94x |
| 128256 | 64 | pipeline | 143.7 | 28.70 | 5.01x |
| 128256 | 128 | pipeline | 193.4 | 35.50 | 5.45x |
| 151936 | 1 | pipeline | 70.7 | 18.50 | 3.81x |
| 151936 | 2 | pipeline | 81.1 | 18.60 | 4.36x |
| 151936 | 4 | pipeline | 87.5 | 19.05 | 4.59x |
| 151936 | 8 | pipeline | 92.0 | 19.80 | 4.65x |
| 151936 | 16 | pipeline | 104.2 | 21.10 | 4.95x |
| 151936 | 32 | pipeline | 112.1 | 21.90 | 5.12x |
| 151936 | 64 | pipeline | 163.6 | 27.70 | 5.91x |
| 151936 | 128 | pipeline | 222.5 | 42.70 | 5.22x |
| 262144 | 1 | pipeline | 86.0 | 19.90 | 4.33x |
| 262144 | 2 | pipeline | 103.7 | 19.75 | 5.25x |
| 262144 | 4 | pipeline | 114.4 | 20.30 | 5.64x |
| 262144 | 8 | pipeline | 123.0 | 21.10 | 5.83x |
| 262144 | 16 | pipeline | 141.1 | 23.35 | 6.04x |
| 262144 | 32 | pipeline | 200.2 | 25.20 | 7.93x |
| 262144 | 64 | pipeline | 266.7 | 34.20 | 7.80x |
| 262144 | 128 | pipeline | 377.5 | 51.30 | 7.37x |

</details>

<details><summary>b200 k=1000 graph: 32 cells, speedup 2.97x / 5.04x /
8.91x</summary>

| V | B | route | top_k_first us | cake us | speedup |
|---|---|---|---|---|---|
| 32768 | 1 | pipeline | 46.8 | 14.50 | 3.23x |
| 32768 | 2 | pipeline | 47.8 | 14.80 | 3.23x |
| 32768 | 4 | pipeline | 47.4 | 14.70 | 3.22x |
| 32768 | 8 | pipeline | 50.8 | 15.20 | 3.34x |
| 32768 | 16 | pipeline | 47.5 | 15.30 | 3.10x |
| 32768 | 32 | pipeline | 55.1 | 16.50 | 3.33x |
| 32768 | 64 | pipeline | 56.4 | 18.00 | 3.13x |
| 32768 | 128 | pipeline | 57.4 | 19.30 | 2.97x |
| 128256 | 1 | pipeline | 83.0 | 17.40 | 4.78x |
| 128256 | 2 | pipeline | 87.7 | 17.70 | 4.95x |
| 128256 | 4 | pipeline | 84.0 | 17.90 | 4.69x |
| 128256 | 8 | pipeline | 88.1 | 18.65 | 4.73x |
| 128256 | 16 | pipeline | 110.5 | 19.60 | 5.65x |
| 128256 | 32 | pipeline | 94.0 | 21.60 | 4.36x |
| 128256 | 64 | pipeline | 153.9 | 30.25 | 5.08x |
| 128256 | 128 | pipeline | 203.6 | 35.95 | 5.67x |
| 151936 | 1 | pipeline | 92.2 | 18.50 | 4.99x |
| 151936 | 2 | pipeline | 98.6 | 19.00 | 5.18x |
| 151936 | 4 | pipeline | 94.1 | 19.40 | 4.86x |
| 151936 | 8 | pipeline | 123.9 | 19.60 | 6.34x |
| 151936 | 16 | pipeline | 104.1 | 21.00 | 4.95x |
| 151936 | 32 | pipeline | 124.2 | 22.85 | 5.42x |
| 151936 | 64 | pipeline | 188.2 | 28.80 | 6.53x |
| 151936 | 128 | pipeline | 234.4 | 44.05 | 5.32x |
| 262144 | 1 | pipeline | 118.9 | 19.90 | 5.98x |
| 262144 | 2 | pipeline | 129.4 | 20.10 | 6.45x |
| 262144 | 4 | pipeline | 119.9 | 20.60 | 5.83x |
| 262144 | 8 | pipeline | 190.8 | 21.40 | 8.91x |
| 262144 | 16 | pipeline | 138.6 | 23.95 | 5.78x |
| 262144 | 32 | pipeline | 223.7 | 26.10 | 8.56x |
| 262144 | 64 | pipeline | 265.7 | 34.90 | 7.61x |
| 262144 | 128 | pipeline | 420.4 | 50.50 | 8.34x |

</details>

<details><summary>h100 k=10 eager: 32 cells, speedup 2.51x / 6.57x /
12.06x</summary>

| V | B | route | top_k_first us | cake us | speedup |
|---|---|---|---|---|---|
| 32768 | 1 | pipeline | 45.0 | 10.20 | 4.40x |
| 32768 | 2 | pipeline | 46.8 | 10.40 | 4.50x |
| 32768 | 4 | pipeline | 48.5 | 10.50 | 4.64x |
| 32768 | 8 | pipeline | 49.1 | 10.80 | 4.57x |
| 32768 | 16 | pipeline | 52.6 | 11.50 | 4.59x |
| 32768 | 32 | pipeline | 54.6 | 11.10 | 4.93x |
| 32768 | 64 | pipeline | 55.7 | 12.30 | 4.53x |
| 32768 | 128 | pipeline | 57.5 | 15.90 | 3.61x |
| 128256 | 1 | pipeline | 113.9 | 9.40 | 12.06x |
| 128256 | 2 | pipeline | 114.4 | 9.60 | 11.88x |
| 128256 | 4 | pipeline | 114.5 | 10.20 | 11.22x |
| 128256 | 8 | pipeline | 114.2 | 11.00 | 10.41x |
| 128256 | 16 | pipeline | 115.1 | 12.70 | 9.06x |
| 128256 | 32 | pipeline | 117.3 | 16.35 | 7.17x |
| 128256 | 64 | pipeline | 117.9 | 23.40 | 5.05x |
| 128256 | 128 | pipeline | 118.5 | 41.00 | 2.89x |
| 151936 | 1 | pipeline | 115.2 | 9.90 | 11.69x |
| 151936 | 2 | pipeline | 114.2 | 10.30 | 11.09x |
| 151936 | 4 | pipeline | 115.4 | 10.80 | 10.67x |
| 151936 | 8 | pipeline | 115.4 | 11.40 | 10.16x |
| 151936 | 16 | pipeline | 115.1 | 13.40 | 8.58x |
| 151936 | 32 | pipeline | 115.1 | 18.50 | 6.22x |
| 151936 | 64 | pipeline | 118.2 | 26.40 | 4.48x |
| 151936 | 128 | pipeline | 119.2 | 42.00 | 2.84x |
| 262144 | 1 | pipeline | 115.4 | 10.90 | 10.61x |
| 262144 | 2 | pipeline | 115.4 | 11.20 | 10.30x |
| 262144 | 4 | pipeline | 115.9 | 12.00 | 9.66x |
| 262144 | 8 | pipeline | 115.7 | 13.20 | 8.73x |
| 262144 | 16 | pipeline | 115.8 | 16.70 | 6.93x |
| 262144 | 32 | pipeline | 126.7 | 27.30 | 4.63x |
| 262144 | 64 | pipeline | 133.3 | 43.50 | 3.06x |
| 262144 | 128 | pipeline | 156.4 | 62.25 | 2.51x |

</details>

<details><summary>h100 k=10 graph: 32 cells, speedup 2.75x / 5.38x /
8.79x</summary>

| V | B | route | top_k_first us | cake us | speedup |
|---|---|---|---|---|---|
| 32768 | 1 | pipeline | 43.6 | 10.20 | 4.26x |
| 32768 | 2 | pipeline | 47.6 | 10.40 | 4.59x |
| 32768 | 4 | pipeline | 51.0 | 10.50 | 4.86x |
| 32768 | 8 | pipeline | 50.1 | 10.80 | 4.66x |
| 32768 | 16 | pipeline | 50.1 | 11.50 | 4.36x |
| 32768 | 32 | pipeline | 53.8 | 11.10 | 4.85x |
| 32768 | 64 | pipeline | 55.8 | 12.30 | 4.53x |
| 32768 | 128 | pipeline | 65.5 | 15.85 | 4.13x |
| 128256 | 1 | pipeline | 82.6 | 9.50 | 8.72x |
| 128256 | 2 | pipeline | 85.2 | 9.70 | 8.79x |
| 128256 | 4 | pipeline | 81.3 | 10.20 | 7.96x |
| 128256 | 8 | pipeline | 84.7 | 11.00 | 7.70x |
| 128256 | 16 | pipeline | 86.6 | 12.70 | 6.80x |
| 128256 | 32 | pipeline | 91.1 | 16.40 | 5.56x |
| 128256 | 64 | pipeline | 100.1 | 23.30 | 4.29x |
| 128256 | 128 | pipeline | 120.1 | 40.85 | 2.94x |
| 151936 | 1 | pipeline | 86.6 | 10.00 | 8.70x |
| 151936 | 2 | pipeline | 88.9 | 10.40 | 8.57x |
| 151936 | 4 | pipeline | 86.8 | 10.80 | 8.02x |
| 151936 | 8 | pipeline | 90.0 | 11.50 | 7.86x |
| 151936 | 16 | pipeline | 90.8 | 13.30 | 6.81x |
| 151936 | 32 | pipeline | 95.4 | 18.30 | 5.21x |
| 151936 | 64 | pipeline | 112.8 | 26.50 | 4.26x |
| 151936 | 128 | pipeline | 130.8 | 42.15 | 3.10x |
| 262144 | 1 | pipeline | 88.8 | 10.90 | 8.14x |
| 262144 | 2 | pipeline | 91.3 | 11.20 | 8.13x |
| 262144 | 4 | pipeline | 88.3 | 12.05 | 7.34x |
| 262144 | 8 | pipeline | 91.9 | 13.20 | 6.95x |
| 262144 | 16 | pipeline | 95.6 | 16.70 | 5.72x |
| 262144 | 32 | pipeline | 142.7 | 27.95 | 5.11x |
| 262144 | 64 | pipeline | 148.3 | 43.75 | 3.39x |
| 262144 | 128 | pipeline | 172.1 | 62.50 | 2.75x |

</details>

<details><summary>h100 k=50 eager: 32 cells, speedup 2.50x / 6.10x /
11.43x</summary>

| V | B | route | top_k_first us | cake us | speedup |
|---|---|---|---|---|---|
| 32768 | 1 | pipeline | 45.7 | 10.30 | 4.45x |
| 32768 | 2 | pipeline | 47.1 | 10.40 | 4.52x |
| 32768 | 4 | pipeline | 48.4 | 10.50 | 4.62x |
| 32768 | 8 | pipeline | 49.9 | 10.80 | 4.62x |
| 32768 | 16 | pipeline | 53.3 | 11.50 | 4.64x |
| 32768 | 32 | pipeline | 54.8 | 11.20 | 4.89x |
| 32768 | 64 | pipeline | 56.3 | 12.50 | 4.50x |
| 32768 | 128 | pipeline | 58.3 | 16.10 | 3.63x |
| 128256 | 1 | pipeline | 114.1 | 10.00 | 11.43x |
| 128256 | 2 | pipeline | 114.0 | 10.40 | 11.00x |
| 128256 | 4 | pipeline | 113.5 | 10.90 | 10.40x |
| 128256 | 8 | pipeline | 114.4 | 11.80 | 9.69x |
| 128256 | 16 | pipeline | 114.3 | 13.80 | 8.27x |
| 128256 | 32 | pipeline | 117.7 | 17.10 | 6.87x |
| 128256 | 64 | pipeline | 117.7 | 24.10 | 4.89x |
| 128256 | 128 | pipeline | 117.8 | 41.60 | 2.83x |
| 151936 | 1 | pipeline | 114.3 | 10.60 | 10.79x |
| 151936 | 2 | pipeline | 114.6 | 11.00 | 10.44x |
| 151936 | 4 | pipeline | 114.2 | 11.50 | 9.92x |
| 151936 | 8 | pipeline | 115.5 | 12.20 | 9.47x |
| 151936 | 16 | pipeline | 114.4 | 14.50 | 7.91x |
| 151936 | 32 | pipeline | 115.0 | 19.70 | 5.84x |
| 151936 | 64 | pipeline | 118.0 | 27.50 | 4.29x |
| 151936 | 128 | pipeline | 156.0 | 42.70 | 3.65x |
| 262144 | 1 | pipeline | 114.9 | 11.10 | 10.32x |
| 262144 | 2 | pipeline | 115.2 | 11.50 | 10.03x |
| 262144 | 4 | pipeline | 115.1 | 12.20 | 9.47x |
| 262144 | 8 | pipeline | 115.7 | 14.20 | 8.16x |
| 262144 | 16 | pipeline | 115.2 | 18.10 | 6.36x |
| 262144 | 32 | pipeline | 126.9 | 27.60 | 4.59x |
| 262144 | 64 | pipeline | 134.5 | 43.75 | 3.07x |
| 262144 | 128 | pipeline | 157.1 | 62.90 | 2.50x |

</details>

<details><summary>h100 k=50 graph: 32 cells, speedup 2.76x / 5.30x /
8.26x</summary>

| V | B | route | top_k_first us | cake us | speedup |
|---|---|---|---|---|---|
| 32768 | 1 | pipeline | 44.9 | 10.30 | 4.37x |
| 32768 | 2 | pipeline | 47.1 | 10.40 | 4.51x |
| 32768 | 4 | pipeline | 48.9 | 10.50 | 4.66x |
| 32768 | 8 | pipeline | 51.0 | 10.80 | 4.73x |
| 32768 | 16 | pipeline | 55.9 | 11.50 | 4.86x |
| 32768 | 32 | pipeline | 67.4 | 11.30 | 5.98x |
| 32768 | 64 | pipeline | 58.9 | 12.60 | 4.68x |
| 32768 | 128 | pipeline | 65.3 | 16.00 | 4.07x |
| 128256 | 1 | pipeline | 82.5 | 10.00 | 8.26x |
| 128256 | 2 | pipeline | 82.8 | 10.40 | 7.96x |
| 128256 | 4 | pipeline | 82.2 | 10.90 | 7.53x |
| 128256 | 8 | pipeline | 86.5 | 11.80 | 7.32x |
| 128256 | 16 | pipeline | 85.7 | 13.90 | 6.18x |
| 128256 | 32 | pipeline | 93.0 | 17.20 | 5.42x |
| 128256 | 64 | pipeline | 102.0 | 24.10 | 4.24x |
| 128256 | 128 | pipeline | 121.2 | 41.50 | 2.92x |
| 151936 | 1 | pipeline | 86.9 | 10.70 | 8.16x |
| 151936 | 2 | pipeline | 86.5 | 11.00 | 7.83x |
| 151936 | 4 | pipeline | 87.9 | 11.50 | 7.63x |
| 151936 | 8 | pipeline | 91.7 | 12.30 | 7.46x |
| 151936 | 16 | pipeline | 90.3 | 14.40 | 6.27x |
| 151936 | 32 | pipeline | 96.9 | 19.55 | 4.96x |
| 151936 | 64 | pipeline | 113.9 | 27.60 | 4.13x |
| 151936 | 128 | pipeline | 172.6 | 42.75 | 4.04x |
| 262144 | 1 | pipeline | 88.2 | 11.20 | 7.89x |
| 262144 | 2 | pipeline | 88.8 | 11.50 | 7.71x |
| 262144 | 4 | pipeline | 88.8 | 12.30 | 7.25x |
| 262144 | 8 | pipeline | 93.0 | 14.10 | 6.57x |
| 262144 | 16 | pipeline | 94.1 | 18.10 | 5.19x |
| 262144 | 32 | pipeline | 144.0 | 28.20 | 5.11x |
| 262144 | 64 | pipeline | 150.1 | 44.15 | 3.40x |
| 262144 | 128 | pipeline | 173.1 | 62.80 | 2.76x |

</details>

<details><summary>h100 k=1000 eager: 32 cells, speedup 2.51x / 4.41x /
6.61x</summary>

| V | B | route | top_k_first us | cake us | speedup |
|---|---|---|---|---|---|
| 32768 | 1 | pipeline | 46.4 | 14.80 | 3.14x |
| 32768 | 2 | pipeline | 47.6 | 15.00 | 3.17x |
| 32768 | 4 | pipeline | 48.6 | 15.10 | 3.22x |
| 32768 | 8 | pipeline | 50.1 | 15.10 | 3.32x |
| 32768 | 16 | pipeline | 53.4 | 15.90 | 3.37x |
| 32768 | 32 | pipeline | 55.5 | 18.00 | 3.09x |
| 32768 | 64 | pipeline | 56.6 | 19.20 | 2.95x |
| 32768 | 128 | pipeline | 59.1 | 23.50 | 2.51x |
| 128256 | 1 | pipeline | 65.8 | 19.55 | 3.38x |
| 128256 | 2 | pipeline | 73.5 | 19.60 | 3.74x |
| 128256 | 4 | pipeline | 78.0 | 20.15 | 3.88x |
| 128256 | 8 | pipeline | 81.7 | 20.70 | 3.94x |
| 128256 | 16 | pipeline | 92.8 | 21.20 | 4.39x |
| 128256 | 32 | pipeline | 106.6 | 28.50 | 3.74x |
| 128256 | 64 | pipeline | 167.3 | 34.65 | 4.83x |
| 128256 | 128 | pipeline | 235.9 | 46.40 | 5.08x |
| 151936 | 1 | pipeline | 73.7 | 18.30 | 4.03x |
| 151936 | 2 | pipeline | 82.4 | 18.60 | 4.43x |
| 151936 | 4 | pipeline | 88.0 | 18.80 | 4.67x |
| 151936 | 8 | pipeline | 92.1 | 19.80 | 4.65x |
| 151936 | 16 | pipeline | 106.7 | 22.10 | 4.83x |
| 151936 | 32 | pipeline | 123.3 | 28.10 | 4.38x |
| 151936 | 64 | pipeline | 194.8 | 34.40 | 5.67x |
| 151936 | 128 | pipeline | 279.9 | 52.20 | 5.37x |
| 262144 | 1 | pipeline | 93.9 | 19.70 | 4.77x |
| 262144 | 2 | pipeline | 105.1 | 20.30 | 5.19x |
| 262144 | 4 | pipeline | 114.8 | 20.80 | 5.52x |
| 262144 | 8 | pipeline | 120.8 | 22.30 | 5.42x |
| 262144 | 16 | pipeline | 146.0 | 25.70 | 5.68x |
| 262144 | 32 | pipeline | 230.8 | 39.00 | 5.92x |
| 262144 | 64 | pipeline | 319.2 | 50.55 | 6.31x |
| 262144 | 128 | pipeline | 469.6 | 71.05 | 6.61x |

</details>

<details><summary>h100 k=1000 graph: 32 cells, speedup 2.83x / 4.62x /
7.48x</summary>

| V | B | route | top_k_first us | cake us | speedup |
|---|---|---|---|---|---|
| 32768 | 1 | pipeline | 49.2 | 14.60 | 3.37x |
| 32768 | 2 | pipeline | 45.9 | 14.80 | 3.10x |
| 32768 | 4 | pipeline | 49.0 | 15.00 | 3.27x |
| 32768 | 8 | pipeline | 56.5 | 15.30 | 3.69x |
| 32768 | 16 | pipeline | 50.8 | 15.80 | 3.22x |
| 32768 | 32 | pipeline | 63.2 | 17.60 | 3.59x |
| 32768 | 64 | pipeline | 65.5 | 19.20 | 3.40x |
| 32768 | 128 | pipeline | 67.3 | 23.80 | 2.83x |
| 128256 | 1 | pipeline | 87.3 | 19.50 | 4.48x |
| 128256 | 2 | pipeline | 74.3 | 19.00 | 3.90x |
| 128256 | 4 | pipeline | 86.9 | 19.80 | 4.39x |
| 128256 | 8 | pipeline | 94.7 | 20.85 | 4.55x |
| 128256 | 16 | pipeline | 94.4 | 20.70 | 4.56x |
| 128256 | 32 | pipeline | 120.5 | 29.40 | 4.10x |
| 128256 | 64 | pipeline | 165.5 | 35.10 | 4.71x |
| 128256 | 128 | pipeline | 251.2 | 46.70 | 5.38x |
| 151936 | 1 | pipeline | 97.9 | 18.35 | 5.34x |
| 151936 | 2 | pipeline | 82.1 | 18.60 | 4.42x |
| 151936 | 4 | pipeline | 95.4 | 19.60 | 4.86x |
| 151936 | 8 | pipeline | 102.5 | 19.80 | 5.18x |
| 151936 | 16 | pipeline | 105.5 | 22.50 | 4.69x |
| 151936 | 32 | pipeline | 116.8 | 27.40 | 4.27x |
| 151936 | 64 | pipeline | 199.5 | 35.00 | 5.70x |
| 151936 | 128 | pipeline | 284.0 | 52.40 | 5.42x |
| 262144 | 1 | pipeline | 124.2 | 19.70 | 6.30x |
| 262144 | 2 | pipeline | 118.4 | 20.30 | 5.83x |
| 262144 | 4 | pipeline | 120.3 | 20.80 | 5.79x |
| 262144 | 8 | pipeline | 132.6 | 22.15 | 5.99x |
| 262144 | 16 | pipeline | 142.2 | 25.70 | 5.53x |
| 262144 | 32 | pipeline | 235.3 | 39.20 | 6.00x |
| 262144 | 64 | pipeline | 352.8 | 52.10 | 6.77x |
| 262144 | 128 | pipeline | 534.2 | 71.40 | 7.48x |

</details>

<details><summary>r200 k=10 eager: 32 cells, speedup 3.16x / 5.24x /
7.28x</summary>

| V | B | route | top_k_first us | cake us | speedup |
|---|---|---|---|---|---|
| 32768 | 1 | pipeline | 28.9 | 9.10 | 3.16x |
| 32768 | 2 | pipeline | 30.6 | 9.40 | 3.25x |
| 32768 | 4 | pipeline | 32.0 | 9.60 | 3.35x |
| 32768 | 8 | pipeline | 32.6 | 9.80 | 3.32x |
| 32768 | 16 | pipeline | 33.8 | 10.35 | 3.27x |
| 32768 | 32 | pipeline | 37.6 | 10.80 | 3.49x |
| 32768 | 64 | pipeline | 37.4 | 10.20 | 3.66x |
| 32768 | 128 | pipeline | 38.2 | 10.80 | 3.52x |
| 128256 | 1 | pipeline | 70.1 | 9.60 | 7.28x |
| 128256 | 2 | pipeline | 70.5 | 10.00 | 7.03x |
| 128256 | 4 | pipeline | 70.5 | 10.10 | 6.97x |
| 128256 | 8 | pipeline | 70.8 | 10.30 | 6.85x |
| 128256 | 16 | pipeline | 70.7 | 11.35 | 6.22x |
| 128256 | 32 | pipeline | 74.7 | 13.00 | 5.75x |
| 128256 | 64 | pipeline | 73.5 | 14.95 | 4.92x |
| 128256 | 128 | pipeline | 72.8 | 18.60 | 3.91x |
| 151936 | 1 | pipeline | 70.5 | 10.05 | 7.02x |
| 151936 | 2 | pipeline | 70.5 | 10.50 | 6.71x |
| 151936 | 4 | pipeline | 70.6 | 10.60 | 6.69x |
| 151936 | 8 | pipeline | 70.3 | 11.00 | 6.39x |
| 151936 | 16 | pipeline | 70.0 | 11.70 | 5.97x |
| 151936 | 32 | pipeline | 70.9 | 14.10 | 5.03x |
| 151936 | 64 | pipeline | 74.3 | 16.60 | 4.47x |
| 151936 | 128 | pipeline | 73.0 | 21.55 | 3.39x |
| 262144 | 1 | pipeline | 70.3 | 10.50 | 6.72x |
| 262144 | 2 | pipeline | 70.6 | 10.80 | 6.56x |
| 262144 | 4 | pipeline | 70.2 | 11.10 | 6.34x |
| 262144 | 8 | pipeline | 70.8 | 11.70 | 6.04x |
| 262144 | 16 | pipeline | 70.6 | 13.00 | 5.44x |
| 262144 | 32 | pipeline | 70.7 | 15.50 | 4.57x |
| 262144 | 64 | pipeline | 86.3 | 20.45 | 4.22x |
| 262144 | 128 | pipeline | 105.3 | 28.00 | 3.76x |

</details>

<details><summary>r200 k=10 graph: 32 cells, speedup 3.51x / 5.52x /
7.31x</summary>

| V | B | route | top_k_first us | cake us | speedup |
|---|---|---|---|---|---|
| 32768 | 1 | pipeline | 32.3 | 9.20 | 3.51x |
| 32768 | 2 | pipeline | 34.9 | 9.60 | 3.63x |
| 32768 | 4 | pipeline | 37.4 | 9.70 | 3.87x |
| 32768 | 8 | pipeline | 37.0 | 10.00 | 3.68x |
| 32768 | 16 | pipeline | 43.1 | 10.50 | 4.12x |
| 32768 | 32 | pipeline | 43.6 | 11.00 | 3.95x |
| 32768 | 64 | pipeline | 45.8 | 10.20 | 4.47x |
| 32768 | 128 | pipeline | 45.8 | 10.90 | 4.20x |
| 128256 | 1 | pipeline | 71.1 | 9.70 | 7.31x |
| 128256 | 2 | pipeline | 69.5 | 10.10 | 6.90x |
| 128256 | 4 | pipeline | 73.5 | 10.10 | 7.25x |
| 128256 | 8 | pipeline | 73.7 | 10.50 | 7.02x |
| 128256 | 16 | pipeline | 72.8 | 11.40 | 6.39x |
| 128256 | 32 | pipeline | 73.7 | 13.30 | 5.53x |
| 128256 | 64 | pipeline | 75.7 | 15.10 | 5.02x |
| 128256 | 128 | pipeline | 77.6 | 18.50 | 4.20x |
| 151936 | 1 | pipeline | 70.8 | 10.20 | 6.92x |
| 151936 | 2 | pipeline | 73.4 | 10.70 | 6.85x |
| 151936 | 4 | pipeline | 75.1 | 10.80 | 6.97x |
| 151936 | 8 | pipeline | 76.2 | 11.30 | 6.77x |
| 151936 | 16 | pipeline | 78.2 | 11.80 | 6.60x |
| 151936 | 32 | pipeline | 79.3 | 14.40 | 5.50x |
| 151936 | 64 | pipeline | 78.9 | 16.80 | 4.70x |
| 151936 | 128 | pipeline | 88.8 | 21.60 | 4.11x |
| 262144 | 1 | pipeline | 75.8 | 10.60 | 7.16x |
| 262144 | 2 | pipeline | 74.1 | 10.90 | 6.81x |
| 262144 | 4 | pipeline | 77.8 | 11.20 | 6.97x |
| 262144 | 8 | pipeline | 78.4 | 11.80 | 6.62x |
| 262144 | 16 | pipeline | 78.6 | 13.00 | 6.04x |
| 262144 | 32 | pipeline | 79.8 | 15.60 | 5.10x |
| 262144 | 64 | pipeline | 104.8 | 20.90 | 5.02x |
| 262144 | 128 | pipeline | 122.0 | 28.10 | 4.35x |

</details>

<details><summary>r200 k=50 eager: 32 cells, speedup 3.28x / 5.22x /
7.25x</summary>

| V | B | route | top_k_first us | cake us | speedup |
|---|---|---|---|---|---|
| 32768 | 1 | pipeline | 29.9 | 9.10 | 3.28x |
| 32768 | 2 | pipeline | 31.4 | 9.60 | 3.28x |
| 32768 | 4 | pipeline | 32.0 | 9.70 | 3.29x |
| 32768 | 8 | pipeline | 33.5 | 9.95 | 3.36x |
| 32768 | 16 | pipeline | 35.5 | 10.60 | 3.36x |
| 32768 | 32 | pipeline | 36.9 | 11.00 | 3.35x |
| 32768 | 64 | pipeline | 38.1 | 10.50 | 3.64x |
| 32768 | 128 | pipeline | 39.2 | 11.00 | 3.56x |
| 128256 | 1 | pipeline | 69.9 | 9.60 | 7.25x |
| 128256 | 2 | pipeline | 70.4 | 10.10 | 6.98x |
| 128256 | 4 | pipeline | 70.6 | 10.15 | 6.96x |
| 128256 | 8 | pipeline | 70.3 | 10.50 | 6.72x |
| 128256 | 16 | pipeline | 70.2 | 11.10 | 6.32x |
| 128256 | 32 | pipeline | 72.5 | 13.20 | 5.52x |
| 128256 | 64 | pipeline | 72.8 | 15.10 | 4.81x |
| 128256 | 128 | pipeline | 72.9 | 18.90 | 3.86x |
| 151936 | 1 | pipeline | 71.1 | 10.15 | 6.96x |
| 151936 | 2 | pipeline | 70.5 | 10.70 | 6.61x |
| 151936 | 4 | pipeline | 71.1 | 10.70 | 6.65x |
| 151936 | 8 | pipeline | 70.5 | 11.10 | 6.35x |
| 151936 | 16 | pipeline | 70.6 | 11.80 | 5.96x |
| 151936 | 32 | pipeline | 70.3 | 14.10 | 4.97x |
| 151936 | 64 | pipeline | 72.3 | 16.80 | 4.30x |
| 151936 | 128 | pipeline | 73.5 | 22.20 | 3.31x |
| 262144 | 1 | pipeline | 70.0 | 10.90 | 6.43x |
| 262144 | 2 | pipeline | 70.4 | 11.00 | 6.39x |
| 262144 | 4 | pipeline | 70.4 | 11.40 | 6.17x |
| 262144 | 8 | pipeline | 70.8 | 11.90 | 5.96x |
| 262144 | 16 | pipeline | 70.3 | 12.80 | 5.48x |
| 262144 | 32 | pipeline | 71.1 | 15.60 | 4.57x |
| 262144 | 64 | pipeline | 87.8 | 20.60 | 4.25x |
| 262144 | 128 | pipeline | 107.5 | 28.20 | 3.81x |

</details>

<details><summary>r200 k=50 graph: 32 cells, speedup 3.40x / 5.57x /
7.31x</summary>

| V | B | route | top_k_first us | cake us | speedup |
|---|---|---|---|---|---|
| 32768 | 1 | pipeline | 36.3 | 9.45 | 3.85x |
| 32768 | 2 | pipeline | 33.4 | 9.85 | 3.40x |
| 32768 | 4 | pipeline | 38.1 | 9.90 | 3.85x |
| 32768 | 8 | pipeline | 42.2 | 10.10 | 4.16x |
| 32768 | 16 | pipeline | 42.5 | 10.70 | 3.98x |
| 32768 | 32 | pipeline | 38.3 | 11.20 | 3.42x |
| 32768 | 64 | pipeline | 44.8 | 10.50 | 4.27x |
| 32768 | 128 | pipeline | 45.2 | 11.00 | 4.11x |
| 128256 | 1 | pipeline | 71.1 | 9.70 | 7.31x |
| 128256 | 2 | pipeline | 69.7 | 10.10 | 6.89x |
| 128256 | 4 | pipeline | 72.5 | 10.20 | 7.11x |
| 128256 | 8 | pipeline | 74.7 | 10.60 | 7.03x |
| 128256 | 16 | pipeline | 71.5 | 11.30 | 6.35x |
| 128256 | 32 | pipeline | 75.1 | 13.45 | 5.59x |
| 128256 | 64 | pipeline | 76.5 | 15.20 | 5.02x |
| 128256 | 128 | pipeline | 79.3 | 18.90 | 4.19x |
| 151936 | 1 | pipeline | 70.8 | 10.40 | 6.82x |
| 151936 | 2 | pipeline | 73.9 | 10.80 | 6.81x |
| 151936 | 4 | pipeline | 75.3 | 10.90 | 6.90x |
| 151936 | 8 | pipeline | 77.7 | 11.35 | 6.84x |
| 151936 | 16 | pipeline | 77.5 | 12.00 | 6.47x |
| 151936 | 32 | pipeline | 80.6 | 14.50 | 5.55x |
| 151936 | 64 | pipeline | 79.3 | 16.90 | 4.69x |
| 151936 | 128 | pipeline | 89.5 | 22.30 | 4.01x |
| 262144 | 1 | pipeline | 76.1 | 11.00 | 6.91x |
| 262144 | 2 | pipeline | 74.3 | 11.10 | 6.67x |
| 262144 | 4 | pipeline | 76.4 | 11.50 | 6.67x |
| 262144 | 8 | pipeline | 79.4 | 12.10 | 6.58x |
| 262144 | 16 | pipeline | 77.2 | 12.90 | 5.99x |
| 262144 | 32 | pipeline | 80.4 | 15.80 | 5.07x |
| 262144 | 64 | pipeline | 106.5 | 21.00 | 5.07x |
| 262144 | 128 | pipeline | 124.2 | 28.30 | 4.39x |

</details>

<details><summary>r200 k=1000 eager: 32 cells, speedup 2.37x / 4.51x /
7.69x</summary>

| V | B | route | top_k_first us | cake us | speedup |
|---|---|---|---|---|---|
| 32768 | 1 | pipeline | 30.0 | 12.70 | 2.37x |
| 32768 | 2 | pipeline | 31.4 | 13.20 | 2.38x |
| 32768 | 4 | pipeline | 32.6 | 13.35 | 2.44x |
| 32768 | 8 | pipeline | 33.6 | 13.70 | 2.45x |
| 32768 | 16 | pipeline | 35.8 | 13.80 | 2.59x |
| 32768 | 32 | pipeline | 36.8 | 14.00 | 2.62x |
| 32768 | 64 | pipeline | 38.5 | 15.80 | 2.43x |
| 32768 | 128 | pipeline | 39.5 | 16.20 | 2.44x |
| 128256 | 1 | pipeline | 55.5 | 14.80 | 3.74x |
| 128256 | 2 | pipeline | 62.2 | 15.70 | 3.97x |
| 128256 | 4 | pipeline | 65.9 | 16.00 | 4.11x |
| 128256 | 8 | pipeline | 68.0 | 16.20 | 4.20x |
| 128256 | 16 | pipeline | 75.6 | 16.75 | 4.51x |
| 128256 | 32 | pipeline | 84.2 | 17.70 | 4.77x |
| 128256 | 64 | pipeline | 92.3 | 23.55 | 3.92x |
| 128256 | 128 | pipeline | 137.9 | 30.55 | 4.51x |
| 151936 | 1 | pipeline | 63.8 | 15.60 | 4.09x |
| 151936 | 2 | pipeline | 70.9 | 16.10 | 4.41x |
| 151936 | 4 | pipeline | 74.7 | 16.20 | 4.60x |
| 151936 | 8 | pipeline | 77.4 | 16.60 | 4.66x |
| 151936 | 16 | pipeline | 87.5 | 17.20 | 5.10x |
| 151936 | 32 | pipeline | 95.4 | 18.50 | 5.16x |
| 151936 | 64 | pipeline | 107.4 | 22.40 | 4.80x |
| 151936 | 128 | pipeline | 161.0 | 35.55 | 4.53x |
| 262144 | 1 | pipeline | 80.2 | 17.55 | 4.57x |
| 262144 | 2 | pipeline | 92.1 | 18.05 | 5.11x |
| 262144 | 4 | pipeline | 99.6 | 17.90 | 5.56x |
| 262144 | 8 | pipeline | 103.5 | 18.30 | 5.67x |
| 262144 | 16 | pipeline | 118.5 | 19.30 | 6.15x |
| 262144 | 32 | pipeline | 135.3 | 20.70 | 6.54x |
| 262144 | 64 | pipeline | 198.7 | 28.20 | 7.05x |
| 262144 | 128 | pipeline | 293.2 | 38.10 | 7.69x |

</details>

<details><summary>r200 k=1000 graph: 32 cells, speedup 2.64x / 4.44x /
10.51x</summary>

| V | B | route | top_k_first us | cake us | speedup |
|---|---|---|---|---|---|
| 32768 | 1 | pipeline | 34.0 | 12.90 | 2.64x |
| 32768 | 2 | pipeline | 35.7 | 13.35 | 2.67x |
| 32768 | 4 | pipeline | 35.4 | 13.40 | 2.64x |
| 32768 | 8 | pipeline | 43.1 | 13.80 | 3.13x |
| 32768 | 16 | pipeline | 38.8 | 14.00 | 2.77x |
| 32768 | 32 | pipeline | 43.2 | 14.10 | 3.07x |
| 32768 | 64 | pipeline | 44.1 | 15.90 | 2.77x |
| 32768 | 128 | pipeline | 46.8 | 17.10 | 2.74x |
| 128256 | 1 | pipeline | 58.7 | 15.30 | 3.84x |
| 128256 | 2 | pipeline | 69.6 | 15.70 | 4.42x |
| 128256 | 4 | pipeline | 62.7 | 16.15 | 3.89x |
| 128256 | 8 | pipeline | 77.0 | 16.20 | 4.77x |
| 128256 | 16 | pipeline | 95.0 | 17.10 | 5.56x |
| 128256 | 32 | pipeline | 79.5 | 18.10 | 4.39x |
| 128256 | 64 | pipeline | 96.7 | 23.85 | 4.03x |
| 128256 | 128 | pipeline | 143.4 | 30.15 | 4.76x |
| 151936 | 1 | pipeline | 65.2 | 16.15 | 4.05x |
| 151936 | 2 | pipeline | 76.8 | 16.95 | 4.53x |
| 151936 | 4 | pipeline | 69.5 | 17.20 | 4.05x |
| 151936 | 8 | pipeline | 99.4 | 17.20 | 5.79x |
| 151936 | 16 | pipeline | 109.1 | 17.75 | 6.14x |
| 151936 | 32 | pipeline | 116.0 | 18.65 | 6.23x |
| 151936 | 64 | pipeline | 116.7 | 22.40 | 5.21x |
| 151936 | 128 | pipeline | 173.4 | 36.35 | 4.78x |
| 262144 | 1 | pipeline | 75.4 | 18.00 | 4.19x |
| 262144 | 2 | pipeline | 98.9 | 19.10 | 5.18x |
| 262144 | 4 | pipeline | 84.0 | 18.80 | 4.46x |
| 262144 | 8 | pipeline | 199.4 | 19.00 | 10.51x |
| 262144 | 16 | pipeline | 117.3 | 19.70 | 5.96x |
| 262144 | 32 | pipeline | 138.1 | 21.00 | 6.58x |
| 262144 | 64 | pipeline | 197.9 | 28.40 | 6.98x |
| 262144 | 128 | pipeline | 305.7 | 37.55 | 8.16x |

</details>

🤖 Generated with [Claude Code](https://claude.com/claude-code)

**CI follow-up (head 3121b2831, test-only).** The mirror CI pipeline for
head aa8e2c596 ran the two `cake_sampling` test files on every runner
class; the only test failure was
`test_cuda_graph_capture_never_registers_the_generator` on the GB300
cu129 shard (torch 2.13.0+cu129, nvidia-cuda-cupti-cu12 12.9.79), where
`torch.profiler` returned no CUDA events for the graph replay and the
test's `assert names and ...` failed on an empty list while every
behavioural assertion before it passed. The same stack reports events on
B200, and the cu130 / cu134 GB300 shards passed the test. The test now
uses CUPTI-independent witnesses (CPU-activity `aten::clone` sentinel,
no dispatcher-level `aten::fill*` event during the replay,
default-generator host state unchanged after two replays,
bitwise-reproducible replay) and keeps the `FillFunctor` kernel-name
check as evidence where CUPTI reports the replay. Validation on a B200
node (torch 2.13): the two test files pass 262 / 18 skipped (the
previous head's count), and a probe of the witnesses on the same node
showed them silent on the shipped sampler and firing (`aten::fill_` CPU
events + host-offset advance) for a capture that consumes the default
generator. The host route and the kernel bundle are unchanged. Follow-up
validation at this head: the two test files pass 262 / 18 skipped on an
R200 (sm_107) node as well, with the same witness probe passing there,
and the PR's own CI shards for this head report the same counts per GPU
class (B200 unit shards 207 + 55 passed / 0 failed / 18 skipped for each
of cu129 / cu130 / cu134, R200 shards 207 + 55 / 0 / 18, RTX PRO 6000
cu130 / cu134 254 / 0 / 26, plan and multi-node jobs green); every GB200
and GB300 unit shard also finished green (207 + 55 passed / 0 failed /
18 skipped per CUDA variant, including the GB300 cu129 shard that failed
on the previous head), and the only red CI jobs are
runner-infrastructure failures that executed no test (multi-GPU jobs
that never left their Slurm queue within the job timeout, one RTX PRO
6000 cu129 job whose node allocation never arrived). The R200 class-C
matrix subset of the small-k local-select route (60 rows, both tree
orders) stays faster than the previous release in every row, at 5.6-8.1x
over `top_k_first`.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Performance**
* Updated sampling launch selection for supported NVIDIA GPUs, including
improved choices for small top-k workloads, small batches, and
large-batch streaming workloads.
* Added hardware-specific limits and selection rules for local-select
and leader-push strategies.
* **Bug Fixes**
* CUDA graph replay now preserves generator state and outputs without
dispatcher-level fill operations.
* **Documentation**
* Updated sampling policy documentation to reflect the revised launch
choices.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

<!-- cake-shared-references:start -->
## References

The shared reference corpus for CAKE kernel development includes the
following projects, documentation, and existing CAKE work:

- **GPU programming and instructions:** [NVIDIA CUDA Programming
Guide](https://docs.nvidia.com/cuda/cuda-programming-guide/index.html),
[NVIDIA PTX
ISA](https://docs.nvidia.com/cuda/parallel-thread-execution/), and
gau-nernst's [tcgen05 tutorial](https://gau-nernst.github.io/tcgen05/)
and [CUDA kernel examples](https://github.com/gau-nernst/learn-cuda).
- **Kernel programming libraries and compilers:** [NVIDIA CUTLASS /
CuTe](https://github.com/NVIDIA/cutlass),
[Triton](https://github.com/triton-lang/triton),
[TileLang](https://github.com/tile-ai/tilelang), [NVIDIA cuTile
Python](https://github.com/NVIDIA/cutile-python), and
[ThunderKittens](https://github.com/HazyResearch/ThunderKittens)
([ThunderKittens 2.0
techniques](https://hazyresearch.stanford.edu/blog/2026-02-19-tk-2)).
- **Attention and inference:** [FlashAttention (including Hopper and
CuTe implementations)](https://github.com/Dao-AILab/flash-attention),
[FlashInfer, including its TRT-LLM kernel
integration](https://github.com/flashinfer-ai/flashinfer), [Flash Linear
Attention](https://github.com/fla-org/flash-linear-attention),
[SageAttention](https://github.com/thu-ml/SageAttention),
[FlashAttention-FP4](https://github.com/hao-ai-lab/flash-attention-fp4),
and [FastVideo](https://github.com/hao-ai-lab/FastVideo).
- **GEMM and MoE:** [DeepGEMM](https://github.com/deepseek-ai/DeepGEMM),
[SonicMoE](https://github.com/Dao-AILab/sonic-moe),
[Alpha-MoE](https://github.com/Aleph-Alpha/Alpha-MoE), and [Mixture of
Kittens](https://github.com/cursor/mixture-of-kittens).
- **Clustering and nearest-neighbor kernels:** [Flash
K-Means](https://github.com/svg-project/flash-kmeans) and
[FlashLib](https://github.com/FlashML-org/flashlib).
- **Existing CAKE implementations and PRs:** [CAKE-generated kernel
progress tracker and PR index
(#4254)](https://github.com/flashinfer-ai/flashinfer/issues/4254).

These are corpus-level references. PR-specific implementation details,
changes, and benchmark references are documented above.
<!-- cake-shared-references:end -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [2fc43da](https://github.com/flashinfer-ai/flashinfer/commit/2fc43da123aa6cca812bd4260ac1bbaa7e6ef4e6)

- **作者**: eigen
- **时间**: 2026-10-08T07:59:28Z
- **提交信息**: feat(cake_dsa_indexer): round 3 generated programs -- SM100 wide-kind register split (232 math / 40 I/O per lane, host-dispatched), bitwise identical to round 2 on SM100 / SM103 / SM107; lean export (shared headers, lever table in tests, cached device queries), SASS unchanged (#6230)

**Context.** Original feature request: #5676 (DSA indexer and top-k with
deterministic selection semantics). This PR is the follow-up to #6056
(merged as be090a08): the `sm_100a` scan kernels are re-tuned (27-shape
acceptance set vs the merged kernels: median 4.3 % faster, up to 11.8 %
on the wide shapes, bit-identical outputs), the `sm_103a` / `sm_107a`
kernels are unchanged, and the export adopts the lean-export mechanical
tier of #5768 (shared device / host headers, lever table out of the
runtime module, cached device facts; SASS-identical cubins, 131 / 131
pairs). The export parity below covers B200, GB300 and R200 (153 / 153
rows).

## Generated-program export evidence

Baseline: **Cake production operator dsa_indexer_topk (scan [+ merge] +
finalize)** at Cake revision `f07b46e2b1ec8e112a4d746c4fedd68e8b7d7995`.

## Hardware stages

- `sm_100a` / world size `1`: GPUs `NVIDIA B200`, capabilities `10.0`,
drivers `580.82.07`, UUIDs `GPU-a038936f-3803-7fc3-f931-0125688e1d6e`;
51 shapes (named in the per-shape tables below).
- `sm_103a` / world size `1`: GPUs `NVIDIA GB300`, capabilities `10.3`,
drivers `580.159.03`, UUIDs `GPU-9c5ed8dd-177b-a878-6eae-395474bbb0b5`;
25 shapes (named in the per-shape tables below).
- `sm_103a` / world size `1`: GPUs `NVIDIA GB300`, capabilities `10.3`,
drivers `580.159.03`, UUIDs `GPU-ce5f6369-0e70-a1d8-ec16-cb9c354eaf3c`;
26 shapes (named in the per-shape tables below).
- `sm_107a` / world size `1`: GPUs `NVIDIA Graphics Device`,
capabilities `10.7`, drivers `620.43`, UUIDs
`GPU-72a5a285-335f-55e2-ab45-bf890ae4c678`; 25 shapes (named in the
per-shape tables below).
- `sm_107a` / world size `1`: GPUs `NVIDIA Graphics Device`,
capabilities `10.7`, drivers `620.43`, UUIDs
`GPU-a1045000-d925-5769-9175-4b92d05ecd0e`; 26 shapes (named in the
per-shape tables below).

Target revision: `be090a089da387f666a60fe9580bc3eda361b015`.

Benchmark execution: `symmetric_external_cuda_graph` with 8
independently captured graph instances per arm, replayed round-robin; 3
counterbalanced groups, 2 warmup calls and 40 reportable calls per
arm/group (fixed counts; no sizing pilot).
Latency metric: CUPTI GPU span per sample, first compute-kernel start to
last compute-kernel end of one arm call (every kernel the call launches,
asynchronous copies excluded), after a cold-L2 flush before each
measured sample; the reported value is the per-arm median. Each row's
``sm_clock_mhz_range`` in the summary JSON is the SM clock range
observed while the row was timed (group-boundary probes and, in the
symmetric graph mode, every sampled warmup/measurement phase).
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
|P1__sm_100a|G0|R1|3.947161|3.940249|1.0018x|—|—|—|pass|
|P1_peaked__sm_100a|G0|R1|3.892902|3.901670|0.9978x|—|—|—|pass|
|P2__sm_100a|G0|R1|3.938968|3.937193|1.0005x|—|—|—|pass|
|P3__sm_100a|G0|R1|4.159149|4.157742|1.0003x|—|—|—|pass|
|S1__sm_100a|G0|R1|0.469487|0.469312|1.0004x|—|—|—|pass|
|S2__sm_100a|G0|R1|1.332302|1.331950|1.0003x|—|—|—|pass|
|S3__sm_100a|G0|R1|4.525421|4.527453|0.9996x|—|—|—|pass|
|S4__sm_100a|G0|R1|16.966603|16.965806|1.0000x|—|—|—|pass|
|S5__sm_100a|G0|R1|60.920094|60.570019|1.0058x|—|—|—|pass|
|S6__sm_100a|G0|R1|232.842782|232.880275|0.9998x|—|—|—|pass|
|S7__sm_100a|G0|R1|937.419788|937.281018|1.0001x|—|—|—|pass|
|S8__sm_100a|G0|R1|3970.990720|3973.870910|0.9993x|—|—|—|pass|
|S4_peaked__sm_100a|G0|R1|17.055260|17.073149|0.9990x|—|—|—|pass|
|C1__sm_100a|G0|R1|1.902483|1.902803|0.9998x|—|—|—|pass|
|C2__sm_100a|G0|R1|3.889830|3.891478|0.9996x|—|—|—|pass|
|C3__sm_100a|G0|R1|3.970151|3.972423|0.9994x|—|—|—|pass|
|V1__sm_100a|G0|R1|9.465903|9.504528|0.9959x|—|—|—|pass|
|V2__sm_100a|G0|R1|15.031960|15.082200|0.9967x|—|—|—|pass|
|V3__sm_100a|G0|R1|18.562496|18.617408|0.9971x|—|—|—|pass|
|RC1__sm_100a|G0|R1|6.604875|6.547403|1.0088x|—|—|—|pass|
|RC2__sm_100a|G0|R1|13.430054|13.426263|1.0003x|—|—|—|pass|
|RC3__sm_100a|G0|R1|26.880021|26.822244|1.0022x|—|—|—|pass|
|RC4__sm_100a|G0|R1|54.223862|54.100327|1.0023x|—|—|—|pass|
|LT_cp32k_1m__sm_100a|G0|R1|224.893058|225.025767|0.9994x|—|—|—|pass|
|LT_pack8x4k__sm_100a|G0|R1|1.094594|1.094514|1.0001x|—|—|—|pass|
|LT_r4_64k__sm_100a|G0|R1|5.413304|5.403816|1.0018x|—|—|—|pass|
|LT_64q_1m__sm_100a|G0|R1|0.530113|0.530304|0.9996x|—|—|—|pass|
|exact_distinct__sm_100a|G0|R1|0.321121|0.321425|0.9991x|—|—|—|pass|
|exact_cutoff_ties__sm_100a|G0|R1|0.353264|0.353345|0.9998x|—|—|—|pass|
|exact_all_equal__sm_100a|G0|R1|0.526913|0.527105|0.9996x|—|—|—|pass|
|exact_signed_zeros__sm_100a|G0|R1|0.516704|0.516625|1.0002x|—|—|—|pass|
|exact_negative__sm_100a|G0|R1|0.345328|0.345521|0.9994x|—|—|—|pass|

|exact_few_winners_large_tie__sm_100a|G0|R1|0.524929|0.524913|1.0000x|—|—|—|pass|

|packed_equal_lengths__sm_100a|G0|R1|0.609953|0.610625|0.9989x|—|—|—|pass|

|packed_unequal_lengths__sm_100a|G0|R1|0.612833|0.613762|0.9985x|—|—|—|pass|

|packed_positive_offsets__sm_100a|G0|R1|0.599393|0.599169|1.0004x|—|—|—|pass|

|packed_negative_offsets__sm_100a|G0|R1|0.599937|0.599792|1.0002x|—|—|—|pass|
|packed_ratio2__sm_100a|G0|R1|0.621009|0.621105|0.9998x|—|—|—|pass|

|packed_ratio2_offsets__sm_100a|G0|R1|0.616129|0.616369|0.9996x|—|—|—|pass|

|packed_empty_segments__sm_100a|G0|R1|0.610625|0.610817|0.9997x|—|—|—|pass|
|packed_singletons__sm_100a|G0|R1|0.582737|0.582337|1.0007x|—|—|—|pass|
|packed_short_rows__sm_100a|G0|R1|0.568849|0.569025|0.9997x|—|—|—|pass|
|packed_k1__sm_100a|G0|R1|0.569921|0.571009|0.9981x|—|—|—|pass|
|packed_k4096__sm_100a|G0|R1|0.895890|0.896001|0.9999x|—|—|—|pass|

|boundary_4097x4097_k2049__sm_100a|G0|R1|0.186464|0.186448|1.0001x|—|—|—|pass|

|boundary_1x4096_k4096__sm_100a|G0|R1|0.663745|0.663441|1.0005x|—|—|—|pass|

|boundary_4096x8192_k1__sm_100a|G0|R1|0.265568|0.265664|0.9996x|—|—|—|pass|

|boundary_2049x2049_k2048__sm_100a|G0|R1|0.064256|0.064432|0.9973x|—|—|—|pass|

|boundary_6018x11754_k1__sm_100a|G0|R1|0.500288|0.500304|1.0000x|—|—|—|pass|

|boundary_6018x11754_k1000__sm_100a|G0|R1|0.560736|0.560801|0.9999x|—|—|—|pass|
|strided_k_p1_16__sm_100a|G0|R1|0.070112|0.070080|1.0005x|—|—|—|pass|
|P1__sm_103a|G1|R2|3.437566|3.436478|1.0003x|—|—|—|pass|
|P1_peaked__sm_103a|G2|R2|3.446839|3.446871|1.0000x|—|—|—|pass|
|P2__sm_103a|G2|R2|3.423676|3.423127|1.0002x|—|—|—|pass|
|P3__sm_103a|G1|R2|3.702112|3.700096|1.0005x|—|—|—|pass|
|S1__sm_103a|G1|R2|0.416352|0.416352|1.0000x|—|—|—|pass|
|S2__sm_103a|G2|R2|1.238944|1.238528|1.0003x|—|—|—|pass|
|S3__sm_103a|G1|R2|3.894624|3.894832|0.9999x|—|—|—|pass|
|S4__sm_103a|G2|R2|13.760128|13.744208|1.0012x|—|—|—|pass|
|S5__sm_103a|G1|R2|51.057488|51.039281|1.0004x|—|—|—|pass|
|S6__sm_103a|G2|R2|190.079441|190.026895|1.0003x|—|—|—|pass|
|S7__sm_103a|G1|R2|841.541262|841.379237|1.0002x|—|—|—|pass|
|S8__sm_103a|G2|R2|3448.960164|3447.457404|1.0004x|—|—|—|pass|
|S4_peaked__sm_103a|G2|R2|13.763744|13.730720|1.0024x|—|—|—|pass|
|C1__sm_103a|G1|R2|1.623072|1.622768|1.0002x|—|—|—|pass|
|C2__sm_103a|G2|R2|3.029072|3.029744|0.9998x|—|—|—|pass|
|C3__sm_103a|G1|R2|3.304224|3.304480|0.9999x|—|—|—|pass|
|V1__sm_103a|G2|R2|7.688928|7.692704|0.9995x|—|—|—|pass|
|V2__sm_103a|G1|R2|13.737248|13.752352|0.9989x|—|—|—|pass|
|V3__sm_103a|G2|R2|14.815488|14.800672|1.0010x|—|—|—|pass|
|RC1__sm_103a|G1|R2|5.723088|5.723632|0.9999x|—|—|—|pass|
|RC2__sm_103a|G2|R2|12.674193|12.543775|1.0104x|—|—|—|pass|
|RC3__sm_103a|G1|R2|25.475856|25.485664|0.9996x|—|—|—|pass|
|RC4__sm_103a|G2|R2|50.354703|50.418672|0.9987x|—|—|—|pass|
|LT_cp32k_1m__sm_103a|G1|R2|202.944609|203.417680|0.9977x|—|—|—|pass|
|LT_pack8x4k__sm_103a|G1|R2|1.014096|1.013968|1.0001x|—|—|—|pass|
|LT_r4_64k__sm_103a|G2|R2|4.735632|4.735536|1.0000x|—|—|—|pass|
|LT_64q_1m__sm_103a|G2|R2|0.461888|0.461744|1.0003x|—|—|—|pass|
|exact_distinct__sm_103a|G1|R2|0.297808|0.297712|1.0003x|—|—|—|pass|
|exact_cutoff_ties__sm_103a|G1|R2|0.325552|0.325344|1.0006x|—|—|—|pass|
|exact_all_equal__sm_103a|G1|R2|0.482912|0.482992|0.9998x|—|—|—|pass|
|exact_signed_zeros__sm_103a|G1|R2|0.476704|0.476720|1.0000x|—|—|—|pass|
|exact_negative__sm_103a|G1|R2|0.320192|0.320448|0.9992x|—|—|—|pass|

|exact_few_winners_large_tie__sm_103a|G1|R2|0.480896|0.481184|0.9994x|—|—|—|pass|

|packed_equal_lengths__sm_103a|G2|R2|0.556224|0.555776|1.0008x|—|—|—|pass|

|packed_unequal_lengths__sm_103a|G2|R2|0.546592|0.546272|1.0006x|—|—|—|pass|

|packed_positive_offsets__sm_103a|G2|R2|0.544400|0.544192|1.0004x|—|—|—|pass|

|packed_negative_offsets__sm_103a|G2|R2|0.544448|0.544064|1.0007x|—|—|—|pass|
|packed_ratio2__sm_103a|G2|R2|0.561696|0.560752|1.0017x|—|—|—|pass|

|packed_ratio2_offsets__sm_103a|G2|R2|0.556864|0.556864|1.0000x|—|—|—|pass|

|packed_empty_segments__sm_103a|G2|R2|0.563888|0.564256|0.9993x|—|—|—|pass|
|packed_singletons__sm_103a|G2|R2|0.552768|0.552976|0.9996x|—|—|—|pass|
|packed_short_rows__sm_103a|G1|R2|0.561264|0.561216|1.0001x|—|—|—|pass|
|packed_k1__sm_103a|G1|R2|0.518704|0.518864|0.9997x|—|—|—|pass|
|packed_k4096__sm_103a|G1|R2|0.776736|0.776752|1.0000x|—|—|—|pass|

|boundary_4097x4097_k2049__sm_103a|G1|R2|0.167680|0.167760|0.9995x|—|—|—|pass|

|boundary_1x4096_k4096__sm_103a|G2|R2|0.615312|0.615584|0.9996x|—|—|—|pass|

|boundary_4096x8192_k1__sm_103a|G1|R2|0.239952|0.240176|0.9991x|—|—|—|pass|

|boundary_2049x2049_k2048__sm_103a|G2|R2|0.058592|0.058672|0.9986x|—|—|—|pass|

|boundary_6018x11754_k1__sm_103a|G1|R2|0.427888|0.427584|1.0007x|—|—|—|pass|

|boundary_6018x11754_k1000__sm_103a|G2|R2|0.521664|0.521808|0.9997x|—|—|—|pass|
|strided_k_p1_16__sm_103a|G2|R2|0.065632|0.065728|0.9985x|—|—|—|pass|
|P1__sm_107a|G3|R3|2.163506|2.163234|1.0001x|—|—|—|pass|
|P1_peaked__sm_107a|G4|R3|2.174951|2.175641|0.9997x|—|—|—|pass|
|P2__sm_107a|G4|R3|2.163687|2.163959|0.9999x|—|—|—|pass|
|P3__sm_107a|G3|R3|2.318948|2.318868|1.0000x|—|—|—|pass|
|S1__sm_107a|G3|R3|0.238114|0.238338|0.9991x|—|—|—|pass|
|S2__sm_107a|G4|R3|0.683112|0.683128|1.0000x|—|—|—|pass|
|S3__sm_107a|G3|R3|2.243524|2.243620|1.0000x|—|—|—|pass|
|S4__sm_107a|G4|R3|7.648565|7.645157|1.0004x|—|—|—|pass|
|S5__sm_107a|G3|R3|29.076491|29.058267|1.0006x|—|—|—|pass|
|S6__sm_107a|G4|R3|113.175390|113.292806|0.9990x|—|—|—|pass|
|S7__sm_107a|G3|R3|463.990837|464.991109|0.9978x|—|—|—|pass|
|S8__sm_107a|G4|R3|1897.852094|1898.094822|0.9999x|—|—|—|pass|
|S4_peaked__sm_107a|G4|R3|7.711457|7.718561|0.9991x|—|—|—|pass|
|C1__sm_107a|G3|R3|1.015068|1.014828|1.0002x|—|—|—|pass|
|C2__sm_107a|G4|R3|1.839939|1.839155|1.0004x|—|—|—|pass|
|C3__sm_107a|G3|R3|1.937590|1.938630|0.9995x|—|—|—|pass|
|V1__sm_107a|G4|R3|4.437954|4.437346|1.0001x|—|—|—|pass|
|V2__sm_107a|G3|R3|7.010933|7.011268|1.0000x|—|—|—|pass|
|V3__sm_107a|G4|R3|8.552471|8.525095|1.0032x|—|—|—|pass|
|RC1__sm_107a|G3|R3|3.293464|3.294456|0.9997x|—|—|—|pass|
|RC2__sm_107a|G4|R3|6.523508|6.533587|0.9985x|—|—|—|pass|
|RC3__sm_107a|G3|R3|13.624116|13.617349|1.0005x|—|—|—|pass|
|RC4__sm_107a|G4|R3|27.050984|26.960925|1.0033x|—|—|—|pass|
|LT_cp32k_1m__sm_107a|G3|R3|111.896372|111.869408|1.0002x|—|—|—|pass|
|LT_pack8x4k__sm_107a|G3|R3|0.604872|0.604728|1.0002x|—|—|—|pass|
|LT_r4_64k__sm_107a|G4|R3|2.727839|2.727919|1.0000x|—|—|—|pass|
|LT_64q_1m__sm_107a|G4|R3|0.291237|0.290933|1.0010x|—|—|—|pass|
|exact_distinct__sm_107a|G3|R3|0.178867|0.179027|0.9991x|—|—|—|pass|
|exact_cutoff_ties__sm_107a|G3|R3|0.222147|0.222147|1.0000x|—|—|—|pass|
|exact_all_equal__sm_107a|G3|R3|0.248211|0.248451|0.9990x|—|—|—|pass|
|exact_signed_zeros__sm_107a|G3|R3|0.249923|0.250179|0.9990x|—|—|—|pass|
|exact_negative__sm_107a|G3|R3|0.226594|0.226579|1.0001x|—|—|—|pass|

|exact_few_winners_large_tie__sm_107a|G3|R3|0.248147|0.248259|0.9995x|—|—|—|pass|

|packed_equal_lengths__sm_107a|G4|R3|0.308885|0.308821|1.0002x|—|—|—|pass|

|packed_unequal_lengths__sm_107a|G4|R3|0.305877|0.305877|1.0000x|—|—|—|pass|

|packed_positive_offsets__sm_107a|G4|R3|0.301829|0.301765|1.0002x|—|—|—|pass|

|packed_negative_offsets__sm_107a|G4|R3|0.302740|0.303013|0.9991x|—|—|—|pass|
|packed_ratio2__sm_107a|G4|R3|0.312341|0.311973|1.0012x|—|—|—|pass|

|packed_ratio2_offsets__sm_107a|G4|R3|0.311589|0.311557|1.0001x|—|—|—|pass|

|packed_empty_segments__sm_107a|G4|R3|0.299716|0.300117|0.9987x|—|—|—|pass|
|packed_singletons__sm_107a|G4|R3|0.296229|0.296100|1.0004x|—|—|—|pass|
|packed_short_rows__sm_107a|G3|R3|0.317620|0.317924|0.9990x|—|—|—|pass|
|packed_k1__sm_107a|G3|R3|0.285636|0.285587|1.0002x|—|—|—|pass|
|packed_k4096__sm_107a|G3|R3|0.530838|0.531095|0.9995x|—|—|—|pass|

|boundary_4097x4097_k2049__sm_107a|G3|R3|0.107105|0.106929|1.0016x|—|—|—|pass|

|boundary_1x4096_k4096__sm_107a|G4|R3|0.536776|0.536873|0.9998x|—|—|—|pass|

|boundary_4096x8192_k1__sm_107a|G3|R3|0.138225|0.138354|0.9991x|—|—|—|pass|

|boundary_2049x2049_k2048__sm_107a|G4|R3|0.038241|0.038241|1.0000x|—|—|—|pass|

|boundary_6018x11754_k1__sm_107a|G3|R3|0.273091|0.273108|0.9999x|—|—|—|pass|

|boundary_6018x11754_k1000__sm_107a|G4|R3|0.374556|0.374444|1.0003x|—|—|—|pass|
|strided_k_p1_16__sm_107a|G4|R3|0.037552|0.037600|0.9987x|—|—|—|pass|

## Route legend

|Key|Route|
|---|---|
|R1|dsa_indexer_topk_sm_100a|
|R2|dsa_indexer_topk_sm_103a|
|R3|dsa_indexer_topk_sm_107a|

## Baseline legend

Each shape row above inlines its applicable external baselines (paired
export ms is the shape's Export ms column); keys resolve here.

|Key|Baseline|Label|Rows|Gate|
|---|---|---|---:|---|

## Geomeans over all correct timed rows

Gate-failing performance rows remain in these geomeans; only rows
without valid correctness and timing are excluded and remain visible
above.

|Shape tag|Timed rows|Denominator|Source ms|Export ms|Source / Export|
|---|---:|---:|---:|---:|---:|
|all|153|153|1.907766|1.907690|1.000040x|
|coverage|72|72|0.337309|0.337383|0.999781x|
|perf|81|81|8.900432|8.898026|1.000270x|

Complete denominator: **true** (153/153).

All gates passed: **true** (153/153).


🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Performance**
* Improved Cake DSA indexer performance for select GPU architectures and
workloads, including updated tile processing and candidate selection.
* Reduced repeated device-property lookups by reusing cached device
information.
* **Bug Fixes**
  * Explicit non-CUDA devices are now rejected when CUDA is available.
* **Documentation**
  * Clarified device dispatch and package layout details.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <root@hecate0360.hecate.clusters.nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-10-09
**监控日期**: 2026-10-08
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4572
- **最后更新**: 2026-10-08T19:07:10Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-10-09
**监控日期**: 2026-10-08
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34695
- **最后更新**: 2026-10-08T21:13:35Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Patrick Ribbsaeter

## AI分析总结

## 1. 主要更新类型
**Bug 修复 + 测试重构**。属于接口一致性（API 契约）层面的修补，而非新增能力或性能优化。

## 2. 关键变更点及与项目方向的关系
- `InpaintProcessor.preprocess` 在 `mask=None` 分支原先返回值结构与其它分支不一致，现在统一返回 `(image, None, postprocessing_kwargs)` 三元组，恢复并锁定**3 元组返回契约**。
- 配套地把分散的单测**整合为参数化测试**，统一覆盖「有 mask」「无 mask」「crop 配置」三类场景，提升测试的覆盖密度与可维护性。
- 与项目整体方向的关系：Diffusers 正在推进图像处理器（`image_processor`）的模块化与统一化，让 `ImageProcessor` / `InpaintProcessor` 等在各 Pipeline（inpainting、SD、SDXL、video 等）间**可互换、行为可预测**。这种返回签名的跨分支一致性，是保证不同 Pipeline 与下游封装能稳定调用处理器的前提。

## 3. 对项目的影响和潜在意义
- **正面**：修复了下游代码在无 mask 场景下可能出现的解包错误（如 `TypeError: cannot unpack non-iterable`），提高了健壮性；契约固定后，第三方基于该 API 二次开发的代码可长期保持兼容。
- **风险与兼容**：严格来说这是**行为变更**——原先 `mask=None` 时的返回结构被改变，依赖旧结构（例如返回 2 元组或 `None` 之外的占位）的外部调用方需要适配。项目选择在补丁层面直接修正，说明团队将其判定为「符合文档预期的正确行为」而非 breaking change。
- 对用户体验：修 bug 后 inpaint 预处理路径的代码分支更少、更易推理，排查问题成本下降。

## 4. 值得关注的技术点
- **返回契约作为隐式 API**：函数的 tuple 形状本质上是接口的一部分，尤其在 Python 这类弱类型语言中，靠测试与约定而非类型系统保障。此次修复值得思考是否进一步用 `typing.NamedTuple` / `dataclass` / `TypedDict` 把契约显式化，从根上杜绝分支间不一致。
- **参数化测试的范式价值**：用 pytest 参数化把三种配置收敛到单一测试入口，既减少重复代码，又让「新增配置需同步新增测试」变成自然约束，是该仓库测试风格的示范。
- **PR 双编号**：提交信息中同时出现 #14481 与 #14470，可能是同一修复的重开/迁移或 issue 关联，提示维护者在协作流程上存在小幅重复工单，值得关注社区贡献流程是否顺畅。
- 从提交前缀 `fix(image_processor):` 可见项目遵循 Conventional Commits，便于自动化生成 changelog。

## 5. 基于项目背景对发展的评估
HuggingFace Diffusers 是扩散模型推理与训练的核心基础设施库，其竞争力在于**接口稳定性 + Pipeline 生态丰富度**。此次提交虽小，却指向两个对长期发展关键的维度：一是把 `image_processor` 这类底层组件的**契约收紧**，为后续更多 inpainting 模型（视频 inpaint、可控生成等）铺平复用路径；二是通过测试参数化积累可扩展的验证资产，降低大规模 Pipeline 矩阵的回归成本。总体上，这属于「打地基」型维护工作——单次收益有限，但累积起来决定了库能否在快速迭代中保持向后兼容与可信度，对项目走向成熟稳定至关重要。

## 详细提交记录

### [d961a38](https://github.com/huggingface/diffusers/commit/d961a388fd02e4db38d17350c8dd9b8abe642e05)

- **作者**: Patrick Ribbsaeter
- **时间**: 2026-10-08T08:24:47Z
- **提交信息**: fix(image_processor): maintain 3-tuple return contract in InpaintProcessor.preprocess when mask is None (#14481)

fix(image_processor): preserve 3-tuple return contract when mask is None (#14470)

Ensure InpaintProcessor.preprocess returns (image, None, postprocessing_kwargs) when mask is None, preserving the expected 3-tuple return contract and signature consistency across all preprocess branches. Consolidate unit tests into a parameterized test covering with-mask, without-mask, and crop configurations.

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-10-09
**监控日期**: 2026-10-08
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


**报告日期**: 2026-10-09
**监控日期**: 2026-10-08
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13212
- **最后更新**: 2026-10-08T14:31:42Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Jinyan Ye

## AI分析总结

## 提交分析：[ee631d4] Add Qwen-Image-2.1-Fun-Controlnet-Union (#1730)

### 1. 主要更新类型
**功能新增（模型/架构支持）**。该提交为项目接入了新的模型组件——Qwen-Image-2.1-Fun-Controlnet-Union，属于典型的模型能力扩展，而非修复或重构类变更。

### 2. 关键变更点及与项目方向的关系
- **新模型接入**：从命名看，该组件结合了 Qwen-Image 2.1（通义千问图像生成模型的迭代版本）、"Fun" 系列（通常指面向可控生成的微调/扩展模型线）与 ControlNet-Union（多条件控制网络的融合形式），意味着 DiffSynth-Studio 进一步扩展了对 Qwen 图像生态和可控生成技术的支持。
- **与项目方向的高度一致性**：DiffSynth-Studio 的核心定位是提供统一的扩散模型训练与推理工作台，覆盖图像、视频的可控生成。本次提交延续了"持续跟踪并集成前沿开源模型"的路线，尤其是对 ControlNet 类可控生成范式的覆盖，正是该仓库相对同类工具库的差异化优势之一。
- **Union 的意义**：ControlNet-Union 形式通常将多种空间/结构控制条件（如深度、边缘、姿态等）合并进一个网络，减少多 ControlNet 堆叠带来的显存与调度开销，契合 DiffSynth 强调"显存高效"（Memory-Efficient）的设计理念。

### 3. 对项目的影响和潜在意义
- **用户价值**：用户可在 DiffSynth 的统一接口下使用基于 Qwen-Image 2.1 的多条件可控生成，降低切换不同控制模型的适配成本。
- **生态卡位**：Qwen-Image 系列在国内开源社区影响力较大，及时跟进 Fun-Controlnet-Union 有助于保持项目在开源图像生成工具链中的活跃度与竞争力，也与 README 中体现的 Trendshift 热榜曝光形成正向循环。
- **潜在影响面**：此类提交通常会涉及模型配置文件、权重加载逻辑、示例脚本与文档，若权重发布同步到位，将直接提升项目的可用版本数。

### 4. 值得关注的技术点
- **多条件控制的融合机制**：Union 结构如何组织不同控制信号的注入方式（共享/独立编码器、条件类型嵌入等），值得关注其与 DiffSynth 现有 pipeline 的对接细节。
- **与 Qwen-Image 2.1 基座的兼容性**：2.1 版本相对前代在分辨率、文本对齐上的变化，是否影响 ControlNet 分支的训练目标与推理调度。
- **显存与推理效率**：Union 单网络替代多 ControlNet 后，在 DiffSynth 的量化/卸载优化下能否进一步降低消费级显卡的门槛。
- **训练支持**：若该提交附带了微调脚本，则意味着用户可自定义 Union 模型的控制条件，扩展性显著增强。

### 5. 基于项目背景的发展影响
DiffSynth-Studio 以"覆盖最广泛的扩散模型训练/推理 + 显存高效优化"为核心叙事，本次提交正是这一叙事的直接体现：通过持续、快速地吸收 Qwen 生态与 ControlNet 前沿变体，项目强化了其作为"前沿模型统一接入层"的定位。这类增量式模型支持提交累积起来，构成了仓库社区活跃度和采用率的基础，也为其向视频可控生成、更复杂多模态控制方向演进提供了架构上的先例与复用路径。总体而言，这是一次巩固核心竞争力、紧贴开源社区节奏的健康发展信号。

## 详细提交记录

### [ee631d4](https://github.com/modelscope/DiffSynth-Studio/commit/ee631d4907d8d6fc3d39063a2a65c00a954c9bf5)

- **作者**: Jinyan Ye
- **时间**: 2026-10-08T07:29:59Z
- **提交信息**: Add Qwen-Image-2.1-Fun-Controlnet-Union (#1730)

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-10-09
**监控日期**: 2026-10-08
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 36893
- **最后更新**: 2026-10-09T01:58:46Z

## 提交统计

- **昨日提交总数**: 56
- **提交者数量**: 33
- **主要提交者**: Sage, Baizhou Zhang, billishyahao

## AI分析总结

## sglang 昨日提交分析（共56条）

### 1. 主要更新类型分布
- **性能优化**：占比最大（约30%），集中在 MoE、AMD/GB300 硬件加速和内存管理
- **Bug修复/健壮性**：KV缓存、缓冲区清理、调度器等底层稳定性修复
- **CI/测试改进**：约12条，优化测试触发条件、缓存管理与专用工作流
- **功能新增**：新模型支持（EmbeddingGemma 2、DFlash block验证等）、dLLM新算法
- **重构/文档**：diffusion 代码去重、cookbook长上下文配方

### 2. 关键变更点
- **统一内存池投机解码（unified-memory 系列，5条）**：将 draft 模型的 KV 融合进目标模型页式内存，翻译所有读写路径，支持 EAGLE/EAGLE3、DFLASH、DSPARK 等投机解码方案。这是最大的架构级演进。
- **DP attention 深化**：解码节点支持 DP attention、按 rank 统计注意力对与失衡指标、失衡比率监控，说明多 DP 扩展能力在成熟。
- **Qwen3.8 系列（GB300 长上下文 + CP 3/4 collocated prefill）**：针对新一代大模型的长上下文与上下文并行支持。
- **AMD 优化持续**：gfx950 上的 W8A8 FP8 GEMM、小型 MoE router 单次 launch、Kimi K3 aiter 汇编，显示 AMD 生态投入加大。
- **rust-server/processor 建设**：DeepSeek-V4 通过 sglang-processor 渲染、与 SGLang 对齐的 parity 校验框架、监听器预热，暗示 Rust 化服务端路线在推进。

### 3. 影响与意义
- **内存效率**：投机解码 KV 融合与 MemCache 接口简化（match_prefix/init_load_back 返回值精简）降低内存碎片和拷贝开销，直接提升吞吐。
- **可观测性**：DP attention 失衡指标、采样前 NaN 检测（opt-in），让大规模部署排障更容易。
- **可维护性**：大量 CI 瘦身（避免 HF API 调用、按条件触发、专用 processor 工作流）降低维护成本，对开源项目的贡献者体验是正向的。
- **PD 分离路径**：decode admission 按页取整计费、KV checksum 精简输入，说明 Prefill-Decode 分离部署在生产化打磨。

### 4. 值得关注的技术点
- **统一内存池 + 投机解码**的分层落地（机制→路径翻译→模型适配）是教科书式的渐进式合入，值得关注其后续对吞吐的实际影响。
- **Claude/Cursor 等 AI 代理出现在 Co-authored-by**，反映 AI 辅助开发已深度嵌入该仓库工作流。
- **DFlash 系列**（QKV hook 化、block 验证）作为投机解码新方案在快速发展。
- **NVFP4 量化**：ReLU2 激活的 per-token MoE 支持、与 FlashInfer cutlass FP4 路径的修复，说明 FP4 量化栈在打通。

### 5. 对项目发展的意义
结合 README 中"为 LLM 和多模态提供高速推理"的目标，本批提交体现三条主线：**（1）持续压榨硬件极限**——AMD/GB300/FP4 量化多路并进，扩大硬件覆盖；**（2）大模型适配前瞻**——Qwen3.8、DeepSeek-V4、MiniMax-M3 等旗舰模型的长上下文、DP attention、投机解码支持，保持对前沿模型的首发支持能力；**（3）工程化成熟**——统一内存池、PD 分离、Rust 服务端、CI 精简，都在为规模化生产部署铺路。整体上，项目正从"推理加速库"向"生产级推理系统"演进，这些提交强化了其在开源 LLM 推理引擎中的技术领先地位。

## 详细提交记录

### [2b94cb4](https://github.com/sgl-project/sglang/commit/2b94cb4eb5fbab75ace8eec410ea9bd45244912f)

- **作者**: Ankur Singh
- **时间**: 2026-10-08T23:56:30Z
- **提交信息**: docs(cookbook): add Qwen3.8 GB300 long-context recipe (#43159)

Signed-off-by: Ankur-singh <ankusingh@nvidia.com>

### [bb43927](https://github.com/sgl-project/sglang/commit/bb43927404076b2935473eb09bc07f07543957fb)

- **作者**: metamergebot
- **时间**: 2026-10-08T23:48:31Z
- **提交信息**: [PD] Charge decode admission the page-rounded allocation when the radix cache is disabled (#43173)

Co-authored-by: hanming-lu <69857889+hanming-lu@users.noreply.github.com>
Co-authored-by: xiezhq-hermann <xiezhq-hermann@users.noreply.github.com>

### [2e64740](https://github.com/sgl-project/sglang/commit/2e647404423ccf50c431eed67afc224e32d3c41b)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-08T23:27:31Z
- **提交信息**: [CI] Avoid Hugging Face Hub API calls when the local model cache is complete (#43229)

### [baee5f3](https://github.com/sgl-project/sglang/commit/baee5f3b62e2ada15b30346a022a41e230c462a8)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-08T23:25:50Z
- **提交信息**: [CI] Drop the `labeled` trigger from the extra CI workflows (#43234)

### [ae4da8c](https://github.com/sgl-project/sglang/commit/ae4da8cd78472d6906e259ce3776f23013328686)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-08T23:19:35Z
- **提交信息**: [MemCache] Skip SWA request-cap pool sizing when chunked prefill is off (#43203)

### [71584b6](https://github.com/sgl-project/sglang/commit/71584b62c0f6c9f1a8dbad1b0a9191f775c0bcd8)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-08T22:51:39Z
- **提交信息**: [CI] Fix stale fakes in the NVFP4 MoE dispatch and CP strategy unit tests (#43226)

### [20bf93b](https://github.com/sgl-project/sglang/commit/20bf93b6bfccc684fea681486b6ad5746f2abb81)

- **作者**: metamergebot
- **时间**: 2026-10-08T22:24:38Z
- **提交信息**: [metrics] Call DPBalanceStats.create by keyword in the ratio ladder test (#43218)

Co-authored-by: Hanming Lu <69857889+hanming-lu@users.noreply.github.com>
Co-authored-by: hanming-lu <hanming-lu@users.noreply.github.com>

### [2abb761](https://github.com/sgl-project/sglang/commit/2abb761639d39fedf40b187ec5ff676cbce36e6c)

- **作者**: metamergebot
- **时间**: 2026-10-08T22:01:37Z
- **提交信息**: [metrics] Count per-rank DP attention pairs and their imbalance (#43180)

Co-authored-by: Hanming Lu <69857889+hanming-lu@users.noreply.github.com>
Co-authored-by: hanming-lu <hanming-lu@users.noreply.github.com>

### [0b658c1](https://github.com/sgl-project/sglang/commit/0b658c12ff1930d0fe75909fe68f6efda449f31d)

- **作者**: metamergebot
- **时间**: 2026-10-08T22:01:16Z
- **提交信息**: [Bench][MoE] Deal the simulated round-robin experts evenly across EP ranks (#43188)

Co-authored-by: Hanming Lu <69857889+hanming-lu@users.noreply.github.com>

### [b0e0635](https://github.com/sgl-project/sglang/commit/b0e06359acf94dc7ffb9cd1b8045604ee8a132b5)

- **作者**: Siyuan Chen
- **时间**: 2026-10-08T21:42:16Z
- **提交信息**: [DSV4.1][PD][5/N] Decode node support DP attention (#40177)

### [d20bdc1](https://github.com/sgl-project/sglang/commit/d20bdc1443c535996ca7a47d8e34df12882af5e6)

- **作者**: Xuanteng Huang
- **时间**: 2026-10-08T21:28:22Z
- **提交信息**: Add per-token NVFP4 MoE support for ReLU2 activation (#39199)

Signed-off-by: Xuanteng Huang <xuanteng.huang@outlook.com>

### [3d8d44a](https://github.com/sgl-project/sglang/commit/3d8d44a4a9f52c9d59bd88617848f031329ab76a)

- **作者**: Shunkangz
- **时间**: 2026-10-08T21:20:27Z
- **提交信息**: [Qwen3.8 CP 3/4] Collocated prefill CP integration (#39723)

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [5a5ea81](https://github.com/sgl-project/sglang/commit/5a5ea81036c13c8f812df3817c679fe3f0b9afb2)

- **作者**: Sage
- **时间**: 2026-10-08T21:09:46Z
- **提交信息**: [rust-server] warm up each rust listener in-process (#43004)

Signed-off-by: Sage Ahrac <sagiahrak@gmail.com>

### [e902207](https://github.com/sgl-project/sglang/commit/e902207a4e65f80da20046c52567eb923cb8ccce)

- **作者**: maocheng23
- **时间**: 2026-10-08T20:59:52Z
- **提交信息**: [Speculative] Support block verification for the DFlash family (#43012)

Co-authored-by: maocheng <mao.cheng@MacBook-Pro-MD663G60VV.local>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [d1ba943](https://github.com/sgl-project/sglang/commit/d1ba943016cb93fe874b924bbd293214ff086413)

- **作者**: Yihao Wang
- **时间**: 2026-10-08T20:54:45Z
- **提交信息**: [Model] Add support for EmbeddingGemma 2 (#42782)

Signed-off-by: Luciano Martins <lucianommartins@users.noreply.github.com>
Co-authored-by: Luciano Martins <lucianommartins@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [b193ef3](https://github.com/sgl-project/sglang/commit/b193ef382a23ccaf2ed79cc735c7da4e1fff3c0c)

- **作者**: Baizhou Zhang
- **时间**: 2026-10-08T20:53:41Z
- **提交信息**: [CI] Clean some unnecessary DSV4 tests (#43195)

### [d8448d2](https://github.com/sgl-project/sglang/commit/d8448d2e6212920eb816390a37e7f8b40cbf0a3a)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-10-08T20:23:26Z
- **提交信息**: [CI] Re-enable GB300 (#43058)

Co-authored-by: Mohammad Angkad <mohammad.angkad@radixark.ai>

### [93f2acf](https://github.com/sgl-project/sglang/commit/93f2acf61487a401816a056675b7281864b8de85)

- **作者**: metamergebot
- **时间**: 2026-10-08T19:58:58Z
- **提交信息**: [Metrics] Use widely supported bucket boundaries for the DP attention imbalance ratio (#43187)

Co-authored-by: hanming-lu <hanming-lu@users.noreply.github.com>

### [3fef129](https://github.com/sgl-project/sglang/commit/3fef129ff8a32c32da5f6a0efd33485f6cc6233c)

- **作者**: Ming Yang
- **时间**: 2026-10-08T19:54:03Z
- **提交信息**: [PD] Allow state-only KV checksum inputs (#42904)

### [075fd8f](https://github.com/sgl-project/sglang/commit/075fd8fa0b1cef651ac22e1b50895d11ebcfbde9)

- **作者**: metamergebot
- **时间**: 2026-10-08T19:47:46Z
- **提交信息**: [Mamba] Describe the track snapshot dtype by its kernel instead of fp32 (#43192)

Co-authored-by: Hanming Lu <69857889+hanming-lu@users.noreply.github.com>
Co-authored-by: jiayisuse <jiayisuse@users.noreply.github.com>

### [e3c5719](https://github.com/sgl-project/sglang/commit/e3c5719713ff9dcaca97bb1941704eea680c6c37)

- **作者**: metamergebot
- **时间**: 2026-10-08T19:46:28Z
- **提交信息**: [DFlash] Build the attention QKV projection through an overridable hook (#43179)

Co-authored-by: Hanming Lu <69857889+hanming-lu@users.noreply.github.com>
Co-authored-by: 842974287 <842974287@users.noreply.github.com>

### [00b3a48](https://github.com/sgl-project/sglang/commit/00b3a487532112adc9c85e8b979c7d1b82608a45)

- **作者**: kunchengit
- **时间**: 2026-10-08T19:44:14Z
- **提交信息**: [dLLM] Add JointThresholdInDel algorithm for insertion & deletion decoding (#31773)

### [b2cb249](https://github.com/sgl-project/sglang/commit/b2cb24995d4adefb2628d73cbf9cf84dae896bc1)

- **作者**: Aurick Qiao
- **时间**: 2026-10-08T19:20:57Z
- **提交信息**: [Debug] Add opt-in NaN detection before sampling (#42690)

Co-authored-by: Qiaolin-Yu <liin1211@outlook.com>

### [393eaed](https://github.com/sgl-project/sglang/commit/393eaed5093ec106c43658257d08e59fa670ad28)

- **作者**: Shenxiu Liu
- **时间**: 2026-10-08T19:19:35Z
- **提交信息**: [Fix] overlap scheduler: record_stream mix_running_indices for the forward-stream relay gather (#34076)

Co-authored-by: Qiaolin-Yu <liin1211@outlook.com>

### [1638c5d](https://github.com/sgl-project/sglang/commit/1638c5d6999525a4ae705120a2ca92e6adf0264e)

- **作者**: shodoco
- **时间**: 2026-10-08T18:56:06Z
- **提交信息**: [http_server] Let custom /generate routes skip the second contract check (#43114)

### [2143478](https://github.com/sgl-project/sglang/commit/214347891a5c9153775a4393f5ec16a1f44b2d26)

- **作者**: Kaixi
- **时间**: 2026-10-08T18:01:27Z
- **提交信息**: [Bugfix] Skip post-experts EP all-reduce on the FlashInfer cutlass FP4 all-gather MoE path (#41072)

Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: Po-Han Huang (NVIDIA) <53919306+nvpohanh@users.noreply.github.com>

### [cbf4969](https://github.com/sgl-project/sglang/commit/cbf49695c38a4f074e6f51a046b269208faa742f)

- **作者**: Kan Wu
- **时间**: 2026-10-08T17:57:05Z
- **提交信息**: [CI] Add dedicated sglang-processor workflow (#43022)

Co-authored-by: Kan Wu <kan.wu@radixark.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [e2fbc6a](https://github.com/sgl-project/sglang/commit/e2fbc6a5508d4f0478578b20e67ccfdc63265d3c)

- **作者**: shodoco
- **时间**: 2026-10-08T17:12:37Z
- **提交信息**: Stream a chunk once stream_interval tokens are unsent (#42643)

### [344b8a8](https://github.com/sgl-project/sglang/commit/344b8a863b664c382813fa6c99121ab59cbec76f)

- **作者**: Eric Zhang
- **时间**: 2026-10-08T16:26:15Z
- **提交信息**: [Perf] Fuse short-convolution checkpoint tracking metadata (#43013)

### [642e81f](https://github.com/sgl-project/sglang/commit/642e81fbb8e91d30a970491e5193e07c166f2617)

- **作者**: Ke Bao
- **时间**: 2026-10-08T16:21:38Z
- **提交信息**: Fix DSA index host buffer cleanup (#43100)

### [46ad9eb](https://github.com/sgl-project/sglang/commit/46ad9eb43919e86d21bd24a5b6f76712c3219fb7)

- **作者**: Ke Bao
- **时间**: 2026-10-08T16:21:27Z
- **提交信息**: Fix K-only host buffer cleanup (#43101)

### [4ab4d90](https://github.com/sgl-project/sglang/commit/4ab4d90d789690cd4e67c41fbe2ae4036c05bceb)

- **作者**: billishyahao
- **时间**: 2026-10-08T16:13:03Z
- **提交信息**: [AMD][DCP 3/N] add aiter asm for kimi k3 target verify (#34537)

### [3030e31](https://github.com/sgl-project/sglang/commit/3030e31ff8f23939577353be31e72c8013c549e5)

- **作者**: Mick
- **时间**: 2026-10-08T15:44:35Z
- **提交信息**: [diffusion] refactor: deduplicate request extraction and ComfyUI test helpers (#42903)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [9f5d871](https://github.com/sgl-project/sglang/commit/9f5d8712514c2d9dd29c76c6080774db3fd50aa2)

- **作者**: 黄孝君
- **时间**: 2026-10-08T13:44:49Z
- **提交信息**: [NPU] Quote the arm64 Triton-ascend wheel URL in npu.Dockerfile (#43035)

### [943621c](https://github.com/sgl-project/sglang/commit/943621c3364de6948fc02ee13c55b4f1cdf97f3a)

- **作者**: Kan Wu
- **时间**: 2026-10-08T12:16:20Z
- **提交信息**: [sgl-router] Render DeepSeek-V4 through sglang-processor (#42665)

Co-authored-by: Kan Wu <kan.wu@radixark.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Shangming Cai <csmthu@gmail.com>

### [11b1fb2](https://github.com/sgl-project/sglang/commit/11b1fb21de1c48acee33c6f23a6fc57b1c322341)

- **作者**: Thanhhao
- **时间**: 2026-10-08T11:39:31Z
- **提交信息**: [MiniMax-M3] Decode: paged K/V tile loads and a tiny GEMM for the router projection (#38841)

Co-authored-by: Hao Phan <htphan@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [6e6ccb2](https://github.com/sgl-project/sglang/commit/6e6ccb26f265b3477ce89ca032cee8e7aeac0e17)

- **作者**: Thanhhao
- **时间**: 2026-10-08T11:33:17Z
- **提交信息**: [MiniMax-M3] Instantiate the decode block top-k in register buckets (#38615)

Co-authored-by: Hao Phan <htphan@nvidia.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>
Co-authored-by: Po-Han Huang (NVIDIA) <53919306+nvpohanh@users.noreply.github.com>

### [45abea0](https://github.com/sgl-project/sglang/commit/45abea0269c4fce45ae811aabacb5bdf2aacd355)

- **作者**: Kan Wu
- **时间**: 2026-10-08T10:35:30Z
- **提交信息**: [rust-processor] DeepSeek-V4 parity with SGLang, plus a reusable parity harness and skill (#42664)

Co-authored-by: Kan Wu <kan.wu@radixark.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [9578cb1](https://github.com/sgl-project/sglang/commit/9578cb1c63bbe3f92aa96467a406947403c24f37)

- **作者**: Shangming Cai
- **时间**: 2026-10-08T10:25:06Z
- **提交信息**: [CI] Don't run the full GPU suite for renderer-only Cargo.lock changes (#43025)

### [7dd512b](https://github.com/sgl-project/sglang/commit/7dd512b0e879710d1162d657b5eeea4bfd7a4e60)

- **作者**: Mick
- **时间**: 2026-10-08T10:18:39Z
- **提交信息**: [diffusion] refactor: deduplicate FLUX positions and RoPE application (#43002)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [8ad24fb](https://github.com/sgl-project/sglang/commit/8ad24fb560df0e95eb600cd3ce15754bdd1d5276)

- **作者**: Horace He
- **时间**: 2026-10-08T09:10:25Z
- **提交信息**: [Perf] Cache compiled ModelOpt exclusion patterns (#42927)

### [4b384df](https://github.com/sgl-project/sglang/commit/4b384df0c94dbd0fe30627c27c98c0441b4ebd96)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-08T08:17:31Z
- **提交信息**: [CI] Keep the KL tests' LongBench cache outside the checkout and bound its download (#43068)

### [7b9c42c](https://github.com/sgl-project/sglang/commit/7b9c42cf49e05d5507af28210b9f336bc0021250)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-08T08:16:39Z
- **提交信息**: [CI] Remove the unregistered chunked-prefill tests under test/manual (#43081)

### [89b5935](https://github.com/sgl-project/sglang/commit/89b5935793650b125b80576f744d9cad44b74383)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-08T08:14:33Z
- **提交信息**: [MemCache] Return only the loaded length from `init_load_back`; drop `empty_device_indices` (#43023)

### [5a4d01a](https://github.com/sgl-project/sglang/commit/5a4d01a3ae631ff77ffc393655b0bb71e86bd38f)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-08T08:10:14Z
- **提交信息**: [MemCache] Return only the matched length from `match_prefix`; read KV indices off the node path (#42923)

### [2d26823](https://github.com/sgl-project/sglang/commit/2d26823f9412f3fab4ca15d444118e1c9409da57)

- **作者**: Spandan Tiwari
- **时间**: 2026-10-08T08:06:34Z
- **提交信息**: [AMD] Drop static input_scale on aiter per-token FP8 path (use dynamic per-token) (#42152)

### [b3e6c87](https://github.com/sgl-project/sglang/commit/b3e6c87be3516f83eaa4bb340bb30dab625d46b1)

- **作者**: Cheng Wan
- **时间**: 2026-10-08T07:58:28Z
- **提交信息**: [Refactor] Translate each KV loc once per iteration (#42753)

### [508ddc8](https://github.com/sgl-project/sglang/commit/508ddc859a1342bcfa4c400b9bf124892781c796)

- **作者**: caihuali95
- **时间**: 2026-10-08T07:56:21Z
- **提交信息**: [unified-memory] Admit DFLASH and DSPARK with fused draft KV (#40492)

Co-authored-by: Caihua Li <caihua.li@bytedance.com>
Co-authored-by: Cheng Wan <cheng.wan@radixark.ai>

### [c2d491e](https://github.com/sgl-project/sglang/commit/c2d491e38bbeab0d6cc14f3958f5b06f7c2e9aea)

- **作者**: caihuali95
- **时间**: 2026-10-08T07:55:54Z
- **提交信息**: [unified-memory] Admit EAGLE/EAGLE3 onto fused draft KV, on mamba-MHA and MLA hosts (#40491)

Co-authored-by: Caihua Li <caihua.li@bytedance.com>
Co-authored-by: Cheng Wan <cheng.wan@radixark.ai>

### [5afe4d6](https://github.com/sgl-project/sglang/commit/5afe4d63346b12c397a9f1354d0d2705e73e1a1c)

- **作者**: Michael
- **时间**: 2026-10-08T07:54:26Z
- **提交信息**: [AMD] Fix DSpark draft bucket tests for the raw in-graph metadata default (#42230)

### [8b80808](https://github.com/sgl-project/sglang/commit/8b80808366bb9ea476b1b2d0be09aa36b7fb6cd2)

- **作者**: caihuali95
- **时间**: 2026-10-08T07:54:19Z
- **提交信息**: [unified-memory] Fuse the draft model's KV into the target's page envelope (mechanism) (#37628)

Co-authored-by: Caihua Li <caihua.li@bytedance.com>
Co-authored-by: Cheng Wan <cheng.wan@radixark.ai>

### [08d30f2](https://github.com/sgl-project/sglang/commit/08d30f230066afec39295f49edf9b317879a9d70)

- **作者**: caihuali95
- **时间**: 2026-10-08T07:52:21Z
- **提交信息**: [unified-memory] Speculative decoding on the unified memory pool: translate every read and write path (#37627)

Co-authored-by: Caihua Li <caihua.li@bytedance.com>
Co-authored-by: Cheng Wan <cheng.wan@radixark.ai>

### [33883a5](https://github.com/sgl-project/sglang/commit/33883a5fa3c34907e2cc315f3db39d6eb80c84db)

- **作者**: chuyeh
- **时间**: 2026-10-08T07:50:16Z
- **提交信息**: [AMD] Small-M W8A8 FP8 projection GEMM for Qwen3.5 AttnFP8 on gfx950 (#41134)

Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: jacky.cheng <yichiche@amd.com>

### [b2cd65b](https://github.com/sgl-project/sglang/commit/b2cd65b8b0d15116e822371892af02977e26dc99)

- **作者**: chuyeh
- **时间**: 2026-10-08T07:47:52Z
- **提交信息**: [AMD] One-launch small-M MoE router for Qwen3.5 on gfx950 (#41133)

Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: jacky.cheng <yichiche@amd.com>

### [f795fe3](https://github.com/sgl-project/sglang/commit/f795fe352d55e0924f5d7bc099f36e47d715c56f)

- **作者**: Martin Hickey
- **时间**: 2026-10-08T07:37:22Z
- **提交信息**: [Test] Add a docs drift check for server_arguments.mdx (#38520)

Signed-off-by: Martin Hickey <martin.hickey@ie.ibm.com>
Co-authored-by: Cheng Wan <54331508+ch-wan@users.noreply.github.com>
Co-authored-by: Cheng Wan <cheng.wan@radixark.ai>

### [785005d](https://github.com/sgl-project/sglang/commit/785005d21b654857bf83736d40be446804ee6332)

- **作者**: Chunan Zeng
- **时间**: 2026-10-08T07:16:54Z
- **提交信息**: [DSpark] Mask uncommitted slots before commit-inject cache lookups (#42624)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-10-09
**监控日期**: 2026-10-08
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1289
- **最后更新**: 2026-10-07T00:36:25Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-10-09
**监控日期**: 2026-10-08
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 93416
- **最后更新**: 2026-10-09T01:57:42Z

## 提交统计

- **昨日提交总数**: 63
- **提交者数量**: 54
- **主要提交者**: Doug Smith, Alberto Massidda, simon-veitner-redhat

## AI分析总结

# vLLM 昨日 63 个提交综合分析

## 一、主要更新类型分布
- **Bug 修复**占比最高（近半数提交），涵盖模型适配、量化、注意力机制、分布式并行与接口层。
- **性能优化**约 7 条，集中在 MoE、KV 缓存与 ROCm 后端。
- **CI/构建**约 12 条，涉及 ARM64、ROCm、macOS abi3 wheels。
- **功能新增**与**重构清理**并行：新增 Responses API 与 structured decisions 能力，同时移除 Python 3.10 支持、torch.compile 序列并行和 AsyncTP 死代码。

## 二、关键变更点
- **API 拓展**：新增 `/v1/systemone` structured decisions 端点并在次日即移除 opt-in flag 正式暴露；Responses API 支持 `min_p` 与 `stop_token_ids`；Rust gRPC 前端修复了显式采样值为 0 被忽略的语义问题，protobuf 默认值处理更可靠。
- **量化演进**：MXFP4 oracle 新增 CUTLASS W4A4 后端；NVFP4 KV cache 扩展至 SM90+FA2；共享专家融合兼容在线量化；批不变性检查扩展到所有 attention 后端，为量化精度提供保障。
- **新模型适配**：GLM-5.3/5.3-Flash、Qwen4、MiniMax-M3、Kimi K3 的修复与优化持续深入，并配套 DFlash2 投机解码草稿模型。
- **平台扩展**：ROCm/AMD 投入显著（AiterExperts、RDNA3 W4A16 MoE、Kimi-K3 fused kernels）；XPU（Intel）活跃维护；CPU 后端修复 fused Gumbel-max 的 wrapping-window bias 计算错误。
- **MoE 与 LoRA**：permute scratch 大小修正、Kimi K3 共享专家分片、latent MoE rank 分片；修复 3D MoE 模型多 LoRA 适配器共享时未走 `FusedMoEWithLoRA` 路径的问题。

## 三、对项目的影响
- **稳定性与正确性**：修复 prefix cache 一致性、HiSparse 路由、异步 KV 加载、Unicode 结构化输出等边界问题，三条关键正确性修复（采样传递、数值偏差、推理路径选择）直接增强生产可信度。
- **长上下文性能**：fallback decode 的 CPU 开销在 32K 上下文下降低 69%，KV cache 队列开销优化，显著改善大规模部署吞吐。
- **构建现代化**：淘汰 EOL 的 Python 3.10、清理死代码、macOS abi3 wheels，降低维护负担并为后续特性腾出空间。

## 四、值得关注的技术点
- **AI 辅助开发迹象明显**：超过半数提交的 Co-authored-by 含 Claude、Codex、Cursor 等工具，vLLM 社区已大规模采用 AI 辅助编码。
- **HiSparse 稀疏注意力**多条修复（swap-row 路由、prefetch buffer、host pool 注册），该路径正走向成熟。
- **FusedMoEWithLoRA 条件分发**涉及张量/流水线/专家并行交互，是 MoE 多租户服务的核心难点。
- **多来源协作**：提交分别来自 NVIDIA、IBM、Daocloud 等贡献者，多硬件、多并行、多接口的社区生态持续健康发展。

## 五、对发展方向的启示
结合 README "Easy, fast, and cheap LLM serving for everyone" 的目标：(1) 快速跟进 GLM-5.3、Kimi K3、Qwen4 等新模型，保持模型覆盖领先；(2) ROCm/XPU/CPU 多后端投入呼应"普惠廉价服务"承诺；(3) 代码清理与死代码移除为性能特性蓄力；(4) structured decisions、Responses API 与 Rust gRPC 前端的成熟，表明 vLLM 正从纯 LLM 推理服务扩展为更完整的生成式 AI 基础设施层，并稳步走向生产就绪。

## 详细提交记录

### [ab905a8](https://github.com/vllm-project/vllm/commit/ab905a885dfbfc60a2c02286cc9c608c93884de3)

- **作者**: Misha Goin
- **时间**: 2026-10-08T22:22:20Z
- **提交信息**: [CI] Run GH200 test on the shared arm64 CI image (#60253)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Kevin H. Luu <khluu000@gmail.com>

### [8d10c38](https://github.com/vllm-project/vllm/commit/8d10c38b7304aa42432f4117f0d197ff46258ecb)

- **作者**: Kamran
- **时间**: 2026-10-08T21:42:56Z
- **提交信息**: [Perf] Reduce fallback decode CPU by 69% at 32K (#60497)

Signed-off-by: spa5k <79936503+spa5k@users.noreply.github.com>
Co-authored-by: Codex <codex@openai.com>

### [240785b](https://github.com/vllm-project/vllm/commit/240785b82c299c6c08bc5239e997cf62d67cf7bb)

- **作者**: Yifan Qiao
- **时间**: 2026-10-08T20:44:04Z
- **提交信息**: [Bugfix] Keep the GLM-5.3 kpool tail and Qwen4 QSA ring out of the null block (#59528)

Signed-off-by: Yifan Qiao <yifanqiao@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [2ddde19](https://github.com/vllm-project/vllm/commit/2ddde19e8e0ba1b9d06a3f9b6201f7fc915d27ab)

- **作者**: sungbin1015
- **时间**: 2026-10-08T20:38:17Z
- **提交信息**: [Frontend] Support min_p in the Responses API (#48084)

Signed-off-by: sungbin1015 <sbin@solbox.com>
Co-authored-by: Flora Feng <4florafeng@gmail.com>

### [c5c1161](https://github.com/vllm-project/vllm/commit/c5c116138267ac738bc262495326d28ffff834a2)

- **作者**: Divakar Verma
- **时间**: 2026-10-08T20:28:38Z
- **提交信息**: [ROCm][Build] Fail fast when `setup.py develop` deps aren't pip-preinstalled (#59447)

Signed-off-by: Divakar Verma <divakar.verma@amd.com>

### [ae9adec](https://github.com/vllm-project/vllm/commit/ae9adec9059b6c6d831cfa46ce966a3d629a4526)

- **作者**: Francisco Javier Arceo
- **时间**: 2026-10-08T20:21:05Z
- **提交信息**: [Frontend] Expose /v1/systemone without an opt-in flag (#60677)

Signed-off-by: Francisco Javier Arceo <4163062+franciscojavierarceo@users.noreply.github.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>

### [72d59ad](https://github.com/vllm-project/vllm/commit/72d59adc2c76de8f77aad640c7a04d663a970735)

- **作者**: Alberto Massidda
- **时间**: 2026-10-08T19:58:13Z
- **提交信息**: [Bugfix][KV Connector][NIXL] Transfer the whole PLE short-conv page in disaggregated P/D (#59997)

Signed-off-by: Alberto Massidda <amassidda@nvidia.com>
Co-authored-by: Alberto Massidda <amassidda@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: Artem Perevedentsev <aperevedents@nvidia.com>

### [1afb029](https://github.com/vllm-project/vllm/commit/1afb029839a7c84f14dae30bb08f2fea79184431)

- **作者**: Matthew Bonanni
- **时间**: 2026-10-08T19:45:44Z
- **提交信息**: [Bugfix][HiSparse] Route by swap-row capacity, not the index-group workspace (#60682)

Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [c23ca06](https://github.com/vllm-project/vllm/commit/c23ca06b6d944579ad9d220297441236755b4744)

- **作者**: simon-veitner-redhat
- **时间**: 2026-10-08T19:38:33Z
- **提交信息**: [Bugfix][Structured Output] Feed the token that implicitly ends reasoning to the grammar (#59627)

Signed-off-by: Simon Veitner <sveitner@redhat.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: Misha Goin <mgoin64@gmail.com>
Co-authored-by: Yifan Zong <263738792+yzong-rh@users.noreply.github.com>

### [bab0ac6](https://github.com/vllm-project/vllm/commit/bab0ac61f8dae8020df6725c90474bdd647f1c40)

- **作者**: dingdangmao
- **时间**: 2026-10-08T19:32:46Z
- **提交信息**: [Bugfix][Frontend] Forward the reasoning wiring to the engine for batch chat completions (#59263)

Signed-off-by: apex-mochen <2756823972@qq.com>
Signed-off-by: sfeng33 <4florafeng@gmail.com>
Co-authored-by: Flora Feng <4florafeng@gmail.com>

### [e3a29aa](https://github.com/vllm-project/vllm/commit/e3a29aa9b33e894ee576d3d092ae7605fb4e7721)

- **作者**: Misha Goin
- **时间**: 2026-10-08T19:32:07Z
- **提交信息**: [Bugfix][MoE] Size the permute scratch from its inputs (#60447)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [fff10d2](https://github.com/vllm-project/vllm/commit/fff10d20728780c58a9427986174eb7485ab5c12)

- **作者**: SeongJun Lee
- **时间**: 2026-10-08T19:16:22Z
- **提交信息**: [Attention] Allow an NVFP4 KV cache on SM90 with fa2 (#60620)

Signed-off-by: lesj0610 <lesj0610@gmail.com>
Co-authored-by: Misha Goin <mgoin64@gmail.com>

### [fc49482](https://github.com/vllm-project/vllm/commit/fc494822eaca100b6339a4911ce36784926573fc)

- **作者**: Kevin Li
- **时间**: 2026-10-08T19:14:35Z
- **提交信息**: [Test][Quantization] Gate CUTLASS W4A8 kernel tests to SM90 (#58878)

Signed-off-by: Kevin Li <kevinbean99@gmail.com>
Co-authored-by: Misha Goin <mgoin64@gmail.com>

### [18751bc](https://github.com/vllm-project/vllm/commit/18751bc6a7b4b24fa5e6bbd5299100dd0b19a22b)

- **作者**: Divakar Verma
- **时间**: 2026-10-08T19:11:45Z
- **提交信息**: [ROCm][CI] Add coverage for AiterExperts token padding: inf/nan garbage rows (#59334)

Signed-off-by: Divakar Verma <divakar.verma@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [9bbc581](https://github.com/vllm-project/vllm/commit/9bbc58156095f45bdb91ddbdbd244119d3afb12c)

- **作者**: Aarushi Jain
- **时间**: 2026-10-08T18:53:00Z
- **提交信息**: [Bugfix] Close MessageQueue zmq resources via finalizer to avoid exit (#60472)

Signed-off-by: aarushjain29 <aarushi.jain2@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [56e6da2](https://github.com/vllm-project/vllm/commit/56e6da2c4717f6c6c2faa0159f8c0fa2cf508d6f)

- **作者**: Yeonwoo Sung
- **时间**: 2026-10-08T18:47:30Z
- **提交信息**: [Bugfix][Frontend] Honor stop_token_ids on the Responses API (#56592)

Signed-off-by: YeonwooSung <neos960518@gmail.com>
Signed-off-by: sfeng33 <4florafeng@gmail.com>
Co-authored-by: Flora Feng <4florafeng@gmail.com>

### [c4a5ff5](https://github.com/vllm-project/vllm/commit/c4a5ff5c18ceba5f06512ef6b17a48338f275763)

- **作者**: Ning Xie
- **时间**: 2026-10-08T18:46:01Z
- **提交信息**: [Frontend] shutdown engine core and its sub processes asap when initializing (#52299)

Signed-off-by: Andy Xie <andy.xning@gmail.com>
Co-authored-by: Simon Mo <simon.mo@hey.com>

### [2274e86](https://github.com/vllm-project/vllm/commit/2274e86842d6e59a5f9f9d1fb6cc1dd2d2bf8350)

- **作者**: Shijin Zhang
- **时间**: 2026-10-08T18:41:10Z
- **提交信息**: [Spec Decode][Model] Support DFlash2 draft models with GLM-5.3-Flash (#56983)

Signed-off-by: Shijin Zhang <75300765+Dovis01@users.noreply.github.com>

### [30c7405](https://github.com/vllm-project/vllm/commit/30c740589055c86f29859f61b13ae6620449f3fc)

- **作者**: Misha Goin
- **时间**: 2026-10-08T18:39:09Z
- **提交信息**: [MoE] MXFP4 oracle: add CUTLASS W4A4 backend and BF16 activation fallback (#60079)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [d8fa463](https://github.com/vllm-project/vllm/commit/d8fa463e2ba751759a3534dd3ce11af92f1eed83)

- **作者**: Wei Zhao
- **时间**: 2026-10-08T18:33:48Z
- **提交信息**: [Bugfix][Prefix caching] Fix inconsistent hybrid Mamba prefix cache boundaries (#60533)

Signed-off-by: Wei Zhao <weizha@aws-cmh-slurm-1-login-01.cm.cluster>
Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: Wei Zhao <weizha@aws-cmh-slurm-1-login-01.cm.cluster>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [1664c4f](https://github.com/vllm-project/vllm/commit/1664c4f44416804dc47e3677e50933e6e9b4f45e)

- **作者**: kyleliang-nv
- **时间**: 2026-10-08T18:27:57Z
- **提交信息**: [Bugfix][MiniMax-M3] Guard sparse decode sentinel indices (#54597)

Signed-off-by: Kyle Liang <kylliang@nvidia.com>
Signed-off-by: Kyle Liang <kyleliang-nv@users.noreply.github.com>
Co-authored-by: Kyle Liang <kyleliang-nv@users.noreply.github.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [972195f](https://github.com/vllm-project/vllm/commit/972195f4f589688fd4cfbbcfb55a5b5502f5af35)

- **作者**: Tialo
- **时间**: 2026-10-08T18:19:20Z
- **提交信息**: [CI][Build] build macos wheels using abi3 (#60312)

Co-authored-by: Misha Goin <mgoin64@gmail.com>

### [705e124](https://github.com/vllm-project/vllm/commit/705e124c05cffe7c00dd19434922c94e0610d674)

- **作者**: Francisco Javier Arceo
- **时间**: 2026-10-08T18:00:03Z
- **提交信息**: [Bugfix] Followup to #59299: preserve Unicode in structured decision state prompts (#60651)

Signed-off-by: Francisco Javier Arceo <4163062+franciscojavierarceo@users.noreply.github.com>
Co-authored-by: Misha Goin <mgoin64@gmail.com>

### [242e421](https://github.com/vllm-project/vllm/commit/242e4213fc9845ff6fe607af1aee626fd8acc990)

- **作者**: Doug Smith
- **时间**: 2026-10-08T16:43:39Z
- **提交信息**: [Doc] Require GCC 13 for CUDA source builds (#60259)

Signed-off-by: Doug Smith <dosmith@redhat.com>

### [8674a79](https://github.com/vllm-project/vllm/commit/8674a794c788d4c7dac10c6f7ddfdae677588d18)

- **作者**: Elvir Crnčević
- **时间**: 2026-10-08T16:42:15Z
- **提交信息**: [Perf] Enable Kimi K3 shared expert sharding with DeepEP v2 (#56875)

Co-authored-by: Misha Goin <mgoin64@gmail.com>

### [f4dde31](https://github.com/vllm-project/vllm/commit/f4dde3132c94cccce485a1a59acac1d06739a59d)

- **作者**: stefankoncarevic
- **时间**: 2026-10-08T16:18:05Z
- **提交信息**: [CI][ROCm] Reuse AITER's prebuilt MoE module in the modular-kernel harness (#60633)

Signed-off-by: Stefan Koncarevic <stefan.koncarevic@amd.com>

### [9f3d70e](https://github.com/vllm-project/vllm/commit/9f3d70e08157a95911f15809f2f1446424825ea7)

- **作者**: fxmarty-amd
- **时间**: 2026-10-08T16:04:46Z
- **提交信息**: [Quantization] Enable shared expert fusion compatibility with online `shared_expert` quantization (showcase: along Quark MXFP4 routed experts) (#55686)

Signed-off-by: Felix Marty <Felix.Marty@amd.com>
Signed-off-by: fxmarty-amd <felmarty@amd.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: Misha Goin <mgoin64@gmail.com>

### [e2414ec](https://github.com/vllm-project/vllm/commit/e2414ec1dbb177b54ac1bbce60e94769ebacbb28)

- **作者**: Mikko Tukiainen
- **时间**: 2026-10-08T15:47:56Z
- **提交信息**: [ROCm][Qwen4Exp] Use fused PLE Triton kernels on the AMD backend (#60021)

Signed-off-by: Mikko Tukiainen <Mikko.Tukiainen@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [0fc0cef](https://github.com/vllm-project/vllm/commit/0fc0cefb4eecf685c4bbd20912db9c1294d84c1e)

- **作者**: Justin Barlow
- **时间**: 2026-10-08T15:34:55Z
- **提交信息**: [Bugfix] Don't int-sort attention-type names in --kv-cache-dtype-skip-layers for packed KV dtypes (#60364)

Signed-off-by: lobo235 <7@netlobo.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [e41d5d5](https://github.com/vllm-project/vllm/commit/e41d5d55439808e79326009599d5d83e157bf2d1)

- **作者**: simon-veitner-redhat
- **时间**: 2026-10-08T15:29:20Z
- **提交信息**: [Bugfix] Don't warn about missing watermark config for default requests (#60412)

Signed-off-by: Simon Veitner <sveitner@redhat.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: Lucas Wilkinson <LucasWilkinson@users.noreply.github.com>

### [0751f52](https://github.com/vllm-project/vllm/commit/0751f5272fb323e0a5c62a6157f0a3c1d93e6bc5)

- **作者**: Haokai Ma
- **时间**: 2026-10-08T15:29:04Z
- **提交信息**: [Bugfix] Scope deprecated CLI argument warnings to the parser that defines them (#59917)

Signed-off-by: Tyler Ma <158780265+TylerMa-debugg@users.noreply.github.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [194bd72](https://github.com/vllm-project/vllm/commit/194bd72be7b9eb1c406e090328ddaf09a4e2d6eb)

- **作者**: Woosuk Kwon
- **时间**: 2026-10-08T15:28:23Z
- **提交信息**: [Compile] Remove torch.compile-based sequence parallelism and AsyncTP (#60517)

### [072d49b](https://github.com/vllm-project/vllm/commit/072d49bb6eb017a1e33bf3d016a979972438a90f)

- **作者**: wangxiyuan
- **时间**: 2026-10-08T15:25:21Z
- **提交信息**: [Platform] Support platform-specific MLA prefill backend selection (#56959)

Signed-off-by: wangxiyuan <wangxiyuan1007@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [fd928e5](https://github.com/vllm-project/vllm/commit/fd928e5f3cf17bce1ba090040beec48f86c84ff6)

- **作者**: yifanFengg
- **时间**: 2026-10-08T15:19:57Z
- **提交信息**: [Bugfix] Check batch-invariance support for every attention backend (#60271)

Signed-off-by: yifanFengg <evanfengff@gmail.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>

### [994b8b7](https://github.com/vllm-project/vllm/commit/994b8b77be74e65c869c1ca8979fefb17b162b11)

- **作者**: JartX
- **时间**: 2026-10-08T15:06:39Z
- **提交信息**: [Bugfix][ROCm] RDNA3 W4A16 MoE: handle the N-first CT weight layout (#60388)

Signed-off-by: JartX <sagformas@epdcenter.es>

### [d80ddaa](https://github.com/vllm-project/vllm/commit/d80ddaac73217770af1548f43e0cd7e68d4ec33d)

- **作者**: kliuae
- **时间**: 2026-10-08T14:55:20Z
- **提交信息**: [ROCm][Perf] Kimi-K3 Store only the current rank's shards in latent MoE up-proj  (#59591)

Signed-off-by: kliuae <kuanfu.liu@embeddedllm.com>

### [d33872d](https://github.com/vllm-project/vllm/commit/d33872dfeb79db89b734ce13e07af4630e8bdce2)

- **作者**: Matt Mastracci
- **时间**: 2026-10-08T14:48:12Z
- **提交信息**: [Feat] Structured decisions endpoint (`/v1/systemone`) (#59299)

Signed-off-by: Matt Mastracci <matthew@mastracci.com>
Signed-off-by: Lucas Wilkinson <lwilkins@redhat.com>
Signed-off-by: Francisco Javier Arceo <4163062+franciscojavierarceo@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: Lucas Wilkinson <LucasWilkinson@users.noreply.github.com>
Co-authored-by: Francisco Javier Arceo <4163062+franciscojavierarceo@users.noreply.github.com>
Co-authored-by: Chauncey <chaunceyjiang@gmail.com>

### [273e099](https://github.com/vllm-project/vllm/commit/273e099693a6c92e1bc516cd10ffc38b18197eec)

- **作者**: yhcheong (vllmellm)
- **时间**: 2026-10-08T14:44:58Z
- **提交信息**: [Bugfix][ROCm] Select page-aligned kernel blocks for pooled indexers so the block table addresses storage pages (GLM-5.3-Flash) (#59412)

Signed-off-by: vllmellm <vllm.ellm@embeddedllm.com>

### [2f7f05c](https://github.com/vllm-project/vllm/commit/2f7f05c256d671a7bdf04bcf4b4fc6a1566bbfcb)

- **作者**: zzaebok
- **时间**: 2026-10-08T14:28:16Z
- **提交信息**: [Bugfix][MoRIIO] Prevent remote KV reload after decoder preemption (#53250)

Signed-off-by: Jaebok Lee <jaebok9541@naver.com>

### [daa9085](https://github.com/vllm-project/vllm/commit/daa9085143d65896ba3fa77635b0b110aab3e585)

- **作者**: Pravein Govindan Kannan
- **时间**: 2026-10-08T14:25:02Z
- **提交信息**: [KV Connector][NIXL] Register HiSparse host pool under single TP Rank (#60161)

Signed-off-by: Pravein Govindan Kannan <pravein.govindan.kannan@ibm.com>
Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [4ed4c44](https://github.com/vllm-project/vllm/commit/4ed4c4433b87e45d72f401f27f1b56c932c90071)

- **作者**: Matthew Bonanni
- **时间**: 2026-10-08T14:00:49Z
- **提交信息**: [Bugfix][HiSparse] Drop the unaccounted, write-only prefill mirror staging buffer (#60429)

Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [194da61](https://github.com/vllm-project/vllm/commit/194da61de1769c28bfad2b6642c60cc7eca544dd)

- **作者**: Vineeth Sai Varikuntla
- **时间**: 2026-10-08T13:01:25Z
- **提交信息**: [Bugfix] Reject negative --device-ids indices instead of selecting the wrong device (#49053)

Signed-off-by: Vineeth Sai <vineethsai4444@gmail.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [458ba2e](https://github.com/vllm-project/vllm/commit/458ba2edf85bc9b7ebc0d5141f34ea658520faf5)

- **作者**: Hexiang Wang
- **时间**: 2026-10-08T12:01:47Z
- **提交信息**: [ROCm][Kimi-K3] Fuse AttnRes output with per-token FP8 input quantization (#59069)

Signed-off-by: whx-sjtu <xiaowang990929@gmail.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: Fangzhou Ai <31551580+Fangzhou-Ai@users.noreply.github.com>

### [73c742b](https://github.com/vllm-project/vllm/commit/73c742b09c14f0260ccc9e9e7449444bdaf5475a)

- **作者**: Stu Cao
- **时间**: 2026-10-08T11:41:14Z
- **提交信息**: [Bugfix] Make disable_any_whitespace actually disable whitespace on xgrammar (#58067)

Signed-off-by: Stu Cao <stu@primeintellect.ai>
Signed-off-by: Artem Perevedentsev <aperevedents@nvidia.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: Artem Perevedentsev <aperevedents@nvidia.com>

### [b49c921](https://github.com/vllm-project/vllm/commit/b49c921a27083c25c16f308be1326055dbc87bbf)

- **作者**: devshah-cohere
- **时间**: 2026-10-08T11:11:55Z
- **提交信息**: [Bugfix][Rust Frontend] Always include token_ids in completion stream choices (#60286)

Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Signed-off-by: devshah-cohere <dev.shah@cohere.com>

### [ba77c4c](https://github.com/vllm-project/vllm/commit/ba77c4c13018aa19244545cdc7ae8e016d66955e)

- **作者**: Andy Lo
- **时间**: 2026-10-08T10:35:22Z
- **提交信息**: [Bugfix][Attention] Preserve small FP8 softmax weights in Triton attention (#60156)

Signed-off-by: Andy Lo <andy@mistral.ai>

### [e161a07](https://github.com/vllm-project/vllm/commit/e161a0798c2305252e2b9bae483c537e9d0fc027)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-10-08T10:17:11Z
- **提交信息**: [Perf][Core] Reduce free KV cache queue overhead (#60269)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [4597641](https://github.com/vllm-project/vllm/commit/459764104d2f8ac1b8a947f9a5a2603bdb07e360)

- **作者**: wang.yuqi
- **时间**: 2026-10-08T09:56:05Z
- **提交信息**: [Frontend] Move offline_utils.py to entrypoints/common. (#58052)

Signed-off-by: wang.yuqi <yuqi.wang@daocloud.io>

### [e73895a](https://github.com/vllm-project/vllm/commit/e73895a5dfc242ed8243bacb394ab75438b591d8)

- **作者**: Muhammad Usman Mateen
- **时间**: 2026-10-08T09:52:50Z
- **提交信息**: [Bugfix] Make `suppress_stdout` redirect fd 1 instead of `sys.stdout.fileno()` (#59336)

Signed-off-by: usmanmateen <usmanmateen255@gmail.com>
Co-authored-by: Misha Goin <mgoin64@gmail.com>

### [dfaabf9](https://github.com/vllm-project/vllm/commit/dfaabf91ac3dfa7e8e6bd0f56c7478026a533b2f)

- **作者**: Chaojun Zhang
- **时间**: 2026-10-08T09:48:47Z
- **提交信息**: [XPU] [CI] Fix stale ignore path for weight_transfer_metrics tests on Intel CI (#60558)

Signed-off-by: Chaojun Zhang <chaojun.zhang@intel.com>

### [24be8c0](https://github.com/vllm-project/vllm/commit/24be8c0bca2fd806548ad84c0999885a65f0805d)

- **作者**: Kevin H. Luu
- **时间**: 2026-10-08T09:42:07Z
- **提交信息**: [CI] Remove dead in-tree TPU (torch_xla) CI scripts (#60591)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [e265b77](https://github.com/vllm-project/vllm/commit/e265b77982e5e2724ce0b2841a2b05fe339d62ee)

- **作者**: Jiangyun Zhu
- **时间**: 2026-10-08T09:39:56Z
- **提交信息**: [CI][Mamba] Use well-conditioned prompts for FlashInfer ReplaySSM parity tests (#60515)

Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [7816afd](https://github.com/vllm-project/vllm/commit/7816afdb259dbb18f9e98d11b05194dd3446d0fa)

- **作者**: stefankoncarevic
- **时间**: 2026-10-08T09:33:41Z
- **提交信息**: [Bugfix][Core] Drain async KV loads in pause(mode="wait"), and pause the drain test only once a request is in flight (#60572)

Signed-off-by: aoshen02 <aoshen@inferact.ai>
Signed-off-by: Stefan Koncarevic <Stefan.Koncarevic@amd.com>
Co-authored-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [c4cd88d](https://github.com/vllm-project/vllm/commit/c4cd88d9fee92ff080837c6c1cdf1de6fe4013fe)

- **作者**: Kevin H. Luu
- **时间**: 2026-10-08T09:31:13Z
- **提交信息**: [CI] Make (H100) Distributed DP + EP optional (#60540)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [21d9758](https://github.com/vllm-project/vllm/commit/21d97584593de08f7a1a44dad8aca32aa4a01c51)

- **作者**: Harry Mellor
- **时间**: 2026-10-08T09:30:52Z
- **提交信息**: Remove Python 3.10 support now that it is EOL (#60402)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [0004536](https://github.com/vllm-project/vllm/commit/0004536dd00f8237fd6dd68171fbda9b680c07b2)

- **作者**: liuzhenwei
- **时间**: 2026-10-08T09:13:48Z
- **提交信息**: [XPU][Graph] Replace boolean-mask assignment with `torch.where` (#60529)

Signed-off-by: zhenwei-intel <zhenwei.liu@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [70bdce6](https://github.com/vllm-project/vllm/commit/70bdce6133d0094f420a3714bb9ee186238c82f6)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-10-08T09:05:52Z
- **提交信息**: [Model][GLM-5.3-Flash] Warm up the DCP top-k merge kernels for the kpool indexer (#60032)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [7d47ac2](https://github.com/vllm-project/vllm/commit/7d47ac2ddba430510f1503dae424bb298fe5a300)

- **作者**: Thang Nguyen
- **时间**: 2026-10-08T08:52:59Z
- **提交信息**: [CI] Enroll five steps in automatic sharding (#60492)

Signed-off-by: Thang Nguyen <thangnguyenvn647@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: khluu <khluu000@gmail.com>

### [4cf1307](https://github.com/vllm-project/vllm/commit/4cf1307e72cb1648e4e3c3ab4e0bf85d5616fcb3)

- **作者**: Paweł Mańczak
- **时间**: 2026-10-08T08:36:05Z
- **提交信息**: [XPU] Add tuned Mamba SSU configs for 2 more B70 shapes (#57565)

Signed-off-by: pmanczak <pawel.manczak@intel.com>

### [0f112d1](https://github.com/vllm-project/vllm/commit/0f112d180033f3757cf283723f5593a40b02ed82)

- **作者**: Ting SUN
- **时间**: 2026-10-08T07:33:28Z
- **提交信息**: [Bugfix][Pooling] Preserve cache_salt for chunked embeddings (#47696)

Signed-off-by: Ting Sun <suntcrick@gmail.com>

### [29ae81f](https://github.com/vllm-project/vllm/commit/29ae81fe83712bb74c00a4ce0515d031f1225c9b)

- **作者**: Alec
- **时间**: 2026-10-08T07:27:47Z
- **提交信息**: [Rust Frontend] Preserve explicit zero sampling values in gRPC requests (#60115)

Signed-off-by: Alec Flowers <aflowers@nvidia.com>

### [fd0216d](https://github.com/vllm-project/vllm/commit/fd0216d3b598501e28041d84ed0b7dd16453aac6)

- **作者**: Rehan Khan
- **时间**: 2026-10-08T07:15:53Z
- **提交信息**: [Bugfix][CPU] Fix fused Gumbel-max wrapping-window bias (#60221)

Signed-off-by: Rehan Khan <Rehan.Khan7@ibm.com>
Co-authored-by: Bob <bob@ibm.com>

### [e58f8dd](https://github.com/vllm-project/vllm/commit/e58f8dde7f02631829142f11eaa89099bcd94a98)

- **作者**: ARAVINDHAN T
- **时间**: 2026-10-08T07:04:32Z
- **提交信息**: [Bugfix] Use FusedMoEWithLoRA for shared MoE LoRAs on 3D models (#60098)

Signed-off-by: ARAVINDHAN T <arvindhant01@gmail.com>
Co-authored-by: linitra24 <renshuang.zhou@daocloud.io>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-10-09
**监控日期**: 2026-10-08
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7093
- **最后更新**: 2026-10-09T02:12:46Z

## 提交统计

- **昨日提交总数**: 21
- **提交者数量**: 19
- **主要提交者**: Yifan Tian, Armaan Amatya, Tianyao Wu

## AI分析总结

# vLLM-Omni 昨日提交分析（21条）

## 一、主要更新类型分布

- **Bug修复**：约 8 条（占比最高），集中在多模态模型的正确性问题上
- **性能优化**：约 5 条，涉及 FP8、稀疏注意力、TensorRT、内存管理等
- **功能新增**：约 4 条，覆盖请求级批处理、NPU 支持、客户端输出扩展等
- **CI/构建**：2 条，ROCm 构建修复与 CPU 队列调度调整
- **模型适配**：若干，新增/更新 Kandinsky、Z-Image 等模型组件

## 二、关键变更点及与项目方向的关系

README 表明项目目标是"让每个人都轻松、快速、低成本地服务全模态模型"。本次提交高度契合这一愿景：

1. **多模态覆盖广度持续扩展**：MiniCPM-o（含 NPU/Code2Wav 图）、Qwen3-TTS、YuE2、CosyVoice3、PersonaPlex、MOSS、SenseNova-U1、Z-Image 等模型均有更新，体现"全模态"的服务覆盖面。
2. **多硬件后端并进**：ROCm（AMD）修复 FP8 契约、Intel 贡献 SDXL 批处理、Huawei 贡献 NPU 编码图、CPU/NPU 张量的 Triton 分发保护——项目正强化跨平台部署能力，降低成本门槛。
3. **低延迟与吞吐优化**：Block-sparse attention（Qwen2.5-Omni Token2Wav DiT）、FP8 GEMM（AuK DiT）、RoPE 表提升（PersonaPlex）、VAE 切片分块（mammoth）、SHM 回收限制——直接服务"快速且低成本"的目标。

## 三、对项目的影响和潜在意义

- **正确性提升**：prefix caching 下的 YuE2 输出构建、多模态 UUID 作用域、TeaCache 系数标定等修复，增强了生产环境可靠性，对长上下文与缓存场景尤其重要。
- **成本下降路径明确**：FP8 与稀疏注意力是推理成本下降的主流手段，AuK 与 DiT 块的 FP8 优化意味着视频/图像扩散模型的服务成本将显著降低。
- **批处理能力增强**：SDXL 请求级批处理（#7033，PR 号显示开发周期长）是图像生成服务吞吐的关键补齐。
- **硬件生态成熟**：AMD/Intel/NPU 贡献者的活跃参与，表明项目在异构硬件上的社区支持正在走向制度化。

## 四、值得关注的技术点

- **TeaCache 系列修复**（SenseNova-U1、ZImageAdapter）：缓存加速机制在不同模型上的正确性标定，是扩散模型推理优化的核心工程难题。
- **块稀疏注意力在 Token2Wav DiT 中的应用**：语音生成的长序列注意力是延迟瓶颈，此优化路径值得后续语音模型复用。
- **PersonaPlex 的 delta-only Code2Wav 输入**：数据最小化传输，对流式语音服务的带宽与延迟均有收益。
- **AI 辅助开发痕迹**：多条提交署名 Cursor、Claude 等 AI 协作者，反映项目在拥抱 AI 编码工具。

## 五、对项目发展的影响

基于 README 的"omni-modality serving for everyone"定位，本批提交呈现三条发展主线：**其一**，模型覆盖从文本-语音扩展到图像/视频扩散（SDXL、Kandinsky、Z-Image），全模态版图趋于完整；**其二**，FP8、稀疏注意力、TE/TensorRT 等手段将"cheap"落到实处，对齐 vLLM 主线的低成本定位；**其三**，CI 稳定性与多硬件支持的投入（ROCm、CPU 队列、NPU），标志着项目从功能期进入生产就绪期。整体而言，这是一批成熟度较高的工程迭代，为 vLLM-Omni 成为全模态推理的默认选择奠定了正确性与性能基础。

## 详细提交记录

### [f9b97d2](https://github.com/vllm-project/vllm-omni/commit/f9b97d258d9621832bb423289afc3998ec330ffc)

- **作者**: haic0
- **时间**: 2026-10-08T23:13:53Z
- **提交信息**: [Bugfix][CI/Build][ROCm] Fix AuK FP8 and diffusion CI contracts (#8643)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>
Signed-off-by: andyluo7 <andy.luo@amd.com>
Co-authored-by: GPT-5.6 Sol <noreply@cursor.com>
Co-authored-by: andyluo7 <andy.luo@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [1e0c4f3](https://github.com/vllm-project/vllm-omni/commit/1e0c4f3d54a91c30de97aa332e772dfe7338f52c)

- **作者**: Nikita Osterov
- **时间**: 2026-10-08T18:27:07Z
- **提交信息**: Map current Kandinsky 6 Diffusers checkpoint names. (#8590)

Signed-off-by: Nikita Osterov <90456300+osipovmekete@users.noreply.github.com>

### [638ba77](https://github.com/vllm-project/vllm-omni/commit/638ba7775dfb8c7201913629cfebae0b6e93cafb)

- **作者**: Yueqian Lin
- **时间**: 2026-10-08T18:00:27Z
- **提交信息**: [Feature][Qwen3-TTS] Return the codec frames code2wav decodes as a client output (#8619)

Signed-off-by: Yueqian Lin <linyueqian@outlook.com>

### [e623cef](https://github.com/vllm-project/vllm-omni/commit/e623cef98adebc01a56c7bd2bc6b614229496055)

- **作者**: Yueqian Lin
- **时间**: 2026-10-08T17:47:08Z
- **提交信息**: [Perf][AuK] Opt-in FP8 GEMMs for the DiT block linears (#8442)

Signed-off-by: Yueqian Lin <linyueqian@outlook.com>

### [2f5db39](https://github.com/vllm-project/vllm-omni/commit/2f5db3999c4134afcf45697f8d9817676c3aeb15)

- **作者**: heyuanliu-intel
- **时间**: 2026-10-08T17:31:27Z
- **提交信息**: [Feature] Support request-level batching for SDXL text2image (#7033)

Signed-off-by: heyuanliu-intel <heyuan.liu@intel.com>

### [e525f51](https://github.com/vllm-project/vllm-omni/commit/e525f51a2abf91633d0adb903f44f5298d4ff540)

- **作者**: Armaan Amatya
- **时间**: 2026-10-08T17:31:17Z
- **提交信息**: [Bugfix] Scope stage-0 multimodal UUIDs on a copy of the prompt (#8062)

Signed-off-by: Armaan Amatya <armaanamatya2014@gmail.com>

### [0242b17](https://github.com/vllm-project/vllm-omni/commit/0242b17c7225abc7c65bb76a7f51e48df8e213ec)

- **作者**: Linze Shi
- **时间**: 2026-10-08T17:31:06Z
- **提交信息**: [Bugfix] Fix missing SenseNova-U1 TeaCache position embeddings (#8260)

Signed-off-by: Linze-Shi <linzeshi0@gmail.com>

### [feba049](https://github.com/vllm-project/vllm-omni/commit/feba049e0fe3b1190872e34ff5f127eac94418f4)

- **作者**: Kuatova Kamila
- **时间**: 2026-10-08T17:30:55Z
- **提交信息**: [Bugfix] Calibrate Z-Image TeaCache coefficients and add ZImageAdapter (#8408)

Signed-off-by: Kamila Kuatova <kuatova_kamila@list.ru>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [508ceaa](https://github.com/vllm-project/vllm-omni/commit/508ceaac13dbee4a22341c6760362e802d6265a6)

- **作者**: Yueqian Lin
- **时间**: 2026-10-08T16:56:28Z
- **提交信息**: [Bugfix][MiniCPM-o] Apply the Talker's 16-frame codec penalty on MRv2 (#8576)

Signed-off-by: Yueqian Lin <linyueqian@outlook.com>

### [d0bdf98](https://github.com/vllm-project/vllm-omni/commit/d0bdf988060c1f9fbe64cd0274fee4d8ed935407)

- **作者**: Tianyao Wu
- **时间**: 2026-10-08T16:56:18Z
- **提交信息**: [Bugfix][YuE2] Build the output from live mm outputs when prefix caching is on (#8479)

Signed-off-by: Tianyao Wu <rayroy31@gmail.com>

### [59196c6](https://github.com/vllm-project/vllm-omni/commit/59196c6873ba3df37d8ceee186db5419ec51bbb5)

- **作者**: Runguo Li
- **时间**: 2026-10-08T16:56:07Z
- **提交信息**: [Perf][Model] Use block-sparse attention in Qwen2.5-Omni Token2Wav DiT (#7975)

Signed-off-by: RunguoLi <li19107254665@gmail.com>

### [283ac10](https://github.com/vllm-project/vllm-omni/commit/283ac1003d0425349b65088459c73ba116ab14c4)

- **作者**: jeffaa729
- **时间**: 2026-10-08T16:55:48Z
- **提交信息**: [Bugfix][Model] Make PersonaPlex Code2Wav input delta-only (#7480)

Signed-off-by: jeffaa729 <hoiwanglo@gmail.com>

### [6667316](https://github.com/vllm-project/vllm-omni/commit/666731612e5e2b2692d6224636b4ec9a71d13f32)

- **作者**: Yifan Tian
- **时间**: 2026-10-08T16:55:38Z
- **提交信息**: [Perf][PersonaPlex] Hoist RoPE tables and RingKV position computation out of the per-layer loop (#7850)

Signed-off-by: Yifan Tian <Yifan.Tian@colorado.edu>

### [f4108d7](https://github.com/vllm-project/vllm-omni/commit/f4108d77eb9c7d649ef65070cd2b7158b7571524)

- **作者**: amy-why-3459
- **时间**: 2026-10-08T14:53:35Z
- **提交信息**: [Model] MiniCPM-o 4.5: add NPU and Code2Wav encoder graphs (#8515)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [a46e9aa](https://github.com/vllm-project/vllm-omni/commit/a46e9aae7bb5065a27a69e34ba3f2a09af17a5ce)

- **作者**: Canlin Guo
- **时间**: 2026-10-08T12:44:12Z
- **提交信息**: [Kernel] Accelerate MOSS Local depth decoding with QKV lookup and fusion (#8232)

Signed-off-by: Canlin Guo <canlinguosdu@gmail.com>

### [cbc43c0](https://github.com/vllm-project/vllm-omni/commit/cbc43c07c309b6e21bcfef5d89df575e893d35ce)

- **作者**: easonyu
- **时间**: 2026-10-08T12:14:49Z
- **提交信息**: [Feat][optimization] mammoth moda2 VAE slicing tiling (#7774)

Signed-off-by: VLa1111 <vyu112@foxmail.com>
Co-authored-by: Claude Code <noreply@anthropic.com>

### [b839e29](https://github.com/vllm-project/vllm-omni/commit/b839e295939bfd181aa47464318c213bdf8f61f2)

- **作者**: ZacheryAU
- **时间**: 2026-10-08T10:16:35Z
- **提交信息**: [Bugfix][CI][Benchmark] switch thread_type to SLICE for HEVC in Omni-DuplexEval (#8307)

### [4e675f8](https://github.com/vllm-project/vllm-omni/commit/4e675f8b6d742c0b9f097594ab98414485bd8692)

- **作者**: trueoneplusone
- **时间**: 2026-10-08T09:35:22Z
- **提交信息**: [Model] Reduce CosyVoice3 TensorRT Euler host overhead (#7767)

Signed-off-by: trueoneplusone <78432179+trueoneplusone@users.noreply.github.com>

### [a3d7a04](https://github.com/vllm-project/vllm-omni/commit/a3d7a0444ab47ea5f636fbb5ab46cfb0335d6777)

- **作者**: wangyu
- **时间**: 2026-10-08T08:26:58Z
- **提交信息**: [CI/Build] Move premerge CPU jobs to the medium queue and retune nightly/weekly suites (#8616)

Signed-off-by: wangyu <410167048@qq.com>
Co-authored-by: Alicia <115451386+congw729@users.noreply.github.com>

### [80d36f4](https://github.com/vllm-project/vllm-omni/commit/80d36f4ed1fc7d1ceb101cd7d61823333efe4928)

- **作者**: Liuchenbing-2026
- **时间**: 2026-10-08T07:40:51Z
- **提交信息**: [Bugfix] Guard OmniVoice Triton dispatch for CPU and NPU tensors (#8589)

Signed-off-by: liuchenbing <chenliumail@163.com>
Co-authored-by: liuchenbing <chenliumail@163.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [d6251a2](https://github.com/vllm-project/vllm-omni/commit/d6251a2400ec76270f9706003631e20c0b79ab68)

- **作者**: psv666
- **时间**: 2026-10-08T07:37:29Z
- **提交信息**: [Core] Limit SHM reaping work on chunk sends (#8618)

Signed-off-by: psv666 <2693925048@qq.com>

---
