# GitHub Stars 合并报告 - 2026-06-16

**合并日期**: 2026-06-17
**监控日期**: 2026-06-16
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


**报告日期**: 2026-06-17
**监控日期**: 2026-06-16
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2021
- **最后更新**: 2026-06-16T22:21:25Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 3
- **主要提交者**: zhangxin.zzzzz, Crystal-jiang, 鐘天楽

## AI分析总结

好的，这是对ByteDance-Seed/VeOmni仓库昨日提交记录的分析总结：

### 1. 主要更新类型

-   **功能新增 (Feature):** 1项
-   **Bug修复 (Bug Fix):** 2项

### 2. 关键变更点及其与项目整体方向的关系

-   **功能新增：支持有效Token动态批处理 (`[data, trainer] feat: support effective-token dynamic batching`)**
    -   **关系：** 这是本次更新的核心。VeOmni的目标是“Scaling Any Modality Model Training”（扩展任意模态模型训练）。动态批处理是提升训练效率和资源利用率的关键技术。通过根据每个样本的“有效Token”数量（而非固定序列长度）来动态组合批次，可以显著减少填充（padding）带来的计算浪费，从而加速多模态模型的训练过程。这直接服务于项目“高效扩展”的核心目标。

-   **Bug修复：修复WAN（Weights & Biases）E2E（端到端）测试的BF16精度问题 (`[ci] fix: run wan e2e in bf16`)**
    -   **关系：** 持续集成（CI）是保证项目稳定性的基石。修复CI测试中的精度问题，确保了在BF16混合精度训练模式下，WAN日志记录和模型评估流程的正确性。这维护了项目在常用训练框架下的可靠性。

-   **Bug修复：修复NPU（神经网络处理器）aarch64架构的依赖解析和UV安装指南 (`[ci] fix: npu aarch64 dependency resolution and uv installation guide`)**
    -   **关系：** 这表明项目正在积极支持非NVIDIA的硬件平台（如华为昇腾NPU）。修复aarch64架构下的依赖问题，并更新安装指南，降低了在国产化硬件上部署VeOmni的门槛。这与项目“Scaling Any Modality”中“Any Hardware”的潜在含义相符，扩大了项目的适用范围和生态影响力。

### 3. 对项目的影响和潜在意义

-   **性能提升：** 有效Token动态批处理是训练优化中的一项重要改进，预计能显著提升多模态模型训练的速度和吞吐量，尤其是在处理文本、图像、视频等长度差异巨大的混合数据时。
-   **稳定性增强：** 修复CI测试和依赖问题，提升了项目的健壮性和可复现性，为开发者提供了更可靠的开发和使用体验。
-   **硬件生态扩展：** 对NPU aarch64的支持，标志着项目正在向更多元的硬件生态迈进，这对于吸引更广泛的用户群体和适应不同部署环境至关重要。

### 4. 值得关注的技术点

-   **有效Token动态批处理 (Effective-Token Dynamic Batching)：** 这是本次更新的技术亮点。它不同于传统的“按序列长度”或“按样本数量”的批处理策略，而是基于每个样本实际参与计算的有效Token数来构建批次。这需要训练框架能够高效地计算和聚合不同样本的有效Token长度，并动态调整计算图。实现这一功能通常需要对数据加载器和训练器进行深度协同优化。
-   **NPU aarch64支持：** 关注其依赖解析的具体方案，以及如何确保在非CUDA架构下的性能与兼容性。这体现了项目在跨平台兼容性上的投入。

### 5. 基于项目背景，这些提交如何影响项目发展

-   **加速核心目标实现：** 动态批处理直接提升了训练效率，使得VeOmni在“扩展任意模态模型训练”的道路上迈出了坚实的一步。它让项目在处理大规模、多模态数据时更具竞争力。
-   **巩固项目成熟度：** CI修复和硬件支持是项目从原型走向成熟产品的关键步骤。它们提升了项目的可靠性和可用性，增强了社区和潜在用户的信心。
-   **拓宽应用场景：** 对NPU的支持，使得VeOmni能够服务于更广泛的用户，尤其是在国内信创和自主可控的背景下，这为项目在特定领域的应用打开了大门。
-   **总结：** 昨日的更新体现了VeOmni项目在**追求极致性能**（动态批处理）和**夯实工程基础**（CI修复、多硬件支持）上的双重努力。前者是项目的核心竞争力，后者是项目可持续发展的保障。两者结合，共同推动VeOmni成为一个更强大、更可靠、更普适的多模态模型训练框架。

## 详细提交记录

### [9cf73e9](https://github.com/ByteDance-Seed/VeOmni/commit/9cf73e98ab1227c01029a1784f1f51bb82059b73)

- **作者**: zhangxin.zzzzz
- **时间**: 2026-06-16T22:21:19Z
- **提交信息**: [data, trainer] feat: support effective-token dynamic batching (#833)

### [a092340](https://github.com/ByteDance-Seed/VeOmni/commit/a092340b2713420cac00ffcb72e581fe74dc7a4b)

- **作者**: 鐘天楽
- **时间**: 2026-06-16T12:40:17Z
- **提交信息**: [ci] fix: run wan e2e in bf16 (#835)

### [81db9bd](https://github.com/ByteDance-Seed/VeOmni/commit/81db9bd36d6a4f98c6a98cf3f87ecc6c4120b17d)

- **作者**: Crystal-jiang
- **时间**: 2026-06-16T09:26:32Z
- **提交信息**: [ci] fix: npu aarch64 dependency resolution and uv installation guide (#832)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-06-17
**监控日期**: 2026-06-16
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2417
- **最后更新**: 2026-06-16T13:46:47Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 2
- **主要提交者**: STwangyingrui, Shankun Wang (王善昆)

## AI分析总结

好的，这是对 `ModelTC/LightX2V` 仓库昨日提交记录的分析总结。

### 1. 主要更新类型

本次更新主要为 **功能新增** 和 **性能优化**。

- **功能新增**：新增了 ProfilerStep GPU 时间线检查工具和 Flux2 PPT 的 Ada Cache 功能。
- **性能优化**：新增了 FlashInfer MoE 自动调优和 PyTorch 分组矩阵乘法 (grouped-MM) MoE 后端。

### 2. 关键变更点及其与项目整体方向的关系

- **`[989b84f]` 添加 ProfilerStep GPU 时间线检查工具**
    - **变更点**：引入了一个独立的跟踪分析器，用于检测 ProfilerStep 中可疑的空闲间隙（基于比率和每次启动预算），并在 TensorBoard 中给出 `ALERT` 提示。
    - **与项目方向关系**：该项目是一个**轻量级视频生成推理框架**，性能分析和调优是核心。该工具直接服务于 **性能诊断**，帮助开发者快速定位推理管线中的瓶颈（如 GPU 空闲等待），符合项目“轻量”和“高效”的目标。

- **`[9c14628]` 为 Flux2 PPT 添加 Ada Cache 功能**
    - **变更点**：为 `Flux2` 模型的 PPT（可能是某种并行或流水线技术）引入了自适应缓存（Ada Cache）。
    - **与项目方向关系**：`Flux2` 是一个流行的图像/视频生成模型。引入自适应缓存是一种典型的 **推理优化** 手段，通过复用中间计算结果来减少计算量，从而**降低延迟、提升吞吐量**。这直接增强了项目对主流模型的支持能力和推理效率。

- **`[97b2320]` 添加 FlashInfer MoE 自动调优和 PyTorch grouped-MM MoE 后端**
    - **变更点**：为混合专家模型（MoE）提供了两种新的后端实现：基于 FlashInfer 的自动调优版本和基于 PyTorch 原生分组矩阵乘法的版本。
    - **与项目方向关系**：MoE 是当前大模型（包括视频生成模型）中提升模型容量和效率的关键架构。提供多种 MoE 后端（特别是自动调优的 FlashInfer 后端）意味着项目在 **适配前沿模型架构** 和 **极致性能优化** 上迈出了重要一步。这有助于项目在处理大规模视频生成任务时，更高效地利用硬件资源。

### 3. 对项目的影响和潜在意义

- **提升可观测性与调试效率**：ProfilerStep 检查工具将帮助开发者和用户更容易地发现推理管线中的性能问题，从“黑盒”走向“白盒”，加速性能优化迭代。
- **增强模型支持与推理速度**：Ada Cache 和 MoE 后端的加入，直接提升了项目对 `Flux2` 等先进模型的支持能力，并显著优化了其推理速度。这对于吸引用户和社区贡献至关重要。
- **夯实技术基础**：通过集成 FlashInfer 等高性能库，项目在底层计算优化上更加扎实，为未来支持更复杂、更大的视频生成模型奠定了性能基础。

### 4. 值得关注的技术点

- **ProfilerStep 空闲间隙分析**：这是一个非常实用的性能分析思路，通过量化“GPU 空闲时间”来定位 CPU 瓶颈或调度问题。
- **Ada Cache（自适应缓存）**：这是一种动态的缓存策略，比静态缓存更灵活，能根据输入或模型状态自适应地决定缓存哪些中间结果，是推理优化的前沿技术。
- **FlashInfer MoE 自动调优**：自动调优意味着系统会根据硬件和模型配置自动选择最优的 MoE 计算内核，避免了手动调优的繁琐，是实现“开箱即用”高性能的关键。
- **PyTorch grouped-MM**：这是 PyTorch 原生支持的一种高效矩阵乘法模式，特别适合 MoE 中不同专家处理不同 token 的场景，能有效减少内存碎片和计算开销。

### 5. 基于项目背景，这些提交如何影响项目发展

- **强化“轻量”与“高效”标签**：这些提交（特别是性能分析和优化）直接回应了项目 README 中“Light Video Generation Inference Framework”的定位。它们不是增加新功能，而是让现有功能跑得更快、更稳、更容易诊断。
- **提升对前沿模型的吸引力**：通过支持 `Flux2` 的 Ada Cache 和 MoE 架构，项目证明了其有能力适配和优化当前最热门的模型架构。这会吸引更多使用 `Flux2` 或类似 MoE 架构模型的开发者关注和使用 `LightX2V`。
- **构建更专业的开发者工具链**：ProfilerStep 检查工具的加入，标志着项目从单纯的推理引擎向包含专业开发工具的平台演进。这有助于降低使用门槛，并提升专业用户的开发体验。
- **为未来扩展铺路**：MoE 和 FlashInfer 的集成，为项目未来支持更大规模、更复杂的视频生成模型（如 Sora 级别的模型）提供了必要的计算基础设施和优化经验。

## 详细提交记录

### [989b84f](https://github.com/ModelTC/LightX2V/commit/989b84f7fd7032f99bac8720b0e2e2dfb9d5a772)

- **作者**: STwangyingrui
- **时间**: 2026-06-16T10:43:45Z
- **提交信息**: Add a tool for ProfilerStep GPU timeline sanity checks (#1156)

Adds a standalone trace linter that flags suspicious ProfilerStep idle
gaps (ratio + per-launch budget); ALERT is a TensorBoard review hint,
not a hard failure.

### [9c14628](https://github.com/ModelTC/LightX2V/commit/9c1462896d429cbd5ee2504587749363961e6263)

- **作者**: Shankun Wang (王善昆)
- **时间**: 2026-06-16T10:33:49Z
- **提交信息**: [feat] Add ada cache for flux2 ppt (#1154)

### [97b2320](https://github.com/ModelTC/LightX2V/commit/97b2320386bf9b276414ace052f3a2450c2fd6ad)

- **作者**: STwangyingrui
- **时间**: 2026-06-16T09:19:40Z
- **提交信息**: add FlashInfer MoE autotune and PyTorch grouped-MM MoE backend (#1153)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-06-17
**监控日期**: 2026-06-16
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2133
- **最后更新**: 2026-06-16T15:19:03Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-06-17
**监控日期**: 2026-06-16
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5801
- **最后更新**: 2026-06-16T19:29:39Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 4
- **主要提交者**: WEI CHENG CHIU, yichengj, Ruoqian Guo

## AI分析总结

好的，以下是对 `flashinfer-ai/flashinfer` 仓库昨日提交记录的分析总结。

### 1. 主要更新类型

- **Bug修复 (Bug Fixes)**: 修复了多CTA radix top-k内核在SM120/SM121架构上的流挂起问题，以及修复了b12x FP4 GEMM中过紧的K维度约束。
- **功能新增 (New Features)**: 为`fused_rmsnorm_silu`算子添加了对非对齐向量化列数的支持；为TensorRT-LLM的FP8/MXFP8 MoE路径添加了可选的SwiGLU激活参数。
- **性能优化 (Performance Optimization)**: 为`fused_rmsnorm_silu`算子新增了针对H100和Blackwell架构的调优查找表。

### 2. 关键变更点及其与项目整体方向的关系

- **修复多CTA Top-K内核流挂起 (Commit 49f2abf)**:
    - **变更点**: 修复了在SM120/SM121 (RTX 5090等) 上，`top_k_mask_logits`等采样内核可能永久挂起的两个根本原因：1) 内核结束时的竞态条件，导致最后一个CTA错误地清除了同步状态；2) 多CTA组无法保证共驻留，在SM压力下可能死锁。
    - **与项目方向关系**: 该项目旨在为推理提供高性能GPU内核。此修复直接解决了影响最新一代GPU架构的严重稳定性问题，确保了FlashInfer在最新硬件上的可用性和可靠性，是项目保持其“高性能”和“生产就绪”承诺的关键。

- **支持非对齐向量化列数的`fused_rmsnorm_silu` (Commit 9dce62e)**:
    - **变更点**: 允许`fused_rmsnorm_silu`内核处理`C=48`等非标准隐藏层大小，这些大小无法被向量化加载完美对齐。同时为H100和Blackwell架构添加了新的性能调优表。
    - **与项目方向关系**: 这增强了算子的通用性和灵活性，使其能适配更多样化的模型架构（如视频VAE），同时通过针对新硬件的调优表保持了高性能。这符合项目支持广泛模型和最新硬件的目标。

- **为MXFP8 MoE添加SwiGLU参数 (Commit 897cddd)**:
    - **变更点**: 为`trtllm_fp8_block_scale_moe`等MoE内核添加了可选的`gemm1_alpha`, `gemm1_beta`, `gemm1_clamp_limit`参数，用于控制每个专家的FC1层SwiGLU激活。
    - **与项目方向关系**: 这是对TensorRT-LLM集成路径的增强，提供了更细粒度的控制能力，以满足特定模型（如使用SwiGLU的模型）的推理需求。这加强了FlashInfer作为主流推理框架（如vLLM、TensorRT-LLM）后端引擎的生态位。

- **放宽b12x FP4 GEMM的K维度约束 (Commit d825c8f)**:
    - **变更点**: 将b12x FP4 GEMM内核的K维度对齐要求从128字节放宽到32字节，允许`K=96, 192`等形状正常工作。
    - **与项目方向关系**: 修复了一个回归问题，恢复了之前支持的形状。这体现了项目对兼容性和正确性的重视，确保新引入的检查不会过度限制用户的使用场景，保持了内核的实用性和鲁棒性。

### 3. 对项目的影响和潜在意义

- **提升稳定性和兼容性**: 修复Top-K挂起问题对vLLM等依赖FlashInfer采样的项目至关重要，可以解除在SM120/121架构上的默认禁用状态，显著提升用户体验。
- **扩展模型支持范围**: 对`fused_rmsnorm_silu`和MoE参数的改进，使得FlashInfer能更好地服务于更广泛的模型架构（如视频模型、使用SwiGLU的MoE模型）。
- **巩固生态地位**: 通过快速响应和修复最新硬件（Blackwell）上的问题，以及深化与TensorRT-LLM的集成，FlashInfer巩固了其作为高性能推理内核库的地位。

### 4. 值得关注的技术点

- **多CTA同步与竞态**: 修复Top-K挂起问题中，对`atom.add`和`wait_ge`等CUDA原子操作和同步原语的深入分析，展示了在复杂GPU内核中处理并发和竞态条件的挑战与技巧。
- **TMA与数据对齐**: 在FP4 GEMM修复中，对TMA（Tensor Memory Accelerator）加载对齐要求的理解，以及如何通过主循环谓词处理非对齐的尾部数据，是GPU编程中的高级技术。
- **硬件特性适配**: 针对SM120/SM121的特定修复，以及为H100和Blackwell添加调优表，体现了项目对不同GPU架构微架构差异的深入理解和针对性优化能力。

### 5. 结合项目背景，这些提交如何影响项目发展

- **巩固“高性能”定位**: 修复了最新硬件上的性能回退和稳定性问题，并针对新硬件添加了调优表，直接兑现了项目“高性能”的承诺。
- **强化“推理”场景**: 所有更新都直接服务于推理场景：采样（Top-K）、归一化（RMSNorm）、MoE（混合专家模型）和矩阵乘法（GEMM）。这些是大型语言模型（LLM）推理的核心

## 详细提交记录

### [49f2abf](https://github.com/flashinfer-ai/flashinfer/commit/49f2abfbdb517e04b14402389213237aa71658e5)

- **作者**: WEI CHENG CHIU
- **时间**: 2026-06-16T19:29:34Z
- **提交信息**: fix(topk): eliminate multi-CTA radix top-k stream hangs on SM120/SM121 (#3615)

> **Update — reduced to the reset-race fix only ("fix 1" / Part A).**
> Per maintainer preference, the occupancy clamp + cooperative-launch
change
> ("fix 2", `RadixTopKClampGroupsToCoResidency` /
`cudaLaunchCooperativeKernel`)
> was **dropped** — it changed launch semantics on every arch and was
the likely
> cause of non-SM120 CI failures. The current diff is
**`include/flashinfer/topk.cuh`
> only** (last-CTA-out barrier reset). The fix-2 discussion below is
kept for
> historical context but is **not** in this PR.

## 📌 Description

Fixes #3610 (closes duplicates #3611, #3612): permanent sampler stream
hangs on SM120/SM121 (RTX 5090 / RTX PRO 6000 / GB10) in the multi-CTA
radix top-k kernels. Also the kernel behind the 12-day-old py-spy trace
in vllm-project/vllm#43885 (`RadixTopKMaskLogitsMultiCTA` never
completing under `CUDA_LAUNCH_BLOCKING=1`), which led vLLM to default
the flashinfer sampler **off** on SM120/121 (vllm-project/vllm#44405).

Two distinct root causes in `include/flashinfer/topk.cuh`:

**1. End-of-kernel reset race (the production hang).** After the
persistent row loop, the *leading* CTA cleared the group's histograms
and zeroed the software barrier's `arrival_counter` — with no
synchronization against peers' final `wait_ge` pass. A peer that arrived
at the last barrier but whose spin-load was delayed (context
time-slicing on consumer/desktop parts makes this routine) then reads `0
< target` and spins forever; the stream wedges at ~96% util / low power,
matching every report in vllm#43885.
*Direct evidence:* back-to-back hammering of `top_k_mask_logits` (batch
256 × vocab 151936, fp32) wedges pre-fix **3/3 runs within ≤3400
calls**, and a side-stream dump of the live `row_states` during the
wedge shows **`arrival_counter == 0` in every group while the kernel is
stuck** — the reset already happened under a spinning waiter. With the
launch queue drained every ≤10 calls, 60k calls never hang — exactly the
"sustained load" signature from the reports.
*Fix:* `RadixGroupResetStateLastCTA` — every CTA marks its exit with a
release-ordered `atom.add` on the same counter; the CTA observing the
final exit is provably the last one out (a CTA only exit-marks after
passing all `wait_ge` spins) and alone clears the histograms (+
deterministic scratch) and resets the counter. Replaces all three reset
sites (MaskLogits / RenormProb / Unified).

**2. Co-residency never guaranteed (latent, deterministic under SM
pressure).** Grid sizing assumed 1 CTA/SM on an idle device; a plain
launch guarantees nothing. With a burner kernel pinning SMs, the
deadlock threshold lands exactly at free SMs < `ctas_per_group` (= 7
here: SM120's 99KB smem/block makes groups 2-4× wider than on SM100's
227KB, which is why these archs live closest to the edge). Two such
kernels on different streams can starve each other permanently, and the
`num_groups==0 → 1` fallback could launch `ctas_per_group > num_sms`
grids that deadlock on an *idle* GPU.
*Fix:* `RadixTopKClampGroupsToCoResidency`
(`cudaOccupancyMaxActiveBlocksPerMultiprocessor`-verified clamp; hard
`cudaErrorCooperativeLaunchTooLarge` instead of a guaranteed hang when
one group can't co-reside) + `LaunchRadixTopKMultiCTAKernel`
(gang-scheduled `cudaLaunchCooperativeKernel`, falling back to plain
launch when the device lacks coop launch **or the stream is capturing**
— CUDA-graph paths keep today's behavior and still get fix 1).

## 🔍 Validation (RTX PRO 6000, SM120, 188 SMs, CUDA 13.0)

| Scenario | pre-fix | post-fix |
|---|---|---|
| back-to-back hammer, 20k calls b256×v151936 | **wedged 3/3 (≤3400
calls)** | **0 hangs in 120k calls (6/6 runs)** |
| 2 streams, mask_logits + renorm_probs ×2000 | **wedged** | completes
1.6s, 6/6 |
| burner holding 182/188 SMs (free < group) | spins until burner exits |
gang launch waits, completes |
| correctness (1..256 × 151936/152064/262144, vs torch.topk) | match |
match |
| `tests/utils/test_topk.py` + `test_sampling.py -k "top_k or topk"` | —
| **1661 passed** |
| perf (gpu ms/call, 4 shapes) | 0.024/0.050/0.365/0.118 |
0.042/0.055/0.356/0.067 (noise-level; +~1µs host launch) |

**Ablation for reviewers:** the reset fix *alone* clears every observed
wedge (hammer 3/3, 2-stream 3/3 with coop launch toggled off). The
occupancy clamp + cooperative launch close the synthetic-but-real
starvation class and the idle-GPU `ctas_per_group > num_sms` case.
Trade-off to weigh: gang scheduling waits for full residency instead of
cascading (the 181-burner case waits ~3.8s rather than trickling at
4.8ms) — if that's a concern for heavily shared GPUs, fix 1 + the
clamp's hard-error can ship standalone; happy to split.

Note for vLLM: once this lands, the SM120/121 default-off in vllm#44405
can be revisited.

## 🧪 Tests

- [x] Tests pass locally (1661 passed; full repro matrix above; repro
scripts available on request)
- [ ] New unit test — the hang requires sustained concurrent launch
pressure that doesn't fit the unit-test harness; validation is via the
deterministic repro scripts documented above. Open to adding a stress
test under an opt-in marker if maintainers want it in-tree.

## Disclosure

AI-assisted (Claude): investigation, fix, and validation runs; the
submitter reviewed every line and the memory-ordering argument.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Improvements**
* Enhanced multi-CTA Top-K kernels with more reliable end-of-round
coordination, improving stability and throughput during synchronized
histogram/state resets.
* Refined host-side multi-CTA launch behavior to improve cooperative
launch selection and robustness.

* **Bug Fixes**
* Prevented potential race conditions and deadlocks by ensuring the
final exiting group performs the required cross-CTA reset work, avoiding
issues when compute groups are only partially resident.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [9dce62e](https://github.com/flashinfer-ai/flashinfer/commit/9dce62e05d475884d569948af12c0028c6e24acc)

- **作者**: xueweilnvidia
- **时间**: 2026-06-16T19:00:05Z
- **提交信息**: Add support for non-multiple VEC_COLS in fused_rmsnorm_silu for bf16/fp8 (#3417)

<!-- .github/pull_request_template.md -->

## 📌 Description
Add support for `C = 48` (and any hidden size whose vectorized column
count is not a multiple of `THREADS_PER_ROW`) in `fused_rmsnorm_silu`.
The bf16/fp8 paths now emit a predicated partial-tail LDG when
`VEC_COLS % VEC_COLS_PER_LDG != 0`; `nvfp4` is unchanged.
  Also add two range-based knob LUTs tuned on video VAE shapes:   
`_KNOB_RANGE_LUT_SM90` (H100, bf16) and `_KNOB_RANGE_LUT_SM100PLUS`
(all Blackwell cards, originally measured on B300). `select_knobs`
consults the exact `_KNOB_LUT` first and falls back to the matching
  range LUT on miss, so previously supported shapes are unaffected.

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

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Prevented out-of-bounds loads/stores and spurious accumulations in
partial-tail kernel paths, preserving correct results for non-divisible
channel counts.

* **New Features**
* Added range-based tuning for newer hardware tiers and adjusted
fallback heuristics; nvfp4 outputs now reject unsupported C sizes (e.g.,
C not divisible by 32).
  * Safer partial-tail handling so bf16/fp8 can cover non-exact tails.

* **Tests**
  * Expanded tests to cover C=48 partial-tail and nvfp4 negative cases.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [897cddd](https://github.com/flashinfer-ai/flashinfer/commit/897cddd68b14aca313ace8773fdb7a47f51c36b8)

- **作者**: Ruoqian Guo
- **时间**: 2026-06-16T18:23:20Z
- **提交信息**: Add MXFP8 MoE SwiGLU OA parameters (#3504)

<!-- .github/pull_request_template.md -->

## 📌 Description

This PR adds optional per-expert FC1 gated-activation parameters to the
TensorRT-LLM FP8 block-scale / MXFP8 MoE path.

Changes include:

- Expose `gemm1_alpha`, `gemm1_beta`, and `gemm1_clamp_limit` on
`trtllm_fp8_block_scale_moe` and `trtllm_fp8_block_scale_routed_moe`.
- Validate the optional tensors as float32 `[local_num_experts]` in the
C++ launcher.
  - Forward the parameters to the trtllm-gen fused FC1 SwiGLU epilogue.
  - Update trace/reference plumbing for the same activation semantics.
- Add an MXFP8 MoE regression test covering default behavior, no-op
parameters, alpha+clamp, and non-default beta behavior.

The new parameters default to `None`, so existing public Python API call
sites preserve the previous behavior.

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

Validation run:

  - `pre-commit run --all-files`
  - `git diff --check`
- `python3.11 -m py_compile tests/moe/test_trtllm_gen_fused_moe.py
flashinfer/fused_moe/core.py flashinfer/trace/templates/moe.py`
- B300:
`tests/moe/test_trtllm_gen_fused_moe.py::test_mxfp8_block_scale_moe_swiglu_oa_activation_params
-q -s`
 

## Reviewer Notes

For MXFP8 block-scale MoE, these values are forwarded as raw per-expert
scalars. FlashInfer does not apply host-side scalar dequant-scale
conversion.

gemm1_beta is included together with gemm1_alpha and gemm1_clamp_limit
because trtllm-gen supports the full fused SwiGLU epilogue parameter
set, and the beta path needs explicit coverage when non-default values
are provided.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* FP8 block-scale MoE adds three optional per-expert SwiGLU parameters
(gemm1_alpha, gemm1_beta, gemm1_clamp_limit) across public APIs, trace
templates, runtime paths, and kernel calls to enable per-expert
activation tuning and optional clamping.
* **Validation**
* Runtime validation ensures these params are only accepted with MxFp8
quantization + SwiGLU and checks device, dtype, shape, contiguity, and
per-expert length.
* **Tests**
* End-to-end and trace tests added for validation, default/no-op, and
alpha/beta/clamp behavior.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Sam (Kesen Li) <lsam@nvidia.com>

### [d825c8f](https://github.com/flashinfer-ai/flashinfer/commit/d825c8f62f2e5c5cf24e8942b66c4f61a5561cf5)

- **作者**: yichengj
- **时间**: 2026-06-16T15:57:40Z
- **提交信息**: fix(gemm): relax b12x FP4 K constraint from 128 to 32 (TMA alignment) (#3646)

## Problem

PR #3560 added a precheck in `_b12x_gemm_fp4_requirement` that rejects
`K` not a multiple of `tile_k = sf_vec_size * 8 = 128`. For explicit
`backend="b12x"` this `raise`s, breaking shapes like **K=192**
(`packed_k=96`):

```
ValueError: b12x FP4 GEMM requires the contraction dim K to be a multiple of 128
(tile_k = sf_vec_size * 8). Got K=192.
```

These shapes ran before #3560.

## Root cause

`K % 128` is the *full MMA K-tile* condition, not the kernel's real
correctness floor. The actual floor is **`K % 32 == 0`**:

- `A` is K-major packed FP4, `(M, K/2)` bytes, loaded via TMA with
`assumed_align=16`, so `K/2 % 16 == 0` → `K % 32 == 0`.
- `K` need **not** divide `tile_k=128`: the mainloop predicates the
partial final K-tile and the swizzled SF layout zero-pads scale-groups,
so ragged K (96, 160, 192, 224, …) computes correctly.

Verified on GB10 (SM121): `cos_sim` 0.98–0.99 for K ∈ {64, 96, 160, 192,
224, 320} across M ∈ {1, 8, 256}, narrow-N (swap_ab), and both autotune
paths; `K % 32 == 16` (e.g. 112, 176) yields garbage and is correctly
rejected.

## Fix

Relax both K guards to `% 32`:

- `_b12x_gemm_fp4_requirement` precheck (gates the non-autotune
default-plan path).
- `DenseGemmKernel.can_implement` (gates the autotune candidate
enumeration).

Both sites move together so the autotune and non-autotune paths accept
the same shapes.

## Tests

`tests/gemm/test_mm_fp4.py`:
- `test_mm_fp4_b12x_ragged_k` — K ∈ {96, 192} × `auto_tuning` ∈ {False,
True} (both `auto_tuning` values exercise the distinct guard paths).
- `test_mm_fp4_b12x_misaligned_k_raises` — K=112 must reject cleanly.

All new tests pass; the 396 existing b12x NVFP4 cases (K=128/256/512)
remain green on SM121.

## Note for reviewers

#3560's precheck mirrored the b12x donor's `can_implement` contract
(which hard-`raise`s on `k % tile_k`). This PR intentionally **extends
past** that contract to `% 32`, justified by the correctness data above
— the kernel's mainloop already handles ragged K via partial-tile
predication.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

## Release Notes

* **New Features**
* Relaxed the b12x FP4 GEMM K-dimension alignment requirement from
multiples of 128 to multiples of 32 to improve support for more matrix
shapes.

* **Tests**
* Added regression coverage for ragged K values across auto-tuning
settings.
* Added a test ensuring misaligned K values are rejected with a clear
“multiple of 32” error (under supported GPU/CUDA conditions).
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-06-17
**监控日期**: 2026-06-16
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3719
- **最后更新**: 2026-06-16T21:36:54Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 1
- **主要提交者**: alexzms

## AI分析总结

好的，这是对 `hao-ai-lab/FastVideo` 仓库昨日提交记录的分析总结。

### 昨日更新要点分析

**1. 主要更新类型**

*   **功能新增 (Feature):** 核心更新，引入了新的注意力机制后端和推理内核。
*   **文档更新 (Documentation):** 伴随功能新增，提供了相应的使用示例和指南。

**2. 关键变更点及其与项目整体方向的关系**

*   **集成 Attn-QAT 推理注意力后端 (88e753f):** 将“注意力量化感知训练 (Attn-QAT)”的推理后端接入项目。这是实现低精度推理的关键一步。
*   **添加修改后的 SageAttention3 FP4 推理内核 (7783205):** 引入了针对 FP4 (4位浮点数) 优化的 `SageAttention3` 内核。这直接服务于在保持模型质量的同时，通过低精度计算加速推理的目标。
*   **添加 NVFP4 + Attn-QAT 推理示例和指南 (c3b9714):** 为上述新功能提供了具体的配置示例和操作步骤，降低了用户的使用门槛。

**与项目方向的关系:** FastVideo 的核心目标是加速视频生成模型的训练和推理。这些提交直接服务于 **推理加速** 这一核心方向，通过引入 **低精度量化 (FP4)** 和 **注意力机制优化 (Attn-QAT, SageAttention3)** 来提升推理效率。

**3. 对项目的影响和潜在意义**

*   **显著提升推理速度:** FP4 精度相比 FP16/FP32 理论上可将内存带宽需求降低 4 倍，结合优化的注意力内核，有望在高端 GPU (如 NVIDIA 5090) 上实现数倍的推理加速。
*   **降低部署成本:** 更低的精度意味着更小的模型内存占用，使得在相同硬件上可以运行更大的模型或同时服务更多用户，从而降低推理成本。
*   **增强项目竞争力:** 率先支持 NVFP4 和 Attn-QAT 等前沿技术，使 FastVideo 在视频生成推理优化领域保持领先地位，吸引对高性能推理有需求的用户。

**4. 值得关注的技术点**

*   **NVFP4:** 这是 NVIDIA 在 Blackwell 架构 (如 RTX 5090) 上引入的新一代低精度浮点格式。项目针对此格式进行优化，表明其紧跟最新硬件特性。
*   **Attn-QAT (注意力量化感知训练):** 这是一种在训练阶段就模拟量化效果的技术，旨在减少量化后模型精度的损失。将其与推理后端集成，是保证 FP4 推理质量的关键。
*   **SageAttention3:** 这是一个特定的、经过修改的注意力机制内核。项目对其进行定制化修改以适配 FP4，说明团队在底层算子优化方面有深入工作。

**5. 基于项目背景，这些提交如何影响项目发展**

*   **从“可用”到“高效”的跨越:** 结合 README 中提到的“快速开始”和“文档”，这些提交标志着项目从提供基础功能，转向提供 **极致性能优化** 的解决方案。特别是针对特定硬件 (5090) 的优化，能吸引拥有该硬件的早期用户和开发者。
*   **构建技术护城河:** 通过集成 NVFP4 和 Attn-QAT 等尚未普及的技术，FastVideo 在技术栈上建立了差异化优势。这有助于在竞争激烈的视频生成工具领域脱颖而出。
*   **推动社区发展:** 详细的示例和指南 (c3b9714) 降低了高级功能的使用门槛，有助于吸引更多开发者进行实验和贡献，形成正向循环的社区生态。

## 详细提交记录

### [c3b9714](https://github.com/hao-ai-lab/FastVideo/commit/c3b971488e2aea78259b39fb0c33b765cde13085)

- **作者**: alexzms
- **时间**: 2026-06-16T21:36:50Z
- **提交信息**: [docs] QAD 5090: Add NVFP4 + Attn-QAT inference example and how-to (9/12) (#1458)

Co-authored-by: William Lin <SolitaryThinker@users.noreply.github.com>
Co-authored-by: Loay Rashid <42599591+loaydatrain@users.noreply.github.com>
Co-authored-by: Kaiqin Kong <k1kong@ucsd.edu>
Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>
Co-authored-by: alexzms <26690162+alexzms@users.noreply.github.com>

### [88e753f](https://github.com/hao-ai-lab/FastVideo/commit/88e753f281063cba53481eadb52aff3c0aa829fb)

- **作者**: alexzms
- **时间**: 2026-06-16T20:12:33Z
- **提交信息**: [feat] QAD 5090: Wire the Attn-QAT inference attention backend (8/12) (#1457)

Co-authored-by: William Lin <SolitaryThinker@users.noreply.github.com>
Co-authored-by: Loay Rashid <42599591+loaydatrain@users.noreply.github.com>
Co-authored-by: Kaiqin Kong <k1kong@ucsd.edu>
Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>
Co-authored-by: alexzms <26690162+alexzms@users.noreply.github.com>

### [7783205](https://github.com/hao-ai-lab/FastVideo/commit/77832059cc176addaf4687852410db7d164e09c5)

- **作者**: alexzms
- **时间**: 2026-06-16T19:02:30Z
- **提交信息**: [kernel] QAD 5090: Add modified SageAttention3 FP4 inference kernels (7/12) (#1455)

Co-authored-by: William Lin <SolitaryThinker@users.noreply.github.com>
Co-authored-by: Loay Rashid <42599591+loaydatrain@users.noreply.github.com>
Co-authored-by: Kaiqin Kong <k1kong@ucsd.edu>
Co-authored-by: Edenzzzz <wtan45@wisc.edu>

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-06-17
**监控日期**: 2026-06-16
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 33874
- **最后更新**: 2026-06-16T22:18:23Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 1
- **主要提交者**: Sayak Paul

## AI分析总结

好的，作为专业的代码分析助手，我将结合 `huggingface/diffusers` 项目的背景，对您提供的提交记录进行分析。

### 提交记录分析总结

#### 1. 主要更新类型

本次更新主要涉及 **Bug修复** 和 **代码回滚**。

#### 2. 关键变更点及其与项目整体方向的关系

*   **`[fd823e8] fix untrusted fork secret mixing (#13970)`**:
    *   **变更点**: 修复了一个与“不可信分支（fork）的密钥混合”相关的安全问题。
    *   **与项目方向的关系**: `diffusers` 是一个开源项目，其CI/CD流程（如GitHub Actions）需要处理来自社区贡献者的Pull Request。这些PR可能来自项目外部的分支（fork）。此修复旨在防止在运行来自不可信源的代码时，项目的重要密钥（如API Token、云服务密钥）被意外泄露或滥用。这直接关系到项目的**安全性**和**社区协作的可靠性**。

*   **`[26ae69b] start` 与 `[4d85a3a] Revert "start"`**:
    *   **变更点**: 一个名为“start”的提交被创建，随后又被立即回滚。
    *   **与项目方向的关系**: 这通常意味着该提交可能是一个实验性、未完成或有问题的改动。回滚操作表明团队决定暂时不引入这个变更，以保持代码库的稳定性和一致性。这体现了项目维护的**严谨性**和**风险控制**。

#### 3. 对项目的影响和潜在意义

*   **安全修复 (`fd823e8`)**:
    *   **直接影响**: 显著提升了项目CI/CD流程的安全性，防止了潜在的供应链攻击或密钥泄露事件。
    *   **潜在意义**: 保护了项目维护者的资产和声誉，也为社区贡献者提供了一个更安全的协作环境。这有助于维持社区对项目的信任，鼓励更多人参与贡献。

*   **代码回滚 (`4d85a3a`)**:
    *   **直接影响**: 代码库恢复到回滚前的稳定状态，避免了潜在的不稳定因素。
    *   **潜在意义**: 表明项目维护者正在谨慎地管理代码变更，确保只有经过充分验证的功能才会被合并。这有助于维护项目长期稳定的发展节奏。

#### 4. 值得关注的技术点

*   **CI/CD安全实践**: `fix untrusted fork secret mixing` 这个提交非常值得关注。它触及了现代开源项目协作中的一个核心安全挑战：如何安全地处理来自不可信外部贡献者的代码。具体技术点可能涉及：
    *   **GitHub Actions 的 `pull_request_target` 事件**：该事件允许访问仓库的密钥，但需要特别小心处理，以防止恶意代码窃取密钥。
    *   **环境变量隔离**：确保在运行来自fork的代码时，敏感的环境变量不会被意外暴露。
    *   **代码审查与沙箱执行**：在安全的环境中审查和测试来自fork的代码。

#### 5. 基于README背景，这些提交如何影响项目发展

*   **强化项目基础设施**: `diffusers` 作为一个旨在让AI模型（特别是扩散模型）更易用的库，其发展高度依赖于一个活跃、健康的社区。这次的安全修复直接加固了支撑社区协作的CI/CD基础设施，为项目未来的大规模社区贡献扫清了安全障碍。
*   **维护项目稳定性**: 回滚操作虽然看似微小，但体现了项目维护者对代码质量的高要求。在快速迭代的AI领域，这种对稳定性的坚持是项目能够长期可靠运行、赢得用户信赖的关键。它确保了 `diffusers` 库的每一次发布都是经过深思熟虑的，而不是仓促的。
*   **总结**: 昨日的更新虽然数量不多，但意义重大。它表明 `diffusers` 项目在积极推动功能发展的同时，**高度重视安全性和稳定性**。这为项目的长期健康发展奠定了坚实的基础。

## 详细提交记录

### [4d85a3a](https://github.com/huggingface/diffusers/commit/4d85a3ae7fcb26158a3d88c356198dd8f8d4d910)

- **作者**: Sayak Paul
- **时间**: 2026-06-16T13:10:11Z
- **提交信息**: Revert "start"

This reverts commit 26ae69b11caa4066717fd4472ff7715668b6924e.

### [26ae69b](https://github.com/huggingface/diffusers/commit/26ae69b11caa4066717fd4472ff7715668b6924e)

- **作者**: Sayak Paul
- **时间**: 2026-06-16T13:09:53Z
- **提交信息**: start

### [fd823e8](https://github.com/huggingface/diffusers/commit/fd823e825c0b8ea929d7175504d564e197e44364)

- **作者**: Sayak Paul
- **时间**: 2026-06-16T07:57:23Z
- **提交信息**: fix untrusted fork secret mixing (#13970)

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-06-17
**监控日期**: 2026-06-16
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 416
- **最后更新**: 2026-06-16T09:13:18Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-06-17
**监控日期**: 2026-06-16
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12587
- **最后更新**: 2026-06-16T17:18:14Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-06-17
**监控日期**: 2026-06-16
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 29082
- **最后更新**: 2026-06-16T22:52:20Z

## 提交统计

- **昨日提交总数**: 22
- **提交者数量**: 19
- **主要提交者**: JINO ROHIT, ashwini rathi, Bingxu Chen

## AI分析总结

好的，这是对仓库 `sgl-project/sglang` 昨日提交记录的分析总结：

### 1. 主要更新类型

- **Bug修复**: 修复了多个关键问题，包括服务器崩溃、导入错误、模型加载失败等。
- **功能新增**: 引入了线性规划负载均衡器、非对称池后端支持、AMD GPU的上下文并行支持等新特性。
- **性能优化**: 优化了AMD GPU上的共享专家门控计算、Wan2.2模型的编译模式。
- **文档更新**: 新增了Amazon SageMaker部署指南、GLM-5.2模型部署教程，并更新了README。
- **重构**: 清理了`UnifiedTree`中的死代码，引入了上下文并行策略抽象层。
- **测试**: 启用了Marlin NVFP4测试，并增加了AMD DeepSeek V4 FlashMLA的夜间测试。

### 2. 关键变更点及其与项目整体方向的关系

- **硬件生态扩展 (AMD/XPU)**:
    - `[AMD] Feat: Add prefill context parallel support for deepseek v4 unified kv attention` (#27928): 为AMD GPU增加了DeepSeek V4模型的预填充上下文并行支持，这是对AMD硬件支持的重要扩展。
    - `[AMD] Fuse sigmoid + mul into single Triton kernel for shared expert gating` (#27636): 通过融合内核优化AMD GPU上的共享专家门控性能。
    - `[XPU] Guard tvm_ffi import in dsv4 compress modules under TYPE_CHECKING` (#28426): 修复了XPU后端的一个导入问题。
    - **关系**: 这些提交直接响应了README中提到的“支持多种硬件后端”的目标，特别是对AMD和XPU等非NVIDIA硬件的支持，扩大了项目的适用范围。

- **模型支持与优化 (DeepSeek V4, GLM-5.2, Wan2.2)**:
    - `[HiCache]Asymmetric pool support direct backend` (#28446): 为HiCache（推测是高性能缓存）增加了非对称池的直接后端支持，可能用于优化大模型推理的内存管理。
    - `LPLB: linear-programming load balancer for MoE expert parallelism` (#24515): 为MoE（混合专家）模型引入了一个基于线性规划的负载均衡器，旨在优化专家并行时的计算负载。
    - `docs(cookbook): add GLM-5.2 deployment cookbook` (#28437) 及相关文档更新: 提供了GLM-5.2模型的部署指南，并优化了其启动参数。
    - `[perf] Use default torch compile mode for Wan2.2 T2V A14B` (#28304): 优化了Wan2.2视频生成模型的性能。
    - **关系**: 这些更新表明项目正积极支持最新的、复杂的模型架构（如MoE、MTP），并为其提供专门的优化和部署方案，这与README中“为各种模型提供高性能推理”的核心目标一致。

- **稳定性与可靠性提升**:
    - `[Tokenizer] Fix abort racing server crash when large amount of aborts` (#28341): 修复了大量请求中止时导致服务器崩溃的竞态条件问题，显著提升了服务稳定性。
    - `fix: get_processor fails when --tokenizer-path lacks model config.json` (#25643): 修复了当tokenizer路径缺少配置文件时的加载失败问题。
    - `fix(openai): validate assistant tool call arguments before chat template` (#28035): 修复了OpenAI兼容API中工具调用参数验证的问题。
    - **关系**: 这些Bug修复直接提升了项目的健壮性和用户体验，是项目走向成熟和可部署的关键。

- **架构与代码质量**:
    - `[2/n] [CP] Add context parallel strategy abstractions` (#27313): 引入了上下文并行策略的抽象层，这是对并行计算架构的模块化重构，便于未来扩展和维护。
    - `[UnifiedTree]: Clean up some unused dead code.` (#28389): 清理无用代码，提升代码库质量。
    - **关系**: 这些重构工作为项目未来的功能迭代和性能优化奠定了更坚实的基础，体现了项目在快速发展中对代码质量的重视。

### 3. 对项目的影响和潜在意义

- **扩大硬件生态**: 对AMD和XPU的持续支持，将使SGLang能够服务于更广泛的用户群体，降低对单一硬件厂商的依赖。
- **增强模型竞争力**: 对DeepSeek V4、GLM-5.2等前沿模型的专门优化和部署指南，将吸引更多使用这些模型的开发者和企业。
- **提升生产环境可靠性**: 修复服务器崩溃和API兼容性问题，是SGLang从研究原型走向生产级部署的关键一步。
- **优化MoE模型性能**: 线性规划负载均衡器是解决MoE模型负载不均问题的先进方案，有望显著提升这类模型的推理吞吐量和效率。
- **促进社区发展**: 丰富的文档（如SageMaker指南）和清晰的代码结构（如CP抽象）降低了新用户和贡献者的参与门槛。

### 4. 值得关注的技术点

- **线性规划负载均衡器 (LPLB)**: 这是一个非常值得关注的技术点。它使用数学优化方法（线性规划）来解决MoE专家并行中的负载均衡问题，相比传统的启发式方法，理论上能实现更优的全局负载分配。
- **非对称池 (Asymmetric Pool)**: 在HiCache中引入非对称池的直接后端，可能是一种新的内存管理策略，用于更高效地处理不同大小和生命周期的

## 详细提交记录

### [4f9b12c](https://github.com/sgl-project/sglang/commit/4f9b12c5ddad5d4d36f9392496e1e2966208c1bf)

- **作者**: ashwini rathi
- **时间**: 2026-06-16T22:52:12Z
- **提交信息**: [XPU] Guard tvm_ffi import in dsv4 compress modules under TYPE_CHECKING (#28426)

### [a10eee3](https://github.com/sgl-project/sglang/commit/a10eee3d80516f8e0d3466856c4be8d542d93b7a)

- **作者**: Hanming Lu
- **时间**: 2026-06-16T21:49:35Z
- **提交信息**: [Tokenizer] Fix abort racing server crash when large amount of aborts (#28341)

### [b8b8992](https://github.com/sgl-project/sglang/commit/b8b8992dde96e964b9c0734fb67b216c4838c06d)

- **作者**: Jyothirmai Kottu
- **时间**: 2026-06-16T20:33:22Z
- **提交信息**: docs: add Amazon SageMaker AI deployment guide (#28338)

### [9b4432f](https://github.com/sgl-project/sglang/commit/9b4432fe18be01d62fdc3aefe16c155cc9d96a95)

- **作者**: huangtingwei
- **时间**: 2026-06-16T20:17:57Z
- **提交信息**: [HiCache]Asymmetric pool support direct backend (#28446)

### [c0a6c3c](https://github.com/sgl-project/sglang/commit/c0a6c3ce66a055a644c3a4bbc49a92f98d74af2b)

- **作者**: Jason Mancuso
- **时间**: 2026-06-16T19:04:34Z
- **提交信息**: Fix circular import when sglang.srt.model_executor.runner_backend is imported first (#28002)

### [13537f8](https://github.com/sgl-project/sglang/commit/13537f8e207ed9d970128667142e6f297bc21f32)

- **作者**: Brayden Zhong
- **时间**: 2026-06-16T18:58:22Z
- **提交信息**: Unskip Marlin NVFP4 tests (#27589)

Co-authored-by: Brayden Zhong <brayden@radixark.ai>
Co-authored-by: shaunkotek <shaunkotek@users.noreply.github.com>

### [33f205d](https://github.com/sgl-project/sglang/commit/33f205d8c5b210861996f294f42e994946ba4e37)

- **作者**: Xinyuan Tong
- **时间**: 2026-06-16T18:17:34Z
- **提交信息**: docs(cookbook): fix GLM-5.2 thinking toggle kwarg + document reasoning effort (#28454)

### [799584e](https://github.com/sgl-project/sglang/commit/799584e1733cee80c6eeb9a08723c1126b8e5e26)

- **作者**: JINO ROHIT
- **时间**: 2026-06-16T17:25:05Z
- **提交信息**: fix:  get_processor fails when --tokenizer-path lacks model config.json (#25643)

Co-authored-by: github-actions[bot] <github-actions[bot]@users.noreply.github.com>
Co-authored-by: ronnie_zheng <zl19940307@163.com>

### [92b42c8](https://github.com/sgl-project/sglang/commit/92b42c8d8adedb4f0ad6436cb98f3c1a5d767b91)

- **作者**: feliang-git
- **时间**: 2026-06-16T17:19:42Z
- **提交信息**: LPLB: linear-programming load balancer for MoE expert parallelism (#24515)

Co-authored-by: xutizhou <xutingz@nvidia.com>

### [00081a0](https://github.com/sgl-project/sglang/commit/00081a00d5b3b8111df81151db7cbd518612c549)

- **作者**: Xinyuan Tong
- **时间**: 2026-06-16T17:18:34Z
- **提交信息**: docs(cookbook): tune GLM-5.2 MTP to 5-1-6 and simplify launch flags (#28448)

### [78b6a4f](https://github.com/sgl-project/sglang/commit/78b6a4fabfb49f9afb24c9fbb7fb70cf6fe35d72)

- **作者**: Zhangheng
- **时间**: 2026-06-16T13:53:35Z
- **提交信息**: [UnifiedTree]: Clean up some unused dead code. (#28389)

### [0cb6183](https://github.com/sgl-project/sglang/commit/0cb6183432dc98b89dd9994cb8db04494c267721)

- **作者**: Xinyuan Tong
- **时间**: 2026-06-16T13:49:25Z
- **提交信息**: docs(cookbook): add GLM-5.2 deployment cookbook (#28437)

### [265202c](https://github.com/sgl-project/sglang/commit/265202cda251bd466930f132ce7ca3b45cf33697)

- **作者**: xianzhiT
- **时间**: 2026-06-16T12:21:23Z
- **提交信息**: fix(openai): validate assistant tool call arguments before chat template (#28035)

Co-authored-by: Xinyuan Tong <115166877+JustinTong0323@users.noreply.github.com>
Co-authored-by: Xinyuan Tong <xinyuantong.cs@gmail.com>

### [fcca461](https://github.com/sgl-project/sglang/commit/fcca4611fa516e2955b787e417ded5a6ff8fcad9)

- **作者**: Yinghai Lu
- **时间**: 2026-06-16T11:49:05Z
- **提交信息**: [CAR] Let custom allreduce support VMM based allocation (#27593)

Co-authored-by: Lianmin Zheng <lianminzheng@gmail.com>

### [12ebb35](https://github.com/sgl-project/sglang/commit/12ebb35439e94724719b1ab790ceab5c3d5b5569)

- **作者**: sglang-bot
- **时间**: 2026-06-16T10:45:10Z
- **提交信息**: docs: refresh README News section and add Modal to adoption list (#28330)

Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>

### [25e696a](https://github.com/sgl-project/sglang/commit/25e696aa8d98bde8bbca90be5cc66b1653eff5ce)

- **作者**: Brayden Zhong
- **时间**: 2026-06-16T09:39:17Z
- **提交信息**: Fix Stage B CUDA CI (#28367)

Co-authored-by: Brayden Zhong <brayden@radixark.ai>

### [a362ba9](https://github.com/sgl-project/sglang/commit/a362ba9da37ef84d7c4a5ece47a94d328f6deb0b)

- **作者**: Wang, FangYuan
- **时间**: 2026-06-16T09:00:51Z
- **提交信息**: [AMD] Feat: Add prefill context parallel support for deepseek v4 unified kv attention (#27928)

Co-authored-by: Thomas Wang <thomawan@amd.com>

### [149fabc](https://github.com/sgl-project/sglang/commit/149fabcca7fae30ec96ef44adadc7f6a27bb6277)

- **作者**: jacky.cheng
- **时间**: 2026-06-16T08:16:58Z
- **提交信息**: [AMD] Fuse sigmoid + mul into single Triton kernel for shared expert gating (#27636)

### [102392d](https://github.com/sgl-project/sglang/commit/102392df5b71b71992f43701567747194f274daf)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-06-16T08:13:22Z
- **提交信息**: [AMD][Fix] Skip EPLB topk remap when global server args are unset (#28404)

### [0fc2bc4](https://github.com/sgl-project/sglang/commit/0fc2bc4a8bb451b435818dbd4c775312d9f8bcf9)

- **作者**: Bingxu Chen
- **时间**: 2026-06-16T08:03:26Z
- **提交信息**: [AMD] Test DeepSeek V4 FlashMLA backend variants nightly (#28290)

### [c5b9106](https://github.com/sgl-project/sglang/commit/c5b9106c1aaf82648d9ea000b44ed470bb020715)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-06-16T07:45:00Z
- **提交信息**: [perf] Use default torch compile mode for Wan2.2 T2V A14B (#28304)

### [77f327c](https://github.com/sgl-project/sglang/commit/77f327cb6e810d5a0f149f4d8727eb0558e5cf16)

- **作者**: Baizhou Zhang
- **时间**: 2026-06-16T07:20:04Z
- **提交信息**: [2/n] [CP] Add context parallel strategy abstractions (#27313)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-06-17
**监控日期**: 2026-06-16
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1203
- **最后更新**: 2026-06-16T12:40:07Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

好的，根据您提供的仓库README摘要和提交记录，以下是昨日更新的分析总结：

### 1. 主要更新类型
- **文档更新**：更新了README.md文件。
- **功能新增**：添加了技术报告（tech report）。

### 2. 关键变更点及其与项目整体方向的关系
- **提交 `077a92c` (Update README.md)**：对项目的主文档README进行了更新。这通常是为了反映项目的最新状态、功能或使用方式。
- **提交 `840c4e0` (chore: add cache-dit tech report)**：为项目添加了技术报告。技术报告是项目核心算法、架构和性能的详细阐述。

**与项目方向的关系**：这两个提交都直接服务于项目的**推广、透明度和学术严谨性**。README是项目的门面，技术报告则深入解释了“cache-dit”这个PyTorch原生推理引擎的核心技术（如缓存、并行、量化、CPU卸载）是如何实现的。

### 3. 对项目的影响和潜在意义
- **提升项目可信度与影响力**：添加技术报告是开源项目走向成熟和学术化的重要一步。它向潜在用户和贡献者证明了项目的技术深度和严谨性，有助于吸引更多关注和贡献。
- **降低使用门槛**：更新README可以更好地引导新用户快速上手，了解项目的最新特性和使用方法。
- **促进社区交流**：技术报告为社区讨论提供了坚实的理论基础，用户和开发者可以基于报告内容提出更深入的问题或改进建议。

### 4. 值得关注的技术点
- **技术报告内容**：虽然提交记录未显示报告的具体内容，但可以推断该报告很可能详细阐述了`cache-dit`的核心创新点，例如：
    - 如何实现高效的**缓存机制**以加速DiT推理。
    - 如何利用**并行化**技术（如张量并行、序列并行）提升吞吐量。
    - **量化**策略（如INT8/FP8）在保持模型质量的同时降低显存和计算开销。
    - **CPU卸载**（CPU Offload）技术，使得超大模型能够在有限显存下运行。
- **README更新细节**：需要查看具体的README diff，了解是否新增了安装指南、快速开始示例、性能基准测试结果或API文档链接。

### 5. 基于项目背景，这些提交如何影响项目发展
根据README，`cache-dit` 的目标是成为一个 **“PyTorch-native”** 的DiT推理引擎，专注于**缓存、并行、量化和CPU卸载**。昨日更新对项目发展的影响如下：

- **从“可用”到“可信”**：技术报告的发布标志着项目从提供代码工具的阶段，进入了提供**理论支撑和性能验证**的阶段。这对于一个旨在成为行业标准推理引擎的项目至关重要。
- **强化“PyTorch-native”定位**：技术报告可以详细解释如何在不依赖过多外部库的情况下，利用PyTorch的原生特性实现高性能推理，这进一步巩固了其“PyTorch-native”的独特卖点。
- **加速社区采纳**：清晰的README和权威的技术报告是开发者决定是否采用一个开源项目的关键因素。这些更新将直接降低潜在用户（如AI研究员、工程师）的决策成本，推动`cache-dit`在DiT推理领域的应用。

## 详细提交记录

### [077a92c](https://github.com/vipshop/cache-dit/commit/077a92cf9b12ce2b3cc6d82d6ba66434d389eef1)

- **作者**: DefTruth
- **时间**: 2026-06-16T12:39:45Z
- **提交信息**: Update README.md

### [840c4e0](https://github.com/vipshop/cache-dit/commit/840c4e0429020a0019a0e8a7bc81a7da4c3d7608)

- **作者**: DefTruth
- **时间**: 2026-06-16T12:38:57Z
- **提交信息**: chore: add cache-dit tech report (#1062)

* chore: add cache-dit tech report

* chore: add cache-dit tech report

* chore: add cache-dit tech report

* chore: add cache-dit tech report

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-06-17
**监控日期**: 2026-06-16
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 83087
- **最后更新**: 2026-06-16T23:45:12Z

## 提交统计

- **昨日提交总数**: 39
- **提交者数量**: 38
- **主要提交者**: Dao007forever, Stan Wozniak, Song Zhixin

## AI分析总结

好的，作为专业的代码分析助手，以下是对 vllm-project/vllm 仓库昨日提交记录的分析总结。

### 项目背景回顾

根据 README，vLLM 的目标是提供“**简单、快速、便宜的 LLM 服务**”。这意味着项目的核心发展方向是：
1.  **性能与效率**：追求更低的延迟、更高的吞吐量、更优的显存利用。
2.  **硬件支持**：支持多种硬件平台（NVIDIA GPU, AMD ROCm, Intel XPU, Google TPU 等）。
3.  **模型兼容性**：支持越来越多的主流和新兴 LLM 架构。
4.  **易用性与稳定性**：提供稳定的 API、清晰的文档和可靠的 Bug 修复。

---

### 昨日更新要点总结

#### 1. 主要更新类型

-   **Bug修复 (Bugfix)**：数量最多，涉及模型推理、内存管理、工具调用等多个方面。
-   **功能新增 (Feature)**：包括新模型支持、新硬件内核、新前端功能（如流式解析器）。
-   **性能优化 (Perf)**：针对特定场景（如多GPU、Triton编译）的加速。
-   **硬件/平台支持**：大量针对 AMD ROCm、Intel XPU、NVIDIA Helion 等平台的适配与优化。
-   **重构与清理 (Refactor/Cleanup)**：移除过时代码、清理测试用例。
-   **文档与CI (Docs/CI)**：新增平台文档、修复CI测试。

#### 2. 关键变更点及其与项目方向的关系

-   **新模型与架构支持**：
    -   **`[Model] Add HrmTextForCausalLM`**：新增对“分层推理模型”的支持，扩展了vLLM能服务的模型生态。
    -   **`[Kernel] Support DS Mamba tail copy for MTP`** & **`[Kernel] Support GLM-5 dimensions for TRT-LLM ragged MLA prefill`**：为 Mamba、GLM 等非Transformer架构或特殊注意力机制（MLA）提供底层内核支持，体现了vLLM紧跟前沿模型架构的趋势。
    -   **`[Frontend] Add Streaming Parser Engine and new MinimaxM2 Parser`**：新增流式解析引擎，支持更复杂的输出格式（如MiniMax M2），提升了对特定模型和场景的兼容性。

-   **性能与效率提升**：
    -   **`[PERF] Fuse multi-group block table staged writes`**：通过融合内存写操作来优化性能，直接服务于“快”和“便宜”的目标。
    -   **`[Perf] Add VLLM_TRITON_FORCE_FIRST_CONFIG to skip Triton autotuning`**：允许跳过耗时的Triton自动调优，加速首次启动，提升用户体验。
    -   **`[MM][Perf][CG] Support dual-path ViT full CUDA graph for DeepSeek-OCR`**：为多模态模型（DeepSeek-OCR）优化CUDA图，提升视觉部分的推理速度。
    -   **`[Core] Add prefill step cadence for better non-PD DP balancing`**：优化非PD分离场景下的数据并行负载均衡，提升整体吞吐。

-   **硬件生态扩展**：
    -   **`[ROCm]` 系列提交**：修复CI、优化量化内核（MXFP8）、清理代码，持续巩固对AMD GPU的支持。
    -   **`[XPU][CI]`**：为Intel XPU添加CI测试，表明vLLM正在积极拓展Intel硬件生态。
    -   **`[Kernel][Helion]`**：新增对NVIDIA Helion平台的内核支持，这是对特定硬件架构的深度优化。
    -   **`[ZenCPU]`**：新增AMD Zen CPU平台的运行时日志和文档，拓展了在CPU上的部署能力。

-   **稳定性与Bug修复**：
    -   **`[Bugfix] Gemma4: skip forced JSON`** & **`[Bugfix] Fix Qwen3 prompt tool-call reasoning`**：修复了Gemma4和Qwen3等热门模型在工具调用功能上的问题，直接提升了用户体验和模型兼容性。
    -   **`[Bugfix][Core] Fall back when numactl --membind is blocked`**：修复了在受限容器环境下的兼容性问题，增强了部署的鲁棒性。
    -   **`[Bugfix] Prevent cuMemcpyBatchAsync segfault with MTP and KV offloading`**：修复了MTP（多Token预测）与KV Cache卸载结合使用时的严重崩溃问题，提升了系统稳定性。

#### 3. 对项目的影响和潜在意义

-   **巩固领先地位**：通过持续支持新模型（如Mamba, GLM, Hierarchical Reasoning Model）和优化性能，vLLM保持了其在LLM推理服务框架中的领先地位。
-   **扩大硬件覆盖**：对AMD、Intel、NVIDIA新平台（Helion）的投入，使vLLM能服务于更广泛的用户群体，降低了对单一硬件厂商的依赖。
-   **提升企业级可用性**：大量Bug修复，特别是针对工具调用、容器部署、多GPU场景的修复，显著提升了vLLM在生产环境中的稳定性和可靠性。
-   **降低使用门槛**：`VLLM_TRITON_FORCE_FIRST_CONFIG` 这样的优化直接改善了开发者和用户的首次使用体验。

#### 4

## 详细提交记录

### [4bf699d](https://github.com/vllm-project/vllm/commit/4bf699d310300edf1df2df2713e3d6516438a798)

- **作者**: sungsoo ha
- **时间**: 2026-06-16T22:50:30Z
- **提交信息**: [Kernel] Support DS Mamba tail copy for MTP align mode (#45473)

Signed-off-by: Sungsoo Ha <sungsooh@nvidia.com>
Co-authored-by: Thomas Parnell <tom.parnell@gmail.com>

### [5208287](https://github.com/vllm-project/vllm/commit/520828789c38acfeefc3095c810e3148b76bac03)

- **作者**: Stan Wozniak
- **时间**: 2026-06-16T21:49:15Z
- **提交信息**: Apply LRU policy only to proper cache entries (#42656)

Signed-off-by: Stanislaw Wozniak <stw@zurich.ibm.com>

### [9d4dc4c](https://github.com/vllm-project/vllm/commit/9d4dc4ca2fefae1a19648d7989f1dffb351e1b29)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-06-16T20:49:47Z
- **提交信息**: [Kernel] Support GLM-5 dimensions for TRT-LLM ragged MLA prefill (#43525)

Signed-off-by: Mohammad Miadh Angkad <176301910+mmangkad@users.noreply.github.com>
Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Matthew Bonanni <mbonanni@redhat.com>

### [b9684d9](https://github.com/vllm-project/vllm/commit/b9684d99e9ba50e06e375d7f1c63083e1e9286f7)

- **作者**: Federico
- **时间**: 2026-06-16T20:38:29Z
- **提交信息**: [Bugfix] Gemma4: skip forced JSON for required/named tool choice (#45795)

Signed-off-by: Federico Iezzi <fiezzi@google.com>

### [4fadf9c](https://github.com/vllm-project/vllm/commit/4fadf9c92c203ac4745caadfaac0ff4e6fe0806e)

- **作者**: Divakar Verma
- **时间**: 2026-06-16T20:31:52Z
- **提交信息**: [ROCm][CI] fix multimodel run cmds (#45858)

Signed-off-by: Divakar Verma <divakar.verma@amd.com>

### [d8d9599](https://github.com/vllm-project/vllm/commit/d8d95998dcb261229369eaae28c4413268ea803d)

- **作者**: Nick Hill
- **时间**: 2026-06-16T20:17:18Z
- **提交信息**: [Core] Add prefill step cadence for better non-PD DP balancing (#44558)

Signed-off-by: Nick Hill <nickhill123@gmail.com>

### [475a6ad](https://github.com/vllm-project/vllm/commit/475a6ad18adf63bd1ab46d5034b2d7fd67065836)

- **作者**: Flora Feng
- **时间**: 2026-06-16T19:08:00Z
- **提交信息**: [Misc] Update Mergify tool-calling label  (#45853)

Signed-off-by: sfeng33 <4florafeng@gmail.com>

### [f2beaa8](https://github.com/vllm-project/vllm/commit/f2beaa80c8d672dc45c3313e0c8b2cec5a9b3ee3)

- **作者**: Hongxia Yang
- **时间**: 2026-06-16T18:50:40Z
- **提交信息**: [ROCm][Quant] mxfp8 moe/linear gfx950 tuning for MiniMax-M3 (#45725)

Signed-off-by: Hongxia Yang <hongxia.yang@amd.com>

### [8e27a9c](https://github.com/vllm-project/vllm/commit/8e27a9c215560ad700036ad4b4d32676d61ef4b1)

- **作者**: Song Zhixin
- **时间**: 2026-06-16T17:53:27Z
- **提交信息**: [PERF] Fuse multi-group block table staged writes (#44944)

Signed-off-by: jesse <szxfml@gmail.com>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>

### [7d56717](https://github.com/vllm-project/vllm/commit/7d567172fcb7fe92bef7d129b1280919acf153dd)

- **作者**: alexbi29
- **时间**: 2026-06-16T17:48:01Z
- **提交信息**: [Bugfix] Fix Qwen3 prompt tool-call reasoning false positive (#45763)

Signed-off-by: Alex Bilichenko <alexbi29@users.noreply.github.com>
Co-authored-by: Alex Bilichenko <alexbi29@users.noreply.github.com>

### [f00e163](https://github.com/vllm-project/vllm/commit/f00e163f3562f9587d564ec4ffa3cb32d7a05403)

- **作者**: Chauncey
- **时间**: 2026-06-16T17:38:17Z
- **提交信息**: [Frontend] Add Streaming Parser Engine and new MinimaxM2 Parser (#45701)

Signed-off-by: chaunceyjiang <chaunceyjiang@gmail.com>

### [44b2512](https://github.com/vllm-project/vllm/commit/44b25127670b16bd5c1e06a093ddd0f137c868dc)

- **作者**: Dao007forever
- **时间**: 2026-06-16T17:24:20Z
- **提交信息**: [KV Connector][Mooncake] Add cache_prefix to namespace store keys (#45767)

Signed-off-by: Dao Le <Dao007forever@gmail.com>
Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [188c687](https://github.com/vllm-project/vllm/commit/188c68798e26c89f4cdb30eaa79dfb96bf8b11f1)

- **作者**: kourosh hakhamaneshi
- **时间**: 2026-06-16T17:18:37Z
- **提交信息**: [KVConnector][MoRIIO] Allow overriding the advertised host IP (#45488)

Signed-off-by: Kourosh Hakhamaneshi <kourosh@anyscale.com>
Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [c45f681](https://github.com/vllm-project/vllm/commit/c45f681932838dda6365e1a4aa1f7092aca97bf9)

- **作者**: Ting SUN
- **时间**: 2026-06-16T16:49:56Z
- **提交信息**: [Bugfix][Core] Fall back when numactl --membind is blocked in constrained containers (#45438)

Signed-off-by: Ting Sun <suntcrick@gmail.com>
Co-authored-by: Shengqi Chen <harry-chen@outlook.com>

### [89e8645](https://github.com/vllm-project/vllm/commit/89e8645a9e5970367e363ce42d664f577b7b4246)

- **作者**: Tiezhen WANG
- **时间**: 2026-06-16T16:32:18Z
- **提交信息**: [Model] Remove Dots1ForCausalLM (#45637)

Signed-off-by: Xianbao QIAN <xianbao.qian@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [88a9cdd](https://github.com/vllm-project/vllm/commit/88a9cdd4397932aa189b9999b346f5cde427ef1e)

- **作者**: Wentao Ye
- **时间**: 2026-06-16T16:31:32Z
- **提交信息**: [Model Runner V2] Enable GraniteMOE for MRv2 by default (#45461)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [6f612fb](https://github.com/vllm-project/vllm/commit/6f612fbedff718af2dabb93692f00044e66a9b4b)

- **作者**: Micah Williamson
- **时间**: 2026-06-16T15:00:15Z
- **提交信息**: [ROCm][CI] Patch conftest to resolve occasional OOMs (#45722)

Signed-off-by: Micah Williamson <micah.williamson@amd.com>

### [506ec6d](https://github.com/vllm-project/vllm/commit/506ec6d656bb9d07a4dc2640956b06cd17e4a8dc)

- **作者**: Sting Lin
- **时间**: 2026-06-16T14:54:57Z
- **提交信息**: Upgrade tpu-inference to v0.22.1 (#45793)

### [a52205b](https://github.com/vllm-project/vllm/commit/a52205bccfc7c270dd445cf253f18deb3778e334)

- **作者**: yifei wu
- **时间**: 2026-06-16T14:41:41Z
- **提交信息**: [Model] Add HrmTextForCausalLM (Hierarchical Reasoning Model — Text) (#43098)

Signed-off-by: Wuyifei <wuyifei@me.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [3d34f8c](https://github.com/vllm-project/vllm/commit/3d34f8cbdcc9545571f5c2ec78e0327b1e5779e4)

- **作者**: Tuukka Sarvi
- **时间**: 2026-06-16T14:28:06Z
- **提交信息**: [ROCm][Cleanup] Remove stale AITER FA hybrid KV-cache TODO (#44178)

Signed-off-by: Tuukka Sarvi <tuukka.sarvi@amd.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>

### [eb04c76](https://github.com/vllm-project/vllm/commit/eb04c769d38d0f39160bd1a2c5279359519de802)

- **作者**: Carl Y
- **时间**: 2026-06-16T14:10:59Z
- **提交信息**: feat: MLA prefill enable FA4 fp8 output (#43050)

Signed-off-by: Carl You <4531192+carlyou@users.noreply.github.com>

### [ce3ef17](https://github.com/vllm-project/vllm/commit/ce3ef17bec12cd3fc4fbecf2902ea54f22d3a953)

- **作者**: Xiaohong (Sean) Chen
- **时间**: 2026-06-16T14:09:52Z
- **提交信息**: [Kernel][Helion][1/N] Add Helion kernel for rms_norm_per_block_quant (#36895)

Signed-off-by: Sean Chen <seachen@redhat.com>
Co-authored-by: Yanan Cao <gmagogsfm@gmail.com>

### [bf5149b](https://github.com/vllm-project/vllm/commit/bf5149b51606dc567503684905705cc26427f099)

- **作者**: Ajay Anubolu
- **时间**: 2026-06-16T14:09:00Z
- **提交信息**: [Bugfix] Fix FlashMLA sparse accuracy with topk_length and zero-init padding (#36616)

Signed-off-by: AjAnubolu <anuboluajay@gmail.com>
Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Matthew Bonanni <mbonanni@redhat.com>

### [cca3365](https://github.com/vllm-project/vllm/commit/cca3365b733b5973d60a6631df8ee65ae53666a9)

- **作者**: Tahsin Tunan
- **时间**: 2026-06-16T13:47:11Z
- **提交信息**: [Rust Frontend] Add CORS support (#45753)

Signed-off-by: Tahsin Tunan <tahsintunan@gmail.com>

### [040df8f](https://github.com/vllm-project/vllm/commit/040df8f2eadf164775d82a9972148070c8f48207)

- **作者**: Matthew Bonanni
- **时间**: 2026-06-16T13:43:37Z
- **提交信息**: [CI] Fix attention benchmark smoke test (#45728)

Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [ced32bb](https://github.com/vllm-project/vllm/commit/ced32bb474feaed7e02723544013298fb1401b31)

- **作者**: Francesco Fusco
- **时间**: 2026-06-16T13:16:45Z
- **提交信息**: [Perf] Add VLLM_TRITON_FORCE_FIRST_CONFIG to skip Triton autotuning (#42425)

Signed-off-by: Francesco Fusco <ffu@zurich.ibm.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [c5e5c33](https://github.com/vllm-project/vllm/commit/c5e5c33fcd510da53270f0845bc7d3ce1cb3ef64)

- **作者**: Netanel Haber
- **时间**: 2026-06-16T13:06:28Z
- **提交信息**: [Bugfix][MoE] Restore routed output unpadding before shared expert add (#45707)

Signed-off-by: Netanel Haber <58652339+netanel-haber@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [a8c86ee](https://github.com/vllm-project/vllm/commit/a8c86eeb1695a3d35d0c748a68a1451379ea497a)

- **作者**: Mike G
- **时间**: 2026-06-16T12:43:44Z
- **提交信息**: [Quant] Support modelopt_mixed on Ampere (SM80/SM86) (#45306)

Signed-off-by: Mike G <180722391+mikekg@users.noreply.github.com>

### [7e179e4](https://github.com/vllm-project/vllm/commit/7e179e4bc0c125d8f06a1779a3712c3173ad13fb)

- **作者**: Andreas Karatzas
- **时间**: 2026-06-16T12:34:11Z
- **提交信息**: [ROCm][CI] Gate incompatible HF references on Transformers v5 (#41532)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [405c7cf](https://github.com/vllm-project/vllm/commit/405c7cf28352e45f68c338e643a4146550f3194e)

- **作者**: Lalithnarayan C
- **时间**: 2026-06-16T12:23:12Z
- **提交信息**: [ZenCPU] Add zencpu Platform Runtime Logging and Docs (#42726)

Signed-off-by: Lalithnarayan C <Lalithnarayan.C@amd.com>
Signed-off-by: Tyler Michael Smith <tlrmchlsmth@gmail.com>
Co-authored-by: Tyler Michael Smith <tlrmchlsmth@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Tyler Michael Smith <tyler@neuralmagic.com>

### [3f53e21](https://github.com/vllm-project/vllm/commit/3f53e2138f09843c5bddb4611df58e11bed01500)

- **作者**: Wentao Ye
- **时间**: 2026-06-16T11:35:58Z
- **提交信息**: [Refactor] Remove `Fp8OnlineLinearMethod` as scheduled (#45463)

Signed-off-by: yewentao256 <zhyanwentao@126.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [d53f459](https://github.com/vllm-project/vllm/commit/d53f4593cec92f9114ed6574dec24b0d69deb65e)

- **作者**: Hank Han
- **时间**: 2026-06-16T11:35:38Z
- **提交信息**: [KV Connector][Mooncake] Pipeline-parallel support for PD-disaggregated serving with Mooncake connector (#44528)

Signed-off-by: hanhan.hank <hanhan.hank@bytedance.com>
Signed-off-by: Hank Han <hanhan7630@outlook.com>

### [ad32608](https://github.com/vllm-project/vllm/commit/ad32608e24c91b5a21a22eeaa7b94dc3882b3854)

- **作者**: Shanshan Shen
- **时间**: 2026-06-16T11:35:20Z
- **提交信息**: [MM][Perf][CG] Support dual-path ViT full CUDA graph for DeepSeek-OCR (#43586)

Signed-off-by: shen-shanshan <467638484@qq.com>
Signed-off-by: Isotr0py <mozf@mail2.sysu.edu.cn>
Co-authored-by: Roger Wang <hey@rogerw.io>
Co-authored-by: Isotr0py <mozf@mail2.sysu.edu.cn>

### [b2cfae7](https://github.com/vllm-project/vllm/commit/b2cfae777dbad80096e5969212da58ff01cc432e)

- **作者**: Thien Tran
- **时间**: 2026-06-16T10:25:28Z
- **提交信息**: Add Triton recompile detection (#45631)

Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>

### [3f1ff1f](https://github.com/vllm-project/vllm/commit/3f1ff1ff1471fa4b53241b881b39d6dffc9ca301)

- **作者**: wangxiyuan
- **时间**: 2026-06-16T09:53:08Z
- **提交信息**: [Misc]Clean up useless test (#45792)

Signed-off-by: wangxiyuan <wangxiyuan1007@gmail.com>

### [c69c734](https://github.com/vllm-project/vllm/commit/c69c73418ab0ad13e28022ed16573019653a9bf7)

- **作者**: wenjun liu
- **时间**: 2026-06-16T08:35:08Z
- **提交信息**: [XPU][CI] add intel xpu cases for nightly CI (#44372)

Signed-off-by: wenjun.liu <wenjun.liu@intel.com>
Signed-off-by: zengxian <xiangdong.zeng@intel.com>
Co-authored-by: zengxian <xiangdong.zeng@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [ebf3a6d](https://github.com/vllm-project/vllm/commit/ebf3a6d70521214d01f23baca7b0b4f92944abab)

- **作者**: Thomas Parnell
- **时间**: 2026-06-16T08:34:27Z
- **提交信息**: [Bugfix] Fix trtllm fused allreduce+rms_norm for transformers backend (#45307)

Signed-off-by: Thomas Parnell <tpa@zurich.ibm.com>

### [c4fd979](https://github.com/vllm-project/vllm/commit/c4fd9794e9060531e98846706d5a4fdc573c2c19)

- **作者**: wang.yuqi
- **时间**: 2026-06-16T08:02:11Z
- **提交信息**: [Frontend] Remove AsyncMicrobatchTokenizer. (#45759)

Signed-off-by: wang.yuqi <yuqi.wang@daocloud.io>

### [7ad894c](https://github.com/vllm-project/vllm/commit/7ad894c86a2f3615fe72d739c25567803b5924ec)

- **作者**: joshua abraham
- **时间**: 2026-06-16T07:58:39Z
- **提交信息**: [Bugfix] Prevent cuMemcpyBatchAsync segfault with MTP and KV offloading (#44784)

Signed-off-by: joshua <joshua.abraham@multicorewareinc.com>
Co-authored-by: joshua <joshua.abraham@multicorewareinc.com>
Co-authored-by: Or Ozeri <oro@il.ibm.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-06-17
**监控日期**: 2026-06-16
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 5165
- **最后更新**: 2026-06-16T16:54:49Z

## 提交统计

- **昨日提交总数**: 9
- **提交者数量**: 9
- **主要提交者**: Hyoseop Song, Samit, TJian

## AI分析总结

好的，根据您提供的仓库 `vllm-project/vllm-omni` 的README摘要和提交记录，以下是昨日更新的要点分析：

### 1. 主要更新类型

- **Bug修复 (Bugfix)**：占比最高，共5项，涉及前缀缓存、模型对齐、NPU适配、测试修复等。
- **功能新增 (Feature)**：1项，新增了对SDXL模型的支持。
- **性能优化 (Perf)**：1项，通过跳过注意力掩码来优化Qwen图像编辑模型的性能。
- **文档更新 (Doc)**：1项，增加了自定义Docker镜像构建的指南。
- **CI/流程改进 (CI/Process)**：1项，优化了CI流水线，在rebase和合并时运行完整的端到端测试。

### 2. 关键变更点及其与项目整体方向的关系

- **`[SDXL] SDXL model enabling (#4331)`**：新增对Stable Diffusion XL (SDXL) 模型的支持。这直接呼应了项目“**easy, fast, and cheap omni-modality model serving**”的愿景，扩展了支持的模态范围，从文本/图像生成扩展到更先进的图像生成模型。
- **`[Bugfix] Fix DFlash prefix cache corruption due to missing lookahead block (#4449)`**：修复了DFlash前缀缓存损坏问题。这对于提升推理性能（尤其是多轮对话或批量推理）至关重要，符合项目“**fast**”和“**cheap**”（通过缓存减少计算）的目标。
- **`[BugFix][Qwen-Image] align txt_seq_lens RoPE width with padded embeds (#4474)`**：修复了Qwen图像模型中文本序列长度与填充嵌入的RoPE宽度对齐问题。这确保了多模态模型（文本+图像）的正确性，是项目支持“**omni-modality**”的关键技术细节。
- **`[BugFix][NPU]: Fix npu model runner too many values to unpack (#4454)`**：修复了NPU（神经网络处理单元）上的模型运行器问题。这表明项目正在积极扩展对不同硬件平台的支持，提升“**for everyone**”的硬件兼容性。
- **`[Perf][qwen-image-edit] Skip attention-mask to avoid varlen path (#4293)`**：针对Qwen图像编辑模型，通过跳过注意力掩码来避免变长路径，从而提升性能。这是对特定多模态模型（图像编辑）的深度优化，体现了项目在追求“**fast**”方面的细致工作。
- **`[Doc] Add guides for custom docker image build on NVIDIA CUDA (#1386)`**：增加了在NVIDIA CUDA环境下构建自定义Docker镜像的指南。这降低了用户部署的门槛，使项目更“**easy**”使用，并强化了对主流GPU平台的支持。
- **`[CI][Rebase]: run full e2e suite in rebase Ready/Merge pipelines`**：优化CI流程，确保代码合并前经过完整测试。这提升了项目的稳定性和可靠性，是保障“**easy**”和“**fast**”体验的基础。

### 3. 对项目的影响和潜在意义

- **模型生态扩展**：SDXL的加入标志着项目从支持基础模型向支持更先进、更复杂的生成模型迈进，显著增强了项目在图像生成领域的能力和吸引力。
- **稳定性与性能提升**：大量Bug修复（特别是前缀缓存、模型对齐、NPU适配）直接提升了项目的稳定性和在不同硬件上的可用性。性能优化则进一步巩固了其“**fast**”的定位。
- **开发者体验改善**：文档更新和CI流程优化降低了新用户的入门门槛，并提高了核心开发者的协作效率，有助于项目社区的健康发展。
- **硬件兼容性增强**：对NPU的Bug修复表明项目正在积极拥抱多样化的硬件生态，这对于实现“**for everyone**”的目标至关重要。

### 4. 值得关注的技术点

- **DFlash前缀缓存**：这是一个关键的性能优化技术，修复其损坏问题对于维持高吞吐量推理至关重要。值得关注其实现细节和后续优化。
- **Qwen图像编辑模型的性能优化**：通过“跳过注意力掩码”来避免“变长路径”是一个巧妙且有针对性的优化，展示了针对特定模型架构进行深度调优的思路。
- **NPU适配**：修复NPU运行器问题，表明项目正在尝试支持除NVIDIA/AMD GPU之外的硬件，这对于在更广泛、更经济的硬件上部署大模型具有重要意义。
- **SDXL模型集成**：SDXL的模型结构、内存占用和推理优化策略与之前的模型不同，其成功集成是项目技术能力的一个重要里程碑。

### 5. 基于项目背景，这些提交如何影响项目发展

- **强化核心定位**：这些提交直接服务于项目“**Easy, fast, and cheap omni-modality model serving for everyone**”的使命。Bug修复和性能优化让服务更“**fast**”和“**cheap**”；文档和CI改进让使用更“**easy**”；SDXL和Qwen图像编辑的支持扩展了“**omni-modality**”的边界；NPU的修复则向“**for everyone**”迈出了坚实一步。
- **从“能用”到“好用”**：早期的提交可能侧重于让模型“跑起来”。昨日的更新明显进入了“优化”和“扩展”阶段：修复各种边界情况下的Bug、针对特定场景进行性能调优、增加对更复杂模型的支持。这表明项目正在从原型验证阶段向一个成熟、稳定、高性能的生产级服务平台演进。
- **

## 详细提交记录

### [b46c5af](https://github.com/vllm-project/vllm-omni/commit/b46c5af06fe56419ade8cae7078fffb12fc46f01)

- **作者**: Hyoseop Song
- **时间**: 2026-06-16T15:15:58Z
- **提交信息**: [Doc] Add guides for custom docker image build on NVIDIA CUDA [Skip-CI] (#1386)

Signed-off-by: Hyoseop Song <crad_on25@naver.com>
Signed-off-by: Hyoseop Song  <crad_on25@naver.com>
Co-authored-by: Zhou Taichang <tzhouam@connect.ust.hk>
Co-authored-by: Alicia <115451386+congw729@users.noreply.github.com>

### [f200e98](https://github.com/vllm-project/vllm-omni/commit/f200e988a69421f47730c11b7eecc0d7007f5ed6)

- **作者**: Junhong Liu
- **时间**: 2026-06-16T14:54:26Z
- **提交信息**: [fix bug] add default limit for image generation (#3381)

Signed-off-by: Junhong Liu <98734602+LJH-LBJ@users.noreply.github.com>
Signed-off-by: Hongsheng Liu <liuhongsheng4@huawei.com>
Co-authored-by: lishunyang <lishunyang12@163.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>
Co-authored-by: Copilot Autofix powered by AI <175728472+Copilot@users.noreply.github.com>

### [e3621ec](https://github.com/vllm-project/vllm-omni/commit/e3621ec633894b6e7d5aa58c10feaa11699da3b7)

- **作者**: Kristoffer
- **时间**: 2026-06-16T14:52:04Z
- **提交信息**: [Perf][qwen-image-edit] Skip attention-mask to avoid varlen path (#4293)

Signed-off-by: kTorp <Kristoffer.Torp@amd.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [e7f0db1](https://github.com/vllm-project/vllm-omni/commit/e7f0db1067275341960f9c04a7c4447cc78893ac)

- **作者**: Chendi.Xue
- **时间**: 2026-06-16T14:51:11Z
- **提交信息**: [SDXL] SDXL model enabling (#4331)

Signed-off-by: Chendi Xue <chendi.xue@intel.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [864d221](https://github.com/vllm-project/vllm-omni/commit/864d22164cc2a5c563067d96046fa266aeafb94f)

- **作者**: Nick Cao
- **时间**: 2026-06-16T14:48:01Z
- **提交信息**: [Bugfix] Fix DFlash prefix cache corruption due to missing lookahead block (#4449)

Signed-off-by: Nick Cao <ncao@redhat.com>

### [5f5b77a](https://github.com/vllm-project/vllm-omni/commit/5f5b77aa9cef5033c015eb40c9c228c5f68244c6)

- **作者**: Samit
- **时间**: 2026-06-16T11:09:25Z
- **提交信息**: [BugFix][Qwen-Image] align txt_seq_lens RoPE width with padded embeds (#4474)

Signed-off-by: samithuang <285365963@qq.com>

### [3fa8817](https://github.com/vllm-project/vllm-omni/commit/3fa8817fc5d72cf3b5f43a06774e0edb81858f83)

- **作者**: Weiming Liao
- **时间**: 2026-06-16T11:06:51Z
- **提交信息**: [BugFix][NPU]: Fix npu model runner too many values to unpack ($[1][0][4]) (#4454)

Signed-off-by: Weiming Liao <liaowm5@gmail.com>
Co-authored-by: Canlin Guo <canlinguosdu@gmail.com>

### [a624204](https://github.com/vllm-project/vllm-omni/commit/a62420450c8a986504454ef93fa3bdce177fc1c0)

- **作者**: Zhou Taichang
- **时间**: 2026-06-16T08:49:19Z
- **提交信息**: [CI][Rebase]: run full e2e suite in rebase Ready/Merge pipelines in the rebase pipeline[skip-ci] (#4478)

Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>

### [5cce797](https://github.com/vllm-project/vllm-omni/commit/5cce797c036dbe919763d40ee08c681ba89fa0f6)

- **作者**: TJian
- **时间**: 2026-06-16T08:39:23Z
- **提交信息**: [Bugfix] [CI] [ROCm] [CUDA] Fix voxtral test (#4380)

Signed-off-by: tjtanaa <tunjian.tan@embeddedllm.com>

---
