# GitHub Stars 合并报告 - 2026-11-13

**合并日期**: 2026-11-14
**监控日期**: 2026-11-13
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


**报告日期**: 2026-11-14
**监控日期**: 2026-11-13
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2293
- **最后更新**: 2026-11-13T17:01:36Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: zhouyang, BeatSeat

## AI分析总结

## VeOmni 昨日提交分析

### 1. 主要更新类型

本次提交包含**一项功能新增**和**一项 Bug 修复**，核心围绕分布式训练效率与训练稳定性展开，属于典型的「性能优化 + 正确性修复」组合。

### 2. 关键变更点及与项目方向的关系

- **FP8 训练支持（#1428）**：为 LLM 和 DiT（Diffusion Transformer）训练引入了 **Tensorwise（张量级）与 Rowwise（行级）两种 float8 量化策略**。FP8 是当前大模型训练降本增效的关键技术，能显著降低显存占用与通信开销。该功能覆盖 LLM 与 DiT 两种主流架构，与 VeOmni「多模态、多模型架构」的定位高度一致。
- **PLE 行裁剪修复（#1394）**：修复 Qwen4-Exp 模型中 PLE（可能是 Position/Parameter Level Encoding）在 DCP（Distributed Checkpoint）与 HF 格式检查点中的行裁剪错误，确保训练/微调/推理时权重对齐。

两项提交分别对应分布式训练框架的两大核心诉求：**性能（FP8）**与**正确性（Checkpoint 兼容）**。

### 3. 对项目的影响和潜在意义

- **FP8 训练**：面向大规模训练场景，降低硬件成本门槛，提升吞吐。对于 LLM+DiT 的统一训练框架而言，这是迈向生产可用的重要一步；Tensorwise/Rowwise 两种粒度提供了不同精度需求下的灵活性。
- **Checkpoint 修复**：直接提升与 HuggingFace 生态的互操作性，降低用户在训练切换到推理/评估环节的踩坑风险，有助于扩大社区采用。

### 4. 值得关注的技术点

- **量化粒度选择**：Tensorwise（整体）与 Rowwise（按行）的并存设计，值得深入研究其对训练稳定性与收敛性的影响差异。
- **DCP 与 HF 双格式兼容**：表明 VeOmni 在分布式 checkpoint 与通用格式间做了适配层，值得后续关注其 checkpoint 迁移工具链。
- **DiT 支持的持续扩展**：FP8 特性同样覆盖 DiT，说明框架对视频/图像生成场景的投入正在加深。

### 5. 对项目发展的综合影响

结合 README 中「Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo」的定位，这两个提交体现了 VeOmni 从「框架搭建」向「生产级训练能力」演进的趋势：FP8 降低了大规模训练的资源门槛，Checkpoint 修复则夯实了与主流生态的互操作性。两者共同推动 VeOmni 在分布式多模态训练赛道上建立技术壁垒，为后续支持更大规模、更多模态的模型训练奠定基础。

## 详细提交记录

### [65e9dff](https://github.com/ByteDance-Seed/VeOmni/commit/65e9dffb6a7df9432a8d0793b679db0f3ef47fb5)

- **作者**: BeatSeat
- **时间**: 2026-11-13T08:27:34Z
- **提交信息**: [dist, model, config, docs] feat: add tensorwise and rowwise float8 training for LLM and DiT (#1428)

### [150f669](https://github.com/ByteDance-Seed/VeOmni/commit/150f6690eec1afb65dd329977e145906877331a2)

- **作者**: zhouyang
- **时间**: 2026-11-13T07:15:35Z
- **提交信息**: [model, ckpt] fix: correct Qwen4-Exp PLE row cropping in DCP and HF checkpoints (#1394)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-11-14
**监控日期**: 2026-11-13
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 3004
- **最后更新**: 2026-11-13T06:41:11Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Musisoul, Shiqiao Gu (谷石桥)

## AI分析总结

## 昨日提交分析总结（ModelTC/LightX2V）

### 1. 主要更新类型
- **功能新增**：ComfyUI 多 GPU 推理、MiniMax-H3 consumer LoRA 融合、LCM 调度器、TBDub V2V 推理。
- **重构**：LoRA 执行模式统一为 `lora_mode`（merge/separate/consumer）三态配置，调度器配置标准化。
- **文档更新**：中英文 README 补充 ComfyUI 用法、集成链接与启动示例。

### 2. 关键变更点及与项目方向的关系
- **多 GPU 与 Ulysses SP 自动配置**：直接呼应项目"轻量视频生成推理"的定位，降低单卡显存压力，提升长视频/高分辨率生成的可用性。
- **LoRA consumer 融合模式**：在保持量化基座 GEMM 不变的前提下单独计算 LoRA 分支，兼顾量化效率与微调灵活性；配合 `torch.compile` 支持，体现"轻量+高效"的核心目标。
- **蒸馏调度体系完善**：新增 LCM 调度器、`distilled_sigma_values`，并将 H3 蒸馏配置整理为 4/6/8 步 profile（含 Pika、Turbo v1.2），显著强化少步数快速生成能力——这是轻量化推理的关键抓手。
- **TBDub V2V**：复用 Wan2.2 5B 组件实现视频到视频推理，扩展了模型支持矩阵。

### 3. 对项目的影响和潜在意义
- 生态接入面扩大：ComfyUI 多 GPU 支持与工作流 JSON 更新，使非开发者用户更易上手，有利于社区采用。
- 推理成本进一步下降：蒸馏 profile 标准化 + LoRA 消费者模式，意味着用户能以更少采样步数、更灵活的适配方式获得可用结果。
- 架构可维护性提升：LoRA 精度统一（`LORA_DTYPE`）、alpha 解析逻辑（张量→元数据→配置回退）和调度器配置规范化，减少隐式行为，便于后续扩展新模型。

### 4. 值得关注的技术点
- **量化与 LoRA 解耦计算**：基座走量化路径、LoRA 走独立精度路径的混合执行策略，是量化推理框架中处理适配器的典型难点。
- **LoRA 感知的 AdaLN 缓存导出与校验**：说明框架开始考虑 LoRA 与缓存机制的交互，对视频生成的时间一致性推理有潜在价值。
- **原生 H3 LoRA 更新 AdaLN/最终调制层**：将适配范围扩展到调制层而非仅注意力层，影响生成风格的深度。

### 5. 对项目发展的整体影响
结合 README 定位（轻量视频生成推理框架），这批提交沿三条主线推进：**多卡扩展性**（ComfyUI SP）、**推理效率**（蒸馏调度 + LoRA consumer 融合）、**生态友好性**（文档与工作流更新）。项目正从"单模型单卡快速推理"向"多模型、多入口（CLI/ComfyUI）、可配置的生产级推理平台"演进，既巩固轻量化技术壁垒，也通过 ComfyUI 集成扩大用户基础，为其在视频生成推理工具链中的竞争位置打下基础。

## 详细提交记录

### [9cb6929](https://github.com/ModelTC/LightX2V/commit/9cb6929d83814ff28c4e1386532298fe93a96af1)

- **作者**: Musisoul
- **时间**: 2026-11-13T07:24:06Z
- **提交信息**: feat(comfyui): support multi-GPU inference and update readme (#1707)

1. Add GPU multi-selection and automatic Ulysses SP configuration.
2. Update H3 Image t2i/i2i workflow JSONs.
3. Update READMEs with ComfyUI usage and integration links.

### [1053bb0](https://github.com/ModelTC/LightX2V/commit/1053bb0aad2e795b18ddae20f458200d18846985)

- **作者**: Shiqiao Gu (谷石桥)
- **时间**: 2026-11-13T05:45:26Z
- **提交信息**: Refactor LoRA execution modes and add MiniMax-H3 consumer fusion (#1706)

## Summary

Refactor LoRA execution modes and add MiniMax-H3 consumer fusion,
improved distillation support, and TBDub V2V inference.

## Changes

- Configure LoRA execution through `lora_mode`: `merge` (default),
`separate`, or `consumer`.
- Add MiniMax-H3 consumer fusion for activation and residual operations,
including `torch.compile` support.
- Keep quantized base GEMMs unchanged while computing LoRA branches
separately.
- Unify LoRA computation precision through `LORA_DTYPE`, defaulting to
`DTYPE`.
- Support native H3 LoRA updates to AdaLN and final modulation layers.
- Resolve alpha from embedded tensors or metadata before falling back to
config, with logging.
- Support LoRA-aware AdaLN cache export and validation.
- Add the LCM scheduler and explicit `distilled_sigma_values`;
standardize scheduler configuration.
- Organize H3 distilled configs into 4-, 6-, and 8-step profiles,
including Pika and Turbo v1.2 examples.
- Add TBDub V2V inference using the existing Wan2.2 5B components.
- Update launch examples and English/Chinese documentation.

---------

Co-authored-by: helloyongyang <yongyang1030@163.com>

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-11-14
**监控日期**: 2026-11-13
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2335
- **最后更新**: 2026-11-13T06:03:52Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: CloudGPU

## AI分析总结

## 昨日提交分析（VideoX-Fun，1/1 批）

### 1. 主要更新类型
**文档更新（docs）**。这是一次纯文档性质的修订，不涉及代码逻辑、功能或性能改动。

### 2. 关键变更点及与项目方向的关系
- 将项目中关于许可证的引用改为指向仓库自身的 LICENSE 文件（commit `991863c`，PR #530），修正了此前可能指向外部或错误许可证说明的问题。
- 与项目整体方向的关系：VideoX-Fun 是阿里 PAI 团队开源的视频生成模型套件（CogVideoX-Fun、Wan-Fun 等），开源合规是其对外发布和社区使用的基础。明确许可证引用属于开源治理的收尾性工作，与 README 中多语言文档、Hugging Face Spaces 等面向社区的基础设施建设一脉相承。

### 3. 对项目的影响和潜在意义
- **合规性提升**：许可证指向准确可避免社区用户、下游集成方（如模型部署平台、衍生项目）产生授权歧义，降低法律风险。
- **对贡献者友好**：贡献者在提交 PR 前能清晰确认授权条款，有助于吸引更多外部协作。
- **影响范围小**：对运行时行为、模型推理结果无任何影响，属于低风险的文档清理。

### 4. 值得关注的技术点
- 值得留意的是**许可证的实际类型**（本次提交摘要未透露具体是 Apache-2.0 还是其他条款），因为它决定了商用、再分发和模型权重使用的边界——对于 Wan2.1/CogVideoX 系列这类重量级模型，许可证选择直接影响企业用户的采纳意愿。
- 由外部贡献者 `mrhy7176` 以 Co-authored 方式提交，说明项目接受社区小型文档修正，维护流程较为开放。

### 5. 对项目发展的综合影响
结合 README，VideoX-Fun 的核心目标是提供可复现、可扩展的视频生成训练与推理框架，近期重点在 CogVideoX-Fun 和 Wan-Fun 两条产品线及多语言文档的完善。本次提交虽然体量极小，但属于开源项目**成熟度打磨**的一部分：准确的许可证声明与英文/中文/日文 README、HF Spaces 演示共同构成规范的对外形象，为后续版本迭代、模型权重发布和社区生态扩张扫清合规障碍。总体而言，这是一次必要但非关键路径的维护性更新，对项目功能演进影响有限，却体现了团队对开源规范性的重视。

## 详细提交记录

### [991863c](https://github.com/aigc-apps/VideoX-Fun/commit/991863c8c3fb9da946f21b675e52e45b0b53ed68)

- **作者**: CloudGPU
- **时间**: 2026-11-13T06:43:47Z
- **提交信息**: docs: point the project license reference to its own license (#530)

Co-authored-by: mrhy7176 <129925370+mrhy7176@users.noreply.github.com>

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-11-14
**监控日期**: 2026-11-13
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6917
- **最后更新**: 2026-11-13T21:03:16Z

## 提交统计

- **昨日提交总数**: 14
- **提交者数量**: 9
- **主要提交者**: wasabitnervous, akshaver, Brian K. Ryu

## AI分析总结

# FlashInfer 昨日提交分析总结

## 一、主要更新类型

昨日共 14 个提交，以**性能优化与正确性修复**为主，辅以**功能新增**和**测试基础设施扩展**：性能优化集中在注意力后端自动调度、GEMM 自动调优与基准测量精度；修复涵盖 CUTLASS 错误状态检查、GDN 内核对齐崩溃、CI 流水线竞态；功能新增包括滑动窗口支持、批不变采样、NVFP4 MoE 路由权重与原地权重改写检测；测试侧则扩展了 SM107 MegaMoE 基准矩阵。

## 二、关键变更点

- **后端自动调度扩展**：`auto` 模式在 H100 分页注意力中按工作量准入 cuDNN、纳入 FP16 输入并限制批量声明；SM107 上 MXFP8 自动调优比较 CuTe-DSL 与 cuDNN，使默认路径在 Hopper 与 Rubin 架构上更快。
- **错误处理与崩溃修复**：SM120 四个 GEMM 启动器补上 CUTLASS 错误状态检查，消除不支持形状静默返回 NaN；Cake GDN 预填充的 292 个分块变体在非 16 字节对齐状态指针下崩溃，现以双 flavor 编译解决。
- **测量基础设施**：用读操作替代 `zero_()` 刷新 L2，消除脏行回写对冷 L2 计时的污染，使基准数据与调优排名更真实。
- **运行时健壮性**：`trace_apply` 通过 torch 版本计数器检测 setup 输入的原地改写，自动重备或拒绝过期 CUDA 图，防止内核使用陈旧权重。
- **功能新增**：cuDNN 分页 prefill 支持 `window_left` 滑动窗口；`sampling_from_probs/logits` 支持 `batch_invariant=True`；NVFP4 MoE 在 GEMM1 epilogue 内应用路由权重并支持 ClampedRelu2 软钳位；CI 预取修复避免 lint 并行池锁竞争误杀下载进程；SM107 MegaMoE 基准覆盖推理/GenPhase、预量化输入与自动调优套件。

## 三、项目影响与潜在意义

用户在 H100/SM107/SM120 上开箱即获更快默认路径（H100 FP16 路由提速约 1.29–1.33 倍），无需手动指定后端；NaN 与对齐崩溃的消除显著提升生产可靠性；权重改写检测为 EPLB、权重热加载等动态部署场景铺路。批不变采样满足合规、调试与回归对比对可复现性的严格要求，其不满足条件即抛错、无静默回退的设计偏严格。MoE 路径在 GEMM2 量化前内联完成路由权重，避免分配 `tokens × top_k × intermediate` 的 BF16 中间缓冲（32k token 时省 4 GiB/GPU），直接缓解大 batch 高吞吐推理的显存压力。更精确的计时与扩展的 SM107 基准则让后续所有性能决策与架构回归防护受益。

## 四、值得关注的技术点

- **声明与执行分离**：cuDNN 批量声明取 2 的幂以保留形状覆盖缓存，真实 batch 由执行时绑定。
- **工作量准入**：以实际 causal query-key 对数量（≥2^24）而非声明的最大长度决定路由，防止空批次误入慢路径。
- **读式 L2 刷新**：`torch.sum(buffer, out=...)` 使脏回写落在计时窗口外，是微基准测量的通用技巧。
- **GDN 双 flavor 编译**：对齐时 SASS 不变、零开销，非对齐时逐访问回退标量，性能区间 0.964×–1.018×。
- **位级可复现舍入**：MoE 舍入全部用内联 PTX 固定，输出与参考实现位级一致。
- **版本计数器失效检测**：整数比较开销极低，但绕过 dispatcher 的裸写入仍不可见，文档明确了责任边界。
- 提交普遍附带严格 AB/BA 顺序、等价区间与独立参考校验，体现高标准的性能声明验证文化。

## 五、整体意义

这些工作共同强化了 FlashInfer 作为"推理内核库 + 智能调度层"的定位：在注意力与 GEMM 两条主线上同时扩大 `auto` 模式的可信覆盖域，修正测量与错误处理的底层缺陷，并补齐可复现推理语义与工程基础设施。项目正以"高性能且可靠"为方向，向更多架构（sm_100a/103a/107a）与更复杂模型（GDN、MegMoE 类 MoE）稳步推进，为后续优化奠定更可靠的基线。

## 详细提交记录

### [1a5fb18](https://github.com/flashinfer-ai/flashinfer/commit/1a5fb18cf84be4a127d6c0f9fbcd2535f98080c9)

- **作者**: wasabitnervous
- **时间**: 2026-11-13T23:55:52Z
- **提交信息**: fix(gemm): raise on CUTLASS failure in SM120 groupwise GEMM launchers (#7421)

<!-- .github/pull_request_template.md -->

## 📌 Description

We found this while benchmarking the FP8 GEMM backends on our RTX 5060
Ti (sm_120) serving node, during an investigation of #6312.

On SM120/SM121, four launchers ignore the `cudaError_t` returned by the
CUTLASS runner:

- `csrc/gemm_groupwise_sm120.cu` (`gemm_fp8_nt_groupwise`, and `bmm_fp8`
/ `mm_fp8` through the `cutlass_sm12x` runner)
- `csrc/group_gemm_fp8_groupwise_sm120.cu`
- `csrc/group_gemm_mxfp4_groupwise_sm120.cu`
- `csrc/group_gemm_nvfp4_groupwise_sm120.cu`

Each one ends its dispatch lambda with `return status == cudaSuccess;`,
and the outer dispatch drops that bool. When CUTLASS `can_implement()`
rejects a problem, the call returns normally and the output tensor is
never written. The SM100 launcher (`csrc/gemm_groupwise_sm100.cu`)
already checks the status with `TVM_FFI_ICHECK_EQ(status, cudaSuccess)`.
This PR adds the same check to the four SM120 files.

Repro on an RTX 5060 Ti (sm_120) at main 225b3b3:
`gemm_fp8_nt_groupwise(a, b, a_scale, b_scale, "MN", out=out,
backend="cutlass")` with m=128 and k=256, and `out` pre-filled with NaN:

| n | before | after |
|---|---|---|
| 256 | correct (rel. err 3.1e-3) | correct (unchanged) |
| 192 | returns without error, `out` still all NaN | `RuntimeError: ...
Failed to run cutlass gemm groupwise scaled sm120: operation not
supported` |
| 200 | returns without error, `out` still all NaN | same `RuntimeError`
|

`bmm_fp8` does not hit this in practice: `CutlassFp8GemmRunner` pads N
and K to multiples of 128 before the call. The direct
`gemm_fp8_nt_groupwise` path does not pad.

Kernels and supported shapes are unchanged. Following review, the same
check is also applied to `csrc/group_gemm_fp8_groupwise_sm100.cu` and
`csrc/group_gemm_mxfp4_groupwise_sm100.cu` for consistency. There,
CUTLASS rejections already throw through `CUTLASS_CHECK`; the dropped
status could only carry a failed prepare-args kernel launch. Those two
are build-checked for sm_100a only; I have no SM100 hardware to run them
on.

## 🔍 Related Issues

Found while measuring #6312. I could not find an existing issue or PR
about the dropped status.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues. (Run on the changed files.)

## 🧪 Tests

- [x] Tests have been added or updated as needed.
New `test_fp8_groupwise_gemm_sm12x_unsupported_shape_raises` (n=192,
200) in `tests/gemm/test_groupwise_scaled_gemm_fp8.py`. Without the fix
it fails (`DID NOT RAISE RuntimeError`, 2 failed). With the fix it
passes.
- [x] All tests are passing (`unittest`, etc.).
  RTX 5060 Ti (sm_120), CUDA 13.3, torch 2.13.0+cu130:
- `tests/gemm/test_groupwise_scaled_gemm_fp8.py -k
"test_fp8_groupwise_gemm and cutlass"`: 252 passed
- `tests/gemm/test_groupwise_scaled_gemm_fp8.py -k
test_fp8_groupwise_group_gemm`: 308 passed, 2104 skipped
  - `tests/gemm/test_groupwise_scaled_gemm_mxfp4.py`: 3456 passed
  - `tests/gemm/test_group_gemm_fp4.py`: 162 passed

## Reviewer Notes

A small, mechanical change. The error message follows the wording of the
SM100 launcher.

AI-assisted (Claude Code). I reviewed every change and ran the tests
above on our own hardware.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Groupwise GEMM operations now report CUDA failures as errors that
include the CUDA error message, rather than returning `false`. This
applies to FP8, MXFP4, and NVFP4 operations on supported GPU
architectures.
* **Tests**
* Added regression coverage for SM12x groupwise FP8 GEMM with input
sizes of 192 and 200, verifying that the operation reports an error. The
test runs only when CUDA is available on a supported device.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: sunboaooo-blip <271910437+sunboaooo-blip@users.noreply.github.com>

### [fad20b5](https://github.com/flashinfer-ai/flashinfer/commit/fad20b57a8519417a9779a44eaf9d4a06d098db6)

- **作者**: Yang Xu
- **时间**: 2026-11-13T23:21:37Z
- **提交信息**: perf(attention): bound Hopper ragged cuDNN batch declarations (#9469)

<!-- .github/pull_request_template.md -->

## 📌 Description

Ordinary cuDNN ragged prefill on Hopper declares at least 4096 batch
entries for shape-override caching. With D256 this can make the SDPA GPU
execution much slower than the same computation declared with a small
batch, even when execution overrides supply the actual batch. This
change rounds the declared batch up to the next power of two for direct
cumulative-length BF16/FP16 D256 MHA/GQA on SM90, retaining the existing
Q/KV sequence cache classes and common FE graph interface.

Batch bounds are separate from packed-Q capacity. Cache keys and plan
reuse track the declaration mode; real Q/K/V/output/workspace pointers
still bind per execution. Scope excludes paged attention, single-token
queries, explicit mask lengths, windows and sinks. Existing graph-mode
wrappers already declare exact lengths and retain that path; scaled
calls retain their public preparation path. **No ragged auto-dispatch
expansion.**

### Current-source reproduction

H100 80GB HBM3 / 132 SM, official FE 1.32.3, verified loaded cuDNN
9.24.0.43 (92400), Torch 2.14.1+cu130. All 8 predetermined examples
below ran in separate parent/candidate/candidate/parent processes (32
successful calls of the public benchmark), with Hq/Hkv 32/8, D256,
causal NHD ragged, ordinary default cuDNN selection and FROST opt-in
unset. Parent `545d9e9e878352e607413a13860cb3de288f95dc`, candidate
`597ac44b650bd3d2eef55372dd3676e2332486af`; identical benchmark script
on both sources. Source/native/import hashes and actual backend version
were checked.

Steady timings exclude plan construction, first calls/compilation and
reference checks. Graph is warm whole-graph CUDA-event replay; completed
eager includes synchronization after a 20-call loop. Each table value is
the geometric mean of two per-process medians. Every process checks an
independent sampled math reference and both poisoned and timed graph
replay. Full-row O/LSE lifecycle checks are separate below.

| dtype | B | Q/KV | graph parent→candidate (us) | speedup | completed
eager parent→candidate (us) | speedup |
|---|---:|---|---:|---:|---:|---:|
| bfloat16 | 3 | 64/4096 | 775.234 → 108.951 | 7.115x | 776.572 →
111.361 | 6.973x |
| bfloat16 | 1 | 512/512 | 683.647 → 23.808 | 28.715x | 686.065 → 29.603
| 23.176x |
| bfloat16 | 16 | 512/8192 | 3985.817 → 3403.426 | 1.171x | 3952.886 →
3389.995 | 1.166x |
| bfloat16 | 8 | 2048/16384 | 13493.205 → 12909.662 | 1.045x | 13422.015
→ 12871.317 | 1.043x |
| float16 | 3 | 64/4096 | 771.077 → 108.866 | 7.083x | 772.738 → 112.145
| 6.891x |
| float16 | 1 | 512/512 | 685.944 → 23.827 | 28.788x | 688.288 → 29.860
| 23.051x |
| float16 | 16 | 512/8192 | 4116.638 → 3506.873 | 1.174x | 4089.594 →
3468.501 | 1.179x |
| float16 | 8 | 2048/16384 | 13930.969 → 13412.190 | 1.039x | 13982.291
→ 13412.198 | 1.043x |

Across all 8 examples, graph improves 3.974x and completed eager 3.741x;
no graph/eager slowdown above 5% persists in both process orders. Host
submission is 32.670→33.202 us. The FP16 B1 full-prefill host
measurement increases from 29.921 to 32.205 us, with a >5% increase in
both orders; this change is not a host-overhead optimization. These are
API/component results, not serving TTFT. A separate complete 200-case
instrumented development survey improved cuDNN-self by 3.556x
graph/3.438x eager but still trailed stock FA3 in aggregate, which is
why this PR leaves auto admission unchanged. That survey is not
presented as final-source qualification.

The benchmark companion is identical to #9463's `50178aa4`
benchmark/test changes; no FP16 dispatch changes from that PR are
included. It adds D/dtype arguments, completed-eager measurements and
per-round backend order alternation. To compare a prior checkout, copy
this PR's `benchmarks/bench_cudnn_wrapper_host.py` to the same external
path, install each intended FI checkout in its own environment, and
verify `flashinfer.__file__`, `cudnn.__version__` and
`cudnn.backend_version()` in that process. For each dtype (`bfloat16`,
`float16`) and `(B,Q,KV)` in `(3,64,4096)`, `(1,512,512)`,
`(16,512,8192)`, `(8,2048,16384)`, run
baseline/candidate/candidate/baseline with:

```bash
python /tmp/bench_cudnn_wrapper_host.py --kind ragged --backends cudnn --batch 1 --q 512 --kv 512 --qo-heads 32 --kv-heads 8 --head-dim 256 --dtype bfloat16 --expected-backend-version 92400 --output result.json
```

Leave `CUDNN_FRONTEND_ENABLE_FROST_ENGINES` unset. The generic ragged
benchmark supplies explicit lengths and does not exercise this
declaration-cache path.

### Validation

- 818 scoped CPU attention/descriptor tests plus 3 benchmark scheduling
tests pass without initializing CUDA.
- 28/28 new public H100 GPU tests pass, with no skips: BF16/FP16 ×
causal/noncausal, batch 2→3→4→5→3, same-bucket reuse/cross-bucket
invalidation, full-row FP64 O/LSE references, retained CUDA Graphs after
changed partitions/data, scalar/device scales, nondefault-stream pointer
rebinding and workspace reset. Production and GPU test sources are
byte-identical between the tested `f8a9f0c8` and published `597ac44b6`;
only the benchmark companion was added afterward and tested by the
32-process reproduction.
- Changed-file pre-commit hooks and `git diff --check` pass.

The first GPU test revision had 4 passing replan tests and 8 failures in
pre-kernel assertions: it incorrectly expected graph-mode to use the
batch cache. Source inspection corrected that expectation and added
explicit unscaled/scale-path controls; the production change did not
expand. Published-head actual CI and independent review are still
required before merge.


## 🔍 Related Issues

Related benchmark companion: #9463. No auto-dispatch or FE version-floor
change.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

Changed-file hooks passed; whole-repository hooks were not run.

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
reviewers may adjust): `tests/cpu/attention/
tests/attention/test_cudnn_ragged_batch_bound.py
tests/attention/test_cudnn_graph_cache_key.py
tests/attention/test_cudnn_prefill_token_indptr.py
tests/attention/test_cudnn_ragged_shape_override.py`

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

The tradeoff is additional cold graph builds when batch crosses a
power-of-two bound. Official FE graph-cache capacity (256) and FI
preparation-history capacity (4) are unchanged; retained user CUDA
Graphs can keep old resources alive. Per-process benchmark peak GPU
allocation is identical between parent and candidate for every case
(0.43–6.54 GiB, including test tensors and fixed workspaces);
application KV-cache pressure and total CPU cache residency are not
qualified here. Both arms emit nanobind reference-leak diagnostics
during interpreter shutdown; all 32 processes exit successfully after
numerical/replay checks. This PR does not claim to fix those existing
shutdown diagnostics. The new boolean deliberately does not reuse the
FROST packed-capacity flag. Upstream changes after the tested base
include L2-flush utilities and paged capability tests; this benchmark
uses direct CUDA events without L2 flushing. Actual merged-tree CI
remains required.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Eligible Hopper cuDNN ragged-attention workloads can reuse graph plans
across batch sizes within the same capacity range.
* The benchmark supports configurable data types, head dimensions, and
page sizes, and reports additional timing, memory, version, and backend
details.
* **Bug Fixes**
* Benchmark sampling continues for working backends when another backend
encounters an error.
* **Documentation**
* Added guidance on supported ragged-attention batch behavior, graph
reuse, and its limitations.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [5967e35](https://github.com/flashinfer-ai/flashinfer/commit/5967e3589360b64864ce343012daa2318b2cbd5d)

- **作者**: akshaver
- **时间**: 2026-11-13T22:25:30Z
- **提交信息**: feat(trace_apply): detect in-place rewrites of setup inputs, re-prepare or refuse (#9408)

## 📌 Description

A setup-bearing Solution keyed its prepared state only on setup-input
identity
(address, shape, stride, dtype, device). An in-place weight rewrite
behind a
stable address — an EPLB rebalance, a weight reload — left the prepared
state
stale, and the kernel kept serving it.

Each entry now also records the setup inputs' `_version` counters, which
torch's dispatcher bumps on every in-place op. On mismatch a call:

- **re-prepares** under the same key (old state torn down and released
first,
so memory does not double; the lock spans teardown and prepare, and a
call
  that lost a re-prepare race re-validates the winner's entry), or
- **raises `StaleSetupError`** once a CUDA-graph capture has frozen the
  binding, because captured graphs replay against the prepared state's
  addresses and the state cannot be replaced.

Re-prepare, like `release()`, assumes the engine quiesces calls around
the
rewrite: a call in flight keeps the state it was handed.

**Cost:** one integer read and compare per setup input per eager call;
nothing
under graph replay, where no Python runs. Setup-less Solutions are
untouched.
`stats()` gains `reprepared` and `refused_stale` counters.

**Limitations:** writes that bypass the dispatcher — a raw copy into the
storage, as a cumem sleep-mode restore does — move no counter and stay
invisible; refusing that class of rewrite stays the consumer's job.
Inference-mode tensors track no counter and stay identity-keyed, exactly
as
before.

## 🔍 Related Issues

Follow-up to #8866 (sealed kernel packages with a setup step). No
tracking
issue; the gap was documented in the module contract itself ("an engine
mode
that rewrites weights in place is the consumer's to refuse").

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] Ran the hooks on the changed files (`pre-commit run --files ...`):
ruff
  check, ruff format and mypy all pass.

## 🧪 Tests

- [x] Tests added: 9 new CPU tests in
`tests/cpu/trace_apply/test_setup.py`
(re-prepare under the same key, rewrite through a view, frozen refusal,
rewrite during capture, failed-teardown recovery, per-weight-set
isolation,
  racing-replacement re-validation, capture-served replacement freeze,
  inference-tensor fallback).
- [x] All tests pass locally: 41/41 in the file; the directory's other
  failures are identical on pristine main (environment, GPU-less host).
- [x] Full-scope CI not required — the change is contained to
trace_apply's
  setup path.

  Suggested CI test targets: `tests/cpu/trace_apply/`

## 🔬 Experimental Track

Not experimental; section intentionally left unapplied.

## Reviewer Notes

Worth a look: the re-prepare race handling (the lock spans delete,
teardown
and prepare; a racing winner's entry is re-validated against the loser's
tensors), the freeze applied when a replacement is served to a capturing
call,
and the two disclosed blind spots above.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Setup state is now refreshed automatically when setup-input tensors
change in place before capture.
* Added `StaleSetupError` for cases where changed inputs cannot be
safely refreshed, including after a binding is frozen or when staleness
is detected during capture.
* Setup statistics now report re-preparations and stale-state refusals.
* **Tests**
* Added coverage for input changes, views, inference tensors, capture
behavior, and teardown failures.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Code <noreply@anthropic.com>

### [0e09318](https://github.com/flashinfer-ai/flashinfer/commit/0e0931876325f3997b834b99036cf2155254332d)

- **作者**: Vadim Gimpelson
- **时间**: 2026-11-13T21:54:12Z
- **提交信息**: fix(testing,autotuner): flush L2 by reading so cold-L2 timing excludes dirty writeback (#9374)

# PR description

<!-- .github/pull_request_template.md -->

## 📌 Description

The cold-L2 flush in `bench_gpu_time_with_cupti`,
`bench_gpu_time_with_cuda_event` and the autotuner (`cold_l2_profile`
and the CUPTI profiling path) evicts L2 with `buffer.zero_()` on a 2x-L2
(3x in the autotuner CUPTI path) buffer. A write leaves L2 full of dirty
lines. The flush kernel itself is outside the timed window, but the next
kernel, which is the one being measured, has to write those lines back
to DRAM while it streams its own operands. On B200 this adds a roughly
constant 8-9 us to a memory-bound BF16 GEMM, independent of the kernel,
so `cold_l2_cache=True` overstates kernel time and compresses the
relative gaps between backends.

This PR adds `flashinfer.utils.make_l2_flush(num_bytes, device)`, which
allocates a read-only int64 buffer and an output scalar once and evicts
L2 with `torch.sum(buffer, dim=0, out=out)`. The buffer is never
written, so L2 is left holding clean lines and the writeback of whatever
was dirty happens inside the flush, outside the timed window. All six
flush sites in `flashinfer/testing/utils.py` and both autotuner sites
use it. Flush sizes are unchanged.

### Measurements

NVIDIA B200 (148 SMs, L2 126.5 MiB), torch 2.15.0+cu132, cuDNN 9.26.0,
`mm_bf16` BF16, default tactic, timed with `bench_gpu_time_with_cupti`
(`dry_run_time_ms=25`, `repeat_time_ms=100`, `use_cuda_graph=False`),
median of 3 repeats, standard error <= 0.01 us.

"Rotate weights" is the reference for a correct cold-L2 measurement: no
flush, and each iteration uses a different copy of the weights so they
are not resident in L2, while L2 holds only clean lines. "Warm" reuses
the same weights with no flush.

| Shape (M x N x K) | Backend | `zero_()` flush (before) | read flush
(this PR) | rotate weights (reference) | warm |
|---|---|---|---|---|---|
| 160 x 7168 x 8448 (weights 115.5 MiB) | cuDNN | 33.25 us | 24.29 us |
24.96 us | 24.99 us |
| 160 x 7168 x 8448 (weights 115.5 MiB) | cuBLASLt | 33.25 us | 24.26 us
| 24.99 us | 24.99 us |
| 160 x 4096 x 4096 (weights 32 MiB) | cuDNN | 13.60 us | 11.33 us |
11.33 us | 9.86 us |
| 160 x 4096 x 4096 (weights 32 MiB) | cuBLASLt | 13.60 us | 11.30 us |
11.33 us | 9.82 us |

The read flush matches the rotating-weights reference, and on the 32 MiB
shape, whose weights fit in L2, it stays slower than warm, so it still
evicts. The penalty of the old flush is the same for every kernel, which
identifies it as the cost of the state the flush leaves rather than of
the GEMM.

The autotuner's cold chain (one flush, then 8 launches on separate
weight copies) paid this penalty only on the first launch, about 1 us
per launch here, so tactic choices change little. After this change its
numbers agree with the standalone benchmark for M=160, N=7168, K=8448:

| Backend (best tactic) | `bench_gpu_time_with_cupti`, before -> after |
autotuner, before -> after |
|---|---|---|
| cuBLASLt | 31.23 -> 23.01 us | 25.09 -> 23.55 us |
| cuDNN | 33.18 -> 24.22 us | 26.11 -> 24.58 us |
| CUTLASS | 39.26 -> 30.02 us | 33.54 -> 32.00 us |

## 🔍 Related Issues

None.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues. (Ran `pre-commit run --files` on the four
changed files; all hooks pass.)

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
reviewers may adjust): `tests/autotuner/`

`test_cold_l2_profile_uses_full_flush_buffer` tracked the int8
allocation of the zero-filled buffer; it now checks the size passed to
`make_l2_flush`, so it still asserts a full 2x-L2 flush.
`tests/autotuner/test_autotuner_core.py`,
`tests/autotuner/test_timer_preparation.py` and
`tests/autotuner/test_cupti_distributed.py` pass on B200 (190 passed).


## Reviewer Notes

- Absolute times reported with `cold_l2_cache=True` drop for
memory-bound kernels (about 8-9 us for the B200 GEMMs above, less for
smaller working sets). Comparisons against numbers collected before this
change are not like for like.
- The autotuner's persisted L2 policy string is still `"cold"`, so
tuning caches written with the old flush are reused without re-tuning.
The effect on the chosen tactics is small (the cold chain paid the
penalty once per 8 launches), but if reviewers prefer, the policy
identity can be bumped to invalidate them.
- The read flush on the 115.5 MiB shape measures about 0.7 us below the
rotating-weights reference. Its cause has not been investigated; it does
not affect the comparison with the old flush.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Benchmark profiling and timing runs now flush the device cache when
cache flushing is enabled. Cache flushing remains inactive when
disabled, and existing device selection and flush-size settings are
preserved.
* Autotuner profiling now uses the same cache-flushing approach for its
event-based and CUPTI measurement paths.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: Vadim Gimpelson <vadim.gimpelson@gmail.com>

### [45c9bcc](https://github.com/flashinfer-ai/flashinfer/commit/45c9bcc781309442765755e0515a46f5450cb2cc)

- **作者**: Akaash Parthasarathy
- **时间**: 2026-11-13T21:13:37Z
- **提交信息**: test(attention): update paged cuDNN capability checks (#9459)

### [545d9e9](https://github.com/flashinfer-ai/flashinfer/commit/545d9e9e878352e607413a13860cb3de288f95dc)

- **作者**: Yang Xu
- **时间**: 2026-11-13T18:40:19Z
- **提交信息**: Enable FP16 in the qualified H100 paged attention auto domain (#9453)

<!-- .github/pull_request_template.md -->

## 📌 Description

Enable matching FP16 Q/K/V/output in the existing H100 D256
paged-attention auto domain. Previously these inputs retained FA3 even
where the corresponding BF16 configuration used cuDNN. The production
change is limited to the dtype predicate; existing hardware,
actual-length work, feature and capture guards remain.

Parameterize the public retained-capture, runtime-scale and owned-table
growth tests over BF16 and FP16, add CPU mixed-precision rejection
coverage, and document the shared domain. Short-query FA2 and workloads
below the existing paired-work floor retain their native provider.

On NVIDIA H100 80GB HBM3 (132 SMs), an independent, predeclared 432-case
FP16 study completed with all numerical/lifecycle checks passing. The
262 newly admitted routes achieved geometric-mean native/auto speedups
of **1.293x warm graph replay** and **1.298x completed eager batches**.
Neither metric had a >5% slowdown persistent in both AB/BA orders. The
170 unchanged native controls measured candidate/native ratios of
1.00453 / 1.00389; their 99% intervals, [1.00219, 1.00700] / [1.00165,
1.00621], satisfied the prospectively specified [0.99, 1.01] equivalence
range. These are not claims of identical measured time.

Three stock CLI examples below independently pass `--refcheck` and
resolve ordinary `auto` to cuDNN. B1, D256, HND/page16, causal FP16;
official FE 1.32.3, actual loaded cuDNN 9.24.0.43, Torch 2.14.1+cu130.
These use the CLI's cold-L2 default and CUDA-event whole-graph timing,
with five warmups and 30 observations. Compilation/startup are outside
timing.

| Hq/Hkv | Q/KV | FA3 (us) | auto(cuDNN) (us) | Speedup |
|---|---|---:|---:|---:|
| 48/48 | 1023/1023 | 101.592 | 82.570 | 1.230x |
| 32/8 | 65/16383 | 547.443 | 410.853 | 1.332x |
| 16/1 | 65/16164 | 530.654 | 399.874 | 1.327x |

Reproduce the middle row with the current branch; substitute the head
and length arguments from the table for the other rows:

```bash
python benchmarks/flashinfer_benchmark.py --routine BatchPrefillWithPagedKVCacheWrapper --backends fa3 auto --batch_size 1 --s_qo 65 --s_kv 16383 --num_qo_heads 32 --num_kv_heads 8 --head_dim_qk 256 --head_dim_vo 256 --page_size 16 --q_dtype float16 --kv_dtype float16 --causal --use_cuda_events --refcheck --num_iters 30 --dry_run_iters 5 -v
```


## 🔍 Related Issues

Extends #9451 (merged H100 BF16 admission and capture-capacity
handling).

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
- [x] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets: `tests/cpu/attention
tests/attention/test_cudnn_paged_hopper_auto.py`

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

- Tested head: `531b6790a5954bb9e939bb500f1d2044f933cb0f`. All 770 CPU
attention tests, 1,728 actual planner route checks, 48 public BF16/FP16
GPU lifecycle cases, and all 432 independent cases pass; no GPU skips.
The old source fails the new FP16 positive work-boundary control.
- Changed-file pre-commit hooks pass. Repository-wide hooks were not
run, following the scoped validation guidance; the corresponding
template checkbox stays unchecked.
- No native kernel, binding, FE ranking, provider API, allocation-policy
or lifetime change. FROST opt-in is unset; ordinary FE default selection
chose backend engine 9. Existing BF16 tolerances are unchanged; new FP16
output checks use 0.002 absolute/relative tolerances.
- Host submission alone was 2.110x the native path in the independent
study. The completed-eager improvement is not a claim of reduced CPU
cost or serving TTFT. Whole-graph timings are distinct from pure-kernel
CUPTI measurements.
- The CLI processes exit successfully but retain nanobind shutdown leak
diagnostics, also present with the same counts in the preceding BF16 CLI
run. Those logs are preserved; this change makes no process-lifetime
leak claim.
- Implemented and validated with AI assistance (Codex).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Automatic cuDNN selection for H100 paged attention now supports FP16
inputs in addition to BF16, provided query, key, value, and output use
the same precision. Mixed-precision inputs remain unsupported.
* **Documentation**
* Updated the H100 paged-attention guidance to include FP16 as an
eligible dtype. Other selection requirements remain unchanged.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [88077bd](https://github.com/flashinfer-ai/flashinfer/commit/88077bda83a714a61740baacc829beb491f4446b)

- **作者**: Chunan Zeng
- **时间**: 2026-11-13T17:51:34Z
- **提交信息**: perf(gemm): let the mm_mxfp8 autotuner rank CuTe-DSL and cuDNN on SM107 (#9020)

## 📌 Description

On SM107, `mm_mxfp8(backend="auto")` resolves to `["cutlass"]` alone, so
the autotuner never times the CuTe-DSL or cuDNN MXFP8 kernels against
it. A caller who wants the CuTe-DSL kernel has to pass
`backend="cute-dsl"`, and then cuDNN is never timed either. On SM107,
cuDNN's kernels (2-CTA, B-reuse, 2x2 or 2x4 clusters) beat the best
CuTe-DSL tactic on some large prefill shapes, with bitwise-equal output.

Changes:
- `_heuristic_func_mm_mxfp8`: on SM107, when CUTLASS is suitable, return
`["cutlass", "cute-dsl", "cudnn"]`, keeping each only if it is suitable
for the inputs. CUTLASS stays first, so an untuned call or a cache miss
still runs CUTLASS exactly as before. Under autotuning, `choose_one`
ranks all of them. Other architectures keep `["cutlass"]`, as
`_heuristic_func_mm_fp4` adds `cute-dsl` only on SM107.
- `mm_mxfp8`: use `_MM_MXFP8_CUTE_DSL_TUNING_CONFIG` (CUDA-graph,
cold-L2 profiling) whenever `cute-dsl` is among the candidates, so every
candidate is timed the same way. With the gate, this only changes SM107
`auto` tuning; explicit backends are unchanged.
- cuDNN runner `get_valid_tactics`: a graph cuDNN declines
(`cudnnGraphNotSupportedError` / `RuntimeError`) now yields no tactics
instead of raising, so `auto` tuning ranks the remaining candidates
instead of failing.

### Results (SM107, one GPU)

DeepSeek-V4.1 dense MXFP8 GEMM shapes. Ratio = time of `backend="auto"`
after autotuning / time of `backend="cute-dsl"` after autotuning; CUDA
graph of 10 calls. Every row's output is bitwise equal to the CuTe-DSL
output.

| M x N x K | `auto` picks | ratio |
|---|---|---|
| 16384 x 25600 x 6144 | cuDNN `256x256_128x6_2x4f_2cta_x2_Breuse` |
0.76 |
| 16384 x 5120 x 8192 | cuDNN `256x256_128x6_2x2f_2cta_x2_Breuse` | 0.85
|
| 16384 x 32768 x 1280 | cuDNN `256x256_128x6_2x4f_2cta_x2_Breuse` |
0.94 |
| 16384 x 1792 x 5120 | cuDNN | 1.06 |
| 16384 x 4096 x 1280 | CuTe-DSL | 0.99 |
| 512 x {5120x8192, 32768x1280, 1792x5120} | CuTe-DSL | 0.99-1.00 |

The 1792x5120 row is a near-tie: the tuner's measurement favored cuDNN,
but the later timing did not.

In an end-to-end DeepSeek-V4.1 prefill benchmark (SGLang, 16K tokens per
GPU), hand-routing just the first two shapes to cuDNN made the step 1.1%
faster. With this change the tuner makes that choice itself, and picks
up the third shape as well.

### Why SM107 only (B300 measurement)

An earlier revision of this PR applied the wider list on every
architecture. On B300, with the same 10 shapes, `auto` tuned before vs
after, two GPUs, every output bitwise equal:

- Autotune time went from 25 s to 193 s.
- wq_b (16384x32768x1280) was 1.03-1.04x and wo_b (16384x5120x8192)
1.04-1.08x slower, timed with warm repeated calls.
- The Engram shape (16384x25600x6144) was 0.78-0.91x.

The slowdowns came from the tuning-config switch, not the extra
candidates. Tuning only CUTLASS under the CuTe-DSL config already made
wq_b 1.02-1.03x slower, while the three candidates under the old config
were 0.99-1.00x on both shapes. The old config, however, takes 274 s to
tune. B200 was not measured. So other architectures keep CUTLASS-only
`auto`.

### Notes

- **Cache shadowing:** the tuner caches a winner per runner and returns
the first runner in the list that has one. A winner cached for the
CuTe-DSL runner, from an earlier `backend="cute-dsl"` tuning in the same
process or a loaded cache file, still wins the lookup for `auto`, and
cuDNN is not timed. This behavior already exists and is not changed
here; re-tune with `auto` to rank cuDNN.
- **Tuning time on SM107:** `auto` now also JIT-compiles the CuTe-DSL
tactics it profiles (cached in memory only, so once per process) and
builds cuDNN graphs per tactic and M bucket. Measured in a fresh process
with an empty CuTe-DSL cache, over the 10 shapes above (each call tuning
every M bucket):

  | candidates | autotune time |
  |---|---|
  | before: `auto` = CUTLASS | 64 s |
  | explicit `backend="cute-dsl"` | 183 s |
  | after: `auto` = CUTLASS + CuTe-DSL + cuDNN | 251 s |

A caller already tuning `cute-dsl` pays +68 s; a default-`auto` caller
on SM107 pays +187 s.

## 🔍 Related Issues

SGLang hand-routes these shapes to cuDNN in sgl-project/sglang#48971
until the autotuner can pick it.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues. (Run on the changed files.)

## 🧪 Tests

- [x] Tests have been added or updated as needed:
`test_mm_mxfp8_auto_ranks_cute_dsl_and_cudnn_after_cutlass` checks the
candidate list for three SM107 suitability cases and that SM100 and
SM103 keep `["cutlass"]`, and
`test_mm_mxfp8_cudnn_runner_declined_graph_has_no_tactics` checks the
declined-graph path with override-shape on and off.
- [ ] All tests are passing: the new tests (7 cases) pass on SM107 and
on B300 (SM103) against v0.7.2 with this PR's code changes applied,
which is also where the measurements come from. With the gate, `auto` on
B300 lists `["cutlass"]` as before. The full `test_mm_mxfp8.py` has not
been run on main yet (CI run requested).
- [ ] This PR requires **full-scope** CI, not targeted tests.

  Suggested CI test targets: `tests/gemm/test_mm_mxfp8.py`

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Improvements**
* Automatic MXFP8 backend selection can consider CuTe-DSL and, when
suitable, cuDNN after CUTLASS. Untuned calls continue to use CUTLASS
first.
* CuTe-DSL tuning settings apply whenever CuTe-DSL is selected,
including in combination with other backends.
* **Bug Fixes**
* If cuDNN cannot build a supported MXFP8 graph, its tactics are skipped
so automatic backend selection can continue with other available
options.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [e1a6fd4](https://github.com/flashinfer-ai/flashinfer/commit/e1a6fd43acf79ee83f5d086e0a5ef456fa055600)

- **作者**: Yang Xu
- **时间**: 2026-11-13T16:49:47Z
- **提交信息**: Enable workload-bounded H100 D256 paged cuDNN auto dispatch (#9451)

<!-- .github/pull_request_template.md -->

## 📌 Description

Enable cuDNN auto dispatch for sufficiently large BF16 D256 paged
attention on H100 80GB HBM3 (132 SMs), using released FE 1.32.3 and
cuDNN 9.24. The native selector must first choose FA3. Admission counts
actual causal query-key pairs across heads and requires `Hq * sum(q_i *
(2 * kv_i - q_i + 1) // 2) >= 2**24`; short/small work retains FA2/FA3.
Paired CPU lengths prevent mostly empty ragged batches from qualifying
through large declared maxima.

The supported domain is causal HND/page16, batches 1–32, query heads
16–48, GQA groups 1/2/4/8/16, Q maxima 65–16384 and KV maxima up to
32768, with positive Q≤KV per request and exact declarations. Existing
masks/window/sinks/split/runtime checks remain. The change adds no
device readback, FE ranking rule or engine override.

A graph-mode wrapper that already owns a native schedule keeps that
provider so retained captures remain valid. A cuDNN-first wrapper may
fall back while refreshing the metadata used by its old captures. Hopper
uses exact cuDNN declarations; Blackwell bucket/admission functions and
the native provider selector remain unchanged.

This changes automatic backend selection only in the documented H100
domain. Public signatures and explicit provider selection are unchanged.
Graph-mode owned cuDNN tables reserve their index capacity independently
of declaration bucketing, including for explicit cuDNN requests.
AI-assisted implementation and self-review; independently approved at
the final head. Targeted actual CI completed successfully: [run
43458797136](https://github.com/flashinfer-ai/flashinfer/actions/runs/43458797136).

## 🔍 Related Issues

Uses the cuDNN 9.24 capability support landed in #9351. This H100
extension requires no new FE release or kernel implementation.

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
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/attention/test_cudnn_paged_hopper_auto.py
tests/attention/test_cudnn_wrapper_regressions.py`

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

Final-head validation at `f0644a29d830872d75739f80e4fe7ee2087a8d74`,
based on main `ae58183fa8a21324c92a1bf2ad2ec658339cfed8`:

- Actual final-head CI: H100 192 passed / 112 predefined skips, CPU
10,062 passed / 20 skips, all six AOT import matrix jobs and all three
provider lint jobs passed. CI tested a merge tree identical to the
qualified head.
- 528 local CPU attention tests, 752 actual-planner route checks and
changed-file pre-commit hooks pass. Repository-wide hooks/full CI have
not run, so those template checkboxes remain unchecked.
- All 24 public H100 GPU tests pass, zero skips/failures: both
initial-provider orders, Q64/65 and actual-work boundaries, retained
O/LSE captures, changed values/page maps, nondefault streams and
non-unit runtime scales.
- At the preceding head `323d0a65416beed2074b0fd5aa8293cfe9e1fabd`, all
320 independent cases pass O/LSE numerical and lifecycle checks,
including all-row provider comparison and sampled FP64 references.
Inputs were frozen before implementing the work floor. An earlier
broader candidate's failing results were retained as development
evidence and are not counted as this independent qualification.
- Official FE 1.32.3, actual cuDNN 9.24.0.43, Torch 2.14.1+cu130, CUDA
13.2, CUDA DSL 13.4, H100 80GB HBM3 / 132 SMs. Native FA2/FA3 AOT is
source-compatible and JIT is disabled.
`CUDNN_FRONTEND_ENABLE_FROST_ENGINES` is unset. All 173 changed routes
use default-selected cuDNN backend engine 9.

The final capacity fix was verified with a red/green GPU control:
Q65/KV8112 first uses 507 pages of a 512-index reservation; planning
KV8192 previously raised `captured cuDNN block table cannot grow` in
both O/O+LSE cases. Both fail on the old production code and all 24
tests pass on the fixed head. The new tests capture at the larger bound
and validate shorter/longer replans; storage reservation does not extend
an older capture's declared limits. The B1 table payload grows from 2028
to 2048 bytes. This does not establish full serving memory headroom.

The final production diff changes only owned-table capacity
construction. The prior 320-case study always supplies caller-owned
tables, so it does not enter the modified branch; dispatch predicates,
exact declarations and execution are unchanged. Its figures below remain
explicitly measurements of `323d0a6`, not a rerun of all 320 cases at
the final head.

The complete 173-case changed-route population improves warmed
whole-graph replay by **1.260x** and completed-eager latency by
**1.266x**, with no case >5% slower in both execution orders.
Candidate/baseline ratio 99% intervals are [0.78145, 0.80661] and
[0.77841, 0.80275]. All 147 unchanged FA2/FA3 controls pass the
preregistered equivalence gate: intervals [0.99837, 1.00211] and
[0.99865, 1.00222], also with zero both-order >5% losses. This is a
bounded performance gate, not a claim that every admitted shape is
faster.

Absolute examples from the complete qualification (`experiment.py`, warm
O-only, BF16/D256/HND/page16). Values are means of the two per-order
medians:

| B, Hq/Hkv, actual Q, actual KV | Native graph → auto graph (µs) |
Native completed eager → auto completed eager (µs) |
|---|---:|---:|
| 1, 48/48, 1023, 1023 | 100.990 → 83.668 | 101.810 → 83.379 |
| 1, 32/32, 65, 16383 | 539.289 → 418.480 | 539.303 → 418.505 |
| 1, 16/16, 65, 16164 | 530.596 → 426.706 | 531.617 → 426.387 |
| Worst admitted graph ratio: 4, 32/32, [65,64,32,1],
[3265,3265,3265,3265] | 152.136 → 158.427 | 152.878 → 158.008 |

The qualification baseline is the same runtime with only the new H100
predicate disabled during initial planning; no monkeypatch is active
during execution/timing. Each arm/order retains 10 observations of 32
replays and 32 eager calls, after warmup. Replay uses CUDA events around
the whole graph; eager wall time includes completion synchronization.
Plan, compilation, first execution and reference work are excluded and
recorded separately. This does not establish cold-start, vLLM
memory-headroom or serving TTFT gains; for example the 1023-token case
above spent approximately 1.31 s in its first cuDNN O+LSE call versus
0.20 ms for FA3, including preparation/compilation not isolated by that
measurement.

Public reproduction of provider selection and the first uniform shape:

```bash
python benchmarks/flashinfer_benchmark.py \
  --routine BatchPrefillWithPagedKVCacheWrapper \
  --backends fa3 auto --batch_size 1 --s_qo 1023 --s_kv 1023 \
  --num_qo_heads 48 --num_kv_heads 48 \
  --head_dim_qk 256 --head_dim_vo 256 --page_size 16 \
  --q_dtype bfloat16 --kv_dtype bfloat16 --causal \
  --use_cuda_events --refcheck --num_iters 30 --dry_run_iters 5 -v
python -m pytest tests/attention/test_cudnn_paged_hopper_auto.py -q
```

Verify actual imports/backend version and `auto(cudnn)` /
`resolved_backend`. This public CLI uses its cold-L2 rotating-buffer
method, unlike the warm qualification above; its eager CUDA-event option
is not completed-eager wall time. The CLI command was executed on the
final head and passed its FA3/cuDNN cross-provider reference check; it
is not the source of the warm table above. The public tests directly
reproduce provider/lifetime boundaries; all 320 qualification cases,
including slow cases, were retained in the complete analysis.

Final-head public CLI results on the same H100/FE/runtime (cold-L2
CUDA-event graph, 30 measured iterations, 5 warmup iterations; one fresh
process per shape):

| B, Hq/Hkv, Q, KV | FA3 (µs) | auto(cuDNN) (µs) |
|---|---:|---:|
| 1, 48/48, 1023, 1023 | 99.722 | 81.920 |
| 1, 32/32, 65, 16383 | 542.546 | 423.067 |
| 1, 16/16, 65, 16164 | 526.774 | 432.899 |

For the other two rows, replace only Q/KV and both head counts in the
command above. All three reported `auto(cudnn)` and passed the CLI
reference comparison. These examples supplement the complete
qualification; they are not a new holdout or serving benchmark.
Process-shutdown nanobind reference-leak warnings were retained; all
processes completed successfully.

Review the actual-length arithmetic, fail-closed metadata guards and
native-first/cuDNN-first capture transitions. The `2**24` floor is an
empirical broad-work criterion validated on independent inputs, not an
architectural theorem. Other Hopper models, FP16 and serving performance
need separate qualification.

### [ae58183](https://github.com/flashinfer-ai/flashinfer/commit/ae58183fa8a21324c92a1bf2ad2ec658339cfed8)

- **作者**: Yang Xu
- **时间**: 2026-11-13T08:45:15Z
- **提交信息**: feat(attention): support explicit cuDNN paged sliding windows (#9411)

<!-- .github/pull_request_template.md -->

## 📌 Description

Explicit `backend="cudnn"` paged prefill currently rejects
`window_left`, although the low-level cuDNN path already supports it.
Pass the existing window argument through prepared metadata and the
scaled/non-prepared execution path. Preserve FlashInfer's inclusive
window convention and the low-level conversion to cuDNN bounds.

Prepared execution also checks the window after a legacy `forward()`
override, so changing the window cannot reuse a graph with the previous
mask. Add retained-capture and FP64 O/LSE tests covering changed
lengths/page mappings, strided Q, scale fallback, nondefault streams and
legacy window changes. Automatic admission continues to exclude windows
pending separate performance qualification.

## 🔍 Related Issues

Independent of the cuDNN attention-sinks plumbing in #6288 and the sinks
argument guard in #9410.

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
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/attention/test_cudnn_paged_window.py
tests/attention/test_cudnn_wrapper_regressions.py tests/cpu/attention`

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

Validation on this exact source: 207 focused CPU contract tests pass;
all 16 new GPU test nodes pass with zero skips on both B200 and B300
using cuDNN 9.24 and FE 1.33 source with matching native bindings.
Changed-file pre-commit hooks pass. The all-files/full-suite checkboxes
remain unchecked because those checks were not run.

This adds explicit wrapper support and makes no performance,
released-wheel or serving claim. Backend and FROST use the same public
preparation/execution contract.

Implemented with Codex assistance.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Explicit cuDNN paged attention plans now support left-window limits in
prepared and scaled execution. Causal plans also limit keys to the
aligned query position; noncausal plans may include later valid keys.
The window setting remains fixed during retained graph capture.
* **Documentation**
* Clarified window boundaries, bottom-right query alignment, and that a
negative window disables the limit. Automatic paged-plan admission
continues to exclude windowed plans.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [99ecf60](https://github.com/flashinfer-ai/flashinfer/commit/99ecf60281e7dfe0e8035ecf668a9e1cfafa2f5e)

- **作者**: Yang Xu
- **时间**: 2026-11-13T07:49:43Z
- **提交信息**: fix(ci): prefetch metadata before parallel provider spec lint (#9441)

<!-- .github/pull_request_template.md -->

## 📌 Description

Parallel provider spec generation can fail on a cold artifact cache when
a metadata download holds its lock longer than another architecture's
30-second wait. The waiter fails and the pool kills the still-running
downloader, cancelling otherwise unrelated CI lanes.

Prefetch the pinned TRT-LLM manifests and metadata/export headers before
starting a parallel lint pool. Reuse the generators' artifact cache,
checksum validation and export-header lists. A prefetch failure stops
before arch workers launch; download timeouts/retries and all provider
coverage remain unchanged. Serial/single-provider invocations keep their
existing path. No kernel binaries are prefetched.

## 🔍 Related Issues

Observed in #9411, [PR Test attempt
2](https://github.com/flashinfer-ai/flashinfer/actions/runs/43310546434/attempts/2).
This separate CI fix does not waive or retry that PR's failed gate.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

Scoped hooks passed for all four changed files; repository-wide
formatting was not run.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: targeted CPU coverage plus the standard provider-lint/AOT matrix
is sufficient; no GPU kernel or dispatch change.

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/cpu/jit/test_prefetch_jit_spec_headers.py
tests/cpu/jit/test_jit_spec_gencode_lint.py`

Validation completed locally:
- 35 CPU tests pass, including manifest/header failure, fail-fast
ordering and existing provider rules.
- Real cold prefetch of 3 pinned manifests/34 headers, followed by
fresh-process offline reuse, passes with CUDA uninitialized.
- Real parallel provider lint for 8.0, 10.0a and 10.3a passes on CUDA
13.3 with downloads disabled.
- Scoped pre-commit, Ruff and shell syntax checks pass.

Actual CI is pending; local CUDA 13.3 does not substitute for its CUDA
matrix. The original contention mechanism was reproduced with a
synthetic delayed response and test-only shortened lock wait; production
limits are unchanged.

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

Please review the prefetch-before-pool failure boundary and artifact
identity reuse. Prepared with Codex assistance; source, failure logs and
behavioral checks were reviewed.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Developer Tooling**
* Parallel provider architecture linting now prepares required
specification headers before starting. If preparation fails, linting
stops with an error instead of proceeding with incomplete inputs.
* **Documentation**
* Updated development guidance to explain the pre-lint step, its
validation and download limits, and its behavior when required headers
are unavailable.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [95955e7](https://github.com/flashinfer-ai/flashinfer/commit/95955e7c6b7cb0effc9db0f8405615e763f25146)

- **作者**: eigen
- **时间**: 2026-11-13T05:47:46Z
- **提交信息**: fix(cake_gdn): GDN prefill accepts element-aligned initial/output state and checkpoints (#9434)

The 292 Cake GDN (gated delta rule) chunked prefill variants span 56
CUDA units. They cover BF16 and FP16 inputs/outputs; FP32, BF16, FP16,
FP8 E4M3 and FP8 E5M2 recurrent state; runs with or without an initial
state; indexed state pools; periodic state checkpoints; full-dv and
dv-split layouts; and gated and ungated forms. This PR changes all 292
so that state that is element aligned but not 16-byte aligned no longer
stops with CUDA "misaligned address". Each unit now compiles in two
flavors. When every state pointer and slot stride is a multiple of 16
bytes, the host selects the previous code, unchanged, with identical
SASS. Otherwise it selects a flavor that checks each access's address
and falls back to scalar accesses that produce the same bits. Compared
with the previous Cake version (FlashInfer main at
a63f775b5c150704dd66e4fad9aac4dd2acf8e83), per-row speedups on
16-byte-aligned state range from 0.997x to 1.018x, which is parity. On
misaligned state, shapes where the previous units faulted now run, and
shapes where they already ran show speedups from 0.964x to 1.012x (mean
latency in us, eager launches and CUDA-graph replays, same GPU for both
sides; speedup = previous latency / this PR latency, above 1 means
faster).

The 112 decode variants are not changed by this PR, and the family ships
on sm_100a, sm_103a and sm_107a.

### 16-byte-aligned state

**NVIDIA B200 (sm_100a), CUDA 13.4**: 16-byte-aligned state; previous
Cake units vs this PR; mean latency (us), eager and CUDA graph

| io / state dtype | state | shape | eager previous | eager this PR |
eager speedup | graph previous | graph this PR | graph speedup |
|---|---|---|---:|---:|---:|---:|---:|---:|
| BF16 / BF16 | indexed pool | Hq 16, Hv 16, 4 x 2048 tokens | 65.57 |
65.52 | 1.001x | 64.85 | 64.78 | 1.001x |
| BF16 / BF16 | initial state | Hq 16, Hv 32, 2 x 4096 tokens | 117.22 |
117.13 | 1.001x | 115.58 | 115.51 | 1.001x |
| BF16 / FP8 E4M3 | initial state | Hq 16, Hv 32, 2 x 4096 tokens |
120.40 | 120.42 | 1.000x | 118.17 | 118.18 | 1.000x |
| BF16 / FP8 E5M2 | initial state | Hq 16, Hv 32, 2 x 4096 tokens |
119.53 | 119.58 | 1.000x | 118.02 | 118.00 | 1.000x |
| FP16 / FP32 | initial state, no gates | Hq 16, Hv 32, 2 x 4096 tokens
| 118.06 | 118.13 | 0.999x | 116.53 | 116.59 | 1.000x |
| FP16 / FP32 | initial state | Hq 16, Hv 32, 2 x 4096 tokens | 118.67 |
118.69 | 1.000x | 116.78 | 116.93 | 0.999x |
| FP16 / FP32 | initial state | Hq 16, Hv 32, 1 x 8192 tokens | 220.13 |
220.33 | 0.999x | 218.77 | 218.68 | 1.000x |
| BF16 / FP16 | initial state | Hq 16, Hv 32, 2 x 4096 tokens | 119.75 |
119.82 | 0.999x | 118.07 | 118.11 | 1.000x |
| BF16 / FP32 | initial state | Hq 16, Hv 32, 2 x 4096 tokens | 116.97 |
116.98 | 1.000x | 115.46 | 115.31 | 1.001x |
| BF16 / FP32 | initial state | Hq 16, Hv 32, 8 x 1024 tokens | 84.22 |
84.24 | 1.000x | 83.34 | 83.28 | 1.001x |
| BF16 / BF16 | initial state | Hq 16, Hv 32, 8 x 1024 tokens | 82.90 |
82.98 | 0.999x | 82.18 | 82.09 | 1.001x |
| BF16 / BF16 | indexed pool | Hq 32, Hv 32, 32 x 256 tokens | 115.98 |
116.22 | 0.998x | 115.47 | 115.63 | 0.999x |
| BF16 / BF16 | initial state | Hq 16, Hv 32, 32 x 256 tokens | 105.09 |
105.06 | 1.000x | 104.42 | 104.42 | 1.000x |
| FP16 / FP32 | initial state | Hq 16, Hv 32, 32 x 256 tokens | 120.89 |
120.90 | 1.000x | 120.49 | 120.43 | 1.000x |
| BF16 / FP32 | initial state | Hq 16, Hv 32, 32 x 256 tokens | 107.16 |
107.12 | 1.000x | 106.32 | 106.44 | 0.999x |
| BF16 / BF16 | indexed pool, checkpoints every 64 | Hq 4, Hv 8, 4 x
1024 tokens | 73.74 | 73.71 | 1.000x | 73.63 | 73.64 | 1.000x |
| BF16 / FP32 | initial state | Hq 16, Hv 32, 16 seqs, 1 to 8192 tokens
| 254.16 | 254.19 | 1.000x | 252.47 | 252.32 | 1.001x |
| BF16 / BF16 | initial state | Hq 16, Hv 32, 16 seqs, 1 to 8192 tokens
| 252.42 | 252.70 | 0.999x | 250.89 | 250.80 | 1.000x |
| BF16 / FP32 | no initial state | Hq 16, Hv 32, 4 x 2048 tokens | 72.60
| 72.58 | 1.000x | 71.86 | 71.70 | 1.002x |
| FP16 / FP32 | no initial state | Hq 16, Hv 32, 4 x 2048 tokens | 72.53
| 72.42 | 1.001x | 71.63 | 71.56 | 1.001x |
| BF16 / FP32 | no initial state | Hq 16, Hv 32, 2 x 4096 tokens |
115.45 | 115.45 | 1.000x | 113.97 | 113.92 | 1.000x |

**NVIDIA GB300 (sm_103a), CUDA 13.4**: 16-byte-aligned state; previous
Cake units vs this PR; mean latency (us), eager and CUDA graph

| io / state dtype | state | shape | eager previous | eager this PR |
eager speedup | graph previous | graph this PR | graph speedup |
|---|---|---|---:|---:|---:|---:|---:|---:|
| BF16 / FP32 | initial state | Hq 16, Hv 32, 2 x 4096 tokens | 107.66 |
107.55 | 1.001x | 107.61 | 107.49 | 1.001x |
| BF16 / BF16 | initial state | Hq 16, Hv 32, 2 x 4096 tokens | 108.39 |
108.42 | 1.000x | 108.44 | 108.54 | 0.999x |
| BF16 / BF16 | indexed pool | Hq 16, Hv 16, 4 x 2048 tokens | 60.85 |
60.85 | 1.000x | 60.86 | 60.83 | 1.000x |
| BF16 / FP8 E4M3 | initial state | Hq 16, Hv 32, 2 x 4096 tokens |
109.90 | 109.81 | 1.001x | 109.81 | 109.76 | 1.000x |
| BF16 / FP8 E5M2 | initial state | Hq 16, Hv 32, 2 x 4096 tokens |
109.89 | 109.90 | 1.000x | 109.86 | 109.87 | 1.000x |
| FP16 / FP32 | initial state | Hq 16, Hv 32, 2 x 4096 tokens | 108.80 |
108.78 | 1.000x | 108.69 | 108.68 | 1.000x |
| FP16 / FP32 | initial state | Hq 16, Hv 32, 1 x 8192 tokens | 201.06 |
201.06 | 1.000x | 201.05 | 200.94 | 1.000x |
| FP16 / FP32 | initial state | Hq 16, Hv 16, 4 x 2048 tokens | 56.62 |
56.63 | 1.000x | 56.69 | 56.69 | 1.000x |
| BF16 / FP16 | initial state | Hq 16, Hv 32, 2 x 4096 tokens | 110.82 |
110.84 | 1.000x | 110.76 | 110.78 | 1.000x |
| BF16 / FP32 | initial state | Hq 16, Hv 32, 8 x 1024 tokens | 76.86 |
76.88 | 1.000x | 76.85 | 76.91 | 0.999x |
| BF16 / BF16 | initial state | Hq 16, Hv 32, 8 x 1024 tokens | 75.68 |
75.73 | 0.999x | 75.71 | 75.60 | 1.002x |
| BF16 / BF16 | indexed pool | Hq 32, Hv 32, 32 x 256 tokens | 108.28 |
108.42 | 0.999x | 108.35 | 108.56 | 0.998x |
| BF16 / BF16 | initial state | Hq 16, Hv 32, 32 x 256 tokens | 97.38 |
97.67 | 0.997x | 97.58 | 97.72 | 0.999x |
| FP16 / FP32 | initial state | Hq 16, Hv 32, 32 x 256 tokens | 109.79 |
109.65 | 1.001x | 109.67 | 109.63 | 1.000x |
| BF16 / FP32 | initial state | Hq 16, Hv 32, 32 x 256 tokens | 100.09 |
100.14 | 0.999x | 100.13 | 100.22 | 0.999x |
| BF16 / BF16 | indexed pool, checkpoints every 64 | Hq 4, Hv 8, 4 x
1024 tokens | 69.85 | 69.68 | 1.002x | 69.77 | 69.65 | 1.002x |
| BF16 / FP32 | initial state | Hq 16, Hv 32, 16 seqs, 1 to 8192 tokens
| 232.15 | 232.34 | 0.999x | 231.98 | 232.26 | 0.999x |
| BF16 / BF16 | initial state | Hq 16, Hv 32, 16 seqs, 1 to 8192 tokens
| 230.90 | 230.86 | 1.000x | 230.66 | 230.71 | 1.000x |
| BF16 / FP32 | no initial state | Hq 16, Hv 32, 4 x 2048 tokens | 66.74
| 66.82 | 0.999x | 66.78 | 66.84 | 0.999x |
| FP16 / FP32 | no initial state | Hq 16, Hv 32, 4 x 2048 tokens | 66.85
| 66.85 | 1.000x | 66.73 | 66.84 | 0.998x |
| BF16 / FP32 | no initial state | Hq 16, Hv 32, 2 x 4096 tokens |
106.38 | 106.37 | 1.000x | 106.39 | 106.25 | 1.001x |

**NVIDIA VR200 (sm_107a), CUDA 13.5**: 16-byte-aligned state; previous
Cake units vs this PR; mean latency (us), eager and CUDA graph

| io / state dtype | state | shape | eager previous | eager this PR |
eager speedup | graph previous | graph this PR | graph speedup |
|---|---|---|---:|---:|---:|---:|---:|---:|
| BF16 / FP32 | initial state | Hq 16, Hv 32, 2 x 4096 tokens | 85.77 |
85.68 | 1.001x | 85.75 | 85.72 | 1.000x |
| BF16 / BF16 | initial state | Hq 16, Hv 32, 2 x 4096 tokens | 86.10 |
86.09 | 1.000x | 86.14 | 86.22 | 0.999x |
| BF16 / FP16 | initial state | Hq 16, Hv 32, 2 x 4096 tokens | 90.82 |
90.76 | 1.001x | 90.75 | 90.85 | 0.999x |
| BF16 / FP8 E4M3 | initial state | Hq 16, Hv 32, 2 x 4096 tokens |
84.74 | 84.73 | 1.000x | 84.82 | 84.78 | 1.000x |
| BF16 / FP8 E5M2 | initial state | Hq 16, Hv 32, 2 x 4096 tokens |
84.70 | 84.61 | 1.001x | 84.62 | 84.80 | 0.998x |
| FP16 / FP32 | initial state | Hq 16, Hv 32, 2 x 4096 tokens | 85.86 |
85.86 | 1.000x | 86.05 | 85.90 | 1.002x |
| FP16 / FP32 | initial state | Hq 16, Hv 32, 1 x 8192 tokens | 163.52 |
163.39 | 1.001x | 163.39 | 163.52 | 0.999x |
| BF16 / FP32 | no initial state | Hq 16, Hv 32, 2 x 4096 tokens | 84.39
| 84.50 | 0.999x | 84.46 | 84.46 | 1.000x |
| FP16 / FP32 | no initial state | Hq 16, Hv 32, 2 x 4096 tokens | 84.49
| 84.48 | 1.000x | 84.59 | 84.58 | 1.000x |
| FP16 / FP32 | no initial state, checkpoints every 64 | Hq 2, Hv 4, 8 x
1024 tokens | 35.74 | 35.80 | 0.998x | 35.87 | 35.84 | 1.001x |
| BF16 / BF16 | indexed pool | Hq 16, Hv 16, 4 x 2048 tokens | 47.71 |
47.65 | 1.001x | 47.79 | 47.68 | 1.002x |
| BF16 / BF16 | indexed pool, checkpoints every 64 | Hq 4, Hv 8, 4 x
1024 tokens | 37.48 | 36.82 | 1.018x | 37.30 | 36.83 | 1.013x |
| BF16 / FP32 | initial state | Hq 16, Hv 32, 32 x 256 tokens | 59.43 |
59.52 | 0.999x | 59.46 | 59.48 | 1.000x |
| BF16 / BF16 | initial state | Hq 16, Hv 32, 32 x 256 tokens | 60.95 |
60.66 | 1.005x | 60.83 | 60.59 | 1.004x |
| FP16 / FP32 | initial state | Hq 16, Hv 32, 32 x 256 tokens | 58.73 |
58.74 | 1.000x | 58.77 | 58.75 | 1.000x |
| BF16 / FP32 | initial state | Hq 4, Hv 16, 32 x 128 tokens (one CTA
per tile) | 32.78 | 32.64 | 1.004x | 32.83 | 32.78 | 1.002x |
| BF16 / BF16 | initial state | Hq 4, Hv 16, 32 x 128 tokens (one CTA
per tile) | 31.09 | 30.93 | 1.005x | 31.15 | 30.91 | 1.008x |
| FP16 / FP32 | initial state | Hq 4, Hv 16, 32 x 128 tokens (one CTA
per tile) | 32.54 | 32.62 | 0.998x | 32.82 | 32.70 | 1.004x |
| BF16 / BF16 | initial state | Hq 16, Hv 32, 8 x 1024 tokens | 59.10 |
59.15 | 0.999x | 59.05 | 59.14 | 0.998x |
| BF16 / FP32 | no initial state | Hq 16, Hv 32, 8 x 1024 tokens | 56.50
| 56.50 | 1.000x | 56.52 | 56.48 | 1.001x |
| FP16 / FP32 | no initial state | Hq 16, Hv 32, 8 x 1024 tokens | 56.42
| 56.41 | 1.000x | 56.45 | 56.56 | 0.998x |
| BF16 / FP32 | initial state | Hq 16, Hv 32, 8 x 1024 tokens | 60.03 |
60.12 | 0.999x | 59.98 | 60.10 | 0.998x |
| BF16 / BF16 | initial state | Hq 16, Hv 32, 4 x 4096 tokens | 98.78 |
98.80 | 1.000x | 98.91 | 98.90 | 1.000x |
| FP16 / FP32 | initial state | Hq 16, Hv 32, 4 x 4096 tokens | 96.40 |
96.23 | 1.002x | 96.46 | 96.35 | 1.001x |
| BF16 / FP32 | no initial state | Hq 16, Hv 32, 4 x 4096 tokens | 95.10
| 95.14 | 1.000x | 95.10 | 95.19 | 0.999x |
| FP16 / FP32 | no initial state | Hq 16, Hv 32, 4 x 4096 tokens | 94.90
| 94.94 | 1.000x | 95.08 | 95.04 | 1.000x |
| BF16 / BF16 | indexed pool | Hq 32, Hv 32, 32 x 256 tokens | 76.85 |
76.93 | 0.999x | 76.91 | 77.06 | 0.998x |
| BF16 / FP32 | initial state | Hq 16, Hv 32, 16 seqs, 1 to 8192 tokens
| 166.14 | 166.03 | 1.001x | 166.30 | 165.96 | 1.002x |
| BF16 / BF16 | initial state | Hq 16, Hv 32, 16 seqs, 1 to 8192 tokens
| 167.21 | 167.21 | 1.000x | 167.25 | 167.38 | 0.999x |
| FP16 / FP32 | initial state | Hq 16, Hv 32, 16 seqs, 1 to 8192 tokens
| 166.58 | 166.50 | 1.000x | 166.81 | 166.60 | 1.001x |
| BF16 / FP32 | no initial state | Hq 16, Hv 32, 16 seqs, 1 to 8192
tokens | 163.29 | 163.58 | 0.998x | 163.30 | 163.48 | 0.999x |
| BF16 / FP32 | initial state | Hq 16, Hv 32, 1 x 16384 tokens | 316.51
| 316.44 | 1.000x | 316.53 | 316.40 | 1.000x |

### State that is not 16-byte aligned

**NVIDIA B200 (sm_100a), CUDA 13.4**: state that is element aligned but
not 16-byte aligned; mean latency (us), eager and CUDA graph; "fault" =
the previous units stop with "misaligned address"

| io / state dtype | state layout | shape | eager previous | eager this
PR | eager speedup | graph previous | graph this PR | graph speedup |
|---|---|---|---:|---:|---:|---:|---:|---:|
| BF16 / FP32 | initial state 2 elements off | Hq 16, Hv 32, 2 x 4096
tokens | 116.07 | 115.56 | 1.004x | 114.56 | 113.70 | 1.008x |
| BF16 / FP32 | initial state 1 element off | Hq 16, Hv 32, 2 x 4096
tokens | 116.10 | 115.62 | 1.004x | 114.62 | 114.00 | 1.006x |
| BF16 / BF16 | initial state 1 element off | Hq 16, Hv 32, 2 x 4096
tokens | fault | 114.86 | - | fault | 113.52 | - |
| BF16 / FP32 | initial state 1 element off | Hq 16, Hv 32, 32 x 256
tokens | fault | 154.69 | - | fault | 154.33 | - |
| BF16 / BF16 | initial state 2 elements off | Hq 16, Hv 32, 8 x 1024
tokens | fault | 92.65 | - | fault | 91.96 | - |
| BF16 / BF16 | initial state 1 element off | Hq 16, Hv 32, 8 x 1024
tokens | fault | 92.56 | - | fault | 92.02 | - |
| BF16 / FP32 | initial + output state 1 element off | Hq 16, Hv 32, 8 x
1024 tokens | fault | 107.15 | - | fault | 106.56 | - |
| BF16 / FP32 | output state 1 element off, no initial state | Hq 16, Hv
32, 4 x 2048 tokens | fault | 79.72 | - | fault | 79.34 | - |
| FP16 / FP32 | initial state 1 element off | Hq 16, Hv 32, 1 x 8192
tokens | 218.90 | 219.53 | 0.997x | 218.18 | 218.93 | 0.997x |
| BF16 / FP8 E4M3 | initial state 1 element off | Hq 16, Hv 32, 2 x 4096
tokens | fault | 117.83 | - | fault | 116.57 | - |
| BF16 / FP16 | initial state 1 element off | Hq 16, Hv 32, 2 x 4096
tokens | 119.24 | 119.09 | 1.001x | 117.38 | 117.40 | 1.000x |
| FP16 / FP32 | checkpoints 1 element off, every 64 tokens | Hq 2, Hv 4,
8 x 1024 tokens | 63.33 | 63.21 | 1.002x | 63.30 | 63.20 | 1.002x |
| BF16 / BF16 | indexed pool, slot stride padded by 257 elements | Hq
16, Hv 16, 4 x 2048 tokens | 65.97 | 65.58 | 1.006x | 65.34 | 64.68 |
1.010x |
| BF16 / BF16 | indexed pool + checkpoints, slot stride padded by 257
elements | Hq 4, Hv 8, 4 x 1024 tokens | 74.15 | 74.51 | 0.995x | 74.22
| 74.63 | 0.994x |

**NVIDIA GB300 (sm_103a), CUDA 13.4**: state that is element aligned but
not 16-byte aligned; mean latency (us), eager and CUDA graph; "fault" =
the previous units stop with "misaligned address"

| io / state dtype | state layout | shape | eager previous | eager this
PR | eager speedup | graph previous | graph this PR | graph speedup |
|---|---|---|---:|---:|---:|---:|---:|---:|
| BF16 / FP32 | initial state 2 elements off | Hq 16, Hv 32, 2 x 4096
tokens | 107.84 | 107.38 | 1.004x | 108.09 | 107.35 | 1.007x |
| BF16 / FP32 | initial state 1 element off | Hq 16, Hv 32, 2 x 4096
tokens | 107.71 | 107.15 | 1.005x | 107.98 | 107.40 | 1.005x |
| BF16 / BF16 | initial state 1 element off | Hq 16, Hv 32, 2 x 4096
tokens | fault | 108.26 | - | fault | 108.50 | - |
| BF16 / FP32 | initial state 1 element off | Hq 16, Hv 32, 32 x 256
tokens | fault | 144.06 | - | fault | 144.00 | - |
| BF16 / BF16 | initial state 2 elements off | Hq 16, Hv 32, 8 x 1024
tokens | fault | 85.74 | - | fault | 85.74 | - |
| BF16 / BF16 | initial state 1 element off | Hq 16, Hv 32, 8 x 1024
tokens | fault | 85.46 | - | fault | 85.45 | - |
| BF16 / FP32 | initial + output state 1 element off | Hq 16, Hv 32, 8 x
1024 tokens | fault | 100.12 | - | fault | 99.93 | - |
| BF16 / FP32 | output state 1 element off, no initial state | Hq 16, Hv
32, 4 x 2048 tokens | fault | 73.72 | - | fault | 74.02 | - |
| FP16 / FP32 | initial state 1 element off | Hq 16, Hv 32, 1 x 8192
tokens | 201.20 | 201.16 | 1.000x | 201.34 | 201.02 | 1.002x |
| BF16 / FP8 E4M3 | initial state 1 element off | Hq 16, Hv 32, 2 x 4096
tokens | fault | 109.68 | - | fault | 110.26 | - |
| BF16 / FP16 | initial state 1 element off | Hq 16, Hv 32, 2 x 4096
tokens | 111.06 | 110.99 | 1.001x | 111.22 | 110.98 | 1.002x |
| FP16 / FP32 | checkpoints 1 element off, every 64 tokens | Hq 2, Hv 4,
8 x 1024 tokens | 59.33 | 59.35 | 1.000x | 59.47 | 59.41 | 1.001x |
| BF16 / BF16 | indexed pool, slot stride padded by 257 elements | Hq
16, Hv 16, 4 x 2048 tokens | 61.42 | 61.33 | 1.001x | 61.66 | 61.42 |
1.004x |
| BF16 / BF16 | indexed pool + checkpoints, slot stride padded by 257
elements | Hq 4, Hv 8, 4 x 1024 tokens | 70.11 | 70.05 | 1.001x | 70.30
| 70.20 | 1.001x |

**NVIDIA VR200 (sm_107a), CUDA 13.5**: state that is element aligned but
not 16-byte aligned; mean latency (us), eager and CUDA graph; "fault" =
the previous units stop with "misaligned address"

| io / state dtype | state layout | shape | eager previous | eager this
PR | eager speedup | graph previous | graph this PR | graph speedup |
|---|---|---|---:|---:|---:|---:|---:|---:|
| BF16 / FP32 | initial state 2 elements off | Hq 16, Hv 32, 2 x 4096
tokens | 86.10 | 85.54 | 1.006x | 86.07 | 85.58 | 1.006x |
| BF16 / FP32 | initial state 1 element off | Hq 16, Hv 32, 2 x 4096
tokens | fault | 85.14 | - | fault | 85.25 | - |
| BF16 / BF16 | initial state 1 element off | Hq 16, Hv 32, 2 x 4096
tokens | fault | 84.94 | - | fault | 85.37 | - |
| BF16 / FP32 | initial state 1 element off | Hq 16, Hv 32, 32 x 256
tokens | fault | 64.58 | - | fault | 64.84 | - |
| BF16 / BF16 | initial state 2 elements off | Hq 16, Hv 32, 8 x 1024
tokens | 59.25 | 58.54 | 1.012x | 59.26 | 58.69 | 1.010x |
| BF16 / BF16 | initial state 1 element off | Hq 16, Hv 32, 8 x 1024
tokens | fault | 58.05 | - | fault | 58.46 | - |
| BF16 / FP32 | initial + output state 1 element off | Hq 16, Hv 32, 8 x
1024 tokens | fault | 62.15 | - | fault | 62.24 | - |
| BF16 / FP32 | output state 1 element off, no initial state | Hq 16, Hv
32, 4 x 2048 tokens | fault | 52.64 | - | fault | 52.74 | - |
| FP16 / FP32 | initial state 1 element off | Hq 16, Hv 32, 1 x 8192
tokens | fault | 163.72 | - | fault | 163.89 | - |
| BF16 / FP8 E4M3 | initial state 1 element off | Hq 16, Hv 32, 2 x 4096
tokens | fault | 84.60 | - | fault | 84.73 | - |
| BF16 / FP16 | initial state 1 element off | Hq 16, Hv 32, 2 x 4096
tokens | fault | 84.66 | - | fault | 84.84 | - |
| FP16 / FP32 | checkpoints 1 element off, every 64 tokens | Hq 2, Hv 4,
8 x 1024 tokens | fault | 46.42 | - | fault | 46.44 | - |
| BF16 / BF16 | indexed pool, slot stride padded by 257 elements | Hq
16, Hv 16, 4 x 2048 tokens | 49.59 | 49.86 | 0.995x | 49.59 | 49.89 |
0.994x |
| BF16 / BF16 | indexed pool + checkpoints, slot stride padded by 257
elements | Hq 4, Hv 8, 4 x 1024 tokens | 38.42 | 39.67 | 0.968x | 38.33
| 39.74 | 0.964x |


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Cake GDN prefill now supports state buffers and slot strides that are
element-aligned but not 16-byte-aligned, including checkpoint buffers.
* Kernel selection adapts to buffer alignment while preserving token
outputs, final states, and checkpoints.
* **Documentation**
* Updated Cake GDN backend guidance to describe supported alignment and
kernel selection.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Xiufan Liang <xiufanl@nvidia.com>

### [9b69c0e](https://github.com/flashinfer-ai/flashinfer/commit/9b69c0e18a13c353bd6229d70780fd14dd19ff82)

- **作者**: Brian K. Ryu
- **时间**: 2026-11-13T03:07:28Z
- **提交信息**: feat(batch_invariant): `sampling_from_probs` / `sampling_from_logits` under `batch_invariant=True` (#9365)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

Second batch invariant sampling kernel PR.
`flashinfer.sampling.sampling_from_probs(probs, ..., seed=, offset=,
batch_invariant=True)` and `sampling_from_logits(logits, ..., seed=,
offset=, batch_invariant=True)` draw one token per row with a specified,
fingerprinted dataflow whose bits depend on the row's values and its
`(seed, offset)` alone. Without the flag both entries are unchanged.

Batch invariant mode accepts every argument the non-BI path accepts and
honors each one's meaning, with the exception of `deterministic`, which
is ignored as the BI mode is deterministic by construction. The RNG is
incompatible across BI and non-BI mode.

**Contract.** bf16 / f16 / fp32 inputs of shape `(..., N)`, any `N` up
to 2^21 (beyond it only where the row's alignment admits a configuration
within the class's share bound of 512 elements per thread; an fp32 row
beyond 2^21 is unsupported); `indices` int32 / int64 (the gather; the
output takes its dtype; an index outside the source rows makes its
output row invalid: token -1); one key per output row as above;
deterministic ignored; `check_nan` the same host check; `return_valid`
the class's validity; `int32` tokens; `M = 0` launches nothing. Anything
else raises `BatchInvariantUnsupportedError`; nothing falls back. SM100
/ SM103 / SM107.

### Performance

Method: `flashinfer.testing.bench_gpu_time(enable_cupti=True,
cold_l2_cache=True, use_cuda_graph=False)`, median; bf16 rows, N {32768,
128256, 152064} x M {1, 8, 64, 512, 4096}; the flag against the
operator's default (non-BI) `sampling_from_probs` /
`sampling_from_logits` (`deterministic=True`) given the fp32 input its
kernels take (a 16-bit input is cast to fp32 inside the default path,
which costs 1.4-6x more than the numbers below; the class reads the bf16
rows as they are). Cells: default us / ours us (default / ours; above 1:
ours is faster).

**Vera Rubin (SM107), `sampling_from_probs`**

| N \ M | 1 | 8 | 64 | 512 | 4096 |
|---|---|---|---|---|---|
| 32768 | 3.6 / 9.3 (0.39x) | 8.7 / 9.6 (0.91x) | 11.3 / 9.4 (1.20x) |
22.6 / 16.4 (1.38x) | 130.5 / 66.7 (1.96x) |
| 128256 | 5.5 / 9.6 (0.57x) | 25.7 / 9.6 (2.67x) | 34.8 / 16.0 (2.18x)
| 66.1 / 51.1 (1.29x) | 355.3 / 285.6 (1.24x) |
| 152064 | 6.5 / 9.6 (0.68x) | 29.8 / 9.9 (3.03x) | 40.2 / 23.4 (1.72x)
| 76.3 / 99.4 (0.77x) | 411.1 / 618.6 (0.66x) |

**Vera Rubin (SM107), `sampling_from_logits`**

| N \ M | 1 | 8 | 64 | 512 | 4096 |
|---|---|---|---|---|---|
| 32768 | 9.1 / 9.4 (0.97x) | 9.3 / 9.7 (0.96x) | 9.6 / 10.6 (0.91x) |
26.8 / 19.6 (1.37x) | 165.4 / 92.2 (1.79x) |
| 128256 | 28.3 / 9.8 (2.89x) | 28.8 / 11.1 (2.60x) | 29.2 / 20.5
(1.43x) | 85.4 / 73.2 (1.17x) | 556.0 / 386.4 (1.44x) |
| 152064 | 33.0 / 10.8 (3.05x) | 33.7 / 12.2 (2.76x) | 34.0 / 31.3
(1.09x) | 99.7 / 147.8 (0.67x) | 652.3 / 928.7 (0.70x) |

Regime geomeans (default / ours; min): probs decode 1.02x (0.39x), mid
1.35x (0.77x), prefill 1.17x (0.66x); logits decode 1.97x (0.96x), mid
1.07x (0.67x), prefill 1.22x (0.70x).

**B200 (SM100), `sampling_from_probs`**

| N \ M | 1 | 8 | 64 | 512 | 4096 |
|---|---|---|---|---|---|
| 32768 | 4.5 / 16.2 (0.28x) | 10.1 / 16.5 (0.61x) | 13.4 / 16.7 (0.80x)
| 34.3 / 24.1 (1.42x) | 215.6 / 106.0 (2.03x) |
| 128256 | 6.7 / 16.6 (0.41x) | 28.7 / 16.8 (1.71x) | 39.3 / 20.2
(1.94x) | 95.6 / 89.3 (1.07x) | 575.6 / 548.0 (1.05x) |
| 152064 | 7.8 / 16.6 (0.47x) | 34.8 / 17.9 (1.94x) | 45.3 / 47.3
(0.96x) | 109.6 / 180.6 (0.61x) | 664.4 / 1194.3 (0.56x) |

**B200 (SM100), `sampling_from_logits`**

| N \ M | 1 | 8 | 64 | 512 | 4096 |
|---|---|---|---|---|---|
| 32768 | 12.0 / 16.2 (0.74x) | 12.1 / 17.3 (0.70x) | 12.4 / 16.9
(0.73x) | 41.3 / 30.0 (1.38x) | 271.2 / 142.4 (1.90x) |
| 128256 | 38.4 / 17.1 (2.25x) | 38.9 / 17.6 (2.21x) | 39.3 / 26.4
(1.49x) | 145.4 / 125.3 (1.16x) | 994.3 / 755.0 (1.32x) |
| 152064 | 44.9 / 17.2 (2.62x) | 45.4 / 17.8 (2.56x) | 45.9 / 62.8
(0.73x) | 171.4 / 264.4 (0.65x) | 1175.5 / 1787.5 (0.66x) |

Regime geomeans (default / ours; min): probs decode 0.69x (0.28x), mid
1.06x (0.61x), prefill 1.06x (0.56x); logits decode 1.61x (0.70x), mid
0.97x (0.65x), prefill 1.18x (0.66x).

### Framework Integration plan 

Plan upon a FlashInfer release that carries this PR

1. **vLLM.** Its sampler (`vllm/v1/sample/ops/topk_topp_sampler.py`)
sends only top-k / top-p rows to FlashInfer and routes every unfiltered
row and every request with a per-request generator to its torch sampler.
A PR against its batch-invariant mode routes the unfiltered rows to
`sampling_from_probs(..., batch_invariant=True)` and turns each
request's generator into a per-row `(seed, offset)` key, so a seeded
request no longer forces the torch path and its draw no longer depends
on its slot; the filtered rows follow when the support family lands.
2. **SGLang.** Its FlashInfer sampling backend
(`python/sglang/srt/layers/sampler.py`) calls the filtered samplers only
and asserts that sampling seeds are unsupported there. A PR adds the
unfiltered branch on `sampling_from_probs(..., batch_invariant=True)`
with the request's seed as the per-row key; the filtered branches and
the seed assertion go with the support family.
3. **verl and Miles** sample through these engines and need no change of
their own; Miles's true-on-policy mode gets the engine's draw and the
trainer's `log_probs` from one class (the drawn token's renormalised
log-probability equals `log_probs` at its id).
4. **NeMo RL** re-scores under the sampler's parameters
(`TrainingSamplingParams`, the sampler-replay support); its vLLM
generation path takes item 1, and the sampler-replay support is served
by the coming support entries.

## 🔍 Related Issues

<!-- Link any related issues here -->

#8999
#9009

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

* **New Features**
* Added opt-in batch-invariant sampling from probabilities and logits,
with reproducible draws based on each output row’s seed and offset.
* Added optional row gathering, temperature scaling for logits, and
automatic or explicit configuration selection.
* Probability sampling can return a validity mask; logits sampling can
return log-probabilities. Invalid rows produce token `-1`.
* Added a `batch_invariant` option to the existing probability and
logits sampling functions; the default behavior remains unchanged.
* **Documentation**
* Expanded sampling documentation with input requirements, random-stream
behavior, and output details.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [c07ac28](https://github.com/flashinfer-ai/flashinfer/commit/c07ac287f2e18a1fd9f3369485cb69e3af91fb39)

- **作者**: Akaash Parthasarathy
- **时间**: 2026-11-13T02:12:54Z
- **提交信息**: bench(moe_ep): cover MegaMoE variants and input policies on SM107 (#9339)

<!-- .github/pull_request_template.md -->

## 📌 Description

Extend the SM107 MegaMoE benchmark to select inference or GenPhase and
accept prequantized activations. Add completed eager-call timing
alongside CUDA-event timing.

An optional JSON workload list runs several configurations in one
distributed process group. Results retain the resolved configuration and
imported package path so comparisons can check what ran.

Run the SM107 reference, routing-graph, autotuning and variant-selection
suites through the distributed test runner on CUDA 13 Rubin lanes. Share
EP dependency setup with the unit runner and reject launches missing
distributed rank metadata.

## 🔍 Related Issues

None.

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
reviewers may adjust): `tests/cpu/test_sm107_benchmark.py`

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

* **Improvements**
* Benchmark runs can select validated workload cases by expert-parallel
size and report graph and eager results, including per-rank performance.
* Timing results distinguish CUDA-event measurements from eager
execution through completion, with optional prequantized-forward timing.
* GenPhase runs support validated heuristic settings and capacity
limits.
* Results include the selected kernel variant, input policy, and
expanded environment details.
  * Non-finite oracle errors are rejected.
* **Tests**
* Added coverage for testlist validation, case selection, timing
metadata, setup ordering, and benchmark output routing.
* SM107 multi-GPU tests run only on compatible CUDA and device
configurations, with required test dependencies configured
automatically.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [6a26a3b](https://github.com/flashinfer-ai/flashinfer/commit/6a26a3bc7cb5d23692244b8f0fdace00c1aaf9b3)

- **作者**: amitz-nv
- **时间**: 2026-11-13T02:10:28Z
- **提交信息**: feat(moe): support routing weights before FC2 for NVFP4 (#9260)

## 📌 Description

Add optional routing weighting before GEMM2-input NVFP4 quantization for
BF16-rounded soft-clamped ReLU² (`ClampedRelu2`). Checkpoints calibrated
with expert activations weighted before the down projection need this to
reproduce the activation distribution they were calibrated on.

- Adds `routing_weights_before_fc2=False` to `cute_dsl_fused_moe` and
the `CuteDslMoEWrapper` constructor. The wrapper `run()` signature and
default behavior are unchanged. Reuses the existing
`clamped_relu2_limit` tensor.
- **GEMM1 does the weighting in its epilogue.** The gather grouped GEMM1
(`blockscaled_contiguous_gather_grouped_gemm_act_fusion`) gets a
`routing_weights` mode for non-gated ClampedRelu2 with NVFP4 output. Its
epilogue rounds the FC1 output to BF16 and applies the BF16-rounded soft
clamp and square. It then multiplies by each route's weight (also
BF16-rounded) and quantizes to NVFP4 with one FC2 input scale per local
expert. FC2 does not reapply the routing weights.
- **No BF16 FC1 buffer.** The weighted activation is quantized straight
from the accumulator, so nothing of size `tokens × top_k × intermediate`
in BF16 is allocated, and neither is a permuted copy of the input. At
32,768 tokens, top-8, intermediate 8192, that buffer alone was 4 GiB per
GPU.
- **Rounding is fixed.** Every rounding step is pinned with inline PTX
(`cvt.rn.bf16.f32`, `div.full.f32`, `tanh.approx.f32`), so results do
not depend on compiler choices. Outputs are bitwise identical to a
reference that stores the BF16 FC1 output and quantizes it separately
(tests below).
- `moe_permute` can now permute FP4 block scales (row-major input,
128x4-swizzled output). Callers that permute scales themselves, such as
`CudnnGroupedGemmNvfp4Runner`, still pass no scale buffers; passing only
one of the two is rejected.
- **Validation.** The pre-FC2 path validates every operand it hands to
the GEMMs as raw pointers, before any GPU routing:
  - activation and weight layouts
  - weight-scale dtype, size and device
  - per-expert float32 alphas
  - routing metadata
  - the output buffer
- **PDL.** The chain `moe_sort` → GEMM1 → GEMM2 honors `enable_pdl`.

**Performance and memory.** GB300 (SM103), hidden 4096, intermediate
8192, 256 experts with 16 local (expert parallelism over 16 ranks),
top-8, fused finalize. The baseline stores the BF16 GEMM1 output and
runs a separate Triton weighting/quantization kernel. GPU times are
CUDA-graph replays; peak extra memory is per call.

| Tokens | Baseline GPU (ms) | **This PR GPU (ms)** | Baseline eager
(ms) | **This PR eager (ms)** | Baseline peak extra | **This PR peak
extra** |
|---:|---:|---:|---:|---:|---:|---:|
| 128 | 0.128 | **0.121** | 0.49 | **0.36** | 35.4 MiB | **13.0 MiB** |
| 2,048 | 0.155 | **0.132** | 0.46 | **0.34** | 377 MiB | **80.6 MiB** |
| 8,192 | 0.257 | **0.223** | 0.46 | **0.37** | 1.44 GiB | **0.29 GiB**
|
| 32,768 | 0.723 | **0.661** | 0.74 | **0.67** | 5.70 GiB | **1.14 GiB**
|

Outputs are bitwise identical to the baseline at every size. In an
internal end-to-end vLLM deployment on 16 GB300 GPUs, serving throughput
is unchanged within run-to-run noise.

## 🔍 Related Issues

No public issue linked.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

Changed-file checks pass: ruff, ruff-format, mypy 1.17.1, clang-format
19.1.1, whitespace/EOF. The full repository was not checked.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/moe/test_routed_nvfp4.py
tests/trace/test_cute_dsl_pre_fc2_reference.py
tests/moe/test_unified_moe_cudnn_grouped_gemm.py
tests/moe/test_cute_dsl_fused_moe.py
tests/trace/test_fi_trace_template_consistency.py`

Validated on NVIDIA GB300 (SM103):

- `tests/moe/test_routed_nvfp4.py` +
`tests/trace/test_cute_dsl_pre_fc2_reference.py --full`: 187 passed.
Covers:
- Bitwise equality of the fused GEMM1 epilogue against a separate
BF16-FC1 + Triton reference quantizer (kept under `tests/` as the
oracle). This includes small, calibrated (~448) and saturating FP8 block
scales, two clamp limits, BF16 and FP32 weights, single and per-expert
FC2 scales, and a case with FP4 output offsets above 2^31 bytes.
  - PyTorch references for the weighted quantization.
  - Permutation with and without scales.
- Graph replay with changed routes, including a rank with no local
routes.
  - Validation before routing.
  - Three-route BF16 reduction order.
- `tests/moe/test_unified_moe_cudnn_grouped_gemm.py` with cuDNN 9.28.1:
282 passed.
-
`tests/moe/test_cute_dsl_fused_moe.py::TestCuteDslFusedMoeFunctional::test_clamped_relu2_accuracy
--full`: 4 passed (default path unchanged).
- `tests/trace/test_fi_trace_template_consistency.py -k cute_dsl`: 36
passed.

The full test suite was not run.

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

- **Supported mode:**
  - W4A4, ClampedRelu2, BF16 output
  - SM100/SM103, 128-aligned widths
  - single-CTA 128x128 tactic for both GEMMs
- The gather GEMM's `routing_weights` mode rejects other tile shapes and
clusters, since bit-exactness was validated only for this tactic.
- **Rejected:** per-token scaling, swap-AB, localized weights, explicit
4over6 recipes.
- **Reference oracle.** The epilogue mirrors the reference quantizer op
by op: `div.full.f32` as Triton lowers `/`, `tanh.approx.f32`, BF16
rounding after FC1, after the soft clamp, after squaring and after
weighting, `amax * (gs / 6)` for the E4M3 block scale, and `gs / scale`
(0 for a zero scale) before E2M1 packing. The reference Triton quantizer
lives only in the tests as the oracle; the library no longer ships a
separate quantization kernel for this path.
- **Possible follow-up:** this path pins the single-CTA 128x128 tactic.
Larger GEMM tiles could help large batches, but would need their own
bitwise validation.

Developed with AI assistance.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Haobin Guo <haobing@nvidia.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-11-14
**监控日期**: 2026-11-13
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4814
- **最后更新**: 2026-11-13T06:32:55Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-11-14
**监控日期**: 2026-11-13
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34919
- **最后更新**: 2026-11-13T23:14:11Z

## 提交统计

- **昨日提交总数**: 5
- **提交者数量**: 4
- **主要提交者**: Steven Liu, Sayak Paul, YiYi Xu

## AI分析总结

# huggingface/diffusers 昨日提交分析

## 1. 主要更新类型

- **功能新增**：模型集成 Agent 流程规范、并行化支持条件层
- **Bug修复**：Flux2 LoRA 模块调制参数顺序、外部链接修复
- **维护发布**：0.43.0 版本发布后收尾
- **文档/流程更新**：AI 技能文档、测试规范调整

## 2. 关键变更点及与项目方向的关系

- **Agent 驱动的模型集成流程（#15268）**：这是一个值得关注的方向性变更——项目正在建立 AI Agent 辅助的模型集成规范，包括 Hub 检查点布局标准、`<name>_diffusers/` 目录与 `modular_model_index.json` 的绑定关系，并且决定**不再为每个模型编写基础功能测试**（由统一机制覆盖）。这反映了 diffusers 正在从"每个模型手工集成"转向"标准化、可被 AI 自动化的集成管线"。
- **Flux2 LoRA 顺序修复（#15276）**：修正了 `final_layer.adaLN_modulation` 中 shift/scale 与 diffusers `norm_out` 的 (scale, shift) 顺序不一致问题，与 checkpoint 转换器保持对齐。这是典型的跨框架对齐 Bug，影响 LoRA 微调的正确性。
- **并行化支持条件层（#15246）**：核心库增强，让条件层（如 AdaLN、调制层）能在并行执行模式下工作，属于多 GPU/分布式推理能力的扩展。
- **0.43.0 后发布清理（#15259）**：常规版本维护节奏。

## 3. 对项目的影响和潜在意义

- AI Agent 集成规范的建立意味着未来新增模型的速度可能大幅提升，但**基础测试的移除**需要社区关注——正确性如何保障成为关键问题。
- LoRA 顺序修复直接改善了 Flux2 微调的生产可用性，修复了可能导致微调结果错误的静默 Bug。
- 并行化条件层支持表明项目在向大规模推理场景持续投入。

## 4. 值得关注的技术点

- **`modular_model_index.json` 机制**：新的模型目录组织约定，可能成为未来 Hub 模型加载的标准。
- **AI 协作开发模式**：多个提交由 Claude 生成代码、由核心维护者 review，体现了 AI 辅助开发在该项目中的常态化，`.ai/skills/` 目录的存在说明项目已在沉淀 AI 工作流知识。
- **调制层参数顺序的隐式约定**：diffusers 与原始实现之间对 (scale, shift) 顺序的差异是容易反复出错的领域，转换器需要严格同步。

## 5. 对项目发展的影响

从 README 背景看，diffusers 是 HuggingFace 的开源扩散模型库，核心价值在于**广泛的模型覆盖、易用的 API 和高质量的预训练权重支持**。这批提交体现了三条发展主线：一是通过 Agent 化和标准化降低模型集成门槛，支撑模型覆盖的持续扩张；二是通过细节 Bug 修复保障微调与转换链路的正确性，维持库的可靠性声誉；三是通过并行化等核心能力增强支撑更大规模的使用场景。唯一需要警惕的是取消逐模型测试的决定，它在提升效率的同时对集成流程的自动化正确性验证提出了更高要求，建议社区持续关注后续回归情况。

## 详细提交记录

### [43e3002](https://github.com/huggingface/diffusers/commit/43e30028af5120d8b0868cb6975b9fad39cc4fab)

- **作者**: YiYi Xu
- **时间**: 2026-11-13T22:33:33Z
- **提交信息**: [agents] model integration: Hub checkpoint layout, no per-model tests… (#15268)

* [agents] model integration: Hub checkpoint layout, no per-model tests for base functionality

Co-Authored-By: Claude Fable 5.2 <noreply@anthropic.com>

* Update .ai/references/testing.md

Co-authored-by: Steven Liu <59462357+stevhliu@users.noreply.github.com>

* Update .ai/skills/model-integration/SKILL.md

Co-authored-by: Steven Liu <59462357+stevhliu@users.noreply.github.com>

* Update .ai/skills/model-integration/SKILL.md

Co-authored-by: Steven Liu <59462357+stevhliu@users.noreply.github.com>

* [agents] <name>_diffusers/ folders only work with modular_model_index.json

Co-Authored-By: Claude Fable 5.2 <noreply@anthropic.com>

---------

Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>
Co-authored-by: Steven Liu <59462357+stevhliu@users.noreply.github.com>

### [7475e22](https://github.com/huggingface/diffusers/commit/7475e2229773beb1f77b73b8ba9ca94227b5264e)

- **作者**: Steven Liu
- **时间**: 2026-11-13T18:52:38Z
- **提交信息**: [CI] Fix external links (#15269)

fix links

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

### [afb2c83](https://github.com/huggingface/diffusers/commit/afb2c83d8faf2ff1520135aa331a2b2490b13274)

- **作者**: Sayak Paul
- **时间**: 2026-11-13T12:42:13Z
- **提交信息**: post release 0.43.0 (#15259)

* post release 0.43.0

* style

### [2c58e66](https://github.com/huggingface/diffusers/commit/2c58e66a08a61ea5c58b9add560cf808e2c851de)

- **作者**: Auden Venn
- **时间**: 2026-11-13T06:05:49Z
- **提交信息**: Swap shift and scale in Flux2 LoRAs of final_layer.adaLN_modulation.1 (#15276)

The original final layer orders its modulation (shift, scale) and diffusers'
norm_out (scale, shift). The checkpoint converter swaps the halves; the LoRA
converter now swaps lora_B's halves the same way.

Fixes #15275

Co-authored-by: audenvenn <352980563+audenvenn@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

### [27a5490](https://github.com/huggingface/diffusers/commit/27a54904a7def137c98b6520141873d9a9b08adb)

- **作者**: Sayak Paul
- **时间**: 2026-11-13T04:09:34Z
- **提交信息**: core: support conditional layers in parallelism. (#15246)

* core: support conditional layers in l layers in parallelism.

* up

* debug instead of warning.

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-11-14
**监控日期**: 2026-11-13
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 431
- **最后更新**: 2026-11-12T08:10:11Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-11-14
**监控日期**: 2026-11-13
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13364
- **最后更新**: 2026-11-13T07:56:58Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-11-14
**监控日期**: 2026-11-13
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 38837
- **最后更新**: 2026-11-14T01:52:53Z

## 提交统计

- **昨日提交总数**: 78
- **提交者数量**: 42
- **主要提交者**: Ilyas Mallah, Ziang Li, Manuel Stehle

## AI分析总结

# sgl-project/sglang 昨日提交分析（共 78 条）

## 1. 主要更新类型分布

- **性能优化**约 18 条：涉及 attention 内核（FA3/FA4）、cuda-graph、KDA、Blackwell MoE、SM103 扩散模型、kimi-k3、aarch64 SHA-256 等。
- **Bug 修复**约 28 条：覆盖 mem_cache、HiCache、AMD/NPU 后端、DeepSeek-V4、MoE 路由、调度器、ComfyUI、量化等。
- **功能新增**约 19 条：集中在 rust-server、NPU（EPLB、FP8 KV、HiCache L3）、PD 分离（Mooncake TENT 传输、KV 逻辑页分片）、混合 Mamba 状态检查点、离线工作流转换器等。
- **重构**约 6 条：主要是 mem_cache 统一子池与多模态 processor 分阶段初始化；其余为文档、测试、CI 与依赖升级。

## 2. 关键变更点与项目方向

- **rust-server 持续成熟**（约 11 条）：完善多模态处理、错误分类、GIL 释放、锁竞争与 abort 语义，与 Python 前端行为对齐，并加入 --warmups、--gc-warning-threshold 等运维参数，正被推向生产可用。
- **分布式与 PD 分离深化**：新增 Mooncake TENT 传输引擎、KV 逻辑页分片支持外部后端、HiCache 写回与窗口锁定修复、测试端口冲突修复，服务大规模部署与 KV 分层缓存方向。
- **调度与内存管理**：分块预填在 KV 预算耗尽时正确挂起（#44823），混合 Mamba 状态仅在分叉点与请求结束时检查点（#49886），mem_cache 将 GDN/KDA/KV 区域迁入统一子池，为投机采样与长序列推理提供清晰的内存生命周期。
- **多硬件生态**：AMD 侧 hipMemcpyBatchAsync 批量写回、DCP、topk-v2；NPU 侧 MoE 后端检查、FP8 KV、Mooncake L3 分层缓存（DeepSeek-V4/GLM-5.2）；NVIDIA 侧 Blackwell SM100/SM103 的 swap-AB MoE 与 QKNorm+RoPE 融合内核，体现国产硬件与最新 GPU 架构的双线投入。
- **多模态与生成式扩展**：ComfyUI 离线工作流转换与权重补丁拒绝、Cosmos3 像素网格对齐、Joy 扩散模型 SM103 优化，呼应项目"LLM 与多模态模型"的定位。

## 3. 对项目的影响

调度器与 MoE 路由修复提升生产环境吞吐稳定性；HiCache/disaggregation 修复降低长上下文与 PD 分离场景的正确性风险；rust-server 一致性增强降低迁移门槛；量化融合与 sgl-kernel 0.4.11 发布改善依赖治理与编译效率；deep-gemm 0.2.8、flash-mla 1.0.5 等升级带来底层算子红利。

## 4. 值得关注的技术点

SiLU+mul 稠密融合进入 masked per_token_group_quant，量化链路进一步融合；pinned memory 暂存主机索引上传是 HiCache 数据通路的系统级优化；SM100 上融合 QKNorm+RoPE 的舍入精度保持，体现低精度内核的数值工程处理；q6 按服务并发限界准备，避免 KV 资源被过度预取占用；MM refactor 分阶段重构需持续跟踪后续批次；多个提交由 Claude Opus 5.5 协作生成，反映项目已规模化采用 AI 代码协作流程。

## 5. 整体意义

SGLang 正处于"推理引擎 + 生产服务器"双轨演进期：一边通过 cuda-graph、FA 内核、量化融合压榨单卡性能，一边以 rust-server、PD 分离、HiCache、多后端 KV 分片构建可扩展服务层。本日提交显示社区在保持 NVIDIA 主线性能领先的同时，加速 AMD/NPU 生态适配，系统性偿还 rust-server 与内存管理的技术债，并向扩散模型、ComfyUI 等生成式多模态生态延伸，推动项目从高性能 LLM 推理引擎演进为覆盖多模态生成、多硬件平台的统一推理框架，为后续稳定发布与商业化部署奠定基础。

## 详细提交记录

### [8c7ec05](https://github.com/sgl-project/sglang/commit/8c7ec05287904d88854d9fb5bcbe1a5181282b5e)

- **作者**: metamergebot
- **时间**: 2026-11-13T23:36:19Z
- **提交信息**: [Test] server_args: Stop two PortArgs tests from probing fixed host ports (#50373)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: ZYHowell <ZYHowell@users.noreply.github.com>

### [d7a4948](https://github.com/sgl-project/sglang/commit/d7a494802517661875ee8dd30fbb4e923e4bf31b)

- **作者**: metamergebot
- **时间**: 2026-11-13T23:36:07Z
- **提交信息**: [Feat] quantization: Support dense SiLU+mul fusion for masked per_token_group_quant (#50364)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: windscope <windscope@users.noreply.github.com>

### [aebd76a](https://github.com/sgl-project/sglang/commit/aebd76a5f3d919bd59a8317e74dca53c7536bdfd)

- **作者**: metamergebot
- **时间**: 2026-11-13T23:35:55Z
- **提交信息**: [Perf] [AMD] hicache: Submit staged write-back copies with hipMemcpyBatchAsync on ROCm (#50363)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: zx3xyy <zx3xyy@users.noreply.github.com>

### [a1bc580](https://github.com/sgl-project/sglang/commit/a1bc580cfdb11d72d9313400dc2572f5adc4ce18)

- **作者**: metamergebot
- **时间**: 2026-11-13T23:35:43Z
- **提交信息**: [Fix] hicache: Lock the window a staged buffer-mode load-back keeps (#49917)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: ZYHowell <ZYHowell@users.noreply.github.com>

### [257ba63](https://github.com/sgl-project/sglang/commit/257ba631d4c1b304c84d879ab056c2c4a1ede0aa)

- **作者**: metamergebot
- **时间**: 2026-11-13T23:35:31Z
- **提交信息**: [Feat] kv-shard: Let out-of-tree backends and pools join logical-page KV sharding (#49636)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: ZYHowell <ZYHowell@users.noreply.github.com>

### [9521f57](https://github.com/sgl-project/sglang/commit/9521f578b7ce624a338a7667874ef6645ec0d77e)

- **作者**: Dayuxiaoshui
- **时间**: 2026-11-13T23:20:25Z
- **提交信息**: [Feat] disaggregation: Add opt-in Mooncake TENT transfer engine backend for PD (#47025)

Signed-off-by: staryxchen <staryxchen@tencent.com>
Co-authored-by: Shangming Cai <csmthu@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Stary <staryxchen@tencent.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [3e4d7bd](https://github.com/sgl-project/sglang/commit/3e4d7bd0c5cf1a18beeb505194aa9433b3263867)

- **作者**: Baizhou Zhang
- **时间**: 2026-11-13T22:40:34Z
- **提交信息**: [Chore] flash-attn: Restore the kernels-hub FA3 loader and the kernel… (#50394)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [d6bc9e7](https://github.com/sgl-project/sglang/commit/d6bc9e7272c7705c48b4c6e9789e11a0fda2f227)

- **作者**: metamergebot
- **时间**: 2026-11-13T22:38:53Z
- **提交信息**: [Perf] rust-server: Keep a multimodal item's identity on the item so its feature is hashed once (#50199)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [108ffbd](https://github.com/sgl-project/sglang/commit/108ffbdc5bb679830070ac9e7154a84c1a9561f8)

- **作者**: metamergebot
- **时间**: 2026-11-13T22:38:26Z
- **提交信息**: [Feat] rust-server: Tell a model package's abort hook which requests an abort names (#50190)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [2815ad0](https://github.com/sgl-project/sglang/commit/2815ad09079b09c5f5d9ef6acb95b947ff68db15)

- **作者**: metamergebot
- **时间**: 2026-11-13T22:37:59Z
- **提交信息**: [Feat] rust-server: Honor --warmups and --gc-warning-threshold-secs (#50189)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [b71901e](https://github.com/sgl-project/sglang/commit/b71901e7addaaa1ec9030bb5420a5f71393046d9)

- **作者**: metamergebot
- **时间**: 2026-11-13T22:37:31Z
- **提交信息**: [Feat] rust-server: Let a multimodal processor fail a request once its result is processed (#49907)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [fbe1896](https://github.com/sgl-project/sglang/commit/fbe18964eb009d832a8892e6d637a717d49324cf)

- **作者**: metamergebot
- **时间**: 2026-11-13T22:37:04Z
- **提交信息**: [Fix] rust-server: Name the type and retryability of streamed /generate errors (#49663)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [27c2438](https://github.com/sgl-project/sglang/commit/27c2438dae836eea0763e4a8facaff09afc863e0)

- **作者**: metamergebot
- **时间**: 2026-11-13T22:36:37Z
- **提交信息**: [Fix] rust-server: Answer and log request rejections as Python does, and refuse generate fields it would drop (#49653)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [b71152a](https://github.com/sgl-project/sglang/commit/b71152ae2ac2ce7f216a1cf868b0fb19523c8b82)

- **作者**: metamergebot
- **时间**: 2026-11-13T22:35:58Z
- **提交信息**: [Feat] rust-server: Serve media the MM processor already holds without a fetch slot, and fail fetches at its deadline (#49650)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [34fd2d4](https://github.com/sgl-project/sglang/commit/34fd2d48c94270a62ec01808576a6b19f5907b4c)

- **作者**: metamergebot
- **时间**: 2026-11-13T22:35:25Z
- **提交信息**: [Fix] rust-server: Answer a full tokenizer queue with 503 instead of blocking intake, take extension metrics off the mutex, release the GIL in shutdown (#49640)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [2932744](https://github.com/sgl-project/sglang/commit/29327444b130ee007fd06ff957b3fdc7066ceaa8)

- **作者**: metamergebot
- **时间**: 2026-11-13T21:11:46Z
- **提交信息**: [Perf] rust-server: Use the CPU's SHA-256 instructions on aarch64 Linux (#50204)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [5bfcc9f](https://github.com/sgl-project/sglang/commit/5bfcc9f1f2e84cff56ffda5cf6844091cba6064e)

- **作者**: metamergebot
- **时间**: 2026-11-13T21:11:32Z
- **提交信息**: [Fix] rust-server: Keep the /v1/loads snapshot lock wait off the async workers (#49635)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [0e509ea](https://github.com/sgl-project/sglang/commit/0e509eaf4c7d20aae67c76bf1838ff9d5975d51e)

- **作者**: metamergebot
- **时间**: 2026-11-13T21:11:18Z
- **提交信息**: [Perf] hicache: Stage kernel-backend host index uploads in pinned memory (#49633)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: Jialin <Jialin@users.noreply.github.com>

### [26f3f4e](https://github.com/sgl-project/sglang/commit/26f3f4e1c0ba8cd045b7f4e23c2bc1df15ca8a53)

- **作者**: metamergebot
- **时间**: 2026-11-13T21:11:08Z
- **提交信息**: [Perf] srt: Encode the load snapshot before taking the shared-memory file lock (#49631)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [6ddfd13](https://github.com/sgl-project/sglang/commit/6ddfd1380c8fe6b9e993736429c5c21c350fee8c)

- **作者**: Aurick Qiao
- **时间**: 2026-11-13T20:44:11Z
- **提交信息**: [Feat] disaggregation: Make the PD top-logprobs metadata width configurable (#49686)

Co-authored-by: Aurick Qiao <6137920+aurickq@users.noreply.github.com>
Co-authored-by: Ke Bao <ispobaoke@gmail.com>
Co-authored-by: Shangming Cai <csmthu@gmail.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [d38c87c](https://github.com/sgl-project/sglang/commit/d38c87c4fd801f4f466780100340b609f8a337cf)

- **作者**: metamergebot
- **时间**: 2026-11-13T20:30:13Z
- **提交信息**: [Fix] mem_cache: Keep freeing SWA slots for an unpublished prefill with a pending SWA branch (#49906)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: Adolfo-Karim <Adolfo-Karim@users.noreply.github.com>

### [cc3e9dc](https://github.com/sgl-project/sglang/commit/cc3e9dc03e2716a3801f1220a9f11cc9930293cb)

- **作者**: metamergebot
- **时间**: 2026-11-13T20:12:50Z
- **提交信息**: [Fix] hicache: Refuse a runtime write_back policy under buffer_only host memory (#50181)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: ZYHowell <ZYHowell@users.noreply.github.com>

### [a8d88db](https://github.com/sgl-project/sglang/commit/a8d88db3d107c9854efc4401f88d2386655ec76e)

- **作者**: metamergebot
- **时间**: 2026-11-13T20:12:35Z
- **提交信息**: [Test] crash-dump: Pin the Python frontend in the tests that resolve --ssl-keyfile-password (#49632)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [ad43866](https://github.com/sgl-project/sglang/commit/ad438669faa67af8d4c8676e58c30c236e7c0e5c)

- **作者**: sglang-bot
- **时间**: 2026-11-13T19:50:55Z
- **提交信息**: [Chore] release: Bump sgl-kernel version to 0.4.11 (#50369)

Co-authored-by: sglang-bot <sglang-bot@users.noreply.github.com>

### [69635d1](https://github.com/sgl-project/sglang/commit/69635d1d3fdd305c9f161a17f243b2539c671d8d)

- **作者**: Ziang Li
- **时间**: 2026-11-13T19:50:25Z
- **提交信息**: [Refactor] moe: simplify FlashInfer MegaMoE autotune handoff (#45905)

### [d133444](https://github.com/sgl-project/sglang/commit/d133444fec9bf339a329171f635823adbe727d7a)

- **作者**: Baizhou Zhang
- **时间**: 2026-11-13T19:46:18Z
- **提交信息**: [Chore] fa3: Serve FA3 from the sgl-fa3 wheel and remove it from sglang-kernel (#50260)

### [4a4f400](https://github.com/sgl-project/sglang/commit/4a4f400022105aca91bddd5d1d5af814ca59bbb1)

- **作者**: Ankith Averineni
- **时间**: 2026-11-13T19:36:36Z
- **提交信息**: [Fix] [AMD] docker: Pin UCX and NIXL commits for ROCm PD disaggregation (#49603)

### [084a5e9](https://github.com/sgl-project/sglang/commit/084a5e9aaede62d1fc4133e85a6361162c98133a)

- **作者**: Yu-Yun Chang
- **时间**: 2026-11-13T17:38:57Z
- **提交信息**: [Fix] [AMD] aiter: Plan the DCP asm verify shard with the draft tokens under CUDA graph replay (#47645)

Co-authored-by: kk <43161300+kkHuang-amd@users.noreply.github.com>

### [914405d](https://github.com/sgl-project/sglang/commit/914405d1071aa34bdb5350de19b2a6e96e2068a3)

- **作者**: Yu-Yun Chang
- **时间**: 2026-11-13T17:37:06Z
- **提交信息**: [Perf] [AMD] DCP: Slice gathered MHA prefixes with host offsets to drop GPU syncs (#43136)

### [410e64b](https://github.com/sgl-project/sglang/commit/410e64bb847a1ef80572926f07349fef092bb5cb)

- **作者**: DarkSharpness
- **时间**: 2026-11-13T15:51:53Z
- **提交信息**: [Refactor] custom-ar-v2: Share one symmetric workspace per group (#49382)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [530db9b](https://github.com/sgl-project/sglang/commit/530db9b470556f24a9e9615cdbc5f05cfa7e5b50)

- **作者**: Zhan Su
- **时间**: 2026-11-13T15:51:09Z
- **提交信息**: [Perf] attention: Optimize FA3/FA4 tree attention (#49477)

### [0758280](https://github.com/sgl-project/sglang/commit/0758280c8db71a5dd81fdab5ff05d9b7ab4909f9)

- **作者**: goldenfox2025
- **时间**: 2026-11-13T15:50:48Z
- **提交信息**: [Fix] disaggregation: Attribute decode HiCache hits to host and storage (#49878)

### [eaf392e](https://github.com/sgl-project/sglang/commit/eaf392e42549175b15fc027498bac77a17bd8a79)

- **作者**: Shuwen Wang
- **时间**: 2026-11-13T15:50:27Z
- **提交信息**: [Doc] hybrid: Document sizing the state and KV pools for multi-turn reuse (#50033)

### [b9283c0](https://github.com/sgl-project/sglang/commit/b9283c02f3efb052b9578230d0e3db87f2263498)

- **作者**: amote-i
- **时间**: 2026-11-13T15:38:59Z
- **提交信息**: [Doc] [NPU] docs: restructure the Ascend parameter tuning guide and align its dependents (#50231)

### [822e3e2](https://github.com/sgl-project/sglang/commit/822e3e2dd1bb236f5223d205aa4dcae91c8b3d40)

- **作者**: zilong
- **时间**: 2026-11-13T15:28:40Z
- **提交信息**: [Perf] models: use fused apply_qk_norm in Exaone, HunYuan-V3, AfMoE, and BailingMoE (#48629)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [0508e4c](https://github.com/sgl-project/sglang/commit/0508e4c6d35b44b89d8b669e8a08163d9b1edc18)

- **作者**: Ilyas Mallah
- **时间**: 2026-11-13T15:28:20Z
- **提交信息**: [Perf] cuda-graph: Raise the decode graph ceiling default to 128 for 35 to 60 GiB GPUs (#46132)

### [2e8a234](https://github.com/sgl-project/sglang/commit/2e8a2346cd16a0e7a45b4a231b6aa919a30d4358)

- **作者**: BingjiaWang
- **时间**: 2026-11-13T15:28:02Z
- **提交信息**: [Fix] deepseek-v4.1: Preserve compact DSpark outputs with CP bounded replay (#50039)

### [7eaa901](https://github.com/sgl-project/sglang/commit/7eaa90110f841f3392a132d07214bd5230a7fab8)

- **作者**: Han-Yin Chang
- **时间**: 2026-11-13T15:27:45Z
- **提交信息**: [Fix] diffusion: Align Wan2.2-TI2V-5B request sizes to its 32-pixel patch grid (#50098)

Signed-off-by: Han-Yin Chang <nick20350@gmail.com>

### [85111ff](https://github.com/sgl-project/sglang/commit/85111ff7636183da3c0742558cf86688f54bbe11)

- **作者**: Rabinovich
- **时间**: 2026-11-13T15:27:26Z
- **提交信息**: [Fix] diffusion: Enable Cosmos 3 Edge and Nano fused QK-norm/RoPE on SM 121 (GB10) (#47842)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Mick <mickjagger19@icloud.com>

### [dad2c79](https://github.com/sgl-project/sglang/commit/dad2c7911152c39a59b63e7a2a6b5b43fded6b04)

- **作者**: 渺如星辰
- **时间**: 2026-11-13T15:27:10Z
- **提交信息**: [Fix] compressed-tensors: Reject WNA16 MoE TP shards that split a scale group (#49338)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: hn1209 <44727020+hn1209@users.noreply.github.com>
Co-authored-by: scdotbox <128663994+scdotbox@users.noreply.github.com>

### [c65c1e5](https://github.com/sgl-project/sglang/commit/c65c1e5d293d1f9f9ef2fd412b5f6aa9e1b12192)

- **作者**: yang zhejun
- **时间**: 2026-11-13T15:26:55Z
- **提交信息**: [Fix] sgl-kernel: Do not compile FA3 instantiation files twice (#49866)

### [806417d](https://github.com/sgl-project/sglang/commit/806417dc7751fcb876a9d666af0e52fd72b75e46)

- **作者**: bthtsang
- **时间**: 2026-11-13T15:26:39Z
- **提交信息**: [Fix] kimi_k25: Run the vision projection under the caller's grad mode (#49964)

### [56b3255](https://github.com/sgl-project/sglang/commit/56b32550c718cc3d9ceea857815f04d2ad226a8b)

- **作者**: Rayan Hatout
- **时间**: 2026-11-13T15:26:23Z
- **提交信息**: [Fix] DeepSeek-V4: Default input_embeds to None in DS4 forward (#50178)

### [dac84ad](https://github.com/sgl-project/sglang/commit/dac84ad8cc170dc8831ff2927a5bcbe8c07a4061)

- **作者**: Rayan Hatout
- **时间**: 2026-11-13T15:26:07Z
- **提交信息**: [Fix] DeepSeek-V4: Skip decode attention TP setup when it is off (#50177)

### [0745bfe](https://github.com/sgl-project/sglang/commit/0745bfe49b855ae48e0c1ef3305362b8e0c78a03)

- **作者**: Yousaf
- **时间**: 2026-11-13T14:53:13Z
- **提交信息**: [Feat] function_call: Add granite_toolcall_parser for Granite 4.2 (#49600)

Add Granite 4.2 tool-call parser with mixed-union argument preservation and auto-detection.

### [1b2870d](https://github.com/sgl-project/sglang/commit/1b2870d33de7b5f31844fd74e97eea6d7896c53a)

- **作者**: Kangrui Du
- **时间**: 2026-11-13T13:45:38Z
- **提交信息**: [Refactor] multimodal: [MM refactor 2/9] Initialize multimodal processors from a processor config (#46408)

Signed-off-by: rockdu <kangrdu@gmail.com>
Co-authored-by: Teng Ma <sima.mt@alibaba-inc.com>

### [6d2d13a](https://github.com/sgl-project/sglang/commit/6d2d13a1c4577a2c549bda968e768eaa85e58116)

- **作者**: Po-Han Huang (NVIDIA)
- **时间**: 2026-11-13T12:20:16Z
- **提交信息**: [Doc] cookbook: Refresh SemiAnalysis AgentX launches to InferenceX main 8f29d8dc (#50289)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [5792cf6](https://github.com/sgl-project/sglang/commit/5792cf6e5e11aebc62d41cf19828f615a8fa7e0a)

- **作者**: Cheng Wan
- **时间**: 2026-11-13T09:12:30Z
- **提交信息**: [Feat] kimi_k3: Serve Kimi-K3.1 on the unified memory pool (#49913)

### [94d3dba](https://github.com/sgl-project/sglang/commit/94d3dbad27dcb10ca0e83ec5ccac3c87f6c1e0ca)

- **作者**: Cheng Wan
- **时间**: 2026-11-13T09:11:52Z
- **提交信息**: [Refactor] mem_cache: Compose same-lifetime parts into one unified sub-pool (#49966)

### [6c29aa5](https://github.com/sgl-project/sglang/commit/6c29aa5954a0dab3c2f8a23835fabda5d759947d)

- **作者**: Aki Yang
- **时间**: 2026-11-13T09:02:35Z
- **提交信息**: [Fix] [NPU] EPLB: preserve NZ storage, reuse TP, and isolate draft capture (#49701)

Co-authored-by: AkiYangDev <331522356+AkiYangDev@users.noreply.github.com>
Co-authored-by: Even Zhou <even.y.zhou@outlook.com>

### [9292957](https://github.com/sgl-project/sglang/commit/9292957782385d5b5ed9f4cdd77a5c5b93c0dd08)

- **作者**: Cheng Wan
- **时间**: 2026-11-13T08:46:24Z
- **提交信息**: [Feat] dsa: Honor the page stride of index-K buffers (#49912)

### [bddf8d0](https://github.com/sgl-project/sglang/commit/bddf8d0126587b7085990bb26f8710cb42691d52)

- **作者**: Cheng Wan
- **时间**: 2026-11-13T08:45:52Z
- **提交信息**: [Fix] mem_cache: Size a fused draft's KV region in the dtype the draft resolves (#49775)

### [e49ce98](https://github.com/sgl-project/sglang/commit/e49ce98eec3c905486d1cc2974934d72fce84c48)

- **作者**: Cheng Wan
- **时间**: 2026-11-13T08:45:04Z
- **提交信息**: [Refactor] mem_cache: Keep the KDA speculative ReplaySSM ring in the request sub-pool (#49720)

### [70a99e7](https://github.com/sgl-project/sglang/commit/70a99e769b417197f59a76f0e342f36f089ab7a1)

- **作者**: Cheng Wan
- **时间**: 2026-11-13T08:44:29Z
- **提交信息**: [Refactor] mem_cache: Keep the GDN speculative ReplaySSM ring in a request sub-pool of unified memory (#49719)

### [9db2337](https://github.com/sgl-project/sglang/commit/9db23378cafafe87bfba80ee642d846e1b9a3d3c)

- **作者**: amote-i
- **时间**: 2026-11-13T08:44:19Z
- **提交信息**: [Doc] [NPU] tutorials: Add deployment scripts for  dsv4-flash，glm5.2-w4a8，qwen3.6-27b (#50267)

### [cd52f02](https://github.com/sgl-project/sglang/commit/cd52f023e67ee2f52e002e9459eb9e1f4c559be4)

- **作者**: pllimax
- **时间**: 2026-11-13T08:42:57Z
- **提交信息**: [CI] [NPU] tests: Move DSV4-Flash W8A8 16-card cases to the full-test suites (#50252)

### [f0820d5](https://github.com/sgl-project/sglang/commit/f0820d5138c666f6ae67da799eb9fcf68ef6a42e)

- **作者**: Eric.Chin.AMD
- **时间**: 2026-11-13T08:27:24Z
- **提交信息**: [Fix] [AMD] topk-v2: Fix wrong picks on split-launch short rows (#48773)

Co-authored-by: jacky.cheng <yichiche@amd.com>

### [5d0de92](https://github.com/sgl-project/sglang/commit/5d0de926ad92eb6ec49e67941e278c93ea41772f)

- **作者**: Gabriel Wu
- **时间**: 2026-11-13T08:14:21Z
- **提交信息**: [Fix] quantization: Load block-FP8 MoE TP shards that split checkpoint blocks (#42566)

Signed-off-by: Zihua Wu <13583761+lucifer1004@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [ca64f2e](https://github.com/sgl-project/sglang/commit/ca64f2e78d37dd526ff0ec35ba2a86363ac4183b)

- **作者**: ZY Y
- **时间**: 2026-11-13T08:02:52Z
- **提交信息**: [Fix] [NPU] test: Set TRITON_CACHE_DIR to /tmp/triton_cache (#50258)

### [75ca91a](https://github.com/sgl-project/sglang/commit/75ca91a03cdc79f1928c36cc2c6afb49a68704c7)

- **作者**: qyb233
- **时间**: 2026-11-13T07:27:38Z
- **提交信息**: [Feat] [NPU] attention: Support FP8 KV for DSA prefill context parallelism (#50096)

### [2091b21](https://github.com/sgl-project/sglang/commit/2091b216cac3527c7466e26c395043290cd063f7)

- **作者**: Shuwen Wang
- **时间**: 2026-11-13T07:19:19Z
- **提交信息**: [Perf] kda: Reuse int64 prefill offsets across layers (#50102)

Co-authored-by: Khoa Pham <khoa.pham@radixark.ai>

### [8550edb](https://github.com/sgl-project/sglang/commit/8550edb467ec58e5013f46bc3db12b1cd1150f50)

- **作者**: Po-Han Huang (NVIDIA)
- **时间**: 2026-11-13T06:57:00Z
- **提交信息**: [Fix] comfyui: Refresh the reviewed MiniMax-H3 source hash after #49826 (#50219)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [6f90555](https://github.com/sgl-project/sglang/commit/6f90555ef542278cbd19095e2c47244bb13a806b)

- **作者**: Lee Nau
- **时间**: 2026-11-13T06:55:14Z
- **提交信息**: [Perf] [NVIDIA] kimi-k3: Bound q6 preparation by server concurrency (#49376)

Co-authored-by: Po-Han Huang (NVIDIA) <53919306+nvpohanh@users.noreply.github.com>

### [be9f2af](https://github.com/sgl-project/sglang/commit/be9f2aff7f299a397bc3a3b4c500c464b69966de)

- **作者**: Manuel Stehle
- **时间**: 2026-11-13T06:54:48Z
- **提交信息**: [Fix] moe/router: Reject CPU-offloaded bias in warp router (#49380)

Signed-off-by: Manuel Stehle <338640100+mercant1982@users.noreply.github.com>
Co-authored-by: Po-Han Huang <pohanh@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [89fe873](https://github.com/sgl-project/sglang/commit/89fe8734cee429281b1ab62d0cd68ebda9a5ddb4)

- **作者**: Lee Nau
- **时间**: 2026-11-13T06:50:19Z
- **提交信息**: [CI] disaggregation: Move Mooncake's handshake port range off the PD test ports (#49951)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Po-Han Huang <pohanh@nvidia.com>

### [a14fd4e](https://github.com/sgl-project/sglang/commit/a14fd4e5b4f90e62aea525e3ead94b8a818e8941)

- **作者**: Shuwen Wang
- **时间**: 2026-11-13T06:37:53Z
- **提交信息**: [Feat] mem_cache: Checkpoint hybrid Mamba state only at fork points and request ends (#49886)

### [4929ba4](https://github.com/sgl-project/sglang/commit/4929ba40246567b004bfe89d33e4709db826cef2)

- **作者**: Ziang Li
- **时间**: 2026-11-13T06:28:50Z
- **提交信息**: [Perf] flashinfer_cutedsl: Use swap-AB MoE on Blackwell (#48350)

### [cb1813a](https://github.com/sgl-project/sglang/commit/cb1813a5ee8c97759b2c68e37d8be78d2d876fee)

- **作者**: chenxu214
- **时间**: 2026-11-13T06:26:32Z
- **提交信息**: [Fix] [NPU] moe: Add ascend_ops backend checks across MoE models (#50004)

### [c2578f2](https://github.com/sgl-project/sglang/commit/c2578f28cfaece96167765ed93cab9a484f6fe95)

- **作者**: dqh1900013087-tech
- **时间**: 2026-11-13T06:11:27Z
- **提交信息**: [Feat] [NPU] HiCache: Support Mooncake L3 for DeepSeek-V4 and GLM-5.2 (#49054)

Co-authored-by: gjsheu <gjsheu@163.com>
Co-authored-by: root <root@localhost.localdomain>
Co-authored-by: d00934833 <duanqinghong@huawei.com>

### [112ecb1](https://github.com/sgl-project/sglang/commit/112ecb1303efe813723afa79606b116fa32dc79f)

- **作者**: em-dreyer
- **时间**: 2026-11-13T05:37:36Z
- **提交信息**: [Test] disaggregation: Give the fake draft pool follows_target_swa_ids (#49699)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [2c75d49](https://github.com/sgl-project/sglang/commit/2c75d49024a19c67bf960cbc7c8cdec98a7d02f2)

- **作者**: Chunan Zeng
- **时间**: 2026-11-13T05:26:03Z
- **提交信息**: [Chore] deps: Bump sgl-deep-gemm to 0.2.8 and sgl-flash-mla to 1.0.5 (#50016)

Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>
Co-authored-by: Po-Han Huang (NVIDIA) <53919306+nvpohanh@users.noreply.github.com>

### [00752f2](https://github.com/sgl-project/sglang/commit/00752f2600b11b78e22aa3153507e0f772c2f27a)

- **作者**: Erik Wijmans
- **时间**: 2026-11-13T04:53:08Z
- **提交信息**: [Fix] scheduler: Park a chunked prefill continuation when its chunk or KV budget is spent (#44823)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Ke Bao <ispobaoke@gmail.com>
Co-authored-by: hnyls2002 <lsyincs@gmail.com>
Co-authored-by: Yihao Wang <42559837+AgainstEntropy@users.noreply.github.com>
Co-authored-by: Zhiqiang Xie <zqx@meta.com>

### [4f8b686](https://github.com/sgl-project/sglang/commit/4f8b6867534c8a6632845353997555fca857dd63)

- **作者**: MatsueYu
- **时间**: 2026-11-13T02:52:54Z
- **提交信息**: [Fix] [NPU] kimi-k3: Skip the CuTe DSL TGV tactic registration on NPU (#50107)

### [d1051b4](https://github.com/sgl-project/sglang/commit/d1051b47bf77bf4530e352cc2543b9a9dedb86a2)

- **作者**: WenhaoZhang
- **时间**: 2026-11-13T01:04:40Z
- **提交信息**: [Feat] comfyui: Add an offline workflow converter and reject weight patches on SGLD models (#48998)

### [4c5fb55](https://github.com/sgl-project/sglang/commit/4c5fb55cb061487b172a30f3619da02999cc5e7d)

- **作者**: Han-Yin Chang
- **时间**: 2026-11-13T01:04:24Z
- **提交信息**: [Fix] diffusion: Align Cosmos3 request sizes to the 16-pixel latent grid (#50114)

Signed-off-by: Han-Yin Chang <nick20350@gmail.com>

### [0ad3488](https://github.com/sgl-project/sglang/commit/0ad34887ef096146c8909d32bae8f82afbc727f7)

- **作者**: Han-Yin Chang
- **时间**: 2026-11-13T01:04:10Z
- **提交信息**: [Fix] diffusion: Keep fused QKNorm+RoPE rounding exact on SM100 (#50101)

Signed-off-by: Han-Yin Chang <nick20350@gmail.com>

### [f9b90d3](https://github.com/sgl-project/sglang/commit/f9b90d33e2c680d41a5b6b9112f930280a4a456b)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-11-13T00:19:36Z
- **提交信息**: [Refactor] cleanup: Prune dead code and env vars, fix silent failures found by the code-cleanup skill (#49189)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [8ab11f2](https://github.com/sgl-project/sglang/commit/8ab11f2bdbe9e1a5db964fba9d45b5f7175763c3)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-11-13T00:19:02Z
- **提交信息**: [Perf] [NVIDIA] diffusion/joy: Enable packed-image QK normalization and RoPE on SM103 (#49417)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-11-14
**监控日期**: 2026-11-13
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for 100+ DiTs.
- **语言**: Python
- **星标数**: 1306
- **最后更新**: 2026-11-13T13:10:33Z

## 提交统计

- **昨日提交总数**: 14
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

## 昨日提交分析（vipshop/cache-dit）

### 1. 主要更新类型
- **性能优化**：FP4 原生 GEMM 与量化、FP8 per-row 内核与编译路径、FlashInfer 链路的 SVDQ 全局 scale 开销削减。
- **功能新增**：原生 NVFP4 后端、默认启用 `torch._scaled_mm`、新增三个开发者 Agent Skill 与多份使用文档。
- **Bug 修复**：`BlockAdapterRegister` 适配器注册范围限定问题。
- **重构/构建清理**：移除冗余的 setuptools_scm 配置表。

### 2. 关键变更点与项目方向的关系
项目定位是"带缓存、并行、量化与 CPU offload 的 DiT 推理引擎"，这些提交精准对应其核心卖点：**量化（FP4/FP8）与缓存正确性**两条主线。
- 提交 #1325/#1314 将 FP4/FP8 GEMM 默认切到 `torch._scaled_mm`，保留原生内核作为备选（`use_native`），在保持 SM120 CuTe 自研能力的同时拥抱 PyTorch 原生算子，符合 README 中"PyTorch-native 推理引擎"的定位。
- 提交 #1320 是缓存方向的关键修复：下游 fork（sglang-diffusion、vllm-omni 等）复用类名前缀时被错误路由到 cache-dit 自有流水线的适配器，导致断言失败或**静默缓存错误架构**。通过 `owned=True` 与 MRO 走查划定边界，保障缓存语义正确。
- Skill 与文档类提交（#1322/#1317）构建围绕项目的开发生态，尤其是下游兼容审计 Skill，说明项目已被多个推理框架深度集成。

### 3. 对项目的影响和潜在意义
- **性能层面**：SVDQ 全局 scale 从 127us 降至 48us/层；FLUX 端到端实测 `--cache` 16.99s→9.94s（37.39dB），量化与缓存协同收益显著。
- **稳定性层面**：#1320 修复了"静默算错"这一最危险的故障模式，14 个注册项标记 owned，配套 9 例边界测试与 252 例回归全绿，极大降低了多下游集成的踩坑风险。
- **生态层面**：文档补齐（内置流水线用法、Agent Skill 说明）降低了外部用户启用 `enable_cache` 的门槛，配合 PyPI 下载量增长形成正向循环。
- **兼容性层面**：#1322 的审计 Skill 将六步审计流程和八类风险分类沉淀为可复用资产，使下游升级 cache-dit 时的问题发现从偶然变为系统化。

### 4. 值得关注的技术点
- **前缀分派的陷阱**：按类名前缀分派适配器是灵活设计，但在 fork 场景下会误命中；修复方案中"在 owned 前缀不匹配处停止查找，而非 fall through 到更短前缀"（外来 `WanS2V*` 不得退化为 `Wan`）是精细且正确的语义。
- **双轨内核策略**：自研 CuTe 内核与 `torch._scaled_mm` 并存，通过配置切换，兼顾可控性与生态跟随。
- **数学上安全的上界替换**：`max|x| * max|smooth|` 替代精确 amax，单次融合归约即可完成，且保证 FP8 块 scale 只会更小（更安全）。
- **构建系统认知**：setuptools_scm 表从未生效的分析展示了对版本推导链路（version_keyword 先于 finalize hook）的深入理解。

### 5. 基于 README 背景对项目发展的评估
cache-dit 正从"功能可用"走向"生产可依赖"阶段：性能上持续榨取量化与缓存收益，正确性上通过 owned 边界与兼容审计堵住跨框架集成的静默错误，生态上以文档和 Skill 降低采用成本。这三条线共同支撑 README 宣称的 PyTorch-native 高效推理目标，为项目在 DiT 推理基础设施中的竞争位次奠定了扎实基础。后续值得关注的是 FP4 NVFP4 后端在更多下游框架的落地验证，以及 owned 边界机制是否需要覆盖更多分派入口。

## 详细提交记录

### [2a1eadf](https://github.com/vipshop/cache-dit/commit/2a1eadfe6a4d929cb67ba15d0be0a2724976f258)

- **作者**: DefTruth
- **时间**: 2026-11-13T16:43:45Z
- **提交信息**: perf(fp4): optimize native GEMM and quantize (#1325)

### [16086e3](https://github.com/vipshop/cache-dit/commit/16086e3ccf77a306a180c03d30cff93113c6edfc)

- **作者**: DefTruth
- **时间**: 2026-11-13T12:12:54Z
- **提交信息**: feat(fp4): add native NVFP4 backend with scaled_mm default

- add FP4 quantize and SM120 CuTe GEMM family plus native NVFP4 Linear
- default FP4 GEMM to torch._scaled_mm and keep native via use_native
- default FP8 per-row/per-tensor GEMM to torch._scaled_mm, keep per-block native
- add tests, benchmarks, docs and operator references

### [69b2ecc](https://github.com/vipshop/cache-dit/commit/69b2eccb7570bba75ee38f8ea42b386bdd48c195)

- **作者**: DefTruth
- **时间**: 2026-11-13T08:46:04Z
- **提交信息**: docs(skill): add a downstream cache-dit compatibility audit skill (#1322)

Adds `.agents/skills/cache-dit-downstream-compat/`, the workflow used to audit
vllm-omni / sglang-diffusion / xDiT / TensorRT-LLM visual_gen against the
current cache-dit tree.

The skill encodes the six steps that actually found issues, not just the happy
path: pin resolution (exact vs range vs open-ended), an AST scan of every
`cache_dit` reference, symbol resolution on the target revision, a registry
dispatch/gate diff (`BlockAdapterRegister` prefixes and `owned=` flags), a
behavior probe on a synthetic DiT (refresh merge semantics, persistent-context
requirement, short-schedule `steps_mask`, `summary` shape, `disable_cache`,
`auto=True` pattern requirement), and the downstream's own test command with the
environment quirks that make it runnable (e.g. `CUDA_VISIBLE_DEVICES=""` for
xDiT, where `fp8_comms` hard-imports `yunchang`).

`references/risk-taxonomy.md` groups the failures into eight classes (renamed
symbols, signature semantics, registry gate, fork drift, counter semantics,
short-schedule mask, persistent context, stats shape) with a real instance of
each. `references/findings.md` records the 2026-11-13 snapshot: pins, verdicts
per downstream, the TensorRT-LLM specifics (unbounded `>=1.3.5` pin, default
`max_continuous_cached_steps=3` meeting #1114), and what #1320 changed.

No production code is touched; the scripts are stdlib + torch only.

### [8dbb58b](https://github.com/vipshop/cache-dit/commit/8dbb58b025fdc4c1899ea81b4a06c623817cdd48)

- **作者**: DefTruth
- **时间**: 2026-11-13T08:21:24Z
- **提交信息**: fix(registry): scope owned adapters to cache-dit's own pipelines (#1320)

`BlockAdapterRegister` dispatches on class-name prefixes, so a downstream
fork reusing a family name (sglang's `LongLive2Transformer3DModel`,
vllm-omni's `LongCatVideoAvatarTransformer3DModel`, ...) was routed into an
adapter written for cache-dit's own vendored pipeline. Those adapters rely on
implementation details the fork does not have - a layer-KV contract
(`force_full_compute` raw-block replay), a marker only the vendored
transformer sets, or a class identity assertion - so the dispatch either
raised a bare AssertionError or silently cached the wrong architecture.

Register those adapters with `owned=True` and skip them for objects that are
not cache-dit's own implementation:

* `_is_cache_dit_owned` walks the MRO, so users and tests that subclass a
  shipped pipeline keep dispatching;
* the lookup stops at an owned-prefix mismatch instead of falling through to
  a shorter family prefix (a foreign `WanS2V*` must not become a plain
  `Wan` model);
* `is_supported` follows the same rule, and the `_predefined_adapters_has_
  separate_cfg` prefix table no longer answers for a class refused above;
* the skip is logged once per class name with the explicit `BlockAdapter`
  workaround.

Fourteen registrations are marked owned (WanS2V/WanSpeechToVideo, CausVid,
LongLive2, LongCatVideoAvatar, Magi2Preview, MOVA, BooguImage, LingBotVideo,
Nomas, HiDreamO1Image, MOSSImage, SanaVideo2, MingImage). `_Flux2Klein` keeps
its diffusers family contract but now uses `_relaxed_assert`, and
`_relaxed_assert` returns early when the expected class matches so cache-dit's
own fused subclasses stop logging a spurious "skipping strict type check".

Tests: `tests/api/test_block_adapter_register_owned.py` (9 cases) locks the
boundary; the existing adapter suites stay green (252 passed, 2 skipped).
FLUX cache e2e on one PRO 5000: baseline 16.99s, `--cache` 9.94s
(37.39dB/0.9690), `--cache --taylorseer` 9.96s (38.22dB/0.9801),
`--cache --compile` 8.75s (36.89dB/0.9592), all 1024x1024/28 steps.

### [d8e592e](https://github.com/vipshop/cache-dit/commit/d8e592e6435b0a162e777fa17b0769cb2c41f850)

- **作者**: DefTruth
- **时间**: 2026-11-13T06:25:09Z
- **提交信息**: Merge pull request #1317 from vipshop/dev

build: drop the redundant [tool.setuptools_scm] table

### [73f185d](https://github.com/vipshop/cache-dit/commit/73f185d0d2661c3a556f759d8dfb2e1bbb61136a)

- **作者**: DefTruth
- **时间**: 2026-11-13T06:15:45Z
- **提交信息**: build: drop the redundant [tool.setuptools_scm] table

setuptools runs the use_scm_version setup keyword before the setuptools_scm finalize hook, so setup.py's USE_SCM_VERSION was already the single source of the version: version_keyword sets dist.metadata.version, and the later infer_version hook only reported VersionAlreadySetWarning ("version of None already set", because dist.metadata.name is still unset that early).

The table's own version_scheme/local_scheme never took effect, so dropping it changes no version: clean tree -> 1.5.4.devN, dirty tree -> 1.5.4.devN+dirty, and SETUPTOOLS_SCM_PRETEND_VERSION still wins.

### [c411f78](https://github.com/vipshop/cache-dit/commit/c411f7886db370539bec80b7353a834f09ddf484)

- **作者**: DefTruth
- **时间**: 2026-11-13T05:04:22Z
- **提交信息**: Merge pull request #1316 from vipshop/opt/fp8-per-row-compile

Optimize FP8 per-row kernels and compile path

### [11b8366](https://github.com/vipshop/cache-dit/commit/11b8366d4fce96576b6e8d490f3198f050a9d9e3)

- **作者**: DefTruth
- **时间**: 2026-11-13T05:00:13Z
- **提交信息**: Finalize FP8 safe scale and kernel docs

### [518182c](https://github.com/vipshop/cache-dit/commit/518182c46c5b999bc03f0adeba1f5805f236a7b2)

- **作者**: DefTruth
- **时间**: 2026-11-13T03:19:50Z
- **提交信息**: Optimize FP8 per-row kernels and compile path

### [c6400a8](https://github.com/vipshop/cache-dit/commit/c6400a8cf280c3e4d6ac3719417d495180926c99)

- **作者**: DefTruth
- **时间**: 2026-11-13T03:24:29Z
- **提交信息**: Merge pull request #1314 from vipshop/dev

docs: document the agent skills for developers

### [4870ab9](https://github.com/vipshop/cache-dit/commit/4870ab95b1088c2fd08047a2fa898f9659bcd8e4)

- **作者**: DefTruth
- **时间**: 2026-11-13T03:22:56Z
- **提交信息**: docs: document the agent skills for developers

The repo ships three developer-facing SKILLs under `.agents/skills`
(model integration, quantization, custom kernel) but only the
model-integration one was mentioned in the README, and nothing
explained how to install them or what each one is for.

Add `developer_guide/AGENTS.md`: what the skills are, the
`gh skill install` command, typical prompts, how a skill is
structured (router + references), and the rule that a workflow
change has to update the matching skill in the same PR.

Register the page in the mkdocs nav under Developer Guide.

### [bb17bdf](https://github.com/vipshop/cache-dit/commit/bb17bdfb0a5dd114ec883784c13100a515d4d660)

- **作者**: DefTruth
- **时间**: 2026-11-13T03:12:09Z
- **提交信息**: Merge pull request #1312 from vipshop/dev

docs: add a usage guide for the built-in pipelines

### [97e81c3](https://github.com/vipshop/cache-dit/commit/97e81c38f3c0e4932781075bba3f7b19d1a91a05)

- **作者**: DefTruth
- **时间**: 2026-11-13T03:10:49Z
- **提交信息**: docs: add a usage guide for the built-in pipelines

The vendored pipelines under `cache_dit.models.pipelines` have to be
imported from cache-dit, but nothing in `docs/` said so. Add
`user_guide/PIPELINES.md` covering the import paths, the one-line
`enable_cache` recipe (cache / parallelism / quantization, as in the
main Quick Start), and the constraints that break a run (checkpoint
layout, return types, CFG bookkeeping, extra assembly steps).

Register the page in the mkdocs nav and in the overviews table of
contents.

### [7c19821](https://github.com/vipshop/cache-dit/commit/7c19821f7ff2725aac978a0240d70c57462097ea)

- **作者**: DefTruth
- **时间**: 2026-11-13T02:27:10Z
- **提交信息**: feat(svdq): select the FlashInfer chain via runtime_kernel and cut its global-scale cost (#1310)

Name the FlashInfer chain in the runtime string (flashinfer+cute-dsl,
flashinfer+cutlass-sm120) so both routes are reachable from the CLI; a bare
'flashinfer' now maps to the fused-prefix cutlass-sm120 route, and ranks it
cannot cover are rejected instead of silently downgraded.

Replace the exact amax(x * smooth) activation global scale with the safe upper
bound max|x| * max|smooth|: one fused reduction instead of a full smoothing
pass, 127us -> 48us per layer, and the FP8 block scales can only shrink.

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-11-14
**监控日期**: 2026-11-13
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 96881
- **最后更新**: 2026-11-14T02:24:01Z

## 提交统计

- **昨日提交总数**: 102
- **提交者数量**: 72
- **主要提交者**: Fadi Arafeh, Canlin Guo, Nick Hill

## AI分析总结

# vLLM 昨日提交综合分析（共 102 个提交）

## 1. 主要更新类型

- **Bug 修复占比最高**（约三至四成），集中于 KV 缓存、投机解码、引擎启动、多模态、量化与模型加载等核心路径。
- **性能优化**集中在硬件内核层面：ROCm/AMD、XPU/Intel、CPU 与 CUDA 内核融合，以及投机解码内核与注意力后端。
- **功能新增**包括：Mistral Large 4 支持、崩溃恢复后继续处理未完成请求、Rust 前端 gRPC 服务及 stop strings、logprobs、工具调用流式传输等能力补全、任意流水线并行阶段划分。
- **CI/测试与依赖**：大量 flaky 测试修复、平台适配、依赖版本升级（vllm-flash-attn、DeepGEMM）与废弃 API 清理。

## 2. 关键变更点及与项目方向的关系

- **KV 缓存架构重构**（RFC #42449 第二步）：将分配策略从 KVCacheSpecs 中解耦，是内存管理走向策略化、可插拔的里程碑。
- **KV 缓存可靠性**：修复混合模型 draft 层页分配、启动 OOM 时释放预热内存、分配器碎片余量、多模态哈希域隔离，直接服务"低成本、稳定服务"目标。
- **投机解码持续深化**：EAGLE 注意力块大小对齐、min_p/logit_bias 支持、token 计数一致性、零气泡草稿 token 交接、动态投机解码与 DP 兼容。
- **前沿模型快速适配**：DeepSeek V4/V4.1、GLM-5.3、Mistral Large 4、Kimi 等，含 EPLB 异构专家、DeepStack 视觉特征、HiSparse 启动修复。
- **多硬件并进**：ROCm（MI355X/gfx1151）、Intel XPU、Arm CPU、CUDA sm100 覆盖，延续跨平台定位。
- **Rust 前端**：错误传播、请求故障处理与流式工具调用，生产就绪度持续提升。

## 3. 对项目的影响与潜在意义

- 内存与启动路径修复（SIGTERM 中断、EngineCore 启动失败清理、CUDA graph 越界回退 eager、encoder 图安全降级）显著降低 OOM 与崩溃风险，提升长上下文及多模态负载下的生产稳定性。
- 量化增强（fp8 在线 per-channel 量化 lm_head、int4 张量描述符内核、`VLLM_STRICT_QUANT_SCHEME` 开关）扩展部署灵活性与精度可排查性。
- 服务韧性功能（恢复后继续未完成请求）对高可用部署有直接价值。
- CI 健康度改善加快合并速度、降低贡献门槛；依赖升级提升开发效率。

## 4. 值得关注的技术点

- **KV 缓存分配策略外置**：内存管理从硬编码迈向可插拔演进。
- **零气泡草稿 token 交接**：兼顾采样约束与投机解码延迟。
- **内核级融合**：GLM-5.3-Flash 的 RMSNorm+RoPE 融合、ROCm MXFP8 大 GEMM tile、AITER MLA 单内核解码元数据、主机端构建 ViT 注意力 metadata、Monokernel 单轮 launch 采样——极致压低内核启动与同步开销。
- **PP 中间张量精确匹配**：增强多级流水线传输的正确性校验。
- **AI 辅助开发普遍化**：大量提交含 Claude/Codex/vllm-agent 等 Co-authored-by 签名，反映开源协作模式转变。

## 5. 对项目发展的整体影响

这批提交整体呈现"**深耕稳定性、巩固多硬件生态、推进架构现代化**"的特征：vLLM 正从功能扩张期转向性能与稳定性精耕期。短期看，用户获得更可靠的故障恢复、更广的平台与模型覆盖；长期看，KV 缓存架构解耦、Rust 前端成熟与内核融合为 vLLM 适应异构算力和多样化内存层级的 serving 需求铺平道路。这些工作共同强化了 README 所述"轻松、快速、廉价的 LLM 服务"愿景，推动项目从快速迭代期稳步迈向企业级推理基础设施的成熟期。

## 详细提交记录

### [d64414d](https://github.com/vllm-project/vllm/commit/d64414d044a898c6db646dcecd122213accd1732)

- **作者**: Ilya Markov
- **时间**: 2026-11-13T23:57:09Z
- **提交信息**: [EPLB] Support heterogeneous DeepSeek V4/V4.1 DSpark draft experts (#61395)

Signed-off-by: Markov Ilya <markovilya197@gmail.com>
Signed-off-by: ilmarkov <markovilya197@gmail.com>

### [e9281bd](https://github.com/vllm-project/vllm/commit/e9281bd939d4ade90d6aacf4b2319aa89ea46c39)

- **作者**: Seyfal Sultanov
- **时间**: 2026-11-13T23:33:35Z
- **提交信息**: [Bugfix] Fix KV cache pages for hybrid models with draft layers (#62800)

Signed-off-by: Seyfal Sultanov <seyfal.s@outlook.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [6606381](https://github.com/vllm-project/vllm/commit/6606381134436f6e726447686d4fe9e0cc7ef2d3)

- **作者**: PerryZhang01
- **时间**: 2026-11-13T23:26:52Z
- **提交信息**: [ROCm][CI] Fix Sharded RDT bake test replay under persisted ROCm MoE padding (#67394)

Signed-off-by: PerryZhang01 <Perry.Zhang@amd.com>
Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [673a155](https://github.com/vllm-project/vllm/commit/673a155d76bb7c7962b1f9090273122381ea6fe5)

- **作者**: Aarushi Jain
- **时间**: 2026-11-13T23:24:55Z
- **提交信息**: [CI] Make DSpark sharded-sampling test deterministic under torch.compile (#65733)

Signed-off-by: Aarushi Jain <aarushi.jain2@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [7f855f6](https://github.com/vllm-project/vllm/commit/7f855f605892656ebf7265642e5d22a34a6ae731)

- **作者**: azaidy
- **时间**: 2026-11-13T22:53:52Z
- **提交信息**: [ROCm][Muse Spark] DSpark Markov sampling with one launch a round (--monokernel) (#66051)

Signed-off-by: Aliasger Zaidy <aliasger.zaidy@amd.com>
Signed-off-by: Matt <156021403+mawong-amd@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Matt <156021403+mawong-amd@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Fangzhou Ai <31551580+Fangzhou-Ai@users.noreply.github.com>

### [1ea7a90](https://github.com/vllm-project/vllm/commit/1ea7a90dbed31a3397482f2cbf076c740e2a02f8)

- **作者**: Ankur Singh
- **时间**: 2026-11-13T22:45:18Z
- **提交信息**: [Bugfix][Spec Decode] Use the target's kernel block sizes for EAGLE draft attention (#64777)

Signed-off-by: Ankur-singh <ankusingh@nvidia.com>
Signed-off-by: wzhao18 <wzhao18.sz@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: wzhao18 <wzhao18.sz@gmail.com>

### [3d091b6](https://github.com/vllm-project/vllm/commit/3d091b6f05f5ab3e688ce4bbe0c453de0646a069)

- **作者**: Kevin H. Luu
- **时间**: 2026-11-13T21:38:31Z
- **提交信息**: [CI] Split ReplaySSM E2E into 1-GPU, TP2 and nightly H100 steps (#67553)

Signed-off-by: Kevin Luu <51931015+khluu@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [1394f82](https://github.com/vllm-project/vllm/commit/1394f8234c39de3cf926727cef3dd5cbb41069d3)

- **作者**: Harry Mellor
- **时间**: 2026-11-13T21:17:15Z
- **提交信息**: [Transformers backend] Support DeepStack vision features (#67312)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [b73d376](https://github.com/vllm-project/vllm/commit/b73d37629f66290cf0c40f68b3b4db2ce248d31c)

- **作者**: Vadim Gimpelson
- **时间**: 2026-11-13T21:10:21Z
- **提交信息**: [Bugfix] Fix startup OOM in KV cache sizing warmup by releasing kernel warmup's KV blocks (#67485)

Signed-off-by: Vadim Gimpelson <vadim.gimpelson@gmail.com>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Nick Hill <nickhill123@gmail.com>

### [2cfbe17](https://github.com/vllm-project/vllm/commit/2cfbe17c928b45d9f70eb5e385c7f57533e466a4)

- **作者**: Nick Hill
- **时间**: 2026-11-13T21:02:05Z
- **提交信息**: [Bugfix] Keep extensible KV cache headroom for measured allocator fragmentation (#67296)

Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Mirza Halilčević <mhalilce@amd.com>

### [7833dce](https://github.com/vllm-project/vllm/commit/7833dce84784045721e177716d5fa16079d76ff8)

- **作者**: Madhav Jivrajani
- **时间**: 2026-11-13T20:36:08Z
- **提交信息**: [CI/Build] Fix docstring Markdown style in test_quark.py (#67549)

Signed-off-by: Madhav Jivrajani <madhav.jiv@gmail.com>

### [fa9ed29](https://github.com/vllm-project/vllm/commit/fa9ed29e6da9223f900bcd7f9e78f30705b1210f)

- **作者**: Jhao-Ting Chen
- **时间**: 2026-11-13T20:33:32Z
- **提交信息**: [Build] Bump vllm-flash-attn to 8dd9eaea (flash-attention#218, #208) (#67280)

Signed-off-by: Jhao-Ting Chen <jhaotingc@nvidia.com>
Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [fc870cd](https://github.com/vllm-project/vllm/commit/fc870cd1522b684681f6b5c9cf714c6f31709c3e)

- **作者**: Harry Mellor
- **时间**: 2026-11-13T20:22:42Z
- **提交信息**: [Chore] Remove deprecated `rope_scaling` usage and forbid it in pre-commit (#67533)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [1e88e38](https://github.com/vllm-project/vllm/commit/1e88e384a2a67c03c7bfb66f37b732bfa1181589)

- **作者**: Nick Hill
- **时间**: 2026-11-13T20:15:45Z
- **提交信息**: [PP] Require exact intermediate-tensor match on every PP transport (#67093)

Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [896a423](https://github.com/vllm-project/vllm/commit/896a4232405d8d2a7b759c5d4012501fe2b0350c)

- **作者**: Yicong Wang
- **时间**: 2026-11-13T20:15:29Z
- **提交信息**: [Feature][DSv4.1] Support arbitrary pipeline stage partitions (#63106)

Signed-off-by: wangyicong <wangyicong@bytedance.com>
Signed-off-by: Yifei Wang <yifei.w@inferact.ai>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: saipakalapati <79748893+saichowdary007@users.noreply.github.com>
Co-authored-by: Yifei Wang <yifei.w@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [5e0c226](https://github.com/vllm-project/vllm/commit/5e0c2269d4bc2898df542e954e818c4491f3c9c6)

- **作者**: Misha Goin
- **时间**: 2026-11-13T20:09:51Z
- **提交信息**: Delete tools/flashinfer-build.sh (#67304)

Signed-off-by: Misha Goin <mgoin64@gmail.com>

### [7a10561](https://github.com/vllm-project/vllm/commit/7a105612774d40d90fd1fdcae9e6b5a59b1c71e5)

- **作者**: Ziyang Ma
- **时间**: 2026-11-13T20:08:38Z
- **提交信息**: [XPU][Perf][Spec Decode] Enable triton greedy_argmax on XPU (#67196)

Signed-off-by: RyanMa29 <ziyang.ma@intel.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [ca09eef](https://github.com/vllm-project/vllm/commit/ca09eef6f353d28116e2d94b28f766fc58024691)

- **作者**: Chenxi Ma
- **时间**: 2026-11-13T20:08:05Z
- **提交信息**: [Bugfix][MoE] Preserve invalid expert IDs in NIXL round-robin mapping (#64086)

Signed-off-by: Chenxi Ma <114001934+algebra-MCX@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Lucas Wilkinson <LucasWilkinson@users.noreply.github.com>

### [dfbda4b](https://github.com/vllm-project/vllm/commit/dfbda4bfc667d74e831075b6dbaf3caa5d659482)

- **作者**: Sudhir Vissa
- **时间**: 2026-11-13T20:06:29Z
- **提交信息**: [Bugfix][Multimodal] Domain-separate content digests and caller uuids in mm hashes (#66473)

Signed-off-by: shadowmodder <sudhirvissa@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [f6bd727](https://github.com/vllm-project/vllm/commit/f6bd727a4c54bbe8a3bc7a34ee1d646eaa723406)

- **作者**: Cenab Batu Bora
- **时间**: 2026-11-13T20:05:13Z
- **提交信息**: [Bugfix] Allow query parameters in benchmark endpoint URLs (#55719)

Signed-off-by: Cenab Batu Bora <40250311+cenab@users.noreply.github.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [06a35d2](https://github.com/vllm-project/vllm/commit/06a35d208376d14ba5125b48548a0c66b2d43668)

- **作者**: afriedri
- **时间**: 2026-11-13T20:04:09Z
- **提交信息**: [Bugfix][Quantization] Handle dict-valued Quark `algo_config` in `maybe_update_config` (#65951)

Signed-off-by: Andy Friedrich <afriedri@amd.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [a9de7ea](https://github.com/vllm-project/vllm/commit/a9de7ea9630625565436e5bc8c09ac533da1fa36)

- **作者**: Harsh
- **时间**: 2026-11-13T20:03:46Z
- **提交信息**: [Bugfix] Reject prompt embeddings for BERT/RoBERTa models (#55233)

Signed-off-by: iharshlalakiya <harshlalakiya.me@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [2a009e1](https://github.com/vllm-project/vllm/commit/2a009e17ece34e0857164e7a5b4cbe365034c3f3)

- **作者**: 0z5a
- **时间**: 2026-11-13T20:01:43Z
- **提交信息**: [Bugfix][V2 runner] Keep idle-DP dummy requests within max_model_len (#64923)

Signed-off-by: aoshen02 <aoshen@inferact.ai>
Signed-off-by: 0z5a <0z5a@users.noreply.github.com>
Signed-off-by: 0z5a <dezhen.lu@student.uni-tuebingen.de>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [b543fff](https://github.com/vllm-project/vllm/commit/b543fffe69c1996abe5ba58d762e67573ae27957)

- **作者**: Harry Mellor
- **时间**: 2026-11-13T19:58:52Z
- **提交信息**: [Bugfix] Apply `WeightsMapper` stacked rules last, and fix the `--mm-encoder-only` shared root check (#65965)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [379a848](https://github.com/vllm-project/vllm/commit/379a8487a2381e69787525f60a9e2e71a72417fa)

- **作者**: pranavabbott
- **时间**: 2026-11-13T19:16:46Z
- **提交信息**: [Bugfix][Model] DiffusionGemma: stop sampler recompiles during serving (#61669)

Signed-off-by: Pranav Abbott <abbott@meta.com>

### [cfee9bc](https://github.com/vllm-project/vllm/commit/cfee9bc62bf49769cfa8d30d7d7141c0f4e9eef4)

- **作者**: Xiao Jin
- **时间**: 2026-11-13T18:39:37Z
- **提交信息**: [Test] Restore PaddleOCR-VL generation coverage on Transformers v5 (#66267)

Signed-off-by: YuZheJin <1370324293@qq.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: YuZheJin <1370324293@qq.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [e58d156](https://github.com/vllm-project/vllm/commit/e58d1560f3aa0b11a54d42f20fb06eb216045847)

- **作者**: Matthew Bonanni
- **时间**: 2026-11-13T18:38:38Z
- **提交信息**: [Bugfix][HiSparse] Fix GLM-5.3-Flash startup: derive resident/hot specs without grouping on workers (#67516)

Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [6839b64](https://github.com/vllm-project/vllm/commit/6839b646554764d4f9d56521437576f442197022)

- **作者**: Matthew Bonanni
- **时间**: 2026-11-13T18:27:57Z
- **提交信息**: [HiSparse] Revert the FlashInfer all-reduce backend override (#65201, #65522) (#67041)

Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>

### [a858aa3](https://github.com/vllm-project/vllm/commit/a858aa3164fd878f8e8b580d6bf2acd3d9f4bf5f)

- **作者**: Dario A
- **时间**: 2026-11-13T18:18:24Z
- **提交信息**: [Quantization] Allow online per-channel fp8 quantization of an unquantized lm_head (#61815)

Signed-off-by: riceharvest <myappleiddarimaan@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [7dadcb6](https://github.com/vllm-project/vllm/commit/7dadcb647ec6a1787b081d6f3faf53a974225178)

- **作者**: fxmarty-amd
- **时间**: 2026-11-13T18:08:02Z
- **提交信息**: [Quantization] Skip kernel dispatch for online requantization sources (#66803)

Signed-off-by: Felix Marty <Felix.Marty@amd.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [55c809d](https://github.com/vllm-project/vllm/commit/55c809dfc9bdbe07173b6b73aa4cec8f0d50b717)

- **作者**: Chaitanya Sri Krishna Lolla
- **时间**: 2026-11-13T18:05:15Z
- **提交信息**: [ROCm][DI-CI] Enable MiniMax-M3.1-Flash in AMD CI pipeline (#67466)

Signed-off-by: lcskrishna <lollachaitanya@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [b7b7a6e](https://github.com/vllm-project/vllm/commit/b7b7a6e8305170fbe1e5158396aa119cd769493f)

- **作者**: Zohaib Moti
- **时间**: 2026-11-13T18:04:50Z
- **提交信息**: [ROCm][gfx1151] ROCM_RDNA_ATTN: prefer 16-token KV blocks (#67344)

Signed-off-by: Zohaib Moti <zohaib.moti@amd.com>
Signed-off-by: Robert Esclapez Garcia <robert.garcia@amd.com>
Co-authored-by: Robert Esclapez <Robert.Garcia@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [38c3f6d](https://github.com/vllm-project/vllm/commit/38c3f6d2501ad80d8036e7eb31e7e56b13317451)

- **作者**: cjackal
- **时间**: 2026-11-13T17:41:42Z
- **提交信息**: [Spec Decode] Enable adaptive verification for `FlashInferMLASparseSM90Backend` (#62515)

Signed-off-by: cjackal <44624812+cjackal@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [63e75b2](https://github.com/vllm-project/vllm/commit/63e75b2093c2cbdfe658159496efdf9442a698d3)

- **作者**: Subhash Polisetti
- **时间**: 2026-11-13T17:40:19Z
- **提交信息**: [Perf][Model] Muse vision encoders: no GPU<->CPU syncs, build Glimmer's vision prep once per call (#64822)

Signed-off-by: subhash polisetti <subhashr161347@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>

### [cfd86e4](https://github.com/vllm-project/vllm/commit/cfd86e43206515956029d5e5cd25ac7bb212da2c)

- **作者**: cjackal
- **时间**: 2026-11-13T16:57:45Z
- **提交信息**: [Model] Extend device-side mm normalization to DeepSeekV4 Vision / DeepSeekV41 (#57985)

Signed-off-by: cjackal <44624812+cjackal@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [3ca16a8](https://github.com/vllm-project/vllm/commit/3ca16a8dff2fb94b669336a6bc4c63c55498248c)

- **作者**: Yi Liu
- **时间**: 2026-11-13T16:11:37Z
- **提交信息**: [Model] Load q/k/v scales for the quantized Kimi-K2.6 (#63097)

Signed-off-by: yiliu30 <yi4.liu@intel.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [9f2aee1](https://github.com/vllm-project/vllm/commit/9f2aee118e02c30405611c41f60f5318ee51d158)

- **作者**: Misha Goin
- **时间**: 2026-11-13T16:01:06Z
- **提交信息**: [Quantization] Make activation-quantization fallbacks explicit, add VLLM_STRICT_QUANT_SCHEME (#59460)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [3d3f440](https://github.com/vllm-project/vllm/commit/3d3f440f4bcdbb03f4d1eee98d531a47496f5bf9)

- **作者**: Cy Cheng
- **时间**: 2026-11-13T15:50:03Z
- **提交信息**: [Bugfix][Pooling] Honor the CrossEncoder activation saved by Sentence Transformers v6 (#62785)

Signed-off-by: Cy <15118312+cycancode@users.noreply.github.com>
Co-authored-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [ae96937](https://github.com/vllm-project/vllm/commit/ae96937c57c4eee9f7d8fd6114bbef822ab88885)

- **作者**: Kevin H. Luu
- **时间**: 2026-11-13T15:48:55Z
- **提交信息**: [CI][Bugfix] Read sliding_window from ManagerConfig.params in voxtral realtime test (#67476)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [157e42a](https://github.com/vllm-project/vllm/commit/157e42a76267566b2e232f47e67d70cbe98fdb9f)

- **作者**: Tomas Ruiz
- **时间**: 2026-11-13T15:27:39Z
- **提交信息**: [Spec Decode] Consistent drafted, verified and accepted token counts (#64156)

Signed-off-by: Yiliu Dong <91178480+qianlihuang@users.noreply.github.com>
Signed-off-by: Tomas Ruiz <tomas.ruiz.te@gmail.com>
Co-authored-by: Yiliu Dong <91178480+qianlihuang@users.noreply.github.com>
Co-authored-by: GLM <noreply@z.ai>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [d713d1b](https://github.com/vllm-project/vllm/commit/d713d1b1019a1d6af57acb8e4d35919d8e15e7ec)

- **作者**: S.J. Lee
- **时间**: 2026-11-13T15:24:05Z
- **提交信息**: [Model] Use FlashInfer for Gemma 4 with an NVFP4 KV cache when FA4 is unavailable (#47547)

Signed-off-by: lesj0610 <lesj0610@users.noreply.github.com>
Signed-off-by: lesj0610 <lesj0610@gmail.com>
Co-authored-by: lesj0610 <lesj0610@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [42a5659](https://github.com/vllm-project/vllm/commit/42a565983a035b8bc66f1eae4fd37111d55d891e)

- **作者**: Bugen Zhao
- **时间**: 2026-11-13T15:19:28Z
- **提交信息**: [Rust Frontend] Render tool-result media in the Inkling renderer (#67398)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [25e9f7b](https://github.com/vllm-project/vllm/commit/25e9f7b3f247f263ac2277f572f1eae36f82563a)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-11-13T15:05:05Z
- **提交信息**: [Model] Add Mistral Large 4 (#64534)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>
Co-authored-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Felix Marty <Felix.Marty@amd.com>
Co-authored-by: Hongxia Yang <hongxia.yang@amd.com>
Co-authored-by: Andy Luo <andy.luo@amd.com>
Co-authored-by: Julien Denize <julien.denize@mistral.ai>
Co-authored-by: Dimitrios Bariamis <12195802+dbari@users.noreply.github.com>
Co-authored-by: Julien Debache <jdebache@nvidia.com>
Co-authored-by: vanshil shah <49670736+vanshilshah97@users.noreply.github.com>

### [10a854e](https://github.com/vllm-project/vllm/commit/10a854ed6b3bbd7411c65ccbf87594e71c4d322c)

- **作者**: Shanshan Shen
- **时间**: 2026-11-13T14:10:51Z
- **提交信息**: [ROCm][Docs] Add DeepSeek-V4.1-Flash MI355X DP2 AgentX preset with UMBP KV offload (#67378)

Signed-off-by: shen-shanshan <467638484@qq.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [cf8fce5](https://github.com/vllm-project/vllm/commit/cf8fce503c326d68fce5a531a43aec25da132bb5)

- **作者**: Afloat
- **时间**: 2026-11-13T13:54:09Z
- **提交信息**: [Bugfix][Multimodal] Preserve values from non-native-endian NumPy embeddings (#67479)

Signed-off-by: Afloat <ShuffleMonkey@163.com>

### [18c7d9b](https://github.com/vllm-project/vllm/commit/18c7d9bcebf0a1f0f42313211fe2517e8c88beb3)

- **作者**: Aditya Ganesh Kumar
- **时间**: 2026-11-13T13:29:51Z
- **提交信息**: [Bugfix][Benchmark] Fix prefix_repetition crash and custom_audio --output-len in bench throughput (#67288)

Signed-off-by: Aditya Ganesh Kumar <adty910@gmail.com>

### [eed3ad5](https://github.com/vllm-project/vllm/commit/eed3ad5edf35a3573c143803433dd9fbec49899d)

- **作者**: Canlin Guo
- **时间**: 2026-11-13T13:08:42Z
- **提交信息**: [Perf][GLM-5.3] build eager attention metadata on the host for ViT (#67194)

Signed-off-by: Canlin <canlinguosdu@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [65c2b39](https://github.com/vllm-project/vllm/commit/65c2b39fac461b9054759c239299d3cb571a3a6a)

- **作者**: PerryZhang01
- **时间**: 2026-11-13T13:00:08Z
- **提交信息**: [CI][Bugfix] Migrate UMBP lazy offload tests to the ManagerConfig KV cache API (#67420)

Signed-off-by: PerryZhang01 <Perry.Zhang@amd.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [4dd68d1](https://github.com/vllm-project/vllm/commit/4dd68d139757b84757d126b7ca279e12d39e91e5)

- **作者**: anhtra3889
- **时间**: 2026-11-13T11:23:53Z
- **提交信息**: [Bugfix][Spec Decode] Allow min_p and logit_bias with speculative decoding (#67061)

Signed-off-by: Anh Tran <anhtra@nvidia.com>

### [191e5d5](https://github.com/vllm-project/vllm/commit/191e5d5df2ec693d5536a635079d58864dfacebb)

- **作者**: Artur Fierka
- **时间**: 2026-11-13T09:59:41Z
- **提交信息**: [Perf][Kernel][Quantization] Tensor-descriptor path for int4 fused_moe_kernel_gptq_awq (XPU default, sm100 opt-in) (#52652)

Signed-off-by: Artur Fierka <artur.fierka@intel.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [3f59772](https://github.com/vllm-project/vllm/commit/3f597728bd2ca23e22fdbc4584a6537d20eb2f15)

- **作者**: Thien Tran
- **时间**: 2026-11-13T09:55:44Z
- **提交信息**: [Bugfix][Kernel] Bump DeepGEMM for the MegaMoE combine-readiness fix under CUDA graph replay (#67181)

Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [aaf0c6c](https://github.com/vllm-project/vllm/commit/aaf0c6c9879246aa716e681242824f55c772c471)

- **作者**: Kevin H. Luu
- **时间**: 2026-11-13T09:44:39Z
- **提交信息**: [CI] Retry the CUDA image bake when the registry rate-limits the push (#67437)

Signed-off-by: Kevin Luu <51931015+khluu@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [7d208d4](https://github.com/vllm-project/vllm/commit/7d208d422916733047351183658936da2141e030)

- **作者**: Bugen Zhao
- **时间**: 2026-11-13T09:41:13Z
- **提交信息**: [Rust Frontend] Keep the mock engine alive in the test_app fixture (#67409)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [a46e2ab](https://github.com/vllm-project/vllm/commit/a46e2ab9dcbf0f533835f42e512afd782b1238d2)

- **作者**: Harry Mellor
- **时间**: 2026-11-13T09:32:13Z
- **提交信息**: [Misc] Fix override and context manager type annotations (#67295)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [93eeae6](https://github.com/vllm-project/vllm/commit/93eeae695f5178eddff728fe50eb18e30c90c33a)

- **作者**: Kevin H. Luu
- **时间**: 2026-11-13T09:16:25Z
- **提交信息**: [CI] Let ci-selector decide CMakeLists.txt changes on CUDA (#65881)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [2b635e9](https://github.com/vllm-project/vllm/commit/2b635e9014c3914b3e881e02ee88b4ddc4d6989d)

- **作者**: Lantao Jin
- **时间**: 2026-11-13T08:51:04Z
- **提交信息**: [Spec Decode] Keep dynamic speculative decoding for dense models with DP (#67005)

Signed-off-by: Lantao Jin <ltjin@amazon.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [1848013](https://github.com/vllm-project/vllm/commit/18480131cde317978e5bf343f9c30492b9abbaba)

- **作者**: Zheng Gong
- **时间**: 2026-11-13T08:45:45Z
- **提交信息**: [ROCm][Perf][GLM-5.3-Flash] Keep the fused gated RMSNorm for the KDA o_norm (#66219)

Signed-off-by: Zheng Gong <zgong@amd.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [b98e194](https://github.com/vllm-project/vllm/commit/b98e1941b499f68c3e87daa4ae96d975e302b597)

- **作者**: swappy
- **时间**: 2026-11-13T08:45:30Z
- **提交信息**: [Test][Model Loader] Leave reload headroom in the LoRA-MoE and online-quantize reload tests (#67210)

Signed-off-by: swappy <59965507+rycerzes@users.noreply.github.com>

### [0ef2a95](https://github.com/vllm-project/vllm/commit/0ef2a95cc861adfae9a92ba104bdfd40ede8cbaa)

- **作者**: Fang Yuchu
- **时间**: 2026-11-13T07:57:38Z
- **提交信息**: [Feature] add the option to continue serving unfinished requests after the recovery (#50265)

Signed-off-by: TianZhuo <2770730562@qq.com>
Signed-off-by: fangyuchu <fangyuchu@qq.com>
Signed-off-by: Tyler Michael Smith <tlrmchlsmth@gmail.com>
Co-authored-by: tianzhuo <2770730562@qq.com>
Co-authored-by: Tyler Michael Smith <tlrmchlsmth@gmail.com>
Co-authored-by: Nicolò Lucchesi <nicolo.lucchesi@mistral.ai>

### [e67fb98](https://github.com/vllm-project/vllm/commit/e67fb98ad39a728a0dcccb1ed59dee3712baa943)

- **作者**: Dao007forever
- **时间**: 2026-11-13T07:45:33Z
- **提交信息**: [Rust Frontend][gRPC] Add the Render service with RenderChat (#65994)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Signed-off-by: Dao Le <Dao007forever@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>

### [329f93e](https://github.com/vllm-project/vllm/commit/329f93e1909efdd4548524b1500fa2c54ef2cbb0)

- **作者**: Lucas Wilkinson
- **时间**: 2026-11-13T07:32:30Z
- **提交信息**: [CI][Bugfix] Pin the GLM5-next shared-expert fusion test to the stock decode (#67369)

Signed-off-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [aee2b20](https://github.com/vllm-project/vllm/commit/aee2b208af6b116db3f6b2085b3d2c9823cdb13f)

- **作者**: Tianmu Li
- **时间**: 2026-11-13T07:31:37Z
- **提交信息**: [CPU][Perf] Split oversized final attention spans (#66855)

Signed-off-by: Li, Tianmu <tianmu.li@intel.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [ce3d4cd](https://github.com/vllm-project/vllm/commit/ce3d4cd9a94d50480107439c7b654aae9b9d9bd7)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-11-13T07:31:25Z
- **提交信息**: [Security] Fall back to eager when encoder CUDA graph replay exceeds capture (#60112)

Signed-off-by: Juan Pérez de Algaba <jperezde@redhat.com>

### [5120e70](https://github.com/vllm-project/vllm/commit/5120e70e181a9801f4a2e1299de4e0a94ce374f2)

- **作者**: abdulrahman-cohere
- **时间**: 2026-11-13T07:31:18Z
- **提交信息**: [Bugfix] Let SIGTERM during engine startup stop the API server (#67096)

Signed-off-by: abdulrahman-cohere <abdulrahman.abdulrazzag@cohere.com>
Co-authored-by: North Code <noreply@cohere.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [8d1843a](https://github.com/vllm-project/vllm/commit/8d1843a904f7ee5f0d3c09ac1b56a714cad1435d)

- **作者**: Chaojun Zhang
- **时间**: 2026-11-13T07:28:51Z
- **提交信息**: [XPU][CI] Use platform dist backend in dist_init test fixture (#67383)

Signed-off-by: Chaojun Zhang <chaojun.zhang@intel.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [74b2399](https://github.com/vllm-project/vllm/commit/74b2399bee59581b071053bf1fc4d4f9dab0a045)

- **作者**: Qiu Chunshuo
- **时间**: 2026-11-13T07:28:32Z
- **提交信息**: [Bugfix] Fix M-RoPE position preparation with PCP (#67002)

Signed-off-by: Baolongs <57425174+baolongsun@users.noreply.github.com>
Signed-off-by: QiuChunshuo <qiuchunshuo@huawei.com>
Co-authored-by: Baolongs <57425174+baolongsun@users.noreply.github.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [519262f](https://github.com/vllm-project/vllm/commit/519262f41015c572f3fca15b5182dba04eb197be)

- **作者**: CharlesWu
- **时间**: 2026-11-13T07:21:06Z
- **提交信息**: [Test][UMBP][10/10] Add lazy offload and token restore coverage (#61798)

Signed-off-by: CharlesWu <Charles.Wu@amd.com>
Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: TJian <tunjian.tan@embeddedllm.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [ab72c46](https://github.com/vllm-project/vllm/commit/ab72c466aaac03524e9282c66cd00daafce647dc)

- **作者**: Isotr0py
- **时间**: 2026-11-13T06:21:34Z
- **提交信息**: [Bugfix] Avoid duplicate values in `compile_ranges_endpoints` for compilation config (#67286)

Signed-off-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [153dc04](https://github.com/vllm-project/vllm/commit/153dc046462c4724a9a4eb393cadd60169ed943c)

- **作者**: Chaojun Zhang
- **时间**: 2026-11-13T05:58:02Z
- **提交信息**: [XPU][Test] Make test_shardq device-agnostic (#66981)

Signed-off-by: Chaojun Zhang <chaojun.zhang@intel.com>
Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [8a8cad0](https://github.com/vllm-project/vllm/commit/8a8cad0253ecf942f0c00c7e55a6bc7ddfee1dc1)

- **作者**: NingLin Liu
- **时间**: 2026-11-13T05:27:26Z
- **提交信息**: docs: typo in Elastic EP error and ASR comment (#67346)

Signed-off-by: ninglinLiu <x07514475479@gmail.com>

### [b3c08a2](https://github.com/vllm-project/vllm/commit/b3c08a2555a0865edab3710136fe91c470002c45)

- **作者**: Kevin H. Luu
- **时间**: 2026-11-13T05:16:24Z
- **提交信息**: [CI] Leave GPU headroom in the offline ColBERT plugin tests (#63405)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Wei Zhao <51183510+wzhao18@users.noreply.github.com>

### [7e4fc7c](https://github.com/vllm-project/vllm/commit/7e4fc7cf4b9aa03a69f1f286b04f2bd0946c1674)

- **作者**: Canlin Guo
- **时间**: 2026-11-13T05:16:12Z
- **提交信息**: [Kernel][GLM-5.3-Flash] Fused in-place q/k RMSNorm + RoPE and residual add inside RMSNorm (#67235)

Signed-off-by: Canlin <canlinguosdu@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [46d2cf0](https://github.com/vllm-project/vllm/commit/46d2cf0c25d5e9961a968bd418a23823a87b826a)

- **作者**: Wei Zhao
- **时间**: 2026-11-13T05:14:31Z
- **提交信息**: [CI] Fix the precompiled wheel variant and wait in python_only_compile.sh (#67311)

Signed-off-by: wzhao18 <wzhao18.sz@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [3b7049a](https://github.com/vllm-project/vllm/commit/3b7049a35cefa6d633339660cc97685b928e01bb)

- **作者**: Wei Zhao
- **时间**: 2026-11-13T05:14:17Z
- **提交信息**: [CI] Wait for the server to exit before checking its children in shutdown tests (#67326)

Signed-off-by: wzhao18 <wzhao18.sz@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [2dadc5c](https://github.com/vllm-project/vllm/commit/2dadc5c1387df8fe58b68c0d7c69a913035a9e32)

- **作者**: Wei Zhao
- **时间**: 2026-11-13T05:14:00Z
- **提交信息**: [CI] Run the Kimi K3 prefix cache Mooncake test over TCP on NVIDIA (#67310)

Signed-off-by: wzhao18 <wzhao18.sz@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [f41371f](https://github.com/vllm-project/vllm/commit/f41371f73b74bd9ccf0b2644793f7e6857229733)

- **作者**: Wei Zhao
- **时间**: 2026-11-13T05:13:36Z
- **提交信息**: [CI] Use torch.cuda.CUDAGraph in the DFlash MXFP8 context KV test on CUDA (#67309)

### [89554d6](https://github.com/vllm-project/vllm/commit/89554d694b4351dbe2f5f44e30341a5a40a674e2)

- **作者**: Yan Ma
- **时间**: 2026-11-13T05:10:36Z
- **提交信息**: [XPU] reduce memory footprint for test_sagemaker_invocation_validation (#67379)

Signed-off-by: Yan Ma <yan.ma@intel.com>

### [43c1db8](https://github.com/vllm-project/vllm/commit/43c1db8c9f30526fe0342c700e99d2c2648d92e4)

- **作者**: Lucas Wilkinson
- **时间**: 2026-11-13T04:47:48Z
- **提交信息**: [Core][KV Cache] Move KV cache allocation policy out of KVCacheSpecs (RFC #42449 part 2) (#61452)

Signed-off-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [c410543](https://github.com/vllm-project/vllm/commit/c410543d9ffff03f5f6c4a8c0ae1d3ad082c4a15)

- **作者**: Bugen Zhao
- **时间**: 2026-11-13T04:39:04Z
- **提交信息**: [Rust Frontend] Support output_mode="text" on the generate route (#67359)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [2c3d557](https://github.com/vllm-project/vllm/commit/2c3d557aa1aab0a550662c51f988dc09dc17f5e1)

- **作者**: Fadi Arafeh
- **时间**: 2026-11-13T04:31:06Z
- **提交信息**: [CPU][Test] Add INT8 W4A8 smoke tests for Arm CPUs (#65191)

Signed-off-by: Fadi Arafeh <fadi.arafeh@arm.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [c8d1f42](https://github.com/vllm-project/vllm/commit/c8d1f428aa9d32a8f4bd9097cf84b41e5ac4f10c)

- **作者**: Shuojie
- **时间**: 2026-11-13T04:30:35Z
- **提交信息**: [CI] Rebalance Arm CPU test shards (#66414)

Signed-off-by: Shuojie Wang <latioswang@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [f745eec](https://github.com/vllm-project/vllm/commit/f745eec5e2d91989f571350109725ed70d277c5b)

- **作者**: Ronald
- **时间**: 2026-11-13T04:14:47Z
- **提交信息**: [Bugfix][Model Loader] Handle merged-linear padding for Qwen4Exp and Kimi KDA (#66784)

Signed-off-by: Ronald1995 <ronaldautomobile@163.com>
Signed-off-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [9763d76](https://github.com/vllm-project/vllm/commit/9763d76048b33326793d75071e06d7975a6084b4)

- **作者**: yhcheong (vllmellm)
- **时间**: 2026-11-13T04:12:35Z
- **提交信息**: [Recipe][ROCm] MiMo-V2.6: use ROCM_AITER_UNIFIED_ATTN and add encoder-parallel opt-in (#67050)

Signed-off-by: vllmellm <vllm.ellm@embeddedllm.com>

### [793a635](https://github.com/vllm-project/vllm/commit/793a6351d624d7cb6c5d56b822f45e5b63f7efd0)

- **作者**: Siddharth Nachane
- **时间**: 2026-11-13T03:52:14Z
- **提交信息**: [Security][Model] Preserve Gemma audio frame dimensions and unified token counts (#47652)

Signed-off-by: Sidd065 <sidd.jml@gmail.com>
Signed-off-by: Siddharth Nachane <78248734+Sidd065@users.noreply.github.com>
Signed-off-by: Juan Pérez de Algaba <jperezde@redhat.com>
Signed-off-by: Isotr0py <2037008807@qq.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: Juan Pérez de Algaba <jperezde@redhat.com>
Co-authored-by: Isotr0py <2037008807@qq.com>

### [c8b94fc](https://github.com/vllm-project/vllm/commit/c8b94fc8ce61a7ba15923232fce2f9a93307fe44)

- **作者**: Bugen Zhao
- **时间**: 2026-11-13T03:50:27Z
- **提交信息**: [Rust Frontend] Return requested logprobs from the mock engine (#67257)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [0e28715](https://github.com/vllm-project/vllm/commit/0e2871508b20815f2e5969f1697a0de5b1b90881)

- **作者**: Bugen Zhao
- **时间**: 2026-11-13T03:43:47Z
- **提交信息**: [Rust Frontend] Support stop strings on the generate route (#66540)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [a9dcfae](https://github.com/vllm-project/vllm/commit/a9dcfae9ef0756ce076d0053429d6c9afef067a3)

- **作者**: Zheng Gong
- **时间**: 2026-11-13T03:23:03Z
- **提交信息**: [ROCm][Perf] MXFP8 native linear: 256x256x128 tile for large prefill GEMMs on gfx950 (#66598)

Signed-off-by: Zheng Gong <zgong@amd.com>

### [a574939](https://github.com/vllm-project/vllm/commit/a574939394086ae79be77f7c67dd32979249a40c)

- **作者**: Liangliang Ma
- **时间**: 2026-11-13T03:00:38Z
- **提交信息**: [XPU][Kimi-K3] Run KDA metadata tests on XPU (#65840)

Signed-off-by: Ma, Liangliang <liangliang.ma@intel.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [33632e8](https://github.com/vllm-project/vllm/commit/33632e85708fed7b26c6935d9b6433277c4e4514)

- **作者**: Zeng, Leixin
- **时间**: 2026-11-13T02:59:16Z
- **提交信息**: [ROCm][Perf] Build AITER MLA full-graph decode metadata in one kernel (#65132)

Signed-off-by: Zeng, Leixin <Leixin.Zeng@amd.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: Shanshan Shen <467638484@qq.com>

### [327eb36](https://github.com/vllm-project/vllm/commit/327eb36e6e80ec4c2119b6929e56f7a49352d99c)

- **作者**: Bugen Zhao
- **时间**: 2026-11-13T02:58:27Z
- **提交信息**: [Rust Frontend] Stream Kimi K3 tool-call arguments (#66530)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [a90a462](https://github.com/vllm-project/vllm/commit/a90a462a6bcfae0daaef885a40b404d65adfa2d4)

- **作者**: Bugen Zhao
- **时间**: 2026-11-13T02:57:58Z
- **提交信息**: [Rust Frontend] Match response_template regexes with PCRE2 in the hf parser (#66222)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [0fab1aa](https://github.com/vllm-project/vllm/commit/0fab1aa459bd5bdfee4950f6a8752870e71810cb)

- **作者**: Bugen Zhao
- **时间**: 2026-11-13T02:57:24Z
- **提交信息**: [Rust Frontend] Fail in-flight requests when an engine disconnects (#67187)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [0f49f3a](https://github.com/vllm-project/vllm/commit/0f49f3a77245f0f97f0c85f247ab93639981479a)

- **作者**: yixing xu
- **时间**: 2026-11-13T02:56:55Z
- **提交信息**: [Spec Decode][FLy][ROCm] Normalize the top-k entropy gate and allow a FLy cost overlay with synthetic acceptance (#66593)

Signed-off-by: yixing xu <167271623+xiaoshingshing2@users.noreply.github.com>

### [4f6bbf8](https://github.com/vllm-project/vllm/commit/4f6bbf835a072fddc96cadaed5e6d72792308e6d)

- **作者**: Bugen Zhao
- **时间**: 2026-11-13T02:53:24Z
- **提交信息**: [Bugfix][Rust Frontend] Resolve auxiliary frames of add requests in the mock engine (#67256)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Hokwang Choi <choi920330@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [f7758c8](https://github.com/vllm-project/vllm/commit/f7758c8bd14680cfbc86708ebf9ece4d6416a13c)

- **作者**: Nick Hill
- **时间**: 2026-11-13T02:35:07Z
- **提交信息**: [Bugfix] Shut down the executor when EngineCore fails to start (#67331)

Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [cf5cb6c](https://github.com/vllm-project/vllm/commit/cf5cb6ca33837e5aa321d0f94bcc003d61962089)

- **作者**: Chaojun Zhang
- **时间**: 2026-11-13T02:31:11Z
- **提交信息**: [XPU][Test] Skip Unlimited-OCR-2 tests on non-CUDA platforms (#66982)

Signed-off-by: Chaojun Zhang <chaojun.zhang@intel.com>
Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [75368eb](https://github.com/vllm-project/vllm/commit/75368eb07f836ba0c5e3b35924ff3617b41508cd)

- **作者**: Nick Hill
- **时间**: 2026-11-13T02:30:01Z
- **提交信息**: [Bugfix][KV Connector] Stop forwarding shutdown() to LMCache until it no longer aborts (#67333)

### [2364ffb](https://github.com/vllm-project/vllm/commit/2364ffbeb78a0e15a3bff9fbc747900ecfdc6097)

- **作者**: xiangdong
- **时间**: 2026-11-13T02:29:23Z
- **提交信息**: [XPU][CI]Skip seed instability issue in Intel GPU CI  (#67148)

Signed-off-by: zengxian <xiangdong.zeng@intel.com>

### [1786f26](https://github.com/vllm-project/vllm/commit/1786f260e3d68fa4d5a97191ddbffd7179edc96a)

- **作者**: Taoyu Zhu
- **时间**: 2026-11-13T02:15:40Z
- **提交信息**: [Recipe] MiniMax-M3.1-Flash: MI355X Agent (#67272)

### [18d8c2e](https://github.com/vllm-project/vllm/commit/18d8c2ea97282e1f0a2872e577545c3a9d67848e)

- **作者**: Oxana Korzh
- **时间**: 2026-11-13T02:04:03Z
- **提交信息**: [ROCm][Perf][DSv4.1] Mono: merge K2(l) and K1(l + 1) into one launch at TP8 (#65461)

Signed-off-by: Oxana Korzh <okorzh@amd.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [c07d58d](https://github.com/vllm-project/vllm/commit/c07d58dc82d75f7d1a947b3264b460384ec3e18d)

- **作者**: yzong-rh
- **时间**: 2026-11-13T00:31:35Z
- **提交信息**: [Perf] Zero bubble draft tokens handoff for structured outputs (#64531)

Signed-off-by: Yifan Zong <yzong@redhat.com>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>

### [a8077ca](https://github.com/vllm-project/vllm/commit/a8077ca459d06fdda58f9bea55d6f0256ce23f3c)

- **作者**: Sriram Kumar
- **时间**: 2026-11-13T00:02:26Z
- **提交信息**: [ROCm] Revert #59420: pass the (B, next_n) context lengths to AITER as is (#65998)

Signed-off-by: Sriram Kumar <sriramkumar.kishorekumar@amd.com>
Co-authored-by: Douglas Lehr <91553416+dllehr-amd@users.noreply.github.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-11-14
**监控日期**: 2026-11-13
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7743
- **最后更新**: 2026-11-14T02:19:57Z

## 提交统计

- **昨日提交总数**: 33
- **提交者数量**: 25
- **主要提交者**: alex7092, Thang Nguyen, wangqiankun13

## AI分析总结

## vllm-omni 昨日提交分析（33 条）

### 1. 主要更新类型分布
- **CI/构建与测试**：约 14 条，占比最高（ROCm/CUDA/NPU 多后端覆盖、矩阵瘦身、阻塞式任务提升）
- **Bug 修复**：约 11 条，涵盖量化、模型运行时、前端校验、内核资源等
- **功能新增**：约 5 条（RL rollout、copy-engine 传输、批量推理、历史归档）
- **性能优化**：约 3 条（flat varlen attention、VAE 加载共享、多轨迹生成）
- **文档**：2 条（NPU 性能数据、低精度注意力文档）

### 2. 关键变更点与项目方向的关系
- **多模态服务稳定性**：修复 IndexTTS-2.5 长语音分段、Qwen3-Omni Code2Wav NPU 批量上限、MiniCPM-o 全双工 CI 等，直接支撑 README 中"易用、快速、低成本的全模态模型服务"目标。
- **多硬件后端扩张**：ROCm 夜间任务转阻塞、XPU wheel 与发布镜像、Ascend NPU 上 MOSS-TTS 支持，表明项目正从 CUDA 单一后端走向 GPU/NPU/CPU/XPU 全覆盖的生产级可用性。
- **扩散与图像模型**：HunyuanImage3 全参数 RL rollout、Qwen-Image 混合融合注意力优化、Ming Whisper 打包注意力参数绑定，体现对图像/扩散模态的深度投入。
- **CI 治理**：通过 timing artifacts 规划分片、收缩 CPU 矩阵、绑定 OOM 残留上报容差，是在提交量激增背景下控制 CI 成本与噪声的必要手段。

### 3. 影响与潜在意义
- 夜间任务提升为阻塞式 + 周覆盖扩充（OmniVoice、Step-Audio、Moss、Higgs、VoxCPM2、Voxtral），显著提高多模态模型在非 CUDA 硬件上的回归保障，降低发布风险。
- 量化（mxfp8 ignored_layers）、解码图池生命周期、Triton 资源拒绝重试等修复，提升了长时运行和混合负载下的健壮性。
- 潜在风险：CI 任务持续增多与"瘦身"并行，说明测试资源压力较大，后续需关注分片策略是否能跟上模型数量增长。

### 4. 值得关注的技术点
- **flat varlen attention 替代 per-bucket 循环**（Qwen-Image mixfusion）：对变长图像批处理是典型的性能范式转换。
- **copy-engine 传输用于 diffusion Ulysses**：为扩散模型并行引入专用传输通道，可能成为后续并行优化的基础。
- **Wan2.2 TI2V VAE 加载共享**：减少重复权重加载，直接降低"cheap serving"目标下的显存与启动开销。
- **Alpamayo 2 Super 单请求 n 轨迹**：一次请求产出多条轨迹，对 RL/推理时计算场景有扩展价值。
- 多条提交由 Cursor/Claude 等 AI 工具协作完成，反映项目开发流程已深度集成 AI 辅助。

### 5. 对项目发展的整体意义
这批提交显示 vllm-omni 正处于"广度扩张 + 质量加固"并行阶段：一方面快速吸收 TTS、语音全双工、图像扩散、RL 等新模态与新模型；另一方面通过 CI 阻塞化、多后端覆盖和大量边界条件修复，把实验性能力推向生产可用。这与 README 定位的"人人可用的全模态服务"高度一致——只有测试矩阵和硬件覆盖跟上，低成本多模态服务的承诺才能兑现。短期内项目的重点将是持续的工程稳定性与硬件生态适配，而非单一功能突破。

## 详细提交记录

### [a7725c2](https://github.com/vllm-project/vllm-omni/commit/a7725c2992a314ed3fb4d923b29df7aefea29ff0)

- **作者**: Shouju Wang | Soju 🍾
- **时间**: 2026-11-13T22:19:41Z
- **提交信息**: [Bugfix] Segment long IndexTTS-2.5 speech requests (#7567)

Signed-off-by: voidreaming <2707786374wsj@gmail.com>
Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [a0f2187](https://github.com/vllm-project/vllm-omni/commit/a0f2187729ddbb0d3fb5091d34ca84246befccbf)

- **作者**: hac17
- **时间**: 2026-11-13T21:47:04Z
- **提交信息**: [CI/Build][ROCm] Promote four NIGHTLY unit and inference jobs to blocking (#10271)

Signed-off-by: hac17 <29197483+hacZ17@users.noreply.github.com>
Co-authored-by: hac17 <29197483+hacZ17@users.noreply.github.com>

### [a33380d](https://github.com/vllm-project/vllm-omni/commit/a33380d3d309ba7135ab2e1297c5627e973ccbe8)

- **作者**: Yi Liu
- **时间**: 2026-11-13T21:11:21Z
- **提交信息**: [Bugfix][Quantization] mxfp8: honour ignored_layers match mode (#10282)

Signed-off-by: Yi Liu <yi4.liu@intel.com>

### [2c148ce](https://github.com/vllm-project/vllm-omni/commit/2c148ceb13737d1170e878c7e49e29f91b13d5a3)

- **作者**: hac17
- **时间**: 2026-11-13T16:28:06Z
- **提交信息**: [CI/Build][ROCm] Promote four NIGHTLY GPU smoke jobs to blocking (#10270)

Signed-off-by: hac17 <29197483+hacZ17@users.noreply.github.com>
Co-authored-by: hac17 <29197483+hacZ17@users.noreply.github.com>

### [12f1a50](https://github.com/vllm-project/vllm-omni/commit/12f1a50e0293f99342e27adbc5b2fbf90599e854)

- **作者**: lm10-arg
- **时间**: 2026-11-13T15:10:27Z
- **提交信息**: [CI/Build][ROCm] Add OmniVoice and Step-Audio weekly coverage (#10326)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>

### [aa2968e](https://github.com/vllm-project/vllm-omni/commit/aa2968e858a718989332a61ad40758024cb4a3a5)

- **作者**: Sheng GAO
- **时间**: 2026-11-13T14:21:01Z
- **提交信息**: [Diffusion] Add Batch for Noisy PP (#10122)

Signed-off-by: Sheng GAO <sheng.gao.dev@gmail.com>
Signed-off-by: sheng <sheng.gao.dev@gmail.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [d601ff8](https://github.com/vllm-project/vllm-omni/commit/d601ff8d1e2151fddda1abda77546752bf2d635e)

- **作者**: alex7092
- **时间**: 2026-11-13T13:19:47Z
- **提交信息**: [Bugfix] Bind FlashAttention arguments by name in the packed Ming Whisper attention (#9751)

Signed-off-by: 刘星 <15105576+alex7092@users.noreply.github.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [d89066a](https://github.com/vllm-project/vllm-omni/commit/d89066abf73bd8e6a979d98c9bb77d6376dfafdf)

- **作者**: lm10-arg
- **时间**: 2026-11-13T12:55:38Z
- **提交信息**: [CI/Build][ROCm] Add Moss and Higgs weekly coverage (#10280)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Signed-off-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>

### [9a6e3a7](https://github.com/vllm-project/vllm-omni/commit/9a6e3a765ce079fdf34adec04319e9201c7d63f1)

- **作者**: wangyu
- **时间**: 2026-11-13T12:04:51Z
- **提交信息**: [CI] Move Qwen3-Omni colocate async to full_model nightly; drop HunyuanImage3 shared TP4 jobs (#10295)

Signed-off-by: wangyu <410167048@qq.com>
Signed-off-by: [Your Name] <your_email@example.com>

### [80ebe1e](https://github.com/vllm-project/vllm-omni/commit/80ebe1e8dd7471ca66ca4b9d378194829ecdb95e)

- **作者**: wangyu
- **时间**: 2026-11-13T12:04:24Z
- **提交信息**: [Bugfix] Install pan2-guardrail in the CI image (#10247)

Signed-off-by: Cursor Agent <cursoragent@cursor.com>
Co-authored-by: Cursor Agent <cursoragent@cursor.com>
Co-authored-by: wangyu <yenuo26@users.noreply.github.com>

### [25e94e5](https://github.com/vllm-project/vllm-omni/commit/25e94e50a432661c01cb640357efadde2b8a8b68)

- **作者**: lm10-arg
- **时间**: 2026-11-13T11:09:28Z
- **提交信息**: [CI/Build][ROCm] Bound OOM residual reporting slack (#10309)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>

### [3ffe6e2](https://github.com/vllm-project/vllm-omni/commit/3ffe6e2e3cb9637bdbdd0ac1b69cbbc0e6a04b45)

- **作者**: mooncake2026
- **时间**: 2026-11-13T09:59:12Z
- **提交信息**: [Model] Add Hy-Nomas CPU history archive with failure cleanup (#10242)

Signed-off-by: lishunyang12 <125541396+lishunyang12@users.noreply.github.com>
Signed-off-by: mooncake2026 <284529637+mooncake2026@users.noreply.github.com>
Signed-off-by: mooncake2026 <yue5964@gmail.com>
Co-authored-by: lishunyang12 <125541396+lishunyang12@users.noreply.github.com>

### [8dedfaa](https://github.com/vllm-project/vllm-omni/commit/8dedfaaddf42bd8c0b5d81c4a04aa5691c1f4982)

- **作者**: wangwei1254
- **时间**: 2026-11-13T09:41:18Z
- **提交信息**: [Test] Unify DFX stability runner and add LingBot-World (GPU&NPU) case (#10250)

Signed-off-by: wangwei1254 <wangwei1254@h-partners.com>
Co-authored-by: wangyu <53896905+yenuo26@users.noreply.github.com>

### [470a28f](https://github.com/vllm-project/vllm-omni/commit/470a28fdd2c76227a8bfc241e4703b64ade2284e)

- **作者**: y-null
- **时间**: 2026-11-13T09:35:06Z
- **提交信息**: [CI/Build] Fix Talker DSpark drafter targeting wrong stage in MiniCPM-o 4.5 E2E (#10316)

Signed-off-by: y_null <y_null@qq.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [6c8f693](https://github.com/vllm-project/vllm-omni/commit/6c8f69303faf2c1d656df474b5b59083a66ba3e1)

- **作者**: wangqiankun13
- **时间**: 2026-11-13T08:57:52Z
- **提交信息**: [Bugfix][Qwen-Image-2.1] Fix decode graph pool lifetime and stream recovery (#10268)

Signed-off-by: wangqiankun13 <wangqiankun13@huawei.com>
Co-authored-by: dengyunyang <584797741@qq.com>

### [744dfe4](https://github.com/vllm-project/vllm-omni/commit/744dfe4d6ce8c385cc375cf9857513fba671196e)

- **作者**: ZacheryAU
- **时间**: 2026-11-13T08:24:23Z
- **提交信息**: [CI][Duplex][MiniCPM-o] Enhance Full Duplex CI test of MiniCPM-o 4.5 (#9555)

Co-authored-by: wangyu <53896905+yenuo26@users.noreply.github.com>

### [7f41e84](https://github.com/vllm-project/vllm-omni/commit/7f41e846e270bc61914973d42eb9d3a9614a1d3c)

- **作者**: zzh
- **时间**: 2026-11-13T07:54:05Z
- **提交信息**: [Bugfix] Retry MAGI-2 expert tiles after Triton resource rejection (#10291)

Signed-off-by: zzh <67720593+BLANKETusers@users.noreply.github.com>
Co-authored-by: Weitian Wang <wangweitian@hotmail.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: dengyunyang <584797741@qq.com>

### [d111310](https://github.com/vllm-project/vllm-omni/commit/d111310d548486118a2d22a943fa0a10fcff65e2)

- **作者**: psv666
- **时间**: 2026-11-13T07:06:04Z
- **提交信息**: [Bugfix][NPU] Bound non-streaming Qwen3-Omni Code2Wav batches (#10116)

Signed-off-by: psv666 <2693925048@qq.com>

### [bac3201](https://github.com/vllm-project/vllm-omni/commit/bac3201dc378fbe059af94833cf31cf67f63895c)

- **作者**: wangyu
- **时间**: 2026-11-13T06:49:13Z
- **提交信息**: [CI/Build] Shrink Ready Simple CPU mp matrices (noisy_kv + wan sharded) (#10070)

Signed-off-by: wangyu <53896905+yenuo26@users.noreply.github.com>
Co-authored-by: wangyu <yenuo26@users.noreply.github.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [42fa561](https://github.com/vllm-project/vllm-omni/commit/42fa561560ba745becbdc1628cae0872c14fa993)

- **作者**: lm10-arg
- **时间**: 2026-11-13T06:13:51Z
- **提交信息**: [CI/Build] Fix invalid-audio MIME error guard (#10302)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>

### [b5d5401](https://github.com/vllm-project/vllm-omni/commit/b5d54010ed06ce96ed1fe0d681cbe307475f7a95)

- **作者**: DarkMatter
- **时间**: 2026-11-13T05:18:49Z
- **提交信息**: [Doc][NPU] Add Atlas 800T A3 performance to the MiniMax-H3-Image recipe (#10292)

Signed-off-by: DarkMatter9527 <1376576122@qq.com>

### [13c8d8d](https://github.com/vllm-project/vllm-omni/commit/13c8d8d25f1c3e5c8b915fafc8d8f9cb1523ef4e)

- **作者**: Wang  fuyin
- **时间**: 2026-11-13T04:45:49Z
- **提交信息**: [Feat] Add HunyuanImage3 full-parameter RL rollout support (#9535)

Signed-off-by: Acerak01-fy <187926210+Acerak01-fy@users.noreply.github.com>
Signed-off-by: Wang  fuyin <wfy2003324@163.com>
Co-authored-by: Acerak01-fy <187926210+Acerak01-fy@users.noreply.github.com>
Co-authored-by: dengyunyang <584797741@qq.com>

### [4dee28c](https://github.com/vllm-project/vllm-omni/commit/4dee28cac13d972ada72b6196a984988ceb3a057)

- **作者**: heyew
- **时间**: 2026-11-13T04:13:06Z
- **提交信息**: [Hardware][Ascend] Support MOSS-TTS-Local on the NPU Model Runner V2 (#9953)

Signed-off-by: heyew <2025190973@qq.com>

### [6c40c5e](https://github.com/vllm-project/vllm-omni/commit/6c40c5edde7fde9bfc084dde3acbb33abdc90c71)

- **作者**: Thang Nguyen
- **时间**: 2026-11-13T03:45:08Z
- **提交信息**: [CI/Build] Publish XPU wheel index and XPU release image (#10124)

Signed-off-by: Thang Nguyen <thangnguyenvn647@gmail.com>
Signed-off-by: Chendi Xue <chendi.xue@intel.com>
Co-authored-by: Chendi.Xue <chendi.xue@intel.com>

### [24e8572](https://github.com/vllm-project/vllm-omni/commit/24e85728aa75083ad31009cf25544ea6462c0aec)

- **作者**: Renyongxing
- **时间**: 2026-11-13T03:36:59Z
- **提交信息**: [Perf][Diffusion][Qwen-Image] Replace per-bucket varlen loop with flat varlen attention for mixfusion (#6711)

Signed-off-by: renyongxing <renyongxing2@huawei.com>
Signed-off-by: Acerak01-fy <187926210+Acerak01-fy@users.noreply.github.com>
Co-authored-by: desenSunUBW <desensun@163.com>
Co-authored-by: Acerak01-fy <187926210+Acerak01-fy@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: dengyunyang <584797741@qq.com>

### [e75eab3](https://github.com/vllm-project/vllm-omni/commit/e75eab3b61b64011c4138c21e1fc2eebdbc53606)

- **作者**: Lucas Kabela
- **时间**: 2026-11-13T03:33:18Z
- **提交信息**: [Core] Share Wan2.2 TI2V VAE loading in OmniAutoencoderKLWan (#10196)

Signed-off-by: Lucas Kabela <20960393+Lucaskabela@users.noreply.github.com>
Co-authored-by: Lucas Kabela <20960393+Lucaskabela@users.noreply.github.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [40b1153](https://github.com/vllm-project/vllm-omni/commit/40b1153fe35645bbd05a6ecbd97b41b5da65bd22)

- **作者**: bastefaniak
- **时间**: 2026-11-13T02:55:07Z
- **提交信息**: [Doc] Add low precision attention docs for Cosmos3 (#9538)

Signed-off-by: Bartosz Stefaniak <bstefaniak@nvidia.com>

### [356edc5](https://github.com/vllm-project/vllm-omni/commit/356edc59647a950d0b787e54a75cbf235cbb3865)

- **作者**: Krzysztof Tomala
- **时间**: 2026-11-13T02:35:14Z
- **提交信息**: [Model] Alpamayo 2 Super: n trajectories from one request (#10076)

Signed-off-by: Krzysztof Tomala <ktomala@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [272c28c](https://github.com/vllm-project/vllm-omni/commit/272c28c5c344b968fb95c37e1b3927ca5cc73bf8)

- **作者**: Yukim1
- **时间**: 2026-11-13T01:56:15Z
- **提交信息**: [Kernel] Add copy-engine transport for diffusion Ulysses (#9922)

Signed-off-by: zwhzzz0821 <2831474076@qq.com>
Co-authored-by: dengyunyang <584797741@qq.com>

### [1525406](https://github.com/vllm-project/vllm-omni/commit/152540631c3abc2c2b89a94518249cb33f2358fd)

- **作者**: Lingwei1943
- **时间**: 2026-11-13T01:52:05Z
- **提交信息**: [Bugfix][Frontend] reject MP4 voice uploads at validation with the conversion hint (#10087)

Signed-off-by: Lingwei1943 <lingwei1943@users.noreply.github.com>
Co-authored-by: Lingwei1943 <lingwei1943@users.noreply.github.com>

### [6039984](https://github.com/vllm-project/vllm-omni/commit/6039984e397d3b4b28afd4538fa0207594e3ecba)

- **作者**: Zeng Chuang
- **时间**: 2026-11-13T01:35:41Z
- **提交信息**: [Bugfix] Preserve HunyuanImage3 AR token identity for KV reuse (#9323)

Signed-off-by: zengchuang-hw <zengchuang1005@gmail.com>
Signed-off-by: zengchuang <zengchuang3@huawei.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [fa7a898](https://github.com/vllm-project/vllm-omni/commit/fa7a8986e799d2ab0ed66c5afe7a2c53cf83a635)

- **作者**: wangyu
- **时间**: 2026-11-13T01:28:40Z
- **提交信息**: [CI] Plan CUDA ready and merge shards from timing artifacts (#9923)

Signed-off-by: wangyu <410167048@qq.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [4a44aa7](https://github.com/vllm-project/vllm-omni/commit/4a44aa79aec08f85f8261609652604d0aee33c39)

- **作者**: lm10-arg
- **时间**: 2026-11-13T00:24:05Z
- **提交信息**: [CI/Build][ROCm] Add VoxCPM2 and Voxtral weekly coverage (#10212)

Signed-off-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>
Co-authored-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>

---
